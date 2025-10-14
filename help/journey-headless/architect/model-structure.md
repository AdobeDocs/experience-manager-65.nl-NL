---
title: Meer informatie over het maken van modellen voor inhoudsfragmenten in AEM
description: Leer over de concepten en de mechanica van het modelleren van inhoud voor uw Zwaarloze CMS gebruikend de Modellen van de Fragments van de Inhoud.
exl-id: b377e01f-e392-4ef5-a259-73ce9ff941d0
solution: Experience Manager, Experience Manager Sites
feature: Headless,Content Fragments
role: Admin, Architect,Data Architect
source-git-commit: 9a3008553b8091b66c72e0b6c317573b235eee24
workflow-type: tm+mt
source-wordcount: '690'
ht-degree: 0%

---

# Meer informatie over het maken van modellen voor inhoudsfragmenten in AEM {#architect-headless-content-fragment-models}

## Het artikel tot nu toe {#story-so-far}

Aan het begin van de [&#x200B; Reis van de Schrijver van de Inhoud de Zwaarloze &#x200B;](overview.md) de [&#x200B; Basisprincipes van de Modellering van de Inhoud voor Zwaartepunt met AEM &#x200B;](basics.md) behandelde de basisconcepten en de terminologie relevant voor creatie voor hoofd.

Dit artikel bouwt op deze voort zodat begrijpt u hoe te om uw eigen Modellen van het Fragment van de Inhoud voor uw project zonder AEM te creëren.

## Doelstelling {#objective}

* **Publiek**: Begin
* **Doelstelling**: de concepten en de mechanica van het modelleren van inhoud voor uw Zwaarloze CMS gebruikend de Modellen van de Fragmenten van de Inhoud.

<!-- which persona does this? -->
<!-- and who allows the configuration on the folders? -->

<!--
## Enabling Content Fragment Models {#enabling-content-fragment-models}

At the very start you need to enable Content Fragment Models for your site, this is done in the Configuration Browser; under Tools > General > Configuration Browser. You can either select to configure the global entry, or create a configuration. For example:

![Define configuration](/help/assets/content-fragments/assets/cfm-conf-01.png)

>[!NOTE]
>
>See Additional Resources - Content Fragments in the Configuration Browser
-->

## Modellen voor inhoudsfragmenten maken {#creating-content-fragment-models}

Vervolgens kunt u de modellen van Content Fragments maken en de structuur definiëren. U doet dit onder Gereedschappen > Assets > Modellen van inhoudsfragmenten.

![&#x200B; Modellen van het Fragment van de Inhoud in Hulpmiddelen &#x200B;](assets/cfm-tools.png)

Na het selecteren van dit navigeert u aan de plaats voor uw model en selecteert **creeert**. Hier kunt u verschillende belangrijke details invoeren.

De optie **laat model** toe wordt geactiveerd door gebrek. Dit betekent dat uw model beschikbaar is voor gebruik (bij het maken van inhoudsfragmenten) zodra u het hebt opgeslagen. U kunt dit desgewenst deactiveren. Er zijn later mogelijkheden om een bestaand model in of uit te schakelen.

![&#x200B; creeer het Model van het Fragment van de Inhoud &#x200B;](/help/assets/content-fragments/assets/cfm-models-02.png)

Bevestig met **creeer** en u kunt **dan** uw model openen &lbrace;beginnen de structuur te bepalen.

## Modellen voor inhoudsfragmenten definiëren {#defining-content-fragment-models}

Wanneer u eerst een nieuw model opent u zult zien - een grote lege ruimte aan de linkerzijde, en een lange lijst van **Types van Gegevens** bij het recht:

![&#x200B; Leeg Model &#x200B;](/help/assets/content-fragments/assets/cfm-models-03.png)

Wat moet er gebeuren?

U kunt instanties van de **Types van Gegevens** op de linkerruimte slepen - u bepaalt reeds uw model!

![&#x200B; die gebieden &#x200B;](/help/assets/content-fragments/assets/cfm-models-04.png) bepalen

Zodra u een gegevenstype toevoegt zult u worden vereist om **Eigenschappen** voor dat gebied te bepalen. Deze hangen van het type af dat wordt gebruikt. Bijvoorbeeld:

![&#x200B; Eigenschappen van Gegevens &#x200B;](/help/assets/content-fragments/assets/cfm-models-05.png)

U kunt zoveel velden toevoegen als u nodig hebt. Bijvoorbeeld:

![&#x200B; Model van het Fragment van de Inhoud &#x200B;](/help/assets/content-fragments/assets/cfm-models-07.png)

### Uw makers van inhoud {#your-content-authors}

De auteurs van de inhoud zien de gegevenstypen en eigenschappen die u hebt gebruikt om uw modellen te maken, niet. Dit betekent dat u mogelijk hulp en informatie moet bieden over de manier waarop specifieke velden worden ingevuld. Voor basisinformatie kunt u het Etiket van het Gebied en StandaardWaarde gebruiken, maar de complexere gevallen zouden de projectspecifieke documentatie kunnen moeten worden overwogen.

>[!NOTE]
>
>Zie Aanvullende bronnen - Modellen van inhoudsfragmenten.

## Modellen voor inhoudsfragmenten beheren {#managing-content-fragment-models}

<!-- needs more details -->

Het beheren van uw modellen van het Fragment van de Inhoud impliceert:

* Het toelaten (of het onbruikbaar maken) hen - dit maakt hen voor auteurs beschikbaar wanneer het creëren van de Fragmenten van de Inhoud.
* Verwijderen - verwijdering is altijd nodig, maar u moet er rekening mee houden dat u een model verwijdert dat al wordt gebruikt voor inhoudsfragmenten, met name fragmenten die al zijn gepubliceerd.

## Publiceren {#publishing}

<!-- needs more details -->

Inhoudsfragmentmodellen moeten worden gepubliceerd wanneer/voordat afhankelijke inhoudsfragmenten worden gepubliceerd.

>[!NOTE]
>
>Als een auteur een inhoudsfragment probeert te publiceren waarvoor het model nog niet is gepubliceerd, zal een selectielijst dit vermelden en het model zal met het fragment worden gepubliceerd.

Zodra een model wordt gepubliceerd is het *gesloten* in een LEZEN-ONLY wijze op auteur. Dit is bedoeld om wijzigingen te voorkomen die zouden leiden tot fouten in bestaande GraphQL-schema&#39;s en query&#39;s, met name in de publicatieomgeving. Het wordt vermeld in de console door **Vergrendelde**.

Wanneer het model **&#x200B;**&#x200B;(op LEZEN-ONLY wijze) wordt gesloten, kunt u de inhoud en de structuur van modellen zien maar u kunt hen niet direct uitgeven; hoewel u **Vergrendelde** modellen van of de console, of de modelredacteur kunt beheren.

## Volgende functies {#whats-next}

Nu u de grondbeginselen hebt geleerd, is de volgende stap het creëren van uw eigen Modellen van het Fragment van de Inhoud te beginnen.

## Aanvullende bronnen {#additional-resources}

* [Concepten ontwerpen](/help/sites-authoring/author.md)

* [&#x200B; Basis Behandelend &#x200B;](/help/sites-authoring/basic-handling.md) - deze pagina is hoofdzakelijk gebaseerd op de **console van Plaatsen**, maar vele/meeste eigenschappen zijn ook relevant voor het navigeren aan, en het nemen van actie op, **Modellen van het Fragment van de Inhoud** onder de **Assets** console.

* [Werken met inhoudsfragmenten](/help/assets/content-fragments/content-fragments.md)

   * [Modellen van inhoudsfragmenten](/help/assets/content-fragments/content-fragments-models.md)

      * [Het model van het inhoudsfragment definiëren](/help/assets/content-fragments/content-fragments-models.md#defining-your-content-fragment-model)

      * [Een inhoudsfragmentmodel in- of uitschakelen](/help/assets/content-fragments/content-fragments-models.md#enabling-disabling-a-content-fragment-model)

      * [Modellen voor inhoudsfragmenten toestaan in uw Assets-map](/help/assets/content-fragments/content-fragments-models.md#allowing-content-fragment-models-assets-folder)

      * [Een inhoudsfragmentmodel verwijderen](/help/assets/content-fragments/content-fragments-models.md#deleting-a-content-fragment-model)

      * [Een inhoudsfragmentmodel publiceren](/help/assets/content-fragments/content-fragments-models.md#publishing-a-content-fragment-model)

      * [Publicatie van een inhoudsfragmentmodel ongedaan maken](/help/assets/content-fragments/content-fragments-models.md#unpublishing-a-content-fragment-model)

      * [Vergrendelde (gepubliceerde) modellen van inhoudsfragmenten](/help/assets/content-fragments/content-fragments-models.md#locked-published-content-fragment-models)

* Aan de slag - hulplijnen

   * [Modellen voor inhoudsfragmenten maken, headless Quick Start Guide](/help/sites-developing/headless/getting-started/create-content-model.md)
