---
title: URL's extern maken
description: De Externalzer is een dienst OSGI die u programmatically een middelweg in een externe en absolute URL laat omzetten
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
docset: aem65
exl-id: 971d6c25-1fbe-4c07-944e-be6b97a59922
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# URL&#39;s extern maken{#externalizing-urls}

In Adobe Experience Manager (AEM), is **externalizer** de dienst OSGI die u programmatically een middelweg (bijvoorbeeld, `/path/to/my/page`) in een externe en absolute URL (bijvoorbeeld, `https://www.mycompany.com/path/to/my/page`) laat omzetten door de weg met pre-gevormde DNS te bevestigen.

Omdat een instantie zijn uiterlijk zichtbare URL niet kan kennen als het achter een Weblaag loopt, en omdat soms een verbinding buiten het verzoekwerkingsgebied moet worden gecreeerd, verstrekt deze dienst een centrale plaats om die externe URLs te vormen en hen te bouwen.

Deze pagina verklaart hoe te om de **dienst te vormen Externalzer** en hoe te om het te gebruiken. Voor meer details, zie [&#x200B; JavaDocs &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/commons/Externalizer.html).

## De service ExternalAlizer configureren {#configuring-the-externalizer-service}

De **ExternalAlizer** dienst laat u veelvoudige domeinen centraal bepalen die aan programmatically voorvoegselmiddelwegen kunnen worden gebruikt. Elk domein wordt geïdentificeerd door een unieke naam die wordt gebruikt om programmatically naar het domein te verwijzen.

Om een domeinafbeelding voor de **Externalalizer** dienst te bepalen:

1. Navigeer aan de configuratiemanager via **Hulpmiddelen**, dan **Console van het Web**, of ga binnen:

   `https://<host>:<port>/system/console/configMgr`

1. Klik **Dag CQ Verbinding Externalzer** om de doos van de configuratiedialoog te openen.

   >[!NOTE]
   >
   >De directe koppeling naar de configuratie is `https://<host>:<port>/system/console/configMgr/com.day.cq.commons.impl.ExternalizerImpl`

   ![&#x200B; aem-externalizer-01 &#x200B;](assets/aem-externalizer-01.png)

1. Bepaal de afbeelding van a **Domeinen**: een afbeelding bestaat uit een unieke naam die in de code kan worden gebruikt om naar het domein, een ruimte, en het domein te verwijzen:

   `<unique-name> [scheme://]server[:port][/contextpath]`

   Waarbij:

   * **regeling** is http of https, maar kan ook ftp, etc. zijn.

      * gebruik https om https-koppelingen af te dwingen, indien gewenst
      * wordt gebruikt als de clientcode het schema niet overschrijft wanneer wordt gevraagd om externalisatie van een URL.

   * **server** is de gastheernaam (kan een domeinnaam of ip adres zijn).
   * **haven** (facultatief) is het havenaantal.
   * **contextpath** (facultatief) wordt slechts geplaatst als AEM als webapp onder een verschillende contextweg geïnstalleerd is.

   Bijvoorbeeld: `production https://my.production.instance`

   De volgende toewijzingsnamen zijn vooraf gedefinieerd en moeten worden ingesteld omdat AEM op deze namen vertrouwt:

   * `local` - de lokale instantie
   * `author` - de DNS van het ontwerpsysteem
   * `publish` - de openbare naar voren gerichte website DNS

   >[!NOTE]
   >
   >Met een aangepaste configuratie kunt u een categorie toevoegen, zoals `production` , `staging` of zelfs externe niet-AEM systemen, zoals `my-internal-webservice` . Het is handig om hardcodering van dergelijke URL&#39;s op verschillende plaatsen in de codebase van een project te voorkomen.

1. Klik **sparen** om uw veranderingen te bewaren.

>[!NOTE]
>
>De Adobe adviseert dat u [&#x200B; de configuratie aan de bewaarplaats &#x200B;](/help/sites-deploying/configuring.md#addinganewconfigurationtotherepository) toevoegt.

### De service ExternalAlizer gebruiken {#using-the-externalizer-service}

Deze sectie toont een paar voorbeelden van hoe de **&#x200B;**&#x200B;dienst Externalzer kan worden gebruikt:

1. **om de dienst Externalzer in JSP te krijgen:**

   ```java
   Externalizer externalizer = resourceResolver.adaptTo(Externalizer.class);
   ```

1. **om een weg met het &quot;te externaliseren&quot;domein:**

   ```java
   String myExternalizedUrl = externalizer.publishLink(resolver, "/my/page") + ".html";
   ```

   Het veronderstellen van de domeinafbeelding:

   * `publish https://www.website.com`

   `myExternalizedUrl` eindigt omhoog met de waarde:

   * `https://www.website.com/contextpath/my/page.html`

1. **om een weg met het &quot;auteur&quot;domein externaliseren:**

   ```java
   String myExternalizedUrl = externalizer.authorLink(resolver, "/my/page") + ".html";
   ```

   Het veronderstellen van de domeinafbeelding:

   * `author https://author.website.com`

   `myExternalizedUrl` eindigt omhoog met de waarde:

   * `https://author.website.com/contextpath/my/page.html`

1. **om een weg met het &quot;lokale&quot;domein externaliseren:**

   ```java
   String myExternalizedUrl = externalizer.externalLink(resolver, Externalizer.LOCAL, "/my/page") + ".html";
   ```

   Het veronderstellen van de domeinafbeelding:

   * `local https://publish-3.internal`

   `myExternalizedUrl` eindigt omhoog met de waarde:

   * `https://publish-3.internal/contextpath/my/page.html`

1. U kunt meer voorbeelden in [&#x200B; JavaDocs &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/commons/Externalizer.html) vinden.
