---
title: Integratie met best practices van Adobe Creative Cloud
description: Aanbevolen werkwijzen voor integratie [!DNL Adobe Experience Manager] with [!DNL Adobe Creative Cloud] om workflows voor middelenoverdracht te stroomlijnen en een hoge snelheid van de inhoud te bereiken.
contentOwner: AG
mini-toc-levels: 1
role: User, Admin
feature: Collaboration,Adobe Asset Link,Desktop App
exl-id: c7d589a3-1c5f-4ff0-879e-15e1c556f6dc
hide: true
source-git-commit: 9d497413d0ca72f22712581cf7eda1413eb8d643
workflow-type: tm+mt
source-wordcount: '3173'
ht-degree: 9%

---

# [!DNL Adobe Experience Manager] en [!DNL Creative Cloud] best practices voor integratie {#aem-and-creative-cloud-integration-best-practices}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/aem-cc-integration-best-practices.html?lang=en) |
| AEM 6,5 | Dit artikel |

[!DNL Adobe Experience Manager Assets] is een DAM-oplossing (Digital Asset Management) die kan worden geïntegreerd met [!DNL Adobe Creative Cloud] om DAM-gebruikers te helpen samen te werken met creatieve teams en de samenwerking bij het maken van inhoud te stroomlijnen.

[!DNL Adobe Creative Cloud] voorziet creatieve teams van een ecosysteem van oplossingen en diensten om hen te helpen om digitale activa tot stand te brengen. Hieronder vallen desktoptoepassingen en mobiele toepassingen, cloudservices zoals opslag met desktopsynchronisatie of webervaring, en marketinglocaties zoals [!DNL Adobe Stock].

Lees verder om te weten welke integraties u kunt kiezen tussen desktop en DAM op bedrijfsniveau op basis van uw gebruiksscenario en wat de bijbehorende beste werkwijzen zijn voor de verbindingsworkflows.

>[!NOTE]
>
>[!DNL Experience Manager] tot [!DNL Creative Cloud] het delen van mappen is vervangen en wordt niet meer behandeld in deze handleiding. Adobe raadt aan om nieuwere mogelijkheden te gebruiken, zoals [Adobe-itemkoppeling](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html) of [Experience Manager-bureaubladtoepassing](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/troubleshoot.html) creatieve gebruikers toegang bieden tot middelen die worden beheerd in [!DNL Experience Manager].

## De behoeften van de samenwerking van creatieven, verkopers, en gebruikers DAM {#collaboration-needs-of-creatives-marketers-and-dam-users}

| Vereisten | Hoofdletters gebruiken | Betrokken oppervlakken |
|---|---|---|
| Ervaring voor creatieve producten op desktopcomputers vereenvoudigen | Toegang tot middelen van een DAM stroomlijnen ([!DNL Experience Manager Assets]) voor creatieve professionals, of meer in het algemeen, gebruikers op desktopcomputers die werken in toepassingen voor het maken van native elementen. Ze hebben een eenvoudige en eenvoudige manier nodig om wijzigingen te detecteren, te gebruiken (openen), te bewerken en op te slaan in [!DNL Experience Manager]en uploaden nieuwe bestanden. | Win- of Mac-bureaublad; [!DNL Creative Cloud] apps |
| Voorzie van hoogwaardige, gebruiksklare middelen van [!DNL Adobe Stock] | Marketers helpen het proces voor het maken van inhoud te versnellen door hulp te bieden bij het aanschaffen en detecteren van bedrijfsmiddelen. Creatieve professionals gebruiken de goedgekeurde middelen direct vanuit hun creatieve gereedschappen. | [!DNL Experience Manager Assets]; [!DNL Adobe Stock] Marketplace; metagegevensvelden |
| Elementen distribueren en delen door organisaties | De interne afdelingen/de lokale takken en de externe partners, de distributeurs, en de agentschappen gebruiken de goedgekeurde activa die door de ouderorganisatie worden gedeeld. De organisatie wil de gemaakte middelen veilig en naadloos delen voor breder hergebruik. | Brand Portal, Commentaar voor het delen van bedrijfsmiddelen |

## Adobe biedt ondersteuning voor de behoefte aan samenwerking {#adobe-offerings-to-support-the-collaboration-need}

| Waardevoorstel voor de betreffende personen | Adobe aanbieden | Betrokken oppervlakken |
|---|---|---|
| Creatieve gebruikers ontdekken elementen van [!DNL Experience Manager], openen en gebruiken, wijzigingen bewerken en uploaden naar [!DNL Experience Manager]en uploadt u nieuwe bestanden naar [!DNL Experience Manager], zonder te vertrekken [!DNL Creative Cloud] apps. | [Adobe-itemkoppeling](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html) | [!DNL Adobe Photoshop], [!DNL Adobe Illustrator], en [!DNL Adobe InDesign]. |
| Zakelijke gebruikers vereenvoudigen het openen en gebruiken van middelen, het bewerken en uploaden van wijzigingen in [!DNL Experience Manager]en nieuwe bestanden uploaden naar [!DNL Experience Manager] in de desktopomgeving. Ze gebruiken een algemene integratie om elk elementtype in de native bureaubladtoepassing te openen, inclusief niet-Adobe toepassingen. | [Experience Manager-bureaubladtoepassing](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html) | [!DNL Experience Manager] bureaubladtoepassing op Win- en Mac-bureaublad |
| Marketers en zakelijke gebruikers ontdekken, voorvertonen, licentiëren en opslaan, en beheren de [!DNL Adobe Stock] activa van binnen [!DNL Experience Manager]. Gelicentieerde en opgeslagen elementen bieden geselecteerde [!DNL Adobe Stock] metagegevens voor beter bestuur. | [Integratie van Experience Manager en Adobe Stock](aem-assets-adobe-stock.md) | [!DNL Experience Manager] webinterface |

Dit artikel richt zich hoofdzakelijk op de eerste twee aspecten van de samenwerkingsbehoeften. Distributie en sourcing van assets op schaal wordt kort als gebruiksscenario genoemd. Overweeg Adobe Brand Portal of Asset Share Commons voor dergelijke oplossingen. Alternatieve oplossingen, zoals [Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/home.html), oplossingen die op [Commentaar voor het delen van bedrijfsmiddelen](https://adobe-marketing-cloud.github.io/asset-share-commons/) componenten, [Delen van koppeling](/help/assets/link-sharing.md), gebruiken [Experience Manager Assets](/help/assets/manage-assets.md) moeten worden herzien op basis van specifieke eisen.

![De verbindingen van het Creative Cloud voor Experience Manager, beslissen welke capaciteit te gebruiken](assets/creative-connections-aem.png)

### Toewijzing van gebruiksgevallen en Adobe-oplossingen {#mapping-of-use-cases-and-adobe-solutions}

<!-- TBD: Add some info about XD integration and possibly info about DA v2.0.
-->

| Hoofdletters gebruiken | [!DNL Adobe Asset Link] | [!DNL Experience Manager] bureaubladtoepassing | Opmerkingen/andere oplossingen |
|---|---|---|---|
| Detecteren - door DAM-mappen bladeren | Ja | [!DNL Experience Manager] Webinterface- en desktopacties | |
| Discover - toegang tot DAM-verzamelingen | Ja | [!DNL Experience Manager] Webinterface- en desktopacties | |
| Discover - zoek naar middelen van DAM | Ja | [!DNL Experience Manager] Webinterface- en desktopacties | |
| Gebruiken - element openen | Ja | Ja | [Openen vanuit webinterface](manage-assets.md#previewing-assets) of van Finder |
| Gebruiken - element van DAM in een document plaatsen | Ja - insluiten | Ja - koppelen of insluiten | [!DNL Experience Manager] bureaubladtoepassing biedt toegang tot elementen als bestanden op het lokale bestandssysteem. Deze koppelingen in de native apps worden weergegeven door lokale paden. |
| Bewerken - openen voor bewerking | Ja, uitchecken, actie | Ja - Handeling openen (in netwerkshare) | [Uitchecken in AAL](https://helpx.adobe.com/nl/enterprise/using/manage-assets-using-adobe-asset-link.html) Hiermee slaat u het element standaard op in de Creative Cloud Storage-account van de gebruiker (gesynchroniseerd door Creative Cloud-app). |
| Bewerken - werk wordt uitgevoerd buiten DAM | Ja - Asset beschikbaar in de opslagaccount van het Creative Cloud van de gebruiker gesynchroniseerd met desktop. | Ja | |
| Bewerken - wijzigingen uploaden | Ja - [Inchecken, actie](https://helpx.adobe.com/nl/enterprise/using/manage-assets-using-adobe-asset-link.html) met optionele opmerking | Ja | |
| Uploaden - één bestand | Ja - het actieve document wordt geüpload | Ja | [Uploaden via webinterface](manage-assets.md#uploading-assets) |
| Uploaden - meerdere bestanden / hiërarchische mapstructuren | Nee | Ja | [Uploaden via webinterface](manage-assets.md#uploading-assets) of via aangepaste scripts of gereedschappen. |
| Diverse - gebruiker en aanmelding | Gebruikers van Creatives Cloud die zich hebben aangemeld bij de desktop-app van het Creative Cloud, worden herkend (SSO) | [!DNL Experience Manager] gebruiker en gebruikersgegevens | Gebruikers van beide oplossingen tellen mee voor de [!DNL Experience Manager] gebruikersquota. |
| Diverse - netwerk en toegang | Toegang van bureaublad van gebruiker tot [!DNL Experience Manager] implementatie via netwerk | Toegang van bureaublad van gebruiker tot [!DNL Experience Manager] implementatie via netwerk | [!DNL Adobe Asset Link] deelt geen milieu van de netwerkvolmacht. |
| Misc - Grote aantallen activa migreren | Nee | Nee | [Richtlijnen voor migratie van middelen](assets-migration-guide.md) |

Om het gebruik van middelen te steunen, zouden andere oplossingen moeten worden overwogen:

* [Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/home.html) voor configureerbaar, toe:voegen-aan SaaS aan [!DNL Experience Manager Assets] elementen publiceren.
* Aangepaste oplossingen worden gemaakt op basis van [Commentaar voor het delen van bedrijfsmiddelen](https://adobe-marketing-cloud.github.io/asset-share-commons/) code base.
* [!DNL Experience Manager] [delen van koppeling](/help/assets/link-sharing.md) om activa op bestelling te delen gebruikend verbindingen.
* [Experience Manager Assets-webinterface](/help/assets/manage-assets.md) met gebieden voor externe partijen die door [!DNL Experience Manager] toegang controleopstelling en met noodzakelijke aanpassingen van de IT/netwerkconfiguratie, die deze externe gebruikers toegang geven tot [!DNL Experience Manager].

## Belangrijkste concepten en gebruiksgevallen {#key-concepts-and-use-cases}

### Verklarende woordenlijst {#glossary-of-common-terms}

* **Werk in uitvoering of creatief werk in uitvoering (WIP):** Een fase in de levenscyclus van assets waarbij een asset meerdere wijzigingen ondergaat en doorgaans nog niet klaar is om te worden gedeeld met grotere teams.
* **Creative-klare middelen:** [!DNL Assets] die klaar zijn om te worden gedeeld met een breder team, of door het creatieve team zijn geselecteerd of goedgekeurd om te worden gedeeld met marketing- of LOB-teams.
* **Goedkeuring van assets:** Het goedkeuringsproces dat wordt uitgevoerd voor assets die reeds naar DAM zijn geüpload, en dat typisch merkgoedkeuringen, wettelijke goedkeuringen, enz. omvat.
* **Definitief actief:** Een middel dat door alle goedkeuringen/meta-gegevens het etiketteren is gegaan en klaar is om door het bredere team te worden gebruikt. Een dergelijke asset wordt opgeslagen in DAM en beschikbaar gesteld aan alle (geïnteresseerde) gebruikers. Deze kan in marketingkanalen of door creatieve teams worden gebruikt om ontwerpen te maken.
* **Kleine update/wijziging van bedrijfsmiddelen:** Een snelle en kleine wijziging in een digitaal middel. Deze wordt vaak uitgevoerd als reactie op een retoucheerverzoek of een verzoek om kleine bewerkingen, een assetrevisie of goedkeuring (bijvoorbeeld om de positie te wijzigen, de tekstgrootte te wijzigen, de verzadiging/helderheid en kleur aan te passen, enz.).
* **Belangrijke update/wijziging van bedrijfsmiddelen:** Een verandering in een digitaal goed dat aanzienlijk werk vereist, en soms over een langere periode moet gebeuren. Dit omvat doorgaans meerdere wijzigingen. De asset moet tijdens het bijwerken meerdere keren worden opgeslagen. De belangrijkste assetupdates leiden er doorgaans toe dat de asset een WIP-status krijgt.
* **DAM:** Beheer van digitale assets. In dit document is het synoniem met [!DNL Experience Manager Assets], tenzij uitdrukkelijk anders vermeld.
* **Creatieve gebruiker:** Een creatieve professional die digitale assets maakt met Creative Cloud-apps en -services. In sommige gevallen is een creatieve gebruiker lid van een creatief team dat mogelijk Creative Cloud gebruikt, maar geen digitale assets maakt (zoals een creatieve directeur of een creatieve teammanager).
* **DAM-gebruiker:** Een typische gebruiker van een DAM-systeem. Afhankelijk van de organisatie, kan een gebruiker DAM een marketing of een niet-marketing gebruiker, bijvoorbeeld, een lijn-van-Bedrijfs (LOB) gebruiker, bibliothecaris, verkooppersoon, etc. zijn.

### Overwegingen bij gebruik [!DNL Experience Manager] en [!DNL Creative Cloud] integratie {#considerations-when-using-aem-and-creative-cloud-integration}

* Zie [best practices voor bureaubladtoepassingen](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/troubleshoot.html#best-practices-to-prevent-troubles)
* Zie [Adobe Stock-integratie](aem-assets-adobe-stock.md)
* Zie [Adobe-itemkoppeling](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html)

Dit is een korte samenvatting van beste praktijken voor [!DNL Experience Manager] en [!DNL Creative Cloud] integratie. Lees de rest van dit document voor een gedetailleerd begrip hiervan.

* **Voor creatieve gebruikers die in Photoshop, InDesign, of Illustrator werken:** Adobe Asset Link biedt de beste gebruikerservaring, waaronder een schone verwerking van de onderhanden werk op middelen die zijn uitgecheckt van [!DNL Experience Manager].
* **Voor het vereenvoudigen van de toegang tot middelen van de Desktop voor om het even welke generische dossierformaat of toepassing:** gebruiken [!DNL Experience Manager] bureaubladtoepassing.
* **Begrijp waarom en wanneer om activa in DAM op te slaan:** Updates die ter beschikking moeten worden gesteld aan het bredere team in uw organisatie.
* **Houd rekening met het volume van de gedeelde assets:** Als u gebruikmaakt van assetdistributie, kunnen governance en beveiliging de belangrijkste aspecten zijn. Overweeg om tools te gebruiken die bedoeld zijn om governance en beveiliging op grote schaal toe te passen, zoals de Brand Portal.
* **De levenscyclus van assets begrijpen:** Begrijp hoe assets in uw organisatie worden verwerkt door verschillende teams
* **Correct en regelmatig opslaan van assets:** Adobe Asset Link doet dit voor u met PS, AI, ID. Voer voor andere toepassingen geen actieve taken uit in toegewezen/gedeelde map tenzij u alle wijzigingen in DAM nodig hebt

### Toegang tot [!DNL Adobe Stock] activa van [!DNL Assets] {#access-to-adobe-stock-assets-from-aem-assets}

[Integratie van Experience Manager en Adobe Stock](/help/assets/aem-assets-adobe-stock.md) verstrekt [!DNL Experience Manager] gebruikers met de mogelijkheid om te zoeken naar, een voorvertoning weer te geven, licenties te maken en bestanden op te slaan, middelen van [!DNL Adobe Stock] in [!DNL Experience Manager]. Gelicentieerd en opgeslagen [!DNL Stock] elementen zijn geselecteerd [!DNL Stock] metagegevens, die kunnen worden gebruikt om met extra filters naar de metagegevens te zoeken.

Een paar belangrijke punten over deze integratie:

* Wanneer elementen uit voorraad Adobe worden opgeslagen naar [!DNL Experience Manager]worden ze regelmatig [!DNL Assets], met binair bestand opgeslagen op de [!DNL Experience Manager] opslagplaats. Sommige metagegevens die betrekking hebben op [!DNL Adobe Stock] worden opgeslagen voor het element in [!DNL Experience Manager]Anders ziet het innameproces er hetzelfde uit als voor elk ander bestand. Als slimme tags bijvoorbeeld actief zijn, worden de tags bij het opslaan aan deze elementen toegevoegd.
* Het element dat is opgeslagen naar [!DNL Experience Manager] is een kopie, geen koppeling terug naar [!DNL Adobe Stock].

**Werken met elementen die zijn opgeslagen vanuit [!DNL Adobe Stock] in [!DNL Experience Manager] in[!DNL Creative Cloud]**. Deze integratie staat los van [!DNL Adobe Asset Link], maar [!DNL Adobe Asset Link] herkent deze elementen die zijn opgeslagen van [!DNL Stock] op die manier en worden aanvullende metagegevens en een [!DNL Adobe Stock] logo op deze middelen in [!DNL Adobe Asset Link] extensie-UI in [!DNL Photoshop], [!DNL Illustrator], of [!DNL InDesign]. De bestanden zijn beschikbaar voor bladeren, openen, enzovoort, omdat het normale elementen zijn wanneer ze worden opgeslagen naar [!DNL Experience Manager].
Creatieve gebruikers die werken in [!DNL Creative Cloud] apps met [!DNL Adobe Asset Link] de uitbreiding, naast de toegang tot reeds in licentie gegeven activa van [!DNL Adobe Stock] in [!DNL Experience Manager]kan ook [!DNL Creative Cloud] Deelvenster Bibliotheken waarin u kunt zoeken, voorvertonen en licentiëren [!DNL Adobe Stock] activa.
[!DNL Assets] van [!DNL Adobe Stock] gelicentieerd en opgeslagen in [!DNL Experience Manager] beschikbaar worden voor de bredere teams die toegang hebben tot [!DNL Experience Manager Assets] implementatie, terwijl creatieve klanten hun middelen van [!DNL Adobe Stock] via [!DNL Creative Cloud] Deelvenster Bibliotheken stelt deze alleen standaard beschikbaar in hun [!DNL Creative Cloud] account.

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

* Activa die nog moeten worden afgerond of die moeten worden getest.
* Middelen die de beoordelingscyclus van het creatieve/interne team niet doorstaan.
* Vergeleken met de middelen in kwestie, heeft het team betere kandidaten om hun werk aan externe teams te vertegenwoordigen.

Gewoonlijk worden de volgende klassenelementen opgeslagen in DAM:

* Activa die een bepaalde looptijd hebben bereikt en die als gereed worden beschouwd om te worden gedeeld.
* Elementen die vooraf zijn geselecteerd door het creatieve team.
* Specifieke activaformaten die door marketing, afhankelijk van een specifiek contract of een overeenkomst (bijvoorbeeld, JPG dossiers die van RAW dossiers, TIFF/beelden van PSD originelen worden omgezet worden gebruikt of worden gevraagd).

#### Wanneer updates van elementen worden opgeslagen in DAM {#when-updates-to-assets-are-stored-in-dam}

Normaliter moeten alleen updates van middelen die relevant zijn voor de bredere reeks DAM-gebruikers in DAM worden opgeslagen. Hiermee zorgt u ervoor dat gebruikers (marketing en soortgelijke functies) alleen relevante versies in de tijdlijn van de DAM-middelen zien.

Doorgaans zijn er wijzigingen die betrekking hebben op belangrijke mijlpalen in de levenscyclus van de middelen. Het eerste marketingklare middel of een officiële update op basis van een verzoek/revisie van het creatieve team moet bijvoorbeeld worden opgeslagen en gecontroleerd in DAM.

De update van het creatieve team voor revisie door het marketingteam na een verzoek om wijziging van het bestaande middel in DAM is een voorbeeld van een relevante update. Het zou in DAM voor verdere verwijzing of voor het terugkeren naar de vorige versie moeten worden opgeslagen en worden versioned.

Hieronder volgen voorbeelden van updates die doorgaans niet relevant zijn:

* Vroege versies van elementen die zijn geüpload voordat ze klaar zijn voor marketingcontrole
* Veelvoorkomende creatieve wijzigingen in het bedrijfsmiddel in de aan de gang zijnde fase voordat creatieve en marketingteams besluiten dat het middel klaar is

### Toegang van gebruikers tot DAM {#user-access-to-dam}

[!DNL Assets] ondersteunt twee typen gebruikers op basis van hun toegang tot de [!DNL Assets] implementatie. Doorgaans hebben gebruikers binnen het bedrijfsnetwerk (firewall) directe toegang tot DAM. Andere gebruikers buiten het ondernemingsnetwerk zouden geen directe toegang hebben. Het gebruikerstype bepaalt welke integraties vanuit technisch oogpunt kunnen worden gebruikt.

#### Creatieve gebruikers met directe toegang tot DAM {#creative-users-with-direct-access-to-dam}

Doorgaans hebben interne creatieve teams of agentschappen/creatieve professionals die aan het interne netwerk zijn toegewezen, toegang tot de DAM-implementatie, waaronder [!DNL Experience Manager] aanmelden. [!DNL Experience Manager] en de netwerkinfrastructuur kan worden opgezet om directe toegang tot externe partijen - gewoonlijk vertrouwde organisaties zoals agentschappen die voor een cliënt werken - te verlenen [!DNL Experience Manager] via netwerk, bijvoorbeeld, als VPN of IP lijst van gewenste personen.

In dergelijke gevallen wordt de Adobe Asset Link of [!DNL Experience Manager] bureaubladtoepassing biedt eenvoudige toegang tot definitieve/goedgekeurde middelen en biedt u de mogelijkheid creatieve middelen op te slaan in DAM.

#### Creatieve gebruikers zonder toegang tot DAM {#creative-users-without-access-to-dam}

Externe agentschappen en freelancers zonder directe toegang tot de DAM-implementatie hebben mogelijk toegang tot goedgekeurde middelen nodig of willen hun nieuwe ontwerpen toevoegen aan de DAM.

Gebruik de volgende strategieën om toegang te verlenen tot definitieve/goedgekeurde middelen:

* Gebruik de bureaubladtoepassing als Asset Link niet werkt.
* Gebruiken [Experience Manager Assets Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/home.html) voor het veilig verdelen van activa aan externe partners
* Gebruik een aangepaste implementatie van een distributie- en sourcingportal op basis van [Commentaar voor het delen van bedrijfsmiddelen](https://adobe-marketing-cloud.github.io/asset-share-commons/)
* Toegangsbeheer instellen in [!DNL Experience Manager] en noodzakelijke netwerkinfrastructuur (bijvoorbeeld, VPN en IP lijst van gewenste personen) om externe partijen toegang tot een specifiek gebied van inhoud in uw DAM te geven. Ze kunnen [!DNL Experience Manager] Web UI om middelen te krijgen en nieuwe inhoud te uploaden in uw DAM.

#### Werk bezig met middelen van [!DNL Experience Manager] {#work-in-progress-on-assets-from-aem}

Zoals in dit document wordt besproken, wordt aanbevolen belangrijke updates uit te voeren voor elementen, ook wel &#39;werk in uitvoering&#39; genoemd, zonder dat alle bewerkingen die in het lokale bestand zijn opgeslagen, ook worden geüpload naar [!DNL Experience Manager] als wijzigingen. Dit versnelt het werk van een Desktopgebruiker, beperkt gebruikte netwerkbandbreedte, en houdt de activa chronologie schoon en concentreert zich op gecontroleerde, belangrijke updates.

De Verbinding van de Activa van de Adobe biedt een goede steun voor dit gebruiksgeval:

* Wanneer gebruikers [!DNL Photoshop], [!DNL InDesign], of [!DNL Illustrator] Beoogd om een bestand te bewerken, voeren ze een uitcheckbewerking uit op het opgegeven element
* Het element wordt op de achtergrond gedownload, in de gebruikersaccount van het Creative Cloud geplaatst en op schijf gesynchroniseerd via de bureaubladtoepassing van het Creative Cloud. De markering voor uitchecken wordt ingeschakeld [!DNL Experience Manager] op het element om bewerkingsconflicten te minimaliseren
* Vanaf dat punt werkt de gebruiker in een bestand dat lokaal is opgeslagen op de gesynchroniseerde locatie. De gebruiker kan doorgaan met het werken en opslaan van noodzakelijke wijzigingen met elke vereiste frequentie
* Aangezien het Creative Cloud zich in de account van het Creative Cloud bevindt, is het ook beschikbaar op andere apparaten die de gebruiker mogelijk heeft (kunnen bijvoorbeeld worden geopend of bewerkt in een speciale mobiele app voor het ) en kan het voor samenwerkingsdoeleinden worden gedeeld met andere gebruikers in het Creative Cloud.
* Wanneer de creatieve gebruiker klaar is met de wijzigingen, kan hij of zij een incheckbewerking op dat bestand uitvoeren in zijn of haar toepassing op het Creative Cloud, met een optionele opmerking. Het corresponderende actief in [!DNL Experience Manager] zijn versioned en bijgewerkt aan met het nieuwe binaire getal. [!DNL Experience Manager] gebruikers zoals Marketers of LOB-gebruikers hebben via [!DNL Experience Manager] UI van de tijdlijn van middelen.

[!DNL Experience Manager] desktop app biedt netwerkshare voor middelen die zijn geopend in de native app. Standaard worden alle lokaal uitgevoerde wijzigingen geüpload naar [!DNL Experience Manager] automatisch na een korte tijd. Met zo&#39;n configuratie, zou het frequente sparen tijdens het werk in lopende fase allen worden geupload in [!DNL Experience Manager] en versioned, creërend talrijke netwerkverkeer en potentiële scalability uitdagingen - om onnodige versies in te noemen [!DNL Experience Manager].

Hier kunt u het beste een optie gebruiken in [!DNL Experience Manager] bureaubladtoepassing om geautomatiseerde updates uit te schakelen en wijzigingen in middelen te uploaden naar [!DNL Experience Manager] wijzigt u handmatig met de actie voor uploaden de status van bedrijfsmiddelen van de app.

#### Bulkupload naar DAM {#bulk-upload-to-dam}

In sommige gevallen moet u wellicht een groter aantal bestanden tegelijkertijd uploaden naar DAM, bijvoorbeeld:

* Resultaten van foto&#39;s of grotere projecten uploaden
* Door creatieve bureaus geleverde activa uploaden
* Geselecteerde elementen uploaden vanaf een grotere set als de selectie buiten DAM is uitgevoerd

De beschrijving verwijst naar het operationeel uploaden van bestanden (bijvoorbeeld elke week of met elke foto), als een normaal onderdeel van de workflow van de desktopgebruiker. De migratie van grote activa wordt hier niet behandeld.

U kunt de volgende uploadmogelijkheden gebruiken:

* Als u grote/hiërarchische mappen bulksgewijs wilt uploaden, gebruikt u [!DNL Experience Manager] bureaubladtoepassing die [map uploaden](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html#upload-and-add-new-assets-to-aem) functionaliteit. U kunt ook hiërarchische mapstructuren uploaden. [!DNL Assets] worden geüpload op de achtergrond en zijn daarom niet gekoppeld aan een webbrowsersessie
* Als u enkele bestanden uit één map wilt uploaden, sleept u de bestanden rechtstreeks naar de webinterface of gebruikt u de optie Maken in het dialoogvenster [!DNL Assets] webinterface.
* Afhankelijk van uw bedrijfsvereisten kunt u ook aangepaste uploader gebruiken.

#### Digitale middelen rechtstreeks vanaf het bureaublad beheren {#managing-digital-assets-directly-from-desktop}

Als u de Delen van het Dossier van het Netwerk gebruikt om digitale activa te beheren, enkel gebruikend het netwerkaandeel in kaart gebracht door [!DNL Experience Manager] bureaubladtoepassing kan worden beschouwd als een handige vervanging. Bij de overgang van netwerkbestandsshares [!DNL Experience Manager] de webinterface biedt een uitgebreide reeks mogelijkheden voor beheer van digitale middelen die veel verder gaan dan wat mogelijk is op een gedeeld netwerk (zoeken, verzamelingen, metagegevens, samenwerking, voorvertoningen, enzovoort), en [!DNL Experience Manager] bureaubladtoepassing biedt een handige koppeling om de DAM-opslagplaats aan de serverzijde te verbinden met het werk op het bureaublad.

Vermijd gebruik [!DNL Experience Manager] bureaubladtoepassing om elementen rechtstreeks te beheren in het netwerkaandeel van [!DNL Assets]. Vermijd bijvoorbeeld het gebruik [!DNL Experience Manager] bureaubladtoepassing om meerdere bestanden te verplaatsen/kopiëren. Gebruik in plaats daarvan de opdracht [!DNL Assets] interface om omslagen van Finder/Ontdekkingsreiziger aan het netwerkaandeel te slepen of te gebruiken [!DNL Assets] Functie Map uploaden.

#### Migratie van bedrijfsmiddelen {#asset-migration}

Als u de migratie van middelen van een bestaand systeem naar een nieuw systeem wilt plannen en uitvoeren, of een grote hoeveelheid op servers opgeslagen middelen wilt migreren, raadpleegt u de [Migratiehandleiding](/help/assets/assets-migration-guide.md). [!DNL Experience Manager] bureaubladtoepassing en [!DNL Experience Manager] tot [!DNL Creative Cloud] dergelijke migraties worden niet door integratie ondersteund . Vanwege de grote hoeveelheden in te nemen elementen en de extra vereisten met betrekking tot het in kaart brengen van metagegevens, transformatie en opname, moeten migraties met verschillende gereedschappen en benaderingen worden afgehandeld.

>[!MORELIKETHIS]
>
>* [Adobe-itemkoppeling](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html)
>* [Aanbevolen werkwijzen voor bureaublad van Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/archive/best-practices-for-v1.html)
>* [Experience Manager Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/introduction/brand-portal.html)
>* [Integratie van Experience Manager en Adobe Stock](aem-assets-adobe-stock.md)
