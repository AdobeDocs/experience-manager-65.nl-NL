---
title: Hotfixes voor AEM Forms
description: Hier vindt u informatie over het downloaden en installeren van een hotfix voor AEM Forms.
exl-id: 37287332-3c8d-4ddc-a77e-3c5ee332898b
solution: Experience Manager
feature: Release Information
role: User,Admin,Architect,Developer
source-git-commit: 5e2799505bc6d69cd5898445a9300ad162ef74fd
workflow-type: tm+mt
source-wordcount: '518'
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
    <td><strong>Hotfix-downloadkoppeling (AEM koppeling voor softwaredistributie)</strong></td>
    <td><strong>Opgeloste problemen</strong></td>
  </tr>
  <tr>
    <td>16 mei 2024</td>
     <td>
     <ul>
     <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/fd/adobe-aemfd-win-pkg-6.0.1192-010.zip">Hotfix voor AEM Service Pack 6.5.20.0 voor Microsoft Windows</a> </li>
     <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/fd/adobe-aemfd-linux-pkg-6.0.1192-010.zip">Hotfix voor AEM Service Pack 6.5.20.0 voor Linux </a> </li>
     <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/fd/adobe-aemfd-osx-pkg-6.0.1192-010.zip">Hotfix voor AEM Service Pack 6.5.20.0 voor Apple macOS</a> </li>
     </ul>
     </td>
    <td>
    <ul>
    <li>In een adaptief formulier dat is gebaseerd op een XDP met ingesloten scripts in selectievakjes, worden de scripts niet uitgevoerd voor elementen na dergelijke selectievakjes. Er is een hotfix beschikbaar voor dit probleem. (FORMS-14244) </li>
     <li> Rijen in de datumkiezer-widget worden afgebroken tijdens het doorlopen van maanden in de pop-upwidget voor velden met het bewerkings-/weergavepatroon. Er is een hotfix beschikbaar voor dit probleem. (FORMS-13620) </li>
     <li>Formulierverzendingen mislukken wanneer wordt geprobeerd de DOR-service (Document of Record) op de achtergrond te gebruiken. Het foutbericht dat wordt aangetroffen, is: "Handeling verzenden kan niet worden voltooid omdat de formulierbron niet correct is toegewezen." (FORMS-13798) </li>
     <li>Wanneer een adaptief formulier van een Adobe Experience Manager-publicatie-instantie naar een Adobe Experience Manager-workflow wordt verzonden, kunnen de bijlagen niet in de workflow worden opgeslagen.  (FORMS-14209) </li>
     <li> Bij het installeren van AEM 6.5 Forms Service Pack 20-pakket (AEM Forms add-on pakket voor SP20), vertoont de AEM Sites-gebruikersinterface (UI) een aanzienlijke verslechtering van de prestaties.  (FORMS-13791) </li>
     <li>De prefill dienst ontbreekt met een ongeldige wijzeruitzondering in Interactieve Mededelingen. (CQDOC-21355)</li>
    </ul>
    </td>    
  </tr>
  <tr>
    <td>29 januari 2024</td>
     <td>
     <ul>
     <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq650%2Ffd%2Fforms-foundation-qs-content-4.0.170-FORMS-12692-B0001.zip">Hotfix voor AEM Service Pack 6.5.19.0 voor Vensters op server JEE</a> </li>
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
     <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq650%2Ffd%2Fadobe-aemfd-win-pkg-6.0.1016-004.zip">Hotfix voor AEM Service Pack 6.5.18.0 voor Microsoft Windows</a> </li>
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
     <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/fd/adobe-aemfd-linux-pkg-6.0.1016-002.zip">Hotfix voor AEM Service Pack 6.5.18.0 voor Linux</a> </li>
     <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/fd/adobe-aemfd-win-pkg-6.0.1016-002.zip">Hotfix voor AEM Service Pack 6.5.18.0 voor Microsoft Windows</a> </li>
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

1. Downloaden [Hotfix](#hotfix-for-adaptive-forms) via de koppeling Softwaredistributie.
1. Extraheer het Hotfix-archiefbestand zodat u een Experience Manager-pakket (.zip) en -bundelbestanden (.jar) kunt verkrijgen.
1. Upload en installeer het pakket (.zip) via de [Pakketbeheer](https://experienceleague.adobe.com/docs/experience-manager-65/content/sites/administering/contentmanagement/package-manager.html?lang=es#accessing).
1. De configuratiemanager-bundels openen `https://server:host/system/console/bundles`, uploadt en installeert de bundel (.jar). De hotfix is geïnstalleerd.
