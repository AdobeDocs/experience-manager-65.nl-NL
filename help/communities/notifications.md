---
title: Publikaties
seo-title: Publikaties
description: AEM-gemeenschappen hebben meldingen die gebeurtenissen weergeven die van belang zijn voor de ondertekenende community
seo-description: AEM-gemeenschappen hebben meldingen die gebeurtenissen weergeven die van belang zijn voor de ondertekenende community
uuid: 2f5ea4b5-7308-414e-a3f8-2e8aa76b1ef4
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: ab9088b7-a691-4153-ac82-1e8c0a19ed5d
docset: aem65
translation-type: tm+mt
source-git-commit: 27a054cc5d502d95c664c3b414d0066c6c120b65

---


# Publikaties{#communities-notifications}

## Overzicht {#overview}

AEM Communities biedt een meldingssectie waarin gebeurtenissen worden weergegeven die van belang zijn voor de ondertekenaars in een community.

Meldingen zijn vergelijkbaar met [activiteiten](/help/communities/essentials-activities.md) en [abonnementen](/help/communities/subscriptions.md) , omdat ze het gevolg kunnen zijn van

* het lid dat inhoud plaatst
* het lid dat een ander lid volgt
* het lid dat ervoor kiest om specifieke onderwerpen, artikelen en andere draden van inhoud te volgen
* het lid dat een ander communitylid in een door de gebruiker gegenereerde inhoud tagt (@genoemd)

Wat maakt onderscheid tussen meldingen en activiteiten en abonnementen?

* een koppeling naar de sectie met meldingen is altijd aanwezig in de koptekst van een communautaire site

   * activiteiten vereisen dat de [activiteitsstroomfunctie](/help/communities/functions.md#activity-stream-function) wordt opgenomen in de structuur van de site van de gemeenschap
   * abonnementen vereisen [configuratie van e-mail](/help/communities/email.md)

* de uitvoering van kennisgevingen verloopt via schaalbare en pluggable kanalen

   * activiteiten zijn alleen beschikbaar op het web
   * abonnementen zijn alleen beschikbaar via e-mail

Vanaf het Communautair [KP1](/help/communities/deploy-communities.md#latestfeaturepack)zijn de beschikbare kennisgevingskanalen

* het webkanaal, geopend via de `Notifications` koppeling
* het e-mailkanaal beschikbaar wanneer e-mail correct is geconfigureerd

Toekomstige kanalen zijn mobiel en desktop.

### Vereisten {#requirements}

**E-mail configureren**

E-mail moet worden gevormd om het e-mailkanaal voor berichten functioneel te zijn.

Zie E-mail [configureren](/help/communities/analytics.md)voor instructies over het instellen van e-mail.

**Volgen inschakelen**

Componenten moeten worden geconfigureerd om het volgende in te schakelen. Functies die het volgende toestaan, zijn [blog](/help/communities/blog-feature.md), [forum](/help/communities/forum.md), [QnA](/help/communities/working-with-qna.md), [agenda](/help/communities/calendar.md), [bestandsbibliotheek](/help/communities/file-library.md)[](/help/communities/comments.md)en commentaren.

Let op:

* componenten die binnen communautaire [plaatssjablonen](/help/communities/sites.md) en [groepsmalplaatjes](/help/communities/tools-groups.md) worden gebruikt kunnen reeds worden gevormd om het volgende toe te staan

* lidprofielen zijn reeds gevormd om andere leden toe te staan om te volgen

## Meldingen van: {#notifications-from-following}

![chlimage_1-243](assets/chlimage_1-243.png)

Met de knop **Volg ** kunt u vermeldingen opvolgen als activiteiten, abonnementen en/of meldingen. Telkens wanneer de knop **Volg **gebruiken is geselecteerd, kunt u een selectie in- of uitschakelen. De `Email Subscriptions` selectie is alleen aanwezig als deze is geconfigureerd.

Als er een methode van het volgende is geselecteerd, verandert de tekst van de knop in **Volgende**. Voor het gemak is het mogelijk om alle methoden uit `Unfollow All` te schakelen.

De knop **Volg **De wordt weergegeven

* bij het bekijken van het profiel van een ander lid
* op een hoofdpagina met functies, zoals forums, QnA en blogs

   * volgt alle activiteiten voor dat algemene kenmerk

* voor een specifiek bericht, zoals een forumonderwerp, een QnA-vraag of een blogartikel

   * volgt alle activiteiten voor die specifieke vermelding

## Meldingsinstellingen beheren {#managing-notification-settings}

Als u de koppeling Instellingen kennisgeving op de pagina Meldingen selecteert, kan elk lid bepalen hoe meldingen worden ontvangen.

Het webkanaal is altijd ingeschakeld.

![chlimage_1-244](assets/chlimage_1-244.png)

Het e-mailkanaal, dat afhankelijk is van de juiste [configuratie van de e-mail](/help/communities/email.md), biedt dezelfde instellingen als voor het webkanaal.

Het e-mailkanaal is standaard uitgeschakeld.

![chlimage_1-245](assets/chlimage_1-245.png)

Het kan door een lid worden aangezet, maar nog hangt van e-mail af die wordt gevormd.

![chlimage_1-246](assets/chlimage_1-246.png)

## Meldingen weergeven {#viewing-notifications}

### Webmeldingen {#web-notifications}

Een door de [wizard gemaakte communitysite](/help/communities/sites-console.md) bevat nu een koppeling naar de `Notifications` functie in de koptekstbalk van de site boven de banner. In tegenstelling tot berichten, worden de berichten gecreeerd voor elke communautaire plaats, terwijl de berichten tijdens het proces van de plaatsverwezenlijking moeten worden toegelaten.

Als u de gepubliceerde site bezoekt en de `Notifications` koppeling selecteert, worden alle meldingen voor het lid weergegeven.

![chlimage_1-247](assets/chlimage_1-247.png)

### E-mailmeldingen {#email-notifications}

Wanneer het e-mailkanaal is ingeschakeld, ontvangt het lid een e-mail met een koppeling naar de inhoud op het web.

![chlimage_1-248](assets/chlimage_1-248.png)

## E-mailberichten aanpassen {#customize-email-notifications}

Organisaties kunnen de e-mailmeldingen aanpassen door de sjablonen te [bedekken](/help/communities/client-customize.md#overlays) op **/libs/settings/community/templates/email/html**.

Als u bijvoorbeeld de meldingen met betrekking tot vermeldingen (voor een component van een gemeenschap) wilt wijzigen, voegt u een** if **voorwaarde toe voor de **vermelding van het werkwoord** in de sjablonen van de componenten waarvoor u ondersteuning voor **@mtifications** hebt ingeschakeld.

Als u de sjabloon voor e-mailmeldingen voor @notify in blogopmerkingen wilt wijzigen, plaatst u de sjabloon voor het vak op: **/libs/settings/community/templates/email/html/social.journal.components.hbs.comment/nl**

```java
{{#equals this.verb "mention"}}\
    A new mention <a href="{{objectUrl}}">comment</a> {{#if this.target.properties.[jcr:title]}}to the article "{{{target.displayName}}}" {{/if}}was added by {{{user.name}}} on {{dateUtil this.published format="EEE, d MMM yyyy HH:mm:ss z"}}.\n \
{{/equals}}\
```

