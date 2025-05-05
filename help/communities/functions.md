---
title: Communautaire functies
description: Leer hoe u toegang krijgt tot de Community Function Console
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
docset: aem65
role: Admin
exl-id: 2395c895-c611-43ac-abb6-c2bc4b4a41f4
solution: Experience Manager
feature: Communities
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '2211'
ht-degree: 0%

---

# Communautaire functies{#community-functions}

Het type functies dat wordt verwacht van een community-ervaring is bekend. De communautaire eigenschappen zijn beschikbaar als communautaire functies. In wezen zijn ze een of meer pagina&#39;s die vooraf zijn bekabeld om een community-functie te implementeren. Hiervoor is meer nodig dan alleen het toevoegen van een component aan een pagina in de modus Schrijven. Zij zijn de bouwstenen die worden gebruikt om de structuur van het malplaatje van de a [ communautaire plaats ](/help/communities/sites.md) te bepalen waarvan de communautaire plaatsen [&#128279;](/help/communities/sites-console.md) worden gecreeerd.

Zodra een communautaire plaats wordt gecreeerd, kan de inhoud aan de resulterende pagina&#39;s worden toegevoegd gebruikend de standaard [ AEM auteurswijze ](/help/sites-authoring/editing-content.md). Verschillende communityfuncties zijn beschikbaar zoals in de console voor communityfuncties.

>[!NOTE]
>
>De consoles voor de verwezenlijking van [ communautaire plaatsen ](/help/communities/sites-console.md), [ communautaire plaatssjablonen ](/help/communities/sites.md), [ communautaire groepsmalplaatjes ](/help/communities/tools-groups.md), en [ communautaire functies ](/help/communities/functions.md) zijn voor gebruik slechts in het auteursmilieu.

## Community-functieconsole {#community-functions-console}

Om de console van communautaire functies in het auteursmilieu te bereiken:

* Navigeer naar **[!UICONTROL Tools]** > **[!UICONTROL Communities]** > **[!UICONTROL Community Functions]** .

![ gemeenschap-functies ](assets/community-functions.png)

## Vooraf gebouwde functies {#pre-built-functions}

Hieronder volgt een korte beschrijving van de functies die bij AEM Communities worden geleverd. Elke functie omvat één of meerdere AEM pagina&#39;s die de componenten bevatten van Gemeenschappen samen in een eigenschap worden getelegrafeerd die gemakkelijk in het malplaatje van de a [ communautaire plaats ](/help/communities/sites.md) wordt opgenomen.

Een communitysitesjabloon biedt de structuur voor een communitysite, zoals aanmeldingsgegevens, gebruikersprofielen, meldingen, berichten, berichten, het menu van de site, zoeken, thema&#39;s en brandingfuncties.

### Instellingen voor Titel en URL {#title-and-url-settings}

**Titel** en **URL** zijn eigenschappen gemeenschappelijk voor alle communautaire functies.

Wanneer een communautaire functie aan een malplaatje van de communautaire plaats wordt toegevoegd of toegevoegd wanneer [ het wijzigen ](/help/communities/sites-console.md#modifying-site-properties) de structuur van een communautaire plaats, opent de dialoog van de functie zodat de Titel en URL kunnen worden gevormd.

#### Configuratiefunctie {#configuration-function-details}

![ titel-url-details ](assets/title-url-details.png)

* **Titel**

  (*Vereiste*) de tekst die in het menu van eigenschappen voor de plaats verschijnt

* **URL**

  (*Vereiste*) de naam die wordt gebruikt om URI te produceren. De naam moet met de [ noemende overeenkomsten ](/help/sites-developing/naming-conventions.md) in overeenstemming zijn die door AEM en JCR worden opgelegd.

Bijvoorbeeld, gebruikend de plaats die van het volgen van [ wordt gecreeerd Begonnen ](/help/communities/getting-started.md) leerprogramma, als

* Titel = webpagina
* URL = pagina

De URL naar de pagina is vervolgens https://localhost:4503/content/sites/engage/en/page.html

en de menukoppeling voor de pagina wordt weergegeven als:

![ in dienst nemen-pagina ](assets/engage-page.png)

### Functie activiteitsstroom {#activity-stream-function}

De functie van de activiteitenstroom is een pagina met een [ component van de Streams van de Activiteit ](/help/communities/activities.md) met alle geselecteerde meningen (alle activiteiten, gebruikersactiviteiten, en het volgende). Zie ook {de Hoofdzaak van de Stroom van de Activiteit 0} [&#128279;](/help/communities/essentials-activities.md) voor ontwikkelaars.

Wanneer u een sjabloon toevoegt, wordt het volgende dialoogvenster geopend:

#### Configuratiefunctie {#configuration-function-details-1}

![ functie-details ](assets/function-details.png)

* [Instellingen voor Titel en URL](#title-and-url-settings)

* **toon &quot;Mijn Activiteiten&quot;mening**

  Als deze optie is geselecteerd, bevat de pagina Activiteiten een tabblad waarop activiteiten worden gefilterd op basis van activiteiten die door het huidige lid binnen de gemeenschap worden gegenereerd. Standaard is geselecteerd.

* **toon &quot;Alle Activiteiten&quot;mening**

  Als deze optie is geselecteerd, bevat de pagina Activiteiten een tabblad dat alle binnen de gemeenschap gegenereerde activiteiten bevat waartoe het huidige lid toegang heeft. Standaard is geselecteerd.

* **toon &quot;News Feed&quot;mening**

  Als deze optie is geselecteerd, bevatten de pagina Activiteiten een tabblad waarop activiteiten worden gefilterd op basis van activiteiten die het huidige lid volgt. Standaard is geselecteerd.

### Blogfunctie {#blog-function}

De blogfunctie is een pagina met de component van a [ Blog ](/help/communities/blog-feature.md) die voor het etiketteren wordt gevormd, uploadt het dossier, na, leden aan zelf-geeft uit te geven, te stemmen, en matiging. Zie ook [ Grondbeginselen van Blog ](/help/communities/blog-developer-basics.md) voor ontwikkelaars.

Wanneer u een sjabloon toevoegt, wordt het volgende dialoogvenster geopend:

![ blog-component ](assets/blog-component.png)

* [Instellingen voor Titel en URL](#title-and-url-settings)

* **staat Geprivilegieerde Leden** toe

  Als geselecteerd, staat blog slechts bevoorrechte leden toe om artikelen tot stand te brengen door selectie van a [ bevoorrechte ledengroep ](/help/communities/users.md#privileged-members-group) toe te staan. Als deze optie niet is geselecteerd, mogen alle leden van de community het bestand maken. De optie Standaard is uitgeschakeld.

* **staat Dossier toe uploadt**

  Als deze optie is geselecteerd, biedt de blog leden de mogelijkheid bestanden te uploaden. Standaard is geselecteerd.

* **staat Verbonden Antwoorden** toe

  Als deze optie niet is geselecteerd, staat de blog reacties (opmerkingen) op een artikel toe, maar zijn reacties op opmerkingen niet toegestaan. Standaard is geselecteerd.

* **sta Aanbevolen Inhoud** toe

  Als geselecteerd, wordt blog geïdentificeerd als [ gekenmerkte inhoud ](/help/communities/featured.md). Standaard is geselecteerd.

### Kalenderfunctie {#calendar-function}

De kalenderfunctie is een pagina met de component van de a [ Kalender ](/help/communities/calendar.md) wordt gevormd om het etiketteren toe te staan. Zie ook {de Hoofdzaak van de Kalender 0} [&#128279;](/help/communities/calendar-basics-for-developers.md) voor ontwikkelaars.

Wanneer u een sjabloon toevoegt, wordt het volgende dialoogvenster geopend:

![ kalender-details ](assets/calendar-details.png)

* [Instellingen voor Titel en URL](#title-and-url-settings)

* **het Draaien** toestaan

  Indien geselecteerd, laat het forum onderwerpantwoorden toe om aan het begin van de lijst van commentaren worden vastgezet. Standaard is geselecteerd.

* **staat Geprivilegieerde Leden** toe

  Als geselecteerd, staat blog slechts bevoorrechte leden toe om artikelen tot stand te brengen door selectie van a [ bevoorrechte ledengroep ](/help/communities/users.md#privileged-members-group) toe te staan. Als deze optie niet is geselecteerd, mogen alle leden van de community het bestand maken. De optie Standaard is uitgeschakeld.

* **staat Dossier toe uploadt**

  Als deze optie is geselecteerd, biedt de blog leden de mogelijkheid bestanden te uploaden. Standaard is geselecteerd.

* **staat Verbonden Antwoorden** toe

  Als deze optie niet is geselecteerd, staat de blog reacties (opmerkingen) op een artikel toe, maar zijn reacties op opmerkingen niet toegestaan. Standaard is geselecteerd.

* **sta Aanbevolen Inhoud** toe

  Als geselecteerd, wordt zijn inhoud geïdentificeerd als [ gekenmerkte inhoud ](/help/communities/featured.md). Standaard is geselecteerd.

### Functie aanbevolen inhoud {#featured-content-function}

De gekenmerkte inhoudsfunctie is een pagina met de component van de Inhoud van de a [ Aanbevolen ](/help/communities/featured.md) wordt gevormd om commentaren toe te staan om worden toegevoegd en worden geschrapt.

De capaciteit om inhoud te voorzien kan worden toegestaan of worden verworpen per component (zie {de Functie van 0} Blog [&#128279;](#blog-function), [ de Functie van de Kalender ](#calendar-function), [ Functie van het Forum ](#forum-function), [ Functie van de Ideatie ](#ideation-function), en [ Functie QnA ](#qna-function)).

Wanneer toegevoegd aan een malplaatje, is de enige configuratie voor de [ Montages van de Titel en URL ](#title-and-url-settings).

### Functie bestandsbibliotheek {#file-library-function}

De functie van de dossierbibliotheek is een pagina met de component van de Bibliotheek van het a [ Dossier ](/help/communities/file-library.md) wordt gevormd om commentaren toe te staan om worden toegevoegd en worden geschrapt.

Wanneer toegevoegd aan een malplaatje, is de enige configuratie voor de [ Montages van de Titel en URL ](#title-and-url-settings).

### Functie van forum {#forum-function}

De forumfunctie is een pagina met de component van het a [ Forum ](/help/communities/forum.md) die voor het etiketteren wordt gevormd, uploadt het dossier, na, leden om zelf-uit te geven, te stemmen, en matiging.

Wanneer u een sjabloon toevoegt, wordt het volgende dialoogvenster geopend:

#### Configuratiefunctie {#configuration-function-details-2}

![ forum-component1 ](assets/forum-component1.png)

* [Instellingen voor Titel en URL](#title-and-url-settings)

* **het Draaien** toestaan

  Indien geselecteerd, laat het forum onderwerpantwoorden toe om aan het begin van de lijst van commentaren worden vastgezet. Standaard is geselecteerd.

* **staat Geprivilegieerde Leden** toe

  Als geselecteerd, staat het forum slechts bevoorrechte leden toe om onderwerpen te posten door selectie van a [ bevoorrechte ledengroep ](/help/communities/users.md#privileged-members-group) toe te staan. Als deze optie niet is geselecteerd, mogen alle leden van de gemeenschap posten. De optie Standaard is uitgeschakeld.

* **staat Dossier toe uploadt**

  Als deze optie is geselecteerd, kunnen leden bestanden uploaden. Standaard is geselecteerd.

* **staat Verbonden Antwoorden** toe

  Als deze optie niet is geselecteerd, staat het forum commentaar op een onderwerp toe, maar zijn antwoorden op deze opmerkingen niet toegestaan. Standaard is geselecteerd.

* **sta Aanbevolen Inhoud** toe

  Als geselecteerd, wordt de inhoud van de component geïdentificeerd als [ gekenmerkte inhoud ](/help/communities/featured.md). Standaard is geselecteerd.

### Functie Groepen {#groups-function}

>[!CAUTION]
>
>De groepsfunctie moet ** niet eerst *zijn noch de enige* functie in de structuur van een plaats of in een malplaatje van de communautaire plaats.
>
>Om het even welke andere functie, zoals de [ paginafunctie ](#page-function), moet worden omvat en eerst vermeld.

De groepsfunctie biedt leden van de gemeenschap de mogelijkheid om subgemeenschappen binnen de gemeenschapssite in de publicatieomgeving te maken.

Afhankelijk van [ montages ](/help/communities/sites-console.md#groupmanagement) wanneer de functie van Groepen in a [ communautair plaatssjabloon ](/help/communities/sites.md) inbegrepen is, kunnen de groepen openbaar of privé zijn en één of meerdere malplaatjes van de communautaire groep kunnen worden gevormd om een keus van malplaatjes te verstrekken wanneer de communautaire groep eigenlijk wordt gecreeerd (zoals van het publicatiemilieu). A [ malplaatje van de communautaire groep ](/help/communities/tools-groups.md) specificeert welke eigenschappen van Gemeenschappen voor de groepspagina&#39;s, zoals forums en kalenders worden gecreeerd.

Wanneer een communautaire groep wordt gecreeerd, wordt een lidgroep dynamisch gecreeerd voor de nieuwe groep, waaraan de leden kunnen worden toegewezen of zich aansluiten. Voor meer informatie, zie [ het Leiden Gebruikers en de Groepen van de Gebruiker ](/help/communities/users.md).

Vanaf de Gemeenschappen [ eigenschappak 1 ](/help/communities/deploy-communities.md#latestfeaturepack), worden de communautaire groepen gecreeerd in het auteursmilieu gebruikend de [ console van de Groepen van Plaatsen van Gemeenschappen ](/help/communities/groups.md), en kunnen in het publicatiemilieu wanneer toegelaten worden gecreeerd.

Wanneer u een sjabloon toevoegt, wordt het volgende dialoogvenster geopend:

![ groep-malplaatje-config ](assets/group-template-config.png)

* [Instellingen voor Titel en URL](#title-and-url-settings)

* **Uitgezochte de Malplaatjes van de Groep**

  Een drop-down die selectie van één of meerdere toegelaten groepsmalplaatjes toestaat waarvan de toekomstige schepper van een nieuwe communautaire groep (in het publicatiemilieu) kan kiezen.

* **staat Geprivilegieerde Leden** toe

  Als geselecteerd, staat het forum slechts bevoorrechte leden toe om onderwerpen te posten door selectie van de groep van de a [ bevoorrechte ledenveiligheid ](/help/communities/users.md#privileged-members-group) toe te staan. Als deze optie niet is geselecteerd, mogen alle leden van de gemeenschap posten. De optie Standaard is uitgeschakeld.

* **staat Publish Creation** toe

  Als deze optie is geselecteerd, kunnen geautoriseerde leden van de gemeenschap een groep maken in de publicatieomgeving. Als deze optie niet is geselecteerd, kunnen alleen nieuwe groepen (subgemeenschappen) worden gemaakt in de auteursomgeving van de console Groepen van sites van de Gemeenschappen.
Standaard is geselecteerd.

### Idealisatiefunctie {#ideation-function}

De videofunctie is een pagina met één [ component van de Ideatie ](/help/communities/ideation-feature.md).

Wanneer u een sjabloon toevoegt, wordt het volgende dialoogvenster geopend met de standaardnamen voor Titel en URL en de standaardweergave-instellingen voor de sjabloon:

![ plaats-functie ](assets/ideation-function.png)

* [Instellingen voor Titel en URL](#title-and-url-settings)

* **staat Geprivilegieerde Leden** toe

  Als geselecteerd, staat het forum slechts bevoorrechte leden toe om onderwerpen te posten door selectie van de groep van de a [ bevoorrechte ledenveiligheid ](/help/communities/users.md#privileged-members-group) toe te staan. Als deze optie niet is geselecteerd, mogen alle leden van de gemeenschap posten. De optie Standaard is uitgeschakeld.

* **staat Dossier toe uploadt**

  Als deze optie is geselecteerd, kunnen leden bestanden uploaden. Standaard is geselecteerd.

* **staat Verbonden Antwoorden** toe

  Als deze optie niet is geselecteerd, kunnen reacties (opmerkingen) op een onderwerp worden geplaatst, maar kunnen opmerkingen niet worden beantwoord. Standaard is geselecteerd.

* **sta Aanbevolen Inhoud** toe

  Als geselecteerd, wordt zijn inhoud geïdentificeerd als [ gekenmerkte inhoud ](/help/communities/featured.md). Standaard is geselecteerd.

### Leaderboard-functie {#leaderboard-function}

De leaderboardfunctie is een pagina met één [ component Leaderboard ](/help/communities/enabling-leaderboard.md).

**NOTA**: De component Leaderboard vereist verdere configuratie *nadat* een communautaire plaats van een communautair malplaatje wordt gecreeerd dat de functie omvat Leaderboard. Specificeer de 3&rbrace; regels [&#128279;](/help/communities/enabling-leaderboard.md#rules-tab) van de component Leaderboard , die van configuratie van [ het scoren en badges ](/help/communities/implementing-scoring.md) voor de communautaire plaats afhangen.

Wanneer u een sjabloon toevoegt, wordt het volgende dialoogvenster geopend met de standaardnamen voor Titel en URL en de standaardweergave-instellingen voor de sjabloon:

![ leaderboard-dialog ](assets/leaderboard-dialog.png)

* [Instellingen voor Titel en URL](#title-and-url-settings)

* **Badge van de Vertoning**

  Als deze optie is geselecteerd, wordt een kolom voor badge-pictogrammen opgenomen in het leaderboard.
De optie Standaard is uitgeschakeld.

* **Naam van de Band van de Vertoning**

  Als deze optie is geselecteerd, wordt een kolom met de naam van de badge in het leaderboard opgenomen.
De optie Standaard is uitgeschakeld.

* **Vertoning Avatar**

  Als deze optie is geselecteerd, wordt de avatarafbeelding van het lid opgenomen in het leaderboard, naast de naamkoppeling naar het profiel van het lid.
De optie Standaard is uitgeschakeld.

### Paginacode {#page-function}

De paginafunctie voegt een lege pagina aan de communautaire plaats toe dat het in de eigenschappen van de communautaire plaats wordt getelegrafeerd: login, menu, berichten, overseinen, thema en branding. De inhoud wordt toegevoegd aan de pagina gebruikend de [ standaard AEM auteurswijze ](/help/sites-authoring/editing-content.md).

Wanneer toegevoegd aan een malplaatje, is de enige configuratie voor de [ Montages van de Titel en URL ](#title-and-url-settings).

### QnA-functie {#qna-function}

De functie QnA is een pagina met de component van a [ QnA ](/help/communities/working-with-qna.md) die voor het etiketteren wordt gevormd, uploadt het dossier, na, leden om zelf-uit te geven, te stemmen, en matiging.

Wanneer toegevoegd aan een malplaatje, staat de configuratie beperking aan bevoorrechte leden toe:

![ qna-dialog ](assets/qna-dialog.png)

* [Instellingen voor Titel en URL](#title-and-url-settings)

* **het Draaien** toestaan

  Indien geselecteerd, laat het forum onderwerpantwoorden toe om aan het begin van de lijst van commentaren worden vastgezet. Standaard is geselecteerd.

* **staat Geprivilegieerde Leden** toe

  Als geselecteerd, staat het forum QnA slechts bevoorrechte leden toe om vragen te posten door selectie van a [ bevoorrechte ledengroep ](/help/communities/users.md#privileged-members-group) toe te staan. Als deze optie niet is geselecteerd, mogen alle leden van de gemeenschap posten. De optie Standaard is uitgeschakeld.

* **staat Dossier toe uploadt**

  Indien geselecteerd, omvat het forum QnA de capaciteit voor leden om dossiers te uploaden. Standaard is geselecteerd.

* **staat Verbonden Antwoorden** toe

  Als deze optie niet is geselecteerd, kan op het QnA-forum commentaar (antwoorden) worden gegeven op een geposte vraag, maar antwoorden op antwoorden zijn niet toegestaan. Standaard is geselecteerd.

* **sta Aanbevolen Inhoud** toe

  Als geselecteerd, wordt zijn inhoud geïdentificeerd als [ gekenmerkte inhoud ](/help/communities/featured.md). Standaard is geselecteerd.

## Community-functie maken {#create-community-function}

De mogelijkheid om een community-functie te maken, wordt bereikt door het pictogram `Create Community Function` boven aan de Community Function-console te selecteren. Er kunnen meerdere functies worden gemaakt die op dezelfde AEM blauwdruk zijn gebaseerd en vervolgens op unieke wijze worden aangepast door het openen in de bewerkingsmodus van de auteur.

![ creeer-gemeenschap-functie ](assets/create-community-function.png)

### Community-functienaam {#community-function-name}

![ functie-naam ](assets/function-name.png)

In het deelvenster Community Function Name worden een naam, beschrijving en of de functie is ingeschakeld of uitgeschakeld geconfigureerd:

* **Communautaire Naam van de Functie**

  De functienaam die wordt gebruikt voor weergave en opslag.

* **Beschrijving van de Functie van de Gemeenschap**

  De functiebeschrijving voor de weergave.

* **Gehandicapten/Toegelaten**

  Een schakeloptie die bepaalt of naar de functie kan worden verwezen.

### AEM {#aem-blueprint}

![ aem-blauwdruk ](assets/aem-blueprint.png)

In het deelvenster `AEM Blueprint` kunt u de blauwdruk selecteren die de onderliggende implementatie van de communautaire functie is.

De functie van de gemeenschap is een mini plaats die één of meerdere pagina&#39;s omvat, die voor opneming in een communautaire plaats met inbegrip van login, gebruikersprofielen, berichten, overseinen, plaatsmenu, onderzoek, thema, en branding eigenschappen vooraf worden getelegrafeerd. Zodra de functie wordt gecreeerd, is het mogelijk om [ de functie ](#open-community-function) op auteur te openen uitgeeft wijze en de pagina of componentenmontages aan te passen.

Aangezien de communautaire functie als a [ levend exemplaar ](/help/sites-administering/msm.md#live-copies) van a [ blauwdruk ](/help/sites-administering/msm-livecopy.md#creatingablueprint) wordt uitgevoerd, is het mogelijk om veranderingen uit te voeren die aan een functie worden aangebracht die alle communautaire plaatspagina&#39;s beïnvloedt die van het [ malplaatje van de communautaire plaats ](/help/communities/sites.md) worden gecreeerd of [ communautair groepsmalplaatje ](/help/communities/tools-groups.md) dat de functie omvatte. Het is ook mogelijk om een pagina los te koppelen van de bovenliggende blauwdruk om wijzigingen op paginaniveau aan te brengen.

Zie ook [ Meerdere Manager van de Plaats ](/help/sites-administering/msm.md).

### Miniatuur {#thumbnail}

![ functie-duimnagel ](assets/funtion-thumbnail.png)

Op het paneel van Duimnagel, kan een beeld worden geupload om in de [ console van de Functies van de Gemeenschap ](#community-functions-console) te tonen.

## Community-functie openen {#open-community-function}

![ open-function ](assets/open-function.png)

Selecteer het pictogram `Open Community Function` om de bewerkingsmodus voor auteurs te activeren voor het ontwerpen van de pagina-inhoud en het wijzigen van de configuratie van de functiecomponent(en).

### Componenten configureren {#configuring-components}

Een communautaire functie wordt uitgevoerd als Levend Exemplaar van een AEM Vervaging, details waarvan onder [ de Manager van de Multisite ](/help/sites-administering/msm.md) worden gedocumenteerd.

Het is mogelijk om niet alleen pagina-inhoud te schrijven, maar componenten te configureren.

Als het vormen van een component op een pagina van een gecreeerde communautaire plaats, kan het noodzakelijk zijn om [ overerving ](/help/sites-administering/msm-livecopy.md#changing-live-copy-content) te annuleren om de component te vormen. De overerving moet worden hersteld wanneer de configuratie is voltooid.

Voor configuratiedetails, bezoek {de Componenten van 0} Gemeenschappen [&#128279;](/help/communities/author-communities.md) voor auteurs.

## Community-functie bewerken {#edit-community-function}

![ geef-functie uit ](assets/edit-function.png)

Selecteer het `Edit Community Function` pictogram om de eigenschappen van de functie uit te geven gebruikend de zelfde panelen zoals [ creërend een communautaire functie ](#create-community-function), met inbegrip van het toelaten van of het onbruikbaar maken van de functie.
