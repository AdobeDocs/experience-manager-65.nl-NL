---
title: Formulier-centric workflow installeren en configureren op OSGi
seo-title: Formulier-centric workflow installeren en configureren op OSGi
description: Installeer en vorm AEM Forms Interactieve Mededelingen om bedrijfscorrespondentie, documenten, verklaringen, voordelenberichten, marketing post, rekeningen, en welkomstkits tot stand te brengen.
seo-description: Installeer en vorm AEM Forms Interactieve Mededelingen om bedrijfscorrespondentie, documenten, verklaringen, voordelenberichten, marketing post, rekeningen, en welkomstkits tot stand te brengen.
uuid: 1ceae822-215a-4b83-a562-4609a09c3a54
topic-tags: installing
discoiquuid: de292a19-07db-4ed3-b13a-7a2f1cd9e0dd
docset: aem65
translation-type: tm+mt
source-git-commit: a18a018181a779b9f48ef3e39c26410a1bc4919b
workflow-type: tm+mt
source-wordcount: '1623'
ht-degree: 0%

---


# Formulier-centric workflow installeren en configureren op OSGi{#installing-and-configuring-forms-centric-workflow-on-osgi}

## Inleiding {#introduction}

Ondernemingen verzamelen en verwerken gegevens van meerdere formulieren, back-endsystemen en andere gegevensbronnen. De verwerking van gegevens omvat toetsings- en goedkeuringsprocedures, herhaalde taken en archivering van gegevens. Een formulier reviseren en converteren naar PDF-document. Wanneer manueel gedaan, kunnen de herhalende taken veel tijd en middelen vergen.

U kunt [Forms-centric workflow gebruiken op OSGi](../../forms/using/aem-forms-workflow.md) om snel adaptieve workflows op basis van formulieren samen te stellen. Deze workflows kunnen u helpen bij het automatiseren van workflows voor revisie en goedkeuring, workflows voor bedrijfsprocessen en andere herhalende taken. Met deze workflows kunt u ook documenten verwerken (PDF-documenten maken, samenstellen, distribueren en archiveren, digitale handtekeningen toevoegen om de toegang tot documenten te beperken, streepjescodes voor formulieren te decoderen en meer) en de ondertekeningsworkflow voor Adobe-handtekeningen gebruiken voor formulieren en documenten.

Nadat de werkstromen zijn ingesteld, kunnen deze handmatig worden geactiveerd om een gedefinieerd proces te voltooien of via programmacode worden uitgevoerd wanneer gebruikers een formulier of interactieve communicatie verzenden. De mogelijkheid is opgenomen in het invoegpakket AEM Forms.

AEM Forms is een krachtig platform op bedrijfsniveau. Forms-centric workflow op OSGi is slechts een van de mogelijkheden van AEM Forms. Voor de volledige lijst van mogelijkheden, zie [Inleiding aan AEM Forms](introduction-aem-forms.md).

>[!NOTE]
>
>Met Forms-centric werkschema op OSGi, kunt u werkschema&#39;s voor diverse taken op de stapel snel bouwen en opstellen OSGi, zonder het moeten het volledige vermogen van het Beheer van het Proces op de stapel van JEE installeren. Zie een [vergelijking](capabilities-osgi-jee-workflows.md) van de Forms-centric AEM Workflows op OSGi en Process Management op JEE om het verschil en de gelijkenissen in de mogelijkheden te leren.
>
>Na de vergelijking, als u verkiest om het vermogen van het Beheer van het Proces op de stapel van JEE te installeren, zie AEM Forms [installeren of van de Verbetering op JEE](/help/forms/home.md) voor gedetailleerde informatie over het installeren van en het vormen van de stapel van JEE en de mogelijkheden van het Beheer van het Proces.

## Implementatietopologie {#deployment-topology}

AEM Forms-invoegtoepassing is een toepassing die op AEM wordt geïmplementeerd. U hebt slechts minimaal één AEM Author- of verwerkingsinstantie (productieauteur) nodig om de Forms-centric workflow op OSGi-functionaliteit uit te voeren. Een verwerkingsinstantie is een [geharde AEM Author](/help/forms/using/hardening-securing-aem-forms-environment.md) -instantie. Voer geen daadwerkelijke ontwerpbewerkingen uit, zoals het maken van workflows of adaptieve formulieren, op de auteur van de productie.

De volgende topologie is indicatieve topologie om AEM Forms Interactieve Mededelingen, het Beheer van de Correspondentie, AEM Forms gegevens vangen, en vorm-Centric werkschema op mogelijkheden in werking te stellen OSGi. Voor gedetailleerde informatie over de topologie, zie [Architectuur en plaatsingstopologieën voor AEM Forms](/help/forms/using/aem-forms-architecture-deployment.md).

![aanbevolen topologie](assets/recommended-topology.png)

AEM Forms vormen-centric werkschema op OSGi stelt AEM Inbox en het Maken UI van het Model van het Werkschema van AEM op de Instanties van de Auteur van AEM Forms in werking.

## Systeemvereisten {#system-requirements}

>[!NOTE]
>
>Ga verder met de sectie [Volgende stappen](../../forms/using/installing-configuring-forms-centric-workflow-on-osgi.md#next-steps) van het document als u al AEM Forms op OSGi hebt geïnstalleerd, zoals uitgelegd in het artikel Mogelijkheden [voor het](../../forms/using/installing-configuring-aem-forms-osgi.md) installeren en configureren van gegevensvastlegging.

Voordat u begint met het installeren en configureren van Forms-centric Workflow op OSGi, moet u ervoor zorgen dat:

* Hardware- en software-infrastructuur is aanwezig. Raadpleeg de [technische vereisten](/help/sites-deploying/technical-requirements.md)voor een gedetailleerde lijst met ondersteunde hardware en software.

* Het installatiepad van de AEM-instantie bevat geen spaties.
* Er wordt een AEM-instantie uitgevoerd. In AEM-terminologie is een &quot;instantie&quot; een kopie van AEM die wordt uitgevoerd op een server in de auteur- of publicatiemodus. U hebt ten minste één AEM-instantie (Auteur of Verwerking) nodig om een op Forms gerichte workflow op OSGi uit te voeren:

   * **Auteur**: Een AEM-instantie die wordt gebruikt om inhoud te maken, te uploaden en te bewerken en om de website te beheren. Wanneer de inhoud gereed is om live te gaan, wordt deze gekopieerd naar de publicatie-instantie.
   * **Verwerking:** Een verwerkingsinstantie is een [geharde AEM Author](/help/forms/using/hardening-securing-aem-forms-environment.md) -instantie. Nadat u de installatie hebt uitgevoerd, kunt u een instantie Auteur instellen en deze lastiger maken.

   * **Publiceren**: Een AEM-instantie die de gepubliceerde inhoud via internet of een intern netwerk aan het publiek levert.

* Er wordt voldaan aan de geheugenvereisten. AEM Forms-invoegpakket vereist:

   * 15 GB tijdelijke ruimte voor op Microsoft Windows gebaseerde installaties.
   * 6 GB tijdelijke ruimte voor UNIX-installaties.

* Extra eisen voor op UNIX gebaseerde systemen: Als u het op UNIX gebaseerde besturingssysteem gebruikt, installeert u de volgende pakketten via de installatiemedia van het desbetreffende besturingssysteem.

<table>
 <tbody>
  <tr>
   <td>uitzetten</td>
   <td>libxcb</td>
   <td>freetype</td>
   <td>libXau</td>
  </tr>
  <tr>
   <td>libSM</td>
   <td>zlib</td>
   <td>libICE</td>
   <td>libuuid</td>
  </tr>
  <tr>
   <td>glibc</td>
   <td>libXext</td>
   <td><p>nss-softokn-freebl</p> </td>
   <td>fontconfig</td>
  </tr>
  <tr>
   <td>libX11</td>
   <td>libXrender</td>
   <td>libXrandr</td>
   <td>libXinerama</td>
  </tr>
 </tbody>
</table>

## AEM Forms-invoegtoepassing installeren {#install-aem-forms-add-on-package}

AEM Forms-invoegtoepassing is een toepassing die op AEM wordt geïmplementeerd. Het pakket bevat Forms-centric workflow voor OSGi en andere mogelijkheden. Voer de volgende stappen uit om het invoegpakket te installeren:

1. Open [Softwaredistributie](https://experience.adobe.com/downloads). U hebt een Adobe ID nodig om u aan te melden bij de Softwaredistributie.
1. Tik **[!UICONTROL Adobe Experience Manager]** beschikbaar in het koptekstmenu.
1. In het **[!UICONTROL Filters]** gedeelte:
   1. Selecteer een optie **[!UICONTROL Forms]** in de **[!UICONTROL Solution]** vervolgkeuzelijst.
   2. Selecteer de versie en typ voor het pakket. U kunt de **[!UICONTROL Search Downloads]** optie ook gebruiken om de resultaten te filteren.
1. Tik op de pakketnaam die van toepassing is op het besturingssysteem, selecteer **[!UICONTROL Accept EULA Terms]** en tik op **[!UICONTROL Download]**.
1. Open [Package Manager](https://docs.adobe.com/content/help/en/experience-manager-65/administering/contentmanagement/package-manager.html) en klik **[!UICONTROL Upload Package]** om het pakket te uploaden.
1. Selecteer het pakket en klik **[!UICONTROL Install]**.

   U kunt het pakket ook downloaden via de directe koppeling in het [AEM Forms-releaseartikel](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) .

1. Nadat het pakket is geïnstalleerd, wordt u gevraagd om de AEM-instantie opnieuw te starten. **Start de server niet onmiddellijk opnieuw.** Alvorens de server van AEM Forms tegen te houden, wacht tot de ServiceEvent REGISTERED en ServiceEvent niet GEREGISTREERDE berichten ophouden verschijnen in het [AEM-Installatie-Folder]/crx-quickstart/logs/error.log- dossier en het logboek stabiel is.
1. Herhaal stap 1-7 voor alle instanties Auteur en Publiceren.

## Configuratie na installatie {#post-installation-configurations}

AEM Forms hebben een paar verplichte en optionele configuraties. De verplichte configuraties omvatten het vormen bibliotheken BouncyCastle en serialization agent. De optionele configuraties zijn het configureren van dispatcher en Adobe Target.

### Verplichte configuraties na installatie {#mandatory-post-installation-configurations}

#### RSA- en BouncyCastle-bibliotheken configureren  {#configure-rsa-and-bouncycastle-libraries}

Voer de volgende stappen op alle Auteur uit en publiceer instanties om de bibliotheken op te starten afvaardigen:

1. Stop de onderliggende AEM-instantie.
1. Open de [AEM-installatiemap]\crx-quickstart\conf\sling.properties.

   Als u de [AEM-installatiemap]\crx-quickstart\bin\start.bat hebt gebruikt om AEM te starten, bewerkt u de sling.properties op de locatie [AEM_root]\crx-quickstart\.

1. Voeg de volgende eigenschappen toe aan het bestand sling.properties:

   ```
   sling.bootdelegation.class.com.rsa.jsafe.provider.JsafeJCE=com.rsa.*
   sling.bootdelegation.class.org.bouncycastle.jce.provider.BouncyCastleProvider=org.bouncycastle.*
   ```

1. Sla het bestand op, sluit het en start de AEM-instantie.
1. Herhaal stap 1-4 voor alle instanties Auteur en Publiceren.

#### Vorm de rangschikkingsagent {#configure-the-serialization-agent}

Voer de volgende stappen uit op alle instanties Auteur en Publish om het pakket aan de lijst van gewenste personen toe te voegen:

1. Open AEM Configuration Manager in een browservenster. De standaard-URL is https://&#39;[server]:[port]&#39;/system/console/configMgr.
1. Zoek en open Configuratie van de Firewall van de **Deserialization**.
1. Voeg het pakket **sun.util.agenda** toe aan het veld **lijst van gewenste personen** . Klik op Opslaan.
1. Herhaal stap 1-3 voor alle instanties Auteur en Publiceren.

### Optionele configuraties na installatie {#optional-post-installation-configurations}

#### Dispatcher configureren {#configure-dispatcher}

Dispatcher is een hulpprogramma voor het in cache plaatsen en taakverdeling voor AEM. AEM Dispatcher helpt ook de AEM-server te beschermen tegen aanvallen. U kunt de beveiliging van uw AEM-instantie verhogen door de Dispatcher in combinatie met een webserver op bedrijfsniveau te gebruiken. Als u [Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html)gebruikt, voert u de volgende configuraties voor AEM Forms uit:

1. Toegang voor AEM Forms configureren:

   Open het bestand dispatcher.any voor bewerking. Navigeer naar de filtersectie en voeg het volgende filter toe aan de filtersectie:

   `/0025 { /type "allow" /glob "* /bin/xfaforms/submitaction*" } # to enable AEM Forms submission`

   Sla het bestand op en sluit het. Raadpleeg de documentatie bij [Dispatcher voor meer informatie over filters](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html).

1. Configureer de referentiefilterservice:

   Meld u als beheerder aan bij het configuratiebeheer van Apache Felix. De standaard-URL van de configuratiemanager is https://&#39;server&#39;:[port_number]/system/console/configMgr. Selecteer in het menu **Configuraties** de optie **Filter** Apache-schuifverwijzing. Voer in het veld Hosts toestaan de hostnaam van de verzender in om het als referentie toe te staan en klik op **Opslaan**. The format of the entry is `https://'[server]:[port]'`.

#### Cache configureren {#configure-cache}

Caching is een mechanisme om gegevenstoegang te verkorten, latentie te verminderen, en input/output (I/O) snelheden te verbeteren. In de cache van adaptieve formulieren worden alleen HTML-inhoud en JSON-structuur van een adaptief formulier opgeslagen zonder dat vooraf ingevulde gegevens worden opgeslagen. Hierdoor wordt de tijd die nodig is om een adaptief formulier te genereren, verkort.

* Als u de cache voor adaptieve formulieren gebruikt, gebruikt u de [AEM Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html) om clientbibliotheken (CSS en JavaScript) van een adaptief formulier in cache te plaatsen.
* Zorg tijdens het ontwikkelen van aangepaste componenten dat de cache van adaptieve formulieren uitgeschakeld blijft op de server die voor ontwikkeling wordt gebruikt.

Voer de volgende stappen uit om de cache voor adaptieve formulieren te configureren:

1. Ga naar AEM webconsoleconfiguratiebeheer op `https://'[server]:[port]'/system/console/configMgr`.
1. Klik op **Adaptive Form Configuration Service** om de configuratiewaarden ervan te bewerken. Geef in het dialoogvenster Configuratiewaarden bewerken het maximumaantal formulieren of documenten op dat een instantie van de AEM Forms-server in cache kan plaatsen in het veld **Aantal adaptieve formulieren** . De standaardwaarde is 100. Click **Save**.

   >[!NOTE]
   >
   >Als u de cache wilt uitschakelen, stelt u de waarde in het veld Aantal adaptieve formulieren in op **0**. De cache wordt opnieuw ingesteld en alle formulieren en documenten worden uit de cache verwijderd wanneer u de cachemonfiguratie uitschakelt of wijzigt.

#### Adobe-ondertekening configureren {#configure-adobe-sign}

Met Adobe Sign kunnen workflows voor e-handtekeningen worden gebruikt voor adaptieve formulieren. E-handtekeningen verbeteren workflows om documenten te verwerken voor juridische documenten, verkoop, salarisadministratie, personeelsbeheer en nog veel meer gebieden.

In een standaardworkflow met Adobe Sign and Forms-centric bij OSGi-scenario vult een gebruiker een adaptief formulier in om een **aanvraag voor een service** in te dienen. Bijvoorbeeld een creditcardaanvraag en een burgerservicepakket. Wanneer een gebruiker het aanvraagformulier invult, verzendt en ondertekent, wordt een workflow voor goedkeuring/afwijzing gestart. Het servicebureau evalueert de toepassing in AEM Inbox en gebruikt Adobe Sign om de toepassing elektronisch te ondertekenen. Als u vergelijkbare workflows voor elektronische handtekeningen wilt inschakelen, kunt u Adobe Sign with AEM Forms integreren.

Als u Adobe Sign with AEM Forms wilt gebruiken, [integreert u Adobe Sign with AEM Forms](../../forms/using/adobe-sign-integration-adaptive-forms.md).

## Volgende stappen {#next-steps}

U hebt een omgeving geconfigureerd voor het gebruik van Forms-centric Workflow op OSGi-mogelijkheden. De volgende stappen voor het gebruik van de mogelijkheid zijn:

* [Forms-centric workflow gebruiken op OSGi](../../forms/using/aem-forms-workflow.md)
* [Referentie workflowstap](/help/sites-developing/workflows-step-ref.md)
* [Nabewerking van brieven en interactieve communicatie](../../forms/using/submit-letter-topostprocess.md)

