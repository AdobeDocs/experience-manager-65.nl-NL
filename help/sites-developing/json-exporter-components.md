---
title: JSON-export inschakelen voor een component
seo-title: JSON-export inschakelen voor een component
description: Componenten kunnen worden aangepast om JSON-export van hun inhoud te genereren op basis van een modellerframework.
seo-description: Componenten kunnen worden aangepast om JSON-export van hun inhoud te genereren op basis van een modellerframework.
uuid: d7cc3347-2adb-4ea5-94a4-a847a2e66d28
contentOwner: User
content-type: reference
topic-tags: components
products: SG_EXPERIENCEMANAGER/6.5/SITES
discoiquuid: 448ad337-d4bb-4603-a27b-77da93feadbd
translation-type: tm+mt
source-git-commit: 10072609bc371b5f2dce425e90e583f14f96e371
workflow-type: tm+mt
source-wordcount: '562'
ht-degree: 3%

---


# JSON-export inschakelen voor een component{#enabling-json-export-for-a-component}

Componenten kunnen worden aangepast om JSON-export van hun inhoud te genereren op basis van een modellerframework.

## Overzicht {#overview}

De JSON-export is gebaseerd op [verkoopmodellen](https://sling.apache.org/documentation/bundles/models.html)en op het [verkoopmodel van de exporteur](https://sling.apache.org/documentation/bundles/models.html#exporter-framework-since-130) (dat zelf op [Jackson-annotaties](https://github.com/FasterXML/jackson-annotations/wiki/Jackson-Annotations)berust).

Dit betekent dat de component een Sling Model moet hebben als het JSON moet uitvoeren. Daarom zult u deze twee stappen moeten volgen om de uitvoer van JSON op om het even welke component toe te laten.

* [Definieer een Sling-model voor de component](/help/sites-developing/json-exporter-components.md#define-a-sling-model-for-the-component)
* [Annoteer de interface van het Verkoopmodel](#annotate-the-sling-model-interface)

## Definieer een Sling-model voor de component {#define-a-sling-model-for-the-component}

Eerst moet een Sling Model voor de component worden bepaald.

>[!NOTE]
>
>Zie het artikel [Developing Sling Model Exporters in AEM](https://helpx.adobe.com/experience-manager/kt/platform-repository/using/sling-model-exporter-tutorial-develop.html)voor een voorbeeld van het gebruik van Sling Models.

De implementatieklasse Sling Model moet met het volgende worden geannoteerd:

```java
@Model(... adapters = {..., ComponentExporter.class})
@Exporter(name = ExporterConstants.SLING_MODEL_EXPORTER_NAME, extensions = ExporterConstants.SLING_MODEL_EXTENSION)
@JsonSerialize(as = MyComponent.class)
```

Zo weet u zeker dat de component zelfstandig kan worden geëxporteerd met de `.model` kiezer en de `.json` extensie.

Daarnaast wordt hiermee aangegeven dat de klasse Sling Model kan worden aangepast in de `ComponentExporter` interface.

>[!NOTE]
>
>Jackson-annotaties worden gewoonlijk niet opgegeven op het klasseniveau Sling Model, maar wel op het interfaceniveau Model. Hiermee zorgt u ervoor dat de JSON-export wordt beschouwd als onderdeel van de API voor componenten.

>[!NOTE]
>
>De `ExporterConstants` klassen en `ComponentExporter` klassen komen uit de `com.adobe.cq.export.json` bundel.

### Meerdere kiezers gebruiken {#multiple-selectors}

Hoewel het geen standaard gebruikscase is, is het mogelijk om veelvoudige selecteurs naast de `model` selecteur te vormen.

```
https://<server>:<port>/content/page.model.selector1.selector2.json
```

In dat geval moet de `model` kiezer echter de eerste kiezer zijn en moet de extensie `.json`.

## De interface van het verkoopmodel notities aanbrengen {#annotate-the-sling-model-interface}

Om door het kader van de Exporteur van JSON in aanmerking te worden genomen, zou de modelinterface de `ComponentExporter` interface (of `ContainerExporter`, in het geval van een containercomponent) moeten uitvoeren.

De overeenkomstige interface van het Schilmodel ( `MyComponent`) zou dan geannoteerd gebruikend [Jackson annotaties](https://github.com/FasterXML/jackson-annotations/wiki/Jackson-Annotations) worden om te bepalen hoe het (geserialiseerd) zou moeten worden uitgevoerd.

De modelinterface moet behoorlijk worden geannoteerd om te bepalen welke methodes zouden moeten in series worden vervaardigd. Standaard worden alle methoden die de gebruikelijke naamgevingsconventie voor getters respecteren, geserialiseerd en worden hun JSON-eigenschapnamen op natuurlijke wijze afgeleid van de namen van getter. Dit kan worden voorkomen of genegeerd door de naam van de JSON-eigenschap te wijzigen `@JsonIgnore` of `@JsonProperty` .

## Voorbeeld {#example}

De kerncomponenten hebben JSON-export ondersteund sinds release [1.1.0 van de kerncomponenten](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/introduction.html) en kunnen als referentie worden gebruikt.

Een voorbeeld vindt u in de implementatie Sling Model van de Image Core-component en de bijbehorende geannoteerde interface.

CODE VOOR GITHUB

U kunt de code van deze pagina op GitHub vinden

* [Open aem-core-wcm-componentenproject op GitHub](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components)
* Het project downloaden als [ZIP-bestand](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/archive/master.zip)

## Related Documentation {#related-documentation}

Zie voor meer informatie:

* Het onderwerp [Inhoudsfragmenten in de gebruikershandleiding voor middelen](https://helpx.adobe.com/experience-manager/6-4/assets/user-guide.html?topic=/experience-manager/6-4/assets/morehelp/content-fragments.ug.js)

* [Modellen van contentfragmenten](/help/assets/content-fragments-models.md)
* [Ontwerpen met inhoudsfragmenten](/help/sites-authoring/content-fragments.md)
* [JSON-exportfunctie voor services voor inhoud](/help/sites-developing/json-exporter.md)
* [Kerncomponenten](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/introduction.html) en de component [Inhoudsfragment](https://helpx.adobe.com/experience-manager/core-components/using/content-fragment-component.html)

