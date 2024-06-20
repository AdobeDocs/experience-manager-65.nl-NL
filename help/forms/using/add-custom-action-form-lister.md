---
title: Aangepaste actie toevoegen aan formulierbibliotheekitems
description: Formulierontwikkelaars kunnen meer acties toevoegen aan de lijst met formulieren op de pagina Formulierportal. Standaard kunt u het formulier openen, invullen en verzenden.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: customization
docset: aem65
exl-id: 7c2a91c8-9b68-4491-88e2-f7ea68f5a79f
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: 872e2de411f51b5f0b26a2ff47cb49f01313d39f
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---

# Aangepaste actie toevoegen aan formulierbibliotheekitems{#adding-custom-action-on-form-lister-items}

In AEM Forms kunt u een poortpagina maken met de beschikbare formulieren. Standaard kunt u formulieren zoeken en weergeven op een portalpagina. U kunt formulieren openen om uw gegevens in te vullen en te verzenden. Alleen renderacties worden in het vak weergegeven voor formulieren die op een portalpagina worden vermeld. Voor meer informatie over de beschikbare acties op een portalpagina raadpleegt u [Een pagina met een portal voor formulieren maken](../../forms/using/creating-form-portal-page.md).

U kunt andere opties aan de portalpagina toevoegen. Deze opties of acties kunnen worden aangepast door de sjabloon van het formulierportaal aan te passen.

In dit artikel wordt uitgelegd hoe u een knop kunt maken om de koppeling van een formulier rechtstreeks vanaf een pagina op een formulierportal te verzenden. Voor deze aanpassing moet de sjabloon voor de component Search &amp; Lister worden bijgewerkt.

De vereiste code om de actie aan het malplaatje toe te voegen is beschikbaar hieronder. De `onclick` in het codefragment bevat een script waarmee een koppeling van een formulier via e-mail wordt verzonden.

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

U kunt vergelijkbare acties toevoegen aan uw aangepaste sjabloon. Als u een JavaScript-functie wilt definiëren, voegt u de functie toe aan een script op paginaniveau en koppelt u deze aan het vereiste HTML-element. In het bovenstaande voorbeeld wordt `onclick` expression is the linked function.

Nadat u de wijzigingen in de sjabloon hebt aangebracht, bevat de pagina met de voorbeeldportal een knop waarmee u de koppeling van het formulier via e-mail kunt verzenden, zoals hieronder wordt weergegeven.

![email](assets/email.png)
