---
title: Documentuitvoerstromen maken
seo-title: Documentuitvoerstromen maken
description: 'null'
seo-description: 'null'
uuid: 80c28efa-35ce-4073-9ca6-2d93bcd67fdd
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: de527d50-991b-4ca3-a8ac-44d5cab988e9
translation-type: tm+mt
source-git-commit: 1343cc33a1e1ce26c0770a3b49317e82353497ab
workflow-type: tm+mt
source-wordcount: '18972'
ht-degree: 0%

---


# Documentuitvoerstromen maken  {#creating-document-output-streams}

**Informatie over de uitvoerservice**

Met de uitvoerservice kunt u documenten uitvoeren als PDF (inclusief PDF/A-documenten), PostScript, Printer Control Language (PCL) en de volgende labelindelingen:

* Zebra - ZPL
* Intermec, IPL
* Datamax - DPL
* TecToshiba - TPCL

Met de Output-service kunt u XML-formuliergegevens samenvoegen met een formulierontwerp en het document uitvoeren naar een netwerkprinter of een bestand.

Er zijn twee manieren waarop u een formulierontwerp (een XDP-bestand) kunt doorgeven aan de uitvoerservice. U kunt een `com.adobe.idp.Document` exemplaar met een formulierontwerp doorgeven aan de Output-service. U kunt ook een URI-waarde doorgeven die de locatie van het formulierontwerp opgeeft. Beide manieren worden besproken in *Programmering met vormen* AEM.

>[!NOTE]
>
>De uitvoerservice ondersteunt geen Acrobat PDF-documenten die toepassingsobjectspecifieke scripts bevatten. Acroform PDF-documenten die toepassingsobjectspecifieke scripts bevatten, worden niet gerenderd.

In de volgende secties ziet u hoe u een formulierontwerp aan de Output-service doorgeeft met behulp van een URI-waarde:

* [PDF-documenten maken](creating-document-output-streams.md#creating-pdf-documents)
* [PDF/A-documenten maken](creating-document-output-streams.md#creating-pdf-a-documents)

In de volgende secties ziet u hoe u een formulierontwerp binnen een `com.adobe.idp.Document` exemplaar doorgeeft:

* [Het overgaan van Documenten die in de (verlaten) Inhoudsdiensten worden gevestigd aan de Dienst van de Output](creating-document-output-streams.md#passing-documents-located-in-content-services-deprecated-to-the-output-service)
* [PDF-documenten maken met behulp van fragmenten](creating-document-output-streams.md#creating-pdf-documents-using-fragments)

Wanneer u bepaalt welke techniek u moet gebruiken, kunt u bijvoorbeeld overwegen of u het formulierontwerp van een andere service AEM Forms wilt ontvangen en het vervolgens in een `com.adobe.idp.Document` exemplaar wilt doorgeven. Zowel het *overgaan van Documenten aan de Dienst* van de Output als het *Creëren van PDF- Documenten gebruikend de secties van Fragments* tonen hoe te om een vormontwerp van een andere dienst van AEM Forms te krijgen. In de eerste sectie wordt het formulierontwerp opgehaald uit Content Services (afgekeurd). In de tweede sectie wordt het formulierontwerp opgehaald uit de Assembler-service.

Als u het formulierontwerp ophaalt vanaf een vaste locatie, zoals het bestandssysteem, kunt u beide methoden gebruiken. U kunt dus de URI-waarde opgeven voor een XDP-bestand of een `com.adobe.idp.Document` instantie gebruiken.

Als u een URI-waarde wilt doorgeven die de locatie van het formulierontwerp opgeeft wanneer u een PDF-document maakt, gebruikt u de `generatePDFOutput` methode. U kunt ook de `com.adobe.idp.Document` `generatePDFOutput2` methode gebruiken om een exemplaar door te geven aan de service Uitvoer wanneer u een PDF-document maakt.

Wanneer u een uitvoerstream naar een netwerkprinter verzendt, kunt u ook een van de twee technieken gebruiken. Als u een uitvoerstream naar een printer wilt verzenden door een `com.adobe.idp.Document` exemplaar met een formulierontwerp door te geven, gebruikt u de `sendToPrinter2`methode. Als u een uitvoerstream naar een printer wilt verzenden door een URI-waarde door te geven, gebruikt u de `sendToPrinter`methode. De *verzendende sectie van de Streams van de Druk aan Printers* gebruikt de `sendToPrinter` methode.

U kunt deze taken uitvoeren met de service Uitvoer:

* [PDF-documenten maken](creating-document-output-streams.md#creating-pdf-documents)
* [PDF/A-documenten maken](creating-document-output-streams.md#creating-pdf-a-documents)
* [Het overgaan van Documenten die in de (verlaten) Inhoudsdiensten worden gevestigd aan de Dienst van de Output](creating-document-output-streams.md#passing-documents-located-in-content-services-deprecated-to-the-output-service)
* [PDF-documenten maken met behulp van fragmenten](creating-document-output-streams.md#creating-pdf-documents-using-fragments)
* [Afdrukken naar bestanden](creating-document-output-streams.md#printing-to-files)
* [Afdrukstromen naar printers verzenden](creating-document-output-streams.md#sending-print-streams-to-printers)
* [Meerdere uitvoerbestanden maken](creating-document-output-streams.md#creating-multiple-output-files)
* [Zoekregels maken](creating-document-output-streams.md#creating-search-rules)
* [PDF-documenten afvlakken](creating-document-output-streams.md#flattening-pdf-documents)

>[!NOTE]
>
>Voor meer informatie over de dienst van de Output, zie de Verwijzing van de [Diensten voor AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## PDF-documenten maken {#creating-pdf-documents}

Met de service Uitvoer kunt u een PDF-document maken dat is gebaseerd op een formulierontwerp en XML-formuliergegevens die u opgeeft. Het PDF-document dat wordt gemaakt door de service Uitvoer is geen interactief PDF-document. een gebruiker kan geen formuliergegevens invoeren of wijzigen.

Als u een PDF-document wilt maken dat bestemd is voor langdurige opslag, is het raadzaam een PDF/A-document te maken. (Zie PDF/A-documenten [maken](creating-document-output-streams.md#creating-pdf-a-documents).)

Met de service Forms kunt u een interactief PDF-formulier maken waarmee een gebruiker gegevens kan invoeren. (Zie Interactieve PDF forms [renderen](/help/forms/developing/rendering-forms.md#rendering-interactive-pdf-forms).)

>[!NOTE]
>
>Voor meer informatie over de dienst van de Output, zie de Verwijzing van de [Diensten voor AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary-of-steps}

Voer de volgende stappen uit om een PDF-document te maken:

1. Inclusief projectbestanden.
1. Maak een Output Client-object.
1. Verwijzen naar een XML-gegevensbron.
1. Stel PDF-runtime-opties in.
1. Stel renderingopties in.
1. Genereer een PDF-document.
1. Haal de resultaten van de bewerking op.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u de proxybestanden opnemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-output-client.jar
* adobe-utilities.jar (vereist als AEM Forms worden geïmplementeerd op JBoss)
* jbossall-client.jar (vereist als AEM Forms worden geïmplementeerd op JBoss)

als AEM Forms worden geïmplementeerd op een ondersteunde J2EE-toepassingsserver die geen JBoss is, moet u de bestanden adobe-utilities.jar en jbossall-client.jar vervangen door JAR-bestanden die specifiek zijn voor de J2EE-toepassingsserver waarop AEM Forms worden geïmplementeerd.

**Een uitvoerclient-object maken**

Voordat u programmatisch een uitvoerservicebewerking kunt uitvoeren, moet u een uitvoerservice-clientobject maken. Als u de Java API gebruikt, maakt u een `OutputClient` object. Als u de Output-webservice-API gebruikt, maakt u een `OutputServiceService` object.

**Verwijzen naar een XML-gegevensbron**

Als u gegevens wilt samenvoegen met het formulierontwerp, moet u verwijzen naar een XML-gegevensbron die gegevens bevat. Er moet een XML-element aanwezig zijn voor elk formulierveld dat u wilt vullen met gegevens. De naam van het XML-element moet overeenkomen met de veldnaam. Een XML-element wordt genegeerd als het niet overeenkomt met een formulierveld of als de naam van het XML-element niet overeenkomt met de veldnaam. Het is niet nodig de volgorde aan te passen waarin de XML-elementen worden weergegeven als alle XML-elementen zijn opgegeven.

Bekijk het volgende voorbeeld van een aanvraagformulier voor een lening.

![cp_cp_loanformdata](assets/cp_cp_loanformdata.png)

Als u gegevens wilt samenvoegen in dit formulierontwerp, moet u een XML-gegevensbron maken die overeenkomt met het formulier. De volgende XML vertegenwoordigt een XDP XML-gegevensbron die overeenkomt met het voorbeeld van een hypotheektoepassing.

```xml
 <?xml version="1.0" encoding="UTF-8" ?>
 - <xfa:datasets xmlns:xfa="https://www.xfa.org/schema/xfa-data/1.0/">
 - <xfa:data>
 - <data>
     - <Layer>
         <closeDate>1/26/2007</closeDate>
         <lastName>Johnson</lastName>
         <firstName>Jerry</firstName>
         <mailingAddress>JJohnson@NoMailServer.com</mailingAddress>
         <city>New York</city>
         <zipCode>00501</zipCode>
         <state>NY</state>
         <dateBirth>26/08/1973</dateBirth>
         <middleInitials>D</middleInitials>
         <socialSecurityNumber>(555) 555-5555</socialSecurityNumber>
         <phoneNumber>5555550000</phoneNumber>
     </Layer>
     - <Mortgage>
         <mortgageAmount>295000.00</mortgageAmount>
         <monthlyMortgagePayment>1724.54</monthlyMortgagePayment>
         <purchasePrice>300000</purchasePrice>
         <downPayment>5000</downPayment>
         <term>25</term>
         <interestRate>5.00</interestRate>
     </Mortgage>
 </data>
 </xfa:data>
 </xfa:datasets>
```

**Opties voor PDF-runtime instellen**

Stel de optie voor bestands-URI in wanneer u een PDF-document maakt. Met deze optie geeft u de naam en locatie op van het PDF-bestand dat de service Uitvoer genereert.

>[!NOTE]
>
>In plaats van de runtime-optie voor bestands-URI in te stellen, kunt u het PDF-document programmatisch ophalen van het complexe gegevenstype dat door de service Output wordt geretourneerd. Als u echter de optie voor het uitvoeren van de bestands-URI instelt, hoeft u geen toepassingslogica te maken die het PDF-document programmatisch ophaalt.

**Renderopties tijdens runtime instellen**

U kunt bij het maken van een PDF-document renderingopties instellen. Hoewel deze opties niet vereist zijn (in tegenstelling tot de vereiste PDF-runtime-opties), kunt u taken uitvoeren zoals het verbeteren van de prestaties van de uitvoerservice. U kunt bijvoorbeeld het formulierontwerp dat de Output-service gebruikt in cache plaatsen om de prestaties te verbeteren.

Als u een gecodeerd Acrobat-formulier als invoer gebruikt, kunt u de instelling voor getagd formulier niet uitschakelen met de Java- of API voor de uitvoerservice. Als u probeert deze optie programmatisch in te stellen op `false`, wordt het PDF-document met het resultaat nog steeds gecodeerd.

>[!NOTE]
>
>Als u geen renderingopties opgeeft, worden standaardwaarden gebruikt. Zie de `RenderOptionsSpec` klasseverwijzing voor informatie over het renderen van runtime-opties. (Zie [AEM Forms API-naslaggids](https://www.adobe.com/go/learn_aemforms_javadocs_63_en)).

**Een PDF-document genereren**

Nadat u naar een geldige XML-gegevensbron met formuliergegevens hebt verwezen en u runtime-opties hebt ingesteld, kunt u de uitvoerservice inschakelen. Hierdoor wordt een PDF-document gegenereerd.

Wanneer u een PDF-document genereert, geeft u de URI-waarden op die de uitvoerservice nodig heeft om een PDF-document te maken. Een formulierontwerp kan worden opgeslagen op locaties als het serverbestandssysteem of als onderdeel van een AEM Forms-toepassing. Naar een formulierontwerp (of andere bronnen zoals een afbeeldingsbestand) dat als onderdeel van een Forms-toepassing bestaat, kan worden verwezen met behulp van de URI-waarde van de hoofdmap van de inhoud `repository:///`. Neem bijvoorbeeld het volgende formulierontwerp met de naam *Loan.xdp* in een Forms-toepassing met de naam *Applications/FormsApplication*:

![cp_cp_formrepository](assets/cp_cp_formrepository.png)

Als u toegang wilt tot het bestand Loan.xdp dat in de vorige afbeelding wordt weergegeven, geeft u `repository:///Applications/FormsApplication/1.0/FormsFolder/` de derde parameter op die wordt doorgegeven aan de `OutputClient` methode van het `generatePDFOutput` object. Geef de formuliernaam (*Loan.xdp*) op als de tweede parameter die wordt doorgegeven aan de `OutputClient` methode van het `generatePDFOutput` object.

Als het XDP-bestand afbeeldingen (of andere bronnen zoals fragmenten) bevat, plaatst u de bronnen in dezelfde toepassingsmap als het XDP-bestand. AEM Forms gebruiken de basis-URI van de inhoud als het basispad om verwijzingen naar afbeeldingen op te lossen. Als het bestand Loan.xdp bijvoorbeeld een afbeelding bevat, moet u de afbeelding eerst in `Applications/FormsApplication/1.0/FormsFolder/`het bestand plaatsen.

>[!NOTE]
>
>U kunt naar de URI van een Forms-toepassing verwijzen wanneer u de methoden `OutputClient` of methoden van het `generatePDFOutput` `generatePrintedOutput` object aanroept.

>[!NOTE]
>
>Zie [Snel starten (EJB-modus) voor een snel begin waarin een PDF-document wordt gemaakt door te verwijzen naar een XDP in een Forms-toepassing: Een PDF-document maken op basis van een XDP-bestand van een toepassing met behulp van de Java API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-a-pdf-document-based-on-an-application-xdp-file-using-the-java-api).

**De resultaten van de bewerking ophalen**

Nadat de dienst van de Output een verrichting uitvoert, keert het diverse gegevenspunten zoals de gegevens van statusXML terug die specificeren of de verrichting succesvol was.

**Zie ook**

[Een PDF-document maken met de Java API](creating-document-output-streams.md#create-a-pdf-document-using-the-java-api)

[Een PDF-document maken met de webservice-API](creating-document-output-streams.md#create-a-pdf-document-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Uitvoerservice-API - Snel starten](/help/forms/developing/output-service-java-api-quick.md#output-service-java-api-quick-start-soap)

### Een PDF-document maken met de Java API {#create-a-pdf-document-using-the-java-api}

Een PDF-document maken met de Output API (Java):

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-output-client.jar, op in het klassenpad van uw Java-project.

1. Maak een Output Client-object.

   * Maak een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Maak een `OutputClient` object door de constructor ervan te gebruiken en het `ServiceClientFactory` object door te geven.

1. Verwijzen naar een XML-gegevensbron.

   * Maak een `java.io.FileInputStream` object dat staat voor de XML-gegevensbron die wordt gebruikt om het PDF-document te vullen met de constructor ervan en geef een tekenreekswaarde door die de locatie van het XML-bestand aangeeft.
   * Maak een `com.adobe.idp.Document` object met de constructor ervan. Geef het `java.io.FileInputStream` object door.

1. Stel PDF-runtime-opties in.

   * Maak een `PDFOutputOptionsSpec` object met de constructor ervan.
   * Stel de optie File URI in door de `PDFOutputOptionsSpec` methode van het `setFileURI` object aan te roepen. Geef een tekenreekswaarde door die de locatie aangeeft van het PDF-bestand dat door de uitvoerservice wordt gegenereerd. De optie File URI is relatief ten opzichte van de J2EE-toepassingsserver die AEM Forms host, niet ten opzichte van de clientcomputer.

1. Stel renderingopties in.

   * Maak een `RenderOptionsSpec` object met de constructor ervan.
   * Plaats het formulierontwerp in de cache om de prestaties van de uitvoerservice te verbeteren door het `RenderOptionsSpec` object aan te roepen `setCacheEnabled` en door te geven `true`.

   >[!NOTE]
   >
   >U kunt de versie van het PDF-document niet instellen met de `RenderOptionsSpec` `setPdfVersion` methode van het object als het invoerdocument een Acrobat-formulier (een formulier dat is gemaakt in Acrobat) of een XFA-document is dat is ondertekend of gecertificeerd. Het PDF-uitvoerdocument behoudt de oorspronkelijke PDF-versie. U kunt ook de optie Adobe PDF met codes niet instellen door de methode van het `RenderOptionsSpec` `setTaggedPDF` object aan te roepen als het invoerdocument een Acrobat-formulier of een ondertekend of gecertificeerd XFA-document is.

   >[!NOTE]
   >
   >U kunt de optie Gelineariseerde PDF niet instellen met de `RenderOptionsSpec` methode van het `setLinearizedPDF` object als het invoer-PDF-document is gecertificeerd of digitaal is ondertekend. (Zie PDF-documenten [digitaal ondertekenen](/help/forms/developing/digitally-signing-certifying-documents.md#digitally-signing-pdf-documents)*.)*

1. Genereer een PDF-document.

   Maak een PDF-document door de methode van het `OutputClient` `generatePDFOutput` object aan te roepen en de volgende waarden door te geven:

   * Een `TransformationFormat` opsommingswaarde. Geef op om een PDF-document te genereren. `TransformationFormat.PDF`
   * Een tekenreekswaarde waarmee de naam van het formulierontwerp wordt opgegeven.
   * Een tekenreekswaarde die de hoofdmap van de inhoud opgeeft waar het formulierontwerp zich bevindt.
   * Een `PDFOutputOptionsSpec` object dat PDF-runtime-opties bevat.
   * Een `RenderOptionsSpec` object dat renderingopties bevat.
   * Het `com.adobe.idp.Document` object dat de XML-gegevensbron bevat die gegevens bevat die met het formulierontwerp moeten worden samengevoegd.

   De `generatePDFOutput` methode retourneert een `OutputResult` object dat de resultaten van de bewerking bevat.

   >[!NOTE]
   >
   >Wanneer u een PDF-document genereert door de `generatePDFOutput` methode aan te roepen, moet u er rekening mee houden dat u geen gegevens kunt samenvoegen met een ondertekend of gecertificeerd XFA PDF-formulier. (Zie Documenten [](/help/forms/developing/digitally-signing-certifying-documents.md#digitally-signing-and-certifying-documents)*digitaal ondertekenen en certificeren.)*

   >[!NOTE]
   >
   >De `OutputResult` methode van het `getRecordLevelMetaDataList` object retourneert `null`*.*

   >[!NOTE]
   >
   >U kunt ook een PDF-document maken door de `OutputClient` methode van het `generatePDFOutput2` object aan te roepen. (Zie Documenten [die in de (afgekeurde) Inhoudsdiensten worden gevestigd tot de Dienst](creating-document-output-streams.md#passing-documents-located-in-content-services-deprecated-to-the-output-service)*van de Output overgaan.)*

1. Haal de resultaten van de bewerking op.

   * Haal een `com.adobe.idp.Document` object op dat de status van de `generatePDFOutput` bewerking vertegenwoordigt door de `OutputResult` methode van het `getStatusDoc` object aan te roepen. Deze methode retourneert XML-gegevens met de status die aangeven of de bewerking is geslaagd.
   * Maak een `java.io.File` object dat de resultaten van de bewerking bevat. Controleer of de bestandsnaamextensie .xml is.
   * Roep de `com.adobe.idp.Document` methode van het `copyToFile` object aan om de inhoud van het `com.adobe.idp.Document` object naar het bestand te kopiëren (zorg dat u het `com.adobe.idp.Document` object gebruikt dat door de `getStatusDoc` methode is geretourneerd).

   Hoewel de service Uitvoer het PDF-document schrijft naar de locatie die is opgegeven door het argument dat wordt doorgegeven aan de `PDFOutputOptionsSpec` methode van het object, kunt u het PDF/A-document programmatisch ophalen door de `setFileURI` methode van het `OutputResult` `getGeneratedDoc` object aan te roepen.

**Zie ook**

[Overzicht van de stappen](creating-document-output-streams.md#summary-of-steps)

[Snel starten (EJB-modus): Een PDF-document maken met de Java API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-a-pdf-document-using-the-java-api)

[Snel starten (SOAP-modus): Een PDF-document maken met de Java API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-a-pdf-document-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Een PDF-document maken met de webservice-API {#create-a-pdf-document-using-the-web-service-api}

Een PDF-document maken met de Output API (webservice):

1. Inclusief projectbestanden.

   Creeer een project van Microsoft .NET dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/OutputService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een Output Client-object.

   * Maak een `OutputServiceClient` object met de standaardconstructor.
   * Maak een `OutputServiceClient.Endpoint.Address` object met de `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de service AEM Forms (bijvoorbeeld `http://localhost:8080/soap/services/OutputService?blob=mtom`.) U hoeft het `lc_version` kenmerk niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt. Geef echter op `?blob=mtom` om MTOM te gebruiken.
   * Maak een `System.ServiceModel.BasicHttpBinding` object door de waarde van het `OutputServiceClient.Endpoint.Binding` veld op te halen. Kiezen naar de geretourneerde waarde `BasicHttpBinding`.
   * Stel het `System.ServiceModel.BasicHttpBinding` veld van het `MessageEncoding` object in op `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam voor AEM-formulieren toe aan het veld `OutputServiceClient.ClientCredentials.UserName.UserName`.
      * Wijs de bijbehorende wachtwoordwaarde aan het veld toe `OutputServiceClient.ClientCredentials.UserName.Password`.
      * Wijs de constante waarde toe `HttpClientCredentialType.Basic` aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Wijs de constante waarde toe `BasicHttpSecurityMode.TransportCredentialOnly` aan het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Verwijzen naar een XML-gegevensbron.

   * Maak een `BLOB` object met de constructor ervan. Het `BLOB` object wordt gebruikt voor het opslaan van XML-gegevens die worden samengevoegd met het PDF-document.
   * Maak een `System.IO.FileStream` object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie vertegenwoordigt van het XML-bestand dat formuliergegevens bevat.
   * Maak een bytearray waarin de inhoud van het `System.IO.FileStream` object wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` eigenschap van het `Length` object op te halen.
   * Vul de bytearray met streamgegevens door de methode van het `System.IO.FileStream` `Read` object aan te roepen en de bytearray, de startpositie en de lengte van de stream door te geven om te lezen.
   * Vul het `BLOB` object door het `MTOM` veld ervan toe te wijzen met de inhoud van de bytearray.

1. Opties voor PDF-runtime instellen

   * Maak een `PDFOutputOptionsSpec` object met de constructor ervan.
   * Stel de optie File URI in door een tekenreekswaarde toe te wijzen die de locatie opgeeft van het PDF-bestand dat de uitvoerservice genereert voor het `PDFOutputOptionsSpec` gegevenslid van het `fileURI` object. De optie File URI is relatief ten opzichte van de J2EE-toepassingsserver die AEM Forms host, niet ten opzichte van de clientcomputer.

1. Stel renderingopties in.

   * Maak een `RenderOptionsSpec` object met de constructor ervan.
   * Plaats het formulierontwerp in de cache om de prestaties van de Output-service te verbeteren door de waarde toe te wijzen `true` aan het `RenderOptionsSpec` gegevenslid van het `cacheEnabled` object.

   >[!NOTE]
   >
   >U kunt de versie van het PDF-document niet instellen met de `RenderOptionsSpec` `setPdfVersion` methode van het object als het invoerdocument een Acrobat-formulier (een formulier dat is gemaakt in Acrobat) of een XFA-document is dat is ondertekend of gecertificeerd. Het PDF-uitvoerdocument behoudt de oorspronkelijke PDF-versie. U kunt ook de optie Adobe PDF met codes niet instellen door de methode `RenderOptionsSpec` * van het `setTaggedPDF`object aan te roepen als het invoerdocument een Acrobat-formulier of een ondertekend of gecertificeerd XFA-document is.*

   >[!NOTE]
   >
   >U kunt de optie Gelineariseerde PDF niet instellen met het `RenderOptionsSpec` lid van het `linearizedPDF` object als het invoer-PDF-document is gecertificeerd of digitaal is ondertekend. (Zie PDF-documenten [digitaal ondertekenen](/help/forms/developing/digitally-signing-certifying-documents.md#digitally-signing-pdf-documents)*.)*

1. Genereer een PDF-document.

   Maak een PDF-document door de `OutputServiceService` methode van het `generatePDFOutput`object aan te roepen en de volgende waarden door te geven:

   * Een `TransformationFormat` opsommingswaarde. Geef op om een PDF-document te genereren. `TransformationFormat.PDF`
   * Een tekenreekswaarde waarmee de naam van het formulierontwerp wordt opgegeven.
   * Een tekenreekswaarde die de hoofdmap van de inhoud opgeeft waar het formulierontwerp zich bevindt.
   * Een `PDFOutputOptionsSpec` object dat PDF-runtime-opties bevat.
   * Een `RenderOptionsSpec` object dat renderingopties bevat.
   * Het `BLOB` object dat de XML-gegevensbron bevat die gegevens bevat die met het formulierontwerp moeten worden samengevoegd.
   * Een `BLOB` object dat door de `generatePDFOutput` methode is gevuld. De `generatePDFOutput` methode vult dit object met gegenereerde metagegevens die het document beschrijven. (Deze parameterwaarde is alleen vereist voor aanroepen van een webservice.)
   * Een `BLOB` object dat door de `generatePDFOutput` methode is gevuld. De `generatePDFOutput` methode vult dit object met resultaatgegevens. (Deze parameterwaarde is alleen vereist voor aanroepen van een webservice.)
   * Een `OutputResult` object dat de resultaten van de bewerking bevat. (Deze parameterwaarde is alleen vereist voor aanroepen van een webservice.)

   >[!NOTE]
   >
   >Wanneer u een PDF-document genereert door de `generatePDFOutput` methode aan te roepen, moet u er rekening mee houden dat u geen gegevens kunt samenvoegen met een ondertekend of gecertificeerd XFA PDF-formulier. (Zie Documenten [](/help/forms/developing/digitally-signing-certifying-documents.md#digitally-signing-and-certifying-documents)*digitaal ondertekenen en certificeren.)*

   >[!NOTE]
   >
   >U kunt ook een PDF-document maken door de `OutputClient` methode van het `generatePDFOutput2` object aan te roepen. (Zie Documenten [die in de (afgekeurde) Inhoudsdiensten worden gevestigd tot de Dienst](creating-document-output-streams.md#passing-documents-located-in-content-services-deprecated-to-the-output-service)*van de Output overgaan.)*

1. Haal de resultaten van de bewerking op.

   * Maak een `System.IO.FileStream` object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die een locatie van een XML-bestand vertegenwoordigt die resultaatgegevens bevat. Controleer of de bestandsnaamextensie .xml is.
   * Maak een bytearray waarin de gegevensinhoud wordt opgeslagen van het `BLOB` object dat met resultaatgegevens is gevuld via de `OutputServiceService` methode van het `generatePDFOutput` object (de achtste parameter). Vul de bytearray met de waarde van het `BLOB` object `MTOM` `field`.
   * Maak een `System.IO.BinaryWriter` object door de constructor ervan aan te roepen en het `System.IO.FileStream` object door te geven.
   * Schrijf de inhoud van de bytearray naar het XML-bestand door de methode van het `System.IO.BinaryWriter` `Write` object aan te roepen en de bytearray door te geven.

   Zie ook

   [Overzicht van de stappen](creating-document-output-streams.md#summary-of-steps)

   [AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

   [AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

   >[!NOTE]
   >
   >De methode van het `OutputServiceService` object is `generateOutput` afgekeurd.

## PDF/A-documenten maken {#creating-pdf-a-documents}

Met de service Uitvoer kunt u een PDF/A-document maken. Omdat PDF/A een archiefindeling is voor langdurige bewaring van de inhoud van het document, worden alle fonts ingesloten en wordt het bestand niet gecomprimeerd. Een PDF/A-document is daarom doorgaans groter dan een standaard PDF-document. Bovendien bevat een PDF/A-document geen audio- en video-inhoud. Net als bij andere uitvoerservicetaken kunt u zowel een formulierontwerp als gegevens opgeven die met een formulierontwerp moeten worden samengevoegd om een PDF/A-document te maken.

De PDF/A-1-specificatie bestaat uit twee conformiteitsniveaus, namelijk a en b. Het grootste verschil tussen beide is de logische structuur (toegankelijkheid) die niet vereist is voor niveau b. PDF/A-1 schrijft voor dat alle lettertypen in het gegenereerde PDF/A-document worden ingesloten, ongeacht het compatibiliteitsniveau.

Hoewel PDF/A de standaard is voor het archiveren van PDF-documenten, is het niet verplicht dat PDF/A wordt gebruikt voor archivering als een standaard PDF-document voldoet aan de behoeften van uw bedrijf. Het doel van de PDF/A-standaard is het maken van een PDF-bestand dat lange tijd kan worden opgeslagen en dat voldoet aan de vereisten voor documentbehoud. Een URL kan bijvoorbeeld niet worden ingesloten in een PDF/A omdat de URL na verloop van tijd ongeldig kan worden.

Uw organisatie moet haar eigen behoeften, de tijdsduur beoordelen u van plan bent om het document te houden, dossiergrootte overwegingen, en uw eigen archiveringsstrategie te bepalen. Met de DocConverter-service kunt u programmatisch bepalen of een PDF-document compatibel is met PDF/A. (Zie PDF/A-compatibiliteit [via programmacode bepalen](/help/forms/developing/pdf-a-documents.md#programmatically-determining-pdf-a-compliancy).)

Een PDF/A-document moet het font gebruiken dat is opgegeven in het formulierontwerp en fonts kunnen niet worden vervangen. Als een lettertype dat zich in een PDF-document bevindt niet beschikbaar is in het besturingssysteem van de host (OS), treedt daarom een uitzondering op.

Wanneer een PDF/A-document wordt geopend in Acrobat, wordt een bericht weergegeven waarin wordt bevestigd dat het document een PDF/A-document is, zoals in de volgende afbeelding wordt getoond.

![cp_cp_pdfamessage](assets/cp_cp_pdfamessage.png)

>[!NOTE]
>
>De AIR-website heeft een sectie met veelgestelde vragen over PDF/A die u kunt openen op [https://www.aiim.org/documents/standards/19005-1_FAQ.pdf](https://www.aiim.org/documents/standards/19005-1_FAQ.pdf).

>[!NOTE]
>
>Voor meer informatie over de dienst van de Output, zie de Verwijzing van de [Diensten voor AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary_of_steps-1}

Voer de volgende stappen uit om een PDF/A-document te maken:

1. Inclusief projectbestanden.
1. Maak een Output Client-object.
1. Verwijzen naar een XML-gegevensbron.
1. Stel PDF/A-runtime-opties in.
1. Stel renderingopties in.
1. Genereer een PDF/A-document.
1. Haal de resultaten van de bewerking op.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een aangepaste toepassing maakt met behulp van Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u de proxybestanden opnemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-output-client.jar
* adobe-utilities.jar (vereist als AEM Forms worden geïmplementeerd op JBoss)
* jbossall-client.jar (vereist als AEM Forms worden geïmplementeerd op JBoss)

als AEM Forms worden geïmplementeerd op een ondersteunde J2EE-toepassingsserver die geen JBoss is, moet u de bestanden adobe-utilities.jar en jbossall-client.jar vervangen door JAR-bestanden die specifiek zijn voor de J2EE-toepassingsserver waarop AEM Forms worden geïmplementeerd.

**Een uitvoerclient-object maken**

Voordat u programmatisch een uitvoerservicebewerking kunt uitvoeren, moet u een uitvoerservice-clientobject maken. Als u de Java API gebruikt, maakt u een `OutputClient` object. Als u de Output-webservice-API gebruikt, maakt u een `OutputServiceService` object.

**Verwijzen naar een XML-gegevensbron**

Als u gegevens wilt samenvoegen met het formulierontwerp, moet u verwijzen naar een XML-gegevensbron die gegevens bevat. Een XML-element moet bestaan voor elk formulierveld dat u wilt vullen met gegevens. De naam van het XML-element moet overeenkomen met de veldnaam. Een XML-element wordt genegeerd als het niet overeenkomt met een formulierveld of als de naam van het XML-element niet overeenkomt met de veldnaam. Het is niet nodig de volgorde aan te passen waarin de XML-elementen worden weergegeven als alle XML-elementen zijn opgegeven.

**Opties voor PDF/A-runtime instellen**

U kunt de optie File URI instellen wanneer u een PDF/A-document maakt. De URI is relatief ten opzichte van de J2EE-toepassingsserver die AEM Forms host. Dit betekent dat als u C:\Adobe instelt, het bestand naar de map op de server wordt geschreven, niet naar de clientcomputer. De URI geeft de naam en locatie op van het PDF/A-bestand dat de uitvoerservice genereert.

**Renderopties tijdens runtime instellen**

Bij het maken van PDF/A-documenten kunt u runtime-renderopties instellen. Twee PDF/A-gerelateerde opties die u kunt instellen, zijn de `PDFAConformance` en de `PDFARevisionNumber` waarden. De `PDFAConformance` waarde verwijst naar de manier waarop een PDF-document voldoet aan de vereisten die opgeven hoe elektronische documenten op lange termijn moeten worden bewaard. Geldige waarden voor deze optie zijn `A` en `B`. Zie de PDF/A-1 ISO-specificatie met de naam *ISO 19005-1 Document management* voor informatie over niveau a- en b-conformiteit.

De `PDFARevisionNumber` waarde verwijst naar het revisienummer van een PDF/A-document. Zie de PDF/A-1 ISO-specificatie met de naam *ISO 19005-1 Document management* voor informatie over het revisienummer van een PDF/A-document.

>[!NOTE]
>
>U kunt de optie Adobe PDF-codes niet instellen op `false` wanneer u een PDF/A 1A-document maakt. PDF/A 1A wordt altijd een gecodeerd PDF-document. Ook kunt u de optie Adobe PDF-codes niet instellen op `true` wanneer u een PDF/A 1B-document maakt. PDF/A 1B wordt altijd een niet-gecodeerd PDF-document.

**Een PDF/A-document genereren**

Nadat u naar een geldige XML-gegevensbron met formuliergegevens hebt verwezen en u runtime-opties hebt ingesteld, kunt u de uitvoerservice aanroepen, zodat er een PDF/A-document wordt gegenereerd.

**De resultaten van de bewerking ophalen**

Nadat de dienst van de Output een verrichting uitvoert, keert het diverse gegevenspunten zoals de gegevens van XML terug die specificeren of de verrichting succesvol was.

**Zie ook**

[Een PDF/A-document maken met de Java API](creating-document-output-streams.md#create-a-pdf-a-document-using-the-java-api)

[Een PDF/A-document maken met de webservice-API](creating-document-output-streams.md#create-a-pdf-a-document-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Uitvoerservice-API - Snel starten](/help/forms/developing/output-service-java-api-quick.md#output-service-java-api-quick-start-soap)

### Een PDF/A-document maken met de Java API {#create-a-pdf-a-document-using-the-java-api}

Een PDF/A-document maken met de Output API (Java):

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-output-client.jar, op in het klassenpad van uw Java-project.

1. Maak een Output Client-object.

   * Maak een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Maak een `OutputClient` object door de constructor ervan te gebruiken en het `ServiceClientFactory` object door te geven.

1. Verwijzen naar een XML-gegevensbron.

   * Maak een `java.io.FileInputStream` object dat staat voor de XML-gegevensbron die wordt gebruikt om het PDF/A-document te vullen met de constructor ervan en geef een tekenreekswaarde door die de locatie van het XML-bestand aangeeft.
   * Maak een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en het `java.io.FileInputStream` object door te geven.

1. Stel PDF/A-runtime-opties in.

   * Maak een `PDFOutputOptionsSpec` object met de constructor ervan.
   * Stel de optie File URI in door de `PDFOutputOptionsSpec` methode van het `setFileURI` object aan te roepen. Geef een tekenreekswaarde door die de locatie aangeeft van het PDF-bestand dat door de uitvoerservice wordt gegenereerd. De optie File URI is relatief ten opzichte van de J2EE-toepassingsserver die AEM Forms host, niet ten opzichte van de clientcomputer.

1. Stel renderingopties in.

   * Maak een `RenderOptionsSpec` object met de constructor ervan.
   * Stel de `PDFAConformance` waarde in door de `RenderOptionsSpec` methode van het `setPDFAConformance` object aan te roepen en een `PDFAConformance` opsommingswaarde door te geven die het compatibiliteitsniveau opgeeft. Als u bijvoorbeeld compatibiliteitsniveau A wilt opgeven, geeft u door `PDFAConformance.A`.
   * Stel de `PDFARevisionNumber` waarde in door de methode van het `RenderOptionsSpec` object aan te roepen `setPDFARevisionNumber` en door te geven `PDFARevisionNumber.Revision_1`.

   >[!NOTE]
   >
   >De PDF-versie van een PDF/A-document is 1.4, ongeacht de waarde die u opgeeft voor de `RenderOptionsSpec` methode van het `setPdfVersion`*object.*

1. Genereer een PDF/A-document.

   Maak een PDF/A-document door de methode van het `OutputClient` `generatePDFOutput` object aan te roepen en de volgende waarden door te geven:

   * Een `TransformationFormat` opsommingswaarde. Geef op om een PDF/A-document te genereren. `TransformationFormat.PDFA`
   * Een tekenreekswaarde waarmee de naam van het formulierontwerp wordt opgegeven.
   * Een tekenreekswaarde die de hoofdmap van de inhoud opgeeft waar het formulierontwerp zich bevindt.
   * Een `PDFOutputOptionsSpec` object dat PDF-runtime-opties bevat.
   * Een `RenderOptionsSpec` object dat renderingopties bevat.
   * Het `com.adobe.idp.Document` object dat de XML-gegevensbron bevat die gegevens bevat die met het formulierontwerp moeten worden samengevoegd.

   De `generatePDFOutput` methode retourneert een `OutputResult` object dat de resultaten van de bewerking bevat.

   >[!NOTE]
   >
   >De `OutputResult` methode van het `getRecordLevelMetaDataList` object retourneert `null`.

   >[!NOTE]
   >
   >U kunt ook een PDF/A-document maken door de methode `OutputClient` 2 van het `generatePDFOutput`object aan te roepen. (Zie Documenten [die in de (afgekeurde) Inhoudsdiensten worden gevestigd tot de Dienst](creating-document-output-streams.md#passing-documents-located-in-content-services-deprecated-to-the-output-service)van de Output overgaan.)

1. Haal de resultaten van de bewerking op.

   * Maak een `com.adobe.idp.Document` object dat de status van de `generatePDFOutput` methode vertegenwoordigt door de `OutputResult` methode van het `getStatusDoc` object aan te roepen.
   * Maak een `java.io.File` object dat de resultaten van de bewerking zal bevatten. Controleer of de bestandsnaamextensie .xml is.
   * Roep de `com.adobe.idp.Document` methode van het `copyToFile` object aan om de inhoud van het `com.adobe.idp.Document` object naar het bestand te kopiëren (zorg dat u het `com.adobe.idp.Document` object gebruikt dat door de `getStatusDoc` methode is geretourneerd).

   >[!NOTE]
   >
   >Hoewel de service Uitvoer het PDF/A-document schrijft naar de locatie die is opgegeven door het argument dat wordt doorgegeven aan de `PDFOutputOptionsSpec` methode van het object, kunt u het PDF/A-document programmatisch ophalen door de `setFileURI` methode van het `OutputResult` `getGeneratedDoc` object aan te roepen.

**Zie ook**

[Overzicht van de stappen](creating-document-output-streams.md#summary-of-steps)

[Snel starten (SOAP-modus): Een PDF/A-document maken met de Java API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-a-pdf-a-document-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)instellen.

### Een PDF/A-document maken met de webservice-API {#create-a-pdf-a-document-using-the-web-service-api}

Een PDF/A-document maken met de Output API (webservice):

1. Inclusief projectbestanden.

   Creeer een project van Microsoft .NET dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/OutputService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een Output Client-object.

   * Maak een `OutputServiceClient` object met de standaardconstructor.
   * Maak een `OutputServiceClient.Endpoint.Address` object met de `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de service AEM Forms (bijvoorbeeld `http://localhost:8080/soap/services/OutputService?blob=mtom`.) U hoeft het `lc_version` kenmerk niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt. Geef echter op `?blob=mtom` om MTOM te gebruiken.
   * Maak een `System.ServiceModel.BasicHttpBinding` object door de waarde van het `OutputServiceClient.Endpoint.Binding` veld op te halen. Kiezen naar de geretourneerde waarde `BasicHttpBinding`.
   * Stel het `System.ServiceModel.BasicHttpBinding` veld van het `MessageEncoding` object in op `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam voor AEM-formulieren toe aan het veld `OutputServiceClient.ClientCredentials.UserName.UserName`.
      * Wijs de bijbehorende wachtwoordwaarde aan het veld toe `OutputServiceClient.ClientCredentials.UserName.Password`.
      * Wijs de constante waarde toe `HttpClientCredentialType.Basic` aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Wijs de constante waarde toe `BasicHttpSecurityMode.TransportCredentialOnly` aan het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Verwijzen naar een XML-gegevensbron.

   * Maak een `BLOB` object met de constructor ervan. Het `BLOB` object wordt gebruikt voor het opslaan van gegevens die worden samengevoegd met het PDF/A-document.
   * Maak een `System.IO.FileStream` object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie vertegenwoordigt van het PDF-document dat moet worden versleuteld en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van het `System.IO.FileStream` object wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` eigenschap van het `Length` object op te halen.
   * Vul de bytearray met streamgegevens door de methode van het `System.IO.FileStream` `Read` object aan te roepen en de bytearray, de startpositie en de lengte van de stream door te geven om te lezen.
   * Vul het `BLOB` object door het `MTOM` veld ervan met de inhoud van de bytearray toe te wijzen.

1. Stel PDF/A-runtime-opties in.

   * Maak een `PDFOutputOptionsSpec` object met de constructor ervan.
   * Stel de optie File URI in door een tekenreekswaarde toe te wijzen die de locatie opgeeft van het PDF-bestand dat de uitvoerservice genereert voor het `PDFOutputOptionsSpec` gegevenslid van het `fileURI` object. De optie File URI is relatief ten opzichte van de J2EE-toepassingsserver die AEM Forms host, niet ten opzichte van de clientcomputer

1. Stel renderingopties in.

   * Maak een `RenderOptionsSpec` object met de constructor ervan.
   * Stel de `PDFAConformance` waarde in door een `PDFAConformance` opsommingswaarde toe te wijzen aan het `RenderOptionsSpec` gegevenslid van het `PDFAConformance` object. Als u bijvoorbeeld compatibiliteitsniveau A wilt opgeven, wijst u dit gegevenslid toe `PDFAConformance.A` .
   * Stel de `PDFARevisionNumber` waarde in door een `PDFARevisionNumber` opsommingswaarde toe te wijzen aan het `RenderOptionsSpec` gegevenslid van het `PDFARevisionNumber` object. Wijs dit gegevenslid `PDFARevisionNumber.Revision_1` toe.

   >[!NOTE]
   >
   >De PDF-versie van een PDF/A-document is 1.4, ongeacht de waarde die u opgeeft.

1. Genereer een PDF/A-document.

   Maak een PDF-document door de `OutputServiceService` methode van het `generatePDFOutput`object aan te roepen en de volgende waarden door te geven:

   * Een opsommingswaarde van TransformationFormat. Geef op om een PDF-document te genereren. `TransformationFormat.PDFA`
   * Een tekenreekswaarde waarmee de naam van het formulierontwerp wordt opgegeven.
   * Een tekenreekswaarde die de hoofdmap van de inhoud opgeeft waar het formulierontwerp zich bevindt.
   * Een `PDFOutputOptionsSpec` object dat PDF-runtime-opties bevat.
   * Een `RenderOptionsSpec` object dat renderingopties bevat.
   * Het `BLOB` object dat de XML-gegevensbron bevat die gegevens bevat die met het formulierontwerp moeten worden samengevoegd.
   * Een `BLOB` object dat door de `generatePDFOutput` methode is gevuld. De `generatePDFOutput` methode vult dit object met gegenereerde metagegevens die het document beschrijven. (Deze parameterwaarde is alleen vereist voor aanroepen van webservices.)
   * Een `BLOB` object dat door de `generatePDFOutput` methode is gevuld. De `generatePDFOutput` methode vult dit object met resultaatgegevens. (Deze parameterwaarde is alleen vereist voor aanroepen van webservices.)
   * Een `OutputResult` object dat de resultaten van de bewerking bevat. (Deze parameterwaarde is alleen vereist voor aanroepen van webservices.)

   >[!NOTE]
   >
   >U kunt ook een PDF/A-document maken door de methode `OutputClient` 2 van het `generatePDFOutput`object aan te roepen. (Zie Documenten [die in de (afgekeurde) Inhoudsdiensten worden gevestigd tot de Dienst](creating-document-output-streams.md#passing-documents-located-in-content-services-deprecated-to-the-output-service)van de Output overgaan.)

1. Haal de resultaten van de bewerking op.

   * Maak een `System.IO.FileStream` object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die een locatie van een XML-bestand vertegenwoordigt die resultaatgegevens bevat. Controleer of de bestandsnaamextensie .xml is.
   * Maak een bytearray waarin de gegevensinhoud wordt opgeslagen van het `BLOB` object dat met resultaatgegevens is gevuld via de `OutputServiceService` methode van het `generatePDFOutput` object (de achtste parameter). Vul de bytearray met de waarde van het `BLOB` veld van het `MTOM` object.
   * Maak een `System.IO.BinaryWriter` object door de constructor ervan aan te roepen en het `System.IO.FileStream` object door te geven.
   * Schrijf de inhoud van de bytearray naar het XML-bestand door de methode van het `System.IO.BinaryWriter` `Write` object aan te roepen en de bytearray door te geven.

**Zie ook**

[Overzicht van de stappen](creating-document-output-streams.md#summary-of-steps)

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Het overgaan van Documenten die in de (verlaten) Inhoudsdiensten worden gevestigd aan de Dienst van de Output {#passing-documents-located-in-content-services-deprecated-to-the-output-service}

De service Uitvoer genereert een niet-interactief PDF-formulier dat is gebaseerd op een formulierontwerp dat gewoonlijk als een XDP-bestand wordt opgeslagen en in Designer wordt gemaakt. U kunt een `com.adobe.idp.Document` object met het formulierontwerp doorgeven aan de service Uitvoer. De uitvoerservice geeft vervolgens het formulierontwerp weer dat zich in het `com.adobe.idp.Document` object bevindt.

Een voordeel van het doorgeven van een `com.adobe.idp.Document` object aan de uitvoerservice is dat andere AEM Forms-servicebewerkingen een `com.adobe.idp.Document` instantie retourneren. Dat wil zeggen dat u een `com.adobe.idp.Document` instantie van een andere servicebewerking kunt ophalen en renderen. Stel bijvoorbeeld dat een XDP-bestand wordt opgeslagen in een knooppunt Content Services (afgekeurd) met de naam `/Company Home/Form Designs`, zoals in de volgende afbeelding wordt getoond.

U kunt Loan.xdp programmatically terugwinnen van de Diensten van de Inhoud (afgekeurd) en het XDP dossier tot de dienst van de Output binnen een `com.adobe.idp.Document` voorwerp overgaan.

>[!NOTE]
>
>Voor meer informatie over de dienst van Vormen, zie de Verwijzing van de [Diensten voor AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary_of_steps-2}

Als u een document dat is verkregen van Content Services (afgekeurd) wilt doorgeven aan de service Uitvoer, voert u de volgende taken uit:

1. Inclusief projectbestanden.
1. Maak een Output- en een Document Management Client API-object.
1. Haal het formulierontwerp op bij Inhoudsservices (afgekeurd).
1. Het niet-interactieve PDF-formulier weergeven.
1. Voer een handeling uit met de gegevensstroom.

**Projectbestanden opnemen**

Neem de benodigde bestanden op voor uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, neemt u de proxybestanden op.

**Een Output en een Document Management Client API-object maken**

Voordat u programmatisch een uitvoerservice-API-bewerking kunt uitvoeren, maakt u een Output Client-API-object. Omdat met deze workflow een XDP-bestand wordt opgehaald van Content Services (afgekeurd), maakt u ook een Document Management API-object.

**Het formulierontwerp ophalen van Content Services (afgekeurd)**

Haal het XDP-bestand op van Content Services (afgekeurd) met behulp van de Java- of webservice-API. Het XDP-bestand wordt geretourneerd binnen een `com.adobe.idp.Document` instantie (of een `BLOB` instantie als u webservices gebruikt). U kunt de `com.adobe.idp.Document` instantie vervolgens aan de uitvoerservice doorgeven.

**Het niet-interactieve PDF-formulier weergeven**

Als u een niet-interactief formulier wilt weergeven, geeft u het exemplaar dat door Content Services (afgekeurd) is geretourneerd, door aan de uitvoerservice. `com.adobe.idp.Document`

>[!NOTE]
>
>Twee nieuwe methoden met de naam `generatePDFOutput2`en g `eneratePrintedOutput2`accepteren een `com.adobe.idp.Document` object dat een formulierontwerp bevat. U kunt ook een formulier `com.adobe.idp.Document`dat het formulierontwerp bevat, aan de Output-service doorgeven wanneer u een afdrukstroom naar een netwerkprinter verzendt.

**Een handeling uitvoeren met de gegevensstroom van het formulier**

U kunt het niet-interactieve formulier opslaan als een PDF-bestand. Het formulier kan worden weergegeven in Adobe Reader of Acrobat.

**Zie ook**

[Documenten doorgeven aan de uitvoerservice met de Java API](creating-document-output-streams.md#pass-documents-to-the-output-service-using-the-java-api)

[Documenten doorgeven aan de uitvoerservice met behulp van de webservice-API](creating-document-output-streams.md#pass-documents-to-the-output-service-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Uitvoerservice-API - Snel starten](/help/forms/developing/output-service-java-api-quick.md#output-service-java-api-quick-start-soap)

[PDF-documenten maken met behulp van fragmenten](creating-document-output-streams.md#creating-pdf-documents-using-fragments)

### Documenten doorgeven aan de uitvoerservice met de Java API {#pass-documents-to-the-output-service-using-the-java-api}

Geef een document door dat is opgehaald uit Content Services (afgekeurd) met de Output-service en Content Services (afgekeurd) API (Java):

1. Inclusief projectbestanden.

   Neem JAR-bestanden voor clients, zoals adobe-output-client.jar en adobe-contentservices-client.jar, op in het klassenpad van uw Java-project.

1. Maak een Output- en een Document Management Client API-object.

   * Maak een `ServiceClientFactory` object dat verbindingseigenschappen bevat. (Zie Verbindingseigenschappen [instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)
   * Maak een `OutputClient` object door de constructor ervan te gebruiken en het `ServiceClientFactory` object door te geven.
   * Maak een `DocumentManagementServiceClientImpl` object door de constructor ervan te gebruiken en het `ServiceClientFactory` object door te geven.

1. Haal het formulierontwerp op bij Inhoudsservices (afgekeurd).

   Roep de methode van het `DocumentManagementServiceClientImpl` `retrieveContent` object aan en geef de volgende waarden door:

   * Een tekenreekswaarde die de opslaglocatie opgeeft waar de inhoud wordt toegevoegd. De standaardopslag is `SpacesStore`. Deze waarde is een verplichte parameter.
   * Een tekenreekswaarde die het volledig gekwalificeerde pad opgeeft van de inhoud die moet worden opgehaald (bijvoorbeeld `/Company Home/Form Designs/Loan.xdp`). Deze waarde is een verplichte parameter.
   * Een tekenreekswaarde die de versie opgeeft. Deze waarde is een optionele parameter en u kunt een lege tekenreeks doorgeven. In dit geval wordt de laatste versie opgehaald.

   De `retrieveContent` methode retourneert een `CRCResult` object dat het XDP-bestand bevat. Haal een `com.adobe.idp.Document` instantie op door de `CRCResult` methode van het `getDocument` object aan te roepen.

1. Het niet-interactieve PDF-formulier weergeven.

   Roep de methode van het `OutputClient` `generatePDFOutput2` object aan en geef de volgende waarden door:

   * Een `TransformationFormat` opsommingswaarde. Geef op om een PDF-document te genereren. `TransformationFormat.PDF`
   * Een tekenreekswaarde die de hoofdmap van de inhoud opgeeft waar de extra bronnen, zoals afbeeldingen, zich bevinden.
   * Een `com.adobe.idp.Document` object dat het formulierontwerp vertegenwoordigt (gebruik de instantie die door de `CRCResult` methode van het `getDocument` object wordt geretourneerd).
   * Een `PDFOutputOptionsSpec` object dat PDF-runtime-opties bevat.
   * Een `RenderOptionsSpec` object dat renderingopties bevat.
   * Het `com.adobe.idp.Document` object dat de XML-gegevensbron bevat die gegevens bevat die met het formulierontwerp moeten worden samengevoegd.

   De `generatePDFOutput2` methode retourneert een `OutputResult` object dat de resultaten van de bewerking bevat.

1. Voer een handeling uit met de gegevensstroom van het formulier.

   * Haal een `com.adobe.idp.Document` object op dat het niet-interactieve formulier vertegenwoordigt door de `OutputResult` methode van het `getGeneratedDoc` object aan te roepen.
   * Maak een `java.io.File` object dat de resultaten van de bewerking bevat. Controleer of de bestandsnaamextensie .pdf is.
   * Roep de `com.adobe.idp.Document` methode van het `copyToFile` object aan om de inhoud van het `com.adobe.idp.Document` object naar het bestand te kopiëren (zorg dat u het `com.adobe.idp.Document` object gebruikt dat door de `getGeneratedDoc` methode is geretourneerd).

**Zie ook**

[Overzicht van de stappen](creating-document-output-streams.md#summary-of-steps)

[Snel starten (EJB-modus): Documenten doorgeven aan de uitvoerservice met de Java API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-passing-documents-to-the-output-service-using-the-java-api)

[Snel starten (SOAP-modus): Documenten doorgeven aan de uitvoerservice met de Java API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-passing-documents-to-the-output-service-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Documenten doorgeven aan de uitvoerservice met behulp van de webservice-API {#pass-documents-to-the-output-service-using-the-web-service-api}

Geef een document door dat is opgehaald uit Content Services (afgekeurd) met de Output-service en Content Services (afgekeurd) API (webservice):

1. Inclusief projectbestanden.

   Creeer een project van Microsoft .NET dat MTOM gebruikt. Omdat deze cliënttoepassing de twee diensten van AEM Forms aanhaalt, creeer twee de dienstverwijzingen. Gebruik de volgende definitie WSDL voor de de dienstverwijzing verbonden aan de dienst van de Output: `http://localhost:8080/soap/services/OutputService?WSDL&lc_version=9.0.1`.

   Gebruik de volgende definitie WSDL voor de de dienstverwijzing verbonden aan de dienst van het Beheer van het Document: `http://localhost:8080/soap/services/DocumentManagementService?WSDL&lc_version=9.0.1`.

   Omdat het `BLOB` gegevenstype gemeenschappelijk voor beide de dienstverwijzingen is, kwalificeer volledig het `BLOB` gegevenstype wanneer het gebruiken van het. In de overeenkomstige webservice quick start zijn alle `BLOB` instanties volledig gekwalificeerd.

   >[!NOTE]
   >
   >Vervangen `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een Output- en een Document Management Client API-object.

   * Maak een `OutputServiceClient` object met de standaardconstructor.
   * Maak een `OutputServiceClient.Endpoint.Address` object met de `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde door die de WSDL opgeeft voor de service Forms (bijvoorbeeld `http://localhost:8080/soap/services/OutputService?blob=mtom`). U hoeft het `lc_version` kenmerk niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.)
   * Maak een `System.ServiceModel.BasicHttpBinding` object door de waarde van het `OutputServiceClient.Endpoint.Binding` veld op te halen. Kiezen naar de geretourneerde waarde `BasicHttpBinding`.
   * Stel het `System.ServiceModel.BasicHttpBinding` veld van het `MessageEncoding` object in op `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam voor AEM-formulieren toe aan het veld `OutputServiceClient.ClientCredentials.UserName.UserName`.
      * Wijs de bijbehorende wachtwoordwaarde aan het veld toe `OutputServiceClient.ClientCredentials.UserName.Password`.
      * Wijs de constante waarde toe `HttpClientCredentialType.Basic` aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
   * Wijs de constante waarde toe `BasicHttpSecurityMode.TransportCredentialOnly` aan het veld `BasicHttpBindingSecurity.Security.Mode`.

   >[!NOTE]
   >
   >Herhaal deze stappen voor de `DocumentManagementServiceClient`dienstcliënt.

1. Haal het formulierontwerp op bij Inhoudsservices (afgekeurd).

   Haal inhoud op door de methode van het `DocumentManagementServiceClient` object aan te roepen `retrieveContent` en de volgende waarden door te geven:

   * Een tekenreekswaarde die de opslaglocatie opgeeft waar de inhoud wordt toegevoegd. De standaardopslag is `SpacesStore`. Deze waarde is een verplichte parameter.
   * Een tekenreekswaarde die het volledig gekwalificeerde pad opgeeft van de inhoud die moet worden opgehaald (bijvoorbeeld `/Company Home/Form Designs/Loan.xdp`). Deze waarde is een verplichte parameter.
   * Een tekenreekswaarde die de versie opgeeft. Deze waarde is een optionele parameter en u kunt een lege tekenreeks doorgeven. In dit geval wordt de laatste versie opgehaald.
   * Een parameter van de koordoutput die doorbladert verbindingswaarde opslaat.
   * Een `BLOB` uitvoerparameter die de inhoud opslaat. U kunt deze uitvoerparameter gebruiken om de inhoud op te halen.
   * Een `ServiceReference1.MyMapOf_xsd_string_To_xsd_anyType` uitvoerparameter die inhoudskenmerken opslaat.
   * Een `CRCResult` uitvoerparameter. In plaats van dit object te gebruiken, kunt u de `BLOB` uitvoerparameter gebruiken om de inhoud op te halen.

1. Het niet-interactieve PDF-formulier weergeven.

   Roep de methode van het `OutputServiceClient` `generatePDFOutput2` object aan en geef de volgende waarden door:

   * Een `TransformationFormat` opsommingswaarde. Geef op om een PDF-document te genereren. `TransformationFormat.PDF`
   * Een tekenreekswaarde die de hoofdmap van de inhoud opgeeft waar de extra bronnen, zoals afbeeldingen, zich bevinden.
   * Een `BLOB` object dat staat voor het formulierontwerp (gebruik de `BLOB` instantie die wordt geretourneerd door Content Services (afgekeurd)).
   * Een `PDFOutputOptionsSpec` object dat PDF-runtime-opties bevat.
   * Een `RenderOptionsSpec` object dat renderingopties bevat.
   * Het `BLOB` object dat de XML-gegevensbron bevat die gegevens bevat die met het formulierontwerp moeten worden samengevoegd.
   * Een uitvoerobject `BLOB` dat door de `generatePDFOutput2` methode wordt gevuld. De `generatePDFOutput2` methode vult dit object met gegenereerde metagegevens die het document beschrijven. (Deze parameterwaarde is alleen vereist voor aanroepen van een webservice.)
   * Een uitvoerobject `OutputResult` dat de resultaten van de bewerking bevat. (Deze parameterwaarde is alleen vereist voor aanroepen van een webservice.)

   De `generatePDFOutput2` methode retourneert een `BLOB` object dat het niet-interactieve PDF-formulier bevat.

1. Voer een handeling uit met de gegevensstroom van het formulier.

   * Maak een `System.IO.FileStream` object door de constructor ervan aan te roepen. Geef een tekenreekswaarde door die staat voor de bestandslocatie van het interactieve PDF-document en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud wordt opgeslagen van het `BLOB` object dat van de `generatePDFOutput2` methode is opgehaald. Vul de bytearray met de waarde van het `BLOB` `MTOM` gegevenslid van het object.
   * Maak een `System.IO.BinaryWriter` object door de constructor ervan aan te roepen en het `System.IO.FileStream` object door te geven.
   * Schrijf de inhoud van de bytearray naar een PDF-bestand door de methode van het `System.IO.BinaryWriter` `Write` object aan te roepen en de bytearray door te geven.

**Zie ook**

[Overzicht van de stappen](creating-document-output-streams.md#summary-of-steps)

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

## Documenten in de opslagplaats doorgeven aan de uitvoerservice {#passing-documents-located-in-the-repository-to-the-output-service}

De service Uitvoer genereert een niet-interactief PDF-formulier dat is gebaseerd op een formulierontwerp dat gewoonlijk als een XDP-bestand wordt opgeslagen en in Designer wordt gemaakt. U kunt een `com.adobe.idp.Document` object met het formulierontwerp doorgeven aan de service Uitvoer. De uitvoerservice geeft vervolgens het formulierontwerp weer dat zich in het `com.adobe.idp.Document` object bevindt.

Een voordeel van het doorgeven van een `com.adobe.idp.Document` object aan de uitvoerservice is dat andere AEM Forms-servicebewerkingen een `com.adobe.idp.Document` instantie retourneren. Dat wil zeggen dat u een `com.adobe.idp.Document` instantie van een andere servicebewerking kunt ophalen en renderen. Stel bijvoorbeeld dat een XDP-bestand wordt opgeslagen in de opslagplaats van AEM Forms, zoals in de volgende afbeelding wordt getoond.

![pd_pd_formrepository](assets/pd_pd_formrepository.png)

De *map FormsFolder* is een door de gebruiker gedefinieerde locatie in de opslagplaats voor AEM Forms (deze locatie is een voorbeeld en bestaat niet standaard). In dit voorbeeld bevindt zich een formulierontwerp met de naam Loan.xdp in deze map. Naast het formulierontwerp kunnen ook andere formulierelementen, zoals afbeeldingen, op deze locatie worden opgeslagen. Het pad naar een bron in de gegevensopslagruimte van AEM Forms is:

`Applications/Application-name/Application-version/Folder.../Filename`

U kunt Loan.xdp programmatically terugwinnen van de bewaarplaats van AEM Forms en het tot de dienst van de Output binnen een `com.adobe.idp.Document` voorwerp overgaan.

U kunt op twee manieren een PDF maken op basis van een XDP-bestand in de opslagplaats. U kunt de XDP-locatie doorgeven via verwijzing of u kunt de XDP-locatie via programmacode ophalen uit de opslagplaats en deze doorgeven aan de Output-service in een XDP-bestand.

[Snel starten (EJB-modus): Een PDF-document maken op basis van een XDP-bestand van een toepassing met behulp van de Java API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-a-pdf-document-based-on-an-application-xdp-file-using-the-java-api) (toont hoe u de locatie van het XDP-bestand via verwijzing doorgeeft).

[Snel starten (EJB-modus): Het overgaan van een document dat in de Bewaarplaats van AEM Forms aan de dienst van de Output gebruikend Java API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-passing-a-document-located-in-the-repository-to-the-output-service-using-the-java-api) wordt gevestigd (toont hoe te om het XDP dossier van de Bewaarplaats van AEM Forms programmatically terug te winnen en het over te gaan tot de dienst van de Output binnen een `com.adobe.idp.Document` geval). (In deze sectie wordt besproken hoe deze taak moet worden uitgevoerd)

>[!NOTE]
>
>Voor meer informatie over de dienst van Vormen, zie de Verwijzing van de [Diensten voor AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary_of_steps-3}

Voer de volgende taken uit om een document dat is verkregen van de gegevensopslagruimte AEM Forms, door te geven aan de uitvoerservice:

1. Inclusief projectbestanden.
1. Maak een Output- en een Document Management Client API-object.
1. Haal het formulierontwerp op uit de gegevensopslagruimte van AEM Forms.
1. Het niet-interactieve PDF-formulier weergeven.
1. Voer een handeling uit met de gegevensstroom.

**Projectbestanden opnemen**

Neem de benodigde bestanden op voor uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, neemt u de proxybestanden op.

**Een Output en een Document Management Client API-object maken**

Voordat u programmatisch een uitvoerservice-API-bewerking kunt uitvoeren, maakt u een Output Client-API-object. Omdat met deze workflow een XDP-bestand wordt opgehaald van Content Services (afgekeurd), maakt u ook een Document Management API-object.

**Het formulierontwerp ophalen uit de gegevensopslagruimte van AEM Forms**

Haal het XDP-bestand op uit de gegevensopslagruimte van AEM Forms met behulp van de Repository-API. (Zie [Bronnen](/help/forms/developing/aem-forms-repository.md#reading-resources)lezen.)

Het XDP-bestand wordt geretourneerd binnen een `com.adobe.idp.Document` instantie (of een `BLOB` instantie als u webservices gebruikt). U kunt de `com.adobe.idp.Document` instantie vervolgens aan de uitvoerservice doorgeven.

**Het niet-interactieve PDF-formulier weergeven**

Als u een niet-interactief formulier wilt genereren, geeft u het exemplaar door dat is geretourneerd met de AEM Forms Repository-API. `com.adobe.idp.Document`

>[!NOTE]
>
>Twee nieuwe methoden noemen `generatePDFOutput2`en `generatePrintedOutput2`accepteren een `com.adobe.idp.Document`object dat een formulierontwerp bevat. U kunt ook een formulier met het formulierontwerp aan de Output-service doorgeven wanneer u een afdrukstroom naar een netwerkprinter verzendt. `com.adobe.idp.Document`

**Een handeling uitvoeren met de gegevensstroom van het formulier**

U kunt het niet-interactieve formulier opslaan als een PDF-bestand. Het formulier kan worden weergegeven in Adobe Reader of Acrobat.

**Zie ook**

[Documenten in de opslagplaats doorgeven aan de uitvoerservice met behulp van de Java API](creating-document-output-streams.md#pass-documents-located-in-the-repository-to-the-output-service-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Uitvoerservice-API - Snel starten](/help/forms/developing/output-service-java-api-quick.md#output-service-java-api-quick-start-soap)

ResourceRepositoryClient

### Documenten in de opslagplaats doorgeven aan de uitvoerservice met behulp van de Java API {#pass-documents-located-in-the-repository-to-the-output-service-using-the-java-api}

Geef een document dat is opgehaald uit de opslagplaats door gebruik te maken van de Output-service en de Repository-API (Java):

1. Inclusief projectbestanden.

   Neem JAR-bestanden voor clients, zoals adobe-output-client.jar en adobe-repository-client.jar, op in het klassenpad van uw Java-project.

1. Maak een Output- en een Document Management Client API-object.

   * Maak een `ServiceClientFactory` object dat verbindingseigenschappen bevat. (Zie Verbindingseigenschappen [instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)
   * Maak een `OutputClient` object door de constructor ervan te gebruiken en het `ServiceClientFactory` object door te geven.
   * Maak een `DocumentManagementServiceClientImpl` object door de constructor ervan te gebruiken en het `ServiceClientFactory` object door te geven.

1. Haal het formulierontwerp op uit de gegevensopslagruimte van AEM Forms.

   Roep de `ResourceRepositoryClient` methode van het `readResourceContent` object aan en geef een tekenreekswaarde door die de URI-locatie aan het XDP-bestand opgeeft. Bijvoorbeeld, `/Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`. Deze waarde is verplicht. Deze methode retourneert een `com.adobe.idp.Document` instantie die het XDP-bestand vertegenwoordigt.

1. Het niet-interactieve PDF-formulier weergeven.

   Roep de methode van het `OutputClient` `generatePDFOutput2` object aan en geef de volgende waarden door:

   * Een `TransformationFormat` opsommingswaarde. Geef op om een PDF-document te genereren. `TransformationFormat.PDF`
   * Een tekenreekswaarde die de hoofdmap van de inhoud opgeeft waar de extra bronnen, zoals afbeeldingen, zich bevinden. Bijvoorbeeld, `repository:///Applications/FormsApplication/1.0/FormsFolder/`.
   * Een `com.adobe.idp.Document` object dat het formulierontwerp vertegenwoordigt (gebruik de instantie die door de `ResourceRepositoryClient` methode van het `readResourceContent` object wordt geretourneerd).
   * Een `PDFOutputOptionsSpec` object dat PDF-runtime-opties bevat.
   * Een `RenderOptionsSpec` object dat renderingopties bevat.
   * Het `com.adobe.idp.Document` object dat de XML-gegevensbron bevat die gegevens bevat die met het formulierontwerp moeten worden samengevoegd.

   De `generatePDFOutput2` methode retourneert een `OutputResult` object dat de resultaten van de bewerking bevat.

1. Voer een handeling uit met de gegevensstroom van het formulier.

   * Haal een `com.adobe.idp.Document` object op dat het niet-interactieve formulier vertegenwoordigt door de `OutputResult` methode van het `getGeneratedDoc` object aan te roepen.
   * Maak een `java.io.File` object dat de resultaten van de bewerking bevat. Controleer of de bestandsnaamextensie .pdf is.
   * Roep de `com.adobe.idp.Document` methode van het `copyToFile` object aan om de inhoud van het `com.adobe.idp.Document` object naar het bestand te kopiëren (zorg dat u het `com.adobe.idp.Document` object gebruikt dat door de `getGeneratedDoc` methode is geretourneerd).

**Zie ook**

[Overzicht van de stappen](creating-document-output-streams.md#summary-of-steps)

[Snel starten (EJB-modus): Een document in de gegevensopslagruimte AEM Forms doorgeven aan de uitvoerservice met behulp van de Java API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-passing-a-document-located-in-the-repository-to-the-output-service-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## PDF-documenten maken met behulp van fragmenten {#creating-pdf-documents-using-fragments}

Met de services Uitvoer en Assembler kunt u een uitvoerstream maken, zoals een PDF-document, die is gebaseerd op fragmenten. De Assembler-service brengt een XDP-document samen dat is gebaseerd op fragmenten die zich in meerdere XDP-bestanden bevinden. Het samengevoegde XDP-document wordt doorgegeven aan de Output-service, die een PDF-document maakt. Hoewel in deze workflow een PDF-document wordt gegenereerd, kan de uitvoerservice voor deze workflow andere uitvoertypen genereren, zoals ZPL. Een PDF-document wordt alleen gebruikt voor discussie.

Deze workflow wordt in de volgende afbeelding getoond.

![cp_cp_outputassemblefragmenten](assets/cp_cp_outputassemblefragments.png)

Voordat u PDF-documenten *maakt met behulp van fragmenten*, is het raadzaam bekend te raken met het gebruik van de Assembler-service om meerdere XDP-documenten samen te stellen. (Zie Meerdere XDP-fragmenten [samenstellen](/help/forms/developing/assembling-pdf-documents.md#assembling-multiple-xdp-fragments).)

>[!NOTE]
>
>U kunt ook een formulierontwerp dat door de Assembler-service is samengesteld, aan de Forms-service doorgeven in plaats van aan de Output-service. Het belangrijkste verschil tussen de service Uitvoer en Forms is dat de service Forms interactieve PDF-documenten genereert en dat de service Uitvoer niet-interactieve PDF-documenten produceert. Ook kan de Forms-service geen op printers gebaseerde uitvoerstreams zoals ZPL genereren.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Output, zie de Verwijzing van de [Diensten voor AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary_of_steps-4}

Voer de volgende stappen uit om een PDF-document te maken op basis van fragmenten:

1. Inclusief projectbestanden.
1. Maak een Output- en Assembler Client-object.
1. Gebruik de Assembler-service om het formulierontwerp te genereren.
1. Gebruik de uitvoerservice om het PDF-document te genereren.
1. Sla het PDF-document op als een PDF-bestand.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u de proxybestanden opnemen.

**Een Output- en Assembler Client-object maken**

Voordat u programmatisch een uitvoerservice-API-bewerking kunt uitvoeren, maakt u een Output Client API-object. Bovendien maakt u een Assembler Client API-object omdat deze workflow de Assembler-service oproept om het formulierontwerp te maken.

**Met de Assembler-service kunt u het formulierontwerp genereren**

Met de Assembler-service kunt u het formulierontwerp genereren met behulp van fragmenten. De Assembler-service retourneert een `com.adobe.idp.Document` exemplaar dat het formulierontwerp bevat.

**De service Uitvoer gebruiken om het PDF-document te genereren**

U kunt de service Uitvoer gebruiken om een PDF-document te genereren met behulp van het formulierontwerp dat de Assembler-service heeft gemaakt. Geef de `com.adobe.idp.Document` instantie door die de Assembler-service aan de Output-service heeft geretourneerd.

**Het PDF-document opslaan als een PDF-bestand**

Nadat de service Uitvoer een PDF-document heeft gegenereerd, kunt u het opslaan als een PDF-bestand.

**Zie ook**

[Een PDF-document maken op basis van fragmenten met de Java API](creating-document-output-streams.md#create-a-pdf-document-based-on-fragments-using-the-java-api)

[Een PDF-document maken op basis van fragmenten met de webservice-API](creating-document-output-streams.md#create-a-pdf-document-based-on-fragments-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Uitvoerservice-API - Snel starten](/help/forms/developing/output-service-java-api-quick.md#output-service-java-api-quick-start-soap)

[Meerdere XDP-fragmenten samenstellen](/help/forms/developing/assembling-pdf-documents.md#assembling-multiple-xdp-fragments)

[PDF-documenten maken](creating-document-output-streams.md#creating-pdf-documents)

### Een PDF-document maken op basis van fragmenten met de Java API {#create-a-pdf-document-based-on-fragments-using-the-java-api}

Maak een PDF-document op basis van fragmenten met de API voor uitvoerservice en de API voor vergaderingsservice (Java):

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-output-client.jar, op in het klassenpad van uw Java-project.

1. Maak een Output- en Assembler Client-object.

   * Maak een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Maak een `OutputClient` object door de constructor ervan te gebruiken en het `ServiceClientFactory` object door te geven.
   * Maak een `AssemblerServiceClient` object door de constructor ervan te gebruiken en het `ServiceClientFactory` object door te geven.

1. Gebruik de Assembler-service om het formulierontwerp te genereren.

   Roep de `AssemblerServiceClient` methode van het `invokeDDX` object aan en geef de volgende vereiste waarden door:

   * Een `com.adobe.idp.Document` object dat staat voor het te gebruiken DDX-document.
   * Een `java.util.Map` object dat de invoer-XDP-bestanden bevat.
   * Een `com.adobe.livecycle.assembler.client.AssemblerOptionSpec` object dat de runtime-opties opgeeft, inclusief het standaardlettertype en het niveau van het taaklogbestand.

   De `invokeDDX` methode retourneert een `com.adobe.livecycle.assembler.client.AssemblerResult` object dat het geassembleerde XDP-document bevat. Voer de volgende handelingen uit om het samengevoegde XDP-document op te halen:

   * Roep de `AssemblerResult` methode van het `getDocuments` object aan. Deze methode retourneert een `java.util.Map` object.
   * Doorloop het `java.util.Map` object totdat u het resulterende `com.adobe.idp.Document` object vindt.
   * Roep de `com.adobe.idp.Document` methode van het `copyToFile` object aan om het samengevoegde XDP-document te extraheren.


1. Gebruik de uitvoerservice om het PDF-document te genereren.

   Roep de methode van het `OutputClient` `generatePDFOutput2` object aan en geef de volgende waarden door:

   * Een `TransformationFormat` opsommingswaarde. Als u een PDF-document wilt genereren, geeft u `TransformationFormat.PDF`
   * Een tekenreekswaarde die de hoofdmap van de inhoud opgeeft waar de extra bronnen, zoals afbeeldingen, zich bevinden
   * Een `com.adobe.idp.Document` object dat het formulierontwerp vertegenwoordigt (gebruik de instantie die door de Assembler-service is geretourneerd)
   * Een `PDFOutputOptionsSpec` object dat PDF-runtime-opties bevat
   * Een `RenderOptionsSpec` object dat renderingopties bevat
   * Het `com.adobe.idp.Document` object dat de XML-gegevensbron bevat die gegevens bevat die met het formulierontwerp moeten worden samengevoegd

   De `generatePDFOutput2` methode retourneert een `OutputResult` object dat de resultaten van de bewerking bevat

1. Sla het PDF-document op als een PDF-bestand.

   * Haal een `com.adobe.idp.Document` object op dat het PDF-document vertegenwoordigt door de `OutputResult` methode van het `getGeneratedDoc` object aan te roepen.
   * Maak een `java.io.File` object dat de resultaten van de bewerking bevat. Zorg ervoor dat de bestandsnaamextensie .pdf is.
   * Roep de `com.adobe.idp.Document` methode van het `copyToFile` object aan om de inhoud van het `com.adobe.idp.Document` object naar het bestand te kopiëren. (Zorg ervoor dat u het `com.adobe.idp.Document` object gebruikt dat de `getGeneratedDoc` methode heeft geretourneerd.)

**Zie ook**

[Overzicht van de stappen](creating-document-output-streams.md#summary-of-steps)

[Snel starten (EJB-modus): Een PDF-document maken op basis van fragmenten met de Java API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-a-pdf-document-based-on-fragments-using-the-java-api)

[Snel starten (SOAP-modus): Een PDF-document maken op basis van fragmenten met de Java API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-a-pdf-document-based-on-fragments-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)instellen.

### Een PDF-document maken op basis van fragmenten met de webservice-API {#create-a-pdf-document-based-on-fragments-using-the-web-service-api}

Maak een PDF-document op basis van fragmenten met de API voor uitvoerservice en de API voor vergaderingsservice (webservice):

1. Inclusief projectbestanden.

   Creeer een project van Microsoft .NET dat MTOM gebruikt. Gebruik de volgende definitie WSDL voor de de dienstverwijzing verbonden aan de dienst van de Output:

   ```java
    http://localhost:8080/soap/services/OutputService?WSDL&lc_version=9.0.1.
   ```

   Gebruik de volgende definitie WSDL voor de de dienstverwijzing verbonden aan de dienst van de Assembler:

   ```java
    http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1.
   ```

   Omdat het `BLOB` gegevenstype gemeenschappelijk voor beide de dienstverwijzingen is, kwalificeer volledig het `BLOB` gegevenstype wanneer het gebruiken van het. In de overeenkomstige webservice quick start zijn alle `BLOB` instanties volledig gekwalificeerd.

   >[!NOTE]
   >
   >Vervangen `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een Output- en Assembler Client-object.

   * Maak een `OutputServiceClient` object met de standaardconstructor.
   * Maak een `OutputServiceClient.Endpoint.Address` object met de `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de service AEM Forms (bijvoorbeeld `http://localhost:8080/soap/services/OutputService?blob=mtom`.) U hoeft het `lc_version` kenmerk niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt. Geef echter op `?blob=mtom` om MTOM te gebruiken.
   * Maak een `System.ServiceModel.BasicHttpBinding` object door de waarde van het `OutputServiceClient.Endpoint.Binding` veld op te halen. Kiezen naar de geretourneerde waarde `BasicHttpBinding`.
   * Stel het `System.ServiceModel.BasicHttpBinding` veld van het `MessageEncoding` object in op `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam voor AEM-formulieren toe aan het `OutputServiceClient.ClientCredentials.UserName.UserName`veld.
      * Wijs de bijbehorende wachtwoordwaarde aan het `OutputServiceClient.ClientCredentials.UserName.Password`veld toe.
      * Wijs de constante waarde toe `HttpClientCredentialType.Basic` aan het `BasicHttpBindingSecurity.Transport.ClientCredentialType`veld.
   * Wijs de `BasicHttpSecurityMode.TransportCredentialOnly` constante waarde toe aan het `BasicHttpBindingSecurity.Security.Mode`veld.

   >[!NOTE]
   >
   >Herhaal deze stappen voor het `AssemblerServiceClient`object.

1. Gebruik de Assembler-service om het formulierontwerp te genereren.

   Roep de methode van het `AssemblerServiceClient` `invokeDDX` object aan en geef de volgende waarden door:

   * Een `BLOB` object dat staat voor het DDX-document
   * Het `MyMapOf_xsd_string_To_xsd_anyType` object dat de vereiste bestanden bevat
   * Een `AssemblerOptionSpec` object dat uitvoeringsopties opgeeft

   De `invokeDDX` methode retourneert een `AssemblerResult` object dat de resultaten van de taak en eventuele uitzonderingen bevat die zich hebben voorgedaan. Voer de volgende handelingen uit om het nieuwe XDP-document te verkrijgen:

   * Open het `AssemblerResult` veld van het `documents` object. Dit is een `Map` object dat de resulterende PDF-documenten bevat.
   * Doorloop het `Map` object om het samengevoegde formulierontwerp op te halen. Cast de naam van dat arraylid `value` naar een `BLOB`. Geef deze `BLOB` instantie door aan de uitvoerservice.


1. Gebruik de uitvoerservice om het PDF-document te genereren.

   Roep de methode van het `OutputServiceClient` `generatePDFOutput2` object aan en geef de volgende waarden door:

   * Een `TransformationFormat` opsommingswaarde. Geef op om een PDF-document te genereren. `TransformationFormat.PDF`
   * Een tekenreekswaarde die de hoofdmap van de inhoud opgeeft waar de extra bronnen, zoals afbeeldingen, zich bevinden.
   * Een `BLOB` object dat het formulierontwerp vertegenwoordigt (gebruik de `BLOB` instantie die door de Assembler-service wordt geretourneerd).
   * Een `PDFOutputOptionsSpec` object dat PDF-runtime-opties bevat.
   * Een `RenderOptionsSpec` object dat renderingopties bevat.
   * Het `BLOB` object dat de XML-gegevensbron bevat die gegevens bevat die met het formulierontwerp moeten worden samengevoegd.
   * Een uitvoerobject `BLOB` dat door de `generatePDFOutput2` methode wordt gevuld. De `generatePDFOutput2` methode vult dit object met gegenereerde metagegevens die het document beschrijven. (Deze parameterwaarde is alleen vereist voor aanroepen van een webservice.)
   * Een uitvoerobject `OutputResult` dat de resultaten van de bewerking bevat. (Deze parameterwaarde is alleen vereist voor aanroepen van een webservice.)

   De `generatePDFOutput2` methode retourneert een `BLOB` object dat het niet-interactieve PDF-formulier bevat.

1. Sla het PDF-document op als een PDF-bestand.

   * Maak een `System.IO.FileStream` object door de constructor ervan aan te roepen. Geef een tekenreekswaarde door die staat voor de bestandslocatie van het interactieve PDF-document en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud wordt opgeslagen van het `BLOB` object dat van de `generatePDFOutput2` methode is opgehaald. Vul de bytearray met de waarde van het `BLOB` `MTOM` gegevenslid van het object.
   * Maak een `System.IO.BinaryWriter` object door de constructor ervan aan te roepen en het `System.IO.FileStream` object door te geven.
   * Schrijf de inhoud van de bytearray naar een PDF-bestand door de methode van het `System.IO.BinaryWriter` `Write` object aan te roepen en de bytearray door te geven.

**Zie ook**

[Overzicht van de stappen](creating-document-output-streams.md#summary-of-steps)

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

## Afdrukken naar bestanden {#printing-to-files}

U kunt de uitvoerservice gebruiken om streams zoals PostScript, Printer Control Language (PCL) of de volgende labelindelingen naar een bestand af te drukken:

* Zebra - ZPL
* Intermec, IPL
* Datamax - DPL
* TecToshiba - TPCL

Met de service Uitvoer kunt u XML-gegevens samenvoegen met een formulierontwerp en het formulier afdrukken naar een bestand. In de volgende afbeelding ziet u hoe de uitvoerservice laser- en labelbestanden maakt.

>[!NOTE]
>
>Zie Afdrukstromen naar printers [verzenden voor informatie over het verzenden van afdrukstromen naar printers](creating-document-output-streams.md#sending-print-streams-to-printers).

>[!NOTE]
>
>Voor meer informatie over de dienst van de Output, zie de Verwijzing van de [Diensten voor AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary_of_steps-5}

Voer de volgende stappen uit om naar een bestand af te drukken:

1. Inclusief projectbestanden.
1. Maak een Output Client-object.
1. Verwijzen naar een XML-gegevensbron.
1. Stel de runtime-opties voor afdrukken in die nodig zijn om af te drukken naar een bestand.
1. Druk de afdrukstroom naar een bestand af.
1. Haal de resultaten van de bewerking op.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u de proxybestanden opnemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-output-client.jar
* adobe-utilities.jar (vereist als AEM Forms worden geïmplementeerd op JBoss)
* jbossall-client.jar (vereist als AEM Forms worden geïmplementeerd op JBoss)

als AEM Forms worden geïmplementeerd op een ondersteunde J2EE-toepassingsserver die geen JBoss is, moet u de bestanden adobe-utilities.jar en jbossall-client.jar vervangen door JAR-bestanden die specifiek zijn voor de J2EE-toepassingsserver waarop AEM Forms worden geïmplementeerd. (Zie [Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).)

**Een uitvoerclient-object maken**

Voordat u programmatisch een uitvoerservicebewerking kunt uitvoeren, moet u een uitvoerservice-clientobject maken. Als u de Java API gebruikt, maakt u een `OutputClient` object. Als u de Output-webservice-API gebruikt, maakt u een `OutputServiceService` object.

**Verwijzen naar een XML-gegevensbron**

Als u een document wilt afdrukken dat gegevens bevat, moet u verwijzen naar een XML-gegevensbron die XML-elementen bevat voor elk formulierveld dat u wilt vullen met gegevens. De naam van het XML-element moet overeenkomen met de veldnaam. Een XML-element wordt genegeerd als het niet overeenkomt met een formulierveld of als de naam van het XML-element niet overeenkomt met de veldnaam. Het is niet nodig de volgorde aan te passen waarin de XML-elementen worden weergegeven als alle XML-elementen zijn opgegeven.

**Stel runtime-opties voor afdrukken in die nodig zijn om af te drukken naar een bestand**

Als u naar een bestand wilt afdrukken, moet u de runtime-optie voor de bestands-URI instellen door de locatie en de naam op te geven van het bestand dat door de uitvoerservice wordt afgedrukt. Als u bijvoorbeeld wilt dat de uitvoerservice een PostScript-bestand met de naam *MortgaugeForm.ps* afdrukt naar C:\Adobe, geeft u C:\Adobe\MortgageForm.ps op.

>[!NOTE]
>
>Er zijn optionele uitvoeringsopties die u kunt definiëren. Zie de `PrintedOutputOptionsSpec` klasseverwijzing in de API-naslaggids voor [AEM Forms voor informatie over alle opties die u kunt instellen](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**De afdrukstroom naar een bestand afdrukken**

Nadat u naar een geldige XML-gegevensbron met formuliergegevens hebt verwezen en u afdrukopties hebt ingesteld, kunt u de uitvoerservice aanroepen, waardoor een bestand wordt afgedrukt.

**De resultaten van de bewerking ophalen**

Nadat de dienst van de Output een verrichting uitvoert, keert het diverse gegevenspunten, zoals de gegevens van XML terug, die specificeren of de verrichting succesvol was.

**Zie ook**

[Afdrukken naar bestanden met de Java API](creating-document-output-streams.md#print-to-files-using-the-java-api)

[Afdrukken naar bestanden met de webservice-API](creating-document-output-streams.md#print-to-files-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Uitvoerservice-API - Snel starten](/help/forms/developing/output-service-java-api-quick.md#output-service-java-api-quick-start-soap)

### Afdrukken naar bestanden met de Java API {#print-to-files-using-the-java-api}

Afdrukken naar een bestand met de Output API (Java):

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-output-client.jar, op in het klassenpad van uw Java-project.

1. Maak een Output Client-object.

   * Maak een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Maak een `OutputClient` object door de constructor ervan te gebruiken en het `ServiceClientFactory` object door te geven.

1. Verwijzen naar een XML-gegevensbron.

   * Maak een `java.io.FileInputStream` object dat staat voor de XML-gegevensbron die wordt gebruikt om het document te vullen met de constructor ervan en geef een tekenreekswaarde door die de locatie van het XML-bestand opgeeft.
   * Maak een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en het `java.io.FileInputStream` object door te geven.

1. Stel de runtime-opties voor afdrukken in die nodig zijn om af te drukken naar een bestand.

   * Maak een `PrintedOutputOptionsSpec` object met de constructor ervan.
   * Geef het bestand op door de methode van het PrintOutputOptionsSpec-object aan te roepen en een tekenreekswaarde door te geven die de naam en locatie van het bestand vertegenwoordigt. `setFileURI` Als u bijvoorbeeld wilt dat de uitvoerservice wordt afgedrukt naar een PostScript-bestand met de naam MortgaugeForm.ps in C:\Adobe, geeft u C:\\Adobe\MortgageForm.ps op.
   * Geef het aantal exemplaren op dat moet worden afgedrukt door de methode van het `PrintedOutputOptionsSpec` `setCopies` object aan te roepen en een geheel-getalwaarde door te geven die het aantal kopieën vertegenwoordigt.

1. Druk de afdrukstroom naar een bestand af.

   Druk af naar een bestand door de methode van het `OutputClient` `generatePrintedOutput` object aan te roepen en de volgende waarden door te geven:

   * Een `PrintFormat` opsommingswaarde waarmee de indeling van de afdrukstroom wordt opgegeven die moet worden gemaakt. Als u bijvoorbeeld een PostScript-afdrukstroom wilt maken, geeft u door `PrintFormat.PostScript`.
   * Een tekenreekswaarde waarmee de naam van het formulierontwerp wordt opgegeven.
   * Een tekenreekswaarde die de locatie van verwante secundaire bestanden, zoals afbeeldingsbestanden, opgeeft.
   * Een tekenreekswaarde die de locatie aangeeft van het XDC-bestand dat moet worden gebruikt (u kunt doorgeven `null` als u het XDC-bestand hebt opgegeven dat moet worden gebruikt met het `PrintedOutputOptionsSpec` object).
   * Het `PrintedOutputOptionsSpec` object dat runtimeopties bevat die vereist zijn om naar een bestand af te drukken.
   * Het `com.adobe.idp.Document` object dat de XML-gegevensbron bevat die formuliergegevens bevat.

   De `generatePrintedOutput` methode retourneert een `OutputResult` object dat de resultaten van de bewerking bevat.

   >[!NOTE]
   >
   >De `OutputResult` methode van het `getRecordLevelMetaDataList` object retourneert `null`.

1. Haal de resultaten van de bewerking op.

   * Maak een `com.adobe.idp.Document` object dat de status van de `generatePrintedOutput` methode vertegenwoordigt door de `OutputResult` methode van het `getStatusDoc` object aan te roepen (het `OutputResult` object is door de `generatePrintedOutput` methode geretourneerd).
   * Maak een `java.io.File` object dat de resultaten van de bewerking zal bevatten. Zorg ervoor dat de bestandsextensie XML is.
   * Roep de `com.adobe.idp.Document` methode van het `copyToFile` object aan om de inhoud van het `com.adobe.idp.Document` object naar het bestand te kopiëren (zorg dat u het `com.adobe.idp.Document` object gebruikt dat door de `getStatusDoc` methode is geretourneerd).

**Zie ook**

[Overzicht van de stappen](creating-document-output-streams.md#summary-of-steps)

[Snel starten (SOAP-modus): Afdrukken naar een bestand met de Java API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-printing-to-a-file-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)instellen.

### Afdrukken naar bestanden met de webservice-API {#print-to-files-using-the-web-service-api}

Afdrukken naar een bestand met de Output API (webservice):

1. Inclusief projectbestanden.

   Creeer een project van Microsoft .NET dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/OutputService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een Output Client-object.

   * Maak een `OutputServiceClient` object met de standaardconstructor.
   * Maak een `OutputServiceClient.Endpoint.Address` object met de `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de service AEM Forms (bijvoorbeeld `http://localhost:8080/soap/services/OutputService?blob=mtom`.) U hoeft het `lc_version` kenmerk niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt. Geef echter op `?blob=mtom` om MTOM te gebruiken.
   * Maak een `System.ServiceModel.BasicHttpBinding` object door de waarde van het `OutputServiceClient.Endpoint.Binding` veld op te halen. Kiezen naar de geretourneerde waarde `BasicHttpBinding`.
   * Stel het `System.ServiceModel.BasicHttpBinding` veld van het `MessageEncoding` object in op `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam voor AEM-formulieren toe aan het veld `OutputServiceClient.ClientCredentials.UserName.UserName`.
      * Wijs de bijbehorende wachtwoordwaarde aan het veld toe `OutputServiceClient.ClientCredentials.UserName.Password`.
      * Wijs de constante waarde toe `HttpClientCredentialType.Basic` aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Wijs de constante waarde toe `BasicHttpSecurityMode.TransportCredentialOnly` aan het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Verwijzen naar een XML-gegevensbron.

   * Maak een `BLOB` object met de constructor ervan. Het `BLOB` object wordt gebruikt om formuliergegevens op te slaan.
   * Maak een `System.IO.FileStream` object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de locatie opgeeft van het XML-bestand dat formuliergegevens bevat.
   * Maak een bytearray waarin de inhoud van het `System.IO.FileStream` object wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` eigenschap van het `Length` object op te halen.
   * Vul de bytearray met streamgegevens door de methode van het `System.IO.FileStream` `Read` object aan te roepen en de bytearray, de startpositie en de lengte van de stream door te geven om te lezen.
   * Vul het `BLOB` object door de `binaryData` eigenschap ervan toe te wijzen met de inhoud van de bytearray.

1. Stel de runtime-opties voor afdrukken in die nodig zijn om af te drukken naar een bestand.

   * Maak een `PrintedOutputOptionsSpec` object met de constructor ervan.
   * Geef het bestand op door een tekenreekswaarde toe te wijzen die de locatie en naam van het bestand vertegenwoordigt voor het `PrintedOutputOptionsSpec` gegevenslid van het `fileURI` object. Als u bijvoorbeeld wilt dat de uitvoerservice wordt afgedrukt naar een PostScript-bestand met de naam *MortgaugeForm.ps* in C:\Adobe, geeft u C:\\Adobe\MortgageForm.ps op.
   * Geef het aantal exemplaren op dat moet worden afgedrukt door een geheel-getalwaarde toe te wijzen die het aantal exemplaren aan de `PrintedOutputOptionsSpec` gegevensleden van het `copies` object vertegenwoordigt.

1. Druk de afdrukstroom naar een bestand af.

   Druk af naar een bestand door de methode van het `OutputServiceService` `generatePrintedOutput` object aan te roepen en de volgende waarden door te geven:

   * Een `PrintFormat` opsommingswaarde waarmee de indeling van de afdrukstroom wordt opgegeven die moet worden gemaakt. Als u bijvoorbeeld een PostScript-afdrukstroom wilt maken, geeft u door `PrintFormat.PostScript`.
   * Een tekenreekswaarde waarmee de naam van het formulierontwerp wordt opgegeven.
   * Een tekenreekswaarde die de locatie van verwante secundaire bestanden, zoals afbeeldingsbestanden, opgeeft.
   * Een tekenreekswaarde die de locatie aangeeft van het XDC-bestand dat moet worden gebruikt (u kunt doorgeven `null` als u het XDC-bestand hebt opgegeven dat moet worden gebruikt met het `PrintedOutputOptionsSpec` object).
   * Het `PrintedOutputOptionsSpec` object dat afdrukopties tijdens runtime bevat die zijn vereist om af te drukken naar een bestand.
   * Het `BLOB` object dat de XML-gegevensbron bevat die formuliergegevens bevat.
   * Een `BLOB` object dat door de `generatePDFOutput` methode is gevuld. De `generatePDFOutput` methode vult dit object met gegenereerde metagegevens die het document beschrijven. (Deze parameterwaarde is alleen vereist voor aanroepen van webservices.)
   * Een `BLOB` object dat door de `generatePDFOutput` methode is gevuld. De `generatePDFOutput` methode vult dit object met resultaatgegevens. (Deze parameterwaarde is alleen vereist voor aanroepen van webservices.)
   * Een `OutputResult` object dat de resultaten van de bewerking bevat. (Deze parameterwaarde is alleen vereist voor aanroepen van webservices.)

1. Haal de resultaten van de bewerking op.

   * Maak een `System.IO.FileStream` object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die een locatie van een XML-bestand vertegenwoordigt die resultaatgegevens bevat. Zorg ervoor dat de bestandsextensie XML is.
   * Maak een bytearray waarin de gegevensinhoud wordt opgeslagen van het `BLOB` object dat met resultaatgegevens is gevuld via de `OutputServiceService` methode van het `generatePDFOutput` object (de achtste parameter). Vul de bytearray met de waarde van het `BLOB` `MTOM` gegevenslid van het object.
   * Maak een `System.IO.BinaryWriter` object door de constructor ervan aan te roepen en het `System.IO.FileStream` object door te geven.
   * Schrijf de inhoud van de bytearray naar het XML-bestand door de methode van het `System.IO.BinaryWriter` `Write` object aan te roepen en de bytearray door te geven.

**Zie ook**

[Overzicht van de stappen](creating-document-output-streams.md#summary-of-steps)

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Afdrukstromen naar printers verzenden {#sending-print-streams-to-printers}

Met de service Uitvoer kunt u afdrukstreams zoals PostScript, Printer Control Language (PCL) of de volgende labelindelingen naar netwerkprinters verzenden:

* Zebra - ZPL
* Intermec, IPL
* Datamax - DPL
* TecToshiba - TPCL

Met de Output-service kunt u XML-gegevens samenvoegen met een formulierontwerp en het formulier uitvoeren als een afdrukstroom. U kunt bijvoorbeeld een PostScript-afdrukstroom maken en deze naar een netwerkprinter verzenden. In de volgende afbeelding ziet u hoe de uitvoerservice afdrukstreams naar netwerkprinters verzendt.

>[!NOTE]
>
>In deze sectie wordt een PostScript-afdrukstroom naar een netwerkprinter verzonden met behulp van het SharedPrinter-printerprotocol om te tonen hoe u een afdrukstream naar een netwerkprinter verzendt.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Output, zie de Verwijzing van de [Diensten voor AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary_of_steps-6}

Voer de volgende stappen uit om een afdrukstroom naar een netwerkprinter te verzenden:

1. Inclusief projectbestanden.
1. Maak een Output Client-object.
1. Verwijzen naar een XML-gegevensbron.
1. Uitvoeropties voor afdrukken instellen
1. Een af te drukken document ophalen.
1. Verzend het document naar een netwerkprinter.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u de proxybestanden opnemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-output-client.jar
* adobe-utilities.jar (vereist als AEM Forms worden geïmplementeerd op JBoss)
* jbossall-client.jar (vereist als AEM Forms worden geïmplementeerd op JBoss)

als AEM Forms worden geïmplementeerd op een ondersteunde J2EE-toepassingsserver die geen JBoss is, moet u de bestanden adobe-utilities.jar en jbossall-client.jar vervangen door JAR-bestanden die specifiek zijn voor de J2EE-toepassingsserver waarop AEM Forms worden geïmplementeerd.

**Een uitvoerclient-object maken**

Voordat u programmatisch een uitvoerservicebewerking kunt uitvoeren, maakt u een uitvoerservice-clientobject. Als u de Java API gebruikt, maakt u een `OutputClient` object. Als u de Output-webservice-API gebruikt, maakt u een `OutputServiceClient` object.

**Verwijzen naar een XML-gegevensbron**

Als u een document wilt afdrukken dat gegevens bevat, moet u verwijzen naar een XML-gegevensbron die XML-elementen bevat voor elk formulierveld dat u wilt vullen met gegevens. De naam van het XML-element moet overeenkomen met de veldnaam. Een XML-element wordt genegeerd als het niet overeenkomt met een formulierveld of als de naam van het XML-element niet overeenkomt met de veldnaam. Het is niet nodig de volgorde aan te passen waarin de XML-elementen worden weergegeven als alle XML-elementen zijn opgegeven.

**Uitvoeropties voor afdrukken instellen**

U kunt de runtime-opties instellen wanneer u een afdrukstroom naar een printer verzendt, inclusief de volgende opties:

* **Exemplaren**: Hier geeft u het aantal exemplaren op dat u naar de printer wilt verzenden. De standaardwaarde is 1.
* **Stapel**: Een optie XCI wordt geplaatst wanneer een nietmachine wordt gebruikt. Deze optie kan in het configuratiemodel door het belangrijkste element worden gespecificeerd en wordt gebruikt voor printers PS en PCL slechts.
* **OutputJog**: Er wordt een XCI-optie ingesteld wanneer uitvoerpagina&#39;s moeten worden samengevoegd (fysiek verschoven in de uitvoerlade). Deze optie geldt alleen voor PS- en PCL-printers.
* **OutputBin**: XCI-waarde die wordt gebruikt om het afdrukstuurprogramma in staat te stellen de juiste uitvoerbak te selecteren.

>[!NOTE]
>
>Zie de `PrintedOutputOptionsSpec` klasseverwijzing voor informatie over alle runtime-opties die u kunt instellen.

**Een af te drukken document ophalen**

Haal een afdrukstroom op die u naar een printer wilt verzenden. U kunt bijvoorbeeld een PostScript-bestand ophalen en naar een printer verzenden.

U kunt een PDF-bestand verzenden als uw printer PDF-bestanden ondersteunt. Een probleem bij het verzenden van een PDF-document naar een printer is echter dat elke printerfabrikant een andere implementatie van de PDF-interpreter heeft. Sommige afdrukfabrikanten gebruiken dus Adobe PDF-interpretatie, maar deze is afhankelijk van de printer. Andere printers hebben een eigen PDF-interpreter. Hierdoor kunnen de afdrukresultaten afwijken.

Een andere beperking bij het verzenden van een PDF-document naar een printer is dat het alleen wordt afgedrukt. de printer heeft alleen toegang tot duplex, selectie van papierlade en nieten, via de printerinstellingen.

Als u een document wilt ophalen om af te drukken, gebruikt u de `generatePrintedOutput` methode. In de volgende tabel worden inhoudstypen aangegeven die voor een bepaalde afdrukstroom zijn ingesteld wanneer de `generatePrintedOutput` methode wordt gebruikt.

<table>
 <thead>
  <tr>
   <th><p>Afdrukindeling </p></th>
   <th><p>Beschrijving</p></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p>DPL </p></td>
   <td><p>Maakt standaard een dpl203.xdc of aangepaste xdc-uitvoerstream.</p></td>
  </tr>
  <tr>
   <td><p>DPL300DPI </p></td>
   <td><p>Maakt een DPL 300 DPI-uitvoerstream.</p></td>
  </tr>
  <tr>
   <td><p>DPL406DPI </p></td>
   <td><p>Maakt een DPL 400 DPI-uitvoerstream.</p></td>
  </tr>
  <tr>
   <td><p>DPL600DPI </p></td>
   <td><p>Maakt een DPL 600 DPI-uitvoerstream.</p></td>
  </tr>
  <tr>
   <td><p>GenericColorPCL </p></td>
   <td><p>Hiermee wordt een algemene PCL-uitvoerstream (5c) van kleur gemaakt.</p></td>
  </tr>
  <tr>
   <td><p>GenericPSLevel3 </p></td>
   <td><p>Hiermee wordt een generieke uitvoerstream van PostScript Level 3 gemaakt.</p></td>
  </tr>
  <tr>
   <td><p>IPL </p></td>
   <td><p>Maakt een aangepaste IPL-uitvoerstream.</p></td>
  </tr>
  <tr>
   <td><p>IPL300DPI </p></td>
   <td><p>Maakt een IPL 300 DPI-uitvoerstream.</p></td>
  </tr>
  <tr>
   <td><p>IPL400DPI </p></td>
   <td><p>Maakt een IPL 400 DPI-uitvoerstream.</p></td>
  </tr>
  <tr>
   <td><p>PCL </p></td>
   <td><p>Hiermee wordt een generieke monochrome PCL-uitvoerstream (5e) gemaakt.</p></td>
  </tr>
  <tr>
   <td><p>PostScript </p></td>
   <td><p>Hiermee wordt een generieke uitvoerstream van PostScript Level 2 gemaakt.</p></td>
  </tr>
  <tr>
   <td><p>TPCL </p></td>
   <td><p>Maakt een aangepaste TPCL-uitvoerstream.</p></td>
  </tr>
  <tr>
   <td><p>TPCL305DPI </p></td>
   <td><p>Maakt een TPCL 305 DPI-uitvoerstream.</p></td>
  </tr>
  <tr>
   <td><p>TPCL600DPI </p></td>
   <td><p>Maakt een TPCL 600 DPI-uitvoerstream.</p></td>
  </tr>
  <tr>
   <td><p>ZPL </p></td>
   <td><p>Maakt een ZPL 203 DPI-uitvoerstream.</p></td>
  </tr>
  <tr>
   <td><p>ZPL300DPI </p></td>
   <td><p>Maakt een ZPL 300 DPI-uitvoerstroom.</p></td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>U kunt ook een afdrukstroom naar een printer verzenden met de `generatePrintedOutput2` methode. De snelle start die echter wordt gekoppeld aan de sectie Afdrukstromen naar printers verzenden, gebruikt de `generatePrintedOutput` methode.

**De afdrukstroom naar een netwerkprinter verzenden**

Nadat u een document hebt opgehaald om af te drukken, kunt u de service Uitvoer inschakelen, waardoor een afdrukstroom naar een netwerkprinter wordt verzonden. Als u de printer wilt vinden in de uitvoerservice, moet u zowel de afdrukserver als de printernaam opgeven. Daarnaast moet u ook het afdrukprotocol opgeven.

>[!NOTE]
>
>Als PDFG op de vormenserver en de serverlooppas op de Server 2008 van Vensters wordt geïnstalleerd, kunt u niet het bezit SharedPrinter gebruiken. In deze situatie, gebruik een verschillend printerprotocol.

>[!NOTE]
>
>Als u een netwerkprinter gebruikt en het toegangsmechanisme SharedPrinter is, moet u het volledige netwerkpad van de printer opgeven.Een afdrukstroom naar een netwerkprinter verzenden met de Java API

Een afdrukstream naar een netwerkprinter verzenden met de Output API (Java):

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-output-client.jar, op in het klassenpad van uw Java-project.

1. Een uitvoerclient-object maken

   * Maak een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Maak een `OutputClient` object door de constructor ervan te gebruiken en het `ServiceClientFactory` object door te geven.

1. Verwijzen naar een XML-gegevensbron

   * Maak een `java.io.FileInputStream` object dat staat voor de XML-gegevensbron die wordt gebruikt om het document te vullen met de constructor ervan en geef een tekenreekswaarde door die de locatie van het XML-bestand opgeeft.
   * Maak een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en het `java.io.FileInputStream` object door te geven.

1. Uitvoeropties voor afdrukken instellen

   Maak een `PrintedOutputOptionsSpec` object dat de afdrukopties bij uitvoering vertegenwoordigt. U kunt bijvoorbeeld het aantal exemplaren opgeven dat moet worden afgedrukt door de `PrintedOutputOptionsSpec` methode van het `setCopies` object aan te roepen.

   >[!NOTE]
   >
   >U kunt de pagineringswaarde niet instellen met de `PrintedOutputOptionsSpec` methode van het `setPagination` object als u een ZPL-afdrukstroom genereert. Evenzo kunt u de volgende opties niet instellen voor een ZPL-afdrukstroom: OutputJog, PageOffset en Stapel. De `setPagination` methode is niet geldig voor het genereren van PostScript. Het is alleen geldig voor PCL-generatie.

1. Een af te drukken document ophalen

   * Haal een document op dat u wilt afdrukken door de methode van het `OutputClient` `generatePrintedOutput` object aan te roepen en de volgende waarden door te geven:

      * Een `PrintFormat` opsommingswaarde waarmee de afdrukstroom wordt opgegeven. Als u bijvoorbeeld een PostScript-afdrukstroom wilt maken, geeft u door `PrintFormat.PostScript`.
      * Een tekenreekswaarde waarmee de naam van het formulierontwerp wordt opgegeven.
      * Een tekenreekswaarde die de locatie van verwante secundaire bestanden opgeeft, zoals afbeeldingsbestanden.
      * Een tekenreekswaarde die de locatie aangeeft van het XDC-bestand dat moet worden gebruikt.
      * Het `PrintedOutputOptionsSpec` object dat uitvoeringsopties bevat die vereist zijn om af te drukken naar een bestand.
      * Het `com.adobe.idp.Document` object dat de XML-gegevensbron vertegenwoordigt die formuliergegevens bevat die met het formulierontwerp moeten worden samengevoegd.

      Deze methode retourneert een `OutputResult` object dat de resultaten van de bewerking bevat.

   * Maak een `com.adobe.idp.Document` object dat u naar de printer wilt verzenden door de `OutputResult` methode van het `getGeneratedDoc` object aan te roepen. Deze methode retourneert een `com.adobe.idp.Document` object.


1. De afdrukstroom naar een netwerkprinter verzenden

   Verzend de afdrukstroom naar een netwerkprinter door de methode van het `OutputClient` `sendToPrinter` object aan te roepen en de volgende waarden door te geven:

   * Een `com.adobe.idp.Document` object dat staat voor de afdrukstream die naar de printer moet worden verzonden.
   * Een `PrinterProtocol` opsommingswaarde die het te gebruiken printerprotocol aangeeft. Als u bijvoorbeeld het SharedPrinter-protocol wilt opgeven, geeft u door `PrinterProtocol.SharedPrinter`.
   * Een tekenreekswaarde die de naam van de afdrukserver opgeeft. Wanneer bijvoorbeeld de naam van de afdrukserver PrintServer1 is, geeft u door `\\\PrintSever1`.
   * Een tekenreekswaarde die de naam van de printer opgeeft. Als de naam van de printer bijvoorbeeld Printer1 is, geeft u door `\\\PrintSever1\Printer1`.

   >[!NOTE]
   >
   >De `sendToPrinter` methode is toegevoegd aan de AEM Forms API in versie 8.2.1.

### Een afdrukstream naar een printer verzenden met de webservice-API {#send-a-print-stream-to-a-printer-using-the-web-service-api}

Een afdrukstroom naar een netwerkprinter verzenden met de Output API (webservice):

1. Inclusief projectbestanden.

   Creeer een project van Microsoft .NET dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/OutputService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een Output Client-object.

   * Maak een `OutputServiceClient` object met de standaardconstructor.
   * Maak een `OutputServiceClient.Endpoint.Address` object met de `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de service AEM Forms (bijvoorbeeld `http://localhost:8080/soap/services/OutputService?blob=mtom`.) U hoeft het `lc_version` kenmerk niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt. Geef echter op `?blob=mtom` om MTOM te gebruiken.
   * Maak een `System.ServiceModel.BasicHttpBinding` object door de waarde van het `OutputServiceClient.Endpoint.Binding` veld op te halen. Kiezen naar de geretourneerde waarde `BasicHttpBinding`.
   * Stel het `System.ServiceModel.BasicHttpBinding` veld van het `MessageEncoding` object in op `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam voor AEM-formulieren toe aan het veld `OutputServiceClient.ClientCredentials.UserName.UserName`.
      * Wijs de bijbehorende wachtwoordwaarde aan het veld toe `OutputServiceClient.ClientCredentials.UserName.Password`.
      * Wijs de constante waarde toe `HttpClientCredentialType.Basic` aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Wijs de constante waarde toe `BasicHttpSecurityMode.TransportCredentialOnly` aan het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Verwijzen naar een XML-gegevensbron.

   * Maak een `BLOB` object met de constructor ervan. Het `BLOB` object wordt gebruikt om formuliergegevens op te slaan.
   * Maak een `System.IO.FileStream` object door de constructor ervan aan te roepen. Geef een tekenreekswaarde door die de locatie aangeeft van het XML-bestand dat formuliergegevens bevat.
   * Maak een bytearray waarin de inhoud van het `System.IO.FileStream` object wordt opgeslagen. Bepaal de lengte van de bytearray door de `System.IO.FileStream` eigenschap van het `Length` object op te halen.
   * Vul de bytearray met streamgegevens door de methode van het `System.IO.FileStream` `Read` object aan te roepen en de bytearray, de startpositie en de lengte van de stream door te geven om te lezen.
   * Vul het `BLOB` object door het `MTOM` veld ervan toe te wijzen met de inhoud van de bytearray.

1. Stel opties voor het uitvoeren van de afdruk in.

   Maak een `PrintedOutputOptionsSpec` object met de constructor ervan. U kunt bijvoorbeeld het aantal exemplaren opgeven dat moet worden afgedrukt door een geheel-getalwaarde toe te wijzen die het aantal exemplaren voor het `PrintedOutputOptionsSpec` gegevenslid van het `copies` object vertegenwoordigt.

   >[!NOTE]
   >
   >U kunt de pagineringswaarde niet instellen met het `PrintedOutputOptionsSpec` gegevenslid van het `pagination` object als u een ZPL-afdrukstroom genereert. Evenzo kunt u de volgende opties niet instellen voor een ZPL-afdrukstroom: OutputJog, PageOffset en Stapel. Het `pagination` gegevenslid is niet geldig voor het genereren van PostScript. Het is alleen geldig voor PCL-generatie.

1. Een af te drukken document ophalen.

   * Haal een document op dat u wilt afdrukken door de methode van het `OutputServiceService` `generatePrintedOutput` object aan te roepen en de volgende waarden door te geven:

      * Een `PrintFormat` opsommingswaarde waarmee de afdrukstroom wordt opgegeven. Als u bijvoorbeeld een PostScript-afdrukstroom wilt maken, geeft u door `PrintFormat.PostScript`.
      * Een tekenreekswaarde waarmee de naam van het formulierontwerp wordt opgegeven.
      * Een tekenreekswaarde die de locatie van verwante secundaire bestanden opgeeft, zoals afbeeldingsbestanden.
      * Een tekenreekswaarde die de locatie aangeeft van het XDC-bestand dat moet worden gebruikt.
      * Het `PrintedOutputOptionsSpec` object dat afdrukopties tijdens runtime bevat die worden gebruikt wanneer een afdrukstroom naar een netwerkprinter wordt verzonden.
      * Het `BLOB` object dat de XML-gegevensbron bevat die formuliergegevens bevat.
      * Een `BLOB` object dat door de `generatePrintedOutput` methode is gevuld. De `generatePrintedOutput` methode vult dit object met gegenereerde metagegevens die het document beschrijven. (Deze parameterwaarde is alleen vereist voor aanroepen van webservices.)
      * Een `BLOB` object dat door de `generatePrintedOutput` methode is gevuld. De `generatePrintedOutput` methode vult dit object met resultaatgegevens. (Deze parameterwaarde is alleen vereist voor aanroepen van webservices.)
      * Een `OutputResult` object dat de resultaten van de bewerking bevat. (Deze parameterwaarde is alleen vereist voor aanroepen van webservices.)
   * Maak een `BLOB` object dat u naar de printer wilt verzenden door de waarde van de `OutputResult` methode van het `generatedDoc` object op te halen. Deze methode retourneert een `BLOB` object dat PostScript-gegevens bevat die door de `generatePrintedOutput` methode worden geretourneerd.


1. Verzend de afdrukstroom naar een netwerkprinter.

   Verzend de afdrukstroom naar een netwerkprinter door de methode van het `OutputClient` `sendToPrinter` object aan te roepen en de volgende waarden door te geven:

   * Een `BLOB` object dat staat voor de afdrukstream die naar de printer moet worden verzonden.
   * Een `PrinterProtocol` opsommingswaarde die het te gebruiken printerprotocol aangeeft. Als u bijvoorbeeld het SharedPrinter-protocol wilt opgeven, geeft u door `PrinterProtocol.SharedPrinter`.
   * Een `bool` waarde die opgeeft of de vorige parameterwaarde moet worden gebruikt. Geef de waarde door `true`. (Deze parameterwaarde is alleen vereist voor aanroepen van webservices.)
   * Een tekenreekswaarde die de naam van de afdrukserver opgeeft. Wanneer bijvoorbeeld wordt aangenomen dat de naam van de afdrukserver PrintServer1 is, geeft u door `\\\PrintSever1`.
   * Een tekenreekswaarde die de naam van de printer opgeeft. Als bijvoorbeeld de naam van de printer Printer1 is, geeft u door `\\\PrintSever1\Printer1`.

   >[!NOTE]
   >
   >De `sendToPrinter` methode is toegevoegd aan de AEM Forms API in versie 8.2.1.

## Meerdere uitvoerbestanden maken {#creating-multiple-output-files}

Met de service Uitvoer kunt u aparte documenten maken voor elke record in een XML-gegevensbron of één bestand dat alle records bevat (deze functionaliteit is de standaardinstelling). Stel bijvoorbeeld dat tien records zich in een XML-gegevensbron bevinden en dat u de Output-service opgeeft om voor elke record afzonderlijke PDF-documenten (of andere uitvoertypen) te maken met de Output Service API. Als gevolg hiervan genereert de uitvoerservice tien PDF-documenten. (In plaats van documenten te maken, kunt u meerdere afdrukstromen naar een printer verzenden.)

In de volgende afbeelding ziet u ook hoe de uitvoerservice een XML-gegevensbestand verwerkt dat meerdere records bevat. Stel echter dat u de uitvoerservice opgeeft één PDF-document te maken dat alle gegevensrecords bevat. In deze situatie genereert de uitvoerservice één document dat alle records bevat.

In de volgende afbeelding ziet u hoe de uitvoerservice een XML-gegevensbestand verwerkt dat meerdere records bevat. Stel dat u de uitvoerservice opgeeft een afzonderlijk PDF-document te maken voor elke gegevensrecord. In dit geval genereert de uitvoerservice een afzonderlijk PDF-document voor elke gegevensrecord.

![cm_outputbatchmany](assets/cm_outputbatchmany.png)

De volgende XML-gegevens laten een voorbeeld zien van een gegevensbestand dat drie gegevensrecords bevat.

```xml
 <?xml version="1.0" encoding="UTF-8"?>
 <batch>
 <LoanRecord>
     <mortgageAmount>500000</mortgageAmount>
     <lastName>Blue</lastName>
     <firstName>Tony</firstName>
     <SSN>555666777</SSN>
     <PositionTitle>Product Manager</PositionTitle>
     <Address>555 No Where Dr</Address>
     <City>New York</City>
     <StateProv>New York</StateProv>
     <ZipCode>51256</ZipCode>
     <Email>TBlue@NoMailServer.com</Email>
     <PhoneNum>555-7418</PhoneNum>
     <FaxNum>555-9981</FaxNum>
     <Description>Buy a home</Description>
 </LoanRecord>
 <LoanRecord>
     <mortgageAmount>300000</mortgageAmount>
     <lastName>White</lastName>
     <firstName>Sam</firstName>
     <SSN>555666222</SSN>
     <PositionTitle>Program Manager</PositionTitle>
     <Address>557 No Where Dr</Address>
     <City>New York</City>
     <StateProv>New York</StateProv>
     <ZipCode>51256</ZipCode>
     <Email>SWhite@NoMailServer.com</Email>
     <PhoneNum>555-7445</PhoneNum>
     <FaxNum>555-9986</FaxNum>
     <Description>Buy a home</Description>
 </LoanRecord>
 <LoanRecord>
     <mortgageAmount>700000</mortgageAmount>
     <lastName>Green</lastName>
     <firstName>Steve</firstName>
     <SSN>55566688</SSN>
     <PositionTitle>Project Manager</PositionTitle>
     <Address>445 No Where Dr</Address>
     <City>New York</City>
     <StateProv>New York</StateProv>
     <ZipCode>51256</ZipCode>
     <Email>SGreeb@NoMailServer.com</Email>
     <PhoneNum>555-2211</PhoneNum>
     <FaxNum>555-2221</FaxNum>
     <Description>Buy a home</Description>
 </LoanRecord>
 </batch>
```

Het XML-element dat elk gegevensrecord start en beëindigt, is `LoanRecord`. Naar dit XML-element wordt verwezen door de toepassingslogica die meerdere bestanden genereert.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Output, zie de Verwijzing van de [Diensten voor AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary_of_steps-7}

Voer de volgende stappen uit om meerdere PDF-bestanden te maken op basis van een XML-gegevensbron:

1. Inclusief projectbestanden.
1. Maak een Output Client-object.
1. Verwijzen naar een XML-gegevensbron.
1. Stel PDF-runtime-opties in.
1. Stel renderingopties in.
1. Genereer meerdere PDF-bestanden.
1. Haal de resultaten van de bewerking op.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u de proxybestanden opnemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-output-client.jar
* adobe-utilities.jar (vereist als AEM Forms worden geïmplementeerd op JBoss)
* jbossall-client.jar (vereist als AEM Forms worden geïmplementeerd op JBoss)

als AEM Forms worden geïmplementeerd op een ondersteunde J2EE-toepassingsserver die geen JBoss is, moet u de bestanden adobe-utilities.jar en jbossall-client.jar vervangen door JAR-bestanden die specifiek zijn voor de J2EE-toepassingsserver waarop AEM Forms worden geïmplementeerd.

**Een uitvoerclient-object maken**

Voordat u programmatisch een uitvoerservicebewerking kunt uitvoeren, moet u een uitvoerservice-clientobject maken. Als u de Java API gebruikt, maakt u een `OutputClient` object. Als u de Output-webservice-API gebruikt, maakt u een `OutputServiceService` object.

**Verwijzen naar een XML-gegevensbron**

Verwijs naar een gegevensbron van XML die veelvoudige verslagen bevat. Een XML-element moet worden gebruikt om de gegevensrecords van elkaar te scheiden. In het voorbeeld-XML-gegevensbron dat eerder in deze sectie wordt weergegeven, wordt bijvoorbeeld het XML-element dat gegevensrecords scheidt, benoemd `LoanRecord`.

Een XML-element moet bestaan voor elk formulierveld dat u wilt vullen met gegevens. De naam van het XML-element moet overeenkomen met de veldnaam. Een XML-element wordt genegeerd als het niet overeenkomt met een formulierveld of als de naam van het XML-element niet overeenkomt met de veldnaam. Het is niet nodig de volgorde aan te passen waarin de XML-elementen worden weergegeven als alle XML-elementen zijn opgegeven.

**Opties voor PDF-runtime instellen**

U moet de volgende runtime opties voor de dienst van de Output plaatsen om veelvoudige dossiers tot stand te brengen die op een gegevensbron van XML worden gebaseerd:

* **Veel bestanden**: Hiermee wordt opgegeven of de service Uitvoer één document of meerdere documenten maakt. U kunt waar of onwaar opgeven. Geef true op als u een afzonderlijk document wilt maken voor elke gegevensrecord in de XML-gegevensbron.
* **Bestands-URI**: Hier geeft u de locatie op van de bestanden die de uitvoerservice genereert. Stel bijvoorbeeld dat u C:\\Adobe\forms\Loan.pdf opgeeft. In dit geval maakt de service Uitvoer een bestand met de naam Loan.pdf en wordt het bestand in de map C:\\Adobe\forms folder geplaatst. Als er meerdere bestanden zijn, zijn de bestandsnamen Loan0001.pdf, Loan0002.pdf, Loan0003.pdf enzovoort. Als u een bestandslocatie opgeeft, worden de bestanden op de server geplaatst, niet op de clientcomputer.
* **Recordnaam**: Hiermee wordt de naam van het XML-element opgegeven in de gegevensbron die de gegevensrecords scheidt. In het voorbeeld-XML-gegevensbron dat eerder in deze sectie wordt weergegeven, wordt bijvoorbeeld het XML-element dat gegevensrecords scheidt, aangeroepen `LoanRecord`. (In plaats van de runtime voor opnamen in te stellen, kunt u het niveau opnemen instellen door er een numerieke waarde aan toe te wijzen die het elementniveau aangeeft dat gegevensrecords bevat. U kunt echter alleen de recordnaam of het recordniveau instellen. U kunt niet beide waarden instellen.)

**Renderopties tijdens runtime instellen**

Tijdens het maken van meerdere bestanden kunt u opties voor het renderen tijdens runtime instellen. Hoewel deze opties niet vereist zijn (in tegenstelling tot uitvoeropties, die vereist zijn), kunt u taken uitvoeren zoals het verbeteren van de prestaties van de uitvoerservice. U kunt bijvoorbeeld het formulierontwerp dat de uitvoerservice gebruikt in cache plaatsen om de prestaties te verbeteren.

Wanneer de dienst van de Output partijverslagen verwerkt, leest het gegevens die veelvoudige verslagen op een stijgende manier bevatten. Dat wil zeggen dat de Output-service de gegevens in het geheugen leest en de gegevens vrijgeeft terwijl de batch met records wordt verwerkt. De uitvoerservice laadt gegevens incrementeel wanneer een van de twee uitvoeringsopties is ingesteld. Als u de runtime van de Naam van het Verslag optie plaatst, leest de dienst van de Output gegevens op een stijgende manier. Op dezelfde manier, als u de runtime van het Niveau van het Verslag optie aan 2 of groter plaatst, leest de dienst van de Output gegevens op een stijgende manier.

U kunt bepalen of de dienst van de Output het stijgende laden door de `PDFOutputOptionsSpec` of `PrintedOutputOptionSpec` methode van de `setLazyLoading` objecten uit te voeren. U kunt de waarde doorgeven `false` aan deze methode waarbij incrementele belasting wordt uitgeschakeld.

**Meerdere PDF-bestanden genereren**

Nadat u naar een geldige XML-gegevensbron verwijst die meerdere gegevensrecords bevat en runtime-opties instelt, kunt u de uitvoerservice aanroepen, waardoor er meerdere bestanden worden gegenereerd. Wanneer u meerdere records genereert, wordt de `OutputResult` methode van het object geretourneerd `getGeneratedDoc` `null`.

**De resultaten van de bewerking ophalen**

Nadat de dienst van de Output een verrichting uitvoert, keert het de gegevens van XML terug die specificeren of de verrichting succesvol was. De volgende XML wordt geretourneerd door de service Uitvoer. In deze situatie genereerde de uitvoerservice 42 documenten.

```xml
 <?xml version="1.0" encoding="UTF-8"?>
 <printResult>
 <status>0</status>
 <requestId>4ad85f9e2</requestId>
 <context/>
 <messages>
 <message>Printed all 42 records successfully.</message>
 </messages>
 <printSpec>
 <input>
 <validated>true</validated>
 <dataFile recordIdField="" recordLevel="0" recordName="LoanRecord"/>
 <sniffRules lookAhead="300"/>
 <formDesign>Loan.xdp</formDesign>
 <contentRoot>C:\Adobe</contentRoot>
 <metadata-spec record="false"/>
 </input>
 <output>
 <format>PDF</format>
 <fileURI>C:\Adobe\forms\Loan.pdf</fileURI>
 <optionString>cacheenabled=true&padebug=false&linearpdf=false&pdfarevisionnumber=1&pdfaconformance=A&taggedpdf=false&TransactionTimeOut=180</optionString>
 <waitForResponse>true</waitForResponse>
 <outputStream>multiple</outputStream>
 </output>
 </printSpec>
 </printResult>
```

**Zie ook**

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Uitvoerservice-API - Snel starten](/help/forms/developing/output-service-java-api-quick.md#output-service-java-api-quick-start-soap)

### Meerdere PDF-bestanden maken met de Java API {#create-multiple-pdf-files-using-the-java-api}

Meerdere PDF-bestanden maken met de Output API (Java):

1. Inclusief projectbestanden&quot;

   Neem client-JAR-bestanden, zoals adobe-output-client.jar, op in het klassenpad van uw Java-project. .

1. Een uitvoerclient-object maken

   * Maak een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Maak een `OutputClient` object door de constructor ervan te gebruiken en het `ServiceClientFactory` object door te geven.

1. Verwijzen naar een XML-gegevensbron

   * Maak een `java.io.FileInputStream` object dat de XML-gegevensbron vertegenwoordigt die meerdere records bevat door de constructor ervan te gebruiken en een tekenreekswaarde door te geven die de locatie van het XML-bestand aangeeft.
   * Maak een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en het `java.io.FileInputStream` object door te geven.

1. Opties voor PDF-runtime instellen

   * Maak een `PDFOutputOptionsSpec` object met de constructor ervan.
   * Stel de optie Veel bestanden in door de `PDFOutputOptionsSpec` methode van het `setGenerateManyFiles` object aan te roepen. Geef bijvoorbeeld de waarde door `true` om de uitvoerservice op te dragen een afzonderlijk PDF-bestand te maken voor elke record in de XML-gegevensbron. (Als u doorgeeft `false`, genereert de service Uitvoer één PDF-document dat alle records bevat.)
   * Stel de optie File URI in door de methode van het `PDFOutputOptionsSpec` `setFileUri` object aan te roepen en een tekenreekswaarde door te geven die de locatie aangeeft van de bestanden die de service Output genereert. De optie File URI is relatief ten opzichte van de J2EE-toepassingsserver die AEM Forms host, niet ten opzichte van de clientcomputer.
   * Stel de optie Naam record in door de `OutputOptionsSpec` methode van het `setRecordName` object aan te roepen en een tekenreekswaarde door te geven die de naam van het XML-element opgeeft in de gegevensbron die de gegevensrecords scheidt. (Neem bijvoorbeeld de XML-gegevensbron die eerder in deze sectie wordt weergegeven. De naam van het XML-element dat gegevensrecords scheidt, is LoanRecord.)

1. Renderopties tijdens runtime instellen

   * Maak een `RenderOptionsSpec` object met de constructor ervan.
   * Plaats het formulierontwerp in de cache om de prestaties van de uitvoerservice te verbeteren door het `RenderOptionsSpec` object aan te roepen `setCacheEnabled` en de `Boolean` waarde `true`door te geven.

1. Meerdere PDF-bestanden genereren

   Genereer meerdere PDF-bestanden door de methode van het `OutputClient` `generatePDFOutput` object aan te roepen en de volgende waarden door te geven:

   * Een `TransformationFormat` opsommingswaarde. Geef op om een PDF-document te genereren. `TransformationFormat.PDF`
   * Een tekenreekswaarde waarmee de naam van het formulierontwerp wordt opgegeven.
   * Een tekenreekswaarde die de hoofdmap van de inhoud opgeeft waar het formulierontwerp zich bevindt.
   * Een `PDFOutputOptionsSpec` object dat PDF-runtime-opties bevat.
   * Een `RenderOptionsSpec` object dat renderingopties bevat.
   * Het `com.adobe.idp.Document` object dat de XML-gegevensbron bevat die gegevens bevat die met het formulierontwerp moeten worden samengevoegd.

   De `generatePDFOutput` methode retourneert een `OutputResult` object dat de resultaten van de bewerking bevat.

1. De resultaten van de bewerking ophalen

   * Maak een `java.io.File` object dat een XML-bestand vertegenwoordigt dat de resultaten van de `generatePDFOutput` methode zal bevatten. Controleer of de bestandsnaamextensie .xml is.
   * Roep de `com.adobe.idp.Document` methode van het `copyToFile` object aan om de inhoud van het `com.adobe.idp.Document` object naar het bestand te kopiëren (zorg dat u het `com.adobe.idp.Document` object gebruikt dat door de `applyUsageRights` methode is geretourneerd).

**Zie ook**

[Overzicht van de stappen](creating-document-output-streams.md#summary-of-steps)

[Snel starten (EJB-modus): Meerdere PDF-bestanden maken met de Java API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-multiple-pdf-files-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Meerdere PDF-bestanden maken met de webservice-API {#create-multiple-pdf-files-using-the-web-service-api}

Meerdere PDF-bestanden maken met de Output API (webservice):

1. Inclusief projectbestanden.

   Creeer een project van Microsoft .NET dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/OutputService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een Output Client-object.

   * Maak een `OutputServiceClient` object met de standaardconstructor.
   * Maak een `OutputServiceClient.Endpoint.Address` object met de `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de service AEM Forms (bijvoorbeeld `http://localhost:8080/soap/services/OutputService?blob=mtom`.) U hoeft het `lc_version` kenmerk niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt. Geef echter op `?blob=mtom` om MTOM te gebruiken.
   * Maak een `System.ServiceModel.BasicHttpBinding` object door de waarde van het `OutputServiceClient.Endpoint.Binding` veld op te halen. Kiezen naar de geretourneerde waarde `BasicHttpBinding`.
   * Stel het `System.ServiceModel.BasicHttpBinding` veld van het `MessageEncoding` object in op `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam voor AEM-formulieren toe aan het veld `OutputServiceClient.ClientCredentials.UserName.UserName`.
      * Wijs de bijbehorende wachtwoordwaarde aan het veld toe `OutputServiceClient.ClientCredentials.UserName.Password`.
      * Wijs de constante waarde toe `HttpClientCredentialType.Basic` aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Wijs de constante waarde toe `BasicHttpSecurityMode.TransportCredentialOnly` aan het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Verwijzen naar een XML-gegevensbron.

   * Maak een `BLOB` object met de constructor ervan. Het `BLOB` object wordt gebruikt om formuliergegevens op te slaan die meerdere records bevatten.
   * Maak een `System.IO.FileStream` object door de constructor ervan aan te roepen. Geef een tekenreekswaarde door die de bestandslocatie vertegenwoordigt van het XML-bestand dat meerdere records bevat.
   * Maak een bytearray waarin de inhoud van het `System.IO.FileStream` object wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` eigenschap van het `Length` object op te halen.
   * Vul de bytearray met streamgegevens door de methode van het `System.IO.FileStream` `Read` object aan te roepen en de bytearray, de startpositie en de lengte van de stream door te geven om te lezen.
   * Vul het `BLOB` object door het `MTOM` veld ervan toe te wijzen met de inhoud van de bytearray.

1. Stel PDF-runtime-opties in.

   * Maak een `PDFOutputOptionsSpec` object met de constructor ervan.
   * Stel de optie Vele bestanden in door een Booleaanse waarde toe te wijzen aan het `OutputOptionsSpec` `generateManyFiles` gegevenslid van het object. Wijs bijvoorbeeld de waarde `true` aan dit gegevenslid toe om de Output-service op te dragen een afzonderlijk PDF-bestand te maken voor elke record in de XML-gegevensbron. (Als u dit gegevenslid toewijst, genereert de service Uitvoer één PDF die alle records bevat.) `false`
   * Stel de bestands-URI-optie in door een tekenreekswaarde toe te wijzen die de locatie aangeeft van het bestand of de bestanden die de uitvoerservice genereert voor het `OutputOptionsSpec` gegevenslid van het `fileURI` object. De optie File URI is relatief ten opzichte van de J2EE-toepassingsserver die AEM Forms host, niet ten opzichte van de clientcomputer.
   * Stel de recordnaamoptie in door een tekenreekswaarde toe te wijzen die de naam van het XML-element in de gegevensbron opgeeft die de gegevensrecords scheidt van het `OutputOptionsSpec` gegevenslid van het `recordName` object.
   * Stel de optie Kopiëren in door een geheel-getalwaarde toe te wijzen die het aantal exemplaren opgeeft dat de service Output genereert voor het `OutputOptionsSpec` gegevenslid van het `copies` object.

1. Stel renderingopties in.

   * Maak een `RenderOptionsSpec` object met de constructor ervan.
   * Plaats het formulierontwerp in de cache om de prestaties van de Output-service te verbeteren door de waarde toe te wijzen `true` aan het `RenderOptionsSpec` gegevenslid van het `cacheEnabled` object.

1. Genereer meerdere PDF-bestanden.

   Maak meerdere PDF-bestanden door de `OutputServiceService` methode van het `generatePDFOutput`object aan te roepen en de volgende waarden door te geven:

   * Een opsommingswaarde van TransformationFormat. Geef op om een PDF-document te genereren. `TransformationFormat.PDF`
   * Een tekenreekswaarde waarmee de naam van het formulierontwerp wordt opgegeven.
   * Een tekenreekswaarde die de hoofdmap van de inhoud opgeeft waar het formulierontwerp zich bevindt.
   * Een `PDFOutputOptionsSpec` object dat PDF-runtime-opties bevat.
   * Een `RenderOptionsSpec` object dat renderingopties bevat.
   * Het `BLOB` object dat de XML-gegevensbron bevat die gegevens bevat die met het formulierontwerp moeten worden samengevoegd.
   * Een `BLOB` object dat door de `generatePDFOutput` methode is gevuld. De `generatePDFOutput` methode vult dit object met gegenereerde metagegevens die het document beschrijven.
   * Een `BLOB` object dat door de `generatePDFOutput` methode is gevuld. De `generatePDFOutput` methode vult dit object met resultaatgegevens.
   * Een `OutputResult` object dat de resultaten van de bewerking bevat.

1. De resultaten van de bewerking ophalen

   * Maak een `System.IO.FileStream` object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die een locatie van een XML-bestand vertegenwoordigt die resultaatgegevens bevat. Controleer of de bestandsnaamextensie .xml is.
   * Maak een bytearray waarin de gegevensinhoud wordt opgeslagen van het `BLOB` object dat met resultaatgegevens is gevuld via de `OutputServiceService` methode van het `generatePDFOutput` object (de achtste parameter). Vul de bytearray met de waarde van het `BLOB` `binaryData` gegevenslid van het object.
   * Maak een `System.IO.BinaryWriter` object door de constructor ervan aan te roepen en het `System.IO.FileStream` object door te geven.
   * Schrijf de inhoud van de bytearray naar het XML-bestand door de methode van het `System.IO.BinaryWriter` `Write` object aan te roepen en de bytearray door te geven.

**Zie ook**

[Overzicht van de stappen](creating-document-output-streams.md#summary-of-steps)

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Zoekregels maken {#creating-search-rules}

U kunt zoekregels maken die ertoe leiden dat de uitvoerservice invoergegevens controleert en verschillende formulierontwerpen gebruikt op basis van de gegevensinhoud om uitvoer te genereren. Als de *teksthypotheek* zich bijvoorbeeld binnen de invoergegevens bevindt, kan de Output-service een formulierontwerp gebruiken met de naam Mortgauge.xdp. Op dezelfde manier geldt dat als de tekst in de *tekstauto* zich in de invoergegevens bevindt, de uitvoerservice een formulierontwerp kan gebruiken dat is opgeslagen als AutomobileLoan.xdp. Hoewel de service Uitvoer verschillende uitvoertypen kan genereren, wordt er in deze sectie van uitgegaan dat de service Uitvoer een PDF-bestand genereert. In het volgende diagram ziet u de service Uitvoer die een PDF-bestand genereert door een XML-gegevensbestand te verwerken en een van de vele formulierontwerpen te gebruiken.

Daarnaast kan de Output-service documentpakketten genereren, waarbij de gegevensset meerdere records bevat en elke record overeenkomt met een formulierontwerp en er één document wordt gegenereerd dat uit meerdere formulierontwerpen bestaat.

![cs_outputbatchmanyformdesigns2](assets/cs_outputbatchmanyformdesigns2.png)

>[!NOTE]
>
>Voor meer informatie over de dienst van de Output, zie de Verwijzing van de [Diensten voor AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary_of_steps-8}

Voer de volgende stappen uit om de uitvoerservice op te dragen de zoekregels te gebruiken tijdens het genereren van een document:

1. Inclusief projectbestanden.
1. Maak een Output Client-object.
1. Verwijzen naar een XML-gegevensbron.
1. Definieer zoekregels.
1. Stel PDF-runtime-opties in.
1. Stel renderingopties in.
1. Genereer een PDF-document.
1. Haal de resultaten van de bewerking op.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u ervoor zorgen dat u de proxybestanden opneemt.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-output-client.jar
* adobe-utilities.jar (vereist als AEM Forms worden geïmplementeerd op JBoss)
* jbossall-client.jar (vereist als AEM Forms worden geïmplementeerd op JBoss)

als AEM Forms worden geïmplementeerd op een ondersteunde J2EE-toepassingsserver die geen JBoss is, moet u adobe-utilities.jar en jbossall-client.jar vervangen door JAR-bestanden die specifiek zijn voor de J2EE-toepassingsserver waarop AEM Forms worden geïmplementeerd.

**Een uitvoerclient-object maken**

Voordat u programmatisch een uitvoerservicebewerking kunt uitvoeren, moet u een uitvoerservice-clientobject maken.

**Verwijzen naar een XML-gegevensbron**

Een XML-element moet bestaan voor elk formulierveld dat u wilt vullen met gegevens. De naam van het XML-element moet overeenkomen met de veldnaam. Een XML-element wordt genegeerd als het niet overeenkomt met een formulierveld of als de naam van het XML-element niet overeenkomt met de veldnaam. Het is niet nodig de volgorde aan te passen waarin de XML-elementen worden weergegeven, zolang alle XML-elementen zijn opgegeven.

**Zoekregels definiëren**

Als u zoekregels wilt definiëren, definieert u een of meer tekstpatronen waarnaar de uitvoerservices zoeken in de invoergegevens. Voor elk tekstpatroon dat u definieert, geeft u een overeenkomstig formulierontwerp op dat wordt gebruikt als het tekstpatroon zich bevindt. Als een tekstpatroon wordt gevonden, gebruikt de uitvoerservice het bijbehorende formulierontwerp om de uitvoer te genereren. Een voorbeeld van een tekstpatroon is *hypotheek*.

>[!NOTE]
>
>Als tekstpatronen niet worden gevonden, wordt het standaardformulier gebruikt. Zorg ervoor dat alle formulierontwerpen die u gebruikt zich in de basisinhoud bevinden.

**Opties voor PDF-runtime instellen**

Stel de volgende PDF-runtime-opties in zodat de uitvoerservice een PDF-document kan maken op basis van meerdere formulierontwerpen:

* **Bestands-URI**: Hier geeft u de naam en locatie op van het PDF-bestand dat de uitvoerservice genereert.
* **Regels**: Hier geeft u de regels op die u hebt gedefinieerd.
* **LookAHead**: Geeft het aantal bytes op dat vanaf het begin van het invoergegevensbestand moet worden gebruikt om te scannen naar de gedefinieerde tekstpatronen. De standaardwaarde is 500 bytes.

**Renderopties tijdens runtime instellen**

Tijdens het maken van PDF-bestanden kunt u renderingopties instellen. Hoewel deze opties niet vereist zijn (in tegenstelling tot PDF-runtime-opties), kunt u taken uitvoeren zoals het verbeteren van de prestaties van de uitvoerservice. U kunt bijvoorbeeld het formulierontwerp dat de Output-service gebruikt in cache plaatsen om de prestaties te verbeteren.

**Een PDF-document genereren**

Nadat u naar een geldige XML-gegevensbron hebt verwezen en runtime-opties hebt ingesteld, kunt u de uitvoerservice aanroepen, waardoor een PDF-document wordt gegenereerd. Als de uitvoerservice een opgegeven tekstpatroon opzoekt in de invoergegevens, wordt het bijbehorende formulierontwerp gebruikt. Als geen tekstpatroon wordt gebruikt, gebruikt de Output-service het standaardformulierontwerp.

**De resultaten van de bewerking ophalen**

Nadat de dienst van de Output een verrichting uitvoert, keert het de gegevens van XML terug die specificeren of de verrichting succesvol was.

**Zie ook**

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Uitvoerservice-API - Snel starten](/help/forms/developing/output-service-java-api-quick.md#output-service-java-api-quick-start-soap)

### Zoekregels maken met de Java API {#create-search-rules-using-the-java-api}

Maak zoekregels met de Output API (Java):

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-output-client.jar, op in het klassenpad van uw Java-project.

1. Maak een Output Client-object.

   * Maak een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Maak een `OutputClient` object door de constructor ervan te gebruiken en het `ServiceClientFactory` object door te geven.

1. Verwijzen naar een XML-gegevensbron.

   * Maak een `java.io.FileInputStream` object dat staat voor de XML-gegevensbron die wordt gebruikt om het PDF-document te vullen met de constructor ervan en geef een tekenreekswaarde door die de locatie van het XML-bestand aangeeft.
   * Maak een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en het `java.io.FileInputStream` object door te geven.

1. Definieer zoekregels.

   * Maak een `Rule` object met de constructor ervan.
   * Definieer een tekstpatroon door de `Rule` methode van het `setPattern` object aan te roepen en een tekenreekswaarde door te geven die een tekstpatroon opgeeft.
   * Definieer het bijbehorende formulierontwerp door de methode van het `Rule` `setForm` object aan te roepen. Geef een tekenreekswaarde door die de naam van het formulierontwerp aangeeft.

   >[!NOTE]
   >
   >Herhaal de vorige drie substappen voor elk tekstpatroon dat u wilt definiëren.

   * Maak een `java.util.List` object met een `java.util.ArrayList` constructor.
   * Voor elk `Rule` object dat u hebt gemaakt, roept u de `java.util.List` methode van het `add` object aan en geeft u het `Rule` object door.


1. Stel PDF-runtime-opties in.

   * Maak een `PDFOutputOptionsSpec` object met de constructor ervan.
   * Geef de naam en locatie op van het PDF-bestand dat de uitvoerservice genereert door de `PDFOutputOptionsSpec` methode van het `setFileURI` object aan te roepen. Geef een tekenreekswaarde door die de locatie van het PDF-bestand aangeeft. De optie File URI is relatief ten opzichte van de J2EE-toepassingsserver die AEM Forms host, niet ten opzichte van de clientcomputer.
   * Stel de regels in die u hebt gedefinieerd door de `PDFOutputOptionsSpec` methode van het `setRules` object aan te roepen. Geef het `java.util.List` object dat de `Rule` objecten bevat door.
   * Stel het aantal bytes in dat u wilt scannen op de gedefinieerde tekstpatronen door de `PDFOutputOptionsSpec` methode van het `setLookAhead` object aan te roepen. Geef een geheel getal door dat het aantal bytes vertegenwoordigt.

1. Stel renderingopties in.

   * Maak een `RenderOptionsSpec` object met de constructor ervan.
   * Plaats het formulierontwerp in de cache om de prestaties van de Output-service te verbeteren door het `RenderOptionsSpec` object aan te roepen `setCacheEnabled` en door te geven `true`.

1. Genereer een PDF-document.

   Genereer een PDF-document dat is gebaseerd op meerdere formulierontwerpen door de methode van het `OutputClient` `generatePDFOutput` object aan te roepen en de volgende waarden door te geven:

   * Een `TransformationFormat` opsommingswaarde. Geef op om een PDF-document te genereren. `TransformationFormat.PDF`
   * Een tekenreekswaarde die de naam van het standaardformulierontwerp aangeeft. Dit is het formulierontwerp dat wordt gebruikt als een tekstpatroon niet wordt gevonden.
   * Een tekenreekswaarde die de hoofdmap van de inhoud opgeeft waar de formulierontwerpen zich bevinden.
   * Een `PDFOutputOptionsSpec` object dat PDF-runtime-opties bevat.
   * Een `RenderOptionsSpec` object dat renderingopties bevat.
   * Het `com.adobe.idp.Document` object dat de formuliergegevens bevat die door de service Uitvoer worden doorzocht op de gedefinieerde tekstpatronen.

   De `generatePDFOutput` methode retourneert een `OutputResult` object dat de resultaten van de bewerking bevat.

1. Haal de resultaten van de bewerking op.

   * Maak een `com.adobe.idp.Document` object dat de status van de `generatePDFOutput` methode vertegenwoordigt door de `OutputResult` methode van het `getStatusDoc` object aan te roepen.
   * Maak een `java.io.File` object dat de resultaten van de bewerking zal bevatten. Controleer of de bestandsextensie .xml is.
   * Roep de `com.adobe.idp.Document` methode van het `copyToFile` object aan om de inhoud van het `com.adobe.idp.Document` object naar het bestand te kopiëren (zorg dat u het `com.adobe.idp.Document` object gebruikt dat door de `getStatusDoc` methode is geretourneerd).

**Zie ook**

[Overzicht van de stappen](creating-document-output-streams.md#summary-of-steps)

[Snel starten (EJB-modus): Zoekregels maken met de Java API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-search-rules-using-the-java-api)

[Snel starten (SOAP-modus): Zoekregels maken met de Java API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-search-rules-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Zoekregels maken met de webservice-API {#create-search-rules-using-the-web-service-api}

Maak zoekregels met de Output API (webservice):

1. Inclusief projectbestanden.

   Creeer een project van Microsoft .NET dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/OutputService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een Output Client-object.

   * Maak een `OutputServiceClient` object met de standaardconstructor.
   * Maak een `OutputServiceClient.Endpoint.Address` object met de `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de service AEM Forms (bijvoorbeeld `http://localhost:8080/soap/services/OutputService?blob=mtom`.) U hoeft het `lc_version` kenmerk niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt. Geef echter op `?blob=mtom` om MTOM te gebruiken.
   * Maak een `System.ServiceModel.BasicHttpBinding` object door de waarde van het `OutputServiceClient.Endpoint.Binding` veld op te halen. Kiezen naar de geretourneerde waarde `BasicHttpBinding`.
   * Stel het `System.ServiceModel.BasicHttpBinding` veld van het `MessageEncoding` object in op `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam voor AEM-formulieren toe aan het veld `OutputServiceClient.ClientCredentials.UserName.UserName`.
      * Wijs de bijbehorende wachtwoordwaarde aan het veld toe `OutputServiceClient.ClientCredentials.UserName.Password`.
      * Wijs de constante waarde toe `HttpClientCredentialType.Basic` aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Wijs de constante waarde toe `BasicHttpSecurityMode.TransportCredentialOnly` aan het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Verwijzen naar een XML-gegevensbron.

   * Maak een `BLOB` object met de constructor ervan. Het `BLOB` object wordt gebruikt voor het opslaan van gegevens die worden samengevoegd met het PDF-document.
   * Maak een `System.IO.FileStream` object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie vertegenwoordigt van het PDF-document dat moet worden versleuteld en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van het `System.IO.FileStream` object wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` eigenschap van het `Length` object op te halen.
   * Vul de bytearray met streamgegevens door de methode van het `System.IO.FileStream` `Read` object aan te roepen en de bytearray, de startpositie en de lengte van de stream door te geven om te lezen.
   * Vul het `BLOB` object door het `MTOM` veld ervan toe te wijzen met de inhoud van de bytearray.

1. Definieer zoekregels.

   * Maak een `Rule` object met de constructor ervan.
   * Definieer een tekstpatroon door een tekenreekswaarde toe te wijzen die een tekstpatroon opgeeft voor het `Rule` gegevenslid van het `pattern` object.
   * Definieer het bijbehorende formulierontwerp door een tekenreekswaarde toe te wijzen die het formulierontwerp opgeeft aan het `Rule` gegevenslid van het `form` object.

   >[!NOTE]
   >
   >Herhaal de vorige drie substappen voor elk tekstpatroon dat u wilt definiëren.

   * Maak een `MyArrayOf_xsd_anyType` object waarin de regels zijn opgeslagen.
   * Wijs elk `Rule` object toe aan een element van de `MyArrayOf_xsd_anyType` array. Roep de `MyArrayOf_xsd_anyType` methode van het `Add` object aan voor elk `Rule` object.


1. Opties voor PDF-runtime instellen

   * Maak een `PDFOutputOptionsSpec` object met de constructor ervan.
   * Stel de bestands-URI-optie in door een tekenreekswaarde toe te wijzen die de locatie opgeeft van het PDF-bestand dat de uitvoerservice genereert voor het `PDFOutputOptionsSpec` gegevenslid van het `fileURI` object. De optie File URI is relatief ten opzichte van de J2EE-toepassingsserver die AEM Forms host, niet ten opzichte van de clientcomputer.
   * Stel de optie Kopiëren in door een geheel-getalwaarde toe te wijzen die het aantal exemplaren opgeeft dat de service Output genereert voor het `PDFOutputOptionsSpec` gegevenslid van het `copies` object.
   * Stel de regels in die u hebt gedefinieerd door het `MyArrayOf_xsd_anyType` object toe te wijzen waarin de regels worden opgeslagen in het `PDFOutputOptionsSpec` gegevenslid van het `rules` object.
   * Stel het aantal bytes in dat moet worden gescand op de gedefinieerde tekstpatronen door een geheel-getalwaarde toe te wijzen die het aantal bytes vertegenwoordigt dat moet worden gescand op de `PDFOutputOptionsSpec` `lookAhead` gegevensmethode van het object.

1. Renderopties tijdens runtime instellen

   * Maak een `RenderOptionsSpec` object met de constructor ervan.
   * Plaats het formulierontwerp in de cache om de prestaties van de Output-service te verbeteren door de waarde toe te wijzen `true` aan het `RenderOptionsSpec` gegevenslid van het `cacheEnabled` object.

   >[!NOTE]
   >
   >U kunt de versie van het PDF-document niet instellen met het `RenderOptionsSpec` lid van het `pdfVersion` object als het invoerdocument een Acrobat-formulier is. Het PDF-uitvoerdocument behoudt de PDF-versie van het Acrobat-formulier. Ook kunt u de optie PDF-codes niet instellen met de `RenderOptionsSpec` methode van het `taggedPDF` object als het invoerdocument een Acrobat-formulier is.

   >[!NOTE]
   >
   >U kunt de optie Gelineariseerde PDF niet instellen met het `RenderOptionsSpec` lid van het `linearizedPDF` object als het invoer-PDF-document is gecertificeerd of digitaal is ondertekend. Zie PDF-documenten [](/help/forms/developing/digitally-signing-certifying-documents.md#digitally-signing-pdf-documents)digitaal ondertekenen voor meer informatie.

1. Een PDF-document genereren

   Maak een PDF-document door de `OutputServiceService` methode van het `generatePDFOutput`object aan te roepen en de volgende waarden door te geven:

   * Een `TransformationFormat` opsommingswaarde. Geef op om een PDF-document te genereren. `TransformationFormat.PDF`
   * Een tekenreekswaarde waarmee de naam van het formulierontwerp wordt opgegeven.
   * Een tekenreekswaarde die de hoofdmap van de inhoud opgeeft waar het formulierontwerp zich bevindt.
   * Een `PDFOutputOptionsSpec` object dat PDF-runtime-opties bevat.
   * Een `RenderOptionsSpec` object dat renderingopties bevat.
   * Het `BLOB` object dat de XML-gegevensbron bevat die gegevens bevat die met het formulierontwerp moeten worden samengevoegd.
   * Een `BLOB` object dat door de `generatePDFOutput` methode is gevuld. De `generatePDFOutput` methode vult dit object met gegenereerde metagegevens die het document beschrijven. (Deze parameterwaarde is alleen vereist voor aanroepen van een webservice.)
   * Een `BLOB` object dat door de `generatePDFOutput` methode is gevuld. De `generatePDFOutput` methode vult dit object met resultaatgegevens. (Deze parameterwaarde is alleen vereist voor aanroepen van een webservice.)
   * Een `OutputResult` object dat de resultaten van de bewerking bevat. (Deze parameterwaarde is alleen vereist voor aanroepen van een webservice.)

   >[!NOTE]
   >
   >Wanneer u een PDF-document genereert door de `generatePDFOutput` methode aan te roepen, moet u er rekening mee houden dat u geen gegevens kunt samenvoegen met een XFA PDF-formulier dat is ondertekend, gecertificeerd of gebruiksrechten bevat. Zie Gebruiksrechten [toepassen op PDF-documenten](/help/forms/developing/assigning-usage-rights.md#applying-usage-rights-to-pdf-documents)voor informatie over gebruiksrechten.

1. De resultaten van de bewerking ophalen

   * Maak een `System.IO.FileStream` object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die een locatie van een XML-bestand vertegenwoordigt die resultaatgegevens bevat. Zorg ervoor dat de bestandsextensie XML is.
   * Maak een bytearray waarin de gegevensinhoud wordt opgeslagen van het `BLOB` object dat met resultaatgegevens is gevuld via de `OutputServiceService` methode van het `generatePDFOutput` object (de achtste parameter). Vul de bytearray met de waarde van het `BLOB` `MTOM` gegevenslid van het object.
   * Maak een `System.IO.BinaryWriter` object door de constructor ervan aan te roepen en het `System.IO.FileStream` object door te geven.
   * Schrijf de inhoud van de bytearray naar het XML-bestand door de methode van het `System.IO.BinaryWriter` `Write` object aan te roepen en de bytearray door te geven.

**Zie ook**

[Overzicht van de stappen](creating-document-output-streams.md#summary-of-steps)

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## PDF-documenten afvlakken {#flattening-pdf-documents}

Met de service Uitvoer kunt u een interactief PDF-document transformeren naar een niet-interactieve PDF. Met een interactief PDF-document kunnen gebruikers gegevens in de PDF-documentvelden invoeren of wijzigen. Het transformeren van een interactief PDF-document naar een niet-interactief PDF-document wordt *afvlakken* genoemd. Wanneer een PDF-document wordt samengevoegd, kan een gebruiker de gegevens in de documentvelden niet wijzigen. Een reden om een PDF-document af te vlakken is ervoor te zorgen dat gegevens niet kunnen worden gewijzigd.

U kunt de volgende typen PDF-documenten samenvoegen:

* Interactieve XFA PDF-documenten
* Acrobat-formulieren

Als u probeert een PDF af te vlakken die een niet-interactief PDF-document is, ontstaat er een uitzondering.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Output, zie de Verwijzing van de [Diensten voor AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary_of_steps-9}

Voer de volgende stappen uit om een interactief PDF-document af te vlakken naar een niet-interactief PDF-document:

1. Inclusief projectbestanden.
1. Maak een Output Client-object.
1. Een interactief PDF-document ophalen.
1. Transformeer het PDF-document.
1. Sla het niet-interactieve PDF-document op als een PDF-bestand.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u werkt met webservices, moet u de proxybestanden opnemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-output-client.jar
* adobe-utilities.jar (vereist als AEM Forms worden geïmplementeerd op JBoss)
* jbossall-client.jar (vereist als AEM Forms worden geïmplementeerd op JBoss)

als AEM Forms worden geïmplementeerd op een ondersteunde J2EE-toepassingsserver die geen JBoss is, moet u de bestanden adobe-utilities.jar en jbossall-client.jar vervangen door JAR-bestanden die specifiek zijn voor de J2EE-toepassingsserver waarop AEM Forms worden geïmplementeerd. Zie [Including AEM Forms Java library files](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)voor informatie over de locatie van alle JAR-bestanden voor AEM Forms.

**Een uitvoerclient-object maken**

Voordat u programmatisch een uitvoerservicebewerking kunt uitvoeren, moet u een uitvoerservice-clientobject maken. Als u de Java API gebruikt, maakt u een `OutputClient` object. Als u de Output-webservice-API gebruikt, maakt u een `OutputServiceService` object.

**Een interactief PDF-document ophalen**

Haal een interactief PDF-document op dat u wilt transformeren naar een niet-interactief PDF-document. Er is een uitzondering opgetreden bij het transformeren van een niet-interactief PDF-document.

**Het PDF-document transformeren**

Nadat u een interactief PDF-document hebt opgehaald, kunt u het omzetten in een niet-interactief PDF-document. De service Uitvoer retourneert een niet-interactief PDF-document.

**Het niet-interactieve PDF-document opslaan als een PDF-bestand**

U kunt het niet-interactieve PDF-document opslaan als een PDF-bestand.

**Zie ook**

[Een PDF-document samenvoegen met de Java API](creating-document-output-streams.md#flatten-a-pdf-document-using-the-java-api)

[Een PDF-document samenvoegen met de webservice-API](creating-document-output-streams.md#flatten-a-pdf-document-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Uitvoerservice-API - Snel starten](/help/forms/developing/output-service-java-api-quick.md#output-service-java-api-quick-start-soap)

### Een PDF-document samenvoegen met de Java API {#flatten-a-pdf-document-using-the-java-api}

Een interactief PDF-document afvlakken naar een niet-interactief PDF-document met de Output API (Java):

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-output-client.jar, op in het klassenpad van uw Java-project.

1. Maak een Output Client-object.

   * Maak een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Maak een `OutputClient` object door de constructor ervan te gebruiken en het `ServiceClientFactory` object door te geven.

1. Een interactief PDF-document ophalen.

   * Maak een `java.io.FileInputStream` object dat staat voor het interactieve PDF-document dat moet worden getransformeerd met de constructor ervan en geef een tekenreekswaarde door die de locatie van het interactieve PDF-bestand aangeeft.
   * Maak een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en het `java.io.FileInputStream` object door te geven.

1. Transformeer het PDF-document.

   Transformeer het interactieve PDF-document naar een niet-interactief PDF-document door de methode van het `OutputServiceService` `transformPDF` object aan te roepen en de volgende waarden door te geven:

   * Het `com.adobe.idp.Document` object dat het interactieve PDF-document bevat.
   * Een `TransformationFormat` opsommingswaarde. Geef op om een niet-interactief PDF-document te genereren. `TransformationFormat.PDF`
   * Een `PDFARevisionNumber` opsommingswaarde die het revisienummer opgeeft. Omdat deze parameter voor een PDF/A-document is bedoeld, kunt u opgeven `null`.
   * Een tekenreekswaarde die staat voor het wijzigingsnummer en -jaar, gescheiden door een dubbele punt. Omdat deze parameter voor een PDF/A-document is bedoeld, kunt u opgeven `null`.
   * Een `PDFAConformance` opsommingswaarde die het PDF/A-compatibiliteitsniveau vertegenwoordigt. Omdat deze parameter voor een PDF/A-document is bedoeld, kunt u opgeven `null`.

   De `transformPDF` methode retourneert een `com.adobe.idp.Document` object dat een niet-interactief PDF-document bevat.

1. Sla het niet-interactieve PDF-document op als een PDF-bestand.

   * Maak een `java.io.File` object en zorg dat de bestandsnaamextensie .pdf is.
   * Roep de `Document` methode van het `copyToFile` object aan om de inhoud van het `Document` object naar het bestand te kopiëren (zorg dat u het `Document` object gebruikt dat door de `transformPDF` methode is geretourneerd).

**Zie ook**

[Overzicht van de stappen](creating-document-output-streams.md#summary-of-steps)

[Snel starten (EJB-modus): Een PDF-document transformeren met de Java API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-transforming-a-pdf-document-using-the-java-api)

[Snel starten (SOAP-modus): Een PDF-document transformeren met de Java API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-transforming-a-pdf-document-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Een PDF-document samenvoegen met de webservice-API {#flatten-a-pdf-document-using-the-web-service-api}

Een interactief PDF-document afvlakken naar een niet-interactief PDF-document met de Output API (webservice):

1. Inclusief projectbestanden.

   Creeer een project van Microsoft .NET dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/OutputService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een Output Client-object.

   * Maak een `OutputServiceClient` object met de standaardconstructor.
   * Maak een `OutputServiceClient.Endpoint.Address` object met de `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de service AEM Forms (bijvoorbeeld `http://localhost:8080/soap/services/OutputService?blob=mtom`.) U hoeft het `lc_version` kenmerk niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt. Geef echter op `?blob=mtom` om MTOM te gebruiken.
   * Maak een `System.ServiceModel.BasicHttpBinding` object door de waarde van het `OutputServiceClient.Endpoint.Binding` veld op te halen. Kiezen naar de geretourneerde waarde `BasicHttpBinding`.
   * Stel het `System.ServiceModel.BasicHttpBinding` veld van het `MessageEncoding` object in op `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam voor AEM-formulieren toe aan het veld `OutputServiceClient.ClientCredentials.UserName.UserName`.
      * Wijs de bijbehorende wachtwoordwaarde aan het veld toe `OutputServiceClient.ClientCredentials.UserName.Password`.
      * Wijs de constante waarde toe `HttpClientCredentialType.Basic` aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Wijs de constante waarde toe `BasicHttpSecurityMode.TransportCredentialOnly` aan het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Een interactief PDF-document ophalen.

   * Maak een `BLOB` object met de constructor ervan. Het `BLOB` object wordt gebruikt om het interactieve PDF-document op te slaan.
   * Maak een `System.IO.FileStream` object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het interactieve PDF-document vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van het `System.IO.FileStream` object wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` eigenschap van het `Length` object op te halen.
   * Vul de bytearray met streamgegevens door de methode van het `System.IO.FileStream` `Read` object aan te roepen en de bytearray, de startpositie en de lengte van de stream door te geven om te lezen.
   * Vul het `BLOB` object door de `MTOM` eigenschap ervan toe te wijzen met de inhoud van de bytearray.

1. Transformeer het PDF-document.

   Transformeer het interactieve PDF-document naar een niet-interactief PDF-document door de methode van het `OutputClient` `transformPDF` object aan te roepen en de volgende waarden door te geven:

   * Een `BLOB` object dat het interactieve PDF-document bevat.
   * Een `TransformationFormat` opsommingswaarde. Geef op om een niet-interactief PDF-document te genereren. `TransformationFormat.PDF`
   * Een `PDFARevisionNumber` opsommingswaarde die het revisienummer opgeeft.
   * Een Booleaanse waarde die opgeeft of de `PDFARevisionNumber` opsommingswaarde wordt gebruikt. Omdat deze parameter voor een PDF/A-document is bedoeld, kunt u opgeven `false`.
   * Een tekenreekswaarde die staat voor het wijzigingsnummer en -jaar, gescheiden door een dubbele punt. Omdat deze parameter voor een PDF/A-document is bedoeld, kunt u opgeven `null`.
   * Een `PDFAConformance` opsommingswaarde die het PDF/A-compatibiliteitsniveau vertegenwoordigt.
   * Booleaanse waarde die opgeeft of de `PDFAConformance` opsommingswaarde wordt gebruikt. Omdat deze parameter voor een PDF/A-document is bedoeld, kunt u opgeven `false`.

   De `transformPDF` methode retourneert een `BLOB` object dat een niet-interactief PDF-document bevat.

1. Sla het niet-interactieve PDF-document op als een PDF-bestand.

   * Maak een `System.IO.FileStream` object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het niet-interactieve PDF-document vertegenwoordigt.
   * Maak een bytearray met de gegevensinhoud van het `BLOB` object dat door de `transformPDF` methode is geretourneerd. Vul de bytearray met de waarde van het `BLOB` `MTOM` gegevenslid van het object.
   * Maak een `System.IO.BinaryWriter` object door de constructor ervan aan te roepen en het `System.IO.FileStream` object door te geven.
   * Schrijf de inhoud van de bytearray naar een PDF-bestand door de methode van het `System.IO.BinaryWriter` `Write` object aan te roepen en de bytearray door te geven.

**Zie ook**

[Overzicht van de stappen](creating-document-output-streams.md#summary-of-steps)

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)
