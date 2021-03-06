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
source-git-commit: f375b40c084ee363757b78c602091f38524b8b03
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 0%

---


# Component {#extend-comments-component} voor opmerkingen uitbreiden

De bedoeling van [het uitbreiden van](client-customize.md#extensions) een standaardcomponent is de verschijning of het gedrag van een component voor specifiek gebruik te veranderen.

Het pad naar de component is uniek en verwijst naar de standaardcomponent als een superbrontype. Er is minder risico omdat het bereik beperkt is in vergelijking met het mondiale bereik van een componentoverlay.

>[!NOTE]
>
>Het uitbreiden van een [overlay](client-customize.md#overlays) component wordt niet gesteund.

## Voorbeeld {#example}

Stel dat de koptekst van de commentaarcomponent op de ene site van de AEM instantie een andere weergave moet krijgen, terwijl de standaardweergave op een andere site wordt weergegeven. In plaats van de standaardopmerking te bedekken, waardoor de commentaarcomponent voor alle instanties wordt gewijzigd, kunt u beter ervoor zorgen dat er meerdere commentaarcomponenten beschikbaar zijn voor gebruik op verschillende sites.

Om deze oplossing uit te voeren, creeer een nieuwe component die (met voeten treedt) bestaande uitbreidt en het manuscript van Handlebars wijzigt. Het gebied van de site dat de nieuwe opmerkingen gebruikt, kan de uitgebreide versie gebruiken, terwijl de sites die de standaardweergave gebruiken, ongewijzigd blijven.

De commentaarcomponent is eigenlijk ????n van twee componenten die uit het commentaarsysteem bestaan. Er zijn dus twee onderdelen die moeten worden uitgebreid: *opmerkingen* en *commentaar*. Het script dat moet worden bewerkt, bevindt zich in het *comment*-bestand van de component, terwijl de bovenliggende *comments*-component (het opmerkingensysteem) is wat een auteur daadwerkelijk aan de pagina toevoegt.`header.hbs`

Als u opmerkingen wilt uitbreiden, moet u:

1. [De componenten maken](extend-create-components.md)
1. [Opmerking toevoegen aan voorbeeldpagina](extend-sample-page.md)
1. [De vormgeving wijzigen](extend-alter-appearance.md)

