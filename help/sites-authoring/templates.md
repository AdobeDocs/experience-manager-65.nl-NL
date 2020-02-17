---
title: Paginasjablonen maken
seo-title: Paginasjablonen maken
description: De sjabloon definieert de structuur van de resulterende pagina en met de sjablooneditor. Het maken en onderhouden van sjablonen is niet langer een taak die alleen voor ontwikkelaars geldt
seo-description: De sjabloon definieert de structuur van de resulterende pagina en met de sjablooneditor. Het maken en onderhouden van sjablonen is niet langer een taak die alleen voor ontwikkelaars geldt
uuid: e14cd298-289f-43f0-aacb-314ed5d56c12
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: site-features
discoiquuid: b53348ca-fc50-4e7d-953d-b4c03a5025bb
docset: aem65
translation-type: tm+mt
source-git-commit: e3f1c932a5937e8a115e2849935b8f5ea5c2613d

---


# Paginasjablonen maken{#creating-page-templates}

Wanneer u een pagina maakt, moet u een sjabloon selecteren die wordt gebruikt als basis voor het maken van de nieuwe pagina. De sjabloon definieert de structuur van de resulterende pagina, eventuele eerste inhoud en de componenten die kunnen worden gebruikt.

Met de Redacteur **van het** Malplaatje, is het creëren van en het handhaven van malplaatjes niet meer een ontwikkelaar-enige taak. Een type van macht-gebruiker, die een **malplaatjeauteur** wordt genoemd, kan ook worden betrokken. De ontwikkelaars worden nog vereist om het milieu te installeren, cliëntbibliotheken te creëren, en de te gebruiken componenten tot stand te brengen, maar zodra deze grondbeginselen op zijn plaats zijn heeft de **malplaatjeauteur** de flexibiliteit om malplaatjes zonder een ontwikkelingsproject tot stand te brengen en te vormen.

Met de **Sjabloonconsole** kunnen sjabloonauteurs:

* Maak een nieuwe sjabloon of kopieer een bestaande sjabloon.
* De levenscyclus van de sjabloon beheren.

Met de **Sjablooneditor** kunnen sjabloonauteurs:

* Voeg componenten aan het malplaatje toe en plaats hen op een ontvankelijk net.
* Configureer de componenten vooraf.
* Bepaal welke componenten op pagina&#39;s kunnen worden uitgegeven die met het malplaatje worden gecreeerd.

In dit document wordt uitgelegd hoe een **sjabloonauteur** de sjabloonconsole en -editor kan gebruiken om bewerkbare sjablonen te maken en te beheren.

Voor gedetailleerde informatie over hoe de editable malplaatjes op een technisch niveau werken, te zien gelieve het document van de ontwikkelaar [PaginaMalplaatjes - editable](/help/sites-developing/page-templates-editable.md) voor meer informatie.

>[!NOTE]
>
>De **Redacteur** van het Malplaatje steunt niet direct het richten op het malplaatjeniveau. Pagina&#39;s die zijn gemaakt op basis van een bewerkbare sjabloon kunnen worden geactiveerd, maar de sjablonen zelf kunnen dat niet.

>[!CAUTION]
>
>Pagina&#39;s en sjablonen die zijn gemaakt met de **Sjabloonconsole** , zijn niet bedoeld voor gebruik met de klassieke interface en worden niet ondersteund.

## Before You Start {#before-you-start}

>[!NOTE]
>
>Een beheerder moet een malplaatjeomslag in Browser **van** Configuraties vormen en juiste toestemmingen toepassen alvorens een malplaatjeauteur een malplaatje in die omslag kan tot stand brengen.

De volgende punten zijn belangrijk om te overwegen alvorens u begint:

* Voor het maken van een nieuwe sjabloon is samenwerking vereist. Daarom wordt voor elke taak de [rol](#roles) vermeld.

* Afhankelijk van hoe uw instantie wordt gevormd, zou het nuttig kunnen zijn om zich ervan bewust te zijn dat AEM nu [twee basistypes van malplaatje](/help/sites-authoring/templates.md#editable-and-static-templates)verstrekt. Dit is niet van invloed op de manier waarop u een sjabloon [gebruikt om een pagina](#using-a-template-to-create-a-page)te maken, maar het heeft wel invloed op het type sjabloon dat u kunt maken en op de manier waarop een pagina betrekking heeft op de sjabloon.

### Rollen {#roles}

Het creëren van een nieuw malplaatje gebruikend de Console **van** Malplaatjes en de Redacteur **van het** Malplaatje vereist samenwerking tussen de volgende rollen:

* **Beheerder**:

   * Hiermee maakt u een nieuwe map voor sjablonen waarvoor `admin` rechten vereist zijn.

   * Dergelijke taken kunnen vaak ook door een ontwikkelaar worden uitgevoerd

* **Ontwikkelaar**:

   * Concentraties op de technische/interne details
   * Heeft ervaring nodig met de ontwikkelomgeving.
   * Verstrekt de malplaatjeauteur van noodzakelijke informatie.

* **Sjabloonauteur**:

   * Dit is een specifieke auteur die lid is van de groep `template-authors`

      * Hiermee worden de vereiste rechten en machtigingen toegewezen.
   * Kan het gebruik van componenten en andere details op hoog niveau configureren die het volgende vereisen:

      * Enkele technische kennis

         * Gebruik bijvoorbeeld patronen bij het definiëren van paden.
      * Technische informatie van de ontwikkelaar.



Vanwege de aard van sommige taken, zoals het maken van een map, is een ontwikkelomgeving nodig. Hiervoor is kennis en ervaring vereist.

De in dit document beschreven taken worden weergegeven met de rol die verantwoordelijk is voor de uitvoering ervan.

### Bewerkbare en statische sjablonen {#editable-and-static-templates}

AEM biedt nu twee basistypen sjablonen:

* [Bewerkbare sjablonen](/help/sites-authoring/templates.md#creatingandmanagingnewtemplates)

   * Kan door malplaatjeauteurs worden [gecreeerd](#creatinganewtemplate) en worden [uitgegeven](#editingatemplate) gebruikend de console en de redacteur van het **Malplaatje** . De **console van het Malplaatje** is toegankelijk in de **Algemene** sectie van de console van **Hulpmiddelen** .

   * Nadat de nieuwe pagina is gemaakt, wordt een dynamische verbinding onderhouden tussen de pagina en de sjabloon. Dit betekent dat wijzigingen in de sjabloonstructuur en/of vergrendelde inhoud worden doorgevoerd op alle pagina&#39;s die met die sjabloon zijn gemaakt. Wijzigingen in de ontgrendelde (dat wil zeggen initiële) inhoud worden niet doorgevoerd.
   * Het inhoudsbeleid van het gebruik, dat u deze van de malplaatjeredacteur kunt bepalen, om de ontwerpeigenschappen voort te zetten. De ontwerpmodus in de pagina-editor wordt niet meer gebruikt voor bewerkbare sjablonen.

* Statische sjablonen

   * Statische sjablonen zijn beschikbaar voor verschillende versies van AEM.
   * Ze worden [geleverd door uw ontwikkelaars](/help/sites-developing/page-templates-static.md)en kunnen dus niet worden gemaakt of bewerkt door auteurs.
   * Er wordt gekopieerd om de nieuwe pagina te maken, maar er bestaat daarna geen dynamische verbinding (hoewel de sjabloonnaam ter informatie is geregistreerd).
   * Gebruik de [ontwerpmodus](/help/sites-authoring/default-components-designmode.md) om de ontwerpeigenschappen te behouden.
   * Omdat het bewerken van statische sjablonen de exclusieve taak van een ontwikkelaar is, raadpleegt u het ontwikkelaarsdocument [Paginasjablonen - statisch](/help/sites-developing/page-templates-static.md) voor meer informatie.

De sjabloonconsole en sjablooneditor staan per definitie alleen het maken en bewerken van bewerkbare sjablonen toe. Daarom richt dit document zich uitsluitend op bewerkbare sjablonen.

### Een sjabloon gebruiken om een pagina te maken {#using-a-template-to-create-a-page}

Wanneer u een sjabloon gebruikt om een nieuwe pagina [te](/help/sites-authoring/managing-pages.md#creating-a-new-page) maken, is er geen zichtbaar verschil en is er geen indicatie tussen statische en bewerkbare sjablonen. Voor de auteur van de pagina is het proces transparant.

## Creating and Managing Templates {#creating-and-managing-templates}

Bij het maken van een nieuwe bewerkbare sjabloon:

* Gebruik de **Sjabloonconsole** . Dit is beschikbaar in de **Algemene** sectie van de console van **Hulpmiddelen** .

   * Of rechtstreeks bij: [https://localhost:4502/libs/wcm/core/content/sites/templates.html/conf](https://localhost:4502/libs/wcm/core/content/sites/templates.html/conf)

* Kan zo nodig een map voor de sjablonen [](#creating-a-template-folder-admin) maken
* [Een nieuwe sjabloon](#creatinganewtemplateauthor)maken die aanvankelijk leeg is [](#templatedefinitions)

* [Definieer indien nodig aanvullende eigenschappen](#definingtemplatepropertiesauthor) voor de sjabloon
* [Bewerk de sjabloon](#editingtemplates) om het volgende te definiëren:

   * [Structuur](#editingatemplatestructureauthor) - vooraf gedefinieerde inhoud die niet kan worden gewijzigd op pagina&#39;s die met de sjabloon zijn gemaakt.
   * [Eerste inhoud](#editing-a-template-initial-content-author) - vooraf gedefinieerde inhoud die kan worden gewijzigd op pagina&#39;s die met de sjabloon zijn gemaakt.
   * [Layout](#editingatemplatelayoutauthor) - Voor een reeks apparaten.
   * [Stijlen](/help/sites-authoring/style-system.md) - Definieer de stijlen die met de sjabloon en de componenten ervan moeten worden gebruikt.

* [De sjabloon](#enablingatemplateauthor) inschakelen voor gebruik bij het maken van een pagina
* [De sjabloon](#allowing-a-template-author) voor de vereiste pagina of vertakking van uw website toestaan
* [De sjabloon](#publishingatemplateauthor) publiceren om deze beschikbaar te maken in de publicatieomgeving

>[!NOTE]
>
>De **toegestane sjablonen** zijn vaak vooraf gedefinieerd wanneer uw website voor het eerst wordt ingesteld.

>[!CAUTION]
>
>Voer nooit informatie in die u wilt [internationaliseren](/help/sites-developing/i18n.md) in een sjabloon.

### Sjabloonmap maken - Beheer {#creating-a-template-folder-admin}

Een malplaatjeomslag zou voor uw project moeten worden gecreeerd om uw project-specifieke malplaatjes te houden. Dit is een beheertaak die wordt beschreven in het document [Paginasjablonen - Bewerkbaar](/help/sites-developing/page-templates-editable.md#template-folders).

### Een nieuwe sjabloon maken - Sjabloonauteur {#creating-a-new-template-template-author}

1. Open de **Sjabloonconsole** (via **Gereedschappen ->** **Algemeen**) en navigeer naar de vereiste map.

   >[!NOTE]
   >
   >In een standaard AEM-instantie bestaat de **algemene** map al in de sjabloonconsole. Dit houdt standaardmalplaatjes vast en doet dienst als reserve als geen beleid en/of malplaatje-types in de huidige omslag worden gevonden.
   >
   >
   >Het wordt aanbevolen een [sjabloonmap te gebruiken die voor uw project](/help/sites-developing/page-templates-editable.md#template-folders)is gemaakt.

1. Selecteer **Maken**, gevolgd door **Sjabloon** maken om de wizard te openen.

1. Kies een **Sjabloontype** en selecteer **Volgende**.

   >[!NOTE]
   >
   >Sjabloontypen zijn vooraf gedefinieerde sjabloonlay-outs en kunnen worden beschouwd als sjablonen voor een sjabloon. Deze worden vooraf bepaald door ontwikkelaars of de systeembeheerder. Meer informatie vindt u in het ontwikkelaarsdocument [Paginasjablonen - Bewerkbaar](/help/sites-developing/page-templates-editable.md#template-type).

1. Voer de **sjabloondetails** in:

   * **Sjabloonnaam**
   * **Beschrijving**

1. Selecteer **Maken**. Er wordt een bevestiging weergegeven. Selecteer **Openen** om de sjabloon [te](#editingatemplate) bewerken of **Gereed** om terug te keren naar de sjabloonconsole.

   >[!NOTE]
   >
   >Wanneer een nieuw malplaatje wordt gecreeerd is het duidelijk als **Ontwerp** in de console, wijst dit erop dat het nog niet beschikbaar aan gebruik door paginaauteurs is.

### Sjablooneigenschappen definiëren - Sjabloonauteur {#defining-template-properties-template-author}

Een sjabloon kan de volgende eigenschappen hebben:

* Afbeelding

   * Afbeelding die moet worden gebruikt als [miniatuur van de sjabloon](/help/sites-authoring/templates.md#template-thumbnail-image) voor selectie, zoals in de wizard Pagina maken.

      * Kan worden geüpload
      * Kan worden gegenereerd op basis van de sjablooninhoud

* Titel

   * Een titel die wordt gebruikt voor het identificeren van de sjabloon, zoals in de wizard **Pagina** maken.

* Beschrijving

   * Een optionele beschrijving voor meer informatie over de sjabloon en het gebruik ervan, die u kunt vinden in bijvoorbeeld de wizard **Pagina** maken.

De eigenschappen weergeven en/of bewerken:

1. Selecteer de sjabloon in de **Sjabloonconsole**.
1. Selecteer Eigenschappen **** weergeven op de werkbalk of kies Snelle opties om het dialoogvenster te openen.
1. U kunt nu de sjablooneigenschappen weergeven of bewerken.

>[!NOTE]
>
>De status van een sjabloon (concept, ingeschakeld of uitgeschakeld) wordt aangegeven in de console.

#### Miniatuurafbeelding sjabloon {#template-thumbnail-image}

De sjabloonminiatuur definiëren:

1. Bewerk de sjablooneigenschappen.
1. Kies of u een miniatuur wilt uploaden of wilt dat deze wordt gegenereerd op basis van de sjablooninhoud.

   * Als u een miniatuur wilt uploaden, klikt u of tikt u op Afbeelding **uploaden**
   * Als u een miniatuur wilt genereren, klikt u of tikt u op Voorvertoning **genereren**

1. Voor beide methoden wordt een voorbeeld van de miniatuur weergegeven.

   Als dit niet het geval is, klikt u of tikt u op **Wissen** om een andere afbeelding te uploaden of de miniatuur opnieuw te genereren.

1. Als u tevreden bent met de miniatuur, klikt u of tikt u op **Opslaan en sluiten**.

### Een sjabloon inschakelen en toestaan - Sjabloonauteur {#enabling-and-allowing-a-template-template-author}

Als u een sjabloon wilt kunnen gebruiken bij het maken van een pagina, moet u:

* [Schakel de sjabloon](#enablingatemplate) in om deze beschikbaar te maken voor gebruik bij het maken van pagina&#39;s.
* [Hiermee kan de sjabloon](#allowingatemplate) de vertakkingen van de inhoud aangeven waarin de sjabloon kan worden gebruikt.

#### Sjabloon inschakelen - Sjabloonauteur {#enabling-a-template-template-author}

U kunt een sjabloon in- of uitschakelen om de sjabloon beschikbaar of niet beschikbaar te maken in de wizard **Pagina** maken.

>[!CAUTION]
>
>Zodra een malplaatje wordt toegelaten zal een waarschuwing worden getoond wanneer een malplaatjeauteur begint om het malplaatje verder bij te werken. Dit moet de gebruiker informeren dat naar de sjabloon kan worden verwezen, zodat wijzigingen van invloed kunnen zijn op de pagina&#39;s die naar de sjabloon verwijzen.

1. Selecteer de sjabloon in de **Sjabloonconsole**.
1. Selecteer **Inschakelen** of **Uitschakelen** op de werkbalk en nogmaals in het bevestigingsvenster.
1. U kunt de sjabloon nu gebruiken wanneer u een nieuwe pagina [](/help/sites-authoring/managing-pages.md#creating-a-new-page)maakt, maar u wilt de sjabloon [waarschijnlijk naar wens](#editingatemplate) bewerken.

>[!NOTE]
>
>De status van een sjabloon (concept, ingeschakeld of uitgeschakeld) wordt aangegeven in de console.

#### Een sjabloon toestaan - Auteur {#allowing-a-template-author}

Een sjabloon kan beschikbaar worden gesteld of niet beschikbaar zijn voor bepaalde paginasvertakkingen.

1. Open de [Pagina-eigenschappen](/help/sites-authoring/editing-page-properties.md) voor de hoofdpagina van de vertakking waar u de sjabloon wilt plaatsen.

1. Open het tabblad **Geavanceerd** .

1. Gebruik onder **Sjablooninstellingen** het veld **** Toevoegen om het pad of de paden naar de sjabloon of sjablonen op te geven.

   Het pad kan expliciet zijn of patronen gebruiken. Bijvoorbeeld:

   `/conf/<your-folder>/settings/wcm/templates/.*`

   De volgorde van de paden is irrelevant, alle paden worden gescand en sjablonen worden opgehaald.

   >[!NOTE]
   >
   >Als de lijst **Toegestane sjablonen** leeg blijft, wordt de structuur opgetrokken totdat een waarde/lijst wordt gevonden.
   >
   >
   >Zie Beschikbaarheid [van](/help/sites-developing/templates.md#template-availability) sjabloon - de principes voor toegestane sjablonen blijven ongewijzigd.

1. Klik op **Opslaan** om de wijzigingen in de pagina-eigenschappen op te slaan.

>[!NOTE]
>
>Vaak zijn de toegestane sjablonen vooraf gedefinieerd voor uw gehele site wanneer deze wordt ingesteld.

### Een sjabloon publiceren - Sjabloonauteur {#publishing-a-template-template-author}

Aangezien het malplaatje van verwijzingen wordt voorzien wanneer een pagina wordt teruggegeven, moet het volledig gevormde malplaatje worden gepubliceerd zodat het op het publicatiemilieu beschikbaar is.

1. Selecteer de sjabloon in de **Sjabloonconsole**.
1. Selecteer **Publiceren** op de werkbalk om de wizard te openen.
1. Selecteer het **inhoudsbeleid** dat u samen wilt publiceren.

1. Selecteer **Publiceren** op de werkbalk om de handeling te voltooien.

## Sjablonen bewerken - Sjabloonauteurs {#editing-templates-template-authors}

Bij het maken of bewerken van een sjabloon zijn er verschillende aspecten die u kunt definiëren. Sjablonen bewerken is vergelijkbaar met het ontwerpen van pagina&#39;s.

De volgende aspecten van een sjabloon kunnen worden bewerkt:

* [Structuur](#editingatemplatestructure)

   Componenten die hier zijn toegevoegd, kunnen niet door de auteurs van de pagina worden verplaatst of verwijderd van de resulterende pagina&#39;s. Als u wilt dat auteurs van pagina&#39;s componenten aan resulterende pagina&#39;s kunnen toevoegen en verwijderen, dan moet u een paragraafsysteem aan het malplaatje toevoegen.

   Wanneer componenten zijn vergrendeld, kunt u inhoud toevoegen die niet kan worden bewerkt door auteurs van pagina&#39;s. U kunt componenten ontgrendelen, zodat u [initiële inhoud](#editingatemplateinitialcontent)kunt definiëren.

   >[!NOTE]
   >
   >In de structuurmodus kunnen componenten die het bovenliggende element van een niet-vergrendelde component zijn, niet worden verplaatst, geknipt of verwijderd.

* [Oorspronkelijke inhoud](#editingatemplateinitialcontent)

   Wanneer een component ontgrendeld is, kunt u de eerste inhoud definiëren die naar de resulterende pagina(&#39;s), gemaakt op basis van de sjabloon, wordt gekopieerd. Deze niet-vergrendelde componenten kunnen op de resulterende pagina(&#39;s) worden bewerkt.

   >[!NOTE]
   >
   >In de modus **Oorspronkelijke inhoud** en op de resulterende pagina&#39;s kunnen alle ontgrendelde onderdelen met een toegankelijk bovenliggend element (d.w.z. onderdelen in een lay-outcontainer) worden verwijderd.

* [Indeling](#editingatemplatelayout)

   Hier kunt u de sjabloonlay-out voor de vereiste apparaatindelingen vooraf definiëren. **De modus Lay-out** voor het ontwerpen van sjablonen heeft dezelfde functionaliteit als de modus [**Lay-out **voor het ontwerpen](/help/sites-authoring/responsive-layout.md#defining-layouts-layout-mode)van pagina&#39;s.

* [Paginabeleid](#editingatemplatepagepolicies)

   Onder paginabeleid kunt u vooraf gedefinieerd paginabeleid verbinden met de pagina. Met dit paginabeleid worden de verschillende ontwerpconfiguraties gedefinieerd.

* [Stijlen](/help/sites-authoring/style-system.md)

   Met het Stijlsysteem kan een sjabloonauteur stijlklassen definiëren in het inhoudsbeleid van een component, zodat de auteur van de inhoud deze kan selecteren wanneer hij de component op een pagina bewerkt. Deze stijlen kunnen alternatieve visuele variaties van een component zijn, waardoor het flexibeler wordt.

   Zie de documentatie [van het Systeem van de](/help/sites-authoring/style-system.md) Stijl voor meer informatie.

Met de **moduskiezer** op de werkbalk kunt u het juiste aspect van de sjabloon selecteren en bewerken:

* [Structuur](#editingatemplatestructure)
* [Oorspronkelijke inhoud](#editingatemplateinitialcontent)
* [Indeling](#editingatemplatelayout)

![chlimage_1-133](assets/chlimage_1-133.png)

Met de optie **Paginabeleid** in het menu **Pagina-informatie** kunt u wel het vereiste paginabeleid [](#editingatemplatepagepolicies)selecteren:

![screen_shot_2018-03-23at120604](assets/screen_shot_2018-03-23at120604.png)

>[!CAUTION]
>
>Als een auteur een sjabloon gaat bewerken die al is ingeschakeld, wordt een waarschuwing weergegeven. Dit moet de gebruiker informeren dat naar de sjabloon kan worden verwezen, zodat wijzigingen van invloed kunnen zijn op de pagina&#39;s die naar de sjabloon verwijzen.

### Een sjabloon bewerken - Structuur - Sjabloonauteur {#editing-a-template-structure-template-author}

In de modus **Structuur** definieert u componenten en inhoud voor de sjabloon en definieert u het beleid voor de sjabloon en de bijbehorende componenten.

* Componenten die in de sjabloonstructuur zijn gedefinieerd, kunnen niet op een resulterende pagina worden verplaatst of uit resulterende pagina&#39;s worden verwijderd.
* Als u wilt dat auteurs van pagina&#39;s componenten kunnen toevoegen en verwijderen, voegt u een alineasysteem toe aan de sjabloon.
* Componenten kunnen worden ontgrendeld en opnieuw worden vergrendeld, zodat u [initiële inhoud](#editingatemplateinitialcontent)kunt definiëren.

* Het ontwerpbeleid voor de componenten en pagina wordt gedefinieerd.

![screen_shot_2018-03-23at120819](assets/screen_shot_2018-03-23at120819.png)

In de modus **Structuur** van de sjablooneditor:

* **Componenten toevoegen**

   Er zijn verschillende manieren om componenten aan de sjabloon toe te voegen:

   * Vanuit de browser **Componenten** in het zijpaneel.
   * Met de optie Component **** invoegen (**+** pictogram) op de werkbalk kunt u de componenten gebruiken die al in de sjabloon staan of de component **slepen hier** .

   * Sleep een element (vanuit de **middelenbrowser** in het zijpaneel) rechtstreeks naar de sjabloon om de juiste component ter plekke te genereren.
   Na toevoeging wordt elke component gemarkeerd met:

   * Een rand
   * Een markering waarmee het componenttype wordt weergegeven
   * Een markering die moet worden weergegeven wanneer de component is ontgrendeld
   >[!NOTE]
   >
   >Wanneer u een uit-van-de-doos component van de **Titel** aan het malplaatje toevoegt zal het de standaardtekststructuur **** bevatten.
   >
   >
   >Als u dit wijzigt en uw eigen tekst toevoegt, wordt deze bijgewerkte tekst gebruikt wanneer een pagina wordt gemaakt op basis van de sjabloon.
   >
   >
   >Als u de standaardtekst (structuur) verlaat, wordt de titel standaard ingesteld op de naam van de volgende pagina.

   >[!NOTE]
   >
   >Hoewel niet identiek, heeft het toevoegen van componenten en activa aan een malplaatje vele gelijkenissen aan gelijkaardige acties wanneer het [paginaontwerp](/help/sites-authoring/editing-content.md).

* **Componenthandelingen**

   Voer acties uit op de componenten nadat deze aan de sjabloon zijn toegevoegd. Elk afzonderlijk exemplaar heeft een toolbar die u toestaat om tot de beschikbare acties toegang te hebben, is de toolbar afhankelijk van het componenttype.

   ![screen_shot_2018-03-23at120909](assets/screen_shot_2018-03-23at120909.png)

   Het kan ook afhankelijk zijn van acties zoals wanneer een beleid met de component is geassocieerd, dan wordt het pictogram van de ontwerpconfiguratie beschikbaar.

* **Bewerken en configureren**

   Met deze twee acties kunt u inhoud toevoegen aan uw componenten.

* **Rand om structuur aan te geven**

   Als u in de **structuurmodus** werkt, wordt een oranje rand weergegeven die aangeeft welke component momenteel is geselecteerd. Een stippellijn geeft ook de bovenliggende component aan.

   In de schermafbeelding onder de component **Tekst** is bijvoorbeeld geselecteerd in een **Layout Container** (responsivegrid).

   ![chlimage_1-134](assets/chlimage_1-134.png)

* **Beleid en eigenschappen (algemeen)**

   Met het inhoudsbeleid (of het ontwerpbeleid) worden de ontwerpeigenschappen van een component gedefinieerd. Bijvoorbeeld de beschikbare componenten of de minimum-/maximumafmetingen. Deze zijn van toepassing op de sjabloon (en op pagina&#39;s die met de sjabloon zijn gemaakt).

   Maak een inhoudsbeleid of selecteer een bestaand beleid voor een component. Zo kunt u de ontwerpdetails definiëren.

   ![chlimage_1-135](assets/chlimage_1-135.png) ![chlimage_1-136](assets/chlimage_1-136.png)

   Het configuratievenster is verdeeld in twee.

   * In de linkerkant van de dialoog onder **Beleid**, hebt u de capaciteit om een bestaand beleid te selecteren of bestaande te selecteren.
   * In de rechterkant van het dialoogvenster onder **Eigenschappen** kunt u de eigenschappen instellen die specifiek zijn voor het componenttype.
   De beschikbare eigenschappen zijn afhankelijk van de geselecteerde component. Voor een tekstcomponent definiëren de eigenschappen bijvoorbeeld de kopieer- en plakopties, opmaakopties en alineastijl.

   ***Beleid***

   Met het inhoudsbeleid (of het ontwerpbeleid) worden de ontwerpeigenschappen van een component gedefinieerd. Bijvoorbeeld de beschikbare componenten of de minimum-/maximumafmetingen. Deze zijn van toepassing op de sjabloon (en op pagina&#39;s die met de sjabloon zijn gemaakt).

   Onder **Beleid** kunt u een bestaand beleid selecteren om op de component via drop-down van toepassing te zijn.

   ![chlimage_1-137](assets/chlimage_1-137.png)

   U kunt een nieuw beleid toevoegen door de knop Toevoegen naast de vervolgkeuzelijst **Beleid** selecteren te selecteren. Vervolgens moet een nieuwe titel worden gegeven in het veld **Beleidstitel** .

   ![chlimage_1-138](assets/chlimage_1-138.png)

   Het geselecteerde bestaande beleid in het **Uitgezochte beleidsdrop** kan als nieuw beleid worden gekopieerd gebruikend de exemplaarknoop naast dropdown. Vervolgens moet een nieuwe titel worden gegeven in het veld **Beleidstitel** . Standaard krijgt het gekopieerde beleid de naam **Kopie van X**, waarbij X de titel van het gekopieerde beleid is.

   ![chlimage_1-139](assets/chlimage_1-139.png)

   Een beschrijving van het beleid is optioneel in het veld **Beleidsbeschrijving** .

   In de **Andere malplaatjes die ook de geselecteerde beleidssectie** gebruiken, kunt u gemakkelijk zien welke andere malplaatjes het beleid gebruiken dat in **Uitgezochte beleidsdrop** wordt geselecteerd.

   ![chlimage_1-140](assets/chlimage_1-140.png)

   >[!NOTE]
   >
   >Als meerdere componenten van hetzelfde type als initiële inhoud worden toegevoegd, geldt hetzelfde beleid voor alle componenten. Dit weerspiegelt dezelfde beperking in de [**ontwerpmodus **voor statische sjablonen](/help/sites-authoring/default-components-designmode.md).

   ***Eigenschappen***

   In de kop **Eigenschappen** kunt u de instellingen van de component definiëren. De kop heeft twee tabbladen:

   * Hoofd
   * Functies
   *Hoofd*

   Op het tabblad **Main** worden de belangrijkste instellingen van de component gedefinieerd.

   Voor een afbeeldingscomponent kunnen bijvoorbeeld de toegestane breedten worden gedefinieerd en kan het laden worden ingeschakeld.

   Als een instelling meerdere configuraties toestaat, klikt of tikt u op de knop **Toevoegen** om nog een configuratie toe te voegen.

   ![chlimage_1-141](assets/chlimage_1-141.png)

   Als u een configuratie wilt verwijderen, klikt of tikt u op de knop **Verwijderen** rechts van de configuratie.

   Als u een configuratie wilt verwijderen, klikt of tikt u op de knop** Verwijderen**.

   ![chlimage_1-142](assets/chlimage_1-142.png)

   *Functies*

   Op het tabblad **Functies** kunt u extra functies van de component in- of uitschakelen.

   Voor een afbeeldingscomponent kunt u bijvoorbeeld de uitsnijdverhoudingen, de toegestane afbeeldingsoriëntaties en de vraag of uploads zijn toegestaan, definiëren.

   ![chlimage_1-143](assets/chlimage_1-143.png)

   >[!CAUTION]
   >
   >In AEM worden uitsnijdverhoudingen gedefinieerd als **hoogte/breedte**. Dit verschilt van de conventionele definitie van breedte/hoogte en wordt gedaan om oude compatibiliteitsredenen. Gebruikers die pagina&#39;s schrijven, zullen zich niet bewust zijn van enig verschil op voorwaarde dat u de **naam** duidelijk definieert aangezien dit is wat wordt weergegeven in de gebruikersinterface.

   >[!NOTE]
   >
   >[Het beleid van de inhoud voor componenten die de rijke tekstredacteur](/help/sites-administering/rich-text-editor.md#main-pars-header-206036638) uitvoeren kan slechts voor opties worden bepaald die door RTE door zijn montages UI ter beschikking worden gesteld. [](/help/sites-administering/rich-text-editor.md#main-pars_header_206036638) [](/help/sites-administering/rich-text-editor.md#main-pars_header_206036638)

* **Beleid en eigenschappen (container met layout)**

   Het beleid en de eigenschappen van een lay-outcontainer zijn gelijkaardig aan het algemene gebruik, maar met sommige verschillen.

   >[!NOTE]
   >
   >Het vormen van een beleid is verplicht voor containercomponenten aangezien het u toelaat om componenten te bepalen die in de container beschikbaar zullen zijn.

   Het configuratievenster wordt verdeeld in twee delen, enkel zoals in het algemene gebruik van het venster.

   ***Beleid***

   Met het inhoudsbeleid (of het ontwerpbeleid) worden de ontwerpeigenschappen van een component gedefinieerd. Bijvoorbeeld de beschikbare componenten of de minimum-/maximumafmetingen. Deze zijn van toepassing op de sjabloon (en op pagina&#39;s die met de sjabloon zijn gemaakt).

   Onder **Beleid** kunt u een bestaand beleid selecteren om op de component via drop-down van toepassing te zijn. Deze functie werkt net als bij het algemene gebruik van het venster.

   ***Eigenschappen***

   In de kop **Eigenschappen** kunt u kiezen welke componenten beschikbaar zijn voor de lay-outcontainer en de instellingen definiëren. De kop heeft drie tabbladen:

   * Toegestane componenten
   * Standaardcomponenten
   * Instellingen voor responsie
   *Toegestane componenten*

   Op het tabblad **Toegestane componenten** definieert u welke componenten beschikbaar zijn voor de lay-outcontainer.

   * De componenten worden gegroepeerd op hun componentgroepen, die kunnen worden uitgevouwen en samengevouwen.
   * U kunt een hele groep selecteren door de naam van de groep te controleren. U kunt de selectie van alle groepen ongedaan maken door de selectie uit te schakelen.
   * Een min vertegenwoordigt minstens één maar niet alle punten in een groep worden geselecteerd.
   * Er is een zoekopdracht beschikbaar om naar een component op naam te filteren.
   * De tellingen die rechts van de naam van de componentengroep worden vermeld vertegenwoordigen het totale aantal geselecteerde componenten in die groepen ongeacht de filter.
   ![chlimage_1-144](assets/chlimage_1-144.png)

   *Standaardcomponenten*

   Op het tabblad **Standaardcomponenten** definieert u welke componenten automatisch aan bepaalde mediatypen worden gekoppeld, zodat AEM weet met welke component deze worden gekoppeld wanneer een auteur een element van de elementenbrowser sleept. Merk op dat slechts de componenten met dalingsstreken voor dergelijke configuratie beschikbaar zijn.

   Klik of tik **Toewijzing** toevoegen om een geheel nieuwe component en MIME typetoewijzing toe te voegen.

   Selecteer een component in de lijst en klik of tik op Type **** toevoegen om een extra MIME-type toe te voegen aan een reeds toegewezen component. Klik op het pictogram **Verwijderen** om een MIME-type te verwijderen.

   ![chlimage_1-145](assets/chlimage_1-145.png)

   *Instellingen voor responsie*

   Op het tabblad **Responsieve instellingen** kunt u het aantal kolommen in het resulterende raster van de layoutcontainer configureren.

* **Componenten ontgrendelen/vergrendelen**

   U ontgrendelt/vergrendelt componenten om te bepalen of de inhoud beschikbaar is voor wijziging in de modus **Oorspronkelijke inhoud** .

   Wanneer een component is ontgrendeld:

   * Een open hangslotindicator wordt getoond in de grens.
   * De componentwerkbalk wordt dienovereenkomstig aangepast.
   * Alle inhoud die al is ingevoerd, wordt niet meer weergegeven in de **structuurmodus** .

      * Al ingevoerde inhoud wordt beschouwd als eerste inhoud en is alleen zichtbaar in de modus **Oorspronkelijke inhoud** .
   * De bovenliggende elementen van de ontgrendelde component kunnen niet worden verplaatst, geknipt of verwijderd.
   ![chlimage_1-146](assets/chlimage_1-146.png)

   Dit omvat het ontgrendelen van containercomponenten zodat andere componenten kunnen worden toegevoegd, in de modus **Initiële inhoud** of op de resulterende pagina&#39;s. Als u al componenten/inhoud aan de container hebt toegevoegd voordat u de container ontgrendelt, worden deze niet meer weergegeven in de modus **Structuur** , maar in de modus **Oorspronkelijke inhoud** . In de **structuurmodus** wordt alleen de containercomponent zelf weergegeven met de lijst **Toegestane componenten**.

   ![chlimage_1-147](assets/chlimage_1-147.png)

   Om ruimte te besparen, groeit de lay-outcontainer niet om de lijst van toegestane componenten aan te passen. In plaats daarvan wordt de container een schuifbare lijst.

   De componenten die configureerbaar zijn worden getoond met een pictogram van het **Beleid** , dat kan worden getikt of worden geklikt om het beleid en de eigenschappen van die component uit te geven.

   ![chlimage_1-148](assets/chlimage_1-148.png)

* **Verhouding tot bestaande pagina&#39;s**

   Als de structuur na het maken van op de sjabloon gebaseerde pagina&#39;s wordt bijgewerkt, worden de wijzigingen in de sjabloon doorgevoerd in deze pagina&#39;s. Er wordt een waarschuwing weergegeven op de werkbalk om u hieraan te herinneren, samen met bevestigingsdialoogvensters.

   ![chlimage_1-149](assets/chlimage_1-149.png)

### Een sjabloon bewerken - Eerste inhoud - Auteur {#editing-a-template-initial-content-author}

**De modus Eerste inhoud** wordt gebruikt voor gedefinieerde inhoud die wordt weergegeven wanneer een pagina voor het eerst wordt gemaakt op basis van de sjabloon. De eerste inhoud kan vervolgens door auteurs van pagina&#39;s worden bewerkt.

Hoewel alle inhoud die in de modus **Structuur** is gemaakt, zichtbaar is in **Initiële inhoud**, kunnen alleen de ontgrendelde componenten worden geselecteerd en bewerkt.

>[!NOTE]
>
>**De modus Oorspronkelijke inhoud** kan worden gebruikt als bewerkingsmodus voor pagina&#39;s die met die sjabloon zijn gemaakt. Het beleid wordt daarom niet gedefinieerd in de modus **Oorspronkelijke inhoud** , maar in de modus [**Structuur **](/help/sites-authoring/templates.md#editing-a-template-structure-template-author).

* Ontgrendelde componenten die beschikbaar zijn voor bewerking, worden gemarkeerd. Als deze optie is geselecteerd, hebben ze een blauwe rand:

   ![chlimage_1-150](assets/chlimage_1-150.png)

* Ontgrendelde componenten beschikken over een werkbalk waarmee u de inhoud kunt bewerken en configureren:

   ![chlimage_1-151](assets/chlimage_1-151.png)

* Als een containercomponent is ontgrendeld (in de modus **Structuur** ), kunt u nieuwe componenten aan de container toevoegen (in de modus **Oorspronkelijke inhoud** ). Componenten die in de modus **Oorspronkelijke inhoud** zijn toegevoegd, kunnen worden verplaatst naar of verwijderd uit de resulterende pagina&#39;s.

   U kunt een component toevoegen met behulp van de **sleepcomponenten hier** of de optie Nieuwe component **** invoegen op de werkbalk van de betreffende container.

   ![chlimage_1-152](assets/chlimage_1-152.png) ![chlimage_1-153](assets/chlimage_1-153.png)

* Als de initiële inhoud van de sjabloon wordt bijgewerkt nadat pagina&#39;s zijn gemaakt op basis van de sjabloon, worden deze pagina&#39;s niet beïnvloed door wijzigingen in de oorspronkelijke inhoud van de sjabloon.

>[!NOTE]
>
>De eerste inhoud is bedoeld voor het voorbereiden van componenten en de paginalay-out die als uitgangspunt dienen voor het maken van de inhoud. Het is niet de bedoeling om de inhoud te zijn die ongewijzigd blijft. Daarom kan de initiële inhoud niet worden vertaald.
>
>Als u vertaalbare tekst in uw sjabloon wilt opnemen, bijvoorbeeld in kop- of voetteksten, kunt u de [lokalisatiefuncties van de kerncomponenten](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/get-started/localization.html)gebruiken.

### Een sjabloon bewerken - Layout - Sjabloonauteur {#editing-a-template-layout-template-author}

U kunt de sjabloonlay-out voor een reeks apparaten definiëren. [De responsieve indeling](/help/sites-authoring/responsive-layout.md) voor sjablonen werkt op dezelfde manier als voor het ontwerpen van pagina&#39;s.

>[!NOTE]
>
>Wijzigingen in de lay-out worden weerspiegeld in de modus **Oorspronkelijke inhoud** , maar in de modus **Structuur** zijn geen wijzigingen zichtbaar.

![chlimage_1-154](assets/chlimage_1-154.png)

### Een sjabloon bewerken - Paginaontwerp - Sjabloonauteur/ontwikkelaar {#editing-a-template-page-design-template-author-developer}

Het paginaontwerp, inclusief de vereiste clientbibliotheken en het paginabeleid, blijft behouden onder de optie **Paginaontwerp** van het menu **Pagina-informatie** .

Het dialoogvenster **Paginaontwerp** openen:

1. Selecteer in de **Sjablooneditor** de optie **Pagina-informatie** op de werkbalk en vervolgens **Paginaontwerp** om het dialoogvenster te openen.
1. Het dialoogvenster **Paginaontwerp** wordt geopend en bestaat uit twee gedeelten:

   * De linkerhelft definieert het [paginabeleid](/help/sites-authoring/templates.md#page-policies)
   * De rechterhelft definieert de [pagina-eigenschappen](/help/sites-authoring/templates.md#page-properties)
   ![chlimage_1-155](assets/chlimage_1-155.png)

#### Paginabeleid {#page-policies}

U kunt een inhoudsbeleid toepassen op de sjabloon of de resulterende pagina&#39;s. Hiermee wordt het inhoudsbeleid voor het hoofdalineasysteem op de pagina gedefinieerd.

![chlimage_1-156](assets/chlimage_1-156.png)

* U kunt een bestaand beleid voor de pagina selecteren in de vervolgkeuzelijst **Beleid** selecteren.

   ![chlimage_1-157](assets/chlimage_1-157.png)

   U kunt een nieuw beleid toevoegen door de knop Toevoegen naast de vervolgkeuzelijst **Beleid** selecteren te selecteren. Vervolgens moet een nieuwe titel worden gegeven in het veld **Beleidstitel** .

   ![chlimage_1-158](assets/chlimage_1-158.png)

   Het geselecteerde bestaande beleid in het **Uitgezochte beleidsdrop** kan als nieuw beleid worden gekopieerd gebruikend de exemplaarknoop naast dropdown. Vervolgens moet een nieuwe titel worden gegeven in het veld **Beleidstitel** . Standaard krijgt het gekopieerde beleid de naam **Kopie van X**, waarbij X de titel van het gekopieerde beleid is.

   ![chlimage_1-159](assets/chlimage_1-159.png)

* Definieer een titel voor het beleid in het veld **Beleidstitel** . Een beleid is vereist om een titel te hebben zodat het gemakkelijk in het **Uitgezochte beleidsdrop** kan worden geselecteerd.

   ![chlimage_1-160](assets/chlimage_1-160.png)

* Een beschrijving van het beleid is optioneel in het veld **Beleidsbeschrijving** .
* In de **Andere malplaatjes die ook de geselecteerde beleidssectie** gebruiken, kunt u gemakkelijk zien welke andere malplaatjes het beleid gebruiken dat in **Uitgezochte beleidsdrop** wordt geselecteerd.

   ![chlimage_1-161](assets/chlimage_1-161.png)

#### Pagina-eigenschappen {#page-properties}

Met pagina-eigenschappen kunt u de vereiste clientbibliotheken definiëren in het dialoogvenster **Paginaontwerp** . Deze client-side bibliotheken bevatten stijlpagina&#39;s en javascript die met de sjabloon moeten worden geladen en pagina&#39;s die met die sjabloon zijn gemaakt.

![chlimage_1-162](assets/chlimage_1-162.png)

* Geef de clientbibliotheken op die u wilt toepassen op pagina&#39;s die met deze sjabloon zijn gemaakt. De naam van een bibliotheek invoeren in het tekstveld in de sectie **Clientzijbibliotheken** .

   ![chlimage_1-163](assets/chlimage_1-163.png)

* Als er meerdere bibliotheken nodig zijn, klikt u op de knop Toevoegen om een extra tekstveld voor de naam van de bibliotheek toe te voegen.

   ![chlimage_1-164](assets/chlimage_1-164.png)

   Voeg zoveel tekstvelden toe als nodig zijn voor uw clientbibliotheken.

   ![chlimage_1-165](assets/chlimage_1-165.png)

* Definieer zo nodig de relatieve positie van de bibliotheken door de velden te slepen met de sleepgreep.

   ![chlimage_1-166](assets/chlimage_1-166.png)

>[!NOTE]
>
>Terwijl de sjabloonauteur het paginabeleid voor de sjabloon kan opgeven, moet hij of zij details van de desbetreffende client-side bibliotheken ophalen van de ontwikkelaar.

### Een sjabloon bewerken - Initiële pagina-eigenschappen - Auteur {#editing-a-template-initial-page-properties-author}

Met de optie Eigenschappen **van** eerste pagina kunt u de eerste [pagina-eigenschappen](/help/sites-authoring/editing-page-properties.md) definiëren die moeten worden gebruikt bij het maken van resulterende pagina&#39;s.

1. Selecteer in de sjablooneditor de optie **Pagina-informatie** op de werkbalk en kies vervolgens **Pagina-eigenschappen** bij openen om het dialoogvenster te openen.

1. In het dialoogvenster kunt u de eigenschappen definiëren die u wilt toepassen op pagina&#39;s die met deze sjabloon zijn gemaakt.

   ![chlimage_1-167](assets/chlimage_1-167.png)

1. Bevestig uw definities met **Gedaan**.

## Aanbevolen werkwijzen {#best-practices}

Houd bij het maken van sjablonen rekening met:

1. Het effect van wijzigingen in de sjabloon wanneer pagina&#39;s zijn gemaakt op basis van die sjabloon.

   Hier volgt een lijst met de verschillende bewerkingen die mogelijk zijn op sjablonen, samen met de manier waarop deze van invloed zijn op de pagina&#39;s die er vanaf worden gemaakt:

   * Wijzigingen in de structuur:

      * Deze worden direct toegepast op de resulterende pagina&#39;s.
      * Bezoekers moeten de wijzigingen nog steeds kunnen zien door de gewijzigde sjabloon te publiceren.
   * Wijzigingen in inhoudsbeleid en ontwerpconfiguraties:

      * Deze zijn direct van toepassing op de resulterende pagina&#39;s.
      * De wijzigingen moeten worden gepubliceerd zodat bezoekers de wijzigingen kunnen zien.
   * Wijzigingen in de oorspronkelijke inhoud:

      * Deze zijn alleen van toepassing op pagina&#39;s die na de wijzigingen in de sjabloon worden gemaakt.
   * Wijzigingen in de layout zijn afhankelijk van of de gewijzigde component deel uitmaakt van:

      * Alleen structuur - onmiddellijk toegepast
      * Bevat initiële inhoud - alleen op pagina&#39;s die na de wijziging zijn gemaakt
   Wees extra voorzichtig als:

   * Componenten op ingeschakelde sjablonen vergrendelen of ontgrendelen.
   * Dit kan bijwerkingen hebben, aangezien bestaande pagina&#39;s het reeds kunnen gebruiken. Doorgaans:

      * Ontgrendelingscomponenten (die vergrendeld waren) ontbreken op bestaande pagina&#39;s.
      * Door componenten te vergrendelen (die bewerkbaar waren) wordt die inhoud niet op de pagina&#39;s weergegeven.
   >[!NOTE]
   >
   >AEM geeft expliciete waarschuwingen wanneer het veranderen van de slotstatus van componenten op malplaatjes die niet meer concepten zijn.

1. [Uw eigen mappen](#creatingatemplatefolderdeveloper) maken voor uw sitespecifieke sjablonen.
1. [Publiceer uw malplaatjes](#publishingatemplateauthor) van de console van **Malplaatjes** .
