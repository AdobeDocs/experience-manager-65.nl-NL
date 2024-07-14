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
| AEM as a Cloud Service | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/previewing-3d-assets.html?lang=en) |
| AEM 6,5 | Dit artikel |

Experience Manager ondersteunt het uploaden, leveren en interactief voorvertonen van 3D-elementen als onderdeel van het ontwerpproces.

De interactieve 3D-viewer is beschikbaar op de pagina met elementdetails in Experience Manager. De viewer bevat onder andere een verzameling interactieve besturingselementen voor camera waarmee u het 3D-element kunt draaien, zoomen en pannen.

<!-- See also [Working with 3D assets in Dynamic Media](/help/assets/assets-3d.md). -->

## Ondersteunde indelingen voor 3D-voorvertoning in Experience Manager {#supported-3d-previewing-assets}

Interactieve 3D-voorvertoning ondersteunt de volgende bestandsindelingen:

| 3D-bestandsextensie | Bestandsindeling | MIME-type | Notities |
|---|---|---|---|
| GLB | Binaire GL-transmissie | model/gltf-binair | |
| GLTF | GL-indeling voor verzending | model/gltf+json | Zie **Nota** hieronder. |
| OBJ | WaveFront 3D-objectbestand | application/x-tgif | |
| STL | Stereolithografie | application/vnd.ms-pki.stl | |
| DN | Adobe Dimension | model/x-adobe-dn | Alleen ondersteuning voor inslikken; voorvertoning niet beschikbaar. |
| USDZ | Universal Scene Description Zip-archief | model/vnd.usdz+zip | Alleen ondersteuning voor inslikken; voorvertoning niet beschikbaar. |

>[!NOTE]
>
>Als materialen niet worden gerenderd in de voorvertoning van een gLTF-model, controleert u of ze op de juiste wijze zijn benoemd en zich in een `textures` -map in dezelfde hoofdmap als het model bevinden, vergelijkbaar met het volgende:

     Activa (omslag) 
     model.gltf 
     model.bin 
     texturen (omslag) 
     material_0_baseColor.jpeg 
     material_0_normal.jpeg 

## Prestatieaspecten wanneer u een voorvertoning van 3D-elementen weergeeft in Experience Manager{#performance-3d-previewing-assets}

De tijd die nodig is om een 3D-element te openen op de pagina met de elementdetails, is afhankelijk van verschillende factoren, zoals bandbreedte, de complexiteit van de afbeelding en de vertraging van de server.

Bovendien zijn de mogelijkheden van de clientcomputer - zoals een werkstation, laptop of mobiel aanraakapparaat - ook belangrijk om te overwegen wanneer u de camera interactief manipuleert. Een redelijk krachtig systeem met goede grafische mogelijkheden kan de interactieve 3D-kijkervaring vloeiender en gunstiger maken.

**aan voorproef 3D activa in Experience Manager:**

1. Zorg ervoor dat u 3D-elementen hebt geüpload naar de Experience Manager.
Zie [ Gesteunde formaten voor 3D voorproef ](#supported-3d-previewing-assets) en [ uploadt Assets ](/help/assets/manage-assets.md#uploading-assets).
1. Selecteer in Experience Manager op de pagina **[!UICONTROL Navigation]** de optie **[!UICONTROL Assets]** > **[!UICONTROL Files]** .

   ![ pagina van de Navigatie ](/help/assets/assets-dm/navigation-assets.png)

1. Selecteer in de rechterbovenhoek van de pagina in de vervolgkeuzelijst Weergave de optie **[!UICONTROL Card View]** en navigeer naar een 3D-element waarvan u een voorvertoning wilt weergeven.

   ![ 3D kaart uitgezocht ](/help/assets/assets-dm/3d-card-select.png)
   _in de Mening van de Kaart, selecteer de kaart van 3D activa u voorproef wilt._

1. Selecteer de kaart van het 3D-element.

   ![ Interactieve 3D voorproef ](/help/assets/assets-dm/3d-preview.png)
   _Interactieve voorproef van een 3D activa in de pagina van de de meningsmening van activadetails._
1. Voer een van de volgende handelingen uit op de pagina met de elementdetails voor het 3D-element:

   | Weergave | Beschrijving | Muishandeling | Handeling op het aanraakscherm |
   | --- | --- | --- | --- |
   | **draai uw camera** | Draai de weergave rond de 3D-scène en -objecten. | Klik met de linkermuisknop en sleep. | Druk met één vinger en sleep. |
   | **Pannen uw camera** | U kunt de weergave naar links, rechts, omhoog of omlaag pannen. | Klik met de rechtermuisknop en sleep. | Druk met twee vingers en sleep. |
   | **Gezoem uw camera** | Ga in- en uit gebieden in de 3D-scène. | Schuifwiel. | Kneep met twee vingers. |
   | **herenter uw camera** | Voer de camera opnieuw in op een punt op een object in de 3D-scène. | Dubbelklik. | Dubbelselecteren. |
   | **Terugstellen** | Selecteer in de rechterbenedenhoek van de pagina het pictogram Herstellen om het doelpunt van de weergave te herstellen naar het midden van het 3D-element. Met Herstellen wordt de camera ook dichter bij of verder weg geplaatst om het middel volledig en bij een redelijke weergavegrootte weer te geven. |   |   |
   | **Volledige het schermwijze** | Als u de modus Volledig scherm wilt inschakelen, klikt u op het pictogram Volledig scherm rechtsonder op de pagina. |   |   |

1. Wanneer u klaar bent, selecteert u **[!UICONTROL Close]** in de rechterbovenhoek van de pagina.
