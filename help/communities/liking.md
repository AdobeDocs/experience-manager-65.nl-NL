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
source-wordcount: '224'
ht-degree: 0%

---


# Koppeling gebruiken {#using-liking}

De component `Liking` is een nuttig hulpmiddel dat gebruikers toestaat om een mening over een bepaald stuk van inhoud, zoals een commentaar binnen een forum te uiten. Met de component `Liking` selecteren de leden het hartpictogram om een positieve mening aan te geven.

## Koppeling toevoegen aan een pagina {#adding-liking-to-a-page}

Als u een `Liking`-component in de ontwerpmodus aan een pagina wilt toevoegen, gebruikt u de componentbrowser om te zoeken naar

* `Communities / Liking`

en sleep het naar de juiste positie op een pagina, zoals een positie ten opzichte van de functie die gebruikers leuk kunnen vinden.

Voor noodzakelijke informatie, bezoek [de Grondbeginselen van Componenten van Gemeenschappen](basics.md).

Als de [vereiste client-side bibliotheken](essentials-liking.md#essentials-for-client-side) worden opgenomen, wordt de `Liking`-component op deze manier weergegeven.

![koppelingscomponent](assets/liking-component.png)

## Koppeling configureren {#configuring-liking}

Selecteer de geplaatste `Liking` component en selecteer `Configure` pictogram dat het Edit dialoog opent.

![configure-new](assets/configure-new.png)

Geef onder het tabblad **[!UICONTROL Texts & Labels]** de eigenschappen op die worden gebruikt voor het opnemen van &#39;like&#39;.

![configureren-koppelen](assets/configure-liking.png)

* **[!UICONTROL Positive Response Label]**

   (*Required*) De bezitsnaam voor een positieve reactie.

* **[!UICONTROL Negative Response Label]**

   (*Required*) de bezitsnaam voor een negatieve reactie.

* **[!UICONTROL Tally Name]**

   (*Required*) De interne, identificeerbare bezitsnaam voor deze instantie van een stemcomponent.

## Ervaring {#site-visitor-experience} voor bezoekers van site

### Leden {#members}

De leden kunnen te allen tijde van mening veranderen.

### Anonieme {#anonymous}

Anonieme koppelingen worden niet ondersteund. Site-bezoekers moeten zich registreren (lid worden) en zich aanmelden om deel te nemen aan een abonnement.

## Aanvullende informatie {#additional-information}

Meer informatie vindt u op de pagina [Liking Essentials](essentials-liking.md) voor ontwikkelaars.
