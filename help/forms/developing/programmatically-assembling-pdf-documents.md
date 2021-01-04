---
title: PDF-documenten programmatisch samenstellen
seo-title: PDF-documenten programmatisch samenstellen
description: Gebruik de API voor de vergaderingsservice om meerdere PDF-documenten samen te stellen tot één PDF-document met de Java API en de webservice-API.
seo-description: Gebruik de API voor de vergaderingsservice om meerdere PDF-documenten samen te stellen tot één PDF-document met de Java API en de webservice-API.
uuid: aa3f8f39-1fbc-48d0-82ff-6caaadf125fc
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: ebe8136b-2a79-4035-b9d5-aa70a5bbd4af
translation-type: tm+mt
source-git-commit: 07889ead2ae402b5fb738ca08c7efe076ef33e44
workflow-type: tm+mt
source-wordcount: '2138'
ht-degree: 0%

---


# PDF-documenten programmatisch samenstellen {#programmatically-assembling-pdf-documents}

U kunt de API van de Dienst van de Assembler gebruiken om veelvoudige PDF documenten in één enkel Pdf- document samen te stellen. In de volgende afbeelding ziet u drie PDF-documenten die in één PDF-document worden samengevoegd.

![pa_pa_document_assembly](assets/pa_pa_document_assembly.png)

Als u twee of meer PDF-documenten in één PDF-document wilt samenvoegen, hebt u een DDX-document nodig. In een DDX-document wordt het PDF-document beschreven dat de Assembler-service produceert. Namelijk draagt het DDX- document de dienst van de Assembler op welke acties om uit te voeren.

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

Dit DDX-document voegt twee PDF-documenten met de naam *map.pdf* en *direction.pdf* samen tot één PDF-document.

>[!NOTE]
>
>Zie [PDF-documenten decompileren](/help/forms/developing/programmatically-disassembling-pdf-documents.md#programmatically-disassembling-pdf-documents) voor een DDX-document dat een PDF-document demonteert.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Assembler, zie [de Verwijzing van de Diensten voor AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Voor meer informatie over een DX- document, zie [de Dienst van de Assembler en DX Verwijzing](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Overwegingen bij het aanroepen van de Assembler-service met behulp van webservices {#considerations-when-invoking-assembler-service-using-web-services}

Wanneer u kop- en voetteksten toevoegt tijdens het samenstellen van grote documenten, kan een fout `OutOfMemory` optreden en worden de bestanden niet samengesteld. Om de kans te verminderen dat dit probleem voorkomt, voeg een `DDXProcessorSetting` element aan uw Dx- document toe, zoals aangetoond in het volgende voorbeeld.

`<DDXProcessorSetting name="checkpoint" value="2000" />`

U kunt dit element toevoegen als een onderliggend element van het element `DDX` of als een onderliggend element van een element `PDF result`. De standaardwaarde voor deze instelling is 0 (nul), waardoor het aanwijzen wordt uitgeschakeld en de DDX zich gedraagt alsof het element `DDXProcessorSetting` niet aanwezig is. Als u een fout `OutOfMemory` hebt ontmoet, kunt u de waarde aan een geheel, typisch tussen 500 en 5000 moeten plaatsen. Een kleine controlepuntwaarde resulteert in frequentere controle die.

## Overzicht van stappen {#summary-of-steps}

Als u één PDF-document wilt samenstellen op basis van meerdere PDF-documenten, voert u de volgende taken uit:

1. Inclusief projectbestanden.
1. Maak een PDF Assembler-client.
1. Verwijs naar een bestaand DDX-document.
1. Referentie-invoer-PDF-documenten.
1. Stel runtime-opties in.
1. Stel de invoer-PDF-documenten samen.
1. Extraheer de resultaten.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-assembler-client.jar
* adobe-utilities.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)

als AEM Forms wordt geïmplementeerd op een andere ondersteunde J2EE-toepassingsserver dan JBoss, moet u de bestanden adobe-utilities.jar en jbossall-client.jar vervangen door JAR-bestanden die specifiek zijn voor de J2EE-toepassingsserver waarop AEM Forms wordt geïmplementeerd.

**Een PDF Assembler-client maken**

Voordat u programmatically een verrichting van de Assembler kunt uitvoeren, moet u een cliënt van de Assembler tot stand brengen.

**Verwijzen naar een bestaand DDX-document**

Er moet naar een DDX-document worden verwezen om een PDF-document samen te stellen. Neem bijvoorbeeld het DDX-document dat in deze sectie is geïntroduceerd. Dit DDX-document geeft de Assembler-service de opdracht om twee PDF-documenten samen te voegen tot één PDF-document.

**Referentie-invoer-PDF-documenten**

Referentie-invoer-PDF-documenten die u wilt doorgeven aan de Assembler-service. Als u bijvoorbeeld twee invoer-PDF-documenten met de naam Kaart en Richtingen wilt doorgeven, moet u de bijbehorende PDF-bestanden doorgeven.

Zowel het bestand map.pdf als het bestand direction.pdf moeten in een verzamelingsobject worden geplaatst. De naam van de sleutel moet overeenkomen met de waarde van het PDF-bronkenmerk in het DDX-document. Het maakt niet uit wat de naam van het PDF-bestand is als de sleutel en het bronkenmerk in het DDX-document overeenkomen.

>[!NOTE]
>
>Een `AssemblerResult` voorwerp, dat een inzamelingsvoorwerp bevat, is teruggekeerd als u `invokeDDX` verrichting aanhaalt. Deze bewerking wordt gebruikt wanneer u twee of meer invoer-PDF-documenten doorgeeft aan de Assembler-service. Als u echter slechts één invoer-PDF doorgeeft aan de Assembler-service en slechts één retourdocument verwacht, roept u de bewerking `invokeOneDocument` aan. Bij het aanroepen van deze bewerking wordt één document geretourneerd. Zie [Gecodeerde PDF-documenten samenstellen](/help/forms/developing/assembling-encrypted-pdf-documents.md#assembling-encrypted-pdf-documents) voor informatie over het gebruik van deze bewerking.

**Uitvoeringsopties instellen**

U kunt runtime opties plaatsen die het gedrag van de dienst van de Assembler controleren terwijl het een baan uitvoert. U kunt bijvoorbeeld een optie instellen die de Assembler-service de opdracht geeft door te gaan met het verwerken van een taak als er een fout optreedt. Zie de `AssemblerOptionSpec`-klasseverwijzing in [AEM Forms API Reference](https://www.adobe.com/go/learn_aemforms_javadocs_63_en) voor informatie over de runtime-opties die u kunt instellen.

**PDF-invoerdocumenten samenstellen**

Nadat u de serviceclient hebt gemaakt, naar een DDX-bestand hebt verwezen, een verzamelingsobject hebt gemaakt waarin de invoer-PDF-documenten zijn opgeslagen en uitvoeropties hebt ingesteld, kunt u de DDX-bewerking activeren. Wanneer u het in deze sectie opgegeven DDX-document gebruikt, worden de bestanden map.pdf en direction.pdf samengevoegd in één PDF-document.

**De resultaten extraheren**

De service Assembler retourneert een `java.util.Map`-object dat kan worden verkregen van het `AssemblerResult`-object en dat de bewerkingsresultaten bevat. Het geretourneerde `java.util.Map`-object bevat de resulterende documenten en eventuele uitzonderingen.

De volgende tabel bevat een overzicht van enkele sleutelwaarden en objecttypen die in het geretourneerde `java.util.Map`-object kunnen worden gevonden.

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

**Zie ook**

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[PDF-documenten programmatisch demonteren](/help/forms/developing/programmatically-disassembling-pdf-documents.md#programmatically-disassembling-pdf-documents)

## PDF-documenten samenstellen met de Java API {#assemble-pdf-documents-using-the-java-api}

U kunt een PDF-document samenstellen met de API (Java) voor vergaderingsservice:

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-assembler-client.jar, op in het klassenpad van uw Java-project.

1. Maak een PDF Assembler-client.

   * Maak een `ServiceClientFactory`-object dat verbindingseigenschappen bevat.
   * Maak een `AssemblerServiceClient`-object door de constructor ervan te gebruiken en het object `ServiceClientFactory` door te geven.

1. Verwijs naar een bestaand DDX-document.

   * Maak een `java.io.FileInputStream`-object dat het DDX-document vertegenwoordigt door de constructor ervan te gebruiken en een tekenreekswaarde door te geven die de locatie van het DDX-bestand aangeeft.
   * Maak een `com.adobe.idp.Document`-object door de constructor ervan te gebruiken en het object `java.io.FileInputStream` door te geven.

1. Referentie-invoer-PDF-documenten.

   * Maak een `java.util.Map`-object dat wordt gebruikt om invoer-PDF-documenten op te slaan met behulp van een `HashMap`-constructor.
   * Maak voor elk invoer-PDF-document een `java.io.FileInputStream`-object door de constructor ervan te gebruiken en de locatie van het invoer-PDF-document door te geven.
   * Maak voor elk invoer-PDF-document een `com.adobe.idp.Document`-object en geef het `java.io.FileInputStream`-object door dat het PDF-document bevat.
   * Voeg voor elk invoerdocument een item toe aan het `java.util.Map`-object door de methode `put` ervan aan te roepen en de volgende argumenten door te geven:

      * Een tekenreekswaarde die de sleutelnaam vertegenwoordigt. Deze waarde moet overeenkomen met de waarde van het PDF-bronelement dat is opgegeven in het DDX-document.
      * Een `com.adobe.idp.Document`-object (of `java.util.List`-object dat meerdere documenten opgeeft) dat het bron-PDF-document bevat.

1. Stel runtime-opties in.

   * Maak een `AssemblerOptionSpec`-object dat uitvoeringsopties opslaat met de constructor ervan.
   * Stel runtime-opties in om aan uw bedrijfsvereisten te voldoen door een methode aan te roepen die tot het object `AssemblerOptionSpec` behoort. Bijvoorbeeld, om de dienst van de Assembler op te dragen om een baan te blijven verwerken wanneer een fout voorkomt, haalt de `AssemblerOptionSpec` methode `setFailOnError` van objecten aan en gaat `false` over.

1. Stel de invoer-PDF-documenten samen.

   Roep de methode `invokeDDX` van het object `AssemblerServiceClient` aan en geef de volgende vereiste waarden door:

   * Een `com.adobe.idp.Document`-object dat het te gebruiken DDX-document vertegenwoordigt
   * Een `java.util.Map`-object dat de invoer-PDF-bestanden bevat die moeten worden samengevoegd
   * Een `com.adobe.livecycle.assembler.client.AssemblerOptionSpec`-object dat de runtime-opties opgeeft, inclusief het standaardniveau voor lettertypen en taaklogbestanden

   De methode `invokeDDX` retourneert een `com.adobe.livecycle.assembler.client.AssemblerResult`-object dat de resultaten van de taak en eventuele uitzonderingen bevat die zich hebben voorgedaan.

1. Extraheer de resultaten.

   Voer de volgende handelingen uit om het nieuwe PDF-document te verkrijgen:

   * Roep de methode `AssemblerResult` van het object `getDocuments` aan. Dit retourneert een `java.util.Map`-object.
   * Doorloop het object `java.util.Map` totdat u het resulterende object `com.adobe.idp.Document` hebt gevonden. (U kunt het PDF-resultaatelement dat in het DDX-document is opgegeven, gebruiken om het document op te halen.)
   * Roep de methode `com.adobe.idp.Document` van het object `copyToFile` aan om het PDF-document uit te pakken.

   >[!NOTE]
   >
   >Als `LOG_LEVEL` is ingesteld om een logbestand te maken, kunt u het logbestand extraheren met de methode `AssemblerResult` van het object `getJobLog`.

**Zie ook**

[Snel starten (SOAP-modus): Een PDF-document samenstellen met de Java API](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-assembling-a-pdf-document-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## PDF-documenten samenstellen met de webservice-API {#assemble-pdf-documents-using-the-web-service-api}

U kunt PDF-documenten samenstellen met de API (webservice) van de Assembler Service:

1. Inclusief projectbestanden.

   Creeer een project van Microsoft .NET dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervang `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een PDF Assembler-client.

   * Maak een `AssemblerServiceClient`-object met de standaardconstructor.
   * Maak een `AssemblerServiceClient.Endpoint.Address`-object met de constructor `System.ServiceModel.EndpointAddress`. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/AssemblerService?blob=mtom`). U hoeft het `lc_version`-kenmerk niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.
   * Maak een `System.ServiceModel.BasicHttpBinding`-object door de waarde van het veld `AssemblerServiceClient.Endpoint.Binding` op te halen. Cast de terugkeerwaarde aan `BasicHttpBinding`.
   * Stel het veld `System.ServiceModel.BasicHttpBinding` van het object `MessageEncoding` in op `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam voor het AEM aan het veld `AssemblerServiceClient.ClientCredentials.UserName.UserName` toe.
      * Wijs de overeenkomstige wachtwoordwaarde aan het gebied `AssemblerServiceClient.ClientCredentials.UserName.Password` toe.
      * Wijs de constante waarde `HttpClientCredentialType.Basic` aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType` toe.
      * Wijs de constante waarde `BasicHttpSecurityMode.TransportCredentialOnly` aan het veld `BasicHttpBindingSecurity.Security.Mode` toe.

1. Verwijs naar een bestaand DDX-document.

   * Maak een `BLOB`-object met de constructor ervan. Het object `BLOB` wordt gebruikt om het DDX-document op te slaan.
   * Maak een `System.IO.FileStream`-object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het DDX-document en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van het object `System.IO.FileStream` wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de eigenschap `System.IO.FileStream` van het object `Length` op te halen.
   * Vul de bytearray met streamgegevens door de methode `Read` van het object `System.IO.FileStream` aan te roepen en de bytearray, de startpositie en de lengte van de stream door te geven om te lezen.
   * Vul het object `BLOB` door de eigenschap `MTOM` ervan toe te wijzen met de inhoud van de bytearray.

1. Referentie-invoer-PDF-documenten.

   * Maak voor elk invoer-PDF-document een `BLOB`-object met behulp van de constructor. Met het object `BLOB` wordt het invoer-PDF-document opgeslagen.
   * Maak een `System.IO.FileStream`-object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het invoer-PDF-document en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van het object `System.IO.FileStream` wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de eigenschap `System.IO.FileStream` van het object `Length` op te halen.
   * Vul de bytearray met streamgegevens door de methode `Read` van het object `System.IO.FileStream` aan te roepen. Geef de bytearray, de startpositie en de streamlengte door om te lezen.
   * Vul het `BLOB`-object door het `MTOM`-veld toe te wijzen met de inhoud van de bytearray.
   * Maak een `MyMapOf_xsd_string_To_xsd_anyType`-object. Dit verzamelobject wordt gebruikt om invoer-PDF-documenten op te slaan.
   * Maak voor elk invoer-PDF-document een `MyMapOf_xsd_string_To_xsd_anyType_Item`-object. Als bijvoorbeeld twee invoer-PDF-documenten worden gebruikt, maakt u twee `MyMapOf_xsd_string_To_xsd_anyType_Item`-objecten.
   * Wijs een tekenreekswaarde toe die de toetsnaam vertegenwoordigt aan het veld `key` van het `MyMapOf_xsd_string_To_xsd_anyType_Item`-object. Deze waarde moet overeenkomen met de waarde van het PDF-bronelement dat is opgegeven in het DDX-document. (Voer deze taak uit voor elk invoer-PDF-document.)
   * Wijs het `BLOB`-object toe dat het PDF-document opslaat in het veld `MyMapOf_xsd_string_To_xsd_anyType_Item` van het `value`-object. (Voer deze taak uit voor elk invoer-PDF-document.)
   * Voeg het object `MyMapOf_xsd_string_To_xsd_anyType_Item` toe aan het object `MyMapOf_xsd_string_To_xsd_anyType`. Roep de methode `MyMapOf_xsd_string_To_xsd_anyType` van het object `Add` aan en geef het object `MyMapOf_xsd_string_To_xsd_anyType` door. (Voer deze taak uit voor elk invoer-PDF-document.)

1. Stel runtime-opties in.

   * Maak een `AssemblerOptionSpec`-object dat uitvoeringsopties opslaat met de constructor ervan.
   * Stel runtime-opties in om aan uw bedrijfsvereisten te voldoen door een waarde toe te wijzen aan een gegevenslid dat tot het object `AssemblerOptionSpec` behoort. Bijvoorbeeld, om de dienst van de Assembler op te dragen om een baan te blijven verwerken wanneer een fout voorkomt, wijs `false` aan `AssemblerOptionSpec` het gegevenslid van `failOnError` van het voorwerp toe.

1. Stel de invoer-PDF-documenten samen.

   Roep de methode `invoke` van het object `AssemblerServiceClient` aan en geef de volgende waarden door:

   * Een `BLOB`-object dat het DDX-document vertegenwoordigt.
   * De array `mapItem` die de invoer-PDF-documenten bevat. De sleutels moeten overeenkomen met de namen van de PDF-bronbestanden en de waarden ervan moeten de `BLOB`-objecten zijn die overeenkomen met die bestanden.
   * Een `AssemblerOptionSpec`-object dat uitvoeringsopties opgeeft.

   De methode `invoke` retourneert een `AssemblerResult`-object dat de resultaten van de taak en eventuele uitzonderingen bevat die zich hebben voorgedaan.

1. Extraheer de resultaten.

   Voer de volgende handelingen uit om het nieuwe PDF-document te verkrijgen:

   * Open het veld `AssemblerResult` van het object `documents`. Dit is een `Map`-object dat de PDF-documenten van het resultaat bevat.
   * Doorloop het object `Map` totdat u de sleutel vindt die overeenkomt met de naam van het resulterende document. Dan giet `value` van dat serielid aan `BLOB`.
   * Pak de binaire gegevens die het PDF-document vertegenwoordigen uit door de eigenschap `MTOM` van het object `BLOB` te openen. Hiermee wordt een array met bytes geretourneerd die u naar een PDF-bestand kunt schrijven.

   >[!NOTE]
   >
   >Als `LOG_LEVEL` is ingesteld om een logbestand te maken, kunt u het logbestand extraheren door de waarde van het `AssemblerResult`-gegevenslid van het object `jobLog` op te halen.

**Zie ook**

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
