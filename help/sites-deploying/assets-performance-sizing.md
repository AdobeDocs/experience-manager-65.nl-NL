---
title: Assets Performance Guide
description: Leer hoe u de optimale hardwaregrootte kunt bepalen voor een nieuwe DAM-installatie (Digital Asset Management) en hoe u prestatieproblemen kunt oplossen
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: configuring
exl-id: fbe15e1b-830b-4752-bd02-0d239a90bc68
solution: Experience Manager, Experience Manager Sites
feature: Configuring
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '1210'
ht-degree: 0%

---

# Assets Performance Guide{#assets-performance-guide}

DAM (Digital Asset Management) wordt vaak gebruikt in gevallen waarin prestaties van belang zijn. De standaard DAM-configuratie bevat echter verschillende hardware- en softwareonderdelen die de prestaties kunnen beïnvloeden. Dit document bevat het volgende:

* Informatie voor systeembeheerders over het bepalen van de optimale hardwaregrootte voor een nieuwe Digital Asset Management-instelling
* Informatie voor softwareontwikkelaars die DAM-instanties problemen willen oplossen met de prestaties

## Prestatieproblemen {#performance-issues}

Slechte prestaties bij het beheer van digitale middelen kunnen de gebruikerservaring op drie manieren beïnvloeden: interactieve prestaties, verwerking van bedrijfsmiddelen en downloadsnelheid. Om de prestaties te verbeteren, is het belangrijk om de waargenomen prestaties correct te meten en doelmeetwaarden te bepalen.

**1. Interactief zoeken en bladeren** De gebruikers zoeken naar activa of doorbladeren de Vinder DAM en klagen over langzame reactietijden of dat de onderzoeksresultaten niet onmiddellijk verschijnen. Dit is een interactief prestatieprobleem.

Interactieve prestaties worden gemeten in termen van responstijd van de pagina. Dit is de tijd die het van het ontvangen van het HTTP- verzoek aan het sluiten van de reactie van HTTP neemt, die van de dossiers van het verzoeklogboek kan worden bepaald. De typische doelprestaties zijn een pagina reactietijd onder twee seconden.

**2. De verwerking van activa** een probleem van de activaverwerking is wanneer de gebruikers activa uploaden en het vergt notulen tot de activa gemakkelijk worden omgezet en in Adobe Experience Manager (AEM) DAM worden opgenomen.

De prestaties van de verwerking van bedrijfsmiddelen worden gemeten in termen van de gemiddelde voltooiingstijd van het werkstroomproces. Dit is de tijd die nodig is om het workflowproces voor het bijwerken van bedrijfsmiddelen aan te roepen tot de voltooiing ervan. Dit kan worden bepaald vanuit de gebruikersinterface van de workflowrapporten. De standaardprestaties van het doel zijn afhankelijk van de grootte en het type van de verwerkte elementen en het aantal uitvoeringen. Voorbeelden van doelprestaties kunnen als volgt zijn:

* minder dan 10 seconden voor afbeeldingen die kleiner zijn dan 1280x1280 pixels, met gebruik van standaardexpressies
* Minder dan één minuut voor afbeeldingen die kleiner zijn dan 100 MB met behulp van standaarduitvoeringen
* minder dan vijf minuten voor HD-videoclips van minder dan één minuut

**3. Downloadsnelheid** Een doorvoerprobleem is wanneer het downloaden vanaf AEM DAM lang duurt en miniaturen niet meteen worden weergegeven wanneer u naar de DAM-beheerder of de DAM-Finder bladert.

De uitvoerprestaties worden gemeten in kilobits per seconde. De typische doelprestaties zijn 300 Kbps voor 100 gelijktijdige downloads.

**4. Factoren die de prestaties van de activaverwerking beïnvloeden**

Om te kunnen schatten welke hardware u vereist om activa te verwerken, de volgende aspecten zouden moeten worden rekenschap gegeven:

* De resolutie van afbeeldingen in het aantal pixels
* De heap die aan AEM proces wordt toegewezen

De verwerkingstijd wordt bepaald door het aantal pixels in de afbeelding. Meer pixels betekent dat de verwerking langer duurt.
Het afbeeldingstype, de compressiesnelheid of de gerelateerde grootte van het bestand waarin de afbeelding is opgeslagen, hebben geen significante invloed op de algehele prestaties.

Er is vastgesteld dat heap de belangrijkste beperkende factor is. Wanneer het element groter is dan het beschikbare vrije geheugen, nemen de verwerkingsprestaties snel af.

De DAM-processen zijn zeer geschikt om in grote hoeveelheden parallel te worden uitgevoerd. Het uploaden van middelen in een batch- en multicore-processor versnelt de absolute tijd die per middel wordt besteed.

**5. Het schatten van de Vereisten van de Hardware voor het Uitvoeren van Activa - verwerking**

Voor een uitgebreide verwerking van digitale elementen zijn geoptimaliseerde hardwarebronnen nodig. De belangrijkste factoren zijn de beeldgrootte en de maximale doorvoer van verwerkte afbeeldingen.

Wijs minstens 16 GB van hoop toe en vorm het [!UICONTROL DAM Update Asset] werkschema om het [ Camera Raw pakket ](/help/assets/camera-raw.md) voor het opnemen van ruwe beelden te gebruiken.

## Het systeem begrijpen {#understanding-the-system}

Een standaard DAM-instelling bestaat uit eindgebruikers die DAM gebruiken via een taakverdelingsmechanisme. De DAM-instantie kan onderdeel zijn van een geclusterde installatie, waarbij elke DAM-instantie wordt uitgevoerd in een Java™ Virtual Machine-proces op een fysieke computer of een virtuele machine. DAM-opslag wordt geleverd door een RAID-schijf als er één computer is geïnstalleerd, of door een beheerde opslag op het netwerk als er geclusterde instellingen zijn.

De volgende legenda beschrijft de mogelijke gebieden van de prestatiesdaling met sommige oplossingen, zoals aangewezen.

**de verbinding van het Netwerk aan eind - gebruiker** Een langzame netwerkverbinding kan productiekwesties veroorzaken, en in sommige zeldzame gevallen ook latentiekwesties. Soms heeft de gebruiker een langzame verbinding van ISP, vooral in intranets. Dit is een teken van onjuiste netwerktopologie.

**het Tijdelijke Systeem van het Dossier** Een langzaam lokaal dossiersysteem kan interactieve prestatiesproblemen veroorzaken, vooral wanneer het zoeken, omdat de onderzoeksindexen op de lokale schijf worden opgeslagen. Het kan ook problemen met de middelenverwerking veroorzaken als het opdrachtregelproces wordt gebruikt.

**AEM de Vinder DAM** Interactieve prestatiesproblemen, vaak ervaren in onderzoeken worden veroorzaakt door hoog gebruik van cpu toe te schrijven aan vele gezamenlijke gebruikers of andere cpu-verbruikende processen op de zelfde instantie. U kunt de prestaties verbeteren door van virtuele machines over te schakelen op speciale machines en ervoor te zorgen dat er geen andere services op de computer worden uitgevoerd. Als een hoge processorbelasting wordt veroorzaakt door de verwerking van bedrijfsmiddelen en veel gelijktijdige gebruikers, wordt u aangeraden extra clusterknooppunten toe te voegen.

**AEM DAM van het Werkschema** Lange-lopende werkschemaprocessen tijdens activa inname veroorzaken de prestatiesproblemen van de activaverwerking. Afhankelijk van het type elementen dat wordt verwerkt, kan dit wijzen op CPU-overbenutting. De dag adviseert dat u het aantal andere processen vermindert die op het systeem lopen en het aantal beschikbare cpu&#39;s verhoogt door clusterknopen toe te voegen.

**NAS Connectiviteit** De slechte netwerkconnectiviteit aan NAS veroorzaakt interactieve prestatiesproblemen, omdat de toegang tot van nieuwe knopen tijdens activaverwerking wordt vertraagd toe te schrijven aan netwerklatentie. Ook, beïnvloedt de langzame netwerkproductie negatief productie, maar ook prestaties van de activaverwerking, omdat het laden en het bewaren van uitvoeringen wordt vertraagd.

De redenen voor slechte latentie en productie in NAS zijn netwerktopologie of NAS overgebruik door andere diensten.

{de 1} over-gebruikte netwerk-in bijlage van het 0&rbrace; Netwerk In bijlage opslagsystemen kunnen een serie van problemen veroorzaken:**&#x200B;**

* Weinig schijfruimte is een vaak aangetroffen probleem dat kan worden voorkomen door een DAM-project naar behoren te rangschikken.
* De hoge schijflatentie verspreidt zich in langzame toegangstijden voor CRX en kan in interactieve prestatiesproblemen resulteren.
* Een lage schijfdoorvoer kan leiden tot lage prestaties voor CQ5 DAM.

## Prestaties testen {#testing-for-performance}

Voor elk DAM-project moet u een systeem voor het testen van de prestaties instellen waarmee knelpunten snel kunnen worden opgespoord en opgelost. Hiervoor moet u rekening houden met de volgende controlepunten:

1. De prestatietests van begin tot eind die JMeter gebruiken - Simuleer een voorbeeld onderzoek-en-doorblader zitting om interactieve prestatiesproblemen te ontdekken.
1. De tests van de productie en van de latentie die JMeter gebruiken - Het lopen op een cliëntcomputer zorgt ervoor dat er geen topologie-verwante kwesties zijn.
1. Gestandaardiseerde tests voor de verwerking van bedrijfsmiddelen - Neem een paar voorbeeldelementen op en meet de tijd. Dit moet ook externe workflowintegratie omvatten.
1. De cpu, de Schijf, en het geheugengebruik van de monitor van elke clusterknoop.
1. CRX-diagnostiek voor lees- en schrijfprestaties om niet-verwerkingsgerelateerde problemen op te sporen.
1. De netwerklatentie en productie van de monitor van de cluster DAM aan uw NAS.
1. Test, lees, en schrijf prestaties en schijflatentie direct op NAS, indien mogelijk.

## Knelpunten aanpassen {#tweaking-bottlenecks}

De volgende prestatietwekken zijn tot dusver gebruikt in projecten:

* Selectieve uitvoering genereren: genereer alleen de uitvoeringen die u nodig hebt door voorwaarden toe te voegen aan de workflow voor het verwerken van elementen, zodat duurdere uitvoeringen alleen worden gegenereerd voor bepaalde elementen.
* Gedeelde gegevensopslag onder instanties: wanneer het lopen van laag op schijfruimte kan dit de hoeveelheid schijfruimte beduidend verminderen nodig ten koste van hogere configuratieinspanningen en het verliezen van de auto-schoonmaakbeurt van de datastore.

## Verdere lezing {#further-reading}

* [ het Analyseren langzaam en Geblokkeerde Processen ](https://helpx.adobe.com/experience-manager/kb/AnalyzeSlowAndBlockedProcesses.html)
