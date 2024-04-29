---
title: Overlay Communities-componenten
description: Leer over het bedekken van een standaardcomponent zodat u de verschijning of het gedrag van een component globaal kunt veranderen, voor alle relatieve verwijzingen naar de component.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
docset: aem65
exl-id: 18376805-c2ed-439a-abc7-e9657afe8baf
solution: Experience Manager
feature: Communities
role: Developer
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 0%

---

# Overlay Communities-componenten {#overlay-communities-components}

De bedoeling van [bedekken](/help/communities/client-customize.md#overlays) een standaardcomponent is het wijzigen van de weergave of het gedrag van een component in het algemeen voor alle relatieve verwijzingen naar de component. Het is afhankelijk van de aard van de sling om naar de map /apps op te lossen voordat u in de map /libs zoekt. Het pad naar de component is dus identiek aan het pad naar de standaardcomponent, behalve dat het pad zich in de map /apps bevindt en niet in de map /libs.

## Voorbeeld {#example}

**Component Overlay-opmerkingen**

Stel dat u de commentaarfunctie wilt wijzigen zodat deze overeenkomt met het ontwerp van uw website, door de koptekst van de opmerking te wijzigen zodat de avatar niet meer wordt weergegeven voor opmerkingen. De oplossingen voor het verbergen van de avatar maken gebruik van CSS of, zoals hier wordt beschreven, van het bedekken van header.jsp in de map apps, zodat de HTML met de avatar nooit naar de client wordt verzonden.

Als u opmerkingen wilt bedekken, moet u:

1. [Pagina met opmerkingen maken](/help/communities/overlay-create-comments-page.md)
1. [Notities maken](/help/communities/overlay-create-nodes.md)
1. [De vormgeving wijzigen](/help/communities/overlay-alter-appearance.md)

**E-mails met overlaymeldingen**

Stel dat u het bericht van e-mailberichten wilt aanpassen, dat kunt u doen door [bedekken](/help/communities/client-customize.md#overlays) de sjablonen op `/libs/settings/community/templates/email/html`.

Stel dat u de e-mailmeldingen voor vermeldingen wilt bewerken (voor een specifiek onderdeel Community waarin UGC is gemaakt). Voeg in dergelijke gevallen een **indien** voorwaarde voor werkwoord **noemen** in de malplaatjes van de componenten waarvoor u toeliet **@mnotices** ondersteuning.

```java
{{#equals this.verb "mention"}}\
    A new mention <a href="{{objectUrl}}">comment</a> {{#if this.target.properties.[jcr:title]}}to the article "{{{target.displayName}}}" {{/if}}was added by {{{user.name}}} on {{dateUtil this.published format="EEE, d MMM yyyy HH:mm:ss z"}}.\n \
{{/equals}}\
```

Als u de sjabloon voor e-mailmeldingen voor @notify in blogopmerkingen wilt wijzigen, plaatst u de sjabloon voor het vak op: `/libs/settings/community/templates/email/html/social.journal.components.hbs.comment/en`
