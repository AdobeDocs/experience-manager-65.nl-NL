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
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '2153'
ht-degree: 0%

---

# DDX-documenten dynamisch maken {#dynamically-creating-ddx-documents}

**Voorbeelden en voorbeelden in dit document gelden alleen voor AEM Forms in JEE-omgeving.**

U kunt dynamisch een DDX-document maken dat kan worden gebruikt om een Assembler-bewerking uit te voeren. Door een DDX-document dynamisch te maken, kunt u waarden in het DDX-document gebruiken die tijdens runtime worden verkregen. Om een DX- document dynamisch tot stand te brengen, gebruik klassen die tot de programmeertaal behoren die u gebruikt. Als u bijvoorbeeld uw clienttoepassing ontwikkelt met Java, gebruikt u klassen die bij het `org.w3c.dom.*`pakket. Eveneens, als u Microsoft .NET gebruikt, gebruiksklassen die tot het behoren `System.Xml` naamruimte.

Voordat u het DDX-document kunt doorgeven aan de Assembler-service, moet u de XML vanuit een `org.w3c.dom.Document` instantie aan een `com.adobe.idp.Document` -instantie. Als u webservices gebruikt, converteert u de XML vanuit het gegevenstype dat wordt gebruikt om de XML te maken (bijvoorbeeld `XmlDocument`) aan een `BLOB` -instantie.

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
>Voor meer informatie over de dienst van de Assembler, zie [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Voor meer informatie over een DDX-document raadpleegt u [De Verwijzing van de AssemblerDienst en DDX](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Overzicht van de stappen {#summary-of-steps}

Als u een PDF-document wilt demonteren met een dynamisch gemaakt DDX-document, voert u de volgende taken uit:

1. Inclusief projectbestanden.
1. Maak een PDF Assembler-client.
1. Maak het DDX-document.
1. Zet het DDX-document om.
1. Stel runtime-opties in.
1. Haal het PDF-document uit elkaar.
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

Maak een DDX-document met de programmeertaal die u gebruikt. Als u een DDX-document wilt maken dat een PDF-document demonteert, controleert u of het het volgende bevat: `PDFsFromBookmarks` element. Zet het gegevenstype om dat wordt gebruikt om het DDX-document te maken `com.adobe.idp.Document` als u de Java API gebruikt. Als u webservices gebruikt, zet u het gegevenstype om in een `BLOB` -instantie.

**Het DDX-document converteren**

Een DX-document dat is gemaakt met `org.w3c.dom` klassen moeten worden omgezet in een `com.adobe.idp.Document` object. Gebruik Java XML-transformatieklassen om deze taak uit te voeren wanneer u de Java API gebruikt. Als u webservices gebruikt, zet u het DDX-document om in een `BLOB` object.

**Verwijzen naar een PDF-document om te demonteren**

Als u een PDF-document wilt demonteren, verwijst u naar een PDF-bestand dat het PDF-document vertegenwoordigt dat u wilt demonteren. Wanneer het tot de dienst van de Assembler wordt overgegaan, wordt een afzonderlijk document van PDF teruggegeven voor elke niveau 1 referentie in het document.

**Uitvoeringsopties instellen**

U kunt runtime opties plaatsen die het gedrag van de dienst van de Assembler controleren terwijl het een baan uitvoert. U kunt bijvoorbeeld een optie instellen die de Assembler-service de opdracht geeft door te gaan met het verwerken van een taak als er een fout optreedt. Als u runtime-opties wilt instellen, gebruikt u een `AssemblerOptionSpec` object.

**Het PDF-document demonteren**

U kunt het PDF-document deassembleren door het `invokeDDX` -bewerking. Geef het DDX-document door dat dynamisch is gemaakt. De dienst van de Assembler keert gedemonteerde documenten van PDF binnen een inzamelingsvoorwerp terug.

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

   * Een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Een `AssemblerServiceClient` object door de constructor ervan te gebruiken en de `ServiceClientFactory` object.

1. Maak het DDX-document.

   * Een Java maken `DocumentBuilderFactory` object aanroepen `DocumentBuilderFactory` class&#39; `newInstance` methode.
   * Een Java maken `DocumentBuilder` object aanroepen `DocumentBuilderFactory` object `newDocumentBuilder` methode.
   * Roep de `DocumentBuilder` object `newDocument` methode om een instantie te maken `org.w3c.dom.Document` object.
   * Maak het basiselement van het DDX-document door het `org.w3c.dom.Document` object `createElement` methode. Deze methode maakt een `Element` object dat het basiselement vertegenwoordigt. Geef een tekenreekswaarde die de naam van het element vertegenwoordigt, door aan de `createElement` methode. De geretourneerde waarde omzetten in `Element`. Stel vervolgens een waarde in voor het onderliggende element door de bijbehorende `setAttribute` methode. Voeg ten slotte het element aan het koptekstelement toe door het koptekstelement aan te roepen `appendChild` en geeft u het onderliggende-elementobject door als argument. De volgende coderegels tonen deze toepassingslogica:
     ` Element root = (Element)document.createElement("DDX");  root.setAttribute("xmlns","https://ns.adobe.com/DDX/1.0/");  document.appendChild(root);`

   * Maak de `PDFsFromBookmarks` element door het `Document` object `createElement` methode. Geef een tekenreekswaarde die de naam van het element vertegenwoordigt, door aan de `createElement` methode. De geretourneerde waarde omzetten in `Element`. Stel een waarde in voor de `PDFsFromBookmarks` element door zijn `setAttribute` methode. Voeg de `PDFsFromBookmarks` aan de `DDX` element door het element DDX te roepen `appendChild` methode. Geef de `PDFsFromBookmarks` elementobject als een argument. De volgende coderegels tonen deze toepassingslogica:

     ` Element PDFsFromBookmarks = (Element)document.createElement("PDFsFromBookmarks");  PDFsFromBookmarks.setAttribute("prefix","stmt");  root.appendChild(PDFsFromBookmarks);`

   * Een `PDF` element door het `Document` object `createElement` methode. Geef een tekenreekswaarde door die de naam van het element vertegenwoordigt. De geretourneerde waarde omzetten in `Element`. Stel een waarde in voor de `PDF` element door zijn `setAttribute` methode. Voeg de `PDF` aan de `PDFsFromBookmarks` element door het `PDFsFromBookmarks` element `appendChild` methode. Geef de `PDF` elementobject als een argument. Deze toepassingslogica wordt in de volgende coderegels getoond:

     ` Element PDF = (Element)document.createElement("PDF");  PDF.setAttribute("source","AssemblerResultPDF.pdf");  PDFsFromBookmarks.appendChild(PDF);`

1. Zet het DDX-document om.

   * Een `javax.xml.transform.Transformer` door het object aan te roepen `javax.xml.transform.Transformer` statisch object `newInstance` methode.
   * Een `Transformer` door het object aan te roepen `TransformerFactory` object `newTransformer` methode.
   * Een `ByteArrayOutputStream` object met behulp van de constructor.
   * Een `javax.xml.transform.dom.DOMSource` object met behulp van de constructor. Geef de `org.w3c.dom.Document` object dat het DDX-document vertegenwoordigt.
   * Een `javax.xml.transform.dom.DOMSource` object door de constructor ervan te gebruiken en de `ByteArrayOutputStream` object.
   * Java vullen `ByteArrayOutputStream` door het object aan te roepen `javax.xml.transform.Transformer` object `transform` methode. Geef de `javax.xml.transform.dom.DOMSource` en de `javax.xml.transform.stream.StreamResult` objecten.
   * Maak een bytearray en wijs de grootte van de array toe `ByteArrayOutputStream` object naar de bytearray.
   * De bytearray vullen door de `ByteArrayOutputStream` object `toByteArray` methode.
   * Een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en de bytearray door te geven.

1. Verwijs naar een document van de PDF om te demonteren.

   * Een `java.util.Map` object dat wordt gebruikt voor het opslaan van PDF-invoerdocumenten met behulp van een `HashMap` constructor.
   * Een `java.io.FileInputStream` -object door de constructor ervan te gebruiken en de locatie van het PDF-document door te geven om te demonteren.
   * Een `com.adobe.idp.Document` object. Geef de `java.io.FileInputStream` -object dat het PDF-document bevat dat moet worden gedemonteerd.
   * Een item toevoegen aan de `java.util.Map` object aanroepen `put` en het doorgeven van de volgende argumenten:

      * Een tekenreekswaarde die de sleutelnaam vertegenwoordigt. Deze waarde moet overeenkomen met de waarde van het PDF-bronelement dat is opgegeven in het DDX-document. (In het DDX-document dat dynamisch wordt gemaakt, wordt de waarde `AssemblerResultPDF.pdf`.)
      * A `com.adobe.idp.Document` -object dat het PDF-document bevat dat moet worden gedemonteerd.

1. Stel runtime-opties in.

   * Een `AssemblerOptionSpec` object dat uitvoeringsopties opslaat met de constructor ervan.
   * Stel runtime-opties in om aan uw bedrijfsvereisten te voldoen door een methode aan te roepen die tot de `AssemblerOptionSpec` object. Bijvoorbeeld, om de dienst van de Assembler op te dragen om een baan te blijven verwerken wanneer een fout voorkomt, haalt het `AssemblerOptionSpec` object `setFailOnError` methode en doorgeven `false`.

1. Haal het PDF-document uit elkaar.

   De `AssemblerServiceClient` object `invokeDDX` en geeft de volgende waarden door:

   * A `com.adobe.idp.Document` object dat het dynamisch gemaakte DDX-document vertegenwoordigt
   * A `java.util.Map` object dat het te demonteren PDF-document bevat
   * A `com.adobe.livecycle.assembler.client.AssemblerOptionSpec` object dat de runtime-opties opgeeft, inclusief het standaardfont en het taaklogniveau

   De `invokeDDX` methode retourneert een `com.adobe.livecycle.assembler.client.AssemblerResult` -object dat de gedemonteerde PDF-documenten en eventuele uitzonderingen bevat.

1. Sla de gedemonteerde PDF-documenten op.

   Voer de volgende handelingen uit om de gedemonteerde PDF-documenten te verkrijgen:

   * De `AssemblerResult` object `getDocuments` methode. Deze methode retourneert een `java.util.Map` object.
   * Doorlopen `java.util.Map` object tot u het resultaat hebt gevonden `com.adobe.idp.Document` object.
   * De `com.adobe.idp.Document` object `copyToFile` methode om het PDF-document te extraheren.

**Zie ook**

[Snel starten (SOAP-modus): dynamisch een DDX-document maken met de Java API](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-dynamically-creating-a-ddx-document-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Een DDX-document dynamisch maken met de webservice-API {#dynamically-create-a-ddx-document-using-the-web-service-api}

Maak dynamisch een DDX-document en demonstreer een PDF-document met behulp van de API (webservice) voor vergaderingsservice:

1. Inclusief projectbestanden.

   Creeer een Microsoft .NET project dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt wanneer het plaatsen van een de dienstverwijzing: `http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` met het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een PDF Assembler-client.

   * Een `AssemblerServiceClient` object met de standaardconstructor.
   * Een `AssemblerServiceClient.Endpoint.Address` object door het `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/AssemblerService?blob=mtom`). U hoeft de `lc_version` kenmerk. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.
   * Een `System.ServiceModel.BasicHttpBinding` object door de waarde van het object op te halen `AssemblerServiceClient.Endpoint.Binding` veld. De geretourneerde waarde omzetten in `BasicHttpBinding`.
   * Stel de `System.ServiceModel.BasicHttpBinding` object `MessageEncoding` veld naar `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld toe `AssemblerServiceClient.ClientCredentials.UserName.UserName`.
      * De bijbehorende wachtwoordwaarde aan het veld toewijzen `AssemblerServiceClient.ClientCredentials.UserName.Password`.
      * De constante waarde toewijzen `HttpClientCredentialType.Basic` naar het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * De constante waarde toewijzen `BasicHttpSecurityMode.TransportCredentialOnly` naar het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Maak het DDX-document.

   * Een `System.Xml.XmlElement` object met behulp van de constructor.
   * Maak het basiselement van het DDX-document door het `XmlElement` object `CreateElement` methode. Deze methode maakt een `Element` object dat het basiselement vertegenwoordigt. Geef een tekenreekswaarde die de naam van het element vertegenwoordigt, door aan de `CreateElement` methode. Plaats een waarde voor het element DDX door zijn te roepen `SetAttribute` methode. Tot slot voeg het element aan het DX- document toe door te roepen `XmlElement` object `AppendChild` methode. Geef het DDX-object door als een argument. De volgende coderegels tonen deze toepassingslogica:

     ` System.Xml.XmlElement root = ddx.CreateElement("DDX");  root.SetAttribute("xmlns", "https://ns.adobe.com/DDX/1.0/");  ddx.AppendChild(root);`

   * De DDX-documenten maken `PDFsFromBookmarks` element door het `XmlElement` object `CreateElement` methode. Geef een tekenreekswaarde die de naam van het element vertegenwoordigt, door aan de `CreateElement` methode. Stel vervolgens een waarde voor het element in door het element aan te roepen `SetAttribute` methode. Voeg de `PDFsFromBookmarks` element aan het wortelelement door te roepen `DDX` element `AppendChild` methode. Geef de `PDFsFromBookmarks` elementobject als een argument. De volgende coderegels tonen deze toepassingslogica:

     ` XmlElement PDFsFromBookmarks = ddx.CreateElement("PDFsFromBookmarks");  PDFsFromBookmarks.SetAttribute("prefix", "stmt");  root.AppendChild(PDFsFromBookmarks);`

   * De DDX-documenten maken `PDF` element door het `XmlElement` object `CreateElement` methode. Geef een tekenreekswaarde die de naam van het element vertegenwoordigt, door aan de `CreateElement` methode. Stel vervolgens een waarde in voor het onderliggende element door de bijbehorende `SetAttribute` methode. Voeg de `PDF` aan de `PDFsFromBookmarks` element door het `PDFsFromBookmarks` element `AppendChild` methode. Geef de `PDF` elementobject als een argument. Deze toepassingslogica wordt in de volgende coderegels getoond:

     ` XmlElement PDF = ddx.CreateElement("PDF");  PDF.SetAttribute("source", "AssemblerResultPDF.pdf");  PDFsFromBookmarks.AppendChild(PDF);`

1. Zet het DDX-document om.

   * Een `System.IO.MemoryStream` object met behulp van de constructor.
   * Vul de `MemoryStream` met het DDX-document `XmlElement` object dat het DDX-document vertegenwoordigt. De `XmlElement` object `Save` en geeft de `MemoryStream` object.
   * Een bytearray maken en deze vullen met gegevens in het dialoogvenster `MemoryStream` object. De volgende code toont deze toepassingslogica:

     ` int bufLen = Convert.ToInt32(stream.Length);  byte[] byteArray = new byte[bufLen];  stream.Position = 0;  int count = stream.Read(byteArray, 0, bufLen);`

   * Een `BLOB` object. Wijs de bytearray toe aan de `BLOB` object `MTOM` veld.

1. Verwijs naar een document van de PDF om te demonteren.

   * Een `BLOB` object met behulp van de constructor. De `BLOB` wordt gebruikt om het invoerdocument PDF op te slaan. Dit `BLOB` object wordt doorgegeven aan de `invokeOneDocument` als argument.
   * Een `System.IO.FileStream` object door de constructor ervan aan te roepen. Geef een tekenreekswaarde door die staat voor de bestandslocatie van het invoerdocument en de modus waarin het PDF-bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van de `System.IO.FileStream` object. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` object `Length` eigenschap.
   * De bytearray vullen met streamgegevens door de `System.IO.FileStream` object `Read` en geeft u de bytearray, de startpositie en de streamlengte door die u wilt lezen.
   * Vul de `BLOB` object door het toe te wijzen `MTOM` geeft de inhoud van de bytearray op.

1. Stel runtime-opties in.

   * Een `AssemblerOptionSpec` object dat uitvoeringsopties opslaat met de constructor ervan.
   * Stel runtime-opties in om aan uw bedrijfsvereisten te voldoen door een waarde toe te wijzen aan een gegevenslid dat tot de `AssemblerOptionSpec` object. Bijvoorbeeld, om de dienst van de Assembler op te dragen om een baan te blijven verwerken wanneer een fout voorkomt, wijs toe `false` aan de `AssemblerOptionSpec` object `failOnError` lid.

1. Haal het PDF-document uit elkaar.

   De `AssemblerServiceClient` object `invokeDDX` en geeft de volgende waarden door:

   * A `BLOB` object dat het dynamisch gemaakte DDX-document vertegenwoordigt
   * De `mapItem` array die het invoerdocument PDF bevat
   * An `AssemblerOptionSpec` object dat uitvoeringsopties opgeeft

   De `invokeDDX` methode retourneert een `AssemblerResult` object dat de resultaten van de taak en eventuele uitzonderingen bevat die zijn opgetreden.

1. Sla de gedemonteerde PDF-documenten op.

   Voer de volgende handelingen uit om de nieuwe PDF-documenten te verkrijgen:

   * Toegang krijgen tot de `AssemblerResult` object `documents` veld, dat een `Map` -object dat de gedemonteerde PDF-documenten bevat.
   * Doorlopen `Map` om elk resulterend document te verkrijgen. Dan, giet dat serielid `value` een `BLOB`.
   * Extraheer de binaire gegevens die het document van de PDF door tot zijn toegang te hebben vertegenwoordigen `BLOB` object `MTOM` eigenschap. Hiermee wordt een array met bytes geretourneerd die u naar een PDF-bestand kunt schrijven.

**Zie ook**

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)
