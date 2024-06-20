---
title: Gebruiksrechten toewijzen
description: Gebruik de Acrobat Reader DC-extensies Java Client API en Web Service API om gebruiksrechten toe te passen op en te verwijderen uit PDF-documenten.
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
exl-id: 6af148eb-427a-4b54-9c5f-8750736882d8
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,  Document Services, Reader Extensions
source-git-commit: 539da06db98395ae6eaee8103a3e4b31204abbb8
workflow-type: tm+mt
source-wordcount: '3897'
ht-degree: 0%

---

# Gebruiksrechten toewijzen {#assigning-usage-rights}

**Voorbeelden en voorbeelden in dit document gelden alleen voor AEM Forms in JEE-omgeving.**

## Over de Acrobat Reader DC-extensieservice {#about-the-acrobat-reader-dc-extensions-service}

Met de Acrobat Reader DC Extension Service kan uw organisatie eenvoudig interactieve PDF-documenten delen door de functionaliteit van Adobe Reader uit te breiden. De Acrobat Reader DC-extensieservice biedt volledige ondersteuning voor alle PDF-documenten, tot en met PDF 1.7. Het werkt met Adobe Reader 7.0 en hoger. De service voegt gebruiksrechten toe aan een PDF-document, waarbij functies worden geactiveerd die gewoonlijk niet beschikbaar zijn wanneer een PDF-document wordt geopend met Adobe Reader. Gebruikers van derden hebben geen extra software of plug-ins nodig om met documenten waarvoor rechten zijn ingeschakeld te kunnen werken.

U kunt deze taken uitvoeren met de Acrobat Reader DC-extensieservice:

* Gebruiksrechten toepassen op PDF-documenten. Zie voor meer informatie [Gebruiksrechten toepassen op PDF-documenten](assigning-usage-rights.md#applying-usage-rights-to-pdf-documents).
* Gebruiksrechten verwijderen uit PDF-documenten. Zie voor meer informatie [Gebruiksrechten verwijderen uit PDF-documenten](assigning-usage-rights.md#removing-usage-rights-from-pdf-documents).
* Retrieve crediteurdetails. Zie voor meer informatie [Referentiegegevens ophalen](assigning-usage-rights.md#retrieving-credential-information).

>[!NOTE]
>
>Ga voor meer informatie over de Acrobat Reader DC Extension Service naar [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Gebruiksrechten toepassen op PDF-documenten {#applying-usage-rights-to-pdf-documents}

U kunt gebruiksrechten toepassen op PDF-documenten met de Acrobat Reader DC Extension Java Client API en webservice. Gebruiksrechten hebben betrekking op functionaliteit die standaard beschikbaar is in Acrobat, maar niet in Adobe Reader, zoals de mogelijkheid om opmerkingen toe te voegen aan een formulier of formuliervelden in te vullen en het formulier op te slaan. PDF-documenten waarop gebruiksrechten zijn toegepast, worden documenten met ingeschakelde rechten genoemd. Een gebruiker die een document met ingeschakelde rechten opent in Adobe Reader, kan bewerkingen uitvoeren die zijn ingeschakeld voor dat specifieke document.

>[!NOTE]
>
>Wanneer u gebruiksrechten toepast op PDF-documenten met de `applyUsageRights` -methode, die onderdeel is van de Java API, kunt u de `isModeFinal` parameter van de `ReaderExtensionsOptionSpec` object naar `false`. Hierdoor worden de verwerkte formulieren niet bijgewerkt en verbeteren de prestaties. Als u de verwerkte teller van de formulieren niet wilt bijwerken, kunt u het beste de instelling `isModeFinal` parameter to `false`.

>[!NOTE]
>
>Ga voor meer informatie over de Acrobat Reader DC Extension Service naar [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary-of-steps}

Voer de volgende stappen uit om gebruiksrechten toe te passen op een PDF-document:

1. Inclusief projectbestanden.
1. Maak een Acrobat Reader DC Extension Client-object.
1. Een PDF-document ophalen.
1. Geef de gebruiksrechten op die u wilt toepassen.
1. Gebruiksrechten toepassen op het PDF-document.
1. Sla het PDF-document waarvoor rechten zijn ingeschakeld op.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u ervoor zorgen dat u de proxybestanden opneemt.

**Acrobat Reader DC-extensies maken voor clientobjecten**

Als u programmatisch een Acrobat Reader DC Extension Service-bewerking wilt uitvoeren, moet u een Acrobat Reader DC Extension Service Client-object maken. Als u de Acrobat Reader DC-extensies Java API gebruikt, maakt u een `ReaderExtensionsServiceClient` object. Als u de Acrobat Reader DC-API voor extensies gebruikt, maakt u een `ReaderExtensionsServiceService` object.

**Een PDF-document ophalen**

Haal een PDF-document op om gebruiksrechten toe te passen. PDF-documenten met ingeschakelde rechten bevatten een gebruiksrechtenwoordenboek. Wanneer Adobe Reader een document met een dergelijk woordenboek opent, worden alleen de gebruiksrechten ingeschakeld die in het woordenboek voor dat document zijn opgegeven. Als het document geen gebruiksrechtenwoordenboek bevat, wordt dit gemaakt door de Acrobat Reader DC Extension Service. Als het al een woordenboek bevat, overschrijft de Acrobat Reader DC-extensieservice bestaande gebruiksrechten met de gebruiksrechten die u opgeeft. In het woordenboek wordt opgegeven welke gebruiksrechten zijn ingeschakeld. Wanneer een gebruiker het document in Adobe Reader opent, zijn alleen de gebruiksrechten toegestaan die in het woordenboek zijn opgegeven.

**Gebruiksrechten opgeven om toe te passen**

De gebruiksrechten die u kunt instellen, worden bepaald door een referentie die u van Adobe Systems Incorporated koopt. Referenties geven doorgaans toestemming om een groep gerelateerde gebruiksrechten in te stellen, zoals rechten die betrekking hebben op interactieve formulieren. Elke referentie biedt het recht om een bepaald aantal PDF-documenten te maken waarvoor rechten zijn ingeschakeld. Een evaluatiereferentie geeft het recht om een onbeperkt aantal ontwerpdocumenten tot stand te brengen.

>[!NOTE]
>
>Als u probeert om een gebruiksrecht toe te wijzen dat niet door uw referentie wordt toegelaten, zult u een uitzondering veroorzaken.

**Gebruiksrechten toepassen op het PDF-document**

Als u gebruiksrechten wilt toepassen op een PDF-document, verwijst u naar de alias van de referentie die u gebruikt om gebruiksrechten toe te passen (een referentie wordt meestal geïnstalleerd tijdens de installatie van AEM Forms). U moet ook het PDF-document opgeven waarop gebruiksrechten worden toegepast. Voor informatie over het vormen van een referentie, zie de het installeren en opstellen gids voor uw toepassingsserver.

**PDF-document met ingeschakelde rechten opslaan**

Nadat de service Acrobat Reader DC-extensies gebruiksrechten heeft toegepast op een PDF-document, kunt u het PDF-document waarvoor rechten zijn ingeschakeld opslaan als een PDF-bestand.

**Zie ook**

[Gebruiksrechten toepassen met de Java API](assigning-usage-rights.md#apply-usage-rights-using-the-java-api)

[Gebruiksrechten toepassen met de webservice-API](assigning-usage-rights.md#apply-usage-rights-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Acrobat Reader DC Extensions Service API - Snel starten](/help/forms/developing/acrobat-reader-dc-extensions-service.md#acrobat-reader-dc-extensions-service-java-api-quick-start-soap)

### Gebruiksrechten toepassen met de Java API {#apply-usage-rights-using-the-java-api}

Gebruiksrechten toepassen op een PDF-document met de Acrobat Reader DC Extensions-API (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden, zoals adobe-reader-extensions-client.jar, op in het klassenpad van uw Java-project.

1. Maak een Acrobat Reader DC Extension Client-object.

   * Een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Een `ReaderExtensionsServiceClient` object door de constructor ervan te gebruiken en de `ServiceClientFactory` object.

1. Een PDF-document ophalen.

   * Een `java.io.FileInputStream` -object dat het PDF-document vertegenwoordigt door de constructor ervan te gebruiken en een tekenreekswaarde door te geven die de locatie van het PDF-document aangeeft.
   * Een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en de `java.io.FileInputStream` object.

1. Geef de gebruiksrechten op die u wilt toepassen.

   * Een `UsageRights` object dat gebruiksrechten vertegenwoordigt door de constructor ervan te gebruiken.
   * Voor elk gebruiksrecht om toe te passen, haalt een overeenkomstige methode aan die tot `UsageRights` object. Als u bijvoorbeeld de opdracht `enableFormFillIn` gebruiksrecht, de `UsageRights` object `enableFormFillIn` methode en doorgeven `true`. (Herhaal deze stap voor elk gebruiksrecht dat u wilt toepassen.)

1. Gebruiksrechten toepassen op het PDF-document.

   * Een `ReaderExtensionsOptionSpec` object met behulp van de constructor. Dit object bevat runtime-opties die vereist zijn voor de Acrobat Reader DC-extensieservice. Wanneer u deze constructor oproept, moet u de volgende waarden opgeven:

      * De `UsageRights` -object dat de gebruiksrechten bevat die op het document moeten worden toegepast.
      * Een tekenreekswaarde die een bericht opgeeft dat wordt weergegeven wanneer het PDF-document waarvoor rechten zijn ingeschakeld, wordt geopend in Adobe Reader 7.x. Dit bericht wordt niet weergegeven in Adobe Reader 8.0.

   * Gebruiksrechten toepassen op het PDF-document door het `ReaderExtensionsServiceClient` object `applyUsageRights` en geeft de volgende waarden door:

      * De `com.adobe.idp.Document` object dat het PDF-document bevat waarop gebruiksrechten zijn toegepast.
      * Een tekenreekswaarde die de alias van de referentie opgeeft waarmee u gebruiksrechten kunt toepassen.
      * Een tekenreekswaarde die de bijbehorende wachtwoordwaarde opgeeft. (Deze parameter wordt momenteel genegeerd. U kunt `null`.)

   * De `ReaderExtensionsOptionSpec` object dat uitvoeringsopties bevat.

   De `applyUsageRights` methode retourneert een `com.adobe.idp.Document` -object dat het PDF-document bevat waarvoor rechten zijn ingeschakeld.

1. Sla het PDF-document waarvoor rechten zijn ingeschakeld op.

   * Een `java.io.File` en zorg dat de bestandsextensie .pdf is.
   * De `com.adobe.idp.Document` object `copyToFile` methode om de inhoud van de `com.adobe.idp.Document` object naar het bestand (gebruik de `com.adobe.idp.Document` object dat is geretourneerd door de `applyUsageRights` methode).

**Zie ook**

[Gebruiksrechten toepassen op PDF-documenten](assigning-usage-rights.md#applying-usage-rights-to-pdf-documents)

[Snel starten (SOAP modus):gebruiksrechten toepassen met de Java API](/help/forms/developing/acrobat-reader-dc-extensions-service.md#quick-start-soap-mode-applying-usage-rights-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Gebruiksrechten toepassen met de webservice-API {#apply-usage-rights-using-the-web-service-api}

Gebruiksrechten toepassen op een PDF-document met de Acrobat Reader DC Extensions-API (webservice):

1. Inclusief projectbestanden.

   Creeer een Microsoft .NET project dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/ReaderExtensionsService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` met het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een Acrobat Reader DC Extension Client-object.

   * Een `ReaderExtensionsServiceClient` object met de standaardconstructor.
   * Een `ReaderExtensionsServiceClient.Endpoint.Address` object door het `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/ReaderExtensionsService?blob=mtom`. Zorg ervoor dat u `?blob=mtom`.)
   * Een `System.ServiceModel.BasicHttpBinding` object door de waarde van het object op te halen `ReaderExtensionsServiceClient.Endpoint.Binding` veld. De geretourneerde waarde omzetten in `BasicHttpBinding`.
   * Stel de `System.ServiceModel.BasicHttpBinding` object `MessageEncoding` veld naar `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld toe `ReaderExtensionsServiceClient.ClientCredentials.UserName.UserName`.
      * De bijbehorende wachtwoordwaarde aan het veld toewijzen `ReaderExtensionsServiceClient.ClientCredentials.UserName.Password`.
      * De constante waarde toewijzen `HttpClientCredentialType.Basic` naar het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * De constante waarde toewijzen `BasicHttpSecurityMode.TransportCredentialOnly` naar het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Een PDF-document ophalen.

   * Een `BLOB` object met behulp van de constructor. De `BLOB` -object wordt gebruikt om een PDF-document op te slaan waarop gebruiksrechten worden toegepast.
   * Een `System.IO.FileStream` door de constructor aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het PDF-document en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van de `System.IO.FileStream` object. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` object `Length` eigenschap.
   * De bytearray vullen met streamgegevens door de `System.IO.FileStream` object `Read` methode. Geef de bytearray, de startpositie en de streamlengte door om te lezen.
   * Vul de `BLOB` object door het toe te wijzen `MTOM` eigenschap met de inhoud van de bytearray.

1. Geef de gebruiksrechten op die u wilt toepassen.

   * Een `UsageRights` object dat gebruiksrechten vertegenwoordigt door de constructor ervan te gebruiken.
   * Wijs voor elk gebruiksrecht de waarde toe `true` aan het overeenkomstige gegevenslid dat tot `UsageRights` object. Als u bijvoorbeeld de opdracht `enableFormFillIn` gebruiksrecht, toewijzen `true` aan de `UsageRights` object `enableFormFillIn` lid. (Herhaal deze stap voor elk gebruiksrecht dat u wilt toepassen.)

1. Gebruiksrechten toepassen op het PDF-document.

   * Een `ReaderExtensionsOptionSpec` object met behulp van de constructor. Dit object bevat runtime-opties die vereist zijn voor de Acrobat Reader DC-extensieservice.
   * Wijs het `UsageRights` aan `ReaderExtensionsOptionSpec` object `usageRights` lid.
   * Wijs een koordwaarde toe die het bericht specificeert dat een gebruiker ziet wanneer het recht-toegelaten PDF document in Adobe Reader aan het `ReaderExtensionsOptionSpec` object `message` lid.
   * Gebruiksrechten toepassen op het PDF-document door het `ReaderExtensionsServiceClient` object `applyUsageRights` en geeft de volgende waarden door:

      * De `BLOB` object dat het PDF-document bevat waarop gebruiksrechten zijn toegepast.
      * Een tekenreekswaarde die de alias van de referentie opgeeft waarmee u gebruiksrechten kunt toepassen.
      * Een tekenreekswaarde die de bijbehorende wachtwoordwaarde opgeeft. (Deze parameter wordt momenteel genegeerd. U kunt `null`.)

   * De `ReaderExtensionsOptionSpec` object dat uitvoeringsopties bevat.

   De `applyUsageRights` methode retourneert een `BLOB` -object dat het PDF-document bevat waarvoor rechten zijn ingeschakeld.

1. Sla het PDF-document waarvoor rechten zijn ingeschakeld op.

   * Een `System.IO.FileStream` object door de constructor ervan aan te roepen. Geef een tekenreekswaarde door die staat voor de bestandslocatie van het PDF-document waarvoor rechten zijn ingeschakeld.
   * Maak een bytearray waarin de gegevensinhoud van de `BLOB` object dat is geretourneerd door de `applyUsageRights` methode. Vul de bytearray met de waarde van de `BLOB` object `MTOM` lid.
   * Een `System.IO.BinaryWriter` object door de constructor aan te roepen en de `System.IO.FileStream` object.
   * Schrijf de inhoud van de bytearray naar een PDF-bestand door het `System.IO.BinaryWriter` object `Write` en geeft u de bytearray door.

**Zie ook**

[Gebruiksrechten toepassen op PDF-documenten](assigning-usage-rights.md#applying-usage-rights-to-pdf-documents)

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Gebruiksrechten verwijderen uit PDF-documenten {#removing-usage-rights-from-pdf-documents}

U kunt gebruiksrechten verwijderen uit een document waarvoor rechten zijn ingeschakeld. U moet ook gebruiksrechten verwijderen uit een PDF-document waarvoor rechten zijn ingeschakeld om andere AEM Forms-bewerkingen op het document uit te voeren. U moet bijvoorbeeld een PDF-document digitaal ondertekenen (of certificeren) voordat u gebruiksrechten instelt. Daarom als u verrichtingen op een recht-toegelaten document wilt uitvoeren, moet u gebruiksrechten uit het document van de PDF verwijderen, de andere verrichtingen uitvoeren, zoals digitaal het ondertekenen van het document, en dan gebruiksrechten op het document opnieuw toepassen.

>[!NOTE]
>
>Ga voor meer informatie over de Acrobat Reader DC Extension Service naar [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary_of_steps-1}

Voer de volgende stappen uit om gebruiksrechten te verwijderen uit een PDF-document waarvoor rechten zijn ingeschakeld:

1. Inclusief projectbestanden.
1. Maak een Acrobat Reader DC Extension Client-object.
1. Een PDF-document met ingeschakelde rechten ophalen.
1. Gebruiksrechten verwijderen uit het PDF-document.
1. Sla het PDF-document op.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u ervoor zorgen dat u de proxybestanden opneemt.

**Acrobat Reader DC-extensies maken voor clientobjecten**

Voordat u een Acrobat Reader DC-extensieservicebewerking programmatisch kunt uitvoeren, moet u een client-object voor de Acrobat Reader DC-extensieservice maken. Als u de Java API gebruikt, maakt u een `ReaderExtensionsServiceClient` object. Als u de Acrobat Reader DC-API voor extensies gebruikt, maakt u een `ReaderExtensionsServiceService` object.

**Een PDF-document met ingeschakelde rechten ophalen**

Haal een PDF-document met ingeschakelde rechten op om gebruiksrechten te verwijderen.

**Gebruiksrechten verwijderen uit het PDF-document**

Nadat u een voor rechten geschikt PDF-document hebt opgehaald, kunt u gebruiksrechten verwijderen. Nadat u gebruiksrechten hebt verwijderd, beschikt het PDF-document niet meer over extra functionaliteit wanneer het wordt weergegeven in Adobe Reader.

**Het PDF-document opslaan**

U kunt het PDF-document dat geen gebruiksrechten meer bevat, opslaan als een PDF-bestand. Als het document is opgeslagen als een PDF-bestand, kan het PDF-document worden weergegeven in Adobe Reader of Acrobat.

**Zie ook**

[Gebruiksrechten verwijderen met de Java API](assigning-usage-rights.md#remove-usage-rights-using-the-java-api)

[Gebruiksrechten verwijderen met de webservice-API](assigning-usage-rights.md#remove-usage-rights-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Acrobat Reader DC Extensions Service API - Snel starten](/help/forms/developing/acrobat-reader-dc-extensions-service.md#acrobat-reader-dc-extensions-service-java-api-quick-start-soap)

[Gebruiksrechten toepassen op PDF-documenten](assigning-usage-rights.md#applying-usage-rights-to-pdf-documents)

### Gebruiksrechten verwijderen met de Java API {#remove-usage-rights-using-the-java-api}

Verwijder gebruiksrechten uit een PDF-document waarvoor rechten zijn ingeschakeld met de Acrobat Reader DC Extension API (Java):

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-reader-extensions-client.jar, op in het klassenpad van uw Java-project.

1. Maak een Acrobat Reader DC Extension Client-object.

   Een `ReaderExtensionsServiceClient` object door de constructor ervan te gebruiken en een `ServiceClientFactory` object dat verbindingseigenschappen bevat.

1. Een PDF-document ophalen.

   * Een `java.io.FileInputStream` -object dat staat voor het PDF-document waarvoor rechten zijn ingeschakeld, met behulp van de constructor en door middel van een tekenreekswaarde die de locatie van het PDF-document aangeeft.
   * Een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en de `java.io.FileInputStream` object.

1. Gebruiksrechten verwijderen uit het PDF-document.

   Gebruiksrechten uit het PDF-document verwijderen door het `ReaderExtensionsServiceClient` object `removeUsageRights` en het doorgeven van de `com.adobe.idp.Document` -object dat het PDF-document bevat waarvoor rechten zijn ingeschakeld. Deze methode retourneert een `com.adobe.idp.Document` object dat een PDF-document bevat dat geen gebruiksrechten heeft.

1. Gebruiksrechten toepassen op het PDF-document.

   * Een `java.io.File` -object en controleer of de bestandsextensie .PDF is.
   * De `Document` object `copyToFile` methode om de inhoud van de `Document` object naar het bestand (gebruik de `Document` object dat is geretourneerd door de `removeUsageRights` methode).

**Zie ook**

[Gebruiksrechten verwijderen uit PDF-documenten](assigning-usage-rights.md#removing-usage-rights-from-pdf-documents)

[Snel starten (SOAP modus): gebruiksrechten verwijderen uit een PDF-document met de Java API](/help/forms/developing/acrobat-reader-dc-extensions-service.md#quick-start-soap-mode-removing-usage-rights-from-a-pdf-document-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Gebruiksrechten verwijderen met de webservice-API {#remove-usage-rights-using-the-web-service-api}

Verwijder gebruiksrechten uit een PDF-document waarvoor rechten zijn ingeschakeld met de Acrobat Reader DC Extension API (webservice):

1. Inclusief projectbestanden.

   Creeer een Microsoft .NET project dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/ReaderExtensionsService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` met het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een Acrobat Reader DC Extension Client-object.

   * Een `ReaderExtensionsServiceClient` object met de standaardconstructor.
   * Een `ReaderExtensionsServiceClient.Endpoint.Address` object door het `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/ReaderExtensionsService?blob=mtom`. Zorg ervoor dat u `?blob=mtom`.)
   * Een `System.ServiceModel.BasicHttpBinding` object door de waarde van het object op te halen `ReaderExtensionsServiceClient.Endpoint.Binding` veld. De geretourneerde waarde omzetten in `BasicHttpBinding`.
   * Stel de `System.ServiceModel.BasicHttpBinding` object `MessageEncoding` veld naar `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld toe `ReaderExtensionsServiceClient.ClientCredentials.UserName.UserName`.
      * De bijbehorende wachtwoordwaarde aan het veld toewijzen `ReaderExtensionsServiceClient.ClientCredentials.UserName.Password`.
      * De constante waarde toewijzen `HttpClientCredentialType.Basic` naar het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * De constante waarde toewijzen `BasicHttpSecurityMode.TransportCredentialOnly` naar het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Een PDF-document ophalen.

   * Een `BLOB` object met behulp van de constructor. De `BLOB` -object wordt gebruikt om het PDF-document met ingeschakelde rechten op te slaan waaruit gebruiksrechten worden verwijderd.
   * Een `System.IO.FileStream` door de constructor aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het PDF-document en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van de `System.IO.FileStream` object. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` object `Length` eigenschap.
   * De bytearray vullen met streamgegevens door de `System.IO.FileStream` object `Read` en geeft u de bytearray, de startpositie en de streamlengte door die u wilt lezen.
   * Vul de `BLOB` object door het toe te wijzen `MTOM` eigenschap met de inhoud van de bytearray.

1. Gebruiksrechten verwijderen uit het PDF-document.

   Gebruiksrechten uit het PDF-document verwijderen door het `ReaderExtensionsServiceClient` object `removeUsageRights` en het doorgeven van de `BLOB` -object dat het PDF-document bevat waarvoor rechten zijn ingeschakeld. Deze methode retourneert een `BLOB` object dat een PDF-document bevat dat geen gebruiksrechten heeft.

1. Gebruiksrechten toepassen op het PDF-document.

   * Een `System.IO.FileStream` door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de locatie van het PDF-bestand vertegenwoordigt.
   * Maak een bytearray waarin de gegevensinhoud van de `BLOB` object dat is geretourneerd door de `removeUsageRights` methode. Vul de bytearray met de waarde van de `BLOB` object `MTOM` lid.
   * Een `System.IO.BinaryWriter` object door de constructor aan te roepen en de `System.IO.FileStream` object.

**Zie ook**

[Gebruiksrechten verwijderen uit PDF-documenten](assigning-usage-rights.md#removing-usage-rights-from-pdf-documents)

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Referentiegegevens ophalen {#retrieving-credential-information}

U kunt informatie ophalen over de referentie die is gebruikt om gebruiksrechten toe te passen op een PDF-document waarvoor gebruiksrechten zijn ingeschakeld. Door informatie over een referentie op te halen, kunt u informatie zoals de datum opvragen waarna het certificaat niet meer geldig is.

>[!NOTE]
>
>Ga voor meer informatie over de Acrobat Reader DC Extension Service naar [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary_of_steps-2}

Voer de volgende stappen uit om informatie op te halen over de referentie die is gebruikt om gebruiksrechten toe te passen op een PDF-document:

1. Inclusief projectbestanden.
1. Maak een Acrobat Reader DC Extension Client-object.
1. Een PDF-document met ingeschakelde rechten ophalen.
1. Haal informatie op over de referentie.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u ervoor zorgen dat u de proxybestanden opneemt.

**Acrobat Reader DC-extensies maken voor clientobjecten**

Voordat u een Acrobat Reader DC-extensieservicebewerking programmatisch kunt uitvoeren, moet u een client-object voor de Acrobat Reader DC-extensieservice maken. Als u de Java API gebruikt, maakt u een `ReaderExtensionsServiceClient` object. Als u de Acrobat Reader DC-API voor extensies gebruikt, maakt u een `ReaderExtensionsServiceService` object.

**Een PDF-document met ingeschakelde rechten ophalen**

Haal een PDF-document met ingeschakelde rechten op om informatie over de referentie op te halen. U kunt informatie over een referentie ook terugwinnen door zijn alias te specificeren; nochtans, als u informatie over een referentie wilt terugwinnen die werd gebruikt om gebruiksrechten op een specifiek recht-toegelaten document van de PDF toe te passen, dan moet u het document terugwinnen.

**Informatie over de referentie ophalen**

Nadat u een voor rechten geschikt document van de PDF terugwint, kunt u informatie over de referentie verkrijgen die werd gebruikt om gebruiksrechten op het toe te passen. U kunt de volgende informatie over de referentie verkrijgen:

* Het bericht dat in Adobe Reader wordt weergegeven wanneer het voor rechten ingeschakelde PDF-document wordt geopend.
* De datum waarna de referentie niet langer geldig is.
* De datum vóór welke de referentie niet geldig is.
* De gebruiksrechten die zijn ingesteld voor dit PDF-document waarvoor rechten zijn ingeschakeld.
* Het aantal keren dat de referentie is gebruikt.

**Zie ook**

[Gebruiksrechten verwijderen met de Java API](assigning-usage-rights.md#remove-usage-rights-using-the-java-api)

[Gebruiksrechten verwijderen met de webservice-API](assigning-usage-rights.md#remove-usage-rights-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Acrobat Reader DC Extensions Service API - Snel starten](/help/forms/developing/acrobat-reader-dc-extensions-service.md#acrobat-reader-dc-extensions-service-java-api-quick-start-soap)

### Crediteringsgegevens ophalen met de Java API {#retrieve-credential-information-using-the-java-api}

Retrireer referentie-informatie met de Acrobat Reader DC Extension API (Java):

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-reader-extensions-client.jar, op in het klassenpad van uw Java-project.

1. Maak een Acrobat Reader DC Extension Client-object.

   Een `ReaderExtensionsServiceClient` object door de constructor ervan te gebruiken en een `ServiceClientFactory` object dat verbindingseigenschappen bevat.

1. Een PDF-document ophalen.

   * Een `java.io.FileInputStream` -object dat het PDF-document waarvoor rechten zijn ingeschakeld vertegenwoordigt met behulp van de constructor en door een tekenreekswaarde door te geven die de locatie van het voor rechten ingeschakelde PDF-document aangeeft.
   * Een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en de `java.io.FileInputStream` object.

1. Gebruiksrechten verwijderen uit het PDF-document.

   * Haal informatie op over de referentie die wordt gebruikt om gebruiksrechten toe te passen op het PDF-document door het `ReaderExtensionsServiceClient` object `getDocumentUsageRights` en het doorgeven van de `com.adobe.idp.Document` -object dat het PDF-document bevat waarvoor rechten zijn ingeschakeld. Deze methode retourneert een `GetUsageRightsResult` object dat referentie-informatie bevat.
   * Haal de datum terug waarna de referentie niet meer geldig is door de `GetUsageRightsResult` object `getNotAfter` methode. Deze methode retourneert een `java.util.Date` object dat staat voor de datum waarna de referentie niet meer geldig is.
   * Hiermee wordt het bericht opgehaald dat in Adobe Reader wordt weergegeven wanneer het voor rechten ingeschakelde PDF-document wordt geopend door het `GetUsageRightsResult` object `getMessage` methode. Deze methode retourneert een tekenreekswaarde die het bericht vertegenwoordigt.

**Zie ook**

[Referentiegegevens ophalen](assigning-usage-rights.md#retrieving-credential-information)

[Snel starten (SOAP modus): referentie-informatie ophalen met de Java API](/help/forms/developing/acrobat-reader-dc-extensions-service.md#quick-start-soap-mode-retrieving-credential-information-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Crediteringsgegevens ophalen met de webservice-API {#retrieve-credential-information-using-the-web-service-api}

Retrificatiegegevens ophalen met de Acrobat Reader DC Extension API (webservice):

1. Inclusief projectbestanden.

   Creeer een Microsoft .NET project dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/ReaderExtensionsService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` met het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een Acrobat Reader DC Extension Client-object.

   * Een `ReaderExtensionsServiceClient` object met de standaardconstructor.
   * Een `ReaderExtensionsServiceClient.Endpoint.Address` object door het `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/ReaderExtensionsService?blob=mtom`. Zorg ervoor dat u `?blob=mtom`.)
   * Een `System.ServiceModel.BasicHttpBinding` object door de waarde van het object op te halen `ReaderExtensionsServiceClient.Endpoint.Binding` veld. De geretourneerde waarde omzetten in `BasicHttpBinding`.
   * Stel de `System.ServiceModel.BasicHttpBinding` object `MessageEncoding` veld naar `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld toe `ReaderExtensionsServiceClient.ClientCredentials.UserName.UserName`.
      * De bijbehorende wachtwoordwaarde aan het veld toewijzen `ReaderExtensionsServiceClient.ClientCredentials.UserName.Password`.
      * De constante waarde toewijzen `HttpClientCredentialType.Basic` naar het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * De constante waarde toewijzen `BasicHttpSecurityMode.TransportCredentialOnly` naar het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Een PDF-document ophalen.

   * Een `BLOB` object met behulp van de constructor. De `BLOB` -object wordt gebruikt om een PDF-document met ingeschakelde rechten op te slaan.
   * Een `System.IO.FileStream` -object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie vertegenwoordigt van het PDF-document waarvoor rechten zijn ingeschakeld en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van de `System.IO.FileStream` object. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` object `Length` eigenschap.
   * De bytearray vullen met streamgegevens door de `System.IO.FileStream` object `Read` en geeft u de bytearray, de startpositie en de streamlengte door die u wilt lezen.
   * Vul de `BLOB` object door het toe te wijzen `MTOM` eigenschap met de inhoud van de bytearray.

1. Gebruiksrechten verwijderen uit het PDF-document.

   * Haal informatie op over de referentie die wordt gebruikt om gebruiksrechten toe te passen op het PDF-document door het `ReaderExtensionsServiceClient` object `getDocumentUsageRights` en het doorgeven van de `com.adobe.idp.Document` -object dat het PDF-document bevat waarvoor rechten zijn ingeschakeld. Deze methode retourneert een `GetUsageRightsResult` object dat referentie-informatie bevat.
   * Haal de datum op waarna de referentie niet meer geldig is door de waarde van de `GetUsageRightsResult` object `notAfter` lid. Het gegevenstype van dit gegevenslid is `System.DateTime`.
   * Hiermee wordt het bericht opgehaald dat wordt weergegeven wanneer het PDF-document waarvoor rechten zijn ingeschakeld in Adobe Reader wordt geopend door de waarde van het dialoogvenster `GetUsageRightsResult` object `message` lid. Het gegevenstype van dit gegevenslid is een tekenreeks.
   * Hiermee wordt het aantal keren opgehaald dat de referentie wordt gebruikt door de waarde van de `GetUsageRightsResult` object `useCount` lid. Het gegevenstype van dit gegevenslid is een geheel getal.

**Zie ook**

[Referentiegegevens ophalen](assigning-usage-rights.md#retrieving-credential-information)

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)
