---
title: Notities maken
seo-title: Notities maken
description: Het opmerkingensysteem bedekken
seo-description: Het opmerkingensysteem bedekken
uuid: 802ae28b-9989-4c2c-b466-ab76a724efd3
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: cd4f53ee-537b-4f10-a64f-474ba2c44576
translation-type: tm+mt
source-git-commit: f375b40c084ee363757b78c602091f38524b8b03
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 4%

---


# Notities maken {#create-nodes}

Bedek het opmerkingensysteem met een aangepaste versie door het minimale aantal bestanden dat nodig is van `/libs` naar te kopiëren `/apps` en te wijzigen in `/apps`.

>[!CAUTION]
>
>De inhoud van de map /libs wordt nooit bewerkt, omdat een nieuwe installatie of upgrade de map /libs kan verwijderen of vervangen, terwijl de inhoud van de map /apps ongewijzigd blijft.

Wanneer u [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md) op een auteurinstantie gebruikt, begint u met het maken van een pad in de map /apps dat identiek is aan het pad naar de bovenliggende componenten in de map /libs.

Het pad dat wordt gedupliceerd is:

* `/libs/social/commons/components/hbs/comments/comment`

Sommige knooppunten in het pad zijn mappen en andere componenten.

1. Bladeren naar [http://localhost:4502/crx/de/index.jsp](http://localhost:4502/crx/de/index.jsp)
1. Maken `/apps/social` (als deze nog niet bestaat)
   * Knooppunt `/apps` selecteren
   * **[!UICONTROL Create > Folder ...]**
      * Naam invoeren: `social`
1. Knooppunt `social` selecteren
   * **[!UICONTROL Create]** > **[!UICONTROL Folder...]**
      * Naam invoeren: `commons`
1. Knooppunt `commons` selecteren
   * **[!UICONTROL Create > Folder...]**
      * Naam invoeren: `components`
1. Knooppunt `components` selecteren
   * **[!UICONTROL Create > Folder..]**.
      * Naam invoeren: `hbs`
1. Knooppunt `hbs` selecteren
   * **[!UICONTROL Create]** > **[!UICONTROL Create Component...]**
      * Label invoeren: `comments`
      * Titel invoeren: `Comments`
      * Beschrijving invoeren: `List of comments without showing avatars`
      * Supertype: `social/commons/components/comments`
      * Groep invoeren: `Communities`
      * Klikken **[!UICONTROL Next]** tot **[!UICONTROL OK]**
1. Knooppunt `comments` selecteren

   * **[!UICONTROL Create]** > **[!UICONTROL Create Component...]**

      * Label invoeren: `comment`
      * Titel invoeren: `Comment`
      * Beschrijving invoeren: `A comment instance without avatars`
      * Supertype: `social/commons/components/comments/comment`
      * Groep invoeren: `.hidden`
      * Klikken **[!UICONTROL Next]** tot **[!UICONTROL OK]**
   * Selecteer **[!UICONTROL Save All]**
1. De standaardinstelling verwijderen `comments.jsp`
   * Knooppunt selecteren `/apps/social/commons/components/hbs/comments/comments.jsp`
   * Selecteer **[!UICONTROL Delete]**
1. De standaardcomment.jsp verwijderen
   * Selecteer knooppunt `/apps/social/commons/components/hbs/comments/comment/comment.jsp`
   * Selecteer **[!UICONTROL Delete]**
   * Selecteer **[!UICONTROL Save All]**

>[!NOTE]
>
>Om de overervingsketen te behouden, wordt de `Super Type` (eigenschap `sling:resourceSuperType`) van de overlaycomponenten op dezelfde waarde ingesteld als de waarde `Super Type` van de componenten die worden bedekt, in dit geval:
>
>* `social/commons/components/comments`
>* `social/commons/components/comments/comment`


De eigen eigenschap `Type`(property `sling:resourceType`) van de overlay moet een relatieve zelfverwijzing zijn, zodat de inhoud die niet wordt gevonden in /apps, vervolgens wordt gezocht in /libs.
* Naam: `sling:resourceType`
* Type: `String`
* Waarde: `social/commons/components/hbs/comments`

1. Groen selecteren `[+] Add`
   * Naam: `sling:resourceType`
   * Type: `String`
   * Waarde: `social/commons/components/hbs/comments/comment`
1. Groen selecteren `[+] Add`
   * Selecteer **[!UICONTROL Save All]**

![create-nodes](assets/create-nodes.png)

