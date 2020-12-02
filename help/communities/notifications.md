---
title: Publikaties
seo-title: Publikaties
description: AEM Communities heeft meldingen die gebeurtenissen weergeven die van belang zijn voor het aanmeldingscommunity-lid
seo-description: AEM Communities heeft meldingen die gebeurtenissen weergeven die van belang zijn voor het aanmeldingscommunity-lid
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


# Communitymeldingen {#communities-notifications}

## Overzicht {#overview}

AEM Communities biedt een meldingssectie waarin gebeurtenissen worden weergegeven die van belang zijn voor de ondertekenaars in het community-lid.

Meldingen zijn vergelijkbaar met [activiteiten](/help/communities/essentials-activities.md) en [abonnementen](/help/communities/subscriptions.md), omdat deze kunnen voortvloeien uit:

* Het lid dat inhoud plaatst.
* Het lid dat ervoor kiest een ander lid te volgen.
* Het lid dat ervoor kiest om specifieke onderwerpen, artikelen en andere draden van inhoud te volgen.
* Het lid dat (@genoemd) een ander lid van de gemeenschap in een gebruiker etiketteert produceerde inhoud.

Wat meldingen onderscheidt van activiteiten en abonnementen is:

* Een koppeling naar de sectie Meldingen staat altijd in de koptekst van een communitysite:

   * Voor activiteiten moet de functie [activity stream](/help/communities/functions.md#activity-stream-function) worden opgenomen in de structuur van de communitysite.
   * Abonnementen vereisen [configuratie van e-mail](/help/communities/email.md).

* De implementatie van meldingen verloopt via schaalbare en pluggable kanalen:

   * Activiteiten zijn alleen beschikbaar op het web.
   * Abonnementen zijn alleen beschikbaar via e-mail.

Vanaf de Gemeenschappen [FP1](/help/communities/deploy-communities.md#latestfeaturepack) zijn de beschikbare kennisgevingskanalen:

* Het webkanaal dat wordt geopend via de koppeling `Notifications`.
* Het e-mailkanaal, beschikbaar wanneer e-mail correct is geconfigureerd.

Toekomstige kanalen zijn mobiel en desktop.

### Vereisten {#requirements}

**E-mail configureren**

E-mail moet worden gevormd om het e-mailkanaal voor berichten functioneel te zijn.

Zie [E-mail configureren](/help/communities/analytics.md) voor instructies voor het instellen van e-mail.

**Volgen inschakelen**

Componenten moeten worden geconfigureerd om het volgende in te schakelen. Functies die het volgende toestaan, zijn [blog](/help/communities/blog-feature.md), [forum](/help/communities/forum.md), [QnA](/help/communities/working-with-qna.md), [agenda](/help/communities/calendar.md), [bestandsbibliotheek](/help/communities/file-library.md) en [commentaren](/help/communities/comments.md).

**Opmerking**:

* Componenten die worden gebruikt binnen de community [sitesjablonen](/help/communities/sites.md) en [groepssjablonen](/help/communities/tools-groups.md) kunnen al zijn geconfigureerd om te volgen.

* Gebruikersprofielen zijn al zo geconfigureerd dat andere leden deze kunnen volgen.

## Meldingen van volgende {#notifications-from-following}

![meldingen](assets/notifications.png)

Met de knop **[!UICONTROL Follow]** kunt u vermeldingen volgen als activiteiten, abonnementen en/of meldingen. Elke keer dat de knop **[!UICONTROL Follow]** wordt geselecteerd, is het mogelijk een selectie in of uit te schakelen. De `Email Subscriptions` selectie is slechts aanwezig wanneer gevormd.

Als een methode van het volgende wordt geselecteerd, verandert de tekst van de knoop in **[!UICONTROL Following]**. Voor het gemak, is het mogelijk om `Unfollow All` te selecteren om alle methodes van een knevel te voorzien.

De knop **[!UICONTROL Follow]** wordt weergegeven:

* Wanneer u het profiel van een ander lid weergeeft.
* Op een hoofdpagina met functies, zoals forums, QnA en blogs:

   * Volg alle activiteiten voor die algemene functie.

* Voor een specifiek bericht, zoals een forumonderwerp, een QnA-vraag of een blogartikel:

   * Hiermee wordt alle activiteit voor die specifieke vermelding gevolgd.

## Meldingsinstellingen {#managing-notification-settings} beheren

Als u de koppeling Instellingen kennisgeving op de pagina Meldingen selecteert, kan elk lid bepalen hoe meldingen worden ontvangen.

Het webkanaal is altijd ingeschakeld.

![meldingen14](assets/notifications1.png)

Het e-mailkanaal, dat afhankelijk is van de juiste [configuratie van e-mail](/help/communities/email.md), biedt dezelfde instellingen als voor het webkanaal.

Het e-mailkanaal is standaard uitgeschakeld.

![notifications2](assets/notifications2.png)

Het kan door een lid worden aangezet, maar nog hangt van e-mail af die wordt gevormd.

![notifications3](assets/notifications3.png)

## Meldingen {#viewing-notifications} weergeven

### Webmeldingen {#web-notifications}

Een [wizard heeft een communitysite](/help/communities/sites-console.md) gemaakt en bevat nu een koppeling naar de functie `Notifications` in de kopbalk van de site boven de banner. In tegenstelling tot berichten, worden de berichten gecreeerd voor elke communautaire plaats, terwijl de berichten tijdens het proces van de plaatsverwezenlijking moeten worden toegelaten.

Als u de gepubliceerde site bezoekt en de koppeling `Notifications` selecteert, worden alle meldingen voor het lid weergegeven.

![meldingen4](assets/notifications4.png)

### E-mailmeldingen {#email-notifications}

Wanneer het e-mailkanaal is ingeschakeld, ontvangt het lid een e-mail met een koppeling naar de inhoud op het web.

![meldingen5](assets/notifications5.png)

## E-mailmeldingen aanpassen {#customize-email-notifications}

Organisaties kunnen de e-mailmeldingen aanpassen door [de sjablonen op **/libs/settings/community/templates/email/html** te bedekken.](/help/communities/client-customize.md#overlays)

Als u bijvoorbeeld de e-mailmeldingen voor vermeldingen wilt wijzigen (voor een onderdeel van een gemeenschap), voegt u een **if** voorwaarde voor werkwoord **specify** toe in de sjablonen van de componenten waarvoor u de ondersteuning **@mtations** hebt ingeschakeld.

Als u de sjabloon voor e-mailmeldingen voor @notify in blogopmerkingen wilt wijzigen, plaatst u de sjabloon voor het vak op: **/libs/settings/community/templates/email/html/social.journal.components.hbs.comment/en**

```java
{{#equals this.verb "mention"}}\
    A new mention <a href="{{objectUrl}}">comment</a> {{#if this.target.properties.[jcr:title]}}to the article "{{{target.displayName}}}" {{/if}}was added by {{{user.name}}} on {{dateUtil this.published format="EEE, d MMM yyyy HH:mm:ss z"}}.\n \
{{/equals}}\
```

