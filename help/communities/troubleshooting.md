---
title: Problemen oplossen
seo-title: Problemen oplossen
description: De Gemeenschap van het oplossen van problemen met inbegrip van Bekende Kwesties
seo-description: De Gemeenschap van het oplossen van problemen met inbegrip van Bekende Kwesties
uuid: 99225430-fa2a-4393-ae5a-18b19541c358
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: cdb2d80a-2fbf-4ee6-b89b-b5d74e6d3bfc
translation-type: tm+mt
source-git-commit: 77d00c1d6e94b257aa0533ca88b5f9a12dba0054

---


# Problemen oplossen {#troubleshooting}

Deze paragraaf bevat gemeenschappelijke zorgen en bekende problemen.

## Bekende problemen {#known-issues}

### Terugzetfout verzender mislukt {#dispatcher-refetch-fails}

Wanneer Dispatcher 4.1.5 wordt gebruikt met een nieuwere versie van Jetty, kan een terugzetbewerking resulteren in &#39;Kan geen reactie van de externe server ontvangen&#39; nadat wordt gewacht tot de aanvraag is verzonden.

Dit probleem wordt opgelost door Dispatcher 4.1.6 of hoger te gebruiken.

### Kan de Post van het Forum na Bevordering van CQ 5.4 niet openen {#cannot-access-forum-post-after-upgrading-from-cq}

Als een forum op CQ 5.4 en geposte onderwerpen werd gecreeerd, en toen de plaats aan AEM 5.6.1 of later werd bevorderd, kan het proberen om de bestaande posten te bekijken in een fout op de pagina resulteren:

Ongeldig patroonteken &#39;a&#39;Cannot serve request to `/content/demoforums/forum-test.html` on this server and the logs contain the following:

```xml
20.03.2014 22:49:35.805 ERROR [10.177.45.32 [1395380975744] GET /content/demoforums/forum-test.html HTTP/1.1] com.day.cq.wcm.tags.IncludeTag Error while executing script content.jsp
org.apache.sling.api.scripting.ScriptEvaluationException:
at org.apache.sling.scripting.core.impl.DefaultSlingScript.call(DefaultSlingScript.java:388)
at org.apache.sling.scripting.core.impl.DefaultSlingScript.eval(DefaultSlingScript.java:171)
```

Het probleem is dat de indelingstekenreeks voor com.day.cq.commons.date.RelativeTimeFormat is gewijzigd tussen 5.4 en 5.5, zodat &quot;a&quot; voor &quot;ago&quot; niet langer wordt geaccepteerd.

Daarom moet elke code die de RelativeTimeFormat()-API gebruikt, worden gewijzigd:

* From: `final RelativeTimeFormat fmt = new RelativeTimeFormat("r a", resourceBundle);`
* Naar: `final RelativeTimeFormat fmt = new RelativeTimeFormat("r", resourceBundle);`

De fout is anders bij auteur en publiceren. Op auteur ontbreekt het stil en toont eenvoudig niet de forumonderwerpen. Bij publicatie wordt de fout op de pagina gegenereerd.

Zie de [com.day.cq.commons.date.RelativeTimeFormat](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/date/RelativeTimeFormat.html) -API voor meer informatie.

## Algemene problemen {#common-concerns}

### Waarschuwing bij logbestanden: Afgekeurde kleurenbalken {#warning-in-logs-handlebars-deprecated}

Tijdens het opstarten (niet 1st - maar om het even welke daarna) kan de volgende waarschuwing in de logboeken worden gezien:

* `11.04.2014 08:38:07.223 WARN [FelixStartLevel]com.github.jknack.handlebars.Handlebars Helper 'i18n'` is vervangen door `com.adobe.cq.social.handlebars.I18nHelper@15bac645`

Deze waarschuwing kan veilig worden genegeerd aangezien `jknack.handlebars.Handlebars`, gebruikt door [SCF](scf.md#handlebarsjavascripttemplatinglanguage), met zijn eigen i18n helpernut komt. Bij het opstarten wordt deze vervangen door een AEM-specifieke [i18n-helper](handlebars-helpers.md#i-n). Deze waarschuwing wordt gegenereerd door de bibliotheek van derden om te bevestigen dat een bestaande helper is genegeerd.

### Waarschuwing bij logbestanden: OakResourceListener processOsgiEventQueue {#warning-in-logs-oakresourcelistener-processosgieventqueue}

Het posten van een aantal onderwerpen van het Forum van Sociale Gemeenschappen kan in enorme hoeveelheden waarschuwing en informatielogboeken van OakResourceListener processOsgiEventQueue resulteren.

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

Als u AEM 5.6.1 GA upgradet naar de nieuwste cq-socialecommunes-pkg-1.4.x of naar AEM 6.0, treedt het logbestand tijdens het opstarten op met fouten. Dit probleem wordt opgelost, zoals blijkt uit de fout die niet wordt gezien bij het opnieuw opstarten.

```xml
14.11.2013 20:52:39.453 ERROR [Apache Sling JCR Resource Event Queue Processor for path '/'] com.adobe.cq.social.storage.index.impl.IndexService Error occurred while processing event java.util.ConcurrentModificationException
14.11.2013 20:52:40.716 ERROR [OsgiInstallerImpl] com.adobe.cq.social.cq-social-commons [CommentListProvider] Error during instantiation of the implementation object (java.lang.NoClassDefFoundError: com/adobe/cq/social/storage/index/IndexElementFactory) java.lang.NoClassDefFoundError: com/adobe/cq/social/storage/index/IndexElementFactory
14.11.2013 20:52:40.717 ERROR [OsgiInstallerImpl] com.adobe.cq.social.cq-social-commons [CommentListProvider] Failed creating the component instance; see log for reason
```
