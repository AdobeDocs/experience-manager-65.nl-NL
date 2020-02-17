---
title: Conflicten MSM-rollout
seo-title: Conflicten MSM-rollout
description: Leer hoe u problemen met de uitrol van meerdere sitebeheer kunt oplossen.
seo-description: Leer hoe u problemen met de uitrol van meerdere sitebeheer kunt oplossen.
uuid: 7a640905-aae2-498e-b95c-2c73008fa1cd
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: site-features
content-type: reference
discoiquuid: 16db5334-604f-44e2-9993-10d683dee5bb
translation-type: tm+mt
source-git-commit: 47b69098a45f774501ebb62ee1a14a8d209ad101

---


# Conflicten MSM-rollout{#msm-rollout-conflicts}

Conflicten kunnen optreden als er nieuwe pagina&#39;s met dezelfde paginanaam worden gemaakt in zowel de vertakking Verblauwdrukken als een afhankelijke vertakking voor live kopieën.

Dergelijke conflicten moeten bij de uitrol worden afgehandeld en opgelost.

## Conflictbehandeling {#conflict-handling}

Wanneer conflicterende pagina&#39;s bestaan (in de blauwdruk en de levende exemplaartakken), staat MSM u toe om te bepalen hoe (of zelfs als) zij zouden moeten worden behandeld.

Om ervoor te zorgen dat de rollout niet wordt geblokkeerd, kunnen mogelijke definities omvatten:

* welke pagina (blauwdruk of live kopie) tijdens de rollout prioriteit heeft;
* welke pagina&#39;s worden hernoemd (en hoe),
* hoe dit van invloed zal zijn op gepubliceerde inhoud.

   Het standaardgedrag van AEM (out-of-the-box) is dat gepubliceerde inhoud niet wordt beïnvloed. Dus als een pagina die handmatig is gemaakt in de live kopie-vertakking is gepubliceerd, wordt die inhoud nog steeds gepubliceerd na de conflictafhandeling en -rollout.

Naast de standaardfunctionaliteit, kunnen de aangepaste conflicthandlers worden toegevoegd om verschillende regels uit te voeren. Hierdoor kunnen publicatiehandelingen ook als een afzonderlijk proces worden toegestaan.

### Voorbeeldscenario {#example-scenario}

In de volgende secties gebruiken wij het voorbeeld van een nieuwe pagina `b`, die in zowel de blauwdruk als de levende exemplaartak (manueel gecreeerd) wordt gecreeerd, om de diverse methodes van conflictoplossing te illustreren:

* blauwdruk: `/b`

   een basispagina; met 1 onderliggende pagina, bp-niveau-1.

* live kopie: `/b`

   Een pagina die handmatig in de actieve kopieervertakking is gemaakt. met 1 onderliggende pagina, `lc-level-1`.

   * Geactiveerd bij publiceren als `/b`, samen met de kindpagina.

**Voor rollout**

<table>
 <tbody>
  <tr>
   <td><strong>blauwdruk voor rollout</strong></td>
   <td><strong>live kopie voor rollout</strong></td>
   <td><strong>publiceren vóór rollout</strong></td>
  </tr>
  <tr>
   <td><code>b</code> <br /> (gemaakt in een vertakking voor blauwdrukken, klaar voor rollout)<br /> </td>
   <td><code>b</code> <br /> (handmatig gemaakt in actieve kopie-vertakking)<br /> </td>
   <td><code>b</code> <br /> (bevat de inhoud van de pagina b die handmatig is gemaakt in de actieve kopieervertakking)</td>
  </tr>
  <tr>
   <td><code> /bp-level-1</code></td>
   <td><code> /lc-level-1</code> <br /> (handmatig gemaakt in actieve kopie-vertakking)<br /> </td>
   <td><code> /lc-level-1</code> <br /> (bevat de inhoud van de pagina<br /> onderliggende-niveau-1 die handmatig is gemaakt in de actieve kopieervertakking)</td>
  </tr>
 </tbody>
</table>

## Rolloutbeheer en Conflict-verwerking {#rollout-manager-and-conflict-handling}

Met de rollout Manager kunt u conflictbeheer activeren of deactiveren.

Dit wordt gedaan gebruikend [configuratie](/help/sites-deploying/configuring-osgi.md) OSGi van **Dag CQ WCM Rollout Manager**:

* **Conflict verwerken met handmatig gemaakte pagina**&#39;s:

   ( `rolloutmgr.conflicthandling.enabled`)

   Ingesteld op true als de rollout manager conflicten moet verwerken van een pagina die in de live kopie is gemaakt met een naam die in de blauwdruk voorkomt.

AEM heeft [vooraf bepaald gedrag wanneer het conflictbeheer is gedeactiveerd](#behavior-when-conflict-handling-deactivated).

## Conflicthandlers {#conflict-handlers}

AEM gebruikt conflictmanagers om het even welke paginaconflicten op te lossen die wanneer het rollen van inhoud van een blauwdruk aan een levende kopie bestaan. De naam van pagina&#39;s wijzigen is een (de gebruikelijke) methode om dergelijke conflicten op te lossen. Er kunnen meerdere conflicthandlers operationeel zijn, zodat u verschillende gedragingen kunt selecteren.

AEM biedt:

* De [standaardconflicthandler](#default-conflict-handler):

   * `ResourceNameRolloutConflictHandler`

* De mogelijkheid om een [aangepaste manager](#customized-handlers)uit te voeren.
* Het de dienstrangschikkingsmechanisme dat u toestaat om de prioriteit van elke individuele manager te plaatsen. De dienst met het hoogste rangschikken wordt gebruikt.

### Standaardconflicthandler {#default-conflict-handler}

De standaardconflicthandler:

* Wordt aangeroepen `ResourceNameRolloutConflictHandler`

* Met deze handler krijgt de blauwdrukpagina prioriteit.
* De dienst die voor deze manager rangschikt wordt geplaatst laag ( &quot;d.w.z. onder de standaardwaarde voor het `service.ranking` bezit) aangezien de veronderstelling is dat de aangepaste managers een hogere rangschikking zullen vereisen. De rangorde is echter niet het absolute minimum om zo nodig flexibiliteit te garanderen.

Deze conflicthandler geeft voorrang aan de blauwdruk. De pagina voor live kopiëren `/b` wordt verplaatst (binnen de actieve kopieervertakking) naar `/b_msm_moved`.

* live kopie: `/b`

   Wordt verplaatst (binnen de live kopie) naar `/b_msm_moved`. Dit fungeert als back-up en zorgt ervoor dat er geen inhoud verloren gaat.

   * `lc-level-1` wordt niet verplaatst.

* blauwdruk: `/b`

   Wordt uitgerold naar de live kopieerpagina `/b`.

   * `bp-level-1` wordt uitgerold naar de livecopy.

**Na rollout**

<table>
 <tbody>
  <tr>
   <td><strong>blauwdruk na rollout</strong></td>
   <td><strong>live kopie na rollout</strong><br /> </td>
   <td></td>
   <td><strong>live kopie na rollout</strong><br /> <br /><br /> </td>
   <td><strong>publiceren na rollout</strong><br /><br /> </td>
  </tr>
  <tr>
   <td><code>b</code></td>
   <td><code>b</code> <br /> (bevat de inhoud van de verfpagina b die is uitgevouwen)<br /> </td>
   <td></td>
   <td><code>b_msm_moved</code> <br /> (heeft de inhoud van de pagina b die handmatig is gemaakt in de actieve kopieervertakking)</td>
   <td><code>b</code> <br /> (geen wijziging; bevat de inhoud van de oorspronkelijke pagina b die handmatig is gemaakt in de actieve kopieervertakking en nu b_msm_moving wordt genoemd)<br /> </td>
  </tr>
  <tr>
   <td><code> /bp-level-1</code></td>
   <td><code class="code"> /bp-level-1</code></td>
   <td><code> /lc-level-1</code> <br /> (geen wijziging)</td>
   <td><code> </code></td>
   <td><code> /lc-level-1</code> <br /> (geen wijziging)</td>
  </tr>
 </tbody>
</table>

### Aangepaste handlers {#customized-handlers}

De aangepaste conflictmanagers staan u toe om uw eigen regels uit te voeren. Gebruikend het de dienstrangschikkingsmechanisme kunt u ook bepalen hoe zij met andere managers in wisselwerking staan.

Aangepaste conflicthandlers kunnen:

* Geef een naam op basis van uw vereisten.
* worden ontwikkeld/geconfigureerd volgens uw vereisten; bijvoorbeeld, kunt u een manager ontwikkelen zodat de levende exemplaarpagina voorrang wordt gegeven.
* kan worden ontworpen om worden gevormd gebruikend de configuratie [](/help/sites-deploying/configuring-osgi.md)OSGi; met name:

   * **Serviceklasse**:

      Bepaalt de orde met betrekking tot andere conflicthandlers ( `service.ranking`).

      De standaardwaarde is 0.

### Gedrag wanneer Conflict afhandelen gedeactiveerd {#behavior-when-conflict-handling-deactivated}

Als u de [conflictafhandeling](#rollout-manager-and-conflict-handling) handmatig deactiveert, voert AEM geen actie uit op conflicterende pagina&#39;s (pagina&#39;s die niet conflicteren worden naar behoren geïmplementeerd).

>[!CAUTION]
>
>AEM geeft geen aanwijzing dat conflicten worden genegeerd aangezien dit gedrag uitdrukkelijk moet worden gevormd, zodat wordt verondersteld dat het het vereiste gedrag is.

In dit geval heeft de live kopie in feite voorrang. De pagina met de blauwdruk `/b` wordt niet gekopieerd en de pagina met de live kopie `/b` blijft ongewijzigd.

* blauwdruk: `/b`

   Wordt helemaal niet gekopieerd, maar wordt genegeerd.

* live kopie: `/b`

   Dat blijft zo.

<table>
 <caption>
   Na rollout
 </caption>
 <tbody>
  <tr>
   <td><strong>blauwdruk na rollout</strong></td>
   <td><strong>live kopie na rollout</strong><br /> <br /><br /> </td>
   <td><strong>publiceren na rollout</strong><br /><br /> </td>
  </tr>
  <tr>
   <td><code>b</code></td>
   <td><code>b</code> <br /> (geen wijziging; heeft de inhoud van de pagina b die handmatig is gemaakt in de actieve kopieervertakking)</td>
   <td><code>b</code> <br /> (geen wijziging; bevat de inhoud van de pagina b die handmatig is gemaakt in de actieve kopieervertakking)<br /> </td>
  </tr>
  <tr>
   <td><code> /bp-level-1</code> </td>
   <td><code> /lc-level-1</code> <br /> (geen wijziging)</td>
   <td><code> /lc-level-1</code> <br /> (geen wijziging)</td>
  </tr>
 </tbody>
</table>

### Servicebeoordelingen {#service-rankings}

De [OSGi](https://www.osgi.org/) de dienstrangschikking kan worden gebruikt om de prioriteit van individuele conflictmanagers te bepalen.
