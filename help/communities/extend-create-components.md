---
title: De componenten maken
description: Leer hoe u componenten uitbreidt met het opmerkingensysteem dat is samengesteld uit componenten Opmerkingen en Opmerkingen.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: 2e02db9f-294d-4d4a-92da-3ab1d38416ab
solution: Experience Manager
feature: Communities
role: Developer
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '548'
ht-degree: 0%

---

# De componenten maken  {#create-the-components}

Het voorbeeld om componenten uit te breiden gebruikt het commentaarsysteem, dat uit twee componenten bestaat.

* Opmerkingen - Het omvattende opmerkingensysteem dat de component is die op een pagina wordt geplaatst.
* Opmerking - De component die een instantie van een geposte opmerking vastlegt.

Beide componenten moeten worden geplaatst, vooral als het aanpassen van de verschijning van een geposte commentaar.

>[!NOTE]
>
>Er is slechts één opmerkingsysteem per sitepagina toegestaan.
>
>Vele eigenschappen van Gemeenschappen omvatten reeds een commentaarsysteem waarvan resourceType kan worden gewijzigd om het uitgebreide commentaarsysteem van verwijzingen te voorzien.

## De component Opmerkingen maken {#create-the-comments-component}

Deze richtingen specificeren a **waarde van de Groep** buiten `.hidden` zodat kan de component van componentenbrowser (sidekick) ter beschikking worden gesteld.

Het verwijderen van het automatisch gemaakte JSP-bestand komt doordat in plaats daarvan het standaard-HBS-bestand wordt gebruikt.

1. Blader naar **CRXDE|Lite** ([&#x200B; http://localhost:4502/crx/de/index.jsp &#x200B;](http://localhost:4502/crx/de/index.jsp))

1. Een locatie maken voor aangepaste toepassingen:

   * De node `/apps` selecteren

      * **creeer Omslag** genoemd **[!UICONTROL custom]**

   * De node `/apps/custom` selecteren

      * **creeer Omslag** genoemd **[!UICONTROL components]**

1. De node `/apps/custom/components` selecteren

   * **[!UICONTROL Create > Component...]**

      * **Etiket**: *commentaren*
      * **Titel**: *De Commentaren van Alt*
      * **Beschrijving**: *Alternatieve commentaarstijl*
      * **Type van Super**: *sociaal/komma&#39;s/componenten/hbs/commentaren*
      * **Groep**: *Douane*

   * Selecteren **[!UICONTROL Next]**
   * Selecteren **[!UICONTROL Next]**
   * Selecteren **[!UICONTROL Next]**
   * Selecteren **[!UICONTROL OK]**

1. Vouw het gemaakte knooppunt uit: `/apps/custom/components/comments`
1. Selecteren **[!UICONTROL Save All]**
1. Klikken met rechtermuisknop `comments.jsp`
1. Selecteren **[!UICONTROL Delete]**
1. Selecteren **[!UICONTROL Save All]**

![&#x200B; creeer-component &#x200B;](assets/create-component.png)

### De component Onderliggende opmerkingen maken {#create-the-child-comment-component}

Deze richtingen plaatsen **Groep** aan `.hidden` aangezien slechts de oudercomponent binnen een pagina zou moeten worden omvat.

Het verwijderen van het automatisch gemaakte JSP-bestand komt doordat in plaats daarvan het standaard-HBS-bestand wordt gebruikt.

1. Navigeren naar het knooppunt `/apps/custom/components/comments`
1. Klik met de rechtermuisknop op het knooppunt

   * Selecteren **[!UICONTROL Create]** > **[!UICONTROL Component...]**

      * **Etiket**: *commentaar*
      * **Titel**: *de Commentaar van Alt*
      * **Beschrijving**: *Alternatieve commentaarstijl*
      * **Type van Super**: *sociaal/komma&#39;s/componenten/hbs/commentaren/commentaar*
      * **Groep**: `*.hidden*`

   * Selecteren **[!UICONTROL Next]**
   * Selecteren **[!UICONTROL Next]**
   * Selecteren **[!UICONTROL Next]**
   * Selecteren **[!UICONTROL OK]**

1. Vouw het gemaakte knooppunt uit: `/apps/custom/components/comments/comment`
1. Selecteren **[!UICONTROL Save All]**
1. Klikken met rechtermuisknop `comment.jsp`
1. Selecteren **[!UICONTROL Delete]**
1. Selecteren **[!UICONTROL Save All]**

![&#x200B; creeer-kind-component &#x200B;](assets/create-child-component.png)

![&#x200B; creeer-component-crxde &#x200B;](assets/create-component-crxde.png)

### De standaard-HBS-scripts kopiëren en wijzigen {#copy-and-modify-the-default-hbs-scripts}

Gebruikend [&#x200B; CRXDE Lite &#x200B;](../../help/sites-developing/developing-with-crxde-lite.md):

* Kopiëren `comments.hbs`

   * Van [&#x200B; /libs/social/commons/components/hbs/comments](http://localhost:4502/crx/de/index.jsp#/libs/social/commons/components/hbs/comments)
   * Aan [&#x200B; /apps/custom/components/comments](http://localhost:4502/crx/de/index.jsp#/apps/custom/components/comments)

* Bewerken `comments.hbs` naar:

   * Wijzig de waarde van het kenmerk `data-scf-component` (~line 20):

      * Van `social/commons/components/hbs/comments`
      * Naar `/apps/custom/components/comments`

   * Wijzigen om de aangepaste commentaarcomponent op te nemen (~line 75):

      * Vervangen `{{include this resourceType='social/commons/components/hbs/comments/comment'}}`
      * Met `{{include this resourceType='/apps/custom/components/comments/comment'}}`

* Kopiëren `comment.hbs`

   * Van [&#x200B; /libs/social/commons/components/hbs/comments/comment &#x200B;](http://localhost:4502/crx/de/index.jsp#/libs/social/commons/components/hbs/comments/comment)
   * Aan [&#x200B; /apps/custom/components/comments/comment](http://localhost:4502/crx/de/index.jsp#/apps/custom/components/comments/comment)

* Bewerken `comment.hbs` naar:

   * De waarde van het kenmerk data-scf-component wijzigen (~ regel 19)

      * Van `social/commons/components/hbs/comments/comment`
      * Naar `/apps/custom/components/comments/comment`

* Knooppunt `/apps/custom` selecteren
* Selecteren **[!UICONTROL Save All]**

## Een clientbibliotheekmap maken {#create-a-client-library-folder}

Als u wilt voorkomen dat deze clientbibliotheek moet worden opgenomen, kunt u de categoriewaarde voor de clientlib van het standaardopmerkingssysteem gebruiken ( `cq.social.author.hbs.comments`). Nochtans, zou deze clientlib dan voor alle instanties van de standaardcomponent moeten worden omvat, ook.

Gebruikend [&#x200B; CRXDE Lite &#x200B;](../../help/sites-developing/developing-with-crxde-lite.md):

* Knooppunt `/apps/custom/components/comments` selecteren
* Selecteren **[!UICONTROL Create Node]**

   * **Naam**: `clientlibs`
   * **Type**: `cq:ClientLibraryFolder`
   * Toevoegen aan tabblad **[!UICONTROL Properties]** :

      * **Naam** `categories` **Type** `String` **Waarde** `cq.social.author.hbs.comments` `Multi`
      * **Naam** `dependencies` **Type** `String` **Waarde** `cq.social.scf` `Multi`

* Selecteren **[!UICONTROL Save All]**
* Met `/apps/custom/components/comments/clientlib` geselecteerde knoop, creeer drie dossiers:

   * **Naam**: `css.txt`
   * **Naam**: `js.txt`
   * **Naam**: customcommentsystem.js

* Voer &#39;customcommentsystem.js&#39; in als de inhoud van `js.txt`
* Selecteren **[!UICONTROL Save All]**

![&#x200B; commentaren-clientlibs &#x200B;](assets/comments-clientlibs.png)

## Het SCF-model en de weergave registreren {#register-the-scf-model-view}

Bij het uitbreiden (met voeten treden) van een component SCF, is resourceType verschillend (het bedekken gebruikt het relatieve onderzoeksmechanisme dat door `/apps` vóór `/libs` zoekt zodat resourceType het zelfde blijft). Daarom is het noodzakelijk om JavaScript (in de cliëntbibliotheek) te schrijven om het model SCF JS en de mening voor custom resourceType te registreren.

Voer de volgende tekst in als de inhoud van `customcommentsystem.js` :

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

* Selecteren **[!UICONTROL Save All]**

## De app Publish {#publish-the-app}

Als u de uitgebreide component wilt ervaren in de publicatieomgeving, moet u de aangepaste component repliceren.

Een manier om dit te doen is:

* Van globale navigatie,

   * Selecteer **[!UICONTROL Tools]** > **[!UICONTROL Deployment]** > **[!UICONTROL Replication]**
   * Selecteren **[!UICONTROL Activate Tree]**
   * `Start Path` instellen op `/apps/custom`
   * Uitschakelen **[!UICONTROL Only Modified]**
   * Knop Selecteren **[!UICONTROL Activate]**
