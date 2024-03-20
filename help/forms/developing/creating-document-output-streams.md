---
title: Documentuitvoerstromen maken
description: Gebruik de uitvoerservice om documenten om te zetten als PDF (inclusief PDF/A-documenten), PostScript, Printer Control Language (PCL) en Zebra - ZPL, Intermec - IPL, Datamax - DPL en TecToshiba - TPCL-labelindelingen.
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
exl-id: a521bfac-f417-4002-9c5c-8d7794d3eec7
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '18860'
ht-degree: 0%

---

# Documentuitvoerstromen maken  {#creating-document-output-streams}

**Voorbeelden en voorbeelden in dit document gelden alleen voor AEM Forms in JEE-omgeving.**

**Informatie over de uitvoerservice**

Met de uitvoerservice kunt u documenten uitvoeren als PDF (inclusief PDF/A-documenten), PostScript, Printer Control Language (PCL) en de volgende labelindelingen:

* Zebra - ZPL
* Intermec, IPL
* Datamax - DPL
* TecToshiba - TPCL

Met de Output-service kunt u XML-formuliergegevens samenvoegen met een formulierontwerp en het document uitvoeren naar een netwerkprinter of een bestand.

Er zijn twee manieren waarop u een formulierontwerp (een XDP-bestand) kunt doorgeven aan de uitvoerservice. U kunt een van beide `com.adobe.idp.Document` -instantie die een formulierontwerp bevat voor de Output-service. U kunt ook een URI-waarde doorgeven die de locatie van het formulierontwerp opgeeft. Beide manieren worden besproken in *Programmeren met AEM formulieren*.

>[!NOTE]
>
>De service Uitvoer biedt geen ondersteuning voor Acrobat PDF-documenten die toepassingsobjectspecifieke scripts bevatten. Acroform PDF-documenten die toepassingsobjectspecifieke scripts bevatten, worden niet gerenderd.

In de volgende secties ziet u hoe u een formulierontwerp aan de Output-service doorgeeft met behulp van een URI-waarde:

* [PDF-documenten maken](creating-document-output-streams.md#creating-pdf-documents)
* [PDF/A-documenten maken](creating-document-output-streams.md#creating-pdf-a-documents)

In de volgende secties ziet u hoe u een formulierontwerp kunt doorgeven in een `com.adobe.idp.Document` -instantie:

* [Documenten in Inhoudsservices (afgekeurd) doorgeven aan de Uitvoerservice](creating-document-output-streams.md#passing-documents-located-in-content-services-deprecated-to-the-output-service)
* [PDF-documenten maken met behulp van fragmenten](creating-document-output-streams.md#creating-pdf-documents-using-fragments)

Als u bepaalt welke techniek u moet gebruiken, moet u eerst bepalen of u het formulierontwerp van een andere AEM Forms-service ontvangt en het vervolgens doorgeeft binnen een `com.adobe.idp.Document` -instantie. Beide *Documenten doorgeven aan de uitvoerservice* en *PDF-documenten maken met behulp van fragmenten* In deze secties ziet u hoe u een formulierontwerp kunt ophalen van een andere AEM Forms-service. De eerste sectie haalt het formulierontwerp op van Content Services (afgekeurd). In de tweede sectie wordt het formulierontwerp opgehaald uit de Assembler-service.

Als u het formulierontwerp ophaalt vanaf een vaste locatie, zoals het bestandssysteem, kunt u beide methoden gebruiken. U kunt dus de URI-waarde opgeven voor een XDP-bestand of een `com.adobe.idp.Document` -instantie.

Als u een URI-waarde wilt doorgeven die de locatie van het formulierontwerp opgeeft bij het maken van een PDF-document, gebruikt u de opdracht `generatePDFOutput` methode. Ook als u een `com.adobe.idp.Document` -instantie gebruiken voor de service Uitvoer wanneer u een PDF-document maakt, `generatePDFOutput2` methode.

Wanneer u een uitvoerstream naar een netwerkprinter verzendt, kunt u ook een van de twee technieken gebruiken. Een uitvoerstroom naar een printer verzenden door een `com.adobe.idp.Document` instantie die een formulierontwerp bevat, gebruikt u de `sendToPrinter2`methode. Als u een uitvoerstream naar een printer wilt verzenden door een URI-waarde door te geven, gebruikt u de optie `sendToPrinter`methode. De *Afdrukstromen naar printers verzenden* de sectie gebruikt de `sendToPrinter` methode.

U kunt deze taken uitvoeren met de service Uitvoer:

* [PDF-documenten maken](creating-document-output-streams.md#creating-pdf-documents)
* [PDF/A-documenten maken](creating-document-output-streams.md#creating-pdf-a-documents)
* [Documenten in Inhoudsservices (afgekeurd) doorgeven aan de Uitvoerservice](creating-document-output-streams.md#passing-documents-located-in-content-services-deprecated-to-the-output-service)
* [PDF-documenten maken met behulp van fragmenten](creating-document-output-streams.md#creating-pdf-documents-using-fragments)
* [Afdrukken naar bestanden](creating-document-output-streams.md#printing-to-files)
* [Afdrukstromen naar printers verzenden](creating-document-output-streams.md#sending-print-streams-to-printers)
* [Meerdere uitvoerbestanden maken](creating-document-output-streams.md#creating-multiple-output-files)
* [Zoekregels maken](creating-document-output-streams.md#creating-search-rules)
* [PDF-documenten afvlakken](creating-document-output-streams.md#flattening-pdf-documents)

>[!NOTE]
>
>Voor meer informatie over de dienst van de Output, zie [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## PDF-documenten maken {#creating-pdf-documents}

Met de service Uitvoer kunt u een PDF-document maken dat is gebaseerd op een formulierontwerp en XML-formuliergegevens die u opgeeft. Het PDF-document dat door de Output-service wordt gemaakt, is geen interactief PDF-document. Een gebruiker kan geen formuliergegevens invoeren of wijzigen.

Als u een PDF-document wilt maken dat is bedoeld voor langdurige opslag, is het raadzaam een PDF/A-document te maken. (Zie [PDF/A-documenten maken](creating-document-output-streams.md#creating-pdf-a-documents).)

Met de Forms-service kunt u een interactief PDF-formulier maken waarmee een gebruiker gegevens kan invoeren. (Zie [Interactieve PDF forms renderen](/help/forms/developing/rendering-forms.md#rendering-interactive-pdf-forms).)

>[!NOTE]
>
>Voor meer informatie over de dienst van de Output, zie [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary-of-steps}

Voer de volgende stappen uit om een PDF-document te maken:

1. Inclusief projectbestanden.
1. Maak een Output Client-object.
1. Verwijzen naar een XML-gegevensbron.
1. Stel PDF-uitvoeringsopties in.
1. Stel renderingopties in.
1. Een PDF-document genereren.
1. Haal de resultaten van de bewerking op.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u de proxybestanden opnemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-output-client.jar
* adobe-utilities.jar (Vereist als AEM Forms wordt geïmplementeerd op JBoss)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)

als AEM Forms wordt geïmplementeerd op een ondersteunde J2EE-toepassingsserver die geen JBoss is, moet u de bestanden adobe-utilities.jar en jbossall-client.jar vervangen door JAR-bestanden die specifiek zijn voor de J2EE-toepassingsserver waarop AEM Forms wordt geïmplementeerd.

**Een Output Client-object maken**

Voordat u programmatisch een uitvoerservicebewerking kunt uitvoeren, moet u een uitvoerservice-clientobject maken. Als u de Java API gebruikt, maakt u een `OutputClient` object. Als u de uitvoerwebservice-API gebruikt, maakt u een `OutputServiceService` object.

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

**Opties voor PDF bij uitvoering instellen**

Stel de bestands-URI-optie in wanneer u een PDF-document maakt. Met deze optie geeft u de naam en locatie op van het PDF-bestand dat de uitvoerservice genereert.

>[!NOTE]
>
>In plaats van de runtimeoptie voor bestands-URI in te stellen, kunt u het PDF-document via programmacode ophalen van het complexe gegevenstype dat door de Output-service wordt geretourneerd. Als u echter de optie voor het uitvoeren van de bestands-URI instelt, hoeft u geen toepassingslogica te maken die het PDF-document programmatisch ophaalt.

**Renderopties tijdens runtime instellen**

U kunt bij het maken van een PDF-document renderingopties instellen. Hoewel deze opties niet vereist zijn (in tegenstelling tot PDF runtime opties die worden vereist), kunt u taken uitvoeren zoals het verbeteren van de prestaties van de Output-service. U kunt bijvoorbeeld het formulierontwerp in cache plaatsen dat de uitvoerservice gebruikt om de prestaties te verbeteren.

Als u een gecodeerd Acrobat-formulier als invoer gebruikt, kunt u de instelling voor getagde invoer niet uitschakelen met de Java- of webservice-API van de Output-service. Als u probeert programmatisch deze optie in te stellen op `false`, is het PDF-document van het resultaat nog steeds gecodeerd.

>[!NOTE]
>
>Als u geen renderingopties opgeeft, worden standaardwaarden gebruikt. Voor informatie over het renderen van runtime-opties raadpleegt u de `RenderOptionsSpec` klasseverwijzing. (Zie [AEM Forms API-naslag](https://www.adobe.com/go/learn_aemforms_javadocs_63_en)).

**Een PDF-document genereren**

Nadat u naar een geldige XML-gegevensbron met formuliergegevens hebt verwezen en u runtime-opties hebt ingesteld, kunt u de uitvoerservice aanroepen, zodat er een PDF-document wordt gegenereerd.

Wanneer u een PDF-document genereert, geeft u de URI-waarden op die de Output-service nodig heeft om een PDF-document te maken. Een formulierontwerp kan worden opgeslagen op locaties als het serverbestandssysteem of als onderdeel van een AEM Forms-toepassing. Er kan naar een formulierontwerp (of andere bronnen zoals een afbeeldingsbestand) dat als onderdeel van een Forms-toepassing bestaat, worden verwezen door de URI-waarde van de hoofdmap van de inhoud te gebruiken `repository:///`. Neem bijvoorbeeld het volgende formulierontwerp met de naam *Lening.xdp* zich bevindt binnen een Forms-toepassing met de naam *Applications/FormsApplication*:

![cp_cp_formrepository](assets/cp_cp_formrepository.png)

Als u toegang wilt krijgen tot het bestand Loan.xdp dat in de vorige afbeelding wordt weergegeven, geeft u `repository:///Applications/FormsApplication/1.0/FormsFolder/` als de derde parameter die aan de `OutputClient` object `generatePDFOutput` methode. Geef de formuliernaam op (*Lening.xdp*) als de tweede parameter die aan de `OutputClient` object `generatePDFOutput` methode.

Als het XDP-bestand afbeeldingen (of andere bronnen zoals fragmenten) bevat, plaatst u de bronnen in dezelfde toepassingsmap als het XDP-bestand. AEM Forms gebruikt de basis-URI van de inhoud als het basispad om verwijzingen naar afbeeldingen op te lossen. Als het bestand Loan.xdp bijvoorbeeld een afbeelding bevat, dient u de afbeelding in `Applications/FormsApplication/1.0/FormsFolder/`.

>[!NOTE]
>
>U kunt verwijzen naar een Forms-toepassings-URI wanneer u het dialoogvenster `OutputClient` object `generatePDFOutput` of `generatePrintedOutput` methoden.

>[!NOTE]
>
>Zie voor een volledige snelle start die een PDF-document maakt door te verwijzen naar een XDP in een Forms-toepassing [Snel starten (EJB-modus): een PDF-document maken op basis van een XDP-bestand van een toepassing met de Java API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-a-pdf-document-based-on-an-application-xdp-file-using-the-java-api).

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

   * Een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Een `OutputClient` object door de constructor ervan te gebruiken en de `ServiceClientFactory` object.

1. Verwijzen naar een XML-gegevensbron.

   * Een `java.io.FileInputStream` object dat de XML-gegevensbron vertegenwoordigt die wordt gebruikt om het PDF-document te vullen met de constructor ervan en die een tekenreekswaarde doorgeeft die de locatie van het XML-bestand aangeeft.
   * Een `com.adobe.idp.Document` object met behulp van de constructor. Geef de `java.io.FileInputStream` object.

1. Stel PDF-uitvoeringsopties in.

   * Een `PDFOutputOptionsSpec` object met behulp van de constructor.
   * Stel de optie File URI in door het `PDFOutputOptionsSpec` object `setFileURI` methode. Geef een tekenreekswaarde door die de locatie opgeeft van het PDF-bestand dat de uitvoerservice genereert. De optie File URI is relatief ten opzichte van de J2EE-toepassingsserver die als host fungeert voor AEM Forms, niet ten opzichte van de clientcomputer.

1. Stel renderingopties in.

   * Een `RenderOptionsSpec` object met behulp van de constructor.
   * Plaats het formulierontwerp in de cache om de prestaties van de uitvoerservice te verbeteren door het aanroepen van de `RenderOptionsSpec` object `setCacheEnabled` en passeren `true`.

   >[!NOTE]
   >
   >U kunt de versie van het PDF-document niet instellen met de opdracht `RenderOptionsSpec` object `setPdfVersion` methode als het invoerdocument een Acrobat-formulier (een formulier dat in Acrobat is gemaakt) of een XFA-document is dat is ondertekend of gecertificeerd. In het uitvoerdocument blijft de oorspronkelijke PDF PDF-versie behouden. Evenzo kunt u de optie Adobe PDF met tags niet instellen door de optie `RenderOptionsSpec` object `setTaggedPDF` methode als het invoerdocument een Acrobat-formulier of een ondertekend of gecertificeerd XFA-document is.

   >[!NOTE]
   >
   >U kunt de optie Lineaire PDF niet instellen met de opdracht `RenderOptionsSpec` object `setLinearizedPDF` als het invoerdocument PDF is gecertificeerd of digitaal is ondertekend. (Zie [PDF-documenten digitaal ondertekenen ](/help/forms/developing/digitally-signing-certifying-documents.md#digitally-signing-pdf-documents)*.)*

1. Een PDF-document genereren.

   Een PDF-document maken door het `OutputClient` object `generatePDFOutput` en geeft de volgende waarden door:

   * A `TransformationFormat` opsommingswaarde. Als u een PDF-document wilt genereren, geeft u `TransformationFormat.PDF`.
   * Een tekenreekswaarde waarmee de naam van het formulierontwerp wordt opgegeven.
   * Een tekenreekswaarde die de hoofdmap van de inhoud opgeeft waar het formulierontwerp zich bevindt.
   * A `PDFOutputOptionsSpec` -object dat PDF-runtime-opties bevat.
   * A `RenderOptionsSpec` -object dat renderingopties bevat.
   * De `com.adobe.idp.Document` object dat de XML-gegevensbron bevat die gegevens bevat die met het formulierontwerp moeten worden samengevoegd.

   De `generatePDFOutput` methode retourneert een `OutputResult` object dat de resultaten van de bewerking bevat.

   >[!NOTE]
   >
   >Wanneer het produceren van een document van de PDF door te halen `generatePDFOutput` -methode, kunt u geen gegevens samenvoegen met een ondertekend of gecertificeerd XFA PDF-formulier. (Zie [Documenten digitaal ondertekenen en certificeren ](/help/forms/developing/digitally-signing-certifying-documents.md#digitally-signing-and-certifying-documents)*.)*

   >[!NOTE]
   >
   >De `OutputResult` object `getRecordLevelMetaDataList` methode retourneert `null`*.*

   >[!NOTE]
   >
   >U kunt ook een PDF-document maken door het `OutputClient` object `generatePDFOutput2` methode. (Zie [Documenten in Inhoudsservices (afgekeurd) doorgeven aan de Uitvoerservice ](creating-document-output-streams.md#passing-documents-located-in-content-services-deprecated-to-the-output-service)*.)*

1. Haal de resultaten van de bewerking op.

   * Een `com.adobe.idp.Document` object dat de status van het `generatePDFOutput` handeling door de `OutputResult` object `getStatusDoc` methode. Deze methode retourneert XML-gegevens met de status die aangeven of de bewerking is geslaagd.
   * Een `java.io.File` object dat de resultaten van de bewerking bevat. Controleer of de bestandsnaamextensie .xml is.
   * De `com.adobe.idp.Document` object `copyToFile` methode om de inhoud van de `com.adobe.idp.Document` object naar het bestand (gebruik de `com.adobe.idp.Document` object dat is geretourneerd door de `getStatusDoc` methode).

   Hoewel de dienst van de Output het document van PDF naar de plaats schrijft die door het argument wordt gespecificeerd dat tot wordt overgegaan `PDFOutputOptionsSpec` object `setFileURI` methode, kunt u het PDF/A- document programmatically terugwinnen door het `OutputResult` object `getGeneratedDoc` methode.

**Zie ook**

[Overzicht van de stappen](creating-document-output-streams.md#summary-of-steps)

[Snel starten (EJB-modus): een PDF-document maken met de Java API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-a-pdf-document-using-the-java-api)

[Snel starten (SOAP-modus): een PDF-document maken met de Java API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-a-pdf-document-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Een PDF-document maken met de webservice-API {#create-a-pdf-document-using-the-web-service-api}

Maak een PDF-document met de Output API (webservice):

1. Inclusief projectbestanden.

   Creeer een Microsoft .NET project dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/OutputService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` met het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een Output Client-object.

   * Een `OutputServiceClient` object met de standaardconstructor.
   * Een `OutputServiceClient.Endpoint.Address` object door het `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/OutputService?blob=mtom`.) U hoeft de `lc_version` kenmerk. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt. Geef echter `?blob=mtom` MTOM gebruiken.
   * Een `System.ServiceModel.BasicHttpBinding` object door de waarde van het object op te halen `OutputServiceClient.Endpoint.Binding` veld. De geretourneerde waarde omzetten in `BasicHttpBinding`.
   * Stel de `System.ServiceModel.BasicHttpBinding` object `MessageEncoding` veld naar `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld toe `OutputServiceClient.ClientCredentials.UserName.UserName`.
      * De bijbehorende wachtwoordwaarde aan het veld toewijzen `OutputServiceClient.ClientCredentials.UserName.Password`.
      * De constante waarde toewijzen `HttpClientCredentialType.Basic` naar het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * De constante waarde toewijzen `BasicHttpSecurityMode.TransportCredentialOnly` naar het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Verwijzen naar een XML-gegevensbron.

   * Een `BLOB` object met behulp van de constructor. De `BLOB` wordt gebruikt om XML-gegevens op te slaan die met het PDF-document worden samengevoegd.
   * Een `System.IO.FileStream` object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie vertegenwoordigt van het XML-bestand dat formuliergegevens bevat.
   * Maak een bytearray waarin de inhoud van de `System.IO.FileStream` object. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` object `Length` eigenschap.
   * De bytearray vullen met streamgegevens door de `System.IO.FileStream` object `Read` en geeft u de bytearray, de startpositie en de streamlengte door die u wilt lezen.
   * Vul de `BLOB` object door het toe te wijzen `MTOM` veld met de inhoud van de bytearray.

1. Opties voor PDF bij uitvoering instellen

   * Een `PDFOutputOptionsSpec` object met behulp van de constructor.
   * Stel de optie File URI in door een tekenreekswaarde toe te wijzen die de locatie opgeeft van het PDF-bestand dat de uitvoerservice genereert voor de `PDFOutputOptionsSpec` object `fileURI` lid. De optie File URI is relatief ten opzichte van de J2EE-toepassingsserver die als host fungeert voor AEM Forms, niet ten opzichte van de clientcomputer.

1. Stel renderingopties in.

   * Een `RenderOptionsSpec` object met behulp van de constructor.
   * Plaats het formulierontwerp in de cache om de prestaties van de uitvoerservice te verbeteren door de waarde toe te wijzen `true` aan de `RenderOptionsSpec` object `cacheEnabled` lid.

   >[!NOTE]
   >
   >U kunt de versie van het PDF-document niet instellen met de opdracht `RenderOptionsSpec` object `setPdfVersion` methode als het invoerdocument een Acrobat-formulier (een formulier dat in Acrobat is gemaakt) of een XFA-document is dat is ondertekend of gecertificeerd. In het uitvoerdocument blijft de oorspronkelijke PDF PDF-versie behouden. Evenzo kunt u de optie Adobe PDF met tags niet instellen door de optie `RenderOptionsSpec` object `setTaggedPDF`* als het invoerdocument een Acrobat-formulier of een ondertekend of gecertificeerd XFA-document is.*

   >[!NOTE]
   >
   >U kunt de optie Lineaire PDF niet instellen met de opdracht `RenderOptionsSpec` object `linearizedPDF` lid als het invoerdocument PDF is gecertificeerd of digitaal is ondertekend. (Zie [PDF-documenten digitaal ondertekenen ](/help/forms/developing/digitally-signing-certifying-documents.md#digitally-signing-pdf-documents)*.)*

1. Een PDF-document genereren.

   Een PDF-document maken door het `OutputServiceService` object `generatePDFOutput`en geeft de volgende waarden door:

   * A `TransformationFormat` opsommingswaarde. Als u een PDF-document wilt genereren, geeft u `TransformationFormat.PDF`.
   * Een tekenreekswaarde waarmee de naam van het formulierontwerp wordt opgegeven.
   * Een tekenreekswaarde die de hoofdmap van de inhoud opgeeft waar het formulierontwerp zich bevindt.
   * A `PDFOutputOptionsSpec` -object dat PDF-runtime-opties bevat.
   * A `RenderOptionsSpec` -object dat renderingopties bevat.
   * De `BLOB` object dat de XML-gegevensbron bevat die gegevens bevat die met het formulierontwerp moeten worden samengevoegd.
   * A `BLOB` object dat wordt gevuld door het `generatePDFOutput` methode. De `generatePDFOutput` Hiermee wordt dit object gevuld met gegenereerde metagegevens die het document beschrijven. (Deze parameterwaarde is alleen vereist voor aanroepen van een webservice.)
   * A `BLOB` object dat wordt gevuld door het `generatePDFOutput` methode. De `generatePDFOutput` Hiermee wordt dit object gevuld met resultaatgegevens. (Deze parameterwaarde is alleen vereist voor aanroepen van een webservice.)
   * An `OutputResult` object dat de resultaten van de bewerking bevat. (Deze parameterwaarde is alleen vereist voor aanroepen van een webservice.)

   >[!NOTE]
   >
   >Wanneer het produceren van een document van de PDF door te halen `generatePDFOutput` -methode, kunt u geen gegevens samenvoegen met een ondertekend of gecertificeerd XFA PDF-formulier. (Zie [Documenten digitaal ondertekenen en certificeren ](/help/forms/developing/digitally-signing-certifying-documents.md#digitally-signing-and-certifying-documents)*.)*

   >[!NOTE]
   >
   >U kunt ook een PDF-document maken door het `OutputClient` object `generatePDFOutput2` methode. (Zie [Documenten in Inhoudsservices (afgekeurd) doorgeven aan de Uitvoerservice ](creating-document-output-streams.md#passing-documents-located-in-content-services-deprecated-to-the-output-service)*.)*

1. Haal de resultaten van de bewerking op.

   * Een `System.IO.FileStream` object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die een locatie vertegenwoordigt van een XML-bestand dat resultaatgegevens bevat. Controleer of de bestandsnaamextensie .xml is.
   * Maak een bytearray waarin de gegevensinhoud van de `BLOB` object dat is gevuld met resultaatgegevens door de `OutputServiceService` object `generatePDFOutput` methode (de achtste parameter). Vul de bytearray met de waarde van de `BLOB` object `MTOM` `field`.
   * Een `System.IO.BinaryWriter` object door de constructor aan te roepen en de `System.IO.FileStream` object.
   * Schrijf de inhoud van de bytearray naar het XML-bestand door het `System.IO.BinaryWriter` object `Write` en geeft u de bytearray door.

   Zie ook

[Overzicht van de stappen](creating-document-output-streams.md#summary-of-steps)

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

   >[!NOTE]
   >
   >De `OutputServiceService` object `generateOutput` is vervangen.

## PDF/A-documenten maken {#creating-pdf-a-documents}

Met de service Uitvoer kunt u een PDF/A-document maken. Omdat PDF/A een archiefindeling is voor langdurige bewaring van de inhoud van het document, worden alle lettertypen ingesloten en wordt het bestand niet gecomprimeerd. Een PDF/A-document is daarom doorgaans groter dan een standaard PDF-document. Bovendien bevat een PDF/A-document geen audio- en video-inhoud. Net als bij andere uitvoerservicetaken kunt u zowel een formulierontwerp als gegevens opgeven die met een formulierontwerp moeten worden samengevoegd om een PDF/A-document te maken.

De PDF/A-1-specificatie bestaat uit twee conformiteitsniveaus, namelijk a en b. Het grootste verschil tussen beide is met betrekking tot de logische structuur (toegankelijkheid) ondersteuning, die niet is vereist voor compatibiliteitsniveau b. Ongeacht het compatibiliteitsniveau, dicteert PDF/A-1 dat alle lettertypen zijn ingesloten in het gegenereerde PDF/A-document.

Hoewel PDF/A de norm voor het archiveren van PDF- documenten is, is het niet verplicht dat PDF/A voor het archiveren wordt gebruikt als een standaarddocument van de PDF voldoet aan de behoeften van uw bedrijf. De PDF/A-standaard heeft tot doel een bestand van het type PDF te maken dat gedurende een lange periode kan worden opgeslagen en voldoet aan de vereisten voor documentbewaring. Een URL kan bijvoorbeeld niet worden ingesloten in een PDF/A omdat de URL na verloop van tijd ongeldig kan worden.

Uw organisatie moet haar eigen behoeften, de tijdsduur beoordelen u van plan bent om het document te houden, dossiergrootte overwegingen, en uw eigen archiveringsstrategie te bepalen. U kunt programmatically bepalen als een document van PDF PDF/A volgzaam is door de dienst te gebruiken DocConverter. (Zie [Programmaticaal bepalen van PDF/A-compatibiliteit](/help/forms/developing/pdf-a-documents.md#programmatically-determining-pdf-a-compliancy).)

Een PDF/A-document moet het font gebruiken dat is opgegeven in het formulierontwerp en fonts kunnen niet worden vervangen. Als een lettertype dat zich in een PDF-document bevindt, niet beschikbaar is in het besturingssysteem van de host (OS), treedt daarom een uitzondering op.

Wanneer een PDF/A-document in Acrobat wordt geopend, wordt een bericht weergegeven waarin wordt bevestigd dat het document een PDF/A-document is, zoals in de volgende afbeelding wordt getoond.

![cp_cp_pdfamessage](assets/cp_cp_pdfamessage.png)

>[!NOTE]
>
>De AIR-website heeft een sectie met veelgestelde vragen over PDF/A die u kunt openen op [https://www.loc.gov/preservation/digital/formats/fdd/fdd000125.shtml](https://www.loc.gov/preservation/digital/formats/fdd/fdd000125.shtml).

>[!NOTE]
>
>Voor meer informatie over de dienst van de Output, zie [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_65).

### Overzicht van de stappen {#summary_of_steps-1}

Voer de volgende stappen uit om een PDF/A-document te maken:

1. Inclusief projectbestanden.
1. Maak een Output Client-object.
1. Verwijzen naar een XML-gegevensbron.
1. Stel PDF/A-runtime-opties in.
1. Stel renderingopties in.
1. Een PDF/A-document genereren.
1. Haal de resultaten van de bewerking op.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een aangepaste toepassing maakt met behulp van Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u de proxybestanden opnemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-output-client.jar
* adobe-utilities.jar (Vereist als AEM Forms wordt geïmplementeerd op JBoss)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)

als AEM Forms wordt geïmplementeerd op een ondersteunde J2EE-toepassingsserver die geen JBoss is, moet u de bestanden adobe-utilities.jar en jbossall-client.jar vervangen door JAR-bestanden die specifiek zijn voor de J2EE-toepassingsserver waarop AEM Forms wordt geïmplementeerd.

**Een Output Client-object maken**

Voordat u programmatisch een uitvoerservicebewerking kunt uitvoeren, moet u een uitvoerservice-clientobject maken. Als u de Java API gebruikt, maakt u een `OutputClient` object. Als u de uitvoerwebservice-API gebruikt, maakt u een `OutputServiceService` object.

**Verwijzen naar een XML-gegevensbron**

Als u gegevens wilt samenvoegen met het formulierontwerp, moet u verwijzen naar een XML-gegevensbron die gegevens bevat. Een XML-element moet bestaan voor elk formulierveld dat u wilt vullen met gegevens. De naam van het XML-element moet overeenkomen met de veldnaam. Een XML-element wordt genegeerd als het niet overeenkomt met een formulierveld of als de naam van het XML-element niet overeenkomt met de veldnaam. Het is niet nodig de volgorde aan te passen waarin de XML-elementen worden weergegeven als alle XML-elementen zijn opgegeven.

**Opties voor PDF/A-runtime instellen**

U kunt de optie File URI instellen wanneer u een PDF/A-document maakt. De URI is relatief ten opzichte van de J2EE-toepassingsserver die als host fungeert voor AEM Forms. Dit betekent dat als u C:\Adobe instelt, het bestand naar de map op de server wordt geschreven, niet naar de clientcomputer. De URI geeft de naam en locatie op van het PDF/A-bestand dat de uitvoerservice genereert.

**Renderopties tijdens runtime instellen**

U kunt renderingopties instellen wanneer u PDF/A-documenten maakt. Twee aan PDF/A verwante opties die u kunt instellen zijn de `PDFAConformance` en `PDFARevisionNumber` waarden. De `PDFAConformance` Met waarde wordt bedoeld hoe een PDF-document voldoet aan vereisten die bepalen hoe elektronische documenten op lange termijn worden bewaard. Geldige waarden voor deze optie zijn `A` en `B`. Zie de PDF/A-1 ISO-specificatie met de titel voor informatie over de conformiteit van niveau a en b. *ISO 19005-1 Documentbeheer*.

De `PDFARevisionNumber` waarde verwijst naar het revisienummer van een PDF/A-document. Zie de PDF/A-1 ISO-specificatie met de titel voor informatie over het revisienummer van een PDF/A-document *ISO 19005-1 Documentbeheer*.

>[!NOTE]
>
>U kunt de optie Adobe PDF met tags niet instellen op `false` wanneer u een PDF/A 1A-document maakt. PDF/A 1A zal altijd een geëtiketteerd document van de PDF zijn. Bovendien kunt u de optie Adobe PDF met tags niet instellen op `true` wanneer u een PDF/A 1B-document maakt. PDF/A 1B wordt altijd een niet-gecodeerd PDF-document.

**Een PDF/A-document genereren**

Nadat u naar een geldige XML-gegevensbron met formuliergegevens hebt verwezen en u runtime-opties hebt ingesteld, kunt u de uitvoerservice aanroepen, waardoor er een PDF/A-document wordt gegenereerd.

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

   * Een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Een `OutputClient` object door de constructor ervan te gebruiken en de `ServiceClientFactory` object.

1. Verwijzen naar een XML-gegevensbron.

   * Een `java.io.FileInputStream` object dat de XML-gegevensbron vertegenwoordigt die wordt gebruikt om het PDF/A-document te vullen met de constructor ervan en die een tekenreekswaarde doorgeeft die de locatie van het XML-bestand aangeeft.
   * Een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en de `java.io.FileInputStream` object.

1. Stel PDF/A-runtime-opties in.

   * Een `PDFOutputOptionsSpec` object met behulp van de constructor.
   * Stel de optie File URI in door het `PDFOutputOptionsSpec` object `setFileURI` methode. Geef een tekenreekswaarde door die de locatie opgeeft van het PDF-bestand dat de uitvoerservice genereert. De optie File URI is relatief ten opzichte van de J2EE-toepassingsserver die als host fungeert voor AEM Forms, niet ten opzichte van de clientcomputer.

1. Stel renderingopties in.

   * Een `RenderOptionsSpec` object met behulp van de constructor.
   * Stel de `PDFAConformance` waarde door de `RenderOptionsSpec` object `setPDFAConformance` methode en een `PDFAConformance` enum-waarde die het compatibiliteitsniveau opgeeft. Als u bijvoorbeeld compatibiliteitsniveau A wilt opgeven, geeft u `PDFAConformance.A`.
   * Stel de `PDFARevisionNumber` waarde door de `RenderOptionsSpec` object `setPDFARevisionNumber` methode en doorgeven `PDFARevisionNumber.Revision_1`.

   >[!NOTE]
   >
   >De PDF-versie van een PDF/A-document is 1.4, ongeacht de waarde die u opgeeft voor het `RenderOptionsSpec` object `setPdfVersion`*methode.*

1. Een PDF/A-document genereren.

   Een PDF/A-document maken door het `OutputClient` object `generatePDFOutput` en geeft de volgende waarden door:

   * A `TransformationFormat` opsommingswaarde. Als u een PDF/A-document wilt genereren, geeft u `TransformationFormat.PDFA`.
   * Een tekenreekswaarde waarmee de naam van het formulierontwerp wordt opgegeven.
   * Een tekenreekswaarde die de hoofdmap van de inhoud opgeeft waar het formulierontwerp zich bevindt.
   * A `PDFOutputOptionsSpec` -object dat PDF-runtime-opties bevat.
   * A `RenderOptionsSpec` -object dat renderingopties bevat.
   * De `com.adobe.idp.Document` object dat de XML-gegevensbron bevat die gegevens bevat die met het formulierontwerp moeten worden samengevoegd.

   De `generatePDFOutput` methode retourneert een `OutputResult` object dat de resultaten van de bewerking bevat.

   >[!NOTE]
   >
   >De `OutputResult` object `getRecordLevelMetaDataList` methode retourneert `null`.

   >[!NOTE]
   >
   >U kunt ook een PDF /A-document maken door het `OutputClient` object `generatePDFOutput`2 methode. (Zie [Documenten in Inhoudsservices (afgekeurd) doorgeven aan de Uitvoerservice](creating-document-output-streams.md#passing-documents-located-in-content-services-deprecated-to-the-output-service).)

1. Haal de resultaten van de bewerking op.

   * Een `com.adobe.idp.Document` object dat de status van het `generatePDFOutput` door de `OutputResult` object `getStatusDoc` methode.
   * Een `java.io.File` -object dat de resultaten van de bewerking bevat. Controleer of de bestandsnaamextensie .xml is.
   * De `com.adobe.idp.Document` object `copyToFile` methode om de inhoud van de `com.adobe.idp.Document` object naar het bestand (gebruik de `com.adobe.idp.Document` object dat is geretourneerd door de `getStatusDoc` methode).

   >[!NOTE]
   >
   >Hoewel de dienst van de Output het PDF/A- document aan de plaats schrijft die door het argument wordt gespecificeerd dat tot wordt overgegaan `PDFOutputOptionsSpec` object `setFileURI` methode, kunt u het PDF/A- document programmatically terugwinnen door het `OutputResult` object `getGeneratedDoc` methode.

**Zie ook**

[Overzicht van de stappen](creating-document-output-streams.md#summary-of-steps)

[Snel starten (SOAP-modus): een PDF/A-document maken met de Java API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-a-pdf-a-document-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).

### Een PDF/A-document maken met de webservice-API {#create-a-pdf-a-document-using-the-web-service-api}

Een PDF/A-document maken met de Output API (webservice):

1. Inclusief projectbestanden.

   Creeer een Microsoft .NET project dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/OutputService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` met het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een Output Client-object.

   * Een `OutputServiceClient` object met de standaardconstructor.
   * Een `OutputServiceClient.Endpoint.Address` object door het `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/OutputService?blob=mtom`.) U hoeft de `lc_version` kenmerk. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt. Geef echter `?blob=mtom` MTOM gebruiken.
   * Een `System.ServiceModel.BasicHttpBinding` object door de waarde van het object op te halen `OutputServiceClient.Endpoint.Binding` veld. De geretourneerde waarde omzetten in `BasicHttpBinding`.
   * Stel de `System.ServiceModel.BasicHttpBinding` object `MessageEncoding` veld naar `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld toe `OutputServiceClient.ClientCredentials.UserName.UserName`.
      * De bijbehorende wachtwoordwaarde aan het veld toewijzen `OutputServiceClient.ClientCredentials.UserName.Password`.
      * De constante waarde toewijzen `HttpClientCredentialType.Basic` naar het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * De constante waarde toewijzen `BasicHttpSecurityMode.TransportCredentialOnly` naar het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Verwijzen naar een XML-gegevensbron.

   * Een `BLOB` object met behulp van de constructor. De `BLOB` -object wordt gebruikt voor het opslaan van gegevens die worden samengevoegd met het PDF/A-document.
   * Een `System.IO.FileStream` -object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie vertegenwoordigt van het te coderen PDF-document en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van de `System.IO.FileStream` object. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` object `Length` eigenschap.
   * De bytearray vullen met streamgegevens door de `System.IO.FileStream` object `Read` en geeft u de bytearray, de startpositie en de streamlengte door die u wilt lezen.
   * Vul de `BLOB` object door het toe te wijzen `MTOM` veld met de inhoud van de bytearray.

1. Stel PDF/A-runtime-opties in.

   * Een `PDFOutputOptionsSpec` object met behulp van de constructor.
   * Stel de optie File URI in door een tekenreekswaarde toe te wijzen die de locatie opgeeft van het PDF-bestand dat de uitvoerservice genereert voor de `PDFOutputOptionsSpec` object `fileURI` lid. De optie File URI is relatief ten opzichte van de J2EE-toepassingsserver die als host fungeert voor AEM Forms, niet de clientcomputer

1. Stel renderingopties in.

   * Een `RenderOptionsSpec` object met behulp van de constructor.
   * Stel de `PDFAConformance` waarde door een `PDFAConformance` enumwaarde aan de `RenderOptionsSpec` object `PDFAConformance` lid. Als u bijvoorbeeld compatibiliteitsniveau A wilt opgeven, wijst u `PDFAConformance.A` aan dit gegevenslid.
   * Stel de `PDFARevisionNumber` waarde door een `PDFARevisionNumber` enumwaarde aan de `RenderOptionsSpec` object `PDFARevisionNumber` lid. Toewijzen `PDFARevisionNumber.Revision_1` aan dit gegevenslid.

   >[!NOTE]
   >
   >De PDF-versie van een PDF/A-document is 1.4, ongeacht de waarde die u opgeeft.

1. Een PDF/A-document genereren.

   Een PDF-document maken door het `OutputServiceService` object `generatePDFOutput`en geeft de volgende waarden door:

   * Een opsommingswaarde van TransformationFormat. Als u een PDF-document wilt genereren, geeft u `TransformationFormat.PDFA`.
   * Een tekenreekswaarde waarmee de naam van het formulierontwerp wordt opgegeven.
   * Een tekenreekswaarde die de hoofdmap van de inhoud opgeeft waar het formulierontwerp zich bevindt.
   * A `PDFOutputOptionsSpec` -object dat PDF-runtime-opties bevat.
   * A `RenderOptionsSpec` -object dat renderingopties bevat.
   * De `BLOB` object dat de XML-gegevensbron bevat die gegevens bevat die met het formulierontwerp moeten worden samengevoegd.
   * A `BLOB` object dat wordt gevuld door het `generatePDFOutput` methode. De `generatePDFOutput` Hiermee wordt dit object gevuld met gegenereerde metagegevens die het document beschrijven. (Deze parameterwaarde is alleen vereist voor aanroepen van webservices.)
   * A `BLOB` object dat wordt gevuld door het `generatePDFOutput` methode. De `generatePDFOutput` Hiermee wordt dit object gevuld met resultaatgegevens. (Deze parameterwaarde is alleen vereist voor aanroepen van webservices.)
   * An `OutputResult` object dat de resultaten van de bewerking bevat. (Deze parameterwaarde is alleen vereist voor aanroepen van webservices.)

   >[!NOTE]
   >
   >U kunt ook een PDF /A-document maken door het `OutputClient` object `generatePDFOutput`2 methode. (Zie [Documenten in Inhoudsservices (afgekeurd) doorgeven aan de Uitvoerservice](creating-document-output-streams.md#passing-documents-located-in-content-services-deprecated-to-the-output-service).)

1. Haal de resultaten van de bewerking op.

   * Een `System.IO.FileStream` object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die een locatie vertegenwoordigt van een XML-bestand dat resultaatgegevens bevat. Controleer of de bestandsnaamextensie .xml is.
   * Maak een bytearray waarin de gegevensinhoud van de `BLOB` object dat is gevuld met resultaatgegevens door de `OutputServiceService` object `generatePDFOutput` methode (de achtste parameter). Vul de bytearray met de waarde van de `BLOB` object `MTOM` veld.
   * Een `System.IO.BinaryWriter` object door de constructor aan te roepen en de `System.IO.FileStream` object.
   * Schrijf de inhoud van de bytearray naar het XML-bestand door het `System.IO.BinaryWriter` object `Write` en geeft u de bytearray door.

**Zie ook**

[Overzicht van de stappen](creating-document-output-streams.md#summary-of-steps)

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Documenten in Inhoudsservices (afgekeurd) doorgeven aan de Uitvoerservice {#passing-documents-located-in-content-services-deprecated-to-the-output-service}

De service Uitvoer genereert een niet-interactief PDF-formulier dat is gebaseerd op een formulierontwerp dat gewoonlijk als een XDP-bestand wordt opgeslagen en in Designer wordt gemaakt. U kunt een `com.adobe.idp.Document` object dat het formulierontwerp bevat voor de uitvoerservice. De service Uitvoer geeft het formulierontwerp vervolgens weer in het dialoogvenster `com.adobe.idp.Document` object.

Een voordeel van het doorgeven van een `com.adobe.idp.Document` object naar de Output-service is dat andere AEM Forms-servicebewerkingen een `com.adobe.idp.Document` -instantie. Dat wil zeggen dat je een `com.adobe.idp.Document` instantie van een andere servicebewerking en rendert u deze. Stel dat een XDP-bestand wordt opgeslagen in een knooppunt Content Services (afgekeurd) genaamd `/Company Home/Form Designs`, zoals in de volgende afbeelding wordt getoond.

U kunt Loan.xdp programmatically terugwinnen van de Diensten van de Inhoud (afgekeurd) en het XDP dossier tot de dienst van de Output binnen overgaan `com.adobe.idp.Document` object.

>[!NOTE]
>
>Voor meer informatie over de Forms-service raadpleegt u [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary_of_steps-2}

Als u een document dat is verkregen van Content Services (afgekeurd) wilt doorgeven aan de service Uitvoer, voert u de volgende taken uit:

1. Inclusief projectbestanden.
1. Maak een Output- en een Document Management Client API-object.
1. Haal het formulierontwerp op bij Inhoudsservices (afgekeurd).
1. Het niet-interactieve PDF formulier weergeven.
1. Voer een handeling uit met de gegevensstroom.

**Projectbestanden opnemen**

Neem de benodigde bestanden op voor uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, neemt u de proxybestanden op.

**Een Output en een Document Management Client API-object maken**

Voordat u programmatisch een uitvoerservice-API-bewerking kunt uitvoeren, maakt u een Output Client API-object. Omdat met deze workflow een XDP-bestand wordt opgehaald van Content Services (afgekeurd), maakt u ook een Document Management API-object.

**Het formulierontwerp ophalen van Content Services (afgekeurd)**

Haal het XDP-bestand op van Content Services (afgekeurd) met de Java- of webservice-API. Het XDP-bestand wordt geretourneerd binnen een `com.adobe.idp.Document` instantie (of een `BLOB` -instantie als u webservices gebruikt). U kunt dan de `com.adobe.idp.Document` naar de service Uitvoer.

**Het niet-interactieve PDF formulier weergeven**

Als u een niet-interactief formulier wilt genereren, geeft u het `com.adobe.idp.Document` instantie die van (afgekeurde) Inhoudsdiensten aan de dienst van de Output is teruggekeerd.

>[!NOTE]
>
>Twee nieuwe methoden met naam `generatePDFOutput2`en g `eneratePrintedOutput2`accepteren `com.adobe.idp.Document` object dat een formulierontwerp bevat. U kunt ook een `com.adobe.idp.Document`die het formulierontwerp naar de uitvoerservice bevat wanneer een afdrukstroom naar een netwerkprinter wordt verzonden.

**Een handeling uitvoeren met de gegevensstroom van het formulier**

U kunt het niet-interactieve formulier opslaan als een PDF-bestand. Het formulier kan worden weergegeven in Adobe Reader of Acrobat.

**Zie ook**

[Documenten doorgeven aan de uitvoerservice met de Java API](creating-document-output-streams.md#pass-documents-to-the-output-service-using-the-java-api)

[Documenten doorgeven aan de uitvoerservice met de API voor webservices](creating-document-output-streams.md#pass-documents-to-the-output-service-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Uitvoerservice-API - Snel starten](/help/forms/developing/output-service-java-api-quick.md#output-service-java-api-quick-start-soap)

[PDF-documenten maken met behulp van fragmenten](creating-document-output-streams.md#creating-pdf-documents-using-fragments)

### Documenten doorgeven aan de uitvoerservice met de Java API {#pass-documents-to-the-output-service-using-the-java-api}

Geef een document door dat is opgehaald uit Content Services (afgekeurd) met de Output-service en Content Services (afgekeurd) API (Java):

1. Inclusief projectbestanden.

   Neem JAR-bestanden voor clients, zoals adobe-output-client.jar en adobe-contentservices-client.jar, op in het klassenpad van uw Java-project.

1. Maak een Output- en een Document Management Client API-object.

   * Een `ServiceClientFactory` object dat verbindingseigenschappen bevat. (Zie [Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)
   * Een `OutputClient` object door de constructor ervan te gebruiken en de `ServiceClientFactory` object.
   * Een `DocumentManagementServiceClientImpl` object door de constructor ervan te gebruiken en de `ServiceClientFactory` object.

1. Haal het formulierontwerp op bij Inhoudsservices (afgekeurd).

   De `DocumentManagementServiceClientImpl` object `retrieveContent` en geeft de volgende waarden door:

   * Een tekenreekswaarde die de opslaglocatie opgeeft waar de inhoud wordt toegevoegd. De standaardopslag is `SpacesStore`. Deze waarde is een verplichte parameter.
   * Een tekenreekswaarde die het volledig gekwalificeerde pad opgeeft van de inhoud die moet worden opgehaald (bijvoorbeeld `/Company Home/Form Designs/Loan.xdp`). Deze waarde is een verplichte parameter.
   * Een tekenreekswaarde die de versie opgeeft. Deze waarde is een optionele parameter en u kunt een lege tekenreeks doorgeven. In dit geval wordt de laatste versie opgehaald.

   De `retrieveContent` methode retourneert een `CRCResult` object dat het XDP-bestand bevat. Een `com.adobe.idp.Document` instantie door de `CRCResult` object `getDocument` methode.

1. Het niet-interactieve PDF formulier weergeven.

   De `OutputClient` object `generatePDFOutput2` en geeft de volgende waarden door:

   * A `TransformationFormat` opsommingswaarde. Als u een PDF-document wilt genereren, geeft u `TransformationFormat.PDF`.
   * Een tekenreekswaarde die de hoofdmap van de inhoud opgeeft waar de extra bronnen, zoals afbeeldingen, zich bevinden.
   * A `com.adobe.idp.Document` object dat het formulierontwerp vertegenwoordigt (gebruik de instantie die door het `CRCResult` object `getDocument` methode).
   * A `PDFOutputOptionsSpec` -object dat PDF-runtime-opties bevat.
   * A `RenderOptionsSpec` -object dat renderingopties bevat.
   * De `com.adobe.idp.Document` object dat de XML-gegevensbron bevat die gegevens bevat die met het formulierontwerp moeten worden samengevoegd.

   De `generatePDFOutput2` methode retourneert een `OutputResult` object dat de resultaten van de bewerking bevat.

1. Voer een handeling uit met de gegevensstroom van het formulier.

   * Een `com.adobe.idp.Document` object dat het niet-interactieve formulier vertegenwoordigt door het `OutputResult` object `getGeneratedDoc` methode.
   * Een `java.io.File` object dat de resultaten van de bewerking bevat. Controleer of de bestandsnaamextensie .pdf is.
   * De `com.adobe.idp.Document` object `copyToFile` methode om de inhoud van de `com.adobe.idp.Document` object naar het bestand (gebruik de `com.adobe.idp.Document` object dat is geretourneerd door de `getGeneratedDoc` methode).

**Zie ook**

[Overzicht van de stappen](creating-document-output-streams.md#summary-of-steps)

[Snel starten (EJB-modus): documenten doorgeven aan de uitvoerservice met de Java API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-passing-documents-to-the-output-service-using-the-java-api)

[Snel starten (SOAP-modus): documenten doorgeven aan de uitvoerservice met behulp van de Java API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-passing-documents-to-the-output-service-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Documenten doorgeven aan de uitvoerservice met de API voor webservices {#pass-documents-to-the-output-service-using-the-web-service-api}

Geef een document door dat is opgehaald uit Content Services (afgekeurd) met de Output-service en Content Services (afgekeurd) API (webservice):

1. Inclusief projectbestanden.

   Creeer een Microsoft .NET project dat MTOM gebruikt. Omdat deze cliënttoepassing de twee diensten van AEM Forms aanhaalt, creeer twee de dienstverwijzingen. Gebruik de volgende definitie WSDL voor de de dienstverwijzing verbonden aan de dienst van de Output: `http://localhost:8080/soap/services/OutputService?WSDL&lc_version=9.0.1`.

   Gebruik de volgende definitie WSDL voor de de dienstverwijzing verbonden aan de dienst van het Beheer van het Document: `http://localhost:8080/soap/services/DocumentManagementService?WSDL&lc_version=9.0.1`.

   Omdat de `BLOB` het gegevenstype is gemeenschappelijk voor beide de dienstverwijzingen, kwalificeer volledig `BLOB` gegevenstype bij gebruik ervan. In de bijbehorende webservice kunt u snel aan de slag met `BLOB` exemplaren zijn volledig gekwalificeerd.

   >[!NOTE]
   >
   >Vervangen `localhost` met het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een Output- en een Document Management Client API-object.

   * Een `OutputServiceClient` object met de standaardconstructor.
   * Een `OutputServiceClient.Endpoint.Address` object door het `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/OutputService?blob=mtom`). U hoeft de `lc_version` kenmerk. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.)
   * Een `System.ServiceModel.BasicHttpBinding` object door de waarde van het object op te halen `OutputServiceClient.Endpoint.Binding` veld. De geretourneerde waarde omzetten in `BasicHttpBinding`.
   * Stel de `System.ServiceModel.BasicHttpBinding` object `MessageEncoding` veld naar `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld toe `OutputServiceClient.ClientCredentials.UserName.UserName`.
      * De bijbehorende wachtwoordwaarde aan het veld toewijzen `OutputServiceClient.ClientCredentials.UserName.Password`.
      * De constante waarde toewijzen `HttpClientCredentialType.Basic` naar het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.

   * De constante waarde toewijzen `BasicHttpSecurityMode.TransportCredentialOnly` naar het veld `BasicHttpBindingSecurity.Security.Mode`.

   >[!NOTE]
   >
   >Herhaal deze stappen voor de `DocumentManagementServiceClient`serviceclient.

1. Haal het formulierontwerp op bij Inhoudsservices (afgekeurd).

   Inhoud ophalen door de `DocumentManagementServiceClient` object `retrieveContent` en geeft de volgende waarden door:

   * Een tekenreekswaarde die de opslaglocatie opgeeft waar de inhoud wordt toegevoegd. De standaardopslag is `SpacesStore`. Deze waarde is een verplichte parameter.
   * Een tekenreekswaarde die het volledig gekwalificeerde pad opgeeft van de inhoud die moet worden opgehaald (bijvoorbeeld `/Company Home/Form Designs/Loan.xdp`). Deze waarde is een verplichte parameter.
   * Een tekenreekswaarde die de versie opgeeft. Deze waarde is een optionele parameter en u kunt een lege tekenreeks doorgeven. In dit geval wordt de laatste versie opgehaald.
   * Een parameter van de koordoutput die doorbladert verbindingswaarde opslaat.
   * A `BLOB` uitvoerparameter die de inhoud opslaat. U kunt deze uitvoerparameter gebruiken om de inhoud op te halen.
   * A `ServiceReference1.MyMapOf_xsd_string_To_xsd_anyType` uitvoerparameter die inhoudskenmerken opslaat.
   * A `CRCResult` uitvoerparameter. In plaats van dit object te gebruiken, kunt u de opdracht `BLOB` uitvoerparameter om de inhoud op te halen.

1. Het niet-interactieve PDF formulier weergeven.

   De `OutputServiceClient` object `generatePDFOutput2` en geeft de volgende waarden door:

   * A `TransformationFormat` opsommingswaarde. Als u een PDF-document wilt genereren, geeft u `TransformationFormat.PDF`.
   * Een tekenreekswaarde die de hoofdmap van de inhoud opgeeft waar de extra bronnen, zoals afbeeldingen, zich bevinden.
   * A `BLOB` object dat staat voor het formulierontwerp (gebruik de `BLOB` instantie geretourneerd door Content Services (afgekeurd).
   * A `PDFOutputOptionsSpec` -object dat PDF-runtime-opties bevat.
   * A `RenderOptionsSpec` -object dat renderingopties bevat.
   * De `BLOB` object dat de XML-gegevensbron bevat die gegevens bevat die met het formulierontwerp moeten worden samengevoegd.
   * Een uitvoer `BLOB` object dat wordt gevuld door het `generatePDFOutput2` methode. De `generatePDFOutput2` Hiermee wordt dit object gevuld met gegenereerde metagegevens die het document beschrijven. (Deze parameterwaarde is alleen vereist voor aanroepen van een webservice.)
   * Een uitvoer `OutputResult` object dat de resultaten van de bewerking bevat. (Deze parameterwaarde is alleen vereist voor aanroepen van een webservice.)

   De `generatePDFOutput2` methode retourneert een `BLOB` -object dat het niet-interactieve PDF-formulier bevat.

1. Voer een handeling uit met de gegevensstroom van het formulier.

   * Een `System.IO.FileStream` object door de constructor ervan aan te roepen. Geef een tekenreekswaarde door die staat voor de bestandslocatie van het interactieve PDF-document en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van de `BLOB` object opgehaald uit het `generatePDFOutput2` methode. Vul de bytearray met de waarde van de `BLOB` object `MTOM` lid.
   * Een `System.IO.BinaryWriter` object door de constructor aan te roepen en de `System.IO.FileStream` object.
   * Schrijf de inhoud van de bytearray naar een PDF-bestand door het `System.IO.BinaryWriter` object `Write` en geeft u de bytearray door.

**Zie ook**

[Overzicht van de stappen](creating-document-output-streams.md#summary-of-steps)

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

## Documenten in de opslagplaats doorgeven aan de uitvoerservice {#passing-documents-located-in-the-repository-to-the-output-service}

De service Uitvoer genereert een niet-interactief PDF-formulier dat is gebaseerd op een formulierontwerp dat gewoonlijk als een XDP-bestand wordt opgeslagen en in Designer wordt gemaakt. U kunt een `com.adobe.idp.Document` object dat het formulierontwerp bevat voor de uitvoerservice. De service Uitvoer geeft het formulierontwerp vervolgens weer in het dialoogvenster `com.adobe.idp.Document` object.

Een voordeel van het doorgeven van een `com.adobe.idp.Document` object naar de Output-service is dat andere AEM Forms-servicebewerkingen een `com.adobe.idp.Document` -instantie. Dat wil zeggen dat je een `com.adobe.idp.Document` instantie van een andere servicebewerking en rendert u deze. Stel bijvoorbeeld dat een XDP-bestand wordt opgeslagen in de AEM Forms-opslagplaats, zoals in de volgende afbeelding wordt getoond.

![pd_pd_formrepository](assets/pd_pd_formrepository.png)

De *FormsFolder* Deze map is een door de gebruiker gedefinieerde locatie in de AEM Forms-opslagplaats (deze locatie is een voorbeeld en bestaat standaard niet). In dit voorbeeld bevindt het formulierontwerp met de naam Loan.xdp zich in deze map. Naast het formulierontwerp kunnen ook andere formulierelementen, zoals afbeeldingen, op deze locatie worden opgeslagen. Het pad naar een resource in de AEM Forms-opslagplaats is:

`Applications/Application-name/Application-version/Folder.../Filename`

U kunt Loan.xdp programmatically van de bewaarplaats van AEM Forms terugwinnen en het tot de dienst van de Output binnen overgaan `com.adobe.idp.Document` object.

U kunt op twee manieren een PDF maken op basis van een XDP-bestand in de opslagplaats. U kunt de XDP-locatie doorgeven via verwijzing of u kunt de XDP-locatie via programmacode ophalen uit de opslagplaats en deze doorgeven aan de Output-service in een XDP-bestand.

[Snel starten (EJB-modus): een PDF-document maken op basis van een XDP-bestand van een toepassing met de Java API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-a-pdf-document-based-on-an-application-xdp-file-using-the-java-api) (geeft aan hoe u de locatie van het XDP-bestand via verwijzing doorgeeft).

[Snel starten (EJB-modus): een document in de AEM Forms Repository doorgeven aan de Output-service met de Java API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-passing-a-document-located-in-the-repository-to-the-output-service-using-the-java-api) (toont hoe u het XDP-bestand programmatisch kunt ophalen uit de AEM Forms Repository en dit kunt doorgeven aan de Output Service in een `com.adobe.idp.Document` -instantie). (In deze sectie wordt besproken hoe deze taak moet worden uitgevoerd)

>[!NOTE]
>
>Voor meer informatie over de Forms-service raadpleegt u [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary_of_steps-3}

Voer de volgende taken uit om een document dat is verkregen van de AEM Forms-opslagplaats door te geven aan de Output-service:

1. Inclusief projectbestanden.
1. Maak een Output- en een Document Management Client API-object.
1. Haal het formulierontwerp op uit de AEM Forms-opslagplaats.
1. Het niet-interactieve PDF formulier weergeven.
1. Voer een handeling uit met de gegevensstroom.

**Projectbestanden opnemen**

Neem de benodigde bestanden op voor uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, neemt u de proxybestanden op.

**Een Output en een Document Management Client API-object maken**

Voordat u programmatisch een uitvoerservice-API-bewerking kunt uitvoeren, maakt u een Output Client API-object. Omdat met deze workflow een XDP-bestand wordt opgehaald van Content Services (afgekeurd), maakt u ook een Document Management API-object.

**Het formulierontwerp ophalen uit de AEM Forms Repository**

Haal het XDP-bestand op uit de AEM Forms Repository met behulp van de Repository API. (Zie [Bronnen lezen](/help/forms/developing/aem-forms-repository.md#reading-resources).)

Het XDP-bestand wordt geretourneerd binnen een `com.adobe.idp.Document` instantie (of een `BLOB` -instantie als u webservices gebruikt). U kunt dan de `com.adobe.idp.Document` -instantie van de uitvoerservice.

**Het niet-interactieve PDF formulier weergeven**

Als u een niet-interactief formulier wilt genereren, geeft u het `com.adobe.idp.Document` instantie die is geretourneerd met de AEM Forms Repository API.

>[!NOTE]
>
>Twee nieuwe methoden met naam `generatePDFOutput2`en `generatePrintedOutput2`accepteren `com.adobe.idp.Document`object dat een formulierontwerp bevat. U kunt ook een `com.adobe.idp.Document` die het formulierontwerp naar de uitvoerservice bevat wanneer een afdrukstroom naar een netwerkprinter wordt verzonden.

**Een handeling uitvoeren met de gegevensstroom van het formulier**

U kunt het niet-interactieve formulier opslaan als een PDF-bestand. Het formulier kan worden weergegeven in Adobe Reader of Acrobat.

**Zie ook**

[Documenten in de gegevensopslagruimte aan de uitvoerservice doorgeven met de Java API](creating-document-output-streams.md#pass-documents-located-in-the-repository-to-the-output-service-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Uitvoerservice-API - Snel starten](/help/forms/developing/output-service-java-api-quick.md#output-service-java-api-quick-start-soap)

ResourceRepositoryClient

### Documenten in de gegevensopslagruimte aan de uitvoerservice doorgeven met de Java API {#pass-documents-located-in-the-repository-to-the-output-service-using-the-java-api}

Geef een document dat is opgehaald uit de opslagplaats door gebruik te maken van de Output-service en de Repository-API (Java):

1. Inclusief projectbestanden.

   Neem JAR-bestanden voor clients, zoals adobe-output-client.jar en adobe-repository-client.jar, op in het klassenpad van uw Java-project.

1. Maak een Output- en een Document Management Client API-object.

   * Een `ServiceClientFactory` object dat verbindingseigenschappen bevat. (Zie [Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)
   * Een `OutputClient` object door de constructor ervan te gebruiken en de `ServiceClientFactory` object.
   * Een `DocumentManagementServiceClientImpl` object door de constructor ervan te gebruiken en de `ServiceClientFactory` object.

1. Haal het formulierontwerp op uit de AEM Forms Repository.

   De `ResourceRepositoryClient` object `readResourceContent` methode en geef een tekenreekswaarde door die de URI-locatie opgeeft aan het XDP-bestand. Bijvoorbeeld: `/Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`. Deze waarde is verplicht. Deze methode retourneert een `com.adobe.idp.Document` -instantie die het XDP-bestand vertegenwoordigt.

1. Het niet-interactieve PDF formulier weergeven.

   De `OutputClient` object `generatePDFOutput2` en geeft de volgende waarden door:

   * A `TransformationFormat` opsommingswaarde. Als u een PDF-document wilt genereren, geeft u `TransformationFormat.PDF`.
   * Een tekenreekswaarde die de hoofdmap van de inhoud opgeeft waar de extra bronnen, zoals afbeeldingen, zich bevinden. Bijvoorbeeld: `repository:///Applications/FormsApplication/1.0/FormsFolder/`.
   * A `com.adobe.idp.Document` object dat het formulierontwerp vertegenwoordigt (gebruik de instantie die door het `ResourceRepositoryClient` object `readResourceContent` methode).
   * A `PDFOutputOptionsSpec` -object dat PDF-runtime-opties bevat.
   * A `RenderOptionsSpec` -object dat renderingopties bevat.
   * De `com.adobe.idp.Document` object dat de XML-gegevensbron bevat die gegevens bevat die met het formulierontwerp moeten worden samengevoegd.

   De `generatePDFOutput2` methode retourneert een `OutputResult` object dat de resultaten van de bewerking bevat.

1. Voer een handeling uit met de gegevensstroom van het formulier.

   * Een `com.adobe.idp.Document` object dat het niet-interactieve formulier vertegenwoordigt door het `OutputResult` object `getGeneratedDoc` methode.
   * Een `java.io.File` object dat de resultaten van de bewerking bevat. Controleer of de bestandsnaamextensie .pdf is.
   * De `com.adobe.idp.Document` object `copyToFile` methode om de inhoud van de `com.adobe.idp.Document` object naar het bestand (gebruik de `com.adobe.idp.Document` object dat is geretourneerd door de `getGeneratedDoc` methode).

**Zie ook**

[Overzicht van de stappen](creating-document-output-streams.md#summary-of-steps)

[Snel starten (EJB-modus): een document in de AEM Forms Repository doorgeven aan de Output-service met de Java API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-passing-a-document-located-in-the-repository-to-the-output-service-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## PDF-documenten maken met behulp van fragmenten {#creating-pdf-documents-using-fragments}

Met de services Uitvoer en Samenstellen kunt u een uitvoerstream maken, zoals een PDF-document, die is gebaseerd op fragmenten. De Assembler-service brengt een XDP-document samen dat is gebaseerd op fragmenten in meerdere XDP-bestanden. Het samengevoegde XDP-document wordt doorgegeven aan de Output-service, die een PDF-document maakt. Hoewel deze workflow een PDF-document weergeeft dat wordt gegenereerd, kan de Output-service andere uitvoertypen genereren, zoals ZPL, voor deze workflow. Een PDF-document wordt alleen gebruikt voor discussiedoeleinden.

Deze workflow wordt in de volgende afbeelding getoond.

![cp_cp_outputassemblefragmenten](assets/cp_cp_outputassemblefragments.png)

Voor lezen *PDF-documenten maken met behulp van fragmenten* Daarom wordt u aangeraden bekend te raken met het gebruik van de Assembler-service voor het samenstellen van meerdere XDP-documenten. (Zie [Meerdere XDP-fragmenten samenstellen](/help/forms/developing/assembling-pdf-documents.md#assembling-multiple-xdp-fragments).)

>[!NOTE]
>
>U kunt ook een formulierontwerp dat door de Assembler-service is samengesteld, aan de Forms-service doorgeven in plaats van aan de Output-service. Het belangrijkste verschil tussen de Output-service en de Forms-service is dat de Forms-service interactieve PDF-documenten genereert en dat de Output-service niet-interactieve PDF-documenten produceert. Ook kan de Forms-service geen op printers gebaseerde uitvoerstreams zoals ZPL genereren.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Output, zie [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary_of_steps-4}

Voer de volgende stappen uit om een PDF-document te maken op basis van fragmenten:

1. Inclusief projectbestanden.
1. Maak een Output- en Assembler Client-object.
1. Gebruik de Assembler-service om het formulierontwerp te genereren.
1. Gebruik de service Uitvoer om het PDF-document te genereren.
1. Sla het PDF-document op als een PDF-bestand.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u de proxybestanden opnemen.

**Een Output- en Assembler Client-object maken**

Voordat u programmatisch een uitvoerservice-API-bewerking kunt uitvoeren, maakt u een Output Client API-object. Bovendien maakt u een Assembler Client API-object omdat deze workflow de Assembler-service oproept om het formulierontwerp te maken.

**Met de Assembler-service kunt u het formulierontwerp genereren**

Met de Assembler-service kunt u het formulierontwerp genereren met behulp van fragmenten. De dienst van de Assembler keert a terug `com.adobe.idp.Document` instantie die het formulierontwerp bevat.

**De service Uitvoer gebruiken om het PDF-document te genereren**

U kunt de service Uitvoer gebruiken om een PDF-document te genereren met behulp van het formulierontwerp dat de Assembler-service heeft gemaakt. Geef de `com.adobe.idp.Document` instantie die de dienst van de Assembler aan de dienst van de Output terugkwam.

**Het PDF-document opslaan als een PDF-bestand**

Nadat de service Uitvoer een PDF-document heeft gegenereerd, kunt u dit opslaan als een PDF-bestand.

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

   * Een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Een `OutputClient` object door de constructor ervan te gebruiken en de `ServiceClientFactory` object.
   * Een `AssemblerServiceClient` object door de constructor ervan te gebruiken en de `ServiceClientFactory` object.

1. Gebruik de Assembler-service om het formulierontwerp te genereren.

   De `AssemblerServiceClient` object `invokeDDX` en geeft de volgende vereiste waarden door:

   * A `com.adobe.idp.Document` -object dat het te gebruiken DDX-document vertegenwoordigt.
   * A `java.util.Map` -object dat de invoer-XDP-bestanden bevat.
   * A `com.adobe.livecycle.assembler.client.AssemblerOptionSpec` -object dat de runtime-opties opgeeft, inclusief het standaardfont en het taaklogniveau.

   De `invokeDDX` methode retourneert een `com.adobe.livecycle.assembler.client.AssemblerResult` object dat het geassembleerde XDP-document bevat. Voer de volgende handelingen uit om het samengevoegde XDP-document op te halen:

   * De `AssemblerResult` object `getDocuments` methode. Deze methode retourneert een `java.util.Map` object.
   * Doorlopen `java.util.Map` object tot u het resultaat hebt gevonden `com.adobe.idp.Document` object.
   * De `com.adobe.idp.Document` object `copyToFile` methode voor het extraheren van het samengevoegde XDP-document.

1. Gebruik de service Uitvoer om het PDF-document te genereren.

   De `OutputClient` object `generatePDFOutput2` en geeft de volgende waarden door:

   * A `TransformationFormat` opsommingswaarde. Als u een PDF-document wilt genereren, geeft u `TransformationFormat.PDF`
   * Een tekenreekswaarde die de hoofdmap van de inhoud opgeeft waar de extra bronnen, zoals afbeeldingen, zich bevinden
   * A `com.adobe.idp.Document` object dat het formulierontwerp vertegenwoordigt (gebruik de instantie die door de Assembler-service wordt geretourneerd)
   * A `PDFOutputOptionsSpec` object dat PDF-runtime-opties bevat
   * A `RenderOptionsSpec` object dat renderingopties bevat
   * De `com.adobe.idp.Document` object dat de XML-gegevensbron bevat die gegevens bevat die met het formulierontwerp moeten worden samengevoegd

   De `generatePDFOutput2` methode retourneert een `OutputResult` object dat de resultaten van de bewerking bevat

1. Sla het PDF-document op als een PDF-bestand.

   * Een `com.adobe.idp.Document` object dat het PDF-document vertegenwoordigt door het `OutputResult` object `getGeneratedDoc` methode.
   * Een `java.io.File` object dat de resultaten van de bewerking bevat. Zorg ervoor dat de bestandsnaamextensie .pdf is.
   * De `com.adobe.idp.Document` object `copyToFile` methode om de inhoud van de `com.adobe.idp.Document` naar het bestand. (Gebruik de `com.adobe.idp.Document` het object dat `getGeneratedDoc` geretourneerde methode.)

**Zie ook**

[Overzicht van de stappen](creating-document-output-streams.md#summary-of-steps)

[Snel starten (EJB-modus): een PDF-document maken op basis van fragmenten met de Java API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-a-pdf-document-based-on-fragments-using-the-java-api)

[Snel starten (SOAP-modus): een PDF-document maken op basis van fragmenten met de Java API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-a-pdf-document-based-on-fragments-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).

### Een PDF-document maken op basis van fragmenten met de webservice-API {#create-a-pdf-document-based-on-fragments-using-the-web-service-api}

Maak een PDF-document op basis van fragmenten met de API voor uitvoerservice en de API voor vergaderingsservice (webservice):

1. Inclusief projectbestanden.

   Creeer een Microsoft .NET project dat MTOM gebruikt. Gebruik de volgende definitie WSDL voor de de dienstverwijzing verbonden aan de dienst van de Output:

   ```java
    http://localhost:8080/soap/services/OutputService?WSDL&lc_version=9.0.1.
   ```

   Gebruik de volgende definitie WSDL voor de de dienstverwijzing verbonden aan de dienst van de Assembler:

   ```java
    http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1.
   ```

   Omdat de `BLOB` het gegevenstype is gemeenschappelijk voor beide de dienstverwijzingen, kwalificeer volledig `BLOB` gegevenstype bij gebruik ervan. In de bijbehorende webservice kunt u snel aan de slag met `BLOB` exemplaren zijn volledig gekwalificeerd.

   >[!NOTE]
   >
   >Vervangen `localhost` met het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een Output- en Assembler Client-object.

   * Een `OutputServiceClient` object met de standaardconstructor.
   * Een `OutputServiceClient.Endpoint.Address` object door het `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/OutputService?blob=mtom`.) U hoeft de `lc_version` kenmerk. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt. Geef echter `?blob=mtom` MTOM gebruiken.
   * Een `System.ServiceModel.BasicHttpBinding` object door de waarde van het object op te halen `OutputServiceClient.Endpoint.Binding` veld. De geretourneerde waarde omzetten in `BasicHttpBinding`.
   * Stel de `System.ServiceModel.BasicHttpBinding` object `MessageEncoding` veld naar `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam voor AEM formulieren toe aan de `OutputServiceClient.ClientCredentials.UserName.UserName`veld.
      * Wijs de overeenkomstige wachtwoordwaarde aan toe `OutputServiceClient.ClientCredentials.UserName.Password`veld.
      * De constante waarde toewijzen `HttpClientCredentialType.Basic` aan de `BasicHttpBindingSecurity.Transport.ClientCredentialType`veld.

   * Wijs het `BasicHttpSecurityMode.TransportCredentialOnly` constante waarde voor de `BasicHttpBindingSecurity.Security.Mode`veld.

   >[!NOTE]
   >
   >Herhaal deze stappen voor de `AssemblerServiceClient`object.

1. Gebruik de Assembler-service om het formulierontwerp te genereren.

   De `AssemblerServiceClient` object `invokeDDX` en geeft de volgende waarden door:

   * A `BLOB` object dat staat voor het DDX-document
   * De `MyMapOf_xsd_string_To_xsd_anyType` object dat de vereiste bestanden bevat
   * An `AssemblerOptionSpec` object dat uitvoeringsopties opgeeft

   De `invokeDDX` methode retourneert een `AssemblerResult` object dat de resultaten van de taak en eventuele uitzonderingen bevat die zijn opgetreden. Voer de volgende handelingen uit om het nieuwe XDP-document te verkrijgen:

   * Toegang krijgen tot de `AssemblerResult` object `documents` veld, dat een `Map` -object dat de resulterende PDF-documenten bevat.
   * Doorlopen `Map` object om het samengevoegde formulierontwerp op te halen. Cast het lid van die array `value` een `BLOB`. Dit doorgeven `BLOB` naar de service Uitvoer.

1. Gebruik de service Uitvoer om het PDF-document te genereren.

   De `OutputServiceClient` object `generatePDFOutput2` en geeft de volgende waarden door:

   * A `TransformationFormat` opsommingswaarde. Als u een PDF-document wilt genereren, geeft u `TransformationFormat.PDF`.
   * Een tekenreekswaarde die de hoofdmap van de inhoud opgeeft waar de extra bronnen, zoals afbeeldingen, zich bevinden.
   * A `BLOB` object dat staat voor het formulierontwerp (gebruik de `BLOB` -instantie die door de Assembler-service wordt geretourneerd).
   * A `PDFOutputOptionsSpec` -object dat PDF-runtime-opties bevat.
   * A `RenderOptionsSpec` -object dat renderingopties bevat.
   * De `BLOB` object dat de XML-gegevensbron bevat die gegevens bevat die met het formulierontwerp moeten worden samengevoegd.
   * Een uitvoer `BLOB` het object dat `generatePDFOutput2` wordt gevuld. De `generatePDFOutput2` Hiermee wordt dit object gevuld met gegenereerde metagegevens die het document beschrijven. (Deze parameterwaarde is alleen vereist voor aanroepen van een webservice.)
   * Een uitvoer `OutputResult` object dat de resultaten van de bewerking bevat. (Deze parameterwaarde is alleen vereist voor aanroepen van een webservice.)

   De `generatePDFOutput2` methode retourneert een `BLOB` -object dat het niet-interactieve PDF-formulier bevat.

1. Sla het PDF-document op als een PDF-bestand.

   * Een `System.IO.FileStream` object door de constructor ervan aan te roepen. Geef een tekenreekswaarde door die staat voor de bestandslocatie van het interactieve PDF-document en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van de `BLOB` object opgehaald uit het `generatePDFOutput2` methode. Vul de bytearray met de waarde van de `BLOB` object `MTOM` lid.
   * Een `System.IO.BinaryWriter` object door de constructor aan te roepen en de `System.IO.FileStream` object.
   * Schrijf de inhoud van de bytearray naar een PDF-bestand door het `System.IO.BinaryWriter` object `Write` en geeft u de bytearray door.

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
>Zie voor informatie over het verzenden van afdrukstromen naar printers [Afdrukstromen naar printers verzenden](creating-document-output-streams.md#sending-print-streams-to-printers).

>[!NOTE]
>
>Voor meer informatie over de dienst van de Output, zie [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

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
* adobe-utilities.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)

als AEM Forms wordt geïmplementeerd op een ondersteunde J2EE-toepassingsserver die geen JBoss is, moet u de bestanden adobe-utilities.jar en jbossall-client.jar vervangen door JAR-bestanden die specifiek zijn voor de J2EE-toepassingsserver waarop AEM Forms wordt geïmplementeerd. (Zie [Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).)

**Een Output Client-object maken**

Voordat u programmatisch een uitvoerservicebewerking kunt uitvoeren, moet u een uitvoerservice-clientobject maken. Als u de Java API gebruikt, maakt u een `OutputClient` object. Als u de uitvoerwebservice-API gebruikt, maakt u een `OutputServiceService` object.

**Verwijzen naar een XML-gegevensbron**

Als u een document wilt afdrukken dat gegevens bevat, moet u verwijzen naar een XML-gegevensbron die XML-elementen bevat voor elk formulierveld dat u wilt vullen met gegevens. De naam van het XML-element moet overeenkomen met de veldnaam. Een XML-element wordt genegeerd als het niet overeenkomt met een formulierveld of als de naam van het XML-element niet overeenkomt met de veldnaam. Het is niet nodig de volgorde aan te passen waarin de XML-elementen worden weergegeven als alle XML-elementen zijn opgegeven.

**Stel runtime-opties voor afdrukken in die nodig zijn om af te drukken naar een bestand**

Als u naar een bestand wilt afdrukken, moet u de runtime-optie voor de bestands-URI instellen door de locatie en de naam op te geven van het bestand dat door de uitvoerservice wordt afgedrukt. U kunt bijvoorbeeld de uitvoerservice de instructie geven een PostScript-bestand met de naam *MortgaugeForm.ps* naar C:\Adobe, geeft u C:\Adobe\MortgageForm.ps op.

>[!NOTE]
>
>Er zijn optionele uitvoeringsopties die u kunt definiëren. Voor informatie over alle opties die u kunt instellen, raadpleegt u de `PrintedOutputOptionsSpec` klasseverwijzing in [AEM Forms API-naslag](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

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

   * Een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Een `OutputClient` object door de constructor ervan te gebruiken en de `ServiceClientFactory` object.

1. Verwijzen naar een XML-gegevensbron.

   * Een `java.io.FileInputStream` object dat de XML-gegevensbron vertegenwoordigt die wordt gebruikt om het document te vullen met de constructor ervan en die een tekenreekswaarde doorgeeft die de locatie van het XML-bestand aangeeft.
   * Een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en de `java.io.FileInputStream` object.

1. Stel de runtime-opties voor afdrukken in die nodig zijn om af te drukken naar een bestand.

   * Een `PrintedOutputOptionsSpec` object met behulp van de constructor.
   * Geef het bestand op door de objecten PrintedOutputOptionsSpec aan te roepen `setFileURI` en het doorgeven van een tekenreekswaarde die de naam en locatie van het bestand vertegenwoordigt. Als u bijvoorbeeld wilt dat de uitvoerservice wordt afgedrukt naar een PostScript-bestand met de naam MortgaugeForm.ps in C:\Adobe, geeft u C:\\Adobe\MortgageForm.ps op.
   * Geef het aantal exemplaren op dat moet worden afgedrukt door het `PrintedOutputOptionsSpec` object `setCopies` methode en het overgaan van een geheelwaarde die het aantal exemplaren vertegenwoordigt.

1. Druk de afdrukstroom naar een bestand af.

   Afdrukken naar een bestand door het `OutputClient` object `generatePrintedOutput` en geeft de volgende waarden door:

   * A `PrintFormat` opsommingswaarde die de indeling van de afdrukstroom opgeeft die moet worden gemaakt. Als u bijvoorbeeld een PostScript-afdrukstroom wilt maken, geeft u `PrintFormat.PostScript`.
   * Een tekenreekswaarde waarmee de naam van het formulierontwerp wordt opgegeven.
   * Een tekenreekswaarde die de locatie van verwante secundaire bestanden, zoals afbeeldingsbestanden, opgeeft.
   * Een tekenreekswaarde die de locatie aangeeft van het XDC-bestand dat moet worden gebruikt (u kunt doorgeven `null` als u het XDC-bestand hebt opgegeven om te gebruiken met de `PrintedOutputOptionsSpec` object).
   * De `PrintedOutputOptionsSpec` -object dat uitvoeringsopties bevat die zijn vereist voor het afdrukken naar een bestand.
   * De `com.adobe.idp.Document` object dat de XML-gegevensbron bevat die formuliergegevens bevat.

   De `generatePrintedOutput` methode retourneert een `OutputResult` object dat de resultaten van de bewerking bevat.

   >[!NOTE]
   >
   >De `OutputResult` object `getRecordLevelMetaDataList` methode retourneert `null`.

1. Haal de resultaten van de bewerking op.

   * Een `com.adobe.idp.Document` object dat de status van het `generatePrintedOutput` door de `OutputResult` object `getStatusDoc` (de `OutputResult` object is geretourneerd door de `generatePrintedOutput` methode).
   * Een `java.io.File` -object dat de resultaten van de bewerking bevat. Zorg ervoor dat de bestandsextensie XML is.
   * De `com.adobe.idp.Document` object `copyToFile` methode om de inhoud van de `com.adobe.idp.Document` object naar het bestand (gebruik de `com.adobe.idp.Document` object dat is geretourneerd door de `getStatusDoc` methode).

**Zie ook**

[Overzicht van de stappen](creating-document-output-streams.md#summary-of-steps)

[Snel starten (SOAP-modus): afdrukken naar een bestand met de Java API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-printing-to-a-file-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).

### Afdrukken naar bestanden met de webservice-API {#print-to-files-using-the-web-service-api}

Afdrukken naar een bestand met de Output API (webservice):

1. Inclusief projectbestanden.

   Creeer een Microsoft .NET project dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/OutputService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` met het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een Output Client-object.

   * Een `OutputServiceClient` object met de standaardconstructor.
   * Een `OutputServiceClient.Endpoint.Address` object door het `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/OutputService?blob=mtom`.) U hoeft de `lc_version` kenmerk. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt. Geef echter `?blob=mtom` MTOM gebruiken.
   * Een `System.ServiceModel.BasicHttpBinding` object door de waarde van het object op te halen `OutputServiceClient.Endpoint.Binding` veld. De geretourneerde waarde omzetten in `BasicHttpBinding`.
   * Stel de `System.ServiceModel.BasicHttpBinding` object `MessageEncoding` veld naar `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld toe `OutputServiceClient.ClientCredentials.UserName.UserName`.
      * De bijbehorende wachtwoordwaarde aan het veld toewijzen `OutputServiceClient.ClientCredentials.UserName.Password`.
      * De constante waarde toewijzen `HttpClientCredentialType.Basic` naar het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * De constante waarde toewijzen `BasicHttpSecurityMode.TransportCredentialOnly` naar het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Verwijzen naar een XML-gegevensbron.

   * Een `BLOB` object met behulp van de constructor. De `BLOB` wordt gebruikt om formuliergegevens op te slaan.
   * Een `System.IO.FileStream` object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de locatie aangeeft van het XML-bestand dat formuliergegevens bevat.
   * Maak een bytearray waarin de inhoud van de `System.IO.FileStream` object. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` object `Length` eigenschap.
   * De bytearray vullen met streamgegevens door de `System.IO.FileStream` object `Read` en geeft u de bytearray, de startpositie en de streamlengte door die u wilt lezen.
   * Vul de `BLOB` object door het toe te wijzen `binaryData` eigenschap met de inhoud van de bytearray.

1. Stel de runtime-opties voor afdrukken in die nodig zijn om af te drukken naar een bestand.

   * Een `PrintedOutputOptionsSpec` object met behulp van de constructor.
   * Geef het bestand op door een tekenreekswaarde toe te wijzen die de locatie en naam van het bestand vertegenwoordigt voor de `PrintedOutputOptionsSpec` object `fileURI` lid. Als u bijvoorbeeld wilt dat de uitvoerservice wordt afgedrukt naar een PostScript-bestand met de naam *MortgaugeForm.ps* in C:\Adobe: C:\\Adobe\MortgageForm.ps.
   * Geef het aantal exemplaren op dat moet worden afgedrukt door een geheel-getalwaarde toe te wijzen die het aantal exemplaren aan de `PrintedOutputOptionsSpec` object `copies` leden van gegevens.

1. Druk de afdrukstroom naar een bestand af.

   Afdrukken naar een bestand door het `OutputServiceService` object `generatePrintedOutput` en geeft de volgende waarden door:

   * A `PrintFormat` opsommingswaarde die de indeling van de afdrukstroom opgeeft die moet worden gemaakt. Als u bijvoorbeeld een PostScript-afdrukstroom wilt maken, geeft u `PrintFormat.PostScript`.
   * Een tekenreekswaarde waarmee de naam van het formulierontwerp wordt opgegeven.
   * Een tekenreekswaarde die de locatie van verwante secundaire bestanden, zoals afbeeldingsbestanden, opgeeft.
   * Een tekenreekswaarde die de locatie aangeeft van het XDC-bestand dat moet worden gebruikt (u kunt doorgeven `null` als u het XDC-bestand hebt opgegeven om te gebruiken met de `PrintedOutputOptionsSpec` object).
   * De `PrintedOutputOptionsSpec` -object dat afdrukopties bevat die vereist zijn voor het afdrukken naar een bestand.
   * De `BLOB` object dat de XML-gegevensbron bevat die formuliergegevens bevat.
   * A `BLOB` object dat wordt gevuld door het `generatePDFOutput` methode. De `generatePDFOutput` Hiermee wordt dit object gevuld met gegenereerde metagegevens die het document beschrijven. (Deze parameterwaarde is alleen vereist voor aanroepen van webservices.)
   * A `BLOB` object dat wordt gevuld door het `generatePDFOutput` methode. De `generatePDFOutput` Hiermee wordt dit object gevuld met resultaatgegevens. (Deze parameterwaarde is alleen vereist voor aanroepen van webservices.)
   * An `OutputResult` object dat de resultaten van de bewerking bevat. (Deze parameterwaarde is alleen vereist voor aanroepen van webservices.)

1. Haal de resultaten van de bewerking op.

   * Een `System.IO.FileStream` object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die een locatie vertegenwoordigt van een XML-bestand dat resultaatgegevens bevat. Zorg ervoor dat de bestandsextensie XML is.
   * Maak een bytearray waarin de gegevensinhoud van de `BLOB` object dat is gevuld met resultaatgegevens door de `OutputServiceService` object `generatePDFOutput` methode (de achtste parameter). Vul de bytearray met de waarde van de `BLOB` object `MTOM` lid.
   * Een `System.IO.BinaryWriter` object door de constructor aan te roepen en de `System.IO.FileStream` object.
   * Schrijf de inhoud van de bytearray naar het XML-bestand door het `System.IO.BinaryWriter` object `Write` en geeft u de bytearray door.

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
>Voor meer informatie over de dienst van de Output, zie [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

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
* adobe-utilities.jar (Vereist als AEM Forms wordt geïmplementeerd op JBoss)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)

als AEM Forms wordt geïmplementeerd op een ondersteunde J2EE-toepassingsserver die geen JBoss is, moet u de bestanden adobe-utilities.jar en jbossall-client.jar vervangen door JAR-bestanden die specifiek zijn voor de J2EE-toepassingsserver waarop AEM Forms wordt geïmplementeerd.

**Een Output Client-object maken**

Voordat u programmatisch een uitvoerservicebewerking kunt uitvoeren, maakt u een uitvoerservice-clientobject. Als u de Java API gebruikt, maakt u een `OutputClient` object. Als u de uitvoerwebservice-API gebruikt, maakt u een `OutputServiceClient` object.

**Verwijzen naar een XML-gegevensbron**

Als u een document wilt afdrukken dat gegevens bevat, moet u verwijzen naar een XML-gegevensbron die XML-elementen bevat voor elk formulierveld dat u wilt vullen met gegevens. De naam van het XML-element moet overeenkomen met de veldnaam. Een XML-element wordt genegeerd als het niet overeenkomt met een formulierveld of als de naam van het XML-element niet overeenkomt met de veldnaam. Het is niet nodig de volgorde aan te passen waarin de XML-elementen worden weergegeven als alle XML-elementen zijn opgegeven.

**Uitvoeropties voor afdrukken instellen**

U kunt de runtime-opties instellen wanneer u een afdrukstroom naar een printer verzendt, inclusief de volgende opties:

* **Exemplaren**: Geeft het aantal exemplaren op dat naar de printer moet worden verzonden. De standaardwaarde is 1.
* **Stapel**: Een optie XCI wordt geplaatst wanneer een nietmachine wordt gebruikt. Deze optie kan in het configuratiemodel door het belangrijkste element worden gespecificeerd en wordt gebruikt voor printers PS en PCL slechts.
* **OutputJog**: Er wordt een XCI-optie ingesteld wanneer uitvoerpagina&#39;s moeten worden samengevoegd (fysiek verschoven in de uitvoerlade). Deze optie geldt alleen voor PS- en PCL-printers.
* **Uitvoerbak**: XCI-waarde die wordt gebruikt om het afdrukstuurprogramma in staat te stellen de juiste uitvoerlade te selecteren.

>[!NOTE]
>
>Voor informatie over alle runtime opties die u kunt instellen, raadpleegt u de `PrintedOutputOptionsSpec` klasseverwijzing.

**Een af te drukken document ophalen**

Haal een afdrukstroom op die u naar een printer wilt verzenden. U kunt bijvoorbeeld een PostScript-bestand ophalen en naar een printer verzenden.

U kunt ervoor kiezen een PDF-bestand te verzenden als uw printer PDF ondersteunt. Een probleem bij het verzenden van een PDF-document naar een printer is echter dat elke printerfabrikant een andere implementatie van de PDF-interpreter heeft. Dat wil zeggen dat sommige afdrukfabrikanten Adobe PDF-interpretatie gebruiken, maar dat hangt van de printer af. Andere drukkers hebben hun eigen PDF-interpreter. Hierdoor kunnen de afdrukresultaten afwijken.

Een andere beperking bij het verzenden van een PDF-document naar een printer is dat het alleen wordt afgedrukt; het heeft geen toegang tot de duplex-, papierlade- en nietfunctie, behalve via de printerinstellingen.

Als u een document wilt ophalen dat u wilt afdrukken, gebruikt u de opdracht `generatePrintedOutput` methode. In de volgende tabel worden de inhoudstypen aangegeven die voor een bepaalde afdrukstroom zijn ingesteld wanneer u de `generatePrintedOutput` methode.

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
>U kunt ook een afdrukstroom naar een printer verzenden met de opdracht `generatePrintedOutput2` methode. Maar de snelle start die gepaard gaat met het verzenden van de sectie Afdrukstromen naar printers, gebruikt de opdracht `generatePrintedOutput` methode.

**De afdrukstroom naar een netwerkprinter verzenden**

Nadat u een document hebt opgehaald om af te drukken, kunt u de service Uitvoer inschakelen, waardoor er een afdrukstroom naar een netwerkprinter wordt verzonden. Als u de printer wilt vinden in de uitvoerservice, moet u zowel de afdrukserver als de printernaam opgeven. Daarnaast moet u ook het afdrukprotocol opgeven.

>[!NOTE]
>
>Als PDFG op de Server van Forms en de serverlooppas op de Server 2008 van Vensters wordt geïnstalleerd, kunt u niet het bezit SharedPrinter gebruiken. In deze situatie, gebruik een verschillend printerprotocol.

>[!NOTE]
>
>Als u een netwerkprinter gebruikt en het toegangsmechanisme SharedPrinter is, moet u het volledige netwerkpad van de printer opgeven.Een afdrukstroom naar een netwerkprinter verzenden met de Java API

Een afdrukstream naar een netwerkprinter verzenden met de Output API (Java):

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-output-client.jar, op in het klassenpad van uw Java-project.

1. Een Output Client-object maken

   * Een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Een `OutputClient` object door de constructor ervan te gebruiken en de `ServiceClientFactory` object.

1. Verwijzen naar een XML-gegevensbron

   * Een `java.io.FileInputStream` object dat de XML-gegevensbron vertegenwoordigt die wordt gebruikt om het document te vullen met de constructor ervan en die een tekenreekswaarde doorgeeft die de locatie van het XML-bestand aangeeft.
   * Een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en de `java.io.FileInputStream` object.

1. Uitvoeropties voor afdrukken instellen

   Een `PrintedOutputOptionsSpec` -object dat afdrukopties tijdens runtime vertegenwoordigt. U kunt bijvoorbeeld het aantal exemplaren opgeven dat moet worden afgedrukt door het `PrintedOutputOptionsSpec` object `setCopies` methode.

   >[!NOTE]
   >
   >U kunt de pagineringswaarde niet instellen met de opdracht `PrintedOutputOptionsSpec` object `setPagination` als u een ZPL-afdrukstroom genereert. Op dezelfde manier kunt u de volgende opties voor een ZPL-afdrukstroom niet instellen: OutputJog, PageOffset en Stapel. De `setPagination` methode is niet geldig voor het genereren van PostScript. Het is alleen geldig voor PCL-generatie.

1. Een af te drukken document ophalen

   * Een document ophalen om af te drukken door het `OutputClient` object `generatePrintedOutput` en geeft de volgende waarden door:

      * A `PrintFormat` opsommingswaarde die de afdrukstroom opgeeft. Als u bijvoorbeeld een PostScript-afdrukstroom wilt maken, geeft u `PrintFormat.PostScript`.
      * Een tekenreekswaarde waarmee de naam van het formulierontwerp wordt opgegeven.
      * Een tekenreekswaarde die de locatie van verwante secundaire bestanden opgeeft, zoals afbeeldingsbestanden.
      * Een tekenreekswaarde die de locatie aangeeft van het XDC-bestand dat moet worden gebruikt.
      * De `PrintedOutputOptionsSpec` -object dat uitvoeringsopties bevat die vereist zijn om af te drukken naar een bestand.
      * De `com.adobe.idp.Document` object dat staat voor de XML-gegevensbron die formuliergegevens bevat die met het formulierontwerp moeten worden samengevoegd.

     Deze methode retourneert een `OutputResult` object dat de resultaten van de bewerking bevat.

   * Een `com.adobe.idp.Document` object dat naar de printer moet worden verzonden door de `OutputResult` object `getGeneratedDoc` methode. Deze methode retourneert een `com.adobe.idp.Document` object.

1. De afdrukstroom naar een netwerkprinter verzenden

   Verzend de afdrukstroom naar een netwerkprinter door de `OutputClient` object `sendToPrinter` en geeft de volgende waarden door:

   * A `com.adobe.idp.Document` object dat staat voor de afdrukstream die naar de printer moet worden verzonden.
   * A `PrinterProtocol` opsommingswaarde die het te gebruiken printerprotocol aangeeft. Als u bijvoorbeeld het SharedPrinter-protocol wilt opgeven, geeft u `PrinterProtocol.SharedPrinter`.
   * Een tekenreekswaarde die de naam van de afdrukserver opgeeft. Als de naam van de afdrukserver bijvoorbeeld PrintServer1 is, geeft u door `\\\PrintSever1`.
   * Een tekenreekswaarde die de naam van de printer opgeeft. Als de naam van de printer bijvoorbeeld Printer1 is, geeft u door `\\\PrintSever1\Printer1`.

   >[!NOTE]
   >
   >De `sendToPrinter` Deze methode is toegevoegd aan de AEM Forms API in versie 8.2.1.

### Een afdrukstream naar een printer verzenden met de webservice-API {#send-a-print-stream-to-a-printer-using-the-web-service-api}

Een afdrukstroom naar een netwerkprinter verzenden met de Output API (webservice):

1. Inclusief projectbestanden.

   Creeer een Microsoft .NET project dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/OutputService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` met het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een Output Client-object.

   * Een `OutputServiceClient` object met de standaardconstructor.
   * Een `OutputServiceClient.Endpoint.Address` object door het `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/OutputService?blob=mtom`.) U hoeft de `lc_version` kenmerk. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt. Geef echter `?blob=mtom` MTOM gebruiken.
   * Een `System.ServiceModel.BasicHttpBinding` object door de waarde van het object op te halen `OutputServiceClient.Endpoint.Binding` veld. De geretourneerde waarde omzetten in `BasicHttpBinding`.
   * Stel de `System.ServiceModel.BasicHttpBinding` object `MessageEncoding` veld naar `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld toe `OutputServiceClient.ClientCredentials.UserName.UserName`.
      * De bijbehorende wachtwoordwaarde aan het veld toewijzen `OutputServiceClient.ClientCredentials.UserName.Password`.
      * De constante waarde toewijzen `HttpClientCredentialType.Basic` naar het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * De constante waarde toewijzen `BasicHttpSecurityMode.TransportCredentialOnly` naar het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Verwijzen naar een XML-gegevensbron.

   * Een `BLOB` object met behulp van de constructor. De `BLOB` wordt gebruikt om formuliergegevens op te slaan.
   * Een `System.IO.FileStream` object door de constructor ervan aan te roepen. Geef een tekenreekswaarde door die de locatie aangeeft van het XML-bestand dat formuliergegevens bevat.
   * Maak een bytearray waarin de inhoud van de `System.IO.FileStream` object. Bepaal de lengte van de bytearray door de `System.IO.FileStream` object `Length` eigenschap.
   * De bytearray vullen met streamgegevens door de `System.IO.FileStream` object `Read` en geeft u de bytearray, de startpositie en de streamlengte door die u wilt lezen.
   * Vul de `BLOB` object door het toe te wijzen `MTOM` veld met de inhoud van de bytearray.

1. Stel opties voor het uitvoeren van afdrukken in.

   Een `PrintedOutputOptionsSpec` object met behulp van de constructor. U kunt bijvoorbeeld het aantal exemplaren opgeven dat moet worden afgedrukt door een geheel-getalwaarde toe te wijzen die het aantal exemplaren aan het `PrintedOutputOptionsSpec` object `copies` lid.

   >[!NOTE]
   >
   >U kunt de pagineringswaarde niet instellen met de opdracht `PrintedOutputOptionsSpec` object `pagination` gegevenslid als u een ZPL-afdrukstroom genereert. Op dezelfde manier kunt u de volgende opties voor een ZPL-afdrukstroom niet instellen: OutputJog, PageOffset en Stapel. De `pagination` gegevenslid is niet geldig voor het genereren van PostScript. Het is alleen geldig voor PCL-generatie.

1. Een af te drukken document ophalen.

   * Een document ophalen om af te drukken door het `OutputServiceService` object `generatePrintedOutput` en geeft de volgende waarden door:

      * A `PrintFormat` opsommingswaarde die de afdrukstroom opgeeft. Als u bijvoorbeeld een PostScript-afdrukstroom wilt maken, geeft u `PrintFormat.PostScript`.
      * Een tekenreekswaarde waarmee de naam van het formulierontwerp wordt opgegeven.
      * Een tekenreekswaarde die de locatie van verwante secundaire bestanden opgeeft, zoals afbeeldingsbestanden.
      * Een tekenreekswaarde die de locatie aangeeft van het XDC-bestand dat moet worden gebruikt.
      * De `PrintedOutputOptionsSpec` -object dat afdrukopties tijdens runtime bevat die worden gebruikt wanneer een afdrukstroom naar een netwerkprinter wordt verzonden.
      * De `BLOB` object dat de XML-gegevensbron bevat die formuliergegevens bevat.
      * A `BLOB` object dat wordt gevuld door het `generatePrintedOutput` methode. De `generatePrintedOutput` Hiermee wordt dit object gevuld met gegenereerde metagegevens die het document beschrijven. (Deze parameterwaarde is alleen vereist voor aanroepen van webservices.)
      * A `BLOB` object dat wordt gevuld door het `generatePrintedOutput` methode. De `generatePrintedOutput` Hiermee wordt dit object gevuld met resultaatgegevens. (Deze parameterwaarde is alleen vereist voor aanroepen van webservices.)
      * An `OutputResult` object dat de resultaten van de bewerking bevat. (Deze parameterwaarde is alleen vereist voor aanroepen van webservices.)

   * Een `BLOB` object dat naar de printer moet worden verzonden door de waarde van `OutputResult` object `generatedDoc` methode. Deze methode retourneert een `BLOB` object dat PostScript-gegevens bevat die worden geretourneerd door het `generatePrintedOutput` methode.

1. Verzend de afdrukstroom naar een netwerkprinter.

   Verzend de afdrukstroom naar een netwerkprinter door de `OutputClient` object `sendToPrinter` en geeft de volgende waarden door:

   * A `BLOB` object dat staat voor de afdrukstream die naar de printer moet worden verzonden.
   * A `PrinterProtocol` opsommingswaarde die het te gebruiken printerprotocol aangeeft. Als u bijvoorbeeld het SharedPrinter-protocol wilt opgeven, geeft u `PrinterProtocol.SharedPrinter`.
   * A `bool` waarde die aangeeft of de vorige parameterwaarde moet worden gebruikt. Geef de waarde door `true`. (Deze parameterwaarde is alleen vereist voor aanroepen van webservices.)
   * Een tekenreekswaarde die de naam van de afdrukserver opgeeft. Als bijvoorbeeld wordt aangenomen dat de naam van de afdrukserver PrintServer1 is, geeft u door `\\\PrintSever1`.
   * Een tekenreekswaarde die de naam van de printer opgeeft. Als de naam van de printer bijvoorbeeld Printer1 is, geeft u door `\\\PrintSever1\Printer1`.

   >[!NOTE]
   >
   >De `sendToPrinter` Deze methode is toegevoegd aan de AEM Forms API in versie 8.2.1.

## Meerdere uitvoerbestanden maken {#creating-multiple-output-files}

Met de service Uitvoer kunt u aparte documenten maken voor elke record in een XML-gegevensbron of één bestand dat alle records bevat (deze functionaliteit is de standaardinstelling). Bijvoorbeeld, veronderstel dat tien verslagen binnen een gegevensbron van XML worden gevestigd en u de dienst van de Output opdraagt om afzonderlijke documenten van de PDF (of andere soorten output) voor elk verslag tot stand te brengen door de Dienst API van de Output te gebruiken. Als gevolg hiervan genereert de uitvoerservice tien PDF-documenten. (In plaats van documenten te maken, kunt u meerdere afdrukstromen naar een printer verzenden.)

In de volgende afbeelding ziet u ook hoe de uitvoerservice een XML-gegevensbestand verwerkt dat meerdere records bevat. Nochtans, veronderstel dat u de dienst van de Output opdraagt om één enkel document van de PDF tot stand te brengen dat alle gegevensverslagen bevat. In deze situatie genereert de uitvoerservice één document dat alle records bevat.

In de volgende afbeelding ziet u hoe de uitvoerservice een XML-gegevensbestand verwerkt dat meerdere records bevat. Veronderstel dat u de dienst van de Output opdraagt om een afzonderlijk document van PDF voor elk gegevensverslag tot stand te brengen. In dit geval genereert de Output-service een apart PDF-document voor elke gegevensrecord.

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
>Voor meer informatie over de dienst van de Output, zie [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary_of_steps-7}

Voer de volgende stappen uit om meerdere PDF-bestanden te maken op basis van een XML-gegevensbron:

1. Inclusief projectbestanden.
1. Maak een Output Client-object.
1. Verwijzen naar een XML-gegevensbron.
1. Stel PDF-uitvoeringsopties in.
1. Stel renderingopties in.
1. Genereer meerdere PDF-bestanden.
1. Haal de resultaten van de bewerking op.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u de proxybestanden opnemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-output-client.jar
* adobe-utilities.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)

als AEM Forms wordt geïmplementeerd op een ondersteunde J2EE-toepassingsserver die geen JBoss is, moet u de bestanden adobe-utilities.jar en jbossall-client.jar vervangen door JAR-bestanden die specifiek zijn voor de J2EE-toepassingsserver waarop AEM Forms wordt geïmplementeerd.

**Een Output Client-object maken**

Voordat u programmatisch een uitvoerservicebewerking kunt uitvoeren, moet u een uitvoerservice-clientobject maken. Als u de Java API gebruikt, maakt u een `OutputClient` object. Als u de uitvoerwebservice-API gebruikt, maakt u een `OutputServiceService` object.

**Verwijzen naar een XML-gegevensbron**

Verwijs naar een gegevensbron van XML die veelvoudige verslagen bevat. Een XML-element moet worden gebruikt om de gegevensrecords van elkaar te scheiden. In het voorbeeld-XML-gegevensbron dat eerder in deze sectie wordt weergegeven, wordt het XML-element dat gegevensrecords scheidt, bijvoorbeeld benoemd `LoanRecord`.

Een XML-element moet bestaan voor elk formulierveld dat u wilt vullen met gegevens. De naam van het XML-element moet overeenkomen met de veldnaam. Een XML-element wordt genegeerd als het niet overeenkomt met een formulierveld of als de naam van het XML-element niet overeenkomt met de veldnaam. Het is niet nodig de volgorde aan te passen waarin de XML-elementen worden weergegeven als alle XML-elementen zijn opgegeven.

**Opties voor PDF bij uitvoering instellen**

Stel de volgende uitvoeringsopties voor de service Uitvoer in om meerdere bestanden te maken op basis van een XML-gegevensbron:

* **Veel bestanden**: Geeft aan of de service Uitvoer een of meer documenten maakt. U kunt waar of onwaar opgeven. Geef true op als u een afzonderlijk document wilt maken voor elke gegevensrecord in de XML-gegevensbron.
* **Bestands-URI**: Hiermee geeft u de locatie op van de bestanden die de uitvoerservice genereert. Stel bijvoorbeeld dat u C:\\Adobe\forms\Loan.pdf opgeeft. In dit geval maakt de service Uitvoer een bestand met de naam Loan.pdf en wordt het bestand in de map C:\\Adobe\forms geplaatst. Als er meerdere bestanden zijn, zijn de bestandsnamen Loan0001.pdf, Loan0002.pdf, Loan0003.pdf, enzovoort. Als u een bestandslocatie opgeeft, worden de bestanden op de server geplaatst, niet op de clientcomputer.
* **Recordnaam**: Geeft de naam van het XML-element op in de gegevensbron die de gegevensrecords scheidt. In het voorbeeld-XML-gegevensbron dat eerder in deze sectie wordt weergegeven, wordt bijvoorbeeld het XML-element dat gegevensrecords scheidt, aangeroepen `LoanRecord`. (In plaats van de runtime voor opnamen in te stellen, kunt u het niveau opnemen instellen door er een numerieke waarde aan toe te wijzen die het elementniveau aangeeft dat gegevensrecords bevat. U kunt echter alleen de recordnaam of het recordniveau instellen. U kunt niet beide waarden instellen.)

**Renderopties tijdens runtime instellen**

Tijdens het maken van meerdere bestanden kunt u opties voor het renderen tijdens runtime instellen. Hoewel deze opties niet vereist zijn (in tegenstelling tot uitvoeropties, die vereist zijn), kunt u taken uitvoeren zoals het verbeteren van de prestaties van de uitvoerservice. U kunt bijvoorbeeld het formulierontwerp in cache plaatsen dat de uitvoerservice gebruikt om de prestaties te verbeteren.

Wanneer de dienst van de Output partijverslagen verwerkt, leest het gegevens die veelvoudige verslagen op een stijgende manier bevatten. Dat wil zeggen dat de Output-service de gegevens in het geheugen leest en de gegevens vrijgeeft terwijl de batch met records wordt verwerkt. De uitvoerservice laadt gegevens incrementeel wanneer een van de twee uitvoeringsopties is ingesteld. Als u de runtime van de Naam van het Verslag optie plaatst, leest de dienst van de Output gegevens op een stijgende manier. Op dezelfde manier, als u de runtime van het Niveau van het Verslag optie aan 2 of groter plaatst, leest de dienst van de Output gegevens op een stijgende manier.

U kunt bepalen of de dienst van de Output stijgende lading door te gebruiken uitvoert `PDFOutputOptionsSpec` of de `PrintedOutputOptionSpec` object `setLazyLoading` methode. U kunt de waarde doorgeven `false` op deze methode waarmee incrementele belasting wordt uitgeschakeld.

**Meerdere PDF-bestanden genereren**

Nadat u naar een geldige XML-gegevensbron verwijst die meerdere gegevensrecords bevat en runtime-opties instelt, kunt u de uitvoerservice aanroepen, waardoor er meerdere bestanden worden gegenereerd. Wanneer het produceren van veelvoudige verslagen, `OutputResult` object `getGeneratedDoc` methode retourneert `null`.

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

   Neem client-JAR-bestanden, zoals adobe-output-client.jar, op in het klassenpad van uw Java-project.

1. Een Output Client-object maken

   * Een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Een `OutputClient` object door de constructor ervan te gebruiken en de `ServiceClientFactory` object.

1. Verwijzen naar een XML-gegevensbron

   * Een `java.io.FileInputStream` object dat de XML-gegevensbron vertegenwoordigt die meerdere records bevat door de constructor ervan te gebruiken en een tekenreekswaarde door te geven die de locatie van het XML-bestand aangeeft.
   * Een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en de `java.io.FileInputStream` object.

1. Opties voor PDF bij uitvoering instellen

   * Een `PDFOutputOptionsSpec` object met behulp van de constructor.
   * Stel de optie Veel bestanden in door de `PDFOutputOptionsSpec` object `setGenerateManyFiles` methode. Geef bijvoorbeeld de waarde door `true` om de Output-service op te dragen een afzonderlijk PDF-bestand te maken voor elke record in de XML-gegevensbron. (Als u `false`, genereert de uitvoerservice één PDF-document dat alle records bevat).
   * Stel de optie File URI in door het `PDFOutputOptionsSpec` object `setFileUri` methode en het overgaan van een koordwaarde die de plaats van de dossiers specificeert die de dienst van de Output produceert. De optie File URI is relatief ten opzichte van de J2EE-toepassingsserver die als host fungeert voor AEM Forms, niet ten opzichte van de clientcomputer.
   * Stel de optie Naam record in door de `OutputOptionsSpec` object `setRecordName` methode en het overgaan van een koordwaarde die de het elementnaam van XML in de gegevensbron specificeert die de gegevensverslagen scheidt. (Neem bijvoorbeeld de XML-gegevensbron die eerder in deze sectie wordt weergegeven. De naam van het XML-element dat gegevensrecords scheidt, is LoanRecord.)

1. Renderopties tijdens runtime instellen

   * Een `RenderOptionsSpec` object met behulp van de constructor.
   * Plaats het formulierontwerp in de cache om de prestaties van de uitvoerservice te verbeteren door het aanroepen van de `RenderOptionsSpec` object `setCacheEnabled` en door te geven `Boolean` waarde van `true`.

1. Meerdere PDF-bestanden genereren

   Genereer meerdere PDF-bestanden door de `OutputClient` object `generatePDFOutput` en geeft de volgende waarden door:

   * A `TransformationFormat` enum value. Als u een PDF-document wilt genereren, geeft u `TransformationFormat.PDF`.
   * Een tekenreekswaarde waarmee de naam van het formulierontwerp wordt opgegeven.
   * Een tekenreekswaarde die de hoofdmap van de inhoud opgeeft waar het formulierontwerp zich bevindt.
   * A `PDFOutputOptionsSpec` -object dat PDF-runtime-opties bevat.
   * A `RenderOptionsSpec` -object dat renderingopties bevat.
   * De `com.adobe.idp.Document` object dat de XML-gegevensbron bevat die gegevens bevat die met het formulierontwerp moeten worden samengevoegd.

   De `generatePDFOutput` methode retourneert een `OutputResult` object dat de resultaten van de bewerking bevat.

1. De resultaten van de bewerking ophalen

   * Een `java.io.File` object dat een XML-bestand vertegenwoordigt dat de resultaten van het `generatePDFOutput` methode. Controleer of de bestandsnaamextensie .xml is.
   * De `com.adobe.idp.Document` object `copyToFile` methode om de inhoud van de `com.adobe.idp.Document` object naar het bestand (gebruik de `com.adobe.idp.Document` object dat is geretourneerd door de `applyUsageRights` methode).

**Zie ook**

[Overzicht van de stappen](creating-document-output-streams.md#summary-of-steps)

[Snel starten (EJB-modus): meerdere PDF-bestanden maken met de Java API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-multiple-pdf-files-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Meerdere PDF-bestanden maken met de webservice-API {#create-multiple-pdf-files-using-the-web-service-api}

Meerdere PDF-bestanden maken met de Output API (webservice):

1. Inclusief projectbestanden.

   Creeer een Microsoft .NET project dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/OutputService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` met het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een Output Client-object.

   * Een `OutputServiceClient` object met de standaardconstructor.
   * Een `OutputServiceClient.Endpoint.Address` object door het `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/OutputService?blob=mtom`.) U hoeft de `lc_version` kenmerk. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt. Geef echter `?blob=mtom` MTOM gebruiken.
   * Een `System.ServiceModel.BasicHttpBinding` object door de waarde van het object op te halen `OutputServiceClient.Endpoint.Binding` veld. De geretourneerde waarde omzetten in `BasicHttpBinding`.
   * Stel de `System.ServiceModel.BasicHttpBinding` object `MessageEncoding` veld naar `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld toe `OutputServiceClient.ClientCredentials.UserName.UserName`.
      * De bijbehorende wachtwoordwaarde aan het veld toewijzen `OutputServiceClient.ClientCredentials.UserName.Password`.
      * De constante waarde toewijzen `HttpClientCredentialType.Basic` naar het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * De constante waarde toewijzen `BasicHttpSecurityMode.TransportCredentialOnly` naar het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Verwijzen naar een XML-gegevensbron.

   * Een `BLOB` object met behulp van de constructor. De `BLOB` wordt gebruikt om formuliergegevens op te slaan die meerdere records bevatten.
   * Een `System.IO.FileStream` object door de constructor ervan aan te roepen. Geef een tekenreekswaarde door die de bestandslocatie vertegenwoordigt van het XML-bestand dat meerdere records bevat.
   * Maak een bytearray waarin de inhoud van de `System.IO.FileStream` object. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` object `Length` eigenschap.
   * De bytearray vullen met streamgegevens door de `System.IO.FileStream` object `Read` en geeft u de bytearray, de startpositie en de streamlengte door die u wilt lezen.
   * Vul de `BLOB` object door het toe te wijzen `MTOM` veld met de inhoud van de bytearray.

1. Stel PDF-uitvoeringsopties in.

   * Een `PDFOutputOptionsSpec` object met behulp van de constructor.
   * Stel de optie Veel bestanden in door een Booleaanse waarde toe te wijzen aan de optie `OutputOptionsSpec` object `generateManyFiles` lid. Wijs bijvoorbeeld de waarde toe `true` aan dit gegevenslid om de dienst van de Output op te dragen om een afzonderlijk dossier van PDF voor elke verslag in de gegevensbron van XML tot stand te brengen. (Als u `false` aan dit gegevenslid, dan produceert de dienst van de Output één enkele PDF die alle verslagen bevat).
   * Stel de bestands-URI-optie in door een tekenreekswaarde toe te wijzen die de locatie opgeeft van de bestanden die de uitvoerservice genereert voor de `OutputOptionsSpec` object `fileURI` lid. De optie File URI is relatief ten opzichte van de J2EE-toepassingsserver die als host fungeert voor AEM Forms, niet ten opzichte van de clientcomputer.
   * Stel de optie voor de recordnaam in door een tekenreekswaarde toe te wijzen die de naam van het XML-element opgeeft in de gegevensbron die de gegevensrecords scheidt van de `OutputOptionsSpec` object `recordName` lid.
   * Stel de optie Kopiëren in door een geheel-getalwaarde toe te wijzen die het aantal exemplaren opgeeft dat de uitvoerservice genereert voor de `OutputOptionsSpec` object `copies` lid.

1. Stel renderingopties in.

   * Een `RenderOptionsSpec` object met behulp van de constructor.
   * Plaats het formulierontwerp in de cache om de prestaties van de uitvoerservice te verbeteren door de waarde toe te wijzen `true` aan de `RenderOptionsSpec` object `cacheEnabled` lid.

1. Genereer meerdere PDF-bestanden.

   Meerdere PDF-bestanden maken door de `OutputServiceService` object `generatePDFOutput`en geeft de volgende waarden door:

   * Een opsommingswaarde van TransformationFormat. Als u een PDF-document wilt genereren, geeft u `TransformationFormat.PDF`.
   * Een tekenreekswaarde waarmee de naam van het formulierontwerp wordt opgegeven.
   * Een tekenreekswaarde die de hoofdmap van de inhoud opgeeft waar het formulierontwerp zich bevindt.
   * A `PDFOutputOptionsSpec` -object dat PDF-runtime-opties bevat.
   * A `RenderOptionsSpec` -object dat renderingopties bevat.
   * De `BLOB` object dat de XML-gegevensbron bevat die gegevens bevat die met het formulierontwerp moeten worden samengevoegd.
   * A `BLOB` object dat wordt gevuld door het `generatePDFOutput` methode. De `generatePDFOutput` Hiermee wordt dit object gevuld met gegenereerde metagegevens die het document beschrijven.
   * A `BLOB` object dat wordt gevuld door het `generatePDFOutput` methode. De `generatePDFOutput` Hiermee wordt dit object gevuld met resultaatgegevens.
   * An `OutputResult` object dat de resultaten van de bewerking bevat.

1. De resultaten van de bewerking ophalen

   * Een `System.IO.FileStream` object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die een locatie vertegenwoordigt van een XML-bestand dat resultaatgegevens bevat. Controleer of de bestandsnaamextensie .xml is.
   * Maak een bytearray waarin de gegevensinhoud van de `BLOB` object dat is gevuld met resultaatgegevens door de `OutputServiceService` object `generatePDFOutput` methode (de achtste parameter). Vul de bytearray met de waarde van de `BLOB` object `binaryData` lid.
   * Een `System.IO.BinaryWriter` object door de constructor aan te roepen en de `System.IO.FileStream` object.
   * Schrijf de inhoud van de bytearray naar het XML-bestand door het `System.IO.BinaryWriter` object `Write` en geeft u de bytearray door.

**Zie ook**

[Overzicht van de stappen](creating-document-output-streams.md#summary-of-steps)

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Zoekregels maken {#creating-search-rules}

U kunt zoekregels maken die ertoe leiden dat de uitvoerservice invoergegevens controleert en verschillende formulierontwerpen gebruikt op basis van de gegevensinhoud om uitvoer te genereren. Als de tekst *hypotheek* bevindt zich binnen de invoergegevens, kan de uitvoerservice een formulierontwerp gebruiken met de naam Mortgauge.xdp. En als de tekst *auto* bevindt zich in de invoergegevens, kan de uitvoerservice een formulierontwerp gebruiken dat is opgeslagen als AutomobileLoan.xdp. Hoewel de Output-service verschillende uitvoertypen kan genereren, wordt er in deze sectie van uitgegaan dat de Output-service een PDF-bestand genereert. In het volgende diagram ziet u de service Output die een PDF-bestand genereert door een XML-gegevensbestand te verwerken en een van de vele formulierontwerpen te gebruiken.

Daarnaast kan de Output-service documentpakketten genereren, waarbij de gegevensset meerdere records bevat en elke record overeenkomt met een formulierontwerp en er één document wordt gegenereerd dat uit meerdere formulierontwerpen bestaat.

![cs_outputbatchmanyformdesigns2](assets/cs_outputbatchmanyformdesigns2.png)

>[!NOTE]
>
>Voor meer informatie over de dienst van de Output, zie [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary_of_steps-8}

Voer de volgende stappen uit om de uitvoerservice op te dragen de zoekregels te gebruiken tijdens het genereren van een document:

1. Inclusief projectbestanden.
1. Maak een Output Client-object.
1. Verwijzen naar een XML-gegevensbron.
1. Definieer zoekregels.
1. Stel PDF-uitvoeringsopties in.
1. Stel renderingopties in.
1. Een PDF-document genereren.
1. Haal de resultaten van de bewerking op.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u ervoor zorgen dat u de proxybestanden opneemt.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-output-client.jar
* adobe-utilities.jar (Vereist als AEM Forms wordt geïmplementeerd op JBoss)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)

als AEM Forms wordt geïmplementeerd op een ondersteunde J2EE-toepassingsserver die geen JBoss is, moet u adobe-utilities.jar en jbossall-client.jar vervangen door JAR-bestanden die specifiek zijn voor de J2EE-toepassingsserver waarop AEM Forms wordt geïmplementeerd.

**Een Output Client-object maken**

Voordat u programmatisch een uitvoerservicebewerking kunt uitvoeren, moet u een uitvoerservice-clientobject maken.

**Verwijzen naar een XML-gegevensbron**

Een XML-element moet bestaan voor elk formulierveld dat u wilt vullen met gegevens. De naam van het XML-element moet overeenkomen met de veldnaam. Een XML-element wordt genegeerd als het niet overeenkomt met een formulierveld of als de naam van het XML-element niet overeenkomt met de veldnaam. Het is niet nodig de volgorde aan te passen waarin de XML-elementen worden weergegeven, zolang alle XML-elementen zijn opgegeven.

**Zoekregels definiëren**

Als u zoekregels wilt definiëren, definieert u een of meer tekstpatronen waarnaar de uitvoerservices zoeken in de invoergegevens. Voor elk tekstpatroon dat u definieert, geeft u een corresponderend formulierontwerp op dat wordt gebruikt als het tekstpatroon zich bevindt. Als een tekstpatroon wordt gevonden, gebruikt de uitvoerservice het bijbehorende formulierontwerp om de uitvoer te genereren. Een voorbeeld van een tekstpatroon is *hypotheek*.

>[!NOTE]
>
>Als tekstpatronen niet worden gevonden, wordt het standaardformulier gebruikt. Zorg ervoor dat alle formulierontwerpen die u gebruikt, zich in de basisinhoud bevinden.

**Opties voor PDF bij uitvoering instellen**

Stel de volgende PDF runtime-opties in zodat de Output-service een PDF-document kan maken dat is gebaseerd op meerdere formulierontwerpen:

* **Bestands-URI**: Hiermee geeft u de naam en locatie op van het PDF-bestand dat door de uitvoerservice wordt gegenereerd.
* **Regels**: Geeft de regels op die u hebt gedefinieerd.
* **LookAHead**: Geeft het aantal bytes op dat vanaf het begin van het invoergegevensbestand moet worden gebruikt om te scannen naar de gedefinieerde tekstpatronen. De standaardwaarde is 500 bytes.

**Renderopties tijdens runtime instellen**

Tijdens het maken van PDF-bestanden kunt u renderingopties instellen. Hoewel deze opties niet vereist zijn (in tegenstelling tot PDF runtime opties), kunt u taken uitvoeren zoals het verbeteren van de prestaties van de Output-service. U kunt bijvoorbeeld het formulierontwerp in cache plaatsen dat de uitvoerservice gebruikt om de prestaties te verbeteren.

**Een PDF-document genereren**

Nadat u naar een geldige XML-gegevensbron verwijst en runtime-opties hebt ingesteld, kunt u de uitvoerservice aanroepen, waardoor een PDF-document wordt gegenereerd. Als de uitvoerservice een opgegeven tekstpatroon opzoekt in de invoergegevens, wordt het bijbehorende formulierontwerp gebruikt. Als geen tekstpatroon wordt gebruikt, gebruikt de Output-service het standaardformulierontwerp.

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

   * Een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Een `OutputClient` object door de constructor ervan te gebruiken en de `ServiceClientFactory` object.

1. Verwijzen naar een XML-gegevensbron.

   * Een `java.io.FileInputStream` object dat de XML-gegevensbron vertegenwoordigt die wordt gebruikt om het PDF-document te vullen met de constructor ervan en die een tekenreekswaarde doorgeeft die de locatie van het XML-bestand aangeeft.
   * Een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en de `java.io.FileInputStream` object.

1. Definieer zoekregels.

   * Een `Rule` object met behulp van de constructor.
   * Een tekstpatroon definiëren door het `Rule` object `setPattern` methode en het overgaan van een koordwaarde die een tekstpatroon specificeert.
   * Definieer het bijbehorende formulierontwerp door het `Rule` object `setForm` methode. Geef een tekenreekswaarde door die de naam van het formulierontwerp aangeeft.

   >[!NOTE]
   >
   >Herhaal de vorige drie substappen voor elk tekstpatroon dat u wilt definiëren.

   * Een `java.util.List` object door een `java.util.ArrayList` constructor.
   * Voor elke `Rule` het object dat u hebt gemaakt, activeert het `java.util.List` object `add` en geeft de `Rule` object.

1. Stel PDF-uitvoeringsopties in.

   * Een `PDFOutputOptionsSpec` object met behulp van de constructor.
   * Geef de naam en locatie op van het PDF-bestand dat de uitvoerservice genereert door het `PDFOutputOptionsSpec` object `setFileURI` methode. Geef een tekenreekswaarde door die de locatie van het PDF-bestand aangeeft. De optie File URI is relatief ten opzichte van de J2EE-toepassingsserver die als host fungeert voor AEM Forms, niet ten opzichte van de clientcomputer.
   * Stel de regels in die u hebt gedefinieerd door de `PDFOutputOptionsSpec` object `setRules` methode. Geef de `java.util.List` object dat het `Rule` objecten.
   * Stel het aantal bytes in dat u wilt scannen voor de gedefinieerde tekstpatronen door het aanroepen van de `PDFOutputOptionsSpec` object `setLookAhead` methode. Geef een geheel getal door dat het aantal bytes vertegenwoordigt.

1. Stel renderingopties in.

   * Een `RenderOptionsSpec` object met behulp van de constructor.
   * Plaats het formulierontwerp in de cache om de prestaties van de uitvoerservice te verbeteren door het aanroepen van de `RenderOptionsSpec` object `setCacheEnabled` en passeren `true`.

1. Een PDF-document genereren.

   Een PDF-document genereren dat is gebaseerd op meerdere formulierontwerpen door het aanroepen van de `OutputClient` object `generatePDFOutput` en geeft de volgende waarden door:

   * A `TransformationFormat` opsommingswaarde. Als u een PDF-document wilt genereren, geeft u `TransformationFormat.PDF`.
   * Een tekenreekswaarde die de naam van het standaardformulierontwerp aangeeft. Dit is het formulierontwerp dat wordt gebruikt als een tekstpatroon niet wordt gevonden.
   * Een tekenreekswaarde die de hoofdmap van de inhoud opgeeft waar de formulierontwerpen zich bevinden.
   * A `PDFOutputOptionsSpec` -object dat PDF-runtime-opties bevat.
   * A `RenderOptionsSpec` -object dat renderingopties bevat.
   * De `com.adobe.idp.Document` -object dat de formuliergegevens bevat die door de uitvoerservice worden doorzocht op de gedefinieerde tekstpatronen.

   De `generatePDFOutput` methode retourneert een `OutputResult` object dat de resultaten van de bewerking bevat.

1. Haal de resultaten van de bewerking op.

   * Een `com.adobe.idp.Document` object dat de status van het `generatePDFOutput` door de `OutputResult` object `getStatusDoc` methode.
   * Een `java.io.File` -object dat de resultaten van de bewerking bevat. Controleer of de bestandsextensie .xml is.
   * De `com.adobe.idp.Document` object `copyToFile` methode om de inhoud van de `com.adobe.idp.Document` object naar het bestand (gebruik de `com.adobe.idp.Document` object dat is geretourneerd door de `getStatusDoc` methode).

**Zie ook**

[Overzicht van de stappen](creating-document-output-streams.md#summary-of-steps)

[Snel starten (EJB-modus): zoekregels maken met de Java API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-search-rules-using-the-java-api)

[Snel starten (SOAP-modus): zoekregels maken met de Java API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-creating-search-rules-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Zoekregels maken met de webservice-API {#create-search-rules-using-the-web-service-api}

Maak zoekregels met de Output API (webservice):

1. Inclusief projectbestanden.

   Creeer een Microsoft .NET project dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/OutputService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` met het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een Output Client-object.

   * Een `OutputServiceClient` object met de standaardconstructor.
   * Een `OutputServiceClient.Endpoint.Address` object door het `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/OutputService?blob=mtom`.) U hoeft de `lc_version` kenmerk. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt. Geef echter `?blob=mtom` MTOM gebruiken.
   * Een `System.ServiceModel.BasicHttpBinding` object door de waarde van het object op te halen `OutputServiceClient.Endpoint.Binding` veld. De geretourneerde waarde omzetten in `BasicHttpBinding`.
   * Stel de `System.ServiceModel.BasicHttpBinding` object `MessageEncoding` veld naar `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld toe `OutputServiceClient.ClientCredentials.UserName.UserName`.
      * De bijbehorende wachtwoordwaarde aan het veld toewijzen `OutputServiceClient.ClientCredentials.UserName.Password`.
      * De constante waarde toewijzen `HttpClientCredentialType.Basic` naar het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * De constante waarde toewijzen `BasicHttpSecurityMode.TransportCredentialOnly` naar het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Verwijzen naar een XML-gegevensbron.

   * Een `BLOB` object met behulp van de constructor. De `BLOB` wordt gebruikt om gegevens op te slaan die met het PDF-document worden samengevoegd.
   * Een `System.IO.FileStream` -object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie vertegenwoordigt van het te coderen PDF-document en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van de `System.IO.FileStream` object. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` object `Length` eigenschap.
   * De bytearray vullen met streamgegevens door de `System.IO.FileStream` object `Read` en geeft u de bytearray, de startpositie en de streamlengte door die u wilt lezen.
   * Vul de `BLOB` object door het toe te wijzen `MTOM` veld met de inhoud van de bytearray.

1. Definieer zoekregels.

   * Een `Rule` object met behulp van de constructor.
   * Definieer een tekstpatroon door een tekenreekswaarde toe te wijzen die een tekstpatroon opgeeft voor het `Rule` object `pattern` lid.
   * Definieer het bijbehorende formulierontwerp door een tekenreekswaarde toe te wijzen die het formulierontwerp opgeeft aan de `Rule` object `form` lid.

   >[!NOTE]
   >
   >Herhaal de vorige drie substappen voor elk tekstpatroon dat u wilt definiëren.

   * Een `MyArrayOf_xsd_anyType` -object dat de regels opslaat.
   * Elke waarde toewijzen `Rule` een object naar een element van het `MyArrayOf_xsd_anyType` array. De `MyArrayOf_xsd_anyType` object `Add` methode voor elke `Rule` object.

1. Opties voor PDF bij uitvoering instellen

   * Een `PDFOutputOptionsSpec` object met behulp van de constructor.
   * Stel de bestands-URI-optie in door een tekenreekswaarde toe te wijzen die de locatie opgeeft van het PDF-bestand dat de uitvoerservice genereert voor de `PDFOutputOptionsSpec` object `fileURI` lid. De optie File URI is relatief ten opzichte van de J2EE-toepassingsserver die als host fungeert voor AEM Forms, niet ten opzichte van de clientcomputer.
   * Stel de optie Kopiëren in door een geheel-getalwaarde toe te wijzen die het aantal exemplaren opgeeft dat de uitvoerservice genereert voor de `PDFOutputOptionsSpec` object `copies` lid.
   * Stel de regels in die u hebt gedefinieerd door de `MyArrayOf_xsd_anyType` object dat de regels opslaat in het dialoogvenster `PDFOutputOptionsSpec` object `rules` lid.
   * Stel het aantal bytes in dat u wilt scannen voor de gedefinieerde tekstpatronen door een geheel-getalwaarde toe te wijzen die het aantal bytes vertegenwoordigt dat u wilt scannen naar de `PDFOutputOptionsSpec` object `lookAhead` gegevensmethode.

1. Renderopties tijdens runtime instellen

   * Een `RenderOptionsSpec` object met behulp van de constructor.
   * Plaats het formulierontwerp in de cache om de prestaties van de uitvoerservice te verbeteren door de waarde toe te wijzen `true` aan de `RenderOptionsSpec` object `cacheEnabled` lid.

   >[!NOTE]
   >
   >U kunt de versie van het PDF-document niet instellen met de opdracht `RenderOptionsSpec` object `pdfVersion` lid als het invoerdocument een Acrobat-formulier is. In het PDF-uitvoerdocument blijft de PDF-versie van het Acrobat-formulier behouden. U kunt ook de optie PDF met tags niet instellen met de opdracht `RenderOptionsSpec` object `taggedPDF` methode als het invoerdocument een Acrobat-formulier is.

   >[!NOTE]
   >
   >U kunt de optie Lineaire PDF niet instellen met de opdracht `RenderOptionsSpec` object `linearizedPDF` lid als het invoerdocument PDF is gecertificeerd of digitaal is ondertekend. Zie voor meer informatie [PDF-documenten digitaal ondertekenen](/help/forms/developing/digitally-signing-certifying-documents.md#digitally-signing-pdf-documents).

1. Een PDF-document genereren

   Een PDF-document maken door het `OutputServiceService` object `generatePDFOutput`en geeft de volgende waarden door:

   * A `TransformationFormat` opsommingswaarde. Als u een PDF-document wilt genereren, geeft u `TransformationFormat.PDF`.
   * Een tekenreekswaarde waarmee de naam van het formulierontwerp wordt opgegeven.
   * Een tekenreekswaarde die de hoofdmap van de inhoud opgeeft waar het formulierontwerp zich bevindt.
   * A `PDFOutputOptionsSpec` -object dat PDF-runtime-opties bevat.
   * A `RenderOptionsSpec` -object dat renderingopties bevat.
   * De `BLOB` object dat de XML-gegevensbron bevat die gegevens bevat die met het formulierontwerp moeten worden samengevoegd.
   * A `BLOB` object dat wordt gevuld door het `generatePDFOutput` methode. De `generatePDFOutput` Hiermee wordt dit object gevuld met gegenereerde metagegevens die het document beschrijven. (Deze parameterwaarde is alleen vereist voor aanroepen van een webservice.)
   * A `BLOB` object dat wordt gevuld door het `generatePDFOutput` methode. De `generatePDFOutput` Hiermee wordt dit object gevuld met resultaatgegevens. (Deze parameterwaarde is alleen vereist voor aanroepen van een webservice.)
   * An `OutputResult` object dat de resultaten van de bewerking bevat. (Deze parameterwaarde is alleen vereist voor aanroepen van een webservice.)

   >[!NOTE]
   >
   >Wanneer het produceren van een document van de PDF door te halen `generatePDFOutput` U kunt geen gegevens samenvoegen met een XFA PDF-formulier dat is ondertekend, gecertificeerd of gebruiksrechten bevat. Voor informatie over gebruiksrechten raadpleegt u [Gebruiksrechten toepassen op PDF-documenten](/help/forms/developing/assigning-usage-rights.md#applying-usage-rights-to-pdf-documents).

1. De resultaten van de bewerking ophalen

   * Een `System.IO.FileStream` object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die een locatie vertegenwoordigt van een XML-bestand dat resultaatgegevens bevat. Zorg ervoor dat de bestandsextensie XML is.
   * Maak een bytearray waarin de gegevensinhoud van de `BLOB` object dat is gevuld met resultaatgegevens door de `OutputServiceService` object `generatePDFOutput` methode (de achtste parameter). Vul de bytearray met de waarde van de `BLOB` object `MTOM` lid.
   * Een `System.IO.BinaryWriter` object door de constructor aan te roepen en de `System.IO.FileStream` object.
   * Schrijf de inhoud van de bytearray naar het XML-bestand door het `System.IO.BinaryWriter` object `Write` en geeft u de bytearray door.

**Zie ook**

[Overzicht van de stappen](creating-document-output-streams.md#summary-of-steps)

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## PDF-documenten afvlakken {#flattening-pdf-documents}

Met de service Uitvoer kunt u een interactief PDF-document transformeren naar een niet-interactieve PDF. Met een interactief PDF-document kunnen gebruikers gegevens invoeren of wijzigen die zich in de documentvelden PDF bevinden. Het proces voor het transformeren van een interactief PDF-document naar een niet-interactief PDF-document wordt *afvlakken*. Wanneer een PDF-document wordt afgevlakt, kan een gebruiker de gegevens in de documentvelden niet wijzigen. Een reden om een PDF-document af te vlakken is ervoor te zorgen dat gegevens niet kunnen worden gewijzigd.

U kunt de volgende typen PDF-documenten samenvoegen:

* Interactieve XFA PDF-documenten
* Acrobat Forms

Als u probeert een PDF af te vlakken die een niet-interactief PDF-document is, wordt er een uitzondering gemaakt.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Output, zie [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

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
* adobe-utilities.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)

als AEM Forms wordt geïmplementeerd op een ondersteunde J2EE-toepassingsserver die geen JBoss is, moet u de bestanden adobe-utilities.jar en jbossall-client.jar vervangen door JAR-bestanden die specifiek zijn voor de J2EE-toepassingsserver waarop AEM Forms wordt geïmplementeerd. Voor informatie over de locatie van alle AEM Forms JAR-bestanden raadpleegt u [Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Een Output Client-object maken**

Voordat u programmatisch een uitvoerservicebewerking kunt uitvoeren, moet u een uitvoerservice-clientobject maken. Als u de Java API gebruikt, maakt u een `OutputClient` object. Als u de uitvoerwebservice-API gebruikt, maakt u een `OutputServiceService` object.

**Een interactief PDF-document ophalen**

Haal een interactief PDF-document op dat u wilt omzetten in een niet-interactief PDF-document. Als u probeert een niet-interactief PDF-document te transformeren, wordt er een uitzondering gemaakt.

**Het PDF-document transformeren**

Nadat u een interactief PDF-document hebt opgehaald, kunt u het omzetten in een niet-interactief PDF-document. De service Uitvoer retourneert een niet-interactief PDF-document.

**Niet-interactief PDF-document opslaan als een PDF--bestand**

U kunt het niet-interactieve PDF-document opslaan als een PDF-bestand.

**Zie ook**

[Een PDF-document samenvoegen met de Java API](creating-document-output-streams.md#flatten-a-pdf-document-using-the-java-api)

[Een PDF-document samenvoegen met de webservice-API](creating-document-output-streams.md#flatten-a-pdf-document-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Uitvoerservice-API - Snel starten](/help/forms/developing/output-service-java-api-quick.md#output-service-java-api-quick-start-soap)

### Een PDF-document samenvoegen met de Java API {#flatten-a-pdf-document-using-the-java-api}

Een interactief PDF-document afvlakken naar een niet-interactief PDF-document met behulp van de Output API (Java):

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-output-client.jar, op in het klassenpad van uw Java-project.

1. Maak een Output Client-object.

   * Een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Een `OutputClient` object door de constructor ervan te gebruiken en de `ServiceClientFactory` object.

1. Een interactief PDF-document ophalen.

   * Een `java.io.FileInputStream` -object dat het interactieve PDF-document vertegenwoordigt dat moet worden getransformeerd met behulp van de constructor en dat een tekenreekswaarde doorgeeft die de locatie van het interactieve PDF-bestand aangeeft.
   * Een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en de `java.io.FileInputStream` object.

1. Transformeer het PDF-document.

   Transformeer het interactieve PDF-document naar een niet-interactief PDF-document door het `OutputServiceService` object `transformPDF` en geeft de volgende waarden door:

   * De `com.adobe.idp.Document` object dat het interactieve PDF-document bevat.
   * A `TransformationFormat` enum value. Als u een niet-interactief PDF-document wilt genereren, geeft u `TransformationFormat.PDF`.
   * A `PDFARevisionNumber` enum value that specifies the revision number. Omdat deze parameter voor een PDF/A-document is bedoeld, kunt u `null`.
   * Een tekenreekswaarde die staat voor het wijzigingsnummer en -jaar, gescheiden door een dubbele punt. Omdat deze parameter voor een PDF/A-document is bedoeld, kunt u `null`.
   * A `PDFAConformance` Enumwaarde die het PDF/A-compatibiliteitsniveau vertegenwoordigt. Omdat deze parameter voor een PDF/A-document is bedoeld, kunt u `null`.

   De `transformPDF` methode retourneert een `com.adobe.idp.Document` -object dat een niet-interactief PDF-document bevat.

1. Sla het niet-interactieve PDF-document op als een PDF-bestand.

   * Een `java.io.File` en zorg ervoor dat de bestandsnaamextensie .pdf is.
   * De `Document` object `copyToFile` methode om de inhoud van de `Document` object naar het bestand (gebruik de `Document` object dat is geretourneerd door de `transformPDF` methode).

**Zie ook**

[Overzicht van de stappen](creating-document-output-streams.md#summary-of-steps)

[Snel starten (EJB-modus): een PDF-document transformeren met de Java API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-transforming-a-pdf-document-using-the-java-api)

[Snel starten (SOAP-modus): een PDF-document transformeren met de Java API](/help/forms/developing/output-service-java-api-quick.md#quick-start-soap-mode-transforming-a-pdf-document-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Een PDF-document samenvoegen met de webservice-API {#flatten-a-pdf-document-using-the-web-service-api}

Een interactief PDF-document afvlakken naar een niet-interactief PDF-document met de Output API (webservice):

1. Inclusief projectbestanden.

   Creeer een Microsoft .NET project dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/OutputService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` met het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een Output Client-object.

   * Een `OutputServiceClient` object met de standaardconstructor.
   * Een `OutputServiceClient.Endpoint.Address` object door het `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/OutputService?blob=mtom`.) U hoeft de `lc_version` kenmerk. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt. Geef echter `?blob=mtom` MTOM gebruiken.
   * Een `System.ServiceModel.BasicHttpBinding` object door de waarde van het object op te halen `OutputServiceClient.Endpoint.Binding` veld. De geretourneerde waarde omzetten in `BasicHttpBinding`.
   * Stel de `System.ServiceModel.BasicHttpBinding` object `MessageEncoding` veld naar `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld toe `OutputServiceClient.ClientCredentials.UserName.UserName`.
      * De bijbehorende wachtwoordwaarde aan het veld toewijzen `OutputServiceClient.ClientCredentials.UserName.Password`.
      * De constante waarde toewijzen `HttpClientCredentialType.Basic` naar het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * De constante waarde toewijzen `BasicHttpSecurityMode.TransportCredentialOnly` naar het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Een interactief PDF-document ophalen.

   * Een `BLOB` object met behulp van de constructor. De `BLOB` wordt gebruikt om het interactieve PDF-document op te slaan.
   * Een `System.IO.FileStream` door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het interactieve PDF-document vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van de `System.IO.FileStream` object. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` object `Length` eigenschap.
   * De bytearray vullen met streamgegevens door de `System.IO.FileStream` object `Read` en geeft u de bytearray, de startpositie en de streamlengte door die u wilt lezen.
   * Vul de `BLOB` object door het toe te wijzen `MTOM` eigenschap met de inhoud van de bytearray.

1. Transformeer het PDF-document.

   Transformeer het interactieve PDF-document naar een niet-interactief PDF-document door het `OutputClient` object `transformPDF` en geeft de volgende waarden door:

   * A `BLOB` object dat het interactieve PDF-document bevat.
   * A `TransformationFormat` opsommingswaarde. Als u een niet-interactief PDF-document wilt genereren, geeft u `TransformationFormat.PDF`.
   * A `PDFARevisionNumber` enum value that specifies the revision number.
   * Een Booleaanse waarde die opgeeft of de klasse `PDFARevisionNumber` de opsommingswaarde wordt gebruikt. Omdat deze parameter voor een PDF/A-document is bedoeld, kunt u `false`.
   * Een tekenreekswaarde die staat voor het wijzigingsnummer en -jaar, gescheiden door een dubbele punt. Omdat deze parameter voor een PDF/A-document is bedoeld, kunt u `null`.
   * A `PDFAConformance` Enumwaarde die het PDF/A-compatibiliteitsniveau vertegenwoordigt.
   * Booleaanse waarde die opgeeft of de `PDFAConformance` de opsommingswaarde wordt gebruikt. Omdat deze parameter voor een PDF/A-document is bedoeld, kunt u `false`.

   De `transformPDF` methode retourneert een `BLOB` -object dat een niet-interactief PDF-document bevat.

1. Sla het niet-interactieve PDF-document op als een PDF-bestand.

   * Een `System.IO.FileStream` door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het niet-interactieve PDF-document vertegenwoordigt.
   * Maak een bytearray waarin de gegevensinhoud van de `BLOB` object dat is geretourneerd door de `transformPDF` methode. Vul de bytearray met de waarde van de `BLOB` object `MTOM` lid.
   * Een `System.IO.BinaryWriter` object door de constructor aan te roepen en de `System.IO.FileStream` object.
   * Schrijf de inhoud van de bytearray naar een PDF-bestand door het `System.IO.BinaryWriter` object `Write` en geeft u de bytearray door.

**Zie ook**

[Overzicht van de stappen](creating-document-output-streams.md#summary-of-steps)

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)
