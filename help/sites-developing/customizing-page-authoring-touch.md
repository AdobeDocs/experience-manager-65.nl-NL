---
title: Paginaontwerp aanpassen
description: Adobe Experience Manager (AEM) biedt verschillende mechanismen waarmee u de functionaliteit voor het schrijven van pagina's kunt aanpassen.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
exl-id: 90594588-db8e-4d4c-a208-22c1c6ea2a2d
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 3aa55b88f589749fb49d5ff46340b0912d490157
workflow-type: tm+mt
source-wordcount: '1264'
ht-degree: 0%

---

# Paginaontwerp aanpassen{#customizing-page-authoring}

>[!CAUTION]
>
>In dit document wordt beschreven hoe u het ontwerpen van pagina&#39;s kunt aanpassen in de moderne interface met aanraakbediening. Dit document is niet van toepassing op de klassieke gebruikersinterface.

Adobe Experience Manager (AEM) verstrekt diverse mechanismen om u de pagina auteursfunctionaliteit (en de [ consoles ](/help/sites-developing/customizing-consoles-touch.md)) van uw auteursinstantie te laten aanpassen.

* Clientlibs

  Clientlibs laten u de standaardimplementatie uitbreiden om nieuwe functionaliteit te realiseren, terwijl het hergebruiken van de standaardfuncties, de voorwerpen, en de methodes. Bij het aanpassen kunt u uw eigen clientlib maken onder `/apps.` De nieuwe clientlib moet:

   * zijn afhankelijk van de client-client voor het schrijven van programmacode `cq.authoring.editor.sites.page`
   * deel uitmaken van de juiste categorie `cq.authoring.editor.sites.page.hook`

* Bedekkingen

  Bedekkingen zijn gebaseerd op knooppuntdefinities en u kunt de standaardfunctionaliteit (in `/libs` ) bedekken met uw eigen aangepaste functionaliteit (in `/apps` ). Wanneer het creëren van een bekleding wordt een 1:1 exemplaar van origineel niet vereist, aangezien de [ dalende middelfusie ](/help/sites-developing/sling-resource-merger.md) voor overerving toestaat.

>[!NOTE]
>
>Voor meer informatie, zie [ JS documentatiereeks ](https://developer.adobe.com/experience-manager/reference-materials/6-5/jsdoc/ui-touch/editor-core/index.html).

Deze kunnen op verschillende manieren worden gebruikt om de functionaliteit voor het schrijven van pagina&#39;s in uw AEM uit te breiden. Een selectie wordt hieronder behandeld (op een hoog niveau).

>[!NOTE]
>
>Zie het volgende voor meer informatie:
>
>* Het gebruiken van en het creëren van [ clientlibs ](/help/sites-developing/clientlibs.md).
>* Het gebruiken van en het creëren van [ bekledingen ](/help/sites-developing/overlays.md).
>* [ Graniet ](https://developer.adobe.com/experience-manager/reference-materials/6-5/granite-ui/api/jcr_root/libs/granite/ui/index.html)
>* [ Structuur van de AEM aanraking-Toegelaten UI ](/help/sites-developing/touch-ui-structure.md) voor details van de structurele gebieden die voor paginaontwerp worden gebruikt.
>


>[!CAUTION]
>
>**&#x200B;**&#x200B;** verander niets in de `/libs` weg.
>
>De reden hiervoor is dat de inhoud van `/libs` wordt overschreven, de volgende keer dat u een upgrade uitvoert van uw exemplaar (en dat u deze mogelijk overschrijft wanneer u een hotfix- of functiepakket toepast).
>
>De aanbevolen methode voor configuratie en andere wijzigingen is:
>
>1. Het vereiste item opnieuw maken (dat wil zeggen, zoals het in `/libs` staat) onder `/apps`
>1. Breng eventuele wijzigingen aan binnen `/apps`

## Nieuwe laag toevoegen (modus) {#add-new-layer-mode}

Wanneer u een pagina uitgeeft, zijn er diverse [ beschikbare wijzen ](/help/sites-authoring/author-environment-tools.md#page-modes). Deze wijzen worden uitgevoerd gebruikend [ lagen ](/help/sites-developing/touch-ui-structure.md#layer). Hiermee hebt u toegang tot verschillende typen functionaliteit voor dezelfde pagina-inhoud. De standaardlagen zijn: bewerken, voorvertonen, notities aanbrengen, ontwikkelaars en doelwitten.

### Voorbeeld van laag: status van actieve kopie {#layer-example-live-copy-status}

Een standaard AEM instantie verstrekt de laag MSM. Dit heeft toegang tot gegevens met betrekking tot [ multisite beheer ](/help/sites-administering/msm.md) en benadrukt het in de laag.

Om het in actie te zien, kunt u om het even welke [&#128279;](/help/sites-developing/we-retail-globalized-site-structure.md) pagina van het wij.Retail taalexemplaar  uitgeven (of een andere levende exemplaarpagina) en de **Levende wijze van de Status van het Exemplaar** selecteren.

U kunt de MSM laagdefinitie (voor verwijzing) vinden in:

`/libs/wcm/msm/content/touch-ui/authoring/editor/js/msm.Layer.js`

### Codevoorbeeld {#code-sample}

Dit is een steekproefpakket dat toont hoe te om een laag (wijze) tot stand te brengen, die een nieuwe laag voor mening MSM is.

CODE VOOR GITHUB

U kunt de code van deze pagina op GitHub vinden

* [ open aem-authoring-new-layer-mode project op GitHub ](https://github.com/Adobe-Marketing-Cloud/aem-authoring-new-layer-mode)
* Download het project als [ een dossier van het PIT ](https://github.com/Adobe-Marketing-Cloud/aem-authoring-new-layer-mode/archive/master.zip)

## Nieuwe selectiecategorie toevoegen aan de middelenbrowser {#add-new-selection-category-to-asset-browser}

In de middelenbrowser worden elementen van verschillende typen/categorieën weergegeven (bijvoorbeeld afbeeldingen en documenten). De activa kunnen ook door deze activacategorieën worden gefiltreerd.

### Codevoorbeeld {#code-sample-1}

`aem-authoring-extension-assetfinder-flickr` is een voorbeeldpakket dat aangeeft hoe u een groep aan de elementenzoeker kunt toevoegen. Dit voorbeeld verbindt met [ de openbare stroom van Flickr ](https://www.flickr.com) en toont hen in het zijpaneel.

CODE VOOR GITHUB

U kunt de code van deze pagina op GitHub vinden

* [ open aem-authoring-extension-assetfinder-flickr project op GitHub ](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-assetfinder-flickr)
* Download het project als [ een dossier van het PIT ](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-assetfinder-flickr/archive/master.zip)

## Bronnen filteren {#filtering-resources}

Bij het ontwerpen van pagina&#39;s moet de gebruiker vaak bronnen selecteren (bijvoorbeeld pagina&#39;s, componenten en elementen). Dit kan bijvoorbeeld de vorm aannemen van een lijst waaruit de auteur een item moet kiezen.

Om de lijst tot een redelijke grootte en ook relevant voor het gebruiksgeval te houden, kan een filter in de vorm van een douanevoorspelling worden uitgevoerd. Bijvoorbeeld, als de [`pathbrowser` ](https://developer.adobe.com/experience-manager/reference-materials/6-5/granite-ui/api/jcr_root/libs/granite/ui/index.html) [ graniet ](/help/sites-developing/touch-ui-concepts.md#granite-ui) component wordt gebruikt om de gebruiker toe te staan om de weg aan een bepaald middel te selecteren, kunnen de voorgestelde wegen op de volgende manier worden gefiltreerd:

* Implementeer de aangepaste voorspelling door de [`com.day.cq.commons.predicate.AbstractNodePredicate` ](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/commons/predicate/package-summary.html) -interface te implementeren.
* Geef een naam voor de voorspelling op en verwijs die naam wanneer u de voorspelling van `pathbrowser` gebruikt.

Voor verder detail bij het creëren van een douane predikaat, zie [ Uitvoerend een Evaluator van de Predicate van de Douane voor de Bouwer van de Vraag ](/help/sites-developing/implementing-custom-predicate-evaluator.md).

>[!NOTE]
>
>Het implementeren van een aangepaste voorspelling door het implementeren van een `com.day.cq.commons.predicate.AbstractNodePredicate` -interface werkt ook in de klassieke UI.
>
>Zie [ dit artikel van de kennisbasis ](https://helpx.adobe.com/experience-manager/using/creating-custom-cq-tree.html) voor een voorbeeld om een douane uit te voeren predikt in klassieke UI.

## Nieuwe handeling toevoegen aan werkbalk Component {#add-new-action-to-a-component-toolbar}

Elke component (gewoonlijk) heeft een werkbalk die toegang biedt tot een reeks handelingen die op die component kunnen worden uitgevoerd.

### Codevoorbeeld {#code-sample-2}

`aem-authoring-extension-toolbar-screenshot` is een voorbeeldpakket dat aangeeft hoe u een aangepaste werkbalkactie kunt maken om componenten te renderen.

CODE VOOR GITHUB

U kunt de code van deze pagina op GitHub vinden

* [ open aem-auteurs-uitbreiding-toolbar-screenshot project op GitHub ](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-toolbar-screenshot)
* Download het project als [ een dossier van het PIT ](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-toolbar-screenshot/archive/master.zip)

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

           Definieert het type inline-editor dat wordt gebruikt wanneer de bewerking op plaats wordt geactiveerd voor die component, bijvoorbeeld `text` , `textimage` , `image` , `title` .

1. Aanvullende configuratiedetails van de editor kunnen worden geconfigureerd met een `config` -knooppunt met configuraties en een `plugin` -knooppunt voor de benodigde insteekconfiguratiedetails.

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
   >AEM gewassenverhoudingen, zoals die door het `ratio` bezit worden geplaatst, worden bepaald als **hoogte/breedte**. Dit verschilt van de conventionele definitie van breedte/hoogte en wordt gedaan om oude compatibiliteitsredenen. De ontwerpgebruikers zijn zich niet bewust van enig verschil op voorwaarde dat u de eigenschap `name` duidelijk definieert, aangezien dit is wat wordt weergegeven in de gebruikersinterface.

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

`aem-authoring-extension-inplace-editor` is een voorbeeldpakket waarin wordt getoond hoe u een lokale editor in AEM kunt maken.

CODE VOOR GITHUB

U kunt de code van deze pagina op GitHub vinden

* [ open aem-authoring-extension-inplace-redacteursproject op GitHub ](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-inplace-editor)
* Download het project als [ een dossier van het PIT ](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-inplace-editor/archive/master.zip)

#### Meerdere lokale editors configureren {#configuring-multiple-in-place-editors}

Het is mogelijk om een component te vormen zodat het veelvoudige op zijn plaats redacteurs heeft. Wanneer er meerdere editors op locatie zijn geconfigureerd, kunt u de juiste inhoud selecteren en de juiste editor openen. Zie [ het Vormen Veelvoudige In-Place documentatie van Editors ](/help/sites-developing/multiple-inplace-editors.md) voor meer informatie.

## Handeling Nieuwe pagina toevoegen {#add-a-new-page-action}

Om een nieuwe paginaactie aan de paginatoolbar toe te voegen, bijvoorbeeld, a **terug naar Plaatsen** (console) actie.

### Codevoorbeeld {#code-sample-3}

`aem-authoring-extension-header-backtosites` is een voorbeeldpakket waarin wordt getoond hoe u een aangepaste actie voor de koptekstbalk kunt maken om terug te gaan naar de Sites-console.

CODE VOOR GITHUB

U kunt de code van deze pagina op GitHub vinden

* [ open aem-authoring-extension-header-backtosites project op GitHub ](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-header-backtosites)
* Download het project als [ een dossier van het PIT ](https://github.com/Adobe-Marketing-Cloud/aem-authoring-extension-header-backtosites/archive/master.zip)

## De workflow voor het aanvragen van activering aanpassen {#customizing-the-request-for-activation-workflow}

Het uit-van-de-dooswerkschema, **Verzoek om Activering**:

* Zal automatisch op het aangewezen menu verschijnen wanneer een inhoudsauteur **&#x200B;**&#x200B;niet de aangewezen replicatierechten heeft, maar **heeft** lidmaatschap van DAM-Gebruikers en Auteurs.

* Anders wordt er niets weergegeven, omdat de replicatierechten zijn verwijderd.

Om aangepast gedrag op dergelijke activering te hebben, kunt u het **Verzoek om het werkschema van de Activering** bedekken:

1. In `/apps` bedekking de **2&rbrace; tovenaar van Plaatsen &lbrace;:**

   `/libs/wcm/core/content/common/managepublicationwizard`

   >[!NOTE]
   >
   >Dit zelf, treedt het gemeenschappelijke geval van met voeten:
   >
   >`/libs/cq/gui/content/common/managepublicationwizard`

1. Werk het [ werkschemamodel ](/help/sites-developing/workflows-models.md) en verwante configuraties/manuscripten zoals vereist bij.
1. Verwijder het recht op de [`replicate` actie ](/help/sites-administering/security.md#actions) van alle aangewezen gebruikers voor alle relevante pagina&#39;s; om dit werkschema als standaardactie teweeggebracht te hebben wanneer om het even welke gebruikers proberen om een pagina te publiceren (of te herhalen).
