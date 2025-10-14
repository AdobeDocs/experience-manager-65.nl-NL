---
title: Conflicten MSM-rollout
description: Leer hoe u problemen met de uitrol van meerdere sitebeheer kunt oplossen.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: site-features
content-type: reference
feature: Multi Site Manager
exl-id: e145e79a-c363-4a33-b9f9-99502ed20563
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: eae057caed533ef16bb541b4ad41b8edd7aaa1c7
workflow-type: tm+mt
source-wordcount: '905'
ht-degree: 0%

---

# Conflicten MSM-rollout{#msm-rollout-conflicts}

Conflicten kunnen optreden als er nieuwe pagina&#39;s met dezelfde paginanaam worden gemaakt in zowel de vertakking Verblauwdrukken als een afhankelijke vertakking voor live kopieën.

Dergelijke conflicten moeten bij de uitrol worden afgehandeld en opgelost.

## Conflictbehandeling {#conflict-handling}

Wanneer conflicterende pagina&#39;s wel bestaan (in de vertakkingen Bladeren en Actieve kopie), kunt u met MSM definiëren hoe (of zelfs als) deze moeten worden verwerkt.

Om ervoor te zorgen dat de rollout niet wordt geblokkeerd, kunnen mogelijke definities omvatten:

* welke pagina (blauwdruk of live kopie) tijdens de rollout prioriteit heeft;
* welke pagina&#39;s worden hernoemd (en hoe),
* hoe dit van invloed is op gepubliceerde inhoud.

  Het standaardgedrag van Adobe Experience Manager (AEM) (out-of-the-box) is dat gepubliceerde inhoud niet wordt beïnvloed. Dus als een pagina die handmatig is gemaakt in de live kopie-vertakking is gepubliceerd, wordt die inhoud nog steeds gepubliceerd na de conflictafhandeling en -rollout.

Naast de standaardfunctionaliteit, kunnen de aangepaste conflicthandlers worden toegevoegd om verschillende regels uit te voeren. Hierdoor kunnen publicatiehandelingen ook als een afzonderlijk proces worden toegestaan.

### Voorbeeldscenario {#example-scenario}

In de volgende secties gebruikt u het voorbeeld van een nieuwe pagina `b` die zowel in de blauwdruk als in de actieve kopieervertakking (manueel gemaakt) is gemaakt, om de verschillende methoden voor conflictoplossing te illustreren:

* blauwdruk: `/b`

  Een basispagina; met één onderliggende pagina, bp-niveau-1.

* live kopie: `/b`

  Een pagina die handmatig in de actieve kopieervertakking is gemaakt; met één onderliggende pagina, `lc-level-1` .

   * Geactiveerd bij publiceren als `/b`, samen met de kindpagina.

**vóór Uitvoer**

<table>
 <tbody>
  <tr>
   <td><strong>blauwdruk voor rollout</strong></td>
   <td><strong>live kopie voor rollout</strong></td>
   <td><strong>publiceren vóór rollout</strong></td>
  </tr>
  <tr>
   <td><code>b</code><br /> <br /> (gemaakt in een vertakking voor blauwdrukken, klaar voor rollout)<br /> </td>
   <td><code>b</code><br /> <br /> (handmatig gemaakt in actieve kopie-vertakking)<br /> </td>
   <td><code>b</code><br /> <br /> (bevat de inhoud van de pagina b die handmatig is gemaakt in de actieve kopieervertakking)</td>
  </tr>
  <tr>
   <td><code> /bp-level-1</code></td>
   <td><code> /lc-level-1</code><br /> <br /> (handmatig gemaakt in actieve kopie-vertakking)<br /> </td>
   <td><code> /lc-level-1</code><br /> <br /> (bevat de inhoud van de pagina <br /> kind-niveau-1 die manueel in de levende exemplaartak werd gecreeerd)</td>
  </tr>
 </tbody>
</table>

## Rolloutbeheer en Conflict-verwerking {#rollout-manager-and-conflict-handling}

Met de rollout Manager kunt u conflictbeheer activeren of deactiveren.

Dit wordt gedaan gebruikend de [&#x200B; configuratie OSGi &#x200B;](/help/sites-deploying/configuring-osgi.md) van **de Manager van de Uitvoer van CQ WCM van de Dag**:

* **de conflicten van de handvat met manueel gecreeerde Pagina&#39;s**:

  ( `rolloutmgr.conflicthandling.enabled`)

  Ingesteld op true als de rollout manager conflicten moet verwerken van een pagina die in de live kopie is gemaakt met een naam die in de blauwdruk voorkomt.

AEM heeft [&#x200B; vooraf bepaald gedrag wanneer het conflictbeheer &#x200B;](#behavior-when-conflict-handling-deactivated) is gedeactiveerd.

## Conflicthandlers {#conflict-handlers}

AEM gebruikt conflicthandlers om eventuele paginaconflicten op te lossen die bestaan wanneer het rollen van inhoud van een blauwdruk aan een levende kopie. De naam van pagina&#39;s wijzigen is een (de gebruikelijke) methode om dergelijke conflicten op te lossen. Er kunnen meerdere conflicthandlers operationeel zijn, zodat u verschillende gedragingen kunt selecteren.

AEM biedt:

* De [&#x200B; standaardconflictmanager &#x200B;](#default-conflict-handler):

   * `ResourceNameRolloutConflictHandler`

* De mogelijkheid om a [&#x200B; aangepaste manager &#x200B;](#customized-handlers) uit te voeren.
* Het de dienstrangschikkingsmechanisme dat u de prioriteit van elke individuele manager laat plaatsen. De dienst met het hoogste rangschikken wordt gebruikt.

### Standaardconflicthandler {#default-conflict-handler}

De standaardconflicthandler:

* Wordt aangeroepen `ResourceNameRolloutConflictHandler`

* Met deze handler krijgt de blauwdrukpagina prioriteit.
* De de dienstrangschikking voor deze manager wordt geplaatst laag (namelijk onder de standaardwaarde voor het `service.ranking` bezit) aangezien de veronderstelling is dat de aangepaste managers een hogere rangschikking nodig hebben. De rangorde is echter niet het absolute minimum om zo nodig flexibiliteit te garanderen.

Deze conflicthandler geeft voorrang aan de blauwdruk. De pagina voor live kopiëren `/b` wordt verplaatst (binnen de actieve kopieervertakking) naar `/b_msm_moved` .

* live kopie: `/b`

  Wordt verplaatst (binnen de live kopie) naar `/b_msm_moved` . Dit fungeert als back-up en zorgt ervoor dat er geen inhoud verloren gaat.

   * `lc-level-1` wordt niet verplaatst.

* blauwdruk: `/b`

  Wordt uitgerold naar de live kopieerpagina `/b` .

   * `bp-level-1` wordt uitgerold naar de live kopie.

**na Uitvoer**

<table>
 <tbody>
  <tr>
   <td><strong>blauwdruk na rollout</strong></td>
   <td><strong> levend exemplaar na rollout </strong><br /> </td>
   <td></td>
   <td><strong> levend exemplaar na rollout </strong><br /> <br /> <br /> </td>
   <td><strong> publiceren na rollout </strong><br /> <br /> </td>
  </tr>
  <tr>
   <td><code>b</code></td>
   <td><code>b</code><br /> <br /> (bevat de inhoud van de verfpagina b die is uitgevouwen)<br /> </td>
   <td></td>
   <td><code>b_msm_moved</code><br /> <br /> (heeft de inhoud van de pagina b die handmatig is gemaakt in de actieve kopieervertakking)</td>
   <td><code>b</code><br /> <br /> (geen wijziging; bevat de inhoud van de oorspronkelijke pagina b die handmatig is gemaakt in de actieve kopieervertakking en nu b_msm_moving wordt genoemd)<br /> </td>
  </tr>
  <tr>
   <td><code> /bp-level-1</code></td>
   <td><code class="code"> /bp-level-1</code></td>
   <td><code> /lc-level-1</code><br /> <br /> (geen wijziging)</td>
   <td><code> </code></td>
   <td><code> /lc-level-1</code><br /> <br /> (geen wijziging)</td>
  </tr>
 </tbody>
</table>

### Aangepaste handlers {#customized-handlers}

De aangepaste conflictmanagers laten u uw eigen regels uitvoeren. Gebruikend het de dienstrangschikkingsmechanisme kunt u ook bepalen hoe zij met andere managers in wisselwerking staan.

Aangepaste conflicthandlers kunnen het volgende hebben:

* Benoemd op basis van uw vereisten.
* Ontwikkeld/gevormd volgens uw vereisten; bijvoorbeeld, kunt u een manager ontwikkelen zodat de levende exemplaarpagina belangrijkheid wordt gegeven.
* Ontworpen om worden gevormd gebruikend de [&#x200B; configuratie OSGi &#x200B;](/help/sites-deploying/configuring-osgi.md); in het bijzonder:

   * **Rangschikking van de Dienst**:

     Definieert de volgorde voor andere conflicthandlers ( `service.ranking` ).

     De standaardwaarde is 0.

### Gedrag wanneer Conflict afhandelen gedeactiveerd {#behavior-when-conflict-handling-deactivated}

Als u manueel [&#x200B; conflicten behandeling &#x200B;](#rollout-manager-and-conflict-handling) deactiveert, dan neemt AEM geen actie op om het even welke conflicterende pagina&#39;s (de niet-conflicterende pagina&#39;s worden opgesteld zoals verwacht).

>[!CAUTION]
>
>AEM geeft geen aanwijzing dat conflicten worden genegeerd omdat dit gedrag expliciet moet worden geconfigureerd, zodat wordt aangenomen dat het vereiste gedrag is.

In dit geval heeft de live kopie in feite voorrang. De pagina met de blauwdruk `/b` wordt niet gekopieerd en de pagina met de live kopie `/b` blijft ongewijzigd.

* blauwdruk: `/b`

  Helemaal niet gekopieerd, maar wordt genegeerd.

* live kopie: `/b`

  Hetzelfde.

<table>
 <caption>
   Na rollout
 </caption>
 <tbody>
  <tr>
   <td><strong>blauwdruk na rollout</strong></td>
   <td><strong> levend exemplaar na rollout </strong><br /> <br /> <br /> </td>
   <td><strong> publiceren na rollout </strong><br /> <br /> </td>
  </tr>
  <tr>
   <td><code>b</code></td>
   <td><code>b</code><br /> <br /> (geen wijziging; bevat de inhoud van de pagina b die handmatig is gemaakt in de vertakking Actieve kopie)</td>
   <td><code>b</code><br /> <br /> (geen wijziging; bevat de inhoud van de pagina b die handmatig is gemaakt in de vertakking Actieve kopie)<br /> </td>
  </tr>
  <tr>
   <td><code> /bp-level-1</code><br /> </td>
   <td><code> /lc-level-1</code><br /> <br /> (geen wijziging)</td>
   <td><code> /lc-level-1</code><br /> <br /> (geen wijziging)</td>
  </tr>
 </tbody>
</table>

### Servicebeoordelingen {#service-rankings}

De [&#x200B; OSGi &#x200B;](https://www.osgi.org/) dienst rangschikt kan worden gebruikt om de prioriteit van individuele conflictmanagers te bepalen.
