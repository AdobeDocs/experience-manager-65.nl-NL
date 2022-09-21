---
title: UAC voor PDFG-configuratie uitschakelen voor zowel JEE als OSGI
description: Stappen om UAC voor Configuratie PDFG onbruikbaar te maken
source-git-commit: f6dcb488c64dad2d65facc0e8e1d6685b7375a08
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---

# Kan Word- of Excel-bestand niet converteren naar PDF op Windows Server {#unable-to-convert-word-excel-files-PDF}

## Probleem {#issue}

Wanneer de gebruiker Word- of Excel-bestanden naar PDF probeert om te zetten op Microsoft Windows Server, wordt de volgende fout aangetroffen:

*Foutbericht van de primaire converter: ALC-PDG-015-003-Het systeem kan het invoerbestand niet openen. Verzend het bestand opnieuw of neem contact op met de systeembeheerder.*


## Oplossing {#solution}

Voer de volgende stappen uit om het probleem op te lossen:
1. Ga naar **[!UICONTROL Start > Run]** en vervolgens voert u **[!UICONTROL MSCONFIG]**.
1. Klik op de knop **[!UICONTROL Tools]** en omlaag schuiven en selecteren **[!UICONTROL Change UAC Settings]**. Klikken **[!UICONTROL Launch]** om de opdracht in een nieuw venster uit te voeren.
1. Pas de schuifregelaar aan op het niveau Nooit aangeven. Als u klaar bent, sluit u het opdrachtvenster en sluit u het venster Systeemconfiguratie.
1. Verifieer dat register het plaatsen voor UAC aan 0 (nul) wordt geplaatst. Voer de volgende stappen uit om te verifiëren:

   1. Microsoft® raadt u aan een back-up van het register te maken voordat u het wijzigt. Voor gedetailleerde stappen raadpleegt u [Hoe te file en herstel de registratie in Vensters](https://support.microsoft.com/en-us/help/322756).
   1. Open Microsoft® Windows Registry Editor. Als u de registereditor wilt openen, gaat u naar Start > Uitvoeren, typt u regedit en klikt u op OK.
   1. Ga naar `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\policies\system\`. Zorg ervoor dat de waarde van EnableLUA is ingesteld op 0 (nul).
   1. Waarde van garanderen **EnableLUA** is ingesteld op 0 (nul). Als de waarde niet 0 is, wijzigt u de waarde in 0. Sluit de registereditor.

1. Start de computer opnieuw op.

## Van toepassing op {#appliesto}

Deze oplossing is van toepassing op het volgende:
* AEM Forms op JEE Server
* AEM Forms op OSGi Server