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
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1815'
ht-degree: 0%

---

# PDF-Portfolio&#39;s samenstellen {#assembling-pdf-portfolios}

**Voorbeelden en voorbeelden in dit document gelden alleen voor AEM Forms in JEE-omgeving.**

U kunt een PDF-Portfolio samenstellen met de API voor Java samenstellen en webservices. In een portfolio kunnen diverse typen documenten worden gecombineerd, zoals tekstbestanden, afbeeldingsbestanden (bijvoorbeeld een JPEG-bestand) en PDF-documenten. De indeling van het portfolio kan worden ingesteld op verschillende stijlen, zoals de *Raster met voorvertoning* de *Op een afbeelding* lay-out of even *Draaien*.

De volgende afbeelding is een schermafbeelding van een portfolio met *Op een afbeelding* stijllayout.

![ap_ap_portfolio](assets/ap_ap_portfolio.png)

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

Het DXX-document moet een `Portfolio` tag met een genest `Navigator` -tag. De tag noteren `<Resource name="navigator/image.xxx" source="myImage.png"/>` is alleen nodig als `myNavigator` wordt toegewezen als de lay-outnavigator onImage: `AdobeOnImage.nav`. Met deze tag kan de Assembler-service de afbeelding selecteren die u wilt gebruiken als de portfolioachtergrond. Inclusief `PackageFiles` en `File` -tags om de bestandsnaam en het MIME-type van het pakketbestand te definiëren.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Assembler, zie [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Voor meer informatie over een DDX-document raadpleegt u [De Verwijzing van de AssemblerDienst en DDX](https://www.adobe.com/go/learn_aemforms_ddx_63).

## Overzicht van de stappen {#summary-of-steps}

Voer de volgende taken uit om een PDF-Portfolio te maken:

1. Inclusief projectbestanden.
1. Maak een PDF Assembler-client.
1. Verwijs naar een bestaand DDX-document.
1. Verwijs naar de vereiste documenten.
1. Stel runtime-opties in.
1. De portfolio samenstellen.
1. Sla het samengevoegde portfolio op.

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

Er moet naar een DDX-document worden verwezen om een PDF-Portfolio samen te stellen. Dit DDX-document moet de `Portfolio`, `Navigator` en `PackageFiles` elementen.

**Verwijzing naar de vereiste documenten**

Als u een PDF-Portfolio wilt samenstellen, verwijst u naar alle bestanden die de samen te stellen documenten vertegenwoordigen. Geef bijvoorbeeld alle afbeeldingsbestanden die in het DDX-document zijn opgegeven, door aan de Assembler-service. U ziet dat naar deze bestanden wordt verwezen in het DDX-document dat in deze sectie is opgegeven: *myImage.png* en *saint_bernard.jpg*.

Wanneer het assembleren van een Portfolio van PDF, geef een NAV- dossier (een navigatordossier) tot de dienst van de Assembler over. Het NAV-bestand dat u doorgeeft aan de Assembler-service, is afhankelijk van het type PDF-Portfolio dat u wilt maken. Als u bijvoorbeeld een *Op een afbeelding* geeft u de indeling door aan het bestand AdobeOnImage.nav. U kunt NAV-bestanden zoeken in de volgende map:

`<Install folder>\Acrobat 9.0\Acrobat\Navigators`

Kopieer het NAV-bestand uit de installatiemap van Acrobat 9 (of hoger). Plaats het NAV-bestand op een locatie waar uw clienttoepassing het kan openen. Alle dossiers worden overgegaan tot de dienst van de Assembler binnen een de inzamelingsvoorwerp van de Kaart.

>[!NOTE]
>
>De snelle start die bij het samenstellen van PDF-Portfolio&#39;s hoort, gebruikt AdobeOnImage.nav.

**Uitvoeringsopties instellen**

U kunt runtime opties plaatsen die het gedrag van de dienst van de Assembler controleren terwijl het een baan uitvoert. U kunt bijvoorbeeld een optie instellen die de Assembler-service de opdracht geeft door te gaan met het verwerken van een taak als er een fout optreedt.

**Het portfolio samenstellen**

Als u een PDF-Portfolio wilt samenstellen, roept u de `invokeDDX` -bewerking. De dienst van de Assembler keert het Portfolio van de PDF binnen een inzamelingsvoorwerp terug.

**De geassembleerde portfolio opslaan**

Een PDF-Portfolio wordt geretourneerd binnen een verzamelingsobject. Doorloop het verzamelingsobject en sla het PDF-Portfolio op als een PDF-bestand.

**Zie ook**

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

   * Een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Een `AssemblerServiceClient` object door de constructor ervan te gebruiken en de `ServiceClientFactory` object.

1. Verwijs naar een bestaand DDX-document.

   * Een `java.io.FileInputStream` een object dat het DDX-document vertegenwoordigt door de constructor ervan te gebruiken en een tekenreekswaarde door te geven die de locatie van het DDX-bestand aangeeft.
   * Een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en de `java.io.FileInputStream` object.

1. Verwijs naar de vereiste documenten.

   * Een `java.util.Map` object dat wordt gebruikt voor het opslaan van PDF-invoerdocumenten met behulp van een `HashMap` constructor.
   * Een `java.io.FileInputStream` object met behulp van de constructor. Geef de locatie van het vereiste NAV-bestand door (herhaal deze taak voor elk bestand dat is vereist om een portfolio te maken).
   * Een `com.adobe.idp.Document` en geeft het `java.io.FileInputStream` -object dat het NAV-bestand bevat (herhaal deze taak voor elk bestand dat is vereist om een portfolio te maken).
   * Een item toevoegen aan de `java.util.Map` object aanroepen `put` en het doorgeven van de volgende argumenten:

      * Een tekenreekswaarde die de sleutelnaam vertegenwoordigt. Deze waarde moet overeenkomen met de waarde van het bronelement dat is opgegeven in het DDX-document. (Herhaal deze taak voor elk bestand dat vereist is om een portfolio te maken).
      * A `com.adobe.idp.Document` object dat het PDF-document bevat. (Herhaal deze taak voor elk bestand dat vereist is om een portfolio te maken).

1. Stel runtime-opties in.

   * Een `AssemblerOptionSpec` object dat uitvoeringsopties opslaat met de constructor ervan.
   * Stel runtime-opties in om aan uw bedrijfsvereisten te voldoen door een methode aan te roepen die tot de `AssemblerOptionSpec` object. Bijvoorbeeld, om de dienst van de Assembler op te dragen om een baan te blijven verwerken wanneer een fout voorkomt, haalt het `AssemblerOptionSpec` object `setFailOnError` methode en doorgeven `false`.

1. De portfolio samenstellen.

   De `AssemblerServiceClient` object `invokeDDX` en geeft de volgende vereiste waarden door:

   * A `com.adobe.idp.Document` object dat staat voor het te gebruiken DDX-document
   * A `java.util.Map` -object dat de bestanden bevat die vereist zijn om een PDF-Portfolio te maken.
   * A `com.adobe.livecycle.assembler.client.AssemblerOptionSpec` object dat de runtime-opties opgeeft, inclusief het standaardfont en het taaklogniveau

   De `invokeDDX` methode retourneert een `com.adobe.livecycle.assembler.client.AssemblerResult` object dat het geassembleerde PDF-Portfolio en eventuele uitzonderingen bevat die zich hebben voorgedaan.

1. Sla het samengevoegde portfolio op.

   Voer de volgende handelingen uit om het PDF-Portfolio te verkrijgen:

   * De `AssemblerResult` object `getDocuments` methode. Deze methode retourneert een `java.util.Map` object.
   * Doorlopen `java.util.Map` object tot u het resultaat hebt gevonden `com.adobe.idp.Document` object.
   * De `com.adobe.idp.Document` object `copyToFile` methode om het PDF-Portfolio te extraheren.

**Zie ook**

[Snel starten (SOAP-modus): PDF-Portfolio&#39;s samenstellen met de Java API](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-assembling-pdf-portfolios-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Een PDF-Portfolio samenstellen met de webservice-API {#assemble-a-pdf-portfolio-using-the-web-service-api}

U kunt een PDF-Portfolio samenstellen met behulp van de API (webservice) voor vergaderingsservice:

1. Inclusief projectbestanden.

   Creeer een Microsoft .NET project dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt wanneer het plaatsen van een de dienstverwijzing: `http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1`.

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
   * De bytearray vullen met streamgegevens door de `System.IO.FileStream` object `Read` methode. Geef de bytearray, de startpositie en de streamlengte door om te lezen.
   * Vul de `BLOB` object door het toe te wijzen `MTOM` eigenschap met de inhoud van de bytearray.

1. Verwijs naar de vereiste documenten.

   * Maak voor elk invoerbestand een `BLOB` object met behulp van de constructor. De `BLOB` wordt gebruikt om het invoerbestand op te slaan.
   * Een `System.IO.FileStream` door de constructor aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het invoerbestand en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van de `System.IO.FileStream` object. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` object `Length` eigenschap.
   * De bytearray vullen met streamgegevens door de `System.IO.FileStream` object `Read` methode. Geef de bytearray, de startpositie en de streamlengte door om te lezen.
   * Vul de `BLOB` object door het toe te wijzen `MTOM` veld met de inhoud van de bytearray.
   * Een `MyMapOf_xsd_string_To_xsd_anyType` object. Dit verzamelingsobject wordt gebruikt om invoerbestanden op te slaan die nodig zijn om een PDF-Portfolio te maken.
   * Maak voor elk invoerbestand een `MyMapOf_xsd_string_To_xsd_anyType_Item` object.
   * Wijs een tekenreekswaarde toe die de sleutelnaam vertegenwoordigt aan de `MyMapOf_xsd_string_To_xsd_anyType_Item` object `key` veld. Deze waarde moet overeenkomen met de waarde van het element dat is opgegeven in het DDX-document. (Voer deze taak uit voor elk invoerbestand.)
   * Wijs het `BLOB` object dat het invoerbestand in het `MyMapOf_xsd_string_To_xsd_anyType_Item` object `value` veld. (Voer deze taak uit voor elk invoerdocument van de PDF.)
   * Voeg de `MyMapOf_xsd_string_To_xsd_anyType_Item` aan `MyMapOf_xsd_string_To_xsd_anyType` object. De `MyMapOf_xsd_string_To_xsd_anyType` object `Add` en geeft de `MyMapOf_xsd_string_To_xsd_anyType` object. (Voer deze taak uit voor elk invoerdocument van de PDF.)

1. Stel runtime-opties in.

   * Een `AssemblerOptionSpec` object dat uitvoeringsopties opslaat met de constructor ervan.
   * Stel runtime-opties in om aan uw bedrijfsvereisten te voldoen door een waarde toe te wijzen aan een gegevenslid dat tot de `AssemblerOptionSpec` object. Bijvoorbeeld, om de dienst van de Assembler op te dragen om een baan te blijven verwerken wanneer een fout voorkomt, wijs toe `false` aan de `AssemblerOptionSpec` object `failOnError` lid.

1. De portfolio samenstellen.

   De `AssemblerServiceClient` object `invokeDDX` en geeft de volgende waarden door:

   * A `BLOB` object dat staat voor het DDX-document
   * De `MyMapOf_xsd_string_To_xsd_anyType` object dat de vereiste bestanden bevat
   * An `AssemblerOptionSpec` object dat uitvoeringsopties opgeeft

   De `invokeDDX` methode retourneert een `AssemblerResult` object dat de resultaten van de taak en eventuele uitzonderingen bevat die zijn opgetreden.

1. Sla het samengevoegde portfolio op.

   Voer de volgende handelingen uit om het nieuwe PDF-Portfolio te verkrijgen:

   * Toegang krijgen tot de `AssemblerResult` object `documents` veld, dat een `Map` -object dat de resulterende PDF-documenten bevat.
   * Doorlopen `Map` om elk resulterend document te verkrijgen. Dan, giet dat serielid `value` een `BLOB`.
   * Extraheer de binaire gegevens die het document van de PDF door tot zijn toegang te hebben vertegenwoordigen `BLOB` object `MTOM` eigenschap. Hiermee wordt een array met bytes geretourneerd die u naar een PDF-bestand kunt schrijven.

**Zie ook**

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)
