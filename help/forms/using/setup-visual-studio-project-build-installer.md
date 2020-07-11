---
title: Opstelling het project van Visual Studio en bouwt Windows app
seo-title: Opstelling het project van Visual Studio en bouwt Windows app
description: Leer hoe te opstelling een project van Visual Studio om AEM Forms Windows mobiele apparatenapp te bouwen.
seo-description: Leer hoe te opstelling een project van Visual Studio om AEM Forms Windows mobiele apparatenapp te bouwen.
uuid: 9559e584-2a40-4740-a29a-d7ad66220224
topic-tags: forms-app
discoiquuid: c71c2a17-54f9-4c95-a90a-3c89d6d45721
docset: aem65
translation-type: tm+mt
source-git-commit: 1dfc8fa91d3e5ae8ca49cf1f3cb739b59feb18cf
workflow-type: tm+mt
source-wordcount: '925'
ht-degree: 0%

---


# Opstelling het project van Visual Studio en bouwt Windows app{#set-up-the-visual-studio-project-and-build-the-windows-app}

AEM Forms bevat de volledige broncode van de app AEM Forms. De bron bevat alle componenten om een toepassing van de douanewerkruimte te bouwen. Het archief van de broncode, `adobe-lc-mobileworkspace-src-<version>.zip`is een deel van het `adobe-aemfd-forms-app-src-pkg-<version>.zip` pakket op de Distributie van de Software.

Voer de volgende stappen uit om de bron van de AEM Forms-app op te halen:

1. Open [Softwaredistributie](https://experience.adobe.com/downloads). U hebt een Adobe ID nodig om u aan te melden bij de Softwaredistributie.
1. Tik **[!UICONTROL Adobe Experience Manager]** beschikbaar in het koptekstmenu.
1. In het **[!UICONTROL Filters]** gedeelte:
   1. Selecteer een optie **[!UICONTROL Forms]** in de **[!UICONTROL Solution]** vervolgkeuzelijst.
   2. Selecteer de versie en typ voor het pakket. U kunt de **[!UICONTROL Search Downloads]** optie ook gebruiken om de resultaten te filteren.
1. Tik op de pakketnaam die van toepassing is op het besturingssysteem, selecteer **[!UICONTROL Accept EULA Terms]** en tik op **[!UICONTROL Download]**.
1. Open [Package Manager](https://docs.adobe.com/content/help/en/experience-manager-65/administering/contentmanagement/package-manager.html) en klik **[!UICONTROL Upload Package]** om het pakket te uploaden.
1. Selecteer het pakket en klik **[!UICONTROL Install]**.

1. Open het archief met de broncode `https://<server>:<port>/crx/de/content/forms/mobileapps/src/adobe-lc-mobileworkspace-src-<version>.zip` in uw browser om dit te downloaden.\
   Het bronpakket wordt gedownload op uw apparaat.

In de volgende afbeelding wordt de geëxtraheerde inhoud van de `adobe-lc-mobileworkspace-src-<version>.zip`afbeelding weergegeven.

![mws-content-1](assets/mws-content-1.png)

In de volgende afbeelding wordt de mapstructuur van de `windows` map in de `src` map weergegeven.

![win-dir](assets/win-dir.png)

## Het milieu instellen {#setting-up-the-environment}

Voor Windows-apparaten hebt u het volgende nodig:

* Microsoft Windows 8.1 of Windows 10
* Microsoft Visual Studio 2015
* Microsoft Visual Studio Tools for Apache Cordova

## Het Project van Visual Studio van vestiging voor AEM Forms app {#setting-up-visual-studio-project-for-aem-forms-app}

Voer de volgende stappen aan opstelling uit AEM Forms app project in Visual Studio.

1. Kopieer het `adobe-lc-mobileworkspace-src-<version>.zip` archief naar de `%HOMEPATH%\Projects` map in Windows 8.1 of Windows 10 met Visual Studio 2015 geïnstalleerd en geconfigureerd.
1. Extraheer het archief in de `%HOMEPATH%\Projects\MobileWorkspace` map.
1. Navigate to the `%HOMEPATH%\Projects\MobileWorkspace\adobe-lc-mobileworkspace-src-[versionsrc]\windows` directory.
1. Open het `CordovaApp.sln` dossier gebruikend Visual Studio 2015 en ga aan de bouw van app van AEM Forms te werk.

## AEM Forms-app samenstellen {#build-aem-forms-app}

Voer de volgende stappen uit om AEM Forms-app te maken en te implementeren.

>[!NOTE]
>
>Gegevens die zijn opgeslagen in het Windows-bestandssysteem voor de toepassing AEM Forms worden niet gecodeerd. Men adviseert dat u een derdehulpmiddel zoals de Encryptie van de Aandrijving van Windows BitLocker gebruikt om schijfgegevens te coderen.

1. In de StandaardToolbar van Visual Studio, uitgezochte **Versie** van drop-down voor bouwstijlwijze.

1. Selecteer Windows-AnyCPU, Windows-x64 of Windows-x86 op basis van uw platform. Windows-AnyCPU wordt aanbevolen.
1. In de Ontdekkingsreiziger van de Oplossing van Visual Studio, klik het project **CordovaApp.Windows** met de rechtermuisknop aan en selecteer **Opslag > Create AppPackages**.

   ![apppackages maken](assets/createapppackages.png)

   De wizard App Packages maken wordt weergegeven.

   Het installatiebestand van CordovaApp.Windows_3.0.2.0_anycpu.appx wordt gemaakt in de map platforms\windows\AppPackages\CordovaApp.Windows_3.0.2.0_anycpu_Test.

   Als de fout optreedt `Retarget to windows 8.1 required`, klikt u met de rechtermuisknop op de fout en selecteert u **Opnieuw toewijzen aan Windows 8.1** in het pop-upmenu.

   ![retarget-oplossing](assets/retarget-solution.png)

1. Selecteer in de wizard App Packages maken de optie weer of u wilt uw app niet uploaden naar de Windows Store en klik op **Volgende**.

   ![createapppackageswizard1](assets/createapppackageswizard1.png)

1. Breng de gewenste wijzigingen aan in de parameters, zoals de versie en uitvoerlocatie van de build van de app.

   ![createapppackageswizard2](assets/createapppackageswizard2.png)

1. Nadat het project is gemaakt, kunt u de app installeren met:

   * Windows PowerShell
   * Visual Studio

   Voor een geslaagde installatie van het `.appx` pakket zijn de volgende items vereist:

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

1. Klik op het dossier PowerShell met de rechtermuisknop aan ( `Add-AppDevPackage.ps1)`, en kies **Looppas met PowerShell**.

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
1. Ga naar **Computerconfiguratie > Systeembeheer > Windows-component > Implementatie** toepassingspakket.
1. Klik met de rechtermuisknop op Alle vertrouwde apps **mogen worden geïnstalleerd**.
1. Klik op **Bewerken** en selecteer **Ingeschakeld**.

1. Click **OK**.

Bewerk het Visual Studio-script dat PowerShell heeft gegenereerd om te voorkomen dat het ontwikkelaarslicentie verwerft.

In het manuscript PowerShell, plaats de variabele: `$NeedDeveloperLicense = $false`.

Voor apparaten die geen domeinverbinding hebben, is de sideladende sleutel van de productactivering vereist. U kunt deze aanschaffen bij een Windows-leverancier.

Voor Windows 8.1 Home Edition, is er geen groepsbeleid, wordt de onderneming zijladen niet toegestaan, en u kunt zich niet bij het met het ondernemingsdomein aansluiten. Implementeer de app op een Windows 8.1 Home Edition-apparaat met een ontwikkelaarslicentie.

Klik [hier](https://blogs.msdn.com/b/mvpawardprogram/archive/2014/03/24/side-loading-deployment-of-windows-store-apps-in-enterprises-step-by-step.aspx)voor meer informatie.

## Het opstellen van een app die Visual Studio gebruikt {#deploying-an-app-using-visual-studio}

Om app op Vensters te installeren gebruikend Visual Studio:

1. Sluit het apparaat aan met extern foutopsporingsprogramma.\
   Zie Windows Store-apps [uitvoeren op een externe computer](https://docs.microsoft.com/en-us/visualstudio/debugger/run-windows-store-apps-on-a-remote-machine)voor meer informatie.

1. Met uw open app in Visual Studio, kies Vensters-x64, Vensters-x86, of Vensters-AnyCPU van de lijst van de Platforms van de Oplossing, en selecteer **Verre Machine**.
1. Uw app wordt geïmplementeerd op de externe computer.

