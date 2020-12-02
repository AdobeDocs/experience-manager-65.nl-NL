---
title: Integratie met best practices van Adobe Creative Cloud
description: Aanbevolen procedures om [!DNL Adobe Experience Manager] with [!DNL Adobe Creative Cloud] te integreren om workflows voor de overdracht van elementen te stroomlijnen en een hoge snelheid van de inhoud te bereiken.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 12c56c27c7f97f1029c757ec6d28f482516149d0
workflow-type: tm+mt
source-wordcount: '3248'
ht-degree: 15%

---


# [!DNL Adobe Experience Manager] en best practices voor  [!DNL Creative Cloud] integratie  {#aem-and-creative-cloud-integration-best-practices}

[!DNL Adobe Experience Manager Assets] is een DAM-oplossing (Digital Asset Management) die kan worden geïntegreerd  [!DNL Adobe Creative Cloud] om DAM-gebruikers te helpen samen te werken met creatieve teams en de samenwerking bij het maken van inhoud te stroomlijnen.

[!DNL Adobe Creative Cloud] voorziet creatieve teams van een ecosysteem van oplossingen en diensten om hen te helpen om digitale activa tot stand te brengen. Hieronder vallen desktoptoepassingen en mobiele toepassingen, cloudservices zoals opslag met desktopsynchronisatie of webervaring, en marketinglocaties zoals [!DNL Adobe Stock].

Lees verder om te weten welke integraties u kunt kiezen tussen desktop en DAM op bedrijfsniveau op basis van uw gebruiksscenario en wat de bijbehorende beste werkwijzen zijn voor de verbindingsworkflows.

>[!NOTE]
>
>[!DNL Experience Manager] naar  [!DNL Creative Cloud] mappen delen is vervangen en wordt niet langer behandeld in deze handleiding. Adobe raadt aan nieuwere mogelijkheden te gebruiken, zoals [Adobe Asset Link](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html) of [Experience Manager desktop app](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/troubleshoot.html), om creatieve gebruikers toegang te bieden tot middelen die worden beheerd in [!DNL Experience Manager].

## Samenwerkingsbehoeften van ontwerpers, marketers en DAM-gebruikers {#collaboration-needs-of-creatives-marketers-and-dam-users}

| Vereisten | Hoofdletters gebruiken | Betrokken oppervlakken |
|---|---|---|
| Ervaring voor creatieve producten op desktop vereenvoudigen | Toegang tot bedrijfsmiddelen vanaf een DAM ([!DNL Experience Manager Assets]) stroomlijnen voor creatieve professionals, of meer in het algemeen gebruikers op desktopcomputers die werken in toepassingen voor het maken van native bedrijfsmiddelen. Ze hebben een eenvoudige en eenvoudige manier nodig om wijzigingen in [!DNL Experience Manager] te detecteren, gebruiken (openen), bewerken en opslaan, en om nieuwe bestanden te uploaden. | Win- of Mac-bureaublad; [!DNL Creative Cloud] apps |
| Voorzie van hoogwaardige, gebruiksklare middelen van [!DNL Adobe Stock] | Marketers helpen het proces voor het maken van inhoud te versnellen door hulp te bieden bij het aanschaffen en detecteren van bedrijfsmiddelen. Creatieve professionals gebruiken de goedgekeurde middelen direct vanuit hun creatieve gereedschappen. | [!DNL Experience Manager Assets];  [!DNL Adobe Stock] markt; metagegevensvelden |
| Elementen distribueren en delen door organisaties | De interne afdelingen/de lokale takken en de externe partners, de distributeurs, en de agentschappen gebruiken de goedgekeurde activa die door de ouderorganisatie worden gedeeld. De organisatie wil de gemaakte middelen veilig en naadloos delen voor breder hergebruik. | Merkportal, Commentaar voor delen van bedrijfsmiddelen |

## Adobe-aanbod ter ondersteuning van de samenwerkingsbehoefte {#adobe-offerings-to-support-the-collaboration-need}

| Waardevoorstel voor de betreffende personen | Adobe-aanbieding | Betrokken oppervlakken |
|---|---|---|
| Creatieve gebruikers ontdekken elementen van [!DNL Experience Manager], openen en gebruiken, bewerken en uploaden wijzigingen in [!DNL Experience Manager] en uploaden nieuwe bestanden naar [!DNL Experience Manager], zonder [!DNL Creative Cloud]-apps te verlaten. | [Adobe-itemkoppeling](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html) | [!DNL Adobe Photoshop],  [!DNL Adobe Illustrator]en  [!DNL Adobe InDesign]. |
| Zakelijke gebruikers vereenvoudigen het openen en gebruiken van middelen, het bewerken en uploaden van wijzigingen in [!DNL Experience Manager] en het uploaden van nieuwe bestanden naar [!DNL Experience Manager] vanuit de desktopomgeving. Ze gebruiken een algemene integratie om elk elementtype in de native bureaubladtoepassing te openen, inclusief niet-Adobe toepassingen. | [Experience Manager-bureaubladtoepassing](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html) | [!DNL Experience Manager] bureaubladtoepassing op Win- en Mac-bureaublad |
| Marketers en zakelijke gebruikers ontdekken, voorvertonen, licentiëren en opslaan, en beheren de [!DNL Adobe Stock]-middelen vanuit [!DNL Experience Manager]. Gelicentieerde en opgeslagen elementen bieden geselecteerde [!DNL Adobe Stock]-metagegevens voor beter beheer. | [Integratie van Experience Manager en Adobe Stock](aem-assets-adobe-stock.md) | [!DNL Experience Manager] webinterface |

Dit artikel richt zich hoofdzakelijk op de eerste twee aspecten van de samenwerkingsbehoeften. Distributie en sourcing van assets op schaal wordt kort als gebruiksscenario genoemd. Overweeg Adobe Brand Portal of Asset Share Commons voor dergelijke oplossingen. Alternatieve oplossingen zoals [Merk Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/home.html), oplossingen die kunnen worden gebouwd op [Asset Share Commons](https://adobe-marketing-cloud.github.io/asset-share-commons/) componenten, [Link Share](/help/assets/link-sharing.md), die [Experience Manager Assets](/help/assets/manage-assets.md) gebruiken, dienen te worden beoordeeld op basis van specifieke vereisten.

![Creative Cloud verbindingen voor Experience Manager, besluit welke capaciteit te gebruiken](assets/creative-connections-aem.png)

### Toewijzing van gebruiksgevallen en Adobe-oplossingen {#mapping-of-use-cases-and-adobe-solutions}

<!-- TBD: Add some info about XD integration and possibly info about DA v2.0.
-->

| Hoofdletters gebruiken | [!DNL Adobe Asset Link] | [!DNL Experience Manager] bureaubladtoepassing | Opmerkingen/andere oplossingen |
|---|---|---|---|
| Detecteren - door DAM-mappen bladeren | Ja | [!DNL Experience Manager] Webinterface- en desktopacties |  |
| Discover - toegang tot DAM-verzamelingen | Ja | [!DNL Experience Manager] Webinterface- en desktopacties |  |
| Discover - zoek naar middelen van DAM | Ja | [!DNL Experience Manager] Webinterface- en desktopacties |  |
| Gebruiken - element openen | Ja | Ja | [Openen vanuit ](manage-assets.md#previewing-assets) webinterface of vanuit Finder |
| Gebruiken - element van DAM in een document plaatsen | Ja - insluiten | Ja - koppelen of insluiten | [!DNL Experience Manager] bureaubladtoepassing biedt toegang tot elementen als bestanden op het lokale bestandssysteem. Deze koppelingen in de native apps worden weergegeven door lokale paden. |
| Bewerken - openen voor bewerking | Ja, uitchecken, actie | Ja - Handeling openen (in netwerkshare) | [Bij uitchecken in ](https://helpx.adobe.com/enterprise/using/manage-assets-using-adobe-asset-link.html) AAL wordt het middel standaard opgeslagen op de Creative Cloud Storage-account van de gebruiker (gesynchroniseerd door de Creative Cloud-app). |
| Bewerken - werk wordt uitgevoerd buiten DAM | Ja - Asset beschikbaar in de Creative Cloud-opslagaccount van de gebruiker gesynchroniseerd met desktop. | Ja |  |
| Bewerken - wijzigingen uploaden | Ja - [Inchecken van handeling](https://helpx.adobe.com/enterprise/using/manage-assets-using-adobe-asset-link.html) met optionele opmerking | Ja |  |
| Uploaden - één bestand | Ja - het actieve document wordt geüpload | Ja | [Uploaden via webinterface](manage-assets.md#uploading-assets) |
| Uploaden - meerdere bestanden / hiërarchische mapstructuren | Nee | Ja | [Uploaden via ](manage-assets.md#uploading-assets) webinterface of via aangepaste scripts of tools. |
| Diverse - gebruiker en aanmelding | Creative Cloud-gebruiker die zich heeft aangemeld bij Creative Cloud-bureaublad wordt herkend (SSO) | [!DNL Experience Manager] gebruiker en gebruikersgegevens | Gebruikers van beide oplossingen tellen mee voor de [!DNL Experience Manager] gebruikersquota. |
| Diverse - netwerk en toegang | Vereist toegang van bureaublad van gebruiker tot [!DNL Experience Manager] plaatsing over netwerk | Vereist toegang van bureaublad van gebruiker tot [!DNL Experience Manager] plaatsing over netwerk | [!DNL Adobe Asset Link] deelt geen milieu van de netwerkvolmacht. |
| Misc - Grote aantallen activa migreren | Nee | Nee | [Richtlijnen voor migratie van middelen](assets-migration-guide.md) |

Om het gebruik van middelen te steunen, zouden andere oplossingen moeten worden overwogen:

* [Merk ](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/home.html) Portalfor een configureerbare, SaaS-invoegtoepassing  [!DNL Experience Manager Assets] om elementen te publiceren.
* De oplossingen van de douane worden gecreeerd gebaseerd op [Commons van het Aandeel van activa](https://adobe-marketing-cloud.github.io/asset-share-commons/) codebasis.
* [!DNL Experience Manager] [link ](/help/assets/link-sharing.md) shareto om assets ad hoc te delen via koppelingen .
* [Experience Manager Assets web interface ](/help/assets/manage-assets.md) met gebieden voor externe partijen die worden beveiligd door  [!DNL Experience Manager] toegangsbeheerinstellingen en met noodzakelijke aanpassingen in de IT/netwerkconfiguratie, zodat deze externe gebruikers toegang hebben tot  [!DNL Experience Manager].

## Belangrijke concepten en gebruiksgevallen {#key-concepts-and-use-cases}

### Verklarende woordenlijst met algemene termen {#glossary-of-common-terms}

* **Werk in uitvoering of creatief werk in uitvoering (WIP):** Een fase in de levenscyclus van assets waarbij een asset meerdere wijzigingen ondergaat en doorgaans nog niet klaar is om te worden gedeeld met grotere teams.
* **Creative-klare middelen:** [!DNL Assets] die klaar zijn om met een breder team te worden gedeeld, of door het creatieve team zijn geselecteerd of goedgekeurd om met marketing- of LOB-teams te delen.
* **Goedkeuring van assets:** Het goedkeuringsproces dat wordt uitgevoerd voor assets die reeds naar DAM zijn geüpload, en dat typisch merkgoedkeuringen, wettelijke goedkeuringen, enz. omvat.
* **Definitieve asset:** Een asset die alle goedkeuringen/metadatatagging heeft doorlopen en klaar is om door het grotere team te worden gebruikt. Een dergelijke asset wordt opgeslagen in DAM en beschikbaar gesteld aan alle (geïnteresseerde) gebruikers. Deze kan in marketingkanalen of door creatieve teams worden gebruikt om ontwerpen te maken.
* **Kleine update/wijziging van assets:** Een snelle en kleine wijziging in een digitale asset. Deze wordt vaak uitgevoerd als reactie op een retoucheerverzoek of een verzoek om kleine bewerkingen, een assetrevisie of goedkeuring (bijvoorbeeld om de positie te wijzigen, de tekstgrootte te wijzigen, de verzadiging/helderheid en kleur aan te passen, enz.).
* **Belangrijke update/wijziging van assets:** Een verandering in een digitale asset die aanzienlijk werk vereist, en soms over een langere periode moet worden uitgevoerd. Dit omvat doorgaans meerdere wijzigingen. De asset moet tijdens het bijwerken meerdere keren worden opgeslagen. De belangrijkste assetupdates leiden er doorgaans toe dat de asset een WIP-status krijgt.
* **DAM:** Beheer van digitale assets. In dit document is dit gelijk aan [!DNL Experience Manager Assets], tenzij uitdrukkelijk anders vermeld.
* **Creatieve gebruiker:** Een creatieve professional die digitale assets maakt met Creative Cloud-apps en -services. In sommige gevallen is een creatieve gebruiker lid van een creatief team dat mogelijk Creative Cloud gebruikt, maar geen digitale assets maakt (zoals een creatieve directeur of een creatieve teammanager).
* **DAM-gebruiker:** Een typische gebruiker van een DAM-systeem. Afhankelijk van de organisatie kan een DAM-gebruiker een marketing- of niet-marketinggebruiker zijn, bijvoorbeeld een LOB-gebruiker (Line-of-Business), bibliothecaris, verkoopmedewerker, enz. zijn.

### Overwegingen bij het gebruik van [!DNL Experience Manager] en [!DNL Creative Cloud] integratie {#considerations-when-using-aem-and-creative-cloud-integration}

* Zie [Aanbevolen werkwijzen voor bureaubladtoepassing](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/troubleshoot.html?lang=en#best-practices-to-prevent-troubles)
* Zie [Adobe Stock-integratie](aem-assets-adobe-stock.md)
* Zie [Adobe Asset Link](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html)

Dit is een korte samenvatting van beste praktijken voor [!DNL Experience Manager] en [!DNL Creative Cloud] integratie. Lees de rest van dit document voor een gedetailleerd begrip hiervan.

* **Voor creatieve gebruikers die in Photoshop, InDesign of Illustrator werken:** Adobe Asset Link biedt de beste gebruikerservaring, zoals een schone verwerking van het werk in uitvoering op assets die zijn uitgecheckt bij [!DNL Experience Manager].
* **Voor eenvoudige toegang tot middelen van het bureaublad voor elke algemene bestandsindeling of toepassing:** gebruik de  [!DNL Experience Manager] bureaubladtoepassing.
* **Begrijpen waarom en wanneer assets in DAM moeten worden opgeslagen:** Updates die ter beschikking moeten worden gesteld aan een groter team in uw organisatie.
* **Houd rekening met het volume van de gedeelde assets:** Als u gebruikmaakt van assetdistributie, kunnen governance en beveiliging de belangrijkste aspecten zijn. Overweeg om tools te gebruiken die bedoeld zijn om governance en beveiliging op grote schaal toe te passen, zoals de Brand Portal.
* **De levenscyclus van assets begrijpen:** Begrijp hoe assets in uw organisatie worden verwerkt door verschillende teams
* **Correct en regelmatig opslaan van assets:** Adobe Asset Link doet dit voor u met PS, AI, ID. Voer voor andere applicaties geen taken in uitvoering uit in een toegewezen/gedeelde map, tenzij u alle wijzigingen in DAM nodig hebt

### Toegang tot [!DNL Adobe Stock] elementen van [!DNL Assets] {#access-to-adobe-stock-assets-from-aem-assets}

[Experience Manager- en Adobe Stock-](/help/assets/aem-assets-adobe-stock.md) integratie biedt  [!DNL Experience Manager] gebruikers de mogelijkheid om te zoeken, een voorvertoning weer te geven, licenties te maken en op te slaan, middelen van  [!DNL Adobe Stock] naar  [!DNL Experience Manager]. Met licentie- en opgeslagen [!DNL Stock]-elementen zijn [!DNL Stock]-metagegevens geselecteerd, die kunnen worden gebruikt om met extra filters naar deze bestanden te zoeken.

Een paar belangrijke punten over deze integratie:

* Wanneer elementen uit Adobe-voorraad worden opgeslagen naar [!DNL Experience Manager], worden ze een gewone [!DNL Assets], met binair opgeslagen naar de [!DNL Experience Manager]-opslagplaats. Sommige metagegevens die betrekking hebben op [!DNL Adobe Stock] worden voor het element opgeslagen in [!DNL Experience Manager], anders ziet het innameproces er hetzelfde uit als voor elk ander bestand. Als slimme tags bijvoorbeeld actief zijn, worden de tags bij het opslaan aan deze elementen toegevoegd.
* Het element dat is opgeslagen naar [!DNL Experience Manager] is een kopie en geen koppeling die weer wordt opgeslagen naar [!DNL Adobe Stock].

**Werken met elementen die zijn opgeslagen van  [!DNL Adobe Stock] naar  [!DNL Experience Manager] in[!DNL Creative Cloud]**. Deze integratie is onafhankelijk van [!DNL Adobe Asset Link], maar [!DNL Adobe Asset Link] herkent deze activa bewaard van [!DNL Stock] die manier, en toont extra meta-gegevens en een [!DNL Adobe Stock] embleem op deze activa in [!DNL Adobe Asset Link] uitbreiding UI in [!DNL Photoshop], [!DNL Illustrator], of [!DNL InDesign]. De bestanden zijn beschikbaar voor bladeren, openen, enzovoort, omdat het normale bestanden zijn wanneer deze worden opgeslagen op [!DNL Experience Manager].
Creatieve gebruikers die werken in [!DNL Creative Cloud]-apps met [!DNL Adobe Asset Link]-extensie aanwezig, hebben naast toegang tot middelen met een licentie van [!DNL Adobe Stock] tot [!DNL Experience Manager], ook toegang tot [!DNL Creative Cloud]-bibliotheken om [!DNL Adobe Stock]-middelen te zoeken, voor te vertonen en te licentiëren.
[!DNL Assets] van  [!DNL Adobe Stock] gelicentieerd en opgeslagen in  [!DNL Experience Manager] worden beschikbaar voor de bredere teams die toegang hebben tot  [!DNL Experience Manager Assets] implementatie, terwijl creatieve licentiefaciliteiten van  [!DNL Adobe Stock] via het deelvenster  [!DNL Creative Cloud] Bibliotheken ze alleen standaard beschikbaar maken in hun  [!DNL Creative Cloud] account.

<!-- 
TBD: A condensed version of the below content is better placed in the Adobe DAM introduction article.
-->

## Informatie over het opslaan van elementen in een DAM {#about-storing-assets-in-a-dam}

Om een efficiënte werkstroom tussen creatieve en marketing/lijn-van-zaken (LOB) teams te ontwerpen en de beste steunmogelijkheden te kiezen, is het belangrijk om te begrijpen wanneer en waarom de activa in DAM worden opgeslagen.

### Waarom elementen zijn opgeslagen in DAM {#why-assets-are-stored-in-dam}

Door middelen in DAM op te slaan, zijn ze gemakkelijk toegankelijk en te vinden. Het zorgt ervoor dat de activa door talrijke gebruikers over de organisatie of het ecosysteem kunnen worden gebruikt, dat partners, klanten, etc. omvat.

De meeste organisaties kiezen ervoor om activa slechts op te slaan die voor de stroomafwaartse marketing/LOB processen relevant zijn (het publiceren aan kanalen zoals Webkanaal via [!DNL Experience Manager Sites] of andere kanalen die door Adobe Experience Cloud - Marketing Cloud, Advertising Cloud worden gediend, en door Analytics Cloud worden gemeten, die aan gebruikers/partners, etc. verstrekken). Bovendien slaan organisaties activa op die aan een overzicht/goedkeuringsprocedure in DAM kunnen worden onderworpen. Op deze manier slaat DAM vooral activa op die een hoge kans hebben om te worden gebruikt, en vermijdt het opslaan van niet-actieve activa.

De opslag van activa is ook onderworpen aan technische overwegingen en middelgebruik. DAM verleent de extra diensten rond opgeslagen activa, met inbegrip van het halen van meta-gegevens, het versioning, het produceren van voorproeven/het transcoderen, het beheren van verwijzingen, en het toevoegen van toegangsbeheerinformatie. Deze diensten verbruiken extra tijd en infrastructuurmiddelen.

Vaak is het niet wenselijk om alle elementen en updates op te slaan. Bijvoorbeeld, als de updates aan specifieke activa van slechte kwaliteit zijn en bovenmatige middelen verbruiken, kunnen de activa niet in DAM worden opgeslagen.

#### Wanneer elementen worden opgeslagen in DAM {#when-assets-are-stored-in-dam}

Creatieve teams (en organisaties) zijn gewoonlijk niet geïnteresseerd in het opslaan van middelen in elke fase van de levenscyclus van de middelen. In de volgende gevallen worden bijvoorbeeld geen elementen opgeslagen:

* Activa die nog moeten worden afgerond of die moeten worden getest.
* Middelen die de beoordelingscyclus van het creatieve/interne team niet doorstaan.
* Vergeleken met de middelen in kwestie, heeft het team betere kandidaten om hun werk aan externe teams te vertegenwoordigen.

Gewoonlijk worden de volgende klassenelementen opgeslagen in DAM:

* Activa die een bepaalde looptijd hebben bereikt en die als gereed worden beschouwd om te worden gedeeld.
* Elementen die vooraf zijn geselecteerd door het creatieve team.
* Bepaalde indelingen voor elementen die kunnen worden gebruikt of aangevraagd door marketing, afhankelijk van een specifiek contract of een specifieke overeenkomst (bijvoorbeeld JPG-bestanden die zijn geconverteerd van RAW-bestanden, TIFF-bestanden/afbeeldingen van PSD-originelen).

#### Wanneer updates van elementen worden opgeslagen in DAM {#when-updates-to-assets-are-stored-in-dam}

Normaliter moeten alleen updates van middelen die relevant zijn voor de bredere reeks DAM-gebruikers in DAM worden opgeslagen. Hiermee zorgt u ervoor dat gebruikers (marketing en soortgelijke functies) alleen relevante versies in de tijdlijn van de DAM-middelen zien.

Doorgaans zijn er wijzigingen die betrekking hebben op belangrijke mijlpalen in de levenscyclus van de middelen. Het eerste marketingklare middel of een officiële update op basis van een verzoek/revisie van het creatieve team moet bijvoorbeeld worden opgeslagen en gecontroleerd in DAM.

De update van het creatieve team voor revisie door het marketingteam na een verzoek om wijziging van het bestaande middel in DAM is een voorbeeld van een relevante update. Het zou in DAM voor verdere verwijzing of voor het terugkeren naar de vorige versie moeten worden opgeslagen en worden versioned.

Hieronder volgen voorbeelden van updates die doorgaans niet relevant zijn:

* Vroege versies van elementen die zijn geüpload voordat ze klaar zijn voor marketingcontrole
* Veelvoorkomende creatieve wijzigingen in het bedrijfsmiddel in de aan de gang zijnde fase voordat creatieve en marketingteams besluiten dat het middel klaar is

### Toegang van gebruikers tot DAM {#user-access-to-dam}

[!DNL Assets] ondersteunt twee soorten gebruikers op basis van hun toegang tot de  [!DNL Assets] implementatie. Doorgaans hebben gebruikers binnen het bedrijfsnetwerk (firewall) directe toegang tot DAM. Andere gebruikers buiten het ondernemingsnetwerk zouden geen directe toegang hebben. Het gebruikerstype bepaalt welke integraties vanuit technisch oogpunt kunnen worden gebruikt.

#### Creatieve gebruikers met directe toegang tot DAM {#creative-users-with-direct-access-to-dam}

In het algemeen hebben interne creatieve teams of agentschappen/creatieve professionals die aan het interne netwerk zijn toegewezen, toegang tot de DAM-implementatie, inclusief [!DNL Experience Manager]-aanmelding. [!DNL Experience Manager] en de netwerkinfrastructuur kan opstelling zijn om directe toegang tot externe partijen - gewoonlijk vertrouwde op organisaties zoals agentschappen toe te staan die voor een cliënt werken - om toegang tot  [!DNL Experience Manager] over netwerk, bijvoorbeeld via VPN of IP lijst van gewenste personen te hebben.

In dergelijke gevallen helpt de Adobe Asset Link of de [!DNL Experience Manager]-bureaubladtoepassing u eenvoudig toegang te krijgen tot definitieve/goedgekeurde middelen en kunt u creatieve middelen opslaan naar DAM.

#### Creatieve gebruikers zonder toegang tot DAM {#creative-users-without-access-to-dam}

Externe agentschappen en freelancers zonder directe toegang tot de DAM-implementatie hebben mogelijk toegang tot goedgekeurde middelen nodig of willen hun nieuwe ontwerpen toevoegen aan de DAM.

Gebruik de volgende strategieën om toegang te verlenen tot definitieve/goedgekeurde middelen:

* Gebruik de bureaubladtoepassing als Asset Link niet werkt.
* Gebruik [Experience Manager Assets Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/home.html) voor het veilig distribueren van elementen aan externe partners
* Gebruik een aangepaste implementatie van een distributie- en sourcingportal op basis van [Commons voor het delen van bedrijfsmiddelen](https://adobe-marketing-cloud.github.io/asset-share-commons/)
* Het Toegangsbeheer van het gebruik in [!DNL Experience Manager] en noodzakelijke netwerkinfrastructuur (bijvoorbeeld, VPN en IP lijst van gewenste personen) wordt opgezet om externe partijen toegang tot een specifiek gebied van inhoud in uw DAM te geven dat. Ze kunnen [!DNL Experience Manager] Web UI gebruiken om middelen op te halen en nieuwe inhoud te uploaden in uw DAM.

#### Werk bezig met middelen van [!DNL Experience Manager] {#work-in-progress-on-assets-from-aem}

Zoals in dit document wordt besproken, wordt aanbevolen belangrijke updates van elementen uit te voeren, ook wel &#39;werk in uitvoering&#39; genoemd, zonder dat alle bewerkingen die in het lokale bestand zijn opgeslagen, als wijzigingen naar [!DNL Experience Manager] worden geüpload. Dit versnelt het werk van een Desktopgebruiker, beperkt gebruikte netwerkbandbreedte, en houdt de activa chronologie schoon en concentreert zich op gecontroleerde, belangrijke updates.

Adobe Asset Link biedt een goede ondersteuning voor dit gebruiksgeval:

* Wanneer gebruikers in [!DNL Photoshop], [!DNL InDesign], of [!DNL Illustrator] intent om een dossier uit te geven, voeren zij een Controle op het bepaalde middel uit
* Het middel wordt gedownload op de achtergrond, in gebruikersCreative Cloud-account gesynchroniseerd op schijf door Creative Cloud desktop app, en de markering voor uitchecken wordt ingeschakeld in [!DNL Experience Manager] op het middel om bewerkingsconflicten te minimaliseren
* Vanaf dat punt werkt de gebruiker in een bestand dat lokaal is opgeslagen op de gesynchroniseerde locatie. De gebruiker kan doorgaan met het werken en opslaan van noodzakelijke wijzigingen met elke vereiste frequentie
* Aangezien het element zich in de Creative Cloud-account bevindt, is het ook beschikbaar op andere apparaten die de gebruiker mogelijk heeft (kunnen bijvoorbeeld worden geopend of bewerkt in een speciale mobiele Creative Cloud-app) en kan het voor samenwerkingsdoeleinden worden gedeeld met andere Creative Cloud-gebruikers.
* Wanneer de creatieve gebruiker klaar is met de wijzigingen, kan hij of zij een incheckbewerking op dat bestand uitvoeren in zijn of haar Creative Cloud-toepassing, met een optionele opmerking. Het overeenkomstige element in [!DNL Experience Manager] wordt versioned en bijgewerkt aan met het nieuwe binaire getal. [!DNL Experience Manager] gebruikers zoals Marketers of LOB-gebruikers hebben via de tijdlijninterface van  [!DNL Experience Manager] middelen toegang tot belangrijke wijzigingen in activa of mijlpalen.

[!DNL Experience Manager] desktop app biedt netwerkshare voor middelen die zijn geopend in de native app. Standaard worden alle lokaal uitgevoerde wijzigingen na een korte tijd automatisch geüpload naar [!DNL Experience Manager]. Met zo&#39;n configuratie, zou het frequente besparen tijdens de werk-in-lopende fase allen in [!DNL Experience Manager] worden geupload en versioned, die tot veel netwerkverkeer en potentiële scalability uitdagingen leiden - om onnodige versies in [!DNL Experience Manager] te noemen.

Hier kunt u het beste een optie in de [!DNL Experience Manager]-bureaubladtoepassing gebruiken om geautomatiseerde updates uit te schakelen en wijzigingen in elementen handmatig te uploaden naar [!DNL Experience Manager], waarbij u de actie voor uploadwijzigingen gebruikt in de statusinterface van de app voor bedrijfsmiddelen.

#### Bulkupload naar DAM {#bulk-upload-to-dam}

In sommige gevallen moet u wellicht een groter aantal bestanden tegelijkertijd uploaden naar DAM, bijvoorbeeld:

* Resultaten van foto&#39;s of grotere projecten uploaden
* Door creatieve bureaus geleverde activa uploaden
* Geselecteerde elementen uploaden vanaf een grotere set als de selectie buiten DAM is uitgevoerd

De beschrijving verwijst naar het operationeel uploaden van bestanden (bijvoorbeeld elke week of met elke foto), als een normaal onderdeel van de workflow van de desktopgebruiker. De migratie van grote activa wordt hier niet behandeld.

U kunt de volgende uploadmogelijkheden gebruiken:

* Als u grote/hiërarchische mappen bulksgewijs wilt uploaden, gebruikt u [!DNL Experience Manager]-bureaubladtoepassing die [functionaliteit voor het uploaden van mappen](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=en#upload-and-add-new-assets-to-aem) biedt. U kunt ook hiërarchische mapstructuren uploaden. [!DNL Assets] worden geüpload op de achtergrond en zijn daarom niet gekoppeld aan een webbrowsersessie
* Als u enkele bestanden uit één map wilt uploaden, sleept u de bestanden rechtstreeks naar de webinterface of gebruikt u de optie Maken in de webinterface [!DNL Assets].
* Afhankelijk van uw bedrijfsvereisten kunt u ook aangepaste uploader gebruiken.

#### Digitale middelen rechtstreeks vanaf desktop beheren {#managing-digital-assets-directly-from-desktop}

Als u Delen van netwerkbestanden gebruikt om digitale elementen te beheren, kan alleen het gebruik van de netwerkshare die is toegewezen door de [!DNL Experience Manager]-bureaubladtoepassing worden beschouwd als een handige vervanging. Wanneer u overschakelt van gedeelde netwerkbestanden, biedt de [!DNL Experience Manager]-webinterface een uitgebreide reeks mogelijkheden voor beheer van digitale bedrijfsmiddelen die veel verder gaan dan wat mogelijk is op een netwerk (zoeken, verzamelingen, metagegevens, samenwerking, voorvertoningen, enzovoort) en de [!DNL Experience Manager]-bureaubladtoepassing biedt een handige koppeling om de server-side DAM-opslagplaats te verbinden met het werk op de desktop.

Vermijd het gebruik van [!DNL Experience Manager]-bureaubladtoepassing om elementen rechtstreeks te beheren in het netwerkaandeel van [!DNL Assets]. Vermijd bijvoorbeeld het gebruik van [!DNL Experience Manager] desktop app om meerdere bestanden te verplaatsen/kopiëren. Gebruik in plaats daarvan de [!DNL Assets]-interface om mappen van Finder/Explorer naar het gedeelde netwerk te slepen of gebruik de functie [!DNL Assets] Map uploaden.

#### Migratie van bedrijfsmiddelen {#asset-migration}

Raadpleeg de [Migratiegids](/help/assets/assets-migration-guide.md) voor informatie over het plannen en uitvoeren van migratie van bedrijfsmiddelen van een bestaand systeem naar een nieuw systeem of voor de migratie van grote hoeveelheden bedrijfsmiddelen die op servers zijn opgeslagen. [!DNL Experience Manager] bureaubladtoepassingen en  [!DNL Experience Manager] de  [!DNL Creative Cloud] integratie bieden geen ondersteuning voor dergelijke migraties. Vanwege de grote hoeveelheden in te nemen elementen en de extra vereisten met betrekking tot het in kaart brengen van metagegevens, transformatie en opname, moeten migraties met verschillende gereedschappen en benaderingen worden afgehandeld.

>[!MORELIKETHIS]
>
>* [Adobe-itemkoppeling](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html)
>* [Aanbevolen werkwijzen voor bureaublad van Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/archive/best-practices-for-v1.html)
>* [Experience Manager Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/introduction/brand-portal.html)
>* [Integratie van Experience Manager en Adobe Stock](aem-assets-adobe-stock.md)

