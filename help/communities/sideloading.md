---
title: Component Sideloading
description: sideloading in een Community-component is handig wanneer een webpagina is ontworpen als een eenvoudige app van één pagina die dynamisch wijzigt wat wordt weergegeven, afhankelijk van wat de bezoeker van de site heeft geselecteerd
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: 960e132c-b370-43d1-bd8f-e7d0ded7c0b3
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# Component Sideloading {#component-sideloading}

## Overzicht {#overview}

sideloading in een Community-component is handig wanneer een webpagina is ontworpen als een eenvoudige app van één pagina die dynamisch wijzigt wat wordt weergegeven, afhankelijk van wat de bezoeker van de site heeft geselecteerd.

Dit wordt gedaan wanneer de componenten van de Gemeenschappen niet in het paginamalplaatje bestaan, maar in plaats daarvan dynamisch na de selectie van een plaatsbezoeker worden toegevoegd.

Aangezien het framework voor sociale componenten (SCF) een lichte aanwezigheid heeft, worden alleen SCF-componenten geregistreerd die bestaan op het moment dat de pagina voor het eerst wordt geladen. Een dynamisch toegevoegde SCF-component die na het laden van de pagina moet worden geregistreerd, kan alleen worden geregistreerd als SCF wordt aangeroepen om de component te &quot;sideloaden&quot;.

Wanneer een pagina is ontworpen om onderdelen van een Gemeenschappen te sideloaden, is het mogelijk om de gehele pagina in cache te plaatsen.

De stappen om componenten dynamisch toe te voegen SCF zijn:

1. [De component toevoegen aan de DOM](#dynamically-add-component-to-dom)

1. [ Sideload de component ](#sideload-by-invoking-scf) gebruikend één van twee methodes:

* [Dynamische insluiting](#dynamic-inclusion)
   * Alle dynamisch toegevoegde componenten versterken
* [Dynamisch laden](#dynamic-loading)
   * Eén specifieke component op aanvraag toevoegen

>[!NOTE]
>
>Sideloading van [ niet-bestaande middelen ](scf.md#add-or-include-a-communities-component) wordt niet gesteund.

## Component dynamisch toevoegen aan DOM {#dynamically-add-component-to-dom}

Of de component nu dynamisch wordt opgenomen of dynamisch wordt geladen, moet deze eerst aan de DOM worden toegevoegd.

Bij het toevoegen van de SCF-component is de meest gebruikte tag de DIV-tag, maar kunnen ook andere tags worden gebruikt. Omdat SCF slechts DOM onderzoekt wanneer de pagina aanvankelijk laadt, zal deze toevoeging aan DOM onopgemerkt blijven tot SCF uitdrukkelijk wordt aangehaald.

Welk label ook wordt gebruikt, het element moet minstens voldoen aan het normale patroon van het SCF-hoofdelement door deze twee kenmerken te bevatten:

* **gegeven-component-id**

  Het effectieve pad naar de toegevoegde component.

* **gegeven-scf-component**

  The resourceType of the component.

Hieronder ziet u een voorbeeld van een component voor toegevoegde opmerkingen:

```xml
<div
    class="scf-commentsystem scf translation-commentsystem"
    data-component-id="<%= currentPage.getPath()%>/jcr:content/content-left/comments"
    data-scf-component="social/commons/components/hbs/comments"
>
</div>
```

## Sideload door SCF aan te roepen {#sideload-by-invoking-scf}

### Dynamische insluiting {#dynamic-inclusion}

De dynamische opneming gebruikt een laarzentrekkerverzoek dat in SCF onderzoek DOM resulteert en bootsrapping alle componenten SCF die op de pagina worden gevonden.

Als u SCF-componenten na het laden van de pagina wilt initialiseren, voert u gewoon een JQuery-gebeurtenis als volgt uit:

`$(document).trigger(SCF.events.BOOTSTRAP_REQUEST);`

### Dynamisch laden {#dynamic-loading}

Dynamisch laden biedt controle over het laden van SCF-componenten.

In plaats van alle SCF-componenten die in het DOM worden gevonden, te bootstrapping, is het mogelijk om een specifieke SCF-component op te geven die moet worden geladen met deze JavaScript-methode:

`SCF.addComponent(document.getElementById(*someId*));`

Waarbij `someId` de waarde van het kenmerk `data-component-id` is.
