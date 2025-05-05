---
title: Probleemoplossing voor artikel om het probleem op te lossen wanneer de PaperCapture-service geen OCR-bewerkingen (Optical Character Recognition) uitvoert op PDF's.
description: Leer de stappen om het probleem op te lossen waarbij de service Documentdigitalisering geen OCR-bewerkingen (Optical Character Recognition) uitvoert op PDF's.
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
exl-id: 64e120ee-5f16-4cd3-9ae9-95b165169e47
source-git-commit: e030a71a0f52e22a803597122369cb111774f49b
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 0%

---


# De service PaperCature kan geen OCR-bewerking uitvoeren op PDF&#39;s

## Probleem

Na een upgrade naar AEM Forms Service Pack 6.5.21.0 of AEM Forms Service Pack 6.5.22.0 kan de `PaperCapture` -service geen OCR-bewerkingen (Optical Character Recognition) uitvoeren op PDF&#39;s. De service genereert geen uitvoer in de vorm van een PDF- of logbestand.

## Van toepassing op

Deze oplossing geldt voor:

* AEM Forms op alle JEE-servers (JBoss, Weblogic, Websphere)
* AEM Forms op OSGi-servers

## Oplossing

1. Download [ hotfix ](https://nam04.safelinks.protection.outlook.com/?url=https%3A%2F%2Fexperience.adobe.com%2F%23%2Fdownloads%2Fcontent%2Fsoftware-distribution%2Fen%2Faem.html%3Fpackage%3D%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq650%2Fhotfix%2FPaperCaptureSvc.zip&amp;data=05%7C02%7Cruchitas%40adobe.com%7Cf50f80aab6994875271a08dc91f2f137%7Cfa7b1b5a7b34438794aed2c178decee1%7C0%7C0%7C638545719814675925%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C0%7C%7C%7C&amp;sdata=9pTrMfiMD%2B5kQezxsZwTdOmaaktxURR99d7f6wHr%2FWQ%3D&amp;reserved=0) van het portaal van de Distributie van de Software.
1. Extraheer en kopieer de inhoud van de gedownloade map.
1. Navigeer naar de onderstaande paden voor de overeenkomende toepassingsservers:
   * **jreliëf**:

     `..\Adobe\Adobe_Experience_Manager_Forms\jboss\standalone\svcnative\PaperCaptureSvc`
   * **weblogic**:

     `..\Adobe\Adobe_Experience_Manager_Forms\crx-repository\bedrock\svcnative\PaperCaptureSvc`
   * **websphere**:\
     `..\Adobe\Adobe_Experience_Manager_Forms\crx-repository\bedrock\svcnative\PaperCaptureSvc`
   * **OSGi opstelling**:\
     `..\quickstart\crx-quickstart\bedrock\svcnative\PaperCaptureSvc`
1. Stop de AEM-toepassingsserver.
1. Vervang de bestaande inhoud van de map `PaperCaptureSvc` door de gekopieerde inhoud.
1. Start de AEM-toepassingsserver opnieuw.

   >[!NOTE]
   >
   > U wordt aangeraden de SDK opnieuw op te starten met de opdracht &#39;Ctrl + C&#39;. Het opnieuw opstarten van de AEM SDK met behulp van alternatieve methoden, bijvoorbeeld het stoppen van Java-processen, kan leiden tot inconsistenties in de AEM-ontwikkelomgeving.
