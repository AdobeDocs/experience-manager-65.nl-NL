---
title: Probleemoplossing voor artikel om het probleem op te lossen wanneer de PaperCapture-service geen OCR-bewerkingen (Optical Character Recognition) op PDF uitvoert.
description: Leer de stappen om het probleem op te lossen waarbij de service Documentdigitalisering geen OCR-bewerkingen (Optical Character Recognition) uitvoert op PDF.
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: 18005ba060954151df126789496c81f7238e32f6
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 0%

---


# PaperCature Service kan geen OCR uitvoeren op PDF

## Probleem

Na de upgrade naar AEM Forms Service Pack 6.5.21.0 wordt de `PaperCapture` De service kan geen OCR-bewerkingen (Optical Character Recognition) uitvoeren op PDF. De service genereert geen uitvoer in de vorm van een PDF- of logbestand.

## Oplossing

1. Download de [hotfix](https://nam04.safelinks.protection.outlook.com/?url=https%3A%2F%2Fexperience.adobe.com%2F%23%2Fdownloads%2Fcontent%2Fsoftware-distribution%2Fen%2Faem.html%3Fpackage%3D%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq650%2Fhotfix%2FPaperCaptureSvc.zip&amp;data=05%7C02%7Cruchitas%40adobe.com%7Ca285aedf27094c9e8d9b08dc91e26aa7%7Cfa7b1b5a7b34438794aed2c178decee1%7C0%7C0%7C638545648843177070%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C0%7C%7C%7C&amp;sdata=uWk0PsSSDjLRxqEMGMW%2BbD%2Fv4egR4vWL%2B0mfKpXdrKQ%3D&amp;reserved=0) via de portal voor softwaredistributie.
1. Extraheer en kopieer de inhoud van de gedownloade map.
1. Navigeer naar de onderstaande paden voor de overeenkomende toepassingsservers:
   * **jager**:
     `..\Adobe\Adobe_Experience_Manager_Forms\jboss\standalone\svcnative\PaperCaptureSvc`
   * **webloem**:
     `..\Adobe\Adobe_Experience_Manager_Forms\crx-repository\bedrock\svcnative\PaperCaptureSvc`
   * **websfeer**:\
     `..\Adobe\Adobe_Experience_Manager_Forms\crx-repository\bedrock\svcnative\PaperCaptureSvc`
   * **OSGi instellen**:\
     `..\quickstart\crx-quickstart\bedrock\svcnative\PaperCaptureSvc`
1. De bestaande inhoud van het dialoogvenster `PaperCaptureSvc` met de gekopieerde inhoud.
1. [De AEM opnieuw starten](/help/forms/using/restart-aem-sdk.md).


