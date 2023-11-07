---
title: Forms renderen
seo-title: Rendering Forms
description: Met de Forms-service kunt u interactieve toepassingen voor het vastleggen van gegevens maken die formulieren valideren, verwerken, transformeren en leveren die normaal gesproken in Designer zijn gemaakt. Formulierauteurs kunnen één formulierontwerp ontwikkelen dat de Forms-service in verschillende browseromgevingen rendert in PDF, SWF of HTML.
seo-description: Use the Forms service to create interactive data capture client applications that validate, process, transform, and deliver forms typically created in Designer. Form authors can develop a single form design that the Forms service renders in PDF, SWF, or HTML in various browser environments.
uuid: 68d7b7bc-7730-4a83-b7b9-ebe2a29d6c51
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/performing_service_operations_using_apis
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: f8749793-e53f-4812-a093-8278f480e6a8
role: Developer
exl-id: ec9ccf04-7cec-493a-91ab-0e399a905338
source-git-commit: 49688c1e64038ff5fde617e52e1c14878e3191e5
workflow-type: tm+mt
source-wordcount: '569'
ht-degree: 0%

---

# Forms renderen {#rendering-forms}

**Voorbeelden en voorbeelden in dit document gelden alleen voor AEM Forms in JEE-omgeving.**

**Informatie over de Forms-service**

Met de Forms-service kunt u interactieve toepassingen voor het vastleggen van gegevens maken die formulieren valideren, verwerken, transformeren en leveren die normaal gesproken in Designer zijn gemaakt. Formulierauteurs kunnen één formulierontwerp ontwikkelen dat de Forms-service in verschillende browseromgevingen rendert in PDF, SWF of HTML.

Wanneer een eindgebruiker een formulier aanvraagt, stuurt een clienttoepassing de aanvraag naar de Forms-service, die het formulier in de juiste indeling retourneert. Zodra de Forms-service een aanvraag ontvangt, worden gegevens met een formulierontwerp samengevoegd en wordt het formulier in de gewenste indeling geleverd. De uitvoer van de formulierservice is een interactief formulier, meestal een PDF-document. Met een interactief formulier kunnen gebruikers de velden op het formulier invullen.

Afhankelijk van het type clienttoepassing kunt u het formulier naar een clientwebbrowser schrijven of het formulier opslaan als een PDF-bestand. Een webtoepassing kan het formulier naar een webbrowser schrijven. Een bureaubladtoepassing kan het formulier opslaan als een PDF-bestand. Om te tonen hoe u naar een webbrowser en naar een PDF-bestand schrijft, begint de snelkoppeling in het dialoogvenster *Forms renderen* de sectie op de volgende wijze wordt georganiseerd:

* De sterk getypte Java API-voorbeelden (SOAP-modus) zijn een Java-servlet.
* De voorbeelden van de webservice (Java Base64) zijn een Java-servlet.
* De voorbeelden van de Webdienst (MTOM) zijn een consoletoepassing (niet alle snelle begin hebben een voorbeeld MTOM).

>[!NOTE]
>
>Ga voor informatie over het maken van een webtoepassing die Java-servlets gebruikt om de Forms-service aan te roepen naar [Webtoepassingen maken die Forms renderen](/help/forms/developing/creating-web-applications-renders-forms.md).

U kunt op twee manieren een formulierontwerp (een XDP-bestand) of een PDF-document doorgeven aan de Forms-service:

* U kunt naar het formulierontwerp verwijzen met een URL-waarde. Bij deze methode wordt een `URLSpec` object. De inhoudroot wordt doorgegeven aan de Forms-service met behulp van de `URLSpec` object `setContentRootURI` methode. De naam van het formulierontwerp ( `formQuery`) wordt doorgegeven als een afzonderlijke parameter. De twee waarden worden samengevoegd om de absolute verwijzing naar het formulierontwerp te verkrijgen. (De meeste sneltoetsen beginnen in het dialoogvenster *Forms renderen* deze aanpak te gebruiken.)
* U kunt een `com.adobe.idp.Document` die het formulierontwerp voor de Forms-service bevat. Twee nieuwe methoden met naam `renderPDFForm2` en `renderHTMLForm2` accepteren `com.adobe.idp.Document` object dat een formulierontwerp bevat. (Zie [Documenten doorgeven aan de Forms-service](/help/forms/developing/passing-documents-forms-service.md)

U kunt deze taken uitvoeren met de Forms-service:

* Interactieve PDF forms renderen. (Zie [Interactieve PDF forms renderen](/help/forms/developing/rendering-interactive-pdf-forms.md).)
* Formulieren weergeven op de client. (Zie [Forms renderen op de client](/help/forms/developing/rendering-forms-client.md).)
* Formulieren weergeven op basis van fragmenten. (Zie [Forms renderen op basis van fragmenten](/help/forms/developing/rendering-forms-based-fragments.md).)
* Formulieren met rechten weergeven. (Zie [Forms met rechten voor renderen](/help/forms/developing/rendering-rights-enabled-forms.md).)
* Formulieren weergeven als HTML. (Zie [Forms renderen als HTML](/help/forms/developing/rendering-forms-html.md).)
* HTML Forms renderen met aangepaste CSS-bestanden ([HTML Forms renderen met aangepaste CSS-bestanden](/help/forms/developing/rendering-html-forms-using-custom.md).)
* Ingevulde formulieren verwerken. (Zie [Verzendde Forms afhandelen](/help/forms/developing/handling-submitted-forms.md).)
* PDF-documenten maken met verzonden XML-gegevens. (Zie [PDF-documenten maken met verzonden XML-gegevens](/help/forms/developing/creating-pdf-documents-submitted-xml.md).)
* Formulieren vooraf invullen. (Zie [Forms vooraf vullen met stroombare indelingen](/help/forms/developing/prepopulating-forms-flowable-layouts.md).)
* Documenten doorgeven. (Zie [Documenten doorgeven aan de Forms-service](/help/forms/developing/passing-documents-forms-service.md)
* Formuliergegevens berekenen. (Zie [Formuliergegevens berekenen](/help/forms/developing/calculating-form-data.md).)
* Optimaliseer een toepassing. (Zie [De prestaties van de Forms-service optimaliseren](/help/forms/developing/optimizing-performance-forms-service.md).)
