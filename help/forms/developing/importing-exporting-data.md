---
title: Gegevens importeren en exporteren
description: Gebruik de dienst van de Integratie van de Gegevens van de Vorm om gegevens in een vorm van de PDF in te voeren en gegevens van een vorm van de PDF uit te voeren gebruikend Java API en de Dienst API van het Web.
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
exl-id: 96310e0a-8e95-4a55-9508-5298b8d67f83
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '2754'
ht-degree: 0%

---

# Gegevens importeren en exporteren {#importing-and-exporting-data}

**Voorbeelden en voorbeelden in dit document gelden alleen voor AEM Forms in JEE-omgeving.**

## Over de service Formuliergegevensintegratie {#about-the-form-data-integration-service}

De dienst van de Integratie van Gegevens van de Vorm kan gegevens in een vorm van PDF invoeren en gegevens van een vorm van PDF uitvoeren. De import- en exportbewerkingen ondersteunen twee typen PDF forms:

* Een Acrobat-formulier (gemaakt in Acrobat) is een PDF-document dat formuliervelden bevat.
* Een XML-formulier voor Adoben (gemaakt in Designer) is een PDF-document dat voldoet aan de XML Adobe XML Forms Architecture (XFA).

Formuliergegevens kunnen afhankelijk van het type PDF-formulier in een van de volgende indelingen bestaan:

* An XFDF file, which is an XML version of the Acrobat form data format.
* Een XDP-bestand, een XML-bestand dat formuliervelddefinities bevat. Het kan ook formulierveldgegevens en een ingesloten PDF-bestand bevatten. Een door Designer gegenereerd XDP-bestand kan alleen worden gebruikt als het een ingesloten basis-64-gecodeerd PDF-document bevat.

U kunt deze taken uitvoeren met de service Formuliergegevensintegratie:

* Gegevens importeren in PDF forms. Zie voor meer informatie [Formuliergegevens importeren](importing-exporting-data.md#importing-form-data).
* Gegevens exporteren uit PDF forms. Zie voor meer informatie [Formuliergegevens exporteren](importing-exporting-data.md#exporting-form-data).

>[!NOTE]
>
>Voor meer informatie over de dienst van de Integratie van de Gegevens van de Vorm, zie [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Formuliergegevens importeren {#importing-form-data}

U kunt formuliergegevens in interactieve PDF forms importeren met de service Formuliergegevensintegratie. Een interactief PDF-formulier is een PDF-document dat een of meer velden bevat voor het verzamelen van informatie van een gebruiker of voor het weergeven van aangepaste informatie. De service Formuliergegevensintegratie ondersteunt geen formulierberekeningen, validatie of scripts.

Als u gegevens wilt importeren in een formulier dat is gemaakt in Designer, moet u verwijzen naar een geldige XML-gegevensbron voor XDP. Neem bijvoorbeeld het volgende voorbeeld van een hypotheekapplicatie.

![ie_ie_lannformdata](assets/ie_ie_loanformdata.png)

Als u gegevenswaarden in dit formulier wilt importeren, moet u beschikken over een geldige XML-gegevensbron die overeenkomt met het formulier. U kunt geen willekeurige XML-gegevensbron gebruiken om gegevens in een formulier te importeren met de service Formuliergegevensintegratie. Het verschil tussen een willekeurige XML-gegevensbron en een XDP XML-gegevensbron is dat een XDP-gegevensbron voldoet aan de XML Forms Architecture (XFA). De volgende XML vertegenwoordigt een XDP XML-gegevensbron die overeenkomt met het voorbeeld van een hypotheektoepassing.

```xml
 <?xml version="1.0" encoding="UTF-8" ?>
 - <xfa:datasets xmlns:xfa="https://www.xfa.org/schema/xfa-data/1.0/">
 - <xfa:data>
 - <data>
     - <Layer>
         <closeDate>1/26/2007</closeDate>
         <lastName>Johnson</lastName>
         <firstName>Jerry</firstName>
         <mailingAddress>JJohnson@NoMailServer.com</mailingAddress>
         <city>New York</city>
         <zipCode>00501</zipCode>
         <state>NY</state>
         <dateBirth>26/08/1973</dateBirth>
         <middleInitials>D</middleInitials>
         <socialSecurityNumber>(555) 555-5555</socialSecurityNumber>
         <phoneNumber>5555550000</phoneNumber>
     </Layer>
     - <Mortgage>
         <mortgageAmount>295000.00</mortgageAmount>
         <monthlyMortgagePayment>1724.54</monthlyMortgagePayment>
         <purchasePrice>300000</purchasePrice>
         <downPayment>5000</downPayment>
         <term>25</term>
         <interestRate>5.00</interestRate>
     </Mortgage>
 </data>
 </xfa:data>
 </xfa:datasets>
```

>[!NOTE]
>
>Voor meer informatie over de dienst van de Integratie van de Gegevens van de Vorm, zie [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary-of-steps}

Voer de volgende stappen uit om formuliergegevens te importeren in een PDF-formulier:

1. Inclusief projectbestanden.
1. Creeer een de dienstcliënt van de Integratie van Gegevens van de Vorm.
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
* adobe-utilities.jar (Vereist als AEM Forms wordt geïmplementeerd op JBoss)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)

Voor informatie over de locatie van deze JAR-bestanden raadpleegt u [Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Een serviceclient voor formuliergegevensintegratie maken**

Voordat u via programmacode gegevens kunt importeren in een PDF formulier-client-API, moet u een Data Integration-service-client maken. Wanneer u een serviceclient maakt, definieert u verbindingsinstellingen die vereist zijn om een service aan te roepen. Zie voor meer informatie [Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).

**Verwijzen naar een PDF-formulier**

Als u gegevens wilt importeren in een PDF-formulier, moet u verwijzen naar een XML-formulier dat in Designer is gemaakt of naar een Acrobat-formulier dat in Acrobat is gemaakt.

**Verwijzen naar een XML-gegevensbron**

Als u formuliergegevens wilt importeren, moet u naar een geldige gegevensbron verwijzen. Als u gegevens wilt importeren in een XFA XML-formulier dat is gemaakt in Designer, moet u een XDP XML-gegevensbron gebruiken. Als u naar een Acrobat-formulier verwijst, moet u een XFDF-gegevensbron gebruiken. Voor elk veld waarin u gegevens wilt importeren, moet een waarde worden opgegeven. Als een element in de XML-gegevensbron niet overeenkomt met een veld in het formulier, wordt het element genegeerd.

**Gegevens importeren in het PDF-formulier**

Nadat u naar een PDF-formulier en een geldige XML-gegevensbron hebt verwezen, kunt u de gegevens in het PDF-formulier importeren.

**Het PDF-formulier opslaan als een PDF-bestand**

Nadat u gegevens in een formulier hebt geïmporteerd, kunt u het formulier opslaan als een PDF-bestand. Wanneer een gebruiker het formulier eenmaal heeft opgeslagen als een PDF-bestand, kan hij het formulier openen in Adobe Reader of Acrobat en het formulier bekijken met de geïmporteerde gegevens.

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

1. Creeer een de dienstcliënt van de Integratie van Gegevens van de Vorm.

   * Een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Een `FormDataIntegrationClient` object door de constructor ervan te gebruiken en de `ServiceClientFactory` object.

1. Verwijzen naar een PDF-formulier.

   * Een `java.io.FileInputStream` object met behulp van de constructor. Geef een tekenreekswaarde door die de locatie van het PDF-formulier aangeeft.
   * Een `com.adobe.idp.Document` object dat het PDF-formulier opslaat met het gereedschap `com.adobe.idp.Document` constructor. Geef de `java.io.FileInputStream` object dat het PDF-formulier bevat voor de constructor.

1. Verwijzen naar een XML-gegevensbron.

   * Een `java.io.FileInputStream` -object door gebruik te maken van de constructor en een tekenreekswaarde door te geven die de locatie aangeeft van het XML-bestand dat de gegevens bevat die in het formulier moeten worden geïmporteerd.
   * Een `com.adobe.idp.Document` object dat formuliergegevens opslaat met het gereedschap `com.adobe.idp.Document` constructor. Geef de `java.io.FileInputStream` object dat formuliergegevens bevat voor de constructor.

1. Gegevens importeren in het PDF-formulier.

   Gegevens importeren in een PDF-formulier door het `FormDataIntegrationClient` object `importData` en geeft de volgende waarden door:

   * De `com.adobe.idp.Document` object waarin het PDF-formulier is opgeslagen.
   * De `com.adobe.idp.Document` -object dat formuliergegevens opslaat.

   De `importData` methode retourneert een `com.adobe.idp.Document` object dat een PDF-formulier opslaat dat de gegevens in de XML-gegevensbron bevat.

1. Sla het PDF-formulier op als een PDF-bestand.

   * Een `java.io.File` -object en zorg ervoor dat de bestandsextensie &quot;.PDF&quot; is.
   * De `Document` object `copyToFile` methode om de inhoud van de `Document` object naar het bestand (gebruik de `Document` object dat is geretourneerd door de `importData` methode).

**Zie ook**

[Overzicht van de stappen](importing-exporting-data.md#summary-of-steps)

[Snel starten (SOAP-modus): formuliergegevens importeren met de Java API](/help/forms/developing/form-data-integration-service-java.md#quick-start-soap-mode-importing-form-data-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Formuliergegevens importeren met de webservice-API {#import-form-data-using-the-web-service-api}

Formuliergegevens importeren met de API (webservice) voor formuliergegevensintegratie:

1. Inclusief projectbestanden.

   Creeer een Microsoft .NET project dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/FormDataIntegration?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` met het IP-adres van de server die als host fungeert voor AEM Forms.

1. Creeer een de dienstcliënt van de Integratie van Gegevens van de Vorm.

   * Een `FormDataIntegrationClient` object met de standaardconstructor.
   * Een `FormDataIntegrationClient.Endpoint.Address` object door het `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/FormDataIntegration?blob=mtom`.) U hoeft de `lc_version` kenmerk. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt. Geef echter `?blob=mtom` MTOM gebruiken.
   * Een `System.ServiceModel.BasicHttpBinding` object door de waarde van het object op te halen `FormDataIntegrationClient.Endpoint.Binding` veld. De geretourneerde waarde omzetten in `BasicHttpBinding`.
   * Stel de `System.ServiceModel.BasicHttpBinding` object `MessageEncoding` veld naar `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld toe `FormDataIntegrationClient.ClientCredentials.UserName.UserName`.
      * De bijbehorende wachtwoordwaarde aan het veld toewijzen `FormDataIntegrationClient.ClientCredentials.UserName.Password`.
      * De constante waarde toewijzen `HttpClientCredentialType.Basic` naar het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * De constante waarde toewijzen `BasicHttpSecurityMode.TransportCredentialOnly` naar het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Verwijzen naar een PDF-formulier.

   * Een `BLOB` object met behulp van de constructor. Dit `BLOB` wordt gebruikt om het PDF-formulier op te slaan.
   * Een `System.IO.FileStream` object door de constructor ervan aan te roepen. Geef een tekenreekswaarde door die de locatie van het PDF-formulier aangeeft en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van de `System.IO.FileStream` object. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` object `Length` eigenschap.
   * De bytearray vullen met streamgegevens door de `System.IO.FileStream` object `Read` methode. Geef de bytearray, de startpositie en de streamlengte door om te lezen.
   * Vul de `BLOB` object door het toe te wijzen `MTOM` veld met de inhoud van de bytearray.

1. Verwijzen naar een XML-gegevensbron.

   * Een `BLOB` object met behulp van de constructor. Dit `BLOB` wordt gebruikt om de gegevens op te slaan die in het formulier worden geïmporteerd.
   * Een `System.IO.FileStream` object door de constructor ervan aan te roepen. Geef een tekenreekswaarde door die de locatie aangeeft van het XML-bestand dat de te importeren gegevens bevat en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van de `System.IO.FileStream` object. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` object `Length` eigenschap.
   * De bytearray vullen met streamgegevens door de `System.IO.FileStream` object `Read` methode. Geef de bytearray, de startpositie en de streamlengte door om te lezen.
   * Vul de `BLOB` object door het toe te wijzen `MTOM` veld met de inhoud van de bytearray.

1. Gegevens importeren in het PDF-formulier.

   Gegevens importeren in het PDF-formulier door het `FormDataIntegrationClient` object `importData` en geeft de volgende waarden door:

   * De `BLOB` object waarin het PDF-formulier is opgeslagen.
   * De `BLOB` -object dat formuliergegevens opslaat.

   De `importData` methode retourneert een `BLOB` object dat een PDF-formulier opslaat dat de gegevens in de XML-gegevensbron bevat.

1. Sla het PDF-formulier op als een PDF-bestand.

   * Een `System.IO.FileStream` door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het PDF-bestand vertegenwoordigt.
   * Maak een bytearray waarin de gegevensinhoud van de `BLOB` object dat is geretourneerd door de `importData` methode. Vul de bytearray met de waarde van de `BLOB` object `MTOM` veld.
   * Een `System.IO.BinaryWriter` object door de constructor aan te roepen en de `System.IO.FileStream` object.
   * Schrijf de inhoud van de bytearray naar een PDF-bestand door het `System.IO.BinaryWriter` object `Write` en geeft u de bytearray door.

**Zie ook**

[Overzicht van de stappen](importing-exporting-data.md#summary-of-steps)

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

## Formuliergegevens exporteren {#exporting-form-data}

U kunt formuliergegevens vanuit een interactief PDF-formulier exporteren met de service Formuliergegevensintegratie. De indeling van de geëxporteerde gegevens is afhankelijk van het formuliertype. Als het formuliertype een Acrobat-formulier is dat in Acrobat is gemaakt, zijn de geëxporteerde gegevens XFDF. Als het formuliertype een XML-formulier is dat is gemaakt in Designer, zijn de geëxporteerde gegevens XDP.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Integratie van de Gegevens van de Vorm, zie [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary_of_steps-1}

Voer de volgende stappen uit om formuliergegevens uit een PDF-formulier te exporteren:

1. Projectbestanden opnemen
1. Creeer een de dienstcliënt van de Integratie van Gegevens van de Vorm.
1. Verwijzen naar een PDF-formulier.
1. Gegevens exporteren uit het PDF-formulier.
1. Sla de geëxporteerde gegevens op als een XML-bestand.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u ervoor zorgen dat u de proxybestanden opneemt.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-formdataintegration-client.jar
* adobe-utilities.jar (Vereist als AEM Forms wordt geïmplementeerd op JBoss)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)

**Een serviceclient voor formuliergegevensintegratie maken**

Voordat u gegevens via programmacode kunt importeren in een PDF formClient-API, moet u een Data Integration-service-client maken. Wanneer u een serviceclient maakt, definieert u verbindingsinstellingen die vereist zijn om een service aan te roepen. Ter informatie: [Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).

**Verwijzen naar een PDF-formulier**

Als u gegevens wilt exporteren uit een PDF-formulier, moet u verwijzen naar een PDF-formulier dat is gemaakt in Designer of Acrobat en dat formuliergegevens bevat. Als u probeert gegevens te exporteren uit een leeg PDF-formulier, krijgt u een leeg XML-schema.

**Gegevens exporteren uit het PDF-formulier**

Nadat u naar een PDF-formulier hebt verwezen dat formuliergegevens bevat, kunt u de gegevens uit het formulier exporteren. De gegevens worden geëxporteerd in een XML-schema dat is gebaseerd op het formulier.

**De formuliergegevens opslaan als een XML-bestand**

Nadat u formuliergegevens hebt geëxporteerd, kunt u de gegevens opslaan als een XML-bestand. Als het XML-bestand eenmaal is opgeslagen, kunt u het XML-bestand openen in een XML-viewer om de formuliergegevens weer te geven.

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

1. Creeer een de dienstcliënt van de Integratie van Gegevens van de Vorm.

   * Een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Een `FormDataIntegrationClient` object door de constructor ervan te gebruiken en de `ServiceClientFactory` object.

1. Verwijzen naar een PDF-formulier.

   * Een `java.io.FileInputStream` -object door gebruik te maken van de constructor en een tekenreekswaarde door te geven die de locatie aangeeft van het PDF-formulier dat de te exporteren gegevens bevat.
   * Een `com.adobe.idp.Document` object dat het PDF-formulier opslaat met het gereedschap `com.adobe.idp.Document` constructor. Geef de `java.io.FileInputStream` object dat het PDF-formulier bevat voor de constructor.

1. Gegevens exporteren uit het PDF-formulier.

   Formuliergegevens exporteren door het `FormDataIntegrationClient` object `exportData` en geeft de `com.adobe.idp.Document` object waarin het PDF-formulier is opgeslagen. Deze methode retourneert een `com.adobe.idp.Document` object dat formuliergegevens opslaat als een XML-schema.

1. Sla het PDF-formulier op als een PDF-bestand.

   * Een `java.io.File` en zorg ervoor dat de bestandsextensie XML is.
   * De `Document` object `copyToFile` methode om de inhoud van de `Document` object naar het bestand (gebruik de `Document` object dat is geretourneerd door de `exportData` methode).

**Zie ook**

[Overzicht van de stappen](importing-exporting-data.md#summary-of-steps)

[Snel starten (SOAP-modus): formuliergegevens exporteren met de Java API](/help/forms/developing/form-data-integration-service-java.md#quick-start-soap-mode-exporting-form-data-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Formuliergegevens exporteren met de webservice-API {#export-form-data-using-the-web-service-api}

Formuliergegevens exporteren met de API (webservice) voor formuliergegevensintegratie:

1. Inclusief projectbestanden.

   Creeer een Microsoft .NET project dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/FormDataIntegration?WSDL&lc_version=9.0.1`.

   * Vervangen `localhost` met het IP-adres van de server die als host fungeert voor AEM Forms.

1. Creeer een de dienstcliënt van de Integratie van Gegevens van de Vorm.

   * Een `FormDataIntegrationClient` object met de standaardconstructor.
   * Een `FormDataIntegrationClient.Endpoint.Address` object door het `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/FormDataIntegration?blob=mtom`.) U hoeft de `lc_version` kenmerk. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt. Geef echter `?blob=mtom` MTOM gebruiken.
   * Een `System.ServiceModel.BasicHttpBinding` object door de waarde van het object op te halen `FormDataIntegrationClient.Endpoint.Binding` veld. De geretourneerde waarde omzetten in `BasicHttpBinding`.
   * Stel de `System.ServiceModel.BasicHttpBinding` object `MessageEncoding` veld naar `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld toe `FormDataIntegrationClient.ClientCredentials.UserName.UserName`.
      * De bijbehorende wachtwoordwaarde aan het veld toewijzen `FormDataIntegrationClient.ClientCredentials.UserName.Password`.
      * De constante waarde toewijzen `HttpClientCredentialType.Basic` naar het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * De constante waarde toewijzen `BasicHttpSecurityMode.TransportCredentialOnly` naar het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Verwijzen naar een PDF-formulier.

   * Een `BLOB` object met behulp van de constructor. Dit `BLOB` wordt gebruikt om het PDF-formulier op te slaan waaruit gegevens worden geëxporteerd.
   * Een `System.IO.FileStream` object door de constructor ervan aan te roepen. Geef een tekenreekswaarde door die de locatie van het PDF-formulier aangeeft en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van de `System.IO.FileStream` object. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` object `Length` eigenschap.
   * De bytearray vullen met streamgegevens door de `System.IO.FileStream` object `Read` en geeft u de bytearray, de startpositie en de streamlengte door die u wilt lezen.
   * Vul de `BLOB` object door het toe te wijzen `MTOM` veld met de inhoud van de bytearray.

1. Gegevens exporteren uit het PDF-formulier.

   Gegevens importeren in een PDF-formulier door het `FormDataIntegrationClient` object `exportData` en geeft de `BLOB` object waarin het PDF-formulier is opgeslagen. Deze methode retourneert een `BLOB` object dat formuliergegevens opslaat als een XML-schema.

1. Sla het PDF-formulier op als een PDF-bestand.

   * Een `System.IO.FileStream` door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de locatie van het XML-bestand vertegenwoordigt.
   * Maak een bytearray waarin de gegevensinhoud van de `BLOB` object dat is geretourneerd door de `exportData` methode. Vul de bytearray met de waarde van de `BLOB` object `MTOM` veld.
   * Een `System.IO.BinaryWriter` object door de constructor aan te roepen en de `System.IO.FileStream` object.
   * Schrijf de inhoud van de bytearray naar een XML-bestand door het `System.IO.BinaryWriter` object `Write` en geeft u de bytearray door.

**Zie ook**

[Overzicht van de stappen](importing-exporting-data.md#summary-of-steps)

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)
