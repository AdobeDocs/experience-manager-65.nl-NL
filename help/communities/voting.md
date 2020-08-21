---
title: Stemmen gebruiken
seo-title: Stemmen gebruiken
description: De component Stemmen toevoegen aan een pagina
seo-description: De component Stemmen toevoegen aan een pagina
uuid: 56e6cced-2f2d-434a-8fde-92a6c2478a04
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 071cac6d-05c5-47ab-85bc-ead6693ca1f4
translation-type: tm+mt
source-git-commit: c190d5f223c85f6c49fea1391d8a3d2baff20192
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 0%

---


# Stemmen gebruiken {#using-voting}

De `Voting` component is een nuttig hulpmiddel dat communautaire leden toestaat om een bepaald stuk van inhoud, zoals een antwoord binnen een component te schatten QnA. Met de `Voting` component selecteren de leden pijlen omhoog of omlaag om hun mening aan te geven.

## Stemmen toevoegen aan een pagina {#adding-voting-to-a-page}

Als u een `Voting` component in de modus Schrijven aan een pagina wilt toevoegen, gebruikt u de componentbrowser om de component te zoeken `Communities / Voting` en naar de juiste positie op een pagina te slepen, zoals een positie ten opzichte van de functie waarop gebruikers kunnen stemmen.

Ga voor de benodigde informatie naar [Community Components Basics](basics.md).

Wanneer de [vereiste client-side bibliotheken](essentials-voting.md#essentials-for-client-side) worden opgenomen, wordt de `Voting` component op deze manier weergegeven.

![stemcomponent](assets/voting-component.png)

## Stemmen configureren {#configuring-voting}

Selecteer de geplaatste `Voting` component die u wilt openen en selecteer het `Configure` pictogram waarmee het dialoogvenster Bewerken wordt geopend.

![vormen](assets/configure-new.png)

Geef onder het **[!UICONTROL Texts & Labels]** tabblad de eigenschappen op die worden gebruikt voor het opnemen van stemmen.

![stemlabel](assets/voting-label.png)

* **[!UICONTROL Positive Response Label]**

   (*Vereist*) De interne eigenschapnaam voor een positieve reactie.

* **[!UICONTROL Negative Response Label]**

   (*Vereist*) De interne eigenschapnaam voor een negatieve reactie.

* **[!UICONTROL Tally Name]**

   (*Vereist*) De interne, identificeerbare eigenschapsnaam voor dit geval van een stemcomponent.

## Ervaring met sitebezoekers {#site-visitor-experience}

### Leden {#members}

De leden kunnen slechts eenmaal stemmen, maar kunnen te allen tijde van stemming veranderen.

### Anoniem {#anonymous}

Anonieme stemming wordt niet ondersteund. Sitebezoekers moeten zich registreren (lid worden) en zich aanmelden om eenmaal aan de stemming deel te nemen.

## Additional Information {#additional-information}

Meer informatie vindt u op de pagina [Stemmateriaal](essentials-voting.md) voor ontwikkelaars.
