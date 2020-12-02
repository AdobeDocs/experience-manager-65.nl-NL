---
title: '"Inhoud opnieuw gebruiken: Multi Site Manager en Live Copy"'
seo-title: '"Inhoud opnieuw gebruiken: Multi Site Manager en Live Copy"'
description: Leer meer over het opnieuw gebruiken van inhoud met Levende Exemplaren en de Multisite Manager.
seo-description: Leer meer over het opnieuw gebruiken van inhoud met Levende Exemplaren en de Multisite Manager.
uuid: 9f955226-8fc9-4357-b90c-c6896b0dc4b4
contentOwner: Alison Heimoz
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: site-features
content-type: reference
discoiquuid: c21debc3-ecf4-4aa9-ab5a-18ddd5cf2fff
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '2684'
ht-degree: 0%

---


# Inhoud opnieuw gebruiken: Beheer van meerdere sites en Live Copy{#reusing-content-multi-site-manager-and-live-copy}

Met MSM (Multi Site Manager) kunt u dezelfde site-inhoud op meerdere locaties gebruiken. MSM gebruikt de functie Live Copy om dit te bereiken:

* Met MSM kunt u:

   * Inhoud eenmaal maken en vervolgens
   * Kopieer deze inhoud naar en hergebruik deze inhoud in andere gebieden ([live kopieën](#live-copies)) van dezelfde of andere sites.

* MSM handhaaft dan de (levende) verhouding tussen uw broninhoud en zijn levende exemplaren zodat:

   * Wanneer u wijzigingen aanbrengt in de broninhoud, worden de bron- en live kopieën gesynchroniseerd (om deze wijzigingen ook toe te passen op de live kopieën).
   * U kunt de inhoud van live kopieën aanpassen door de live relatie voor afzonderlijke subpagina&#39;s en/of componenten te verbreken. Hierdoor worden wijzigingen in de bron niet meer toegepast op de live kopie.

Op deze en de volgende pagina&#39;s worden de gerelateerde kwesties besproken:

* [Actieve kopieën maken en synchroniseren](/help/sites-administering/msm-livecopy.md)
* [Console voor live kopiëren](/help/sites-administering/msm-livecopy-overview.md)
* [Synchronisatie van actieve kopie configureren](/help/sites-administering/msm-sync.md)
* [Conflicten MSM-rollout](/help/sites-administering/msm-rollout-conflicts.md)
* [Aanbevolen MSM-procedures](/help/sites-administering/msm-best-practices.md)

## Mogelijke scenario&#39;s {#possible-scenarios}

Er zijn vele gebruiksgevallen voor MSM en levende exemplaren, sommige scènes omvatten:

* **Multinationals - wereldwijd tot lokaal bedrijf**

   Een typisch gebruiksgeval dat MSM steunt is inhoud in verscheidene multinationale plaatsen van het zelfde-Taal opnieuw te gebruiken. Hierdoor kan de kerninhoud opnieuw worden gebruikt, terwijl nationale variaties mogelijk zijn.

   Bijvoorbeeld, wordt de Engelse sectie van de steekproef van de Plaats van de Verwijzing Wij.Retail gecreeerd voor klanten in de V.S. De meeste inhoud in deze plaats kan ook voor andere plaatsen worden gebruikt Web.Retail die aan Engelstalige klanten van verschillende landen en culturen behandelen. De kerninhoud blijft voor alle sites hetzelfde, terwijl regionale aanpassingen kunnen worden aangebracht.

   De volgende structuur kan voor plaatsen voor de Verenigde Staten, het Verenigd Koninkrijk, Canada, en Australië worden gebruikt:

   ```xml
   /content
       |- we.retail
           |- language-masters
               |- en
       |- we.retail
           |- us
               |- en
       |- we.retail
           |- gb
               |- en
       |- we.retail
           |- ca
               |- en
       |- we.retail
           |- au
               |- en
   ```

   >[!NOTE]
   >
   >MSM vertaalt de inhoud niet. Het wordt gebruikt om de vereiste structuur tot stand te brengen en de inhoud op te stellen.
   >
   >
   >Zie [Inhoud vertalen voor meertalige sites](/help/sites-administering/translation.md) als u een dergelijk voorbeeld wilt uitbreiden.

* **Nationaal — Hoofdkantoor van regionale afdelingen**

   Een bedrijf met een netwerk van dealers zou ook aparte websites voor hun individuele dealers willen, elk een variant van de hoofdsite die door het hoofdkantoor wordt aangeboden. Dit kan het geval zijn voor één enkele onderneming met meerdere regionale kantoren, of voor een nationaal franchisesysteem dat bestaat uit een centrale franchisegever en meerdere lokale franchisehouders.

   Het hoofdkantoor kan de kerninformatie verstrekken, terwijl de regionale entiteiten lokale informatie kunnen toevoegen, zoals contactgegevens, openingstijden en evenementen.

   ```xml
   /content
       |- head-office-Berlin
       |- branch-Hamburg
       |- branch-Stuttgart
       |- branch-Munich
       |- branch-Frankfurt
   ```

* **Meerdere versies**

   Of u kunt MSM gebruiken om versies van een specifieke subtak tot stand te brengen, bijvoorbeeld, een steunsubsite die details van de verschillende versies van een specifiek product houdt, waar de basisinformatie constant blijft en slechts de bijgewerkte eigenschappen moeten worden veranderd:

   ```xml
   /content
       |- support
           |- product X
               |- v5.0
               |- v4.0
               |- v3.0
               |- v2.0
               |- v1.0
   ```

   >[!NOTE]
   >
   >In een dergelijk scenario is het altijd de vraag of er een eenvoudige kopie moet worden gemaakt of dat er live kopieën moeten worden gemaakt.
   >
   >Er is een evenwicht tussen:
   >
   >  * Hoeveel van de kerninhoud zal over de veelvoudige versies moeten bijwerken.
   >
   >Tegen:
   >
   >  * Hoeveel van de afzonderlijke kopieën moeten worden aangepast.


## MSM van UI {#msm-from-the-ui}

MSM is direct toegankelijk in UI gebruikend diverse opties van de aangewezen console. Voor een inleiding geeft u de volgende hoofdlocaties weer:

* **Site**  maken (**sites**)

   * Met MSM kunt u meerdere websites beheren die gemeenschappelijke inhoud delen. websites worden bijvoorbeeld vaak aangeboden voor een internationaal publiek , zodat de meeste inhoud in alle landen gemeenschappelijk is , met een subset van de inhoud die specifiek is voor elk land afzonderlijk . Met MSM kunt u [live kopieën maken die automatisch een of meer sites bijwerken op basis van uw bronsite](/help/sites-administering/msm-livecopy.md#creating-a-live-copy-of-a-site-from-a-blueprint-configuration). Dit helpt u ook om een gemeenschappelijke basisstructuur af te dwingen, de gemeenschappelijke inhoud over de veelvoudige plaatsen te gebruiken, een gemeenschappelijke blik te handhaven en zich te concentreren inspanningen op het beheren van de inhoud die eigenlijk tussen de plaatsen verschilt.
   * Vereist een vooraf bepaalde blauwdrukconfiguratie om de bron te specificeren.
   * Hiermee maakt u een live kopie van de (vooraf gedefinieerde) bron.
   * Biedt de gebruiker de knop **Uitvoeren**.

* **Live kopie**  maken (**sites**)

   * Met MSM kunt u [een ad-hoc (eenmalige) live kopie van een afzonderlijke pagina of subvertakking van een website maken](/help/sites-administering/msm-livecopy.md#creating-a-live-copy-of-a-page); Bijvoorbeeld, het dupliceren van een subtak om informatie over een nieuwe/bijgewerkte versie van een product te verstrekken.
   * Hiermee maakt u een live ad-hockopie (geen configuratie voor blauwdrukken vereist).
   * Kan worden gebruikt om (direct) een live kopie van elke pagina of vertakking te maken.
   * Vereist **Synchronize** (verstrekt niet **Rollout** knoop).

* **Eigenschappen**  weergeven (**sites**)

   * Deze optie helpt u, waar van toepassing, [uw live kopie te controleren](/help/sites-administering/msm-livecopy.md#monitoring-your-live-copy) door informatie op te geven over de verwante **actieve kopie** y of **blauwdruk**.

* **Verwijzingen** (**sites**)

   * De [References](/help/sites-authoring/basic-handling.md#references) rail verstrekt informatie over **Actieve exemplaren** samen met toegang tot aangewezen acties.

* **Overzicht**  van live kopiëren (**sites**)

   * Met deze console kunt u uw blauwdruk en de bijbehorende live kopieën [ weergeven en beheren.](/help/sites-administering/msm-livecopy-overview.md)

* **Blauwdrukken**  (**gereedschappen**  -  **Sites**)

   * Met deze console kunt u [uw blauwdrukconfiguraties maken en beheren](/help/sites-administering/msm-livecopy.md#creating-a-blueprint-configuration).

>[!NOTE]
>
>De aspecten van de functionaliteit MSM worden gebruikt in verscheidene andere AEM eigenschappen (bijvoorbeeld, Lanceringen, Catalogus); in deze gevallen wordt de levende kopie beheerd door die eigenschap.

### Gebruikte termen {#terms-used}

Als inleiding geeft de volgende tabel een overzicht van de belangrijkste termen die met MSM worden gebruikt; deze zullen nader worden toegelicht in de volgende secties en pagina &#39; s :

<table>
 <tbody>
  <tr>
   <td><strong>Term</strong></td>
   <td><strong>Definitie</strong></td>
   <td><strong>Meer details</strong></td>
  </tr>
  <tr>
   <td><strong>Bron</strong></td>
   <td>De originele pagina's.</td>
   <td>Gelijk aan blauwdrukken en/of vervagingspagina's.</td>
  </tr>
  <tr>
   <td><strong>Live kopie</strong></td>
   <td>De kopie (van de bron), onderhouden door synchronisatiehandelingen zoals gedefinieerd door de rollout-configuraties. </td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Configuratie van live kopiëren</strong></td>
   <td>Definitie van de configuratiedetails voor een levende kopie.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Live relatie</strong><br /> </td>
   <td>een effectieve definitie van de erfenis van een bepaalde bron; de verbinding(en) tussen de bron en live kopieën.<br /> </td>
   <td>Hiermee zorgt u ervoor dat wijzigingen in de bron kunnen worden gesynchroniseerd met de live kopie.</td>
  </tr>
  <tr>
   <td><strong>Blauwdruk</strong></td>
   <td>Gelijk aan bron.</td>
   <td>Kan worden gedefinieerd door een blauwdrukconfiguratie.</td>
  </tr>
  <tr>
   <td><strong>Blauwdrukconfiguratie</strong></td>
   <td>Vooraf gedefinieerde configuratie die een bronpad opgeeft.</td>
   <td>Wanneer in een blauwdrukconfiguratie naar een blauwdrukpagina wordt verwezen, wordt de opdracht Uitrollen beschikbaar.</td>
  </tr>
  <tr>
   <td><strong>Synchronisatie</strong></td>
   <td>De generische termijn voor de synchronisatie van inhoud tussen de bron en de levende exemplaren (door zowel <strong>Uitvoer</strong> als <strong>Synchronize</strong>).</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Uitrol</strong><br /> </td>
   <td>Synchroniseert van bron naar livecopy.<br /> Kan worden geactiveerd door een auteur (op een blauwdrukpagina) of door een systeemgebeurtenis (zoals gedefinieerd door de rollout-configuratie).</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Rolloutconfiguratie</strong></td>
   <td>Regels die bepalen welke eigenschappen worden gesynchroniseerd, hoe en wanneer.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Synchroniseren</strong></td>
   <td>Een handmatig verzoek om synchronisatie, uitgevoerd vanaf de bibliotheekpagina's.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Overerving</strong></td>
   <td>Een pagina/component voor live kopiëren overerft de inhoud van de bronpagina/component wanneer de synchronisatie plaatsvindt.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Onderbreken</strong></td>
   <td>Hiermee verwijdert u tijdelijk de live relatie tussen een live kopie en de bijbehorende blauwdrukpagina.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Loskoppelen</strong></td>
   <td>Hiermee verwijdert u permanent de live relatie tussen een live kopie en de bijbehorende blauwdrukpagina.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Herstellen</strong></td>
   <td><p>Een pagina voor live kopiëren opnieuw instellen op:</p>
    <ul>
     <li>Alle annuleringen van overerving verwijderen en<br /> </li>
     <li>Hiermee keert u de pagina terug naar hetzelfde frame als de bronpagina.</li>
    </ul> <p>Herstellen is van invloed op wijzigingen die u hebt aangebracht in pagina-eigenschappen, het alineasysteem en de componenten.</p> </td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Ondiep</strong></td>
   <td>Een live kopie van één pagina.</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Diep</strong></td>
   <td>Een live kopie van een pagina, samen met de onderliggende pagina's.</td>
   <td> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Zie [Overzicht van de Java API](/help/sites-developing/extending-msm.md#overview-of-the-java-api) voor de objectnamen.

## Actieve kopieën {#live-copies}

Een live MSM-kopie is een kopie van specifieke site-inhoud waarvoor een live relatie met de oorspronkelijke bron wordt onderhouden:

* De live kopie neemt de inhoud van de bron over.
* De synchronisatie voert de daadwerkelijke overdracht van inhoud uit wanneer de veranderingen in de bron worden aangebracht.
* Een live kopie kan worden beschouwd als:

   * Ondiep: één pagina
   * Diep: de pagina, samen met de onderliggende pagina&#39;s ervan

* De regels van de synchronisatie, genoemd rollout configuraties, bepalen welke eigenschappen worden gesynchroniseerd en wanneer de synchronisatie voorkomt.

In het vorige voorbeeld is `/content/we-retail/language-masters/en` de algemene master site in het Engels. Om de inhoud van deze site opnieuw te gebruiken, worden live kopieën van MSM gemaakt:

* De inhoud onder `/content/we-retail/language-masters/en` is de bron.

* De inhoud onder `/content/we-retail/language-masters/en` wordt gekopieerd onder de `/content/we-retail/us/en/`, `/content/we-retail/gb/en`, `/content/we-retail/ca/en`, en `/content/we-retail/au/en` knopen. Dit zijn de live kopieën.

* Auteurs brengen wijzigingen aan op de pagina&#39;s onder `/content/we-retail/language-masters/en`.
* Wanneer teweeggebracht, synchroniseert MSM deze veranderingen in de levende exemplaren.

### Actieve kopieën - Compositie {#live-copies-composition}

>[!NOTE]
>
>De diagrammen en beschrijvingen in deze sectie vertegenwoordigen momentopnamen van potentiële levende exemplaren. Ze zijn niet volledig, maar bieden een overzicht om specifieke kenmerken te benadrukken.

Wanneer u in eerste instantie een live kopie maakt, worden de geselecteerde bronpagina&#39;s in de live kopie op een 1:1-basis weergegeven. Hierna kunnen ook nieuwe bronnen (pagina&#39;s en/of alinea&#39;s) rechtstreeks in de live kopie worden gemaakt. Het is dus handig om op de hoogte te zijn van deze variaties en van de invloed die deze op synchronisatie hebben. Mogelijke composities zijn:

* [Live kopiëren met pagina&#39;s die niet live zijn gekopieerd](#live-copy-with-non-live-copy-pages)
* [Geneste actieve kopieën](#nested-live-copies)

De basisvorm van een kopie van het origineel is:

* Live kopiëren pagina&#39;s die de geselecteerde bronpagina&#39;s op een 1:1-basis weerspiegelen.
* Eén configuratiedefinitie.
* Een live relatie gedefinieerd voor elke resource:

   * Verbind het levende exemplaarmiddel met zijn blauwdruk/bron.
   * Wordt gebruikt bij het realiseren van overerving en rollout.

* Wijzigingen kunnen [gesynchroniseerd](/help/sites-administering/msm-livecopy.md#synchronizing-your-live-copy) zijn volgens de vereisten.

![chlimage_1-367](assets/chlimage_1-367.png)

#### Live kopiëren met pagina&#39;s van niet-Live-kopie {#live-copy-with-non-live-copy-pages}

Wanneer u een live kopie maakt in AEM kunt u de live kopie van de vertakking zien en door de live kopie navigeren. De normale AEM van de actieve kopie kunt u ook gebruiken. Dit betekent dat u (of een proces) nieuwe bronnen (pagina&#39;s en/of alinea&#39;s) binnen de actieve kopieervertakking kunt maken (bijvoorbeeld `myCanadaOnlyProduct`).

* Dergelijke bronnen hebben geen live relatie met de bron-/blauwdrukpagina&#39;s en zijn niet gesynchroniseerd.
* De scenario&#39;s kunnen voorkomen dat MSM als speciale gevallen behandelt. Wanneer u (of een proces) bijvoorbeeld een pagina maakt met dezelfde positie en naam in zowel de vertakking van de bron/blauwdruk als de vertakking van de actieve kopie. Voor dergelijke situaties zie [Conflicten van de Uitvoer MSM](/help/sites-administering/msm-rollout-conflicts.md) voor meer informatie.

![chlimage_1-368](assets/chlimage_1-368.png)

#### Geneste actieve kopieën {#nested-live-copies}

Wanneer u (of een proces) een [nieuwe pagina binnen een bestaand levend exemplaar ](#live-copy-with-non-live-copy-pages) creeert kan deze nieuwe pagina ook opstelling als levende exemplaar van een verschillende blauwdruk zijn. Dit wordt een geneste live kopie genoemd, waarbij het gedrag van de tweede (binnenste) live kopie op de volgende manier wordt beïnvloed door de eerste (buitenste) live kopie:

* Een uitgebreide rollout die wordt geactiveerd voor de live kopie op hoofdniveau, kan worden voortgezet in de geneste live kopie (bijvoorbeeld als de trigger overeenkomt).
* Alle koppelingen tussen de bronnen worden in de live kopieën herschreven.

   Koppelingen van de tweede naar de eerste blauwdruk worden bijvoorbeeld herschreven als koppelingen van de geneste/tweede live kopie naar de eerste live kopie.

![chlimage_1-369](assets/chlimage_1-369.png)

>[!NOTE]
>
>Als u een pagina binnen de actieve kopieervertakking verplaatst/hernoemt, wordt deze (intern) behandeld als een geneste live kopie, zodat AEM de relaties kan volgen.

#### Gestapelde actieve kopieën {#stacked-live-copies}

Een live kopie wordt een Gestapelde live kopie genoemd wanneer deze wordt gemaakt als het onderliggende element van een oppervlakkige live kopie. Het gedraagt zich op dezelfde manier als [Geneste actieve kopie](#nested-live-copies).

### Bronconfiguraties, blauwdrukken en blauwdrukken {#source-blueprints-and-blueprint-configurations}

Elke pagina of vertakking van pagina&#39;s kan worden gebruikt als bron van een live kopie.

Nochtans, staat MSM u ook toe om een blauwdrukconfiguratie te bepalen die een bronweg specificeert. De voordelen van het gebruik van een blauwdrukconfiguratie zijn:

* Laat de auteur de optie **Uitvoer** op een blauwdruk gebruiken - aan (uitdrukkelijk) duw wijzigingen aan levende exemplaren die van deze blauwdruk erven.
* De auteur toestaan **Site maken/> te gebruiken; hierdoor kan de gebruiker eenvoudig talen selecteren en de structuur van de live kopie configureren .**
* Definieer een standaardrollout-configuratie voor live kopieën die een relatie hebben met de blauwdruk.

De bron voor een live kopie kan bestaan uit gewone pagina&#39;s of pagina&#39;s die door een blauwdrukconfiguratie worden omringd. Beide zijn geldige gebruiksgevallen.

De bron vormt de blauwdruk voor het levende exemplaar. De blauwdruk wordt gedefinieerd wanneer u:

* [Een blauwdrukconfiguratie maken](/help/sites-administering/msm-livecopy.md#creating-a-blueprint-configuration)

   De configuratie definieert (vooraf) de pagina&#39;s die moeten worden gebruikt om de live kopie te maken.

* [Een actieve kopie van een pagina maken](/help/sites-administering/msm-livecopy.md#creating-a-live-copy-of-a-page)

   De pagina&#39;s die worden gebruikt om de live kopie (de bronpagina&#39;s) te maken, zijn de blauwdrukpagina&#39;s.

   Naar de bronpagina kan door een blauwdrukconfiguratie worden verwezen, of niet.

### Uitvoeren en synchroniseren {#rollout-and-synchronize}

Een rollout is de centrale actie MSM die levende exemplaren met hun bron synchroniseert. U kunt rollouts handmatig uitvoeren of automatisch uitvoeren:

* Een [rollout configuratie](#rollout-configurations) kan worden bepaald zodat specifieke [gebeurtenissen](/help/sites-administering/msm-sync.md#rollout-triggers) een rollout kan veroorzaken om automatisch voor te komen.
* Bij het ontwerpen van een blauwdrukpagina kunt u de opdracht [Uitvoer](/help/sites-administering/msm-livecopy.md#rolling-out-a-blueprint) gebruiken om wijzigingen in de actieve kopie door te voeren.

   **Het** bevel Rolloutcommand is beschikbaar op een blauwdrukpagina die door een blauwdrukconfiguratie van verwijzingen wordt voorzien.

   ![chlimage_1-370](assets/chlimage_1-370.png)

* Wanneer het ontwerpen van een levende exemplaarpagina kunt u [Synchronize](/help/sites-administering/msm-livecopy.md#synchronizing-a-live-copy) bevel gebruiken om veranderingen van de bron aan het levende exemplaar te trekken.

   De **Synchronize** bevel is altijd beschikbaar op de levende exemplaarpagina (ongeacht of de bron/blauwdruk pagina door een blauwdrukconfiguratie wordt omvat).

   ![chlimage_1-371](assets/chlimage_1-371.png)

### Uitrolconfiguraties {#rollout-configurations}

Een rollout-configuratie bepaalt wanneer en hoe een live kopie wordt gesynchroniseerd met de broninhoud. Een rollout-configuratie bestaat uit een trigger en een of meer synchronisatiehandelingen:

* **Trigger**

   Een trigger is een gebeurtenis die ervoor zorgt dat de synchronisatie van een live actie plaatsvindt, zoals de activering van een bronpagina. MSM bepaalt de trekkers die u kunt gebruiken.

* **Synchronisatiehandelingen**

   Wordt uitgevoerd op de live kopie om deze te synchroniseren met de bron. Voorbeelden van handelingen zijn het kopiëren van inhoud, het bestellen van onderliggende knooppunten en het activeren van de pagina voor live kopiëren. MSM biedt een aantal synchronisatiehandelingen.

   >[!NOTE]
   >
   >U kunt aangepaste handelingen voor uw instantie maken met de Java API.

De configuraties van de rollout kunnen worden opnieuw gebruikt, zodat meer dan één levende kopie de zelfde rollout configuratie kan gebruiken. Verschillende [implementatieconfiguraties](/help/sites-administering/msm-sync.md#installed-rollout-configurations) zijn opgenomen in een standaardinstallatie.

### Uitrolconflicten {#rollout-conflicts}

Rollouts kunnen ingewikkeld worden, vooral wanneer de auteurs inhoud in zowel de bron als de levende kopie uitgeven, zodat is het nuttig om zich van bewust te zijn hoe AEM om het even welke [conflicten behandelt die tijdens rollout](/help/sites-administering/msm-rollout-conflicts.md) zouden kunnen voorkomen.

### Overerving en synchronisatie opheffen en annuleren {#suspending-and-cancelling-inheritance-and-synchronization}

Elke pagina en component in een live kopie wordt via een live relatie gekoppeld aan de bronpagina en -component ervan. De levende verhouding vormt de synchronisatie van levende exemplaarinhoud van de bron.

U kunt **De overerving van de levende kopie voor een levende exemplaarpagina opheffen &lt;a0/>Opschorsen zodat u pagina-eigenschappen en componenten kunt veranderen.** Wanneer u overerving onderbreekt, worden de pagina-eigenschappen en -componenten niet meer gesynchroniseerd met de bron.

Tijdens het bewerken van een afzonderlijke pagina kunnen auteurs Overerving **Annuleren** voor een component. Wanneer de overerving wordt geannuleerd, wordt de live relatie onderbroken en vindt de synchronisatie niet plaats voor die component. Het annuleren van overerving en synchronisatie is handig wanneer subsecties van de inhoud moeten worden aangepast.

### Live kopie {#detaching-a-live-copy} ontkoppelen

U kunt ook [een live kopie](/help/sites-administering/msm-livecopy.md#detaching-a-live-copy) loskoppelen van de blauwdruk om alle verbindingen te verwijderen.

>[!CAUTION]
>
>De handeling Loskoppelen is permanent en niet-omkeerbaar.

Met Loskoppelen verwijdert u permanent de live relatie tussen een live kopie en de bijbehorende blauwdrukpagina. Alle MSM-relevante eigenschappen worden verwijderd uit de live kopie en de live kopieerpagina&#39;s worden een zelfstandige kopie.

>[!NOTE]
>
>Zie [Een Live kopie loskoppelen](/help/sites-administering/msm-livecopy.md#detaching-a-live-copy) voor meer informatie. met inbegrip van de bijbehorende impact op subpagina&#39;s en bovenliggende pagina&#39;s.

## Standaardstappen voor het gebruik van MSM {#standard-steps-for-using-msm}

De volgende stappen beschrijven de standaardprocedure voor het gebruiken van MSM om inhoud opnieuw te gebruiken en veranderingen in levende exemplaren te synchroniseren.

1. De inhoud van de bronsite ontwikkelen.
1. Bepaal de rollout configuratie aan gebruik.

   1. MSM [installeert verscheidene rollout configuraties](/help/sites-administering/msm-sync.md#installed-rollout-configurations) die aan een aantal gebruiksgevallen kunnen voldoen.
   1. Naar keuze kunt u [een rollout configuratie](/help/sites-administering/msm-sync.md#creating-a-rollout-configuration) indien nodig tot stand brengen.

1. Bepaal waar u [de rollout configuraties aan gebruik ](/help/sites-administering/msm-sync.md#specifying-the-rollout-configurations-to-use) moet specificeren en zonodig vormen.
1. Indien nodig, [creeer een blauwdrukconfiguratie](/help/sites-administering/msm-livecopy.md#creating-a-blueprint-configuration) die de broninhoud van het levende exemplaar identificeert.
1. [Een live kopie](/help/sites-administering/msm-livecopy.md#creating-a-live-copy) maken.
1. Breng de gewenste wijzigingen aan in de broninhoud. U dient het normale proces voor het beoordelen en goedkeuren van inhoud dat uw organisatie heeft ingesteld, te gebruiken.
1. [Schuif ](/help/sites-administering/msm-livecopy.md#rolling-out-a-blueprint) de blauwdruk uit of  [synchroniseer de live ](/help/sites-administering/msm-livecopy.md#synchronizing-a-live-copy) kopie met de wijzigingen.

## MSM {#customizing-msm} aanpassen

MSM verstrekt hulpmiddelen zodat uw implementatie aan de uitzonderlijke ingewikkeldheid kan aanpassen die wanneer het delen van inhoud kan bestaan:

* **Aangepaste implementatieconfiguraties**
   [Maak een ](/help/sites-administering/msm-sync.md#creating-a-rollout-configuration) rollout-configuratie als de geïnstalleerde rollout-configuraties niet aan uw vereisten voldoen. U kunt elke beschikbare uitrolltrigger- en synchronisatiehandeling gebruiken.

* **Aangepaste synchronisatiehandelingen**
   [Maak een aangepaste synchronisatiehandeling ](/help/sites-developing/extending-msm.md#creating-a-new-synchronization-action) wanneer de geïnstalleerde handelingen niet voldoen aan uw specifieke toepassingsvereisten. MSM biedt een Java API voor het maken van aangepaste synchronisatiehandelingen.

## Best practices voor {#best-practices}

De [MSM beste praktijken](/help/sites-administering/msm-best-practices.md) pagina bevat belangrijke informatie betreffende uw implementatie.
