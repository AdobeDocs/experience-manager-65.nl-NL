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
translation-type: tm+mt
source-git-commit: 27a054cc5d502d95c664c3b414d0066c6c120b65

---


# Sites-console van gemeenschappen{#communities-sites-console}

De console van de Plaatsen van Gemeenschappen verleent toegang tot

* site maken
* site bewerken
* sitebeheer
* [geneste groepen](/help/communities/groups.md) maken en bewerken (subgemeenschappen)

Zie [Aan de slag met AEM-gemeenschappen](/help/communities/getting-started.md) om te zien hoe snel een gemeenschapssite kan worden gemaakt in de auteursomgeving en hoe u groepen van gemeenschappen kunt maken vanuit de auteur- en publicatieomgeving.

>[!NOTE]
>
>De belangrijkste menu&#39;s van Gemeenschappen voor de verwezenlijking van [communautaire plaatsen](/help/communities/sites-console.md), de malplaatjes [van de](/help/communities/sites.md)communautaire plaats, [communautaire groepsmalplaatjes](/help/communities/tools-groups.md) en [communautaire functies](/help/communities/functions.md) zijn voor gebruik slechts in het auteursmilieu.

## Vereisten {#prerequisites}

Voordat u een community-site maakt, moet *u deze* naar

* ervoor zorgen dat een of meer publicatie-instanties worden uitgevoerd
* de [tunneldienst](/help/communities/deploy-communities.md#tunnel-service-on-author) in staat stellen leden en leden te beheren
* de [primaire uitgever identificeren](/help/communities/deploy-communities.md#primary-publisher)
* [vorm replicatie](/help/communities/deploy-communities.md#replication-agents-on-author) wanneer de primaire uitgevershaven niet het gebrek is (4503)

De beste praktijken, om ervoor te zorgen de plaats bereid is om vele eigenschappen te steunen, moeten de volgende stappen nemen:

* installeer het [recentste eigenschappak](/help/communities/deploy-communities.md#latestfeaturepack)
* inschakelen, [Adobe Analytics](/help/communities/analytics.md) voor AEM Communities
* e- [mail configureren](/help/communities/email.md)
* communautaire [beheerders identificeren](/help/communities/users.md#creating-community-members)
* [OAuth-handler](/help/communities/social-login.md#adobe-granite-oauth-authentication-handler) inschakelen voor sociale aanmelding

## Toegang tot de console met sites van Gemeenschappen {#accessing-communities-sites-console}

In het auteursmilieu, om de console van de Plaatsen van Gemeenschappen te bereiken

* vanuit de globale navigatie:** Gemeenschappen, sites**

De console van de Plaatsen van Gemeenschappen toont om het even welke bestaande communautaire plaatsen. Vanuit deze console kunnen gemeenschapssites worden gemaakt, bewerkt, beheerd en verwijderd.

Als u een nieuwe communitysite wilt maken, selecteert u het pictogram **Maken **.

Als u toegang wilt krijgen tot een bestaande communitysite, ten behoeve van het ontwerpen, wijzigen, publiceren, exporteren of toevoegen van een geneste groep, selecteert u het mappictogram van de site.

In de volgende afbeelding ziet u bijvoorbeeld de hoofdconsole van Communitysites met de mappen voor twee communitysites: [inschakelen](/help/communities/getting-started-enablement.md) en [inschakelen](/help/communities/getting-started.md) :

![chlimage_1-154](assets/chlimage_1-154.png)

## Site maken {#site-creation}

De console van de plaatsverwezenlijking verstrekt een geleidelijke benadering om eigenschappen van de plaats samen te stellen die op een geselecteerde malplaatje [en montages van de](/help/communities/sites.md) communautaire plaats wordt gebaseerd.

Elke gemaakte site bevat een aanmeldingsfunctie omdat bezoekers van de site zich moeten aanmelden voordat ze inhoud kunnen posten, berichten kunnen verzenden of aan een groep kunnen deelnemen. Andere inbegrepen eigenschappen zijn gebruikersprofielen, overseinen, berichten, plaatsmenu, onderzoek, thema, en branding.

Het proces wordt gelanceerd door de `Create` knoop te selecteren die bij de bovenkant van de console van de Plaatsen van Gemeenschappen wordt gevestigd.

Het ontwerpproces is een reeks stappen die worden gepresenteerd als deelvensters met een set functies die moeten worden geconfigureerd (weergegeven als subdeelvensters). Het is mogelijk om naar de **Volgende stap **of **Terug **aan de vorige stap vooruit te gaan alvorens de plaats in de definitieve stap te bevestigen.

### Stap 1: Sitesjabloon {#step-site-template}

![nieuwssite](assets/newsitetemplate.png)

In het deelvenster Sjabloon site worden de titel, beschrijving, hoofdmap van site, basistaal, naam en Sjabloon van site opgegeven:

* **Titel van de communautaire site **: een weergavetoewijzing voor de site.
De titel wordt weergegeven op de gepubliceerde site en in de interface voor sitebeheer.

* **Beschrijving van gebied van de Gemeenschap **: een beschrijving van de locatie.
De beschrijving wordt niet weergegeven op de gepubliceerde site.

* **Hoofdmap van communautaire site **: het hoofdpad naar de site.
De standaardhoofdmap is `/content/sites`, maar de hoofdmap kan naar een willekeurige locatie op de website worden verplaatst.

* **Basistaal** van de communautaire site: (ongewijzigd laten voor één taal: (Engels) gebruik het keuzemenu om één *of meerdere* basistalen van de beschikbare talen - Duits, Italiaans, Frans, Japans, Spaans, Portugees (Brazilië), Chinees (Traditioneel), en Chinees (Vereenvoudigd) te kiezen. Er wordt één communitysite gemaakt voor elke toegevoegde taal en deze wordt in dezelfde sitemap gebruikt volgens de beste praktijken die worden beschreven in Inhoud [vertalen voor Meerdere sites](/help/sites-administering/translation.md). De hoofdpagina van elke site bevat een onderliggende pagina met de taalcode van een van de geselecteerde talen, zoals &#39;en&#39; voor Engels of &#39;fr&#39; voor Frans.

* **Naam van het communautaire gebied **: de naam van de hoofdpagina van de site die wordt weergegeven in de URL

   * Controleer de naam nogmaals omdat deze na het maken van de site niet gemakkelijk kan worden gewijzigd
   * de basis-URL ( `https://*server:port/site root/site name*)` wordt onder de `Community Site Name`

   * voor een geldige URL voegt u een basistaalcode + &quot;.html&quot; toe
      *bijvoorbeeld*: `https://localhost:4502/content/sites/mysight/en.html`

* **Menu Sjabloon** communautaire site: Gebruik het keuzemenu om een beschikbare sjabloon voor een [community-site](/help/communities/tools.md)te kiezen.

Selecteer **Volgende**

### Stap 2: Ontwerp {#step-design}

Het deelvenster Ontwerp bevat twee subdeelvensters voor het selecteren van het thema en de brandbanner:

#### COMMUNAUTAIR SITE-THEMA {#community-site-theme}

![sitethema](assets/sitetheme.png)

Het framework gebruikt [Twitter Bootstrap](https://twitterbootstrap.org/) om de site een responsief, flexibel ontwerp te geven. U kunt een van de vele vooraf geladen Bootstrap-thema&#39;s selecteren om de geselecteerde communitysitesjabloon op te maken of u kunt een Bootstrap-thema uploaden.

Als deze optie is geselecteerd, wordt het thema bedekt met een ondoorzichtig blauw vinkje.

Nadat de communitysite is gepubliceerd, kunt u de eigenschappen [](#modifying-site-properties) bewerken en een ander thema selecteren.

#### COMMUNAUTAIRE SITOBRANDING {#community-site-branding}

![chlimage_1-155](assets/chlimage_1-155.png)

De branding van de communautaire plaats is een beeld dat als kopbal over de bovenkant van elke pagina wordt getoond.

Het formaat van de afbeelding moet zo breed zijn als de verwachte weergave van de pagina in de browser en 120 pixels hoog.

Houd rekening met het volgende wanneer u een afbeelding maakt of selecteert:

* de afbeeldingshoogte wordt bijgesneden tot 120 pixels, gemeten vanaf de bovenrand van de afbeelding
* de afbeelding is vastgezet aan de linkerrand van het browservenster
* de afbeelding wordt niet vergroot of verkleind, zodat de afbeeldingsbreedte...

   * kleiner dan de breedte van de browser, wordt de afbeelding horizontaal herhaald
   * groter dan de breedte van de browser, lijkt de afbeelding te zijn bijgesneden

Selecteer **Volgende**.

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
>De conventie is dat [gebruikers en gebruikersgroepen](/help/communities/users.md) (leden en lidgroepen) aan de publiczijde niet in de auteursomgeving worden gedupliceerd.
>
>Zo is het bij het maken van de gemeenschapssite in de auteursomgeving en het toewijzen van vertrouwde leden aan verschillende rollen noodzakelijk om lidgegevens op te halen uit de publicatieomgeving.
>
>Dit wordt verwezenlijkt door het ` [AEM Communities Publish Tunnel Service](/help/communities/deploy-communities.md#tunnel-service-on-author)`voor het auteursmilieu toe te laten.

#### GEBRUIKERSBEHEER {#user-management}

![creaties](assets/createsitesettings.png)

>[!NOTE]
>
>Aanbevolen wordt om websites [van](/help/communities/overview.md#enablement-community) gemeenschappen voor activering privé te maken (neem contact op met uw accountvertegenwoordiger voor meer informatie).
>
>Een gemeenschapssite is persoonlijk wanneer anonieme sitebezoekers geen toegang krijgen, zich mogelijk niet zelf registreren en geen gebruik maken van sociale aanmelding.

* **Gebruikersregistratie**toestaan Als deze optie is ingeschakeld, kunnen bezoekers van de site leden van de community worden via zelfregistratie.
Als deze optie niet is ingeschakeld, is de site van de community *beperkt* en moeten bezoekers van de site worden toegewezen aan de groep van leden van de site van de community, een aanvraag indienen of een uitnodiging per e-mail ontvangen. Als deze optie uitgeschakeld is, mag anonieme toegang niet worden toegestaan.
Schakel de optie uit voor een *persoonlijke *community-site. Standaard is ingeschakeld.

* **Anonieme toegang**toestaan Als deze optie is ingeschakeld, is de communitysite *open *en kan elke bezoeker van de site toegang krijgen tot de site.
Als deze optie is uitgeschakeld, hebben alleen leden met een aanmelding toegang tot de site.
Schakel de optie uit voor een *persoonlijke *community-site. Standaard is ingeschakeld.

* **Laat Overseinen**toe indien gecontroleerd, kunnen de leden berichten naar elkaar en naar de groep binnen de communautaire plaats verzenden.
Als niet gecontroleerd, is het overseinen niet opstelling voor de gemeenschap.
De optie Standaard is uitgeschakeld.

* **Sociale aanmeldingen toestaan: Facebook**Als deze optie is ingeschakeld, kunnen bezoekers van de site zich aanmelden met hun Facebook-accountgegevens. De geselecteerde [Facebook-wolkenconfiguratie](/help/communities/social-login.md#create-a-facebook-connect-cloud-service) moet zo worden geconfigureerd dat gebruikers worden toegevoegd aan de groep leden van de site van de gemeenschap zodra de communitysite is gemaakt.
Als deze optie uitgeschakeld is, wordt geen Facebook-aanmelding weergegeven.
Laat de optie voor een *privésite* van de community uitgeschakeld. De optie Standaard is uitgeschakeld.

* **Sociale aanmeldingen toestaan: Twitter** Als deze optie is ingeschakeld, kunnen bezoekers van de site zich aanmelden met hun Twitter-accountgegevens. De geselecteerde [Twitter-wolkenconfiguratie](/help/communities/social-login.md#create-a-twitter-connect-cloud-service) moet zo worden geconfigureerd dat gebruikers aan de ledengroep van de site van de community worden toegevoegd zodra de communitysite is gemaakt.
Als deze optie uitgeschakeld is, wordt er geen Twitter-aanmelding weergegeven.
Laat de optie voor een *privésite* van de community uitgeschakeld. De optie Standaard is uitgeschakeld.

>[!NOTE]
>
>**Sociale aanmeldingen toestaan**
>
>Hoewel er voorbeelden van Facebook- en Twitter-configuraties kunnen bestaan en kunnen worden geselecteerd, is het voor een [productieomgeving](/help/sites-administering/production-ready.md)noodzakelijk om aangepaste Facebook- en Twitter-toepassingen te maken. Zie [Sociale aanmelding bij Facebook en Twitter](/help/communities/social-login.md).

#### TAGS {#tagging}

![chlimage_1-156](assets/chlimage_1-156.png)

De tags die kunnen worden toegepast op community-inhoud, worden beheerd door de tagnaamruimten te selecteren die eerder zijn gedefinieerd via de [tagconsole](/help/sites-administering/tags.md#tagging-console).

Bovendien beperkt het selecteren van tagnaamruimten voor de site van de community de weergegeven selectie bij het definiëren van catalogi en bronnen. Zie [Tags toewijzen Hulpbronnen](/help/communities/tag-resources.md) voor belangrijke informatie.

* tekstzoekvak: beginnen met typen om tags te identificeren die op de site mogen worden gebruikt

#### ROLES {#roles}

![Communautaire rollen](assets/site-admin-2.png)

De [rollen van leden](/help/communities/users.md) van de gemeenschap worden toegewezen met deze montages.

Het zoeken naar leden van een community is eenvoudig met &#39;type-ahead&#39;-zoekopdracht.

* **De managers** van de Gemeenschap beginnen te typen om één of meerdere communautaire leden of lidgroepen te selecteren die communautaire leden en lidgroepen kunnen leiden.

* **De Moderatoren** van de Gemeenschap beginnen te typen om één of meerdere communautaire leden of lidgroepen te selecteren die als moderatoren van gebruiker geproduceerde inhoud moeten worden vertrouwd.

* **Geprivilegieerde leden** van de Gemeenschap Begin te typen om één of meerdere leden van de gemeenschap of lidgroepen te selecteren die de capaciteit moeten krijgen om nieuwe inhoud tot stand te brengen wanneer `Allow Privileged Member` is geselecteerd voor een [communautaire functie](/help/communities/functions.md).

* **Gemeenschapsbeheerders** typen het begin van het typen om een of meer sitebeheerders te selecteren die de sitestructuur onafhankelijk van andere sitebeheerders en standaardbeheerder kunnen beheren. Zij kunnen tot groep op om het even welk niveau van de hiërarchie leiden, en de standaardbeheerder van de genestelde groepen worden (maar zij kunnen later uit de adminrol van genestelde groepen worden verwijderd).

#### MODERING {#moderation}

![chlimage_1-157](assets/chlimage_1-157.png)

De globale instelling voor het modereren van door gebruikers gegenereerde inhoud (UGC) wordt door deze instellingen beheerd. Individuele componenten hebben extra montages om matiging te controleren.

* **Inhoud wordt vooraf gemodereerd** Als deze wordt gecontroleerd, wordt de geposte inhoud van de community pas weergegeven nadat deze is goedgekeurd door een moderator. De optie Standaard is uitgeschakeld. Voor meer informatie, zie het [Modereren van Communautaire Inhoud](/help/communities/moderate-ugc.md#premoderation).

* **Markeringsdrempel voor inhoud wordt verborgen** Als de waarde groter is dan 0, moet het aantal keren dat een onderwerp of bericht moet worden gemarkeerd voordat het wordt verborgen in de openbare weergave. Indien ingesteld op -1, wordt het gemarkeerde onderwerp of de post nooit verborgen voor de openbare weergave. De standaardwaarde is 5.

#### ANALYSE {#analytics}

![chlimage_1-158](assets/chlimage_1-158.png)

* **Schakel Analytics** Only beschikbaar in als Adobe Analytics is [geconfigureerd](/help/communities/analytics.md) voor de functies van Communities.
De optie Standaard is uitgeschakeld. Als deze optie is ingeschakeld, wordt een extra selectiemenu weergegeven:

![chlimage_1-159](assets/chlimage_1-159.png)

* **Verwijzing naar**Cloud Config Framework vanuit het keuzemenu selecteert het voor deze communitysite geconfigureerde framework Analytics Cloud Service.
   `Communities`is het kadervoorbeeld van de Configuratie van [Analytics voor de documentatie van de Eigenschappen](/help/communities/analytics.md#aem-analytics-framework-configuration) van Communities.

#### VERTALING {#translation}

![chlimage_1-160](assets/chlimage_1-160.png)

* **Machine Translation** toestaan Als deze optie is ingeschakeld (de standaardinstelling is uitgeschakeld), is de functie voor machinevertaling ingeschakeld voor UGC op de site. Dit heeft geen invloed op andere inhoud, zoals pagina-inhoud, zelfs niet als de site is ingesteld als een meertalige site. Zie Door gebruiker gegenereerde inhoud [](/help/communities/translate-ugc.md) vertalen voor informatie over het configureren van een gelicentieerde vertaalservice voor AEM-gemeenschappen. Zie Inhoud [vertalen voor meertalige sites](/help/sites-administering/translation.md) voor een volledig overzicht.

![chlimage_1-161](assets/chlimage_1-161.png)

* **Schakel Machine Translation in voor de geselecteerde talen**. De talen die worden ingeschakeld voor machinevertaling, worden standaard ingesteld op de systeeminstelling die is opgegeven in de configuratie [voor](/help/communities/translate-ugc.md#translation-integration-configuration)vertaalintegratie. Deze standaardinstellingen kunnen voor deze site worden overschreven door standaardinstellingen te verwijderen en/of andere talen te selecteren in het keuzemenu.

* **Kies** standaard een vertaalprovider `microsoft`. Het servicebureau is een testservice die alleenvoor demonstraties wordt gebruikt. Als er geen licentie is voor een vertaalservicebureau, **moet de optie Machine Translation** toestaan zijn uitgeschakeld.

* **Kies de globale gedeelde opslag** Voor een website met veelvoudige taalexemplaren, verstrekt een globale gedeelde opslag één enkele draad van gesprek, zichtbaar van elke taalexemplaar. Dit wordt bereikt door een van de talen te selecteren die als een taalkopie worden opgenomen. De standaardinstelling is *Geen wereldwijde gedeelde opslag*.

* **Kies de configuratie** van de vertaalleverancierKies een kader [van de](/help/sites-administering/tc-tic.md) vertaalintegratie dat voor de vergunning gegeven vertaalleverancier wordt gecreeerd.

* **Selecteer de vertaalopties voor uw communitysite**

   * **Gehele pagina**vertalen Als deze optie is geselecteerd, wordt alle UGC op een pagina vertaald naar de basistaal van de pagina.
Standaard is *niet geselecteerd*.

   * **Alleen**Selectie vertalen Als u deze optie selecteert, wordt naast elke post een vertaaloptie weergegeven waarmee afzonderlijke posts kunnen worden vertaald in de basistaal van de pagina.
Standaard is *geselecteerd*.

* **Persistopties selecteren**

   * **Vertaal bijdragen op verzoek van de gebruiker en blijf daarna**Indien geselecteerd, wordt de inhoud niet vertaald tot een verzoek wordt gedaan. Nadat de vertaling is vertaald, wordt de vertaling opgeslagen in de opslagplaats.
Standaard is *niet geselecteerd*.

   * **Zet de vertalingen**niet voort Als deze optie is geselecteerd, worden de vertalingen niet opgeslagen in de opslagplaats.
Als deze optie niet is geselecteerd, blijven de vertalingen behouden.
Standaard is *niet geselecteerd*.

* **Slimme rendering** selecteren een van

   * `Always show contributions in the original language` (standaardwaarde)
   * `Always show contributions in user preferred language`
   * `Show contributions in user preferred language for only logged-in users`

#### UITSCHAKELING {#enablement}

![chlimage_1-162](assets/chlimage_1-162.png)

De `ENABLEMENT`montages zijn van toepassing wanneer het gekozen malplaatje van de communautaire plaats de [toewijzingsfunctie](/help/communities/functions.md#assignments-function)omvat, die beschikbaar is wanneer de enablement eigenschappen vergunning en [gevormd](/help/communities/enablement.md)zijn. De verwijzingsplaatssjabloon die de toewijzingsfunctie omvat is `Reference Structured Learning Site Template.`

* **Enablement Managers**(vereist) Slechts zijn de leden van de `Community Enablementmanagers` groep beschikbaar om worden geselecteerd om deze enablement gemeenschap te beheren. Enablement managers zijn verantwoordelijk voor het toewijzen van leden aan bronnen. Zie ook Gebruikers en gebruikersgroepen [beheren](/help/communities/users.md).

* **Org-id** voor marketingcloud (optioneel) De id voor een licentie voor [Videohartslag Analytics](/help/communities/analytics.md#video-heartbeat-analytics) .

Selecteer **Volgende**.

### Stap 4: Communitysite maken {#step-create-communities-site}

Als er aanpassingen nodig zijn, gebruikt u de knop **Terug ** om deze aan te brengen.

Nadat **Maken** is geselecteerd en gestart, kan het maken van de site niet worden onderbroken.

Nadat de site is gemaakt:

* wijzigen van de URL (knooppuntnaam) wordt niet ondersteund
* toekomstige wijzigingen van de sjabloon voor de communitysite hebben geen invloed op de gemaakte community-site
* het onbruikbaar maken van het malplaatje van de communautaire plaats zal niet de gecreeerde communautaire plaats beïnvloeden
* het is mogelijk de [STRUCTUUR](#modify-structure) van een communautaire plaats te bewerken door zijn eigenschappen te wijzigen

![chlimage_1-163](assets/chlimage_1-163.png)

Wanneer het proces is voltooid, wordt de map voor de nieuwe site weergegeven in de console Communitysites, waar auteurs pagina-inhoud kunnen toevoegen of waar beheerders de eigenschappen van de site kunnen wijzigen.

![chlimage_1-164](assets/chlimage_1-164.png)

Als u een communitysite wilt wijzigen, selecteert u de projectmap om deze te openen:

![site-1](assets/siteactions-1.png)

Wanneer u de muisaanwijzer op een site of een sitekaart plaatst, worden pictogrammen weergegeven waarmee u de site kunt [bewerken in de ontwerpmodus](#authoring-site-content), de site-eigenschappen kunt [openen voor wijziging](#modifying-site-properties), de site [kunt](#publishing-the-site)publiceren, de site [kunt](#exporting-the-site)exporteren en de site [kunt](#deleting-the-site)verwijderen.

## Site-inhoud ontwerpen {#authoring-site-content}

![chlimage_1-165](assets/chlimage_1-165.png)

De inhoud van een site kan met dezelfde gereedschappen worden gemaakt als elke andere AEM-website. Als u de site wilt openen voor ontwerpen, selecteert u het `Open Site` pictogram dat wordt weergegeven wanneer u de muis op de site plaatst. De site wordt op een nieuw tabblad geopend, zodat de console Communitysites toegankelijk blijft.

![chlimage_1-166](assets/chlimage_1-166.png)

>[!NOTE]
>
>Als u niet bekend bent met AEM, bekijkt u de documentatie over [basisverwerking](/help/sites-authoring/basic-handling.md) en een [handleiding voor het ontwerpen van pagina](/help/sites-authoring/qg-page-authoring.md)&#39;s.

## Site-eigenschappen wijzigen {#modifying-site-properties}

![chlimage_1-167](assets/chlimage_1-167.png)

De eigenschappen van een bestaande site die tijdens het maken van de site zijn opgegeven, kunnen worden gewijzigd door het `Edit Site`pictogram te selecteren dat met de muis op de site wordt weergegeven.

`Details of the following properties match the descriptions provided in the` Sectie [Site maken](#site-creation) .

![chlimage_1-168](assets/chlimage_1-168.png)

### Basis wijzigen {#modify-basic}

Met het BASIC-deelvenster kunt u

* Titel van gemeenschapssite
* Beschrijving van community-site

De naam van de communautaire site mag niet worden gewijzigd.

Het kiezen van een verschillend malplaatje van de communautaire plaats zou geen invloed op een bestaande communautaire plaats hebben aangezien geen verbinding tussen malplaatjes en plaatsen blijft.

In plaats daarvan kan de [STRUCTUUR](#modify-structure) van de site van de community worden gewijzigd.

### Structuur wijzigen {#modify-structure}

In het deelvenster STRUCTUUR kunt u de structuur wijzigen die oorspronkelijk is gemaakt op basis van de geselecteerde communitysitesjabloon. Vanuit het deelvenster kunt u

* aanvullende [gemeenschapsfuncties](/help/communities/functions.md) naar de sitestructuur slepen
* betreffende een communautaire functie in de sitestructuur:

   * **`gear icon`**
bewerkingsinstellingen, waaronder de weergavetoek en URL-naam*en [geprivilegieerde ledengroepen](/help/communities/users.md#privilegedmembersgroups)

   * **`trashcan icon`**
functies verwijderen (verwijderen) uit de sitestructuur

   * **`grid icon`**
de volgorde van functies wijzigen zoals deze wordt weergegeven op de navigatiebalk op hoofdniveau van de site

>[!NOTE]
>
>U kunt de volgorde van alle functies in de sitestructuur wijzigen, behalve van de functie bovenaan. Daarom kan de homepage van de plaats van gemeenschappen niet worden veranderd.

>[!CAUTION]
>
>* Hoewel de titel van de weergave zonder bijwerkingen kan worden gewijzigd, wordt het niet aangeraden de URL-naam te bewerken van een communautaire functie die bij een communautaire site hoort.
Als u bijvoorbeeld de naam van de URL wijzigt, wordt de bestaande UGC niet verplaatst, waardoor de UGC verloren gaat.

>[!CAUTION]
De groepfunctie moet *niet *de *eerste of enige* functie in de sitestructuur zijn.
Alle andere functies, zoals de [paginafunctie](/help/communities/functions.md#page-function), moeten worden opgenomen en als eerste worden vermeld.

#### Voorbeeld: Een catalogusfunctie toevoegen aan een community-sitestructuur {#example-adding-a-catalog-function-to-a-community-site-structure}

![chlimage_1-169](assets/chlimage_1-169.png)

### Ontwerp wijzigen {#modify-design}

In het deelvenster ONTWERP kunt u een nieuw thema toepassen:

* [Thema van communautaire site](#community-site-theme)
* [Gemeenschapsmerk](#community-site-branding)

   * schuiven naar de onderkant van het deelvenster om de merkafbeelding te wijzigen

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

Zie de beschrijving van [ENABLEMENT](#enablement) .

## De site publiceren {#publishing-the-site}

Nadat een communitysite net is gemaakt of gewijzigd, is het mogelijk om de site te publiceren (activeren) door het `Publish Site` pictogram te selecteren dat wordt weergegeven wanneer u de muisaanwijzer op de site plaatst.

![chlimage_1-170](assets/chlimage_1-170.png)

Er verschijnt een indicatie nadat de site is gepubliceerd.

![chlimage_1-171](assets/chlimage_1-171.png)

### Publiceren met geneste groepen {#publishing-with-nested-groups}

Na het publiceren van een communautaire plaats, is het noodzakelijk om elke subcommunity (genestelde groep) individueel te publiceren die gebruikend de console [van](/help/communities/groups.md)Groepen wordt gecreeerd.

## De site exporteren {#exporting-the-site}

![chlimage_1-172](assets/chlimage_1-172.png)

Selecteer het exportpictogram als u de muisaanwijzer op de site plaatst, om een pakket van de communitysite te maken dat zowel in [pakketbeheer](/help/sites-administering/package-manager.md) wordt opgeslagen als wordt gedownload.
UGC is niet opgenomen in het sitepakket.

## De site verwijderen {#deleting-the-site}

![deleteicon](assets/deleteicon.png)

Als u de communitysite wilt verwijderen, selecteert u het pictogram Site verwijderen dat verschijnt wanneer u de muisaanwijzer op de site in de Community Site Console plaatst. Met deze actie verwijdert u alle items die aan de site zijn gekoppeld, zoals UGC, gebruikersgroepen, elementen en databaserecords.

## Gemaakte gebruikersgroepen {#created-community-user-groups}

Zodra de nieuwe communautaire plaats wordt gepubliceerd, worden de nieuwe lidgroepen (gebruikersgroepen worden gecreeerd in publicatiemilieu) die de aangewezen toestemmingen hebben die voor diverse administratieve en lidrollen worden geplaatst.

De naam die voor de lidgroepen wordt gemaakt, bevat de *site-naam* die in [Stap 1](#step13asitetemplate) (de naam die in de URL wordt weergegeven) aan de site is gegeven, en een unieke id om conflicten te voorkomen met gemeenschapssites en groepen die dezelfde site-naam hebben voor verschillende lokale sites.

Als de naam bijvoorbeeld &quot;enter&quot; was voor een site met de naam &quot;Getting Started Tutorial&quot;, zou de gebruikersgroep voor moderatoren het volgende zijn:

* titel:Maatschappelijke experts
* name : community-*engid*-moderators

Bericht dat om het even welke leden rollen als moderatoren of groepsbeheerders terwijl het creëren van de plaats toewezen, aan de aangewezen groep zal worden toegewezen evenals aan de lidgroep toegewezen. Deze groepen en lidtoewijzingen worden gemaakt bij publicatie wanneer de nieuwe site wordt gepubliceerd.

Zie Gebruikers en gebruikersgroepen [](/help/communities/users.md)beheren voor meer informatie.

>[!NOTE]
Als aanmelden via sociaal netwerk [toestaan: Facebook](#user-management) is ingeschakeld, zodra de gebruikersgroep
* community-*&lt;site-name>*-*&lt;uid>*-members

is gemaakt, moet de toegepaste [Facebook-cloudservice](/help/communities/social-login.md#createafacebookcloudservice) zo worden geconfigureerd dat gebruikers aan deze groep worden toegevoegd.

## Configureren voor verificatiefout {#configure-for-authentication-error}

Standaard leidt een communitysite naar een voorbeeld van een aanmeldingspagina als de gebruiker de verkeerde gegevens heeft ingevoerd en zich niet heeft aangemeld. Deze voorbeeldaanmelding is niet aanwezig op een [productieserver](/help/sites-administering/production-ready.md).

Om correct om te leiden, zodra een plaats is gevormd en ertoe aangezet om te publiceren, voltooi deze stappen om authentificatiemislukking te krijgen om aan de communautaire plaats om te leiden:

* op elke publicatie-instantie van AEM
* eerste aanmelding met beheerdersrechten
* toegang tot de [webconsole](/help/sites-deploying/configuring-osgi.md)

   * bijvoorbeeld [https://localhost:4503/system/console/configMgr](https://localhost:4503/system/console/configMgr)

* lokaliseren `Adobe Granite Login Selector Authentication Handler`
* Selecteer het `pencil`pictogram om de configuratie voor bewerken te openen
* Voer een** Mappingen voor aanmeldingspagina** als volgt in:
/content/sites/*&lt;site-name>*/path/to/login/page**:**/content/sites/*&lt;site-name>*bijvoorbeeld:
/content/sites/*engame*/nl/signation:/content/sites/*commit*/nl

* Selecteer **Opslaan**

![chlimage_1-173](assets/chlimage_1-173.png)

### Omleiding van verificatie testen {#test-authentication-redirection}

Op zelfde AEM publiceert instantie die met een login paginaplaat voor de communautaire plaats wordt gevormd:

* naar de homepage van de website van de gemeenschap bladeren

   * bijvoorbeeld [https://localhost:4503/content/sites/engage/en.html](https://localhost:4503/content/sites/engage/en.html)

* Afmelden selecteren
* aanmelden selecteren
* Voer duidelijk onjuiste gegevens in, zoals gebruikersnaam &quot;x&quot; en wachtwoord &quot;x&quot;
* de aanmeldingspagina moet worden weergegeven met de fout &quot;Ongeldige aanmelding&quot;

![chlimage_1-174](assets/chlimage_1-174.png)

## Toegang tot communitysites vanuit de hoofdsiteconsole {#accessing-community-sites-from-main-sites-console}

Vanuit de globale console van navigatiesites bevinden de communitysites zich in de `Community Sites` map.

Terwijl het mogelijk is om tot een communautaire plaats op deze manier, voor administratieve taken toegang te hebben, zou de communautaire plaats van de console van de Plaatsen van Gemeenschappen moeten worden betreden.

![chlimage_1-175](assets/chlimage_1-175.png)

