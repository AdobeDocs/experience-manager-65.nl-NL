---
title: URL's extern maken
seo-title: Externalizing URLs
description: De Externalzer is de dienst OSGI die u toestaat om een middelweg in een externe en absolute URL programmatically om te zetten
seo-description: The Externalizer is an OSGI service that allows you to programmatically transform a resource path into an external and absolute URL
uuid: 65bcc352-fc8c-4aa0-82fb-1321a035602d
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
discoiquuid: 938469ad-f466-42f4-8b6f-bfc060ae2785
docset: aem65
exl-id: 971d6c25-1fbe-4c07-944e-be6b97a59922
source-git-commit: 259f257964829b65bb71b5a46583997581a91a4e
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 0%

---

# URL&#39;s extern maken{#externalizing-urls}

In AEM **ExternalAlizer** is de dienst OSGI die u toestaat om een middelweg programmatically om te zetten (bijvoorbeeld `/path/to/my/page`) in een externe en absolute URL (bijvoorbeeld `https://www.mycompany.com/path/to/my/page`) door het pad vooraf te bevestigen met een vooraf geconfigureerde DNS.

Omdat een instantie zijn uiterlijk zichtbare URL niet kan kennen als het achter een Weblaag loopt, en omdat soms een verbinding buiten het verzoekwerkingsgebied moet worden gecreeerd, verstrekt deze dienst een centrale plaats om die externe URLs te vormen en hen te bouwen.

Deze pagina verklaart hoe te om te vormen **ExternalAlizer** en hoe deze te gebruiken. Raadpleeg voor meer informatie de [Javadocs](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/Externalizer.html).

## De service ExternalAlizer configureren {#configuring-the-externalizer-service}

De **ExternalAlizer** De dienst staat u toe om veelvoudige domeinen centraal te bepalen die aan programmatically prefixmiddelwegen kunnen worden gebruikt. Elk domein wordt geïdentificeerd door een unieke naam die wordt gebruikt om programmatically naar het domein te verwijzen.

Een domeintoewijzing definiëren voor de **ExternalAlizer** service:

1. Navigeer naar de configuratiemanager via **Gereedschappen** vervolgens **Webconsole** of voer in:

   `https://<host>:<port>/system/console/configMgr`

1. Klikken **Day CQ Link ExternalAlizer** om het dialoogvenster Configuratie te openen.

   >[!NOTE]
   >
   >De directe koppeling naar de configuratie is `https://<host>:<port>/system/console/configMgr/com.day.cq.commons.impl.ExternalizerImpl`

   ![aem-externalizer-01](assets/aem-externalizer-01.png)

1. Een **Domeinen** toewijzing: een toewijzing bestaat uit een unieke naam die in de code kan worden gebruikt om naar het domein, een ruimte en het domein te verwijzen:

   `<unique-name> [scheme://]server[:port][/contextpath]`

   Waar:

   * **regeling** is meestal http of https, maar kan ook ftp, enz. zijn.

      * Gebruik https om https-koppelingen desgewenst te forceren
      * wordt gebruikt als de clientcode het schema niet overschrijft wanneer wordt gevraagd om externalisatie van een URL.

   * **server** is de gastheernaam (kan een domeinnaam of ip adres zijn).
   * **poort** (optioneel) is het poortnummer.
   * **contextpad** (optioneel) wordt alleen ingesteld als AEM is geïnstalleerd als een webapp onder een ander contextpad.

   Bijvoorbeeld: `production https://my.production.instance`

   De volgende toewijzingsnamen zijn vooraf gedefinieerd en moeten altijd worden ingesteld op basis van AEM:

   * `local` - de lokale instantie
   * `author` - DNS van het ontwerpsysteem
   * `publish` - het publiek met de website DNS geconfronteerd

   >[!NOTE]
   >
   >Met een aangepaste configuratie kunt u een nieuwe categorie toevoegen, zoals `production`, `staging` of zelfs externe niet-AEM systemen zoals `my-internal-webservice`. Het is handig om hardcodering van dergelijke URL&#39;s op verschillende plaatsen in de codebase van een project te voorkomen.

1. Klikken **Opslaan** om uw wijzigingen op te slaan.

>[!NOTE]
>
>Adobe raadt u aan [de configuratie toevoegen aan de repository](/help/sites-deploying/configuring.md#addinganewconfigurationtotherepository).

### De service ExternalAlizer gebruiken {#using-the-externalizer-service}

In deze sectie worden enkele voorbeelden getoond van de manier waarop **ExternalAlizer** de dienst kan worden gebruikt:

1. **Om de dienst Externalzer in JSP te krijgen:**

   ```java
   Externalizer externalizer = resourceResolver.adaptTo(Externalizer.class);
   ```

1. **Een pad extern maken met het domein &#39;publish&#39;:**

   ```java
   String myExternalizedUrl = externalizer.publishLink(resolver, "/my/page") + ".html";
   ```

   Het veronderstellen van de domeinafbeelding:

   * `publish https://www.website.com`

   `myExternalizedUrl` eindigt omhoog met de waarde:

   * `https://www.website.com/contextpath/my/page.html`

1. **Een pad extern maken met het domein &#39;auteur&#39;:**

   ```java
   String myExternalizedUrl = externalizer.authorLink(resolver, "/my/page") + ".html";
   ```

   Het veronderstellen van de domeinafbeelding:

   * `author https://author.website.com`

   `myExternalizedUrl` eindigt omhoog met de waarde:

   * `https://author.website.com/contextpath/my/page.html`

1. **Een pad extern maken met het &#39;lokale&#39; domein:**

   ```java
   String myExternalizedUrl = externalizer.externalLink(resolver, Externalizer.LOCAL, "/my/page") + ".html";
   ```

   Het veronderstellen van de domeinafbeelding:

   * `local https://publish-3.internal`

   `myExternalizedUrl` eindigt omhoog met de waarde:

   * `https://publish-3.internal/contextpath/my/page.html`

1. Meer voorbeelden vindt u in het gedeelte [Javadocs](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/Externalizer.html).
