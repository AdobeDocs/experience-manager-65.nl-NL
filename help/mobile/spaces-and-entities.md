---
title: Spaties en entiteiten
seo-title: AEM Mobile Content Services ontwikkelen
description: Deze pagina bevat een openingspagina voor de ontwikkeling van AEM Mobile Content Services.
seo-description: Deze pagina bevat een openingspagina voor de ontwikkeling van AEM Mobile Content Services.
uuid: eab5a61b-a9e8-4863-90a3-df1f18510cd8
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
discoiquuid: ef568577-c74e-4fc2-b66e-eedac2948310
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Spaties en entiteiten{#spaces-and-entities}

>[!NOTE]
>
>Adobe adviseert gebruikend de Redacteur van het KUUROORD voor projecten die op kader-gebaseerde cliënt-zijteruggeven van enige paginatoepassing (b.v. Reageren) vereisen. [Meer](/help/sites-developing/spa-overview.md)informatie.

Een spatie is een handige locatie voor het opslaan van entiteiten die via de REST-API van Content Services worden weergegeven. Dit is vooral handig omdat een app (of elk kanaal) aan veel entiteiten kan worden gekoppeld. Als u entiteiten dwingt zich in een ruimte te bevinden, kunt u de best practices voor het groeperen van de vereisten van een app bundelen. U kunt desgewenst een toepassing in AEM koppelen aan een klein aantal spaties.

>[!NOTE]
>
>Om iets van de Diensten van de Inhoud ter beschikking te stellen aan om het even welk kanaal, moet het onder een ruimte zijn.

## Een spatie maken {#creating-a-space}

Als de gebruiker een aantal inhoud en elementen toegankelijk wil maken voor een mobiele app, maakt de gebruiker de ruimte met behulp van het AEM Mobile-dashboard.

Voor het eerst wordt op het AEM Mobile-dashboard alleen Apps weergegeven nadat u **Content Services** hebt geselecteerd, een gebruiker die de inhoudsservices niet heeft geconfigureerd voor gebruik met spaties.

>[!CAUTION]
>
>**Voorwaarden voor het toevoegen van een spatie**
>
>Schakel AEM Content Services **** inschakelen in om te werken met spaties en schakel deze in het dashboard voor uw AEM Mobile-toepassing in.
>
>Zie [Inhoudsservices](/help/mobile/developing-content-services.md) beheren voor meer informatie.

Nadat u de spaties in het dashboard hebt geconfigureerd, voert u de volgende stappen uit om spaties te maken:

1. Kies **Spaties** in Content Services.

   ![chlimage_1-83](assets/chlimage_1-83.png)

1. Kies **Maken** om een spatie te maken. Voer **Titel**, **Naam** en **Beschrijving** in voor de ruimte.

   Klik op **Maken**.

   ![chlimage_1-84](assets/chlimage_1-84.png)

## Een spatie beheren {#managing-a-space}

Wanneer u een spatie hebt gemaakt, klikt u links om de ruimte in de lijst te beheren.

U kunt de eigenschappen van de ruimte weergeven, de ruimte verwijderen of de ruimte en de inhoud ervan publiceren naar een AEM-publicatie-instantie.

![chlimage_1-85](assets/chlimage_1-85.png)

**Eigenschappen van een spatie weergeven en bewerken**

1. De ruimte in de lijst selecteren
1. Kies **Eigenschappen** op de werkbalk
1. Klik op **Sluiten** als u klaar bent

**Een spatie** publiceren Wanneer een spatie wordt gepubliceerd, worden ook alle mappen en entiteiten in die ruimte gepubliceerd.

1. Selecteer de ruimte door op het bijbehorende pictogram in de lijst voor de ruimteconsole te klikken
1. Publicatiestructuur **kiezen**

>[!NOTE]
>
>U kunt de publicatie van een spatie **ongedaan maken** . Hierdoor wordt de ruimte uit het publicatie-exemplaar verwijderd.
>
>De volgende afbeelding illustreert de acties die kunnen worden uitgevoerd nadat u de ruimte hebt gepubliceerd.

![chlimage_1-86](assets/chlimage_1-86.png)

## Werken met mappen in een spatie {#working-with-folders-in-a-space}

Spaties kunnen mappen bevatten voor een betere organisatie van de inhoud en elementen van de ruimte. Gebruikers kunnen hun eigen hiërarchie onder een spatie maken.

### Een map maken {#creating-a-folder}

1. Klik op de ruimte in de lijst in de ruimteconsole en klik op Map **maken**

   ![chlimage_1-87](assets/chlimage_1-87.png)

1. Voer de **titel**, **** naam en **beschrijving** voor de map in

   ![chlimage_1-88](assets/chlimage_1-88.png)

1. Klik op **Maken** om de map in een ruimte te maken

## Taalkopie {#language-copy}

>[!CAUTION]
>
>Taalkopie is niet volledig functioneel voor deze release. De structuur wordt alleen ingesteld.

Met de functie **Taalkopie** kunnen auteurs hun hoofdtaalkopie kopiëren en vervolgens een project en workflow maken om de inhoud automatisch te vertalen. Met Taalkopie maakt u de juiste structuur. Nadat u een map in een ruimte hebt toegevoegd, kunt u het taalexemplaar aan de ruimte toevoegen.

>[!NOTE]
>
>Het wordt aanbevolen om inhoud die vertaald kan worden onder het knooppunt Taalkopie te plaatsen.

### Taalkopie toevoegen {#adding-language-copy}

1. Wanneer u ruimte hebt gemaakt, klikt u op die ruimte om een taalkopie te maken.

   Klik op **Maken** en kies **Taalkopie**.

   ![chlimage_1-89](assets/chlimage_1-89.png)

   >[!NOTE]
   >
   >De knopen van het Exemplaar van de Taal kunnen slechts als direct kind van de Ruimte bestaan.

1. **** Taal&amp;amp voor **inhoudspakket kiezen;ast; en voer de** titel&amp;amp in; in het dialoogvenster **Taalkopie** maken.

   Klik op **Maken**.

   ![chlimage_1-90](assets/chlimage_1-90.png)

1. Zodra u een Exemplaar van de Taal creeert, verschijnt het in uw ruimte in de **Stramienen** van de Taal.

   ![chlimage_1-91](assets/chlimage_1-91.png)

   >[!NOTE]
   >
   >Selecteer **Taalstramienen** om de mappen voor het kopiëren van talen weer te geven.

### Een map uit de ruimte verwijderen {#removing-a-folder-from-the-space}

1. Selecteer de map in de lijst met ruimte-inhoud
1. Klik op **Verwijderen** op de werkbalk

   >[!NOTE]
   >
   >Als u in een map wilt navigeren en de inhoud ervan wilt bekijken of een submap of entiteit wilt toevoegen, klikt u op de titel van de map in de inhoudslijst van de ruimte.

## Werken met entiteiten in een spatie {#working-with-entities-in-a-space}

De entiteiten vertegenwoordigen inhoud die door het eindpunt van de Webdienst wordt blootgesteld. Entiteiten worden opgeslagen in ruimtes zodat ze gemakkelijk kunnen worden gevonden en onafhankelijk blijven van de AEM-opslagstructuur die hun gerelateerde inhoud bevat.

U kunt entiteiten in één of andere logische inzameling willen groeperen. Hiertoe kunt u een willekeurig aantal mappen maken.

Als de entiteitkinderen, die andere entiteiten zijn, voor gegevensmodellering worden verzameld, kan de ontwikkelaarsgebruiker specifieke &quot;Modellen van de Groep&quot;van het modeltype van de &quot;Groep van de Entiteit&quot;tot stand brengen, verstrekt uit-van-de-doos.

>[!NOTE]
>
>Entiteiten worden altijd gekoppeld aan een spatie, zodat het grootste deel van de gebruikersinterface van de entiteit wordt benaderd via de spatieconsole.

### Entiteiten maken {#creating-an-entity}

1. Open de Ruimteconsole en klik op de titel van de ruimte.

   U kunt desgewenst naar de map navigeren door op de titel van de map in de lijst te klikken.

   ![chlimage_1-92](assets/chlimage_1-92.png)

1. Kies het model voor de entiteit. Dit is het type entiteit dat u wilt maken. Klik op Volgende.

   ![chlimage_1-93](assets/chlimage_1-93.png)

   >[!NOTE]
   >
   >U kunt kiezen uit het **middelenmodel**, het **paginamodel** of een model van het eenheidstype dat u eerder hebt gemaakt.
   >
   >Zie Een model [](/help/mobile/administer-mobile-apps.md)maken om een aangepaste entiteit te maken.

1. Voer een **titel**, **naam**, **beschrijving** en **tags** voor de entiteit in. Klik op **Maken**.

   ![chlimage_1-94](assets/chlimage_1-94.png)

   Zodra u wordt gedaan, verschijnt de entiteit in de nakomelingen van uw ruimte.

### Een entiteit bewerken {#editing-an-entity}

1. Nadat u een entiteit hebt gemaakt, gaat u naar de map of ruimte en kiest u uw entiteit in de ruimteconsole die u wilt bewerken.

   ![chlimage_1-95](assets/chlimage_1-95.png)

1. Selecteer een entiteit die u wilt bewerken en klik op **Bewerken**.

   ![chlimage_1-96](assets/chlimage_1-96.png)

   >[!CAUTION]
   >
   >Afhankelijk van de sjabloon die u kiest om uw entiteit te maken, zal de interface voor beide variëren, voor het bewerken en weergeven van eigenschappen van uw entiteit. Zie de onderstaande stappen voor meer informatie.

   ***Als u de sjabloon voor het maken van de entiteit als middelenmodellen*** kiest en u op **Bewerken** klikt, kunt u elementen toevoegen zoals in de onderstaande afbeelding wordt getoond:

   ![chlimage_1-97](assets/chlimage_1-97.png)

   U kunt ook op **Voorvertoning** klikken om de koppeling JSON weer te geven.

   ![chlimage_1-98](assets/chlimage_1-98.png)

   ***Als u de sjabloon voor het maken van de entiteit als paginamodellen*** kiest en u op **Bewerken** klikt, kunt u elementen toevoegen zoals in de onderstaande afbeelding wordt getoond:

   ![chlimage_1-99](assets/chlimage_1-99.png)

   Klik op het pictogram in het **pad** om een element toe te voegen

   ![chlimage_1-100](assets/chlimage_1-100.png)

   >[!NOTE]
   >
   >Als u een entiteit hebt toegevoegd, moet deze worden opgeslagen voordat de koppeling Voorvertoning werkt. Klik op **Opslaan** om de voorvertoning weer te geven. Klik op de **voorvertoning** om de hoek van het toegevoegde element weer te geven, zoals in de onderstaande afbeelding wordt getoond:

   ![chlimage_1-101](assets/chlimage_1-101.png)

   >[!NOTE]
   >
   >Wanneer u klaar bent met het toevoegen van elementen aan uw entiteit, kunt u kiezen **Opslaan** om de wijzigingen op te slaan of **Opslaan en sluiten** kiezen om op te slaan en om te leiden naar de lijst met ruimteconsole waarin de entiteiten zijn gedefinieerd.

   Selecteer bovendien een entiteit in de lijst met ruimteconsole en klik op **Eigenschappen** om de eigenschappen voor een gedefinieerde entiteit weer te geven en te bewerken.

   ![chlimage_1-102](assets/chlimage_1-102.png)

   U kunt de titel, beschrijving, tags bewerken en de elementen aan de entiteit toevoegen.

   ![chlimage_1-103](assets/chlimage_1-103.png)

### Entiteiten verwijderen {#removing-an-entity}

1. Entiteiten in de lijst met ruimte-inhoud selecteren

   ![chlimage_1-104](assets/chlimage_1-104.png)

1. Klik op **Verwijderen** op de werkbalk om de specifieke entiteit uit de ruimte te verwijderen

### Entiteiten publiceren {#publishing-an-entity}

U kunt desgewenst de **publicatiestructuur** of **Snel publiceren** kiezen om uw entiteit te publiceren.

1. Selecteer een entiteit in de lijst met ruimteconsole en klik op **Publiceer de structuur **om die entiteit en de onderliggende elementen te publiceren.

   ![chlimage_1-105](assets/chlimage_1-105.png)

   **Of**,

   Klik op **Snel publiceren** om die specifieke entiteit te publiceren.
