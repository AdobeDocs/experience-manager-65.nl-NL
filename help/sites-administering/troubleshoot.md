---
title: AEM
seo-title: AEM
description: Meer informatie over het oplossen van problemen met AEM.
seo-description: Meer informatie over het oplossen van problemen met AEM.
uuid: 72379531-915c-45d0-ba70-42b212665272
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
discoiquuid: 6346cd93-1ca3-4510-9c31-a74c41017ddb
docset: aem65
translation-type: tm+mt
source-git-commit: 4b965d8f7814816126601f6366c1ba313e404538
workflow-type: tm+mt
source-wordcount: '555'
ht-degree: 0%

---


# AEM {#troubleshooting-aem} oplossen

De volgende sectie behandelt sommige kwesties die u wanneer het gebruiken van AEM kunt ontmoeten, samen met suggesties op hoe te om hen problemen op te lossen.

>[!NOTE]
>
>Zie [Problemen met auteurs oplossen als u problemen met het schrijven van AEM oplost.](/help/sites-authoring/troubleshooting.md)

>[!NOTE]
>
>Wanneer het ervaren van problemen het ook de moeite waard is de lijst van [Bekende Kwesties](/help/release-notes/known-issues.md) voor uw instantie (versie en de dienstpakken) te controleren.

## Problemen met scenario&#39;s voor beheerders {#troubleshooting-scenarios-for-administrators} oplossen

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

Zie [Algemene installatiekwesties](/help/sites-deploying/troubleshooting.md#common-installation-issues) voor informatie over de volgende probleemoplossingsscenario&#39;s:

* Dubbelklikken op de Quickstart-strip heeft geen effect op het JAR-bestand met een ander programma (zoals archiefbeheer).
* Toepassingen die op CRX worden uitgevoerd, genereren fouten die zich buiten het geheugen bevinden.
* Het welkomstscherm AEM wordt niet weergegeven in de browser nadat u hebt dubbelgeklikt op AEM QuickStart.

## Methoden voor de Analyse van het Oplossen van problemen {#methods-for-troubleshooting-analysis}

### Een thread Dump {#making-a-thread-dump} maken

De draadstortplaats is een lijst van alle draden van Java die momenteel actief zijn. Als AEM niet behoorlijk antwoordt, kan de draadstortplaats u helpen kastjes of andere problemen identificeren.

### Het gebruiken van de Dumper van de Dumper van de Schilddraad {#using-sling-thread-dumper}

1. Open de **AEM webconsole**; bijvoorbeeld op `https://localhost:4502/system/console/`.
1. Selecteer **Draden** onder **Status** tabel.

![screen_shot_2012-02-13at43925pm](assets/screen_shot_2012-02-13at43925pm.png)

### jstack (opdrachtregel) {#using-jstack-command-line} gebruiken

1. Zoek de PID (process id) van de AEM Java-instantie.

   U kunt bijvoorbeeld `ps -ef` of `jps` gebruiken.

1. Uitvoeren:

   `jstack <pid>`

1. Dit zal de draadstortplaats tonen.

>[!NOTE]
>
>U kunt de draaddumps aan een logboekdossier toevoegen door `>>` outputredirection te gebruiken:
>
>`jstack <pid> >> /path/to/logfile.log`

Zie de [Hoe te om Dumpels van de Draad van een JVM](https://helpx.adobe.com/cq/kb/TakeThreadDump.html) documentatie voor meer informatie te nemen

### Controleren op niet-afgesloten JCR-sessies {#checking-for-unclosed-jcr-sessions}

Wanneer de functionaliteit voor AEM WCM wordt ontwikkeld, kunnen de zittingen van JCR worden geopend (vergelijkbaar met het openen van een gegevensbestandverbinding). Als de geopende sessies nooit gesloten zijn, kan uw systeem de volgende symptomen ervaren:

* Het systeem wordt langzamer.
* U kunt veel CacheManager zien: resizeAll ingangen in het logboekdossier; het volgende aantal (grootte=&lt;x>) toont het aantal geheime voorgeheugens, elke zittingen opent verscheidene geheime voorgeheugens.
* Van tijd tot tijd heeft het systeem onvoldoende geheugen (na een paar uur, dagen of weken - afhankelijk van de ernst).

Om unclosed zittingen te analyseren en te weten te komen welke code een zitting niet sluit, verwijs naar het artikel [Analyze Unclosed Sessions](https://helpx.adobe.com/crx/kb/AnalyzeUnclosedSessions.html) van de Kennisbank.

### De Adobe Experience Manager-webconsole {#using-the-adobe-experience-manager-web-console} gebruiken

De status van de OSGi-bundels kan ook een vroege indicatie geven van mogelijke problemen.

1. Open de **AEM webconsole**; bijvoorbeeld op `https://localhost:4502/system/console/`.
1. Selecteer **Bundels** onder **OSGI** tabblad.
1. Vinkje:

   * de status van de bundels. Als er inactief of ontevreden zijn, kunt u de bundel stoppen en opnieuw starten. Als het probleem zich blijft voordoen, moet u mogelijk verder onderzoeken met andere methoden.
   * of een van de bundels afhankelijkheden mist. Dergelijke details kunnen worden gezien door op de individuele bundelnaam te klikken, die een verbinding is (het volgende voorbeeld heeft geen kwesties):

![screen_shot_2012-02-13at44706pm](assets/screen_shot_2012-02-13at44706pm.png)

