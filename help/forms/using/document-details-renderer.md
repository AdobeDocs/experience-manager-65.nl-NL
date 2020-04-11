---
title: Documentdetails voor renderer
seo-title: Documentdetails voor renderer
description: Conceptuele informatie over de manier waarop rendering werkt in de werkruimte van AEM Forms om de verschillende ondersteunde formulier- en bestandstypen weer te geven.
seo-description: Conceptuele informatie over de manier waarop rendering werkt in de werkruimte van AEM Forms om de verschillende ondersteunde formulier- en bestandstypen weer te geven.
uuid: ae3f0585-9105-4ca7-a490-ffdefd3ac8cd
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: b6e88080-6ffc-4796-98c7-d7462bca454e
translation-type: tm+mt
source-git-commit: 56c6cfd437ef185336e81373bd5f758205b96317

---


# Documentdetails voor renderer {#document-details-for-renderer}

## Inleiding {#introduction}

In de werkruimte van AEM-formulieren worden meerdere formuliertypen naadloos ondersteund. Deze omvatten:

* PDF-formulieren (XDP / Acrobat / Platte PDF&#39;s)
* Nieuwe HTML-formulieren
* Afbeeldingen
* Toepassingen van derden (bijvoorbeeld Correspondence Management)

In dit document wordt uitgelegd hoe deze renderers werken vanuit het perspectief van semantische aanpassing/hergebruik van componenten, zodat aan de vereisten van de klant wordt voldaan zonder dat een renditie wordt verbroken. Hoewel de werkruimte van de Vormen van AEM voor om het even welke gebruikersinterface/semantische veranderingen toestaat, wordt geadviseerd dat de het teruggeven logica van verschillende vormtypes niet wordt veranderd, anders kunnen de resultaten onvoorspelbaar zijn. Dit document is bedoeld als leidraad/kennis ter ondersteuning van rendering van hetzelfde formulier, waarbij dezelfde werkruimtecomponenten in verschillende portalen worden gebruikt, en niet voor het wijzigen van de renderinglogica zelf.

## PDF-formulieren {#pdf-forms}

PDF-formulieren worden gerenderd door `PdfTaskForm View`.

Wanneer een XDP-formulier wordt weergegeven als PDF, wordt een `FormBridge` JavaScript™ toegevoegd door de FormsAugmenter-service. Met dit JavaScript™ (in het PDF-formulier) kunt u handelingen uitvoeren zoals het verzenden, opslaan of offline maken van formulieren.

In de werkruimte van Vormen AEM, communiceert de mening PDFTaskForm met `FormBridge`javascript, via intermediaire HTML aanwezig bij `/lc/libs/ws/libs/ws/pdf.html`. De stroom is:

**PDFTaskForm, weergave - pdf.html**

Communiceert met `window.postMessage` / `window.attachEvent('message')`

Dit is de standaardmanier van communicatie tussen een bovenliggend frame en een iframe. De bestaande gebeurtenislisteners van eerder geopende PDF-formulieren worden verwijderd voordat een nieuwe wordt toegevoegd. Bij deze bewerking wordt ook gekeken naar het schakelen tussen het tabblad Formulier en het tabblad Historie in de weergave met taakdetails.

**pdf.html -`FormBridge`javascript in de gerenderde PDF**

Communiceert met `pdfObject.postMessage` / `pdfObject.messageHandler`

Dit is de standaardmanier voor communicatie met een PDF-javascript vanuit een HTML. In de PDFTaskForm-weergave wordt ook de platte PDF verzorgd en weergegeven.

>[!NOTE]
>
>Het wordt niet aanbevolen de inhoud van de PDFTaskForm-weergave te wijzigen.

## Nieuwe HTML-formulieren {#new-html-forms}

Nieuwe HTML-formulieren worden gegenereerd door de NewHTMLTaskForm View.

Als een XDP-formulier wordt weergegeven als HTML met het pakket voor mobiele formulieren dat wordt geïmplementeerd op CRX, wordt ook extra `FormBridge` javascript toegevoegd aan het formulier, dat verschillende methoden voor het opslaan en verzenden van formuliergegevens beschikbaar maakt.

Dit JavaScript-bestand verschilt van het JavaScript waarnaar in PDF-formulieren hierboven wordt verwezen, maar heeft hetzelfde doel.

>[!NOTE]
>
>Het wordt afgeraden de inhoud van de weergave NewHTMLTaskForm te wijzigen.

## Flex-formulieren en hulplijnen {#flex-forms-and-guides}

Flex Forms wordt door SwfTaskForm teruggegeven en de gidsen worden teruggegeven door Meningen HtmlTaskForm.

In de werkruimte van AEM-formulieren communiceren deze weergaven met het SWF-bestand dat de flex-vorm/hulplijn vormt met behulp van een intermediair SWF-bestand dat zich bevindt op `/lc/libs/ws/libs/ws/WSNextAdapter.swf`

De communicatie vindt plaats met `swfObject.postMessage` / `window.flexMessageHandler`.

Dit protocol wordt bepaald door het `WsNextAdapter.swf`. Het bestaande object `flexMessageHandlers`in het venster van eerder geopende SWF-formulieren wordt verwijderd voordat een nieuw formulier wordt toegevoegd. De logica houdt ook rekening met het schakelen tussen formuliertabblad en historietabblad in de weergave met taakdetails. `WsNextAdapter.swf` wordt gebruikt voor het uitvoeren van verschillende formulierhandelingen, zoals opslaan of verzenden.

>[!NOTE]
>
>Het wordt afgeraden de inhoud van de weergave SWFTaskForm / HTMLTaskForm te wijzigen `WSNextAdapter.swf` of te wijzigen.

## Toepassingen van derden (bijvoorbeeld Correspondence Management) {#third-party-applications-for-example-correspondence-management}

Toepassingen van derden worden gerenderd met de ExtAppTaskForm-weergave.

**Toepassing van derden op communicatie in de werkruimte van AEM Forms**

AEM-werkruimte Formulieren luistert naar `window.global.postMessage([Message],[Payload])`

[Bericht] kan een tekenreeks zijn die is opgegeven als `SubmitMessage`| `CancelMessage`| `ErrorMessage`| `actionEnabledMessage`in het `runtimeMap`gebied. Toepassingen van derden moeten deze interface gebruiken om de werkruimte van AEM Forms naar behoefte op de hoogte te stellen. Het gebruik van deze interface is verplicht, omdat de werkruimte van AEM Forms moet weten dat wanneer de taak wordt verzonden zodat deze het taakvenster kan opschonen.

**AEM vormt werkruimte aan derdetoepassingsmededeling**

Als de directe actieknoppen van AEM Forms in de werkruimte zichtbaar zijn, wordt het aangeroepen `window.[External-App-Name].getMessage([Action])`, waarbij [ `Action]` wordt gelezen van het `routeActionMap`. De externe toepassing moet luisteren naar deze interface en vervolgens de werkruimte van AEM Forms via de `postMessage ()` API op de hoogte stellen.

Een Flex-toepassing kan bijvoorbeeld definiëren `ExternalInterface.addCallback('getMessage', listener)` om deze communicatie te ondersteunen. Als de externe toepassing het verzenden van formulieren via eigen knoppen wil verwerken, moet u dit opgeven `hideDirectActions = true() in the runtimeMap` en kunt u deze listener overslaan. Deze constructie is dus optioneel.

U kunt meer lezen over de integratie van toepassingen van derden met betrekking tot Correspondence Management bij het [integreren van Correspondentiebeheer in de werkruimte](/help/forms/using/integrating-correspondence-management-html-workspace.md)van AEM Forms.
