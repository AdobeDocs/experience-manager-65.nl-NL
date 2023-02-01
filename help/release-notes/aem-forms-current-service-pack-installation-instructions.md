---
title: AEM Forms Patch Installation Instructions for AEM Forms
description: AEM Forms service pack installatieinstructies voor OSGi- en JEE-omgeving
source-git-commit: a470627eb87735dd55edda93c3e2dac4a2c36752
workflow-type: tm+mt
source-wordcount: '1844'
ht-degree: 0%

---


# AEM 6.5 installatie-instructies voor Forms Service Pack {#aem-form-patch-installation-instructions}

## Gegevens vrijgeven

| Product | Adobe Experience Manager 6.5 Forms |
|---|---|
| Versie | 6.5.15.0 |
| Type | Service Pack-release |
| Date | 1 december 2022 |
| URL downloaden | [Laatste AEM Forms-releases](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) |

>[!NOTE]
>
>Zie de nieuwste [Opmerkingen bij de release AEM Service Pack](https://experienceleague.adobe.com/docs/experience-manager-65/release-notes/release-notes.html#forms-6515) voor een volledige lijst van opgeloste problemen.

## Wat is inbegrepen in Experience Manager Forms 6.5

Adobe Experience Manager (AEM) Forms Service Pack bevat nieuwe en verbeterde functies, zoals belangrijke verbeteringen op verzoek van de klant, prestaties, stabiliteit en verbeteringen op het gebied van beveiliging. De de versieservicepacks van AEM Forms met regelmatige tussenpozen om recentste eigenschappen en verbeteringen te verstrekken. Afhankelijk van uw stapel, kies één van de volgende wegen om de dienstpak op uw milieu te downloaden en te installeren:

* [Download en installeer Service Pack op een AEM FormOn JEE-omgeving](#download-and-install-for-jee-service-pack)
* [De download en installeert Service Pack op een AEMVorm op milieu OSGi](#download-and-install-for-osgi-service-pack)

>[!NOTE]
>
> Adobe geeft na elk 6e servicepakket een volledig installatieprogramma uit. AEM 6.5 Forms Service Pack 12 (6.5.12.0) op JEE is het laatste volledige installatieprogramma. Het volledige installatieprogramma biedt ondersteuning voor nieuwe platforms, terwijl het installatieprogramma voor het gewone servicepack alleen foutoplossingen en algemene verbeteringen bevat. Als u een nieuwe installatie uitvoert of van plan bent om de nieuwste software voor uw AEM 6.5 Forms in JEE-omgeving te gebruiken, raadt Adobe aan AEM 6.5.12.0 Forms op het volledige installatieprogramma van JEE te gebruiken dat op 3 maart 2022 wordt uitgebracht in plaats van AEM 6.5 Forms-installatieprogramma dat op 8 april 2019 wordt uitgebracht. Installeer na gebruik van het volledige installatieprogramma het nieuwste servicepakket.

## Download en installeer Service Pack op een AEM FormOn JEE-omgeving {#download-and-install-for-jee-service-pack}

![JEE-installatie](/help/forms/using/assets/jeeinstallation.png)

+++1. Maak back-up van uw bestaande omgeving:

1. Maak een back-up van uw [CRX Repository, Databaseschema en GDS (Global Document Storage)](https://experienceleague.adobe.com/docs/experience-manager-65/forms/administrator-help/aem-forms-backup-recovery/backing-aem-forms-data.html).
1. Maak een back-up van de &lt;*AEM_forms_root*>/implementatiemap. Dit is vereist als u besluit het servicepack te verwijderen.

>[!NOTE]
>
> Voordat u het installatieprogramma voor het AEM servicepack uitvoert, moet u ervoor zorgen dat u schrijftoegangsrechten hebt voor AEM installatiemap.

+++

+++2.Download de vereiste software:

* [AEM Forms op 6.5.15.0 Service Pack in JEE](https://experienceleague.adobe.com/docs/experience-manager-65/release-notes/jee-patch-installer-65.html)
* [AEM 6.5.15.0 Service Pack](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq650%2Fservicepack%2Faem-service-pkg-6.5.15.0.zip)
* [Forms-invoegtoepassing](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faemcloud%2Fpublic%2Faem-forms-addon-2022.12.20.00-220900.zip)
* [Fragmentserver](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq650%2Ffeaturepack%2Forg.apache.felix.http.servlet-api-1.2.0_fragment_full.jar)

+++

+++3. Installeer AEM Forms op JEE service pack:

1. Stop uw toepassingsserver.
1. Het gereedschap Extraheren **AEM Forms op JEE 6.5.15.0 Service Pack installer-archief** op uw vaste schijf:

   * **Windows**
Navigeer naar de juiste directory op de installatiemedia of de installatiemap op de vaste schijf waarnaar u het installatieprogramma hebt gekopieerd en dubbelklik op de knop 
`aemforms65_cfp_install.exe` bestand.

      * (Windows 32-bits) `Windows\Disk1\InstData\VM`
      * (Windows 64-bits) `Windows_64Bit`\ `Disk1\InstData\VM`
   * **Linux®**
Navigeer naar de juiste map en van een shell en type 
`./aem65_cfp_install.bin`.

      * (Linux®) `Linux/Disk1/InstData/NoVM`

   Hiermee wordt een installatiewizard gestart die u door de installatie begeleidt.

1. Klik in het deelvenster Inleiding op **[!UICONTROL Next]**.
1. Op de **Installatiemap kiezen** , controleert u of de weergegeven standaardlocatie correct is voor uw bestaande installatie of klikt u op **[!UICONTROL Browse]** om de alternatieve map te selecteren waarin AEM formulieren zijn geïnstalleerd en klik op **[!UICONTROL Next]**.
1. Lees de overzichtsinformatie van Service Pack en klik **[!UICONTROL Next]**.
1. Lees de informatie van het Pre-installatieoverzicht en klik **[!UICONTROL Install]**.
1. Wanneer de installatie is voltooid, klikt u op **[!UICONTROL Next]** om de snelle reparatie updates op uw geïnstalleerde dossiers toe te passen.
1. **[Alleen voor Windows]:** Voer een van de volgende stappen uit:

   * Schakel de optie **Configuratiebeheer starten** voordat u klikt op **[!UICONTROL Done]**. Uitvoeren **Configuratiebeheer** door **ConfigurationManager.bat** bestand in `[aem-forms root]\configurationManager\bin`.

   * U kunt de selectie van de **Configuratiebeheer starten** voordat u klikt op **[!UICONTROL Done]**. Voor uitvoering **Configuratiebeheer** gebruiken **ConfigurationManager.exe** of **ConfigurationManager_IPv6.exe**, navigeer naar *`<AEMForms_Install_Dir>\configurationManager\bin`* directory en replace [ConfigurationManager.lax](/help/assets/ConfigurationManager.lax) en [ConfigurationManager_IPV6.lax](/help/assets/ConfigurationManager_IPv6.lax) bestanden.

      >[!NOTE]
      >
      > Met de **ConfigurationManager.bat** kunt u voorkomen dat de naam van de .lax-bestanden handmatig wordt bijgewerkt.

1. **[Alleen voor Unix]:** De **Configuratiebeheer starten** selectievakje is standaard ingeschakeld. Klikken **[!UICONTROL Done]** om de Manager van de Configuratie onmiddellijk in werking te stellen of in werking te stellen **Configuratiebeheer** later, schrap **Configuratiebeheer starten** voordat u klikt op **[!UICONTROL Done]**. U kunt beginnen **Configuratiebeheer** later het gebruiken van het aangewezen manuscript in `[AEM_forms_root]/configurationManager/bin` directory.

   U moet de vermelde taken uitvoeren wanneer u de **Configuratiebeheer**:
   * CRX configureren
   * Adobe Experience Manager Forms EAR&#39;s implementeren
   * Adobe Experience Manager Forms-database initialiseren
   * Adobe Experience Manager Forms-componenten implementeren
   * Implementeer en valideer DSC-jars.

1. Afhankelijk van uw toepassingsserver kiest u een van de volgende documenten en volgt u de instructies in het dialoogvenster *Formulieren configureren en implementeren AEM* sectie.

   * [AEM voor JBoss® installeren en implementeren](https://www.adobe.com/go/learn_aemforms_installJBoss_65)
   * [AEM voor WebSphere® installeren en implementeren](https://www.adobe.com/go/learn_aemforms_installWebSphere_65)
   * [AEM Forms for WebLogic installeren en implementeren](https://www.adobe.com/go/learn_aemforms_installWebLogic_65)

>[!NOTE]
>
> Nadat u AEM Forms op het JEE-servicepack hebt geïnstalleerd, moet u het Forms-add-onpakket verwijderen uit `crx-repository\install` voordat u de toepassingsserver opnieuw start. Download het nieuwste Forms add-on pakket van de [Software Distribution Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html).

+++

+++4. Het serverfragment installeren

De installatie is verplicht **servlet-fragment** voor alle toepassingsservers, behalve voor servers die op JBoss® EAP 7.4.0 worden uitgevoerd. U kunt als volgt het serverfragment downloaden en installeren:

1. Als u het fragment niet hebt gedownload, downloadt u het van [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/featurepack/org.apache.felix.http.servlet-api-1.2.0_fragment_full.jar).

1. Start de toepassingsserver, wacht tot de logbestanden zijn gestabiliseerd en controleer de toestand van de bundel.

1. Open Web Console-bundels. De standaard-URL is `http://[Server]:[Port]/system/console/bundles`.

1. Klik op Installeren/Bijwerken. Kies het gedownloade fragment. `org.apache.felix.http.servlet-api-1.2.0_fragment_full.jar`. Klikken **Installeren** of **Bijwerken**. Wacht tot de toepassingsserver is gestabiliseerd

1. Stop de toepassingsserver.

+++

+++5. AEM Service Pack installeren

1. Start de instantie opnieuw vóór de installatie als de updatemodus voor de instantie is geactiveerd (wanneer de instantie is bijgewerkt vanaf een eerdere versie). Adobe raadt aan de toepassing opnieuw te starten als de huidige uptime voor een instantie hoog is.
1. Maak voordat u gaat installeren een momentopname of een nieuwe back-up van uw [!DNL Experience Manager] -instantie.
1. Download het servicepack van [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.15.0.zip). <!-- UPDATE FOR EACH NEW RELEASE -->
1. Pakketbeheer openen en vervolgens selecteren **[!UICONTROL Upload Package]** om het pakket te uploaden. Zie voor meer informatie [Pakketbeheer](/help/sites-administering/package-manager.md).
1. Selecteer het pakket en selecteer vervolgens **[!UICONTROL Install]**.
1. Om de S3 schakelaar bij te werken, stop de instantie na installatie van het Service Pack, vervang de bestaande schakelaar met een nieuw binair dossier dat in de installatiemap wordt verstrekt, en begin de instantie opnieuw. Zie [Amazon S3 Data Store](/help/sites-deploying/data-store-config.md#upgrading-to-a-new-version-of-the-s-connector).

**Automatische installatie**

Er zijn twee verschillende methoden die u automatisch kunt installeren [!DNL ExperienceManager] 6.5.15.0.<!--       UPDATE FOR EACH NEW RELEASE -->

* Plaats het pakket in `../crx-quickstart/install` als de server online beschikbaar is.
Het pakket wordt automatisch geïnstalleerd.

* Gebruik de [HTTP-API van Package Manager](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html). Gebruiken  `cmd=install&recursive=true` zodat de geneste pakketten worden geïnstalleerd.

   >[!NOTE]
   >
   >Experience Manager 6.5.15.0 ondersteunt geen Bootstrap-installatie. <!-- UPDATE FOR EACHNEW RELEASE -->

**De installatie valideren**

Als u wilt weten welke platformen gecertificeerd zijn voor deze release, raadpleegt u de [technische voorschriften](/help/sites-deploying/technical-requirements.md).

1. De pagina met productinformatie (`/system/console/productinfo`) geeft de bijgewerkte versietekenreeks weer `Adobe Experience      Manager (6.5.15.0)` krachtens [!UICONTROL Installed Products].<!-- UPDATE FOR EACH NEW RELEASE -->
1. Alle OSGi-bundels zijn **[!UICONTROL ACTIVE]** of **[!UICONTROL FRAGMENT]** in OSGi Console (de Console van het Gebruik: `/system/console/bundles`).
1. De OSGi-bundel `org.apache.jackrabbit.oak-core` is versie 1.22.13 of hoger (WebConsole gebruiken: `/system/console/     bundles`).

+++

+++6. Experience Manager Forms-invoegtoepassing installeren AEM

1. Controleer of u de [!DNL Experience Manager] service pack.
1. Download het overeenkomstige Forms-add-on-pakket dat is vermeld op [AEM Forms-releases](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=en#forms-updates) voor uw besturingssysteem.
1. Het Forms-invoegtoepassingspakket installeren zoals beschreven in [AEM Forms-add-onpakketten installeren](https://experienceleague.adobe.com/docs/experience-manager-65/forms/install-aem-forms/osgi-installation/installing-configuring-aem-forms-osgi.html?lang=en#install-aem-forms-add-on-package).
1. Als u letters gebruikt in Experience Manager 6.5 Forms, installeert u de [nieuwste AEMFD-compatibiliteitspakket](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html).

+++


<!-- 1. (JBoss only) After installing the patch and configuring the server, delete  tmp  and work directories of JBoss application server.

>[!IMPORTANT]
>
>Before installing [AEM 6.5.15.0 service pack](#install-the-aem-service-pack-install-aem-service-pack), for all the AEM Forms on JEE environments using any application servers other than JBoss EAP 7.4.0: 
> * Install  the [org.apache.felix.http.servlet-api-1.2.0_fragment-full.jar](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/featurepack/org.apache.felix.http.servlet-api-1.2.0_fragment_full.jar) servlet fragment and wait for the application server to stabilize.
>* If you install the latest [AEM service pack (6.5.15.0)](#install-the-aem-service-pack-install-aem-service-pack), prior to the fragment servlet `org.apache.felix.http.servlet-api-1.2.0_fragment-full.jar` on JEE environment, the CRX/bundle and the start page show service unavailable errors, [click here](/help/forms/using/aem-service-pack-installation-solution.md) to know the troubleshooting steps. 

### !-->


## De download en installeert Service Pack op een AEMVorm op milieu OSGi {#download-and-install-for-osgi-service-pack}

![OSGi Installatiestappen](/help/forms/using/assets/osgiinstallation.png)


+++1. Maak back-up van uw bestaande omgeving:

1. Maak een back-up van uw [CRX Repository en Databaseschema](https://experienceleague.adobe.com/docs/experience-manager-65/forms/administrator-help/aem-forms-backup-recovery/backing-aem-forms-data.html).

>[!NOTE]
>
> Als u het de dienstpak van AEM Forms voor relationele gegevensbestand installeert, is het verplicht om steun van DB_schema te nemen.

+++

+++2.Download de vereiste software:

* [AEM 6.5.15.0 Service Pack](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq650%2Fservicepack%2Faem-service-pkg-6.5.15.0.zip)
* [Forms-invoegtoepassing](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faemcloud%2Fpublic%2Faem-forms-addon-2022.12.20.00-220900.zip)

+++

+++3. AEM Service Pack installeren

1. Start de instantie opnieuw vóór de installatie als de updatemodus voor de instantie is geactiveerd (wanneer de instantie is bijgewerkt vanaf een eerdere versie). Adobe raadt aan de toepassing opnieuw te starten als de huidige uptime voor een instantie hoog is.
1. Maak voordat u gaat installeren een momentopname of een nieuwe back-up van uw [!DNL Experience Manager] -instantie.
1. Download het servicepack van [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.15.0.zip). <!-- UPDATE FOR EACH NEW RELEASE -->
1. Pakketbeheer openen en vervolgens selecteren **[!UICONTROL Upload Package]** om het pakket te uploaden. Zie voor meer informatie [Pakketbeheer](/help/sites-administering/package-manager.md).
1. Selecteer het pakket en selecteer vervolgens **[!UICONTROL Install]**.
1. Om de S3 schakelaar bij te werken, stop de instantie na installatie van het Service Pack, vervang de bestaande schakelaar met een nieuw binair dossier dat in de installatiemap wordt verstrekt, en begin de instantie opnieuw. Zie [Amazon S3 Data Store](/help/sites-deploying/data-store-config.md#upgrading-to-a-new-version-of-the-s-connector).

**Automatische installatie**

Er zijn twee verschillende methoden die u automatisch kunt installeren [!DNL Experience Manager] 6.5.15.0.<!--       UPDATE FOR EACH NEW RELEASE -->

* Plaats het pakket in `../crx-quickstart/install` als de server online beschikbaar is. Het pakket wordt automatisch geïnstalleerd.
* Gebruik de [HTTP-API van Package Manager](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html). Gebruiken `cmd=install&recursive=true` zodat de geneste pakketten worden geïnstalleerd.

   >[!NOTE]
   >
   >Experience Manager 6.5.15.0 ondersteunt geen Bootstrap-installatie. <!-- UPDATE FOR EACH NEW RELEASE -->

**De installatie valideren**

Als u wilt weten welke platformen gecertificeerd zijn voor deze release, raadpleegt u de [technische voorschriften](/help/sites-deploying/technical-requirements.md).

1. De pagina met productinformatie (`/system/console/productinfo`) geeft de bijgewerkte versietekenreeks weer `Adobe Experience      Manager (6.5.15.0)` krachtens [!UICONTROL Installed Products]. <!-- UPDATE FOR EACH NEW RELEASE -->

1. Alle OSGi-bundels zijn **[!UICONTROL ACTIVE]** of **[!UICONTROL FRAGMENT]** in de Console OSGi (de Console van het Gebruik: `/system/console/bundles`).

   1. De OSGi-bundel `org.apache.jackrabbit.oak-core` is versie 1.22.13 of hoger (webconsole gebruiken: `/system/console/bundles`).

+++

+++4. Experience Manager Forms-invoegtoepassing installeren AEM

1. Controleer of u de [!DNL Experience Manager] service pack.
1. Download het overeenkomstige Forms-add-on-pakket dat is vermeld op [AEM Forms-releases](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=en#forms-updates) voor uw besturingssysteem.
1. Het Forms-invoegtoepassingspakket installeren zoals beschreven in [AEM Forms-add-onpakketten installeren](https://experienceleague.adobe.com/docs/experience-manager-65/forms/install-aem-forms/osgi-installation/installing-configuring-aem-forms-osgi.html?lang=en#install-aem-forms-add-on-package).
1. Als u letters gebruikt in Experience Manager 6.5 Forms, installeert u de [nieuwste AEMFD-compatibiliteitspakket](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html).

+++

## Problemen oplossen

* Installeer de AEM Forms-servicepacks opnieuw als er een fout optreedt tijdens de installatie. Neem contact op met het productteam als het probleem zich blijft voordoen.

* Indien **Dialoogvenster over interface van pakketbeheer** Sluit tijdens de installatie van het de dienstpak af, wacht op foutenlogboeken om zich te stabiliseren alvorens tot de plaatsing toegang te hebben. Wacht op de specifieke logboeken met betrekking tot het verwijderen van de updaterbundel alvorens wordt verzekerd dat de installaties succesvol zijn. Dit probleem doet zich doorgaans voor in de Safari-browser, maar kan soms ook in elke browser optreden.

* Controleer de monitorlogboeken (error.log) zodra de installatie voor om het even welke activiteit volledig is. Wacht een paar minuten totdat er geen activiteit in de logboeken voorkomt. Start de AEM opnieuw.

* Als u een **service-niet-beschikbare fout** na installatie van het nieuwste AEM Forms 6.5.15.0-servicepakket, [het serverfragment en de bundel installeren](/help/forms/using/aem-service-pack-installation-solution.md) om de fout te herstellen.


