---
title: Forms met rechten voor renderen
description: Gebruik de Forms-service om formulieren te genereren waarop gebruiksrechten zijn toegepast. U kunt formulieren met ingeschakelde rechten weergeven met de API van Java API en de webservice.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
exl-id: 012a3a9f-542c-4ed1-a092-572bfccbdf21
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Document Services,APIs & Integrations
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '1447'
ht-degree: 0%

---

# Forms met rechten voor renderen {#rendering-rights-enabled-forms}

De Forms-service kan formulieren weergeven waarop gebruiksrechten zijn toegepast. Gebruiksrechten hebben betrekking op functionaliteit die standaard beschikbaar is in Acrobat, maar niet in Adobe Reader, zoals de mogelijkheid om opmerkingen toe te voegen aan een formulier of formuliervelden in te vullen en het formulier op te slaan. Forms waarop gebruiksrechten zijn toegepast, worden formulieren genoemd die geschikt zijn voor rechten. Een gebruiker die een formulier met ingeschakelde rechten opent in Adobe Reader, kan bewerkingen uitvoeren die zijn ingeschakeld voor dat formulier.

Als u gebruiksrechten wilt toepassen op een formulier, moet de Acrobat Reader DC-extensieservice onderdeel zijn van de installatie van AEM formulieren. Bovendien moet u een geldige referentie hebben waarmee u gebruiksrechten kunt toepassen op PDF-documenten. Dit betekent dat u de Acrobat Reader DC-extensieservice op de juiste wijze moet configureren voordat u een formulier met ingeschakelde rechten kunt genereren. (Zie [ Ongeveer de de uitbreidingsdienst van Acrobat Reader DC ](/help/forms/developing/assigning-usage-rights.md#about-the-acrobat-reader-dc-extensions-service).)

>[!NOTE]
>
>Als u een formulier wilt genereren dat gebruiksrechten bevat, moet u een XDP-bestand als invoer gebruiken, niet als een PDF-bestand. Als u een PDF-bestand als invoer gebruikt, wordt het formulier nog steeds gegenereerd. Het is echter geen formulier waarvoor rechten zijn ingeschakeld.

>[!NOTE]
>
>U kunt een formulier niet vooraf invullen met XML-gegevens wanneer u de volgende gebruiksrechten opgeeft: `enableComments`, `enableCommentsOnline`, `enableEmbeddedFiles` of `enableDigitalSignatures` . (Zie [ Prepopulating Forms met Stroombare Lay-outs ](/help/forms/developing/prepopulating-forms-flowable-layouts.md).)

>[!NOTE]
>
>Voor meer informatie over de dienst van Forms, zie [ Verwijzing van de Diensten voor AEM Forms ](https://www.adobe.com/go/learn_aemforms_services_63).

## Overzicht van de stappen {#summary-of-steps}

Voer de volgende taken uit om een formulier waarvoor rechten zijn ingeschakeld, te genereren:

1. Inclusief projectbestanden.
1. Maak een Forms Client API-object.
1. Stel uitvoeringsopties voor gebruiksrechten in.
1. Een formulier met ingeschakelde rechten weergeven.
1. Schrijf het formulier waarvoor rechten zijn ingeschakeld naar de webbrowser van de client.

**omvat projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

**creeer een voorwerp van Forms Cliënt API**

Voordat u programmatisch een client-API-bewerking voor Forms-services kunt uitvoeren, moet u een Forms-serviceclient maken.

**plaats runtime opties van gebruiksrechten**

Stel uitvoeringsopties voor gebruiksrechten in om een formulier met toegangsrechten te genereren. Geef de alias op van de referentie die wordt gebruikt om gebruiksrechten toe te passen op een formulier. Nadat u de alias-waarde hebt opgegeven, geeft u elk gebruiksrecht op dat u op het formulier wilt toepassen.

**geef een recht-toegelaten vorm** terug

Als u een formulier met ingeschakelde rechten wilt genereren, gebruikt u dezelfde toepassingslogica als voor het weergeven van een formulier zonder gebruiksrechten. Het enige verschil is dat u ervoor moet zorgen dat de gebruiksrechten tijdens runtime opties zijn opgenomen in uw toepassingslogica.

>[!NOTE]
>
>Als u een formulier met toegangsrechten weergeeft met de Forms-API voor webservices, kunt u geen bestanden aan het formulier koppelen.

**schrijf de stroom van vormgegevens aan cliëntWeb browser**

Wanneer een formulier waarvoor rechten zijn ingeschakeld door de Forms-service wordt gegenereerd, wordt een formuliergegevensstroom geretourneerd die u moet schrijven naar de webbrowser van de client. Nadat het formulier naar de webbrowser van de client is geschreven, is het zichtbaar voor de gebruiker. Een gebruiker die het voor rechten ingeschakelde formulier in Adobe Reader weergeeft, kan bewerkingen uitvoeren die zijn ingeschakeld voor dat formulier.

**zie ook**

[Formulieren waarvoor rechten zijn ingeschakeld, renderen met de Java API](#render-rights-enabled-forms-using-the-java-api)

[Formulieren waarvoor rechten zijn ingeschakeld, renderen met de API voor webservices](#render-rights-enabled-forms-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Forms Service API Quick Start](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

[Interactieve PDF forms renderen](/help/forms/developing/rendering-interactive-pdf-forms.md)

[Webtoepassingen maken die Forms renderen](/help/forms/developing/creating-web-applications-renders-forms.md)

### Formulieren waarvoor rechten zijn ingeschakeld, renderen met de Java API {#render-rights-enabled-forms-using-the-java-api}

Een formulier met ingeschakelde rechten weergeven met de Forms API (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden, zoals adobe-forms-client.jar, op in het klassepad van uw Java-project.

1. Een Forms Client API-object maken

   * Maak een `ServiceClientFactory` -object dat verbindingseigenschappen bevat.
   * Maak een `FormsServiceClient` -object door de constructor ervan te gebruiken en het `ServiceClientFactory` -object door te geven.

1. Opties voor het uitvoeren van gebruiksrechten instellen

   * Maak een `ReaderExtensionSpec` -object met behulp van de constructor.
   * Geef de alias van de referentie op door de methode `setReCredentialAlias` van het object `ReaderExtensionSpec` aan te roepen en geef een tekenreekswaarde op die de aliaswaarde vertegenwoordigt.
   * Stel elk gebruiksrecht in door de bijbehorende methode aan te roepen die bij het object `ReaderExtensionSpec` hoort. U kunt echter alleen een gebruiksrecht instellen als de referentie die u gebruikt dat toestaat. U kunt dus geen gebruiksrecht instellen als de referentie dit niet toestaat. Bijvoorbeeld. Als u het gebruiksrecht wilt instellen waarmee een gebruiker formuliervelden kan invullen en het formulier kan opslaan, roept u de methode `setReFillIn` van het object `ReaderExtensionSpec` aan en geeft u dit door `true` .

   >[!NOTE]
   >
   >U hoeft de methode `setReCredentialPassword` van het object `ReaderExtensionSpec` niet op te roepen. Deze methode wordt niet gebruikt door de Forms-service.

1. Een formulier met ingeschakelde rechten weergeven

   Roep de methode `renderPDFFormWithUsageRights` van het object `FormsServiceClient` aan en geef de volgende waarden door:

   * Een tekenreekswaarde die de naam van het formulierontwerp opgeeft, inclusief de bestandsnaamextensie. Als u verwijst naar een formulierontwerp dat deel uitmaakt van een Forms-toepassing, moet u het volledige pad opgeven, bijvoorbeeld `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp` .
   * Een `com.adobe.idp.Document` -object dat gegevens bevat die met het formulier moeten worden samengevoegd. Wanneer u geen gegevens wilt samenvoegen, geeft u een leeg `com.adobe.idp.Document` -object door.
   * Een `PDFFormRenderSpec` -object dat uitvoeringsopties opslaat.
   * Een `ReaderExtensionSpec` -object dat gebruiksrechten opslaat.
   * Een `URLSpec` -object dat URI-waarden bevat die door de Forms-service worden vereist.

   De methode `renderPDFFormWithUsageRights` retourneert een `FormsResult` -object dat een formuliergegevensstroom bevat die naar de webbrowser van de client moet worden geschreven.

1. De formuliergegevensstroom naar de webbrowser van de client schrijven

   * Maak een `com.adobe.idp.Document` -object door de methode `FormsResult` object `getOutputContent` aan te roepen.
   * Haal het inhoudstype van het object `com.adobe.idp.Document` op door de methode `getContentType` ervan aan te roepen.
   * Stel het inhoudstype van het `javax.servlet.http.HttpServletResponse` -object in door de methode `setContentType` ervan aan te roepen en het inhoudstype van het `com.adobe.idp.Document` -object door te geven.
   * Maak een `javax.servlet.ServletOutputStream` -object dat wordt gebruikt om de formuliergegevensstroom naar de webbrowser van de client te schrijven door de methode `javax.servlet.http.HttpServletResponse` object `getOutputStream` aan te roepen.
   * Maak een `java.io.InputStream` -object door de methode `com.adobe.idp.Document` object `getInputStream` aan te roepen.
   * Maak een bytearray die deze met de gegevensstroom van het formulier vult door de methode `read` van het object `InputStream` aan te roepen en de bytearray door te geven als een argument.
   * Roep de methode `write` van het object `javax.servlet.ServletOutputStream` aan om de gegevensstroom van het formulier naar de webbrowser van de client te verzenden. Geef de bytearray door aan de methode `write` .

**zie ook**

[Snel starten (SOAP modus): Een formulier waarvoor rechten zijn ingeschakeld, weergeven met de Java API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-rendering-a-rights-enabled-form-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Formulieren waarvoor rechten zijn ingeschakeld, renderen met de API voor webservices {#render-rights-enabled-forms-using-the-web-service-api}

Een formulier met ingeschakelde rechten weergeven met de Forms API (webservice):

1. Projectbestanden opnemen

   * Maak Java-proxyklassen die gebruikmaken van de Forms-service WSDL.
   * Neem de Java-proxyklassen op in het klassepad.

1. Een Forms Client API-object maken

   Maak een `FormsService` -object en stel de verificatiewaarden in.

1. Opties voor het uitvoeren van gebruiksrechten instellen

   * Maak een `ReaderExtensionSpec` -object met behulp van de constructor.
   * Geef de alias van de referentie op door de methode `setReCredentialAlias` van het object `ReaderExtensionSpec` aan te roepen en geef een tekenreekswaarde op die de aliaswaarde vertegenwoordigt.
   * Stel elk gebruiksrecht in door de bijbehorende methode aan te roepen die bij het object `ReaderExtensionSpec` hoort. U kunt echter alleen een gebruiksrecht instellen als de referentie die u gebruikt dat toestaat. U kunt dus geen gebruiksrecht instellen als de referentie dit niet toestaat. Als u het gebruiksrecht wilt instellen waarmee een gebruiker formuliervelden kan invullen en het formulier kan opslaan, roept u de methode `setReFillIn` van het object `ReaderExtensionSpec` aan en geeft u `true` door.

1. Een formulier met ingeschakelde rechten weergeven

   Roep de methode `renderPDFFormWithUsageRights` van het object `FormsService` aan en geef de volgende waarden door:

   * Een tekenreekswaarde die de naam van het formulierontwerp opgeeft, inclusief de bestandsnaamextensie. Als u verwijst naar een formulierontwerp dat deel uitmaakt van een Forms-toepassing, moet u het volledige pad opgeven, bijvoorbeeld `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp` .
   * Een `BLOB` -object dat gegevens bevat die met het formulier moeten worden samengevoegd. Als u geen gegevens wilt samenvoegen met het formulier, moet u een `BLOB` -object doorgeven dat is gebaseerd op een lege XML-gegevensbron. U kunt geen `BLOB` -object doorgeven dat null is; anders wordt een uitzondering gegenereerd.
   * Een `PDFFormRenderSpec` -object dat uitvoeringsopties opslaat.
   * Een `ReaderExtensionSpec` -object dat gebruiksrechten opslaat.
   * Een `URLSpec` -object dat URI-waarden bevat die door de Forms-service worden vereist.

   De methode `renderPDFFormWithUsageRights` retourneert een `FormsResult` -object dat een formuliergegevensstroom bevat die naar de webbrowser van de client moet worden geschreven.

1. De formuliergegevensstroom naar de webbrowser van de client schrijven

   * Maak een `BLOB` -object dat formuliergegevens bevat door de methode `FormsResult` object `getOutputContent` aan te roepen.
   * Haal het inhoudstype van het object `BLOB` op door de methode `getContentType` ervan aan te roepen.
   * Stel het inhoudstype van het `javax.servlet.http.HttpServletResponse` -object in door de methode `setContentType` ervan aan te roepen en het inhoudstype van het `BLOB` -object door te geven.
   * Maak een `javax.servlet.ServletOutputStream` -object dat wordt gebruikt om de formuliergegevensstroom naar de webbrowser van de client te schrijven door de methode `javax.servlet.http.HttpServletResponse` object `getOutputStream` aan te roepen.
   * Maak een bytearray en vul deze door de methode `getBinaryData` van het object `BLOB` aan te roepen. Hierdoor wordt de inhoud van het `FormsResult` -object toegewezen aan de bytearray.
   * Roep de methode `write` van het object `javax.servlet.http.HttpServletResponse` aan om de gegevensstroom van het formulier naar de webbrowser van de client te verzenden. Geef de bytearray door aan de methode `write` .

**zie ook**

[Forms met rechten voor renderen](#rendering-rights-enabled-forms)

[AEM Forms aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
