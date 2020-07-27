---
title: PDF-documenten samenstellen met bladwijzers
seo-title: PDF-documenten samenstellen met bladwijzers
description: 'null'
seo-description: 'null'
uuid: a306d2a6-0b12-4eb3-bff4-968a33417486
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 9f4711a8-033c-4051-ab41-65a26838899b
translation-type: tm+mt
source-git-commit: 1343cc33a1e1ce26c0770a3b49317e82353497ab
workflow-type: tm+mt
source-wordcount: '2526'
ht-degree: 0%

---


# PDF-documenten samenstellen met bladwijzers {#assembling-pdf-documents-with-bookmarks}

U kunt een PDF-document samenstellen dat bladwijzers bevat. Stel dat u een PDF-document hebt dat geen bladwijzers bevat en dat u het document wilt wijzigen door bladwijzers op te geven. Met de Assembler-service kunt u een PDF-document zonder bladwijzers doorgeven en een PDF-document met bladwijzers terugkrijgen.

Bladwijzers bevatten de volgende eigenschappen:

* Een titel die als tekst op het scherm verschijnt.
* Een handeling die aangeeft wat er gebeurt wanneer een gebruiker op de bladwijzer klikt. De gebruikelijke actie voor een bladwijzer is het verplaatsen naar een andere locatie in het huidige document of het openen van een ander PDF-document, hoewel u andere handelingen kunt opgeven.

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

Binnen dit DDX-document wordt de waarde toegewezen aan het bronkenmerk `Loan.pdf`. Dit DDX-document geeft aan dat één PDF-document wordt doorgegeven aan de Assembler-service. Wanneer u een PDF-document samenstelt met bladwijzers, moet u een XML-bladwijzerdocument opgeven dat de bladwijzers in het resulterende document beschrijft. Als u een XML-bladwijzerdocument wilt opgeven, moet u controleren of het `Bookmarks` element is opgegeven in uw DDX-document.

In dit voorbeeld-DDX-document geeft het `Bookmarks` element `doc2` als waarde op. Deze waarde wijst erop dat de inputkaart die tot de dienst van de Assembler wordt overgegaan een genoemde sleutel bevat `doc2`. De waarde van de `doc2` sleutel is een `com.adobe.idp.Document` waarde die het bladwijzerdocument van XML vertegenwoordigt. (Zie &quot;Taal van Bladwijzers&quot;in de [Dienst van de Assembler en DX Verwijzing](https://www.adobe.com/go/learn_aemforms_ddx_63).)

In dit onderwerp wordt de volgende taal voor XML-bladwijzers gebruikt om een PDF-document met bladwijzers samen te stellen.

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

In dit XML-bladwijzerdocument ziet u het element Handeling dat de handeling definieert die wordt uitgevoerd wanneer een gebruiker op de bladwijzer klikt. Onder het element Handeling bevindt zich het element Launch dat toepassingen start, zoals NotePad, en bestanden opent, zoals PDF-bestanden. Als u een PDF-bestand wilt openen, moet u het element Bestand gebruiken dat het bestand aangeeft dat moet worden geopend. In het XML-bladwijzerbestand dat in deze sectie is opgegeven, is LoanDetails.pdf de naam van het bestand dat wordt geopend.

>[!NOTE]
>
>Voor volledige details over gesteunde acties, zie &quot; `Action` element&quot;in de Dienst van de [Assembler en Verwijzing](https://www.adobe.com/go/learn_aemforms_ddx_63)DDX.

Gezien het DDX-document dat in deze sectie is opgegeven en het XML-bladwijzerbestand als invoer, stelt de Assembler-service een PDF-document samen dat de volgende bladwijzers bevat.

![aw_aw_bmark](assets/aw_aw_bmark.png)

Wanneer een gebruiker op de *Open referentie Loan Details* klikt, wordt LoanDetails.pdf geopend. Op dezelfde manier wordt NotePad gestart wanneer de gebruiker op de bladwijzer *Launch NotePad* klikt.

>[!NOTE]
>
>Voordat u deze sectie leest, is het raadzaam om vertrouwd te zijn met het samenstellen van PDF-documenten met de Assembler-service. Deze sectie bespreekt geen concepten, zoals het creëren van een inzamelingsvoorwerp dat inputdocumenten of het leren hoe te om de resultaten uit het teruggekeerde inzamelingsvoorwerp te halen bevat. (Zie PDF-documenten [programmatisch samenstellen](/help/forms/developing/programmatically-assembling-pdf-documents.md#programmatically-assembling-pdf-documents).)

>[!NOTE]
>
>Voor meer informatie over de dienst van de Assembler, zie de Verwijzing van de [Diensten voor AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Voor meer informatie over een DX- document, zie de Dienst van de [Assembler en de Verwijzing](https://www.adobe.com/go/learn_aemforms_ddx_63)DDX.

## Overzicht van de stappen {#summary-of-steps}

Voer de volgende taken uit om een PDF-document met bladwijzers samen te stellen:

1. Inclusief projectbestanden.
1. Maak een PDF Assembler-client.
1. Verwijs naar een bestaand DDX-document.
1. Verwijs naar een PDF-document waaraan bladwijzers worden toegevoegd.
1. Verwijs naar het XML-document van de bladwijzer.
1. Voeg het PDF-document en het XML-bladwijzerdocument toe aan een Kaartenverzameling.
1. Stel runtime-opties in.
1. Stel het PDF-document samen.
1. Sla het PDF-document met bladwijzers op.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-assembler-client.jar
* adobe-utilities.jar (vereist als AEM Forms worden geïmplementeerd op JBoss)
* jbossall-client.jar (vereist als AEM Forms worden geïmplementeerd op JBoss)

als AEM Forms worden geïmplementeerd op een andere ondersteunde J2EE-toepassingsserver dan JBoss, moet u de bestanden adobe-utilities.jar en jbossall-client.jar vervangen door JAR-bestanden die specifiek zijn voor de J2EE-toepassingsserver waarop AEM Forms worden geïmplementeerd. Zie [Including AEM Forms Java library files](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)voor informatie over de locatie van alle JAR-bestanden voor AEM Forms.

**Een PDF Assembler-client maken**

Alvorens u programmatically een verrichting van de Assembler kunt uitvoeren, moet u een de dienstcliënt van de Assembler tot stand brengen.

**Verwijzen naar een bestaand DDX-document**

Er moet naar een DDX-document worden verwezen om een PDF-document samen te stellen. Dit DDX-document moet het `Bookmarks` element bevatten dat de Assembler-service de instructie geeft een PDF samen te stellen die bladwijzers bevat. (Zie het DDX-document dat eerder in deze sectie wordt weergegeven voor een voorbeeld.)

**Verwijzen naar een PDF-document waaraan bladwijzers worden toegevoegd**

Verwijs naar een PDF-document waaraan bladwijzers worden toegevoegd. Het maakt niet uit of het PDF-document waarnaar wordt verwezen al bladwijzers bevat. Als het `Bookmarks` element een onderliggend element van het PDF-bronelement is, worden de bestaande bladwijzers in de PDF-bron vervangen door de bladwijzers. Als u echter de bestaande bladwijzers wilt behouden, moet u ervoor zorgen dat dit een nevenfunctie van het PDF-bronelement `Bookmarks` is. Neem bijvoorbeeld het volgende voorbeeld:

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
>Zie &quot;Taal van Bladwijzers&quot;in de Dienst van de [Assembler en de Verwijzing](https://www.adobe.com/go/learn_aemforms_ddx_63)DDX.

**Het PDF-document en het XML-bladwijzerdocument toevoegen aan een Map-verzameling**

U moet zowel het PDF-document waaraan bladwijzers worden toegevoegd als het XML-bladwijzerdocument aan de Kaartenverzameling toevoegen. Daarom bevat het verzamelingsobject Map twee elementen: een PDF-document en het XML-bladwijzerdocument.

**Uitvoeringsopties instellen**

U kunt runtime opties plaatsen die het gedrag van de dienst van de Assembler controleren terwijl het een baan uitvoert. U kunt bijvoorbeeld een optie instellen die de Assembler-service de opdracht geeft door te gaan met het verwerken van een taak als er een fout optreedt. Zie de `AssemblerOptionSpec` klasseverwijzing in de API-naslaggids voor [AEM Forms voor informatie over de runtime-opties die u kunt instellen](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**Het PDF-document samenstellen**

Als u een PDF-document met nieuwe bladwijzers wilt samenstellen, gebruikt u de `invokeDDX` bewerking van de Assembler-service. De reden waarom u de `invokeDDX` verrichting in tegenstelling tot andere de dienstverrichtingen van de Assembler zoals moet gebruiken `invokeOneDocument` is omdat de dienst van de Assembler een document van referentieXML vereist dat binnen het de inzamelingsvoorwerp van de Kaart wordt overgegaan. Dit object is een parameter van de `invokeDDX` bewerking.

**Het PDF-document met bladwijzers opslaan**

U moet de resultaten extraheren uit het geretourneerde object Map en het bijbehorende PDF-document opslaan. (Zie &quot;De resultaten extraheren&quot; in PDF-documenten [programmatisch samenstellen](/help/forms/developing/programmatically-assembling-pdf-documents.md).)

**Zie ook**

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[PDF-documenten programmatisch samenstellen](/help/forms/developing/programmatically-assembling-pdf-documents.md)

## PDF-documenten samenstellen met bladwijzers met behulp van de Java API {#assemble-pdf-documents-with-bookmarks-using-the-java-api}

U kunt een PDF-document samenstellen met bladwijzers met behulp van de API (Java) voor vergaderingsservice:

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-assembler-client.jar, op in het klassenpad van uw Java-project.

1. Maak een PDF Assembler-client.

   * Maak een `ServiceClientFactory` object dat verbindingseigenschappen bevat. (Zie Verbindingseigenschappen [instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)
   * Maak een `AssemblerServiceClient` object door de constructor ervan te gebruiken en het `ServiceClientFactory` object door te geven.

1. Verwijs naar een bestaand DDX-document.

   * Maak een `java.io.FileInputStream` object dat het DDX-document vertegenwoordigt door de constructor ervan te gebruiken en een tekenreekswaarde door te geven die de locatie van het DDX-bestand aangeeft.
   * Maak een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en het `java.io.FileInputStream` object door te geven.

1. Verwijs naar een PDF-document waaraan bladwijzers worden toegevoegd.

   * Maak een `java.io.FileInputStream` object door de constructor ervan te gebruiken en de locatie van het PDF-document door te geven.
   * Maak een `com.adobe.idp.Document` object met de constructor en geef het `java.io.FileInputStream` object met het PDF-document door.

1. Verwijs naar het XML-document van de bladwijzer.

   * Maak een `java.io.FileInputStream` object door de constructor ervan te gebruiken en de locatie door te geven van het XML-bestand dat het XML-bladwijzerdocument vertegenwoordigt.
   * Maak een `com.adobe.idp.Document` object en geef het `java.io.FileInputStream` object met het PDF-document door.

1. Voeg het PDF-document en het XML-bladwijzerdocument toe aan een Kaartenverzameling.

   * Maak een `java.util.Map` object waarin zowel het invoer-PDF-document als het XML-bladwijzerdocument worden opgeslagen.
   * Voeg het PDF-invoerdocument toe door de methode van het `java.util.Map` `put` object aan te roepen en de volgende argumenten door te geven:

      * Een tekenreekswaarde die de sleutelnaam vertegenwoordigt. Deze waarde moet overeenkomen met de waarde van het PDF-bronelement dat is opgegeven in het DDX-document.
      * Een `com.adobe.idp.Document` object dat het invoer-PDF-document bevat.
   * Voeg het XML-document van de bladwijzer toe door de methode van het `java.util.Map` `put` object aan te roepen en de volgende argumenten door te geven:

      * Een tekenreekswaarde die de sleutelnaam vertegenwoordigt. Deze waarde moet overeenkomen met de waarde van het bronelement Bladwijzers dat is opgegeven in het DDX-document.
      * Een `com.adobe.idp.Document` object dat het XML-bladwijzerdocument bevat.


1. Stel runtime-opties in.

   * Maak een `AssemblerOptionSpec` object dat uitvoeringsopties opslaat met de constructor ervan.
   * Stel runtime-opties in om aan uw bedrijfsvereisten te voldoen door een methode aan te roepen die tot het `AssemblerOptionSpec` object behoort. Bijvoorbeeld, om de dienst van de Assembler op te dragen om een baan te blijven verwerken wanneer een fout voorkomt, haalt de methode van `AssemblerOptionSpec` objecten aan en gaat over `setFailOnError` `false`.

1. Stel het PDF-document samen.

   Roep de `AssemblerServiceClient` methode van het `invokeDDX` object aan en geef de volgende vereiste waarden door:

   * Een `com.adobe.idp.Document` object dat staat voor het te gebruiken DDX-document
   * Een `java.util.Map` object dat zowel het invoer-PDF-document als het XML-bladwijzerdocument bevat.
   * Een `com.adobe.livecycle.assembler.client.AssemblerOptionSpec` object dat de runtime-opties opgeeft, inclusief standaardniveau voor lettertypen en taaklogbestanden

   De `invokeDDX` methode retourneert een `com.adobe.livecycle.assembler.client.AssemblerResult` object dat de resultaten van de taak en eventuele uitzonderingen bevat die zich hebben voorgedaan.

1. Sla het PDF-document met bladwijzers op.

   Voer de volgende handelingen uit om het nieuwe PDF-document te verkrijgen:

   * Roep de `AssemblerResult` methode van het `getDocuments` object aan. Hiermee wordt een `java.util.Map` object geretourneerd.
   * Doorloop het `java.util.Map` object totdat u het resulterende `com.adobe.idp.Document` object vindt. (U kunt het PDF-resultaatelement dat in het DDX-document is opgegeven, gebruiken om het document op te halen.)
   * Roep de `com.adobe.idp.Document` methode van het `copyToFile` object aan om het PDF-document uit te pakken.

**Zie ook**

[Snel starten (SOAP-modus): PDF-documenten samenstellen met bladwijzers met behulp van de Java API](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-assembling-pdf-documents-with-bookmarks-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## PDF-documenten samenstellen met bladwijzers met behulp van de webservice-API {#assemble-pdf-documents-with-bookmarks-using-the-web-service-api}

U kunt een PDF-document samenstellen met bladwijzers met behulp van de API (webservice) van de Assembler Service:

1. Inclusief projectbestanden.

   Creeer een project van Microsoft .NET dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een PDF Assembler-client.

   * Maak een `AssemblerServiceClient` object met de standaardconstructor.
   * Maak een `AssemblerServiceClient.Endpoint.Address` object met de `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde door die de WSDL opgeeft voor de service AEM Forms (bijvoorbeeld `http://localhost:8080/soap/services/AssemblerService?blob=mtom`). U hoeft het `lc_version` kenmerk niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.
   * Maak een `System.ServiceModel.BasicHttpBinding` object door de waarde van het `AssemblerServiceClient.Endpoint.Binding` veld op te halen. Kiezen naar de geretourneerde waarde `BasicHttpBinding`.
   * Stel het `System.ServiceModel.BasicHttpBinding` veld van het `MessageEncoding` object in op `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam voor AEM-formulieren toe aan het veld `AssemblerServiceClient.ClientCredentials.UserName.UserName`.
      * Wijs de bijbehorende wachtwoordwaarde aan het veld toe `AssemblerServiceClient.ClientCredentials.UserName.Password`.
      * Wijs de constante waarde toe `HttpClientCredentialType.Basic` aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Wijs de constante waarde toe `BasicHttpSecurityMode.TransportCredentialOnly` aan het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Verwijs naar een bestaand DDX-document.

   * Maak een `BLOB` object met de constructor ervan. Het `BLOB` object wordt gebruikt om het DDX-document op te slaan.
   * Maak een `System.IO.FileStream` object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het DDX-document en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van het `System.IO.FileStream` object wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` eigenschap van het `Length` object op te halen.
   * Vul de bytearray met streamgegevens door de methode van het `System.IO.FileStream` `Read` object aan te roepen en de bytearray, de startpositie en de lengte van de stream door te geven om te lezen.
   * Vul het `BLOB` object door het `MTOM` veld ervan toe te wijzen met de inhoud van de bytearray.

1. Verwijs naar een PDF-document waaraan bladwijzers worden toegevoegd.

   * Maak een `BLOB` object met de constructor ervan. Het `BLOB` object wordt gebruikt om de invoer-PDF op te slaan.
   * Maak een `System.IO.FileStream` object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het invoer-PDF-document en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van het `System.IO.FileStream` object wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` eigenschap van het `Length` object op te halen.
   * Vul de bytearray met streamgegevens door de methode van het `System.IO.FileStream` `Read` object aan te roepen en de bytearray, de startpositie en de lengte van de stream door te geven om te lezen.
   * Vul het `BLOB` object door het `MTOM` veld ervan toe te wijzen met de inhoud van de bytearray.

1. Verwijs naar het XML-document van de bladwijzer.

   * Maak een `BLOB` object met de constructor ervan. Het `BLOB` object wordt gebruikt om het XML-bladwijzerdocument op te slaan.
   * Maak een `System.IO.FileStream` object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het invoer-PDF-document en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van het `System.IO.FileStream` object wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` eigenschap van het `Length` object op te halen.
   * Vul de bytearray met streamgegevens door de methode van het `System.IO.FileStream` `Read` object aan te roepen en de bytearray, de startpositie en de lengte van de stream door te geven om te lezen.
   * Vul het `BLOB` object door het `MTOM` veld ervan toe te wijzen met de inhoud van de bytearray.

1. Voeg het PDF-document en het XML-bladwijzerdocument toe aan een Kaartenverzameling.

   * Create a `MyMapOf_xsd_string_To_xsd_anyType` object. Dit verzamelingsobject wordt gebruikt om de invoer-PDF-documenten en het XML-bladwijzerdocument op te slaan.
   * Maak voor elk invoer-PDF-document en het XML-bladwijzerdocument een `MyMapOf_xsd_string_To_xsd_anyType_Item` object.
   * Wijs een tekenreekswaarde toe die de sleutelnaam aan het `MyMapOf_xsd_string_To_xsd_anyType_Item` `key` gebied van het voorwerp vertegenwoordigt. Deze waarde moet overeenkomen met de waarde van het PDF-bronelement dat is opgegeven in het DDX-document.
   * Wijs het `BLOB` object waarin het PDF-document is opgeslagen, toe aan het `MyMapOf_xsd_string_To_xsd_anyType_Item` veld van het `value` object.
   * Voeg het `MyMapOf_xsd_string_To_xsd_anyType_Item` object toe aan het `MyMapOf_xsd_string_To_xsd_anyType` object. Roep de `MyMapOf_xsd_string_To_xsd_anyType` methode van het `Add` object aan en geef het `MyMapOf_xsd_string_To_xsd_anyType` object door. (Voer deze taak uit voor elk invoer-PDF-document en voor het XML-bladwijzerdocument.)

1. Stel runtime-opties in.

   * Maak een `AssemblerOptionSpec` object dat uitvoeringsopties opslaat met de constructor ervan.
   * Stel runtime-opties in om aan uw bedrijfsvereisten te voldoen door een waarde toe te wijzen aan een gegevenslid dat tot het `AssemblerOptionSpec` object behoort. Bijvoorbeeld, om de dienst van de Assembler op te dragen om een baan te blijven verwerken wanneer een fout voorkomt, wijs `false` aan het de `AssemblerOptionSpec` gegevenslid van het `failOnError` voorwerp toe.

1. Stel het PDF-document samen.

   Roep de methode van het `AssemblerServiceClient` `invokeDDX` object aan en geef de volgende waarden door:

   * Een `BLOB` object dat staat voor het DDX-document
   * De `MyMapOf_xsd_string_To_xsd_anyType` array die de invoerdocumenten bevat
   * Een `AssemblerOptionSpec` object dat uitvoeringsopties opgeeft

   De `invokeDDX` methode retourneert een `AssemblerResult` object dat de resultaten van de taak en eventuele uitzonderingen bevat die zich hebben voorgedaan.

1. Sla het PDF-document met bladwijzers op.

   Voer de volgende handelingen uit om het nieuwe PDF-document te verkrijgen:

   * Open het `AssemblerResult` veld van het `documents` object. Dit is een `Map` object dat de PDF-resultaatdocumenten bevat.
   * Doorloop het `Map` object totdat u de sleutel vindt die overeenkomt met de naam van het resulterende document. Dan giet dat serielid `value` aan een `BLOB`.
   * Pak de binaire gegevens die het PDF-document vertegenwoordigen, uit door het `BLOB` objectveld `MTOM` te openen. Hiermee wordt een array met bytes geretourneerd die u naar een PDF-bestand kunt schrijven.

**Zie ook**

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
