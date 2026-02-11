---
title: Hotfixes voor AEM Forms
description: Hier vindt u informatie over het downloaden en installeren van een hotfix voor AEM Forms.
exl-id: 37287332-3c8d-4ddc-a77e-3c5ee332898b
solution: Experience Manager
feature: Release Information
role: User,Admin,Developer
source-git-commit: 598bd1a0b3ad48a958f09ae3810b4f2663ee1014
workflow-type: tm+mt
source-wordcount: '2024'
ht-degree: 0%

---

# Adobe Experience Manager Forms Hotfixes{#aem-form-hotfix}

Dit artikel bevat een overzicht van de kritieke oplossingen die zijn geïmplementeerd om bekende problemen aan te pakken, de stabiliteit van het systeem te verbeteren en de algehele prestaties van AEM Forms te verbeteren.

>[!NOTE]
>
> De hotfixes zijn cumulatief ontworpen en omvatten alle voorafgaande fixes. Wanneer u de nieuwste hotfix toepast op een release, wordt niet alleen het meest recente probleem opgelost, maar worden ook alle eerdere correcties en verbeteringen aangebracht.

## Hotfixes voor AEM Forms {#hotfix-for-aem-forms}

<table>
  <tbody>
  <tr>
    <td><strong>Datum</strong></td>
    <td><strong>Hotfix-downloadkoppeling (AEM-koppeling voor softwaredistributie)</strong></td>
    <td><strong>Opgeloste problemen</strong></td>
  </tr>
    <tr>
    <td>
      <strong> feb 10, 2026 </strong><br>
      <em> is op van toepassing:</em> AEM Forms SP24 <br>
    </td>
    <td>
    <ul> <a href = "https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/featurepack/bb-expressionmanager-pkg-10.0.48.zip"> AEM 6.5 Forms AddOn Hotfix </a>
    </ul>
    </td>
    <td>
    <ul>
    <li><b> FORMS-23875 </b> in het modelonderzoek van de Gegevens van het Vorm, wordt een markering van HTML getoond in UI zelfs wanneer een relevante entiteit niet aanwezig is.
      <ul></tr>
  <tr>
    <td>
      <strong> 14 okt., 2025 </strong><br>
      <em> is op van toepassing:</em> ImgToPdf ontbreekt met AEM Forms SP23 Jrelige <br>
    </td>
    <td>
    <ul> Voor resolutie, contacteer <a href="https://business.adobe.com/in/support/main.html"> de Steun van Adobe Experience Manager Forms </a>
    </ul>
    </td>
    <td>
    <ul>
    <li> <b> (FORMS-22029): </b> verbetert de betrouwbaarheid van PDF-conversie door een probleem op te lossen waarbij PDF Generator (PDFG) afbeeldingsbestanden na de upgrade naar SP23 niet naar PDF kan converteren. Dit leidt tot onverwachte naverwerkingsfouten.
      <ul></tr>
  <tr>
    <td>
      <strong> sep 23, 2025 </strong><br>
    </td>
    <td>
    <ul>
    <strong> Jreliëf:</strong>
    <li>Vensters - <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-23-0-hotfix-3/jboss/adobe-aem-forms-jee-hotfix3-6.5.23.0-win-jboss.zip"> Hotfix voor AEM Service Pack 6.5.23.0 op Vensters voor server JBoss </a></li>
    <li>Linux - <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-23-0-hotfix-3/jboss/adobe-aem-forms-jee-hotfix3-6.5.23.0-linux-jboss.tar.gz"> Hotfix voor AEM Service Pack 6.5.23.0 op Linux voor JBoss server JEE </a></li>
    <strong> Weblogic:</strong>
    <li>Vensters - <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-23-0-hotfix-3/weblogic/adobe-aem-forms-jee-hotfix3-6.5.23.0-win-weblogic.zip"> Hotfix voor AEM Service Pack 6.5.23.0 op Vensters voor de server van de Weblogic JEE </a></li>
    <li>Linux - <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-23-0-hotfix-3/weblogic/adobe-aem-forms-jee-hotfix3-6.5.23.0-linux-weblogic.tar.gz"> Hotfix voor AEM Service Pack 6.5.23.0 op Linux voor de server van de Weblogic JEE </a></li>
    <strong> Websphere:</strong>
    <li>Vensters - <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-23-0-hotfix-3/websphere/adobe-aem-forms-jee-hotfix3-6.5.23.0-win-websphere.zip"> Hotfix voor AEM Service Pack 6.5.23.0 op Vensters voor de server van JEE Websphere </a></li>
    <li>Linux - <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-23-0-hotfix-3/websphere/adobe-aem-forms-jee-hotfix3-6.5.23.0-linux-websphere.tar.gz"> Hotfix voor AEM Service Pack 6.5.23.0 op Linux voor de server van Websphere JEE </a></li>
    </ul>
    </td>
    <td>
    <ul>
    <strong> dit hotfix bevestigt het volgende:</strong> 
    <li> <b> (FORMS-21378):</b> Verbeterde betrouwbaarheid van formulierverzendingen door een probleem op te lossen waarbij verzending mislukt wanneer Server-Side Validation (SSV) is ingeschakeld en Meta Info is berekend.

<li> <b> (FORMS-21721):</b> Verbeterde een kwestie waar PS aan PDF en HTML aan PDF (WebKit) omzettingen ontbreken na het opstellen van hotfix (vrijgegeven op <b> Aug 05, 2025 </b>) voor 6.5.23.0. 
    </li>
    </ul>
    </td>    
  </tr>
    </ul>
    </td>
  <tr>
    <td>
      <strong> aug 05, 2025 </strong><br>
      <em> is op van toepassing:</em> AEM 6.5 Forms Service Pack 23 <br>
      <em> instructies van de Opstelling:</em>
      <a href="/help/forms/using/mitigating-xxe-and-configuration-vulnerabilities-for-experience-manager-forms-jee.md#option-1-for-users-on-version-65230-install-latest-hotfix">
        XE-, configuratie- en externe code-uitvoering beperken (CVE-2025-49533)-kwetsbaarheden voor AEM Forms op JEE
      </a>
    </td>
    <td>
    <ul>
    <li><strong>Reliëf:</strong></li>
    <li>Vensters - <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-0-hotfix-02/jboss/adobe-aem-forms-jee-hotfix2-6.5.23.0-win-jboss.zip"> Hotfix voor AEM Service Pack 6.5.23.0 op Vensters voor server JBoss </a></li>
    <li>Linux - <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-0-hotfix-02/jboss/adobe-aem-forms-jee-hotfix2-6.5.23.0-linux-jboss.tar.gz"> Hotfix voor AEM Service Pack 6.5.23.0 op Linux voor JBoss server JEE </a></li>
    <li><strong>Weblogic:</strong></li>
    <li>Vensters - <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-0-hotfix-02/weblogic/adobe-aem-forms-jee-hotfix2-6.5.23.0-win-weblogic.zip"> Hotfix voor AEM Service Pack 6.5.23.0 op Vensters voor de server van de Weblogic JEE </a></li>
    <li>Linux - <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-0-hotfix-02/weblogic/adobe-aem-forms-jee-hotfix2-6.5.23.0-linux-weblogic.tar.gz"> Hotfix voor AEM Service Pack 6.5.23.0 op Linux voor de server van de Weblogic JEE </a></li>
    <li><strong>Websfeer:</strong></li>
    <li>Vensters - <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-0-hotfix-02/websphere/adobe-aem-forms-jee-hotfix2-6.5.23.0-win-websphere.zip"> Hotfix voor AEM Service Pack 6.5.23.0 op Vensters voor de server van JEE Websphere </a></li>
    <li>Linux - <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-0-hotfix-02/websphere/adobe-aem-forms-jee-hotfix2-6.5.23.0-linux-websphere.zip"> Hotfix voor AEM Service Pack 6.5.23.0 op Linux voor de server van Websphere JEE </a></li>
    </ul>
    </td>
    <td>
    <ul>
    <li>Verbeterde beveiliging door een RCE-kwetsbaarheid (Remote Code Execution) in Adobe Experience Manager (AEM) Forms aan te pakken. De kwestie hield verband met de ontwikkelingswijze van Struts in het admin gebruikersinterface (UI), die willekeurige voorwerp-Grafiek de Taal van de Navigatie (OGNL) beoordeling door zuivert functionaliteit toeliet. Deze moeilijke situatie zorgt ervoor dat de de ontwikkelingswijze van Struts wordt onbruikbaar gemaakt en de aangewezen veiligheidsfilters worden toegepast om onbevoegde toegang te verhinderen.</li>
    <li>Verbeterde bescherming tegen XE-kwetsbaarheden (Extensible Markup Language) in de module Electronic Document Component (EDC) van Adobe Experience Manager (AEM) Forms. De kwetsbaarheden zijn veroorzaakt door een onjuiste verwerking van XML-documenten zonder XXE-beveiliging, wat kan leiden tot het lezen van lokale bestanden. De oplossing omvat:
      <ul>
        <li>Ervoor zorgen dat DocumentBuilderFactory in de klasse SecurityCheckHandler wordt gebruikt wordt gevormd om aanvallen van XXE te verhinderen.</li>
        <li>De EDC-webservice bijwerken om XML-documenten veilig te verwerken, zodat onbevoegde toegang tot lokale bestanden wordt voorkomen.</li>
      </ul>
    </li>
    </ul>
    </td>    
  </tr>
  <tr>
    <td>
      <strong> aug 05, 2025 </strong><br>
      <em> is op van toepassing:</em> AEM 6.5 Forms Service Pack 18 - 22 <br>
      <em> instructies van de Opstelling:</em>
      <a href="/help/forms/using/mitigating-xxe-and-configuration-vulnerabilities-for-experience-manager-forms-jee.md#option-2-for-users-on-65180---65220-manual-hotfix-installation">
        Handmatige hotfix-installatie voor servicepacks 18-22
      </a>
    </td>
    <td>
    <ul>
    <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/adobe-xxe-configuration-hotfix.zip">Reparatie voor AEM 6.5 Forms Service Pack 18 - AEM 6.5 Forms Service Pack 22 </a></li>
    </ul>
    </td>
    <td>
    <ul>
    <li>Verbeterde beveiliging door een RCE-kwetsbaarheid (Remote Code Execution) in Adobe Experience Manager (AEM) Forms aan te pakken. De kwestie hield verband met de ontwikkelingswijze van Struts in het admin gebruikersinterface (UI), die willekeurige voorwerp-Grafiek de Taal van de Navigatie (OGNL) beoordeling door zuivert functionaliteit toeliet. Deze moeilijke situatie zorgt ervoor dat de de ontwikkelingswijze van Struts wordt onbruikbaar gemaakt en de aangewezen veiligheidsfilters worden toegepast om onbevoegde toegang te verhinderen.</li>
    <li>Verbeterde bescherming tegen XE-kwetsbaarheden (Extensible Markup Language) in de documentbeveiligingsmodule van Adobe Experience Manager (AEM) Forms. De kwetsbaarheden zijn veroorzaakt door een onjuiste verwerking van XML-documenten zonder XXE-beveiliging, wat kan leiden tot het lezen van lokale bestanden. De oplossing omvat:
      <ul>
        <li>Ervoor zorgen dat DocumentBuilderFactory in de klasse SecurityCheckHandler wordt gebruikt wordt gevormd om aanvallen van XXE te verhinderen.</li>
        <li>De documentbeveiligingswebservice bijwerken om XML-documenten veilig te verwerken, zodat onbevoegde toegang tot lokale bestanden wordt voorkomen.</li>
      </ul>
    </li>
    </ul>
    </td>    
  </tr>
  <tr>
    <td>10 jul. 2025-</td>
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
    <li><strong> dit hotfix bevestigt het volgende:</strong>
      <ul>
        <li><strong> FORMS-20533:</strong> AEM Forms omvat nu een verbetering van de versie van Struts van 2.5.33 aan 6.x voor de vormencomponent. Dit levert eerder gemiste veranderingen van Struts die niet inbegrepen in SP23 waren. De ondersteuning is toegevoegd via een hotfix die u kunt downloaden en installeren om ondersteuning toe te voegen voor de nieuwste versie van Struts.</li>
        <li><strong> FORMS-20532:</strong> AEM Forms omvat nu een verbetering van de versie van Struts van 2.5.33 aan 6.x voor de outputcomponent. Dit levert eerder gemiste veranderingen van Struts die niet inbegrepen in SP23 waren. De ondersteuning is toegevoegd via een hotfix die u kunt downloaden en installeren om ondersteuning toe te voegen voor de nieuwste versie van Struts.</li>
        <li><strong> FORMS-20203:</strong> wanneer een gebruiker steunen van AEM Service Pack 2.5.x aan AEM Forms Service Pack 6.x bevordert, ontbreekt UI van het Beleid om alle configuraties, zoals de optie te tonen om een watermerk toe te voegen. U kunt de hotfix downloaden en installeren om dit probleem op te lossen.</li>
        <li><strong> FORMS-20360:</strong> Na bevordering aan AEM Forms Service Pack 6.5.23.0, ontbreekt de de omzettingsdienst ImageToPDF met de fout:<br>
        <code>17:15:44,468 ERROR [com.adobe.pdfg.GeneratePDFImpl] (default task-49) ALC-PDG-001-000-ALC-PDG-011-028-Error occurred while converting the input image file to PDF. com/adobe/internal/pdftoolkit/core/encryption/EncryptionImp</code><br>
        U kunt de hotfix downloaden en installeren om dit probleem op te lossen.</li>
      </ul>
    </li>
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
     <li><a href="https://nam04.safelinks.protection.outlook.com/?url=https%3A%2F%2Fexperience.adobe.com%2F%23%2Fdownloads%2Fcontent%2Fsoftware-distribution%2Fen%2Faem.html%3Fpackage%3D%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq650%2Fhotfix%2FPaperCaptureSvc.zip&data=05%7C02%7Cruchitas%40adobe.com%7Cf50f80aab6994875271a08dc91f2f137%7Cfa7b1b5a7b34438794aed2c178decee1%7C0%7C0%7C638545719814675925%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C0%7C%7C%7C&sdata=9pTrMfiMD%2B5kQezxsZwTdOmaaktxURR99d7f6wHr%2FWQ%3D&reserved=0"> Hotfix voor AEM Service Pack 6.5.21.0 of AEM Forms Service Pack 6.5.22.0 op JBoss JEE server </a> </li>
      <li><a href="https://nam04.safelinks.protection.outlook.com/?url=https%3A%2F%2Fexperience.adobe.com%2F%23%2Fdownloads%2Fcontent%2Fsoftware-distribution%2Fen%2Faem.html%3Fpackage%3D%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq650%2Fhotfix%2FPaperCaptureSvc.zip&data=05%7C02%7Cruchitas%40adobe.com%7Cf50f80aab6994875271a08dc91f2f137%7Cfa7b1b5a7b34438794aed2c178decee1%7C0%7C0%7C638545719814675925%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C0%7C%7C%7C&sdata=9pTrMfiMD%2B5kQezxsZwTdOmaaktxURR99d7f6wHr%2FWQ%3D&reserved=0"> Hotfix voor AEM Service Pack 6.5.21.0 of AEM Forms Service Pack 6.5.22.0 op Weblogic JEE-server </a> </li>
       <li><a href="https://nam04.safelinks.protection.outlook.com/?url=https%3A%2F%2Fexperience.adobe.com%2F%23%2Fdownloads%2Fcontent%2Fsoftware-distribution%2Fen%2Faem.html%3Fpackage%3D%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq650%2Fhotfix%2FPaperCaptureSvc.zip&data=05%7C02%7Cruchitas%40adobe.com%7Cf50f80aab6994875271a08dc91f2f137%7Cfa7b1b5a7b34438794aed2c178decee1%7C0%7C0%7C638545719814675925%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C0%7C%7C%7C&sdata=9pTrMfiMD%2B5kQezxsZwTdOmaaktxURR99d7f6wHr%2FWQ%3D&reserved=0"> Hotfix voor AEM Service Pack 6.5.21.0 of AEM Forms Service Pack 6.5.22.0 op de server van de JEE van de Ruimte van de Websfeer </a> </li>
        <li><a href="https://nam04.safelinks.protection.outlook.com/?url=https%3A%2F%2Fexperience.adobe.com%2F%23%2Fdownloads%2Fcontent%2Fsoftware-distribution%2Fen%2Faem.html%3Fpackage%3D%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq650%2Fhotfix%2FPaperCaptureSvc.zip&data=05%7C02%7Cruchitas%40adobe.com%7Cf50f80aab6994875271a08dc91f2f137%7Cfa7b1b5a7b34438794aed2c178decee1%7C0%7C0%7C638545719814675925%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C0%7C%7C%7C&sdata=9pTrMfiMD%2B5kQezxsZwTdOmaaktxURR99d7f6wHr%2FWQ%3D&reserved=0"> Hotfix voor AEM Service Pack 6.5.21.0 of AEM Forms Service Pack 6.5.22.0 op server OSGi </a> </li>
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

## Een OSGi Hotfix downloaden en installeren {#download-install-hotfix}

Voer de volgende stappen uit om de hotfix te downloaden en installeren:

1. Download [&#x200B; Hotfix &#x200B;](#hotfix-for-adaptive-forms) van de verbinding van de Distributie van de Software.
1. Extraheer het Hotfix-archiefbestand zodat u een Experience Manager-pakket (.zip) en -bundelbestanden (.jar) kunt verkrijgen.
1. Upload en installeer het pakket (.zip) via de [&#x200B; Manager van het Pakket &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-65/content/sites/administering/contentmanagement/package-manager.html?lang=es#accessing).
1. Open de bundels voor configuratiebeheer `https://server:host/system/console/bundles`, upload en installeer de bundel (.jar). De hotfix is geïnstalleerd.

## Een JEE-patch installeren {#download-install-jee-patch}

Voor instructies om een flard te installeren JEE, zie de [&#x200B; documentatie van de Installateur van de Reparatie van AEM Forms JEE &#x200B;](/help/release-notes/jee-patch-installer-65.md).


## Hotfix downloaden en installeren voor conceptversie van brief {#install-hotfix}

Voer de volgende stappen uit om het probleem op te lossen:

1. Download [&#x200B; hotfix &#x200B;](#hotfix-for-adaptive-forms) van het portaal van de Distributie van de Software.
2. Upload en installeer het pakket (.zip) gebruikend de [&#x200B; Manager van het Pakket van CRX &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-65/content/sites/administering/contentmanagement/package-manager.html?lang=es#accessing).
