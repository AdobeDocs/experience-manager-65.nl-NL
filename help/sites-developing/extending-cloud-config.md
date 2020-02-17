---
title: Cloud Service Configurations
seo-title: Cloud Service Configurations
description: U kunt de bestaande instanties uitbreiden om uw eigen configuraties te maken
seo-description: U kunt de bestaande instanties uitbreiden om uw eigen configuraties te maken
uuid: 9d20c3a4-2a12-4d3c-80c3-fcac3137a675
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: d25c03bf-6eaa-45f4-ab60-298865935a62
translation-type: tm+mt
source-git-commit: 5128a08d4db21cda821de0698b0ac63ceed24379

---


# Cloud Service Configurations{#cloud-service-configurations}

Configuraties zijn ontworpen om de logica en structuur te bieden voor het opslaan van serviceconfiguraties.

U kunt de bestaande instanties uitbreiden om uw eigen configuraties tot stand te brengen.

## Concepten {#concepts}

De beginselen die bij de ontwikkeling van de configuraties worden gebruikt, zijn gebaseerd op de volgende concepten:

* Services/adapters worden gebruikt om de configuratie(s) op te halen.
* Configuraties (bijvoorbeeld eigenschappen/alinea&#39;s) worden overgenomen van de bovenliggende elementen.
* Verwezen van analytische node(s) per pad.
* Gemakkelijk uitbreidbaar.
* Biedt de flexibiliteit om rekening te houden met complexere configuraties, zoals [Adobe Analytics](/help/sites-administering/marketing-cloud.md#integrating-with-adobe-analytics).
* Ondersteuning voor afhankelijkheden (voor [Adobe Analytics](/help/sites-administering/marketing-cloud.md#integrating-with-adobe-analytics) -plug-ins is bijvoorbeeld een configuratie voor [Adobe Analytics](/help/sites-administering/marketing-cloud.md#integrating-with-adobe-analytics) vereist).

## Structuur {#structure}

Het basispad van de configuraties is:

`/etc/cloudservices`.

Voor elk type van configuratie zullen een malplaatje en een component worden verstrekt.Dit maakt het mogelijk om configuratiemalplaatjes te hebben die aan de meeste behoeften kunnen voldoen nadat wordt aangepast.

Om een configuratie voor de nieuwe diensten te verstrekken moet u:

* een servicepagina maken in

   `/etc/cloudservices`

* in dit verband :

   * een configuratiesjabloon
   * een configuratiecomponent

De sjabloon en de component moeten de sjabloon overnemen `sling:resourceSuperType` van de basissjabloon:

`cq/cloudserviceconfigs/templates/configpage`

of basiscomponent

`cq/cloudserviceconfigs/components/configpage`

De dienstverlener zou ook de de dienstpagina moeten verstrekken:

`/etc/cloudservices/<service-name>`

### Sjabloonmodel {#template}

Uw sjabloon breidt de basissjabloon uit:

`cq/cloudserviceconfigs/templates/configpage`

en definieert u een `resourceType` element dat naar de aangepaste component wijst.

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

### Componenten {#components}

De component moet de basiscomponent uitbreiden:

`cq/cloudserviceconfigs/templates/configpage`

```xml
/libs/cq/analytics/components/sitecatalystpage

/libs/cq/analytics/components/generictrackerpage
```

Nadat u de sjabloon en de component hebt ingesteld, kunt u de configuratie toevoegen door subpagina&#39;s toe te voegen onder:

`/etc/cloudservices/<service-name>`

### Inhoudsmodel {#content-model}

Het inhoudsmodel wordt opgeslagen als `cq:Page` onder:

`/etc/cloudservices/<service-name>(/*)`

```xml
/etc/cloudservices
/etc/cloudservices/service-name
/etc/cloudservices/service-name/config
/etc/cloudservices/service-name/config/inherited-config
```

De configuraties worden opgeslagen onder het subknooppunt `jcr:content`.

* Vaste eigenschappen, die in een dialoogvenster zijn gedefinieerd, moeten `jcr:node` rechtstreeks in het dialoogvenster worden opgeslagen.
* Dynamische elementen (met `parsys` of `iparsys`) gebruiken een subknooppunt om de componentgegevens op te slaan.

```xml
/etc/cloudservices/service/config/jcr:content as nt:unstructured
propertyname
*
par/component/ as cq:Component
propertyname
*
```

### API {#api}

Zie [com.day.cq.wcm.webservicesupport](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/webservicesupport/package-summary.html)voor documentatie over de API.

### AEM-integratie {#aem-integration}

De beschikbare services worden vermeld op het tabblad **Cloud Services** van het dialoogvenster **Pagina-eigenschappen** (van elke pagina die overerft van `foundation/components/page` of `wcm/mobile/components/page`).

Het tabblad bevat ook:

* een koppeling naar de locatie waar u de service kunt inschakelen
* Kies een configuratie (subknooppunt van de service) in een padveld

#### Wachtwoordversleuteling {#password-encryption}

Wanneer het opslaan van gebruikersgeloofsbrieven voor de dienst, zouden alle wachtwoorden moeten worden gecodeerd.

U kunt dit bereiken door een verborgen formulierveld toe te voegen. Dit veld moet de annotatie `@Encrypted` in de naam van de eigenschap hebben. Voor het `password` veld wordt de naam als volgt geschreven:

`password@Encrypted`

De eigenschap wordt vervolgens automatisch gecodeerd (met de `CryptoSupport` service) door de `EncryptionPostProcessor`instantie.

>[!NOTE]
>
>Dit is vergelijkbaar met de standaardannotaties ` [SlingPostServlet](https://sling.apache.org/site/manipulating-content-the-slingpostservlet-servletspost.html)` .

>[!NOTE]
>
>Standaard worden `EcryptionPostProcessor` alleen `POST` verzoeken versleuteld die aan zijn gedaan `/etc/cloudservices`.

#### Aanvullende eigenschappen voor servicepagina jcr:inhoudsknooppunten {#additional-properties-for-service-page-jcr-content-nodes}

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschap</strong></td>
   <td><strong>Beschrijving</strong></td>
  </tr>
  <tr>
   <td>componentReference</td>
   <td>Verwijzingspad naar een component die automatisch op de pagina moet worden opgenomen.<br /> Dit wordt gebruikt voor extra functionaliteit en JS inbegrepen.<br /> Dit omvat de component op de pagina waar<br /> <code> cq/cloudserviceconfigs/components/servicecomponents</code><br /> is inbegrepen (normaal vóór de <code>body</code> markering).<br /> Voor het geval dat Analytics en Target dit gebruiken om extra functionaliteit op te nemen, zoals JavaScript-aanroepen om het gedrag van bezoekers te volgen.</td>
  </tr>
  <tr>
   <td>beschrijving</td>
   <td>Korte beschrijving van de dienst.<br /> </td>
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
   <td>Zichtbaarheid in dialoogvenster Pagina-eigenschappen standaard zichtbaar (optioneel)</td>
  </tr>
 </tbody>
</table>

### Gevallen gebruiken {#use-cases}

Deze services worden standaard geleverd:

* [Trackerfragmenten](/help/sites-administering/external-providers.md) (Google, WebTrends, enz.)
* [Adobe Analytics](/help/sites-administering/marketing-cloud.md#integrating-with-adobe-analytics)
* [&amp;Doel testen](/help/sites-administering/marketing-cloud.md#integrating-with-adobe-target)
* [&amp;Zoeken bevorderen](/help/sites-administering/marketing-cloud.md#integrating-with-search-promote)
* [Scene7](/help/sites-administering/marketing-cloud.md#integrating-with-scene)

>[!NOTE]
>
>Zie ook [Een aangepaste Cloud-service](/help/sites-developing/extending-cloud-config-custom-cloud.md)maken.

