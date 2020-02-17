---
title: Revisie opschonen
seo-title: Revisie opschonen
description: Leer hoe u de functie Revision Cleanup in AEM 6.3 gebruikt.
seo-description: Leer hoe u de functie Revision Cleanup in AEM 6.3 gebruikt.
uuid: 321f5038-44b0-4f1e-a1aa-2d29074eed70
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: deploying
discoiquuid: f03ebe60-88c0-4fc0-969f-949490a8e768
translation-type: tm+mt
source-git-commit: 2fc35bfd93585a586cb1d4e3299261611db49ba6

---


# Revisie opschonen{#revision-cleanup}

## Inleiding {#introduction}

Bij elke update van de opslagplaats wordt een nieuwe inhoudsrevisie gemaakt. Als gevolg hiervan neemt de grootte van de gegevensopslagruimte bij elke update toe. Om ongecontroleerde groei van opslagplaatsen te voorkomen, moeten oude revisies worden opgeschoond tot vrije schijfmiddelen. Deze onderhoudsfunctionaliteit wordt Revision Cleanup genoemd. Het is sinds AEM 6.0 als offline routine beschikbaar.

Met AEM 6.3 werd een online versie van deze functionaliteit genoemd Online Revision Cleanup geïntroduceerd. In vergelijking met het opschonen van een offlinerevisie waarbij de AEM-instantie moet worden afgesloten, kan Online revisie-opschoning worden uitgevoerd terwijl de AEM-instantie online is. Onlinerevisie opschonen is standaard ingeschakeld en is de aanbevolen manier om een revisie op te schonen.

**Opmerking**: [Zie de video](https://helpx.adobe.com/experience-manager/kt/platform-repository/using/revision-cleanup-technical-video-use.html) voor een inleiding en hoe u Onlinerevisie opschonen kunt gebruiken.

Het opschoningsproces van de revisie bestaat uit drie fasen: **schatting**, **verdichting** en **schoonmaken**. Schatting bepaalt of de volgende fase (compensatie) al dan niet wordt uitgevoerd op basis van hoeveel huisvuil kan worden verzameld. Tijdens de samenstellingsfase worden de segmenten en de teerdossiers herschreven verlaten om het even welke ongebruikte inhoud. De opschoonfase verwijdert vervolgens de oude segmenten, inclusief eventuele ongewenste details. In de offlinemodus kan doorgaans meer ruimte worden vrijgemaakt, omdat in de onlinemodus rekening moet worden gehouden met de werkset van AEM, waarin extra segmenten van de verzameling behouden blijven.

Raadpleeg de volgende koppelingen voor meer informatie over Revision Cleanup:

* [Onlinerevisie-opschoning uitvoeren](/help/sites-deploying/revision-cleanup.md#how-to-run-online-revision-cleanup)
* [Online revisie opschonen Veelgestelde vragen](/help/sites-deploying/revision-cleanup.md#online-revision-cleanup-frequently-asked-questions)
* [Offline revisie opschonen uitvoeren](/help/sites-deploying/revision-cleanup.md#how-to-run-offline-revision-cleanup)

Bovendien kunt u ook de [officiële documentatie van eikenhout lezen.](https://jackrabbit.apache.org/oak/docs/nodestore/segment/overview.html)

### Wanneer u de Online revisie-opruiming wilt gebruiken in tegenstelling tot de offlinerevisie-opruiming? {#when-to-use-online-revision-cleanup-as-opposed-to-offline-revision-cleanup}

**Online revisie opschonen is de aanbevolen manier om revisie op te schonen.** Offline revisie-opruiming mag alleen bij uitzondering worden gebruikt, bijvoorbeeld voordat u naar de nieuwe opslagindeling gaat of als de klantenservice van Adobe u daarom verzoekt.

## Onlinerevisie-opschoning uitvoeren {#how-to-run-online-revision-cleanup}

Onlinerevisie-opschoning is standaard geconfigureerd om automatisch één keer per dag te worden uitgevoerd op zowel AEM-auteur- als -publicatieexemplaren. U hoeft alleen het onderhoudvenster te definiëren gedurende een periode met de minste gebruikersactiviteit. U kunt de Online taak van de Opruiming van de Revisie als volgt vormen:

1. In het belangrijkste venster van AEM, ga naar **Hulpmiddelen - Verrichtingen - Dashboard - Onderhoud** of richt uw browser aan: `https://serveraddress:serverport/libs/granite/operations/content/maintenance.html`

   ![chlimage_1-90](assets/chlimage_1-90.png)

1. Houd de muisaanwijzer boven het venster **Dagelijks onderhoud** en klik op het pictogram **Instellingen** .

   ![chlimage_1-91](assets/chlimage_1-91.png)

1. Voer de gewenste waarden in (herhaling, begintijd, eindtijd) en klik op **Opslaan**.

   ![chlimage_1-92](assets/chlimage_1-92.png)

Alternatief, als u de revisie schoonmaakbeurttaak manueel wilt in werking stellen, kunt u:

1. Ga naar **Gereedschappen - Bewerkingen - Dashboard - Onderhoud** of blader rechtstreeks naar `https://serveraddress:serverport/libs/granite/operations/content/maintenance.html`
1. Klik op het venster **Dagelijks onderhoud**.
1. Houd de muisaanwijzer boven het pictogram **Revision Cleanup** .
1. Klik op **Uitvoeren**.

   ![chlimage_1-93](assets/chlimage_1-93.png)

### Online revisie opschonen na offlinerevisie opschonen uitvoeren {#running-online-revision-cleanup-after-offline-revision-cleanup}

Het opschoningsproces van de herziening herstelt oude herzieningen door generaties. Dit betekent dat telkens als u revisie in werking stelt een nieuwe generatie wordt gecreeerd en op de schijf gehouden. Er is echter een verschil tussen de twee soorten opschoning: offline revisie opschonen houdt één generatie bij terwijl online revisie opschonen twee generaties lang duurt. Dus wanneer u online revisie opschoont **na** offline revisie, wordt het volgende gewist:

1. Nadat de eerste online revisie is gereinigd, wordt de gegevensopslagruimte twee keer zo groot. Dit gebeurt omdat er nu twee generaties op schijf zitten.
1. Tijdens de volgende runtime zal de opslagplaats tijdelijk groeien terwijl de nieuwe generatie wordt gemaakt en zich vervolgens stabiliseren tot de grootte die het had na de eerste run, terwijl het proces voor online revisie-opruiming de vorige generatie opruimt.

Houd er ook rekening mee dat elke generatie afhankelijk van het type en het aantal bewerkingen een andere grootte kan hebben dan de vorige, zodat de uiteindelijke grootte van de afzonderlijke bewerkingen kan verschillen.

Daarom wordt aanbevolen de schijf minstens twee of drie keer groter te maken dan de aanvankelijk geschatte grootte van de opslagplaats.

## Compactiemodi voor volledig en op het spoor {#full-and-tail-compaction-modes}

**AEM 6.5** introduceert **twee nieuwe wijzen** voor de **samenstellingsfase** van het Online proces van de Overgang van de Revisie:

* In de **volledige compactiemodus** worden alle segmenten en teerbestanden in de gehele opslagruimte opnieuw genoteerd. De volgende opschoningsfase kan zo de maximumhoeveelheid huisvuil over de bewaarplaats verwijderen. Aangezien volledige compactie de gehele opslagplaats beïnvloedt, vereist het een aanzienlijke hoeveelheid systeembronnen en tijd om te voltooien. Volledige compactie komt overeen met de verdichtingsfase in AEM 6.3.
* In de modus **Sluitingscompositie** worden alleen de meest recente segmenten en teerbestanden in de opslagplaats herschreven. De meest recente segmenten en teerbestanden zijn de segmenten die zijn toegevoegd sinds de laatste keer dat de volledige of eindcompressie is uitgevoerd. De volgende opschoningsfase kan dus alleen het afval verwijderen dat zich in het recente deel van de opslagplaats bevindt. Aangezien de staartcompensatie slechts een deel van de bewaarplaats beïnvloedt vereist het aanzienlijk minder systeemmiddelen en tijd om te voltooien dan volledige compensatie.

Deze verrekeningsmodi vormen een afweging tussen efficiëntie en hulpbronnengebruik: hoewel de &quot;tail compaction&quot; minder effectief is, heeft het ook minder invloed op de normale werking van het systeem. Daarentegen is volledige compressie effectiever, maar heeft deze een grotere invloed op de normale werking van het systeem.

AEM 6.5 introduceert ook een efficiënter mechanisme voor het dedupliceren van inhoud tijdens het comprimeren, waardoor de hoeveelheid schijfruimte van de opslagplaats nog verder wordt verminderd.

De twee onderstaande grafieken zijn de resultaten van interne laboratoriumtests die de vermindering van de gemiddelde uitvoeringstijden en de gemiddelde voetafdruk op schijf in AEM 6.5 ten opzichte van AEM 6.3 aantonen:

![onrc-duration-6_4vs63](assets/onrc-duration-6_4vs63.png) ![segmentstore-6_4vs63](assets/segmentstore-6_4vs63.png)

### Hoe te om Volledige en Samenstelling van het Lusje te vormen {#how-to-configure-full-and-tail-compaction}

Bij de standaardconfiguratie wordt op weekdagen een verdichtingseffect en op zondag een volledige vereffening uitgevoerd. De standaardconfiguratie kan worden veranderd door de nieuwe configuratiewaarde `full.gc.days` van de `RevisionCleanupTask`[onderhoudstaak](/help/sites-deploying/revision-cleanup.md#how-to-run-online-revision-cleanup)te gebruiken.

Wanneer u de `full.gc.days` waarde configureert, moet u er rekening mee houden dat de volledige compressie wordt uitgevoerd tijdens de dag(en) die in de waarde en de staart zijn gedefinieerd, tijdens de dagen die niet in de waarde zijn gedefinieerd. Als u bijvoorbeeld volledige compressie configureert om op zondag te worden uitgevoerd, wordt de compressie van de staart van maandag tot en met zaterdag uitgevoerd. Als, bijvoorbeeld, u volledige compilatie vormt om elke dag van de week in werking te stellen dan zal de staartcompensatie niet bij allen lopen.

Houd er ook rekening mee dat:

* **De verbinding** van de staart is minder effectief en het heeft minder effect op normale systeemverrichtingen. Het is dus de bedoeling dat het gedurende werkdagen wordt uitgevoerd.
* **Volledige compactie** is effectiever, maar heeft ook een grotere invloed op normale systeembewerkingen. Het is dus bedoeld om buiten werkdagen te worden gebruikt.
* Zowel de staartvervorming als de volledige vervorming zouden moeten worden gepland om tijdens buiten piekuren te lopen.

### Problemen oplossen {#troubleshooting}

Houd rekening met het volgende wanneer u de nieuwe compressiemodi gebruikt:

* U kunt bijvoorbeeld de invoer-/uitvoeractiviteit (I/O) controleren: I/O-bewerkingen, CPU die wacht op IO, limiet van wachtrijgrootte vastleggen. Dit helpt bepalen of het systeem I/O verbindend wordt en vereist upsizing.
* De `RevisionCleanupTaskHealthCheck` code geeft de algemene gezondheidsstatus van de Online revisie-opruiming aan. Deze methode werkt op dezelfde manier als in AEM 6.3 en maakt geen onderscheid tussen volledige en eindcompressie.
* De logberichten bevatten relevante informatie over de compactiemodi. Bijvoorbeeld, wanneer de Online Opruiming van de Revisie begint, zullen de overeenkomstige logboekberichten op de samenstellingswijze wijzen. Bovendien, in sommige hoekgevallen, zal het systeem aan volledige compressie terugkeren wanneer het werd gepland om een staartcompensatie in werking te stellen en de logboekberichten zullen op deze verandering wijzen. De hieronder logboeksteekproeven wijzen op de samenstellingswijze en de verandering van staart in volledige compressie:

```
TarMK GC: running tail compaction
TarMK GC: no base state available, running full compaction instead
```

### Bekende beperkingen {#known-limitations}

In sommige gevallen vertraagt het opruimen door het afwisselen tussen de eindmodus en de volledige-compressiemodi. Meer in het bijzonder, zal de bewaarplaats na een volledige compensatie groeien (het zal in grootte verdubbelen). De extra ruimte wordt teruggezet in de volgende &#39;tail&#39;-compactie, wanneer de opslagplaats onder de pre-volledige compactiegrootte daalt. Parallelle uitvoering van onderhoudstaken moet ook worden vermeden.

**Het wordt aanbevolen de schijf minstens twee of drie keer groter te maken dan de aanvankelijk geschatte grootte van de opslagplaats.**

## Online revisie opschonen Veelgestelde vragen {#online-revision-cleanup-frequently-asked-questions}

### AEM 6.5-upgradeoverwegingen {#aem-upgrade-considerations}

<table>
 <tbody>
  <tr>
   <td>Vragen </td>
   <td>Antwoorden</td>
  </tr>
  <tr>
   <td>Wat zou ik van op de hoogte moeten zijn wanneer ik aan AEM 6.5 opwaardeer?</td>
   <td><p>Het persistentieformaat van TarMK zal met AEM 6.5 veranderen. Deze wijzigingen vereisen geen proactieve migratiestap. Bestaande opslagruimten zullen door een het rollen migratie gaan, die voor de gebruiker transparant is. Het migratieproces wordt gestart de eerste keer dat AEM 6.5 (of verwante hulpmiddelen) toegang krijgt tot de opslagplaats.</p> <p><strong>Zodra de migratie naar de AEM 6.5 persistence-indeling is gestart, kan de gegevensopslagruimte niet terugkeren naar de vorige AEM 6.3 persistence-format.</strong></p> </td>
  </tr>
 </tbody>
</table>

### Migreren naar eiken segmentteer {#migrating-to-oak-segment-tar}

<table>
 <tbody>
  <tr>
   <td><strong>Vragen</strong></td>
   <td><strong>Antwoorden</strong></td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Waarom moet ik de repository migreren?</strong></td>
   <td><p>In AEM 6.3 waren wijzigingen in het opslagformaat nodig, vooral om de prestaties en de doeltreffendheid van Online Revision Cleanup te verbeteren. Deze wijzigingen zijn niet compatibel met oudere versies en opslagruimten die zijn gemaakt met het oude eikensegment (AEM 6.2 en lager) moeten worden gemigreerd.</p> <p>Extra voordelen van het wijzigen van de opslagindeling:</p>
    <ul>
     <li>Betere schaalbaarheid (geoptimaliseerde segmentgrootte).</li>
     <li>Snellere <a href="/help/sites-administering/data-store-garbage-collection.md" target="_blank">afvalophaling</a>voor gegevensopslag.<br /> </li>
     <li>Grondwerkzaamheden voor toekomstige verbeteringen.</li>
    </ul> </td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Wordt de vorige opmaak van de Tar nog steeds ondersteund?</strong></td>
   <td>Alleen de nieuwe Oak Segment Tar wordt ondersteund met AEM 6.3.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Is migratie van inhoud altijd verplicht?</strong></td>
   <td>Ja. Tenzij u met een nieuw exemplaar begint, zult u altijd de inhoud moeten migreren.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Kan ik upgraden naar 6.3 en de migratie later uitvoeren (bijvoorbeeld met een ander onderhoudsvenster)?</strong></td>
   <td>Nee, zoals hierboven is uiteengezet, is migratie van inhoud verplicht.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Kan downtime tijdens migreren worden voorkomen?</strong></td>
   <td>Nee. Dit is een eenmalige inspanning die niet op een lopende instantie kan worden gedaan.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Wat gebeurt er als ik per ongeluk tegen de verkeerde gegevensopslagindeling looppas?</strong></td>
   <td>Als u probeert om de eiken-segmentmodule tegen een eak-segment-teer bewaarplaats (of vice versa) in werking te stellen, zal het opstarten met een <em>IllegalStateException</em> met het bericht "Ongeldig segmentformaat"ontbreken. Er treedt geen gegevensbeschadiging op.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Zal een herindex van de zoekindexen noodzakelijk zijn?</strong></td>
   <td>Nee. Bij het migreren van een eikensegment naar een eikensegment worden wijzigingen aangebracht in de containerindeling. De ingesloten gegevens worden niet beïnvloed en worden niet gewijzigd.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Hoe kan de verwachte schijfruimte die tijdens en na de migratie nodig is het beste worden berekend?</strong></td>
   <td>De migratie is gelijk aan het opnieuw maken van de segmentstore in de nieuwe indeling. Dit kan worden gebruikt om de extra schijfruimte te schatten nodig tijdens migratie. Na de migratie kan de oude segmentwinkel worden verwijderd om ruimte vrij te maken.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Hoe kan de duur van de migratie het best worden ingeschat?</strong></td>
   <td>De prestaties van de migratie kunnen enorm worden verbeterd als de <a href="/help/sites-deploying/revision-cleanup.md#how-to-run-offline-revision-cleanup">off-line revisie schoonmaakbeurt</a> voorafgaand aan de migratie wordt uitgevoerd. Alle klanten wordt geadviseerd om het als eerste vereiste van het verbeteringsproces uit te voeren. In het algemeen, zou de duur van de migratie aan de duur van de off-line revisie schoonmaakbeurttaak gelijkaardig moeten zijn, veronderstellend dat de off-line revisie schoonmaakbeurttaak vóór de migratie is uitgevoerd.</td>
   <td> </td>
  </tr>
 </tbody>
</table>

### Onlinerevisie opschonen uitvoeren {#running-online-revision-cleanup}

<table>
 <tbody>
  <tr>
   <td><strong>Vragen</strong></td>
   <td><strong>Antwoorden</strong></td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Hoe vaak moet Onlinerevisie opschonen worden uitgevoerd?</strong></td>
   <td>Eenmaal per dag. Dit is de standaardconfiguratie in het Dashboard van Verrichtingen.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Hoe kan ik de begintijd van de Online het onderhoudstaak van de Opruiming van de Revisie vormen?</strong></td>
   <td>Zie de sectie <a href="/help/sites-deploying/revision-cleanup.md#how-to-run-online-revision-cleanup">Online revisie-opruiming</a> uitvoeren. </td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Is er een maximumfrequentie die niet mag worden overschreden voor Online revisie-opschoning?</strong></td>
   <td>Het wordt aanbevolen om online revisie-opschoning eenmaal per dag uit te voeren, zoals standaard is geconfigureerd.<br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Wat zijn de belangrijkste indicatoren die de frequentie bepalen waarop Online de Opruiming van de Revisie zou moeten worden in werking gesteld?</strong></td>
   <td>Er is geen behoefte om de frequentie te bepalen aangezien de Online Opruiming van de Revisie als onderhoudstaak wordt gevormd en het automatisch elke dag loopt.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Waarom wordt bij Online revisie-opruiming geen ruimte vrijgemaakt wanneer deze voor het eerst wordt uitgevoerd?</strong></td>
   <td>Met Online revisie opschonen worden oude revisies door generaties teruggezet. Elke keer dat de revisie wordt opgeschoond, wordt een nieuwe generatie gegenereerd. Alleen de inhoud die minstens twee generaties oud is, zal worden teruggevorderd, wat betekent dat er voor het eerst niets terug te vorderen is.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Waarom wint de eerste Online Opruiming van de Revisie geen ruimte terug wanneer die na de Offline Opruiming van de Revisie in werking wordt gesteld?</strong></td>
   <td><p>Met Offline revisie Cleanup wordt alles geherclaimd, behalve de nieuwste generatie in vergelijking met de nieuwste twee generaties voor online revisie Cleanup. In het geval van een nieuwe opslagplaats zal Online Revision Cleanup geen ruimte terugwinnen wanneer deze voor de eerste keer wordt uitgevoerd na de Offline Revision Cleanup omdat er geen generatie oud genoeg is om te worden teruggewonnen.</p> <p>Lees ook de sectie "Online revisie-opruiming uitvoeren na offlinerevisie opruimen" van <a href="/help/sites-deploying/revision-cleanup.md#how-to-run-online-revision-cleanup">dit hoofdstuk</a>.</p> </td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Zouden Auteur en Publiceren typisch verschillende Online vensters van de Overgang van de Herziening hebben?</strong></td>
   <td>Dit hangt van kantooruren en de verkeerspatronen van de klant online aanwezigheid af. De onderhoudsvensters moeten buiten de hoofdproductietijden worden geconfigureerd om de beste schoonmaakefficiëntie te waarborgen. Voor meerdere AEM-publicatie-instanties (TarMK Farm) moeten de onderhoudsvensters voor Online revisie Cleanup worden gefaseerd.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Zijn er om het even welke eerste vereisten alvorens Online de Opruiming van de Revisie in werking te stellen?</strong></td>
   <td><p>Onlinerevisie-opschoning is alleen beschikbaar in versies van AEM 6.3 en hoger. Als u een oudere versie van AEM gebruikt, moet u ook migreren naar de nieuwe <a href="/help/sites-deploying/revision-cleanup.md#migrating-to-oak-segment-tar">Oak-segmentmarkering</a>.</p> </td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Wat zijn de factoren die de duur van de Online Opruiming van de Revisie bepalen?</strong></td>
   <td>De factoren zijn:<br />
    <ul>
     <li>Grootte opslagplaats</li>
     <li>Laden op het systeem (aanvragen per minuut, schrijven specifiek bewerkingen)</li>
     <li>Activiteitspatroon (lezen versus schrijven)</li>
     <li>Hardwarespecificaties (CPU-prestaties, geheugen, IOPS)</li>
    </ul> </td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Kunnen auteurs nog steeds werken terwijl Online revisie Cleanup wordt uitgevoerd?</strong></td>
   <td>Ja, Online Revision Cleanup kan gelijktijdige schrijvingen verwerken. Onlinerevisie opschonen werkt echter sneller en efficiënter zonder gelijktijdige schrijftransacties. Het wordt geadviseerd om de Online het onderhoudstaak van de Opruiming van de Revisie aan een vrij rustige tijd zonder veel verkeer te plannen.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Wat zijn de minimumvereisten voor schijfruimte en heapgeheugen wanneer het runnen van Online Herziening Opschoning?</strong></td>
   <td><p>De schijfruimte wordt voortdurend gecontroleerd tijdens het online opschonen van revisies. Als de beschikbare schijfruimte onder een kritieke waarde daalt, wordt het proces geannuleerd. De kritieke waarde is 25% van de huidige schijfvoetafdruk van de opslagplaats en kan niet worden geconfigureerd.</p> <p><strong>Het wordt aanbevolen de schijf minstens twee of drie keer groter te maken dan de aanvankelijk geschatte grootte van de opslagplaats.</strong></p> <p>De vrije heapruimte wordt voortdurend gecontroleerd tijdens het schoonmaakproces. Als de vrije heapruimte onder een kritieke waarde daalt, wordt het proces geannuleerd. De kritieke waarde wordt gevormd door org.apache.jackrabbit.segment.SegmentNodeStoreService#MEMORY_THRESHOLD. De standaardwaarde is 15%.</p> <p>Aanbevelingen voor minimale heapgrootte van de compacte versie worden niet gescheiden van de aanbevelingen voor het vergroten of verkleinen van het AEM-geheugen. In de regel: <strong>Als een AEM-instantie groot genoeg is om de gebruiksgevallen en de verwachte lading daarop aan te kunnen, krijgt het opschoonproces voldoende geheugen.</strong></p> </td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Wat is het verwachte effect op de prestaties tijdens het uitvoeren van Online Revision Cleanup?</strong></td>
   <td>Online Revision Cleanup is een achtergrondproces dat tegelijkertijd leest van en schrijft naar de opslagplaats voor normale systeembewerkingen. Het kan met name nodig zijn om gedurende korte tijd exclusieve toegang tot de opslagplaats te verkrijgen, zodat andere draden niet naar de opslagplaats kunnen schrijven.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Hoe lang wordt de Online Correctie van de Revisie verwacht om te lopen?</strong></td>
   <td>Het mag niet langer dan twee uur duren voordat de uitvoering plaatsvindt volgens de laatste prestatietests die we intern hebben uitgevoerd.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Wat moet u doen als het opruimen van online revisies langer duurt?</strong></td>
   <td>
    <ul>
     <li>Zorg ervoor dat het dagelijks wordt uitgevoerd.<br /> </li>
     <li>Zorg ervoor dat het tijdens minimale opslagruimteactiviteiten wordt uitgevoerd door de onderhoudsvensters in het Dashboard van Verrichtingen dienovereenkomstig te configureren.</li>
     <li>Schaal de systeembronnen (CPU, geheugen, I/O) op.</li>
    </ul> </td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Wat gebeurt als de Online Opruiming van de Revisie gevormde Vensters van het Onderhoud overschrijdt?</strong></td>
   <td>Zorg ervoor dat andere onderhoudstaken de uitvoering ervan niet vertragen. Dit zou het geval kunnen zijn als meer onderhoudstaken dan Online Revision Cleanup binnen het zelfde onderhoudsvenster worden uitgevoerd. Merk op dat de onderhoudstaken opeenvolgend zonder een configureerbare orde worden uitgevoerd.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Waarom wordt afvalophaling overgeslagen?</strong></td>
   <td><p>Herzieningsopschoning is gebaseerd op een schattingsfase om te bepalen of er voldoende afval is om te worden schoongemaakt. De schatter vergelijkt de huidige grootte met de grootte van de bewaarplaats nadat het laatst werd vergeleken. Als de grootte de gevormde delta overschrijdt, zal de schoonmaakbeurt lopen. De delta van de grootte wordt geplaatst op 1 GB. Dit betekent in feite dat als de grootte van de opslagplaats sinds de laatste schoonmaakbeurt niet met 1 GB is toegenomen, de nieuwe herhaling van de revisie wordt overgeslagen. </p> <p>Hieronder staan de relevante logitems voor de ramingsfase:</p>
    <ul>
     <li>Revision GC wordt uitgevoerd: De delta van de <em>Grootte is N% of N/N (N/N bytes), zodat lopende compressie</em></li>
     <li>Revision GC wordt <strong>niet</strong> uitgevoerd: De delta van de <em>Grootte is N% of N/N (N/N bytes), zodat slaat nu compressie over</em></li>
    </ul> </td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Is het mogelijk om de automatische compressie veilig af te breken als de invloed op de prestaties te groot is?</strong></td>
   <td>Ja. Aangezien AEM 6.3 veilig kan worden tegengehouden via het venster van de Taak van het Onderhoud binnen het Dashboard van Verrichtingen of via JMX.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Als de instantie AEM tijdens een geplande opschoontaak wordt afgesloten, veilig afbreekt het proces, of wordt de sluiting geblokkeerd tot de compensatie heeft gebeëindigd?</strong></td>
   <td>Revision Cleanup wordt onderbroken en de repository wordt veilig afgesloten.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Wat gebeurt er als het systeem vastloopt tijdens het opschonen van de online revisie?</strong></td>
   <td>In dergelijke gevallen bestaat er geen risico op gegevensbeschadiging. De afvalrestanten worden opgeschoond door een volgende run.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Wat is de impact van het niet uitvoeren van Online Revision Cleanup?</strong></td>
   <td>Verslechtering van prestaties in de loop der tijd.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Welke herzieningen worden verzameld?</strong></td>
   <td>Standaard verzamelt de Online revisie-opruiming alleen revisies die minstens 24 uur oud zijn.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Wat gebeurt er in het geval van te veel interferentie van gelijktijdig schrijven naar de dataopslag?</strong></td>
   <td><p>Als er schrijfgelijktijdig op het systeem is, zou de online revisie schoonmaakbeurt exclusieve schrijftoegang kunnen vereisen om de veranderingen aan het eind van een samenstellingscyclus te kunnen begaan. Het systeem zal in <strong>forceCompact wijze</strong>, zoals meer gedetailleerd in de <a href="https://jackrabbit.apache.org/oak/docs/nodestore/segment/overview.html" target="_blank">eiken documentatie</a>wordt verklaard. Tijdens forceren compact, wordt een exclusieve schrijfslot verworven om de veranderingen definitief te begaan zonder enige gelijktijdige schrijffout. Om het effect op responstijden te beperken, kan een time-outwaarde worden gedefinieerd. Deze waarde wordt standaard ingesteld op 1 minuut, wat betekent dat als het compacte effect niet binnen 1 minuut wordt voltooid, het verrekeningsproces wordt afgebroken ten gunste van gelijktijdige vastleggingen.</p> <p>De duur van het forceren is afhankelijk van de volgende factoren:</p>
    <ul>
     <li>hardware: specifiek IOPS. De duur neemt af met meer IOPS.</li>
     <li>grootte segmentwinkel: de duur neemt toe met de grootte van de segmentopslag.</li>
    </ul> </td>
   <td> </td>
  </tr>
  <tr>
   <td><p><strong>Hoe wordt de Online Opruiming van de Revisie uitgevoerd op een reserve instantie?</strong></p> </td>
   <td><p>In een koude stand-by opstelling, slechts moet de primaire instantie worden gevormd om Online Correctie van de Revisie in werking te stellen. Voor de stand-by instantie hoeft de Online Revision Cleanup niet specifiek te worden gepland.</p> <p>De bijbehorende bewerking op een stand-byinstantie is de automatische opschoning. Dit komt overeen met de opschoningsfase van de Online revisie-opschoning. De automatische opschoning wordt uitgevoerd op de reservekopie na de uitvoering van de Online revisie-opschoning op de primaire instantie.</p> <p>Schatings- en samenstellingsfasen worden niet uitgevoerd op een stand-byinstantie.</p> </td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Kan offlinerevisie opschonen meer schijfruimte vrijmaken dan online revisie opschonen?</strong></td>
   <td><p>Met Offline revisie-opruiming kunt u oude revisies direct verwijderen, terwijl bij Online revisie-opruiming rekening moet worden gehouden met oude revisies waarnaar nog steeds wordt verwezen door de toepassingsstapel. Het eerste kan zo afval agressiever verwijderen dan het laatste waar het effect wordt geamortiseerd tijdens een paar afvalophalingscycli.</p> <p>Lees ook de sectie "Online revisie-opruiming uitvoeren na offlinerevisie opruimen" van <a href="/help/sites-deploying/revision-cleanup.md#how-to-run-online-revision-cleanup">dit hoofdstuk</a>.</p> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Eventuele overwegingen met betrekking tot bestandsbewerkingen die zijn toegewezen aan het geheugen?</td>
   <td>
    <ul>
     <li><strong>In Windows-omgevingen</strong>wordt de reguliere bestandstoegang altijd afgedwongen, zodat in geheugen toegewezen toegang niet wordt gebruikt. Als algemeen advies, zou al beschikbaar RAM aan de heap moeten worden toegewezen en de segmentcachegrootte zou moeten worden verhoogd. U verhoogt segmentCache door de segmentCache.size optie aan org.apache.jackrabbit.segment.SegmentNodeStoreService.config (bijvoorbeeld, segmentCache.size=20480) toe te voegen. Vergeet niet wat RAM-geheugen over te houden voor het besturingssysteem en andere processen.</li>
     <li><strong>In andere omgevingen</strong>dan Windows vergroot u het fysieke geheugen om de geheugentoewijzing van de opslagplaats te verbeteren.</li>
    </ul> </td>
   <td>
    <ul>
     <li> </li>
    </ul> </td>
  </tr>
 </tbody>
</table>

### Onlinerevisie controleren {#monitoring-online-revision-cleanup}

<table>
 <tbody>
  <tr>
   <td><strong>Wat moet worden gecontroleerd tijdens Online Revision Cleanup?</strong></td>
   <td>
    <ul>
     <li>De schijfruimte moet worden bewaakt wanneer Online revisie-opschoning is ingeschakeld. De opschoonbewerking wordt niet uitgevoerd of wordt voortijdig beëindigd wanneer er onvoldoende schijfruimte is.</li>
     <li>Controleer de logboeken op de voltooiingstijd van Online Revision Cleanup. Het mag niet langer dan 2 uur duren.</li>
     <li>Aantal controlepunten. Als er meer dan 3 controlepunten zijn wanneer de samenstellingslooppas het wordt geadviseerd om de controlepunten schoon te maken.</li>
    </ul> </td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Hoe te om te controleren als Online Correctie van de Revisie met succes heeft voltooid?</strong></td>
   <td><p>U kunt controleren of de Online revisie-opruiming is voltooid door de logbestanden te controleren.</p> <p>"<code>TarMK GC #{}: compaction completed in {} ({} ms), after {} cycles</code>" betekent bijvoorbeeld dat de samenstellingsstap met succes is voltooid, tenzij deze wordt voorafgegaan door het bericht "<code>TarMK GC #{}: compaction gave up compacting concurrent commits after {} cycles</code>", wat betekent dat er te veel gelijktijdige lading is.</p> <p>Er is dus een bericht "<code>TarMK GC #{}: cleanup completed in {} ({} ms</code>" voor de geslaagde voltooiing van de opschoningsstap.</p> </td>
   <td><p> </p> </td>
  </tr>
  <tr>
   <td><strong>Waar kunnen wij de statistieken van de laatste Online Uitvoeren van de Herziening vinden?</strong></td>
   <td><p>De status, de vooruitgang en de statistieken worden blootgesteld via JMX (<code>SegmentRevisionGarbageCollection</code> MBean). Lees de <code>SegmentRevisionGarbageCollection</code> volgende alinea <a href="https://jackrabbit.apache.org/oak/docs/nodestore/segment/overview.html#monitoring-via-jmx" target="_blank">voor meer informatie over de</a>MBean.</p> <p>De voortgang kan worden bijgehouden via het <code>EstimatedRevisionGCCompletion</code> kenmerk van het <code>SegmentRevisionGarbageCollection MBean.</code></p> <p>U kunt een verwijzing van MBean verkrijgen gebruikend <code>ObjectName org.apache.jackrabbit.oak:name="Segment node store revision garbage collection",type="SegmentRevisionGarbageCollection”</code>.</p> <p>Merk op dat de statistieken slechts beschikbaar zijn sinds het laatste systeembegin. De functie voor externe bewaking kan worden gebruikt om de gegevens buiten de AEM-uptime te houden. Zie <a href="/help/sites-administering/operations-dashboard.md#monitoring-with-nagios" target="_blank">de documentatie van AEM voor het vastmaken van gezondheidscontroles aan Nagios als voorbeeld voor een extern controlehulpmiddel</a>.</p> </td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Wat zijn relevante logbestandvermeldingen?</strong></td>
   <td>
    <ul>
     <li>Onlinerevisie-opschoning is gestart/gestopt
      <ul>
       <li>De online Overzichtsopruiming bestaat uit drie fasen: schatting, verdichting en schoonmaak. Schatting kan compaction en schoonmaakbeurt dwingen om over te slaan als de bewaarplaats niet genoeg huisvuil bevat. In de meest recente versie van AEM markeert het bericht "<code>TarMK GC #{}: estimation started</code>" het begin van de schatting, "<code>TarMK GC #{}: compaction started, strategy={}</code>" het begin van de compilatie en "T<code>arMK GC #{}: cleanup started. Current repository size is {} ({} bytes</code>" het begin van de opschoonbewerking.</li>
      </ul> </li>
     <li>Schijfruimte die wordt opgeschoond door de revisie
      <ul>
       <li>De ruimte wordt slechts teruggewonnen wanneer de schoonmaakfase voltooit. De voltooiing van de schoonmaakfase wordt duidelijk door het logboekbericht "T<code>arMK GC #{}: cleanup completed in {} ({} ms</code>". De grootte van de opschoonbewerking na de opschoonbewerking is {} ({} bytes) en de ruimte die is teruggezet {} ({} bytes). Dikte/diepte van compactiemap is {}/{} ({} bytes/{}).".</li>
      </ul> </li>
     <li>Er is een probleem opgetreden tijdens het opschonen van de revisie
      <ul>
       <li>Er zijn vele mislukkingsvoorwaarden, worden elk duidelijk door WARN of FOUT logboekberichten die met "TarMK GC"beginnen.</li>
      </ul> </li>
    </ul> <p>Zie ook de onderstaande sectie <a href="/help/sites-deploying/revision-cleanup.md#troubleshooting-based-on-error-messages">Problemen oplossen op basis van foutberichten</a> .</p> </td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Hoe te om te controleren hoeveel ruimte werd teruggewonnen nadat de Online Opruiming van de Revisie heeft voltooid?</strong></td>
   <td>Er staat een bericht in het logbestand aan het einde van de opschooncyclus: "<code>TarMK GC #3: cleanup completed</code>" dat de grootte van de opslagplaats en de hoeveelheid geregenereerd afval omvat.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Hoe kan de integriteit van de opslagplaats worden gecontroleerd nadat de Online Revision Cleanup is voltooid?</strong></td>
   <td><p>Er is geen integriteitscontrole voor de repository nodig nadat de Online Revision Cleanup is uitgevoerd. </p> <p>U kunt echter de volgende handelingen uitvoeren om de status van de opslagplaats te controleren na het opschonen:</p>
    <ul>
     <li>Een <a href="/help/sites-deploying/consistency-check.md" target="_blank">doorreiscontrole in de repository</a></li>
     <li>Gebruik het gereedschap voor het uitvoeren van de eik nadat het opschoonproces is voltooid om te controleren op inconsistenties. Raadpleeg de documentatie bij <a href="https://github.com/apache/jackrabbit-oak/blob/trunk/oak-doc/src/site/markdown/nodestore/segment/overview.md#check" target="_blank">Apache voor meer informatie over hoe u dit kunt doen.</a> U hoeft AEM niet uit te schakelen om het gereedschap uit te voeren.</li>
    </ul> </td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Hoe te om te ontdekken als de Online Opruiming van de Revisie heeft ontbroken en welke stappen zijn om te herstellen?</strong></td>
   <td>De voorwaarden van de mislukking worden duidelijk door WARN of FOUTlogboekberichten die met "TarMK GC"beginnen. Zie ook de onderstaande sectie <a href="/help/sites-deploying/revision-cleanup.md#troubleshooting-based-on-error-messages">Problemen oplossen op basis van foutberichten</a> .</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Welke informatie wordt in de Controle van de Gezondheid van de Reinigingscontrole van de Revisie blootgesteld? Hoe en wanneer dragen ze bij aan de statusniveaus van de kleurcodering? </strong></td>
   <td><p>De Revision Clean-up Health Check maakt deel uit van het <a href="/help/sites-administering/operations-dashboard.md#health-reports" target="_blank">Operations-dashboard</a>.<br /> </p> <p>De status wordt <strong>GROEN</strong> als de laatste uitvoering van de onderhoudstaak voor het opschonen van de online revisie met succes is voltooid.</p> <p>Het wordt <strong>GEEL</strong> als de onderhoudstaak voor het opschonen van de online revisie eenmaal is geannuleerd.<br /> </p> <p>Het zal <strong>ROOD</strong> zijn als de Online het onderhoudstaak van de Opruiming van de Revisie driemaal in een rij werd geannuleerd. <strong>In dit geval is handmatige interactie vereist</strong> of wordt het opschonen van de online revisie waarschijnlijk opnieuw mislukt. Lees de onderstaande sectie <a href="/help/sites-deploying/revision-cleanup.md#troubleshooting-online-revision-cleanup">Problemen oplossen</a> voor meer informatie.<br /> </p> <p>De status van de Health Check wordt opnieuw ingesteld nadat het systeem opnieuw is opgestart. Dus een nieuw opgestarte instantie zal een groene status tonen op de Revision Cleanup Health Check. De functie voor externe bewaking kan worden gebruikt om de gegevens buiten de AEM-uptime te houden. Zie <a href="/help/sites-administering/operations-dashboard.md#monitoring-with-nagios">de documentatie van AEM voor het vastmaken van gezondheidscontroles aan Nagios als voorbeeld voor een extern controlehulpmiddel</a>.</p> </td>
   <td> </td>
  </tr>
  <tr>
   <td><p><strong>Hoe te om Automatische Opschoning op een reserve instantie te controleren?</strong></p> </td>
   <td><p>De status, de vooruitgang en de statistieken worden blootgesteld via JMX door <code>SegmentRevisionGarbageCollection</code> MBean te gebruiken. Zie ook de volgende <a href="https://jackrabbit.apache.org/oak/docs/nodestore/segment/overview.html#monitoring-via-jmx" target="_blank">documentatie</a>voor eikenhout. </p> <p>U kunt een verwijzing van MBean verkrijgen door <code>ObjectName org.apache.jackrabbit.oak:name="Segment node store revision garbage collection",type="SegmentRevisionGarbageCollection”</code>te gebruiken.</p> <p>Merk op dat de statistieken beschikbaar slechts sinds het laatste systeembegin zijn. De functie voor externe bewaking kan worden gebruikt om de gegevens buiten de AEM-uptime te houden. Zie ook <a href="/help/sites-administering/operations-dashboard.md#monitoring-with-nagios" target="_blank">de AEM-documentatie voor het koppelen van gezondheidscontroles aan Nagios als voorbeeld voor een extern monitoringgereedschap</a>.</p> <p>De logboekdossiers kunnen ook worden gebruikt om de status, de vooruitgang en de statistieken van Automatische Opschoning te controleren.</p> </td>
   <td> </td>
  </tr>
  <tr>
   <td><p><strong>Wat moet tijdens Automatische Opschoning op een reserve instantie worden gecontroleerd?</strong></p> </td>
   <td>
    <ul>
     <li>De schijfruimte moet worden bewaakt wanneer de automatische opschoning wordt uitgevoerd.</li>
     <li>Voltooiingstijd (via de logboeken) om ervoor te zorgen dat 2 uur niet wordt overschreden.</li>
     <li>De grootte van de segmentstore nadat de Automatische Opschoning in werking is gesteld. De grootte van de segmentstore op de standby-instantie moet ongeveer gelijk zijn aan die op de primaire instantie.</li>
    </ul> </td>
   <td> </td>
  </tr>
 </tbody>
</table>

### Oplossen van problemen met online revisie {#troubleshooting-online-revision-cleanup}

<table>
 <tbody>
  <tr>
   <td><strong>Wat is het ergste dat kan gebeuren als u de Online Opruiming van de Revisie niet in werking stelt?</strong></td>
   <td>De AEM-instantie heeft onvoldoende schijfruimte, waardoor de productie afneemt.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Is het hoge gebruikersverkeer problematisch voor het runnen van Online Opruiming van de Revisie op een publicatieinstantie?</strong></td>
   <td>Het hoge gebruikersverkeer beïnvloedt of de samenstellingsfase met succes kan voltooien of niet.<br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Volgens de Health Check en de logbestandvermeldingen is de Online Revision Cleanup niet driemaal achter elkaar voltooid. Wat is vereist om het opruimen van online revisie met succes te voltooien?</strong></td>
   <td>U kunt verschillende stappen uitvoeren om het probleem te zoeken en op te lossen:<br />
    <ul>
     <li>Controleer eerst de logbestandvermeldingen<br /> </li>
     <li>Afhankelijk van de informatie in de logboeken, neem aangewezen actie:
      <ul>
       <li>Als de logboeken vijf gemiste compacte cycli en een onderbreking op de <code>forceCompact</code> cyclus tonen, plant het onderhoudsvenster aan een stille tijd wanneer de hoeveelheid opbergplaats laag schrijft. U kunt controleren of de gegevensopslagruimte schrijft in het hulpprogramma voor de bewaking van statistische gegevens in de gegevensopslagruimte op <em>https://serveraddress:serverport/libs/granite/operations/content/monitoring/page.html</em></li>
       <li>Als de schoonmaakbeurt aan het eind van het onderhoudsvenster ophield, zorg ervoor de configuratie van het onderhoudsvenster in het gebruikersinterface van de Taken van het Onderhoud groot genoeg is</li>
       <li>Als er onvoldoende heapgeheugen beschikbaar is, moet u ervoor zorgen dat de instantie voldoende geheugen heeft.</li>
       <li>In het geval van een late reactie, zou de segmentstore te veel voor Online Correctie van de Revisie kunnen groeien om zelfs binnen een langer onderhoudsvenster te voltooien. Bijvoorbeeld, als er geen succesvolle Online Correctie van de Revisie voltooide in de laatste week was dan wordt het geadviseerd om een off-line onderhoud te plannen en Offline de Opruiming van de Revisie uit te voeren om segmenstore terug naar een handelbare grootte te brengen.</li>
      </ul> </li>
    </ul> </td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Wat moet er gebeuren als het alarm voor de health check is ingeschakeld?</strong></td>
   <td>Zie het vorige punt.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Wat gebeurt er als de Online Opruiming van de Revisie uit tijd tijdens het geplande onderhoudsvenster loopt?</strong></td>
   <td>De Online revisie-opschoning wordt geannuleerd en de restanten worden verwijderd. De volgende keer dat het onderhoudsvenster is gepland, wordt het programma opnieuw gestart.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Wat veroorzaakt <code>SegmentNotFoundException</code> instanties om worden het programma geopend <code>error.log</code> en hoe kan ik terugkrijgen?</strong></td>
   <td><p>A <code>SegmentNotFoundException</code> wordt geregistreerd door TarMK wanneer het probeert om tot een opslageenheid (een segment) toegang te hebben die het niet kan vinden. Er zijn drie scenario's die deze kwestie kunnen veroorzaken:</p>
    <ol>
     <li>Een toepassing die de aanbevolen toegangsmechanismen omzeilt (zoals Sling en de JCR API) en een API/SPI op een lager niveau gebruikt om toegang te krijgen tot de opslagplaats en vervolgens de retentietijd van een segment overschrijdt. Dat wil zeggen dat een verwijzing naar een entiteit langer wordt bewaard dan de retentietijd die is toegestaan door de Online Revision Cleanup (standaard 24 uur). Dit geval is van voorbijgaande aard en leidt niet tot gegevenscorruptie. Om te herstellen, zou het eiken-loophulpmiddel moeten worden gebruikt om de voorbijgaande aard van de uitzondering te bevestigen (de eiken-loopcontrole zou geen fouten moeten melden). Hiervoor moet de instantie offline worden genomen en daarna opnieuw worden gestart.</li>
     <li>Een externe gebeurtenis veroorzaakte de corruptie van de gegevens op de schijf. Dit kan een schijffout, een gebrek aan schijfruimte of een toevallige wijziging van de vereiste gegevensdossiers zijn. In dit geval moet de instantie offline worden genomen en worden gerepareerd met behulp van de eikenrun-controle. Lees de volgende <a href="https://github.com/apache/jackrabbit-oak/blob/trunk/oak-doc/src/site/markdown/nodestore/segment/overview.md#check" target="_blank">Apache-documentatie</a>voor meer informatie over het uitvoeren van de controle tijdens het gebruik van het eiken.</li>
     <li>Alle andere gevallen moeten worden opgelost via de <a href="https://helpx.adobe.com/marketing-cloud/contact-support.html" target="_blank">klantenservice</a>van Adobe.</li>
    </ol> </td>
   <td> </td>
  </tr>
 </tbody>
</table>

### Problemen oplossen op basis van foutberichten {#troubleshooting-based-on-error-messages}

Error.log zal uitgebreid zijn als er incidenten tijdens het online herzieningsproces schoonmaakbeurt zijn. De volgende matrix is bedoeld om de meest voorkomende boodschappen uit te leggen en mogelijke oplossingen te bieden:

| **Fase** | **Logberichten** | **Toelichting** | **Volgende stappen** |
|---|---|---|---|
|  |  |  |  |
| Schatting | TarMK GC #2: Schatting overgeslagen omdat de compressie is gepauzeerd | De schattingsfase wordt overgeslagen wanneer de compressie op het systeem door configuratie wordt onbruikbaar gemaakt. | Onlinerevisie opschonen inschakelen. |
|  | TarMK GC #2: Schatting onderbroken: ${REASON}. Compressie wordt overgeslagen. | De schattingsfase liep voortijdig af. Enkele voorbeelden van gebeurtenissen die de schattingsfase kunnen onderbreken: onvoldoende geheugen of schijfruimte op het hostsysteem. | Afhankelijk van de gegeven reden. |
| Compactie | TarMK GC #2: verdichting gepauzeerd | Zolang de samenstellingsfase door configuratie wordt gepauzeerd, noch zal de ramingsfase noch de samenstellingsfase worden uitgevoerd. | Opschonen van online revisie inschakelen. |
|  | TarMK GC #2: verdichting geannuleerd: ${REASON}. | De samenstellingsfase eindigde voortijdig. Enkele voorbeelden van gebeurtenissen die de compactiefase kunnen onderbreken: onvoldoende geheugen of schijfruimte op het hostsysteem. Bovendien kan de vereffening ook worden geannuleerd door het systeem te sluiten of door het expliciet te annuleren via administratieve interfaces zoals het onderhoudvenster binnen de operatiedashobard. | Afhankelijk van de gegeven reden. |
|  | TarMK GC #2: Verwerking mislukt in 32,902 min (1974140 ms), na 5 cycli | Dit bericht betekent niet dat er een onherstelbare fout is opgetreden, maar alleen dat de compensatie na een bepaalde hoeveelheid pogingen is beëindigd. Lees ook de [volgende alinea](https://jackrabbit.apache.org/oak/docs/nodestore/segment/overview.html#how-does-compaction-works-with-concurrent-writes). | Lees de volgende [documentatie](https://jackrabbit.apache.org/oak/docs/nodestore/segment/overview.html#how-does-compaction-works-with-concurrent-writes)van het Eik, en de laatste vraag van de [Lopende Online sectie van de Opruiming](/help/sites-deploying/revision-cleanup.md#running-online-revision-cleanup) van de Revisie. |
| Overbodig verwijderen | TarMK GC #2: opruiming onderbroken | Opruiming is geannuleerd door de opslagplaats te sluiten. Er wordt geen invloed op de consistentie verwacht. Bovendien wordt de schijfruimte hoogstwaarschijnlijk niet volledig vrijgemaakt. Deze wordt teruggewonnen tijdens de volgende opschoningscyclus van de revisie. | Onderzoek waarom de opslagplaats is afgesloten en probeer in de toekomst te voorkomen dat de opslagplaats tijdens onderhoudsvensters wordt afgesloten. |

## Offline revisie opschonen uitvoeren {#how-to-run-offline-revision-cleanup}

>[!CAUTION]
>
>Afhankelijk van de eikenversie die u gebruikt bij de AEM-installatie, moeten verschillende versies van het gereedschap voor het uitvoeren van de eek worden gebruikt. Controleer de onderstaande lijst met versievereisten voordat u het gereedschap gebruikt:
>
>* Voor Eak-versies **1.0.0 tot en met 1.0.11** of **1.1.0 tot en met 1.1.6** gebruikt u Eak-run versie** 1.0.11**
   >
   >
* Gebruik voor eikenversies die **nieuwer zijn dan de bovenstaande** versie de versie van Oak-run die overeenkomt met de eik-kern van uw AEM-installatie.
>



Adobe biedt een hulpprogramma met de naam **eikenrun** voor het opschonen van revisies. U kunt het downloaden op de volgende locatie:

[https://repo1.maven.org/maven2/org/apache/jackrabbit/oak-run/](https://repo1.maven.org/maven2/org/apache/jackrabbit/oak-run/)

Het hulpmiddel is een runnable pot die manueel kan worden in werking gesteld om de bewaarplaats te comprimeren. Het proces wordt genoemd off-line revisie schoonmaakbeurt omdat de bewaarplaats moet worden gesloten om het hulpmiddel behoorlijk in werking te stellen. Zorg ervoor dat u de opschoonbewerking plant in overeenstemming met uw onderhoudspad.

Voor uiteinden op hoe te om de prestaties van het schoonmaakproces te verhogen, zie het [Vergroten van de Prestaties van de Off-line Opruiming](/help/sites-deploying/revision-cleanup.md#increasing-the-performance-of-offline-revision-cleanup)van de Revisie.

>[!NOTE]
>
>U kunt ook oude controlepunten wissen voordat het onderhoud plaatsvindt (stappen 2 en 3 in de onderstaande procedure). Dit wordt alleen aanbevolen voor instanties met meer dan 100 controlepunten.

1. Zorg altijd dat u een recente back-up van de AEM-instantie hebt.

   Sluit AEM af.

1. (Optioneel) Gebruik het gereedschap om oude controlepunten te zoeken:

   ```xml
   java -jar oak-run.jar checkpoints install-folder/crx-quickstart/repository/segmentstore
   ```

1. (Optioneel) Verwijder vervolgens de controlepunten waarnaar niet wordt verwezen:

   ```xml
   java -jar oak-run.jar checkpoints install-folder/crx-quickstart/repository/segmentstore rm-unreferenced
   ```

1. Voer de compressie uit en wacht tot deze is voltooid:

   ```xml
   java -jar -Dsun.arch.data.model=32 oak-run.jar compact install-folder/crx-quickstart/repository/segmentstore
   ```

### De prestaties van opschonen van offlinerevisie verhogen {#increasing-the-performance-of-offline-revision-cleanup}

Het gereedschap voor het uitvoeren van een eikenhout bevat verschillende functies die tot doel hebben de prestaties van het opschonen van de revisie te verbeteren en het onderhoudsvenster zoveel mogelijk te minimaliseren.

De lijst bevat verschillende opdrachtregelparameters, zoals hieronder wordt beschreven:

* **-mmap.** U kunt deze waarde instellen op true of false. Indien ingesteld op true, wordt toegewezen toegang tot het geheugen gebruikt. Indien ingesteld op false, wordt bestandstoegang gebruikt. Indien niet gespecificeerd, wordt de geheugen in kaart gebrachte toegang gebruikt op systemen met 64 bits en de dossiertoegang wordt gebruikt op systemen met 32 bits. In Windows wordt de reguliere bestandstoegang altijd afgedwongen en wordt deze optie genegeerd. **Deze parameter heeft de parameter -Dtar.memoryMapping vervangen.**

* **-Dupdate.limit**. Bepaalt de drempel voor het spoelen van een tijdelijke transactie aan schijf. De standaardwaarde is 10000.

* **-Dcompress-interval**. Het aantal items in de compactiekaart dat behouden moet blijven totdat de huidige kaart wordt gecomprimeerd. De standaardwaarde is 1000000. U zou deze waarde aan een nog hoger aantal voor snellere productie moeten verhogen, als genoeg heapgeheugen beschikbaar is. **Deze parameter is verwijderd uit Oak versie 1.6 en heeft geen effect.**

* **-Dcompaction-progress-log**. Het aantal gecomprimeerde knooppunten dat wordt geregistreerd. De standaardwaarde is 150000, wat betekent dat de eerste 150000 samengeperste knopen tijdens de verrichting zullen worden geregistreerd. Gebruik dit in combinatie met de volgende parameter die hieronder wordt beschreven.

* **-Dtar.PersistCompactionMap.** Stel deze parameter in op true als u schijfruimte wilt gebruiken in plaats van heapgeheugen voor de persistentie van de compactietoewijzing. Vereist de werktuigversie 1.4 **en hoger van het gereedschap** Eiken. Zie vraag 3 in de sectie [Offline revisie opschonen Veelgestelde vragen](/help/sites-deploying/revision-cleanup.md#offline-revision-cleanup-frequently-asked-questions) voor meer informatie. **Deze parameter is verwijderd uit Oak versie 1.6 en heeft geen effect.**

* **—kracht.** Drijf compensatie en negeer een niet passende versie van de segmentopslag.

>[!CAUTION]
>
>Het gebruiken van de `--force` parameter zal de segmentopslag aan de recentste versie bevorderen, die met oudere versies van het Eak onverenigbaar is. Houd er ook rekening mee dat een downgrade niet mogelijk is. Als algemene regel, zou u deze parameters met voorzichtigheid en slechts moeten gebruiken als u kennis over hoe te om hen te gebruiken bent.

Een voorbeeld van de gebruikte parameters:

```xml
java -Dupdate.limit=10000 -Dcompaction-progress-log=150000 -Dlogback.configurationFile=logback.xml -Xmx8g -jar oak-run-*.jar checkpoints <repository>
```

### Aanvullende methoden voor het opschonen van revisies {#additional-methods-of-triggering-revision-cleanup}

Naast de hierboven vermelde methodes, kunt u het mechanisme van de revisieschoonmaakbeurt ook teweegbrengen door de console te gebruiken JMX als volgt:

1. Open de JMX-console op [http://localhost:4502/system/console/jmx](http://localhost:4502/system/console/jmx)
1. Klik **RevisionGarbageCollection** MBean.
1. Klik in het volgende venster op **startRevisionGC()** en **roep** vervolgens aan om de Revision Garbage Collection-taak te starten.

### Offline revisie opschonen Veelgestelde vragen {#offline-revision-cleanup-frequently-asked-questions}

<table>
 <tbody>
  <tr>
   <td><strong>Wat zijn de factoren die de duur van de Offline Opruiming van de Revisie bepalen?</strong></td>
   <td><p>De grootte van de opslagplaats en de hoeveelheid revisies die moeten worden opgeschoond, bepalen de duur van de opruiming.</p> </td>
  </tr>
  <tr>
   <td><strong>Wat is het verschil tussen een revisie en een paginaversie?</strong></td>
   <td>
    <ul>
     <li><strong></strong> Oak-revisie: Met eikenhout ordent u alle inhoud in een grote boomstructuur die uit knooppunten en eigenschappen bestaat. Elke momentopname of revisie van deze inhoudsstructuur is onveranderlijk, en de veranderingen in de boom worden uitgedrukt als opeenvolging van nieuwe revisies. Doorgaans leidt elke inhoudwijziging tot een nieuwe revisie. Zie ook <a href="https://jackrabbit.apache.org/dev/ngp.html" target="_blank"> Koppeling</a>volgen.</li>
     <li><strong></strong> Paginaversie:Met Versioning maakt u een "momentopname" van een pagina op een bepaald tijdstip. Gewoonlijk wordt een nieuwe versie gemaakt wanneer een pagina wordt geactiveerd. Zie <a href="/help/sites-authoring/working-with-page-versions.md" target="_blank">Werken met paginasversies</a>voor meer informatie.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Hoe te om de Offline taak van de Opruiming van de Revisie te versnellen als het niet binnen 8 uur voltooit?</strong></td>
   <td>Als de revisietaak niet binnen 8 uur voltooit en de <a href="/help/sites-administering/operations-dashboard.md#diagnosis-tools" target="_blank">draaddumps</a> onthullen dat belangrijkste hotspot is <code>InMemoryCompactionMap.findEntry</code>, gebruik de volgende parameter met het werktuig <strong>versies 1.4 </strong>of hoger. <code>-Dtar.PersistCompactionMap=true</code>. Houd er rekening mee dat de <code>-Dtar.PersistCompactionMap</code> parameter is verwijderd uit Oak versie 1.6.</td>
  </tr>
 </tbody>
</table>

