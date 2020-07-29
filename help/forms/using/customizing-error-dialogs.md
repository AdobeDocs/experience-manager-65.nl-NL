---
title: Foutdialoogvensters aanpassen
seo-title: Foutdialoogvensters aanpassen
description: Hoe kan ik-om de foutendialogen van de werkruimte van LiveCycle AEM Forms aan te passen om verschillende foutenbeschrijvingen toe te voegen.
seo-description: Hoe kan ik-om de foutendialogen van de werkruimte van LiveCycle AEM Forms aan te passen om verschillende foutenbeschrijvingen toe te voegen.
uuid: 5ed1da68-bd5b-4a36-9a14-9d61733237e6
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: f547c0c1-3917-4092-9d63-c1b3aaefcef0
translation-type: tm+mt
source-git-commit: 07abce0e6e4d1a299ce32ab130366b4e676b6388
workflow-type: tm+mt
source-wordcount: '170'
ht-degree: 4%

---


# Foutdialoogvensters aanpassen {#customizing-error-dialogs}

In de werkruimte AEM Forms kunt u de foutmeldingen aanpassen. Voer de [algemene stappen voor de aanpassing](/help/forms/using/generic-steps-html-workspace-customization.md) van de werkruimte AEM Forms uit, gevolgd door de onderstaande stappen, om foutmeldingen aan te passen.

## Tekst aanpassen {#customizing-text}

1. Wijzig in het `/apps/ws/locales/en-US/translation.json` bestand de waarden van `wserror` de aangepaste waarden. Bijvoorbeeld:

   ```json
   "wserror" : {
    "message" : "Message:",
    "ComponentUI" : "Component UI:",
    "error" : "Error",
    "ok" : "Ok",
    "ErrorCode" : "Error Code:"
    }
   ```

   Naar

   ```json
    "wserror" : {
    "message" : "Error Message:",
    "ComponentUI" : "UI Component:",
    "error" : "Something went wrong!!",
    "ok" : "Ok",
    "ErrorCode" : "Error Code:"
    }
   ```

   >[!NOTE]
   >
   >Voeg overeenkomstige sleutel-waarde paren voor alle gesteunde talen toe.

## CSS aanpassen {#customizing-css}

1. U kunt dialoogvensters, koptekst, inhoudsgebied, voetbalk, voetbalknoppen en andere elementen bijwerken door het volgende fragment toe te voegen in het `/apps/ws/css/newStyle.css` bestand:

   ```css
   /*-------- Error Dialog -------------------------------------------------------------------------------------------------------------------*/
   .error-dialog{
       border: 2px solid #DEDEDE;
       width: 540px;
       height: 400px;
       position: absolute;
       z-index: 99999;
       left: 50%;
       margin-left: -271px;
       background:#2b2b2b;
       box-shadow:0px 0px 10px 3px #888;
       display:none;
   }
   .error-dialog .head-bar{
       height: 31px;
       background: url(../images/error.png) no-repeat 7px 10px #DEDEDE;
       color: #2B2B2B;
       font-size: 18px;
       padding-left: 30px;
       padding-top: 7px;
       text-overflow: ellipsis;
       overflow: hidden;
       white-space: nowrap;
   }
   .error-dialog .content-area{
       padding: 20px;
       border-bottom: 1px solid #1B1B1B;
       height: 268px;
   }
   .error-dialog .foot-bar{
       border-top: 1px solid #404040;
       height: 32px;
       padding:10px;
       text-align: right;
   }
   .error-dialog .foot-bar button{
       background: #52a1dc; /* Old browsers */
       background: -moz-linear-gradient(top,  #52a1dc 0%, #2680ce 100%, #207cca 100%, #2989d8 100%, #207cca 100%); /* FF3.6+ */
       background: -webkit-gradient(linear, left top, left bottom, color-stop(0%,#52a1dc), color-stop(100%,#2680ce), color-stop(100%,#207cca), color-stop(100%,#2989d8), color-stop(100%,#207cca)); /* Chrome,Safari4+ */
       background: -webkit-linear-gradient(top,  #52a1dc 0%,#2680ce 100%,#207cca 100%,#2989d8 100%,#207cca 100%); /* Chrome10+,Safari5.1+ */
       background: -o-linear-gradient(top,  #52a1dc 0%,#2680ce 100%,#207cca 100%,#2989d8 100%,#207cca 100%); /* Opera 11.10+ */
       background: -ms-linear-gradient(top,  #52a1dc 0%,#2680ce 100%,#207cca 100%,#2989d8 100%,#207cca 100%); /* IE10+ */
       background: linear-gradient(to bottom,  #52a1dc 0%,#2680ce 100%,#207cca 100%,#2989d8 100%,#207cca 100%); /* W3C */
       filter: progid:DXImageTransform.Microsoft.gradient( startColorstr='#52a1dc', endColorstr='#2680ce',GradientType=0 ); /* IE6-9 */
       border: #4F748F;
       height: 30px;
       width: 100px;
       font-size: 18px;
       color: white;
   
   }
   .error-dialog .single-col{
       width: 100%;
       list-style-type: none;
       padding: 0px;
       margin: 0px;
   }
   .error-dialog .single-col li{
       height: 28px;
       font-size:14px;
       color:#bebebe;
       text-overflow: ellipsis;
       overflow: hidden;
       white-space: nowrap;
   }
   .error-dialog .single-col li label{
       height: 28px;
       color:#fff;
       max-width:100px;
       margin-right: 14px;
       text-overflow: ellipsis;
       overflow: hidden;
       white-space: nowrap;
       float: left;
   }
   .error-dialog .double-col{
       width: 100%;
       list-style-type: none;
       padding: 0px;
       margin:0px;
   }
   .error-dialog .double-col li{
       height: 28px;
       font-size:14px;
       color:#bebebe;
       width: 50%;
       float: left;
       text-overflow: ellipsis;
       white-space: nowrap;
       overflow: hidden;
   }
   .error-dialog .double-col li.small{
       width: 30%;
   }
   .error-dialog .double-col li.big{
       width: 70%;
   }
   .error-dialog .double-col li label{
       height: 28px;
       color:#fff;
       max-width:100px;
       margin-right: 14px;
       text-overflow: ellipsis;
       overflow: hidden;
       white-space: nowrap;
       float: left;
   }
   .error-dialog .scroll-content{
       color:#bebebe;
       font-size:12px;
       height:175px;
       overflow-y:scroll;
       overflow-x:hidden;
       width:100%;
   
   }
   
   .error-background, .popup-background, .wsMessageBackGround, .userInfoBackGround, .busyState, .aboutWorkspaceBG {
       width: 100%;
       height: 100%;
       display: none;
       opacity: 0.6;
       background-color: black;
       left: 0px;
       top: 0px;
       position: fixed;
       z-index: 999;
       margin: 0px;
       padding: 0px;
   }
   ```

1. Voor het bereik van de voetbalkknop scheidt u de `.error-dialog` `.foot-bar` knopbereiken en de knopbereiken van de samengestelde lijst. U brengt deze wijziging door het volgende toe te voegen in het bestand newStyle.css:

   ```css
   .browse-btn span, .attachementbtn span, .cancelAttachmentUpdate span, #taskAttachmentsContainer .uploadStatus span, .submitNoteButton span, .updateNoteButton span, .cancelNoteUpdate span,
   #userSearchPopUp #actionbar span, #taskarea .action button span, .error-dialog .foot-bar button span, .oooAction button span, .wsMessageContainerDiv .action button span
   {
       display: block;
       text-overflow: ellipsis;
       white-space: nowrap;
       overflow: hidden;
   }
   ```

   Naar

   ```css
   .browse-btn span, .attachementbtn span, .cancelAttachmentUpdate span, #taskAttachmentsContainer .uploadStatus span, .submitNoteButton span, .updateNoteButton span, .cancelNoteUpdate span,
   #userSearchPopUp #actionbar span, #taskarea .action button span, .oooAction button span, .wsMessageContainerDiv .action button span
   {
       display: block;
       text-overflow: ellipsis;
       white-space: nowrap;
       overflow: hidden;
   }
   
   /*-------- Customized following Portion --------*/
   .error-dialog .foot-bar button span
   {
       display: block;
       text-overflow: ellipsis;
       text-decoration:underline;
       white-space: wrap;
   }
   ```

>[!NOTE]
>
>Als u naar extra afbeeldingen verwijst, voegt u deze toe in de gewenste hiërarchie onder `/apps/ws/images`.

## Voorbeelden {#examples}

* **Als u het dialoogvenster met fouten wilt aanpassen, wijzigt u:**

```css
.error-dialog{
    border: 2px solid #DEDEDE;
    width: 540px;
    height: 400px;
    position: absolute;
    z-index: 99999;
    left: 50%;
    margin-left: -271px;
    background:#2b2b2b;
    box-shadow:0px 0px 10px 3px #888;
    display:none;
}
```

Naar

```css
.error-dialog{
    border: 9px solid #DEDEDE;
    width: 200px;
    height: 200px;
    position: absolute;
    z-index: 99999;
    left: 50%;
    margin-left: -271px;
    background: url(../images/my-error-bg.png) no-repeat 7px 10px #DEDEDE;
    box-shadow:0px 0px 10px 3px #888;
    display:none;
}
```

* **Als u de koptekst van het foutvenster wilt aanpassen, wijzigt u:**

```css
.error-dialog .head-bar{
    height: 31px;
    background: url(../images/error.png) no-repeat 7px 10px #DEDEDE;
    color: #2B2B2B;
    font-size: 18px;
    padding-left: 30px;
    padding-top: 7px;
    text-overflow: ellipsis;
    overflow: hidden;
    white-space: nowrap;
}
```

Naar

```css
.error-dialog .head-bar{
    height: 40px;
    background: url(../images/error.png) no-repeat 7px 10px #DEDEDE;
    color: #FA0E39;
    font-size: 18px;
    padding-left: 30px;
    padding-top: 15px;
}
```
