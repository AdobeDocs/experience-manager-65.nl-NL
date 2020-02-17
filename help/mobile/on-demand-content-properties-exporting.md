---
title: Inhoud-eigenschappen gebruiken om inhoud te exporteren
seo-title: Inhoud-eigenschappen gebruiken om inhoud te exporteren
description: Op de volgende pagina worden App-eigenschappen en -knooppunten weergegeven.
seo-description: Op de volgende pagina worden App-eigenschappen en -knooppunten weergegeven.
uuid: 73f1832f-e457-47d0-a0e1-80af90897d31
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-on-demand-services-app
discoiquuid: a3006835-b1d2-47d6-959a-cdb692e34e1e
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Inhoud-eigenschappen gebruiken om inhoud te exporteren{#using-content-properties-to-export-content}

>[!NOTE]
>
>Adobe adviseert gebruikend de Redacteur van het KUUROORD voor projecten die op kader-gebaseerde cliënt-zijteruggeven van enige paginatoepassing (b.v. Reageren) vereisen. [Meer](/help/sites-developing/spa-overview.md)informatie.

Apps worden weergegeven als *cq:Pages* in AEM.

Ze delen dezelfde algemene eigenschappen die in elke *cq:Page* worden gevonden, naast de hieronder getoonde eigenschappen die integratie ondersteunen.

## App-eigenschappen {#app-properties}

In de volgende tabel staan de eigenschappen en knooppunten van de **app**.

<table>
 <tbody>
  <tr>
   <td><strong>PropertyName</strong></td>
   <td><strong>Type</strong></td>
   <td><strong>Beschrijving</strong></td>
  </tr>
  <tr>
   <td>dps-cloudConfig</td>
   <td>String:Path</td>
   <td><p>Pad naar een geconfigureerde Mobile On-Demand Cloud Service. Wordt gebruikt voor AEM Mobile naar Mobile On-Demand-handelingen (API-aanroep)</p> <p>Deze koppeling wordt geconfigureerd via de tegel Verbinding beheren wanneer een auteur een Mobile On-Demand Cloud Service kiest om de app aan te koppelen.</p> </td>
  </tr>
  <tr>
   <td>dps-exportTemplate</td>
   <td>String:Path</td>
   <td><p>Pad naar de exportconfiguraties van de app. De exportconfiguratie is een map met 2 onderliggende ContentSync-exportconfiguratiesjablonen;</p> <p><i>dps-artikel</i>: ContentSync exportconfiguratie om artikelinhoud te exporteren</p> <p><i>dps-HTMLResources</i>: ContentSync exportconfiguratie voor het exporteren van gedeelde app/artikel-bronnen</p> </td>
  </tr>
  <tr>
   <td>dps-projectId</td>
   <td>Tekenreeks</td>
   <td><p>Id/URI van het Mobile On-Demand-project waaraan deze app is gekoppeld of gekoppeld.</p> <p>Deze koppeling wordt geconfigureerd via de beheertegel Verbinding wanneer een auteur het project kiest uit een lijst met beschikbare projecten voor de bijbehorende Mobile On-Demand Cloud Service.</p> </td>
  </tr>
  <tr>
   <td>dps-projectTitle</td>
   <td>Tekenreeks</td>
   <td>App-titel.</td>
  </tr>
  <tr>
   <td>dps-resourceType</td>
   <td>Tekenreeks</td>
   <td>Inhoudstype.</td>
  </tr>
  <tr>
   <td>dps-sharedHTMLResources-lastUploaded</td>
   <td>Date</td>
   <td>Datum van laatste upload van gedeelde bronnen van AEM naar AEM Mobile.</td>
  </tr>
  <tr>
   <td>dps-sharedHTMLResources-lastUploadedBy</td>
   <td>String:userid</td>
   <td>Id van de gebruiker die het laatste uploaden van een verzoek om gedeelde bronnen van AEM naar AEM Mobile heeft uitgevoerd.</td>
  </tr>
  <tr>
   <td>pge-dashboard-config</td>
   <td>String:Path</td>
   <td>Pad naar een dashboardconfiguratie. Het pad kan zo nodig worden omgeleid naar een aangepaste dashbaord-configuratie.</td>
  </tr>
  <tr>
   <td>sling:resourceType</td>
   <td>String:Path</td>
   <td><p>Pad naar een cq:Component die <i>mobileapps/core/components/instance is of uitbreidt.</i></p> <p>Dit biedt de aanwezigheid en rendering in de Apps Catalog.</p> </td>
  </tr>
 </tbody>
</table>

U kunt ***Inhoud-eigenschappen*** gebruiken om inhoud te maken. Zie de volgende bronnen voor het maken en exporteren van artikelen en gedeelde bronnen:

* [Eigenschappen van inhoud](/help/mobile/content-properties.md)
* [Artikel-exportconfiguratie maken](/help/mobile/creating-article-export-configuration.md)
* [Configuratie voor gedeelde bronnen exporteren](/help/mobile/creating-shared-resources-export-configuration.md)
