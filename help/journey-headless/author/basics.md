---
title: Grondbeginselen van ontwerpen leren
description: Leer over de concepten en de mechanica van creatie inhoud voor uw Zwaarloze CMS gebruikend Inhoudsfragmenten.
source-git-commit: 38525b6cc14e9f6025564c060b8cfb4f9e0ea473
workflow-type: tm+mt
source-wordcount: '1693'
ht-degree: 1%

---

# Grondbeginselen van ontwerpen voor headless met AEM {#author-headless-basics}

## Het artikel tot nu toe {#story-so-far}

Aan het begin van de [AEM Schrijverreis zonder kopinhoud](overview.md) de [Inleiding](introduction.md) heeft betrekking op de basisbegrippen en de terminologie die relevant zijn voor het ontwerpen van koploze producten.

Dit artikel bouwt hierop voort, zodat u begrijpt hoe u uw eigen inhoud voor uw AEM project zonder titel kunt ontwerpen.

## Doelstelling {#objective}

* **Publiek**: Begin
* **Doelstelling**: Introduceer de basisbeginselen van CMS-authoring zonder koppen:
   * Inleiding tot ontwerpen met AEMaaCS
   * Inleiding tot inhoudsfragmenten

## Basisbewerkingen {#basic-handling}

Voordat u de inhoud van fragmenten gaat beheren, volgt een (zeer) korte inleiding op het gebruik van AEM....maar niets vervangt echt de ervaring van het aanmelden en het proberen om het systeem te gebruiken.

### Auteur en publicatie {#author-preview-publish}

Een AEM installatie bestaat meestal uit minstens twee omgevingen:

* Auteur
* Publicatie

U meldt zich aan, en gebruikt het auteursmilieu om uw inhoud te produceren. Wanneer u klaar bent, publiceert u de inhoud zodat deze algemeen beschikbaar wordt. Voor koploze gebruikers is dit voor andere toepassingen, voor webpagina&#39;s is dit voor lezers op het web.

Zie Concepten ontwerpen voor meer informatie.

### Aanmelden {#signing-in}

Net als bij de meeste systemen moet u zich aanmelden. Als auteur krijgt u de volgende informatie:

* Gebruikersnaam (account)
* Wachtwoord
* Koppeling voor toegang tot het aanmeldingsscherm

Uw account is geconfigureerd met alle rechten die u nodig hebt. Als u om het even welke kwesties hebt, adviseren wij dat u uw intern team van de projectsteun contacteert.

### Navigatie {#navigation}

De eerste keer dat u zich aanmeldt bij een kleine online zelfstudie, worden enkele van de belangrijkste functies van de gebruikersinterface gemarkeerd.

Vervolgens kunt u het navigatievenster gebruiken om toegang te krijgen tot belangrijke gebieden van AEM. Voor inhoudsfragmenten gebruikt u de opdracht **Elementenconsole**.

U kunt het navigatievenster openen door het Adobe-pictogram linksboven te selecteren, gevolgd door het kleine kompaspictogram:

![Navigatievenster](/help/journey-headless/author/assets/headless-journey-author-navigation-01.png)

>[!NOTE]
>Hoewel Inhoudsfragmenten een kenmerk van AEM zijn **Sites**, vindt u deze in de **Activa** console. Dit is een technisch detail dat u niet zou moeten be??nvloeden, maar zou nuttig kunnen zijn om te weten.

Binnen de console kunt u mappen selecteren om naar het inhoudsfragment te navigeren of de broodkruimels (in de koptekst) om een back-up van de structuur te maken.

![Broodkruimels](/help/journey-headless/author/assets/headless-journey-author-navigation-02.png)

### Handelingen, selecteren, weergeven {#actions-selecting-viewing}

De **Activa** console heeft toegewezen **Werkbalken voor handelingen**, en **Snelle handelingen** die u kunt gebruiken nadat u een bron hebt geselecteerd (bijvoorbeeld een map of inhoudsfragment).

De snelle Acties zijn beschikbaar voor ????n enkel middel, zie **Bazel** in het onderstaande voorbeeld:

![Snelle handelingen](/help/journey-headless/author/assets/headless-journey-author-navigation-05.png)

De werkbalk Handelingen biedt toegang tot het volledige scala aan handelingen die voor het huidige scenario gelden. De beschikbare acties kunnen veranderen; bijvoorbeeld, afhankelijk van uw plaats, of of u veelvoudige middelen hebt geselecteerd:

![Werkbalk Handelingen](/help/journey-headless/author/assets/headless-journey-author-navigation-06.png)

U kunt de indeling voor het weergeven van uw bronnen selecteren met de Weergaveselector:

![Kiezer weergeven](/help/journey-headless/author/assets/headless-journey-author-navigation-03.png)

U kunt aanvullende informatie over items weergeven met de spoorkiezer. Dit geeft ook toegang tot extra acties.

![Linkerspoor](/help/journey-headless/author/assets/headless-journey-author-navigation-04.png)

## Inhoudsfragmenten ontwerpen {#authoring-content-fragments}

Dat was dus een zeer snelle inleiding op de AEM Gebruikersinterface (UI), maar hopelijk hebt u de kans gehad om het uit te proberen. Nu komen we neer op je echte interesse - Content Fragments voor Headless.

We moeten de zaken van begin tot eind doorlopen, maar in uw instantie zijn mogelijk al mappen en/of fragmenten gemaakt. Deze bevinden zich mogelijk op verschillende locaties. De beginselen zijn dezelfde.

### Organiseren en navigeren {#organizing-and-navigating}

Tenzij u zeer weinig Inhoudsfragmenten hebt, wilt u deze ordenen - zodat u (en anderen) ze opnieuw kunt vinden.

#### Een map maken {#creating-folder}

U kunt dit doen door een reeks mappen te maken binnen **Bestanden** van de middelenconsole. Selecteer **Maken** optie (rechtsboven), gevolgd door **Map**:

![Map maken, optie](/help/journey-headless/author/assets/headless-journey-author-folder-01.png)

Er wordt een dialoogvenster geopend waarin u de details kunt invoeren en vervolgens kunt bevestigen met **Maken**:

![Map maken, dialoogvenster](/help/journey-headless/author/assets/headless-journey-author-folder-02.png)

#### Paden en tags gebruiken om de in de map beschikbare modellen van inhoudsfragmenten te beperken {#tags-paths-for-models-in-folder}

Deze sectie is iets geavanceerder. Je hebt het niet echt nodig als je gewoon begint en dingen probeert, maar het is *zeer* Dit is handig als u veel fragmenten hebt. Dus het is goed om over te weten - zelfs als je het nog niet helemaal gebruikt.

Uw Content Architect zal alle Content Fragment Models hebben gecreeerd die voor uw huidige project worden vereist, en misschien ook sommige andere projecten. Om de zaken voor zich, en andere auteurs eenvoudig te houden, kunt u de lijst van modellen beperken beschikbaar voor een specifieke omslag.

Nadat u de map hebt gemaakt, kunt u de map openen **Eigenschappen**. Hier zijn diverse lusjes met informatie, en configuratiedetails, over de omslag. Met name voor inhoudsfragmenten kunt u de opdracht **Beleid** om specifieke paden en/of tags voor deze map te defini??ren. Dit beperkt de modellen van het Fragment van de Inhoud beschikbaar voor gebruik in de omslag aangezien het betekent dat de Modellen van het Fragment van de Inhoud aan deze vereisten moeten voldoen alvorens zij kunnen worden gebruikt om fragmenten in deze omslag te produceren.

![Mapeigenschappen maken - beleid](/help/journey-headless/author/assets/headless-journey-author-folder-04.png)

>[!NOTE]
>
>U kunt meer informatie lezen onder Modellen van inhoudsfragmenten - Modellen van inhoudsfragmenten toestaan in de middelenmap.

Vervolgens navigeert u door deze mappen om inhoudsfragmenten te maken en te bewerken.

#### Net voor het geval - Configuratie van Cloud Services van mappen {#cloud-services-folder}

Alleen voor het geval...

U krijgt waarschijnlijk een eerste map waarin u uw mappen kunt maken. Dit is aangezien sommige configuratiedetails (gewoonlijk door een Ontwikkelaar of Beheerder van het Systeem) op de wortelomslag moeten worden toegepast. Dit interesseert u waarschijnlijk niet, maar als nodig kunt u controleren **Configuratie** in de **Cloud Services** van de map **Eigenschappen**:

![Mapeigenschappen maken - configuratie](/help/journey-headless/author/assets/headless-journey-author-folder-03.png)

>[!NOTE]
>
>U kunt meer lezen onder De configuratie toepassen op uw middelenmap.

### Een inhoudsfragment maken {#creating-fragment}

Het maken van een inhoudsfragment lijkt sterk op het instellen van een **Inhoudsfragment** in plaats daarvan:

![Inhoudsfragment maken, optie](/help/journey-headless/author/assets/headless-journey-author-content-fragment-01.png)

Dit keer wordt een wizard geopend. De eerste stap bestaat uit het selecteren van het inhoudsfragmentmodel waarop het fragment wordt gebaseerd:

![Inhoudsfragment maken - Model selecteren](/help/journey-headless/author/assets/headless-journey-author-content-fragment-02.png)

Na voortzetting met **Volgende** u kunt de details opgeven (**Basis** en **Geavanceerd**) voor het fragment:

![Inhoudsfragment maken - naam opgeven](/help/journey-headless/author/assets/headless-journey-author-content-fragment-03.png)

Bevestigen met **Maken** en u kunt **Openen** het fragment in de editor.

### Een fragment bewerken {#editing-fragment}

U kunt een fragment direct openen nadat u het hebt gemaakt of door het te selecteren in de middelenconsole.

Wanneer de redacteur eerst opent zult u zien:

* Een lijst met pictogrammen aan de linkerkant - hiermee hebt u toegang tot verschillende functies. De editor wordt geopend in het dialoogvenster **Variaties** -tabblad, vindt u hier de meeste bewerkingen plaats. U bent wellicht ook ge??nteresseerd in de **Annotaties** en **Metagegevens** tabs.

* Een koptekst met informatie over het fragment en toegang tot verschillende handelingen.

* Het hoofdbewerkingsgebied. Dit is afhankelijk van het model waarmee het fragment is gemaakt.

Als voorbeelden:

* Een fragment dat alleen meerdere gegevens vereist, waarvan sommige een specifiek type hebben. Voor inhoud zonder kop zijn verwijzingen van essentieel belang. U leert hierover later tijdens uw reis.

   ![Inhoudsfragmenteditor - Mijn fragment](/help/journey-headless/author/assets/headless-journey-author-content-fragment-04.png)

* Een fragment waarmee u een lange sectie tekst kunt schrijven. Hier zijn aanvullende opties voor het beheren en opmaken van de tekst. U kunt zelfs de afzonderlijke tekstvelden openen in een volledige-schermeditor (met het kleine schermachtige pictogram rechts)

   ![Content Fragment Editor - Alaska Spirits](/help/journey-headless/author/assets/headless-journey-author-content-fragment-05.png)

>[!NOTE]
>
>Projectspecifieke documentatie kan nodig zijn om auteurs te helpen bij het voltooien van bepaalde velden.
>
>Zie Modellen van de Fragmenten van de Inhoud - de Types van Gegevens en Eigenschappen voor generische details.

Bevestig uw updates met of **Opslaan** of **Opslaan en sluiten**.

>[!NOTE]
>
>Voor meer details kunt u Variaties lezen - Inhoudsfragmenten ontwerpen.

#### Wat u (waarschijnlijk) niet hoeft te maken {#what-you-probably-do-not-need-to-worry-about}

Dit lijkt misschien een iets vreemde sectie, maar als u de Content Fragment Editor opent en gaat onderzoeken, ziet u verschillende opties die (waarschijnlijk) niet van toepassing zijn op de tocht zonder kop als Content Author. Dit is dus slechts een kort overzicht van wat je zou moeten kunnen negeren in de context zonder kop:

* **Modellen van contentfragmenten**

   De naam van het inhoudsfragmentmodel wordt boven in de editor weergegeven, direct onder de fragmentnaam. Dit is ook een verbinding die u aan de modelredacteur neemt.
Modellen van inhoudsfragmenten zijn in feite van vitaal belang voor inhoudsfragmenten als ze de structuur defini??ren die u gebruikt. Het maken en bewerken van deze bestanden valt (gewoonlijk) echter onder de verantwoordelijkheid van een andere persoon, de Content Architect.

   >[!NOTE]
   >
   >Als u meer wilt weten, kunt u de AEM Headless Content Architect Journey lezen.

* **Gekoppelde inhoud**

   Dit is duidelijk aangezien het een lusje in de redacteur is.

   Inhoudsfragmenten zijn in AEM al een aantal versies beschikbaar. Oorspronkelijk zijn ze beschikbaar gesteld voor &quot;traditioneel&quot; gebruik bij het ontwerpen van pagina&#39;s....en zij worden in dit verband nog steeds gebruikt . Hierbij kan het gaan om het koppelen van elementen (bijvoorbeeld afbeeldingen) die weliswaar niet in het fragment zijn ingesloten, maar die wel beschikbaar moeten zijn voor de auteur wanneer deze een pagina ontwerpt.

* **Voorvertoning**

   Dit is een ander tabblad in de editor en biedt een technische weergave, voornamelijk bedoeld voor ontwikkelaars.

* **Paginaverwijzingen bijwerken**

   Deze handeling is beschikbaar via de **...** (ellipsen). Het is niet interessant voor headless auteurs aangezien het op paginascreatie betrekking heeft.

### Publiceren {#publishing}

<!-- needs more details -->

Nadat u het fragment hebt voltooid, kunt u **Publiceren** zodat deze beschikbaar is voor toepassingen zonder koppen.

De publicatiehandelingen zijn beschikbaar in de editor (of op de werkbalk van het **Activa** console):

![Inhoudsfragmenteditor - Mijn fragment](/help/journey-headless/author/assets/headless-journey-author-content-fragment-06.png)

## Volgende functies {#whats-next}

Nu u de grondbeginselen hebt geleerd, is de volgende stap: [Meer informatie over verwijzingen](references.md). Dit zal de diverse beschikbare verwijzingen introduceren en bespreken, en hoe te om niveaus van structuur met de Verwijzingen van het Fragment tot stand te brengen - een zeer belangrijk deel van creatie voor headless.

## Aanvullende bronnen {#additional-resources}

* [Authoring van concepten](/help/sites-authoring/author.md)

* [Basisverwerking](/help/sites-authoring/basic-handling.md) - deze pagina is voornamelijk gebaseerd op de **Sites** console, maar veel/de meeste eigenschappen zijn ook relevant voor het ontwerpen **Inhoudsfragmenten** onder de **Activa** console.

   * [Deelvenster Navigatie](/help/sites-authoring/basic-handling.md#navigation-panel)

   * [De koptekst](/help/sites-authoring/basic-handling.md#the-header)

   * [Werkbalk Handelingen](/help/sites-authoring/basic-handling.md#actions-toolbar)

   * [Snelle handelingen](/help/sites-authoring/basic-handling.md#quick-actions)

   * [Bronnen weergeven en selecteren](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources)

   * [Spoorwegkiezer](/help/sites-authoring/basic-handling.md#rail-selector)

* [Werken met contentfragmenten](/help/assets/content-fragments/content-fragments.md)

   * [Contentfragmenten beheren](/help/assets/content-fragments/content-fragments-managing.md)

      * [De configuratie toepassen op de middelenmap](/help/assets/content-fragments/content-fragments-configuration-browser.md#apply-the-configuration-to-your-assets-folder)

      * [Een inhoudsfragment maken](/help/assets/content-fragments/content-fragments-managing.md#creating-a-content-fragment)
   * [Variaties - Inhoudsfragmenten ontwerpen](/help/assets/content-fragments/content-fragments-variations.md)

   * [Modellen van contentfragmenten](/help/assets/content-fragments/content-fragments-models.md)

      * [Content Fragment Models - Data Types](/help/assets/content-fragments/content-fragments-models.md#data-types)

      * [Modellen van inhoudsfragmenten - eigenschappen](/help/assets/content-fragments/content-fragments-models.md#properties)

      * [Modellen van inhoudsfragmenten - Modellen van inhoudsfragmenten toestaan in uw middelenmap](/help/assets/content-fragments/content-fragments-models.md#allowing-content-fragment-models-assets-folder)


* Aan de slag - hulplijnen
   * [Snelstartgids voor mappen zonder middelenkoppen maken](/help/sites-developing/headless/getting-started/create-assets-folder.md)

* [Reis van architect zonder hoofdinhoud AEM](/help/journey-headless/architect/overview.md)

* [AEM doorlopende vertaalreis](/help/journey-headless/translation/overview.md)
