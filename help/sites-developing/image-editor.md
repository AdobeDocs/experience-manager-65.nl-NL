---
title: Afbeeldingseditor
seo-title: Afbeeldingseditor
description: De Afbeeldingseditor is een kernstuk van AEM en kan door componenten worden gebruikt om het bewerken van afbeeldingen door auteurs van inhoud te vergemakkelijken.
seo-description: De Afbeeldingseditor is een kernstuk van AEM en kan door componenten worden gebruikt om het bewerken van afbeeldingen door auteurs van inhoud te vergemakkelijken.
uuid: de6ac71b-380a-4b67-b697-ac34a79a9cc4
contentOwner: bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: components
discoiquuid: f6347492-cf48-4835-b8fd-ce9a75a09abe
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Afbeeldingseditor{#image-editor}

De Afbeeldingseditor is een kernstuk van AEM en kan door componenten worden gebruikt om het bewerken van afbeeldingen door auteurs van inhoud te vergemakkelijken.

>[!CAUTION]
>
>Om de eigenschappen van de Redacteur van het Beeld te gebruiken die in dit artikel worden beschreven, [eigenschappak 24267](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/featurepack/cq-6.4.0-featurepack-24267) moet worden geïnstalleerd.

## Relatieve eenheden voor afbeelding met hyperlinks {#relative-units-for-image-map}

In de Afbeeldingseditor blijven afbeeldingskaartgebieden behouden als absolute en relatieve eenheden. Relatieve eenheden zijn handig wanneer deze worden opgegeven als gegevenskenmerken voor het dynamisch wijzigen van de grootte van een afbeeldingskaart (ten opzichte van de afbeeldingsgrootte) aan de clientzijde in een responsieve afbeeldingscomponent.

### imageMap, eigenschap {#imagemap-property}

De coördinaten van de afbeelding met hyperlinks blijven als een `imageMap` eigenschap bij de JCR. Deze heeft de volgende indeling.

In de eigenschap worden kaartgebieden als volgt opgeslagen:

`[area1][area2][...]`

Vlakindeling:

`[SHAPE(COORDINATES)"HREF"|"TARGET"|"ALT"|(RELATIVE_COORDINATES)]`

Voorbeeld:

`[rect(0,0,10,10)"https://www.adobe.com"|"_self"|"alt"|(0,0,0.8,0.8)]`
`[circle(10,10,10)"https://www.adobe.com"|"_self"|"alt"|(0.8,0.8,0.8)]`

## Ondersteuning voor SVG-afbeeldingen {#support-for-svg-images}

SVG (Scalable Vector Graphics) wordt ondersteund door de Afbeeldingseditor.

* Het slepen en neerzetten van een SVG-element van DAM en het uploaden van een SVG-bestandsupload vanuit een lokaal bestandssysteem worden beide ondersteund.

## Plug-ins inschakelen op basis van MIME-type {#enabling-plugins-by-mime-type}

In bepaalde situaties moeten ontwerpacties voor bepaalde MIME-typen worden beperkt, omdat er geen ondersteuning is voor verwerking op de server. Het bewerken van SVG-afbeeldingen is bijvoorbeeld niet toegestaan.

Plug-ins in de Afbeeldingseditor kunnen selectief worden ingeschakeld door het MIME-type door een `supportedMimeTypes` eigenschap in te stellen op het configuratieknooppunt van de afzonderlijke plug-in.

### Voorbeeld {#example}

Stel bijvoorbeeld dat de mogelijkheid om uit te snijden alleen is toegestaan voor GIF-, JPEG-, PNG-, WEBP- en TIFF-afbeeldingen.

De `supportedMimeTypes` eigenschap moet vervolgens worden ingesteld als een tekenreeks van de toegestane MIME-typen op het configuratieknooppunt van de insteekmodule op het `cq:editConfig` knooppunt van de afbeeldingscomponent.

`/apps/core/wcm/components/image/v2/image/cq:editConfig`

```xml
 jcr:primaryType="cq:EditConfig">
     <cq:dropTargets jcr:primaryType="nt:unstructured">
         <image ...>
            ...
         </image>
     </cq:dropTargets>
     <cq:inplaceEditing
         jcr:primaryType="cq:InplaceEditingConfig"
         active="{Boolean}true"
         editorType="image">
         <config jcr:primaryType="nt:unstructured">
             <plugins jcr:primaryType="nt:unstructured">
                 <crop
                     jcr:primaryType="nt:unstructured"
                     supportedMimeTypes="[image/gif,image/jpeg,image/png,image/webp,image/tiff]"
                     features="*">
                     <aspectRatios jcr:primaryType="nt:unstructured">
                        ...
                     </aspectRatios>
                 </crop>
                 ...
             </plugins>
             <ui jcr:primaryType="nt:unstructured">
                 ...
             </ui>
         </config>
     </cq:inplaceEditing>
 </jcr:root>
```

