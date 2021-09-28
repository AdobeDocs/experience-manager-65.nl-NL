---
title: Paginaontwerp aanpassen
seo-title: Customizing Page Authoring
description: AEM biedt verschillende mechanismen waarmee u de functionaliteit voor het schrijven van pagina's kunt aanpassen
seo-description: AEM provides various mechanisms to enable you to customize page authoring functionality
uuid: 9dc72d98-c5ff-4a00-b367-688ccf896526
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: 6825dcd6-fa75-4410-b6b2-e7bd4a391224
exl-id: 90594588-db8e-4d4c-a208-22c1c6ea2a2d
source-git-commit: 273836ad0afd6466eac437bf7711e7dbabc1d5e9
workflow-type: tm+mt
source-wordcount: '1383'
ht-degree: 0%

---

# Paginaontwerp aanpassen{#customizing-page-authoring}

>[!CAUTION]
>
>In dit document wordt beschreven hoe u het ontwerpen van pagina&#39;s kunt aanpassen in de moderne interface met aanraakbediening. Dit document is niet van toepassing op de klassieke gebruikersinterface.

AEM biedt verschillende mechanismen waarmee u de functionaliteit voor het schrijven van pagina&#39;s (en de [consoles](/help/sites-developing/customizing-consoles-touch.md)) van de ontwerpinstantie kunt aanpassen.

* Clientlibs

   Clientlibs staan u toe om de standaardimplementatie uit te breiden om nieuwe functionaliteit te realiseren, terwijl het hergebruiken van de standaardfuncties, de voorwerpen, en de methodes. Wanneer het aanpassen, kunt u uw eigen clientlib onder `/apps.` tot stand brengen de nieuwe clientlib moet:

   * afhankelijk zijn van de creatieve clientlib `cq.authoring.editor.sites.page`
   * deel uitmaken van de desbetreffende categorie `cq.authoring.editor.sites.page.hook`

* Bedekkingen

   Bedekkingen zijn gebaseerd op knooppuntdefinities en staan u toe om de standaardfunctionaliteit (in `/libs`) met uw eigen aangepaste functionaliteit (in `/apps`) te bedekken. Bij het maken van een overlay is een 1:1-kopie van het origineel niet vereist, omdat de [sling resource merge](/help/sites-developing/sling-resource-merger.md) overerving toestaat.

>[!NOTE]
>
>Zie de [JS-documentatieset](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/jsdoc/ui-touch/editor-core/index.html) voor meer informatie.

Deze kunnen op verschillende manieren worden gebruikt om de functionaliteit voor het schrijven van pagina&#39;s in uw AEM uit te breiden. Een selectie wordt hieronder behandeld (op een hoog niveau).

>[!NOTE]
>
>Zie voor meer informatie:
>
>* Het gebruiken en het creëren van [clientlibs](/help/sites-developing/clientlibs.md).
>* [overlays](/help/sites-developing/overlays.md) gebruiken en maken.
>* [Graniet](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/index.html)
>* [Structuur van de ](/help/sites-developing/touch-ui-structure.md) UI voor het maken van AEM aanraakfuncties voor meer informatie over de structurele gebieden die worden gebruikt voor het ontwerpen van pagina&#39;s.

>
>Dit onderwerp wordt ook behandeld in [AEM Gems](https://docs.adobe.com/content/ddc/en/gems.html) zitting - [Gebruikersinterfaceaanpassing voor AEM 6.0](https://helpx.adobe.com/experience-manager/kt/eseminars/gems/aem-user-interface-customization-for-aem6.html).

>[!CAUTION]
>
>U ***must*** verandert niets in `/libs` weg.
>
>Dit komt doordat de inhoud van `/libs` de volgende keer wordt overschreven dat u uw exemplaar bijwerkt (en dat kan worden overschreven wanneer u een hotfix- of functiepakket toepast).
>
>De aanbevolen methode voor configuratie en andere wijzigingen is:
>
>1. Het vereiste item opnieuw maken (dat wil zeggen zoals het bestaat in `/libs`) onder `/apps`
>1. Wijzigingen aanbrengen binnen `/apps`


## Nieuwe laag toevoegen (modus) {#add-new-layer-mode}

Wanneer u een pagina bewerkt, zijn er verschillende [modi](/help/sites-authoring/author-environment-tools.md#page-modes) beschikbaar. Deze modi worden geïmplementeerd met behulp van [layers](/help/sites-developing/touch-ui-structure.md#layer). Hiermee hebt u toegang tot verschillende typen functionaliteit voor dezelfde pagina-inhoud. De standaardlagen zijn: bewerken, voorvertonen, notities aanbrengen, ontwikkelen en aanwijzen.

### Voorbeeld van laag: Status van live kopiëren {#layer-example-live-copy-status}

Een standaard AEM instantie verstrekt de laag MSM. Hiermee krijgt u toegang tot gegevens met betrekking tot [beheer op meerdere locaties](/help/sites-administering/msm.md) en markeert u deze in de laag.

Om het in actie te zien kunt u om het even welke [Wij.Retail taalexemplaar](/help/sites-developing/we-retail-globalized-site-structure.md) pagina (of een andere levende exemplaarpagina) uitgeven en **Live de Status van het Exemplaar** wijze selecteren.

U kunt de MSM laagdefinitie (voor verwijzing) vinden in:

`/libs/wcm/msm/content/touch-ui/authoring/editor/js/msm.Layer.js`

### Codevoorbeeld {#code-sample}

Dit is een steekproefpakket dat toont hoe te om een nieuwe laag (wijze) tot stand te brengen, die een nieuwe laag voor mening MSM is.

CODE VOOR GITHUB

U kunt de code van deze pagina op GitHub vinden

* [Open aem-creatie-nieuw-laag-wijze project op GitHub](https://github.com/Adobe-Marketing-Cloud/aem-authoring-new-layer-mode)
* Het project downloaden als [een ZIP-bestand](https://github.com/Adobe-Marketing-Cloud/aem-authoring-new-layer-mode/archive/master.zip)

## Nieuwe selectiecategorie toevoegen aan de middelenbrowser {#add-new-selection-category-to-asset-browser}

In de middelenbrowser worden elementen van verschillende typen/categorieën weergegeven (bijvoorbeeld afbeeldingen, documenten, enz.). De activa kunnen ook door deze activacategorieën worden gefiltreerd.

### Codevoorbeeld {#code-sample-1}

`aem-authoring-extension-assetfinder-flickr` Dit is een voorbeeldpakket dat aangeeft hoe u een nieuwe groep aan de zoeker van elementen kunt toevoegen. Dit voorbeeld verbindt met [de openbare stroom van Flickr](https://www.flickr.com) en toont hen in sidepanel.

CODE VOOR GITHUB

U kunt de code van deze pagina op GitHub vinden

* [Open aem-authoring-extension-assetfinder-flickr project op GitHub](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-assetfinder-flickr)
* Het project downloaden als [een ZIP-bestand](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-assetfinder-flickr/archive/master.zip)

## Bronnen filteren {#filtering-resources}

Bij het ontwerpen van pagina&#39;s moet de gebruiker vaak bronnen selecteren (zoals pagina&#39;s, componenten, elementen, enz.). Dit kan de vorm hebben van een lijst, bijvoorbeeld van waaruit de auteur een punt moet kiezen.

Om de lijst tot een redelijke grootte te houden en ook relevant voor het gebruiksgeval, kan een filter in de vorm van een douane predikaat worden uitgevoerd. Als bijvoorbeeld de [`pathbrowser`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/index.html) [Granite](/help/sites-developing/touch-ui-concepts.md#granite-ui) component wordt gebruikt om de gebruiker toe te staan het pad naar een bepaalde bron te selecteren, kunnen de voorgestelde paden op de volgende manier worden gefilterd:

* Implementeer de aangepaste voorspelling door de interface [`com.day.cq.commons.predicate.AbstractNodePredicate`](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/predicate/package-summary.html) te implementeren.
* Geef een naam voor de voorspelling op en verwijs deze naam bij gebruik van de `pathbrowser`.

Zie [dit artikel](/help/sites-developing/implementing-custom-predicate-evaluator.md) voor meer informatie over het maken van een aangepaste voorspelling.

>[!NOTE]
>
>Het uitvoeren van een douanevoorspelling door `com.day.cq.commons.predicate.AbstractNodePredicate` interface uit te voeren werkt ook in klassieke UI.
>
>Zie [dit kennisbasisartikel](https://helpx.adobe.com/experience-manager/using/creating-custom-cq-tree.html) voor een voorbeeld van het uitvoeren van een douanevoorspelling in klassieke UI.

## Nieuwe handeling toevoegen aan werkbalk Component {#add-new-action-to-a-component-toolbar}

Elke component (gewoonlijk) heeft een werkbalk die toegang biedt tot een reeks handelingen die op die component kunnen worden uitgevoerd.

### Codevoorbeeld {#code-sample-2}

`aem-authoring-extension-toolbar-screenshot` Dit is een voorbeeldpakket dat laat zien hoe u een aangepaste werkbalkactie maakt om componenten te renderen.

CODE VOOR GITHUB

U kunt de code van deze pagina op GitHub vinden

* [Open aem-authoring-extension-toolbar-screenshot project op GitHub](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-toolbar-screenshot)
* Het project downloaden als [een ZIP-bestand](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-toolbar-screenshot/archive/master.zip)

## Nieuwe op-plaats-editor toevoegen {#add-new-in-place-editor}

### Standaardeditor {#standard-in-place-editor}

In een standaard AEM-installatie:

1. `/libs/cq/gui/components/authoring/editors/clientlibs/core/js/editors/editorExample.js`

   Bevat definities van de verschillende beschikbare editors.

1. Er is een verbinding tussen de redacteur en elk middeltype (zoals in component) dat het kan gebruiken:

   * `cq:inplaceEditing`

      bijvoorbeeld:

      * `/libs/foundation/components/text/cq:editConfig`
      * `/libs/foundation/components/image/cq:editConfig`

         * eigenschap: `editorType`

            Bepaalt het type van gealigneerde redacteur die zal worden gebruikt wanneer het op zijn plaats uitgeven voor die component wordt teweeggebracht; bijv. `text`, `textimage`, `image`, `title`.

1. De extra configuratiedetails van de redacteur kunnen worden gevormd gebruikend een `config` knoop die configuraties evenals een verdere `plugin` knoop bevat om noodzakelijke plugin configuratiedetails te bevatten.

   Hieronder ziet u een voorbeeld van het definiëren van hoogte-breedteverhoudingen voor de uitsnijdplug-in van de afbeeldingscomponent. De hoogte-breedteverhouding van het uitsnijdvak is vanwege de mogelijkheid van een zeer beperkte schermgrootte verplaatst naar de volledige schermeditor en kan daar alleen worden weergegeven.

   ```xml
   <cq:inplaceEditing
           jcr:primaryType="cq:InplaceEditingConfig"
           active="{Boolean}true"
           editorType="image">
           <config jcr:primaryType="nt:unstructured">
               <plugins jcr:primaryType="nt:unstructured">
                   <crop jcr:primaryType="nt:unstructured">
                       <aspectRatios jcr:primaryType="nt:unstructured">
                           <_x0031_6-10
                               jcr:primaryType="nt:unstructured"
                               name="16 : 10"
                               ratio="0.625"/>
                       </aspectRatios>
                   </crop>
               </plugins>
           </config>
   </cq:inplaceEditing>
   ```

   >[!CAUTION]
   >
   >In AEM uitsnijdverhoudingen, zoals ingesteld door de eigenschap `ratio`, worden gedefinieerd als **height/width**. Dit verschilt van de conventionele definitie van breedte/hoogte en wordt gedaan om oude compatibiliteitsredenen. De auteursgebruikers zullen zich van geen verschil bewust zijn op voorwaarde dat u het `name` bezit duidelijk bepaalt aangezien dit is wat in UI wordt getoond.

#### Een nieuwe plaatseditor maken {#creating-a-new-in-place-editor}

Om een nieuwe op zijn plaats redacteur (binnen uw clientlib) uit te voeren:

>[!NOTE]
>
>Zie bijvoorbeeld:
>`/libs/cq/gui/components/authoring/editors/clientlibs/core/js/editors/editorExample.js`

1. Implementeren:

   * `setUp`
   * `tearDown`

1. Registreer de editor (inclusief de constructor):

   * `editor.register`

1. Verstrek de verbinding tussen de redacteur en elk middeltype (zoals in component) dat het kan gebruiken.

#### Codevoorbeeld voor het maken van een nieuwe plaatseditor {#code-sample-for-creating-a-new-in-place-editor}

`aem-authoring-extension-inplace-editor` Dit is een voorbeeldpakket waarin wordt getoond hoe u een nieuwe interne editor in AEM kunt maken.

CODE VOOR GITHUB

U kunt de code van deze pagina op GitHub vinden

* [Open aem-authoring-extension-inplace-editor project op GitHub](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-inplace-editor)
* Het project downloaden als [een ZIP-bestand](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-inplace-editor/archive/master.zip)

#### Meerdere lokale editors configureren {#configuring-multiple-in-place-editors}

Het is mogelijk om een component te vormen zodat het veelvoudige op zijn plaats redacteurs heeft. Wanneer er meerdere editors op locatie zijn geconfigureerd, kunt u de juiste inhoud selecteren en de juiste editor openen. Zie [Veelvoudige In-Place Redacteurs](/help/sites-developing/multiple-inplace-editors.md) documentatie voor meer informatie vormen.

## Handeling Nieuwe pagina toevoegen {#add-a-new-page-action}

Om een nieuwe paginaactie aan de paginagtoolbar toe te voegen, bijvoorbeeld een **Terug naar Plaatsen** (console) actie.

### Codevoorbeeld {#code-sample-3}

`aem-authoring-extension-header-backtosites` is een voorbeeldpakket dat toont hoe te om een actie van de douanekopbalbar tot stand te brengen om terug naar de console van Plaatsen te springen.

CODE VOOR GITHUB

U kunt de code van deze pagina op GitHub vinden

* [Open aem-authoring-extension-header-backtosites project op GitHub](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-header-backtosites)
* Het project downloaden als [een ZIP-bestand](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-header-backtosites/archive/master.zip)

## De workflow voor het aanvragen van activering aanpassen {#customizing-the-request-for-activation-workflow}

De out-of-the-box workflow, **Verzoek om activering**:

* Wordt automatisch weergegeven in het juiste menu wanneer een auteur van inhoud **niet over** de juiste replicatierechten beschikt, maar **wel** lidmaatschap van DAM-Users en Auteurs heeft.

* Anders wordt er niets weergegeven, omdat de replicatierechten zijn verwijderd.

Als u op deze activering een aangepast gedrag wilt toepassen, kunt u de **Verzoek om activering**-workflow bedekken:

1. In `/apps` bedek de wizard **Sites**:

   `/libs/wcm/core/content/common/managepublicationwizard`

   >[!NOTE]
   >
   >Dit zelf, treedt het gemeenschappelijke geval van met voeten:
   >
   >`/libs/cq/gui/content/common/managepublicationwizard`

1. Werk het [workflowmodel](/help/sites-developing/workflows-models.md) en de bijbehorende configuraties/scripts naar wens bij.
1. Het recht op de [ `replicate` actie](/help/sites-administering/security.md#actions) van alle relevante gebruikers voor alle relevante pagina&#39;s verwijderen; om deze workflow als een standaardactie te laten activeren wanneer een van de gebruikers een pagina probeert te publiceren (of te repliceren).
