---
title: UAC voor PDFG-configuratie uitschakelen voor zowel JEE als OSGI
description: Leer de stappen op hoe u UAC voor Configuratie PDFG kunt onbruikbaar maken om Word aan PDF omzetting te bevestigen.
exl-id: 785b7bb4-7158-45ea-a1e5-eebf3dc3ebc3
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Document Services
role: User, Developer
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---

# Kan Word- of Excel-bestand niet converteren naar PDF op Windows Server {#unable-to-convert-word-excel-files-PDF}

## Probleem {#issue}

Wanneer de gebruiker Word- of Excel-bestanden naar PDF probeert om te zetten op Microsoft® Windows Server, wordt de volgende fout aangetroffen:

*Foutbericht van de primaire converter:*
*ALC-PDG-015-003-Het systeem kan het invoerbestand niet openen. Verzend het bestand opnieuw of neem contact op met de systeembeheerder.*


## Oplossing {#solution}

Ga als volgt te werk:

1. Ga voor toegang tot het hulpprogramma Systeemconfiguratie naar **[!UICONTROL Start > Run]** en vervolgens voert u **[!UICONTROL MSCONFIG]**.
1. Klik op de knop **[!UICONTROL Tools]** en omlaag schuiven en selecteren **[!UICONTROL Change UAC Settings]**. Klikken **[!UICONTROL Launch]** zodat u de opdracht in een nieuw venster kunt uitvoeren.
1. Pas de schuifregelaar aan op het niveau Nooit aangeven. Wanneer gebeëindigd, sluit het bevelvenster en sluit het venster van de Configuratie van het Systeem.
1. Verifieer dat register het plaatsen voor UAC aan 0 (nul) wordt geplaatst. Voer de volgende stappen uit om te verifiëren:

   1. Microsoft® raadt u aan een back-up van het register te maken voordat u het wijzigt. Zie voor meer informatie [Hoe te file en herstel de registratie in Vensters](https://support.microsoft.com/en-us/help/322756).
   1. Open Microsoft® Windows Registry Editor. Als u de registereditor wilt openen, gaat u naar Start > Uitvoeren, typt u regedit en klikt u op OK.
   1. Navigeren naar `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\policies\system\`. Zorg ervoor dat de waarde van EnableLUA is ingesteld op 0 (nul).
   1. Waarde van garanderen **EnableLUA** is ingesteld op 0 (nul). Als de waarde niet 0 is, wijzigt u de waarde in 0. Sluit de registereditor.

1. Start de computer opnieuw op.

## Van toepassing op {#appliesto}

Deze oplossing is van toepassing op AEM Forms op JEE Server en AEM Forms op OSGi Server.
