---
title: Koppeling gebruiken
description: Leer hoe u de component Liking toevoegt en configureert, zodat gebruikers een mening over een bepaald stuk inhoud, zoals een commentaar, kunnen uiten.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
exl-id: 226fa91c-4a12-4586-b694-1a52fa2ba358
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 0%

---

# Koppeling gebruiken {#using-liking}

De component `Liking` is een handig hulpmiddel waarmee gebruikers een mening over bepaalde inhoud kunnen uiten, zoals een opmerking in een forum. Met de component `Liking` selecteren de leden het hartpictogram om een positieve mening aan te geven.

## Koppeling toevoegen aan een pagina {#adding-liking-to-a-page}

Als u een component `Liking` in de ontwerpmodus aan een pagina wilt toevoegen, gebruikt u de componentbrowser om te zoeken naar

* `Communities / Liking`

En sleep het naar de juiste positie op een pagina, zoals een positie ten opzichte van de functie die gebruikers leuk kunnen vinden.

Voor noodzakelijke informatie, bezoek {de Grondbeginselen van de Componenten van 0} Gemeenschappen [&#128279;](basics.md).

Wanneer de [ vereiste cliënt-zijbibliotheken ](essentials-liking.md#essentials-for-client-side) inbegrepen zijn, is dit hoe de `Liking` component verschijnt.

![ houden-component ](assets/liking-component.png)

## Liking configureren {#configuring-liking}

Selecteer de geplaatste component `Liking` , zodat u het pictogram `Configure` kunt openen en selecteren waarmee het dialoogvenster Bewerken wordt geopend.

![ vorm-nieuw ](assets/configure-new.png)

Geef onder het tabblad **[!UICONTROL Texts & Labels]** de eigenschappen op die worden gebruikt voor het opnemen van &#39;like&#39;.

![ vormen-houden ](assets/configure-liking.png)

* **[!UICONTROL Positive Response Label]**

  (*Vereist*) de bezitsnaam voor een positieve reactie.

* **[!UICONTROL Negative Response Label]**

  (*Vereist*) de bezitsnaam voor een negatieve reactie.

* **[!UICONTROL Tally Name]**

  (*Vereist*) de interne, identificeerbare bezitsnaam voor dit geval van een stemcomponent.

## Ervaring met sitebezoekers {#site-visitor-experience}

### Leden {#members}

Leden kunnen te allen tijde van mening veranderen.

### Anoniem {#anonymous}

Anonieme koppelingen worden niet ondersteund. Site-bezoekers moeten zich registreren (lid worden) en zich aanmelden om deel te nemen aan een abonnement.

## Aanvullende informatie {#additional-information}

Meer informatie kan op de [ Vergelijkende Hoofdzaak ](essentials-liking.md) pagina voor ontwikkelaars worden gevonden.
