---
title: Rendering en levering
seo-title: Rendering en levering
description: 'null'
seo-description: 'null'
uuid: 1253b6a5-6bf3-42b1-be3a-efa23b6ddb51
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
discoiquuid: 672d5b1e-6b2f-4afe-ab04-c398e5ef45d5
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Rendering en levering{#rendering-and-delivery}

>[!NOTE]
>
>Adobe adviseert gebruikend de Redacteur van het KUUROORD voor projecten die op kader-gebaseerde cliënt-zijteruggeven van enige paginatoepassing (b.v. Reageren) vereisen. [Meer](/help/sites-developing/spa-overview.md)informatie.

AEM-inhoud kan eenvoudig worden gerenderd via [Sling Default Servlets](https://sling.apache.org/documentation/bundles/rendering-content-default-get-servlets.html) om [JSON](https://sling.apache.org/documentation/bundles/rendering-content-default-get-servlets.html#default-json-rendering) en andere indelingen te renderen.

Die buiten-de-box-renders lopen doorgaans de repository en retourneren inhoud zoals ze is.

AEM, via Sling, steunt ook het ontwikkelen van en het opstellen van douane het plaatsen renderers om volledige controle van het teruggegeven schema en de inhoud te nemen.

De Standaard Renderers van de Diensten van de inhoud vullen het hiaat tussen uit-van-de-doos het Verspreiden Gebreken en de Ontwikkeling van de Douane die aanpassing en controle van vele aspecten van de teruggegeven inhoud zonder ontwikkeling toestaat.

Het volgende diagram toont het teruggeven van inhoudsdiensten.

![chlimage_1-15](assets/chlimage_1-15.png)

## JSON aanvragen {#requesting-json}

Gebruik **&lt;RESOURCE.caas[.&lt;EXPORTCONFIG][.&lt;EXPORT-CONFIG].json** om JSON aan te vragen.

<table>
 <tbody>
  <tr>
   <td>BRON</td>
   <td>een entiteitsmiddel onder /content/entities<br /> of <br /> een inhoudsmiddel onder /content</td>
  </tr>
  <tr>
   <td>EXPORTCONFIG</td>
   <td><p><strong>OPTIONEEL</strong><br /> </p> <p>een exportconfiguratie gevonden onder /apps/mobileapps/caas/exportConfigs/EXPORT-CONFIG<br /> <br /> Als u dit weglaat, wordt de standaardexportconfiguratie toegepast </p> </td>
  </tr>
  <tr>
   <td>DEPTH-INT</td>
   <td><strong>OPTIONELE</strong><br /> <br /> diepteherhaling voor rendering van kinderen, zoals wordt gebruikt bij rendering van elementen</td>
  </tr>
 </tbody>
</table>

## Exportconfiguraties maken {#creating-export-configs}

U kunt exportconfiguraties maken om JSON-rendering aan te passen.

U kunt een configuratieknooppunt maken onder */apps/mobileapps/caas/exportConfigs.*

| Node Name | Naam van de configuratie (voor renderingkiezer) |
|---|---|
| jcr:primaryType | nt:ongestructureerd |

In de volgende tabel worden de eigenschappen van Export Configs weergegeven:

<table>
 <tbody>
  <tr>
   <td><strong>Naam</strong></td>
   <td><strong>Type</strong></td>
   <td><strong>Standaard (indien, niet ingesteld)</strong></td>
   <td><strong>Waarde</strong></td>
   <td><strong>Beschrijving</strong></td>
  </tr>
  <tr>
   <td>includeComponents</td>
   <td>Tekenreeks[]</td>
   <td>alles opnemen</td>
   <td>sling:resourceType</td>
   <td>uitsluiten, details voor knooppunten met opgegeven volgorde:resourceType van JSON-export</td>
  </tr>
  <tr>
   <td>excludeComponents</td>
   <td>Tekenreeks[]</td>
   <td>niets uitsluiten</td>
   <td>sling:resourceType</td>
   <td>alleen details opnemen voor knooppunten met opgegeven afstand:resourceType van JSON-export</td>
  </tr>
  <tr>
   <td>excludePropertyPrefixes</td>
   <td>Tekenreeks[]</td>
   <td>niets uitsluiten</td>
   <td>Voorvoegsels voor eigenschappen</td>
   <td>eigenschappen die beginnen met opgegeven voorvoegsels, uitsluiten van JSON-export</td>
  </tr>
  <tr>
   <td>excludeProperties</td>
   <td>Tekenreeks[]</td>
   <td>niets uitsluiten</td>
   <td>Namen van eigenschappen</td>
   <td>opgegeven eigenschappen uitsluiten van JSON-export</td>
  </tr>
  <tr>
   <td>includeProperties</td>
   <td>Tekenreeks[]</td>
   <td>alles opnemen</td>
   <td>Namen van eigenschappen</td>
   <td><p>if excludePropertyPrefixes set<br /> this includes specified properties while matching the prefix being exclude,</p> <p>else (eigenschappen uitsluiten genegeerd) bevatten alleen deze eigenschappen</p> </td>
  </tr>
  <tr>
   <td>includeChildren</td>
   <td>Tekenreeks[]</td>
   <td>alles opnemen</td>
   <td>onderliggende namen</td>
   <td>gespecificeerde kinderen van de uitvoer van JSON uitsluiten</td>
  </tr>
  <tr>
   <td>excludeChildren</td>
   <td>Tekenreeks[]<br /> <br /> </td>
   <td>niets uitsluiten</td>
   <td>onderliggende namen</td>
   <td>alleen opgegeven onderliggende items opnemen van JSON-export, andere uitsluiten</td>
  </tr>
  <tr>
   <td>renameProperties</td>
   <td>Tekenreeks[]<br /> <br /> </td>
   <td>naam wijzigen</td>
   <td>&lt;actual_property_name&gt;,&lt;replacement_property_name&gt;</td>
   <td>naam van eigenschappen wijzigen met vervangingen</td>
  </tr>
 </tbody>
</table>

### Exportoverschrijvingen van het type resource {#resource-type-export-overrides}

Maak een configuratieknooppunt onder */apps/mobileapps/caas/exportConfigs.*

| name | resourceTypeOverrides |
|---|---|
| jcr:primaryType | nt:ongestructureerd |

In de volgende tabel worden de eigenschappen weergegeven:

<table>
 <tbody>
  <tr>
   <td><strong>Naam</strong></td>
   <td><strong>Type</strong></td>
   <td><strong>Standaard (indien, niet ingesteld)</strong></td>
   <td><strong>Waarde</strong></td>
   <td><strong>Beschrijving</strong></td>
  </tr>
  <tr>
   <td>&lt;SELECTOR_TO_INC&gt;</td>
   <td>Tekenreeks[] </td>
   <td>-</td>
   <td>sling:resourceType</td>
   <td>Voor de volgende het slingeren middeltypes, keer niet de standaardUitvoer van CaaS.<br /><br /> Retourneer een klant json-export door de resource als te renderen; &lt;RESOURCE&gt;.&lt;SELECTOR_TO_INC&gt;.json </td>
  </tr>
 </tbody>
</table>

### Bestaande Content Services Exportconfiguraties {#existing-content-services-export-configs}

De Diensten van de inhoud omvat twee uitvoerconfiguraties:

* default (geen config gespecificeerd)
* pagina (om sitepagina&#39;s te renderen)

#### Standaard exportconfiguratie {#default-export-configuration}

De standaard de uitvoerconfiguratie van de Diensten van de inhoud zal worden toegepast als een config in gevraagde URI wordt gespecificeerd.

&lt;RESOURCE>.caas[.&lt;DEPTH-INT>].json

<table>
 <tbody>
  <tr>
   <td><strong>Naam</strong></td>
   <td><strong>Waarde</strong></td>
  </tr>
  <tr>
   <td>excludeProperties</td>
   <td> </td>
  </tr>
  <tr>
   <td>excludePropertyPrefixes</td>
   <td>jcr:,sling:,cq:,eiken:,pge-</td>
  </tr>
  <tr>
   <td>includeProperties</td>
   <td>jcr:text,text<br /> jcr:title,title<br /> jcr:description,description<br /> jcr:lastModified,lastModified<br /> cq:tags,tags<br /> cq:lastModified,lastModified</td>
  </tr>
  <tr>
   <td>includeComponents</td>
   <td> </td>
  </tr>
  <tr>
   <td>excludeComponents</td>
   <td> </td>
  </tr>
  <tr>
   <td>includeChildren</td>
   <td> </td>
  </tr>
  <tr>
   <td>excludeChildren</td>
   <td> </td>
  </tr>
  <tr>
   <td>Sling JSON-overschrijvingen</td>
   <td>foundation/components/image<br /> wcm/foundation/components/image<br /> mobileapps/caas/components/data/contentReference<br /> mobileapps/caas/components/data/assetlist</td>
  </tr>
 </tbody>
</table>

#### Configuratie pagina exporteren {#page-export-configuration}

Deze configuratie breidt het gebrek uit om groeperende kinderen onder een kindknoop te omvatten.

&lt;SITE_PAGE>.caas.page[.&lt;DEPTH-INT>].json

### Additional Resources {#additional-resources}

Zie hieronder de middelen om over extra onderwerpen in de Diensten van de Inhoud te leren:

* [Modellen ontwikkelen](/help/mobile/models-in-repository.md)
* [Services voor het ontwerpen van inhoud](/help/mobile/develop-content-as-a-service.md)
* [Inhoudsservices beheren](/help/mobile/developing-content-services.md)

