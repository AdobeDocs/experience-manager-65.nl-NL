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
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '2519'
ht-degree: 0%

---

# PDF-documenten samenstellen met bladwijzers {#assembling-pdf-documents-with-bookmarks}

**Voorbeelden en voorbeelden in dit document gelden alleen voor AEM Forms in JEE-omgeving.**

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

Binnen dit DDX-document wordt de waarde toegewezen aan het bronkenmerk `Loan.pdf`. Dit DDX-document geeft aan dat één PDF-document wordt doorgegeven aan de Assembler-service. Wanneer u een PDF-document samenstelt met bladwijzers, moet u een XML-bladwijzerdocument opgeven dat de bladwijzers in het resulterende document beschrijft. Als u een XML-bladwijzerdocument wilt opgeven, moet u ervoor zorgen dat `Bookmarks` -element wordt opgegeven in uw DDX-document.

In dit voorbeeld-DDX-document worden `Bookmarks` element specifies `doc2` als de waarde. Deze waarde wijst erop dat de inputkaart die tot de dienst van de Assembler wordt overgegaan een sleutel genoemd bevat `doc2`. De waarde van `doc2` key is a `com.adobe.idp.Document` waarde die staat voor het XML-bladwijzerdocument. (Zie &quot;Taal van bladwijzers&quot; in het dialoogvenster [De Verwijzing van de AssemblerDienst en DDX](https://www.adobe.com/go/learn_aemforms_ddx_63).)

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
>Voor volledige informatie over ondersteunde acties raadpleegt u &quot; `Action` element&quot; in de [De Verwijzing van de AssemblerDienst en DDX](https://www.adobe.com/go/learn_aemforms_ddx_63).

Op basis van het DDX-document dat in deze sectie is opgegeven en het XML-bladwijzerbestand als invoer, stelt de Assembler-service een PDF-document samen dat de volgende bladwijzers bevat.

![aw_aw_bmark](assets/aw_aw_bmark.png)

Wanneer een gebruiker op de knop *De leningsdetails openen* bladwijzer, LoanDetails.pdf wordt geopend. En wanneer de gebruiker op het *NotePad starten* bladwijzer, NotePad is gestart.

>[!NOTE]
>
>Alvorens deze sectie te lezen, adviseert men dat u vertrouwd bent met het assembleren van de documenten van PDF gebruikend de dienst van de Assembler. Deze sectie bespreekt geen concepten, zoals het creëren van een inzamelingsvoorwerp dat inputdocumenten of het leren hoe te om de resultaten uit het teruggekeerde inzamelingsvoorwerp te halen bevat. (Zie [PDF-documenten programmatisch samenstellen](/help/forms/developing/programmatically-assembling-pdf-documents.md#programmatically-assembling-pdf-documents).)

>[!NOTE]
>
>Voor meer informatie over de dienst van de Assembler, zie [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Voor meer informatie over een DDX-document raadpleegt u [De Verwijzing van de AssemblerDienst en DDX](https://www.adobe.com/go/learn_aemforms_ddx_63).

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

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-assembler-client.jar
* adobe-utilities.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)

als AEM Forms wordt geïmplementeerd op een andere ondersteunde J2EE-toepassingsserver dan JBoss, moet u de bestanden adobe-utilities.jar en jbossall-client.jar vervangen door JAR-bestanden die specifiek zijn voor de J2EE-toepassingsserver waarop AEM Forms is geïmplementeerd. Voor informatie over de locatie van alle AEM Forms JAR-bestanden raadpleegt u [Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Een PDF Assembler-client maken**

Alvorens u programmatically een verrichting van de Assembler kunt uitvoeren, moet u een de dienstcliënt van de Assembler tot stand brengen.

**Verwijzen naar een bestaand DDX-document**

Er moet naar een DDX-document worden verwezen om een PDF-document samen te stellen. Dit DDX-document moet de `Bookmarks` element, dat de dienst van de Assembler opdraagt om een PDF samen te stellen die referenties bevat. (Zie het DDX-document dat eerder in deze sectie wordt weergegeven voor een voorbeeld.)

**Verwijzen naar een PDF-document waaraan bladwijzers worden toegevoegd**

Verwijs naar een PDF-document waaraan bladwijzers worden toegevoegd. Het maakt niet uit of het document waarnaar wordt verwezen PDF al bladwijzers bevat. Als de `Bookmarks` -element is een onderliggend element van het PDF-bronelement. De bladwijzers vervangen de bladwijzers die al in de PDF-bron bestaan. Als u echter de bestaande bladwijzers wilt behouden, moet u ervoor zorgen dat `Bookmarks` is een vergelijk van het PDF-bronelement. Neem bijvoorbeeld het volgende voorbeeld:

```xml
 <PDF result="foo">
      <PDF source="inDoc"/>
      <Bookmarks source="doc2"/>
 </PDF>
```

**Verwijzen naar het XML-bladwijzerdocument**

Als u een PDF wilt samenstellen die nieuwe bladwijzers bevat, moet u naar een XML-bladwijzerdocument verwijzen. Het bladwijzerdocument van XML wordt overgegaan tot de dienst van de Assembler binnen het de inzamelingsvoorwerp van de Kaart. (Zie het referentie-XML-document dat eerder in deze sectie wordt weergegeven voor een voorbeeld.)

>[!NOTE]
>
>Zie &quot;Taal van bladwijzers&quot; in het dialoogvenster [De Verwijzing van de AssemblerDienst en DDX](https://www.adobe.com/go/learn_aemforms_ddx_63).

**Het PDF-document en het XML-bladwijzerdocument toevoegen aan een Map-verzameling**

Voeg zowel het PDF-document toe waaraan bladwijzers worden toegevoegd als het XML-bladwijzerdocument aan de Map-verzameling. Het verzamelingsobject Map bevat daarom twee elementen: een PDF-document en het XML-bladwijzerdocument.

**Uitvoeringsopties instellen**

U kunt runtime opties plaatsen die het gedrag van de dienst van de Assembler controleren terwijl het een baan uitvoert. U kunt bijvoorbeeld een optie instellen die de Assembler-service de opdracht geeft door te gaan met het verwerken van een taak als er een fout optreedt. Voor informatie over de runtime opties die u kunt plaatsen, zie `AssemblerOptionSpec` klasseverwijzing in [AEM Forms API-naslag](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**Het PDF-document samenstellen**

Als u een PDF-document wilt samenstellen dat nieuwe bladwijzers bevat, gebruikt u de Assembler-service `invokeDDX` -bewerking. De reden waarom u de `invokeDDX` verrichting in tegenstelling tot andere de dienstverrichtingen van de Assembler zoals `invokeOneDocument` is omdat de Assembler dienst een document van referentieXML vereist dat binnen het de inzamelingsvoorwerp van de Kaart wordt overgegaan. Dit object is een parameter van de `invokeDDX` -bewerking.

**PDF-document met bladwijzers opslaan**

Extraheer de resultaten van het geretourneerde object Map en sla het bijbehorende PDF-document op. (Zie De resultaten extraheren in [PDF-documenten programmatisch samenstellen](/help/forms/developing/programmatically-assembling-pdf-documents.md).)

**Zie ook**

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[PDF-documenten programmatisch samenstellen](/help/forms/developing/programmatically-assembling-pdf-documents.md)

## PDF-documenten samenstellen met bladwijzers met behulp van de Java API {#assemble-pdf-documents-with-bookmarks-using-the-java-api}

U kunt een PDF-document samenstellen met bladwijzers met behulp van de API (Java) voor vergaderingsservice:

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-assembler-client.jar, op in het klassenpad van uw Java-project.

1. Maak een PDF Assembler-client.

   * Een `ServiceClientFactory` object dat verbindingseigenschappen bevat. (Zie [Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)
   * Een `AssemblerServiceClient` object door de constructor ervan te gebruiken en de `ServiceClientFactory` object.

1. Verwijs naar een bestaand DDX-document.

   * Een `java.io.FileInputStream` een object dat het DDX-document vertegenwoordigt door de constructor ervan te gebruiken en een tekenreekswaarde door te geven die de locatie van het DDX-bestand aangeeft.
   * Een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en de `java.io.FileInputStream` object.

1. Verwijs naar een PDF-document waaraan bladwijzers worden toegevoegd.

   * Een `java.io.FileInputStream` object door de constructor ervan te gebruiken en de locatie van het PDF-document door te geven.
   * Een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en de `java.io.FileInputStream` object dat het PDF-document bevat.

1. Verwijs naar het XML-document van de bladwijzer.

   * Een `java.io.FileInputStream` object door de constructor ervan te gebruiken en de locatie door te geven van het XML-bestand dat het XML-bladwijzerdocument vertegenwoordigt.
   * Een `com.adobe.idp.Document` en geeft het `java.io.FileInputStream` object dat het PDF-document bevat.

1. Voeg het document van de PDF en het referentieXML- document aan een inzameling van de Kaart toe.

   * Een `java.util.Map` -object dat wordt gebruikt voor het opslaan van zowel het invoerdocument als het XML-document met bladwijzers.
   * Voeg het invoerdocument PDF toe door het `java.util.Map` object `put` en het doorgeven van de volgende argumenten:

      * Een tekenreekswaarde die de sleutelnaam vertegenwoordigt. Deze waarde moet overeenkomen met de waarde van het PDF-bronelement dat is opgegeven in het DDX-document.
      * A `com.adobe.idp.Document` -object dat het invoerdocument PDF bevat.

   * Voeg het bladwijzerdocument van XML toe door aan te halen `java.util.Map` object `put` en het doorgeven van de volgende argumenten:

      * Een tekenreekswaarde die de sleutelnaam vertegenwoordigt. Deze waarde moet overeenkomen met de waarde van het bronelement Bladwijzers dat is opgegeven in het DDX-document.
      * A `com.adobe.idp.Document` object dat het XML-bladwijzerdocument bevat.

1. Stel runtime-opties in.

   * Een `AssemblerOptionSpec` object dat uitvoeringsopties opslaat met de constructor ervan.
   * Stel runtime-opties in om aan uw bedrijfsvereisten te voldoen door een methode aan te roepen die tot de `AssemblerOptionSpec` object. Bijvoorbeeld, om de dienst van de Assembler op te dragen om een baan te blijven verwerken wanneer een fout voorkomt, haalt het `AssemblerOptionSpec` object `setFailOnError` methode en doorgeven `false`.

1. Samenstellen van het PDF-document.

   De `AssemblerServiceClient` object `invokeDDX` en geeft de volgende vereiste waarden door:

   * A `com.adobe.idp.Document` object dat staat voor het te gebruiken DDX-document
   * A `java.util.Map` -object dat zowel het invoerdocument als het XML-bladwijzerdocument PDF bevat.
   * A `com.adobe.livecycle.assembler.client.AssemblerOptionSpec` object dat de runtime-opties opgeeft, inclusief standaardfont- en taaklogniveau

   De `invokeDDX` methode retourneert een `com.adobe.livecycle.assembler.client.AssemblerResult` object dat de resultaten van de taak en eventuele uitzonderingen bevat die zijn opgetreden.

1. Sla het PDF-document op dat bladwijzers bevat.

   Voer de volgende handelingen uit om het nieuwe PDF-document te verkrijgen:

   * De `AssemblerResult` object `getDocuments` methode. Dit retourneert een `java.util.Map` object.
   * Doorlopen `java.util.Map` object tot u het resultaat hebt gevonden `com.adobe.idp.Document` object. (U kunt het PDF-resultaatelement gebruiken dat in het DDX-document is opgegeven.)
   * De `com.adobe.idp.Document` object `copyToFile` methode om het PDF-document te extraheren.

**Zie ook**

[Snel starten (SOAP-modus): PDF-documenten samenstellen met bladwijzers met behulp van de Java API](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-assembling-pdf-documents-with-bookmarks-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## PDF-documenten samenstellen met bladwijzers met behulp van de webservice-API {#assemble-pdf-documents-with-bookmarks-using-the-web-service-api}

U kunt een PDF-document samenstellen met bladwijzers met behulp van de API (webservice) van de Assembler Service:

1. Inclusief projectbestanden.

   Creeer een Microsoft .NET project dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` met het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een PDF Assembler-client.

   * Een `AssemblerServiceClient` object met de standaardconstructor.
   * Een `AssemblerServiceClient.Endpoint.Address` object door het `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/AssemblerService?blob=mtom`). U hoeft de `lc_version` kenmerk. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.
   * Een `System.ServiceModel.BasicHttpBinding` object door de waarde van het object op te halen `AssemblerServiceClient.Endpoint.Binding` veld. De geretourneerde waarde omzetten in `BasicHttpBinding`.
   * Stel de `System.ServiceModel.BasicHttpBinding` object `MessageEncoding` veld naar `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld toe `AssemblerServiceClient.ClientCredentials.UserName.UserName`.
      * De bijbehorende wachtwoordwaarde aan het veld toewijzen `AssemblerServiceClient.ClientCredentials.UserName.Password`.
      * De constante waarde toewijzen `HttpClientCredentialType.Basic` naar het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * De constante waarde toewijzen `BasicHttpSecurityMode.TransportCredentialOnly` naar het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Verwijs naar een bestaand DDX-document.

   * Een `BLOB` object met behulp van de constructor. De `BLOB` wordt gebruikt om het DDX-document op te slaan.
   * Een `System.IO.FileStream` door de constructor aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het DDX-document en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van de `System.IO.FileStream` object. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` object `Length` eigenschap.
   * De bytearray vullen met streamgegevens door de `System.IO.FileStream` object `Read` en geeft u de bytearray, de startpositie en de streamlengte door die u wilt lezen.
   * Vul de `BLOB` object door het toe te wijzen `MTOM` veld met de inhoud van de bytearray.

1. Verwijs naar een PDF-document waaraan bladwijzers worden toegevoegd.

   * Een `BLOB` object met behulp van de constructor. De `BLOB` wordt gebruikt om de invoer-PDF op te slaan.
   * Een `System.IO.FileStream` door de constructor aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het invoerdocument PDF en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van de `System.IO.FileStream` object. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` object `Length` eigenschap.
   * De bytearray vullen met streamgegevens door de `System.IO.FileStream` object `Read` en geeft u de bytearray, de startpositie en de streamlengte door die u wilt lezen.
   * Vul de `BLOB` object door het toe te wijzen `MTOM` veld met de inhoud van de bytearray.

1. Verwijs naar het XML-document van de bladwijzer.

   * Een `BLOB` object met behulp van de constructor. De `BLOB` wordt gebruikt om het XML-bladwijzerdocument op te slaan.
   * Een `System.IO.FileStream` door de constructor aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het invoerdocument PDF en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van de `System.IO.FileStream` object. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` object `Length` eigenschap.
   * De bytearray vullen met streamgegevens door de `System.IO.FileStream` object `Read` en geeft u de bytearray, de startpositie en de streamlengte door die u wilt lezen.
   * Vul de `BLOB` object door het toe te wijzen `MTOM` veld met de inhoud van de bytearray.

1. Voeg het document van de PDF en het referentieXML- document aan een inzameling van de Kaart toe.

   * Een `MyMapOf_xsd_string_To_xsd_anyType` object. Dit verzamelingsobject wordt gebruikt om de invoerdocumenten PDF en het XML-bladwijzerdocument op te slaan.
   * Maak voor elk invoerdocument en het XML-bladwijzerdocument een `MyMapOf_xsd_string_To_xsd_anyType_Item` object.
   * Wijs een tekenreekswaarde toe die de sleutelnaam vertegenwoordigt aan de `MyMapOf_xsd_string_To_xsd_anyType_Item` object `key` veld. Deze waarde moet overeenkomen met de waarde van het PDF-bronelement dat is opgegeven in het DDX-document.
   * Wijs het `BLOB` object waarin het PDF-document is opgeslagen in het `MyMapOf_xsd_string_To_xsd_anyType_Item` object `value` veld.
   * Voeg de `MyMapOf_xsd_string_To_xsd_anyType_Item` aan `MyMapOf_xsd_string_To_xsd_anyType` object. De `MyMapOf_xsd_string_To_xsd_anyType` object `Add` en geeft de `MyMapOf_xsd_string_To_xsd_anyType` object. (Voer deze taak uit voor elk invoer-PDF-document en voor het XML-bladwijzerdocument.)

1. Stel runtime-opties in.

   * Een `AssemblerOptionSpec` object dat uitvoeringsopties opslaat met de constructor ervan.
   * Stel runtime-opties in om aan uw bedrijfsvereisten te voldoen door een waarde toe te wijzen aan een gegevenslid dat tot de `AssemblerOptionSpec` object. Bijvoorbeeld, om de dienst van de Assembler op te dragen om een baan te blijven verwerken wanneer een fout voorkomt, wijs toe `false` aan de `AssemblerOptionSpec` object `failOnError` lid.

1. Samenstellen van het PDF-document.

   De `AssemblerServiceClient` object `invokeDDX` en geeft de volgende waarden door:

   * A `BLOB` object dat staat voor het DDX-document
   * De `MyMapOf_xsd_string_To_xsd_anyType` array die de invoerdocumenten bevat
   * An `AssemblerOptionSpec` object dat uitvoeringsopties opgeeft

   De `invokeDDX` methode retourneert een `AssemblerResult` -object dat de resultaten van de taak en eventuele uitzonderingen bevat die zich hebben voorgedaan.

1. Sla het PDF-document op dat bladwijzers bevat.

   Voer de volgende handelingen uit om het nieuwe PDF-document te verkrijgen:

   * Toegang krijgen tot de `AssemblerResult` object `documents` veld, dat een `Map` -object dat de PDF-documenten van het resultaat bevat.
   * Doorlopen `Map` -object totdat u de sleutel vindt die overeenkomt met de naam van het resulterende document. Dan giet dat serielid `value` een `BLOB`.
   * Extraheer de binaire gegevens die het document van de PDF door tot zijn toegang te hebben vertegenwoordigen `BLOB` object `MTOM` veld. Hiermee wordt een array met bytes geretourneerd die u naar een PDF-bestand kunt schrijven.

**Zie ook**

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
