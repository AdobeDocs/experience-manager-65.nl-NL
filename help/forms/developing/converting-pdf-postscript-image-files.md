---
title: PDF converteren naar PostScript- en afbeeldingsbestanden
description: Met de service PDF converteren kunt u PDF-documenten converteren naar PostScript en naar verschillende indelingen voor afbeeldingen (JPEG, JPEG 2000, PNG en TIFF) met behulp van de API voor Java en Web Service API.
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

**Voorbeelden en voorbeelden in dit document gelden alleen voor AEM Forms in JEE-omgeving.**

**Over de Convert PDF Service**

Met de service PDF converteren worden PDF-documenten geconverteerd naar PostScript en naar verschillende afbeeldingsindelingen (JPEG, JPEG 2000, PNG en TIFF). Het converteren van een PDF-document naar PostScript is handig voor afdrukken op basis van een server zonder toezicht op elke PostScript-printer. Het omzetten van een PDF-document in een TIFF-bestand met meerdere pagina&#39;s is handig bij het archiveren van documenten in systemen voor inhoudsbeheer die geen ondersteuning bieden voor PDF-documenten.

U kunt deze taken uitvoeren met de service PDF converteren:

* PDF-documenten converteren naar PostScript.
* Zet PDF-documenten om in afbeeldingsindelingen.

>[!NOTE]
>
>Zie voor meer informatie over de service PDF converteren [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## PDF-documenten converteren naar PostScript {#converting-pdf-documents-to-postscript}

In dit onderwerp wordt beschreven hoe u de API voor PDF-service converteren (Java en webservice) kunt gebruiken om PDF-documenten programmatisch om te zetten in PostScript-bestanden. Het PDF-document dat wordt geconverteerd naar een PostScript-bestand, moet een niet-interactief PDF-document zijn. Dit betekent dat als u probeert een interactief PDF-document om te zetten in een PostScript-bestand, een uitzondering wordt gegenereerd.

>[!NOTE]
>
>Zie voor meer informatie over de service PDF converteren [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary-of-steps}

Voer de volgende stappen uit om een PDF-document om te zetten in een PostScript-bestand:

1. Inclusief projectbestanden.
1. Maak een Convert PDF service-client.
1. Verwijs naar het PDF-document dat u wilt converteren naar een PostScript-bestand.
1. Stel opties voor de uitvoering van de conversie in.
1. Zet het PDF-document om in een PostScript-bestand.
1. Sla het PostScript-bestand op.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u de proxybestanden opnemen.

**Een Convert PDF-client maken**

Voordat u programmatically een Convert PDF de dienstverrichting kunt uitvoeren, moet u een Convert PDF de dienstcliënt creëren. Als u de Java API gebruikt, maakt u een `ConvertPdfServiceClient` object. Als u de webservice-API gebruikt, maakt u een `ConvertPDFServiceService` object.

Deze sectie gebruikt webservicefunctionaliteit die in AEM Forms is geïntroduceerd. Als u toegang wilt tot nieuwe functionaliteit, moet u het proxyobject maken met de `lc_version` kenmerk. (Zie &quot;Toegang tot nieuwe functionaliteit via webservices&quot; in [AEM Forms aanroepen met webservices](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-web-services).)

**Verwijs naar het PDF-document dat u wilt converteren naar een PostScript-bestand**

Verwijs naar het PDF-document dat u naar een PostScript-bestand wilt converteren. Zoals eerder in dit onderwerp is vermeld, moet het PDF-document een niet-interactief PDF-document zijn. Als u probeert een interactief PDF-document om te zetten in een PostScript-bestand, wordt een uitzondering gegenereerd.

**Uitvoeringsopties voor conversie instellen**

Wanneer u een PDF-document naar een PostScript-bestand converteert, kunt u runtime-opties definiëren waarmee het PostScript-type wordt opgegeven dat wordt gemaakt. U kunt bijvoorbeeld een PostScript-bestand van niveau 3 definiëren.

Doorgaans geeft het gegenereerde PostScript-bestand de grootte van het invoer-PDF-document aan. Als u `ShrinkToFit` (waardoor de uitvoer van het PostScript-bestand wordt verkleind zodat het op de pagina past), ziet u geen verschil tussen het invoerdocument en het gegenereerde PostScript-PDF-bestand. De `ShrinkToFit` Deze optie is alleen van kracht als u ervoor kiest om af te drukken op een kleiner paginaformaat dan het invoerdocument PDF. Als u een kleiner paginaformaat wilt selecteren, definieert u de optie `PageSize` -optie. Daarnaast wordt u aangeraden het `RotateAndCenter` optie voor `true` om de juiste PostScript-uitvoer te verkrijgen.

En als u de optie `ExpandToFit` (waarmee de uitvoer van het PostScript-bestand wordt uitgebreid zodat het op de pagina past), heeft deze optie alleen effect als u ervoor kiest om af te drukken op een grotere pagina dan het invoerdocument PDF. Als u een groter paginaformaat wilt selecteren, definieert u de optie `PageSize` -optie. Daarnaast wordt u aangeraden het `RotateAndCenter` optie voor `true` om de juiste PostScript-uitvoer te verkrijgen.

>[!NOTE]
>
>Voor informatie over de runtime waarden die u kunt plaatsen, zie `ToPSOptionsSpec` klasseverwijzing in [AEM Forms API-naslag](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**Het PDF-document converteren naar een PostScript-bestand**

Nadat u de de dienstcliënt creeert en runtime opties plaatst, kunt u de de omzettingsverrichting van PostScript aanhalen. Voor deze bewerking is informatie nodig over het document dat moet worden geconverteerd, inclusief het PostScript-niveau dat bij voorkeur voor het doeldocument wordt gebruikt.

**Het PostScript-bestand opslaan**

Nadat u het PDF-document hebt omgezet in PostScript, kunt u de uitvoer opslaan als een PostScript-bestand.

**Zie ook**

[Een PDF-document naar PS converteren met de Java API](converting-pdf-postscript-image-files.md#convert-a-pdf-document-to-ps-using-the-java-api)

[Een PDF-document naar PS converteren met de webservice-API](converting-pdf-postscript-image-files.md#convert-a-pdf-document-to-ps-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Snel aan de slag met de PDF Service API](/help/forms/developing/convert-pdf-service-java-api.md#convert-pdf-service-java-api-quick-start-soap)

### Een PDF-document naar PS converteren met de Java API {#convert-a-pdf-document-to-ps-using-the-java-api}

Converteer een PDF-document naar PostScript met de Java-API (Convert PDF Service):

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-convertpdf-client.jar, op in het klassepad van uw Java-project.

1. Maak een Convert PDF-client.

   * Een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Een `ConvertPdfServiceClient` object door de constructor ervan te gebruiken en de `ServiceClientFactory` object.

1. Verwijs naar het PDF-document dat u wilt converteren naar een PostScript-bestand.

   * Een `java.io.FileInputStream` -object door de constructor ervan te gebruiken en een tekenreekswaarde door te geven die de locatie aangeeft van het PDF-document dat moet worden omgezet.
   * Een `com.adobe.idp.Document` object dat het PDF-document opslaat met het gereedschap `com.adobe.idp.Document` constructor. Geef de `java.io.FileInputStream` object dat het PDF-document bevat.

1. Stel opties voor de uitvoering van de conversie in.

   * Een `ToPSOptionsSpec` object door de constructor ervan aan te roepen.
   * Stel runtime-opties in door een geschikte methode aan te roepen die tot de `ToPSOptionsSpec` object. Als u bijvoorbeeld het PostScript-niveau wilt definiëren dat wordt gemaakt, roept u het `ToPSOptionsSpec` object `setPsLevel` methode en een `PSLevel` opsommingswaarde die het PostScript-niveau opgeeft. Voor informatie over alle runtime waarden die u kunt plaatsen, zie `ToPSOptionsSpec` klasseverwijzing in [AEM Forms API-naslag](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

1. Zet het PDF-document om in een PostScript-bestand.

   De `ConvertPdfServiceClient`object `toPS2` en geeft de volgende waarden door:

   * A `com.adobe.idp.Document` object dat staat voor het PDF-document dat naar een PostScript-bestand moet worden geconverteerd.
   * A `ToPSOptionsSpec` object dat opties voor PostScript-runtime opgeeft.

   De `toPS2` methode retourneert een `Document` -object dat het nieuwe PostScript-document bevat.

1. Sla het PostScript-bestand op.

   * Een `java.io.File` -object en zorg ervoor dat de bestandsnaamextensie .ps is.
   * De `Document` object `copyToFile` methode om de inhoud van de `Document` object naar het bestand (gebruik de `Document` object dat is geretourneerd door de `toPS2` methode).

**Zie ook**

[Overzicht van de stappen](converting-pdf-postscript-image-files.md#summary-of-steps)

[Snel starten (SOAP modus): een PDF-document converteren naar PostScript met de Java API](/help/forms/developing/convert-pdf-service-java-api.md#quick-start-soap-mode-converting-a-pdf-document-to-postscript-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Een PDF-document naar PS converteren met de webservice-API {#convert-a-pdf-document-to-ps-using-the-web-service-api}

Converteer een PDF-document naar PostScript met de Convert PDF Service API (webservice):

1. Inclusief projectbestanden.

   Creeer een Microsoft .NET project dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/ConvertPDFService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` met het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een Convert PDF-client.

   * Een `ConvertPdfServiceClient` object met de standaardconstructor.
   * Een `ConvertPdfServiceClient.Endpoint.Address` object door het `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/ConvertPDFService?blob=mtom`.) U hoeft de `lc_version` kenmerk. Geef echter `?blob=mtom`.
   * Een `System.ServiceModel.BasicHttpBinding` object door de waarde van het object op te halen `ConvertPdfServiceClient.Endpoint.Binding` veld. De geretourneerde waarde omzetten in `BasicHttpBinding`.
   * Stel de `System.ServiceModel.BasicHttpBinding` object `MessageEncoding` veld naar `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld toe `ConvertPdfServiceClient.ClientCredentials.UserName.UserName`.
      * De bijbehorende wachtwoordwaarde aan het veld toewijzen `ConvertPdfServiceClient.ClientCredentials.UserName.Password`.
      * De constante waarde toewijzen `HttpClientCredentialType.Basic` naar het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * De constante waarde toewijzen `BasicHttpSecurityMode.TransportCredentialOnly` naar het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Verwijs naar het PDF-document dat u wilt converteren naar een PostScript-bestand.

   * Een `BLOB` object met behulp van de constructor. De `BLOB` -object wordt gebruikt om een PDF-document op te slaan dat wordt omgezet in een PostScript-bestand.
   * Een `System.IO.FileStream` -object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie vertegenwoordigt van het PDF-document dat moet worden omgezet en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van de `System.IO.FileStream` object. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` object `Length` eigenschap.
   * De bytearray vullen met streamgegevens door de `System.IO.FileStream` object `Read` en het doorgeven van de bytearray, de startpositie en de streamlengte om te lezen.
   * Vul de `BLOB` object door het toe te wijzen `MTOM` veld met de inhoud van de bytearray.

1. Stel opties voor de uitvoering van de conversie in.

   * Een `ToPSOptionsSpec` object door de constructor ervan aan te roepen.
   * Stel runtime-opties in door een waarde toe te wijzen aan de `ToPSOptionsSpec` lid van objectgegevens. Als u bijvoorbeeld het PostScript-niveau wilt definiëren dat wordt gemaakt, wijst u een `PSLevel` opsommingswaarde voor de `ToPSOptionsSpec` object `psLevel` lid.

1. Zet het PDF-document om in een PostScript-bestand.

   De `GeneratePDFServiceService` object `toPS2` en geeft de volgende waarden door:

   * A `BLOB` object dat staat voor het PDF-document dat moet worden omgezet in een PostScript-bestand
   * A `ToPSOptionsSpec` object dat uitvoeringsopties opgeeft

   Nadat de conversie is voltooid, extraheert u de binaire gegevens die het PostScript-document vertegenwoordigen door het document te openen `BLOB` object `MTOM` eigenschap. Hiermee wordt een bytearray geretourneerd die u naar een PostScript-bestand kunt schrijven.

1. Sla het PostScript-bestand op.

   * Een `System.IO.FileStream` object door de constructor ervan aan te roepen. Geef een tekenreekswaarde door die de bestandslocatie van het PS-bestand vertegenwoordigt.
   * Maak een bytearray waarin de gegevensinhoud van de `BLOB` object dat is geretourneerd door de `encryptPDFUsingPassword` methode. Vul de bytearray met de waarde van de `BLOB` object `MTOM` veld.
   * Een `System.IO.BinaryWriter` object door de constructor aan te roepen en de `System.IO.FileStream` object.
   * Schrijf de inhoud van de bytearray naar het PostScript-bestand door het `System.IO.BinaryWriter` object `Write` en geeft u de bytearray door.

**Zie ook**

[Overzicht van de stappen](converting-pdf-postscript-image-files.md#summary-of-steps)

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## PDF-documenten omzetten in afbeeldingsindelingen {#converting-pdf-documents-to-image-formats}

Met de service PDF converteren kunt u PDF-documenten programmatisch converteren naar afbeeldingsindelingen, zoals JPEG, JPEG 2000, TIFF en PNG. Door een PDF-document om te zetten in een afbeeldingsbestand, kunt u het PDF-document gebruiken als een afbeeldingsbestand. U kunt het image bijvoorbeeld in een inhoudbeheersysteem voor bedrijven plaatsen voor opslag.

Wanneer u een PDF-document omzet in een afbeelding, maakt de service PDF omzetten een aparte afbeelding voor elke pagina in het document. Met andere woorden, als het document uit 20 pagina&#39;s bestaat, maakt de service PDF converteren 20 afbeeldingsbestanden. Wanneer u een PDF-document omzet in een afbeeldingsindeling, kunt u afzonderlijke afbeeldingen maken voor elke pagina in het PDF-document of één afbeeldingsbestand voor het gehele PDF-document.

>[!NOTE]
>
>Zie voor meer informatie over de service PDF converteren [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary_of_steps-1}

Voer de volgende stappen uit om een PDF-document te converteren naar een van de ondersteunde typen:

1. Inclusief projectbestanden.
1. Maak een Convert PDF service-client.
1. Haal het PDF-document op dat u wilt converteren.
1. Stel runtime-opties in.
1. Zet de PDF om in een afbeelding.
1. Haal de afbeeldingsbestanden op uit een verzameling.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u de proxybestanden opnemen.

**Een Convert PDF-client maken**

Voordat u programmatically een Convert PDF de dienstverrichting kunt uitvoeren, moet u een Convert PDF de dienstcliënt creëren. Als u de Java API gebruikt, maakt u een `ConvertPdfServiceClient` object. Als u de webservice-API gebruikt, maakt u een `ConvertPDFServiceService` object.

**Het te converteren PDF-document ophalen**

Haal het PDF-document op dat u wilt omzetten in een afbeelding. U kunt een interactief PDF-document niet omzetten in een afbeelding. Wanneer u dit probeert, wordt een uitzondering gegenereerd. Als u een interactief PDF-document wilt converteren naar een afbeeldingsbestand, moet u het PDF-document samenvoegen voordat u het converteert. (Zie [PDF-documenten afvlakken](/help/forms/developing/creating-document-output-streams.md#flattening-pdf-documents).)

**Uitvoeringsopties instellen**

Stel runtime-opties in, zoals de afbeeldingsindeling en de resolutiewaarden. Voor informatie over de runtime waarden, zie `ToImageOptionsSpec` klasseverwijzing in [AEM Forms API-naslag](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**De PDF omzetten in een afbeelding**

Nadat u de de dienstcliënt creeert en runtime opties plaatst, kunt u het document van de PDF in een beeld omzetten. Een verzamelingsobject dat de afbeeldingen bevat, wordt geretourneerd.

**De afbeeldingsbestanden ophalen uit een verzameling**

U kunt afbeeldingsbestanden ophalen uit een verzamelingsobject dat wordt geretourneerd door de service PDF converteren. Elk element in de verzameling is een `com.adobe.idp.Document` instantie (of een `BLOB` -instantie als u webservices gebruikt) die u kunt opslaan als een afbeeldingsbestand, zoals een JPG-bestand.

De indeling van het afbeeldingsbestand is afhankelijk van de `ImageConvertFormat` uitvoeringsoptie. Dat wil zeggen, als u de `ImageConvertFormat` runtime-optie voor `ImageConvertFormat.JPEG`kunt u afbeeldingsbestanden opslaan als JPG-bestanden.

**Zie ook**

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Snel aan de slag met de PDF Service API](/help/forms/developing/convert-pdf-service-java-api.md#convert-pdf-service-java-api-quick-start-soap)

### Een PDF-document converteren naar afbeeldingsbestanden met de Java API {#convert-a-pdf-document-to-image-files-using-the-java-api}

Een PDF-document converteren naar een afbeeldingsindeling met de API (Java) voor de convertservice PDF:

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-convertpdf-client.jar, op in het klassepad van uw Java-project.

1. Maak een Convert PDF-client.

   * Een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Een `ConvertPdfServiceClient` object door de constructor ervan te gebruiken en de `ServiceClientFactory` object.

1. Haal het PDF-document op dat u wilt converteren.

   * Een `java.io.FileInputStream` object dat staat voor het PDF-document dat moet worden geconverteerd met de constructor ervan en dat een tekenreekswaarde doorgeeft die de locatie van het PDF-document aangeeft.
   * Een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en de `java.io.FileInputStream` object.

1. Stel runtime-opties in.

   * Een `ToImageOptionsSpec` object met behulp van de constructor.
   * Roep de vereiste methoden aan die bij dit object horen. Stel bijvoorbeeld het afbeeldingstype in door het `setImageConvertFormat` methode en een `ImageConvertFormat` enum-waarde die het indelingstype aangeeft.

   >[!NOTE]
   >
   >De instelling van `ImageConvertFormat` opsommingswaarde is verplicht.

1. Zet de PDF om in een afbeelding.

   De `ConvertPdfServiceClient` object `toImage2` en geeft de volgende waarden door:

   * A `com.adobe.idp.Document` object dat staat voor het PDF-bestand dat moet worden omgezet.
   * A `com.adobe.livecycle.converpdfservice.client.ToImageOptionsSpec` -object dat de verschillende voorkeuren voor de indeling van de doelafbeelding bevat.

   De `toImage2` methode retourneert een `java.util.List` object dat afbeeldingen bevat. Elk element in de verzameling is een `com.adobe.idp.Document` -instantie.

1. Haal de afbeeldingsbestanden op uit een verzameling.

   Doorlopen `java.util.List` om te bepalen of er afbeeldingen aanwezig zijn. Elk element is een `com.adobe.idp.Document` -instantie. Sla de afbeelding op door de `com.adobe.idp.Document` object `copyToFile` methode en een `java.io.File` object.

**Zie ook**

[Snel starten (SOAP modus): een PDF-document converteren naar JPEG-bestanden met de Java API](/help/forms/developing/convert-pdf-service-java-api.md#quick-start-soap-mode-converting-a-pdf-document-to-jpeg-files-using-the-java-api)

### Een PDF-document converteren naar afbeeldingsbestanden met de webservice-API {#convert-a-pdf-document-to-image-files-using-the-web-service-api}

Een PDF-document converteren naar een afbeeldingsindeling met de Convert PDF Service API (webservice):

1. Inclusief projectbestanden.

   Creeer een Microsoft .NET project dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/ConvertPDFService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` met het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een PDF-client voor converteren.

   * Een `ConvertPdfServiceClient` object met de standaardconstructor.
   * Een `ConvertPdfServiceClient.Endpoint.Address` object door het `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/ConvertPDFService?blob=mtom`.) U hoeft de `lc_version` kenmerk. Geef echter `?blob=mtom`.
   * Een `System.ServiceModel.BasicHttpBinding` object door de waarde van het object op te halen `ConvertPdfServiceClient.Endpoint.Binding` veld. De geretourneerde waarde omzetten in `BasicHttpBinding`.
   * Stel de `System.ServiceModel.BasicHttpBinding` object `MessageEncoding` veld naar `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld toe `ConvertPdfServiceClient.ClientCredentials.UserName.UserName`.
      * De bijbehorende wachtwoordwaarde aan het veld toewijzen `ConvertPdfServiceClient.ClientCredentials.UserName.Password`.
      * De constante waarde toewijzen `HttpClientCredentialType.Basic` naar het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * De constante waarde toewijzen `BasicHttpSecurityMode.TransportCredentialOnly` naar het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Haal het PDF-document op dat u wilt converteren.

   * Een `BLOB` object met behulp van de constructor. Dit `BLOB` wordt gebruikt om het PDF-formulier op te slaan.
   * Een `System.IO.FileStream` object door de constructor ervan aan te roepen. Geef een tekenreekswaarde door die de locatie aangeeft van het PDF-formulier en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van de `System.IO.FileStream` object. Bepaal de grootte van de bytearray door de `System.IO.FileStream` object `Length` eigenschap.
   * De bytearray vullen met streamgegevens door de `System.IO.FileStream` object `Read` methode. Geef de bytearray, de startpositie en de streamlengte door om te lezen.
   * Vul de `BLOB` object door het toe te wijzen `MTOM` veld met de inhoud van de bytearray.

1. Stel runtime-opties in.

   * Een `ToImageOptionsSpec` object met behulp van de constructor.
   * Roep de vereiste methoden aan die bij dit object horen. Stel bijvoorbeeld het afbeeldingstype in door het `setImageConvertFormat` methode en een `ImageConvertFormat` opsommingswaarde die het opmaaktype aangeeft.

   >[!NOTE]
   >
   >De instelling van `ImageConvertFormat` opsommingswaarde is verplicht.

1. Zet de PDF om in een afbeelding.

   De `ConvertPDFServiceService` object `toImage2` en geeft de volgende waarden door:

   * A `BLOB` object dat staat voor het bestand dat moet worden omgezet
   * A `ToImageOptionsSpec` object dat de verschillende voorkeuren voor de indeling van de doelafbeelding bevat

   De `toImage2` methode retourneert een `MyArrayOfBLOB` -object dat de nieuwe afbeeldingsbestanden bevat.

1. Haal de afbeeldingsbestanden op uit een verzameling.

   * Het aantal elementen in het dialoogvenster `MyArrayOfBLOB` object door de waarde van het object op te halen `Count` veld. Elk element is een `BLOB` -object dat de afbeelding bevat.
   * Doorlopen `MyArrayOfBLOB` objecten maken en elk afbeeldingsbestand opslaan.

**Zie ook**

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)
