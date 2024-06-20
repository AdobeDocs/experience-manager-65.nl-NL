---
title: Opstelling het project van Visual Studio en bouwt Windows app
description: Leer hoe te opstelling een project van Visual Studio om AEM Forms Windows mobiele apparatenapp te bouwen.
topic-tags: forms-app
docset: aem65
exl-id: ae7340c8-38cc-4b2b-ba17-22011471fd7d
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: e821be5233fd5f6688507096790d219d25903892
workflow-type: tm+mt
source-wordcount: '881'
ht-degree: 0%

---

# Opstelling het project van Visual Studio en bouwt Windows app{#set-up-the-visual-studio-project-and-build-the-windows-app}

AEM Forms biedt de volledige broncode van de AEM Forms-app. De bron bevat alle componenten om een toepassing van de douanewerkruimte te bouwen. Het broncodearchief, `adobe-lc-mobileworkspace-src-<version>.zip`maakt deel uit van de `adobe-aemfd-forms-app-src-pkg-<version>.zip` pakket over Softwaredistributie.

Voer de volgende stappen uit om de AEM Forms-toepassingsbron op te halen:

1. Openen [Softwaredistributie](https://experience.adobe.com/downloads). U hebt een Adobe ID nodig om u aan te melden bij de softwaredistributie.
1. Selecteren **[!UICONTROL Adobe Experience Manager]** beschikbaar in het koptekstmenu.
1. In de **[!UICONTROL Filters]** sectie:
   1. Selecteren **[!UICONTROL Forms]** van de **[!UICONTROL Solution]** vervolgkeuzelijst.
   2. Selecteer de versie en typ voor het pakket. U kunt ook de opdracht **[!UICONTROL Search Downloads]** om de resultaten te filteren.
1. Selecteer de pakketnaam die van toepassing is op het besturingssysteem. Selecteer **[!UICONTROL Accept EULA Terms]** en selecteert u **[!UICONTROL Download]**.
1. Openen [Pakketbeheer](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html)  en klik op **[!UICONTROL Upload Package]** om het pakket te uploaden.
1. Selecteer het pakket en klik op **[!UICONTROL Install]**.

1. Als u het broncodearchief wilt downloaden, opent u `https://<server>:<port>/crx/de/content/forms/mobileapps/src/adobe-lc-mobileworkspace-src-<version>.zip` in uw browser.\
   Het bronpakket wordt gedownload op uw apparaat.

In de volgende afbeelding wordt de geëxtraheerde inhoud van de `adobe-lc-mobileworkspace-src-<version>.zip`.

![mws-content-1](assets/mws-content-1.png)

In de volgende afbeelding wordt de mapstructuur van de `windows` in de `src` map.

![win-dir](assets/win-dir.png)

## Het milieu instellen {#setting-up-the-environment}

Voor Windows-apparaten hebt u het volgende nodig:

* Microsoft Windows 8.1 of Windows 10
* Microsoft Visual Studio 2015
* Microsoft Visual Studio Tools for Apache Cordova

## Visual Studio Project instellen voor AEM Forms-app {#setting-up-visual-studio-project-for-aem-forms-app}

Voer de volgende stappen aan opstelling uit AEM Forms app project in Visual Studio.

1. De `adobe-lc-mobileworkspace-src-<version>.zip` archiveren naar `%HOMEPATH%\Projects` map in Windows 8.1 of Windows 10 met Visual Studio 2015 geïnstalleerd en geconfigureerd.
1. Het archief in het dialoogvenster `%HOMEPATH%\Projects\MobileWorkspace` directory.
1. Ga naar de `%HOMEPATH%\Projects\MobileWorkspace\adobe-lc-mobileworkspace-src-[versionsrc]\windows` directory.
1. Open de `CordovaApp.sln` dossier gebruikend Visual Studio 2015 en ga aan de bouw van AEM Forms app te werk.

## AEM Forms-app ontwikkelen {#build-aem-forms-app}

Voer de volgende stappen uit om AEM Forms-app te maken en te implementeren.

>[!NOTE]
>
>Gegevens die zijn opgeslagen in het Windows-bestandssysteem voor de AEM Forms-toepassing, worden niet gecodeerd. Het wordt geadviseerd dat u een derdehulpmiddel zoals de Encryptie van de Aandrijving van Windows BitLocker gebruikt om schijfgegevens te coderen.

1. In de StandaardToolbar van Visual Studio, selecteer **Geen** in het keuzemenu voor de constructiemodus.

1. Selecteer Windows-AnyCPU, Windows-x64 of Windows-x86 op basis van uw platform. Windows-AnyCPU wordt aanbevolen.
1. In de Ontdekkingsreiziger van de Oplossing van Visual Studio, klik het project met de rechtermuisknop aan **CordovaApp.Windows** en selecteert u **Store > Create AppPackages**.

   ![apppackages maken](assets/createapppackages.png)

   De wizard App Packages maken wordt weergegeven.

   Het installatiebestand van CordovaApp.Windows_3.0.2.0_anycpu.appx wordt gemaakt in de map platforms\windows\AppPackages\CordovaApp.Windows_3.0.2.0_anycpu_Test.

   Als u de fout tegenkomt `Retarget to windows 8.1 required`, klikt u met de rechtermuisknop op de fout en selecteert u in het pop-upmenu de optie **Opnieuw toewijzen aan Windows 8.1**.

   ![retarget-oplossing](assets/retarget-solution.png)

1. Selecteer in de wizard App Packages maken het weer of u de app niet naar de winkel Windows wilt uploaden en klik vervolgens op **Volgende**.

   ![createAppPackageswizard1](assets/createapppackageswizard1.png)

1. Breng de gewenste wijzigingen aan in de parameters, zoals de versie en uitvoerlocatie van de build van de app.

   ![createAppPackageswizard2](assets/createapppackageswizard2.png)

1. Nadat het project is gemaakt, kunt u de app installeren met:

   * Windows PowerShell
   * Visual Studio

   De `.appx` de volgende onderdelen zijn vereist voor een correcte installatie van het pakket:

   1. WinJS-bibliotheek
   1. Zorg ervoor dat het pakket wordt geleverd met een zelfondertekend certificaat of een door een vertrouwde instantie ondertekend openbaar certificaat, zoals VeriSign.
   1. Licentie voor ontwikkelaars

   De map Platforms\windows\AppPackages\CordovaApp.Windows_3.0.2.0_anycpu_Test bevat de vier hoofdcomponenten ervan:

   1. `.appx` file
   1. Certificaat (momenteel is het een zelfondertekend certificaat van Apache Cordova)
   1. Afhankelijkheidsmap
   1. PowerShell-bestand (.ps1-extensie)

## Het opstellen van een app die Vensters PowerShell gebruikt {#deploying-an-app-using-windows-powershell}

Er zijn twee manieren om de toepassing op een apparaat van Vensters te installeren.

### Door de ontwikkelaarslicentie aan te schaffen {#by-acquiring-the-developer-license}

1. Klik met de rechtermuisknop op het PowerShell-bestand ( `Add-AppDevPackage.ps1)`en kiest u **Uitvoeren met PowerShell**.

1. De opstelling zet u ertoe aan om een ontwikkelaarvergunning te krijgen. Gebruik Microsoft-accountgegevens om een ontwikkelaarslicentie te verkrijgen.\
   Deze licentie is 30 dagen geldig en u kunt deze gratis verlengen.
1. Wanneer u de ontwikkelaarslicentie aanschaft, wordt het zelfondertekende certificaat geïnstalleerd op het systeem en wordt de toepassing correct geïnstalleerd.

### Door apparaten in bedrijfsbezit te gebruiken {#by-using-enterprise-owned-devices}

Voor apparaten die eigendom zijn van een onderneming en die zijn aangesloten bij het domein van de onderneming, is het niet nodig een ontwikkelaarslicentie aan te schaffen.

Apparaten in bedrijfsbezit gebruiken Professional- en Enterprise-versies van Windows.

Microsoft raadt u aan een door een vertrouwde instantie uitgegeven openbaar certificaat, zoals VeriSign, te installeren.

De app implementeren:

* Zorg ervoor dat het apparaat wordt aangesloten bij het domein van de onderneming.
* Groepsbeleid instellen inschakelen.

**Groepsbeleid instellen inschakelen:**

1. Voer de handeling uit op uw apparaat `gpedit.msc`.
1. Navigeren naar **Computerconfiguratie > Systeembeheersjablonen > Windows-component > Implementatie toepassingspakket**.
1. Klikken met rechtermuisknop **Alle vertrouwde toepassingen installeren**.
1. Klikken **Bewerken** en selecteert u **Ingeschakeld**.

1. Klikken **OK**.

Bewerk het Visual Studio-script dat PowerShell heeft gegenereerd om te voorkomen dat het ontwikkelaarslicentie verwerft.

In het manuscript PowerShell, plaats de variabele: `$NeedDeveloperLicense = $false`.

Voor apparaten die geen domeinverbinding hebben, is de sideladende sleutel van de productactivering vereist. U kunt deze aanschaffen bij een Windows-leverancier.

Voor Windows 8.1 Home Edition, is er geen groepsbeleid, wordt de onderneming zijladen niet toegestaan, en u kunt zich niet bij het met het ondernemingsdomein aansluiten. Implementeer de app op een Windows 8.1 Home Edition-apparaat met een ontwikkelaarslicentie.

Klik voor meer informatie op [hier](https://blogs.msdn.com/b/mvpawardprogram/archive/2014/03/24/side-loading-deployment-of-windows-store-apps-in-enterprises-step-by-step.aspx).

## Het opstellen van een app die Visual Studio gebruikt {#deploying-an-app-using-visual-studio}

Om app op Vensters te installeren gebruikend Visual Studio:

1. Sluit het apparaat aan met extern foutopsporingsprogramma.\
   Zie voor meer informatie [Windows Store-apps uitvoeren op een externe computer](https://docs.microsoft.com/en-us/visualstudio/debugger/run-windows-store-apps-on-a-remote-machine).

1. Met uw open app in Visual Studio, kies Vensters-x64, Vensters-x86, of Vensters-AnyCPU van de lijst van de Platforms van de Oplossing, en selecteer **Externe machine**.
1. Uw app wordt geïmplementeerd op de externe computer.
