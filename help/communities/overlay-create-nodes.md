---
title: Notities maken
description: Leer hoe te om het commentaarsysteem met een douaneversie te bedekken door het minimale aantal dossiers noodzakelijk van /libs te kopiëren en hen in /apps uit te geven.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: 3d72cbdf-5eb4-477d-aa61-035a846f7dcb
solution: Experience Manager
feature: Communities
role: Developer
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---

# Notities maken {#create-nodes}

Bedek het opmerkingensysteem met een aangepaste versie door het minimale aantal bestanden te kopiëren dat nodig is van `/libs` in `/apps` en deze aan te passen `/apps`.

>[!CAUTION]
>
>De inhoud van de map /libs wordt nooit bewerkt, omdat bij een nieuwe installatie of upgrade de map /libs kan worden verwijderd of vervangen terwijl de inhoud van de map /apps ongewijzigd blijft.

Gebruiken [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md) op een auteurinstantie, begin door een weg in de /apps omslag te creëren die aan de overlapte componenten in de /libs omslag identiek is.

Het pad dat wordt gedupliceerd is:

* `/libs/social/commons/components/hbs/comments/comment`

Sommige knooppunten in het pad zijn mappen en andere componenten.

1. Bladeren naar [http://localhost:4502/crx/de/index.jsp](http://localhost:4502/crx/de/index.jsp)
1. Maken `/apps/social` (als deze nog niet bestaat)
   * Selecteren `/apps` node
   * **[!UICONTROL Create > Folder]**
      * Naam invoeren: `social`
1. Selecteren `social` node
   * **[!UICONTROL Create]** > **[!UICONTROL Folder]**
      * Naam invoeren: `commons`
1. Selecteren `commons` node
   * **[!UICONTROL Create > Folder]**
      * Naam invoeren: `components`
1. Selecteren `components` node
   * **[!UICONTROL Create > Folder]**.
      * Naam invoeren: `hbs`
1. Selecteren `hbs` node
   * **[!UICONTROL Create]** > **[!UICONTROL Create Component]**
      * Label invoeren: `comments`
      * Titel invoeren: `Comments`
      * Beschrijving invoeren: `List of comments without showing avatars`
      * Supertype: `social/commons/components/comments`
      * Groep invoeren: `Communities`
      * Klikken **[!UICONTROL Next]** tot **[!UICONTROL OK]**
1. Selecteren `comments` node

   * **[!UICONTROL Create]** > **[!UICONTROL Create Component]**

      * Label invoeren: `comment`
      * Titel invoeren: `Comment`
      * Beschrijving invoeren: `A comment instance without avatars`
      * Supertype: `social/commons/components/comments/comment`
      * Groep invoeren: `.hidden`
      * Klikken **[!UICONTROL Next]** tot **[!UICONTROL OK]**
   * Selecteren **[!UICONTROL Save All]**
1. De standaardinstelling verwijderen `comments.jsp`
   * Knooppunt selecteren `/apps/social/commons/components/hbs/comments/comments.jsp`
   * Selecteren **[!UICONTROL Delete]**
1. De standaardcomment.jsp verwijderen
   * Selecteer knooppunt `/apps/social/commons/components/hbs/comments/comment/comment.jsp`
   * Selecteren **[!UICONTROL Delete]**
   * Selecteren **[!UICONTROL Save All]**

>[!NOTE]
>
>Als u de overervingsketen wilt behouden, `Super Type` (eigenschap `sling:resourceSuperType`) van de bedekkingscomponenten op dezelfde waarde worden ingesteld als de `Super Type` van de onderdelen waarop de toepassing betrekking heeft, in dit geval:
>
>* `social/commons/components/comments`
>* `social/commons/components/comments/comment`

De eigen overlay `Type`(eigenschap `sling:resourceType`) moet een relatieve zelfverwijzing zijn, zodat de inhoud die niet wordt gevonden in /apps, wordt gezocht in /libs.
* Naam: `sling:resourceType`
* Type: `String`
* Waarde: `social/commons/components/hbs/comments`

1. Groen selecteren `[+] Add`
   * Naam: `sling:resourceType`
   * Type: `String`
   * Waarde: `social/commons/components/hbs/comments/comment`
1. Groen selecteren `[+] Add`
   * Selecteren **[!UICONTROL Save All]**

![create-nodes](assets/create-nodes.png)
