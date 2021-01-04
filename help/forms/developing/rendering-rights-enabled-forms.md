---
title: Forms met renderrechten
seo-title: Forms met renderrechten
description: Gebruik de Forms-service om formulieren te genereren waarop gebruiksrechten zijn toegepast. U kunt formulieren met ingeschakelde rechten weergeven met de API van Java API en de webservice.
seo-description: Gebruik de Forms-service om formulieren te genereren waarop gebruiksrechten zijn toegepast. U kunt formulieren met ingeschakelde rechten weergeven met de API van Java API en de webservice.
uuid: ce5e4be6-d9b0-4989-a0e1-a8c3b98aed77
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: d4c2b2f0-613a-409d-b39b-8e37fdb96eea
translation-type: tm+mt
source-git-commit: 07889ead2ae402b5fb738ca08c7efe076ef33e44
workflow-type: tm+mt
source-wordcount: '1493'
ht-degree: 0%

---


# Forms {#rendering-rights-enabled-forms} met rechten voor renderen

De Forms-service kan formulieren weergeven waarop gebruiksrechten zijn toegepast. Gebruiksrechten hebben betrekking op functionaliteit die standaard beschikbaar is in Acrobat, maar niet in Adobe Reader, zoals de mogelijkheid om opmerkingen toe te voegen aan een formulier of formuliervelden in te vullen en het formulier op te slaan. Forms waarop gebruiksrechten zijn toegepast, worden formulieren genoemd die geschikt zijn voor rechten. Een gebruiker die een formulier met ingeschakelde rechten opent in Adobe Reader, kan bewerkingen uitvoeren die zijn ingeschakeld voor dat formulier.

Als u gebruiksrechten wilt toepassen op een formulier, moet de Acrobat Reader DC-extensieservice onderdeel zijn van de installatie van uw AEM. Bovendien moet u beschikken over een geldige referentie waarmee u gebruiksrechten kunt toepassen op PDF-documenten. Dit betekent dat u de Acrobat Reader DC-extensieservice op de juiste wijze moet configureren voordat u een formulier met ingeschakelde rechten kunt genereren. (Zie [Informatie over de Acrobat Reader DC Extension Service](/help/forms/developing/assigning-usage-rights.md#about-the-acrobat-reader-dc-extensions-service).)

>[!NOTE]
>
>Als u een formulier wilt genereren dat gebruiksrechten bevat, moet u een XDP-bestand als invoer gebruiken, niet als een PDF-bestand. Als u een PDF-bestand als invoer gebruikt, wordt het formulier nog steeds gegenereerd. het is echter geen formulier waarvoor rechten gelden.

>[!NOTE]
>
>U kunt een formulier niet vooraf invullen met XML-gegevens als u de volgende gebruiksrechten opgeeft: `enableComments`, `enableCommentsOnline`, `enableEmbeddedFiles` of `enableDigitalSignatures`. (Zie [Forms vooraf vullen met stroombare layouts](/help/forms/developing/prepopulating-forms-flowable-layouts.md).)

>[!NOTE]
>
>Zie [Referentiehandleiding voor services voor AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63) voor meer informatie over de Forms-service.

## Overzicht van stappen {#summary-of-steps}

Voer de volgende taken uit om een formulier waarvoor rechten zijn ingeschakeld, te genereren:

1. Inclusief projectbestanden.
1. Maak een Forms Client API-object.
1. Stel uitvoeringsopties voor gebruiksrechten in.
1. Een formulier met ingeschakelde rechten weergeven.
1. Schrijf het formulier waarvoor rechten zijn ingeschakeld naar de webbrowser van de client.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

**Een Forms Client API-object maken**

Voordat u programmatisch een client-API-bewerking voor Forms-services kunt uitvoeren, moet u een Forms-serviceclient maken.

**Opties voor het uitvoeren van gebruiksrechten instellen**

U moet de runtime van gebruiksrechten opties plaatsen om een recht-Toegelaten vorm terug te geven. U moet ook de alias van de referentie opgeven die wordt gebruikt om gebruiksrechten toe te passen op een formulier. Nadat u de alias-waarde hebt opgegeven, geeft u elk gebruiksrecht op dat u op het formulier wilt toepassen.

**Een formulier met ingeschakelde rechten weergeven**

Als u een formulier met ingeschakelde rechten wilt genereren, gebruikt u dezelfde toepassingslogica als voor het weergeven van een formulier zonder gebruiksrechten. Het enige verschil is dat u ervoor moet zorgen dat de gebruiksrechten tijdens runtime opties zijn opgenomen in uw toepassingslogica.

>[!NOTE]
>
>Als u een formulier met toegangsrechten weergeeft met de Forms-API voor webservices, kunt u geen bestanden aan het formulier koppelen.

**De formuliergegevensstroom naar de webbrowser van de client schrijven**

Wanneer een formulier waarvoor rechten zijn ingeschakeld door de Forms-service wordt gegenereerd, wordt een formuliergegevensstroom geretourneerd die u moet schrijven naar de webbrowser van de client. Nadat het formulier naar de webbrowser van de client is geschreven, is het zichtbaar voor de gebruiker. Een gebruiker die het voor rechten ingeschakelde formulier in Adobe Reader weergeeft, kan bewerkingen uitvoeren die zijn ingeschakeld voor dat formulier.

**Zie ook**

[Formulieren waarvoor rechten zijn ingeschakeld, renderen met de Java API](#render-rights-enabled-forms-using-the-java-api)

[Formulieren waarvoor rechten zijn ingeschakeld, renderen met de API voor webservices](#render-rights-enabled-forms-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Forms Service API Quick Start](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

[Interactieve PDF forms renderen](/help/forms/developing/rendering-interactive-pdf-forms.md)

[Webtoepassingen maken die Forms renderen](/help/forms/developing/creating-web-applications-renders-forms.md)

### Formulieren waarvoor rechten zijn ingeschakeld, weergeven met de Java API {#render-rights-enabled-forms-using-the-java-api}

Een formulier met ingeschakelde rechten weergeven met de Forms API (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden, zoals adobe-forms-client.jar, op in het klassenpad van uw Java-project.

1. Een Forms Client API-object maken

   * Maak een `ServiceClientFactory`-object dat verbindingseigenschappen bevat.
   * Maak een `FormsServiceClient`-object door de constructor ervan te gebruiken en het object `ServiceClientFactory` door te geven.

1. Opties voor het uitvoeren van gebruiksrechten instellen

   * Maak een `ReaderExtensionSpec`-object met de constructor ervan.
   * Geef de alias van de referentie op door de methode `setReCredentialAlias` van het object `ReaderExtensionSpec` aan te roepen en geef een tekenreekswaarde op die de aliaswaarde vertegenwoordigt.
   * Plaats elk gebruiksrecht door de overeenkomstige methode aan te halen die tot het `ReaderExtensionSpec` voorwerp behoort. U kunt echter alleen een gebruiksrecht instellen als de referentie die u gebruikt dit toestaat. U kunt dus geen gebruiksrecht instellen als de referentie het instellen niet toestaat. Bijvoorbeeld. Als u het gebruiksrecht wilt instellen waarmee een gebruiker formuliervelden kan invullen en het formulier kan opslaan, roept u de methode `setReFillIn` van het object `ReaderExtensionSpec` aan en geeft u `true` door.

   >[!NOTE]
   >
   >Het is niet nodig om de methode `setReCredentialPassword` van het `ReaderExtensionSpec` voorwerp aan te halen. Deze methode wordt niet gebruikt door de Forms-service.

1. Een formulier met ingeschakelde rechten weergeven

   Roep de methode `renderPDFFormWithUsageRights` van het object `FormsServiceClient` aan en geef de volgende waarden door:

   * Een tekenreekswaarde die de naam van het formulierontwerp opgeeft, inclusief de bestandsnaamextensie. Als u naar een formulierontwerp verwijst dat deel uitmaakt van een Forms-toepassing, moet u het volledige pad opgeven, bijvoorbeeld `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * Een object `com.adobe.idp.Document` dat gegevens bevat die met het formulier moeten worden samengevoegd. Als u geen gegevens wilt samenvoegen, geeft u een leeg `com.adobe.idp.Document`-object door.
   * Een `PDFFormRenderSpec`-object dat uitvoeringsopties opslaat.
   * Een `ReaderExtensionSpec`-object dat gebruiksrechten opslaat tijdens runtime.
   * Een object `URLSpec` dat URI-waarden bevat die door de Forms-service worden vereist.

   De methode `renderPDFFormWithUsageRights` retourneert een `FormsResult`-object dat een formuliergegevensstroom bevat die naar de webbrowser van de client moet worden geschreven.

1. De formuliergegevensstroom naar de webbrowser van de client schrijven

   * Maak een `com.adobe.idp.Document`-object door de methode `getOutputContent` van het object aan te roepen.`FormsResult`
   * Hiermee wordt het inhoudstype van het object `com.adobe.idp.Document` opgehaald door de methode `getContentType` ervan aan te roepen.
   * Stel het inhoudstype van het object `javax.servlet.http.HttpServletResponse` in door de methode `setContentType` ervan aan te roepen en het inhoudstype van het object `com.adobe.idp.Document` door te geven.
   * Maak een `javax.servlet.ServletOutputStream`-object dat wordt gebruikt om de formuliergegevensstroom naar de webbrowser van de client te schrijven door de methode `javax.servlet.http.HttpServletResponse` van het object `getOutputStream` aan te roepen.
   * Maak een `java.io.InputStream`-object door de methode `getInputStream` van het object `com.adobe.idp.Document` aan te roepen.
   * Maak een bytearray die deze met de formuliergegevensstroom vult door de methode `read` van het object `InputStream` aan te roepen en de bytearray als een argument door te geven.
   * Roep de methode `javax.servlet.ServletOutputStream` van het object `write` aan om de gegevensstroom van het formulier naar de webbrowser van de client te verzenden. Geef de bytearray door aan de methode `write`.

**Zie ook**

[Snel starten (SOAP-modus): Een formulier waarvoor rechten zijn ingeschakeld weergeven met de Java API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-rendering-a-rights-enabled-form-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Formulieren waarvoor rechten zijn ingeschakeld, weergeven met de API {#render-rights-enabled-forms-using-the-web-service-api} van de webservice

Een formulier met ingeschakelde rechten weergeven met de Forms API (webservice):

1. Projectbestanden opnemen

   * Maak Java-proxyklassen die gebruikmaken van de Forms-service WSDL.
   * Neem de Java-proxyklassen op in het klassepad.

1. Een Forms Client API-object maken

   Maak een `FormsService`-object en stel de verificatiewaarden in.

1. Opties voor het uitvoeren van gebruiksrechten instellen

   * Maak een `ReaderExtensionSpec`-object met de constructor ervan.
   * Geef de alias van de referentie op door de methode `setReCredentialAlias` van het object `ReaderExtensionSpec` aan te roepen en geef een tekenreekswaarde op die de aliaswaarde vertegenwoordigt.
   * Plaats elk gebruiksrecht door de overeenkomstige methode aan te halen die tot het `ReaderExtensionSpec` voorwerp behoort. U kunt echter alleen een gebruiksrecht instellen als de referentie die u gebruikt dit toestaat. U kunt dus geen gebruiksrecht instellen als de referentie het instellen niet toestaat. Als u het gebruiksrecht wilt instellen waarmee een gebruiker formuliervelden kan invullen en het formulier kan opslaan, roept u de methode `setReFillIn` van het object `ReaderExtensionSpec` aan en geeft u `true` door.

1. Een formulier met ingeschakelde rechten weergeven

   Roep de methode `renderPDFFormWithUsageRights` van het object `FormsService` aan en geef de volgende waarden door:

   * Een tekenreekswaarde die de naam van het formulierontwerp opgeeft, inclusief de bestandsnaamextensie. Als u naar een formulierontwerp verwijst dat deel uitmaakt van een Forms-toepassing, moet u het volledige pad opgeven, bijvoorbeeld `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * Een object `BLOB` dat gegevens bevat die met het formulier moeten worden samengevoegd. Als u geen gegevens wilt samenvoegen met het formulier, moet u een `BLOB`-object doorgeven dat is gebaseerd op een lege XML-gegevensbron. U kunt geen `BLOB` voorwerp overgaan dat ongeldig is; anders wordt een uitzondering gegenereerd.
   * Een `PDFFormRenderSpec`-object dat uitvoeringsopties opslaat.
   * Een `ReaderExtensionSpec`-object dat gebruiksrechten opslaat tijdens runtime.
   * Een object `URLSpec` dat URI-waarden bevat die door de Forms-service worden vereist.

   De methode `renderPDFFormWithUsageRights` retourneert een `FormsResult`-object dat een formuliergegevensstroom bevat die naar de webbrowser van de client moet worden geschreven.

1. De formuliergegevensstroom naar de webbrowser van de client schrijven

   * Maak een `BLOB`-object dat formuliergegevens bevat door de methode `getOutputContent` van het object `FormsResult` aan te roepen.
   * Hiermee wordt het inhoudstype van het object `BLOB` opgehaald door de methode `getContentType` ervan aan te roepen.
   * Stel het inhoudstype van het object `javax.servlet.http.HttpServletResponse` in door de methode `setContentType` ervan aan te roepen en het inhoudstype van het object `BLOB` door te geven.
   * Maak een `javax.servlet.ServletOutputStream`-object dat wordt gebruikt om de formuliergegevensstroom naar de webbrowser van de client te schrijven door de methode `javax.servlet.http.HttpServletResponse` van het object `getOutputStream` aan te roepen.
   * Maak een bytearray en vul deze door de methode `getBinaryData` van het object `BLOB` aan te roepen. Deze taak wijst de inhoud van het `FormsResult` voorwerp aan de byteserie toe.
   * Roep de methode `javax.servlet.http.HttpServletResponse` van het object `write` aan om de gegevensstroom van het formulier naar de webbrowser van de client te verzenden. Geef de bytearray door aan de methode `write`.

**Zie ook**

[Forms met renderrechten](#rendering-rights-enabled-forms)

[AEM Forms aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
