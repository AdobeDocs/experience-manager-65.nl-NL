---
title: Component Opmerkingen uitbreiden
description: De component Comments uitbreiden om de weergave of het gedrag ervan voor specifieke toepassingen te wijzigen
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: e57198cb-8fd9-43e2-b416-e40e462561c8
solution: Experience Manager
feature: Communities
role: Developer
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---

# Component Opmerkingen uitbreiden  {#extend-comments-component}

De bedoeling van [verlenging](client-customize.md#extensions) een standaardcomponent bestaat uit het wijzigen van de vormgeving of het gedrag van een component voor specifieke toepassingen.

Het pad naar de component is uniek en verwijst naar de standaardcomponent als een superbrontype. Er is minder risico omdat het bereik beperkt is in vergelijking met het mondiale bereik van een componentoverlay.

>[!NOTE]
>
>Een [bedeesd](client-customize.md#overlays) wordt niet ondersteund.

## Voorbeeld {#example}

Stel dat de koptekst van de commentaarcomponent op de ene site van de AEM instantie een andere weergave moet krijgen, terwijl de standaardweergave op een andere site wordt weergegeven. In plaats van de standaardopmerking te bedekken, waardoor de commentaarcomponent voor alle instanties wordt gewijzigd, kunt u beter ervoor zorgen dat er meerdere commentaarcomponenten beschikbaar zijn voor gebruik op verschillende sites.

Om deze oplossing uit te voeren, creeer een component die (met voeten treedt) bestaande uitbreidt en het manuscript van Handlebars wijzigt. Het gebied van de site dat de nieuwe opmerkingen gebruikt, kan de uitgebreide versie gebruiken, terwijl de sites die de standaardweergave gebruiken, ongewijzigd blijven.

De commentaarcomponent is eigenlijk één van twee componenten die uit het commentaarsysteem bestaan. Er zijn dus twee onderdelen die moeten worden uitgebreid: *opmerkingen* en *opmerking*. Het script dat moet worden bewerkt, staat in het dialoogvenster *opmerking* component `header.hbs` bestand, terwijl het bovenliggende bestand *opmerkingen* is wat een auteur daadwerkelijk aan de pagina toevoegt (het opmerkingensysteem).

Als u opmerkingen wilt uitbreiden, moet u:

1. [De componenten maken](extend-create-components.md)
1. [Opmerking toevoegen aan voorbeeldpagina](extend-sample-page.md)
1. [De vormgeving wijzigen](extend-alter-appearance.md)
