---
title: Best practices voor workflow
description: Leer de beste werkwijzen voor het werken met workflows in Adobe Experience Manager.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
exl-id: 14775476-6fe5-4583-8ab5-b55fef892174
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '1925'
ht-degree: 0%

---

# Best practices voor workflow{#workflow-best-practices}

Met workflows kunt u Adobe Experience Manager-activiteiten (AEM) automatiseren.

Ze vertegenwoordigen vaak een groot deel van de verwerking die plaatsvindt in een AEM omgeving. Wanneer aangepaste workflowstappen niet volgens de beste praktijken worden geschreven, of workflows buiten de doos niet zodanig worden geconfigureerd dat ze zo efficiënt mogelijk worden uitgevoerd, kan het systeem hiervan de gevolgen ondervinden.

Daarom wordt u ten zeerste aangeraden de implementaties van uw workflows zorgvuldig te plannen.

## Configuratie {#configuration}

Bij het configureren van workflowprocessen (aangepast en/of out-of-the-box) zijn er een aantal zaken die in gedachten moeten worden gehouden.

### Tijdelijke workflows {#transient-workflows}

Om hoge opnameladingen te optimaliseren kunt u a [ werkschema als transient ](/help/sites-developing/workflows.md#transient-workflows) bepalen.

Wanneer een workflow een overgang is, worden de runtimegegevens met betrekking tot de tussenliggende werkstappen niet in het JCR voortgezet wanneer ze worden uitgevoerd (de uitvoeruitvoeruitvoeruitvoeringen blijven bestaan).

De voordelen kunnen zijn:

* Een verkorting van de werkschemaverwerkingstijd; van tot 10%.
* De groei van de opslagplaats aanzienlijk verminderen.
* Er zijn geen CRUD-workflows meer nodig om te wissen.
* Bovendien wordt het aantal TAR-bestanden dat moet worden gecomprimeerd, verminderd.

>[!CAUTION]
>
>Schakel deze functie niet in als uw bedrijf voorschrijft dat u gegevens over de werkstroomruntime voor controledoeleinden wilt behouden/archiveren.

### DAM-workflows afstemmen {#tuning-dam-workflows}

Voor prestaties die richtlijnen voor de werkschema&#39;s van DAM stemmen, zie de [ Gids van de Prestaties van AEM Assets ](/help/assets/performance-tuning-guidelines.md) stemmen.

### Het maximumaantal gelijktijdige workflows configureren {#configure-the-maximum-number-of-concurrent-workflows}

AEM kunnen meerdere workflowthreads tegelijk uitvoeren. Door gebrek wordt het aantal draden gevormd om de helft van het aantal bewerkerkernen op het systeem te zijn.

In gevallen waarin de workflows die worden uitgevoerd veeleisend zijn aan systeembronnen, kan dit betekenen dat er weinig over AEM is om te gebruiken voor andere taken, zoals het renderen van de ontwerpgebruikersinterface. Hierdoor kan het systeem traag zijn tijdens activiteiten zoals het uploaden van grote hoeveelheden afbeeldingen.

Om deze kwestie te richten, adviseert de Adobe het aantal **Maximum Parallelle Banen** te vormen tussen de helft tot driekwart van het aantal bewerkerkernen op het systeem. Hierdoor moet het systeem voldoende capaciteit hebben om snel te kunnen reageren wanneer deze workflows worden verwerkt.

Om **Maximum Parallelle Banen** te vormen, kunt u of:

* Vorm de **[Configuratie OSGi](/help/sites-deploying/configuring-osgi.md)** van de AEM console van het Web; voor **Rij: De Rij van het Werkschema van Granite** (een **Apache het Verdelen Configuratie van de Rij van de Baan**).

* Vorm de rij van de **het Verschuiven optie van Banen** van de AEM console van het Web; voor **de Configuratie van de Rij van de Baan: De Rij van het Werkschema van Granite**, bij `http://localhost:4502/system/console/slingevent`.

Bovendien, is er een afzonderlijke configuratie voor de **Externe Rij van de Baan van het Proces van het Proces van Granite van het Werkschema**. Dit wordt gebruikt voor werkschemaprocessen die externe binaire getallen, zoals **InDesign Server** of **Magisch Beeld** lanceren.

### Afzonderlijke taakwachtrij configureren {#configure-individual-job-queues}

In sommige gevallen is het nuttig om individuele baanrijen te vormen om gezamenlijke draden, of andere rijopties, op een individuele baanbasis te controleren. U kunt een individuele rij van de console van het Web via de **Apache die de Configuratie van de Rij van de Rij van de Rij van de Band** fabriek van de Rij van de Band vormt toevoegen en vormen. Om het aangewezen onderwerp te vinden om van een lijst te maken, voer het model van uw werkschema uit en zoek het in de **het Verschuiven console van Banen**; bijvoorbeeld, bij `http://localhost:4502/system/console/slingevent`.

Afzonderlijke taakwachtrijen kunnen ook worden toegevoegd voor tijdelijke werkstromen.

### Workflow leegmaken configureren {#configure-workflow-purging}

In een standaardinstallatie AEM een onderhoudsconsole biedt waar dagelijkse en wekelijkse onderhoudsactiviteiten kunnen worden gepland en geconfigureerd, bijvoorbeeld bij:

`http://localhost:4502/libs/granite/operations/content/maintenance.html`

Door gebrek, heeft het **Wekelijkse Venster van het Onderhoud** de taak van de Woordenwissing van het a **Werkschema**, maar dit moet worden gevormd alvorens het zal lopen. Om werkschemazuiveringen te vormen, moet een nieuwe **Configuratie van de Woorden van het Werkschema van de Adobe Granite** in de console van het Web worden toegevoegd.

Voor verdere details op onderhoudstaken in AEM, zie het [ Dashboard van Verrichtingen ](/help/sites-administering/operations-dashboard.md).

## Aanpassing {#customization}

Bij het schrijven van aangepaste workflowprocessen moet u rekening houden met een aantal zaken.

### Locaties {#locations}

Definities van workflowmodellen, draagraketten, scripts en meldingen worden in de gegevensopslagruimte opgeslagen volgens het type, dat wil zeggen, &#39;out-of-the-box&#39;, zoals aangepaste gegevens.

>[!NOTE]
>
>Zie ook [ Herstructurering van de Bewaarplaats in AEM 6.5 ](/help/sites-deploying/repository-restructuring.md).

#### Locaties - workflowmodellen {#locations-workflow-models}

Workflowmodellen worden in de opslagplaats opgeslagen volgens het type:

* Workflowontwerpen die buiten de box vallen, worden opgeslagen onder het volgende pad:

  `/libs/settings/workflow/models/`

  >[!CAUTION]
  >
  >Niet:
  >
  >* plaats om het even welke modellen van uw douanewerkschema in deze omslag
  >* alles bewerken in `/libs`
  >
  >Aangezien om het even welke veranderingen bij verbetering of wanneer het installeren van heet-moeilijke situaties kunnen worden beschreven, cumulatieve moeilijke fixpakken of de dienstpakken.

* Aangepaste workflowontwerpen vindt u onder:

  ```
  /conf/global/settings/workflow/models/...
  ```

* Workflowontwerpen bij uitvoering (zowel out-of-the-box als aangepast) bevinden zich onder het volgende pad:

  `/var/workflow/models/`

* Verouderde workflowontwerpen (zowel tijdens het ontwerpen als bij uitvoering) staan onder het volgende pad:

  `/etc/workflow/models/`

  >[!NOTE]
  >
  >Als deze ontwerpen *gebruikend AEM UI* worden uitgegeven, dan zullen de details aan de nieuwe plaatsen worden gekopieerd.

#### Locaties - Workflowstartprogramma&#39;s {#locations-workflow-launchers}

Werkstroomstartdefinities worden ook volgens het type opgeslagen in de opslagplaats:

* Startprogramma&#39;s voor workflows die buiten de box vallen, worden ondergebracht in het volgende pad:

  `/libs/settings/workflow/launcher/`

  >[!CAUTION]
  >
  >Niet:
  >
  >* plaats om het even welke douane werkschemalanceerders in deze omslag
  >* alles bewerken in `/libs`
  >
  >Aangezien om het even welke veranderingen bij verbetering of wanneer het installeren van heet-moeilijke situaties kunnen worden beschreven, cumulatieve moeilijke fixpakken of de dienstpakken.

* Aangepaste draagraketten voor workflows vindt u onder:

  ```
  /conf/global/settings/workflow/launcher/...
  ```

* Verouderde draagraketten voor workflows worden opgeslagen onder het volgende pad:

  `/etc/workflow/launcher/`

  >[!NOTE]
  >
  >Als deze definities *gebruikend AEM UI* worden uitgegeven, dan zullen de details aan de nieuwe plaatsen worden gekopieerd.

#### Locaties - Workflowscripts {#locations-workflow-scripts}

Workflowscripts worden ook in de repository opgeslagen volgens het type:

* Workflowscripts buiten de box worden opgeslagen onder het volgende pad:

  `/libs/workflow/scripts/`

  >[!CAUTION]
  >
  >Niet:
  >
  >* Plaats om het even welke manuscripten van uw douanewerkschema in deze omslag
  >* alles bewerken in `/libs`
  >
  >Aangezien om het even welke veranderingen bij verbetering of wanneer het installeren van heet-moeilijke situaties kunnen worden beschreven, cumulatieve moeilijke fixpakken of de dienstpakken.

* Scripts voor aangepaste workflows staan onder:

  ```
  /apps/workflow/scripts/...
  ```

* Oudere workflowscripts staan in het volgende pad:

  `/etc/workflow/scripts/`

#### Locaties - Workflowmeldingen {#locations-workflow-notifications}

Workflowmeldingen worden ook opgeslagen in de repository volgens het type:

* De definities van de out-of-the-box workflowmelding worden gehouden onder het volgende pad:

  `/libs/settings/workflow/notification/`

  >[!CAUTION]
  >
  >Niet:
  >
  >* Plaats om het even welke definities van uw douanewerkschemabericht in deze omslag
  >* alles bewerken in `/libs`
  >
  >Aangezien om het even welke veranderingen bij verbetering of wanneer het installeren van heet-moeilijke situaties kunnen worden beschreven, cumulatieve moeilijke fixpakken of de dienstpakken.

* Definities van aangepaste workflowmeldingen vindt u onder:

  ```
  /conf/global/settings/workflow/notification/...
  ```

  >[!NOTE]
  >
  >Als u de tekst van een workflowmelding wilt overschrijven, maakt u een overlaypad onder:
  >
  >
  >`/conf/global/settings/workflow/notification/<path-under-libs>`

* Definities van verouderde workflowmeldingen vindt u onder het volgende pad:

  `/etc/workflow/notification/`

### Processessies {#process-sessions}

Net als bij elke aangepaste ontwikkeling wordt altijd aanbevolen om de sessie van een gebruiker te gebruiken als dat mogelijk is:

* voor een optimale naleving van de beveiligingsrichtlijnen
* om het systeem toe te staan om het openen en het sluiten van de zitting te leiden

Bij het implementeren van een workflowproces:

* Er wordt een workflowsessie aangeboden die moet worden gebruikt, tenzij er een dwingende reden is om dit niet te doen.
* Nieuwe sessies moeten niet worden gemaakt op basis van workflowstappen, omdat dit leidt tot inconsistenties in de status(s) en mogelijke gelijktijdige problemen in de workflow-engine.
* U moet geen nieuwe JCR-sessie aanschaffen vanuit een processtap in een workflow. U moet de workflowsessie die wordt geleverd door de Process Step API aanpassen aan een JCr-sessie. Bijvoorbeeld:

```
public void execute(WorkItem item, WorkflowSession workflowSession, MetaDataMap args) throws WorkflowException {
        // to obtain a jcr session:
        javax.jcr.Session jcrSession = workflowSession.adaptTo(javax.jcr.Session.class);

        // to obtain a sling resource resolver:
        org.apache.sling.api.resource.ResourceResolver slingResourceResolver = workflowSession.adaptTo(org.apache.sling.api.resource.ResourceResolver.class);
```

Een sessie opslaan:

* Als in een workflowproces de `WorkflowSession` wordt gebruikt om de gegevensopslagruimte te wijzigen, slaat dit niet expliciet de sessie op. De workflow slaat de sessie op wanneer deze is voltooid.
* `Session.Save` mag niet worden aangeroepen vanuit een workflowstap:

   * het wordt aanbevolen de werkstroom-jcr-sessie aan te passen; vervolgens is `save` niet nodig omdat de werkstroom de sessie automatisch opslaat zodra de werkstroom is voltooid.
   * het wordt niet aanbevolen dat een processtap een eigen jcr-sessie maakt.

* Door onnodige besparingen te elimineren, kunt u overheadkosten verminderen en zo de werkschema&#39;s efficiënter maken.

>[!CAUTION]
>
>Als u, ondanks de aanbevelingen hier, uw eigen jcr zitting creeert, dan moet het worden bewaard.

### Aantal/bereik van opstarters minimaliseren {#minimize-the-number-scope-of-launchers}

Er is één luisteraar die voor alle [ werkschemalanceerders ](/help/sites-administering/workflows-starting.md#workflows-launchers) verantwoordelijk is die worden geregistreerd:

* Er wordt geluisterd naar wijzigingen op alle paden die zijn opgegeven in de globbingseigenschappen van de andere draagraketten.
* Wanneer een gebeurtenis wordt verzonden, zal de werkschemamotor dan elke lancerer evalueren om te bepalen of het zou moeten lopen.

Het maken van te veel draagraketten zorgt ervoor dat het evaluatieproces langzamer wordt uitgevoerd.

Door een globbingpad in de basis van de opslagplaats te maken op één startpunt, zou de workflowengine luisteren naar gebeurtenissen voor het maken/wijzigen van gebeurtenissen in elk knooppunt in de opslagplaats en deze evalueren. Daarom wordt aangeraden alleen de nodige draagraketten te maken en het globbende pad zo specifiek mogelijk te maken.

Vanwege de invloed van deze draagraketten op het workflowgedrag, kan het ook handig zijn om alle draagraketten die niet in gebruik zijn, uit te schakelen.

### Verbeteringen in configuratie voor opstartprogramma&#39;s {#configuration-enhancements-for-launchers}

De douane [ startconfiguratie ](/help/sites-administering/workflows-starting.md#workflows-launchers) is verbeterd om het volgende te steunen:

* Meerdere voorwaarden &quot;AND&quot; hebben.
* OR-voorwaarden hebben in één voorwaarde.
* Schakel draagraketten uit of in op basis van het feit of een functiemarkering is ingeschakeld of uitgeschakeld.
* Ondersteuning voor regex in opstartomstandigheden.

### Workflows niet starten vanuit andere Workflows {#do-not-start-workflows-from-other-workflows}

Workflows kunnen een aanzienlijke hoeveelheid overhead met zich meebrengen, zowel in termen van objecten die in het geheugen zijn gemaakt als van knooppunten die in de opslagplaats worden bijgehouden. Daarom is het beter om een workflow op zichzelf te laten verwerken in plaats van extra workflows te laten starten.

Een voorbeeld hiervan is een workflow die een bedrijfsproces implementeert op een set inhoud en die inhoud vervolgens activeert. Het is beter om een proces van het douanewerkschema tot stand te brengen dat elk van deze knopen activeert, eerder dan het beginnen van **actief Inhoud** model voor elk van de inhoudsknopen die moeten worden gepubliceerd. Deze benadering vereist extra ontwikkelingswerk, maar is efficiënter wanneer uitgevoerd dan het beginnen van een afzonderlijke werkschemainstantie voor elke activering.

Een ander voorbeeld zou een werkschema zijn dat verscheidene knopen verwerkt, tot een werkschemapakket leidt, dan genoemd pakket activeert. In plaats van het pakket te maken en vervolgens een aparte workflow te starten met het pakket als de lading, kunt u de lading van uw workflow wijzigen in de stap die het pakket maakt en vervolgens de stap aanroepen om het pakket binnen hetzelfde workflowmodel te activeren.

### Handler Advance {#handler-advance}

Bij het ontwerpen van een workflowmodel hebt u de optie om de handler in staat te stellen de stappen van uw workflow te doorlopen. U kunt ook code toevoegen aan de workflowstap om te bepalen welke stap vervolgens moet worden uitgevoerd en vervolgens moet worden uitgevoerd.

Het wordt aanbevolen om de voortgang van de handlers te gebruiken omdat deze betere prestaties levert.

### Werkstroomfasen {#workflow-stages}

U kunt [ werkschemasfases ](/help/sites-developing/workflows.md#workflow-stages) bepalen, dan taken/stappen aan een specifiek werkschemastadium toewijzen.

Deze informatie wordt gebruikt voor het tonen van de vooruitgang van een werkschema wanneer u het [**lusje van Info van het Werkschema** van een werkpunt van **Inbox**](/help/sites-authoring/workflows-participating.md#opening-a-workflow-item-to-view-details-and-take-actions) klikt. Bestaande workflowmodellen kunnen worden bewerkt om stadia toe te voegen.

### Stap in paginaproces activeren {#activate-page-process-step}

De **activeer 1} stap van het Proces van de Pagina {zal pagina&#39;s voor u activeren, maar het zal automatisch om het even welke referenced activa van DAM niet vinden en zal die ook activeren.**

Dit is iets om in mening te houden als u deze stap als deel van een werkschemamodel wilt gebruiken.

### Overwegingen voor upgrades {#upgrade-considerations}

Wanneer u uw exemplaar upgradet:

* ervoor zorgen dat een back-up wordt gemaakt van aangepaste workflowmodellen voordat een upgrade wordt uitgevoerd.
* bevestig dat geen van uw douanewerkschema&#39;s onder de [ plaats ](#locations) worden opgeslagen:

   * `/libs/settings/workflow/models/projects`

>[!NOTE]
>
>Zie ook [ Herstructurering van de Bewaarplaats in AEM 6.5 ](/help/sites-deploying/repository-restructuring.md).

## Systeemgereedschappen {#system-tools}

Er zijn vele systeemhulpmiddelen beschikbaar om met controle, het handhaven, en het oplossen van problemenwerkschema&#39;s te helpen. Alle onderstaande voorbeeld-URL&#39;s gebruiken `localhost:4502` , maar moeten beschikbaar zijn voor elke instantie van de auteur ( `<hostname>:<port>` ).

### Sling Job Handling Console {#sling-job-handling-console}

`http://localhost:4502/system/console/slingevent`

De Sling Job Handling-console geeft het volgende weer:

* Statistieken over de stand van de werkgelegenheid in het systeem sinds de laatste herstart.
* Het zal ook de configuraties voor alle baanrijen tonen en een kortere weg verstrekken aan het uitgeven van hen in de configuratiemanager.

### Workflow Report Tool {#workflow-report-tool}

Het werkstroomrapportagehulpprogramma wordt verwijderd in 6.3 om te voorkomen dat de prestaties afnemen.

### Workflowonderhoudsbewerkingen MBean {#workflow-maintenance-operations-mbean}

`http://localhost:4502/system/console/jmx/com.adobe.granite.workflow:type=Maintenance`

Het werkstroomonderhoud MBean stelt verscheidene nuttige onderhoudroutines zoals het zuiveren van voltooide werkschema&#39;s en het terugwinnen van werkschemastatistieken bloot.

## Aanvullende informatie {#further-information}

Zie voor meer informatie:

* [Werken met workflows](/help/sites-authoring/workflows.md)
* [Workflows beheren](/help/sites-administering/workflows.md)
* [Workflows ontwikkelen en uitbreiden](/help/sites-developing/workflows.md)
* [Optimalisatie van prestaties](/help/sites-deploying/configuring-performance.md)
