---
title: AEM Forms JEE Patch Installer
description: Leer hoe u AEM Forms JEE Patch Installer kunt gebruiken om problemen in AEM 6.5 Forms-componenten op te lossen.
content-type: reference
exl-id: 6b17472b-9226-4319-b305-4dba862d21af
hide: true
hidefromtoc: true
source-git-commit: 947f45e043c2ce1b683212f70157d1e9a08e1941
workflow-type: tm+mt
source-wordcount: '552'
ht-degree: 0%

---

# AEM Forms JEE Patch Installer {#aem-forms-jee-patch-installer}

>[!NOTE]
>
>[Contact opnemen met ondersteuning](https://experienceleague.adobe.com/?support-solution=General&amp;support-tab=home#support) voor meer informatie of om de pleister te verkrijgen.

## Het installatieprogramma van de patch {#about-the-patch-installer}

Het AEM 6.5 Forms JEE-patchinstallatieprogramma bevat alle opgeloste problemen voor alle componenten van AEM 6.5 Forms JEE die beschikbaar zijn tot de release van deze patch. Zie de nieuwste  [Release-aantekeningen bij Service Pack](release-notes.md) voor een volledige lijst van opgeloste problemen.

## Vereisten voor de installatie van de patch {#prerequisites-to-installing-the-patch}

* AEM 6,5 Forms

## De patch installeren en configureren {#installing-and-configuring-the-patch}

1. Maak een back-up van de &lt;*AEM_forms_root*>/implementatiemap. Dit is vereist als u besluit de snelle oplossing te verwijderen.
1. Stop uw toepassingsserver.
1. Pak het archiefbestand van het patch-installatieprogramma uit op de vaste schijf.
1. In de map met de naam volgens het besturingssysteem dat u gebruikt:

   * **Windows**
Navigeer naar de juiste map op de installatiemedia of de installatiemap op de vaste schijf waarnaar u het installatieprogramma hebt gekopieerd en dubbelklik op het bestand aemforms65_cfp_install.exe.

      * (Windows 32-bits) `Windows\Disk1\InstData\VM`
      * (Windows 64-bits) `Windows_64Bit`\ `Disk1\InstData\VM`

   * **Linux®**
Navigeer aan de aangewezen folder, en van een bevelherinnering, type `./aem65_cfp_install.bin`.

      * (Linux®) `Linux/Disk1/InstData/NoVM`

   Hiermee wordt een installatiewizard gestart die u door de installatie begeleidt.

1. Klik in het deelvenster Inleiding op **[!UICONTROL Next]**.
1. Op de **Installatiemap kiezen** , controleert u of de weergegeven standaardlocatie correct is voor uw bestaande installatie of klikt u op **[!UICONTROL Browse]** om de alternatieve map te selecteren waarin AEM formulieren zijn geïnstalleerd en klik op **[!UICONTROL Next]**.
1. Lees de informatie over het overzicht van reparaties in Snel repareren en klik op **[!UICONTROL Next]**.
1. Lees de informatie van het Pre-installatieoverzicht en klik **[!UICONTROL Install]**.
1. Wanneer de installatie is voltooid, klikt u op **[!UICONTROL Next]** om de snelle reparatie updates op uw geïnstalleerde dossiers toe te passen.

1. **[Alleen voor Windows]:** Ga als volgt te werk:
   * Schakel de optie **Configuratiebeheer starten** voordat u klikt op **[!UICONTROL Done]**. Uitvoeren **Configuratiebeheer** door de **ConfigurationManager.bat** bestand in `[aem-forms root]\configurationManager\bin`.

   * U kunt de selectie van de **Configuratiebeheer starten** voordat u klikt op **[!UICONTROL Done]**. Voor uitvoering **Configuratiebeheer** gebruiken **ConfigurationManager.exe** of **ConfigurationManager_IPv6.exe**, navigeer naar *`<AEMForms_Install_Dir>\configurationManager\bin`* en vervangt u de **ConfigurationManager.lax** en **ConfigurationManager_IPV6.lax** uiterlijk [ConfigurationManager.lax](/help/assets/ConfigurationManager.lax) en [ConfigurationManager_IPV6.lax](/help/assets/ConfigurationManager_IPv6.lax) bestanden, zoeken en vervangen **as-1.4.1.1.jar** with **as-1.4.1.2.jar** in deze twee bestanden.

   >[!NOTE]
   >
   >Gebruiken **ConfigurationManager.bat** kunt u voorkomen dat de naam van de .lax-bestanden handmatig wordt bijgewerkt.
   >

1. **[Alleen voor Unix]:**

   * De **Configuratiebeheer starten** selectievakje is standaard ingeschakeld. Klikken **[!UICONTROL Done]** om de Manager van de Configuratie onmiddellijk in werking te stellen of te lopen **Configuratiebeheer** later, schrap **Configuratiebeheer starten** voordat u klikt op **[!UICONTROL Done]**. U kunt beginnen **Configuratiebeheer** later het gebruiken van het aangewezen manuscript in `[AEM_forms_root]/configurationManager/bin` directory.

1. Kies afhankelijk van uw toepassingsserver een van de volgende documenten en volg de instructies in het dialoogvenster *Formulieren configureren en implementeren AEM* sectie.

   * [AEM voor JBoss® installeren en implementeren](https://www.adobe.com/go/learn_aemforms_installJBoss_65)
   * [AEM voor WebSphere® installeren en implementeren](https://www.adobe.com/go/learn_aemforms_installWebSphere_65)

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
> Het wordt aanbevolen de SDK opnieuw te starten met de opdracht &#39;Ctrl + C&#39;. Het opnieuw opstarten van de AEM SDK met behulp van alternatieve methoden, bijvoorbeeld het stoppen van Java-processen, kan leiden tot inconsistenties in de AEM ontwikkelomgeving.

## Betrokken modules {#impacted-modules}

* Document Services
* Documentbeveiliging
* Foundation JEE

[Contact opnemen met ondersteuning](https://experienceleague.adobe.com/?support-solution=General&amp;support-tab=home#support)
