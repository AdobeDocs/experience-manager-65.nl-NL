---
title: De vormgeving wijzigen
description: Leer hoe u het script comment.hbs bewerkt dat verantwoordelijk is voor het maken van de algemene HTML voor elke opmerking in Adobe Experience Manager Communities.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
docset: aem65
exl-id: cb8f6967-216c-46d3-a7ba-068b0f5e3b94
solution: Experience Manager
feature: Communities
role: Developer
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---

# De vormgeving wijzigen {#alter-the-appearance}

## Het script wijzigen {#modify-the-script}

Het script van `comment.hbs` is verantwoordelijk voor het maken van de algemene HTML voor elke opmerking.

Als u de avatar niet naast elke geposte opmerking wilt weergeven:

1. `comment.hbs` kopiëren van `libs` naar `apps`

   1. Selecteren `/libs/social/commons/components/hbs/comments/comment/comment.hbs`
   1. Selecteren **[!UICONTROL Copy]**
   1. Selecteren `/apps/social/commons/components/hbs/comments/comment`
   1. Selecteren **[!UICONTROL Paste]**

1. De bedekking openen `comment.hbs`

   * Dubbelklikken op knooppunt `comment.hbs` in `/apps/social/commons/components/hbs/comments/comment folder`

1. Zoek de volgende regels en verwijder of verwijder deze of verwijder ze:

```xml
  <aside class="scf-comment-author">
        <img class="scf-comment-avatar {{#if topLevel}}withTopLevel{{/if}}" src="{{author.avatarUrl}}"></img>
```

Verwijder de lijnen of omring deze met `<!--` en `-->` , zodat u ze weglaat. Bovendien worden de tekens &#39;xxx&#39; toegevoegd als visuele indicator van waar de avatar zou zijn geweest.

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
>Een robuustere vorm van replicatie zou een pakket in de Manager van het Pakket moeten tot stand brengen en [&#128279;](/help/sites-administering/package-manager.md#replicating-packages) het activeren. Een pakket kan worden geëxporteerd en gearchiveerd.

Selecteer in de globale navigatie **[!UICONTROL Tools]** > **[!UICONTROL Deployment]** > **[!UICONTROL Replication]** en klik op **[!UICONTROL Activate Tree]** .

Voer bij Beginpad `/apps/social/commons` in en selecteer **[!UICONTROL Activate]** .

![ verifieer-inhoud-malplaatje ](assets/verify-content-template.png)

### Resultaten weergeven {#view-results}

Als u zich als beheerder, bijvoorbeeld, https://localhost:4503/crx/de als admin/admin bij de publicatie-instantie aanmeldt, kunt u controleren of de bovenliggende componenten aanwezig zijn.

Als u zich afmeldt en zich vervolgens aanmeldt als `aaron.mcdonald@mailinator.com/password` en de pagina vernieuwt, ziet u dat een avatar niet wordt weergegeven met de geposte opmerking. In plaats daarvan wordt een eenvoudige &#39;xxx&#39; weergegeven.

![ creeer-malplaatje-component ](assets/create-template-component.png)
