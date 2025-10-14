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
feature: Adaptive Forms,Document Services,APIs & Integrations
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '2894'
ht-degree: 0%

---

# Verzendde Forms afhandelen {#handling-submitted-forms}

**de Steekproeven en de voorbeelden in dit document zijn slechts voor AEM Forms op milieu JEE.**

Web-based toepassingen die een gebruiker toelaten om interactieve vormen in te vullen vereisen dat de gegevens terug naar de server worden voorgelegd. Met de Forms-service kunt u de gegevens ophalen die de gebruiker in een interactief formulier heeft ingevoerd. Nadat u de gegevens hebt opgehaald, kunt u de gegevens verwerken om aan uw bedrijfsvereisten te voldoen. U kunt de gegevens bijvoorbeeld opslaan in een database, de gegevens naar een andere toepassing verzenden, de gegevens naar een andere service verzenden, de gegevens in een formulierontwerp samenvoegen, de gegevens weergeven in een webbrowser, enzovoort.

Formuliergegevens worden naar de Forms-service verzonden als XML- of PDF-gegevens. Dit is een optie die in Designer is ingesteld. Met een formulier dat als XML wordt verzonden, kunt u afzonderlijke waarden van veldgegevens extraheren. Met andere woorden, u kunt de waarde extraheren van elk formulierveld dat de gebruiker in het formulier heeft ingevoerd. Een formulier dat wordt verzonden als PDF-gegevens, is binaire gegevens, niet XML-gegevens. U kunt het formulier opslaan als een PDF-bestand of het formulier verzenden naar een andere service. Als u gegevens wilt extraheren uit een formulier dat als XML is verzonden en vervolgens de formuliergegevens wilt gebruiken om een PDF-document te maken, roept u een andere AEM Forms-bewerking op. (Zie [&#x200B; Creërend de Documenten van PDF met Voorgelegde Gegevens van XML &#x200B;](/help/forms/developing/creating-pdf-documents-submitted-xml.md))

In het volgende diagram worden gegevens weergegeven die vanuit een interactief formulier dat in een webbrowser wordt weergegeven, worden verzonden naar een Java Server met de naam `HandleData` .

![&#x200B; hs_hs_handlesubmit &#x200B;](assets/hs_hs_handlesubmit.png)

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
   <td><p>Gegevens worden als XML-gegevens naar de <code>HandleData</code> Java Server verzonden.</p></td>
  </tr>
  <tr>
   <td><p>3</p></td>
   <td><p>De Java Server van <code>HandleData</code> bevat toepassingslogica om de gegevens terug te winnen.</p></td>
  </tr>
 </tbody>
</table>

## Verzonden XML-gegevens verwerken {#handling-submitted-xml-data}

Wanneer formuliergegevens als XML worden verzonden, kunt u XML-gegevens ophalen die de verzonden gegevens vertegenwoordigen. Alle formuliervelden worden weergegeven als knooppunten in een XML-schema. De knoopwaarden komen overeen met de waarden die de gebruiker heeft ingevuld. Neem bijvoorbeeld een leningformulier waarin elk veld in het formulier wordt weergegeven als een knooppunt in de XML-gegevens. De waarde van elk knooppunt komt overeen met de waarde die een gebruiker invult. Stel dat een gebruiker het leningformulier vult met gegevens die in het volgende formulier worden getoond.

![&#x200B; hs_hs_loanformdata &#x200B;](assets/hs_hs_loanformdata.png)

In de volgende afbeelding ziet u de overeenkomstige XML-gegevens die zijn opgehaald met de Forms Service Client API.

![&#x200B; hs_hs_loandata &#x200B;](assets/hs_hs_loandata.png)

De velden in het leningformulier. Deze waarden kunnen worden opgehaald
Java XML-klassen gebruiken.

>[!NOTE]
>
>Gegevens die als XML-gegevens moeten worden verzonden, moeten correct zijn geconfigureerd in Designer. Als u het formulierontwerp correct wilt configureren voor het verzenden van XML-gegevens, moet u ervoor zorgen dat de knop Verzenden die zich in het formulierontwerp bevindt, is ingesteld op het verzenden van XML-gegevens. Voor informatie over het plaatsen van de Submit knoop om de gegevens van XML voor te leggen, zie [&#x200B; AEM Forms Designer &#x200B;](https://www.adobe.com/go/learn_aemforms_designer_63).

## Ingediende PDF-gegevens verwerken {#handling-submitted-pdf-data}

Neem bijvoorbeeld een webtoepassing die de Forms-service oproept. Nadat de Forms-service een interactief PDF-formulier heeft gerenderd naar een clientwebbrowser, vult de gebruiker het formulier in en verzendt het terug als PDF-gegevens. Wanneer de Forms-service de PDF-gegevens ontvangt, kunnen de PDF-gegevens naar een andere service worden verzonden of worden opgeslagen als een PDF-bestand. Het volgende diagram toont de logische stroom van de toepassing.

![&#x200B; hs_hs_savingforms &#x200B;](assets/hs_hs_savingforms.png)

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
   <td><p>De gebruiker vult een interactief formulier in en klikt op een verzendknop. Het formulier wordt als PDF-gegevens teruggestuurd naar de Forms-service. Deze optie is ingesteld in Designer.</p></td>
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
>Voor meer informatie over de dienst van Forms, zie [&#x200B; Verwijzing van de Diensten voor AEM Forms &#x200B;](https://www.adobe.com/go/learn_aemforms_services_63).

## Overzicht van de stappen {#summary-of-steps}

Voer de volgende taken uit om verzonden formulieren te verwerken:

1. Inclusief projectbestanden.
1. Maak een Forms Client API-object.
1. Formuliergegevens ophalen.
1. Bepaal of de formulierverzending bestandsbijlagen bevat.
1. Verwerk de verzonden gegevens.

**omvat projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

**creeer een voorwerp van Forms Cliënt API**

Voordat u programmatisch een client-API-bewerking voor Forms-services kunt uitvoeren, moet u een Forms-serviceclient maken. Maak een `FormsServiceClient` -object als u de Java API gebruikt. Maak een `FormsService` -object als u de Forms-API voor webservices gebruikt.

**wint vormgegevens** terug

Als u verzonden formuliergegevens wilt ophalen, roept u de methode `processFormSubmission` van het object `FormsServiceClient` aan. Wanneer u deze methode aanroept, moet u het inhoudstype van het verzonden formulier opgeven. Wanneer gegevens vanuit een clientwebbrowser naar de Forms-service worden verzonden, kunnen deze als XML- of PDF-gegevens worden verzonden. Om de gegevens op te halen die in formuliervelden zijn ingevoerd, kunnen de gegevens als XML-gegevens worden verzonden.

U kunt ook formuliervelden ophalen uit een formulier dat als PDF-gegevens wordt verzonden door de volgende runtime-opties in te stellen:

* Geef de volgende waarde door aan de methode `processFormSubmission` als parameter voor het inhoudstype: `CONTENT_TYPE=application/pdf` .
* Stel de `PDFToXDP` -waarde `true` van het object `RenderOptionsSpec` in
* Stel de `ExportDataFormat` -waarde `XMLData` van het object `RenderOptionsSpec` in

U geeft het inhoudstype van het verzonden formulier op wanneer u de methode `processFormSubmission` aanroept. In de volgende lijst worden de toepasselijke waarden voor inhoudstypen aangegeven:

* **text/xml**: Vertegenwoordigt het inhoudstype aan gebruik wanneer een vorm van PDF formuliergegevens als XML voorlegt.
* **toepassing/x-www-vorm-urlencoded**: Vertegenwoordigt het inhoudstype aan gebruik wanneer een vorm van HTML gegevens als XML voorlegt.
* **toepassing/pdf**: Vertegenwoordigt het inhoudstype aan gebruik wanneer een vorm van de PDF gegevens als PDF voorlegt.

>[!NOTE]
>
>Er zijn drie bijbehorende snelstarthandleidingen gekoppeld aan de sectie Verzendde Forms afhandelen. De PDF forms die worden verzonden als PDF met de Java API Quick start tonen aan hoe de verzonden PDF-gegevens moeten worden verwerkt. Het inhoudstype dat in deze snelle start wordt opgegeven, is `application/pdf` . De PDF forms die worden verzonden als XML met de snelle start van de Java API laten zien hoe de verzonden XML-gegevens worden verwerkt die worden verzonden vanuit een PDF-formulier. Het inhoudstype dat in deze snelle start wordt opgegeven, is `text/xml` . Op dezelfde manier tonen de HTML-formulieren voor verwerking die als XML worden verzonden met de snelle start van de Java API aan hoe de verzonden XML-gegevens die vanuit een HTML-formulier zijn verzonden, moeten worden afgehandeld. Het inhoudstype dat in deze snelle start wordt opgegeven, is application/x-www-form-urlencoded.

U haalt formuliergegevens op die naar de Forms-service zijn verzonden en bepaalt de verwerkingsstatus. Dat wil zeggen dat wanneer gegevens worden ingediend bij de Forms-dienst, dit niet noodzakelijkerwijs betekent dat de Forms-dienst de gegevens heeft verwerkt en dat de gegevens klaar zijn om te worden verwerkt. Gegevens kunnen bijvoorbeeld naar de Forms-service worden verzonden, zodat een berekening kan worden uitgevoerd. Wanneer de berekening is voltooid, wordt het formulier teruggestuurd naar de gebruiker met de weergegeven berekeningsresultaten. Voordat u verzonden gegevens verwerkt, wordt u aangeraden te bepalen of de Forms-service de gegevens heeft verwerkt.

De Forms-service retourneert de volgende waarden om aan te geven of de verwerking van de gegevens is voltooid:

* **0 (voorlegt):** Voorgelegde gegevens zijn klaar om te worden verwerkt.
* **1 (Bereken):** de dienst van Forms voerde een berekeningsverrichting op de gegevens uit en de resultaten moeten terug naar de gebruiker worden teruggegeven.
* **2 (Valideren):** de dienst van Forms bevestigde vormgegevens en de resultaten moeten terug naar de gebruiker worden teruggegeven.
* **3 (Volgende):** De huidige pagina is veranderd met resultaten die aan de cliënttoepassing moeten worden geschreven.
* **4 (Vorige**): De huidige pagina is veranderd met resultaten die aan de cliënttoepassing moeten worden geschreven.

>[!NOTE]
>
>Berekeningen en validaties moeten worden teruggegeven aan de gebruiker. (Zie [&#x200B; Berekend de Gegevens van de Vorm &#x200B;](/help/forms/developing/calculating-form-data.md#calculating-form-data).

**bepaalt als de vormvoorlegging dossiergehechtheid** bevat

Forms dat is verzonden naar de Forms-service kan bestandsbijlagen bevatten. Met het venster voor ingebouwde bijlagen van Acrobat kan een gebruiker bijvoorbeeld bestandsbijlagen selecteren die samen met het formulier moeten worden verzonden. Een gebruiker kan ook bestandsbijlagen selecteren met een HTML-werkbalk die wordt weergegeven met een HTML-bestand.

Nadat u hebt bepaald of een formulier bestandsbijlagen bevat, kunt u de gegevens verwerken. U kunt bijvoorbeeld de bestandsbijlage opslaan in het lokale bestandssysteem.

>[!NOTE]
>
>Het formulier moet worden verzonden als PDF-gegevens om bestandsbijlagen op te halen. Als het formulier wordt verzonden als XML-gegevens, worden bestandsbijlagen niet verzonden.

**Proces de voorgelegde gegevens**

Afhankelijk van het inhoudstype van de verzonden gegevens, kunt u afzonderlijke formulierveldwaarden extraheren uit de verzonden XML-gegevens of de verzonden PDF-gegevens opslaan als een PDF-bestand (of deze naar een andere service verzenden). Als u afzonderlijke formuliervelden wilt extraheren, converteert u de ingediende XML-gegevens naar een XML-gegevensbron en haalt u vervolgens de XML-gegevensbronwaarden op met behulp van `org.w3c.dom` -klassen.

**zie ook**

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

   * Maak een `ServiceClientFactory` -object dat verbindingseigenschappen bevat.
   * Maak een `FormsServiceClient` -object door de constructor ervan te gebruiken en het `ServiceClientFactory` -object door te geven.

1. Formuliergegevens ophalen

   * Als u formuliergegevens wilt ophalen die naar een Java Server zijn gepost, maakt u een `com.adobe.idp.Document` -object met de constructor ervan en roept u de methode `javax.servlet.http.HttpServletResponse` object `getInputStream` vanuit de constructor aan.
   * Maak een `RenderOptionsSpec` -object met behulp van de constructor. Stel de waarde van de landinstelling in door de methode van het `RenderOptionsSpec` -object `setLocale` aan te roepen en een tekenreekswaarde door te geven die de waarde van de landinstelling opgeeft.

   >[!NOTE]
   >
   >U kunt de Forms-service de instructie geven om XDP- of XML-gegevens te maken op basis van verzonden PDF-inhoud door de methode `setPDF2XDP` van het object `RenderOptionsSpec` aan te roepen en door te geven `true` en `setXMLData` en door te geven `true` . Vervolgens kunt u de methode `getOutputXML` van het object `FormsResult` aanroepen om de XML-gegevens op te halen die overeenkomen met de XDP/XML-gegevens. (Het object `FormsResult` wordt geretourneerd door de methode `processFormSubmission` , die in de volgende substap wordt beschreven.)

   * Roep de methode `processFormSubmission` van het object `FormsServiceClient` aan en geef de volgende waarden door:

      * Het `com.adobe.idp.Document` -object dat de formuliergegevens bevat.
      * Een tekenreekswaarde die omgevingsvariabelen opgeeft, inclusief alle relevante HTTP-headers. Geef het inhoudstype op dat u wilt afhandelen. Als u XML-gegevens wilt verwerken, geeft u de volgende tekenreekswaarde voor deze parameter op: `CONTENT_TYPE=text/xml` . Als u PDF-gegevens wilt verwerken, geeft u de volgende tekenreekswaarde voor deze parameter op: `CONTENT_TYPE=application/pdf` .
      * Een tekenreekswaarde die bijvoorbeeld de headerwaarde `HTTP_USER_AGENT` opgeeft. `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)`. Deze parameterwaarde is optioneel.
      * Een `RenderOptionsSpec` -object dat uitvoeringsopties opslaat.

     De methode `processFormSubmission` retourneert een `FormsResult` -object dat de resultaten van het verzenden van het formulier bevat.

   * Bepaal of de Forms-service de formuliergegevens heeft verwerkt door de methode `getAction` van het object `FormsResult` aan te roepen. Als deze methode de waarde `0` retourneert, kunnen de gegevens worden verwerkt.

1. Bepalen of de formulierverzending bestandsbijlagen bevat

   * Roep de methode `getAttachments` van het object `FormsResult` aan. Deze methode retourneert een `java.util.List` -object dat bestanden bevat die met het formulier zijn verzonden.
   * Doorloop het `java.util.List` -object om te bepalen of er bestandsbijlagen zijn. Als er bestandsbijlagen zijn, is elk element een `com.adobe.idp.Document` -instantie. U kunt de bestandsbijlagen opslaan door de methode `copyToFile` van het object `com.adobe.idp.Document` aan te roepen en een object `java.io.File` door te geven.

   >[!NOTE]
   >
   >Deze stap is alleen van toepassing als het formulier wordt verzonden als PDF.

1. De verzonden gegevens verwerken

   * Als het gegevenstype `application/vnd.adobe.xdp+xml` of `text/xml` is, maakt u toepassingslogica om XML-gegevenswaarden op te halen.

      * Maak een `com.adobe.idp.Document` -object door de methode `FormsResult` object `getOutputContent` aan te roepen.
      * Maak een `java.io.InputStream` -object door de `java.io.DataInputStream` -constructor aan te roepen en het `com.adobe.idp.Document` -object door te geven.
      * Maak een `org.w3c.dom.DocumentBuilderFactory` -object door de statische methode `org.w3c.dom.DocumentBuilderFactory` van het object `newInstance` aan te roepen.
      * Maak een `org.w3c.dom.DocumentBuilder` -object door de methode `org.w3c.dom.DocumentBuilderFactory` object `newDocumentBuilder` aan te roepen.
      * Maak een `org.w3c.dom.Document` -object door de methode `org.w3c.dom.DocumentBuilder` object `parse` aan te roepen en het `java.io.InputStream` -object door te geven.
      * Haal de waarde van elk knooppunt in het XML-document op. U kunt deze taak uitvoeren door een aangepaste methode te maken die twee parameters accepteert: het `org.w3c.dom.Document` -object en de naam van het knooppunt waarvan u de waarde wilt ophalen. Deze methode retourneert een tekenreekswaarde die de waarde van het knooppunt vertegenwoordigt. In het codevoorbeeld dat dit proces volgt, wordt deze aangepaste methode `getNodeText` genoemd. De hoofdtekst van deze methode wordt weergegeven.

   * Als het gegevenstype `application/pdf` is, maakt u toepassingslogica om de verzonden PDF-gegevens op te slaan als een PDF-bestand.

      * Maak een `com.adobe.idp.Document` -object door de methode `FormsResult` object `getOutputContent` aan te roepen.
      * Maak een `java.io.File` -object met behulp van de openbare constructor. Zorg ervoor dat u PDF opgeeft als bestandsextensie.
      * Vul het bestand PDF door de methode `copyToFile` van het object `com.adobe.idp.Document` aan te roepen en het object `java.io.File` door te geven.

**zie ook**

[Snel starten (SOAP modus): PDF forms verwerken die zijn verzonden als XML met de Java API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-handling-pdf-forms-submitted-as-xml-using-the-java-api)

[Snel starten (SOAP modus): HTML-formulieren verwerken die zijn verzonden als XML met de Java API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-handling-html-forms-submitted-as-xml-using-the-java-api)

[Snel starten (SOAP modus): PDF forms verwerken die als PDF zijn verzonden met de Java API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-handling-pdf-forms-submitted-as-pdf-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Verzonden PDF-gegevens verwerken met de webservice-API {#handle-submitted-pdf-data-using-the-web-service-api}

Een verzonden formulier verwerken met de Forms API (webservice):

1. Projectbestanden opnemen

   * Maak Java-proxyklassen die gebruikmaken van de Forms-service WSDL.
   * Neem de Java-proxyklassen op in het klassepad.

1. Een Forms Client API-object maken

   Maak een `FormsService` -object en stel de verificatiewaarden in.

1. Formuliergegevens ophalen

   * Als u formuliergegevens wilt ophalen die naar een Java Server zijn gepost, maakt u een `BLOB` -object met behulp van de bijbehorende constructor.
   * Maak een `java.io.InputStream` -object door de methode `javax.servlet.http.HttpServletResponse` object `getInputStream` aan te roepen.
   * Maak een `java.io.ByteArrayOutputStream` -object door de constructor ervan te gebruiken en de lengte van het `java.io.InputStream` -object door te geven.
   * Kopieer de inhoud van het object `java.io.InputStream` naar het object `java.io.ByteArrayOutputStream` .
   * Maak een bytearray door de methode `toByteArray` van het object `java.io.ByteArrayOutputStream` aan te roepen.
   * Vul het object `BLOB` door de methode `setBinaryData` ervan aan te roepen en de bytearray als een argument door te geven.
   * Maak een `RenderOptionsSpec` -object met behulp van de constructor. Stel de waarde van de landinstelling in door de methode van het `RenderOptionsSpec` -object `setLocale` aan te roepen en een tekenreekswaarde door te geven die de waarde van de landinstelling opgeeft.
   * Roep de methode `processFormSubmission` van het object `FormsService` aan en geef de volgende waarden door:

      * Het `BLOB` -object dat de formuliergegevens bevat.
      * Een tekenreekswaarde die omgevingsvariabelen opgeeft, inclusief alle relevante HTTP-headers. Geef het inhoudstype op dat u wilt afhandelen. Als u XML-gegevens wilt verwerken, geeft u de volgende tekenreekswaarde voor deze parameter op: `CONTENT_TYPE=text/xml` . Als u PDF-gegevens wilt verwerken, geeft u de volgende tekenreekswaarde voor deze parameter op: `CONTENT_TYPE=application/pdf` .
      * Een tekenreekswaarde die de headerwaarde `HTTP_USER_AGENT` opgeeft, bijvoorbeeld `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 1.1.4322)` .
      * Een `RenderOptionsSpec` -object dat uitvoeringsopties opslaat.
      * Een leeg `BLOBHolder` -object dat door de methode wordt gevuld.
      * Een leeg `javax.xml.rpc.holders.StringHolder` -object dat door de methode wordt gevuld.
      * Een leeg `BLOBHolder` -object dat door de methode wordt gevuld.
      * Een leeg `BLOBHolder` -object dat door de methode wordt gevuld.
      * Een leeg `javax.xml.rpc.holders.ShortHolder` -object dat door de methode wordt gevuld.
      * Een leeg `MyArrayOf_xsd_anyTypeHolder` -object dat door de methode wordt gevuld. Met deze parameter worden bestandsbijlagen opgeslagen die samen met het formulier worden verzonden.
      * Een leeg `FormsResultHolder` -object dat door de methode wordt gevuld met het formulier dat wordt verzonden.

     Met de methode `processFormSubmission` wordt de parameter `FormsResultHolder` gevuld met de resultaten van het verzenden van het formulier.

   * Bepaal of de Forms-service de formuliergegevens heeft verwerkt door de methode `getAction` van het object `FormsResult` aan te roepen. Als deze methode de waarde `0` retourneert, kunnen de formuliergegevens worden verwerkt. U kunt een `FormsResult` -object ophalen door de waarde van het gegevenslid van het `FormsResultHolder` object `value` op te halen.

1. Bepalen of de formulierverzending bestandsbijlagen bevat

   Hiermee wordt de waarde van het gegevenslid `value` van het `MyArrayOf_xsd_anyTypeHolder` -object opgehaald (het object `MyArrayOf_xsd_anyTypeHolder` is doorgegeven aan de methode `processFormSubmission` ). Dit gegevenslid retourneert een array van `Objects` . Elk element binnen de `Object` serie is `Object` die aan de dossiers beantwoordt die samen met de vorm werden voorgelegd. U kunt elk element in de array ophalen en naar een `BLOB` -object casten.

1. De verzonden gegevens verwerken

   * Als het gegevenstype `application/vnd.adobe.xdp+xml` of `text/xml` is, maakt u toepassingslogica om XML-gegevenswaarden op te halen.

      * Maak een `BLOB` -object door de methode `FormsResult` object `getOutputContent` aan te roepen.
      * Maak een bytearray door de methode `getBinaryData` van het object `BLOB` aan te roepen.
      * Maak een `java.io.InputStream` -object door de `java.io.ByteArrayInputStream` -constructor aan te roepen en de bytearray door te geven.
      * Maak een `org.w3c.dom.DocumentBuilderFactory` -object door de statische methode `org.w3c.dom.DocumentBuilderFactory` van het object `newInstance` aan te roepen.
      * Maak een `org.w3c.dom.DocumentBuilder` -object door de methode `org.w3c.dom.DocumentBuilderFactory` object `newDocumentBuilder` aan te roepen.
      * Maak een `org.w3c.dom.Document` -object door de methode `org.w3c.dom.DocumentBuilder` object `parse` aan te roepen en het `java.io.InputStream` -object door te geven.
      * Haal de waarde van elk knooppunt in het XML-document op. U kunt deze taak uitvoeren door een aangepaste methode te maken die twee parameters accepteert: het `org.w3c.dom.Document` -object en de naam van het knooppunt waarvan u de waarde wilt ophalen. Deze methode retourneert een tekenreekswaarde die de waarde van het knooppunt vertegenwoordigt. In het codevoorbeeld dat dit proces volgt, wordt deze aangepaste methode `getNodeText` genoemd. De hoofdtekst van deze methode wordt weergegeven.

   * Als het gegevenstype `application/pdf` is, maakt u toepassingslogica om de verzonden PDF-gegevens op te slaan als een PDF-bestand.

      * Maak een `BLOB` -object door de methode `FormsResult` object `getOutputContent` aan te roepen.
      * Maak een bytearray door de methode `getBinaryData` van het object `BLOB` aan te roepen.
      * Maak een `java.io.File` -object met behulp van de openbare constructor. Zorg ervoor dat u PDF opgeeft als bestandsextensie.
      * Maak een `java.io.FileOutputStream` -object door de constructor ervan te gebruiken en het `java.io.File` -object door te geven.
      * Vul het bestand PDF door de methode `write` van het object `java.io.FileOutputStream` aan te roepen en de bytearray door te geven.

**zie ook**

[AEM Forms aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
