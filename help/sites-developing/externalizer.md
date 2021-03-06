---
title: URL's extern maken
seo-title: URL's extern maken
description: De Externalzer is de dienst OSGI die u toestaat om een middelweg in een externe en absolute URL programmatically om te zetten
seo-description: De Externalzer is de dienst OSGI die u toestaat om een middelweg in een externe en absolute URL programmatically om te zetten
uuid: 65bcc352-fc8c-4aa0-82fb-1321a035602d
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
discoiquuid: 938469ad-f466-42f4-8b6f-bfc060ae2785
docset: aem65
translation-type: tm+mt
source-git-commit: ec528e115f3e050e4124b5c232063721eaed8df5
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 0%

---


# URL&#39;s extern maken{#externalizing-urls}

In AEM, is **ExternalAlizer** de dienst OSGI die u toestaat om een middelweg programmatically om te zetten (b.v. `/path/to/my/page`) in een externe en absolute URL (bijvoorbeeld `https://www.mycompany.com/path/to/my/page`) door de weg met vooraf gevormde DNS te bevestigen.

Omdat een instantie zijn uiterlijk zichtbare URL niet kan kennen als het achter een Weblaag loopt, en omdat soms een verbinding buiten het verzoekwerkingsgebied moet worden gecreeerd, verstrekt deze dienst een centrale plaats om die externe URLs te vormen en hen te bouwen.

Deze pagina verklaart hoe te om de **Externalzer** dienst te vormen en hoe te om het te gebruiken. Raadpleeg [Javadocs](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/Externalizer.html) voor meer informatie.

## De service ExternalAlizer {#configuring-the-externalizer-service} configureren

Met de service **ExternalAlizer** kunt u meerdere domeinen centraal definiëren die kunnen worden gebruikt om programmatisch een voorvoegsel voor bronnenpaden toe te voegen. Elk domein wordt geïdentificeerd door een unieke naam die wordt gebruikt om programmatically naar het domein te verwijzen.

Een domeinafbeelding definiëren voor de service **Externalalizer**:

1. Navigeer naar de configuratiemanager via **Tools**, dan **Webconsole**, of ga in:

   `https://<host>:<port>/system/console/configMgr`

1. Klik **De Verbinding van CQ van de Dag uiterlijk** om de doos van de configuratiedialoog te openen.

   >[!NOTE]
   >
   >De directe verbinding aan de configuratie is `https://<host>:<port>/system/console/configMgr/com.day.cq.commons.impl.ExternalizerImpl`

   ![aem-externalizer-01](assets/aem-externalizer-01.png)

1. Definieer een **Domeinen**-toewijzing: een toewijzing bestaat uit een unieke naam die in de code kan worden gebruikt om naar het domein, een ruimte en het domein te verwijzen:

   `<unique-name> [scheme://]server[:port][/contextpath]`

   Waar:

   * **** schema&#39;s zijn meestal http of https, maar ook ftp, enz.

      * Gebruik https om https-koppelingen desgewenst te forceren
      * wordt gebruikt als de clientcode het schema niet overschrijft wanneer wordt gevraagd om externalisatie van een URL.
   * **De** server is de hostnaam (kan een domeinnaam of ip-adres zijn).
   * **port**  (optioneel) is het poortnummer.
   * **contextpath**  (optioneel) wordt alleen ingesteld als AEM is geïnstalleerd als een webapp onder een ander contextpad.

   Bijvoorbeeld: `production https://my.production.instance`

   De volgende toewijzingsnamen zijn vooraf gedefinieerd en moeten altijd worden ingesteld op basis van AEM:

   * `local` - de lokale instantie
   * `author` - DNS van het ontwerpsysteem
   * `publish` - het publiek met de website DNS geconfronteerd

   >[!NOTE]
   >
   >Met een aangepaste configuratie kunt u een nieuwe categorie toevoegen, zoals `production`, `staging` of zelfs externe niet-AEM systemen zoals `my-internal-webservice`. Het is handig om hardcodering van dergelijke URL&#39;s op verschillende plaatsen in de codebase van een project te voorkomen.

1. Klik **Opslaan** om uw wijzigingen op te slaan.

>[!NOTE]
>
>Adobe raadt aan dat u [de configuratie toevoegt aan de gegevensopslagruimte](/help/sites-deploying/configuring.md#addinganewconfigurationtotherepository).

### De service ExternalAlizer gebruiken {#using-the-externalizer-service}

Deze sectie toont een paar voorbeelden van hoe de **Externalzer** dienst kan worden gebruikt:

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


1. U kunt meer voorbeelden in [Javadocs](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/Externalizer.html) vinden.
