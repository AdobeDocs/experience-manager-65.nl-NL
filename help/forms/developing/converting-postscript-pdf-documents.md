---
title: Postscript converteren naar PDF-documenten
description: Met de Distiller-service kunt u PostScript®-, Encapsulated PostScript- (EPS) en PRN-bestanden converteren naar compacte, betrouwbare en veiligere PDF-bestanden via een netwerk. De Distiller-service converteert grote hoeveelheden gedrukte documenten naar elektronische documenten, zoals facturen en instructies met de Java API en Web Service API.
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
exl-id: 744df8b2-0c61-410f-89e9-20b8adddbf45
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Document Services,APIs & Integrations
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '1315'
ht-degree: 0%

---

# Postscript converteren naar PDF-documenten {#converting-postscript-to-pdf-documents}

**de Steekproeven en de voorbeelden in dit document zijn slechts voor AEM Forms op milieu JEE.**

## Informatie over de Distiller Service {#about-the-distiller-service}

De Distiller® service zet PostScript®-, Encapsulated PostScript (EPS)- en PRN-bestanden om in compacte, betrouwbare en veiligere PDF-bestanden via een netwerk. De Distiller-service wordt vaak gebruikt om grote hoeveelheden gedrukte documenten om te zetten in elektronische documenten, zoals facturen en verklaringen. Door documenten om te zetten in PDF, kunnen bedrijven hun klanten ook een papieren versie en een elektronische versie van een document sturen.

>[!NOTE]
>
>Voor meer informatie over de dienst van Distiller, zie [ Verwijzing van de Diensten voor AEM Forms ](https://www.adobe.com/go/learn_aemforms_services_63).

## PostScript converteren naar PDF-documenten {#converting-postscript-to-pdf-documents-inner}

In dit onderwerp wordt beschreven hoe u de Distiller Service API (Java en webservice) kunt gebruiken om PostScript (PS), Encapsulated PostScript (EPS) en PRN-bestanden programmatisch om te zetten in PDF-documenten.

>[!NOTE]
>
>Voor meer informatie over de dienst van Distiller, zie [ Verwijzing van de Diensten voor AEM Forms ](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Als u PostScript-bestanden wilt converteren naar PDF-documenten, moet u een van de volgende programma&#39;s installeren op de server die als host fungeert voor AEM Forms: Acrobat 9 of Microsoft Visual C++ 2005 redistributable package.

### Overzicht van de stappen {#summary-of-steps}

Voer de volgende stappen uit als u een van de ondersteunde typen wilt converteren naar een PDF-document:

1. Inclusief projectbestanden.
1. Maak een Distiller-serviceclient.
1. Haal het bestand op dat u wilt converteren.
1. Roep de bewerking PDF maken aan.
1. Sla het PDF-document op.

**omvat projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u de proxybestanden opnemen.

**creeer een de dienstcliënt van Distiller**

Voordat u een Distiller-servicebewerking programmatisch kunt uitvoeren, moet u een Distiller-serviceclient maken. Maak een `DistillerServiceClient` -object als u de Java API gebruikt. Maak een `DistillerServiceService` -object als u de webservice-API gebruikt.

**wint het dossier terug om** om te zetten

Haal het bestand op dat u wilt converteren. Als u bijvoorbeeld een PS-bestand wilt converteren naar een PDF-document, moet u het PS-bestand ophalen.

**Roep de PDF creatieverrichting** aan

Nadat u de de dienstcliënt creeert, kunt u de PDF creatieverrichting dan aanhalen. Voor deze bewerking is informatie nodig over het document dat moet worden geconverteerd, inclusief het pad naar het doeldocument.

**sparen het document van de PDF**

U kunt het PDF-document opslaan als een PDF-bestand.

**zie ook**

[Een PostScript-bestand converteren naar PDF met de Java API](converting-postscript-pdf-documents.md#convert-a-postscript-file-to-pdf-using-the-java-api)

[PostScript-bestanden converteren naar PDF met de API voor webservices](converting-postscript-pdf-documents.md#converting-a-postscript-file-to-pdf-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Uitvoerservice-API - Snel starten](/help/forms/developing/output-service-java-api-quick.md#output-service-java-api-quick-start-soap)

### Een PostScript-bestand converteren naar PDF met de Java API {#convert-a-postscript-file-to-pdf-using-the-java-api}

Converteer een PostScript-bestand naar een PDF-document met de Distiller Service API (Java):

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-distiller-client.jar, op in het klassenpad van uw Java-project.

1. Maak een Distiller-serviceclient.

   * Maak een `ServiceClientFactory` -object dat verbindingseigenschappen bevat.
   * Maak een `DistillerServiceClient` -object door de constructor ervan te gebruiken en het `ServiceClientFactory` -object door te geven.

1. Haal het bestand op dat u wilt converteren.

   * Maak een `java.io.FileInputStream` -object dat het te converteren bestand vertegenwoordigt met behulp van de constructor en geef een tekenreekswaarde door die de locatie van het bestand aangeeft.
   * Maak een `com.adobe.idp.Document` -object door de constructor ervan te gebruiken en het `java.io.FileInputStream` -object door te geven.

1. Roep de bewerking PDF maken aan.

   Roep de methode `createPDF` van het object `DistillerServiceClient` aan en geef de volgende waarden door:

   * Het `com.adobe.idp.Document` -object dat het om te zetten PS-, EPS- of PRN-bestand vertegenwoordigt
   * Een `java.lang.String` -object dat de naam bevat van het bestand dat moet worden omgezet
   * Een `java.lang.String` -object dat de naam bevat van de Adobe PDF-instellingen die moeten worden gebruikt
   * Een `java.lang.String` -object dat de naam bevat van de beveiligingsinstellingen die moeten worden gebruikt
   * Een optioneel `com.adobe.idp.Document` -object dat de instellingen bevat die moeten worden toegepast tijdens het genereren van het PDF-document
   * Een optioneel `com.adobe.idp.Document` -object dat metagegevens bevat die moeten worden toegepast op het PDF-document

   De methode `createPDF` retourneert een `CreatePDFResult` -object dat het nieuwe PDF-document bevat en een logbestand dat kan worden gegenereerd. Het logbestand bevat doorgaans fout- of waarschuwingsberichten die worden gegenereerd door de conversieaanvraag.

1. Sla het PDF-document op.

   Voer de volgende handelingen uit om het nieuwe PDF-document te verkrijgen:

   * Roep de methode `getCreatedDocument` van het object `CreatePDFResult` aan. Hiermee wordt een `com.adobe.idp.Document` -object geretourneerd.
   * Roep de methode `copyToFile` van het `com.adobe.idp.Document` -object aan om het PDF-document te extraheren.

   Op dezelfde manier om het logboekdocument te verkrijgen, voer de volgende acties uit.

   * Roep de methode `getLogDocument` van het object `CreatePDFResult` aan. Hiermee wordt een `com.adobe.idp.Document` -object geretourneerd.
   * Roep de methode `copyToFile` van het `com.adobe.idp.Document` -object aan om het logdocument te extraheren.

**zie ook**

[Overzicht van de stappen](converting-postscript-pdf-documents.md#summary-of-steps)

[Snel starten (SOAP modus): een PostScript-bestand converteren naar een PDF-document met de Java API](/help/forms/developing/distiller-service-java-api-quick.md#quick-start-soap-mode-converting-a-postscript-file-to-a-pdf-document-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### PostScript-bestanden converteren naar PDF met de API voor webservices {#converting-a-postscript-file-to-pdf-using-the-web-service-api}

Converteer een PostScript-bestand naar een PDF-document met de Distiller Service API (webservice):

1. Inclusief projectbestanden.

   Creeer een Microsoft .NET project dat MTOM gebruikt. Gebruik de volgende WSDL-definitie: `http://localhost:8080/soap/services/DistillerService?WSDL&lc_version=9.0.1` .

   >[!NOTE]
   >
   >Vervang `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een Distiller-serviceclient.

   * Maak een `DistillerServiceClient` -object met de standaardconstructor.
   * Maak een `DistillerServiceClient.Endpoint.Address` -object met de `System.ServiceModel.EndpointAddress` -constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/DistillerService?blob=mtom` .) U hoeft het attribuut `lc_version` niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt. Geef echter `?blob=mtom` op om MTOM te gebruiken.
   * Maak een `System.ServiceModel.BasicHttpBinding` -object door de waarde van het `DistillerServiceClient.Endpoint.Binding` -veld op te halen. De geretourneerde waarde wordt gecast naar `BasicHttpBinding` .
   * Stel het veld `MessageEncoding` van het `System.ServiceModel.BasicHttpBinding` -object in op `WSMessageEncoding.Mtom` . Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld `DistillerServiceClient.ClientCredentials.UserName.UserName` toe.
      * Wijs de bijbehorende wachtwoordwaarde toe aan het veld `DistillerServiceClient.ClientCredentials.UserName.Password` .
      * Wijs de constante waarde `HttpClientCredentialType.Basic` toe aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType` .
      * Wijs de constante waarde `BasicHttpSecurityMode.TransportCredentialOnly` toe aan het veld `BasicHttpBindingSecurity.Security.Mode` .

1. Haal het bestand op dat u wilt converteren.

   * Maak een `BLOB` -object met behulp van de constructor. Met dit `BLOB` -object wordt het bestand opgeslagen dat naar een PDF-document moet worden geconverteerd.
   * Maak een `System.IO.FileStream` -object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie en de modus vertegenwoordigt waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van het object `System.IO.FileStream` wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de eigenschap `Length` van het object `System.IO.FileStream` op te halen.
   * Vul de bytearray met streamgegevens door de methode `Read` van het object `System.IO.FileStream` aan te roepen en de bytearray, de startpositie en de lengte van de stream door te geven om te lezen.
   * Vul het object `BLOB` door de eigenschap `MTOM` ervan toe te wijzen met de inhoud van de bytearray.

1. Roep de bewerking PDF maken aan.

   Roep de methode `CreatePDF2` van het object `DistillerServiceService` aan en geef de volgende vereiste waarden door:

   * Het `BLOB` -object dat het PS-bestand vertegenwoordigt dat moet worden omgezet
   * Een tekenreeks die de padnaam bevat van het bestand dat moet worden omgezet
   * Een tekenreeksobject dat de Adobe PDF-instellingen bevat die moeten worden gebruikt (bijvoorbeeld `Standard`)
   * Een koordvoorwerp dat de te gebruiken veiligheidsmontages bevat (bijvoorbeeld, `No Securit` y)
   * Een optioneel `BLOB` -object dat de instellingen bevat die moeten worden toegepast tijdens het genereren van het PDF-document
   * Een optioneel `BLOB` -object dat metagegevens bevat die moeten worden toegepast op het PDF-document
   * Een uitvoerparameter `BLOB` die wordt gebruikt om het PDF-document op te slaan
   * Een `BLOB` uitvoerparameter die wordt gebruikt om het logboek op te slaan

1. Sla het PDF-document op.

   * Maak een `System.IO.FileStream` -object door de constructor ervan aan te roepen. Geef een tekenreekswaarde door die staat voor de bestandslocatie van het ondertekende PDF-document en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud wordt opgeslagen van het object `BLOB` dat door de methode `CreatePDF2` (de uitvoerparameter) is geretourneerd. Vul de bytearray met de waarde van het gegevenslid `MTOM` van het object `BLOB` .
   * Maak een `System.IO.BinaryWriter` -object door de constructor ervan aan te roepen en het `System.IO.FileStream` -object door te geven.
   * Schrijf de inhoud van de bytearray naar een PDF-bestand door de methode `Write` van het object `System.IO.BinaryWriter` aan te roepen en de bytearray door te geven.

**zie ook**

[Overzicht van de stappen](converting-postscript-pdf-documents.md#summary-of-steps)

<!-- UNRESOLVED LINKS
[Quick Start (MTOM): Converting a PostScript file to a PDF document using the web service API](unresolvedlink-lc-qs-distiller-di.xml#ws624e3cba99b79e12e69a9941333732bac8-7f01.2)

[Quick Start (SwaRef): Converting a PostScript file to a PDF document using the web service API](unresolvedlink-lc-qs-distiller-di.xml#ws624e3cba99b79e12e69a9941333732bac8-7eff.2)
-->

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)
