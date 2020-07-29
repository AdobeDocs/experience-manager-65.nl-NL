---
title: Ervaar de gepubliceerde site
seo-title: Ervaar de gepubliceerde site
description: Naar een gepubliceerde site bladeren
seo-description: Naar een gepubliceerde site bladeren
uuid: 44594e9e-27ad-475d-953d-3611b04f0df8
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: introduction
content-type: reference
discoiquuid: dd0cbc05-a361-46bc-b9f1-d045f8f23890
docset: aem65
translation-type: tm+mt
source-git-commit: bd9abe033216a00b93b2098e12b100ad478a8d08
workflow-type: tm+mt
source-wordcount: '1202'
ht-degree: 0%

---


# Ervaar de gepubliceerde site {#experience-the-published-site}

## Bladeren naar nieuwe site bij publicatie {#browse-to-new-site-on-publish}

Nu de nieuwe site voor gemeenschappen is gepubliceerd, bladert u naar de URL die wordt weergegeven bij het maken van de site, maar naar de publicatieserver, bijvoorbeeld:

* Auteur-URL = https://localhost:4502/content/sites/engage/en.html
* URL publiceren = https://localhost:4503/content/sites/engage/en.html

Om verwarring over welk lid bij auteur en publicatie is aangemeld, te minimaliseren, wordt aangeraden voor elke instantie verschillende browsers te gebruiken.

Wanneer de bezoeker van de site voor het eerst op de gepubliceerde site aankomt, is deze doorgaans nog niet aangemeld en is de site anoniem.

`https://localhost:4503/content/sites/engage/en.html {#http-localhost-content-sites-engage-en-html}`

![chlimage_1-31](assets/chlimage_1-31.png)

## Anonieme sitebezoeker {#anonymous-site-visitor}

Een anonieme sitebezoeker ziet het volgende in de gebruikersinterface:

* Titel van de site (zelfstudie Aan de slag)
* Geen profielkoppeling
* Geen berichtenkoppeling
* Geen koppeling voor meldingen
* Zoekveld
* Aanmeldingskoppeling
* De merkbanner
* Menukoppelingen voor de componenten die zijn opgenomen in het referentiesjabloon voor sites.

Als u verschillende koppelingen selecteert, bevindt de modus Alleen-lezen zich.

### Anonieme toegang tot JCR voorkomen {#prevent-anonymous-access-on-jcr}

Een bekende beperking stelt de inhoud van de communautaire plaats aan anonieme bezoekers door jcr inhoud en json bloot, hoewel het **toestaan van anonieme toegang** voor de inhoud van de plaats wordt onbruikbaar gemaakt. Nochtans, kan dit gedrag worden gecontroleerd gebruikend de Beperkingen van het Schuiven als oplossing.

Voer de volgende stappen uit om de inhoud van uw site te beschermen tegen toegang door anonieme gebruikers via jcr-inhoud en json:

1. Ga bij AEM Author-instantie naar https:// hostname:port/editor.html/content/site/sitename.html.

   >[!NOTE]
   >
   >Ga niet naar de gelokaliseerde site.

1. Ga naar **Pagina-eigenschappen**.

   ![page-eigenschappen](assets/page-properties.png)

1. Ga naar het tabblad **Geavanceerd** .

1. Schakel **verificatievereiste** in.

   ![plaatsverificatie](assets/site-authentication.png)

1. Voeg het pad van de aanmeldingspagina toe. Bijvoorbeeld: **/content/......./GetStarted**.
1. Publiceer de pagina.

## Vertrouwd lid van de Gemeenschap {#trusted-community-member}

Deze ervaring veronderstelt [Aaron McDonald](/help/communities/tutorials.md#demo-users) de rol van [gemeenschapsleider en moderator](/help/communities/create-site.md#roles)werd toegewezen. Als dat niet het geval is, gaat u terug naar de auteursomgeving om de site-instellingen [te](/help/communities/sites-console.md#modifying-site-properties) wijzigen en selecteert u Aaron McDonald als gemeenschapsbeheerder en moderator.

Selecteer en onderteken in de rechterbovenhoek met gebruikersnaam (aaron.mcdonald@mailinator.com) en wachtwoord (wachtwoord). `Log in` Meld u aan met de Twitter- of Facebook-referenties.

![chlimage_1-32](assets/chlimage_1-32.png)

Zodra u bent aangemeld als lid van de geregistreerde gemeenschap, ziet u de volgende menu-items om op uw communitysite te klikken en deze te verkennen:

* **Met de optie Profiel** kunt u uw profiel weergeven en bewerken.
* [De optie Berichten](/help/communities/configure-messaging.md) geeft u de opdracht om een berichtensectie te sturen, waar u:

   1. Bekijk de directe berichten die u hebt ontvangen (Postvak IN), verzonden (Items verzenden) en verwijderd (Prullenbak).
   1. Stel nieuwe directe berichten samen om naar individuen en groepen te verzenden.

* [De optie Meldingen](/help/communities/notifications.md) geeft u de opdracht om de sectie Meldingen te openen waarin u uw belangwekkende gebeurtenissen kunt bekijken en de berichtinstellingen kunt bewerken.
* [Het beleid](/help/communities/published-site.md#moderationlink) leidt u aan de Pagina van de Moderatie van AEM Communities, als u moderatievoorrechten hebt.

![chlimage_1-33](assets/chlimage_1-33.png)

U ziet dat de kalenderpagina de startpagina is omdat de gekozen Sjabloon Referentie-site eerst de kalenderfunctie bevatte, gevolgd door de functie Activiteitenstroom, de functie Forum, enzovoort. Deze structuur is zichtbaar van de console van het Malplaatje [van de](/help/communities/sites.md#edit-site-template) Plaats of wanneer het wijzigen van plaatseigenschappen in het auteursmilieu:

![chlimage_1-34](assets/chlimage_1-34.png)

>[!NOTE]
>
>Voor meer informatie over de onderdelen en functies van de Gemeenschappen gaat u naar:
>
>* [Community Components](/help/communities/author-communities.md) (voor auteurs)
>* [Component, Function en Feature Essentials](/help/communities/essentials.md) (voor ontwikkelaars)

>



### Forum-koppeling {#forum-link}

U kunt de standaardfunctie voor forums weergeven door de koppeling Forum te selecteren.

Leden kunnen een nieuw onderwerp plaatsen of een onderwerp volgen.

Sitebezoekers kunnen artikelen weergeven en op verschillende manieren sorteren.

![chlimage_1-35](assets/chlimage_1-35.png)

### Groepen koppelen {#groups-link}

Aangezien Aaron een groepsbeheerder is, zal het selecteren van de verbinding van Groepen Aaron toestaan om een nieuwe communautaire groep tot stand te brengen door een groepsmalplaatje, beeld te selecteren, of de groep open of geheim is, en het uitnodigen van leden.

Dit is een voorbeeld waarin een groep wordt gemaakt in de publicatieomgeving.

Groepen kunnen ook in de auteursomgeving worden gecreeerd en binnen de communautaire plaats in het auteursmilieu (de console[van](/help/communities/groups.md)Communautaire Groepen) worden beheerd. In deze zelfstudie wordt vervolgens uitgelegd hoe u groepen [kunt maken over de auteur](/help/communities/nested-groups.md) .

![classic-ui](assets/classic-ui.png)

Een referentiegroep maken:

1. Nieuwe **groep selecteren**
1. **Het tabblad Instellingen**

   * Groepsnaam: `Sports`
   * Beschrijving : `A parent group for various sporting groups`.
   * Groepsnaam URL: `sports`
   * Selecteren `Open Group` (lid van gemeenschap toestaan om deel te nemen door lid te worden)

1. **Tabblad Sjabloon**

   * Selecteren `Reference Group` (bevat een groepfunctie in de structuur om geneste groepen toe te staan)

1. Groep **maken selecteren**

![classic-ui-website](assets/classic-ui-website.png)

Nadat er een nieuwe groep is gemaakt, **selecteert u de nieuwe groep** Sport om er twee (geneste) groepen in te maken. Aangezien een sitestructuur niet kan beginnen met de groepsfunctie, moet u na het openen van de Sportgroep de koppeling Groepen selecteren:

![classic-ui-create-page](assets/classic-ui-create-page.png)

De tweede set koppelingen, die begint met `Blog`, behoort tot de geselecteerde groep, de `Sports` groep. Door de verbinding van Sport te selecteren `Groups` , is het mogelijk om twee groepen binnen de groep van Sport te nesten.

Voeg er bijvoorbeeld twee toe `new groups`.

* Eén naam `Baseball`

   * Laat deze ingesteld staan als een `Open Group` (vereist lidmaatschap).
   * Selecteer op het tabblad Sjablonen de optie `Conversational Group`.

* Eén naam `Gymnastics`

   * Wijzig de instelling in `Member Only Group` (beperkt lidmaatschap).
   * Selecteer op het tabblad Sjablonen de optie `Conversational Group`.

**Opmerking**:

* Mogelijk moet de pagina worden vernieuwd voordat beide groepen worden weergegeven.
* Deze sjabloon bevat *niet* de groepfunctie, dus het nesten van groepen is niet meer mogelijk.
* Op auteur, verstrekt de console [van](/help/communities/groups.md) Groepen een derde keus - een `Public Group` (facultatief lidmaatschap).

Nadat beide groepen zijn gemaakt, selecteert u de Baseball-groep, een open groep en ziet u de koppelingen:

`Discussions` `What's New` `Members`

De koppelingen van de groep worden weergegeven onder de koppelingen van de hoofdsite en resulteren in de volgende weergave:

![classic-ui-website-page](assets/classic-ui-website-page.png)

Op auteur - met administratieve voorrechten, navigeer aan de console [van de Groepen van](/help/communities/members.md) Gemeenschappen en voeg Weston McCall aan de `Community Engage Gymnastics <uid> Members` groep toe.

Als u doorgaat met publiceren, meldt u zich af als Aaron McDonald en bekijkt u de groepen in de Sports Group als anonieme bezoeker van de site:

* Van homepage
* Koppeling `Groups` selecteren
* Koppeling `Sports` selecteren
* De `Groups` koppeling Sport selecteren

Alleen de Baseball-groep is zichtbaar.

Meld u aan bij Weston McCall (weston.mccall@dodgit.com / wachtwoord) en navigeer naar dezelfde locatie. Het is bekend dat Weston in staat is om `Join` de open `Baseball` groep en ook `enter or Leave` de particuliere `Gymnastics` groep te vormen.

![classic-ui-repository-view](assets/classic-ui-repository-view.png)

### Koppeling naar webpagina {#web-page-link}

Selecteer de koppeling Webpagina om de basiswebpagina weer te geven die in de site is opgenomen. U kunt de standaardinstellingen AEM de ontwerpgereedschappen gebruiken om inhoud aan deze pagina toe te voegen in de ontwerpomgeving.

Ga bijvoorbeeld naar de **auteur** -instantie, open de `engage` map in de console [](/help/communities/sites-console.md)Communitysites en selecteer het pictogram Site **** openen om de modus Schrijfbewerking te openen. Selecteer vervolgens de voorvertoningsmodus om de `Web Page` koppeling te selecteren en selecteer vervolgens de bewerkingsmodus om titel- en tekstcomponenten toe te voegen. Ten slotte publiceert u alleen de pagina of de hele site opnieuw.

![classic-ui-repository-path](assets/classic-ui-repository-path.png)

### Moderniseringskoppeling {#moderationlink}

Wanneer het communautaire lid moderatievoorrechten heeft, dan zal de verbinding van de Moderatie zichtbaar zijn en het selecteren zal het geposte communautaire inhoud tonen en het toestaan om op een manier te worden [gematigd](/help/communities/moderate-ugc.md) gelijkend op de [moderatieconsole](/help/communities/moderation.md) in het auteursmilieu.

Gebruik de knop Vorige van de browser om terug te keren naar de gepubliceerde site. De meeste consoles zijn niet toegankelijk via globale navigatie in de publicatieomgeving. [](/help/communities/moderate-ugc.md)

![chlimage_1-42](assets/chlimage_1-42.png)

## Zelfregistratie {#self-registration}

Nadat u zich hebt afgemeld, kunt u een nieuwe gebruikersregistratie maken.

* Selecteer `Log In`
* Selecteer `Sign up for a new account`

![chlimage_1-43](assets/chlimage_1-43.png) ![chlimage_1-44](assets/chlimage_1-44.png)

Standaard is het e-mailadres de aanmeldings-id. Als deze optie is uitgeschakeld, kan de bezoeker zijn of haar eigen aanmeldings-id (gebruikersnaam) invoeren. De gebruikersnaam moet uniek zijn in de publicatieomgeving.

Als u de naam, het e-mailadres en het wachtwoord van de gebruiker hebt opgegeven, `Sign Up` wordt de gebruiker gemaakt en kunnen deze worden ondertekend.

Nadat u zich hebt aangemeld, is de eerste pagina die wordt weergegeven de bijbehorende `Profile` pagina, die ze zelf kunnen aanpassen.

![chlimage_1-45](assets/chlimage_1-45.png)

Als het lid zijn aanmeldings-id vergeet, wordt het e-mailadres gebruikt.

![chlimage_1-46](assets/chlimage_1-46.png)

