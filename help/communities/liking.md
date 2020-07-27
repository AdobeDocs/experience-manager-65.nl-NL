---
title: Koppeling gebruiken
seo-title: Koppeling gebruiken
description: De Liking-component toevoegen en configureren
seo-description: De Liking-component toevoegen en configureren
uuid: 12103ab7-1a1c-49cd-8dad-6c7508b4550e
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: dcde4e03-78ab-4779-96a1-05ac41f14701
translation-type: tm+mt
source-git-commit: c9fa5624a59f4b9a6f970628b03bbd8b7a277a73
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Koppeling gebruiken {#using-liking}

De `Liking` component is een nuttig hulpmiddel dat gebruikers toestaat om een mening over een bepaald stuk van inhoud, zoals een commentaar binnen een forum te uiten. Met de `Liking` component selecteren de leden het hartpictogram om een positief advies aan te geven.

## Koppeling toevoegen aan een pagina {#adding-liking-to-a-page}

Als u een `Liking` component aan een pagina wilt toevoegen in de ontwerpmodus, gebruikt u de componentbrowser om te zoeken naar

* `Communities / Liking`

en sleep het naar de juiste positie op een pagina, zoals een positie ten opzichte van de functie die gebruikers leuk kunnen vinden.

Ga voor de benodigde informatie naar [Community Components Basics](basics.md).

Wanneer de [vereiste client-side bibliotheken](essentials-liking.md#essentials-for-client-side) worden opgenomen, wordt de `Liking` component op deze manier weergegeven.

![koppelingscomponent](assets/liking-component.png)

## Liking configureren {#configuring-liking}

Selecteer de geplaatste `Liking` component die u wilt openen en selecteer het `Configure` pictogram waarmee het dialoogvenster Bewerken wordt geopend.

![configure-new](assets/configure-new.png)

Geef onder het **[!UICONTROL Texts & Labels]** tabblad de eigenschappen op die worden gebruikt voor het opnemen van &#39;like&#39;.

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

## Additional Information {#additional-information}

Meer informatie vindt u op de pagina [Liking Essentials](essentials-liking.md) voor ontwikkelaars.
