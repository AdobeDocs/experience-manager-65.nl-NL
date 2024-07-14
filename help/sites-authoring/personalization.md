---
title: Personalization en inhoud gericht
description: Leer hoe u met Adobe Experience Manager 6.5 persoonlijke inhoud kunt maken.
exl-id: be34760a-875b-419d-9fa4-2359b314a3b7
solution: Experience Manager, Experience Manager Sites
feature: Authoring,Personalization
role: User,Admin,Architect,Developer
source-git-commit: 9a3008553b8091b66c72e0b6c317573b235eee24
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 0%

---

# Personalization en inhoud gericht {#personalization}

## Personalization en inhoud gericht {#personalization-and-content-targeting}

AEM biedt een kader van instrumenten voor het ontwerpen van gerichte inhoud en het presenteren van persoonlijke ervaringen.

## Doelmodus {#targeting-mode}

[ de Auteur richtte inhoud ](/help/sites-authoring/content-targeting-touch.md) gebruikend het richten wijze van AEM. De gerichte wijze en de component van het Doel verstrekken hulpmiddelen om inhoud voor de ervaringen van uw marketing activiteiten tot stand te brengen.

## Activiteiten {#activities}

Met de activiteiten worden uw marketingactiviteiten gedefinieerd en georganiseerd. De activiteiten omvatten het publiek dat u richt, en de periode waarin het richten wordt toegepast.

Bijvoorbeeld, omvat de het productcatalogus van Wij.Retail meters die aandacht op seizoensgebonden producten richten. De activiteit van de Sport van de Zomer bepaalt de marketing segmenten die de telers tijdens zomermaanden richten.

De activiteiten identificeren ook [ richtend motor ](/help/sites-authoring/personalization.md#targeting-engine) die uw pagina&#39;s gebruiken.

Gebruik de [ console van Activiteiten ](/help/sites-authoring/activitylib.md) om de activiteiten voor uw merken tot stand te brengen en te beheren. U kunt activiteiten ook tot stand brengen aangezien u [ auteur gerichte inhoud ](/help/sites-authoring/content-targeting-touch.md).

## Ervaringen {#experiences}

Voor elke activiteit, bepaalt u één of meerdere ervaringen die het publiek identificeren dat u richt. AEM stelt u in staat de inhoud te beheren die elke ervaring omvat.

De soorten publiek zijn gebaseerd op marketing segmenten die of in AEM of Adobe Target worden gecreeerd. Wanneer een bezoeker een webpagina opent, bepaalt de paginalogica het publiek waartoe zij behoren en geeft deze de inhoud weer die u voor dat publiek hebt gemaakt.

Een activiteit definieert bijvoorbeeld ervaringen voor twee verschillende doelgroepen: vrouwen ouder dan 30 jaar en vrouwen jonger dan 30 jaar. Op de pagina Vrouwen van de website We.Retail staan verschillende producten voor elke ervaring.

U definieert ervaringen voor een activiteit. U kunt de [ console van Activiteiten ](/help/sites-authoring/activitylib.md#adding-editing-an-activity-using-the-activities-console) of [ het richten wijze ](/help/sites-authoring/content-targeting-touch.md#adding-and-removing-experiences-using-targeting-mode) gebruiken om ervaringen aan een activiteit toe te voegen.

## Aanbiedingen {#offers}

Een aanbieding is inhoud die op een plaats op een pagina voor een ervaring verschijnt. Gebruik verschillende aanbiedingen voor verschillende ervaringen om de doeltreffendheid van de inhoud voor uw publiek te maximaliseren.

De pagina Vrouwen van de voorbeeldwebsite We.Retail kan bijvoorbeeld aanbiedingen gebruiken als de laserafbeelding die boven aan de pagina wordt weergegeven. Een ander aanbod wordt gebruikt als taser voor vrouwen ouder dan 30 jaar en voor vrouwen jonger dan 30 jaar.

Gebruik de [ console van Aanbiedingen ](/help/sites-authoring/offerlib.md) om aanbiedingen tot stand te brengen die u in veelvoudige ervaringen kunt gebruiken. Creeer enig-gebruik aanbiedingen of voeg aanbiedingen van een aanbiedingsbibliotheek toe wanneer [ creërend gerichte inhoud ](/help/sites-authoring/content-targeting-touch.md).

## Richtingsmotor {#targeting-engine}

De doelengine is het mechanisme dat de logica voor doelgerichte inhoud aandrijft. [ de Activiteiten ](/help/sites-authoring/activitylib.md) worden gevormd om één van twee het richten motoren te gebruiken die beschikbaar zijn: AEM en Adobe Target.

### AEM {#aem}

AEM verstrekt ingebouwde het richten motor die paginaverzoeken verwerkt en de inhoud aan vertoning bepaalt. Wanneer u de AEM doelengine gebruikt, kunt u alleen segmenten gebruiken die zijn gemaakt in AEM voor het definiëren van het publiek van uw ervaringen.

### Adobe Target {#adobe-target}

De Adobe Target-engine voor doelwitten zorgt ervoor dat informatie die tijdens paginabezoeken is verzameld, wordt bijgehouden in Adobe Target.

* Wanneer u deze doelengine gebruikt, gebruikt u de segmenten die u uit Adobe Target importeert om het publiek voor uw ervaringen te definiëren.
* De activiteiten die de motor van Adobe Target gebruiken worden [ gesynchroniseerd aan Doel ](/help/sites-authoring/activitylib.md#synchronizing-activities-with-adobe-target).

U kunt deze motor gebruiken wanneer u [ met Adobe Target ](/help/sites-administering/opt-in.md) geïntegreerd hebt.
