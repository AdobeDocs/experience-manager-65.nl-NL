---
title: Serverpaginanamen voor analyse implementeren
description: Adobe Analytics gebruikt de eigenschap s.pageName om unieke pagina's te identificeren en de gegevens te koppelen die voor de pagina's worden verzameld
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
exl-id: 17a4e4dc-804e-44a9-9942-c37dbfc8016f
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '847'
ht-degree: 0%

---

# Serverpaginanamen voor analyse implementeren{#implementing-server-side-page-naming-for-analytics}

Adobe Analytics gebruikt de `s.pageName` om pagina&#39;s op unieke wijze te identificeren en de gegevens die voor de pagina&#39;s worden verzameld, te koppelen. Typisch, voert u de volgende taken in AEM uit om een waarde aan dit bezit toe te wijzen dat AEM naar Analytics verzendt:

* Gebruik het Cloud Service Framework Analytics om een CQ-variabele toe te wijzen aan Analytics `s.pageName` eigenschap. (Zie [Componentgegevens toewijzen aan Adobe Analytics-eigenschappen](/help/sites-administering/adobeanalytics-mapping.md).)

* Ontwerp de paginacomponent zodanig dat deze de CQ-variabele bevat die u toewijst aan de `s.pageName` eigenschap. (Zie [Adobe Analytics-tracking voor aangepaste componenten implementeren](/help/sites-developing/extending-analytics-components.md).)

Om analysegegevens in de console van Plaatsen en in Inzicht van de Inhoud bloot te stellen, vereist AEM de waarde van `s.pageName` eigenschap voor elke pagina. De Java API voor AEM Analytics definieert de `AnalyticsPageNameProvider` interface die u implementeert om de Sites-console en Content Insights de waarde van de `s.pageName` eigenschap. Uw `AnaltyicsPageNameProvider` De service verhelpt de eigenschap pageName op de server voor rapportagedoeleinden, aangezien deze dynamisch kan worden ingesteld met JavaScript op de client voor traceringsdoeleinden.

## De service Default Analytics Page Name Provider {#the-default-analytics-page-name-provider-service}

De `DefaultPageNameProvider` de dienst is de standaarddienst die de waarde van bepaalt `s.pageName` eigenschap die moet worden gebruikt voor het ophalen van analysegegevens voor een pagina. De dienst werkt samen met de component van de AEM stichting ( `/libs/foundation/components/page`). Deze paginacomponent definieert de volgende CQ-variabelen die aan de `s.pageName` eigenschap:

* `pagedata.path`: De waarde wordt ingesteld op het paginapad.
* `pagedata.title`: De waarde wordt ingesteld op de paginatitel.
* `pagedata.navTitle`: De waarde wordt ingesteld op de paginanavigatiettel.

De `DefaultPageNameProvider` de dienst bepaalt welke van deze variabelen CQ aan in kaart wordt gebracht `s.pageName` in het Cloud-serviceframework Analytics. De dienst bepaalt dan het aangewezen paginabezit voor het terugwinnen van analyserapportgegevens te gebruiken:

* `pagedata.path`: De service gebruikt `page.getPath()`

* `pagedata.title`: De service gebruikt `page.getTitle()`

* `pagedata.navTitle`: De service gebruikt `page.getNavigationTitle()`

De `page` het object is [`com.day.cq.wcm.api.Page`](https://helpx.adobe.com/experience-manager/6-3/sites-developing/reference-materials/javadoc/com/day/cq/wcm/api/Page.html) Java-object voor de pagina.

Als u geen CQ-variabele toewijst aan de `s.pageName` eigenschap in het framework, de waarde voor `s.pageName` wordt gegenereerd op basis van het paginapad. De pagina met het pad `/content/geometrixx/en` gebruikt de waarde `content:geometrixx:en` for `s.pageName`.

>[!NOTE]
>
>De service DefaultPageNameProvider gebruikt een servicerangschikking van 100.

## Continuïteit behouden in analytische rapportage {#maintaining-continuity-in-analytics-reporting}

Voor het bijhouden van een complete geschiedenis van analysegegevens voor een pagina moet de waarde van de eigenschap s.pageName die voor een pagina wordt gebruikt, nooit worden gewijzigd. Nochtans, kunnen de analtytische eigenschappen die de component van de stichtingspagina bepaalt gemakkelijk worden veranderd. Als u bijvoorbeeld een pagina verplaatst, wijzigt u de waarde van `pagedata.path` en breekt de continuïteit van de rapportagegeschiedenis:

* Gegevens die voor het vorige pad zijn verzameld, zijn niet meer gekoppeld aan de pagina.
* Als een andere pagina het pad gebruikt dat een andere pagina ooit heeft gebruikt, neemt de andere pagina de gegevens voor dat pad over.

Om de continuïteit van de rapportage te waarborgen, moet de waarde van `s.pageName` moeten de volgende kenmerken hebben:

* Uniek.
* Stabiel.
* Voor de mens leesbaar.

Een aangepaste pagina-component kan bijvoorbeeld een pagina-eigenschap bevatten die auteurs gebruiken om een unieke id op te geven voor de pagina die wordt gebruikt als de waarde voor de component `s.pageProperties` eigenschap:

* De pagina bevat een analytische variabele die is ingesteld op de waarde van de unieke id die is opgeslagen in de pagina-eigenschap.
* De variabele Analytics wordt toegewezen aan de `s.pageProperties` in het Analytics-framework.
* Uw implementatie van de interface AnalycsPageNameProvider wint de waarde van het paginabezit aan gebruik voor het vragen van de gegevens van de pagina Analytics terug.

>[!NOTE]
>
>Vraag uw analist om hulp bij het ontwikkelen van een effectieve strategie voor uw `s.pageName` waarde.

### De service voor het uitvoeren van een analyse van paginanummerservice {#implementing-an-analytics-page-name-provider-service}

Implementeer de `com.day.cq.analytics.sitecatalyst.AnalyticsPageNameProvider` interface als dienst OSGi om de logica aan te passen die terugwint `s.pageName` eigenschapswaarde. De de paginaanalyses van Plaatsen en Inzicht van de Inhoud gebruiken de dienst om rapportgegevens van Analytics terug te winnen.

De interface AnalyticsPageNameProvider definieert twee methoden die u moet implementeren:

* `getPageName`: Retourneert een `String` waarde die de waarde vertegenwoordigt die als de `s.pageName` eigenschap.

* `getResource`: Hiermee wordt een `org.apache.sling.api.resource.Resource` object dat staat voor de pagina die is gekoppeld aan de `s.pageName` eigenschap.

Beide methoden hebben een `com.day.cq.analytics.sitecatalyst.AnalyticsPageNameContext` object als parameter. De `AnalyticsPageNameContext` class geeft informatie over de context van de analytische aanroepen:

* Het basispad van de paginabron.
* De `Framework` -object voor de cloudserviceconfiguratie Analytics.
* De `Resource` -object voor de pagina.
* De `ResourceResolver` -object voor de pagina.

De klasse biedt ook een setter voor de paginanaam.

### Voorbeeld-analysePageNameProvider-implementatie {#example-analyticspagenameprovider-implementation}

Het volgende voorbeeld `AnalyticsPageNameProvider` de implementatie ondersteunt een aangepaste pagina-component:

* De component breidt de component van de stichtingspagina uit.
* Het dialoogvenster bevat een veld dat auteurs gebruiken om de waarde van de optie `s.pageName` eigenschap.
* De eigenschapswaarde wordt opgeslagen in de eigenschap pageName van het dialoogvenster `jcr:content`knooppunt van de pagina-instanties.
* De eigenschap analytics die de `s.pageName` eigenschap wordt aangeroepen `pagedata.pagename`. Deze eigenschap wordt toegewezen aan de `s.pageName` in het Analytics-framework.

De volgende uitvoering van de `getPageName` De methode keert de waarde van het pageName knoopbezit terug als de kaderafbeelding correct wordt gevormd:

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

De volgende code vertegenwoordigt de volledige klasse, met inbegrip van SCR annotaties die de dienst vormen. De de dienstrangschikking is 200 die de standaarddienst met voeten treedt.

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
