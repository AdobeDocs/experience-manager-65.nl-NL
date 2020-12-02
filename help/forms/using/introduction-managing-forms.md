---
title: Inleiding tot het beheren van formulieren
seo-title: Inleiding tot het beheren van formulieren
description: AEM Forms biedt tools voor het beheer van Adaptive Forms en gerelateerde middelen. In dit artikel worden de belangrijkste mogelijkheden voor formulierbeheer en gebruikersinterface-elementen besproken.
seo-description: AEM Forms biedt tools voor het beheer van Adaptive Forms en gerelateerde middelen. In dit artikel worden de belangrijkste mogelijkheden voor formulierbeheer en gebruikersinterface-elementen besproken.
uuid: 2275a0b6-b31e-4d8e-8154-ccdfff3705aa
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-manager, introduction
discoiquuid: c0e4c9bb-e12a-4f9a-a8fa-1a8ad41d3995
docset: aem65
translation-type: tm+mt
source-git-commit: 46f2ae565fe4a8cfea49572eb87a489cb5d9ebd7
workflow-type: tm+mt
source-wordcount: '1589'
ht-degree: 0%

---


# Inleiding tot het beheren van formulieren {#introduction-to-managing-forms}

AEM [!DNL Forms] biedt een vereenvoudigde maar toch krachtige gebruikersinterface voor het maken en beheren van formulieren, documenten, thema&#39;s, letters, documentfragmenten, gegevenswoordenboeken en verwante elementen. Het helpt de volledige levenscyclus van formulieren, documenten en gerelateerde elementen te beheren - van de desktop van een ontwikkelaar tot de aanbieding
op een portalserver voor eindgebruikers. U kunt de AEM [!DNL Forms] gebruikersinterface gebruiken aan:

* Toegang tot AEM [!DNL Forms]-componenten
* Toegang AEM [!DNL Forms] configuraties

>[!NOTE]
>
>Voor gedetailleerde informatie over andere AEM hulpmiddelen en opties, zie [Authoring](/help/sites-authoring/author.md).

## Toegang tot AEM Forms-componenten {#access-aem-forms-components}

AEM biedt naast opties voor het maken van formulieren, documenten en gerelateerde elementen opties voor het maken van sites, elementen, het beheren van een AEM en meer. U kunt op het ![adobeexperienceManager](assets/adobeexperiencemanager.png)-logo van de Experience Manager klikken om naar alle beschikbare gereedschappen te navigeren. Samen met verbindingen aan de consoles van andere componenten, bevat het ook verbindingen voor AEM [!DNL Forms]. Als u naar AEM [!DNL Forms] wilt navigeren, klikt u op het Experience Manager-logo ![adobeexperienceManager](assets/adobeexperiencemanager.png) > navigatie ![kompas](assets/compass.png) > **[!UICONTROL Forms]**. Koppelingen van de volgende consoles worden weergegeven:

* Forms &amp; Documenten
* Thema&#39;s
* Letters
* Documentfragmenten
* Gegevenswoordenboeken

   ![AEM Forms Console](assets/aem_forms_console_new.png)

### Forms &amp; Documents {#forms-documents}

Forms &amp; Documents biedt opties voor het maken van interactieve communicatie, adaptief formulier, adaptief formulierfragment en formulierset. Alleen voor AEM [!DNL Forms] in JEE biedt Forms en Documenten een optie voor het importeren van bestanden uit lokale opslag en het synchroniseren van AEM [!DNL Forms]-middelen met Workbench.

De knop Maken is het beginpunt van het proces voor het maken of uploaden van AEM [!DNL Forms]. U hebt de volgende opties:

* **Interactieve communicatie**: Een interactieve communicatie is een gepersonaliseerde, interactieve, en apparaat-vriendelijke digitale correspondentie op HTML-Gebaseerde verklaring, of document. De interactieve Mededelingen zijn ontvankelijk in aard en veranderingslay-out en ontwerp automatisch gebaseerd op gebruikersapparaat en montages. Voor gedetailleerde informatie, zie [Interactief Communicatie Overzicht](/help/forms/using/interactive-communications-overview.md)

* **Adaptief formulier:** Een adaptief formulier is een aantrekkelijke en responsieve vorm. U kunt een adaptief formulier ontwerpen om het dynamisch aan te passen aan de invoer van de gebruiker door formuliersecties toe te voegen of te verwijderen op basis van gebruikersreactie, apparaat of werkomgeving. Het artikel [Inleiding tot het ontwerpen van adaptieve formulieren](../../forms/using/introduction-forms-authoring.md) biedt gedetailleerde informatie over de adaptieve formulieren.

* **Adaptief formulierfragment:** Hoewel elk formulier is ontworpen voor een bepaald doel, zijn er in de meeste vormen enkele gangbare segmenten, zoals het opgeven van persoonlijke gegevens zoals naam en adres, familiedetails, inkomstengegevens enzovoort. U kunt voor dergelijke secties een afzonderlijk element maken. Deze herbruikbare, zelfstandige segmenten worden adaptieve formulierfragmenten genoemd. Zie [artikel Adaptieve formulierfragmenten](../../forms/using/adaptive-form-fragments.md) voor meer informatie.

* **Formulierset:** Een formulierset is een verzameling HTML5-formulieren die zijn gegroepeerd en worden weergegeven als één set formulieren voor eindgebruikers. Wanneer eindgebruikers een formulierset beginnen in te vullen, worden de formulieren naadloos van het ene naar het andere formulier overgebracht. Uiteindelijk kan een gebruiker alle formulieren als één entiteit met één klik verzenden. Zie [Formulier ingesteld in AEM Forms](../../forms/using/formset-in-aem-forms.md) voor meer informatie.

* **Map:** AEM  [!DNL Forms] gebruikersinterface gebruikt mappen om elementen te rangschikken. Twee soorten mappen worden ondersteund:

   * **Algemene map:** deze mappen worden gebruikt voor elementen die in AEM  [!DNL Forms] gebruikersinterface zijn gemaakt. Deze mappen hebben geen strikte mapstructuur. U kunt de namen van submappen wijzigen, submappen maken en adaptieve formulieren, interactieve communicatie, adaptieve formulierfragmenten, formuliersjablonen (XDP&#39;s), PDF forms, documenten en gerelateerde elementen in deze mappen opslaan.
   * **Map Forms Workflow:** Forms-workflowmappen worden gemaakt wanneer Workbench-processen (LiveCycle-archieven) worden gemigreerd en gesynchroniseerd met AEM  [!DNL Forms] gebruikersinterface. Het is niet toegestaan de naam te wijzigen, een submap te maken, een interactieve communicatie, een adaptief formulierfragment of een interactieve communicatie te maken. Het is ook niet toegestaan om een versiemap te verwijderen of een adaptief formulier, een adaptief formulierfragment of een interactieve communicatie te maken en te uploaden parallel aan de versiemap.

   ![mappen](assets/folders.png)

   **A.** Algemene map  **B.** Forms Workflow

Het deelvenster Forms en het deelvenster Document bevatten ook opties voor:

* **Bestanden importeren van lokale opslag:** u kunt PDF forms en documenten, formuliersjablonen (XFA-formulieren) en andere bronnen (afbeeldings- en XML-schema voor XSD&#39;s) importeren. Zie [Elementen importeren en exporteren naar AEM Forms](../../forms/using/import-export-forms-templates.md) voor stapsgewijze instructies.
* **AEM Forms-middelen synchroniseren met Workbench:** u kunt de optie Bestanden van Workbench gebruiken om elementen te synchroniseren tussen de AEM Forms-gebruikersinterface en Workbench. Hiermee zorgt u ervoor dat alle middelen beschikbaar zijn in AEM [!DNL Forms] gebruikersinterface en selectie van crx-repository&#39;s van Workbench.

### Thema&#39;s {#themes}

Een thema bevat opmaakgegevens voor componenten en deelvensters. Thema&#39;s hebben een onafhankelijke identiteit. U kunt een thema dus opnieuw gebruiken op meerdere adaptieve formulieren. U kunt stijlen voor een component opgeven of CSS-eigenschappen wijzigen voor verschillende componenten die in de verschillende formulieren worden gebruikt. Stijlen omvatten eigenschappen zoals achtergrondkleuren, statuskleuren, transparantie en grootte. U kunt aanpassingen in een thema opslaan en deze als een voorinstelling op componenten van het formulier importeren. Wanneer u het thema aan uw formulier toevoegt, weerspiegelt de opgegeven stijl de corresponderende componenten van het formulier. Met AEM 6.2 [!DNL Forms] kunt u thema&#39;s maken en deze toepassen op uw formulieren.

Zie [Thema&#39;s in AEM Forms](../../forms/using/themes.md) voor informatie over het maken en gebruiken van thema&#39;s.

### Letters {#letters}

Een AEM [!DNL Forms] brief is veilige, gepersonaliseerde, en interactieve correspondentie. U kunt AEM [!DNL Forms] gebruiken om letters (ook wel correspondentie genoemd) van zowel vooraf goedgekeurde als aangepaste inhoud in een gestroomlijnd proces snel samen te stellen.

Zie [Letter maken](../../forms/using/create-letter.md) voor informatie over het maken en gebruiken van letters.

### Documentfragmenten {#document-fragments}

Documentfragmenten zijn herbruikbare onderdelen of onderdelen van een correspondentie waarmee u letters kunt samenstellen. De documentfragmenten zijn van het type tekst, lijst, voorwaarde en lay-outfragment. Zie [Documentfragmenten maken](/help/forms/using/document-fragments.md) voor informatie over het maken en gebruiken van documentfragmenten.

### Gegevenswoordenboeken {#data-dictionaries}

Zakelijke gebruikers hebben doorgaans geen kennis nodig van metagegevensrepresentaties zoals XSD (XML-schema) en Java-klassen. Nochtans, vereisen zij gewoonlijk toegang tot deze gegevensstructuren en attributen om oplossingen te bouwen. AEM [!DNL Forms] gebruikt gegevenswoordenboek dat bedrijfsgebruikers toelaat om informatie van achterste-eindgegevensbronnen te gebruiken zonder technische details over hun onderliggende gegevensmodellen te kennen.

Zie [gegevenswoordenboekartikel](../../forms/using/data-dictionary.md) maken voor informatie over het maken en gebruiken van gegevenswoordenboeken.

## Toegang tot AEM [!DNL Forms] Configuraties {#accessing-aem-forms-configurations}

AEM deelvenster Gereedschappen bevat gereedschappen voor diverse componenten. Als u naar AEM Forms-specifieke gereedschappen wilt navigeren, klikt u op het logo van de Experience Manager ![adobeexperienceManager](assets/adobeexperiencemanager.png) > ![hammer](assets/hammer.png) > **[!UICONTROL Forms]**. De hulpmiddelen om de volgende functies uit te voeren worden getoond:

* **Gecontroleerde map configureren:** een beheerder kan een netwerkmap, ook wel een gecontroleerde map genoemd, zo configureren dat wanneer een gebruiker een bestand (zoals een PDF-bestand) in de gecontroleerde map plaatst, een vooraf geconfigureerde bewerking wordt gestart en het bestand wordt gemanipuleerd. Zie [Een gecontroleerde map maken en configureren](/help/forms/using/creating-configure-watched-folder.md) voor gedetailleerde informatie.
* **Forms App Offline Service configureren:** de AEM  [!DNL Forms] app offline service plaatst de paden of URL&#39;s van de bronnen die in een formulier worden gebruikt in cache. Het in cache plaatsen van paden of URL&#39;s van de bronnen die in een formulier worden gebruikt, verbetert de prestaties op de server. Zie [Werken in de offlinemodus](/help/forms/using/work-offline-mode.md) om de offlinecomponent van de AEM Forms-app aan de serverzijde te configureren.

   ![AEM Forms-gereedschappen](assets/aem_forms_tools_new.png)

* **PDF-generator configureren:** een beheerder kan instellingen voor AEM  [!DNL Forms] PDF-generator configureren, gebruikersaccounts toevoegen en configuratie importeren of exporteren naar de PDF-Generator.
* **Correspondence Management Assets publiceren:** AEM  [!DNL Forms] kunt u alle letters, documentfragmenten en gegevenswoordenboeken en gerelateerde afhankelijkheden van een auteur tegelijk publiceren. De gepubliceerde activa omvatten alle activa van het Beheer van de Correspondentie en verwante gebiedsdelen. Zie [Formulieren en documenten publiceren en verwijderen](../../forms/using/publishing-unpublishing-forms.md#publishallthecorrespondencemanagementassets) voor meer informatie.
* **Correspondence Management Assets exporteren:** u kunt alle Correspondence Management-elementen en gerelateerde afhankelijkheden als een pakket downloaden van een AEM  [!DNL Forms] instantie. Zie [Elementen importeren en exporteren naar AEM Forms](../../forms/using/import-export-forms-templates.md#importandexportassetsincorrespondencemanagement) voor gedetailleerde stappen

## Gemeenschappelijke elementen van gebruikersinterface {#commonelements}

* **Linkerrails:** U kunt op het pictogram Linkerrails klikken  ![](assets/railleftpng.png) om de tijdlijn- en referentiemogelijkheden van AEM zichtbaar te maken  [!DNL Forms].

   * **Tijdlijn:** u kunt opmerkingen toevoegen en weergeven over een element dat beschikbaar is voor revisie in de tijdlijn. Zie [Revisies voor elementen in formulieren maken en beheren](../../forms/using/create-reviews-forms.md) voor gedetailleerde instructies.
   * **Referenties:** Een AEM  [!DNL Forms] element kan in meerdere AEM  [!DNL Forms] elementen worden gebruikt. Een documentfragment kan bijvoorbeeld in meerdere letters worden gebruikt. Verwijzingen zijn een lijst met elementen (andere vormen of bronnen) waarin het geselecteerde element wordt gebruikt en ook de lijst met andere elementen die het geselecteerde element gebruikt.

* **Broodkruimels:** Een broodkruimel vertegenwoordigt de titel van de huidige console of omslag. U kunt op de optie Breadcrumb klikken om te navigeren tussen het niveau van mappen dat hoger is in de hiërarchie.
* **Weergaveswitcher:** u kunt op de  ![](assets/viewlist.png) viewlist of  ![](assets/viewcard.png) viewcard van het pictogram Weergaveswitter klikken om snel tussen de lijst- en kaartweergave te schakelen. Voor meer informatie over gemeenschappelijke gebruikersinterfacecomponenten, zie [Authoring](/help/sites-authoring/author.md).
* **Zoeken:met** de zoekoptie kunt u  ![](assets/search.png) zoeken naar inhoud en gereedschappen die u nodig hebt. Typ de naam van de inhoud of het productvermogen en selecteer een van de suggesties, bijvoorbeeld, type &quot;Documenten&quot;om snel **[!UICONTROL Forms & Documents]** of de console van de Fragments van het Document te vinden en te navigeren. Voor meer informatie over onderzoek, zie AEM 6.2 [search](/help/sites-authoring/search.md) artikel

* **Werkbalk** Handelingen: Als u een element selecteert, verschijnt de werkbalk Handelingen boven de lijst met elementen. Het bevat alle beheerhulpmiddelen voor het geselecteerde element. U kunt de muisaanwijzer boven een gereedschapspictogram plaatsen om de knopinfo met een beschrijving van de functionaliteit weer te geven

>[!NOTE]
>
>Wanneer een gebruiker een onderzoek uitvoert om het even welke console van Forms &amp; Documenten, dan bevat het spoor slechts **Filters &amp; Opties**. U kunt Filters en Opties gebruiken om geavanceerd zoeken uit te voeren.

* **Werkbalk** Handelingen: Als u een element selecteert, verschijnt de werkbalk Handelingen boven de lijst met elementen. Het bevat alle beheerhulpmiddelen voor het geselecteerde element. U kunt de muisaanwijzer boven een gereedschapspictogram plaatsen om de knopinfo met een beschrijving van de functionaliteit weer te geven

   ![Werkbalk voor acties voor een adaptief formulier](assets/action_toolbar_new.png)

   Werkbalk voor acties voor een adaptief formulier
