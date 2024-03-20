---
title: 3D-elementen voorvertonen
description: Leer hoe u een voorvertoning van 3D-elementen in Experience Manager kunt weergeven.
contentOwner: Rick Brough
docset: aem65
feature: 3D Assets
role: User
exl-id: fdebbc2b-c04d-4cdd-b7c2-8e9a2a854e79
hide: true
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '562'
ht-degree: 1%

---

# 3D-elementen voorvertonen in Adobe Experience Manager {#previewing-3d-assets-aem}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/previewing-3d-assets.html?lang=en) |
| AEM 6,5 | Dit artikel |

Experience Manager ondersteunt het uploaden, leveren en interactief voorvertonen van 3D-elementen als onderdeel van het ontwerpproces.

De interactieve 3D-viewer is beschikbaar op de pagina met elementdetails in Experience Manager. De viewer bevat onder andere een verzameling interactieve besturingselementen voor camera waarmee u het 3D-element kunt draaien, zoomen en pannen.

<!-- See also [Working with 3D assets in Dynamic Media](/help/assets/assets-3d.md). -->

## Ondersteunde indelingen voor 3D-voorvertoning in Experience Manager {#supported-3d-previewing-assets}

Interactieve 3D-voorvertoning ondersteunt de volgende bestandsindelingen:

| 3D-bestandsextensie | Bestandsindeling | MIME-type | Notities |
|---|---|---|---|
| GLB | Binaire GL-transmissie | model/gltf-binair | |
| GLTF | GL-indeling voor verzending | model/gltf+json | Zie **Opmerking** hieronder. |
| OBJ | WaveFront 3D-objectbestand | application/x-tgif | |
| STL | Stereolithografie | application/vnd.ms-pki.stl | |
| DN | Adobe Dimension | model/x-adobe-dn | Alleen ondersteuning voor inslikken; voorvertoning niet beschikbaar. |
| USDZ | Universal Scene Description Zip-archief | model/vnd.usdz+zip | Alleen ondersteuning voor inslikken; voorvertoning niet beschikbaar. |

>[!NOTE]
>
>Als materialen niet worden gerenderd in de voorvertoning van een gLTF-model, moet u ervoor zorgen dat ze een juiste naam hebben en in een `textures` map in dezelfde hoofdmap als het model, vergelijkbaar met het volgende:

    Element (map)
    model.gltf
    model.bin
    structuren (map)
    materiaal_0_baseColor.jpeg
    materiaal_0_normaal.jpeg

## Prestatieaspecten wanneer u een voorvertoning van 3D-elementen weergeeft in Experience Manager{#performance-3d-previewing-assets}

De tijd die nodig is om een 3D-element te openen op de pagina met de elementdetails, is afhankelijk van verschillende factoren, zoals bandbreedte, de complexiteit van de afbeelding en de vertraging van de server.

Bovendien zijn de mogelijkheden van de clientcomputer - zoals een werkstation, laptop of mobiel aanraakapparaat - ook belangrijk om te overwegen wanneer u de camera interactief manipuleert. Een redelijk krachtig systeem met goede grafische mogelijkheden kan de interactieve 3D-kijkervaring vloeiender en gunstiger maken.

**Een voorvertoning van 3D-elementen weergeven in Experience Manager:**

1. Zorg ervoor dat u 3D-elementen hebt geüpload naar de Experience Manager.
Zie [Ondersteunde indelingen voor 3D-voorvertoning](#supported-3d-previewing-assets) en [Elementen uploaden](/help/assets/manage-assets.md#uploading-assets).
1. Van Experience Manager, op **[!UICONTROL Navigation]** pagina, selecteert u **[!UICONTROL Assets]** > **[!UICONTROL Files]**.

   ![Navigatiepagina](/help/assets/assets-dm/navigation-assets.png)

1. Selecteer in de vervolgkeuzelijst Weergave rechtsboven op de pagina de optie **[!UICONTROL Card View]** Navigeer vervolgens naar een 3D-element waarvan u een voorvertoning wilt weergeven.

   ![3D-kaart selecteren](/help/assets/assets-dm/3d-card-select.png)
   _Selecteer in de Kaartweergave de kaart van het 3D-element waarvan u een voorvertoning wilt weergeven._

1. Selecteer de kaart van het 3D-element.

   ![Interactieve 3D-voorvertoning](/help/assets/assets-dm/3d-preview.png)
   _Interactieve voorvertoning van een 3D-element op de pagina met de elementdetails._
1. Voer een van de volgende handelingen uit op de pagina met de elementdetails voor het 3D-element:

   | Weergave | Beschrijving | Muishandeling | Handeling op het aanraakscherm |
   | --- | --- | --- | --- |
   | **De camera draaien** | Draai de weergave rond de 3D-scène en -objecten. | Klik met de linkermuisknop en sleep. | Druk met één vinger en sleep. |
   | **Uw camera pannen** | U kunt de weergave naar links, rechts, omhoog of omlaag pannen. | Klik met de rechtermuisknop en sleep. | Druk met twee vingers en sleep. |
   | **Uw camera zoomen** | Ga in- en uit gebieden in de 3D-scène. | Schuifwiel. | Kneep met twee vingers. |
   | **De camera opnieuw opnemen** | Voer de camera opnieuw in op een punt op een object in de 3D-scène. | Dubbelklik. | Dubbelselecteren. |
   | **Herstellen** | Selecteer in de rechterbenedenhoek van de pagina het pictogram Herstellen om het doelpunt van de weergave te herstellen naar het midden van het 3D-element. Met Herstellen wordt de camera ook dichter bij of verder weg geplaatst om het middel volledig en bij een redelijke weergavegrootte weer te geven. |   |   |
   | **Modus Volledig scherm** | Als u de modus Volledig scherm wilt inschakelen, klikt u op het pictogram Volledig scherm rechtsonder op de pagina. |   |   |

1. Als u klaar bent, selecteert u in de rechterbovenhoek van de pagina de optie **[!UICONTROL Close]**.
