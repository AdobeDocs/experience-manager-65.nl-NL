---
title: Inleiding tot het beheren van formulieren
seo-title: Inleiding tot het beheren van formulieren
description: AEM Forms biedt hulpprogramma's voor het beheer van adaptieve formulieren en gerelateerde elementen. In dit artikel worden de belangrijkste mogelijkheden voor formulierbeheer en gebruikersinterface-elementen besproken.
seo-description: AEM Forms biedt hulpprogramma's voor het beheer van adaptieve formulieren en gerelateerde elementen. In dit artikel worden de belangrijkste mogelijkheden voor formulierbeheer en gebruikersinterface-elementen besproken.
uuid: 2275a0b6-b31e-4d8e-8154-ccdfff3705aa
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: introduction
discoiquuid: c0e4c9bb-e12a-4f9a-a8fa-1a8ad41d3995
docset: aem65
translation-type: tm+mt
source-git-commit: 8e724af4d69cb859537dd088119aaca652ea3931

---


# Inleiding tot het beheren van formulieren{#introduction-to-managing-forms}

AEM Forms biedt een vereenvoudigde maar toch krachtige gebruikersinterface voor het maken en beheren van formulieren, documenten, thema&#39;s, letters, documentfragmenten, gegevenswoordenboeken en verwante elementen. Hiermee kunt u de volledige levenscyclus van formulieren, documenten en gerelateerde elementen beheren - van de desktop van een ontwikkelaar tot de aanbieding ervan op een portalserver voor eindgebruikers. U kunt de gebruikersinterface van AEM-formulieren gebruiken voor:

* Toegang tot componenten van AEM-formulieren
* Toegang tot AEM Forms-configuraties

>[!NOTE]
>
>Zie [Authoring](/help/sites-authoring/author.md)voor gedetailleerde informatie over andere AEM-gereedschappen en -opties.

## Toegang tot componenten van AEM-formulieren {#access-aem-forms-components}

Naast opties voor het maken van formulieren, documenten en gerelateerde elementen biedt AEM opties voor het maken van sites, elementen, het beheren van een AEM-instantie en meer. U kunt op het logo van ![adobeexperience](assets/adobeexperiencemanager.png) Experience Manager klikken om naar alle beschikbare gereedschappen te navigeren. Het bevat naast koppelingen naar de consoles van andere componenten ook koppelingen voor AEM-formulieren. Als u naar AEM Forms wilt navigeren, klikt u op het logo Experience Manager ![adobeExperience Manager Manager](assets/adobeexperiencemanager.png) > ![Navigatiekompas](assets/compass.png) > Formulieren. Koppelingen van de volgende consoles worden weergegeven:

* Formulieren en documenten
* Thema&#39;s
* Letters
* Documentfragmenten
* Gegevenswoordenboeken

![AEM Forms Console](assets/aem_forms_console_new.png)

### Formulieren en documenten {#forms-documents}

Formulieren en documenten bieden opties voor het maken van een interactieve communicatie, een adaptief formulier, een adaptief formulierfragment en een formulierset. Alleen voor AEM Forms on JEE biedt Forms &amp; Documents een optie voor het importeren van bestanden van lokale opslag en het synchroniseren van AEM Forms-elementen met Workbench.

De knop Maken is het beginpunt voor het maken of uploaden van AEM Forms-elementen. U hebt de volgende opties:

* **Interactieve communicatie**: Een interactieve communicatie is een gepersonaliseerde, interactieve, en apparaat-vriendelijke digitale correspondentie op HTML-Gebaseerde verklaring, of document. De interactieve Mededelingen zijn ontvankelijk in aard en veranderingslay-out en ontwerp automatisch gebaseerd op gebruikersapparaat en montages. Voor gedetailleerde informatie, zie [Interactieve Communicatie Overzicht](/help/forms/using/interactive-communications-overview.md)

* **** Adaptief formulier: Een adaptief formulier is een aantrekkelijke en responsieve vorm. U kunt een adaptief formulier ontwerpen om het dynamisch aan te passen aan de invoer van de gebruiker door formuliersecties toe te voegen of te verwijderen op basis van gebruikersreactie, apparaat of werkomgeving. Het artikel [Inleiding tot het ontwerpen van adaptieve formulieren](../../forms/using/introduction-forms-authoring.md) bevat gedetailleerde informatie over de adaptieve formulieren.

* **** Adaptief formulierfragment:Hoewel elk formulier voor een bepaald doel is ontworpen, zijn er in de meeste vormen enkele gangbare segmenten, zoals het verstrekken van persoonlijke gegevens zoals naam en adres, familiedetails, inkomstengegevens enzovoort. U kunt voor dergelijke secties een afzonderlijk element maken. Deze herbruikbare, zelfstandige segmenten worden adaptieve formulierfragmenten genoemd. Zie het artikel over [adaptieve formulierfragmenten](../../forms/using/adaptive-form-fragments.md) voor meer informatie.

* **** Formulierset:Een formulierset is een verzameling HTML5-formulieren die zijn gegroepeerd en worden weergegeven als één set formulieren voor eindgebruikers. Wanneer eindgebruikers een formulierset beginnen in te vullen, worden de formulieren naadloos van het ene naar het andere formulier overgebracht. Uiteindelijk kan een gebruiker alle formulieren als één entiteit met één klik verzenden. Zie [Formulierset in AEM-formulieren](../../forms/using/formset-in-aem-forms.md)voor meer informatie.

* **** Map:In de gebruikersinterface van AEM Forms worden mappen gebruikt om elementen te rangschikken. Twee soorten mappen worden ondersteund:

   * **** Algemene map: Deze mappen worden gebruikt voor elementen die zijn gemaakt in de gebruikersinterface van AEM Forms. Deze mappen hebben geen strikte mapstructuur. U kunt de namen van submappen wijzigen, submappen maken en adaptieve formulieren, interactieve communicatie, adaptieve formulierfragmenten, formuliersjablonen (XDP&#39;s), PDF-formulieren, documenten en gerelateerde elementen in deze mappen opslaan.
   * **** Formulierwerkstroommap: Workflowmappen voor formulieren worden gemaakt wanneer Workbench-processen (LiveCycle-archieven) worden gemigreerd en gesynchroniseerd met de gebruikersinterface van AEM Forms. Het is niet toegestaan de naam te wijzigen, een submap te maken, een interactieve communicatie, een adaptief formulierfragment of een interactieve communicatie te maken. Het is ook niet toegestaan om een versiemap te verwijderen of een adaptief formulier, een adaptief formulierfragment of een interactieve communicatie te maken en te uploaden parallel aan de versiemap.

![mappen](assets/folders.png)

******A. Algemene map** B. Map Formulierwerkstroom

Het deelvenster Formulieren en Document bevat ook opties voor:

* **** Bestanden importeren van lokale opslag: U kunt PDF-formulieren en -documenten, formuliersjablonen (XFA-formulieren) en andere bronnen (afbeeldings- en XML-schema voor XSD&#39;s) importeren. Zie Elementen [importeren en exporteren naar AEM-formulieren](../../forms/using/import-export-forms-templates.md)voor stapsgewijze instructies.
* **** AEM Forms-middelen synchroniseren met Workbench: Met de optie Bestanden van Workbench kunt u elementen synchroniseren tussen de gebruikersinterface van AEM Forms en Workbench. Hiermee zorgt u ervoor dat alle elementen beschikbaar zijn in de gebruikersinterface van AEM Forms en de selectie van de crx-repository-elementen van Workbench.

### Thema&#39;s {#themes}

Een thema bevat opmaakgegevens voor componenten en deelvensters. Thema&#39;s hebben een onafhankelijke identiteit. U kunt een thema dus opnieuw gebruiken op meerdere adaptieve formulieren. U kunt stijlen voor een component opgeven of CSS-eigenschappen wijzigen voor verschillende componenten die in de verschillende formulieren worden gebruikt. Stijlen omvatten eigenschappen zoals achtergrondkleuren, statuskleuren, transparantie en grootte. U kunt aanpassingen in een thema opslaan en deze als een voorinstelling op componenten van het formulier importeren. Wanneer u het thema aan uw formulier toevoegt, weerspiegelt de opgegeven stijl de corresponderende componenten van het formulier. Met AEM 6.2-formulieren kunt u thema&#39;s maken en deze toepassen op uw formulieren.

Zie [Thema&#39;s in AEM-formulieren](../../forms/using/themes.md)voor informatie over het maken en gebruiken van thema&#39;s.

### Letters {#letters}

Een AEM-formulierbrief is een beveiligde, gepersonaliseerde en interactieve correspondentie. Met AEM Forms kunt u in een gestroomlijnd proces snel letters (ook wel correspondentie genoemd) samenstellen op basis van vooraf goedgekeurde en door u geschreven inhoud.

Zie Letter [maken voor informatie over het maken en gebruiken van letters](../../forms/using/create-letter.md).

### Documentfragmenten {#document-fragments}

Documentfragmenten zijn herbruikbare onderdelen of onderdelen van een correspondentie waarmee u letters kunt samenstellen. De documentfragmenten zijn van het type tekst, lijst, voorwaarde en lay-outfragment. Zie Documentfragmenten [maken voor informatie over het maken en gebruiken van documentfragmenten](/help/forms/using/document-fragments.md).

### Gegevenswoordenboeken {#data-dictionaries}

Zakelijke gebruikers hebben doorgaans geen kennis nodig van metagegevensrepresentaties zoals XSD (XML-schema) en Java-klassen. Nochtans, vereisen zij gewoonlijk toegang tot deze gegevensstructuren en attributen om oplossingen te bouwen. In AEM Forms wordt gebruik gemaakt van gegevenswoordenboek, zodat zakelijke gebruikers informatie uit back-end gegevensbronnen kunnen gebruiken zonder technische details over de onderliggende gegevensmodellen te kennen.

Zie [gegevenswoordenboekartikel maken voor informatie over het maken en gebruiken van gegevenswoordenboeken](../../forms/using/data-dictionary.md)

## AEM-formulierconfiguraties openen {#accessing-aem-forms-configurations}

Het deelvenster met AEM-gereedschappen bevat gereedschappen voor verschillende componenten. Als u naar specifieke gereedschappen voor AEM-formulieren wilt navigeren, klikt u op het logo ![adobeexperience](assets/adobeexperiencemanager.png) Manager > ![hamer](assets/hammer.png) op gereedschappen > Formulieren. De hulpmiddelen om de volgende functies uit te voeren worden getoond:

* **** Controlemap configureren: Een beheerder kan een netwerkmap, ook wel een controlemap genoemd, zo configureren dat wanneer een gebruiker een bestand (zoals een PDF-bestand) in de controlemap plaatst, een vooraf geconfigureerde bewerking wordt gestart en het bestand wordt gemanipuleerd. Zie Een gecontroleerde map [](/help/forms/using/creating-configure-watched-folder.md)maken en configureren voor gedetailleerde informatie.
* **** Forms App Offline Service configureren:De app-offlineservice van AEM Forms plaatst de paden of URL&#39;s van de bronnen die in een formulier worden gebruikt in cache. Het in cache plaatsen van paden of URL&#39;s van de bronnen die in een formulier worden gebruikt, verbetert de prestaties op de server. Zie [Werken in de offlinemodus](/help/forms/using/work-offline-mode.md)voor informatie over het configureren van de offlinecomponent van de app AEM Forms aan de serverzijde.

![Gereedschappen voor AEM-formulieren](assets/aem_forms_tools_new.png)

* **** PDF-generator configureren: Een beheerder kan instellingen voor AEM Forms PDF Generator configureren, gebruikersaccounts toevoegen en configuratie importeren of exporteren naar de PDF Generator.
* **** Correspondentiebeheermiddelen publiceren: Met AEM Forms kunt u alle letters, documentfragmenten en gegevenswoordenboeken en gerelateerde afhankelijkheden van een auteurinstantie tegelijk publiceren. De gepubliceerde activa omvatten alle activa van het Beheer van de Correspondentie en verwante gebiedsdelen. Zie Formulieren en documenten [](../../forms/using/publishing-unpublishing-forms.md#publishallthecorrespondencemanagementassets)publiceren en publiceren ongedaan maken voor meer informatie.
* **** Correspondentenbeheermiddelen exporteren: U kunt alle Correspondence Management-elementen en gerelateerde afhankelijkheden als een pakket downloaden van een instantie van AEM-formulieren. Zie Elementen [importeren en exporteren naar AEM-formulieren voor gedetailleerde stappen](../../forms/using/import-export-forms-templates.md#importandexportassetsincorrespondencemanagement)

## Algemene elementen van de gebruikersinterface {#commonelements}

* **** Linkerspoor: U kunt op de koppeling naar het pictogram ![links van het spoor klikken](assets/railleftpng.png) om de mogelijkheden voor tijdlijn en verwijzingen van AEM-formulieren weer te geven.

   * **** Tijdlijn: U kunt opmerkingen toevoegen aan en weergeven over een element dat beschikbaar is voor revisie in de tijdlijn. Zie Revisies voor elementen in formulieren [maken en beheren voor gedetailleerde instructies](../../forms/using/create-reviews-forms.md).
   * **** Referenties: Een AEM Forms-element kan worden gebruikt in meerdere AEM Forms-elementen. Een documentfragment kan bijvoorbeeld in meerdere letters worden gebruikt. Verwijzingen zijn een lijst met elementen (andere vormen of bronnen) waarin het geselecteerde element wordt gebruikt en ook de lijst met andere elementen die het geselecteerde element gebruikt.

* **** Broodkruimels: Een broodkruimel vertegenwoordigt de titel van de huidige console of de omslag. U kunt op de optie Breadcrumb klikken om te navigeren tussen het niveau van mappen dat hoger is in de hiërarchie.
* **** Weergaveswitcher: U kunt op de ![weergavelijst](assets/viewlist.png) of de ![viewcard](assets/viewcard.png) van het pictogram Omschakeling weergeven klikken om snel tussen de lijst- en kaartweergave te schakelen. Voor meer informatie over gemeenschappelijke gebruikersinterfacecomponenten, zie [Authoring](/help/sites-authoring/author.md).
* **** Zoeken: Met de zoekoptie kunt u ![zoeken](assets/search.png) naar inhoud en gereedschappen die u nodig hebt. Typ de naam van de inhoud of de productmogelijkheden en selecteer een van de suggesties. Typ bijvoorbeeld &quot;Documenten&quot; om snel naar de console Formulieren en documenten of Documentfragmenten te zoeken en er naartoe te navigeren. Raadpleeg voor meer informatie over zoeken het [zoekartikel](/help/sites-authoring/search.md) van AEM 6.2

* **Werkbalk** Handelingen: Als u een element selecteert, verschijnt de werkbalk Handelingen boven de lijst met elementen. Het bevat alle beheerhulpmiddelen voor het geselecteerde element. U kunt de muisaanwijzer boven een gereedschapspictogram plaatsen om de knopinfo met een beschrijving van de functionaliteit weer te geven

>[!NOTE]
>
>Wanneer een gebruiker een onderzoek uitvoert om het even welke console van Vormen &amp; Documenten, dan bevat het spoor slechts **Filters &amp; Opties**. U kunt Filters en Opties gebruiken om geavanceerd zoeken uit te voeren.

* **Werkbalk** Handelingen: Als u een element selecteert, verschijnt de werkbalk Handelingen boven de lijst met elementen. Het bevat alle beheerhulpmiddelen voor het geselecteerde element. U kunt de muisaanwijzer boven een gereedschapspictogram plaatsen om de knopinfo met een beschrijving van de functionaliteit weer te geven

![Werkbalk voor acties voor een adaptief formulier](assets/action_toolbar_new.png)

Werkbalk voor acties voor een adaptief formulier

