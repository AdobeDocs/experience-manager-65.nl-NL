---
title: Apps maken en bewerken met de toepassingsconsole
description: Volg deze pagina voor meer informatie over het maken en bewerken van apps met de toepassingsconsole.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-adobe-phonegap-enterprise
exl-id: 49e0b3f6-7ac7-4417-9c31-cc3d3c2305f3
solution: Experience Manager
feature: Mobile
role: Admin
source-git-commit: 2dae56dc9ec66f1bf36bbb24d6b0315a5f5040bb
workflow-type: tm+mt
source-wordcount: '2654'
ht-degree: 0%

---

# Apps maken en bewerken met de toepassingsconsole{#creating-and-editing-apps-using-the-apps-console}

{{ue-over-mobile}}

In het AEM ontwikkelingsproces voor mobiele toepassingen wordt erkend dat gebruikers met verschillende expertise bijdragen aan de ontwikkeling van mobiele toepassingen. De volgende procesafbeelding illustreert de algemene volgorde waarin inhoudsauteurs en toepassingsontwikkelaars taken uitvoeren.

![ chlimage_1-10 ](assets/chlimage_1-10.gif)

Op deze pagina wordt informatie weergegeven over het uitvoeren van de markeringstaken. Voor informatie over de taken van de Ontwikkelaar, zie de Toepassingen van PhoneGap van de Bouwstijl.

## De structuur van mobiele toepassingen {#the-structure-of-mobile-applications}

AEM Mobile biedt de blauwdruk van de PhoneGap App voor het maken van mobiele toepassingen. De blauwdruk bepaalt de structuur van de toepassingen die u creeert. Toepassingen bestaan uit de volgende onderdelen:

* De basispagina.
* De taalvariaties van de toepassing.
* De homepage van de taalvariatie.

### De hoofdmap van een PhoneGap-app {#the-root-of-a-phonegap-app}

De hoofdpagina van de mobiele toepassingen die u in AEM maakt, wordt weergegeven in de toepassingsconsole.

De basispagina wordt opgeslagen onder de eigenschap Doelpad van de toepassing die is opgegeven bij het maken van de toepassing (het standaardpad is /content/phonegap/apps). De paginanaam is het bezit van de Naam van de toepassing. De standaard-URL van de hoofdpagina van de site met de naam `myphonegapapp` is bijvoorbeeld `http://localhost:4502/content/phonegap/apps/myphonegapapp.html` .

![ chlimage_1-146 ](assets/chlimage_1-146.png)

### De taalvariatie van een PhoneGap-app {#the-language-variation-of-a-phonegap-app}

De eerste onderliggende pagina&#39;s van de basispagina zijn de taalvariaties van de toepassing. De naam van elke pagina is de taal waarvoor de toepassing wordt gemaakt. Engels is bijvoorbeeld de naam van de Engelse variatie van de toepassing.

**Nota:** de standaardblauwdruk PhoneGap leidt slechts tot een Engelse toepassing. Uw ontwikkelaar kan de blauwdruk aanpassen zodat deze meer taalvariaties kan maken.

![ chlimage_1-147 ](assets/chlimage_1-147.png)

De taalpagina heeft twee doelen:

* De pagina-inhoud is de spash-pagina voor de taalvariatie van de toepassing.
* De pagina-eigenschappen beheren verschillende ontwerpaspecten van de toepassing, zoals de URL die moet worden gebruikt voor het aanvragen van updates van inhoud, en informatie over het maken van verbinding met de cloud en de integratie met Adobe Analytics Services.

![ chlimage_1-148 ](assets/chlimage_1-148.png)

### De startpagina {#the-home-page}

De pagina Home of index.html van een taalvariatie van een toepassing wordt weergegeven wanneer de toepassing wordt geopend. De homepage voorziet gebruikers van een menu van verbindingen aan diverse pagina&#39;s in de toepassing. Met het alineasysteem kunt u componenten aan de pagina toevoegen om inhoud te maken.

## Een mobiele toepassing maken {#creating-a-mobile-application}

Mobiele toepassingen zijn gebaseerd op een blauwdruk die een paginastructuur en eigenschappen definieert. U kunt de volgende toepassingseigenschappen configureren:

* **Titel:** de toepassingstitel.
* **Weg van de Bestemming:** de plaats in de bewaarplaats waar de toepassing wordt opgeslagen. Laat de standaardinstelling ongewijzigd om een pad te maken op basis van de toepassingsnaam.

* **Naam:** De standaardwaarde is de waarde van het bezit van de Titel met verwijderde ruimtekarakters. De naam wordt gebruikt binnen CQ om naar de toepassing te verwijzen, bijvoorbeeld voor de opslagplaats knoop die de toepassing vertegenwoordigt.
* **Beschrijving:** een beschrijving van de toepassing.
* **Server URL:** URL die over-de-Air (OTA) inhoudsupdates aan de toepassing verstrekt. De standaardwaarde is de URL van de publicatieserver van de instantie die wordt gebruikt om een toepassing te maken (deze is afkomstig van de externalizer-service). Opmerking: dit moet een publicatieserverinstantie zijn in plaats van een auteur, die verificatie vereist.

U kunt ook een afbeeldingsbestand opgeven dat u als miniatuur van de toepassing wilt gebruiken, de configuratie PhoneGap Build selecteren die u wilt gebruiken en de analytische configuratie voor de mobiele app selecteren. Deze afbeelding wordt alleen gebruikt als miniatuur voor uw mobiele toepassing in de console voor mobiele apps in Experience Manager.

Er zijn extra (en optionele) tabbladen voor het samenstellen van cloudservice en het integreren van de Adobe Mobile Services SDK-plug-in in uw app.

* Samenstellen: klik hier op Configuraties beheren en stel de service voor het samenstellen van build.phonegap.com in. Vervolgens kunt u in de vervolgkeuzelijst de nieuwe PhoneGap-service voor de build-cloud selecteren.
* Analytics: Klik beheert configuraties en opstelling uw [ Adobe Mobiele Diensten de clouddienst van SDK ](https://experienceleague.adobe.com/docs/mobile-services/using/home.html?lang=nl-NL). Vervolgens kunt u in het keuzemenu de nieuwe mobiele service selecteren die u wilt integreren in uw mobiele app.

>[!NOTE]
>
>Ontwikkelaars kunnen de AEM PhoneGap Starter Kit gebruiken om apps te maken en deze toe te voegen aan de console.

In de volgende procedure wordt de Touch-gebruikersinterface gebruikt om een mobiele toepassing te maken.

1. Klik op Apps op de rail.
1. Klik het Create pictogram.

   ![ het Create pictogram dat door een plusteken binnen een vierkant wordt vermeld.](do-not-localize/chlimage_1-7.png)

1. (Optioneel) Geef op het tabblad Geavanceerd een beschrijving voor de toepassing op en wijzig zo nodig de URL van de server.
1. (Optioneel) Als u PhoneGap Build gebruikt om de toepassing te compileren, selecteert u op het tabblad Build de configuratie die u wilt gebruiken.

   Klik op Configuraties beheren om een PhoneGap-build-configuratie te maken.

1. (Optioneel) Als u SiteCatalyst gebruikt om de toepassingsactiviteit te volgen, selecteert u op het tabblad Analyse de configuratie die u wilt gebruiken.

   Klik op Configuraties beheren als u een mobiele toepassingsconfiguratie wilt maken.

1. (Optioneel) Als u een toepassingspictogram wilt maken, klikt u op de knop Bladeren, selecteert u het afbeeldingsbestand in uw bestandssysteem en klikt u op Openen.
1. Klik op Maken.

### De eigenschappen van een mobiele toepassing wijzigen {#changing-the-properties-of-a-mobile-application}

Nadat u een mobiele toepassing hebt gemaakt, kunt u de eigenschappen wijzigen.

#### De titel, beschrijving en het pictogram wijzigen {#change-the-title-description-and-icon}

1. Klik op Apps op de rail.
1. Selecteer de toepassing die u wilt configureren en klik op het pictogram Pagina-eigenschappen weergeven.

   ![ het pictogram van de Eigenschappen van de Pagina van de Mening die door de brief I binnen een cirkel wordt vermeld.](do-not-localize/chlimage_1-8.png)

1. Klik op het pictogram Bewerken om eigenschapswaarden te wijzigen.

   ![ het Edit pictogram dat door een potlood wordt vermeld.](do-not-localize/chlimage_1-9.png)

1. Configureer de eigenschappen Standaard en Geavanceerd en klik op het pictogram Gereed.

   ![ het Gereed pictogram dat door een symbool van het vinkje wordt vermeld.](do-not-localize/chlimage_1-10.png)

#### Een taalvariatie van de toepassing configureren {#configure-a-language-variation-of-the-application}

1. Klik op Apps op de rail.
1. Klik om de mobiele toepassing die u wilt bewerken, in te roepen in de Admin Console apps. Selecteer de taalversie van de toepassing die u wilt configureren en klik op het pictogram Toepassingseigenschappen weergeven.

   ![ het pictogram van de Eigenschappen van de Toepassing van de Mening die door de brief I binnen een cirkel wordt vermeld.](do-not-localize/chlimage_1-11.png)

1. Klik op het pictogram Bewerken om eigenschapswaarden te wijzigen.

   ![ het Edit pictogram dat door een potlood wordt vermeld.](do-not-localize/chlimage_1-12.png)

1. Configureer de eigenschappen op de tabbladen Standaard, Geavanceerd, Samenstellen en Analyse en klik vervolgens op het pictogram Gereed.

   ![ het Gereed pictogram dat door een symbool van het vinkje wordt vermeld.](do-not-localize/chlimage_1-13.png)

### De inhoud van een mobiele toepassing ontwerpen {#authoring-the-content-of-a-mobile-application}

Nadat u de mobiele toepassing hebt gemaakt, voegt u inhoud toe die wordt gebruikt als de interface van de toepassing.

1. Klik op Apps op de rail.
1. Klik op de toepassing en vervolgens op Engels.
1. Bewerk de startpagina of voeg naar wens onderliggende pagina&#39;s toe.

### Inhoud verplaatsen naar mobiele toepassingen {#moving-content-to-mobile-applications}

De cache voor het synchroniseren van inhoud op de AEM-publicatie-instantie wordt gebruikt als opslagplaats voor inhoud voor mobiele toepassingen:

* Inhoud in de cache van Content Sync wordt in de toepassing opgenomen wanneer ontwikkelaars de toepassing compileren.
* Inhoud in de cache is beschikbaar voor geïnstalleerde mobiele toepassingen voor het bijwerken van de inhoud van de toepassing.

Mobiele toepassingen hebben een opdracht Updates waarmee bijgewerkte toepassingsinhoud wordt gedownload en geïnstalleerd. Wanneer een toepassingsinstantie een updateverzoek verzendt, bepaalt Content Sync welke inhoud is gewijzigd sinds de laatste keer dat de toepassing werd bijgewerkt of geïnstalleerd, en verstrekt de nieuwe inhoud.

![ chlimage_1-149 ](assets/chlimage_1-149.png)

Als u bijgewerkte inhoud beschikbaar wilt maken voor toepassingen, werkt u de cache van Content Sync bij. De eerste keer dat u de cache bijwerkt, wordt alle gepubliceerde inhoud toegevoegd. Bij volgende updates wordt alleen de gepubliceerde inhoud toegevoegd die is gewijzigd sinds de vorige update.

Met Content Sync wordt ook bijgehouden wanneer de updates plaatsvinden. Met deze informatie kan Content Sync bepalen welke cache-update naar een mobiele toepassing moet worden verzonden.

Voer de volgende procedure uit op de instantie waar u het cachegeheugen wilt bijwerken. Als uw toepassing bijvoorbeeld updates vraagt van de instantie publish, voert u de procedure uit op de instantie publish.

1. Klik op Apps (Apps) in de track en klik vervolgens op uw toepassing.
1. Selecteer de welkomstpagina en klik op het pictogram Cache bijwerken.

   ![ het pictogram van het Geheime voorgeheugen van de Update dat door een gestreept barrell met een recycle symbool over het wordt vermeld.](do-not-localize/chlimage_1-14.png)

### App-sjablonen gebruiken {#using-app-templates}

Deze functie is beschikbaar in Apps 6.1 Feature Pack 2 en biedt een eenvoudige manier om bestaande toepassingssjablonen te gebruiken voor het maken van nieuwe apps binnen AEM.

Wat is een toepassingssjabloon? Beschouw het als een verzameling paginasjablonen en componenten die een basislijn of basis van een app vormen.
Wanneer u een app maakt op basis van de sjabloon van een andere app, krijgt u een app met een beginpunt dat representatief is voor de app waarin deze is gemaakt.

U moet een bestaande sjabloon voor mobiele apps (of een app met een toepassingssjabloon) hebben om deze functie te kunnen gebruiken.

Het meest recente AEM Apps 6.1 voorbeeldenpakket bevat een bijgewerkte versie van de Geometrixx-app met een toepassingssjabloon. U kunt ook de StarterKit installeren die ook een sjabloon biedt.

Stappen voor het maken van een app op basis van een toepassingssjabloon:

1. Zorg ervoor dat u het nieuwste AEM Apps 6.1 functiepakket en referentiemonsteringspakketten hebt geïnstalleerd
1. Klik Apps van de linkerspoorstaaf.

![ chlimage_1-1 ](assets/chlimage_1-1.jpeg)

1. Klik op de knop + Maken bovenaan en selecteer App maken.
1. Als u de lijst met App Templates hebt ontvangen, selecteert u een van deze sjablonen:

![ chlimage_1-2 ](assets/chlimage_1-2.jpeg)

1. Klik op Volgende.
1. Geef een app-id en -titel op, maar u wilt mogelijk ook een naam en een beschrijving opnemen.

   1. U kunt ook een PNG-bestand (ondersteunde PhoneGap-pictogramindeling) opgeven als pictogram door AEM elementen te bladeren.
   1. U kunt al deze velden bewerken nadat de app is gemaakt in de tegel App beheren. Met uitzondering van de toepassings-id kunt u deze niet wijzigen nadat de toepassings-id is ingesteld.

![ chlimage_1-150 ](assets/chlimage_1-150.png)

1. Klik op de knop Maken. Er worden twee opties weergegeven: Gereed (ga terug naar de catalogusweergave van apps) of Toepassen beheren (hiermee wordt het dashboard van de app geopend).
1. Nadat de app is gemaakt, wordt de nieuwe app weergegeven in de App-catalogus:

![ chlimage_1-3 ](assets/chlimage_1-3.jpeg)

1. Klik op de app om deze te openen. U hebt een nieuwe app gemaakt op basis van de sjabloon van een bestaande app.

>[!NOTE]
>
>Als u het Geometrixx Outdoors referentie-app-pakket van AEM verwijdert en een app hebt gemaakt op basis van de sjabloon, werkt die app niet meer. De app Geometrixx Outdoors kan worden verwijderd, maar de toepassingssjabloon moet blijven staan als deze wordt gebruikt door andere mobiele toepassingen.

## De Sample Geometrixx Outdoors App verkennen {#exploring-the-sample-geometrixx-outdoors-app}

Geometrixx Outdoors App is een voorbeeld van een PhoneGap-toepassing die de functies van de standaardblauwdruk van de PhoneGap-toepassing en de mobiele voorbeeldcomponenten demonstreert.

Als u de toepassing wilt openen, klikt u in de track op Mobiele toepassingen en selecteert u vervolgens Geometrixx Outdoors App.

### Functies voor algemene pagina&#39;s - mobiele Geometrixx-app {#common-page-features-geometrixx-mobile-app}

Elke pagina van de mobiele app bevat de volgende functies:

* Een knop Terug om terug te keren naar de bovenliggende pagina. De knop Terug wordt niet weergegeven op de startpagina.
* Een uitbreidbare rail met een menu van opdrachten en koppelingen:

   * Open de pagina Locaties.
   * Open de winkelwagen.
   * Log in.
   * Werk de toepassing bij.

* Het alineasysteem voor het toevoegen van componenten en het maken van inhoud.

### De startpagina - de mobiele toepassing Geometrixx {#the-home-page-geometrixx-mobile-app}

De inhoud van de startpagina bestaat uit de volgende navigatiegereedschappen:

* Een component Menu List die koppelingen biedt naar de onderliggende pagina&#39;s Gear, Reviews, News en About US.
* Een Veeggebaar waarmee de onderliggende pagina&#39;s worden weergegeven.

### De tandwielpagina - de mobiele toepassing van Geometrixx {#the-gear-page-geometrixx-mobile-app}

De pagina Gear biedt gebruikers toegang tot productpagina&#39;s. Een component van de menulijst verleent toegang tot de kindpagina&#39;s van de pagina van het Gear. De onderliggende pagina&#39;s zijn productcategorieën die de website bevat.

* Seizoen
* Deksel
* Geslacht
* Activiteit

Elke categoriepagina gebruikt dezelfde inhoudsstructuur als de pagina Verwerk. De carrousel biedt toegang tot onderliggende pagina&#39;s die subcategorieën van producten zijn. De subcategoriepagina&#39;s bevatten productaanbiedingen met koppelingen naar productpagina&#39;s.

### De productpagina - de mobiele toepassing van Geometrixx {#the-products-page-geometrixx-mobile-app}

De pagina Producten en zijn hiërarchie van kindpagina&#39;s voeren een classificatiesysteem voor productpagina&#39;s uit. De laagste pagina&#39;s in elke vertakking van de hiërarchie zijn een productpagina die een ng component van het Product bevat.

De pagina Producten is niet beschikbaar voor gebruikers van de toepassing. De pagina Gear biedt toegang tot elke productpagina.

### De pagina Revisies - Geometrixx Mobile-app {#the-reviews-page-geometrixx-mobile-app}

Bevat een knop Terug. Met het alineasysteem kunt u componenten toevoegen.

Als u de toepassing gebruikt, is de pagina Revisies beschikbaar via de carrousel op de pagina Engels.

### De nieuwspagina - Geometrixx Mobile-app {#the-news-page-geometrixx-mobile-app}

Bevat een knop Terug. Met het alineasysteem kunt u componenten toevoegen.

Wanneer u de toepassing gebruikt, is de pagina News beschikbaar via de carrousel op de Engelse pagina.

### De pagina Over ons - Geometrixx Mobile-toepassing {#the-about-us-page-geometrixx-mobile-app}

De pagina Info over ons bevat verschillende componenten Twee kolomrijen. Elke kolom bevat een component Image of Text. De componenten zijn bewerkbaar en het alineasysteem biedt u de mogelijkheid componenten toe te voegen.

Wanneer u de toepassing gebruikt, is de pagina Over gebruikers beschikbaar via de carrousel op de Engelse pagina.

### De locatiepagina - Geometrixx Mobile-toepassing {#the-locations-page-geometrixx-mobile-app}

De pagina Locations bevat een component Locations.

Wanneer u de toepassing gebruikt, is de pagina Locaties beschikbaar in de menulijst op de pagina Engels.

## Voorbeeld van mobiele componenten {#sample-mobile-components}

Verschillende componenten zijn direct beschikbaar in Sidekick wanneer u pagina&#39;s van een mobiele toepassing ontwerpt. De componenten behoren tot de PhoneGap-componentgroep.

### Swipe Carousel {#swipe-carousel}

De component VeegCarrousel is een hulpmiddel om sitepagina&#39;s weer te geven en te navigeren. De component bevat een carrousel die de afbeeldingen doorloopt voor de pagina&#39;s boven een lijst met paginakoppelingen. Bewerk de component om de pagina&#39;s op te geven die u wilt weergeven en het gedrag van de carrousel.

Afbeeldingen worden in de carrousel weergegeven voor pagina&#39;s die op een specifieke manier aan een afbeelding zijn gekoppeld. Wanneer pagina&#39;s niet aan afbeeldingen zijn gekoppeld, wordt alleen de lijst met koppelingen weergegeven.

![ chlimage_1-151 ](assets/chlimage_1-151.png)

**Carousel eigenschappen tabel**

Configureer het gedrag van de carrousel:

* Afspeelsnelheid: de tijd in milliseconden dat elke afbeelding wordt weergegeven voordat de volgende afbeelding wordt weergegeven.
* Overgangstijd: de duur in milliseconden van de animatie voor afbeeldingsovergangen.
* Besturingsstijl: het type besturingselement dat wordt gebruikt voor het verplaatsen tussen afbeeldingen.

**de eigenschappen tabel van de Lijst**

Geef op hoe de paginalijst wordt gegenereerd:

* Lijst samenstellen met: de methode die moet worden gebruikt voor het opgeven van de pagina&#39;s die moeten worden opgenomen in de carrousel. Zie De paginalijst samenstellen.
* Volgorde door: selecteer een pagina-eigenschap die u wilt gebruiken voor het sorteren van de paginalijst. Selecteer bijvoorbeeld jcr:title om pagina&#39;s alfabetisch op titel te sorteren.
* Limiet: het maximumaantal pagina&#39;s dat moet worden opgenomen. Deze eigenschap is geschikt voor op zoeken gebaseerde methoden om de paginalijst samen te stellen.

#### De paginalijst samenstellen {#building-the-page-list}

De component van Carrousel van de Veeggebaar verstrekt de volgende waarden voor de Bouwstijl Lijst Gebruikend bezit. Het dialoogvenster Bewerken verandert op basis van de waarde die u selecteert:

**de Pagina&#39;s van het Kind**

De component bevat een lijst met alle onderliggende pagina&#39;s van een specifieke pagina. Nadat u deze waarde hebt geselecteerd, selecteert u de pagina op het tabblad Onderliggende pagina&#39;s of geeft u geen waarde op om de onderliggende pagina van de huidige pagina weer te geven.

**Vaste Lijst**

Geef een lijst op met pagina&#39;s van include-bestanden. Nadat u deze waarde hebt geselecteerd, configureert u de lijst op het tabblad Vaste lijst die wordt weergegeven wanneer u Vaste lijst selecteert:

* Als u een pagina wilt toevoegen, klikt u op Item toevoegen en bladert u naar de pagina.
* Gebruik de pictogrammen Pijl-omhoog en Pijl-omlaag om de pagina binnen de lijst te verplaatsen.
* Klik op de knop Verwijderen om een pagina uit de lijst te verwijderen.

De eigenschap Volgorde op heeft geen invloed op de volgorde van vaste lijsten.

**Zoeken**

Vul de lijst met de resultaten van een trefwoordzoekopdracht. De zoekopdracht wordt uitgevoerd in de onderliggende pagina&#39;s van een pagina die u opgeeft:

1. Als u de hoofdpagina van de zoekopdracht wilt opgeven, gebruikt u de eigenschap Beginnen in om het paginapad te selecteren. Geef geen pad op om onder de huidige pagina te zoeken.
1. Voer de zoektrefwoorden in de eigenschap Zoekquery in.

**Geavanceerd Onderzoek**

Vul de lijst gebruikend vraag van de a [ Querybuilder ](/help/sites-developing/querybuilder-api.md).

### Afbeelding {#image}

Voeg een afbeelding toe aan uw toepassingsinhoud.

### Tekst {#text}

Voeg rijke tekst toe aan uw toepassingsinhoud.

### Locaties opslaan {#store-locations}

De component Locaties van de Opslag voorziet gebruikers van hulpmiddelen om bedrijfsafzet te vinden:

* Zoeken
* Een lijst met locaties die dicht bij of ver van de GPS-coördinaten van het apparaat liggen.

De component vereist dat de gegevensopslagruimte locatie locatie-informatie voor elke opslagruimte bevat. De plaatsen van de steekproef zijn geïnstalleerd bij de /etc/commerce/locations/adobe knoop. ![ chlimage_1-152 ](assets/chlimage_1-152.png)

### Twee kolommen, rij {#two-column-row}

Hiermee kunt u componenten naast elkaar aan een pagina toevoegen.

![ chlimage_1-153 ](assets/chlimage_1-153.png)
