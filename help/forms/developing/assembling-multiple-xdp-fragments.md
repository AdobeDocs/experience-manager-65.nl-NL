---
title: Meerdere XDP-fragmenten samenstellen
seo-title: Meerdere XDP-fragmenten samenstellen
description: U kunt meerdere XDP-fragmenten samenvoegen in één XDP-document met de Java API en Web Service API.
seo-description: U kunt meerdere XDP-fragmenten samenvoegen in één XDP-document met de Java API en Web Service API.
uuid: 0e35ff85-ff40-4878-ae31-aa8da75bd3ec
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: c4706632-02e5-4510-ad9c-4f732d5fbdad
docset: aem65
role: Developer
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '1909'
ht-degree: 0%

---


# Meerdere XDP-fragmenten samenstellen{#assembling-multiple-xdp-fragments}

U kunt meerdere XDP-fragmenten samenvoegen tot één XDP-document. Neem bijvoorbeeld XDP-fragmenten waarin elk XDP-bestand een of meer subformulieren bevat die worden gebruikt om een gezondheidsformulier te maken. De volgende afbeelding toont de omtrekweergave (vertegenwoordigt het bestand tuc018_template_flowed.xdp dat wordt gebruikt in het bestand *Meerdere XDP-fragmenten samenstellen* snel starten):

![am_am_forma](assets/am_am_forma.png)

In de volgende afbeelding ziet u de sectie Patiënt (staat voor het bestand tuc018_contact.xdp dat wordt gebruikt in het bestand *Meerdere XDP-fragmenten samenstellen* Snel starten):

![am_am_formb](assets/am_am_formb.png)

In de volgende afbeelding ziet u de sectie over de gezondheid van de patiënt (staat voor het bestand tuc018_patiënt.xdp dat wordt gebruikt in het bestand *Meerdere XDP-fragmenten samenstellen* snel starten):

![am_am_formc](assets/am_am_formc.png)

Dit fragment bevat twee subformulieren met de naam *subPatientphysical* en *subPatientHealth*. Beide subformulieren worden vermeld in het DDX-document dat wordt doorgegeven aan de Assembler-service. Met de Assembler-service kunt u al deze XDP-fragmenten combineren in één XDP-document, zoals in de volgende afbeelding wordt getoond.

![am_am_formd](assets/am_am_formd.png)

In het volgende DDX-document worden meerdere XDP-fragmenten samengevoegd in een XDP-document.

```xml
 <?xml version="1.0" encoding="UTF-8"?>
 <DDX xmlns="https://ns.adobe.com/DDX/1.0/">
         <XDP result="tuc018result.xdp">
            <XDP source="tuc018_template_flowed.xdp">
             <XDPContent insertionPoint="ddx_fragment" source="tuc018_contact.xdp" fragment="subPatientContact" required="false"/>
               <XDPContent insertionPoint="ddx_fragment" source="tuc018_patient.xdp" fragment="subPatientPhysical" required="false"/>
               <XDPContent insertionPoint="ddx_fragment" source="tuc018_patient.xdp" fragment="subPatientHealth" required="false"/>
            </XDP>
         </XDP>
 </DDX>
```

Het DDX-document bevat een XDP-tag `result` die de naam van het resultaat opgeeft. In deze situatie is de waarde `tuc018result.xdp`. Naar deze waarde wordt verwezen in de toepassingslogica die wordt gebruikt om het XDP-document op te halen nadat de Assembler-service het resultaat heeft geretourneerd. Neem bijvoorbeeld de volgende Java-toepassingslogica die wordt gebruikt om het geassembleerde XDP-document op te halen (de waarde is vet):

```java
 //Iterate through the map object to retrieve the result XDP document
 for (Iterator i = allDocs.entrySet().iterator(); i.hasNext();) {
     // Retrieve the Map object’s value
     Map.Entry e = (Map.Entry)i.next();
     //Get the key name as specified in the
     //DDX document
     String keyName = (String)e.getKey();
     if (keyName.equalsIgnoreCase("tuc018result.xdp"))
                 {
         Object o = e.getValue();
         outDoc = (Document)o;
         //Save the result PDF file
         File myOutFile = new File("C:\\AssemblerResultXDP.xdp");
         outDoc.copyToFile(myOutFile);
     }
 }
```

Met de tag `XDP source` wordt het XDP-bestand opgegeven dat een volledig XDP-document vertegenwoordigt dat kan worden gebruikt als container voor het toevoegen van XDP-fragmenten of als een van een aantal documenten die op volgorde worden toegevoegd. In deze situatie wordt het XDP-document alleen als container gebruikt (de eerste illustratie die wordt getoond in *Meerdere XDP-fragmenten samenvoegen*). De andere XDP-bestanden worden dus in de XDP-container geplaatst.

Voor elk subformulier kunt u een `XDPContent`-element toevoegen (dit element is optioneel). In het bovenstaande voorbeeld zijn er drie subformulieren: `subPatientContact`, `subPatientPhysical` en `subPatientHealth`. Zowel het subformulier `subPatientPhysical` als het subformulier `subPatientHealth` bevinden zich in hetzelfde XDP-bestand, tuc018_patiënt.xdp. Het fragmentelement geeft de naam van het subformulier op, zoals gedefinieerd in Designer.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Assembler, zie [de Verwijzing van de Diensten voor AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Voor meer informatie over een DX- document, zie [de Dienst van de Assembler en DX Verwijzing](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Overzicht van stappen {#summary-of-steps}

Voer de volgende taken uit om meerdere XDP-fragmenten samen te stellen:

1. Inclusief projectbestanden.
1. Maak een PDF Assembler-client.
1. Verwijs naar een bestaand DDX-document.
1. Verwijs naar de XDP-documenten.
1. Stel runtime-opties in.
1. Stel de meerdere XDP-documenten samen.
1. Haal het samengevoegde XDP-document op.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-assembler-client.jar
* adobe-utilities.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)

**Een PDF Assembler-client maken**

Alvorens u programmatically een verrichting van de Assembler kunt uitvoeren, creeer een de dienstcliënt van de Assembler.

**Verwijzen naar een bestaand DDX-document**

Er moet naar een DDX-document worden verwezen om meerdere XDP-documenten samen te stellen. Dit DDX-document moet `XDP result`, `XDP source` en `XDPContent` elementen bevatten.

**Verwijzen naar de XDP-documenten**

Als u meerdere XDP-documenten wilt samenstellen, verwijst u naar alle XDP-bestanden die worden gebruikt om het resultaat-XDP-document samen te stellen. Zorg ervoor dat de naam van het subformulier in het XDP-document waarnaar wordt verwezen door het `source`-kenmerk, is opgegeven in het `fragment`-kenmerk. Een subformulier wordt gedefinieerd in Designer. Neem bijvoorbeeld de volgende XML.

```xml
 <XDPContent insertionPoint="ddx_fragment" source="tuc018_contact.xdp" fragment="subPatientContact" required="false"/>
```

Het subformulier met de naam *subPatientContact* moet zich bevinden in het XDP-bestand met de naam *tuc018_contact.xdp*.

**Uitvoeringsopties instellen**

U kunt runtime opties plaatsen die het gedrag van de dienst van de Assembler controleren terwijl het een baan uitvoert. U kunt bijvoorbeeld een optie instellen die de Assembler-service de opdracht geeft door te gaan met het verwerken van een taak als er een fout optreedt.

**Meerdere XDP-documenten samenstellen**

Als u meerdere XDP-bestanden wilt samenstellen, roept u de bewerking `invokeDDX` aan. De dienst van de Assembler keert het geassembleerde XDP document binnen een inzamelingsvoorwerp terug.

**Het samengevoegde XDP-document ophalen**

Een samengesteld XDP-document wordt geretourneerd binnen een verzamelingsobject. Doorloop het verzamelingsobject en sla het XDP-document op als een XDP-bestand. U kunt het XDP-document ook doorgeven aan een andere AEM Forms-service, zoals Output.

**Zie ook**

[Meerdere XDP-fragmenten samenstellen met de Java API](assembling-multiple-xdp-fragments.md#assemble-multiple-xdp-fragments-using-the-java-api)

[Meerdere XDP-fragmenten samenstellen met de webservice-API](assembling-multiple-xdp-fragments.md#assemble-multiple-xdp-fragments-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[PDF-documenten programmatisch samenstellen](/help/forms/developing/programmatically-assembling-pdf-documents.md#programmatically-assembling-pdf-documents)

[PDF-documenten maken met behulp van fragmenten](/help/forms/developing/creating-document-output-streams.md#creating-pdf-documents-using-fragments)

## Meerdere XDP-fragmenten samenstellen met de Java API {#assemble-multiple-xdp-fragments-using-the-java-api}

U kunt meerdere XDP-fragmenten samenstellen met behulp van de API (Java) voor vergaderingsservice:

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-assembler-client.jar, op in het klassenpad van uw Java-project.

1. Maak een PDF Assembler-client.

   * Maak een `ServiceClientFactory`-object dat verbindingseigenschappen bevat.
   * Maak een `AssemblerServiceClient`-object door de constructor ervan te gebruiken en het object `ServiceClientFactory` door te geven.

1. Verwijs naar een bestaand DDX-document.

   * Maak een `java.io.FileInputStream`-object dat het DDX-document vertegenwoordigt door de constructor ervan te gebruiken en een tekenreekswaarde door te geven die de locatie van het DDX-bestand aangeeft.
   * Maak een `com.adobe.idp.Document`-object door de constructor ervan te gebruiken en het object `java.io.FileInputStream` door te geven.

1. Verwijs naar de XDP-documenten.

   * Maak een `java.util.Map`-object dat wordt gebruikt om invoer-XDP-documenten op te slaan met behulp van een `HashMap`-constructor.
   * Maak een `com.adobe.idp.Document`-object en geef het `java.io.FileInputStream`-object door dat het invoer-XDP-bestand bevat (herhaal deze taak voor elk XDP-bestand).
   * Voeg een item aan het object `java.util.Map` toe door de methode `put` ervan aan te roepen en de volgende argumenten door te geven:

      * Een tekenreekswaarde die de sleutelnaam vertegenwoordigt. Deze waarde moet overeenkomen met de waarde van het element `source` die is opgegeven in het DDX-document (herhaal deze taak voor elk XDP-bestand).
      * Een object `com.adobe.idp.Document` dat het XDP-document bevat dat overeenkomt met het element `source` (herhaal deze taak voor elk XDP-bestand).

1. Stel de runtime-opties in.

   * Maak een `AssemblerOptionSpec`-object dat uitvoeringsopties opslaat met de constructor ervan.
   * Stel runtime-opties in om aan uw bedrijfsvereisten te voldoen door een methode aan te roepen die tot het object `AssemblerOptionSpec` behoort. Bijvoorbeeld, om de dienst van de Assembler op te dragen om een baan te blijven verwerken wanneer een fout voorkomt, haalt de `AssemblerOptionSpec` methode `setFailOnError` van objecten aan en gaat `false` over.

1. Stel de meerdere XDP-documenten samen.

   Roep de methode `invokeDDX` van het object `AssemblerServiceClient` aan en geef de volgende vereiste waarden door:

   * Een `com.adobe.idp.Document`-object dat het te gebruiken DDX-document vertegenwoordigt
   * Een `java.util.Map`-object dat de invoer-XDP-bestanden bevat
   * Een `com.adobe.livecycle.assembler.client.AssemblerOptionSpec`-object dat de runtime-opties opgeeft, inclusief het standaardfont en het taaklogniveau

   De methode `invokeDDX` retourneert een `com.adobe.livecycle.assembler.client.AssemblerResult`-object dat het geassembleerde XDP-document bevat.

1. Haal het samengevoegde XDP-document op.

   Voer de volgende handelingen uit om het samengevoegde XDP-document te verkrijgen:

   * Roep de methode `AssemblerResult` van het object `getDocuments` aan. Deze methode retourneert een `java.util.Map`-object.
   * Doorloop het object `java.util.Map` totdat u het resulterende object `com.adobe.idp.Document` hebt gevonden.
   * Roep de methode `com.adobe.idp.Document` van het object `copyToFile` aan om het samengevoegde XDP-document te extraheren.

**Zie ook**

[Meerdere XDP-](assembling-multiple-xdp-fragments.md#assembling-multiple-xdp-fragments)
[fragmenten samenstellen in Quick Start (SOAP-modus): Meerdere XDP-fragmenten samenstellen met de Java ](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-assembling-multiple-xdp-fragments-using-the-java-api)
[APIInIncluding AEM Forms Java-bibliotheekbestandenVerbindingseigenschappen ](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)
[instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Meerdere XDP-fragmenten samenstellen met de webservice-API {#assemble-multiple-xdp-fragments-using-the-web-service-api}

U kunt meerdere XDP-fragmenten samenstellen met behulp van de API (webservice) van de Assembler Service:

1. Inclusief projectbestanden.

   Creeer een project van Microsoft .NET dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt wanneer het plaatsen van een de dienstverwijzing:

   ```java
    https://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1.
   ```

   >[!NOTE]
   >
   >Vervang `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een PDF Assembler-client.

   * Maak een `AssemblerServiceClient`-object met de standaardconstructor.
   * Maak een `AssemblerServiceClient.Endpoint.Address`-object met de constructor `System.ServiceModel.EndpointAddress`. Geef een tekenreekswaarde door die de WSDL opgeeft voor de AEM Forms-service, zoals `https://localhost:8080/soap/services/AssemblerService?blob=mtom`). U hoeft het `lc_version`-kenmerk niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.
   * Maak een `System.ServiceModel.BasicHttpBinding`-object door de waarde van het veld `AssemblerServiceClient.Endpoint.Binding` op te halen. Cast de terugkeerwaarde aan `BasicHttpBinding`.
   * Stel het veld `System.ServiceModel.BasicHttpBinding` van het object `MessageEncoding` in op `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam voor het AEM aan het veld `AssemblerServiceClient.ClientCredentials.UserName.UserName` toe.
      * Wijs de overeenkomstige wachtwoordwaarde aan het `AssemblerServiceClient.ClientCredentials.UserName.Password`gebied toe.
      * Wijs de constante waarde `HttpClientCredentialType.Basic` toe aan het `BasicHttpBindingSecurity.Transport.ClientCredentialType`veld.
      * Wijs de constante waarde `BasicHttpSecurityMode.TransportCredentialOnly` toe aan het `BasicHttpBindingSecurity.Security.Mode`veld.

1. Verwijs naar een bestaand DDX-document.

   * Maak een `BLOB`-object met de constructor ervan. Het object `BLOB` wordt gebruikt om het DDX-document op te slaan.
   * Maak een `System.IO.FileStream`-object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het DDX-document en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van het object `System.IO.FileStream` wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de eigenschap `System.IO.FileStream` van het object `Length` op te halen.
   * Vul de bytearray met streamgegevens door de methode `Read` van het object `System.IO.FileStream` aan te roepen. Geef de bytearray, de startpositie en de streamlengte door om te lezen.
   * Vul het object `BLOB` door de eigenschap `MTOM` ervan toe te wijzen met de inhoud van de bytearray.

1. Verwijs naar de XDP-documenten.

   * Maak voor elk invoer-XDP-bestand een `BLOB`-object met behulp van de constructor. Het object `BLOB` wordt gebruikt om het invoerbestand op te slaan.
   * Maak een `System.IO.FileStream`-object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het invoerbestand en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van het object `System.IO.FileStream` wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de eigenschap `System.IO.FileStream` van het object `Length` op te halen.
   * Vul de bytearray met streamgegevens door de methode `Read` van het object `System.IO.FileStream` aan te roepen. Geef de bytearray, de startpositie en de streamlengte door om te lezen.
   * Vul het `BLOB`-object door het `MTOM`-veld toe te wijzen met de inhoud van de bytearray.
   * Maak een `MyMapOf_xsd_string_To_xsd_anyType`-object. Dit verzamelingsobject wordt gebruikt voor het opslaan van invoerbestanden die nodig zijn om een samengesteld XDP-document te maken.
   * Maak voor elk invoerbestand een `MyMapOf_xsd_string_To_xsd_anyType_Item`-object.
   * Wijs een tekenreekswaarde toe die de toetsnaam vertegenwoordigt aan het veld `key` van het `MyMapOf_xsd_string_To_xsd_anyType_Item`-object. Deze waarde moet overeenkomen met de waarde van het element dat is opgegeven in het DDX-document. (Voer deze taak uit voor elk invoer-XDP-bestand.)
   * Wijs het `BLOB`-object toe dat het invoerbestand opslaat in het veld `MyMapOf_xsd_string_To_xsd_anyType_Item` van het `value`-object. (Voer deze taak uit voor elk invoer-XDP-bestand.)
   * Voeg het object `MyMapOf_xsd_string_To_xsd_anyType_Item` toe aan het object `MyMapOf_xsd_string_To_xsd_anyType`. Roep de methode `MyMapOf_xsd_string_To_xsd_anyType` van het object `Add` aan en geef het object `MyMapOf_xsd_string_To_xsd_anyType` door. (Voer deze taak uit voor elk invoer-XDP-document.)

1. Stel runtime-opties in.

   * Maak een `AssemblerOptionSpec`-object dat uitvoeringsopties opslaat met de constructor ervan.
   * Stel runtime-opties in om aan uw bedrijfsvereisten te voldoen door een waarde toe te wijzen aan een gegevenslid dat tot het object `AssemblerOptionSpec` behoort. Bijvoorbeeld, om de dienst van de Assembler op te dragen om een baan te blijven verwerken wanneer een fout voorkomt, wijs `false` aan `AssemblerOptionSpec` het gegevenslid van `failOnError` van het voorwerp toe.

1. Stel de meerdere XDP-documenten samen.

   Roep de methode `invokeDDX` van het object `AssemblerServiceClient` aan en geef de volgende waarden door:

   * Een `BLOB`-object dat het DDX-document vertegenwoordigt
   * Het `MyMapOf_xsd_string_To_xsd_anyType`-object dat de vereiste bestanden bevat
   * Een `AssemblerOptionSpec`-object dat uitvoeringsopties opgeeft

   De methode `invokeDDX` retourneert een `AssemblerResult`-object dat de resultaten van de taak en eventuele uitzonderingen bevat die zich hebben voorgedaan.

1. Haal het samengevoegde XDP-document op.

   Voer de volgende handelingen uit om het nieuwe XDP-document te verkrijgen:

   * Open het veld `AssemblerResult` van het object `documents`. Dit is een `Map`-object dat de resulterende PDF-documenten bevat.
   * Doorloop het object `Map` om elk resulterend document te verkrijgen. Vervolgens cast u `value` van dat arraylid naar een `BLOB`.
   * Pak de binaire gegevens die het PDF-document vertegenwoordigen uit door de eigenschap `MTOM` van het object `BLOB` te openen. Hiermee wordt een array met bytes geretourneerd die u naar een XDP-bestand kunt schrijven.

**Zie ook**

[Meerdere XDP-](assembling-multiple-xdp-fragments.md#assembling-multiple-xdp-fragments)
[fragmenten samenstellenAEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)