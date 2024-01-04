---
title: Hotfixes voor AEM Forms
description: Hier vindt u informatie over het downloaden en installeren van een hotfix voor AEM Forms.
exl-id: 37287332-3c8d-4ddc-a77e-3c5ee332898b
source-git-commit: 276b0122fb3d88c584dd6b2b4c2c6f6eda9d0537
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 0%

---

# Adobe Experience Manager Forms Hotfixes{#aem-form-hotfix}

Dit artikel bevat een overzicht van de kritieke oplossingen die zijn geïmplementeerd om bekende problemen aan te pakken, de stabiliteit van het systeem te verbeteren en de algehele prestaties van AEM Forms te verbeteren.

## Hotfixes voor adaptieve Forms {#hotfix-for-adaptive-forms}

<table>
  <tbody>
  <tr>
    <td><strong>Datum</strong></td>
    <td><strong>Hotfix-downloadkoppeling (AEM koppeling Softwaredistributie)</strong></td>
    <td><strong>Opgeloste problemen</strong></td>
   </tr>
   <tr>
    <td>20 november 2023</td>
     <td>
     <ul>
     <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/fd/adobe-aemfd-linux-pkg-6.0.1016-002.zip">Hotfix voor AEM Service Pack 6.5.18.0 voor Linux</a> </li>
     <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/fd/adobe-aemfd-win-pkg-6.0.1016-002.zip">Hotfix voor AEM Service Pack 6.5.18.0 voor Vensters</a> </li>
     <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/fd/adobe-aemfd-osx-pkg-6.0.1016-002.zip">Hotfix voor AEM Service Pack 6.5.18.0 voor Mac OS</a></li>
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

1. Downloaden [Hotfix](#hotfix-for-adaptive-forms) via de koppeling Software Distribition.
1. Extraheer het Hotfix-archiefbestand zodat u een Experience Manager-pakket (.zip) en -bundelbestanden (.jar) kunt verkrijgen.
1. Upload en installeer het pakket (.zip) via de [Pakketbeheer](https://experienceleague.adobe.com/docs/experience-manager-65/content/sites/administering/contentmanagement/package-manager.html?lang=es#accessing).
1. De configuratiemanager-bundels openen `https://server:host/system/console/bundles`, uploadt en installeert de bundel (.jar). De hotfix is geïnstalleerd.
