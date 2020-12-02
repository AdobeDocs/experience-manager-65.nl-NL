---
title: PDF-documenten programmatisch demonteren
seo-title: PDF-documenten programmatisch demonteren
description: 'null'
seo-description: 'null'
uuid: d71cc044-e948-4b7a-b598-b041723b69e9
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 8e38a597-5d22-4d83-95fe-4494fb04e4a3
translation-type: tm+mt
source-git-commit: 1343cc33a1e1ce26c0770a3b49317e82353497ab
workflow-type: tm+mt
source-wordcount: '1730'
ht-degree: 0%

---


# PDF-documenten {#programmatically-disassembling-pdf-documents} programmatisch demonteren

U kunt een PDF-document demonteren door het door te geven aan de Assembler-service. Deze taak is meestal handig wanneer het PDF-document oorspronkelijk is gemaakt op basis van veel afzonderlijke documenten, zoals een verzameling instructies. In de volgende afbeelding wordt DocA opgedeeld in meerdere resulterende documenten, waarbij de bladwijzer van het eerste niveau 1 op een pagina het begin van een nieuw resulterend document aangeeft.

![pd_pd_pdfsfrombookmarks](assets/pd_pd_pdfsfrombookmarks.png)

Als u een PDF-document wilt demonteren, controleert u of het element `PDFsFromBookmarks` zich in het DDX-document bevindt. Het element `PDFsFromBookmarks` is een resulterend element en kan slechts een kindelement van het `DDX` element zijn. Het heeft geen `result` attribuut omdat het in de generatie van veelvoudige documenten kan resulteren.

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
>Voordat u deze sectie leest, is het raadzaam bekend te zijn met het samenstellen van PDF-documenten met de Assembler-service. (Zie [PDF-documenten programmatisch samenstellen](/help/forms/developing/programmatically-assembling-pdf-documents.md).)

>[!NOTE]
>
>Wanneer u één PDF-document doorgeeft aan de Assembler-service en één document terugkrijgt, kunt u de `invokeOneDocument`-bewerking activeren. Als u een PDF-document echter wilt demonteren, gebruikt u de `invokeDDX`-bewerking omdat, hoewel één PDF-invoerdocument wordt doorgegeven aan de Assembler-service, de Assembler-service een verzamelingsobject retourneert dat een of meer documenten bevat.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Assembler, zie [de Verwijzing van de Diensten voor AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Voor meer informatie over een DX- document, zie [de Dienst van de Assembler en DX Verwijzing](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Overzicht van stappen {#summary-of-steps}

Voer de volgende taken uit om een PDF-document te demonteren:

1. Inclusief projectbestanden.
1. Maak een PDF Assembler-client.
1. Verwijs naar een bestaand DDX-document.
1. Verwijs naar een PDF-document dat u wilt demonteren.
1. Stel runtime-opties in.
1. Het PDF-document demonteren.
1. Sla de gedemonteerde PDF-documenten op.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-assembler-client.jar
* adobe-utilities.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)

als AEM Forms wordt geïmplementeerd op een ondersteunde J2EE-toepassingsserver die geen JBoss is, moet u adobe-utilities.jar en jbossall-client.jar vervangen door JAR-bestanden die specifiek zijn voor de J2EE-toepassingsserver waarop AEM Forms wordt geïmplementeerd.

**Een PDF Assembler-client maken**

Alvorens u programmatically een verrichting van de Assembler kunt uitvoeren, moet u een de dienstcliënt van de Assembler tot stand brengen.

**Verwijzen naar een bestaand DDX-document**

Er moet naar een DDX-document worden verwezen om een PDF-document te demonteren. Dit DDX-document moet het element `PDFsFromBookmarks` bevatten.

**Verwijzen naar een PDF-document om te demonteren**

Als u een PDF-document wilt demonteren, verwijst u naar een PDF-bestand dat het PDF-document vertegenwoordigt dat u wilt demonteren. Als u een document doorgeeft aan de Assembler-service, wordt een afzonderlijk PDF-document geretourneerd voor elke bladwijzer van niveau 1 in het document.

**Uitvoeringsopties instellen**

U kunt runtime opties plaatsen die het gedrag van de dienst van de Assembler controleren terwijl het een baan uitvoert. U kunt bijvoorbeeld een optie instellen die de Assembler-service de opdracht geeft door te gaan met het verwerken van een taak als er een fout optreedt.

**Het PDF-document dempen**

Nadat u de Assembler-serviceclient hebt gemaakt, naar het DDX-document hebt verwezen, naar een PDF-document hebt verwezen om het samen te voegen en uitvoeringsopties hebt ingesteld, kunt u een PDF-document demonteren door de methode `invokeDDX` aan te roepen. Op voorwaarde dat het DDX-document instructies bevat voor het demonteren van het PDF-document, retourneert de Assembler-service gedemonteerde PDF-documenten in een verzamelingsobject.

**De gedemonteerde PDF-documenten opslaan**

Alle gedemonteerde PDF-documenten worden geretourneerd in een verzamelingsobject. Doorloop het verzamelingsobject en sla elk PDF-document op als een PDF-bestand.

**Zie ook**

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[PDF-documenten programmatisch samenstellen](/help/forms/developing/programmatically-assembling-pdf-documents.md)

## Een PDF-document ontkoppelen met de Java API {#disassemble-a-pdf-document-using-the-java-api}

U kunt een PDF-document desassembleren met de API (Java) voor de vergaderingsservice:

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-assembler-client.jar, op in het klassenpad van uw Java-project.

1. Maak een PDF Assembler-client.

   * Maak een `ServiceClientFactory`-object dat verbindingseigenschappen bevat.
   * Maak een `AssemblerServiceClient`-object door de constructor ervan te gebruiken en het object `ServiceClientFactory` door te geven.

1. Verwijs naar een bestaand DDX-document.

   * Maak een `java.io.FileInputStream`-object dat het DDX-document vertegenwoordigt door de constructor ervan te gebruiken en een tekenreekswaarde door te geven die de locatie van het DDX-bestand aangeeft.
   * Maak een `com.adobe.idp.Document`-object door de constructor ervan te gebruiken en het object `java.io.FileInputStream` door te geven.

1. Verwijs naar een PDF-document dat u wilt demonteren.

   * Maak een `java.util.Map`-object dat wordt gebruikt om invoer-PDF-documenten op te slaan met behulp van een `HashMap`-constructor.
   * Maak een `java.io.FileInputStream`-object door de constructor ervan te gebruiken en de locatie van het PDF-document door te geven om te demonteren.
   * Maak een `com.adobe.idp.Document`-object en geef het `java.io.FileInputStream`-object door dat het PDF-document bevat dat u wilt demonteren.
   * Voeg een item aan het object `java.util.Map` toe door de methode `put` ervan aan te roepen en de volgende argumenten door te geven:

      * Een tekenreekswaarde die de sleutelnaam vertegenwoordigt. Deze waarde moet overeenkomen met de waarde van het PDF-bronelement dat is opgegeven in het DDX-document.
      * Een `com.adobe.idp.Document`-object dat het te demonteren PDF-document bevat.

1. Stel runtime-opties in.

   * Maak een `AssemblerOptionSpec`-object dat uitvoeringsopties opslaat met de constructor ervan.
   * Stel runtime-opties in om aan uw bedrijfsvereisten te voldoen door een methode aan te roepen die tot het object `AssemblerOptionSpec` behoort. Bijvoorbeeld, om de dienst van de Assembler op te dragen om een baan te blijven verwerken wanneer een fout voorkomt, haalt de `AssemblerOptionSpec` methode `setFailOnError` van objecten aan en gaat `false` over.

1. Het PDF-document demonteren.

   Roep de methode `invokeDDX` van het object `AssemblerServiceClient` aan en geef de volgende vereiste waarden door:

   * Een `com.adobe.idp.Document`-object dat het te gebruiken DDX-document vertegenwoordigt
   * Een `java.util.Map`-object dat het te demonteren PDF-document bevat
   * Een `com.adobe.livecycle.assembler.client.AssemblerOptionSpec`-object dat de runtime-opties opgeeft, inclusief het standaardfont en het taaklogniveau

   De methode `invokeDDX` retourneert een `com.adobe.livecycle.assembler.client.AssemblerResult`-object dat de gedemonteerde PDF-documenten en eventuele uitzonderingen bevat.

1. Sla de gedemonteerde PDF-documenten op.

   Voer de volgende handelingen uit om de gedemonteerde PDF-documenten te verkrijgen:

   * Roep de methode `AssemblerResult` van het object `getDocuments` aan. Dit retourneert een `java.util.Map`-object.
   * Doorloop het object `java.util.Map` totdat u het resulterende object `com.adobe.idp.Document` hebt gevonden.
   * Roep de methode `com.adobe.idp.Document` van het object `copyToFile` aan om het PDF-document uit te pakken.

**Zie ook**

[PDF-documenten programmatisch demonteren](#programmatically-disassembling-pdf-documents)

[Snel starten (SOAP-modus): Een PDF-document demonteren met de Java API](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-disassembling-a-pdf-document-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Een PDF-document ontkoppelen met de webservice-API {#disassemble-a-pdf-document-using-the-web-service-api}

U kunt een PDF-document desassembleren met de API (webservice) voor de Assembler-service:

1. Inclusief projectbestanden.

   Creeer een project van Microsoft .NET dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt wanneer het plaatsen van een de dienstverwijzing: `http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1`.

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
   * Maak een `System.IO.FileStream`-object door de constructor ervan aan te roepen. Geef een tekenreekswaarde door die staat voor de bestandslocatie van het DDX-document en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van het object `System.IO.FileStream` wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de eigenschap `System.IO.FileStream` van het object `Length` op te halen.
   * Vul de bytearray met streamgegevens door de methode `Read` van het object `System.IO.FileStream` aan te roepen en de bytearray, de startpositie en de lengte van de stream door te geven om te lezen.
   * Vul het object `BLOB` door de eigenschap `MTOM` ervan toe te wijzen met de inhoud van de bytearray.

1. Verwijs naar een PDF-document dat u wilt demonteren.

   * Maak een `BLOB`-object met de constructor ervan. Met het object `BLOB` wordt het invoer-PDF-document opgeslagen. Dit `BLOB` voorwerp wordt overgegaan tot `invokeOneDocument` als argument.
   * Maak een `System.IO.FileStream`-object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het invoer-PDF-document en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van het object `System.IO.FileStream` wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de eigenschap `System.IO.FileStream` van het object `Length` op te halen.
   * Vul de bytearray met streamgegevens door de methode `Read` van het object `System.IO.FileStream` aan te roepen en de bytearray, de startpositie en de lengte van de stream door te geven om te lezen.
   * Vul het object `BLOB` door het veld `MTOM` ervan de inhoud van de bytearray toe te wijzen.
   * Maak een `MyMapOf_xsd_string_To_xsd_anyType`-object. Met dit verzamelingsobject wordt de PDF opgeslagen om te demonteren.
   * Maak een `MyMapOf_xsd_string_To_xsd_anyType_Item`-object.
   * Wijs een tekenreekswaarde toe die de sleutelnaam vertegenwoordigt aan het `key`-veld van het `MyMapOf_xsd_string_To_xsd_anyType_Item`-object. Deze waarde moet overeenkomen met de waarde van het PDF-bronelement dat is opgegeven in het DDX-document.
   * Wijs het `BLOB`-object toe dat het PDF-document opslaat in het veld `MyMapOf_xsd_string_To_xsd_anyType_Item` van het `value`-object.
   * Voeg het object `MyMapOf_xsd_string_To_xsd_anyType_Item` toe aan het object `MyMapOf_xsd_string_To_xsd_anyType`. Roep de `MyMapOf_xsd_string_To_xsd_anyType`-methode `Add` aan en geef het `MyMapOf_xsd_string_To_xsd_anyType`-object door.

1. Stel runtime-opties in.

   * Maak een `AssemblerOptionSpec`-object dat uitvoeringsopties opslaat met de constructor ervan.
   * Stel runtime-opties in om aan uw bedrijfsvereisten te voldoen door een waarde toe te wijzen aan een gegevenslid dat tot het object `AssemblerOptionSpec` behoort. Als u bijvoorbeeld de Assembler-service wilt instrueren een taak te blijven verwerken wanneer een fout optreedt, wijst u `false` toe aan het veld `AssemblerOptionSpec` van het `failOnError`-object.

1. Het PDF-document demonteren.

   Roep de methode `invokeDDX` van het object `AssemblerServiceClient` aan en geef de volgende waarden door:

   * Een `BLOB`-object dat staat voor het DDX-document dat het PDF-document demonteert
   * Het `MyMapOf_xsd_string_To_xsd_anyType`-object dat het te demonteren PDF-document bevat
   * Een `AssemblerOptionSpec`-object dat uitvoeringsopties opgeeft

   De methode `invokeDDX` retourneert een `AssemblerResult`-object dat de taakresultaten en eventuele uitzonderingen bevat die zich hebben voorgedaan.

1. Sla de gedemonteerde PDF-documenten op.

   Voer de volgende handelingen uit om de nieuwe PDF-documenten te verkrijgen:

   * Open het veld `AssemblerResult` van het object `documents`. Dit is een `Map`-object dat de gedemonteerde PDF-documenten bevat.
   * Doorloop het object `Map` om elk resulterend document te verkrijgen. Vervolgens cast u `value` van dat arraylid naar een `BLOB`.
   * Pak de binaire gegevens die het PDF-document vertegenwoordigen uit door de eigenschap `MTOM` van het object `BLOB` te openen. Hiermee wordt een array met bytes geretourneerd die u naar een PDF-bestand kunt schrijven.

**Zie ook**

[PDF-documenten programmatisch demonteren](#programmatically-disassembling-pdf-documents)

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
