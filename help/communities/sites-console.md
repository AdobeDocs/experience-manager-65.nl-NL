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
* [Geneste groepen maken en bewerken](/help/communities/groups.md) (subgemeenschappen)

Zie [Aan de slag met AEM Communities](/help/communities/getting-started.md) waar u kunt ervaren hoe snel een communautaire plaats in het auteursmilieu kan worden gecreeerd, en hoe te om communautaire groepen van de auteur tot stand te brengen en milieu&#39;s te publiceren.

>[!NOTE]
>
>De belangrijkste menu&#39;s van de Gemeenschappen voor de oprichting van [communitysites](/help/communities/sites-console.md), [communitysjablonen](/help/communities/sites.md), [communitygroepsjablonen](/help/communities/tools-groups.md), en [communautaire functies](/help/communities/functions.md) zijn alleen bestemd voor gebruik in de ontwerpomgeving.

## Vereisten {#prerequisites}

Voordat u een communitysite maakt, moet u *vereist* tot:

* Zorg ervoor dat een of meer publicatie-exemplaren actief zijn.
* De optie [tunneldienst](/help/communities/deploy-communities.md#tunnel-service-on-author) leden en leden te beheren.
* Identificeer [primaire uitgever](/help/communities/deploy-communities.md#primary-publisher).
* [Replicatie configureren](/help/communities/deploy-communities.md#replication-agents-on-author) als de primaire uitgevershoort niet het gebrek is (4503).

De beste praktijken, om ervoor te zorgen de plaats bereid is om vele eigenschappen te steunen, moeten de volgende stappen nemen:

* Installeer de [nieuwste functiepakket](/help/communities/deploy-communities.md#latestfeaturepack).
* Inschakelen [Adobe Analytics](/help/communities/analytics.md) voor AEM Communities.
* Configureren [email](/help/communities/email.md)
* Identificeren [Community-beheerders](/help/communities/users.md#creating-community-members).
* [De handler OAuth inschakelen](/help/communities/social-login.md#adobe-granite-oauth-authentication-handler) voor aanmelden bij een sociaal netwerk.

## Toegang tot de console met sites van Gemeenschappen {#accessing-communities-sites-console}

In het auteursmilieu, om de console van de Plaatsen van Gemeenschappen te bereiken:

* Vanuit globale navigatie: **[!UICONTROL Communities]** > **[!UICONTROL Sites]**

De console van de Plaatsen van Gemeenschappen toont om het even welke bestaande communautaire plaatsen. Vanuit deze console kunnen gemeenschapssites worden gemaakt, bewerkt, beheerd en verwijderd.

Als u een communitysite wilt maken, selecteert u de optie **Maken** pictogram.

Als u een bestaande communitysite wilt openen voor het ontwerpen, wijzigen, publiceren, exporteren of toevoegen van een geneste groep, selecteert u het mappictogram van de site.

## Site maken {#site-creation}

De console van de plaatsverwezenlijking verstrekt een geleidelijke benadering om eigenschappen van de plaats samen te stellen die op een geselecteerde wordt gebaseerd [sjabloon voor community-site](/help/communities/sites.md) en instellingen.

Elke gemaakte site bevat een aanmeldingsfunctie omdat bezoekers van de site zich moeten aanmelden voordat ze inhoud kunnen posten, berichten kunnen verzenden of aan een groep kunnen deelnemen. Andere functies zijn gebruikersprofielen, berichten, meldingen, sitemenu, zoeken, thema&#39;s en branding.

Het proces wordt gestart door de `Create` boven aan de console Communitysites.

Het ontwerpproces is een reeks stappen die als deelvensters worden gepresenteerd met een set functies die moeten worden geconfigureerd (weergegeven als subdeelvensters). Het is mogelijk verder te gaan naar de **Volgende** stap of **Vorige** naar de vorige stap voordat u de site in de laatste stap toewijst.

### Stap 1: Sjabloon van site {#step-site-template}

![nieuwssite](assets/newsitetemplate.png)

In het deelvenster Sjabloon site worden de volgende waarden opgegeven: Titel, Beschrijving, Hoofdmap, Basistaal, Naam en Sjabloon van site:

* **Titel van gemeenschapssite**

  Een weergavetitel voor de site.

  De titel wordt weergegeven op de gepubliceerde site en in de interface voor sitebeheer.

* **Beschrijving van community-site**

  Een beschrijving van de site.

  De beschrijving wordt niet weergegeven op de gepubliceerde site.

* **Hoofdmap van gemeenschapssite**

  Het hoofdpad naar de site.

  De standaardhoofdmap is `/content/sites`, maar de hoofdmap kan naar een willekeurige locatie op de website worden verplaatst.

* **Basis van gemeenschapssite**

  (Niet gewijzigd laten voor één taal: Engels) Gebruik het keuzemenu om er een te kiezen *of meer* basistalen uit de beschikbare talen: Duits, Italiaans, Frans, Japans, Spaans, Portugees (Brazilië), Chinees (traditioneel) en Chinees (vereenvoudigd). Er wordt één communitysite gemaakt voor elke toegevoegde taal en deze bestaat in dezelfde sitemap volgens de in [Inhoud vertalen voor meertalige sites](/help/sites-administering/translation.md). De hoofdpagina van elke site bevat een onderliggende pagina die wordt genoemd door de taalcode van een van de geselecteerde talen, zoals &#39;en&#39; voor Engels of &#39;fr&#39; voor Frans.

* **Naam van communautaire site**:

  De naam van de hoofdpagina van de site die in de URL wordt weergegeven.

   * Controleer de naam nogmaals omdat deze na het maken van de site niet gemakkelijk kan worden gewijzigd.
   * De basis-URL ( `https://server:port/site root/site name)` wordt onder de `Community Site Name`.

   * Voeg voor een geldige URL een basistaalcode + &quot;.html&quot; toe

     *Bijvoorbeeld*, `https://localhost:4502/content/sites/mysight/en.html`

* **Sjabloon voor communautaire site** menu

  Kies een beschikbare optie in het keuzemenu [sjabloon voor community-site](/help/communities/tools.md).

* Selecteren **Volgende**.

### Stap 2: Ontwerp {#step-design}

Het deelvenster Ontwerp bevat twee subdeelvensters voor het selecteren van het thema en de brandbanner:

#### COMMUNAUTAIR SITE-THEMA {#community-site-theme}

![sitethema](assets/sitetheme.png)

Het kader gebruikt `Twitter Bootstrap` om een ontvankelijk, flexibel ontwerp aan de plaats te brengen. Een van de vele vooraf geladen thema&#39;s van de Bootstrap kan worden geselecteerd om het geselecteerde malplaatje van de communautaire plaats te stileren, of een thema van de Bootstrap kan worden geupload.

Als deze optie is geselecteerd, wordt het thema bedekt met een ondoorzichtig blauw vinkje.

Nadat de communitysite is gepubliceerd, is het mogelijk om [de eigenschappen bewerken](#modifying-site-properties) en selecteer een ander thema.

#### COMMUNAUTAIRE SITOBRANDING {#community-site-branding}

![branding op de site](assets/site-branding.png)

De branding van de communautaire plaats is een beeld dat als kopbal over de bovenkant van elke pagina wordt getoond.

Het formaat van de afbeelding moet zo breed zijn als de verwachte weergave van de pagina in de browser en 120 pixels hoog.

Houd rekening met het volgende wanneer u een afbeelding maakt of selecteert:

* De afbeeldingshoogte wordt uitgesneden tot 120 pixels, gemeten vanaf de bovenrand van de afbeelding.
* De afbeelding is vastgezet aan de linkerrand van het browservenster.
* De afbeelding wordt niet vergroot of verkleind, zodat de afbeeldingsbreedte..

   * Bij een lagere breedte dan de breedte van de browser wordt de afbeelding horizontaal herhaald.
   * Meer dan de breedte van de browser, lijkt de afbeelding te zijn uitgesneden.

* Selecteren **Volgende**.

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
>**Tunnelservice inschakelen**
>
>Verscheidene van subpanels van Montages staan toewijzing van een vertrouwd lid aan gematigde UGC toe, leiden groepen, of zijn contacten voor inschrijvingsmiddelen in het publicatiemilieu.
>
>De conventie is bedoeld voor publicatie [gebruikers en gebruikersgroepen](/help/communities/users.md) (leden en lidgroepen) om niet in het auteursmilieu worden gedupliceerd.
>
>Zo is het bij het maken van de gemeenschapssite in de auteursomgeving en het toewijzen van vertrouwde leden aan verschillende rollen noodzakelijk om lidgegevens op te halen uit de publicatieomgeving.
>
>Dit wordt verwezenlijkt door toe te laten ` [AEM Communities Publish Tunnel Service](/help/communities/deploy-communities.md#tunnel-service-on-author)` voor de auteursomgeving.

#### GEBRUIKERSBEHEER {#user-management}

![creaties](assets/createsitesettings.png)

* **Gebruikersregistratie toestaan**

  Als deze optie ingeschakeld is, kunnen bezoekers van de site leden van de community worden via zelfregistratie.
Als deze optie niet is ingeschakeld, wordt de site van de community *beperkt* en bezoekers van de site moeten worden toegewezen aan de groep leden van de site van de community, een aanvraag indienen of een uitnodiging per e-mail ontvangen. Als deze optie uitgeschakeld is, mag anonieme toegang niet worden toegestaan.
Uitschakelen voor een *privé* community-site. Standaard is ingeschakeld.

* **Anonieme toegang toestaan**

  Indien gecontroleerd, is de communautaire plaats *open* en elke bezoeker van de site heeft toegang tot de site.
Als deze optie is uitgeschakeld, hebben alleen leden met een aanmelding toegang tot de site.
Uitschakelen voor een *privé* community-site. Standaard is ingeschakeld.

* **Berichten toestaan**

  Als deze optie is ingeschakeld, kunnen leden berichten naar elkaar en naar de groep binnen de site van de community verzenden.
Als niet gecontroleerd, is het overseinen niet opstelling voor de gemeenschap.
De optie Standaard is uitgeschakeld.

* **Sociale aanmeldingen toestaan: Facebook**

  Als deze optie is ingeschakeld, kunnen sitebezoekers zich aanmelden met hun Facebook-accountgegevens. De geselecteerde [Facebook-cloudconfiguratie](/help/communities/social-login.md#create-a-facebook-connect-cloud-service) moeten worden gevormd om gebruikers aan de de ledengroep van de communautaire plaats toe te voegen zodra de communautaire plaats wordt gecreeerd.
Als deze optie uitgeschakeld is, wordt geen Facebook-aanmelding weergegeven.
Niet ingeschakeld laten voor een *privé* community-site. De optie Standaard is uitgeschakeld.

* **Sociale aanmeldingen toestaan: Twitter**

  Als deze optie is ingeschakeld, kunnen sitebezoekers zich aanmelden met hun gegevens voor de Twitter-account. De geselecteerde [Twitter cloudconfiguratie](/help/communities/social-login.md#create-a-twitter-connect-cloud-service) moeten worden gevormd om gebruikers aan de de ledengroep van de communautaire plaats toe te voegen zodra de communautaire plaats wordt gecreeerd.
Als deze optie uitgeschakeld is, wordt er geen aanmeldingsnaam voor de Twitter weergegeven.
Niet ingeschakeld laten voor een *privé* community-site. De optie Standaard is uitgeschakeld.

>[!NOTE]
>
>**Sociale aanmeldingen toestaan**
>
>Hoewel er voorbeelden kunnen zijn van Facebook- en Twitter-configuraties en deze kunnen kunnen worden geselecteerd voor een [productieomgeving](/help/sites-administering/production-ready.md)moet u aangepaste Facebook- en Twitter-toepassingen maken. Zie [Sociale aanmelding met Facebook en Twitter](/help/communities/social-login.md).

#### TAGS {#tagging}

![sitetags](assets/site-tagging.png)

De tags die kunnen worden toegepast op community-inhoud, worden beheerd door Tag-naamruimten te selecteren die eerder zijn gedefinieerd via het dialoogvenster [Tagingsconsole](/help/sites-administering/tags.md#tagging-console).

Bovendien beperkt het selecteren van tagnaamruimten voor de site van de community de weergegeven selectie bij het definiëren van catalogi en bronnen.

* tekstzoekvak: typ tags die op de site mogen worden gebruikt.

#### ROLES {#roles}

![Communautaire rollen](assets/site-admin-2.png)

De [rol van de leden van de gemeenschap](/help/communities/users.md) worden toegewezen met deze instellingen.

Het zoeken naar leden van een community is eenvoudig met &#39;type-ahead&#39;-zoekopdracht.

* **Community-managers**

  Begin te typen om een of meer leden van de gemeenschap of leden te selecteren die leden van de gemeenschap en leden kunnen beheren.

* **Moderatoren van de Gemeenschap**

  Begin te typen om één of meerdere leden van de gemeenschap of lidgroepen te selecteren die als moderators van user-generated inhoud moeten worden vertrouwd.

* **Geprivilegieerde leden van de Gemeenschap**

  Begin te typen om een of meer leden van de gemeenschap of lidgroepen te selecteren die de mogelijkheid moeten krijgen om inhoud te maken wanneer `Allow Privileged Member` is geselecteerd voor een [gemeenschapsfunctie](/help/communities/functions.md).

* **Community Admins**

  Begin te typen om één of meerdere plaatsbeheerders te selecteren die de plaatsstructuur onafhankelijk van andere plaatsbeheerders en de standaardcommunautaire beheerder kunnen behandelen. Zij kunnen groepen op om het even welk niveau van de hiërarchie tot stand brengen, en de standaardbeheerder van de genestelde groepen worden (maar zij kunnen later uit de adminrol van genestelde groepen worden verwijderd).

#### MODERING {#moderation}

![verruiming van de locatie](assets/site-moderation.png)

De globale instelling voor het modereren van door de gebruiker gegenereerde inhoud (UGC) wordt door deze instellingen beheerd. Individuele componenten hebben extra montages om matiging te controleren.

* **Inhoud is vooraf gemodereerd**

  Als deze optie is ingeschakeld, wordt de geposte community-inhoud pas weergegeven nadat deze is goedgekeurd door een moderator. De optie Standaard is uitgeschakeld. Zie voor meer informatie [Modernisering van communautaire inhoud](/help/communities/moderate-ugc.md#premoderation).

* **Markeringsdrempel voordat inhoud wordt verborgen**

  Als de waarde groter is dan 0, moet het aantal keren dat een onderwerp of bericht moet worden gemarkeerd voordat het wordt verborgen in de openbare weergave. Indien ingesteld op -1, wordt het gemarkeerde onderwerp of de post nooit verborgen voor de openbare weergave. De standaardwaarde is 5.

#### ANALYTICA {#analytics}

![locatieanalyse](assets/site-analytics.png)

* **Analyse inschakelen**

  Alleen beschikbaar als Adobe Analytics is [geconfigureerd](/help/communities/analytics.md) voor communautaire elementen.
De optie Standaard is uitgeschakeld. Als deze optie is ingeschakeld, wordt een extra selectiemenu weergegeven:

![voor locatieanalyse](assets/site-analytics-enable.png)

* **Verwijzing naar Cloud Config Framework**

  Selecteer in het keuzemenu het Analytics Cloud-serviceframework dat voor deze communitysite is geconfigureerd.
  `Communities` is het kadervoorbeeld van [Analytische configuratie voor functies van Gemeenschappen](/help/communities/analytics.md#aem-analytics-framework-configuration) documentatie.

#### VERTALING {#translation}

![site-vertaling](assets/site-translation.png)

* **Machinevertaling toestaan**

  Als deze optie is ingeschakeld (de standaardinstelling is uitgeschakeld), wordt automatische omzetting ingeschakeld voor UGC binnen de site. Dit heeft geen invloed op andere inhoud, zoals pagina-inhoud, zelfs niet als de site is ingesteld als een meertalige site. Zie [Door de gebruiker gegenereerde inhoud vertalen](/help/communities/translate-ugc.md) voor informatie over het configureren van een vertaalservice met licentie voor AEM Communities. Zie [Inhoud vertalen voor meertalige sites](/help/sites-administering/translation.md) voor een volledig overzicht.

![allow-machine-translatie](assets/allow-machine-translation.png)

* **Machine Translation inschakelen voor geselecteerde talen**

  De talen die zijn ingeschakeld voor machinevertaling, worden standaard ingesteld op de systeeminstelling die is opgegeven in het dialoogvenster [configuratie voor vertaalintegratie](/help/communities/translate-ugc.md#translation-integration-configuration). Deze standaardinstellingen kunnen voor deze site worden overschreven door standaardinstellingen te verwijderen en/of andere talen te selecteren in het keuzemenu.

* **Een vertaalprovider kiezen**

  Standaard is de serviceprovider een testservice met `microsoft` alleen voor demonstratie. Indien geen enkele aanbieder van vertaaldiensten een licentie heeft, **Machinevertaling toestaan** moet worden uitgeschakeld.

* **Kies een algemene gedeelde opslag**

  Voor een website met veelvoudige taalexemplaren, verstrekt een globale gedeelde opslag één enkele draad van gesprek, zichtbaar van elke taalexemplaar. Dit wordt bereikt door een van de talen te selecteren die als een taalkopie worden opgenomen. De standaardwaarde is *Geen algemene gedeelde winkel*.

* **Configuratie van vertaalprovider kiezen**

  Kies een [vertaalintegratiekader](/help/sites-administering/tc-tic.md) gemaakt voor de vertaalbureau met licentie.

* **Selecteer de vertaalopties voor uw communitysite**

   * **Gehele pagina vertalen**

     Als deze optie is geselecteerd, wordt alle UGC op een pagina vertaald in de basistaal van de pagina.

     Standaard is *niet geselecteerd*.

   * **Alleen selectie vertalen**

     Als deze optie is geselecteerd, wordt naast elke advertentie een vertaaloptie weergegeven waarmee afzonderlijke posts kunnen worden vertaald in de basistaal van de pagina.
Standaard is *geselecteerd*.

* **Persistopties selecteren**

   * **Vertaal bijdragen op verzoek van gebruiker en blijf daarna voortbestaan**
Als deze optie is geselecteerd, wordt de inhoud pas omgezet wanneer een aanvraag wordt ingediend. Nadat de vertaling is vertaald, wordt de vertaling opgeslagen in de opslagplaats.

     Standaard is *niet geselecteerd*.

   * **Geen vertalingen behouden**

     Indien geselecteerd, worden de vertalingen niet opgeslagen in de bewaarplaats.

     Als deze optie niet is geselecteerd, blijven de vertalingen behouden.

     Standaard is *niet geselecteerd*.

* **Slimme rendering**

  Selecteer een van de volgende opties:

   * `Always show contributions in the original language` (standaard)
   * `Always show contributions in user preferred language`
   * `Show contributions in user preferred language for only logged-in users`

### Stap 4: Create Communities Site {#step-create-communities-site}

Als er aanpassingen nodig zijn, gebruikt u de **Vorige** om ze te maken.

Eenmaal **Maken** is geselecteerd en gestart, kan het maken van de site niet worden onderbroken.

Nadat de site is gemaakt:

* Het wijzigen van de URL (knooppuntnaam) wordt niet ondersteund.
* De toekomstige veranderingen in het malplaatje van de communautaire plaats beïnvloeden niet de gecreeerde communautaire plaats.
* Het onbruikbaar maken van het malplaatje van de communautaire plaats beïnvloedt niet de gecreeerde communautaire plaats.
* Het is mogelijk om de [STRUCTUUR](#modify-structure) van een communautaire site door de eigenschappen ervan te wijzigen.

![site maken](assets/create-site1.png)

Wanneer het proces is voltooid, wordt de map voor de nieuwe site weergegeven in de console Communitysites, waar auteurs pagina-inhoud kunnen toevoegen of kunnen beheerders de eigenschappen van de site wijzigen.

![modify-site-property](assets/modify-site-property.png)

Als u een communitysite wilt bewerken, selecteert u de projectmap om deze te openen:

![plaatsproject](assets/site-project.png)

Wanneer u de muisaanwijzer op een site plaatst of een sitekaart aanraakt, worden pictogrammen weergegeven die het volgende mogelijk maken:

* [de site bewerken in de ontwerpmodus](#authoring-site-content)
* [site-eigenschappen openen om te wijzigen](#modifying-site-properties)
* [publiceren, de site](#publishing-the-site)
* [site exporteren](#exporting-the-site)
* [site verwijderen](#deleting-the-site)

## Site-inhoud ontwerpen {#authoring-site-content}

De inhoud van een site kan met dezelfde gereedschappen worden gemaakt als elke andere AEM website. Als u de site wilt openen voor ontwerpen, selecteert u de optie `Open Site` pictogram dat wordt weergegeven bij het aanwijzen van de site met de muis. De site wordt op een nieuw tabblad geopend, zodat de console Communitysites toegankelijk blijft.

![site-inhoud](assets/site-content.png)

>[!NOTE]
>
>Als u niet bekend bent met AEM, kunt u de documentatie raadplegen op [basisbehandeling](/help/sites-authoring/basic-handling.md) en [snelle handleiding voor het ontwerpen van pagina&#39;s](/help/sites-authoring/qg-page-authoring.md).

## Site-eigenschappen wijzigen {#modifying-site-properties}

![site bewerken](assets/edit-site.png)

De eigenschappen van een bestaande site die tijdens het maken van de site zijn opgegeven, kunnen worden gewijzigd door de optie `Edit Site`pictogram dat wordt weergegeven bij het aanwijzen van de site met de muis.

`Details of the following properties match the descriptions provided in the` [Site maken](#site-creation) sectie.

![modify-site-basicinfo](assets/modify-site-basicinfo.png)

### Basis wijzigen {#modify-basic}

In het BASIC-deelvenster kunt u de volgende wijzigingen aanbrengen:

* Titel van gemeenschapssite
* Beschrijving van community-site

De naam van de communautaire site mag niet worden gewijzigd.

Het kiezen van een verschillend malplaatje van de communautaire plaats zou geen effect op een bestaande communautaire plaats hebben aangezien geen verbinding tussen malplaatjes en plaatsen blijft.

In plaats daarvan [STRUCTUUR](#modify-structure) van het communautaire gebied kan worden gewijzigd.

### Structuur wijzigen {#modify-structure}

In het deelvenster STRUCTUUR kunt u de structuur wijzigen die oorspronkelijk is gemaakt op basis van de geselecteerde communitysitesjabloon. Vanuit het deelvenster kunt u het volgende doen:

* Aanvullende slepen en neerzetten [communautaire functies](/help/communities/functions.md) in de sitestructuur.
* Bij een instantie van een communautaire functie in de sitestructuur:

   * **`gear icon`**

     Instellingen bewerken, waaronder de titel en de URL van de weergave, en [groepen geprivilegieerde leden](/help/communities/users.md#privilegedmembersgroups).

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
>De groepfunctie moet *niet* zijn *eerst of alleen* in de sitestructuur.
>
>Elke andere functie, zoals de [page, functie](/help/communities/functions.md#page-function), moet worden opgenomen en als eerste worden vermeld.

#### Voorbeeld: een catalogusfunctie toevoegen aan een community-sitestructuur {#example-adding-a-catalog-function-to-a-community-site-structure}

![add-catalog-site](assets/add-catalog-site.png)

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

Nadat een communitysite pas is gemaakt of gewijzigd, is het mogelijk om de site te publiceren (activeren) door de `Publish Site` pictogram dat wordt weergegeven wanneer de muisaanwijzer op de site wordt geplaatst.

![publicatiesite](assets/publish-site.png)

Er is een indicatie nadat de site is gepubliceerd.

![op de site gepubliceerd](assets/site-published.png)

### Publiceren met geneste groepen {#publishing-with-nested-groups}

Na het publiceren van een communautaire plaats, is het noodzakelijk om elke subcommunity (genestelde groep) individueel te publiceren die gebruikend wordt gecreeerd [Groepsconsole](/help/communities/groups.md).

## De site exporteren {#exporting-the-site}

![exportlocatie](assets/export-site.png)

Selecteer het exportpictogram als u de muisaanwijzer op de site plaatst, zodat u een pakket van de communitysite kunt maken dat beide is opgeslagen in het dialoogvenster [Pakketbeheer](/help/sites-administering/package-manager.md) en gedownload.

UGC is niet opgenomen in het sitepakket.

## De site verwijderen {#deleting-the-site}

![deleteicon](assets/deleteicon.png)

Als u de communitysite wilt verwijderen, selecteert u het pictogram Site verwijderen dat verschijnt wanneer u de muisaanwijzer op de site in de Community Site Console plaatst. Deze actie verwijdert alle punten verbonden aan de plaats, zoals UGC, gebruikersgroepen, activa, en gegevensbestandverslagen.

## Gemaakte gebruikersgroepen {#created-community-user-groups}

Zodra de nieuwe communautaire plaats wordt gepubliceerd, worden de nieuwe lidgroepen (gebruikersgroepen worden gecreeerd in publicatiemilieu) die de aangewezen toestemmingen hebben die voor diverse administratieve en lidrollen worden geplaatst.

De naam die voor de lidgroepen is gemaakt, bevat de *sitenaam* gegeven in [Stap 1](#step13asitetemplate) (de naam die wordt weergegeven in de URL). Het omvat ook een unieke identiteitskaart om conflicten met communautaire plaatsen en groepen te vermijden die de plaats-naam voor verschillende communautaire plaatwortels hebben.

Als de naam bijvoorbeeld &quot;enter&quot; was voor een site met de naam &quot;Getting Started Tutorial&quot;, zou de gebruikersgroep voor moderatoren het volgende zijn:

* titel: Moderatoren van de communautaire vakkennis
* naam : community-*toewijding*-moderators

Om het even welke leden toegewezen rollen als moderatoren of groepsbeheerders terwijl het creëren van de plaats, worden toegewezen aan de aangewezen groep en aan de ledengroep toegewezen. Deze groepen en lidtoewijzingen worden gemaakt bij publicatie wanneer de nieuwe site wordt gepubliceerd.

Zie voor meer informatie [Gebruikers en gebruikersgroepen beheren](/help/communities/users.md).

>[!NOTE]
>
>Indien [Sociale aanmelding toestaan: Facebook](#user-management) wordt ingeschakeld, zodra de gebruikersgroep `community-<site-name>-<uid>-members`
>wordt gemaakt, wordt de toepassing [Facebook-cloudservice](/help/communities/social-login.md#createafacebookcloudservice) moet worden geconfigureerd om gebruikers toe te voegen aan deze groep.

## Configureren voor verificatiefout {#configure-for-authentication-error}

Standaard wordt een communautaire site omgeleid naar een voorbeeld van een aanmeldingspagina wanneer de gebruiker de verkeerde gegevens invoert en zich niet kan aanmelden. Deze voorbeeldaanmelding is niet aanwezig op een [productieserver](/help/sites-administering/production-ready.md).

Om correct om te leiden, zodra een plaats is gevormd en ertoe aangezet om te publiceren, voltooi deze stappen om authentificatiemislukking te krijgen om aan de communautaire plaats om te leiden:

* Op elke AEM-publicatie-instantie.
* Meld u aan met beheerdersrechten.
* Toegang krijgen tot de [Webconsole](/help/sites-deploying/configuring-osgi.md).

   * Bijvoorbeeld: [https://localhost:4503/system/console/configMgr](https://localhost:4503/system/console/configMgr).

* Zoeken `Adobe Granite Login Selector Authentication Handler`.
* Selecteer de `pencil` zodat u de configuratie kunt openen voor bewerken.
* Voer een **Toewijzingen aanmeldingspagina&#39;s** als volgt:

  `/content/sites/<site-name>/path/to/login/page:/content/sites/<site-name>`

  Bijvoorbeeld:
  `/content/sites/engage/en/signin:/content/sites/engage/en`

* Selecteren **Opslaan**.

![auth-error](assets/auth-error.png)

### Omleiding van verificatie testen {#test-authentication-redirection}

Op zelfde AEM publiceer instantie die met een login paginaplaat voor de communautaire plaats wordt gevormd:

* Blader naar de homepage van de website van de community.

   * Bijvoorbeeld: [https://localhost:4503/content/sites/engage/en.html](https://localhost:4503/content/sites/engage/en.html)

* Selecteer Afmelden.
* Selecteer Aanmelden.
* Voer onjuiste gegevens in, zoals gebruikersnaam &quot;x&quot; en wachtwoord &quot;x&quot;.
* De aanmeldingspagina moet worden weergegeven met de fout &quot;Ongeldige aanmelding&quot;.

![testverificatie](assets/test-authentication.png)

## Toegang tot communitysites vanuit de hoofdsiteconsole {#accessing-community-sites-from-main-sites-console}

Vanuit de globale console van navigatiesites, zijn de communautaire plaatsen in `Community Sites` map.

Terwijl het mogelijk is om tot een communautaire plaats op deze manier, voor administratieve taken toegang te hebben, zou de communautaire plaats van de console van de Plaatsen van Gemeenschappen moeten worden betreden.

![toegangs-plaats](assets/access-site.png)
