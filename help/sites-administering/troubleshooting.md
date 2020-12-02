---
title: Werken met logbestanden
seo-title: Werken met logbestanden
description: Leer hoe te om AEM problemen op te lossen door met logboeken te werken.
seo-description: Leer hoe te om AEM problemen op te lossen door met logboeken te werken.
uuid: af8b7f50-c8d4-4760-9f00-3feb0b79ee4c
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
discoiquuid: da92d751-6f14-4512-9d77-7ecf098bd58e
docset: aem65
translation-type: tm+mt
source-git-commit: 8b53e79e3a88f58423e99477db930a4912a1ba09
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 2%

---


# Werken met logbestanden{#working-with-logs}

Deze sectie omvat gedetailleerde informatie over logboeken beschikbaar om u te helpen problemen oplossen.

CRX registreert gedetailleerde logboeken. Nadat u QuickStart hebt uitpakken en gestart, kunt u logbestanden op de volgende locaties vinden:

* crx-quickstart/launch/logs
* crx-quickstart/server/logs
* crx-quickstart/logs

## Het FOUTOPSPORINGSlogniveau {#activating-the-debug-log-level} activeren

Het standaardlogboekniveau is INFO, dat wil zeggen, worden de DEBUG- berichten niet geregistreerd.

Als u het niveau van het DEBUG-logbestand wilt activeren, gebruikt u de CRX-verkenner om de

```xml
/libs/sling/config/org.apache.sling.commons.log.LogManager/org.apache.sling.commons.log.level
```

eigenschap voor foutopsporing. Verlaat het logboek bij het DEBUG logboekniveau niet langer dan nodig, aangezien het veel logboeken produceert.

Een lijn in zuivert dossier begint gewoonlijk met DEBUG, en verstrekt dan het logboekniveau, de installeractie en het logboekbericht. Bijvoorbeeld:

```xml
DEBUG 3 WebApp Panel: WebApp successfully deployed
```

De logniveaus zijn als volgt:

| 0 | Fatale fout | De handeling is mislukt en het installatieprogramma kan niet doorgaan. |
|---|---|---|
| 1 | Fout | De handeling is mislukt. De installatie gaat door, maar een deel van CRX is niet correct geïnstalleerd en werkt niet. |
| 2 | Waarschuwing | De actie is geslaagd maar heeft problemen ondervonden. CRX werkt mogelijk niet correct. |
| 3 | Informatie | De actie is geslaagd. |

## Uitgebreide optie gebruikt voor probleemoplossing {#verbose-option-used-for-troubleshooting}

Wanneer u CRX start, kunt u de optie -v (verbose) toevoegen aan de opdrachtregel zoals in:

` java -jar crx-<*version*>-<*edition*>.jar -v`

Gebruik de uitgebreide optie voor het oplossen van problemen aangezien deze optie sommige van de uitvoer van het snelstartlogboek op de console toont.