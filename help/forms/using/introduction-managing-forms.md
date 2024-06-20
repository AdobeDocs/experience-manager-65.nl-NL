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

AEM [!DNL Forms] biedt een vereenvoudigde maar toch krachtige gebruikersinterface voor het maken en beheren van formulieren, documenten, thema&#39;s, letters, documentfragmenten, gegevenswoordenboeken en verwante elementen. Hiermee kunt u de volledige levenscyclus van formulieren, documenten en gerelateerde elementen beheren - van de desktop van een ontwikkelaar tot het aanbieden ervan op een portalserver voor eindgebruikers. U kunt de AEM gebruiken [!DNL Forms] gebruikersinterface naar:

* AEM [!DNL Forms] componenten
* AEM [!DNL Forms] configuraties

>[!NOTE]
>
>Zie voor meer informatie over andere AEM gereedschappen en opties [Authoring](/help/sites-authoring/author.md).

## AEM Forms-componenten openen {#access-aem-forms-components}

AEM biedt naast opties voor het maken van formulieren, documenten en gerelateerde elementen opties voor het maken van sites, elementen, het beheren van een AEM en meer. U kunt op de knop ![adobeexperienceManager](assets/adobeexperiencemanager.png) Het logo van de Experience Manager om naar alle beschikbare gereedschappen te navigeren. Het bevat naast koppelingen naar de consoles van andere componenten ook koppelingen voor AEM [!DNL Forms]. Ga naar AEM [!DNL Forms]klikt u op het logo van de Experience Manager ![adobeexperienceManager](assets/adobeexperiencemanager.png) > Navigatie ![kompas](assets/compass.png) > **[!UICONTROL Forms]**. Koppelingen van de volgende consoles worden weergegeven:

* Forms &amp; Documenten
* Thema&#39;s
* Letters
* Documentfragmenten
* Gegevenswoordenboeken

  ![AEM Forms Console](assets/aem_forms_console_new.png)

### Forms &amp; Documenten  {#forms-documents}

Forms &amp; Documents biedt opties voor het maken van interactieve communicatie, adaptief formulier, adaptief formulierfragment en formulierset. Alleen voor AEM [!DNL Forms] in JEE biedt Forms &amp; Documents een optie om bestanden te importeren van lokale opslag en AEM te synchroniseren [!DNL Forms] middelen met Workbench.

De knop Maken is het beginpunt van het maken of uploaden van AEM [!DNL Forms] activa. U hebt de volgende opties om te maken:

* **Interactieve communicatie**: Een interactieve communicatie is een gepersonaliseerde, interactieve en apparaatvriendelijke digitale HTML-correspondentie, -instructie of -document. De interactieve Mededelingen zijn ontvankelijk in aard en veranderingslay-out en ontwerp automatisch gebaseerd op gebruikersapparaat en montages. Zie voor meer informatie [Interactieve communicatie - overzicht](/help/forms/using/interactive-communications-overview.md)

* **Adaptief formulier:** Een adaptief formulier is een aantrekkelijke en responsieve vorm. U kunt een adaptief formulier ontwerpen om het dynamisch aan te passen aan de invoer van de gebruiker door formuliersecties toe te voegen of te verwijderen op basis van gebruikersreactie, apparaat of werkomgeving. De [Inleiding tot het ontwerpen van adaptieve formulieren](../../forms/using/introduction-forms-authoring.md) artikel bevat gedetailleerde informatie over de adaptieve formulieren .

* **Adaptief formulierfragment:** Hoewel elk formulier voor een bepaald doel is ontworpen, zijn er in de meeste vormen enkele gangbare segmenten, zoals het verstrekken van persoonlijke gegevens zoals naam en adres, familiedetails, inkomstengegevens enzovoort. U kunt voor dergelijke secties een afzonderlijk element maken. Deze herbruikbare, zelfstandige segmenten worden adaptieve formulierfragmenten genoemd. Zie voor meer informatie [adaptieve formulierfragmenten](../../forms/using/adaptive-form-fragments.md) artikel.

* **Formulierset:** Een formulierset is een verzameling HTML5-formulieren die zijn gegroepeerd en worden weergegeven als één set formulieren voor eindgebruikers. Wanneer eindgebruikers een formulierset beginnen in te vullen, worden de formulieren naadloos van het ene naar het andere formulier overgebracht. Uiteindelijk kan een gebruiker alle formulieren als één entiteit met één klik verzenden. Zie voor meer informatie [Formulierset in AEM Forms](../../forms/using/formset-in-aem-forms.md).

* **Map:** AEM [!DNL Forms] gebruikersinterface gebruikt mappen om elementen te rangschikken. Er worden twee soorten mappen ondersteund:

   * **Algemene map:** Deze mappen worden gebruikt voor elementen die zijn gemaakt in AEM [!DNL Forms] gebruikersinterface. Deze mappen hebben geen strikte mapstructuur. U kunt de namen van submappen wijzigen, submappen maken en adaptieve formulieren, interactieve communicatie, adaptieve formulierfragmenten, formuliersjablonen (XDP&#39;s), PDF forms, documenten en gerelateerde elementen in deze mappen opslaan.
   * **Map Forms Workflow:** Forms-workflowmappen worden gemaakt wanneer Workbench-processen (archiefbestanden voor LiveCycles) worden gemigreerd en gesynchroniseerd met AEM [!DNL Forms] gebruikersinterface. U mag de naam niet wijzigen, geen submap maken, een interactieve communicatie, een adaptief formulierfragment of een interactieve communicatie maken. Het is ook niet toegestaan om een versiemap te verwijderen of een adaptief formulier, een adaptief formulierfragment of een interactieve communicatie te maken en te uploaden parallel aan de versiemap.

  ![mappen](assets/folders.png)

  **A.** Algemene map **B.** Map Forms Workflow

Het deelvenster Forms en het deelvenster Document bevatten ook opties voor:

* **Bestanden importeren van lokale opslag:** U kunt PDF forms en documenten, formuliersjablonen (XFA-formulieren) en andere bronnen (Afbeelding en XML-schema voor XSD&#39;s) importeren. Zie voor stapsgewijze instructies [Elementen importeren en exporteren naar AEM Forms](../../forms/using/import-export-forms-templates.md).
* **AEM Forms-middelen synchroniseren met Workbench:** Met de optie Bestanden van Workbench kunt u elementen synchroniseren tussen de AEM Forms-gebruikersinterface en Workbench. Het zorgt ervoor dat alle activa in AEM beschikbaar zijn [!DNL Forms] gebruikersinterface en selectie van crx-repository&#39;s van Workbench.

### Thema&#39;s  {#themes}

Een thema bevat opmaakgegevens voor componenten en deelvensters. Thema&#39;s hebben een onafhankelijke identiteit. U kunt een thema dus opnieuw gebruiken op meerdere adaptieve formulieren. U kunt stijlen voor een component opgeven of CSS-eigenschappen wijzigen voor verschillende componenten die in de verschillende formulieren worden gebruikt. Stijlen omvatten eigenschappen zoals achtergrondkleuren, statuskleuren, transparantie en grootte. U kunt aanpassingen in een thema opslaan en deze als een voorinstelling op componenten van het formulier importeren. Wanneer u het thema aan uw formulier toevoegt, weerspiegelt de opgegeven stijl de corresponderende componenten van het formulier. Met AEM 6.2 [!DNL Forms]kunt u thema&#39;s maken en deze toepassen op uw formulieren.

Zie voor informatie over het maken en gebruiken van thema&#39;s [Thema&#39;s in AEM Forms](../../forms/using/themes.md).

### Letters  {#letters}

Een AEM [!DNL Forms] letter is een veilige, persoonlijke en interactieve correspondentie. U kunt AEM [!DNL Forms] om in een gestroomlijnd proces snel letters (ook wel correspondentie genoemd) samen te stellen op basis van zowel vooraf goedgekeurde als aangepaste inhoud.

Zie voor informatie over het maken en gebruiken van letters [Letter maken](../../forms/using/create-letter.md).

### Documentfragmenten {#document-fragments}

Documentfragmenten zijn herbruikbare onderdelen of onderdelen van een correspondentie waarmee u letters kunt samenstellen. De documentfragmenten zijn van het type tekst, lijst, voorwaarde en lay-outfragment. Zie voor informatie over het maken en gebruiken van documentfragmenten [maken, documentfragmenten](/help/forms/using/document-fragments.md).

### Gegevenswoordenboeken {#data-dictionaries}

Zakelijke gebruikers hebben doorgaans geen kennis nodig van metagegevensrepresentaties zoals XSD (XML-schema) en Java-klassen. Nochtans, vereisen zij gewoonlijk toegang tot deze gegevensstructuren en attributen om oplossingen te bouwen. AEM [!DNL Forms] gebruikt gegevenswoordenboek dat bedrijfsgebruikers toelaat om informatie van achterste-eindgegevensbronnen te gebruiken zonder technische details over hun onderliggende gegevensmodellen te kennen.

Voor informatie over het creëren van en het gebruiken van gegevenswoordenboeken, zie het creëren [gegevenswoordenboekartikel](../../forms/using/data-dictionary.md)

## Toegang tot AEM [!DNL Forms] Configuraties {#accessing-aem-forms-configurations}

AEM deelvenster Gereedschappen bevat gereedschappen voor diverse componenten. Om naar AEM Forms-specifieke hulpmiddelen te navigeren, klik het embleem van de Experience Manager ![adobeexperienceManager](assets/adobeexperiencemanager.png) > Gereedschappen ![hamer](assets/hammer.png) > **[!UICONTROL Forms]**. De hulpmiddelen om de volgende functies uit te voeren worden getoond:

* **Controlemap configureren:** Een beheerder kan een netwerkmap, ook wel een gecontroleerde map genoemd, zo configureren dat wanneer een gebruiker een bestand (zoals een PDF-bestand) in de gecontroleerde map plaatst, een vooraf geconfigureerde bewerking wordt gestart en het bestand wordt gemanipuleerd. Zie voor meer informatie [Een gecontroleerde map maken en configureren](/help/forms/using/creating-configure-watched-folder.md).
* **Forms App Offline Service configureren:** De AEM [!DNL Forms] de app offline service plaatst de paden of URL&#39;s van de bronnen die in een formulier worden gebruikt in cache. Het in cache plaatsen van paden of URL&#39;s van de bronnen die in een formulier worden gebruikt, verbetert de prestaties op de server. Als u de offline servercomponent van de AEM Forms-app wilt configureren, raadpleegt u [Werken in de offlinemodus](/help/forms/using/work-offline-mode.md).

  ![AEM Forms-gereedschappen](assets/aem_forms_tools_new.png)

* **PDF Generator configureren:** Een beheerder kan AEM configureren [!DNL Forms] De montages van de PDF Generator, voegen gebruikersrekeningen toe, en de invoer of de uitvoerconfiguratie aan de PDF Generator.
* **Correspondentiebeheermiddelen publiceren:** AEM [!DNL Forms] Hiermee kunt u alle letters, documentfragmenten en gegevenswoordenboeken en verwante afhankelijkheden van een auteur tegelijk publiceren. De gepubliceerde activa omvatten alle activa van het Beheer van de Correspondentie en verwante gebiedsdelen. Zie voor meer informatie [Formulieren en documenten publiceren en de publicatie ervan opheffen](../../forms/using/publishing-unpublishing-forms.md#publishallthecorrespondencemanagementassets).
* **Correspondentenbeheermiddelen exporteren:** U kunt alle Correspondentenbeheermiddelen en gerelateerde afhankelijkheden als een pakket downloaden van een AEM [!DNL Forms] -instantie. Zie voor meer informatie [Elementen importeren en exporteren naar AEM Forms](../../forms/using/import-export-forms-templates.md#importandexportassetsincorrespondencemanagement)

## Algemene elementen van de gebruikersinterface {#commonelements}

* **Linkerspoor:** U kunt op het pictogram van het linkerspoor klikken ![railleftpng](assets/railleftpng.png) om de mogelijkheden van AEM voor tijdlijn en verwijzingen weer te geven [!DNL Forms].

   * **Tijdlijn:** U kunt opmerkingen toevoegen aan en weergeven over een element dat beschikbaar is voor revisie in de tijdlijn. Zie voor gedetailleerde instructies [Revisies voor elementen in formulieren maken en beheren](../../forms/using/create-reviews-forms.md).
   * **Referenties:** Een AEM [!DNL Forms] element kan in meerdere AEM worden gebruikt [!DNL Forms] activa. Een documentfragment kan bijvoorbeeld in meerdere letters worden gebruikt. Verwijzingen zijn een lijst met elementen (andere vormen of bronnen) waarin het geselecteerde element wordt gebruikt en ook de lijst met andere elementen die het geselecteerde element gebruikt.

* **Broodkruimels:** Een broodkruimel vertegenwoordigt de titel van de huidige console of de omslag. U kunt op de optie Breadcrumb klikken om te navigeren tussen het niveau van mappen dat hoger is in de hiërarchie.
* **Weergaveswitcher:** U kunt klikken op het pictogram Weergaveswitcher ![weergaveoverzicht](assets/viewlist.png) of ![viewcard](assets/viewcard.png) om snel tussen lijst en kaartmening te schakelen. Voor meer informatie over gemeenschappelijke gebruikersinterfacecomponenten, zie [Authoring](/help/sites-authoring/author.md).
* **Zoeken:** De zoekoptie ![zoeken](assets/search.png) biedt mogelijkheden om snel naar de gewenste inhoud en gereedschappen te zoeken en deze te gebruiken. Typ de naam van de inhoud of de productmogelijkheden en selecteer een van de suggesties. Typ bijvoorbeeld &quot;Documenten&quot; om snel te zoeken en naar **[!UICONTROL Forms & Documents]** of de Document Fragments console. Zie AEM 6.2 voor meer informatie over zoeken. [zoeken](/help/sites-authoring/search.md) artikel

* **Werkbalk Handelingen**: Als u een element selecteert, wordt de werkbalk Handelingen boven de lijst met elementen weergegeven. Het bevat alle beheerhulpmiddelen voor het geselecteerde element. U kunt de muisaanwijzer boven een gereedschapspictogram plaatsen om de knopinfo met een beschrijving van de functionaliteit weer te geven

>[!NOTE]
>
>Wanneer een gebruiker een zoekconsole van Forms &amp; Documents uitvoert, bevat de rail alleen **Filters en opties**. U kunt Filters en Opties gebruiken om geavanceerd zoeken uit te voeren.

* **Werkbalk Handelingen**: Als u een element selecteert, wordt de werkbalk Handelingen boven de lijst met elementen weergegeven. Het bevat alle beheerhulpmiddelen voor het geselecteerde element. U kunt de muisaanwijzer boven een gereedschapspictogram plaatsen om de knopinfo met een beschrijving van de functionaliteit weer te geven

  ![Werkbalk voor acties voor een adaptief formulier](assets/action_toolbar_new.png)

  Werkbalk voor acties voor een adaptief formulier
