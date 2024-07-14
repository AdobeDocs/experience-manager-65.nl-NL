---
title: AEM Forms JEE Patch Installer
description: Leer hoe u AEM Forms JEE Patch Installer kunt gebruiken om problemen in AEM 6.5 Forms-componenten op te lossen.
content-type: reference
exl-id: 6b17472b-9226-4319-b305-4dba862d21af
hide: true
hidefromtoc: true
solution: Experience Manager
feature: Release Information
role: User,Admin,Architect,Developer
source-git-commit: 10268f617b8a1bb22f1f131cfd88236e7d5beb47
workflow-type: tm+mt
source-wordcount: '552'
ht-degree: 0%

---

# AEM Forms JEE Patch Installer {#aem-forms-jee-patch-installer}

>[!NOTE]
>
>[ Steun van het Contact ](https://experienceleague.adobe.com/?support-solution=General&amp;support-tab=home#support) voor meer informatie of om het flard te verkrijgen.

## Het installatieprogramma van de patch {#about-the-patch-installer}

Het AEM 6.5 Forms JEE-patchinstallatieprogramma bevat alle opgeloste problemen voor alle componenten van AEM 6.5 Forms JEE die beschikbaar zijn tot de release van deze patch. Zie de recentste [ Nota&#39;s van de Versie van het Pak van de Dienst ](release-notes.md) voor een volledige lijst van vaste kwesties.

## Vereisten voor de installatie van de patch {#prerequisites-to-installing-the-patch}

* AEM 6,5 Forms

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
1. Op **kies installeer het scherm van de Omslag**, verifieer dat de getoonde standaardplaats voor uw bestaande installatie correct is, of klik **[!UICONTROL Browse]** om de afwisselende omslag te selecteren waar de AEM vormen geïnstalleerd zijn, en **[!UICONTROL Next]** te klikken.
1. Lees de informatie over het overzicht van reparaties in Snel repareren en klik op **[!UICONTROL Next]** .
1. Lees de informatie over het pre-installatieoverzicht en klik op **[!UICONTROL Install]** .
1. Wanneer de installatie is voltooid, klikt u op **[!UICONTROL Next]** om de snelle reparatie-updates toe te passen op de geïnstalleerde bestanden.

1. **[slechts voor Vensters ]:** doe het volgende:
   * Of schrap de **optie van de Manager van de Configuratie van het Begin** alvorens u **[!UICONTROL Done]** klikt. Voer **Manager van de Configuratie** in werking door het {**dossier 3} te gebruiken 2} ConfigurationManager.bat in `[aem-forms root]\configurationManager\bin`.**

   * Of schrap de **optie van de Manager van de Configuratie van het Begin** alvorens u **[!UICONTROL Done]** klikt. Alvorens **Manager van de Configuratie in werking te stellen** gebruikend **ConfigurationManager.exe** of **ConfigurationManager_IPv6.exe**, navigeer aan *`<AEMForms_Install_Dir>\configurationManager\bin`* folder en vervang **ConfigurationManager.lax** en **ConfigurationManager_IPV6.lax** met recentste [ ConfigurationManager.lax ](/help/assets/ConfigurationManager.lax) en [ ConfigurationManager_IPV6.lax ](/help/assets/ConfigurationManager_IPv6.lax) dossiers, Onderzoek, en vervang **as-1.4.1.1.jar** met **as-1.4.1.2.jar** in deze twee dossiers.

   >[!NOTE]
   >
   >Het gebruiken van **ConfigurationManager.bat** dossier helpt u vermijden het bijwerken naam van .lax dossiers manueel.
   >

1. **[voor op unix-Gebaseerd slechts ]:**

   * De **controledoos van de Manager van de Configuratie van het 0} Begin wordt geselecteerd door gebrek.** Klik **[!UICONTROL Done]** om de Manager van de Configuratie in werking te stellen onmiddellijk of **de Manager van de Configuratie** later in werking te stellen, schrap de **optie van de Manager van de Configuratie van het Begin** alvorens u **[!UICONTROL Done]** klikt. U kunt **Manager van de Configuratie** later beginnen gebruikend het aangewezen manuscript in de `[AEM_forms_root]/configurationManager/bin` folder.

1. Afhankelijk van uw toepassingsserver, kies één van de volgende documenten en volg de instructies in *het Vormen en het Opstellen van AEM vormen* sectie.

   * [ het Installeren van en het Opstellen van AEM vormen voor JBoss® ](https://www.adobe.com/go/learn_aemforms_installJBoss_65)
   * [ het Installeren van en het Opstellen van AEM vormen voor WebSphere® ](https://www.adobe.com/go/learn_aemforms_installWebSphere_65)

1. (Alleen JBoss®) Nadat u de patch hebt geïnstalleerd en de server hebt geconfigureerd, verwijdert u tmp- en werkmappen van de JBoss®-toepassingsserver.

## Post-implementatieconfiguraties {#post-deployment-configurations}

### SAML-configuraties {#saml-configurations}

Als u de authentificatie van SAML gevormd hebt en problemen met grote meta-gegevens IDP onder ogen ziet, doe het volgende na het installeren van het flard:

1. Stel de volgende systeemeigenschap in op uw toepassingsserver:\
   `um.saml.enable.large.xml=true`
1. Start de server opnieuw.
1. Verwijder bestaande SAML-auteproviders en voeg deze opnieuw toe voor bestaande domeinen zoals beschreven in SAML-instellingen.

>[!NOTE]
>
> Het wordt aanbevolen de SDK opnieuw te starten met de opdracht &#39;Ctrl + C&#39;. Het opnieuw opstarten van de AEM SDK met behulp van alternatieve methoden, bijvoorbeeld het stoppen van Java-processen, kan leiden tot inconsistenties in de AEM ontwikkelomgeving.

## Betrokken modules {#impacted-modules}

* Document Services
* Documentbeveiliging
* Foundation JEE

[ Steun van het Contact ](https://experienceleague.adobe.com/?support-solution=General&amp;support-tab=home#support)
