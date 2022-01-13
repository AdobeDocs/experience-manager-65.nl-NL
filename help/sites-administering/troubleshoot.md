---
title: AEM
seo-title: Troubleshooting AEM
description: Meer informatie over het oplossen van problemen met AEM.
seo-description: Learn about troubleshooting issues with AEM.
uuid: 72379531-915c-45d0-ba70-42b212665272
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
discoiquuid: 6346cd93-1ca3-4510-9c31-a74c41017ddb
docset: aem65
exl-id: d2d351e7-87a5-4895-b4ec-391fb0b66798
source-git-commit: d1b4cf87291f7e4a0670a21feca1ebf8dd5e0b5e
workflow-type: tm+mt
source-wordcount: '547'
ht-degree: 0%

---

# AEM {#troubleshooting-aem}

De volgende sectie behandelt sommige kwesties die u wanneer het gebruiken van AEM kunt ontmoeten, samen met suggesties op hoe te om hen problemen op te lossen.

>[!NOTE]
>
>Als u problemen met het maken van AEM met het oplossen van problemen oplost, raadpleegt u [Problemen met auteurs oplossen.](/help/sites-authoring/troubleshooting.md)

>[!NOTE]
>
>Wanneer u problemen ondervindt, is het ook de moeite waard om de lijst met [Bekende problemen](/help/release-notes/release-notes.md) voor uw instantie (release- en servicepacks).

## Het oplossen van problemen scenario&#39;s voor Beheerders {#troubleshooting-scenarios-for-administrators}

De volgende lijst verstrekt een overzicht van problemen beheerders kunnen moeten problemen oplossen:

<table>
 <tbody>
  <tr>
   <td><strong>Rol/rollen</strong></td>
   <td><strong>Probleem </strong></td>
  </tr>
  <tr>
   <td>Systeembeheerder</td>
   <td><p>Als u dubbelklikt op de Quickstart-jar, heeft dit geen effect en wordt het jar-bestand geopend met een ander programma (bijvoorbeeld archiefbeheer)</p> </td>
  </tr>
  <tr>
   <td><p>Systeembeheerder</p> </td>
   <td><p>Mijn toepassing die op CRX loopt werpt fouten uit het geheugen</p> </td>
  </tr>
  <tr>
   <td><p>Systeembeheerder</p> </td>
   <td><p>Het welkomstscherm AEM wordt niet weergegeven in de browser nadat u hebt dubbelgeklikt op AEM CM QuickStart</p> </td>
  </tr>
  <tr>
   <td><p>Systeembeheerder</p> <p>beheerder</p> </td>
   <td><p>Een Thread Dump maken</p> </td>
  </tr>
  <tr>
   <td><p>Systeembeheerder</p> <p>beheerder</p> </td>
   <td><p>Controleren op niet-afgesloten JCR-sessies</p> </td>
  </tr>
 </tbody>
</table>

## Installatieproblemen {#installation-issues}

Zie [Algemene installatieproblemen](/help/sites-deploying/troubleshooting.md#common-installation-issues) voor informatie over de volgende het oplossen van problemenscenario&#39;s:

* Dubbelklikken op de Quickstart-strip heeft geen effect op het JAR-bestand met een ander programma (zoals archiefbeheer).
* Toepassingen die op CRX worden uitgevoerd, genereren fouten die zich buiten het geheugen bevinden.
* Het welkomstscherm AEM wordt niet weergegeven in de browser nadat u hebt dubbelgeklikt op AEM QuickStart.

## Methoden voor de Analyse van het Oplossen van problemen {#methods-for-troubleshooting-analysis}

### Een Thread Dump maken {#making-a-thread-dump}

De draadstortplaats is een lijst van alle draden van Java die momenteel actief zijn. Als AEM niet behoorlijk antwoordt, kan de draadstortplaats u helpen kastjes of andere problemen identificeren.

### Dumper met slingerdraad gebruiken {#using-sling-thread-dumper}

1. Open de **Webconsole AEM**; bijvoorbeeld op `https://localhost:4502/system/console/`.
1. Selecteer **Threads** krachtens **Status** tab.

![screen_shot_2012-02-13at43925pm](assets/screen_shot_2012-02-13at43925pm.png)

### jstack gebruiken (opdrachtregel) {#using-jstack-command-line}

1. Zoek de PID (process id) van de AEM Java-instantie.

   U kunt bijvoorbeeld `ps -ef` of `jps`.

1. Uitvoeren:

   `jstack <pid>`

1. Dit zal de draadstortplaats tonen.

>[!NOTE]
>
>U kunt de draaddumps aan een logboekdossier toevoegen door te gebruiken `>>` uitvoeromleiding:
>
>`jstack <pid> >> /path/to/logfile.log`

Zie de [Hoe u de Thread Dumps van een JVM inneemt](https://helpx.adobe.com/cq/kb/TakeThreadDump.html) documentatie voor meer informatie

### Controleren op niet-afgesloten JCR-sessies {#checking-for-unclosed-jcr-sessions}

Wanneer de functionaliteit voor AEM WCM wordt ontwikkeld, kunnen de zittingen van JCR worden geopend (vergelijkbaar met het openen van een gegevensbestandverbinding). Als de geopende sessies nooit gesloten zijn, kan uw systeem de volgende symptomen ervaren:

* Het systeem wordt langzamer.
* U kunt veel CacheManager zien: resizeAll ingangen in het logboekdossier; het volgende getal (size=&lt;x>) geeft het aantal caches weer. Elke sessie opent meerdere caches.
* Van tijd tot tijd heeft het systeem onvoldoende geheugen (na een paar uur, dagen of weken - afhankelijk van de ernst).

Raadpleeg het artikel in de Knowledge Base als u niet-afgesloten sessies wilt analyseren en wilt weten welke code een sessie niet sluit [Niet-gesloten sessies analyseren](https://helpx.adobe.com/crx/kb/AnalyzeUnclosedSessions.html).

### De Adobe Experience Manager-webconsole gebruiken {#using-the-adobe-experience-manager-web-console}

De status van de OSGi-bundels kan ook een vroege indicatie geven van mogelijke problemen.

1. Open de **Webconsole AEM**; bijvoorbeeld op `https://localhost:4502/system/console/`.
1. Selecteren **Bundels** krachtens **OSGI** tab.
1. Vinkje:

   * de status van de bundels. Als er inactief of ontevreden zijn, kunt u de bundel stoppen en opnieuw starten. Als het probleem zich blijft voordoen, moet u mogelijk verder onderzoeken met andere methoden.
   * of een van de bundels afhankelijkheden mist. Dergelijke details kunnen worden gezien door op de individuele bundelnaam te klikken, die een verbinding is (het volgende voorbeeld heeft geen kwesties):

![screen_shot_2012-02-13at44706pm](assets/screen_shot_2012-02-13at44706pm.png)
