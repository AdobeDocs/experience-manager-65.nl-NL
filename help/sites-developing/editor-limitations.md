---
title: Editor-beperkingen
seo-title: Editor-beperkingen
description: De editor in de interface met aanraakbediening maakt gebruik van overlays voor interactie met inhoud die zich in een iframe bevindt. Deze interactie leidt tot sommige beperkingen in zowel gebruik van de redacteur als ook voor ontwikkelaars.
seo-description: De editor in de interface met aanraakbediening maakt gebruik van overlays voor interactie met inhoud die zich in een iframe bevindt. Deze interactie leidt tot sommige beperkingen in zowel gebruik van de redacteur als ook voor ontwikkelaars.
uuid: ff524530-3f3a-4c5b-9f94-4aa9aeb9d461
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: introduction
discoiquuid: d748decb-a614-4c9e-a502-d6176b720f1a
translation-type: tm+mt
source-git-commit: 844d42ed50da153077423190684aa85265bce12f

---


# Editor-beperkingen{#editor-limitations}

De editor in de interface met aanraakbediening maakt gebruik van overlays voor interactie met inhoud die zich in een iframe bevindt. Deze interactie leidt tot sommige beperkingen in zowel gebruik van de redacteur als ook voor ontwikkelaars. Deze pagina geeft een overzicht van deze beperkingen en biedt waar mogelijk oplossingen of tijdelijke oplossingen.

## Functionele beperkingen {#functional-limitations}

Een auteur kan de volgende functionele beperkingen tegenkomen wanneer hij de editor gebruikt om pagina&#39;s te schrijven.

### Koppelingen niet actief {#links-not-active}

Wanneer u een pagina [](/help/sites-authoring/editing-content.md)bewerkt, zijn koppelingen niet actief.

* [Schakel over naar de modus **Voorvertoning**](/help/sites-authoring/editing-content.md#preview-mode) om te navigeren met de koppelingen in de inhoud.

### Structuurpagina&#39;s {#structure-pages}

Pagina&#39;s kunnen geen naam krijgen `structure`. Pagina&#39;s waaraan een naam is gegeven, kunnen niet worden bewerkt in de pagina-editor. `structure`

## CSS-beperkingen {#css-limitations}

Een ontwikkelaar kan de volgende beperkingen ondervinden bij de interactie van de editor met CSS.

### Absoluut gepositioneerde elementen {#absolutely-positioned-elements}

Absoluut gepositioneerde elementen kunnen problemen veroorzaken in de positie van de overlay.

* Als dit gebeurt, zorg ervoor dat de afmetingen van absoluut gepositioneerd element correct zijn omdat de redacteur tot een bekleding met de nauwkeurige zelfde afmetingen zal leiden.

### vh Eenheden {#vh-units}

`vh` De eenheden worden niet ondersteund omdat de hoogte van het iframe automatisch moet worden aangepast door AEM.

### Vaste achtergrondafbeeldingen {#fixed-background-images}

Vaste achtergrondafbeeldingen worden mogelijk niet als vast weergegeven tijdens het schuiven omdat deze zijn ingesloten in een iframe.

* Als u de optie Pagina **weergeven als gepubliceerd** selecteert in de acties op de kopbalk, wordt de pagina correct weergegeven.

### 100% hoogte {#height}

100% hoogte wordt niet ondersteund op het tekstelement van een pagina.

* U kunt de hoofdtekst van een volledig scherm als volgt &quot;uitrekken&quot; implementeren om dit te omzeilen:

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

