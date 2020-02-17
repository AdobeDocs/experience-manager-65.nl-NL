---
title: Aanbevolen werkwijzen voor AEM- en Creative Cloud-integratie
description: Aanbevolen procedures om AEM te integreren met Adobe Creative Cloud om workflows voor middelenoverdracht te stroomlijnen en maximale efficiëntie te bereiken.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0ff23556444fcb161b0adf744bb72fdc50322d92

---


# Aanbevolen werkwijzen voor AEM- en Creative Cloud-integratie {#aem-and-creative-cloud-integration-best-practices}

<!-- TBD: Reconcile with 6.4 article that's behind this article in terms of content streamlining and structuring.
-->

Adobe Experience Manager Assets is een DAM-oplossing (Digital Asset Management) die kan worden geïntegreerd met Adobe Creative Cloud om DAM-gebruikers te helpen met creatieve teams samen te werken en de samenwerking bij het maken van inhoud te stroomlijnen.

Adobe Creative Cloud biedt creatieve teams een ecosysteem van oplossingen en services waarmee ze digitale middelen kunnen maken. Hieronder vallen desktoptoepassingen en mobiele toepassingen, cloudservices zoals opslag met desktopsynchronisatie of webervaring, en markten zoals Adobe Stock.

Lees verder om te weten welke integraties u kunt kiezen tussen desktop en DAM op bedrijfsniveau op basis van uw gebruiksscenario en wat de bijbehorende beste werkwijzen zijn voor de verbindingsworkflows.

>[!NOTE]
>
>Het delen van mappen van AEM naar Creative Cloud is verouderd en wordt niet langer behandeld in deze handleiding. Adobe raadt u aan nieuwere mogelijkheden, zoals [Adobe Asset Link](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html) of de AEM-bureaubladtoepassing [](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/introduction.html) , te gebruiken om creatieve gebruikers toegang te bieden tot middelen die in AEM worden beheerd.

## De behoeften van de samenwerking van creatieven, verkopers, en gebruikers DAM {#collaboration-needs-of-creatives-marketers-and-dam-users}

| Vereisten | Hoofdletters gebruiken | Betrokken oppervlakken |
|---|---|---|
| Ervaring voor creatieve producten op desktopcomputers vereenvoudigen | Toegang tot middelen van een DAM (AEM Assets) stroomlijnen voor creatieve professionals, of meer in het algemeen gebruikers op desktopcomputers die werken in toepassingen voor het maken van native bedrijfsmiddelen. Ze hebben een eenvoudige en eenvoudige manier nodig om wijzigingen in AEM te detecteren, te gebruiken (openen), te bewerken en op te slaan, en om nieuwe bestanden te uploaden. | Win- of Mac-bureaublad; Creative Cloud-toepassingen |
| Middelen van Adobe Stock van hoge kwaliteit en gebruiksklaar maken | Marketers helpen het proces voor het maken van inhoud te versnellen door hulp te bieden bij het aanschaffen en detecteren van bedrijfsmiddelen. Creatieve professionals gebruiken de goedgekeurde middelen direct vanuit hun creatieve gereedschappen. | AEM-activa; Adobe Stock MarketPlace; metagegevensvelden |
| Elementen distribueren en delen door organisaties | De interne afdelingen/de lokale takken en de externe partners, de distributeurs, en de agentschappen gebruiken de goedgekeurde activa die door de ouderorganisatie worden gedeeld. De organisatie wil de gemaakte middelen veilig en naadloos delen voor breder hergebruik. | Merkportal, Commentaar voor delen van bedrijfsmiddelen |

## Adobe-aanbiedingen ter ondersteuning van de behoefte aan samenwerking {#adobe-offerings-to-support-the-collaboration-need}

| Waardevoorstel voor de betreffende personen | Adobe-aanbieding | Betrokken oppervlakken |
|---|---|---|
| Creatieve gebruikers ontdekken elementen van AEM, openen en gebruiken deze, bewerken en uploaden wijzigingen in AEM en uploaden nieuwe bestanden naar AEM zonder Creative Cloud-apps te verlaten. | [Adobe-elementkoppeling](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html) | Photoshop, Illustrator en InDesign |
| Zakelijke gebruikers vereenvoudigen het openen en gebruiken van middelen, het bewerken en uploaden van wijzigingen in AEM en het uploaden van nieuwe bestanden naar AEM vanuit de desktopomgeving. Ze gebruiken een algemene integratie om elk elementtype in de native bureaubladtoepassing te openen, inclusief niet-Adobe toepassingen. | [AEM-bureaubladtoepassing](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/using.html) | AEM-bureaubladtoepassing op Windows- en Mac-bureaublad |
| Marketers en zakelijke gebruikers ontdekken, voorvertonen, licentiëren en opslaan de Adobe Stock Assets vanuit AEM en beheren deze. Gelicentieerde en opgeslagen middelen bieden geselecteerde Adobe Stock-metagegevens voor beter beheer. | [Experience Manager en Adobe Stock-integratie](aem-assets-adobe-stock.md) | AEM-webinterface |

Dit artikel richt zich hoofdzakelijk op de eerste twee aspecten van de samenwerkingsbehoeften. Distributie en aanschaf van activa op schaal wordt kort als gebruiksscenario genoemd. Overweeg Adobe Brand Portal of Asset Share Commons voor dergelijke oplossingen. Alternatieve oplossingen zoals het Portaal [van het](https://helpx.adobe.com/experience-manager/brand-portal/user-guide.html)Merk, oplossingen die op de componenten van het Aandeel van [Activa](https://adobe-marketing-cloud.github.io/asset-share-commons/) , het Aandeel [van de](/help/assets/link-sharing.md)Verbinding, gebruikend de Elementen [van de Manager van de](/help/assets/managing-assets-touch-ui.md) Ervaring kunnen worden gebouwd zouden op specifiek vereiste moeten worden herzien.

![Creative Cloud-verbindingen voor AEM: Bepalen welke mogelijkheid moet worden gebruikt](assets/creative-connections-aem.png)

### Toewijzing van gebruiksgevallen en Adobe-oplossingen {#mapping-of-use-cases-and-adobe-solutions}

| Hoofdletters gebruiken | Adobe-elementkoppeling | AEM-bureaubladtoepassing | Opmerkingen/andere oplossingen |
|---|---|---|---|
| Detecteren - door AEM-mappen bladeren | Ja | AEM Web UI + Desktopacties | Als u op het gedeelde netwerk bladert, schakelt u de miniaturen uit om te voorkomen dat binaire bestanden met elementen worden gedownload. |
| Discover - toegang tot AEM-verzamelingen | Ja | AEM Web UI + Desktopacties |  |
| Discover - zoek naar middelen van AEM | Ja | AEM Web UI + Desktopacties |  |
| Gebruiken - element openen | Ja | Ja, voor elke app | [Openen vanuit webinterface](managing-assets-touch-ui.md#previewing-assets) of vanuit Finder |
| Gebruiken - middelen van AEM in een document plaatsen | Ja - insluiten | Ja - koppelen of insluiten | De AEM-bureaubladtoepassing biedt toegang tot elementen als bestanden op het lokale bestandssysteem. Deze koppelingen in de native apps worden weergegeven door lokale paden. |
| Bewerken - openen voor bewerking | Ja, uitchecken, actie | Ja - Handeling openen (in netwerkshare) | [Met Uitchecken in AAL](https://helpx.adobe.com/enterprise/using/manage-assets-using-adobe-asset-link.html) wordt het middel standaard opgeslagen op de Creative Cloud Storage-account (gesynchroniseerd door de Creative Cloud-toepassing) van de gebruiker. |
| Bewerken - werk wordt uitgevoerd buiten AEM | Ja, middelen beschikbaar in de Creative Cloud-opslagaccount van de gebruiker worden gesynchroniseerd met bureaublad. | Ja |  |
| Bewerken - wijzigingen uploaden | Ja - [Inchecken](https://helpx.adobe.com/enterprise/using/manage-assets-using-adobe-asset-link.html) met optionele opmerking | Ja |  |
| Uploaden - één bestand | Ja - het actieve document wordt geüpload | Ja | [Uploaden via webinterface](managing-assets-touch-ui.md#uploading-assets) |
| Uploaden - meerdere bestanden / hiërarchische mapstructuren | Nee | Ja | [Uploaden via webinterface](managing-assets-touch-ui.md#uploading-assets);<br>Aangepaste scripts of gereedschappen |
| Diverse - gebruiker en aanmelding | Creative Cloud-gebruiker die zich heeft aangemeld bij Creative Cloud-bureaubladtoepassing wordt herkend (SSO) | AEM-gebruiker/aanmelding | Gebruikers van beide oplossingen tellen mee voor de AEM-gebruikersquota. |
| Diverse - netwerk en toegang | Vereist toegang van de Desktop van de gebruiker tot AEM plaatsing over netwerk | Vereist toegang van de Desktop van de gebruiker tot AEM plaatsing over netwerk | Adobe Asset Link deelt de omgeving van de netwerkproxy niet. |
| Misc - Grote aantallen activa migreren | Nee | Nee | [Migratiehandleiding](assets-migration-guide.md) |

Om het gebruik van middelen te steunen, zouden andere oplossingen moeten worden overwogen:

* [Brand Portal](https://helpx.adobe.com/experience-manager/brand-portal/user-guide.html) voor een configureerbare SaaS-invoegtoepassing op AEM-middelen om elementen te publiceren.
* De oplossingen van de douane worden gecreeerd gebaseerd op de codebasis van de Commons [van het Aandeel van](https://adobe-marketing-cloud.github.io/asset-share-commons/) Activa.
* AEM- [koppelingen delen](/help/assets/link-sharing.md) met koppelingen om elementen ad hoc te delen.
* [AEM Middelen Webinterface](/help/assets/managing-assets-touch-ui.md) met gebieden voor externe partijen die door de opstelling van het Toegangsbeheer van AEM en met noodzakelijke aanpassingen van IT/netwerkconfiguratie worden beveiligd, die deze externe gebruikers toegang tot AEM geven.

## Belangrijkste concepten en gebruiksgevallen {#key-concepts-and-use-cases}

### Verklarende woordenlijst {#glossary-of-common-terms}

* **** Werk in uitvoering of creatief werk in uitvoering (WIP): Een fase in de levenscyclus van bedrijfsmiddelen waarbij een middel meerdere wijzigingen ondergaat en doorgaans nog niet klaar is om te worden gedeeld met bredere teams.
* **** Creatieve elementen: Elementen die klaar zijn om te worden gedeeld met een breder team, of die zijn geselecteerd/goedgekeurd door het creatieve team voor delen met marketing- of LOB-teams.
* **** Goedkeuring van bedrijfsmiddelen: Het goedkeuringsproces dat loopt voor activa die reeds aan DAM worden geupload, die typisch merkgoedkeuringen, wettelijke goedkeuringen, etc. omvat.
* **** Definitief actief: Een middel dat door alle goedkeuringen/meta-gegevens het etiketteren is gegaan en klaar is om door het bredere team te worden gebruikt. Een dergelijk middel wordt opgeslagen in DAM en beschikbaar gesteld aan alle (of alle geïnteresseerde) gebruikers. Het kan in marketing kanalen of door creatieve teams worden gebruikt om ontwerpen tot stand te brengen.
* **** Kleine update/wijziging van bedrijfsmiddelen: Een snelle en kleine wijziging in een digitaal middel. Deze wordt vaak uitgevoerd als reactie op een retoucheerverzoek of een verzoek om kleine bewerkingen, een elementenrevisie of goedkeuring (bijvoorbeeld door de positie te wijzigen, de tekstgrootte te wijzigen, de verzadiging/helderheid, de kleur aan te passen, enzovoort).
* **** Belangrijke update/wijziging van bedrijfsmiddelen: Een verandering in een digitaal goed dat aanzienlijk werk vereist, en soms over een langere periode moet gebeuren. Dit omvat doorgaans meerdere wijzigingen. Het element moet tijdens het bijwerken meerdere keren worden opgeslagen. De belangrijkste activa updates veroorzaken typisch de activa om een stadium van het WIP in te gaan.
* **** DAM: Beheer van digitale middelen. In dit document is dit gelijk aan AEM Experience Manager-middelen, tenzij anders vermeld.
* **** Creatieve gebruiker: Een creatieve professional die digitale middelen maakt met Creative Cloud-apps en -services. In sommige gevallen is een creatieve gebruiker lid van een creatief team dat mogelijk Creative Cloud gebruikt, maar geen digitale middelen maakt (zoals een creatieve directeur of een creatieve teammanager).
* **** DAM-gebruiker: Een typische gebruiker van een systeem DAM. Afhankelijk van de organisatie, kan een gebruiker DAM een marketing of een niet-marketing gebruiker, bijvoorbeeld een Line-of-Business (LOB) gebruiker, bibliothecaris, verkooppersoon, etc. zijn.

### Overwegingen bij het gebruik van de integratie met AEM en Creative Cloud {#considerations-when-using-aem-and-creative-cloud-integration}

* Zie aanbevolen werkwijzen voor [bureaubladtoepassingen](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/troubleshoot.html#best-practices-to-prevent-troubles)
* Zie [Adobe Stock Integration](aem-assets-adobe-stock.md)
* Zie [Adobe Asset Link](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html)

Hier volgt een korte samenvatting van aanbevolen procedures voor Experience Manager en Creative Cloud-integratie. Lees de rest van dit document voor een gedetailleerd begrip hiervan.

* **** Voor creatieve gebruikers die in Photoshop, InDesign of Illustrator werken: Adobe Asset Link biedt de beste gebruikerservaring, zoals een schone verwerking van de onderhanden werk op middelen die zijn uitgecheckt bij AEM
* **** Voor het vereenvoudigen van de toegang tot middelen van de Desktop voor om het even welke generische dossierformaat of toepassing: AEM-bureaubladtoepassing gebruiken
* **** Begrijp waarom en wanneer om activa in DAM op te slaan: Updates die ter beschikking moeten worden gesteld aan het bredere team in uw organisatie
* **** Bedenk het volume van de gedeelde elementen: Als je gebruik maakt van vermogensdistributie, kunnen bestuur en beveiliging de belangrijkste aspecten zijn. Overweeg om hulpmiddelen te gebruiken die voor het doen van dat bij schaal, zoals het Portaal van het Merk worden gebouwd.
* **** Levenscyclus van middelen begrijpen: Weet hoe elementen in uw organisatie worden verwerkt door verschillende teams
* **** Regelmatig opslaan van middelen met zorg afhandelen: Adobe Asset Link verzorgt die voor u met PS, AI, ID. Voer voor andere toepassingen geen actieve taken uit in toegewezen/gedeelde map tenzij u alle wijzigingen in DAM nodig hebt

### Toegang tot Adobe Stock Assets van AEM Assets {#access-to-adobe-stock-assets-from-aem-assets}

[Met AEM en de Adobe Stock Integration](/help/assets/aem-assets-adobe-stock.md) kunnen AEM-gebruikers middelen van Adobe Stock zoeken, voorvertonen, licentiëren en opslaan in AEM. In Adobe Stock-elementen met licentie en opgeslagen gegevens zijn de metagegevens van de bestanden geselecteerd. Deze gegevens kunnen worden gebruikt om met extra filters naar deze bestanden te zoeken.

Een paar belangrijke punten over deze integratie:

* Wanneer middelen uit Adobe-bestanden naar AEM worden opgeslagen, worden ze een gewone AEM-middelen, waarbij het binaire getal wordt opgeslagen in de AEM-opslagplaats. Sommige metagegevens die betrekking hebben op Adobe Stock worden opgeslagen voor het element in AEM. Als dit niet het geval is, ziet het innameproces er hetzelfde uit als voor andere bestanden. Als slimme tags bijvoorbeeld actief zijn, worden de tags bij het opslaan aan deze elementen toegevoegd.
* Het aan AEM opgeslagen middel is een kopie en geen koppeling naar Adobe Stock.

**Werken met middelen die zijn opgeslagen van Adobe Stock in AEM in Creative Cloud**. Deze integratie is onafhankelijk van Adobe Asset Link, maar Adobe Asset Link herkent deze middelen die op die manier uit Stock zijn opgeslagen en geeft aanvullende metagegevens en het pictogram Stock weer voor deze middelen in de gebruikersinterface van de Adobe Asset Link-extensie in Photoshop, Illustrator of InDesign. De bestanden zijn beschikbaar voor bladeren, openen, enzovoort, omdat het normale AEM-elementen zijn die worden opgeslagen in AEM.
Creatieve gebruikers die werken in Creative Cloud-apps met de Adobe Asset Link-extensie, hebben niet alleen toegang tot middelen met een licentie van Adobe Stock in AEM, maar kunnen ook het deelvenster Creative Cloud Libraries gebruiken om Adobe Stock-middelen te zoeken, voor te vertonen en in licentie te geven.
Elementen van Adobe Stock die in licentie zijn gegeven en in AEM zijn opgeslagen, worden beschikbaar voor bredere teams die toegang hebben tot de implementatie van AEM Assets, terwijl creatieve licentiebestanden van Adobe Stock via het deelvenster Creative Cloud Libraries ze alleen standaard beschikbaar maken voor zichzelf in hun Creative Cloud-account.

<!-- 
TBD: A condensed version of the below content is better placed in the Adobe DAM article.
-->

## Elementen opslaan in een DAM {#about-storing-assets-in-a-dam}

Om een efficiënte werkstroom tussen creatieve en marketing/lijn-van-zaken (LOB) teams te ontwerpen en de beste steunmogelijkheden te kiezen, is het belangrijk om te begrijpen wanneer en waarom de activa in DAM worden opgeslagen.

### Waarom elementen zijn opgeslagen in DAM {#why-assets-are-stored-in-dam}

Door middelen in DAM op te slaan, zijn ze gemakkelijk toegankelijk en te vinden. Het zorgt ervoor dat de activa door talrijke gebruikers over de organisatie of het ecosysteem kunnen worden gebruikt, dat partners, klanten, etc. omvat.

De meeste organisaties kiezen ervoor alleen middelen op te slaan die relevant zijn voor de downstream marketing-/LOB-processen (publiceren naar kanalen zoals webkanalen via AEM-sites of andere kanalen die worden aangeboden door Adobe Experience Cloud - Marketing Cloud, Advertising Cloud, en gemeten door Analytics Cloud, leveren aan gebruikers/partners, enzovoort). Bovendien slaan organisaties activa op die aan een overzicht/goedkeuringsprocedure in DAM kunnen worden onderworpen. Op deze manier slaat DAM vooral activa op die een hoge kans hebben om te worden gebruikt, en vermijdt het opslaan van niet-actieve activa.

De opslag van activa is ook onderworpen aan technische overwegingen en middelgebruik. DAM verleent de extra diensten rond opgeslagen activa, met inbegrip van het halen van meta-gegevens, het versioning, het produceren van voorproeven/het transcoderen, het beheren van verwijzingen, en het toevoegen van toegangsbeheerinformatie. Deze diensten verbruiken extra tijd en infrastructuurmiddelen.

Vaak is het niet wenselijk om alle elementen en updates op te slaan. Bijvoorbeeld, als de updates aan specifieke activa van slechte kwaliteit zijn en bovenmatige middelen verbruiken, kunnen de activa niet in DAM worden opgeslagen.

#### Wanneer elementen zijn opgeslagen in DAM {#when-assets-are-stored-in-dam}

Creatieve teams (en organisaties) zijn gewoonlijk niet geïnteresseerd in het opslaan van middelen in elke fase van de levenscyclus van de middelen. In de volgende gevallen worden bijvoorbeeld geen elementen opgeslagen:

* Activa die nog moeten worden afgerond of die moeten worden getest
* Middelen die niet de cyclus van het creatieve/interne teamoverzicht doorstaan
* Vergeleken met de middelen in kwestie, heeft het team betere kandidaten om hun werk aan externe teams te vertegenwoordigen

Gewoonlijk worden de volgende klassenelementen opgeslagen in DAM:

* Activa die een bepaalde looptijd hebben bereikt en die klaar worden geacht om te worden gedeeld
* Elementen die vooraf zijn geselecteerd door het creatieve team
* Specifieke asset-indelingen die kunnen worden gebruikt of aangevraagd door marketing, afhankelijk van een specifiek contract of een specifieke overeenkomst (bijvoorbeeld JPG-bestanden die zijn geconverteerd van RAW-bestanden, TIFF-bestanden/afbeeldingen van PSD-originelen)

#### Wanneer updates van elementen worden opgeslagen in DAM {#when-updates-to-assets-are-stored-in-dam}

Normaliter moeten alleen updates van middelen die relevant zijn voor de bredere reeks DAM-gebruikers in DAM worden opgeslagen. Hiermee zorgt u ervoor dat gebruikers (marketing en soortgelijke functies) alleen relevante versies in de tijdlijn van de DAM-middelen zien.

Doorgaans zijn er wijzigingen die betrekking hebben op belangrijke mijlpalen in de levenscyclus van de middelen. Het eerste marketingklare middel of een officiële update op basis van een verzoek/revisie van het creatieve team moet bijvoorbeeld worden opgeslagen en gecontroleerd in DAM.

De update van het creatieve team voor revisie door het marketingteam na een verzoek om wijziging van het bestaande middel in DAM is een voorbeeld van een relevante update. Het zou in DAM voor verdere verwijzing of voor het terugkeren naar de vorige versie moeten worden opgeslagen en worden versioned.

Hieronder volgen voorbeelden van updates die doorgaans niet relevant zijn:

* Vroege versies van elementen die zijn geüpload voordat ze klaar zijn voor marketingcontrole
* Veelvoorkomende creatieve wijzigingen in het bedrijfsmiddel in de aan de gang zijnde fase voordat creatieve en marketingteams besluiten dat het middel klaar is

### Toegang van gebruikers tot DAM {#user-access-to-dam}

AEM Assets ondersteunt twee soorten gebruikers op basis van hun toegang tot de implementatie van AEM Assets. Doorgaans hebben gebruikers binnen het bedrijfsnetwerk (firewall) directe toegang tot DAM. Andere gebruikers buiten het ondernemingsnetwerk zouden geen directe toegang hebben. Het gebruikerstype bepaalt welke integraties vanuit technisch oogpunt kunnen worden gebruikt.

#### Creatieve gebruikers met directe toegang tot DAM {#creative-users-with-direct-access-to-dam}

In het algemeen hebben interne creatieve teams of agentschappen/creatieve professionals die aan het interne netwerk zijn toegewezen, toegang tot het DAM-exemplaar, inclusief AEM-aanmelding. AEM en netwerkinfrastructuur kunnen worden opgezet om directe toegang tot externe partijen - gewoonlijk vertrouwde organisaties zoals agentschappen die voor een cliënt werken - toe te staan om toegang tot AEM over netwerk (b.v., via VPN of IP fluitend) te hebben.

In dergelijke gevallen helpt de Adobe Asset Link- of AEM-bureaubladtoepassing u eenvoudig toegang te krijgen tot definitieve/goedgekeurde middelen en kunt u creatieve middelen opslaan naar DAM.

#### Creatieve gebruikers zonder toegang tot DAM {#creative-users-without-access-to-dam}

Externe agentschappen en freelancers zonder directe toegang tot het DAM-exemplaar hebben mogelijk toegang tot goedgekeurde activa nodig of willen hun nieuwe ontwerpen toevoegen aan het DAM.

Gebruik de volgende strategieën om toegang te verlenen tot definitieve/goedgekeurde middelen:

* Gebruik de bureaubladtoepassing als Asset Link niet werkt.
* Gebruik [AEM Assets Brand Portal](https://helpx.adobe.com/experience-manager/brand-portal/user-guide.html) voor het veilig distribueren van middelen aan externe partners
* Gebruik een aangepaste implementatie van een distributie- en sourcingportal op basis van [Asset Share Commons](https://adobe-marketing-cloud.github.io/asset-share-commons/)
* Het Toegangsbeheer van het gebruik opstelling in AEM en noodzakelijke netwerkinfrastructuur (bijvoorbeeld, VPN en IP flits) om externe partijen toegang tot een specifiek gebied van inhoud in uw DAM te geven. Ze kunnen AEM Web UI gebruiken om middelen op te halen en nieuwe inhoud te uploaden in uw DAM.

#### Werk bezig met middelen van AEM {#work-in-progress-on-assets-from-aem}

Zoals in dit document wordt besproken, wordt aanbevolen belangrijke updates uit te voeren voor elementen, ook wel &#39;werk in uitvoering&#39; genoemd, zonder dat alle bewerkingen die in het lokale bestand zijn opgeslagen, als wijzigingen naar AEM worden geüpload. Dit versnelt het werk van een Desktopgebruiker, beperkt gebruikte netwerkbandbreedte, en houdt de activa chronologie schoon en concentreert zich op gecontroleerde, belangrijke updates.

Adobe Asset Link biedt een goede ondersteuning voor dit gebruiksgeval:

* Wanneer gebruikers in Photoshop, InDesign of Illustrator van plan zijn een bestand te bewerken, voeren zij een uitcheckbewerking uit op het desbetreffende element
* Het middel wordt op de achtergrond gedownload, in gebruikers geplaatst met een Creative Cloud-account dat door de Creative Cloud-bureaubladtoepassing op de schijf is gesynchroniseerd en de uitcheckmarkering wordt in AEM op het middel in- en uitgeschakeld om bewerkingsconflicten te minimaliseren
* Vanaf dat punt werkt de gebruiker in een bestand dat lokaal is opgeslagen op de gesynchroniseerde locatie. De gebruiker kan doorgaan met het werken en opslaan van noodzakelijke wijzigingen met elke vereiste frequentie
* Aangezien het middel zich in de Creative Cloud-account bevindt, is het ook beschikbaar op andere apparaten die de gebruiker mogelijk heeft (kunnen bijvoorbeeld worden geopend of bewerkt in een speciale Creative Cloud mobile-app) en kan het voor samenwerkingsdoeleinden worden gedeeld met andere Creative Cloud-gebruikers.
* Wanneer de creatieve gebruiker klaar is met de wijzigingen, kan hij of zij een incheckbewerking op dat bestand uitvoeren in zijn of haar Creative Cloud-toepassing, met een optionele opmerking. Het overeenkomstige element in AEM wordt versioned en bijgewerkt aan met het nieuwe binaire getal. AEM-gebruikers zoals Marketers of LOB-gebruikers hebben via de tijdlijngebruikersinterface van AEM-middelen toegang tot belangrijke wijzigingen in bedrijfsmiddelen of mijlpalen.

De AEM-bureaubladtoepassing biedt een netwerkshare voor elementen die zijn geopend in de native app. Standaard worden alle lokaal uitgevoerde wijzigingen na een korte tijd automatisch geüpload naar AEM. Met zo&#39;n configuratie, zouden de frequente besparingen tijdens de werk-in-lopende fase allen in AEM worden geupload en versioned, die tot veel netwerkverkeer en potentiële scalability uitdagingen leiden - om onnodige versies in AEM te noemen.

Hier kunt u het beste een optie in de AEM-bureaubladtoepassing gebruiken om geautomatiseerde updates uit te schakelen en wijzigingen in elementen handmatig te uploaden naar AEM. Hierbij wordt gebruikgemaakt van de actie voor uploadwijzigingen in de Asset Status UI van de app.

#### Bulkupload naar DAM {#bulk-upload-to-dam}

In sommige gevallen moet u wellicht een groter aantal bestanden tegelijkertijd uploaden naar DAM, bijvoorbeeld:

* Resultaten van foto&#39;s of grotere projecten uploaden
* Door creatieve bureaus geleverde activa uploaden
* Geselecteerde elementen uploaden vanaf een grotere set als de selectie buiten DAM is uitgevoerd

De beschrijving verwijst naar het operationeel uploaden van bestanden (bijvoorbeeld elke week of met elke foto), als een normaal onderdeel van de workflow van de desktopgebruiker. De migratie van grote activa wordt hier niet behandeld.

U kunt de volgende uploadmogelijkheden gebruiken:

* Als u grote/hiërarchische mappen bulksgewijs wilt uploaden, gebruikt u de AEM-bureaubladtoepassing die functionaliteit voor het uploaden van [mappen](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app.html#bulkupload) biedt. U kunt ook hiërarchische mapstructuren uploaden. Elementen worden op de achtergrond geüpload en zijn daarom niet gekoppeld aan een webbrowsersessie
* Als u enkele bestanden uit één map wilt uploaden, sleept u de bestanden rechtstreeks naar de webinterface of gebruikt u de optie Maken in de AEM Assets-webinterface.
* Afhankelijk van uw bedrijfsvereisten kunt u ook aangepaste uploader gebruiken.

#### Digitale middelen rechtstreeks vanaf het bureaublad beheren {#managing-digital-assets-directly-from-desktop}

Als u Delen van netwerkbestanden gebruikt om digitale elementen te beheren, kan het gebruik van de netwerkshare die is toegewezen door de AEM-bureaubladtoepassing worden beschouwd als een handige vervanging. Bij de overgang van netwerkbestanden biedt de AEM-webinterface een uitgebreide reeks mogelijkheden voor beheer van digitale middelen die veel verder gaan dan wat mogelijk is op een gedeeld netwerk (zoeken, verzamelingen, metagegevens, samenwerking, voorvertoningen, enzovoort) en de AEM-bureaubladtoepassing biedt een handige koppeling om de DAM-opslagplaats aan de serverzijde te verbinden met het werk op een desktopcomputer.

Gebruik de AEM-bureaubladtoepassing niet om elementen rechtstreeks in het netwerkaandeel van AEM-middelen te beheren. Vermijd bijvoorbeeld het gebruik van de AEM-bureaubladtoepassing voor het verplaatsen/kopiëren van meerdere bestanden. Gebruik in plaats daarvan de interface van AEM Assets-webinterface om mappen van Finder/Explorer naar het gedeelde netwerk te slepen of gebruik de functie Map uploaden naar AEM Assets.

#### Migratie van middelen {#asset-migration}

Raadpleeg de [migratiehandleiding](/help/assets/assets-migration-guide.md)voor informatie over het plannen en uitvoeren van migratie van middelen van een bestaand systeem naar een nieuw systeem of het migreren van grote hoeveelheden middelen die op servers zijn opgeslagen. AEM-bureaubladtoepassingen en integratie van AEM naar Creative Cloud ondersteunen dergelijke migraties niet. Vanwege de grote hoeveelheden in te nemen elementen en de extra vereisten met betrekking tot het in kaart brengen van metagegevens, transformatie en opname, moeten migraties met verschillende gereedschappen en benaderingen worden afgehandeld.

>[!MORELIKETHIS]
>
>* [Adobe-elementkoppeling](https://helpx.adobe.com/in/enterprise/using/adobe-asset-link.html)
>* [Aanbevolen werkwijzen voor AEM-bureaubladtoepassingen](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/archive/best-practices-for-v1.html)
>* [AEM Brand Portal](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/introduction/brand-portal.html)
>* [AEM en de integratie van Adobe Stock](aem-assets-adobe-stock.md)

