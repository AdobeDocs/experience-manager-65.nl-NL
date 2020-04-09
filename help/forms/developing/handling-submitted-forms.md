---
title: Ingediende formulieren verwerken
seo-title: Ingediende formulieren verwerken
description: 'null'
seo-description: 'null'
uuid: 673b28f1-f023-4da8-a6a0-c5ff921c5f5d
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 3d838027-6bde-4a71-a428-4d5102f7d799
translation-type: tm+mt
source-git-commit: b97452eb42275d889a82eb9364b5daf7075fcc41

---


# Ingediende formulieren verwerken {#handling-submitted-forms}

Web-based toepassingen die een gebruiker toelaten om interactieve vormen in te vullen vereisen dat de gegevens terug naar de server worden voorgelegd. Met de Forms-service kunt u de gegevens ophalen die de gebruiker in een interactief formulier heeft ingevoerd. Nadat u de gegevens hebt opgehaald, kunt u de gegevens verwerken om aan uw bedrijfsvereisten te voldoen. U kunt de gegevens bijvoorbeeld opslaan in een database, de gegevens naar een andere toepassing verzenden, de gegevens naar een andere service verzenden, de gegevens in een formulierontwerp samenvoegen, de gegevens weergeven in een webbrowser, enzovoort.

Formuliergegevens worden naar de service Forms verzonden als XML- of PDF-gegevens. Dit is een optie die is ingesteld in Designer. Met een formulier dat als XML wordt verzonden, kunt u afzonderlijke waarden van veldgegevens extraheren. Met andere woorden, u kunt de waarde extraheren van elk formulierveld dat de gebruiker in het formulier heeft ingevoerd. Een formulier dat als PDF-gegevens wordt verzonden, is binaire gegevens, niet XML-gegevens. U kunt het formulier opslaan als PDF-bestand of het formulier naar een andere service verzenden. Als u gegevens wilt extraheren uit een formulier dat als XML is verzonden en de formuliergegevens vervolgens wilt gebruiken om een PDF-document te maken, roept u een andere bewerking voor AEM-formulieren aan. (Zie PDF-documenten [maken met verzonden XML-gegevens](/help/forms/developing/creating-pdf-documents-submitted-xml.md))

In het volgende diagram worden gegevens weergegeven die worden verzonden naar een Java-server die is benoemd `HandleData` vanuit een interactief formulier dat wordt weergegeven in een webbrowser.

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
   <td><p>Gegevens worden als XML-gegevens naar de <code>HandleData</code> Java-server verzonden.</p></td>
  </tr>
  <tr>
   <td><p>3</p></td>
   <td><p>De <code>HandleData</code> Java Server bevat toepassingslogica om de gegevens op te halen.</p></td>
  </tr>
 </tbody>
</table>

## Verzonden XML-gegevens verwerken {#handling-submitted-xml-data}

Wanneer formuliergegevens als XML worden verzonden, kunt u XML-gegevens ophalen die de verzonden gegevens vertegenwoordigen. Alle formuliervelden worden weergegeven als knooppunten in een XML-schema. De knoopwaarden komen overeen met de waarden die de gebruiker heeft ingevuld. Neem bijvoorbeeld een leningformulier waarin elk veld in het formulier wordt weergegeven als een knooppunt in de XML-gegevens. De waarde van elk knooppunt komt overeen met de waarde die een gebruiker invult. Stel dat een gebruiker het leningformulier vult met gegevens die in het volgende formulier worden getoond.

![hs_hs_linformdata](assets/hs_hs_loanformdata.png)

In de volgende afbeelding ziet u de overeenkomstige XML-gegevens die zijn opgehaald met de API van de Forms service Client.

![hs_hs_loandata](assets/hs_hs_loandata.png)

De velden in het leningformulier. Deze waarden kunnen worden opgehaald met Java XML-klassen.

>[!NOTE]
>
>Gegevens die als XML-gegevens moeten worden verzonden, moeten correct zijn geconfigureerd in Designer. Als u het formulierontwerp correct wilt configureren voor het verzenden van XML-gegevens, moet u ervoor zorgen dat de knop Verzenden die zich in het formulierontwerp bevindt, is ingesteld op het verzenden van XML-gegevens. Zie [AEM Forms Designer](https://www.adobe.com/go/learn_aemforms_designer_63)voor informatie over het instellen van de knop Verzenden om XML-gegevens te verzenden.

## Verzonden PDF-gegevens verwerken {#handling-submitted-pdf-data}

Neem bijvoorbeeld een webtoepassing die de service Forms aanroept. Nadat de Forms-service een interactief PDF-formulier heeft gerenderd naar een webbrowser van een client, vult de gebruiker het formulier in en verzendt het als PDF-gegevens. Wanneer de service Forms de PDF-gegevens ontvangt, kunnen de PDF-gegevens naar een andere service worden verzonden of als PDF-bestand worden opgeslagen. Het volgende diagram toont de logische stroom van de toepassing.

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
   <td><p>Een webpagina bevat een koppeling die toegang krijgt tot een Java Server die de service Forms aanroept.</p></td>
  </tr>
  <tr>
   <td><p>2</p></td>
   <td><p>Met de service Forms wordt een interactief PDF-formulier weergegeven in de webbrowser van de client.</p></td>
  </tr>
  <tr>
   <td><p>3</p></td>
   <td><p>De gebruiker vult een interactief formulier in en klikt op een verzendknop. Het formulier wordt als PDF-gegevens teruggestuurd naar de service Forms. Deze optie wordt ingesteld in Designer.</p></td>
  </tr>
  <tr>
   <td><p>4</p></td>
   <td><p>De service Forms slaat de PDF-gegevens op als een PDF-bestand. </p></td>
  </tr>
 </tbody>
</table>

## Verzonden URL UTF-16-gegevens verwerken {#handling-submitted-url-utf-16-data}

Als formuliergegevens worden verzonden als UTF-16-URL-gegevens, vereist de clientcomputer Adobe Reader of Acrobat 8.1 of hoger. Als het formulierontwerp een verzendknop bevat met URL-gecodeerde gegevens (HTTP Post) en de optie voor gegevenscodering UTF-16 is, moet het formulierontwerp worden gewijzigd in een teksteditor, zoals Kladblok. U kunt de coderingsoptie instellen op `UTF-16LE` of `UTF-16BE` voor de verzendknop. Designer biedt deze functionaliteit niet.

>[!NOTE]
>
>Voor meer informatie over de dienst van Vormen, zie de Verwijzing van de [Diensten voor Vormen](https://www.adobe.com/go/learn_aemforms_services_63)AEM.

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

Voordat u een API-bewerking voor Forms-service programmatisch kunt uitvoeren, moet u een Forms-service-client maken. Als u de Java API gebruikt, maakt u een `FormsServiceClient` object. Als u de API voor webservices van Forms gebruikt, maakt u een `FormsService` object.

**Formuliergegevens ophalen**

Als u verzonden formuliergegevens wilt ophalen, roept u de `FormsServiceClient` methode van het `processFormSubmission` object aan. Wanneer u deze methode aanroept, moet u het inhoudstype van het verzonden formulier opgeven. Wanneer gegevens vanuit een clientwebbrowser naar de service Forms worden verzonden, kunnen deze als XML- of PDF-gegevens worden verzonden. Om de gegevens op te halen die in formuliervelden zijn ingevoerd, kunnen de gegevens als XML-gegevens worden verzonden.

U kunt ook formuliervelden ophalen uit een formulier dat als PDF-gegevens is verzonden door de volgende runtime-opties in te stellen:

* Geef de volgende waarde als parameter voor het inhoudstype door aan de `processFormSubmission` methode: `CONTENT_TYPE=application/pdf`.
* De `RenderOptionsSpec` waarde van het `PDFToXDP` object instellen op `true`
* De `RenderOptionsSpec` waarde van het `ExportDataFormat` object instellen op `XMLData`

U geeft het inhoudstype van het verzonden formulier op wanneer u de `processFormSubmission` methode aanroept. In de volgende lijst worden de toepasselijke waarden voor inhoudstypen aangegeven:

* **text/xml**: Het inhoudstype dat wordt gebruikt wanneer een PDF-formulier formuliergegevens als XML verzendt.
* **application/x-www-form-urlencoded**: Vertegenwoordigt het inhoudstype dat moet worden gebruikt wanneer een HTML-formulier gegevens als XML verzendt.
* **application/pdf**: Vertegenwoordigt het inhoudstype dat moet worden gebruikt wanneer een PDF-formulier gegevens als PDF verzendt.

>[!NOTE]
>
>Er zijn drie bijbehorende snelle start gekoppeld aan de sectie Verzendformulieren verwerken. De PDF-formulieren verwerken die zijn verzonden als PDF met de snelle start van de Java API laat zien hoe verzonden PDF-gegevens worden verwerkt. Het inhoudstype dat in deze snelle start wordt opgegeven, is `application/pdf`. De functie PDF-formulieren verwerken die zijn verzonden als XML met de Java API Quick start laat zien hoe de verzonden XML-gegevens worden verwerkt die worden verzonden vanuit een PDF-formulier. Het inhoudstype dat in deze snelle start wordt opgegeven, is `text/xml`. Op dezelfde manier wordt met de snelle start van de Java API getoond hoe de verzonden HTML-formulieren die zijn verzonden als XML worden verwerkt. Deze bewerking laat zien hoe de verzonden XML-gegevens die zijn verzonden vanuit een HTML-formulier, worden verwerkt. Het inhoudstype dat in deze snelle start wordt opgegeven, is application/x-www-form-urlencoded.

U haalt formuliergegevens op die naar de Forms-service zijn gepost en bepaalt de verwerkingsstatus. Wanneer gegevens naar de service Forms worden verzonden, betekent dit niet noodzakelijkerwijs dat de service Forms de gegevens heeft verwerkt en dat de gegevens klaar zijn om te worden verwerkt. Gegevens kunnen bijvoorbeeld naar de service Forms worden verzonden, zodat een berekening kan worden uitgevoerd. Wanneer de berekening is voltooid, wordt het formulier teruggestuurd naar de gebruiker met de weergegeven berekeningsresultaten. Voordat u verzonden gegevens verwerkt, wordt u aangeraden vast te stellen of de service Forms de gegevens heeft verwerkt.

De service Forms retourneert de volgende waarden om aan te geven of de verwerking van de gegevens is voltooid:

* **0 (Verzenden):** De verzonden gegevens zijn klaar om te worden verwerkt.
* **1 (berekenen):** De Forms-service heeft de gegevens berekend en de resultaten moeten worden teruggegeven aan de gebruiker.
* **2 (Valideren):** De door de Forms-service gevalideerde formuliergegevens en de resultaten moeten naar de gebruiker worden teruggestuurd.
* **3 (Volgende):** De huidige pagina is gewijzigd met resultaten die naar de clienttoepassing moeten worden geschreven.
* **4 (Vorige**): De huidige pagina is gewijzigd met resultaten die naar de clienttoepassing moeten worden geschreven.

>[!NOTE]
>
>Berekeningen en validaties moeten worden teruggegeven aan de gebruiker. (Zie Formuliergegevens [berekenen](/help/forms/developing/calculating-form-data.md#calculating-form-data).

**Bepalen of de formulierverzending bestandsbijlagen bevat**

Formulieren die worden verzonden naar de service Forms kunnen bestandsbijlagen bevatten. Met het ingebouwde venster Bijlage van Acrobat kan een gebruiker bijvoorbeeld bestandsbijlagen selecteren die samen met het formulier moeten worden verzonden. Een gebruiker kan ook bestandsbijlagen selecteren met een HTML-werkbalk die wordt weergegeven met een HTML-bestand.

Nadat u hebt bepaald of een formulier bestandsbijlagen bevat, kunt u de gegevens verwerken. U kunt bijvoorbeeld de bestandsbijlage opslaan in het lokale bestandssysteem.

>[!NOTE]
>
>Het formulier moet worden verzonden als PDF-gegevens om bestandsbijlagen op te halen. Als het formulier wordt verzonden als XML-gegevens, worden bestandsbijlagen niet verzonden.

**De verzonden gegevens verwerken**

Afhankelijk van het inhoudstype van de verzonden gegevens, kunt u afzonderlijke formulierveldwaarden extraheren uit de verzonden XML-gegevens of de verzonden PDF-gegevens opslaan als een PDF-bestand (of deze naar een andere service verzenden). Als u afzonderlijke formuliervelden wilt extraheren, converteert u de ingediende XML-gegevens naar een XML-gegevensbron en haalt u vervolgens de XML-gegevensbronwaarden op met behulp van `org.w3c.dom` klassen.

**Zie ook**

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Forms Service API, snel aan de slag](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

[Documenten doorgeven aan de Forms Service](/help/forms/developing/passing-documents-forms-service.md)

[Webtoepassingen maken die formulieren renderen](/help/forms/developing/creating-web-applications-renders-forms.md)

## Ingevulde formulieren verwerken met de Java API {#handle-submitted-forms-using-the-java-api}

Een verzonden formulier verwerken met de Forms API (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden, zoals adobe-forms-client.jar, op in het klassenpad van uw Java-project.

1. Een Forms Client API-object maken

   * Maak een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Maak een `FormsServiceClient` object door de constructor ervan te gebruiken en het `ServiceClientFactory` object door te geven.

1. Formuliergegevens ophalen

   * Als u formuliergegevens wilt ophalen die naar een Java Server zijn gepost, maakt u een `com.adobe.idp.Document` object met behulp van de constructor van het object en roept u de `javax.servlet.http.HttpServletResponse` methode van het `getInputStream` object aan vanuit de constructor.
   * Maak een `RenderOptionsSpec` object met de constructor ervan. Stel de waarde van de landinstelling in door de methode van het `RenderOptionsSpec` `setLocale` object aan te roepen en een tekenreekswaarde door te geven die de waarde van de landinstelling opgeeft.
   >[!NOTE]
   >
   >U kunt de Forms-service de opdracht geven XDP- of XML-gegevens te maken van verzonden PDF-inhoud door de methode van het `RenderOptionsSpec` object aan te roepen en door te geven `setPDF2XDP` en `true` door te geven `setXMLData` `true`. Vervolgens kunt u de `FormsResult` methode van het `getOutputXML` object aanroepen om de XML-gegevens op te halen die overeenkomen met de XDP/XML-gegevens. (Het `FormsResult` object wordt geretourneerd door de `processFormSubmission` methode, die in de volgende substap wordt beschreven.)

   * Roep de methode van het `FormsServiceClient` `processFormSubmission` object aan en geef de volgende waarden door:

      * Het `com.adobe.idp.Document` object dat de formuliergegevens bevat.
      * Een tekenreekswaarde die omgevingsvariabelen opgeeft, inclusief alle relevante HTTP-headers. Geef het inhoudstype op dat u wilt afhandelen. Als u XML-gegevens wilt verwerken, geeft u de volgende tekenreekswaarde op voor deze parameter: `CONTENT_TYPE=text/xml`. Als u PDF-gegevens wilt verwerken, geeft u de volgende tekenreekswaarde op voor deze parameter: `CONTENT_TYPE=application/pdf`.
      * Een tekenreekswaarde die bijvoorbeeld de `HTTP_USER_AGENT` koptekstwaarde opgeeft. `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)`. Deze parameterwaarde is optioneel.
      * Een `RenderOptionsSpec` object dat uitvoeringsopties opslaat.
      De `processFormSubmission` methode retourneert een `FormsResult` object dat de resultaten van het verzenden van het formulier bevat.

   * Bepaal of de service Forms klaar is met het verwerken van de formuliergegevens door de `FormsResult` `getAction` methode van het object aan te roepen. Als deze methode de waarde retourneert `0`, kunnen de gegevens worden verwerkt.



1. Bepalen of de formulierverzending bestandsbijlagen bevat

   * Roep de `FormsResult` methode van het `getAttachments` object aan. Deze methode retourneert een `java.util.List` object dat bestanden bevat die met het formulier zijn verzonden.
   * Doorloop het `java.util.List` object om te bepalen of er bestandsbijlagen zijn. Als er bestandsbijlagen zijn, is elk element een `com.adobe.idp.Document` instantie. U kunt de bestandsbijlagen opslaan door de methode van het `com.adobe.idp.Document` object aan te roepen en een `copyToFile` `java.io.File` object door te geven.
   >[!NOTE]
   >
   >Deze stap is alleen van toepassing als het formulier als PDF is verzonden.

1. De verzonden gegevens verwerken

   * Als het gegevenstype van de gegevens is `application/vnd.adobe.xdp+xml` of `text/xml`, creeer toepassingslogica om de gegevenswaarden van XML terug te winnen.

      * Maak een `com.adobe.idp.Document` object door de `FormsResult` methode van het `getOutputContent` object aan te roepen.
      * Maak een `java.io.InputStream` object door de `java.io.DataInputStream` constructor aan te roepen en het `com.adobe.idp.Document` object door te geven.
      * Maak een `org.w3c.dom.DocumentBuilderFactory` object door de `org.w3c.dom.DocumentBuilderFactory` methode van het statische `newInstance` object aan te roepen.
      * Maak een `org.w3c.dom.DocumentBuilder` object door de `org.w3c.dom.DocumentBuilderFactory` methode van het `newDocumentBuilder` object aan te roepen.
      * Maak een `org.w3c.dom.Document` object door de methode van het `org.w3c.dom.DocumentBuilder` object aan te roepen `parse` en het `java.io.InputStream` object door te geven.
      * Hiermee wordt de waarde van elk knooppunt in het XML-document opgehaald. U kunt deze taak uitvoeren door een aangepaste methode te maken die twee parameters accepteert: het `org.w3c.dom.Document` object en de naam van het knooppunt waarvan u de waarde wilt ophalen. Deze methode retourneert een tekenreekswaarde die de waarde van het knooppunt vertegenwoordigt. In het codevoorbeeld dat dit proces volgt, wordt deze douanemethode geroepen `getNodeText`. De hoofdtekst van deze methode wordt weergegeven.
   * Als het gegevenstype van de gegevens is, maakt u toepassingslogica om de verzonden PDF-gegevens op te slaan als een PDF-bestand. `application/pdf`

      * Maak een `com.adobe.idp.Document` object door de `FormsResult` methode van het `getOutputContent` object aan te roepen.
      * Maak een `java.io.File` object met behulp van de openbare constructor. Geef PDF op als bestandsnaamextensie.
      * Vul het PDF-bestand door de methode van het `com.adobe.idp.Document` object aan te roepen `copyToFile` en het `java.io.File` object door te geven.


**Zie ook**

[Snel starten (SOAP-modus): PDF-formulieren die zijn verzonden als XML, verwerken met de Java API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-handling-pdf-forms-submitted-as-xml-using-the-java-api)

[Snel starten (SOAP-modus): HTML-formulieren verwerken die zijn verzonden als XML met de Java API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-handling-html-forms-submitted-as-xml-using-the-java-api)

[Snel starten (SOAP-modus): PDF-formulieren die zijn verzonden als PDF, verwerken met de Java API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-handling-pdf-forms-submitted-as-pdf-using-the-java-api)

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Verzonden PDF-gegevens verwerken met de webservice-API {#handle-submitted-pdf-data-using-the-web-service-api}

Een verzonden formulier verwerken met de API voor formulieren (webservice):

1. Projectbestanden opnemen

   * Maak Java-proxyklassen die de Forms service WSDL gebruiken.
   * Neem de Java-proxyklassen op in het klassepad.

1. Een Forms Client API-object maken

   Maak een `FormsService` object en stel verificatiewaarden in.

1. Formuliergegevens ophalen

   * Als u formuliergegevens wilt ophalen die naar een Java Server zijn gepost, maakt u een `BLOB` object met de constructor ervan.
   * Maak een `java.io.InputStream` object door de `javax.servlet.http.HttpServletResponse` methode van het `getInputStream` object aan te roepen.
   * Maak een `java.io.ByteArrayOutputStream` object door de constructor ervan te gebruiken en de lengte van het `java.io.InputStream` object door te geven.
   * Kopieer de inhoud van het `java.io.InputStream` object naar het `java.io.ByteArrayOutputStream` object.
   * Maak een bytearray door de `java.io.ByteArrayOutputStream` methode van het `toByteArray` object aan te roepen.
   * Vul het `BLOB` `setBinaryData` object door de methode ervan aan te roepen en de bytearray als een argument door te geven.
   * Maak een `RenderOptionsSpec` object met de constructor ervan. Stel de waarde van de landinstelling in door de methode van het `RenderOptionsSpec` `setLocale` object aan te roepen en een tekenreekswaarde door te geven die de waarde van de landinstelling opgeeft.
   * Roep de methode van het `FormsService` `processFormSubmission` object aan en geef de volgende waarden door:

      * Het `BLOB` object dat de formuliergegevens bevat.
      * Een tekenreekswaarde die omgevingsvariabelen opgeeft, inclusief alle relevante HTTP-headers. Geef het inhoudstype op dat u wilt afhandelen. Als u XML-gegevens wilt verwerken, geeft u de volgende tekenreekswaarde op voor deze parameter: `CONTENT_TYPE=text/xml`. Als u PDF-gegevens wilt verwerken, geeft u de volgende tekenreekswaarde op voor deze parameter: `CONTENT_TYPE=application/pdf`.
      * Een tekenreekswaarde die de `HTTP_USER_AGENT` koptekstwaarde opgeeft; bijvoorbeeld `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)`.
      * Een `RenderOptionsSpec` object dat uitvoeringsopties opslaat.
      * Een leeg `BLOBHolder` object dat door de methode wordt gevuld.
      * Een leeg `javax.xml.rpc.holders.StringHolder` object dat door de methode wordt gevuld.
      * Een leeg `BLOBHolder` object dat door de methode wordt gevuld.
      * Een leeg `BLOBHolder` object dat door de methode wordt gevuld.
      * Een leeg `javax.xml.rpc.holders.ShortHolder` object dat door de methode wordt gevuld.
      * Een leeg `MyArrayOf_xsd_anyTypeHolder` object dat door de methode wordt gevuld. Met deze parameter worden bestandsbijlagen opgeslagen die samen met het formulier worden verzonden.
      * Een leeg `FormsResultHolder` object dat door de methode wordt gevuld met het formulier dat wordt verzonden.
      De `processFormSubmission` methode vult de `FormsResultHolder` parameter met de resultaten van het verzenden van het formulier.

   * Bepaal of de service Forms klaar is met het verwerken van de formuliergegevens door de `FormsResult` `getAction` methode van het object aan te roepen. Als deze methode de waarde retourneert `0`, kunnen de formuliergegevens worden verwerkt. U kunt een `FormsResult` object ophalen door de waarde van het `FormsResultHolder` `value` gegevenslid van het object op te halen.


1. Bepalen of de formulierverzending bestandsbijlagen bevat

   Hiermee wordt de waarde van het `MyArrayOf_xsd_anyTypeHolder` gegevenslid van het `value` object opgehaald (het `MyArrayOf_xsd_anyTypeHolder` object is aan de `processFormSubmission` methode doorgegeven). Dit gegevenslid retourneert een array van `Objects`. Elk element in de `Object` array is een element `Object`dat overeenkomt met de bestanden die samen met het formulier zijn verzonden. U kunt elk element binnen de array ophalen en naar een `BLOB` object casten.

1. De verzonden gegevens verwerken

   * Als het gegevenstype van de gegevens is `application/vnd.adobe.xdp+xml` of `text/xml`, creeer toepassingslogica om de gegevenswaarden van XML terug te winnen.

      * Maak een `BLOB` object door de `FormsResult` methode van het `getOutputContent` object aan te roepen.
      * Maak een bytearray door de `BLOB` methode van het `getBinaryData` object aan te roepen.
      * Maak een `java.io.InputStream` object door de `java.io.ByteArrayInputStream` constructor aan te roepen en de bytearray door te geven.
      * Maak een `org.w3c.dom.DocumentBuilderFactory` object door de `org.w3c.dom.DocumentBuilderFactory` methode van het statische `newInstance` object aan te roepen.
      * Maak een `org.w3c.dom.DocumentBuilder` object door de `org.w3c.dom.DocumentBuilderFactory` methode van het `newDocumentBuilder` object aan te roepen.
      * Maak een `org.w3c.dom.Document` object door de methode van het `org.w3c.dom.DocumentBuilder` object aan te roepen `parse` en het `java.io.InputStream` object door te geven.
      * Hiermee wordt de waarde van elk knooppunt in het XML-document opgehaald. U kunt deze taak uitvoeren door een aangepaste methode te maken die twee parameters accepteert: het `org.w3c.dom.Document` object en de naam van het knooppunt waarvan u de waarde wilt ophalen. Deze methode retourneert een tekenreekswaarde die de waarde van het knooppunt vertegenwoordigt. In het codevoorbeeld dat dit proces volgt, wordt deze douanemethode geroepen `getNodeText`. De hoofdtekst van deze methode wordt weergegeven.
   * Als het gegevenstype van de gegevens is, maakt u toepassingslogica om de verzonden PDF-gegevens op te slaan als een PDF-bestand. `application/pdf`

      * Maak een `BLOB` object door de `FormsResult` methode van het `getOutputContent` object aan te roepen.
      * Maak een bytearray door de `BLOB` methode van het `getBinaryData` object aan te roepen.
      * Maak een `java.io.File` object met behulp van de openbare constructor. Geef PDF op als bestandsnaamextensie.
      * Maak een `java.io.FileOutputStream` object door de constructor ervan te gebruiken en het `java.io.File` object door te geven.
      * Vul het PDF-bestand door de methode van het `java.io.FileOutputStream` `write` object aan te roepen en de bytearray door te geven.


**Zie ook**

[AEM-formulieren aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)