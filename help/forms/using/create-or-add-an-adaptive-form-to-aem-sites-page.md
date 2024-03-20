---
title: Een adaptief formulier maken of toevoegen aan een AEM Sites-pagina
description: Ontdek hoe u moeiteloos een adaptief formulier kunt maken of toevoegen aan uw AEM Sites-pagina. Leer stapsgewijze technieken en tips en trucs voor het integreren van dynamische en aanpasbare formulieren in uw website en het optimaliseren van uw digitale ervaringen voor maximale impact.
Keywords: AEM Forms in sites, AF in Sites editor, af in aem sites, aem sites af, add af to a sites page, af aem sites, af sites, create af in a sites page, adaptive form in aem sites, forms aem sites, add form to a sites page, adaptive forms aem sites, add adaptive forms to aem page, create forms in an aem sites page
feature: Adaptive Forms, Foundation Components
exl-id: dcf023a1-8735-48cb-b3ea-d17357eeedaf
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '2832'
ht-degree: 0%

---

# Een adaptief formulier maken of toevoegen aan een AEM Sites-pagina {#create-or-add-an-adaptive-form-to-aem-sites-page}

<span class="preview"> Adobe beveelt aan moderne en uitbreidbare gegevensvastlegging te gebruiken [Kernonderdelen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html) for [nieuwe Adaptieve Forms maken](/help/forms/using/create-an-adaptive-form-core-components.md) of [Aangepaste Forms toevoegen aan AEM Sites-pagina&#39;s](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor de auteur Adaptive Forms die gebruikmaakt van stichtingscomponenten. </span>

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | Dit artikel |
| AEM as a Cloud Service | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/create-or-add-an-adaptive-form-to-aem-sites-page.html) |

Met AEM Forms kunt u naadloos adaptieve formulieren opnemen in uw webpagina&#39;s. Zo kunnen bezoekers formulieren op een gemakkelijke manier invullen en verzenden zonder de pagina waarop ze staan te verlaten. Op die manier kunnen ze moeiteloos betrokken blijven bij andere elementen van de website terwijl ze actief met het formulier communiceren.

Met AEM paginaeditor kunt u snel meerdere formulieren maken en toevoegen aan uw AEM Sites-pagina&#39;s. Met AEM Pagina-editor kunnen auteurs van inhoud naadloze ervaringen met het vastleggen van gegevens maken op een sitepagina met behulp van de kracht van adaptieve formuliercomponenten, zoals dynamisch gedrag, validaties, gegevensintegratie, het genereren van een document van record- en bedrijfsprocesautomatisering. Met deze functie kunt u ook verschillende functies van AEM Sites-pagina&#39;s gebruiken, zoals versioning, adressering, vertaling en beheer voor meerdere sites.

AEM Forms biedt adaptieve formuliercontainer en adaptieve Forms - Embed-componenten. U kunt de container van het Aangepaste Vorm gebruiken om een vorm in een Fragment van de Ervaring of een pagina van AEM Sites tot stand te brengen, terwijl de Aangepast Forms - sluit component u een bestaand Aangepast Formulier of tot een vorm toe te voegen gebruikend de Redacteur van de AanpassingsForms.

![Aangepast formulier op sitepagina](/help/forms/using/assets/adaptive-form-in-sites-page.png)

## Voordelen van het gebruik van de component Aangepaste formuliercontainer in AEM paginaeditor of Ervaar fragment

Met de adaptieve formuliercontainer in AEM paginaeditor kunt u naadloze ervaringen met het vastleggen van gegevens maken op een sitepagina en daarbij gebruikmaken van de kracht van adaptieve Forms-componenten, zoals dynamisch gedrag, validaties, gegevensintegratie, het genereren van een document van registratie- en bedrijfsprocesautomatisering. Met deze functie kunt u ook verschillende functies van AEM Sites-pagina&#39;s gebruiken, zoals versioning, doelgericht maken, vertalen en beheer op meerdere sites, waardoor het maken en beheren van formulieren in hun geheel wordt verbeterd. Hieronder volgen enkele voorbeelden:

* **Versioning:** AEM Sites-pagina&#39;s bieden [robuuste versiemogelijkheden](/help/sites-authoring/working-with-page-versions.md), waarmee u verschillende versies van uw formulieren kunt bijhouden en beheren. Op deze manier kunt u wijzigingen aanbrengen en formulieren verbeteren terwijl u de mogelijkheid behoudt om indien nodig terug te draaien naar vorige versies. Versioning zorgt voor een beheerste en georganiseerde benadering van formulierontwikkeling en -ontwikkeling.
* **Doelstelling (integratie met Adobe Target):** Met AEM Sites-pagina&#39;s die zich richten op mogelijkheden, kunt u ook [de formulierervaring aanpassen voor verschillende doelgroepen](/help/sites-administering/target.md). Door gebruikerssegmenten en doelcriteria te gebruiken, kunt u de inhoud, het ontwerp of het gedrag van het formulier aanpassen aan specifieke groepen gebruikers. Hierdoor kunt u een gepersonaliseerde en relevante formulierervaring bieden, waardoor de betrokkenheid en conversiesnelheden toenemen.
* **Vertaling:** AEM Sites [naadloze integratie met vertaalservices](/help/sites-administering/translation.md)waarmee u formulieren eenvoudig in meerdere talen kunt vertalen. Deze functie vereenvoudigt het lokalisatieproces, zodat uw formulieren toegankelijk zijn voor een wereldwijd publiek. U kunt vertalingen efficiënt beheren binnen AEM vertaalprojecten, waardoor u minder tijd en moeite nodig hebt voor ondersteuning van meertalige formulieren. Zie de sectie Overwegingen voor meer informatie over vertaling.
* **Beheer van meerdere sites en Live Copy:** AEM Sites biedt robuuste [Multisite beheer en mogelijkheden voor live kopiëren](/help/sites-administering/msm.md), waarmee u meerdere websites kunt maken en beheren in één omgeving. Met deze functie kunt u nu formulieren hergebruiken op verschillende sites, zodat u consistent bent en dubbel werk kunt voorkomen. Met gecentraliseerde controle en beheer kunt u formulieren efficiënt onderhouden en bijwerken op meerdere websites.
* **Thema&#39;s:** AEM Sites-pagina&#39;s bieden een raamwerk voor het ontwerpen en onderhouden van consistente visuele stijlen op meerdere webpagina&#39;s. Met deze opties definieert u kleuren, lettertypen, stijlpagina&#39;s en andere visuele elementen die een bijdrage leveren aan het algehele uiterlijk van de website. [U kunt de voor een AEM Sites-pagina ontworpen thema&#39;s gebruiken voor een adaptief formulier, zodat u tijd en moeite bespaart](/help/sites-authoring/style-system.md).
* **Tags:** Met AEM Sites-pagina&#39;s kunt u [Labels of labels toewijzen aan een pagina, element of andere inhoud](/help/sites-authoring/tags.md). Tags zijn trefwoorden of metagegevenslabels waarmee u inhoud kunt indelen en indelen op basis van specifieke criteria. U kunt een of meer tags toewijzen aan pagina&#39;s, elementen of andere inhoudsonderdelen binnen AEM om de zoekopdracht te verbeteren en de elementen te categoriseren.
* **Inhoud vergrendelen en ontgrendelen:** AEM Sites staat gebruikers toe om [toegang tot en wijzigingen in pagina&#39;s beheren](/help/sites-authoring/editing-content.md#locking-a-page-locking-a-page) in de AEM Sites-omgeving. Wanneer een pagina is vergrendeld, betekent dit dat deze is beveiligd tegen onbevoegde wijzigingen of bewerkingen door andere gebruikers. Alleen de gebruiker die de inhoud heeft vergrendeld of een aangewezen beheerder kan deze ontgrendelen om wijzigingen toe te staan.


## Verschillende opties voor het toevoegen van een adaptief formulier in AEM paginaeditor

U kunt deze functie optimaal benutten door de volgende opties te gebruiken:

* **[Een aangepast adaptief formulier toevoegen aan een AEM Sites-pagina:](#create-an-adaptive-form-in-sites-editor)** Een geheel nieuw formulier maken, dat speciaal aan uw vereisten en ontwerpvoorkeuren is aangepast.

* **[Voeg een aangepast adaptief formulier toe aan een Experience Fragments:](#create-an-adaptive-form-in-experience-fragment)** Vergroot het bereik van uw formulieren door deze toe te voegen aan AEM Experience Fragments, zodat u ze naadloos kunt hergebruiken op meerdere pagina&#39;s of sites.

* **[Een adaptief formulier converteren naar fragment:](#convert-an-adaptive-form-in-sites-page-to-an-experience-fragment)** Converteer een adaptief formulier dat aan een AEM Sites-pagina is toegevoegd naar een Experience-fragment en gebruik het formulier opnieuw op meerdere AEM Sites-pagina&#39;s.

* **Formulieren op basis van goedgekeurde sjablonen maken en toevoegen aan een AEM Sites-pagina:** Gebruik vooraf goedgekeurde sjablonen om snel formulieren te maken die zijn afgestemd op de brandingrichtlijnen en ontwerpstandaarden van uw organisatie. Deze optie is alleen beschikbaar voor Adaptive Forms die is gemaakt met de Adaptive Forms Editor of de Adaptive Forms - Embed-component.

* **Bestaande formulieren toevoegen aan een AEM Sites-pagina:** U kunt formulieren die u al hebt gemaakt, eenvoudig integreren in uw websites, zodat bezoekers direct met ze kunnen communiceren. Deze optie is alleen beschikbaar voor Adaptive Forms die is gemaakt met de Adaptive Forms Editor of de Adaptive Forms - Embed-component.

* **Meerdere formulieren toevoegen aan een AEM Sites-pagina of Ervaar fragment:**  Voeg meerdere formulieren aan een pagina toe om gebruikers meerdere keuzes te bieden op basis van hun voorkeuren en vereisten. Dit kan een combinatie van geheel nieuwe formulieren en bestaande formulieren zijn.

## Overwegingen {#consideration}

* Wanneer u een formulier maakt of toevoegt met de container voor adaptieve formulieren, worden de formulieren vertaald en gelokaliseerd via de AEM Sites-vertaalstroom. Voor elke taal wordt een afzonderlijke kopie (taalkopie) van de sitepagina en de bijbehorende formulieren gegenereerd en wanneer een auteur van de inhoud een regel in een formulier op de bovenliggende pagina wijzigt, moeten dezelfde wijzigingen worden aangebracht in alle taalkopieën van het formulier. Met de adaptieve formuliercontainer kunt u ook verschillende functies van AEM Sites-pagina&#39;s gebruiken, zoals versioning, adressering, vertaling en beheer voor meerdere sites.

* Wanneer u een formulier maakt of toevoegt met de component Adaptief insluiten van formulieren, worden de formulieren vertaald en gelokaliseerd met behulp van de AEM Forms-vertaalstroom. In dit geval wordt één formulier onderhouden en wordt ernaar verwezen in alle taalkopieën van de sitepagina&#39;s. De adaptieve component Form-embed biedt geen toegang tot verschillende functies van AEM Sites-pagina&#39;s, zoals versioning, adressering, vertaling en beheer voor meerdere sites.


## Voordat u begint {#before-you-start}

+++  Adaptieve Forms Core-componenten inschakelen voor uw omgeving

Zorg ervoor dat de [Adaptieve Forms Core-componenten zijn ingeschakeld voor uw omgeving](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/quick-setup/enable-headless-adaptive-forms-and-core-components.html?lang=en).

+++

+++  Adaptieve Forms-clientbibliotheken toevoegen aan uw AEM Sites-pagina en onderdelen van de Experience Fragment-pagina

Om volledige functionaliteit van de Adaptive Forms Container component toe te laten, voeg de Customheaderlibs en Customfooterlibs cliëntbibliotheken aan uw AEM Sites pagina toe gebruikend de plaatsingspijpleiding. De bibliotheken toevoegen:

1. Meld u aan bij de AEM Author-instantie en open CRX DE. De standaard-URL voor een instantie van de Auteur die lokaal wordt uitgevoerd `http://localhost:4502/crx/de`.

1. Open de `/apps/[your-sites-project]/components/page/customheaderlibs.html` en voeg de volgende code toe aan het bestand:

   ```
       //Customheaderlibs.html
       <sly data-sly-use.clientlib="core/wcm/components/commons/v1/templates/clientlib.html">
       <sly data-sly-call="${clientlib.css @ categories='core.forms.components.runtime.all'}"/>
       </sly> 
   ```

1. Open de `/apps/[your-sites-project]/components/page/customfooterlibs.html` en voeg de volgende code toe aan het bestand:

   ```
       //customfooterlibs.html
       <sly data-sly-use.clientlib="core/wcm/components/commons/v1/templates/clientlib.html">
       <sly data-sly-test="${!wcmmode.edit}" data-sly-call="${clientlib.js @ categories='core.forms.components.runtime.all', async=true}"/>
       </sly> 
   ```

1. Open de `/apps/[your-sites-project]/components/xfpage/customheaderlibs.html` en voeg de volgende code toe aan het bestand:

   ```
       //Customheaderlibs.html
       <sly data-sly-use.clientlib="core/wcm/components/commons/v1/templates/clientlib.html">
       <sly data-sly-call="${clientlib.css @ categories='core.forms.components.runtime.all'}"/>
       </sly> 
   ```

1. Open de `/apps/[your-sites-project]/components/customfooterlibs.html` en voeg de volgende code toe aan het bestand:

   ```
       //customfooterlibs.html
       <sly data-sly-use.clientlib="core/wcm/components/commons/v1/templates/clientlib.html">
       <sly data-sly-test="${!wcmmode.edit}" data-sly-call="${clientlib.js @ categories='core.forms.components.runtime.all', async=true}"/>
       </sly> 
   ```

1. Herhaal bovenstaande stappen voor alle instanties Auteur en Publiceren in uw omgeving.

+++

+++ Adaptieve Forms-container inschakelen

Inschakelen [!UICONTROL Adaptive Forms Container] in het sjabloonbeleid voert u de volgende stappen uit:

1. Open de AEM Sites-pagina of Experience Fragment om te bewerken. Als u de pagina wilt openen om te bewerken, selecteert u de pagina en klikt u op Bewerken.
1. Open de sjabloon van de pagina Sites of Experience Fragment. Ga naar de [!UICONTROL Page Information] ![Pagina-informatie](/help/forms/using/assets/Smock_Properties_18_N.svg) > [!UICONTROL Edit Template]. De bijbehorende sjabloon wordt geopend in de sjablooneditor.
1. Klik in de structuurweergave op de knop **[!UICONTROL Policy]** ![Beleid](/help/forms/using/assets/Smock_FeedManagement_18_N.svg) in de menubalk. In de **[!UICONTROL Allowed Components]** en selecteert u de **[!UICONTROL Adaptive Forms Container]**  selectievakje onder **[Projectnaam AEM] - Adaptief formulier**.
1. Klik op **[!UICONTROL Done]**.

>[!VIDEO](https://video.tv.adobe.com/v/3419370?quality=12&learn=on)

+++

## Een adaptief formulier maken {#create-an-adaptive-form-in-sites-editor-or-experience-fragment}

U kunt een geheel nieuw formulier maken en dit aanpassen aan uw vereisten en ontwerpvoorkeuren, rechtstreeks op een AEM Sites-pagina of in Experience Fragment. Voor formulieren voor eenmalig gebruik wordt direct schrijven naar een AEM Sites-pagina aanbevolen, terwijl Experience Fragments ideaal zijn voor formulieren die opnieuw moeten worden gebruikt op meerdere pagina&#39;s op uw website.

* [Een formulier maken op een AEM Sites-pagina](#create-an-adaptive-form-in-sites-editor)
* [Een formulier maken in een ervaringsfragment](#create-an-adaptive-form-in-experience-fragment)
* [Een adaptief formulier in AEM Sites-pagina converteren naar een Experience-fragment](#convert-an-adaptive-form-in-sites-page-to-an-experience-fragment)

### Een formulier maken op een AEM Sites-pagina {#create-an-adaptive-form-in-sites-editor}

Met de component Aangepaste formuliercontainer in AEM paginaeditor kunt u een aangepast formulier maken. Met de component kunt u een formulier maken door de formuliercomponenten te slepen en neer te zetten. De formuliercomponenten zijn gebaseerd op kerncomponenten. U kunt deze instellingen eenvoudig aanpassen aan de vereisten van uw organisatie.

>[!VIDEO](https://video.tv.adobe.com/v/3419284?quality=12&learn=on)

Een adaptief formulier maken op een sitepagina:

1. Open de AEM Sites-pagina in de bewerkingsmodus.
1. Sleep de **[!UICONTROL Adaptive Forms Container]** van de Browser van de Component aan de pagina van Plaatsen. Er wordt een spatie op de pagina voor het formulier gemaakt. U kunt de lay-outmodus gebruiken om de grootte van de containerruimte te wijzigen.
1. Sleep Adaptieve componenten van Form Core naar de containerruimte om het formulier te maken.
1. Voeg de knop Verzenden toe.

Volgende [De handeling Verzenden instellen](#configure-submit-action-for-form) en geavanceerde eigenschappen.

### Een formulier maken in een ervaringsfragment {#create-an-adaptive-form-in-experience-fragment}

U kunt het bereik van uw formulieren uitbreiden door ze toe te voegen aan AEM Experience Fragments, zodat u ze naadloos kunt hergebruiken op meerdere pagina&#39;s of sites. U kunt bijvoorbeeld een inschrijvingsformulier voor een nieuwsbrief opnemen in een Experience-fragment. Zo kunt u het fragment op meerdere pagina&#39;s van uw website opnieuw gebruiken, zodat u het formulier niet herhaaldelijk opnieuw hoeft te maken. Alle updates of wijzigingen die worden aangebracht in het inschrijvingsformulier voor nieuwsbrieven binnen het Experience Fragment, worden automatisch doorgegeven aan alle pagina&#39;s waar het wordt gebruikt. Dit stroomlijnt het proces en zorgt voor een naadloze gebruikerservaring en vereenvoudigt het beheer van de formulieren van uw website.

Een adaptief formulier maken in een ervaringsfragment:

1. Open een ervaringsfragment.
1. Sleep de **[!UICONTROL Adaptive Forms Container]** van Componentbrowser naar Experience Fragment.
1. Sleep Adaptieve componenten van Form Core naar de containerruimte in het Experience Fragment om het formulier te maken.
1. Voeg de knop Verzenden toe.

Volgende [De handeling Verzenden instellen](#configure-submit-action-for-form) en geavanceerde eigenschappen.

### Een adaptief formulier in AEM Sites-pagina converteren naar een Experience-fragment {#convert-an-adaptive-form-in-sites-page-to-an-experience-fragment}

U kunt een bestaand adaptief formulier in een sitepagina-editor converteren naar een ervaringsfragment om het formulier te hergebruiken op meerdere pagina&#39;s of sites.

Een adaptief formulier in AEM Sites-pagina converteren naar een Experience-fragment:

1. Open de AEM Sites-pagina met het adaptieve formulier (in de Adaptive Forms Container-component) in de bewerkingsmodus.
1. Open de inhoudsstructuur en selecteer de **[!UICONTROL Adaptive Forms Container]** dat als host fungeert voor uw adaptieve formulier. Een AEM Sites-pagina kan meerdere Adaptive Forms hosten. Selecteer dus zorgvuldig de juiste adaptieve Forms-container.
1. Selecteer in de menubalk de optie ![Omzetten in ervaringspictogram voor fragmentvariatie](/help/forms/using/assets/Smock_FilingCabinet_18_N.svg) Omzetten in het pictogram voor het ervaren van fragmentvariatie.
   ![Formulier in sitepagina converteren naar een ervaringsfragment](/help/forms/using/assets/convert-form-in-sites-page-to-an-experience-fragment.png)

   Er wordt een dialoogvenster weergegeven waarin u de container Adaptief formulier kunt converteren naar een nieuw Ervaringsfragment of een bestaand Erviteitsfragment kunt uitbreiden
1. Stel in het dialoogvenster Converteren naar ervaringsfragmentvariatie waarden in voor de volgende opties:

   * **Handeling:** Selecteer deze optie om een ervaringsfragment te maken of aan een bestaand ervaringsfragment toe te voegen.
   * **Bovenliggend pad:** Geef het pad van de map op waarin u het ervaringsfragment wilt plaatsen. De optie is alleen beschikbaar voor het maken van een ervaringsfragment.
   * **Template:** Geef het pad van de fragmentsjabloon voor ervaring op. Als u geen fragmentsjabloon voor ervaring hebt, [maken](/help/sites-developing/experience-fragments.md). De optie is alleen beschikbaar als u een adaptief formulier toevoegt aan een bestaand ervaringsfragment.
   * **Fragmenttitel:** Geef de titel van het ervaringsfragment op. De titel identificeert op unieke wijze een ervaringsfragment


## Handeling voor verzenden voor het formulier configureren {#configure-submit-action-for-form}

Met een handeling Verzenden kunt u de bestemming kiezen van gegevens die zijn vastgelegd in een adaptief formulier. Deze wordt geactiveerd wanneer een gebruiker op de knop Verzenden klikt op een adaptief formulier. Aangepaste formulieren bevatten enkele van de verzendacties. U kunt ook een standaardverzendactie uitbreiden om uw eigen aangepaste verzendactie te maken. Een handeling verzenden voor uw formulier configureren:

1. Open de AEM van de Pagina-editor of Ervaar Fragment dat het adaptieve formulier bevat.
1. Open de inhoudsstructuur en selecteer de **[!UICONTROL Adaptive Forms Container]** dat als host fungeert voor uw adaptieve formulier. Een AEM Sites-pagina kan meerdere Adaptive Forms hosten. Selecteer dus zorgvuldig de juiste adaptieve Forms-container.
1. Klik op de eigenschappen van de container van het adaptieve formulier ![Eigenschappen van adaptieve formuliercontainers](/help/forms/using/assets/configure-icon.svg) pictogram. Het dialoogvenster Aangepaste formuliercontainer voor het configureren van verzendacties wordt geopend.
   ![Container voor adaptieve formulieren](/help/forms/using/assets/adaptive-forms-container.png)
1. Selecteer en vorm een Submit actie, die op uw vereisten wordt gebaseerd. Zie voor meer informatie over Handelingen verzenden [Handeling Adaptief verzenden van formulier](configuring-submit-actions.md)


## Een schema of formuliergegevensmodel voor een formulier configureren {#configure-schema-or-data-model-for-form}

Met het formuliergegevensmodel kunt u een formulier verbinden met een gegevensbron om gegevens te verzenden en te ontvangen op basis van gebruikersacties. U kunt een formulier ook verbinden met een JSON-schema om de verzonden gegevens in een vooraf gedefinieerde indeling te ontvangen.

Voordat u een formulier koppelt aan een schema of formuliergegevensmodel

* [Een JSON-schema maken en uploaden naar uw omgeving](adaptive-form-json-schema-form-model.md)
* [Een formuliergegevensmodel maken](create-form-data-models.md)

Een JSON-schema of formuliergegevensmodel configureren voor uw formulier:

1. Open de AEM van de Pagina-editor of Ervaar Fragment dat het adaptieve formulier bevat.
1. Open de inhoudsstructuur en selecteer de **[!UICONTROL Adaptive Forms Container]** dat als host fungeert voor uw adaptieve formulier. Een AEM Sites-pagina kan meerdere Adaptive Forms hosten. Selecteer dus zorgvuldig de juiste adaptieve Forms-container.
1. Klik op de eigenschappen van de container van het adaptieve formulier ![Eigenschappen van adaptieve formuliercontainers](/help/forms/using/assets/configure-icon.svg) pictogram. Het dialoogvenster Aangepaste formuliercontainer voor het configureren van gegevensmodellen wordt geopend.
   ![Formuliergegevensmodel adaptieve formuliercontainer](/help/forms/using/assets/form-data-model-adaptive-forms-container.png)
1. Selecteer en configureer een JSON-schema of formuliergegevensmodel op basis van uw vereisten. Zie voor meer informatie over Handelingen verzenden [Handeling Adaptief verzenden van formulier](configuring-submit-actions.md).

   * Wanneer u **[!UICONTROL Form Model]** gebruiken **[!UICONTROL Select Form Data Model]** om een vooraf geconfigureerd formuliergegevensmodel te selecteren.
   * Wanneer u **[!UICONTROL Schema]** gebruiken **[!UICONTROL Schema]** Selecteer een JSON-schema voor uw formulier.

1. Klik op **[!UICONTROL Done]**.

## Een prefill-service voor een formulier configureren {#configure-prefill-service-for-form}

U kunt de Prefill-service gebruiken om automatisch velden van een adaptief formulier in te vullen met bestaande gegevens. Wanneer een gebruiker een formulier opent, worden de waarden voor die velden vooraf ingevuld. U kunt:

* [Een aangepaste prefill-service maken](prepopulate-adaptive-form-fields.md)
* [Vooraf ingevulde service Formuliergegevensmodel gebruiken](#fdm-prefill-service)

### Vooraf ingevulde service Formuliergegevensmodel gebruiken {#fdm-prefill-service}

Met de service Vooraf invullen formuliergegevensmodel kunt u velden van een formulier vooraf invullen met een geconfigureerd formuliergegevensmodel. De service Vooraf invullen formuliergegevensmodel gebruikt de [De service van het geconfigureerde formuliergegevensmodel ophalen](work-with-form-data-model.md#add-data-model-objects-and-services-add-data-model-objects-and-services) om gegevens op te halen. Als u de service Vooraf invullen van formuliergegevensmodel wilt gebruiken voor een adaptief formulier:

1. Open de AEM van de Pagina-editor of Ervaar Fragment dat het adaptieve formulier bevat.
1. Open de inhoudsstructuur en selecteer de **[!UICONTROL Adaptive Forms Container]** dat als host fungeert voor uw adaptieve formulier. Een AEM Sites-pagina kan meerdere Adaptive Forms hosten. Selecteer dus zorgvuldig de juiste adaptieve Forms-container.
1. Klik op de eigenschappen van de container van het adaptieve formulier ![Eigenschappen van adaptieve formuliercontainers](/help/forms/using/assets/configure-icon.svg) pictogram. Het dialoogvenster Aangepaste formuliercontainer voor het configureren van gegevensmodellen wordt geopend.
   ![Pagina-editor voor Fdm-sites vooraf invullen](/help/forms/using/assets/prefill-service-fdm-aem-sites-page-editor.png)
1. Selecteer een formuliergegevensmodel. Open de **[!UICONTROL Basic]** tab. Selecteer in de service Prefill de optie **[!UICONTROL Forms Portal Draft Prefill Service]**.
1. Klik op **[!UICONTROL Done]**.

## Leid de gebruiker om naar een nieuwe gebruiker bij het indienen van een formulier of toon een bedankje

Bij het verzenden van een formulier kunt u de gebruiker omleiden naar een andere webpagina of een bericht. Om de gebruiker om te leiden of het dank u bericht te vormen:

1. Open de AEM van de Pagina-editor of Ervaar Fragment dat het adaptieve formulier bevat.
1. Open de inhoudsstructuur en selecteer de **[!UICONTROL Adaptive Forms Container]** dat als host fungeert voor uw adaptieve formulier. Een AEM Sites-pagina kan meerdere Adaptive Forms hosten. Selecteer dus zorgvuldig de juiste adaptieve Forms-container.
1. Klik op de eigenschappen van de container van het adaptieve formulier ![Eigenschappen van adaptieve formuliercontainers](/help/forms/using/assets/configure-icon.svg) pictogram. Het dialoogvenster Aangepaste formuliercontainer voor het configureren van gegevensmodellen wordt geopend.
1. Open de **[!UICONTROL Submission]** tab.

   * Als u een omleidings-URL wilt configureren, selecteert u bij Verzenden de optie Omleiden naar URL en geeft u een absoluut adres, een omleidings-URL of een relatief pad van een AEM Sites-pagina op.

   * Als u een aangepast bericht of een bedankbericht wilt configureren, selecteert u bij Verzenden de optie Bericht tonen en geeft u een bericht op in het vak Berichtinhoud. Het is een tekstvak met tekstopmaak. U kunt de optie Volledig scherm gebruiken om alle beschikbare tekstitems weer te geven.

## Zie ook {#see-also}

* [Een op zichzelf staand adaptief formulier voor kerncomponenten maken](/help/forms/using/create-an-adaptive-form-core-components.md)
* [Stijlen of thema&#39;s maken voor uw formulieren](/help/forms/using/create-or-customize-themes-for-adaptive-forms-core-components.md)
