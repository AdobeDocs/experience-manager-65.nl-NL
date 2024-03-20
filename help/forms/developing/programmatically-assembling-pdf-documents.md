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
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '2105'
ht-degree: 0%

---

# PDF-documenten programmatisch samenstellen {#programmatically-assembling-pdf-documents}

**Voorbeelden en voorbeelden in dit document gelden alleen voor AEM Forms in JEE-omgeving.**

Met de API voor vergaderingsservice kunt u meerdere PDF-documenten samenvoegen tot één PDF-document. In de volgende afbeelding ziet u drie PDF-documenten die worden samengevoegd in één PDF-document.

![pa_pa_document_assembly](assets/pa_pa_document_assembly.png)

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

In dit DDX-document worden twee PDF-documenten samengevoegd met de naam *map.pdf* en *direction.pdf* in één PDF-document.

>[!NOTE]
>
>Als u een DDX-document wilt bekijken dat een PDF-document demonteert, raadpleegt u [PDF-documenten programmatisch demonteren](/help/forms/developing/programmatically-disassembling-pdf-documents.md#programmatically-disassembling-pdf-documents).

>[!NOTE]
>
>Voor meer informatie over de dienst van de Assembler, zie [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Voor meer informatie over een DDX-document raadpleegt u [De Verwijzing van de AssemblerDienst en DDX](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Overwegingen bij het aanroepen van de Assembler-service met behulp van webservices {#considerations-when-invoking-assembler-service-using-web-services}

Wanneer u kop- en voetteksten toevoegt tijdens het samenstellen van grote documenten, kan het zijn dat u een `OutOfMemory` fout en de bestanden worden niet samengesteld. Om de kans dat dit probleem zich voordoet te verkleinen, voegt u een `DDXProcessorSetting` element aan uw Dx- document, zoals aangetoond in het volgende voorbeeld.

`<DDXProcessorSetting name="checkpoint" value="2000" />`

U kunt dit element toevoegen als een onderliggend element van het dialoogvenster `DDX` element of als onderliggend element van een `PDF result` element. De standaardwaarde voor deze instelling is 0 (nul). Hiermee schakelt u het aanwijzen uit en de DDX gedraagt zich alsof de `DDXProcessorSetting` element is not present. Als u een `OutOfMemory` Als er een fout optreedt, moet u de waarde mogelijk instellen op een geheel getal, meestal tussen 500 en 5000. Een kleine controlepuntwaarde resulteert in frequentere controle die.

## Overzicht van de stappen {#summary-of-steps}

Als u één PDF-document wilt samenstellen op basis van meerdere PDF-documenten, voert u de volgende taken uit:

1. Inclusief projectbestanden.
1. Maak een PDF Assembler-client.
1. Verwijs naar een bestaand DDX-document.
1. Referentie-invoer PDF-documenten.
1. Stel runtime-opties in.
1. Stel de invoerdocumenten PDF samen.
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

Voordat u een Assembler-bewerking programmatisch kunt uitvoeren, moet u een Assembler-client maken.

**Verwijzen naar een bestaand DDX-document**

Er moet naar een DDX-document worden verwezen om een PDF-document samen te stellen. Neem bijvoorbeeld het DDX-document dat in deze sectie is geïntroduceerd. Dit DDX-document geeft de Assembler-service de opdracht om twee PDF-documenten samen te voegen tot één PDF-document.

**Referentie-invoer PDF-documenten**

Referentie-invoer PDF documenten die u aan de dienst van de Assembler wilt overgaan. Als u bijvoorbeeld twee invoerdocumenten met de naam Kaart en Richtingen wilt doorgeven, moet u de bijbehorende PDF-PDF-bestanden doorgeven.

Zowel het bestand map.pdf als het bestand direction.pdf moeten in een verzamelingsobject worden geplaatst. De naam van de sleutel moet de waarde van het PDF bronattribuut in het DX- document aanpassen. Het maakt niet uit wat de naam van het PDF-bestand is als de sleutel en het bronkenmerk in het DDX-document overeenkomen.

>[!NOTE]
>
>An `AssemblerResult` object, dat een verzamelingsobject bevat, wordt geretourneerd wanneer u het object activeert `invokeDDX` -bewerking. Deze bewerking wordt gebruikt wanneer u twee of meer invoerdocumenten van PDF doorgeeft aan de Assembler-service. Als u echter maar één invoerdocument doorgeeft aan de Assembler-service en slechts één retourdocument verwacht, roept u de instelling `invokeOneDocument` -bewerking. Bij het aanroepen van deze bewerking wordt één document geretourneerd. Zie voor informatie over het gebruik van deze bewerking [Gecodeerde PDF-documenten samenstellen](/help/forms/developing/assembling-encrypted-pdf-documents.md#assembling-encrypted-pdf-documents).

**Uitvoeringsopties instellen**

U kunt runtime opties plaatsen die het gedrag van de dienst van de Assembler controleren terwijl het een baan uitvoert. U kunt bijvoorbeeld een optie instellen die de Assembler-service de opdracht geeft door te gaan met het verwerken van een taak als er een fout optreedt. Voor informatie over de runtime opties die u kunt plaatsen, zie `AssemblerOptionSpec` klasseverwijzing in [AEM Forms API-naslag](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**De invoerdocumenten PDF samenstellen**

Nadat u de de dienstcliënt creeert, verwijs een DX- dossier, creeer een inzamelingsvoorwerp dat de documenten van de inputPDF opslaat, en vastgestelde runtime opties, kunt u de verrichting DDX aanhalen. Wanneer u het DDX-document gebruikt dat in deze sectie is opgegeven, worden de bestanden map.pdf en direction.pdf samengevoegd in één PDF-document.

**De resultaten extraheren**

De dienst van de Assembler keert a terug `java.util.Map` -object, dat kan worden verkregen uit het `AssemblerResult` en die bewerkingsresultaten bevatten. De geretourneerde `java.util.Map` bevat de resulterende documenten en eventuele uitzonderingen.

In de volgende tabel vindt u een overzicht van enkele sleutelwaarden en objecttypen die in het geretourneerde object kunnen worden gebruikt `java.util.Map` object.

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

U kunt een PDF-document samenstellen met behulp van de API (Java) voor vergaderingsservice:

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-assembler-client.jar, op in het klassenpad van uw Java-project.

1. Maak een PDF Assembler-client.

   * Een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Een `AssemblerServiceClient` object door de constructor ervan te gebruiken en de `ServiceClientFactory` object.

1. Verwijs naar een bestaand DDX-document.

   * Een `java.io.FileInputStream` een object dat het DDX-document vertegenwoordigt door de constructor ervan te gebruiken en een tekenreekswaarde door te geven die de locatie van het DDX-bestand aangeeft.
   * Een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en de `java.io.FileInputStream` object.

1. Referentie-invoer PDF-documenten.

   * Een `java.util.Map` object dat wordt gebruikt voor het opslaan van PDF-invoerdocumenten met behulp van een `HashMap` constructor.
   * Maak voor elk invoerdocument een PDF `java.io.FileInputStream` object door de constructor ervan te gebruiken en de locatie van het invoerdocument PDF door te geven.
   * Maak voor elk invoerdocument een PDF `com.adobe.idp.Document` en geeft het `java.io.FileInputStream` object dat het PDF-document bevat.
   * Voor elk invoerdocument voegt u een item toe aan de `java.util.Map` object aanroepen `put` en het doorgeven van de volgende argumenten:

      * Een tekenreekswaarde die de sleutelnaam vertegenwoordigt. Deze waarde moet overeenkomen met de waarde van het PDF-bronelement dat is opgegeven in het DDX-document.
      * A `com.adobe.idp.Document` object (of `java.util.List` -object dat meerdere documenten opgeeft) die het PDF-brondocument bevatten.

1. Stel runtime-opties in.

   * Een `AssemblerOptionSpec` object dat uitvoeringsopties opslaat met de constructor ervan.
   * Stel runtime-opties in om aan uw bedrijfsvereisten te voldoen door een methode aan te roepen die tot de `AssemblerOptionSpec` object. Bijvoorbeeld, om de dienst van de Assembler op te dragen om een baan te blijven verwerken wanneer een fout voorkomt, haalt het `AssemblerOptionSpec` object `setFailOnError` methode en doorgeven `false`.

1. Stel de invoerdocumenten PDF samen.

   De `AssemblerServiceClient` object `invokeDDX` en geeft de volgende vereiste waarden door:

   * A `com.adobe.idp.Document` object dat staat voor het te gebruiken DDX-document
   * A `java.util.Map` object dat de invoerbestanden bevat die moeten worden samengesteld PDF
   * A `com.adobe.livecycle.assembler.client.AssemblerOptionSpec` object dat de runtime-opties opgeeft, inclusief standaardfont- en taaklogniveau

   De `invokeDDX` methode retourneert een `com.adobe.livecycle.assembler.client.AssemblerResult` object dat de resultaten van de taak en eventuele uitzonderingen bevat die zijn opgetreden.

1. Extraheer de resultaten.

   Voer de volgende handelingen uit om het nieuwe PDF-document te verkrijgen:

   * De `AssemblerResult` object `getDocuments` methode. Dit retourneert een `java.util.Map` object.
   * Doorlopen `java.util.Map` object tot u het resultaat hebt gevonden `com.adobe.idp.Document` object. (U kunt het PDF-resultaatelement gebruiken dat in het DDX-document is opgegeven.)
   * De `com.adobe.idp.Document` object `copyToFile` methode om het PDF-document te extraheren.

   >[!NOTE]
   >
   >Indien `LOG_LEVEL` is ingesteld om een logboek te maken, kunt u het logboek extraheren met de optie `AssemblerResult` object `getJobLog` methode.

**Zie ook**

[Snel starten (SOAP-modus): een PDF-document samenstellen met de Java API](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-assembling-a-pdf-document-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## PDF-documenten samenstellen met de webservice-API {#assemble-pdf-documents-using-the-web-service-api}

U kunt PDF-documenten samenstellen met behulp van de API (webservice) voor vergaderingsservice:

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
   * Vul de `BLOB` object door het toe te wijzen `MTOM` eigenschap met de inhoud van de bytearray.

1. Referentie-invoer PDF-documenten.

   * Maak voor elk invoerdocument een PDF `BLOB` object met behulp van de constructor. De `BLOB` wordt gebruikt om het invoerdocument PDF op te slaan.
   * Een `System.IO.FileStream` door de constructor aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het invoerdocument PDF en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van de `System.IO.FileStream` object. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` object `Length` eigenschap.
   * De bytearray vullen met streamgegevens door de `System.IO.FileStream` object `Read` methode. Geef de bytearray, de startpositie en de streamlengte door om te lezen.
   * Vul de `BLOB` object door het toe te wijzen `MTOM` veld met de inhoud van de bytearray.
   * Een `MyMapOf_xsd_string_To_xsd_anyType` object. Dit verzamelingsobject wordt gebruikt om invoer-PDF-documenten op te slaan.
   * Maak voor elk invoerdocument een PDF `MyMapOf_xsd_string_To_xsd_anyType_Item` object. Als bijvoorbeeld twee invoerdocumenten PDF worden gebruikt, maakt u twee invoerdocumenten `MyMapOf_xsd_string_To_xsd_anyType_Item` objecten.
   * Wijs een tekenreekswaarde toe die de sleutelnaam vertegenwoordigt aan de `MyMapOf_xsd_string_To_xsd_anyType_Item` object `key` veld. Deze waarde moet overeenkomen met de waarde van het PDF-bronelement dat is opgegeven in het DDX-document. (Voer deze taak uit voor elk invoerdocument van de PDF.)
   * Wijs het `BLOB` object waarin het PDF-document is opgeslagen in het `MyMapOf_xsd_string_To_xsd_anyType_Item` object `value` veld. (Voer deze taak uit voor elk invoerdocument van de PDF.)
   * Voeg de `MyMapOf_xsd_string_To_xsd_anyType_Item` aan `MyMapOf_xsd_string_To_xsd_anyType` object. De `MyMapOf_xsd_string_To_xsd_anyType` object `Add` en geeft de `MyMapOf_xsd_string_To_xsd_anyType` object. (Voer deze taak uit voor elk invoerdocument van de PDF.)

1. Stel runtime-opties in.

   * Een `AssemblerOptionSpec` object dat uitvoeringsopties opslaat met de constructor ervan.
   * Stel runtime-opties in om aan uw bedrijfsvereisten te voldoen door een waarde toe te wijzen aan een gegevenslid dat tot de `AssemblerOptionSpec` object. Bijvoorbeeld, om de dienst van de Assembler op te dragen om een baan te blijven verwerken wanneer een fout voorkomt, wijs toe `false` aan de `AssemblerOptionSpec` object `failOnError` lid.

1. Stel de invoerdocumenten PDF samen.

   De `AssemblerServiceClient` object `invoke` en geeft de volgende waarden door:

   * A `BLOB` object dat het DDX-document vertegenwoordigt.
   * De `mapItem` -array die de invoerdocumenten PDF bevat. Zijn sleutels moeten de namen van de PDF brondossiers aanpassen, en zijn waarden moeten zijn `BLOB` objecten die overeenkomen met die bestanden.
   * An `AssemblerOptionSpec` -object dat uitvoeringsopties opgeeft.

   De `invoke` methode retourneert een `AssemblerResult` -object dat de resultaten van de taak en eventuele uitzonderingen bevat die zich hebben voorgedaan.

1. Extraheer de resultaten.

   Voer de volgende handelingen uit om het nieuwe PDF-document te verkrijgen:

   * Toegang krijgen tot de `AssemblerResult` object `documents` veld, dat een `Map` -object dat de PDF-documenten van het resultaat bevat.
   * Doorlopen `Map` -object totdat u de sleutel vindt die overeenkomt met de naam van het resulterende document. Dan giet dat serielid `value` een `BLOB`.
   * Extraheer de binaire gegevens die het document van de PDF door tot zijn toegang te hebben vertegenwoordigen `BLOB` object `MTOM` eigenschap. Hiermee wordt een array met bytes geretourneerd die u naar een PDF-bestand kunt schrijven.

   >[!NOTE]
   >
   >Indien `LOG_LEVEL` is ingesteld om een logboek te maken, kunt u het logboek extraheren door de waarde van het `AssemblerResult` object `jobLog` lid.

**Zie ook**

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
