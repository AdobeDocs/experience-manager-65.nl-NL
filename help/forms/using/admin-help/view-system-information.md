---
title: Systeeminformatie weergeven
seo-title: Systeeminformatie weergeven
description: Leer hoe u grafieken en informatie over de server waarop AEM-formulieren worden uitgevoerd, kunt bekijken.
seo-description: Leer hoe u grafieken en informatie over de server waarop AEM-formulieren worden uitgevoerd, kunt bekijken.
uuid: 983c1cc7-a8b3-48b2-a4c8-7b28a2e32537
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/health_monitor
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: d51460d9-c96c-4661-b93e-e015427878ab
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Systeeminformatie weergeven {#view-system-information}

Het lusje van het Systeem toont middel controlerende grafieken en informatie over de server die AEM vormen in werking stelt. Om tot deze informatie, in beleidsconsole toegang te hebben, klik de Monitor van de Gezondheid in de hoger-juiste hoek van de pagina. Als u AEM-formulieren uitvoert in een geclusterde omgeving, wordt de informatie weergegeven voor het knooppunt dat is geselecteerd in de lijst Server.

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

**** Virtuele machine: JVM-versie (Java Virtual Machine) op de server.

**** Leverancier van virtuele machines: Fabrikant van de JVM.

**** Versie virtuele machine: JVM-versienummer

**** Naam machine: Hostnaam van de server waarop AEM-formulieren zijn geïnstalleerd.

**** Omhoog tijd: De tijd, in uren en minuten, dat de server is uitgevoerd.

**** Just-In-Time Compiler: De naam van de compiler die wordt gebruikt.

**** Tijd compileren: De hoeveelheid tijd die in compilatie wordt doorgebracht.

**** Aantal actieve draden: Het totale aantal threads dat momenteel aanwezig is in het AEM-formuliersysteem.

**** Aantal draden Piek: Het grootste aantal live threads dat ooit op het systeem is opgenomen.

**** Aantal geladen klassen: Aantal klassen dat in JVM wordt geladen.

**** Aantal verwijderde klassen: Aantal klassen dat uit JVM wordt verwijderd.

**** Minimale heap: De minimale hoeveelheid heap die is gebruikt.

**** Maximale heap: De maximale hoeveelheid heap die is gebruikt.

**** Naam besturingssysteem: De naam van het besturingssysteem dat op de AEM-formulierserver wordt uitgevoerd.

**** Versie besturingssysteem: Versienummer van het besturingssysteem dat op de AEM-formulierserver wordt uitgevoerd.

**** Arch besturingssysteem: De architectuur van het besturingssysteem waarop de JVM wordt uitgevoerd.

**** Aantal processors: Het aantal processors op het systeem.

**** Argumenten voor virtuele machines: Het argument dat door de JVM wordt gebruikt.

**** Klassepad: Het klassepad dat door de JVM wordt gebruikt.

**** Bibliotheekpad: Het bibliotheekpad dat door de JVM wordt gebruikt.

**** Pad van opstartklasse: Het pad naar de opstartklasse dat door de JVM wordt gebruikt.

**** Type toepassingsserver: Type toepassingsserver waarmee AEM-formulieren worden uitgevoerd.

**** Versie toepassingsserver: Versienummer van de toepassingsserver waarmee AEM-formulieren worden uitgevoerd.

**** Leverancier toepassingsserver: Fabrikant van de toepassingsserver die wordt gebruikt om AEM-formulieren uit te voeren.

**** Datum installatie: Datum (in jjjj-mm-dd formaat) waarop AEM-formulieren zijn geïnstalleerd.

**** Versie AEM-formulieren: Versie van geïnstalleerde AEM-formulieren.

**** Patchversie: AEM-formulieren patchnummer.

**** Databasenaam: Type database dat door AEM-formulieren wordt gebruikt.

**** Databaseversie: Versienummer van de database die door AEM-formulieren wordt gebruikt.

**** Naam databasestation: De naam van het stuurprogramma dat door de JVM wordt gebruikt om verbinding te maken met de database.

**** Versie databasestuurprogramma: De versie van het stuurprogramma dat door de JVM wordt gebruikt om verbinding te maken met de database.

Met de knop **Opslaan** kunt u deze systeemgegevens opslaan in een eigenschappenbestand.
