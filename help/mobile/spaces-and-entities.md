---
title: Spaties en entiteiten
description: Deze pagina dient een openingspagina voor het ontwikkelen van AEM Mobile Content Services.
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
exl-id: 44591900-b01b-4a33-9910-839564477e7d
solution: Experience Manager
feature: Mobile
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '1206'
ht-degree: 0%

---

# Spaties en entiteiten{#spaces-and-entities}

>[!NOTE]
>
>De Adobe adviseert het gebruiken van de SPARedacteur voor projecten die op kader-gebaseerde cliënt-zijteruggeven van enige paginatoepassing (bijvoorbeeld, Reageren) vereisen. [Meer informatie](/help/sites-developing/spa-overview.md).

Een spatie is een handige locatie voor het opslaan van entiteiten die via de REST-API van Content Services worden weergegeven. Dit is vooral handig omdat een app (of elk kanaal) aan veel entiteiten kan worden gekoppeld. Als u entiteiten dwingt zich in een ruimte te bevinden, kunt u de best practices voor het groeperen van de vereisten van een app bundelen. U kunt desgewenst een toepassing in AEM koppelen aan een klein aantal spaties.

>[!NOTE]
>
>Om iets van de Diensten van de Inhoud ter beschikking te stellen aan om het even welk kanaal, moet het onder een ruimte zijn.

## Een spatie maken {#creating-a-space}

Als de gebruiker een aantal inhoud en elementen toegankelijk wil maken voor een mobiele app, maakt de gebruiker de ruimte met behulp van het AEM Mobile-dashboard.

Voor de eerste gebruiker, die geen inhoudsservices heeft geconfigureerd voor gebruik met spaties, geeft het AEM Mobile-dashboard alleen Apps weer na het selecteren **Inhoudsservices**.

>[!CAUTION]
>
>**Voorwaarden voor het toevoegen van een spatie**
>
>Controleer de **AEM Content Services inschakelen** om met Spaces te werken en het in uw AEM Mobile toepassingsdashboard toe te laten.
>
>Zie [Inhoudsservices beheren](/help/mobile/developing-content-services.md) voor meer informatie .

Nadat u de spaties in het dashboard hebt geconfigureerd, voert u de volgende stappen uit om spaties te maken:

1. Kies **Spaties** van Content Services.

   ![chlimage_1-83](assets/chlimage_1-83.png)

1. Kies **Maken** om een spatie te maken. Enter **Titel**, **Naam**, en **Beschrijving** voor de ruimte.

   Klikken **Maken**.

   ![chlimage_1-84](assets/chlimage_1-84.png)

## Een spatie beheren {#managing-a-space}

Nadat u een spatie hebt gemaakt, klikt u links om de ruimte in de lijst te beheren.

U kunt de eigenschappen van de ruimte weergeven, de ruimte verwijderen of de ruimte en de inhoud ervan publiceren naar een AEM-publicatie-instantie.

![chlimage_1-85](assets/chlimage_1-85.png)

**Eigenschappen van een spatie weergeven en bewerken**

1. De ruimte in de lijst selecteren
1. Kies **Eigenschappen** van de werkbalk
1. Klikken **Sluiten** wanneer gereed

**Een spatie publiceren** Wanneer een ruimte wordt gepubliceerd, worden alle mappen en entiteiten in die ruimte ook gepubliceerd.

1. Selecteer de ruimte door op het bijbehorende pictogram in de lijst voor de ruimteconsole te klikken
1. Kies **Boomstructuur publiceren**

>[!NOTE]
>
>U kunt **Publiceren ongedaan maken** een spatie, die de ruimte uit de publicatie-instantie verwijdert.
>
>De volgende afbeelding illustreert de acties die kunnen worden uitgevoerd nadat u de ruimte hebt gepubliceerd.

![chlimage_1-86](assets/chlimage_1-86.png)

## Werken met mappen in een spatie {#working-with-folders-in-a-space}

De ruimten kunnen omslagen omvatten om ruimteinhoud en activa verder te organiseren. Gebruikers kunnen hun eigen hiërarchie onder een spatie maken.

### Een map maken {#creating-a-folder}

1. Klik op de ruimte in de lijst in de ruimteconsole en klik op **Map maken**

   ![chlimage_1-87](assets/chlimage_1-87.png)

1. Voer de **Titel**, **Naam,** en **Beschrijving** voor de map

   ![chlimage_1-88](assets/chlimage_1-88.png)

1. Klikken **Maken** om de map in een ruimte te maken

## Taalkopie {#language-copy}

>[!CAUTION]
>
>Taalkopie is niet volledig functioneel voor deze release. De structuur wordt alleen ingesteld.

De **Taalkopie** kunnen auteurs hun hoofdtaalkopie kopiëren en vervolgens een project en workflow maken om de inhoud automatisch te vertalen. Met Taalkopie maakt u de juiste structuur. Nadat u een map in een ruimte hebt toegevoegd, kunt u het taalexemplaar aan de ruimte toevoegen.

>[!NOTE]
>
>Het wordt aanbevolen om inhoud die vertaald kan worden onder het knooppunt Taalkopie te plaatsen.

### Taalkopie toevoegen {#adding-language-copy}

1. Nadat u ruimte hebt gemaakt, klikt u op die ruimte om een taalkopie te maken.

   Klikken **Maken** en kiest u **Taalkopie**.

   ![chlimage_1-89](assets/chlimage_1-89.png)

   >[!NOTE]
   >
   >De knopen van het Exemplaar van de Taal kunnen slechts als direct kind van de Ruimte bestaan.

1. Kies **Taal&amp;ast inhoudspakket;** en voert u de **Titel&amp;ast;** in **Taalkopie maken** in.

   Klikken **Maken**.

   ![chlimage_1-90](assets/chlimage_1-90.png)

1. Wanneer u een taalkopie hebt gemaakt, wordt deze in uw ruimte weergegeven in **Taalmeesters**.

   ![chlimage_1-91](assets/chlimage_1-91.png)

   >[!NOTE]
   >
   >Selecteren **Taalmeesters** om de mappen voor het kopiëren van talen weer te geven.

### Een map uit de ruimte verwijderen {#removing-a-folder-from-the-space}

1. Selecteer de map in de lijst met ruimte-inhoud
1. Klikken **Verwijderen** van de werkbalk

   >[!NOTE]
   >
   >Als u in een map wilt navigeren en de inhoud ervan wilt bekijken of een submap of entiteit wilt toevoegen, klikt u op de titel van de map in de inhoudslijst van de ruimte.

## Werken met entiteiten in een spatie {#working-with-entities-in-a-space}

De entiteiten vertegenwoordigen inhoud die door het eindpunt van de Webdienst wordt blootgesteld. Entiteiten worden opgeslagen in spaties, zodat ze gemakkelijk kunnen worden gevonden en onafhankelijk blijven van de AEM opslagplaats die de bijbehorende inhoud bevat.

U kunt entiteiten in één of andere logische inzameling willen groeperen. Hiertoe kunt u een willekeurig aantal mappen maken.

Als de entiteitkinderen, die andere entiteiten zijn, voor gegevensmodellering worden verzameld, kan de ontwikkelaarsgebruiker specifieke &quot;Modellen van de Groep&quot;van het modeltype van de &quot;Groep van de Entiteit&quot;tot stand brengen, verstrekt uit-van-de-doos.

>[!NOTE]
>
>Entiteiten worden altijd gekoppeld aan een spatie, zodat het grootste deel van de gebruikersinterface van de entiteit wordt benaderd via de spatieconsole.

### Entiteiten maken {#creating-an-entity}

1. Open de Ruimteconsole en klik de titel van de ruimte.

   U kunt desgewenst naar de map navigeren door op de titel van de map in de lijst te klikken.

   ![chlimage_1-92](assets/chlimage_1-92.png)

1. Kies het model voor de entiteit. Dit is het type entiteit dat u wilt maken. Klik op Volgende.

   ![chlimage_1-93](assets/chlimage_1-93.png)

   >[!NOTE]
   >
   >U kunt kiezen uit de **Elementenmodel**, **Paginamodel** of een model van een eenheidstype dat u eerder hebt gemaakt.
   >
   >Zie [Een model maken](/help/mobile/administer-mobile-apps.md), om uw aangepaste entiteit te maken.

1. Voer een **Titel**, **Naam**, **Beschrijving**, en **Tags** voor de entiteit. Klikken **Maken**.

   ![chlimage_1-94](assets/chlimage_1-94.png)

   Zodra u wordt gedaan, verschijnt de entiteit in de nakomelingen van uw ruimte.

### Entiteiten bewerken {#editing-an-entity}

1. Nadat u een entiteit hebt gemaakt, gaat u naar de map of ruimte en kiest u uw entiteit in de ruimteconsole die u wilt bewerken.

   ![chlimage_1-95](assets/chlimage_1-95.png)

1. Entiteiten selecteren voor bewerken en klikken **Bewerken**.

   ![chlimage_1-96](assets/chlimage_1-96.png)

   >[!CAUTION]
   >
   >Afhankelijk van de sjabloon die u kiest om uw entiteit te maken, zal de interface voor beide variëren, voor het bewerken en weergeven van eigenschappen van uw entiteit. Zie de onderstaande stappen voor meer informatie.

   ***Als u de sjabloon voor het maken van de entiteit kiest als middelenmodellen***, klikken op **Bewerken** Hiermee kunt u elementen toevoegen, zoals in de onderstaande afbeelding wordt getoond:

   ![chlimage_1-97](assets/chlimage_1-97.png)

   U kunt ook op **Voorvertoning** om de json link te bekijken.

   ![chlimage_1-98](assets/chlimage_1-98.png)

   ***Als u de sjabloon voor het maken van de entiteit kiest als paginamodellen***, klikken op **Bewerken** Hiermee kunt u elementen toevoegen, zoals in de onderstaande afbeelding wordt getoond:

   ![chlimage_1-99](assets/chlimage_1-99.png)

   Klik op het pictogram in het dialoogvenster **Pad** om een element toe te voegen

   ![chlimage_1-100](assets/chlimage_1-100.png)

   >[!NOTE]
   >
   >Als u een entiteit hebt toegevoegd, moet deze worden opgeslagen om de koppeling Voorvertoning te kunnen gebruiken. Klik op **Opslaan**. Klik op de knop **Voorvertoning** toont de json van de toegevoegde activa, zoals aangetoond in het hieronder figuur:

   ![chlimage_1-101](assets/chlimage_1-101.png)

   >[!NOTE]
   >
   >Wanneer u klaar bent met het toevoegen van elementen aan uw entiteit, kunt u **Opslaan** om de wijzigingen op te slaan of **Opslaan en sluiten** om op te slaan en om te leiden naar de Spatieconsolelijst waar de entiteiten zijn gedefinieerd.

   Selecteer bovendien een entiteit in de lijst met ruimteconsole en klik op **Eigenschappen** om de eigenschappen voor een gedefinieerde entiteit weer te geven en te bewerken.

   ![chlimage_1-102](assets/chlimage_1-102.png)

   U kunt de titel, beschrijving, tags bewerken en de elementen aan de entiteit toevoegen.

   ![chlimage_1-103](assets/chlimage_1-103.png)

### Entiteiten verwijderen {#removing-an-entity}

1. Entiteiten in de lijst met ruimte-inhoud selecteren

   ![chlimage_1-104](assets/chlimage_1-104.png)

1. Klikken **Verwijderen** van de werkbalk om de specifieke entiteit uit de ruimte te verwijderen

### Entiteiten publiceren {#publishing-an-entity}

U kunt kiezen **Boomstructuur publiceren** of **Snel publiceren** om uw entiteit te publiceren.

1. Selecteer een entiteit in de lijst met ruimteconsole en klik op **Publiceer de structuur **om die entiteit en de onderliggende elementen te publiceren.

   ![chlimage_1-105](assets/chlimage_1-105.png)

   **of**,

   Klikken **Snel publiceren** die specifieke entiteit te publiceren.
