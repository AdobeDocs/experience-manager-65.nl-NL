---
title: Documenten samenstellen met Bates-nummering
description: Gebruik Bates-nummering om PDF-documenten samen te stellen met de API voor Java en Web Service.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
exl-id: 2a4e21c4-f2f5-44cd-b8ed-7b572782a2f1
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Document Services
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '1910'
ht-degree: 0%

---

# Documenten samenstellen met Bates-nummering {#assembling-documents-using-bates-numbering}

**de Steekproeven en de voorbeelden in dit document zijn slechts voor AEM Forms op milieu JEE.**

Met Bates-nummering kunt u PDF-documenten samenstellen die unieke pagina-id&#39;s bevatten. *Bates nummering* is een methode om uniek toe te passen identificeert zich aan een partij van verwante documenten. Aan elke pagina in het document (of elke set documenten) wordt een Bates-nummer toegewezen dat de pagina uniek identificeert. Bijvoorbeeld, kunnen de productiedocumenten die rekening van materiaalinformatie bevatten en met de productie van een assemblage worden geassocieerd een herkenningsteken bevatten. Een Bates-nummer bevat een opeenvolgend verhoogde numerieke waarde en een optioneel voor- en achtervoegsel. Het prefix + numeriek + achtervoegsel wordt bedoeld als a *het patroon van Bates*.

In de volgende afbeelding ziet u een PDF-document dat een unieke id bevat in de koptekst van het document.

![&#x200B; au_au_batesnumber &#x200B;](assets/au_au_batesnumber.png)

In het kader van deze beschrijving wordt de unieke pagina-id in de koptekst van een document geplaatst. Stel dat het volgende DDX-document wordt gebruikt.

```xml
 <?xml version="1.0" encoding="UTF-8"?>
 <DDX xmlns="https://ns.adobe.com/DDX/1.0/">
        <PDF result="out.pdf">
        <Header>
         <Center>
             <StyledText>
                 <p font-size="20pt"><BatesNumber/></p>
             </StyledText>
         </Center>
     </Header>
           <PDF source="map.pdf" />
          <PDF source="directions.pdf" />
          </PDF>
 </DDX>
```

Dit DX- document voegt twee PDF documenten genoemd *map.pdf* en *richtingen.pdf* in één enkel document van PDF samen. Het resulterende PDF-document bevat een koptekst die bestaat uit een unieke pagina-id. Het document in de bovenstaande illustratie toont bijvoorbeeld 000016.

>[!NOTE]
>
>Alvorens deze sectie te lezen, adviseert men dat u vertrouwd bent met het assembleren van de documenten van PDF gebruikend de dienst van de Assembler. In deze sectie worden de concepten niet besproken, zoals het maken van een verzamelingsobject dat invoerdocumenten bevat of het extraheren van de resultaten van het geretourneerde verzamelingsobject. (Zie [&#x200B; Programmatiatically het assembleren van de Documenten van PDF &#x200B;](/help/forms/developing/programmatically-assembling-pdf-documents.md).)

>[!NOTE]
>
>Voor meer informatie over de dienst van de Assembler, zie [&#x200B; Verwijzing van de Diensten voor AEM Forms &#x200B;](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Voor meer informatie over een document DDX, zie [&#x200B; de Dienst van de Assembler en de Verwijzing DDX &#x200B;](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Overzicht van de stappen {#summary-of-steps}

U kunt als volgt een PDF-document samenstellen dat een unieke pagina-id (Bates-nummering) bevat:

1. Inclusief projectbestanden.
1. Maak een PDF Assembler-client.
1. Verwijs naar een bestaand DDX-document.
1. Referentie-invoer PDF-documenten.
1. Stel de oorspronkelijke waarde voor Bates-nummer in.
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

Als AEM Forms wordt geïmplementeerd op een andere ondersteunde J2EE-toepassingsserver dan JBoss, moet u de bestanden adobe-utilities.jar en jbossall-client.jar vervangen door JAR-bestanden die specifiek zijn voor de J2EE-toepassingsserver waarop AEM Forms wordt geïmplementeerd. Voor informatie over de plaats van alle dossiers van AEM Forms JAR, zie [&#x200B; Inclusief de bibliotheekdossiers van AEM Forms Java &#x200B;](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**creeer een cliënt van de Assembler van de PDF**

Alvorens u programmatically een verrichting van de Assembler kunt uitvoeren, moet u een de dienstcliënt van de Assembler tot stand brengen.

**Verwijzing een bestaand document DDX**

Er moet naar een DDX-document worden verwezen om een PDF-document samen te stellen. Neem bijvoorbeeld het DDX-document dat in deze sectie is geïntroduceerd. Als u een PDF-document wilt samenstellen dat unieke pagina-id&#39;s bevat, moet het DDX-document het `BatesNumber` -element bevatten.

**de documenten van de inputPDF van de Verwijzing**

Er moet worden verwezen naar invoerdocumenten voor PDF om een PDF-document samen te stellen. Er moet bijvoorbeeld naar de documenten map.pdf en direction.pdf worden verwezen om deze PDF-documenten samen te voegen tot één PDF-document.

**plaats de aanvankelijke waarde van het aantal Bates**

U kunt de aanvankelijke waarde van Bates aantal plaatsen om aan uw bedrijfsvereisten te voldoen. Stel bijvoorbeeld dat u de beginwaarde moet instellen op 000100. Als u de beginwaarde niet instelt, is de waarde van de eerste pagina 000000.

**assembleer de documenten van de inputPDF**

Nadat u de de dienstcliënt van de Assembler creeert, van verwijzingen het DX- document dat `BatesNumber` elementeninformatie bevat, van verwijzingen voorzien een document van de input, en runtime opties plaatsen, kunt u `invokeDDX` verrichting aanhalen die in de dienst van de Assembler resulteert die een document van de PDF samenvoegt dat unieke paginaadentifiers bevat.

**Extraheer de resultaten**

De dienst van de Assembler keert een inzamelingsvoorwerp terug dat de baanresultaten bevat. U kunt het resulterende PDF-document extraheren en eventuele uitzonderingen die worden gegenereerd. In dit geval bevindt een versleuteld PDF-document zich in het verzamelingsobject.

>[!NOTE]
>
>Een verzamelingsobject wordt geretourneerd wanneer u de bewerking `invokeDDX` aanroept. Deze bewerking wordt gebruikt wanneer u twee of meer invoerdocumenten van de PDF doorgeeft aan de Assembler-service. Als u echter slechts één invoerdocument van de PDF doorgeeft aan de service Assembler, moet u de bewerking `invokeOneDocument` aanroepen. Voor informatie over het gebruiken van deze verrichting, zie [&#x200B; Assemblbling de Documenten van de PDF &#x200B;](/help/forms/developing/assembling-encrypted-pdf-documents.md).

**zie ook**

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[PDF-documenten programmatisch samenstellen](/help/forms/developing/programmatically-assembling-pdf-documents.md)

## Documenten samenstellen met Bates-nummering met de Java API {#assemble-documents-with-bates-numbering-using-the-java-api}

U kunt een PDF-document samenstellen dat unieke pagina-id&#39;s (Bates-nummering) gebruikt met de API (Java) voor vergaderingsservice:

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
   * Maak voor elk invoerdocument een `java.io.FileInputStream` -object door de constructor ervan te gebruiken en de locatie van het invoerdocument door te geven. In dit geval geeft u de locatie van een onbeveiligd PDF-document door.
   * Maak voor elk invoerdocument een `com.adobe.idp.Document` -object en geef het `java.io.FileInputStream` -object door dat het PDF PDF-document bevat.
   * Voeg een item aan het object `java.util.Map` toe door de methode `put` ervan aan te roepen en de volgende argumenten door te geven:

      * Een tekenreekswaarde die de sleutelnaam vertegenwoordigt. Deze waarde moet overeenkomen met de waarde van het PDF-bronelement dat is opgegeven in het DDX-document. De naam van het PDF-bronbestand dat is opgegeven in het DDX-document dat in deze sectie wordt geïntroduceerd, is bijvoorbeeld Loan.pdf.
      * Een `com.adobe.idp.Document` -object dat het onbeveiligde PDF-document bevat.

1. Stel de oorspronkelijke waarde voor Bates-nummer in.

   * Maak een `AssemblerOptionSpec` -object dat uitvoeringsopties opslaat met behulp van de bijbehorende constructor.
   * Stel het eerste Bates-nummer in door het `AssemblerOptionSpec` -object `setFirstBatesNumber` aan te roepen en een numerieke waarde door te geven die de beginwaarde opgeeft.

1. Stel de invoerdocumenten PDF samen.

   Roep de methode `invokeDDX` van het object `AssemblerServiceClient` aan en geef de volgende vereiste waarden door:

   * Een `com.adobe.idp.Document` -object dat het DDX-document vertegenwoordigt.
   * Een `java.util.Map` -object dat het onbeveiligde invoerbestand PDF bevat.
   * Een `com.adobe.livecycle.assembler.client.AssemblerOptionSpec` -object dat de runtime-opties opgeeft, inclusief het standaardniveau voor lettertypen en taaklogbestanden.

   De methode `invokeDDX` retourneert een `com.adobe.livecycle.assembler.client.AssemblerResult` -object dat een met een wachtwoord gecodeerd PDF-document bevat.

1. Extraheer de resultaten.

   Voer de volgende handelingen uit om het nieuwe PDF-document te verkrijgen:

   * Roep de methode `getDocuments` van het object `AssemblerResult` aan. Deze handeling retourneert een `java.util.Map` -object.
   * Doorloop het object `java.util.Map` totdat u het object `com.adobe.idp.Document` vindt.
   * Roep de methode `copyToFile` van het `com.adobe.idp.Document` -object aan om het PDF-document te extraheren.

**zie ook**

[Snel starten (SOAP modus): een PDF-document samenstellen met een Bates-nummering met de Java API](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-assembling-a-pdf-document-with-bates-numbering-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Documenten samenstellen met Bates-nummering met de webservice-API {#assemble-documents-with-bates-numbering-using-the-web-service-api}

U kunt een PDF-document samenstellen dat gebruikmaakt van unieke pagina-id&#39;s (Bates-nummering) met behulp van de API (webservice) van de Assembler-service:

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
   * Vul de bytearray met streamgegevens door de methode `Read` van het object `System.IO.FileStream` aan te roepen. Geef de bytearray, de startpositie en de streamlengte door om te lezen.
   * Vul het `BLOB` -object door het `MTOM` -veld ervan toe te wijzen met de inhoud van de bytearray.

1. Referentie-invoer PDF-documenten.

   * Maak voor elk invoerdocument een `BLOB` -object met behulp van de constructor. Het `BLOB` -object wordt gebruikt om het invoer-PDF-document op te slaan.
   * Maak een `System.IO.FileStream` -object door de constructor ervan aan te roepen. Geef een tekenreekswaarde door die staat voor de bestandslocatie van het invoerdocument en de modus waarin het PDF-bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van het object `System.IO.FileStream` wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de eigenschap `Length` van het object `System.IO.FileStream` op te halen.
   * Vul de bytearray met streamgegevens door de methode `Read` van het object `System.IO.FileStream` aan te roepen. Geef de bytearray, de startpositie en de streamlengte door om te lezen.
   * Vul het object `BLOB` door de eigenschap `MTOM` ervan toe te wijzen met de inhoud van de bytearray.
   * Maak een `MyMapOf_xsd_string_To_xsd_anyType` -object. Dit verzamelingsobject wordt gebruikt om de invoerdocumenten PDF op te slaan.
   * Maak voor elk invoerdocument een PDF-object `MyMapOf_xsd_string_To_xsd_anyType_Item` . Als bijvoorbeeld twee invoerdocumenten PDF worden gebruikt, maakt u twee `MyMapOf_xsd_string_To_xsd_anyType_Item` -objecten.
   * Wijs een tekenreekswaarde toe die de sleutelnaam vertegenwoordigt aan het veld `key` van het `MyMapOf_xsd_string_To_xsd_anyType_Item` -object. Deze waarde moet overeenkomen met de waarde van het PDF-bronelement dat is opgegeven in het DDX-document. (Voer deze taak uit voor elk invoerdocument van de PDF.)
   * Wijs het `BLOB` -object toe dat het PDF-document opslaat in het veld `MyMapOf_xsd_string_To_xsd_anyType_Item` object `value` . (Voer deze taak uit voor elk invoerdocument van de PDF.)
   * Voeg het object `MyMapOf_xsd_string_To_xsd_anyType_Item` toe aan het object `MyMapOf_xsd_string_To_xsd_anyType` . Roep de methode `Add` van het object `MyMapOf_xsd_string_To_xsd_anyType` aan en geef het object `MyMapOf_xsd_string_To_xsd_anyType` door. (Voer deze taak uit voor elk invoerdocument van de PDF.)

1. Stel de oorspronkelijke waarde voor Bates-nummer in.

   * Maak een `AssemblerOptionSpec` -object dat uitvoeringsopties opslaat met behulp van de bijbehorende constructor.
   * Stel het eerste Bates-nummer in door een numerieke waarde toe te wijzen aan het `firstBatesNumber` -gegevenslid dat tot het `AssemblerOptionSpec` -object behoort.

1. Stel de invoerdocumenten PDF samen.

   Roep de methode `invoke` van het object `AssemblerServiceClient` aan en geef de volgende waarden door:

   * Een `BLOB` -object dat het DDX-document vertegenwoordigt.
   * Het `MyMapOf_xsd_string_To_xsd_anyType` -object dat de invoerdocumenten PDF bevat. De sleutels moeten overeenkomen met de namen van de bronbestanden van de PDF en de waarden ervan moeten de `BLOB` -objecten zijn die overeenkomen met die bestanden.
   * Een `AssemblerOptionSpec` -object dat uitvoeringsopties opgeeft.

   De methode `invoke` retourneert een `AssemblerResult` -object dat de resultaten van de taak en eventuele uitzonderingen bevat.

1. Extraheer de resultaten.

   Voer de volgende handelingen uit om het nieuwe PDF-document te verkrijgen:

   * Open het veld `documents` van het `AssemblerResult` -object (een `Map` -object dat de PDF-documenten van het resultaat bevat).
   * Doorloop het `Map` -object totdat u de sleutel vindt die overeenkomt met de naam van het resulterende document. Vervolgens cast u het element `value` van dat arraylid naar een `BLOB` .
   * Extraheer de binaire gegevens die het PDF-document vertegenwoordigen door de eigenschap `MTOM` van het object `BLOB` te openen. Hiermee wordt een array met bytes geretourneerd die u naar een PDF-bestand kunt schrijven.

**zie ook**

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
