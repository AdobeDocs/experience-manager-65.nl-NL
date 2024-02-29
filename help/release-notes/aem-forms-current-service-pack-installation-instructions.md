---
title: AEM Forms Patch Installation Instructions for AEM Forms
description: AEM Forms service pack installatie-instructies voor OSGi- en JEE-omgeving
exl-id: ae4c7e9d-9af8-4288-a6f9-e3bcbe7d153d
source-git-commit: 181d5ffcefcf55aa75cfaf29c42dbd8d8d665398
workflow-type: tm+mt
source-wordcount: '1728'
ht-degree: 0%

---

# AEM 6.5 installatie-instructies voor Forms Service Pack {#aem-form-patch-installation-instructions}

## Gegevens vrijgeven

| Product | Adobe Experience Manager 6.5 Forms |
|---|---|
| Versie | 6.5.20,0 |
| Type | Service Pack-release |
| Datum | 29 februari 2024 |
| URL downloaden | [Nieuwste AEM Forms-releases](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html) |

>[!NOTE]
>
>Zie de nieuwste [Opmerkingen bij de release AEM Service Pack](https://experienceleague.adobe.com/docs/experience-manager-65/release-notes/release-notes.html) voor een volledige lijst van opgeloste problemen.

## Wat bevat Experience Manager Forms 6.5

Adobe Experience Manager (AEM) Forms Service Pack bevat nieuwe en verbeterde functies, zoals belangrijke verbeteringen op verzoek van de klant, prestaties, stabiliteit en verbeteringen op het gebied van beveiliging. De de versieservicepacks van AEM Forms met regelmatige tussenpozen om recentste eigenschappen en verbeteringen te verstrekken. Afhankelijk van uw technologiestapel, kies één van de volgende wegen om de dienstpak op uw milieu te downloaden en te installeren:

* [Download en installeer Service Pack op een AEM FormOn JEE-omgeving](#download-and-install-for-jee-service-pack)
* [De download en installeert Service Pack op een AEMVorm op milieu OSGi](#download-and-install-for-osgi-service-pack)

>[!NOTE]
>
> * Adobe geeft een volledig installatieprogramma elke zesde service pack uit. AEM 6.5 Forms Service Pack 18 (6.5.18.0) is het nieuwste volledige installatieprogramma voor JEE. Het volledige installatieprogramma ondersteunt nieuwe platforms, terwijl het installatieprogramma voor het gewone servicepack nieuwe functies, gecorrigeerde en algemene verbeteringen bevat. Als u een nieuwe installatie uitvoert of van plan bent om de nieuwste software voor uw AEM 6.5 Forms te gebruiken in JEE-omgeving, raadt de Adobe aan AEM 6.5.18.0 Forms te gebruiken op het volledige installatieprogramma van JEE dat op 31 augustus 2023 wordt uitgebracht in plaats van AEM 6.5 Forms-installatieprogramma dat op 8 april 2019 wordt uitgebracht of AEM 6.5.12.00 3 maart 2022. Installeer na gebruik van het volledige installatieprogramma het nieuwste servicepakket.
> * De AEM Forms-functie, zoals Adaptive Forms, is beschikbaar in [AEM 6.5 QuickStart](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/deploy.html), uitsluitend bestemd zijn voor exploratie en evaluatie. Voor productiedoeleinden is het van essentieel belang een geldige vergunning voor AEM Forms te verkrijgen.

<!--

## Prerequisites {#prerequisites}

From AEM Service Pack 6.5.19.0 and onwards, XMLFM (XML output) will be available in 64-bit only, therefore you require the latest [Microsoft Visual C++ Redistributable (2015-2022) 64-bit](https://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist?view=msvc-170) to be installed on Windows Server prior to JEE or OSGi installation.

>[!NOTE]
> This prerequisite is required in addition to the already existing Microsoft Visual C++ Redistributable 32-bit.

-->

## Download en installeer Service Pack op een AEM FormOn JEE-omgeving {#download-and-install-for-jee-service-pack}

<!--
![JEE Installation](/help/forms/using/assets/jeeinstallation.png) -->

+++1. Maak back-ups van uw bestaande omgeving

1. Maak een back-up van uw [CRX Repository, Databaseschema en GDS (Global Document Storage)](https://experienceleague.adobe.com/docs/experience-manager-65/forms/administrator-help/aem-forms-backup-recovery/backing-aem-forms-data.html).
1. Maak een back-up van de &lt;*AEM_forms_root*>/implementatiemap.

>[!NOTE]
>
> Voordat u het installatieprogramma voor het AEM servicepack uitvoert, moet u ervoor zorgen dat u schrijftoegangsrechten hebt voor AEM installatiemap.

+++

+++2. De vereiste software downloaden

* [AEM Forms on JEE Service Pack](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html)
* [AEM Service Pack](https://experienceleague.adobe.com/docs/experience-manager-65/release-notes/release-notes.html)
* [Forms-invoegtoepassing](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html)
* [Fragmentserver](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq650%2Ffeaturepack%2Forg.apache.felix.http.servlet-api-1.2.0_fragment_full.jar)

+++

+++3. Microsoft Visual C++ Redistributable pakketten installeren

* Download en installeer de [64-bits versie van Microsoft Visual C++ Redistributable pakketten voor Visual Studio 2015, 2017, 2019, en 2022](https://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist?view=msvc-170#visual-studio-2015-2017-2019-and-2022) op de computer waarop AEM 6.5 Forms is geïnstalleerd.

>[!NOTE]
>
> Zorg ervoor dat u Redistributable installeert, zelfs als een vorige versie wordt geïnstalleerd, om de beschikbaarheid van de recentste versie te waarborgen.

+++

+++4. Installeer AEM Forms op JEE service pack:

1. Stop uw toepassingsserver.
1. Het gereedschap **AEM Forms on JEE Service Pack installer archiveren** op uw vaste schijf:

   * **Windows**
Navigeer naar de juiste directory op de installatiemedia of de installatiemap op de vaste schijf waarnaar u het installatieprogramma hebt gekopieerd en dubbelklik op de knop `aemforms65_cfp_install.exe` bestand.

      * (Windows 32-bits) `Windows\Disk1\InstData\VM`
      * (Windows 64-bits) `Windows_64Bit`\ `Disk1\InstData\VM`

   * **Linux®**
Navigeer naar de juiste map en van een shell en type `./aem65_cfp_install.bin`.

      * (Linux®) `Linux/Disk1/InstData/NoVM`

   Hiermee wordt een installatiewizard gestart die u door de installatie begeleidt.

1. Klik in het deelvenster Inleiding op **[!UICONTROL Next]**.
1. Op de **Installatiemap kiezen** , controleert u of de weergegeven standaardlocatie correct is voor uw bestaande installatie of klikt u op **[!UICONTROL Browse]** om de alternatieve map te selecteren waarin AEM formulieren zijn geïnstalleerd en klik op **[!UICONTROL Next]**.
1. Lees de overzichtsinformatie van Service Pack en klik **[!UICONTROL Next]**.
1. Lees de informatie van het Pre-installatieoverzicht en klik **[!UICONTROL Install]**.
1. Wanneer de installatie is voltooid, klikt u op **[!UICONTROL Next]** om de snelle reparatie updates op uw geïnstalleerde dossiers toe te passen.
1. **[Alleen voor Windows]:** Voer een van de volgende stappen uit:

   * Schakel de optie **Configuratiebeheer starten** voordat u klikt op **[!UICONTROL Done]**. Uitvoeren **Configuratiebeheer** door de **ConfigurationManager.bat** bestand in `[aem-forms root]\configurationManager\bin`.

   * U kunt de selectie van de **Configuratiebeheer starten** voordat u klikt op **[!UICONTROL Done]**. Voor uitvoering **Configuratiebeheer** gebruiken **ConfigurationManager.exe** of **ConfigurationManager_IPv6.exe**, navigeer naar *`<AEMForms_Install_Dir>\configurationManager\bin`* en vervangt u de **ConfigurationManager.lax** en **ConfigurationManager_IPV6.lax** uiterlijk [ConfigurationManager.lax](/help/assets/ConfigurationManager.lax) en [ConfigurationManager_IPV6.lax](/help/assets/ConfigurationManager_IPv6.lax) bestanden, zoeken en vervangen **as-1.4.1.1.jar** with **as-1.4.1.2.jar** in deze twee bestanden.

     >[!NOTE]
     >
     >* Het bijwerken van of het vervangen van **ConfigurationManager.bat** kunt u voorkomen dat de .lax-bestanden handmatig worden bijgewerkt.

1. **[Alleen voor Unix]:** De **Configuratiebeheer starten** selectievakje is standaard ingeschakeld. Klikken **[!UICONTROL Done]** om de Manager van de Configuratie onmiddellijk in werking te stellen of te lopen **Configuratiebeheer** later, schrap **Configuratiebeheer starten** voordat u klikt op **[!UICONTROL Done]**. U kunt beginnen **Configuratiebeheer** later het gebruiken van het aangewezen manuscript in `[AEM_forms_root]/configurationManager/bin` directory.

1. Kies afhankelijk van uw toepassingsserver een van de volgende documenten en volg de instructies in het dialoogvenster *Formulieren configureren en implementeren AEM* sectie.

   * [AEM voor JBoss® installeren en implementeren](https://www.adobe.com/go/learn_aemforms_installJBoss_65)
   * [AEM voor WebSphere® installeren en implementeren](https://www.adobe.com/go/learn_aemforms_installWebSphere_65)
   * [AEM Forms for WebLogic installeren en implementeren](https://www.adobe.com/go/learn_aemforms_installWebLogic_65)
   * [AEM voor JBoss® Cluster installeren en implementeren](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-5/forms/pdf/install-cluster-jboss.pdf)
   * [AEM voor WebSphere®-cluster installeren en implementeren](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-5/forms/pdf/install-cluster-websphere.pdf)
   * [AEM Forms for WebLogic-cluster installeren en implementeren](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-5/forms/pdf/install-cluster-weblogic.pdf)


>[!NOTE]
>
>* Nadat u AEM Forms op het JEE-servicepack hebt geïnstalleerd, moet u het Forms-add-onpakket verwijderen uit `crx-repository\install` voordat u de toepassingsserver opnieuw start. Download het nieuwste Forms add-on pakket van de [Software Distribution Portal](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html).
>* Het wordt aanbevolen de SDK opnieuw te starten met de opdracht &#39;Ctrl + C&#39;. Het opnieuw opstarten van de AEM SDK met behulp van alternatieve methoden, bijvoorbeeld het stoppen van Java-processen, kan leiden tot inconsistenties in de AEM ontwikkelomgeving.

+++

+++5. Installeer het serverfragment (AEM Service Pack 6.5.14.0 of eerder)

>[!NOTE]
>
> * Als u een upgrade uitvoert van **AEM Service Pack 6.5.15.0**, de installatie van de **servlet-fragment** is niet vereist. Voor versies **AEM Service Pack 6.5.14.0** of eerder is het verplicht het servletfragment te installeren.
> * Het is verplicht om de **servlet-fragment** voor alle toepassingsservers behalve de servers die worden uitgevoerd **JBoss® EAP 7.4.0**.


U kunt als volgt het serverfragment downloaden en installeren:

1. Als u het fragment niet hebt gedownload, downloadt u het van [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/featurepack/org.apache.felix.http.servlet-api-1.2.0_fragment_full.jar).

2. Start de toepassingsserver, wacht tot de logbestanden zijn gestabiliseerd en controleer de toestand van de bundel.

3. Open Web Console-bundels. De standaard-URL is `http://[Server]:[Port]/system/console/bundles`.

4. Klik op Installeren/Bijwerken. Kies het gedownloade fragment. `org.apache.felix.http.servlet-api-1.2.0_fragment_full.jar`. Klikken **Installeren** of **Bijwerken**. Wacht tot de toepassingsserver is gestabiliseerd

5. Stop de toepassingsserver.

+++

+++6. AEM Service Pack installeren

1. Start de instantie opnieuw vóór de installatie als de updatemodus voor de instantie is geactiveerd (wanneer de instantie is bijgewerkt vanaf een eerdere versie). Adobe raadt aan de toepassing opnieuw te starten als de huidige uptime voor een instantie hoog is.
1. Maak een momentopname of een nieuwe back-up van uw [!DNL Experience Manager] -instantie.
1. Download het servicepack van [Softwaredistributie](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html). <!-- UPDATE FOR EACH NEW RELEASE -->
1. Pakketbeheer openen en vervolgens selecteren **[!UICONTROL Upload Package]** om het pakket te uploaden. Zie voor meer informatie [Pakketbeheer](/help/sites-administering/package-manager.md).
1. Selecteer het pakket en selecteer **[!UICONTROL Install]**.

**Automatische installatie**

Er zijn twee verschillende methoden die u automatisch kunt installeren [!DNL ExperienceManager] service pack.<!--       UPDATE FOR EACH NEW RELEASE -->

* Plaats het pakket in `../crx-quickstart/install` als de server online beschikbaar is.
Het pakket wordt automatisch geïnstalleerd.

* Gebruik de [HTTP-API van Package Manager](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html). Gebruiken  `cmd=install&recursive=true` zodat de geneste pakketten worden geïnstalleerd.

  >[!NOTE]
  >
  >Het de dienstpak van de Experience Manager steunt geen Bootstrap installatie. <!-- UPDATE FOR EACH NEW RELEASE -->

  **De installatie valideren**

  Als u wilt weten welke platformen gecertificeerd zijn voor deze release, raadpleegt u de [technische voorschriften](/help/sites-deploying/technical-requirements.md).

   1. De pagina met productinformatie (`/system/console/productinfo`) geeft de bijgewerkte versietekenreeks weer `Adobe Experience Manager (spversion)` krachtens [!UICONTROL Installed Products].<!-- UPDATE FOR EACH NEW RELEASE -->
   1. Alle OSGi-pakketten zijn **[!UICONTROL ACTIVE]** of **[!UICONTROL FRAGMENT]** in OSGi Console (de Console van het Gebruik: `/system/console/bundles`).
   1. De OSGi-bundel `org.apache.jackrabbit.oak-core` is versie 1.22.14 of hoger (WebConsole gebruiken: `/system/console/bundles`).

+++

+++7. Experience Manager Forms-invoegtoepassing installeren AEM

1. Controleer of u de [!DNL Experience Manager] service pack.
1. Download het overeenkomstige Forms-add-on-pakket dat is vermeld op [AEM Forms-releases](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html) voor uw besturingssysteem.
1. Het Forms-invoegtoepassingspakket installeren zoals beschreven in [AEM Forms-add-onpakketten installeren](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html).
1. Als u letters gebruikt in Experience Manager 6.5 Forms, installeert u de [nieuwste pakket AEMFD-compatibiliteit](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html).

+++

## De download en installeert Service Pack op een AEMVorm op milieu OSGi {#download-and-install-for-osgi-service-pack}


<!-- ![OSGi Installation Steps](/help/forms/using/assets/osgiinstallation.png)
-->

+++1. Maak back-ups van uw bestaande omgeving

1. Maak een back-up van uw [CRX Repository en Databaseschema](https://experienceleague.adobe.com/docs/experience-manager-65/forms/administrator-help/aem-forms-backup-recovery/backing-aem-forms-data.html).

>[!NOTE]
>
> Als u het de dienstpak van AEM Forms voor relationele gegevensbestand installeert, is het verplicht om steun van DB_schema te nemen.

+++

+++2. De vereiste software downloaden

* [AEM Service Pack](https://experienceleague.adobe.com/docs/experience-manager-65/release-notes/release-notes.html)
* [Forms-invoegtoepassing](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html)

+++

+++ 3. Installeer Microsoft Visual C++ Redistributable pakketten

* Download en installeer de [64-bits versie van Microsoft Visual C++ Redistributable pakketten voor Visual Studio 2015, 2017, 2019, en 2022](https://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist?view=msvc-170#visual-studio-2015-2017-2019-and-2022) op de computer waarop AEM 6.5 Forms is geïnstalleerd.

>[!NOTE]
>
>
> Zorg ervoor dat u Redistributable installeert, zelfs als een vorige versie wordt geïnstalleerd, om de beschikbaarheid van de recentste versie te waarborgen.

+++

+++4. AEM Service Pack installeren

1. Start de instantie opnieuw vóór de installatie als de updatemodus voor de instantie is geactiveerd (wanneer de instantie is bijgewerkt vanaf een eerdere versie). Adobe raadt aan de toepassing opnieuw te starten als de huidige uptime voor een instantie hoog is.
1. Maak een momentopname of een nieuwe back-up van uw [!DNL Experience Manager] -instantie.
1. Download het servicepack van [Softwaredistributie](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html). <!-- UPDATE FOR EACH NEW RELEASE -->
1. Pakketbeheer openen en vervolgens selecteren **[!UICONTROL Upload Package]** om het pakket te uploaden. Zie voor meer informatie [Pakketbeheer](/help/sites-administering/package-manager.md).
1. Selecteer het pakket en selecteer **[!UICONTROL Install]**.

**Automatische installatie**

Er zijn twee verschillende methoden die u automatisch kunt installeren [!DNL Experience Manager] service pack.<!--  UPDATE FOR EACH NEW RELEASE -->

* Plaats het pakket in `../crx-quickstart/install` als de server online beschikbaar is. Het pakket wordt automatisch geïnstalleerd.
* Gebruik de [HTTP-API van Package Manager](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html). Gebruiken `cmd=install&recursive=true` zodat de geneste pakketten worden geïnstalleerd.

  >[!NOTE]
  >
  >Het de dienstpak van de Experience Manager steunt geen Bootstrap installatie. <!-- UPDATE FOR EACH NEW RELEASE -->

  **De installatie valideren**

  Als u wilt weten welke platformen gecertificeerd zijn voor deze release, raadpleegt u de [technische voorschriften](/help/sites-deploying/technical-requirements.md).

   1. De pagina met productinformatie (`/system/console/productinfo`) geeft de bijgewerkte versietekenreeks weer `Adobe Experience Manager (spversion)` krachtens [!UICONTROL Installed Products]. <!-- UPDATE FOR EACH NEW RELEASE -->

   1. Alle OSGi-pakketten zijn **[!UICONTROL ACTIVE]** of **[!UICONTROL FRAGMENT]** in de Console OSGi (de Console van het Gebruik: `/system/console/bundles`).

      1. De OSGi-bundel `org.apache.jackrabbit.oak-core` is versie 1.22.14 of hoger (webconsole gebruiken: `/system/console/bundles`).

+++

+++4. Invoegpakket voor Adobe Experience Manager Forms (AEM) installeren

1. Controleer of u de [!DNL Experience Manager] service pack.
1. Download het overeenkomstige Forms-add-on-pakket dat is vermeld op [AEM Forms-releases](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html) voor uw besturingssysteem.
1. Het Forms-invoegtoepassingspakket installeren zoals beschreven in [AEM Forms-add-onpakketten installeren](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html).
1. Als u letters gebruikt in Experience Manager 6.5 Forms, installeert u de [nieuwste pakket AEMFD-compatibiliteit](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html).

+++

## Problemen oplossen

* Indien **Dialoogvenster over interface van pakketbeheer** Sluit tijdens de installatie van het de dienstpak af, wacht op foutenlogboeken om zich te stabiliseren alvorens tot de plaatsing toegang te hebben. Wacht op de specifieke logboeken met betrekking tot het verwijderen van de updaterbundel alvorens wordt verzekerd dat de installaties succesvol zijn. Dit probleem doet zich doorgaans voor in de Safari-browser, maar kan soms ook in elke browser optreden.

* Controleer de monitorlogboeken (error.log) zodra de installatie voor om het even welke activiteit volledig is. Wacht een paar minuten totdat er geen activiteit in de logboeken voorkomt. Start de AEM opnieuw.

* Voor het geval u een **service-niet-beschikbare fout** na de installatie van het servicepakket AEM Forms 6.5.15.0 of hoger, [het serverfragment en de bundel installeren](/help/forms/using/aem-service-pack-installation-solution.md) om de fout te herstellen.
