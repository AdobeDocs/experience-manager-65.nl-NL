---
title: De vormgeving wijzigen
seo-title: Alter the Appearance
description: Het script wijzigen
seo-description: Modify the script
uuid: 30555b9f-da29-4115-9ed5-25f80a247bd6
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: c9d31ed8-c105-453b-bd3c-4660dfd81272
docset: aem65
exl-id: cb8f6967-216c-46d3-a7ba-068b0f5e3b94
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 1%

---

# De vormgeving wijzigen {#alter-the-appearance}

## Het script wijzigen {#modify-the-script}

Het script comment.hbs is verantwoordelijk voor het maken van de algemene HTML voor elke opmerking.

Als u de avatar niet naast elke geposte opmerking wilt weergeven:

1. Kopiëren `comment.hbs`van `libs`tot `apps`

   1. Selecteer `/libs/social/commons/components/hbs/comments/comment/comment.hbs`
   1. Selecteer **[!UICONTROL Copy]**
   1. Selecteer `/apps/social/commons/components/hbs/comments/comment`
   1. Selecteer **[!UICONTROL Paste]**

1. De bedekking openen `comment.hbs`

   * Dubbelklikken op knooppunt `comment.hbs` in `/apps/social/commons/components/hbs/comments/comment folder`

1. Zoek de volgende regels en verwijder of verwijder deze of verwijder ze:

```xml
  <aside class="scf-comment-author">
        <img class="scf-comment-avatar {{#if topLevel}}withTopLevel{{/if}}" src="{{author.avatarUrl}}"></img>
```

Verwijder de lijnen of omring deze met `<!--` en `-->` om opmerkingen te maken. Bovendien worden de tekens &#39;xxx&#39; toegevoegd als visuele indicator van waar de avatar zou zijn geweest.

```xml
   xxx
   <!-- do not display avatar with comment
    <aside class="scf-comment-author">
        <img class="scf-comment-avatar {{#if topLevel}}withTopLevel{{/if}}" src="{{author.avatarUrl}}"></img>
```

### De bedekking dupliceren {#replicate-the-overlay}

Duw de bedekte commentaarcomponent aan de publicatieinstantie gebruikend het Hulpmiddel van de Replicatie.

>[!NOTE]
>
>Een robuustere vorm van replicatie zou zijn om een pakket in de Manager van het Pakket te creëren en [activate](/help/sites-administering/package-manager.md#replicating-packages) het. Een pakket kan worden geëxporteerd en gearchiveerd.

Selecteer in de globale navigatie de optie **[!UICONTROL Tools]** > **[!UICONTROL Deployment]** > **[!UICONTROL Replication]** en klik op **[!UICONTROL Activate Tree]**.

Voor het Startpad voert u in `/apps/social/commons` en selecteert u **[!UICONTROL Activate]**.

![verify-content-template](assets/verify-content-template.png)

### Resultaten weergeven {#view-results}

Als u zich als beheerder aanmeldt bij de publicatie-instantie, bijvoorbeeld https://localhost:4503/crx/de als beheerder/beheerder, kunt u controleren of de bovenliggende componenten aanwezig zijn.

Als u zich afmeldt en opnieuw inlogt als `aaron.mcdonald@mailinator.com/password` en vernieuwt u de pagina. U zult zien dat de geposte opmerking niet meer wordt weergegeven met een avatar, maar met een eenvoudige &#39;xxx&#39;.

![create-template-component](assets/create-template-component.png)
