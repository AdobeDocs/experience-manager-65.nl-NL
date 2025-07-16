---
title: Hotfixes voor AEM Forms
description: Hier vindt u informatie over het downloaden en installeren van een hotfix voor AEM Forms.
exl-id: 37287332-3c8d-4ddc-a77e-3c5ee332898b
solution: Experience Manager
feature: Release Information
role: User,Admin,Architect,Developer
source-git-commit: 80482da847b86c91963dbb0d37375e370a503588
workflow-type: tm+mt
source-wordcount: '1163'
ht-degree: 0%

---

# Adobe Experience Manager Forms Hotfixes{#aem-form-hotfix}

Dit artikel bevat een overzicht van de kritieke oplossingen die zijn geïmplementeerd om bekende problemen aan te pakken, de stabiliteit van het systeem te verbeteren en de algehele prestaties van AEM Forms te verbeteren.

>[!NOTE]
>
> De hotfixes zijn cumulatief ontworpen en omvatten alle voorafgaande fixes. Wanneer u de nieuwste hotfix toepast op een release, wordt niet alleen het meest recente probleem opgelost, maar worden ook alle eerdere correcties en verbeteringen aangebracht.

## Hotfixes voor adaptieve Forms {#hotfix-for-adaptive-forms}

<table>
  <tbody>
  <tr>
    <td><strong>Datum</strong></td>
    <td><strong>Hotfix-downloadkoppeling (AEM-koppeling voor softwaredistributie)</strong></td>
    <td><strong>Opgeloste problemen</strong></td>
  </tr>
  <tr>
    <td>SP23 Hotfix geüpload naar SD-</td>
    <td>
    <ul>
    <li><strong>Reliëf:</strong></li>
    <li>Vensters - <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-0-hotfix-2/jboss/adobe-aem-forms-jee-hotfix-6.5.23.0-win-jboss.zip"> Hotfix voor AEM Service Pack 6.5.23.0 op Vensters voor server JBoss </a></li>
    <li>Linux - <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-0-hotfix-2/jboss/adobe-aem-forms-jee-hotfix-6.5.23.0-linux-jboss.tar.gz"> Hotfix voor AEM Service Pack 6.5.23.0 op Linux voor JBoss server JEE </a></li>
    <li><strong>Weblogic:</strong></li>
    <li>Vensters - <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-0-hotfix-2/weblogic/adobe-aem-forms-jee-hotfix-6.5.23.0-win-weblogic.zip"> Hotfix voor AEM Service Pack 6.5.23.0 op Vensters voor de server van de Weblogic JEE </a></li>
    <li>Linux - <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-0-hotfix-2/weblogic/adobe-aem-forms-jee-hotfix-6.5.23.0-linux-weblogic.tar.gz"> Hotfix voor AEM Service Pack 6.5.23.0 op Linux voor de server van de Weblogic JEE </a></li>
    <li><strong>Websfeer:</strong></li>
    <li>Vensters: <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-0-hotfix-2/websphere/adobe-aem-forms-jee-hotfix-6.5.23.0-win-websphere.zip"> Hotfix voor AEM Service Pack 6.5.23.0 op Vensters voor de server van JEE Websphere </a></li>
    <li>Linux: <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-0-hotfix-2/websphere/adobe-aem-forms-jee-hotfix-6.5.23.0-linux-websphere.tar.gz"> Hotfix voor AEM Service Pack 6.5.23.0 op Linux voor de server van Websphere JEE </a></li>
    </ul>
    </td>
    <td>
    <ul>
    <li>SP23 Hotfix voor AEM Forms op JEE</li>
    </ul>
    </td>    
  </tr>
  <tr>
    <td>26 maart 2025 </br> </br> Volg de instructies <a href="/help/forms/using/mitigating-spring-framework-vulnerabilities-for-aem-forms-on-jee.md"> De kwetsbaarheden van het Voorjaarsframework voor AEM Forms op JEE verminderen </a> om deze correctie te installeren.</td>
     <td>
     <ul>
     <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-0-hotfix-vuln-30727/jboss/adobe-aem-forms-jee-hotfix-6.5.22.0-win-jboss.tar.gz"> Hotfix voor AEM Service Pack 6.5.22.0 op Vensters voor server JBoss JEE </a> </li>
      <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-0-hotfix-vuln-30727/jboss/adobe-aem-forms-jee-hotfix-6.5.22.0-linux-jboss.tar.gz"> Hotfix voor AEM Service Pack 6.5.22.0 op Linux voor JBoss JEE server </a> </li>
       <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-0-hotfix-vuln-30727/weblogic/adobe-aem-forms-jee-hotfix-6.5.22.0-win-weblogic.tar.gz"> Hotfix voor AEM Service Pack 6.5.22.0 op Windows for Weblogic JEE-server </a> </li>
        <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-0-hotfix-vuln-30727/weblogic/adobe-aem-forms-jee-hotfix-6.5.22.0-linux-weblogic.tar.gz"> Hotfix voor AEM Service Pack 6.5.22.0 op Linux voor Weblogic JEE server </a> </li>
        <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-0-hotfix-vuln-30727/websphere/adobe-aem-forms-jee-hotfix-6.5.22.0-win-websphere.tar.gz"> Hotfix voor AEM Service Pack 6.5.22.0 op Vensters voor server Websphere JEE </a> </li>
        <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-0-hotfix-vuln-30727/websphere/adobe-aem-forms-jee-hotfix-6.5.22.0-linux-websphere.tar.gz"> Hotfix voor AEM Service Pack 6.5.22.0 op Linux voor server Websphere JEE </a> </li>
     </ul>
     </td>
    <td>
    <ul>
    <li>Risico's van het voorjaarskader voor AEM Forms op JEE verminderen</li>
    </ul>
    </td>    
  </tr>
  <tr>
    <td>10 juli 2024</td>
     <td>
     <ul>
     <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/fd/aemforms-6-5-0-0089/jboss/win/adobe-aem-forms-jee-service-pack-6.5.21.0-hotfix-windows-jboss.zip.zip"> Hotfix voor AEM Service Pack 6.5.21.0 op Vensters voor server JBoss JEE </a> </li>
      <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/fd/aemforms-6-5-0-0089/jboss/linux/adobe-aem-forms-jee-service-pack-6.5.21.0-hotfix-linux-jboss.tar.gz"> Hotfix voor AEM Service Pack 6.5.21.0 op Linux voor JBoss JEE server </a> </li>
       <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/fd/aemforms-6-5-0-0089/websphere/win/adobe-aem-forms-jee-service-pack-6.5.21.0-hotfix-windows-websphere.zip.zip"> Hotfix voor AEM Service Pack 6.5.21.0 op Vensters voor de server van de JEE van Webampère </a> </li>
        <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/fd/aemforms-6-5-0-0089/websphere/linux/adobe-aem-forms-jee-service-pack-6.5.21.0-hotfix-linux-websphere.tar.gz"> Hotfix voor AEM Service Pack 6.5.21.0 op Linux voor de server van JEE van de Ruimte van de Websfeer </a> </li>
        <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/fd/aemforms-6-5-0-0089/weblogic/win/adobe-aem-forms-jee-service-pack-6.5.21.0-hotfix-windows-weblogic.zip.zip"> Hotfix voor AEM Service Pack 6.5.21.0 op Windows for Weblogic JEE-server </a> </li>
        <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/fd/aemforms-6-5-0-0089/weblogic/linux/adobe-aem-forms-jee-service-pack-6.5.21.0-hotfix-linux-weblogic.tar.gz"> Hotfix voor AEM Service Pack 6.5.21.0 op Linux voor Weblogic JEE server </a> </li>
     </ul>
     </td>
    <td>
    <ul><li>Wanneer een gebruiker AEM Forms Service Pack 20 (6.5.20.0) bijwerkt op de JEE-server en PDF's genereert met behulp van uitvoerservices, worden de PDF's weergegeven met toegankelijkheidsproblemen. (LC-3922112)</li><li>Gecodeerde PDF's die zijn gegenereerd met behulp van een uitvoerservice op AEM Forms JEE tonen "Onjuiste structuurwaarschuwing". (LC-392/2038)</li><li>Wanneer een formulier wordt verzonden op AEM Forms JEE, worden de instanties van een herhalend XML-element verwijderd uit de gegevens. (LC-392/2017)</li><li>Wanneer een gebruiker in een Linux-omgeving een adaptief formulier (in JEE) rendert in HTML, wordt het formulier niet correct weergegeven. (LC-3921957)</li><li>Wanneer een gebruiker een XTG-bestand naar PostScript-indeling converteert met de Output Service op AEM Forms JEE, treedt de fout op: AEM_OUT_001_003: Onverwachte uitzondering: PAExecute failure: XFA_RENDER_FAILURE. (LC-3921720)</li><li>Na de upgrade naar AEM Forms Service Pack 18 (6.5.18.0) op de JEE-server kan een gebruiker die een formulier verzendt, HTML5 of PDF forms en XMLFM niet genereren. (LC-3921718)
    </ul>
    </td>    
  </tr>
  <tr>
    <td>21 juni 2024</td>
     <td>
     <ul>
     <li><a href="https://nam04.safelinks.protection.outlook.com/?url=https%3A%2F%2Fexperience.adobe.com%2F%23%2Fdownloads%2Fcontent%2Fsoftware-distribution%2Fen%2Faem.html%3Fpackage%3D%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq650%2Fhotfix%2FPaperCaptureSvc.zip&amp;data=05%7C02%7Cruchitas%40adobe.com%7Cf50f80aab6994875271a08dc91f2f137%7Cfa7b1b5a7b34438794aed2c178decee1%7C0%7C0%7C638545719814675925%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C0%7C%7C%7C&amp;sdata=9pTrMfiMD%2B5kQezxsZwTdOmaaktxURR99d7f6wHr%2FWQ%3D&amp;reserved=0"> Hotfix voor AEM Service Pack 6.5.21.0 of AEM Forms Service Pack 6.5.22.0 op JBoss JEE server </a> </li>
      <li><a href="https://nam04.safelinks.protection.outlook.com/?url=https%3A%2F%2Fexperience.adobe.com%2F%23%2Fdownloads%2Fcontent%2Fsoftware-distribution%2Fen%2Faem.html%3Fpackage%3D%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq650%2Fhotfix%2FPaperCaptureSvc.zip&amp;data=05%7C02%7Cruchitas%40adobe.com%7Cf50f80aab6994875271a08dc91f2f137%7Cfa7b1b5a7b34438794aed2c178decee1%7C0%7C0%7C638545719814675925%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C0%7C%7C%7C&amp;sdata=9pTrMfiMD%2B5kQezxsZwTdOmaaktxURR99d7f6wHr%2FWQ%3D&amp;reserved=0"> Hotfix voor AEM Service Pack 6.5.21.0 of AEM Forms Service Pack 6.5.22.0 op Weblogic JEE-server </a> </li>
       <li><a href="https://nam04.safelinks.protection.outlook.com/?url=https%3A%2F%2Fexperience.adobe.com%2F%23%2Fdownloads%2Fcontent%2Fsoftware-distribution%2Fen%2Faem.html%3Fpackage%3D%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq650%2Fhotfix%2FPaperCaptureSvc.zip&amp;data=05%7C02%7Cruchitas%40adobe.com%7Cf50f80aab6994875271a08dc91f2f137%7Cfa7b1b5a7b34438794aed2c178decee1%7C0%7C0%7C638545719814675925%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C0%7C%7C%7C&amp;sdata=9pTrMfiMD%2B5kQezxsZwTdOmaaktxURR99d7f6wHr%2FWQ%3D&amp;reserved=0"> Hotfix voor AEM Service Pack 6.5.21.0 of AEM Forms Service Pack 6.5.22.0 op de server van de JEE van de Ruimte van de Websfeer </a> </li>
        <li><a href="https://nam04.safelinks.protection.outlook.com/?url=https%3A%2F%2Fexperience.adobe.com%2F%23%2Fdownloads%2Fcontent%2Fsoftware-distribution%2Fen%2Faem.html%3Fpackage%3D%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq650%2Fhotfix%2FPaperCaptureSvc.zip&amp;data=05%7C02%7Cruchitas%40adobe.com%7Cf50f80aab6994875271a08dc91f2f137%7Cfa7b1b5a7b34438794aed2c178decee1%7C0%7C0%7C638545719814675925%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C0%7C%7C%7C&amp;sdata=9pTrMfiMD%2B5kQezxsZwTdOmaaktxURR99d7f6wHr%2FWQ%3D&amp;reserved=0"> Hotfix voor AEM Service Pack 6.5.21.0 of AEM Forms Service Pack 6.5.22.0 op server OSGi </a> </li>
     </ul>
     </td>
    <td>
    <ul>
    <li> Na de upgrade naar AEM Forms Service Pack 6.5.21.0 of AEM Forms Service Pack 6.5.22.0 kan de service Documentdigitalisering geen OCR-bewerkingen (Optical Character Recognition) uitvoeren op PDF's. Raadpleeg het artikel <a href="/help/forms/using/papercapture-service-resolution.md"> Problemen oplossen </a> voor installatie-instructies.(CQDOC-21680) </li>
    </ul>
    </td>    
  </tr>
  <tr>
    <td>21 juni 2024</td>
     <td>
     <ul>
     <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq650%2Fhotfix%2Fccm-ccr-content-10.0.206.zip"> Hotfix voor AEM Service Pack 6.5.21.0 </a> </li>
     </ul>
     </td>
    <td>
    <ul>
    <li>Conceptletters met XML-gegevens blijven tijdens de voorvertoning vastzitten in de laadstatus. Voor het downloaden en installatie instructies van hotfix, verwijs naar <a href="#install-hotfix"> download en installeer hotfix voor de kwestie van de ontwerp brief </a> sectie.(FORMS-14521)</li>
    </ul>
    </td>    
  </tr>
  <tr>
    <td>16 mei 2024</td>
     <td>
     <ul>
     <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/fd/adobe-aemfd-win-pkg-6.0.1192-010.zip"> Hotfix voor AEM Service Pack 6.5.20.0 voor Microsoft Vensters </a> </li>
     <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/fd/adobe-aemfd-linux-pkg-6.0.1192-010.zip"> Hotfix voor AEM Service Pack 6.5.20.0 voor Linux </a> </li>
     <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/fd/adobe-aemfd-osx-pkg-6.0.1192-010.zip"> Hotfix voor AEM Service Pack 6.5.20.0 voor Apple macOS </a> </li>
     </ul>
     </td>
    <td>
    <ul>
    <li>In een adaptief formulier dat is gebaseerd op een XDP met ingesloten scripts in selectievakjes, worden de scripts niet uitgevoerd voor elementen na dergelijke selectievakjes. Er is een hotfix beschikbaar voor dit probleem. (FORMS-14244) </li>
     <li> Rijen in de datumkiezer-widget worden afgebroken tijdens het doorlopen van maanden in de pop-upwidget voor velden met het bewerkings-/weergavepatroon. Er is een hotfix beschikbaar voor dit probleem. (FORMS-13620) </li>
     <li>Formulierverzendingen mislukken wanneer wordt geprobeerd de DOR-service (Document of Record) op de achtergrond te gebruiken. Het foutbericht dat wordt aangetroffen, is: "Handeling verzenden kan niet worden voltooid omdat de formulierbron niet correct is toegewezen." (FORMS-13798) </li>
     <li>Wanneer een adaptief formulier van een Adobe Experience Manager-publicatie-instantie naar een Adobe Experience Manager-workflow wordt verzonden, kunnen de bijlagen niet in de workflow worden opgeslagen.  (FORMS-14209) </li>
     <li> Bij het installeren van het AEM 6.5 Forms Service Pack 20-pakket (AEM Forms add-on pakket voor SP20), vertoont de AEM Sites-gebruikersinterface (UI) een aanzienlijke verslechtering van de prestaties.  (FORMS-13791) </li>
     <li>De prefill dienst ontbreekt met een ongeldige wijzeruitzondering in Interactieve Mededelingen. (CQDOC-21355)</li>
     <li>Configuraties die gebruikmaken van de oudere cloudservice voor Adobe Analytics met gebruikersverificatie op basis van referenties functioneren niet correct, waardoor de regels voor de analyse niet worden uitgevoerd. (FORMS-15428)
    </ul>
    </td>    
  </tr>
  <tr>
    <td>29 januari 2024</td>
     <td>
     <ul>
     <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq650%2Ffd%2Fforms-foundation-qs-content-4.0.170-FORMS-12692-B0001.zip"> Hotfix voor AEM Service Pack 6.5.19.0 voor Vensters op server JEE </a> </li>
     </ul>
     </td>
    <td>
    <ul>
    <li>Op AEM Forms op de JEE-server kan de HTML5 Forms die gebruik maakt van het contextpad niet worden gerenderd. (FORMS-12485, FORMS-12691).</li>
    </ul>
    </td>    
  </tr>
  <tr>
    <td>29 januari 2024</td>
     <td>
     <ul>
     <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq650%2Ffd%2Fadobe-aemfd-win-pkg-6.0.1016-004.zip"> Hotfix voor AEM Service Pack 6.5.18.0 voor Microsoft Vensters </a> </li>
     <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq650%2Ffd%2Fadobe-aemfd-linux-pkg-6.0.1016-004.zip">Hotfix voor AEM Service Pack 6.5.18.0 voor Linux</a></li>
     <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq650%2Ffd%2Fadobe-aemfd-osx-pkg-6.0.1016-004.zip">Hotfix voor AEM Service Pack 6.5.18.0 voor Apple macOS</a></li>
     </ul>
     </td>
    <td>
    <ul>
    <li> De uit-van-de-doos component van de KrabbelHandtekening ontbreekt om voor een voorproef in een adaptieve vorm terug te geven. (FORMS-12073).</li>
    </ul>
    </td>    
   </tr>
   <tr>
    <td>20 november 2023</td>
     <td>
     <ul>
     <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/fd/adobe-aemfd-linux-pkg-6.0.1016-002.zip"> Hotfix voor AEM Service Pack 6.5.18.0 voor Linux </a> </li>
     <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/fd/adobe-aemfd-win-pkg-6.0.1016-002.zip"> Hotfix voor AEM Service Pack 6.5.18.0 voor Microsoft Vensters </a> </li>
     <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/fd/adobe-aemfd-osx-pkg-6.0.1016-002.zip">Hotfix voor AEM Service Pack 6.5.18.0 voor Apple macOS</a></li>
     </ul>
     </td>
    <td>
    <ul>
    <li>Inline ondertekenen werkt niet meer wanneer een omleidings-URL wordt ingesteld in de hulplijncontainer van een adaptief formulier. (FORMS-10493)</li>
    <li>Document of Record (DoR)-sjablonen kunnen niet worden gepubliceerd voor gelokaliseerde adaptieve Forms. (FORMS-10535)</li>
    <li>Interactieve communicatie met grote inline-afbeeldingen kan niet worden geopend in de bewerkingsmodus. (FORMS-10578)</li>
    </ul>
    </td>    
  </tr>
  <tbody>
</table>

## Een hotfix downloaden en installeren {#download-install-hotfix}

Voer de volgende stappen uit om de hotfix te downloaden en installeren:

1. Download [ Hotfix ](#hotfix-for-adaptive-forms) van de verbinding van de Distributie van de Software.
1. Extraheer het Hotfix-archiefbestand zodat u een Experience Manager-pakket (.zip) en -bundelbestanden (.jar) kunt verkrijgen.
1. Upload en installeer het pakket (.zip) via de [ Manager van het Pakket ](https://experienceleague.adobe.com/docs/experience-manager-65/content/sites/administering/contentmanagement/package-manager.html?lang=es#accessing).
1. Open de bundels voor configuratiebeheer `https://server:host/system/console/bundles`, upload en installeer de bundel (.jar). De hotfix is geïnstalleerd.


## Hotfix downloaden en installeren voor conceptversie van brief {#install-hotfix}

Voer de volgende stappen uit om het probleem op te lossen:

1. Download [ hotfix ](#hotfix-for-adaptive-forms) van het portaal van de Distributie van de Software.
2. Upload en installeer het pakket (.zip) gebruikend de [ Manager van het Pakket van CRX ](https://experienceleague.adobe.com/docs/experience-manager-65/content/sites/administering/contentmanagement/package-manager.html?lang=es#accessing).