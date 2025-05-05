---
title: Actieve kopieën maken en synchroniseren
description: Leer hoe u Actieve kopieën maakt en synchroniseert in Adobe Experience Manager.
feature: Multi Site Manager
exl-id: 896b35dd-4510-4c94-8615-03d9649c2f64
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: d5fb67933676c9ea5fdbeafe592960403e78af79
workflow-type: tm+mt
source-wordcount: '4177'
ht-degree: 0%

---

# Actieve kopieën maken en synchroniseren{#creating-and-synchronizing-live-copies}

U kunt een live kopie maken van een pagina- of blauwdrukconfiguratie en vervolgens overerving en synchronisatie beheren.

## Browserconfiguraties beheren {#managing-blueprint-configurations}

Een blauwdrukconfiguratie identificeert een bestaande website die u als bron voor één of meerdere levende exemplaarpagina&#39;s wilt gebruiken.

>[!NOTE]
>
>Met vervagingsconfiguraties kunt u wijzigingen in de inhoud doorvoeren in live kopieën. Zie [ Levende Kopieën - Source, Blauwdrukken en de Configuraties van de Vervaging ](/help/sites-administering/msm.md#source-blueprints-and-blueprint-configurations).

Wanneer u een blauwdrukconfiguratie creeert, selecteert u een malplaatje dat de interne structuur van de blauwdruk bepaalt. In de standaardsjabloon voor blauwdrukken wordt ervan uitgegaan dat de bronwebsite de volgende kenmerken heeft:

* De website heeft een hoofdpagina.
* De directe onderliggende pagina&#39;s van de hoofdmap zijn taalvertakkingen van de website. Wanneer u een live kopie maakt, worden de talen weergegeven als optionele inhoud die in de kopie moet worden opgenomen.
* De hoofdmap van elke taalvertakking bevat een of meer onderliggende pagina&#39;s. Wanneer u een live kopie maakt, worden onderliggende pagina&#39;s weergegeven als hoofdstukken die u in de live kopie kunt opnemen.

>[!NOTE]
>
>Een andere structuur vereist een andere blauwdruksjabloon.

Nadat u de blauwdrukconfiguratie creeert, vormt u de volgende eigenschappen:

* **Naam**: De naam van de blauwdrukconfiguratie.
* **Weg van Source**: De weg van de wortelpagina van de plaats die u als bron (blauwdruk) gebruikt.
* **Beschrijving**. (Optioneel) Een beschrijving van de configuratie van de blauwdruk. De beschrijving wordt weergegeven in de lijst met blauwdrukconfiguraties waaruit u kunt kiezen bij het maken van een site.

Wanneer uw blauwdrukconfiguratie wordt gebruikt, kunt u het met een rollout configuratie associëren die bepaalt hoe de levende exemplaren van de bron/de blauwdruk worden gesynchroniseerd. Zie [ het specificeren van de Configuraties van de Output aan Gebruik ](/help/sites-administering/msm-sync.md#specifying-the-rollout-configurations-to-use).

### Een blauwdrukconfiguratie maken {#creating-a-blueprint-configuration}

Een blauwdrukconfiguratie maken:

1. [ navigeer ](/help/sites-authoring/basic-handling.md#global-navigation) aan het **Hulpmiddelen** menu, dan selecteer het **Sites** menu.
1. Selecteer **Vervagen** om de **console van de Configuraties van de Vervaging** te openen:

   ![ configuraties van de Vervaging ](assets/blueprint-configurations.png)

1. Selecteer **creeer**.
1. Selecteer het blauwdrukmalplaatje, dan **daarna** om verder te gaan.
1. Selecteer de bronpagina die als blauwdruk moet worden gebruikt; dan **daarna** om verder te gaan.
1. Definiëren:

   * **Titel**: verplichte titel voor de blauwdruk
   * **Beschrijving**: een facultatieve beschrijving om meer details te verstrekken.

1. **creeer** zal tot de blauwdrukconfiguratie leiden die op uw specificatie wordt gebaseerd.

### Een configuratie van een blauwdruk bewerken of verwijderen {#editing-or-deleting-a-blueprint-configuration}

U kunt een bestaande configuratie van de blauwdruk bewerken of verwijderen:

1. [ navigeer ](/help/sites-authoring/basic-handling.md#global-navigation) aan het **Hulpmiddelen** menu, dan selecteer het **Sites** menu.
1. Selecteer **Vervagen** om de **console van de Configuraties van de Vervaging** te openen:

   ![ configuraties van de Vervaging ](assets/blueprint-configurations.png)

1. Selecteer de vereiste blauwdrukconfiguratie. De juiste acties worden beschikbaar op de werkbalk:

   * **Eigenschappen**; u kunt dit gebruiken om de eigenschappen van de configuratie te bekijken en dan uit te geven.
   * **Schrapping**

## Een actieve kopie maken {#creating-a-live-copy}

### Een actieve kopie van een pagina maken {#creating-a-live-copy-of-a-page}

U kunt een live kopie van elke pagina of vertakking maken. Wanneer u de live kopie maakt, kunt u de rollout-configuraties opgeven die moeten worden gebruikt voor het synchroniseren van de inhoud:

* De geselecteerde rollout-configuraties zijn van toepassing op de live kopieerpagina en de onderliggende pagina&#39;s.
* Als u geen rollout configuraties specificeert, bepaalt MSM welke rollout configuraties aan gebruik. Zie [ specificerend de Configuratie van de Uitvoer aan Gebruik ](/help/sites-administering/msm-sync.md#specifying-the-rollout-configurations-to-use).

U kunt een live kopie van elke pagina maken:

* Pagina&#39;s die door a [ blauwdrukconfiguratie ](#creating-a-blueprint-configuration) van verwijzingen worden voorzien.
* En pagina&#39;s die geen verbinding met een configuratie hebben.
* AEM ondersteunt ook het maken van een live kopie op de pagina&#39;s van een andere live kopie.

Het enige verschil is dat de beschikbaarheid van het **bevel van de Uitvoer** op de bron/de blauwdruk pagina&#39;s afhankelijk is van of de bron door een blauwdrukconfiguratie van verwijzingen wordt voorzien:

* Als u het levende exemplaar van een bronpagina creeert die **&#x200B;**&#x200B;in een blauwdrukconfiguratie van verwijzingen wordt voorzien, dan zal het bevel van de Uitvoer op de bron/de pagina(s) van de blauwdruk beschikbaar zijn.
* Als u het levende exemplaar van een bronpagina creeert die **niet** in een blauwdrukconfiguratie van verwijzingen wordt voorzien, dan zal het bevel van de Uitvoer niet beschikbaar op de bron/blauwdruk pagina(s) zijn.

Een live kopie maken:

1. In de **console 1&rbrace; uitgezochte** van Plaatsen **, dan** Levende Exemplaar **.**

   ![ creeer Levend Exemplaar ](assets/chlimage_1-212.png)

1. Selecteer de bronpagina dan klik **daarna**. Bijvoorbeeld:

   ![ Uitgezochte bronpagina ](assets/chlimage_1-213.png)

1. Specificeer de bestemmingspad van het levende exemplaar (open de ouderomslag/de pagina van het levende exemplaar) en klik dan **daarna**.

   ![ specificeer bestemming ](assets/chlimage_1-214.png)

   >[!NOTE]
   >
   >Het doelpad kan zich niet binnen het bronpad bevinden.

1. Enter:

   * a **Titel** voor de pagina.
   * a **Naam**, die in URL wordt gebruikt.

   ![ ga titel en naam ](assets/chlimage_1-215.png) in

1. Gebruik **sluit subpagina&#39;s** checkbox uit:

   * Geselecteerd: alleen een live kopie van de geselecteerde pagina maken (oppervlakkige live kopie)
   * Niet geselecteerd: maak een live kopie die alle onderliggende elementen van de geselecteerde pagina bevat (diepe live kopie)

1. (Facultatief) om één of meerdere rollout configuraties aan gebruik voor de livecopy te specificeren, gebruik de **drop-down lijst van de Output vormt** om hen te selecteren; de geselecteerde configuraties worden getoond onder de drop-down selecteur.
1. Klik **creëren**. Een bevestigingsbericht wordt getoond, van hier kunt u of **Open** selecteren of **Gereed**.

### Een live kopie van een site maken op basis van een blauwdrukconfiguratie {#creating-a-live-copy-of-a-site-from-a-blueprint-configuration}

Maak een live kopie met behulp van een blauwdrukconfiguratie om een site te maken op basis van de blauwdrukinhoud (bron). Wanneer u een levend exemplaar van een blauwdrukconfiguratie creeert, selecteert u één of meerdere taaltakken van de blauwdrukbron om te kopiëren, dan selecteert u de hoofdstukken om van de taaltakken te kopiëren. Zie [ Creërend een Configuratie van de Vervaging ](/help/sites-administering/msm-livecopy.md#creating-a-blueprint-configuration).

Als u sommige taaltakken of hoofdstukken van het levende exemplaar weglaat, kunt u hen later toevoegen; zie [ Creërend Levend Exemplaar binnen een Levend Exemplaar (de Configuratie van de Vervaging) ](#creating-a-live-copy-inside-a-live-copy-blueprint-configuration).

>[!CAUTION]
>
>Wanneer de bron van de blauwdruk verbindingen en verwijzingen bevat die een paragraaf in een verschillende tak richten, worden de doelstellingen niet bijgewerkt in de levende exemplaarpagina&#39;s, maar blijven gericht aan de originele bestemming.

Geef bij het maken van de site waarden op voor de volgende eigenschappen:

* **Aanvankelijke Talen**: De taaltakken van de blauwdrukbron om in het levende exemplaar te omvatten.
* **Aanvankelijke Hoofdstukken**: De kindpagina&#39;s van de de taaltakken van de blauwdruk om in het levende exemplaar te omvatten.
* **Weg van de Bestemming**: De plaats van de wortelpagina van de levende exemplaarplaats.
* **Titel**: De titel van de wortelpagina van de levende exemplaarplaats.
* **Naam**: (Facultatief) de naam van de knoop JCR die de wortelpagina van het levende exemplaar opslaat. De standaardwaarde is gebaseerd op de titel.
* **Eigenaar van de Plaats**: (Facultatief)
* **Levende Exemplaar**: Selecteer deze optie om een levende verhouding met de bronplaats te vestigen. Als u deze optie niet selecteert, wordt een kopie van de blauwdruk gemaakt, maar wordt deze niet gesynchroniseerd met de bron.
* **Rollout vormt**: (Facultatief) selecteer één of meerdere rollout configuraties om voor het synchroniseren van het levende exemplaar te gebruiken. Door gebrek, worden de rollout configuraties geërft van de blauwdruk; zie [ specificerend de Configuraties van de Output ](/help/sites-administering/msm-sync.md#specifying-the-rollout-configurations-to-use) voor meer details te gebruiken.

Een live kopie van een site maken op basis van een blauwdrukconfiguratie:

1. In de **console van Plaatsen**, uitgezochte **creeert**, toen **Plaats** van de drop-down selecteur.
1. Selecteer de blauwdrukconfiguratie als bron van het levende exemplaar te gebruiken en met **daarna** te werk te gaan:

   ![ Uitgezochte blauwdrukconfiguratie als bron van levend exemplaar ](assets/blueprint-configuration-select.png)

1. Gebruik de **Aanvankelijke Talen** selecteur om de talen van de blauwdrukplaats te specificeren voor het levende exemplaar te gebruiken.

   Standaard zijn alle beschikbare talen geselecteerd. Om een taal te verwijderen, klik **X** die naast de taal verschijnt.

   Bijvoorbeeld:

   ![ Uitgezochte Eerste Talen ](assets/chlimage_1-217.png)

1. Gebruik de **Aanvankelijke drop-down Hoofdstukken** om de secties van de blauwdruk te selecteren om in het levende exemplaar te omvatten. Opnieuw zijn alle beschikbare hoofdstukken inbegrepen door gebrek, maar kunnen worden verwijderd.
1. Verstrek waarden voor de resterende eigenschappen en selecteer dan **creeer**. In het bevestigingsdialoogvakje, uitgezochte **Gedaan** om aan de **console van Plaatsen** terug te keren, of **Open Plaats** om de wortelpagina van de plaats te openen.

### Een actieve kopie maken in een live kopie (configuratie blauwdruk) {#creating-a-live-copy-inside-a-live-copy-blueprint-configuration}

Wanneer u een levende kopie binnen de bestaande live kopie (gemaakt met behulp van een blauwdrukconfiguratie) maakt, kunt u elke taalkopie of hoofdstukken invoegen die niet waren opgenomen toen de live kopie oorspronkelijk werd gemaakt.

## Uw Live kopie controleren {#monitoring-your-live-copy}

### De status van een live kopie bekijken {#seeing-the-status-of-a-live-copy}

De eigenschappen van een pagina met live kopieën geven de volgende informatie over de live kopie weer:

* **Source**: De bronpagina van de levende exemplaarpagina.
* **Status**: De synchronisatiestatus van het levende exemplaar. De status omvat of de live kopie up-to-date is met de bron, en wanneer de laatste synchronisatie heeft plaatsgevonden en wie de synchronisatie heeft uitgevoerd.
* **Configuratie**:

   * Of de pagina nog steeds onderhevig is aan overerving van live-kopieën.
   * Of de configuratie wordt overgeërfd van de ouderpagina.
   * Om het even welke rollout configuraties die het levende exemplaar gebruikt.

De eigenschappen weergeven:

1. In de **console van Plaatsen**, selecteer de levende exemplaarpagina en open de eigenschappen.
1. Selecteer het **Levende 1&rbrace; lusje van het Exemplaar &lbrace;.**

   Bijvoorbeeld:

   ![ Uitgezochte Levende Exemplaar ](assets/chlimage_1-218.png)

### De actieve kopieën van een vervagingspagina bekijken {#seeing-the-live-copies-of-a-blueprint-page}

De pagina&#39;s van de blauwdruk (die in een blauwdrukconfiguratie van verwijzingen worden voorzien) verstrekken u een lijst van de levende exemplaarpagina&#39;s die de huidige (blauwdruk) pagina als bron gebruiken. Gebruik deze lijst om de live kopieën bij te houden. De lijst verschijnt op het **Vervagen** lusje van de [ paginaeigenschappen ](/help/sites-authoring/editing-page-properties.md).

![ het lusje van de Vervaging ](assets/chlimage_1-219.png)

## Live kopie synchroniseren {#synchronizing-your-live-copy}

### Een blauwdruk uitrollen {#rolling-out-a-blueprint}

Leer een pagina van de blauwdruk uit om inhoudsveranderingen in levende exemplaren te duwen. A **Rollout** actie voert de rollout configuraties uit die [ op de trekker ](/help/sites-administering/msm-sync.md#rollout-triggers) gebruiken van de Output.

>[!NOTE]
>
>Conflicten kunnen optreden als er nieuwe pagina&#39;s met dezelfde paginanaam worden gemaakt in zowel de vertakking Verblauwdrukken als een afhankelijke vertakking voor live kopieën.
>
>Zulke [ conflicten moeten worden behandeld en op rollout ](/help/sites-administering/msm-rollout-conflicts.md) worden opgelost.
>

#### Een vervaging uitrollen uit pagina-eigenschappen {#rolling-out-a-blueprint-from-page-properties}

1. In de **console van Plaatsen**, selecteer de pagina in de blauwdruk en open de eigenschappen.
1. Open het **Vervagen** lusje.
1. Selecteer **Uitvoer**.

   ![ Uitgezochte Uitvoer ](assets/chlimage_1-220.png)

1. Geef de pagina&#39;s en eventuele subpagina&#39;s op en bevestig vervolgens met het vinkje:

   ![ specificeer pagina&#39;s en sub-pagina&#39;s ](assets/chlimage_1-221.png)

1. Specificeer als de rollout baan onmiddellijk (**nu**) of op een andere datum/tijd (**later**) zou moeten worden uitgevoerd.

   ![ Beeldscherm van de Uitvoer ](assets/rollout-blueprint.png)

Rollouts worden verwerkt als asynchrone banen en kunnen in het **dashboard [&#128279;](asynchronous-jobs.md#monitor-the-status-of-asynchronous-operations) van de Banen van 0&rbrace; Async &lbrace;worden gecontroleerd** Globale Navigatie **>** Hulpmiddelen **>** Verrichtingen **>** Banen **&#x200B;**

>[!NOTE]
>
>Voor asynchrone rollout-verwerking is AEM 6.5.3.0 of hoger vereist. In vorige versies werden pagina&#39;s direct en synchroon verwerkt.

#### Een vervaging uitrollen vanuit de referentierail {#roll-out-a-blueprint-from-the-reference-rail}

1. In de **console van Plaatsen**, selecteer de pagina in het levende exemplaar en open het **[paneel van Verwijzingen](/help/sites-authoring/basic-handling.md#references)** (van de toolbar).
1. Selecteer de **Vervaging** optie van de lijst, om de blauwdrukken te tonen verbonden aan deze pagina.
1. Selecteer de gewenste blauwdruk in de lijst.
1. Klik **Uitvoer**.
1. U wordt gevraagd de details van de rollout te bevestigen:

   * **werkingsgebied van de Uitvoer**:

     Geef op of het bereik alleen voor de geselecteerde pagina is of dat subpagina&#39;s moeten worden opgenomen.

   * **Programma**:

     Specificeer als de rollout baan onmiddellijk (**nu**) of bij een recentere datum/tijd (**later**) zou moeten worden uitgevoerd.

     ![ specificeer het programma ](assets/rollout-live-copy.png)

1. Na het bevestigen van deze details, uitgezochte **Uitvoer** om de actie uit te voeren.

Rollouts worden verwerkt als asynchrone banen en kunnen in het **dashboard [&#128279;](asynchronous-jobs.md#monitor-the-status-of-asynchronous-operations) van de Banen van 0&rbrace; Async &lbrace;worden gecontroleerd** Globale Navigatie **>** Hulpmiddelen **>** Verrichtingen **>** Banen **&#x200B;**

>[!NOTE]
>
>Voor asynchrone rollout-verwerking is AEM 6.5.3.0 of hoger vereist. In vorige versies, werden de pagina&#39;s verwerkt onmiddellijk en synchroon tenzij de **achtergrond rollout** optie werd gecontroleerd.

#### Een vervaging uitrollen met het overzicht van Actieve kopie {#roll-out-a-blueprint-from-the-live-copy-overview}

De [ actie van de Output is ook beschikbaar bij het Levende Overzicht van het Exemplaar ](/help/sites-administering/msm-livecopy-overview.md#using-the-live-copy-overview), wanneer een pagina van de Vervaging wordt geselecteerd.

1. Open het [ Levende Overzicht van het Exemplaar ](/help/sites-administering/msm-livecopy-overview.md#using-the-live-copy-overview) en selecteer een Pagina van de Vervaging.
1. Selecteer **Uitvoer** van de toolbar.
1. Geef de pagina&#39;s en eventuele subpagina&#39;s op en bevestig vervolgens met het vinkje:

   ![ selecteer de pagina&#39;s en sub-pagina&#39;s ](assets/chlimage_1-223.png)

1. Specificeer als de rollout baan onmiddellijk (**nu**) of op een andere datum/tijd (**later**) zou moeten worden uitgevoerd.

   ![ Beeldscherm van de Uitvoer ](assets/rollout-blueprint.png)

Rollouts worden verwerkt als asynchrone banen en kunnen in het **dashboard [&#128279;](asynchronous-jobs.md#monitor-the-status-of-asynchronous-operations) van de Banen van 0&rbrace; Async &lbrace;worden gecontroleerd** Globale Navigatie **>** Hulpmiddelen **>** Verrichtingen **>** Banen **&#x200B;**

>[!NOTE]
>
>Voor asynchrone rollout-verwerking is AEM 6.5.3.0 of hoger vereist. In vorige versies werden pagina&#39;s direct en synchroon verwerkt.

### Een actieve kopie synchroniseren {#synchronizing-a-live-copy}

Synchroniseer een pagina voor live kopieën om wijzigingen in de inhoud van de bron naar de live kopie over te brengen.

#### Een actieve kopie van pagina-eigenschappen synchroniseren {#synchronize-a-live-copy-from-page-properties}

Synchroniseer een live kopie om wijzigingen van de bron naar de livecopy over te brengen.

>[!NOTE]
>
>Het synchroniseren voert de rollout configuraties uit die [ op de trekker van de Uitvoer ](/help/sites-administering/msm-sync.md#rollout-triggers) gebruiken.

1. In de **console van Plaatsen**, selecteer de levende exemplaarpagina en open de eigenschappen.
1. Open het **Levende 1&rbrace; lusje van het Exemplaar &lbrace;.**
1. Klik **synchroniseren**.

   ![ synchroniseren ](assets/chlimage_1-224.png)

   De bevestiging zal worden gevraagd, gebruik **Synchronisatie** te werk te gaan.

#### Een actieve kopie synchroniseren vanuit het overzicht Live kopie {#synchronize-a-live-copy-from-the-live-copy-overview}

De [ synchroniseer actie is ook beschikbaar bij het Levende Overzicht van het Exemplaar ](/help/sites-administering/msm-livecopy-overview.md#using-the-live-copy-overview), wanneer een Levende pagina van het Exemplaar wordt geselecteerd.

1. Open het [ Levende Overzicht van het Exemplaar ](/help/sites-administering/msm-livecopy-overview.md#using-the-live-copy-overview) en selecteer een Levende Pagina van het Exemplaar.
1. Selecteer **Synchroniseer** van de toolbar.
1. Bevestig de **actie van de Uitvoer** in de dialoog na het specificeren van of u wilt omvatten:

   * **Pagina en Subpagina&#39;s**
   * **slechts Pagina**

   ![ bevestig rollout ](assets/chlimage_1-225.png)

## Live kopie van inhoud wijzigen {#changing-live-copy-content}

Als u inhoud voor live kopieën wilt wijzigen, kunt u:

* Voeg alinea&#39;s toe aan de pagina.
* Bestaande inhoud bijwerken door de overerving van live kopieën voor een pagina of component te verbreken.

>[!NOTE]
>
>Als u handmatig een pagina maakt in de live kopie, is deze lokaal bij de live kopie, wat betekent dat er geen bijbehorende bronpagina aan is gekoppeld.
>
>De beste praktijken om een lokale pagina tot stand te brengen die deel van de verhouding uitmaakt zouden het in de bron moeten creëren en (diepe) rollout doen. Hierdoor wordt de pagina lokaal gemaakt als live kopieën.

>[!NOTE]
>
>Conflicten kunnen optreden als er nieuwe pagina&#39;s met dezelfde paginanaam worden gemaakt in zowel de vertakking Verblauwdrukken als een afhankelijke vertakking voor live kopieën.
>
>Zulke [ conflicten moeten worden behandeld en op rollout ](/help/sites-administering/msm-rollout-conflicts.md) worden opgelost.
>

### Componenten toevoegen aan een Live Copy-pagina {#adding-components-to-a-live-copy-page}

Voeg op elk gewenst moment componenten toe aan een pagina voor live kopieën. De overervingsstatus van de live kopie en het bijbehorende alineasysteem bepaalt niet hoe u componenten kunt toevoegen.

Wanneer de pagina met live kopieën wordt gesynchroniseerd met de bronpagina, blijven de toegevoegde componenten ongewijzigd. Zie ook [ Veranderend de Orde van Componenten op een Levende Pagina van het Exemplaar ](#changing-the-order-of-components-on-a-live-copy-page).

>[!NOTE]
>
>Wijzigingen die lokaal worden aangebracht in een component die als container is gemarkeerd, worden niet overschreven door de inhoud van de blauwdruk op een rollout. Zie [&#128279;](/help/sites-administering/msm-best-practices.md#components-and-container-synchronization) Beste praktijken MSM  voor meer informatie.

### Overerving voor een pagina onderbreken {#suspending-inheritance-for-a-page}

Wanneer u een live kopie maakt, wordt de live kopieerconfiguratie opgeslagen op de hoofdpagina van de gekopieerde pagina&#39;s. Alle onderliggende pagina&#39;s van de hoofdpagina nemen de configuraties van de actieve kopie over. De componenten op de bibliotheekpagina&#39;s erven ook de live kopieerconfiguratie.

U kunt de overerving van live kopieën voor een live kopieerpagina opschorten, zodat u pagina-eigenschappen en -componenten kunt wijzigen. Wanneer u overerving onderbreekt, worden de pagina-eigenschappen en -componenten niet meer gesynchroniseerd met de bron.

>[!NOTE]
>
>U kunt [ een levend exemplaar ](#detaching-a-live-copy) van zijn blauwdruk ook losmaken om alle verbindingen te verwijderen. De handeling Loskoppelen is permanent en niet-omkeerbaar.

>[!NOTE]
>
>Als de component als container wordt gemerkt, zijn de annulering en onderbreekt acties niet op zijn kindcomponenten van toepassing. Zie ook [ Beste praktijken MSM ](/help/sites-administering/msm-best-practices.md#components-and-container-synchronization) voor extra informatie.

#### Overerving van pagina-eigenschappen onderbreken {#suspending-inheritance-from-page-properties}

Overerving op een pagina opschorten:

1. Open de eigenschappen van de levende exemplaarpagina of gebruikend het **bevel van de Eigenschappen van de Mening** van de **console van Plaatsen** of het gebruiken van **Informatie van de Pagina** op de paginatoolbar.
1. Klik het **Levende Exemplaar** lusje.
1. Selecteer **Onderbreking** van de toolbar. U kunt vervolgens een van de volgende opties selecteren:

   * **Uitstel**: huidige slechts pagina
   * **Opschorting met kinderen**: huidige pagina samen met om het even welke kindpagina&#39;s

1. Selecteer **Onderbreking** op de bevestigingsdialoog.

#### Overerving van het Live Copy-overzicht opschorten {#suspending-inheritance-from-the-live-copy-overview}

De [ opschortende actie is ook beschikbaar bij het Levende Overzicht van het Exemplaar ](/help/sites-administering/msm-livecopy-overview.md#using-the-live-copy-overview), wanneer een Levende pagina van het Exemplaar wordt geselecteerd.

1. Open het [ Levende Overzicht van het Exemplaar ](/help/sites-administering/msm-livecopy-overview.md#using-the-live-copy-overview) en selecteer een Levende Pagina van het Exemplaar.
1. Selecteer **Onderbreking** van de toolbar.
1. Selecteer de gewenste optie uit:

   * **Suspend**
   * **Opschorting met kinderen**

   ![ Uitgezocht aangewezen Opschorting optie ](assets/chlimage_1-226.png)

1. Bevestig **Onderbreking** actie in de **Levende dialoog van het Exemplaar** onderbreken:

   ![ opschortende actie ](assets/chlimage_1-227.png)

### Overerving voor een pagina hervatten {#resuming-inheritance-for-a-page}

Het onderbreken van overerving van live-kopieën voor een pagina is een tijdelijke handeling. Zodra opgeschort wordt de **Hervatten** actie beschikbaar, toestaand u om de levende verhouding opnieuw op te nemen.

Wanneer u overerving weer inschakelt, wordt de pagina niet automatisch gesynchroniseerd met de bron. U kunt een synchronisatie aanvragen, als dit vereist is:

* In **hervat**/**keert** dialoog terug; bijvoorbeeld:

  ![ hervatten of terugkeren ](assets/chlimage_1-228.png)

* In een later stadium, door de synchronisatieactie manueel te selecteren.

>[!CAUTION]
>
>Wanneer u overerving weer inschakelt, wordt de pagina niet automatisch gesynchroniseerd met de bron. U kunt handmatig een synchronisatie aanvragen als dat nodig is. Dit kan gebeuren bij het hervatten of later.

#### Overerving van pagina-eigenschappen hervatten {#resuming-inheritance-from-page-properties}

Zodra [&#128279;](#suspending-inheritance-from-page-properties) opgeschort **hervat** actie in de toolbar van de paginaeigenschappen wordt:

![ Hervatten ](assets/chlimage_1-229.png)

Als deze optie is geselecteerd, wordt het dialoogvenster weergegeven. U kunt, indien nodig, een synchronisatie selecteren en de actie vervolgens bevestigen.

#### Een Live Copy-pagina hervatten vanuit het Live Copy-overzicht {#resume-a-live-copy-page-from-the-live-copy-overview}

De [ actie van het Hervatten is ook beschikbaar bij het Levende Overzicht van het Exemplaar ](/help/sites-administering/msm-livecopy-overview.md#using-the-live-copy-overview), wanneer een Levende pagina van het Exemplaar wordt geselecteerd.

1. Open het [ Levende Overzicht van het Exemplaar ](/help/sites-administering/msm-livecopy-overview.md#using-the-live-copy-overview) en selecteer een Levende Pagina van het Exemplaar die is opgeschort; het wordt getoond als **GEANNULEERDE OVERERVING**.
1. Selecteer **Hervatten** van de toolbar.
1. Wijs erop of u de pagina na het terugkeren van overerving wilt synchroniseren, dan de **Actie van het Hervatten** in de **Levende dialoog van het Exemplaar van de Hervatten** bevestigen.

### Overervingsdiepte wijzigen (Ondiep/Ondiep) {#changing-inheritance-depth-shallow-deep}

Op een bestaande live kopie kunt u de diepte van een pagina wijzigen, dat wil zeggen of onderliggende pagina&#39;s worden opgenomen.

* Schakelen naar een oppervlakkige live kopie:

   * Zal onmiddellijk effect hebben en is niet omkeerbaar.

      * Onderliggende pagina&#39;s worden expliciet losgekoppeld van de actieve kopie. Verdere wijzigingen op kinderen kunnen niet bewaard worden als ze ongedaan worden gemaakt.

      * Hiermee verwijdert u alle afstammingen `LiveRelationships`, zelfs als er `LiveCopies` is genest.

* Schakelen naar een diepe live kopie:

   * Onderliggende pagina&#39;s blijven ongewijzigd.
   * Om het effect van de schakelaar te zien, kunt u uitlooptraject maken, worden om het even welke inhoudswijzigingen toegepast volgens de uitrolconfiguratie.

* Het schakelen naar een oppervlakkige levende kopie, dan terug naar diep:

   * Alle onderliggende items van de (eerdere) oppervlakkige live kopie worden behandeld alsof ze handmatig zijn gemaakt en worden daarom met `[oldname]_msm_moved name` van de lijst verwijderd.

U kunt als volgt de diepte opgeven of wijzigen:

1. Open de eigenschappen van de levende exemplaarpagina of gebruikend het **bevel van de Eigenschappen van de Mening** van de **console van Plaatsen** of het gebruiken van **Informatie van de Pagina** op de paginatoolbar.
1. Klik het **Levende Exemplaar** lusje.
1. In de **sectie van de Configuratie**, plaats of ontruim de **Levende optie van de Overerving van het Exemplaar** afhankelijk van of de kindpagina&#39;s inbegrepen zijn:

   * gecontroleerd - een diepe levende kopie (de kindpagina&#39;s worden omvat)
   * clear - een oppervlakkige live kopie (onderliggende pagina&#39;s zijn uitgesloten)

   >[!CAUTION]
   >
   >Het overschakelen naar een oppervlakkige live kopie heeft onmiddellijk effect en is niet-omkeerbaar.
   >
   >Zie [ Levende Exemplaren - Samenstelling ](/help/sites-administering/msm.md#live-copies-composition) voor meer informatie.

1. Klik **sparen** om uw updates voort te zetten.

### Overerving voor een component annuleren {#cancelling-inheritance-for-a-component}

Annuleer de overerving van de live kopie voor een component zodat de component niet meer wordt gesynchroniseerd met de broncomponent. U kunt overerving indien nodig op een later tijdstip inschakelen.

>[!NOTE]
>
>Als de component als container wordt gemerkt, zijn de annulering en onderbreekt acties niet op zijn kindcomponenten van toepassing. Zie ook [ Beste praktijken MSM ](/help/sites-administering/msm-best-practices.md#components-and-container-synchronization) voor extra informatie.

>[!NOTE]
>
>Wanneer u overerving weer inschakelt, wordt de component niet automatisch gesynchroniseerd met de bron. U kunt handmatig een synchronisatie aanvragen als dit vereist is.

Overerving annuleren om de inhoud van de component te wijzigen of de component te verwijderen:

1. Klik op de component waarvoor u overerving wilt annuleren.

   ![ Uitgezochte component voor annuleren overervingsactie ](assets/chlimage_1-230.png)

1. Voor de componententoolbar, klik **annuleer Overerving** pictogram.

   ![ annuleert Overerving ](do-not-localize/chlimage_1-8.png)

1. In het Cancel de dialoogvakje van de Overerving, bevestig de actie met **ja**.

   De werkbalk van de component wordt bijgewerkt en bevat alle (toepasselijke) bewerkingsopdrachten.

### Overerving voor een component opnieuw inschakelen {#re-enabling-inheritance-for-a-component}

Om overerving voor een component toe te laten, klik **re-enable het pictogram van de Overerving** op de componententoolbar.

![ re-enable overerving ](do-not-localize/chlimage_1-9.png)

### De volgorde van componenten op een Live Copy-pagina wijzigen {#changing-the-order-of-components-on-a-live-copy-page}

Als een live kopie componenten bevat die onderdeel zijn van een alineasysteem, worden de volgende regels toegepast bij de overerving van dat alineasysteem:

* De volgorde van componenten in een overgeërfd alineasysteem kan worden gewijzigd, zelfs als overerving is ingesteld.
* Bij rollout wordt de volgorde van de componenten hersteld op basis van de blauwdruk. als er vóór de uitrol nieuwe componenten aan de live kopie zijn toegevoegd , worden deze opnieuw gerangschikt , samen met de componenten waarboven ze zijn toegevoegd .
* Als de overerving van het alineasysteem wordt geannuleerd, wordt de volgorde van componenten niet hersteld bij de rollout en blijft deze zoals in de live kopie.

>[!NOTE]
>
>Wanneer het terugkeren van een geannuleerde overerving op een paragraafsysteem, zal de orde van componenten **niet automatisch worden hersteld** van de blauwdruk. U kunt handmatig een synchronisatie aanvragen als dit vereist is.

Gebruik de volgende procedure om de overname van het alineasysteem te annuleren.

1. Open de pagina voor live kopiëren.
1. Sleep een bestaande component naar een nieuwe locatie op de pagina.
1. In **annuleer Overerving** dialoogdoos, bevestig de actie met **ja**.

### Eigenschappen van een Live Copy-pagina overschrijven {#overriding-properties-of-a-live-copy-page}

De pagina-eigenschappen van een pagina van Live Copy worden standaard overgeërfd (en kunnen niet worden bewerkt) van de bronpagina.

U kunt overerving voor een eigenschap annuleren wanneer u de eigenschapswaarde voor de live kopie moet wijzigen. Een koppelingspictogram geeft aan dat overerving is ingeschakeld voor de eigenschap.

![ annuleert overerving van bezit ](assets/chlimage_1-231.png)

Wanneer u overerving annuleert, kunt u de waarde van de eigenschap wijzigen. Een pictogram voor verbroken koppelingen geeft aan dat overerving wordt geannuleerd.

![ bezit van de Verandering wanneer de erfenis gebroken ](assets/chlimage_1-232.png)

U kunt overerving voor een eigenschap indien nodig later opnieuw inschakelen.

>[!NOTE]
>
>Wanneer u overerving opnieuw inschakelt, wordt de pagina-eigenschap voor live kopiëren niet automatisch gesynchroniseerd met de eigenschap source. U kunt handmatig een synchronisatie aanvragen als dit vereist is.

1. Open de eigenschappen van de levende exemplaarpagina gebruikend of de **optie van de Eigenschappen van de Mening** van de **console van Plaatsen** of **pictogram van de Informatie van de Pagina** op de paginaboolbar.
1. Als u de overerving van een eigenschap wilt annuleren, klikt u op het koppelingspictogram rechts van de eigenschap.

   ![ annuleert overerving van bezit ](do-not-localize/chlimage_1-10.png)

1. In **annuleer de bevestigingsdialoog van de Overerving**, klik **ja**.

### Eigenschappen van een Live Copy-pagina herstellen {#revert-properties-of-a-live-copy-page}

Om overerving voor een bezit toe te laten, klik het **Revert pictogram van de Overerving** dat naast het bezit verschijnt.

![ keert Overerving ](do-not-localize/chlimage_1-11.png) terug

### Live Copy-pagina opnieuw instellen {#resetting-a-live-copy-page}

Een pagina voor live kopiëren opnieuw instellen op:

* Alle annuleringen van overerving verwijderen
* Hiermee keert u de pagina terug naar hetzelfde frame als de bronpagina.

Het opnieuw instellen beïnvloedt de wijzigingen die u hebt aangebracht in pagina-eigenschappen, het alineasysteem en de componenten.

#### Een actieve pagina voor kopiëren herstellen vanuit de pagina-eigenschappen {#reset-a-live-copy-page-from-the-page-properties}

1. In de **console van Plaatsen**, selecteer de levende exemplaarpagina en selecteer **Eigenschappen van de Mening**.
1. Open het **Levende 1&rbrace; lusje van het Exemplaar &lbrace;.**
1. Selecteer **Terugstellen** van de toolbar.

   ![ Terugstellen ](assets/chlimage_1-233.png)

1. In het **Levende de dialoogvakje van het Exemplaar van het Terugstellen**, bevestig met **Terugstellen**.

#### Een Live Copy-pagina herstellen vanuit het Live Copy-overzicht {#reset-a-live-copy-page-from-the-live-copy-overview}

De [ actie van het Terugstellen is ook beschikbaar bij het Levende Overzicht van het Exemplaar ](/help/sites-administering/msm-livecopy-overview.md#using-the-live-copy-overview), wanneer een Levende pagina van het Exemplaar wordt geselecteerd.

1. Open het [ Levende Overzicht van het Exemplaar ](/help/sites-administering/msm-livecopy-overview.md#using-the-live-copy-overview) en selecteer een Levende Pagina van het Exemplaar.
1. Selecteer **Terugstellen** van de toolbar.
1. Bevestig de **1&rbrace; actie van het Terugstellen &lbrace;in de** Levende dialoog van het Exemplaar van het Terugstellen **:**

   ![ Bevestig Terugstellen ](assets/chlimage_1-234.png)

## Een Live Copy-pagina vergelijken met een vervagingspagina {#comparing-a-live-copy-page-with-a-blueprint-page}

Om de veranderingen te volgen u hebt aangebracht, kunt u de blauwdrukpagina in **Verwijzingen** bekijken en het met zijn levende exemplaarpagina vergelijken:

1. In de **console van Plaatsen**, [ navigeert aan een blauwdruk of een levende exemplaarpagina en selecteert het ](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources).
1. Open het **[paneel van Verwijzingen](/help/sites-authoring/basic-handling.md#references)** en selecteer:

   * **Vervaging** (wanneer een levende geselecteerde exemplaarpagina)
   * **Levende Exemplaren** (wanneer een geselecteerde blauwdrukpagina)

1. Selecteer vervolgens uw specifieke live kopie:

   * **vergelijk met Vervaging** (wanneer een levende exemplaarpagina selecteerde)
   * **vergelijk met Levend Exemplaar** (wanneer een geselecteerde blauwdrukpagina)

   Bijvoorbeeld:

   ![ vergelijk ](assets/chlimage_1-235.png)

1. De twee pagina&#39;s (live kopie en blauwdruk) worden naast elkaar geopend.

   Voor volledige informatie over het gebruiken van deze eigenschap zie [ Afschuiving van de Pagina ](/help/sites-authoring/page-diff.md).

## Een actieve kopie ontkoppelen {#detaching-a-live-copy}

Met Loskoppelen verwijdert u permanent de live relatie tussen een live kopie en de bron-/blauwdrukpagina. Alle MSM-relevante eigenschappen worden verwijderd uit de live kopie en de live kopieerpagina&#39;s worden een zelfstandige kopie.

>[!CAUTION]
>
>U kunt de live relatie niet meer herstellen nadat u de live kopie hebt losgekoppeld.
>
>Om de levende verhouding met de optie van het later opnieuw opnemen van het te verwijderen, kunt u [ levende exemplaarovererving ](#suspending-inheritance-for-a-page) voor de pagina annuleren.

Er zijn implicaties op waar binnen de boom die u **gebruikt losmaken**:

* **losmaken op een Wortel- Pagina van een LiveCopy**

  Wanneer deze bewerking wordt uitgevoerd op de hoofdpagina van een live kopie, wordt de live relatie tussen alle pagina&#39;s van de blauwdruk en de bijbehorende livecopy verwijderd.

  Verdere veranderingen in pagina&#39;s in de blauwdruk (zoals was) **zullen niet** de livecopy (zoals was) beïnvloeden.

* **losmaken op een Subpagina van een LiveCopy**

  Wanneer deze bewerking wordt uitgevoerd op een subpagina (of vertakking) binnen een live kopie:

   * de live relatie is verwijderd voor die subpagina (of vertakking)
   * en de (sub)pagina&#39;s in de levende exemplaartak worden behandeld alsof zij manueel waren gecreeerd.

  *Nochtans*, zijn de subpagina&#39;s nog onderworpen aan de levende verhouding van de oudertak zodat zal een verdere uitrol van de blauwdrukpagina(s) allebei:

   1. Wijzig de naam van de losgekoppelde pagina(&#39;s):

      * Dit komt omdat MSM hen als manueel gecreëerde pagina&#39;s beschouwt die een conflict veroorzaken aangezien zij de zelfde naam zoals de levenspagina&#39;s hebben het probeert te creëren.

   1. Maak een pagina (livecopy) met de oorspronkelijke naam, die de wijzigingen bevat die u tijdens de rollout hebt aangebracht.

  >[!NOTE]
  >
  >Zie &lbrace;de Conflicten van de Uitvoer MSM [&#128279;](/help/sites-administering/msm-rollout-conflicts.md) voor details van dergelijke situaties.

### Een actieve pagina voor kopiëren loskoppelen van de pagina-eigenschappen {#detach-a-live-copy-page-from-the-page-properties}

Een actieve kopie loskoppelen:

1. In de **console van Plaatsen**, selecteer de levende exemplaarpagina en klik **Eigenschappen van de Mening**.
1. Open het **Levende 1&rbrace; lusje van het Exemplaar &lbrace;.**
1. Voor de toolbar, uitgezochte **maak** los.

   ![ losmaken ](assets/chlimage_1-236.png)

1. Een bevestigingsdialoog wordt getoond, wordt uitgezocht **losgemaakt** om de actie te voltooien.

### Een Live Copy-pagina loskoppelen van het Live Copy-overzicht {#detach-a-live-copy-page-from-the-live-copy-overview}

De [ ontkoppelde actie is ook beschikbaar bij het Levende Overzicht van het Exemplaar ](/help/sites-administering/msm-livecopy-overview.md#using-the-live-copy-overview), wanneer een Levende pagina van het Exemplaar wordt geselecteerd.

1. Open het [ Levende Overzicht van het Exemplaar ](/help/sites-administering/msm-livecopy-overview.md#using-the-live-copy-overview) en selecteer een Levende Pagina van het Exemplaar.
1. Selecteer **losmaken** van de toolbar.
1. Bevestig **losmaken** actie in de **Levende dialoog van het Exemplaar** loskoppelen:

   ![ bevestig los ](assets/chlimage_1-237.png)
