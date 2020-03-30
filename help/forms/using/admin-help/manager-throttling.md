---
title: Tijdelijk beheer en vertraging
seo-title: Tijdelijk beheer en vertraging
description: Dit document bevat achtergrondinformatie over Werkbeheer en instructies voor het configureren van opties voor het vertragen van werkbeheer.
seo-description: Dit document bevat achtergrondinformatie over Werkbeheer en instructies voor het configureren van opties voor het vertragen van werkbeheer.
uuid: b90998bc-e3d4-493a-9371-55ccb44da20d
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_aem_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 9a8b4e3a-f416-4dc6-a90a-9018df5c844e
translation-type: tm+mt
source-git-commit: 317fadfe48724270e59644d2ed9a90fbee95cf9f

---


# Tijdelijk beheer en vertraging{#work-manager-and-throttling}

In AEM-formulieren (en eerdere versies) werden wachtrijen voor JMS gebruikt om bewerkingen asynchroon uit te voeren. In AEM-formulieren zijn JMS-wachtrijen vervangen door Work Manager. Dit document bevat achtergrondinformatie over Werkbeheer en instructies voor het configureren van opties voor het vertragen van werkbeheer.

## Over langlevende (asynchrone) bewerkingen {#about-long-lived-asynchronous-operations}

In AEM-formulieren kunnen bewerkingen die door services worden uitgevoerd, van korte duur (synchroon) of van lange duur (asynchroon) zijn. Korte-levende verrichtingen voltooien synchroon op de zelfde draad waarvan zij werden aangehaald. Deze bewerkingen wachten op een reactie voordat u verdergaat.

Langdurige bewerkingen kunnen systemen omvatten of zelfs verder reiken dan de organisatie, bijvoorbeeld wanneer een klant een aanvraagformulier voor een lening moet invullen en indienen als onderdeel van een grotere oplossing waarin meerdere geautomatiseerde en menselijke taken zijn geïntegreerd. Dergelijke bewerkingen moeten worden voortgezet in afwachting van een reactie. Langdurige bewerkingen voeren hun onderliggende werk asynchroon uit, waardoor bronnen op een andere manier kunnen worden gebruikt in afwachting van voltooiing. In tegenstelling tot een kortstondige bewerking beschouwt de Manager van het Werk een langlevende bewerking niet als voltooid zodra deze is aangeroepen. Een externe trigger, zoals een systeem dat een andere bewerking op dezelfde service aanvraagt of een gebruiker die een formulier indient, moet worden uitgevoerd om de bewerking te voltooien.

## Info over Werkbeheer {#about-work-manager}

AEM-formulieren (en eerdere versies) gebruikten JMS-wachtrijen om bewerkingen asynchroon uit te voeren. AEM de vormen gebruiken de Manager van het Werk om asynchrone verrichtingen via beheerde draden te plannen en uit te voeren.

Asynchrone bewerkingen worden op deze manier afgehandeld:

1. De Manager van het werk ontvangt een het werkpunt voor uitvoering.
1. De Manager van het werk slaat het het werkpunt in een gegevensbestandlijst op en wijst een uniek herkenningsteken aan het het werkpunt toe. De databaserecord bevat alle informatie die nodig is om het werkitem uit te voeren.
1. De draden van de Manager van het werk trekken in het werkpunten wanneer de draden vrij worden. Alvorens in de het werkpunten te trekken, kunnen de draden controleren of de vereiste diensten zijn begonnen, of er genoeg heapgrootte om in het volgende het werkpunt te trekken is, en of er genoeg cycli van cpu zijn om het het werkpunt te verwerken. De Manager van het werk evalueert ook attributen van het het werkpunt (zoals zijn prioriteit) wanneer het plannen van zijn uitvoering.

AEM formulieren beheerders kunnen Health Monitor gebruiken om de statistieken van de Manager van het Werk, zoals het aantal werkpunten in de rij en hun status te controleren. U kunt Health Monitor ook gebruiken om het werkpunten te pauzeren, te hervatten, opnieuw te proberen of te schrappen. (Zie [Statistieken weergeven met betrekking tot Werkmanager](/help/forms/using/admin-help/view-statistics-related-manager.md#view-statistics-related-to-work-manager).)

## Opties voor het wijzigen van de snelheid van het werkbeheer configureren {#configuring-work-manager-throttling-options}

U kunt het vertragen voor de Manager van het Werk vormen, zodat de het werkpunten slechts gepland zijn wanneer er genoeg geheugenmiddelen beschikbaar zijn. U configureert vertraging door de volgende JVM-opties in te stellen in uw toepassingsserver.

<table>
 <thead>
  <tr>
   <th><p>Eigenschap</p></th>
   <th><p>Beschrijving</p></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><code> adobe.work-manager.queue-refill-interval</code></td>
   <td><p>Geeft het tijdinterval, in milliseconden, aan dat de Manager van het Werk gebruikt wanneer het controleren op nieuwe punten in zijn rij.</p><p>De waarde voor deze optie is een geheel getal. De standaardwaarde is <code>1000</code> milliseconden (1 seconde). </p><p>Als het volume van asynchrone aanroepen laag is, kunt u deze waarde verhogen. U kunt de waarde bijvoorbeeld verhogen naar een waarde tussen 2000 en 5000 (2 tot 5 seconden). </p><p>Als het volume van asynchrone aanroepen hoog is, zou de standaardwaarde voldoende moeten zijn, maar u kunt een lagere waarde gebruiken indien nodig. Als u deze waarde te veel verlaagt (bijvoorbeeld tot minder dan 50, wat resulteert in een opiniepeilingsfrequentie van 20 keer per seconde), veroorzaakt dit een aanzienlijke overhead op het systeem.</p></td>
  </tr>
  <tr>
   <td><code> adobe.workmanager.debug-mode-enabled</code></td>
   <td><p>Stel deze optie in <code>true</code> om de foutopsporingsmodus in te schakelen of op false om deze uit te schakelen. </p><p>In zuivert wijze, worden de berichten betreffende de beleidsschendingen van de Manager van het Werk en de pauze/hervat acties van de Manager van het Werk geregistreerd. Stel deze optie alleen in op true wanneer problemen worden opgelost.</p></td>
  </tr>
  <tr>
   <td><code> adobe.workmanager.memory-control.enabled</code></td>
   <td><p>Stel deze optie in <code>true</code> om vertraging in te schakelen op basis van de instellingen voor geheugenbeheer die hieronder worden beschreven, of om vertraging uit <code>false</code> te schakelen.</p></td>
  </tr>
  <tr>
   <td><code> adobe.workmanager.memory-control.high-limit</code></td>
   <td><p>Hiermee geeft u het maximale percentage geheugen op dat in gebruik kan zijn voordat de taken van de werkmanager binnenkomen.</p><p>De standaardwaarde voor deze optie is <code>95</code>. Deze waarde is bij de meeste systemen prima. Verhoog deze alleen als uw systeem de maximale capaciteit moet benutten. Maar aangezien u deze waarde verhoogt, neemt het risico van uit Geheugen kwesties ook toe.</p><p>Als u AEM-formulieren uitvoert in een geclusterde omgeving, kunt u de limietinstellingen voor geheugenbeheer op verschillende knooppunten van de cluster anders instellen. U kunt bijvoorbeeld een lagere hoge limiet hebben voor knooppunten A en B, die in het taakverdelingsmechanisme zijn geprogrammeerd voor interactief werk. En u zou hogere hoge grenzen kunnen hebben die op knopen C en D worden geplaatst, die niet door het taakverdelingsmechanisme worden gebruikt, maar voor asynchroon werk gereserveerd.</p></td>
  </tr>
  <tr>
   <td><code> adobe.workmanager.memory-control.low-limit</code></td>
   <td><p>Hiermee geeft u het maximale percentage geheugen op dat in gebruik kan zijn voordat Werkbeheer stopt met het vertragen van binnenkomende taken.</p><p>De standaardwaarde voor deze optie is <code>20</code>. Deze waarde is bij de meeste systemen prima.</p></td>
  </tr>
  <tr>
   <td><code>Dadobe.workmanager.allocate.max-batch-size</code></td>
   <td><p>Hiermee geeft u de maximale batchgrootte voor workmanager op. De standaardgrootte van de batch is 10.</p><p>Als de status van een proces in de werkmanager niet wordt bijgewerkt, zelfs nadat de taak is voltooid, stelt u de batchgrootte in op 1.</p></td>
  </tr>
 </tbody>
</table>

**Java-opties toevoegen aan JBoss**

1. Stop de JBoss-toepassingsserver.
1. Open de *[hoofdmap]*/bin/run.bat (Windows) of run.sh (Linux of UNIX) van de toepassingsserver in een editor en voeg zo nodig Java-opties toe in de indeling `-Dproperty=value`.
1. Start de server opnieuw.

**Java-opties toevoegen aan WebLogic**

1. Start de WebLogic-beheerconsole `https://[host name]:[port]/console` in een webbrowser.
1. Typ de gebruikersnaam en het wachtwoord die u voor het WebLogic Server-domein hebt gemaakt en klik op Log Under Change Center, klik op Vergrendelen en bewerken.
1. Klik onder Domeinstructuur op Omgeving > Servers en klik in het rechterdeelvenster op de naam van de beheerde server.
1. Voor het volgende scherm, klik het lusje van de Configuratie > het Begin tabel van de Server.
1. Voeg in het vak Argumenten de gewenste argumenten toe aan het einde van de huidige inhoud. Als u bijvoorbeeld Health Monitor wilt uitschakelen, voegt u het volgende toe:

   `-Dadobe.healthmonitor.enabled=false` Schakelt Health Monitor uit.

1. Klik op Opslaan en vervolgens op Wijzigingen activeren.
1. Start WebLogic managed server opnieuw.

**Java-opties toevoegen aan WebSphere**

1. Klik in de WebSphere-navigatiestructuur voor beheerconsole op Servers > Servertypen > WebSphere-toepassingsservers.
1. Klik in het rechterdeelvenster op de servernaam.
1. Klik onder Serverinfrastructuur op Java en de formulierworkflow > Procesdefinitie.
1. Klik onder Extra eigenschappen op Java Virtual Machine.
1. Typ in het vak Algemene JVM-argumenten de argumenten die u nodig hebt.
1. Klik op OK of Toepassen en klik vervolgens rechtstreeks op Opslaan in de hoofdconfiguratie.

