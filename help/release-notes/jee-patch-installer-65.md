---
title: AEM Forms JEE Patch Installer
description: AEM Forms JEE Patch Installer
uuid: 76662858-afca-4ba3-883b-9b9a61874f15
content-type: reference
discoiquuid: b0283feb-c3ec-4ef0-885c-46bc83a61e26
exl-id: 6b17472b-9226-4319-b305-4dba862d21af
source-git-commit: 6c6ddaba0e42df4b4701670e8abfdabe5205879c
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 0%

---

# AEM Forms JEE Patch Installer {#aem-forms-jee-patch-installer}

>[!NOTE]
>
>[Contact opnemen met ondersteuning](https://www.adobe.com/account/sign-in.supportportal.html) voor meer informatie of om de pleister te verkrijgen.

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
   * **Linux**
Navigeer aan de aangewezen folder, en van een bevelherinnering, type 
`./aem65_cfp_install.bin`.

      * (Linux) `Linux/Disk1/InstData/NoVM`

   Hiermee wordt een installatiewizard gestart die u door de installatie begeleidt.

1. Klik in het deelvenster Inleiding op **[!UICONTROL Next]**.
1. Op de **Installatiemap kiezen** , controleert u of de weergegeven standaardlocatie correct is voor uw bestaande installatie of klikt u op **[!UICONTROL Browse]** om de alternatieve map te selecteren waarin AEM formulieren zijn geïnstalleerd en klik op **[!UICONTROL Next]**.
1. Lees de informatie over het overzicht van reparaties in Snel repareren en klik op **[!UICONTROL Next]**.
1. Lees de informatie van het Pre-installatieoverzicht en klik **[!UICONTROL Install]**.
1. Wanneer de installatie is voltooid, klikt u op **[!UICONTROL Next]** om de snelle reparatie updates op uw geïnstalleerde dossiers toe te passen.

1. **[Alleen voor Windows]:** Voer een van de volgende stappen uit:
   * Schakel de optie **Configuratiebeheer starten** voordat u klikt op **[!UICONTROL Done]**. Uitvoeren **Configuratiebeheer** door **ConfigurationManager.bat** bestand in `[aem-forms root]\configurationManager\bin`.

   * Schakel de optie **Configuratiebeheer starten** voordat u klikt op **[!UICONTROL Done]**. Voor uitvoering **Configuratiebeheer** gebruiken **ConfigurationManager.exe** of **ConfigurationManager_IPv6.exe**, navigeer naar *`<AEMForms_Install_Dir>\configurationManager\bin`* directory en replace [ConfigurationManager.lax](/help/assets/ConfigurationManager.lax) en [ConfigurationManager_IPV6.lax](/help/assets/ConfigurationManager_IPv6.lax) bestanden.
   >[!NOTE]
   >Gebruiken **ConfigurationManager.bat** kunt u voorkomen dat de naam van de .lax-bestanden handmatig wordt bijgewerkt.

1. **[Alleen voor Unix]:** Voer een van de volgende stappen uit:

   * De **Configuratiebeheer starten** selectievakje is standaard ingeschakeld. Klikken **[!UICONTROL Done]** om de Manager van de Configuratie onmiddellijk in werking te stellen.

   * Uitvoeren **Configuratiebeheer** later, schrap **Configuratiebeheer starten** voordat u klikt op **[!UICONTROL Done]**. U kunt beginnen **Configuratiebeheer** later het gebruiken van het aangewezen manuscript in `[AEM_forms_root]/configurationManager/bin` directory.

1. Afhankelijk van uw toepassingsserver kiest u een van de volgende documenten en volgt u de instructies in het dialoogvenster *Formulieren configureren en implementeren AEM* sectie.

   * [AEM voor JBoss installeren en implementeren](http://www.adobe.com/go/learn_aemforms_installJBoss_65)
   * [AEM voor WebSphere installeren en implementeren](http://www.adobe.com/go/learn_aemforms_installWebSphere_65)

1. (Alleen JBoss) Nadat u de patch hebt geïnstalleerd en de server hebt geconfigureerd, verwijdert u tmp- en werkmappen van de JBoss-toepassingsserver.

## Configuratie na implementatie {#post-deployment-configurations}

### SAML-configuraties {#saml-configurations}

Als u de authentificatie van SAML en het onder ogen zien van kwesties met grote meta-gegevens IDP had gevormd, doe het volgende na het installeren van het flard:

1. Stel de volgende systeemeigenschap in op uw toepassingsserver:\
   `um.saml.enable.large.xml=true`
1. Start de server opnieuw.
1. Verwijder bestaande SAML-auteproviders en voeg deze opnieuw toe voor bestaande domeinen zoals beschreven in SAML-instellingen.

## Betrokken modules {#impacted-modules}

* Document Services
* Documentbeveiliging
* Foundation JEE

[Contact opnemen met ondersteuning](https://www.adobe.com/account/sign-in.supportportal.html)
