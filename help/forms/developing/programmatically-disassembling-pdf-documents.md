---
title: PDF-documenten programmatisch demonteren
description: Gebruik de dienst van de Assembler om één enkel document van PDF in veelvoudige documenten van PDF te demonteren gebruikend Java API en de Dienst API van het Web.
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
exl-id: c5e712e0-5c3f-48cd-91cf-fd347222a6b2
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Document Services
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '1749'
ht-degree: 0%

---

# PDF-documenten programmatisch demonteren {#programmatically-disassembling-pdf-documents}

**de Steekproeven en de voorbeelden in dit document zijn slechts voor AEM Forms op milieu JEE.**

U kunt een document van de PDF demonteren door het tot de dienst van de Assembler over te gaan. Deze taak is meestal handig wanneer het PDF-document oorspronkelijk is gemaakt op basis van veel afzonderlijke documenten, zoals een verzameling instructies. In de volgende afbeelding wordt DocA opgedeeld in meerdere resulterende documenten, waarbij de bladwijzer van het eerste niveau 1 op een pagina het begin van een nieuw resulterend document aangeeft.

![&#x200B; pd_pd_pdfsfrombookmarks &#x200B;](assets/pd_pd_pdfsfrombookmarks.png)

Als u een PDF-document wilt demonteren, controleert u of het `PDFsFromBookmarks` -element zich in het DDX-document bevindt. Het element `PDFsFromBookmarks` is een resulterend element en kan slechts een onderliggend element van het element `DDX` zijn. Het heeft geen attribuut `result` omdat het in de generatie van veelvoudige documenten kan resulteren.

Met het element `PDFsFromBookmarks` wordt één document gegenereerd voor elke bladwijzer van niveau 1 in het brondocument.

Voor deze bespreking, veronderstel het volgende Dx- document wordt gebruikt.

```xml
 <?xml version="1.0" encoding="UTF-8"?>
 <DDX xmlns="https://ns.adobe.com/DDX/1.0/">
      <PDFsFromBookmarks prefix="stmt">
     <PDF source="AssemblerResultPDF.pdf"/>
 </PDFsFromBookmarks>
 </DDX>
```

>[!NOTE]
>
>Alvorens deze sectie te lezen, adviseert men dat u met het assembleren van de documenten van PDF door de dienst van de Assembler vertrouwd bent. (Zie [&#x200B; Programmatiatically het assembleren van de Documenten van PDF &#x200B;](/help/forms/developing/programmatically-assembling-pdf-documents.md).)

>[!NOTE]
>
>Wanneer u één PDF-document doorgeeft aan de Assembler-service en één document terugkrijgt, kunt u de `invokeOneDocument` -bewerking aanroepen. Als u een PDF-document echter wilt demonteren, gebruikt u de `invokeDDX` -bewerking. Hoewel één invoerdocument wordt doorgegeven aan de Assembler-service, retourneert de Assembler-service een verzamelingsobject dat een of meer documenten bevat.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Assembler, zie [&#x200B; Verwijzing van de Diensten voor AEM Forms &#x200B;](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Voor meer informatie over een document DDX, zie [&#x200B; de Dienst van de Assembler en de Verwijzing DDX &#x200B;](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Overzicht van de stappen {#summary-of-steps}

Als u een PDF-document wilt demonteren, voert u de volgende taken uit:

1. Inclusief projectbestanden.
1. Maak een PDF Assembler-client.
1. Verwijs naar een bestaand DDX-document.
1. Verwijs naar een document van de PDF om te demonteren.
1. Stel runtime-opties in.
1. Haal het PDF-document uit elkaar.
1. Sla de gedemonteerde PDF-documenten op.

**omvat projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-assembler-client.jar
* adobe-utilities.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)

als AEM Forms wordt geïmplementeerd op een ondersteunde J2EE-toepassingsserver die geen JBoss is, moet u adobe-utilities.jar en jbossall-client.jar vervangen door JAR-bestanden die specifiek zijn voor de J2EE-toepassingsserver waarop AEM Forms wordt geïmplementeerd.

**creeer een cliënt van de Assembler van de PDF**

Alvorens u programmatically een verrichting van de Assembler kunt uitvoeren, moet u een de dienstcliënt van de Assembler tot stand brengen.

**Verwijzing een bestaand document DDX**

Er moet naar een DDX-document worden verwezen om een PDF-document te demonteren. Dit DDX-document moet het element `PDFsFromBookmarks` bevatten.

**Verwijzing een document van PDF om** te demonteren

Als u een PDF-document wilt demonteren, verwijst u naar een PDF-bestand dat het PDF-document vertegenwoordigt dat u wilt demonteren. Wanneer het tot de dienst van de Assembler wordt overgegaan, wordt een afzonderlijk document van PDF teruggegeven voor elke niveau 1 referentie in het document.

**vastgestelde runtime opties**

U kunt runtime opties plaatsen die het gedrag van de dienst van de Assembler controleren terwijl het een baan uitvoert. U kunt bijvoorbeeld een optie instellen die de Assembler-service de opdracht geeft door te gaan met het verwerken van een taak als er een fout optreedt.

**demonstreert het document van de PDF**

Nadat u de de dienstcliënt van de Assembler creeert, van verwijzingen het DX- document, van verwijzingen een document van de PDF aan demontable, en vastgestelde runtime opties, kunt u een document van de PDF dempen door de `invokeDDX` methode aan te halen. Mits het DDX-document instructies bevat voor het demonteren van het PDF-document, retourneert de Assembler-service gedemonteerde PDF-documenten binnen een verzamelingsobject.

**sparen de gedemonteerde documenten van de PDF**

Alle gedemonteerde PDF-documenten worden geretourneerd in een verzamelingsobject. Doorloop het verzamelingsobject en sla elk PDF-document op als een PDF-bestand.

**zie ook**

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[PDF-documenten programmatisch samenstellen](/help/forms/developing/programmatically-assembling-pdf-documents.md)

## Een PDF-document dempen met de Java API {#disassemble-a-pdf-document-using-the-java-api}

U kunt een PDF-document desassembleren met de Java-API (Assembler Service):

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-assembler-client.jar, op in het klassenpad van uw Java-project.

1. Maak een PDF Assembler-client.

   * Maak een `ServiceClientFactory` -object dat verbindingseigenschappen bevat.
   * Maak een `AssemblerServiceClient` -object door de constructor ervan te gebruiken en het `ServiceClientFactory` -object door te geven.

1. Verwijs naar een bestaand DDX-document.

   * Maak een `java.io.FileInputStream` -object dat het DDX-document vertegenwoordigt door de constructor ervan te gebruiken en een tekenreekswaarde door te geven die de locatie van het DDX-bestand aangeeft.
   * Maak een `com.adobe.idp.Document` -object door de constructor ervan te gebruiken en het `java.io.FileInputStream` -object door te geven.

1. Verwijs naar een document van de PDF om te demonteren.

   * Maak een `java.util.Map` -object dat wordt gebruikt om invoerdocumenten van de PDF op te slaan met behulp van een `HashMap` -constructor.
   * Maak een `java.io.FileInputStream` -object door de constructor ervan te gebruiken en de locatie van het PDF-document door te geven om te demonteren.
   * Maak een `com.adobe.idp.Document` -object en geef het `java.io.FileInputStream` -object door dat het PDF-document bevat dat moet worden gedemonteerd.
   * Voeg een item aan het object `java.util.Map` toe door de methode `put` ervan aan te roepen en de volgende argumenten door te geven:

      * Een tekenreekswaarde die de sleutelnaam vertegenwoordigt. Deze waarde moet overeenkomen met de waarde van het PDF-bronelement dat is opgegeven in het DDX-document.
      * Een `com.adobe.idp.Document` -object dat het PDF-document bevat dat moet worden gedemonteerd.

1. Stel runtime-opties in.

   * Maak een `AssemblerOptionSpec` -object dat uitvoeringsopties opslaat met behulp van de bijbehorende constructor.
   * Stel runtime-opties in om aan uw bedrijfsvereisten te voldoen door een methode aan te roepen die tot het `AssemblerOptionSpec` -object behoort. Als u bijvoorbeeld de Assembler-service de instructie wilt geven een taak te blijven verwerken wanneer een fout optreedt, roept u de methode `setFailOnError` van het object `AssemblerOptionSpec` aan en geeft u deze door `false` .

1. Haal het PDF-document uit elkaar.

   Roep de methode `invokeDDX` van het object `AssemblerServiceClient` aan en geef de volgende vereiste waarden door:

   * Een `com.adobe.idp.Document` -object dat het te gebruiken DDX-document vertegenwoordigt
   * Een `java.util.Map` -object dat het te demonteren PDF-document bevat
   * Een `com.adobe.livecycle.assembler.client.AssemblerOptionSpec` -object dat de runtime-opties opgeeft, inclusief het standaardfont en het logniveau van de taak

   De methode `invokeDDX` retourneert een `com.adobe.livecycle.assembler.client.AssemblerResult` -object dat de gedemonteerde PDF-documenten en eventuele uitzonderingen bevat.

1. Sla de gedemonteerde PDF-documenten op.

   Voer de volgende handelingen uit om de gedemonteerde PDF-documenten te verkrijgen:

   * Roep de methode `getDocuments` van het object `AssemblerResult` aan. Hiermee wordt een `java.util.Map` -object geretourneerd.
   * Doorloop het `java.util.Map` -object totdat u het resulterende `com.adobe.idp.Document` -object vindt.
   * Roep de methode `copyToFile` van het `com.adobe.idp.Document` -object aan om het PDF-document te extraheren.

**zie ook**

[PDF-documenten programmatisch demonteren](#programmatically-disassembling-pdf-documents)

[Snel starten (SOAP modus): Een PDF-document ontkoppelen met de Java API](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-disassembling-a-pdf-document-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Een PDF-document dempen met de webservice-API {#disassemble-a-pdf-document-using-the-web-service-api}

U kunt een PDF-document desassembleren met de API (webservice) van de Assembler-service:

1. Inclusief projectbestanden.

   Creeer een Microsoft .NET project dat MTOM gebruikt. Zorg ervoor dat u de volgende WSDL-definitie gebruikt wanneer u een serviceverwijzing instelt: `http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1` .

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
   * Maak een `System.IO.FileStream` -object door de constructor ervan aan te roepen. Geef een tekenreekswaarde door die staat voor de bestandslocatie van het DDX-document en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van het object `System.IO.FileStream` wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de eigenschap `Length` van het object `System.IO.FileStream` op te halen.
   * Vul de bytearray met streamgegevens door de methode `Read` van het object `System.IO.FileStream` aan te roepen en de bytearray, de startpositie en de lengte van de stream door te geven om te lezen.
   * Vul het object `BLOB` door de eigenschap `MTOM` ervan toe te wijzen met de inhoud van de bytearray.

1. Verwijs naar een document van de PDF om te demonteren.

   * Maak een `BLOB` -object met behulp van de constructor. Het `BLOB` -object wordt gebruikt om het invoer-PDF-document op te slaan. Dit `BLOB` -object wordt als een argument aan `invokeOneDocument` doorgegeven.
   * Maak een `System.IO.FileStream` -object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het PDF-invoerdocument en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van het object `System.IO.FileStream` wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de eigenschap `Length` van het object `System.IO.FileStream` op te halen.
   * Vul de bytearray met streamgegevens door de methode `Read` van het object `System.IO.FileStream` aan te roepen en de bytearray, de startpositie en de lengte van de stream door te geven om te lezen.
   * Vul het `BLOB` -object door het `MTOM` -veld ervan de inhoud van de bytearray toe te wijzen.
   * Maak een `MyMapOf_xsd_string_To_xsd_anyType` -object. Dit verzamelingsobject wordt gebruikt om de PDF op te slaan die moet worden gedemonteerd.
   * Maak een `MyMapOf_xsd_string_To_xsd_anyType_Item` -object.
   * Wijs een tekenreekswaarde toe die de sleutelnaam vertegenwoordigt aan het veld `key` van het `MyMapOf_xsd_string_To_xsd_anyType_Item` -object. Deze waarde moet overeenkomen met de waarde van het PDF-bronelement dat is opgegeven in het DDX-document.
   * Wijs het `BLOB` -object toe dat het PDF-document opslaat in het veld `MyMapOf_xsd_string_To_xsd_anyType_Item` object `value` .
   * Voeg het object `MyMapOf_xsd_string_To_xsd_anyType_Item` toe aan het object `MyMapOf_xsd_string_To_xsd_anyType` . Roep de methode `MyMapOf_xsd_string_To_xsd_anyType` object&#39; `Add` aan en geef het object `MyMapOf_xsd_string_To_xsd_anyType` door.

1. Stel runtime-opties in.

   * Maak een `AssemblerOptionSpec` -object dat uitvoeringsopties opslaat met behulp van de bijbehorende constructor.
   * Stel runtime-opties in om aan uw bedrijfsvereisten te voldoen door een waarde toe te wijzen aan een gegevenslid dat tot het `AssemblerOptionSpec` -object behoort. Als u bijvoorbeeld de Assembler-service wilt instrueren een taak te blijven verwerken wanneer een fout optreedt, wijst u `false` toe aan het veld `AssemblerOptionSpec` object `failOnError` .

1. Haal het PDF-document uit elkaar.

   Roep de methode `invokeDDX` van het object `AssemblerServiceClient` aan en geef de volgende waarden door:

   * Een `BLOB` -object dat staat voor het DDX-document dat het PDF-document demonteert
   * Het `MyMapOf_xsd_string_To_xsd_anyType` -object dat het te demonteren PDF-document bevat
   * Een `AssemblerOptionSpec` -object dat uitvoeringsopties opgeeft

   De methode `invokeDDX` retourneert een `AssemblerResult` -object dat de taakresultaten en eventuele uitzonderingen bevat die zijn opgetreden.

1. Sla de gedemonteerde PDF-documenten op.

   Voer de volgende handelingen uit om de nieuwe PDF-documenten te verkrijgen:

   * Open het veld `documents` van het `AssemblerResult` -object (een `Map` -object dat de gedemonteerde PDF-documenten bevat).
   * Doorloop het `Map` -object om elk resulterend document te verkrijgen. Vervolgens cast u het element `value` van dat arraylid naar een `BLOB` .
   * Extraheer de binaire gegevens die het PDF-document vertegenwoordigen door de eigenschap `MTOM` van het object `BLOB` te openen. Hiermee wordt een array met bytes geretourneerd die u naar een PDF-bestand kunt schrijven.

**zie ook**

[PDF-documenten programmatisch demonteren](#programmatically-disassembling-pdf-documents)

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
