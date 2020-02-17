---
title: Formulieren weergeven waarvoor rechten zijn ingeschakeld
seo-title: Formulieren weergeven waarvoor rechten zijn ingeschakeld
description: 'null'
seo-description: 'null'
uuid: ce5e4be6-d9b0-4989-a0e1-a8c3b98aed77
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: d4c2b2f0-613a-409d-b39b-8e37fdb96eea
translation-type: tm+mt
source-git-commit: 7cbe3e94eddb81925072f68388649befbb027e6d

---


# Formulieren weergeven waarvoor rechten zijn ingeschakeld {#rendering-rights-enabled-forms}

De service Forms kan formulieren weergeven waarop gebruiksrechten zijn toegepast. Gebruiksrechten hebben betrekking op functionaliteit die standaard beschikbaar is in Acrobat, maar niet in Adobe Reader, zoals de mogelijkheid om opmerkingen toe te voegen aan een formulier of formuliervelden in te vullen en het formulier op te slaan. Formulieren waarop gebruiksrechten zijn toegepast, worden formulieren die voor rechten zijn ingeschakeld genoemd. Een gebruiker die een formulier met ingeschakelde rechten opent in Adobe Reader, kan bewerkingen uitvoeren die zijn ingeschakeld voor dat formulier.

Als u gebruiksrechten wilt toepassen op een formulier, moet de Acrobat Reader DC-extensieservice onderdeel zijn van de installatie van AEM-formulieren. Bovendien moet u beschikken over een geldige referentie waarmee u gebruiksrechten kunt toepassen op PDF-documenten. U moet dus de Acrobat Reader DC-extensieservice op de juiste wijze configureren voordat u een formulier met ingeschakelde rechten kunt genereren. (Zie [Informatie over de Acrobat Reader DC extensions Service](/help/forms/developing/assigning-usage-rights.md#about-the-acrobat-reader-dc-extensions-service).)

>[!NOTE]
>
>Als u een formulier wilt genereren dat gebruiksrechten bevat, moet u een XDP-bestand als invoer gebruiken, niet als een PDF-bestand. Als u een PDF-bestand als invoer gebruikt, wordt het formulier nog steeds gegenereerd. het is echter geen formulier waarvoor rechten gelden.

>[!NOTE]
>
>U kunt een formulier niet vooraf invullen met XML-gegevens als u de volgende gebruiksrechten opgeeft: `enableComments`, `enableCommentsOnline`, `enableEmbeddedFiles`, of `enableDigitalSignatures`. (Zie Formulieren [vooraf invullen met stroombare indelingen](/help/forms/developing/prepopulating-forms-flowable-layouts.md).)

>[!NOTE]
>
>Voor meer informatie over de dienst van Vormen, zie de Verwijzing van de [Diensten voor Vormen](https://www.adobe.com/go/learn_aemforms_services_63)AEM.

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

Voordat u een API-bewerking voor Forms-service programmatisch kunt uitvoeren, moet u een Forms-service-client maken.

**Opties voor het uitvoeren van gebruiksrechten instellen**

U moet de runtime van gebruiksrechten opties plaatsen om een recht-Toegelaten vorm terug te geven. U moet ook de alias van de referentie opgeven die wordt gebruikt om gebruiksrechten toe te passen op een formulier. Nadat u de alias-waarde hebt opgegeven, geeft u elk gebruiksrecht op dat u op het formulier wilt toepassen.

**Een formulier met ingeschakelde rechten weergeven**

Als u een formulier met ingeschakelde rechten wilt genereren, gebruikt u dezelfde toepassingslogica als voor het weergeven van een formulier zonder gebruiksrechten. Het enige verschil is dat u ervoor moet zorgen dat de gebruiksrechten tijdens runtime opties zijn opgenomen in uw toepassingslogica.

>[!NOTE]
>
>Wanneer u een formulier met ingeschakelde rechten weergeeft met de API voor webservices van Forms, kunt u geen bestanden aan het formulier koppelen.

**De formuliergegevensstroom naar de webbrowser van de client schrijven**

Wanneer een formulier waarvoor rechten zijn ingeschakeld door de Forms-service wordt gegenereerd, wordt een formuliergegevensstroom geretourneerd die u naar de webbrowser van de client moet schrijven. Nadat het formulier naar de webbrowser van de client is geschreven, is het zichtbaar voor de gebruiker. Een gebruiker die het formulier met ingeschakelde rechten weergeeft in Adobe Reader, kan bewerkingen uitvoeren die zijn ingeschakeld voor dat formulier.

**Zie ook**

[Formulieren waarvoor rechten zijn ingeschakeld, renderen met de Java API](#render-rights-enabled-forms-using-the-java-api)

[Formulieren waarvoor rechten zijn ingeschakeld, renderen met de API voor webservices](#render-rights-enabled-forms-using-the-web-service-api)

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Forms Service API, snel aan de slag](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

[Interactieve PDF-formulieren renderen](/help/forms/developing/rendering-interactive-pdf-forms.md)

[Webtoepassingen maken die formulieren renderen](/help/forms/developing/creating-web-applications-renders-forms.md)

### Formulieren waarvoor rechten zijn ingeschakeld, renderen met de Java API {#render-rights-enabled-forms-using-the-java-api}

Een formulier met ingeschakelde rechten weergeven met de Forms API (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden, zoals adobe-forms-client.jar, op in het klassenpad van uw Java-project.

1. Een Forms Client API-object maken

   * Maak een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Maak een `FormsServiceClient` object door de constructor ervan te gebruiken en het `ServiceClientFactory` object door te geven.

1. Opties voor het uitvoeren van gebruiksrechten instellen

   * Maak een `ReaderExtensionSpec` object met de constructor ervan.
   * Geef de alias van de referentie op door de methode van het `ReaderExtensionSpec` `setReCredentialAlias` object aan te roepen en geef een tekenreekswaarde op die de aliaswaarde vertegenwoordigt.
   * Stel elk gebruiksrecht in door de bijbehorende methode aan te roepen die bij het `ReaderExtensionSpec` object hoort. U kunt echter alleen een gebruiksrecht instellen als de referentie die u gebruikt dit toestaat. U kunt dus geen gebruiksrecht instellen als de referentie het instellen niet toestaat. Bijvoorbeeld. Als u het gebruiksrecht wilt instellen waarmee een gebruiker formuliervelden kan invullen en het formulier kan opslaan, roept u de methode van het `ReaderExtensionSpec` object aan en geeft u het door `setReFillIn` `true`.
   >[!NOTE]
   >
   >U hoeft de `ReaderExtensionSpec` methode van het `setReCredentialPassword` object niet aan te roepen. Deze methode wordt niet gebruikt door de dienst van Vormen.

1. Een formulier met ingeschakelde rechten weergeven

   Roep de methode van het `FormsServiceClient` `renderPDFFormWithUsageRights` object aan en geef de volgende waarden door:

   * Een tekenreekswaarde die de naam van het formulierontwerp opgeeft, inclusief de bestandsnaamextensie. Als u verwijst naar een formulierontwerp dat deel uitmaakt van een Forms-toepassing, moet u controleren of u het volledige pad opgeeft, bijvoorbeeld `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * Een `com.adobe.idp.Document` object dat gegevens bevat die met het formulier moeten worden samengevoegd. Geef een leeg `com.adobe.idp.Document` object door als u geen gegevens wilt samenvoegen.
   * Een `PDFFormRenderSpec` object dat uitvoeringsopties opslaat.
   * Een `ReaderExtensionSpec` object waarin opties voor gebruiksrechten zijn opgeslagen.
   * Een `URLSpec` object dat URI-waarden bevat die door de service Forms worden vereist.
   De `renderPDFFormWithUsageRights` methode retourneert een `FormsResult` object dat een formuliergegevensstroom bevat die naar de webbrowser van de client moet worden geschreven.

1. De formuliergegevensstroom naar de webbrowser van de client schrijven

   * Maak een `com.adobe.idp.Document` object door de `FormsResult` methode van het `getOutputContent` object aan te roepen.
   * Haal het inhoudstype van het `com.adobe.idp.Document` object op door de `getContentType` methode ervan aan te roepen.
   * Stel het inhoudstype van het `javax.servlet.http.HttpServletResponse` object in door de bijbehorende `setContentType` methode op te roepen en het inhoudstype van het `com.adobe.idp.Document` object door te geven.
   * Maak een `javax.servlet.ServletOutputStream` object dat wordt gebruikt om de gegevensstroom van het formulier naar de webbrowser van de client te schrijven door de `javax.servlet.http.HttpServletResponse` methode van het `getOutputStream` object aan te roepen.
   * Maak een `java.io.InputStream` object door de `com.adobe.idp.Document` methode van het `getInputStream` object aan te roepen.
   * Maak een bytearray die deze met de formuliergegevensstroom vult door de methode van het `InputStream` `read` object aan te roepen en de bytearray als een argument door te geven.
   * Roep de `javax.servlet.ServletOutputStream` methode van het `write` object aan om de formuliergegevensstroom naar de webbrowser van de client te verzenden. Geef de bytearray door aan de `write` methode.

**Zie ook**

[Snel starten (SOAP-modus): Een formulier waarvoor rechten zijn ingeschakeld weergeven met de Java API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-rendering-a-rights-enabled-form-using-the-java-api)

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Formulieren waarvoor rechten zijn ingeschakeld, renderen met de API voor webservices {#render-rights-enabled-forms-using-the-web-service-api}

Een formulier met ingeschakelde rechten weergeven met de API voor formulieren (webservice):

1. Projectbestanden opnemen

   * Maak Java-proxyklassen die de Forms service WSDL gebruiken.
   * Neem de Java-proxyklassen op in het klassepad.

1. Een Forms Client API-object maken

   Maak een `FormsService` object en stel verificatiewaarden in.

1. Opties voor het uitvoeren van gebruiksrechten instellen

   * Maak een `ReaderExtensionSpec` object met de constructor ervan.
   * Geef de alias van de referentie op door de methode van het `ReaderExtensionSpec` `setReCredentialAlias` object aan te roepen en geef een tekenreekswaarde op die de aliaswaarde vertegenwoordigt.
   * Stel elk gebruiksrecht in door de bijbehorende methode aan te roepen die bij het `ReaderExtensionSpec` object hoort. U kunt echter alleen een gebruiksrecht instellen als de referentie die u gebruikt dit toestaat. U kunt dus geen gebruiksrecht instellen als de referentie het instellen niet toestaat. Als u het gebruiksrecht wilt instellen waarmee een gebruiker formuliervelden kan invullen en het formulier kan opslaan, roept u de methode van het `ReaderExtensionSpec` object aan en geeft u het door `setReFillIn` `true`.

1. Een formulier met ingeschakelde rechten weergeven

   Roep de methode van het `FormsService` `renderPDFFormWithUsageRights` object aan en geef de volgende waarden door:

   * Een tekenreekswaarde die de naam van het formulierontwerp opgeeft, inclusief de bestandsnaamextensie. Als u verwijst naar een formulierontwerp dat deel uitmaakt van een Forms-toepassing, moet u controleren of u het volledige pad opgeeft, bijvoorbeeld `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * Een `BLOB` object dat gegevens bevat die met het formulier moeten worden samengevoegd. Als u geen gegevens wilt samenvoegen met het formulier, moet u een `BLOB` object doorgeven dat is gebaseerd op een lege XML-gegevensbron. U kunt geen null- `BLOB` object doorgeven. anders wordt een uitzondering gegenereerd.
   * Een `PDFFormRenderSpec` object dat uitvoeringsopties opslaat.
   * Een `ReaderExtensionSpec` object waarin opties voor gebruiksrechten zijn opgeslagen.
   * Een `URLSpec` object dat URI-waarden bevat die door de service Forms worden vereist.
   De `renderPDFFormWithUsageRights` methode retourneert een `FormsResult` object dat een formuliergegevensstroom bevat die naar de webbrowser van de client moet worden geschreven.

1. De formuliergegevensstroom naar de webbrowser van de client schrijven

   * Maak een `BLOB` object dat formuliergegevens bevat door de `FormsResult` methode van het `getOutputContent` object aan te roepen.
   * Haal het inhoudstype van het `BLOB` object op door de `getContentType` methode ervan aan te roepen.
   * Stel het inhoudstype van het `javax.servlet.http.HttpServletResponse` object in door de bijbehorende `setContentType` methode op te roepen en het inhoudstype van het `BLOB` object door te geven.
   * Maak een `javax.servlet.ServletOutputStream` object dat wordt gebruikt om de gegevensstroom van het formulier naar de webbrowser van de client te schrijven door de `javax.servlet.http.HttpServletResponse` methode van het `getOutputStream` object aan te roepen.
   * Maak een bytearray en vul deze door de `BLOB` methode van het `getBinaryData` object aan te roepen. Hierdoor wordt de inhoud van het `FormsResult` object toegewezen aan de bytearray.
   * Roep de `javax.servlet.http.HttpServletResponse` methode van het `write` object aan om de formuliergegevensstroom naar de webbrowser van de client te verzenden. Geef de bytearray door aan de `write` methode.

**Zie ook**

[Formulieren weergeven waarvoor rechten zijn ingeschakeld](#rendering-rights-enabled-forms)

[AEM-formulieren aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
