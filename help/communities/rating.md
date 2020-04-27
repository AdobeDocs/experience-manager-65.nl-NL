---
title: Classificaties gebruiken
seo-title: Classificaties gebruiken
description: Een beoordelingscomponent toevoegen aan een pagina
seo-description: Een beoordelingscomponent toevoegen aan een pagina
uuid: a986970b-1221-4648-9a69-410f4480e0ae
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: a0e5491e-66bc-47b0-94a5-45a02bc558da
translation-type: tm+mt
source-git-commit: 62f2a11491e427a13cecae75c225ed41a44783cd

---


# Classificaties gebruiken {#using-ratings}

De `Rating` component wordt op zichzelf of in combinatie met andere communautaire kenmerken gebruikt. Met deze component kunnen leden van de gemeenschap die zich hebben aangemeld hun mening kenbaar maken door inhoud te beoordelen.

## Een waardering toevoegen aan een pagina {#adding-a-rating-to-a-page}

Als u een `Rating` component aan een pagina wilt toevoegen in de modus Schrijven, zoekt u de component `Communities / Rating` en sleept u deze naar een plaats op een pagina, zoals een positie ten opzichte van de functie die leden kunnen waarderen.

Ga voor de benodigde informatie naar [Community Components Basics](basics.md).

Wanneer de [vereiste client-side bibliotheken](rating-basics.md#essentials-for-client-side) worden opgenomen, wordt de `Rating` component op deze manier weergegeven.

![chlimage_1-493](assets/chlimage_1-493.png)

## Classificatie configureren {#configuring-rating}

Selecteer de geplaatste `Rating` component die u wilt openen en selecteer het `Configure` pictogram waarmee het dialoogvenster Bewerken wordt geopend.

![chlimage_1-494](assets/chlimage_1-494.png)

Onder het tabblad **[!UICONTROL Teksten en labels]** geeft u de interne id voor de waardering op.

![chlimage_1-495](assets/chlimage_1-495.png)

**[!UICONTROL Tally Name]**(*Required*) Een eenvoudige naam voor `Rating`welke uniek dit geval identificeert. Moet een geldige knooppuntnaam voor de bewaarplaats zijn.

## Ervaring met sitebezoekers {#site-visitor-experience}

### Leden {#members}

Er is slechts één score per lid toegestaan. Het lid kan zijn rating te allen tijde wijzigen.

### Anoniem {#anonymous}

Anonieme detachering van een rating wordt niet ondersteund. Site-bezoekers moeten zich registreren (lid worden) en zich aanmelden om deel te nemen.

## Additional Information {#additional-information}

Meer informatie vindt u op de pagina [Beoordelingselementen](rating-basics.md) voor ontwikkelaars.
