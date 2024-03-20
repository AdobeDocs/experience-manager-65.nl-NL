---
title: Integreren met Adobe Analytics
description: Leer hoe u Adobe Experience Manager (AEM) kunt integreren met Adobe Analytics.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
docset: aem65
exl-id: 0a87ece4-57ed-4022-a78a-264c1edf4b4e
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 19%

---

# Integreren met Adobe Analytics{#integrating-with-adobe-analytics}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/integrations/integrating-adobe-analytics.html) |
| AEM 6,5 | Dit artikel |


Door Adobe Analytics en AEM te integreren, kunt u de activiteiten van uw webpagina volgen:

* Met een Adobe Analytics-configuratie kunnen AEM verifiëren met Adobe Analytics.
* Een framework geeft de gegevens aan die naar uw Adobe Analytics-rapportenpakket worden verzonden.

De gegevens bevatten pagina- en gebruikersgegevens, bijvoorbeeld:

* gegevens die AEM componenten verzamelen
* koppelingsklikken
* videogebruiksinformatie
* het aantal pagina-bezoeken van Adobe Analytics

Met de volgende pagina&#39;s kunt u de integratie configureren:

* [Verbinding maken met Adobe Analytics en frameworks maken](/help/sites-administering/adobeanalytics-connect.md)
* [Koppeling bijhouden configureren voor Adobe Analytics](/help/sites-administering/adobeanalytics-link.md)
* [Componentgegevens toewijzen aan Adobe Analytics-eigenschappen](/help/sites-administering/adobeanalytics-mapping.md)
* [Video bijhouden configureren voor Adobe Analytics](/help/sites-administering/adobeanalytics-video.md)
* [Adobe-classificaties](/help/sites-administering/adobeanalytics-classifications.md)

U kunt ook de opdracht [Wizard Inschakelen](/help/sites-administering/opt-in.md) om de integratie gemakkelijk uit te voeren.

>[!NOTE]
>
>Zie ook het &#39;Hoe kan ik?-artikel: [AEM integreren met Adobe Target en Adobe Analytics met behulp van DTM](https://helpx.adobe.com/experience-manager/using/integrate-digital-marketing-solutions.html).

## Aanvullende informatie {#further-information}

Zie:

* [Uitbreiding van de Adobe Analytics-integratie](/help/sites-developing/extending-analytics.md) voor informatie over het ontwikkelen van componenten die gebruikersgegevens verzamelen en het kader van Adobe Analytics aanpassen.
* Het kennisbankartikel, [Adobe Analytics-integratie - problemen oplossen](https://helpx.adobe.com/experience-manager/kb/sitecatalystintegrationtroubleshooting.html), voor informatie over het oplossen van problemen uw integratie van Adobe Analytics.

>[!NOTE]
>
>Als u Adobe Analytics gebruikt met een aangepaste proxyconfiguratie, moet u [twee OSGi-bundels configureren](/help/sites-deploying/configuring-osgi.md) (bijvoorbeeld met de webconsole) die voor de **Apache HTTP Client**-proxyconfiguraties vereist zijn. Beide zijn vereist omdat sommige functies van AEM de 3.x-API&#39;s gebruiken, terwijl andere de 4.x-API&#39;s gebruiken. Configureren:
>
>* **Day Commons HTTP Client 3.1** om de 3.x API te configureren;
>  bijvoorbeeld: [https://localhost:4502/system/console/configMgr/com.day.commons.httpclient](https://localhost:4502/system/console/configMgr/com.day.commons.httpclient)
>
>* **Apache HTTP Components Proxy Configuration** om de 4.x API te configureren;
>  bijvoorbeeld: [https://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator](https://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator)
>
