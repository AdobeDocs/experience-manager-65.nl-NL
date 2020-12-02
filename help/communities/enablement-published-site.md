---
title: Ervaar de gepubliceerde site
seo-title: Ervaar de gepubliceerde site
description: Naar een gepubliceerde site bladeren om deze in te schakelen
seo-description: Naar een gepubliceerde site bladeren om deze in te schakelen
uuid: 1bfefa8a-fd9c-4ca8-b2ff-add79776c8ae
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: introduction
content-type: reference
discoiquuid: 26715b94-e2ea-4da7-a0e2-3e5a367ac1cd
translation-type: tm+mt
source-git-commit: f375b40c084ee363757b78c602091f38524b8b03
workflow-type: tm+mt
source-wordcount: '1210'
ht-degree: 0%

---



# Geniet van de gepubliceerde site {#experience-the-published-site}


**[⇐ maken en toewijzen van Enablement-bronnen](resource.md)**

## Bladeren naar nieuwe site bij publicatie {#browse-to-new-site-on-publish}

Nu de nieuwe site van de community en de bijbehorende bronnen en leerpaden zijn gepubliceerd, is het mogelijk om de zelfstudie Enablement te ervaren.

Begin door naar de weergegeven URL te bladeren wanneer u de site maakt, maar op de publicatieserver, bijvoorbeeld

* Auteur-URL = [http://localhost:4502/content/sites/enable/en.html](http://localhost:4502/content/sites/enable/en.html)
* URL publiceren = [http://localhost:4503/content/sites/enable/en.html](http://localhost:4503/content/sites/enable/en.html)

Als de [standaardstartpagina is ingesteld](enablement-create-site.md#changethedefaulthomepage), moet u de site starten door naar [http://localhost:4503/](http://localhost:4503/) te bladeren.

Wanneer de bezoeker van de site voor het eerst op de gepubliceerde site aankomt, is deze doorgaans nog niet aangemeld en is de site anoniem.

**http://localhost:4503/content/sites/enable/en.html**

![enablement-login](assets/enablement-login.png)

## Anonieme sitebezoeker {#anonymous-site-visitor}

Een anonieme sitebezoeker wordt direct de aanmeldingspagina voor deze persoonlijke communitysite voor activering getoond. Er is geen optie voor zelfinschrijving of aanmelden bij Facebook of Twitter.

Deze homepage bevat vier menu-items: `Assignments, Ski Catalog, What's New` en `Discussions`, maar geen kan worden bereikt zonder het ondertekenen binnen.

>[!NOTE]
>
>Het is mogelijk anonieme toegang tot een enablement-site te verlenen zonder bezoekers van de site toe te staan zich te registreren.
>
>Als een enablement-bron is ingesteld op `show in catalog` en `allow anonymous access`, kunnen anonieme sitebezoekers bronnen in de catalogus weergeven.

### Anonieme toegang tot JCR {#prevent-anonymous-access-on-jcr} voorkomen

Een bekende beperking stelt de inhoud van de site van de community aan anonieme bezoekers beschikbaar via jcr-inhoud en json, hoewel **[!UICONTROL allow anonymous access]** is uitgeschakeld voor de inhoud van de site. Nochtans, kan dit gedrag worden gecontroleerd gebruikend de Beperkingen van het Schuiven als oplossing.

Voer de volgende stappen uit om de inhoud van uw site te beschermen tegen toegang door anonieme gebruikers via jcr-inhoud en json:

1. Ga AEM auteur naar https://&lt;host>:&lt;port>/editor.html/content/site/&lt;sitename>.html.

   >[!NOTE]
   >
   >Ga niet naar de gelokaliseerde site.

1. Ga naar **[!UICONTROL Page Properties]**.

   ![page-eigenschappen](assets/page-properties.png)

1. Ga naar **[!UICONTROL Advanced]** tabblad.
1. **[!UICONTROL Authentication Requirement]** inschakelen.

   ![plaatsverificatie](assets/site-authentication.png)

1. Voeg het pad van de aanmeldingspagina toe. Bijvoorbeeld, `/content/......./GetStarted`.
1. Publiceer de pagina.

## Ingeschreven lid {#enrolled-member}

Deze ervaring is gebaseerd op het feit dat gebruikers `Riley Taylor` en `Sidney Croft` zijn gemaakt [en [toegewezen](resource.md#settings) hebben aan het *Ski Lessen* leerpad door hun lidmaatschap in de *Community Ski Class* groep.](enablement-setup.md#publishcreateenablementmembers)

Aanmelden met

* `Username: riley`
* `Password: password`

Als het gebruikersprofiel niet door zelfregistratie werd gecreeerd, wordt de zeer eerste keer een lid binnen ondertekent, hun pagina van het Profiel getoond zodat kunnen zij het verifiëren en wijzigen zonodig.

De volgende keer dat het lid inlogt, wordt de homepage, die door het eerste menupunt wordt geïdentificeerd, getoond.

![chlimage_1-434](assets/chlimage_1-434.png)

### Toewijzingen {#assignments}

De pagina van Toewijzingen is waar het lid alle het leren wegen en enablement middelen wordt getoond die specifiek aan hen worden toegewezen.

Elke toewijzing bevat basisinformatie over:

* Het type toewijzing
* Of het een nieuwe Toewijzing is
* De naam
* Bijzonderheden die relevant zijn voor het soort toewijzing
* Contactpersoon, deskundige en auteur van toewijzing (indien opgegeven)

Het type toewijzing wordt aangegeven met een pictogram in de linkerbovenhoek van de kaart. Het beeld van een weg is voor een het leren weg met het aantal inbegrepen enablement middelen.

![chlimage_1-435](assets/chlimage_1-435.png)

Als u *Ski Lessen* selecteert, worden de twee bronnen voor activering weergegeven waarnaar door het leerpad wordt verwezen.

![chlimage_1-436](assets/chlimage_1-436.png)

Als u *Ski Les 1* selecteert, wordt de detailpagina van de Enablement resource geopend.

Van de detailpagina, kan het lid leren, [rate](rating.md) de les en [commentaren toevoegen](comments.md). Om het even welke lidactiviteit zal in wat worden weerspiegeld Nieuw gedeelte van de plaats.

De interactie met het enablement middel zal in de sectie van het Rapport worden genoteerd die in het auteursmilieu toegankelijk is.

![chlimage_1-437](assets/chlimage_1-437.png)

### Ski-catalogus {#ski-catalog}

De pagina van de Catalogus van het Ski is de catalogus van enablement middelen die met markeringen van `Tutorial` namespace worden geëtiketteerd. De twee *Ski Les* middelen worden geëtiketteerd met de `Skiing` markering, dusdanig dat als om het even welke markeringen buiten `All` of `Tutorial: Sports / Skiing` wordt geselecteerd, niets wordt getoond.

Wanneer aan een lid geen middelen van toelage, of direct of door een het leren weg is toegewezen, is het mogelijk om met enablement middelen in een catalogus in wisselwerking te staan en terugkoppelen door commentaren en classificaties te verstrekken.

![chlimage_1-438](assets/chlimage_1-438.png)

### Discussies {#discussions}

Naast het beoordelen van en het becommentariëren over enablement middelen ([indien toegelaten](enablement-create-site.md#step33asettings)), omvat het malplaatje van de communautaire plaats waarvan `Enablement Tutorial` werd gecreeerd [forumfunctie](functions.md#forum-function) (titel is `Discussions)`.

Selecteer `Discussions`verbinding en post een onderwerp.

Meld u af en meld u aan als Sidney Croft (sidney/password) en beantwoord de vraag en volg het onderwerp.

Het bericht, naast gealigneerde matiging, zijn er opties om het onderwerp op sociale media te delen of het onderwerp te e-mailen.

![chlimage_1-439](assets/chlimage_1-439.png)

### Wat is er nieuw?{#what-s-new}

Het menu-item `What's New` is de titel die is gegeven aan de functie [activity stream](functions.md#activity-stream-function) in de structuur van deze communitysite.

Nog steeds aangemeld als Sidney, selecteert u de `What's New`-koppeling om de activiteit weer te geven.

![chlimage_1-440](assets/chlimage_1-440.png)

## Vertrouwd communautair lid {#trusted-community-member}

Deze ervaring veronderstelt ` [Quinn Harper](enablement-setup.md#publishcreateenablementmembers)` de rollen van [moderator](enablement-create-site.md#moderation) en [middelcontact](resource.md#settings) werd toegewezen.

Aanmelden met

* `Username: quinn`
* `Password: password`

Zodra ondertekend binnen, merk op is er een nieuw menupunt, `Administration`, dat verschijnt omdat het lid de rol van moderator werd gegeven.

![chlimage_1-441](assets/chlimage_1-441.png)

De homepage wordt geïdentificeerd door het eerste menupunt, Toewijzingen. Quinn is de moderator en enablement middelcontact en werd niet ingeschreven in om het even welke enablement middelen of het leren wegen, en zodat is er niets aan vertoning.

### Beheer {#administration}

Er is activiteit van de twee studenten, `Riley Taylor` en `Sidney Croft`. Door de `Administration` verbinding te selecteren om tot de Console van de Moderatie toegang te hebben, kan Quinn [bulkmoderatieconsole](moderation.md) gebruiken om hun posten te matigen.

Als u de pictogramschakelopties voor het zijpaneel selecteert, worden de filters geopend waarmee wordt gezocht in community-inhoud.

Als u de muis boven een opmerkingskaart houdt, worden moderatiehandelingen weergegeven.

![chlimage_1-442](assets/chlimage_1-442.png)

## Rapporten over auteur {#reports-on-author}

Er zijn twee manieren om toegang te krijgen tot rapporten over studenten en bronnen voor activering.

Navigeer bij de auteur naar **Communities, [Resources console](resources.md)**, waar de enablement-bronnen worden beheerd, en na het selecteren van een communitysite, is het mogelijk om rapporten te genereren voor

* Alle actiemiddelen en leerpaden
* Eén specifieke activeringsbron of leerpad

Navigeer naar **Communities, [Reports console](reports.md)** en genereer rapporten volgens:

* Toewijzingen aan actiemiddelen en leerpaden
* Berichten naar een gemeenschapssite over een specifieke periode
* Weergaven (bezoeken ter plaatse) van een communitysite over een specifieke periode

* Posten en weergaven kunnen betrekking hebben op alle inhoud of op specifieke inhoud:

   * Forum
   * Forum-onderwerp
   * QnA
   * Vraag QnA
   * Blog
   * Blogartikel
   * Kalender
   * Kalendergebeurtenis

### Bronnenconsole {#resources-console}

Met een kleine activiteit en interactie met de Middelen bij publiceren, is het bekijken van de rapporten over auteur het waard om te kijken.

* Meld u bij de auteur aan met beheerdersrechten.
* Navigeer van het hoofdmenu aan **[!UICONTROL Communities]** > **[!UICONTROL Resources]**.
* Selecteer de `Enablement Tutorial`-site.
* Selecteer het pictogram `Report` voor een overzicht van alle Middelen.
* Selecteer een Middel en dan `Report` pictogram voor een rapport over dat Middel.

Het is waarschijnlijk te vroeg om gegevens van Adobe Analytics weer te geven, wat 1 tot 12 uur kan duren. Standaard SCORM-rapportage is echter al beschikbaar.

#### Resournerapport Ski Lessen {#ski-lessons-resource-report}

![chlimage_1-443](assets/chlimage_1-443.png)

#### Ski Lessen Rapport {#ski-lessons-user-report}

* Selecteer **[!UICONTROL Communities > Resources]**

* Kaart `Enablement Tutorial` openen
* Kaart `Ski Lessons` openen
* Selecteer `Report > User Report`

![chlimage_1-444](assets/chlimage_1-444.png)

### Rapportconsole {#reports-console}

De console van Rapporten staat voor generatie van rapporten op toe

* **Toewijzingen** voor elke community-site van enablement
* **Weergaven** voor alle communitysites
* **** Posts voor alle communitysites

Voor rapporten over toewijzingen:

* Meld u bij de auteur aan met beheerdersrechten.
* Ga naar **[!UICONTROL Communities]** > **[!UICONTROL Reports]** > **[!UICONTROL Assignments Report]**.
* Selecteer een **[!UICONTROL Site]** in het keuzemenu (selecteer `Enablement Tutorial`).

* Selecteer **[!UICONTROL Group]** (selecteer `Community Ski Class`)

* Selecteer een **[!UICONTROL Assignment]** (selecteer `Ski Lessons`)

* Selecteer **[!UICONTROL Generate]**

![chlimage_1-445](assets/chlimage_1-445.png)

Voor rapporten over weergaven:

* Meld u bij de auteur aan met beheerdersrechten.
* Ga naar **[!UICONTROL Communities]** > **[!UICONTROL Reports]** > **[!UICONTROL Views Report]**.
* Selecteer een **Site** in het keuzemenu (selecteer `Enablement Tutorial`).

* Selecteer **[!UICONTROL Content Type]** (selecteer `all`).

* Selecteer een **[!UICONTROL date range]** (selecteer `Last 7 days`).

* Selecteer **[!UICONTROL Generate]**.

![chlimage_1-446](assets/chlimage_1-446.png)

**[⇐ maken en toewijzen van Enablement-bronnen](resource.md)**
