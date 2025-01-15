---
title: Inhoud-eigenschappen gebruiken om inhoud te exporteren
description: Op de volgende pagina worden App-eigenschappen en -knooppunten weergegeven.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-on-demand-services-app
exl-id: db1c33c9-8539-436d-b4d0-3d5e6fd688ed
solution: Experience Manager
feature: Mobile
role: Developer
source-git-commit: 2dae56dc9ec66f1bf36bbb24d6b0315a5f5040bb
workflow-type: tm+mt
source-wordcount: '311'
ht-degree: 0%

---

# Inhoud-eigenschappen gebruiken om inhoud te exporteren{#using-content-properties-to-export-content}

{{ue-over-mobile}}

Apps worden vertegenwoordigd als *cq:Pagina&#39;s* in AEM.

Zij delen de zelfde gemeenschappelijke eigenschappen die in om het even welk *worden gevonden:Pagina* naast hieronder getoonde anderen die integratie ondersteunende eigenschappen vertegenwoordigen.

## App-eigenschappen {#app-properties}

De volgende lijst toont **Eigenschappen en Knooppunten van de Toepassing**.

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
   <td><p>Pad naar een geconfigureerde Mobile On-Demand Cloud Service. Wordt gebruikt voor acties van AEM Mobile naar Mobile On-Demand (API-aanroep)</p> <p>Deze koppeling wordt geconfigureerd via de tegel Verbinding beheren wanneer een auteur een Cloud Service Mobiel op aanvraag kiest om de app aan te koppelen.</p> </td>
  </tr>
  <tr>
   <td>dps-exportTemplate</td>
   <td>String:Path</td>
   <td><p>Pad naar de exportconfiguraties van de app. De exportconfiguratie is een map met 2 onderliggende ContentSync-exportconfiguratiesjablonen;</p> <p><i> dps-artikel </i>: De de uitvoerconfiguratie van ContentSync om artikelinhoud uit te voeren</p> <p><i> dps-HTMLResources </i>: De de uitvoerconfiguratie van ContentSync om app/artikel gedeelde middelen uit te voeren</p> </td>
  </tr>
  <tr>
   <td>dps-projectId</td>
   <td>String</td>
   <td><p>Id/URI van het Mobile On-Demand-project waaraan deze app is gekoppeld of gekoppeld.</p> <p>Deze vereniging wordt gevormd via de Manage tegel van de Verbinding wanneer een auteur het project van een lijst van beschikbare projecten voor de bijbehorende Mobiele Cloud Service On-Demand kiest.</p> </td>
  </tr>
  <tr>
   <td>dps-projectTitle</td>
   <td>String</td>
   <td>App-titel.</td>
  </tr>
  <tr>
   <td>dps-resourceType</td>
   <td>String</td>
   <td>Inhoudstype.</td>
  </tr>
  <tr>
   <td>dps-sharedHTMLResources-lastUploaded</td>
   <td>Datum</td>
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
   <td><p>Weg aan cq:Component die <i> mobileapps/core/components/instance is of uitbreidt.</i></p> <p>Dit biedt de aanwezigheid en rendering in de Apps Catalog.</p> </td>
  </tr>
 </tbody>
</table>

U kunt ***Eigenschappen van de Inhoud*** gebruiken om inhoud tot stand te brengen. Zie de volgende bronnen voor het maken en exporteren van artikelen en gedeelde bronnen:

* [Eigenschappen van inhoud](/help/mobile/content-properties.md)
* [Artikel-exportconfiguratie maken](/help/mobile/creating-article-export-configuration.md)
* [Configuratie voor gedeelde bronnen exporteren](/help/mobile/creating-shared-resources-export-configuration.md)
