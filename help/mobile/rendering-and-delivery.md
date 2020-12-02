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
source-git-commit: 7eb3529de1c99d09eaa78c7589320a85e729400b
workflow-type: tm+mt
source-wordcount: '575'
ht-degree: 4%

---


# Renderen en leveren{#rendering-and-delivery}

>[!NOTE]
>
>Adobe raadt aan de SPA Editor te gebruiken voor projecten die renderen op basis van één pagina voor toepassingsframework op de client-side vereisen (bijvoorbeeld Reageren). [Meer](/help/sites-developing/spa-overview.md) informatie.

AEM inhoud kan eenvoudig worden gerenderd via [Standaardservers verkopen](https://sling.apache.org/documentation/bundles/rendering-content-default-get-servlets.html) om [JSON](https://sling.apache.org/documentation/bundles/rendering-content-default-get-servlets.html#default-json-rendering) en andere indelingen te renderen.

Die buiten-de-box-renders lopen doorgaans de repository en retourneren inhoud zoals ze is.

AEM, via Sling, steunt ook het ontwikkelen van en het opstellen van douane rangschikkende renderers om volledige controle van het teruggegeven schema en de inhoud te nemen.

De Standaard Renderers van de Diensten van de inhoud vullen het hiaat tussen uit-van-de-doos het Verspreiden Gebreken en de Ontwikkeling van de Douane die aanpassing en controle van vele aspecten van de teruggegeven inhoud zonder ontwikkeling toestaat.

Het volgende diagram toont het teruggeven van inhoudsdiensten.

![chlimage_1-15](assets/chlimage_1-15.png)

## JSON {#requesting-json} aanvragen

Gebruik **&lt;RESOURCE.caas[.&lt;export-config>.][&lt;export-config>.] jsonto request JSON.**

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
   <td><strong></strong><br /> <br /> OPTIONALdepth recursion for rendering children as used in Sling rendering</td>
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

### Overschrijvingen {#resource-type-export-overrides} van het type resource

Een configuratienode maken onder */apps/mobileapps/caas/exportConfigs.*

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
   <td>&lt;selector_to_inc&gt;</td>
   <td>Tekenreeks[] </td>
   <td>-</td>
   <td>sling:resourceType</td>
   <td>Voor de volgende het slingeren middeltypes, keer niet de standaardUitvoer van CaaS.<br /> Retourneer een klant json-export door de resource als weer te geven;<br /> &lt;resource&gt;.&lt;selector_to_inc&gt;.json </td>
  </tr>
 </tbody>
</table>

### Existing Content Services Export Configs {#existing-content-services-export-configs}

De Diensten van de inhoud omvat twee uitvoerconfiguraties:

* default (geen config gespecificeerd)
* pagina (om sitepagina&#39;s te renderen)

#### Standaard exportconfiguratie {#default-export-configuration}

De standaard de uitvoerconfiguratie van de Diensten van de inhoud zal worden toegepast als een config in gevraagde URI wordt gespecificeerd.

&lt;resource>.caas[.&lt;depth-int>].json

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

#### Configuratie voor exporteren van pagina {#page-export-configuration}

Deze configuratie breidt het gebrek uit om groeperende kinderen onder een kindknoop te omvatten.

&lt;site_page>.caas.page[.&lt;depth-int>].json

### Aanvullende bronnen {#additional-resources}

Zie hieronder de middelen om over extra onderwerpen in de Diensten van de Inhoud te leren:

* [Modellen ontwikkelen](/help/mobile/administer-mobile-apps.md)
* [Services voor het ontwerpen van inhoud](/help/mobile/develop-content-as-a-service.md)
* [Inhoudsservices beheren](/help/mobile/developing-content-services.md)

