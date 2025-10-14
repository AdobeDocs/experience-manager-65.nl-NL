---
title: Documentdetails voor renderer
description: Conceptuele informatie over hoe de rendering werkt in de AEM Forms-werkruimte om de verschillende ondersteunde formulier- en bestandstypen weer te geven.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
exl-id: 946f0f6d-86af-41c1-98ef-98c8f5566e95
solution: Experience Manager, Experience Manager Forms
feature: HTML5 Forms,Adaptive Forms,Mobile Forms
role: Admin, User, Developer
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '666'
ht-degree: 0%

---

# Documentdetails voor renderer {#document-details-for-renderer}

## Inleiding {#introduction}

In de AEM Forms-werkruimte worden meerdere formuliertypen naadloos ondersteund. Deze omvatten:

* PDF forms (XDP / acroform / Platte PDF)
* Nieuwe HTML-formulieren
* Afbeeldingen
* Toepassingen van derden (bijvoorbeeld Correspondence Management)

In dit document wordt uitgelegd hoe deze renderers werken vanuit het perspectief van semantische aanpassing/hergebruik van componenten, zodat aan de vereisten van de klant wordt voldaan zonder dat een renditie wordt verbroken. Hoewel in de AEM Forms-werkruimte alle gebruikersinterface-/semantische wijzigingen mogelijk zijn, wordt aangeraden de renderinglogica van verschillende formuliertypen niet te wijzigen, anders kunnen de resultaten onvoorspelbaar zijn. Dit document is bedoeld als leidraad/kennis ter ondersteuning van rendering van dezelfde vorm, waarbij dezelfde werkruimtecomponenten in verschillende portalen worden gebruikt, en niet voor het wijzigen van de renderinglogica zelf.

## PDF forms {#pdf-forms}

PDF forms worden gerenderd door `PdfTaskForm View` .

Wanneer een XDP-formulier wordt weergegeven als PDF, wordt een `FormBridge` JavaScript™ toegevoegd door de FormsAugmenter-service. Met deze JavaScript™ (in het PDF-formulier) kunt u handelingen uitvoeren zoals het verzenden, opslaan of offline maken van formulieren.

In de werkruimte van AEM Forms, communiceert de mening PDFTaskForm met `FormBridge` JavaScript, als intermediaire HTML aanwezig bij `/lc/libs/ws/libs/ws/pdf.html`. De stroom is:

**PDFTaskForm mening - pdf.html**

Communiceert met `window.postMessage` / `window.attachEvent('message')`

Dit is de standaardmanier van communicatie tussen een bovenliggend frame en een iframe. De bestaande gebeurtenislisteners van eerder geopende PDF forms worden verwijderd voordat een nieuwe wordt toegevoegd. Bij deze bewerking wordt ook gekeken naar het schakelen tussen het tabblad Formulier en het tabblad Historie in de weergave met taakdetails.

**pdf.html - `FormBridge` JavaScript binnen de teruggegeven PDF**

Communiceert met `pdfObject.postMessage` / `pdfObject.messageHandler`

Deze methode is de standaardmanier van communicatie met een PDFJavaScript van een HTML. De PDFTaskForm-weergave zorgt ook voor een vlakke PDF en geeft deze onbewerkt weer.

>[!NOTE]
>
>Het wordt niet aanbevolen de inhoud van de PDFTaskForm-weergave te bewerken.

## New HTML Forms {#new-html-forms}

Nieuwe HTML-formulieren worden gegenereerd door de NewHTMLTaskForm View.

Wanneer een XDP Vorm als HTML gebruikend het mobiele vormenpakket wordt teruggegeven dat op CRX wordt opgesteld, voegt het ook extra `FormBridge` JavaScript aan de vorm toe, die verschillende methodes voor het opslaan en het voorleggen van vormgegevens blootstelt.

Deze JavaScript verschilt van de in de bovenstaande PDF forms genoemde, maar heeft een soortgelijk doel.

>[!NOTE]
>
>Adobe raadt het bewerken van de inhoud van de weergave NewHTMLTaskForm niet aan.

## Flex Forms en hulplijnen {#flex-forms-and-guides}

Flex Forms wordt gerenderd door SWFTaskForm en de hulplijnen worden gerenderd door respectievelijk HTMLTaskForm Views.

In de AEM Forms-werkruimte communiceren deze weergaven met de werkelijke SWF die het Flex®-formulier/de-hulplijn vormt via een tussenliggende SWF die zich bevindt op `/lc/libs/ws/libs/ws/WSNextAdapter.swf`

De communicatie vindt plaats met `swfObject.postMessage` / `window.flexMessageHandler` .

Dit protocol wordt gedefinieerd door de `WsNextAdapter.swf` . Het bestaande `flexMessageHandlers` op venstervoorwerp, van eerder geopende vormen van SWF wordt verwijderd alvorens nieuwe toe te voegen. De logica houdt ook rekening met het schakelen tussen formuliertabblad en historietabblad in de weergave met taakdetails. `WsNextAdapter.swf` wordt gebruikt om verschillende formulierhandelingen uit te voeren, zoals opslaan of verzenden.

>[!NOTE]
>
>Het wordt afgeraden `WSNextAdapter.swf` of de inhoud van de weergave SWFTaskForm / HTMLTaskForm te wijzigen.

## Toepassingen van derden (bijvoorbeeld Correspondence Management) {#third-party-applications-for-example-correspondence-management}

Toepassingen van derden worden gerenderd met de ExtAppTaskForm-weergave.

**de werkruimtetransformatie van de derdetoepassing aan AEM Forms**

AEM Forms-werkruimte luistert naar `window.global.postMessage([Message],[Payload])`

[ Bericht ] kan een koord zijn dat als `SubmitMessage` wordt gespecificeerd| `CancelMessage`| `ErrorMessage`| `actionEnabledMessage` in `runtimeMap`. Toepassingen van derden moeten deze interface gebruiken om de AEM Forms-werkruimte naar wens op de hoogte te stellen. Het gebruik van deze interface is verplicht, omdat de AEM Forms-werkruimte moet weten dat wanneer de taak wordt verzonden, zodat deze het taakvenster kan opschonen.

**de werkruimte van AEM Forms aan mededeling van de derdetoepassing**

Als de knoppen voor directe acties van de AEM Forms-werkruimte zichtbaar zijn, wordt `window.[External-App-Name].getMessage([Action])` aangeroepen, waarbij `[Action]` wordt gelezen van de `routeActionMap` . De externe toepassing moet luisteren naar deze interface en vervolgens de AEM Forms-werkruimte via de `postMessage ()` API op de hoogte stellen.

Een Flex-toepassing kan bijvoorbeeld `ExternalInterface.addCallback('getMessage', listener)` definiëren ter ondersteuning van deze communicatie. Als de toepassing van derden het verzenden van formulieren via eigen knoppen wil verwerken, moet u `hideDirectActions = true() in the runtimeMap` opgeven en kunt u deze listener overslaan. Deze constructie is dus optioneel.

U kunt meer over de integratie van de derdetoepassing betreffende het Beheer van de Correspondentie bij [&#x200B; het Integreren van het Beheer van de Correspondentie in de werkruimte van AEM Forms &#x200B;](/help/forms/using/integrating-correspondence-management-html-workspace.md) lezen.
