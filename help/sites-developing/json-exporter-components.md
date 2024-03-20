---
title: JSON-export inschakelen voor een component
description: Componenten kunnen worden aangepast om JSON-export van hun inhoud te genereren op basis van een modellerframework.
contentOwner: User
content-type: reference
topic-tags: components
products: SG_EXPERIENCEMANAGER/6.5/SITES
exl-id: 6d127e14-767e-46ad-aaeb-0ce9dd14d553
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---

# JSON-export inschakelen voor een component{#enabling-json-export-for-a-component}

Componenten kunnen worden aangepast om JSON-export van hun inhoud te genereren op basis van een modellerframework.

## Overzicht {#overview}

De JSON-export is gebaseerd op [Verkoopmodellen](https://sling.apache.org/documentation/bundles/models.html)en de [Verkoopmodel exporteren](https://sling.apache.org/documentation/bundles/models.html#exporter-framework-since-130) kader (dat zelf op [Jackson-annotaties](https://github.com/FasterXML/jackson-annotations/wiki/Jackson-Annotations)).

Dit betekent dat de component een Sling Model moet hebben als het JSON moet uitvoeren. Voer daarom de volgende twee stappen uit om JSON-export voor een willekeurige component mogelijk te maken.

* [Definieer een verkoopmodel voor de component](/help/sites-developing/json-exporter-components.md#define-a-sling-model-for-the-component)
* [Annoteer de interface van het Verkoopmodel](#annotate-the-sling-model-interface)

## Definieer een verkoopmodel voor de component {#define-a-sling-model-for-the-component}

Eerst moet een Sling Model voor de component worden bepaald.

>[!NOTE]
>
>Voor een voorbeeld van het gebruiken van het Verdelen Modellen, zie [Exporteurs van verkoopmodellen ontwikkelen in AEM](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/development/develop-sling-model-exporter.html).

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
>Jackson-annotaties worden niet opgegeven op het klasseniveau Sling Model, maar wel op het interfaceniveau Model. Hiermee zorgt u ervoor dat de JSON-export wordt beschouwd als onderdeel van de API voor componenten.

>[!NOTE]
>
>De `ExporterConstants` en `ComponentExporter` klassen komen uit `com.adobe.cq.export.json` bundel.

### Meerdere kiezers gebruiken {#multiple-selectors}

Hoewel het geen standaard gebruikscase is, is het mogelijk om veelvoudige selecteurs naast te vormen `model` kiezer.

```
https://<server>:<port>/content/page.model.selector1.selector2.json
```

In dat geval echter `model` moet de eerste kiezer zijn en de extensie moet `.json`.

## De interface van het verkoopmodel notities aanbrengen {#annotate-the-sling-model-interface}

Om door het JSON Exporter-kader in aanmerking te worden genomen, moet de modelinterface de `ComponentExporter` interface (of `ContainerExporter`, als er een containercomponent is).

De overeenkomstige interface van het Model van de Verkoop ( `MyComponent`) wordt vervolgens met behulp van [Jackson-annotaties](https://github.com/FasterXML/jackson-annotations/wiki/Jackson-Annotations) om te bepalen hoe het (geserialiseerd) zou moeten worden uitgevoerd.

De modelinterface moet behoorlijk worden geannoteerd om te bepalen welke methodes zouden moeten in series worden vervaardigd. Standaard worden alle methoden die de gebruikelijke naamgevingsconventie voor getters respecteren, geserialiseerd en worden hun JSON-eigenschapnamen op natuurlijke wijze afgeleid van de namen van getter. Dit kan worden voorkomen of overschreven door `@JsonIgnore` of `@JsonProperty` om de naam van de JSON-eigenschap te wijzigen.

## Voorbeeld {#example}

De Core Components hebben JSON-export ondersteund sinds de release [1.1.0 van de kerncomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) en kan als referentie worden gebruikt.

Een voorbeeld vindt u in de implementatie Sling Model van de Image Core-component en de bijbehorende geannoteerde interface.

CODE VOOR GITHUB

U kunt de code van deze pagina op GitHub vinden

* [Open aem-core-wcm-componentenproject op GitHub](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components)
* Het project downloaden als [een ZIP-bestand](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/archive/master.zip)

## Verwante documentatie {#related-documentation}

Raadpleeg de volgende secties voor meer informatie:

* De [Het onderwerp Inhoudsfragmenten in de gebruikershandleiding voor middelen](https://helpx.adobe.com/experience-manager/6-4/assets/user-guide.html?topic=/experience-manager/6-4/assets/morehelp/content-fragments.ug.js)

* [Modellen van inhoudsfragmenten](/help/assets/content-fragments/content-fragments-models.md)
* [Ontwerpen met inhoudsfragmenten](/help/sites-authoring/content-fragments.md)
* [JSON-exportfunctie voor services voor inhoud](/help/sites-developing/json-exporter.md)
* [Kernonderdelen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) en de [Component Inhoudsfragment](https://helpx.adobe.com/experience-manager/core-components/using/content-fragment-component.html)
