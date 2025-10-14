---
title: PDF-documenten samenstellen met bladwijzers
description: Gebruik de dienst van de Assembler om een document te wijzigen van PDF dat geen referenties bevat om referenties te omvatten gebruikend Java API en de Dienst API van het Web.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
exl-id: 2b938410-f51b-420b-b5d4-2ed13ec29c5a
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Document Services
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '2519'
ht-degree: 0%

---

# PDF-documenten samenstellen met bladwijzers {#assembling-pdf-documents-with-bookmarks}

**de Steekproeven en de voorbeelden in dit document zijn slechts voor AEM Forms op milieu JEE.**

U kunt een PDF-document samenstellen dat bladwijzers bevat. Stel dat u een PDF-document hebt dat geen bladwijzers bevat en dat u het wilt wijzigen door bladwijzers op te geven. Met de Assembler-service kunt u een PDF-document zonder bladwijzers doorgeven en een PDF-document met bladwijzers terugkrijgen.

Bladwijzers bevatten de volgende eigenschappen:

* Een titel die als tekst op het scherm verschijnt.
* Een handeling die aangeeft wat er gebeurt wanneer een gebruiker op de bladwijzer klikt. Een bladwijzer wordt gewoonlijk gebruikt om naar een andere locatie in het huidige document te gaan of een ander PDF-document te openen, maar er kunnen nog andere handelingen worden opgegeven.

Voor deze bespreking, veronderstel dat het volgende DDX- document wordt gebruikt.

```xml
 <?xml version="1.0" encoding="UTF-8"?>
 <DDX xmlns="https://ns.adobe.com/DDX/1.0/">
       <PDF result="FinalDoc.pdf">
          <PDF source="Loan.pdf">
             <Bookmarks source="doc2" />
          </PDF>
       </PDF>
 </DDX>
```

In dit DDX-document wordt de waarde `Loan.pdf` toegewezen aan het bronkenmerk. Dit DDX-document geeft aan dat één PDF-document wordt doorgegeven aan de Assembler-service. Wanneer u een PDF-document samenstelt met bladwijzers, moet u een XML-bladwijzerdocument opgeven dat de bladwijzers in het resulterende document beschrijft. Als u een XML-bladwijzerdocument wilt opgeven, moet u controleren of het element `Bookmarks` is opgegeven in uw DDX-document.

In dit voorbeeld-DDX-document geeft het `Bookmarks` -element `doc2` op als de waarde. Deze waarde geeft aan dat de invoerkaart die aan de Assembler-service wordt doorgegeven, een sleutel met de naam `doc2` bevat. De waarde van de `doc2` -toets is een `com.adobe.idp.Document` -waarde die het XML-bladwijzerdocument vertegenwoordigt. (Zie &quot;Taal van Bladwijzers&quot;in de [&#x200B; Dienst van de Assembler en Verwijzing DDX &#x200B;](https://www.adobe.com/go/learn_aemforms_ddx_63).)

In dit onderwerp wordt de volgende XML-bladwijzertaal gebruikt om een PDF-document met bladwijzers samen te stellen.

```xml
 <?xml version="1.0" encoding="UTF-8"?>
 <Bookmarks xmlns="https://ns.adobe.com/pdf/bookmarks" version="1.0">
       <Bookmark>
          <Action>
             <Launch NewWindow="true">
                <File Name="C:\Adobe\LoanDetails.pdf" />
             </Launch>
          </Action>
         <Title>Open the Loan document</Title>
       </Bookmark>
 <Bookmark>
          <Action>
             <Launch>
                <Win Name="C:\WINDOWS\notepad.exe" />
             </Launch>
          </Action>
     <Title>Launch NotePad</Title>
       </Bookmark>
 </Bookmarks>
```

In dit XML-bladwijzerdocument ziet u het element Handeling dat de handeling definieert die wordt uitgevoerd wanneer een gebruiker op de bladwijzer klikt. Onder het element Handeling bevindt zich het element Launch dat toepassingen start, zoals NotePad, en bestanden opent, zoals PDF-bestanden. Als u een PDF-bestand wilt openen, moet u het File-element gebruiken dat het bestand aangeeft dat moet worden geopend. In het XML-bladwijzerbestand dat in deze sectie is opgegeven, is LoanDetails.pdf de naam van het bestand dat wordt geopend.

>[!NOTE]
>
>Voor volledige details over gesteunde acties, zie &quot; `Action` element&quot;in de [&#x200B; Dienst van de Assembler en Verwijzing DDX &#x200B;](https://www.adobe.com/go/learn_aemforms_ddx_63).

Op basis van het DDX-document dat in deze sectie is opgegeven en het XML-bladwijzerbestand als invoer, stelt de Assembler-service een PDF-document samen dat de volgende bladwijzers bevat.

![&#x200B; aw_aw_bmark &#x200B;](assets/aw_aw_bmark.png)

Wanneer een gebruiker op *klikt Open de 1&rbrace; referentie van de Details van de Lening {, wordt LoanDetails.pdf geopend.* Eveneens, wanneer de gebruiker op de *1} bookmark van de Lancering NotePad &lbrace;klikt, is NotePad begonnen.*

>[!NOTE]
>
>Alvorens deze sectie te lezen, adviseert men dat u vertrouwd bent met het assembleren van de documenten van PDF gebruikend de dienst van de Assembler. Deze sectie bespreekt geen concepten, zoals het creëren van een inzamelingsvoorwerp dat inputdocumenten of het leren hoe te om de resultaten uit het teruggekeerde inzamelingsvoorwerp te halen bevat. (Zie [&#x200B; Programmatiatically het assembleren van de Documenten van PDF &#x200B;](/help/forms/developing/programmatically-assembling-pdf-documents.md#programmatically-assembling-pdf-documents).)

>[!NOTE]
>
>Voor meer informatie over de dienst van de Assembler, zie [&#x200B; Verwijzing van de Diensten voor AEM Forms &#x200B;](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Voor meer informatie over een document DDX, zie [&#x200B; de Dienst van de Assembler en de Verwijzing DDX &#x200B;](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Overzicht van de stappen {#summary-of-steps}

U kunt als volgt een PDF-document met bladwijzers samenstellen:

1. Inclusief projectbestanden.
1. Maak een PDF Assembler-client.
1. Verwijs naar een bestaand DDX-document.
1. Verwijs naar een PDF-document waaraan bladwijzers worden toegevoegd.
1. Verwijs naar het XML-document van de bladwijzer.
1. Voeg het document van de PDF en het referentieXML- document aan een inzameling van de Kaart toe.
1. Stel runtime-opties in.
1. Samenstellen van het PDF-document.
1. Sla het PDF-document op dat bladwijzers bevat.

**omvat projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-assembler-client.jar
* adobe-utilities.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)

als AEM Forms wordt geïmplementeerd op een andere ondersteunde J2EE-toepassingsserver dan JBoss, moet u de bestanden adobe-utilities.jar en jbossall-client.jar vervangen door JAR-bestanden die specifiek zijn voor de J2EE-toepassingsserver waarop AEM Forms is geïmplementeerd. Voor informatie over de plaats van alle dossiers van AEM Forms JAR, zie [&#x200B; Inclusief de bibliotheekdossiers van AEM Forms Java &#x200B;](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**creeer een cliënt van de Assembler van de PDF**

Alvorens u programmatically een verrichting van de Assembler kunt uitvoeren, moet u een de dienstcliënt van de Assembler tot stand brengen.

**Verwijzing een bestaand document DDX**

Er moet naar een DDX-document worden verwezen om een PDF-document samen te stellen. Dit DDX-document moet het `Bookmarks` -element bevatten, dat de Assembler-service opgeeft een PDF samen te stellen die bladwijzers bevat. (Zie het DDX-document dat eerder in deze sectie wordt weergegeven voor een voorbeeld.)

**Verwijzing een document van PDF waaraan de referenties worden toegevoegd**

Verwijs naar een PDF-document waaraan bladwijzers worden toegevoegd. Het maakt niet uit of het document waarnaar wordt verwezen PDF al bladwijzers bevat. Als het `Bookmarks` -element een onderliggend element is van het PDF-bronelement, worden de bladwijzers gebruikt die al in de PDF-bron staan. Als u de bestaande bladwijzers echter wilt behouden, moet u ervoor zorgen dat `Bookmarks` een item op hetzelfde niveau is als het bronelement PDF. Neem bijvoorbeeld het volgende voorbeeld:

```xml
 <PDF result="foo">
      <PDF source="inDoc"/>
      <Bookmarks source="doc2"/>
 </PDF>
```

**Verwijzing het document van referentieXML**

Als u een PDF wilt samenstellen die nieuwe bladwijzers bevat, moet u naar een XML-bladwijzerdocument verwijzen. Het bladwijzerdocument van XML wordt overgegaan tot de dienst van de Assembler binnen het de inzamelingsvoorwerp van de Kaart. (Zie het referentie-XML-document dat eerder in deze sectie wordt weergegeven voor een voorbeeld.)

>[!NOTE]
>
>Zie &quot;Taal van Bladwijzers&quot;in de [&#x200B; Dienst van de Assembler en Verwijzing DDX &#x200B;](https://www.adobe.com/go/learn_aemforms_ddx_63).

**voeg het document van PDF en het document van referentieXML aan een inzameling van de Kaart** toe

Voeg zowel het PDF-document toe waaraan bladwijzers worden toegevoegd als het XML-bladwijzerdocument aan de Map-verzameling. Het verzamelingsobject Map bevat daarom twee elementen: een PDF-document en het XML-bladwijzerdocument.

**vastgestelde runtime opties**

U kunt runtime opties plaatsen die het gedrag van de dienst van de Assembler controleren terwijl het een baan uitvoert. U kunt bijvoorbeeld een optie instellen die de Assembler-service de opdracht geeft door te gaan met het verwerken van een taak als er een fout optreedt. Voor informatie over de runtime opties die u kunt plaatsen, zie de `AssemblerOptionSpec` klassenverwijzing in [&#x200B; AEM Forms API Verwijzing &#x200B;](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**assembleer het document van de PDF**

Als u een PDF-document wilt samenstellen dat nieuwe bladwijzers bevat, gebruikt u de bewerking `invokeDDX` van de Assembler-service. De reden waarom u de `invokeDDX` verrichting in tegenstelling tot andere de dienstverrichtingen van de Assembler zoals `invokeOneDocument` moet gebruiken is omdat de dienst van de Assembler een document van referentieXML vereist dat binnen het de inzamelingsvoorwerp van de Kaart wordt overgegaan. Dit object is een parameter van de `invokeDDX` -bewerking.

**sparen het document van de PDF dat referenties** bevat

Extraheer de resultaten van het geretourneerde object Map en sla het bijbehorende PDF-document op. (Zie &quot;de resultaten&quot;in [&#x200B; Programmatiatically Assemblbling PDF Documenten &#x200B;](/help/forms/developing/programmatically-assembling-pdf-documents.md) trekken.)

**zie ook**

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[PDF-documenten programmatisch samenstellen](/help/forms/developing/programmatically-assembling-pdf-documents.md)

## PDF-documenten samenstellen met bladwijzers met behulp van de Java API {#assemble-pdf-documents-with-bookmarks-using-the-java-api}

U kunt een PDF-document samenstellen met bladwijzers met behulp van de API (Java) voor vergaderingsservice:

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-assembler-client.jar, op in het klassenpad van uw Java-project.

1. Maak een PDF Assembler-client.

   * Maak een `ServiceClientFactory` -object dat verbindingseigenschappen bevat. (Zie [&#x200B; Plaatsende verbindingseigenschappen &#x200B;](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)
   * Maak een `AssemblerServiceClient` -object door de constructor ervan te gebruiken en het `ServiceClientFactory` -object door te geven.

1. Verwijs naar een bestaand DDX-document.

   * Maak een `java.io.FileInputStream` -object dat het DDX-document vertegenwoordigt door de constructor ervan te gebruiken en een tekenreekswaarde door te geven die de locatie van het DDX-bestand aangeeft.
   * Maak een `com.adobe.idp.Document` -object door de constructor ervan te gebruiken en het `java.io.FileInputStream` -object door te geven.

1. Verwijs naar een PDF-document waaraan bladwijzers worden toegevoegd.

   * Maak een `java.io.FileInputStream` -object door de constructor ervan te gebruiken en de locatie van het PDF-document door te geven.
   * Maak een `com.adobe.idp.Document` -object met behulp van de constructor en geef het `java.io.FileInputStream` -object door dat het PDF-document bevat.

1. Verwijs naar het XML-document van de bladwijzer.

   * Maak een `java.io.FileInputStream` -object door de constructor ervan te gebruiken en de locatie door te geven van het XML-bestand dat het XML-bladwijzerdocument vertegenwoordigt.
   * Maak een `com.adobe.idp.Document` -object en geef het `java.io.FileInputStream` -object door dat het PDF-document bevat.

1. Voeg het document van de PDF en het referentieXML- document aan een inzameling van de Kaart toe.

   * Maak een `java.util.Map` -object dat wordt gebruikt om zowel het invoerdocument als het XML-document met de bladwijzer op te slaan.
   * Voeg het invoerdocument PDF toe door de methode `put` van het object `java.util.Map` aan te roepen en de volgende argumenten door te geven:

      * Een tekenreekswaarde die de sleutelnaam vertegenwoordigt. Deze waarde moet overeenkomen met de waarde van het PDF-bronelement dat is opgegeven in het DDX-document.
      * Een `com.adobe.idp.Document` -object dat het invoerdocument PDF bevat.

   * Voeg het XML-bladwijzerdocument toe door de methode `put` van het object `java.util.Map` aan te roepen en de volgende argumenten door te geven:

      * Een tekenreekswaarde die de sleutelnaam vertegenwoordigt. Deze waarde moet overeenkomen met de waarde van het bronelement Bladwijzers dat is opgegeven in het DDX-document.
      * Een `com.adobe.idp.Document` -object dat het XML-bladwijzerdocument bevat.

1. Stel runtime-opties in.

   * Maak een `AssemblerOptionSpec` -object dat uitvoeringsopties opslaat met behulp van de bijbehorende constructor.
   * Stel runtime-opties in om aan uw bedrijfsvereisten te voldoen door een methode aan te roepen die tot het `AssemblerOptionSpec` -object behoort. Als u bijvoorbeeld de Assembler-service de instructie wilt geven een taak te blijven verwerken wanneer een fout optreedt, roept u de methode `setFailOnError` van het object `AssemblerOptionSpec` aan en geeft u deze door `false` .

1. Samenstellen van het PDF-document.

   Roep de methode `invokeDDX` van het object `AssemblerServiceClient` aan en geef de volgende vereiste waarden door:

   * Een `com.adobe.idp.Document` -object dat het te gebruiken DDX-document vertegenwoordigt
   * Een `java.util.Map` -object dat zowel het invoerdocument als het XML-document met de bladwijzer bevat.
   * Een `com.adobe.livecycle.assembler.client.AssemblerOptionSpec` -object dat de runtime-opties opgeeft, inclusief het standaardniveau voor lettertypen en taaklogbestanden

   De methode `invokeDDX` retourneert een `com.adobe.livecycle.assembler.client.AssemblerResult` -object dat de resultaten van de taak en eventuele uitzonderingen bevat die zijn opgetreden.

1. Sla het PDF-document op dat bladwijzers bevat.

   Voer de volgende handelingen uit om het nieuwe PDF-document te verkrijgen:

   * Roep de methode `getDocuments` van het object `AssemblerResult` aan. Hiermee wordt een `java.util.Map` -object geretourneerd.
   * Doorloop het `java.util.Map` -object totdat u het resulterende `com.adobe.idp.Document` -object vindt. (U kunt het PDF-resultaatelement gebruiken dat in het DDX-document is opgegeven.)
   * Roep de methode `copyToFile` van het `com.adobe.idp.Document` -object aan om het PDF-document te extraheren.

**zie ook**

[Snel starten (SOAP modus): PDF-documenten samenstellen met bladwijzers met behulp van de Java API](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-assembling-pdf-documents-with-bookmarks-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## PDF-documenten samenstellen met bladwijzers met behulp van de webservice-API {#assemble-pdf-documents-with-bookmarks-using-the-web-service-api}

U kunt een PDF-document samenstellen met bladwijzers met behulp van de API (webservice) van de Assembler Service:

1. Inclusief projectbestanden.

   Creeer een Microsoft .NET project dat MTOM gebruikt. Gebruik de volgende WSDL-definitie: `http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1` .

   >[!NOTE]
   >
   >Vervang `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een PDF Assembler-client.

   * Maak een `AssemblerServiceClient` -object met de standaardconstructor.
   * Maak een `AssemblerServiceClient.Endpoint.Address` -object met de `System.ServiceModel.EndpointAddress` -constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/AssemblerService?blob=mtom` ). U hoeft het attribuut `lc_version` niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.
   * Maak een `System.ServiceModel.BasicHttpBinding` -object door de waarde van het `AssemblerServiceClient.Endpoint.Binding` -veld op te halen. De geretourneerde waarde wordt gecast naar `BasicHttpBinding` .
   * Stel het veld `MessageEncoding` van het `System.ServiceModel.BasicHttpBinding` -object in op `WSMessageEncoding.Mtom` . Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld `AssemblerServiceClient.ClientCredentials.UserName.UserName` toe.
      * Wijs de bijbehorende wachtwoordwaarde toe aan het veld `AssemblerServiceClient.ClientCredentials.UserName.Password` .
      * Wijs de constante waarde `HttpClientCredentialType.Basic` toe aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType` .
      * Wijs de constante waarde `BasicHttpSecurityMode.TransportCredentialOnly` toe aan het veld `BasicHttpBindingSecurity.Security.Mode` .

1. Verwijs naar een bestaand DDX-document.

   * Maak een `BLOB` -object met behulp van de constructor. Het `BLOB` -object wordt gebruikt om het DDX-document op te slaan.
   * Maak een `System.IO.FileStream` -object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het DDX-document en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van het object `System.IO.FileStream` wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de eigenschap `Length` van het object `System.IO.FileStream` op te halen.
   * Vul de bytearray met streamgegevens door de methode `Read` van het object `System.IO.FileStream` aan te roepen en de bytearray, de startpositie en de lengte van de stream door te geven om te lezen.
   * Vul het `BLOB` -object door het `MTOM` -veld ervan toe te wijzen met de inhoud van de bytearray.

1. Verwijs naar een PDF-document waaraan bladwijzers worden toegevoegd.

   * Maak een `BLOB` -object met behulp van de constructor. Het `BLOB` -object wordt gebruikt om de invoer-PDF op te slaan.
   * Maak een `System.IO.FileStream` -object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het PDF-invoerdocument en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van het object `System.IO.FileStream` wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de eigenschap `Length` van het object `System.IO.FileStream` op te halen.
   * Vul de bytearray met streamgegevens door de methode `Read` van het object `System.IO.FileStream` aan te roepen en de bytearray, de startpositie en de lengte van de stream door te geven om te lezen.
   * Vul het `BLOB` -object door het `MTOM` -veld ervan toe te wijzen met de inhoud van de bytearray.

1. Verwijs naar het XML-document van de bladwijzer.

   * Maak een `BLOB` -object met behulp van de constructor. Met het `BLOB` -object wordt het XML-bladwijzerdocument opgeslagen.
   * Maak een `System.IO.FileStream` -object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het PDF-invoerdocument en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van het object `System.IO.FileStream` wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de eigenschap `Length` van het object `System.IO.FileStream` op te halen.
   * Vul de bytearray met streamgegevens door de methode `Read` van het object `System.IO.FileStream` aan te roepen en de bytearray, de startpositie en de lengte van de stream door te geven om te lezen.
   * Vul het `BLOB` -object door het `MTOM` -veld ervan toe te wijzen met de inhoud van de bytearray.

1. Voeg het document van de PDF en het referentieXML- document aan een inzameling van de Kaart toe.

   * Maak een `MyMapOf_xsd_string_To_xsd_anyType` -object. Dit verzamelingsobject wordt gebruikt om de invoerdocumenten PDF en het XML-bladwijzerdocument op te slaan.
   * Maak voor elk invoerdocument PDF en het XML-bladwijzerdocument een `MyMapOf_xsd_string_To_xsd_anyType_Item` -object.
   * Wijs een tekenreekswaarde toe die de sleutelnaam vertegenwoordigt aan het veld `key` van het `MyMapOf_xsd_string_To_xsd_anyType_Item` -object. Deze waarde moet overeenkomen met de waarde van het PDF-bronelement dat is opgegeven in het DDX-document.
   * Wijs het `BLOB` -object toe dat het PDF-document opslaat in het veld `MyMapOf_xsd_string_To_xsd_anyType_Item` object `value` .
   * Voeg het object `MyMapOf_xsd_string_To_xsd_anyType_Item` toe aan het object `MyMapOf_xsd_string_To_xsd_anyType` . Roep de methode `Add` van het object `MyMapOf_xsd_string_To_xsd_anyType` aan en geef het object `MyMapOf_xsd_string_To_xsd_anyType` door. (Voer deze taak uit voor elk invoer-PDF-document en voor het XML-bladwijzerdocument.)

1. Stel runtime-opties in.

   * Maak een `AssemblerOptionSpec` -object dat uitvoeringsopties opslaat met behulp van de bijbehorende constructor.
   * Stel runtime-opties in om aan uw bedrijfsvereisten te voldoen door een waarde toe te wijzen aan een gegevenslid dat tot het `AssemblerOptionSpec` -object behoort. Als u bijvoorbeeld de Assembler-service wilt instrueren een taak te blijven verwerken wanneer een fout optreedt, wijst u `false` toe aan het gegevenslid van het `AssemblerOptionSpec` object `failOnError` .

1. Samenstellen van het PDF-document.

   Roep de methode `invokeDDX` van het object `AssemblerServiceClient` aan en geef de volgende waarden door:

   * Een `BLOB` -object dat het DDX-document vertegenwoordigt
   * De array `MyMapOf_xsd_string_To_xsd_anyType` die de invoerdocumenten bevat
   * Een `AssemblerOptionSpec` -object dat uitvoeringsopties opgeeft

   De methode `invokeDDX` retourneert een `AssemblerResult` -object dat de resultaten van de taak en eventuele uitzonderingen bevat die hebben plaatsgevonden.

1. Sla het PDF-document op dat bladwijzers bevat.

   Voer de volgende handelingen uit om het nieuwe PDF-document te verkrijgen:

   * Open het veld `documents` van het `AssemblerResult` -object (een `Map` -object dat de PDF-documenten van het resultaat bevat).
   * Doorloop het `Map` -object totdat u de sleutel vindt die overeenkomt met de naam van het resulterende document. Vervolgens cast u het element `value` van dat arraylid naar een `BLOB` .
   * Haal de binaire gegevens uit het PDF-document door het `BLOB` -veld `MTOM` van het object te openen. Hiermee wordt een array met bytes geretourneerd die u naar een PDF-bestand kunt schrijven.

**zie ook**

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
