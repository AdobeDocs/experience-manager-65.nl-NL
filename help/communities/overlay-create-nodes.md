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

Bedek het opmerkingensysteem met een aangepaste versie door het minimale aantal bestanden dat nodig is van `/libs` naar `/apps` te kopiëren en deze te wijzigen in `/apps` .

>[!CAUTION]
>
>De inhoud van de map /libs wordt nooit bewerkt, omdat bij een nieuwe installatie of upgrade de map /libs kan worden verwijderd of vervangen terwijl de inhoud van de map /apps ongewijzigd blijft.

Gebruikend [ CRXDE Lite ](../../help/sites-developing/developing-with-crxde-lite.md) op een auteursinstantie, begin door een weg in de /apps omslag te creëren die aan de weg aan de beklede componenten in de /libs omslag identiek is.

Het pad dat wordt gedupliceerd is:

* `/libs/social/commons/components/hbs/comments/comment`

Sommige knooppunten in het pad zijn mappen en andere componenten.

1. Blader naar [ http://localhost:4502/crx/de/index.jsp](http://localhost:4502/crx/de/index.jsp)
1. Maken `/apps/social` (als deze nog niet bestaat)
   * Knooppunt `/apps` selecteren
   * **[!UICONTROL Create > Folder]**
      * Voer naam in: `social`
1. Knooppunt `social` selecteren
   * **[!UICONTROL Create]** > **[!UICONTROL Folder]**
      * Voer naam in: `commons`
1. Knooppunt `commons` selecteren
   * **[!UICONTROL Create > Folder]**
      * Voer naam in: `components`
1. Knooppunt `components` selecteren
   * **[!UICONTROL Create > Folder]**.
      * Voer naam in: `hbs`
1. Knooppunt `hbs` selecteren
   * **[!UICONTROL Create]** > **[!UICONTROL Create Component]**
      * Voer label in: `comments`
      * Voer titel in: `Comments`
      * Voer beschrijving in: `List of comments without showing avatars`
      * Supertype: `social/commons/components/comments`
      * Enter Group: `Communities`
      * Klik op **[!UICONTROL Next]** tot **[!UICONTROL OK]**
1. Knooppunt `comments` selecteren

   * **[!UICONTROL Create]** > **[!UICONTROL Create Component]**

      * Voer label in: `comment`
      * Voer titel in: `Comment`
      * Voer beschrijving in: `A comment instance without avatars`
      * Supertype: `social/commons/components/comments/comment`
      * Enter Group: `.hidden`
      * Klik op **[!UICONTROL Next]** tot **[!UICONTROL OK]**
   * Selecteren **[!UICONTROL Save All]**
1. De standaardinstelling verwijderen `comments.jsp`
   * Knooppunt selecteren `/apps/social/commons/components/hbs/comments/comments.jsp`
   * Selecteren **[!UICONTROL Delete]**
1. De standaardcomment.jsp verwijderen
   * select node `/apps/social/commons/components/hbs/comments/comment/comment.jsp`
   * Selecteren **[!UICONTROL Delete]**
   * Selecteren **[!UICONTROL Save All]**

>[!NOTE]
>
>Om de overervingsketen te behouden, worden de `Super Type` (eigenschap `sling:resourceSuperType` ) van de overlaycomponenten op dezelfde waarde ingesteld als de `Super Type` van de componenten die worden bedekt, in dit geval:
>
>* `social/commons/components/comments`
>* `social/commons/components/comments/comment`

De eigen `Type` eigenschap `sling:resourceType` (eigenschap) van de overlay moet een relatieve zelfverwijzing zijn, zodat de inhoud die niet wordt gevonden in /apps, vervolgens wordt gezocht in /libs.
* Naam: `sling:resourceType`
* Type: `String`
* Waarde: `social/commons/components/hbs/comments`

1. Groen selecteren `[+] Add`
   * Naam: `sling:resourceType`
   * Type: `String`
   * Waarde: `social/commons/components/hbs/comments/comment`
1. Groen selecteren `[+] Add`
   * Selecteren **[!UICONTROL Save All]**

![ creeer-knopen ](assets/create-nodes.png)
