---
title: PDF-documenten programmatisch samenstellen
description: Gebruik de Assembler service-API om meerdere PDF-documenten samen te stellen tot één PDF-document met de Java API en de Web Service-API.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
exl-id: 7d6fd230-e477-4286-9fb3-18a3474e3e48
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Document Services
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '2105'
ht-degree: 0%

---

# PDF-documenten programmatisch samenstellen {#programmatically-assembling-pdf-documents}

**de Steekproeven en de voorbeelden in dit document zijn slechts voor AEM Forms op milieu JEE.**

Met de API voor vergaderingsservice kunt u meerdere PDF-documenten samenvoegen tot één PDF-document. In de volgende afbeelding ziet u drie PDF-documenten die worden samengevoegd in één PDF-document.

![ pa_pa_document_assembly ](assets/pa_pa_document_assembly.png)

U hebt een DDX-document nodig om twee of meer PDF-documenten samen te voegen tot één PDF-document. Een DX-document beschrijft het PDF-document dat de Assembler-service produceert. Namelijk draagt het DDX- document de dienst van de Assembler op welke acties om uit te voeren.

Voor deze bespreking, veronderstel dat het volgende DDX- document wordt gebruikt.

```xml
 <?xml version="1.0" encoding="UTF-8"?>
 <DDX xmlns="https://ns.adobe.com/DDX/1.0/">
     <PDF result="out.pdf">
         <PDF source="map.pdf" />
         <PDF source="directions.pdf" />
     </PDF>
 </DDX>
```

Dit DX- document voegt twee PDF documenten genoemd *map.pdf* en *richtingen.pdf* in één enkel document van PDF samen.

>[!NOTE]
>
>Om een Dx- document te zien dat een document van de PDF demonteert, zie [ Programmatiatically het demonteren van de Documenten van de PDF ](/help/forms/developing/programmatically-disassembling-pdf-documents.md#programmatically-disassembling-pdf-documents).

>[!NOTE]
>
>Voor meer informatie over de dienst van de Assembler, zie [ Verwijzing van de Diensten voor AEM Forms ](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Voor meer informatie over een document DDX, zie [ de Dienst van de Assembler en de Verwijzing DDX ](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Overwegingen bij het aanroepen van de Assembler-service met behulp van webservices {#considerations-when-invoking-assembler-service-using-web-services}

Wanneer u kop- en voetteksten toevoegt tijdens het samenstellen van grote documenten, kan er een `OutOfMemory` -fout optreden en worden de bestanden niet samengevoegd. Om de kans te verminderen dat dit probleem zich voordoet, voegt u een `DDXProcessorSetting` -element toe aan uw DDX-document, zoals in het volgende voorbeeld wordt getoond.

`<DDXProcessorSetting name="checkpoint" value="2000" />`

U kunt dit element toevoegen als een onderliggend element van het element `DDX` of als een onderliggend element van een element `PDF result` . De standaardwaarde voor deze instelling is 0 (nul). Hiermee wordt het aanwijzen uitgeschakeld en gedraagt de DDX zich alsof het element `DDXProcessorSetting` niet aanwezig is. Als u een `OutOfMemory` -fout hebt aangetroffen, moet u de waarde mogelijk op een geheel getal instellen, meestal tussen 500 en 5000. Een kleine controlepuntwaarde resulteert in frequentere controle die.

## Overzicht van de stappen {#summary-of-steps}

Als u één PDF-document wilt samenstellen op basis van meerdere PDF-documenten, voert u de volgende taken uit:

1. Inclusief projectbestanden.
1. Maak een PDF Assembler-client.
1. Verwijs naar een bestaand DDX-document.
1. Referentie-invoer PDF-documenten.
1. Stel runtime-opties in.
1. Stel de invoerdocumenten PDF samen.
1. Extraheer de resultaten.

**omvat projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-assembler-client.jar
* adobe-utilities.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)

als AEM Forms wordt geïmplementeerd op een andere ondersteunde J2EE-toepassingsserver dan JBoss, moet u de bestanden adobe-utilities.jar en jbossall-client.jar vervangen door JAR-bestanden die specifiek zijn voor de J2EE-toepassingsserver waarop AEM Forms wordt geïmplementeerd.

**creeer een cliënt van de Assembler van de PDF**

Voordat u een Assembler-bewerking programmatisch kunt uitvoeren, moet u een Assembler-client maken.

**Verwijzing een bestaand document DDX**

Er moet naar een DDX-document worden verwezen om een PDF-document samen te stellen. Neem bijvoorbeeld het DDX-document dat in deze sectie is geïntroduceerd. Dit DDX-document geeft de Assembler-service de opdracht om twee PDF-documenten samen te voegen tot één PDF-document.

**de documenten van de inputPDF van de Verwijzing**

Referentie-invoer PDF documenten die u aan de dienst van de Assembler wilt overgaan. Als u bijvoorbeeld twee invoerdocumenten met de naam Kaart en Richtingen wilt doorgeven, moet u de bijbehorende PDF-PDF-bestanden doorgeven.

Zowel het bestand map.pdf als het bestand direction.pdf moeten in een verzamelingsobject worden geplaatst. De naam van de sleutel moet de waarde van het PDF bronattribuut in het DX- document aanpassen. Het maakt niet uit wat de naam van het PDF-bestand is als de sleutel en het bronkenmerk in het DDX-document overeenkomen.

>[!NOTE]
>
>Een `AssemblerResult` -object dat een verzamelingsobject bevat, wordt geretourneerd wanneer u de `invokeDDX` -bewerking aanroept. Deze bewerking wordt gebruikt wanneer u twee of meer invoerdocumenten van PDF doorgeeft aan de Assembler-service. Als u echter slechts één invoercode-PDF doorgeeft aan de Assembler-service en slechts één retourdocument verwacht, roept u de bewerking `invokeOneDocument` aan. Bij het aanroepen van deze bewerking wordt één document geretourneerd. Voor informatie over het gebruiken van deze verrichting, zie [ Assemblbling de Documenten van de PDF ](/help/forms/developing/assembling-encrypted-pdf-documents.md#assembling-encrypted-pdf-documents).

**vastgestelde runtime opties**

U kunt runtime opties plaatsen die het gedrag van de dienst van de Assembler controleren terwijl het een baan uitvoert. U kunt bijvoorbeeld een optie instellen die de Assembler-service de opdracht geeft door te gaan met het verwerken van een taak als er een fout optreedt. Voor informatie over de runtime opties die u kunt plaatsen, zie de `AssemblerOptionSpec` klassenverwijzing in [ AEM Forms API Verwijzing ](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**assembleer de documenten van de inputPDF**

Nadat u de de dienstcliënt creeert, verwijs een DX- dossier, creeer een inzamelingsvoorwerp dat de documenten van de inputPDF opslaat, en vastgestelde runtime opties, kunt u de verrichting DDX aanhalen. Wanneer u het DDX-document gebruikt dat in deze sectie is opgegeven, worden de bestanden map.pdf en direction.pdf samengevoegd in één PDF-document.

**Extraheer de resultaten**

De service Assembler retourneert een `java.util.Map` -object dat kan worden opgehaald uit het `AssemblerResult` -object en dat bewerkingsresultaten bevat. Het geretourneerde `java.util.Map` -object bevat de resulterende documenten en eventuele uitzonderingen.

De volgende tabel bevat een overzicht van enkele sleutelwaarden en objecttypen die in het geretourneerde `java.util.Map` -object kunnen voorkomen.

<table>
 <thead>
  <tr>
   <th><p>Sleutelwaarde</p></th>
   <th><p>Objecttype</p></th>
   <th><p>Beschrijving</p></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p><code><i>documentName</i></code></p></td>
   <td><p><code>com.adobe.idp.Document</code></p></td>
   <td><p>Bevat de resulterende documenten die in een DX resulterend element worden gespecificeerd</p></td>
  </tr>
  <tr>
   <td><p><code><i>documentName</i></code></p></td>
   <td><p><code>Exception</code></p></td>
   <td><p>Bevat een uitzondering voor het document</p></td>
  </tr>
  <tr>
   <td><p><code>OutputMapConstants.LOG_NAME</code></p></td>
   <td><p><code>com.adobe.idp.Documen</code></p></td>
   <td><p>Bevat het taaklogboek</p></td>
  </tr>
 </tbody>
</table>

**zie ook**

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[PDF-documenten programmatisch demonteren](/help/forms/developing/programmatically-disassembling-pdf-documents.md#programmatically-disassembling-pdf-documents)

## PDF-documenten samenstellen met de Java API {#assemble-pdf-documents-using-the-java-api}

U kunt een PDF-document samenstellen met behulp van de API (Java) voor vergaderingsservice:

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-assembler-client.jar, op in het klassenpad van uw Java-project.

1. Maak een PDF Assembler-client.

   * Maak een `ServiceClientFactory` -object dat verbindingseigenschappen bevat.
   * Maak een `AssemblerServiceClient` -object door de constructor ervan te gebruiken en het `ServiceClientFactory` -object door te geven.

1. Verwijs naar een bestaand DDX-document.

   * Maak een `java.io.FileInputStream` -object dat het DDX-document vertegenwoordigt door de constructor ervan te gebruiken en een tekenreekswaarde door te geven die de locatie van het DDX-bestand aangeeft.
   * Maak een `com.adobe.idp.Document` -object door de constructor ervan te gebruiken en het `java.io.FileInputStream` -object door te geven.

1. Referentie-invoer PDF-documenten.

   * Maak een `java.util.Map` -object dat wordt gebruikt om invoerdocumenten van de PDF op te slaan met behulp van een `HashMap` -constructor.
   * Maak voor elk invoerdocument een `java.io.FileInputStream` -object door de constructor ervan te gebruiken en de locatie van het invoerdocument door te geven.
   * Maak voor elk invoerdocument een `com.adobe.idp.Document` -object en geef het `java.io.FileInputStream` -object door dat het PDF PDF-document bevat.
   * Voeg voor elk invoerdocument een item aan het `java.util.Map` -object toe door de methode `put` ervan aan te roepen en de volgende argumenten door te geven:

      * Een tekenreekswaarde die de sleutelnaam vertegenwoordigt. Deze waarde moet overeenkomen met de waarde van het PDF-bronelement dat is opgegeven in het DDX-document.
      * Een `com.adobe.idp.Document` -object (of `java.util.List` -object dat meerdere documenten opgeeft) dat het PDF-brondocument bevat.

1. Stel runtime-opties in.

   * Maak een `AssemblerOptionSpec` -object dat uitvoeringsopties opslaat met behulp van de bijbehorende constructor.
   * Stel runtime-opties in om aan uw bedrijfsvereisten te voldoen door een methode aan te roepen die tot het `AssemblerOptionSpec` -object behoort. Als u bijvoorbeeld wilt dat de Assembler-service een taak blijft verwerken wanneer een fout optreedt, roept u de methode `setFailOnError` van het object `AssemblerOptionSpec` aan en geeft u deze door `false` .

1. Stel de invoerdocumenten PDF samen.

   Roep de methode `invokeDDX` van het object `AssemblerServiceClient` aan en geef de volgende vereiste waarden door:

   * Een `com.adobe.idp.Document` -object dat het te gebruiken DDX-document vertegenwoordigt
   * Een `java.util.Map` -object dat de invoerbestanden voor PDF bevat die moeten worden samengesteld
   * Een `com.adobe.livecycle.assembler.client.AssemblerOptionSpec` -object dat de runtime-opties opgeeft, inclusief het standaardniveau voor lettertypen en taaklogbestanden

   De methode `invokeDDX` retourneert een `com.adobe.livecycle.assembler.client.AssemblerResult` -object dat de resultaten van de taak en eventuele uitzonderingen bevat die zijn opgetreden.

1. Extraheer de resultaten.

   Voer de volgende handelingen uit om het nieuwe PDF-document te verkrijgen:

   * Roep de methode `getDocuments` van het object `AssemblerResult` aan. Hiermee wordt een `java.util.Map` -object geretourneerd.
   * Doorloop het `java.util.Map` -object totdat u het resulterende `com.adobe.idp.Document` -object vindt. (U kunt het PDF-resultaatelement gebruiken dat in het DDX-document is opgegeven.)
   * Roep de methode `copyToFile` van het `com.adobe.idp.Document` -object aan om het PDF-document te extraheren.

   >[!NOTE]
   >
   >Als `LOG_LEVEL` is ingesteld om een logboek te maken, kunt u het logboek extraheren met de methode `AssemblerResult` object `getJobLog` .

**zie ook**

[Snel starten (SOAP modus): een PDF-document samenstellen met de Java API](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-assembling-a-pdf-document-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## PDF-documenten samenstellen met de webservice-API {#assemble-pdf-documents-using-the-web-service-api}

U kunt PDF-documenten samenstellen met behulp van de API (webservice) voor vergaderingsservice:

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
   * Vul het object `BLOB` door de eigenschap `MTOM` ervan toe te wijzen met de inhoud van de bytearray.

1. Referentie-invoer PDF-documenten.

   * Maak voor elk invoerdocument een `BLOB` -object met behulp van de constructor. Het `BLOB` -object wordt gebruikt om het invoer-PDF-document op te slaan.
   * Maak een `System.IO.FileStream` -object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het PDF-invoerdocument en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van het object `System.IO.FileStream` wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de eigenschap `Length` van het object `System.IO.FileStream` op te halen.
   * Vul de bytearray met streamgegevens door de methode `Read` van het object `System.IO.FileStream` aan te roepen. Geef de bytearray, de startpositie en de streamlengte door om te lezen.
   * Vul het `BLOB` -object door het `MTOM` -veld ervan toe te wijzen met de inhoud van de bytearray.
   * Maak een `MyMapOf_xsd_string_To_xsd_anyType` -object. Dit verzamelingsobject wordt gebruikt om invoer-PDF-documenten op te slaan.
   * Maak voor elk invoerdocument een PDF-object `MyMapOf_xsd_string_To_xsd_anyType_Item` . Als bijvoorbeeld twee invoerdocumenten PDF worden gebruikt, maakt u twee `MyMapOf_xsd_string_To_xsd_anyType_Item` -objecten.
   * Wijs een tekenreekswaarde toe die de sleutelnaam vertegenwoordigt aan het veld `key` van het `MyMapOf_xsd_string_To_xsd_anyType_Item` -object. Deze waarde moet overeenkomen met de waarde van het PDF-bronelement dat is opgegeven in het DDX-document. (Voer deze taak uit voor elk invoerdocument van de PDF.)
   * Wijs het `BLOB` -object toe dat het PDF-document opslaat in het veld `MyMapOf_xsd_string_To_xsd_anyType_Item` object `value` . (Voer deze taak uit voor elk invoerdocument van de PDF.)
   * Voeg het object `MyMapOf_xsd_string_To_xsd_anyType_Item` toe aan het object `MyMapOf_xsd_string_To_xsd_anyType` . Roep de methode `Add` van het object `MyMapOf_xsd_string_To_xsd_anyType` aan en geef het object `MyMapOf_xsd_string_To_xsd_anyType` door. (Voer deze taak uit voor elk invoerdocument van de PDF.)

1. Stel runtime-opties in.

   * Maak een `AssemblerOptionSpec` -object dat uitvoeringsopties opslaat met behulp van de bijbehorende constructor.
   * Stel runtime-opties in om aan uw bedrijfsvereisten te voldoen door een waarde toe te wijzen aan een gegevenslid dat tot het `AssemblerOptionSpec` -object behoort. Als u bijvoorbeeld de Assembler-service wilt instrueren een taak te blijven verwerken wanneer een fout optreedt, wijst u `false` toe aan het gegevenslid van het `AssemblerOptionSpec` object `failOnError` .

1. Stel de invoerdocumenten PDF samen.

   Roep de methode `invoke` van het object `AssemblerServiceClient` aan en geef de volgende waarden door:

   * Een `BLOB` -object dat het DDX-document vertegenwoordigt.
   * De array `mapItem` die de invoerdocumenten PDF bevat. De sleutels moeten overeenkomen met de namen van de bronbestanden van de PDF en de waarden ervan moeten de `BLOB` -objecten zijn die overeenkomen met die bestanden.
   * Een `AssemblerOptionSpec` -object dat uitvoeringsopties opgeeft.

   De methode `invoke` retourneert een `AssemblerResult` -object dat de resultaten van de taak en eventuele uitzonderingen bevat die hebben plaatsgevonden.

1. Extraheer de resultaten.

   Voer de volgende handelingen uit om het nieuwe PDF-document te verkrijgen:

   * Open het veld `documents` van het `AssemblerResult` -object (een `Map` -object dat de documenten van result PDF bevat).
   * Doorloop het `Map` -object totdat u de sleutel vindt die overeenkomt met de naam van het resulterende document. Vervolgens cast u het element `value` van dat arraylid naar een `BLOB` .
   * Haal de binaire gegevens die het PDF-document vertegenwoordigen op door de eigenschap `MTOM` van het object `BLOB` te openen. Hiermee wordt een array met bytes geretourneerd die u naar een PDF-bestand kunt schrijven.

   >[!NOTE]
   >
   >Als `LOG_LEVEL` is ingesteld om een logbestand te maken, kunt u het logbestand extraheren door de waarde van het gegevenslid van het `AssemblerResult` object `jobLog` op te halen.

**zie ook**

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
