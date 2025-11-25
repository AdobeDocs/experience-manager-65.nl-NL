---
title: Inhoudsfragmenten zonder kop Handleiding voor snel starten maken
description: Leer hoe u AEM Content Fragments kunt gebruiken om pagina-onafhankelijke inhoud te ontwerpen, maken, beheren en gebruiken voor levering zonder kop.
exl-id: 5787204d-bcce-447e-b98c-2bc1c0d744c3
solution: Experience Manager, Experience Manager Sites
feature: Headless,Content Fragments,GraphQL,Persisted Queries,Developing
role: Admin,Developer
source-git-commit: 07289e891399a78568dcac957bc089cc08c7898c
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# Inhoudsfragmenten zonder kop Handleiding voor snel starten maken {#creating-content-fragments}

Leer hoe u AEM Content Fragments kunt gebruiken om pagina-onafhankelijke inhoud te ontwerpen, maken, beheren en gebruiken voor levering zonder kop.

## Wat zijn inhoudsfragmenten? {#what-are-content-fragments}

[ nu dat u een activa omslag ](create-assets-folder.md) hebt gecreeerd waar u uw Fragmenten van de Inhoud kunt opslaan, kunt u de fragmenten nu tot stand brengen!

Met inhoudsfragmenten kunt u pagina-onafhankelijke inhoud ontwerpen, maken, beheren en publiceren. Hiermee kunt u inhoud voorbereiden en deze op meerdere locaties en via meerdere kanalen gebruiken.

Inhoudsfragmenten bevatten gestructureerde inhoud en kunnen in JSON-indeling worden geleverd.

## Een inhoudsfragment maken {#how-to-create-a-content-fragment}

Inhoudsauteurs maken een willekeurig aantal Inhoudsfragmenten om de inhoud weer te geven die zij maken. Dit zal hun belangrijkste taak in AEM zijn. Met het oog op deze gids voor het op gang brengen van de werkzaamheden zullen we slechts één gids hoeven te maken.

1. Logboek in AEM en van het belangrijkste menu selecteert **Navigatie > Assets**.
1. Navigeer aan de [ omslag u eerder creeerde.](create-assets-folder.md)
1. Klik **creëren > het Fragment van de Inhoud**.
1. Het maken van een inhoudsfragment wordt in twee stappen weergegeven als een wizard. Selecteer eerst welk model u wenst om uw inhoudsfragment tot stand te brengen en **daarna** te klikken.
   * De beschikbare modellen hangen van de [**Configuratie van de Wolk** af u voor de activa omslag ](create-assets-folder.md) bepaalde waarin u het Fragment van de Inhoud creeert.
   * Als u het bericht `We could not find any models` ontvangt, controleert u de configuratie van de map Assets.

   ![ Uitgezochte Model van het Fragment van de Inhoud ](assets/content-fragment-model-select.png)
1. Verstrek a **Titel**, **Beschrijving**, en **Markeringen** zonodig en klik **creeer**.

   ![ creeer het Fragment van de Inhoud ](assets/content-fragment-create.png)
1. Klik **Open** in het bevestigingsvenster.

   ![ gecreeerd van het Fragment van de Inhoud bevestiging ](assets/content-fragment-confirmation.png)
1. Geef de details van het inhoudsfragment op in de Inhoudsfragmenteditor.

   ![ de Redacteur van het Fragment van de Inhoud ](assets/content-fragment-edit.png)
1. Klik **sparen** of **sparen en sluit**.

Inhoudsfragmenten kunnen verwijzen naar andere inhoudsfragmenten, waarbij zo nodig een geneste inhoudsstructuur mogelijk is.

Inhoudsfragmenten kunnen ook verwijzen naar andere elementen in AEM. [ Deze activa moeten in AEM ](/help/assets/manage-assets.md) worden opgeslagen alvorens een het van verwijzingen voorzien Fragment van de Inhoud te creëren.

## Volgende stappen {#next-steps}

Nu u een Fragment van de Inhoud hebt gecreeerd, kunt u zich op het definitieve deel van het begonnen worden gids bewegen en [ creeer API verzoeken om tot inhoudsfragmenten toegang te hebben en te leveren.](create-api-request.md)

>[!TIP]
>
>Voor volledige details over het beheren van de Fragmenten van de Inhoud, zie de [ documentatie van de Fragmenten van de Inhoud ](/help/assets/content-fragments/content-fragments.md)
