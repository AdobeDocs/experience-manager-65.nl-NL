---
title: Standaardcomponenten configureren in ontwerpmodus
description: Adobe Experience Manager-componenten configureren in ontwerpmodus.
exl-id: 5e232886-75c1-4f0f-b359-4739ae035fd3
solution: Experience Manager, Experience Manager Sites
feature: Authoring
role: User,Admin,Developer
source-git-commit: c77849740fab51377ce60aff5f611e0408dca728
workflow-type: tm+mt
source-wordcount: '905'
ht-degree: 0%

---

# Standaardcomponenten configureren in ontwerpmodus{#configuring-components-in-design-mode}

Wanneer een AEM-instantie buiten de box is geïnstalleerd, is er direct een selectie van componenten beschikbaar in de browser van de component.

Daarnaast zijn er verschillende andere componenten beschikbaar. U kunt de wijze van het Ontwerp gebruiken om [&#x200B; toe te laten/onbruikbaar te maken dergelijke componenten &#x200B;](#enable-disable-components). Wanneer toegelaten en gevestigd op uw pagina kunt u de wijze van het Ontwerp dan gebruiken om [&#x200B; aspecten van het componentenontwerp &#x200B;](#configuring-the-design-of-a-component) te vormen door de attributenparameters uit te geven.

>[!NOTE]
>
>Bij het bewerken van deze componenten moet de nodige voorzichtigheid worden betracht. De ontwerpinstellingen vormen vaak een integraal onderdeel van het ontwerp van de gehele website. Ze moeten daarom alleen worden gewijzigd door iemand met de juiste bevoegdheden en ervaring, vaak een beheerder of een ontwikkelaar. Zie [&#x200B; het Ontwikkelen Componenten &#x200B;](/help/sites-developing/components.md) voor meer informatie.

>[!NOTE]
>
>De ontwerpmodus is alleen beschikbaar voor statische sjablonen. De malplaatjes die met editable malplaatjes worden gecreeerd zouden moeten worden uitgegeven gebruikend de [&#x200B; malplaatjeredacteur &#x200B;](/help/sites-authoring/templates.md).

>[!NOTE]
>
>De ontwerpmodus is alleen beschikbaar voor ontwerpconfiguraties die zijn opgeslagen als inhoud onder ( `/etc`).
>
>Vanaf AEM 6.4 wordt aangeraden ontwerpen op te slaan als configuratiegegevens onder `/apps` ter ondersteuning van scenario&#39;s voor continue implementatie. Ontwerpen die zijn opgeslagen onder `/apps`, kunnen niet worden bewerkt in runtime en de ontwerpmodus is niet beschikbaar voor gebruikers zonder beheerdersrechten voor dergelijke sjablonen.

Dit betekent dat u de onderdelen die zijn toegestaan in het alineasysteem voor de pagina, toevoegt of verwijdert. Het alineasysteem ( `parsys` ) is een samengestelde component die alle andere alineacomponenten bevat. Met het alineasysteem kunnen auteurs componenten van verschillende typen aan een pagina toevoegen omdat deze alle andere alineacomponenten bevat. Elk alineatype wordt vertegenwoordigd als een component.

De inhoud van een productpagina kan bijvoorbeeld een alineasysteem bevatten dat het volgende bevat:

* Een afbeelding van het product (in de vorm van een afbeeldings- of textielafbeeldingsalinea)
* De productomschrijving (als tekstalinea)
* Een tabel met technische gegevens (als tabelalinea)
* Een formulier dat gebruikers invullen (als een formulier begint, formulierelement en alinea die eindigt met een formulier)

>[!NOTE]
>
>Zie [&#x200B; het Ontwikkelen van Componenten &#x200B;](/help/sites-developing/components.md) en [&#x200B; Richtlijnen voor het Gebruiken van Malplaatjes en Componenten &#x200B;](/help/sites-developing/dev-guidelines-bestpractices.md#guidelines-for-using-templates-and-components) voor meer informatie over `parsys`.

>[!CAUTION]
>
>Het bewerken van het ontwerp in de ontwerpmodus, zoals beschreven in dit artikel, is de aanbevolen manier om ontwerpen van statische sjablonen te definiëren
>
>Het aanpassen van ontwerpen in CRX DE is bijvoorbeeld geen goede praktijk en de toepassing van dergelijke ontwerpen kan afwijken van het verwachte gedrag. Zie het ontwikkelaarsdocument [&#x200B; Malplaatjes van de Pagina - Statisch &#x200B;](/help/sites-developing/page-templates-static.md#how-template-designs-are-applied) voor meer informatie.

## Componenten in-/uitschakelen {#enable-disable-components}

Een component in- of uitschakelen:

1. Selecteer de **wijze van het Ontwerp**.

   ![&#x200B; screen_shot_2018-03-22at103113 &#x200B;](assets/screen_shot_2018-03-22at103113.png)

1. Klik op een component. Wanneer de component is geselecteerd, heeft deze een blauwe rand.

   ![&#x200B; screen_shot_2018-03-22at103204 &#x200B;](assets/screen_shot_2018-03-22at103204.png)

1. Klik het **pictogram van de Ouder**.

   ![&#x200B; Ouder &#x200B;](do-not-localize/screen_shot_2018-03-22at103204.png)

   Hiermee selecteert u het alineasysteem dat de huidige component bevat.

1. **vormt** pictogram voor het paragraafsysteem wordt getoond in de de actiebar van de ouder.

   ![&#x200B; vormen &#x200B;](do-not-localize/screen_shot_2018-03-22at103256.png)

   Selecteer deze optie om het dialoogvenster weer te geven.

1. In het dialoogvenster kunt u de componenten definiëren die beschikbaar zijn in de componentenbrowser wanneer u de huidige pagina bewerkt.

   ![&#x200B; screen_shot_2018-03-22at103329 &#x200B;](assets/screen_shot_2018-03-22at103329.png)

   Het dialoogvenster heeft twee tabbladen:

   * Toegestane componenten
   * Instellingen

   **Toegestane Componenten**

   Op het **Toegestane lusje van Componenten**, bepaalt u welke componenten voor parsys beschikbaar zijn.

   * De componenten worden gegroepeerd op hun componentgroepen, die kunnen worden uitgevouwen en samengevouwen.
   * U kunt een hele groep selecteren door de naam van de groep te controleren. U kunt de selectie van alle groepen ongedaan maken door de selectie uit te schakelen.
   * Een min vertegenwoordigt minstens één maar niet alle punten in een groep worden geselecteerd.
   * Er is een zoekopdracht beschikbaar om naar een component op naam te filteren.
   * De tellingen die rechts van de naam van de componentengroep worden vermeld vertegenwoordigen het totale aantal geselecteerde componenten in die groepen ongeacht de filter.

   U definieert de configuratie per paginacomponent. Als onderliggende pagina&#39;s dezelfde sjabloon en/of paginacomponent gebruiken (gewoonlijk uitgelijnd), wordt dezelfde configuratie toegepast op het corresponderende alineasysteem.

   >[!NOTE]
   >
   >Adaptieve formuliercomponenten zijn ontworpen voor gebruik in adaptieve formuliercontainers met het Forms-ecosysteem. Daarom moeten deze componenten alleen worden gebruikt in een adaptieve formuliereditor en werken ze niet in de pagina-editor Sites.

   **Montages**

   Op het **lusje van Montages** kunt u extra opties zoals bepalen om een anker voor elke component te trekken en de cel het opvullen van elke container te bepalen.

1. Selecteer **Gedaan** om uw configuratie te bewaren.

## Het ontwerp van een component configureren {#configuring-the-design-of-a-component}

1. Selecteer de **wijze van het Ontwerp**.

   ![&#x200B; screen_shot_2018-03-22at103113-1 &#x200B;](assets/screen_shot_2018-03-22at103113-1.png)

1. Klik op een component met een blauwe rand. In dit voorbeeld wordt een hoofdafbeeldingscomponent geselecteerd.

   ![&#x200B; screen_shot_2018-03-22at103434 &#x200B;](assets/screen_shot_2018-03-22at103434.png)

1. Gebruik **vormen** pictogram om de dialoog te openen.

   ![&#x200B; vorm pictogram &#x200B;](do-not-localize/screen_shot_2018-03-22at103256-1.png)

   In het ontwerpdialoogvenster kunt u de component configureren op basis van de beschikbare ontwerpparameters.

   ![&#x200B; screen_shot_2018-03-22at103530 &#x200B;](assets/screen_shot_2018-03-22at103530.png)

   Het dialoogvenster heeft drie tabbladen:

   * Hoofd
   * Functies
   * Stijlen

   **Eigenschappen**

   Het **lusje van Eigenschappen** laat u de belangrijke ontwerpparameters van de component vormen. Voor een afbeeldingscomponent kunt u bijvoorbeeld de maximale en minimale grootte van de toegestane afbeelding definiëren.

   **Eigenschappen**

   Het **lusje van Eigenschappen** laat u extra eigenschappen van de component toelaten of onbruikbaar maken. Voor een afbeeldingscomponent kunt u bijvoorbeeld de richting van de afbeelding, de beschikbare uitsnijdopties en of een afbeelding kan worden geüpload definiëren.

   **Stijlen**

   Het **lusje van Stijlen** laat u de CSS klassen en stijlen bepalen die met de component moeten worden gebruikt.

   ![&#x200B; screen_shot_2018-03-22at103741 &#x200B;](assets/screen_shot_2018-03-22at103741.png)

   Gebruik **toevoegen** knoop om extra ingangen aan een veelvoudig-ingangs dialooglijst toe te voegen.

   ![&#x200B; voeg extra ingang &#x200B;](assets/chlimage_1-94.png) toe

   Gebruik het **pictogram van de Schrapping** om een ingang uit een veelvoudig-ingangsdialoog lijst te verwijderen.

   ![&#x200B; Schrapping &#x200B;](do-not-localize/screen_shot_2018-03-22at103809.png)

   Gebruik het **pictogram van de Beweging** om de orde van ingangen in een veelvoudig-ingangsdialoog lijst te herschikken.

   ![&#x200B; Beweging &#x200B;](do-not-localize/screen_shot_2018-03-22at103816.png)

1. Klik het **Gereed** pictogram om de dialoog te bewaren en te sluiten.
