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
* Heeft de flexibiliteit om voor complexere configuraties, zoals te behandelen [Adobe Analytics](/help/sites-administering/marketing-cloud.md#integrating-with-adobe-analytics).
* Ondersteuning voor afhankelijkheden (bijvoorbeeld [Adobe Analytics](/help/sites-administering/marketing-cloud.md#integrating-with-adobe-analytics) plug-ins hebben een [Adobe Analytics](/help/sites-administering/marketing-cloud.md#integrating-with-adobe-analytics) configuratie).

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

De sjabloon en component moeten de `sling:resourceSuperType` uit het basissjabloon:

`cq/cloudserviceconfigs/templates/configpage`

of basiscomponent

`cq/cloudserviceconfigs/components/configpage`

De dienstverlener zou ook de de dienstpagina moeten verstrekken:

`/etc/cloudservices/<service-name>`

### Sjabloon {#template}

Uw sjabloon breidt de basissjabloon uit:

`cq/cloudserviceconfigs/templates/configpage`

En definieer een `resourceType` dat naar de aangepaste component wijst.

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

De configuraties worden opgeslagen onder het subknooppunt `jcr:content`.

* Vaste eigenschappen, gedefinieerd in een dialoogvenster, moeten worden opgeslagen op het tabblad `jcr:node` rechtstreeks.
* Dynamische elementen (gebruiken `parsys` of `iparsys`) gebruikt u een subknooppunt om de componentgegevens op te slaan.

```xml
/etc/cloudservices/service/config/jcr:content as nt:unstructured
propertyname
*
par/component/ as cq:Component
propertyname
*
```

### API {#api}

Zie voor documentatie over de API [com.day.cq.wcm.webservicesSupport](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/wcm/webservicesupport/package-summary.html).

### AEM integratie {#aem-integration}

Beschikbare services worden vermeld in de **Cloud Servicen** tabblad van het **Pagina-eigenschappen** (van elke pagina die overerft van `foundation/components/page` of `wcm/mobile/components/page`).

Het tabblad bevat ook:

* een koppeling naar de locatie waar u de service kunt inschakelen
* Kies een configuratie (subknooppunt van de service) in een padveld

#### Wachtwoordversleuteling {#password-encryption}

Wanneer het opslaan van gebruikersgeloofsbrieven voor de dienst, zouden alle wachtwoorden moeten worden gecodeerd.

U kunt dit bereiken door een verborgen formulierveld toe te voegen. Dit veld moet de annotatie hebben `@Encrypted` in de eigenschapsnaam, dat wil zeggen, voor de `password` in het veld zou de naam worden geschreven als:

`password@Encrypted`

De eigenschap wordt dan automatisch gecodeerd (met de opdracht `CryptoSupport` door de `EncryptionPostProcessor`.

>[!NOTE]
>
>Dit is vergelijkbaar met de standaard ` [SlingPostServlet](https://sling.apache.org/site/manipulating-content-the-slingpostservlet-servletspost.html)` annotaties.

>[!NOTE]
>
>Standaard worden de `EcryptionPostProcessor` alleen versleutelen `POST` verzoeken aan `/etc/cloudservices`.

#### Aanvullende eigenschappen voor servicepagina jcr:inhoudsknooppunten {#additional-properties-for-service-page-jcr-content-nodes}

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschap</strong></td>
   <td><strong>Beschrijving</strong></td>
  </tr>
  <tr>
   <td>componentReference</td>
   <td>Verwijzingspad naar een component die automatisch op de pagina moet worden opgenomen.<br /> Dit wordt gebruikt voor extra functionaliteit en JS inbegrepen.<br /> Dit omvat de component op de pagina waar<br /> <code> cq/cloudserviceconfigs/components/servicecomponents</code><br /> wordt opgenomen (gewoonlijk vóór de <code>body</code> -tag).<br /> In het geval van Adobe Analytics en Adobe Target gebruiken wij dit om extra functionaliteit, zoals JavaScript vraag te omvatten om bezoekersgedrag te volgen.</td>
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
   <td>Zichtbaarheid in dialoogvenster Pagina-eigenschappen; standaard zichtbaar (optioneel)</td>
  </tr>
 </tbody>
</table>

### Gevallen gebruiken {#use-cases}

Deze services worden standaard geleverd:

* [Fragmenten voor Beheer](/help/sites-administering/external-providers.md) (Google, WebTrends, enzovoort)
* [Adobe Analytics](/help/sites-administering/marketing-cloud.md#integrating-with-adobe-analytics)
* [&amp;Doel testen](/help/sites-administering/marketing-cloud.md#integrating-with-adobe-target)
<!-- Search&Promote is end of life as of September 1, 2022 * [Search&Promote](/help/sites-administering/marketing-cloud.md#integrating-with-search-promote) -->
* [Dynamic Media](/help/sites-administering/marketing-cloud.md#integrating-with-scene)

>[!NOTE]
>
>Zie ook [Een aangepaste Cloud Service maken](/help/sites-developing/extending-cloud-config-custom-cloud.md).
