---
title: Replicatie
description: Leer om replicatieagenten in Adobe Experience Manager te vormen en te controleren.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: configuring
docset: aem65
feature: Configuring
exl-id: 09943de5-8d62-4354-a37f-0521a66b4c49
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '3354'
ht-degree: 0%

---

# Replicatie{#replication}

De agenten van de replicatie zijn centraal aan Adobe Experience Manager (AEM) als mechanisme dat wordt gebruikt om:

* [Publiceren (activeren)](/help/sites-authoring/publishing-pages.md#activatingcontent) inhoud van een auteur naar een publicatieomgeving.
* Inhoud expliciet uit de Dispatcher-cache verwijderen.
* Hiermee wordt gebruikersinvoer (bijvoorbeeld formulierinvoer) vanuit de publicatieomgeving teruggestuurd naar de auteur-omgeving (onder controle van de auteur-omgeving).

Verzoeken zijn [in de wachtrij](/help/sites-deploying/osgi-configuration-settings.md#apacheslingjobeventhandler) aan het voor verwerking geschikte agens.

>[!NOTE]
>
>Gebruikersgegevens (gebruikers, gebruikersgroepen en gebruikersprofielen) worden niet gerepliceerd tussen auteur- en publicatieinstanties.
>
>Voor meerdere publicatie-instanties worden gebruikersgegevens verkocht wanneer [Gebruikerssynchronisatie](/help/sites-administering/sync.md) is ingeschakeld.

## Repliceren van auteur naar publicatie {#replicating-from-author-to-publish}

De replicatie, aan een Publish instantie of een Verzender, vindt in verscheidene stappen plaats:

* De auteur vraagt dat bepaalde inhoud wordt gepubliceerd (geactiveerd). Dit kan worden geïnitieerd door een handmatig verzoek of door automatische triggers die vooraf zijn geconfigureerd.
* het verzoek wordt overgegaan tot de aangewezen standaard replicatieagent; een milieu kan verscheidene standaardagenten hebben die altijd voor dergelijke acties worden geselecteerd.
* de replicatieagent &quot;verpakt&quot;de inhoud en plaatst het in de replicatierij.
* op het tabblad Websites [gekleurde statusindicator](/help/sites-authoring/publishing-pages.md#determiningpagepublicationstatus) wordt ingesteld voor de afzonderlijke pagina&#39;s.
* de inhoud wordt opgeheven van de rij en aan het Publish milieu gebruikend het gevormde protocol vervoerd; gewoonlijk is dit HTTP.
* een servlet in het Publish milieu ontvangt het verzoek en publiceert de ontvangen inhoud; het standaardservlet is `https://localhost:4503/bin/receive`.

* Er kunnen meerdere auteur- en publicatieomgevingen worden geconfigureerd.

![chlimage_1-21](assets/chlimage_1-21.png)

### Repliceren van Publiceren naar Auteur {#replicating-from-publish-to-author}

Met sommige functies kunnen gebruikers gegevens invoeren op een instantie Publiceren.

Soms, is een type van replicatie die als omgekeerde replicatie wordt bekend, nodig om deze gegevens aan het milieu van de Auteur terug te keren van waar het aan andere Publish milieu&#39;s opnieuw wordt verdeeld. Om veiligheidsredenen moet het verkeer van de Publicatie naar de Auteur-omgeving strikt worden gecontroleerd.

De omgekeerde replicatie gebruikt een agent in het Publish milieu dat verwijzingen het milieu van de Auteur. Deze agent plaatst de gegevens in een outbox. Deze outbox wordt aangepast met replicatieluisteraars in het milieu van de Auteur. De luisteraars onderzoeken de outboxes om het even welke ingevoerde gegevens te verzamelen en dan het zonodig te verspreiden. Dit zorgt ervoor dat het milieu van de Auteur al verkeer controleert.

In andere gevallen, zoals bij de functies van de Gemeenschappen (bijvoorbeeld forums, blogs, opmerkingen en revisies), is het moeilijk om de hoeveelheid door de gebruiker gegenereerde inhoud (UGC) die wordt ingevoerd in de publicatieomgeving, op efficiënte wijze te synchroniseren in verschillende AEM instanties met behulp van replicatie.

AEM [Gemeenschappen](/help/communities/overview.md) gebruikt nooit replicatie voor UGC. In plaats daarvan vereist de plaatsing voor Gemeenschappen een gemeenschappelijke opslag voor UGC (zie [Opslag van communautaire inhoud](/help/communities/working-with-srp.md)).

### Replicatie - uit de doos {#replication-out-of-the-box}

De wij-kleinhandelswebsite die in een standaardinstallatie van AEM inbegrepen is kan worden gebruikt om replicatie te illustreren.

Om dit voorbeeld te volgen, en de standaardreplicatieagenten te gebruiken, [AEM installeren](/help/sites-deploying/deploy.md) met:

* de auteuromgeving op de haven `4502`
* de publicatie-omgeving op de poort `4503`

>[!NOTE]
>
>Standaard ingeschakeld:
>
>* Agenten op Auteur: StandaardAgent (publiceren)
>
>Effectief uitgeschakeld (vanaf AEM 6.1):
>
>* Agenten op Auteur: Omgekeerde Agent van de Replicatie (publish_reverse)
>* Medewerkers op Publiceren: Reverse Replication (outbox)
>
>Om het statuut van of de agent of de rij te controleren, gebruik **Gereedschappen** console.
>Zie [Uw replicatieagents controleren](#monitoring-your-replication-agents).

#### Replicatie (te publiceren auteur) {#replication-author-to-publish}

1. Navigeer naar de ondersteuningspagina in de ontwerpomgeving.
   **https://localhost:4502/content/we-retail/us/en/experience.html** `<pi>`
1. Bewerk de pagina zodat u nieuwe tekst kunt toevoegen.
1. **Pagina activeren** zodat u de wijzigingen kunt publiceren.
1. Open de ondersteuningspagina in de publicatieomgeving:
   **https://localhost:4503/content/we-retail/us/en/experience.html**
1. U kunt nu de wijzigingen zien die u hebt ingevoerd voor de auteur.

Deze replicatie wordt van het milieu van de Auteur in actie gebracht door:

* **Standaardagent (publiceren)**
Deze agent repliceert inhoud aan het gebrek publiceren instantie.
De details van dit (configuratie en logboeken) kunnen van de console van Hulpmiddelen van het milieu van de Auteur worden betreden; of:
  `https://localhost:4502/etc/replication/agents.author/publish.html`.

#### Replication Agents - Out of the Box {#replication-agents-out-of-the-box}

De volgende agenten zijn beschikbaar in een standaard AEM installatie:

* [Standaardagent](#replication-author-to-publish)
Wordt gebruikt voor het repliceren van Auteur naar Publiceren.

* Dispatcher Flush Dit wordt gebruikt voor het beheren van de Dispatcher cache. Zie [Dispatcher Cache van de ontwerpomgeving ongeldig maken](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/page-invalidate.html#invalidating-dispatcher-cache-from-the-authoring-environment) en [Dispatcher Cache van een publicatie-instantie ongeldig maken](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/page-invalidate.html#invalidating-dispatcher-cache-from-a-publishing-instance) voor meer informatie .

* [Replicatie omkeren](#reverse-replication-publish-to-author)
Wordt gebruikt voor het repliceren van Publiceren naar Auteur. Reverse-replicatie wordt niet gebruikt voor functies van Gemeenschappen, zoals forums, blogs en opmerkingen. De optie is in feite uitgeschakeld omdat de Postvak UIT niet is ingeschakeld. Het gebruik van omgekeerde replicatie zou douaneconfiguratie vereisen.

* De statische Agent dit is een &quot;Agent die een statische vertegenwoordiging van een knoop in het filesystem opslaat.&quot;
Met de standaardinstellingen worden inhoudspagina&#39;s en dameselementen bijvoorbeeld opgeslagen onder `/tmp`, hetzij als HTML, hetzij in de juiste indeling van de activa. Zie de `Settings` en `Rules` tabs voor de configuratie.
Dit is aangevraagd zodat de inhoud zichtbaar is wanneer de pagina rechtstreeks bij de toepassingsserver wordt aangevraagd. Dit is een gespecialiseerde agent en (waarschijnlijk) wordt niet vereist voor de meeste gevallen.

## Replicatieagents - configuratieparameters {#replication-agents-configuration-parameters}

Wanneer het vormen van een replicatieagent van de console van Hulpmiddelen, zijn vier lusjes beschikbaar binnen de dialoog:

### Instellingen {#settings}

* **Naam**

  Een unieke naam voor de replicatieagent.

* **Beschrijving**

  Een beschrijving van het doel deze replicatieagent dient.

* **Ingeschakeld**

  Geeft aan of de replicatieagent is ingeschakeld.

  Wanneer de agent is **enabled**, wordt de wachtrij weergegeven als:

   * **Actief** wanneer objecten worden verwerkt.
   * **Niet-actief** als de wachtrij leeg is.
   * **Geblokkeerd** wanneer de punten in de rij zijn, maar niet kunnen worden verwerkt; bijvoorbeeld, wanneer de ontvangende rij wordt onbruikbaar gemaakt.

* **Type serienummering**

  Het type van rangschikking:

   * **Standaard**: Plaats als de agent automatisch moet worden geselecteerd.
   * **Dispatcher Flush**: Selecteer deze optie als de agent moet worden gebruikt voor het leegmaken van de Dispatcher-cache.

* **Vertraging opnieuw proberen**

  De vertraging (wachttijd in milliseconden) tussen twee pogingen, mocht een probleem worden ontmoet.

  Standaard: `60000`

* **Gebruiker-id agent**

  Afhankelijk van het milieu, gebruikt de agent deze gebruikersrekening om:

   * de inhoud van de ontwerpomgeving verzamelen en in een pakket plaatsen
   * de inhoud maken en schrijven in de publicatieomgeving

  Laat dit veld leeg om de systeemgebruikersaccount te gebruiken (de account die in sling is gedefinieerd als de beheerder; standaard is dit `admin`).

  >[!CAUTION]
  >
  >Voor een agent in de omgeving van de auteur deze account *moet* hebben leestoegang tot alle paden die u wilt herhalen.

  >[!CAUTION]
  >
  >Voor een agent in de publicatieomgeving wordt deze account *moet* beschikken over de benodigde lees- en schrijfrechten om de inhoud te repliceren.

  >[!NOTE]
  >
  >Dit kan als mechanisme worden gebruikt om specifieke inhoud voor replicatie te selecteren.

* **Logboekniveau**

  Hiermee bepaalt u het detailniveau dat voor logberichten moet worden gebruikt.

   * `Error`: alleen fouten worden vastgelegd
   * `Info`: fouten, waarschuwingen en andere informatieberichten worden vastgelegd
   * `Debug`: een hoog niveau van detail wordt gebruikt in de berichten, hoofdzakelijk voor zuivert doeleinden

  Standaard: `Info`

* **Gebruiken voor omgekeerde replicatie**

  Wijst erop of deze agent voor omgekeerde replicatie wordt gebruikt; keert gebruikersinput van Publish aan het milieu van de Auteur terug.

* **Alias-update**

  Als u deze optie selecteert, worden aanvragen voor validatie van aliassen of ijdelingspaden naar Dispatcher ingeschakeld. Zie ook [Een Dispatcher Flush-agent configureren](/help/sites-deploying/replication.md#configuring-a-dispatcher-flush-agent).

#### Vervoer {#transport}

* **URI**

  Dit specificeert het ontvangende servlet bij de doelplaats. Met name kunt u hier de hostnaam (of alias) en het contextpad naar de doelinstantie opgeven.

  Bijvoorbeeld:

   * Een standaardagent kan worden gerepliceerd naar `https://localhost:4503/bin/receive`
   * Een Dispatcher Flush-agent kan zich repliceren naar `https://localhost:8000/dispatcher/invalidate.cache`

  Het hier opgegeven protocol (HTTP of HTTPS) bepaalt de transportmethode.

  Voor de agenten van de Vlek van de Verzender, wordt het bezit van URI gebruikt slechts als u op weg-gebaseerde virtuele gastheeringangen gebruikt om tussen landbouwbedrijven te onderscheiden, gebruikt u dit gebied om het landbouwbedrijf te richten om ongeldig te maken. farm #1 heeft bijvoorbeeld een virtuele host van `www.mysite.com/path1/*` en farm #2 heeft een virtuele host van `www.mysite.com/path2/*`. U kunt een URL gebruiken van `/path1/invalidate.cache` om de eerste boerderij te richten en `/path2/invalidate.cache` om de tweede boerderij te richten.

* **Gebruiker**

  De gebruikersnaam van de account die moet worden gebruikt voor toegang tot het doel.

* **Wachtwoord**

  Wachtwoord voor de account die moet worden gebruikt voor toegang tot het doel.

* **NTLM-domein**

  Domein voor NTML-verificatie.

* **NTLM-host**

  Host voor NTML-verificatie.

* **Versoepelde SSL inschakelen**

  Schakel deze optie in als u wilt dat zelfgecertificeerde SSL-certificaten worden geaccepteerd.

* **Verlopen certificaten toestaan**

  Schakel deze optie in als u verlopen SSL-certificaten wilt accepteren.

#### Proxy {#proxy}

De volgende instellingen zijn alleen nodig als een proxy nodig is:

* **Proxyhost**

  Hostnaam van de proxy die wordt gebruikt voor vervoer.

* **Proxypoort**

  Poort van de proxy.

* **Proxygebruiker**

  De gebruikersnaam van de account die moet worden gebruikt.

* **Proxywachtwoord**

  Wachtwoord van de account die moet worden gebruikt.

* **NTLM-domein proxy**

  Het NTLM-proxydomein.

* **NTLM-host proxy**

  Het NTLM-proxydomein.

#### Uitgebreid {#extended}

* **Interface**

  Hier kunt u de socketinterface definiëren waaraan u wilt binden.

  Hiermee wordt het lokale adres ingesteld dat moet worden gebruikt bij het maken van verbindingen. Als deze niet is ingesteld, wordt het standaardadres gebruikt. Dit is nuttig om de interface te specificeren om op multi-homed of gegroepeerde systemen te gebruiken.

* **HTTP-methode**

  De HTTP-methode die moet worden gebruikt.

  Voor een Dispatcher Flush agent, is dit bijna altijd GET en zou niet moeten worden veranderd (POST zou een andere mogelijke waarde zijn).

* **HTTP-headers**

  Deze worden gebruikt voor Dispatcher Flush-middelen en geven elementen op die moeten worden verwijderd.

  Voor een Dispatcher Flush-agent hoeven de drie standaarditems niet te worden gewijzigd:

   * `CQ-Action:{action}`
   * `CQ-Handle:{path}`
   * `CQ-Path:{path}`

  Deze worden, indien van toepassing, gebruikt om de actie aan te geven die moet worden gebruikt bij het spoelen van de handgreep of het pad. De subparameters zijn dynamisch:

   * `{action}` geeft een replicatieactie aan

   * `{path}` Hiermee wordt een pad aangegeven

  Zij worden vervangen door het pad/de actie die relevant is voor het verzoek en hoeven daarom niet &quot;hardcoded&quot; te zijn:

  >[!NOTE]
  >
  >Als u AEM in een andere context dan de geadviseerde standaardcontext hebt geïnstalleerd, dan moet u de context in de Kopballen van HTTP registreren. Bijvoorbeeld:
  >`CQ-Handle:/<*yourContext*>{path}`

* **Verbinding sluiten**

  Schakel deze optie in zodat u de verbinding na elke aanvraag kunt sluiten.

* **Time-out voor verbinding**

  Time-out (in milliseconden) die moet worden toegepast wanneer wordt geprobeerd verbinding te maken.

* **Time-out socket**

  Time-out (in milliseconden) die moet worden toegepast wanneer wordt gewacht op verkeer nadat een verbinding tot stand is gebracht.

* **Protocol versie**

  Versie van het protocol. Bijvoorbeeld: `1.0` voor HTTP/1.0.

#### Triggers {#triggers}

Deze instellingen worden gebruikt om triggers voor geautomatiseerde replicatie te definiëren:

* **Standaard negeren**

  Indien gecontroleerd, wordt de agent uitgesloten van standaardreplicatie; dit betekent het niet wordt gebruikt als een tevreden auteur een replicatieactie uitgeeft.

* **Bij wijziging**

  Hier wordt een replicatie door deze agent automatisch teweeggebracht wanneer een pagina wordt gewijzigd. Gebruikt voor de agenten van de Vlek van de Verzender, maar ook voor omgekeerde replicatie.

* **Bij distribueren**

  Als deze optie is ingeschakeld, wordt alle inhoud die is gemarkeerd voor distributie automatisch door de agent gerepliceerd wanneer deze wordt gewijzigd.

* **On-/Offtime bereikt**

  Dit activeert automatische replicatie (om een pagina te activeren of te deactiveren zoals aangewezen) wanneer de tijden of de tijden die voor een pagina worden bepaald voorkomen. Dit wordt vooral gebruikt voor Dispatcher Flush-middelen.

* **Bij ontvangst**

  Indien gecontroleerd, repliceren de agentenketens wanneer het ontvangen van replicatiegebeurtenissen.

* **Geen statusupdate**

  Wanneer gecontroleerd, dwingt de agent geen update van de replicatiestatus.

* **Geen versie**

  Als deze optie is ingeschakeld, dwingt de agent geen versiering van geactiveerde pagina&#39;s.

## De replicatieagents configureren {#configuring-your-replication-agents}

Voor informatie over het verbinden van replicatieagenten aan de Publish instantie die MSSL gebruikt, zie [Repliceren met wederzijdse SSL](/help/sites-deploying/mssl-replication.md).

### Het vormen van uw Agenten van de Replicatie van het Milieu van de Auteur {#configuring-your-replication-agents-from-the-author-environment}

Van het lusje van Hulpmiddelen in het milieu van de Auteur, kunt u replicatieagenten vormen die in of het milieu van de Auteur (**Medewerkers op auteur**) of de publicatieomgeving (**Medewerkers voor publicatie**). De volgende procedures illustreren de configuratie van een agent voor het milieu van de Auteur, maar kunnen voor beide worden gebruikt.

>[!NOTE]
>
>Wanneer een Dispatcher HTTP- verzoeken om Auteur of Publish instanties behandelt, moet het HTTP- verzoek van de replicatieagent de kopbal van de PAD omvatten. Naast de volgende procedure, moet u de kopbal van het PAD aan de lijst van de Verzender van cliëntkopballen toevoegen. Zie [/clientheaders (clientheaders)](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#specifying-the-http-headers-to-pass-through-clientheaders).
>

1. Toegang krijgen tot de **Gereedschappen** in AEM.
1. Klikken **Replicatie** (linkerdeelvenster om de map te openen).
1. Dubbelklikken **Medewerkers op auteur** (het linker- of rechterdeelvenster).
1. Klik de aangewezen agentennaam (die een verbinding) is om gedetailleerde informatie over die agent te tonen.
1. Klikken **Bewerken** zodat wordt het de configuratiedialoogvakje geopend:

   ![chlimage_1-22](assets/chlimage_1-22.png)

1. De opgegeven waarden moeten voldoende zijn voor een standaardinstallatie. Als u wijzigingen aanbrengt, klikt u **OK** om ze op te slaan (zie [Replicatieagents - configuratieparameters](#replication-agents-configuration-parameters) voor informatie over individuele parameters).

>[!NOTE]
>
>Een standaardinstallatie van AEM specificeert `admin` als gebruiker voor vervoergeloofsbrieven binnen de standaardreplicatieagenten.
>
>Dit moet worden gewijzigd in een sitespecifieke gebruikersaccount voor replicatie met de bevoegdheden om de vereiste paden te repliceren.

### Omgekeerde replicatie configureren {#configuring-reverse-replication}

De omgekeerde replicatie wordt gebruikt om gebruikersinhoud terug te krijgen die op een Publish instantie wordt geproduceerd aan een instantie van de Auteur. Dit wordt doorgaans gebruikt voor functies zoals enquêtes en registratieformulieren.

Om veiligheidsredenen staan de meeste netwerktopologieën geen verbindingen toe *van* de &quot;Gedemilitariseerde Zone&quot; (een subnetwerk dat de externe diensten aan een onvertrouwd netwerk zoals Internet blootstelt).

Aangezien het Publish milieu gewoonlijk in DMZ is, om inhoud terug naar het milieu van de Auteur te krijgen moet de verbinding van de instantie van de Auteur in werking worden gesteld. Dit wordt gedaan met:

* een *outbox* in de publicatieomgeving waarin de inhoud wordt geplaatst.
* een agent (publiceren) in het milieu van de Auteur die periodiek outbox voor nieuwe inhoud opiniepeilt.

>[!NOTE]
>
>Voor AEM [Gemeenschappen](/help/communities/overview.md), wordt de replicatie niet gebruikt voor gebruiker-geproduceerde inhoud op een Publish instantie. Zie [Opslag van communautaire inhoud](/help/communities/working-with-srp.md).

Hiervoor hebt u het volgende nodig:

**Een omgekeerde replicatieagent in het milieu van de Auteur** - Handelt als actieve component om informatie van outbox in het Publish milieu te verzamelen:

Als u omgekeerde replicatie wilt gebruiken, zorg ervoor dat deze agent wordt geactiveerd.

![chlimage_1-23](assets/chlimage_1-23.png)

**Een omgekeerde replicatieagent in het Publish milieu (een outbox)** - Het passieve element als &quot;uitbox&quot;. De input van de gebruiker wordt hier geplaatst, van waar het door de agent in het milieu van de Auteur wordt verzameld.

![chlimage_1-1](assets/chlimage_1-1.jpeg)

### Replicatie configureren voor meerdere publicatieinstanties {#configuring-replication-for-multiple-publish-instances}

>[!NOTE]
>
>Alleen inhoud wordt gerepliceerd. Gebruikersgegevens worden niet gekopieerd (gebruikers, gebruikersgroepen en gebruikersprofielen).
>
>Schakel [Gebruikerssynchronisatie](/help/sites-administering/sync.md).

Na installatie, wordt een standaardagent reeds gevormd voor replicatie van inhoud aan een Publish instantie die op haven 4503 van localhost loopt.

Om replicatie van inhoud voor een extra Publish instantie te vormen, creeer en vorm een nieuwe replicatieagent:

1. Open de **Gereedschappen** in AEM.
1. Selecteren **Replicatie** vervolgens **Medewerkers op auteur** in het linkerdeelvenster.
1. Selecteren **Nieuw...**.
1. Stel de **Titel** en **Naam** selecteert u vervolgens **Replication Agent**.
1. Klikken **Maken** zodat kunt u de agent tot stand brengen.
1. Dubbelklik op het nieuwe agentitem zodat het configuratievenster wordt geopend.
1. Klikken **Bewerken** - de **Instellingen agent** wordt geopend - de **Type serienummering** is reeds gedefinieerd als Standaard, dit moet zo blijven.

   * In de **Instellingen** tab:

      * Activeren **Ingeschakeld**.
      * Voer een **Beschrijving**.
      * Stel de **Vertraging opnieuw proberen** tot `60000`.

      * Laat de **Type serienummering** als `Default`.

   * In de **Vervoer** tab:

      * Voer de vereiste URI in voor de nieuwe instantie Publiceren, bijvoorbeeld
        `https://localhost:4504/bin/receive`.

      * Voer de sitespecifieke gebruikersaccount in die voor replicatie wordt gebruikt.
      * U kunt desgewenst andere parameters configureren.

1. Klikken **OK**.

Vervolgens kunt u de bewerking testen door een pagina in de ontwerpomgeving bij te werken en te publiceren.

De updates verschijnen op alle Publish instanties die zoals hierboven zijn gevormd.

Als u problemen ondervindt, kunt u de logboekbestanden in de instantie Auteur controleren. Afhankelijk van het vereiste detailniveau kunt u ook de **Logboekniveau** tot `Debug` met de **Instellingen agent** zoals hierboven.

>[!NOTE]
>
>Dit kan worden gecombineerd met het gebruik van de [Gebruiker-id agent](#agentuserid) om verschillende inhoud te selecteren voor replicatie naar de afzonderlijke publicatieomgevingen. Voor elke publicatie-omgeving:
>
>1. Vorm een replicatieagent voor het herhalen aan die Publish milieu.
>1. Een gebruikersaccount configureren; met de toegangsrechten die zijn vereist voor het lezen van de inhoud die wordt gerepliceerd naar die specifieke publicatieomgeving.
>1. Wijs de gebruikersaccount toe als de **Gebruiker-id agent** voor de replicatieagent.
>

### Een Dispatcher Flush-agent configureren {#configuring-a-dispatcher-flush-agent}

De standaardagenten zijn inbegrepen met de installatie. Nochtans, is een bepaalde configuratie nog nodig en het zelfde is van toepassing als u een nieuwe agent bepaalt:

1. Open de **Gereedschappen** in AEM.
1. Klikken **Implementatie**.
1. Selecteren **Replicatie** en vervolgens **Medewerkers voor publicatie**.
1. Dubbelklik op de knop **Dispatcher Flush** item om het overzicht te openen.
1. Klikken **Bewerken** - de **Instellingen agent** wordt geopend:

   * In de **Instellingen** tab:

      * Activeren **Ingeschakeld**.
      * Voer een **Beschrijving**.
      * Laat de **Type serienummering** als `Dispatcher Flush`, of plaats het als dusdanig als creërend een agent.

      * (optioneel) Selecteer **Alias-update** om validatieverzoeken van aliassen of ijdelingspaden naar Dispatcher in te schakelen.

   * In de **Vervoer** tab:

      * Voer de vereiste URI in voor de nieuwe instantie Publiceren, bijvoorbeeld
        `https://localhost:80/dispatcher/invalidate.cache`.

      * Voer de sitespecifieke gebruikersaccount in die voor replicatie wordt gebruikt.
      * U kunt desgewenst andere parameters configureren.

   Voor de agenten van de Vlek van de Verzender, wordt het bezit van URI gebruikt slechts als u op weg-gebaseerde virtuele gastheeringangen gebruikt om tussen landbouwbedrijven te onderscheiden, gebruikt u dit gebied om het landbouwbedrijf te richten om ongeldig te maken. farm #1 heeft bijvoorbeeld een virtuele host van `www.mysite.com/path1/*` en farm #2 heeft een virtuele host van `www.mysite.com/path2/*`. U kunt een URL gebruiken van `/path1/invalidate.cache` om de eerste boerderij te richten en `/path2/invalidate.cache` om de tweede boerderij te richten.

   >[!NOTE]
   >
   >Als u AEM in een andere context dan de geadviseerde standaardcontext hebt geïnstalleerd, vorm [HTTP-headers](#extended) in de **Uitgebreid** tab.

1. Klikken **OK**.
1. Terugkeren naar de **Gereedschappen** tab, vanaf hier kunt u **Activeren** de **Dispatcher Flush** agent (**Medewerkers voor publicatie**).

De **Dispatcher Flush** de replicatieagent is niet actief op de Auteur. U kunt dezelfde pagina openen in de publicatieomgeving met behulp van de equivalente URI, bijvoorbeeld `https://localhost:4503/etc/replication/agents.publish/flush.html`.

### Toegang tot replicatieagents beheren {#controlling-access-to-replication-agents}

De toegang tot de pagina&#39;s die worden gebruikt om de replicatieagenten te vormen kan worden gecontroleerd door gebruiker en/of groepspaginachtigingen op te gebruiken `etc/replication` knooppunt.

>[!NOTE]
>
>Het instellen van dergelijke machtigingen heeft geen invloed op gebruikers die inhoud repliceren (bijvoorbeeld via de websiteconsole of de optie sidekick). Het replicatieframework gebruikt niet de &quot;gebruikerssessie&quot; van de huidige gebruiker om toegang te krijgen tot replicatieagents tijdens het repliceren van pagina&#39;s.

### Het vormen van uw Medewerkers van de Replicatie van CRXDE Lite {#configuring-your-replication-agents-from-crxde-lite}

>[!NOTE]
>
>Het maken van replicatieagents wordt alleen ondersteund in het dialoogvenster `/etc/replication` locatie van de opslagplaats. Dit is nodig voor bijbehorende ACLs om behoorlijk te worden behandeld. Het creëren van een replicatieagent in een andere plaats van de boom zou tot onbevoegde toegang kunnen leiden.

Diverse parameters van uw replicatieagenten kunnen worden gevormd gebruikend CRXDE Lite.

Als u naar `/etc/replication`De volgende drie knooppunten worden weergegeven:

* `agents.author`
* `agents.publish`
* `treeactivation`

De twee `agents` houden configuratieinformatie over het aangewezen milieu, en zijn slechts actief wanneer dat milieu loopt. Bijvoorbeeld: `agents.publish` wordt alleen gebruikt in de publicatieomgeving. De volgende schermafbeelding toont de publicatieagent in de auteuromgeving, zoals opgenomen in AEM WCM:

![chlimage_1-24](assets/chlimage_1-24.png)

## Uw replicatieagents controleren {#monitoring-your-replication-agents}

Om een replicatieagent te controleren:

1. Toegang krijgen tot de **Gereedschappen** in AEM.
1. Klikken **Replicatie**.
1. Dubbelklik op de koppeling naar agents voor de juiste omgeving (links of rechts). Bijvoorbeeld: **Medewerkers op auteur**.

   Het resulterende venster toont een overzicht van al uw replicatieagenten voor het milieu van de Auteur, met inbegrip van hun doel en status.

1. Klik de aangewezen agentennaam (die een verbinding is) om gedetailleerde informatie over die agent te tonen:

   ![chlimage_1-2](assets/chlimage_1-2.jpeg)

   Hier kunt u het volgende doen:

   * Zie of de agent wordt toegelaten.
   * Zie het doel van eventuele replicaties.
   * Zie of de replicatierij actief (toegelaten) is.
   * Zie of er items in de wachtrij staan.
   * **Vernieuwen** of **Wissen** om de weergave van wachtrijitems bij te werken. Dit helpt u zien dat de punten ingaan en de rij verlaten.

   * **Logboek weergeven** om tot het logboek van om het even welke acties door de replicatieagent toegang te hebben.
   * **Verbinding testen** naar de doelinstantie.
   * **Opnieuw forceren** indien nodig op alle wachtrij-items.

   >[!CAUTION]
   >
   >Gebruik de koppeling &quot;Verbinding testen&quot; niet voor het selectievakje Reverse Replication Outbox op een instantie Publish.
   >
   >
   >Als een replicatietest voor een Postbus rij wordt uitgevoerd, worden om het even welke punten die ouder zijn dan de testreplicatie opnieuw verwerkt met elke omgekeerde replicatie.
   >
   >
   >Als dergelijke punten in een rij bestaan, kunnen zij met de volgende vraag van JCR van XPath worden gevonden en zouden moeten worden verwijderd.
   >
   >
   >`/jcr:root/var/replication/outbox//*[@cq:repActionType='TEST']`

## Batchreplicatie {#batch-replication}

De batchreplicatie dupliceert geen afzonderlijke pagina&#39;s of elementen, maar wacht op de eerste drempelwaarde van de twee, op basis van de tijd of grootte, die moeten worden geactiveerd.

Vervolgens worden alle replicatiepunten in een pakket opgenomen, dat vervolgens als één bestand wordt gerepliceerd naar de uitgever.

De uitgever pak alle punten, sparen hen en rapporteert terug naar de Auteur.

### Batchreplicatie configureren {#configuring-batch-replication}

1. Ga naar `http://serveraddress:serverport/siteadmin`
1. Druk op **[!UICONTROL Tools]** pictogram in de bovenzijde van het scherm
1. Ga vanaf de linkerzijspoor naar **[!UICONTROL Replication - Agents on Author]** en dubbelklikken **[!UICONTROL Default Agent]**.
   * U kunt ook de standaardpublicatiereplicatieagent bereiken door rechtstreeks naar `http://serveraddress:serverport/etc/replication/agents.author/publish.html`
1. Druk op **[!UICONTROL Edit]** boven de replicatiewachtrij.
1. Ga in het volgende venster naar de **[!UICONTROL Batch]** tab:
   ![batchreplicatie](assets/batchreplication.png)
1. Vorm de agent.

### Parameters {#parameters}

* `[!UICONTROL Enable Batch Mode]` - schakelt batchreplicatiemodus in of uit
* `[!UICONTROL Max Wait Time]` - Maximale wachttijd tot een batchverzoek is gestart, in seconden. De standaardwaarde is 2 seconden.
* `[!UICONTROL Trigger Size]` - Batch-replicatie wordt gestart als deze formaatlimiet

## Aanvullende bronnen {#additional-resources}

Voor meer informatie over het oplossen van problemen, kunt u lezen [Problemen met replicatie oplossen](/help/sites-deploying/troubleshoot-rep.md) pagina.
