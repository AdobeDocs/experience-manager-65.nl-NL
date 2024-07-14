---
title: Meerdere XDP-fragmenten samenstellen
description: U kunt meerdere XDP-fragmenten samenvoegen in één XDP-document met de Java API en Web Service API.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
docset: aem65
role: Developer
exl-id: 54d98c69-2b2e-46cb-9f6a-7e9bdbe5c378
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Document Services
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '1859'
ht-degree: 0%

---

# Meerdere XDP-fragmenten samenstellen{#assembling-multiple-xdp-fragments}

U kunt meerdere XDP-fragmenten samenvoegen tot één XDP-document. Neem bijvoorbeeld XDP-fragmenten waarin elk XDP-bestand een of meer subformulieren bevat die worden gebruikt om een gezondheidsformulier te maken. De volgende illustratie toont de overzicht mening (vertegenwoordigt het bestand tuc018_template_flowed.xdp dat in *wordt gebruikt die veelvoudige fragmenten samenbrengt XDP* snel begin):

![ am_am_forma ](assets/am_am_forma.png)

De volgende illustratie toont de patiëntsectie (vertegenwoordigt het bestand tuc018_contact.xdp dat in *wordt gebruikt die veelvoudige fragmenten samenbrengt XDP* snel begin):

![ am_am_formb ](assets/am_am_formb.png)

De volgende illustratie toont de sectie van de patiëntgezondheid (vertegenwoordigt het bestand tuc018_patient.xdp dat in *wordt gebruikt die veelvoudige fragmenten samenbrengt XDP* snel begin):

![ am_am_formc ](assets/am_am_formc.png)

Dit fragment bevat twee subforms genoemd *subPatientphysical* en *subPatientHealth*. Beide subformulieren worden vermeld in het DDX-document dat wordt doorgegeven aan de Assembler-service. Met de Assembler-service kunt u al deze XDP-fragmenten combineren in één XDP-document, zoals in de volgende afbeelding wordt getoond.

![ am_am_formd ](assets/am_am_formd.png)

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

Het DDX-document bevat een XDP `result` -tag met de naam van het resultaat. In deze situatie is de waarde `tuc018result.xdp` . Naar deze waarde wordt verwezen in de toepassingslogica die wordt gebruikt om het XDP-document op te halen nadat de Assembler-service het resultaat heeft geretourneerd. Neem bijvoorbeeld de volgende Java-toepassingslogica die wordt gebruikt om het geassembleerde XDP-document op te halen (de waarde is vet):

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

Met de tag `XDP source` wordt het XDP-bestand opgegeven dat een volledig XDP-document vertegenwoordigt dat kan worden gebruikt als container voor het toevoegen van XDP-fragmenten of als een van de verschillende documenten die op volgorde worden toegevoegd. In deze situatie, wordt het XDP document gebruikt slechts als container (de eerste illustratie die in *wordt getoond die Veelvoudige XDP Fragments* samenstellen). De andere XDP-bestanden worden dus in de XDP-container geplaatst.

Voor elk subformulier kunt u een `XDPContent` -element toevoegen (dit element is optioneel). In het bovenstaande voorbeeld zijn er drie subformulieren: `subPatientContact`, `subPatientPhysical` en `subPatientHealth` . Zowel het subformulier `subPatientPhysical` als het subformulier `subPatientHealth` bevinden zich in hetzelfde XDP-bestand, tuc018_patiënt.xdp. Het fragmentelement geeft de naam van het subformulier op, zoals gedefinieerd in Designer.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Assembler, zie [ Verwijzing van de Diensten voor AEM Forms ](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Voor meer informatie over een document DDX, zie [ de Dienst van de Assembler en de Verwijzing DDX ](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Overzicht van de stappen {#summary-of-steps}

Voer de volgende taken uit om meerdere XDP-fragmenten samen te stellen:

1. Inclusief projectbestanden.
1. Maak een PDF Assembler-client.
1. Verwijs naar een bestaand DDX-document.
1. Verwijs naar de XDP-documenten.
1. Stel runtime-opties in.
1. Stel de meerdere XDP-documenten samen.
1. Haal het samengevoegde XDP-document op.

**omvat projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-assembler-client.jar
* adobe-utilities.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)

**creeer een cliënt van de Assembler van de PDF**

Alvorens u programmatically een verrichting van de Assembler kunt uitvoeren, creeer een de dienstcliënt van de Assembler.

**Verwijzing een bestaand document DDX**

Er moet naar een DDX-document worden verwezen om meerdere XDP-documenten samen te stellen. Dit DDX-document moet `XDP result` -, `XDP source` - en `XDPContent` -elementen bevatten.

**Verwijzing de XDP documenten**

Als u meerdere XDP-documenten wilt samenstellen, verwijst u naar alle XDP-bestanden die worden gebruikt om het resultaat-XDP-document samen te stellen. Controleer of de naam van het subformulier in het XDP-document waarnaar wordt verwezen door het kenmerk `source` , is opgegeven in het kenmerk `fragment` . Een subformulier wordt gedefinieerd in Designer. Neem bijvoorbeeld de volgende XML.

```xml
 <XDPContent insertionPoint="ddx_fragment" source="tuc018_contact.xdp" fragment="subPatientContact" required="false"/>
```

Subvorm genoemd *subPatientContact* moet in het XDP dossier genoemd *zijn tuc018_contact.xdp*.

**vastgestelde runtime opties**

U kunt runtime opties plaatsen die het gedrag van de dienst van de Assembler controleren terwijl het een baan uitvoert. U kunt bijvoorbeeld een optie instellen die de Assembler-service de opdracht geeft door te gaan met het verwerken van een taak als er een fout optreedt.

**assembleer de veelvoudige XDP documenten**

Als u meerdere XDP-bestanden wilt samenstellen, roept u de bewerking `invokeDDX` aan. De dienst van de Assembler keert het geassembleerde XDP document binnen een inzamelingsvoorwerp terug.

**wint het geassembleerde XDP document** terug

Een samengesteld XDP-document wordt geretourneerd binnen een verzamelingsobject. Doorloop het verzamelingsobject en sla het XDP-document op als een XDP-bestand. U kunt het XDP-document ook doorgeven aan een andere AEM Forms-service, zoals Output.

**zie ook**

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

   * Maak een `ServiceClientFactory` -object dat verbindingseigenschappen bevat.
   * Maak een `AssemblerServiceClient` -object door de constructor ervan te gebruiken en het `ServiceClientFactory` -object door te geven.

1. Verwijs naar een bestaand DDX-document.

   * Maak een `java.io.FileInputStream` -object dat het DDX-document vertegenwoordigt door de constructor ervan te gebruiken en een tekenreekswaarde door te geven die de locatie van het DDX-bestand aangeeft.
   * Maak een `com.adobe.idp.Document` -object door de constructor ervan te gebruiken en het `java.io.FileInputStream` -object door te geven.

1. Verwijs naar de XDP-documenten.

   * Maak een `java.util.Map` -object dat wordt gebruikt om invoer-XDP-documenten op te slaan met behulp van een `HashMap` -constructor.
   * Maak een object `com.adobe.idp.Document` en geef het object `java.io.FileInputStream` door dat het invoer-XDP-bestand bevat (herhaal deze taak voor elk XDP-bestand).
   * Voeg een item aan het object `java.util.Map` toe door de methode `put` ervan aan te roepen en de volgende argumenten door te geven:

      * Een tekenreekswaarde die de sleutelnaam vertegenwoordigt. Deze waarde moet overeenkomen met de elementwaarde `source` die is opgegeven in het DDX-document (herhaal deze taak voor elk XDP-bestand).
      * Een `com.adobe.idp.Document` -object dat het XDP-document bevat dat overeenkomt met het `source` -element (herhaal deze taak voor elk XDP-bestand).

1. Stel de runtime-opties in.

   * Maak een `AssemblerOptionSpec` -object dat uitvoeringsopties opslaat met behulp van de bijbehorende constructor.
   * Stel runtime-opties in om aan uw bedrijfsvereisten te voldoen door een methode aan te roepen die tot het `AssemblerOptionSpec` -object behoort. Als u bijvoorbeeld wilt dat de Assembler-service een taak blijft verwerken wanneer een fout optreedt, roept u de methode `setFailOnError` van het object `AssemblerOptionSpec` aan en geeft u deze door `false` .

1. Stel de meerdere XDP-documenten samen.

   Roep de methode `invokeDDX` van het object `AssemblerServiceClient` aan en geef de volgende vereiste waarden door:

   * Een `com.adobe.idp.Document` -object dat het te gebruiken DDX-document vertegenwoordigt
   * Een `java.util.Map` -object dat de invoer-XDP-bestanden bevat
   * Een `com.adobe.livecycle.assembler.client.AssemblerOptionSpec` -object dat de runtime-opties opgeeft, inclusief het standaardfont en het logniveau van de taak

   De methode `invokeDDX` retourneert een `com.adobe.livecycle.assembler.client.AssemblerResult` -object dat het geassembleerde XDP-document bevat.

1. Haal het samengevoegde XDP-document op.

   Voer de volgende handelingen uit om het samengevoegde XDP-document te verkrijgen:

   * Roep de methode `getDocuments` van het object `AssemblerResult` aan. Deze methode retourneert een `java.util.Map` -object.
   * Doorloop het `java.util.Map` -object totdat u het resulterende `com.adobe.idp.Document` -object vindt.
   * Roep de methode `copyToFile` van het `com.adobe.idp.Document` -object aan om het samengevoegde XDP-document te extraheren.

**zie ook**

[ samenstellend Veelvoudige XDP Fragments ](assembling-multiple-xdp-fragments.md#assembling-multiple-xdp-fragments)
[ Snel Begin (SOAP wijze): Het samenbrengen van veelvoudige fragmenten XDP gebruikend Java API ](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-assembling-multiple-xdp-fragments-using-the-java-api)
[ Met inbegrip van de bibliotheekdossiers van AEM Forms Java ](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)
[ Plaatsende verbindingseigenschappen ](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Meerdere XDP-fragmenten samenstellen met de webservice-API {#assemble-multiple-xdp-fragments-using-the-web-service-api}

U kunt meerdere XDP-fragmenten samenstellen met behulp van de API (webservice) van de Assembler Service:

1. Inclusief projectbestanden.

   Creeer een Microsoft .NET project dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt wanneer het plaatsen van een de dienstverwijzing:

   ```java
    https://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1.
   ```

   >[!NOTE]
   >
   >Vervang `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een PDF Assembler-client.

   * Maak een `AssemblerServiceClient` -object met de standaardconstructor.
   * Maak een `AssemblerServiceClient.Endpoint.Address` -object met de `System.ServiceModel.EndpointAddress` -constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service, zoals `https://localhost:8080/soap/services/AssemblerService?blob=mtom` . U hoeft het attribuut `lc_version` niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.
   * Maak een `System.ServiceModel.BasicHttpBinding` -object door de waarde van het `AssemblerServiceClient.Endpoint.Binding` -veld op te halen. De geretourneerde waarde wordt gecast naar `BasicHttpBinding` .
   * Stel het veld `MessageEncoding` van het `System.ServiceModel.BasicHttpBinding` -object in op `WSMessageEncoding.Mtom` . Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld `AssemblerServiceClient.ClientCredentials.UserName.UserName` toe.
      * Wijs de overeenkomstige wachtwoordwaarde aan het `AssemblerServiceClient.ClientCredentials.UserName.Password` gebied toe.
      * Wijs de `HttpClientCredentialType.Basic` constante waarde aan het `BasicHttpBindingSecurity.Transport.ClientCredentialType` gebied toe.
      * Wijs de `BasicHttpSecurityMode.TransportCredentialOnly` constante waarde aan het `BasicHttpBindingSecurity.Security.Mode` gebied toe.

1. Verwijs naar een bestaand DDX-document.

   * Maak een `BLOB` -object met behulp van de constructor. Het `BLOB` -object wordt gebruikt om het DDX-document op te slaan.
   * Maak een `System.IO.FileStream` -object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het DDX-document en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van het object `System.IO.FileStream` wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de eigenschap `Length` van het object `System.IO.FileStream` op te halen.
   * Vul de bytearray met streamgegevens door de methode `Read` van het object `System.IO.FileStream` aan te roepen. Geef de bytearray, de startpositie en de streamlengte door om te lezen.
   * Vul het object `BLOB` door de eigenschap `MTOM` ervan toe te wijzen met de inhoud van de bytearray.

1. Verwijs naar de XDP-documenten.

   * Maak voor elk invoer-XDP-bestand een `BLOB` -object met behulp van de constructor. Het `BLOB` -object wordt gebruikt om het invoerbestand op te slaan.
   * Maak een `System.IO.FileStream` -object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het invoerbestand en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van het object `System.IO.FileStream` wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de eigenschap `Length` van het object `System.IO.FileStream` op te halen.
   * Vul de bytearray met streamgegevens door de methode `Read` van het object `System.IO.FileStream` aan te roepen. Geef de bytearray, de startpositie en de streamlengte door om te lezen.
   * Vul het `BLOB` -object door het `MTOM` -veld ervan toe te wijzen met de inhoud van de bytearray.
   * Maak een `MyMapOf_xsd_string_To_xsd_anyType` -object. Dit verzamelingsobject wordt gebruikt voor het opslaan van invoerbestanden die nodig zijn om een samengesteld XDP-document te maken.
   * Maak voor elk invoerbestand een `MyMapOf_xsd_string_To_xsd_anyType_Item` -object.
   * Wijs een tekenreekswaarde toe die de sleutelnaam vertegenwoordigt aan het veld `key` van het `MyMapOf_xsd_string_To_xsd_anyType_Item` -object. Deze waarde moet overeenkomen met de waarde van het element dat is opgegeven in het DDX-document. (Voer deze taak uit voor elk invoer-XDP-bestand.)
   * Wijs het `BLOB` -object toe dat het invoerbestand opslaat in het veld `MyMapOf_xsd_string_To_xsd_anyType_Item` Object `value` . (Voer deze taak uit voor elk invoer-XDP-bestand.)
   * Voeg het object `MyMapOf_xsd_string_To_xsd_anyType_Item` toe aan het object `MyMapOf_xsd_string_To_xsd_anyType` . Roep de methode `Add` van het object `MyMapOf_xsd_string_To_xsd_anyType` aan en geef het object `MyMapOf_xsd_string_To_xsd_anyType` door. (Voer deze taak uit voor elk invoer-XDP-document.)

1. Stel runtime-opties in.

   * Maak een `AssemblerOptionSpec` -object dat uitvoeringsopties opslaat met behulp van de bijbehorende constructor.
   * Stel runtime-opties in om aan uw bedrijfsvereisten te voldoen door een waarde toe te wijzen aan een gegevenslid dat tot het `AssemblerOptionSpec` -object behoort. Als u bijvoorbeeld de Assembler-service wilt instrueren een taak te blijven verwerken wanneer een fout optreedt, wijst u `false` toe aan het gegevenslid van het `AssemblerOptionSpec` object `failOnError` .

1. Stel de meerdere XDP-documenten samen.

   Roep de methode `invokeDDX` van het object `AssemblerServiceClient` aan en geef de volgende waarden door:

   * Een `BLOB` -object dat het DDX-document vertegenwoordigt
   * Het `MyMapOf_xsd_string_To_xsd_anyType` -object dat de vereiste bestanden bevat
   * Een `AssemblerOptionSpec` -object dat uitvoeringsopties opgeeft

   De methode `invokeDDX` retourneert een `AssemblerResult` -object dat de resultaten van de taak en eventuele uitzonderingen bevat.

1. Haal het samengevoegde XDP-document op.

   Voer de volgende handelingen uit om het nieuwe XDP-document te verkrijgen:

   * Open het veld `documents` van het `AssemblerResult` -object (een `Map` -object dat de resulterende PDF-documenten bevat).
   * Doorloop het `Map` -object om elk resulterend document te verkrijgen. Vervolgens cast u het element `value` van dat arraylid naar een `BLOB` .
   * Haal de binaire gegevens die het PDF-document vertegenwoordigen op door de eigenschap `MTOM` van het object `BLOB` te openen. Hiermee wordt een array met bytes geretourneerd die u naar een XDP-bestand kunt schrijven.

**zie ook**

[ samenstellend Veelvoudige XDP Fragments ](assembling-multiple-xdp-fragments.md#assembling-multiple-xdp-fragments)
[ het Aanhalen van AEM Forms die MTOM ](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom) gebruikt
