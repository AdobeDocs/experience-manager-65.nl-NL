---
title: Locaties voor Forms configureren
seo-title: Locaties voor Forms configureren
description: Leer hoe u locatie voor Forms configureert.
seo-description: Leer hoe u locatie voor Forms configureert.
uuid: ba35888b-492c-4678-890b-160b53e7d659
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 3d2b7cfb-228c-4cc2-8fcd-d500f0010010
translation-type: tm+mt
source-git-commit: 2cf9dcf2e9cf71c54e19e2c6ee825c9a8f00a9b7

---


# Locaties voor Forms configureren {#configuring-locations-for-forms}

U kunt de URL, URI en bestandslocaties van kenmerken opgeven, zoals de hoofdmap van het web, de locatie van de formulieren die moeten worden opgehaald, het PDF-bestand met het zaadbestand dat wordt gebruikt in PDFForm-transformaties en de cachelocatie.

1. Klik in de beheerconsole op Services > Forms.
1. Geef onder Locaties de juiste opties op. De opties worden hieronder beschreven.
1. Klik op Opslaan.

## Locatie-instellingen {#locations-settings}

**Basis-URL:** De basis-URL waar formulierbronnen zoals afbeeldingen en scripts zich bevinden. Deze waarde is vereist voor HTML-transformaties die HREF-verwijzingen naar externe afhankelijkheden bevatten, zoals afbeeldingen of scripts. Een dergelijk script is xfasubset.js, dat vereist is voor HTML-formulieren om XFA-intelligentie uit te voeren. Deze waarde moet het HTTP-equivalent zijn van de inhoudroot-URI.

>[!NOTE]
>
>Basis-URL ondersteunt alleen HTTP- of dataopslagprotocollen. Het steunt geen protocollen zoals file:///. Als u toegang moet krijgen tot een bron, zoals een aangepaste CSS- of digitale handtekening-URI, gebruikt u de juiste API-parameterwaarde om de absolute locatie op te geven.

Wanneer een afhankelijkheidspad absoluut is, wordt de basis-URL-waarde genegeerd. Anders wordt het afhankelijkheidspad gecombineerd met de basis-URL.

De standaardwaarde is een lege tekenreeks.

In het volgende voorbeeld wordt naar dezelfde inhoud verwezen (met Inhoudsopgave-URI en Basis-URL):

`(ContentRootURI)/subdir/image1.jpg`

`(BaseURL)/subdir/image1.jpg`

**FS Web Root URI:** De URL van de webtoepassing Forms. U kunt dit vak leeg laten als de webtoepassing Forms en de clienttoepassing op dezelfde toepassingsserver worden geïmplementeerd. De URL van de webhoofdmap van de Forms API wordt gebruikt.

Als de Forms-webtoepassing en de clienttoepassing niet op dezelfde toepassingsserver worden geïmplementeerd, geeft u in dit vak de URL voor de Forms-webtoepassing op, zoals in dit voorbeeld:

`https://<host name>:<port>/FormServer`

Waar `host name`en `port` zijn de servernaam en het poortnummer van de server die als host fungeert voor de Forms-webtoepassing.

De standaardwaarde is een lege tekenreeks.

**Web Root URI:** De hoofdmap van de toepassing. Deze waarde wordt gecombineerd met de parameter sTargetURL (wanneer sTargetURL als relatief wordt verstrekt), gespecificeerd door AEM vormen SDK, om een absolute URL te construeren om tot toepassing-specifieke Web-inhoud toegang te hebben.

De standaardwaarde is een lege tekenreeks.

**URI van basisinhoud:** De URI of absolute locatie waaruit formulieren worden opgehaald. Deze waarde wordt gecombineerd met de sFormQuery-parameter, opgegeven via de API, om het absolute pad naar het opgehaalde formulier te maken. Deze waarde kan verwijzen naar een map of een weblocatie die toegankelijk is via HTTP.

De standaardwaarde is een lege tekenreeks.

**URI XCI-configuratie:** De relatieve of absolute locatie waarin het XCI-bestand dat voor rendering wordt gebruikt, wordt gevonden. Voor een relatieve waarde wordt aangenomen dat het XCI-bestand zich in het implementeerbare AEM-formulierbestand EAR bevindt.

De standaardwaarde is `com/adobe/formServer/PA/pa.xci`.

**URI lettertypetoewijzing:** De relatieve of absolute locatie van het fonttoewijzingsbestand. Voor een relatieve waarde wordt aangenomen dat dit bestand zich in het implementeerbare AEM-formulierbestand EAU bevindt.

Het fonttoewijzingsbestand wordt gebruikt om aangepaste fonttoewijzingen te maken voor HTML-transformaties in formulieren. Hierdoor kunt u opgeven welk font wordt vervangen wanneer een font niet beschikbaar is op de computer van de client.

De standaardwaarde is `com/adobe/formServer/client-font-map.properties`.

De volgende vermelding is een voorbeeld van een item in het fonttoewijzingsbestand:

`Arial=Arial,Helvetica,sans-serif`

**PDF-zaadbestand:** Het oorspronkelijke PDF-bestand dat wordt gebruikt in een PDFForm-transformatie om de levering te optimaliseren. In het PDF-bestand met de zaadnaam wordt een aangepast PDF-bestand opgegeven (dat alleen XFA-stroom, afbeelding en fontbronnen bevat) dat wordt toegevoegd aan het formulierontwerp en de gegevens. Het formulier wordt gegenereerd door Acrobat 7 of hoger en is van toepassing op PDFForm-transformatie.

De standaardwaarde is een lege tekenreeks.

**Cachelocatie:** Hiermee geeft u de locatie op van de schijfcache van Forms. Wanneer u deze instelling wijzigt, worden alle bestaande cachegegevens van de huidige locatie opnieuw ingesteld en wordt een nieuwe cache gemaakt op de nieuwe locatie. Kies een van de volgende opties:

**Standaardlocatie:** Dit is de standaardselectie. Als deze optie is geselecteerd, wordt de cache gemaakt op een locatie die afhankelijk is van de toepassingsserver die u gebruikt:

* **JBoss:** [JBoss Home]\server\[installatietype]\svcdata\FormServer\Cache
* **WebLogic:** [WebLogic Home]\user_projects\domains\[domeinnaam aem-formulieren]\adobe\[naam formulierserver]\FormServer\Cache
* **WebSphere:** [IBM Home]\WebSphere\AppServer\installedApps\adobe\server1\FormServer\Cache

**LC Temp-map:** De cache wordt gemaakt in een submap van de map AEM forms temp, die wordt opgegeven in de beheerconsole onder Instellingen > Core System Settings > Configurations > Location of Temp Directory. De submap heeft de naam adobeform_[servername].

>[!NOTE]
>
>Als u een hulpprogramma voor tijdelijke reiniging gebruikt, moet u er rekening mee houden dat het verwijderen van deze mappen geen invloed heeft op de functionaliteit, maar dat dit de prestaties gedurende korte tijd aanzienlijk kan beïnvloeden totdat de nieuwe cache wordt gemaakt. U voorkomt dit door deze mappen niet te verwijderen terwijl u de tijdelijke map voor AEM-formulieren wist.

