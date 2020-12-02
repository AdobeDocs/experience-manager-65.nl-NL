---
title: Ervaringsfragmenten
seo-title: Ervaringsfragmenten
description: 'null'
seo-description: 'null'
uuid: 9a1d12ef-5690-4a2e-8635-a710775efa39
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: 4c5b52c3-5e23-4125-9306-48bf2ded23cb
docset: aem65
translation-type: tm+mt
source-git-commit: 5c88d9cfdd6238961aa46d36ebc1206a5d0507e0
workflow-type: tm+mt
source-wordcount: '1397'
ht-degree: 8%

---


# Ervaringsfragmenten{#experience-fragments}

Een ervaringsfragment is een groep van een of meer componenten, inclusief inhoud en lay-out, waarnaar op pagina&#39;s kan worden verwezen. Ze kunnen elke gewenste component bevatten.

Een ervaringsfragment:

* Maakt deel uit van een ervaring (pagina).
* Kan op meerdere pagina&#39;s worden gebruikt.
* Is gebaseerd op een malplaatje (editable slechts) om structuur en componenten te bepalen.
* Bestaat uit een of meer componenten, met layout, in een alineasysteem.
* Kan andere ervaringsfragmenten bevatten.
* Kan worden gecombineerd met andere componenten (waaronder andere Experience Fragments) om een volledige pagina (ervaring) te vormen.
* Kan verschillende variaties hebben, die inhoud en/of componenten kunnen delen.
* Kan worden opgedeeld in bouwstenen die kunnen worden gebruikt voor meerdere variaties van het fragment.

U kunt Experience Fragments gebruiken:

* Als een auteur onderdelen (een fragment van een ervaring) van een pagina opnieuw wil gebruiken, moet hij of zij dat fragment kopiëren en plakken. Het maken en onderhouden van deze kopiëren/plakken-ervaringen kost veel tijd en is vaak het gevolg van gebruikersfouten. De Fragmenten van de ervaring elimineren de behoefte aan exemplaar/deeg.
* Om het hoofdloze gebruik-geval CMS te steunen. Auteurs willen AEM alleen gebruiken voor ontwerpen, maar niet voor levering aan de klant. Een systeem/aanraakpunt van derden zou deze ervaring gebruiken en vervolgens leveren aan de eindgebruiker.

>[!NOTE]
>
>Schrijf toegang voor ervaringsfragmenten vereist dat de gebruikersaccount in de groep wordt geregistreerd:
>
>    `experience-fragments-editors`
Neem contact op met de systeembeheerder als er problemen optreden.

## Wanneer moet u ervaringsfragmenten gebruiken? {#when-should-you-use-experience-fragments}

Er moeten ervaringsfragmenten worden gebruikt:

* Wanneer u ervaringen wilt hergebruiken.

   * Ervaringen die opnieuw worden gebruikt met dezelfde of vergelijkbare inhoud

* Wanneer u AEM gebruikt als platform voor het leveren van inhoud voor derden.

   * Om het even welke oplossing die AEM als platform van de inhoudslevering wil gebruiken
   * Inhoud insluiten in aanraakpunten van derden

* Als u ervaring hebt met verschillende variaties of uitvoeringen.

   * Kanaal- of contextspecifieke variaties
   * Ervaringen die zinvol zijn om te groeperen (bijvoorbeeld een campagne met verschillende ervaringen over kanalen)

* Wanneer u Omnichannel Commerce gebruikt.

   * Commerciële inhoud delen op [sociale media](/help/sites-developing/experience-fragments.md#social-variations) kanalen op schaal
   * Transactie aanraakpunten maken

## Uw ervaringsfragmenten ordenen {#organizing-your-experience-fragments}

Het wordt aanbevolen:
* mappen gebruiken om uw fragmenten van de ervaring te ordenen,

* [configureer de toegestane sjablonen voor deze mappen](#configure-allowed-templates-folder).

Door mappen te maken kunt u:

* een zinvolle structuur voor uw ervaringsfragmenten maken; bijvoorbeeld volgens classificatie

   >[!NOTE]
   U hoeft de structuur van uw ervaringsfragmenten niet uit te lijnen met de paginastructuur van uw site.

* [de toegestane sjablonen toewijzen op mapniveau](#configure-allowed-templates-folder)

   >[!NOTE]
   U kunt [malplaatjeredacteur](/help/sites-authoring/templates.md) gebruiken om uw eigen malplaatje te creëren.

Het WKND-project structureert een aantal Ervaringsfragmenten volgens `Contributors`. De gebruikte structuur illustreert ook hoe andere functies, zoals beheer voor meerdere sites (inclusief taalkopieën), kunnen worden gebruikt.

Zie:

`http://localhost:4502/aem/experience-fragments.html/content/experience-fragments/wknd/language-masters/en/contributors/kumar-selveraj/master`

![Mappen voor ervaringsfragmenten](/help/sites-authoring/assets/xf-folders.png)

## Het creëren van en het Vormen van een Omslag voor uw Fragmenten {#creating-and-configuring-a-folder-for-your-experience-fragments} van de Ervaring

Om een omslag voor uw Fragments van de Ervaring tot stand te brengen en te vormen wordt het geadviseerd:

1. [Maak een map](/help/sites-authoring/managing-pages.md#creating-a-new-folder).

1. [Configureer de toegestane sjablonen voor ervaringsfragmenten voor die map](#configure-allowed-templates-folder).

>[!NOTE]
Het is ook mogelijk om [Toegestane Malplaatjes voor uw instantie ](#configure-allowed-templates-instance) te vormen, maar deze methode is **niet** geadviseerd aangezien de waarden bij verbetering kunnen worden beschreven.

### Vorm de Toegestane Malplaatjes voor uw Omslag {#configure-allowed-templates-folder}

>[!NOTE]
Dit is de geadviseerde methode om **Toegestane Malplaatjes** te specificeren, aangezien de waarden niet op verbetering zullen worden beschreven.

1. Navigeer naar de vereiste **map Experience Fragments**.

1. Selecteer de map en **Eigenschappen**.

1. Geef de reguliere expressie op voor het ophalen van de vereiste sjablonen in het veld **Toegestane sjablonen**.

   Bijvoorbeeld:
   `/conf/(.*)/settings/wcm/templates/experience-fragment(.*)?`

   Zie:
   `http://localhost:4502/mnt/overlay/cq/experience-fragments/content/experience-fragments/folderproperties.html/content/experience-fragments/wknd`

   ![Ervaar fragmenteigenschappen - Toegestane sjablonen](/help/sites-authoring/assets/xf-folders-templates.png)

   >[!NOTE]
   Zie [Sjablonen voor ervaringsfragmenten](/help/sites-developing/experience-fragments.md#templates-for-experience-fragments) voor meer informatie.

1. Selecteer **Opslaan en sluiten**.

### Vorm de Toegestane Malplaatjes voor uw Instantie {#configure-allowed-templates-instance}

>[!CAUTION]
Het wordt niet geadviseerd om **Toegestane Malplaatjes** door deze methode te veranderen, aangezien de gespecificeerde malplaatjes op verbetering kunnen worden beschreven.
Gebruik dit dialoogvenster alleen ter informatie.

1. Navigeer naar de vereiste **Experience Fragments** console.

1. Selecteer **Configuratieopties**:

   ![Knop Configuratie](assets/ef-02.png)

1. Specificeer de vereiste malplaatjes in **vorm de Fragments van de Ervaring** dialoog:

   ![Fragmenten voor ervaring configureren](assets/ef-01.png)

   >[!NOTE]
   Zie [Sjablonen voor ervaringsfragmenten](/help/sites-developing/experience-fragments.md#templates-for-experience-fragments) voor meer informatie.

1. Selecteer **Opslaan**.

## Een ervaringsfragment maken {#creating-an-experience-fragment}

Een ervaringsfragment maken:

1. Selecteer Fragmenten van de Ervaring van de Globale Navigatie.

   ![xf-01](assets/xf-01.png)

1. Navigeer naar de vereiste map en selecteer **Maken**.

   ![xf-02](assets/xf-02.png)

1. Selecteer **Fragment van de Ervaring** om **Create de tovenaar van het Fragment van de Ervaring** te openen.

   Selecteer de vereiste **sjabloon** en kies vervolgens **Volgende**:

   ![xf-03](assets/xf-03.png)

1. Voer de **Eigenschappen** voor uw **Experience-fragment** in.

   A **Titel** is verplicht. Als de **Naam** leeg wordt gelaten, wordt deze afgeleid van de **Titel**.

   ![xf-04](assets/xf-04.png)

1. Klik **Maken**.

   Er wordt een bericht weergegeven. Selecteer:

   * **Ga** niet terug naar de console

   * **Openen om de fragmenteditor te openen** 

## Uw ervaringsfragment {#editing-your-experience-fragment} bewerken

De Experience Fragment Editor biedt u vergelijkbare mogelijkheden als de normale pagina-editor.

>[!NOTE]
Zie [Pagina-inhoud bewerken](/help/sites-authoring/editing-content.md) voor meer informatie over het gebruik van de pagina-editor.

De volgende voorbeeldprocedure laat zien hoe u een gummetje voor een product kunt maken:

1. Sleep een **Taser** vanuit de [Componentbrowser](/help/sites-authoring/author-environment-tools.md#components-browser).

   ![xf-05](assets/xf-05.png)

1. Selecteer **[Configureren](/help/sites-authoring/editing-content.md#edit-configure-copy-cut-delete-paste)** in de werkbalk van de component.
1. Voeg de **asset** toe en definieer desgewenst de **eigenschappen**.
1. Bevestig de definities met **Done** (tik pictogram).
1. Voeg desgewenst meer componenten toe.

## Een ervaringsfragmentvariatie {#creating-an-experience-fragment-variation} maken

U kunt variaties van uw Fragment van de Ervaring tot stand brengen, afhankelijk van uw behoeften:

1. Open het fragment voor [bewerken](/help/sites-authoring/experience-fragments.md#editing-your-experience-fragment).
1. Open het tabblad **Variaties**.

   ![xf-authoring-06](assets/xf-authoring-06.png)

1. **Met** Create kunt u het volgende maken:

   * **Variatie**
   * **Variatie als live-kopie**.

1. Definieer de vereiste eigenschappen:

   * **Sjabloonmodel**
   * **Titel**
   * **Naam**; indien niet ingevuld, wordt het afgeleid van de titel
   * **Beschrijving**
   * **Variatietags**

   ![xf-08](assets/xf-06.png)

1. Bevestig met **Done** (tik icon) de nieuwe variatie in het paneel:

   ![xf-07](assets/xf-07.png)

## Het gebruiken van uw Fragment van de Ervaring {#using-your-experience-fragment}

U kunt het fragment van de Ervaring nu gebruiken wanneer het ontwerpen van uw pagina&#39;s:

1. Open een pagina om te bewerken.

   Bijvoorbeeld: [https://localhost:4502/editor.html/content/we-retail/language-masters/en/products/men.html](https://localhost:4502/editor.html/content/we-retail/language-masters/en/products/men.html)

1. Maak een instantie van de component Experience Fragment door de component van de browser Components naar het alineasysteem van de pagina te slepen:

   ![xf-08](assets/xf-08.png)

1. Voeg het daadwerkelijke fragment van de Ervaring aan de componenteninstantie toe; ofwel:

   * Sleep het vereiste fragment vanuit de middelenbrowser en zet het neer op de component
   * Selecteer **Configureren** op de componentwerkbalk en geef het te gebruiken fragment op. Bevestig dit met **Done** (tik)

   ![xf-09](assets/xf-09.png)

   >[!NOTE]
   Bewerken werkt op de werkbalk van de component als een sneltoets waarmee het fragment in de fragmenteditor wordt geopend.

## Bouwstenen {#building-blocks}

U kunt een of meer componenten selecteren om een bouwsteen voor recycling binnen uw fragment te maken:

### Een bouwsteen maken {#creating-a-building-block}

Een nieuw bouwblok maken:

1. In de redacteur van het Fragment van de Ervaring, selecteer de componenten u wilt hergebruiken:

   ![xf-10](assets/xf-10.png)

1. Selecteer **Omzetten in bouwsteen** op de werkbalk Componenten:

   ![xf-authoring-13-icon](assets/xf-authoring-13-icon.png)

1. Voer de naam van de **bouwsteen** in en bevestig dit met **Converteren**:

   ![xf-11](assets/xf-11.png)

1. De **bouwsteen** wordt weergegeven op het tabblad en kan worden geselecteerd in het alineasysteem:

   ![xf-12](assets/xf-12.png)

#### Een bouwblok beheren {#managing-a-building-block}

Uw bouwsteen is zichtbaar in **Bouwstenen** tabel. Voor elk blok zijn de volgende acties beschikbaar:

* Ga naar master: open de mastervariatie op een nieuw tabblad
* Naam wijzigen
* Verwijderen

![xf-13](assets/xf-13.png)

#### Een bouwsteen gebruiken {#using-a-building-block}

U kunt de bouwsteen naar het alineasysteem van om het even welk fragment slepen, zoals met om het even welke component.

## Details van uw ervaringsfragment {#details-of-your-experience-fragment}

Details van het fragment kunt u zien:

1. Details worden getoond in alle weergaven van de console voor **Experience-fragmenten**, met de **Lijstweergave**[ inclusief details van een exportbewerking naar het doel](/help/sites-administering/experience-fragments-target.md):

   ![ef-03](assets/ef-03.png)

1. Wanneer u **Eigenschappen** van het Fragment van de Ervaring opent:

   ![ef-04](assets/ef-04.png)

   De eigenschappen zijn beschikbaar op verschillende tabbladen:

   >[!CAUTION]
   Deze lusjes worden getoond wanneer u **Eigenschappen** van de console van de Fragmenten van de Ervaring opent.
   Als u **Eigenschappen opent** tijdens het bewerken van een Experience-fragment, worden de juiste [Pagina-eigenschappen](/help/sites-authoring/editing-page-properties.md) weergegeven.

   ![ef-05](assets/ef-05.png)

   * **Basis**

      * **Titel**  - verplicht

      * **Beschrijving**
      * **Tags**
      * **Totaal aantal varianten**  - alleen informatie

      * **Aantal webvarianten**  - alleen informatie
      * **Aantal niet-webvarianten**  - alleen **informatie**

      * **Aantal pagina&#39;s dat dit fragment**  gebruikt - alleen informatie
   * **Cloud Services**

      * **Cloud Configuration**
      * **Configuraties van Cloud Servicen**
      * **Facebook-pagina-id**
      * **Pinterest board**
   * **Verwijzingen**

      * Een lijst met referenties.
   * **Status van sociale media**

      * Bijzonderheden over variaties in sociale media.




## De normale HTML-uitvoering {#the-plain-html-rendition}

Met de kiezer `.plain.` in de URL hebt u vanuit de browser toegang tot de normale HTML-uitvoering.

>[!NOTE]
Hoewel dit direct beschikbaar is in de browser, is het primaire doel [andere toepassingen (bijvoorbeeld web-apps van derden, aangepaste mobiele implementaties) toe te staan rechtstreeks toegang te krijgen tot de inhoud van het Experience Fragment door alleen de URL](/help/sites-developing/experience-fragments.md#the-plain-html-rendition) te gebruiken.

## Fragmenten {#exporting-experience-fragments} exporteren

Experience Fragments worden standaard geleverd in de HTML-indeling. Dit kan zowel door AEM als derdekanalen worden gebruikt.

Voor export naar Adobe Target kan JSON ook worden gebruikt. Zie [Doelintegratie met ervaringsfragmenten](/help/sites-administering/experience-fragments-target.md) voor volledige informatie.
