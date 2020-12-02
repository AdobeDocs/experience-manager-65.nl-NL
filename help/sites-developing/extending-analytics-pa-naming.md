---
title: Serverpaginanamen voor analyse implementeren
seo-title: Serverpaginanamen voor analyse implementeren
description: Adobe Analytics gebruikt de eigenschap s.pageName om unieke pagina's te identificeren en de gegevens te koppelen die voor de pagina's worden verzameld
seo-description: Adobe Analytics gebruikt de eigenschap s.pageName om unieke pagina's te identificeren en de gegevens te koppelen die voor de pagina's worden verzameld
uuid: 37b92099-0cce-4b2d-b55c-928f636dbd7e
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: be2aa297-5b78-4b1d-8ff1-e6a585a177dd
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '885'
ht-degree: 0%

---


# Serverpaginanaam implementeren voor Analytics{#implementing-server-side-page-naming-for-analytics}

Adobe Analytics gebruikt de eigenschap `s.pageName` om pagina&#39;s op unieke wijze te identificeren en de gegevens die voor de pagina&#39;s worden verzameld, te koppelen. Typisch, voert u de volgende taken in AEM uit om een waarde aan dit bezit toe te wijzen dat AEM naar Analytics verzendt:

* Gebruik het de wolkendienstkader van de Analyse om een variabele CQ aan de Analytics `s.pageName` bezit in kaart te brengen. (Zie [Componentgegevens toewijzen met Adobe Analytics-eigenschappen](/help/sites-administering/adobeanalytics-mapping.md).)

* Ontwerp de paginacomponent zodat deze de CQ-variabele bevat die u toewijst aan de eigenschap `s.pageName`. (Zie [Adobe Analytics-tracking implementeren voor aangepaste componenten](/help/sites-developing/extending-analytics-components.md).)

Om analysegegevens in de console van Plaatsen en in Inzicht van de Inhoud bloot te stellen, vereist AEM de waarde van `s.pageName` bezit voor elke pagina. De AEM Analytics Java API definieert de `AnalyticsPageNameProvider`-interface die u implementeert om de Sites-console en Content Insights te voorzien van de waarde van de `s.pageName`-eigenschap. Uw `AnaltyicsPageNameProvider`-service verhelpt de eigenschap pageName op de server voor rapportagedoeleinden, aangezien deze dynamisch kan worden ingesteld met JavaScript op de client voor traceringsdoeleinden.

## De standaardservice {#the-default-analytics-page-name-provider-service} voor paginanummers

De service `DefaultPageNameProvider` is de standaardservice die de waarde bepaalt van de eigenschap `s.pageName` die moet worden gebruikt voor het ophalen van analysegegevens voor een pagina. De service werkt samen met de component AEM basispagina ( `/libs/foundation/components/page`). Deze paginacomponent definieert de volgende CQ-variabelen die moeten worden toegewezen aan de eigenschap `s.pageName`:

* `pagedata.path`: De waarde wordt ingesteld op het paginapad.
* `pagedata.title`: De waarde wordt ingesteld op de paginatitel.
* `pagedata.navTitle`: De waarde wordt ingesteld op de titel van de paginanavigatie.

De `DefaultPageNameProvider`-service bepaalt welke van deze CQ-variabelen wordt toegewezen aan de eigenschap `s.pageName` in het cloudserviceframework Analytics. De dienst bepaalt dan het aangewezen paginabezit voor het terugwinnen van analyserapportgegevens te gebruiken:

* `pagedata.path`: De service gebruikt  `page.getPath()`

* `pagedata.title`: De service gebruikt  `page.getTitle()`

* `pagedata.navTitle`: De service gebruikt  `page.getNavigationTitle()`

Het `page`-object is het Java-object [ `com.day.cq.wcm.api.Page`](https://helpx.adobe.com/experience-manager/6-3/sites-developing/reference-materials/javadoc/com/day/cq/wcm/api/Page.html) voor de pagina.

Als u geen CQ-variabele toewijst aan de eigenschap `s.pageName` in het framework, wordt de waarde voor `s.pageName` gegenereerd vanuit het paginapad. De pagina met het pad `/content/geometrixx/en` gebruikt bijvoorbeeld de waarde `content:geometrixx:en` voor `s.pageName`.

>[!NOTE]
>
>De service DefaultPageNameProvider gebruikt een servicerangschikking van 100.

## Continuïteit behouden in analytische rapportage {#maintaining-continuity-in-analytics-reporting}

Voor het bijhouden van een complete geschiedenis van analysegegevens voor een pagina moet de waarde van de eigenschap s.pageName die voor een pagina wordt gebruikt, nooit worden gewijzigd. Nochtans, kunnen de analtytische eigenschappen die de component van de stichtingspagina bepaalt gemakkelijk worden veranderd. Als u bijvoorbeeld een pagina verplaatst, verandert de waarde van `pagedata.path` en wordt de continuïteit van de rapportgeschiedenis verbroken:

* Gegevens die voor het vorige pad zijn verzameld, zijn niet meer gekoppeld aan de pagina.
* Als een andere pagina het pad gebruikt dat een andere pagina ooit heeft gebruikt, neemt de andere pagina de gegevens voor dat pad over.

Om de continuïteit van de rapportage te garanderen, moet de waarde van `s.pageName` de volgende kenmerken hebben:

* Uniek.
* Stabiel.
* Geschikt voor mensen.

Een aangepaste pagina-component kan bijvoorbeeld een pagina-eigenschap bevatten die auteurs gebruiken om een unieke id op te geven voor de pagina die wordt gebruikt als de waarde voor de eigenschap `s.pageProperties`:

* De pagina bevat een analytische variabele die is ingesteld op de waarde van de unieke id die is opgeslagen in de pagina-eigenschap.
* De variabele analytics wordt toegewezen aan de eigenschap `s.pageProperties` in het Analytics-framework.
* Uw implementatie van de interface AnalycsPageNameProvider wint de waarde van het paginabezit aan gebruik voor het vragen van de gegevens van de pagina Analytics terug.

>[!NOTE]
>
>Vraag uw consultant voor Analytics om hulp bij het ontwikkelen van een effectieve strategie voor uw `s.pageName`-waarde.

### Service {#implementing-an-analytics-page-name-provider-service} voor het implementeren van een analytische paginanummerservice

Implementeer de `com.day.cq.analytics.sitecatalyst.AnalyticsPageNameProvider` interface als dienst OSGi om de logica aan te passen die `s.pageName` bezitswaarde terugwint. De de paginaanalyses van Plaatsen en Inzicht van de Inhoud gebruiken de dienst om rapportgegevens van Analytics terug te winnen.

De interface AnalyticsPageNameProvider definieert twee methoden die u moet implementeren:

* `getPageName`: Retourneert een  `String` waarde die de waarde vertegenwoordigt die als  `s.pageName` eigenschap moet worden gebruikt.

* `getResource`: Retourneert een  `org.apache.sling.api.resource.Resource` object dat de pagina vertegenwoordigt die aan de  `s.pageName` eigenschap is gekoppeld.

Beide methoden gebruiken een object `com.day.cq.analytics.sitecatalyst.AnalyticsPageNameContext` als parameter. De klasse `AnalyticsPageNameContext` biedt informatie over de context van de analytische aanroepen:

* Het basispad van de paginabron.
* Het `Framework`-object voor de configuratie van de Analytics-cloudservice.
* Het object `Resource` voor de pagina.
* Het object `ResourceResolver` voor de pagina.

De klasse biedt ook een setter voor de paginanaam.

### Voorbeeld-analysePageNameProvider-implementatie {#example-analyticspagenameprovider-implementation}

In het volgende voorbeeld wordt een aangepaste pagina-component ondersteund door de `AnalyticsPageNameProvider`-implementatie:

* De component breidt de component van de stichtingspagina uit.
* Het dialoogvenster bevat een veld dat auteurs gebruiken om de waarde van de eigenschap `s.pageName` op te geven.
* De eigenschapswaarde wordt opgeslagen in de eigenschap pageName van het knooppunt `jcr:content`van de pagina-instanties.
* De eigenschap analytics die de eigenschap `s.pageName` opslaat, wordt `pagedata.pagename` genoemd. Deze eigenschap wordt toegewezen aan de eigenschap `s.pageName` in het Analyseframework.

De volgende implementatie van de methode `getPageName` keert de waarde van het pageName knoopbezit terug als de kaderafbeelding correct wordt gevormd:

```java
public String getPageName(AnalyticsPageNameContext context) {
        String pageName = null;

        Framework framework = context.getFramework();
        Resource resource = context.getResource();

        if (resource != null && framework != null && framework.mapsSCVariable(S_PAGE_NAME)) {
            String cqVar = framework.getMapping(S_PAGE_NAME);
            Page page = resource.adaptTo(Page.class);
            if (cqVar.equals("pagedata.pagename")) {
                pageName = page.getProperties().get("pageName",null);
            }
        }
        return pageName;
    }
```

De volgende implementatie van de methode getResource keert het voorwerp van het Middel voor de pagina terug:

```java
     public Resource getResource(AnalyticsPageNameContext context) {
        Resource res = null;

        Framework framework = context.getFramework();
        ResourceResolver resolver = context.getResourceResolver();
        String pageName = context.getPageName();
        String basePath = context.getBasePath();

        if (pageName != null && basePath != null && resolver != null
                && framework != null && framework.mapsSCVariable(S_PAGE_NAME)) {
            String cqVar = framework.getMapping(S_PAGE_NAME);
            if (cqVar.equals("pagedata.pagename")) {
             Iterator<Resource>
             hits = resolver.findResources(createQuery(pageName, basePath, "pagename"), Query.JCR_SQL2);
             if (hits.hasNext()) {
              res = hits.next();
              res = res.getParent();
             }
            }
        }
        return res;
    }

    private String createQuery(String pageName, String basePath, String propName) {
        return "SELECT * FROM [cq:PageContent] WHERE ISDESCENDANTNODE(["
                + basePath + "]) and [" + propName + "] = \"" + pageName + "\"";
    }
```

De volgende code vertegenwoordigt de volledige klasse, met inbegrip van SCR annotaties die de dienst vormen. Merk op dat de de dienstrangschikking 200 is die de standaarddienst met voeten treedt.

```java
/*************************************************************************
 *
 * ADOBE CONFIDENTIAL
 * __________________
 *
 * Copyright 2019 Adobe Systems Incorporated
 * All Rights Reserved.
 *
 * NOTICE:  All information contained herein is, and remains
 * the property of Adobe Systems Incorporated and its suppliers,
 * if any.  The intellectual and technical concepts contained
 * herein are proprietary to Adobe Systems Incorporated and its
 * suppliers and may be covered by U.S. and Foreign Patents,
 * patents in process, and are protected by trade secret or copyright law.
 * Dissemination of this information or reproduction of this material
 * is strictly forbidden unless prior written permission is obtained
 * from Adobe Systems Incorporated.
 **************************************************************************/
package com.day.cq.analytics.sitecatalyst;

import java.util.Iterator;

import javax.jcr.query.Query;

import org.apache.sling.api.resource.Resource;
import org.apache.sling.api.resource.ResourceResolver;
import org.osgi.framework.Constants;
import org.osgi.service.component.annotations.Component;

import com.day.cq.analytics.sitecatalyst.AnalyticsPageNameContext;
import com.day.cq.analytics.sitecatalyst.AnalyticsPageNameProvider;
import com.day.cq.analytics.sitecatalyst.Framework;
import com.day.cq.wcm.api.Page;

import static com.day.cq.analytics.sitecatalyst.AnalyticsPageNameContext.S_PAGE_NAME;

/**
 * Default implementation of {@link AnalyticsPageNameProvider} that resolves
 * page title, path or navTitle if mapped in {@link Framework}.
 */
@Component(
    service = { AnalyticsPageNameProvider.class },
    property = {
        Constants.SERVICE_DESCRIPTION + "=Example Page Name Resolver implementation",
        Constants.SERVICE_RANKING + ":Integer=200"
    }
)
public class ExamplePageNameProvider implements AnalyticsPageNameProvider {
    public String getPageName(AnalyticsPageNameContext context) {
        String pageName = null;

        Framework framework = context.getFramework();
        Resource resource = context.getResource();

        if (resource != null && framework != null && framework.mapsSCVariable(S_PAGE_NAME)) {
            String cqVar = framework.getMapping(S_PAGE_NAME);
            Page page = resource.adaptTo(Page.class);
            if (cqVar.equals("pagedata.path")) {
                pageName = page.getProperties().get("pageName",null);
            }
        }
        return pageName;
    }

    public Resource getResource(AnalyticsPageNameContext context) {
        Resource res = null;

        Framework framework = context.getFramework();
        ResourceResolver resolver = context.getResourceResolver();
        String pageName = context.getPageName();
        String basePath = context.getBasePath();

        if (pageName != null && basePath != null && resolver != null
                && framework != null && framework.mapsSCVariable(S_PAGE_NAME)) {
            String cqVar = framework.getMapping(S_PAGE_NAME);
            if (cqVar.equals("pagedata.pagename")) {
                Iterator<Resource>
                hits = resolver.findResources(createQuery(pageName, basePath, "pagename"), Query.JCR_SQL2);
                if (hits.hasNext()) {
                    res = hits.next();
                    res = res.getParent();
                }
            }
        }
        return res;
    }

    private String createQuery(String pageName, String basePath, String propName) {
        return "SELECT * FROM [cq:PageContent] WHERE ISDESCENDANTNODE(["
                + basePath + "]) and [" + propName + "] = \"" + pageName + "\"";
    }
}
```

