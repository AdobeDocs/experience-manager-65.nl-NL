---
title: Configuraties van Cloud Servicen
description: U kunt de bestaande instanties uitbreiden om uw eigen configuraties te maken
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
exl-id: 20a19ee5-7113-4aca-934a-a42c415a8d93
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '552'
ht-degree: 0%

---

# Configuraties van Cloud Servicen{#cloud-service-configurations}

Configuraties zijn ontworpen om de logica en structuur te bieden voor het opslaan van serviceconfiguraties.

U kunt de bestaande instanties uitbreiden om uw eigen configuraties tot stand te brengen.

## Concepten {#concepts}

De beginselen die bij de ontwikkeling van de configuraties worden gebruikt, zijn gebaseerd op de volgende concepten:

* De diensten/de Adapters worden gebruikt om de configuraties terug te winnen.
* Configuraties (bijvoorbeeld eigenschappen/alinea&#39;s) worden overgeërfd van de bovenliggende elementen.
* Verwezen van analytische knooppunten naar pad.
* Gemakkelijk uitbreidbaar.
* Heeft de flexibiliteit om voor complexere configuraties, zoals [&#x200B; Adobe Analytics &#x200B;](/help/sites-administering/marketing-cloud.md#integrating-with-adobe-analytics) te behandelen.
* Steun voor gebiedsdelen (bijvoorbeeld, [&#x200B; Adobe Analytics &#x200B;](/help/sites-administering/marketing-cloud.md#integrating-with-adobe-analytics) plugins vereist een [&#x200B; Adobe Analytics &#x200B;](/help/sites-administering/marketing-cloud.md#integrating-with-adobe-analytics) configuratie).

## Structuur {#structure}

Het basispad van de configuraties is:

`/etc/cloudservices`.

Voor elk type configuratie, worden een malplaatje en een component verstrekt. Dit maakt het mogelijk om configuratiesjablonen te hebben die aan de meeste behoeften kunnen voldoen nadat ze zijn aangepast.

Om een configuratie voor de nieuwe diensten te verstrekken, doe het volgende:

* Servicepagina maken in

  `/etc/cloudservices`

* Onder deze regel:

   * een configuratiesjabloon
   * een configuratiecomponent

De sjabloon en component moeten de `sling:resourceSuperType` overnemen van de basissjabloon:

`cq/cloudserviceconfigs/templates/configpage`

of basiscomponent

`cq/cloudserviceconfigs/components/configpage`

De dienstverlener zou ook de de dienstpagina moeten verstrekken:

`/etc/cloudservices/<service-name>`

### Sjabloon {#template}

Uw sjabloon breidt de basissjabloon uit:

`cq/cloudserviceconfigs/templates/configpage`

Definieer een `resourceType` die naar de aangepaste component wijst.

```xml
/libs/cq/analytics/templates/sitecatalyst
sling:resourceSuperType = cq/cloudserviceconfigs/templates/configpage
allowedChildren = /libs/cq/analytics/templates/sitecatalyst
allowedPaths = /etc/cloudservices/analytics/*, /etc/cloudservices/analytics/.*
componentReference = cq/analytics/components/sitecatalyst
jcr:content/
cq:designPath = /etc/designs/cloudservices
sling:resourceType = cq/analytics/components/sitecatalystpage

/libs/cq/analytics/templates/generictracker
sling:resourceSuperType = cq/cloudservices/templates/configpage
allowedChildren = /libs/cq/analytics/templates/generictracker
allowedPaths = /etc/cloudservices/analytics/*, /etc/cloudservices/analytics/.*
jcr:content/
cq:designPath = /etc/designs/cloudservices
sling:resourceType = cq/analytics/components/generictrackerpage
```

### Onderdelen {#components}

De component moet de basiscomponent uitbreiden:

`cq/cloudserviceconfigs/templates/configpage`

```xml
/libs/cq/analytics/components/sitecatalystpage

/libs/cq/analytics/components/generictrackerpage
```

Nadat u de sjabloon en de component hebt ingesteld, kunt u de configuratie toevoegen door subpagina&#39;s toe te voegen onder:

`/etc/cloudservices/<service-name>`

### Content Model {#content-model}

Het inhoudsmodel wordt opgeslagen als `cq:Page` onder:

`/etc/cloudservices/<service-name>(/*)`

```xml
/etc/cloudservices
/etc/cloudservices/service-name
/etc/cloudservices/service-name/config
/etc/cloudservices/service-name/config/inherited-config
```

De configuraties worden opgeslagen onder het subknooppunt `jcr:content` .

* Vaste eigenschappen, die in een dialoogvenster zijn gedefinieerd, moeten rechtstreeks in de `jcr:node` worden opgeslagen.
* Dynamische elementen (met `parsys` of `iparsys` ) gebruiken een subknooppunt om de componentgegevens op te slaan.

```xml
/etc/cloudservices/service/config/jcr:content as nt:unstructured
propertyname
*
par/component/ as cq:Component
propertyname
*
```

### API {#api}

Voor verwijzingsdocumentatie op API, zie [&#x200B; com.day.cq.wcm.webservicesupport &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/wcm/webservicesupport/package-summary.html).

### AEM integratie {#aem-integration}

De beschikbare diensten zijn vermeld in het **Cloud Servicen** lusje van de **dialoog van de Eigenschappen van de Pagina** (van om het even welke pagina die van `foundation/components/page` of `wcm/mobile/components/page` erft).

Het tabblad bevat ook:

* een koppeling naar de locatie waar u de service kunt inschakelen
* Kies een configuratie (subknooppunt van de service) in een padveld

#### Wachtwoordversleuteling {#password-encryption}

Wanneer het opslaan van gebruikersgeloofsbrieven voor de dienst, zouden alle wachtwoorden moeten worden gecodeerd.

U kunt dit bereiken door een verborgen formulierveld toe te voegen. Dit veld moet de annotatie `@Encrypted` hebben in de eigenschapsnaam. Voor het veld `password` wordt de naam geschreven als:

`password@Encrypted`

De eigenschap wordt vervolgens automatisch gecodeerd (met de service `CryptoSupport` ) door de `EncryptionPostProcessor` .

>[!NOTE]
>
>Dit is vergelijkbaar met de standaard ` [SlingPostServlet](https://sling.apache.org/site/manipulating-content-the-slingpostservlet-servletspost.html)` -annotaties.

>[!NOTE]
>
>Standaard versleutelen de `EcryptionPostProcessor` alleen `POST` -verzoeken die aan `/etc/cloudservices` zijn gedaan.

#### Aanvullende eigenschappen voor servicepagina jcr:inhoudsknooppunten {#additional-properties-for-service-page-jcr-content-nodes}

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschap</strong></td>
   <td><strong>Beschrijving</strong></td>
  </tr>
  <tr>
   <td>componentReference</td>
   <td>Verwijzingspad naar een component die automatisch op de pagina moet worden opgenomen.<br /> Deze wordt gebruikt voor extra functionaliteit en JS-insluitingen.<br /> Dit omvat de component op de pagina waar <br /> <code> cq/cloudserviceconfigs/components/servicecomponents</code><br /> is opgenomen (normaal vóór de <code>body</code> -tag).<br /> Voor het geval dat Adobe Analytics en Adobe Target dit doen, gebruiken wij dit om extra functionaliteit, zoals de vraag van JavaScript te omvatten om bezoekersgedrag te volgen.</td>
  </tr>
  <tr>
   <td>beschrijving</td>
   <td>Korte beschrijving van de service.<br /> </td>
  </tr>
  <tr>
   <td>descriptionExtended</td>
   <td>Uitgebreide beschrijving van de service.</td>
  </tr>
  <tr>
   <td>rangschikking</td>
   <td>Servicerangschikking voor gebruik in aanbiedingen.</td>
  </tr>
  <tr>
   <td>selectableChildren</td>
   <td>Filter voor het weergeven van configuraties in het dialoogvenster Pagina-eigenschappen.</td>
  </tr>
  <tr>
   <td>serviceUrl</td>
   <td>URL naar servicewebsite.</td>
  </tr>
  <tr>
   <td>serviceUrlLabel</td>
   <td>Label voor service-URL.</td>
  </tr>
  <tr>
   <td>miniatuurPath</td>
   <td>Pad naar miniatuur voor service.</td>
  </tr>
  <tr>
   <td>visible</td>
   <td>Zichtbaarheid in dialoogvenster Pagina-eigenschappen; standaard zichtbaar (optioneel)</td>
  </tr>
 </tbody>
</table>

### Gevallen gebruiken {#use-cases}

Deze services worden standaard geleverd:

* [&#x200B; de Fragmenten van de Beheer &#x200B;](/help/sites-administering/external-providers.md) (Google, WebTrends, etc.)
* [Adobe Analytics](/help/sites-administering/marketing-cloud.md#integrating-with-adobe-analytics)
* [&amp;Doel testen](/help/sites-administering/marketing-cloud.md#integrating-with-adobe-target)
<!-- Search&Promote is end of life as of September 1, 2022 * [Search&Promote](/help/sites-administering/marketing-cloud.md#integrating-with-search-promote) -->
* [Dynamic Media](/help/sites-administering/marketing-cloud.md#integrating-with-scene)

>[!NOTE]
>
>Zie ook [&#x200B; Creërend een Cloud Service van de Douane &#x200B;](/help/sites-developing/extending-cloud-config-custom-cloud.md).
