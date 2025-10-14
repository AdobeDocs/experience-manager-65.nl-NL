---
title: Clientcontext
description: Leer hoe u de clientcontext gebruikt om informatie over de huidige pagina en bezoeker in Adobe Experience Manager weer te geven.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
docset: aem65
exl-id: 69c66c82-fbd6-406e-aefd-b85480a62109
solution: Experience Manager, Experience Manager Sites
feature: Administering,Personalization
role: Admin
source-git-commit: 305227eff3c0d6414a5ae74bcf3a74309dccdd13
workflow-type: tm+mt
source-wordcount: '1961'
ht-degree: 0%

---


# Clientcontext{#client-context}

>[!NOTE]
>
>De Context van de cliënt is vervangen door ContextHub. Voor meer details, zie de verwante [&#x200B; configuratie &#x200B;](/help/sites-developing/ch-configuring.md) en [&#x200B; ontwikkelaar &#x200B;](/help/sites-developing/contexthub.md) documentatie.

De context van de Cliënt is een mechanisme dat u van bepaalde informatie over de huidige pagina en de bezoeker voorziet. Het kan worden geopend gebruikend **Ctrl-Alt-c** (vensters) of **controle-optie-c** (Mac):

![&#x200B; een steekproef van het venster van de Context van de Cliënt &#x200B;](assets/clientcontext_alisonparker.png)

In zowel de publicatie- als de auteursomgeving wordt informatie weergegeven over:

* De bezoeker; afhankelijk van uw instantie wordt bepaalde informatie gevraagd, of afgeleid.
* Paginalabels en het aantal keren dat deze labels door de huidige bezoeker zijn geopend (dit wordt weergegeven wanneer u de muis over een specifieke tag beweegt).
* Pagina-informatie.
* Informatie over het technische milieu; zoals het IP adres, browser en het schermresolutie.
* Om het even welke segmenten die momenteel worden opgelost.

Met de pictogrammen (alleen beschikbaar in de auteursomgeving) kunt u de details van de clientcontext configureren:

![&#x200B; Edit, Laad, en de pictogrammen van het Terugstellen van het venster van de Context van de Cliënt &#x200B;](do-not-localize/clientcontext_icons.png)

* **geeft** uit
Een nieuwe pagina opent, latend u [&#x200B; uitgeeft, toevoegt, of verwijdert een profielbezit &#x200B;](#editingprofiledetails).

* **Lading**
U kunt [&#x200B; van een lijst van profielen selecteren en het profiel laden &#x200B;](#loading-a-new-user-profile) u wilt testen.

* **Terugstellen**
U kunt [&#x200B; het profiel &#x200B;](#resetting-the-profile-to-the-current-user) aan dat van de huidige gebruiker terugstellen.

## Beschikbare clientcontextcomponenten {#available-client-context-components}

De context van de Cliënt kan de volgende eigenschappen ([&#x200B; afhankelijk van tonen wat gebruikend uitgeeft &#x200B;](#adding-a-property-component) is geselecteerd):

**toont de Informatie van de Opslag van 0&rbrace; de volgende cliënt-zijinformatie:**

* het **IP adres**
* **sleutelwoorden** voor verwijzing van de onderzoeksmotor worden gebruikt
* **browser** die wordt gebruikt
* **OS** (werkend systeem) die worden gebruikt
* het scherm **resolutie**
* de **muisX** positie
* de **muisY** positie

**de Stream van de Activiteit** dit verstrekt informatie over de sociale activiteit van de gebruiker op diverse platforms; bijvoorbeeld, de AEM forums, blogs, classificaties, etc.

**Campagne** staat auteurs toe om een specifieke ervaring voor een campagne te simuleren. Deze component overschrijft de normale campagneresolutie en ervaringsselectie om het testen van verschillende permutaties mogelijk te maken.

De oplossing van de campagne is doorgaans gebaseerd op de prioritaire eigenschap van de campagne. De ervaring wordt gewoonlijk geselecteerd gebaseerd op segmentatie.

**toont het Kart van 0&rbrace; winkelwagentinformatie met inbegrip van productingangen (titel, hoeveelheid, priceFormatted, etc.), opgeloste promoties (titel, bericht, etc.) en vouchers (code, beschrijving, etc.).**

De opslag van de wortelzitting brengt de server ook op de hoogte van opgeloste bevorderingsveranderingen (die op segmenteringsveranderingen worden gebaseerd) gebruikend ClientContextCartServlet.

**Algemene Opslag** is een generische component die de inhoud van een opslag toont. Het is een lagere versie van de Algemene component van de Eigenschappen van de Opslag.

De Generic Store moet met een renderer worden gevormd JS die de gegevens op een douanemethode zal tonen.

**Algemene Eigenschappen van de Opslag** is een generische component die de inhoud van een opslag toont. Het is een versie op hoger niveau van de Algemene component van de Opslag.

De component Algemene opslageigenschappen bevat een standaardrenderer met de geconfigureerde eigenschappen (samen met een miniatuur).

**Geolocation** toont de breedte en de lengte van de cliënt. De HTML5-geolocatie-API wordt gebruikt om in de browser te zoeken naar de huidige locatie. Dit leidt ertoe dat een pop-up aan de bezoeker wordt getoond, waar browser hen vraagt of komen zij overeen om hun plaats te delen.

Wanneer de component in de Context Cloud wordt weergegeven, gebruikt de component een Google API om een kaart als miniatuur weer te geven. De component is onderworpen aan de Google API [&#x200B; gebruiksgrenzen &#x200B;](https://developers.google.com/maps/documentation/staticmaps/intro#Limits).

>[!NOTE]
>
>In AEM 6.1 biedt het Geolocation Store niet langer de functie voor omgekeerde geocoding. Daarom wint de opslag Geolocation geen details meer over de huidige plaats, zoals de plaatsnaam of landcode terug. Segmenten die deze opslaggegevens gebruiken, werken niet correct. De Geolocation Store bevat alleen de breedte en lengte van een locatie.

**opslag JSONP** een component die inhoud toont die van uw installatie afhankelijk is.

De norm JSONP is een aanvulling aan JSON die de omzeiling van het zelfde oorsprongbeleid toestaat (die het voor een Web app onmogelijk maakt om met servers te communiceren die op een ander domein zijn). Het bestaat uit het verpakken van het JSON-object in een functieaanroep om het te kunnen laden als een `<script>` van het andere domein (een toegestane uitzondering op hetzelfde oorsprongbeleid).

De opslag JSONP is als een andere opslag, maar het laadt informatie die uit een ander domein zonder de behoefte komt om een volmacht voor die informatie over het huidige domein te hebben. Zie het voorbeeld in [&#x200B; Opstellend Gegevens in de Context van de Cliënt via JSONP &#x200B;](/help/sites-administering/client-context.md#storing-data-in-client-context-via-jsonp).

>[!NOTE]
>
>De opslag JSONP bewaart niet de informatie in het koekje, maar wint die gegevens over elke paginading terug.

**Gegevens van het Profiel** toont informatie die in het gebruikersprofiel wordt verzameld. Bijvoorbeeld geslacht, leeftijd, e-mailadres.

**Resolved segmenten** toont welke segmenten momenteel oplossen (vaak afhankelijk van andere informatie die in de cliëntcontext wordt getoond). Dit is van belang wanneer u een campagne configureert.

Hiermee wordt bijvoorbeeld aangegeven of de muis zich momenteel op het linker- of rechtergedeelte van het venster bevindt. Dit segment wordt vooral gebruikt voor het testen, omdat wijzigingen direct zichtbaar zijn.

**Sociale Grafiek** toont de sociale grafiek van de vrienden en de volgers van de gebruiker.

>[!NOTE]
>
>Dit is momenteel een demo-functie die afhankelijk is van vooraf geconfigureerde gegevensset op de profielknooppunten van onze demonstratiegebruikers. Zie bijvoorbeeld:
>
>`/home/users/geometrixx/aparker@geometrixx.info/profile` =>, eigenschap vrienden

**de Wolk van de Markering** toont markeringen die op de huidige pagina en die worden verzameld terwijl het surfen van de plaats. Als u de muis over een tag beweegt, wordt het aantal keren weergegeven dat de huidige gebruiker pagina&#39;s met die specifieke tag heeft geopend.

>[!NOTE]
>
>Labels die zijn ingesteld op DAM-elementen die worden weergegeven op de bezochte pagina&#39;s, worden niet meegeteld.

**Opslag van Technologieën** Deze component is afhankelijk van uw installatie.

**ViewedProducts** houdt spoor van producten de verkoopster heeft bekeken. Kan worden aangevraagd voor het meest recent bekeken product, of het meest recent bekeken product dat nog niet in de kar zit.

Deze zittingsopslag heeft geen standaardcomponent van de cliëntcontext.

Voor extra informatie, zie [&#x200B; Context van de Cliënt in Detail &#x200B;](/help/sites-developing/client-context.md).

>[!NOTE]
>
>Paginagegevens bevinden zich niet meer in de clientcontext als een standaardcomponent. Indien nodig, kunt u dit toevoegen door de cliëntcontext uit te geven, toevoegend de **Algemene component van de Eigenschappen van de Opslag**, dan vormend dit om de **Opslag** als `pagedata` te bepalen.

## Het clientcontextprofiel wijzigen {#changing-the-client-context-profile}

Met de clientcontext kunt u op interactieve wijze details wijzigen:

* Als u het profiel wijzigt dat wordt gebruikt in de clientcontext, kunt u de verschillende ervaringen zien die de verschillende gebruikers zien voor de huidige pagina.
* U kunt niet alleen het gebruikersprofiel wijzigen, maar ook bepaalde profieldetails wijzigen om te zien hoe de pagina er onder verschillende omstandigheden anders uitziet.

### Een nieuw gebruikersprofiel laden {#loading-a-new-user-profile}

U kunt het profiel als volgt wijzigen:

* [het pictogram load gebruiken](#loading-a-new-visitor-profile-with-the-load-profile-icon)
* [met de selectieregelaar](#loadinganewvisitorprofilewiththeselectionslider)

Wanneer gebeëindigd kunt u [&#x200B; het profiel &#x200B;](#resetting-the-profile-to-the-current-user) terugstellen.

#### Een nieuw bezoekersprofiel laden met het pictogram Profiel laden {#loading-a-new-visitor-profile-with-the-load-profile-icon}

1. Klik op het pictogram Profiel laden:

   ![&#x200B; het pictogram van het Profiel van de Lading van de Context van de Cliënt &#x200B;](do-not-localize/clientcontext_loadprofile.png)

1. Hiermee wordt het dialoogvenster geopend waarin u het profiel kunt selecteren dat u wilt laden:

   ![&#x200B; de dialoog van de Lader van het Profiel die drop-down toont om een profiel te selecteren &#x200B;](assets/clientcontext_profileloader.png)

1. Klik **O.K.** om te laden.

#### Een nieuw gebruikersprofiel laden met de schuifregelaar Selectie {#loading-a-new-user-profile-with-the-selection-slider}

U kunt ook een profiel selecteren met de selectieregelaar:

1. Dubbelklik op het pictogram dat de huidige gebruiker vertegenwoordigt. De kiezer wordt geopend, u kunt met de pijlen navigeren en de beschikbare profielen weergeven:

   ![&#x200B; de gebruikersselecteur &#x200B;](assets/clientcontext_profileselector.png)

1. Klik op het profiel dat u wilt laden. Klik buiten de kiezer om de details te sluiten wanneer deze zijn geladen.

#### Het profiel opnieuw instellen op de huidige gebruiker {#resetting-the-profile-to-the-current-user}

1. Gebruik het pictogram Herstellen om het profiel in de context van de Cliënt aan dat van de huidige gebruiker terug te keren:

   ![&#x200B; het terugstellingspictogram &#x200B;](do-not-localize/clientcontext_resetprofile.png)

### Het browserplatform wijzigen {#changing-the-browser-platform}

1. Dubbelklik op het pictogram dat het browserplatform vertegenwoordigt. De kiezer wordt geopend en u kunt met de pijlen navigeren naar de beschikbare platformen/browsers.

   ![&#x200B; Browser platformselecteur &#x200B;](assets/clientcontext_browserplatform.png)

1. Klik op de platformbrowser die u wilt laden. Klik buiten de kiezer om de details te sluiten wanneer deze zijn geladen.

### De Geolocatie wijzigen {#changing-the-geolocation}

1. Dubbelklik op het geolocatiepictogram. Er wordt een uitgevouwen kaart geopend en u kunt de markering naar een nieuwe locatie slepen:

   ![&#x200B; Geolocation detail &#x200B;](assets/clientcontext_geomocationrelocate.png)

1. Klik buiten de kaart om deze te sluiten.

### De tagselectie wijzigen {#changing-the-tag-selection}

1. Dubbelklik op het gedeelte Tagwolk van de clientcontext. Het dialoogvenster wordt geopend, waar u tags kunt selecteren:

   ![&#x200B; de wolkendialoog van de Markering &#x200B;](assets/clientcontext_tagselection.png)

1. Klik op OK om te laden in de clientcontext.

## De clientcontext bewerken {#editing-the-client-context}

Het bewerken van een clientcontext kan worden gebruikt om de waarden van bepaalde eigenschappen in te stellen (of opnieuw in te stellen), een nieuwe eigenschap toe te voegen of een eigenschap te verwijderen die niet langer nodig is.

### Eigenschappendetails bewerken {#editing-property-details}

Als u een clientcontext bewerkt, kunt u de waarden van bepaalde eigenschappen instellen (of opnieuw instellen). Dit laat u specifieke scenario&#39;s (met name nuttig voor [&#x200B; segmentatie &#x200B;](/help/sites-administering/campaign-segmentation.md) en [&#x200B; campagnes &#x200B;](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md)) testen.

![&#x200B; Uitgevend de Context van de Cliënt &#x200B;](assets/clientcontext_alisonparker_edit.png)

### Een component Property toevoegen {#adding-a-property-component}

Nadat u de **het ontwerppagina van de ClientContext** hebt geopend, kunt u **ook** een volledig nieuw bezit toevoegen gebruikend de beschikbare componenten (de componenten zijn vermeld op zowel sidekick als van de **Nieuwe dialoog van de Component van het Tussenvoegsel** die na een dubbel-klik de **componenten of de activa van de Belemmering hier** doos) wordt geopend:

![&#x200B; Toevoegend een bezit aan het venster van de Context van de Cliënt &#x200B;](assets/clientcontext_alisonparker_new.png)

### Een component Property verwijderen {#removing-a-property-component}

Nadat u de **pagina van het het ontwerpontwerp van de ClientContext** hebt geopend, kunt u **&#x200B;**&#x200B;a bezit ook verwijderen als niet meer vereist. Dit omvat eigenschappen die uit-van-de-doos worden verstrekt; **het Terugstellen** zal deze opnieuw opnemen als zij zijn verwijderd.

## Gegevens opslaan in clientcontext via JSONP {#storing-data-in-client-context-via-jsonp}

Volg dit voorbeeld om de JSONP component van de de contextopslag van de Opslag te gebruiken om externe gegevens aan de Context van de Cliënt toe te voegen. Maak vervolgens een segment op basis van de informatie uit die gegevens. Het voorbeeld gebruikt de dienst JSONP die WIPmania.com verstrekt. De service retourneert informatie over de geolocatie op basis van het IP-adres van de webclient.

In dit voorbeeld wordt de voorbeeldwebsite van Geometrixx Outdoors gebruikt om toegang te krijgen tot Client Context en het gemaakte segment te testen. U kunt een andere website gebruiken zolang de pagina Clientcontext heeft ingeschakeld. (Zie [&#x200B; Toevoegend de Context van de Cliënt aan een Pagina &#x200B;](/help/sites-developing/client-context.md#adding-client-context-to-a-page).)

### De JSONP Store-component toevoegen {#add-the-jsonp-store-component}

Voeg de component van de Winkel JSONP aan de Context van de Cliënt toe en gebruik het om geolocatieinformatie over de Webcliënt terug te winnen en op te slaan.

1. Open de Engelse homepage van de site Geometrixx Outdoors op de AEM auteur. ([&#x200B; https://localhost:4502/content/geometrixx-outdoors/en.html &#x200B;](https://localhost:4502/content/geometrixx-outdoors/en.html)).
1. Druk op Ctrl+Alt+c (vensters) of Control+Option+c (Mac) om de clientcontext te openen.
1. Klik op het bewerkingspictogram boven aan Client Context om Client Context Designer te openen.

   ![&#x200B; het pictogram van de Verbinding &#x200B;](do-not-localize/chlimage_1.png)

1. Sleep de JSONP Store-component naar Client-context.

   ![&#x200B; het slepen en het laten vallen van de component van de JSONP Winkel in de Context van de Cliënt &#x200B;](assets/chlimage_1-4.jpeg)

1. Dubbelklik op de component om het dialoogvenster Bewerken te openen.
1. Voer in het vak URL JSONP-service de volgende URL in en klik op Opslag zoeken:

   `https://api.wipmania.com/jsonp?callback=${callback}`

   De component roept de dienst JSONP en maakt een lijst van alle eigenschappen die de teruggekeerde gegevens bevat. De eigenschappen die in de lijst zijn zijn die die in de Context van de Cliënt beschikbaar zullen zijn.

   ![&#x200B; de eigenschappen van de Dienst JSONP &#x200B;](assets/chlimage_1-40.png)

1. Klik op OK.
1. Ga terug naar de startpagina van Geometrixx Outdoors en vernieuw de pagina. De Context van de cliënt omvat nu de informatie van de component van de Winkel JSONP.

   ![&#x200B; Voorbeeld van de component JSONP bevolkt met gegevens &#x200B;](assets/chlimage_1-41.png)

### Het segment maken {#create-the-segment}

Gebruik de gegevens van de zittingsopslag die u gebruikend de JSONP opslagcomponent creeerde. Het segment gebruikt de breedtegraad van de zittingsopslag en de huidige datum om te bepalen of het wintertijd bij de plaats van de cliënt is.

1. Open de console van Hulpmiddelen in uw Webbrowser (`https://localhost:4502/miscadmin#/etc`).
1. Klik in de mappenstructuur op de map Tools/Segmentation en klik vervolgens op Nieuw > Nieuwe map. Geef de volgende eigenschapswaarden op en klik op Maken:

   * Naam: mijnsegmenten
   * Titel: Mijn segmenten

1. Selecteer de map Mijn segmenten en klik op Nieuw > Nieuwe pagina:

   1. Voor de titel typt u Winter.
   1. Selecteer de Segmentsjabloon.
   1. Klik op Maken.

1. Klik met de rechtermuisknop op het wintersegment en klik op Openen.
1. Sleep het Algemene bezit van de Opslag aan het gebrek EN container.

   ![&#x200B; Toevoegend een component aan de segmentredacteur &#x200B;](assets/chlimage_1-5.jpeg)

1. Dubbelklik op de component om het dialoogvenster Bewerken te openen, geef de volgende eigenschapswaarden op en klik op OK:

   * Bewaren: wipmanie
   * Eigenschapnaam: breedtegraad
   * Operator: is groter dan
   * Waarde eigenschap: 30

1. Sleep de component Script naar dezelfde container AND en open het dialoogvenster voor het bewerken van de component. Voeg het volgende script toe en klik op OK:

   `3 < new Date().getMonth() < 12`
