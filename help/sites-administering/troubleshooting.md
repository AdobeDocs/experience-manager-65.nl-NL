---
title: Werken met logbestanden
description: Leer hoe te om AEM problemen op te lossen door met logboeken te werken.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
docset: aem65
exl-id: ab4fc41f-e0e9-4577-aab2-f0b4298f9a59
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 2%

---

# Werken met logbestanden{#working-with-logs}

Deze sectie omvat gedetailleerde informatie over logboeken beschikbaar om u te helpen problemen oplossen.

>[!NOTE]
>
>Zie voor meer informatie over logboeken:
>
>* [Onderhoud controlelogbestand in AEM](/help/sites-administering/operations-audit-log.md)
>* [Werken met auditrecords en logbestanden](/help/sites-deploying/monitoring-and-maintaining.md#working-with-audit-records-and-log-files)

CRX registreert gedetailleerde logboeken. Nadat u QuickStart hebt uitpakken en gestart, kunt u logbestanden op de volgende locaties vinden:

* crx-quickstart/launch/logs
* crx-quickstart/server/logs
* crx-quickstart/logs

## Het FOUTOPSPORINGSlogniveau activeren {#activating-the-debug-log-level}

Het standaardlogboekniveau is INFO, dat wil zeggen, worden de DEBUG- berichten niet geregistreerd.

Als u het niveau van het DEBUG-logbestand wilt activeren, gebruikt u de CRX-verkenner om de

```xml
/libs/sling/config/org.apache.sling.commons.log.LogManager/org.apache.sling.commons.log.level
```

eigenschap voor foutopsporing. Verlaat het logboek bij het DEBUG logboekniveau niet langer dan nodig, aangezien het talrijke logboeken produceert.

Een lijn in zuivert dossier begint gewoonlijk met DEBUG, en verstrekt dan het logboekniveau, de installeractie en het logboekbericht. Bijvoorbeeld:

```xml
DEBUG 3 WebApp Panel: WebApp successfully deployed
```

De logniveaus zijn als volgt:

| 0 | Fatale fout | De handeling is mislukt en het installatieprogramma kan niet doorgaan. |
|---|---|---|
| 1 | Fout | De handeling is mislukt. De installatie gaat door, maar een deel van CRX is niet correct geïnstalleerd en werkt niet. |
| 2 | Waarschuwing | De actie is geslaagd maar heeft problemen ondervonden. CRX werkt mogelijk wel of niet correct. |
| 3 | Informatie | De actie is geslaagd. |

## Uitgebreide optie gebruikt voor probleemoplossing {#verbose-option-used-for-troubleshooting}

Wanneer u CRX start, kunt u de optie -v (verbose) toevoegen aan de opdrachtregel zoals in:

` java -jar crx-<*version*>-<*edition*>.jar -v`

Gebruik de uitgebreide optie voor het oplossen van problemen aangezien deze optie sommige van de uitvoer van het snelstartlogboek op de console toont.
