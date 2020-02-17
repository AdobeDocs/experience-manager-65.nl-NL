---
title: Postscript converteren naar PDF-documenten
seo-title: Postscript converteren naar PDF-documenten
description: 'null'
seo-description: 'null'
uuid: 2143f406-1fdd-4551-a738-1a8388f8d478
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 06ad343a-f74d-41f5-b3c8-b85bb723ceeb
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Postscript converteren naar PDF-documenten {#converting-postscript-to-pdf-documents}

## De Distiller-service {#about-the-distiller-service}

De service Distiller® converteert PostScript®-, Encapsulated PostScript- (EPS) en PRN-bestanden naar compacte, betrouwbare en veiligere PDF-bestanden via een netwerk. De Distiller-service wordt vaak gebruikt om grote hoeveelheden gedrukte documenten om te zetten in elektronische documenten, zoals facturen en instructies. Door documenten naar PDF te converteren, kunnen bedrijven hun klanten ook een papieren versie en een elektronische versie van een document sturen.

>[!NOTE]
>
>Zie [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63)voor meer informatie over de Distiller-service.

## PostScript converteren naar PDF-documenten {#converting-postscript-to-pdf-documents-inner}

In dit onderwerp wordt beschreven hoe u de API (Java en webservice) van Distiller Service kunt gebruiken om PostScript (PS)-, Encapsulated PostScript- (EPS) en PRN-bestanden programmatisch om te zetten in PDF-documenten.

>[!NOTE]
>
>Zie [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63)voor meer informatie over de Distiller-service.

>[!NOTE]
>
>Als u PostScript-bestanden naar PDF-documenten wilt converteren, moet een van de volgende items zijn geïnstalleerd op de server die als host fungeert voor AEM-formulieren: Acrobat 9 of Microsoft Visual C++ 2005 herdistribueerbaar pakket.

### Overzicht van de stappen {#summary-of-steps}

Voer de volgende stappen uit als u een van de ondersteunde typen wilt converteren naar een PDF-document:

1. Inclusief projectbestanden.
1. Maak een Distiller-serviceclient.
1. Haal het te converteren bestand op.
1. De PDF-ontwerpbewerking aanroepen.
1. Sla het PDF-document op.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u de proxybestanden opnemen.

**Een Distiller-serviceclient maken**

Voordat u via programmacode een Distiller-servicebewerking kunt uitvoeren, moet u een Distiller-serviceclient maken. Als u de Java API gebruikt, maakt u een `DistillerServiceClient` object. Als u de webservice-API gebruikt, maakt u een `DistillerServiceService` object.

**Het te converteren bestand ophalen**

U moet het bestand ophalen dat u wilt converteren. Als u bijvoorbeeld een PS-bestand naar een PDF-document wilt converteren, moet u het PS-bestand ophalen.

**De PDF-ontwerpbewerking aanroepen**

Nadat u de serviceclient hebt gemaakt, kunt u het maken van de PDF vervolgens activeren. Voor deze bewerking is informatie nodig over het document dat moet worden geconverteerd, inclusief het pad naar het doeldocument.

**Het PDF-document opslaan**

U kunt het PDF-document opslaan als een PDF-bestand.

**Zie ook**

[Een PostScript-bestand converteren naar PDF met de Java API](converting-postscript-pdf-documents.md#convert-a-postscript-file-to-pdf-using-the-java-api)

[Een PostScript-bestand converteren naar PDF met de webservice-API](converting-postscript-pdf-documents.md#converting-a-postscript-file-to-pdf-using-the-web-service-api)

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Uitvoerservice-API - Snel starten](/help/forms/developing/output-service-java-api-quick.md#output-service-java-api-quick-start-soap)

### Een PostScript-bestand converteren naar PDF met de Java API {#convert-a-postscript-file-to-pdf-using-the-java-api}

Een PostScript-bestand converteren naar PDF-document met de Distiller Service API (Java):

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-distiller-client.jar, op in het klassenpad van uw Java-project.

1. Maak een Distiller-serviceclient.

   * Maak een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Maak een `DistillerServiceClient` object door de constructor ervan te gebruiken en het `ServiceClientFactory` object door te geven.

1. Haal het te converteren bestand op.

   * Maak een `java.io.FileInputStream` object dat het te converteren bestand vertegenwoordigt met de constructor ervan en geef een tekenreekswaarde door die de locatie van het bestand aangeeft.
   * Maak een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en het `java.io.FileInputStream` object door te geven.

1. De PDF-ontwerpbewerking aanroepen.

   Roep de methode van het `DistillerServiceClient` `createPDF` object aan en geef de volgende waarden door:

   * Het `com.adobe.idp.Document` object dat het om te zetten PS-, EPS- of PRN-bestand vertegenwoordigt
   * Een `java.lang.String` object dat de naam bevat van het bestand dat moet worden omgezet
   * Een `java.lang.String` object met de naam van de te gebruiken Adobe PDF-instellingen
   * Een `java.lang.String` object dat de naam bevat van de beveiligingsinstellingen die moeten worden gebruikt
   * Een optioneel `com.adobe.idp.Document` object dat de instellingen bevat die moeten worden toegepast tijdens het genereren van het PDF-document
   * Een optioneel `com.adobe.idp.Document` object dat metagegevens bevat die op het PDF-document moeten worden toegepast
   De `createPDF` methode retourneert een `CreatePDFResult` object dat het nieuwe PDF-document bevat en een logbestand dat kan worden gegenereerd. Het logbestand bevat doorgaans fout- of waarschuwingsberichten die worden gegenereerd door de conversieaanvraag.

1. Sla het PDF-document op.

   Voer de volgende handelingen uit om het nieuwe PDF-document te verkrijgen:

   * Roep de `CreatePDFResult` methode van het `getCreatedDocument` object aan. Hiermee wordt een `com.adobe.idp.Document` object geretourneerd.
   * Roep de `com.adobe.idp.Document` methode van het `copyToFile` object aan om het PDF-document uit te pakken.
   Op dezelfde manier om het logboekdocument te verkrijgen, voer de volgende acties uit.

   * Roep de `CreatePDFResult` methode van het `getLogDocument` object aan. Hiermee wordt een `com.adobe.idp.Document` object geretourneerd.
   * Roep de `com.adobe.idp.Document` methode van het `copyToFile` object aan om het logdocument te extraheren.


**Zie ook**

[Overzicht van de stappen](converting-postscript-pdf-documents.md#summary-of-steps)

[Snel starten (SOAP-modus): Een PostScript-bestand converteren naar een PDF-document met de Java API](/help/forms/developing/distiller-service-java-api-quick.md#quick-start-soap-mode-converting-a-postscript-file-to-a-pdf-document-using-the-java-api)

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Een PostScript-bestand converteren naar PDF met de webservice-API {#converting-a-postscript-file-to-pdf-using-the-web-service-api}

Een PostScript-bestand converteren naar PDF-document met de Distiller Service API (webservice):

1. Inclusief projectbestanden.

   Creeer een project van Microsoft .NET dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/DistillerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een Distiller-serviceclient.

   * Maak een `DistillerServiceClient` object met de standaardconstructor.
   * Maak een `DistillerServiceClient.Endpoint.Address` object met de `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/DistillerService?blob=mtom`.) U hoeft het `lc_version` kenmerk niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt. Geef echter op `?blob=mtom` om MTOM te gebruiken.
   * Maak een `System.ServiceModel.BasicHttpBinding` object door de waarde van het `DistillerServiceClient.Endpoint.Binding` veld op te halen. Kiezen naar de geretourneerde waarde `BasicHttpBinding`.
   * Stel het `System.ServiceModel.BasicHttpBinding` veld van het `MessageEncoding` object in op `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam voor AEM-formulieren toe aan het veld `DistillerServiceClient.ClientCredentials.UserName.UserName`.
      * Wijs de bijbehorende wachtwoordwaarde aan het veld toe `DistillerServiceClient.ClientCredentials.UserName.Password`.
      * Wijs de constante waarde toe `HttpClientCredentialType.Basic` aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Wijs de constante waarde toe `BasicHttpSecurityMode.TransportCredentialOnly` aan het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Haal het te converteren bestand op.

   * Maak een `BLOB` object met de constructor ervan. Met dit `BLOB` object wordt het bestand opgeslagen dat naar een PDF-document moet worden geconverteerd.
   * Maak een `System.IO.FileStream` object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die staat voor de bestandslocatie en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van het `System.IO.FileStream` object wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` eigenschap van het `Length` object op te halen.
   * Vul de bytearray met streamgegevens door de methode van het `System.IO.FileStream` `Read` object aan te roepen en de bytearray, de startpositie en de lengte van de stream door te geven om te lezen.
   * Vul het `BLOB` object door de `MTOM` eigenschap ervan toe te wijzen met de inhoud van de bytearray.

1. De PDF-ontwerpbewerking aanroepen.

   Roep de `DistillerServiceService` methode van het `CreatePDF2` object aan en geef de volgende vereiste waarden door:

   * Het `BLOB` object dat staat voor het PS-bestand dat moet worden omgezet
   * Een tekenreeks die de padnaam bevat van het bestand dat moet worden omgezet
   * Een tekenreeksobject dat de Adobe PDF-instellingen bevat die moeten worden gebruikt (bijvoorbeeld `Standard`)
   * Een tekenreeksobject dat de beveiligingsinstellingen bevat die moeten worden gebruikt (bijvoorbeeld `No Securit`y)
   * Een optioneel `BLOB` object dat de instellingen bevat die moeten worden toegepast tijdens het genereren van het PDF-document
   * Een optioneel `BLOB` object dat metagegevens bevat die op het PDF-document moeten worden toegepast
   * Een `BLOB` uitvoerparameter die wordt gebruikt om het PDF-document op te slaan
   * Een `BLOB` outputparameter die wordt gebruikt om het logboek op te slaan

1. Sla het PDF-document op.

   * Maak een `System.IO.FileStream` object door de constructor ervan aan te roepen. Geef een tekenreekswaarde door die staat voor de bestandslocatie van het ondertekende PDF-document en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud wordt opgeslagen van het `BLOB` object dat door de `CreatePDF2` methode (de uitvoerparameter) is geretourneerd. Vul de bytearray met de waarde van het `BLOB` `MTOM` gegevenslid van het object.
   * Maak een `System.IO.BinaryWriter` object door de constructor ervan aan te roepen en het `System.IO.FileStream` object door te geven.
   * Schrijf de inhoud van de bytearray naar een PDF-bestand door de methode van het `System.IO.BinaryWriter` `Write` object aan te roepen en de bytearray door te geven.

**Zie ook**

[Overzicht van de stappen](converting-postscript-pdf-documents.md#summary-of-steps)

<!-- UNRESOLVED LINKS
[Quick Start (MTOM): Converting a PostScript file to a PDF document using the web service API](unresolvedlink-lc-qs-distiller-di.xml#ws624e3cba99b79e12e69a9941333732bac8-7f01.2)

[Quick Start (SwaRef): Converting a PostScript file to a PDF document using the web service API](unresolvedlink-lc-qs-distiller-di.xml#ws624e3cba99b79e12e69a9941333732bac8-7eff.2)
-->

[AEM-formulieren aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM-formulieren aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)
