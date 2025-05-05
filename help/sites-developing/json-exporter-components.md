---
title: JSON-export inschakelen voor een component
description: Componenten kunnen worden aangepast om JSON-export van hun inhoud te genereren op basis van een modellerframework.
contentOwner: User
content-type: reference
topic-tags: components
products: SG_EXPERIENCEMANAGER/6.5/SITES
exl-id: 6d127e14-767e-46ad-aaeb-0ce9dd14d553
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---

# JSON-export inschakelen voor een component{#enabling-json-export-for-a-component}

Componenten kunnen worden aangepast om JSON-export van hun inhoud te genereren op basis van een modellerframework.

## Overzicht {#overview}

De uitvoer JSON is gebaseerd op [ het Verdelen Modellen ](https://sling.apache.org/documentation/bundles/models.html), en op het [ Verschuiven ModelExporter ](https://sling.apache.org/documentation/bundles/models.html#exporter-framework-since-130) kader (dat zelf op [ Jackson annotations ](https://github.com/FasterXML/jackson-annotations/wiki/Jackson-Annotations) vertrouwt).

Dit betekent dat de component een Sling Model moet hebben als het JSON moet uitvoeren. Voer daarom de volgende twee stappen uit om JSON-export voor een willekeurige component mogelijk te maken.

* [Definieer een verkoopmodel voor de component](/help/sites-developing/json-exporter-components.md#define-a-sling-model-for-the-component)
* [Annoteer de interface van het Verkoopmodel](#annotate-the-sling-model-interface)

## Definieer een verkoopmodel voor de component {#define-a-sling-model-for-the-component}

Eerst moet een Sling Model voor de component worden bepaald.

>[!NOTE]
>
>Voor een voorbeeld om het Verdelen Modellen te gebruiken, zie [ het Ontwikkelen van het Verdelen ModelExporters in AEM ](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/development/develop-sling-model-exporter.html?lang=nl-NL).

De implementatieklasse Sling Model moet met het volgende worden geannoteerd:

```java
@Model(... adapters = {..., ComponentExporter.class})
@Exporter(name = ExporterConstants.SLING_MODEL_EXPORTER_NAME, extensions = ExporterConstants.SLING_MODEL_EXTENSION)
@JsonSerialize(as = MyComponent.class)
```

Dit zorgt ervoor dat uw component zelfstandig kan worden geëxporteerd met de extensie `.model` selector en `.json` .

Daarnaast geeft dit op dat de klasse Sling Model kan worden aangepast in de interface `ComponentExporter` .

>[!NOTE]
>
>Jackson-annotaties worden niet opgegeven op het klasseniveau Sling Model, maar wel op het interfaceniveau Model. Hiermee zorgt u ervoor dat de JSON-export wordt beschouwd als onderdeel van de API voor componenten.

>[!NOTE]
>
>De klassen `ExporterConstants` en `ComponentExporter` zijn afkomstig uit de `com.adobe.cq.export.json` -bundel.

### Meerdere kiezers gebruiken {#multiple-selectors}

Hoewel het geen standaard gebruikscase is, is het mogelijk om meerdere kiezers te configureren naast de kiezer van `model` .

```
https://<server>:<port>/content/page.model.selector1.selector2.json
```

In een dergelijk geval moet de `model` kiezer echter de eerste kiezer zijn en moet de extensie `.json` zijn.

## De interface van het verkoopmodel notities aanbrengen {#annotate-the-sling-model-interface}

Om door het kader van de Exporter van JSON in aanmerking te worden genomen, zou de Model interface `ComponentExporter` interface (of `ContainerExporter`, als er een containercomponent is) moeten uitvoeren.

De overeenkomstige het Verdelen Model interface ( `MyComponent`) zou dan worden geannoteerd gebruikend [ de annotaties van Jackson ](https://github.com/FasterXML/jackson-annotations/wiki/Jackson-Annotations) om te bepalen hoe het (geserialiseerd) zou moeten worden uitgevoerd.

De modelinterface moet behoorlijk worden geannoteerd om te bepalen welke methodes zouden moeten in series worden vervaardigd. Standaard worden alle methoden die de gebruikelijke naamgevingsconventie voor getters respecteren, geserialiseerd en worden hun JSON-eigenschapnamen op natuurlijke wijze afgeleid van de namen van getter. Dit kan worden voorkomen of genegeerd door `@JsonIgnore` of `@JsonProperty` te gebruiken om de naam van de JSON-eigenschap te wijzigen.

## Voorbeeld {#example}

De Componenten van de Kern hebben de uitvoer JSON sinds versie [ 1.1.0 van de kerncomponenten ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=nl-NL) gesteund en kunnen als verwijzing worden gebruikt.

Een voorbeeld vindt u in de implementatie Sling Model van de Image Core-component en de bijbehorende geannoteerde interface.

CODE VOOR GITHUB

U kunt de code van deze pagina op GitHub vinden

* [ open aem-kern-wcm-componenten project op GitHub ](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components)
* Download het project als [ een dossier van het PIT ](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/archive/master.zip)

## Verwante documentatie {#related-documentation}

Raadpleeg de volgende secties voor meer informatie:

* Het [ onderwerp van de Fragmenten van de Inhoud in de gebruikersgids van Assets ](https://helpx.adobe.com/nl/experience-manager/6-4/assets/user-guide.html?topic=/experience-manager/6-4/assets/morehelp/content-fragments.ug.js)

* [Modellen van inhoudsfragmenten](/help/assets/content-fragments/content-fragments-models.md)
* [Ontwerpen met inhoudsfragmenten](/help/sites-authoring/content-fragments.md)
* [JSON-exportfunctie voor services voor inhoud](/help/sites-developing/json-exporter.md)
* [ Componenten van de Kern ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=nl-NL) en de [ component van het Fragment van de Inhoud ](https://helpx.adobe.com/nl/experience-manager/core-components/using/content-fragment-component.html)
