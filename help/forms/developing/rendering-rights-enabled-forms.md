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
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1447'
ht-degree: 0%

---

# Forms met rechten voor renderen {#rendering-rights-enabled-forms}

De Forms-service kan formulieren weergeven waarop gebruiksrechten zijn toegepast. Gebruiksrechten hebben betrekking op functionaliteit die standaard beschikbaar is in Acrobat, maar niet in Adobe Reader, zoals de mogelijkheid om opmerkingen toe te voegen aan een formulier of formuliervelden in te vullen en het formulier op te slaan. Forms waarop gebruiksrechten zijn toegepast, worden formulieren genoemd die geschikt zijn voor rechten. Een gebruiker die een formulier met ingeschakelde rechten opent in Adobe Reader, kan bewerkingen uitvoeren die zijn ingeschakeld voor dat formulier.

Als u gebruiksrechten wilt toepassen op een formulier, moet de Acrobat Reader DC-extensieservice onderdeel zijn van de installatie van AEM formulieren. Bovendien moet u een geldige referentie hebben waarmee u gebruiksrechten kunt toepassen op PDF-documenten. Dit betekent dat u de Acrobat Reader DC-extensieservice op de juiste wijze moet configureren voordat u een formulier met ingeschakelde rechten kunt genereren. (Zie [Over de Acrobat Reader DC-extensieservice](/help/forms/developing/assigning-usage-rights.md#about-the-acrobat-reader-dc-extensions-service).)

>[!NOTE]
>
>Als u een formulier wilt genereren dat gebruiksrechten bevat, moet u een XDP-bestand als invoer gebruiken, niet als een PDF-bestand. Als u een PDF-bestand als invoer gebruikt, wordt het formulier nog steeds gegenereerd. Het is echter geen formulier waarvoor rechten zijn ingeschakeld.

>[!NOTE]
>
>U kunt een formulier niet vooraf invullen met XML-gegevens als u de volgende gebruiksrechten opgeeft: `enableComments`, `enableCommentsOnline`, `enableEmbeddedFiles`, of `enableDigitalSignatures`. (Zie [Forms vooraf vullen met stroombare indelingen](/help/forms/developing/prepopulating-forms-flowable-layouts.md).)

>[!NOTE]
>
>Voor meer informatie over de Forms-service raadpleegt u [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Overzicht van de stappen {#summary-of-steps}

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

Stel uitvoeringsopties voor gebruiksrechten in om een formulier met toegangsrechten te genereren. Geef de alias op van de referentie die wordt gebruikt om gebruiksrechten toe te passen op een formulier. Nadat u de alias-waarde hebt opgegeven, geeft u elk gebruiksrecht op dat u op het formulier wilt toepassen.

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

### Formulieren waarvoor rechten zijn ingeschakeld, renderen met de Java API {#render-rights-enabled-forms-using-the-java-api}

Een formulier met ingeschakelde rechten weergeven met de Forms API (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden, zoals adobe-forms-client.jar, op in het klassepad van uw Java-project.

1. Een Forms Client API-object maken

   * Een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Een `FormsServiceClient` object door de constructor ervan te gebruiken en de `ServiceClientFactory` object.

1. Opties voor het uitvoeren van gebruiksrechten instellen

   * Een `ReaderExtensionSpec` object met behulp van de constructor.
   * Geef de alias van de referentie op door de `ReaderExtensionSpec` object `setReCredentialAlias` en geeft u een tekenreekswaarde op die de aliaswaarde vertegenwoordigt.
   * Plaats elk gebruiksrecht door de overeenkomstige methode aan te halen die tot het behoort `ReaderExtensionSpec` object. U kunt echter alleen een gebruiksrecht instellen als de referentie die u gebruikt dat toestaat. U kunt dus geen gebruiksrecht instellen als de referentie dit niet toestaat. Bijvoorbeeld. om het gebruiksrecht in te stellen waarmee een gebruiker formuliervelden kan invullen en het formulier kan opslaan, roept u de `ReaderExtensionSpec` object `setReFillIn` methode en doorgeven `true`.

   >[!NOTE]
   >
   >Het is niet nodig om de `ReaderExtensionSpec` object `setReCredentialPassword` methode. Deze methode wordt niet gebruikt door de Forms-service.

1. Een formulier met ingeschakelde rechten weergeven

   De `FormsServiceClient` object `renderPDFFormWithUsageRights` en geeft de volgende waarden door:

   * Een tekenreekswaarde die de naam van het formulierontwerp opgeeft, inclusief de bestandsnaamextensie. Als u naar een formulierontwerp verwijst dat deel uitmaakt van een Forms-toepassing, moet u het volledige pad opgeven, zoals `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * A `com.adobe.idp.Document` object dat gegevens bevat die met het formulier moeten worden samengevoegd. Als u geen gegevens wilt samenvoegen, geeft u een lege waarde door `com.adobe.idp.Document` object.
   * A `PDFFormRenderSpec` -object dat uitvoeringsopties opslaat.
   * A `ReaderExtensionSpec` -object dat gebruiksrechten opslaat.
   * A `URLSpec` object dat URI-waarden bevat die door de Forms-service worden vereist.

   De `renderPDFFormWithUsageRights` methode retourneert een `FormsResult` object dat een formuliergegevensstroom bevat die naar de webbrowser van de client moet worden geschreven.

1. De formuliergegevensstroom naar de webbrowser van de client schrijven

   * Een `com.adobe.idp.Document` door het object aan te roepen `FormsResult` object `getOutputContent` methode.
   * Hiermee wordt het inhoudstype van het dialoogvenster `com.adobe.idp.Document` object aanroepen `getContentType` methode.
   * Stel de `javax.servlet.http.HttpServletResponse` inhoudstype van object aanroepen `setContentType` en geeft u het inhoudstype van de `com.adobe.idp.Document` object.
   * Een `javax.servlet.ServletOutputStream` object dat wordt gebruikt om de formuliergegevensstroom naar de webbrowser van de client te schrijven door het aanroepen van de `javax.servlet.http.HttpServletResponse` object `getOutputStream` methode.
   * Een `java.io.InputStream` door het object aan te roepen `com.adobe.idp.Document` object `getInputStream` methode.
   * Maak een bytearray die deze met de formuliergegevensstroom vult door de `InputStream` object `read` en de bytearray doorgeven als een argument.
   * De `javax.servlet.ServletOutputStream` object `write` methode om de formuliergegevensstroom naar de webbrowser van de client te verzenden. Geef de bytearray door aan de `write` methode.

**Zie ook**

[Snel starten (SOAP-modus): Een formulier waarvoor rechten zijn ingeschakeld, weergeven met de Java API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-rendering-a-rights-enabled-form-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Formulieren waarvoor rechten zijn ingeschakeld, renderen met de API voor webservices {#render-rights-enabled-forms-using-the-web-service-api}

Een formulier met ingeschakelde rechten weergeven met de Forms API (webservice):

1. Projectbestanden opnemen

   * Maak Java-proxyklassen die gebruikmaken van de Forms-service WSDL.
   * Neem de Java-proxyklassen op in het klassepad.

1. Een Forms Client API-object maken

   Een `FormsService` -object en stel verificatiewaarden in.

1. Opties voor het uitvoeren van gebruiksrechten instellen

   * Een `ReaderExtensionSpec` object met behulp van de constructor.
   * Geef de alias van de referentie op door de `ReaderExtensionSpec` object `setReCredentialAlias` en geeft u een tekenreekswaarde op die de aliaswaarde vertegenwoordigt.
   * Plaats elk gebruiksrecht door de overeenkomstige methode aan te halen die tot het behoort `ReaderExtensionSpec` object. U kunt echter alleen een gebruiksrecht instellen als de referentie die u gebruikt dat toestaat. U kunt dus geen gebruiksrecht instellen als de referentie dit niet toestaat. Als u het gebruiksrecht wilt instellen waarmee een gebruiker formuliervelden kan invullen en het formulier kan opslaan, roept u het `ReaderExtensionSpec` object `setReFillIn` methode en doorgeven `true`.

1. Een formulier met ingeschakelde rechten weergeven

   De `FormsService` object `renderPDFFormWithUsageRights` en geeft de volgende waarden door:

   * Een tekenreekswaarde die de naam van het formulierontwerp opgeeft, inclusief de bestandsnaamextensie. Als u naar een formulierontwerp verwijst dat deel uitmaakt van een Forms-toepassing, moet u het volledige pad opgeven, zoals `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * A `BLOB` object dat gegevens bevat die met het formulier moeten worden samengevoegd. Als u geen gegevens wilt samenvoegen met het formulier, moet u een `BLOB` object dat is gebaseerd op een lege XML-gegevensbron. U kunt geen `BLOB` object dat null is; anders wordt een uitzondering gegenereerd.
   * A `PDFFormRenderSpec` -object dat uitvoeringsopties opslaat.
   * A `ReaderExtensionSpec` -object dat gebruiksrechten opslaat.
   * A `URLSpec` object dat URI-waarden bevat die door de Forms-service worden vereist.

   De `renderPDFFormWithUsageRights` methode retourneert een `FormsResult` object dat een formuliergegevensstroom bevat die naar de webbrowser van de client moet worden geschreven.

1. De formuliergegevensstroom naar de webbrowser van de client schrijven

   * Een `BLOB` object dat formuliergegevens bevat door het `FormsResult` object `getOutputContent` methode.
   * Hiermee wordt het inhoudstype van het dialoogvenster `BLOB` object aanroepen `getContentType` methode.
   * Stel de `javax.servlet.http.HttpServletResponse` inhoudstype van object aanroepen `setContentType` en geeft u het inhoudstype van de `BLOB` object.
   * Een `javax.servlet.ServletOutputStream` object dat wordt gebruikt om de formuliergegevensstroom naar de webbrowser van de client te schrijven door het aanroepen van de `javax.servlet.http.HttpServletResponse` object `getOutputStream` methode.
   * Maak een bytearray en vul deze door het `BLOB` object `getBinaryData` methode. Deze taak wijst de inhoud van toe `FormsResult` object naar de bytearray.
   * De `javax.servlet.http.HttpServletResponse` object `write` methode om de formuliergegevensstroom naar de webbrowser van de client te verzenden. Geef de bytearray door aan de `write` methode.

**Zie ook**

[Forms met rechten voor renderen](#rendering-rights-enabled-forms)

[AEM Forms aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
