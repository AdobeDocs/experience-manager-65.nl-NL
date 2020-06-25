---
title: Communautaire functies
seo-title: Communautaire functies
description: Leer hoe u toegang krijgt tot de Community Function Console
seo-description: Leer hoe u toegang krijgt tot de Community Function Console
uuid: d3d70134-f318-4709-a673-b01a3467d980
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 91833914-b811-4355-a97d-e1a9cb7441f1
docset: aem65
translation-type: tm+mt
source-git-commit: 1b200f9dd5fc99b37bcc629be7a785e02e8320c0
workflow-type: tm+mt
source-wordcount: '2454'
ht-degree: 0%

---


# Communautaire functies{#community-functions}

Het type functies dat wordt verwacht van een community-ervaring is bekend. De communautaire eigenschappen zijn beschikbaar als communautaire functies. In wezen zijn ze een of meer pagina&#39;s die vooraf zijn bekabeld om een community-functie te implementeren. Hiervoor is meer nodig dan alleen het toevoegen van een component aan een pagina in de modus Schrijven. Zij zijn de bouwstenen die worden gebruikt om de structuur van een malplaatje [van de](/help/communities/sites.md) communautaire plaats te bepalen waarvan de communautaire plaatsen worden [gecreeerd](/help/communities/sites-console.md).

Nadat een gemeenschapssite is gemaakt, kan inhoud aan de resulterende pagina&#39;s worden toegevoegd met de standaard [AEM-ontwerpmodus](/help/sites-authoring/editing-content.md). Verschillende communityfuncties zijn beschikbaar zoals in de console voor communityfuncties.

>[!NOTE]
>
>De consoles voor de verwezenlijking van [communautaire plaatsen](/help/communities/sites-console.md), de malplaatjes [van de](/help/communities/sites.md)communautaire plaats, [communautaire groepsmalplaatjes](/help/communities/tools-groups.md), en [communautaire functies](/help/communities/functions.md) zijn voor gebruik slechts in het auteursmilieu.


## Community-functieconsole {#community-functions-console}

Om de console van communautaire functies in het auteursmilieu te bereiken:

* Ga naar **[!UICONTROL Tools]** > **[!UICONTROL Communities]** > **[!UICONTROL Community Functions]**.

![chlimage_1-379](assets/chlimage_1-379.png)

## Vooraf gebouwde functies {#pre-built-functions}

Hier volgt een korte beschrijving van de functies die bij AEM Communities worden geleverd. Elke functie bevat een of meer AEM-pagina&#39;s die onderdelen van een Community bevatten die zijn samengevoegd tot een functie die eenvoudig kan worden opgenomen in een [community-sitesjabloon](/help/communities/sites.md).

Een communitysitesjabloon biedt de structuur voor een communitysite, zoals aanmeldingsgegevens, gebruikersprofielen, meldingen, berichten, berichten, het menu van de site, zoeken, thema&#39;s en brandingfuncties.

### Instellingen voor Titel en URL {#title-and-url-settings}

**Titel** en **URL** zijn eigenschappen die voor alle communautaire functies gelden.

Wanneer een communautaire functie aan een malplaatje van de communautaire plaats wordt toegevoegd of toegevoegd wanneer het [wijzigen](/help/communities/sites-console.md#modifying-site-properties) van de structuur van een communautaire plaats, opent de dialoog van de functie zodat de Titel en URL kunnen worden gevormd.

#### Configuratiefunctie {#configuration-function-details}

![chlimage_1-380](assets/chlimage_1-380.png)

* **Titel**

   (*Vereist*) De tekst die wordt weergegeven in het menu met functies voor de site

* **URL**

   (*Vereist*) De naam die wordt gebruikt om URI te genereren. De naam moet voldoen aan de [naamgevingsconventies](/help/sites-developing/naming-conventions.md) die door AEM en JCR worden opgelegd.

Als u bijvoorbeeld de site gebruikt die u hebt gemaakt op basis van de zelfstudie [Aan de slag](/help/communities/getting-started.md) , als

* Titel = webpagina
* URL = pagina

De URL naar de pagina is vervolgens https://localhost:4503/content/sites/engage/en/page.html

en de menukoppeling voor de pagina wordt weergegeven als:

![chlimage_1-381](assets/chlimage_1-381.png)

### Functie activiteitsstroom {#activity-stream-function}

De functie van de activiteitenstroom is een pagina met een component [van de Streams van de](/help/communities/activities.md) Activiteit met alle geselecteerde meningen (alle activiteiten, gebruikersactiviteiten, en het volgende). Zie ook Essentiële [elementen](/help/communities/essentials-activities.md) van Activiteitenstroom voor ontwikkelaars.

Wanneer u een sjabloon toevoegt, wordt het volgende dialoogvenster geopend:

#### Configuratiefunctie {#configuration-function-details-1}

![chlimage_1-382](assets/chlimage_1-382.png)

* [Instellingen voor Titel en URL](#title-and-url-settings)

* **Weergave Mijn activiteiten tonen**

   Als deze optie is geselecteerd, bevat de pagina Activiteiten een tabblad waarop activiteiten worden gefilterd op basis van activiteiten die door het huidige lid binnen de gemeenschap worden gegenereerd. Standaard is geselecteerd.

* **Weergave Alle activiteiten tonen**

   Als deze optie is geselecteerd, bevat de pagina Activiteiten een tabblad dat alle binnen de gemeenschap gegenereerde activiteiten bevat waartoe het huidige lid toegang heeft. Standaard is geselecteerd.

* **Weergave Nieuwe feed tonen**

   Als deze optie is geselecteerd, bevatten de pagina Activiteiten een tabblad waarop activiteiten worden gefilterd op basis van activiteiten die het huidige lid volgt. Standaard is geselecteerd.

### Toewijzingsfunctie {#assignments-function}

De toewijzingsfunctie is de basisfunctie die een [communitysite voor activering](/help/communities/overview.md#enablement-community)definieert. Het maakt het mogelijk middelen voor activering toe te wijzen aan leden van de gemeenschap. Zie ook Essentiële [toewijzingen](/help/communities/essentials-assignments.md) voor ontwikkelaars.

Deze functie is beschikbaar als een eigenschap van [enablement toe:voegen-aan](/help/communities/enablement.md). De inschakelingsadd-on vereist aanvullende licenties voor gebruik in een productieomgeving.

Als u een sjabloon toevoegt, is de enige configuratie de instellingen [Titel en URL](#title-and-url-settings).

### Blogfunctie {#blog-function}

De blogfunctie is een pagina met een [blogcomponent](/help/communities/blog-feature.md) die is geconfigureerd voor het labelen, uploaden van bestanden en volgende, leden die zichzelf kunnen bewerken, stemmen en moderatie. Zie ook [Blog Essentials](/help/communities/blog-developer-basics.md) voor ontwikkelaars.

Wanneer u een sjabloon toevoegt, wordt het volgende dialoogvenster geopend:

![chlimage_1-383](assets/chlimage_1-383.png)

* [Instellingen voor Titel en URL](#title-and-url-settings)

* **Geprivilegieerde leden toestaan**

   Als deze optie is geselecteerd, staat de blog alleen geprivilegieerde leden toe artikelen te maken door de selectie van een groep [](/help/communities/users.md#privileged-members-group)geprivilegieerde leden toe te staan. Als deze optie niet is geselecteerd, mogen alle leden van de community het bestand maken. Standaard is uitgeschakeld.

* **Uploaden van bestanden toestaan**

   Als deze optie is geselecteerd, bevat de blog de mogelijkheid voor leden om bestanden te uploaden. Standaard is geselecteerd.

* **Reacties met verbindingen toestaan**

   Als deze optie niet is geselecteerd, staat de blog reacties (opmerkingen) op een artikel toe, maar zijn reacties op opmerkingen niet toegestaan. Standaard is geselecteerd.

* **Aanbevolen inhoud toestaan**

   Als deze optie is geselecteerd, wordt de blog aangeduid als [aanbevolen inhoud](/help/communities/featured.md). Standaard is geselecteerd.

### Kalenderfunctie {#calendar-function}

De kalenderfunctie is een pagina met een component [van de](/help/communities/calendar.md) Kalender die wordt gevormd om het etiketteren toe te staan. Zie ook Essentiële [kalender](/help/communities/calendar-basics-for-developers.md) voor ontwikkelaars.

Wanneer u een sjabloon toevoegt, wordt het volgende dialoogvenster geopend:

![chlimage_1-384](assets/chlimage_1-384.png)

* [Instellingen voor Titel en URL](#title-and-url-settings)

* **Vastzetten toestaan**

   Indien geselecteerd, laat het forum onderwerpantwoorden toe om aan het begin van de lijst van commentaren worden vastgezet. Standaard is geselecteerd.

* **Geprivilegieerde leden toestaan**

   Als deze optie is geselecteerd, staat de blog alleen geprivilegieerde leden toe artikelen te maken door de selectie van een groep [](/help/communities/users.md#privileged-members-group)geprivilegieerde leden toe te staan. Als deze optie niet is geselecteerd, mogen alle leden van de community het bestand maken. Standaard is uitgeschakeld.

* **Uploaden van bestanden toestaan**

   Als deze optie is geselecteerd, bevat de blog de mogelijkheid voor leden om bestanden te uploaden. Standaard is geselecteerd.

* **Reacties met verbindingen toestaan**

   Als deze optie niet is geselecteerd, staat de blog reacties (opmerkingen) op een artikel toe, maar zijn reacties op opmerkingen niet toegestaan. Standaard is geselecteerd.

* **Aanbevolen inhoud toestaan**

   Als deze optie is geselecteerd, wordt de inhoud ervan geïdentificeerd als [aanbevolen inhoud](/help/communities/featured.md). Standaard is geselecteerd.

### Catalogusfunctie {#catalog-function}

De catalogusfunctie biedt de mogelijkheid voor [leden van de gemeenschap](/help/communities/overview.md#enablement-community) om te bladeren in bronnen voor activering die niet aan hen zijn toegewezen. Zie Hulpmiddelen [van Enablement van de](/help/communities/tag-resources.md) Tags en de Hoofdzaak [van de](/help/communities/catalog-developer-essentials.md) Catalogus voor ontwikkelaars.

Alle actiemiddelen en leerwegen voor de communautaire plaats toont in alle catalogi als hun bezit, ` [Show in Catalog](/help/communities/resources.md)`, aan waar wordt geplaatst. Als u expliciet bronnen en leerpaden wilt opnemen, moet u een [voorfilter](/help/communities/catalog-developer-essentials.md#pre-filters) toepassen op de catalogus.

Wanneer de configuratie aan een sjabloon is toegevoegd, kunt u met de configuratie tagnaamruimten opgeven die worden gebruikt om het tagfilter te configureren dat aan bezoekers van de site wordt aangeboden:

![Catalog, functie](assets/catalog-function.png)

* [Instellingen voor Titel en URL](#title-and-url-settings)

* **Alle naamruimten selecteren**

   Met de geselecteerde tagnaamruimten wordt gedefinieerd welke tags bezoekers kunnen selecteren voor het filteren van de lijst met activeringsbronnen die in de catalogus wordt vermeld.
Als deze optie is geselecteerd, zijn alle naamruimten voor tags die zijn toegestaan voor de communitysite beschikbaar.
Als deze optie is uitgeschakeld, is het mogelijk een of meer naamruimten te selecteren die zijn toegestaan voor de site van de community.
Standaard is geselecteerd.

### Functie aanbevolen inhoud {#featured-content-function}

De functie aanbevolen inhoud is een pagina met een component [](/help/communities/featured.md) aanbevolen inhoud die is geconfigureerd om opmerkingen toe te voegen en te verwijderen.

De mogelijkheid om inhoud van inhoud te voorzien, is per component toegestaan of niet toegestaan (zie [Blogfunctie](#blog-function), [Kalenderfunctie](#calendar-function), [de Functie](#forum-function)van het Forum, de Functie [van het](#ideation-function)Ideeën, en Functie [](#qna-function)QnA).

Als u een sjabloon toevoegt, is de enige configuratie de instellingen [Titel en URL](#title-and-url-settings).

### Functie bestandsbibliotheek {#file-library-function}

De bestandsbibliotheekfunctie is een pagina waarvan de component [](/help/communities/file-library.md) Bestandsbibliotheek is geconfigureerd voor het toevoegen en verwijderen van opmerkingen.

Als u een sjabloon toevoegt, is de enige configuratie de instellingen [Titel en URL](#title-and-url-settings).

### Functie van forum {#forum-function}

De forumfunctie is een pagina met een component [van het](/help/communities/forum.md) Forum dat voor het etiketteren wordt gevormd, uploadt het dossier, na, leden aan zelf-uit te geven, te stemmen, en matiging.

Wanneer u een sjabloon toevoegt, wordt het volgende dialoogvenster geopend:

#### Configuratiefunctie {#configuration-function-details-2}

![chlimage_1-384](assets/chlimage_1-384.png)

* [Instellingen voor Titel en URL](#title-and-url-settings)

* **Vastzetten toestaan**

   Indien geselecteerd, laat het forum onderwerpantwoorden toe om aan het begin van de lijst van commentaren worden vastgezet. Standaard is geselecteerd.

* **Geprivilegieerde leden toestaan**

   Indien geselecteerd, staat het forum slechts bevoorrechte leden toe om onderwerpen te posten door selectie van een [bevoorrechte ledengroep](/help/communities/users.md#privileged-members-group)toe te staan. Als deze optie niet is geselecteerd, mogen alle leden van de gemeenschap posten. Standaard is uitgeschakeld.

* **Uploaden van bestanden toestaan**

   Als deze optie is geselecteerd, kunnen leden bestanden uploaden. Standaard is geselecteerd.

* **Reacties met verbindingen toestaan**

   Als deze optie niet is geselecteerd, staat het forum commentaar op een onderwerp toe, maar zijn antwoorden op deze opmerkingen niet toegestaan. Standaard is geselecteerd.

* **Aanbevolen inhoud toestaan**

   Als deze optie is geselecteerd, wordt de inhoud van de component aangeduid als [aanbevolen inhoud](/help/communities/featured.md). Standaard is geselecteerd.

### Functie Groepen {#groups-function}

>[!CAUTION]
>
>De groepfunctie mag *niet* de *eerste of de enige* functie in de structuur van een site of in een sjabloon voor een community-site zijn.
>
>Alle andere functies, zoals de [paginafunctie](#page-function), moeten worden opgenomen en als eerste worden vermeld.


De groepsfunctie biedt leden van de gemeenschap de mogelijkheid om subgemeenschappen binnen de gemeenschapssite in de publicatieomgeving te maken.

Afhankelijk van [montages](/help/communities/sites-console.md#groupmanagement) wanneer de functie van Groepen in een malplaatje [van de](/help/communities/sites.md)communautaire plaats inbegrepen is, kunnen de groepen openbaar of privé zijn en één of meerdere malplaatjes van de communautaire groep kunnen worden gevormd om een keus van malplaatjes te verstrekken wanneer de communautaire groep eigenlijk wordt gecreeerd (zoals van het publicatiemilieu). In een sjabloon [voor een](/help/communities/tools-groups.md) community-groep wordt aangegeven welke Gemeenschappen-functies worden gemaakt voor de groepspagina&#39;s, zoals forums en kalenders.

Wanneer een communautaire groep wordt gecreeerd, wordt een lidgroep dynamisch gecreeerd voor de nieuwe groep, waaraan de leden kunnen worden toegewezen of zich aansluiten. Zie Gebruikers en gebruikersgroepen [](/help/communities/users.md)beheren voor meer informatie.

Vanaf de [eigenschapverpakking 1](/help/communities/deploy-communities.md#latestfeaturepack)van de Gemeenschappen, worden de communautaire groepen gecreeerd in het auteursmilieu gebruikend de console [van de Groepen van](/help/communities/groups.md)Plaatsen van Gemeenschappen, en kunnen in het publicatiemilieu worden gecreeerd wanneer toegelaten.

Wanneer u een sjabloon toevoegt, wordt het volgende dialoogvenster geopend:

![chlimage_1-386](assets/chlimage_1-386.png)

* [Instellingen voor Titel en URL](#title-and-url-settings)

* **Groepssjablonen selecteren**

   Een drop-down die selectie van één of meerdere toegelaten groepsmalplaatjes toestaat waarvan de toekomstige schepper van een nieuwe communautaire groep (in het publicatiemilieu) kan kiezen.

* **Geprivilegieerde leden toestaan**

   Indien geselecteerd, staat het forum slechts bevoorrechte leden toe om onderwerpen te posten door selectie van een [bevoorrechte groep](/help/communities/users.md#privileged-members-group)van de ledenveiligheid toe te staan. Als deze optie niet is geselecteerd, mogen alle leden van de gemeenschap posten. Standaard is uitgeschakeld.

* **Publiceren toestaan**

   Als deze optie is geselecteerd, kunnen geautoriseerde leden van de gemeenschap een groep maken in de publicatieomgeving. Als deze optie niet is geselecteerd, kunnen alleen nieuwe groepen (subgemeenschappen) worden gemaakt in de auteursomgeving van de console Groepen van sites van de Gemeenschappen.
Standaard is geselecteerd.

### Idealisatiefunctie {#ideation-function}

De videofunctie is een pagina met één component [](/help/communities/ideation-feature.md)Ideatie.

Wanneer u een sjabloon toevoegt, wordt het volgende dialoogvenster geopend met de standaardnamen voor Titel en URL en de standaardweergave-instellingen voor de sjabloon:

![chlimage_1-387](assets/chlimage_1-387.png)

* [Instellingen voor Titel en URL](#title-and-url-settings)

* **Geprivilegieerde leden toestaan**

   Indien geselecteerd, staat het forum slechts bevoorrechte leden toe om onderwerpen te posten door selectie van een [bevoorrechte groep](/help/communities/users.md#privileged-members-group)van de ledenveiligheid toe te staan. Als deze optie niet is geselecteerd, mogen alle leden van de gemeenschap posten. Standaard is uitgeschakeld.

* **Uploaden van bestanden toestaan**

   Als deze optie is geselecteerd, kunnen leden bestanden uploaden. Standaard is geselecteerd.

* **Reacties met verbindingen toestaan**

   Als deze optie niet is geselecteerd, kunnen reacties (opmerkingen) op een onderwerp worden geplaatst, maar kunnen opmerkingen niet worden beantwoord. Standaard is geselecteerd.

* **Aanbevolen inhoud toestaan**

   Als deze optie is geselecteerd, wordt de inhoud ervan geïdentificeerd als [aanbevolen inhoud](/help/communities/featured.md). Standaard is geselecteerd.

### Leaderboard-functie {#leaderboard-function}

De leaderboard-functie is een pagina met één [Leaderboard-component](/help/communities/enabling-leaderboard.md).

**OPMERKING**: De component Leaderboard moet verder worden geconfigureerd *nadat* een site van een community is gemaakt op basis van een sjabloon van een community die de functie Leaderboard bevat. Geef de [regels](/help/communities/enabling-leaderboard.md#rules-tab)van de component Leaderboard op, die afhankelijk zijn van de configuratie van [scoring en badges](/help/communities/implementing-scoring.md) voor de site van de community.

Wanneer u een sjabloon toevoegt, wordt het volgende dialoogvenster geopend met de standaardnamen voor Titel en URL en de standaardweergave-instellingen voor de sjabloon:

![chlimage_1-388](assets/chlimage_1-388.png)

* [Instellingen voor Titel en URL](#title-and-url-settings)

* **Badge weergeven**

   Als deze optie is geselecteerd, wordt een kolom voor badge-pictogrammen opgenomen in het leaderboard.
Standaard is uitgeschakeld.

* **Naam van badge weergeven**

   Als deze optie is geselecteerd, wordt een kolom met de naam van de badge in het leaderboard opgenomen.
Standaard is uitgeschakeld.

* **Avatar weergeven**

   Als deze optie is geselecteerd, wordt de avatarafbeelding van het lid opgenomen in het leaderboard, naast de naamkoppeling naar het profiel van het lid.
Standaard is uitgeschakeld.

### Paginacode {#page-function}

De paginafunctie voegt een lege pagina aan de communautaire plaats toe dat het in de eigenschappen van de communautaire plaats wordt getelegrafeerd: aanmelden, menu, meldingen, berichten, berichten, thema&#39;s en branding. Inhoud wordt aan de pagina toegevoegd met de [standaardontwerpmodus](/help/sites-authoring/editing-content.md)van AEM.

Als u een sjabloon toevoegt, is de enige configuratie de instellingen [Titel en URL](#title-and-url-settings).

### QnA-functie {#qna-function}

De functie QnA is een pagina met een component [](/help/communities/working-with-qna.md) QnA die voor het etiketteren wordt gevormd, uploadt het dossier, na, leden aan zelf-uitgeven, het stemmen, en matiging.

Wanneer toegevoegd aan een malplaatje, staat de configuratie beperking aan bevoorrechte leden toe:

![chlimage_1-384](assets/chlimage_1-384.png)

* [Instellingen voor Titel en URL](#title-and-url-settings)

* **Vastzetten toestaan**

   Indien geselecteerd, laat het forum onderwerpantwoorden toe om aan het begin van de lijst van commentaren worden vastgezet. Standaard is geselecteerd.

* **Geprivilegieerde leden toestaan**

   Indien geselecteerd, staat het forum QnA slechts bevoorrechte leden toe om vragen te posten door selectie van een [bevoorrechte ledengroep](/help/communities/users.md#privileged-members-group)toe te staan. Als deze optie niet is geselecteerd, mogen alle leden van de gemeenschap posten. Standaard is uitgeschakeld.

* **Uploaden van bestanden toestaan**

   Indien geselecteerd, omvat het forum QnA de capaciteit voor leden om dossiers te uploaden. Standaard is geselecteerd.

* **Reacties met verbindingen toestaan**

   Als deze optie niet is geselecteerd, kan op het QnA-forum commentaar (antwoorden) worden gegeven op een geposte vraag, maar antwoorden op antwoorden zijn niet toegestaan. Standaard is geselecteerd.

* **Aanbevolen inhoud toestaan**

   Als deze optie is geselecteerd, wordt de inhoud ervan geïdentificeerd als [aanbevolen inhoud](/help/communities/featured.md). Standaard is geselecteerd.

## Community-functie maken {#create-community-function}

De capaciteit om een communautaire functie tot stand te brengen wordt bereikt door het `Create Community Function` pictogram te selecteren dat bij de bovenkant van de console van de Functies van de Gemeenschap wordt gevestigd. Er kunnen meerdere functies worden gemaakt op basis van dezelfde AEM-blauwdruk en deze kunnen vervolgens op unieke wijze worden aangepast door het openen in de bewerkingsmodus voor auteurs.

![chlimage_1-390](assets/chlimage_1-390.png)

### Community-functienaam {#community-function-name}

![chlimage_1-391](assets/chlimage_1-391.png)

In het deelvenster Community Function Name worden een naam, beschrijving en of de functie is ingeschakeld of uitgeschakeld geconfigureerd:

* **Community-functienaam**

   De functienaam die wordt gebruikt voor weergave en opslag.

* **Beschrijving van functie Gemeenschap**

   De functiebeschrijving voor de weergave.

* **Uitgeschakeld/Ingeschakeld**

   Een schakeloptie die bepaalt of naar de functie kan worden verwezen.

### AEM-vervaging {#aem-blueprint}

![chlimage_1-392](assets/chlimage_1-392.png)

In het `AEM Blueprint` deelvenster kunt u de blauwdruk selecteren die de onderliggende implementatie van de communautaire functie is.

De functie van de gemeenschap is een mini plaats die één of meerdere pagina&#39;s omvat, die voor opneming in een communautaire plaats met inbegrip van login, gebruikersprofielen, berichten, overseinen, plaatsmenu, onderzoek, thema, en branding eigenschappen vooraf worden getelegrafeerd. Nadat de functie is gemaakt, kan de functie [worden](#open-community-function) geopend in de bewerkingsmodus van de auteur en kunnen de pagina- of componentinstellingen worden aangepast.

Aangezien de communautaire functie als [levende exemplaar](/help/sites-administering/msm.md#live-copies) van een [blauwdruk](/help/sites-administering/msm-livecopy.md#creatingablueprint)wordt uitgevoerd, is het mogelijk om veranderingen uit te voeren die aan een functie worden aangebracht die alle communautaire plaatspagina&#39;s beïnvloedt die van het malplaatje [van de](/help/communities/sites.md) communautaire plaats of het malplaatje [van de](/help/communities/tools-groups.md) communautaire groep worden gecreeerd die de functie omvatte. Het is ook mogelijk om een pagina los te koppelen van de bovenliggende blauwdruk om wijzigingen op paginaniveau aan te brengen.

Zie ook [Beheer](/help/sites-administering/msm.md)van meerdere sites.

### Miniatuur {#thumbnail}

![chlimage_1-393](assets/chlimage_1-393.png)

In het venster Miniatuur kan een afbeelding worden geüpload om te worden weergegeven in de [Community Functions-console](#community-functions-console).

## Community-functie openen {#open-community-function}

![chlimage_1-394](assets/chlimage_1-394.png)

Selecteer het `Open Community Function` pictogram om de bewerkingsmodus voor de auteur te activeren voor het ontwerpen van de pagina-inhoud en het wijzigen van de configuratie van de component(en) met functies.

### Componenten configureren {#configuring-components}

Een gemeenschapsfunctie wordt geïmplementeerd als een live kopie van een AEM-blauwdruk, waarvan de details worden gedocumenteerd onder [Multi-Site Manager](/help/sites-administering/msm.md).

Het is mogelijk om niet alleen pagina-inhoud te schrijven, maar componenten te configureren.

Als het vormen van een component op een pagina van een gecreeerde communautaire plaats, kan het noodzakelijk zijn om [overerving](/help/sites-administering/msm-livecopy.md#changing-live-copy-content) te annuleren om de component te vormen. De overerving moet worden hersteld wanneer de configuratie is voltooid.

Voor configuratiedetails, bezoek [de Componenten](/help/communities/author-communities.md) van Gemeenschappen voor auteurs.

## Community-functie bewerken {#edit-community-function}

![chlimage_1-395](assets/chlimage_1-395.png)

Selecteer het `Edit Community Function` pictogram om de eigenschappen van de functie te bewerken met dezelfde deelvensters als het [maken van een gemeenschapsfunctie](#create-community-function), inclusief het in- of uitschakelen van de functie.
