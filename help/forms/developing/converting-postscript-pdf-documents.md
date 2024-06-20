---
title: Postscript converteren naar PDF-documenten
description: Gebruik de Distiller-service om PostScript®-, Encapsulated PostScript- (EPS) en PRN-bestanden om te zetten in compacte, betrouwbare en veiligere PDF-bestanden via een netwerk. De Distiller-service converteert grote hoeveelheden gedrukte documenten naar elektronische documenten, zoals facturen en instructies met de Java API en Web Service API.
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
exl-id: 744df8b2-0c61-410f-89e9-20b8adddbf45
solution: Experience Manager, Experience Manager Forms
source-git-commit: 872e2de411f51b5f0b26a2ff47cb49f01313d39f
workflow-type: tm+mt
source-wordcount: '1315'
ht-degree: 0%

---

# Postscript converteren naar PDF-documenten {#converting-postscript-to-pdf-documents}

**Voorbeelden en voorbeelden in dit document gelden alleen voor AEM Forms in JEE-omgeving.**

## Informatie over de Distiller Service {#about-the-distiller-service}

De Distiller® service zet PostScript®-, Encapsulated PostScript- (EPS) en PRN-bestanden om in compacte, betrouwbare en veiligere PDF-bestanden via een netwerk. De Distiller-service wordt vaak gebruikt om grote hoeveelheden gedrukte documenten om te zetten in elektronische documenten, zoals facturen en verklaringen. Door documenten om te zetten in PDF, kunnen bedrijven hun klanten ook een papieren versie en een elektronische versie van een document sturen.

>[!NOTE]
>
>Voor meer informatie over de Distiller-service raadpleegt u [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## PostScript converteren naar PDF-documenten {#converting-postscript-to-pdf-documents-inner}

In dit onderwerp wordt beschreven hoe u de Distiller Service API (Java en webservice) kunt gebruiken om PostScript (PS), Encapsulated PostScript (EPS) en PRN-bestanden programmatisch om te zetten in PDF-documenten.

>[!NOTE]
>
>Voor meer informatie over de Distiller-service raadpleegt u [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Als u PostScript-bestanden wilt converteren naar PDF-documenten, moet u een van de volgende elementen installeren op de server die als host fungeert voor AEM Forms: Acrobat 9 of Microsoft Visual C++ 2005 redistributable-pakket.

### Overzicht van de stappen {#summary-of-steps}

Voer de volgende stappen uit als u een van de ondersteunde typen wilt converteren naar een PDF-document:

1. Inclusief projectbestanden.
1. Maak een Distiller-serviceclient.
1. Haal het bestand op dat u wilt converteren.
1. Roep de bewerking PDF maken aan.
1. Sla het PDF-document op.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u de proxybestanden opnemen.

**Een Distiller-serviceclient maken**

Voordat u een Distiller-servicebewerking programmatisch kunt uitvoeren, moet u een Distiller-serviceclient maken. Als u de Java API gebruikt, maakt u een `DistillerServiceClient` object. Als u de webservice-API gebruikt, maakt u een `DistillerServiceService` object.

**Het te converteren bestand ophalen**

Haal het bestand op dat u wilt converteren. Als u bijvoorbeeld een PS-bestand wilt converteren naar een PDF-document, moet u het PS-bestand ophalen.

**De bewerking PDF maken aanroepen**

Nadat u de de dienstcliënt creeert, kunt u de PDF creatieverrichting dan aanhalen. Voor deze bewerking is informatie nodig over het document dat moet worden geconverteerd, inclusief het pad naar het doeldocument.

**Het PDF-document opslaan**

U kunt het PDF-document opslaan als een PDF-bestand.

**Zie ook**

[Een PostScript-bestand converteren naar PDF met de Java API](converting-postscript-pdf-documents.md#convert-a-postscript-file-to-pdf-using-the-java-api)

[Een PostScript-bestand converteren naar PDF met de webservice-API](converting-postscript-pdf-documents.md#converting-a-postscript-file-to-pdf-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Uitvoerservice-API - Snel starten](/help/forms/developing/output-service-java-api-quick.md#output-service-java-api-quick-start-soap)

### Een PostScript-bestand converteren naar PDF met de Java API {#convert-a-postscript-file-to-pdf-using-the-java-api}

Een PostScript-bestand converteren naar een PDF-document met de Distiller Service API (Java):

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-distiller-client.jar, op in het klassenpad van uw Java-project.

1. Maak een Distiller-serviceclient.

   * Een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Een `DistillerServiceClient` object door de constructor ervan te gebruiken en de `ServiceClientFactory` object.

1. Haal het bestand op dat u wilt converteren.

   * Een `java.io.FileInputStream` object dat het bestand vertegenwoordigt dat moet worden omgezet met de constructor ervan en dat een tekenreekswaarde doorgeeft die de locatie van het bestand aangeeft.
   * Een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en de `java.io.FileInputStream` object.

1. Roep de bewerking PDF maken aan.

   De `DistillerServiceClient` object `createPDF` en geeft de volgende waarden door:

   * De `com.adobe.idp.Document` object dat staat voor het te converteren PS-, EPS- of PRN-bestand
   * A `java.lang.String` object dat de naam bevat van het bestand dat moet worden omgezet
   * A `java.lang.String` object dat de naam bevat van de Adobe PDF-instellingen die moeten worden gebruikt
   * A `java.lang.String` object dat de naam bevat van de te gebruiken beveiligingsinstellingen
   * Een optioneel `com.adobe.idp.Document` object dat instellingen bevat die moeten worden toegepast tijdens het genereren van het PDF-document
   * Een optioneel `com.adobe.idp.Document` object dat metagegevens bevat die moeten worden toegepast op het PDF-document

   De `createPDF` methode retourneert een `CreatePDFResult` -object dat het nieuwe PDF-document en een logbestand bevat dat kan worden gegenereerd. Het logbestand bevat doorgaans fout- of waarschuwingsberichten die worden gegenereerd door de conversieaanvraag.

1. Sla het PDF-document op.

   Voer de volgende handelingen uit om het nieuwe PDF-document te verkrijgen:

   * De `CreatePDFResult` object `getCreatedDocument` methode. Dit retourneert een `com.adobe.idp.Document` object.
   * De `com.adobe.idp.Document` object `copyToFile` methode om het PDF-document te extraheren.

   Op dezelfde manier om het logboekdocument te verkrijgen, voer de volgende acties uit.

   * De `CreatePDFResult` object `getLogDocument` methode. Dit retourneert een `com.adobe.idp.Document` object.
   * De `com.adobe.idp.Document` object `copyToFile` methode om het logdocument te extraheren.

**Zie ook**

[Overzicht van de stappen](converting-postscript-pdf-documents.md#summary-of-steps)

[Snel starten (SOAP modus): een PostScript-bestand converteren naar een PDF-document met de Java API](/help/forms/developing/distiller-service-java-api-quick.md#quick-start-soap-mode-converting-a-postscript-file-to-a-pdf-document-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Een PostScript-bestand converteren naar PDF met de webservice-API {#converting-a-postscript-file-to-pdf-using-the-web-service-api}

Een PostScript-bestand converteren naar een PDF-document met de Distiller Service API (webservice):

1. Inclusief projectbestanden.

   Creeer een Microsoft .NET project dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/DistillerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` met het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een Distiller-serviceclient.

   * Een `DistillerServiceClient` object met de standaardconstructor.
   * Een `DistillerServiceClient.Endpoint.Address` object door het `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/DistillerService?blob=mtom`.) U hoeft de `lc_version` kenmerk. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt. Geef echter `?blob=mtom` MTOM gebruiken.
   * Een `System.ServiceModel.BasicHttpBinding` object door de waarde van het object op te halen `DistillerServiceClient.Endpoint.Binding` veld. De geretourneerde waarde omzetten in `BasicHttpBinding`.
   * Stel de `System.ServiceModel.BasicHttpBinding` object `MessageEncoding` veld naar `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld toe `DistillerServiceClient.ClientCredentials.UserName.UserName`.
      * De bijbehorende wachtwoordwaarde aan het veld toewijzen `DistillerServiceClient.ClientCredentials.UserName.Password`.
      * De constante waarde toewijzen `HttpClientCredentialType.Basic` naar het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * De constante waarde toewijzen `BasicHttpSecurityMode.TransportCredentialOnly` naar het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Haal het bestand op dat u wilt converteren.

   * Een `BLOB` object met behulp van de constructor. Dit `BLOB` wordt gebruikt om het bestand op te slaan dat naar een PDF-document moet worden geconverteerd.
   * Een `System.IO.FileStream` -object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie en de modus vertegenwoordigt waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van de `System.IO.FileStream` object. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` object `Length` eigenschap.
   * De bytearray vullen met streamgegevens door de `System.IO.FileStream` object `Read` en geeft u de bytearray, de startpositie en de streamlengte door die u wilt lezen.
   * Vul de `BLOB` object door het toe te wijzen `MTOM` eigenschap met de inhoud van de bytearray.

1. Roep de bewerking PDF maken aan.

   De `DistillerServiceService` object `CreatePDF2` en geeft de volgende vereiste waarden door:

   * De `BLOB` object dat staat voor het PS-bestand dat moet worden omgezet
   * Een tekenreeks die de padnaam bevat van het bestand dat moet worden omgezet
   * Een tekenreeksobject dat de Adobe PDF-instellingen bevat die moeten worden gebruikt (bijvoorbeeld `Standard`)
   * Een tekenreeksobject dat de te gebruiken beveiligingsinstellingen bevat (bijvoorbeeld `No Securit`y)
   * Een optioneel `BLOB` object dat instellingen bevat die moeten worden toegepast tijdens het genereren van het PDF-document
   * Een optioneel `BLOB` object dat metagegevens bevat die moeten worden toegepast op het PDF-document
   * A `BLOB` uitvoerparameter die wordt gebruikt om het PDF-document op te slaan
   * A `BLOB` uitvoerparameter die wordt gebruikt om het logboek op te slaan

1. Sla het PDF-document op.

   * Een `System.IO.FileStream` object door de constructor ervan aan te roepen. Geef een tekenreekswaarde door die staat voor de bestandslocatie van het ondertekende PDF-document en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van de `BLOB` object dat is geretourneerd door de `CreatePDF2` methode (de uitvoerparameter). Vul de bytearray met de waarde van de `BLOB` object `MTOM` lid.
   * Een `System.IO.BinaryWriter` object door de constructor aan te roepen en de `System.IO.FileStream` object.
   * Schrijf de inhoud van de bytearray naar een PDF-bestand door het `System.IO.BinaryWriter` object `Write` en geeft u de bytearray door.

**Zie ook**

[Overzicht van de stappen](converting-postscript-pdf-documents.md#summary-of-steps)

<!-- UNRESOLVED LINKS
[Quick Start (MTOM): Converting a PostScript file to a PDF document using the web service API](unresolvedlink-lc-qs-distiller-di.xml#ws624e3cba99b79e12e69a9941333732bac8-7f01.2)

[Quick Start (SwaRef): Converting a PostScript file to a PDF document using the web service API](unresolvedlink-lc-qs-distiller-di.xml#ws624e3cba99b79e12e69a9941333732bac8-7eff.2)
-->

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)
