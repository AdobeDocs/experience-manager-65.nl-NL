---
title: JSON-export inschakelen voor een component
seo-title: Enabling JSON Export for a Component
description: Componenten kunnen worden aangepast om JSON-export van hun inhoud te genereren op basis van een modellerframework.
seo-description: Components can be adapted to generate JSON export of their content based on a modeler framework.
uuid: d7cc3347-2adb-4ea5-94a4-a847a2e66d28
contentOwner: User
content-type: reference
topic-tags: components
products: SG_EXPERIENCEMANAGER/6.5/SITES
discoiquuid: 448ad337-d4bb-4603-a27b-77da93feadbd
exl-id: 6d127e14-767e-46ad-aaeb-0ce9dd14d553
source-git-commit: b886844dc80482ae4aae5fc7ce09e466efecc3bd
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 0%

---

# JSON-export inschakelen voor een component{#enabling-json-export-for-a-component}

Componenten kunnen worden aangepast om JSON-export van hun inhoud te genereren op basis van een modellerframework.

## Overzicht {#overview}

De JSON-export is gebaseerd op [Verkoopmodellen](https://sling.apache.org/documentation/bundles/models.html)en de [Verkoopmodel exporteren](https://sling.apache.org/documentation/bundles/models.html#exporter-framework-since-130) kader (dat zelf op [Jackson-annotaties](https://github.com/FasterXML/jackson-annotations/wiki/Jackson-Annotations)).

Dit betekent dat de component een Sling Model moet hebben als het JSON moet uitvoeren. Daarom zult u deze twee stappen moeten volgen om de uitvoer van JSON op om het even welke component toe te laten.

* [Definieer een Sling-model voor de component](/help/sites-developing/json-exporter-components.md#define-a-sling-model-for-the-component)
* [Annoteer de interface van het Verkoopmodel](#annotate-the-sling-model-interface)

## Definieer een Sling-model voor de component {#define-a-sling-model-for-the-component}

Eerst moet een Sling Model voor de component worden bepaald.

>[!NOTE]
>
>Zie het artikel voor een voorbeeld van het gebruik van Sling Models [Exporteurs van verkoopmodellen ontwikkelen in AEM](https://helpx.adobe.com/experience-manager/kt/platform-repository/using/sling-model-exporter-tutorial-develop.html).

De implementatieklasse Sling Model moet met het volgende worden geannoteerd:

```java
@Model(... adapters = {..., ComponentExporter.class})
@Exporter(name = ExporterConstants.SLING_MODEL_EXPORTER_NAME, extensions = ExporterConstants.SLING_MODEL_EXTENSION)
@JsonSerialize(as = MyComponent.class)
```

Zo weet u zeker dat uw component zelfstandig kan worden geëxporteerd met de opdracht `.model` en de `.json` extensie.

Daarnaast wordt hiermee aangegeven dat de klasse Sling Model kan worden aangepast aan de `ComponentExporter` interface.

>[!NOTE]
>
>Jackson-annotaties worden gewoonlijk niet opgegeven op het klasseniveau Sling Model, maar wel op het interfaceniveau Model. Hiermee zorgt u ervoor dat de JSON-export wordt beschouwd als onderdeel van de API voor componenten.

>[!NOTE]
>
>De `ExporterConstants` en `ComponentExporter` klassen komen uit `com.adobe.cq.export.json` bundel.

### Meerdere kiezers gebruiken {#multiple-selectors}

Hoewel het geen standaard gebruikscase is, is het mogelijk om veelvoudige selecteurs naast te vormen `model` kiezer.

```
https://<server>:<port>/content/page.model.selector1.selector2.json
```

In dat geval echter `model` selector moet de eerste kiezer zijn en de extensie moet `.json`.

## De interface van het verkoopmodel notities aanbrengen {#annotate-the-sling-model-interface}

Om door het JSON Exporter-kader in aanmerking te worden genomen, moet de modelinterface de `ComponentExporter` interface (of `ContainerExporter`, in het geval van een containercomponent).

De overeenkomstige interface van het Model van de Verkoop ( `MyComponent`) wordt vervolgens geannoteerd met [Jackson-annotaties](https://github.com/FasterXML/jackson-annotations/wiki/Jackson-Annotations) om te bepalen hoe het (geserialiseerd) zou moeten worden uitgevoerd.

De modelinterface moet behoorlijk worden geannoteerd om te bepalen welke methodes zouden moeten in series worden vervaardigd. Standaard worden alle methoden die de gebruikelijke naamgevingsconventie voor getters respecteren, geserialiseerd en worden hun JSON-eigenschapnamen op natuurlijke wijze afgeleid van de namen van getters. Dit kan worden voorkomen of overschreven door `@JsonIgnore` of `@JsonProperty` om de naam van de JSON-eigenschap te wijzigen.

## Voorbeeld {#example}

De Core Components hebben JSON-export ondersteund sinds de release [1.1.0 van de kerncomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) en kan als referentie worden gebruikt.

Een voorbeeld vindt u in de implementatie Sling Model van de Image Core-component en de bijbehorende geannoteerde interface.

CODE VOOR GITHUB

U kunt de code van deze pagina op GitHub vinden

* [Open aem-core-wcm-componentenproject op GitHub](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components)
* Het project downloaden als [een ZIP-bestand](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/archive/master.zip)

## Verwante documentatie {#related-documentation}

Zie voor meer informatie:

* De [Het onderwerp Inhoudsfragmenten in de gebruikershandleiding voor middelen](https://helpx.adobe.com/experience-manager/6-4/assets/user-guide.html?topic=/experience-manager/6-4/assets/morehelp/content-fragments.ug.js)

* [Modellen van contentfragmenten](/help/assets/content-fragments/content-fragments-models.md)
* [Ontwerpen met inhoudsfragmenten](/help/sites-authoring/content-fragments.md)
* [JSON-exportfunctie voor services voor inhoud](/help/sites-developing/json-exporter.md)
* [Kernonderdelen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) en de [Component Inhoudsfragment](https://helpx.adobe.com/experience-manager/core-components/using/content-fragment-component.html)
