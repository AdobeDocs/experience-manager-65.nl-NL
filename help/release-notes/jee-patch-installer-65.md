---
title: AEM Forms JEE Patch Installer
description: AEM Forms JEE Patch Installer
uuid: 76662858-afca-4ba3-883b-9b9a61874f15
content-type: reference
discoiquuid: b0283feb-c3ec-4ef0-885c-46bc83a61e26
exl-id: 6b17472b-9226-4319-b305-4dba862d21af
source-git-commit: 3af8a2425596ff6c15fb49fed66e9fbd0e9d391e
workflow-type: tm+mt
source-wordcount: '487'
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
1. Controleer in het scherm Installatiemap kiezen of de standaardlocatie die wordt weergegeven correct is voor uw bestaande installatie of klik op **[!UICONTROL Browse]** om de alternatieve map te selecteren waarin AEM formulieren zijn geïnstalleerd en klik op **[!UICONTROL Next]**.
1. Lees de informatie over het overzicht van reparaties in Snel repareren en klik op **[!UICONTROL Next]**.
1. Lees de informatie van het Pre-installatieoverzicht en klik **[!UICONTROL Install]**.
1. Wanneer de installatie is voltooid, klikt u op **[!UICONTROL Next]** om de snelle reparatie updates op uw geïnstalleerde dossiers toe te passen.

1. Schakel de optie Configuratiebeheer starten uit voordat u op Gereed klikt. Voordat u configuratiebeheer uitvoert **ConfigurationManager.exe** of **ConfigurationManager_IPv6.exe**, navigeer naar *&lt;aemforms_install_dir>\configurationManager\bin* map en update `ConfigurationManager.lax` en `ConfigurationManager_IPv6.lax` bestanden waarvan de naam als volgt wordt gewijzigd:

   * `axis.jar` tot `axis-1.4.1.1.jar`
   * `serializer-2.7.1.jar` tot `serializer-2.7.2.jar`
   * `xalan-2.7.1.jar` tot `xalan-2.7.2.jar`
   * `xercesImpl-2.9.1.jar` tot `xercesImpl-2.12.0.jar`
   * `xml-apis-2.7.1.jar` tot `xml-apis-2.7.2.jar`

1. Het selectievakje Configuratiebeheer starten is standaard ingeschakeld. Klikken **[!UICONTROL Done]** om de Manager van de Configuratie in werking te stellen.

1. Als u Configuratiebeheer later wilt uitvoeren, schakelt u de optie Configuratiebeheer starten uit voordat u op Gereed klikt. U kunt de Manager van de Configuratie later beginnen gebruikend het aangewezen manuscript in `[AEM_forms_root]/configurationManager/bin` directory.

1. Afhankelijk van uw toepassingsserver kiest u een van de volgende documenten en volgt u de instructies in het dialoogvenster *Formulieren configureren en implementeren AEM* sectie.

   * [AEM voor JBoss installeren en implementeren](http://www.adobe.com/go/learn_aemforms_installJBoss_65)
   * [AEM voor WebSphere installeren en implementeren](http://www.adobe.com/go/learn_aemforms_installWebSphere_65)

1. (Alleen JBoss) Nadat u de patch hebt geïnstalleerd en de server hebt geconfigureerd, verwijdert u tmp- en werkmappen van de JBoss-toepassingsserver.

>**Opmerking:** Voordat u start **Configuratiebeheer**, downloaden en vervangen [ConfigurationManager.lax](/help/assets/ConfigurationManager.lax) bestand.
>
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
