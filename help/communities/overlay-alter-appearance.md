---
title: De vormgeving wijzigen
description: Het script wijzigen
uuid: 30555b9f-da29-4115-9ed5-25f80a247bd6
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: c9d31ed8-c105-453b-bd3c-4660dfd81272
docset: aem65
exl-id: cb8f6967-216c-46d3-a7ba-068b0f5e3b94
source-git-commit: 78c584db8c35ea809048580fe5b440a0b73c8eea
workflow-type: tm+mt
source-wordcount: '210'
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

Verwijder de lijnen of omring deze met `<!--` en `-->` dus je geeft commentaar. Bovendien worden de tekens &#39;xxx&#39; toegevoegd als visuele indicator van waar de avatar zou zijn geweest.

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

Voer bij Beginpad het volgende in `/apps/social/commons` en selecteert u **[!UICONTROL Activate]**.

![verify-content-template](assets/verify-content-template.png)

### Resultaten weergeven {#view-results}

Als u zich als beheerder, bijvoorbeeld, https://localhost:4503/crx/de als admin/admin bij de publicatie-instantie aanmeldt, kunt u controleren of de bovenliggende componenten aanwezig zijn.

Als u zich afmeldt en dan login als `aaron.mcdonald@mailinator.com/password` en vernieuwt u de pagina. U ziet dat een avatar niet wordt weergegeven met de geposte opmerking. In plaats daarvan wordt een eenvoudige &#39;xxx&#39; weergegeven.

![create-template-component](assets/create-template-component.png)
