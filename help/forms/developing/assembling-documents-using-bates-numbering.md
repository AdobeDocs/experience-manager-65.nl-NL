---
title: Documenten samenstellen met gebruik van Bates-nummering
seo-title: Documenten samenstellen met gebruik van Bates-nummering
description: 'null'
seo-description: 'null'
uuid: 28d5faeb-6915-41a2-b6a0-78d255df024f
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 77e9b895-1313-4a5b-a2d5-cdb65bdc1966
translation-type: tm+mt
source-git-commit: 1343cc33a1e1ce26c0770a3b49317e82353497ab
workflow-type: tm+mt
source-wordcount: '1901'
ht-degree: 0%

---


# Documenten samenstellen met gebruik van Bates-nummering {#assembling-documents-using-bates-numbering}

U kunt PDF-documenten die unieke pagina-id&#39;s bevatten, samenstellen met Bates-nummering. *Bates-nummering* is een methode voor het toepassen van unieke identificaties op een batch gerelateerde documenten. Aan elke pagina in het document (of elke set documenten) wordt een Bates-nummer toegewezen dat de pagina op unieke wijze identificeert. Bijvoorbeeld, kunnen de productiedocumenten die rekening van materiaalinformatie bevatten en met de productie van een assemblage worden geassocieerd een herkenningsteken bevatten. Een Bates-nummer bevat een opeenvolgend verhoogde numerieke waarde en een optioneel voor- en achtervoegsel. Het voorvoegsel + numeriek + achtervoegsel wordt een *bates-patroon* genoemd.

In de volgende afbeelding ziet u een PDF-document dat een unieke id bevat die zich in de koptekst van het document bevindt.

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

Dit DDX-document voegt twee PDF-documenten met de naam *map.pdf* en *direction.pdf* samen tot één PDF-document. Het resulterende PDF-document bevat een koptekst die bestaat uit een unieke pagina-id. Het document in de bovenstaande afbeelding toont bijvoorbeeld 000016.

>[!NOTE]
>
>Voordat u deze sectie leest, is het raadzaam om vertrouwd te zijn met het samenstellen van PDF-documenten met de Assembler-service. In deze sectie worden de concepten niet besproken, zoals het maken van een verzamelingsobject dat invoerdocumenten bevat of het extraheren van de resultaten van het geretourneerde verzamelingsobject. (Zie PDF-documenten [programmatisch samenstellen](/help/forms/developing/programmatically-assembling-pdf-documents.md).)

>[!NOTE]
>
>Voor meer informatie over de dienst van de Assembler, zie de Verwijzing van de [Diensten voor AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Voor meer informatie over een DX- document, zie de Dienst van de [Assembler en de Verwijzing](https://www.adobe.com/go/learn_aemforms_ddx_63)DDX.

## Overzicht van de stappen {#summary-of-steps}

U kunt als volgt een PDF-document samenstellen dat een unieke pagina-id (Bates-nummering) bevat:

1. Inclusief projectbestanden.
1. Maak een PDF Assembler-client.
1. Verwijs naar een bestaand DDX-document.
1. Referentie-invoer-PDF-documenten.
1. Stel de oorspronkelijke waarde voor Bates-nummer in.
1. Stel de invoer-PDF-documenten samen.
1. Extraheer de resultaten.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-assembler-client.jar
* adobe-utilities.jar (vereist als AEM Forms worden geïmplementeerd op JBoss)
* jbossall-client.jar (vereist als AEM Forms worden geïmplementeerd op JBoss)

Als AEM Forms worden geïmplementeerd op een andere ondersteunde J2EE-toepassingsserver dan JBoss, moet u de bestanden adobe-utilities.jar en jbossall-client.jar vervangen door JAR-bestanden die specifiek zijn voor de J2EE-toepassingsserver waarop AEM Forms worden geïmplementeerd. Zie [Including AEM Forms Java library files](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)voor informatie over de locatie van alle JAR-bestanden voor AEM Forms.

**Een PDF Assembler-client maken**

Alvorens u programmatically een verrichting van de Assembler kunt uitvoeren, moet u een de dienstcliënt van de Assembler tot stand brengen.

**Verwijzen naar een bestaand DDX-document**

Er moet naar een DDX-document worden verwezen om een PDF-document samen te stellen. Neem bijvoorbeeld het DDX-document dat in deze sectie is geïntroduceerd. Als u een PDF-document wilt samenstellen dat unieke pagina-id&#39;s bevat, moet het DDX-document het `BatesNumber` element bevatten.

**Referentie-invoer PDF-documenten**

Er moet worden verwezen naar invoer-PDF-documenten om een PDF-document samen te stellen. Er moet bijvoorbeeld naar de documenten map.pdf en direction.pdf worden verwezen om deze PDF-documenten samen te voegen tot één PDF-document.

**Stel de oorspronkelijke waarde voor het Bates-nummer in**

U kunt de aanvankelijke waarde van Bates aantal plaatsen om aan uw bedrijfsvereisten te voldoen. Stel bijvoorbeeld dat het een vereiste is om de beginwaarde in te stellen op 000100. Als u de beginwaarde niet instelt, is de waarde van de eerste pagina 000000.

**PDF-invoerdocumenten samenstellen**

Nadat u de de dienstcliënt van de Assembler creeert, verwijzing het DX- document dat `BatesNumber` elementeninformatie bevat, een inputPDF- document, en vastgestelde runtime opties bevat, kunt u de `invokeDDX` verrichting aanhalen die in de dienst van de Assembler resulteert die een Pdf- document assembleert dat unieke paginaadentifiers bevat.

**De resultaten extraheren**

De dienst van de Assembler keert een inzamelingsvoorwerp terug dat de baanresultaten bevat. U kunt het resulterende PDF-document en eventuele uitzonderingen extraheren. In dit geval bevindt een versleuteld PDF-document zich in het verzamelingsobject.

>[!NOTE]
>
>Een verzamelingsobject wordt geretourneerd als u de `invokeDDX` bewerking activeert. Deze bewerking wordt gebruikt wanneer twee of meer invoer-PDF-documenten worden doorgegeven aan de Assembler-service. Als u echter slechts één PDF-invoerdocument doorgeeft aan de Assembler-service, moet u de `invokeOneDocument` bewerking activeren. Zie Gecodeerde PDF-documenten [](/help/forms/developing/assembling-encrypted-pdf-documents.md)samenstellen voor informatie over het gebruik van deze bewerking.

**Zie ook**

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[PDF-documenten programmatisch samenstellen](/help/forms/developing/programmatically-assembling-pdf-documents.md)

## Documenten samenstellen met Bates-nummering met de Java API {#assemble-documents-with-bates-numbering-using-the-java-api}

U kunt een PDF-document samenstellen dat gebruikmaakt van unieke pagina-id&#39;s (Bates-nummering) met de API (Java) van de Assembler Service:

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-assembler-client.jar, op in het klassenpad van uw Java-project.

1. Maak een PDF Assembler-client.

   * Maak een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Maak een `AssemblerServiceClient` object door de constructor ervan te gebruiken en het `ServiceClientFactory` object door te geven.

1. Verwijs naar een bestaand DDX-document.

   * Maak een `java.io.FileInputStream` object dat het DDX-document vertegenwoordigt door de constructor ervan te gebruiken en een tekenreekswaarde door te geven die de locatie van het DDX-bestand aangeeft.
   * Maak een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en het `java.io.FileInputStream` object door te geven.

1. Referentie-invoer-PDF-documenten.

   * Maak een `java.util.Map` object dat wordt gebruikt om invoer-PDF-documenten op te slaan met behulp van een `HashMap` constructor.
   * Maak voor elk invoer-PDF-document een `java.io.FileInputStream` object met behulp van de constructor en geef de locatie van het invoer-PDF-document door. Geef dan de locatie van een onbeveiligd PDF-document door.
   * Maak voor elk invoer-PDF-document een `com.adobe.idp.Document` object en geef het `java.io.FileInputStream` object met het PDF-document door.
   * Voeg een item aan het `java.util.Map` `put` object toe door de methode ervan aan te roepen en de volgende argumenten door te geven:

      * Een tekenreekswaarde die de sleutelnaam vertegenwoordigt. Deze waarde moet overeenkomen met de waarde van het PDF-bronelement dat is opgegeven in het DDX-document. De naam van het PDF-bronbestand dat is opgegeven in het DDX-document dat in deze sectie wordt geïntroduceerd, is bijvoorbeeld Loan.pdf.
      * Een `com.adobe.idp.Document` object dat het onbeveiligde PDF-document bevat.

1. Stel de oorspronkelijke waarde voor Bates-nummer in.

   * Maak een `AssemblerOptionSpec` object dat uitvoeringsopties opslaat met de constructor ervan.
   * Stel het eerste Bates-nummer in door het `AssemblerOptionSpec` object aan te roepen `setFirstBatesNumber` en een numerieke waarde door te geven die de beginwaarde opgeeft.

1. Stel de invoer-PDF-documenten samen.

   Roep de `AssemblerServiceClient` methode van het `invokeDDX` object aan en geef de volgende vereiste waarden door:

   * Een `com.adobe.idp.Document` object dat het DDX-document vertegenwoordigt.
   * Een `java.util.Map` object dat het invoer-onbeveiligde PDF-bestand bevat.
   * Een `com.adobe.livecycle.assembler.client.AssemblerOptionSpec` object dat de runtime-opties opgeeft, inclusief het standaardniveau voor lettertypen en taaklogbestanden.

   De `invokeDDX` methode retourneert een `com.adobe.livecycle.assembler.client.AssemblerResult` object dat een PDF-document met een wachtwoord bevat.

1. Extraheer de resultaten.

   Voer de volgende handelingen uit om het nieuwe PDF-document te verkrijgen:

   * Roep de `AssemblerResult` methode van het `getDocuments` object aan. Deze handeling retourneert een `java.util.Map` object.
   * Doorloop het `java.util.Map` object totdat u het `com.adobe.idp.Document` object vindt.
   * Roep de `com.adobe.idp.Document` methode van het `copyToFile` object aan om het PDF-document uit te pakken.

**Zie ook**

[Snel starten (SOAP-modus): Een PDF-document samenstellen met Bates-nummering met behulp van de Java API](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-assembling-a-pdf-document-with-bates-numbering-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Documenten samenstellen met Bates-nummering met behulp van de webservice-API {#assemble-documents-with-bates-numbering-using-the-web-service-api}

U kunt een PDF-document samenstellen dat gebruikmaakt van unieke pagina-id&#39;s (Bates-nummering) met behulp van de API (webservice) van de Assembler-service:

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
   * Maak een `System.IO.FileStream` object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het DDX-document en de modus voor het openen van het bestand in vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van het `System.IO.FileStream` object wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` eigenschap van het `Length` object op te halen.
   * Vul de bytearray met streamgegevens door de `System.IO.FileStream` `Read` methode van het object aan te roepen. Geef de bytearray, de startpositie en de streamlengte door om te lezen.
   * Vul het `BLOB` object door het `MTOM` veld ervan toe te wijzen met de inhoud van de bytearray.

1. Referentie-invoer-PDF-documenten.

   * Maak voor elk invoer-PDF-document een `BLOB` object met behulp van de constructor ervan. Het `BLOB` object wordt gebruikt om het invoer-PDF-document op te slaan.
   * Maak een `System.IO.FileStream` object door de constructor ervan aan te roepen. Geef een tekenreekswaarde door die staat voor de bestandslocatie van het invoer-PDF-document en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van het `System.IO.FileStream` object wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` eigenschap van het `Length` object op te halen.
   * Vul de bytearray met streamgegevens door de `System.IO.FileStream` `Read` methode van het object aan te roepen. Geef de bytearray, de startpositie en de streamlengte door om te lezen.
   * Vul het `BLOB` object door de `MTOM` eigenschap ervan toe te wijzen met de inhoud van de bytearray.
   * Create a `MyMapOf_xsd_string_To_xsd_anyType` object. Dit verzamelingsobject wordt gebruikt om de invoer-PDF-documenten op te slaan.
   * Maak voor elk invoer-PDF-document een `MyMapOf_xsd_string_To_xsd_anyType_Item` object. Als bijvoorbeeld twee invoer-PDF-documenten worden gebruikt, maakt u twee `MyMapOf_xsd_string_To_xsd_anyType_Item` objecten.
   * Wijs een tekenreekswaarde toe die de sleutelnaam aan het `MyMapOf_xsd_string_To_xsd_anyType_Item` `key` gebied van het voorwerp vertegenwoordigt. Deze waarde moet overeenkomen met de waarde van het PDF-bronelement dat is opgegeven in het DDX-document. (Voer deze taak uit voor elk invoer-PDF-document.)
   * Wijs het `BLOB` object waarin het PDF-document is opgeslagen, toe aan het `MyMapOf_xsd_string_To_xsd_anyType_Item` veld van het `value` object. (Voer deze taak uit voor elk invoer-PDF-document.)
   * Voeg het `MyMapOf_xsd_string_To_xsd_anyType_Item` object toe aan het `MyMapOf_xsd_string_To_xsd_anyType` object. Roep de `MyMapOf_xsd_string_To_xsd_anyType` methode van het `Add` object aan en geef het `MyMapOf_xsd_string_To_xsd_anyType` object door. (Voer deze taak uit voor elk invoer-PDF-document.)

1. Stel de oorspronkelijke waarde voor Bates-nummer in.

   * Maak een `AssemblerOptionSpec` object dat uitvoeringsopties opslaat met de constructor ervan.
   * Stel het eerste Bates-nummer in door een numerieke waarde toe te wijzen aan het `firstBatesNumber` gegevenslid dat tot het `AssemblerOptionSpec` object behoort.

1. Stel de invoer-PDF-documenten samen.

   Roep de methode van het `AssemblerServiceClient` `invoke` object aan en geef de volgende waarden door:

   * Een `BLOB` object dat het DDX-document vertegenwoordigt.
   * Het `MyMapOf_xsd_string_To_xsd_anyType` object dat de invoer-PDF-documenten bevat. De sleutels moeten overeenkomen met de namen van de PDF-bronbestanden en de waarden ervan moeten de `BLOB` objecten zijn die overeenkomen met die bestanden.
   * Een `AssemblerOptionSpec` object dat uitvoeringsopties opgeeft.

   De `invoke` methode retourneert een `AssemblerResult` object dat de resultaten van de taak en eventuele uitzonderingen bevat die zich hebben voorgedaan.

1. Extraheer de resultaten.

   Voer de volgende handelingen uit om het nieuwe PDF-document te verkrijgen:

   * Open het `AssemblerResult` veld van het `documents` object. Dit is een `Map` object dat de PDF-resultaatdocumenten bevat.
   * Doorloop het `Map` object totdat u de sleutel vindt die overeenkomt met de naam van het resulterende document. Dan giet dat serielid `value` aan een `BLOB`.
   * Pak de binaire gegevens die het PDF-document vertegenwoordigen, uit door de `BLOB` eigenschap van het `MTOM` object te openen. Hiermee wordt een array met bytes geretourneerd die u naar een PDF-bestand kunt schrijven.

**Zie ook**

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
