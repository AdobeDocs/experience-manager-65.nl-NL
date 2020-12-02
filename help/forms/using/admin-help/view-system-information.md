---
title: Systeeminformatie weergeven
seo-title: Systeeminformatie weergeven
description: Leer hoe u grafieken en informatie over de server waarop AEM formulieren worden uitgevoerd, kunt bekijken.
seo-description: Leer hoe u grafieken en informatie over de server waarop AEM formulieren worden uitgevoerd, kunt bekijken.
uuid: 983c1cc7-a8b3-48b2-a4c8-7b28a2e32537
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/health_monitor
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: d51460d9-c96c-4661-b93e-e015427878ab
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '561'
ht-degree: 0%

---


# Systeeminformatie {#view-system-information} weergeven

Het lusje van het Systeem toont middel controlerende grafieken en informatie over de server die AEM vormen in werking stelt. Om tot deze informatie, in beleidsconsole toegang te hebben, klik de Monitor van de Gezondheid in de hoger-juiste hoek van de pagina. Als u AEM formulieren uitvoert in een geclusterde omgeving, wordt de informatie weergegeven voor het knooppunt dat is geselecteerd in de lijst Server.

Klik op Opslaan als u de huidige systeeminformatie als een eigenschappenbestand wilt opslaan.

In het rechterdeelvenster van het tabblad Systeem worden grafische voorstellingen van de volgende informatie weergegeven:

* Taak- en Aantal werkplekken
* Heap en gebruik van opgetekende heap
* Niet-heap en toegewezen niet-heapgebruik

U kunt de aanwijzer over de tijdlijn slepen om waarden voor een bepaald tijdpunt op te halen.

>[!NOTE]
>
>De grafiekgegevens, de waarden van de serverinformatie, en kloktijd worden bijgewerkt om de 10 minuten. De informatie wordt niet in real time getoond.

In het linkerdeelvenster van het tabblad Systeem wordt de volgende informatie over de server of het knooppunt weergegeven:

**Virtuele machine:JVM-versie (** Java Virtual Machine) op de server.

**leverancier van virtuele machines:** fabrikant van de JVM.

**Versie virtuele machine:** JVM-versienummer

**Naam machine:** hostnaam van de server waarop AEM formulieren zijn geïnstalleerd.

**Omhoog tijd:** de tijd, in uren en minuten, dat de server is uitgevoerd.

**Just-In-Time Compiler:** de naam van de compiler die wordt gebruikt.

**Tijd compileren:** de hoeveelheid tijd die in compileert wordt doorgebracht.

**Aantal actieve draden:** het totale aantal draden dat momenteel aanwezig is in het AEM.

**Aantal Draden Piek:** Grootste aantal levende draden ooit geregistreerd op het systeem.

**Aantal geladen klassen:** aantal klassen dat in de JVM is geladen.

**Aantal verwijderde klassen:** Aantal klassen dat uit JVM is verwijderd.

**Minimale heap:** de minimale hoeveelheid heap die is gebruikt.

**Maximale heap:** de maximale hoeveelheid heap die is gebruikt.

**Naam besturingssysteem:** de naam van het besturingssysteem dat op de AEM formulierserver wordt uitgevoerd.

**Versie besturingssysteem:** versienummer van het besturingssysteem dat op de AEM formulierserver wordt uitgevoerd.

**Arch van besturingssysteem:** de architectuur van het besturingssysteem waarop de JVM wordt uitgevoerd.

**Aantal processors:** het aantal processors op het systeem.

**Argumenten van virtuele machines:** het argument dat door JVM wordt gebruikt.

**Klassepad:** het klassepad dat door de JVM wordt gebruikt.

**Bibliotheekpad:** het bibliotheekpad dat door de JVM wordt gebruikt.

**Boot Class Path:** het laarsklassenpad dat door de JVM wordt gebruikt.

**Type toepassingsserver:** type toepassingsserver dat wordt gebruikt om AEM formulieren uit te voeren.

**Versie toepassingsserver:** versienummer van de toepassingsserver die wordt gebruikt om AEM formulieren uit te voeren.

**Leverancier van toepassingsserver:** fabrikant van toepassingsserver die wordt gebruikt om AEM formulieren uit te voeren.

**Datum van installatie:** datum (in jjjj-mm-dd formaat) waarop AEM formulieren zijn geïnstalleerd.

**AEM formulieren Versie:** Versie van AEM geïnstalleerde formulieren.

**Patchversie:** AEM patchnummer formulieren.

**Databasenaam:** type database dat door AEM wordt gebruikt.

**Databaseversie:** Versienummer van de database die door AEM formulieren wordt gebruikt.

**Naam databasestation:** de naam van het stuurprogramma dat door de JVM wordt gebruikt om verbinding te maken met de database.

**Versie databasestuurprogramma:** de versie van het stuurprogramma dat door de JVM wordt gebruikt om verbinding te maken met de database.

Met de knop **Opslaan** kunt u deze systeemgegevens opslaan in een eigenschapbestand.
