---
title: AEM Forms Patch Installation Instructions for AEM Forms
description: AEM Forms service pack installatie-instructies voor OSGi- en JEE-omgeving
solution: Experience Manager
feature: Release Information
role: User,Admin,Architect,Developer
exl-id: ae4c7e9d-9af8-4288-a6f9-e3bcbe7d153d
source-git-commit: 652878504d2225e50ea14885ec96bdd408f77ed0
workflow-type: tm+mt
source-wordcount: '1698'
ht-degree: 0%

---

# Installatie-instructies voor AEM 6.5 Forms Service Pack {#aem-form-patch-installation-instructions}

## Gegevens vrijgeven

| Product | Adobe Experience Manager 6.5 Forms |
|---|---|
| Versie | 6.5.22.0 |
| Type | Service Pack-release |
| Datum | 29 november 2024 |
| URL downloaden | [ Laatste versies van AEM Forms ](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html) |

>[!NOTE]
>
>Zie de recentste [ Nota&#39;s van de Versie van het Pak van de Dienst van AEM ](https://experienceleague.adobe.com/docs/experience-manager-65/release-notes/release-notes.html) voor een volledige lijst van vaste kwesties.

## Wat bevat Experience Manager Forms 6.5

Adobe Experience Manager (AEM) Forms Service Pack bevat nieuwe en verbeterde functies, zoals belangrijke verbeteringen op verzoek van de klant, prestaties, stabiliteit en verbeteringen op het gebied van beveiliging. De de versieservicepacks van AEM Forms met regelmatige tussenpozen om recentste eigenschappen en verbeteringen te verstrekken. Afhankelijk van uw technologiestapel, kies één van de volgende wegen om de dienstpak op uw milieu te downloaden en te installeren:

* [ Download en installeer het Pak van de Dienst op een Vorm van AEM op milieu JEE ](#download-and-install-for-jee-service-pack)
* [ Download en installeer het Pak van de Dienst op een Vorm van AEM op milieu OSGi ](#download-and-install-for-osgi-service-pack)

>[!NOTE]
>
> * Adobe geeft elk zesde servicepakket een volledig installatieprogramma uit. AEM 6.5 Forms Service Pack 18 (6.5.18.0) is het nieuwste volledige installatieprogramma voor JEE. Het volledige installatieprogramma ondersteunt nieuwe platforms, terwijl het installatieprogramma voor het gewone servicepack nieuwe functies, gecorrigeerde en algemene verbeteringen bevat. Als u een nieuwe installatie uitvoert of van plan bent om de nieuwste software voor uw AEM 6.5 Forms te gebruiken in JEE-omgeving, raadt Adobe aan AEM 6.5.18.0 Forms te gebruiken op het volledige installatieprogramma van JEE dat op 31 augustus 2023 wordt uitgebracht in plaats van het installatieprogramma van AEM 6.5 Forms dat op 8 april 2019 is uitgebracht, of AEM 6.5.12.0 Forms Installer dat op 322222222222. Installeer na gebruik van het volledige installatieprogramma het nieuwste servicepakket.
> * De eigenschap van AEM Forms, zoals Aangepast Forms, beschikbaar in [ AEM 6.5 QuickStart ](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/deploy.html), is voorgenomen voor exploratie en evaluatiedoeleinden slechts. Voor productiedoeleinden is het van essentieel belang een geldige vergunning voor AEM Forms te verkrijgen.

<!--

## Prerequisites {#prerequisites}

From AEM Service Pack 6.5.19.0 and onwards, XMLFM (XML output) will be available in 64-bit only, therefore you require the latest [Microsoft Visual C++ Redistributable (2015-2022) 64-bit](https://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist?view=msvc-170) to be installed on Windows Server prior to JEE or OSGi installation.

>[!NOTE]
> This prerequisite is required in addition to the already existing Microsoft Visual C++ Redistributable 32-bit.

-->

## Service Pack downloaden en installeren op een AEM-formulier in een JEE-omgeving {#download-and-install-for-jee-service-pack}

<!--
![JEE Installation](/help/forms/using/assets/jeeinstallation.png) -->

+++1. Maak back-ups van uw bestaande omgeving

1. Maak een file uw [ Bewaarplaats van CRX, het Schema van het Gegevensbestand, en GDS (Globale Opslag van het Document) ](https://experienceleague.adobe.com/docs/experience-manager-65/forms/administrator-help/aem-forms-backup-recovery/backing-aem-forms-data.html).
1. Maak een back-up van de map &lt;*AEM_forms_root*>/distribueren.

>[!NOTE]
>
> Controleer voordat u het installatieprogramma voor het AEM-servicepack uitvoert of u schrijftoegangsrechten hebt in de installatiemap van AEM.

+++

+++2. De vereiste software downloaden

* [ AEM Forms op het Pak van de Dienst JEE ](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html)

* [ Servlet van het Fragment ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq650%2Ffeaturepack%2Forg.apache.felix.http.servlet-api-1.2.0_fragment_full.jar)

* [ AEM Service Pack ](https://experienceleague.adobe.com/docs/experience-manager-65/release-notes/release-notes.html)
* [ Forms toe:voegen-op pakket ](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html)


+++

+++3. Microsoft Visual C++ Redistributable pakketten installeren

* De download en installeert [ versie met 64 bits van Microsoft Visual C++ Redistributable pakketten voor Visual Studio 2015, 2017, 2019, en 2022 ](https://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist?view=msvc-170#visual-studio-2015-2017-2019-and-2022) op de computer waar AEM 6.5 Forms geïnstalleerd is.

>[!NOTE]
>
> Zorg ervoor dat u Redistributable installeert, zelfs als een vorige versie wordt geïnstalleerd, om de beschikbaarheid van de recentste versie te waarborgen.

+++

+++4. Installeer AEM Forms op JEE service pack:

1. Stop uw toepassingsserver.
1. Extraheer **AEM Forms op het installateursarchief van het Pak van de Dienst JEE** aan uw harde aandrijving:

   * **Vensters**
Navigeer naar de juiste map op de installatiemedia of -map op de vaste schijf waarnaar u hebt gekopieerd     en dubbelklikt u op het `aemforms65_cfp_install.exe` -bestand.

      * (Windows 32-bits) `Windows\Disk1\InstData\VM`
      * (Windows 64-bits) `Windows_64Bit`\ `Disk1\InstData\VM`

   * **Linux®**
Navigeer naar de juiste map en van een shell en type `./aem65_cfp_install.bin` .

      * (Linux®) `Linux/Disk1/InstData/NoVM`

   Hiermee wordt een installatiewizard gestart die u door de installatie begeleidt.

1. Klik in het deelvenster Inleiding op **[!UICONTROL Next]** .
1. Op **kies installeer het scherm van de Omslag**, verifieer dat de getoonde standaardplaats voor uw bestaande installatie correct is, of klik **[!UICONTROL Browse]** om de afwisselende omslag te selecteren waar de vormen van AEM worden geïnstalleerd, en **[!UICONTROL Next]** te klikken.
1. Lees de samenvattingsinformatie van Service Pack en klik **[!UICONTROL Next]**.
1. Lees de informatie over het pre-installatieoverzicht en klik op **[!UICONTROL Install]** .
1. Wanneer de installatie is voltooid, klikt u op **[!UICONTROL Next]** om de snelle reparatie-updates toe te passen op de geïnstalleerde bestanden.
1. **[slechts voor Vensters ]:** voer één van de volgende stap uit:

   * Of schrap de **optie van de Manager van de Configuratie van het Begin** alvorens u **[!UICONTROL Done]** klikt. Voer **Manager van de Configuratie** in werking door het {**dossier 3} te gebruiken 2&rbrace; ConfigurationManager.bat in `[aem-forms root]\configurationManager\bin`.**

   * Of schrap de **optie van de Manager van de Configuratie van het Begin** alvorens u **[!UICONTROL Done]** klikt. Alvorens **Manager van de Configuratie in werking te stellen** gebruikend **ConfigurationManager.exe** of **ConfigurationManager_IPv6.exe**, navigeer aan *`<AEMForms_Install_Dir>\configurationManager\bin`* folder en vervang **ConfigurationManager.lax** en **ConfigurationManager_IPV6.lax** met recentste [ ConfigurationManager.lax ](/help/assets/ConfigurationManager.lax) en [ ConfigurationManager_IPV6.lax ](/help/assets/ConfigurationManager_IPv6.lax) dossiers, Onderzoek, en vervang **as- 1.4.1.1 .jar** met **as- 1.4.1.2 .jar** in deze twee dossiers.

     >[!NOTE]
     >
     >* Het bijwerken van of het vervangen van het {**dossier 0} ConfigurationManager.bat helpt u om het bijwerken van de .lax dossiers manueel te vermijden.**

1. **[voor op unix-Gebaseerd slechts ]:** het **de controlevakje van de Manager van de Configuratie van het Begin** wordt geselecteerd door gebrek. Klik **[!UICONTROL Done]** om de Manager van de Configuratie in werking te stellen onmiddellijk of **de Manager van de Configuratie** later in werking te stellen, schrap de **optie van de Manager van de Configuratie van het Begin** alvorens u **[!UICONTROL Done]** klikt. U kunt **Manager van de Configuratie** later beginnen gebruikend het aangewezen manuscript in de `[AEM_forms_root]/configurationManager/bin` folder.

1. Afhankelijk van uw toepassingsserver, kies één van de volgende documenten en volg de instructies in *het Vormen en het Opstellen van de vormen van AEM* sectie.

   * [ het Installeren van en het Opstellen van de vormen van AEM voor JBoss® ](https://www.adobe.com/go/learn_aemforms_installJBoss_65)
   * [ het Installeren van en het Opstellen van de vormen van AEM voor WebSphere® ](https://www.adobe.com/go/learn_aemforms_installWebSphere_65)
   * [ het Installeren van en het Opstellen van AEM Forms voor WebLogic ](https://www.adobe.com/go/learn_aemforms_installWebLogic_65)
   * [ het Installeren van en het Opstellen van de vormen van AEM voor Cluster JBoss® ](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-5/forms/pdf/install-cluster-jboss.pdf)
   * [ Installerend en het Opstellen van de vormen van AEM voor Cluster WebSphere® ](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-5/forms/pdf/install-cluster-websphere.pdf)
   * [ het Installeren van en het Opstellen van AEM Forms voor Cluster WebLogic ](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-5/forms/pdf/install-cluster-weblogic.pdf)


>[!NOTE]
>
>* Nadat u AEM Forms op het JEE-servicepakket hebt geïnstalleerd, moet u het invoegpakket voor Forms uit de `crx-repository\install` -map verwijderen voordat u de toepassing opnieuw start. Download het recentste Forms toe:voegen-op pakket van het [ portaal van de Distributie van de Software ](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html).
>* U wordt aangeraden de SDK opnieuw op te starten met de opdracht &#39;Ctrl + C&#39;. Het opnieuw opstarten van de AEM SDK met behulp van alternatieve methoden, bijvoorbeeld het stoppen van Java-processen, kan leiden tot inconsistenties in de AEM-ontwikkelomgeving.
>* Voor [ Hotfix voor het Verhelpen van de Kwetsbaarheid van het Kader van de Lente voor AEM Forms op JEE ](/help/release-notes/aem-forms-hotfix.md), wanneer het opstellen in een clustermilieu, is het essentieel om ervoor te zorgen dat de merktekens JDK 17 beginnen te gebruiken.

+++

+++5. Installeer het servletfragment als niet geïnstalleerd (**Verplicht stap**)

<!-- >[!NOTE] > > * If you are upgrading from **AEM Service Pack 6.5.15.0**, the installation of the **servlet fragment** is not required. For versions **AEM Service Pack 6.5.14.0** or earlier, it is **mandatory to install** the servlet fragment. -->

U kunt als volgt het serverfragment downloaden en installeren:

1. Als u niet het fragment hebt gedownload, download het van [ Distributie van de Software ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/featurepack/org.apache.felix.http.servlet-api-1.2.0_fragment_full.jar).

2. Start de toepassingsserver, wacht tot de logbestanden zijn gestabiliseerd en controleer de toestand van de bundel.

3. Open Web Console-bundels. De standaard-URL is `http://[Server]:[Port]/system/console/bundles` .

4. Klik op Installeren/Bijwerken. Kies het gedownloade fragment, `org.apache.felix.http.servlet-api-1.2.0_fragment_full.jar` . Klik **installeren** of **Update**. Wacht tot de toepassingsserver is gestabiliseerd

5. Stop de toepassingsserver.

+++

+++6. AEM Service Pack installeren

1. Start de instantie opnieuw vóór de installatie als de updatemodus voor de instantie is geactiveerd (wanneer de instantie is bijgewerkt vanaf een eerdere versie). Adobe raadt aan de toepassing opnieuw te starten als de huidige uptime voor een instantie hoog is.
1. Maak voordat u gaat installeren een momentopname of een nieuwe back-up van de [!DNL Experience Manager] -instantie.
1. Download het de dienstpak van [ Distributie van de Software ](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html). <!-- UPDATE FOR EACH NEW RELEASE -->
1. Open Package Manager en selecteer vervolgens **[!UICONTROL Upload Package]** om het pakket te uploaden. Om meer te weten, zie [ Manager van het Pakket ](/help/sites-administering/package-manager.md).
1. Selecteer het pakket en selecteer vervolgens **[!UICONTROL Install]** .

**Automatische installatie**

Er zijn twee verschillende methodes die u kunt gebruiken om [!DNL ExperienceManager] de dienstpak automatisch te installeren.<!--       UPDATE FOR EACH NEW RELEASE -->

* Plaats het pakket in de map `../crx-quickstart/install` wanneer de server online beschikbaar is.
Het pakket is      automatisch geïnstalleerd.

* Gebruik [ HTTP API van de Manager van het Pakket ](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html). Gebruik `cmd=install&recursive=true` om de geneste pakketten te installeren.

  >[!NOTE]
  >
  >Experience Manager Service Pack biedt geen ondersteuning voor Bootstrap-installatie. <!-- UPDATE FOR EACH NEW RELEASE -->

  **bevestigt de installatie**

  Om de platforms te kennen die om met deze versie worden verklaard te werken, zie de [ technische vereisten ](/help/sites-deploying/technical-requirements.md).

   1. Op de pagina met productinformatie (`/system/console/productinfo`) wordt de bijgewerkte versietekenreeks weergegeven `Adobe Experience Manager (spversion)` onder [!UICONTROL Installed Products] . <!-- UPDATE FOR EACH NEW RELEASE -->
   1. Alle OSGi-bundels staan **[!UICONTROL ACTIVE]** of **[!UICONTROL FRAGMENT]** in de OSGi-console (Web gebruiken     Console: `/system/console/bundles` ).
   1. De OSGi-bundel `org.apache.jackrabbit.oak-core` is versie 1.22.14 of hoger (WebConsole gebruiken: `/system/console/bundles` ).

+++

+++7. AEM Experience Manager Forms-invoegtoepassing installeren

1. Controleer of u het servicepack [!DNL Experience Manager] hebt geïnstalleerd.
1. Download het overeenkomstige Forms toe:voegen-op pakket dat bij [ wordt vermeld de versies van AEM Forms ](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html) voor uw werkend systeem.
1. Installeer het toe:voegen-op pakket van Forms zoals die in [ wordt beschreven Installing AEM Forms toe:voegen-op pakketten ](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html).
1. Als u brieven in Experience Manager 6.5 Forms gebruikt, installeer het [ recentste pakket van de Verenigbaarheid AEMFD ](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html).

+++

## Download en installeer Service Pack op een AEM Form on OSGi environment {#download-and-install-for-osgi-service-pack}


<!-- ![OSGi Installation Steps](/help/forms/using/assets/osgiinstallation.png)
-->

+++1. Maak back-ups van uw bestaande omgeving

1. Maak een file uw [ Bewaarplaats van CRX en Schema van het Gegevensbestand ](https://experienceleague.adobe.com/docs/experience-manager-65/forms/administrator-help/aem-forms-backup-recovery/backing-aem-forms-data.html).

>[!NOTE]
>
> Als u het de dienstpak van AEM Forms voor relationele gegevensbestand installeert, is het verplicht om steun van DB_schema te nemen.

+++

+++2. De vereiste software downloaden

* [ AEM Service Pack ](https://experienceleague.adobe.com/docs/experience-manager-65/release-notes/release-notes.html)
* [ Forms toe:voegen-op pakket ](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html)

+++

+++ 3. Installeer Microsoft Visual C++ Redistributable pakketten

* De download en installeert [ versie met 64 bits van Microsoft Visual C++ Redistributable pakketten voor Visual Studio 2015, 2017, 2019, en 2022 ](https://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist?view=msvc-170#visual-studio-2015-2017-2019-and-2022) op de computer waar AEM 6.5 Forms geïnstalleerd is.

>[!NOTE]
>
>
> Zorg ervoor dat u Redistributable installeert, zelfs als een vorige versie wordt geïnstalleerd, om de beschikbaarheid van de recentste versie te waarborgen.

+++

+++4. AEM Service Pack installeren

1. Start de instantie opnieuw vóór de installatie als de updatemodus voor de instantie is geactiveerd (wanneer de instantie is bijgewerkt vanaf een eerdere versie). Adobe raadt aan de toepassing opnieuw te starten als de huidige uptime voor een instantie hoog is.
1. Maak voordat u gaat installeren een momentopname of een nieuwe back-up van de [!DNL Experience Manager] -instantie.
1. Download het de dienstpak van [ Distributie van de Software ](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html). <!-- UPDATE FOR EACH NEW RELEASE -->
1. Open Package Manager en selecteer vervolgens **[!UICONTROL Upload Package]** om het pakket te uploaden. Om meer te weten, zie [ Manager van het Pakket ](/help/sites-administering/package-manager.md).
1. Selecteer het pakket en selecteer vervolgens **[!UICONTROL Install]** .

**Automatische installatie**

Er zijn twee verschillende methodes die u kunt gebruiken om [!DNL Experience Manager] de dienstpak automatisch te installeren.<!--  UPDATE FOR EACH NEW RELEASE -->

* Plaats het pakket in de map `../crx-quickstart/install` wanneer de server online beschikbaar is. Het pakket is      automatisch geïnstalleerd.
* Gebruik [ HTTP API van de Manager van het Pakket ](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html). Gebruik `cmd=install&recursive=true` om de geneste pakketten te installeren.

  >[!NOTE]
  >
  >Experience Manager Service Pack biedt geen ondersteuning voor Bootstrap-installatie. <!-- UPDATE FOR EACH NEW RELEASE -->

  **bevestigt de installatie**

  Om de platforms te kennen die om met deze versie worden verklaard te werken, zie de [ technische vereisten ](/help/sites-deploying/technical-requirements.md).

   1. Op de pagina met productinformatie (`/system/console/productinfo`) wordt de bijgewerkte versietekenreeks weergegeven `Adobe Experience Manager (spversion)` onder [!UICONTROL Installed Products] . <!-- UPDATE FOR EACH NEW RELEASE -->

   1. Alle OSGi-bundels staan **[!UICONTROL ACTIVE]** of **[!UICONTROL FRAGMENT]** in de OSGi-console (Webconsole gebruiken: `/system/console/bundles`).

      1. De OSGi-bundel `org.apache.jackrabbit.oak-core` is versie 1.22.14 of hoger (Webconsole gebruiken: `/system/console/bundles` ).

+++

+++5. Invoegpakket voor Adobe Experience Manager Forms (AEM) installeren

1. Controleer of u het servicepack [!DNL Experience Manager] hebt geïnstalleerd.
1. Download het overeenkomstige Forms toe:voegen-op pakket dat bij [ wordt vermeld de versies van AEM Forms ](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html) voor uw werkend systeem.
1. Installeer het toe:voegen-op pakket van Forms zoals die in [ wordt beschreven Installing AEM Forms toe:voegen-op pakketten ](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html).
1. Als u brieven in Experience Manager 6.5 Forms gebruikt, installeer het [ recentste pakket van de Verenigbaarheid AEMFD ](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html).

+++

## Problemen oplossen

* Als **Dialoog op de Manager UI van het Pakket** tijdens de installatie van het de dienstpak weggaat, op foutenlogboeken wacht om zich te stabiliseren alvorens tot de plaatsing toegang te hebben. Wacht op de specifieke logboeken met betrekking tot het verwijderen van de updaterbundel alvorens wordt verzekerd dat de installaties succesvol zijn. Dit probleem doet zich doorgaans voor in de Safari-browser, maar kan soms ook in elke browser optreden.

* Controleer de monitorlogboeken (error.log) zodra de installatie voor om het even welke activiteit volledig is. Wacht een paar minuten totdat er geen activiteit in de logboeken voorkomt. Start de AEM-instantie opnieuw.

* In het geval dat u a **dienst-niet beschikbare fout** na het installeren van AEM Forms 6.5.15.0 of recenter de dienstpak krijgt, [ installeert het servletfragment en de bundel ](/help/forms/using/aem-service-pack-installation-solution.md) om de fout te bevestigen.
