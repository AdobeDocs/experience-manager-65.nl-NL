---
title: Forms renderen
description: Met de Forms-service kunt u interactieve gegevensvastleggingsclienttoepassingen maken die formulieren valideren, verwerken, transformeren en leveren die gewoonlijk in Designer zijn gemaakt. Formulierauteurs kunnen één formulierontwerp ontwikkelen dat de Forms-service in verschillende browseromgevingen rendert in PDF, SWF of HTML.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/performing_service_operations_using_apis
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: operations
role: Developer
exl-id: ec9ccf04-7cec-493a-91ab-0e399a905338
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
source-git-commit: 939a2efa64c853928a9082aa30d7338e98deb695
workflow-type: tm+mt
source-wordcount: '569'
ht-degree: 0%

---

# Forms renderen {#rendering-forms}

**de Steekproeven en de voorbeelden in dit document zijn slechts voor AEM Forms op milieu JEE.**

**Ongeveer de dienst van Forms**

Met de Forms-service kunt u interactieve toepassingen voor het vastleggen van gegevens maken die formulieren valideren, verwerken, transformeren en leveren die gewoonlijk in Designer zijn gemaakt. Formulierauteurs kunnen één formulierontwerp ontwikkelen dat de Forms-service in verschillende browseromgevingen rendert in PDF, SWF of HTML.

Wanneer een eindgebruiker een formulier aanvraagt, stuurt een clienttoepassing de aanvraag naar de Forms-service, die het formulier in de juiste indeling retourneert. Zodra de Forms-service een aanvraag ontvangt, worden gegevens met een formulierontwerp samengevoegd en wordt het formulier in de gewenste indeling geleverd. De uitvoer van de formulierservice is een interactief formulier, meestal een PDF-document. Met een interactief formulier kunnen gebruikers de velden op het formulier invullen.

Afhankelijk van het type clienttoepassing kunt u het formulier naar een clientwebbrowser schrijven of het formulier opslaan als een PDF-bestand. Een webtoepassing kan het formulier naar een webbrowser schrijven. Een bureaubladtoepassing kan het formulier opslaan als een PDF-bestand. Om aan te tonen hoe te om aan Webbrowser en aan een dossier van PDF te schrijven, begint het snelle begin in *het Teruggeven van Forms* sectie wordt georganiseerd op de volgende manier:

* De sterk getypte Java API-voorbeelden (SOAP modus) zijn een Java-servlet.
* De voorbeelden van de webservice (Java Base64) zijn een Java-servlet.
* De voorbeelden van de Webdienst (MTOM) zijn een consoletoepassing (niet alle snelle begin hebben een voorbeeld MTOM).

>[!NOTE]
>
>Voor informatie over het creëren van een Webtoepassing die Java servlets gebruikt om de dienst van Forms aan te halen, zie [&#x200B; Creërend de Toepassingen van het Web die Forms &#x200B;](/help/forms/developing/creating-web-applications-renders-forms.md) teruggeven.

U kunt op twee manieren een formulierontwerp (een XDP-bestand) of een PDF-document doorgeven aan de Forms-service:

* U kunt naar het formulierontwerp verwijzen met een URL-waarde. Deze aanpak omvat het gebruik van een `URLSpec` -object. De basisinhoud wordt aan de Forms-service doorgegeven met de methode `setContentRootURI` van het object `URLSpec` . De naam van het formulierontwerp ( `formQuery` ) wordt doorgegeven als een aparte parameter. De twee waarden worden samengevoegd om de absolute verwijzing naar het formulierontwerp te verkrijgen. (Het grootste deel van het snelle begin in *teruggevend Forms* sectie gebruikt deze benadering.)
* U kunt een `com.adobe.idp.Document` met het formulierontwerp doorgeven aan de Forms-service. Twee nieuwe methoden met de naam `renderPDFForm2` en `renderHTMLForm2` accepteren een `com.adobe.idp.Document` -object dat een formulierontwerp bevat. (Zie [&#x200B; het overgaan van Documenten tot de Dienst van Forms &#x200B;](/help/forms/developing/passing-documents-forms-service.md)

U kunt deze taken uitvoeren met de Forms-service:

* Interactieve PDF forms renderen. (Zie [&#x200B; teruggevend Interactieve PDF forms &#x200B;](/help/forms/developing/rendering-interactive-pdf-forms.md).)
* Formulieren weergeven op de client. (Zie [&#x200B; teruggevend Forms bij de Cliënt &#x200B;](/help/forms/developing/rendering-forms-client.md).)
* Formulieren weergeven op basis van fragmenten. (Zie [&#x200B; teruggevend Forms dat op Fragments &#x200B;](/help/forms/developing/rendering-forms-based-fragments.md) wordt gebaseerd.)
* Formulieren met rechten weergeven. (Zie [&#x200B; teruggevend rechten-Toegelaten Forms &#x200B;](/help/forms/developing/rendering-rights-enabled-forms.md).)
* Formulieren weergeven als HTML. (Zie [&#x200B; teruggevend Forms als HTML &#x200B;](/help/forms/developing/rendering-forms-html.md).)
* Het teruggeven van HTML Forms die de Dossiers van CSS van de Douane gebruiken ([&#x200B; teruggevend HTML Forms gebruikend de Dossiers van douaneCSS &#x200B;](/help/forms/developing/rendering-html-forms-using-custom.md).)
* Ingevulde formulieren verwerken. (Zie [&#x200B; Behandelend Voorgelegde Forms &#x200B;](/help/forms/developing/handling-submitted-forms.md).)
* PDF-documenten maken met verzonden XML-gegevens. (Zie [&#x200B; Creërend de Documenten van de PDF met Voorgelegde Gegevens van XML &#x200B;](/help/forms/developing/creating-pdf-documents-submitted-xml.md).)
* Formulieren vooraf invullen. (Zie [&#x200B; Prepopulating Forms met Stroombare Lay-outs &#x200B;](/help/forms/developing/prepopulating-forms-flowable-layouts.md).)
* Documenten doorgeven. (Zie [&#x200B; het overgaan van Documenten tot de Dienst van Forms &#x200B;](/help/forms/developing/passing-documents-forms-service.md)
* Formuliergegevens berekenen. (Zie [&#x200B; Berekend de Gegevens van de Vorm &#x200B;](/help/forms/developing/calculating-form-data.md).)
* Optimaliseer een toepassing. (Zie [&#x200B; Optimizing de Prestaties van de Dienst van Forms &#x200B;](/help/forms/developing/optimizing-performance-forms-service.md).)
