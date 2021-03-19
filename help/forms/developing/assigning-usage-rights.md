---
title: Gebruiksrechten toewijzen
seo-title: Gebruiksrechten toewijzen
description: Met de Acrobat Reader DC-extensies Java Client API en Web Service API kunt u gebruiksrechten toepassen op en verwijderen uit PDF-documenten.
seo-description: Met de Acrobat Reader DC-extensies Java Client API en Web Service API kunt u gebruiksrechten toepassen op en verwijderen uit PDF-documenten.
uuid: 8c2020df-ea3c-49fa-916f-38a458f40d2b
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 9e8db506-9ace-4e1f-8a7b-c4e9b15dde7e
role: Developer
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '3952'
ht-degree: 0%

---


# Gebruiksrechten {#assigning-usage-rights} toewijzen

**Voorbeelden en voorbeelden in dit document gelden alleen voor AEM Forms in JEE-omgeving.**

## Informatie over de Acrobat Reader DC Extension Service {#about-the-acrobat-reader-dc-extensions-service}

Met de Acrobat Reader DC-extensieservice kunt u eenvoudig interactieve PDF-documenten delen door de functionaliteit van Adobe Reader uit te breiden. De Acrobat Reader DC-extensieservice biedt volledige ondersteuning voor alle PDF-documenten, tot en met PDF 1.7. Het werkt met Adobe Reader 7.0 en hoger. De service voegt gebruiksrechten toe aan een PDF-document. Functies die gewoonlijk niet beschikbaar zijn wanneer een PDF-document wordt geopend met Adobe Reader, worden geactiveerd. Gebruikers van derden hebben geen extra software of plug-ins nodig om met documenten waarvoor rechten zijn ingeschakeld te kunnen werken.

U kunt deze taken uitvoeren met de Acrobat Reader DC-extensieservice:

* Gebruiksrechten toepassen op PDF-documenten. Zie [Gebruiksrechten toepassen op PDF-documenten](assigning-usage-rights.md#applying-usage-rights-to-pdf-documents) voor meer informatie.
* Gebruiksrechten verwijderen uit PDF-documenten. Zie [Gebruiksrechten verwijderen uit PDF-documenten](assigning-usage-rights.md#removing-usage-rights-from-pdf-documents) voor meer informatie.
* Crediteringsgegevens ophalen. Zie [Referentiegegevens ophalen](assigning-usage-rights.md#retrieving-credential-information) voor meer informatie.

>[!NOTE]
>
>Zie [Referentiehandleiding voor services voor AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63) voor meer informatie over de service Acrobat Reader DC-extensies.

## Gebruiksrechten toepassen op PDF-documenten {#applying-usage-rights-to-pdf-documents}

U kunt gebruiksrechten toepassen op PDF-documenten met de Acrobat Reader DC-extensies Java Client API en webservice. Gebruiksrechten hebben betrekking op functionaliteit die standaard beschikbaar is in Acrobat, maar niet in Adobe Reader, zoals de mogelijkheid om opmerkingen toe te voegen aan een formulier of formuliervelden in te vullen en het formulier op te slaan. PDF-documenten waarop gebruiksrechten zijn toegepast, worden documenten met ingeschakelde rechten genoemd. Een gebruiker die een document met ingeschakelde rechten opent in Adobe Reader, kan bewerkingen uitvoeren die zijn ingeschakeld voor dat specifieke document.

>[!NOTE]
>
>Wanneer u gebruiksrechten toepast op PDF-documenten met de methode `applyUsageRights`, die deel uitmaakt van de Java API, kunt u de parameter `isModeFinal` van het `ReaderExtensionsOptionSpec`-object instellen op `false`. Hierdoor worden de verwerkte formulieren niet bijgewerkt en verbeteren de prestaties. Als u niet bezorgd bent over het bijwerken van de verwerkte teller van de formulieren, adviseert u de `isModeFinal` parameter aan `false` te plaatsen.

>[!NOTE]
>
>Zie [Referentiehandleiding voor services voor AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63) voor meer informatie over de service Acrobat Reader DC-extensies.

### Overzicht van stappen {#summary-of-steps}

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

Als u programmatisch een Acrobat Reader DC Extension Service-bewerking wilt uitvoeren, moet u een Acrobat Reader DC Extension Service Client-object maken. Als u de Java API voor Acrobat Reader DC-extensies gebruikt, maakt u een `ReaderExtensionsServiceClient`-object. Als u de API voor webservices voor Acrobat Reader DC-extensies gebruikt, maakt u een `ReaderExtensionsServiceService`-object.

**Een PDF-document ophalen**

U moet een PDF-document ophalen om gebruiksrechten toe te passen. PDF-documenten met rechten bevatten een gebruiksrechtenwoordenboek. Wanneer Adobe Reader een document met een dergelijk woordenboek opent, worden alleen de gebruiksrechten ingeschakeld die in het woordenboek voor dat document zijn opgegeven. Als het document geen gebruiksrechtenwoordenboek bevat, wordt dit gemaakt door de Acrobat Reader DC Extension Service. Als het al een woordenboek bevat, overschrijft de Acrobat Reader DC-extensieservice bestaande gebruiksrechten met de gebruiksrechten die u opgeeft. In het woordenboek wordt opgegeven welke gebruiksrechten zijn ingeschakeld. Wanneer een gebruiker het document in Adobe Reader opent, zijn alleen de gebruiksrechten toegestaan die in het woordenboek zijn opgegeven.

**Gebruiksrechten opgeven om toe te passen**

De gebruiksrechten die u kunt instellen, worden bepaald door een referentie die u van Adobe Systems Incorporated koopt. Referenties geven doorgaans toestemming om een groep gerelateerde gebruiksrechten in te stellen, zoals rechten die betrekking hebben op interactieve formulieren. Elke referentie biedt het recht om een bepaald aantal PDF-documenten te maken waarvoor rechten zijn ingeschakeld. Een evaluatiereferentie geeft het recht om een onbeperkt aantal ontwerpdocumenten tot stand te brengen.

>[!NOTE]
>
>Als u probeert om een gebruiksrecht toe te wijzen dat niet door uw referentie wordt toegelaten, zult u een uitzondering veroorzaken.

**Gebruikersrechten toepassen op het PDF-document**

Als u gebruiksrechten wilt toepassen op een PDF-document, verwijst u naar de alias van de referentie die u gebruikt om gebruiksrechten toe te passen (een referentie wordt meestal geïnstalleerd tijdens de installatie van AEM Forms). U moet ook het PDF-document opgeven waarop gebruiksrechten worden toegepast. Voor informatie over het vormen van een referentie, zie de het installeren en opstellen gids voor uw toepassingsserver.

**PDF-document met ingeschakelde rechten opslaan**

Nadat de service Acrobat Reader DC-extensies gebruiksrechten heeft toegepast op een PDF-document, kunt u het PDF-document met toegangsrechten opslaan als een PDF-bestand.

**Zie ook**

[Gebruiksrechten toepassen met de Java API](assigning-usage-rights.md#apply-usage-rights-using-the-java-api)

[Gebruiksrechten toepassen met de webservice-API](assigning-usage-rights.md#apply-usage-rights-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Acrobat Reader DC Extensions Service API - Snel starten](/help/forms/developing/acrobat-reader-dc-extensions-service.md#acrobat-reader-dc-extensions-service-java-api-quick-start-soap)

### Gebruiksrechten toepassen met de Java-API {#apply-usage-rights-using-the-java-api}

Gebruiksrechten toepassen op een PDF-document met de Acrobat Reader DC Extensions-API (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden, zoals adobe-reader-extensions-client.jar, op in het klassenpad van uw Java-project.

1. Maak een Acrobat Reader DC Extension Client-object.

   * Maak een `ServiceClientFactory`-object dat verbindingseigenschappen bevat.
   * Maak een `ReaderExtensionsServiceClient`-object door de constructor ervan te gebruiken en het object `ServiceClientFactory` door te geven.

1. Een PDF-document ophalen.

   * Maak een `java.io.FileInputStream`-object dat het PDF-document vertegenwoordigt door de constructor ervan te gebruiken en een tekenreekswaarde door te geven die de locatie van het PDF-document aangeeft.
   * Maak een `com.adobe.idp.Document`-object door de constructor ervan te gebruiken en het object `java.io.FileInputStream` door te geven.

1. Geef de gebruiksrechten op die u wilt toepassen.

   * Maak een `UsageRights`-object dat gebruiksrechten vertegenwoordigt door de constructor ervan te gebruiken.
   * Roep voor elk gebruiksrecht een overeenkomende methode aan die tot het object `UsageRights` behoort. Als u bijvoorbeeld het gebruiksrecht `enableFormFillIn` wilt toevoegen, roept u de methode `enableFormFillIn` van het object `UsageRights` aan en geeft u `true` door. (Herhaal deze stap voor elk gebruiksrecht dat u wilt toepassen.)

1. Gebruiksrechten toepassen op het PDF-document.

   * Maak een `ReaderExtensionsOptionSpec`-object met de constructor ervan. Dit object bevat runtime-opties die vereist zijn voor de Acrobat Reader DC-extensieservice. Wanneer u deze constructor oproept, moet u de volgende waarden opgeven:

      * Het `UsageRights`-object dat de gebruiksrechten bevat die op het document moeten worden toegepast.
      * Een tekenreekswaarde die een bericht opgeeft dat wordt weergegeven wanneer het PDF-document waarvoor rechten zijn ingeschakeld, wordt geopend in Adobe Reader 7.x. Dit bericht wordt niet weergegeven in Adobe Reader 8.0.
   * Pas gebruiksrechten toe op het PDF-document door de methode `ReaderExtensionsServiceClient` van het object `applyUsageRights` aan te roepen en de volgende waarden door te geven:

      * Het `com.adobe.idp.Document`-object dat het PDF-document bevat waarop gebruiksrechten worden toegepast.
      * Een tekenreekswaarde die de alias van de referentie opgeeft waarmee u gebruiksrechten kunt toepassen.
      * Een tekenreekswaarde die de bijbehorende wachtwoordwaarde opgeeft. (Deze parameter wordt momenteel genegeerd. U kunt `null` overgaan.)
   * Het `ReaderExtensionsOptionSpec`-object dat uitvoeringsopties bevat.

   De methode `applyUsageRights` retourneert een `com.adobe.idp.Document`-object dat het PDF-document bevat waarvoor rechten zijn ingeschakeld.

1. Sla het PDF-document waarvoor rechten zijn ingeschakeld op.

   * Maak een `java.io.File`-object en controleer of de bestandsextensie .pdf is.
   * Roep de methode `com.adobe.idp.Document` van het object `copyToFile` aan om de inhoud van het object `com.adobe.idp.Document` naar het bestand te kopiëren (zorg dat u het object `com.adobe.idp.Document` gebruikt dat door de methode `applyUsageRights` is geretourneerd).

**Zie ook**

[Gebruiksrechten toepassen op PDF-documenten](assigning-usage-rights.md#applying-usage-rights-to-pdf-documents)

[Snel starten (SOAP-modus):gebruiksrechten toepassen met de Java API](/help/forms/developing/acrobat-reader-dc-extensions-service.md#quick-start-soap-mode-applying-usage-rights-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Gebruiksrechten toepassen met de webservice-API {#apply-usage-rights-using-the-web-service-api}

Gebruiksrechten toepassen op een PDF-document met de Acrobat Reader DC Extensions API (webservice):

1. Inclusief projectbestanden.

   Creeer een project van Microsoft .NET dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/ReaderExtensionsService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervang `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een Acrobat Reader DC Extension Client-object.

   * Maak een `ReaderExtensionsServiceClient`-object met de standaardconstructor.
   * Maak een `ReaderExtensionsServiceClient.Endpoint.Address`-object met de constructor `System.ServiceModel.EndpointAddress`. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/ReaderExtensionsService?blob=mtom`). Zorg ervoor dat u `?blob=mtom` opgeeft.)
   * Maak een `System.ServiceModel.BasicHttpBinding`-object door de waarde van het veld `ReaderExtensionsServiceClient.Endpoint.Binding` op te halen. Cast de terugkeerwaarde aan `BasicHttpBinding`.
   * Stel het veld `System.ServiceModel.BasicHttpBinding` van het object `MessageEncoding` in op `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam voor het AEM aan het veld `ReaderExtensionsServiceClient.ClientCredentials.UserName.UserName` toe.
      * Wijs de overeenkomstige wachtwoordwaarde aan het gebied `ReaderExtensionsServiceClient.ClientCredentials.UserName.Password` toe.
      * Wijs de constante waarde `HttpClientCredentialType.Basic` aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType` toe.
      * Wijs de constante waarde `BasicHttpSecurityMode.TransportCredentialOnly` aan het veld `BasicHttpBindingSecurity.Security.Mode` toe.

1. Een PDF-document ophalen.

   * Maak een `BLOB`-object met de constructor ervan. Met het object `BLOB` wordt een PDF-document opgeslagen waarop gebruiksrechten worden toegepast.
   * Maak een `System.IO.FileStream`-object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het PDF-document en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van het object `System.IO.FileStream` wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de eigenschap `System.IO.FileStream` van het object `Length` op te halen.
   * Vul de bytearray met streamgegevens door de methode `Read` van het object `System.IO.FileStream` aan te roepen. Geef de bytearray, de startpositie en de streamlengte door om te lezen.
   * Vul het object `BLOB` door de eigenschap `MTOM` ervan toe te wijzen met de inhoud van de bytearray.

1. Geef de gebruiksrechten op die u wilt toepassen.

   * Maak een `UsageRights`-object dat gebruiksrechten vertegenwoordigt door de constructor ervan te gebruiken.
   * Voor elk gebruiksrecht om toe te passen, wijs de waarde `true` aan het overeenkomstige gegevenslid toe dat tot `UsageRights` voorwerp behoort. Als u bijvoorbeeld het gebruiksrecht `enableFormFillIn` wilt toevoegen, wijst u `true` toe aan het `UsageRights`-gegevenslid van het `enableFormFillIn`-object. (Herhaal deze stap voor elk gebruiksrecht dat u wilt toepassen.)

1. Gebruiksrechten toepassen op het PDF-document.

   * Maak een `ReaderExtensionsOptionSpec`-object met de constructor ervan. Dit object bevat runtime-opties die vereist zijn voor de Acrobat Reader DC-extensieservice.
   * Wijs het `UsageRights`-object toe aan het `ReaderExtensionsOptionSpec`-gegevenslid van het object.`usageRights`
   * Wijs een tekenreekswaarde toe die het bericht aangeeft dat een gebruiker ziet wanneer het PDF-document waarvoor rechten zijn ingeschakeld in Adobe Reader wordt geopend in het `ReaderExtensionsOptionSpec`-gegevenslid van het `message`-object.
   * Pas gebruiksrechten toe op het PDF-document door de methode `ReaderExtensionsServiceClient` van het object `applyUsageRights` aan te roepen en de volgende waarden door te geven:

      * Het `BLOB`-object dat het PDF-document bevat waarop gebruiksrechten worden toegepast.
      * Een tekenreekswaarde die de alias van de referentie opgeeft waarmee u gebruiksrechten kunt toepassen.
      * Een tekenreekswaarde die de bijbehorende wachtwoordwaarde opgeeft. (Deze parameter wordt momenteel genegeerd. U kunt `null` overgaan.)
   * Het `ReaderExtensionsOptionSpec`-object dat uitvoeringsopties bevat.

   De methode `applyUsageRights` retourneert een `BLOB`-object dat het PDF-document bevat waarvoor rechten zijn ingeschakeld.

1. Sla het PDF-document waarvoor rechten zijn ingeschakeld op.

   * Maak een `System.IO.FileStream`-object door de constructor ervan aan te roepen. Geef een tekenreekswaarde door die de bestandslocatie van het PDF-document met toegangsrechten vertegenwoordigt.
   * Maak een bytearray met de gegevensinhoud van het object `BLOB` dat door de methode `applyUsageRights` is geretourneerd. Vul de bytearray met de waarde van het `BLOB`-gegevenslid van het object `MTOM`.
   * Maak een `System.IO.BinaryWriter`-object door de constructor ervan aan te roepen en het object `System.IO.FileStream` door te geven.
   * Schrijf de inhoud van de bytearray naar een PDF-bestand door de methode `Write` van het object `System.IO.BinaryWriter` aan te roepen en de bytearray door te geven.

**Zie ook**

[Gebruiksrechten toepassen op PDF-documenten](assigning-usage-rights.md#applying-usage-rights-to-pdf-documents)

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Gebruiksrechten verwijderen uit PDF-documenten {#removing-usage-rights-from-pdf-documents}

U kunt gebruiksrechten verwijderen uit een document waarvoor rechten zijn ingeschakeld. U moet ook gebruiksrechten verwijderen uit een PDF-document waarvoor rechten zijn ingeschakeld om andere AEM Forms-bewerkingen uit te voeren. U moet bijvoorbeeld een PDF-document digitaal ondertekenen (of certificeren) voordat u gebruiksrechten instelt. Als u bewerkingen wilt uitvoeren op een document waarvoor rechten zijn ingeschakeld, moet u daarom gebruiksrechten verwijderen uit het PDF-document, de andere bewerkingen uitvoeren, zoals het digitaal ondertekenen van het document, en vervolgens gebruiksrechten opnieuw toepassen op het document.

>[!NOTE]
>
>Zie [Referentiehandleiding voor services voor AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63) voor meer informatie over de service Acrobat Reader DC-extensies.

### Overzicht van stappen {#summary_of_steps-1}

Voer de volgende stappen uit om gebruiksrechten te verwijderen uit een PDF-document waarvoor rechten zijn ingeschakeld:

1. Inclusief projectbestanden.
1. Maak een Acrobat Reader DC Extension Client-object.
1. Een PDF-document waarvoor rechten zijn ingeschakeld ophalen.
1. Gebruiksrechten verwijderen uit het PDF-document.
1. Sla het PDF-document op.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u ervoor zorgen dat u de proxybestanden opneemt.

**Acrobat Reader DC-extensies maken voor clientobjecten**

Voordat u een Acrobat Reader DC-extensieservicebewerking programmatisch kunt uitvoeren, moet u een client-object voor de Acrobat Reader DC-extensieservice maken. Als u de Java API gebruikt, maakt u een `ReaderExtensionsServiceClient`-object. Als u de API voor webservices voor Acrobat Reader DC-extensies gebruikt, maakt u een `ReaderExtensionsServiceService`-object.

**Een PDF-document met ingeschakelde rechten ophalen**

U kunt PDF-documenten waarvoor rechten zijn ingeschakeld, ophalen om gebruiksrechten te verwijderen.

**Gebruikersrechten uit het PDF-document verwijderen**

Nadat u een PDF-document met ingeschakelde rechten hebt opgehaald, kunt u gebruiksrechten verwijderen. Nadat u gebruiksrechten hebt verwijderd, beschikt het PDF-document niet meer over extra functionaliteit wanneer het wordt weergegeven in Adobe Reader.

**Het PDF-document opslaan**

U kunt het PDF-document dat geen gebruiksrechten meer bevat, opslaan als een PDF-bestand. Als het PDF-document eenmaal is opgeslagen als een PDF-bestand, kan het worden weergegeven in Adobe Reader of Acrobat.

**Zie ook**

[Gebruiksrechten verwijderen met de Java API](assigning-usage-rights.md#remove-usage-rights-using-the-java-api)

[Gebruiksrechten verwijderen met de webservice-API](assigning-usage-rights.md#remove-usage-rights-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Acrobat Reader DC Extensions Service API - Snel starten](/help/forms/developing/acrobat-reader-dc-extensions-service.md#acrobat-reader-dc-extensions-service-java-api-quick-start-soap)

[Gebruiksrechten toepassen op PDF-documenten](assigning-usage-rights.md#applying-usage-rights-to-pdf-documents)

### Gebruiksrechten verwijderen met de Java-API {#remove-usage-rights-using-the-java-api}

Verwijder gebruiksrechten uit een PDF-document waarvoor rechten zijn ingeschakeld met de Acrobat Reader DC-API voor extensies (Java):

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-reader-extensions-client.jar, op in het klassenpad van uw Java-project.

1. Maak een Acrobat Reader DC Extension Client-object.

   Maak een `ReaderExtensionsServiceClient`-object door de constructor ervan te gebruiken en een `ServiceClientFactory`-object door te geven dat verbindingseigenschappen bevat.

1. Een PDF-document ophalen.

   * Maak een `java.io.FileInputStream`-object dat het PDF-document waarvoor rechten zijn ingeschakeld, vertegenwoordigt door de constructor ervan te gebruiken en een tekenreekswaarde door te geven die de locatie van het PDF-document aangeeft.
   * Maak een `com.adobe.idp.Document`-object door de constructor ervan te gebruiken en het object `java.io.FileInputStream` door te geven.

1. Gebruiksrechten verwijderen uit het PDF-document.

   Verwijder gebruiksrechten uit het PDF-document door de methode `removeUsageRights` van het object `ReaderExtensionsServiceClient` aan te roepen en het object `com.adobe.idp.Document` door te geven dat het PDF-document met toegangsrechten bevat. Deze methode retourneert een `com.adobe.idp.Document`-object dat een PDF-document bevat dat geen gebruiksrechten heeft.

1. Gebruiksrechten toepassen op het PDF-document.

   * Maak een `java.io.File`-object en controleer of de bestandsextensie .PDF is.
   * Roep de methode `Document` van het object `copyToFile` aan om de inhoud van het object `Document` naar het bestand te kopiëren (zorg dat u het object `Document` gebruikt dat door de methode `removeUsageRights` is geretourneerd).

**Zie ook**

[Gebruiksrechten verwijderen uit PDF-documenten](assigning-usage-rights.md#removing-usage-rights-from-pdf-documents)

[Snel starten (SOAP-modus): Gebruiksrechten verwijderen uit een PDF-document met de Java API](/help/forms/developing/acrobat-reader-dc-extensions-service.md#quick-start-soap-mode-removing-usage-rights-from-a-pdf-document-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Gebruiksrechten verwijderen met de webservice-API {#remove-usage-rights-using-the-web-service-api}

Verwijder gebruiksrechten uit een PDF-document waarvoor rechten zijn ingeschakeld met de API voor Acrobat Reader DC-extensies (webservice):

1. Inclusief projectbestanden.

   Creeer een project van Microsoft .NET dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/ReaderExtensionsService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervang `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een Acrobat Reader DC Extension Client-object.

   * Maak een `ReaderExtensionsServiceClient`-object met de standaardconstructor.
   * Maak een `ReaderExtensionsServiceClient.Endpoint.Address`-object met de constructor `System.ServiceModel.EndpointAddress`. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/ReaderExtensionsService?blob=mtom`). Zorg ervoor dat u `?blob=mtom` opgeeft.)
   * Maak een `System.ServiceModel.BasicHttpBinding`-object door de waarde van het veld `ReaderExtensionsServiceClient.Endpoint.Binding` op te halen. Cast de terugkeerwaarde aan `BasicHttpBinding`.
   * Stel het veld `System.ServiceModel.BasicHttpBinding` van het object `MessageEncoding` in op `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam voor het AEM aan het veld `ReaderExtensionsServiceClient.ClientCredentials.UserName.UserName` toe.
      * Wijs de overeenkomstige wachtwoordwaarde aan het gebied `ReaderExtensionsServiceClient.ClientCredentials.UserName.Password` toe.
      * Wijs de constante waarde `HttpClientCredentialType.Basic` aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType` toe.
      * Wijs de constante waarde `BasicHttpSecurityMode.TransportCredentialOnly` aan het veld `BasicHttpBindingSecurity.Security.Mode` toe.

1. Een PDF-document ophalen.

   * Maak een `BLOB`-object met de constructor ervan. Met het object `BLOB` wordt het PDF-document met toegangsrechten opgeslagen waaruit gebruiksrechten worden verwijderd.
   * Maak een `System.IO.FileStream`-object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het PDF-document en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van het object `System.IO.FileStream` wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de eigenschap `System.IO.FileStream` van het object `Length` op te halen.
   * Vul de bytearray met streamgegevens door de methode `Read` van het object `System.IO.FileStream` aan te roepen en de bytearray, de startpositie en de lengte van de stream door te geven om te lezen.
   * Vul het object `BLOB` door de eigenschap `MTOM` ervan toe te wijzen met de inhoud van de bytearray.

1. Gebruiksrechten verwijderen uit het PDF-document.

   Verwijder gebruiksrechten uit het PDF-document door de methode `removeUsageRights` van het object `ReaderExtensionsServiceClient` aan te roepen en het object `BLOB` door te geven dat het PDF-document met toegangsrechten bevat. Deze methode retourneert een `BLOB`-object dat een PDF-document bevat dat geen gebruiksrechten heeft.

1. Gebruiksrechten toepassen op het PDF-document.

   * Maak een `System.IO.FileStream`-object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de locatie van het PDF-bestand vertegenwoordigt.
   * Maak een bytearray met de gegevensinhoud van het object `BLOB` dat door de methode `removeUsageRights` is geretourneerd. Vul de bytearray met de waarde van het `BLOB`-gegevenslid van het object `MTOM`.
   * Maak een `System.IO.BinaryWriter`-object door de constructor ervan aan te roepen en het object `System.IO.FileStream` door te geven.

**Zie ook**

[Gebruiksrechten verwijderen uit PDF-documenten](assigning-usage-rights.md#removing-usage-rights-from-pdf-documents)

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Referentiegegevens {#retrieving-credential-information} ophalen

U kunt informatie ophalen over de referentie die is gebruikt om gebruiksrechten toe te passen op een PDF-document waarvoor rechten zijn ingeschakeld. Door informatie over een referentie op te halen, kunt u informatie zoals de datum opvragen waarna het certificaat niet meer geldig is.

>[!NOTE]
>
>Zie [Referentiehandleiding voor services voor AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63) voor meer informatie over de service Acrobat Reader DC-extensies.

### Overzicht van stappen {#summary_of_steps-2}

Voer de volgende stappen uit om informatie op te halen over de referentie die is gebruikt om gebruiksrechten toe te passen op een PDF-document:

1. Inclusief projectbestanden.
1. Maak een Acrobat Reader DC Extension Client-object.
1. Een PDF-document waarvoor rechten zijn ingeschakeld ophalen.
1. Haal informatie op over de referentie.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u ervoor zorgen dat u de proxybestanden opneemt.

**Acrobat Reader DC-extensies maken voor clientobjecten**

Voordat u een Acrobat Reader DC-extensieservicebewerking programmatisch kunt uitvoeren, moet u een client-object voor de Acrobat Reader DC-extensieservice maken. Als u de Java API gebruikt, maakt u een `ReaderExtensionsServiceClient`-object. Als u de API voor webservices voor Acrobat Reader DC-extensies gebruikt, maakt u een `ReaderExtensionsServiceService`-object.

**Een PDF-document met ingeschakelde rechten ophalen**

U moet een PDF-document met ingeschakelde rechten ophalen om informatie over de referentie op te halen. U kunt informatie over een referentie ook terugwinnen door zijn alias te specificeren; als u echter informatie wilt ophalen over een referentie die is gebruikt om gebruiksrechten toe te passen op een specifiek PDF-document waarvoor gebruiksrechten zijn ingeschakeld, moet u het document ophalen.

**Informatie over de referentie ophalen**

Nadat u een PDF-document waarvoor rechten zijn ingeschakeld, hebt opgehaald, kunt u informatie opvragen over de referentie die is gebruikt om gebruiksrechten op het document toe te passen. U kunt de volgende informatie over de referentie verkrijgen:

* Het bericht dat in Adobe Reader wordt weergegeven wanneer het PDF-document met toegangsrechten wordt geopend.
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

   Maak een `ReaderExtensionsServiceClient`-object door de constructor ervan te gebruiken en een `ServiceClientFactory`-object door te geven dat verbindingseigenschappen bevat.

1. Een PDF-document ophalen.

   * Maak een `java.io.FileInputStream`-object dat het PDF-document waarvoor rechten zijn ingeschakeld, vertegenwoordigt door de constructor ervan te gebruiken en een tekenreekswaarde door te geven die de locatie van het PDF-document waarvoor rechten zijn ingeschakeld, aangeeft.
   * Maak een `com.adobe.idp.Document`-object door de constructor ervan te gebruiken en het object `java.io.FileInputStream` door te geven.

1. Gebruiksrechten verwijderen uit het PDF-document.

   * Haal informatie op over de referentie die wordt gebruikt om gebruiksrechten toe te passen op het PDF-document door de methode `ReaderExtensionsServiceClient` van het object `getDocumentUsageRights` aan te roepen en het object `com.adobe.idp.Document` door te geven dat het PDF-document met toegangsrechten bevat. Deze methode retourneert een `GetUsageRightsResult`-object dat referentie-informatie bevat.
   * Haal de datum op waarna de referentie niet meer geldig is door de methode `GetUsageRightsResult` van het object `getNotAfter` aan te roepen. Deze methode retourneert een `java.util.Date`-object dat de datum vertegenwoordigt waarna de referentie niet langer geldig is.
   * Haal het bericht op dat in Adobe Reader wordt weergegeven wanneer het PDF-document waarvoor rechten zijn ingeschakeld, wordt geopend door de methode `GetUsageRightsResult` van het object `getMessage` aan te roepen. Deze methode retourneert een tekenreekswaarde die het bericht vertegenwoordigt.

**Zie ook**

[Referentiegegevens ophalen](assigning-usage-rights.md#retrieving-credential-information)

[Snel starten (SOAP-modus): Crediteringsgegevens ophalen met de Java API](/help/forms/developing/acrobat-reader-dc-extensions-service.md#quick-start-soap-mode-retrieving-credential-information-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Crediteringsgegevens ophalen met de API {#retrieve-credential-information-using-the-web-service-api} van de webservice

Retrificatiegegevens ophalen met de Acrobat Reader DC Extension API (webservice):

1. Inclusief projectbestanden.

   Creeer een project van Microsoft .NET dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/ReaderExtensionsService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervang `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een Acrobat Reader DC Extension Client-object.

   * Maak een `ReaderExtensionsServiceClient`-object met de standaardconstructor.
   * Maak een `ReaderExtensionsServiceClient.Endpoint.Address`-object met de constructor `System.ServiceModel.EndpointAddress`. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/ReaderExtensionsService?blob=mtom`). Zorg ervoor dat u `?blob=mtom` opgeeft.)
   * Maak een `System.ServiceModel.BasicHttpBinding`-object door de waarde van het veld `ReaderExtensionsServiceClient.Endpoint.Binding` op te halen. Cast de terugkeerwaarde aan `BasicHttpBinding`.
   * Stel het veld `System.ServiceModel.BasicHttpBinding` van het object `MessageEncoding` in op `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam voor het AEM aan het veld `ReaderExtensionsServiceClient.ClientCredentials.UserName.UserName` toe.
      * Wijs de overeenkomstige wachtwoordwaarde aan het gebied `ReaderExtensionsServiceClient.ClientCredentials.UserName.Password` toe.
      * Wijs de constante waarde `HttpClientCredentialType.Basic` aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType` toe.
      * Wijs de constante waarde `BasicHttpSecurityMode.TransportCredentialOnly` aan het veld `BasicHttpBindingSecurity.Security.Mode` toe.

1. Een PDF-document ophalen.

   * Maak een `BLOB`-object met de constructor ervan. Met het object `BLOB` wordt een PDF-document met toegangsrechten opgeslagen.
   * Maak een `System.IO.FileStream`-object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie vertegenwoordigt van het PDF-document waarvoor rechten zijn ingeschakeld en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van het object `System.IO.FileStream` wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de eigenschap `System.IO.FileStream` van het object `Length` op te halen.
   * Vul de bytearray met streamgegevens door de methode `Read` van het object `System.IO.FileStream` aan te roepen en de bytearray, de startpositie en de lengte van de stream door te geven om te lezen.
   * Vul het object `BLOB` door de eigenschap `MTOM` ervan toe te wijzen met de inhoud van de bytearray.

1. Gebruiksrechten verwijderen uit het PDF-document.

   * Haal informatie op over de referentie die wordt gebruikt om gebruiksrechten toe te passen op het PDF-document door de methode `ReaderExtensionsServiceClient` van het object `getDocumentUsageRights` aan te roepen en het object `com.adobe.idp.Document` door te geven dat het PDF-document met toegangsrechten bevat. Deze methode retourneert een `GetUsageRightsResult`-object dat referentie-informatie bevat.
   * Haal de datum op waarna de referentie niet meer geldig is door de waarde op te halen van het `GetUsageRightsResult` gegevenslid van het object. `notAfter` Het gegevenstype van dit gegevenslid is `System.DateTime`.
   * Haal het bericht op dat wordt weergegeven wanneer het PDF-document waarvoor rechten zijn ingeschakeld in Adobe Reader wordt geopend door de waarde van het `GetUsageRightsResult`-gegevenslid van het object op te halen. `message` Het gegevenstype van dit gegevenslid is een tekenreeks.
   * Haal het aantal keren op dat de referentie wordt gebruikt door de waarde op te halen van het `GetUsageRightsResult`-gegevenslid van het object. `useCount` Het gegevenstype van dit gegevenslid is een geheel getal.

**Zie ook**

[Referentiegegevens ophalen](assigning-usage-rights.md#retrieving-credential-information)

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)
