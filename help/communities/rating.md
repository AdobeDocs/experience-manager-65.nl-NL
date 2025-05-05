---
title: Classificaties gebruiken
description: Leer hoe u een Beoordelingscomponent aan een pagina toevoegt waarmee leden van de gemeenschap die zich hebben aangemeld hun mening kunnen uiten door inhoud te beoordelen.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
exl-id: 7534ad5d-b408-4b09-bd3d-da7ab009d55b
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '215'
ht-degree: 0%

---

# Classificaties gebruiken {#using-ratings}

De component `Rating` wordt gebruikt op zichzelf of met andere functies van een Gemeenschappen. Met deze component kunnen leden van de gemeenschap die zich hebben aangemeld hun mening kenbaar maken door inhoud te beoordelen.

## Een waardering toevoegen aan een pagina {#adding-a-rating-to-a-page}

Als u een component `Rating` in de modus Schrijven aan een pagina wilt toevoegen, zoekt u de component `Communities / Rating` en sleept u deze naar de juiste positie op een pagina, zoals een positie ten opzichte van de functie die leden kunnen toekennen.

Voor noodzakelijke informatie, bezoek {de Grondbeginselen van de Componenten van 0} Gemeenschappen [&#128279;](basics.md).

Wanneer de [ vereiste cliënt-zijbibliotheken ](rating-basics.md#essentials-for-client-side) inbegrepen zijn, is dit hoe de `Rating` component verschijnt.

![ classificatie ](assets/rating.png)

## Classificatie configureren {#configuring-rating}

Selecteer de geplaatste component `Rating` , zodat u het pictogram `Configure` kunt openen en selecteren waarmee het dialoogvenster Bewerken wordt geopend.

![ vorm-nieuw ](assets/configure-new.png)

Onder het tabblad **[!UICONTROL Texts & Labels]** geeft u de interne id voor de waardering op.

![ tallyname ](assets/tallyname.png)

**[!UICONTROL Tally Name]**
(*Vereist*) Een eenvoudige naam voor `Rating` die uniek deze instantie identificeert. Moet een geldige knooppuntnaam voor de bewaarplaats zijn.

## Ervaring met sitebezoekers {#site-visitor-experience}

### Leden {#members}

Er is slechts één score per lid toegestaan. Het lid kan zijn rating te allen tijde wijzigen.

### Anoniem {#anonymous}

Anonieme detachering van een rating wordt niet ondersteund. Site-bezoekers moeten zich registreren (lid worden) en zich aanmelden om deel te nemen.

## Aanvullende informatie {#additional-information}

Meer informatie kan op de [&#128279;](rating-basics.md) pagina van de Hoofdzaak van de Classificatie  worden gevonden voor ontwikkelaars.
