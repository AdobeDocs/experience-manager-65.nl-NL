---
title: PDF-Portfolio's samenstellen
description: U kunt een PDF-portfolio samenstellen om verschillende typen documenten te combineren, zoals tekstbestanden, afbeeldingsbestanden en PDF-documenten. U kunt een PDF-portfolio samenstellen met een Java API en een webservice-API.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
exl-id: d2bd7c3e-4f75-4234-a7aa-ee8524430493
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Document Services
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '1815'
ht-degree: 0%

---

# PDF-Portfolio&#39;s samenstellen {#assembling-pdf-portfolios}

**de Steekproeven en de voorbeelden in dit document zijn slechts voor AEM Forms op milieu JEE.**

U kunt een PDF-Portfolio samenstellen met de API voor Java samenstellen en webservices. In een portfolio kunnen diverse typen documenten worden gecombineerd, zoals tekstbestanden, afbeeldingsbestanden (bijvoorbeeld een JPEG-bestand) en PDF-documenten. De lay-out van de portefeuille kan aan verschillende stijlen zoals het *Net met Voorproef* worden geplaatst, *op een lay-out van het Beeld* of zelfs *Draai*.

De volgende illustratie is een het schermschot van een portefeuille met *op een lay-out van de de stijlstijl van het Beeld*.

![&#x200B; ap_ap_portfolio &#x200B;](assets/ap_ap_portfolio.png)

Het maken van een PDF-Portfolio is een papierloos alternatief voor het doorgeven van een verzameling documenten. Met AEM Forms kunt u portfolio&#39;s maken door de Assembler-service aan te roepen met een gestructureerd DDX-document. Het volgende DDX-document is een voorbeeld van een DDX-document dat een PDF-Portfolio maakt.

```xml
 <DDX xmlns="https://ns.adobe.com/DDX/1.0/">
     <PDF result="portfolio1.pdf">
         <Portfolio>
             <Navigator source="myNavigator">
                 <Resource name="navigator/image.xxx" source="myImage.png"/>
             </Navigator>
         </Portfolio>
         <PackageFiles source="dog1"  >
              <FieldData name="X">72</FieldData>
             <FieldData name="Y">72</FieldData>
             <File filename="saint_bernard.jpg" mimetype="image/jpeg"/>
         </PackageFiles>
         <PackageFiles source="dog2"  >
             <FieldData name="X">120</FieldData>
             <FieldData name="Y">216</FieldData>
             <File filename="greyhound.pdf"/>
         </PackageFiles>
     </PDF>
 </DDX>
```

Het DXX-document moet een `Portfolio` -tag met een geneste `Navigator` -tag bevatten. Het label `<Resource name="navigator/image.xxx" source="myImage.png"/>` is alleen nodig als `myNavigator` is toegewezen als de onImage-layoutnavigator: `AdobeOnImage.nav` . Met deze tag kan de Assembler-service de afbeelding selecteren die u wilt gebruiken als de portfolioachtergrond. Neem `PackageFiles` - en `File` -tags op om de bestandsnaam en het MIME-type van het pakketbestand te definiëren.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Assembler, zie [&#x200B; Verwijzing van de Diensten voor AEM Forms &#x200B;](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Voor meer informatie over een document DDX, zie [&#x200B; de Dienst van de Assembler en de Verwijzing DDX &#x200B;](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Overzicht van de stappen {#summary-of-steps}

Voer de volgende taken uit om een PDF-Portfolio te maken:

1. Inclusief projectbestanden.
1. Maak een PDF Assembler-client.
1. Verwijs naar een bestaand DDX-document.
1. Verwijs naar de vereiste documenten.
1. Stel runtime-opties in.
1. De portfolio samenstellen.
1. Sla het samengevoegde portfolio op.

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

Er moet naar een DDX-document worden verwezen om een PDF-Portfolio samen te stellen. Dit DDX-document moet de elementen `Portfolio` , `Navigator` en `PackageFiles` bevatten.

**Verwijzing de vereiste documenten**

Als u een PDF-Portfolio wilt samenstellen, verwijst u naar alle bestanden die de samen te stellen documenten vertegenwoordigen. Geef bijvoorbeeld alle afbeeldingsbestanden die in het DDX-document zijn opgegeven, door aan de Assembler-service. Bericht dat deze dossiers in het Ddx- document van verwijzingen worden voorzien dat in deze sectie wordt gespecificeerd: *myImage.png* en *saint_bernard.jpg*.

Wanneer het assembleren van een Portfolio van PDF, geef een NAV- dossier (een navigatordossier) tot de dienst van de Assembler over. Het NAV-bestand dat u doorgeeft aan de Assembler-service, is afhankelijk van het type PDF-Portfolio dat u wilt maken. Bijvoorbeeld, om een *op een lay-out van het Beeld* tot stand te brengen, ga het dossier over AdobeOnImage.nav. U kunt NAV-bestanden zoeken in de volgende map:

`<Install folder>\Acrobat 9.0\Acrobat\Navigators`

Kopieer het NAV-bestand uit de installatiemap van Acrobat 9 (of hoger). Plaats het NAV-bestand op een locatie waar uw clienttoepassing het kan openen. Alle dossiers worden overgegaan tot de dienst van de Assembler binnen een de inzamelingsvoorwerp van de Kaart.

>[!NOTE]
>
>De snelle start die bij het samenstellen van PDF-Portfolio&#39;s hoort, gebruikt AdobeOnImage.nav.

**vastgestelde runtime opties**

U kunt runtime opties plaatsen die het gedrag van de dienst van de Assembler controleren terwijl het een baan uitvoert. U kunt bijvoorbeeld een optie instellen die de Assembler-service de opdracht geeft door te gaan met het verwerken van een taak als er een fout optreedt.

**assembleer de portefeuille**

Als u een PDF-Portfolio wilt samenstellen, roept u de bewerking `invokeDDX` aan. De dienst van de Assembler keert het Portfolio van de PDF binnen een inzamelingsvoorwerp terug.

**sparen de samengestelde portefeuille**

Een PDF-Portfolio wordt geretourneerd binnen een verzamelingsobject. Doorloop het verzamelingsobject en sla het PDF-Portfolio op als een PDF-bestand.

**zie ook**

[Een PDF-Portfolio samenstellen met de Java API](#assemble-a-pdf-portfolio-using-the-java-api)

[Een PDF-Portfolio samenstellen met de webservice-API](#assemble-a-pdf-portfolio-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[PDF-documenten programmatisch samenstellen](/help/forms/developing/programmatically-assembling-pdf-documents.md)

## Een PDF-Portfolio samenstellen met de Java API {#assemble-a-pdf-portfolio-using-the-java-api}

U kunt een PDF-Portfolio samenstellen met de API (Java) voor de Assembler-service:

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-assembler-client.jar, op in het klassenpad van uw Java-project.

1. Maak een PDF Assembler-client.

   * Maak een `ServiceClientFactory` -object dat verbindingseigenschappen bevat.
   * Maak een `AssemblerServiceClient` -object door de constructor ervan te gebruiken en het `ServiceClientFactory` -object door te geven.

1. Verwijs naar een bestaand DDX-document.

   * Maak een `java.io.FileInputStream` -object dat het DDX-document vertegenwoordigt door de constructor ervan te gebruiken en een tekenreekswaarde door te geven die de locatie van het DDX-bestand aangeeft.
   * Maak een `com.adobe.idp.Document` -object door de constructor ervan te gebruiken en het `java.io.FileInputStream` -object door te geven.

1. Verwijs naar de vereiste documenten.

   * Maak een `java.util.Map` -object dat wordt gebruikt om invoerdocumenten van de PDF op te slaan met behulp van een `HashMap` -constructor.
   * Maak een `java.io.FileInputStream` -object met behulp van de constructor. Geef de locatie van het vereiste NAV-bestand door (herhaal deze taak voor elk bestand dat is vereist om een portfolio te maken).
   * Maak een `com.adobe.idp.Document` -object en geef het `java.io.FileInputStream` -object door dat het NAV-bestand bevat (herhaal deze taak voor elk bestand dat nodig is om een portfolio te maken).
   * Voeg een item aan het object `java.util.Map` toe door de methode `put` ervan aan te roepen en de volgende argumenten door te geven:

      * Een tekenreekswaarde die de sleutelnaam vertegenwoordigt. Deze waarde moet overeenkomen met de waarde van het bronelement dat is opgegeven in het DDX-document. (Herhaal deze taak voor elk bestand dat vereist is om een portfolio te maken).
      * Een `com.adobe.idp.Document` -object dat het PDF-document bevat. (Herhaal deze taak voor elk bestand dat vereist is om een portfolio te maken).

1. Stel runtime-opties in.

   * Maak een `AssemblerOptionSpec` -object dat uitvoeringsopties opslaat met behulp van de bijbehorende constructor.
   * Stel runtime-opties in om aan uw bedrijfsvereisten te voldoen door een methode aan te roepen die tot het `AssemblerOptionSpec` -object behoort. Als u bijvoorbeeld wilt dat de Assembler-service een taak blijft verwerken wanneer een fout optreedt, roept u de methode `setFailOnError` van het object `AssemblerOptionSpec` aan en geeft u deze door `false` .

1. De portfolio samenstellen.

   Roep de methode `invokeDDX` van het object `AssemblerServiceClient` aan en geef de volgende vereiste waarden door:

   * Een `com.adobe.idp.Document` -object dat het te gebruiken DDX-document vertegenwoordigt
   * Een `java.util.Map` -object dat de bestanden bevat die zijn vereist om een PDF-Portfolio te maken.
   * Een `com.adobe.livecycle.assembler.client.AssemblerOptionSpec` -object dat de runtime-opties opgeeft, inclusief het standaardfont en het taaklogniveau

   De methode `invokeDDX` retourneert een `com.adobe.livecycle.assembler.client.AssemblerResult` -object dat het geassembleerde PDF-Portfolio en eventuele uitzonderingen bevat.

1. Sla het samengevoegde portfolio op.

   Voer de volgende handelingen uit om het PDF-Portfolio te verkrijgen:

   * Roep de methode `getDocuments` van het object `AssemblerResult` aan. Deze methode retourneert een `java.util.Map` -object.
   * Doorloop het `java.util.Map` -object totdat u het resulterende `com.adobe.idp.Document` -object vindt.
   * Roep de methode `copyToFile` van het `com.adobe.idp.Document` -object aan om het PDF-Portfolio te extraheren.

**zie ook**

[Snel starten (SOAP modus): PDF-Portfolio&#39;s samenstellen met de Java API](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-assembling-pdf-portfolios-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Een PDF-Portfolio samenstellen met de webservice-API {#assemble-a-pdf-portfolio-using-the-web-service-api}

U kunt een PDF-Portfolio samenstellen met behulp van de API (webservice) voor vergaderingsservice:

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
   * Maak een `System.IO.FileStream` -object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het DDX-document en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van het object `System.IO.FileStream` wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de eigenschap `Length` van het object `System.IO.FileStream` op te halen.
   * Vul de bytearray met streamgegevens door de methode `Read` van het object `System.IO.FileStream` aan te roepen. Geef de bytearray, de startpositie en de streamlengte door om te lezen.
   * Vul het object `BLOB` door de eigenschap `MTOM` ervan toe te wijzen met de inhoud van de bytearray.

1. Verwijs naar de vereiste documenten.

   * Maak voor elk invoerbestand een `BLOB` -object met behulp van de constructor. Het `BLOB` -object wordt gebruikt om het invoerbestand op te slaan.
   * Maak een `System.IO.FileStream` -object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het invoerbestand en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van het object `System.IO.FileStream` wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de eigenschap `Length` van het object `System.IO.FileStream` op te halen.
   * Vul de bytearray met streamgegevens door de methode `Read` van het object `System.IO.FileStream` aan te roepen. Geef de bytearray, de startpositie en de streamlengte door om te lezen.
   * Vul het `BLOB` -object door het `MTOM` -veld ervan toe te wijzen met de inhoud van de bytearray.
   * Maak een `MyMapOf_xsd_string_To_xsd_anyType` -object. Dit verzamelingsobject wordt gebruikt om invoerbestanden op te slaan die nodig zijn om een PDF-Portfolio te maken.
   * Maak voor elk invoerbestand een `MyMapOf_xsd_string_To_xsd_anyType_Item` -object.
   * Wijs een tekenreekswaarde toe die de sleutelnaam vertegenwoordigt aan het veld `key` van het `MyMapOf_xsd_string_To_xsd_anyType_Item` -object. Deze waarde moet overeenkomen met de waarde van het element dat is opgegeven in het DDX-document. (Voer deze taak uit voor elk invoerbestand.)
   * Wijs het `BLOB` -object toe dat het invoerbestand opslaat in het veld `MyMapOf_xsd_string_To_xsd_anyType_Item` Object `value` . (Voer deze taak uit voor elk invoerdocument van de PDF.)
   * Voeg het object `MyMapOf_xsd_string_To_xsd_anyType_Item` toe aan het object `MyMapOf_xsd_string_To_xsd_anyType` . Roep de methode `Add` van het object `MyMapOf_xsd_string_To_xsd_anyType` aan en geef het object `MyMapOf_xsd_string_To_xsd_anyType` door. (Voer deze taak uit voor elk invoerdocument van de PDF.)

1. Stel runtime-opties in.

   * Maak een `AssemblerOptionSpec` -object dat uitvoeringsopties opslaat met behulp van de bijbehorende constructor.
   * Stel runtime-opties in om aan uw bedrijfsvereisten te voldoen door een waarde toe te wijzen aan een gegevenslid dat tot het `AssemblerOptionSpec` -object behoort. Als u bijvoorbeeld de Assembler-service wilt instrueren een taak te blijven verwerken wanneer een fout optreedt, wijst u `false` toe aan het gegevenslid van het `AssemblerOptionSpec` object `failOnError` .

1. De portfolio samenstellen.

   Roep de methode `invokeDDX` van het object `AssemblerServiceClient` aan en geef de volgende waarden door:

   * Een `BLOB` -object dat het DDX-document vertegenwoordigt
   * Het `MyMapOf_xsd_string_To_xsd_anyType` -object dat de vereiste bestanden bevat
   * Een `AssemblerOptionSpec` -object dat uitvoeringsopties opgeeft

   De methode `invokeDDX` retourneert een `AssemblerResult` -object dat de resultaten van de taak en eventuele uitzonderingen bevat.

1. Sla het samengevoegde portfolio op.

   Voer de volgende handelingen uit om het nieuwe PDF-Portfolio te verkrijgen:

   * Open het veld `documents` van het `AssemblerResult` -object (een `Map` -object dat de resulterende PDF-documenten bevat).
   * Doorloop het `Map` -object om elk resulterend document te verkrijgen. Vervolgens cast u het element `value` van dat arraylid naar een `BLOB` .
   * Haal de binaire gegevens die het PDF-document vertegenwoordigen op door de eigenschap `MTOM` van het object `BLOB` te openen. Hiermee wordt een array met bytes geretourneerd die u naar een PDF-bestand kunt schrijven.

**zie ook**

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)
