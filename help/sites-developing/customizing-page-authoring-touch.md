---
title: Paginaontwerp aanpassen
description: Adobe Experience Manager (AEM) biedt verschillende mechanismen waarmee u de functionaliteit voor het schrijven van pagina's kunt aanpassen.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
exl-id: 90594588-db8e-4d4c-a208-22c1c6ea2a2d
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1257'
ht-degree: 0%

---

# Paginaontwerp aanpassen{#customizing-page-authoring}

>[!CAUTION]
>
>In dit document wordt beschreven hoe u het ontwerpen van pagina&#39;s kunt aanpassen in de moderne interface met aanraakbediening. Dit document is niet van toepassing op de klassieke gebruikersinterface.

Adobe Experience Manager (AEM) biedt verschillende mechanismen waarmee u de functionaliteit voor het schrijven van pagina&#39;s (en de [consoles](/help/sites-developing/customizing-consoles-touch.md)) van de ontwerpinstantie.

* Clientlibs

  Clientlibs laten u de standaardimplementatie uitbreiden om nieuwe functionaliteit te realiseren, terwijl het hergebruiken van de standaardfuncties, de voorwerpen, en de methodes. Bij het aanpassen kunt u uw eigen clientlib maken onder `/apps.` De nieuwe client moet:

   * afhankelijk van de creatie clientlib `cq.authoring.editor.sites.page`
   * deel uitmaken van de passende `cq.authoring.editor.sites.page.hook` categorie

* Bedekkingen

  Bedekkingen zijn gebaseerd op knooppuntdefinities en laten u de standaardfunctionaliteit bedekken (in `/libs`) met uw eigen aangepaste functionaliteit (in `/apps`). Bij het maken van een bedekking is een 1:1-kopie van het origineel niet vereist, omdat de optie [fusie van bronnen](/help/sites-developing/sling-resource-merger.md) staat overerving toe.

>[!NOTE]
>
>Zie voor meer informatie [JS-documentatieset](https://developer.adobe.com/experience-manager/reference-materials/6-5/jsdoc/ui-touch/editor-core/index.html).

Deze kunnen op verschillende manieren worden gebruikt om de functionaliteit voor het schrijven van pagina&#39;s in uw AEM uit te breiden. Een selectie wordt hieronder behandeld (op een hoog niveau).

>[!NOTE]
>
>Zie het volgende voor meer informatie:
>
>* Gebruiken en maken [clientlibs](/help/sites-developing/clientlibs.md).
>* Gebruiken en maken [bedekkingen](/help/sites-developing/overlays.md).
>* [Graniet](https://developer.adobe.com/experience-manager/reference-materials/6-5/granite-ui/api/jcr_root/libs/granite/ui/index.html)
>* [Structuur van de interface voor AEM aanraakbediening](/help/sites-developing/touch-ui-structure.md) voor meer informatie over de structuurgebieden die worden gebruikt voor het ontwerpen van pagina&#39;s.
>


>[!CAUTION]
>
>***Niet gebruiken*** om het even wat in `/libs` pad.
>
>De reden is dat de inhoud van `/libs` wordt overschreven, de volgende keer u uw exemplaar (en kan goed worden beschreven wanneer u of hotfix of eigenschapspak toepast) bevordert.
>
>De aanbevolen methode voor configuratie en andere wijzigingen is:
>
>1. Het vereiste item opnieuw maken (dat wil zeggen, zoals het bestaat in `/libs`) onder `/apps`
>1. Breng wijzigingen aan in `/apps`

## Nieuwe laag toevoegen (modus) {#add-new-layer-mode}

Wanneer u een pagina bewerkt, zijn er verschillende [modi](/help/sites-authoring/author-environment-tools.md#page-modes) beschikbaar. Deze modi worden geïmplementeerd met [lagen](/help/sites-developing/touch-ui-structure.md#layer). Hiermee hebt u toegang tot verschillende typen functionaliteit voor dezelfde pagina-inhoud. De standaardlagen zijn: bewerken, voorvertonen, notities aanbrengen, ontwikkelaars en doelwitten.

### Voorbeeld van laag: status van actieve kopie {#layer-example-live-copy-status}

Een standaard AEM instantie verstrekt de laag MSM. Hiermee krijgt u toegang tot gegevens die betrekking hebben op [multisite beheer](/help/sites-administering/msm.md) en markeert deze in de laag.

Als u het wilt zien in actie, kunt u [We.Kopie in de detailhandel](/help/sites-developing/we-retail-globalized-site-structure.md) pagina (of een andere live kopiëren pagina) en selecteer de **Status van live kopiëren** -modus.

U kunt de MSM laagdefinitie (voor verwijzing) vinden in:

`/libs/wcm/msm/content/touch-ui/authoring/editor/js/msm.Layer.js`

### Codevoorbeeld {#code-sample}

Dit is een steekproefpakket dat toont hoe te om een laag (wijze) tot stand te brengen, die een nieuwe laag voor mening MSM is.

CODE VOOR GITHUB

U kunt de code van deze pagina op GitHub vinden

* [Open aem-creatie-nieuw-laag-wijze project op GitHub](https://github.com/Adobe-Marketing-Cloud/aem-authoring-new-layer-mode)
* Het project downloaden als [een ZIP-bestand](https://github.com/Adobe-Marketing-Cloud/aem-authoring-new-layer-mode/archive/master.zip)

## Nieuwe selectiecategorie toevoegen aan de middelenbrowser {#add-new-selection-category-to-asset-browser}

In de middelenbrowser worden elementen van verschillende typen/categorieën weergegeven (bijvoorbeeld afbeeldingen en documenten). De activa kunnen ook door deze activacategorieën worden gefiltreerd.

### Codevoorbeeld {#code-sample-1}

`aem-authoring-extension-assetfinder-flickr` Dit is een voorbeeldpakket dat aangeeft hoe u een groep aan de zoeker van middelen kunt toevoegen. Dit voorbeeld maakt verbinding met [Flickr](https://www.flickr.com)s public stream en toont deze in het zijpaneel.

CODE VOOR GITHUB

U kunt de code van deze pagina op GitHub vinden

* [Open aem-authoring-extension-assetfinder-flickr project op GitHub](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-assetfinder-flickr)
* Het project downloaden als [een ZIP-bestand](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-assetfinder-flickr/archive/master.zip)

## Bronnen filteren {#filtering-resources}

Bij het ontwerpen van pagina&#39;s moet de gebruiker vaak bronnen selecteren (bijvoorbeeld pagina&#39;s, componenten en elementen). Dit kan bijvoorbeeld de vorm aannemen van een lijst waaruit de auteur een item moet kiezen.

Om de lijst tot een redelijke grootte en ook relevant voor het gebruiksgeval te houden, kan een filter in de vorm van een douanevoorspelling worden uitgevoerd. Als de [`pathbrowser`](https://developer.adobe.com/experience-manager/reference-materials/6-5/granite-ui/api/jcr_root/libs/granite/ui/index.html) [Graniet](/help/sites-developing/touch-ui-concepts.md#granite-ui) wordt gebruikt om de gebruiker toe te staan om de weg aan een bepaalde middel te selecteren, kunnen de voorgestelde wegen op de volgende manier worden gefilterd:

* Implementeer de aangepaste voorspelling door deze te implementeren [`com.day.cq.commons.predicate.AbstractNodePredicate`](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/commons/predicate/package-summary.html) interface.
* Geef een naam voor de voorspelling op en verwijs deze naam naar het tabblad `pathbrowser`.

Zie voor meer informatie over het maken van een aangepaste predikaat [dit artikel](/help/sites-developing/implementing-custom-predicate-evaluator.md).

>[!NOTE]
>
>Een aangepaste voorspelling implementeren door `com.day.cq.commons.predicate.AbstractNodePredicate` de interface werkt ook in klassieke UI.
>
>Zie [dit kennisbasisartikel](https://helpx.adobe.com/experience-manager/using/creating-custom-cq-tree.html) voor een voorbeeld van het uitvoeren van een douane predikaat in klassieke UI.

## Nieuwe handeling toevoegen aan werkbalk Component {#add-new-action-to-a-component-toolbar}

Elke component (gewoonlijk) heeft een werkbalk die toegang biedt tot een reeks handelingen die op die component kunnen worden uitgevoerd.

### Codevoorbeeld {#code-sample-2}

`aem-authoring-extension-toolbar-screenshot` Dit is een voorbeeldpakket dat laat zien hoe u een aangepaste werkbalkactie maakt om componenten te renderen.

CODE VOOR GITHUB

U kunt de code van deze pagina op GitHub vinden

* [Open aem-authoring-extension-toolbar-screenshot project op GitHub](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-toolbar-screenshot)
* Het project downloaden als [een ZIP-bestand](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-toolbar-screenshot/archive/master.zip)

## Nieuwe plaatseditor toevoegen {#add-new-in-place-editor}

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

           Bepaalt het type van gealigneerde redacteur die wordt gebruikt wanneer het op zijn plaats uitgeven voor die component wordt teweeggebracht; bijvoorbeeld `text`, `textimage`, `image`, `title`.

1. De extra configuratiedetails van de redacteur kunnen worden gevormd gebruikend een `config` knooppunt met configuraties en een `plugin` -knooppunt voor de benodigde configuratiegegevens van de plug-in.

   Hieronder ziet u een voorbeeld van het definiëren van hoogte-breedteverhoudingen voor de uitsnijdplug-in van de afbeeldingscomponent. Vanwege de beperkte schermgrootte zijn de hoogte-breedteverhoudingen voor uitsnijden verplaatst naar de volledige schermeditor en kunnen deze alleen daar worden weergegeven.

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
   >Uitsnijdverhoudingen AEM, zoals ingesteld door de `ratio` eigenschap, worden gedefinieerd als **hoogte/breedte**. Dit verschilt van de conventionele definitie van breedte/hoogte en wordt gedaan om oude compatibiliteitsredenen. De gebruikers van de auteur zullen zich niet van enig verschil bewust zijn op voorwaarde dat u bepaalt `name` duidelijk bezit aangezien dit is wat in UI wordt getoond.

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

`aem-authoring-extension-inplace-editor` Dit is een voorbeeldpakket waarin wordt getoond hoe u een lokale editor in AEM kunt maken.

CODE VOOR GITHUB

U kunt de code van deze pagina op GitHub vinden

* [Open aem-authoring-extension-inplace-editor project op GitHub](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-inplace-editor)
* Het project downloaden als [een ZIP-bestand](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-inplace-editor/archive/master.zip)

#### Meerdere lokale editors configureren {#configuring-multiple-in-place-editors}

Het is mogelijk om een component te vormen zodat het veelvoudige op zijn plaats redacteurs heeft. Wanneer er meerdere editors op locatie zijn geconfigureerd, kunt u de juiste inhoud selecteren en de juiste editor openen. Zie de [Meerdere lokale editors configureren](/help/sites-developing/multiple-inplace-editors.md) documentatie voor meer informatie.

## Handeling Nieuwe pagina toevoegen {#add-a-new-page-action}

Als u een nieuwe paginahandeling wilt toevoegen aan de pagina-werkbalk, bijvoorbeeld een handeling **Terug naar sites** (console) handeling.

### Codevoorbeeld {#code-sample-3}

`aem-authoring-extension-header-backtosites` is een voorbeeldpakket dat toont hoe te om een actie van de douanekopbalbar tot stand te brengen om terug naar de console van Plaatsen te springen.

CODE VOOR GITHUB

U kunt de code van deze pagina op GitHub vinden

* [Open aem-authoring-extension-header-backtosites project op GitHub](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-header-backtosites)
* Het project downloaden als [een ZIP-bestand](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-header-backtosites/archive/master.zip)

## De workflow voor het aanvragen van activering aanpassen {#customizing-the-request-for-activation-workflow}

De workflow buiten de box, **Verzoek om activering**:

* Wordt automatisch weergegeven in het juiste menu wanneer een inhoudsauteur **heeft geen** de juiste replicatierechten, maar **heeft** lidmaatschap van DAM-gebruikers en auteurs.

* Anders wordt er niets weergegeven, omdat de replicatierechten zijn verwijderd.

Voor een aangepast gedrag bij een dergelijke activering kunt u de **Verzoek om activering** workflow:

1. In `/apps` bedekken de **Sites** wizard:

   `/libs/wcm/core/content/common/managepublicationwizard`

   >[!NOTE]
   >
   >Dit zelf, treedt het gemeenschappelijke geval van met voeten:
   >
   >`/libs/cq/gui/content/common/managepublicationwizard`

1. Werk de [workflowmodel](/help/sites-developing/workflows-models.md) en gerelateerde configuraties/scripts, indien vereist.
1. Rechts van de [`replicate` action](/help/sites-administering/security.md#actions) van alle relevante gebruikers voor alle relevante pagina&#39;s; om deze workflow als een standaardactie te laten activeren wanneer een van de gebruikers een pagina probeert te publiceren (of te repliceren).
