---
title: Koppeling gebruiken
seo-title: Using Liking
description: De Liking-component toevoegen en configureren
seo-description: Adding and configuring the Liking component
uuid: 12103ab7-1a1c-49cd-8dad-6c7508b4550e
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: dcde4e03-78ab-4779-96a1-05ac41f14701
exl-id: 226fa91c-4a12-4586-b694-1a52fa2ba358
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 0%

---

# Koppeling gebruiken {#using-liking}

De `Liking` is een nuttig hulpmiddel dat gebruikers toestaat om een mening over een bepaald stuk van inhoud, zoals een commentaar binnen een forum te uiten. Met de `Liking` leden selecteren het hartpictogram om een positieve mening aan te geven.

## Koppeling toevoegen aan een pagina {#adding-liking-to-a-page}

Als u een `Liking` van een component aan een pagina op auteurswijze, gebruik componentenbrowser om van

* `Communities / Liking`

en sleep het naar de juiste positie op een pagina, zoals een positie ten opzichte van de functie die gebruikers leuk kunnen vinden.

Voor de nodige informatie gaat u naar [Grondbeginselen van Community-componenten](basics.md).

Wanneer de [vereiste clientbibliotheken](essentials-liking.md#essentials-for-client-side) worden opgenomen, is dit hoe `Liking` wordt weergegeven.

![koppelingscomponent](assets/liking-component.png)

## Liking configureren {#configuring-liking}

Selecteer de geplaatste `Liking` te openen en de component te selecteren `Configure` wordt het dialoogvenster Bewerken geopend.

![configure-new](assets/configure-new.png)

Onder de **[!UICONTROL Texts & Labels]** , geeft u de eigenschappen op die worden gebruikt voor het opnemen van &#39;like&#39;.

![configureren-koppelen](assets/configure-liking.png)

* **[!UICONTROL Positive Response Label]**

   (*Vereist*) De eigenschapsnaam voor een positieve reactie.

* **[!UICONTROL Negative Response Label]**

   (*Vereist*) De eigenschapsnaam voor een negatieve reactie.

* **[!UICONTROL Tally Name]**

   (*Vereist*) De interne, identificeerbare eigenschapsnaam voor dit geval van een stemcomponent.

## Ervaring met sitebezoekers {#site-visitor-experience}

### Leden {#members}

De leden kunnen te allen tijde van mening veranderen.

### Anoniem {#anonymous}

Anonieme koppelingen worden niet ondersteund. Site-bezoekers moeten zich registreren (lid worden) en zich aanmelden om deel te nemen aan een abonnement.

## Aanvullende informatie {#additional-information}

Meer informatie is te vinden op de [Belangrijkste elementen](essentials-liking.md) pagina voor ontwikkelaars.
