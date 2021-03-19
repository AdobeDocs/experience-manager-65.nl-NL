---
title: Verzendde Forms afhandelen
seo-title: Verzendde Forms afhandelen
description: Gebruik de Forms-service om de verzonden gegevens op te halen die in een interactief formulier zijn ingevoerd. De gebruiker kan de formuliergegevens verzenden in de indelingen XML, PDF en URL UTF-16.
seo-description: Gebruik de Forms-service om de verzonden gegevens op te halen die in een interactief formulier zijn ingevoerd. De gebruiker kan de formuliergegevens verzenden in de indelingen XML, PDF en URL UTF-16.
uuid: 673b28f1-f023-4da8-a6a0-c5ff921c5f5d
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 3d838027-6bde-4a71-a428-4d5102f7d799
role: Developer
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '2936'
ht-degree: 0%

---


# Verzendde Forms {#handling-submitted-forms} verwerken

**Voorbeelden en voorbeelden in dit document gelden alleen voor AEM Forms in JEE-omgeving.**

Web-based toepassingen die een gebruiker toelaten om interactieve vormen in te vullen vereisen dat de gegevens terug naar de server worden voorgelegd. Met de Forms-service kunt u de gegevens ophalen die de gebruiker in een interactief formulier heeft ingevoerd. Nadat u de gegevens hebt opgehaald, kunt u de gegevens verwerken om aan uw bedrijfsvereisten te voldoen. U kunt de gegevens bijvoorbeeld opslaan in een database, de gegevens naar een andere toepassing verzenden, de gegevens naar een andere service verzenden, de gegevens in een formulierontwerp samenvoegen, de gegevens weergeven in een webbrowser, enzovoort.

Formuliergegevens worden naar de Forms-service verzonden als XML- of PDF-gegevens. Dit is een optie die is ingesteld in Designer. Met een formulier dat als XML wordt verzonden, kunt u afzonderlijke waarden van veldgegevens extraheren. Met andere woorden, u kunt de waarde extraheren van elk formulierveld dat de gebruiker in het formulier heeft ingevoerd. Een formulier dat als PDF-gegevens wordt verzonden, is binaire gegevens, niet XML-gegevens. U kunt het formulier opslaan als PDF-bestand of het formulier naar een andere service verzenden. Als u gegevens wilt extraheren uit een formulier dat als XML is verzonden en vervolgens de formuliergegevens wilt gebruiken om een PDF-document te maken, roept u een andere AEM Forms-bewerking op. (Zie [PDF-documenten maken met verzonden XML-gegevens](/help/forms/developing/creating-pdf-documents-submitted-xml.md))

In het volgende diagram worden gegevens weergegeven die vanuit een interactief formulier in een webbrowser worden verzonden naar een Java-server met de naam `HandleData`.

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
   <td><p>Gegevens worden als XML-gegevens verzonden naar de Java Server <code>HandleData</code>.</p></td>
  </tr>
  <tr>
   <td><p>3</p></td>
   <td><p>De Java Server <code>HandleData</code> bevat toepassingslogica om de gegevens op te halen.</p></td>
  </tr>
 </tbody>
</table>

## Ingediende XML-gegevens {#handling-submitted-xml-data} verwerken

Wanneer formuliergegevens als XML worden verzonden, kunt u XML-gegevens ophalen die de verzonden gegevens vertegenwoordigen. Alle formuliervelden worden weergegeven als knooppunten in een XML-schema. De knoopwaarden komen overeen met de waarden die de gebruiker heeft ingevuld. Neem bijvoorbeeld een leningformulier waarin elk veld in het formulier wordt weergegeven als een knooppunt in de XML-gegevens. De waarde van elk knooppunt komt overeen met de waarde die een gebruiker invult. Stel dat een gebruiker het leningformulier vult met gegevens die in het volgende formulier worden getoond.

![hs_hs_linformdata](assets/hs_hs_loanformdata.png)

In de volgende afbeelding ziet u de overeenkomstige XML-gegevens die zijn opgehaald met de Forms Service Client API.

![hs_hs_loandata](assets/hs_hs_loandata.png)

De velden in het leningformulier. Deze waarden kunnen worden opgehaald
Java XML-klassen gebruiken.

>[!NOTE]
>
>Gegevens die als XML-gegevens moeten worden verzonden, moeten correct zijn geconfigureerd in Designer. Als u het formulierontwerp correct wilt configureren voor het verzenden van XML-gegevens, moet u ervoor zorgen dat de knop Verzenden die zich in het formulierontwerp bevindt, is ingesteld op het verzenden van XML-gegevens. Zie [AEM Forms Designer](https://www.adobe.com/go/learn_aemforms_designer_63) voor informatie over het instellen van de knop Verzenden om XML-gegevens te verzenden.

## Verzonden PDF-gegevens {#handling-submitted-pdf-data} verwerken

Neem bijvoorbeeld een webtoepassing die de Forms-service oproept. Nadat de Forms-service een interactief PDF-formulier heeft gerenderd naar een webbrowser van de client, vult de gebruiker het formulier in en verzendt het als PDF-gegevens. Wanneer de Forms-service de PDF-gegevens ontvangt, kan deze de PDF-gegevens naar een andere service verzenden of als PDF-bestand opslaan. Het volgende diagram toont de logische stroom van de toepassing.

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
   <td><p>3</p></td>
   <td><p>Een webpagina bevat een koppeling die toegang krijgt tot een Java Servlet die de Forms-service aanroept.</p></td>
  </tr>
  <tr>
   <td><p>2</p></td>
   <td><p>De Forms-service geeft een interactief PDF-formulier weer aan de webbrowser van de client.</p></td>
  </tr>
  <tr>
   <td><p>1</p></td>
   <td><p>De gebruiker vult een interactief formulier in en klikt op een verzendknop. Het formulier wordt als PDF-gegevens teruggestuurd naar de Forms-service. Deze optie wordt ingesteld in Designer.</p></td>
  </tr>
  <tr>
   <td><p>4</p></td>
   <td><p>De Forms-service slaat de PDF-gegevens op als een PDF-bestand. </p></td>
  </tr>
 </tbody>
</table>

## Behandeling verzonden URL UTF-16-gegevens {#handling-submitted-url-utf-16-data}

Als formuliergegevens worden verzonden als UTF-16-URL-gegevens, vereist de clientcomputer Adobe Reader of Acrobat 8.1 of hoger. Als het formulierontwerp een verzendknop bevat met URL-gecodeerde gegevens (HTTP Post) en de optie voor gegevenscodering UTF-16 is, moet het formulierontwerp worden gewijzigd in een teksteditor, zoals Kladblok. U kunt de coderingsoptie instellen op `UTF-16LE` of `UTF-16BE` voor de verzendknop. Designer biedt deze functionaliteit niet.

>[!NOTE]
>
>Zie [Referentiehandleiding voor services voor AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63) voor meer informatie over de Forms-service.

## Overzicht van stappen {#summary-of-steps}

Voer de volgende taken uit om verzonden formulieren te verwerken:

1. Inclusief projectbestanden.
1. Maak een Forms Client API-object.
1. Formuliergegevens ophalen.
1. Bepaal of de formulierverzending bestandsbijlagen bevat.
1. Verwerk de verzonden gegevens.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

**Een Forms Client API-object maken**

Voordat u programmatisch een client-API-bewerking voor Forms-services kunt uitvoeren, moet u een Forms-serviceclient maken. Als u de Java API gebruikt, maakt u een `FormsServiceClient`-object. Als u de Forms-API voor webservices gebruikt, maakt u een `FormsService`-object.

**Formuliergegevens ophalen**

Als u verzonden formuliergegevens wilt ophalen, roept u de methode `processFormSubmission` van het object `FormsServiceClient` aan. Wanneer u deze methode aanroept, moet u het inhoudstype van het verzonden formulier opgeven. Wanneer gegevens vanuit een clientwebbrowser naar de Forms-service worden verzonden, kunnen deze als XML- of PDF-gegevens worden verzonden. Om de gegevens op te halen die in formuliervelden zijn ingevoerd, kunnen de gegevens als XML-gegevens worden verzonden.

U kunt ook formuliervelden ophalen uit een formulier dat als PDF-gegevens is verzonden door de volgende runtime-opties in te stellen:

* Geef de volgende waarde aan de methode `processFormSubmission` als parameter van het inhoudstype door: `CONTENT_TYPE=application/pdf`.
* Stel de `RenderOptionsSpec`-waarde van het object `PDFToXDP` in op `true`
* Stel de `RenderOptionsSpec`-waarde van het object `ExportDataFormat` in op `XMLData`

U geeft het inhoudstype van het verzonden formulier op wanneer u de methode `processFormSubmission` aanroept. In de volgende lijst worden de toepasselijke waarden voor inhoudstypen aangegeven:

* **text/xml**: Het inhoudstype dat wordt gebruikt wanneer een PDF-formulier formuliergegevens als XML verzendt.
* **application/x-www-form-urlencoded**: Vertegenwoordigt het inhoudstype dat moet worden gebruikt wanneer een HTML-formulier gegevens als XML verzendt.
* **application/pdf**: Vertegenwoordigt het inhoudstype dat moet worden gebruikt wanneer een PDF-formulier gegevens als PDF verzendt.

>[!NOTE]
>
>Er zijn drie bijbehorende snelstarthandleidingen gekoppeld aan de sectie Verzendde Forms afhandelen. De PDF forms voor verwerking die met de Java API-snelstarthandleiding als PDF zijn verzonden, tonen aan hoe verzonden PDF-gegevens moeten worden verwerkt. Het inhoudstype dat in deze snelle start wordt opgegeven, is `application/pdf`. De PDF forms voor verwerking die als XML worden verzonden met de Java API Quick start tonen aan hoe de verzonden XML-gegevens die vanuit een PDF-formulier worden verzonden, moeten worden verwerkt. Het inhoudstype dat in deze snelle start wordt opgegeven, is `text/xml`. Op dezelfde manier wordt met de snelle start van de Java API getoond hoe de verzonden HTML-formulieren die zijn verzonden als XML worden verwerkt. Deze bewerking laat zien hoe de verzonden XML-gegevens die zijn verzonden vanuit een HTML-formulier, worden verwerkt. Het inhoudstype dat in deze snelle start wordt opgegeven, is application/x-www-form-urlencoded.

U haalt formuliergegevens op die naar de Forms-service zijn verzonden en bepaalt de verwerkingsstatus. Dat wil zeggen dat wanneer gegevens worden ingediend bij de Forms-dienst, dit niet noodzakelijkerwijs betekent dat de Forms-dienst de gegevens heeft verwerkt en dat de gegevens klaar zijn om te worden verwerkt. Gegevens kunnen bijvoorbeeld naar de Forms-service worden verzonden, zodat een berekening kan worden uitgevoerd. Wanneer de berekening is voltooid, wordt het formulier teruggestuurd naar de gebruiker met de weergegeven berekeningsresultaten. Voordat u verzonden gegevens verwerkt, wordt u aangeraden te bepalen of de Forms-service de gegevens heeft verwerkt.

De Forms-service retourneert de volgende waarden om aan te geven of de verwerking van de gegevens is voltooid:

* **0 (Verzenden):** verzonden gegevens kunnen worden verwerkt.
* **1 (Berekenen):** De Forms-service heeft een rekenbewerking uitgevoerd op de gegevens en de resultaten moeten worden teruggegeven aan de gebruiker.
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

Afhankelijk van het inhoudstype van de verzonden gegevens, kunt u afzonderlijke formulierveldwaarden extraheren uit de verzonden XML-gegevens of de verzonden PDF-gegevens opslaan als een PDF-bestand (of deze naar een andere service verzenden). Als u afzonderlijke formuliervelden wilt extraheren, converteert u de ingediende XML-gegevens naar een XML-gegevensbron en haalt u vervolgens de XML-gegevensbronwaarden op met de klassen `org.w3c.dom`.

**Zie ook**

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Forms Service API Quick Start](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

[Documenten doorgeven aan de Forms-service](/help/forms/developing/passing-documents-forms-service.md)

[Webtoepassingen maken die Forms renderen](/help/forms/developing/creating-web-applications-renders-forms.md)

## Verzonden formulieren verwerken met de Java API {#handle-submitted-forms-using-the-java-api}

Een verzonden formulier verwerken met de Forms API (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden, zoals adobe-forms-client.jar, op in het klassenpad van uw Java-project.

1. Een Forms Client API-object maken

   * Maak een `ServiceClientFactory`-object dat verbindingseigenschappen bevat.
   * Maak een `FormsServiceClient`-object door de constructor ervan te gebruiken en het object `ServiceClientFactory` door te geven.

1. Formuliergegevens ophalen

   * Als u formuliergegevens wilt ophalen die naar een Java Server zijn gepost, maakt u een `com.adobe.idp.Document`-object met de constructor ervan en roept u vanuit de constructor de methode `javax.servlet.http.HttpServletResponse` van het object `getInputStream` aan.
   * Maak een `RenderOptionsSpec`-object met de constructor ervan. Stel de waarde van de landinstelling in door de methode `setLocale` van het object `RenderOptionsSpec` aan te roepen en een tekenreekswaarde door te geven die de waarde van de landinstelling opgeeft.

   >[!NOTE]
   >
   >U kunt de Forms-service de instructie geven XDP- of XML-gegevens te maken van verzonden PDF-inhoud door de methode `RenderOptionsSpec` van het object `setPDF2XDP` aan te roepen en `true` door te geven en `setXMLData` en `true` door te geven. Vervolgens kunt u de methode `FormsResult` van het object `getOutputXML` aanroepen om de XML-gegevens op te halen die overeenkomen met de XDP/XML-gegevens. (Het object `FormsResult` wordt geretourneerd door de methode `processFormSubmission`, die in de volgende substap wordt beschreven.)

   * Roep de methode `processFormSubmission` van het object `FormsServiceClient` aan en geef de volgende waarden door:

      * Het object `com.adobe.idp.Document` dat de formuliergegevens bevat.
      * Een tekenreekswaarde die omgevingsvariabelen opgeeft, inclusief alle relevante HTTP-headers. Geef het inhoudstype op dat u wilt afhandelen. Als u XML-gegevens wilt verwerken, geeft u de volgende tekenreekswaarde op voor deze parameter: `CONTENT_TYPE=text/xml`. Als u PDF-gegevens wilt verwerken, geeft u de volgende tekenreekswaarde op voor deze parameter: `CONTENT_TYPE=application/pdf`.
      * Een tekenreekswaarde die bijvoorbeeld de koptekstwaarde `HTTP_USER_AGENT` opgeeft. `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)`. Deze parameterwaarde is optioneel.
      * Een `RenderOptionsSpec`-object dat uitvoeringsopties opslaat.

      De methode `processFormSubmission` retourneert een `FormsResult`-object dat de resultaten van het verzenden van het formulier bevat.

   * Bepaal of de Forms-service de formuliergegevens heeft verwerkt door de methode `getAction` van het object `FormsResult` aan te roepen. Als deze methode de waarde `0` retourneert, zijn de gegevens klaar om te worden verwerkt.



1. Bepalen of de formulierverzending bestandsbijlagen bevat

   * Roep de methode `FormsResult` van het object `getAttachments` aan. Deze methode retourneert een `java.util.List`-object dat bestanden bevat die met het formulier zijn verzonden.
   * Doorloop het object `java.util.List` om te bepalen of er bestandsbijlagen zijn. Als er dossiergehechtheid zijn, is elk element een `com.adobe.idp.Document` instantie. U kunt de bestandsbijlagen opslaan door de methode `copyToFile` van het object `com.adobe.idp.Document` aan te roepen en een object `java.io.File` door te geven.

   >[!NOTE]
   >
   >Deze stap is alleen van toepassing als het formulier als PDF is verzonden.

1. De verzonden gegevens verwerken

   * Als het gegevenstype `application/vnd.adobe.xdp+xml` of `text/xml` is, maakt u toepassingslogica om XML-gegevenswaarden op te halen.

      * Maak een `com.adobe.idp.Document`-object door de methode `getOutputContent` van het object `FormsResult` aan te roepen.
      * Maak een `java.io.InputStream`-object door de constructor `java.io.DataInputStream` aan te roepen en het object `com.adobe.idp.Document` door te geven.
      * Maak een `org.w3c.dom.DocumentBuilderFactory`-object door de methode `newInstance` van het statische object aan te roepen.`org.w3c.dom.DocumentBuilderFactory`
      * Maak een `org.w3c.dom.DocumentBuilder`-object door de methode `newDocumentBuilder` van het object `org.w3c.dom.DocumentBuilderFactory` aan te roepen.
      * Maak een `org.w3c.dom.Document`-object door de methode `parse` van het object `org.w3c.dom.DocumentBuilder` aan te roepen en het object `java.io.InputStream` door te geven.
      * Hiermee wordt de waarde van elk knooppunt in het XML-document opgehaald. U kunt deze taak uitvoeren door een aangepaste methode te maken die twee parameters accepteert: het object `org.w3c.dom.Document` en de naam van het knooppunt waarvan u de waarde wilt ophalen. Deze methode retourneert een tekenreekswaarde die de waarde van het knooppunt vertegenwoordigt. In het codevoorbeeld dat dit proces volgt, wordt deze douanemethode genoemd `getNodeText`. De hoofdtekst van deze methode wordt weergegeven.
   * Als het gegevenstype `application/pdf` is, maakt u toepassingslogica om de verzonden PDF-gegevens op te slaan als een PDF-bestand.

      * Maak een `com.adobe.idp.Document`-object door de methode `getOutputContent` van het object `FormsResult` aan te roepen.
      * Maak een `java.io.File`-object met behulp van de openbare constructor. Geef PDF op als bestandsnaamextensie.
      * Vul het PDF-bestand door de methode `copyToFile` van het object `com.adobe.idp.Document` aan te roepen en het object `java.io.File` door te geven.


**Zie ook**

[Snel starten (SOAP-modus): PDF forms die als XML zijn verzonden, afhandelen met de Java API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-handling-pdf-forms-submitted-as-xml-using-the-java-api)

[Snel starten (SOAP-modus): HTML-formulieren verwerken die zijn verzonden als XML met de Java API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-handling-html-forms-submitted-as-xml-using-the-java-api)

[Snel starten (SOAP-modus): PDF forms die als PDF zijn verzonden, verwerken met de Java API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-handling-pdf-forms-submitted-as-pdf-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Verzonden PDF-gegevens verwerken met de webservice-API {#handle-submitted-pdf-data-using-the-web-service-api}

Een verzonden formulier verwerken met de Forms API (webservice):

1. Projectbestanden opnemen

   * Maak Java-proxyklassen die gebruikmaken van de Forms-service WSDL.
   * Neem de Java-proxyklassen op in het klassepad.

1. Een Forms Client API-object maken

   Maak een `FormsService`-object en stel de verificatiewaarden in.

1. Formuliergegevens ophalen

   * Als u formuliergegevens wilt ophalen die naar een Java Server zijn gepost, maakt u een `BLOB`-object met de bijbehorende constructor.
   * Maak een `java.io.InputStream`-object door de methode `getInputStream` van het object `javax.servlet.http.HttpServletResponse` aan te roepen.
   * Maak een `java.io.ByteArrayOutputStream`-object door de constructor ervan te gebruiken en de lengte van het object `java.io.InputStream` door te geven.
   * Kopieer de inhoud van het object `java.io.InputStream` naar het object `java.io.ByteArrayOutputStream`.
   * Maak een bytearray door de methode `toByteArray` van het object `java.io.ByteArrayOutputStream` aan te roepen.
   * Vul het object `BLOB` door de methode `setBinaryData` ervan aan te roepen en de bytearray als een argument door te geven.
   * Maak een `RenderOptionsSpec`-object met de constructor ervan. Stel de waarde van de landinstelling in door de methode `setLocale` van het object `RenderOptionsSpec` aan te roepen en een tekenreekswaarde door te geven die de waarde van de landinstelling opgeeft.
   * Roep de methode `processFormSubmission` van het object `FormsService` aan en geef de volgende waarden door:

      * Het object `BLOB` dat de formuliergegevens bevat.
      * Een tekenreekswaarde die omgevingsvariabelen opgeeft, inclusief alle relevante HTTP-headers. Geef het inhoudstype op dat u wilt afhandelen. Als u XML-gegevens wilt verwerken, geeft u de volgende tekenreekswaarde op voor deze parameter: `CONTENT_TYPE=text/xml`. Als u PDF-gegevens wilt verwerken, geeft u de volgende tekenreekswaarde op voor deze parameter: `CONTENT_TYPE=application/pdf`.
      * Een tekenreekswaarde die de koptekstwaarde `HTTP_USER_AGENT` opgeeft; bijvoorbeeld `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)`.
      * Een `RenderOptionsSpec`-object dat uitvoeringsopties opslaat.
      * Een leeg object `BLOBHolder` dat door de methode is gevuld.
      * Een leeg object `javax.xml.rpc.holders.StringHolder` dat door de methode is gevuld.
      * Een leeg object `BLOBHolder` dat door de methode is gevuld.
      * Een leeg object `BLOBHolder` dat door de methode is gevuld.
      * Een leeg object `javax.xml.rpc.holders.ShortHolder` dat door de methode is gevuld.
      * Een leeg object `MyArrayOf_xsd_anyTypeHolder` dat door de methode is gevuld. Met deze parameter worden bestandsbijlagen opgeslagen die samen met het formulier worden verzonden.
      * Een leeg `FormsResultHolder`-object dat door de methode wordt gevuld met het formulier dat wordt verzonden.

      Met de methode `processFormSubmission` wordt de parameter `FormsResultHolder` gevuld met de resultaten van het verzenden van het formulier.

   * Bepaal of de Forms-service de formuliergegevens heeft verwerkt door de methode `getAction` van het object `FormsResult` aan te roepen. Als deze methode de waarde `0` retourneert, kunnen de formuliergegevens worden verwerkt. U kunt een `FormsResult` voorwerp krijgen door de waarde van `FormsResultHolder` te krijgen van het `value` gegevenslid van het voorwerp.


1. Bepalen of de formulierverzending bestandsbijlagen bevat

   Hiermee wordt de waarde opgehaald van het `MyArrayOf_xsd_anyTypeHolder`-gegevenslid van het `value`-object (het `MyArrayOf_xsd_anyTypeHolder`-object is doorgegeven aan de methode `processFormSubmission`). Dit gegevenslid retourneert een array van `Objects`. Elk element in de `Object`-array is een `Object`element dat overeenkomt met de bestanden die samen met het formulier zijn verzonden. U kunt elk element binnen de serie krijgen en het gieten aan een `BLOB` voorwerp.

1. De verzonden gegevens verwerken

   * Als het gegevenstype `application/vnd.adobe.xdp+xml` of `text/xml` is, maakt u toepassingslogica om XML-gegevenswaarden op te halen.

      * Maak een `BLOB`-object door de methode `getOutputContent` van het object `FormsResult` aan te roepen.
      * Maak een bytearray door de methode `getBinaryData` van het object `BLOB` aan te roepen.
      * Maak een `java.io.InputStream`-object door de constructor `java.io.ByteArrayInputStream` aan te roepen en de bytearray door te geven.
      * Maak een `org.w3c.dom.DocumentBuilderFactory`-object door de methode `newInstance` van het statische object aan te roepen.`org.w3c.dom.DocumentBuilderFactory`
      * Maak een `org.w3c.dom.DocumentBuilder`-object door de methode `newDocumentBuilder` van het object `org.w3c.dom.DocumentBuilderFactory` aan te roepen.
      * Maak een `org.w3c.dom.Document`-object door de methode `parse` van het object `org.w3c.dom.DocumentBuilder` aan te roepen en het object `java.io.InputStream` door te geven.
      * Hiermee wordt de waarde van elk knooppunt in het XML-document opgehaald. U kunt deze taak uitvoeren door een aangepaste methode te maken die twee parameters accepteert: het object `org.w3c.dom.Document` en de naam van het knooppunt waarvan u de waarde wilt ophalen. Deze methode retourneert een tekenreekswaarde die de waarde van het knooppunt vertegenwoordigt. In het codevoorbeeld dat dit proces volgt, wordt deze douanemethode genoemd `getNodeText`. De hoofdtekst van deze methode wordt weergegeven.
   * Als het gegevenstype `application/pdf` is, maakt u toepassingslogica om de verzonden PDF-gegevens op te slaan als een PDF-bestand.

      * Maak een `BLOB`-object door de methode `getOutputContent` van het object `FormsResult` aan te roepen.
      * Maak een bytearray door de methode `getBinaryData` van het object `BLOB` aan te roepen.
      * Maak een `java.io.File`-object met behulp van de openbare constructor. Geef PDF op als bestandsnaamextensie.
      * Maak een `java.io.FileOutputStream`-object door de constructor ervan te gebruiken en het object `java.io.File` door te geven.
      * Vul het PDF-bestand door de methode `write` van het object `java.io.FileOutputStream` aan te roepen en de bytearray door te geven.


**Zie ook**

[AEM Forms aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)