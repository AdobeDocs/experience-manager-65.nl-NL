---
title: Rendering en levering
description: Leer hoe u Adobe Experience Manager-inhoud kunt renderen door Default Services te verkopen en JSON en andere indelingen te renderen.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
exl-id: f0c543ae-33ed-40bb-9eb7-0dc3bdea69e0
source-git-commit: 9d497413d0ca72f22712581cf7eda1413eb8d643
workflow-type: tm+mt
source-wordcount: '574'
ht-degree: 0%

---

# Rendering en levering{#rendering-and-delivery}

>[!NOTE]
>
>De Adobe adviseert het gebruiken van de SPARedacteur voor projecten die op kader-gebaseerde cliënt-zijteruggeven van enige paginatoepassing (bijvoorbeeld, Reageren) vereisen. [Meer informatie](/help/sites-developing/spa-overview.md).

Adobe Experience Manager-inhoud (AEM) kan eenvoudig worden gerenderd via [Standaardservers splitsen](https://sling.apache.org/documentation/bundles/rendering-content-default-get-servlets.html) renderen [JSON](https://sling.apache.org/documentation/bundles/rendering-content-default-get-servlets.html#default-json-rendering) en andere indelingen.

Die uitleveringen buiten de doos lopen normaal gesproken de opslagplaats en retourneren inhoud.

AEM, als Verbergen, steunt ook het ontwikkelen van en het opstellen van douane het plaatsen renderers om volledige controle van het teruggegeven schema en de inhoud te nemen.

De Standaard Renderers van de Diensten van de inhoud vullen het hiaat tussen uit-van-de-doos het Verspreiden Gebreken en de Ontwikkeling van de Douane die aanpassing en controle van vele aspecten van de teruggegeven inhoud zonder ontwikkeling toestaat.

Het volgende diagram toont het teruggeven van inhoudsdiensten.

![chlimage_1-15](assets/chlimage_1-15.png)

## JSON aanvragen {#requesting-json}

Gebruiken **&lt;resource.caas span=&quot;&quot; id=&quot;1&quot; translate=&quot;no&quot; />.[&lt;export-config span=&quot;&quot; id=&quot;0&quot; translate=&quot;no&quot; />.][&lt;export-config span=&quot;&quot; id=&quot;0&quot; translate=&quot;no&quot; />.json** om JSON aan te vragen.]

<table>
 <tbody>
  <tr>
   <td>BRON</td>
   <td>een entiteitsmiddel onder /content/entities<br /> of <br /> een inhoudsbron onder /content</td>
  </tr>
  <tr>
   <td>EXPORTCONFIG</td>
   <td><p><strong>OPTIONEEL</strong><br /> </p> <p>een exportconfiguratie gevonden onder /apps/mobileapps/caas/exportConfigs/EXPORT-CONFIG<br /> <br /> Indien weggelaten, wordt de standaardexportconfiguratie toegepast </p> </td>
  </tr>
  <tr>
   <td>DEPTH-INT</td>
   <td><strong>OPTIONEEL</strong><br /> <br /> diepteherhaling voor renderen van kinderen zoals gebruikt bij rendering van elementen</td>
  </tr>
 </tbody>
</table>

## Exportconfiguraties maken {#creating-export-configs}

U kunt exportconfiguraties maken om JSON-rendering aan te passen.

U kunt een configuratieknoop tot stand brengen onder */apps/mobileapps/caas/exportConfigs.*

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
   <td>String[]</td>
   <td>alles opnemen</td>
   <td>sling:resourceType</td>
   <td>uitsluiten, details voor knooppunten met opgegeven volgorde:resourceType van JSON-export</td>
  </tr>
  <tr>
   <td>excludeComponents</td>
   <td>String[]</td>
   <td>niets uitsluiten</td>
   <td>sling:resourceType</td>
   <td>alleen details opnemen voor knooppunten met opgegeven afstand:resourceType van JSON-export</td>
  </tr>
  <tr>
   <td>excludePropertyPrefixes</td>
   <td>String[]</td>
   <td>niets uitsluiten</td>
   <td>Voorvoegsels voor eigenschappen</td>
   <td>eigenschappen die beginnen met opgegeven voorvoegsels, uitsluiten van JSON-export</td>
  </tr>
  <tr>
   <td>excludeProperties</td>
   <td>String[]</td>
   <td>niets uitsluiten</td>
   <td>Namen van eigenschappen</td>
   <td>opgegeven eigenschappen uitsluiten van JSON-export</td>
  </tr>
  <tr>
   <td>includeProperties</td>
   <td>String[]</td>
   <td>alles opnemen</td>
   <td>Namen van eigenschappen</td>
   <td><p>if excludePropertyPrefixes set<br /> dit omvat opgegeven eigenschappen, ook al komen deze overeen met het voorvoegsel dat wordt uitgesloten,</p> <p>else (eigenschappen uitsluiten genegeerd) bevatten alleen deze eigenschappen</p> </td>
  </tr>
  <tr>
   <td>includeChildren</td>
   <td>String[]</td>
   <td>alles opnemen</td>
   <td>onderliggende namen</td>
   <td>gespecificeerde kinderen van de uitvoer van JSON uitsluiten</td>
  </tr>
  <tr>
   <td>excludeChildren</td>
   <td>String[]<br /> <br /> </td>
   <td>niets uitsluiten</td>
   <td>onderliggende namen</td>
   <td>alleen opgegeven onderliggende items opnemen van JSON-export, andere uitsluiten</td>
  </tr>
  <tr>
   <td>renameProperties</td>
   <td>String[]<br /> <br /> </td>
   <td>naam wijzigen</td>
   <td>&lt;actual_property_name&gt;,&lt;replacement_property_name&gt;</td>
   <td>naam van eigenschappen wijzigen met vervangingen</td>
  </tr>
 </tbody>
</table>

### Exportoverschrijvingen van het type resource {#resource-type-export-overrides}

Een configuratieknooppunt maken onder */apps/mobileapps/caas/exportConfigs.*

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
   <td>String[] </td>
   <td>-</td>
   <td>sling:resourceType</td>
   <td>Voor de volgende het rangschikken middeltypes, keer niet de standaardUitvoer van CaaS.<br /> Retourneer een klant json-export door de resource als te renderen;<br /> &lt;resource&gt;.&lt;selector_to_inc&gt;.json </td>
  </tr>
 </tbody>
</table>

### Bestaande Content Services Exporteren Configs {#existing-content-services-export-configs}

De Diensten van de inhoud omvat twee uitvoerconfiguraties:

* default (geen config gespecificeerd)
* pagina (om sitepagina&#39;s te renderen)

#### Standaard exportconfiguratie {#default-export-configuration}

De standaard de uitvoerconfiguratie van de Diensten van de inhoud wordt toegepast als een config in gevraagde URI wordt gespecificeerd.

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
   <td>jcr:tekst,tekst<br /> jcr:title,title<br /> jcr:description<br /> jcr:lastModified,lastModified<br /> cq:tags,tags<br /> cq:lastModified,lastModified</td>
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
   <td>basis/componenten/afbeelding<br /> wcm/stichting/componenten/afbeelding<br /> mobileapps/caas/components/data/contentReference<br /> mobileapps/caas/components/data/assetlist</td>
  </tr>
 </tbody>
</table>

#### Configuratie pagina exporteren {#page-export-configuration}

Deze configuratie breidt het gebrek uit om groeperende kinderen onder een kindknoop te omvatten.

&lt;site_page>.caas.page[.&lt;depth-int>].json

### Aanvullende bronnen {#additional-resources}

Zie hieronder de middelen om over extra onderwerpen in de Diensten van de Inhoud te leren:

* [Modellen ontwikkelen](/help/mobile/administer-mobile-apps.md)
* [Services voor het ontwerpen van inhoud](/help/mobile/develop-content-as-a-service.md)
* [Inhoudsservices beheren](/help/mobile/developing-content-services.md)
