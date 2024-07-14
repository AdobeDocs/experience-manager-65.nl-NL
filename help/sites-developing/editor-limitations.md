---
title: Editor-beperkingen
description: De editor in de interface met aanraakbediening gebruikt overlays voor interactie met inhoud die is opgesloten in een iframe. Deze interactie leidt tot sommige beperkingen in zowel gebruik van de redacteur als ook voor ontwikkelaars.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: introduction
exl-id: fd64f5dc-dfff-466b-8cdd-3c24ea1a15c8
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 0%

---

# Editor-beperkingen{#editor-limitations}

De editor in de interface met aanraakbediening gebruikt overlays voor interactie met inhoud die is opgesloten in een iframe. Deze interactie leidt tot sommige beperkingen in zowel gebruik van de redacteur als ook voor ontwikkelaars. Deze pagina geeft een overzicht van deze beperkingen en biedt waar mogelijk oplossingen of tijdelijke oplossingen.

## Functionele beperkingen {#functional-limitations}

Een auteur kan de volgende functionele beperkingen tegenkomen wanneer hij de editor gebruikt om pagina&#39;s te schrijven.

### Koppelingen niet actief {#links-not-active}

Wanneer [ het uitgeven van een pagina ](/help/sites-authoring/editing-content.md), zijn de verbindingen niet actief.

* [ Schakelaar aan **Voorproef** wijze ](/help/sites-authoring/editing-content.md#preview-mode) om het gebruiken van de verbindingen in uw inhoud te navigeren.

### Structuurpagina&#39;s {#structure-pages}

Pagina&#39;s kunnen geen naam `structure` krijgen. Pagina&#39;s met de naam `structure` kunnen niet worden bewerkt in de pagina-editor.

## CSS-beperkingen {#css-limitations}

Een ontwikkelaar kan de volgende beperkingen ondervinden bij de interactie van de editor met CSS.

### Absoluut gepositioneerde elementen {#absolutely-positioned-elements}

Absoluut gepositioneerde elementen kunnen problemen veroorzaken in de positie van de overlay.

* Als dit gebeurt, zorg ervoor dat de afmetingen van absoluut gepositioneerd element correct zijn omdat de redacteur tot een bekleding met de nauwkeurige zelfde afmetingen leidt.

### vh Eenheden {#vh-units}

`vh` -eenheden worden niet ondersteund, omdat de hoogte van het iframe automatisch moet worden aangepast door Adobe Experience Manager (AEM).

### Vaste achtergrondafbeeldingen {#fixed-background-images}

Vaste achtergrondafbeeldingen worden mogelijk niet als vast weergegeven tijdens het schuiven omdat deze zijn ingesloten in een iframe.

* Het selecteren van **Pagina van de Mening zoals Gepubliceerd** in de acties van de kopbalbar toont behoorlijk de pagina.

### 100% hoogte {#height}

100% hoogte wordt niet ondersteund op het tekstelement van een pagina.

* U kunt doorwerken om een hoofdtekst op volledig scherm te implementeren door het tekstelement als volgt uit te rekken:

```xml
body {
    position: absolute;
    top: 0;
    bottom: 0;
    right: 0;
    left: 0;
}
```

### Marge samenvouwen {#margin-collapsing}

Problemen met samenvouwen van marges kunnen worden gezien als het eerste onderliggende element van het body-element een marge heeft.

* De oplossing is een duidelijke oplossing op het niveau van het lichaamselement als volgt toe te voegen:

```xml
body:before, body:after{
    content: ' ';
    display: table;
}
```
