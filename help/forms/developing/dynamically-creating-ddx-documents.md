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

Voordat u het DDX-document kunt doorgeven aan de Assembler-service, moet u de XML van een `org.w3c.dom.Document`-instantie omzetten in een `com.adobe.idp.Document`-instantie. Als u webservices gebruikt, zet u de XML van het gegevenstype dat wordt gebruikt om de XML te maken (bijvoorbeeld `XmlDocument`) om in een `BLOB`-instantie.

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
>Voor meer informatie over de dienst van de Assembler, zie [de Verwijzing van de Diensten voor AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Voor meer informatie over een DX- document, zie [de Dienst van de Assembler en DX Verwijzing](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Overzicht van stappen {#summary-of-steps}

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
* adobe-utilities.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)

**Een PDF Assembler-client maken**

Alvorens u programmatically een verrichting van de Assembler kunt uitvoeren, creeer een de dienstcliënt van de Assembler.

**Het DDX-document maken**

Maak een DDX-document met de programmeertaal die u gebruikt. Als u een DDX-document wilt maken dat een PDF-document demonteert, moet u ervoor zorgen dat het het element `PDFsFromBookmarks` bevat. Zet het gegevenstype dat wordt gebruikt om het DDX-document te maken om in een `com.adobe.idp.Document`-instantie als u de Java API gebruikt. Als u webservices gebruikt, zet u het gegevenstype om in een `BLOB`-instantie.

**Het DDX-document converteren**

Een DX-document dat is gemaakt met de klassen `org.w3c.dom` moet worden omgezet in een `com.adobe.idp.Document`-object. Gebruik Java XML-transformatieklassen om deze taak uit te voeren wanneer u de Java API gebruikt. Als u webservices gebruikt, zet u het DDX-document om in een `BLOB`-object.

**Verwijzen naar een PDF-document om te demonteren**

Als u een PDF-document wilt demonteren, verwijst u naar een PDF-bestand dat het PDF-document vertegenwoordigt dat u wilt demonteren. Als u een document doorgeeft aan de Assembler-service, wordt een afzonderlijk PDF-document geretourneerd voor elke bladwijzer van niveau 1 in het document.

**Uitvoeringsopties instellen**

U kunt runtime opties plaatsen die het gedrag van de dienst van de Assembler controleren terwijl het een baan uitvoert. U kunt bijvoorbeeld een optie instellen die de Assembler-service de opdracht geeft door te gaan met het verwerken van een taak als er een fout optreedt. Als u runtime-opties wilt instellen, gebruikt u een `AssemblerOptionSpec`-object.

**Het PDF-document dempen**

U kunt het PDF-document dempen door de bewerking `invokeDDX` aan te roepen. Geef het DDX-document door dat dynamisch is gemaakt. De Assembler-service retourneert gedemonteerde PDF-documenten in een verzamelingsobject.

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

   * Maak een `ServiceClientFactory`-object dat verbindingseigenschappen bevat.
   * Maak een `AssemblerServiceClient`-object door de constructor ervan te gebruiken en het object `ServiceClientFactory` door te geven.

1. Maak het DDX-document.

   * Maak een Java `DocumentBuilderFactory`-object door de `DocumentBuilderFactory`-klasse&quot; `newInstance`-methode aan te roepen.
   * Maak een Java `DocumentBuilder`-object door de methode `newDocumentBuilder` van het object `DocumentBuilderFactory` aan te roepen.
   * Roep de methode `DocumentBuilder` van het object `newDocument` aan om een `org.w3c.dom.Document`-object te instantiëren.
   * Maak het basiselement van het DDX-document door de methode `createElement` van het object `org.w3c.dom.Document` aan te roepen. Met deze methode wordt een `Element`-object gemaakt dat het basiselement vertegenwoordigt. Geef een tekenreekswaarde die de naam van het element vertegenwoordigt, door aan de methode `createElement`. Cast de terugkeerwaarde aan `Element`. Stel vervolgens een waarde voor het onderliggende element in door de methode `setAttribute` ervan aan te roepen. Voeg ten slotte het element aan het koptekstelement toe door de methode `appendChild` van het koptekstelement aan te roepen en geef het onderliggende-elementobject door als een argument. De volgende coderegels tonen deze toepassingslogica:
      ` Element root = (Element)document.createElement("DDX");  root.setAttribute("xmlns","https://ns.adobe.com/DDX/1.0/");  document.appendChild(root);`

   * Maak het element `PDFsFromBookmarks` door de methode `createElement` van het object `Document` aan te roepen. Geef een tekenreekswaarde die de naam van het element vertegenwoordigt, door aan de methode `createElement`. Cast de terugkeerwaarde aan `Element`. Plaats een waarde voor het `PDFsFromBookmarks` element door zijn `setAttribute` methode te roepen. Voeg het `PDFsFromBookmarks` element aan `DDX` element toe door de methode `appendChild` van het element te roepen DDX. Geef het elementobject `PDFsFromBookmarks` door als een argument. De volgende coderegels tonen deze toepassingslogica:

      ` Element PDFsFromBookmarks = (Element)document.createElement("PDFsFromBookmarks");  PDFsFromBookmarks.setAttribute("prefix","stmt");  root.appendChild(PDFsFromBookmarks);`

   * Maak een `PDF`-element door de methode `createElement` van het object `Document` aan te roepen. Geef een tekenreekswaarde door die de naam van het element vertegenwoordigt. Cast de terugkeerwaarde aan `Element`. Plaats een waarde voor het `PDF` element door zijn `setAttribute` methode te roepen. Voeg het `PDF` element aan het `PDFsFromBookmarks` element toe door `PDFsFromBookmarks` methode `appendChild` van het element te roepen. Geef het elementobject `PDF` door als een argument. Deze toepassingslogica wordt in de volgende coderegels getoond:

      ` Element PDF = (Element)document.createElement("PDF");  PDF.setAttribute("source","AssemblerResultPDF.pdf");  PDFsFromBookmarks.appendChild(PDF);`

1. Zet het DDX-document om.

   * Maak een `javax.xml.transform.Transformer`-object door de statische methode `newInstance` van het object aan te roepen.`javax.xml.transform.Transformer`
   * Maak een `Transformer`-object door de methode `newTransformer` van het object `TransformerFactory` aan te roepen.
   * Maak een `ByteArrayOutputStream`-object met de constructor ervan.
   * Maak een `javax.xml.transform.dom.DOMSource`-object met de constructor ervan. Geef het object `org.w3c.dom.Document` dat het DDX-document vertegenwoordigt door.
   * Maak een `javax.xml.transform.dom.DOMSource`-object door de constructor ervan te gebruiken en het object `ByteArrayOutputStream` door te geven.
   * Vul het Java `ByteArrayOutputStream`-object door de methode `transform` van het `javax.xml.transform.Transformer`-object aan te roepen. Geef de objecten `javax.xml.transform.dom.DOMSource` en `javax.xml.transform.stream.StreamResult` door.
   * Maak een bytearray en wijs de grootte van het `ByteArrayOutputStream`-object toe aan de bytearray.
   * Vul de bytearray door de methode `toByteArray` van het object `ByteArrayOutputStream` aan te roepen.
   * Maak een `com.adobe.idp.Document`-object door de constructor ervan te gebruiken en de bytearray door te geven.

1. Verwijs naar een PDF-document dat u wilt demonteren.

   * Maak een `java.util.Map`-object dat wordt gebruikt om invoer-PDF-documenten op te slaan met behulp van een `HashMap`-constructor.
   * Maak een `java.io.FileInputStream`-object door de constructor ervan te gebruiken en de locatie van het PDF-document door te geven om te demonteren.
   * Maak een `com.adobe.idp.Document`-object. Geef het `java.io.FileInputStream`-object met het PDF-document door dat moet worden gedemonteerd.
   * Voeg een item aan het object `java.util.Map` toe door de methode `put` ervan aan te roepen en de volgende argumenten door te geven:

      * Een tekenreekswaarde die de sleutelnaam vertegenwoordigt. Deze waarde moet overeenkomen met de waarde van het PDF-bronelement dat is opgegeven in het DDX-document. (In het DDX-document dat dynamisch wordt gemaakt, is de waarde `AssemblerResultPDF.pdf`.)
      * Een `com.adobe.idp.Document`-object dat het te demonteren PDF-document bevat.

1. Stel runtime-opties in.

   * Maak een `AssemblerOptionSpec`-object dat uitvoeringsopties opslaat met de constructor ervan.
   * Stel runtime-opties in om aan uw bedrijfsvereisten te voldoen door een methode aan te roepen die tot het object `AssemblerOptionSpec` behoort. Bijvoorbeeld, om de dienst van de Assembler op te dragen om een baan te blijven verwerken wanneer een fout voorkomt, haalt de `AssemblerOptionSpec` methode `setFailOnError` van objecten aan en gaat `false` over.

1. Het PDF-document demonteren.

   Roep de methode `invokeDDX` van het object `AssemblerServiceClient` aan en geef de volgende waarden door:

   * Een `com.adobe.idp.Document`-object dat het dynamisch gemaakte DDX-document vertegenwoordigt
   * Een `java.util.Map`-object dat het te demonteren PDF-document bevat
   * Een `com.adobe.livecycle.assembler.client.AssemblerOptionSpec`-object dat de runtime-opties opgeeft, inclusief het standaardfont en het taaklogniveau

   De methode `invokeDDX` retourneert een `com.adobe.livecycle.assembler.client.AssemblerResult`-object dat de gedemonteerde PDF-documenten en eventuele uitzonderingen bevat.

1. Sla de gedemonteerde PDF-documenten op.

   Voer de volgende handelingen uit om de gedemonteerde PDF-documenten te verkrijgen:

   * Roep de methode `AssemblerResult` van het object `getDocuments` aan. Deze methode retourneert een `java.util.Map`-object.
   * Doorloop het object `java.util.Map` totdat u het resulterende object `com.adobe.idp.Document` hebt gevonden.
   * Roep de methode `com.adobe.idp.Document` van het object `copyToFile` aan om het PDF-document uit te pakken.

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
   >Vervang `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een PDF Assembler-client.

   * Maak een `AssemblerServiceClient`-object met de standaardconstructor.
   * Maak een `AssemblerServiceClient.Endpoint.Address`-object met de constructor `System.ServiceModel.EndpointAddress`. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/AssemblerService?blob=mtom`). U hoeft het `lc_version`-kenmerk niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.
   * Maak een `System.ServiceModel.BasicHttpBinding`-object door de waarde van het veld `AssemblerServiceClient.Endpoint.Binding` op te halen. Cast de terugkeerwaarde aan `BasicHttpBinding`.
   * Stel het veld `System.ServiceModel.BasicHttpBinding` van het object `MessageEncoding` in op `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam voor het AEM aan het veld `AssemblerServiceClient.ClientCredentials.UserName.UserName` toe.
      * Wijs de overeenkomstige wachtwoordwaarde aan het gebied `AssemblerServiceClient.ClientCredentials.UserName.Password` toe.
      * Wijs de constante waarde `HttpClientCredentialType.Basic` aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType` toe.
      * Wijs de constante waarde `BasicHttpSecurityMode.TransportCredentialOnly` aan het veld `BasicHttpBindingSecurity.Security.Mode` toe.

1. Maak het DDX-document.

   * Maak een `System.Xml.XmlElement`-object met de constructor ervan.
   * Maak het basiselement van het DDX-document door de methode `CreateElement` van het object `XmlElement` aan te roepen. Met deze methode wordt een `Element`-object gemaakt dat het basiselement vertegenwoordigt. Geef een tekenreekswaarde die de naam van het element vertegenwoordigt, door aan de methode `CreateElement`. Plaats een waarde voor het element DDX door zijn `SetAttribute` methode te roepen. Ten slotte voegt u het element aan het DDX-document toe door de methode `XmlElement` van het object `AppendChild` aan te roepen. Geef het DDX-object door als een argument. De volgende coderegels tonen deze toepassingslogica:

      ` System.Xml.XmlElement root = ddx.CreateElement("DDX");  root.SetAttribute("xmlns", "https://ns.adobe.com/DDX/1.0/");  ddx.AppendChild(root);`

   * Maak het element `PDFsFromBookmarks` van het DDX-document door de methode `CreateElement` van het `XmlElement`-object aan te roepen. Geef een tekenreekswaarde die de naam van het element vertegenwoordigt, door aan de methode `CreateElement`. Stel vervolgens een waarde voor het element in door de methode `SetAttribute` ervan aan te roepen. Voeg het `PDFsFromBookmarks` element aan het wortelelement toe door `DDX` methode `AppendChild` van het element te roepen. Geef het elementobject `PDFsFromBookmarks` door als een argument. De volgende coderegels tonen deze toepassingslogica:

      ` XmlElement PDFsFromBookmarks = ddx.CreateElement("PDFsFromBookmarks");  PDFsFromBookmarks.SetAttribute("prefix", "stmt");  root.AppendChild(PDFsFromBookmarks);`

   * Maak het element `PDF` van het DDX-document door de methode `CreateElement` van het `XmlElement`-object aan te roepen. Geef een tekenreekswaarde die de naam van het element vertegenwoordigt, door aan de methode `CreateElement`. Stel vervolgens een waarde voor het onderliggende element in door de methode `SetAttribute` ervan aan te roepen. Voeg het `PDF` element aan het `PDFsFromBookmarks` element toe door `PDFsFromBookmarks` methode `AppendChild` van het element te roepen. Geef het elementobject `PDF` door als een argument. Deze toepassingslogica wordt in de volgende coderegels getoond:

      ` XmlElement PDF = ddx.CreateElement("PDF");  PDF.SetAttribute("source", "AssemblerResultPDF.pdf");  PDFsFromBookmarks.AppendChild(PDF);`

1. Zet het DDX-document om.

   * Maak een `System.IO.MemoryStream`-object met de constructor ervan.
   * Vul het `MemoryStream` voorwerp met het DX- document door het `XmlElement` voorwerp te gebruiken dat het DX- document vertegenwoordigt. Roep de methode `XmlElement` van het object `Save` aan en geef het object `MemoryStream` door.
   * Maak een bytearray en vul deze met gegevens in het object `MemoryStream`. De volgende code toont deze toepassingslogica:

      ` int bufLen = Convert.ToInt32(stream.Length);  byte[] byteArray = new byte[bufLen];  stream.Position = 0;  int count = stream.Read(byteArray, 0, bufLen);`

   * Maak een `BLOB`-object. Wijs de bytearray toe aan het veld `MTOM` van het `BLOB`-object.

1. Verwijs naar een PDF-document dat u wilt demonteren.

   * Maak een `BLOB`-object met de constructor ervan. Met het object `BLOB` wordt het invoer-PDF-document opgeslagen. Dit `BLOB` voorwerp wordt overgegaan tot `invokeOneDocument` als argument.
   * Maak een `System.IO.FileStream`-object door de constructor ervan aan te roepen. Geef een tekenreekswaarde door die staat voor de bestandslocatie van het invoer-PDF-document en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van het object `System.IO.FileStream` wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de eigenschap `System.IO.FileStream` van het object `Length` op te halen.
   * Vul de bytearray met streamgegevens door de methode `Read` van het object `System.IO.FileStream` aan te roepen en de bytearray, de startpositie en de lengte van de stream door te geven om te lezen.
   * Vul het object `BLOB` door de eigenschap `MTOM` van het object toe te wijzen aan de inhoud van de bytearray.

1. Stel runtime-opties in.

   * Maak een `AssemblerOptionSpec`-object dat uitvoeringsopties opslaat met de constructor ervan.
   * Stel runtime-opties in om aan uw bedrijfsvereisten te voldoen door een waarde toe te wijzen aan een gegevenslid dat tot het object `AssemblerOptionSpec` behoort. Bijvoorbeeld, om de dienst van de Assembler op te dragen om een baan te blijven verwerken wanneer een fout voorkomt, wijs `false` aan `AssemblerOptionSpec` het gegevenslid van `failOnError` van het voorwerp toe.

1. Het PDF-document demonteren.

   Roep de methode `invokeDDX` van het object `AssemblerServiceClient` aan en geef de volgende waarden door:

   * Een `BLOB`-object dat het dynamisch gemaakte DDX-document vertegenwoordigt
   * De `mapItem`-array die het invoer-PDF-document bevat
   * Een `AssemblerOptionSpec`-object dat uitvoeringsopties opgeeft

   De methode `invokeDDX` retourneert een `AssemblerResult`-object dat de resultaten van de taak en eventuele uitzonderingen bevat die zich hebben voorgedaan.

1. Sla de gedemonteerde PDF-documenten op.

   Voer de volgende handelingen uit om de nieuwe PDF-documenten te verkrijgen:

   * Open het veld `AssemblerResult` van het object `documents`. Dit is een `Map`-object dat de gedemonteerde PDF-documenten bevat.
   * Doorloop het object `Map` om elk resulterend document te verkrijgen. Vervolgens cast u `value` van dat arraylid naar een `BLOB`.
   * Pak de binaire gegevens die het PDF-document vertegenwoordigen uit door de eigenschap `MTOM` van het object `BLOB` te openen. Hiermee wordt een array met bytes geretourneerd die u naar een PDF-bestand kunt schrijven.

**Zie ook**

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)
