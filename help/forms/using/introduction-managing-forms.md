---
title: Inleiding tot het beheren van formulieren
description: AEM Forms biedt tools voor het beheer van Adaptive Forms en gerelateerde middelen. In dit artikel wordt uitgelegd wat de belangrijkste mogelijkheden voor formulierbeheer en gebruikersinterface-elementen zijn.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-manager, introduction
docset: aem65
exl-id: 3e063456-7f96-483d-86a3-6a414746db8a
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: Admin, User
source-git-commit: e821be5233fd5f6688507096790d219d25903892
workflow-type: tm+mt
source-wordcount: '1562'
ht-degree: 0%

---

# Inleiding tot het beheren van formulieren {#introduction-to-managing-forms}

AEM [!DNL Forms] biedt een vereenvoudigde maar toch krachtige gebruikersinterface voor het maken en beheren van formulieren, documenten, thema&#39;s, letters, documentfragmenten, gegevenswoordenboeken en verwante elementen. Het helpt de volledige levenscyclus van formulieren, documenten en gerelateerde elementen te beheren - van de desktop van een ontwikkelaar tot de aanbieding
op een portalserver voor eindgebruikers. U kunt de AEM [!DNL Forms] -gebruikersinterface gebruiken voor:

* Toegang tot AEM [!DNL Forms] -componenten
* Toegang tot AEM [!DNL Forms] configuraties

>[!NOTE]
>
>Voor gedetailleerde informatie over andere AEM hulpmiddelen en opties, zie [&#x200B; Authoring &#x200B;](/help/sites-authoring/author.md).

## AEM Forms-componenten openen {#access-aem-forms-components}

AEM biedt naast opties voor het maken van formulieren, documenten en gerelateerde elementen opties voor het maken van sites, elementen, het beheren van een AEM en meer. U kunt het ![&#x200B; adobeexperienceManager &#x200B;](assets/adobeexperiencemanager.png) embleem van de Experience Manager klikken om aan alle beschikbare hulpmiddelen te navigeren. Het bevat naast koppelingen naar de consoles van andere componenten ook koppelingen voor AEM [!DNL Forms] . Om aan AEM [!DNL Forms] te navigeren, klik het embleem van de Experience Manager ![&#x200B; adobeexperienceManager &#x200B;](assets/adobeexperiencemanager.png) > navigatie ![&#x200B; kompas &#x200B;](assets/compass.png) > **[!UICONTROL Forms]**. Koppelingen van de volgende consoles worden weergegeven:

* Forms &amp; Documenten
* Thema&#39;s
* Letters
* Documentfragmenten
* Gegevenswoordenboeken

  ![&#x200B; AEM Forms Console &#x200B;](assets/aem_forms_console_new.png)

### Forms &amp; Documenten  {#forms-documents}

Forms &amp; Documents biedt opties voor het maken van interactieve communicatie, adaptief formulier, adaptief formulierfragment en formulierset. Alleen voor AEM [!DNL Forms] in JEE biedt Forms en Documenten een optie om bestanden te importeren van lokale opslag en AEM [!DNL Forms] -elementen te synchroniseren met Workbench.

De knop Maken is het beginpunt van het maken of uploaden van AEM [!DNL Forms] -element. U hebt de volgende opties om te maken:

* **Interactieve Mededeling**: Een Interactieve Mededeling is gepersonaliseerde, interactieve, en apparaat vriendschappelijke digitale HTML correspondentie, verklaring, of document. De interactieve Mededelingen zijn ontvankelijk in aard en veranderingslay-out en ontwerp automatisch gebaseerd op gebruikersapparaat en montages. Voor gedetailleerde informatie, zie [&#x200B; Interactief Communicatie Overzicht &#x200B;](/help/forms/using/interactive-communications-overview.md)

* **Aangepaste vorm:** een adaptieve vorm is een aansprekende en ontvankelijke vorm. U kunt een adaptief formulier ontwerpen om het dynamisch aan te passen aan de invoer van de gebruiker door formuliersecties toe te voegen of te verwijderen op basis van gebruikersreactie, apparaat of werkomgeving. De [&#x200B; Inleiding aan auteursadaptieve vormen &#x200B;](../../forms/using/introduction-forms-authoring.md) artikel verstrekt gedetailleerde informatie over de adaptieve vormen.

* **Aangepast vormfragment:** Terwijl elke vorm voor een specifiek doel wordt ontworpen, zijn er sommige gemeenschappelijke segmenten in de meeste vormen, zoals om persoonlijke details zoals naam en adres, familiedetails, inkomensdetails, etc. te verstrekken. U kunt voor dergelijke secties een afzonderlijk element maken. Deze herbruikbare, zelfstandige segmenten worden adaptieve formulierfragmenten genoemd. Voor gedetailleerde informatie, zie [&#x200B; adaptieve vormfragmenten &#x200B;](../../forms/using/adaptive-form-fragments.md) artikel.

* **Reeks van de Vorm:** A vormreeks is een inzameling van HTML5 vormen gegroepeerd en voorgesteld als één enkele reeks vormen aan eind - gebruikers. Wanneer eindgebruikers een formulierset beginnen in te vullen, worden de formulieren naadloos van het ene naar het andere formulier overgebracht. Uiteindelijk kan een gebruiker alle formulieren als één entiteit met één klik verzenden. Voor gedetailleerde informatie, zie [&#x200B; Vorm die in AEM Forms &#x200B;](../../forms/using/formset-in-aem-forms.md) wordt geplaatst.

* **Omslag:** AEM [!DNL Forms] gebruikersinterface gebruikt omslagen om activa te schikken. Er worden twee soorten mappen ondersteund:

   * **Algemene Omslag:** Deze omslagen worden gebruikt voor activa die binnen AEM [!DNL Forms] gebruikersinterface worden gecreeerd. Deze mappen hebben geen strikte mapstructuur. U kunt de namen van submappen wijzigen, submappen maken en adaptieve formulieren, interactieve communicatie, adaptieve formulierfragmenten, formuliersjablonen (XDP&#39;s), PDF forms, documenten en gerelateerde elementen in deze mappen opslaan.
   * **omslag van de Forms Workflow:** de werkschemamappen van Forms worden gecreeerd wanneer de processen Workbench (de archieven van het LiveCycle) met AEM [!DNL Forms] gebruikersinterface worden gemigreerd en gesynchroniseerd. U mag de naam niet wijzigen, geen submap maken, een interactieve communicatie, een adaptief formulierfragment of een interactieve communicatie maken. Het is ook niet toegestaan om een versiemap te verwijderen of een adaptief formulier, een adaptief formulierfragment of een interactieve communicatie te maken en te uploaden parallel aan de versiemap.

  ![&#x200B; omslagen &#x200B;](assets/folders.png)

  **A.** Algemene omslag **B.** de omslag van de Forms Workflow

Het deelvenster Forms en het deelvenster Document bevatten ook opties voor:

* **de dossiers van de Invoer van lokale opslag:** u kunt PDF forms &amp; Documenten, de malplaatjes van de Vorm (vormen XFA), en andere middel (Beeld en schema van XML voor XSDs) invoeren. Voor geleidelijke instructies, zie [&#x200B; het Invoeren van en het uitvoeren van activa naar AEM Forms &#x200B;](../../forms/using/import-export-forms-templates.md).
* **de activa van de Synchronisatie AEM Forms met Workbench:** u kunt de Dossiers van Workbench optie gebruiken om activa tussen het gebruikersinterface van AEM Forms en Workbench te synchroniseren. Hiermee zorgt u ervoor dat alle middelen beschikbaar zijn in AEM gebruikersinterface van [!DNL Forms] en de selectie van de crx-repository-elementen van Workbench.

### Thema&#39;s  {#themes}

Een thema bevat opmaakgegevens voor componenten en deelvensters. Thema&#39;s hebben een onafhankelijke identiteit. U kunt een thema dus opnieuw gebruiken op meerdere adaptieve formulieren. U kunt stijlen voor een component opgeven of CSS-eigenschappen wijzigen voor verschillende componenten die in de verschillende formulieren worden gebruikt. Stijlen omvatten eigenschappen zoals achtergrondkleuren, statuskleuren, transparantie en grootte. U kunt aanpassingen in een thema opslaan en deze als een voorinstelling op componenten van het formulier importeren. Wanneer u het thema aan uw formulier toevoegt, weerspiegelt de opgegeven stijl de corresponderende componenten van het formulier. Met AEM 6.2 [!DNL Forms] kunt u thema&#39;s maken en deze toepassen op uw formulieren.

Voor informatie over het creëren van en het gebruiken van thema&#39;s, zie [&#x200B; Thema&#39;s in AEM Forms &#x200B;](../../forms/using/themes.md).

### Letters  {#letters}

Een AEM [!DNL Forms] -brief is een veilige, gepersonaliseerde en interactieve correspondentie. U kunt AEM [!DNL Forms] gebruiken om snel letters (ook wel correspondentie genoemd) samen te stellen van zowel vooraf goedgekeurde als door u geschreven inhoud in een gestroomlijnd proces.

Voor informatie over het creëren van en het gebruiken van brieven, zie [&#x200B; Brief &#x200B;](../../forms/using/create-letter.md) creëren.

### Documentfragmenten {#document-fragments}

Documentfragmenten zijn herbruikbare onderdelen of onderdelen van een correspondentie waarmee u letters kunt samenstellen. De documentfragmenten zijn van het type tekst, lijst, voorwaarde en lay-outfragment. Voor informatie over het creëren van en het gebruiken van documentfragmenten, zie [&#x200B; creërend documentfragmenten &#x200B;](/help/forms/using/document-fragments.md).

### Gegevenswoordenboeken {#data-dictionaries}

Zakelijke gebruikers hebben doorgaans geen kennis nodig van metagegevensrepresentaties zoals XSD (XML-schema) en Java-klassen. Nochtans, vereisen zij gewoonlijk toegang tot deze gegevensstructuren en attributen om oplossingen te bouwen. AEM [!DNL Forms] gebruikt gegevenswoordenboek waarmee zakelijke gebruikers informatie uit back-end gegevensbronnen kunnen gebruiken zonder technische details over de onderliggende gegevensmodellen te kennen.

Voor informatie over het creëren van en het gebruiken van gegevenswoordenboeken, zie het creëren van [&#x200B; artikel van het gegevenswoordenboek &#x200B;](../../forms/using/data-dictionary.md)

## Toegang tot AEM [!DNL Forms] configuraties {#accessing-aem-forms-configurations}

AEM deelvenster Gereedschappen bevat gereedschappen voor diverse componenten. Om aan AEM Forms-Specifieke hulpmiddelen te navigeren, klik het embleem van de Experience Manager ![&#x200B; adobeexperienceManager &#x200B;](assets/adobeexperiencemanager.png) > hulpmiddelen ![&#x200B; hamer &#x200B;](assets/hammer.png) > **[!UICONTROL Forms]**. De hulpmiddelen om de volgende functies uit te voeren worden getoond:

* **vorm Gecontroleerde Omslag:** een beheerder kan een netwerkomslag vormen, die als gecontroleerde omslag wordt bekend, zodat wanneer een gebruiker een dossier (zoals een dossier van PDF) in de gelete op omslag plaatst, een pre-gevormde verrichting is begonnen en het dossier manipuleert. Voor gedetailleerde informatie, zie [&#x200B; creëren en vormen een gelete op omslag &#x200B;](/help/forms/using/creating-configure-watched-folder.md).
* **vorm Forms App Offline Dienst:** de AEM [!DNL Forms] app offline dienst geheime voorgeheugens de wegen of URLs van de middelen die in een vorm worden gebruikt. Het in cache plaatsen van paden of URL&#39;s van de bronnen die in een formulier worden gebruikt, verbetert de prestaties op de server. Om de server-kant off-line component van AEM Forms te vormen app, zie [&#x200B; Werkend op de off-line wijze &#x200B;](/help/forms/using/work-offline-mode.md).

  ![&#x200B; de hulpmiddelen van AEM Forms &#x200B;](assets/aem_forms_tools_new.png)

* **vormt PDF Generator:** een beheerder kan AEM [!DNL Forms] montages van de PDF Generator vormen, gebruikersrekeningen toevoegen, en invoer of de uitvoerconfiguratie aan de PDF Generator invoeren.
* **Publish Correspondence Management Assets:** AEM [!DNL Forms] laat u alle Brieven, de Fragmenten van het Document, en de Woordenboeken van Gegevens en verwante gebiedsdelen van een auteursinstantie tegelijkertijd publiceren. De gepubliceerde activa omvatten alle activa van het Beheer van de Correspondentie en verwante gebiedsdelen. Voor gedetailleerde informatie, zie [&#x200B; het Publiceren en het unpublishing vormen &amp; documenten &#x200B;](../../forms/using/publishing-unpublishing-forms.md#publishallthecorrespondencemanagementassets).
* **het Beheer Assets van de Correspondentie van de Uitvoer:** u kunt alle activa van het Beheer van de Correspondentie en verwante gebiedsdelen als pakket van een AEM [!DNL Forms] instantie downloaden. Voor gedetailleerde stappen, zie [&#x200B; het Invoeren van en het uitvoeren van activa naar AEM Forms &#x200B;](../../forms/using/import-export-forms-templates.md#importandexportassetsincorrespondencemanagement)

## Algemene elementen van de gebruikersinterface {#commonelements}

* **Linkerspoor:** U kunt het linker spoorpictogram ![&#x200B; spoorstaaf &#x200B;](assets/railleftpng.png) klikken om Chronologie en mogelijkheden van Verwijzingen van AEM [!DNL Forms] te openbaren.

   * **Chronologie:** u kunt commentaar op activa toevoegen en bekijken die voor overzicht in de chronologie beschikbaar is. Voor gedetailleerde instructies, zie [&#x200B; Creërend en het leiden overzichten voor activa in vormen &#x200B;](../../forms/using/create-reviews-forms.md).
   * **Verwijzingen:** een AEM [!DNL Forms] activa kan in veelvoudige AEM [!DNL Forms] activa worden gebruikt. Een documentfragment kan bijvoorbeeld in meerdere letters worden gebruikt. Verwijzingen zijn een lijst met elementen (andere vormen of bronnen) waarin het geselecteerde element wordt gebruikt en ook de lijst met andere elementen die het geselecteerde element gebruikt.

* **Broodkruimels:** A Breadcrumb vertegenwoordigt de titel van de huidige console of de omslag. U kunt op de optie Breadcrumb klikken om te navigeren tussen het niveau van mappen dat hoger is in de hiërarchie.
* **Schakelaar van de Mening:** u kunt het pictogram van de Schakelaar van de Mening ![&#x200B; viewlist &#x200B;](assets/viewlist.png) of ![&#x200B; viewcard &#x200B;](assets/viewcard.png) klikken om tussen lijst en kaartmening snel te schakelen. Voor meer informatie over gemeenschappelijke gebruikersinterfacecomponenten, zie [&#x200B; Authoring &#x200B;](/help/sites-authoring/author.md).
* **Onderzoek:** het onderzoek van de onderzoeksoptie ![&#x200B; &#x200B;](assets/search.png) verstrekt vermogen om snel aan de inhoud en de hulpmiddelen te vinden en te springen u nodig hebt. Typ de naam van de inhoud of de productmogelijkheden en selecteer een van de suggesties. Typ bijvoorbeeld &quot;Documenten&quot; om snel naar **[!UICONTROL Forms & Documents]** of de Document Fragments Console te zoeken en ernaar te navigeren. Voor meer informatie over onderzoek, zie AEM 6.2 [&#x200B; onderzoek &#x200B;](/help/sites-authoring/search.md) artikel

* **toolbar van Acties**: Bij het selecteren van een activa, verschijnt de actiestoolbar boven de lijst van activa. Het bevat alle beheerhulpmiddelen voor het geselecteerde element. U kunt de muisaanwijzer boven een gereedschapspictogram plaatsen om de knopinfo met een beschrijving van de functionaliteit weer te geven

>[!NOTE]
>
>Wanneer een gebruiker een onderzoek uitvoert om het even welke console van Forms &amp; Documenten, dan bevat het spoor slechts **Filters &amp; Opties**. U kunt Filters en Opties gebruiken om geavanceerd zoeken uit te voeren.

* **toolbar van Acties**: Bij het selecteren van een activa, verschijnt de actiestoolbar boven de lijst van activa. Het bevat alle beheerhulpmiddelen voor het geselecteerde element. U kunt de muisaanwijzer boven een gereedschapspictogram plaatsen om de knopinfo met een beschrijving van de functionaliteit weer te geven

  ![&#x200B; toolbar van de Actie voor een adaptieve vorm &#x200B;](assets/action_toolbar_new.png)

  Werkbalk voor acties voor een adaptief formulier
