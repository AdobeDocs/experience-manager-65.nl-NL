---
title: De weergave wijzigen (GB)
seo-title: De vormgeving wijzigen
description: De HBS-scripts wijzigen
seo-description: De HBS-scripts wijzigen
uuid: cff24505-dbb3-4312-9b1b-c1693b8d1c98
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: e0da09b3-725d-4ed1-9273-2532132f6918
docset: aem65
translation-type: tm+mt
source-git-commit: 570c970c328ded828680baeb1b04ab4361a36226
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---


# De weergave wijzigen (GB) {#alter-the-appearance-hbs}

Nu de componenten voor het systeem van de douanecommentaar in de toepassingsfolder (/apps) op zijn plaats zijn, met een resourceSuperType die naar het standaardcommentaarsysteem en het aangepaste Model/Beeld verwijzen geregistreerd, is het mogelijk om de implementatie te wijzigen.

Voor een eenvoudige demonstratie, een visuele functie, wordt de avatar verwijderd die wordt getoond van de aangemelde gebruiker die een opmerking plaatst.

>[!NOTE]
>
>Als u de extensie wilt gebruiken, moet de instantie van het opmerkingensysteem in een website die wordt beïnvloed (content), het resourceType instellen op het aangepaste opmerkingssysteem.


## De HBS-scripts wijzigen {#modify-the-hbs-scripts}

Met [CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md):

* Openen [/apps/custom/components/comments/comment/**comment.hbs**](https://localhost:4502/crx/de/index.jsp#/apps/custom/components/comments/comment/comment.hbs)

   * Plaats een opmerking bij de tag die de avatar bevat voor een commentaarbericht (~ regel 21):

      ```
        <!--
         <<img class="scf-comment-avatar {{#if topLevel}}withTopLevel{{/if}}" src="{{author.avatarUrl}}"></img>
         -->
      ```

* Openen [/apps/custom/components/comments/**comments.hbs**](https://localhost:4502/crx/de/index.jsp#/apps/custom/components/comments/comments.hbs)

   * Verwijder de commentaarmarkering die de avatar voor de volgende commentaaringang (~ lijn 44) omvat:

      ```
        <!--
         <img class="scf-composer-avatar" src="{{loggedInUser.avatarUrl}}"></img>
         -->
      ```

* Alles **opslaan selecteren**

### Aangepaste app repliceren {#replicate-custom-app}

Nadat de toepassing is gewijzigd, moet de aangepaste component opnieuw worden gerepliceerd.

Een manier om dit te doen is:

* Vanuit het hoofdmenu

   * Selecteer **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Replication]**.
   * Selecteer **[!UICONTROL Activate Tree]**.
   * Instellen `Start Path` op `/apps/custom`.
   * Deselecteer **[!UICONTROL Only Modified]**.
   * Selecteer **[!UICONTROL Activate]** de knop.

### Gewijzigde opmerking weergeven op gepubliceerde voorbeeldpagina {#view-modified-comment-on-published-sample-page}

[Als u doorgaat met de ervaring](/help/communities/extend-sample-page.md#publish-sample-page) met het publicatieexemplaar, dat nog steeds is aangemeld als dezelfde gebruiker, kunt u de pagina nu vernieuwen in de publicatieomgeving om de wijziging te bekijken om de avatar te verwijderen:

![view-modified-content](assets/view-modified-content.png)

### Voorbeeld van extensiepakket voor opmerkingen {#sample-comment-extension-package}

Bijgevoegd is een pakket van de toepassing van douanecommentaren die in dit leerprogramma wordt gecreeerd.

[Bestand ophalen](assets/sample-comment-extension-6-1-fp3.zip)
