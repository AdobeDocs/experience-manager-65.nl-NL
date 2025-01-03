---
title: Locaties configureren voor Forms
description: Leer hoe u locatie voor AEM formulier configureert. U kunt de bestandslocaties van kenmerken, de locatie van het formulier, het zaadbestand en de cachelocatie opgeven.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 0d9eb7fe-28a6-444e-957d-023687158c61
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: 6a9806d8f40f711a610c130c63d9ab9b2460d075
workflow-type: tm+mt
source-wordcount: '834'
ht-degree: 0%

---

# Locaties configureren voor Forms {#configuring-locations-for-forms}

>[!NOTE]
> 
> Zorg ervoor dat de gebruiker beheerdersrechten heeft om toegang te krijgen tot de beheerdersconsole.

U kunt de URL, URI en bestandslocaties van kenmerken opgeven, zoals de hoofdmap van het web, de locatie van de formulieren die moeten worden opgehaald, het PDF-bestand van het zaadbestand dat wordt gebruikt in PDFForm-transformaties en de cachelocatie.

1. Klik in de beheerconsole op Services > Forms.
1. Geef onder Locaties de juiste opties op. De opties worden hieronder beschreven.
1. Klik op Opslaan.

## Locatie-instellingen {#locations-settings}

**Basis URL:** de basis URL waar de vormmiddelen zoals beelden en manuscripten worden gevestigd. Deze waarde is vereist voor HTML-transformaties die HREF-verwijzingen naar externe afhankelijkheden bevatten, zoals afbeeldingen of scripts. Een dergelijk script is xfasubset.js, dat vereist is voor HTML-formulieren om XFA-intelligentie uit te voeren. Deze waarde moet het HTTP-equivalent zijn van de inhoudroot-URI.

>[!NOTE]
>
>Basis-URL ondersteunt alleen HTTP- of dataopslagprotocollen. Het steunt geen protocollen zoals file:///. Als u toegang moet krijgen tot een bron, zoals een aangepaste CSS- of digitale handtekening-URI, gebruikt u de juiste API-parameterwaarde om de absolute locatie op te geven.

Wanneer een afhankelijkheidspad absoluut is, wordt de basis-URL-waarde genegeerd. Anders wordt het afhankelijkheidspad gecombineerd met de basis-URL.

De standaardwaarde is een lege tekenreeks.

In het volgende voorbeeld wordt naar dezelfde inhoud verwezen (met Inhoudsopgave-URI en Basis-URL):

`(ContentRootURI)/subdir/image1.jpg`

`(BaseURL)/subdir/image1.jpg`

**URI van de Wortel van fs Web:** URL van de het Webtoepassing van Forms. U kunt dit vak leeg laten als de Forms-webtoepassing en de clienttoepassing worden geïmplementeerd op dezelfde toepassingsserver. De Forms API-webhoofdmap wordt gebruikt.

Als de Forms-webtoepassing en de clienttoepassing niet op dezelfde toepassingsserver worden geïmplementeerd, geeft u in dit vak de URL voor de Forms-webtoepassing op, zoals in dit voorbeeld:

`https://<host name>:<port>/FormServer`

Waar `host name` en `port` de servernaam en het havenaantal van de server zijn die de het Webtoepassing van Forms ontvangt.

De standaardwaarde is een lege tekenreeks.

**Wortel URI van het Web:** de het Webwortel van de toepassing. Deze waarde wordt gecombineerd met de parameter sTargetURL (wanneer sTargetURL als relatief wordt verstrekt), opgegeven via de AEM formulieren SDK, om een absolute URL samen te stellen voor toegang tot toepassingsspecifieke webinhoud.

De standaardwaarde is een lege tekenreeks.

**Inhoudswortel URI:** URI of absolute plaats dat de vormen van worden teruggewonnen. Deze waarde wordt gecombineerd met de sFormQuery-parameter, opgegeven via de API, om het absolute pad naar het opgehaalde formulier te maken. Deze waarde kan verwijzen naar een map of een weblocatie die toegankelijk is via HTTP.

De standaardwaarde is een lege tekenreeks.

**URI van de Configuratie XCI:** de relatieve of absolute plaats waarin het XCI dossier dat voor het teruggeven wordt gebruikt wordt gevonden. Voor een relatieve waarde wordt aangenomen dat het XCI-bestand zich in het implementeerbare AEM-bestand bevindt.

De standaardwaarde is `com/adobe/formServer/PA/pa.xci` .

**URI van de Kaart van de Doopvont:** de relatieve of absolute plaats van het doopvont-in kaart brengend dossier. Voor een relatieve waarde wordt aangenomen dat dit bestand zich in het inzetbare AEM van het EAR-bestand bevindt.

Het fonttoewijzingsbestand wordt gebruikt om aangepaste fonttoewijzingen te maken voor HTML-transformaties in formulieren. U kunt dan ook opgeven welk font wordt vervangen wanneer een font niet beschikbaar is op de computer van de client.

De standaardwaarde is `com/adobe/formServer/client-font-map.properties` .

De volgende vermelding is een voorbeeld van een item in het fonttoewijzingsbestand:

`Arial=Arial,Helvetica,sans-serif`

**het Dossier van Zaad PDF:** het aanvankelijke dossier van PDF dat in een transformatie PDFForm wordt gebruikt om levering te optimaliseren. Met het zaadbestand PDF wordt een aangepast PDF-bestand opgegeven (dat alleen XFA-streams, afbeeldingen en fontbronnen bevat) dat wordt toegevoegd aan het formulierontwerp en de gegevens. Het formulier wordt gegenereerd door Acrobat 7 of hoger en is van toepassing op PDFForm-transformatie.

De standaardwaarde is een lege tekenreeks.

**Plaats van het Geheime voorgeheugen:** specificeert de plaats van het de schijfgeheime voorgeheugen van Forms. Wanneer u deze instelling wijzigt, worden alle bestaande cachegegevens van de huidige locatie opnieuw ingesteld en wordt een nieuwe cache gemaakt op de nieuwe locatie. Selecteer een van de volgende opties:

**StandaardPlaats:** dit is de standaardselectie. Als deze optie is geselecteerd, wordt de cache gemaakt op een locatie die afhankelijk is van de toepassingsserver die u gebruikt:

* **JBoss:** [ JBoss Huis ] \ server \ [installeer type]\svcdata\FormServer\Cache
* **WebLogic:** [ WebLogic Huis ] \user_projects\domains\[naam van het domein aem-vormen] \ adobe\ [naam van de Server van Forms] \ FormServer \ Geheime voorgeheugen
* **WebSphere:** [ IBM Huis ] \WebSphere\AppServer\installedApps\adobe\server1\FormServer\Cache

**LC Temp Folder:** het geheime voorgeheugen wordt gecreeerd in een subdirectory van de folder van de AEM vormen temp, die in de beleidsconsole onder Montages > de Montages van het Systeem van de Kern > Configuraties > Plaats van de Folder van Temp wordt gespecificeerd. Subdirectory wordt genoemd adobeform_ [ servernaam ].

>[!NOTE]
>
>Als u een tijdelijk schoonmaakprogramma gebruikt, terwijl het schrappen van deze folders niet functionaliteit beïnvloedt, kan het prestaties voor een korte tijd beduidend beïnvloeden tot het nieuwe geheime voorgeheugen wordt gecreeerd. U voorkomt dit door deze mappen niet te verwijderen terwijl u de tijdelijke map voor AEM formulieren wist.
