---
title: De weergave wijzigen (GB)
description: Leer hoe u de weergave (HBS) wijzigt door de HBS-scripts te bewerken.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
docset: aem65
exl-id: 27e1bff3-385e-4ced-87af-54044b7e8812
solution: Experience Manager
feature: Communities
role: Developer
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---

# De weergave wijzigen (GB) {#alter-the-appearance-hbs}

Nu de componenten voor het systeem van de douanecommentaar in de toepassingsfolder (/apps) op zijn plaats zijn, met een resourceSuperType die naar het standaardcommentaarsysteem verwijzen, en het aangepaste Model/Beeld geregistreerde, kunt u de implementatie uitgeven.

Voor een eenvoudige demonstratie, een visuele functie, wordt de avatar verwijderd die wordt getoond van de aangemelde gebruiker die een opmerking plaatst.

>[!NOTE]
>
>Als u de extensie wilt gebruiken, moet de instantie van het opmerkingensysteem in een website die wordt beïnvloed (content), het resourceType instellen op het aangepaste opmerkingssysteem.

## De HBS-scripts wijzigen {#modify-the-hbs-scripts}

Gebruikend [&#x200B; CRXDE Lite &#x200B;](/help/sites-developing/developing-with-crxde-lite.md):

* Open [/apps/custom/components/comments/comment/**comment.hbs** &#x200B;](https://localhost:4502/crx/de/index.jsp#/apps/custom/components/comments/comment/comment.hbs)

   * Plaats een opmerking bij de tag die de avatar bevat voor een commentaarbericht (~ regel 21):

     ```
       <!--
        <<img class="scf-comment-avatar {{#if topLevel}}withTopLevel{{/if}}" src="{{author.avatarUrl}}"></img>
        -->
     ```

* Open [/apps/custom/components/comments/**comments.hbs** &#x200B;](https://localhost:4502/crx/de/index.jsp#/apps/custom/components/comments/comments.hbs)

   * Verwijder de commentaarmarkering die de avatar voor de volgende commentaaringang (~ lijn 44) omvat:

     ```
       <!--
        <img class="scf-composer-avatar" src="{{loggedInUser.avatarUrl}}"></img>
        -->
     ```

* Selecteer **sparen allen**

### Aangepaste app repliceren {#replicate-custom-app}

Nadat de toepassing is gewijzigd, moet de aangepaste component opnieuw worden gerepliceerd.

Een manier om dit te doen is:

* Vanuit het hoofdmenu

   * Selecteer **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Replication]** .
   * Selecteer **[!UICONTROL Activate Tree]** .
   * Stel `Start Path` in op `/apps/custom` .
   * Deselecteer **[!UICONTROL Only Modified]** .
   * Selecteer **[!UICONTROL Activate]** .

### Gewijzigde opmerking weergeven op gepubliceerde voorbeeldpagina {#view-modified-comment-on-published-sample-page}

[&#x200B; Verblijvend de ervaring &#x200B;](/help/communities/extend-sample-page.md#publish-sample-page) op publiceer instantie, nog binnen ondertekend als de zelfde gebruiker, is het nu mogelijk om de pagina in het publicatiemilieu te verfrissen om de wijziging te bekijken om avatar te verwijderen:

![&#x200B; mening-gewijzigd-inhoud &#x200B;](assets/view-modified-content.png)

### Voorbeeld van extensiepakket voor opmerkingen {#sample-comment-extension-package}

Bijgevoegd is een pakket van de toepassing van douanecommentaren die in dit leerprogramma wordt gecreeerd.

[Bestand ophalen](assets/sample-comment-extension-6-1-fp3.zip)
