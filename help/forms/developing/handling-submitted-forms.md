---
title: Verzendde Forms afhandelen
description: Gebruik de Forms-service om de verzonden gegevens op te halen die in een interactief formulier zijn ingevoerd. De gebruiker kan de formuliergegevens verzenden in de indelingen XML, PDF en URL UTF-16.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
exl-id: 419335b2-2aae-4e83-98ff-18e61b7efa9c
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '2894'
ht-degree: 0%

---

# Verzendde Forms afhandelen {#handling-submitted-forms}

**Voorbeelden en voorbeelden in dit document gelden alleen voor AEM Forms in JEE-omgeving.**

Web-based toepassingen die een gebruiker toelaten om interactieve vormen in te vullen vereisen dat de gegevens terug naar de server worden voorgelegd. Met de Forms-service kunt u de gegevens ophalen die de gebruiker in een interactief formulier heeft ingevoerd. Nadat u de gegevens hebt opgehaald, kunt u de gegevens verwerken om aan uw bedrijfsvereisten te voldoen. U kunt de gegevens bijvoorbeeld opslaan in een database, de gegevens naar een andere toepassing verzenden, de gegevens naar een andere service verzenden, de gegevens in een formulierontwerp samenvoegen, de gegevens weergeven in een webbrowser, enzovoort.

Formuliergegevens worden naar de Forms-service verzonden als XML- of PDF-gegevens. Dit is een optie die is ingesteld in Designer. Met een formulier dat als XML wordt verzonden, kunt u afzonderlijke waarden van veldgegevens extraheren. Met andere woorden, u kunt de waarde extraheren van elk formulierveld dat de gebruiker in het formulier heeft ingevoerd. Een formulier dat wordt verzonden als PDF-gegevens, is binaire gegevens, niet XML-gegevens. U kunt het formulier opslaan als een PDF-bestand of het formulier verzenden naar een andere service. Als u gegevens wilt extraheren uit een formulier dat als XML is verzonden en vervolgens de formuliergegevens wilt gebruiken om een PDF-document te maken, roept u een andere AEM Forms-bewerking op. (Zie [PDF-documenten maken met verzonden XML-gegevens](/help/forms/developing/creating-pdf-documents-submitted-xml.md))

In het volgende diagram worden gegevens weergegeven die worden verzonden naar een Java-server met de naam `HandleData` van een interactief formulier dat wordt weergegeven in een webbrowser.

![hs_hs_handlesubmit](assets/hs_hs_handlesubmit.png)

De volgende lijst verklaart de stappen in het diagram.

<table>
 <thead>
  <tr>
   <th><p>Stap</p></th>
   <th><p>Beschrijving</p></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p>1</p></td>
   <td><p>Een gebruiker vult een interactief formulier in en klikt op de knop Verzenden van het formulier.</p></td>
  </tr>
  <tr>
   <td><p>2</p></td>
   <td><p>Gegevens worden ingediend bij de <code>HandleData</code> Java Server als XML-gegevens.</p></td>
  </tr>
  <tr>
   <td><p>3</p></td>
   <td><p>De <code>HandleData</code> Java Servlet bevat toepassingslogica om de gegevens op te halen.</p></td>
  </tr>
 </tbody>
</table>

## Verzonden XML-gegevens verwerken {#handling-submitted-xml-data}

Wanneer formuliergegevens als XML worden verzonden, kunt u XML-gegevens ophalen die de verzonden gegevens vertegenwoordigen. Alle formuliervelden worden weergegeven als knooppunten in een XML-schema. De knoopwaarden komen overeen met de waarden die de gebruiker heeft ingevuld. Neem bijvoorbeeld een leningformulier waarin elk veld in het formulier wordt weergegeven als een knooppunt in de XML-gegevens. De waarde van elk knooppunt komt overeen met de waarde die een gebruiker invult. Stel dat een gebruiker het leningformulier vult met gegevens die in het volgende formulier worden getoond.

![hs_hs_linformdata](assets/hs_hs_loanformdata.png)

In de volgende afbeelding ziet u de overeenkomstige XML-gegevens die zijn opgehaald met de Forms Service Client API.

![hs_hs_loandata](assets/hs_hs_loandata.png)

De velden in het leningformulier. Deze waarden kunnen worden opgehaald met Java XML-klassen.

>[!NOTE]
>
>Gegevens die als XML-gegevens moeten worden verzonden, moeten correct zijn geconfigureerd in Designer. Als u het formulierontwerp correct wilt configureren voor het verzenden van XML-gegevens, moet u ervoor zorgen dat de knop Verzenden die zich in het formulierontwerp bevindt, is ingesteld op het verzenden van XML-gegevens. Voor informatie over het instellen van de knop Verzenden voor het verzenden van XML-gegevens raadpleegt u [AEM Forms Designer](https://www.adobe.com/go/learn_aemforms_designer_63).

## Ingediende PDF-gegevens verwerken {#handling-submitted-pdf-data}

Neem bijvoorbeeld een webtoepassing die de Forms-service oproept. Nadat de Forms-service een interactief PDF-formulier heeft gerenderd naar een clientwebbrowser, vult de gebruiker het formulier in en verzendt het terug als PDF-gegevens. Wanneer de Forms-service de PDF-gegevens ontvangt, kunnen de PDF-gegevens naar een andere service worden verzonden of worden opgeslagen als een PDF-bestand. Het volgende diagram toont de logische stroom van de toepassing.

![hs_hs_savingformulieren](assets/hs_hs_savingforms.png)

In de volgende tabel worden de stappen in dit diagram beschreven.

<table>
 <thead>
  <tr>
   <th><p>Stap</p></th>
   <th><p>Beschrijving</p></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p>1</p></td>
   <td><p>Een webpagina bevat een koppeling die toegang krijgt tot een Java Servlet die de Forms-service aanroept.</p></td>
  </tr>
  <tr>
   <td><p>2</p></td>
   <td><p>De Forms-service geeft een interactief PDF-formulier weer aan de webbrowser van de client.</p></td>
  </tr>
  <tr>
   <td><p>3</p></td>
   <td><p>De gebruiker vult een interactief formulier in en klikt op een verzendknop. Het formulier wordt als PDF-gegevens teruggestuurd naar de Forms-service. Deze optie wordt ingesteld in Designer.</p></td>
  </tr>
  <tr>
   <td><p>4</p></td>
   <td><p>De Forms-service slaat de PDF-gegevens op als een PDF-bestand. </p></td>
  </tr>
 </tbody>
</table>

## Verzonden URL UTF-16-gegevens verwerken {#handling-submitted-url-utf-16-data}

Als formuliergegevens worden verzonden als UTF-16-URL-gegevens, vereist de clientcomputer Adobe Reader of Acrobat 8.1 of hoger. Als het formulierontwerp een verzendknop bevat met URL-gecodeerde gegevens (HTTP Post) en de optie voor gegevenscodering UTF-16 is, moet het formulierontwerp worden gewijzigd in een teksteditor, zoals Kladblok. U kunt de coderingsoptie instellen op `UTF-16LE` of `UTF-16BE` voor de verzendknop. Designer biedt deze functionaliteit niet.

>[!NOTE]
>
>Voor meer informatie over de Forms-service raadpleegt u [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Overzicht van de stappen {#summary-of-steps}

Voer de volgende taken uit om verzonden formulieren te verwerken:

1. Inclusief projectbestanden.
1. Maak een Forms Client API-object.
1. Formuliergegevens ophalen.
1. Bepaal of de formulierverzending bestandsbijlagen bevat.
1. Verwerk de verzonden gegevens.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

**Een Forms Client API-object maken**

Voordat u programmatisch een client-API-bewerking voor Forms-services kunt uitvoeren, moet u een Forms-serviceclient maken. Als u de Java API gebruikt, maakt u een `FormsServiceClient` object. Als u de Forms-webservice-API gebruikt, maakt u een `FormsService` object.

**Formuliergegevens ophalen**

Als u verzonden formuliergegevens wilt ophalen, roept u de `FormsServiceClient` object `processFormSubmission` methode. Wanneer u deze methode aanroept, moet u het inhoudstype van het verzonden formulier opgeven. Wanneer gegevens vanuit een clientwebbrowser naar de Forms-service worden verzonden, kunnen deze als XML- of PDF-gegevens worden verzonden. Om de gegevens op te halen die in formuliervelden zijn ingevoerd, kunnen de gegevens als XML-gegevens worden verzonden.

U kunt ook formuliervelden ophalen uit een formulier dat als PDF-gegevens wordt verzonden door de volgende runtime-opties in te stellen:

* Geef de volgende waarde door aan de `processFormSubmission` methode als parameter voor inhoudstype: `CONTENT_TYPE=application/pdf`.
* Stel de `RenderOptionsSpec` object `PDFToXDP` waarde aan `true`
* Stel de `RenderOptionsSpec` object `ExportDataFormat` waarde aan `XMLData`

U geeft het inhoudstype van het verzonden formulier op wanneer u het `processFormSubmission` methode. In de volgende lijst worden de toepasselijke waarden voor inhoudstypen aangegeven:

* **text/xml**: Vertegenwoordigt het inhoudstype dat moet worden gebruikt wanneer een PDF-formulier formuliergegevens als XML verzendt.
* **application/x-www-form-urlencoded**: Vertegenwoordigt het inhoudstype dat moet worden gebruikt wanneer een HTML-formulier gegevens als XML verzendt.
* **application/pdf**: Vertegenwoordigt het inhoudstype dat moet worden gebruikt wanneer een PDF-formulier gegevens verzendt als PDF.

>[!NOTE]
>
>Er zijn drie bijbehorende snelstarthandleidingen gekoppeld aan de sectie Verzendde Forms afhandelen. De PDF forms die worden verzonden als PDF met de Java API Quick start tonen aan hoe de verzonden PDF-gegevens moeten worden verwerkt. Het inhoudstype dat in deze snelle start wordt opgegeven, is `application/pdf`. De PDF forms die worden verzonden als XML met de snelle start van de Java API laten zien hoe de verzonden XML-gegevens worden verwerkt die worden verzonden vanuit een PDF-formulier. Het inhoudstype dat in deze snelle start wordt opgegeven, is `text/xml`. Op dezelfde manier tonen de HTML-formulieren voor verwerking die als XML worden verzonden met de snelle start van de Java API aan hoe de verzonden XML-gegevens die vanuit een HTML-formulier zijn verzonden, moeten worden afgehandeld. Het inhoudstype dat in deze snelle start wordt opgegeven, is application/x-www-form-urlencoded.

U haalt formuliergegevens op die naar de Forms-service zijn verzonden en bepaalt de verwerkingsstatus. Dat wil zeggen dat wanneer gegevens worden ingediend bij de Forms-dienst, dit niet noodzakelijkerwijs betekent dat de Forms-dienst de gegevens heeft verwerkt en dat de gegevens klaar zijn om te worden verwerkt. Gegevens kunnen bijvoorbeeld naar de Forms-service worden verzonden, zodat een berekening kan worden uitgevoerd. Wanneer de berekening is voltooid, wordt het formulier teruggestuurd naar de gebruiker met de weergegeven berekeningsresultaten. Voordat u verzonden gegevens verwerkt, wordt u aangeraden te bepalen of de Forms-service de gegevens heeft verwerkt.

De Forms-service retourneert de volgende waarden om aan te geven of de verwerking van de gegevens is voltooid:

* **0 (Verzenden):** De verzonden gegevens zijn klaar om te worden verwerkt.
* **1 (berekenen):** De Forms-service heeft een rekenbewerking uitgevoerd op de gegevens en de resultaten moeten worden teruggegeven aan de gebruiker.
* **2 (Valideren):** De door de Forms-service gevalideerde formuliergegevens en de resultaten moeten naar de gebruiker worden teruggestuurd.
* **3 (Volgende):** De huidige pagina is gewijzigd met resultaten die naar de clienttoepassing moeten worden geschreven.
* **4 (Vorige**): De huidige pagina is gewijzigd met resultaten die naar de clienttoepassing moeten worden geschreven.

>[!NOTE]
>
>Berekeningen en validaties moeten worden teruggegeven aan de gebruiker. (Zie [Formuliergegevens berekenen](/help/forms/developing/calculating-form-data.md#calculating-form-data).

**Bepalen of de formulierverzending bestandsbijlagen bevat**

Forms dat is verzonden naar de Forms-service kan bestandsbijlagen bevatten. Met het venster voor ingebouwde bijlagen van Acrobat kan een gebruiker bijvoorbeeld bestandsbijlagen selecteren die samen met het formulier moeten worden verzonden. Een gebruiker kan ook bestandsbijlagen selecteren met een HTML-werkbalk die wordt weergegeven met een HTML-bestand.

Nadat u hebt bepaald of een formulier bestandsbijlagen bevat, kunt u de gegevens verwerken. U kunt bijvoorbeeld de bestandsbijlage opslaan in het lokale bestandssysteem.

>[!NOTE]
>
>Het formulier moet worden verzonden als PDF-gegevens om bestandsbijlagen op te halen. Als het formulier wordt verzonden als XML-gegevens, worden bestandsbijlagen niet verzonden.

**De verzonden gegevens verwerken**

Afhankelijk van het inhoudstype van de verzonden gegevens, kunt u afzonderlijke formulierveldwaarden extraheren uit de verzonden XML-gegevens of de verzonden PDF-gegevens opslaan als een PDF-bestand (of deze naar een andere service verzenden). Als u afzonderlijke formuliervelden wilt extraheren, converteert u de ingediende XML-gegevens naar een XML-gegevensbron en haalt u vervolgens de XML-gegevensbronwaarden op met `org.w3c.dom` klassen.

**Zie ook**

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Forms Service API Quick Start](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

[Documenten doorgeven aan de Forms-service](/help/forms/developing/passing-documents-forms-service.md)

[Webtoepassingen maken die Forms renderen](/help/forms/developing/creating-web-applications-renders-forms.md)

## Ingevulde formulieren verwerken met de Java API {#handle-submitted-forms-using-the-java-api}

Een verzonden formulier verwerken met de Forms API (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden, zoals adobe-forms-client.jar, op in het klassenpad van uw Java-project.

1. Een Forms Client API-object maken

   * Een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Een `FormsServiceClient` object door de constructor ervan te gebruiken en de `ServiceClientFactory` object.

1. Formuliergegevens ophalen

   * Als u formuliergegevens wilt ophalen die naar een Java Server zijn gepost, maakt u een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en de `javax.servlet.http.HttpServletResponse` object `getInputStream` methode vanuit de constructor.
   * Een `RenderOptionsSpec` object met behulp van de constructor. Stel de waarde van de landinstelling in door de `RenderOptionsSpec` object `setLocale` en het doorgeven van een tekenreekswaarde die de waarde van de landinstelling opgeeft.

   >[!NOTE]
   >
   >U kunt de Forms-service opdragen om XDP- of XML-gegevens te maken van verzonden PDF-inhoud door het `RenderOptionsSpec` object `setPDF2XDP` methode en doorgeven `true` en tevens `setXMLData` en passeren `true`. Vervolgens kunt u de opdracht `FormsResult` object `getOutputXML` methode om de XML-gegevens op te halen die overeenkomen met de XDP/XML-gegevens. (De `FormsResult` object wordt geretourneerd door de `processFormSubmission` methode, die in de volgende substap wordt toegelicht.)

   * De `FormsServiceClient` object `processFormSubmission` en geeft de volgende waarden door:

      * De `com.adobe.idp.Document` object dat de formuliergegevens bevat.
      * Een tekenreekswaarde die omgevingsvariabelen opgeeft, inclusief alle relevante HTTP-headers. Geef het inhoudstype op dat u wilt afhandelen. Als u XML-gegevens wilt verwerken, geeft u de volgende tekenreekswaarde op voor deze parameter: `CONTENT_TYPE=text/xml`. Als u PDF-gegevens wilt verwerken, geeft u de volgende tekenreekswaarde op voor deze parameter: `CONTENT_TYPE=application/pdf`.
      * Een tekenreekswaarde die de `HTTP_USER_AGENT` headerwaarde, bijvoorbeeld . `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)`. Deze parameterwaarde is optioneel.
      * A `RenderOptionsSpec` -object dat uitvoeringsopties opslaat.

     De `processFormSubmission` methode retourneert een `FormsResult` object met de resultaten van het verzenden van het formulier.

   * Bepaal of de Forms-service de formuliergegevens heeft verwerkt door de `FormsResult` object `getAction` methode. Als deze methode de waarde retourneert `0`De gegevens zijn klaar om te worden verwerkt.

1. Bepalen of de formulierverzending bestandsbijlagen bevat

   * De `FormsResult` object `getAttachments` methode. Deze methode retourneert een `java.util.List` object dat bestanden bevat die met het formulier zijn verzonden.
   * Doorlopen `java.util.List` -object om te bepalen of er bestandsbijlagen zijn. Als er bestandsbijlagen zijn, is elk element een `com.adobe.idp.Document` -instantie. U kunt de bestandsbijlagen opslaan door de `com.adobe.idp.Document` object `copyToFile` methode en een `java.io.File` object.

   >[!NOTE]
   >
   >Deze stap is alleen van toepassing als het formulier wordt verzonden als PDF.

1. De verzonden gegevens verwerken

   * Als het gegevenstype van de gegevensinhoud `application/vnd.adobe.xdp+xml` of `text/xml`, maakt u toepassingslogica om XML-gegevenswaarden op te halen.

      * Een `com.adobe.idp.Document` door het object aan te roepen `FormsResult` object `getOutputContent` methode.
      * Een `java.io.InputStream` door het object aan te roepen `java.io.DataInputStream` aannemer en het overgaan van `com.adobe.idp.Document` object.
      * Een `org.w3c.dom.DocumentBuilderFactory` object door het statische object aan te roepen `org.w3c.dom.DocumentBuilderFactory` object `newInstance` methode.
      * Een `org.w3c.dom.DocumentBuilder` door het object aan te roepen `org.w3c.dom.DocumentBuilderFactory` object `newDocumentBuilder` methode.
      * Een `org.w3c.dom.Document` door het object aan te roepen `org.w3c.dom.DocumentBuilder` object `parse` en het doorgeven van de `java.io.InputStream` object.
      * Haal de waarde van elk knooppunt in het XML-document op. U kunt deze taak uitvoeren door een aangepaste methode te maken die twee parameters accepteert: de `org.w3c.dom.Document` -object en de naam van het knooppunt waarvan u de waarde wilt ophalen. Deze methode retourneert een tekenreekswaarde die de waarde van het knooppunt vertegenwoordigt. In het codevoorbeeld dat dit proces volgt, wordt deze douanemethode geroepen `getNodeText`. De hoofdtekst van deze methode wordt weergegeven.

   * Als het gegevenstype van de gegevensinhoud `application/pdf`, maakt u toepassingslogica om de verzonden PDF-gegevens op te slaan als een PDF-bestand.

      * Een `com.adobe.idp.Document` door het object aan te roepen `FormsResult` object `getOutputContent` methode.
      * Een `java.io.File` object met behulp van de openbare constructor. Zorg ervoor dat u PDF opgeeft als bestandsextensie.
      * Vul het PDF-bestand door het `com.adobe.idp.Document` object `copyToFile` en het doorgeven van de `java.io.File` object.

**Zie ook**

[Snel starten (SOAP-modus): PDF forms verwerken die als XML zijn verzonden met de Java API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-handling-pdf-forms-submitted-as-xml-using-the-java-api)

[Snel starten (SOAP-modus): HTML-formulieren verwerken die zijn verzonden als XML met de Java API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-handling-html-forms-submitted-as-xml-using-the-java-api)

[Snel starten (SOAP-modus): PDF forms verwerken die als PDF zijn verzonden met de Java API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-handling-pdf-forms-submitted-as-pdf-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Verzonden PDF-gegevens verwerken met de webservice-API {#handle-submitted-pdf-data-using-the-web-service-api}

Een verzonden formulier verwerken met de Forms API (webservice):

1. Projectbestanden opnemen

   * Maak Java-proxyklassen die gebruikmaken van de Forms-service WSDL.
   * Neem de Java-proxyklassen op in het klassepad.

1. Een Forms Client API-object maken

   Een `FormsService` -object en stel verificatiewaarden in.

1. Formuliergegevens ophalen

   * Als u formuliergegevens wilt ophalen die naar een Java Server zijn gepost, maakt u een `BLOB` object met behulp van de constructor.
   * Een `java.io.InputStream` door het object aan te roepen `javax.servlet.http.HttpServletResponse` object `getInputStream` methode.
   * Een `java.io.ByteArrayOutputStream` object door de constructor ervan te gebruiken en de lengte van het object door te geven `java.io.InputStream` object.
   * Kopieer de inhoud van het dialoogvenster `java.io.InputStream` in het `java.io.ByteArrayOutputStream` object.
   * Maak een bytearray door de `java.io.ByteArrayOutputStream` object `toByteArray` methode.
   * Vul de `BLOB` object aanroepen `setBinaryData` en de bytearray doorgeven als een argument.
   * Een `RenderOptionsSpec` object met behulp van de constructor. Stel de waarde van de landinstelling in door de `RenderOptionsSpec` object `setLocale` en het doorgeven van een tekenreekswaarde die de waarde van de landinstelling opgeeft.
   * De `FormsService` object `processFormSubmission` en geeft de volgende waarden door:

      * De `BLOB` object dat de formuliergegevens bevat.
      * Een tekenreekswaarde die omgevingsvariabelen opgeeft, inclusief alle relevante HTTP-headers. Geef het inhoudstype op dat u wilt afhandelen. Als u XML-gegevens wilt verwerken, geeft u de volgende tekenreekswaarde op voor deze parameter: `CONTENT_TYPE=text/xml`. Als u PDF-gegevens wilt verwerken, geeft u de volgende tekenreekswaarde op voor deze parameter: `CONTENT_TYPE=application/pdf`.
      * Een tekenreekswaarde die de `HTTP_USER_AGENT` koptekstwaarde, bijvoorbeeld `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)`.
      * A `RenderOptionsSpec` -object dat uitvoeringsopties opslaat.
      * Een leeg `BLOBHolder` object dat door de methode wordt gevuld.
      * Een leeg `javax.xml.rpc.holders.StringHolder` object dat door de methode wordt gevuld.
      * Een leeg `BLOBHolder` object dat door de methode wordt gevuld.
      * Een leeg `BLOBHolder` object dat door de methode wordt gevuld.
      * Een leeg `javax.xml.rpc.holders.ShortHolder` object dat door de methode wordt gevuld.
      * Een leeg `MyArrayOf_xsd_anyTypeHolder` object dat door de methode wordt gevuld. Met deze parameter worden bestandsbijlagen opgeslagen die samen met het formulier worden verzonden.
      * Een leeg `FormsResultHolder` object dat door de methode is gevuld met het formulier dat wordt verzonden.

     De `processFormSubmission` wordt de `FormsResultHolder` met de resultaten van het verzenden van het formulier.

   * Bepaal of de Forms-service de formuliergegevens heeft verwerkt door de `FormsResult` object `getAction` methode. Als deze methode de waarde retourneert `0`, zijn de formuliergegevens klaar om te worden verwerkt. U kunt een `FormsResult` object door de waarde van het object op te halen `FormsResultHolder` object `value` lid.

1. Bepalen of de formulierverzending bestandsbijlagen bevat

   Hiermee wordt de waarde van de opdracht `MyArrayOf_xsd_anyTypeHolder` object `value` lid van de gegevens (de `MyArrayOf_xsd_anyTypeHolder` object is doorgegeven aan de `processFormSubmission` methode). Dit gegevenslid retourneert een array van `Objects`. Elk element binnen de `Object` array is een `Object`dat overeenkomt met de dossiers die samen met het formulier zijn ingediend. U kunt elk element binnen de serie krijgen en het gieten aan een `BLOB` object.

1. De verzonden gegevens verwerken

   * Als het gegevenstype van de gegevensinhoud `application/vnd.adobe.xdp+xml` of `text/xml`, maakt u toepassingslogica om XML-gegevenswaarden op te halen.

      * Een `BLOB` door het object aan te roepen `FormsResult` object `getOutputContent` methode.
      * Maak een bytearray door de `BLOB` object `getBinaryData` methode.
      * Een `java.io.InputStream` door het object aan te roepen `java.io.ByteArrayInputStream` en de bytearray doorgeven.
      * Een `org.w3c.dom.DocumentBuilderFactory` object door het statische object aan te roepen `org.w3c.dom.DocumentBuilderFactory` object `newInstance` methode.
      * Een `org.w3c.dom.DocumentBuilder` door het object aan te roepen `org.w3c.dom.DocumentBuilderFactory` object `newDocumentBuilder` methode.
      * Een `org.w3c.dom.Document` door het object aan te roepen `org.w3c.dom.DocumentBuilder` object `parse` en het doorgeven van de `java.io.InputStream` object.
      * Haal de waarde van elk knooppunt in het XML-document op. U kunt deze taak uitvoeren door een aangepaste methode te maken die twee parameters accepteert: de `org.w3c.dom.Document` -object en de naam van het knooppunt waarvan u de waarde wilt ophalen. Deze methode retourneert een tekenreekswaarde die de waarde van het knooppunt vertegenwoordigt. In het codevoorbeeld dat dit proces volgt, wordt deze douanemethode geroepen `getNodeText`. De hoofdtekst van deze methode wordt weergegeven.

   * Als het gegevenstype van de gegevensinhoud `application/pdf`, maakt u toepassingslogica om de verzonden PDF-gegevens op te slaan als een PDF-bestand.

      * Een `BLOB` door het object aan te roepen `FormsResult` object `getOutputContent` methode.
      * Maak een bytearray door de `BLOB` object `getBinaryData` methode.
      * Een `java.io.File` object met behulp van de openbare constructor. Zorg ervoor dat u PDF opgeeft als bestandsextensie.
      * Een `java.io.FileOutputStream` object door de constructor ervan te gebruiken en de `java.io.File` object.
      * Vul het PDF-bestand door het `java.io.FileOutputStream` object `write` en geeft u de bytearray door.

**Zie ook**

[AEM Forms aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
