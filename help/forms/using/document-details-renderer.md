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

PDF forms worden gerenderd door `PdfTaskForm View`.

Wanneer een XDP-formulier wordt weergegeven als PDF, wordt een `FormBridge` JavaScript™ wordt toegevoegd door de service FormsAugmenter. Met dit JavaScript™ (in het PDF-formulier) kunt u handelingen uitvoeren zoals het verzenden, opslaan of offline maken van formulieren.

In de AEM Forms-werkruimte communiceert de PDFTaskForm-weergave met de `FormBridge`JavaScript, via een tussenliggende HTML die aanwezig is op `/lc/libs/ws/libs/ws/pdf.html`. De stroom is:

**PDFTaskForm, weergave - pdf.html**

Communiceert met `window.postMessage` / `window.attachEvent('message')`

Dit is de standaardmanier van communicatie tussen een bovenliggend frame en een iframe. De bestaande gebeurtenislisteners van eerder geopende PDF forms worden verwijderd voordat een nieuwe wordt toegevoegd. Bij deze bewerking wordt ook gekeken naar het schakelen tussen het tabblad Formulier en het tabblad Historie in de weergave met taakdetails.

**pdf.html - `FormBridge`JavaScript in de gerenderde PDF**

Communiceert met `pdfObject.postMessage` / `pdfObject.messageHandler`

Deze methode is de standaardmanier van communicatie met een PDFJavaScript van een HTML. De PDFTaskForm-weergave zorgt ook voor een vlakke PDF en geeft deze onbewerkt weer.

>[!NOTE]
>
>Het wordt niet aanbevolen de inhoud van de PDFTaskForm-weergave te bewerken.

## New HTML Forms {#new-html-forms}

Nieuwe HTML-formulieren worden gegenereerd door de NewHTMLTaskForm View.

Als een XDP-formulier wordt weergegeven als HTML met het pakket voor mobiele formulieren dat wordt geïmplementeerd op CRX, wordt ook extra `FormBridge`JavaScript naar het formulier, dat verschillende methoden voor het opslaan en verzenden van formuliergegevens beschikbaar maakt.

Dit JavaScript verschilt van het JavaScript waarnaar in de bovenstaande PDF forms wordt verwezen, maar heeft een soortgelijk doel.

>[!NOTE]
>
>Adobe raadt het bewerken van de inhoud van de weergave NewHTMLTaskForm niet aan.

## Flex Forms en hulplijnen {#flex-forms-and-guides}

Flex Forms wordt gerenderd door SWFTaskForm en de hulplijnen worden gerenderd door respectievelijk HTMLTaskForm Views.

In de AEM Forms-werkruimte communiceren deze weergaven met de werkelijke SWF die het Flex®-formulier/de-handleiding vormt. Hierbij wordt gebruikgemaakt van een intermediaire SWF die aanwezig is op `/lc/libs/ws/libs/ws/WSNextAdapter.swf`

De communicatie gebeurt met `swfObject.postMessage` / `window.flexMessageHandler`.

Dit protocol wordt gedefinieerd door de `WsNextAdapter.swf`. De bestaande `flexMessageHandlers`in het vensterobject worden van eerder geopende SWF-formulieren verwijderd voordat een nieuw formulier wordt toegevoegd. De logica houdt ook rekening met het schakelen tussen formuliertabblad en historietabblad in de weergave met taakdetails. De `WsNextAdapter.swf` wordt gebruikt om verschillende formulierhandelingen uit te voeren, zoals opslaan of verzenden.

>[!NOTE]
>
>Het wordt niet aanbevolen om `WSNextAdapter.swf` of de inhoud van de weergave SwfTaskForm / HtmlTaskForm.

## Toepassingen van derden (bijvoorbeeld Correspondence Management) {#third-party-applications-for-example-correspondence-management}

Toepassingen van derden worden gerenderd met de ExtAppTaskForm-weergave.

**Communicatie van externe toepassingen naar de AEM Forms-werkruimte**

AEM Forms-werkruimte luistert naar `window.global.postMessage([Message],[Payload])`

[Bericht] kan een tekenreeks zijn die is opgegeven als `SubmitMessage`| `CancelMessage`| `ErrorMessage`| `actionEnabledMessage`in de `runtimeMap`. Toepassingen van derden moeten deze interface gebruiken om de AEM Forms-werkruimte naar wens op de hoogte te stellen. Het gebruik van deze interface is verplicht, omdat de AEM Forms-werkruimte moet weten dat wanneer de taak wordt verzonden, zodat deze het taakvenster kan opschonen.

**AEM Forms-werkruimte voor communicatie met toepassingen van derden**

Als de knoppen voor directe actie van de AEM Forms-werkruimte zichtbaar zijn, wordt dit aangeroepen `window.[External-App-Name].getMessage([Action])`, waarbij `[Action]` wordt gelezen uit de `routeActionMap`. De externe toepassing moet luisteren naar deze interface en vervolgens de AEM Forms-werkruimte via het dialoogvenster `postMessage ()` API.

Een Flex-toepassing kan bijvoorbeeld `ExternalInterface.addCallback('getMessage', listener)` deze mededeling te ondersteunen. Als de externe toepassing het verzenden van formulieren via eigen knoppen wil verwerken, moet u `hideDirectActions = true() in the runtimeMap` en u kunt deze listener overslaan. Deze constructie is dus optioneel.

Meer informatie over de integratie van toepassingen van derden met betrekking tot Correspondence Management vindt u op [Correspondentenbeheer integreren in de AEM Forms-werkruimte](/help/forms/using/integrating-correspondence-management-html-workspace.md).
