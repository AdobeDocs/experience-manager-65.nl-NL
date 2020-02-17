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
source-git-commit: 27a054cc5d502d95c664c3b414d0066c6c120b65

---


# De vormgeving wijzigen {#alter-the-appearance}

## Het script wijzigen {#modify-the-script}

Het script comment.hbs is verantwoordelijk voor het maken van de algemene HTML voor elke opmerking.

Als u de avatar niet naast elke geposte opmerking wilt weergeven:

1. kopiëren `comment.hbs`van `libs`naar `apps`

   1. select `/libs/social/commons/components/hbs/comments/comment/comment.hbs`
   1. Selecteer **Kopiëren**
   1. select `/apps/social/commons/components/hbs/comments/comment`
   1. selecteren **Plakken**

1. openen `comment.hbs`

   * dubbelklikken op knooppunt `comment.hbs`in `/apps/social/commons/components/hbs/comments/comment folder`

1. de volgende regels zoeken en deze verwijderen of er opmerkingen over plaatsen:

```xml
  <aside class="scf-comment-author">
        <img class="scf-comment-avatar {{#if topLevel}}withTopLevel{{/if}}" src="{{author.avatarUrl}}"></img>
```

Verwijder de regels of omring ze met &#39;&lt;!—&#39; en &#39;—>&#39; om ze uit te lichten. Bovendien worden de tekens &#39;xxx&#39; toegevoegd als visuele indicator van waar de avatar zou zijn geweest.

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

Selecteer in de globale navigatie **Extra, Implementatie, Replicatie** en **activeer vervolgens de structuur**.

Voer voor het beginpad `/apps/social/commons`** **in en selecteer **Activeren**.

![chlimage_1-77](assets/chlimage_1-77.png)

### Resultaten weergeven {#view-results}

Als u zich als beheerder aanmeldt bij de publicatie-instantie, bijvoorbeeld https://localhost:4503/crx/de als beheerder/beheerder, kunt u controleren of de bovenliggende componenten aanwezig zijn.

Als u zich afmeldt en opnieuw aanmeldt als `aaron.mcdonald@mailinator.com/password` en de pagina vernieuwt, ziet u dat de geposte opmerking niet meer wordt weergegeven bij een avatar, maar een eenvoudige &#39;xxx&#39; wordt weergegeven.

![chlimage_1-78](assets/chlimage_1-78.png)

