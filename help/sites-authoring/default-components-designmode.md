---
title: Standaardcomponenten configureren in ontwerpmodus
description: Componenten configureren in ontwerpmodus
uuid: b9c9792d-4398-446d-8767-44d4e7ce9a2e
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: 8ae6817a-16d3-4740-b67a-498e75adf350
exl-id: 5e232886-75c1-4f0f-b359-4739ae035fd3
source-git-commit: e1a0b114ce16d0e7f6a464e9d30b8f111297bcc6
workflow-type: tm+mt
source-wordcount: '907'
ht-degree: 0%

---

# Standaardcomponenten configureren in ontwerpmodus{#configuring-components-in-design-mode}

Wanneer AEM instantie buiten de doos wordt geïnstalleerd, is een selectie van componenten onmiddellijk beschikbaar in Componentbrowser.

Daarnaast zijn er verschillende andere componenten beschikbaar. U kunt de ontwerpmodus gebruiken om [deze componenten in-/uitschakelen](#enable-disable-components). Als deze optie is ingeschakeld en zich op de pagina bevindt, kunt u de ontwerpmodus gebruiken om [aspecten van het componentontwerp configureren](#configuring-the-design-of-a-component) door de kenmerkparameters te bewerken.

>[!NOTE]
>
>Bij het bewerken van deze componenten moet de nodige voorzichtigheid worden betracht. De ontwerpinstellingen vormen vaak een integraal onderdeel van het ontwerp van de gehele website. Ze moeten daarom alleen worden gewijzigd door iemand met de juiste bevoegdheden en ervaring, vaak een beheerder of een ontwikkelaar. Zie [Componenten ontwikkelen](/help/sites-developing/components.md) voor meer informatie .

>[!NOTE]
>
>De ontwerpmodus is alleen beschikbaar voor statische sjablonen. Sjablonen die met bewerkbare sjablonen zijn gemaakt, moeten worden bewerkt met de [sjablooneditor](/help/sites-authoring/templates.md).

>[!NOTE]
>
>De ontwerpmodus is alleen beschikbaar voor ontwerpconfiguraties die zijn opgeslagen als inhoud onder ( `/etc`).
>
>Beginnend in AEM 6.4, wordt het geadviseerd om ontwerpen als configuratiegegevens onder op te slaan `/apps` om ononderbroken plaatsingsscenario&#39;s te steunen. Onder `/apps` kunnen niet worden bewerkt tijdens runtime en de ontwerpmodus is niet beschikbaar voor gebruikers zonder beheerdersrechten voor dergelijke sjablonen.

Dit betekent dat u de onderdelen die zijn toegestaan in het alineasysteem voor de pagina, toevoegt of verwijdert. Het alineasysteem ( `parsys`) is een samengestelde component die alle andere alineacomponenten bevat. Met het alineasysteem kunnen auteurs componenten van verschillende typen aan een pagina toevoegen omdat deze alle andere alineacomponenten bevat. Elk alineatype wordt vertegenwoordigd als een component.

De inhoud van een productpagina kan bijvoorbeeld een alineasysteem bevatten dat het volgende bevat:

* Een afbeelding van het product (in de vorm van een afbeeldings- of textielafbeeldingsalinea)
* De productomschrijving (als tekstalinea)
* Een tabel met technische gegevens (als tabelalinea)
* Een formulier dat gebruikers invullen (als een formulier begint, formulierelement en alinea die eindigt met een formulier)

>[!NOTE]
>
>Zie [Componenten ontwikkelen](/help/sites-developing/components.md) en [Richtlijnen voor het gebruik van sjablonen en componenten](/help/sites-developing/dev-guidelines-bestpractices.md#guidelines-for-using-templates-and-components) voor meer informatie over `parsys`.

>[!CAUTION]
>
>Het bewerken van het ontwerp in de ontwerpmodus, zoals beschreven in dit artikel, is de aanbevolen manier om ontwerpen van statische sjablonen te definiëren
>
>Het aanpassen van ontwerpen in bijvoorbeeld CRX DE is geen goede praktijk en de toepassing van dergelijke ontwerpen kan van verwacht gedrag variëren. Zie het document voor ontwikkelaars [Paginasjablonen - statisch](/help/sites-developing/page-templates-static.md#how-template-designs-are-applied) voor meer informatie .

## Componenten in-/uitschakelen {#enable-disable-components}

Een component in- of uitschakelen:

1. Selecteer **Ontwerp** in.

   ![screen_shot_2018-03-22at103113](assets/screen_shot_2018-03-22at103113.png)

1. Tik of klik op een component. Wanneer de component is geselecteerd, krijgt deze een blauwe rand.

   ![screen_shot_2018-03-22at103204](assets/screen_shot_2018-03-22at103204.png)

1. Klik of tik op **Bovenliggend** pictogram.

   ![](do-not-localize/screen_shot_2018-03-22at103204.png)

   Hiermee selecteert u het alineasysteem dat de huidige component bevat.

1. De **Configureren** pictogram voor het alineasysteem wordt weergegeven op de actiebalk van het bovenliggende element.

   ![](do-not-localize/screen_shot_2018-03-22at103256.png)

   Selecteer deze optie om het dialoogvenster weer te geven.

1. In het dialoogvenster kunt u de componenten definiëren die beschikbaar zijn in de componentenbrowser wanneer u de huidige pagina bewerkt.

   ![screen_shot_2018-03-22at103329](assets/screen_shot_2018-03-22at103329.png)

   Het dialoogvenster heeft twee tabbladen:

   * Toegestane componenten
   * Instellingen

   **Toegestane componenten**

   Op de **Toegestane componenten** tab, bepaalt u welke componenten voor parsys beschikbaar zijn.

   * De componenten worden gegroepeerd op hun componentgroepen, die kunnen worden uitgevouwen en samengevouwen.
   * U kunt een hele groep selecteren door de naam van de groep te controleren en u kunt de selectie van alle groepen opheffen door de selectie uit te schakelen.
   * Een min vertegenwoordigt minstens één maar niet alle punten in een groep worden geselecteerd.
   * Er is een zoekopdracht beschikbaar om naar een component op naam te filteren.
   * De tellingen die rechts van de naam van de componentengroep worden vermeld vertegenwoordigen het totale aantal geselecteerde componenten in die groepen ongeacht de filter.

   U definieert de configuratie per paginacomponent. Als onderliggende pagina&#39;s dezelfde sjabloon en/of paginacomponent gebruiken (gewoonlijk uitgelijnd), wordt dezelfde configuratie toegepast op het corresponderende alineasysteem.

   >[!NOTE]
   >
   >Adaptieve formuliercomponenten zijn ontworpen om te werken in de container van adaptieve formulieren met behulp van het Forms-ecosysteem. Daarom moeten deze componenten alleen worden gebruikt in een adaptieve formuliereditor en werken ze niet in de pagina-editor Sites.

   **Instellingen**

   Op de **Instellingen** kunt u aanvullende opties definiëren, zoals het tekenen van een anker voor elke component en het definiëren van de celopvulling van elke container.

1. Selecteren **Gereed** om uw configuratie op te slaan.

## Het ontwerp van een component configureren {#configuring-the-design-of-a-component}

1. Selecteer **Ontwerp** in.

   ![screen_shot_2018-03-22at103113-1](assets/screen_shot_2018-03-22at103113-1.png)

1. Tik of klik op een component met een blauwe rand. In dit voorbeeld wordt een hoofdafbeeldingscomponent geselecteerd.

   ![screen_shot_2018-03-22at103434](assets/screen_shot_2018-03-22at103434.png)

1. Gebruik de **Configureren** om het dialoogvenster te openen.

   ![](do-not-localize/screen_shot_2018-03-22at103256-1.png)

   In het ontwerpdialoogvenster kunt u de component configureren op basis van de beschikbare ontwerpparameters.

   ![screen_shot_2018-03-22at103530](assets/screen_shot_2018-03-22at103530.png)

   Het dialoogvenster heeft drie tabbladen:

   * Hoofd
   * Functies
   * Stijlen

   **Eigenschappen**

   De **Eigenschappen** kunt u de belangrijke ontwerpparameters van de component configureren. Voor een afbeeldingscomponent kunt u bijvoorbeeld de maximale en minimale grootte van de toegestane afbeelding definiëren.

   **Functies**

   De **Functies** kunt u extra functies van de component in- of uitschakelen. Voor een afbeeldingscomponent kunt u bijvoorbeeld de richting van de afbeelding, de beschikbare uitsnijdopties en of een afbeelding kan worden geüpload definiëren.

   **Stijlen**

   De **Stijlen** kunt u de CSS-klassen en -stijlen definiëren die met de component moeten worden gebruikt.

   ![screen_shot_2018-03-22at103741](assets/screen_shot_2018-03-22at103741.png)

   Gebruik de **Toevoegen** om aanvullende vermeldingen toe te voegen aan een lijst met meervoudige vermeldingen.

   ![chlimage_1-94](assets/chlimage_1-94.png)

   Gebruik het pictogram** Verwijderen **pictogram om een item uit een lijst met meervoudige items te verwijderen.

   ![](do-not-localize/screen_shot_2018-03-22at103809.png)

   Gebruik de **Verplaatsen** om de volgorde van items in een meervoudige-invoerdialooglijst te wijzigen.

   ![](do-not-localize/screen_shot_2018-03-22at103816.png)

1. Klik of tik op **Gereed** om het dialoogvenster op te slaan en te sluiten.
