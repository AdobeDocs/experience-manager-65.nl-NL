---
title: Systeeminformatie weergeven
description: Leer hoe u grafieken en informatie over de server waarop AEM formulieren worden uitgevoerd, kunt bekijken.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/health_monitor
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 27a2e81c-47b0-4de8-95bd-7cb34b9450da
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: e821be5233fd5f6688507096790d219d25903892
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---

# Systeeminformatie weergeven {#view-system-information}

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

**Virtuele Machine:** versie van de Virtuele Machine van Java (JVM) op de server.

**Virtuele Leverancier van de Machine:** Producent van JVM.

**Virtuele Versie van de Machine:** JVM versieaantal

**Naam van de Machine:** Naam van de Gastheer van de server waar de AEM vormen geïnstalleerd zijn.

**Omhoog Tijd:** de tijd, in uren en notulen, dat de server in werking is gesteld.

**enkel-in-tijd Compiler:** de naam van de compiler die wordt gebruikt.

**compileert Tijd:** de hoeveelheid tijd in compileert.

**Aantal Levende Threads:** het totale aantal draden momenteel in het systeem van AEM vormen aanwezig.

**Aantal Piek van Threads:** het grootste aantal levende draden ooit geregistreerd op het systeem.

**Aantal Geladen Klassen:** Aantal klassen die in JVM worden geladen.

**Aantal Ongeladen Klassen:** Aantal klassen die van JVM worden gedesload.

**Minimale Heap:** de minimumhoeveelheid hoop die werd gebruikt.

**Maximale Heap:** de maximumhoeveelheid heap die werd gebruikt.

**de Naam van het Werkende Systeem:** de naam van het werkende systeem dat op de Server van AEM Forms loopt.

**Versie van het Werkende Systeem:** aantal van de Versie van het werkende systeem dat op de Server van AEM Forms loopt.

**Arch van het Werkende Systeem:** de werkend systeemarchitectuur die JVM loopt.

**Aantal Processors:** Het aantal bewerkers op het systeem.

**Virtuele Argumenten van de Machine:** het argument dat door JVM wordt gebruikt.

**Weg van de Klasse:** de klassenweg die door JVM wordt gebruikt.

**Weg van de Bibliotheek:** de bibliotheekweg die door JVM wordt gebruikt.

**Weg van de Klasse van de Laars:** de weg van de laarsklasse die door JVM wordt gebruikt.

**Type van Server van de Toepassing:** Type van toepassingsserver die wordt gebruikt om AEM vormen in werking te stellen.

**Versie van de Server van de Toepassing:** Aantal van de versie van de toepassingsserver die wordt gebruikt om AEM vormen in werking te stellen.

**de Leverancier van de Server van de Toepassing:** Fabrikant van de toepassingsserver die wordt gebruikt om AEM vormen in werking te stellen.

**Datum van de Installatie:** Datum (in jjjj-mm-dd formaat) dat AEM vormen geïnstalleerd was.

**AEM vorm Versie:** Versie van AEM vormen die geïnstalleerd is.

**Versie van het Reparatie:** AEM het aantal van het vormflard.

**Naam van het Gegevensbestand:** Type van gegevensbestand dat door AEM vormen wordt gebruikt.

**Versie van het Gegevensbestand:** Aantal van de Versie van het gegevensbestand dat door AEM vormen wordt gebruikt.

**Naam van de Aandrijving van het Gegevensbestand:** De naam van de bestuurder die door JVM wordt gebruikt om met het gegevensbestand te verbinden.

**Versie van de Bestuurder van het Gegevensbestand:** de versie van de bestuurder die door JVM wordt gebruikt om met het gegevensbestand te verbinden.

**sparen** knoop laat u deze systeeminformatie in een bezitsdossier opslaan.
