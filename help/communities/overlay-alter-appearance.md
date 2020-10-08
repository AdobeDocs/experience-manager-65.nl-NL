---
title: De vormgeving wijzigen
seo-title: De vormgeving wijzigen
description: Het script wijzigen
seo-description: Het script wijzigen
uuid: 30555b9f-da29-4115-9ed5-25f80a247bd6
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: c9d31ed8-c105-453b-bd3c-4660dfd81272
docset: aem65
translation-type: tm+mt
source-git-commit: f375b40c084ee363757b78c602091f38524b8b03
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 1%

---


# De vormgeving wijzigen {#alter-the-appearance}

## Het script wijzigen {#modify-the-script}

Het script comment.hbs is verantwoordelijk voor het maken van de algemene HTML voor elke opmerking.

Als u de avatar niet naast elke geposte opmerking wilt weergeven:

1. Kopiëren `comment.hbs`van `libs`naar `apps`

   1. Selecteer `/libs/social/commons/components/hbs/comments/comment/comment.hbs`
   1. Selecteer **[!UICONTROL Copy]**
   1. Selecteer `/apps/social/commons/components/hbs/comments/comment`
   1. Selecteer **[!UICONTROL Paste]**

1. De bedekking openen `comment.hbs`

   * Dubbelklik op knooppunt `comment.hbs` in `/apps/social/commons/components/hbs/comments/comment folder`

1. Zoek de volgende regels en verwijder of verwijder deze of verwijder ze:

```xml
  <aside class="scf-comment-author">
        <img class="scf-comment-avatar {{#if topLevel}}withTopLevel{{/if}}" src="{{author.avatarUrl}}"></img>
```

Verwijder de lijnen of omring deze met `<!--` en verwijder `-->` de lijnen. Bovendien worden de tekens &#39;xxx&#39; toegevoegd als visuele indicator van waar de avatar zou zijn geweest.

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
>Een robuustere vorm van replicatie zou zijn om een pakket in de Manager van het Pakket te creëren en het te [activeren](/help/sites-administering/package-manager.md#replicating-packages) . Een pakket kan worden geëxporteerd en gearchiveerd.

Selecteer in de globale navigatie **[!UICONTROL Tools]** > **[!UICONTROL Deployment]** > **[!UICONTROL Replication]** en klik **[!UICONTROL Activate Tree]**.

Voer voor het beginpad in `/apps/social/commons` en selecteer **[!UICONTROL Activate]**.

![verify-content-template](assets/verify-content-template.png)

### Resultaten weergeven {#view-results}

Als u zich als beheerder aanmeldt bij de publicatie-instantie, bijvoorbeeld https://localhost:4503/crx/de als beheerder/beheerder, kunt u controleren of de bovenliggende componenten aanwezig zijn.

Als u zich afmeldt en opnieuw aanmeldt als `aaron.mcdonald@mailinator.com/password` en de pagina vernieuwt, ziet u dat de geposte opmerking niet meer wordt weergegeven bij een avatar, maar een eenvoudige &#39;xxx&#39; wordt weergegeven.

![create-template-component](assets/create-template-component.png)

