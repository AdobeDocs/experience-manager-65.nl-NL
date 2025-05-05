---
title: Integratie met best practices van Adobe Creative Cloud
description: De beste praktijken om  [!DNL Adobe Experience Manager]  met  [!DNL Adobe Creative Cloud]  te integreren om de werkschema's van de activaoverdracht te stroomlijnen en hoge inhoudssnelheid te bereiken.
contentOwner: AG
mini-toc-levels: 1
role: User, Admin
feature: Collaboration,Adobe Asset Link,Desktop App
exl-id: c7d589a3-1c5f-4ff0-879e-15e1c556f6dc
hide: true
solution: Experience Manager, Experience Manager Assets
source-git-commit: a144f7cc75b1a5cdb45d2aaf90e87013ac68a431
workflow-type: tm+mt
source-wordcount: '3173'
ht-degree: 9%

---

# [!DNL Adobe Experience Manager] en [!DNL Creative Cloud] best practices voor integratie {#aem-and-creative-cloud-integration-best-practices}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [ klik hier ](https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-service/content/assets/manage/aem-cc-integration-best-practices) |
| AEM 6,5 | Dit artikel |

[!DNL Adobe Experience Manager Assets] is een DAM-oplossing (Digital Asset Management) die in [!DNL Adobe Creative Cloud] kan worden geïntegreerd om DAM-gebruikers te helpen met creatieve teams samen te werken en de samenwerking bij het maken van inhoud te stroomlijnen.

[!DNL Adobe Creative Cloud] biedt creatieve teams een ecosysteem van oplossingen en services om hen te helpen digitale elementen te maken. Hieronder vallen desktoptoepassingen en mobiele toepassingen, cloudservices zoals opslag met desktopsynchronisatie of webervaring, en marketinglocaties zoals [!DNL Adobe Stock] .

Lees verder om te weten welke integraties u kunt kiezen tussen desktop en DAM op bedrijfsniveau op basis van uw gebruiksscenario en wat de bijbehorende beste werkwijzen zijn voor de verbindingsworkflows.

>[!NOTE]
>
>[!DNL Experience Manager] naar [!DNL Creative Cloud] delen van mappen is afgekeurd en wordt niet langer behandeld in deze handleiding. De Adobe adviseert gebruikend nieuwere mogelijkheden zoals [ de Verbinding van Activa van de Adobe ](https://helpx.adobe.com/nl/enterprise/using/adobe-asset-link.html) of [ Desktop app van de Experience Manager ](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/troubleshoot.html?lang=nl-NL) om creatieve gebruiker van toegang tot activa te voorzien die in [!DNL Experience Manager] worden beheerd.

## Collaboration-behoeften van creatieve, marketers- en DAM-gebruikers {#collaboration-needs-of-creatives-marketers-and-dam-users}

| Vereisten | Hoofdletters gebruiken | Betrokken oppervlakken |
|---|---|---|
| Ervaring voor creatieve producten op desktopcomputers vereenvoudigen | Toegang tot middelen van een DAM ([!DNL Experience Manager Assets]) stroomlijnen voor creatieve professionals, of meer in het algemeen gebruikers op desktopcomputers die werken in toepassingen voor het maken van native elementen. Ze hebben een eenvoudige en eenvoudige manier nodig om wijzigingen in [!DNL Experience Manager] te detecteren, te gebruiken (openen), te bewerken en op te slaan en nieuwe bestanden te uploaden. | Windows- of Mac-bureaublad; [!DNL Creative Cloud] apps |
| Middelen van hoge kwaliteit en gebruiksklaar bieden vanuit [!DNL Adobe Stock] | Marketers helpen het proces voor het maken van inhoud te versnellen door hulp te bieden bij het aanschaffen en detecteren van bedrijfsmiddelen. Creatieve professionals gebruiken de goedgekeurde middelen direct vanuit hun creatieve gereedschappen. | [!DNL Experience Manager Assets]; [!DNL Adobe Stock] Marketplace; metagegevensvelden |
| Elementen distribueren en delen door organisaties | De interne afdelingen/de lokale takken en de externe partners, de distributeurs, en de agentschappen gebruiken de goedgekeurde activa die door de ouderorganisatie worden gedeeld. De organisatie wil de gemaakte middelen veilig en naadloos delen voor breder hergebruik. | Brand Portal, Commentaar voor het delen van bedrijfsmiddelen |

## Adobe biedt ondersteuning voor de behoefte aan samenwerking {#adobe-offerings-to-support-the-collaboration-need}

| Waardevoorstel voor de betreffende personen | Adobe aanbieden | Betrokken oppervlakken |
|---|---|---|
| Creatieve gebruikers detecteren elementen vanuit [!DNL Experience Manager] , openen en gebruiken deze, bewerken en uploaden wijzigingen in [!DNL Experience Manager] en uploaden nieuwe bestanden naar [!DNL Experience Manager] zonder [!DNL Creative Cloud] -apps te verlaten. | [ de Verbinding van Activa van de Adobe ](https://helpx.adobe.com/nl/enterprise/using/adobe-asset-link.html) | [!DNL Adobe Photoshop] , [!DNL Adobe Illustrator] en [!DNL Adobe InDesign] . |
| Zakelijke gebruikers vereenvoudigen het openen en gebruiken van middelen, het bewerken en uploaden van wijzigingen in [!DNL Experience Manager] en het uploaden van nieuwe bestanden naar [!DNL Experience Manager] vanuit de bureaubladomgeving. Ze gebruiken een algemene integratie om elk elementtype in de native bureaubladtoepassing te openen, inclusief niet-Adobe toepassingen. | [ Desktop app van de Experience Manager ](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=nl-NL) | [!DNL Experience Manager] bureaubladtoepassing op Windows- en Mac-bureaublad |
| Marketers en zakelijke gebruikers detecteren, voorvertonen, licentiëren en opslaan, en beheren de [!DNL Adobe Stock] -middelen vanuit [!DNL Experience Manager] . Gelicentieerde en opgeslagen elementen bieden geselecteerde [!DNL Adobe Stock] metagegevens voor een beter beheer. | [ Experience Manager en de integratie van Adobe Stock ](aem-assets-adobe-stock.md) | [!DNL Experience Manager] webinterface |

Dit artikel richt zich hoofdzakelijk op de eerste twee aspecten van de samenwerkingsbehoeften. Distributie en sourcing van assets op schaal wordt kort als gebruiksscenario genoemd. Overweeg Adobe Brand Portal of Asset Share Commons voor dergelijke oplossingen. De afwisselende oplossingen zoals [ Brand Portal ](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/home.html?lang=nl-NL), oplossingen die kunnen worden gebouwd gebaseerd op [ de Commons van het Aandeel van het Activa ](https://adobe-marketing-cloud.github.io/asset-share-commons/) componenten, [ het Aandeel van de Verbinding ](/help/assets/link-sharing.md), gebruikend [ Experience Manager Assets ](/help/assets/manage-assets.md) zou moeten worden herzien gebaseerd op specifiek vereiste.

![ de verbindingen van het Creative Cloud voor Experience Manager, besluit welk vermogen te gebruiken ](assets/creative-connections-aem.png)

### Toewijzing van gebruiksgevallen en Adobe-oplossingen {#mapping-of-use-cases-and-adobe-solutions}

<!-- TBD: Add some info about XD integration and possibly info about DA v2.0.
-->

| Hoofdletters gebruiken | [!DNL Adobe Asset Link] | [!DNL Experience Manager] bureaubladtoepassing | Opmerkingen/andere oplossingen |
|---|---|---|---|
| Detecteren - door DAM-mappen bladeren | Ja | [!DNL Experience Manager] Webinterface- en desktopacties | |
| Discover - toegang tot DAM-verzamelingen | Ja | [!DNL Experience Manager] Webinterface- en desktopacties | |
| Discover - zoek naar middelen van DAM | Ja | [!DNL Experience Manager] Webinterface- en desktopacties | |
| Gebruiken - element openen | Ja | Ja | [ Open van de interface van het Web ](manage-assets.md#previewing-assets) of van Vinder |
| Gebruiken - element van DAM in een document plaatsen | Ja - insluiten | Ja - koppelen of insluiten | [!DNL Experience Manager] biedt toegang tot elementen als bestanden op het lokale bestandssysteem. Deze koppelingen in de native apps worden weergegeven door lokale paden. |
| Bewerken - openen voor bewerking | Ja, uitchecken, actie | Ja - Handeling openen (in netwerkshare) | [ Controle-uit in AAL ](https://helpx.adobe.com/nl/enterprise/using/manage-assets-using-adobe-asset-link.html) bewaart de activa aan de creatieve rekening van de wolkenopslag van de gebruiker (die door Creative Cloud app wordt gesynchroniseerd) door gebrek. |
| Bewerken - werk wordt uitgevoerd buiten DAM | Ja - Asset beschikbaar in de opslagaccount van het Creative Cloud van de gebruiker gesynchroniseerd met desktop. | Ja | |
| Bewerken - wijzigingen uploaden | Ja - [ Controle-in actie ](https://helpx.adobe.com/nl/enterprise/using/manage-assets-using-adobe-asset-link.html) met facultatieve commentaar | Ja | |
| Uploaden - één bestand | Ja - het actieve document wordt geüpload | Ja | [ uploadt via Webinterface ](manage-assets.md#uploading-assets) |
| Uploaden - meerdere bestanden / hiërarchische mapstructuren | Nee | Ja | [ uploadt via Webinterface ](manage-assets.md#uploading-assets) of via douane scripting of hulpmiddel. |
| Diverse - gebruiker en aanmelding | Gebruikers van Creatives Cloud die zich hebben aangemeld bij de desktop-app van het Creative Cloud, worden herkend (SSO) | [!DNL Experience Manager] gebruiker en referenties | Gebruikers van beide oplossingen tellen mee voor de [!DNL Experience Manager] gebruikersquota. |
| Diverse - netwerk en toegang | Toegang van bureaublad van gebruiker tot [!DNL Experience Manager] -implementatie via netwerk vereist | Toegang van bureaublad van gebruiker tot [!DNL Experience Manager] -implementatie via netwerk vereist | [!DNL Adobe Asset Link] deelt de omgeving van de netwerkproxy niet. |
| Misc - Grote aantallen activa migreren | Nee | Nee | [ de migratiegids van Assets ](assets-migration-guide.md) |

Om het gebruik van middelen te steunen, zouden andere oplossingen moeten worden overwogen:

* [ Brand Portal ](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/home.html?lang=nl-NL) voor een configureerbare, toe:voegen-op SaaS aan [!DNL Experience Manager Assets] om activa te publiceren.
* De oplossingen van de douane worden gecreeerd gebaseerd op [&#128279;](https://adobe-marketing-cloud.github.io/asset-share-commons/) de codebasis van het Aandeel van activa 0&rbrace;.
* [!DNL Experience Manager] [ verbindingsaandeel ](/help/assets/link-sharing.md) om activa te delen op bestelling gebruikend verbindingen.
* [ het Webinterface van Experience Manager Assets ](/help/assets/manage-assets.md) met gebieden voor externe partijen die door [!DNL Experience Manager] worden beveiligd toegangsbeheeropstelling en met noodzakelijke aanpassingen van IT/netwerkconfiguratie, die deze externe gebruikers toegang geven tot [!DNL Experience Manager].

## Belangrijkste concepten en gebruiksgevallen {#key-concepts-and-use-cases}

### Verklarende woordenlijst {#glossary-of-common-terms}

* **Werk in uitvoering of creatief werk in uitvoering (WIP):** Een fase in de levenscyclus van assets waarbij een asset meerdere wijzigingen ondergaat en doorgaans nog niet klaar is om te worden gedeeld met grotere teams.
* **creatief-klaar activa:** [!DNL Assets] die klaar zijn om met een breder team te worden gedeeld, of door het creatieve team voor het delen met marketing of teams LOB geselecteerd of goedgekeurd zijn.
* **Goedkeuring van assets:** Het goedkeuringsproces dat wordt uitgevoerd voor assets die reeds naar DAM zijn geüpload, en dat typisch merkgoedkeuringen, wettelijke goedkeuringen, enz. omvat.
* **Definitief activa:** activa die door alle goedkeuringen/meta-gegevens het etiketteren zijn gegaan en klaar om door het bredere team zijn te worden gebruikt. Een dergelijke asset wordt opgeslagen in DAM en beschikbaar gesteld aan alle (geïnteresseerde) gebruikers. Deze kan in marketingkanalen of door creatieve teams worden gebruikt om ontwerpen te maken.
* **Kleine activa update/verandering:** een snelle en kleine verandering in een digitaal middel. Deze wordt vaak uitgevoerd als reactie op een retoucheerverzoek of een verzoek om kleine bewerkingen, een assetrevisie of goedkeuring (bijvoorbeeld om de positie te wijzigen, de tekstgrootte te wijzigen, de verzadiging/helderheid en kleur aan te passen, enz.).
* **Belangrijke activa update/verandering:** een verandering in een digitaal middel dat behoorlijk werk vereist, en soms over een langere periode moet worden gedaan. Dit omvat doorgaans meerdere wijzigingen. De asset moet tijdens het bijwerken meerdere keren worden opgeslagen. De belangrijkste assetupdates leiden er doorgaans toe dat de asset een WIP-status krijgt.
* **DAM:** Beheer van digitale assets. In dit document is dit gelijk aan [!DNL Experience Manager Assets] , tenzij anders vermeld.
* **Creatieve gebruiker:** Een creatieve professional die digitale assets maakt met Creative Cloud-apps en -services. In sommige gevallen is een creatieve gebruiker lid van een creatief team dat mogelijk Creative Cloud gebruikt, maar geen digitale assets maakt (zoals een creatieve directeur of een creatieve teammanager).
* **DAM-gebruiker:** Een typische gebruiker van een DAM-systeem. Afhankelijk van de organisatie, kan een gebruiker DAM een marketing of een niet-marketing gebruiker, bijvoorbeeld, een lijn-van-Bedrijfs (LOB) gebruiker, bibliothecaris, verkooppersoon, etc. zijn.

### Overwegingen bij het gebruik van [!DNL Experience Manager] en [!DNL Creative Cloud] integratie {#considerations-when-using-aem-and-creative-cloud-integration}

* Zie [ Desktop app beste praktijken ](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/troubleshoot.html?lang=nl-NL#best-practices-to-prevent-troubles)
* Zie [ de integratie van Adobe Stock ](aem-assets-adobe-stock.md)
* Zie {de Verbinding van Activa van 0} Adobe [&#128279;](https://helpx.adobe.com/nl/enterprise/using/adobe-asset-link.html)

Dit is een korte samenvatting van aanbevolen procedures voor [!DNL Experience Manager] en [!DNL Creative Cloud] integratie. Lees de rest van dit document voor een gedetailleerd begrip hiervan.

* **voor creatieve gebruikers, die in Photoshop, InDesign, of Illustrator werken:** De Verbinding van de Activa van de Adobe verstrekt de beste gebruikerservaring, met inbegrip van schone behandeling van het Werk-in-lopend op activa die uit [!DNL Experience Manager] worden gecontroleerd.
* **voor het vereenvoudigen van toegang tot activa van Desktop voor om het even welk generisch dossierformaat of toepassing:** gebruik [!DNL Experience Manager] Desktop app.
* **Begrijp waarom en wanneer om activa in DAM op te slaan:** Updates die aan het bredere team in uw organisatie ter beschikking moeten worden gesteld.
* **Houd rekening met het volume van de gedeelde assets:** Als u gebruikmaakt van assetdistributie, kunnen governance en beveiliging de belangrijkste aspecten zijn. Overweeg om tools te gebruiken die bedoeld zijn om governance en beveiliging op grote schaal toe te passen, zoals de Brand Portal.
* **De levenscyclus van assets begrijpen:** Begrijp hoe assets in uw organisatie worden verwerkt door verschillende teams
* **Correct en regelmatig opslaan van assets:** Adobe Asset Link doet dit voor u met PS, AI, ID. Voer voor andere toepassingen geen actieve taken uit in toegewezen/gedeelde map tenzij u alle wijzigingen in DAM nodig hebt

### Toegang tot [!DNL Adobe Stock] elementen van [!DNL Assets] {#access-to-adobe-stock-assets-from-aem-assets}

[ de integratie van de Experience Manager en van Adobe Stock ](/help/assets/aem-assets-adobe-stock.md) voorziet [!DNL Experience Manager] gebruikers van de capaciteit om, activa van [!DNL Adobe Stock] in [!DNL Experience Manager] te zoeken, te voorproef, vergunning te geven en te bewaren. In licentie gegeven en opgeslagen [!DNL Stock] -elementen hebben [!DNL Stock] -metagegevens geselecteerd, die kunnen worden gebruikt om met extra filters naar deze elementen te zoeken.

Een paar belangrijke punten over deze integratie:

* Wanneer elementen uit Adobe stock worden opgeslagen naar [!DNL Experience Manager] , worden ze een gewone [!DNL Assets] , met binair opgeslagen naar de [!DNL Experience Manager] repository. Sommige metagegevens die betrekking hebben op [!DNL Adobe Stock] , worden voor het element opgeslagen in [!DNL Experience Manager] . Als dit niet het geval is, ziet het innameproces er hetzelfde uit als voor andere bestanden. Als slimme tags bijvoorbeeld actief zijn, worden de tags bij het opslaan aan deze elementen toegevoegd.
* Het middel dat wordt opgeslagen naar [!DNL Experience Manager] is een kopie en geen koppeling terug naar [!DNL Adobe Stock] .

**Werken met elementen die zijn opgeslagen van [!DNL Adobe Stock] naar [!DNL Experience Manager] in[!DNL Creative Cloud]** . Deze integratie is onafhankelijk van [!DNL Adobe Asset Link] , maar [!DNL Adobe Asset Link] herkent deze elementen die op die manier zijn opgeslagen vanuit [!DNL Stock] en geeft aanvullende metagegevens en een [!DNL Adobe Stock] logo op deze elementen weer in de [!DNL Adobe Asset Link] extensie-interface in [!DNL Photoshop] , [!DNL Illustrator] of [!DNL InDesign] . De bestanden zijn beschikbaar voor bladeren, openen, enzovoort, omdat het normale elementen zijn wanneer ze worden opgeslagen in [!DNL Experience Manager] .
Creatieve gebruikers die werken in [!DNL Creative Cloud] -apps met een [!DNL Adobe Asset Link] -extensie, hebben niet alleen toegang tot middelen met een licentie van [!DNL Adobe Stock] tot [!DNL Experience Manager] , maar kunnen ook het deelvenster [!DNL Creative Cloud] Bibliotheken gebruiken om [!DNL Adobe Stock] -elementen te zoeken, voor te vertonen en te licentiëren.
[!DNL Assets] van [!DNL Adobe Stock] licensed and saved into [!DNL Experience Manager] worden beschikbaar voor de bredere teams die [!DNL Experience Manager Assets] -implementatie gebruiken, terwijl creatieve licentieelementen van [!DNL Adobe Stock] via het deelvenster [!DNL Creative Cloud] Bibliotheken deze alleen standaard beschikbaar maken in hun [!DNL Creative Cloud] -account.

<!-- 
TBD: A condensed version of the below content is better placed in the Adobe DAM introduction article.
-->

## Elementen opslaan in een DAM {#about-storing-assets-in-a-dam}

Om een efficiënte werkstroom tussen creatieve en marketing/lijn-van-zaken (LOB) teams te ontwerpen en de beste steunmogelijkheden te kiezen, is het belangrijk om te begrijpen wanneer en waarom de activa in DAM worden opgeslagen.

### Waarom elementen zijn opgeslagen in DAM {#why-assets-are-stored-in-dam}

Door middelen in DAM op te slaan, zijn ze gemakkelijk toegankelijk en te vinden. Het zorgt ervoor dat de activa door talrijke gebruikers over de organisatie of het ecosysteem kunnen worden gebruikt, die partners, klanten, etc. omvat.

De meeste organisaties kiezen ervoor om activa slechts op te slaan die voor de stroomafwaartse marketing/LOB processen relevant zijn (het publiceren aan kanalen zoals Webkanaal via [!DNL Experience Manager Sites] of andere kanalen die door Adobe Experience Cloud - Marketing Cloud, Advertising Cloud worden gediend, en door Analytics Cloud worden gemeten, die aan gebruikers/partners, etc. verstrekken). Bovendien slaan organisaties activa op die aan een overzicht/goedkeuringsprocedure in DAM kunnen worden onderworpen. Op deze manier slaat DAM vooral activa op die een grote kans hebben om te worden gebruikt, en vermijdt het opslaan van niet-actieve activa.

De opslag van activa is ook onderworpen aan technische overwegingen en middelgebruik. DAM verleent de extra diensten rond opgeslagen activa, met inbegrip van het halen van meta-gegevens, het versioning, het produceren van voorproeven/het transcoderen, het beheren van verwijzingen, en het toevoegen van toegangsbeheerinformatie. Deze diensten verbruiken extra tijd en infrastructuurmiddelen.

Vaak is het niet wenselijk om alle elementen en updates op te slaan. Bijvoorbeeld, als de updates aan specifieke activa van slechte kwaliteit zijn en bovenmatige middelen verbruiken, kunnen de activa niet in DAM worden opgeslagen.

#### Wanneer elementen zijn opgeslagen in DAM {#when-assets-are-stored-in-dam}

Creatieve teams (en organisaties) zijn gewoonlijk niet geïnteresseerd in het opslaan van middelen in elke fase van de levenscyclus van de middelen. In de volgende gevallen worden bijvoorbeeld geen elementen opgeslagen:

* Assets dat nog moet worden afgerond of moet worden getest.
* Assets die de beoordelingscyclus voor creatieve/interne teams niet doorstaat.
* Vergeleken met de middelen in kwestie, heeft het team betere kandidaten om hun werk aan externe teams te vertegenwoordigen.

Gewoonlijk worden de volgende klassenelementen opgeslagen in DAM:

* Assets dat een bepaalde rijpheid heeft bereikt en dat klaar wordt geacht om te worden gedeeld.
* Assets die door het creatieve team zijn geselecteerd.
* Specifieke activaformaten die door marketing, afhankelijk van een specifiek contract of een overeenkomst (bijvoorbeeld, JPG dossiers die van RAW dossiers, TIFF/beelden van PSD originelen worden omgezet worden gebruikt of worden gevraagd).

#### Wanneer updates van elementen worden opgeslagen in DAM {#when-updates-to-assets-are-stored-in-dam}

Normaliter moeten alleen updates van middelen die relevant zijn voor de bredere reeks DAM-gebruikers in DAM worden opgeslagen. Hiermee zorgt u ervoor dat gebruikers (marketing en soortgelijke functies) alleen relevante versies in de tijdlijn van de DAM-middelen zien.

Doorgaans zijn er wijzigingen die betrekking hebben op belangrijke mijlpalen in de levenscyclus van de middelen. Het eerste marketingklare middel of een officiële update op basis van een verzoek/revisie van het creatieve team moet bijvoorbeeld worden opgeslagen en gecontroleerd in DAM.

De update van het creatieve team voor revisie door het marketingteam na een verzoek om wijziging van het bestaande middel in DAM is een voorbeeld van een relevante update. Het zou in DAM voor verdere verwijzing of voor het terugkeren naar de vorige versie moeten worden opgeslagen en worden versioned.

Hieronder volgen voorbeelden van updates die doorgaans niet relevant zijn:

* Vroege versies van elementen die zijn geüpload voordat ze klaar zijn voor marketingcontrole
* Veelvoorkomende creatieve wijzigingen in het bedrijfsmiddel in de aan de gang zijnde fase voordat creatieve en marketingteams besluiten dat het middel klaar is

### Toegang van gebruikers tot DAM {#user-access-to-dam}

[!DNL Assets] ondersteunt twee typen gebruikers op basis van hun toegang tot de [!DNL Assets] -implementatie. Doorgaans hebben gebruikers binnen het bedrijfsnetwerk (firewall) directe toegang tot DAM. Andere gebruikers buiten het ondernemingsnetwerk zouden geen directe toegang hebben. Het gebruikerstype bepaalt welke integraties vanuit technisch oogpunt kunnen worden gebruikt.

#### Creatieve gebruikers met directe toegang tot DAM {#creative-users-with-direct-access-to-dam}

In het algemeen hebben interne creatieve teams of agentschappen/creatieve professionals die aan het interne netwerk zijn toegewezen, toegang tot de DAM-implementatie, inclusief aanmelding bij [!DNL Experience Manager] . [!DNL Experience Manager] en de netwerkinfrastructuur kunnen worden opgezet om directe toegang tot externe partijen - gewoonlijk vertrouwde organisaties zoals agentschappen die voor een cliënt werken - te verlenen om toegang tot [!DNL Experience Manager] over netwerk, bijvoorbeeld, door VPN of IP lijst van gewenste personen te hebben.

In dergelijke gevallen biedt de Adobe Asset Link of de desktop-app [!DNL Experience Manager] eenvoudig toegang tot definitieve/goedgekeurde middelen en kunt u creatieve elementen opslaan naar DAM.

#### Creatieve gebruikers zonder toegang tot DAM {#creative-users-without-access-to-dam}

Externe agentschappen en freelancers zonder directe toegang tot de DAM-implementatie hebben mogelijk toegang tot goedgekeurde middelen nodig of willen hun nieuwe ontwerpen toevoegen aan de DAM.

Gebruik de volgende strategieën om toegang te verlenen tot definitieve/goedgekeurde middelen:

* Gebruik de bureaubladtoepassing als Asset Link niet werkt.
* Het gebruik [ Experience Manager Assets Brand Portal ](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/home.html?lang=nl-NL) voor het verdelen van activa veilig aan externe partners
* Gebruik een douanetoepassing van een distributie en het sourcen portaal die op [ wordt gebaseerd de Commons van het Aandeel van Activa ](https://adobe-marketing-cloud.github.io/asset-share-commons/)
* Gebruik Toegangsbeheer ingesteld in [!DNL Experience Manager] en de benodigde netwerkinfrastructuur (bijvoorbeeld VPN en IP lijst van gewenste personen) om externe partijen toegang te geven tot een specifiek inhoudsgebied in uw DAM. Ze kunnen [!DNL Experience Manager] Web UI gebruiken om elementen op te halen en nieuwe inhoud te uploaden naar uw DAM.

#### Werk in uitvoering met middelen van [!DNL Experience Manager] {#work-in-progress-on-assets-from-aem}

Zoals in dit document wordt besproken, wordt aanbevolen belangrijke updates van elementen uit te voeren, ook wel &#39;werk in uitvoering&#39; genoemd, zonder dat alle bewerkingen die in het lokale bestand zijn opgeslagen, als wijzigingen naar [!DNL Experience Manager] worden geüpload. Dit versnelt het werk van een Desktopgebruiker, beperkt gebruikte netwerkbandbreedte, en houdt de activa chronologie schoon en concentreert zich op gecontroleerde, belangrijke updates.

De Verbinding van de Activa van de Adobe biedt een goede steun voor dit gebruiksgeval:

* Wanneer gebruikers in [!DNL Photoshop] , [!DNL InDesign] of [!DNL Illustrator] een bestand willen bewerken, voeren zij een uitcheckbewerking uit op het opgegeven element
* Het element wordt op de achtergrond gedownload, in de gebruikersaccount van het Creative Cloud gesynchroniseerd op schijf per Creative Cloud desktop-app en de uitcheckmarkering wordt in [!DNL Experience Manager] op het element geschakeld om bewerkingsconflicten te minimaliseren
* Vanaf dat punt werkt de gebruiker in een bestand dat lokaal is opgeslagen op de gesynchroniseerde locatie. De gebruiker kan doorgaan met het werken en opslaan van noodzakelijke wijzigingen met elke vereiste frequentie
* Aangezien het Creative Cloud zich in de account van het Creative Cloud bevindt, is het ook beschikbaar op andere apparaten die de gebruiker mogelijk heeft (kunnen bijvoorbeeld worden geopend of bewerkt in een speciale mobiele app voor het ) en kan het voor samenwerkingsdoeleinden worden gedeeld met andere gebruikers in het Creative Cloud.
* Wanneer de creatieve gebruiker klaar is met de wijzigingen, kan hij of zij een incheckbewerking op dat bestand uitvoeren in zijn of haar toepassing op het Creative Cloud, met een optionele opmerking. Het overeenkomstige element in [!DNL Experience Manager] wordt versioned en bijgewerkt aan met het nieuwe binaire getal. [!DNL Experience Manager] -gebruikers zoals Marketers of LOB-gebruikers hebben via de tijdlijngebruikersinterface van [!DNL Experience Manager] elementen toegang tot belangrijke wijzigingen in elementen of mijlpalen.

De bureaubladtoepassing van [!DNL Experience Manager] biedt een gedeelde netwerkinhoud voor elementen die zijn geopend in de native app. Standaard worden alle lokaal uitgevoerde wijzigingen na een korte tijd automatisch geüpload naar [!DNL Experience Manager] . Met een dergelijke configuratie worden veelvuldig opgeslagen tijdens de aan de gang zijnde fase allemaal geüpload naar [!DNL Experience Manager] en geversileerd, waardoor er talloze uitdagingen op het gebied van netwerkverkeer en schaalbaarheid ontstaan, om nog maar te zwijgen van overbodige versies in [!DNL Experience Manager] .

Hier kunt u het beste een optie in de bureaubladtoepassing van [!DNL Experience Manager] gebruiken om geautomatiseerde updates uit te schakelen en wijzigingen in elementen handmatig naar [!DNL Experience Manager] te uploaden. Hierbij wordt de actie voor uploadwijzigingen gebruikt in de statusinterface van de app voor middelen.

#### Bulkupload naar DAM {#bulk-upload-to-dam}

In sommige gevallen moet u wellicht een groter aantal bestanden tegelijkertijd uploaden naar DAM, bijvoorbeeld:

* Resultaten van foto&#39;s of grotere projecten uploaden
* Door creatieve bureaus geleverde activa uploaden
* Geselecteerde elementen uploaden vanaf een grotere set als de selectie buiten DAM is uitgevoerd

De beschrijving verwijst naar het operationeel uploaden van bestanden (bijvoorbeeld elke week of met elke foto), als een normaal onderdeel van de workflow van de desktopgebruiker. De migratie van grote activa wordt hier niet behandeld.

U kunt de volgende uploadmogelijkheden gebruiken:

* Om grote/hiërarchische omslagen in massa te uploaden, gebruik [!DNL Experience Manager] Desktop app die [ omslag verstrekt uploadt ](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=nl-NL#upload-and-add-new-assets-to-aem) functionaliteit. U kunt ook hiërarchische mapstructuren uploaden. [!DNL Assets] worden op de achtergrond geüpload en zijn daarom niet gekoppeld aan een webbrowsersessie
* Als u enkele bestanden uit één map wilt uploaden, sleept u de bestanden rechtstreeks naar de webinterface of gebruikt u de optie Maken in de webinterface van [!DNL Assets] .
* Afhankelijk van uw bedrijfsvereisten kunt u ook aangepaste uploader gebruiken.

#### Digitale middelen rechtstreeks vanaf het bureaublad beheren {#managing-digital-assets-directly-from-desktop}

Als u Delen van netwerkbestanden gebruikt om digitale elementen te beheren, kunt u het gebruik van de netwerkshare die is toegewezen door de bureaubladtoepassing van [!DNL Experience Manager] beter zien als een handige vervanging. Wanneer u overschakelt van gedeelde netwerkbestanden, biedt de webinterface van [!DNL Experience Manager] een uitgebreide reeks mogelijkheden voor beheer van digitale middelen die veel verder gaan dan wat mogelijk is op een gedeeld netwerk (zoeken, verzamelingen, metagegevens, samenwerking, voorvertoningen, enzovoort). De desktop-app van [!DNL Experience Manager] biedt een handige koppeling om de DAM-opslagruimte aan de serverzijde te verbinden met het werk op een desktopcomputer.

Vermijd het gebruik van de [!DNL Experience Manager] -bureaubladtoepassing voor het rechtstreeks beheren van elementen in het gedeelde netwerk van [!DNL Assets] . Vermijd bijvoorbeeld het gebruik van de bureaubladtoepassing [!DNL Experience Manager] om meerdere bestanden te verplaatsen/kopiëren. Gebruik in plaats daarvan de interface van [!DNL Assets] om mappen van Finder/Explorer naar het gedeelde netwerk te slepen of gebruik de functie [!DNL Assets] Map uploaden.

#### Migratie van bedrijfsmiddelen {#asset-migration}

Om activa migraties van bestaand systeem aan een nieuw systeem of migratie van groot volume van activa te plannen en uit te voeren die op servers worden opgeslagen, zie de [ Gids van de Migratie ](/help/assets/assets-migration-guide.md). [!DNL Experience Manager] -desktop en [!DNL Experience Manager] to [!DNL Creative Cloud] -integratie bieden geen ondersteuning voor dergelijke migraties. Vanwege de grote hoeveelheden in te nemen elementen en de extra vereisten met betrekking tot het in kaart brengen van metagegevens, transformatie en opname, moeten migraties met verschillende gereedschappen en benaderingen worden afgehandeld.

>[!MORELIKETHIS]
>
>* [ de Verbinding van Activa van de Adobe ](https://helpx.adobe.com/nl/enterprise/using/adobe-asset-link.html)
>* [ Desktop van de Experience Manager app beste praktijken ](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/archive/best-practices-for-v1.html?lang=nl-NL)
>* [ Experience Manager Brand Portal ](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/introduction/brand-portal.html?lang=nl-NL)
>* [ Experience Manager en de integratie van Adobe Stock ](aem-assets-adobe-stock.md)
