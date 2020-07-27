---
title: DDX-documenten dynamisch maken
seo-title: DDX-documenten dynamisch maken
description: 'null'
seo-description: 'null'
uuid: b73e8069-6c9f-4517-a0ae-f3d503191d2d
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 2ad227de-68a8-446f-8c4f-a33a6f95bec8
translation-type: tm+mt
source-git-commit: 1343cc33a1e1ce26c0770a3b49317e82353497ab
workflow-type: tm+mt
source-wordcount: '2123'
ht-degree: 0%

---


# DDX-documenten dynamisch maken {#dynamically-creating-ddx-documents}

U kunt dynamisch een DDX-document maken dat kan worden gebruikt om een Assembler-bewerking uit te voeren. Door een DDX-document dynamisch te maken, kunt u waarden in het DDX-document gebruiken die tijdens runtime worden verkregen. Om een DX- document dynamisch tot stand te brengen, gebruik klassen die tot de programmeertaal behoren die u gebruikt. Als u bijvoorbeeld uw clienttoepassing ontwikkelt met Java, gebruikt u klassen die bij het `org.w3c.dom.*`pakket horen. Eveneens, als u Microsoft .NET gebruikt, gebruik klassen die tot `System.Xml` namespace behoren.

Voordat u het DDX-document kunt doorgeven aan de Assembler-service, moet u de XML van een `org.w3c.dom.Document` instantie omzetten in een `com.adobe.idp.Document` instantie. Als u webservices gebruikt, moet u de XML van het gegevenstype dat wordt gebruikt om de XML te maken (bijvoorbeeld `XmlDocument`), omzetten naar een `BLOB` instantie.

Voor deze bespreking, veronderstel dat het volgende Dx- document dynamisch wordt gecreeerd.

```xml
 <?xml version="1.0" encoding="UTF-8"?>
 <DDX xmlns="https://ns.adobe.com/DDX/1.0/">
      <PDFsFromBookmarks prefix="stmt">
     <PDF source="AssemblerResultPDF.pdf"/>
 </PDFsFromBookmarks>
 </DDX>
```

Dit DDX-document demonteert een PDF-document. Het wordt aanbevolen dat u vertrouwd bent met het demonteren van PDF-documenten.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Assembler, zie de Verwijzing van de [Diensten voor AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Voor meer informatie over een DX- document, zie de Dienst van de [Assembler en de Verwijzing](https://www.adobe.com/go/learn_aemforms_ddx_63)DDX.

## Overzicht van de stappen {#summary-of-steps}

Als u een PDF-document wilt demonteren met een dynamisch gemaakt DDX-document, voert u de volgende taken uit:

1. Inclusief projectbestanden.
1. Maak een PDF Assembler-client.
1. Maak het DDX-document.
1. Zet het DDX-document om.
1. Stel runtime-opties in.
1. Het PDF-document demonteren.
1. Sla de gedemonteerde PDF-documenten op.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-assembler-client.jar
* adobe-utilities.jar (vereist als AEM Forms worden geïmplementeerd op JBoss)
* jbossall-client.jar (vereist als AEM Forms worden geïmplementeerd op JBoss)

**Een PDF Assembler-client maken**

Alvorens u programmatically een verrichting van de Assembler kunt uitvoeren, creeer een de dienstcliënt van de Assembler.

**Het DDX-document maken**

Maak een DDX-document met de programmeertaal die u gebruikt. Als u een DDX-document wilt maken dat een PDF-document demonteert, moet u controleren of dit het `PDFsFromBookmarks` element bevat. Zet het gegevenstype dat wordt gebruikt om het DDX-document te maken, om in een `com.adobe.idp.Document` instantie als u de Java API gebruikt. Als u webservices gebruikt, zet u het gegevenstype om in een `BLOB` instantie.

**Het DDX-document converteren**

Een DDX-document dat is gemaakt met behulp van `org.w3c.dom` klassen, moet worden omgezet in een `com.adobe.idp.Document` object. Gebruik Java XML-transformatieklassen om deze taak uit te voeren wanneer u de Java API gebruikt. Als u webservices gebruikt, zet u het DDX-document om in een `BLOB` object.

**Verwijzen naar een PDF-document om te demonteren**

Als u een PDF-document wilt demonteren, verwijst u naar een PDF-bestand dat het PDF-document vertegenwoordigt dat u wilt demonteren. Als u een document doorgeeft aan de Assembler-service, wordt een afzonderlijk PDF-document geretourneerd voor elke bladwijzer van niveau 1 in het document.

**Uitvoeringsopties instellen**

U kunt runtime opties plaatsen die het gedrag van de dienst van de Assembler controleren terwijl het een baan uitvoert. U kunt bijvoorbeeld een optie instellen die de Assembler-service de opdracht geeft door te gaan met het verwerken van een taak als er een fout optreedt. Gebruik een `AssemblerOptionSpec` object om uitvoeringsopties in te stellen.

**Het PDF-document dempen**

Schakel het PDF-document uit door de `invokeDDX` bewerking aan te roepen. Geef het DDX-document door dat dynamisch is gemaakt. De Assembler-service retourneert gedemonteerde PDF-documenten in een verzamelingsobject.

**De gedemonteerde PDF-documenten opslaan**

Alle gedemonteerde PDF-documenten worden geretourneerd in een verzamelingsobject. Doorloop het verzamelingsobject en sla elk PDF-document op als een PDF-bestand.

**Zie ook**

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

   * Maak een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Maak een `AssemblerServiceClient` object door de constructor ervan te gebruiken en het `ServiceClientFactory` object door te geven.

1. Maak het DDX-document.

   * Maak een Java- `DocumentBuilderFactory` object door de `DocumentBuilderFactory` methode `newInstance` class aan te roepen.
   * Maak een Java- `DocumentBuilder` object door de `DocumentBuilderFactory` methode van het `newDocumentBuilder` object aan te roepen.
   * Roep de `DocumentBuilder` methode van het `newDocument` object aan om een `org.w3c.dom.Document` object te instantiëren.
   * Maak het basiselement van het DDX-document door de `org.w3c.dom.Document` methode van het `createElement` object aan te roepen. Met deze methode maakt u een `Element` object dat het basiselement vertegenwoordigt. Geef een tekenreekswaarde die de naam van het element vertegenwoordigt, door aan de `createElement` methode. Kiezen naar de geretourneerde waarde `Element`. Stel vervolgens een waarde in voor het onderliggende element door de `setAttribute` methode ervan aan te roepen. Voeg ten slotte het element aan het koptekstelement toe door de methode van het koptekstelement aan te roepen en geef het onderliggende elementobject door als een argument. `appendChild` De volgende coderegels tonen deze toepassingslogica:
      ` Element root = (Element)document.createElement("DDX");  root.setAttribute("xmlns","https://ns.adobe.com/DDX/1.0/");  document.appendChild(root);`

   * Maak het `PDFsFromBookmarks` element door de `Document` methode van het `createElement` object aan te roepen. Geef een tekenreekswaarde die de naam van het element vertegenwoordigt, door aan de `createElement` methode. Kiezen naar de geretourneerde waarde `Element`. Stel een waarde voor het `PDFsFromBookmarks` element in door de `setAttribute` methode ervan aan te roepen. Voeg het `PDFsFromBookmarks` element aan het `DDX` element toe door de `appendChild` methode van het element DDX te roepen. Geef het `PDFsFromBookmarks` elementobject door als een argument. De volgende coderegels tonen deze toepassingslogica:

      ` Element PDFsFromBookmarks = (Element)document.createElement("PDFsFromBookmarks");  PDFsFromBookmarks.setAttribute("prefix","stmt");  root.appendChild(PDFsFromBookmarks);`

   * Maak een `PDF` element door de `Document` methode van het `createElement` object aan te roepen. Geef een tekenreekswaarde door die de naam van het element vertegenwoordigt. Kiezen naar de geretourneerde waarde `Element`. Stel een waarde voor het `PDF` element in door de `setAttribute` methode ervan aan te roepen. Voeg het `PDF` element aan het `PDFsFromBookmarks` element toe door de `PDFsFromBookmarks` methode van het `appendChild` element te roepen. Geef het `PDF` elementobject door als een argument. Deze toepassingslogica wordt in de volgende coderegels getoond:

      ` Element PDF = (Element)document.createElement("PDF");  PDF.setAttribute("source","AssemblerResultPDF.pdf");  PDFsFromBookmarks.appendChild(PDF);`

1. Zet het DDX-document om.

   * Maak een `javax.xml.transform.Transformer` object door de statische `javax.xml.transform.Transformer` methode van het `newInstance` object aan te roepen.
   * Maak een `Transformer` object door de `TransformerFactory` methode van het `newTransformer` object aan te roepen.
   * Maak een `ByteArrayOutputStream` object met de constructor ervan.
   * Maak een `javax.xml.transform.dom.DOMSource` object met de constructor ervan. Geef het `org.w3c.dom.Document` object dat het DDX-document vertegenwoordigt door.
   * Maak een `javax.xml.transform.dom.DOMSource` object door de constructor ervan te gebruiken en het `ByteArrayOutputStream` object door te geven.
   * Vul het Java- `ByteArrayOutputStream` object door de `javax.xml.transform.Transformer` methode van het `transform` object aan te roepen. Geef de `javax.xml.transform.dom.DOMSource` objecten en de `javax.xml.transform.stream.StreamResult` objecten door.
   * Maak een bytearray en wijs de grootte van het `ByteArrayOutputStream` object toe aan de bytearray.
   * Vul de bytearray door de `ByteArrayOutputStream` `toByteArray` methode van het object aan te roepen.
   * Maak een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en de bytearray door te geven.

1. Verwijs naar een PDF-document dat u wilt demonteren.

   * Maak een `java.util.Map` object dat wordt gebruikt om invoer-PDF-documenten op te slaan met behulp van een `HashMap` constructor.
   * Maak een `java.io.FileInputStream` object door de constructor ervan te gebruiken en de locatie van het PDF-document door te geven om het te demonteren.
   * Create a `com.adobe.idp.Document` object. Geef het `java.io.FileInputStream` object met het PDF-document door dat u wilt demonteren.
   * Voeg een item aan het `java.util.Map` `put` object toe door de methode ervan aan te roepen en de volgende argumenten door te geven:

      * Een tekenreekswaarde die de sleutelnaam vertegenwoordigt. Deze waarde moet overeenkomen met de waarde van het PDF-bronelement dat is opgegeven in het DDX-document. (In het DDX-document dat dynamisch wordt gemaakt, is de waarde `AssemblerResultPDF.pdf`.)
      * Een `com.adobe.idp.Document` object dat het PDF-document bevat dat moet worden gedemonteerd.

1. Stel runtime-opties in.

   * Maak een `AssemblerOptionSpec` object dat uitvoeringsopties opslaat met de constructor ervan.
   * Stel runtime-opties in om aan uw bedrijfsvereisten te voldoen door een methode aan te roepen die tot het `AssemblerOptionSpec` object behoort. Bijvoorbeeld, om de dienst van de Assembler op te dragen om een baan te blijven verwerken wanneer een fout voorkomt, haalt de methode van `AssemblerOptionSpec` objecten aan en gaat over `setFailOnError` `false`.

1. Het PDF-document demonteren.

   Roep de methode van het `AssemblerServiceClient` `invokeDDX` object aan en geef de volgende waarden door:

   * Een `com.adobe.idp.Document` object dat het dynamisch gemaakte DDX-document vertegenwoordigt
   * Een `java.util.Map` object dat het te demonteren PDF-document bevat
   * Een `com.adobe.livecycle.assembler.client.AssemblerOptionSpec` object dat de runtime-opties opgeeft, inclusief het standaardfont en het logniveau van de taak

   De `invokeDDX` methode retourneert een `com.adobe.livecycle.assembler.client.AssemblerResult` object dat de gedemonteerde PDF-documenten en eventuele uitzonderingen bevat.

1. Sla de gedemonteerde PDF-documenten op.

   Voer de volgende handelingen uit om de gedemonteerde PDF-documenten te verkrijgen:

   * Roep de `AssemblerResult` methode van het `getDocuments` object aan. Deze methode retourneert een `java.util.Map` object.
   * Doorloop het `java.util.Map` object totdat u het resulterende `com.adobe.idp.Document` object vindt.
   * Roep de `com.adobe.idp.Document` methode van het `copyToFile` object aan om het PDF-document uit te pakken.

**Zie ook**

[Snel starten (SOAP-modus): Een DDX-document dynamisch maken met de Java API](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-dynamically-creating-a-ddx-document-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Een DDX-document dynamisch maken met de webservice-API {#dynamically-create-a-ddx-document-using-the-web-service-api}

Maak dynamisch een DDX-document en demonstreer een PDF-document met de API (webservice) van Assembler Service:

1. Inclusief projectbestanden.

   Creeer een project van Microsoft .NET dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt wanneer het plaatsen van een de dienstverwijzing: `http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een PDF Assembler-client.

   * Maak een `AssemblerServiceClient` object met de standaardconstructor.
   * Maak een `AssemblerServiceClient.Endpoint.Address` object met de `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde door die de WSDL opgeeft voor de service AEM Forms (bijvoorbeeld `http://localhost:8080/soap/services/AssemblerService?blob=mtom`). U hoeft het `lc_version` kenmerk niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.
   * Maak een `System.ServiceModel.BasicHttpBinding` object door de waarde van het `AssemblerServiceClient.Endpoint.Binding` veld op te halen. Kiezen naar de geretourneerde waarde `BasicHttpBinding`.
   * Stel het `System.ServiceModel.BasicHttpBinding` veld van het `MessageEncoding` object in op `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam voor AEM-formulieren toe aan het veld `AssemblerServiceClient.ClientCredentials.UserName.UserName`.
      * Wijs de bijbehorende wachtwoordwaarde aan het veld toe `AssemblerServiceClient.ClientCredentials.UserName.Password`.
      * Wijs de constante waarde toe `HttpClientCredentialType.Basic` aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Wijs de constante waarde toe `BasicHttpSecurityMode.TransportCredentialOnly` aan het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Maak het DDX-document.

   * Maak een `System.Xml.XmlElement` object met de constructor ervan.
   * Maak het basiselement van het DDX-document door de `XmlElement` methode van het `CreateElement` object aan te roepen. Met deze methode maakt u een `Element` object dat het basiselement vertegenwoordigt. Geef een tekenreekswaarde die de naam van het element vertegenwoordigt, door aan de `CreateElement` methode. Plaats een waarde voor het element DDX door zijn `SetAttribute` methode te roepen. Voeg ten slotte het element aan het DDX-document toe door de `XmlElement` methode van het `AppendChild` object aan te roepen. Geef het DDX-object door als een argument. De volgende coderegels tonen deze toepassingslogica:

      ` System.Xml.XmlElement root = ddx.CreateElement("DDX");  root.SetAttribute("xmlns", "https://ns.adobe.com/DDX/1.0/");  ddx.AppendChild(root);`

   * Maak het `PDFsFromBookmarks` element van het DDX-document door de `XmlElement` methode van het `CreateElement` object aan te roepen. Geef een tekenreekswaarde die de naam van het element vertegenwoordigt, door aan de `CreateElement` methode. Stel vervolgens een waarde voor het element in door de `SetAttribute` methode ervan aan te roepen. Voeg het `PDFsFromBookmarks` element aan het wortelelement toe door de `DDX` methode van het `AppendChild` element te roepen. Geef het `PDFsFromBookmarks` elementobject door als een argument. De volgende coderegels tonen deze toepassingslogica:

      ` XmlElement PDFsFromBookmarks = ddx.CreateElement("PDFsFromBookmarks");  PDFsFromBookmarks.SetAttribute("prefix", "stmt");  root.AppendChild(PDFsFromBookmarks);`

   * Maak het `PDF` element van het DDX-document door de `XmlElement` methode van het `CreateElement` object aan te roepen. Geef een tekenreekswaarde die de naam van het element vertegenwoordigt, door aan de `CreateElement` methode. Stel vervolgens een waarde in voor het onderliggende element door de `SetAttribute` methode ervan aan te roepen. Voeg het `PDF` element aan het `PDFsFromBookmarks` element toe door de `PDFsFromBookmarks` methode van het `AppendChild` element te roepen. Geef het `PDF` elementobject door als een argument. Deze toepassingslogica wordt in de volgende coderegels getoond:

      ` XmlElement PDF = ddx.CreateElement("PDF");  PDF.SetAttribute("source", "AssemblerResultPDF.pdf");  PDFsFromBookmarks.AppendChild(PDF);`

1. Zet het DDX-document om.

   * Maak een `System.IO.MemoryStream` object met de constructor ervan.
   * Vul het `MemoryStream` object met het DDX-document met het `XmlElement` object dat het DDX-document vertegenwoordigt. Roep de `XmlElement` methode van het `Save` object aan en geef het `MemoryStream` object door.
   * Maak een bytearray en vul deze met gegevens in het `MemoryStream` object. De volgende code toont deze toepassingslogica:

      ` int bufLen = Convert.ToInt32(stream.Length);  byte[] byteArray = new byte[bufLen];  stream.Position = 0;  int count = stream.Read(byteArray, 0, bufLen);`

   * Create a `BLOB` object. Wijs de bytearray toe aan het `BLOB` veld van het `MTOM` object.

1. Verwijs naar een PDF-document dat u wilt demonteren.

   * Maak een `BLOB` object met de constructor ervan. Het `BLOB` object wordt gebruikt om het invoer-PDF-document op te slaan. Dit `BLOB` object wordt als een argument `invokeOneDocument` aan het object doorgegeven.
   * Maak een `System.IO.FileStream` object door de constructor ervan aan te roepen. Geef een tekenreekswaarde door die staat voor de bestandslocatie van het invoer-PDF-document en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van het `System.IO.FileStream` object wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` eigenschap van het `Length` object op te halen.
   * Vul de bytearray met streamgegevens door de methode van het `System.IO.FileStream` `Read` object aan te roepen en de bytearray, de startpositie en de lengte van de stream door te geven om te lezen.
   * Vul het `BLOB` object door de `MTOM` eigenschap ervan toe te wijzen aan de inhoud van de bytearray.

1. Stel runtime-opties in.

   * Maak een `AssemblerOptionSpec` object dat uitvoeringsopties opslaat met de constructor ervan.
   * Stel runtime-opties in om aan uw bedrijfsvereisten te voldoen door een waarde toe te wijzen aan een gegevenslid dat tot het `AssemblerOptionSpec` object behoort. Bijvoorbeeld, om de dienst van de Assembler op te dragen om een baan te blijven verwerken wanneer een fout voorkomt, wijs `false` aan het de `AssemblerOptionSpec` gegevenslid van het `failOnError` voorwerp toe.

1. Het PDF-document demonteren.

   Roep de methode van het `AssemblerServiceClient` `invokeDDX` object aan en geef de volgende waarden door:

   * Een `BLOB` object dat het dynamisch gemaakte DDX-document vertegenwoordigt
   * De `mapItem` array die het invoer-PDF-document bevat
   * Een `AssemblerOptionSpec` object dat uitvoeringsopties opgeeft

   De `invokeDDX` methode retourneert een `AssemblerResult` object dat de resultaten van de taak en eventuele uitzonderingen bevat die zich hebben voorgedaan.

1. Sla de gedemonteerde PDF-documenten op.

   Voer de volgende handelingen uit om de nieuwe PDF-documenten te verkrijgen:

   * Open het `AssemblerResult` veld van het `documents` object. Dit is een `Map` object dat de gedemonteerde PDF-documenten bevat.
   * Doorloop het `Map` object om elk resulterend document te verkrijgen. Dan, giet dat serielid `value` aan een `BLOB`.
   * Pak de binaire gegevens die het PDF-document vertegenwoordigen, uit door de `BLOB` eigenschap van het `MTOM` object te openen. Hiermee wordt een array met bytes geretourneerd die u naar een PDF-bestand kunt schrijven.

**Zie ook**

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)
