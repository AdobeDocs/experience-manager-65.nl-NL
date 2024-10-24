---
title: Probleemoplossing in de Gemeenschap
description: Meer informatie over het oplossen van problemen in de community, inclusief bekende problemen en problemen.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: ef4f4108-c485-4e2e-a58f-ff64eee9937e
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# Probleemoplossing in de Gemeenschap {#troubleshooting}

Deze sectie bevat gemeenschappelijke zorgen en bekende kwesties wanneer het oplossen van problemenGemeenschap.

## Bekende problemen {#known-issues}

### Herstellen Dispatcher mislukt {#dispatcher-refetch-fails}

Als u Dispatcher 4.1.5 gebruikt met een nieuwere versie van Jetty, kan een terugzetbewerking resulteren in &#39;Kan geen antwoord van de externe server ontvangen&#39; nadat wordt gewacht tot de aanvraag is verzonden.

Als u Dispatcher 4.1.6 of hoger gebruikt, wordt dit probleem opgelost.

### Kan geen toegang krijgen tot Forum Post na upgrade vanaf CQ 5.4 {#cannot-access-forum-post-after-upgrading-from-cq}

Als een forum op CQ 5.4 en geposte onderwerpen werd gecreeerd, en toen de plaats aan AEM 5.6.1 of later werd bevorderd, kan het proberen om de bestaande posten te bekijken in een fout op de pagina resulteren:

Ongeldig patroonteken &#39;a&#39;
Kan aanvraag aan `/content/demoforums/forum-test.html` op deze server niet verzenden en de logboeken bevatten het volgende:

```xml
20.03.2014 22:49:35.805 ERROR [10.177.45.32 [1395380975744] GET /content/demoforums/forum-test.html HTTP/1.1] com.day.cq.wcm.tags.IncludeTag Error while executing script content.jsp
org.apache.sling.api.scripting.ScriptEvaluationException:
at org.apache.sling.scripting.core.impl.DefaultSlingScript.call(DefaultSlingScript.java:388)
at org.apache.sling.scripting.core.impl.DefaultSlingScript.eval(DefaultSlingScript.java:171)
```

Het probleem is dat de indelingstekenreeks voor com.day.cq.commons.date.RelativeTimeFormat is gewijzigd tussen 5.4 en 5.5, zodat &quot;a&quot; voor &quot;ago&quot; niet langer wordt geaccepteerd.

Daarom moet elke code die de RelativeTimeFormat()-API gebruikt, worden gewijzigd:

* Van: `final RelativeTimeFormat fmt = new RelativeTimeFormat("r a", resourceBundle);`
* Aan: `final RelativeTimeFormat fmt = new RelativeTimeFormat("r", resourceBundle);`

De fout is anders bij Auteur en Publish. Op Auteur, ontbreekt het stil en toont eenvoudig niet de forumonderwerpen. In Publish wordt de fout op de pagina gegenereerd.

Zie [ com.day.cq.commons.date.RelativeTimeFormat ](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/commons/date/RelativeTimeFormat.html) API voor meer informatie.

## Vaak voorkomende problemen {#common-concerns}

### Waarschuwing bij logbestanden: afgekeurde handgrepen {#warning-in-logs-handlebars-deprecated}

Tijdens het opstarten (niet de eerste - maar elke daarna) kan de volgende waarschuwing in de logboeken worden gezien:

* `11.04.2014 08:38:07.223 WARN [FelixStartLevel]com.github.jknack.handlebars.Handlebars Helper 'i18n'` is vervangen door `com.adobe.cq.social.handlebars.I18nHelper@15bac645`

Deze waarschuwing kan veilig worden genegeerd aangezien `jknack.handlebars.Handlebars`, door [ SCF ](scf.md#handlebarsjavascripttemplatinglanguage) wordt gebruikt, met zijn eigen i18n helpernut komt. Bij opstarten, wordt het vervangen met een AEM-specifieke [ i18n helper ](handlebars-helpers.md#i-n). Deze waarschuwing wordt gegenereerd door de bibliotheek van derden om te bevestigen dat een bestaande helper is genegeerd.

### Waarschuwing bij aanmelden: OakResourceListener processOsgiEventQueue {#warning-in-logs-oakresourcelistener-processosgieventqueue}

Het posten van verscheidene het forumonderwerpen van de Sociale Gemeenschappen kan in enorme hoeveelheden waarschuwing en informatielogboeken van OakResourceListener processOsgiEventQueue resulteren.

Deze waarschuwingen kunnen veilig worden genegeerd.

```xml
23.04.2014 14:21:18.900 *WARN* [pool-5-thread-3] org.apache.sling.jcr.resource.internal.OakResourceListener processOsgiEventQueue: Resource at /var/search-collections/ugc-sc/_m.frq/jcr:content not found, which is not expected for an added or modified node
23.04.2014 14:21:18.908 *WARN* [pool-5-thread-3] org.apache.sling.jcr.resource.internal.OakResourceListener processOsgiEventQueue: Resource at /var/search-collections/ugc-sc/_m.prx/jcr:content not found, which is not expected for an added or modified node
23.04.2014 14:21:18.909 *WARN* [pool-5-thread-3] org.apache.sling.jcr.resource.internal.OakResourceListener processOsgiEventQueue: Resource at /var/replication/data/1f799fb4-0aeb-4660-aadb-705657f16048/67/67699ab5-9d57-4c79-a755-2727ba9e6452/jcr:content not found, which is not expected for an added or modified node
23.04.2014 14:21:18.909 *WARN* [pool-5-thread-3] org.apache.sling.jcr.resource.internal.OakResourceListener processOsgiEventQueue: Resource at /var/replication/data/1f799fb4-0aeb-4660-aadb-705657f16048/67/67699ab5-9d57-4c79-a755-2727ba9e6452/jcr:content not found, which is not expected for an added or modified node
23.04.2014 14:21:18.990 *WARN* [pool-5-thread-3] org.apache.sling.jcr.resource.internal.OakResourceListener processOsgiEventQueue: Resource at /var/replication/data/1f799fb4-0aeb-4660-aadb-705657f16048/b9/b91f1690-87e8-41d8-a78e-cd2259f837c8/jcr:content not found, which is not expected for an added or modified node
23.04.2014 14:21:18.990 *WARN* [pool-5-thread-3] org.apache.sling.jcr.resource.internal.OakResourceListener processOsgiEventQueue: Resource at /var/replication/data/1f799fb4-0aeb-4660-aadb-705657f16048/b9/b91f1690-87e8-41d8-a78e-cd2259f837c8/jcr:content not found, which is not expected for an added or modified node
```

### Fout in logbestanden: NoClassDefFoundError voor IndexElementFactory {#error-in-logs-noclassdeffounderror-for-indexelementfactory}

Als u AEM 5.6.1 upgradet naar de nieuwste cq-socialcommunity-pkg-1.4.x of naar AEM 6.0, resulteert dit in fouten in het logbestand. Dit komt tijdens opstarten voor een voorwaarde voor die zich zoals aangetoond door de fout oplost die niet bij nieuw begin wordt gezien.

```xml
14.11.2013 20:52:39.453 ERROR [Apache Sling JCR Resource Event Queue Processor for path '/'] com.adobe.cq.social.storage.index.impl.IndexService Error occurred while processing event java.util.ConcurrentModificationException
14.11.2013 20:52:40.716 ERROR [OsgiInstallerImpl] com.adobe.cq.social.cq-social-commons [CommentListProvider] Error during instantiation of the implementation object (java.lang.NoClassDefFoundError: com/adobe/cq/social/storage/index/IndexElementFactory) java.lang.NoClassDefFoundError: com/adobe/cq/social/storage/index/IndexElementFactory
14.11.2013 20:52:40.717 ERROR [OsgiInstallerImpl] com.adobe.cq.social.cq-social-commons [CommentListProvider] Failed creating the component instance; see log for reason
```
