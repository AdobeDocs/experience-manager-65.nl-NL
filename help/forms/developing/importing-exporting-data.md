---
title: Gegevens importeren en exporteren
seo-title: Gegevens importeren en exporteren
description: Met de service Formuliergegevensintegratie kunt u gegevens in een PDF-formulier importeren en gegevens uit een PDF-formulier exporteren met de API voor Java API en Web Service.
seo-description: Met de service Formuliergegevensintegratie kunt u gegevens in een PDF-formulier importeren en gegevens uit een PDF-formulier exporteren met de API voor Java API en Web Service.
uuid: 94ccb6f2-6e5f-43ea-a954-9a4402871a17
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 2e783745-c986-45ba-8e65-7437d114ca38
role: Developer
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '2811'
ht-degree: 0%

---


# Gegevens {#importing-and-exporting-data} importeren en exporteren

**Voorbeelden en voorbeelden in dit document gelden alleen voor AEM Forms in JEE-omgeving.**

## Informatie over de service Formuliergegevensintegratie {#about-the-form-data-integration-service}

Met de service Formuliergegevensintegratie kunt u gegevens importeren in een PDF-formulier en gegevens exporteren uit een PDF-formulier. De import- en exportbewerkingen ondersteunen twee typen PDF forms:

* Een Acrobat-formulier (gemaakt in Acrobat) is een PDF-document dat formuliervelden bevat.
* Een Adobe XML-formulier (gemaakt in Designer) is een PDF-document dat voldoet aan de XML Adobe XML Forms Architecture (XFA).

Afhankelijk van het type PDF-formulier kunnen formuliergegevens in een van de volgende indelingen bestaan:

* An XFDF file, which is an XML version of the Acrobat form data format.
* Een XDP-bestand, dat een XML-bestand is dat formuliervelddefinities bevat. Het kan ook formulierveldgegevens en een ingesloten PDF-bestand bevatten. Een door Designer gegenereerd XDP-bestand kan alleen worden gebruikt als het een ingesloten PDF-document met basis 64-codering bevat.

U kunt deze taken uitvoeren met de service Formuliergegevensintegratie:

* Gegevens importeren in PDF forms. Zie [Formuliergegevens importeren](importing-exporting-data.md#importing-form-data) voor meer informatie.
* Gegevens exporteren uit PDF forms. Zie [Formuliergegevens exporteren](importing-exporting-data.md#exporting-form-data) voor meer informatie.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Integratie van de Gegevens van de Vorm, zie [de Verwijzing van de Diensten voor AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Formuliergegevens {#importing-form-data} importeren

U kunt formuliergegevens in interactieve PDF forms importeren met de service Formuliergegevensintegratie. Een interactief PDF-formulier is een PDF-document dat een of meer velden bevat voor het verzamelen van informatie van een gebruiker of voor het weergeven van aangepaste informatie. De service Formuliergegevensintegratie ondersteunt geen formulierberekeningen, validatie of scripts.

Als u gegevens wilt importeren in een formulier dat is gemaakt in Designer, moet u verwijzen naar een geldige XML-gegevensbron voor XDP. Neem bijvoorbeeld het volgende voorbeeld van een hypotheekapplicatie.

![ie_ie_lannformdata](assets/ie_ie_loanformdata.png)

Als u gegevenswaarden wilt importeren in dit formulier, moet u beschikken over een geldige XML-gegevensbron die overeenkomt met het formulier. U kunt geen willekeurige XML-gegevensbron gebruiken om gegevens in een formulier te importeren met de service Formuliergegevensintegratie. Het verschil tussen een willekeurige XML-gegevensbron en een XDP XML-gegevensbron is dat een XDP-gegevensbron voldoet aan de XML Forms Architecture (XFA). De volgende XML vertegenwoordigt een XDP XML-gegevensbron die overeenkomt met het voorbeeld van een hypotheektoepassing.

```xml
???<?xml version="1.0" encoding="UTF-8" ?>
???- <xfa:datasets xmlns:xfa="https://www.xfa.org/schema/xfa-data/1.0/">
???- <xfa:data>
???- <data>
???    - <Layer>
???        <closeDate>1/26/2007</closeDate>
???        <lastName>Johnson</lastName>
???        <firstName>Jerry</firstName>
???        <mailingAddress>JJohnson@NoMailServer.com</mailingAddress>
???        <city>New York</city>
???        <zipCode>00501</zipCode>
???        <state>NY</state>
???        <dateBirth>26/08/1973</dateBirth>
???        <middleInitials>D</middleInitials>
???        <socialSecurityNumber>(555) 555-5555</socialSecurityNumber>
???        <phoneNumber>5555550000</phoneNumber>
???    </Layer>
???    - <Mortgage>
???        <mortgageAmount>295000.00</mortgageAmount>
???        <monthlyMortgagePayment>1724.54</monthlyMortgagePayment>
???        <purchasePrice>300000</purchasePrice>
???        <downPayment>5000</downPayment>
???        <term>25</term>
???        <interestRate>5.00</interestRate>
???    </Mortgage>
???</data>
???</xfa:data>
???</xfa:datasets>
```

>[!NOTE]
>
>Voor meer informatie over de dienst van de Integratie van de Gegevens van de Vorm, zie [de Verwijzing van de Diensten voor AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van stappen {#summary-of-steps}

Voer de volgende stappen uit om formuliergegevens te importeren in een PDF-formulier:

1. Inclusief projectbestanden.
1. Creeer een de dienstcli??nt van de Integratie van Gegevens van de Vorm.
1. Verwijzen naar een PDF-formulier.
1. Verwijzen naar een XML-gegevensbron.
1. Gegevens importeren in het PDF-formulier.
1. Sla het PDF-formulier op als een PDF-bestand.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u ervoor zorgen dat u de proxybestanden opneemt.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-formdataintegration-client.jar
* adobe-utilities.jar (Vereist als AEM Forms wordt ge??mplementeerd op JBoss)
* jbossall-client.jar (vereist als AEM Forms wordt ge??mplementeerd op JBoss)

Zie [Including AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files) voor informatie over de locatie van deze JAR-bestanden.

**Een serviceclient voor formuliergegevensintegratie maken**

Voordat u gegevens via programmacode kunt importeren in een PDF-formulier met client-API, moet u een client voor gegevensintegratie maken. Wanneer u een serviceclient maakt, definieert u verbindingsinstellingen die vereist zijn om een service aan te roepen. Zie [Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties) voor meer informatie.

**Verwijzen naar een PDF-formulier**

Als u gegevens wilt importeren in een PDF-formulier, moet u verwijzen naar een XML-formulier dat is gemaakt in Designer of een Acrobat-formulier dat is gemaakt in Acrobat.

**Verwijzen naar een XML-gegevensbron**

Als u formuliergegevens wilt importeren, moet u verwijzen naar een geldige gegevensbron. Als u gegevens wilt importeren in een XFA XML-formulier dat is gemaakt in Designer, moet u een XDP XML-gegevensbron gebruiken. Als u naar een Acrobat-formulier verwijst, moet u een XFDF-gegevensbron gebruiken. Voor elk veld waarin u gegevens wilt importeren, moet een waarde worden opgegeven. Als een element in de XML-gegevensbron niet overeenkomt met een veld in het formulier, wordt het element genegeerd.

**Gegevens importeren in het PDF-formulier**

Nadat u naar een PDF-formulier en een geldige XML-gegevensbron hebt verwezen, kunt u de gegevens in het PDF-formulier importeren.

**Het PDF-formulier opslaan als een PDF-bestand**

Nadat u gegevens in een formulier hebt ge??mporteerd, kunt u het formulier opslaan als een PDF-bestand. Als het formulier eenmaal is opgeslagen als PDF-bestand, kan een gebruiker het formulier openen in Adobe Reader of Acrobat en het formulier bekijken met de ge??mporteerde gegevens.

**Zie ook**

[Formuliergegevens importeren met de Java API](importing-exporting-data.md#import-form-data-using-the-java-api)

[Formuliergegevens importeren met de webservice-API](importing-exporting-data.md#import-form-data-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[API voor formuliergegevensintegratie - Snel aan de slag](/help/forms/developing/form-data-integration-service-java.md#form-data-integration-service-java-api-quick-start-soap)

[Formuliergegevens exporteren](importing-exporting-data.md#exporting-form-data)

### Formuliergegevens importeren met de Java API {#import-form-data-using-the-java-api}

Formuliergegevens importeren met de API voor formuliergegevensintegratie (Java):

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-formdataintegration-client.jar, op in het klassenpad van uw Java-project.

1. Creeer een de dienstcli??nt van de Integratie van Gegevens van de Vorm.

   * Maak een `ServiceClientFactory`-object dat verbindingseigenschappen bevat.
   * Maak een `FormDataIntegrationClient`-object door de constructor ervan te gebruiken en het object `ServiceClientFactory` door te geven.

1. Verwijzen naar een PDF-formulier.

   * Maak een `java.io.FileInputStream`-object met de constructor ervan. Geef een tekenreekswaarde door die de locatie van het PDF-formulier aangeeft.
   * Maak een `com.adobe.idp.Document`-object waarmee het PDF-formulier wordt opgeslagen met de constructor `com.adobe.idp.Document`. Geef het object `java.io.FileInputStream` dat het PDF-formulier bevat door aan de constructor.

1. Verwijzen naar een XML-gegevensbron.

   * Maak een `java.io.FileInputStream`-object met de constructor ervan en geef een tekenreekswaarde door die de locatie aangeeft van het XML-bestand dat de gegevens bevat die in het formulier moeten worden ge??mporteerd.
   * Maak een `com.adobe.idp.Document`-object dat formuliergegevens opslaat met de constructor `com.adobe.idp.Document`. Geef het object `java.io.FileInputStream` dat formuliergegevens bevat door aan de constructor.

1. Gegevens importeren in het PDF-formulier.

   Importeer gegevens naar een PDF-formulier door de methode `importData` van het object `FormDataIntegrationClient` aan te roepen en de volgende waarden door te geven:

   * Het object `com.adobe.idp.Document` dat het PDF-formulier opslaat.
   * Het object `com.adobe.idp.Document` dat formuliergegevens opslaat.

   De methode `importData` retourneert een object `com.adobe.idp.Document` dat een PDF-formulier opslaat dat de gegevens in de XML-gegevensbron bevat.

1. Sla het PDF-formulier op als een PDF-bestand.

   * Maak een `java.io.File`-object en zorg dat de bestandsextensie .PDF is.
   * Roep de methode `Document` van het object `copyToFile` aan om de inhoud van het object `Document` naar het bestand te kopi??ren (zorg dat u het object `Document` gebruikt dat door de methode `importData` is geretourneerd).

**Zie ook**

[Overzicht van de stappen](importing-exporting-data.md#summary-of-steps)

[Snel starten (SOAP-modus): Formuliergegevens importeren met de Java API](/help/forms/developing/form-data-integration-service-java.md#quick-start-soap-mode-importing-form-data-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Formuliergegevens importeren met de webservice-API {#import-form-data-using-the-web-service-api}

Formuliergegevens importeren met de API (webservice) voor formuliergegevensintegratie:

1. Inclusief projectbestanden.

   Creeer een project van Microsoft .NET dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/FormDataIntegration?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervang `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Creeer een de dienstcli??nt van de Integratie van Gegevens van de Vorm.

   * Maak een `FormDataIntegrationClient`-object met de standaardconstructor.
   * Maak een `FormDataIntegrationClient.Endpoint.Address`-object met de constructor `System.ServiceModel.EndpointAddress`. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/FormDataIntegration?blob=mtom`). U hoeft het `lc_version`-kenmerk niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt. Geef `?blob=mtom` echter op om MTOM te gebruiken.
   * Maak een `System.ServiceModel.BasicHttpBinding`-object door de waarde van het veld `FormDataIntegrationClient.Endpoint.Binding` op te halen. Cast de terugkeerwaarde aan `BasicHttpBinding`.
   * Stel het veld `System.ServiceModel.BasicHttpBinding` van het object `MessageEncoding` in op `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam voor het AEM aan het veld `FormDataIntegrationClient.ClientCredentials.UserName.UserName` toe.
      * Wijs de overeenkomstige wachtwoordwaarde aan het gebied `FormDataIntegrationClient.ClientCredentials.UserName.Password` toe.
      * Wijs de constante waarde `HttpClientCredentialType.Basic` aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType` toe.
      * Wijs de constante waarde `BasicHttpSecurityMode.TransportCredentialOnly` aan het veld `BasicHttpBindingSecurity.Security.Mode` toe.

1. Verwijzen naar een PDF-formulier.

   * Maak een `BLOB`-object met de constructor ervan. Met dit `BLOB`-object wordt het PDF-formulier opgeslagen.
   * Maak een `System.IO.FileStream`-object door de constructor ervan aan te roepen. Geef een tekenreekswaarde door die de locatie van het PDF-formulier aangeeft en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van het object `System.IO.FileStream` wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de eigenschap `System.IO.FileStream` van het object `Length` op te halen.
   * Vul de bytearray met streamgegevens door de methode `Read` van het object `System.IO.FileStream` aan te roepen. Geef de bytearray, de startpositie en de streamlengte door om te lezen.
   * Vul het `BLOB`-object door het `MTOM`-veld toe te wijzen met de inhoud van de bytearray.

1. Verwijzen naar een XML-gegevensbron.

   * Maak een `BLOB`-object met de constructor ervan. Dit `BLOB`-object wordt gebruikt om de gegevens op te slaan die in het formulier worden ge??mporteerd.
   * Maak een `System.IO.FileStream`-object door de constructor ervan aan te roepen. Geef een tekenreekswaarde door die de locatie aangeeft van het XML-bestand dat de te importeren gegevens bevat en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van het object `System.IO.FileStream` wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de eigenschap `System.IO.FileStream` van het object `Length` op te halen.
   * Vul de bytearray met streamgegevens door de methode `Read` van het object `System.IO.FileStream` aan te roepen. Geef de bytearray, de startpositie en de streamlengte door om te lezen.
   * Vul het `BLOB`-object door het `MTOM`-veld toe te wijzen met de inhoud van de bytearray.

1. Gegevens importeren in het PDF-formulier.

   Importeer gegevens in het PDF-formulier door de methode `FormDataIntegrationClient` van het object `importData` aan te roepen en de volgende waarden door te geven:

   * Het object `BLOB` dat het PDF-formulier opslaat.
   * Het object `BLOB` dat formuliergegevens opslaat.

   De methode `importData` retourneert een object `BLOB` dat een PDF-formulier opslaat dat de gegevens in de XML-gegevensbron bevat.

1. Sla het PDF-formulier op als een PDF-bestand.

   * Maak een `System.IO.FileStream`-object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het PDF-bestand vertegenwoordigt.
   * Maak een bytearray met de gegevensinhoud van het object `BLOB` dat door de methode `importData` is geretourneerd. Vul de bytearray met de waarde van het veld `BLOB` van het object `MTOM`.
   * Maak een `System.IO.BinaryWriter`-object door de constructor ervan aan te roepen en het object `System.IO.FileStream` door te geven.
   * Schrijf de inhoud van de bytearray naar een PDF-bestand door de methode `Write` van het object `System.IO.BinaryWriter` aan te roepen en de bytearray door te geven.

**Zie ook**

[Overzicht van de stappen](importing-exporting-data.md#summary-of-steps)

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

## Formuliergegevens exporteren {#exporting-form-data}

U kunt formuliergegevens vanuit een interactief PDF-formulier exporteren met de service Formuliergegevensintegratie. De indeling van de ge??xporteerde gegevens is afhankelijk van het formuliertype. Als het formuliertype een Acrobat-formulier is dat in Acrobat is gemaakt, zijn de ge??xporteerde gegevens XFDF. Als het formuliertype een XML-formulier is dat is gemaakt in Designer, zijn de ge??xporteerde gegevens XDP.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Integratie van de Gegevens van de Vorm, zie [de Verwijzing van de Diensten voor AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van stappen {#summary_of_steps-1}

Voer de volgende stappen uit om formuliergegevens uit een PDF-formulier te exporteren:

1. Projectbestanden opnemen
1. Creeer een de dienstcli??nt van de Integratie van Gegevens van de Vorm.
1. Verwijzen naar een PDF-formulier.
1. Exporteer gegevens uit het PDF-formulier.
1. Sla de ge??xporteerde gegevens op als een XML-bestand.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u ervoor zorgen dat u de proxybestanden opneemt.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-formdataintegration-client.jar
* adobe-utilities.jar (Vereist als AEM Forms wordt ge??mplementeerd op JBoss)
* jbossall-client.jar (vereist als AEM Forms wordt ge??mplementeerd op JBoss)

**Een serviceclient voor formuliergegevensintegratie maken**

Voordat u gegevens via programmacode kunt importeren in een PDF formClient-API, moet u een Data Integration-service-client maken. Wanneer u een serviceclient maakt, definieert u verbindingsinstellingen die vereist zijn om een service aan te roepen. [Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties) ter informatie.

**Verwijzen naar een PDF-formulier**

Als u gegevens uit een PDF-formulier wilt exporteren, moet u verwijzen naar een PDF-formulier dat is gemaakt in Designer of Acrobat en dat formuliergegevens bevat. Als u probeert gegevens uit een leeg PDF-formulier te exporteren, krijgt u een leeg XML-schema.

**Gegevens exporteren uit het PDF-formulier**

Nadat u naar een PDF-formulier hebt verwezen dat formuliergegevens bevat, kunt u de gegevens uit het formulier exporteren. De gegevens worden ge??xporteerd in een XML-schema dat is gebaseerd op het formulier.

**De formuliergegevens opslaan als een XML-bestand**

Nadat u formuliergegevens hebt ge??xporteerd, kunt u de gegevens opslaan als een XML-bestand. Als het XML-bestand eenmaal is opgeslagen, kunt u het XML-bestand openen in een XML-viewer om de formuliergegevens weer te geven.

**Zie ook**

[Formuliergegevens exporteren met de Java API](importing-exporting-data.md#export-form-data-using-the-java-api)

[Formuliergegevens exporteren met de webservice-API](importing-exporting-data.md#export-form-data-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[API voor formuliergegevensintegratie - Snel aan de slag](/help/forms/developing/form-data-integration-service-java.md#form-data-integration-service-java-api-quick-start-soap)

[Formuliergegevens importeren](importing-exporting-data.md#importing-form-data)

### Formuliergegevens exporteren met de Java API {#export-form-data-using-the-java-api}

Formuliergegevens exporteren met de API voor formuliergegevensintegratie (Java):

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-formdataintegration-client.jar, op in het klassenpad van uw Java-project.

1. Creeer een de dienstcli??nt van de Integratie van Gegevens van de Vorm.

   * Maak een `ServiceClientFactory`-object dat verbindingseigenschappen bevat.
   * Maak een `FormDataIntegrationClient`-object door de constructor ervan te gebruiken en het object `ServiceClientFactory` door te geven.

1. Verwijzen naar een PDF-formulier.

   * Maak een `java.io.FileInputStream`-object met de constructor ervan en geef een tekenreekswaarde door die de locatie aangeeft van het PDF-formulier dat de te exporteren gegevens bevat.
   * Maak een `com.adobe.idp.Document`-object waarmee het PDF-formulier wordt opgeslagen met de constructor `com.adobe.idp.Document`. Geef het object `java.io.FileInputStream` dat het PDF-formulier bevat door aan de constructor.

1. Exporteer gegevens uit het PDF-formulier.

   Exporteer formuliergegevens door de methode `exportData` van het object `FormDataIntegrationClient` aan te roepen en geef het object `com.adobe.idp.Document` door dat het PDF-formulier opslaat. Deze methode retourneert een `com.adobe.idp.Document`-object dat formuliergegevens opslaat als een XML-schema.

1. Sla het PDF-formulier op als een PDF-bestand.

   * Maak een `java.io.File`-object en zorg dat de bestandsextensie XML is.
   * Roep de methode `Document` van het object `copyToFile` aan om de inhoud van het object `Document` naar het bestand te kopi??ren (zorg dat u het object `Document` gebruikt dat door de methode `exportData` is geretourneerd).

**Zie ook**

[Overzicht van de stappen](importing-exporting-data.md#summary-of-steps)

[Snel starten (SOAP-modus): Formuliergegevens exporteren met de Java API](/help/forms/developing/form-data-integration-service-java.md#quick-start-soap-mode-exporting-form-data-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Formuliergegevens exporteren met de webservice-API {#export-form-data-using-the-web-service-api}

Formuliergegevens exporteren met de API (webservice) voor formuliergegevensintegratie:

1. Inclusief projectbestanden.

   Creeer een project van Microsoft .NET dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/FormDataIntegration?WSDL&lc_version=9.0.1`.

   * Vervang `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Creeer een de dienstcli??nt van de Integratie van Gegevens van de Vorm.

   * Maak een `FormDataIntegrationClient`-object met de standaardconstructor.
   * Maak een `FormDataIntegrationClient.Endpoint.Address`-object met de constructor `System.ServiceModel.EndpointAddress`. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/FormDataIntegration?blob=mtom`). U hoeft het `lc_version`-kenmerk niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt. Geef `?blob=mtom` echter op om MTOM te gebruiken.
   * Maak een `System.ServiceModel.BasicHttpBinding`-object door de waarde van het veld `FormDataIntegrationClient.Endpoint.Binding` op te halen. Cast de terugkeerwaarde aan `BasicHttpBinding`.
   * Stel het veld `System.ServiceModel.BasicHttpBinding` van het object `MessageEncoding` in op `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam voor het AEM aan het veld `FormDataIntegrationClient.ClientCredentials.UserName.UserName` toe.
      * Wijs de overeenkomstige wachtwoordwaarde aan het gebied `FormDataIntegrationClient.ClientCredentials.UserName.Password` toe.
      * Wijs de constante waarde `HttpClientCredentialType.Basic` aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType` toe.
      * Wijs de constante waarde `BasicHttpSecurityMode.TransportCredentialOnly` aan het veld `BasicHttpBindingSecurity.Security.Mode` toe.

1. Verwijzen naar een PDF-formulier.

   * Maak een `BLOB`-object met de constructor ervan. Met dit `BLOB`-object wordt het PDF-formulier opgeslagen waaruit gegevens worden ge??xporteerd.
   * Maak een `System.IO.FileStream`-object door de constructor ervan aan te roepen. Geef een tekenreekswaarde door die de locatie van het PDF-formulier aangeeft en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van het object `System.IO.FileStream` wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de eigenschap `System.IO.FileStream` van het object `Length` op te halen.
   * Vul de bytearray met streamgegevens door de methode `Read` van het object `System.IO.FileStream` aan te roepen en de bytearray, de startpositie en de lengte van de stream door te geven om te lezen.
   * Vul het `BLOB`-object door het `MTOM`-veld toe te wijzen met de inhoud van de bytearray.

1. Exporteer gegevens uit het PDF-formulier.

   Importeer gegevens in een PDF-formulier door de methode `exportData` van het object `FormDataIntegrationClient` aan te roepen en geef het object `BLOB` door dat het PDF-formulier opslaat. Deze methode retourneert een `BLOB`-object dat formuliergegevens opslaat als een XML-schema.

1. Sla het PDF-formulier op als een PDF-bestand.

   * Maak een `System.IO.FileStream`-object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de locatie van het XML-bestand vertegenwoordigt.
   * Maak een bytearray met de gegevensinhoud van het object `BLOB` dat door de methode `exportData` is geretourneerd. Vul de bytearray met de waarde van het veld `BLOB` van het object `MTOM`.
   * Maak een `System.IO.BinaryWriter`-object door de constructor ervan aan te roepen en het object `System.IO.FileStream` door te geven.
   * Schrijf de inhoud van de bytearray naar een XML-bestand door de methode `Write` van het object `System.IO.BinaryWriter` aan te roepen en de bytearray door te geven.

**Zie ook**

[Overzicht van de stappen](importing-exporting-data.md#summary-of-steps)

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)
