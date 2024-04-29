---
title: Stemmen gebruiken
description: Leer hoe u de component Stemmen toevoegt aan een pagina waarop ingetekende communityleden een bepaalde inhoud kunnen beoordelen, zoals een antwoord.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
exl-id: aa90bf1b-6053-4949-b061-232d72b80682
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 0%

---

# Stemmen gebruiken {#using-voting}

De `Voting` is een nuttig hulpmiddel dat communautaire leden toestaat om een bepaald stuk van inhoud, zoals een antwoord binnen een component te schatten QnA. Met de `Voting` leden selecteren pijlen omhoog of omlaag om hun mening aan te geven.

## Stemmen toevoegen aan een pagina {#adding-voting-to-a-page}

Als u een `Voting` in de modus Auteur naar een pagina, gebruikt u de deelbrowser. Zoeken `Communities / Voting` en sleep het naar de juiste positie op een pagina, zoals een positie ten opzichte van de functie waar gebruikers op kunnen stemmen.

Voor de nodige informatie gaat u naar [Grondbeginselen van Community-componenten](basics.md).

Wanneer de [vereiste clientbibliotheken](essentials-voting.md#essentials-for-client-side) worden opgenomen, is dit hoe `Voting` wordt weergegeven.

![stemcomponent](assets/voting-component.png)

## Stemmen configureren {#configuring-voting}

Selecteer de geplaatste `Voting` zodat u toegang hebt tot `Configure` wordt het dialoogvenster Bewerken geopend.

![vormen](assets/configure-new.png)

Onder de **[!UICONTROL Texts & Labels]** , geeft u de eigenschappen op die worden gebruikt voor het opnemen van stemmen.

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

## Aanvullende informatie {#additional-information}

Meer informatie is te vinden op de [Grondbeginselen van de stemming](essentials-voting.md) pagina voor ontwikkelaars.
