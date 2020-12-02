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
source-git-commit: 0051791da06d15a48b82cf93164a89b4ea42ce98
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 0%

---


# Waarderingen {#using-ratings} gebruiken

De `Rating` component wordt gebruikt standalone of samen met andere eigenschappen van Gemeenschappen. Met deze component kunnen leden van de gemeenschap die zich hebben aangemeld hun mening kenbaar maken door inhoud te beoordelen.

## Een waardering toevoegen aan een pagina {#adding-a-rating-to-a-page}

Als u een component `Rating` in de modus Schrijver aan een pagina wilt toevoegen, zoekt u de component `Communities / Rating` en sleept u deze naar een plaats op een pagina, zoals een positie ten opzichte van de functie waarop leden een waardering moeten toepassen.

Voor noodzakelijke informatie, bezoek [de Grondbeginselen van Componenten van Gemeenschappen](basics.md).

Als de [vereiste client-side bibliotheken](rating-basics.md#essentials-for-client-side) worden opgenomen, wordt de `Rating`-component op deze manier weergegeven.

![beoordeling](assets/rating.png)

## Classificatie {#configuring-rating} configureren

Selecteer de geplaatste `Rating` component en selecteer `Configure` pictogram dat het Edit dialoog opent.

![configure-new](assets/configure-new.png)

Onder **[!UICONTROL Texts & Labels]** lusje specificeert u het interne herkenningsteken voor de Classificatie.

![tallyname](assets/tallyname.png)

**[!UICONTROL Tally Name]**
(*Vereist*) Een eenvoudige naam voor  `Rating` welke uniek dit geval identificeert. Moet een geldige knooppuntnaam voor de bewaarplaats zijn.

## Ervaring {#site-visitor-experience} voor bezoekers van site

### Leden {#members}

Er is slechts één score per lid toegestaan. Het lid kan zijn rating te allen tijde wijzigen.

### Anonieme {#anonymous}

Anonieme detachering van een rating wordt niet ondersteund. Site-bezoekers moeten zich registreren (lid worden) en zich aanmelden om deel te nemen.

## Aanvullende informatie {#additional-information}

Meer informatie vindt u op de pagina [Beoordelingsbasisbegrippen](rating-basics.md) voor ontwikkelaars.
