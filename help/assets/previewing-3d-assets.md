---
title: 3D-elementen voorvertonen
description: Leer hoe u een voorvertoning van 3D-elementen kunt weergeven
contentOwner: Rick Brough
docset: aem65
feature: 3D-middelen
role: Business Practitioner
exl-id: fdebbc2b-c04d-4cdd-b7c2-8e9a2a854e79
translation-type: tm+mt
source-git-commit: 666bc5d943af371726708cb2ef157a9b3f07eb8e
workflow-type: tm+mt
source-wordcount: '547'
ht-degree: 4%

---

# Voorvertoning weergeven van 3D-elementen in Adobe Experience Manager{#previewing-3d-assets-aem}

Experience Manager ondersteunt het uploaden, leveren en interactief voorvertonen van 3D-elementen als onderdeel van het ontwerpproces.

De interactieve 3D-viewer is beschikbaar op de pagina met elementdetails in Experience Manager. De viewer bevat onder andere een verzameling interactieve besturingselementen voor camera waarmee u het 3D-element kunt draaien, zoomen en pannen.

<!-- See also [Working with 3D assets in Dynamic Media](/help/assets/assets-3d.md). -->

## Ondersteunde indelingen voor 3D-voorvertoning in Experience Manager {#supported-3d-previewing-assets}

Interactieve 3D-voorvertoning ondersteunt de volgende bestandsindelingen:

| 3D-bestandsextensie | Bestandsindeling | MIME-type | Opmerkingen |
|---|---|---|---|
| GLB | Binaire GL-transmissie | model/gltf-binair |  |
| GLTF | GL-indeling voor verzending | model/gltf+json | Zie **Opmerking** hieronder. |
| OBJ | WaveFront 3D-objectbestand | application/x-tgif |  |
| STL | Stereolithografie | application/vnd.ms-pki.stl |  |
| DN | Adobe Dimension | model/x-adobe-dn | Alleen ondersteuning voor inname; voorvertoning niet beschikbaar. |
| USDZ | Universal Scene Description Zip-archief | model/vnd.usdz+zip | Alleen ondersteuning voor inname; voorvertoning niet beschikbaar. |

>[!NOTE]
>
>Als materialen niet in voorproef van een gLTF model teruggeven, zorg ervoor zij behoorlijk en in een `textures` omslag in de zelfde wortelomslag zoals het model worden genoemd, gelijkend op het volgende:

    Element (map)
    model.
    gltfmodel.
    bintextures (map)
    material_0_baseColor.
    jpegmaterial_0_normal.jpeg

## Prestatieoverwegingen wanneer u een voorvertoning van 3D-elementen weergeeft in Experience Manager{#performance-3d-previewing-assets}

De tijd die nodig is om een 3D-element te openen op de pagina met de elementdetails, is afhankelijk van verschillende factoren, zoals bandbreedte, de complexiteit van de afbeelding en de vertraging van de server.

Bovendien zijn de mogelijkheden van de clientcomputer, zoals een werkstation, laptop of mobiel aanraakapparaat, ook belangrijk om te overwegen wanneer u de camera interactief manipuleert. Een redelijk krachtig systeem met goede grafische mogelijkheden kan de interactieve 3D-kijkervaring vloeiender en gunstiger maken.

**Een voorvertoning van 3D-elementen weergeven in Experience Manager:**

1. Zorg ervoor dat u 3D-elementen hebt geüpload naar de Experience Manager.
Zie [Ondersteunde indelingen voor 3D-voorvertoning](#supported-3d-previewing-assets) en [Elementen uploaden](/help/assets/manage-assets.md#uploading-assets).
1. Tik in Experience Manager op de pagina **[!UICONTROL Navigation]** op **[!UICONTROL Assets > Files.]**

   ![Navigatiepagina](/help/assets/assets-dm/navigation-assets.png)

1. Tik in de rechterbovenhoek van de pagina in de vervolgkeuzelijst Weergave op **[!UICONTROL Card View]** en ga naar een 3D-asset waarvan u een voorvertoning wilt weergeven.

   ![3D-kaart selecteren](/help/assets/assets-dm/3d-card-select.png)
   _Tik in de Kaartweergave op de kaart van het 3D-element waarvan u een voorvertoning wilt weergeven._

1. Tik op de kaart van het 3D-element.

   ![Interactieve 3D-voorvertoning](/help/assets/assets-dm/3d-preview.png)
   _Interactieve voorvertoning van een 3D-element op de pagina met de elementdetails._
1. Voer een van de volgende handelingen uit op de pagina met de elementdetails voor het 3D-element:

   | Weergave | Beschrijving | Muishandeling | Handeling op aanraakscherm |
   | --- | --- | --- | --- |
   | **De camera draaien** | Draai de weergave rond de 3D-scène en -objecten. | Klik met de linkermuisknop en sleep. | Druk met één vinger en sleep. |
   | **Uw camera pannen** | U kunt de weergave naar links, rechts, omhoog of omlaag pannen. | Klik met de rechtermuisknop en sleep. | Druk met twee vingers en sleep. |
   | **Uw camera zoomen** | In- en uitzoomen op gebieden in de 3D-scène. | Schuifwiel. | Kneep met twee vingers. |
   | **De camera opnieuw opnemen** | Voer de camera opnieuw in op een punt op een object in de 3D-scène. | Dubbelklik. | Dubbeltik. |
   | **Herstellen** | Tik in de rechterbenedenhoek van de pagina op het pictogram Herstellen om het doelpunt van de weergave te herstellen naar het midden van het 3D-element. Met Herstellen wordt de camera ook dichter bij of verder weg geplaatst om het middel volledig en bij een redelijke weergavegrootte weer te geven. |  |  |
   | **Modus Volledig scherm** | Tik op het pictogram Volledig scherm in de rechterbenedenhoek van de pagina om de modus Volledig scherm te activeren. |  |  |

1. Tik, als u klaar bent, in de rechterbovenhoek van de pagina op **[!UICONTROL Close.]**
