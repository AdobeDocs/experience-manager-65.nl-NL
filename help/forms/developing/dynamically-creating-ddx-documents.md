---
title: DDX-documenten dynamisch maken
description: Maak dynamisch een DDX-document met behulp van de Java API en Web Service API. Door een DDX-document dynamisch te maken, kunt u waarden in het DDX-document gebruiken die tijdens runtime worden verkregen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
exl-id: b3c19c82-e26f-4dc8-b846-6aec705cee08
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Document Services,APIs & Integrations
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '2153'
ht-degree: 0%

---

# DDX-documenten dynamisch maken {#dynamically-creating-ddx-documents}

**de Steekproeven en de voorbeelden in dit document zijn slechts voor AEM Forms op milieu JEE.**

U kunt dynamisch een DDX-document maken dat kan worden gebruikt om een Assembler-bewerking uit te voeren. Door een DDX-document dynamisch te maken, kunt u waarden in het DDX-document gebruiken die tijdens runtime worden verkregen. Om een DX- document dynamisch tot stand te brengen, gebruik klassen die tot de programmeertaal behoren die u gebruikt. Bijvoorbeeld, als u uw cliënttoepassing gebruikend Java ontwikkelt, gebruiksklassen die tot het `org.w3c.dom.*` pakket behoren. Op dezelfde manier, als u Microsoft .NET gebruikt, gebruik klassen die tot `System.Xml` namespace behoren.

Voordat u het DDX-document kunt doorgeven aan de Assembler-service, moet u de XML van een `org.w3c.dom.Document` -instantie omzetten in een `com.adobe.idp.Document` -instantie. Als u webservices gebruikt, moet u de XML van het gegevenstype dat wordt gebruikt om de XML te maken (bijvoorbeeld `XmlDocument` ) omzetten naar een `BLOB` -instantie.

Voor deze bespreking, veronderstel dat het volgende Dx- document dynamisch wordt gecreeerd.

```xml
 <?xml version="1.0" encoding="UTF-8"?>
 <DDX xmlns="https://ns.adobe.com/DDX/1.0/">
      <PDFsFromBookmarks prefix="stmt">
     <PDF source="AssemblerResultPDF.pdf"/>
 </PDFsFromBookmarks>
 </DDX>
```

Dit DDX-document demonteert een PDF-document. U wordt aangeraden bekend te zijn met het demonteren van PDF-documenten.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Assembler, zie [ Verwijzing van de Diensten voor AEM Forms ](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Voor meer informatie over een document DDX, zie [ de Dienst van de Assembler en de Verwijzing DDX ](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Overzicht van de stappen {#summary-of-steps}

Als u een PDF-document wilt demonteren met een dynamisch gemaakt DDX-document, voert u de volgende taken uit:

1. Inclusief projectbestanden.
1. Maak een PDF Assembler-client.
1. Maak het DDX-document.
1. Zet het DDX-document om.
1. Stel runtime-opties in.
1. Haal het PDF-document uit elkaar.
1. Sla de gedemonteerde PDF-documenten op.

**omvat projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-assembler-client.jar
* adobe-utilities.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)

**creeer een cliënt van de Assembler van de PDF**

Alvorens u programmatically een verrichting van de Assembler kunt uitvoeren, creeer een de dienstcliënt van de Assembler.

**creeer het DDX- document**

Maak een DDX-document met de programmeertaal die u gebruikt. Als u een DDX-document wilt maken dat een PDF-document demonteert, controleert u of het `PDFsFromBookmarks` -element bevat. Zet het gegevenstype dat wordt gebruikt om het DDX-document te maken, om in een `com.adobe.idp.Document` -instantie als u de Java API gebruikt. Als u webservices gebruikt, zet u het gegevenstype om in een `BLOB` -instantie.

**zet het DDX- document** om

Een DDX-document dat is gemaakt met `org.w3c.dom` -klassen, moet worden omgezet in een `com.adobe.idp.Document` -object. Gebruik Java XML-transformatieklassen om deze taak uit te voeren wanneer u de Java API gebruikt. Als u webservices gebruikt, zet u het DDX-document om in een `BLOB` -object.

**Verwijzing een document van PDF om** te demonteren

Als u een PDF-document wilt demonteren, verwijst u naar een PDF-bestand dat het PDF-document vertegenwoordigt dat u wilt demonteren. Wanneer het tot de dienst van de Assembler wordt overgegaan, wordt een afzonderlijk document van PDF teruggegeven voor elke niveau 1 referentie in het document.

**vastgestelde runtime opties**

U kunt runtime opties plaatsen die het gedrag van de dienst van de Assembler controleren terwijl het een baan uitvoert. U kunt bijvoorbeeld een optie instellen die de Assembler-service de opdracht geeft door te gaan met het verwerken van een taak als er een fout optreedt. Gebruik een `AssemblerOptionSpec` -object om runtime-opties in te stellen.

**demonstreert het document van de PDF**

U kunt het PDF-document dempen door de bewerking `invokeDDX` aan te roepen. Geef het DDX-document door dat dynamisch is gemaakt. De dienst van de Assembler keert gedemonteerde documenten van PDF binnen een inzamelingsvoorwerp terug.

**sparen de gedemonteerde documenten van de PDF**

Alle gedemonteerde PDF-documenten worden geretourneerd in een verzamelingsobject. Doorloop het verzamelingsobject en sla elk PDF-document op als een PDF-bestand.

**zie ook**

[Een DDX-document dynamisch maken met de Java API](/help/forms/developing/dynamically-creating-ddx-documents.md#dynamically-create-a-ddx-document-using-the-java-api)

[Een DDX-document dynamisch maken met de webservice-API](/help/forms/developing/dynamically-creating-ddx-documents.md#dynamically-create-a-ddx-document-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[PDF-documenten programmatisch demonteren](/help/forms/developing/programmatically-disassembling-pdf-documents.md#programmatically-disassembling-pdf-documents)

## Een DDX-document dynamisch maken met de Java API {#dynamically-create-a-ddx-document-using-the-java-api}

Maak dynamisch een DDX-document en demonstreer een PDF-document met de API (Java) voor vergaderingsservice:

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-assembler-client.jar, op in het klassenpad van uw Java-project.

1. Maak een PDF Assembler-client.

   * Maak een `ServiceClientFactory` -object dat verbindingseigenschappen bevat.
   * Maak een `AssemblerServiceClient` -object door de constructor ervan te gebruiken en het `ServiceClientFactory` -object door te geven.

1. Maak het DDX-document.

   * Maak een Java `DocumentBuilderFactory` -object door de methode `DocumentBuilderFactory` class&#39; `newInstance` aan te roepen.
   * Maak een Java `DocumentBuilder` -object door de methode `DocumentBuilderFactory` object `newDocumentBuilder` aan te roepen.
   * Roep de methode `newDocument` van het `DocumentBuilder` -object aan om een `org.w3c.dom.Document` -object te instantiëren.
   * Maak het basiselement van het DDX-document door de methode `createElement` van het `org.w3c.dom.Document` -object aan te roepen. Deze methode maakt een `Element` -object dat het hoofdelement vertegenwoordigt. Geef een tekenreekswaarde die de naam van het element vertegenwoordigt, door aan de methode `createElement` . De geretourneerde waarde wordt gecast naar `Element` . Stel vervolgens een waarde voor het onderliggende element in door de methode `setAttribute` ervan aan te roepen. Voeg ten slotte het element aan het koptekstelement toe door de methode `appendChild` van het koptekstelement aan te roepen en geef het onderliggende-elementobject door als een argument. De volgende coderegels tonen deze toepassingslogica:

     ` Element root = (Element)document.createElement("DDX");  root.setAttribute("xmlns","https://ns.adobe.com/DDX/1.0/");  document.appendChild(root);`

   * Maak het `PDFsFromBookmarks` -element door de methode `Document` object `createElement` aan te roepen. Geef een tekenreekswaarde die de naam van het element vertegenwoordigt, door aan de methode `createElement` . De geretourneerde waarde wordt gecast naar `Element` . Stel een waarde voor het element `PDFsFromBookmarks` in door de methode `setAttribute` ervan aan te roepen. Voeg het element `PDFsFromBookmarks` toe aan het element `DDX` door de methode `appendChild` van het element DDX aan te roepen. Geef het `PDFsFromBookmarks` -elementobject door als argument. De volgende coderegels tonen deze toepassingslogica:

     ` Element PDFsFromBookmarks = (Element)document.createElement("PDFsFromBookmarks");  PDFsFromBookmarks.setAttribute("prefix","stmt");  root.appendChild(PDFsFromBookmarks);`

   * Maak een `PDF` -element door de methode `Document` object `createElement` aan te roepen. Geef een tekenreekswaarde door die de naam van het element vertegenwoordigt. De geretourneerde waarde wordt gecast naar `Element` . Stel een waarde voor het element `PDF` in door de methode `setAttribute` ervan aan te roepen. Voeg het element `PDF` toe aan het element `PDFsFromBookmarks` door de methode `PDFsFromBookmarks` van het element `appendChild` aan te roepen. Geef het `PDF` -elementobject door als argument. Deze toepassingslogica wordt in de volgende coderegels getoond:

     ` Element PDF = (Element)document.createElement("PDF");  PDF.setAttribute("source","AssemblerResultPDF.pdf");  PDFsFromBookmarks.appendChild(PDF);`

1. Zet het DDX-document om.

   * Maak een `javax.xml.transform.Transformer` -object door de statische methode `javax.xml.transform.Transformer` van het object `newInstance` aan te roepen.
   * Maak een `Transformer` -object door de methode `TransformerFactory` object `newTransformer` aan te roepen.
   * Maak een `ByteArrayOutputStream` -object met behulp van de constructor.
   * Maak een `javax.xml.transform.dom.DOMSource` -object met behulp van de constructor. Geef het `org.w3c.dom.Document` -object door dat het DDX-document vertegenwoordigt.
   * Maak een `javax.xml.transform.dom.DOMSource` -object door de constructor ervan te gebruiken en het `ByteArrayOutputStream` -object door te geven.
   * Vul het Java `ByteArrayOutputStream` -object door de methode `javax.xml.transform.Transformer` object `transform` aan te roepen. Geef de objecten `javax.xml.transform.dom.DOMSource` en `javax.xml.transform.stream.StreamResult` door.
   * Maak een bytearray en wijs de grootte van het `ByteArrayOutputStream` -object toe aan de bytearray.
   * Vul de bytearray door de methode `toByteArray` van het object `ByteArrayOutputStream` aan te roepen.
   * Maak een `com.adobe.idp.Document` -object door de constructor ervan te gebruiken en de bytearray door te geven.

1. Verwijs naar een document van de PDF om te demonteren.

   * Maak een `java.util.Map` -object dat wordt gebruikt om invoerdocumenten van de PDF op te slaan met behulp van een `HashMap` -constructor.
   * Maak een `java.io.FileInputStream` -object door de constructor ervan te gebruiken en de locatie van het PDF-document door te geven om te demonteren.
   * Maak een `com.adobe.idp.Document` -object. Geef het `java.io.FileInputStream` -object door dat het PDF-document bevat dat moet worden gedemonteerd.
   * Voeg een item aan het object `java.util.Map` toe door de methode `put` ervan aan te roepen en de volgende argumenten door te geven:

      * Een tekenreekswaarde die de sleutelnaam vertegenwoordigt. Deze waarde moet overeenkomen met de waarde van het PDF-bronelement dat is opgegeven in het DDX-document. (In het DDX-document dat dynamisch wordt gemaakt, is de waarde `AssemblerResultPDF.pdf` .)
      * Een `com.adobe.idp.Document` -object dat het PDF-document bevat dat moet worden gedemonteerd.

1. Stel runtime-opties in.

   * Maak een `AssemblerOptionSpec` -object dat uitvoeringsopties opslaat met behulp van de bijbehorende constructor.
   * Stel runtime-opties in om aan uw bedrijfsvereisten te voldoen door een methode aan te roepen die tot het `AssemblerOptionSpec` -object behoort. Als u bijvoorbeeld de Assembler-service de instructie wilt geven een taak te blijven verwerken wanneer een fout optreedt, roept u de methode `setFailOnError` van het object `AssemblerOptionSpec` aan en geeft u deze door `false` .

1. Haal het PDF-document uit elkaar.

   Roep de methode `invokeDDX` van het object `AssemblerServiceClient` aan en geef de volgende waarden door:

   * Een `com.adobe.idp.Document` -object dat het dynamisch gemaakte DDX-document vertegenwoordigt
   * Een `java.util.Map` -object dat het te demonteren PDF-document bevat
   * Een `com.adobe.livecycle.assembler.client.AssemblerOptionSpec` -object dat de runtime-opties opgeeft, inclusief het standaardfont en het logniveau van de taak

   De methode `invokeDDX` retourneert een `com.adobe.livecycle.assembler.client.AssemblerResult` -object dat de gedemonteerde PDF-documenten en eventuele uitzonderingen bevat.

1. Sla de gedemonteerde PDF-documenten op.

   Voer de volgende handelingen uit om de gedemonteerde PDF-documenten te verkrijgen:

   * Roep de methode `getDocuments` van het object `AssemblerResult` aan. Deze methode retourneert een `java.util.Map` -object.
   * Doorloop het `java.util.Map` -object totdat u het resulterende `com.adobe.idp.Document` -object vindt.
   * Roep de methode `copyToFile` van het `com.adobe.idp.Document` -object aan om het PDF-document te extraheren.

**zie ook**

[Snel starten (SOAP modus): dynamisch een DDX-document maken met de Java API](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-dynamically-creating-a-ddx-document-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Een DDX-document dynamisch maken met de webservice-API {#dynamically-create-a-ddx-document-using-the-web-service-api}

Maak dynamisch een DDX-document en demonstreer een PDF-document met behulp van de API (webservice) voor vergaderingsservice:

1. Inclusief projectbestanden.

   Creeer een Microsoft .NET project dat MTOM gebruikt. Zorg ervoor dat u de volgende WSDL-definitie gebruikt wanneer u een serviceverwijzing instelt: `http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1` .

   >[!NOTE]
   >
   >Vervang `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een PDF Assembler-client.

   * Maak een `AssemblerServiceClient` -object met de standaardconstructor.
   * Maak een `AssemblerServiceClient.Endpoint.Address` -object met de `System.ServiceModel.EndpointAddress` -constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/AssemblerService?blob=mtom` ). U hoeft het attribuut `lc_version` niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.
   * Maak een `System.ServiceModel.BasicHttpBinding` -object door de waarde van het `AssemblerServiceClient.Endpoint.Binding` -veld op te halen. De geretourneerde waarde wordt gecast naar `BasicHttpBinding` .
   * Stel het veld `MessageEncoding` van het `System.ServiceModel.BasicHttpBinding` -object in op `WSMessageEncoding.Mtom` . Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld `AssemblerServiceClient.ClientCredentials.UserName.UserName` toe.
      * Wijs de bijbehorende wachtwoordwaarde toe aan het veld `AssemblerServiceClient.ClientCredentials.UserName.Password` .
      * Wijs de constante waarde `HttpClientCredentialType.Basic` toe aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType` .
      * Wijs de constante waarde `BasicHttpSecurityMode.TransportCredentialOnly` toe aan het veld `BasicHttpBindingSecurity.Security.Mode` .

1. Maak het DDX-document.

   * Maak een `System.Xml.XmlElement` -object met behulp van de constructor.
   * Maak het basiselement van het DDX-document door de methode `CreateElement` van het `XmlElement` -object aan te roepen. Deze methode maakt een `Element` -object dat het hoofdelement vertegenwoordigt. Geef een tekenreekswaarde die de naam van het element vertegenwoordigt, door aan de methode `CreateElement` . Stel een waarde voor het DDX-element in door de bijbehorende methode `SetAttribute` aan te roepen. Voeg ten slotte het element toe aan het DDX-document door de methode `AppendChild` van het object `XmlElement` aan te roepen. Geef het DDX-object door als een argument. De volgende coderegels tonen deze toepassingslogica:

     ` System.Xml.XmlElement root = ddx.CreateElement("DDX");  root.SetAttribute("xmlns", "https://ns.adobe.com/DDX/1.0/");  ddx.AppendChild(root);`

   * Maak het element `PDFsFromBookmarks` van het DDX-document door de methode `XmlElement` object `CreateElement` aan te roepen. Geef een tekenreekswaarde die de naam van het element vertegenwoordigt, door aan de methode `CreateElement` . Stel vervolgens een waarde voor het element in door de methode `SetAttribute` ervan aan te roepen. Voeg het element `PDFsFromBookmarks` toe aan het hoofdelement door de methode `DDX` element `AppendChild` aan te roepen. Geef het `PDFsFromBookmarks` -elementobject door als argument. De volgende coderegels tonen deze toepassingslogica:

     ` XmlElement PDFsFromBookmarks = ddx.CreateElement("PDFsFromBookmarks");  PDFsFromBookmarks.SetAttribute("prefix", "stmt");  root.AppendChild(PDFsFromBookmarks);`

   * Maak het element `PDF` van het DDX-document door de methode `XmlElement` object `CreateElement` aan te roepen. Geef een tekenreekswaarde die de naam van het element vertegenwoordigt, door aan de methode `CreateElement` . Stel vervolgens een waarde voor het onderliggende element in door de methode `SetAttribute` ervan aan te roepen. Voeg het element `PDF` toe aan het element `PDFsFromBookmarks` door de methode `PDFsFromBookmarks` van het element `AppendChild` aan te roepen. Geef het `PDF` -elementobject door als argument. Deze toepassingslogica wordt in de volgende coderegels getoond:

     ` XmlElement PDF = ddx.CreateElement("PDF");  PDF.SetAttribute("source", "AssemblerResultPDF.pdf");  PDFsFromBookmarks.AppendChild(PDF);`

1. Zet het DDX-document om.

   * Maak een `System.IO.MemoryStream` -object met behulp van de constructor.
   * Vul het `MemoryStream` -object met het DDX-document met het `XmlElement` -object dat het DDX-document vertegenwoordigt. Roep de methode `Save` van het object `XmlElement` aan en geef het object `MemoryStream` door.
   * Maak een bytearray en vul deze met gegevens in het `MemoryStream` -object. De volgende code toont deze toepassingslogica:

     ` int bufLen = Convert.ToInt32(stream.Length);  byte[] byteArray = new byte[bufLen];  stream.Position = 0;  int count = stream.Read(byteArray, 0, bufLen);`

   * Maak een `BLOB` -object. Wijs de bytearray toe aan het veld `MTOM` van het `BLOB` -object.

1. Verwijs naar een document van de PDF om te demonteren.

   * Maak een `BLOB` -object met behulp van de constructor. Het `BLOB` -object wordt gebruikt om het invoer-PDF-document op te slaan. Dit `BLOB` -object wordt als een argument aan `invokeOneDocument` doorgegeven.
   * Maak een `System.IO.FileStream` -object door de constructor ervan aan te roepen. Geef een tekenreekswaarde door die staat voor de bestandslocatie van het invoerdocument en de modus waarin het PDF-bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van het object `System.IO.FileStream` wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de eigenschap `Length` van het object `System.IO.FileStream` op te halen.
   * Vul de bytearray met streamgegevens door de methode `Read` van het object `System.IO.FileStream` aan te roepen en de bytearray, de startpositie en de lengte van de stream door te geven om te lezen.
   * Vul het object `BLOB` door de eigenschap `MTOM` ervan toe te wijzen aan de inhoud van de bytearray.

1. Stel runtime-opties in.

   * Maak een `AssemblerOptionSpec` -object dat uitvoeringsopties opslaat met behulp van de bijbehorende constructor.
   * Stel runtime-opties in om aan uw bedrijfsvereisten te voldoen door een waarde toe te wijzen aan een gegevenslid dat tot het `AssemblerOptionSpec` -object behoort. Als u bijvoorbeeld de Assembler-service wilt instrueren een taak te blijven verwerken wanneer een fout optreedt, wijst u `false` toe aan het gegevenslid van het `AssemblerOptionSpec` object `failOnError` .

1. Haal het PDF-document uit elkaar.

   Roep de methode `invokeDDX` van het object `AssemblerServiceClient` aan en geef de volgende waarden door:

   * Een `BLOB` -object dat het dynamisch gemaakte DDX-document vertegenwoordigt
   * De array `mapItem` die het invoerdocument PDF bevat
   * Een `AssemblerOptionSpec` -object dat uitvoeringsopties opgeeft

   De methode `invokeDDX` retourneert een `AssemblerResult` -object dat de resultaten van de taak en eventuele uitzonderingen bevat.

1. Sla de gedemonteerde PDF-documenten op.

   Voer de volgende handelingen uit om de nieuwe PDF-documenten te verkrijgen:

   * Open het veld `documents` van het `AssemblerResult` -object (een `Map` -object dat de gedemonteerde PDF-documenten bevat).
   * Doorloop het `Map` -object om elk resulterend document te verkrijgen. Vervolgens cast u het element `value` van dat arraylid naar een `BLOB` .
   * Extraheer de binaire gegevens die het PDF-document vertegenwoordigen door de eigenschap `MTOM` van het object `BLOB` te openen. Hiermee wordt een array met bytes geretourneerd die u naar een PDF-bestand kunt schrijven.

**zie ook**

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)
