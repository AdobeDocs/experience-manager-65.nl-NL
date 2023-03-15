---
title: Essentiële elementen van de Rich Text Editor
seo-title: Rich Text Editor Essentials
description: Overzicht van de functie Rich Text Editor
seo-description: Rich text Editor feature overview
uuid: f96015cc-114b-431a-a5ba-dc195c2a0b83
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 0225a543-0fad-488b-8b0b-8b3512d44fbe
exl-id: 821e32f4-da8d-4bbb-936a-0844b8a24cdd
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 1%

---

# Essentiële elementen van de Rich Text Editor {#rich-text-editor-essentials}

## Overzicht {#overview}

Een Rich Text Editor (RTE) biedt de mogelijkheid om tekst met opmaak in te voeren.

Voor communautaire componenten, terwijl gelijkaardig aan [RTF-editor in de ontwerpomgeving](../../help/sites-authoring/rich-text-editor.md), heeft dit invloed op tekst die wordt ingevoerd in de publicatieomgeving.

![rich-text-editor](assets/rich-text-editor.png)

## RTF-editor inschakelen {#enabling-rich-text-editor}

De componenten van gemeenschappen die gebruiker geproduceerde inhoud (UGC) toestaan kunnen worden toegelaten om RTE toe te staan. Afhankelijk van of de component aan een pagina is toegevoegd of binnen een [function](functions.md), kan RTE door gebrek worden toegelaten of niet.

Als deze optie niet is ingeschakeld, voert u gewoon de invoer in [bewerkingsmodus auteur](sites-console.md#authoring-site-content)selecteert u de component die u wilt bewerken en selecteert u de component `Rich Text Editor` selectievakje.

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

Aanpassing van de rijke teksteditor is mogelijk omdat de implementatie is gebaseerd op [CKEditor](https://www.ckeditor.com/).

De huidige configuratie voor communautaire componenten is in de `cq.social.  scf   clientlib`, gevestigd in de gegevensopslagruimte op

`/libs/clientlibs/social/commons/scf/ckrte.js`

Het wijzigen van de client lib cq.social.scf wordt niet aangeraden, omdat toekomstige upgrades mogelijk alle bewerkingen overschrijven.

### Voorbeeld van aanpassing: Inline-koppelingen {#example-customization-inline-links}

Vanwege beveiligingsproblemen zijn de hyperlinkopties niet opgenomen in de set met RTF-pictogrammen die standaard aan leden worden gepresenteerd. De mogelijkheid tot stuipen is uitgebreid wanneer hrefs in UGC zijn toegestaan.

De hyperlinkopties toevoegen aan de werkbalk:

* Een werkbalk toevoegen met de naam &quot; `links`&quot;
   * `{ name: 'links', items: [ 'Link','Unlink','Anchor' ] }`
* Selecteer **[!UICONTROL Save All]**

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
