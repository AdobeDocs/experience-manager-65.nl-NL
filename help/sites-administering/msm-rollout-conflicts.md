---
title: Conflicten MSM-rollout
seo-title: MSM Rollout Conflicts
description: Leer hoe u problemen met de uitrol van meerdere sitebeheer kunt oplossen.
seo-description: Learn how to deal with Multi Site Manager rollout conflicts.
uuid: 7a640905-aae2-498e-b95c-2c73008fa1cd
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: site-features
content-type: reference
discoiquuid: 16db5334-604f-44e2-9993-10d683dee5bb
feature: Multi Site Manager
exl-id: e145e79a-c363-4a33-b9f9-99502ed20563
source-git-commit: 50d29c967a675db92e077916fb4adef6d2d98a1a
workflow-type: tm+mt
source-wordcount: '906'
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
* hoe dit van invloed zal zijn op gepubliceerde inhoud.

  Het standaardgedrag van AEM (out-of-the-box) is dat gepubliceerde inhoud niet wordt beïnvloed. Dus als een pagina die handmatig is gemaakt in de live kopie-vertakking is gepubliceerd, wordt die inhoud nog steeds gepubliceerd na de conflictafhandeling en -rollout.

Naast de standaardfunctionaliteit, kunnen de aangepaste conflicthandlers worden toegevoegd om verschillende regels uit te voeren. Hierdoor kunnen publicatiehandelingen ook als een afzonderlijk proces worden toegestaan.

### Voorbeeldscenario {#example-scenario}

In de volgende secties gebruiken we het voorbeeld van een nieuwe pagina `b`, die zowel in de blauwdruk als in de actieve (handmatig gemaakte) kopieervertakking zijn gemaakt, om de verschillende methoden voor het oplossen van conflicten te illustreren:

* blauwdruk: `/b`

  Een basispagina; met 1 onderliggende pagina, bp-niveau-1.

* live kopie: `/b`

  Een pagina die handmatig in de actieve kopieervertakking is gemaakt, met 1 onderliggende pagina, `lc-level-1`.

   * Geactiveerd bij publiceren als `/b`en de onderliggende pagina.

**Voor rollout**

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
   <td><code> /lc-level-1</code><br /> <br /> (bevat de inhoud van de pagina<br /> kind-niveau-1 dat manueel in de levende exemplaartak) werd gecreeerd</td>
  </tr>
 </tbody>
</table>

## Rolloutbeheer en Conflict-verwerking {#rollout-manager-and-conflict-handling}

Met de rollout Manager kunt u conflictbeheer activeren of deactiveren.

Dit gebeurt met [OSGi-configuratie](/help/sites-deploying/configuring-osgi.md) van **Day CQ WCM-implementatiebeheer**:

* **Conflict met handmatig gemaakte pagina&#39;s afhandelen**:

  ( `rolloutmgr.conflicthandling.enabled`)

  Ingesteld op true als de rollout manager conflicten moet verwerken van een pagina die in de live kopie is gemaakt met een naam die in de blauwdruk voorkomt.

AEM heeft [vooraf gedefinieerd gedrag wanneer conflictbeheer is gedeactiveerd](#behavior-when-conflict-handling-deactivated).

## Conflicthandlers {#conflict-handlers}

AEM gebruikt conflicthandlers om eventuele paginaconflicten op te lossen die bestaan wanneer het rollen van inhoud van een blauwdruk aan een levende kopie. De naam van pagina&#39;s wijzigen is een (de gebruikelijke) methode om dergelijke conflicten op te lossen. Er kunnen meerdere conflicthandlers operationeel zijn, zodat u verschillende gedragingen kunt selecteren.

AEM biedt:

* De [default conflict handler](#default-conflict-handler):

   * `ResourceNameRolloutConflictHandler`

* De mogelijkheid om een [aangepaste handler](#customized-handlers).
* Het de dienstrangschikkingsmechanisme dat u de prioriteit van elke individuele manager laat plaatsen. De dienst met het hoogste rangschikken wordt gebruikt.

### Standaardconflicthandler {#default-conflict-handler}

De standaardconflicthandler:

* Wordt aangeroepen `ResourceNameRolloutConflictHandler`

* Met deze handler krijgt de blauwdrukpagina prioriteit.
* De servicerangschikking voor deze handler is ingesteld op laag ( &quot;d.w.z. onder de standaardwaarde voor de `service.ranking` eigenschap) aangezien de veronderstelling is dat de aangepaste managers een hogere rangschikking zullen vereisen. De rangorde is echter niet het absolute minimum om zo nodig flexibiliteit te garanderen.

Deze conflicthandler geeft voorrang aan de blauwdruk. De pagina Live kopiëren `/b` wordt verplaatst (binnen de actieve kopieervertakking) naar `/b_msm_moved`.

* live kopie: `/b`

  Wordt verplaatst (binnen de live kopie) naar `/b_msm_moved`. Dit fungeert als back-up en zorgt ervoor dat er geen inhoud verloren gaat.

   * `lc-level-1` wordt niet verplaatst.

* blauwdruk: `/b`

  Is uitgerekt aan de levende exemplaarpagina `/b`.

   * `bp-level-1` wordt uitgerold naar de livecopy.

**Na rollout**

<table>
 <tbody>
  <tr>
   <td><strong>blauwdruk na rollout</strong></td>
   <td><strong>live kopie na rollout</strong><br /> </td>
   <td></td>
   <td><strong>live kopie na rollout</strong><br /> <br /> <br /> </td>
   <td><strong>publiceren na rollout</strong><br /> <br /> </td>
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

Aangepaste conflicthandlers kunnen:

* Geef een naam op basis van uw vereisten.
* Wordt ontwikkeld/geconfigureerd volgens uw vereisten. U kunt bijvoorbeeld een handler ontwikkelen zodat de pagina met live kopieën voorrang krijgt.
* Kan worden ontworpen om te worden gevormd gebruikend [OSGi-configuratie](/help/sites-deploying/configuring-osgi.md); met name:

   * **Servicereeks**:

     Definieert de volgorde voor andere conflicthandlers ( `service.ranking`).

     De standaardwaarde is 0.

### Gedrag wanneer Conflict afhandelen gedeactiveerd {#behavior-when-conflict-handling-deactivated}

Als u handmatig [conflictoplossing deactiveren](#rollout-manager-and-conflict-handling) dan onderneemt AEM geen actie op om het even welke conflicterende pagina&#39;s (de niet-conflicterende pagina&#39;s worden uitgevoerd zoals verwacht).

>[!CAUTION]
>
>AEM geeft geen aanwijzing dat conflicten worden genegeerd omdat dit gedrag expliciet moet worden geconfigureerd, zodat wordt aangenomen dat het vereiste gedrag is.

In dit geval heeft de live kopie in feite voorrang. De blauwdrukpagina `/b` niet is gekopieerd en de pagina voor live kopiëren `/b` onaangeroerd blijft.

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
   <td><strong>live kopie na rollout</strong><br /> <br /> <br /> </td>
   <td><strong>publiceren na rollout</strong><br /> <br /> </td>
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

De [OSGi](https://www.osgi.org/) de dienst rangschikt kan worden gebruikt om de prioriteit van individuele conflictmanagers te bepalen.
