---
title: Gebruik van CIF-product en rubriekkiezer
description: Leer hoe te om het product en de categoriekiezer van CIF in uw componenten van de klantenhandel te gebruiken om auteurs en verkopers te steunen om met handelsproduct en catalogusgegevens efficiënt te werken.
sub-product: Handel
topics: Development
version: cloud-service
activity: develop
audience: developer
feature: Kader voor integratie in de handel
source-git-commit: d84993e704096eabe85c4d4d61e24096d15ae9bd
workflow-type: tm+mt
source-wordcount: '579'
ht-degree: 0%

---

# AEM Content &amp; Commerce Authoring Pickers {#cif-pickers}

AEM Content &amp; Commerce Authoring biedt een reeks ontwerpgereedschappen waarmee AEM auteurs en marketers efficiënt kunnen werken met handelsproductgegevens en -catalogi. De productkiezer en de categoriekiezer maken deel uit van de CIF-invoegtoepassing en worden gebruikt door de CIF Core-componenten. Projecten kunnen deze kiezers in elk dialoogvenster gebruiken om producten of categorieën te selecteren.

## Productkiezer {#product-picker}

Om de productkiezer in een projectcomponent te gebruiken moet een ontwikkelaar `commerce/gui/components/common/cifproductfield` aan een componentendialoog toevoegen. Gebruik bijvoorbeeld het volgende voor het dialoogvenster cq:dialog:

```xml
<product jcr:primaryType="nt:unstructured"
    sling:resourceType="commerce/gui/components/common/cifproductfield"
    fieldDescription="The product or product variant displayed by the teaser"
    fieldLabel="Select Product"
    filter="folderOrProductOrVariant"
    name="./selection"
    selectionId="sku"/>
```

In het productveld kan worden genavigeerd naar het product dat een gebruiker wil selecteren via de verschillende weergaven. Door gebrek keert het productgebied identiteitskaart van het product terug, maar het kan worden gevormd gebruikend het `selectionId` attribuut.

Het veld Productkiezer ondersteunt de volgende optionele eigenschappen:

- selectionId (id, uid, sku, slug, gecombineerdeSlug, CombinationSku) - maakt het mogelijk het productkenmerk te kiezen dat door de kiezer moet worden geretourneerd (standaard = id). Het gebruiken van sku keert de sku van het geselecteerde product terug, terwijl het gebruiken van compiledSku en keert een koord als base#variant met de skus van het basisproduct en de geselecteerde variant, of één enkele sku terug als een basisproduct wordt geselecteerd.
- filter (folderOrProduct, folderOrProductOrVariant) - filtert de inhoud die door de kiezer moet worden gerenderd tijdens het navigeren in de productstructuur. folderOrProduct - rendert mappen en producten. folderOrProductOrVariant - geeft omslagen, product en productvarianten terug. Als een product of productvariant wordt weergegeven, wordt deze ook selecteerbaar in de kiezer. (standaard = folderOrProduct)
- meerdere (true, false) - de selectie van een of meerdere producten inschakelen (standaard = false)
- emptyText - om de lege tekstwaarde van het plukkerveld te vormen

Ook worden standaardeigenschappen van diagramvelden zoals `name`, `fieldLabel` of `fieldDescription` ondersteund.

>[!CAUTION]
>
>De `cifproductfield` component vereist `cif.shell.picker` cliëntlib. Als u een clientlib aan een dialoogvenster wilt toevoegen, kunt u de eigenschap extraClientlibs gebruiken.

Een volledig werkend voorbeeld van `cifproductfield` kan in [CIF de Componenten van de Kern worden gevonden](https://github.com/adobe/aem-core-cif-components/blob/master/ui.apps/src/main/content/jcr_root/apps/core/cif/components/commerce/productteaser/v1/productteaser/_cq_dialog/.content.xml) project. Zie ook [Dialoogvensters aanpassen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/customizing.html?lang=en#customizing-dialogs) van de documentatie van de Componenten van de AEMKern.

## Categoriekiezer {#category-picker}

De categoriekiezer kan ook in een componentdialoogvenster worden gebruikt, net als de productkiezer.

Het volgende fragment kan in een cq:dialog-configuratie worden gebruikt:

```xml
<category jcr:primaryType="nt:unstructured" 
    sling:resourceType="commerce/gui/components/common/cifcategoryfield" 
    fieldLabel="Category" 
    name="./categoryId" 
    selectionId="uid" />
```

Het veld Categoriekiezer ondersteunt de volgende optionele eigenschappen:

- selectionId(id, uid, slug, idAndUrlPath, uidAndUrlPath) - staat toe om het categoriekenmerk te kiezen dat door de plukker moet worden teruggekeerd (gebrek = id). De idAndUrlPath &amp; uidAndUrlPath zijn speciale opties die de categorie id/uid en url_path opslaan, gescheiden door een | personage zoals bijvoorbeeld 1|mannen/toppen.
- meerdere (true, false) - de selectie van een of meerdere categorieën inschakelen (standaard = false)

Ook worden standaardeigenschappen van diagramvelden zoals `name`, `fieldLabel` of `fieldDescription` ondersteund.

>[!CAUTION]
>
>Hetzelfde als de `cifproductfield`-component vereist de `cifcategoryfield`-component ook de `cif.shell.picker`-client. Als u een client aan een dialoogvenster wilt toevoegen, kunt u de eigenschap `extraClientlibs` gebruiken. Zie [Dialoogvensters aanpassen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/customizing.html?lang=en#customizing-dialogs) van de documentatie van de Componenten van de AEMKern.

Een volledig werkend voorbeeld van `cifcategoryfield` kan in [CIF de Componenten van de Kern worden gevonden](https://github.com/adobe/aem-core-cif-components/blob/master/ui.apps/src/main/content/jcr_root/apps/core/cif/components/commerce/featuredcategorylist/v1/featuredcategorylist/_cq_dialog/.content.xml) project.
