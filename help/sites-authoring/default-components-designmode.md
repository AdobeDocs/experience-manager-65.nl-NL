---
title: Standaardcomponenten configureren in ontwerpmodus
description: Adobe Experience Manager-componenten configureren in ontwerpmodus.
exl-id: 5e232886-75c1-4f0f-b359-4739ae035fd3
solution: Experience Manager, Experience Manager Sites
feature: Authoring
role: User,Admin,Architect,Developer
source-git-commit: 9a3008553b8091b66c72e0b6c317573b235eee24
workflow-type: tm+mt
source-wordcount: '905'
ht-degree: 0%

---

# Standaardcomponenten configureren in ontwerpmodus{#configuring-components-in-design-mode}

Wanneer AEM instantie buiten de doos wordt geïnstalleerd, is een selectie van componenten onmiddellijk beschikbaar in Componentbrowser.

Daarnaast zijn er verschillende andere componenten beschikbaar. U kunt de wijze van het Ontwerp gebruiken om [ toe te laten/onbruikbaar te maken dergelijke componenten ](#enable-disable-components). Wanneer toegelaten en gevestigd op uw pagina kunt u de wijze van het Ontwerp dan gebruiken om [ aspecten van het componentenontwerp ](#configuring-the-design-of-a-component) te vormen door de attributenparameters uit te geven.

>[!NOTE]
>
>Bij het bewerken van deze componenten moet de nodige voorzichtigheid worden betracht. De ontwerpinstellingen vormen vaak een integraal onderdeel van het ontwerp van de gehele website. Ze moeten daarom alleen worden gewijzigd door iemand met de juiste bevoegdheden en ervaring, vaak een beheerder of een ontwikkelaar. Zie [ het Ontwikkelen Componenten ](/help/sites-developing/components.md) voor meer informatie.

>[!NOTE]
>
>De ontwerpmodus is alleen beschikbaar voor statische sjablonen. De malplaatjes die met editable malplaatjes worden gecreeerd zouden moeten worden uitgegeven gebruikend de [ malplaatjeredacteur ](/help/sites-authoring/templates.md).

>[!NOTE]
>
>De ontwerpmodus is alleen beschikbaar voor ontwerpconfiguraties die zijn opgeslagen als inhoud onder ( `/etc`).
>
>Beginnend in AEM 6.4, wordt het geadviseerd om ontwerpen als configuratiegegevens onder `/apps` op te slaan om ononderbroken plaatsingsscenario&#39;s te steunen. Ontwerpen die zijn opgeslagen onder `/apps`, kunnen niet worden bewerkt in runtime en de ontwerpmodus is niet beschikbaar voor gebruikers zonder beheerdersrechten voor dergelijke sjablonen.

Dit betekent dat u de onderdelen die zijn toegestaan in het alineasysteem voor de pagina, toevoegt of verwijdert. Het alineasysteem ( `parsys` ) is een samengestelde component die alle andere alineacomponenten bevat. Met het alineasysteem kunnen auteurs componenten van verschillende typen aan een pagina toevoegen omdat deze alle andere alineacomponenten bevat. Elk alineatype wordt vertegenwoordigd als een component.

De inhoud van een productpagina kan bijvoorbeeld een alineasysteem bevatten dat het volgende bevat:

* Een afbeelding van het product (in de vorm van een afbeeldings- of textielafbeeldingsalinea)
* De productomschrijving (als tekstalinea)
* Een tabel met technische gegevens (als tabelalinea)
* Een formulier dat gebruikers invullen (als een formulier begint, formulierelement en alinea die eindigt met een formulier)

>[!NOTE]
>
>Zie [ het Ontwikkelen van Componenten ](/help/sites-developing/components.md) en [ Richtlijnen voor het Gebruiken van Malplaatjes en Componenten ](/help/sites-developing/dev-guidelines-bestpractices.md#guidelines-for-using-templates-and-components) voor meer informatie over `parsys`.

>[!CAUTION]
>
>Het bewerken van het ontwerp in de ontwerpmodus, zoals beschreven in dit artikel, is de aanbevolen manier om ontwerpen van statische sjablonen te definiëren
>
>Het aanpassen van ontwerpen in CRX DE is bijvoorbeeld geen goede praktijk en de toepassing van dergelijke ontwerpen kan afwijken van het verwachte gedrag. Zie het ontwikkelaarsdocument [ Malplaatjes van de Pagina - Statisch ](/help/sites-developing/page-templates-static.md#how-template-designs-are-applied) voor meer informatie.

## Componenten in-/uitschakelen {#enable-disable-components}

Een component in- of uitschakelen:

1. Selecteer de **wijze van het Ontwerp**.

   ![ screen_shot_2018-03-22at103113 ](assets/screen_shot_2018-03-22at103113.png)

1. Klik op een component. Wanneer de component is geselecteerd, heeft deze een blauwe rand.

   ![ screen_shot_2018-03-22at103204 ](assets/screen_shot_2018-03-22at103204.png)

1. Klik het **pictogram van de Ouder**.

   ![ Ouder ](do-not-localize/screen_shot_2018-03-22at103204.png)

   Hiermee selecteert u het alineasysteem dat de huidige component bevat.

1. **vormt** pictogram voor het paragraafsysteem wordt getoond in de de actiebar van de ouder.

   ![ vormen ](do-not-localize/screen_shot_2018-03-22at103256.png)

   Selecteer deze optie om het dialoogvenster weer te geven.

1. In het dialoogvenster kunt u de componenten definiëren die beschikbaar zijn in de componentenbrowser wanneer u de huidige pagina bewerkt.

   ![ screen_shot_2018-03-22at103329 ](assets/screen_shot_2018-03-22at103329.png)

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

   ![ screen_shot_2018-03-22at103113-1 ](assets/screen_shot_2018-03-22at103113-1.png)

1. Klik op een component met een blauwe rand. In dit voorbeeld wordt een hoofdafbeeldingscomponent geselecteerd.

   ![ screen_shot_2018-03-22at103434 ](assets/screen_shot_2018-03-22at103434.png)

1. Gebruik **vormen** pictogram om de dialoog te openen.

   ![ vorm pictogram ](do-not-localize/screen_shot_2018-03-22at103256-1.png)

   In het ontwerpdialoogvenster kunt u de component configureren op basis van de beschikbare ontwerpparameters.

   ![ screen_shot_2018-03-22at103530 ](assets/screen_shot_2018-03-22at103530.png)

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

   ![ screen_shot_2018-03-22at103741 ](assets/screen_shot_2018-03-22at103741.png)

   Gebruik **toevoegen** knoop om extra ingangen aan een veelvoudig-ingangs dialooglijst toe te voegen.

   ![ voeg extra ingang ](assets/chlimage_1-94.png) toe

   Gebruik het **pictogram van de Schrapping** om een ingang uit een veelvoudig-ingangsdialoog lijst te verwijderen.

   ![ Schrapping ](do-not-localize/screen_shot_2018-03-22at103809.png)

   Gebruik het **pictogram van de Beweging** om de orde van ingangen in een veelvoudig-ingangsdialoog lijst te herschikken.

   ![ Beweging ](do-not-localize/screen_shot_2018-03-22at103816.png)

1. Klik het **Gereed** pictogram om de dialoog te bewaren en te sluiten.
