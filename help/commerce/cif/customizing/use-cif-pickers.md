---
title: Gebruik van CIF-product- en rubriekkiezer
description: Leer hoe u de product- en categoriekiezer van CIF in uw componenten voor klantenhandel gebruikt om auteurs en marketers te ondersteunen bij het efficiënt werken met product- en catalogusgegevens.
sub-product: Commerce
topics: Development
version: Experience Manager as a Cloud Service
activity: develop
audience: developer
feature: Commerce Integration Framework
exl-id: 1e7c3748-92b5-45f1-8dd9-f1816e3e34aa
solution: Experience Manager,Commerce
role: Admin, Developer
source-git-commit: a45b09c52d780a954e606d4cae73a3a02a8a6aa4
workflow-type: tm+mt
source-wordcount: '563'
ht-degree: 0%

---

# AEM Content &amp; Commerce Authoring Pickers {#cif-pickers}

AEM Content &amp; Commerce Authoring biedt een reeks ontwerpgereedschappen waarmee AEM-auteurs en -marketers efficiënt kunnen werken met handelsproductgegevens en -catalogi. De productkiezer en de rubriekkiezer maken deel uit van de invoegtoepassing CIF en worden gebruikt door de CIF Core-componenten. Projecten kunnen deze kiezers in elk dialoogvenster gebruiken om producten of categorieën te selecteren.

## Productkiezer {#product-picker}

Als u de productkiezer in een projectcomponent wilt gebruiken, moet een ontwikkelaar `commerce/gui/components/common/cifproductfield` aan een componentdialoogvenster toevoegen. Gebruik bijvoorbeeld het volgende voor de instructie `cq:dialog` :

```xml
<product jcr:primaryType="nt:unstructured"
    sling:resourceType="commerce/gui/components/common/cifproductfield"
    fieldDescription="The product or product variant displayed by the teaser"
    fieldLabel="Select Product"
    filter="folderOrProductOrVariant"
    name="./selection"
    selectionId="sku"/>
```

In het productveld kan worden genavigeerd naar het product dat een gebruiker wil selecteren op basis van de verschillende weergaven. Standaard retourneert het productveld de id van het product, maar het kan worden geconfigureerd met het kenmerk `selectionId` .

Het veld Productkiezer ondersteunt de volgende optionele eigenschappen:

- selectionId (id, uid, sku, slug, gecombineerdeSlug, gecombineerdeSku) - laat u het productkenmerk kiezen dat door de kiezer moet worden geretourneerd (gebrek = id). Het gebruiken van sku keert de sku van het geselecteerde product terug, terwijl het gebruiken van compiledSku en keert een koord als base#variant met de skus van het basisproduct en de geselecteerde variant, of één enkele sku terug als een basisproduct wordt geselecteerd.
- filter (folderOrProduct, folderOrProductOrVariant) - filtert de inhoud die door de kiezer moet worden gerenderd tijdens het navigeren in de productstructuur. folderOrProduct - rendert mappen en producten. folderOrProductOrVariant - geeft omslagen, product, en productvarianten terug. Als een product of productvariant wordt weergegeven, wordt deze ook selecteerbaar in de kiezer. (standaard = folderOrProduct)
- meerdere (true, false) - de selectie van een of meerdere producten inschakelen (standaard = false)
- emptyText - om de lege tekstwaarde van het plukkerveld te vormen

Ook worden standaardeigenschappen van dialoogvelden zoals `name` , `fieldLabel` of `fieldDescription` ondersteund.

>[!CAUTION]
>
>Voor de component `cifproductfield` is de component `cif.shell.picker` clientlib vereist. Als u een clientlib aan een dialoogvenster wilt toevoegen, kunt u de eigenschap extraClientlibs gebruiken.
>[!CAUTION]
>
>Vanaf CIF Core Components versie 2.0.0 is de ondersteuning voor `id` verwijderd en vervangen door `uid` . Adobe raadt u aan `sku` of `slug` als product-id te gebruiken. Adobe blijft `id` alleen ondersteunen voor projecten met CIF Core Components versie 1.x.

Een volledig werkend voorbeeld van `cifproductfield` kan in het [ 2&rbrace; project van de Componenten van de Kern van CIF &lbrace;worden gevonden. ](https://github.com/adobe/aem-core-cif-components/blob/master/ui.apps/src/main/content/jcr_root/apps/core/cif/components/commerce/productteaser/v1/productteaser/_cq_dialog/.content.xml) Zie ook [ het Aanpassen Dialogen ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/customizing.html?lang=nl-NL#customizing-dialogs) van de documentatie van de Componenten van de Kern van AEM.

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

- selectionId(id, uid, slug, urlPath, idAndUrlPath _(afgekeurd)_, uidAndUrlPath _(afgekeurd)_) - laat u het categoriekenmerk kiezen dat door de plukker moet worden teruggekeerd (gebrek = id).
- meerdere (true, false) - de selectie van een of meerdere categorieën inschakelen (standaard = false)

Ook worden standaardeigenschappen van dialoogvelden zoals `name` , `fieldLabel` of `fieldDescription` ondersteund.

>[!CAUTION]
>
>Hetzelfde als de component `cifproductfield` vereist de component `cifcategoryfield` ook de clientlib `cif.shell.picker` . U kunt de eigenschap `extraClientlibs` gebruiken om een clientlib aan een dialoogvenster toe te voegen. Zie [ het Aanpassen Dialogen ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/customizing.html?lang=nl-NL#customizing-dialogs) van de documentatie van de Componenten van de Kern van AEM.
>[!CAUTION]
>
>Vanaf CIF Core Components versie 2.0.0 is de ondersteuning voor `id` verwijderd en vervangen door `uid` . Adobe raadt u aan `uid` of `urlPath` als categorie-id te gebruiken. Adobe blijft `id` &amp; `idAndUrlPath` alleen ondersteunen voor projecten met CIF Core Components versie 1.x.

Een volledig werkend voorbeeld van `cifcategoryfield` kan in het [ 2&rbrace; project van de Componenten van de Kern van CIF &lbrace;worden gevonden.](https://github.com/adobe/aem-core-cif-components/blob/master/ui.apps/src/main/content/jcr_root/apps/core/cif/components/commerce/featuredcategorylist/v1/featuredcategorylist/_cq_dialog/.content.xml)
