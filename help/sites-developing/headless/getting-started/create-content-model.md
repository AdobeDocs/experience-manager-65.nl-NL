---
title: Modellen voor inhoudsfragmenten maken, headless Quick Start Guide
description: Definieer de structuur van de inhoud die u wilt maken en gebruiken met behulp van AEM mogelijkheden zonder kop door Modellen van inhoudsfragmenten te gebruiken.
exl-id: 8e3e4d00-34d3-4d4f-bc3a-43b8a322b986
source-git-commit: a5cb385aa369a5e59889e77597119358b77b55be
workflow-type: tm+mt
source-wordcount: '492'
ht-degree: 0%

---

# Modellen voor inhoudsfragmenten maken, headless Quick Start Guide {#creating-content-fragment-models}

Definieer de structuur van de inhoud die u wilt maken en gebruiken met behulp van AEM mogelijkheden zonder kop door Modellen van inhoudsfragmenten te gebruiken.

## Wat zijn modellen van inhoudsfragmenten? {#what-are-content-fragment-models}

[Nu u een configuratie hebt gecreeerd,](create-configuration.md) U kunt het gebruiken om de Modellen van het Fragment van de Inhoud tot stand te brengen.

Met Content Fragment Models wordt de structuur gedefinieerd van de gegevens en inhoud die u in AEM maakt en beheert. Ze dienen als een soort basisstructuur voor je inhoud. Wanneer u ervoor kiest inhoud te maken, selecteren de auteurs een model voor inhoudsfragmenten dat u definieert en dat hen bij het maken van inhoud begeleidt.

## Een model voor een inhoudsfragment maken {#how-to-create-a-content-fragment-model}

Een informatiearchitect zou deze taken slechts sporadisch uitvoeren aangezien de nieuwe modellen worden vereist. Om aan de slag te kunnen gaan, hoeven we maar één model te maken.

1. Meld u aan bij AEM en selecteer in het hoofdmenu **Gereedschappen -> Middelen -> Modellen van inhoudsfragmenten**.
1. Tik of klik op de map die u hebt gemaakt door uw configuratie te maken.

   ![De map Modellen](../assets/models-folder.png)
1. Tik of klik op **Maken**.
1. Een **Modeltitel**, **Tags** en **Beschrijving**. U kunt ook selecteren/deselecteren **Model inschakelen** om te bepalen of het model onmiddellijk na verwezenlijking wordt toegelaten.

   ![Een model maken](../assets/models-create.png)
1. Tik of klik in het bevestigingsvenster op **Openen** om uw model te configureren.

   ![Bevestigingsvenster](../assets/models-confirmation.png)
1. Met de **Inhoudsfragmentmodeleditor**, maakt u het model van het inhoudsfragment door velden te slepen en neer te zetten vanaf het tabblad **Gegevenstypen** kolom.

   ![Velden slepen en neerzetten](../assets/models-drag-and-drop.png)

1. Nadat u een veld hebt geplaatst, moet u de eigenschappen ervan configureren. De redacteur zal automatisch aan **Eigenschappen** voor het toegevoegde veld waarin u de verplichte velden kunt opgeven.

   ![Eigenschappen configureren](../assets/models-configure-properties.png)
1. Tik of klik op **Opslaan**.

1. De modus van het nieuwe model is afhankelijk van of u **Model inschakelen** bij het maken van het model:
   * geselecteerd - het nieuwe model zal reeds worden **Ingeschakeld**
   * niet geselecteerd - het nieuwe model wordt gecreeerd in **Concept** mode

1. Als dit nog niet het geval is, moet het model **Ingeschakeld** om het te gebruiken.
   1. Selecteer het model dat u net hebt gemaakt en tik of klik op **Inschakelen**.

      ![Het model inschakelen](../assets/models-enable.png)
   1. Bevestig het toelaten van het model door te tikken of te klikken **Inschakelen** in het bevestigingsdialoogvenster.

      ![Bevestigingsvenster inschakelen](../assets/models-enabling.png)
1. Het model is nu ingeschakeld en klaar voor gebruik.

   ![Model ingeschakeld](../assets/models-enabled.png)

De **Inhoudsfragmentmodeleditor** ondersteunt veel verschillende gegevenstypen, zoals eenvoudige tekstvelden, elementverwijzingen, verwijzingen naar andere modellen en JSON-gegevens.

U kunt meerdere modellen maken. Modellen kunnen verwijzen naar andere inhoudsfragmenten. Gebruiken [configuraties](create-configuration.md) om uw modellen te organiseren.

## Volgende stappen {#next-steps}

Nu u de structuren van uw Inhoudsfragmenten hebt gedefinieerd door modellen te maken, kunt u verdergaan naar het derde deel van de gids Aan de slag en [Maak mappen waarin u de fragmenten zelf opslaat.](create-assets-folder.md)

>[!TIP]
>
>Voor volledige informatie over modellen van inhoudsfragmenten raadpleegt u de [Documentatie bij Content Fragment Models](/help/assets/content-fragments/content-fragments-models.md)
