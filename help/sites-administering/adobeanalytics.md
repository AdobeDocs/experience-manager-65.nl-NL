---
title: Integreren met Adobe Analytics
seo-title: Integreren met Adobe Analytics
description: Leer hoe u AEM kunt integreren met Adobe Analytics.
seo-description: Leer hoe u AEM kunt integreren met Adobe Analytics.
uuid: d8548263-6ac5-45fb-8c70-52ecd4161bbb
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
discoiquuid: 444c522e-2f33-4f41-846c-8d317e799659
docset: aem65
translation-type: tm+mt
source-git-commit: ca25e66b280db479f69c487753a557b0240233da

---


# Integreren met Adobe Analytics{#integrating-with-adobe-analytics}

Door Adobe Analytics en AEM te integreren, kunt u uw webpaginageactiviteit volgen:

* Met een configuratie voor Adobe Analytics kan AEM verificatie uitvoeren met Adobe Analytics.
* Een framework geeft de gegevens aan die naar uw Adobe Analytics-rapportsuite worden verzonden.

De gegevens omvatten pagina- en gebruikersgegevens; bijvoorbeeld:

* gegevens die door AEM-componenten worden verzameld
* koppelingsklikken
* videogebruiksinformatie
* het aantal pagina-bezoeken van Adobe Analytics

Met de volgende pagina&#39;s kunt u de integratie configureren:

* [Verbinding maken met Adobe Analytics en frameworks maken](/help/sites-administering/adobeanalytics-connect.md)
* [Koppelingen bijhouden configureren voor Adobe Analytics](/help/sites-administering/adobeanalytics-link.md)
* [Componentgegevens toewijzen met de eigenschappen van Adobe Analytics](/help/sites-administering/adobeanalytics-mapping.md)
* [Video bijhouden configureren voor Adobe Analytics](/help/sites-administering/adobeanalytics-video.md)
* [Adobe-classificaties](/help/sites-administering/adobeanalytics-classifications.md)

U kunt de [Opt-in tovenaar](/help/sites-administering/opt-in.md) ook gebruiken om de integratie gemakkelijk uit te voeren.

>[!NOTE]
>
>Zie ook het &#39;Hoe kan ik?-artikel: AEM [integreren met Adobe Target en Adobe Analytics met DTM](https://helpx.adobe.com/experience-manager/using/integrate-digital-marketing-solutions.html).

## Aanvullende informatie {#further-information}

Zie:

* [De Adobe Analytics Integration](/help/sites-developing/extending-analytics.md) uitbreiden voor informatie over het ontwikkelen van componenten die gebruikersgegevens verzamelen en het Adobe Analytics-framework aanpassen.
* Het kennisbankartikel, [Adobe Analytics-integratie - Problemen](https://helpx.adobe.com/experience-manager/kb/sitecatalystintegrationtroubleshooting.html)oplossen, voor informatie over het oplossen van problemen met de integratie van Adobe Analytics.

>[!NOTE]
>
>Als u Adobe Analytics met een configuratie van de douanevolmacht gebruikt, moet u twee bundels [OSGi (bijvoorbeeld, met de console van het Web)](/help/sites-deploying/configuring-osgi.md) vormen die voor de de volmachtsconfiguraties van de Cliënt **van** Apache HTTP wordt vereist. Beide zijn vereist omdat sommige functies van AEM de 3.x API&#39;s gebruiken, terwijl andere de 4.x API&#39;s gebruiken. Configureren:
>
>* **Day Commons HTTP Client 3.1** om de 3.x API te configureren;
   >  bijvoorbeeld [https://localhost:4502/system/console/configMgr/com.day.commons.httpclient](https://localhost:4502/system/console/configMgr/com.day.commons.httpclient)
   >
   >
* **Apache HTTP Components Proxy Configuration** om de 4.x API te configureren;
   >  bijvoorbeeld [https://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator](https://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator)
>



