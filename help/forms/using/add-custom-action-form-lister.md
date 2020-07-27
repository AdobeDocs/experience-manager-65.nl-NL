---
title: Aangepaste actie toevoegen aan formulierbibliotheekitems
seo-title: Aangepaste actie toevoegen aan formulierbibliotheekitems
description: Formulierontwikkelaars kunnen meer acties toevoegen aan de lijst met formulieren op de pagina Formulierportal. Standaard kunt u het formulier openen, invullen en verzenden.
seo-description: Formulierontwikkelaars kunnen meer acties toevoegen aan de lijst met formulieren op de pagina Formulierportal. Standaard kunt u het formulier openen, invullen en verzenden.
uuid: 5703ba27-7fb8-482e-b933-a060574165dc
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: customization
discoiquuid: c34dd4c2-5fff-4355-b86d-cc8a956dd8af
docset: aem65
translation-type: tm+mt
source-git-commit: 1343cc33a1e1ce26c0770a3b49317e82353497ab
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---


# Aangepaste actie toevoegen aan formulierbibliotheekitems{#adding-custom-action-on-form-lister-items}

In AEM Forms kunt u een poortpagina maken met de beschikbare formulieren. Standaard kunt u formulieren zoeken en weergeven op een portalpagina. U kunt formulieren openen om uw gegevens in te vullen en te verzenden. Alleen renderacties worden in het vak weergegeven voor formulieren die op een portalpagina worden vermeld. Zie [Een pagina](../../forms/using/creating-form-portal-page.md)met een formulierportal maken voor meer informatie over de beschikbare acties op een poortpagina.

U kunt andere opties aan de portalpagina toevoegen. Deze opties of acties kunnen worden aangepast door de sjabloon van het formulierportaal aan te passen.

In dit artikel wordt uitgelegd hoe u een knop kunt maken om de koppeling van een formulier rechtstreeks vanaf een pagina op een formulierportal te verzenden. Voor deze aanpassing moet de sjabloon voor de component Search &amp; Lister worden bijgewerkt.

De vereiste code om de actie aan het malplaatje toe te voegen is beschikbaar hieronder. Het `onclick` kenmerk in het codefragment bevat een script waarmee een koppeling van een formulier via e-mail wordt verzonden.

```html
<div class="__FP_boxes-container __FP_single-color">
    <div class="boxes __FP_boxes __FP_single-color" data-repeatable="true">
  <div class="__FP_boxes-thumbnail">
            <img src ="${contextPath}${path}/jcr:content/renditions/cq5dam.thumbnail.319.319.png">
        </div>
        <h3 class="__FP_single-color" title="${name}" tabindex="0">${name}</h3>
        <p>${description}</p>
        <div class="boxes-icon-cont __FP_boxes-icon-cont">
            <div class="op-dow">
                <a href="${formUrl}" target="_blank" class="__FP_button ${htmlStyle}" title="${config-htmlLinkText}">Apply</a>
                <a class="__FP_button" title="Email a friend" href="#" onclick="javascript:window.location=&apos;mailto:?subject=Interesting information&body=I thought you might find {name} form helpful :  &apos;+window.location.protocol+window.location.host+&apos;${formUrl}&apos; ;">Email</a>
                <a href="${pdfUrl}" class="__FP_button ${pdfStyle}" title="${config-pdfLinkText}">Download</a>
            </div>
        </div>
    </div>
</div>
```

U kunt vergelijkbare acties toevoegen aan uw aangepaste sjabloon. Als u een JavaScript-functie wilt definiëren, voegt u de functie toe aan een script op paginaniveau en koppelt u deze aan het vereiste HTML-element. In het bovenstaande voorbeeld is de `onclick` expressie de gekoppelde functie.

Nadat u de wijzigingen in de sjabloon hebt aangebracht, bevat de pagina met de voorbeeldportal een knop waarmee u de koppeling van het formulier via e-mail kunt verzenden, zoals hieronder wordt weergegeven.

![email](assets/email.png)

