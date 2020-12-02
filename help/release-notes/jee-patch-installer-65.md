---
title: AEM Forms JEE Patch Installer
description: 'null'
uuid: 76662858-afca-4ba3-883b-9b9a61874f15
content-type: reference
discoiquuid: b0283feb-c3ec-4ef0-885c-46bc83a61e26
translation-type: tm+mt
source-git-commit: c1af919d4c0fd984249e1a7009274c63b8ce9adb
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---


# AEM Forms JEE Patch Installer {#aem-forms-jee-patch-installer}

>[!NOTE]
>
>[Neem contact op met ](https://www.adobe.com/account/sign-in.supportportal.html) Ondersteuning voor meer informatie of om de pleister te verkrijgen.

## Informatie over het patchinstallatieprogramma {#about-the-patch-installer}

Het AEM 6.5 Forms JEE-patchinstallatieprogramma bevat alle opgeloste problemen voor alle componenten van AEM 6.5 Forms JEE die beschikbaar zijn tot de release van deze patch. Raadpleeg de nieuwste [Opmerkingen bij de release van Service Pack](sp-release-notes.md) voor een volledige lijst met opgeloste problemen.

## Vereisten voor de installatie van de patch {#prerequisites-to-installing-the-patch}

* AEM 6,5 Forms

## De patch installeren en configureren {#installing-and-configuring-the-patch}

1. Maak een back-up van de &lt;*AEM_forms_root*>/implementatiemap. Dit is vereist als u besluit de snelle oplossing te verwijderen.
1. Stop uw toepassingsserver.
1. Pak het archiefbestand van het patch-installatieprogramma uit op de vaste schijf.
1. In de map met de naam volgens het besturingssysteem dat u gebruikt:

   * ****
Windows: ga naar de juiste map op de installatiemedia of de installatiemap op de vaste schijf waarnaar u het installatieprogramma hebt gekopieerd en dubbelklik op het bestand aemforms65_cfp_install.exe.

      * (Windows 32-bits) `Windows\Disk1\InstData\VM`
      * (Windows 64-bits) `Windows_64Bit`\ `Disk1\InstData\VM`
   * ****
LinuxNavigate aan de aangewezen folder, en van een bevelherinnering, type 
`./aem65_cfp_install.bin`.

      * (Linux) `Linux/Disk1/InstData/NoVM`

   Hiermee wordt een installatiewizard gestart die u door de installatie begeleidt.

1. Klik in het deelvenster Inleiding op **[!UICONTROL Next]**.
1. Controleer in het scherm Install Folder (Installatiemap kiezen) of de standaardlocatie correct is voor uw bestaande installatie of klik **[!UICONTROL Browse]** om de alternatieve map te selecteren waarin AEM formulieren zijn geïnstalleerd en klik op **[!UICONTROL Next]**.
1. Lees de informatie van het Overzicht van de Reparatie van de Snelle Moeilijke situatie en klik **[!UICONTROL Next]**.
1. Lees de informatie over het Pre-Installation Summary en klik op **[!UICONTROL Install]**.
1. Wanneer de installatie is voltooid, klikt u op **[!UICONTROL Next]** om de snelle reparatie-updates toe te passen op de geïnstalleerde bestanden.

1. Schakel de optie Configuratiebeheer starten uit voordat u op Gereed klikt. Voordat u configuratiebeheer uitvoert met **ConfigurationManager.exe** of **ConfigurationManager_IPv6.exe**, navigeert u naar *&lt;AEMForms_Install_Dir>\configurationManager\bin* en werkt u **axis.jar** bij **axis-1.4.1.1 1.jar** in de volgende bestanden:

   * ConfigurationManager.lax
   * ConfigurationManager_IPv6.lax

1. Het selectievakje Configuratiebeheer starten is standaard ingeschakeld. Klik **[!UICONTROL Done]** om de Manager van de Configuratie in werking te stellen.

1. Als u Configuratiebeheer later wilt uitvoeren, schakelt u de optie Configuratiebeheer starten uit voordat u op Gereed klikt. U kunt de Manager van de Configuratie later beginnen gebruikend het aangewezen manuscript in `[AEM_forms_root]/configurationManager/bin` folder.

1. Afhankelijk van uw toepassingsserver kiest u een van de volgende documenten en volgt u de instructies in de sectie *AEM formulieren configureren en implementeren*.

   * [AEM voor JBoss installeren en implementeren](http://www.adobe.com/go/learn_aemforms_installJBoss_65)
   * [AEM voor WebSphere installeren en implementeren](http://www.adobe.com/go/learn_aemforms_installWebSphere_65)

1. (Alleen JBoss) Nadat u de patch hebt geïnstalleerd en de server hebt geconfigureerd, verwijdert u tmp- en werkmappen van de JBoss-toepassingsserver.

## Configuratie {#post-deployment-configurations} na implementatie

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
