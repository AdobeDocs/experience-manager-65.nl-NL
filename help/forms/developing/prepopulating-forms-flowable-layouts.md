---
title: Forms vooraf vullen met stroombare indelingen
description: Formulieren vooraf invullen met een stroombare indeling om gegevens weer te geven aan gebruikers in een gegenereerd formulier met de Java API en de webservice-API.
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
exl-id: ff087084-fb1c-43a4-ae54-cc77eb862493
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Document Services,APIs & Integrations
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '3478'
ht-degree: 0%

---

# Forms vooraf vullen met stroombare indelingen {#prepopulating-forms-with-flowable-layouts1}

## Forms vooraf vullen met stroombare indelingen {#prepopulating-forms-with-flowable-layouts2}

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

U kunt bijvoorbeeld een formulier zoals het voorbeeldbevestigingsformulier vooraf invullen. (Zie &quot;Bevestigingsvorm&quot;in [ teruggevend Interactieve PDF forms ](/help/forms/developing/rendering-interactive-pdf-forms.md).)

Als u het voorbeeldbevestigingsformulier vooraf wilt invullen, moet u een XML-gegevensbron maken die drie XML-elementen bevat die overeenkomen met de drie velden in het formulier. Dit formulier bevat de volgende drie velden: `FirstName` , `LastName` en `Amount` . De eerste stap bestaat uit het maken van een XML-gegevensbron die XML-elementen bevat die overeenkomen met de velden in het formulierontwerp. De volgende stap bestaat uit het toewijzen van gegevenswaarden aan de XML-elementen, zoals in de volgende XML-code wordt getoond.

```xml
     <Untitled>
         <FirstName>Jerry</FirstName>
         <LastName>Johnson</LastName>
         <Amount>250000</Amount>
     </Untitled>
```

Nadat u het bevestigingsformulier vooraf hebt ingevuld met deze XML-gegevensbron en het formulier hebt gegenereerd, worden de gegevenswaarden weergegeven die u aan de XML-elementen hebt toegewezen, zoals in het volgende diagram wordt getoond.

![ pf_pf_confirmxml3 ](assets/pf_pf_confirmxml3.png)

### Formulieren vooraf invullen met stroombare indelingen {#prepopulating_forms_with_flowable_layouts-1}

Forms met stroombare indelingen is handig om een onbepaalde hoeveelheid gegevens weer te geven aan gebruikers. Omdat de indeling van het formulier automatisch wordt aangepast aan de hoeveelheid samengevoegde gegevens, hoeft u niet vooraf een vaste indeling of een vast aantal pagina&#39;s voor het formulier vast te stellen, zoals u moet doen met een formulier met een vaste indeling.

Een formulier wordt meestal gevuld met gegevens die tijdens runtime worden verkregen. Hierdoor kunt u een formulier vooraf invullen door een XML-gegevensbron in het geheugen te maken en de gegevens rechtstreeks in de XML-gegevensbron in het geheugen te plaatsen.

Overweeg een webtoepassing, zoals een onlinewinkel. Nadat een online winkelier de aanschaf van items heeft voltooid, worden alle aangeschafte items in een XML-gegevensbron in het geheugen geplaatst die wordt gebruikt om een formulier vooraf in te vullen. Het volgende diagram toont dit proces, dat in de lijst na het diagram wordt verklaard.

![ pf_pf_finsrv_webapp_v1 ](assets/pf_pf_finsrv_webapp_v1.png)

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

![ pf_pf_poform ](assets/pf_pf_poform.png)

>[!NOTE]
>
>Een formulier kan vooraf worden ingevuld met gegevens uit andere bronnen, zoals een ondernemingsdatabase of externe toepassingen.

### Overwegingen bij het ontwerpen van formulieren {#form-design-considerations}

Forms met stroombare indelingen is gebaseerd op formulierontwerpen die in Designer zijn gemaakt. Een formulierontwerp bevat een set regels voor de indeling, presentatie en gegevensvastlegging, inclusief het berekenen van waarden op basis van de gebruikersinvoer. De regels worden toegepast wanneer gegevens in een formulier worden ingevoerd. Velden die aan een formulier worden toegevoegd, zijn subformulieren die zich binnen het formulierontwerp bevinden. In het inkooporderformulier dat in het vorige diagram wordt weergegeven, is elke regel bijvoorbeeld een subformulier. Voor informatie over het creëren van een vormontwerp dat subforms bevat, zie [ Creërend een vorm van de kooporde die een stroombare lay-out ](https://www.adobe.com/go/learn_aemforms_qs_poformflowable_9) heeft.

### Gegevensubgroepen {#understanding-data-subgroups}

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

De naam van het bovenliggende XML-element van een gegevenssubgroep moet overeenkomen met de naam van het subformulier in het formulierontwerp. In het vorige diagram ziet u bijvoorbeeld dat de naam van het bovenliggende XML-element van de gegevenssubgroep `detail` is. Dit komt overeen met de naam van het subformulier in het formulierontwerp waarop het inkooporderformulier is gebaseerd. Als de naam van het bovenliggende XML-element van de gegevenssubgroep en het subformulier niet overeenkomen, wordt een formulier op de server niet vooraf ingevuld.

Elke gegevenssubgroep moet XML-elementen bevatten die overeenkomen met de veldnamen in het subformulier. Het subformulier `detail` in het formulierontwerp bevat de volgende velden:

* txtPartNum
* txtDescription
* numQty
* numUnitPrice

>[!NOTE]
>
>Als u probeert een formulier vooraf in te vullen met een gegevensbron die herhaalde XML-elementen bevat en u de optie `RenderAtClient` instelt op `No` , wordt alleen de eerste gegevensrecord in het formulier samengevoegd. Stel de `RenderAtClient` in op `Yes` om ervoor te zorgen dat alle gegevensrecords in het formulier worden samengevoegd. Voor informatie over de `RenderAtClient` optie, zie [ Renderen Forms bij de Cliënt ](/help/forms/developing/rendering-forms-client.md).

>[!NOTE]
>
>Voor meer informatie over de dienst van Forms, zie [ Verwijzing van de Diensten voor AEM Forms ](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary-of-steps}

Als u een formulier vooraf wilt invullen met een stroombare indeling, voert u de volgende taken uit:

1. Inclusief projectbestanden.
1. Maak een XML-gegevensbron in het geheugen.
1. Zet de XML-gegevensbron om.
1. Een vooraf ingevuld formulier weergeven.

**omvat projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

**omvat projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

**creeer een in-geheugen de gegevensbron van XML**

Met `org.w3c.dom` -klassen kunt u een XML-gegevensbron in het geheugen maken om een formulier vooraf in te vullen met een stroombare indeling. Plaats gegevens in een XML-gegevensbron die voldoet aan het formulier. Voor informatie over het verband tussen een vorm met een stroombare lay-out en de gegevensbron van XML, zie [ Begrijpend gegevenssubgroups ](#understanding-data-subgroups).

**zet de gegevensbron van XML** om

Een XML-gegevensbron in het geheugen die met `org.w3c.dom` -klassen is gemaakt, kan worden geconverteerd naar een `com.adobe.idp.Document` -object voordat het kan worden gebruikt om een formulier vooraf in te vullen. Een XML-gegevensbron in het geheugen kan worden geconverteerd met Java XML-transformatieklassen.

>[!NOTE]
>
>Als u de WSDL van de Forms-service gebruikt om een formulier vooraf in te vullen, moet u een `org.w3c.dom.Document` -object omzetten in een `BLOB` -object.

**teruggeeft een vooraf bevolkte vorm**

U kunt een vooraf ingevuld formulier net als een ander formulier weergeven. Het enige verschil is dat u het object `com.adobe.idp.Document` dat de XML-gegevensbron bevat, gebruikt om het formulier vooraf in te vullen.

**zie ook**

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Forms Service API Quick Start](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

[Interactieve PDF forms renderen](/help/forms/developing/rendering-interactive-pdf-forms.md)

[Webtoepassingen maken die Forms renderen](/help/forms/developing/creating-web-applications-renders-forms.md)

### Formulieren vooraf invullen met de Java API {#prepopulating-forms-using-the-java-api}

Voer de volgende stappen uit om een formulier met een stroombare indeling vooraf in te vullen met de Forms API (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden, zoals adobe-forms-client.jar, op in het klassepad van uw Java-project. Voor informatie over de plaats van deze dossiers, zie [ Inclusief de bibliotheekdossiers van AEM Forms Java ](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

1. Een XML-gegevensbron in het geheugen maken

   * Maak een Java `DocumentBuilderFactory` -object door de methode `DocumentBuilderFactory` class&#39; `newInstance` aan te roepen.
   * Maak een Java `DocumentBuilder` -object door de methode `DocumentBuilderFactory` object `newDocumentBuilder` aan te roepen.
   * Roep de methode `newDocument` van het `DocumentBuilder` -object aan om een `org.w3c.dom.Document` -object te instantiëren.
   * Maak het basiselement van de XML-gegevensbron door de methode `createElement` van het object `org.w3c.dom.Document` aan te roepen. Hiermee wordt een `Element` -object gemaakt dat het hoofdelement vertegenwoordigt. Geef een tekenreekswaarde die de naam van het element vertegenwoordigt, door aan de methode `createElement` . De geretourneerde waarde wordt gecast naar `Element` . Voeg vervolgens het hoofdelement aan het document toe door de methode `appendChild` van het `Document` -object aan te roepen en geef het hoofdelement als een argument door. Deze toepassingslogica wordt in de volgende coderegels getoond:

     ` Element root = (Element)document.createElement("transaction");  document.appendChild(root);`

   * Maak het headerelement van de XML-gegevensbron door de methode `createElement` van het object `Document` aan te roepen. Geef een tekenreekswaarde die de naam van het element vertegenwoordigt, door aan de methode `createElement` . De geretourneerde waarde wordt gecast naar `Element` . Voeg vervolgens het headerelement toe aan het hoofdelement door de methode `appendChild` van het `root` -object aan te roepen en geef het headerelement als argument door. De XML-elementen die aan het koptekstelement worden toegevoegd, komen overeen met het statische gedeelte van het formulier. De volgende coderegels tonen deze toepassingslogica:

     ` Element header = (Element)document.createElement("header");  root.appendChild(header);`

   * Maak een onderliggend element dat tot het koptekstelement behoort door de methode `createElement` van het object `Document` aan te roepen en geef een tekenreekswaarde door die de naam van het element vertegenwoordigt. De geretourneerde waarde wordt gecast naar `Element` . Stel vervolgens een waarde voor het onderliggende element in door de methode `appendChild` ervan aan te roepen en geef de methode `Document` object `createTextNode` als argument door. Geef een tekenreekswaarde op die als waarde van het onderliggende element wordt weergegeven. Voeg ten slotte het onderliggende element toe aan het koptekstelement door de methode `appendChild` van het koptekstelement aan te roepen en geef het onderliggende element als argument door. De volgende coderegels tonen deze toepassingslogica:

     ` Element poNum= (Element)document.createElement("txtPONum");  poNum.appendChild(document.createTextNode("8745236985"));  header.appendChild(LastName);`


   * Voeg alle resterende elementen aan het kopbalelement toe door laatste sub-stap voor elk gebied te herhalen dat in het statische gedeelte van de vorm verschijnt (in het gegevensbrondiagram van XML, worden deze gebieden getoond in sectie A. (Zie [ Begrijpend gegevenssubgroups ](#understanding-data-subgroups).)
   * Maak het detailelement van de XML-gegevensbron door de methode `createElement` van het object `Document` aan te roepen. Geef een tekenreekswaarde die de naam van het element vertegenwoordigt, door aan de methode `createElement` . De geretourneerde waarde wordt gecast naar `Element` . Voeg vervolgens het detailelement toe aan het hoofdelement door de methode `appendChild` van het `root` -object aan te roepen en geef het detailelementobject door als argument. De XML-elementen die aan het detailelement worden toegevoegd, komen overeen met het dynamische gedeelte van het formulier. De volgende coderegels tonen deze toepassingslogica:

     ` Element detail = (Element)document.createElement("detail");  root.appendChild(detail);`

   * Maak een onderliggend element dat tot het detailelement behoort door de methode `createElement` van het object `Document` aan te roepen en geef een tekenreekswaarde door die de naam van het element vertegenwoordigt. De geretourneerde waarde wordt gecast naar `Element` . Stel vervolgens een waarde voor het onderliggende element in door de methode `appendChild` ervan aan te roepen en geef de methode `Document` object `createTextNode` als argument door. Geef een tekenreekswaarde op die als waarde van het onderliggende element wordt weergegeven. Voeg ten slotte het onderliggende element toe aan het detailelement door de methode `appendChild` van het detailelement aan te roepen en geef het onderliggende element als argument door. De volgende coderegels tonen deze toepassingslogica:

     ` Element txtPartNum = (Element)document.createElement("txtPartNum");  txtPartNum.appendChild(document.createTextNode("00010-100"));  detail.appendChild(txtPartNum);`

   * Herhaal de laatste substap voor alle XML-elementen die aan het detailelement moeten worden toegevoegd. Als u de XML-gegevensbron correct wilt maken die wordt gebruikt om het inkooporderformulier te vullen, moet u de volgende XML-elementen aan het detailelement toevoegen: `txtDescription`, `numQty` en `numUnitPrice` .
   * Herhaal de laatste twee substappen voor alle gegevensitems die worden gebruikt om het formulier vooraf in te vullen.

1. De XML-gegevensbron converteren

   * Maak een `javax.xml.transform.Transformer` -object door de statische methode `javax.xml.transform.Transformer` van het object `newInstance` aan te roepen.
   * Maak een `Transformer` -object door de methode `TransformerFactory` object `newTransformer` aan te roepen.
   * Maak een `ByteArrayOutputStream` -object met behulp van de constructor.
   * Maak een `javax.xml.transform.dom.DOMSource` -object door de constructor ervan te gebruiken en het `org.w3c.dom.Document` -object door te geven dat in stap 1 is gemaakt.
   * Maak een `javax.xml.transform.dom.DOMSource` -object door de constructor ervan te gebruiken en het `ByteArrayOutputStream` -object door te geven.
   * Vul het Java `ByteArrayOutputStream` -object door de methode `javax.xml.transform.Transformer` object `transform` aan te roepen en de objecten `javax.xml.transform.dom.DOMSource` en `javax.xml.transform.stream.StreamResult` door te geven.
   * Maak een bytearray en wijs de grootte van het `ByteArrayOutputStream` -object toe aan de bytearray.
   * Vul de bytearray door de methode `toByteArray` van het object `ByteArrayOutputStream` aan te roepen.
   * Maak een `com.adobe.idp.Document` -object door de constructor ervan te gebruiken en de bytearray door te geven.

1. Een vooraf ingevuld formulier renderen

   Roep de methode `renderPDFForm` van het object `FormsServiceClient` aan en geef de volgende waarden door:

   * Een tekenreekswaarde die de naam van het formulierontwerp opgeeft, inclusief de bestandsnaamextensie.
   * Een `com.adobe.idp.Document` -object dat gegevens bevat die met het formulier moeten worden samengevoegd. Zorg ervoor dat u het `com.adobe.idp.Document` -object gebruikt dat in stap 1 en 2 is gemaakt.
   * Een `PDFFormRenderSpec` -object dat uitvoeringsopties opslaat.
   * Een `URLSpec` -object dat URI-waarden bevat die door de Forms-service worden vereist.
   * Een `java.util.HashMap` -object dat bestandsbijlagen opslaat. Dit is een optionele parameter en u kunt `null` opgeven als u geen bestanden aan het formulier wilt koppelen.

   De methode `renderPDFForm` retourneert een `FormsResult` -object dat een formuliergegevensstroom bevat die naar de webbrowser van de client moet worden geschreven.

   * Maak een `javax.servlet.ServletOutputStream` -object dat wordt gebruikt om een formuliergegevensstroom naar de webbrowser van de client te verzenden.
   * Maak een `com.adobe.idp.Document` -object door de methode `FormsResult` object `getOutputContent` aan te roepen.
   * Maak een `java.io.InputStream` -object door de methode `com.adobe.idp.Document` object `getInputStream` aan te roepen.
   * Maak een bytearray die deze met de gegevensstroom van het formulier vult door de methode `read` van het object `InputStream` aan te roepen en de bytearray door te geven als een argument.
   * Roep de methode `write` van het object `javax.servlet.ServletOutputStream` aan om de gegevensstroom van het formulier naar de webbrowser van de client te verzenden. Geef de bytearray door aan de methode `write` .

**zie ook**

[Snel starten (SOAP modus): Forms vooraf vullen met stroombare indelingen met de Java API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-prepopulating-forms-with-flowable-layouts-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Formulieren vooraf invullen met de webservice-API {#prepopulating-forms-using-the-web-service-api}

Voer de volgende stappen uit om een formulier met een stroombare indeling vooraf in te vullen met de Forms API (webservice):

1. Projectbestanden opnemen

   * Maak Java-proxyklassen die gebruikmaken van de Forms-service WSDL. (Zie [ Creërend de volmachtsklassen van Java gebruikend de As van Apache ](/help/forms/developing/invoking-aem-forms-using-web.md#creating-java-proxy-classes-using-apache-axis).)
   * Neem de Java-proxyklassen op in het klassepad.

1. Een XML-gegevensbron in het geheugen maken

   * Maak een Java `DocumentBuilderFactory` -object door de methode `DocumentBuilderFactory` class&#39; `newInstance` aan te roepen.
   * Maak een Java `DocumentBuilder` -object door de methode `DocumentBuilderFactory` object `newDocumentBuilder` aan te roepen.
   * Roep de methode `newDocument` van het `DocumentBuilder` -object aan om een `org.w3c.dom.Document` -object te instantiëren.
   * Maak het basiselement van de XML-gegevensbron door de methode `createElement` van het object `org.w3c.dom.Document` aan te roepen. Hiermee wordt een `Element` -object gemaakt dat het hoofdelement vertegenwoordigt. Geef een tekenreekswaarde die de naam van het element vertegenwoordigt, door aan de methode `createElement` . De geretourneerde waarde wordt gecast naar `Element` . Voeg vervolgens het hoofdelement aan het document toe door de methode `appendChild` van het `Document` -object aan te roepen en geef het hoofdelement als een argument door. De volgende coderegels tonen deze toepassingslogica:

     ` Element root = (Element)document.createElement("transaction");  document.appendChild(root);`

   * Maak het headerelement van de XML-gegevensbron door de methode `createElement` van het object `Document` aan te roepen. Geef een tekenreekswaarde die de naam van het element vertegenwoordigt, door aan de methode `createElement` . De geretourneerde waarde wordt gecast naar `Element` . Voeg vervolgens het headerelement toe aan het hoofdelement door de methode `appendChild` van het `root` -object aan te roepen en geef het headerelement als argument door. De XML-elementen die aan het koptekstelement worden toegevoegd, komen overeen met het statische gedeelte van het formulier. De volgende coderegels tonen deze toepassingslogica:

     ` Element header = (Element)document.createElement("header");  root.appendChild(header);`

   * Maak een onderliggend element dat tot het koptekstelement behoort door de methode `createElement` van het object `Document` aan te roepen en geef een tekenreekswaarde door die de naam van het element vertegenwoordigt. De geretourneerde waarde wordt gecast naar `Element` . Stel vervolgens een waarde voor het onderliggende element in door de methode `appendChild` ervan aan te roepen en geef de methode `Document` object `createTextNode` als argument door. Geef een tekenreekswaarde op die als waarde van het onderliggende element wordt weergegeven. Voeg ten slotte het onderliggende element toe aan het koptekstelement door de methode `appendChild` van het koptekstelement aan te roepen en geef het onderliggende element als argument door. Deze toepassingslogica wordt in de volgende coderegels getoond:

     ` Element poNum= (Element)document.createElement("txtPONum");  poNum.appendChild(document.createTextNode("8745236985"));  header.appendChild(LastName);`

   * Voeg alle resterende elementen aan het kopbalelement toe door laatste sub-stap voor elk gebied te herhalen dat in het statische gedeelte van de vorm verschijnt (in het gegevensbrondiagram van XML, worden deze gebieden getoond in sectie A. (Zie [ Begrijpend gegevenssubgroups ](#understanding-data-subgroups).)
   * Maak het detailelement van de XML-gegevensbron door de methode `createElement` van het object `Document` aan te roepen. Geef een tekenreekswaarde die de naam van het element vertegenwoordigt, door aan de methode `createElement` . De geretourneerde waarde wordt gecast naar `Element` . Voeg vervolgens het detailelement toe aan het hoofdelement door de methode `appendChild` van het `root` -object aan te roepen en geef het detailelementobject door als argument. De XML-elementen die aan het detailelement worden toegevoegd, komen overeen met het dynamische gedeelte van het formulier. Deze toepassingslogica wordt in de volgende coderegels getoond:

     ` Element detail = (Element)document.createElement("detail");  root.appendChild(detail);`

   * Maak een onderliggend element dat tot het detailelement behoort door de methode `createElement` van het object `Document` aan te roepen en geef een tekenreekswaarde door die de naam van het element vertegenwoordigt. De geretourneerde waarde wordt gecast naar `Element` . Stel vervolgens een waarde voor het onderliggende element in door de methode `appendChild` ervan aan te roepen en geef de methode `Document` object `createTextNode` als argument door. Geef een tekenreekswaarde op die als waarde van het onderliggende element wordt weergegeven. Voeg ten slotte het onderliggende element toe aan het detailelement door de methode `appendChild` van het detailelement aan te roepen en geef het onderliggende element als argument door. Deze toepassingslogica wordt in de volgende coderegels getoond:

     ` Element txtPartNum = (Element)document.createElement("txtPartNum");  txtPartNum.appendChild(document.createTextNode("00010-100"));  detail.appendChild(txtPartNum);`

   * Herhaal de laatste substap voor alle XML-elementen die aan het detailelement moeten worden toegevoegd. Als u de XML-gegevensbron correct wilt maken die wordt gebruikt om het inkooporderformulier te vullen, moet u de volgende XML-elementen aan het detailelement toevoegen: `txtDescription`, `numQty` en `numUnitPrice` .
   * Herhaal de laatste twee substappen voor alle gegevensitems die worden gebruikt om het formulier vooraf in te vullen.

1. De XML-gegevensbron converteren

   * Maak een `javax.xml.transform.Transformer` -object door de statische methode `javax.xml.transform.Transformer` van het object `newInstance` aan te roepen.
   * Maak een `Transformer` -object door de methode `TransformerFactory` object `newTransformer` aan te roepen.
   * Maak een `ByteArrayOutputStream` -object met behulp van de constructor.
   * Maak een `javax.xml.transform.dom.DOMSource` -object door de constructor ervan te gebruiken en het `org.w3c.dom.Document` -object door te geven dat in stap 1 is gemaakt.
   * Maak een `javax.xml.transform.dom.DOMSource` -object door de constructor ervan te gebruiken en het `ByteArrayOutputStream` -object door te geven.
   * Vul het Java `ByteArrayOutputStream` -object door de methode `javax.xml.transform.Transformer` object `transform` aan te roepen en de objecten `javax.xml.transform.dom.DOMSource` en `javax.xml.transform.stream.StreamResult` door te geven.
   * Maak een bytearray en wijs de grootte van het `ByteArrayOutputStream` -object toe aan de bytearray.
   * Vul de bytearray door de methode `toByteArray` van het object `ByteArrayOutputStream` aan te roepen.
   * Maak een `BLOB` -object met behulp van de constructor en activeer de methode `setBinaryData` ervan en geef de bytearray door.

1. Een vooraf ingevuld formulier renderen

   Roep de methode `renderPDFForm` van het object `FormsService` aan en geef de volgende waarden door:

   * Een tekenreekswaarde die de naam van het formulierontwerp opgeeft, inclusief de bestandsnaamextensie.
   * Een `BLOB` -object dat gegevens bevat die met het formulier moeten worden samengevoegd. Gebruik het `BLOB` -object dat in stap 1 en 2 is gemaakt.
   * Een `PDFFormRenderSpecc` -object dat uitvoeringsopties opslaat. Voor meer informatie, zie [ AEM Forms API Verwijzing ](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).
   * Een `URLSpec` -object dat URI-waarden bevat die door de Forms-service worden vereist.
   * Een `java.util.HashMap` -object dat bestandsbijlagen opslaat. Dit is een optionele parameter en u kunt `null` opgeven als u geen bestanden aan het formulier wilt koppelen.
   * Een leeg `com.adobe.idp.services.holders.BLOBHolder` -object dat door de methode wordt gevuld. Hiermee slaat u het gerenderde PDF formulier op.
   * Een leeg `javax.xml.rpc.holders.LongHolder` -object dat door de methode wordt gevuld. (In dit argument wordt het aantal pagina&#39;s in het formulier opgeslagen).
   * Een leeg `javax.xml.rpc.holders.StringHolder` -object dat door de methode wordt gevuld. (In dit argument wordt de waarde van de landinstelling opgeslagen.)
   * Een leeg `com.adobe.idp.services.holders.FormsResultHolder` -object dat de resultaten van deze bewerking bevat.

   Met de methode `renderPDFForm` wordt het `com.adobe.idp.services.holders.FormsResultHolder` -object dat als laatste argumentwaarde wordt doorgegeven, gevuld met een formuliergegevensstroom die naar de webbrowser van de client moet worden geschreven.

   * Maak een `FormResult` -object door de waarde van het gegevenslid van het `com.adobe.idp.services.holders.FormsResultHolder` object `value` op te halen.
   * Maak een `BLOB` -object dat formuliergegevens bevat door de methode `FormsResult` object `getOutputContent` aan te roepen.
   * Haal het inhoudstype van het object `BLOB` op door de methode `getContentType` ervan aan te roepen.
   * Stel het inhoudstype van het `javax.servlet.http.HttpServletResponse` -object in door de methode `setContentType` ervan aan te roepen en het inhoudstype van het `BLOB` -object door te geven.
   * Maak een `javax.servlet.ServletOutputStream` -object dat wordt gebruikt om de formuliergegevensstroom naar de webbrowser van de client te schrijven door de methode `javax.servlet.http.HttpServletResponse` object `getOutputStream` aan te roepen.
   * Maak een bytearray en vul deze door de methode `getBinaryData` van het object `BLOB` aan te roepen. Hierdoor wordt de inhoud van het `FormsResult` -object toegewezen aan de bytearray.
   * Roep de methode `write` van het object `javax.servlet.http.HttpServletResponse` aan om de gegevensstroom van het formulier naar de webbrowser van de client te verzenden. Geef de bytearray door aan de methode `write` .

   >[!NOTE]
   >
   >Met de methode `renderPDFForm` wordt het `com.adobe.idp.services.holders.FormsResultHolder` -object dat als laatste argumentwaarde wordt doorgegeven, gevuld met een formuliergegevensstroom die naar de webbrowser van de client moet worden geschreven.

**zie ook**

[AEM Forms aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
