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

Het type functies dat wordt verwacht van een community-ervaring is bekend. De communautaire eigenschappen zijn beschikbaar als communautaire functies. In wezen zijn ze een of meer pagina&#39;s die vooraf zijn bekabeld om een community-functie te implementeren. Hiervoor is meer nodig dan alleen het toevoegen van een component aan een pagina in de modus Schrijven. Zij zijn de bouwstenen die worden gebruikt om de structuur van een [sjabloon voor community-site](/help/communities/sites.md) waarvan sites uit de gemeenschap [gemaakt](/help/communities/sites-console.md).

Nadat een communitysite is gemaakt, kan inhoud aan de resulterende pagina&#39;s worden toegevoegd met de standaard [AEM ontwerpmodus](/help/sites-authoring/editing-content.md). Verschillende communityfuncties zijn beschikbaar zoals in de console voor communityfuncties.

>[!NOTE]
>
>De consoles voor het creëren van [communitysites](/help/communities/sites-console.md), [communitysjablonen](/help/communities/sites.md), [communitygroepsjablonen](/help/communities/tools-groups.md), en [communautaire functies](/help/communities/functions.md) zijn alleen bestemd voor gebruik in de ontwerpomgeving.

## Community-functieconsole {#community-functions-console}

Om de console van communautaire functies in het auteursmilieu te bereiken:

* Navigeren naar **[!UICONTROL Tools]** > **[!UICONTROL Communities]** > **[!UICONTROL Community Functions]**.

![communautaire functies](assets/community-functions.png)

## Vooraf gebouwde functies {#pre-built-functions}

Hieronder volgt een korte beschrijving van de functies die bij AEM Communities worden geleverd. Elke functie bevat een of meer AEM pagina&#39;s die onderdelen van een Gemeenschappen bevatten die zijn samengevoegd tot een functie die eenvoudig in een [sjabloon voor community-site](/help/communities/sites.md).

Een communitysitesjabloon biedt de structuur voor een communitysite, zoals aanmeldingsgegevens, gebruikersprofielen, meldingen, berichten, berichten, het menu van de site, zoeken, thema&#39;s en brandingfuncties.

### Instellingen voor Titel en URL {#title-and-url-settings}

**Titel** en **URL** zijn eigenschappen die alle functies van de gemeenschap gemeen hebben.

Wanneer een communautaire functie aan een malplaatje van de communautaire plaats wordt toegevoegd of wanneer toegevoegd [wijzigen](/help/communities/sites-console.md#modifying-site-properties) In de structuur van een communitysite wordt het dialoogvenster van de functie geopend, zodat de titel en de URL kunnen worden geconfigureerd.

#### Configuratiefunctie {#configuration-function-details}

![title-url-details](assets/title-url-details.png)

* **Titel**

  (*Vereist*) De tekst die wordt weergegeven in het menu met functies voor de site

* **URL**

  (*Vereist*) De naam die wordt gebruikt om de URI te genereren. De naam moet overeenkomen met de [naamconventies](/help/sites-developing/naming-conventions.md) opgelegd door AEM en JCR.

Als u bijvoorbeeld de site gebruikt die u hebt gemaakt op basis van de [Aan de slag](/help/communities/getting-started.md) zelfstudie, als

* Titel = webpagina
* URL = pagina

De URL naar de pagina is vervolgens https://localhost:4503/content/sites/engage/en/page.html

en de menukoppeling voor de pagina wordt weergegeven als:

![opengageren](assets/engage-page.png)

### Functie activiteitsstroom {#activity-stream-function}

De functie activity stream is een pagina met een [Activiteitsstromen](/help/communities/activities.md) met alle geselecteerde weergaven (alle activiteiten, gebruikersactiviteiten en volgende). Zie ook [Essentiële elementen activiteitsstroom](/help/communities/essentials-activities.md) voor ontwikkelaars.

Wanneer u een sjabloon toevoegt, wordt het volgende dialoogvenster geopend:

#### Configuratiefunctie {#configuration-function-details-1}

![functiedetails](assets/function-details.png)

* [Instellingen voor Titel en URL](#title-and-url-settings)

* **Weergave &quot;Mijn activiteiten&quot; weergeven**

  Als deze optie is geselecteerd, bevat de pagina Activiteiten een tabblad waarop activiteiten worden gefilterd op basis van activiteiten die door het huidige lid binnen de gemeenschap worden gegenereerd. Standaard is geselecteerd.

* **Weergave Alle activiteiten tonen**

  Als deze optie is geselecteerd, bevat de pagina Activiteiten een tabblad dat alle binnen de gemeenschap gegenereerde activiteiten bevat waartoe het huidige lid toegang heeft. Standaard is geselecteerd.

* **Weergave &quot;News Feed&quot; weergeven**

  Als deze optie is geselecteerd, bevatten de pagina Activiteiten een tabblad waarop activiteiten worden gefilterd op basis van activiteiten die het huidige lid volgt. Standaard is geselecteerd.

### Blogfunctie {#blog-function}

De blogfunctie is een pagina met een [Blogcomponent](/help/communities/blog-feature.md) geconfigureerd voor labelen, het uploaden van bestanden, als volgt, leden die zichzelf moeten bewerken, stemmen en moderatie. Zie ook [Grondbeginselen van blogs](/help/communities/blog-developer-basics.md) voor ontwikkelaars.

Wanneer u een sjabloon toevoegt, wordt het volgende dialoogvenster geopend:

![blogcomponent](assets/blog-component.png)

* [Instellingen voor Titel en URL](#title-and-url-settings)

* **Geprivilegieerde leden toestaan**

  Als deze optie is geselecteerd, kunnen geprivilegieerde leden alleen artikelen maken door de selectie van een [groep geprivilegieerde leden](/help/communities/users.md#privileged-members-group). Als deze optie niet is geselecteerd, mogen alle leden van de community het bestand maken. De optie Standaard is uitgeschakeld.

* **Uploaden van bestanden toestaan**

  Als deze optie is geselecteerd, biedt de blog leden de mogelijkheid bestanden te uploaden. Standaard is geselecteerd.

* **Reacties met verbindingen toestaan**

  Als deze optie niet is geselecteerd, staat de blog reacties (opmerkingen) op een artikel toe, maar zijn reacties op opmerkingen niet toegestaan. Standaard is geselecteerd.

* **Aanbevolen inhoud toestaan**

  Indien geselecteerd, wordt de blog geïdentificeerd als [aanbevolen inhoud](/help/communities/featured.md). Standaard is geselecteerd.

### Kalenderfunctie {#calendar-function}

De kalenderfunctie is een pagina met een [Kalendercomponent](/help/communities/calendar.md) geconfigureerd om tags toe te staan. Zie ook [Essentiële elementen van agenda](/help/communities/calendar-basics-for-developers.md) voor ontwikkelaars.

Wanneer u een sjabloon toevoegt, wordt het volgende dialoogvenster geopend:

![Kalender](assets/calendar-details.png)

* [Instellingen voor Titel en URL](#title-and-url-settings)

* **Vastzetten toestaan**

  Indien geselecteerd, laat het forum onderwerpantwoorden toe om aan het begin van de lijst van commentaren worden vastgezet. Standaard is geselecteerd.

* **Geprivilegieerde leden toestaan**

  Als deze optie is geselecteerd, kunnen geprivilegieerde leden alleen artikelen maken door de selectie van een [groep geprivilegieerde leden](/help/communities/users.md#privileged-members-group). Als deze optie niet is geselecteerd, mogen alle leden van de community het bestand maken. De optie Standaard is uitgeschakeld.

* **Uploaden van bestanden toestaan**

  Als deze optie is geselecteerd, biedt de blog leden de mogelijkheid bestanden te uploaden. Standaard is geselecteerd.

* **Reacties met verbindingen toestaan**

  Als deze optie niet is geselecteerd, staat de blog reacties (opmerkingen) op een artikel toe, maar zijn reacties op opmerkingen niet toegestaan. Standaard is geselecteerd.

* **Aanbevolen inhoud toestaan**

  Indien geselecteerd, wordt de inhoud ervan geïdentificeerd als [aanbevolen inhoud](/help/communities/featured.md). Standaard is geselecteerd.

### Functie aanbevolen inhoud {#featured-content-function}

De functie voor aanbevolen inhoud is een pagina met een [Aanbevolen inhoudscomponent](/help/communities/featured.md) geconfigureerd om opmerkingen toe te voegen en te verwijderen.

De mogelijkheid om inhoud van kenmerken te voorzien, is mogelijk toegestaan of niet toegestaan voor elk onderdeel (zie [Blogfunctie](#blog-function), [Kalenderfunctie](#calendar-function), [Functie van forum](#forum-function), [Idealisatiefunctie](#ideation-function), en [QnA-functie](#qna-function)).

Wanneer toegevoegd aan een malplaatje, is de enige configuratie voor [Instellingen voor Titel en URL](#title-and-url-settings).

### Functie bestandsbibliotheek {#file-library-function}

De bestandsbibliotheekfunctie is een pagina met een [Bestandsbibliotheek, component](/help/communities/file-library.md) geconfigureerd om opmerkingen toe te voegen en te verwijderen.

Wanneer toegevoegd aan een malplaatje, is de enige configuratie voor [Instellingen voor Titel en URL](#title-and-url-settings).

### Functie van forum {#forum-function}

De forumfunctie is een pagina met een [Forum-component](/help/communities/forum.md) geconfigureerd voor labelen, het uploaden van bestanden, als volgt, leden die zichzelf moeten bewerken, stemmen en moderatie.

Wanneer u een sjabloon toevoegt, wordt het volgende dialoogvenster geopend:

#### Configuratiefunctie {#configuration-function-details-2}

![forum-component1](assets/forum-component1.png)

* [Instellingen voor Titel en URL](#title-and-url-settings)

* **Vastzetten toestaan**

  Indien geselecteerd, laat het forum onderwerpantwoorden toe om aan het begin van de lijst van commentaren worden vastgezet. Standaard is geselecteerd.

* **Geprivilegieerde leden toestaan**

  Indien geselecteerd, staat het forum slechts bevoorrechte leden toe om onderwerpen te posten door selectie van toe te staan [groep geprivilegieerde leden](/help/communities/users.md#privileged-members-group). Als deze optie niet is geselecteerd, mogen alle leden van de gemeenschap posten. De optie Standaard is uitgeschakeld.

* **Uploaden van bestanden toestaan**

  Als deze optie is geselecteerd, kunnen leden bestanden uploaden. Standaard is geselecteerd.

* **Reacties met verbindingen toestaan**

  Als deze optie niet is geselecteerd, staat het forum commentaar op een onderwerp toe, maar zijn antwoorden op deze opmerkingen niet toegestaan. Standaard is geselecteerd.

* **Aanbevolen inhoud toestaan**

  Indien geselecteerd, wordt de inhoud van de component geïdentificeerd als [aanbevolen inhoud](/help/communities/featured.md). Standaard is geselecteerd.

### Functie Groepen {#groups-function}

>[!CAUTION]
>
>De groepfunctie moet *niet* zijn *eerst of alleen* functioneren in de structuur van een site of in een sjabloon voor een community-site.
>
>Elke andere functie, zoals de [page, functie](#page-function), moet worden opgenomen en als eerste worden vermeld.

De groepsfunctie biedt leden van de gemeenschap de mogelijkheid om subgemeenschappen binnen de gemeenschapssite in de publicatieomgeving te maken.

Afhankelijk van [instellingen](/help/communities/sites-console.md#groupmanagement) wanneer de functie Groepen is opgenomen in een [sjabloon voor community-site](/help/communities/sites.md), kunnen de groepen openbaar of privé zijn en één of meerdere malplaatjes van de communautaire groep kunnen worden gevormd om een keus van malplaatjes te verstrekken wanneer de communautaire groep eigenlijk wordt gecreeerd (zoals van het publicatiemilieu). A [communitygroepsjabloon](/help/communities/tools-groups.md) Hiermee geeft u aan welke communautaire functies worden gemaakt voor de pagina&#39;s van de groep, zoals forums en kalenders.

Wanneer een communautaire groep wordt gecreeerd, wordt een lidgroep dynamisch gecreeerd voor de nieuwe groep, waaraan de leden kunnen worden toegewezen of zich aansluiten. Zie voor meer informatie [Gebruikers en gebruikersgroepen beheren](/help/communities/users.md).

Vanaf Gemeenschappen [functiepakket 1](/help/communities/deploy-communities.md#latestfeaturepack), worden in de ontwerpomgeving groepen gemaakt met de [Community Sites Group-console](/help/communities/groups.md)en kan worden gemaakt in de publicatieomgeving wanneer deze is ingeschakeld.

Wanneer u een sjabloon toevoegt, wordt het volgende dialoogvenster geopend:

![group-template-config](assets/group-template-config.png)

* [Instellingen voor Titel en URL](#title-and-url-settings)

* **Groepssjablonen selecteren**

  Een drop-down die selectie van één of meerdere toegelaten groepsmalplaatjes toestaat waarvan de toekomstige schepper van een nieuwe communautaire groep (in het publicatiemilieu) kan kiezen.

* **Geprivilegieerde leden toestaan**

  Indien geselecteerd, staat het forum slechts bevoorrechte leden toe om onderwerpen te posten door selectie van toe te staan [veiligheidsgroep van geprivilegieerde leden](/help/communities/users.md#privileged-members-group). Als deze optie niet is geselecteerd, mogen alle leden van de gemeenschap posten. De optie Standaard is uitgeschakeld.

* **Publiceren toestaan**

  Als deze optie is geselecteerd, kunnen geautoriseerde leden van de gemeenschap een groep maken in de publicatieomgeving. Als deze optie niet is geselecteerd, kunnen alleen nieuwe groepen (subgemeenschappen) worden gemaakt in de auteursomgeving van de console Groepen van sites van de Gemeenschappen.
Standaard is geselecteerd.

### Idealisatiefunctie {#ideation-function}

De videofunctie is een pagina met één [Onderdeel voor ideeën](/help/communities/ideation-feature.md).

Wanneer u een sjabloon toevoegt, wordt het volgende dialoogvenster geopend met de standaardnamen voor Titel en URL en de standaardweergave-instellingen voor de sjabloon:

![ideatie-functie](assets/ideation-function.png)

* [Instellingen voor Titel en URL](#title-and-url-settings)

* **Geprivilegieerde leden toestaan**

  Indien geselecteerd, staat het forum slechts bevoorrechte leden toe om onderwerpen te posten door selectie van toe te staan [veiligheidsgroep van geprivilegieerde leden](/help/communities/users.md#privileged-members-group). Als deze optie niet is geselecteerd, mogen alle leden van de gemeenschap posten. De optie Standaard is uitgeschakeld.

* **Uploaden van bestanden toestaan**

  Als deze optie is geselecteerd, kunnen leden bestanden uploaden. Standaard is geselecteerd.

* **Reacties met verbindingen toestaan**

  Als deze optie niet is geselecteerd, kunnen reacties (opmerkingen) op een onderwerp worden geplaatst, maar kunnen opmerkingen niet worden beantwoord. Standaard is geselecteerd.

* **Aanbevolen inhoud toestaan**

  Indien geselecteerd, wordt de inhoud ervan geïdentificeerd als [aanbevolen inhoud](/help/communities/featured.md). Standaard is geselecteerd.

### Leaderboard-functie {#leaderboard-function}

De leaderboardfunctie is een pagina met één pagina [Leaderboard-component](/help/communities/enabling-leaderboard.md).

**OPMERKING**: De component Leaderboard moet verder worden geconfigureerd *na* Er wordt een community-site gemaakt op basis van een communitysjabloon die de Leaderboard-functie bevat. De Leaderboard-componenten opgeven [regels](/help/communities/enabling-leaderboard.md#rules-tab), die afhankelijk zijn van de configuratie van [scoring en badges](/help/communities/implementing-scoring.md) voor de site van de community.

Wanneer u een sjabloon toevoegt, wordt het volgende dialoogvenster geopend met de standaardnamen voor Titel en URL en de standaardweergave-instellingen voor de sjabloon:

![leaderboard-dialog](assets/leaderboard-dialog.png)

* [Instellingen voor Titel en URL](#title-and-url-settings)

* **Badge weergeven**

  Als deze optie is geselecteerd, wordt een kolom voor badge-pictogrammen opgenomen in het leaderboard.
De optie Standaard is uitgeschakeld.

* **Naam van badge weergeven**

  Als deze optie is geselecteerd, wordt een kolom met de naam van de badge in het leaderboard opgenomen.
De optie Standaard is uitgeschakeld.

* **Avatar weergeven**

  Als deze optie is geselecteerd, wordt de avatarafbeelding van het lid opgenomen in het leaderboard, naast de naamkoppeling naar het profiel van het lid.
De optie Standaard is uitgeschakeld.

### Paginacode {#page-function}

De paginafunctie voegt een lege pagina aan de communautaire plaats toe dat het in de eigenschappen van de communautaire plaats wordt getelegrafeerd: login, menu, berichten, overseinen, thema en branding. Inhoud wordt aan de pagina toegevoegd met de [standaard AEM ontwerpmodus](/help/sites-authoring/editing-content.md).

Wanneer toegevoegd aan een malplaatje, is de enige configuratie voor [Instellingen voor Titel en URL](#title-and-url-settings).

### QnA-functie {#qna-function}

De functie QnA is een pagina met een [QnA-component](/help/communities/working-with-qna.md) geconfigureerd voor labelen, het uploaden van bestanden, als volgt, leden die zichzelf moeten bewerken, stemmen en moderatie.

Wanneer toegevoegd aan een malplaatje, staat de configuratie beperking aan bevoorrechte leden toe:

![qna-dialog](assets/qna-dialog.png)

* [Instellingen voor Titel en URL](#title-and-url-settings)

* **Vastzetten toestaan**

  Indien geselecteerd, laat het forum onderwerpantwoorden toe om aan het begin van de lijst van commentaren worden vastgezet. Standaard is geselecteerd.

* **Geprivilegieerde leden toestaan**

  Indien geselecteerd, staat het forum QnA slechts bevoorrechte leden toe om vragen te posten door selectie van toe te staan [groep geprivilegieerde leden](/help/communities/users.md#privileged-members-group). Als deze optie niet is geselecteerd, mogen alle leden van de gemeenschap posten. De optie Standaard is uitgeschakeld.

* **Uploaden van bestanden toestaan**

  Indien geselecteerd, omvat het forum QnA de capaciteit voor leden om dossiers te uploaden. Standaard is geselecteerd.

* **Reacties met verbindingen toestaan**

  Als deze optie niet is geselecteerd, kan op het QnA-forum commentaar (antwoorden) worden gegeven op een geposte vraag, maar antwoorden op antwoorden zijn niet toegestaan. Standaard is geselecteerd.

* **Aanbevolen inhoud toestaan**

  Indien geselecteerd, wordt de inhoud ervan geïdentificeerd als [aanbevolen inhoud](/help/communities/featured.md). Standaard is geselecteerd.

## Community-functie maken {#create-community-function}

De mogelijkheid om een gemeenschapsfunctie te maken, wordt bereikt door de `Create Community Function` pictogram boven aan de console voor communautaire functies. Er kunnen meerdere functies worden gemaakt die op dezelfde AEM blauwdruk zijn gebaseerd en vervolgens op unieke wijze worden aangepast door het openen in de bewerkingsmodus van de auteur.

![create-community-function](assets/create-community-function.png)

### Community-functienaam {#community-function-name}

![function-name](assets/function-name.png)

In het deelvenster Community Function Name worden een naam, beschrijving en of de functie is ingeschakeld of uitgeschakeld geconfigureerd:

* **Community-functienaam**

  De functienaam die wordt gebruikt voor weergave en opslag.

* **Beschrijving van functie Gemeenschap**

  De functiebeschrijving voor de weergave.

* **Uitgeschakeld/Ingeschakeld**

  Een schakeloptie die bepaalt of naar de functie kan worden verwezen.

### AEM {#aem-blueprint}

![aem-blauwdruk](assets/aem-blueprint.png)

Op de `AEM Blueprint` is het mogelijk de blauwdruk te selecteren die de onderliggende uitvoering van de communautaire functie is .

De functie van de gemeenschap is een mini plaats die één of meerdere pagina&#39;s omvat, die voor opneming in een communautaire plaats met inbegrip van login, gebruikersprofielen, berichten, overseinen, plaatsmenu, onderzoek, thema, en branding eigenschappen vooraf worden getelegrafeerd. Wanneer de functie is gemaakt, is het mogelijk om [open de functie](#open-community-function) in de bewerkingsmodus van de auteur en pas de pagina- of componentinstellingen aan.

Aangezien de communautaire functie als [live kopie](/help/sites-administering/msm.md#live-copies) van een [blauwdruk](/help/sites-administering/msm-livecopy.md#creatingablueprint), is het mogelijk wijzigingen door te voeren die zijn aangebracht in een functie die van invloed is op alle pagina&#39;s van de gemeenschapssite die zijn gemaakt op basis van de [sjabloon voor community-site](/help/communities/sites.md) of [communitygroepsjabloon](/help/communities/tools-groups.md) dat de functie omvatte. Het is ook mogelijk om een pagina los te koppelen van de bovenliggende blauwdruk om wijzigingen op paginaniveau aan te brengen.

Zie ook [Beheer van meerdere sites](/help/sites-administering/msm.md).

### Miniatuur {#thumbnail}

![functie-miniatuur](assets/funtion-thumbnail.png)

In het deelvenster Miniatuur kan een afbeelding worden geüpload om te worden weergegeven in het dialoogvenster [Community Functions-console](#community-functions-console).

## Community-functie openen {#open-community-function}

![open functie](assets/open-function.png)

Selecteer de `Open Community Function` pictogram om de bewerkingsmodus voor auteurs in te schakelen voor het ontwerpen van de pagina-inhoud en het wijzigen van de configuratie van de component(en) met functies.

### Componenten configureren {#configuring-components}

Een communautaire functie wordt uitgevoerd als Levende Kopie van een AEM Blauwdruk, die details onder wordt gedocumenteerd [Beheer van meerdere sites](/help/sites-administering/msm.md).

Het is mogelijk om niet alleen pagina-inhoud te schrijven, maar componenten te configureren.

Als het vormen van een component op een pagina van een gecreeerde communautaire plaats, kan het noodzakelijk zijn om te annuleren [overerving](/help/sites-administering/msm-livecopy.md#changing-live-copy-content) om de component te configureren. De overerving moet worden hersteld wanneer de configuratie is voltooid.

Voor configuratiedetails, bezoek [Community-componenten](/help/communities/author-communities.md) voor auteurs.

## Community-functie bewerken {#edit-community-function}

![bewerken, functie](assets/edit-function.png)

Selecteer de `Edit Community Function` pictogram om de eigenschappen van de functie te bewerken met dezelfde deelvensters als [gemeenschapsfunctie maken](#create-community-function), inclusief het inschakelen of uitschakelen van de functie.
