---
title: Modellen voor inhoudsfragmenten maken, headless Quick Start Guide
description: Definieer de structuur van de inhoud die u maakt en gebruikt met behulp van de mogelijkheden zonder kop in Adobe Experience Manager (AEM), met behulp van Content Fragment Models.
exl-id: 653e35c9-7b6a-49ae-b55d-af2ec40e257d
solution: Experience Manager, Experience Manager Sites
feature: Headless,Content Fragments,GraphQL,Persisted Queries,Developing
role: Admin,Architect,Data Architect,Developer
source-git-commit: 9a3008553b8091b66c72e0b6c317573b235eee24
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---

# Modellen voor inhoudsfragmenten maken, headless Quick Start Guide {#creating-content-fragment-models}

Definieer de structuur van de inhoud die u maakt en gebruikt met behulp van de mogelijkheden zonder kop in Adobe Experience Manager (AEM), met behulp van Content Fragment Models.

## Wat zijn modellen van inhoudsfragmenten? {#what-are-content-fragment-models}

[Nu u een configuratie hebt gecreeerd,](create-configuration.md) U kunt het gebruiken om de Modellen van het Fragment van de Inhoud te creëren.

Met Content Fragment Models wordt de structuur gedefinieerd van de gegevens en inhoud die u maakt en beheert in AEM. Ze dienen als een soort basisstructuur voor je inhoud. Wanneer u ervoor kiest inhoud te maken, selecteren de auteurs een van de door u gedefinieerde modellen van inhoudsfragmenten die u als hulplijnen bij het maken van inhoud gebruikt.

## Een model voor een inhoudsfragment maken {#how-to-create-a-content-fragment-model}

Een informatiearchitect zou deze taken slechts sporadisch uitvoeren aangezien de nieuwe modellen worden vereist. Voor deze gids Aan de slag, creeert u slechts één model.

1. Meld u aan bij AEM en selecteer in het hoofdmenu **Gereedschappen > Elementen > Modellen van inhoudsfragmenten**.
1. Klik op de map die u hebt gemaakt door uw configuratie te maken.

   ![De map Modellen](assets/models-folder.png)
1. Klikken **Maken**.
1. Geef een **Modeltitel**, **Tags**, en **Beschrijving**. U kunt ook selecteren/deselecteren **Model inschakelen** om te bepalen of het model onmiddellijk na verwezenlijking wordt toegelaten.

   ![Een model maken](assets/models-create.png)
1. Klik in het bevestigingsvenster op **Openen** om uw model te configureren.

   ![Bevestigingsvenster](assets/models-confirmation.png)
1. Met de **Inhoudsfragmentmodeleditor** kunt u het inhoudsfragmentmodel samenstellen door velden te slepen en neer te zetten vanaf het tabblad **Gegevenstypen** kolom.

   ![Velden slepen en neerzetten](assets/models-drag-and-drop.png)

1. Nadat u een veld hebt geplaatst, moet u de eigenschappen ervan configureren. De redacteur schakelt automatisch aan **Eigenschappen** voor het toegevoegde veld waarin u de verplichte velden kunt opgeven.

   ![Eigenschappen configureren](assets/models-configure-properties.png)
1. Wanneer u klaar bent met het samenstellen van uw model, klikt u op **Opslaan**.

1. De modus van het nieuwe model is afhankelijk van of u **Model inschakelen** bij het maken van het model:
   * geselecteerd - het nieuwe model is al **Ingeschakeld**
   * niet geselecteerd - het nieuwe model wordt gecreeerd in **Concept** mode

1. Als dit nog niet het geval is, moet het model **Ingeschakeld** om het te gebruiken.
   1. Selecteer het model dat u hebt gemaakt en klik op **Inschakelen**.

      ![Het model inschakelen](assets/models-enable.png)
   1. Bevestig het toelaten van het model door te tikken of te klikken **Inschakelen** in het bevestigingsdialoogvenster.

      ![Bevestigingsvenster inschakelen](assets/models-enabling.png)
1. Het model is nu ingeschakeld en klaar voor gebruik.

   ![Model ingeschakeld](assets/models-enabled.png)

De **Inhoudsfragmentmodeleditor** ondersteunt veel verschillende gegevenstypen, zoals eenvoudige tekstvelden, elementverwijzingen, verwijzingen naar andere modellen en JSON-gegevens.

U kunt meerdere modellen maken. Modellen kunnen verwijzen naar andere inhoudsfragmenten. Gebruiken [configuraties](create-configuration.md) om uw modellen te organiseren.

## Volgende stappen {#next-steps}

Nu u de structuren van uw Inhoudsfragmenten hebt gedefinieerd door modellen te maken, kunt u verdergaan naar het derde deel van de gids Aan de slag en [Maak mappen waarin u de fragmenten opslaat.](create-assets-folder.md)

>[!TIP]
>
>Voor volledige details over de Modellen van het Fragment van de Inhoud, zie [Documentatie bij Content Fragment Models](/help/assets/content-fragments/content-fragments-models.md)
