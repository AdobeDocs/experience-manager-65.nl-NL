---
title: Sites-console van gemeenschappen
description: Leer hoe u toegang krijgt tot de console Communitysites voor het maken, bewerken en beheren van sites.
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
docset: aem65
role: Admin
exl-id: 426e3adf-3723-4d17-a988-6eb050939e68
solution: Experience Manager
feature: Communities
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '3082'
ht-degree: 0%

---

# Sites-console van gemeenschappen {#communities-sites-console}

De console van de Plaatsen van Gemeenschappen verleent toegang tot:

* Site maken
* Site bewerken
* Sitebeheer
* [&#x200B; Creërend en het uitgeven genestelde groepen &#x200B;](/help/communities/groups.md) (subCommunities)

Zie [&#x200B; Begonnen Worden met AEM Communities &#x200B;](/help/communities/getting-started.md) waar u kunt ervaren hoe snel een communautaire plaats in het auteursmilieu kan worden gecreeerd, en hoe te om communautaire groepen van de auteur tot stand te brengen en milieu&#39;s te publiceren.

>[!NOTE]
>
>De belangrijkste menu&#39;s van Gemeenschappen voor de verwezenlijking van [&#x200B; communautaire plaatsen &#x200B;](/help/communities/sites-console.md), [&#x200B; communautaire plaatssjablonen &#x200B;](/help/communities/sites.md), [&#x200B; communautaire groepsmalplaatjes &#x200B;](/help/communities/tools-groups.md), en [&#x200B; communautaire functies &#x200B;](/help/communities/functions.md) zijn voor gebruik slechts in het auteursmilieu.

## Vereisten {#prerequisites}

Alvorens tot een communautaire plaats te leiden, wordt het *vereist* aan:

* Zorg ervoor dat een of meer Publish-exemplaren worden uitgevoerd.
* Laat de [&#x200B; tunneldienst &#x200B;](/help/communities/deploy-communities.md#tunnel-service-on-author) toe om leden en lidgroepen te beheren.
* Identificeer de [&#x200B; primaire uitgever &#x200B;](/help/communities/deploy-communities.md#primary-publisher).
* [&#x200B; vorm replicatie &#x200B;](/help/communities/deploy-communities.md#replication-agents-on-author) wanneer de primaire uitgevershaven niet het gebrek (4503) is.

De beste praktijken, om ervoor te zorgen de plaats bereid is om vele eigenschappen te steunen, moeten de volgende stappen nemen:

* Installeer het [&#x200B; recentste eigenschappak &#x200B;](/help/communities/deploy-communities.md#latestfeaturepack).
* Laat [&#x200B; Adobe Analytics &#x200B;](/help/communities/analytics.md) voor AEM Communities toe.
* Vorm [&#x200B; email &#x200B;](/help/communities/email.md)
* Identificeer [&#x200B; Communautaire Beheerders &#x200B;](/help/communities/users.md#creating-community-members).
* [&#x200B; laat de manager van de UAuth &#x200B;](/help/communities/social-login.md#adobe-granite-oauth-authentication-handler) voor sociale login toe.

## Toegang tot de console met sites van Gemeenschappen {#accessing-communities-sites-console}

In het auteursmilieu, om de console van de Plaatsen van Gemeenschappen te bereiken:

* Vanuit globale navigatie: **[!UICONTROL Communities]** > **[!UICONTROL Sites]**

De console van de Plaatsen van Gemeenschappen toont om het even welke bestaande communautaire plaatsen. Vanuit deze console kunnen gemeenschapssites worden gemaakt, bewerkt, beheerd en verwijderd.

Om een communautaire plaats tot stand te brengen, selecteer **creeer** pictogram.

Als u een bestaande communitysite wilt openen voor het ontwerpen, wijzigen, publiceren, exporteren of toevoegen van een geneste groep, selecteert u het mappictogram van de site.

## Site maken {#site-creation}

De console van de plaatsverwezenlijking verstrekt een geleidelijke benadering om eigenschappen van de plaats samen te stellen die op een geselecteerd [&#x200B; malplaatje van de communautaire plaats &#x200B;](/help/communities/sites.md) en montages wordt gebaseerd.

Elke gemaakte site bevat een aanmeldingsfunctie omdat bezoekers van de site zich moeten aanmelden voordat ze inhoud kunnen posten, berichten kunnen verzenden of aan een groep kunnen deelnemen. Andere functies zijn gebruikersprofielen, berichten, meldingen, sitemenu, zoeken, thema&#39;s en branding.

Het proces wordt gestart door op de knop `Create` boven aan de console Communitysites te klikken.

Het ontwerpproces is een reeks stappen die als deelvensters worden gepresenteerd met een set functies die moeten worden geconfigureerd (weergegeven als subdeelvensters). Het is mogelijk om zich aan de **Volgende** stap of **terug** naar de vorige stap vooruit te bewegen alvorens de plaats in de definitieve stap vast te leggen.

### Stap 1: Sjabloon van site {#step-site-template}

![&#x200B; newsitetemplate &#x200B;](assets/newsitetemplate.png)

In het deelvenster Sjabloon site worden de volgende waarden opgegeven: Titel, Beschrijving, Hoofdmap, Basistaal, Naam en Sjabloon van site:

* **Titel van de Communautaire Plaats**

  Een weergavetitel voor de site.

  De titel wordt weergegeven op de gepubliceerde site en in de interface voor sitebeheer.

* **Beschrijving van de Communautaire Plaats**

  Een beschrijving van de site.

  De beschrijving wordt niet weergegeven op de gepubliceerde site.

* **Hoofdmap van de Communautaire Plaats**

  Het hoofdpad naar de site.

  De standaardhoofdmap is `/content/sites` , maar de hoofdmap kan naar een willekeurige locatie op de website worden verplaatst.

* **Communautaire Taal van de Basis van de Plaats**

  (Ongewijzigd laten voor één taal: Engels) Gebruik het keuzemenu om een *of meer* basistalen te kiezen uit de beschikbare talen: Duits, Italiaans, Frans, Japans, Spaans, Portugees (Brazilië), Chinees (Traditioneel) en Chinees (Vereenvoudigd). Één communautaire plaats wordt gecreeerd voor elke toegevoegde taal, en bestaat binnen de zelfde plaatsomslag na de beste praktijken die in [&#x200B; worden beschreven Vertaalend Inhoud voor Meertalige Plaatsen &#x200B;](/help/sites-administering/translation.md). De hoofdpagina van elke site bevat een onderliggende pagina die wordt genoemd door de taalcode van een van de geselecteerde talen, zoals &#39;en&#39; voor Engels of &#39;fr&#39; voor Frans.

* **Naam van de Communautaire Plaats**:

  De naam van de hoofdpagina van de site die in de URL wordt weergegeven.

   * Controleer de naam nogmaals omdat deze na het maken van de site niet gemakkelijk kan worden gewijzigd.
   * De basis-URL ( `https://server:port/site root/site name)` ) wordt onder de `Community Site Name` weergegeven.

   * Voeg voor een geldige URL een basistaalcode + &quot;.html&quot; toe

     *bijvoorbeeld*, `https://localhost:4502/content/sites/mysight/en.html`

* **Communautair Sjabloon van de Plaats** menu

  Gebruik het pull down menu om een beschikbaar [&#x200B; malplaatje van de communautaire plaats &#x200B;](/help/communities/tools.md) te kiezen.

* Selecteer **daarna**.

### Stap 2: Ontwerp {#step-design}

Het deelvenster Ontwerp bevat twee subdeelvensters voor het selecteren van het thema en de brandbanner:

#### COMMUNAUTAIR SITE-THEMA {#community-site-theme}

![&#x200B; plaatsthema &#x200B;](assets/sitetheme.png)

Het framework gebruikt `Twitter Bootstrap` om een responsief, flexibel ontwerp naar de site te brengen. Een van de vele vooraf geladen thema&#39;s van de Bootstrap kan worden geselecteerd om het geselecteerde malplaatje van de communautaire plaats te stileren, of een thema van de Bootstrap kan worden geupload.

Als deze optie is geselecteerd, wordt het thema bedekt met een ondoorzichtig blauw vinkje.

Nadat de communautaire plaats wordt gepubliceerd, is het mogelijk om [&#x200B; de eigenschappen &#x200B;](#modifying-site-properties) uit te geven en een verschillend thema te selecteren.

#### COMMUNAUTAIRE SITOBRANDING {#community-site-branding}

![&#x200B; plaats-branding &#x200B;](assets/site-branding.png)

De branding van de communautaire plaats is een beeld dat als kopbal over de bovenkant van elke pagina wordt getoond.

Het formaat van de afbeelding moet zo breed zijn als de verwachte weergave van de pagina in de browser en 120 pixels hoog.

Houd rekening met het volgende wanneer u een afbeelding maakt of selecteert:

* De afbeeldingshoogte wordt uitgesneden tot 120 pixels, gemeten vanaf de bovenrand van de afbeelding.
* De afbeelding is vastgezet aan de linkerrand van het browservenster.
* De afbeelding wordt niet vergroot of verkleind, zodat de afbeeldingsbreedte..

   * Bij een lagere breedte dan de breedte van de browser wordt de afbeelding horizontaal herhaald.
   * Meer dan de breedte van de browser, lijkt de afbeelding te zijn uitgesneden.

* Selecteer **daarna**.

### Stap 3: Instellingen {#step-settings}

Het deelvenster Instellingen bevat verschillende subdeelvensters met functies die moeten worden geconfigureerd voordat de laatste stap wordt uitgevoerd om de site te maken.

* [GEBRUIKERSBEHEER](#user-management)
* [TAGS](#tagging)
* [ROLES](#roles)
* [MODERING](#moderation)
* [ANALYTICA](#analytics)
* [VERTALING](#translation)

>[!NOTE]
>
>**laat de Dienst van de Tunnel** toe
>
>Verscheidene van subpanels van Montages staan toewijzing van een vertrouwd lid aan gematigde UGC toe, leiden groepen, of zijn contacten voor inschrijvingsmiddelen in het publicatiemilieu.
>
>De overeenkomst is voor publiceren-kant [&#x200B; gebruikers en gebruikersgroepen &#x200B;](/help/communities/users.md) (leden en lidgroepen) om niet in het auteursmilieu worden gedupliceerd.
>
>Zo is het bij het maken van de gemeenschapssite in de auteursomgeving en het toewijzen van vertrouwde leden aan verschillende rollen noodzakelijk om lidgegevens op te halen uit de publicatieomgeving.
>
>Dit wordt verwezenlijkt door ` [AEM Communities Publish Tunnel Service](/help/communities/deploy-communities.md#tunnel-service-on-author)` voor het auteursmilieu toe te laten.

#### GEBRUIKERSBEHEER {#user-management}

![&#x200B; createsitesettings &#x200B;](assets/createsitesettings.png)

* **staat de Registratie van de Gebruiker** toe

  Als deze optie ingeschakeld is, kunnen bezoekers van de site leden van de community worden via zelfregistratie.
Als ongecontroleerd, is de communautaire plaats *beperkt* en de bezoekers van de plaats moeten aan de de ledengroep van de communautaire plaats worden toegewezen, een verzoek indienen, of een uitnodiging per e-mail worden verzonden. Als deze optie uitgeschakeld is, mag anonieme toegang niet worden toegestaan.
Uncheck voor a *privé* communautaire plaats. Standaard is ingeschakeld.

* **staat Anonieme Toegang** toe

  Als gecontroleerd, is de communautaire plaats open *en om het even welke plaatsbezoeker kan tot de plaats toegang hebben.*
Als deze optie is uitgeschakeld, hebben alleen leden met een aanmelding toegang tot de site.
Uncheck voor a *privé* communautaire plaats. Standaard is ingeschakeld.

* **toestaan Overseinen**

  Als deze optie is ingeschakeld, kunnen leden berichten naar elkaar en naar de groep binnen de site van de community verzenden.
Als niet gecontroleerd, is het overseinen niet opstelling voor de gemeenschap.
De optie Standaard is uitgeschakeld.

* **staat Sociale Logins toe: Facebook**

  Als deze optie is ingeschakeld, kunnen sitebezoekers zich aanmelden met hun Facebook-accountgegevens. De geselecteerde [&#x200B; de wolkenconfiguratie van Facebook &#x200B;](/help/communities/social-login.md#create-a-facebook-connect-cloud-service) zou moeten worden gevormd om gebruikers aan de de ledengroep van de communautaire plaats toe te voegen zodra de communautaire plaats wordt gecreeerd.
Als deze optie uitgeschakeld is, wordt geen Facebook-aanmelding weergegeven.
Laat ongecontroleerd voor a *privé* communautaire plaats. De optie Standaard is uitgeschakeld.

* **staat Sociale Logins toe: Twitter**

  Als deze optie is ingeschakeld, kunnen sitebezoekers zich aanmelden met hun gegevens voor de Twitter-account. De geselecteerde [&#x200B; wolkenconfiguratie van de Twitter &#x200B;](/help/communities/social-login.md#create-a-twitter-connect-cloud-service) zou moeten worden gevormd om gebruikers aan de de ledengroep van de communautaire plaats toe te voegen zodra de communautaire plaats wordt gecreeerd.
Als deze optie uitgeschakeld is, wordt er geen aanmeldingsnaam voor de Twitter weergegeven.
Laat ongecontroleerd voor a *privé* communautaire plaats. De optie Standaard is uitgeschakeld.

>[!NOTE]
>
>**Toestaand Sociale Logins**
>
>Terwijl de configuraties van de steekproefFacebook en van de Twitter kunnen bestaan en verkiesbaar voor a [&#x200B; productiemilieu &#x200B;](/help/sites-administering/production-ready.md) zijn, is het noodzakelijk om douaneFacebook en Twitter toepassingen tot stand te brengen. Zie [&#x200B; Sociale Login met Facebook en Twitter &#x200B;](/help/communities/social-login.md).

#### TAGS {#tagging}

![&#x200B; plaats-etiketterend &#x200B;](assets/site-tagging.png)

Tags-die op communautaire inhoud-kunnen worden toegepast worden gecontroleerd door de Namespaces van de Markering te selecteren die eerder door de [&#x200B; Tagende Console &#x200B;](/help/sites-administering/tags.md#tagging-console) worden bepaald.

Bovendien beperkt het selecteren van tagnaamruimten voor de site van de community de weergegeven selectie bij het definiëren van catalogi en bronnen.

* tekstzoekvak: typ tags die op de site mogen worden gebruikt.

#### ROLES {#roles}

![&#x200B; Communautaire rollen &#x200B;](assets/site-admin-2.png)

De [&#x200B; rollen van communautaire leden &#x200B;](/help/communities/users.md) worden toegewezen met deze montages.

Het zoeken naar leden van een community is eenvoudig met &#39;type-ahead&#39;-zoekopdracht.

* **Communautaire Managers**

  Begin te typen om een of meer leden van de gemeenschap of leden te selecteren die leden van de gemeenschap en leden kunnen beheren.

* **Communautaire Moderatoren**

  Begin te typen om één of meerdere leden van de gemeenschap of lidgroepen te selecteren die als moderators van user-generated inhoud moeten worden vertrouwd.

* **Gemeenschap Bevoorrechte Leden**

  Begin het typen om één of meerdere communautaire leden of lidgroepen te selecteren die de capaciteit moeten worden gegeven om inhoud tot stand te brengen wanneer `Allow Privileged Member` voor a [&#x200B; communautaire functie &#x200B;](/help/communities/functions.md) is geselecteerd.

* **Communautaire Admins**

  Begin te typen om één of meerdere plaatsbeheerders te selecteren die de plaatsstructuur onafhankelijk van andere plaatsbeheerders en de standaardcommunautaire beheerder kunnen behandelen. Zij kunnen groepen op om het even welk niveau van de hiërarchie tot stand brengen, en de standaardbeheerder van de genestelde groepen worden (maar zij kunnen later uit de adminrol van genestelde groepen worden verwijderd).

#### MODERING {#moderation}

![&#x200B; plaats-moderatie &#x200B;](assets/site-moderation.png)

De globale instelling voor het modereren van door de gebruiker gegenereerde inhoud (UGC) wordt door deze instellingen beheerd. Individuele componenten hebben extra montages om matiging te controleren.

* **de Inhoud wordt vooraf gematigd**

  Als deze optie is ingeschakeld, wordt de geposte community-inhoud pas weergegeven nadat deze is goedgekeurd door een moderator. De optie Standaard is uitgeschakeld. Voor meer informatie, zie [&#x200B; Modererend Communautaire Inhoud &#x200B;](/help/communities/moderate-ugc.md#premoderation).

* **het Vlaggen drempel alvorens de inhoud wordt verborgen**

  Als de waarde groter is dan 0, moet het aantal keren dat een onderwerp of bericht moet worden gemarkeerd voordat het wordt verborgen in de openbare weergave. Indien ingesteld op -1, wordt het gemarkeerde onderwerp of de post nooit verborgen voor de openbare weergave. De standaardwaarde is 5.

#### ANALYTICA {#analytics}

![&#x200B; plaats-analytics &#x200B;](assets/site-analytics.png)

* **laat Analytics** toe

  Slechts beschikbaar wanneer Adobe Analytics [&#128279;](/help/communities/analytics.md) voor de eigenschappen van Gemeenschappen is gevormd.
De optie Standaard is uitgeschakeld. Als deze optie is ingeschakeld, wordt een extra selectiemenu weergegeven:

![&#x200B; plaats-analytics-toelaat &#x200B;](assets/site-analytics-enable.png)

* **Verwijzing van het Kader van Config van de Wolk**

  Selecteer in het keuzemenu het Analytics Cloud-serviceframework dat voor deze communitysite is geconfigureerd.
  `Communities` is het kadervoorbeeld van [&#x200B; Configuratie Analytics voor de documentatie van de Eigenschappen van Gemeenschappen &#x200B;](/help/communities/analytics.md#aem-analytics-framework-configuration).

#### VERTALING {#translation}

![&#x200B; plaats-vertaling &#x200B;](assets/site-translation.png)

* **staat de Vertaling van de Machine toe**

  Als deze optie is ingeschakeld (de standaardinstelling is uitgeschakeld), wordt automatische omzetting ingeschakeld voor UGC binnen de site. Dit heeft geen invloed op andere inhoud, zoals pagina-inhoud, zelfs niet als de site is ingesteld als een meertalige site. Zie [&#x200B; Vertaal Gebruiker-Gegenereerde Inhoud &#x200B;](/help/communities/translate-ugc.md) voor informatie bij het vormen van een vergunning gegeven vertaaldienst voor AEM Communities. Zie [&#x200B; Vertaal Inhoud voor Meertalige Plaatsen &#x200B;](/help/sites-administering/translation.md) voor een volledig overzicht.

![&#x200B; toestaan-machine-vertaling &#x200B;](assets/allow-machine-translation.png)

* **laat de Vertaling van de Machine voor geselecteerde talen** toe

  De talen die voor machinevertaling gebrek aan het systeem worden toegelaten dat door de [&#x200B; configuratie van de vertaalintegratie &#x200B;](/help/communities/translate-ugc.md#translation-integration-configuration) wordt gespecificeerd. Deze standaardinstellingen kunnen voor deze site worden overschreven door standaardinstellingen te verwijderen en/of andere talen te selecteren in het keuzemenu.

* **kies een vertaalleverancier**

  Standaard is het servicebureau een testservice die `microsoft` alleen voor demonstraties gebruikt. Als geen vertaaldienstverlener vergunning heeft, **zou de Vertaling van de Machine** moeten worden ongecontroleerd.

* **kies een globale gedeelde opslag**

  Voor een website met veelvoudige taalexemplaren, verstrekt een globale gedeelde opslag één enkele draad van gesprek, zichtbaar van elke taalexemplaar. Dit wordt bereikt door een van de talen te selecteren die als een taalkopie worden opgenomen. Het gebrek is *geen Globale Gedeelde Opslag*.

* **kies de config van de vertaalleverancier**

  Kies het kader van de a [&#x200B; vertaalintegratie &#x200B;](/help/sites-administering/tc-tic.md) dat voor de vergunning gegeven vertaalleverancier wordt gecreeerd.

* **selecteer de vertaalopties voor uw communautaire plaats**

   * **vertaal volledige pagina**

     Als deze optie is geselecteerd, wordt alle UGC op een pagina vertaald in de basistaal van de pagina.

     Het gebrek is *niet geselecteerd*.

   * **zet slechts selectie** om

     Als deze optie is geselecteerd, wordt naast elke advertentie een vertaaloptie weergegeven waarmee afzonderlijke posts kunnen worden vertaald in de basistaal van de pagina.
Het gebrek is *geselecteerd*.

* **Uitgezochte Persistence Opties**

   * **vertaalt bijdragen op gebruikersverzoek en blijft na**
Als deze optie is geselecteerd, wordt de inhoud pas omgezet wanneer een aanvraag wordt ingediend. Nadat de vertaling is vertaald, wordt de vertaling opgeslagen in de opslagplaats.

     Het gebrek is *niet geselecteerd*.

   * **presteert geen vertalingen**

     Indien geselecteerd, worden de vertalingen niet opgeslagen in de bewaarplaats.

     Als deze optie niet is geselecteerd, blijven de vertalingen behouden.

     Het gebrek is *niet geselecteerd*.

* **Slimme Render**

  Selecteer een van de volgende opties:

   * `Always show contributions in the original language` (standaardwaarde)
   * `Always show contributions in user preferred language`
   * `Show contributions in user preferred language for only logged-in users`

### Stap 4: Create Communities Site {#step-create-communities-site}

Als om het even welke aanpassingen nodig zijn, gebruik de **Achtergrond** knoop om hen te maken.

Zodra **creeer** wordt geselecteerd en begonnen, kan het proces om de plaats tot stand te brengen niet worden onderbroken.

Nadat de site is gemaakt:

* Het wijzigen van de URL (knooppuntnaam) wordt niet ondersteund.
* De toekomstige veranderingen in het malplaatje van de communautaire plaats beïnvloeden niet de gecreeerde communautaire plaats.
* Het onbruikbaar maken van het malplaatje van de communautaire plaats beïnvloedt niet de gecreeerde communautaire plaats.
* Het is mogelijk om de [&#x200B; STRUCTUUR &#x200B;](#modify-structure) van een communautaire plaats uit te geven door zijn eigenschappen te wijzigen.

![&#x200B; creeer-plaats &#x200B;](assets/create-site1.png)

Wanneer het proces is voltooid, wordt de map voor de nieuwe site weergegeven in de console Communitysites, waar auteurs pagina-inhoud kunnen toevoegen of kunnen beheerders de eigenschappen van de site wijzigen.

![&#x200B; wijzigen-plaats-bezit &#x200B;](assets/modify-site-property.png)

Als u een communitysite wilt bewerken, selecteert u de projectmap om deze te openen:

![&#x200B; plaats-project &#x200B;](assets/site-project.png)

Wanneer u de muisaanwijzer op een site plaatst of een sitekaart aanraakt, worden pictogrammen weergegeven die het volgende mogelijk maken:

* [de site bewerken in de ontwerpmodus](#authoring-site-content)
* [site-eigenschappen openen om te wijzigen](#modifying-site-properties)
* [publiceren, de site](#publishing-the-site)
* [site exporteren](#exporting-the-site)
* [site verwijderen](#deleting-the-site)

## Site-inhoud ontwerpen {#authoring-site-content}

De inhoud van een site kan met dezelfde gereedschappen worden gemaakt als elke andere AEM website. Als u de site wilt openen om deze te ontwerpen, selecteert u het pictogram `Open Site` dat wordt weergegeven wanneer u de muis op de site plaatst. De site wordt op een nieuw tabblad geopend, zodat de console Communitysites toegankelijk blijft.

![&#x200B; plaats-inhoud &#x200B;](assets/site-content.png)

>[!NOTE]
>
>Als niet vertrouwd met AEM, bekijk de documentatie over [&#x200B; basisbehandeling &#x200B;](/help/sites-authoring/basic-handling.md) en a [&#x200B; snelle gids aan auteurspagina&#39;s &#x200B;](/help/sites-authoring/qg-page-authoring.md).

## Site-eigenschappen wijzigen {#modifying-site-properties}

![&#x200B; geef-plaats uit &#x200B;](assets/edit-site.png)

De eigenschappen van een bestaande plaats, die tijdens het proces van de plaatsverwezenlijking wordt gespecificeerd, kan worden gewijzigd door het `Edit Site` pictogram te selecteren dat bij het bewegen van de plaats met muis verschijnt.

`Details of the following properties match the descriptions provided in the` [&#x200B; sectie van de Verwezenlijking van de Plaats &#x200B;](#site-creation).

![&#x200B; wijzigen-plaats-grondbeginselen &#x200B;](assets/modify-site-basicinfo.png)

### Basis wijzigen {#modify-basic}

In het BASIC-deelvenster kunt u de volgende wijzigingen aanbrengen:

* Titel van gemeenschapssite
* Beschrijving van community-site

De naam van de communautaire site mag niet worden gewijzigd.

Het kiezen van een verschillend malplaatje van de communautaire plaats zou geen effect op een bestaande communautaire plaats hebben aangezien geen verbinding tussen malplaatjes en plaatsen blijft.

In plaats daarvan, kan de [&#x200B; STRUCTUUR &#x200B;](#modify-structure) van de communautaire plaats worden gewijzigd.

### Structuur wijzigen {#modify-structure}

In het deelvenster STRUCTUUR kunt u de structuur wijzigen die oorspronkelijk is gemaakt op basis van de geselecteerde communitysitesjabloon. Vanuit het deelvenster kunt u het volgende doen:

* De belemmering-en-daling extra [&#x200B; communautaire functies &#x200B;](/help/communities/functions.md) in de plaatsstructuur.
* Bij een instantie van een communautaire functie in de sitestructuur:

   * **`gear icon`**

     Geef montages, met inbegrip van de vertoningstitel en naam URL, en [&#x200B; bevoorrechte ledengroepen &#x200B;](/help/communities/users.md#privilegedmembersgroups) uit.

   * **`trashcan icon`**

     Verwijder (verwijder) functies uit de sitestructuur.

   * **`grid icon`**

     Wijzig de volgorde van de functies die wordt weergegeven in de navigatiebalk op het hoogste niveau van de site.

>[!NOTE]
>
>U kunt de volgorde van alle functies in de sitestructuur wijzigen, behalve van de functie bovenaan. Daarom kan de homepage van een communautaire plaats niet worden veranderd.

>[!CAUTION]
>
>* Hoewel de titel van de weergave zonder bijwerkingen kan worden gewijzigd, wordt het niet aanbevolen de URL-naam te bewerken van een communautaire functie die bij een communautaire site hoort.
>
>Als u bijvoorbeeld de naam van de URL wijzigt, wordt de bestaande UGC niet verplaatst, waardoor de UGC &#39;verloren&#39; gaat.

>[!CAUTION]
>
>De groepsfunctie moet ** niet *eerst of de enige* functie in de plaatsstructuur zijn.
>
>Om het even welke andere functie, zoals de [&#x200B; paginafunctie &#x200B;](/help/communities/functions.md#page-function), moet worden omvat en eerst vermeld.

#### Voorbeeld: een catalogusfunctie toevoegen aan een community-sitestructuur {#example-adding-a-catalog-function-to-a-community-site-structure}

![&#x200B; toe:voegen-catalogus-plaats &#x200B;](assets/add-catalog-site.png)

### Ontwerp wijzigen {#modify-design}

In het deelvenster ONTWERP kunt u een nieuw thema toepassen:

* [Thema van communautaire site](#community-site-theme)
* [Gemeenschapsmerk](#community-site-branding)

   * Blader naar de onderkant van het deelvenster, zodat u de afbeelding van het merk kunt wijzigen.

### Instellingen wijzigen {#modify-settings}

In het deelvenster INSTELLINGEN hebt u toegang tot de meeste instellingen onder de subdeelvensters van Stap 3 van het maken van de gemeenschapssite:

* [Gebruikersbeheer](#user-management)
* [Tags](#tagging)
* [Moderatie](#moderation)
* [Lidrollen](#roles)
* [Analyse](#analytics)
* [Vertaling](#translation)

### Miniatuur wijzigen {#modify-thumbnail}

In het deelvenster MINIATUUR kunt u een afbeelding uploaden om de site in de console Sites van Gemeenschappen weer te geven.

## De site publiceren {#publishing-the-site}

Nadat een communitysite net is gemaakt of gewijzigd, is het mogelijk om de site te publiceren (activeren) door het pictogram `Publish Site` te selecteren dat wordt weergegeven wanneer u de muisaanwijzer op de site plaatst.

![&#x200B; publiceren-plaats &#x200B;](assets/publish-site.png)

Er is een indicatie nadat de site is gepubliceerd.

![&#x200B; plaats-gepubliceerde &#x200B;](assets/site-published.png)

### Publiceren met geneste groepen {#publishing-with-nested-groups}

Na het publiceren van een communautaire plaats, is het noodzakelijk om elke subcommunity (genestelde groep) individueel te publiceren die gebruikend de [&#x200B; console van Groepen &#x200B;](/help/communities/groups.md) wordt gecreeerd.

## De site exporteren {#exporting-the-site}

![&#x200B; export-plaats &#x200B;](assets/export-site.png)

Selecteer het uitvoerpictogram, op muiswijzer over de plaats, zodat kunt u een pakket van de communautaire plaats tot stand brengen die zowel in de [&#x200B; Manager van het Pakket &#x200B;](/help/sites-administering/package-manager.md) wordt opgeslagen en gedownload.

UGC is niet opgenomen in het sitepakket.

## De site verwijderen {#deleting-the-site}

![&#x200B; deleteicon &#x200B;](assets/deleteicon.png)

Als u de communitysite wilt verwijderen, selecteert u het pictogram Site verwijderen dat verschijnt wanneer u de muisaanwijzer op de site in de Community Site Console plaatst. Deze actie verwijdert alle punten verbonden aan de plaats, zoals UGC, gebruikersgroepen, activa, en gegevensbestandverslagen.

## Gemaakte gebruikersgroepen {#created-community-user-groups}

Zodra de nieuwe communautaire plaats wordt gepubliceerd, worden de nieuwe lidgroepen (gebruikersgroepen worden gecreeerd in publicatiemilieu) die de aangewezen toestemmingen hebben die voor diverse administratieve en lidrollen worden geplaatst.

De naam die voor de lidgroepen wordt gecreeerd omvat *plaats-naam* die in [&#x200B; Stap 1 &#x200B;](#step13asitetemplate) wordt gegeven (de naam die in URL verschijnt). Het omvat ook een unieke identiteitskaart om conflicten met communautaire plaatsen en groepen te vermijden die de plaats-naam voor verschillende communautaire plaatwortels hebben.

Als de naam bijvoorbeeld &quot;enter&quot; was voor een site met de naam &quot;Getting Started Tutorial&quot;, zou de gebruikersgroep voor moderatoren het volgende zijn:

* titel: Moderatoren van de communautaire vakkennis
* naam: community-*in werking stellen-uid* - moderators

Om het even welke leden toegewezen rollen als moderatoren of groepsbeheerders terwijl het creëren van de plaats, worden toegewezen aan de aangewezen groep en aan de ledengroep toegewezen. Deze groepen en lidtoewijzingen worden gemaakt bij publicatie wanneer de nieuwe site wordt gepubliceerd.

Voor details, zie [&#x200B; het Leiden Gebruikers en de Groepen van de Gebruiker &#x200B;](/help/communities/users.md).

>[!NOTE]
>
>Als [&#x200B; sociale Login toestaat: Facebook &#x200B;](#user-management) wordt toegelaten, zodra de gebruikersgroep `community-<site-name>-<uid>-members`
>wordt gecreeerd, zou de toegepaste [&#x200B; de wolkendienst van Facebook &#x200B;](/help/communities/social-login.md#createafacebookcloudservice) moeten worden gevormd om gebruikers aan deze groep toe te voegen.

## Configureren voor verificatiefout {#configure-for-authentication-error}

Standaard wordt een communautaire site omgeleid naar een voorbeeld van een aanmeldingspagina wanneer de gebruiker de verkeerde gegevens invoert en zich niet kan aanmelden. Deze steekproeflogin is niet aanwezig op de server van de a [&#x200B; productie &#x200B;](/help/sites-administering/production-ready.md).

Om correct om te leiden, zodra een plaats is gevormd en ertoe aangezet om te publiceren, voltooi deze stappen om authentificatiemislukking te krijgen om aan de communautaire plaats om te leiden:

* Op elke AEM-publicatie-instantie.
* Meld u aan met beheerdersrechten.
* Heb toegang tot de [&#x200B; Console van het Web &#x200B;](/help/sites-deploying/configuring-osgi.md).

   * Bijvoorbeeld, [&#x200B; https://localhost:4503/system/console/configMgr &#x200B;](https://localhost:4503/system/console/configMgr).

* Zoek `Adobe Granite Login Selector Authentication Handler` .
* Selecteer het pictogram `pencil` zodat u de configuratie voor bewerking kunt openen.
* Ga de Toewijzingen van de Pagina van de a **Login** als volgt in:

  `/content/sites/<site-name>/path/to/login/page:/content/sites/<site-name>`

  Bijvoorbeeld:
  `/content/sites/engage/en/signin:/content/sites/engage/en`

* Selecteer **sparen**.

![&#x200B; auth-error &#x200B;](assets/auth-error.png)

### Omleiding van verificatie testen {#test-authentication-redirection}

Op zelfde AEM publiceer instantie die met een login paginaplaat voor de communautaire plaats wordt gevormd:

* Blader naar de homepage van de website van de community.

   * Bijvoorbeeld, [&#x200B; https://localhost:4503/content/sites/engage/en.html](https://localhost:4503/content/sites/engage/en.html)

* Selecteer Afmelden.
* Selecteer Aanmelden.
* Voer onjuiste gegevens in, zoals gebruikersnaam &quot;x&quot; en wachtwoord &quot;x&quot;.
* De aanmeldingspagina moet worden weergegeven met de fout &quot;Ongeldige aanmelding&quot;.

![&#x200B; test-authentificatie &#x200B;](assets/test-authentication.png)

## Toegang tot communitysites vanuit de hoofdsiteconsole {#accessing-community-sites-from-main-sites-console}

Vanuit de algemene console voor navigatiesites bevinden communitysites zich in de map `Community Sites` .

Terwijl het mogelijk is om tot een communautaire plaats op deze manier, voor administratieve taken toegang te hebben, zou de communautaire plaats van de console van de Plaatsen van Gemeenschappen moeten worden betreden.

![&#x200B; toegang-plaats &#x200B;](assets/access-site.png)
