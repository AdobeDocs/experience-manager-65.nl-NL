---
title: PDF-portfolio's samenstellen
seo-title: PDF-portfolio's samenstellen
description: 'null'
seo-description: 'null'
uuid: 1778c90b-9d26-466b-a7c7-401d737395e0
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/assembling_pdf_documents
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 023f0d9e-bfde-4879-a839-085fadffb48e
translation-type: tm+mt
source-git-commit: 1343cc33a1e1ce26c0770a3b49317e82353497ab
workflow-type: tm+mt
source-wordcount: '1785'
ht-degree: 0%

---


# PDF-portfolio&#39;s samenstellen {#assembling-pdf-portfolios}

U kunt een PDF-portfolio samenstellen met de API voor het samenstellen van Java en webservices. In een portfolio kunnen diverse typen documenten worden gecombineerd, zoals tekstbestanden, afbeeldingsbestanden (bijvoorbeeld een JPEG-bestand) en PDF-documenten. De indeling van het portfolio kan worden ingesteld op verschillende stijlen, zoals *Raster met voorvertoning*, de indeling *Op afbeelding* of zelfs *Draaien*.

De volgende afbeelding is een schermafbeelding van een portfolio met de stijl *Op afbeelding* .

![ap_ap_portfolio](assets/ap_ap_portfolio.png)

Het maken van een PDF-portfolio is een papierloos alternatief voor het doorgeven van een verzameling documenten. Met behulp van AEM Forms kunt u portfolio&#39;s maken door de Assembler-service aan te roepen met een gestructureerd DDX-document. Het volgende DDX-document is een voorbeeld van een DDX-document waarmee een PDF-portfolio wordt gemaakt.

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

Het DXX-document moet een `Portfolio` tag met een geneste `Navigator` tag bevatten. Let op: de tag `<Resource name="navigator/image.xxx" source="myImage.png"/>` is alleen nodig als `myNavigator` deze is toegewezen als de lay-outnavigator onImage: `AdobeOnImage.nav`. Met deze tag kan de Assembler-service de afbeelding selecteren die u wilt gebruiken als de portfolioachtergrond. Neem tags `PackageFiles` en `File` tags op om de bestandsnaam en het MIME-type van het pakketbestand te definiëren.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Assembler, zie de Verwijzing van de [Diensten voor AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Voor meer informatie over een DX- document, zie de Dienst van de [Assembler en de Verwijzing](https://www.adobe.com/go/learn_aemforms_ddx_63)DDX.

## Overzicht van de stappen {#summary-of-steps}

Voer de volgende taken uit om een PDF-portfolio te maken:

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
* adobe-utilities.jar (vereist als AEM Forms worden geïmplementeerd op JBoss)
* jbossall-client.jar (vereist als AEM Forms worden geïmplementeerd op JBoss)

**Een PDF Assembler-client maken**

Alvorens u programmatically een verrichting van de Assembler kunt uitvoeren, creeer een de dienstcliënt van de Assembler.

**Verwijzen naar een bestaand DDX-document**

Er moet naar een DDX-document worden verwezen om een PDF-portfolio samen te stellen. Dit DDX-document moet de `Portfolio`, `Navigator` en, `PackageFiles` elementen bevatten.

**Verwijzing naar de vereiste documenten**

Als u een PDF-portfolio wilt samenstellen, verwijst u naar alle bestanden die de samen te stellen documenten vertegenwoordigen. Geef bijvoorbeeld alle afbeeldingsbestanden die in het DDX-document zijn opgegeven, door aan de Assembler-service. U ziet dat naar deze bestanden wordt verwezen in het DDX-document dat in deze sectie is opgegeven: *myImage.png* en *saint_bernard.jpg*.

Wanneer u een PDF-portfolio samenstelt, geeft u een NAV-bestand (een navigatorbestand) door aan de Assembler-service. Het NAV-bestand dat u doorgeeft aan de Assembler-service, is afhankelijk van het type PDF-portfolio dat u wilt maken. Als u bijvoorbeeld een indeling *Op afbeelding* wilt maken, geeft u het bestand AdobeOnImage.nav door. U kunt NAV-bestanden zoeken in de volgende map:

`<Install folder>\Acrobat 9.0\Acrobat\Navigators`

Kopieer het NAV-bestand uit de installatiemap van Acrobat 9 (of hoger). Plaats het NAV-bestand op een locatie waar uw clienttoepassing het kan openen. Alle dossiers worden overgegaan tot de dienst van de Assembler binnen een de inzamelingsvoorwerp van de Kaart.

>[!NOTE]
>
>De snelle start die bij het samenstellen van PDF-portfolio&#39;s hoort, is gebaseerd op AdobeOnImage.nav.

**Uitvoeringsopties instellen**

U kunt runtime opties plaatsen die het gedrag van de dienst van de Assembler controleren terwijl het een baan uitvoert. U kunt bijvoorbeeld een optie instellen die de Assembler-service de opdracht geeft door te gaan met het verwerken van een taak als er een fout optreedt.

**Het portfolio samenstellen**

Als u een PDF-portfolio wilt samenstellen, roept u de `invokeDDX` bewerking aan. De service Assembler retourneert de PDF-portfolio in een verzamelingsobject.

**De geassembleerde portfolio opslaan**

Een PDF-portfolio wordt geretourneerd in een verzamelingsobject. Doorloop het verzamelingsobject en sla het PDF-portfolio op als een PDF-bestand.

**Zie ook**

[Een PDF-portfolio samenstellen met de Java API](#assemble-a-pdf-portfolio-using-the-java-api)

[Een PDF-portfolio samenstellen met de API voor webservices](#assemble-a-pdf-portfolio-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[PDF-documenten programmatisch samenstellen](/help/forms/developing/programmatically-assembling-pdf-documents.md)

## Een PDF-portfolio samenstellen met de Java API {#assemble-a-pdf-portfolio-using-the-java-api}

U kunt een PDF-portfolio samenstellen met de API (Java) voor vergaderingsservice:

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-assembler-client.jar, op in het klassenpad van uw Java-project.

1. Maak een PDF Assembler-client.

   * Maak een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Maak een `AssemblerServiceClient` object door de constructor ervan te gebruiken en het `ServiceClientFactory` object door te geven.

1. Verwijs naar een bestaand DDX-document.

   * Maak een `java.io.FileInputStream` object dat het DDX-document vertegenwoordigt door de constructor ervan te gebruiken en een tekenreekswaarde door te geven die de locatie van het DDX-bestand aangeeft.
   * Maak een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en het `java.io.FileInputStream` object door te geven.

1. Verwijs naar de vereiste documenten.

   * Maak een `java.util.Map` object dat wordt gebruikt om invoer-PDF-documenten op te slaan met behulp van een `HashMap` constructor.
   * Maak een `java.io.FileInputStream` object met de constructor ervan. Geef de locatie van het vereiste NAV-bestand door (herhaal deze taak voor elk bestand dat is vereist om een portfolio te maken).
   * Maak een `com.adobe.idp.Document` object en geef het `java.io.FileInputStream` object door dat het NAV-bestand bevat (herhaal deze taak voor elk bestand dat nodig is om een portfolio te maken).
   * Voeg een item aan het `java.util.Map` `put` object toe door de methode ervan aan te roepen en de volgende argumenten door te geven:

      * Een tekenreekswaarde die de sleutelnaam vertegenwoordigt. Deze waarde moet overeenkomen met de waarde van het bronelement dat is opgegeven in het DDX-document. (Herhaal deze taak voor elk bestand dat vereist is om een portfolio te maken).
      * Een `com.adobe.idp.Document` object dat het PDF-document bevat. (Herhaal deze taak voor elk bestand dat vereist is om een portfolio te maken).

1. Stel runtime-opties in.

   * Maak een `AssemblerOptionSpec` object dat uitvoeringsopties opslaat met de constructor ervan.
   * Stel runtime-opties in om aan uw bedrijfsvereisten te voldoen door een methode aan te roepen die tot het `AssemblerOptionSpec` object behoort. Bijvoorbeeld, om de dienst van de Assembler op te dragen om een baan te blijven verwerken wanneer een fout voorkomt, haalt de methode van `AssemblerOptionSpec` objecten aan en gaat over `setFailOnError` `false`.

1. De portfolio samenstellen.

   Roep de `AssemblerServiceClient` methode van het `invokeDDX` object aan en geef de volgende vereiste waarden door:

   * Een `com.adobe.idp.Document` object dat staat voor het te gebruiken DDX-document
   * Een `java.util.Map` object dat de bestanden bevat die zijn vereist om een PDF-portfolio te maken.
   * Een `com.adobe.livecycle.assembler.client.AssemblerOptionSpec` object dat de runtime-opties opgeeft, inclusief het standaardfont en het taaklogniveau

   De `invokeDDX` methode retourneert een `com.adobe.livecycle.assembler.client.AssemblerResult` object dat de geassembleerde PDF-portfolio en eventuele uitzonderingen bevat.

1. Sla het samengevoegde portfolio op.

   Voer de volgende handelingen uit om het PDF-portfolio te verkrijgen:

   * Roep de `AssemblerResult` methode van het `getDocuments` object aan. Deze methode retourneert een `java.util.Map` object.
   * Doorloop het `java.util.Map` object totdat u het resulterende `com.adobe.idp.Document` object vindt.
   * Roep de `com.adobe.idp.Document` methode van het `copyToFile` object aan om het PDF-portfolio te extraheren.

**Zie ook**

[Snel starten (SOAP-modus): PDF-portfolio&#39;s samenstellen met de Java API](/help/forms/developing/assembler-service-java-api-quick.md#quick-start-soap-mode-assembling-pdf-portfolios-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Een PDF-portfolio samenstellen met de API voor webservices {#assemble-a-pdf-portfolio-using-the-web-service-api}

U kunt een PDF-portfolio samenstellen met de API (webservice) voor vergaderingsservice:

1. Inclusief projectbestanden.

   Creeer een project van Microsoft .NET dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt wanneer het plaatsen van een de dienstverwijzing: `http://localhost:8080/soap/services/AssemblerService?WSDL&lc_version=9.0.1`.

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
   * Maak een `System.IO.FileStream` object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het DDX-document en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van het `System.IO.FileStream` object wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` eigenschap van het `Length` object op te halen.
   * Vul de bytearray met streamgegevens door de `System.IO.FileStream` `Read` methode van het object aan te roepen. Geef de bytearray, de startpositie en de streamlengte door om te lezen.
   * Vul het `BLOB` object door de `MTOM` eigenschap ervan toe te wijzen met de inhoud van de bytearray.

1. Verwijs naar de vereiste documenten.

   * Maak voor elk invoerbestand een `BLOB` object met behulp van de constructor ervan. Het `BLOB` object wordt gebruikt om het invoerbestand op te slaan.
   * Maak een `System.IO.FileStream` object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het invoerbestand en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van het `System.IO.FileStream` object wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` eigenschap van het `Length` object op te halen.
   * Vul de bytearray met streamgegevens door de `System.IO.FileStream` `Read` methode van het object aan te roepen. Geef de bytearray, de startpositie en de streamlengte door om te lezen.
   * Vul het `BLOB` object door het `MTOM` veld ervan toe te wijzen met de inhoud van de bytearray.
   * Create a `MyMapOf_xsd_string_To_xsd_anyType` object. Dit verzamelobject wordt gebruikt voor het opslaan van invoerbestanden die nodig zijn om een PDF-portfolio te maken.
   * Maak voor elk invoerbestand een `MyMapOf_xsd_string_To_xsd_anyType_Item` object.
   * Wijs een tekenreekswaarde toe die de sleutelnaam aan het `MyMapOf_xsd_string_To_xsd_anyType_Item` `key` gebied van het voorwerp vertegenwoordigt. Deze waarde moet overeenkomen met de waarde van het element dat is opgegeven in het DDX-document. (Voer deze taak uit voor elk invoerbestand.)
   * Wijs het `BLOB` object dat het invoerbestand opslaat toe aan het `MyMapOf_xsd_string_To_xsd_anyType_Item` veld van het `value` object. (Voer deze taak uit voor elk invoer-PDF-document.)
   * Voeg het `MyMapOf_xsd_string_To_xsd_anyType_Item` object toe aan het `MyMapOf_xsd_string_To_xsd_anyType` object. Roep de `MyMapOf_xsd_string_To_xsd_anyType` methode van het `Add` object aan en geef het `MyMapOf_xsd_string_To_xsd_anyType` object door. (Voer deze taak uit voor elk invoer-PDF-document.)

1. Stel runtime-opties in.

   * Maak een `AssemblerOptionSpec` object dat uitvoeringsopties opslaat met de constructor ervan.
   * Stel runtime-opties in om aan uw bedrijfsvereisten te voldoen door een waarde toe te wijzen aan een gegevenslid dat tot het `AssemblerOptionSpec` object behoort. Bijvoorbeeld, om de dienst van de Assembler op te dragen om een baan te blijven verwerken wanneer een fout voorkomt, wijs `false` aan het de `AssemblerOptionSpec` gegevenslid van het `failOnError` voorwerp toe.

1. De portfolio samenstellen.

   Roep de methode van het `AssemblerServiceClient` `invokeDDX` object aan en geef de volgende waarden door:

   * Een `BLOB` object dat staat voor het DDX-document
   * Het `MyMapOf_xsd_string_To_xsd_anyType` object dat de vereiste bestanden bevat
   * Een `AssemblerOptionSpec` object dat uitvoeringsopties opgeeft

   De `invokeDDX` methode retourneert een `AssemblerResult` object dat de resultaten van de taak en eventuele uitzonderingen bevat die zich hebben voorgedaan.

1. Sla het samengevoegde portfolio op.

   Voer de volgende handelingen uit om het nieuwe PDF-portfolio te verkrijgen:

   * Open het `AssemblerResult` veld van het `documents` object. Dit is een `Map` object dat de resulterende PDF-documenten bevat.
   * Doorloop het `Map` object om elk resulterend document te verkrijgen. Dan, giet dat serielid `value` aan een `BLOB`.
   * Pak de binaire gegevens die het PDF-document vertegenwoordigen, uit door de `BLOB` eigenschap van het `MTOM` object te openen. Hiermee wordt een array met bytes geretourneerd die u naar een PDF-bestand kunt schrijven.

**Zie ook**

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)
