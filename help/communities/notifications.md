---
title: Publikaties
seo-title: Publikaties
description: AEM Communities hebben meldingen die gebeurtenissen weergeven die van belang zijn voor het aanmeldingscommunity-lid
seo-description: AEM Communities hebben meldingen die gebeurtenissen weergeven die van belang zijn voor het aanmeldingscommunity-lid
uuid: 2f5ea4b5-7308-414e-a3f8-2e8aa76b1ef4
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: ab9088b7-a691-4153-ac82-1e8c0a19ed5d
docset: aem65
translation-type: tm+mt
source-git-commit: 5d196d1f6d5f94f2d3ef0d4461cfe38562f8ba8c
workflow-type: tm+mt
source-wordcount: '621'
ht-degree: 0%

---


# Publikaties {#communities-notifications}

## Overzicht {#overview}

AEM Communities geeft een sectie met meldingen weer waarin gebeurtenissen worden weergegeven die van belang zijn voor de ondertekenaars in het community-lid.

Meldingen zijn vergelijkbaar met [activiteiten](/help/communities/essentials-activities.md) en [abonnementen](/help/communities/subscriptions.md) , omdat zij het gevolg kunnen zijn van:

* Het lid dat inhoud plaatst.
* Het lid dat ervoor kiest een ander lid te volgen.
* Het lid dat ervoor kiest om specifieke onderwerpen, artikelen en andere draden van inhoud te volgen.
* Het lid dat (@genoemd) een ander lid van de gemeenschap in een gebruiker etiketteert produceerde inhoud.

Wat meldingen onderscheidt van activiteiten en abonnementen is:

* Een koppeling naar de sectie Meldingen staat altijd in de koptekst van een communitysite:

   * De activiteiten vereisen dat de functie [van de](/help/communities/functions.md#activity-stream-function) activiteitsstroom in de structuur van de communautaire plaats wordt omvat.
   * Voor abonnementen moet e-mail [worden](/help/communities/email.md)geconfigureerd.

* De implementatie van meldingen verloopt via schaalbare en pluggable kanalen:

   * Activiteiten zijn alleen beschikbaar op het web.
   * Abonnementen zijn alleen beschikbaar via e-mail.

Vanaf het Communautair [KP1](/help/communities/deploy-communities.md#latestfeaturepack)zijn de beschikbare kennisgevingskanalen:

* Het webkanaal, toegankelijk via de `Notifications` koppeling.
* Het e-mailkanaal, beschikbaar wanneer e-mail correct is geconfigureerd.

Toekomstige kanalen zijn mobiel en desktop.

### Vereisten {#requirements}

**E-mail configureren**

E-mail moet worden gevormd om het e-mailkanaal voor berichten functioneel te zijn.

Zie E-mail [configureren](/help/communities/analytics.md)voor instructies over het instellen van e-mail.

**Volgen inschakelen**

Componenten moeten worden geconfigureerd om het volgende in te schakelen. Functies die het volgende toestaan, zijn [blog](/help/communities/blog-feature.md), [forum](/help/communities/forum.md), [QnA](/help/communities/working-with-qna.md), [agenda](/help/communities/calendar.md), [bestandsbibliotheek](/help/communities/file-library.md)[](/help/communities/comments.md)en commentaren.

**Opmerking**:

* Componenten die worden gebruikt binnen sjablonen [voor communitysites en](/help/communities/sites.md) groepssjablonen [](/help/communities/tools-groups.md) , kunnen al geconfigureerd zijn om te volgen.

* Gebruikersprofielen zijn al zo geconfigureerd dat andere leden deze kunnen volgen.

## Meldingen van: {#notifications-from-following}

![meldingen](assets/notifications.png)

Met de **[!UICONTROL Follow]** knop kunt u items opvolgen als activiteiten, abonnementen en/of meldingen. Elke keer dat de **[!UICONTROL Follow]** knop wordt geselecteerd, is het mogelijk om een selectie in of uit te schakelen. De `Email Subscriptions` selectie is alleen aanwezig als deze is geconfigureerd.

Als een van de volgende methoden is geselecteerd, verandert de tekst van de knop in **[!UICONTROL Following]**. Voor het gemak is het mogelijk om alle methoden uit `Unfollow All` te schakelen.

De **[!UICONTROL Follow]** knop verschijnt:

* Wanneer u het profiel van een ander lid weergeeft.
* Op een hoofdpagina met functies, zoals forums, QnA en blogs:

   * Volg alle activiteiten voor die algemene functie.

* Voor een specifiek bericht, zoals een forumonderwerp, een QnA-vraag of een blogartikel:

   * Hiermee wordt alle activiteit voor die specifieke vermelding gevolgd.

## Meldingsinstellingen beheren {#managing-notification-settings}

Als u de koppeling Instellingen kennisgeving op de pagina Meldingen selecteert, kan elk lid bepalen hoe meldingen worden ontvangen.

Het webkanaal is altijd ingeschakeld.

![notifications14](assets/notifications1.png)

Het e-mailkanaal, dat afhankelijk is van de juiste [configuratie van de e-mail](/help/communities/email.md), biedt dezelfde instellingen als voor het webkanaal.

Het e-mailkanaal is standaard uitgeschakeld.

![notifications2](assets/notifications2.png)

Het kan door een lid worden aangezet, maar nog hangt van e-mail af die wordt gevormd.

![notifications3](assets/notifications3.png)

## Meldingen weergeven {#viewing-notifications}

### Webmeldingen {#web-notifications}

Een door de [wizard gemaakte communitysite](/help/communities/sites-console.md) bevat nu een koppeling naar de `Notifications` functie in de koptekstbalk van de site boven de banner. In tegenstelling tot berichten, worden de berichten gecreeerd voor elke communautaire plaats, terwijl de berichten tijdens het proces van de plaatsverwezenlijking moeten worden toegelaten.

Als u de gepubliceerde site bezoekt en de `Notifications` koppeling selecteert, worden alle meldingen voor het lid weergegeven.

![notifications4](assets/notifications4.png)

### E-mailmeldingen {#email-notifications}

Wanneer het e-mailkanaal is ingeschakeld, ontvangt het lid een e-mail met een koppeling naar de inhoud op het web.

![notifications5](assets/notifications5.png)

## E-mailberichten aanpassen {#customize-email-notifications}

Organisaties kunnen de e-mailmeldingen aanpassen door de sjablonen te [bedekken](/help/communities/client-customize.md#overlays) op **/libs/settings/community/templates/email/html**.

Als u bijvoorbeeld de meldingen met betrekking tot vermeldingen wilt wijzigen (voor een onderdeel van een community), voegt u een **if** -voorwaarde toe voor de vermelding **van het werkwoord in de sjablonen van de componenten waarvoor u ondersteuning van** @gesproken **** hebt ingeschakeld.

Als u de sjabloon voor e-mailmeldingen voor @notify in blogopmerkingen wilt wijzigen, plaatst u de sjabloon voor het vak op: **/libs/settings/community/templates/email/html/social.journal.components.hbs.comment/nl**

```java
{{#equals this.verb "mention"}}\
    A new mention <a href="{{objectUrl}}">comment</a> {{#if this.target.properties.[jcr:title]}}to the article "{{{target.displayName}}}" {{/if}}was added by {{{user.name}}} on {{dateUtil this.published format="EEE, d MMM yyyy HH:mm:ss z"}}.\n \
{{/equals}}\
```

