---
title: PDF converteren naar PostScript- en afbeeldingsbestanden
description: Met de service PDF converteren kunt u PDF-documenten converteren naar PostScript en naar verschillende afbeeldingsindelingen (JPEG, JPEG 2000, PNG en TIFF) met behulp van de Java API en Web Service API.
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
exl-id: 31730c24-46c3-4111-9391-ccd4342740e9
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Document Services,APIs & Integrations
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '2774'
ht-degree: 0%

---

# PDF omzetten in PostScript- en afbeeldingsbestanden {#converting-pdf-to-postscript-andimage-files}

**de Steekproeven en de voorbeelden in dit document zijn slechts voor AEM Forms op milieu JEE.**

**Ongeveer de Omzetten Dienst van PDF**

Met de service PDF converteren worden PDF-documenten geconverteerd naar PostScript en naar verschillende afbeeldingsindelingen (JPEG, JPEG 2000, PNG en TIFF). Het converteren van een PDF-document naar PostScript is handig voor afdrukken op basis van een onbeheerde server op elke PostScript-printer. Het omzetten van een PDF-document in een TIFF-bestand met meerdere pagina&#39;s is handig bij het archiveren van documenten in systemen voor inhoudsbeheer die geen ondersteuning bieden voor PDF-documenten.

U kunt deze taken uitvoeren met de service PDF converteren:

* PDF-documenten converteren naar PostScript.
* Zet PDF-documenten om in afbeeldingsindelingen.

>[!NOTE]
>
>Voor meer informatie over de dienst van de PDF van de Bekeerling, zie [ Verwijzing van de Diensten voor AEM Forms ](https://www.adobe.com/go/learn_aemforms_services_63).

## PDF-documenten converteren naar PostScript {#converting-pdf-documents-to-postscript}

In dit onderwerp wordt beschreven hoe u de API (Java en webservice) voor het converteren van PDF Service kunt gebruiken om PDF-documenten programmatisch om te zetten in PostScript-bestanden. Het PDF-document dat naar een PostScript-bestand wordt geconverteerd, moet een niet-interactief PDF-document zijn. Dit betekent dat als u probeert een interactief PDF-document te converteren naar een PostScript-bestand, er een uitzondering wordt gegenereerd.

>[!NOTE]
>
>Voor meer informatie over de dienst van de PDF van de Bekeerling, zie [ Verwijzing van de Diensten voor AEM Forms ](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary-of-steps}

Voer de volgende stappen uit om een PDF-document te converteren naar een PostScript-bestand:

1. Inclusief projectbestanden.
1. Maak een Convert PDF service-client.
1. Verwijs naar het PDF-document voor conversie naar een PostScript-bestand.
1. Stel opties voor de uitvoering van de conversie in.
1. Zet het PDF-document om in een PostScript-bestand.
1. Sla het PostScript-bestand op.

**omvat projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u de proxybestanden opnemen.

**creeer een ConvertPDF cliënt**

Voordat u programmatically een Convert PDF de dienstverrichting kunt uitvoeren, moet u een Convert PDF de dienstcliënt creëren. Maak een `ConvertPdfServiceClient` -object als u de Java API gebruikt. Maak een `ConvertPDFServiceService` -object als u de webservice-API gebruikt.

Deze sectie gebruikt webservicefunctionaliteit die in AEM Forms is geïntroduceerd. Als u toegang wilt tot nieuwe functionaliteit, moet u het proxyobject maken met het attribuut `lc_version` . (Zie &quot;Toegang tot nieuwe functionaliteit gebruikend de Webdiensten&quot;in [ het Aanhalen van AEM Forms gebruikend de Diensten van het Web ](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-web-services).)

**Verwijzing het document van PDF om in een dossier van PostScript om te zetten**

Verwijs naar het PDF-document dat u naar een PostScript-bestand wilt converteren. Zoals eerder in dit onderwerp is vermeld, moet het PDF-document een niet-interactief PDF-document zijn. Als u probeert een interactief PDF-document te converteren naar een PostScript-bestand, wordt een uitzondering gegenereerd.

**plaats omzettingsruntime opties**

Wanneer u een PDF-document naar een PostScript-bestand converteert, kunt u runtime-opties definiëren die het PostScript-type opgeven dat wordt gemaakt. U kunt bijvoorbeeld een PostScript-bestand van niveau 3 definiëren.

Doorgaans geeft het gegenereerde PostScript-bestand de grootte van het invoerdocument PDF aan. Als u de optie `ShrinkToFit` selecteert (waarmee de uitvoer van het PostScript-bestand wordt verkleind zodat het op de pagina past), ziet u geen verschil tussen het invoerdocument en het gegenereerde PostScript-bestand. De optie `ShrinkToFit` is alleen van kracht als u ervoor kiest om af te drukken op een kleiner paginaformaat dan het invoerdocument PDF. Als u een kleiner paginaformaat wilt selecteren, definieert u de optie `PageSize` . Daarnaast wordt aangeraden de optie `RotateAndCenter` in te stellen op `true` om de juiste PostScript-uitvoer te verkrijgen.

Op dezelfde manier geldt dat als u de optie `ExpandToFit` selecteert (waarmee de uitvoer van het PostScript-bestand wordt aangepast aan de pagina), dit alleen als u ervoor kiest om af te drukken op een groter paginaformaat dan het invoerdocument PDF. Als u een grotere pagina wilt selecteren, definieert u de optie `PageSize` . Daarnaast wordt aangeraden de optie `RotateAndCenter` in te stellen op `true` om de juiste PostScript-uitvoer te verkrijgen.

>[!NOTE]
>
>Voor informatie over de runtime waarden die u kunt plaatsen, zie de `ToPSOptionsSpec` klassenverwijzing in [ AEM Forms API Verwijzing ](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**zet het document van de PDF in een dossier van PostScript** om

Nadat u de de dienstcliënt creeert en runtime opties plaatst, kunt u de de omzettingsverrichting van PostScript aanhalen. Voor deze bewerking is informatie nodig over het document dat u wilt converteren, inclusief het voorkeursniveau van PostScript voor het doeldocument.

**sparen het dossier van PostScript**

Nadat u het PDF-document hebt omgezet in PostScript, kunt u de uitvoer opslaan als een PostScript-bestand.

**zie ook**

[Een PDF-document naar PS converteren met de Java API](converting-pdf-postscript-image-files.md#convert-a-pdf-document-to-ps-using-the-java-api)

[Een PDF-document naar PS converteren met de webservice-API](converting-pdf-postscript-image-files.md#convert-a-pdf-document-to-ps-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Snel aan de slag met de PDF Service API](/help/forms/developing/convert-pdf-service-java-api.md#convert-pdf-service-java-api-quick-start-soap)

### Een PDF-document naar PS converteren met de Java API {#convert-a-pdf-document-to-ps-using-the-java-api}

Een PDF-document converteren naar PostScript met de Convert PDF Service API (Java):

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-convertpdf-client.jar, op in het klassepad van uw Java-project.

1. Maak een Convert PDF-client.

   * Maak een `ServiceClientFactory` -object dat verbindingseigenschappen bevat.
   * Maak een `ConvertPdfServiceClient` -object door de constructor ervan te gebruiken en het `ServiceClientFactory` -object door te geven.

1. Verwijs naar het PDF-document voor conversie naar een PostScript-bestand.

   * Maak een `java.io.FileInputStream` -object met behulp van de constructor en geef een tekenreekswaarde door die de locatie aangeeft van het PDF-document dat u wilt converteren.
   * Maak een `com.adobe.idp.Document` -object dat het PDF-document opslaat met de `com.adobe.idp.Document` -constructor. Geef het `java.io.FileInputStream` -object dat het PDF-document bevat door.

1. Stel opties voor de uitvoering van de conversie in.

   * Maak een `ToPSOptionsSpec` -object door de constructor ervan aan te roepen.
   * Stel uitvoeringsopties in door een geschikte methode aan te roepen die tot het `ToPSOptionsSpec` -object behoort. Als u bijvoorbeeld het PostScript-niveau wilt definiëren dat wordt gemaakt, roept u de methode `setPsLevel` van het object `ToPSOptionsSpec` aan en geeft u een opsommingswaarde `PSLevel` door die het PostScript-niveau opgeeft. Voor informatie over alle runtime waarden die u kunt plaatsen, zie de `ToPSOptionsSpec` klassenverwijzing in [ AEM Forms API Verwijzing ](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

1. Zet het PDF-document om in een PostScript-bestand.

   Roep de methode `toPS2` van het object `ConvertPdfServiceClient` aan en geef de volgende waarden door:

   * Een `com.adobe.idp.Document` -object dat staat voor het PDF-document dat naar een PostScript-bestand moet worden geconverteerd.
   * Een `ToPSOptionsSpec` -object dat PostScript-runtime-opties opgeeft.

   De methode `toPS2` retourneert een `Document` -object dat het nieuwe PostScript-document bevat.

1. Sla het PostScript-bestand op.

   * Maak een `java.io.File` -object en zorg dat de bestandsnaamextensie .ps is.
   * Roep de methode `copyToFile` van het object `Document` aan om de inhoud van het object `Document` naar het bestand te kopiëren (gebruik het object `Document` dat door de methode `toPS2` is geretourneerd).

**zie ook**

[Overzicht van de stappen](converting-pdf-postscript-image-files.md#summary-of-steps)

[Snel starten (SOAP modus): een PDF-document converteren naar PostScript met de Java API](/help/forms/developing/convert-pdf-service-java-api.md#quick-start-soap-mode-converting-a-pdf-document-to-postscript-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Een PDF-document naar PS converteren met de webservice-API {#convert-a-pdf-document-to-ps-using-the-web-service-api}

Converteer een PDF-document naar PostScript met de Convert PDF Service API (webservice):

1. Inclusief projectbestanden.

   Creeer een Microsoft .NET project dat MTOM gebruikt. Gebruik de volgende WSDL-definitie: `http://localhost:8080/soap/services/ConvertPDFService?WSDL&lc_version=9.0.1` .

   >[!NOTE]
   >
   >Vervang `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een Convert PDF-client.

   * Maak een `ConvertPdfServiceClient` -object met de standaardconstructor.
   * Maak een `ConvertPdfServiceClient.Endpoint.Address` -object met de `System.ServiceModel.EndpointAddress` -constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/ConvertPDFService?blob=mtom` .) U hoeft het attribuut `lc_version` niet te gebruiken. Geef echter `?blob=mtom` op.
   * Maak een `System.ServiceModel.BasicHttpBinding` -object door de waarde van het `ConvertPdfServiceClient.Endpoint.Binding` -veld op te halen. De geretourneerde waarde wordt gecast naar `BasicHttpBinding` .
   * Stel het veld `MessageEncoding` van het `System.ServiceModel.BasicHttpBinding` -object in op `WSMessageEncoding.Mtom` . Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld `ConvertPdfServiceClient.ClientCredentials.UserName.UserName` toe.
      * Wijs de bijbehorende wachtwoordwaarde toe aan het veld `ConvertPdfServiceClient.ClientCredentials.UserName.Password` .
      * Wijs de constante waarde `HttpClientCredentialType.Basic` toe aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType` .
      * Wijs de constante waarde `BasicHttpSecurityMode.TransportCredentialOnly` toe aan het veld `BasicHttpBindingSecurity.Security.Mode` .

1. Verwijs naar het PDF-document voor conversie naar een PostScript-bestand.

   * Maak een `BLOB` -object met behulp van de constructor. Met het `BLOB` -object wordt een PDF-document opgeslagen dat wordt geconverteerd naar een PostScript-bestand.
   * Maak een `System.IO.FileStream` -object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie vertegenwoordigt van het PDF-document dat moet worden omgezet en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van het object `System.IO.FileStream` wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de eigenschap `Length` van het object `System.IO.FileStream` op te halen.
   * Vul de bytearray met streamgegevens door de methode `Read` van het object `System.IO.FileStream` aan te roepen en de bytearray, de startpositie en de streamlengte door te geven om te lezen.
   * Vul het `BLOB` -object door het `MTOM` -veld ervan toe te wijzen met de inhoud van de bytearray.

1. Stel opties voor de uitvoering van de conversie in.

   * Maak een `ToPSOptionsSpec` -object door de constructor ervan aan te roepen.
   * Stel uitvoeringsopties in door een waarde toe te wijzen aan het gegevenslid van het `ToPSOptionsSpec` -object. Als u bijvoorbeeld het PostScript-niveau wilt definiëren dat wordt gemaakt, wijst u een `PSLevel` opsommingswaarde toe aan het gegevenslid van het `ToPSOptionsSpec` object `psLevel` .

1. Zet het PDF-document om in een PostScript-bestand.

   Roep de methode `toPS2` van het object `GeneratePDFServiceService` aan en geef de volgende waarden door:

   * Een `BLOB` -object dat staat voor het PDF-document dat moet worden omgezet in een PostScript-bestand
   * Een `ToPSOptionsSpec` -object dat uitvoeringsopties opgeeft

   Nadat de conversie is voltooid, extraheert u de binaire gegevens die het PostScript-document vertegenwoordigen door de eigenschap `MTOM` van het object `BLOB` te openen. Hiermee wordt een bytearray geretourneerd die u naar een PostScript-bestand kunt schrijven.

1. Sla het PostScript-bestand op.

   * Maak een `System.IO.FileStream` -object door de constructor ervan aan te roepen. Geef een tekenreekswaarde door die de bestandslocatie van het PS-bestand vertegenwoordigt.
   * Maak een bytearray waarin de gegevensinhoud wordt opgeslagen van het object `BLOB` dat door de methode `encryptPDFUsingPassword` is geretourneerd. Vul de bytearray met de waarde van het veld `MTOM` van het object `BLOB` .
   * Maak een `System.IO.BinaryWriter` -object door de constructor ervan aan te roepen en het `System.IO.FileStream` -object door te geven.
   * Schrijf de inhoud van de bytearray naar het PostScript-bestand door de methode `Write` van het object `System.IO.BinaryWriter` aan te roepen en de bytearray door te geven.

**zie ook**

[Overzicht van de stappen](converting-pdf-postscript-image-files.md#summary-of-steps)

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## PDF-documenten omzetten in afbeeldingsindelingen {#converting-pdf-documents-to-image-formats}

Met de service PDF converteren kunt u PDF-documenten programmatisch converteren naar afbeeldingsindelingen, zoals JPEG, JPEG 2000, TIFF en PNG. Door een PDF-document om te zetten in een afbeeldingsbestand, kunt u het PDF-document gebruiken als een afbeeldingsbestand. U kunt het image bijvoorbeeld in een inhoudbeheersysteem voor bedrijven plaatsen voor opslag.

Wanneer u een PDF-document omzet in een afbeelding, maakt de service PDF omzetten een aparte afbeelding voor elke pagina in het document. Met andere woorden, als het document uit 20 pagina&#39;s bestaat, maakt de service PDF converteren 20 afbeeldingsbestanden. Wanneer u een PDF-document omzet in een afbeeldingsindeling, kunt u afzonderlijke afbeeldingen maken voor elke pagina in het PDF-document of één afbeeldingsbestand voor het gehele PDF-document.

>[!NOTE]
>
>Voor meer informatie over de dienst van de PDF van de Bekeerling, zie [ Verwijzing van de Diensten voor AEM Forms ](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary_of_steps-1}

Voer de volgende stappen uit om een PDF-document te converteren naar een van de ondersteunde typen:

1. Inclusief projectbestanden.
1. Maak een Convert PDF service-client.
1. Haal het PDF-document op dat u wilt converteren.
1. Stel runtime-opties in.
1. Zet de PDF om in een afbeelding.
1. Haal de afbeeldingsbestanden op uit een verzameling.

**omvat projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u de proxybestanden opnemen.

**creeer een ConvertPDF cliënt**

Voordat u programmatically een Convert PDF de dienstverrichting kunt uitvoeren, moet u een Convert PDF de dienstcliënt creëren. Maak een `ConvertPdfServiceClient` -object als u de Java API gebruikt. Maak een `ConvertPDFServiceService` -object als u de webservice-API gebruikt.

**wint het document van PDF terug om** om te zetten

Haal het PDF-document op dat u wilt omzetten in een afbeelding. U kunt een interactief PDF-document niet omzetten in een afbeelding. Wanneer u dit probeert, wordt een uitzondering gegenereerd. Als u een interactief PDF-document wilt converteren naar een afbeeldingsbestand, moet u het PDF-document samenvoegen voordat u het converteert. (Zie [ het Afvlakken de Documenten van PDF ](/help/forms/developing/creating-document-output-streams.md#flattening-pdf-documents).)

**vastgestelde runtime opties**

Stel runtime-opties in, zoals de afbeeldingsindeling en de resolutiewaarden. Voor informatie over de runtime waarden, zie de `ToImageOptionsSpec` klassenverwijzing in [ AEM Forms API Verwijzing ](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**zet PDF in een beeld** om

Nadat u de de dienstcliënt creeert en runtime opties plaatst, kunt u het document van de PDF in een beeld omzetten. Een verzamelingsobject dat de afbeeldingen bevat, wordt geretourneerd.

**wint de beelddossiers van een inzameling** terug

U kunt afbeeldingsbestanden ophalen uit een verzamelingsobject dat wordt geretourneerd door de service PDF converteren. Elk element in de verzameling is een `com.adobe.idp.Document` -instantie (of een `BLOB` -instantie als u webservices gebruikt) die u kunt opslaan als afbeeldingsbestand, zoals een JPG-bestand.

De indeling van het afbeeldingsbestand is afhankelijk van de runtime-optie van `ImageConvertFormat` . Met andere woorden, als u de `ImageConvertFormat` runtime-optie instelt op `ImageConvertFormat.JPEG` , kunt u afbeeldingsbestanden opslaan als JPG-bestanden.

**zie ook**

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Snel aan de slag met de PDF Service API](/help/forms/developing/convert-pdf-service-java-api.md#convert-pdf-service-java-api-quick-start-soap)

### Een PDF-document converteren naar afbeeldingsbestanden met de Java API {#convert-a-pdf-document-to-image-files-using-the-java-api}

Een PDF-document converteren naar een afbeeldingsindeling met de API (Java) voor de convertservice PDF:

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-convertpdf-client.jar, op in het klassepad van uw Java-project.

1. Maak een Convert PDF-client.

   * Maak een `ServiceClientFactory` -object dat verbindingseigenschappen bevat.
   * Maak een `ConvertPdfServiceClient` -object door de constructor ervan te gebruiken en het `ServiceClientFactory` -object door te geven.

1. Haal het PDF-document op dat u wilt converteren.

   * Maak een `java.io.FileInputStream` -object dat staat voor het PDF-document dat u wilt converteren met behulp van de constructor ervan en geef een tekenreekswaarde door die de locatie van het PDF-document aangeeft.
   * Maak een `com.adobe.idp.Document` -object door de constructor ervan te gebruiken en het `java.io.FileInputStream` -object door te geven.

1. Stel runtime-opties in.

   * Maak een `ToImageOptionsSpec` -object met behulp van de constructor.
   * Roep de vereiste methoden aan die bij dit object horen. Stel het afbeeldingstype bijvoorbeeld in door de methode `setImageConvertFormat` aan te roepen en een opsommingswaarde van `ImageConvertFormat` door te geven die het indelingstype aangeeft.

   >[!NOTE]
   >
   >U moet de opsommingswaarde `ImageConvertFormat` instellen.

1. Zet de PDF om in een afbeelding.

   Roep de methode `toImage2` van het object `ConvertPdfServiceClient` aan en geef de volgende waarden door:

   * Een `com.adobe.idp.Document` -object dat het te converteren PDF-bestand vertegenwoordigt.
   * Een `com.adobe.livecycle.converpdfservice.client.ToImageOptionsSpec` -object dat de verschillende voorkeuren voor de indeling van de doelafbeelding bevat.

   De methode `toImage2` retourneert een `java.util.List` -object dat afbeeldingen bevat. Elk element in de verzameling is een `com.adobe.idp.Document` -instantie.

1. Haal de afbeeldingsbestanden op uit een verzameling.

   Doorloop het `java.util.List` -object om te bepalen of er afbeeldingen aanwezig zijn. Elk element is een `com.adobe.idp.Document` -instantie. Sla de afbeelding op door de methode `copyToFile` van het object `com.adobe.idp.Document` aan te roepen en een object `java.io.File` door te geven.

**zie ook**

[Snel starten (SOAP modus): een PDF-document converteren naar JPEG-bestanden met de Java API](/help/forms/developing/convert-pdf-service-java-api.md#quick-start-soap-mode-converting-a-pdf-document-to-jpeg-files-using-the-java-api)

### Een PDF-document converteren naar afbeeldingsbestanden met de webservice-API {#convert-a-pdf-document-to-image-files-using-the-web-service-api}

Een PDF-document converteren naar een afbeeldingsindeling met de Convert PDF Service API (webservice):

1. Inclusief projectbestanden.

   Creeer een Microsoft .NET project dat MTOM gebruikt. Gebruik de volgende WSDL-definitie: `http://localhost:8080/soap/services/ConvertPDFService?WSDL&lc_version=9.0.1` .

   >[!NOTE]
   >
   >Vervang `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een PDF-client voor converteren.

   * Maak een `ConvertPdfServiceClient` -object met de standaardconstructor.
   * Maak een `ConvertPdfServiceClient.Endpoint.Address` -object met de `System.ServiceModel.EndpointAddress` -constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/ConvertPDFService?blob=mtom` .) U hoeft het attribuut `lc_version` niet te gebruiken. Geef echter `?blob=mtom` op.
   * Maak een `System.ServiceModel.BasicHttpBinding` -object door de waarde van het `ConvertPdfServiceClient.Endpoint.Binding` -veld op te halen. De geretourneerde waarde wordt gecast naar `BasicHttpBinding` .
   * Stel het veld `MessageEncoding` van het `System.ServiceModel.BasicHttpBinding` -object in op `WSMessageEncoding.Mtom` . Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld `ConvertPdfServiceClient.ClientCredentials.UserName.UserName` toe.
      * Wijs de bijbehorende wachtwoordwaarde toe aan het veld `ConvertPdfServiceClient.ClientCredentials.UserName.Password` .
      * Wijs de constante waarde `HttpClientCredentialType.Basic` toe aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType` .
      * Wijs de constante waarde `BasicHttpSecurityMode.TransportCredentialOnly` toe aan het veld `BasicHttpBindingSecurity.Security.Mode` .

1. Haal het PDF-document op dat u wilt converteren.

   * Maak een `BLOB` -object met behulp van de constructor. Met dit `BLOB` -object wordt het PDF-formulier opgeslagen.
   * Maak een `System.IO.FileStream` -object door de constructor ervan aan te roepen. Geef een tekenreekswaarde door die de locatie aangeeft van het PDF-formulier en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van het object `System.IO.FileStream` wordt opgeslagen. Bepaal de grootte van de bytearray door de eigenschap `Length` van het object `System.IO.FileStream` op te halen.
   * Vul de bytearray met streamgegevens door de methode `Read` van het object `System.IO.FileStream` aan te roepen. Geef de bytearray, de startpositie en de streamlengte door om te lezen.
   * Vul het `BLOB` -object door het `MTOM` -veld ervan toe te wijzen met de inhoud van de bytearray.

1. Stel runtime-opties in.

   * Maak een `ToImageOptionsSpec` -object met behulp van de constructor.
   * Roep de vereiste methoden aan die bij dit object horen. Stel het afbeeldingstype bijvoorbeeld in door de methode `setImageConvertFormat` aan te roepen en een opsommingswaarde `ImageConvertFormat` door te geven die het indelingstype aangeeft.

   >[!NOTE]
   >
   >U moet de opsommingswaarde `ImageConvertFormat` instellen.

1. Zet de PDF om in een afbeelding.

   Roep de methode `toImage2` van het object `ConvertPDFServiceService` aan en geef de volgende waarden door:

   * Een `BLOB` -object dat het te converteren bestand vertegenwoordigt
   * Een `ToImageOptionsSpec` -object dat de verschillende voorkeuren voor de indeling van de doelafbeelding bevat

   De methode `toImage2` retourneert een `MyArrayOfBLOB` -object dat de nieuwe afbeeldingsbestanden bevat.

1. Haal de afbeeldingsbestanden op uit een verzameling.

   * Bepaal het aantal elementen in het `MyArrayOfBLOB` -object door de waarde van het `Count` -veld op te halen. Elk element is een `BLOB` -object dat de afbeelding bevat.
   * Doorloop het `MyArrayOfBLOB` -object en sla elk afbeeldingsbestand op.

**zie ook**

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)
