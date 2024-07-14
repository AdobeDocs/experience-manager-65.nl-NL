---
title: JSON-exportfunctie voor services voor inhoud
description: AEM Content Services zijn ontworpen om de beschrijving en levering van inhoud in of vanuit AEM te veralgemenen, waarbij de aandacht niet op webpagina's wordt gevestigd. Zij verstrekken de levering van inhoud aan kanalen die niet traditionele AEM Web-pagina's zijn, gebruikend gestandaardiseerde methodes die door om het even welke cliënt kunnen worden gebruikt.
contentOwner: User
content-type: reference
topic-tags: components
products: SG_EXPERIENCEMANAGER/6.5/SITES
exl-id: 647395c0-f392-427d-a998-e9ddf722b9f9
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# JSON-exportfunctie voor services voor inhoud{#json-exporter-for-content-services}

AEM Content Services zijn ontworpen om de beschrijving en levering van inhoud in of vanuit AEM te veralgemenen, waarbij de aandacht niet op webpagina&#39;s wordt gevestigd.

Zij verstrekken de levering van inhoud aan kanalen die niet traditionele AEM Web-pagina&#39;s zijn, gebruikend gestandaardiseerde methodes die door om het even welke cliënt kunnen worden gebruikt. Deze kanalen kunnen zijn:

* [Toepassingen voor één pagina](spa-walkthrough.md)
* Systeemeigen mobiele toepassingen
* andere kanalen en aanraakpunten buiten AEM

Met inhoudsfragmenten die gestructureerde inhoud gebruiken, kunt u de inhoudsdiensten verlenen door de exporteur te gebruiken JSON om de inhoud van om het even welke AEM pagina in het formaat van het JSON gegevensmodel te leveren. Deze methode kan vervolgens door uw eigen toepassingen worden gebruikt.

>[!NOTE]
>
>De hier beschreven functionaliteit is beschikbaar voor alle Componenten van de Kern sinds [ versie 1.1.0 van de Componenten van de Kern ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html).

## JSON-exportfunctie met kerncomponenten van inhoudsfragment {#json-exporter-with-content-fragment-core-components}

Met de AEM JSON-exportfunctie kunt u de inhoud van elke AEM pagina leveren in de indeling van het JSON-gegevensmodel. Deze methode kan vervolgens door uw eigen toepassingen worden gebruikt.

Binnen AEM wordt de levering bereikt met de extensie selector `model` en `.json` .

`.model.json`

1. Bijvoorbeeld een URL zoals:

   ```shell
   http://localhost:4502/content/we-retail/language-masters/en.model.json
   ```

1. Levert inhoud zoals:

   ![ chlimage_1-192 ](assets/chlimage_1-192.png)

U kunt de inhoud van een gestructureerd inhoudsfragment ook leveren door dit specifiek te activeren.

Gebruik het volledige pad naar het fragment (als `jcr:content` ), bijvoorbeeld met een achtervoegsel zoals.

`.../jcr:content/root/responsivegrid/contentfragment.model.json`

De pagina kan één inhoudsfragment of meerdere componenten van verschillende typen bevatten. U kunt mechanismen zoals lijstcomponenten ook gebruiken om automatisch naar relevante inhoud te zoeken.

* Bijvoorbeeld een URL zoals:

  ```shell
  http://localhost:4502/content/we-retail/language-masters/en/manchester-airport/jcr:content/root/responsivegrid/contentfragment.model.json
  ```

* Levert inhoud zoals:

  ![ chlimage_1-193 ](assets/chlimage_1-193.png)

  >[!NOTE]
  >
  >U kunt [ uw eigen componenten ](/help/sites-developing/json-exporter-components.md) aanpassen om tot dit gegeven toegang te hebben en te gebruiken.

  >[!NOTE]
  >
  >Hoewel niet een standaardimplementatie, [ veelvoudige selecteurs worden gesteund, ](json-exporter-components.md#multiple-selectors) maar `model` moet de eerste zijn.

### Aanvullende informatie {#further-information}

Zie ook:

* ASSETS HTTP API

   * [ASSETS HTTP API](/help/assets/mac-api-assets.md)

* Modellen voor verkopen:

   * [ het Verdelen Modellen - het associëren van een modelklasse met een middeltype sinds 130 ](https://sling.apache.org/documentation/bundles/models.html#associating-a-model-class-with-a-resource-type-since-130)

* AEM met JSON:

   * [Pagina-informatie ophalen in JSON-indeling](/help/sites-developing/pageinfo.md)

## Verwante documentatie {#related-documentation}

Zie voor meer informatie:

* Het [ onderwerp van de Fragmenten van de Inhoud in de gebruikersgids van Assets ](/help/assets/content-fragments/content-fragments.md)

* [Modellen van inhoudsfragmenten](/help/assets/content-fragments/content-fragments-models.md)
* [Ontwerpen met inhoudsfragmenten](/help/sites-authoring/content-fragments.md)
* [JSON-export inschakelen voor een component](/help/sites-developing/json-exporter-components.md)

* [ Componenten van de Kern ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) en de [ component van het Fragment van de Inhoud ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/content-fragment-component.html)
