---
title: Sites-console van gemeenschappen
seo-title: Sites-console van gemeenschappen
description: Hoe te tot de console van de Plaatsen van Gemeenschappen toegang te hebben
seo-description: Hoe te tot de console van de Plaatsen van Gemeenschappen toegang te hebben
uuid: 74134281-244c-40da-a941-7f2f3e706d4b
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 4130f952-5bb5-4e32-91d6-47b2885b30a4
docset: aem65
role: Admin
source-git-commit: d42057a2f8ce50332f404388fd1cfc9b6a154765
workflow-type: tm+mt
source-wordcount: '3286'
ht-degree: 0%

---


# Sites-console van gemeenschappen {#communities-sites-console}

De console van de Plaatsen van Gemeenschappen verleent toegang tot:

* Site maken
* Site bewerken
* Sitebeheer
* [Geneste groepen](/help/communities/groups.md)  maken en bewerken (subgemeenschappen)

Zie [Aan de slag met AEM Communities](/help/communities/getting-started.md) om te zien hoe snel een communautaire plaats in het auteursmilieu kan worden gecreeerd, evenals hoe te om communautaire groepen van de auteur tot stand te brengen en milieu&#39;s te publiceren.

>[!NOTE]
>
>De belangrijkste menu&#39;s van Gemeenschappen voor de verwezenlijking van [communautaire plaatsen](/help/communities/sites-console.md), [communautaire plaatssjablonen](/help/communities/sites.md), [communitygroepsmalplaatjes](/help/communities/tools-groups.md) en [communityfuncties](/help/communities/functions.md) zijn voor gebruik slechts in het auteursmilieu.

## Vereisten {#prerequisites}

Voordat u een communitysite maakt, moet u *a1/> gebruiken om:*

* Zorg ervoor dat een of meer publicatie-instanties actief zijn.
* Schakel de [tunnelservice](/help/communities/deploy-communities.md#tunnel-service-on-author) in om leden en lidgroepen te beheren.
* Identificeer [primaire uitgever](/help/communities/deploy-communities.md#primary-publisher).
* [Configureer ](/help/communities/deploy-communities.md#replication-agents-on-author) replicatie wanneer primaire uitgevershavens niet het gebrek is (4503).

De beste praktijken, om ervoor te zorgen de plaats bereid is om vele eigenschappen te steunen, moeten de volgende stappen nemen:

* Installeer het [nieuwste functiepakket](/help/communities/deploy-communities.md#latestfeaturepack).
* Schakel [Adobe Analytics](/help/communities/analytics.md) voor AEM Communities in.
* [e-mail](/help/communities/email.md) configureren
* [Community Administrators](/help/communities/users.md#creating-community-members) identificeren.
* [Schakel OAuth-](/help/communities/social-login.md#adobe-granite-oauth-authentication-handler) handleraar in voor aanmelden bij een sociaal netwerk.

## Toegang tot de console met sites van Gemeenschappen {#accessing-communities-sites-console}

In het auteursmilieu, om de console van de Plaatsen van Gemeenschappen te bereiken:

* Vanuit globale navigatie: **[!UICONTROL Communities]** > **[!UICONTROL Sites]**

De console van de Plaatsen van Gemeenschappen toont om het even welke bestaande communautaire plaatsen. Vanuit deze console kunnen gemeenschapssites worden gemaakt, bewerkt, beheerd en verwijderd.

Als u een nieuwe communitysite wilt maken, selecteert u het pictogram **Maken**.

Als u toegang wilt krijgen tot een bestaande communitysite, ten behoeve van het ontwerpen, wijzigen, publiceren, exporteren of toevoegen van een geneste groep, selecteert u het mappictogram van de site.

In de volgende afbeelding ziet u bijvoorbeeld de hoofdconsole van Communitysites met de mappen voor twee communitysites: [enable](/help/communities/getting-started-enablement.md) en [engageren](/help/communities/getting-started.md):

![site-console](assets/site-console.png)

## Site maken {#site-creation}

De console voor het maken van sites biedt een stapsgewijze benadering voor het samenstellen van functies van de site op basis van een geselecteerde [communitysjabloon](/help/communities/sites.md) en instellingen.

Elke gemaakte site bevat een aanmeldingsfunctie omdat bezoekers van de site zich moeten aanmelden voordat ze inhoud kunnen posten, berichten kunnen verzenden of aan een groep kunnen deelnemen. Andere inbegrepen eigenschappen zijn gebruikersprofielen, overseinen, berichten, plaatsmenu, onderzoek, thema, en branding.

Het proces wordt gestart door de `Create` knoop te selecteren die bij de bovenkant van de console van de Plaatsen van Gemeenschappen wordt gevestigd.

Het ontwerpproces is een reeks stappen die worden gepresenteerd als deelvensters met een set functies die moeten worden geconfigureerd (weergegeven als subdeelvensters). Het is mogelijk om naar **Volgende** stap of **Terug** naar de vorige stap te gaan alvorens de plaats in de definitieve stap te bevestigen.

### Stap 1: Sitesjabloon {#step-site-template}

![nieuwssite](assets/newsitetemplate.png)

In het deelvenster Sjabloon site worden de titel, beschrijving, hoofdmap van site, basistaal, naam en Sjabloon van site opgegeven:

* **Titel van gemeenschapssite**

   Een weergavetitel voor de site.

   De titel wordt weergegeven op de gepubliceerde site en in de interface voor sitebeheer.

* **Beschrijving van community-site**

   Een beschrijving van de site.

   De beschrijving wordt niet weergegeven op de gepubliceerde site.

* **Hoofdmap van gemeenschapssite**

   Het hoofdpad naar de site.

   De standaardhoofdmap is `/content/sites`, maar de hoofdmap kan naar een willekeurige locatie binnen de website worden verplaatst.

* **Basis van gemeenschapssite**

   (Niet gewijzigd laten voor één taal: (Engels) Gebruik het keuzemenu om een *of meer* basistalen te kiezen uit de beschikbare talen - Duits, Italiaans, Frans, Japans, Spaans, Portugees (Brazilië), Chinees (Traditioneel) en Chinees (Vereenvoudigd). Er wordt één communitysite gemaakt voor elke toegevoegde taal en deze wordt in dezelfde sitemap gebruikt volgens de best practices die worden beschreven in [Inhoud vertalen voor meertalige sites](/help/sites-administering/translation.md). De hoofdpagina van elke site bevat een onderliggende pagina met de taalcode van een van de geselecteerde talen, zoals &#39;en&#39; voor Engels of &#39;fr&#39; voor Frans.

* **Naam** van communautaire site:

   De naam van de hoofdpagina van de site die in de URL wordt weergegeven.

   * Controleer de naam nogmaals omdat deze na het maken van de site niet gemakkelijk kan worden gewijzigd.
   * De basis-URL ( `https://server:port/site root/site name)` wordt onder `Community Site Name` weergegeven.

   * Voeg voor een geldige URL een basistaalcode + &quot;.html&quot; toe

      *Bijvoorbeeld*, `https://localhost:4502/content/sites/mysight/en.html`

* **Community Site** Templatemenu

   Gebruik het keuzemenu om een beschikbare [communitysitesjabloon](/help/communities/tools.md) te kiezen.

* Selecteer **Volgende**.

### Stap 2: Ontwerp {#step-design}

Het deelvenster Ontwerp bevat twee subdeelvensters voor het selecteren van het thema en de brandingbanner:

#### COMMUNAUTAIR SITE-THEMA {#community-site-theme}

![sitethema](assets/sitetheme.png)

Het framework gebruikt `Twitter Bootstrap` om de site een responsief, flexibel ontwerp te geven. U kunt een van de vele vooraf geladen Bootstrap-thema&#39;s selecteren om de stijl van de geselecteerde communitysitesjabloon te bepalen of u kunt een Bootstrap-thema uploaden.

Als deze optie is geselecteerd, wordt het thema bedekt met een ondoorzichtig blauw vinkje.

Nadat de communitysite is gepubliceerd, is het mogelijk om de eigenschappen [te bewerken en een ander thema te selecteren.](#modifying-site-properties)

#### COMMUNAUTAIRE SITOBRANDING {#community-site-branding}

![branding van sites](assets/site-branding.png)

De branding van de communautaire plaats is een beeld dat als kopbal over de bovenkant van elke pagina wordt getoond.

Het formaat van de afbeelding moet zo breed zijn als de verwachte weergave van de pagina in de browser en 120 pixels hoog.

Houd rekening met het volgende wanneer u een afbeelding maakt of selecteert:

* De afbeeldingshoogte wordt bijgesneden tot 120 pixels, gemeten vanaf de bovenrand van de afbeelding.
* De afbeelding is vastgezet aan de linkerrand van het browservenster.
* De afbeelding wordt niet vergroot of verkleind, zodat de afbeeldingsbreedte..

   * Bij een lagere breedte dan de breedte van de browser wordt de afbeelding horizontaal herhaald.
   * Als de breedte van de browser groter is, wordt de afbeelding bijgesneden.

* Selecteer **Volgende**.

### Stap 3: Instellingen {#step-settings}

Het deelvenster Instellingen bevat verschillende subdeelvensters met functies die moeten worden geconfigureerd voordat de laatste stap wordt uitgevoerd om de site te maken.

* [GEBRUIKERSBEHEER](#user-management)
* [TAGS](#tagging)
* [ROLES](#roles)
* [MODERING](#moderation)
* [ANALYSE](#analytics)
* [VERTALING](#translation)
* [UITSCHAKELING](#enablement)

>[!NOTE]
>
>**Tunnelservice inschakelen**
>
>Verscheidene sub-panelen van Montages staan toewijzing van een vertrouwd lid aan gematigde UGC toe, leiden groepen, of zijn contacten voor inschrijvingsmiddelen in het publicatiemilieu.
>
>De conventie is dat [gebruikers en gebruikersgroepen](/help/communities/users.md) (leden en lidgroepen) niet in de auteursomgeving worden gedupliceerd.
>
>Zo is het bij het maken van de gemeenschapssite in de auteursomgeving en het toewijzen van vertrouwde leden aan verschillende rollen noodzakelijk om lidgegevens op te halen uit de publicatieomgeving.
>
>Dit wordt verwezenlijkt door ` [AEM Communities Publish Tunnel Service](/help/communities/deploy-communities.md#tunnel-service-on-author)` voor het auteursmilieu toe te laten.

#### GEBRUIKERSBEHEER {#user-management}

![creaties](assets/createsitesettings.png)

>[!NOTE]
>
>Het wordt aanbevolen [communitysites inschakelen](/help/communities/overview.md#enablement-community) privé te laten zijn (neem contact op met uw accountvertegenwoordiger voor meer informatie).
>
>Een gemeenschapssite is persoonlijk wanneer anonieme sitebezoekers geen toegang krijgen, zich mogelijk niet zelf registreren en geen gebruik maken van sociale aanmelding.

* **Gebruikersregistratie toestaan**

   Als deze optie ingeschakeld is, kunnen bezoekers van de site leden van de community worden via zelfregistratie.
Als deze optie niet is ingeschakeld, is de site van de community *beperkt* en moeten sitebezoekers worden toegewezen aan de groep van leden van de site van de community, een aanvraag indienen of een uitnodiging per e-mail ontvangen. Als deze optie uitgeschakeld is, mag anonieme toegang niet worden toegestaan.
Schakel de optie uit voor een *private*-communitysite. Standaard is ingeschakeld.

* **Anonieme toegang toestaan**

   Als deze optie is ingeschakeld, is de site van de community *open *en kan elke bezoeker van de site toegang krijgen tot de site.
Als deze optie is uitgeschakeld, hebben alleen leden met een aanmelding toegang tot de site.
Schakel de optie uit voor een *persoonlijke *community-site. Standaard is ingeschakeld.

* **Berichten toestaan**

   Als deze optie is ingeschakeld, kunnen leden berichten naar elkaar en naar de groep binnen de site van de community verzenden.
Als niet gecontroleerd, is het overseinen niet opstelling voor de gemeenschap.
De optie Standaard is uitgeschakeld.

* **Sociale aanmeldingen toestaan: Facebook**

   Als deze optie is ingeschakeld, kunnen sitebezoekers zich aanmelden met hun Facebook-accountgegevens. De geselecteerde [Facebook wolkenconfiguratie](/help/communities/social-login.md#create-a-facebook-connect-cloud-service) zou moeten worden gevormd om gebruikers aan de de ledengroep van de communautaire plaats toe te voegen zodra de communautaire plaats wordt gecreeerd.
Als deze optie uitgeschakeld is, wordt geen Facebook-aanmelding weergegeven.
Laat de *private*-communitysite uitgeschakeld. De optie Standaard is uitgeschakeld.

* **Sociale aanmeldingen toestaan: Twitter**

   Als deze optie is ingeschakeld, kunnen sitebezoekers zich aanmelden met hun Twitter-accountgegevens. De geselecteerde [Twitter wolkenconfiguratie](/help/communities/social-login.md#create-a-twitter-connect-cloud-service) zou moeten worden gevormd om gebruikers aan de de ledengroep van de communautaire plaats toe te voegen zodra de communautaire plaats wordt gecreeerd.
Als deze optie uitgeschakeld is, wordt geen Twitter-aanmelding weergegeven.
Laat de *private*-communitysite uitgeschakeld. De optie Standaard is uitgeschakeld.

>[!NOTE]
>
>**Sociale aanmeldingen toestaan**
>
>Hoewel voorbeelden van Facebook- en Twitter-configuraties kunnen bestaan en kunnen worden geselecteerd, is het voor een [productieomgeving](/help/sites-administering/production-ready.md) noodzakelijk om aangepaste Facebook- en Twitter-toepassingen te maken. Zie [Sociale aanmelding met Facebook en Twitter](/help/communities/social-login.md).

#### TAGS {#tagging}

![sitetags](assets/site-tagging.png)

De tags die kunnen worden toegepast op community-inhoud, worden beheerd door Tag-naamruimten te selecteren die eerder zijn gedefinieerd via de [Tagingconsole](/help/sites-administering/tags.md#tagging-console).

Bovendien beperkt het selecteren van tagnaamruimten voor de site van de community de weergegeven selectie bij het definiëren van catalogi en bronnen. Zie [Tags toewijzen Bronnen](/help/communities/tag-resources.md) voor belangrijke informatie.

* tekstzoekvak: Begin te typen om tags te identificeren die op de site mogen worden gebruikt.

#### ROLES {#roles}

![Communautaire rollen](assets/site-admin-2.png)

De [rollen van communityleden](/help/communities/users.md) worden toegewezen met deze montages.

Het zoeken naar leden van een community is eenvoudig met &#39;type-ahead&#39;-zoekopdracht.

* **Community-managers**

   Begin te typen om een of meer leden van de gemeenschap of leden te selecteren die leden van de gemeenschap en leden kunnen beheren.

* **Communautaire moderatoren**

   Begin te typen om één of meerdere leden van de gemeenschap of lidgroepen te selecteren die als moderatoren van gebruiker geproduceerde inhoud moeten worden vertrouwd.

* **Geprivilegieerde leden van de Gemeenschap**

   Begin te typen om één of meerdere leden van de gemeenschap of lidgroepen te selecteren die de capaciteit moeten worden gegeven om nieuwe inhoud tot stand te brengen wanneer `Allow Privileged Member` voor een [communautaire functie](/help/communities/functions.md) is geselecteerd.

* **Community Admins**

   Begin te typen om één of meerdere plaatsbeheerders te selecteren die de plaatsstructuur onafhankelijk van andere plaatsbeheerders en standaardcommunautaire beheerder kunnen behandelen. Zij kunnen tot groep op om het even welk niveau van de hiërarchie leiden, en de standaardbeheerder van de genestelde groepen worden (maar zij kunnen later uit de adminrol van genestelde groepen worden verwijderd).

#### MODERING {#moderation}

![modernisering van de locatie](assets/site-moderation.png)

De globale instelling voor het modereren van door gebruikers gegenereerde inhoud (UGC) wordt door deze instellingen beheerd. Individuele componenten hebben extra montages om matiging te controleren.

* **Inhoud is vooraf gemodereerd**

   Als deze optie is ingeschakeld, wordt de geposte community-inhoud pas weergegeven nadat deze is goedgekeurd door een moderator. De optie Standaard is uitgeschakeld. Voor meer informatie, zie [Moderating Community Content](/help/communities/moderate-ugc.md#premoderation).

* **Markeringsdrempel voordat inhoud wordt verborgen**

   Als de waarde groter is dan 0, moet het aantal keren dat een onderwerp of bericht moet worden gemarkeerd voordat het wordt verborgen in de openbare weergave. Indien ingesteld op -1, wordt het gemarkeerde onderwerp of de post nooit verborgen voor de openbare weergave. De standaardwaarde is 5.

#### ANALYSE {#analytics}

![locatieanalyse](assets/site-analytics.png)

* **Analyse inschakelen**

   Alleen beschikbaar wanneer Adobe Analytics [geconfigureerd](/help/communities/analytics.md) is voor functies van Communities.
De optie Standaard is uitgeschakeld. Als deze optie is ingeschakeld, wordt een extra selectiemenu weergegeven:

![voor locatieanalyse](assets/site-analytics-enable.png)

* **Verwijzing naar Cloud Config Framework**

   Selecteer in het keuzemenu het cloudserviceframework Analytics dat voor deze communitysite is geconfigureerd.
   `Communities` Dit is het kadervoorbeeld van  [Analytics Configuration for Communities ](/help/communities/analytics.md#aem-analytics-framework-configuration) Featuresdocumentation.

#### VERTALING {#translation}

![site-vertaling](assets/site-translation.png)

* **Machinevertaling toestaan**

   Als deze optie is ingeschakeld (de standaardinstelling is uitgeschakeld), wordt automatische omzetting ingeschakeld voor UGC binnen de site. Dit heeft geen invloed op andere inhoud, zoals pagina-inhoud, zelfs niet als de site is ingesteld als een meertalige site. Zie [Door gebruiker gegenereerde inhoud vertalen](/help/communities/translate-ugc.md) voor informatie over het configureren van een gelicentieerde vertaalservice voor AEM Communities. Zie [Inhoud vertalen voor meertalige sites](/help/sites-administering/translation.md) voor een volledig overzicht.

![allow-machine-translatie](assets/allow-machine-translation.png)

* **Machine Translation inschakelen voor geselecteerde talen**

   De talen die voor machinevertaling worden toegelaten gebrek aan het systeem dat door [vertaalintegratieconfiguratie](/help/communities/translate-ugc.md#translation-integration-configuration) wordt gespecificeerd. Deze standaardinstellingen kunnen voor deze site worden overschreven door standaardinstellingen te verwijderen en/of andere talen te selecteren in het keuzemenu.

* **Vertaalprovider kiezen**

   Standaard is de serviceprovider een proefversie die alleen `microsoft` gebruikt voor demonstratie. Als er geen licentie is voor een vertaalservicebureau, moet **Machinevertaling toestaan** zijn uitgeschakeld.

* **Globale gedeelde opslag kiezen**

   Voor een website met veelvoudige taalexemplaren, verstrekt een globale gedeelde opslag één enkele draad van gesprek, zichtbaar van elke taalexemplaar. Dit wordt bereikt door een van de talen te selecteren die als een taalkopie worden opgenomen. Standaard is *Geen globale gedeelde opslag*.

* **Configuratie van vertaalprovider kiezen**

   Kies een [vertaalintegratieframework](/help/sites-administering/tc-tic.md) dat is gemaakt voor de vertaalprovider met licentie.

* **Selecteer de vertaalopties voor uw communitysite**

   * **Gehele pagina vertalen**

      Als deze optie is geselecteerd, wordt alle UGC op een pagina vertaald in de basistaal van de pagina.

      Standaard is *niet geselecteerd*.

   * **Alleen selectie vertalen**

      Als deze optie is geselecteerd, wordt naast elke advertentie een vertaaloptie weergegeven waarmee afzonderlijke posts kunnen worden vertaald in de basistaal van de pagina.
Standaard is *selected*.

* **Persistopties selecteren**

   * **Vertaal bijdragen op verzoek van de gebruiker en blijf**
daarna bestaanAls geselecteerd, wordt de inhoud niet vertaald tot een verzoek wordt gedaan. Nadat de vertaling is vertaald, wordt de vertaling opgeslagen in de opslagplaats.

      Standaard is *niet geselecteerd*.

   * **Geen vertalingen behouden**

      Indien geselecteerd, worden de vertalingen niet opgeslagen in de bewaarplaats.

      Als deze optie niet is geselecteerd, blijven de vertalingen behouden.

      Standaard is *niet geselecteerd*.

* **Slimme rendering**

   Selecteer een van de volgende opties:

   * `Always show contributions in the original language` (standaardwaarde)
   * `Always show contributions in user preferred language`
   * `Show contributions in user preferred language for only logged-in users`

#### UITSCHAKELING {#enablement}

![locatienablement](assets/site-enablement.png)

De `ENABLEMENT`montages zijn van toepassing wanneer het gekozen malplaatje van de communautaire plaats [toewijzingsfunctie](/help/communities/functions.md#assignments-function) omvat, die beschikbaar is wanneer de enablement eigenschappen vergunning en [configured](/help/communities/enablement.md) hebben. De verwijzingsplaatssjabloon die de toewijzingsfunctie omvat is `Reference Structured Learning Site Template.`

* **Enablement Managers**
 (Vereist) Slechts zijn de leden van de  `Community Enablementmanagers` groep beschikbaar om worden geselecteerd om deze enablement gemeenschap te beheren. Enablement managers zijn verantwoordelijk voor het toewijzen van leden aan bronnen. Zie ook [Gebruikers en gebruikersgroepen beheren](/help/communities/users.md).

* **Org-id Marketing Cloud**

   (optioneel) De id voor een [Video Heartbone Analytics](/help/communities/analytics.md#video-heartbeat-analytics)-licentie.

* Selecteer **Volgende**.

### Stap 4: Communitysite maken {#step-create-communities-site}

Als er aanpassingen nodig zijn, gebruikt u de knop **Terug** om deze aan te brengen.

Als **Create** eenmaal is geselecteerd en gestart, kan het maken van de site niet worden onderbroken.

Nadat de site is gemaakt:

* Het wijzigen van de URL (knooppuntnaam) wordt niet ondersteund.
* De toekomstige veranderingen in het malplaatje van de communautaire plaats zullen niet de gecreeerde communautaire plaats beïnvloeden.
* Het onbruikbaar maken van het malplaatje van de communautaire plaats zal niet de gecreeerde communautaire plaats beïnvloeden.
* Het is mogelijk om de [STRUCTUUR](#modify-structure) van een communautaire plaats uit te geven door zijn eigenschappen te wijzigen.

![site maken](assets/create-site1.png)

Wanneer het proces is voltooid, wordt de map voor de nieuwe site weergegeven in de console Communitysites, waar auteurs pagina-inhoud kunnen toevoegen of waar beheerders de eigenschappen van de site kunnen wijzigen.

![modify-site-property](assets/modify-site-property.png)

Als u een communitysite wilt wijzigen, selecteert u de projectmap om deze te openen:

![project](assets/site-project.png)

Als u de muis boven een site houdt of een sitekaart aanraakt, worden pictogrammen weergegeven waarmee [de site kan worden bewerkt in de modus Schrijver](#authoring-site-content), [de site-eigenschappen kunnen worden geopend voor modificatie](#modifying-site-properties), [het publiceren van de site](#publishing-the-site), [het exporteren van de site](#exporting-the-site) en [het verwijderen van de site.](#deleting-the-site)

## Site-inhoud ontwerpen {#authoring-site-content}

De inhoud van een site kan met dezelfde gereedschappen worden gemaakt als elke andere AEM website. Als u de site wilt openen voor ontwerpen, selecteert u het `Open Site`-pictogram dat wordt weergegeven wanneer u de muis op de site plaatst. De site wordt op een nieuw tabblad geopend, zodat de console Communitysites toegankelijk blijft.

![site-inhoud](assets/site-content.png)

>[!NOTE]
>
>Als u niet bekend bent met AEM, bekijkt u de documentatie over [basisverwerking](/help/sites-authoring/basic-handling.md) en een [handleiding voor het schrijven van pagina&#39;s](/help/sites-authoring/qg-page-authoring.md).

## Site-eigenschappen wijzigen {#modifying-site-properties}

![site bewerken](assets/edit-site.png)

De eigenschappen van een bestaande site die tijdens het maken van de site zijn opgegeven, kunnen worden gewijzigd door het pictogram `Edit Site`te selecteren dat wordt weergegeven wanneer u de muis op de site plaatst.

`Details of the following properties match the descriptions provided in the` [Site ](#site-creation) maken.

![modify-site-basicinfo](assets/modify-site-basicinfo.png)

### Basis wijzigen {#modify-basic}

In het BASIC-deelvenster kunt u de volgende wijzigingen aanbrengen:

* Titel van gemeenschapssite
* Beschrijving van community-site

De naam van de communautaire site mag niet worden gewijzigd.

Het kiezen van een verschillend malplaatje van de communautaire plaats zou geen invloed op een bestaande communautaire plaats hebben aangezien geen verbinding tussen malplaatjes en plaatsen blijft.

In plaats daarvan kan de [STRUCTUUR](#modify-structure) van de communitysite worden gewijzigd.

### Structuur wijzigen {#modify-structure}

In het deelvenster STRUCTUUR kunt u de structuur wijzigen die oorspronkelijk is gemaakt op basis van de geselecteerde communitysitesjabloon. Vanuit het deelvenster kunt u het volgende doen:

* Sleep extra [communityfuncties](/help/communities/functions.md) naar de sitestructuur.
* Bij een instantie van een communautaire functie in de sitestructuur:

   * **`gear icon`**

      Bewerk instellingen, zoals de titel van de weergave en de URL-naam*, en [groepen van geprivilegieerde leden](/help/communities/users.md#privilegedmembersgroups).

   * **`trashcan icon`**

      Verwijder (verwijder) functies uit de sitestructuur.

   * **`grid icon`**

      Hiermee wijzigt u de volgorde van de functies die wordt weergegeven op de navigatiebalk op hoofdniveau van de site.

>[!NOTE]
>
>U kunt de volgorde van alle functies in de sitestructuur wijzigen, behalve van de functie bovenaan. Daarom kan de homepage van de plaats van gemeenschappen niet worden veranderd.

>[!CAUTION]
>
>* Hoewel de titel van de weergave zonder bijwerkingen kan worden gewijzigd, wordt het niet aanbevolen de URL-naam te bewerken van een communautaire functie die bij een communautaire site hoort.
>
>
Als u bijvoorbeeld de naam van de URL wijzigt, wordt de bestaande UGC niet verplaatst, waardoor de UGC verloren gaat.

>[!CAUTION]
>
>De groepsfunctie moet *niet* eerst of de enige functie *in de sitestructuur zijn.*
>
>Elke andere functie, zoals de [paginafunctie](/help/communities/functions.md#page-function), moet worden opgenomen en als eerste worden vermeld.

#### Voorbeeld: Een catalogusfunctie toevoegen aan een community-sitestructuur {#example-adding-a-catalog-function-to-a-community-site-structure}

![add-catalog-site](assets/add-catalog-site.png)

### Ontwerp wijzigen {#modify-design}

In het deelvenster ONTWERP kunt u een nieuw thema toepassen:

* [Thema van communautaire site](#community-site-theme)
* [Gemeenschapsmerk](#community-site-branding)

   * Schuif naar de onderkant van het deelvenster om de afbeelding van het merk te wijzigen.

### Instellingen wijzigen {#modify-settings}

In het deelvenster INSTELLINGEN hebt u toegang tot de meeste instellingen onder de subdeelvensters van Stap 3 van het maken van de communitysite:

* [Gebruikersbeheer](#user-management)
* [Tags](#tagging)
* [Moderatie](#moderation)
* [Lidrollen](#roles)
* [Analyse](#analytics)
* [Vertaling](#translation)

### Miniatuur wijzigen {#modify-thumbnail}

In het deelvenster MINIATUUR kunt u een afbeelding uploaden om de site in de console Sites van Gemeenschappen weer te geven.

### Inschakelen wijzigen {#modify-enablement}

Met het deelvenster ENABLEMENT hebt u toegang tot de instellingen die zijn opgegeven tijdens het maken van de site van de community.

Zie de beschrijving [ENABLEMENT](#enablement).

## De site publiceren {#publishing-the-site}

Nadat een communitysite net is gemaakt of gewijzigd, is het mogelijk om de site te publiceren (activeren) door het pictogram `Publish Site` te selecteren, dat verschijnt als u de muisaanwijzer op de site plaatst.

![publicatiesite](assets/publish-site.png)

Er verschijnt een indicatie nadat de site is gepubliceerd.

![op de site gepubliceerd](assets/site-published.png)

### Publiceren met geneste groepen {#publishing-with-nested-groups}

Na het publiceren van een communautaire plaats, is het noodzakelijk om elke subgemeenschap (genestelde groep) individueel te publiceren die gebruikend [de console van Groepen](/help/communities/groups.md) wordt gecreeerd.

## De site exporteren {#exporting-the-site}

![exportlocatie](assets/export-site.png)

Selecteer het exportpictogram als u de muisaanwijzer op de site plaatst om een pakket van de communitysite te maken dat zowel in [pakketbeheer](/help/sites-administering/package-manager.md) wordt opgeslagen als wordt gedownload.

UGC is niet opgenomen in het sitepakket.

## De site verwijderen {#deleting-the-site}

![deleteicon](assets/deleteicon.png)

Als u de communitysite wilt verwijderen, selecteert u het pictogram Site verwijderen dat verschijnt wanneer u de muisaanwijzer op de site in de Community Site Console plaatst. Met deze actie verwijdert u alle items die aan de site zijn gekoppeld, zoals UGC, gebruikersgroepen, elementen en databaserecords.

## Gemaakte gebruikersgroepen {#created-community-user-groups}

Zodra de nieuwe communautaire plaats wordt gepubliceerd, worden de nieuwe lidgroepen (gebruikersgroepen worden gecreeerd in publicatiemilieu) die de aangewezen toestemmingen hebben die voor diverse administratieve en lidrollen worden geplaatst.

De naam die voor de lidgroepen is gemaakt, bevat de *site-naam* die op de site is vermeld in [Stap 1](#step13asitetemplate) (de naam die in de URL wordt weergegeven) en een unieke id om conflicten te voorkomen met gemeenschapssites en groepen die dezelfde site-naam hebben voor verschillende hoofdmappen van de site.

Als de naam bijvoorbeeld &quot;enter&quot; was voor een site met de naam &quot;Getting Started Tutorial&quot;, zou de gebruikersgroep voor moderatoren het volgende zijn:

* titel: Maatschappelijke experts
* naam: community-*commit-uid*-moderators

Bericht dat om het even welke leden rollen als moderatoren of groepsbeheerders terwijl het creëren van de plaats toewezen, aan de aangewezen groep zal worden toegewezen evenals aan de lidgroep toegewezen. Deze groepen en lidtoewijzingen worden gemaakt bij publicatie wanneer de nieuwe site wordt gepubliceerd.

Zie [Gebruikers en gebruikersgroepen beheren](/help/communities/users.md) voor meer informatie.

>[!NOTE]
>
>Als [Sociale aanmelding toestaan: Facebook](#user-management) is ingeschakeld, zodra de gebruikersgroep
>
>* `community-<site-name>-<uid>-members`
>
>
wordt gecreeerd, zou de toegepaste [Facebook wolkendienst](/help/communities/social-login.md#createafacebookcloudservice) moeten worden gevormd om gebruikers aan deze groep toe te voegen.

## Configureren voor verificatiefout {#configure-for-authentication-error}

Standaard leidt een communitysite naar een voorbeeld van een aanmeldingspagina als de gebruiker de verkeerde gegevens heeft ingevoerd en zich niet heeft aangemeld. Deze voorbeeldaanmelding is niet aanwezig op een [productieserver](/help/sites-administering/production-ready.md).

Om correct om te leiden, zodra een plaats is gevormd en ertoe aangezet om te publiceren, voltooi deze stappen om authentificatiemislukking te krijgen om aan de communautaire plaats om te leiden:

* Op elke AEM-publicatie-instantie.
* Meld u aan met beheerdersrechten.
* Open de [Webconsole](/help/sites-deploying/configuring-osgi.md).

   * Bijvoorbeeld [https://localhost:4503/system/console/configMgr](https://localhost:4503/system/console/configMgr).

* `Adobe Granite Login Selector Authentication Handler` zoeken.
* Selecteer het pictogram `pencil` om de configuratie voor bewerking te openen.
* Voer als volgt een **Aanmeldingspagina-toewijzingen** in:

   `/content/sites/<site-name>/path/to/login/page:/content/sites/<site-name>`

   Bijvoorbeeld:
   `/content/sites/engage/en/signin:/content/sites/engage/en`

* Selecteer **Opslaan**.

![auth-error](assets/auth-error.png)

### Omleiding van verificatie testen {#test-authentication-redirection}

Op zelfde AEM publiceer instantie die met een login paginaplaat voor de communautaire plaats wordt gevormd:

* Blader naar de homepage van de website van de community.

   * Bijvoorbeeld [https://localhost:4503/content/sites/engage/en.html](https://localhost:4503/content/sites/engage/en.html)

* Selecteer Afmelden.
* Selecteer Aanmelden.
* Voer duidelijk onjuiste gegevens in, zoals gebruikersnaam &quot;x&quot; en wachtwoord &quot;x&quot;.
* De aanmeldingspagina moet worden weergegeven met de fout &quot;Ongeldige aanmelding&quot;.

![testverificatie](assets/test-authentication.png)

## Toegang tot communitysites vanuit de hoofdsiteconsole {#accessing-community-sites-from-main-sites-console}

Vanuit de globale console van navigatiesites bevinden communitysites zich in de map `Community Sites`.

Terwijl het mogelijk is om tot een communautaire plaats op deze manier, voor administratieve taken toegang te hebben, zou de communautaire plaats van de console van de Plaatsen van Gemeenschappen moeten worden betreden.

![toegangs-plaats](assets/access-site.png)



