---
title: Forms renderen
seo-title: Forms renderen
description: Met de Forms-service kunt u interactieve toepassingen voor het vastleggen van gegevens maken die formulieren valideren, verwerken, transformeren en leveren die normaal gesproken in Designer zijn gemaakt. Formulierauteurs kunnen één formulierontwerp ontwikkelen dat de Forms-service in verschillende browseromgevingen weergeeft in PDF, SWF of HTML.
seo-description: Met de Forms-service kunt u interactieve toepassingen voor het vastleggen van gegevens maken die formulieren valideren, verwerken, transformeren en leveren die normaal gesproken in Designer zijn gemaakt. Formulierauteurs kunnen één formulierontwerp ontwikkelen dat de Forms-service in verschillende browseromgevingen weergeeft in PDF, SWF of HTML.
uuid: 68d7b7bc-7730-4a83-b7b9-ebe2a29d6c51
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/performing_service_operations_using_apis
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
discoiquuid: f8749793-e53f-4812-a093-8278f480e6a8
translation-type: tm+mt
source-git-commit: 9cf46a26d2aa2e41b924a4de89cf8ab5fdeeefc6
workflow-type: tm+mt
source-wordcount: '656'
ht-degree: 0%

---


# Forms {#rendering-forms} renderen

**Voorbeelden en voorbeelden in dit document gelden alleen voor AEM Forms in JEE-omgeving.**

**Informatie over de Forms-service**

Met de Forms-service kunt u interactieve toepassingen voor het vastleggen van gegevens maken die formulieren valideren, verwerken, transformeren en leveren die normaal gesproken in Designer zijn gemaakt. Formulierauteurs kunnen één formulierontwerp ontwikkelen dat de Forms-service in verschillende browseromgevingen weergeeft in PDF, SWF of HTML.

Wanneer een eindgebruiker een formulier aanvraagt, stuurt een clienttoepassing de aanvraag naar de Forms-service, die het formulier in de juiste indeling retourneert. Zodra de Forms-service een aanvraag ontvangt, worden gegevens met een formulierontwerp samengevoegd en wordt het formulier in de gewenste indeling geleverd. De uitvoer van de formulierservice is een interactief formulier, meestal een PDF-document. Met een interactief formulier kunnen gebruikers de velden op het formulier invullen.

Afhankelijk van het type clienttoepassing kunt u het formulier naar een clientwebbrowser schrijven of het formulier opslaan als een PDF-bestand. Een webtoepassing kan het formulier naar een webbrowser schrijven. Een bureaubladtoepassing kan het formulier opslaan als een PDF-bestand. Als u wilt aantonen hoe u gegevens naar een webbrowser en een PDF-bestand schrijft, wordt het snelstarten in de sectie *Forms renderen* als volgt geordend:

* De sterk getypte Java API-voorbeelden (SOAP-modus) zijn een Java-servlet.
* De voorbeelden van de webservice (Java Base64) zijn een Java-servlet.
* De voorbeelden van de Webdienst (MTOM) zijn een consoletoepassing (niet alle snelle begin hebben een voorbeeld MTOM).

>[!NOTE]
>
>Zie [Webtoepassingen maken die Forms](/help/forms/developing/creating-web-applications-renders-forms.md) renderen voor informatie over het maken van een webtoepassing die Java-servlets gebruikt om de Forms-service aan te roepen.

U kunt op twee manieren een formulierontwerp (een XDP-bestand) of een PDF-document doorgeven aan de Forms-service:

* U kunt naar het formulierontwerp verwijzen met een URL-waarde. Deze benadering omvat het gebruik van een `URLSpec`-object. De inhoudsbasis wordt aan de Forms-service doorgegeven met de methode `setContentRootURI` van het object. `URLSpec` De naam van het formulierontwerp ( `formQuery`) wordt doorgegeven als een afzonderlijke parameter. De twee waarden worden samengevoegd om de absolute verwijzing naar het formulierontwerp te verkrijgen. (De meeste snelle start bevindt zich in de sectie *Forms* renderen gebruikt deze benadering.)
* U kunt een `com.adobe.idp.Document` met het formulierontwerp doorgeven aan de Forms-service. Twee nieuwe methoden met de naam `renderPDFForm2` en `renderHTMLForm2` accepteren een `com.adobe.idp.Document`-object dat een formulierontwerp bevat. (Zie [Documenten doorgeven aan de Forms Service](/help/forms/developing/passing-documents-forms-service.md)

U kunt deze taken uitvoeren met de Forms-service:

* Interactieve PDF forms renderen. (Zie [Interactieve PDF forms renderen](/help/forms/developing/rendering-interactive-pdf-forms.md).)
* Formulieren weergeven op de client. (Zie [Forms renderen op de client](/help/forms/developing/rendering-forms-client.md).)
* Formulieren weergeven op basis van fragmenten. (Zie [Forms renderen op basis van fragmenten](/help/forms/developing/rendering-forms-based-fragments.md).)
* Formulieren met rechten weergeven. (Zie [Forms](/help/forms/developing/rendering-rights-enabled-forms.md) renderen met rechten ingeschakeld.)
* Formulieren weergeven als HTML. (Zie [Forms renderen als HTML](/help/forms/developing/rendering-forms-html.md).)
* HTML Forms renderen met aangepaste CSS-bestanden ([HTML Forms renderen met aangepaste CSS-bestanden](/help/forms/developing/rendering-html-forms-using-custom.md).)
* Ingevulde formulieren verwerken. (Zie [Ingediende Forms verwerken](/help/forms/developing/handling-submitted-forms.md).)
* PDF-documenten maken met verzonden XML-gegevens. (Zie [PDF-documenten maken met verzonden XML-gegevens](/help/forms/developing/creating-pdf-documents-submitted-xml.md).)
* Formulieren vooraf invullen. (Zie [Forms vooraf vullen met stroombare layouts](/help/forms/developing/prepopulating-forms-flowable-layouts.md).)
* Documenten doorgeven. (Zie [Documenten doorgeven aan de Forms Service](/help/forms/developing/passing-documents-forms-service.md)
* Formuliergegevens berekenen. (Zie [Formuliergegevens berekenen](/help/forms/developing/calculating-form-data.md).)
* Optimaliseer een toepassing. (Zie [De prestaties van de Forms-service optimaliseren](/help/forms/developing/optimizing-performance-forms-service.md).)

   ***Tip **: De website van de Ontwikkelaar van Adobe bevat het volgende artikel dat bespreekt hoe te om een toepassing tot stand te brengen ASP.NET die de dienst van Forms aanhaalt en vormen teruggeeft. Zie [Creating form rendering ASP.NET applications](https://www.adobe.com/devnet/livecycle/articles/asp_net.html).*

