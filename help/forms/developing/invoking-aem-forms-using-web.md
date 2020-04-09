---
title: AEM-formulieren aanroepen met webservices
seo-title: AEM-formulieren aanroepen met webservices
description: 'null'
seo-description: 'null'
uuid: 66bcd010-c476-4b66-831d-a48307d8d67a
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: coding
discoiquuid: d5722281-bea9-4fc7-abdc-e678899e0a15
translation-type: tm+mt
source-git-commit: 72a582b7ac19322b81fd1a92de8fce34e55b9db1

---


# AEM-formulieren aanroepen met webservices {#invoking-aem-forms-using-web-services}

De meeste services van AEM Forms in de servicecontainer zijn geconfigureerd om een webservice beschikbaar te maken, met volledige ondersteuning voor het genereren van een WSDL (Web Service Definition Language). Met andere woorden, u kunt proxyobjecten maken die de native SOAP-stapel van een AEM Forms-service gebruiken. Hierdoor kunnen AEM Forms-services de volgende SOAP-berichten uitwisselen en verwerken:

* **SOAP-verzoek**: Verzonden naar de service Forms door een clienttoepassing die een handeling aanvraagt.
* **SOAP-reactie**: Verzonden naar een cliënttoepassing door de dienst van Vormen nadat een verzoek van de ZEEP wordt verwerkt.

Met webservices kunt u dezelfde bewerkingen van AEM Forms uitvoeren als met de Java API. Een voordeel van het gebruik van webservices om AEM Forms-services aan te roepen is dat u een clienttoepassing kunt maken in een ontwikkelomgeving die SOAP ondersteunt. Een clienttoepassing is niet gebonden aan een specifieke ontwikkelomgeving of programmeertaal. Bijvoorbeeld, kunt u een cliënttoepassing tot stand brengen gebruikend Microsoft Visual Studio .NET en C# als programmeertaal.

De diensten van Vormen AEM worden blootgesteld over het protocol van de ZEEP en zijn volgzaam WSI BasisProfiel 1.1. De Interoperabiliteit van de Diensten van het Web (WSI) is een open normenorganisatie die Webdienst interoperabiliteit over platforms bevordert. Zie [https://www.ws-i.org/](https://www.ws-i.org)voor meer informatie.

AEM Forms ondersteunt de volgende webservicenormen:

* **Codering**: Ondersteunt alleen document- en letterlijke codering (dit is de voorkeurscodering volgens het WSI Basic Profile). (Zie [AEM-formulieren aanroepen met Base64-codering](#invoking-aem-forms-using-base64-encoding).)
* **MTOM**: Vertegenwoordigt een manier om gehechtheid met de verzoeken van de ZEEP te coderen. (Zie AEM-formulieren [aanroepen met MTOM](#invoking-aem-forms-using-mtom).)
* **SwaRef**: Vertegenwoordigt een andere manier om gehechtheid met de verzoeken van de ZEEP te coderen. (Zie [AEM-formulieren aanroepen met SwaRef](#invoking-aem-forms-using-swaref).)
* **SOAP met bijlagen**: Steunt zowel MIME als DIME (de Directe Inkapseling van het Bericht van Internet). Deze protocollen zijn standaardmanieren om gehechtheid over ZEEP te verzenden. Microsoft Visual Studio .NET-toepassingen gebruiken DIME. (Zie [AEM-formulieren aanroepen met Base64-codering](#invoking-aem-forms-using-base64-encoding).)
* **WS-beveiliging**: Ondersteunt een symbolisch profiel voor een wachtwoord voor een gebruikersnaam. Dit is een standaardmanier om gebruikersnamen en wachtwoorden als onderdeel van de WS Security SOAP-header te verzenden. AEM Forms ondersteunt ook HTTP-basisverificatie. (Zie Referenties [doorgeven met WS-beveiligingskoppen](https://www.adobe.com/devnet/livecycle/articles/passing_credentials.html).)

Als u AEM Forms-services wilt aanroepen met behulp van een webservice, maakt u doorgaans een proxybibliotheek die de service WSDL gebruikt. Het *aanroepen van Vormen AEM die de sectie van de Diensten* van het Web gebruiken JAX-WS gebruikt om de volmachtsklassen van Java tot stand te brengen om de diensten aan te halen. (Zie Java-proxyklassen [maken met JAX-WS](#creating-java-proxy-classes-using-jax-ws).)

U kunt de dienst WDSL terugwinnen door de volgende definitie URL te specificeren (de punten tussen haakjes zijn facultatief):

```as3
 https://<your_serverhost>:<your_port>/soap/services/<service_name>?wsdl[&version=<version>][&async=true|false][lc_version=<lc_version>]
```

waarbij:

* *your_server* representeert het IP-adres van de J2EE-toepassingsserver die als host fungeert voor AEM Forms.
* *your_port* staat voor de HTTP-poort die de J2EE-toepassingsserver gebruikt.
* *service_name* vertegenwoordigt de de dienstnaam.
* *versie* vertegenwoordigt de doelversie van de dienst (de recentste de dienstversie wordt gebruikt door gebrek).
* `async` geeft de waarde op die extra bewerkingen voor asynchrone aanroep mogelijk maakt ( `true` `false` standaard).
* *lc_version* staat voor de versie van AEM Forms die u wilt aanroepen.

De volgende lijst maakt een lijst van de dienstWSDL definities (veronderstellend dat de Vormen van AEM op de lokale gastheer en de post 8080 wordt opgesteld).

<table>
 <thead>
  <tr>
   <th><p>Service</p></th>
   <th><p>WSDL-definitie</p></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p>Assembler</p></td>
   <td><p><code>http://localhost:8080/soap/services/ AssemblerService?wsdl</code></p></td>
  </tr>
  <tr>
   <td><p>Terug en herstellen</p></td>
   <td><p><code>http://localhost:8080/soap/services/BackupService?wsdl</code></p></td>
  </tr>
  <tr>
   <td><p>Barcoded Forms</p></td>
   <td><p><code>http://localhost:8080/soap/services/ BarcodedFormsService?wsdl</code></p></td>
  </tr>
  <tr>
   <td><p>PDF converteren</p></td>
   <td><p><code>http://localhost:8080/soap/services/ ConvertPDFService?wsdl</code></p></td>
  </tr>
  <tr>
   <td><p>Distiller</p></td>
   <td><p><code>http://localhost:8080/soap/services/ DistillerService?wsdl</code></p></td>
  </tr>
  <tr>
   <td><p>DocConverter </p></td>
   <td><p><code>http://localhost:8080/soap/services/DocConverterService?WSDL</code></p></td>
  </tr>
  <tr>
   <td><p>DocumentManagement</p></td>
   <td><p><code>http://localhost:8080/soap/services/DocumentManagementService?WSDL</code></p></td>
  </tr>
  <tr>
   <td><p>Versleuteling </p></td>
   <td><p><code>http://localhost:8080/soap/services/EncryptionService?wsdl</code></p></td>
  </tr>
  <tr>
   <td><p>Formulieren</p></td>
   <td><p><code>http://localhost:8080/soap/services/FormsService?wsdl</code></p></td>
  </tr>
  <tr>
   <td><p>Integratie van formuliergegevens</p></td>
   <td><p><code>http://localhost:8080/soap/services/FormDataIntegration?wsdl</code></p></td>
  </tr>
  <tr>
   <td><p>PDF genereren</p></td>
   <td><p><code>http://localhost:8080/soap/services/ GeneratePDFService?wsdl</code></p></td>
  </tr>
  <tr>
   <td><p>3D-PDF genereren</p></td>
   <td><p><code>http://localhost:8080/soap/services/Generate3dPDFService?WSDL</code></p></td>
  </tr>
  <tr>
   <td><p>Uitvoer</p></td>
   <td><p><code>http://localhost:8080/soap/services/ OutputService?wsdl</code></p></td>
  </tr>
  <tr>
   <td><p>PDF-hulpprogramma </p></td>
   <td><p><code>http://localhost:8080/soap/services/ PDFUtilityService?wsdl</code></p></td>
  </tr>
  <tr>
   <td><p>Acrobat Reader DC-extensies</p></td>
   <td><p><code>http://localhost:8080/soap/services/ ReaderExtensionsService?wsdl</code></p></td>
  </tr>
  <tr>
   <td><p>Bewaarplaats</p></td>
   <td><p><code>http://localhost:8080/soap/services/ RepositoryService?wsdl</code></p></td>
  </tr>
  <tr>
   <td><p>Rechtenbeheer </p></td>
   <td><p><code>http://localhost:8080/soap/services/ RightsManagementService?wsdl</code></p></td>
  </tr>
  <tr>
   <td><p>Handtekening </p></td>
   <td><p><code>http://localhost:8080/soap/services/ SignatureService?wsdl</code></p></td>
  </tr>
  <tr>
   <td><p>XMP-hulpprogramma's</p></td>
   <td><p><code>http://localhost:8080/soap/services/ XMPUtilityService?wsdl</code></p></td>
  </tr>
 </tbody>
</table>

**WSDL-definities van AEM Forms Process**

U moet de naam van de Toepassing en de naam van het Proces binnen de definitie van WSDL specificeren om tot WSDL toegang te hebben die tot een proces behoort dat in Workbench wordt gecreeerd. Veronderstel dat de naam van de toepassing is `MyApplication` en de naam van het proces `EncryptDocument`. In dit geval, specificeer de volgende definitie WSDL:

```as3
 http://localhost:8080/soap/services/MyApplication/EncryptDocument?wsdl
```

>[!NOTE]
>
>Voor informatie over het voorbeeld `MyApplication/EncryptDocument` kortstondig proces, zie het [Kortstondige procesvoorbeeld](/help/forms/developing/aem-forms-processes.md).

>[!NOTE]
>
>Een toepassing kan map(pen) bevatten. Geef in dit geval de mapnaam of -namen op in de WSDL-definitie:

```as3
 http://localhost:8080/soap/services/MyApplication/[<folderA>/.../<folderZ>/]EncryptDocument?wsdl
```

**Toegang krijgen tot nieuwe functionaliteit met behulp van webservices**

De nieuwe de dienstfunctionaliteit van Vormen AEM kan worden betreden gebruikend Webdiensten. In AEM Forms wordt bijvoorbeeld de mogelijkheid geïntroduceerd om bijlagen te coderen met MTOM. (Zie AEM-formulieren [aanroepen met MTOM](#invoking-aem-forms-using-mtom).)

Om tot nieuwe functionaliteit toegang te hebben die in Vormen AEM wordt geïntroduceerd, specificeer de `lc_version` attributen in de definitie WSDL. Als u bijvoorbeeld toegang wilt krijgen tot nieuwe servicefunctionaliteit (inclusief MTOM-ondersteuning), geeft u de volgende WSDL-definitie op:

```as3
 http://localhost:8080/soap/services/MyApplication/EncryptDocument?wsdl&lc_version=9.0.1
```

>[!NOTE]
>
>Zorg dat u drie cijfers gebruikt wanneer u het `lc_version` kenmerk instelt. 9.0.1 is bijvoorbeeld gelijk aan versie 9.0.

**Web service BLOB, gegevenstype**

AEM Forms service WSDL&#39;s definiëren een groot aantal gegevenstypen. Een van de belangrijkste gegevenstypen in een webservice is een `BLOB` type. Dit gegevenstype wordt toegewezen aan de `com.adobe.idp.Document` klasse wanneer u werkt met AEM Forms Java API&#39;s. (Zie Gegevens [doorgeven aan AEM Forms-services met behulp van de Java API](/help/forms/developing/invoking-aem-forms-using-java.md#passing-data-to-aem-forms-services-using-the-java-api).)

Een `BLOB` object verzendt en haalt binaire gegevens op (bijvoorbeeld PDF-bestanden, XML-gegevens enzovoort) naar en van AEM Forms-services. Het `BLOB` type wordt bepaald in de dienst WSDL als volgt:

```as3
 <complexType name="BLOB">
     <sequence>
         <element maxOccurs="1" minOccurs="0" name="contentType"
             type="xsd:string"/>
         <element maxOccurs="1" minOccurs="0" name="binaryData"
             type="xsd:base64Binary"/>
         <element maxOccurs="1" minOccurs="0" name="attachmentID"
             type="xsd:string"/>
         <element maxOccurs="1" minOccurs="0" name="remoteURL"
             type="xsd:string"/>
         <element maxOccurs="1" minOccurs="0" name="MTOM"
             type="xsd:base64Binary"
             xmime:expectedContentTypes="*/*"
             xmlns:xmime="https://www.w3.org/2005/05/xmlmime"/>
         <element maxOccurs="1" minOccurs="0" name="swaRef"
             type="tns1:swaRef"/>
         <element maxOccurs="1" minOccurs="0" name="attributes"
             type="impl:MyMapOf_xsd_string_To_xsd_anyType"/>
     </sequence>
 </complexType>
```

De velden `MTOM` en `swaRef` worden alleen ondersteund in AEM-formulieren. U kunt deze nieuwe velden alleen gebruiken als u een URL opgeeft die de `lc_version` eigenschap bevat.

**BLOB-objecten leveren in serviceaanvragen**

Als een AEM Forms-servicebewerking een `BLOB` type als invoerwaarde vereist, maakt u een instantie van het `BLOB` type in uw toepassingslogica. (Veel webservices beginnen snel bij *Programmeren met AEM-formulieren* en laten zien hoe u met een BLOB-gegevenstype werkt.)

Wijs als volgt waarden toe aan velden die tot de `BLOB` instantie behoren:

* **Base64**: Als u gegevens wilt doorgeven als tekst die is gecodeerd in de Base64-indeling, stelt u de gegevens in het `BLOB.binaryData` veld in en stelt u het gegevenstype in de MIME-indeling (bijvoorbeeld `application/pdf`) in het `BLOB.contentType` veld in. (Zie [AEM-formulieren aanroepen met Base64-codering](#invoking-aem-forms-using-base64-encoding).)
* **MTOM**: Als u binaire gegevens in een MTOM-bijlage wilt doorgeven, stelt u de gegevens in het `BLOB.MTOM` veld in. Deze instelling koppelt de gegevens aan de SOAP-aanvraag met behulp van het Java JAX-WS-framework of de native API van het SOAP-framework. (Zie AEM-formulieren [aanroepen met MTOM](#invoking-aem-forms-using-mtom).)
* **SwaRef**: Als u binaire gegevens in een WS-I SwaRef-bijlage wilt doorgeven, stelt u de gegevens in het `BLOB.swaRef` veld in. Deze instelling koppelt de gegevens aan het SOAP-verzoek met behulp van het Java JAX-WS-framework. (Zie [AEM-formulieren aanroepen met SwaRef](#invoking-aem-forms-using-swaref).)
* **MIME- of DIME-bijlage**: Als u gegevens wilt doorgeven in een MIME- of DIME-bijlage, voegt u de gegevens toe aan de SOAP-aanvraag met de native API van het SOAP-framework. Stel de id van de bijlage in het `BLOB.attachmentID` veld in. (Zie [AEM-formulieren aanroepen met Base64-codering](#invoking-aem-forms-using-base64-encoding).)
* **Externe URL**: Als gegevens worden gehost op een webserver en toegankelijk zijn via een HTTP-URL, stelt u de HTTP-URL in het `BLOB.remoteURL` veld in. (Zie AEM-formulieren [aanroepen met behulp van BLOB-gegevens via HTTP](#invoking-aem-forms-using-blob-data-over-http).)

**Toegang verkrijgen tot gegevens in BLOB-objecten die zijn geretourneerd door services**

Het transmissieprotocol voor teruggekeerde `BLOB` voorwerpen hangt van verscheidene factoren af, die in de volgende orde worden overwogen, die ophouden wanneer de belangrijkste voorwaarde wordt voldaan aan:

1. **Doel-URL verwijst naar het verzendprotocol**. Als het doelURL bij de aanroeping van de ZEEP de parameter `blob="`*BLOB_TYPE *&quot;bevat, dan* BLOB_TYPE *bepaalt het transmissieprotocol.* BLOB_TYPE *is een placeholder voor base64, dime, mime, http, mtom, of swaref.
1. **Het eindpunt van de ZEEP van de dienst is Slim**. Als aan de volgende voorwaarden wordt voldaan, worden de uitvoerdocumenten geretourneerd met hetzelfde verzendprotocol als de invoerdocumenten:

   * De het eindpuntparameterStandaardprotocol van de ZEEP van de dienst voor de Voorwerpen van de Klodder van de Output wordt geplaatst aan Slim.

      Voor elke dienst met een eindpunt van de ZEEP, staat de beleidsconsole u toe om het transmissieprotocol voor om het even welke teruggekeerde blobs te specificeren. (Zie [Help bij](https://www.adobe.com/go/learn_aemforms_admin_63)de administratie.)

   * AEM Forms-service neemt een of meer documenten op als invoer.

1. **Het eindpunt van de ZEEP van de dienst is niet Slim**. Het gevormde protocol bepaalt het protocol van de documenttransmissie, en de gegevens zijn teruggekeerd op het overeenkomstige `BLOB` gebied. Bijvoorbeeld, als het eindpunt van de ZEEP aan DIME wordt geplaatst, dan is de teruggekeerde blob op het `blob.attachmentID` gebied ongeacht het transmissieprotocol van om het even welk inputdocument.
1. **Anders**. Als een service het documenttype niet als invoer gebruikt, worden de uitvoerdocumenten in het `BLOB.remoteURL` veld via het HTTP-protocol geretourneerd.

Zoals beschreven in de eerste voorwaarde, kunt u het transmissietype voor om het even welke teruggekeerde documenten verzekeren door het eindpunt URL van de ZEEP met een achtervoegsel als volgt uit te breiden:

```as3
     https://<your_serverhost>:<your_port>/soap/services/<service
     name>?blob=base64|dime|mime|http|mtom|swaref
```

Hier is de correlatie tussen transmissietypen en het gebied waarvan u de gegevens verkrijgt:

* **Base64-indeling**: Stel het `blob` achtervoegsel zo in dat de gegevens in het `base64` `BLOB.binaryData` veld worden geretourneerd.
* **MIME- of DIME-bijlage**: Stel het `blob` achtervoegsel in op `DIME` of `MIME` om de gegevens te retourneren als een bijlagetype met de bijlage-id die in het `BLOB.attachmentID` veld wordt geretourneerd. Gebruik de eigen API van het SOAP-framework om de gegevens in de bijlage te lezen.
* **Externe URL**: Stel het `blob` achtervoegsel zo in dat de gegevens op de toepassingsserver blijven staan en dat de URL die naar de gegevens in het `http` `BLOB.remoteURL` veld verwijst, wordt geretourneerd.
* **MTOM of SwaRef**: Stel het `blob` achtervoegsel in op `mtom` of `swaref` om de gegevens te retourneren als een overeenkomstig bijlagetype met de bijlage-id die wordt geretourneerd in de `BLOB.MTOM` velden of in de `BLOB.swaRef` velden. Gebruik de native API van het SOAP-framework om de gegevens in de bijlage te lezen.

>[!NOTE]
>
>U wordt aangeraden een `BLOB` object niet groter dan 30 MB te laten vullen door de `setBinaryData` methode aan te roepen. Anders bestaat de mogelijkheid dat er een `OutOfMemory` uitzondering optreedt.

>[!NOTE]
>
>Op JAX WS gebaseerde toepassingen die het MTOM transmissieprotocol gebruiken zijn beperkt tot 25MB van verzonden en ontvangen gegevens. Deze beperking is het gevolg van een bug in JAX-WS. Als de gecombineerde grootte van uw verzonden en ontvangen dossiers 25MB overschrijdt, gebruik het SwaRef transmissieprotocol in plaats van MTOM. Anders bestaat de mogelijkheid van een `OutOfMemory` uitzondering.

**MTOM-transmissie van bytearrays met base64-codering**

Naast het `BLOB` object ondersteunt het MTOM-protocol alle byte-arrayparameters of byte-arrayvelden van een complex type. Dit betekent dat de kaders van de ZEEP van de cliënt die MTOM steunen om het even welk `xsd:base64Binary` element als gehechtheid MTOM (in plaats van een base64-gecodeerde tekst) kunnen verzenden. AEM Forms SOAP-eindpunten kunnen dit type bytearray-codering lezen. De service AEM Forms retourneert echter altijd een bytearraytype als een base64-gecodeerde tekst. De bytearray-uitvoerparameters ondersteunen MTOM niet.

De diensten van Vormen AEM die een grote hoeveelheid binaire gegevens terugkeren gebruiken het document/BLOB type eerder dan het byte-serie type. Het documenttype is veel efficiënter voor het verzenden van grote hoeveelheden gegevens.

## Webservicetypen {#web-service-data-types}

In de volgende tabel worden de gegevenstypen van Java weergegeven en het overeenkomstige gegevenstype van de webservice.

<table>
 <thead>
  <tr>
   <th><p>Java-gegevenstype</p></th>
   <th><p>Gegevenstype webservice</p></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p><code>java.lang.byte[]</code></p></td>
   <td><p><code>xsd:base64Binary</code></p></td>
  </tr>
  <tr>
   <td><p><code>java.lang.Boolean</code></p></td>
   <td><p><code>xsd:boolean</code></p></td>
  </tr>
  <tr>
   <td><p><code>java.util.Date</code></p></td>
   <td><p>Het <code>DATE</code> type, dat in de dienst WSDL als volgt wordt bepaald:</p><p><code>&lt;complexType name="DATE"&gt;</code></p><p><code>&lt;sequence&gt;</code></p><p><code>&lt;element maxOccurs="1" minOccurs="0" name="date" </code><code>type="xsd:dateTime" /&gt; </code></p><p><code>&lt;element maxOccurs="1" minOccurs="0" name="calendar" </code><code>type="xsd:dateTime" /&gt; </code></p><p><code>&lt;/sequence&gt;</code></p><p><code>&lt;/complexType&gt;</code></p><p>Als een AEM Forms-servicebewerking een <code>java.util.Date</code> waarde als invoer gebruikt, moet de SOAP-clienttoepassing de datum in het <code>DATE.date</code> veld doorgeven. Als u het <code>DATE.calendar</code> veld in dit geval instelt, treedt een runtime-uitzondering op. Als de service een waarde retourneert <code>java.util.Date</code>, wordt de datum in het <code>DATE.date</code> veld geretourneerd.</p></td>
  </tr>
  <tr>
   <td><p><code>java.util.Calendar</code></p></td>
   <td><p>Het <code>DATE</code> type, dat in de dienst WSDL als volgt wordt bepaald:</p><p><code>&lt;complexType name="DATE"&gt;</code></p><p><code>&lt;sequence&gt;</code></p><p><code>&lt;element maxOccurs="1" minOccurs="0" name="date" </code><code>type="xsd:dateTime" /&gt; </code></p><p><code>&lt;element maxOccurs="1" minOccurs="0" name="calendar" </code><code>type="xsd:dateTime" /&gt; </code></p><p><code>&lt;/sequence&gt;</code></p><p><code>&lt;/complexType&gt;</code></p><p>Als een AEM Forms-servicebewerking een <code>java.util.Calendar</code> waarde als invoer gebruikt, moet de SOAP-clienttoepassing de datum in het <code>DATE.caledendar</code> veld doorgeven. Als u in dit geval het <code>DATE.date</code> veld instelt, treedt een runtime-uitzondering op. Als de dienst een terugkeert <code>java.util.Calendar</code>, dan is de datum teruggekeerd op het <code>DATE.calendar</code> gebied. </p></td>
  </tr>
  <tr>
   <td><p><code>java.math.BigDecimal</code></p></td>
   <td><p><code>xsd:decimal</code></p></td>
  </tr>
  <tr>
   <td><p><code>com.adobe.idp.Document</code></p></td>
   <td><p><code>BLOB</code></p></td>
  </tr>
  <tr>
   <td><p><code>java.lang.Double</code></p></td>
   <td><p><code>xsd:double</code></p></td>
  </tr>
  <tr>
   <td><p><code>java.lang.Float</code></p></td>
   <td><p><code>xsd:float</code></p></td>
  </tr>
  <tr>
   <td><p><code>java.lang.Integer</code></p></td>
   <td><p><code>xsd:int</code></p></td>
  </tr>
  <tr>
   <td><p><code>java.util.List</code></p></td>
   <td><p><code>MyArrayOf_xsd_anyType</code></p></td>
  </tr>
  <tr>
   <td><p><code>java.lang.Long</code></p></td>
   <td><p><code>xsd:long</code></p></td>
  </tr>
  <tr>
   <td><p><code>java.util.Map</code></p></td>
   <td><p>De <code>apachesoap:Map</code>code, die als volgt in een dienst WSDL wordt gedefinieerd:</p><p><code>&lt;schema elementFormDefault="qualified" targetNamespace="https://xml.apache.org/xml-soap" xmlns="https://www.w3.org/2001/XMLSchema"&gt;</code></p><p><code>&lt;complexType name="mapItem"&gt;</code></p><p><code>&lt;sequence&gt;</code></p><p><code>&lt;element name="key" nillable="true" type="xsd:anyType"/&gt;</code></p><p><code>&lt;element name="value" nillable="true" type="xsd:anyType"/&gt;</code></p><p><code>&lt;/sequence&gt;</code></p><p><code>&lt;/complexType&gt;</code></p><p><code>&lt;complexType name="Map"&gt;</code></p><p><code>&lt;sequence&gt;</code></p><p><code>&lt;element maxOccurs="unbounded" minOccurs="0" name="item" </code><code>type="apachesoap:mapItem"/&gt;</code></p><p><code>&lt;/sequence&gt;</code></p><p><code>&lt;/complexType&gt;</code></p><p><code>&lt;/schema&gt;</code></p><p>De Kaart wordt vertegenwoordigd als opeenvolging van sleutel/waardeparen.</p></td>
  </tr>
  <tr>
   <td><p><code>java.lang.Object</code></p></td>
   <td><p><code>$1</code></p></td>
  </tr>
  <tr>
   <td><p><code>java.lang.Short</code></p></td>
   <td><p><code>xsd:short</code></p></td>
  </tr>
  <tr>
   <td><p><code>java.lang.String</code></p></td>
   <td><p><code>xsd:string</code></p></td>
  </tr>
  <tr>
   <td><p><code>org.w3c.dom.Document</code></p></td>
   <td><p>Het type van XML, dat in de dienst WSDL als volgt wordt bepaald:</p><p><code>&lt;complexType name="XML"&gt;</code></p><p><code>&lt;sequence&gt;</code></p><p><code>&lt;element maxOccurs="1" minOccurs="0" name="document" </code><code>type="xsd:string" /&gt; </code></p><p><code>&lt;element maxOccurs="1" minOccurs="0" name="element" </code><code>type="xsd:string" /&gt; </code></p><p><code>&lt;/sequence&gt;</code></p><p><code>&lt;/complexType&gt;</code></p><p>Als een AEM Forms-service een <code>org.w3c.dom.Document</code> waarde accepteert, geeft u de XML-gegevens in het <code>XML.document</code> veld door.</p><p>Als u het <code>XML.element</code> veld instelt, treedt een runtime-uitzondering op. Als de service een waarde retourneert <code>org.w3c.dom.Document</code>, worden de XML-gegevens in het <code>XML.document</code> veld geretourneerd.</p></td>
  </tr>
  <tr>
   <td><p><code>org.w3c.dom.Element</code></p></td>
   <td><p>Het type van XML, dat in de dienst WSDL als volgt wordt bepaald:</p><p><code>&lt;complexType name="XML"&gt;</code></p><p><code>&lt;sequence&gt;</code></p><p><code>&lt;element maxOccurs="1" minOccurs="0" name="document" </code><code>type="xsd:string" /&gt; </code></p><p><code>&lt;element maxOccurs="1" minOccurs="0" name="element" </code><code>type="xsd:string" /&gt; </code></p><p><code>&lt;/sequence&gt;</code></p><p><code>&lt;/complexType&gt;</code></p><p>Als een AEM Forms-service een bewerking <code>org.w3c.dom.Element</code> als invoer uitvoert, geeft u de XML-gegevens door in het <code>XML.element</code> veld.</p><p>Als u het <code>XML.document</code> veld instelt, treedt een runtime-uitzondering op. Als de service een waarde retourneert <code>org.w3c.dom.Element</code>, worden de XML-gegevens in het <code>XML.element</code> veld geretourneerd.</p></td>
  </tr>
 </tbody>
</table>

**Adobe Developer-website**

De Adobe Developer-website bevat het volgende artikel waarin wordt besproken hoe AEM Forms-services kunnen worden aangeroepen met behulp van de webservice-API:

[ASP.NET-toepassingen maken voor het genereren van formulieren](https://www.adobe.com/devnet/livecycle/articles/asp_net.html)

[Webservices aanroepen met behulp van aangepaste componenten](https://www.adobe.com/devnet/livecycle/articles/extend_webservices.html)

>[!NOTE]
>
>Wanneer u webservices aanroept met behulp van aangepaste componenten, wordt beschreven hoe u een component AEM Forms maakt die webservices van derden aanroept.

## Java-proxyklassen maken met JAX-WS {#creating-java-proxy-classes-using-jax-ws}

U kunt JAX-WS gebruiken om een WSDL-service van Forms om te zetten in Java-proxyklassen. Met deze klassen kunt u de services van AEM Forms aanroepen. Met Apache Ant kunt u een constructiescript maken waarmee Java-proxyklassen worden gegenereerd door naar de AEM Forms-service WSDL te verwijzen. U kunt JAX-WS-proxybestanden genereren door de volgende stappen uit te voeren:

1. Installeer Apache Ant op de clientcomputer. (Zie [https://ant.apache.org/bindownload.cgi](https://ant.apache.org/bindownload.cgi).)

   * Voeg de binmap toe aan het klassepad.
   * Stel de omgevingsvariabele in op de map waarin u Ant hebt geïnstalleerd. `ANT_HOME`

1. Installeer JDK 1.6 of later.

   * Voeg de JDK bin-map toe aan het klassepad.
   * Voeg de binmap JRE toe aan het klassepad. Dit vak bevindt zich in de `[JDK_INSTALL_LOCATION]/jre` map.
   * Stel de omgevingsvariabele in op de map waarin u de JDK hebt geïnstalleerd. `JAVA_HOME`
   JDK 1.6 omvat het havenprogramma dat in het build.xml- dossier wordt gebruikt. JDK 1.5 omvat dat programma niet.

1. Installeer JAX-WS op de clientcomputer. (Zie [Java API voor XML-webservices](https://jax-ws.dev.java.net/jax-ws-ea3/docs/mtom-swaref.html).)
1. Gebruik JAX-WS en Apache Ant om Java-proxyklassen te genereren. Maak een Ant-constructiescript om deze taak uit te voeren. Het volgende script is een voorbeeldscript voor Ant-build met de naam build.xml:

   ```as3
    <?xml version="1.0" encoding="UTF-8"?>
    
    <project basedir="." default="compile">
    
    <property name="port" value="8080" />
    <property name="host" value="localhost" />
    <property name="username" value="administrator" />
    <property name="password" value="password" />
    <property name="tests" value="all" />
    
    <target name="clean" >
           <delete dir="classes" />
    </target>
    
    <target name="wsdl" depends="clean">
           <mkdir dir="classes"/>
           <exec executable="wsimport" failifexecutionfails="false" failonerror="true" resultproperty="foundWSIMPORT">
               <arg line="-keep -d classes https://${host}:${port}/soap/services/EncryptionService?wsdl&lc_version=9.0.1"/>
           </exec>
           <fail unless="foundWSIMPORT">
              !!! Failed to execute JDK's wsimport tool. Make sure that JDK 1.6 (or later) is on your PATH !!!
           </fail>
    </target>
    
    <target name="compile" depends="clean, wsdl" >
         <javac destdir="./classes" fork="true" debug="true">
            <src path="./src"/>
         </javac>
    </target>
    
    <target name="run">
         <java classname="Client" fork="yes" failonerror="true" maxmemory="200M">
            <classpath>
              <pathelement location="./classes"/>
            </classpath>
            <arg value="${port}"/>
            <arg value="${host}"/>
            <arg value="${username}"/>
            <arg value="${password}"/>
            <arg value="${tests}"/>
         </java>
    </target>
    </project>
   ```

   Binnen dit Ant bouwstijlmanuscript, merk op dat het `url` bezit wordt geplaatst om de dienstWSDL van de Encryptie van verwijzingen te verwijzen die op localhost loopt. De eigenschappen `username` en `password` moeten worden ingesteld op een geldige gebruikersnaam en wachtwoord voor AEM-formulieren. De URL bevat het `lc_version` kenmerk. Als u de `lc_version` optie niet opgeeft, kunt u geen nieuwe AEM Forms-servicebewerkingen uitvoeren.

   >[!NOTE]
   >
   >Vervang dit door de servicenaam `EncryptionService`van AEM Forms die u wilt gebruiken met Java-proxyklassen. Als u bijvoorbeeld Java-proxyklassen wilt maken voor de Rights Management-service, geeft u het volgende op:

   ```as3
    http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1
   ```

1. Maak een BAT-bestand om het Ant-constructiescript uit te voeren. De volgende opdracht kan worden gevonden in een BAT-bestand dat verantwoordelijk is voor het uitvoeren van het Ant-constructiescript:

   ```as3
    ant -buildfile "build.xml" wsdl
   ```

   Plaats het bouwstijlmanuscript van de ANE in C:\Program Files\Java\jaxws-ri\bin directory. Het script schrijft de JAVA-bestanden naar de ./classes. Het script genereert JAVA-bestanden die de service kunnen aanroepen.

1. Plaats de JAVA-bestanden in een JAR-bestand. Voer de volgende stappen uit als u werkt aan Eclipse:

   * Maak een nieuw Java-project dat wordt gebruikt om de JAVA-proxybestanden in te pakken in een JAR-bestand.
   * Maak een bronmap in het project.
   * Maak een `com.adobe.idp.services` pakket in de map Source.
   * Selecteer het `com.adobe.idp.services` pakket en importeer de JAVA-bestanden in de map adobe/idp/services naar het pakket.
   * Maak indien nodig een `org/apache/xml/xmlsoap` pakket in de map Bron.
   * Selecteer de bronmap en importeer de JAVA-bestanden vanuit de map org/apache/xml/xmlsoap.
   * Stel het compatibiliteitsniveau van de Java-compiler in op 5.0 of hoger.
   * Bouw het project.
   * Exporteer het project als een JAR-bestand.
   * Importeer dit JAR-bestand in het klassepad van een clientproject. Bovendien importeert u alle JAR-bestanden in &lt;Install Directory>\Adobe\Adobe_Experience_Manager_forms\sdk\client-libs\thirdparty.
   >[!NOTE]
   >
   >Alle Java-webservices die snel kunnen worden gestart (behalve de service Formulieren) in Programmeren met AEM-formulieren, maken Java-proxybestanden met JAX-WS. Bovendien begint alle Java-webservice snel met SwaRef. (Zie [AEM-formulieren aanroepen met SwaRef](#invoking-aem-forms-using-swaref).)

**Zie ook**

[Java-proxyklassen maken met Apache Axis](#creating-java-proxy-classes-using-apache-axis)

[AEM-formulieren aanroepen met Base64-codering](#invoking-aem-forms-using-base64-encoding)

[AEM-formulieren aanroepen met behulp van BLOB-gegevens via HTTP](#invoking-aem-forms-using-blob-data-over-http)

[AEM-formulieren aanroepen met SwaRef](#invoking-aem-forms-using-swaref)

## Java-proxyklassen maken met Apache Axis {#creating-java-proxy-classes-using-apache-axis}

Met het gereedschap Apache Axis WSDL2Java kunt u een Forms-service converteren naar Java-proxyklassen. Met deze klassen kunt u Forms-servicebewerkingen aanroepen. Met Apache Ant kunt u Axis-bibliotheekbestanden genereren op basis van een service-WSDL. U kunt Apache Axis downloaden via de URL [https://ws.apache.org/axis/](https://ws.apache.org/axis/).

>[!NOTE]
>
>De webservice begint snel met het gebruik van Java-proxyklassen die met Apache Axis zijn gemaakt. Met de webservice Forms wordt snel begonnen met het gebruik van Base64 als coderingstype. (Zie [Forms Service API Quick Start](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts).)

U kunt Java-bibliotheekbestanden van de as genereren door de volgende stappen uit te voeren:

1. Installeer Apache Ant op de clientcomputer. Het is beschikbaar op [https://ant.apache.org/bindownload.cgi](https://ant.apache.org/bindownload.cgi).

   * Voeg de binmap toe aan het klassepad.
   * Stel de omgevingsvariabele in op de map waarin u Ant hebt geïnstalleerd. `ANT_HOME`

1. Installeer Apache Axis 1.4 op de clientcomputer. Het is beschikbaar op [https://ws.apache.org/axis/](https://ws.apache.org/axis/.md).
1. Stel het klassepad in om de Axis JAR-bestanden te gebruiken in uw webserviceclient, zoals wordt beschreven in de installatie-instructies voor de as op [https://ws.apache.org/axis/java/install.html](https://ws.apache.org/axis/java/install.html).
1. Gebruik Apache WSDL2Java in As om Java-proxyklassen te genereren. Maak een Ant-constructiescript om deze taak uit te voeren. Het volgende script is een voorbeeldscript voor Ant-build met de naam build.xml:

   ```as3
    <?xml version="1.0"?>
    <project name="axis-wsdl2java">
    
    <path id="axis.classpath">
    <fileset dir="C:\axis-1_4\lib" >
        <include name="**/*.jar" />
    </fileset>
    </path>
    
    <taskdef resource="axis-tasks.properties" classpathref="axis.classpath" />
    
    <target name="encryption-wsdl2java-client" description="task">
    <axis-wsdl2java
        output="C:\JavaFiles"
        testcase="false"
        serverside="false"
        verbose="true"
        username="administrator"
        password="password"
        url="http://localhost:8080/soap/services/EncryptionService?wsdl&lc_version=9.0.1" >
    </axis-wsdl2java>
    </target>
    
    </project>
   ```

   Binnen dit Ant bouwstijlmanuscript, merk op dat het `url` bezit wordt geplaatst om de dienstWSDL van de Encryptie van verwijzingen te verwijzen die op localhost loopt. De eigenschappen `username` en `password` moeten worden ingesteld op een geldige gebruikersnaam en wachtwoord voor AEM-formulieren.

1. Maak een BAT-bestand om het Ant-constructiescript uit te voeren. De volgende opdracht kan worden gevonden in een BAT-bestand dat verantwoordelijk is voor het uitvoeren van het Ant-constructiescript:

   ```as3
    ant -buildfile "build.xml" encryption-wsdl2java-client
   ```

   De JAVA-bestanden worden naar de eigenschap C:\JavaFiles folder as specified by the `output` geschreven. Als u de service Forms wilt inschakelen, importeert u deze JAVA-bestanden in het klassepad.

   Deze bestanden behoren standaard tot een Java-pakket met de naam `com.adobe.idp.services`. U wordt aangeraden deze JAVA-bestanden in een JAR-bestand te plaatsen. Importeer vervolgens het JAR-bestand in het klassepad van de clienttoepassing.

   >[!NOTE]
   >
   >Er zijn verschillende manieren om .JAVA-bestanden in een JAR te plaatsen. Een manier is het gebruik van een Java IDE zoals Eclipse. Maak een Java-project en maak een `com.adobe.idp.services`pakket (alle .JAVA-bestanden horen bij dit pakket). Importeer vervolgens alle .JAVA-bestanden in het pakket. Exporteer het project ten slotte als een JAR-bestand.

1. Wijzig de URL in de `EncryptionServiceLocator` klasse om het coderingstype op te geven. Als u bijvoorbeeld base64 wilt gebruiken, geeft u op `?blob=base64` of het `BLOB` object binaire gegevens retourneert. In de `EncryptionServiceLocator` klasse wordt dus de volgende coderegel gezocht:

   ```as3
    http://localhost:8080/soap/services/EncryptionService;
   ```

   en wijzig deze in:

   ```as3
    http://localhost:8080/soap/services/EncryptionService?blob=base64;
   ```

1. Voeg de volgende Axis JAR-bestanden toe aan het klassepad van uw Java-project:

   * activation.jar
   * axis.jar
   * commons-codec-1.3.jar
   * commons-collections-3.1.jar
   * commons-discovery.jar
   * commons-logging.jar
   * dom3-xml-apis-2.5.0.jar
   * jai_imageio.jar
   * jaxen-1,1-bèta-9.jar
   * jaxrpc.jar
   * log4j.jar
   * mail.jar
   * saaj.jar
   * wsdl4j.jar
   * xalan.jar
   * xbean.jar
   * xercesImpl.jar
   Deze JAR-bestanden staan in de `[install directory]/Adobe/Adobe Experience Manager Forms/sdk/lib/thirdparty` map.

**Zie ook**

[Java-proxyklassen maken met JAX-WS](#creating-java-proxy-classes-using-jax-ws)

[AEM-formulieren aanroepen met Base64-codering](#invoking-aem-forms-using-base64-encoding)

[AEM-formulieren aanroepen met behulp van BLOB-gegevens via HTTP](#invoking-aem-forms-using-blob-data-over-http)

## AEM-formulieren aanroepen met Base64-codering {#invoking-aem-forms-using-base64-encoding}

U kunt een dienst van Vormen AEM aanhalen gebruikend het coderen Base64. Base64-codering codeert bijlagen die worden verzonden met een aanroepingsverzoek voor een webservice. Dat wil zeggen dat `BLOB` gegevens Base64-gecodeerd zijn, niet het volledige SOAP-bericht.

&quot;Het aanroepen van Vormen AEM gebruikend het coderen Base64&quot;bespreekt het aanhalen van het volgende proces van de Vormen AEM van korte duur genoemd `MyApplication/EncryptDocument` door het gebruiken van het coderen Base64.

>[!NOTE]
>
>Dit proces is niet gebaseerd op een bestaand AEM Forms-proces. Om samen met het codevoorbeeld te volgen, creeer een proces genoemd `MyApplication/EncryptDocument` gebruikend Workbench. (Zie [Workbench](https://www.adobe.com/go/learn_aemforms_workbench_63)gebruiken.)

Wanneer dit proces wordt aangeroepen, worden de volgende handelingen uitgevoerd:

1. Hiermee verkrijgt u het onbeveiligde PDF-document dat aan het proces wordt doorgegeven. Deze handeling is gebaseerd op de `SetValue` bewerking. De invoerparameter voor dit proces is een `document` procesvariabele met de naam `inDoc`.
1. Hiermee versleutelt u het PDF-document met een wachtwoord. Deze handeling is gebaseerd op de `PasswordEncryptPDF` bewerking. Het met wachtwoord gecodeerde PDF-document wordt geretourneerd in een procesvariabele met de naam `outDoc`.

### Creërend een .NET cliëntassemblage die het coderen Base64 gebruikt {#creating-a-net-client-assembly-that-uses-base64-encoding}

U kunt een .NET cliëntassemblage tot stand brengen om de dienst van Vormen van een project van Microsoft Visual Studio .NET aan te halen. Om een .NET cliëntassemblage tot stand te brengen die base64 het coderen gebruikt, voer de volgende stappen uit:

1. Maak een proxyklasse op basis van een URL voor het oproepen van AEM Forms.
1. Creeer een project van Microsoft Visual Studio .NET dat de .NET cliëntassemblage veroorzaakt.

**Een proxyklasse maken**

U kunt een volmachtsklasse tot stand brengen die wordt gebruikt om de .NET cliëntassemblage tot stand te brengen door een hulpmiddel te gebruiken dat Microsoft Visual Studio begeleidt. De naam van het hulpmiddel is wsdl.exe en het wordt gevestigd in de de installatiemap van Microsoft Visual Studio. Als u een proxyklasse wilt maken, opent u de opdrachtprompt en navigeert u naar de map die het bestand wsdl.exe bevat. Voor meer informatie over het hulpmiddel wsdl.exe, zie de *Hulp* MSDN.

Ga het volgende bevel bij de bevelherinnering in:

```as3
 wsdl https://hiro-xp:8080/soap/services/MyApplication/EncryptDocument?WSDL&lc_version=9.0.1
```

Standaard maakt u met dit gereedschap een CS-bestand in dezelfde map die is gebaseerd op de naam van de WSDL. In dit geval maakt het een CS-bestand met de naam *EncryptDocumentService.cs*. Met dit CS-bestand kunt u een proxyobject maken waarmee u de service kunt aanroepen die is opgegeven in de oproepings-URL.

Wijzig de URL in de proxyklasse zodat deze wordt opgenomen `?blob=base64` om ervoor te zorgen dat het `BLOB` object binaire gegevens retourneert. Zoek in de proxyklasse de volgende coderegel:

```as3
 "https://hiro-xp:8080/soap/services/MyApplication/EncryptDocument";
```

en wijzig deze in:

```as3
 "https://hiro-xp:8080/soap/services/MyApplication/EncryptDocument?blob=base64";
```

Het *aanroepen van Vormen AEM die Base64 het Coderen* sectie gebruiken gebruikt `MyApplication/EncryptDocument` als voorbeeld. Als u een .NET cliëntassemblage voor een andere dienst van Vormen creeert, zorg ervoor dat u `MyApplication/EncryptDocument` met de naam van de dienst vervangt.

**Het ontwikkelen van de .NET cliëntassemblage**

Creeer een project van de Bibliotheek van de Klasse van Visual Studio dat een .NET cliëntassemblage veroorzaakt. Het CS- dossier dat u gebruikend wsdl.exe creeerde kan in dit project worden ingevoerd. Dit project veroorzaakt een Dll- dossier (de .NET cliëntassemblage) dat u in andere projecten van Visual Studio .NET kunt gebruiken om de dienst aan te halen.

1. Start Microsoft Visual Studio .NET.
1. Creeer een project van de Bibliotheek van de Klasse en noem het DocumentService.
1. Importeer het CS-bestand dat u hebt gemaakt met wsdl.exe.
1. Selecteer Referentie **toevoegen in het menu** Project ****.
1. In het Add de dialoogvakje van de Verwijzing, uitgezochte **System.Web.Services.dll**.
1. Click **Select** and then click **OK**.
1. Compileer en bouw het project.

>[!NOTE]
>
>Deze procedure leidt tot een .NET cliëntassemblage genoemd DocumentService.dll die u kunt gebruiken om de verzoeken van de ZEEP naar de `MyApplication/EncryptDocument` dienst te verzenden.

>[!NOTE]
>
>Zorg ervoor dat u `?blob=base64` aan URL in de volmachtsklasse toevoegde die wordt gebruikt om de .NET cliëntassemblage tot stand te brengen. Anders kunt u geen binaire gegevens van het `BLOB` object ophalen.

**Verwijzend de .NET cliëntassemblage**

Plaats uw onlangs gecreeerde .NET cliëntassemblage op de computer waar u uw cliënttoepassing ontwikkelt. Nadat u de .NET cliëntassemblage in een folder plaatst, kunt u het van een project van verwijzingen voorzien. Verwijs ook naar de `System.Web.Services` bibliotheek van uw project. Als u niet naar deze bibliotheek van verwijzingen voorziet, kunt u niet de .NET cliëntassemblage gebruiken om de dienst aan te halen.

1. Selecteer Referentie **toevoegen in het menu** Project ****.
1. Klik op het tabblad **.NET** .
1. Klik op **Bladeren** en zoek het bestand DocumentService.dll.
1. Click **Select** and then click **OK**.

**Het aanhalen van de dienst die een .NET cliëntassemblage gebruikt die het coderen Base64 gebruikt**

U kunt de `MyApplication/EncryptDocument` dienst (die in Workbench) werd gebouwd aanhalen gebruikend een .NET cliëntassemblage die Base64 het coderen gebruikt. Voer de volgende stappen uit om de `MyApplication/EncryptDocument` service aan te roepen:

1. Creeer een de cliëntassemblage van Microsoft .NET die de `MyApplication/EncryptDocument` dienst WSDL verbruikt.
1. Creeer een project van cliëntMicrosoft .NET. Verwijs de de cliëntassemblage van Microsoft .NET in het cliëntproject. Verwijs ook `System.Web.Services`.
1. Gebruikend de de cliëntassemblage van Microsoft .NET, creeer een `MyApplication_EncryptDocumentService` voorwerp door zijn standaardaannemer aan te halen.
1. Stel de `MyApplication_EncryptDocumentService` eigenschap van het `Credentials` object in met een `System.Net.NetworkCredential` object. Geef binnen de `System.Net.NetworkCredential` constructor een gebruikersnaam voor AEM-formulieren en het bijbehorende wachtwoord op. Plaats authentificatiewaarden om uw .NET cliënttoepassing toe te laten om de berichten van de ZEEP met de Vormen van AEM met succes uit te wisselen.
1. Maak een `BLOB` object met de constructor ervan. Het `BLOB` object wordt gebruikt om een PDF-document op te slaan dat aan het `MyApplication/EncryptDocument` proces wordt doorgegeven.
1. Maak een `System.IO.FileStream` object door de constructor ervan aan te roepen. Geef een tekenreekswaarde door die staat voor de bestandslocatie van het PDF-document en de modus waarin het bestand moet worden geopend.
1. Maak een bytearray waarin de inhoud van het `System.IO.FileStream` object wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` eigenschap van het `Length` object op te halen.
1. Vul de bytearray met streamgegevens door de `System.IO.FileStream` `Read` methode van het object aan te roepen. Geef de bytearray, de startpositie en de streamlengte door om te lezen.
1. Vul het `BLOB` object door de `binaryData` eigenschap ervan toe te wijzen met de inhoud van de bytearray.
1. Roep het `MyApplication/EncryptDocument` proces aan door de `MyApplication_EncryptDocumentService` methode van het `invoke` object aan te roepen en het `BLOB` object dat het PDF-document bevat door te geven. Hiermee wordt een versleuteld PDF-document binnen een `BLOB` object geretourneerd.
1. Maak een `System.IO.FileStream` object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het met wachtwoord gecodeerde document vertegenwoordigt.
1. Maak een bytearray waarin de gegevensinhoud wordt opgeslagen van het `BLOB` object dat door de `MyApplicationEncryptDocumentService` methode van het `invoke` object wordt geretourneerd. Vul de bytearray met de waarde van het `BLOB` `binaryData` gegevenslid van het object.
1. Maak een `System.IO.BinaryWriter` object door de constructor ervan aan te roepen en het `System.IO.FileStream` object door te geven.
1. Schrijf de inhoud van de bytearray naar een PDF-bestand door de methode van het `System.IO.BinaryWriter` `Write` object aan te roepen en de bytearray door te geven.

### Een service aanroepen met Java-proxyklassen en Base64-codering {#invoking-a-service-using-java-proxy-classes-and-base64-encoding}

U kunt een dienst van Vormen AEM aanhalen gebruikend de volmachtsklassen van Java en Base64. Voer de volgende stappen uit om de `MyApplication/EncryptDocument` service aan te roepen met Java-proxyklassen:

1. Creeer de volmachtsklassen van Java gebruikend JAX-WS die de `MyApplication/EncryptDocument` dienst WSDL verbruikt. Gebruik het volgende eindpunt van WSDL:

   `https://hiro-xp:8080/soap/services/MyApplication/EncryptDocument?WSDL&lc_version=9.0.1`

   >[!NOTE]
   >
   >Vervangen `hiro-xp` *door het IP-adres van de J2EE-toepassingsserver die als host fungeert voor AEM Forms.*

1. Plaats de Java-proxyklassen die met JAX-WS zijn gemaakt in een JAR-bestand.
1. Neem het JAR-bestand voor de Java-proxy en de JAR-bestanden op in het volgende pad:

   &lt;Install Directory>\Adobe\Adobe_Experience_Manager_forms\sdk\client-libs\thirdparty

   in het klassenpad van uw Java-clientproject.

1. Maak een `MyApplicationEncryptDocumentService` object met de constructor ervan.
1. Maak een `MyApplicationEncryptDocument` object door de `MyApplicationEncryptDocumentService` methode van het `getEncryptDocument` object aan te roepen.
1. Stel de verbindingswaarden in die nodig zijn om AEM Forms aan te roepen door waarden toe te wijzen aan de volgende gegevensleden:

   * Wijs het eindpunt WSDL en het coderingstype aan het `javax.xml.ws.BindingProvider` gebied van het `ENDPOINT_ADDRESS_PROPERTY` voorwerp toe. Als u de `MyApplication/EncryptDocument` service wilt aanroepen met behulp van Base64-codering, geeft u de volgende URL-waarde op:

      `https://hiro-xp:8080/soap/services/MyApplication/EncryptDocument?blob=base64`

   * Wijs de gebruiker van AEM-formulieren toe aan het `javax.xml.ws.BindingProvider` veld van het `USERNAME_PROPERTY` object.
   * Wijs de bijbehorende wachtwoordwaarde toe aan het `javax.xml.ws.BindingProvider` veld van het `PASSWORD_PROPERTY` object.
   In het volgende codevoorbeeld wordt deze toepassingslogica getoond:

   ```as3
    //Set connection values required to invoke AEM Forms
    String url = "https://hiro-xp:8080/soap/services/MyApplication/EncryptDocument?blob=base64";
    String username = "administrator";
    String password = "password";
    ((BindingProvider) encryptDocClient).getRequestContext().put(BindingProvider.ENDPOINT_ADDRESS_PROPERTY, url);
    ((BindingProvider) encryptDocClient).getRequestContext().put(BindingProvider.USERNAME_PROPERTY, username);
    ((BindingProvider) encryptDocClient).getRequestContext().put(BindingProvider.PASSWORD_PROPERTY, password);
   ```

1. Haal het PDF-document op dat u naar het `MyApplication/EncryptDocument` proces wilt verzenden door een `java.io.FileInputStream` object te maken met de constructor ervan. Geef een tekenreekswaarde door die de locatie van het PDF-document aangeeft.
1. Maak een bytearray en vul deze met de inhoud van het `java.io.FileInputStream` object.
1. Maak een `BLOB` object met de constructor ervan.
1. Vul het `BLOB` `setBinaryData` object door de methode ervan aan te roepen en de bytearray door te geven. Het `BLOB` object `setBinaryData` is de methode die moet worden aangeroepen wanneer Base64-codering wordt gebruikt. Zie BLOB-objecten leveren in serviceaanvragen.
1. Roep het `MyApplication/EncryptDocument` proces aan door de `MyApplicationEncryptDocument` methode van het `invoke` object aan te roepen. Geef het `BLOB` object dat het PDF-document bevat door. De aanroepmethode retourneert een `BLOB` object dat het gecodeerde PDF-document bevat.
1. Maak een bytearray die het gecodeerde PDF-document bevat door de `BLOB` `getBinaryData` methode van het object aan te roepen.
1. Sla het versleutelde PDF-document op als een PDF-bestand. Schrijf de bytearray naar een bestand.

**Zie ook**

[Snel starten: Een service aanroepen met Java-proxybestanden en Base64-codering](/help/forms/developing/invocation-api-quick-starts.md#quick-start-invoking-a-service-using-java-proxy-files-and-base64-encoding)

[Creërend een .NET cliëntassemblage die het coderen Base64 gebruikt](#creating-a-net-client-assembly-that-uses-base64-encoding)

## AEM-formulieren aanroepen met MTOM {#invoking-aem-forms-using-mtom}

U kunt de services van AEM Forms aanroepen met behulp van de MTOM-standaard voor webservices. Deze standaard bepaalt hoe binaire gegevens, zoals een PDF-document, via internet of intranet worden verzonden. Een eigenschap van MTOM is het gebruik van het `XOP:Include` element. Dit element wordt bepaald in de Binary Optimized Packaging (XOP) specificatie van XML om de binaire gehechtheid van een bericht van de ZEEP van verwijzingen te voorzien.

De discussie gaat hier over het gebruik van MTOM voor het aanroepen van het volgende kortstondige AEM Forms-proces met de naam `MyApplication/EncryptDocument`.

>[!NOTE]
>
>Dit proces is niet gebaseerd op een bestaand AEM Forms-proces. Om samen met het codevoorbeeld te volgen, creeer een proces genoemd `MyApplication/EncryptDocument` gebruikend Workbench. (Zie [Workbench](https://www.adobe.com/go/learn_aemforms_workbench_63)gebruiken.)

Wanneer dit proces wordt aangeroepen, worden de volgende handelingen uitgevoerd:

1. Hiermee verkrijgt u het onbeveiligde PDF-document dat aan het proces wordt doorgegeven. Deze handeling is gebaseerd op de `SetValue` bewerking. De invoerparameter voor dit proces is een `document` procesvariabele met de naam `inDoc`.
1. Hiermee versleutelt u het PDF-document met een wachtwoord. Deze handeling is gebaseerd op de `PasswordEncryptPDF` bewerking. Het met wachtwoord gecodeerde PDF-document wordt geretourneerd in een procesvariabele met de naam `outDoc`.

>[!NOTE]
>
>Ondersteuning voor MTOM is toegevoegd aan AEM Forms, versie 9.

>[!NOTE]
>
>Op JAX WS gebaseerde toepassingen die het MTOM transmissieprotocol gebruiken zijn beperkt tot 25MB van verzonden en ontvangen gegevens. Deze beperking is het gevolg van een bug in JAX-WS. Als de gecombineerde grootte van uw verzonden en ontvangen dossiers 25MB overschrijdt, gebruik het SwaRef transmissieprotocol in plaats van MTOM. Anders bestaat de mogelijkheid van een `OutOfMemory` uitzondering.

De bespreking hier is over het gebruiken van MTOM binnen een project van Microsoft .NET om de diensten van Vormen AEM aan te halen. Het .NET gebruikte kader is 3.5, en het ontwikkelmilieu is Visual Studio 2008. Als u de Verbeteringen van de Dienst van het Web (WSE) hebt die op uw ontwikkelingscomputer worden geïnstalleerd, verwijder het. .NET 3.5 kader steunt een kader van de ZEEP genoemd Communicatie van Vensters Stichting (WCF). Wanneer het aanhalen van Vormen AEM door MTOM te gebruiken, slechts WCF (niet WSE) wordt gesteund.

### Creërend een .NET project dat de dienst aanhaalt gebruikend MTOM {#creating-a-net-project-that-invokes-a-service-using-mtom}

U kunt een project van Microsoft .NET tot stand brengen dat de dienst van Vormen AEM kan aanhalen gebruikend Webdiensten. Eerst, creeer een project van Microsoft .NET door Visual Studio 2008 te gebruiken. Om de dienst van Vormen AEM aan te halen, creeer een Verwijzing van de Dienst naar de dienst van Vormen AEM die u binnen uw project wilt aanhalen. Wanneer u een serviceverwijzing maakt, geeft u een URL op naar de service AEM Forms:

```as3
 http://localhost:8080/soap/services/MyApplication/EncryptDocument?WSDL&lc_version=9.0.1
```

Vervangen `localhost` door het IP-adres van de J2EE-toepassingsserver die als host fungeert voor AEM Forms. Vervangen door de naam van de AEM Forms-service die moet worden aangeroepen. `MyApplication/EncryptDocument` Bijvoorbeeld, om een verrichting van het Beheer van Rechten aan te halen, specificeer:

`http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`

De `lc_version` optie zorgt ervoor dat de functionaliteit van Vormen AEM, zoals MTOM, beschikbaar is. U kunt AEM-formulieren niet aanroepen met MTOM zonder deze `lc_version` optie op te geven.

Nadat u een Verwijzing van de Dienst creeert, zijn de gegevenstypes verbonden aan de dienst van Vormen AEM beschikbaar voor gebruik binnen uw .NET project. Om een .NET project tot stand te brengen dat de dienst van Vormen AEM aanhaalt, voer de volgende stappen uit:

1. Creeer een .NET project gebruikend Microsoft Visual Studio 2008.
1. Selecteer in het menu **Project** de optie **Serviceverwijzing** toevoegen.
1. Geef in het dialoogvenster **Adres** de WSDL op voor de service AEM-formulieren. Bijvoorbeeld:

   ```as3
    http://localhost:8080/soap/services/MyApplication/EncryptDocument?WSDL&lc_version=9.0.1
   ```

1. Click **Go** and then click **OK**.

### Het aanhalen van de dienst die MTOM in een .NET project gebruikt {#invoking-a-service-using-mtom-in-a-net-project}

Neem bijvoorbeeld het `MyApplication/EncryptDocument` proces waarbij een onbeveiligd PDF-document wordt geaccepteerd en een PDF-document met een wachtwoord wordt geretourneerd. Voer de volgende stappen uit om het `MyApplication/EncryptDocument` proces (dat in Workbench is ingebouwd) met MTOM aan te roepen:

1. Creeer een project van Microsoft .NET.
1. Maak een `MyApplication_EncryptDocumentClient` object met de standaardconstructor.
1. Maak een `MyApplication_EncryptDocumentClient.Endpoint.Address` object met de `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde door die de WSDL opgeeft voor de service AEM Forms en het coderingstype:

   ```as3
    https://hiro-xp:8080/soap/services/MyApplication/EncryptDocument?blob=mtom
   ```

   U hoeft het `lc_version` kenmerk niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt. Zorg er echter voor dat u opgeeft `?blob=mtom`.

   >[!NOTE]
   >
   >Vervangen `hiro-xp` *door het IP-adres van de J2EE-toepassingsserver die als host fungeert voor AEM Forms.*

1. Maak een `System.ServiceModel.BasicHttpBinding` object door de waarde van het `EncryptDocumentClient.Endpoint.Binding` gegevenslid op te halen. Kiezen naar de geretourneerde waarde `BasicHttpBinding`.
1. Stel het `System.ServiceModel.BasicHttpBinding` gegevenslid van het object in op `MessageEncoding` `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
1. Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

   * Wijs de gebruikersnaam voor AEM-formulieren toe aan het gegevenslid `MyApplication_EncryptDocumentClient.ClientCredentials.UserName.UserName`.
   * Wijs de overeenkomstige wachtwoordwaarde aan het gegevenslid toe `MyApplication_EncryptDocumentClient.ClientCredentials.UserName.Password`.
   * Wijs de constante waarde toe `HttpClientCredentialType.Basic` aan het gegevenslid `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
   * Wijs de constante waarde toe `BasicHttpSecurityMode.TransportCredentialOnly` aan het gegevenslid `BasicHttpBindingSecurity.Security.Mode`.
   In het volgende codevoorbeeld worden deze taken getoond.

   ```as3
    //Enable BASIC HTTP authentication
    encryptProcess.ClientCredentials.UserName.UserName = "administrator";
    encryptProcess.ClientCredentials.UserName.Password = "password";
    b.Security.Transport.ClientCredentialType = HttpClientCredentialType.Basic;
    b.Security.Mode = BasicHttpSecurityMode.TransportCredentialOnly;
    b.MaxReceivedMessageSize = 4000000;
    b.MaxBufferSize = 4000000;
    b.ReaderQuotas.MaxArrayLength = 4000000;
   ```

1. Maak een `BLOB` object met de constructor ervan. Met dit `BLOB` object wordt een PDF-document opgeslagen dat aan het `MyApplication/EncryptDocument` proces wordt doorgegeven.
1. Maak een `System.IO.FileStream` object door de constructor ervan aan te roepen. Geef een tekenreekswaarde door die staat voor de bestandslocatie van het PDF-document en de modus waarin het bestand moet worden geopend.
1. Maak een bytearray waarin de inhoud van het `System.IO.FileStream` object wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` eigenschap van het `Length` object op te halen.
1. Vul de bytearray met streamgegevens door de `System.IO.FileStream` `Read` methode van het object aan te roepen. Geef de bytearray, de startpositie en de streamlengte door om te lezen.
1. Vul het `BLOB` object door het `MTOM` gegevenslid ervan de inhoud van de bytearray toe te wijzen.
1. Roep het `MyApplication/EncryptDocument` proces aan door de `MyApplication_EncryptDocumentClient` methode van het `invoke` object aan te roepen. Geef het `BLOB` object dat het PDF-document bevat door. Hiermee wordt een versleuteld PDF-document binnen een `BLOB` object geretourneerd.
1. Maak een `System.IO.FileStream` object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het beveiligde PDF-document vertegenwoordigt.
1. Maak een bytearray met de gegevensinhoud van het `BLOB` object dat door de `invoke` methode is geretourneerd. Vul de bytearray met de waarde van het `BLOB` `MTOM` gegevenslid van het object.
1. Maak een `System.IO.BinaryWriter` object door de constructor ervan aan te roepen en het `System.IO.FileStream` object door te geven.
1. Schrijf de inhoud van de bytearray naar een PDF-bestand door de methode van het `System.IO.BinaryWriter` `Write` object aan te roepen en de bytearray door te geven.

>[!NOTE]
>
>De meeste AEM Forms-servicebewerkingen beginnen met MTOM. U kunt deze snelle begin in de overeenkomstige snelle beginsectie van de dienst bekijken. Zie bijvoorbeeld Snel aan de slag met de uitvoerservice-API voor informatie over de sectie Snelle start voor uitvoer [](/help/forms/developing/output-service-java-api-quick.md#output-service-java-api-quick-start-soap).

**Zie ook**

[Snel starten: Het aanhalen van de dienst die MTOM in een .NET project gebruikt](/help/forms/developing/invocation-api-quick-starts.md#quick-start-invoking-a-service-using-mtom-in-a-net-project)

[Toegang tot meerdere services via webservices](#accessing-multiple-services-using-web-services)

[Creërend een Asp.net- Webtoepassing die een mens-centric langlevend proces aanhaalt](/help/forms/developing/invoking-human-centric-long-lived.md#creating-an-asp-net-web-application-that-invokes-a-human-centric-long-lived-process)

## AEM-formulieren aanroepen met SwaRef {#invoking-aem-forms-using-swaref}

U kunt AEM Forms-services aanroepen met SwaRef. De inhoud van het element `wsi:swaRef` XML wordt verzonden als gehechtheid binnen een lichaam van de ZEEP dat de verwijzing naar de gehechtheid opslaat. Wanneer het aanhalen van de dienst van Vormen door SwaRef te gebruiken, creeer de volmachtsklassen van Java door Java API voor de Diensten van het Web van XML te gebruiken (JAX-WS). (Zie [Java API voor XML-webservices](https://jax-ws.dev.java.net/jax-ws-ea3/docs/mtom-swaref.html).)

De discussie gaat hier over het aanroepen van het volgende kortstondige proces van Forms genoemd `MyApplication/EncryptDocument` door SwaRef te gebruiken.

>[!NOTE]
>
>Dit proces is niet gebaseerd op een bestaand AEM Forms-proces. Om samen met het codevoorbeeld te volgen, creeer een proces genoemd `MyApplication/EncryptDocument` gebruikend Workbench. (Zie [Workbench](https://www.adobe.com/go/learn_aemforms_workbench_63)gebruiken.)

Wanneer dit proces wordt aangeroepen, worden de volgende handelingen uitgevoerd:

1. Hiermee verkrijgt u het onbeveiligde PDF-document dat aan het proces wordt doorgegeven. Deze handeling is gebaseerd op de `SetValue` bewerking. De invoerparameter voor dit proces is een `document` procesvariabele met de naam `inDoc`.
1. Hiermee versleutelt u het PDF-document met een wachtwoord. Deze handeling is gebaseerd op de `PasswordEncryptPDF` bewerking. Het met wachtwoord gecodeerde PDF-document wordt geretourneerd in een procesvariabele met de naam `outDoc`.

>[!NOTE]
>
>Ondersteuning voor SwaRef toegevoegd in AEM-formulieren

Hieronder wordt beschreven hoe u Forms-services kunt aanroepen met SwaRef in een Java-clienttoepassing. De Java-toepassing gebruikt proxyklassen die met JAX-WS zijn gemaakt.

### Roep de dienst aan gebruikend JAX-WS bibliotheekdossiers die SwaRef gebruiken {#invoke-a-service-using-jax-ws-library-files-that-use-swaref}

Voer de volgende stappen uit om het `MyApplication/EncryptDocument` proces aan te roepen met Java-proxybestanden die zijn gemaakt met JAX-WS en SwaRef:

1. Creeer de volmachtsklassen van Java gebruikend JAX-WS die de `MyApplication/EncryptDocument` dienst WSDL verbruikt. Gebruik het volgende eindpunt van WSDL:

   ```as3
    https://hiro-xp:8080/soap/services/MyApplication/EncryptDocument?WSDL&lc_version=9.0.1
   ```

   Zie Java-proxyklassen [maken met JAX-WS](#creating-java-proxy-classes-using-jax-ws)voor meer informatie.

   >[!NOTE]
   >
   >Vervangen `hiro-xp` *door het IP-adres van de J2EE-toepassingsserver die als host fungeert voor AEM Forms.*

1. Plaats de Java-proxyklassen die met JAX-WS zijn gemaakt in een JAR-bestand.
1. Neem het JAR-bestand voor de Java-proxy en de JAR-bestanden op in het volgende pad:

   &lt;Install Directory>\Adobe\Adobe_Experience_Manager_forms\sdk\client-libs\thirdparty

   in het klassenpad van uw Java-clientproject.

1. Maak een `MyApplicationEncryptDocumentService` object met de constructor ervan.
1. Maak een `MyApplicationEncryptDocument` object door de `MyApplicationEncryptDocumentService` methode van het `getEncryptDocument` object aan te roepen.
1. Stel de verbindingswaarden in die nodig zijn om AEM Forms aan te roepen door waarden toe te wijzen aan de volgende gegevensleden:

   * Wijs het eindpunt WSDL en het coderingstype aan het `javax.xml.ws.BindingProvider` gebied van het `ENDPOINT_ADDRESS_PROPERTY` voorwerp toe. Als u de `MyApplication/EncryptDocument` service wilt aanroepen met SwaRef-codering, geeft u de volgende URL-waarde op:

      ` https://hiro-xp:8080/soap/services/MyApplication/EncryptDocument?blob=swaref`

   * Wijs de gebruiker van AEM-formulieren toe aan het `javax.xml.ws.BindingProvider` veld van het `USERNAME_PROPERTY` object.
   * Wijs de bijbehorende wachtwoordwaarde toe aan het `javax.xml.ws.BindingProvider` veld van het `PASSWORD_PROPERTY` object.
   In het volgende codevoorbeeld wordt deze toepassingslogica getoond:

   ```as3
    //Set connection values required to invoke AEM Forms
    String url = "https://hiro-xp:8080/soap/services/MyApplication/EncryptDocument?blob=swaref";
    String username = "administrator";
    String password = "password";
    ((BindingProvider) encryptDocClient).getRequestContext().put(BindingProvider.ENDPOINT_ADDRESS_PROPERTY, url);
    ((BindingProvider) encryptDocClient).getRequestContext().put(BindingProvider.USERNAME_PROPERTY, username);
    ((BindingProvider) encryptDocClient).getRequestContext().put(BindingProvider.PASSWORD_PROPERTY, password);
   ```

1. Haal het PDF-document op dat u naar het `MyApplication/EncryptDocument` proces wilt verzenden door een `java.io.File` object te maken met de constructor ervan. Geef een tekenreekswaarde door die de locatie van het PDF-document aangeeft.
1. Maak een `javax.activation.DataSource` object met de `FileDataSource` constructor. Geef het `java.io.File` object door.
1. Maak een `javax.activation.DataHandler` object door de constructor ervan te gebruiken en het `javax.activation.DataSource` object door te geven.
1. Maak een `BLOB` object met de constructor ervan.
1. Vul het `BLOB` object door de `setSwaRef` methode aan te roepen en het `javax.activation.DataHandler` object door te geven.
1. Roep het `MyApplication/EncryptDocument` proces aan door de `MyApplicationEncryptDocument` methode van het `invoke` object aan te roepen en het `BLOB` object dat het PDF-document bevat door te geven. De aanroepmethode retourneert een `BLOB` object dat een versleuteld PDF-document bevat.
1. Vul een `javax.activation.DataHandler` object door de `BLOB` methode van het `getSwaRef` object aan te roepen.
1. Zet het `javax.activation.DataHandler` object om in een `java.io.InputSteam` instantie door de `javax.activation.DataHandler` methode van het `getInputStream` object aan te roepen.
1. Schrijf de `java.io.InputSteam` instantie naar een PDF-bestand dat het gecodeerde PDF-document vertegenwoordigt.

>[!NOTE]
>
>De meeste de dienstverrichtingen van Vormen AEM hebben een SwaRef snel begin. U kunt deze snelle begin in de overeenkomstige snelle beginsectie van de dienst bekijken. Zie bijvoorbeeld Snel aan de slag met de uitvoerservice-API voor informatie over de sectie Snelle start voor uitvoer [](/help/forms/developing/output-service-java-api-quick.md#output-service-java-api-quick-start-soap).

**Zie ook**

[Snel starten: Een service aanroepen met SwaRef in een Java-project](/help/forms/developing/invocation-api-quick-starts.md#quick-start-invoking-a-service-using-swaref-in-a-java-project)

## AEM-formulieren aanroepen met behulp van BLOB-gegevens via HTTP {#invoking-aem-forms-using-blob-data-over-http}

U kunt AEM Forms-services aanroepen met behulp van webservices en BLOB-gegevens via HTTP doorgeven. Het overbrengen van BLOB-gegevens via HTTP is een alternatieve techniek in plaats van het gebruik van base64-codering, DIME of MIME. Bijvoorbeeld, kunt u gegevens over HTTP in een project van Microsoft .NET overgaan dat de Verbetering 3.0 van de Dienst van het Web gebruikt, die geen DIME of MIME steunt. Wanneer u BLOB-gegevens via HTTP gebruikt, worden de invoergegevens geüpload voordat de AEM Forms-service wordt aangeroepen.

&quot;AEM-formulieren aanroepen met behulp van BLOB-gegevens via HTTP&quot; bespreekt het aanroepen van het volgende kortstondige AEM-proces dat wordt genoemd `MyApplication/EncryptDocument` door het doorgeven van BLOB-gegevens via HTTP.

>[!NOTE]
>
>Dit proces is niet gebaseerd op een bestaand AEM Forms-proces. Om samen met het codevoorbeeld te volgen, creeer een proces genoemd `MyApplication/EncryptDocument` gebruikend Workbench. (Zie [Workbench](https://www.adobe.com/go/learn_aemforms_workbench_63)gebruiken.)

Wanneer dit proces wordt aangeroepen, worden de volgende handelingen uitgevoerd:

1. Hiermee verkrijgt u het onbeveiligde PDF-document dat aan het proces wordt doorgegeven. Deze handeling is gebaseerd op de `SetValue` bewerking. De invoerparameter voor dit proces is een `document` procesvariabele met de naam `inDoc`.
1. Hiermee versleutelt u het PDF-document met een wachtwoord. Deze handeling is gebaseerd op de `PasswordEncryptPDF` bewerking. Het met wachtwoord gecodeerde PDF-document wordt geretourneerd in een procesvariabele met de naam `outDoc`.

>[!NOTE]
>
>Het wordt aanbevolen bekend te zijn met het aanroepen van AEM-formulieren met SOAP. (Zie [AEM-formulieren aanroepen met behulp van webservices](#invoking-aem-forms-using-web-services).)

### Creërend een .NET cliëntassemblage die gegevens over HTTP gebruikt {#creating-a-net-client-assembly-that-uses-data-over-http}

Om een cliëntassemblage tot stand te brengen die gegevens over HTTP gebruikt, volg het proces dat in het [Aanhalen van Vormen AEM gebruikend het Coderen](#invoking-aem-forms-using-base64-encoding)Base64 wordt gespecificeerd. Wijzig echter de URL in de proxyklasse om deze op te nemen `?blob=http` in plaats van `?blob=base64`. Deze actie zorgt ervoor dat de gegevens over HTTP worden overgegaan. Zoek in de proxyklasse de volgende coderegel:

```as3
 "http://localhost:8080/soap/services/MyApplication/EncryptDocument";
```

en wijzig deze in:

```as3
 "http://localhost:8080/soap/services/MyApplication/EncryptDocument?blob=http";
```

**Verwijzen naar de .NET clientMyApplication/EncryptDocument-verzameling**

Plaats uw nieuwe .NET cliëntassemblage op de computer waar u uw cliënttoepassing ontwikkelt. Nadat u de .NET cliëntassemblage in een folder plaatst, kunt u het van een project van verwijzingen voorzien. Verwijs naar de `System.Web.Services` bibliotheek van uw project. Als u niet naar deze bibliotheek van verwijzingen voorziet, kunt u niet de .NET cliëntassemblage gebruiken om de dienst aan te halen.

1. Selecteer Referentie **toevoegen in het menu** Project ****.
1. Klik op het tabblad **.NET** .
1. Klik op **Bladeren** en zoek het bestand DocumentService.dll.
1. Click **Select** and then click **OK**.

**Het aanhalen van de dienst die een .NET cliëntassemblage gebruikt die gegevens BLOB over HTTP gebruikt**

U kunt de `MyApplication/EncryptDocument` dienst (die in Workbench) werd gebouwd aanhalen gebruikend een .NET cliëntassemblage die gegevens over HTTP gebruikt. Voer de volgende stappen uit om de `MyApplication/EncryptDocument` service aan te roepen:

1. Creeer de .NET cliëntassemblage.
1. Verwijs naar de cliëntassemblage van Microsoft .NET. Creeer een project van cliëntMicrosoft .NET. Verwijs de de cliëntassemblage van Microsoft .NET in het cliëntproject. Verwijs ook `System.Web.Services`.
1. Gebruikend de de cliëntassemblage van Microsoft .NET, creeer een `MyApplication_EncryptDocumentService` voorwerp door zijn standaardaannemer aan te halen.
1. Stel de `MyApplication_EncryptDocumentService` eigenschap van het `Credentials` object in met een `System.Net.NetworkCredential` object. Geef binnen de `System.Net.NetworkCredential` constructor een gebruikersnaam voor AEM-formulieren en het bijbehorende wachtwoord op. Plaats authentificatiewaarden om uw .NET cliënttoepassing toe te laten om de berichten van de ZEEP met de Vormen van AEM met succes uit te wisselen.
1. Maak een `BLOB` object met de constructor ervan. Het `BLOB` object wordt gebruikt om gegevens door te geven aan het `MyApplication/EncryptDocument` proces.
1. Wijs een tekenreekswaarde toe aan het `BLOB` gegevenslid van het `remoteURL` object die de URI-locatie opgeeft van een PDF-document dat aan de `MyApplication/EncryptDocument`service moet worden doorgegeven.
1. Roep het `MyApplication/EncryptDocument` proces aan door de `MyApplication_EncryptDocumentService` methode van het `invoke` object aan te roepen en het `BLOB` object door te geven. Hiermee wordt een versleuteld PDF-document binnen een `BLOB` object geretourneerd.
1. Maak een `System.UriBuilder` object door de constructor ervan te gebruiken en de waarde van het gegevenslid van het geretourneerde `BLOB` `remoteURL` object door te geven.
1. Zet het `System.UriBuilder` object om in een `System.IO.Stream` object. (Het snelle Begin C# dat deze lijst volgt illustreert hoe te om deze taak uit te voeren.)
1. Maak een bytearray en vul deze met de gegevens in het `System.IO.Stream` object.
1. Maak een `System.IO.BinaryWriter` object door de constructor ervan aan te roepen en het `System.IO.FileStream` object door te geven.
1. Schrijf de inhoud van de bytearray naar een PDF-bestand door de methode van het `System.IO.BinaryWriter` `Write` object aan te roepen en de bytearray door te geven.

### Een service aanroepen met Java-proxyklassen en BLOB-gegevens via HTTP {#invoking-a-service-using-java-proxy-classes-and-blob-data-over-http}

U kunt een AEM Forms-service aanroepen met Java-proxyklassen en BLOB-gegevens via HTTP. Voer de volgende stappen uit om de `MyApplication/EncryptDocument` service aan te roepen met Java-proxyklassen:

1. Creeer de volmachtsklassen van Java gebruikend JAX-WS die de `MyApplication/EncryptDocument` dienst WSDL verbruikt. Gebruik het volgende eindpunt van WSDL:

   ```as3
    https://hiro-xp:8080/soap/services/MyApplication/EncryptDocument?WSDL&lc_version=9.0.1
   ```

   Zie Java-proxyklassen [maken met JAX-WS](#creating-java-proxy-classes-using-jax-ws)voor meer informatie.

   >[!NOTE]
   >
   >Vervangen `hiro-xp` *door het IP-adres van de J2EE-toepassingsserver die als host fungeert voor AEM Forms.*

1. Plaats de Java-proxyklassen die met JAX-WS zijn gemaakt in een JAR-bestand.
1. Neem het JAR-bestand voor de Java-proxy en de JAR-bestanden op in het volgende pad:

   &lt;Install Directory>\Adobe\Adobe_Experience_Manager_forms\sdk\client-libs\thirdparty

   in het klassenpad van uw Java-clientproject.

1. Maak een `MyApplicationEncryptDocumentService` object met de constructor ervan.
1. Maak een `MyApplicationEncryptDocument` object door de `MyApplicationEncryptDocumentService` methode van het `getEncryptDocument` object aan te roepen.
1. Stel de verbindingswaarden in die nodig zijn om AEM Forms aan te roepen door waarden toe te wijzen aan de volgende gegevensleden:

   * Wijs het eindpunt WSDL en het coderingstype aan het `javax.xml.ws.BindingProvider` gebied van het `ENDPOINT_ADDRESS_PROPERTY` voorwerp toe. Als u de `MyApplication/EncryptDocument` service wilt aanroepen met BLOB via HTTP-codering, geeft u de volgende URL-waarde op:

      `https://hiro-xp:8080/soap/services/MyApplication/EncryptDocument?blob=http`

   * Wijs de gebruiker van AEM-formulieren toe aan het `javax.xml.ws.BindingProvider` veld van het `USERNAME_PROPERTY` object.
   * Wijs de bijbehorende wachtwoordwaarde toe aan het `javax.xml.ws.BindingProvider` veld van het `PASSWORD_PROPERTY` object.
   In het volgende codevoorbeeld wordt deze toepassingslogica getoond:

   ```as3
    //Set connection values required to invoke AEM Forms
    String url = "https://hiro-xp:8080/soap/services/MyApplication/EncryptDocument?blob=http";
    String username = "administrator";
    String password = "password";
    ((BindingProvider) encryptDocClient).getRequestContext().put(BindingProvider.ENDPOINT_ADDRESS_PROPERTY, url);
    ((BindingProvider) encryptDocClient).getRequestContext().put(BindingProvider.USERNAME_PROPERTY, username);
    ((BindingProvider) encryptDocClient).getRequestContext().put(BindingProvider.PASSWORD_PROPERTY, password);
   ```

1. Maak een `BLOB` object met de constructor ervan.
1. Vul het `BLOB` object door de `setRemoteURL` methode ervan aan te roepen. Geef een tekenreekswaarde door die de URI-locatie opgeeft van een PDF-document dat aan de `MyApplication/EncryptDocument` service moet worden doorgegeven.
1. Roep het `MyApplication/EncryptDocument` proces aan door de `MyApplicationEncryptDocument` methode van het `invoke` object aan te roepen en het `BLOB` object dat het PDF-document bevat door te geven. Hiermee wordt een versleuteld PDF-document binnen een `BLOB` object geretourneerd.
1. Maak een bytearray om de gegevensstroom op te slaan die het gecodeerde PDF-document vertegenwoordigt. Roep de `BLOB` methode van het `getRemoteURL` object aan (gebruik het `BLOB` object dat door de `invoke` methode wordt geretourneerd).
1. Maak een `java.io.File` object met de constructor ervan. Dit object vertegenwoordigt het gecodeerde PDF-document.
1. Maak een `java.io.FileOutputStream` object door de constructor ervan te gebruiken en het `java.io.File` object door te geven.
1. Roep de `java.io.FileOutputStream` methode van het `write` object aan. Geef de bytearray door die de gegevensstroom bevat die het gecodeerde PDF-document vertegenwoordigt.

## AEM-formulieren aanroepen met DIME {#invoking-aem-forms-using-dime}

U kunt AEM Forms-services aanroepen met SOAP met bijlagen. AEM Forms ondersteunt zowel MIME- als DIME-webservicenormen. Met DIME kunt u binaire bijlagen, zoals PDF-documenten, samen met aanroepingsverzoeken verzenden in plaats van de bijlage te coderen. In de sectie *AEM-formulieren aanroepen met gebruik van DIME* wordt het aanroepen van het volgende kortstondige AEM Forms-proces met de naam `MyApplication/EncryptDocument` DIME besproken.

Wanneer dit proces wordt aangeroepen, worden de volgende handelingen uitgevoerd:

1. Hiermee verkrijgt u het onbeveiligde PDF-document dat aan het proces wordt doorgegeven. Deze handeling is gebaseerd op de `SetValue` bewerking. De invoerparameter voor dit proces is een `document` procesvariabele met de naam `inDoc`.
1. Hiermee versleutelt u het PDF-document met een wachtwoord. Deze handeling is gebaseerd op de `PasswordEncryptPDF` bewerking. Het met wachtwoord gecodeerde PDF-document wordt geretourneerd in een procesvariabele met de naam `outDoc`.

Dit proces is niet gebaseerd op een bestaand AEM Forms-proces. Om samen met de codevoorbeelden te volgen, creeer een proces genoemd `MyApplication/EncryptDocument` gebruikend Workbench. (Zie [Workbench](https://www.adobe.com/go/learn_aemforms_workbench_63)gebruiken.)

>[!NOTE]
>
>Het aanroepen van AEM Forms service-bewerkingen met DIME is afgekeurd. Het wordt aanbevolen MTOM te gebruiken. (Zie AEM-formulieren [aanroepen met MTOM](#invoking-aem-forms-using-mtom).)

### Het creëren van een .NET project dat DIME gebruikt {#creating-a-net-project-that-uses-dime}

Om een .NET project tot stand te brengen dat de dienst van Vormen kan aanhalen gebruikend DIME, voer de volgende taken uit:

* Installeer de Verbeteringen 2.0 van de Diensten van het Web op uw ontwikkelingscomputer.
* Van binnen uw .NET project, creeer een Webverwijzing naar de dienst van Vormen FormsAEM.

**Verbeteringen voor webservices 2.0 installeren**

Installeer de Verbeteringen 2.0 van de Diensten van het Web op uw ontwikkelingscomputer en integreer het met Microsoft Visual Studio .NET. U kunt de Verbeteringen 2.0 van de Diensten van het Web van het Centrum van de Download van [Microsoft downloaden.](https://www.microsoft.com/downloads/search.aspx)

Van deze Web-pagina, onderzoek naar de Verbeteringen van de Diensten van het Web 2.0 en download het op uw ontwikkelingscomputer. Met deze download plaatst u een bestand met de naam Microsoft WSE 2.0 SPI.msi op uw computer. Voer het installatieprogramma uit en volg de online instructies.

>[!NOTE]
>
>De Verbeteringen 2.0 van de Diensten van het Web steunen DIME. De gesteunde versie van Microsoft Visual Studio is 2003 wanneer het werken met de Verbeteringen van de Diensten van het Web 2.0. De Verbeteringen 3.0 van de Diensten van het Web steunen geen DIME; het ondersteunt echter MTOM.

**Een webverwijzing naar een AEM Forms-service maken**

Nadat u de Verbeteringen 2.0 van de Diensten van het Web op uw ontwikkelingscomputer installeert en een project van Microsoft .NET creeert, creeer een Webverwijzing naar de dienst van Vormen. Als u bijvoorbeeld een webverwijzing naar het `MyApplication/EncryptDocument` proces wilt maken en ervan wilt uitgaan dat Forms op de lokale computer is geïnstalleerd, geeft u de volgende URL op:

```as3
     http://localhost:8080/soap/services/MyApplication/EncryptDocument?WSDL
```

Nadat u een Webverwijzing creeert, zijn de volgende twee types van volmachtsgegevens beschikbaar voor u binnen uw .NET project te gebruiken: `EncryptDocumentService` en `EncryptDocumentServiceWse`. Als u het `MyApplication/EncryptDocument` proces wilt aanroepen met DIME, gebruikt u het `EncryptDocumentServiceWse` type.

>[!NOTE]
>
>Alvorens een Webverwijzing naar de dienst van Vormen tot stand te brengen, zorg ervoor dat u de Verbeteringen 2.0 van de Diensten van het Web in uw project van verwijzingen voorziet. (Zie &quot;De Verbeteringen 2.0 van de Diensten van het Web installeren&quot;.)

**Verwijzen naar de WSE-bibliotheek**

1. Selecteer Referentie toevoegen in het menu Project.
1. Selecteer Microsoft.Web.Services2.dll in het dialoogvenster Referentie toevoegen.
1. Selecteer System.Web.Services.dll.
1. Klik op Selecteren en vervolgens op OK.

**Een webverwijzing naar een Forms-service maken**

1. Selecteer Webverwijzing toevoegen in het menu Project.
1. Geef in het dialoogvenster URL de URL op naar de service Forms.
1. Klik op Ga en vervolgens op Referentie toevoegen.

>[!NOTE]
>
>Zorg ervoor dat u uw .NET project toelaat om de bibliotheek te gebruiken WSE. Van binnen de Ontdekkingsreiziger van het Project, klik de projectnaam met de rechtermuisknop aan en selecteer toelaten WSE 2.0. Zorg ervoor dat het selectievakje in het dialoogvenster dat wordt weergegeven, is ingeschakeld.

**Het aanhalen van de dienst die DIME in een .NET project gebruikt**

U kunt een Forms-service aanroepen met DIME. Neem bijvoorbeeld het `MyApplication/EncryptDocument` proces waarbij een onbeveiligd PDF-document wordt geaccepteerd en een PDF-document met een wachtwoord wordt geretourneerd. Voer de volgende stappen uit om het `MyApplication/EncryptDocument` proces met DIME aan te roepen:

1. Creeer een project van Microsoft .NET dat u toelaat om de dienst van Vormen aan te halen gebruikend DIME. Zorg ervoor dat u de Verbeteringen 2.0 van de Diensten van het Web omvat en creeer een Webverwijzing naar de dienst van Vormen AEM.
1. Nadat u een webverwijzing naar het `MyApplication/EncryptDocument` proces hebt ingesteld, maakt u een `EncryptDocumentServiceWse` object met behulp van de standaardconstructor.
1. Stel het `EncryptDocumentServiceWse` gegevenslid van het `Credentials` object in met een `System.Net.NetworkCredential` waarde die de gebruikersnaam en het wachtwoord voor AEM-formulieren opgeeft.
1. Maak een `Microsoft.Web.Services2.Dime.DimeAttachment` object door de constructor ervan te gebruiken en de volgende waarden door te geven:

   * Een koordwaarde die een waarde GUID specificeert. U kunt een waarde verkrijgen GUID door de `System.Guid.NewGuid.ToString` methode aan te halen.
   * Een tekenreekswaarde die het inhoudstype opgeeft. Voor dit proces is een PDF-document vereist. Geef daarom op `application/pdf`.
   * Een `TypeFormat` opsommingswaarde. Geef `TypeFormat.MediaType`op.
   * Een tekenreekswaarde die de locatie opgeeft van het PDF-document dat moet worden doorgegeven aan het AEM Forms-proces.

1. Maak een `BLOB` object met de constructor ervan.
1. Voeg de DIME-bijlage aan het `BLOB` object toe door de waarde van het `Microsoft.Web.Services2.Dime.DimeAttachment` gegevenslid van het `Id` object toe te wijzen aan het `BLOB` gegevenslid van het `attachmentID` object.
1. Roep de `EncryptDocumentServiceWse.RequestSoapContext.Attachments.Add` methode aan en geef het `Microsoft.Web.Services2.Dime.DimeAttachment` object door.
1. Roep het `MyApplication/EncryptDocument` proces aan door de `EncryptDocumentServiceWse` methode van het `invoke` object aan te roepen en het `BLOB` object met de DIME-bijlage door te geven. Hiermee wordt een versleuteld PDF-document binnen een `BLOB` object geretourneerd.
1. Verkrijg de waarde van gehechtheid herkenningsteken door de waarde van het teruggekeerde `BLOB` gegevenslid van `attachmentID` objecten te krijgen.
1. Doorloop de bijlagen in `EncryptDocumentServiceWse.ResponseSoapContext.Attachments` en gebruik de waarde van de bijlage-id om het gecodeerde PDF-document te verkrijgen.
1. Haal een `System.IO.Stream` object op door de waarde van het `Attachment` `Stream` gegevenslid van het object op te halen.
1. Maak een bytearray en geef die bytearray door aan de `System.IO.Stream` methode van het `Read` object. Met deze methode wordt de bytearray gevuld met een gegevensstroom die het gecodeerde PDF-document vertegenwoordigt.
1. Maak een `System.IO.FileStream` object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die een locatie van een PDF-bestand vertegenwoordigt. Dit object vertegenwoordigt het gecodeerde PDF-document.
1. Maak een `System.IO.BinaryWriter` object door de constructor ervan aan te roepen en het `System.IO.FileStream` object door te geven.
1. Schrijf de inhoud van de bytearray naar het PDF-bestand door de methode van het `System.IO.BinaryWriter` `Write` object aan te roepen en de bytearray door te geven.

### Apache Axis Java-proxyklassen maken die gebruikmaken van DIME {#creating-apache-axis-java-proxy-classes-that-use-dime}

Met het hulpprogramma Apache Axis WSDL2Java kunt u een service-WSDL converteren naar Java-proxyklassen, zodat u servicebewerkingen kunt activeren. Met Apache Ant kunt u Axis-bibliotheekbestanden genereren op basis van een WSDL-service van AEM Forms waarmee u de service kunt aanroepen. (Zie Java-proxyklassen [maken met Apache Axis](#creating-java-proxy-classes-using-apache-axis).)

Met het hulpprogramma Apache Axis WSDL2Java worden JAVA-bestanden gegenereerd die methoden bevatten die worden gebruikt om SOAP-aanvragen naar een service te verzenden. De verzoeken van de ZEEP die door de dienst worden ontvangen worden gedecodeerd door de as-Gegenereerde bibliotheken en worden terug gezet in de methodes en de argumenten.

Voer de volgende stappen uit om de `MyApplication/EncryptDocument` service (die in Workbench is ingebouwd) aan te roepen met behulp van door Axis gegenereerde bibliotheekbestanden en DIME:

1. Maak Java-proxyklassen die de `MyApplication/EncryptDocument` service WSDL gebruiken met Apache Axis. (Zie Java-proxyklassen [maken met Apache Axis](#creating-java-proxy-classes-using-apache-axis).)
1. Neem de Java-proxyklassen op in het klassepad.
1. Maak een `MyApplicationEncryptDocumentServiceLocator` object met de constructor ervan.
1. Maak een `URL` object door de constructor ervan te gebruiken en een tekenreekswaarde door te geven die de WSDL-definitie van de AEM Forms service aangeeft. Zorg ervoor dat u `?blob=dime` aan het eind van het eindpunt URL van de ZEEP specificeert. Gebruik bijvoorbeeld

   ```as3
    https://hiro-xp:8080/soap/services/MyApplication/EncryptDocument?blob=dime.
   ```

1. Maak een `EncryptDocumentSoapBindingStub` object door de constructor ervan aan te roepen en het `MyApplicationEncryptDocumentServiceLocator`object en het `URL` object door te geven.
1. Stel de gebruikersnaam en het wachtwoord voor AEM-formulieren in door de methoden `EncryptDocumentSoapBindingStub` en methoden van het `setUsername` `setPassword` object aan te roepen.

   ```as3
    encryptionClientStub.setUsername("administrator");
    encryptionClientStub.setPassword("password");
   ```

1. U kunt het PDF-document ophalen om naar de `MyApplication/EncryptDocument` service te verzenden door een `java.io.File` object te maken. Geef een tekenreekswaarde door die de locatie van het PDF-document aangeeft.
1. Maak een `javax.activation.DataHandler` object door de constructor ervan te gebruiken en een `javax.activation.FileDataSource` object door te geven. U kunt het `javax.activation.FileDataSource` object maken door de constructor ervan te gebruiken en het `java.io.File` object dat het PDF-document vertegenwoordigt door te geven.
1. Maak een `org.apache.axis.attachments.AttachmentPart` object door de constructor ervan te gebruiken en het `javax.activation.DataHandler` object door te geven.
1. Koppel de bijlage door de methode van het `EncryptDocumentSoapBindingStub` object aan te roepen `addAttachment` en het `org.apache.axis.attachments.AttachmentPart` object door te geven.
1. Maak een `BLOB` object met de constructor ervan. Vul het `BLOB` object met de waarde van de bijlage-id door de methode van het `BLOB` `setAttachmentID` object aan te roepen en de waarde van de bijlage-id door te geven. Deze waarde kan worden verkregen door de `org.apache.axis.attachments.AttachmentPart` methode van het `getContentId` object aan te roepen.
1. Roep het `MyApplication/EncryptDocument` proces aan door de `EncryptDocumentSoapBindingStub` methode van het `invoke` object aan te roepen. Geef het `BLOB` object met de DIME-bijlage door. Hiermee wordt een versleuteld PDF-document binnen een `BLOB` object geretourneerd.
1. Haal de waarde van de gehechtheid-id op door de `BLOB` methode van het teruggekeerde `getAttachmentID` voorwerp aan te halen. Deze methode retourneert een tekenreekswaarde die de id-waarde van de geretourneerde bijlage vertegenwoordigt.
1. Haal de bijlagen op door de `EncryptDocumentSoapBindingStub` methode van het `getAttachments` object aan te roepen. Deze methode retourneert een array van `Objects` die de bijlagen vertegenwoordigen.
1. Doorloop de bijlagen (de `Object` array) en gebruik de waarde van de bijlage-id om het gecodeerde PDF-document te verkrijgen. Elk element is een `org.apache.axis.attachments.AttachmentPart` object.
1. Haal het `javax.activation.DataHandler` object op dat aan de bijlage is gekoppeld door de `org.apache.axis.attachments.AttachmentPart` methode van het `getDataHandler` object aan te roepen.
1. Haal een `java.io.FileStream` object op door de `javax.activation.DataHandler` methode van het `getInputStream` object aan te roepen.
1. Maak een bytearray en geef die bytearray door aan de `java.io.FileStream` methode van het `read` object. Met deze methode wordt de bytearray gevuld met een gegevensstroom die het gecodeerde PDF-document vertegenwoordigt.
1. Maak een `java.io.File` object met de constructor ervan. Dit object vertegenwoordigt het gecodeerde PDF-document.
1. Maak een `java.io.FileOutputStream` object door de constructor ervan te gebruiken en het `java.io.File` object door te geven.
1. Roep de methode van het `java.io.FileOutputStream` object aan `write` en geef de bytearray door die de gegevensstroom bevat die het gecodeerde PDF-document vertegenwoordigt.

**Zie ook**

[Snel starten: Een service aanroepen met DIME in een Java-project](/help/forms/developing/invocation-api-quick-starts.md#quick-start-invoking-a-service-using-dime-in-a-java-project)

## Op SAML gebaseerde verificatie gebruiken {#using-saml-based-authentication}

AEM Forms ondersteunt verschillende verificatiemodi voor webservices bij het aanroepen van services. Één authentificatiemodus specificeert zowel een gebruikersnaam als wachtwoordwaarde gebruikend een basisvergunningskopbal in de vraag van de Webdienst. AEM Forms steunt ook op bevestiging-gebaseerde authentificatie SAML. Wanneer een clienttoepassing een AEM Forms-service aanroept met behulp van een webservice, kan de clienttoepassing op een van de volgende manieren verificatiegegevens opgeven:

* Bevoegdheden doorgeven als onderdeel van de basisautorisatie
* Gebruikersnaam-token doorgeven als onderdeel van de WS-Security-header
* Het overgaan van een bevestiging van SAML als deel van WS-Veiligheid kopbal
* Het overgaan van het teken Kerberos als deel van WS-Veiligheid kopbal

AEM Forms ondersteunt geen standaardverificatie op basis van certificaten, maar wel verificatie op basis van certificaten in een ander formulier.

>[!NOTE]
>
>De webservice begint snel met Programmeren met AEM Forms en geeft gebruikersnaam en wachtwoord op om autorisatie uit te voeren.

De identiteit van gebruikers van AEM-formulieren kan worden weergegeven via een SAML-bevestiging die is ondertekend met een geheime sleutel. De volgende code van XML toont een voorbeeld van een bewering van SAML.

```as3
 <Assertion xmlns="urn:oasis:names:tc:SAML:1.0:assertion"
     xmlns:saml="urn:oasis:names:tc:SAML:1.0:assertion"
     xmlns:samlp="urn:oasis:names:tc:SAML:1.0:protocol"
     AssertionID="fd4bd0c87302780e0d9bbfa8726d5bc0" IssueInstant="2008-04-17T13:47:00.720Z" Issuer="LiveCycle"
     MajorVersion="1" MinorVersion="1">
     <Conditions NotBefore="2008-04-17T13:47:00.720Z" NotOnOrAfter="2008-04-17T15:47:00.720Z">
     </Conditions>
     <AuthenticationStatement
         AuthenticationInstant="2008-04-17T13:47:00.720Z"
         AuthenticationMethod="urn:oasis:names:tc:SAML:1.0:am:unspecified">
         <Subject>
             <NameIdentifier NameQualifier="DefaultDom">administrator</NameIdentifier>
             <SubjectConfirmation>
                 <ConfirmationMethod>urn:oasis:names:tc:SAML:1.0:cm:sender-vouches</ConfirmationMethod>
             </SubjectConfirmation>
         </Subject>
     </AuthenticationStatement>
     <ds:Signature >
         <ds:SignedInfo>
             <ds:CanonicalizationMethod Algorithm="https://www.w3.org/2001/10/xml-exc-c14n#"></ds:CanonicalizationMethod>
             <ds:SignatureMethod    Algorithm="https://www.w3.org/2000/09/xmldsig#hmac-sha1"></ds:SignatureMethod>
             <ds:Reference URI="#fd4bd0c87302780e0d9bbfa8726d5bc0">
                 <ds:Transforms>
                     <ds:Transform Algorithm="https://www.w3.org/2000/09/xmldsig#enveloped-signature"></ds:Transform>
                     <ds:Transform Algorithm="https://www.w3.org/2001/10/xml-exc-c14n#">
                         <ec:InclusiveNamespaces
                             PrefixList="code ds kind rw saml samlp typens #default">
                         </ec:InclusiveNamespaces>
                     </ds:Transform>
                 </ds:Transforms>
                 <ds:DigestMethod Algorithm="https://www.w3.org/2000/09/xmldsig#sha1"></ds:DigestMethod>
                 <ds:DigestValue>hVrtqjWr+VzaVUIpQx0YI9lIjaY=</ds:DigestValue>
             </ds:Reference>
         </ds:SignedInfo>
         <ds:SignatureValue>UMbBb+cUcPtcWDCIhXes4n4FxfU=</ds:SignatureValue>
     </ds:Signature>
 </Assertion>
```

Deze voorbeeldbewering wordt uitgegeven voor een beheerdergebruiker. Deze bewering bevat de volgende opvallende items:

* Deze is gedurende een bepaalde periode geldig.
* Het wordt uitgegeven voor een bepaalde gebruiker.
* Het is digitaal ondertekend. Elke wijziging die er wordt aangebracht, zou dus de handtekening breken.
* Deze kan aan AEM Forms als teken van de identiteit van de gebruiker gelijkend op gebruikersnaam en wachtwoord worden voorgesteld.

Een clienttoepassing kan de bevestiging ophalen vanuit elke API van AEM Forms AuthenticationManager die een `AuthResult` object retourneert. U kunt een `AuthResult` instantie verkrijgen door een van de volgende twee methoden uit te voeren:

* Het verifiëren van de gebruiker die om het even welke authentiek methodes gebruikt die door AuthenticationManager API worden blootgesteld. Doorgaans wordt de gebruikersnaam en het wachtwoord gebruikt. nochtans, kunt u de certificaatauthentificatie ook gebruiken.
* De `AuthenticationManager.getAuthResultOnBehalfOfUser` methode gebruiken. Met deze methode kan een clienttoepassing een `AuthResult` object ophalen voor elke gebruiker van AEM-formulieren.

Een gebruiker van AEM-formulieren kan worden geverifieerd met een SAML-token dat is verkregen. Deze bevestiging van SAML (xml- fragment) kan als deel van de WS-Veiligheid kopbal met de vraag van de Webdienst voor gebruikersauthentificatie worden verzonden. Een clienttoepassing heeft doorgaans een gebruiker geverifieerd, maar heeft de gebruikersgegevens niet opgeslagen. (Of de gebruiker heeft het programma geopend aan die cliënt door een ander mechanisme dan het gebruiken van een gebruikersnaam en een wachtwoord.) In deze situatie moet de clienttoepassing AEM Forms aanroepen en zich een specifieke gebruiker voorstellen die AEM Forms mag aanroepen.

Als u een bepaalde gebruiker wilt verpersoonlijken, roept u de `AuthenticationManager.getAuthResultOnBehalfOfUser` methode aan met behulp van een webservice. Deze methode keert een `AuthResult` geval terug dat de bevestiging van SAML voor die gebruiker bevat.

Daarna, gebruik die bevestiging SAML om het even welke dienst aan te halen die authentificatie vereist. Deze actie omvat het verzenden van de bevestiging als deel van de kopbal van de ZEEP. Wanneer met deze bewering een webserviceaanroep wordt gemaakt, identificeert AEM Forms de gebruiker als de gebruiker die door die bewering wordt vertegenwoordigd. Namelijk is de gebruiker die in de bewering wordt gespecificeerd de gebruiker die de dienst aanhaalt.

### Het gebruiken van de klassen van de As van Apache en op SAML-Gebaseerde authentificatie {#using-apache-axis-classes-and-saml-based-authentication}

U kunt een AEM Forms-service aanroepen door Java-proxyklassen die zijn gemaakt met de Axis-bibliotheek. (Zie Java-proxyklassen [maken met Apache Axis](#creating-java-proxy-classes-using-apache-axis).)

Wanneer het gebruiken van AXIS die op SAML-Gebaseerde authentificatie gebruikt, registreer de verzoek en reactiemanager met As. Apache Axis roept de handler aan voordat een aanroepingsverzoek naar AEM Forms wordt verzonden. Als u een handler wilt registreren, maakt u een Java-klasse die wordt uitgebreid `org.apache.axis.handlers.BasicHandler`.

**Creeer een AssertionHandler met As**

De volgende Java-klasse met de naam `AssertionHandler.java`toont een voorbeeld van een Java-klasse die een uitbreiding vormt `org.apache.axis.handlers.BasicHandler`.

```as3
 public class AssertionHandler extends BasicHandler {
        public void invoke(MessageContext ctx) throws AxisFault {
            String assertion = (String) ctx.getProperty(LC_ASSERTION);
 
            //no assertion hence nothing to insert
            if(assertion == null) return;
 
            try {
                MessageElement samlElement = new MessageElement(convertToXML(assertion));
                SOAPHeader header = (SOAPHeader) ctx.getRequestMessage().getSOAPHeader();
                //Create the wsse:Security element which would contain the SAML element
                SOAPElement wsseHeader = header.addChildElement("Security", "wsse", WSSE_NS);
                wsseHeader.appendChild(samlElement);
                //remove the actor attribute as in LC we do not specify any actor. This would not remove the actor attribute though
                //it would only remove it from the soapenv namespace
                wsseHeader.getAttributes().removeNamedItem("actor");
            } catch (SOAPException e) {
                throw new AxisFault("Error occured while adding the assertion to the SOAP Header",e);
            }
        }
 }
```

**De handler registreren**

Om een manager bij As te registreren, creeer een cliënt-config.wsdd- dossier. Standaard zoekt Axis naar een bestand met deze naam. De volgende XML-code is een voorbeeld van een client-config.wsdd-bestand. Zie de documentatie van de As voor meer informatie.

```as3
 <deployment xmlns="https://xml.apache.org/axis/wsdd/" xmlns:java="https://xml.apache.org/axis/wsdd/providers/java">
     <transport name="http" pivot="java:org.apache.axis.transport.http.HTTPSender"/>
      <globalConfiguration >
       <requestFlow >
        <handler type="java:com.adobe.idp.um.example.AssertionHandler" />
       </requestFlow >
      </globalConfiguration >
 </deployment>
 
```

**Een AEM Forms-service aanroepen**

Het volgende codevoorbeeld roept de dienst van Vormen AEM gebruikend op SAML-Gebaseerde authentificatie aan.

```as3
 public class ImpersonationExample {
        . . .
        public void  authenticateOnBehalf(String superUsername,String password,
                String canonicalName,String domainName) throws UMException, RemoteException{
            ((org.apache.axis.client.Stub) authenticationManager).setUsername(superUsername);
            ((org.apache.axis.client.Stub) authenticationManager).setPassword(password);
 
            //Step 1 - Invoke the Auth manager api to get an assertion for the user to be impersonated
            AuthResult ar = authenticationManager.getAuthResultOnBehalfOfUser(canonicalName, domainName, null);
            String assertion = ar.getAssertion();
            //Step 2 - Setting the assertion here to be picked later by the AssertionHandler. Note that stubs are not threadSafe
            //hence should not be reused. For this simple example we have made them instance variable but care should be taken
            //regarding the thread safety
            ((javax.xml.rpc.Stub) authorizationManager)._setProperty(AssertionHandler.LC_ASSERTION, assertion);
        }
 
        public Role findRole(String roleId) throws UMException, RemoteException{
            //This api would be invoked under bob's user rights
            return authorizationManager.findRole(roleId);
        }
 
        public static void main(String[] args) throws Exception {
            ImpersonationExample ie = new ImpersonationExample("http://localhost:5555");
            //Get the SAML assertion for the user to impersonate and store it in stub
            ie.authenticateOnBehalf(
                    "administrator", //The Super user which has the required impersonation permission
                    "password", // Password of the super user as referred above
                    "bob", //Cannonical name of the user to impersonate
                    "testdomain" //Domain of the user to impersonate
                    );
 
            Role r = ie.findRole("BASIC_ROLE_ADMINISTRATOR");
            System.out.println("Role "+r.getName());
        }
 }
```

### Het gebruiken van een .NET cliëntassemblage en op SAML-Gebaseerde authentificatie {#using-a-net-client-assembly-and-saml-based-authentication}

U kunt de dienst van Vormen aanhalen door een .NET cliëntassemblage en op SAML-Gebaseerde authentificatie te gebruiken. Om dit te doen, moet u de Verbeteringen 3.0 van de Dienst van het Web (WSE) gebruiken. Voor informatie over het creëren van een .NET cliëntassemblage die WSE gebruikt, zie het [Creëren van een .NET project dat DIME](#creating-a-net-project-that-uses-dime)gebruikt.

>[!NOTE]
>
>In de sectie DIME wordt WSE 2.0 gebruikt. Om op SAML-Gebaseerde authentificatie te gebruiken, volg de zelfde instructies die in het DIME onderwerp worden gespecificeerd. Vervang WSE 2.0 echter door WSE 3.0. Installeer de Verbeteringen 3.0 van de Diensten van het Web op uw ontwikkelingscomputer en integreer het met Microsoft Visual Studio .NET. U kunt de Verbeteringen 3.0 van de Diensten van het Web van het Centrum [van de Download van](https://www.microsoft.com/downloads/search.aspx)Microsoft downloaden.

De architectuur WSE gebruikt Beleid, Assertions, en de gegevenstypes SecurityToken. Geef voor een webserviceaanroep kort een beleid op. Een beleid kan meerdere beweringen hebben. Elke bewering kan filters bevatten. Een filter wordt aangehaald in bepaalde stadia in een vraag van de Webdienst en, op dat ogenblik, kunnen zij het verzoek van de ZEEP wijzigen. Voor volledige details, zie de Verbeteringen 3.0 van de Dienst van het Web documentatie.

**De bevestiging en het filter maken**

In het volgende C#-codevoorbeeld worden filter- en assertieklassen gemaakt. In dit codevoorbeeld wordt een SamlAssertionOutputFilter gemaakt. Dit filter wordt aangehaald door het kader van WSE alvorens het verzoek van de ZEEP wordt verzonden naar Vormen AEM.

```as3
 class LCSamlPolicyAssertion : Microsoft.Web.ServicES4.Design.PolicyAssertion
 {
        public override Microsoft.Web.ServicES4.SoapFilter CreateClientOutputFilter(FilterCreationContext context)
        {
           return new SamlAssertionOutputFilter();
        }
        . . .
 }
 
 
 class SamlAssertionOutputFilter : SendSecurityFilter
 {
        public override void SecureMessage(SoapEnvelope envelope, Security security)
        {
           // Get the SamlToken from the SessionState
           SamlToken samlToken = envelope.Context.Credentials.UltimateReceiver.GetClientToken<SamlToken>();
           security.Tokens.Add(samlToken);
        }
 }
```

**SAML-token maken**

Creeer een klasse om de bewering van SAML te vertegenwoordigen. De belangrijkste taak die deze klasse uitvoert, is het omzetten van gegevenswaarden van tekenreeks in xml en het behouden van witruimte. Deze bewering-xml wordt later geïmporteerd in de SOAP-aanvraag.

```as3
 class SamlToken : SecurityToken
 {
        public const string SAMLAssertion = "https://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1";
        private XmlElement _assertionElement;
 
        public SamlToken(string assertion)
             : base(SAMLAssertion)
        {
           XmlDocument xmlDoc = new XmlDocument();
           //The white space has to be preserved else the digital signature would get broken
           xmlDoc.PreserveWhitespace = true;
           xmlDoc.LoadXml(assertion);
           _assertionElement = xmlDoc.DocumentElement;
         }
 
         public override XmlElement GetXml(XmlDocument document)
         {
            return (XmlElement)document.ImportNode(_assertionElement, true);
         }
        . . .
 }
```

**Een AEM Forms-service aanroepen**

Het volgende C# codevoorbeeld roept de dienst van Vormen door op SAML-Gebaseerde authentificatie te gebruiken aan.

```as3
 public class ImpersonationExample
 {
        . . .
        public void AuthenticateOnBehalf(string superUsername, string password, string canonicalName, string domainName)
        {
            //Create a policy for UsernamePassword Token
            Policy usernamePasswordPolicy = new Policy();
            usernamePasswordPolicy.Assertions.Add(new UsernameOverTransportAssertion());
 
            UsernameToken token = new UsernameToken(superUsername, password, PasswordOption.SendPlainText);
            authenticationManager.SetClientCredential(token);
            authenticationManager.SetPolicy(usernamePasswordPolicy);
 
            //Get the SAML assertion for impersonated user
            AuthClient.AuthenticationManagerService.AuthResult ar
                = authenticationManager.getAuthResultOnBehalfOfUser(canonicalName, domainName, null);
            System.Console.WriteLine("Received assertion " + ar.assertion);
 
            //Create a policy for inserting SAML assertion
            Policy samlPolicy = new Policy();
            samlPolicy.Assertions.Add(new LCSamlPolicyAssertion());
            authorizationManager.SetPolicy(samlPolicy);
            //Set the SAML assertion obtained previously as the token
            authorizationManager.SetClientCredential(new SamlToken(ar.assertion));
        }
 
        public Role findRole(string roleId)
        {
            return authorizationManager.findRole(roleId);
        }
 
        static void Main(string[] args)
        {
            ImpersonationExample ie = new ImpersonationExample("http://localhost:5555");
            ie.AuthenticateOnBehalf(
                 "administrator", //The Super user which has the required impersonation permission
                 "password", // Password of the super user as referred above
                 "bob", //Cannonical name of the user to impersonate
                 "testdomain" //Domain of the user to impersonate
                 );
 
         Role r = ie.findRole("BASIC_ROLE_ADMINISTRATOR");
            System.Console.WriteLine("Role "+r.name);
     }
 }
```

## Verwante overwegingen bij het gebruik van webservices {#related-considerations-when-using-web-services}

Soms doen zich problemen voor wanneer bepaalde services van AEM Forms worden aangeroepen met behulp van webservices. Het doel van deze discussie is om die kwesties te identificeren en een oplossing te bieden, als die beschikbaar is.

### Asynchroon dienstenbewerkingen aanroepen {#invoking-service-operations-asynchronously}

Als u probeert een servicebewerking in AEM Forms asynchroon aan te roepen, zoals de `htmlToPDF` bewerking PDF genereren, treedt een `SoapFaultException` fout op. U lost dit probleem op door een XML-bestand met aangepaste binding te maken waarin het `ExportPDF_Result` element en andere elementen in verschillende klassen worden ingedeeld. De volgende XML vertegenwoordigt een aangepast bindingsbestand.

```as3
 <bindings
        xmlns:xsd="https://www.w3.org/2001/XMLSchema"
        xmlns:jxb="https://java.sun.com/xml/ns/jaxb" jxb:version="1.0"
        xmlns:wsdl="https://schemas.xmlsoap.org/wsdl/"
      wsdlLocation="http://localhost:8080/soap/services/GeneratePDFService?wsdl&async=true&lc_version=9.0.0"
        xmlns="https://java.sun.com/xml/ns/jaxws">
        <enableAsyncMapping>false</enableAsyncMapping>
        <package name="external_customize.client"/>
        <enableWrapperStyle>true</enableWrapperStyle>
        <bindings node="/wsdl:definitions/wsdl:types/xsd:schema[@targetNamespace='https://adobe.com/idp/services']/xsd:element[@name='ExportPDF_Result']">
            <jxb:class name="ExportPDFAsyncResult">
            </jxb:class>
        </bindings>
        <bindings node="/wsdl:definitions/wsdl:types/xsd:schema[@targetNamespace='https://adobe.com/idp/services']/xsd:element[@name='CreatePDF_Result']">
            <jxb:class name="CreatePDFAsyncResult">
            </jxb:class>
        </bindings>
        <bindings node="/wsdl:definitions/wsdl:types/xsd:schema[@targetNamespace='https://adobe.com/idp/services']/xsd:element[@name='HtmlToPDF_Result']">
            <jxb:class name="HtmlToPDFAsyncResult">
            </jxb:class>
        </bindings>
        <bindings node="/wsdl:definitions/wsdl:types/xsd:schema[@targetNamespace='https://adobe.com/idp/services']/xsd:element[@name='OptimizePDF_Result']">
            <jxb:class name="OptimizePDFAsyncResult">
            </jxb:class>
        </bindings>
        <!--bindings node="//wsdl:portType[@name='GeneratePDFService']/wsdl:operation[@name='HtmlToPDF_Result']">
            <jxb:class name="HtmlToPDFAsyncResult"/>
        </bindings-->
 </bindings>
```

Gebruik dit XML-bestand wanneer u Java-proxybestanden maakt met JAX-WS. (Zie Java-proxyklassen [maken met JAX-WS](#creating-java-proxy-classes-using-jax-ws).)

Verwijs dit dossier van XML wanneer het uitvoeren van het hulpmiddel JAX-WS (wsimport.exe) door - de optie van de bevellijn te gebruiken `b` . Werk het `wsdlLocation` element in het bindende dossier van XML bij om URL van Vormen te specificeren AEM.

Om ervoor te zorgen dat asynchrone aanroep werkt, wijzigt u de URL-eindpuntwaarde en geeft u deze op `async=true`. Voor Java-proxybestanden die met JAX-WS zijn gemaakt, geeft u bijvoorbeeld het volgende op voor de `BindingProvider.ENDPOINT_ADDRESS_PROPERTY`code.

`https://server:port/soap/services/ServiceName?wsdl&async=true&lc_version=9.0.0`

In de volgende lijst worden andere services opgegeven waarvoor een aangepast bindingsbestand nodig is wanneer dit asynchroon wordt aangeroepen:

* PDFG3D
* Taakbeheer
* Toepassingsbeheer
* Directorybeheer
* Distiller
* Rechtenbeheer
* Documentbeheer

### Verschillen in J2EE-toepassingsservers {#differences-in-j2ee-application-servers}

Soms roept een proxybibliotheek die is gemaakt met een specifieke J2EE-toepassingsserver niet met succes AEM-formulieren aan die worden gehost op een andere J2EE-toepassingsserver. Overweeg een volmachtsbibliotheek die gebruikend Vormen AEM wordt geproduceerd die op WebSphere wordt opgesteld. Deze volmachtsbibliotheek kan de geen diensten van Vormen AEM aanhalen die op de Server van de Toepassing JBoss worden opgesteld.

Sommige Vormen AEM complexe gegevenstypes, zoals `PrincipalReference`, verschillend worden bepaald wanneer de Vormen AEM op WebSphere in vergelijking met de Server van de Toepassing JBoss wordt opgesteld. Verschillen in JDKs die door de verschillende J2EE toepassingsdiensten worden gebruikt zijn de reden waarom er verschillen in WSDL definities zijn. Het resultaat is dat u proxybibliotheken gebruikt die op dezelfde J2EE-toepassingsserver worden gegenereerd.

### Toegang tot meerdere services via webservices {#accessing-multiple-services-using-web-services}

Vanwege naamruimteconflicten kunnen gegevensobjecten niet worden gedeeld tussen meerdere service-WSDL&#39;s. De verschillende diensten kunnen gegevenstypes delen en, daarom delen de diensten de definitie van deze types in WSDLs. Bijvoorbeeld, kunt u niet twee .NET cliëntassemblage toevoegen die een `BLOB` gegevenstype aan het zelfde .NET cliëntproject bevatten. Als u dit probeert, treedt er een compilatiefout op.

De volgende lijst specificeert gegevenstypes die niet tussen veelvoudige dienst WSDLs kunnen worden gedeeld:

* `User`
* `Principals`
* `PrincipalReference`
* `Groups`
* `Roles`
* `BLOB`

Om dit probleem te voorkomen, wordt u aangeraden de gegevenstypen volledig te kwalificeren. Bijvoorbeeld, overweeg een .NET toepassing die zowel de dienst van Vormen als de dienst van de Handtekening gebruikend een de dienstverwijzing van verwijzingen voorziet. Beide de dienstverwijzingen zullen een `BLOB` klasse bevatten. Als u een `BLOB` instantie wilt gebruiken, moet u het `BLOB` object bij het declareren volledig kwalificeren. Deze benadering wordt getoond in het volgende codevoorbeeld. Zie Interactieve formulieren [digitaal ondertekenen voor meer informatie over dit codevoorbeeld](/help/forms/developing/digitally-signing-certifying-documents.md#digitally-signing-interactive-forms).

Het volgende C# codevoorbeeld ondertekent een interactief formulier dat door de dienst van Vormen wordt teruggegeven. De clienttoepassing heeft twee serviceverwijzingen. De `BLOB` instantie die aan de service Forms is gekoppeld, behoort tot de `SignInteractiveForm.ServiceReference2` naamruimte. Op dezelfde manier behoort de `BLOB` instantie die aan de handtekeningservice is gekoppeld tot de `SignInteractiveForm.ServiceReference1` naamruimte. Het ondertekende interactieve formulier wordt opgeslagen als een PDF-bestand met de naam *LoanXFASigned.pdf*.

```as3
 ???/**
     * Ensure that you create a .NET project that uses
     * MS Visual Studio 2008 and version 3.5 of the .NET
     * framework. This is required to invoke a
     * AEM Forms service using MTOM.
     *
     * For information, see "Invoking AEM Forms using MTOM" in Programming with AEM forms
     */
 using System;
 using System.Collections.Generic;
 using System.Linq;
 using System.Text;
 using System.ServiceModel;
 using System.IO;
 
 //A reference to the Signature service
 using SignInteractiveForm.ServiceReference1;
 
 //A reference to the Forms service
 using SignInteractiveForm.ServiceReference2;
 
 namespace SignInteractiveForm
 {
        class Program
        {
            static void Main(string[] args)
            {
                try
                {
                    //Because BLOB objects are used in both service references
                    //it is necessary to fully-qualify the BLOB objects
 
                    //Retrieve the form -- invoke the Forms service
                    SignInteractiveForm.ServiceReference2.BLOB formData = GetForm();
 
                    //Create a BLOB object associated with the Signature service
                    SignInteractiveForm.ServiceReference1.BLOB sigData = new SignInteractiveForm.ServiceReference1.BLOB();
 
                    //Transfer the byte stream from one Forms BLOB object to the
                    //Signature BLOB object
                    sigData.MTOM = formData.MTOM;
 
                    //Sign the Form -- invoke the Signature service
                    SignForm(sigData);
                }
                catch (Exception ee)
                {
                    Console.WriteLine(ee.Message);
                }
            }
 
            //Creates an interactive PDF form based on a XFA form - invoke the Forms service
            private static SignInteractiveForm.ServiceReference2.BLOB GetForm()
            {
 
                try
                {
                    //Create a FormsServiceClient object
                    FormsServiceClient formsClient = new FormsServiceClient();
                    formsClient.Endpoint.Address = new System.ServiceModel.EndpointAddress("https://hiro-xp:8080/soap/services/FormsService?blob=mtom");
 
                    //Enable BASIC HTTP authentication
                    BasicHttpBinding b = (BasicHttpBinding)formsClient.Endpoint.Binding;
                    b.MessageEncoding = WSMessageEncoding.Mtom;
                    formsClient.ClientCredentials.UserName.UserName = "administrator";
                    formsClient.ClientCredentials.UserName.Password = "password";
                    b.Security.Transport.ClientCredentialType = HttpClientCredentialType.Basic;
                    b.Security.Mode = BasicHttpSecurityMode.TransportCredentialOnly;
                    b.MaxReceivedMessageSize = 2000000;
                    b.MaxBufferSize = 2000000;
                    b.ReaderQuotas.MaxArrayLength = 2000000;
 
                    //Create a BLOB to store form data
                    SignInteractiveForm.ServiceReference2.BLOB formData = new SignInteractiveForm.ServiceReference2.BLOB();
                    SignInteractiveForm.ServiceReference2.BLOB pdfForm = new SignInteractiveForm.ServiceReference2.BLOB();
 
                    //Specify a XML form data
                    string path = "C:\\Adobe\Loan.xml";
                    FileStream fs = new FileStream(path, FileMode.Open);
 
                    //Get the length of the file stream
                    int len = (int)fs.Length;
                    byte[] ByteArray = new byte[len];
 
                    fs.Read(ByteArray, 0, len);
                    formData.MTOM = ByteArray;
 
                    //Specify a XML form data
                    string path2 = "C:\\Adobe\LoanSigXFA.pdf";
                    FileStream fs2 = new FileStream(path2, FileMode.Open);
 
                    //Get the length of the file stream
                    int len2 = (int)fs2.Length;
                    byte[] ByteArray2 = new byte[len2];
 
                    fs2.Read(ByteArray2, 0, len2);
                    pdfForm.MTOM = ByteArray2;
 
                    PDFFormRenderSpec renderSpec = new PDFFormRenderSpec();
                    renderSpec.generateServerAppearance = true;
 
                    //Set out parameter values
                    long pageCount = 1;
                    String localValue = "en_US";
                    FormsResult result = new FormsResult();
 
                    //Render an interactive PDF form
                    formsClient.renderPDFForm2(
                        pdfForm,
                        formData,
                        renderSpec,
                        null,
                        null,
                        out pageCount,
                        out localValue,
                        out result);
 
                    //Write the data stream to the BLOB object
                    SignInteractiveForm.ServiceReference2.BLOB outForm = result.outputContent;
                    return outForm;
                }
                catch (Exception ee)
                {
                    Console.WriteLine(ee.Message);
                }
                return null;
            }
 
            //Sign the form -- invoke the Signature service
            private static void SignForm(SignInteractiveForm.ServiceReference1.BLOB inDoc)
            {
 
                try
                {
                    //Create a SignatureServiceClient object
                    SignatureServiceClient signatureClient = new SignatureServiceClient();
                    signatureClient.Endpoint.Address = new System.ServiceModel.EndpointAddress("https://hiro-xp:8080/soap/services/SignatureService?blob=mtom");
 
                    //Enable BASIC HTTP authentication
                    BasicHttpBinding b = (BasicHttpBinding)signatureClient.Endpoint.Binding;
                    b.MessageEncoding = WSMessageEncoding.Mtom;
                    signatureClient.ClientCredentials.UserName.UserName = "administrator";
                    signatureClient.ClientCredentials.UserName.Password = "password";
                    b.Security.Transport.ClientCredentialType = HttpClientCredentialType.Basic;
                    b.Security.Mode = BasicHttpSecurityMode.TransportCredentialOnly;
                    b.MaxReceivedMessageSize = 2000000;
                    b.MaxBufferSize = 2000000;
                    b.ReaderQuotas.MaxArrayLength = 2000000;
 
                    //Specify the name of the signature field
                    string fieldName = "form1[0].grantApplication[0].page1[0].SignatureField1[0]";
 
                    //Create a Credential object
                    Credential myCred = new Credential();
                    myCred.alias = "secure";
 
                    //Specify the reason to sign the document
                    string reason = "The document was reviewed";
 
                    //Specify the location of the signer
                    string location = "New York HQ";
 
                    //Specify contact information
                    string contactInfo = "Tony Blue";
 
                    //Create a PDFSignatureAppearanceOptions object
                    //and show date information
                    PDFSignatureAppearanceOptionSpec appear = new PDFSignatureAppearanceOptionSpec();
                    appear.showDate = true;
 
                    //Sign the PDF document
                    SignInteractiveForm.ServiceReference1.BLOB signedDoc = signatureClient.sign(
                        inDoc,
                        fieldName,
                        myCred,
                        HashAlgorithm.SHA1,
                        reason,
                        location,
                        contactInfo,
                        appear,
                        true,
                        null,
                        null,
                        null);
 
                    //Populate a byte array with BLOB data that represents the signed form
                    byte[] outByteArray = signedDoc.MTOM;
 
                    //Save the signed PDF document
                    string fileName = "C:\\Adobe\LoanXFASigned.pdf";
                    FileStream fs2 = new FileStream(fileName, FileMode.OpenOrCreate);
 
                    //Create a BinaryWriter object
                    BinaryWriter w = new BinaryWriter(fs2);
                    w.Write(outByteArray);
                    w.Close();
                    fs2.Close();
                }
 
                catch (Exception ee)
                {
                    Console.WriteLine(ee.Message);
                }
            }
        }
 }
 
 
```

### Services die beginnen met de letter I produceren ongeldige proxybestanden {#services-starting-with-the-letter-i-produce-invalid-proxy-files}

De naam van sommige AEM Vormen geproduceerde volmachtsklassen is onjuist wanneer het gebruiken van Microsoft .Net 3.5 en WCF. Dit probleem doet zich voor wanneer proxyklassen worden gemaakt voor de IBMFilenetContentRepositoryConnector, IDPSchedulerService of een andere service waarvan de naam begint met de letter I. Zo is de naam van de gegenereerde client in het geval van IBMFileNetContentRepositoryConnector `BMFileNetContentRepositoryConnectorClient`. De letter I ontbreekt in de gegenereerde proxyklasse.

