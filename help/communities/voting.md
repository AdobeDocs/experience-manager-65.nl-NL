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

De component `Voting` is een handig hulpmiddel waarmee leden van de gemeenschap een bepaalde inhoud kunnen beoordelen, zoals een antwoord binnen een component QnA. Met de component `Voting` selecteren leden pijlen omhoog of omlaag om hun mening aan te geven.

## Stemmen toevoegen aan een pagina {#adding-voting-to-a-page}

Gebruik de componentbrowser om een component `Voting` in de modus Auteur aan een pagina toe te voegen. Zoek `Communities / Voting` en sleep het naar de juiste positie op een pagina, zoals een positie ten opzichte van de functie waar gebruikers op kunnen stemmen.

Voor noodzakelijke informatie, bezoek {de Grondbeginselen van de Componenten van 0} Gemeenschappen [&#128279;](basics.md).

Wanneer de [ vereiste cliënt-zijbibliotheken ](essentials-voting.md#essentials-for-client-side) inbegrepen zijn, is dit hoe de `Voting` component verschijnt.

![ stem-component ](assets/voting-component.png)

## Stemmen configureren {#configuring-voting}

Selecteer de geplaatste component `Voting` , zodat u het pictogram `Configure` kunt openen en selecteren waarmee het dialoogvenster Bewerken wordt geopend.

![ vormen ](assets/configure-new.png)

Geef onder het tabblad **[!UICONTROL Texts & Labels]** de eigenschappen op die worden gebruikt voor het opnemen van stemmen.

![ stem-etiket ](assets/voting-label.png)

* **[!UICONTROL Positive Response Label]**

  (*Vereist*) de interne bezitsnaam voor een positieve reactie.

* **[!UICONTROL Negative Response Label]**

  (*Vereist*) de interne bezitsnaam voor een negatieve reactie.

* **[!UICONTROL Tally Name]**

  (*Vereist*) de interne, identificeerbare bezitsnaam voor dit geval van een stemcomponent.

## Ervaring met sitebezoekers {#site-visitor-experience}

### Leden {#members}

De leden kunnen slechts eenmaal stemmen, maar kunnen te allen tijde van stemming veranderen.

### Anoniem {#anonymous}

Anonieme stemming wordt niet ondersteund. Sitebezoekers moeten zich registreren (lid worden) en zich aanmelden om eenmaal aan de stemming deel te nemen.

## Aanvullende informatie {#additional-information}

Meer informatie kan op de [ Stemende Belangrijkste ](essentials-voting.md) pagina voor ontwikkelaars worden gevonden.
