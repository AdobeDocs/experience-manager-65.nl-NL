---
title: PDF converteren naar Postscript- en afbeeldingsbestanden
seo-title: PDF converteren naar Postscript- en afbeeldingsbestanden
description: 'null'
seo-description: 'null'
uuid: 07da0391-7180-4197-aaa6-ae753d753b84
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: f8707752-2c83-461a-b83d-708754b0f3f6
translation-type: tm+mt
source-git-commit: f9389a06f9c2cd720919486765cee76257f272c3

---


# PDF converteren naar Postscript- en afbeeldingsbestanden {#converting-pdf-to-postscript-andimage-files}

**Over de Convert PDF Service**

Met de service PDF converteren worden PDF-documenten geconverteerd naar PostScript en naar een aantal afbeeldingsindelingen (JPEG, JPEG 2000, PNG en TIFF). Het converteren van een PDF-document naar PostScript is handig voor afdrukken op basis van een server zonder toezicht op elke PostScript-printer. Het converteren van een PDF-document naar een TIFF-bestand met meerdere pagina&#39;s is handig bij het archiveren van documenten in inhoudsbeheersystemen die geen PDF-documenten ondersteunen.

U kunt deze taken uitvoeren met de service PDF converteren:

* Converteer PDF-documenten naar PostScript.
* PDF-documenten converteren naar afbeeldingsindelingen.

>[!NOTE]
>
>Zie [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63)voor meer informatie over de service PDF converteren.

## PDF-documenten converteren naar PostScript {#converting-pdf-documents-to-postscript}

In dit onderwerp wordt beschreven hoe u de API (Java en webservice) voor het converteren van PDF-documenten naar PostScript-bestanden kunt gebruiken. Het PDF-document dat wordt geconverteerd naar een PostScript-bestand, moet een niet-interactief PDF-document zijn. Als u een interactief PDF-document naar een PostScript-bestand probeert te converteren, wordt een uitzondering gegenereerd.

>[!NOTE]
>
>Zie [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63)voor meer informatie over de service PDF converteren.

### Overzicht van de stappen {#summary-of-steps}

Voer de volgende stappen uit om een PDF-document te converteren naar een PostScript-bestand:

1. Inclusief projectbestanden.
1. Maak een Convert PDF service client.
1. Verwijs naar het PDF-document dat u wilt converteren naar een PostScript-bestand.
1. Stel opties voor de uitvoering van de conversie in.
1. Converteer het PDF-document naar een PostScript-bestand.
1. Sla het PostScript-bestand op.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u de proxybestanden opnemen.

**Een conversie-PDF-client maken**

Voordat u een servicebewerking PDF converteren via programmacode kunt uitvoeren, moet u een client voor PDF-service converteren maken. Als u de Java API gebruikt, maakt u een `ConvertPdfServiceClient` object. Als u de webservice-API gebruikt, maakt u een `ConvertPDFServiceService` object.

Deze sectie gebruikt de functionaliteit van de Webdienst die in Vormen AEM wordt geïntroduceerd. Als u toegang wilt tot nieuwe functionaliteit, moet u een proxyobject maken met het `lc_version` kenmerk. (Zie &quot;Toegang tot nieuwe functionaliteit met behulp van webservices&quot; in [AEM-formulieren aanroepen met behulp van webservices](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-web-services).)

**Verwijzen naar het PDF-document dat moet worden geconverteerd naar een PostScript-bestand**

Verwijs naar het PDF-document dat u naar een PostScript-bestand wilt converteren. Zoals eerder in dit onderwerp is vermeld, moet het PDF-document een niet-interactief PDF-document zijn. Als u probeert een interactief PDF-document te converteren naar een PostScript-bestand, wordt een uitzondering gegenereerd.

**Uitvoeringsopties voor conversie instellen**

Wanneer u een PDF-document naar een PostScript-bestand converteert, kunt u runtime-opties definiëren voor het PostScript-type dat wordt gemaakt. U kunt bijvoorbeeld een PostScript-bestand van niveau 3 definiëren.

Gewoonlijk geeft het gegenereerde PostScript-bestand de grootte van het invoer-PDF-document aan. Als u de `ShrinkToFit` optie selecteert (waarmee de uitvoer van het PostScript-bestand wordt verkleind zodat het op de pagina past), ziet u geen verschil tussen het invoer-PDF-document en het gegenereerde PostScript-bestand. De `ShrinkToFit` optie is alleen van kracht als u ervoor kiest om af te drukken op een kleiner paginaformaat dan het invoer-PDF-document. Als u een kleiner paginaformaat wilt selecteren, definieert u de `PageSize` optie. Daarnaast wordt aanbevolen de `RotateAndCenter` optie in te stellen `true` om de juiste PostScript-uitvoer te verkrijgen.

Op dezelfde manier geldt dat als u de `ExpandToFit` optie selecteert (waarmee de uitvoer van het PostScript-bestand wordt aangepast aan de pagina), dit alleen als u ervoor kiest om af te drukken op een grotere pagina dan het invoer-PDF-document. Als u een grotere pagina wilt selecteren, definieert u de `PageSize` optie. Daarnaast wordt aanbevolen de `RotateAndCenter` optie in te stellen `true` om de juiste PostScript-uitvoer te verkrijgen.

>[!NOTE]
>
>Zie de `ToPSOptionsSpec` klasseverwijzing in de API-naslaggids voor [AEM-formulieren voor informatie over de runtime-waarden die u kunt instellen](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**Het PDF-document converteren naar een PostScript-bestand**

Nadat u de de dienstcliënt creeert en runtime opties plaatst, kunt u de de omzettingsverrichting van PostScript aanhalen. Voor deze bewerking is informatie nodig over het document dat moet worden geconverteerd, inclusief het PostScript-niveau dat bij voorkeur voor het doeldocument wordt gebruikt.

**Het PostScript-bestand opslaan**

Nadat u het PDF-document naar PostScript hebt geconverteerd, kunt u de uitvoer opslaan als een PostScript-bestand.

**Zie ook**

[Een PDF-document converteren naar PS met de Java API](converting-pdf-postscript-image-files.md#convert-a-pdf-document-to-ps-using-the-java-api)

[Een PDF-document naar PS converteren met de webservice-API](converting-pdf-postscript-image-files.md#convert-a-pdf-document-to-ps-using-the-web-service-api)

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Converteer PDF Service API Quick Start](/help/forms/developing/convert-pdf-service-java-api.md#convert-pdf-service-java-api-quick-start-soap)

### Een PDF-document converteren naar PS met de Java API {#convert-a-pdf-document-to-ps-using-the-java-api}

Converteer een PDF-document naar PostScript met de API (Java) voor PDF-service converteren:

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-convertpdf-client.jar, op in het klassenpad van uw Java-project.

1. Maak een Convert PDF-client.

   * Maak een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Maak een `ConvertPdfServiceClient` object door de constructor ervan te gebruiken en het `ServiceClientFactory` object door te geven.

1. Verwijs naar het PDF-document dat u wilt converteren naar een PostScript-bestand.

   * Maak een `java.io.FileInputStream` object met behulp van de constructor en geef een tekenreekswaarde door die de locatie opgeeft van het PDF-document dat u wilt converteren.
   * Maak een `com.adobe.idp.Document` object waarin het PDF-document wordt opgeslagen met de `com.adobe.idp.Document` constructor. Geef het `java.io.FileInputStream` object dat het PDF-document bevat door.

1. Stel opties voor de uitvoering van de conversie in.

   * Maak een `ToPSOptionsSpec` object door de constructor ervan aan te roepen.
   * Stel runtime-opties in door een geschikte methode aan te roepen die tot het `ToPSOptionsSpec` object behoort. Als u bijvoorbeeld het PostScript-niveau wilt definiëren dat wordt gemaakt, roept u de `ToPSOptionsSpec` methode van het object aan en geeft u een `setPsLevel` `PSLevel` opsommingswaarde door die het PostScript-niveau opgeeft. Zie de `ToPSOptionsSpec` klasseverwijzing in de API-naslaggids voor [AEM-formulieren voor informatie over alle runtime-waarden die u kunt instellen](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

1. Converteer het PDF-document naar een PostScript-bestand.

   Roep de methode van het `ConvertPdfServiceClient``toPS2` object aan en geef de volgende waarden door:

   * Een `com.adobe.idp.Document` object dat het PDF-document vertegenwoordigt dat naar een PostScript-bestand moet worden geconverteerd.
   * Een `ToPSOptionsSpec` object dat opties voor PostScript-runtime opgeeft.
   De `toPS2` methode retourneert een `Document` object dat het nieuwe PostScript-document bevat.

1. Sla het PostScript-bestand op.

   * Maak een `java.io.File` object en zorg dat de bestandsnaamextensie .ps is.
   * Roep de `Document` methode van het `copyToFile` object aan om de inhoud van het `Document` object naar het bestand te kopiëren (zorg dat u het `Document` object gebruikt dat door de `toPS2` methode is geretourneerd).

**Zie ook**

[Overzicht van de stappen](converting-pdf-postscript-image-files.md#summary-of-steps)

[Snel starten (SOAP-modus): Een PDF-document converteren naar PostScript met de Java API](/help/forms/developing/convert-pdf-service-java-api.md#quick-start-soap-mode-converting-a-pdf-document-to-postscript-using-the-java-api)

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Een PDF-document naar PS converteren met de webservice-API {#convert-a-pdf-document-to-ps-using-the-web-service-api}

Converteer een PDF-document naar PostScript met de Convert PDF Service API (webservice):

1. Inclusief projectbestanden.

   Creeer een project van Microsoft .NET dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/ConvertPDFService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een Convert PDF-client.

   * Maak een `ConvertPdfServiceClient` object met de standaardconstructor.
   * Maak een `ConvertPdfServiceClient.Endpoint.Address` object met de `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/ConvertPDFService?blob=mtom`.) U hoeft het `lc_version` kenmerk niet te gebruiken. Geef dit echter op `?blob=mtom`.
   * Maak een `System.ServiceModel.BasicHttpBinding` object door de waarde van het `ConvertPdfServiceClient.Endpoint.Binding` veld op te halen. Kiezen naar de geretourneerde waarde `BasicHttpBinding`.
   * Stel het `System.ServiceModel.BasicHttpBinding` veld van het `MessageEncoding` object in op `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam voor AEM-formulieren toe aan het veld `ConvertPdfServiceClient.ClientCredentials.UserName.UserName`.
      * Wijs de bijbehorende wachtwoordwaarde aan het veld toe `ConvertPdfServiceClient.ClientCredentials.UserName.Password`.
      * Wijs de constante waarde toe `HttpClientCredentialType.Basic` aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Wijs de constante waarde toe `BasicHttpSecurityMode.TransportCredentialOnly` aan het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Verwijs naar het PDF-document dat u wilt converteren naar een PostScript-bestand.

   * Maak een `BLOB` object met de constructor ervan. Met dit `BLOB` object wordt een PDF-document opgeslagen dat wordt geconverteerd naar een PostScript-bestand.
   * Maak een `System.IO.FileStream` object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie vertegenwoordigt van het PDF-document dat moet worden geconverteerd en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van het `System.IO.FileStream` object wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` eigenschap van het `Length` object op te halen.
   * Vul de bytearray met streamgegevens door de methode van het `System.IO.FileStream` `Read` object aan te roepen en de bytearray, de startpositie en de streamlengte door te geven om te lezen.
   * Vul het `BLOB` object door het `MTOM` veld ervan toe te wijzen met de inhoud van de bytearray.

1. Stel opties voor de uitvoering van de conversie in.

   * Maak een `ToPSOptionsSpec` object door de constructor ervan aan te roepen.
   * Stel uitvoeringsopties in door een waarde toe te wijzen aan het gegevenslid van het `ToPSOptionsSpec` object. Als u bijvoorbeeld het PostScript-niveau wilt definiëren dat wordt gemaakt, wijst u een `PSLevel` opsommingswaarde toe aan het `ToPSOptionsSpec` gegevenslid van het `psLevel` object.

1. Converteer het PDF-document naar een PostScript-bestand.

   Roep de methode van het `GeneratePDFServiceService` `toPS2` object aan en geef de volgende waarden door:

   * Een `BLOB` object dat het PDF-document vertegenwoordigt dat naar een PostScript-bestand moet worden geconverteerd
   * Een `ToPSOptionsSpec` object dat uitvoeringsopties opgeeft
   Nadat de conversie is voltooid, extraheert u de binaire gegevens die het PostScript-document vertegenwoordigen door toegang te krijgen tot de `BLOB` eigenschap van het `MTOM` object. Hiermee wordt een bytearray geretourneerd die u naar een PostScript-bestand kunt schrijven.

1. Sla het PostScript-bestand op.

   * Maak een `System.IO.FileStream` object door de constructor ervan aan te roepen. Geef een tekenreekswaarde door die de bestandslocatie van het PS-bestand vertegenwoordigt.
   * Maak een bytearray met de gegevensinhoud van het `BLOB` object dat door de `encryptPDFUsingPassword` methode is geretourneerd. Vul de bytearray met de waarde van het `BLOB` veld van het `MTOM` object.
   * Maak een `System.IO.BinaryWriter` object door de constructor ervan aan te roepen en het `System.IO.FileStream` object door te geven.
   * Schrijf de inhoud van de bytearray naar het PostScript-bestand door de methode van het `System.IO.BinaryWriter` `Write` object aan te roepen en de bytearray door te geven.

**Zie ook**

[Overzicht van de stappen](converting-pdf-postscript-image-files.md#summary-of-steps)

[AEM-formulieren aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM-formulieren aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## PDF-documenten converteren naar afbeeldingsindelingen {#converting-pdf-documents-to-image-formats}

Met de service PDF converteren kunt u PDF-documenten programmatisch converteren naar afbeeldingsindelingen, zoals JPEG, JPEG 2000, TIFF en PNG. Door een PDF-document naar een afbeeldingsbestand te converteren, kunt u het PDF-document gebruiken als afbeeldingsbestand. U kunt het image bijvoorbeeld in een inhoudbeheersysteem voor bedrijven plaatsen voor opslag.

Als u een PDF-document naar een afbeelding converteert, maakt de service PDF converteren een aparte afbeelding voor elke pagina in het document. Met andere woorden, als het document uit 20 pagina&#39;s bestaat, maakt de service PDF converteren 20 afbeeldingsbestanden. Wanneer u een PDF-document converteert naar een afbeeldingsindeling, kunt u voor elke pagina in het PDF-document of voor het gehele PDF-document één afbeeldingsbestand maken.

>[!NOTE]
>
>Zie [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63)voor meer informatie over de service PDF converteren.

### Overzicht van de stappen {#summary_of_steps-1}

Voer de volgende stappen uit om een PDF-document te converteren naar een van de ondersteunde typen:

1. Inclusief projectbestanden.
1. Maak een Convert PDF service client.
1. Hiermee haalt u het te converteren PDF-document op.
1. Stel runtime-opties in.
1. Converteer de PDF naar een afbeelding.
1. Haal de afbeeldingsbestanden op uit een verzameling.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u de proxybestanden opnemen.

**Een conversie-PDF-client maken**

Voordat u een servicebewerking PDF converteren via programmacode kunt uitvoeren, moet u een client voor PDF-service converteren maken. Als u de Java API gebruikt, maakt u een `ConvertPdfServiceClient` object. Als u de webservice-API gebruikt, maakt u een `ConvertPDFServiceService` object.

**Het te converteren PDF-document ophalen**

U moet het PDF-document opvragen om het naar een afbeelding te converteren. U kunt een interactief PDF-document niet converteren naar een afbeelding. Wanneer u dit probeert, wordt een uitzondering gegenereerd. Als u een interactief PDF-document naar een afbeeldingsbestand wilt converteren, moet u het PDF-document samenvoegen tot één laag voordat u het converteert. (Zie [PDF-documenten](/help/forms/developing/creating-document-output-streams.md#flattening-pdf-documents)afvlakken.)

**Uitvoeringsopties instellen**

U moet runtime opties instellen, zoals de afbeeldingsindeling en de resolutiewaarden. Zie de `ToImageOptionsSpec` klasseverwijzing in de API-naslaggids voor [AEM-formulieren voor informatie over de runtimewaarden](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**De PDF converteren naar een afbeelding**

Nadat u de serviceclient hebt gemaakt en runtime-opties hebt ingesteld, kunt u het PDF-document converteren naar een afbeelding. Een verzamelingsobject dat de afbeeldingen bevat, wordt geretourneerd.

**De afbeeldingsbestanden ophalen uit een verzameling**

U kunt afbeeldingsbestanden ophalen van een verzamelobject dat door de service PDF converteren wordt geretourneerd. Elk element in de verzameling is een `com.adobe.idp.Document` instantie (of een `BLOB` instantie als u webservices gebruikt) die u kunt opslaan als afbeeldingsbestand, zoals een JPG-bestand.

De indeling van het afbeeldingsbestand is afhankelijk van de optie `ImageConvertFormat` bij uitvoering. Met andere woorden, als u de `ImageConvertFormat` runtime-optie instelt op `ImageConvertFormat.JPEG`, kunt u afbeeldingsbestanden opslaan als JPG-bestanden.

**Zie ook**

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Converteer PDF Service API Quick Start](/help/forms/developing/convert-pdf-service-java-api.md#convert-pdf-service-java-api-quick-start-soap)

### Een PDF-document converteren naar afbeeldingsbestanden met de Java API {#convert-a-pdf-document-to-image-files-using-the-java-api}

Een PDF-document converteren naar een afbeeldingsindeling met de API (Java) voor PDF-service converteren:

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-convertpdf-client.jar, op in het klassenpad van uw Java-project.

1. Maak een Convert PDF-client.

   * Maak een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Maak een `ConvertPdfServiceClient` object door de constructor ervan te gebruiken en het `ServiceClientFactory` object door te geven.

1. Hiermee haalt u het te converteren PDF-document op.

   * Maak een `java.io.FileInputStream` object dat staat voor het te converteren PDF-document met de constructor ervan en geef een tekenreekswaarde door die de locatie van het PDF-document aangeeft.
   * Maak een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en het `java.io.FileInputStream` object door te geven.

1. Stel runtime-opties in.

   * Maak een `ToImageOptionsSpec` object met de constructor ervan.
   * Roep de vereiste methoden aan die bij dit object horen. Stel het afbeeldingstype bijvoorbeeld in door de `setImageConvertFormat` methode aan te roepen en een `ImageConvertFormat` opsommingswaarde door te geven die het indelingstype aangeeft.
   >[!NOTE]
   >
   >Het instellen van de `ImageConvertFormat` opsommingswaarde is verplicht.

1. Converteer de PDF naar een afbeelding.

   Roep de methode van het `ConvertPdfServiceClient` `toImage2` object aan en geef de volgende waarden door:

   * Een `com.adobe.idp.Document` object dat staat voor het PDF-bestand dat moet worden geconverteerd.
   * Een `com.adobe.livecycle.converpdfservice.client.ToImageOptionsSpec` object dat de verschillende voorkeuren voor de indeling van de doelafbeelding bevat.
   De `toImage2` methode retourneert een `java.util.List` object dat afbeeldingen bevat. Elk element in de verzameling is een `com.adobe.idp.Document` instantie.

1. Haal de afbeeldingsbestanden op uit een verzameling.

   Doorloop het `java.util.List` object om te bepalen of er afbeeldingen aanwezig zijn. Elk element is een `com.adobe.idp.Document` instantie. Sla de afbeelding op door de methode van het `com.adobe.idp.Document` object aan te roepen `copyToFile` en een `java.io.File` object door te geven.

**Zie ook**

[Snel starten (SOAP-modus): Een PDF-document converteren naar JPEG-bestanden met de Java API](/help/forms/developing/convert-pdf-service-java-api.md#quick-start-soap-mode-converting-a-pdf-document-to-jpeg-files-using-the-java-api)

### Een PDF-document converteren naar afbeeldingsbestanden met de webservice-API {#convert-a-pdf-document-to-image-files-using-the-web-service-api}

Een PDF-document converteren naar een afbeeldingsindeling met de Convert PDF Service API (webservice):

1. Inclusief projectbestanden.

   Creeer een project van Microsoft .NET dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/ConvertPDFService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een geconverteerde PDF-client.

   * Maak een `ConvertPdfServiceClient` object met de standaardconstructor.
   * Maak een `ConvertPdfServiceClient.Endpoint.Address` object met de `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/ConvertPDFService?blob=mtom`.) U hoeft het `lc_version` kenmerk niet te gebruiken. Geef dit echter op `?blob=mtom`.
   * Maak een `System.ServiceModel.BasicHttpBinding` object door de waarde van het `ConvertPdfServiceClient.Endpoint.Binding` veld op te halen. Kiezen naar de geretourneerde waarde `BasicHttpBinding`.
   * Stel het `System.ServiceModel.BasicHttpBinding` veld van het `MessageEncoding` object in op `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam voor AEM-formulieren toe aan het veld `ConvertPdfServiceClient.ClientCredentials.UserName.UserName`.
      * Wijs de bijbehorende wachtwoordwaarde aan het veld toe `ConvertPdfServiceClient.ClientCredentials.UserName.Password`.
      * Wijs de constante waarde toe `HttpClientCredentialType.Basic` aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Wijs de constante waarde toe `BasicHttpSecurityMode.TransportCredentialOnly` aan het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Hiermee haalt u het te converteren PDF-document op.

   * Maak een `BLOB` object met de constructor ervan. Met dit `BLOB` object wordt het PDF-formulier opgeslagen.
   * Maak een `System.IO.FileStream` object door de constructor ervan aan te roepen. Geef een tekenreekswaarde door die de locatie aangeeft van het PDF-formulier en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van het `System.IO.FileStream` object wordt opgeslagen. Bepaal de grootte van de bytearray door de `System.IO.FileStream` eigenschap van het `Length` object op te halen.
   * Vul de bytearray met streamgegevens door de `System.IO.FileStream` `Read` methode van het object aan te roepen. Geef de bytearray, de startpositie en de streamlengte door om te lezen.
   * Vul het `BLOB` object door het `MTOM` veld ervan toe te wijzen met de inhoud van de bytearray.

1. Stel runtime-opties in.

   * Maak een `ToImageOptionsSpec` object met de constructor ervan.
   * Roep de vereiste methoden aan die bij dit object horen. Stel bijvoorbeeld het afbeeldingstype in door de `setImageConvertFormat` methode aan te roepen en een `ImageConvertFormat` opsommingswaarde door te geven die het indelingstype aangeeft.
   >[!NOTE]
   >
   >Het instellen van de `ImageConvertFormat` opsommingswaarde is verplicht.

1. Converteer de PDF naar een afbeelding.

   Roep de methode van het `ConvertPDFServiceService` `toImage2` object aan en geef de volgende waarden door:

   * Een `BLOB` object dat staat voor het bestand dat moet worden omgezet
   * Een `ToImageOptionsSpec` object dat de verschillende voorkeuren voor de indeling van de doelafbeelding bevat
   De `toImage2` methode retourneert een `MyArrayOfBLOB` object dat de nieuwe afbeeldingsbestanden bevat.

1. Haal de afbeeldingsbestanden op uit een verzameling.

   * Bepaal het aantal elementen in het `MyArrayOfBLOB` object door de waarde van het `Count` veld op te halen. Elk element is een `BLOB` object dat de afbeelding bevat.
   * Doorloop het `MyArrayOfBLOB` object en sla elk afbeeldingsbestand op.

**Zie ook**

[AEM-formulieren aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM-formulieren aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)
