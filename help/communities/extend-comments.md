---
title: Component Opmerkingen uitbreiden
seo-title: Component Opmerkingen uitbreiden
description: De component Comments uitbreiden om de weergave of het gedrag ervan voor specifieke toepassingen te wijzigen
seo-description: De component Comments uitbreiden om de weergave of het gedrag ervan voor specifieke toepassingen te wijzigen
uuid: 6f439097-b1d0-4e7d-afcf-01d8f43aa866
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: a07a4690-0e47-4a76-84cb-96abdc70b835
translation-type: tm+mt
source-git-commit: 0b25d956c19c5fc5d79f87b292a0c61a23e5d66a

---


# Component Opmerkingen uitbreiden {#extend-comments-component}

Het is de bedoeling om een standaardcomponent [uit te breiden](client-customize.md#extensions) om de weergave of het gedrag van een component voor specifieke toepassingen te wijzigen.

Het pad naar de component is uniek en verwijst naar de standaardcomponent als een superbrontype. Er is minder risico omdat het bereik beperkt is in vergelijking met het mondiale bereik van een componentoverlay.

>[!NOTE]
>
>Het uitbreiden van een [overlappende](client-customize.md#overlays) component wordt niet ondersteund.

## Voorbeeld {#example}

Stel dat de koptekst van de commentaarcomponent op de ene site van de AEM-instantie een andere weergave moet krijgen, terwijl de standaardweergave op een andere site wordt weergegeven. In plaats van de standaardopmerking te bedekken, waardoor de commentaarcomponent voor alle instanties wordt gewijzigd, kunt u beter ervoor zorgen dat er meerdere commentaarcomponenten beschikbaar zijn voor gebruik op verschillende sites.

Om deze oplossing uit te voeren, creeer een nieuwe component die (met voeten treedt) bestaande uitbreidt en het manuscript van Handlebars wijzigt. Het gebied van de site dat de nieuwe opmerkingen gebruikt, kan de uitgebreide versie gebruiken, terwijl de sites die de standaardweergave gebruiken, ongewijzigd blijven.

De commentaarcomponent is eigenlijk één van twee componenten die uit het commentaarsysteem bestaan. Er zijn dus twee onderdelen die moeten worden uitgebreid: *opmerkingen* en *opmerkingen*. Het script dat moet worden bewerkt, bevindt zich in het *bestand van de component* Commentaar `header.hbs` , terwijl de bovenliggende ** commentaarcomponent (het opmerkingensysteem) de component is die een auteur daadwerkelijk aan de pagina toevoegt.

Als u opmerkingen wilt uitbreiden, moet u:

1. [De componenten maken](extend-create-components.md)
1. [Opmerking toevoegen aan voorbeeldpagina](extend-sample-page.md)
1. [De vormgeving wijzigen](extend-alter-appearance.md)

