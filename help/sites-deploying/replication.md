---
title: Replicatie
seo-title: Replicatie
description: Leer hoe te om replicatieagenten in AEM te vormen en te controleren.
seo-description: Leer hoe te om replicatieagenten in AEM te vormen en te controleren.
uuid: 6c0bc2fe-523a-401f-8d93-e5795f2e88b9
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: configuring
discoiquuid: 3cae081e-93e3-4317-b307-1316283c307a
docset: aem65
feature: Configureren
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '3435'
ht-degree: 0%

---


# Replicatie{#replication}

De agenten van de replicatie zijn centraal aan Adobe Experience Manager (AEM) als mechanisme dat wordt gebruikt om:

* [Publiceer (activeer) ](/help/sites-authoring/publishing-pages.md#activatingcontent) inhoud van een auteur aan een publicatiemilieu.
* Inhoud expliciet uit de Dispatcher-cache verwijderen.
* Hiermee wordt gebruikersinvoer (bijvoorbeeld formulierinvoer) vanuit de publicatieomgeving geretourneerd naar de auteursomgeving (onder controle van de auteursomgeving).

De verzoeken zijn [een rij gevormd](/help/sites-deploying/osgi-configuration-settings.md#apacheslingjobeventhandler) aan de aangewezen agent voor verwerking.

>[!NOTE]
>
>Gebruikersgegevens (gebruikers, gebruikersgroepen en gebruikersprofielen) worden niet gerepliceerd tussen auteur- en publicatieinstanties.
>
>Bij meerdere publicatie-instanties worden gebruikersgegevens verspreid wanneer [Gebruikerssynchronisatie](/help/sites-administering/sync.md) is ingeschakeld.

## Repliceren van auteur naar publicatie {#replicating-from-author-to-publish}

De replicatie, aan een publicatie-instantie of verzender, vindt in verscheidene stappen plaats:

* de auteur verzoekt om publicatie (activering) van bepaalde inhoud; dit kan door een handverzoek, of door automatische trekkers in werking worden gesteld die preconfigured zijn geweest.
* het verzoek wordt overgegaan tot de aangewezen standaard replicatieagent; een milieu kan verscheidene standaardagenten hebben die altijd voor dergelijke acties zullen worden geselecteerd.
* de replicatieagent &quot;verpakt&quot;de inhoud en plaatst het in de replicatierij.
* op het tabblad Websites wordt de [gekleurde statusindicator](/help/sites-authoring/publishing-pages.md#determiningpagepublicationstatus) ingesteld voor de afzonderlijke pagina&#39;s.
* de inhoud wordt uit de wachtrij gehaald en naar de publicatieomgeving getransporteerd met behulp van het geconfigureerde protocol; doorgaans is dit HTTP.
* een servlet in de publicatieomgeving ontvangt het verzoek en publiceert de ontvangen inhoud; de standaardservlet is `https://localhost:4503/bin/receive`.

* er kunnen meerdere auteur- en publicatieomgevingen worden geconfigureerd.

![chlimage_1-21](assets/chlimage_1-21.png)

### Replicatie van publiceren naar auteur {#replicating-from-publish-to-author}

Met sommige functies kunnen gebruikers gegevens invoeren op een publicatie-instantie.

In sommige gevallen, is een type van replicatie die als omgekeerde replicatie wordt bekend, nodig om deze gegevens aan het auteursmilieu terug te keren van waar het aan andere publicatiemilieu&#39;s opnieuw wordt verdeeld. Om veiligheidsredenen moet het verkeer van de publicatie naar de auteursomgeving strikt worden gecontroleerd.

De omgekeerde replicatie gebruikt een agent in het publicatiemilieu die verwijzingen het auteursmilieu. Deze agent plaatst de gegevens in een outbox. Deze outbox wordt aangepast met replicatieluisteraars in het auteursmilieu. De luisteraars onderzoeken de outboxes om het even welke ingevoerde gegevens te verzamelen en dan het zonodig te verspreiden. Dit zorgt ervoor dat het auteursmilieu al verkeer controleert.

In andere gevallen, zoals bij Community-functies (bijvoorbeeld forums, blogs, opmerkingen en revisies), is het moeilijk om de hoeveelheid door de gebruiker gegenereerde inhoud (UGC) die in de publicatieomgeving wordt ingevoerd, op efficiënte wijze te synchroniseren in verschillende AEM gevallen met replicatie.

AEM [Communities](/help/communities/overview.md) gebruikt nooit replicatie voor UGC. In plaats daarvan, vereist de plaatsing voor Gemeenschappen een gemeenschappelijke opslag voor UGC (zie [Community Content Storage](/help/communities/working-with-srp.md)).

### Replicatie - uit het vak {#replication-out-of-the-box}

De wij-kleinhandelswebsite die in een standaardinstallatie van AEM inbegrepen is kan worden gebruikt om replicatie te illustreren.

Om dit voorbeeld te volgen en de standaardreplicatieagenten te gebruiken moet u AEM [installeren ](/help/sites-deploying/deploy.md) met:

* de auteursomgeving op poort `4502`
* de publicatieomgeving op de poort `4503`

>[!NOTE]
>
>Standaard ingeschakeld:
>
>* Medewerkers op auteur: Standaardagent (publiceren)
>
>
Effectief uitgeschakeld (vanaf AEM 6.1):
>
>* Medewerkers op auteur: Reverse Replication Agent (publish_reverse)
>* Medewerkers op publicatie: Reverse Replication (outbox)

>
>
Om de status van of de agent of de rij te controleren gebruik **Tools** console.
>Zie [Uw Replicatieagenten controleren](#monitoring-your-replication-agents).

#### Replicatie (te publiceren auteur) {#replication-author-to-publish}

1. Navigeer naar de ondersteuningspagina in de ontwerpomgeving.
   **https://localhost:4502/content/we-retail/us/en/experience.html** `<pi>`
1. Bewerk de pagina om nieuwe tekst toe te voegen.
1. **Activeer** Pagina om de wijzigingen te publiceren.
1. Open de ondersteuningspagina in de publicatieomgeving:
   **https://localhost:4503/content/we-retail/us/en/experience.html**
1. U kunt nu de wijzigingen zien die u bij de auteur hebt ingevoerd.

Deze replicatie wordt in de auteursomgeving geactiveerd door:

* **Standaard Agent (publiceren)**
Deze agent repliceert inhoud aan het gebrek publiceert instantie.
De details van dit (configuratie en logboeken) kunnen van de console van Hulpmiddelen van het auteursmilieu worden betreden; of:

   `https://localhost:4502/etc/replication/agents.author/publish.html`.

#### Replication Agents - Out of the Box {#replication-agents-out-of-the-box}

De volgende agenten zijn beschikbaar in een standaard AEM installatie:

* [Standaard ](#replication-author-to-publish)
AgentGebruikt voor het herhalen van auteur om te publiceren.

* Dispatcher Flush
Dit wordt gebruikt voor het beheren van het cachegeheugen van Dispatcher. Zie [De Dispatcher Cache van het Authoring Environment](https://helpx.adobe.com/experience-manager/dispatcher/using/page-invalidate.html#invalidating-dispatcher-cache-from-the-authoring-environment) en [De Dispatcher Cache van een het Publiceren Instantie](https://helpx.adobe.com/experience-manager/dispatcher/using/page-invalidate.html#invalidating-dispatcher-cache-from-a-publishing-instance) voor meer informatie ongeldig maken.

* [Omgekeerde ](#reverse-replication-publish-to-author)
replicatieGebruikt voor het herhalen van publiceren aan auteur. Reverse-replicatie wordt niet gebruikt voor functies van Gemeenschappen, zoals forums, blogs en opmerkingen. De optie is in feite uitgeschakeld omdat de Postvak UIT niet is ingeschakeld. Het gebruik van omgekeerde replicatie zou douaneconfiguratie vereisen.

* Statische agent
Dit is een &quot;Agent die een statische vertegenwoordiging van een knoop in het filesystem opslaat.&quot;
Met de standaardinstellingen worden de inhoudspagina&#39;s en de dam-elementen bijvoorbeeld opgeslagen onder `/tmp`, als HTML of in de juiste indeling voor elementen. Zie `Settings` en `Rules` lusjes voor de configuratie.
Dit is aangevraagd zodat de inhoud zichtbaar is wanneer de pagina rechtstreeks bij de toepassingsserver wordt aangevraagd. Dit is een gespecialiseerde agent en (waarschijnlijk) zal niet voor de meeste gevallen worden vereist.

## Replicatieagents - Configuratieparameters {#replication-agents-configuration-parameters}

Wanneer het vormen van een replicatieagent van de console van Hulpmiddelen, zijn vier lusjes beschikbaar binnen de dialoog:

### Instellingen {#settings}

* **Naam**

   Een unieke naam voor de replicatieagent.

* **Beschrijving**

   Een beschrijving van het doel deze replicatieagent zal dienen.

* **Ingeschakeld**

   Wijst erop of de replicatieagent momenteel wordt toegelaten.

   Wanneer de agent **enabled** is zal de rij als worden getoond:

   * **Activeer** wanneer items worden verwerkt.
   * **** Niet beschikbaar wanneer de wachtrij leeg is.
   * **** geblokkeerd wanneer de punten in de rij zijn, maar niet kunnen worden verwerkt; bijvoorbeeld wanneer de ontvangende wachtrij is uitgeschakeld.

* **Type serienummering**

   Het type van rangschikking:

   * **Standaard**: Plaats als de agent automatisch moet worden geselecteerd.
   * **Uitspoelen**: Selecteer dit als de agent moet worden gebruikt voor het leegmaken van de verzendingscache.

* **Vertraging opnieuw proberen**

   De vertraging (wachttijd in milliseconden) tussen twee pogingen, mocht een probleem worden ontmoet.

   Standaard: `60000`

* **Gebruiker-id agent**

   Afhankelijk van het milieu, zal de agent deze gebruikersrekening gebruiken om:

   * de inhoud van de ontwerpomgeving verzamelen en in een pakket plaatsen
   * de inhoud maken en schrijven in de publicatieomgeving

   Laat dit veld leeg om de systeemgebruikersaccount te gebruiken (de account die in sling is gedefinieerd als de beheerdersgebruiker). standaard is dit `admin`).

   >[!CAUTION]
   >
   >Voor een agent op het auteursmilieu *must* heeft leestoegang tot alle wegen die u wilt hebben herhaald.

   >[!CAUTION]
   >
   >Voor een agent op het publicatiemilieu *must* heeft deze rekening creeer/schrijf toegang wordt vereist om de inhoud te herhalen.

   >[!NOTE]
   >
   >Dit kan als mechanisme worden gebruikt om specifieke inhoud voor replicatie te selecteren.

* **Logboekniveau**

   Hiermee bepaalt u het detailniveau dat voor logberichten moet worden gebruikt.

   * `Error`: alleen fouten worden vastgelegd
   * `Info`: fouten, waarschuwingen en andere informatieberichten worden geregistreerd
   * `Debug`: een hoog niveau van detail zal in de berichten, hoofdzakelijk voor zuiveringsdoeleinden worden gebruikt

   Standaard: `Info`

* **Gebruiken voor omgekeerde replicatie**

   Wijst erop of deze agent voor omgekeerde replicatie zal worden gebruikt; Hiermee wordt gebruikersinvoer vanuit de publicatieomgeving geretourneerd naar de auteursomgeving.

* **Alias-update**

   Als u deze optie selecteert, worden aanvragen voor validatie van aliassen of ijdelingspaden naar Dispatcher ingeschakeld. Zie ook [Een Dispatcher Flush Agent](/help/sites-deploying/replication.md#configuring-a-dispatcher-flush-agent) configureren.

#### Vervoer {#transport}

* **URI**

   Dit specificeert het ontvangende servlet bij de doelplaats. Met name kunt u hier de hostnaam (of alias) en het contextpad naar de doelinstantie opgeven.

   Bijvoorbeeld:

   * Een standaardagent kan worden gerepliceerd naar `https://localhost:4503/bin/receive`
   * Een Dispatcher Flush-agent kan worden gerepliceerd naar `https://localhost:8000/dispatcher/invalidate.cache`

   Het hier opgegeven protocol (HTTP of HTTPS) bepaalt de transportmethode.

   Voor de agenten van de Vlek van de Verzender, wordt het bezit van URI gebruikt slechts als u op weg-gebaseerde virtuele gastheeringangen gebruikt om tussen landbouwbedrijven te onderscheiden, gebruikt u dit gebied om het landbouwbedrijf te richten om ongeldig te maken. Zo heeft farm #1 bijvoorbeeld een virtuele host van `www.mysite.com/path1/*` en farm #2 heeft een virtuele host van `www.mysite.com/path2/*`. U kunt een URL van `/path1/invalidate.cache` gebruiken om het eerste landbouwbedrijf te richten en `/path2/invalidate.cache` om het tweede landbouwbedrijf te richten.

* **Gebruiker**

   Gebruikersnaam van de account die moet worden gebruikt voor toegang tot het doel.

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

   Gebruikersnaam van de account die moet worden gebruikt.

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

   Voor een Dispatcher Flush-agent is dit bijna altijd GET en mag het niet worden gewijzigd (POST zou een andere mogelijke waarde zijn).

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
   >Als u AEM in een andere context dan de geadviseerde standaardcontext hebt geïnstalleerd, dan zult u de context in de Kopballen van HTTP moeten registreren. Bijvoorbeeld:
   >`CQ-Handle:/<*yourContext*>{path}`

* **Verbinding sluiten**

   Schakel deze optie in om de verbinding na elk verzoek te sluiten.

* **Time-out voor verbinding**

   Time-out (in milliseconden) die moet worden toegepast wanneer wordt geprobeerd een verbinding tot stand te brengen.

* **Time-out socket**

   Time-out (in milliseconden) die moet worden toegepast wanneer wordt gewacht op verkeer nadat een verbinding tot stand is gebracht.

* **Protocol versie**

   Versie van het protocol; bijvoorbeeld `1.0` voor HTTP/1.0.

#### Triggers {#triggers}

Deze instellingen worden gebruikt om triggers voor geautomatiseerde replicatie te definiëren:

* **Standaard negeren**

   Indien gecontroleerd, wordt de agent uitgesloten van standaardreplicatie; dit betekent dat de code niet wordt gebruikt als een auteur van de inhoud een replicatiehandeling uitvoert.

* **Bij wijziging**

   Hier zal een replicatie door deze agent automatisch teweeggebracht worden wanneer een pagina wordt gewijzigd. Dit wordt hoofdzakelijk gebruikt voor de agenten van de Vlek van de Verzender, maar ook voor omgekeerde replicatie.

* **Bij distribueren**

   Als deze optie is ingeschakeld, wordt alle inhoud die is gemarkeerd voor distributie automatisch door de agent gerepliceerd wanneer deze wordt gewijzigd.

* **On-/Offtime bereikt**

   Dit zal automatische replicatie (om een pagina te activeren of te deactiveren zoals aangewezen) teweegbrengen wanneer de ontijden of de tijden voor een pagina worden bepaald voorkomen. Dit wordt vooral gebruikt voor Dispatcher Flush-middelen.

* **Bij ontvangst**

   Als gecontroleerd, zal de agent herhalen wanneer het ontvangen van replicatiegebeurtenissen.

* **Geen statusupdate**

   Wanneer gecontroleerd zal de agent geen update van de replicatiestatus dwingen.

* **Geen versie**

   Als deze optie is ingeschakeld, wordt het versienummer van geactiveerde pagina&#39;s niet geforceerd.

## Het vormen van uw Agenten van de Replicatie {#configuring-your-replication-agents}

Voor informatie over het aansluiten van replicatieagenten aan de publicatieinstantie die MSSL gebruikt, zie [Replicating Using Mutual SSL](/help/sites-deploying/mssl-replication.md).

### Het vormen van uw Agenten van de Replicatie van het Milieu {#configuring-your-replication-agents-from-the-author-environment}

Van het lusje van Hulpmiddelen in het auteursmilieu kunt u replicatieagenten vormen die in of het auteursmilieu (**Agenten op auteur**) of het publicatiemilieu (**Agenten op publish**) verblijven. De volgende procedures illustreren de configuratie van een agent voor het auteursmilieu, maar kunnen voor beide worden gebruikt.

>[!NOTE]
>
>Wanneer een verzender HTTP- verzoeken om auteur behandelt of instanties publiceert, moet het HTTP- verzoek van de replicatieagent de kopbal van de PAD omvatten. Naast de volgende procedure, moet u de kopbal van het PAD aan de verzender lijst van cliëntkopballen toevoegen. (Zie [/clientheaders (de Kopballen van de Cliënt)](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html#specifying-the-http-headers-to-pass-through-clientheaders). [](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html#specifying-the-http-headers-to-pass-through-clientheaders)


1. Open de tab **Tools** in AEM.
1. Klik **Replication** (linkerdeelvenster om de map te openen).
1. Dubbelklik **Agenten op auteur** (of de linkerzijde of de juiste ruit).
1. Klik de aangewezen agentennaam (die een verbinding) is om gedetailleerde informatie over die agent te tonen.
1. Klik **Bewerken** om het configuratiedialoogvenster te openen:

   ![chlimage_1-22](assets/chlimage_1-22.png)

1. De opgegeven waarden moeten voldoende zijn voor een standaardinstallatie. Als u wijzigingen aanbrengt, klikt u op **OK** om deze op te slaan (zie [Replication Agents - Configuration Parameters](#replication-agents-configuration-parameters) voor meer details van de individuele parameters).

>[!NOTE]
>
>Een standaardinstallatie van AEM specificeert `admin` als gebruiker voor vervoergeloofsbrieven binnen de standaardreplicatieagenten.
>
>Deze moet worden gewijzigd in een sitespecifieke gebruikersaccount voor replicatie met de bevoegdheden om de vereiste paden te repliceren.

### Omgekeerde replicatie configureren {#configuring-reverse-replication}

De omgekeerde replicatie wordt gebruikt om gebruikersinhoud terug te krijgen die op een te publiceren instantie wordt geproduceerd aan een auteursinstantie. Dit wordt doorgaans gebruikt voor functies zoals enquêtes en registratieformulieren.

Om veiligheidsredenen staan de meeste netwerktopologieën geen verbindingen *van* de &quot;Gedemilitariseerde Zone&quot; toe (een subnetwerk dat de externe services toegankelijk maakt voor een niet-vertrouwd netwerk zoals internet).

Aangezien het publiceren milieu gewoonlijk in DMZ is, om inhoud terug naar het auteursmilieu te krijgen moet de verbinding van de auteursinstantie in werking worden gesteld. Dit gebeurt met:

* en *outbox* in het publicatiemilieu waar de inhoud wordt geplaatst.
* een agent (publiceren) in het auteursmilieu dat periodiek outbox voor nieuwe inhoud opiniepeilt.

>[!NOTE]
>
>Voor AEM [Communities](/help/communities/overview.md), wordt de replicatie niet gebruikt voor gebruiker geproduceerde inhoud op een publicatieinstantie. Zie [Community Content Storage](/help/communities/working-with-srp.md).

Hiervoor hebt u het volgende nodig:

**Een omgekeerde replicatieagent in de auteur** environmentThis handelt als actieve component om informatie van outbox in het publicatiemilieu te verzamelen:

Als u omgekeerde replicatie wilt gebruiken dan zorg ervoor dat deze agent wordt geactiveerd.

![chlimage_1-23](assets/chlimage_1-23.png)

**Een omgekeerde replicatieagent in publiceert milieu (een outbox)** Dit is het passieve element aangezien het als &quot;outbox&quot;dienst doet. De input van de gebruiker wordt hier geplaatst, van waar het door de agent in het auteursmilieu wordt verzameld.

![chlimage_1-1](assets/chlimage_1-1.jpeg)

### Replicatie configureren voor meerdere publicatieinstanties {#configuring-replication-for-multiple-publish-instances}

>[!NOTE]
>
>Alleen inhoud wordt gerepliceerd. Gebruikersgegevens worden niet gekopieerd (gebruikers, gebruikersgroepen en gebruikersprofielen).
>
>Schakel [Gebruikerssynchronisatie](/help/sites-administering/sync.md) in om gebruikersgegevens in meerdere publicatieinstanties te synchroniseren.

Op installatie wordt een standaardagent reeds gevormd voor replicatie van inhoud aan een te publiceren instantie die op haven 4503 van localhost loopt.

Om replicatie van inhoud voor een extra te vormen publiceer instantie moet u, een nieuwe replicatieagent creëren en vormen:

1. Open het tabblad **Gereedschappen** in AEM.
1. Selecteer **Replication** en **Agents op auteur** in het linkerdeelvenster.
1. **Nieuw selecteren...**.
1. Stel de **Title** en **Name** in en selecteer **Replication Agent**.
1. Klik **Create** om de nieuwe agent tot stand te brengen.
1. Dubbelklik op het nieuwe agentitem om het configuratievenster te openen.
1. Klik **Edit** - het **de dialoogvakje van de Montages van de Agent** zal openen - **Serialization Type** wordt reeds bepaald als Gebrek, dit moet zo blijven.

   * Op het tabblad **Instellingen**:

      * Activeer **Enabled**.
      * Voer een **Beschrijving** in.
      * Stel **Opnieuw Vertraging** in op `60000`.

      * Laat **Serienummeringstype** ongewijzigd als `Default`.
   * Op het tabblad **Vervoer**:

      * Voer de vereiste URI in voor het nieuwe publicatie-exemplaar; bijvoorbeeld:
         `https://localhost:4504/bin/receive`.

      * Voer de sitespecifieke gebruikersaccount in die voor replicatie wordt gebruikt.
      * U kunt desgewenst andere parameters configureren.


1. Klik **OK** om de instellingen op te slaan.

Vervolgens kunt u de bewerking testen door een pagina in de ontwerpomgeving bij te werken en te publiceren.

De updates verschijnen op alle publicatieinstanties die zoals hierboven zijn gevormd.

Als u problemen ondervindt, kunt u de logboeken op de auteurinstantie controleren. Afhankelijk van het vereiste detailniveau kunt u **Logniveau** ook instellen op `Debug` door het dialoogvenster **Agent-instellingen** als hierboven beschreven te gebruiken.

>[!NOTE]
>
>Dit kan worden gecombineerd met het gebruik van [Agent-gebruikersnaam](#agentuserid) om verschillende inhoud te selecteren voor replicatie naar de afzonderlijke publicatieomgevingen. Voor elke publicatieomgeving:
>
>1. Vorm een replicatieagent voor het herhalen aan dat publicatiemilieu.
>1. Een gebruikersaccount configureren; met de toegangsrechten die zijn vereist voor het lezen van de inhoud die wordt gerepliceerd naar die specifieke publicatieomgeving.
>1. Wijs de gebruikersrekening als **Gebruiker van de Agent ID** voor de replicatieagent toe.

>



### Een Dispatcher Flush-agent {#configuring-a-dispatcher-flush-agent} configureren

De standaardagenten zijn inbegrepen met de installatie. Nochtans, is bepaalde configuratie nog nodig en het zelfde is van toepassing als u een nieuwe agent bepaalt:

1. Open het tabblad **Gereedschappen** in AEM.
1. Klik **Implementatie**.
1. Selecteer **Replication** en **Agents op publish**.
1. Dubbelklik op het item **Dispatcher Flush** om het overzicht te openen.
1. Klik op **Bewerken** - het dialoogvenster **Agent-instellingen** wordt geopend:

   * Op het tabblad **Instellingen**:

      * Activeer **Enabled**.
      * Voer een **Beschrijving** in.
      * Verlaat **Serialization Type** als `Dispatcher Flush`, of plaats het als dusdanig als het creëren van een nieuwe agent.

      * (optioneel) Selecteer **Alias-update** om aanvragen voor validatie van aliassen of ijdelingspaden voor Dispatcher in te schakelen.
   * Op het tabblad **Vervoer**:

      * Voer de vereiste URI in voor het nieuwe publicatie-exemplaar; bijvoorbeeld:
         `https://localhost:80/dispatcher/invalidate.cache`.

      * Voer de sitespecifieke gebruikersaccount in die voor replicatie wordt gebruikt.
      * U kunt desgewenst andere parameters configureren.

   Voor de agenten van de Vlek van de Verzender, wordt het bezit van URI gebruikt slechts als u op weg-gebaseerde virtuele gastheeringangen gebruikt om tussen landbouwbedrijven te onderscheiden, gebruikt u dit gebied om het landbouwbedrijf te richten om ongeldig te maken. Zo heeft farm #1 bijvoorbeeld een virtuele host van `www.mysite.com/path1/*` en farm #2 heeft een virtuele host van `www.mysite.com/path2/*`. U kunt een URL van `/path1/invalidate.cache` gebruiken om het eerste landbouwbedrijf te richten en `/path2/invalidate.cache` om het tweede landbouwbedrijf te richten.

   >[!NOTE]
   >
   >Als u AEM in een andere context dan de geadviseerde standaardcontext hebt geïnstalleerd, dan moet u [Kopballen van HTTP ](#extended) in **Uitgebreide** tabel vormen.

1. Klik **OK** om de wijzigingen op te slaan.
1. Keer terug naar **Tools** tabel, vanaf hier kunt u **Activate** de **Dispatcher Flush** agent (**Agenten op publish**).

De **Dispatcher Flush** replicatieagent is niet actief op auteur. U hebt toegang tot dezelfde pagina in de publicatieomgeving met behulp van de equivalente URI. bijvoorbeeld `https://localhost:4503/etc/replication/agents.publish/flush.html`.

### Toegang tot replicatieagents beheren {#controlling-access-to-replication-agents}

De toegang tot de pagina&#39;s die worden gebruikt om de replicatieagenten te vormen kan worden gecontroleerd door gebruiker en/of groepspaginachtigingen op `etc/replication` knoop te gebruiken.

>[!NOTE]
>
>Het instellen van dergelijke machtigingen heeft geen invloed op gebruikers die inhoud repliceren (bijvoorbeeld via de websiteconsole of de optie sidekick). Het replicatieframework gebruikt niet de &quot;gebruikerssessie&quot; van de huidige gebruiker om toegang te krijgen tot replicatieagents tijdens het repliceren van pagina&#39;s.

### Het vormen van uw Agenten van de Replicatie van CRXDE Lite {#configuring-your-replication-agents-from-crxde-lite}

>[!NOTE]
>
>Het maken van replicatieagents wordt alleen ondersteund in de opslaglocatie `/etc/replication`. Dit is nodig opdat bijbehorende ACLs behoorlijk wordt behandeld. Het creëren van een replicatieagent in een andere plaats van de boom zou tot onbevoegde toegang kunnen leiden.

Diverse parameters van uw replicatieagenten kunnen worden gevormd gebruikend CRXDE Lite.

Als u naar `/etc/replication` navigeert, kunt u de volgende drie knooppunten zien:

* `agents.author`
* `agents.publish`
* `treeactivation`

Twee `agents` houden configuratieinformatie over het aangewezen milieu, en zijn slechts actief wanneer dat milieu loopt. `agents.publish` wordt bijvoorbeeld alleen gebruikt in de publicatieomgeving. Het volgende screenshot toont de publicatieagent in de auteursomgeving, zoals inbegrepen met AEM WCM:

![chlimage_1-24](assets/chlimage_1-24.png)

## Uw replicatieagents {#monitoring-your-replication-agents} controleren

Om een replicatieagent te controleren:

1. Open de tab **Tools** in AEM.
1. Klik **Replication**.
1. Dubbelklik op de koppeling naar agents voor de juiste omgeving (links of rechts); bijvoorbeeld **Agenten op auteur**.

   Het resulterende venster toont een overzicht van al uw replicatieagenten voor het auteursmilieu, met inbegrip van hun doel en status.

1. Klik de aangewezen agentennaam (die een verbinding is) om gedetailleerde informatie over die agent te tonen:

   ![chlimage_1-2](assets/chlimage_1-2.jpeg)

   Hier kunt u:

   * Zie of de agent wordt toegelaten.
   * Zie het doel van eventuele replicaties.
   * Zie of de replicatierij momenteel actief (toegelaten) is.
   * Zie of er items in de wachtrij staan.
   * **** Vernieuwen of  **** wissen om de weergave van wachtrijitems bij te werken; dit helpt u punten te zien ingaan en de rij verlaten.

   * **Logboek van de mening** om tot het logboek van om het even welke acties door de replicatieagent toegang te hebben.
   * **Test** Connection to the target instance.
   * **Indien nodig** opnieuw in de wachtrij plaatsen.

   >[!CAUTION]
   >
   >Gebruik de koppeling &quot;Verbinding testen&quot; niet voor het selectievakje Reverse Replication Outbox op een publicatie-instantie.
   >
   >
   >Als een replicatietest voor een Postbus rij wordt uitgevoerd, om het even welke punten die ouder zijn dan de testreplicatie zullen met elke omgekeerde replicatie opnieuw worden verwerkt.
   >
   >
   >Als dergelijke items al in een wachtrij staan, kunt u ze vinden met de volgende JCR-query voor XPath en moet u ze verwijderen.
   >
   >
   >`/jcr:root/var/replication/outbox//*[@cq:repActionType='TEST']`

## Batchreplicatie {#batch-replication}

De batchreplicatie dupliceert geen afzonderlijke pagina&#39;s of elementen, maar wacht op de eerste drempelwaarde van de twee, op basis van de tijd of grootte, die moeten worden geactiveerd.

Vervolgens worden alle replicatiepunten in een pakket opgenomen, dat vervolgens als één bestand aan de uitgever wordt gerepliceerd.

De uitgever zal alle punten uitpakken, sparen hen en rapport terug aan de auteur.

### Batchreplicatie configureren {#configuring-batch-replication}

1. Ga naar `http://serveraddress:serverport/siteadmin`
1. Druk op het pictogram **[!UICONTROL Tools]** in de bovenzijde van het scherm
1. Ga vanuit de linkerzijnavigatieregel naar **[!UICONTROL Replication - Agents on Author]** en dubbelklik **[!UICONTROL Default Agent]**.
   * U kunt de standaard ook bereiken publiceert replicatieagent door rechtstreeks naar `http://serveraddress:serverport/etc/replication/agents.author/publish.html` te gaan
1. Druk **[!UICONTROL Edit]** knoop boven de replicatierij.
1. Ga in het volgende venster naar het tabblad **[!UICONTROL Batch]**:
   ![batchreplicatie](assets/batchreplication.png)
1. Vorm de agent.

### Parameters {#parameters}

* `[!UICONTROL Enable Batch Mode]` - schakelt batchreplicatiemodus in of uit
* `[!UICONTROL Max Wait Time]` - Maximale wachttijd tot een batchverzoek is gestart, in seconden. De standaardwaarde is 2 seconden.
* `[!UICONTROL Trigger Size]` - Batch-replicatie wordt gestart als deze formaatlimiet

## Aanvullende bronnen {#additional-resources}

Voor meer informatie over het oplossen van problemen, kunt u [het Oplossen van problemen Replicatie](/help/sites-deploying/troubleshoot-rep.md) pagina lezen.