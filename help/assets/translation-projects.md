---
title: Vertaalprojecten maken
description: Leer hoe te om vertaalprojecten in  [!DNL Adobe Experience Manager] tot stand te brengen.
contentOwner: AG
role: Developer, Admin
feature: Translation
exl-id: 8990feca-cfda-4974-915e-27aa9d8f2ee1
solution: Experience Manager, Experience Manager Assets
source-git-commit: 07289e891399a78568dcac957bc089cc08c7898c
workflow-type: tm+mt
source-wordcount: '1752'
ht-degree: 9%

---

# Vertaalprojecten maken {#creating-translation-projects}

Als u een taalkopie wilt maken, activeert u een van de volgende workflows voor het kopiëren van talen die beschikbaar zijn onder de References-rail in de gebruikersinterface van [!DNL Experience Manager] .

* **creeer en vertaal**: In dit werkschema, worden de te vertalen activa gekopieerd aan de taalwortel van de taal waaraan u wilt vertalen. Bovendien wordt, afhankelijk van de opties u kiest, een vertaalproject gecreeerd voor de activa in de console van Projecten. Afhankelijk van de instellingen kan het vertaalproject handmatig worden gestart of automatisch worden uitgevoerd zodra het vertaalproject is gemaakt.

* **de taalexemplaren van de Update**: Looppas dit werkschema om een extra groep activa te vertalen en het in een taalexemplaar voor een bepaalde scène te omvatten. In dit geval worden de vertaalde elementen toegevoegd aan de doelmap die al eerder vertaalde elementen bevat.

>[!PREREQUISITES]
>
>* Gebruikers die vertaalprojecten maken, zijn lid van de groep `projects-administrators` .
>* De vertaaldienstverlener steunt de vertaling van binaire getallen.

## Workflow maken en vertalen {#create-and-translate-workflow}

Met de workflow Maken en vertalen kunt u voor het eerst voor een bepaalde taal een kopie van de taal genereren. De workflow bevat de volgende opties:

* Alleen structuur maken.
* Maak een vertaalproject.
* Toevoegen aan bestaand vertaalproject.

### Alleen structuur maken {#create-structure-only}

Gebruik de optie **[!UICONTROL Create structure only]** om een hiërarchie van doelmappen te maken in de hoofdmap van de doeltaal, zodat deze overeenkomt met de hiërarchie van de bronmap in de hoofdmap van de brontaal. In dit geval worden bronassets naar de doelmap gekopieerd. Er wordt echter geen vertaalproject gegenereerd.

1. Selecteer in de interface [!DNL Assets] de bronmap waarvoor u een structuur wilt maken in de hoofdmap van de doeltaal.

1. Open het deelvenster **[!UICONTROL References]** en klik op **[!UICONTROL Language Copies]** onder **[!UICONTROL Copies]** .

   ![ de exemplaren van de Taal ](assets/translation-language-copies.png)

1. Klik op **[!UICONTROL Create & Translate]**. Selecteer in de lijst **[!UICONTROL Target Languages]** de taal waarvoor u een mapstructuur wilt maken.

1. Kies in de lijst **[!UICONTROL Project]** de optie **[!UICONTROL Create structure only]**.

1. Klik op **[!UICONTROL Create]**. De nieuwe structuur voor de doeltaal wordt weergegeven onder **[!UICONTROL Language Copies]** .

   ![ taalexemplaren ](assets/lang-copy2.png)

1. Klik op de structuur in de lijst en klik vervolgens op **[!UICONTROL Reveal in Assets]** om naar de mapstructuur in de doeltaal te navigeren.

   ![ openbaren-in-activa ](assets/reveal-in-assets.png)

### Een vertaalproject maken {#create-a-new-translation-project}

Als u deze optie gebruikt, worden de te vertalen middelen gekopieerd aan de taalwortel van de taal waaraan u wilt vertalen. Afhankelijk van de opties u kiest, wordt een vertaalproject gecreeerd voor de activa in de console van Projecten. Afhankelijk van de instellingen kan het vertaalproject handmatig worden gestart of automatisch worden uitgevoerd zodra het vertaalproject is gemaakt.

1. Selecteer in de gebruikersinterface van [!DNL Assets] de bronmap waarvoor u een taalkopie wilt maken.
1. Open het deelvenster **[!UICONTROL References]** en klik op **[!UICONTROL Language Copies]** onder **[!UICONTROL Copies]** .

   ![ chlimage_1-63 ](assets/chlimage_1-63.png)

1. Klik op **[!UICONTROL Create & Translate]** onderaan.

1. Selecteer in de lijst **[!UICONTROL Target Languages]** de talen waarvoor u een mapstructuur wilt maken.

1. Selecteer in de lijst **[!UICONTROL Project]** de optie **[!UICONTROL Create a new translation project]** .

1. Voer in het veld **[!UICONTROL Project Title]** een titel in voor het project.

1. Klik op **[!UICONTROL Create]**. [!DNL Assets] uit de bronmap wordt gekopieerd naar de doelmappen voor de landinstellingen die u in stap 4 hebt geselecteerd.

   ![ taalexemplaren ](assets/lang-copy2.png)

1. Als u naar de map wilt navigeren, selecteert u de taalkopie en klikt u op **[!UICONTROL Reveal in Assets]** .

   ![ openbaren-in-activa ](assets/reveal-in-assets.png)

1. Navigeer aan de console van Projecten. De vertaalomslag wordt gekopieerd aan de console van Projecten.

   ![ chlimage_1-70 ](assets/chlimage_1-70.png)

1. Open de map om het vertaalproject weer te geven.

   ![ chlimage_1-71 ](assets/chlimage_1-71.png)

1. Klik op het project om de detailpagina te openen.

   ![ chlimage_1-72 ](assets/chlimage_1-72.png)

1. Als u de status van de vertaaltaak wilt weergeven, klikt u op de ellips onder aan de tegel **[!UICONTROL Translation Job]** .

   ![ chlimage_1-73 ](assets/chlimage_1-73.png)

   Voor meer details rond baanstatussen, zie [ Controle de Status van een VertaalBaan ](/help/sites-administering/tc-manage.md#monitoring-the-status-of-a-translation-job).

1. Navigeer naar de gebruikersinterface van [!DNL Assets] en open de pagina [!UICONTROL Properties] voor elk van de vertaalde elementen om de vertaalde metagegevens weer te geven.

   ![ mening de vertaalde meta-gegevens in de pagina van ActivaEigenschappen ](assets/translated-metadata-asset-properties.png)

   *Cijfer: Vertaalde meta-gegevens in de pagina van activa eigenschappen.*

   >[!NOTE]
   >
   >Deze functie is beschikbaar voor zowel elementen als mappen. Wanneer een middel in plaats van een omslag wordt geselecteerd, wordt de volledige hiërarchie van omslagen tot de taalwortel gekopieerd om een taalexemplaar voor de activa tot stand te brengen.

### Toevoegen aan bestaand vertaalproject {#add-to-existing-translation-project}

Als u deze optie gebruikt, wordt de vertaalworkflow uitgevoerd voor elementen die u na een vorige vertaalworkflow aan de bronmap toevoegt. Alleen de nieuw toegevoegde elementen worden gekopieerd naar de doelmap die eerder vertaalde elementen bevat. In dit geval wordt geen nieuw vertaalproject opgezet.

1. Navigeer in de gebruikersinterface van [!DNL Assets] naar de bronmap die niet-vertaalde elementen bevat.
1. Selecteer een asset die u wilt vertalen en open het **[!UICONTROL Reference pane]**. In de sectie **[!UICONTROL Language Copies]** wordt het aantal momenteel beschikbare vertaalkopieën weergegeven.
1. Klik op **[!UICONTROL Language Copies]** onder **[!UICONTROL Copies]** . Er wordt een lijst met beschikbare vertaalkopieën weergegeven.
1. Klik op **[!UICONTROL Create & Translate]** onderaan.

1. Selecteer in de lijst **[!UICONTROL Target Languages]** de talen waarvoor u een mapstructuur wilt maken.

1. Selecteer in de lijst **[!UICONTROL Project]** de optie **[!UICONTROL Add to existing translation project]** om de vertaalworkflow in de map uit te voeren.

   >[!NOTE]
   >
   >Als u de optie **[!UICONTROL Add to existing translation project]** kiest, wordt uw vertaalproject alleen aan een reeds bestaand project toegevoegd als uw projectinstellingen exact overeenkomen met de instellingen van het reeds bestaande project. Anders wordt een nieuw project gemaakt.

1. Selecteer in de lijst **[!UICONTROL Existing translation project]** een project waaraan u het element voor vertaling wilt toevoegen.

1. Klik op **[!UICONTROL Create]**. De te vertalen assets worden toegevoegd aan de doelmap. De bijgewerkte map wordt weergegeven onder de sectie **[!UICONTROL Language Copies]**.

   ![ chlimage_1-79 ](assets/chlimage_1-79.png)

1. Navigeer aan de console van Projecten, en open het bestaande vertaalproject u aan toevoegde.
1. Klik op de pagina met projectdetails voor het vertaalproject.

   ![ chlimage_1-80 ](assets/chlimage_1-80.png)

1. Klik de ellips bij de bodem van de **tegel van de VertaalBaan** om de activa in het vertaalwerkschema te bekijken. In de lijst met vertaaltaken worden ook items voor metagegevens en tags van elementen weergegeven. Deze vermeldingen geven aan dat de metagegevens en tags voor de elementen ook worden vertaald.

   >[!NOTE]
   >
   >Als u het item voor tags of metagegevens verwijdert, worden er geen tags of metagegevens voor de elementen omgezet.

   >[!NOTE]
   >
   >Als het element dat u toevoegt aan de vertaaltaak subelementen bevat, selecteert u de subelementen en verwijdert u deze zodat de vertaling zonder scheuren kan worden uitgevoerd.

1. Als u de vertaling voor de elementen wilt starten, klikt u op de pijl op de **[!UICONTROL Translation Job]** -tegel en selecteert u **[!UICONTROL Start]** in de lijst.

   ![ chlimage_1-81 ](assets/chlimage_1-81.png)

   Een bericht brengt het begin van de vertaalbaan op de hoogte.

1. Als u de status van de vertaaltaak wilt weergeven, klikt u op de ellips onder aan de tegel **[!UICONTROL Translation Job]** .

   ![ chlimage_1-83 ](assets/chlimage_1-83.png)

   Voor meer details, zie [ Controle de Status van een VertaalBaan ](/help/sites-administering/tc-manage.md#monitoring-the-status-of-a-translation-job).

1. Nadat de vertaling is voltooid, verandert de status in Klaar voor revisie. Navigeer naar de gebruikersinterface van [!DNL Assets] en open de pagina Eigenschappen voor elk van de vertaalde elementen om de vertaalde metagegevens weer te geven.

## Taalkopieën bijwerken {#update-language-copies}

Voer deze workflow uit om extra elementen te vertalen en deze op te nemen in een taalkopie voor een bepaalde landinstelling. In dit geval worden de vertaalde elementen toegevoegd aan de doelmap die al eerder vertaalde elementen bevat. Afhankelijk van de keuze van opties wordt een vertaalproject gemaakt of wordt een bestaand vertaalproject bijgewerkt voor de nieuwe elementen. De workflow voor het kopiëren van de taal Bijwerken bevat de volgende opties:

* Een vertaalproject maken
* Toevoegen aan bestaand vertaalproject

### Een vertaalproject maken {#create-a-new-translation-project-1}

Als u deze optie gebruikt, wordt een vertaalproject gecreeerd voor de reeks activa waarvoor u een taalexemplaar wilt bijwerken.

1. Selecteer in de gebruikersinterface van [!DNL Assets] de bronmap waarin u elementen hebt toegevoegd.
1. Open het deelvenster **[!UICONTROL References]** en klik op **[!UICONTROL Language Copies]** onder **[!UICONTROL Copies]** om de lijst met taalkopieën weer te geven.
1. Schakel het selectievakje voor **[!UICONTROL Language Copies]** in en selecteer vervolgens de doelmap die overeenkomt met de juiste landinstelling.

   ![ uitgezochte taalexemplaar ](assets/lang-copy1.png)

1. Klik op **[!UICONTROL Update language copies]** onderaan.

1. Kies in de lijst **[!UICONTROL Project]** de optie **[!UICONTROL Create a new translation project]**.

1. Voer in het veld **[!UICONTROL Project Title]** een titel in voor het project.

1. Klik op **[!UICONTROL Start]**.
1. Navigeer aan de console van Projecten. De vertaalomslag wordt gekopieerd aan de console van Projecten.

   ![ chlimage_1-88 ](assets/chlimage_1-88.png)

1. Open de map om het vertaalproject weer te geven.

   ![ chlimage_1-89 ](assets/chlimage_1-89.png)

1. Klik op het project om de detailpagina te openen.

   ![ chlimage_1-90 ](assets/chlimage_1-90.png)

1. Als u de vertaling voor de elementen wilt starten, klikt u op de pijl op de **[!UICONTROL Translation Job]** -tegel en selecteert u **[!UICONTROL Start]** in de lijst.

   ![ chlimage_1-91 ](assets/chlimage_1-91.png)

   Een bericht brengt het begin van de vertaalbaan op de hoogte.

1. Als u de status van de vertaaltaak wilt weergeven, klikt u op de ellips onder aan de tegel **[!UICONTROL Translation Job]** .

   ![ chlimage_1-93 ](assets/chlimage_1-93.png)

   Voor meer details rond baanstatussen, zie [ Controle de Status van een VertaalBaan ](../sites-administering/tc-manage.md#monitoring-the-status-of-a-translation-job).

1. Navigeer naar de gebruikersinterface van [!DNL Assets] en open de pagina Eigenschappen voor elk van de vertaalde elementen om de vertaalde metagegevens weer te geven.

### Toevoegen aan bestaand vertaalproject {#add-to-existing-translation-project-1}

Als u deze optie gebruikt, worden de elementen toegevoegd aan een bestaand vertaalproject en wordt de taalkopie bijgewerkt voor de landinstelling die u kiest.

1. Selecteer in de gebruikersinterface van [!DNL Assets] de bronmap waaraan u een elementmap hebt toegevoegd.
1. Open **[!UICONTROL References pane]** en klik **[!UICONTROL Language Copies]** onder **[!UICONTROL Copies]** om de lijst met taalkopieën weer te geven.

   ![ chlimage_1-94 ](assets/chlimage_1-94.png)

1. Schakel het selectievakje voor **[!UICONTROL Language Copies]** in om alle taalkopieën te selecteren. Hef de selectie van andere kopieën op, met uitzondering van de taalkopieën die overeenkomen met de landinstellingen waarnaar u wilt vertalen.

   ![ uitgezochte taalexemplaar ](assets/lang-copy1.png)

1. Klik op **[!UICONTROL Update language copies]** onderaan.

1. Kies in de lijst **[!UICONTROL Project]** de optie **[!UICONTROL Add to existing translation project]**.

1. Selecteer in de lijst **[!UICONTROL Existing translation project]** een project waaraan u het element voor vertaling wilt toevoegen.

1. Klik op **[!UICONTROL Start]**.
1. Zie stappen 9-14 van [ toevoegen aan bestaand vertaalproject ](translation-projects.md#add-to-existing-translation-project) om de rest van de procedure te voltooien.

## Tijdelijke taalkopieën maken {#creating-temporary-language-copies}

Wanneer u een vertaalworkflow uitvoert om een taalkopie bij te werken met bewerkte versies van originele elementen, blijft de bestaande taalkopie behouden totdat u de vertaalde elementen goedkeurt. [!DNL Adobe Experience Manager Assets] slaat de nieuw vertaalde middelen op een tijdelijke plaats op en werkt het bestaande taalexemplaar bij nadat u uitdrukkelijk de activa goedkeurt. Als u de elementen afwijst, blijft de taalkopie ongewijzigd.

1. Klik op de bronhoofdmap onder **[!UICONTROL Language Copies]** waarvoor u al een taalkopie hebt gemaakt en klik vervolgens op **[!UICONTROL Reveal in Assets]** om de map te openen in [!DNL Experience Manager Assets] .

   ![ chlimage_1-99 ](assets/chlimage_1-99.png)

1. Selecteer in de interface van [!DNL Assets] een element dat u al hebt omgezet en klik op **[!UICONTROL Edit]** op de werkbalk om het element te openen in de bewerkingsmodus.
1. Bewerk het element en sla de wijzigingen op.
1. Voer stappen 2-14 van [ uit toevoegen aan bestaand vertaalproject ](#add-to-existing-translation-project) procedure om het taalexemplaar bij te werken.
1. Klik op de ellips onder aan de tegel **[!UICONTROL Translation Job]** . In de lijst met elementen op de pagina **[!UICONTROL Translation Job]** kunt u duidelijk de tijdelijke locatie weergeven waar de vertaalde versie van het element is opgeslagen.

   ![ chlimage_1-101 ](assets/chlimage_1-101.png)

1. Schakel het selectievakje naast **[!UICONTROL Title]** in.
1. Van de toolbar, keurt de klik **[!UICONTROL Accept Translation]** ![ vertaling ](assets/do-not-localize/thumb-up.png) goed en klikt dan **[!UICONTROL Accept]** in de dialoog om de vertaalde activa in de doelomslag met de vertaalde versie van de uitgegeven activa te beschrijven.

   >[!NOTE]
   >
   >Accepteer zowel het element als de metagegevens om de vertaalworkflow in staat te stellen de doelelementen bij te werken.

   Klik **[!UICONTROL Reject Translation]** ![ vertalen ](assets/do-not-localize/thumb-down.png) verwerpen om de oorspronkelijk vertaalde versie van de activa in de doelscènewortel te behouden en de uitgegeven versie te verwerpen.

1. Als u de vertaalde metagegevens wilt weergeven, navigeert u naar de [!DNL Assets] -console en opent u de pagina [!UICONTROL Properties] voor elk van de vertaalde elementen.

## Tips en beperkingen {#tips-limitations}

* Als u een vertaalworkflow start voor complexe elementen, zoals PDF- en [!DNL Adobe InDesign] -bestanden, worden de subelementen of vertoningen (indien aanwezig) van die elementen niet verzonden voor vertaling.
* Als u automatische vertaling gebruikt, worden de binaire bestanden met elementen niet vertaald.
