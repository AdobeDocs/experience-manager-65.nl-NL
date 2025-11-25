---
title: AEM Forms JEE Patch Installer
description: Leer hoe u AEM Forms JEE Patch Installer kunt gebruiken om problemen in AEM 6.5 Forms-componenten op te lossen.
content-type: reference
exl-id: 6b17472b-9226-4319-b305-4dba862d21af
hide: true
hidefromtoc: true
solution: Experience Manager
feature: Release Information
role: User,Admin,Developer
source-git-commit: c77849740fab51377ce60aff5f611e0408dca728
workflow-type: tm+mt
source-wordcount: '552'
ht-degree: 0%

---

# AEM Forms JEE Patch Installer {#aem-forms-jee-patch-installer}

>[!NOTE]
>
>[&#x200B; Steun van het Contact &#x200B;](https://experienceleague.adobe.com/nl?support-solution=General&support-tab=home#support) voor meer informatie of om het flard te verkrijgen.

## Het installatieprogramma van de patch {#about-the-patch-installer}

Het AEM 6.5 Forms JEE-patchinstallatieprogramma bevat alle opgeloste problemen voor alle componenten van AEM 6.5 Forms JEE die beschikbaar zijn tot de release van deze patch. Zie de recentste [&#x200B; Nota&#39;s van de Versie van het Pak van de Dienst &#x200B;](release-notes.md) voor een volledige lijst van vaste kwesties.

## Vereisten voor de installatie van de patch {#prerequisites-to-installing-the-patch}

* AEM 6.5 Forms

## De patch installeren en configureren {#installing-and-configuring-the-patch}

1. Neem een steun van &lt;*AEM_forms_root*>/stel omslag op. Dit is vereist als u besluit de snelle oplossing te verwijderen.
1. Stop uw toepassingsserver.
1. Pak het archiefbestand van het patch-installatieprogramma uit op de vaste schijf.
1. In de map met de naam volgens het besturingssysteem dat u gebruikt:

   * **Vensters**
Navigeer naar de juiste map op de installatiemedia of de installatiemap op de vaste schijf waarnaar u het installatieprogramma hebt gekopieerd en dubbelklik op het bestand aemforms65_cfp_install.exe.

      * (Windows 32-bits) `Windows\Disk1\InstData\VM`
      * (Windows 64-bits) `Windows_64Bit`\ `Disk1\InstData\VM`

   * **Linux®**
Navigeer naar de juiste map en typ `./aem65_cfp_install.bin` vanaf een opdrachtprompt.

      * (Linux®) `Linux/Disk1/InstData/NoVM`

   Hiermee wordt een installatiewizard gestart die u door de installatie begeleidt.

1. Klik in het deelvenster Inleiding op **[!UICONTROL Next]** .
1. Op **kies installeer het scherm van de Omslag**, verifieer dat de getoonde standaardplaats voor uw bestaande installatie correct is, of klik **[!UICONTROL Browse]** om de afwisselende omslag te selecteren waar de vormen van AEM worden geïnstalleerd, en **[!UICONTROL Next]** te klikken.
1. Lees de informatie over het overzicht van reparaties in Snel repareren en klik op **[!UICONTROL Next]** .
1. Lees de informatie over het pre-installatieoverzicht en klik op **[!UICONTROL Install]** .
1. Wanneer de installatie is voltooid, klikt u op **[!UICONTROL Next]** om de snelle reparatie-updates toe te passen op de geïnstalleerde bestanden.

1. **[slechts voor Vensters ]:** doe het volgende:
   * Of schrap de **optie van de Manager van de Configuratie van het Begin** alvorens u **[!UICONTROL Done]** klikt. Voer **Manager van de Configuratie** in werking door het {**dossier 3} te gebruiken 2&rbrace; ConfigurationManager.bat in**.`[aem-forms root]\configurationManager\bin`

   * Of schrap de **optie van de Manager van de Configuratie van het Begin** alvorens u **[!UICONTROL Done]** klikt. Alvorens **Manager van de Configuratie in werking te stellen** gebruikend **ConfigurationManager.exe** of **ConfigurationManager_IPv6.exe**, navigeer aan *`<AEMForms_Install_Dir>\configurationManager\bin`* folder en vervang **ConfigurationManager.lax** en **ConfigurationManager_IPV6.lax** met recentste [&#x200B; ConfigurationManager.lax &#x200B;](/help/assets/ConfigurationManager.lax) en [&#x200B; ConfigurationManager_IPV6.lax &#x200B;](/help/assets/ConfigurationManager_IPv6.lax) dossiers, Onderzoek, en vervang **as- 1.4.1.1 .jar** met **as- 1.4.1.2 .jar** in deze twee dossiers.

   >[!NOTE]
   >
   >Het gebruiken van **ConfigurationManager.bat** dossier helpt u vermijden het bijwerken naam van .lax dossiers manueel.
   >

1. **[voor op unix-Gebaseerd slechts ]:**

   * De **controledoos van de Manager van de Configuratie van het 0&rbrace; Begin wordt geselecteerd door gebrek.** Klik **[!UICONTROL Done]** om de Manager van de Configuratie in werking te stellen onmiddellijk of **de Manager van de Configuratie** later in werking te stellen, schrap de **optie van de Manager van de Configuratie van het Begin** alvorens u **[!UICONTROL Done]** klikt. U kunt **Manager van de Configuratie** later beginnen gebruikend het aangewezen manuscript in de `[AEM_forms_root]/configurationManager/bin` folder.

1. Afhankelijk van uw toepassingsserver, kies één van de volgende documenten en volg de instructies in *het Vormen en het Opstellen van de vormen van AEM* sectie.

   * [&#x200B; het Installeren van en het Opstellen van de vormen van AEM voor JBoss® &#x200B;](https://www.adobe.com/go/learn_aemforms_installJBoss_65)
   * [&#x200B; het Installeren van en het Opstellen van de vormen van AEM voor WebSphere® &#x200B;](https://www.adobe.com/go/learn_aemforms_installWebSphere_65)

1. (Alleen JBoss®) Nadat u de patch hebt geïnstalleerd en de server hebt geconfigureerd, verwijdert u tmp- en werkmappen van de JBoss®-toepassingsserver.

## Configuratie na implementatie {#post-deployment-configurations}

### SAML-configuraties {#saml-configurations}

Als u de authentificatie van SAML gevormd hebt en problemen met grote meta-gegevens IDP onder ogen ziet, doe het volgende na het installeren van het flard:

1. Stel de volgende systeemeigenschap in op uw toepassingsserver:\
   `um.saml.enable.large.xml=true`
1. Start de server opnieuw.
1. Verwijder bestaande SAML-auteproviders en voeg deze opnieuw toe voor bestaande domeinen zoals beschreven in SAML-instellingen.

>[!NOTE]
>
> U wordt aangeraden de SDK opnieuw op te starten met de opdracht &#39;Ctrl + C&#39;. Het opnieuw opstarten van de AEM SDK met behulp van alternatieve methoden, bijvoorbeeld het stoppen van Java-processen, kan leiden tot inconsistenties in de AEM-ontwikkelomgeving.

## Betrokken modules {#impacted-modules}

* Document Services
* Documentbeveiliging
* Foundation JEE

[&#x200B; Steun van het Contact &#x200B;](https://experienceleague.adobe.com/nl?support-solution=General&support-tab=home#support)
