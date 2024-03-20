---
title: Problemen met Adobe Experience Manager oplossen
description: Meer informatie over het oplossen van problemen die zich kunnen voordoen met Adobe Experience Manager.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
docset: aem65
exl-id: d2d351e7-87a5-4895-b4ec-391fb0b66798
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 0%

---

# Problemen met Adobe Experience Manager oplossen {#troubleshooting-aem}

In de volgende sectie worden enkele problemen beschreven die u kunt tegenkomen bij het gebruik van AEM (Adobe Experience Manager), samen met suggesties voor het oplossen van problemen.

>[!NOTE]
>
>Als u problemen oplost met het schrijven van AEM, raadpleegt u [Problemen met auteurs oplossen.](/help/sites-authoring/troubleshooting.md)

>[!NOTE]
>
>Wanneer u problemen ondervindt, is het ook de moeite waard om de lijst met [Bekende problemen](/help/release-notes/release-notes.md) voor uw instantie (release- en servicepacks).

## Problemen oplossen voor beheerders {#troubleshooting-scenarios-for-administrators}

De volgende lijst verstrekt een overzicht van problemen die de beheerders kunnen problemen oplossen:

<table>
 <tbody>
  <tr>
   <td><strong>Rol</strong></td>
   <td><strong>Probleem </strong></td>
  </tr>
  <tr>
   <td>Systeembeheerder</td>
   <td><p>Als u dubbelklikt op de QuickStart-jar, heeft dit geen effect of wordt het jar-bestand geopend met een ander programma (bijvoorbeeld archiefbeheer)</p> </td>
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

Zie [Veelvoorkomende installatieproblemen](/help/sites-deploying/troubleshooting.md#common-installation-issues) voor informatie over de volgende het oplossen van problemenscenario&#39;s:

* Dubbelklikken op de Quickstart-strip heeft geen effect op het JAR-bestand met een ander programma (zoals archiefbeheer).
* Toepassingen die op CRX worden uitgevoerd, genereren fouten die zich buiten het geheugen bevinden.
* Het welkomstscherm AEM wordt niet weergegeven in de browser nadat u hebt dubbelgeklikt op AEM QuickStart.

## Methoden voor de Analyse van het Oplossen van problemen {#methods-for-troubleshooting-analysis}

### Een Thread Dump maken {#making-a-thread-dump}

De draadstortplaats is een lijst van alle draden Java™ die momenteel actief zijn. Als AEM niet behoorlijk antwoordt, kan de draadstortplaats u helpen kastjes of andere problemen identificeren.

### Dumper met slingerdraad gebruiken {#using-sling-thread-dumper}

1. Open de **Webconsole AEM**; bijvoorbeeld bij `https://localhost:4502/system/console/`.
1. Selecteer de **Threads** krachtens **Status** tab.

![screen_shot_2012-02-13at43925pm](assets/screen_shot_2012-02-13at43925pm.png)

### jstack gebruiken (opdrachtregel) {#using-jstack-command-line}

1. Zoek de PID (process id) van de AEM Java™-instantie.

   U kunt bijvoorbeeld `ps -ef` of `jps`.

1. Uitvoeren:

   `jstack <pid>`

1. Toont de draadstortplaats.

>[!NOTE]
>
>U kunt de draaddumps aan een logboekdossier toevoegen door `>>` uitvoeromleiding:
>
>`jstack <pid> >> /path/to/logfile.log`

Zie de [Hoe u de Thread Dumps van een JVM inneemt](https://experienceleague.adobe.com/docs/experience-cloud-kcs/kbarticles/KA-17452.html) documentatie voor meer informatie

### Controleren op niet-afgesloten JCR-sessies {#checking-for-unclosed-jcr-sessions}

Wanneer de functionaliteit voor AEM WCM wordt ontwikkeld, kunnen de zittingen van JCR worden geopend (vergelijkbaar met het openen van een gegevensbestandverbinding). Als de geopende sessies nooit gesloten zijn, kan uw systeem de volgende symptomen ervaren:

* Het systeem wordt langzamer.
* U kunt veel van CacheManager zien: resizeAll ingangen in het logboekdossier; het volgende aantal (grootte=&lt;x>) geeft het aantal caches weer. Elke sessie opent meerdere caches.
* Van tijd tot tijd heeft het systeem onvoldoende geheugen (na een paar uur, dagen of weken - afhankelijk van de ernst).

Om unclosed zittingen te analyseren en te weten te komen welke code een zitting niet sluit, zie het artikel van de Kennisbank [Niet-gesloten sessies analyseren](https://helpx.adobe.com/experience-manager/kb/AnalyzeUnclosedSessions.html).

### De Adobe Experience Manager-webconsole gebruiken {#using-the-adobe-experience-manager-web-console}

De status van de OSGi-bundels kan ook een vroege indicatie geven van mogelijke problemen.

1. Open de **Webconsole AEM**; bijvoorbeeld bij `https://localhost:4502/system/console/`.
1. Selecteren **Bundels** krachtens **OSGI** tab.
1. Controleren:

   * de status van de bundels. Als er inactief of ontevreden zijn, probeert u de bundel te stoppen en opnieuw te starten. Als het probleem zich blijft voordoen, kunt u het verder onderzoeken met andere methoden.
   * of een van de bundels afhankelijkheden mist. Dergelijke details kunnen worden gezien door de individuele bundelnaam te klikken, die een verbinding is (het volgende voorbeeld heeft geen kwesties):

![screen_shot_2012-02-13at44706pm](assets/screen_shot_2012-02-13at44706pm.png)
