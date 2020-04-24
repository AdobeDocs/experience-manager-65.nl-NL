---
title: Componenten van overlaygemeenschappen
seo-title: Componenten van overlaygemeenschappen
description: Componenten van overlaygemeenschappen
seo-description: Componenten van overlaygemeenschappen
uuid: 872f7006-959a-49d2-b025-3a5abb7c6dca
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 502c0916-6c54-440c-be8c-eae56001fa26
docset: aem65
translation-type: tm+mt
source-git-commit: 48afa2146d0dcbab4beaa1044645c269b49fd7ff

---


# Componenten van overlaygemeenschappen {#overlay-communities-components}

Het is de bedoeling om een standaardcomponent te [bedekken](/help/communities/client-customize.md#overlays) door de weergave of het gedrag van een component globaal te wijzigen voor alle relatieve verwijzingen naar de component. Het is afhankelijk van de aard van de sling om naar de map /apps op te lossen voordat u in de map /libs zoekt. Het pad naar de component is dus identiek aan het pad naar de standaardcomponent, behalve dat het pad zich in de map /apps bevindt en niet in de map /libs.

## Voorbeeld {#example}

**Component Overlay-opmerkingen**

Stel dat u de commentaarfunctie wilt wijzigen zodat deze overeenkomt met het ontwerp van uw website, door de koptekst van de opmerking te wijzigen zodat de avatar niet meer wordt weergegeven voor opmerkingen. De oplossingen voor het verbergen van de avatar maken gebruik van CSS of bedekken, zoals hier beschreven, header.jsp in de map apps, zodat de HTML die de avatar bevat nooit naar de client wordt verzonden.

Als u opmerkingen wilt bedekken, moet u:

1. [Opmerkingen pagina](/help/communities/overlay-create-comments-page.md)
1. [Notities maken](/help/communities/overlay-create-nodes.md)
1. [De vormgeving wijzigen](/help/communities/overlay-alter-appearance.md)

**E-mails met overlaymeldingen**

Stel dat u het bericht van e-mailberichten wilt aanpassen, kunt u dit doen door de sjablonen te [bedekken](/help/communities/client-customize.md#overlays) op **/libs/settings/community/templates/email/html**.

Als u bijvoorbeeld de meldingen met betrekking tot vermeldingen wilt wijzigen (voor een specifieke component van een community waarin ugc is gemaakt), voegt u een **if** -voorwaarde toe voor het **vermelden** van werkwoorden in de sjablonen van de componenten waarvoor u de ondersteuning voor **@gesproken** hebt ingeschakeld.

```java
{{#equals this.verb "mention"}}\
    A new mention <a href="{{objectUrl}}">comment</a> {{#if this.target.properties.[jcr:title]}}to the article "{{{target.displayName}}}" {{/if}}was added by {{{user.name}}} on {{dateUtil this.published format="EEE, d MMM yyyy HH:mm:ss z"}}.\n \
{{/equals}}\
```

Als u de sjabloon voor e-mailmeldingen voor @notify in blogopmerkingen wilt wijzigen, plaatst u de sjabloon voor het vak op: `/libs/settings/community/templates/email/html/social.journal.components.hbs.comment/en`
