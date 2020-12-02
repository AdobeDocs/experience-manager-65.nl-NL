---
title: JSON-exportfunctie voor services voor inhoud
seo-title: JSON-exportfunctie voor services voor inhoud
description: AEM Content Services zijn ontworpen om de beschrijving en levering van inhoud in of vanuit AEM te veralgemenen, waarbij de aandacht niet op webpagina's wordt gevestigd. Zij verstrekken de levering van inhoud aan kanalen die niet traditionele AEM Web-pagina's zijn, gebruikend gestandaardiseerde methodes die door om het even welke cliënt kunnen worden verbruikt.
seo-description: AEM Content Services zijn ontworpen om de beschrijving en levering van inhoud in of vanuit AEM te veralgemenen, waarbij de aandacht niet op webpagina's wordt gevestigd. Zij verstrekken de levering van inhoud aan kanalen die niet traditionele AEM Web-pagina's zijn, gebruikend gestandaardiseerde methodes die door om het even welke cliënt kunnen worden verbruikt.
uuid: be6457b1-fa9c-4f3b-b219-01a4afc239e7
contentOwner: User
content-type: reference
topic-tags: components
products: SG_EXPERIENCEMANAGER/6.5/SITES
discoiquuid: 4c7e33ea-f2d3-4d69-b676-aeb50c610d70
translation-type: tm+mt
source-git-commit: a430c4de89bde3b907d342106465d3b5a7c75cc8
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 3%

---


# JSON Exporter voor Content Services{#json-exporter-for-content-services}

AEM Content Services zijn ontworpen om de beschrijving en levering van inhoud in of vanuit AEM te veralgemenen, waarbij de aandacht niet op webpagina&#39;s wordt gevestigd.

Zij verstrekken de levering van inhoud aan kanalen die niet traditionele AEM Web-pagina&#39;s zijn, gebruikend gestandaardiseerde methodes die door om het even welke cliënt kunnen worden verbruikt. Deze kanalen kunnen zijn:

* [Toepassingen voor één pagina](spa-walkthrough.md)
* Systeemeigen mobiele toepassingen
* andere kanalen en aanraakpunten buiten AEM

Met inhoudsfragmenten die gestructureerde inhoud gebruiken, kunt u de inhoudsdiensten verlenen door JSON-exporter te gebruiken om de inhoud van een (y) AEM pagina in het formaat van het JSON-gegevensmodel te leveren. Dit kan dan door uw eigen toepassingen worden verbruikt.

>[!NOTE]
>
>De hier beschreven functionaliteit is beschikbaar voor alle Core Components sinds [release 1.1.0 van de Core Components](https://docs.adobe.com/content/docs/en/core-components/v1.html).

## JSON-exportfunctie met kerncomponenten van inhoudsfragment {#json-exporter-with-content-fragment-core-components}

Met de AEM JSON-exportfunctie kunt u de inhoud van een (y) AEM pagina in de indeling van het JSON-gegevensmodel leveren. Dit kan dan door uw eigen toepassingen worden verbruikt.

Binnen AEM wordt de levering bereikt gebruikend de selecteur `model` en `.json` uitbreiding.

`.model.json`

1. Bijvoorbeeld een URL zoals:

   ```shell
   http://localhost:4502/content/we-retail/language-masters/en.model.json
   ```

1. Zal inhoud leveren zoals:

   ![chlimage_1-112](assets/chlimage_1-192.png)

U kunt de inhoud van een gestructureerd inhoudsfragment ook leveren door dit specifiek te activeren.

Dit wordt gedaan gebruikend de volledige weg aan het fragment (via `jcr:content`); bijvoorbeeld met een achtervoegsel zoals

`.../jcr:content/root/responsivegrid/contentfragment.model.json`

De pagina kan één inhoudsfragment of meerdere componenten van verschillende typen bevatten. U kunt mechanismen zoals lijstcomponenten ook gebruiken om automatisch naar relevante inhoud te zoeken.

* Bijvoorbeeld een URL zoals:

   ```shell
   http://localhost:4502/content/we-retail/language-masters/en/manchester-airport/jcr:content/root/responsivegrid/contentfragment.model.json
   ```

* Zal inhoud leveren zoals:

   ![chlimage_1-193](assets/chlimage_1-193.png)

   >[!NOTE]
   >
   >U kunt [uw eigen componenten ](/help/sites-developing/json-exporter-components.md) aanpassen om tot deze gegevens toegang te hebben en te gebruiken.

   >[!NOTE]
   >
   >Hoewel geen standaardimplementatie, [worden de veelvoudige selecteurs gesteund, ](json-exporter-components.md#multiple-selectors) maar `model` moet de eerste zijn.

### Aanvullende informatie {#further-information}

Zie ook:

* HTTP-API voor assets

   * [HTTP-API voor assets](/help/assets/mac-api-assets.md)

* Modellen voor verkopen:

   * [Sling Models - het associëren van een modelklasse met een middeltype sinds 130](https://sling.apache.org/documentation/bundles/models.html#associating-a-model-class-with-a-resource-type-since-130)

* AEM met JSON:

   * [Pagina-informatie ophalen in JSON-indeling](/help/sites-developing/pageinfo.md)

## Verwante documentatie {#related-documentation}

Zie voor meer informatie:

* Het onderwerp [Inhoudsfragmenten in de gebruikershandleiding voor middelen](https://helpx.adobe.com/experience-manager/6-4/assets/user-guide.html?topic=/experience-manager/6-4/assets/morehelp/content-fragments.ug.js)

* [Modellen van contentfragmenten](/help/assets/content-fragments/content-fragments-models.md)
* [Ontwerpen met inhoudsfragmenten](/help/sites-authoring/content-fragments.md)
* [JSON-export inschakelen voor een component](/help/sites-developing/json-exporter-components.md)

* [De ](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/introduction.html) Componenten van de kern en de component van het Fragment van de  [Inhoud](https://helpx.adobe.com/experience-manager/core-components/using/content-fragment-component.html)

