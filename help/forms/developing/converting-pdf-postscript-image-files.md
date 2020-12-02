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
workflow-type: tm+mt
source-wordcount: '2772'
ht-degree: 0%

---


# PDF converteren naar Postscript- en afbeeldingsbestanden {#converting-pdf-to-postscript-andimage-files}

**Over de Convert PDF Service**

Met de service PDF converteren worden PDF-documenten geconverteerd naar PostScript en naar een aantal afbeeldingsindelingen (JPEG, JPEG 2000, PNG en TIFF). Het converteren van een PDF-document naar PostScript is handig voor afdrukken op basis van een server zonder toezicht op elke PostScript-printer. Het converteren van een PDF-document naar een TIFF-bestand met meerdere pagina&#39;s is handig bij het archiveren van documenten in inhoudsbeheersystemen die geen PDF-documenten ondersteunen.

U kunt deze taken uitvoeren met de service PDF converteren:

* Converteer PDF-documenten naar PostScript.
* PDF-documenten converteren naar afbeeldingsindelingen.

>[!NOTE]
>
>Zie [Referentiehandleiding voor services voor AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63) voor meer informatie over de service PDF converteren.

## PDF-documenten converteren naar PostScript {#converting-pdf-documents-to-postscript}

In dit onderwerp wordt beschreven hoe u de API (Java en webservice) voor het converteren van PDF-documenten naar PostScript-bestanden kunt gebruiken. Het PDF-document dat wordt geconverteerd naar een PostScript-bestand, moet een niet-interactief PDF-document zijn. Als u een interactief PDF-document naar een PostScript-bestand probeert te converteren, wordt een uitzondering gegenereerd.

>[!NOTE]
>
>Zie [Referentiehandleiding voor services voor AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63) voor meer informatie over de service PDF converteren.

### Overzicht van stappen {#summary-of-steps}

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

Voordat u een servicebewerking PDF converteren via programmacode kunt uitvoeren, moet u een client voor PDF-service converteren maken. Als u de Java API gebruikt, maakt u een `ConvertPdfServiceClient`-object. Als u de webservice-API gebruikt, maakt u een `ConvertPDFServiceService`-object.

Deze sectie gebruikt webservicefunctionaliteit die in AEM Forms is geïntroduceerd. Om tot nieuwe functionaliteit toegang te hebben, moet u uw volmachtsvoorwerp construeren gebruikend het `lc_version` attribuut. (Zie &quot;Toegang tot nieuwe functionaliteit via webservices&quot; in [AEM Forms aanroepen met behulp van webservices](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-web-services).)

**Verwijzen naar het PDF-document dat moet worden geconverteerd naar een PostScript-bestand**

Verwijs naar het PDF-document dat u naar een PostScript-bestand wilt converteren. Zoals eerder in dit onderwerp is vermeld, moet het PDF-document een niet-interactief PDF-document zijn. Als u probeert een interactief PDF-document te converteren naar een PostScript-bestand, wordt een uitzondering gegenereerd.

**Uitvoeringsopties voor conversie instellen**

Wanneer u een PDF-document naar een PostScript-bestand converteert, kunt u runtime-opties definiëren voor het PostScript-type dat wordt gemaakt. U kunt bijvoorbeeld een PostScript-bestand van niveau 3 definiëren.

Gewoonlijk geeft het gegenereerde PostScript-bestand de grootte van het invoer-PDF-document aan. Als u de optie `ShrinkToFit` selecteert (waardoor de uitvoer van het PostScript-bestand wordt verkleind zodat het op de pagina past), ziet u geen verschil tussen het invoer-PDF-document en het gegenereerde PostScript-bestand. De optie `ShrinkToFit` wordt alleen van kracht als u ervoor kiest om af te drukken op een kleiner paginaformaat dan het invoer-PDF-document. Als u een kleiner paginaformaat wilt selecteren, definieert u de optie `PageSize`. Daarnaast wordt aanbevolen de optie `RotateAndCenter` in te stellen op `true` om de juiste PostScript-uitvoer te verkrijgen.

Op dezelfde manier geldt dat als u de optie `ExpandToFit` selecteert (waarmee de uitvoer van het PostScript-bestand wordt aangepast aan de pagina), dit alleen als u ervoor kiest om af te drukken op een groter paginaformaat dan het invoer-PDF-document. Als u een grotere pagina wilt selecteren, definieert u de optie `PageSize`. Daarnaast wordt aanbevolen de optie `RotateAndCenter` in te stellen op `true` om de juiste PostScript-uitvoer te verkrijgen.

>[!NOTE]
>
>Zie de `ToPSOptionsSpec`-klasseverwijzing in [AEM Forms API Reference](https://www.adobe.com/go/learn_aemforms_javadocs_63_en) voor informatie over de runtime waarden die u kunt instellen.

**Het PDF-document converteren naar een PostScript-bestand**

Nadat u de de dienstcliënt creeert en runtime opties plaatst, kunt u de de omzettingsverrichting van PostScript aanhalen. Voor deze bewerking is informatie nodig over het document dat moet worden geconverteerd, inclusief het PostScript-niveau dat bij voorkeur voor het doeldocument wordt gebruikt.

**Het PostScript-bestand opslaan**

Nadat u het PDF-document naar PostScript hebt geconverteerd, kunt u de uitvoer opslaan als een PostScript-bestand.

**Zie ook**

[Een PDF-document converteren naar PS met de Java API](converting-pdf-postscript-image-files.md#convert-a-pdf-document-to-ps-using-the-java-api)

[Een PDF-document naar PS converteren met de webservice-API](converting-pdf-postscript-image-files.md#convert-a-pdf-document-to-ps-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Converteer PDF Service API Quick Start](/help/forms/developing/convert-pdf-service-java-api.md#convert-pdf-service-java-api-quick-start-soap)

### Een PDF-document converteren naar PS met de Java API {#convert-a-pdf-document-to-ps-using-the-java-api}

Converteer een PDF-document naar PostScript met de API (Java) voor PDF-service converteren:

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-convertpdf-client.jar, op in het klassenpad van uw Java-project.

1. Maak een Convert PDF-client.

   * Maak een `ServiceClientFactory`-object dat verbindingseigenschappen bevat.
   * Maak een `ConvertPdfServiceClient`-object door de constructor ervan te gebruiken en het object `ServiceClientFactory` door te geven.

1. Verwijs naar het PDF-document dat u wilt converteren naar een PostScript-bestand.

   * Maak een `java.io.FileInputStream`-object met de constructor ervan en geef een tekenreekswaarde door die de locatie aangeeft van het PDF-document dat u wilt converteren.
   * Maak een `com.adobe.idp.Document`-object waarmee het PDF-document wordt opgeslagen met de constructor `com.adobe.idp.Document`. Geef het object `java.io.FileInputStream` dat het PDF-document bevat door.

1. Stel opties voor de uitvoering van de conversie in.

   * Maak een `ToPSOptionsSpec`-object door de constructor ervan aan te roepen.
   * Stel uitvoeringsopties in door een geschikte methode aan te roepen die tot het object `ToPSOptionsSpec` behoort. Als u bijvoorbeeld het PostScript-niveau wilt definiëren dat wordt gemaakt, roept u de methode `setPsLevel` van het object `ToPSOptionsSpec` aan en geeft u een opsommingswaarde `PSLevel` door die het PostScript-niveau opgeeft. Voor informatie over alle runtime waarden die u kunt plaatsen, zie `ToPSOptionsSpec` klassenverwijzing in [AEM Forms API Verwijzing](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

1. Converteer het PDF-document naar een PostScript-bestand.

   Roep de methode `ConvertPdfServiceClient`van het object `toPS2` aan en geef de volgende waarden door:

   * Een `com.adobe.idp.Document`-object dat het PDF-document vertegenwoordigt dat naar een PostScript-bestand moet worden geconverteerd.
   * Een `ToPSOptionsSpec`-object dat PostScript-runtimeopties opgeeft.

   De methode `toPS2` retourneert een `Document`-object dat het nieuwe PostScript-document bevat.

1. Sla het PostScript-bestand op.

   * Maak een `java.io.File`-object en zorg dat de bestandsnaamextensie .ps is.
   * Roep de methode `Document` van het object `copyToFile` aan om de inhoud van het object `Document` naar het bestand te kopiëren (zorg dat u het object `Document` gebruikt dat door de methode `toPS2` is geretourneerd).

**Zie ook**

[Overzicht van de stappen](converting-pdf-postscript-image-files.md#summary-of-steps)

[Snel starten (SOAP-modus): Een PDF-document converteren naar PostScript met de Java API](/help/forms/developing/convert-pdf-service-java-api.md#quick-start-soap-mode-converting-a-pdf-document-to-postscript-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Een PDF-document converteren naar PS met de webservice-API {#convert-a-pdf-document-to-ps-using-the-web-service-api}

Converteer een PDF-document naar PostScript met de Convert PDF Service API (webservice):

1. Inclusief projectbestanden.

   Creeer een project van Microsoft .NET dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/ConvertPDFService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervang `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een Convert PDF-client.

   * Maak een `ConvertPdfServiceClient`-object met de standaardconstructor.
   * Maak een `ConvertPdfServiceClient.Endpoint.Address`-object met de constructor `System.ServiceModel.EndpointAddress`. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/ConvertPDFService?blob=mtom`). U hoeft het `lc_version`-kenmerk niet te gebruiken. Geef `?blob=mtom` echter op.
   * Maak een `System.ServiceModel.BasicHttpBinding`-object door de waarde van het veld `ConvertPdfServiceClient.Endpoint.Binding` op te halen. Cast de terugkeerwaarde aan `BasicHttpBinding`.
   * Stel het veld `System.ServiceModel.BasicHttpBinding` van het object `MessageEncoding` in op `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam voor het AEM aan het veld `ConvertPdfServiceClient.ClientCredentials.UserName.UserName` toe.
      * Wijs de overeenkomstige wachtwoordwaarde aan het gebied `ConvertPdfServiceClient.ClientCredentials.UserName.Password` toe.
      * Wijs de constante waarde `HttpClientCredentialType.Basic` aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType` toe.
      * Wijs de constante waarde `BasicHttpSecurityMode.TransportCredentialOnly` aan het veld `BasicHttpBindingSecurity.Security.Mode` toe.

1. Verwijs naar het PDF-document dat u wilt converteren naar een PostScript-bestand.

   * Maak een `BLOB`-object met de constructor ervan. Met het object `BLOB` wordt een PDF-document opgeslagen dat is geconverteerd naar een PostScript-bestand.
   * Maak een `System.IO.FileStream`-object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie vertegenwoordigt van het PDF-document dat moet worden geconverteerd en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van het object `System.IO.FileStream` wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de eigenschap `System.IO.FileStream` van het object `Length` op te halen.
   * Vul de bytearray met streamgegevens door de methode `Read` van het object `System.IO.FileStream` aan te roepen en de bytearray, startpositie en streamlengte door te geven om te lezen.
   * Vul het `BLOB`-object door het `MTOM`-veld toe te wijzen met de inhoud van de bytearray.

1. Stel opties voor de uitvoering van de conversie in.

   * Maak een `ToPSOptionsSpec`-object door de constructor ervan aan te roepen.
   * Stel runtime-opties in door een waarde toe te wijzen aan het gegevenslid van het object `ToPSOptionsSpec`. Als u bijvoorbeeld het PostScript-niveau wilt definiëren dat wordt gemaakt, wijst u een `PSLevel`-opsommingswaarde toe aan het `ToPSOptionsSpec`-gegevenslid van het `psLevel`-object.

1. Converteer het PDF-document naar een PostScript-bestand.

   Roep de methode `toPS2` van het object `GeneratePDFServiceService` aan en geef de volgende waarden door:

   * Een `BLOB`-object dat het PDF-document vertegenwoordigt dat naar een PostScript-bestand moet worden geconverteerd
   * Een `ToPSOptionsSpec`-object dat uitvoeringsopties opgeeft

   Nadat de conversie is voltooid, extraheert u de binaire gegevens die het PostScript-document vertegenwoordigen door de eigenschap `BLOB` van het `MTOM`-object te openen. Hiermee wordt een bytearray geretourneerd die u naar een PostScript-bestand kunt schrijven.

1. Sla het PostScript-bestand op.

   * Maak een `System.IO.FileStream`-object door de constructor ervan aan te roepen. Geef een tekenreekswaarde door die de bestandslocatie van het PS-bestand vertegenwoordigt.
   * Maak een bytearray met de gegevensinhoud van het object `BLOB` dat door de methode `encryptPDFUsingPassword` is geretourneerd. Vul de bytearray met de waarde van het veld `BLOB` van het object `MTOM`.
   * Maak een `System.IO.BinaryWriter`-object door de constructor ervan aan te roepen en het object `System.IO.FileStream` door te geven.
   * Schrijf de inhoud van de bytearray naar het PostScript-bestand door de methode `Write` van het object `System.IO.BinaryWriter` aan te roepen en de bytearray door te geven.

**Zie ook**

[Overzicht van de stappen](converting-pdf-postscript-image-files.md#summary-of-steps)

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## PDF-documenten converteren naar afbeeldingsindelingen {#converting-pdf-documents-to-image-formats}

Met de service PDF converteren kunt u PDF-documenten programmatisch converteren naar afbeeldingsindelingen, zoals JPEG, JPEG 2000, TIFF en PNG. Door een PDF-document naar een afbeeldingsbestand te converteren, kunt u het PDF-document gebruiken als afbeeldingsbestand. U kunt het image bijvoorbeeld in een inhoudbeheersysteem voor bedrijven plaatsen voor opslag.

Als u een PDF-document naar een afbeelding converteert, maakt de service PDF converteren een aparte afbeelding voor elke pagina in het document. Met andere woorden, als het document uit 20 pagina&#39;s bestaat, maakt de service PDF converteren 20 afbeeldingsbestanden. Wanneer u een PDF-document converteert naar een afbeeldingsindeling, kunt u voor elke pagina in het PDF-document of voor het gehele PDF-document één afbeeldingsbestand maken.

>[!NOTE]
>
>Zie [Referentiehandleiding voor services voor AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63) voor meer informatie over de service PDF converteren.

### Overzicht van stappen {#summary_of_steps-1}

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

Voordat u een servicebewerking PDF converteren via programmacode kunt uitvoeren, moet u een client voor PDF-service converteren maken. Als u de Java API gebruikt, maakt u een `ConvertPdfServiceClient`-object. Als u de webservice-API gebruikt, maakt u een `ConvertPDFServiceService`-object.

**Het te converteren PDF-document ophalen**

U moet het PDF-document opvragen om het naar een afbeelding te converteren. U kunt een interactief PDF-document niet converteren naar een afbeelding. Wanneer u dit probeert, wordt een uitzondering gegenereerd. Als u een interactief PDF-document naar een afbeeldingsbestand wilt converteren, moet u het PDF-document samenvoegen tot één laag voordat u het converteert. (Zie [PDF-documenten afvlakken](/help/forms/developing/creating-document-output-streams.md#flattening-pdf-documents).)

**Uitvoeringsopties instellen**

U moet runtime opties instellen, zoals de afbeeldingsindeling en de resolutiewaarden. Zie de `ToImageOptionsSpec`-klasseverwijzing in [AEM Forms API Reference](https://www.adobe.com/go/learn_aemforms_javadocs_63_en) voor informatie over de runtime waarden.

**De PDF converteren naar een afbeelding**

Nadat u de serviceclient hebt gemaakt en runtime-opties hebt ingesteld, kunt u het PDF-document converteren naar een afbeelding. Een verzamelingsobject dat de afbeeldingen bevat, wordt geretourneerd.

**De afbeeldingsbestanden ophalen uit een verzameling**

U kunt afbeeldingsbestanden ophalen van een verzamelobject dat door de service PDF converteren wordt geretourneerd. Elk element in de verzameling is een `com.adobe.idp.Document`-instantie (of een `BLOB`-instantie als u webservices gebruikt) die u kunt opslaan als een afbeeldingsbestand, zoals een JPG-bestand.

De indeling van het afbeeldingsbestand is afhankelijk van de runtimeoptie `ImageConvertFormat`. Met andere woorden, als u de runtime-optie `ImageConvertFormat` instelt op `ImageConvertFormat.JPEG`, kunt u afbeeldingsbestanden opslaan als JPG-bestanden.

**Zie ook**

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Converteer PDF Service API Quick Start](/help/forms/developing/convert-pdf-service-java-api.md#convert-pdf-service-java-api-quick-start-soap)

### Een PDF-document converteren naar afbeeldingsbestanden met de Java API {#convert-a-pdf-document-to-image-files-using-the-java-api}

Een PDF-document converteren naar een afbeeldingsindeling met de API (Java) voor PDF-service converteren:

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-convertpdf-client.jar, op in het klassenpad van uw Java-project.

1. Maak een Convert PDF-client.

   * Maak een `ServiceClientFactory`-object dat verbindingseigenschappen bevat.
   * Maak een `ConvertPdfServiceClient`-object door de constructor ervan te gebruiken en het object `ServiceClientFactory` door te geven.

1. Hiermee haalt u het te converteren PDF-document op.

   * Maak een `java.io.FileInputStream`-object dat het te converteren PDF-document vertegenwoordigt met de constructor ervan en geef een tekenreekswaarde door die de locatie van het PDF-document aangeeft.
   * Maak een `com.adobe.idp.Document`-object door de constructor ervan te gebruiken en het object `java.io.FileInputStream` door te geven.

1. Stel runtime-opties in.

   * Maak een `ToImageOptionsSpec`-object met de constructor ervan.
   * Roep de vereiste methoden aan die bij dit object horen. Stel het afbeeldingstype bijvoorbeeld in door de methode `setImageConvertFormat` aan te roepen en een opsommingswaarde `ImageConvertFormat` door te geven die het indelingstype aangeeft.

   >[!NOTE]
   >
   >Het instellen van de opsommingswaarde `ImageConvertFormat` is verplicht.

1. Converteer de PDF naar een afbeelding.

   Roep de methode `toImage2` van het object `ConvertPdfServiceClient` aan en geef de volgende waarden door:

   * Een `com.adobe.idp.Document`-object dat het te converteren PDF-bestand vertegenwoordigt.
   * Een object `com.adobe.livecycle.converpdfservice.client.ToImageOptionsSpec` dat de verschillende voorkeuren voor de indeling van de doelafbeelding bevat.

   De methode `toImage2` retourneert een `java.util.List`-object dat afbeeldingen bevat. Elk element in de verzameling is een `com.adobe.idp.Document`-instantie.

1. Haal de afbeeldingsbestanden op uit een verzameling.

   Doorloop het object `java.util.List` om te bepalen of er afbeeldingen aanwezig zijn. Elk element is een `com.adobe.idp.Document` instantie. Sla de afbeelding op door de methode `copyToFile` van het object `com.adobe.idp.Document` aan te roepen en een object `java.io.File` door te geven.

**Zie ook**

[Snel starten (SOAP-modus): Een PDF-document converteren naar JPEG-bestanden met de Java API](/help/forms/developing/convert-pdf-service-java-api.md#quick-start-soap-mode-converting-a-pdf-document-to-jpeg-files-using-the-java-api)

### Een PDF-document converteren naar afbeeldingsbestanden met de API {#convert-a-pdf-document-to-image-files-using-the-web-service-api} voor webservices

Een PDF-document converteren naar een afbeeldingsindeling met de Convert PDF Service API (webservice):

1. Inclusief projectbestanden.

   Creeer een project van Microsoft .NET dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/ConvertPDFService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervang `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een geconverteerde PDF-client.

   * Maak een `ConvertPdfServiceClient`-object met de standaardconstructor.
   * Maak een `ConvertPdfServiceClient.Endpoint.Address`-object met de constructor `System.ServiceModel.EndpointAddress`. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/ConvertPDFService?blob=mtom`). U hoeft het `lc_version`-kenmerk niet te gebruiken. Geef `?blob=mtom` echter op.
   * Maak een `System.ServiceModel.BasicHttpBinding`-object door de waarde van het veld `ConvertPdfServiceClient.Endpoint.Binding` op te halen. Cast de terugkeerwaarde aan `BasicHttpBinding`.
   * Stel het veld `System.ServiceModel.BasicHttpBinding` van het object `MessageEncoding` in op `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam voor het AEM aan het veld `ConvertPdfServiceClient.ClientCredentials.UserName.UserName` toe.
      * Wijs de overeenkomstige wachtwoordwaarde aan het gebied `ConvertPdfServiceClient.ClientCredentials.UserName.Password` toe.
      * Wijs de constante waarde `HttpClientCredentialType.Basic` aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType` toe.
      * Wijs de constante waarde `BasicHttpSecurityMode.TransportCredentialOnly` aan het veld `BasicHttpBindingSecurity.Security.Mode` toe.

1. Hiermee haalt u het te converteren PDF-document op.

   * Maak een `BLOB`-object met de constructor ervan. Met dit `BLOB`-object wordt het PDF-formulier opgeslagen.
   * Maak een `System.IO.FileStream`-object door de constructor ervan aan te roepen. Geef een tekenreekswaarde door die de locatie aangeeft van het PDF-formulier en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van het object `System.IO.FileStream` wordt opgeslagen. Bepaal de grootte van de bytearray door de `System.IO.FileStream`-eigenschap van het object `Length` op te halen.
   * Vul de bytearray met streamgegevens door de methode `Read` van het object `System.IO.FileStream` aan te roepen. Geef de bytearray, de startpositie en de streamlengte door om te lezen.
   * Vul het `BLOB`-object door het `MTOM`-veld toe te wijzen met de inhoud van de bytearray.

1. Stel runtime-opties in.

   * Maak een `ToImageOptionsSpec`-object met de constructor ervan.
   * Roep de vereiste methoden aan die bij dit object horen. Stel het afbeeldingstype bijvoorbeeld in door de methode `setImageConvertFormat` aan te roepen en een opsommingswaarde `ImageConvertFormat` door te geven die het indelingstype aangeeft.

   >[!NOTE]
   >
   >Het instellen van de opsommingswaarde `ImageConvertFormat` is verplicht.

1. Converteer de PDF naar een afbeelding.

   Roep de methode `toImage2` van het object `ConvertPDFServiceService` aan en geef de volgende waarden door:

   * Een `BLOB`-object dat het te converteren bestand vertegenwoordigt
   * Een `ToImageOptionsSpec`-object dat de verschillende voorkeuren voor de indeling van de doelafbeelding bevat

   De methode `toImage2` retourneert een `MyArrayOfBLOB`-object dat de zojuist gemaakte afbeeldingsbestanden bevat.

1. Haal de afbeeldingsbestanden op uit een verzameling.

   * Bepaal het aantal elementen in het `MyArrayOfBLOB` voorwerp door de waarde van zijn `Count` gebied te krijgen. Elk element is een `BLOB`-object dat de afbeelding bevat.
   * Doorloop het object `MyArrayOfBLOB` en sla elk afbeeldingsbestand op.

**Zie ook**

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)
