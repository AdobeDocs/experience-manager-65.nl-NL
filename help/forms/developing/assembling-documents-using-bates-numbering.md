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

**Voorbeelden en voorbeelden in dit document gelden alleen voor AEM Forms in JEE-omgeving.**

Met Bates-nummering kunt u PDF-documenten samenstellen die unieke pagina-id&#39;s bevatten. *Bates-nummering* is een methode om unieke identificaties toe te passen op een batch gerelateerde documenten. Aan elke pagina in het document (of elke set documenten) wordt een Bates-nummer toegewezen dat de pagina uniek identificeert. Bijvoorbeeld, kunnen de productiedocumenten die rekening van materiaalinformatie bevatten en met de productie van een assemblage worden geassocieerd een herkenningsteken bevatten. Een Bates-nummer bevat een opeenvolgend verhoogde numerieke waarde en een optioneel voor- en achtervoegsel. Het voorvoegsel + het numerieke + achtervoegsel wordt een *bates-patroon*.

In de volgende afbeelding ziet u een PDF-document dat een unieke id bevat in de koptekst van het document.

![au_au_batesnumber](assets/au_au_batesnumber.png)

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

In dit DDX-document worden twee PDF-documenten samengevoegd met de naam *map.pdf* en *direction.pdf* in één PDF-document. Het resulterende PDF-document bevat een koptekst die bestaat uit een unieke pagina-id. Het document in de bovenstaande illustratie toont bijvoorbeeld 000016.

>[!NOTE]
>
>Alvorens deze sectie te lezen, adviseert men dat u vertrouwd bent met het assembleren van de documenten van PDF gebruikend de dienst van de Assembler. In deze sectie worden de concepten niet besproken, zoals het maken van een verzamelingsobject dat invoerdocumenten bevat of het extraheren van de resultaten van het geretourneerde verzamelingsobject. (Zie [PDF-documenten programmatisch samenstellen](/help/forms/developing/programmatically-assembling-pdf-documents.md).)

>[!NOTE]
>
>Voor meer informatie over de dienst van de Assembler, zie [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Voor meer informatie over een DDX-document raadpleegt u [De Verwijzing van de AssemblerDienst en DDX](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Overzicht van de stappen {#summary-of-steps}

U kunt als volgt een PDF-document samenstellen dat een unieke pagina-id (Bates-nummering) bevat:

1. Inclusief projectbestanden.
1. Maak een PDF Assembler-client.
1. Verwijs naar een bestaand DDX-document.
1. Referentie-invoer PDF-documenten.
1. Stel de oorspronkelijke waarde voor Bates-nummer in.
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

Als AEM Forms wordt geïmplementeerd op een andere ondersteunde J2EE-toepassingsserver dan JBoss, moet u de bestanden adobe-utilities.jar en jbossall-client.jar vervangen door JAR-bestanden die specifiek zijn voor de J2EE-toepassingsserver waarop AEM Forms wordt geïmplementeerd. Voor informatie over de locatie van alle AEM Forms JAR-bestanden raadpleegt u [Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Een PDF Assembler-client maken**

Alvorens u programmatically een verrichting van de Assembler kunt uitvoeren, moet u een de dienstcliënt van de Assembler tot stand brengen.

**Verwijzen naar een bestaand DDX-document**

Er moet naar een DDX-document worden verwezen om een PDF-document samen te stellen. Neem bijvoorbeeld het DDX-document dat in deze sectie is geïntroduceerd. Als u een PDF-document wilt samenstellen dat unieke pagina-id&#39;s bevat, moet het DDX-document het `BatesNumber` element.

**Referentie-invoer PDF-documenten**

Er moet worden verwezen naar invoerdocumenten voor PDF om een PDF-document samen te stellen. Er moet bijvoorbeeld naar de documenten map.pdf en direction.pdf worden verwezen om deze PDF-documenten samen te voegen tot één PDF-document.

**Stel de oorspronkelijke waarde voor het Bates-nummer in**

U kunt de aanvankelijke waarde van Bates aantal plaatsen om aan uw bedrijfsvereisten te voldoen. Stel bijvoorbeeld dat u de beginwaarde moet instellen op 000100. Als u de beginwaarde niet instelt, is de waarde van de eerste pagina 000000.

**De invoerdocumenten PDF samenstellen**

Nadat u de de dienstcliënt van de Assembler creeert, verwijs het DX- document dat bevat `BatesNumber` elementgegevens, verwijzingen naar een invoerdocument en PDF-uitvoeringsopties instellen, kunt u de `invokeDDX` bewerking die resulteert in het samenstellen van een PDF-document dat unieke pagina-id&#39;s bevat door de Assembler-service.

**De resultaten extraheren**

De dienst van de Assembler keert een inzamelingsvoorwerp terug dat de baanresultaten bevat. U kunt het resulterende PDF-document extraheren en eventuele uitzonderingen die worden gegenereerd. In dit geval bevindt een versleuteld PDF-document zich in het verzamelingsobject.

>[!NOTE]
>
>Er wordt een verzamelingsobject geretourneerd als u het dialoogvenster `invokeDDX` -bewerking. Deze bewerking wordt gebruikt wanneer u twee of meer invoerdocumenten van de PDF doorgeeft aan de Assembler-service. Als u echter slechts één invoerdocument van de PDF doorgeeft aan de Assembler-service, moet u de instelling `invokeOneDocument` -bewerking. Zie voor informatie over het gebruik van deze bewerking [Gecodeerde PDF-documenten samenstellen](/help/forms/developing/assembling-encrypted-pdf-documents.md).

**Zie ook**

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[PDF-documenten programmatisch samenstellen](/help/forms/developing/programmatically-assembling-pdf-documents.md)

## Documenten samenstellen met Bates-nummering met de Java API {#assemble-documents-with-bates-numbering-using-the-java-api}

U kunt een PDF-document samenstellen dat unieke pagina-id&#39;s (Bates-nummering) gebruikt met de API (Java) voor vergaderingsservice:

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-assembler-client.jar, op in het klassenpad van uw Java-project.

1. Maak een PDF Assembler-client.

   * Een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Een `AssemblerServiceClient` object door de constructor ervan te gebruiken en de `ServiceClientFactory` object.

1. Verwijs naar een bestaand DDX-document.

   * Een `java.io.FileInputStream` een object dat het DDX-document vertegenwoordigt door de constructor ervan te gebruiken en een tekenreekswaarde door te geven die de locatie van het DDX-bestand aangeeft.
   * Een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en de `java.io.FileInputStream` object.

1. Referentie-invoer PDF-documenten.

   * Een `java.util.Map` object dat wordt gebruikt voor het opslaan van PDF-invoerdocumenten met een `HashMap` constructor.
   * Maak voor elk invoerdocument een PDF `java.io.FileInputStream` object door de constructor ervan te gebruiken en de locatie van het invoerdocument PDF door te geven. In dit geval geeft u de locatie van een onbeveiligd PDF-document door.
   * Maak voor elk invoerdocument een PDF `com.adobe.idp.Document` en geeft het `java.io.FileInputStream` object dat het PDF-document bevat.
   * Een item toevoegen aan de `java.util.Map` object aanroepen `put` en het doorgeven van de volgende argumenten:

      * Een tekenreekswaarde die de sleutelnaam vertegenwoordigt. Deze waarde moet overeenkomen met de waarde van het PDF-bronelement dat is opgegeven in het DDX-document. De naam van het PDF-bronbestand dat is opgegeven in het DDX-document dat in deze sectie wordt geïntroduceerd, is bijvoorbeeld Loan.pdf.
      * A `com.adobe.idp.Document` object dat het onbeveiligde PDF-document bevat.

1. Stel de oorspronkelijke waarde voor Bates-nummer in.

   * Een `AssemblerOptionSpec` object dat uitvoeringsopties opslaat met de constructor ervan.
   * Stel het aanvankelijke Bates-nummer in door het `AssemblerOptionSpec` object `setFirstBatesNumber` en door een numerieke waarde te geven die de beginwaarde opgeeft.

1. Stel de invoerdocumenten PDF samen.

   De `AssemblerServiceClient` object `invokeDDX` en geeft de volgende vereiste waarden door:

   * A `com.adobe.idp.Document` object dat het DDX-document vertegenwoordigt.
   * A `java.util.Map` -object dat het niet-beveiligde invoerbestand PDF bevat.
   * A `com.adobe.livecycle.assembler.client.AssemblerOptionSpec` -object dat de runtime-opties opgeeft, inclusief het standaardniveau voor fonts en taaklogbestanden.

   De `invokeDDX` methode retourneert een `com.adobe.livecycle.assembler.client.AssemblerResult` object dat een met wachtwoord gecodeerd PDF-document bevat.

1. Extraheer de resultaten.

   Voer de volgende handelingen uit om het nieuwe PDF-document te verkrijgen:

   * De `AssemblerResult` object `getDocuments` methode. Deze handeling retourneert een `java.util.Map` object.
   * Doorlopen `java.util.Map` object tot u het object hebt gevonden `com.adobe.idp.Document` object.
   * De `com.adobe.idp.Document` object `copyToFile` methode om het PDF-document te extraheren.

**Zie ook**

[Snel starten (SOAP modus): een PDF-document samenstellen met een Bates-nummering met de Java API](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-assembling-a-pdf-document-with-bates-numbering-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Documenten samenstellen met Bates-nummering met de webservice-API {#assemble-documents-with-bates-numbering-using-the-web-service-api}

U kunt een PDF-document samenstellen dat gebruikmaakt van unieke pagina-id&#39;s (Bates-nummering) met behulp van de API (webservice) van de Assembler-service:

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
   * Een `System.IO.FileStream` door de constructor aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het DDX-document en de modus voor het openen van het bestand in vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van de `System.IO.FileStream` object. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` object `Length` eigenschap.
   * De bytearray vullen met streamgegevens door de `System.IO.FileStream` object `Read` methode. Geef de bytearray, de startpositie en de streamlengte door om te lezen.
   * Vul de `BLOB` object door het toe te wijzen `MTOM` veld met de inhoud van de bytearray.

1. Referentie-invoer PDF-documenten.

   * Maak voor elk invoerdocument een PDF `BLOB` object met behulp van de constructor. De `BLOB` wordt gebruikt om het invoerdocument PDF op te slaan.
   * Een `System.IO.FileStream` object door de constructor ervan aan te roepen. Geef een tekenreekswaarde door die staat voor de bestandslocatie van het invoerdocument en de modus waarin het PDF-bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van de `System.IO.FileStream` object. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` object `Length` eigenschap.
   * De bytearray vullen met streamgegevens door de `System.IO.FileStream` object `Read` methode. Geef de bytearray, de startpositie en de streamlengte door om te lezen.
   * Vul de `BLOB` object door het toe te wijzen `MTOM` eigenschap met de inhoud van de bytearray.
   * Een `MyMapOf_xsd_string_To_xsd_anyType` object. Dit verzamelingsobject wordt gebruikt om de invoerdocumenten PDF op te slaan.
   * Maak voor elk invoerdocument een PDF `MyMapOf_xsd_string_To_xsd_anyType_Item` object. Als bijvoorbeeld twee invoerdocumenten PDF worden gebruikt, maakt u twee invoerdocumenten `MyMapOf_xsd_string_To_xsd_anyType_Item` objecten.
   * Wijs een tekenreekswaarde toe die de sleutelnaam vertegenwoordigt aan de `MyMapOf_xsd_string_To_xsd_anyType_Item` object `key` veld. Deze waarde moet overeenkomen met de waarde van het PDF-bronelement dat is opgegeven in het DDX-document. (Voer deze taak uit voor elk invoerdocument van de PDF.)
   * Wijs het `BLOB` object waarin het PDF-document is opgeslagen in het `MyMapOf_xsd_string_To_xsd_anyType_Item` object `value` veld. (Voer deze taak uit voor elk invoerdocument van de PDF.)
   * Voeg de `MyMapOf_xsd_string_To_xsd_anyType_Item` aan `MyMapOf_xsd_string_To_xsd_anyType` object. De `MyMapOf_xsd_string_To_xsd_anyType` object `Add` en geeft de `MyMapOf_xsd_string_To_xsd_anyType` object. (Voer deze taak uit voor elk invoerdocument van de PDF.)

1. Stel de oorspronkelijke waarde voor Bates-nummer in.

   * Een `AssemblerOptionSpec` object dat uitvoeringsopties opslaat met de constructor ervan.
   * Stel het initiële Bates-nummer in door een numerieke waarde toe te wijzen aan de `firstBatesNumber` gegevenslid dat tot `AssemblerOptionSpec` object.

1. Stel de invoerdocumenten PDF samen.

   De `AssemblerServiceClient` object `invoke` en geeft de volgende waarden door:

   * A `BLOB` object dat het DDX-document vertegenwoordigt.
   * De `MyMapOf_xsd_string_To_xsd_anyType` -object dat de invoerdocumenten PDF bevat. Zijn sleutels moeten de namen van de PDF brondossiers aanpassen, en zijn waarden moeten zijn `BLOB` objecten die overeenkomen met die bestanden.
   * An `AssemblerOptionSpec` -object dat uitvoeringsopties opgeeft.

   De `invoke` methode retourneert een `AssemblerResult` object dat de resultaten van de taak en eventuele uitzonderingen bevat die zijn opgetreden.

1. Extraheer de resultaten.

   Voer de volgende handelingen uit om het nieuwe PDF-document te verkrijgen:

   * Toegang krijgen tot de `AssemblerResult` object `documents` veld, dat een `Map` -object dat de PDF-documenten van het resultaat bevat.
   * Doorlopen `Map` -object totdat u de sleutel vindt die overeenkomt met de naam van het resulterende document. Dan giet dat serielid `value` een `BLOB`.
   * Extraheer de binaire gegevens die het document van de PDF door tot zijn toegang te hebben vertegenwoordigen `BLOB` object `MTOM` eigenschap. Hiermee wordt een array met bytes geretourneerd die u naar een PDF-bestand kunt schrijven.

**Zie ook**

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
