---
title: Publikaties
description: AEM Communities heeft meldingen die gebeurtenissen weergeven die van belang zijn voor het aanmeldingscommunity-lid
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
docset: aem65
role: Admin
exl-id: cadb62c9-210d-4204-8abc-d0cf70960392
solution: Experience Manager
feature: Communities
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '605'
ht-degree: 0%

---

# Publikaties {#communities-notifications}

## Overzicht {#overview}

AEM Communities biedt een meldingssectie waarin gebeurtenissen worden weergegeven die van belang zijn voor de ondertekenaars in het community-lid.

De berichten zijn gelijkaardig aan [&#x200B; activiteiten &#x200B;](/help/communities/essentials-activities.md) en [&#x200B; abonnementen &#x200B;](/help/communities/subscriptions.md) aangezien zij uit kunnen voortvloeien:

* Het lid dat inhoud plaatst.
* Het lid dat ervoor kiest een ander lid te volgen.
* Het lid dat ervoor kiest om specifieke onderwerpen, artikelen en andere draden van inhoud te volgen.
* Het lid dat (@genoemd) een ander lid van de gemeenschap in een gebruiker etiketteert produceerde inhoud.

Wat meldingen onderscheidt van activiteiten en abonnementen is:

* Een koppeling naar de sectie Meldingen staat altijd in de koptekst van een communitysite:

   * De activiteiten vereisen de [&#x200B; functie van de activiteitenstroom &#x200B;](/help/communities/functions.md#activity-stream-function) om in de structuur van de communautaire plaats worden omvat.
   * De abonnementen vereisen [&#x200B; configuratie van e-mail &#x200B;](/help/communities/email.md).

* De implementatie van meldingen verloopt via schaalbare en pluggable kanalen:

   * Activiteiten zijn alleen beschikbaar op het web.
   * Abonnementen zijn alleen beschikbaar via e-mail.

Vanaf de Gemeenschappen [&#x200B; FP1 &#x200B;](/help/communities/deploy-communities.md#latestfeaturepack), zijn de beschikbare berichtkanalen:

* Het webkanaal, toegankelijk via de koppeling `Notifications` .
* Het e-mailkanaal, beschikbaar wanneer e-mail correct is geconfigureerd.

Toekomstige kanalen zijn mobiel en desktop.

### Vereisten {#requirements}

**vorm E-mail**

E-mail moet worden gevormd om het e-mailkanaal voor berichten functioneel te zijn.

Voor instructies bij vestiging e-mail, zie [&#x200B; het Vormen E-mail &#x200B;](/help/communities/analytics.md).

**laat volgen** toe

Componenten moeten worden geconfigureerd om het volgende in te schakelen. De eigenschappen die het volgende toestaan zijn [&#x200B; blog &#x200B;](/help/communities/blog-feature.md), [&#x200B; forum &#x200B;](/help/communities/forum.md), [&#x200B; QnA &#x200B;](/help/communities/working-with-qna.md), [&#x200B; kalender &#x200B;](/help/communities/calendar.md), [&#x200B; dossier &#x200B;](/help/communities/file-library.md), en [&#x200B; commentaren &#x200B;](/help/communities/comments.md).

**Nota**:

* De componenten die binnen gemeenschap [&#x200B; worden gebruikt plaatsmalplaatjes &#x200B;](/help/communities/sites.md) en [&#x200B; groepsmalplaatjes &#x200B;](/help/communities/tools-groups.md) kunnen reeds worden gevormd om te volgen.

* Gebruikersprofielen zijn al zo geconfigureerd dat andere leden deze kunnen volgen.

## Meldingen van de volgende {#notifications-from-following}

![&#x200B; berichten &#x200B;](assets/notifications.png)

Met de knop **[!UICONTROL Follow]** kunt u items opvolgen als activiteiten, abonnementen en/of meldingen. Elke keer dat de knop **[!UICONTROL Follow]** wordt geselecteerd, is het mogelijk om een selectie in of uit te schakelen. De selectie van `Email Subscriptions` is alleen aanwezig als deze is geconfigureerd.

Als een van de volgende methoden is geselecteerd, verandert de tekst van de knop in **[!UICONTROL Following]** . Voor het gemak is het mogelijk om `Unfollow All` te selecteren om alle methoden uit te schakelen.

De knop **[!UICONTROL Follow]** wordt weergegeven:

* Wanneer u het profiel van een ander lid weergeeft.
* Op een hoofdpagina met functies, zoals forums, QnA en blogs:

   * Volg alle activiteiten voor die algemene functie.

* Voor een specifiek bericht, zoals een forumonderwerp, een QnA-vraag of een blogartikel:

   * Hiermee wordt alle activiteit voor die specifieke vermelding gevolgd.

## Meldingsinstellingen beheren {#managing-notification-settings}

Als u de koppeling Instellingen kennisgeving op de pagina Meldingen selecteert, kan elk lid bepalen hoe meldingen worden ontvangen.

Het webkanaal is altijd ingeschakeld.

![&#x200B; notifications14 &#x200B;](assets/notifications1.png)

Het e-mailkanaal, dat op juiste [&#x200B; configuratie van e-mail &#x200B;](/help/communities/email.md) baseert, verstrekt de zelfde montages zoals voor het Webkanaal.

Het e-mailkanaal is standaard uitgeschakeld.

![&#x200B; notifications2 &#x200B;](assets/notifications2.png)

Het kan door een lid worden aangezet, maar nog hangt van e-mail af die wordt gevormd.

![&#x200B; notifications3 &#x200B;](assets/notifications3.png)

## Meldingen weergeven {#viewing-notifications}

### Webmeldingen {#web-notifications}

A [&#x200B; tovenaar creeerde communautaire plaats &#x200B;](/help/communities/sites-console.md) omvat nu een verbinding aan de `Notifications` eigenschap in de de kopbalbar van de plaats boven de banner. In tegenstelling tot berichten, worden de berichten gecreeerd voor elke communautaire plaats, terwijl de berichten tijdens het proces van de plaatsverwezenlijking moeten worden toegelaten.

Als u de gepubliceerde site bezoekt en de koppeling `Notifications` selecteert, worden alle meldingen voor het lid weergegeven.

![&#x200B; notifications4 &#x200B;](assets/notifications4.png)

### E-mailmeldingen {#email-notifications}

Wanneer het e-mailkanaal is ingeschakeld, ontvangt het lid een e-mail met een koppeling naar de inhoud op het web.

![&#x200B; notifications5 &#x200B;](assets/notifications5.png)

## E-mailberichten aanpassen {#customize-email-notifications}

De organisaties kunnen de e-mailberichten aanpassen door [&#x200B; bedekkend &#x200B;](/help/communities/client-customize.md#overlays) de malplaatjes bij **/libs/settings/community/templates/email/html**.

Bijvoorbeeld, om de herinneringen e-mailberichten (voor een component van gemeenschappen) te wijzigen voeg **toe als** voorwaarde voor werkwoord **&#x200B;**&#x200B;in de malplaatjes van de componenten vermeldt waarvoor u **@mtations** steun toeliet.

Om het malplaatje van e-mailberichten voor @genoemd in blogcommentaren te wijzigen, plaats uit het vakje malplaatje bij: **/libs/settings/community/templates/email/html/social.journal.components.hbs.comment/nl**

```java
{{#equals this.verb "mention"}}\
    A new mention <a href="{{objectUrl}}">comment</a> {{#if this.target.properties.[jcr:title]}}to the article "{{{target.displayName}}}" {{/if}}was added by {{{user.name}}} on {{dateUtil this.published format="EEE, d MMM yyyy HH:mm:ss z"}}.\n \
{{/equals}}\
```
