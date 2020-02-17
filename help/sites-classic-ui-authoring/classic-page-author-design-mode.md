---
title: Componenten configureren in ontwerpmodus
seo-title: Componenten configureren in ontwerpmodus
description: Wanneer een AEM-instantie buiten de verpakking wordt geïnstalleerd, is er direct een selectie van componenten beschikbaar in het hulpstuk. Daarnaast zijn er verschillende andere componenten beschikbaar. U kunt de ontwerpmodus gebruiken om dergelijke componenten in- en uit te schakelen.
seo-description: Wanneer een AEM-instantie buiten de verpakking wordt geïnstalleerd, is er direct een selectie van componenten beschikbaar in het hulpstuk. Daarnaast zijn er verschillende andere componenten beschikbaar. U kunt de ontwerpmodus gebruiken om dergelijke componenten in- en uit te schakelen.
uuid: 2cd5dad0-2f9c-4f34-aae8-1638d1445eb3
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: 10466b49-f8bd-4c2c-8106-b0c7ba054989
docset: aem65
translation-type: tm+mt
source-git-commit: bcb1840d23ae538c183eecb0678b6a75d346aa50

---


# Componenten configureren in ontwerpmodus{#configuring-components-in-design-mode}

Wanneer een AEM-instantie buiten de verpakking wordt geïnstalleerd, is er direct een selectie van componenten beschikbaar in het hulpstuk.

Daarnaast zijn er verschillende andere componenten beschikbaar. U kunt de ontwerpmodus gebruiken om dergelijke componenten [in of uit te](#enabledisablecomponentsusingdesignmode)schakelen. Wanneer toegelaten en gevestigd op uw pagina kunt u de wijze van het Ontwerp dan gebruiken om aspecten van het componentenontwerp [te](#configuringcomponentsusingdesignmode) vormen door de attributenparameters uit te geven.

>[!NOTE]
>
>Bij het bewerken van deze componenten moet de nodige voorzichtigheid worden betracht. De ontwerpinstellingen vormen vaak een integraal onderdeel van het ontwerp van de gehele website en moeten daarom alleen worden gewijzigd door iemand met de juiste bevoegdheden (en ervaring), vaak een beheerder of ontwikkelaar. Zie [Componenten](/help/sites-developing/components.md) ontwikkelen voor meer informatie.

Hierbij worden in feite de onderdelen toegevoegd of verwijderd die in het alineasysteem voor de pagina zijn toegestaan. Het alineasysteem ( `parsys`) is een samengestelde component die alle andere alineacomponenten bevat. Met het alineasysteem kunnen auteurs componenten van verschillende typen aan een pagina toevoegen omdat deze alle andere alineacomponenten bevat. Elk alineatype wordt vertegenwoordigd als een component.

De inhoud van een productpagina kan bijvoorbeeld een alineasysteem bevatten dat het volgende bevat:

* Een afbeelding van het product (in de vorm van een afbeeldings- of textielafbeeldingsalinea)
* De productomschrijving (als tekstalinea)
* Een tabel met technische gegevens (als tabelalinea)
* Een formulier dat gebruikers invullen (als een formulier begint, formulierelement en alinea die eindigt met een formulier)

>[!NOTE]
>
>Zie [Componenten](/help/sites-developing/components.md#paragraphsystem) en [Richtlijnen ontwikkelen voor het Gebruiken van Malplaatjes en Componenten](/help/sites-developing/dev-guidelines-bestpractices.md#guidelines-for-using-templates-and-components) voor meer informatie over `parsys`.

## Componenten in-/uitschakelen {#enable-disable-components}

In de ontwerpmodus wordt het hulpprogramma geminimaliseerd en kunt u de componenten configureren die toegankelijk zijn voor ontwerpen:

1. Als u de ontwerpmodus wilt activeren, opent u een pagina die u wilt bewerken en gebruikt u het pictogram Sidetrap:

   ![](do-not-localize/chlimage_1.png)

1. Klik op **Bewerken** op het alineasysteem (**Ontwerp van delen**).

   ![screen_shot_2012-02-08at102726am](assets/screen_shot_2012-02-08at102726am.png)

1. Er wordt een dialoogvenster geopend met een lijst van de componentgroepen die in de Sidetrap worden weergegeven, samen met de afzonderlijke componenten die ze bevatten.

   Selecteer de gewenste onderdelen om de componenten toe te voegen of te verwijderen die beschikbaar moeten zijn in het zijpaneel.

   ![screen_shot_2012-02-08at103407am](assets/screen_shot_2012-02-08at103407am.png)

1. In de ontwerpmodus wordt de Sidetrap geminimaliseerd. Door op de pijl te klikken kunt u de Sidetrap maximaliseren en terugkeren naar de bewerkingsmodus:

   ![](do-not-localize/sidekick-collapsed.png)

## Het ontwerp van een component configureren {#configuring-the-design-of-a-component}

In de ontwerpmodus kunt u ook kenmerken configureren voor de afzonderlijke componenten. Elke component heeft zijn eigen parameters, toont het volgende voorbeeld de component van het **Beeld** :

1. Als u de ontwerpmodus wilt activeren, opent u een pagina die u wilt bewerken en gebruikt u het pictogram Sidetrap:

   ![](do-not-localize/chlimage_1-1.png)

1. U kunt het ontwerp van componenten configureren.

   Als u bijvoorbeeld op **Bewerken** klikt in de component Image (**Ontwerp van afbeelding**), kunt u de componentspecifieke parameters configureren:

   ![chlimage_1-5](assets/chlimage_1-5.png)

1. Klik op **OK** om de wijzigingen op te slaan.

1. In de ontwerpmodus wordt de Sidetrap geminimaliseerd. Door op de pijl te klikken kunt u de Sidetrap maximaliseren en terugkeren naar de bewerkingsmodus:

   ![](do-not-localize/sidekick-collapsed-1.png)
