---
title: Essentiële elementen van de Rich Text Editor
description: Leer over de grondbeginselen en de eigenschappen van een Rich Text Editor die u tekst met prijsverhoging laat ingaan.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: 821e32f4-da8d-4bbb-936a-0844b8a24cdd
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 0%

---

# Essentiële elementen van de Rich Text Editor {#rich-text-editor-essentials}

## Overzicht {#overview}

Met een Rich Text Editor (RTE) kunt u tekst met opmaak invoeren.

Voor de componenten van Gemeenschappen, terwijl gelijkend op de [&#x200B; rijke tekstredacteur in het auteursmilieu &#x200B;](../../help/sites-authoring/rich-text-editor.md), beïnvloedt het tekst ingegaan in het publicatiemilieu.

![&#x200B; rijk-text-redacteur &#x200B;](assets/rich-text-editor.png)

## RTF-editor inschakelen {#enabling-rich-text-editor}

De componenten van gemeenschappen die gebruiker geproduceerde inhoud (UGC) toestaan kunnen worden toegelaten om RTE toe te staan. Als de component aan een pagina werd toegevoegd of inbegrepen binnen a [&#x200B; functie &#x200B;](functions.md), kan RTE of niet door gebrek worden toegelaten.

Als niet toegelaten, ga eenvoudig [&#x200B; auteur in geef wijze &#x200B;](sites-console.md#authoring-site-content) uit, selecteer de component voor geef uit, en selecteer `Rich Text Editor` checkbox.

RTE is beschikbaar voor de volgende componenten van de Gemeenschappen:

* [Blog](blog-feature.md)
* [Kalender](calendar.md)
* [Opmerkingen](comments.md)
* [FileLibrary](file-library.md)
* [Forum](forum.md)
* [Berichten](configure-messaging.md)
* [QnA](working-with-qna.md)
* [Revisies](reviews.md)

## Aanpassing {#customization}

De aanpassing van de rijke tekstredacteur is mogelijk aangezien de implementatie op [&#x200B; CKEditor &#x200B;](https://ckeditor.com/) wordt gebaseerd.

De huidige configuratie voor componenten van Communities bevindt zich in de `cq.social.  scf   clientlib` , in de repository op

`/libs/clientlibs/social/commons/scf/ckrte.js`

Het wijzigen van de client lib cq.social.scf wordt niet aangeraden, omdat toekomstige upgrades mogelijk alle bewerkingen overschrijven.

### Voorbeeld-aanpassing: inline koppelingen {#example-customization-inline-links}

Vanwege beveiligingsproblemen zijn de hyperlinkopties niet opgenomen in de set met RTF-pictogrammen die standaard aan leden worden gepresenteerd. De mogelijkheid tot stuipen is uitgebreid wanneer hrefs in UGC zijn toegestaan.

De hyperlinkopties toevoegen aan de werkbalk:

* Een werkbalk met de naam &quot; `links`&quot; toevoegen
   * `{ name: 'links', items: [ 'Link','Unlink','Anchor' ] }`
* Selecteren **[!UICONTROL Save All]**

#### /libs/clientlibs/social/commons/scf/ckrte.js {#libs-clientlibs-social-commons-scf-ckrte-js}

```
CKRte.prototype.config = {
    toolbar: [
        { name: "basicstyles",
           items: ["Bold", "Italic", "Underline", "NumberedList", "BulletedList", "Outdent", "Indent", "JustifyLeft", "JustifyCenter", "JustifyRight", "JustifyBlock", "TextColor"]
        },
        { name: 'links',
           items: [ 'Link','Unlink','Anchor' ]
        }
    ],
    autoParagraph: false,
    autoUpdateElement: false,
    removePlugins: "elementspath",
    resize_enabled: false
};
```
