---
title: Grondbeginselen van ontwerpen leren
description: Leer over de concepten en de mechanica van creatie inhoud voor uw Zwaarloze CMS gebruikend Inhoudsfragmenten.
exl-id: 125c4d0b-1572-4dba-823d-cdef2778f275
solution: Experience Manager, Experience Manager Sites
feature: Headless,Content Fragments
role: Admin, Architect,Data Architect,Developer,User,Leader
source-git-commit: 9a3008553b8091b66c72e0b6c317573b235eee24
workflow-type: tm+mt
source-wordcount: '1694'
ht-degree: 0%

---

# Grondbeginselen van ontwerpen voor headless met AEM {#author-headless-basics}

## Het artikel tot nu toe {#story-so-far}

Aan het begin van de [ Reis van de Auteur van de Inhoud zonder hoofd ](overview.md) de [ Inleiding ](introduction.md) behandelde de basisconcepten en de terminologie relevant voor creatie voor hoofd.

Dit artikel bouwt hierop voort, zodat u begrijpt hoe u uw eigen inhoud voor uw AEM project zonder titel kunt ontwerpen.

## Doelstelling {#objective}

* **Publiek**: Begin
* **Doelstelling**: Introduceer de grondbeginselen van Schrijven CMS zonder Zwaartepunt:
   * Inleiding tot ontwerpen met AEMaaCS
   * Inleiding tot inhoudsfragmenten

## Basisverwerking {#basic-handling}

Voordat u de stappen met inhoudsfragmenten gaat beheren, volgt een (zeer) korte inleiding op het gebruik van AEM...maar niets vervangt echt de ervaring van het aanmelden en het proberen om het systeem te gebruiken.

### Auteur en Publish {#author-preview-publish}

Een AEM installatie bestaat meestal uit minstens twee omgevingen:

* Auteur
* Publish

U meldt zich aan, en gebruikt het auteursmilieu om uw inhoud te produceren. Wanneer u klaar bent, publiceert u de inhoud zodat deze algemeen beschikbaar wordt. Voor koploze gebruikers is dit voor andere toepassingen, voor webpagina&#39;s is dit voor lezers op het web.

Zie Concepten ontwerpen voor meer informatie.

### Aanmelden {#signing-in}

Net als bij de meeste systemen moet u zich aanmelden. Als auteur krijgt u de volgende informatie:

* Gebruikersnaam (account)
* Wachtwoord
* Koppeling voor toegang tot het aanmeldingsscherm

Uw account is geconfigureerd met alle rechten die u nodig hebt. Als u problemen hebt, raadt de Adobe u aan contact op te nemen met uw interne team voor projectondersteuning.

### Navigatie {#navigation}

De eerste keer dat u zich aanmeldt bij een kleine online zelfstudie, worden enkele van de belangrijkste functies van de gebruikersinterface gemarkeerd.

Vervolgens kunt u het navigatievenster gebruiken om toegang te krijgen tot belangrijke gebieden van AEM. Voor Inhoudsfragmenten zult u de **Console van Assets** gebruiken.

U kunt het navigatievenster openen door het pictogram Adobe linksboven te selecteren, gevolgd door het kleine kompaspictogram:

![ het paneel van de Navigatie ](/help/journey-headless/author/assets/headless-journey-author-navigation-01.png)

>[!NOTE]
>Hoewel de Fragmenten van de Inhoud een eigenschap van AEM **Plaatsen** zijn, worden zij gevonden in de **Assets** console. Dit is een technisch detail dat u niet zou moeten beïnvloeden, maar zou nuttig kunnen zijn om te weten.

Binnen de console kunt u mappen selecteren om naar het inhoudsfragment te navigeren, of de broodkruimels (in de koptekst) om een back-up van de structuur te maken.

![ Broodkruimels ](/help/journey-headless/author/assets/headless-journey-author-navigation-02.png)

### Handelingen, selecteren, weergeven {#actions-selecting-viewing}

De **console van 0&rbrace; Assets &lbrace;heeft** Toolbars van de Actie **gewijd, en** Snelle Acties **die u na het selecteren van een middel (bijvoorbeeld, een omslag of inhoudsfragment) kunt gebruiken.**

De Snelle Acties zijn beschikbaar voor één enkel middel, zie **Bazel** in het voorbeeld hieronder:

![ Snelle Acties ](/help/journey-headless/author/assets/headless-journey-author-navigation-05.png)

De werkbalk Handelingen biedt toegang tot het volledige scala aan handelingen die voor het huidige scenario gelden. De beschikbare acties kunnen veranderen, bijvoorbeeld afhankelijk van uw locatie of van het feit of u meerdere bronnen hebt geselecteerd:

![ Toolbar van de Actie ](/help/journey-headless/author/assets/headless-journey-author-navigation-06.png)

U kunt de indeling voor het weergeven van uw bronnen selecteren met de Weergaveselector:

![ de Selecteur van de Mening ](/help/journey-headless/author/assets/headless-journey-author-navigation-03.png)

U kunt aanvullende informatie over items weergeven met de spoorkiezer. Dit geeft ook toegang tot extra acties.

![ Linkerspoor ](/help/journey-headless/author/assets/headless-journey-author-navigation-04.png)

## Inhoudsfragmenten ontwerpen {#authoring-content-fragments}

Dat was dus een zeer snelle inleiding op de AEM Gebruikersinterface (UI), maar hopelijk hebt u de kans gehad om het uit te proberen. Nu komen we neer op je echte interesse - Content Fragments voor Headless.

We moeten de zaken van begin tot eind doorlopen, maar in uw instantie zijn mogelijk al mappen en/of fragmenten gemaakt. Deze bevinden zich mogelijk op verschillende locaties. De beginselen zijn dezelfde.

### Organiseren en navigeren {#organizing-and-navigating}

Tenzij u zeer weinig Inhoudsfragmenten hebt, wilt u deze ordenen - zodat u (en anderen) ze opnieuw kunt vinden.

#### Een map maken {#creating-folder}

U kunt dit doen door een reeks omslagen binnen **te creëren Dossiers** sectie van de console van Assets. Selecteer **creeer** optie (hoogste recht), die door **Omslag** wordt gevolgd:

![ creeer de optie van de Omslag ](/help/journey-headless/author/assets/headless-journey-author-folder-01.png)

Een dialoog opent waar u de details kunt ingaan, dan bevestig met **&#x200B;**&#x200B;creëren:

![ creeer de dialoog van de Omslag ](/help/journey-headless/author/assets/headless-journey-author-folder-02.png)

#### Paden en tags gebruiken om de in de map beschikbare modellen van inhoudsfragmenten te beperken {#tags-paths-for-models-in-folder}

Deze sectie is iets geavanceerder. U hebt het niet echt nodig als u gewoon begint en dingen probeert, maar het is vooral handig als u veel fragmenten hebt. Het is dus goed om dat te weten, ook al gebruikt u het nog niet helemaal.

Uw Content Architect zal alle Content Fragment Models hebben gecreeerd die voor uw huidige project worden vereist, en misschien ook sommige andere projecten. Om de zaken voor zich, en andere auteurs eenvoudig te houden, kunt u de lijst van modellen beperken beschikbaar voor een specifieke omslag.

Na het creëren van uw omslag kunt u de omslag **Eigenschappen** openen. Hier zijn diverse lusjes met informatie, en configuratiedetails, over de omslag. Met name voor de Fragmenten van de Inhoud, kunt u het **lusje van Beleid** gebruiken om specifieke wegen en/of markeringen voor deze omslag te bepalen. Dit beperkt de modellen van het Fragment van de Inhoud beschikbaar voor gebruik in de omslag aangezien het betekent dat de Modellen van het Fragment van de Inhoud aan deze vereisten moeten voldoen alvorens zij kunnen worden gebruikt om fragmenten in deze omslag te produceren.

![ creeer de Eigenschappen van de Omslag - Beleid ](/help/journey-headless/author/assets/headless-journey-author-folder-04.png)

>[!NOTE]
>
>U kunt meer informatie lezen onder Modellen van inhoudsfragmenten - Modellen van inhoudsfragmenten toestaan in uw Assets-map.

Vervolgens navigeert u door deze mappen om inhoudsfragmenten te maken en te bewerken.

#### Net voor het geval - Configuratie van Cloud Servicen van mappen {#cloud-services-folder}

Alleen voor het geval...

U krijgt waarschijnlijk een eerste map waarin u uw mappen kunt maken. Dit is aangezien sommige configuratiedetails (gewoonlijk door een Ontwikkelaar of Beheerder van het Systeem) op de wortelomslag moeten worden toegepast. Dit is waarschijnlijk van geen belang u, maar indien nodig kunt u de **Configuratie** in de **Cloud Servicen** van de omslag **Eigenschappen** controleren:

![ creeer de Eigenschappen van de Omslag - Configuratie ](/help/journey-headless/author/assets/headless-journey-author-folder-03.png)

>[!NOTE]
>
>U kunt meer lezen onder De configuratie toepassen op uw Assets-map.

### Een inhoudsfragment maken {#creating-fragment}

Het creëren van een Fragment van de Inhoud is zeer gelijkaardig - u gebruikt enkel de **optie van het Fragment van de Inhoud** in plaats daarvan:

![ creeer de optie van het Fragment van de Inhoud ](/help/journey-headless/author/assets/headless-journey-author-content-fragment-01.png)

Dit keer wordt een wizard geopend. De eerste stap bestaat uit het selecteren van het inhoudsfragmentmodel waarop het fragment wordt gebaseerd:

![ creeer het Fragment van de Inhoud - uitgezocht Model ](/help/journey-headless/author/assets/headless-journey-author-content-fragment-02.png)

Na het verdergaan met **daarna** kunt u de details (**Basis** en **Geavanceerd**) voor uw fragment verstrekken:

![ creeer het Fragment van de Inhoud - verstrek Naam ](/help/journey-headless/author/assets/headless-journey-author-content-fragment-03.png)

Bevestig met **creeer** en u kunt **dan** uw fragment in de redacteur openen.

### Een fragment bewerken {#editing-fragment}

U kunt een fragment direct openen nadat u het hebt gemaakt of door het te selecteren in de Assets-console.

Wanneer de redacteur eerst opent zult u zien:

* Een lijst met pictogrammen aan de linkerkant - hiermee hebt u toegang tot verschillende functies. De redacteur opent in het **lusje van Variaties**, is dit waar het grootste deel van het uitgeven gebeurt. U zou in de **Annotaties** en **Meta-gegevens** lusjes ook geinteresseerd kunnen zijn.

* Een koptekst met informatie over het fragment en toegang tot verschillende handelingen.

* Het hoofdbewerkingsgebied. Dit is afhankelijk van het model waarmee het fragment is gemaakt.

Als voorbeelden:

* Een fragment dat alleen meerdere gegevens vereist, waarvan sommige een specifiek type hebben. Voor inhoud zonder kop zijn verwijzingen van essentieel belang. U leert hierover later tijdens uw reis.

  ![ de Redacteur van het Fragment van de Inhoud - Mijn Fragment ](/help/journey-headless/author/assets/headless-journey-author-content-fragment-04.png)

* Een fragment waarmee u een lang tekstgedeelte kunt schrijven. Hier zijn aanvullende opties voor het beheren en opmaken van de tekst. U kunt zelfs de afzonderlijke tekstvelden openen in een volledige-schermeditor (met het kleine schermachtige pictogram rechts)

  ![ de Redacteur van het Fragment van de Inhoud - de Rondjes van Alaska ](/help/journey-headless/author/assets/headless-journey-author-content-fragment-05.png)

>[!NOTE]
>
>Projectspecifieke documentatie kan nodig zijn om auteurs te helpen bij het voltooien van bepaalde velden.
>
>Zie Modellen van de Fragmenten van de Inhoud - de Types van Gegevens en Eigenschappen voor generische details.

Bevestig uw updates met of **sparen** of **sparen &amp; sluit**.

>[!NOTE]
>
>Voor meer details kunt u Variaties lezen - Inhoudsfragmenten ontwerpen.

#### Wat u (waarschijnlijk) niet hoeft te maken {#what-you-probably-do-not-need-to-worry-about}

Dit lijkt misschien een iets vreemde sectie, maar als u de Content Fragment Editor opent en gaat onderzoeken, ziet u verschillende opties die (waarschijnlijk) niet van toepassing zijn op de tocht zonder kop als Content Author. Dit is dus slechts een kort overzicht van wat je zou moeten kunnen negeren in de context zonder kop:

* **Modellen van contentfragmenten**

  De naam van het inhoudsfragmentmodel wordt boven in de editor weergegeven, direct onder de fragmentnaam. Dit is ook een verbinding die u aan de modelredacteur neemt.
Modellen van inhoudsfragmenten zijn in feite van vitaal belang voor inhoudsfragmenten als ze de structuur definiëren die u gebruikt. Het maken en bewerken van deze bestanden valt (gewoonlijk) echter onder de verantwoordelijkheid van een andere persoon, de Content Architect.

  >[!NOTE]
  >
  >Als u meer wilt weten, kunt u de AEM Headless Content Architect Journey lezen.

* **Verwante Inhoud**

  Dit is heel duidelijk, omdat het een tabblad in de editor is.

  Inhoudsfragmenten zijn in AEM al een aantal versies beschikbaar. Oorspronkelijk zijn ze beschikbaar gesteld voor &quot;traditioneel&quot; gebruik bij het ontwerpen van pagina&#39;s...en zij worden in dit verband nog steeds gebruikt . Hierbij kan het gaan om het koppelen van elementen (bijvoorbeeld afbeeldingen) die weliswaar niet in het fragment zijn ingesloten, maar die wel beschikbaar moeten zijn voor de auteur wanneer deze een pagina ontwerpt.

* **Voorproef**

  Dit is een ander tabblad in de editor en biedt een technische weergave, voornamelijk bedoeld voor ontwikkelaars.

* **de paginaverwijzingen van de Update**

  Deze handeling is beschikbaar in de vervolgkeuzelijst **...** (ovalen). Het is niet interessant voor headless auteurs aangezien het op paginascreatie betrekking heeft.

### Publiceren {#publishing}

<!-- needs more details -->

Zodra u uw fragment hebt voltooid kunt u **Publish** het zodat het aan de toepassingen zonder kop beschikbaar is.

De publiceer acties zijn beschikbaar in de redacteur (of van de toolbar van de **Assets** console):

![ de Redacteur van het Fragment van de Inhoud - Mijn Fragment ](/help/journey-headless/author/assets/headless-journey-author-content-fragment-06.png)

## Volgende functies {#whats-next}

Nu u de grondbeginselen hebt geleerd, moet de volgende stap [ leren hoe over Verwijzingen ](references.md). Dit zal de diverse beschikbare verwijzingen introduceren en bespreken, en hoe te om niveaus van structuur met de Verwijzingen van het Fragment tot stand te brengen - een zeer belangrijk deel van creatie voor headless.

## Aanvullende bronnen {#additional-resources}

* [Concepten ontwerpen](/help/sites-authoring/author.md)

* [ Basis Behandelend ](/help/sites-authoring/basic-handling.md) - deze pagina is hoofdzakelijk gebaseerd op de **console van Plaatsen**, maar vele/de meeste eigenschappen zijn ook relevant voor het ontwerpen van **Fragmenten van de Inhoud** onder de **Assets** console.

   * [Deelvenster Navigatie](/help/sites-authoring/basic-handling.md#navigation-panel)

   * [De koptekst](/help/sites-authoring/basic-handling.md#the-header)

   * [Werkbalk Handelingen](/help/sites-authoring/basic-handling.md#actions-toolbar)

   * [Snelle handelingen](/help/sites-authoring/basic-handling.md#quick-actions)

   * [Bronnen weergeven en selecteren](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources)

   * [Spoorwegkiezer](/help/sites-authoring/basic-handling.md#rail-selector)

* [Werken met inhoudsfragmenten](/help/assets/content-fragments/content-fragments.md)

   * [Inhoudsfragmenten beheren](/help/assets/content-fragments/content-fragments-managing.md)

      * [De configuratie toepassen op uw Assets-map](/help/assets/content-fragments/content-fragments-configuration-browser.md#apply-the-configuration-to-your-assets-folder)

      * [Een inhoudsfragment maken](/help/assets/content-fragments/content-fragments-managing.md#creating-a-content-fragment)

   * [Variaties - Inhoudsfragmenten ontwerpen](/help/assets/content-fragments/content-fragments-variations.md)

   * [Modellen van inhoudsfragmenten](/help/assets/content-fragments/content-fragments-models.md)

      * [Modellen van inhoudsfragmenten - gegevenstypen](/help/assets/content-fragments/content-fragments-models.md#data-types)

      * [Modellen van inhoudsfragmenten - eigenschappen](/help/assets/content-fragments/content-fragments-models.md#properties)

      * [Modellen van inhoudsfragmenten - Modellen van inhoudsfragmenten toestaan in uw Assets-map](/help/assets/content-fragments/content-fragments-models.md#allowing-content-fragment-models-assets-folder)

* Aan de slag - hulplijnen
   * [Een Assets-map zonder koppen en een snelstartgids maken](/help/sites-developing/headless/getting-started/create-assets-folder.md)

* [Reis van architect zonder hoofdinhoud AEM](/help/journey-headless/architect/overview.md)

* [AEM doorsnedenloze vertaalreis](/help/journey-headless/translation/overview.md)
