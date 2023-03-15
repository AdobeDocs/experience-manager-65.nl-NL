---
title: Documentdetails voor renderer
seo-title: Document details for renderer
description: Conceptuele informatie over hoe renderingen werken in de AEM Forms-werkruimte om de verschillende ondersteunde formulier- en bestandstypen weer te geven.
seo-description: Conceptual information on how renders work in AEM Forms workspace to render the various supported form and file types.
uuid: ae3f0585-9105-4ca7-a490-ffdefd3ac8cd
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: b6e88080-6ffc-4796-98c7-d7462bca454e
exl-id: 946f0f6d-86af-41c1-98ef-98c8f5566e95
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '653'
ht-degree: 0%

---

# Documentdetails voor renderer {#document-details-for-renderer}

## Inleiding {#introduction}

In de AEM Forms-werkruimte worden meerdere formuliertypen naadloos ondersteund. Deze omvatten:

* PDF forms (XDP / acroform / Platte PDF)
* Nieuwe HTML-formulieren
* Afbeeldingen
* Toepassingen van derden (bijvoorbeeld Correspondence Management)

In dit document wordt uitgelegd hoe deze renderers werken vanuit het perspectief van semantische aanpassing/hergebruik van componenten, zodat aan de vereisten van de klant wordt voldaan zonder dat een renditie wordt verbroken. Hoewel in de AEM Forms-werkruimte alle gebruikersinterface-/semantische wijzigingen mogelijk zijn, wordt aangeraden de renderinglogica van verschillende formuliertypen niet te wijzigen, anders kunnen de resultaten onvoorspelbaar zijn. Dit document is bedoeld als leidraad/kennis ter ondersteuning van rendering van hetzelfde formulier, waarbij dezelfde werkruimtecomponenten in verschillende portalen worden gebruikt, en niet voor het wijzigen van de renderinglogica zelf.

## PDF forms {#pdf-forms}

PDF forms worden gerenderd door `PdfTaskForm View`.

Wanneer een XDP-formulier wordt weergegeven als PDF, wordt een `FormBridge` JavaScript™ wordt toegevoegd door de service FormsAugmenter. Met dit JavaScript™ (in het PDF-formulier) kunt u handelingen uitvoeren zoals het verzenden, opslaan of offline maken van formulieren.

In de AEM Forms-werkruimte communiceert de PDFTaskForm-weergave met de `FormBridge`javascript, via een intermediaire HTML aanwezig op `/lc/libs/ws/libs/ws/pdf.html`. De stroom is:

**PDFTaskForm, weergave - pdf.html**

Communiceert met `window.postMessage` / `window.attachEvent('message')`

Dit is de standaardmanier van communicatie tussen een bovenliggend frame en een iframe. De bestaande gebeurtenislisteners van eerder geopende PDF forms worden verwijderd voordat een nieuwe wordt toegevoegd. Bij deze bewerking wordt ook gekeken naar het schakelen tussen het tabblad Formulier en het tabblad Historie in de weergave met taakdetails.

**pdf.html - `FormBridge`javascript in de gerenderde PDF**

Communiceert met `pdfObject.postMessage` / `pdfObject.messageHandler`

Deze methode is de standaardmanier van communicatie met een PDFJavaScript van een HTML. De PDFTaskForm-weergave zorgt ook voor platte PDF en geeft deze duidelijk weer.

>[!NOTE]
>
>Het wordt niet aanbevolen de inhoud van de PDFTaskForm-weergave te wijzigen.

## New HTML Forms {#new-html-forms}

Nieuwe HTML-formulieren worden gegenereerd door de NewHTMLTaskForm View.

Als een XDP-formulier wordt weergegeven als HTML met het pakket voor mobiele formulieren dat wordt geïmplementeerd op CRX, wordt ook extra `FormBridge`JavaScript naar het formulier, dat verschillende methoden voor het opslaan en verzenden van formuliergegevens beschikbaar maakt.

Dit JavaScript verschilt van het JavaScript waarnaar in de bovenstaande PDF forms wordt verwezen, maar heeft een soortgelijk doel.

>[!NOTE]
>
>Het wordt afgeraden de inhoud van de weergave NewHTMLTaskForm te wijzigen.

## Flex Forms en hulplijnen {#flex-forms-and-guides}

Flex Forms wordt gerenderd door SWFTaskForm en de hulplijnen worden gerenderd door respectievelijk HTMLTaskForm Views.

In de AEM Forms-werkruimte communiceren deze weergaven met de werkelijke SWF die het flex-formulier/de flex-hulplijn vormt met behulp van een intermediaire SWF aanwezig op `/lc/libs/ws/libs/ws/WSNextAdapter.swf`

De communicatie gebeurt met `swfObject.postMessage` / `window.flexMessageHandler`.

Dit protocol wordt gedefinieerd door de `WsNextAdapter.swf`. De bestaande `flexMessageHandlers`in het vensterobject worden van eerder geopende SWF-formulieren verwijderd voordat een nieuw formulier wordt toegevoegd. De logica houdt ook rekening met het schakelen tussen formuliertabblad en historietabblad in de weergave met taakdetails. `WsNextAdapter.swf` wordt gebruikt voor het uitvoeren van verschillende formulierhandelingen, zoals opslaan of verzenden.

>[!NOTE]
>
>Het wordt niet aanbevolen om `WSNextAdapter.swf` of de inhoud van de weergave SwfTaskForm/HTMLTaskForm.

## Toepassingen van derden (bijvoorbeeld Correspondence Management) {#third-party-applications-for-example-correspondence-management}

Toepassingen van derden worden gerenderd met de ExtAppTaskForm-weergave.

**Communicatie van externe toepassingen naar de AEM Forms-werkruimte**

AEM Forms-werkruimte luistert naar `window.global.postMessage([Message],[Payload])`

[Bericht] kan een tekenreeks zijn die is opgegeven als `SubmitMessage`| `CancelMessage`| `ErrorMessage`| `actionEnabledMessage`in de `runtimeMap`. Toepassingen van derden moeten deze interface gebruiken om AEM Forms-werkruimte naar behoefte op de hoogte te stellen. Het gebruik van deze interface is verplicht, omdat de AEM Forms-werkruimte moet weten dat wanneer de taak wordt verzonden, zodat deze het taakvenster kan opschonen.

**AEM Forms-werkruimte voor communicatie met toepassingen van derden**

Als de knoppen voor directe actie van de AEM Forms-werkruimte zichtbaar zijn, wordt dit aangeroepen `window.[External-App-Name].getMessage([Action])`, waarbij `[Action]` wordt gelezen uit de `routeActionMap`. De externe toepassing moet luisteren naar deze interface en vervolgens de AEM Forms-werkruimte via het dialoogvenster `postMessage ()` API.

Een Flex-toepassing kan bijvoorbeeld `ExternalInterface.addCallback('getMessage', listener)` deze mededeling te ondersteunen. Als de externe toepassing het verzenden van formulieren via eigen knoppen wil verwerken, moet u `hideDirectActions = true() in the runtimeMap` en u kunt deze listener overslaan. Deze constructie is dus optioneel.

U kunt meer lezen over de integratie van toepassingen van derden met betrekking tot Correspondence Management op [Correspondentenbeheer integreren in de AEM Forms-werkruimte](/help/forms/using/integrating-correspondence-management-html-workspace.md).
