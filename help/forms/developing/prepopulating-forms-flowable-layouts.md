---
title: Formulieren vooraf invullen met stroombare indelingen
seo-title: Formulieren vooraf invullen met stroombare indelingen
description: 'null'
seo-description: 'null'
uuid: 93ccb496-e1c2-4b79-8e89-7a2abfce1537
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 30a12fc6-07b8-4c7c-b9e2-caa2bec0ac48
translation-type: tm+mt
source-git-commit: 1343cc33a1e1ce26c0770a3b49317e82353497ab
workflow-type: tm+mt
source-wordcount: '3489'
ht-degree: 0%

---


# Formulieren vooraf invullen met stroombare indelingen {#prepopulating-forms-with-flowable-layouts1}

## Formulieren vooraf invullen met stroombare indelingen {#prepopulating-forms-with-flowable-layouts2}

Als u formulieren vooraf invult, worden gegevens weergegeven voor gebruikers in een gegenereerd formulier. Stel bijvoorbeeld dat een gebruiker zich aanmeldt bij een website met een gebruikersnaam en wachtwoord. Als de verificatie is gelukt, vraagt de clienttoepassing een database om gebruikersgegevens. De gegevens worden samengevoegd in het formulier en het formulier wordt vervolgens weergegeven aan de gebruiker. Hierdoor kan de gebruiker gepersonaliseerde gegevens weergeven in het formulier.

Het vooraf invullen van een formulier heeft de volgende voordelen:

* Hiermee kan de gebruiker aangepaste gegevens in een formulier bekijken.
* Hiermee vermindert u de hoeveelheid die de gebruiker invoert om een formulier in te vullen.
* Zorgt voor gegevensintegriteit door controle te hebben over waar de gegevens worden geplaatst.

De volgende twee XML-gegevensbronnen kunnen een formulier vooraf invullen:

* Een XDP-gegevensbron, te weten XML die voldoet aan de XFA-syntaxis (of XFDF-gegevens voor het vooraf invullen van een formulier dat is gemaakt met Acrobat).
* Een willekeurige XML-gegevensbron die naam/waardeparen bevat die overeenkomen met de veldnamen van het formulier (in de voorbeelden in deze sectie wordt een willekeurige XML-gegevensbron gebruikt).

Er moet een XML-element aanwezig zijn voor elk formulierveld dat u vooraf wilt invullen. De naam van het XML-element moet overeenkomen met de veldnaam. Een XML-element wordt genegeerd als het niet overeenkomt met een formulierveld of als de naam van het XML-element niet overeenkomt met de veldnaam. Het is niet nodig de volgorde aan te passen waarin de XML-elementen worden weergegeven, zolang alle XML-elementen zijn opgegeven.

Wanneer u een formulier invult dat al gegevens bevat, moet u opgeven welke gegevens al in de XML-gegevensbron worden weergegeven. Stel dat een formulier met tien velden gegevens bevat in vier velden. Ga er vervolgens van uit dat u de resterende zes velden vooraf wilt invullen. In dit geval moet u 10 XML-elementen opgeven in de XML-gegevensbron die wordt gebruikt om het formulier vooraf in te vullen. Als u slechts zes elementen opgeeft, zijn de oorspronkelijke vier velden leeg.

U kunt bijvoorbeeld een formulier zoals het voorbeeldbevestigingsformulier vooraf invullen. (Zie &#39;Bevestigingsformulier&#39; in Interactieve PDF forms [](/help/forms/developing/rendering-interactive-pdf-forms.md)renderen.)

Als u het voorbeeldbevestigingsformulier vooraf wilt invullen, moet u een XML-gegevensbron maken die drie XML-elementen bevat die overeenkomen met de drie velden in het formulier. Dit formulier bevat de volgende drie velden: `FirstName`, `LastName`en `Amount`. De eerste stap bestaat uit het maken van een XML-gegevensbron die XML-elementen bevat die overeenkomen met de velden in het formulierontwerp. De volgende stap bestaat uit het toewijzen van gegevenswaarden aan de XML-elementen, zoals in de volgende XML-code wordt getoond.

```xml
     <Untitled>
         <FirstName>Jerry</FirstName>
         <LastName>Johnson</LastName>
         <Amount>250000</Amount>
     </Untitled>
```

Nadat u het bevestigingsformulier vooraf hebt ingevuld met deze XML-gegevensbron en het formulier hebt gegenereerd, worden de gegevenswaarden weergegeven die u aan de XML-elementen hebt toegewezen, zoals in het volgende diagram wordt getoond.

![pf_pf_confirmxml3](assets/pf_pf_confirmxml3.png)

### Formulieren vooraf invullen met stroombare indelingen {#prepopulating_forms_with_flowable_layouts-1}

Formulieren met stroombare indelingen zijn handig om een onbepaalde hoeveelheid gegevens weer te geven aan gebruikers. Omdat de indeling van het formulier automatisch wordt aangepast aan de hoeveelheid samengevoegde gegevens, hoeft u niet vooraf een vaste indeling of een vast aantal pagina&#39;s voor het formulier vast te stellen, zoals u moet doen met een formulier met een vaste indeling.

Een formulier wordt meestal gevuld met gegevens die tijdens runtime worden verkregen. Hierdoor kunt u een formulier vooraf invullen door een XML-gegevensbron in het geheugen te maken en de gegevens rechtstreeks in de XML-gegevensbron in het geheugen te plaatsen.

Overweeg een webtoepassing, zoals een onlinewinkel. Nadat een online winkelier de aanschaf van items heeft voltooid, worden alle aangeschafte items in een XML-gegevensbron in het geheugen geplaatst die wordt gebruikt om een formulier vooraf in te vullen. Het volgende diagram toont dit proces, dat in de lijst na het diagram wordt verklaard.

![pf_pf_finsrv_webapp_v1](assets/pf_pf_finsrv_webapp_v1.png)

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
   <td><p>Een gebruiker koopt objecten aan in een online winkel op internet. </p></td>
  </tr>
  <tr>
   <td><p>2</p></td>
   <td><p>Nadat de gebruiker klaar is met het aanschaffen van items en op de knop Verzenden klikt, wordt een XML-gegevensbron in het geheugen gemaakt. Aangeschafte items en gebruikersgegevens worden in de XML-gegevensbron in het geheugen geplaatst. </p></td>
  </tr>
  <tr>
   <td><p>3</p></td>
   <td><p>De XML-gegevensbron wordt gebruikt om een inkooporderformulier vooraf in te vullen (een voorbeeld van dit formulier wordt in deze tabel weergegeven). </p></td>
  </tr>
  <tr>
   <td><p>4</p></td>
   <td><p>Het inkooporderformulier wordt weergegeven in de webbrowser van de client. </p></td>
  </tr>
 </tbody>
</table>

In het volgende diagram ziet u een voorbeeld van een inkooporderformulier. De informatie in de tabel kan worden aangepast aan het aantal records in de XML-gegevens.

![pf_pf_poform](assets/pf_pf_poform.png)

>[!NOTE]
>
>Een formulier kan vooraf worden ingevuld met gegevens uit andere bronnen, zoals een ondernemingsdatabase of externe toepassingen.

### Overwegingen bij het ontwerpen van formulieren {#form-design-considerations}

Formulieren met stroombare indelingen zijn gebaseerd op formulierontwerpen die zijn gemaakt in Designer. Een formulierontwerp bevat een set regels voor de indeling, presentatie en gegevensvastlegging, inclusief het berekenen van waarden op basis van de gebruikersinvoer. De regels worden toegepast wanneer gegevens in een formulier worden ingevoerd. Velden die aan een formulier worden toegevoegd, zijn subformulieren die zich binnen het formulierontwerp bevinden. In het inkooporderformulier dat in het vorige diagram wordt weergegeven, is elke regel bijvoorbeeld een subformulier. Zie Een inkooporderformulier met een stroombare indeling [](https://www.adobe.com/go/learn_aemforms_qs_poformflowable_9)maken voor informatie over het maken van een formulierontwerp dat subformulieren bevat.

### Werken met gegevenssubgroepen {#understanding-data-subgroups}

Een XML-gegevensbron wordt gebruikt om formulieren vooraf in te vullen met vaste indelingen en stroombare indelingen. Het verschil is echter dat een XML-gegevensbron die een formulier met een stroombare indeling vooraf invult, herhalende XML-elementen bevat die worden gebruikt om vooraf subformulieren in te vullen die in het formulier worden herhaald. Deze herhaalde XML-elementen worden gegevenssubgroepen genoemd.

Een XML-gegevensbron die wordt gebruikt om de inkoopordervorm die in het vorige diagram wordt weergegeven, vooraf in te vullen, bevat vier herhalende gegevenssubgroepen. Elke gegevenssubgroep komt overeen met een aangeschaft item. De aangeschafte items zijn een monitor, een bureaulamp, een telefoon en een adresboek.

De volgende XML-gegevensbron wordt gebruikt om het inkooporderformulier vooraf in te vullen.

```xml
     <header>
         <!-- XML elements used to prepopulate non-repeating fields such as address
         <!and city
         <txtPONum>8745236985</txtPONum>
         <dtmDate>2004-02-08</dtmDate>
         <txtOrderedByCompanyName>Any Company Name</txtOrderedByCompanyName>
         <txtOrderedByAddress>555, Any Blvd.</txtOrderedByAddress>
         <txtOrderedByCity>Any City</txtOrderedByCity>
         <txtOrderedByStateProv>ST</txtOrderedByStateProv>
         <txtOrderedByZipCode>12345</txtOrderedByZipCode>
         <txtOrderedByCountry>Any Country</txtOrderedByCountry>
         <txtOrderedByPhone>(123) 456-7890</txtOrderedByPhone>
         <txtOrderedByFax>(123) 456-7899</txtOrderedByFax>
         <txtOrderedByContactName>Contact Name</txtOrderedByContactName>
         <txtDeliverToCompanyName>Any Company Name</txtDeliverToCompanyName>
         <txtDeliverToAddress>7895, Any Street</txtDeliverToAddress>
         <txtDeliverToCity>Any City</txtDeliverToCity>
         <txtDeliverToStateProv>ST</txtDeliverToStateProv>
         <txtDeliverToZipCode>12346</txtDeliverToZipCode>
         <txtDeliverToCountry>Any Country</txtDeliverToCountry>
         <txtDeliverToPhone>(123) 456-7891</txtDeliverToPhone>
         <txtDeliverToFax>(123) 456-7899</txtDeliverToFax>
         <txtDeliverToContactName>Contact Name</txtDeliverToContactName>
     </header>
     <detail>
         <!-- A data subgroup that contains information about the monitor>
         <txtPartNum>00010-100</txtPartNum>
         <txtDescription>Monitor</txtDescription>
         <numQty>1</numQty>
         <numUnitPrice>350.00</numUnitPrice>
     </detail>
     <detail>
         <!-- A data subgroup that contains information about the desk lamp>
         <txtPartNum>00010-200</txtPartNum>
         <txtDescription>Desk lamps</txtDescription>
         <numQty>3</numQty>
         <numUnitPrice>55.00</numUnitPrice>
     </detail>
     <detail>
         <!-- A data subgroup that contains information about the Phone>
             <txtPartNum>00025-275</txtPartNum>
             <txtDescription>Phone</txtDescription>
             <numQty>5</numQty>
             <numUnitPrice>85.00</numUnitPrice>
     </detail>
     <detail>
         <!-- A data subgroup that contains information about the address book>
         <txtPartNum>00300-896</txtPartNum>
         <txtDescription>Address book</txtDescription>
         <numQty>2</numQty>
         <numUnitPrice>15.00</numUnitPrice>
     </detail>
```

Elke gegevenssubgroep bevat vier XML-elementen die overeenkomen met deze informatie:

* Artikelonderdeelnummer
* Objectbeschrijving
* Aantal objecten
* Eenheidsprijs

De naam van het bovenliggende XML-element van een gegevenssubgroep moet overeenkomen met de naam van het subformulier dat zich in het formulierontwerp bevindt. In het vorige diagram ziet u bijvoorbeeld dat de naam van het bovenliggende XML-element van de gegevenssubgroep `detail`is. Dit komt overeen met de naam van het subformulier in het formulierontwerp waarop het inkooporderformulier is gebaseerd. Als de naam van het bovenliggende XML-element van de gegevenssubgroep en het subformulier niet overeenkomen, wordt een formulier op de server niet vooraf ingevuld.

Elke gegevenssubgroep moet XML-elementen bevatten die overeenkomen met de veldnamen in het subformulier. Het `detail` subformulier in het formulierontwerp bevat de volgende velden:

* txtPartNum
* txtDescription
* numQty
* numUnitPrice

>[!NOTE]
>
>Als u probeert een formulier vooraf in te vullen met een gegevensbron die herhaalde XML-elementen bevat en u stelt de `RenderAtClient` optie in op `No`, wordt alleen de eerste gegevensrecord in het formulier samengevoegd. Als u wilt dat alle gegevensrecords in het formulier worden samengevoegd, stelt u de waarde in `RenderAtClient` op `Yes`. Zie Formulieren `RenderAtClient` renderen op de client [voor informatie over de](/help/forms/developing/rendering-forms-client.md)optie.

>[!NOTE]
>
>Voor meer informatie over de dienst van Vormen, zie de Verwijzing van de [Diensten voor AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary-of-steps}

Als u een formulier vooraf wilt invullen met een stroombare indeling, voert u de volgende taken uit:

1. Inclusief projectbestanden.
1. Maak een XML-gegevensbron in het geheugen.
1. Zet de XML-gegevensbron om.
1. Een vooraf ingevuld formulier weergeven.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

**Een XML-gegevensbron in het geheugen maken**

Met `org.w3c.dom` klassen kunt u een XML-gegevensbron in het geheugen maken om een formulier vooraf in te vullen met een stroombare indeling. U moet gegevens in een XML-gegevensbron plaatsen die voldoet aan het formulier. Zie [Werken met gegevenssubgroepen](#understanding-data-subgroups)voor informatie over de relatie tussen een formulier met een stroombare indeling en de XML-gegevensbron.

**De XML-gegevensbron converteren**

Een XML-gegevensbron in het geheugen die met behulp van `org.w3c.dom` klassen is gemaakt, kan worden omgezet in een `com.adobe.idp.Document` object voordat het kan worden gebruikt om een formulier vooraf in te vullen. Een XML-gegevensbron in het geheugen kan worden geconverteerd met Java XML-transformatieklassen.

>[!NOTE]
>
>Als u een formulier vooraf invult met de WSDL van de Forms-service, moet u een `org.w3c.dom.Document` object converteren naar een `BLOB` object.

**Een vooraf ingevuld formulier renderen**

U kunt een vooraf ingevuld formulier net als een ander formulier weergeven. Het enige verschil is dat u het `com.adobe.idp.Document` object dat de XML-gegevensbron bevat, gebruikt om het formulier vooraf in te vullen.

**Zie ook**

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Forms Service API, snel aan de slag](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

[Interactieve PDF forms renderen](/help/forms/developing/rendering-interactive-pdf-forms.md)

[Webtoepassingen maken die formulieren renderen](/help/forms/developing/creating-web-applications-renders-forms.md)

### Formulieren vooraf invullen met de Java API {#prepopulating-forms-using-the-java-api}

Voer de volgende stappen uit om een formulier vooraf in te vullen met een stroombare indeling met de API voor formulieren (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden, zoals adobe-forms-client.jar, op in het klassenpad van uw Java-project. Zie [Including AEM Forms Java library files](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)voor informatie over de locatie van deze bestanden.

1. Een XML-gegevensbron in het geheugen maken

   * Maak een Java- `DocumentBuilderFactory` object door de `DocumentBuilderFactory` methode `newInstance` class aan te roepen.
   * Maak een Java- `DocumentBuilder` object door de `DocumentBuilderFactory` methode van het `newDocumentBuilder` object aan te roepen.
   * Roep de `DocumentBuilder` methode van het `newDocument` object aan om een `org.w3c.dom.Document` object te instantiëren.
   * Maak het hoofdelement van de XML-gegevensbron door de `org.w3c.dom.Document` methode van het `createElement` object aan te roepen. Hiermee wordt een `Element` object gemaakt dat het basiselement vertegenwoordigt. Geef een tekenreekswaarde die de naam van het element vertegenwoordigt, door aan de `createElement` methode. Kiezen naar de geretourneerde waarde `Element`. Voeg vervolgens het hoofdelement aan het document toe door de methode van het `Document` `appendChild` object aan te roepen en geef het hoofdelement als een argument door. Deze toepassingslogica wordt in de volgende coderegels getoond:

      ` Element root = (Element)document.createElement("transaction");  document.appendChild(root);`

   * Maak het koptekstelement van de XML-gegevensbron door de `Document` methode van het `createElement` object aan te roepen. Geef een tekenreekswaarde die de naam van het element vertegenwoordigt, door aan de `createElement` methode. Kiezen naar de geretourneerde waarde `Element`. Voeg vervolgens het koptekstelement aan het hoofdelement toe door de methode van het `root` `appendChild` object aan te roepen en geef het kopelement als een argument door. De XML-elementen die aan het koptekstelement worden toegevoegd, komen overeen met het statische gedeelte van het formulier. De volgende coderegels tonen deze toepassingslogica:

      ` Element header = (Element)document.createElement("header");  root.appendChild(header);`

   * Maak een onderliggend element dat tot het koptekstelement behoort door de methode van het `Document` `createElement` object aan te roepen en geef een tekenreekswaarde door die de naam van het element vertegenwoordigt. Kiezen naar de geretourneerde waarde `Element`. Stel vervolgens een waarde voor het onderliggende element in door de bijbehorende `appendChild` methode aan te roepen en geef de methode van het `Document` object als een argument door `createTextNode` . Geef een tekenreekswaarde op die als waarde van het onderliggende element wordt weergegeven. Voeg ten slotte het onderliggende element toe aan het koptekstelement door de methode van het koptekstelement aan te roepen en geef het onderliggende element als een argument door. `appendChild` De volgende coderegels tonen deze toepassingslogica:

      ` Element poNum= (Element)document.createElement("txtPONum");  poNum.appendChild(document.createTextNode("8745236985"));  header.appendChild(LastName);`


   * Voeg alle resterende elementen aan het koptekstelement toe door de laatste substap te herhalen voor elk veld in het statische gedeelte van het formulier (in het XML-gegevensbrondiagram worden deze velden weergegeven in sectie A. (Zie [Werken met gegevenssubgroepen](#understanding-data-subgroups).)
   * Maak het detailelement van de XML-gegevensbron door de `Document` `createElement` methode van het object aan te roepen. Geef een tekenreekswaarde die de naam van het element vertegenwoordigt, door aan de `createElement` methode. Kiezen naar de geretourneerde waarde `Element`. Voeg vervolgens het detailelement toe aan het hoofdelement door de methode van het `root` `appendChild` object aan te roepen en geef het detailelementobject door als een argument. De XML-elementen die aan het detailelement worden toegevoegd, komen overeen met het dynamische gedeelte van het formulier. De volgende coderegels tonen deze toepassingslogica:

      ` Element detail = (Element)document.createElement("detail");  root.appendChild(detail);`

   * Maak een onderliggend element dat tot het detailelement behoort door de methode van het `Document` `createElement` object aan te roepen en geef een tekenreekswaarde door die de naam van het element vertegenwoordigt. Kiezen naar de geretourneerde waarde `Element`. Stel vervolgens een waarde voor het onderliggende element in door de bijbehorende `appendChild` methode aan te roepen en geef de methode van het `Document` object als een argument door `createTextNode` . Geef een tekenreekswaarde op die als waarde van het onderliggende element wordt weergegeven. Ten slotte voegt u het onderliggende element toe aan het detailelement door de methode van het detailelement aan te roepen en geeft u het onderliggende element als een argument door. `appendChild` De volgende coderegels tonen deze toepassingslogica:

      ` Element txtPartNum = (Element)document.createElement("txtPartNum");  txtPartNum.appendChild(document.createTextNode("00010-100"));  detail.appendChild(txtPartNum);`

   * Herhaal de laatste substap voor alle XML-elementen die aan het detailelement moeten worden toegevoegd. Als u de XML-gegevensbron correct wilt maken die wordt gebruikt om het inkooporderformulier te vullen, moet u de volgende XML-elementen aan het detailelement toevoegen: `txtDescription`, `numQty`en `numUnitPrice`.
   * Herhaal de laatste twee substappen voor alle gegevensitems die worden gebruikt om het formulier vooraf in te vullen.

1. De XML-gegevensbron converteren

   * Maak een `javax.xml.transform.Transformer` object door de statische `javax.xml.transform.Transformer` methode van het `newInstance` object aan te roepen.
   * Maak een `Transformer` object door de `TransformerFactory` methode van het `newTransformer` object aan te roepen.
   * Maak een `ByteArrayOutputStream` object met de constructor ervan.
   * Maak een `javax.xml.transform.dom.DOMSource` object door de constructor ervan te gebruiken en het `org.w3c.dom.Document` object door te geven dat in stap 1 is gemaakt.
   * Maak een `javax.xml.transform.dom.DOMSource` object door de constructor ervan te gebruiken en het `ByteArrayOutputStream` object door te geven.
   * Vul het Java- `ByteArrayOutputStream` object door de `javax.xml.transform.Transformer` methode van het `transform` object aan te roepen en de `javax.xml.transform.dom.DOMSource` en de `javax.xml.transform.stream.StreamResult` objecten door te geven.
   * Maak een bytearray en wijs de grootte van het `ByteArrayOutputStream` object toe aan de bytearray.
   * Vul de bytearray door de `ByteArrayOutputStream` `toByteArray` methode van het object aan te roepen.
   * Maak een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en de bytearray door te geven.

1. Een vooraf ingevuld formulier renderen

   Roep de methode van het `FormsServiceClient` `renderPDFForm` object aan en geef de volgende waarden door:

   * Een tekenreekswaarde die de naam van het formulierontwerp opgeeft, inclusief de bestandsnaamextensie.
   * Een `com.adobe.idp.Document` object dat gegevens bevat die met het formulier moeten worden samengevoegd. Zorg ervoor dat u het `com.adobe.idp.Document` object gebruikt dat u in stap 1 en 2 hebt gemaakt.
   * Een `PDFFormRenderSpec` object dat uitvoeringsopties opslaat.
   * Een `URLSpec` object dat URI-waarden bevat die door de service Forms worden vereist.
   * Een `java.util.HashMap` object dat bestandsbijlagen opslaat. Dit is een optionele parameter en u kunt opgeven `null` of u geen bestanden aan het formulier wilt koppelen.

   De `renderPDFForm` methode retourneert een `FormsResult` object dat een formuliergegevensstroom bevat die naar de webbrowser van de client moet worden geschreven.

   * Maak een `javax.servlet.ServletOutputStream` object dat wordt gebruikt om een formuliergegevensstroom naar de webbrowser van de client te verzenden.
   * Maak een `com.adobe.idp.Document` object door de `FormsResult` methode van het `getOutputContent` object aan te roepen.
   * Maak een `java.io.InputStream` object door de `com.adobe.idp.Document` methode van het `getInputStream` object aan te roepen.
   * Maak een bytearray die deze met de formuliergegevensstroom vult door de methode van het `InputStream` `read` object aan te roepen en de bytearray als een argument door te geven.
   * Roep de `javax.servlet.ServletOutputStream` methode van het `write` object aan om de formuliergegevensstroom naar de webbrowser van de client te verzenden. Geef de bytearray door aan de `write` methode.


**Zie ook**

[Snel starten (SOAP-modus): Formulieren met stroombare indelingen vooraf invullen met de Java API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-prepopulating-forms-with-flowable-layouts-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Formulieren vooraf invullen met de webservice-API {#prepopulating-forms-using-the-web-service-api}

Voer de volgende stappen uit om een formulier met een stroombare indeling vooraf in te vullen met de API voor formulieren (webservice):

1. Projectbestanden opnemen

   * Maak Java-proxyklassen die de Forms service WSDL gebruiken. (Zie Java-proxyklassen [maken met Apache Axis](/help/forms/developing/invoking-aem-forms-using-web.md#creating-java-proxy-classes-using-apache-axis).)
   * Neem de Java-proxyklassen op in het klassepad.

1. Een XML-gegevensbron in het geheugen maken

   * Maak een Java- `DocumentBuilderFactory` object door de `DocumentBuilderFactory` methode `newInstance` class aan te roepen.
   * Maak een Java- `DocumentBuilder` object door de `DocumentBuilderFactory` methode van het `newDocumentBuilder` object aan te roepen.
   * Roep de `DocumentBuilder` methode van het `newDocument` object aan om een `org.w3c.dom.Document` object te instantiëren.
   * Maak het hoofdelement van de XML-gegevensbron door de `org.w3c.dom.Document` methode van het `createElement` object aan te roepen. Hiermee wordt een `Element` object gemaakt dat het basiselement vertegenwoordigt. Geef een tekenreekswaarde die de naam van het element vertegenwoordigt, door aan de `createElement` methode. Kiezen naar de geretourneerde waarde `Element`. Voeg vervolgens het hoofdelement aan het document toe door de methode van het `Document` `appendChild` object aan te roepen en geef het hoofdelement als een argument door. De volgende coderegels tonen deze toepassingslogica:

      ` Element root = (Element)document.createElement("transaction");  document.appendChild(root);`

   * Maak het koptekstelement van de XML-gegevensbron door de `Document` methode van het `createElement` object aan te roepen. Geef een tekenreekswaarde die de naam van het element vertegenwoordigt, door aan de `createElement` methode. Kiezen naar de geretourneerde waarde `Element`. Voeg vervolgens het koptekstelement aan het hoofdelement toe door de methode van het `root` `appendChild` object aan te roepen en geef het kopelement als een argument door. De XML-elementen die aan het koptekstelement worden toegevoegd, komen overeen met het statische gedeelte van het formulier. De volgende coderegels tonen deze toepassingslogica:

      ` Element header = (Element)document.createElement("header");  root.appendChild(header);`

   * Maak een onderliggend element dat tot het koptekstelement behoort door de methode van het `Document` `createElement` object aan te roepen en geef een tekenreekswaarde door die de naam van het element vertegenwoordigt. Kiezen naar de geretourneerde waarde `Element`. Stel vervolgens een waarde voor het onderliggende element in door de bijbehorende `appendChild` methode aan te roepen en geef de methode van het `Document` object als een argument door `createTextNode` . Geef een tekenreekswaarde op die als waarde van het onderliggende element wordt weergegeven. Voeg ten slotte het onderliggende element toe aan het koptekstelement door de methode van het koptekstelement aan te roepen en geef het onderliggende element als een argument door. `appendChild` Deze toepassingslogica wordt in de volgende coderegels getoond:

      ` Element poNum= (Element)document.createElement("txtPONum");  poNum.appendChild(document.createTextNode("8745236985"));  header.appendChild(LastName);`

   * Voeg alle resterende elementen aan het koptekstelement toe door de laatste substap te herhalen voor elk veld in het statische gedeelte van het formulier (in het XML-gegevensbrondiagram worden deze velden weergegeven in sectie A. (Zie [Werken met gegevenssubgroepen](#understanding-data-subgroups).)
   * Maak het detailelement van de XML-gegevensbron door de `Document` `createElement` methode van het object aan te roepen. Geef een tekenreekswaarde die de naam van het element vertegenwoordigt, door aan de `createElement` methode. Kiezen naar de geretourneerde waarde `Element`. Voeg vervolgens het detailelement toe aan het hoofdelement door de methode van het `root` `appendChild` object aan te roepen en geef het detailelementobject door als een argument. De XML-elementen die aan het detailelement worden toegevoegd, komen overeen met het dynamische gedeelte van het formulier. Deze toepassingslogica wordt in de volgende coderegels getoond:

      ` Element detail = (Element)document.createElement("detail");  root.appendChild(detail);`

   * Maak een onderliggend element dat tot het detailelement behoort door de methode van het `Document` `createElement` object aan te roepen en geef een tekenreekswaarde door die de naam van het element vertegenwoordigt. Kiezen naar de geretourneerde waarde `Element`. Stel vervolgens een waarde voor het onderliggende element in door de bijbehorende `appendChild` methode aan te roepen en geef de methode van het `Document` object als een argument door `createTextNode` . Geef een tekenreekswaarde op die als waarde van het onderliggende element wordt weergegeven. Ten slotte voegt u het onderliggende element toe aan het detailelement door de methode van het detailelement aan te roepen en geeft u het onderliggende element als een argument door. `appendChild` Deze toepassingslogica wordt in de volgende coderegels getoond:

      ` Element txtPartNum = (Element)document.createElement("txtPartNum");  txtPartNum.appendChild(document.createTextNode("00010-100"));  detail.appendChild(txtPartNum);`

   * Herhaal de laatste substap voor alle XML-elementen die aan het detailelement moeten worden toegevoegd. Als u de XML-gegevensbron correct wilt maken die wordt gebruikt om het inkooporderformulier te vullen, moet u de volgende XML-elementen aan het detailelement toevoegen: `txtDescription`, `numQty`en `numUnitPrice`.
   * Herhaal de laatste twee substappen voor alle gegevensitems die worden gebruikt om het formulier vooraf in te vullen.

1. De XML-gegevensbron converteren

   * Maak een `javax.xml.transform.Transformer` object door de statische `javax.xml.transform.Transformer` methode van het `newInstance` object aan te roepen.
   * Maak een `Transformer` object door de `TransformerFactory` methode van het `newTransformer` object aan te roepen.
   * Maak een `ByteArrayOutputStream` object met de constructor ervan.
   * Maak een `javax.xml.transform.dom.DOMSource` object door de constructor ervan te gebruiken en het `org.w3c.dom.Document` object door te geven dat in stap 1 is gemaakt.
   * Maak een `javax.xml.transform.dom.DOMSource` object door de constructor ervan te gebruiken en het `ByteArrayOutputStream` object door te geven.
   * Vul het Java- `ByteArrayOutputStream` object door de `javax.xml.transform.Transformer` methode van het `transform` object aan te roepen en de `javax.xml.transform.dom.DOMSource` en de `javax.xml.transform.stream.StreamResult` objecten door te geven.
   * Maak een bytearray en wijs de grootte van het `ByteArrayOutputStream` object toe aan de bytearray.
   * Vul de bytearray door de `ByteArrayOutputStream` `toByteArray` methode van het object aan te roepen.
   * Maak een `BLOB` object met behulp van de constructor en activeer de `setBinaryData` methode van het object en geef de bytearray door.

1. Een vooraf ingevuld formulier renderen

   Roep de methode van het `FormsService` `renderPDFForm` object aan en geef de volgende waarden door:

   * Een tekenreekswaarde die de naam van het formulierontwerp opgeeft, inclusief de bestandsnaamextensie.
   * Een `BLOB` object dat gegevens bevat die met het formulier moeten worden samengevoegd. Zorg ervoor dat u het `BLOB` object gebruikt dat in stap 1 en 2 is gemaakt.
   * Een `PDFFormRenderSpecc` object dat uitvoeringsopties opslaat. Zie [AEM Forms API Reference](https://www.adobe.com/go/learn_aemforms_javadocs_63_en)voor meer informatie.
   * Een `URLSpec` object dat URI-waarden bevat die door de service Forms worden vereist.
   * Een `java.util.HashMap` object dat bestandsbijlagen opslaat. Dit is een optionele parameter en u kunt opgeven `null` of u geen bestanden aan het formulier wilt koppelen.
   * Een leeg `com.adobe.idp.services.holders.BLOBHolder` object dat door de methode wordt gevuld. Hiermee slaat u het gerenderde PDF-formulier op.
   * Een leeg `javax.xml.rpc.holders.LongHolder` object dat door de methode wordt gevuld. (In dit argument wordt het aantal pagina&#39;s in het formulier opgeslagen).
   * Een leeg `javax.xml.rpc.holders.StringHolder` object dat door de methode wordt gevuld. (In dit argument wordt de waarde van de landinstelling opgeslagen.)
   * Een leeg `com.adobe.idp.services.holders.FormsResultHolder` object dat de resultaten van deze bewerking zal bevatten.

   De `renderPDFForm` methode vult het `com.adobe.idp.services.holders.FormsResultHolder` object dat als laatste argumentwaarde wordt doorgegeven, met een formuliergegevensstroom die naar de webbrowser van de client moet worden geschreven.

   * Maak een `FormResult` object door de waarde van het `com.adobe.idp.services.holders.FormsResultHolder` `value` gegevenslid van het object op te halen.
   * Maak een `BLOB` object dat formuliergegevens bevat door de `FormsResult` methode van het `getOutputContent` object aan te roepen.
   * Haal het inhoudstype van het `BLOB` object op door de `getContentType` methode ervan aan te roepen.
   * Stel het inhoudstype van het `javax.servlet.http.HttpServletResponse` object in door de bijbehorende `setContentType` methode op te roepen en het inhoudstype van het `BLOB` object door te geven.
   * Maak een `javax.servlet.ServletOutputStream` object dat wordt gebruikt om de gegevensstroom van het formulier naar de webbrowser van de client te schrijven door de `javax.servlet.http.HttpServletResponse` methode van het `getOutputStream` object aan te roepen.
   * Maak een bytearray en vul deze door de `BLOB` methode van het `getBinaryData` object aan te roepen. Hierdoor wordt de inhoud van het `FormsResult` object toegewezen aan de bytearray.
   * Roep de `javax.servlet.http.HttpServletResponse` methode van het `write` object aan om de formuliergegevensstroom naar de webbrowser van de client te verzenden. Geef de bytearray door aan de `write` methode.

   >[!NOTE]
   >
   >De `renderPDFForm` methode vult het `com.adobe.idp.services.holders.FormsResultHolder` object dat als laatste argumentwaarde wordt doorgegeven, met een formuliergegevensstroom die naar de webbrowser van de client moet worden geschreven.

**Zie ook**

[AEM Forms aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

