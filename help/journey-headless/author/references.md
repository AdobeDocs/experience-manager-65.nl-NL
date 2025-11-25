---
title: Meer informatie over het gebruik van verwijzingen in inhoudsfragmenten
description: Leer over het gebruiken van verwijzingen in de Fragmenten van de Inhoud, voor inhoud, andere fragmenten en andere activa (media). Introduceer de noodzaak voor en de mechanica van geneste fragmenten voor Headless CMS Authoring.
exl-id: d54a0a40-a8af-456a-9bf5-219d84540c97
solution: Experience Manager, Experience Manager Sites
feature: Headless,Content Fragments
role: Admin, Developer, User, Leader
source-git-commit: 07289e891399a78568dcac957bc089cc08c7898c
workflow-type: tm+mt
source-wordcount: '722'
ht-degree: 0%

---

# Meer informatie over het gebruik van verwijzingen in inhoudsfragmenten {#author-headless-references}

## Het artikel tot nu toe {#story-so-far}

Aan het begin van de [ Reis van de Auteur van de Inhoud van AEM Headless ](overview.md) de [ Inleiding ](introduction.md) behandelde de basisconcepten en de terminologie relevant voor creatie voor hoofd.

U hebt de grondbeginselen geleerd van Headless CMS Authoring, met een inleiding tot het ontwerpen met AEMaaCS en in het bijzonder, het ontwerpen van Inhoudsfragmenten.

Dit artikel bouwt hierop voort, zodat u begrijpt hoe u verwijzingen kunt gebruiken naar auteur uw eigen inhoud voor uw AEM-project zonder kop.

## Doelstelling {#objective}

* **Publiek**: Geavanceerd
* **Doelstelling**: Introduceer het gebruik van verwijzingen voor de Authoring van CMS zonder hoofd. Welke soorten verwijzingen beschikbaar zijn, en wat zijn hun doeleinden:

   * Content References
   * Verwijzingen naar element/media
   * Fragmentverwijzingen
   * Ad-hocverwijzingen vanuit een tekstblok

## Wat zijn referenties? {#what-are-references}

Verwijzingen zijn gewoon een mechanisme om uw bronnen aan te sluiten, of het nu andere inhoud, elementen (zoals afbeeldingen) of andere fragmenten betreft. Er zijn enkele verschillen, ook al zijn deze zeer vergelijkbaar.

Sommige verwijzingen hebben specifieke gegevenstypen (bijvoorbeeld Content References en Fragmentverwijzingen), terwijl andere eenvoudig worden toegevoegd als een verwijzing binnen een tekstblok (elementverwijzingen en ad-hocverwijzingen).

![ de Fragmenten van de Inhoud - Verwijzingen ](/help/journey-headless/author/assets/headless-journey-author-references-01.png)

## Content References {#content-references}

Content Reference do just that - they lets you reference any other content. Hiermee wordt een browser geopend waarin u het inhoudsitem kunt selecteren.

## Verwijzingen naar element/media {#assets-media-references}

Assets (bijvoorbeeld, beelden of media) kan binnen een blok van de Tekst van verwijzingen worden voorzien door de **activa van het Tussenvoegsel** optie te gebruiken. Hiermee opent u een browser waarin u het element kunt selecteren.

![ de Fragmenten van de Inhoud - Tussenvoegsel Activa ](/help/journey-headless/author/assets/headless-journey-author-references-02.png)

## Fragmentverwijzingen {#fragment-references}

Ook hier geldt dat fragmentverwijzingen alleen dat doen - ze laten u naar een ander fragment verwijzen. Waarom dit belangrijk is, moet er wat meer uitleg komen.

U kunt bijvoorbeeld de volgende modellen van inhoudsfragmenten definiëren:

* Plaats
* Bedrijf
* Persoon
* Uitreiking

Het lijkt vrij eenvoudig, maar een bedrijf heeft zowel een CEO als werknemers...en dit zijn allemaal mensen, elk gedefinieerd als een persoon.

En een persoon kan een Prijs (of misschien twee) hebben.

* Mijn bedrijf - Bedrijf
   * CEO - Persoon
   * Werknemer(s) - Persoon
      * Persoonlijke onderscheiding(en) - Uitreiking

Dat is alleen maar voor starters. Afhankelijk van de complexiteit kan een prijs bedrijfsspecifiek zijn of kan een bedrijf zijn hoofdkantoor in een bepaalde stad hebben.

U kunt deze relaties vertegenwoordigen met fragmentverwijzingen, omdat deze worden begrepen door zowel u (de auteur) als de toepassingen zonder kop.

Als auteur bent u niet verantwoordelijk voor het definiëren van deze relaties (dat wordt gedaan door de Content Architect bij het maken van het Content Fragment Model), maar u moet weten hoe u de verwijzingen herkent en bewerkt.

### Geneste fragmenten ontwerpen {#author-nested-fragment}

Het ontwerpen van de Verwijzingen van het Fragment is vrij ongecompliceerd (hoewel gewoonlijk zal het gebied niet als **Verwijzing van het Fragment** worden geëtiketteerd). U kunt de verwijzing rechtstreeks invoeren of (waarschijnlijker) het mappictogram selecteren om een browser te openen waarin u door het gewenste fragment kunt navigeren en het gewenste fragment kunt selecteren.

![ de Fragmenten van de Inhoud - Verwijzingen ](/help/journey-headless/author/assets/headless-journey-author-references-03.png)

De definitie van de besturingselementen van het inhoudsfragmentmodel:

* of u meerdere referenties kunt selecteren om toe te voegen
* de modeltypen van inhoudsfragmenten die u kunt selecteren; het model van het Fragment van de Inhoud bepaalt de fragmentmodellen die voor de verwijzing worden toegestaan, zodat presenteert AEM slechts fragmenten die op die modellen worden gebaseerd.

### Door geneste fragmenten navigeren {#navigate-nested-fragment}

Gebruikend het **lusje van de Boom van de Structuur** van de Redacteur van het Fragment van de Inhoud kunt u door de fragmenten navigeren die door uw fragment van verwijzingen worden voorzien, en dan door om het even welke verwijzingen zij kunnen bevatten. Als u een verwijzing selecteert, wordt dat fragment geopend voor bewerking.

>[!NOTE]
>
>Met de broodkruimels in het hoofddeelvenster kunt u terugnavigeren naar het beginpunt.

![ de Structuur van het Fragment van de Inhoud Boom ](/help/assets/content-fragments/assets/cfm-structuretree-02.png)

## Ad-hocverwijzingen {#adhoc-references}

Ad-hocverwijzingen kunnen worden toegevoegd als een eenvoudige koppeling binnen een tekstblok:

![ de Fragmenten van de Inhoud - ad hoc Verwijzingen ](/help/journey-headless/author/assets/headless-journey-author-references-04.png)

## Volgende functies {#whats-next}

Nu u over verwijzingen en structuur in de Fragmenten van de Inhoud hebt geleerd, moet de volgende stap [ leren hoe over Meta-gegevens en het Tags ](metadata-tagging.md). Zo leert en bespreekt u hoe u metagegevens en tags voor de inhoudsfragmenten kunt definiëren.

## Aanvullende bronnen {#additional-resources}

* [Werken met inhoudsfragmenten](/help/assets/content-fragments/content-fragments.md)

   * [Inhoudsfragmenten beheren](/help/assets/content-fragments/content-fragments-managing.md)

      * [De configuratie toepassen op uw Assets-map](/help/assets/content-fragments/content-fragments-configuration-browser.md#apply-the-configuration-to-your-assets-folder)

      * [Een inhoudsfragment maken](/help/assets/content-fragments/content-fragments-managing.md#creating-a-content-fragment)

   * [Variaties - Inhoudsfragmenten ontwerpen](/help/assets/content-fragments/content-fragments-variations.md)

   * [Modellen van inhoudsfragmenten](/help/assets/content-fragments/content-fragments-models.md)

      * [Modellen van inhoudsfragmenten - gegevenstypen](/help/assets/content-fragments/content-fragments-models.md#data-types)

      * [Modellen van inhoudsfragmenten - eigenschappen](/help/assets/content-fragments/content-fragments-models.md#properties)

* Aan de slag - hulplijnen
   * [Een Assets-map zonder koppen en een snelstartgids maken](/help/sites-developing/headless/getting-started/create-assets-folder.md)

* [AEM Headless Content Architect Reis](/help/journey-headless/architect/overview.md)

* [AEM Headless Translation Reis](/help/journey-headless/translation/overview.md)
