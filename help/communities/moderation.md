---
title: Moderatieconsole
seo-title: Moderation Console
description: Hoe te om tot de console van de Moderatie toegang te hebben
seo-description: How to access the Moderation console
uuid: d3b8a160-85b2-43f4-9891-5fafa8c48c5f
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 404582ab-bb4c-4775-9ae3-17356d376dca
docset: aem65
role: Admin
exl-id: 829da16a-4083-43c1-857d-f2666b363bfc
source-git-commit: 1d334c42088342954feb34f6179dc5b134f81bb8
workflow-type: tm+mt
source-wordcount: '2040'
ht-degree: 1%

---

# Moderatieconsole {#moderation-console}

In AEM Communities, bulkgoederen [modernisering van de communautaire inhoud](/help/communities/moderate-ugc.md) is mogelijk van zowel auteur als publiceer milieu&#39;s door beheerders en communautaire moderatoren (vertrouwde op communautaire leden die als moderators worden toegewezen).

Beheerders en moderatoren van de gemeenschap kunnen ook [contextmatiging](/help/communities/in-context.md) in de publicatieomgeving.

Een kenmerk van alles [communitysites](/help/communities/sites-console.md) is een `Administration` menu-item beschikbaar voor gebruikers die zich aanmelden met beheerdersrechten. De `Administration` de verbinding verleent toegang tot de console van de Moderatie.

Van de console van de Moderatie, zullen de beheerders en de communautaire moderatoren toegang tot al gebruiker geproduceerde inhoud (UGC) hebben waarvoor zij toestemming hebben te matigen. Als u meerdere sites wilt gematigd, is het mogelijk om posten op alle sites weer te geven of door geselecteerde communitysites te filteren.

Voor meer informatie gaat u naar [Gebruikers en gebruikersgroepen beheren](/help/communities/users.md).

De console van de Moderatie steunt:

* Het uitvoeren van moderatietaken in bulk.
* Zoeken in UGC.
* UGC-details weergeven.
* UGC-auteurdetails weergeven.

Alleen bij aanmelding als beheerder of lid met ` [moderator permissions](/help/communities/in-context.md#identifyingtrustedmembers)`kan worden uitgevoerd.

## Toegang tot omgeving publiceren {#publish-environment-access}

De toegang tot de console van de Moderatie van een gepubliceerde communautaire plaats is door een verbinding van het Beleid die verschijnt wanneer een communautaire moderator binnen wordt ondertekend.

![uitgeverij](assets/publishweretail.png)

Door de verbinding van het Beleid te selecteren, verschijnt de console van de Moderatie:

![moderatie-console-publish](assets/moderation-console-publish.png)

## Toegang tot ontwerpomgeving {#author-environment-access}

In het auteursmilieu, om de console van de Moderatie te bereiken

* Selecteer bij globale navigatie de optie **[!UICONTROL Communities]** > **[!UICONTROL Moderation]**.

Alleen bij aanmelding als beheerder of als lid met [moderatormachtigingen](/help/communities/in-context.md#identifyingtrustedmembers), kunnen moderatietaken worden uitgevoerd. De enige inhoud van de gemeenschap die wordt weergegeven, is de inhoud die de ondertekenaar mag verkleinen.

>[!NOTE]
>
>UGC van het publicatiemilieu zal slechts op auteur zichtbaar zijn als gekozen SRP een gemeenschappelijke opslag uitvoert. De opslag is standaard bijvoorbeeld JSRP, wat geen algemene opslag is voor auteur en publiceren. Zie [Opslag van communautaire inhoud](/help/communities/working-with-srp.md).

![moderationconsoletoewijzing](assets/moderationconsoleauthor.png)

## Gebruikersinterface van aanpassingsconsole {#moderation-console-ui}

Afgezien van de linkse navigatiespoor (die bij auteur, maar niet bij publicatie verschijnt), heeft de moderatie UI de volgende belangrijkste gebieden:

* **[Bovenste navigatiebalk](#top-navigation-bar)**
* **[Werkbalk](#toolbar)**
* **[Inhoudsgebied](#content-area)**

### Bovenste navigatiebalk {#top-navigation-bar}

De bovenste navigatiebalk is voor alle consoles constant. Zie voor meer informatie [Basisverwerking](/help/sites-authoring/basic-handling.md).

### Werkbalk {#toolbar}

De werkbalk, die zich onder de bovenste navigatiebalk bevindt, biedt de volgende schakeloptie aan de linkerkant:

* [Filterrail](/help/communities/moderation.md#filterrail)
opent een rails waarin u de eigenschappen kunt kiezen waarop u de inhoud wilt filteren.

De werkbalk, die zich onder de bovenste navigatiebalk bevindt, biedt de volgende schakeloptie aan de linkerkant:

![toggleswitch](assets/toggleswitch.png)

[Filterrail](/help/communities/moderation.md#filterrail)
Hiermee opent u een rails bij het selecteren van Zoeken, zodat u kunt kiezen op welke eigenschappen u de inhoud wilt filteren.

![filterrail](assets/filterrail.png)

### Inhoudsgebied {#content-area}

Het inhoudsgebied bevat informatie voor gepost UGC:

* UGC geplaatst
* Lidnaam
* Member avatar
* Locatie van het bericht.
* Toen het werd gepost.
* Aantal reacties op de post.
* [Sentiment](/help/communities/moderate-ugc.md#sentiment) in verband met het bericht
* Indien goedgekeurd, wordt een vinkje getoond.
* Als er een bijlage is, wordt een paperclip weergegeven.

>[!NOTE]
> 
>Het inhoudsgebied bevat een *oneindig schuiven*, wat betekent dat u kunt blijven schuiven totdat u het einde van de inhoud hebt bereikt. De werkbalk blijft tijdens het schuiven op een vaste, zichtbare positie boven het inhoudsgebied staan.

### Rail filteren {#ootbfilters}

![open-filterrail](assets/open-filterrail.png)

Met het pictogram van het zijpaneel wordt de filterrail geopend. De filterrail, die links van het inhoudsgebied verschijnt, verstrekt verschillende filters, elk die een onmiddellijk effect op referenced UGC hebben die in het inhoudsgebied verschijnt.

De filters binnen elke categorie zijn **OF**&#39;d bij elkaar en de filters in verschillende categorieën zijn **EN**&#39;Samen.

Als u bijvoorbeeld beide incheckt **Vraag** en **Antwoord**, ziet u inhoud die een van de **Vraag** *of* een **Antwoord**.

Als u echter **Vraag** en **In behandeling**, ziet u alleen inhoud die een **Vraag** en is **In behandeling**.

>[!NOTE]
>
>De moderatoren van de Gemeenschap kunnen referentie de vooraf bepaalde filters op moderatieconsole UI. Aangezien deze filters aan het eind van URL (als parameters van het vraagkoord) worden toegevoegd, kunnen de moderatoren aan de bookmarked filters later terugkomen en deze verbindingen ook delen.

![zoekpictogram](assets/searchicon.png)

Wanneer de filterrail is geopend, schakelt het zoekpictogram de zijpaneel gesloten. Als u echter de filterrail wilt sluiten en alleen de door de gebruiker gegenereerde inhoud wilt weergeven, klikt u op het pictogram Zoeken en selecteert u de optie Alleen inhoud.

#### Inhoudspad {#content-path}

Met Inhoudspad wordt de referentie-UGC beperkt tot de posten die in de opgegeven opslagplaats voor inhoud zijn geplaatst.

![inhoudspad](assets/content-path.png)

#### Tekst zoeken {#text-search}

Bij zoeken naar tekst wordt de UGC waarnaar wordt verwezen, beperkt tot advertenties waarin de ingevoerde tekst voorkomt.

![tekst zoeken](assets/text-search.png)

#### Site {#site}

De site beperkt de UGC waarnaar wordt verwezen, tot advertenties aan geselecteerde communitysites. Als geen plaatsen worden gecontroleerd, dan worden alle verwijzingen naar UGC getoond.

![site-panel](assets/site-panel.png)

>[!NOTE]
>
>Wanneer de bulkmoderatieconsole door een beheerder wordt betreden, worden alle verwijzingen naar UGC getoond, met inbegrip van plaatsen niet gecreeerd met [wizard voor het maken van sites](/help/communities/sites-console.md), zoals de Geometrixx monsters.
>
>Wanneer de bulkmoderatieconsole bij publiceren door een vertrouwd communautair lid wordt betreden, dan slechts worden de verwijzingen naar UGC die voor communautaire plaatsen worden gecreeerd het lid aan gematigd wordt toegelaten getoond, en met de filter van de Plaats kunnen worden gefiltreerd.

#### Inhoudstype {#content-type}

Het Type van inhoud beperkt referenced UGC getoond aan posten van het geselecteerde middeltype. Een of meer van de volgende typen kunnen worden geselecteerd. Alle typen worden weergegeven als er geen is geselecteerd.

* **Opmerking**
* **Forum-onderwerp**
* **Forum Reageren**
* **Vraag QnA**
* **Antwoord vragen**
* **Blogartikel**
* **Blogopmerking**
* **Kalendergebeurtenis**
* **Opmerking kalender**
* **Map bestandsbibliotheek**
* **Document bestandsbibliotheek**
* **Idea**
* **Commentaar bij idee**

![inhoudstypen](assets/content-types.png)

#### Aanvullende inhoudstypen {#additional-content-types}

Aanvullende bronnen toevoegen waarop moet worden gefilterd:

* Meld u als beheerder aan bij de auteurinstantie.
* Openen [Webconsole](https://localhost:4502/system/console/configMgr).
* Zoeken `AEM Communities Moderation Dashboard Filters`.
* Selecteer de configuratie die u wilt openen in de bewerkingsmodus.
* Ga ResourceType van een component in waarop te filtreren:

   * Als u bijvoorbeeld wilt filteren op opgenomen stemcomponenten, voert u het volgende in:

      `Voting=social/tally/components/hbs/voting`
   ![extra-contenttype](assets/additional-contenttype.png)

* Selecteer Opslaan.
* Vernieuw de Gemeenschappen - de console van de Moderatie.

Het resultaat is een nieuw selecteerbaar filter voor `Voting` onder de `Content Type` filtergroep.

Wanneer dat filter wordt geselecteerd zal de inhoud van het dashboard UGC tonen die om het even welke ingevoerde ResourceTypes aanpast.

#### Status {#status}

De status beperkt de UGC waarnaar wordt verwezen, tot posten van de geselecteerde status, die één of meer van In behandeling, Goedgekeurd, Afgewezen of Gesloten, evenals Ontwerp of Gepland voor Blogartikelen, en Beantwoord of niet Beantwoord voor Vragen QnA kan zijn. Als geen wordt geselecteerd, dan worden allen getoond.

>[!NOTE]
>
>Als slechts de niet Beantwoorde status wordt geselecteerd, dan zal de moderator al inhoud (voor alle inhoudstypes) behalve de beantwoorde vragen zien. Dit komt omdat de eigenschap die verantwoordelijk is voor de beantwoorde vraag niet bestaat in het geval van niet-beantwoorde vragen en andere inhoud zoals het onderwerp van het forum, het blogartikel of opmerkingen.

![statussen](assets/statuses.png)

#### Markering {#flagging}

Als u een vlag voert, wordt de UGC waarnaar wordt verwezen, beperkt tot publicaties die zijn gemarkeerd of verborgen.

Wanneer een stuk inhoud is gemarkeerd, blijft het gemarkeerd totdat u de markering van dat stuk inhoud ongedaan maakt door de optie **Markering** nogmaals. Er zijn geen markeringsniveaus, zoals belangrijk of opgevolgd.

![vlaggen](assets/flagging.png)

#### Leden {#members}

Leden beperken de UGC waarnaar wordt verwezen, die aan UGC wordt weergegeven en die door de ingevoerde lidnaam is gepost.

![leden](assets/members.png)

#### Gepost in de laatste {#posted-in-the-last}

Gepost in de Laatste grenzen UGC van verwijzingen aan posten die in het laatste uur, de dag, de week, de maand, of het jaar worden getoond.

![gepost-laatst](assets/posted-last.png)

#### Sentiment {#sentiment}

[Sentiment](/help/communities/moderate-ugc.md#sentiment) beperkt de UGC waarnaar wordt verwezen, tot posten met een sentiment-waarde die positief, negatief of neutraal is.

![sentiment](assets/sentiment.png)

## Aangepaste filters {#custom-filters}

Behalve de filters uit de doos in [Rail filteren](/help/communities/moderation.md#ootbfilters)aanvullende aangepaste filters voor metagegevens kunnen worden toegevoegd aan de moderatie-interface. De ontwikkelaars kunnen de steekproefcode in Github gebruiken om de bestaande filters van moderatie UI uit te breiden.

![custom-tag-filter](assets/custom-tag-filter.png)

De [voorbeeldproject](https://github.com/Adobe-Marketing-Cloud/aem-communities-extensions/tree/main/aem-communities-moderation-filter) op Github implementeert het filter Tag om de UGC-lijst te filteren op basis van of de specifieke tags worden toegepast op door de gebruiker gegenereerde inhoud. U kunt de voorbeeldcode volgen en analoge filters voor andere vergelijkbare UGC-metagegevensvelden maken.

Het voorbeeld voor het filter Codes installeren:

1. Pakketbeheer openen op AEM-auteur (`https://[aem-author]:4502/crx/packmgr/index.jsp`) en AEM-publicatie (`https://[aem-publish]:4503/crx/packmgr/index.jsp`).
1. Het pakket maken `com.adobe.social.sample.moderation.filter.ui.apps-1.0-SNAPSHOT.zip` uit Github-code, en installeer en schakel dezelfde optie in.
1. De bundelconsole openen op AEM Author ( `https://[aem-author]:4502/system/console/bundles`) en AEM-publicatie ( `https://[aem-publish]:4503/system/console/bundles`).
1. Het pakket maken (`[com](https://sample-moderation-filter.com/).adobe.social.sample.moderation.filter.core-1.0-SNAPSHOT.jar`) van Github, installeren en inschakelen.
1. Ga naar **/apps/social/moderation/facets** knooppunt op AEM-auteur (`https://[aem-author]:4502/crx/de/index.jsp#/apps/social/moderation/facets`) en AEM-publicatie (`https://[aem-publish]:4502/crx/de/index.jsp#/apps/social/moderation/facets`).
1. Een technische gebruiker toevoegen **gemeenschappen-nutsbedrijven-lezer** with `jcr:read` machtigingen.

Aangepaste filters beschikbaar maken op bestaande communautaire sites:

1. Bewerken `Clientlibs` van bestaande moderniseringspagina `/content/we-retail/us/en/community/moderation/shell3/jcr:content/head/clientlibs.`

   * Nieuwe categorie toevoegen `cq.social.hbs.moderation.v2.`

1. Ga naar `/content/we-retail/us/en/community/moderation/shell3/jcr:content/rails/searchWell/items/filters.`

   * Instellen op nieuwe component `sling:resourceType = social/moderation/v2/filters.`

1. Ga naar `/content/we-retail/us/en/community/moderation/shell3/jcr:content/views/content/items/modcontainer`.

   * Instellen op nieuwe component `sling:resourceType = social/moderation/v2/modcontainer`.

## Moderatiehandelingen {#moderation-actions}

[Moderniseringsacties](/help/communities/moderate-ugc.md#moderation-actions) kan worden uitgevoerd op een of meer selecties die in het inhoudsgebied zijn gemaakt of wanneer u de details van de inhoud weergeeft.

Klik in het inhoudsgebied op Selecteren (![selecticon](assets/selecticon.png)) op een post, die verschijnt als u de muisaanwijzer (bureaublad) op het desbetreffende artikel plaatst of met een vinger op het betreffende artikel (mobiel) drukt. Op deze manier opent u de multiselectiemodus en kunt u nu de volgende posts selecteren die bulksgewijs moeten worden gemodereerd door er gewoon op te klikken. Gebruik de knoppen op de werkbalk om moderatiehandelingen uit te voeren op de geselecteerde posten. Alle acties worden ter bevestiging voorgelegd.

Als u één artikel in het inhoudsgebied wilt gematigd, houdt u de muisaanwijzer (bureaublad) of drukt u met een vinger op de post (mobiel), zodat er knoppen op de post verschijnen. Als u op één inhoudsgegeven werkt, wordt alleen een verwijderactie ter bevestiging verzonden.

### Meerdere posts modereren {#moderating-multiple-posts}

U opent de modus voor bulkselectie door op de knop `Select` pictogram op een bericht:

![select-icon](assets/select-icon.png)

Als u de modus voor bulkselectie wilt afsluiten, selecteert u het pictogram voor annuleren (x) op de werkbalk:

De moderniseringsacties die op meerdere posten kunnen worden uitgevoerd zijn:

* Weigeren
* Verwijderen
* De berichten sluiten/opnieuw openen

De pictogrammen voor deze handelingen worden alleen op de werkbalk weergegeven als er meerdere posts zijn geselecteerd.

![paars](assets/bulkmoderate.png)

### Eén artikel moderniseren {#moderating-a-single-post}

In de enkelvoudige selectiemodus is het mogelijk:

* Geef gebruikersgegevens weer door de gebruikersnaam te selecteren.
* Klik op de link naar het bericht in de context om het bericht te bekijken.
* [Reageren](#reply)
* [Toestaan](#allow)
* [Weigeren](#deny)
* [Verwijderen](#delete)
* [Sluiten](#close)
* Weergave [Moderatiegeschiedenis](#moderation-history)
* [Details weergeven](#viewdetails)

De tekst van de post op de kaartweergave boven de mageractiepictogrammen is de tekst van de post en hieronder staan de gegevens die aangeven:

* Indien de Commissie antwoord heeft, en zo ja, voorafgegaan door het aantal antwoorden.
* Als het is gemarkeerd.
* Indien goedgekeurd.
* Toen de UGC werd geplaatst.

![singleElectmode](assets/singleselectmode.png)

#### Reageren {#reply}

![antwoord](assets/reply.png)

Wanneer het werken met één enkele post, zal een pictogram van het Antwoord verschijnen als het type UGC antwoorden steunt en wordt gevormd om antwoorden toe te staan.

#### Toestaan {#allow}

![toestaan](assets/allow.png)

Wanneer u met één bericht werkt, wordt het pictogram Toestaan weergegeven wanneer de advertentie is gemarkeerd of geweigerd. Als deze optie is gemarkeerd, worden alle markeringen gewist als u Toestaan selecteert.

#### Weigeren {#deny}

![ontkennen](assets/deny.png)

De **Weigeren** matigheidsactie is slechts beschikbaar voor inhoud die wordt gematigd, en niet op ongematigde inhoud behalve in multi-selectiemodus verschijnt.

Inhoud die niet wordt gematigd, wordt altijd goedgekeurd.

De inhoud die aanvankelijk wordt gematigd gaat een Hangende staat in, en kan later worden gewijzigd om worden goedgekeurd of worden ontkend.

Inhoud die de status in behandeling verlaat, kan nooit terugkeren naar een status in behandeling. Inhoud die is gemarkeerd als goedgekeurd of geweigerd, kan op elk gewenst moment worden gewijzigd in een andere status.

#### Verwijderen {#delete}

![delete](assets/delete.png)

In de modus Enkel selecteren of Samenvoegen kunt u items selecteren en verwijderen. De verwijderactie leidt tot een bevestigingsvenster. Als deze items eenmaal zijn verwijderd, verdwijnen ze direct uit het inhoudsgebied. **Zodra UGC wordt geschrapt, wordt het permanent verwijderd uit de bewaarplaats en kan later niet worden teruggewonnen**.

#### Sluiten {#close}

![close](assets/close.png)

Wanneer u met één artikel werkt, wordt een pictogram Sluiten weergegeven als het type UGC de mogelijkheid ondersteunt om verdere posten voor die bron te voorkomen.

#### Moderatiegeschiedenis {#moderation-history}

![matiging](assets/moderation.png)

Wanneer u met één bericht werkt, wordt een pictogram Moderatiegeschiedenis weergegeven wanneer u de muisaanwijzer op de desbetreffende post plaatst. Als u het pictogram selecteert, wordt een deelvenster weergegeven met een overzicht van de acties die met betrekking tot de UGC-post zijn uitgevoerd.

Als u wilt terugkeren naar de weergave van het inhoudsgebied van meerdere UGC-posten, selecteert u de X in de rechterbovenhoek van het deelvenster met weergavedetails.

Bijvoorbeeld:

![gematigdheid in de geschiedenis](assets/moderation-history.png)

#### Details weergeven {#view-detail}

![weergave](assets/view.png)

Als u met één artikel werkt, kunt u meer details bekijken door de UGC in de detailmodus te openen.

Houd hiertoe de muisaanwijzer boven de post om de `View Detail` en selecteert u deze om een deelvenster weer te geven met meer details over de advertentie.

Als u wilt terugkeren naar de weergave van het inhoudsgebied van meerdere UGC-posten, selecteert u de X in de rechterbovenhoek van het deelvenster met weergavedetails.

Bijvoorbeeld:

![view1](assets/view1.png)
