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
source-git-commit: 48afa2146d0dcbab4beaa1044645c269b49fd7ff

---


# Notities maken {#create-nodes}

Bedek het opmerkingensysteem met een aangepaste versie door het minimale aantal bestanden dat nodig is van `/libs` naar te kopiëren `/apps` en te wijzigen in `/apps`.

>[!CAUTION]
>
>De inhoud van de map /libs wordt nooit bewerkt, omdat een nieuwe installatie of upgrade de map /libs kan verwijderen of vervangen, terwijl de inhoud van de map /apps ongewijzigd blijft.


Gebruikend [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md) op een auteursinstantie, begin door een weg in de /apps omslag te creëren die aan de weg aan de overlappende componenten in de /libs omslag identiek is.

Het pad dat wordt gedupliceerd is:

* `/libs/social/commons/components/hbs/comments/comment`

Sommige knooppunten in het pad zijn mappen en andere componenten.

1. Bladeren naar [http://localhost:4502/crx/de/index.jsp](http://localhost:4502/crx/de/index.jsp)
1. Maken `/apps/social` (als deze nog niet bestaat)
   * Knooppunt `/apps` selecteren
   * **[!UICONTROL Maken > Map...]**
      * Naam invoeren: `social`
1. Knooppunt `social` selecteren
   * **[!UICONTROL Maken]** > **[!UICONTROL Map...]**
      * Naam invoeren: `commons`
1. Knooppunt `commons` selecteren
   * **[!UICONTROL Maken > Map...]**
      * Naam invoeren: `components`
1. Knooppunt `components` selecteren
   * **[!UICONTROL Maken > Map..]**.
      * Naam invoeren: `hbs`
1. Knooppunt `hbs` selecteren
   * **[!UICONTROL Maken]** > Component **[!UICONTROL maken...]**
      * Label invoeren: `comments`
      * Titel invoeren: `Comments`
      * Beschrijving invoeren: `List of comments without showing avatars`
      * Supertype: `social/commons/components/comments`
      * Groep invoeren: `Communities`
      * Klik op **[!UICONTROL Volgende]** totdat **[!UICONTROL OK]**
1. Knooppunt `comments` selecteren

   * **[!UICONTROL Maken > Component maken...]**

      * Label invoeren: `comment`
      * Titel invoeren: `Comment`
      * Beschrijving invoeren: `A comment instance without avatars`
      * Supertype: `social/commons/components/comments/comment`
      * Groep invoeren: `.hidden`
      * Klik op **[!UICONTROL Volgende]** totdat **[!UICONTROL OK]**
   * Alles **[!UICONTROL opslaan selecteren]**
1. De standaardinstelling verwijderen `comments.jsp`
   * Knooppunt selecteren `/apps/social/commons/components/hbs/comments/comments.jsp`
   * Selecteren **[!UICONTROL Verwijderen]**
1. De standaardcomment.jsp verwijderen
   * Selecteer knooppunt `/apps/social/commons/components/hbs/comments/comment/comment.jsp`
   * Selecteren **[!UICONTROL Verwijderen]**
   * Alles **[!UICONTROL opslaan selecteren]**

>[!NOTE]
>
>Om de overervingsketen te behouden, wordt de `Super Type` (eigenschap `sling:resourceSuperType`) van de overlaycomponenten op dezelfde waarde ingesteld als de waarde `Super Type` van de componenten die worden bedekt, in dit geval:
>
>* `social/commons/components/comments`
>* `social/commons/components/comments/comment`
>



De eigen eigenschap `Type`(property `sling:resourceType`) van de overlay moet een relatieve zelfverwijzing zijn, zodat de inhoud die niet wordt gevonden in /apps, vervolgens wordt gezocht in /libs.
* Naam: `sling:resourceType`
* Type: `String`
* Waarde: `social/commons/components/hbs/comments`

1. Groen selecteren `[+] Add`
   * Naam: `sling:resourceType`
   * Type: `String`
   * Waarde: `social/commons/components/hbs/comments/comment`
1. Groen selecteren `[+] Add`
   * Alles **[!UICONTROL opslaan selecteren]**

![chlimage_1-4](assets/chlimage_1-4.png)

