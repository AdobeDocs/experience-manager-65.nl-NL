---
title: De componenten maken
seo-title: De componenten maken
description: De component Opmerkingen maken
seo-description: De component Opmerkingen maken
uuid: ea6e00d4-1db7-40ef-ae49-9ec55df58adf
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 83c4f18a-d7d6-4090-88c7-41a9075153b5
translation-type: tm+mt
source-git-commit: 0b25d956c19c5fc5d79f87b292a0c61a23e5d66a

---


# De componenten maken {#create-the-components}

In het voorbeeld van het uitbreiden van componenten wordt het opmerkingssysteem gebruikt, dat eigenlijk uit twee componenten bestaat

* Opmerkingen - Het omvattende opmerkingensysteem dat de component is die op een pagina wordt geplaatst
* Opmerking - De component die een instantie van een geposte opmerking vastlegt

Beide componenten moeten worden geplaatst, vooral als het aanpassen van de verschijning van een geposte commentaar.

>[!NOTE]
>
>Er is slechts één opmerkingsysteem per sitepagina toegestaan.
>
>Vele eigenschappen van Gemeenschappen omvatten reeds een commentaarsysteem waarvan resourceType kan worden gewijzigd om het uitgebreide commentaarsysteem van verwijzingen te voorzien.

## De component Opmerkingen maken {#create-the-comments-component}

Deze richtingen specificeren een waarde van de **Groep** buiten `.hidden` zodat kan de component van componentenbrowser (sidekick) ter beschikking worden gesteld.

De verwijdering van het automatisch gemaakte JSP-bestand komt doordat in plaats daarvan het standaard-HBS-bestand wordt gebruikt.

1. Bladeren naar **CRXDE|Lite** ([http://localhost:4502/crx/de/index.jsp](http://localhost:4502/crx/de/index.jsp))

1. Een locatie maken voor aangepaste toepassingen:

   * Selecteer het `/apps` knooppunt

      * **Map** maken met de naam **[!UICONTROL custom]**
   * Selecteer het `/apps/custom` knooppunt

      * **Map** maken met naam **[!UICONTROL componenten]**


1. Selecteer het `/apps/custom/components` knooppunt

   * **[!UICONTROL Maken > Component...]**

      * **Label**: *opmerkingen*
      * **Titel**: Opmerkingen *Alt*
      * **Omschrijving**: Stijl *van alternatieve opmerkingen*
      * **Supertype**: *social/commons/components/hbs/comments*
      * **Groep**: *Aangepast*
   * Selecteer **[!UICONTROL Volgende]**
   * Selecteer **[!UICONTROL Volgende]**
   * Selecteer **[!UICONTROL Volgende]**
   * Selecteer **[!UICONTROL OK]**


1. Vouw het zojuist gemaakte knooppunt uit: `/apps/custom/components/comments`
1. Alles **[!UICONTROL opslaan selecteren]**
1. Klikken met rechtermuisknop `comments.jsp`
1. Selecteren **[!UICONTROL Verwijderen]**
1. Alles **[!UICONTROL opslaan selecteren]**

![chlimage_1-70](assets/chlimage_1-70.png)

### De component Onderliggende opmerkingen maken {#create-the-child-comment-component}

Deze richtingen plaatsen **Groep** aan `.hidden` aangezien slechts de oudercomponent binnen een pagina zou moeten worden omvat.

De verwijdering van het automatisch gemaakte JSP-bestand komt doordat in plaats daarvan het standaard-HBS-bestand wordt gebruikt.

1. Navigate to the `/apps/custom/components/comments` node
1. Klik met de rechtermuisknop op het knooppunt

   * Selecteer **[!UICONTROL Maken > Component...]**

      * **Label**: *opmerking*
      * **Titel**: Opmerking *Alt*
      * **Omschrijving**: *Alternatieve commentaarstijl*
      * **Supertype**: *social/commons/components/hbs/comments/comment*
      * **Groep**: `*.hidden*`
   * Selecteer **[!UICONTROL Volgende]**
   * Selecteer **[!UICONTROL Volgende]**
   * Selecteer **[!UICONTROL Volgende]**
   * Selecteer **[!UICONTROL OK]**


1. Vouw het zojuist gemaakte knooppunt uit: `/apps/custom/components/comments/comment`
1. Alles **[!UICONTROL opslaan selecteren]**
1. Klikken met rechtermuisknop `comment.jsp`
1. Selecteren **[!UICONTROL Verwijderen]**
1. Alles **[!UICONTROL opslaan selecteren]**

![chlimage_1-71](assets/chlimage_1-71.png) ![chlimage_1-72](assets/chlimage_1-72.png)

### De standaard-HBS-scripts kopiëren en wijzigen {#copy-and-modify-the-default-hbs-scripts}

Met [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md):

* Kopiëren `comments.hbs`

   * Van [/libs/social/commons/components/hbs/comments](http://localhost:4502/crx/de/index.jsp#/libs/social/commons/components/hbs/comments)
   * To [/apps/custom/components/comments](http://localhost:4502/crx/de/index.jsp#/apps/custom/components/comments)

* Bewerken `comments.hbs` naar:

   * Wijzig de waarde van het `data-scf-component` kenmerk (~line 20):

      * From `social/commons/components/hbs/comments`
      * Naar `/apps/custom/components/comments`
   * Wijzigen om de aangepaste commentaarcomponent op te nemen (~line 75):

      * Replace `{{include this resourceType='social/commons/components/hbs/comments/comment'}}`
      * Met `{{include this resourceType='/apps/custom/components/comments/comment'}}`


* Kopiëren `comment.hbs`

   * Van [/libs/social/commons/components/hbs/comments/comment](http://localhost:4502/crx/de/index.jsp#/libs/social/commons/components/hbs/comments/comment)
   * To [/apps/custom/components/comments/comment](http://localhost:4502/crx/de/index.jsp#/apps/custom/components/comments/comment)

* Bewerken `comment.hbs` naar:

   * De waarde van het kenmerk data-scf-component wijzigen (~ regel 19)

      * From `social/commons/components/hbs/comments/comment`
      * Naar `/apps/custom/components/comments/comment`

* Knooppunt `/apps/custom` selecteren
* Alles **[!UICONTROL opslaan selecteren]**

## Een clientbibliotheekmap maken {#create-a-client-library-folder}

Als u wilt voorkomen dat deze clientbibliotheek expliciet moet worden opgenomen, kunt u de categoriewaarde voor de clientlib van het standaardopmerkingssysteem gebruiken ( `cq.social.author.hbs.comments`), maar dan wordt deze clientlib ook opgenomen voor alle instanties van de standaardcomponent.

Met [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md):

* Knooppunt `/apps/custom/components/comments` selecteren
* Knooppunt **[!UICONTROL maken selecteren]**

   * **Naam**: `clientlibs`
   * **Type**: `cq:ClientLibraryFolder`
   * Toevoegen aan tabblad **[!UICONTROL Eigenschappen]** :

      * **Naam** `categories` Type **** Waarde `String` **** `cq.social.author.hbs.comments``Multi`
      * **Naam** `dependencies` Type **** Waarde `String` **** `cq.social.scf``Multi`

* Alles **[!UICONTROL opslaan selecteren]**
* Selecteer `/apps/custom/components/comments/clientlib`het knooppunt, maak 3 bestanden:

   * **Naam**: `css.txt`
   * **Naam**: `js.txt`
   * **Naam**: customcommentsystem.js

* Voer &#39;customcommentsystem.js&#39; in als de inhoud van `js.txt`
* Alles **[!UICONTROL opslaan selecteren]**

![chlimage_1-73](assets/chlimage_1-73.png)

## Het SCF-model en de weergave registreren {#register-the-scf-model-view}

Wanneer het uitbreiden van (het met voeten treden) een component SCF, is resourceType verschillend (het bedekken maakt gebruik van het relatieve onderzoeksmechanisme dat `/apps` alvorens zoekt `/libs` zodat resourceType het zelfde blijft). Daarom is het noodzakelijk om JavaScript (in de cliëntbibliotheek) te schrijven om het model SCF JS en mening voor custom resourceType te registreren.

Voer de volgende tekst in als de inhoud van `customcommentsystem.js`:

### customcommentsystem.js {#customcommentsystem-js}

```xml
(function($CQ, _, Backbone, SCF) {
    "use strict";

    var CustomComment = SCF.Components["social/commons/components/hbs/comments/comment"].Model;
    var CustomCommentView = SCF.Components["social/commons/components/hbs/comments/comment"].View;

    var CustomCommentSystem = SCF.Components["social/commons/components/hbs/comments"].Model;
    var CustomCommentSystemView = SCF.Components["social/commons/components/hbs/comments"].View;

    SCF.registerComponent('/apps/custom/components/comments/comment', CustomComment, CustomCommentView);
    SCF.registerComponent('/apps/custom/components/comments', CustomCommentSystem, CustomCommentSystemView);

})($CQ, _, Backbone, SCF);
```

* Alles **[!UICONTROL opslaan selecteren]**

## De app publiceren {#publish-the-app}

Als u de uitgebreide component wilt ervaren in de publicatieomgeving, moet u de aangepaste component repliceren.

Een manier om dit te doen is

* Van globale navigatie

   * Selecteer **[!UICONTROL Gereedschappen > Implementatie > Replicatie]**
   * Selecteer `Activate Tree`
   * Instellen `Start Path`: tot `/apps/custom`
   * Uitschakelen `Only Modified`
   * Selecteren, `Activate`knop

