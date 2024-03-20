---
title: Afbeeldingseditor
description: De Afbeeldingseditor is een AEM en kan door componenten worden gebruikt om het bewerken van afbeeldingen door makers van inhoud te vergemakkelijken.
contentOwner: bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: components
exl-id: af6cf1e0-8901-4621-9f72-e791cb8d68ae
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# Afbeeldingseditor{#image-editor}

De Afbeeldingseditor is een AEM en kan door componenten worden gebruikt om het bewerken van afbeeldingen door makers van inhoud te vergemakkelijken.

>[!CAUTION]
>
>Om de eigenschappen van de Redacteur van het Beeld te gebruiken die in dit artikel worden beschreven, [functiepakket 24267](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/featurepack/cq-6.4.0-featurepack-24267) moet geïnstalleerd zijn.

## Relatieve eenheden voor afbeelding met hyperlinks {#relative-units-for-image-map}

In de Afbeeldingseditor blijven afbeeldingskaartgebieden behouden als absolute en relatieve eenheden. Relatieve eenheden zijn handig wanneer deze worden opgegeven als gegevenskenmerken voor het dynamisch wijzigen van de grootte van een afbeeldingskaart (ten opzichte van de afbeeldingsgrootte) aan de clientzijde in een responsieve afbeeldingscomponent.

### imageMap, eigenschap {#imagemap-property}

De coördinaten van de afbeeldingskaart blijven als een `imageMap` door de Afbeeldingseditor. Deze heeft de volgende indeling.

In de eigenschap worden kaartgebieden als volgt opgeslagen:

`[area1][area2][...]`

Vlakindeling:

`[SHAPE(COORDINATES)"HREF"|"TARGET"|"ALT"|(RELATIVE_COORDINATES)]`

Voorbeeld:

`[rect(0,0,10,10)"https://www.adobe.com"|"_self"|"alt"|(0,0,0.8,0.8)]`
`[circle(10,10,10)"https://www.adobe.com"|"_self"|"alt"|(0.8,0.8,0.8)]`

## Ondersteuning voor SVG-afbeeldingen {#support-for-svg-images}

Scalable Vector Graphics (SVG) wordt ondersteund door de Afbeeldingseditor.

* De belemmering-en-daling van SVG activa van DAM en het uploaden van een SVG dossier van een lokaal dossiersysteem worden allebei gesteund.

## Plug-ins inschakelen op basis van MIME-type {#enabling-plugins-by-mime-type}

In bepaalde situaties moeten ontwerpacties voor bepaalde MIME-typen worden beperkt, omdat er geen ondersteuning is voor verwerking op de server. Het bewerken van SVG-afbeeldingen is bijvoorbeeld niet toegestaan.

Plug-ins in de Afbeeldingseditor kunnen selectief worden ingeschakeld door een MIME-type in te stellen `supportedMimeTypes` eigenschap op het configuratieknooppunt van de individuele plug-in.

### Voorbeeld {#example}

Laten we bijvoorbeeld zeggen dat de mogelijkheid om uit te snijden alleen moet worden toegestaan voor GIF-, JPEG-, PNG-, WEBP- en TIFF-afbeeldingen.

De `supportedMimeTypes` eigenschap moet vervolgens worden ingesteld als een tekenreeks van de toegestane MIME-typen op het configuratieknooppunt van de plug-in op het tabblad `cq:editConfig` knooppunt van de afbeeldingscomponent.

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
