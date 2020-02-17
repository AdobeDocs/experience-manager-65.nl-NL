---
title: Gebruiksrechten toewijzen
seo-title: Gebruiksrechten toewijzen
description: 'null'
seo-description: 'null'
uuid: 8c2020df-ea3c-49fa-916f-38a458f40d2b
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 9e8db506-9ace-4e1f-8a7b-c4e9b15dde7e
translation-type: tm+mt
source-git-commit: 413af4ef9bc3652e05da78d622183bcf20a8bee7

---


# Gebruiksrechten toewijzen {#assigning-usage-rights}

## Over de Acrobat Reader DC-extensieservice {#about-the-acrobat-reader-dc-extensions-service}

Met de Acrobat Reader DC-extensieservice kan uw organisatie eenvoudig interactieve PDF-documenten delen door de functionaliteit van Adobe Reader uit te breiden. De Acrobat Reader DC-extensieservice biedt volledige ondersteuning voor alle PDF-documenten, tot en met PDF 1.7. Het werkt met Adobe Reader 7.0 en hoger. De service voegt gebruiksrechten toe aan een PDF-document en activeert functies die gewoonlijk niet beschikbaar zijn wanneer een PDF-document wordt geopend met Adobe Reader. Gebruikers van derden hebben geen extra software of plug-ins nodig om met documenten waarvoor rechten zijn ingeschakeld te kunnen werken.

U kunt deze taken uitvoeren met de Acrobat Reader DC-extensieservice:

* Gebruiksrechten toepassen op PDF-documenten. Zie Gebruiksrechten [toepassen op PDF-documenten](assigning-usage-rights.md#applying-usage-rights-to-pdf-documents)voor meer informatie.
* Gebruiksrechten verwijderen uit PDF-documenten. Zie Gebruiksrechten [verwijderen uit PDF-documenten](assigning-usage-rights.md#removing-usage-rights-from-pdf-documents)voor meer informatie.
* Crediteringsgegevens ophalen. Zie [Referentiegegevens](assigning-usage-rights.md#retrieving-credential-information)ophalen voor meer informatie.

>[!NOTE]
>
>Zie [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63)voor meer informatie over de Acrobat Reader DC extensions-service.

## Gebruiksrechten toepassen op PDF-documenten {#applying-usage-rights-to-pdf-documents}

U kunt gebruiksrechten toepassen op PDF-documenten met de Acrobat Reader DC-extensies Java Client API en webservice. Gebruiksrechten hebben betrekking op functionaliteit die standaard beschikbaar is in Acrobat, maar niet in Adobe Reader, zoals de mogelijkheid om opmerkingen toe te voegen aan een formulier of formuliervelden in te vullen en het formulier op te slaan. PDF-documenten waarop gebruiksrechten zijn toegepast, worden documenten met ingeschakelde rechten genoemd. Een gebruiker die een document met ingeschakelde rechten opent in Adobe Reader, kan bewerkingen uitvoeren die zijn ingeschakeld voor dat specifieke document.

>[!NOTE]
>
>Wanneer u gebruiksrechten toepast op PDF-documenten met de `applyUsageRights` methode, die deel uitmaakt van de Java API, kunt u de `isModeFinal` parameter van het `ReaderExtensionsOptionSpec` object instellen op `false`. Hierdoor worden de verwerkte formulieren niet bijgewerkt en verbeteren de prestaties. Als u niet bezorgd bent over het bijwerken van de verwerkte teller van de vormen, adviseert men dat u de `isModeFinal` parameter aan `false`.

>[!NOTE]
>
>Zie [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63)voor meer informatie over de Acrobat Reader DC extensions-service.

### Overzicht van de stappen {#summary-of-steps}

Voer de volgende stappen uit om gebruiksrechten toe te passen op een PDF-document:

1. Inclusief projectbestanden.
1. Maak een Client-object voor Acrobat Reader DC-extensies.
1. Een PDF-document ophalen.
1. Geef de gebruiksrechten op die u wilt toepassen.
1. Gebruiksrechten toepassen op het PDF-document.
1. Sla het PDF-document waarvoor rechten zijn ingeschakeld op.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u ervoor zorgen dat u de proxybestanden opneemt.

**Acrobat Reader DC-extensies maken voor een Client-object**

Als u een Acrobat Reader DC-extensieserbewerking programmatisch wilt uitvoeren, moet u een Acrobat Reader DC-extensieserservice-clientobject maken. Als u de Java API voor Acrobat Reader DC-extensies gebruikt, maakt u een `ReaderExtensionsServiceClient` object. Als u de webservice-API voor Acrobat Reader DC-extensies gebruikt, maakt u een `ReaderExtensionsServiceService` object.

**Een PDF-document ophalen**

U moet een PDF-document ophalen om gebruiksrechten toe te passen. PDF-documenten met rechten bevatten een gebruiksrechtenwoordenboek. Wanneer Adobe Reader een document met een dergelijk woordenboek opent, worden alleen de gebruiksrechten ingeschakeld die in het woordenboek voor dat document zijn opgegeven. Als het document geen gebruiksrechtenwoordenboek bevat, maakt de service voor Acrobat Reader DC-extensies er een. Als het al een woordenboek bevat, overschrijft de Acrobat Reader DC-extensieservice bestaande gebruiksrechten met de gebruiksrechten die u opgeeft. In het woordenboek wordt opgegeven welke gebruiksrechten zijn ingeschakeld. Wanneer een gebruiker het document in Adobe Reader opent, zijn alleen de gebruiksrechten toegestaan die in het woordenboek zijn opgegeven.

**Gebruiksrechten opgeven om toe te passen**

De gebruiksrechten die u kunt instellen, worden bepaald door een referentie die u koopt bij Adobe Systems Incorporated. Referenties geven doorgaans toestemming om een groep gerelateerde gebruiksrechten in te stellen, zoals rechten die betrekking hebben op interactieve formulieren. Elke referentie biedt het recht om een bepaald aantal PDF-documenten te maken waarvoor rechten zijn ingeschakeld. Een evaluatiereferentie geeft het recht om een onbeperkt aantal ontwerpdocumenten tot stand te brengen.

>[!NOTE]
>
>Als u probeert om een gebruiksrecht toe te wijzen dat niet door uw referentie wordt toegelaten, zult u een uitzondering veroorzaken.

**Gebruikersrechten toepassen op het PDF-document**

Als u gebruiksrechten wilt toepassen op een PDF-document, verwijst u naar de alias van de referentie die u gebruikt om gebruiksrechten toe te passen (een referentie wordt meestal geïnstalleerd tijdens de installatie van AEM Forms). U moet ook het PDF-document opgeven waarop gebruiksrechten worden toegepast. Voor informatie over het vormen van een referentie, zie de het installeren en opstellen gids voor uw toepassingsserver.

**PDF-document met ingeschakelde rechten opslaan**

Nadat de Acrobat Reader DC-extensieservice gebruiksrechten heeft toegepast op een PDF-document, kunt u het PDF-document met toegangsrechten opslaan als een PDF-bestand.

**Zie ook**

[Gebruiksrechten toepassen met de Java API](assigning-usage-rights.md#apply-usage-rights-using-the-java-api)

[Gebruiksrechten toepassen met de webservice-API](assigning-usage-rights.md#apply-usage-rights-using-the-web-service-api)

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Acrobat Reader DC Extensions Service API - Snel starten](/help/forms/developing/acrobat-reader-dc-extensions-service.md#acrobat-reader-dc-extensions-service-java-api-quick-start-soap)

### Gebruiksrechten toepassen met de Java API {#apply-usage-rights-using-the-java-api}

Gebruiksrechten toepassen op een PDF-document met de Acrobat Reader DC Extensions-API (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden, zoals adobe-reader-extensions-client.jar, op in het klassenpad van uw Java-project.

1. Maak een Client-object voor Acrobat Reader DC-extensies.

   * Maak een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Maak een `ReaderExtensionsServiceClient` object door de constructor ervan te gebruiken en het `ServiceClientFactory` object door te geven.

1. Een PDF-document ophalen.

   * Maak een `java.io.FileInputStream` object dat het PDF-document vertegenwoordigt met behulp van de constructor en geef een tekenreekswaarde door die de locatie van het PDF-document aangeeft.
   * Maak een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en het `java.io.FileInputStream` object door te geven.

1. Geef de gebruiksrechten op die u wilt toepassen.

   * Maak een `UsageRights` object dat gebruiksrechten vertegenwoordigt met de constructor ervan.
   * Roep voor elk gebruiksrecht een methode aan die bij het `UsageRights` object hoort. Als u bijvoorbeeld het `enableFormFillIn` gebruiksrecht wilt toevoegen, roept u de `UsageRights` methode van het `enableFormFillIn` object aan en geeft u deze door `true`. (Herhaal deze stap voor elk gebruiksrecht dat u wilt toepassen.)

1. Gebruiksrechten toepassen op het PDF-document.

   * Maak een `ReaderExtensionsOptionSpec` object met de constructor ervan. Dit object bevat uitvoeringsopties die worden vereist door de Acrobat Reader DC-extensieservice. Wanneer u deze constructor oproept, moet u de volgende waarden opgeven:

      * Het `UsageRights` object dat de gebruiksrechten bevat die op het document moeten worden toegepast.
      * Een tekenreekswaarde die een bericht opgeeft dat wordt weergegeven wanneer het PDF-document waarvoor rechten zijn ingeschakeld, wordt geopend in Adobe Reader 7.x. Dit bericht wordt niet weergegeven in Adobe Reader 8.0.
   * Pas gebruiksrechten toe op het PDF-document door de methode van het `ReaderExtensionsServiceClient` `applyUsageRights` object aan te roepen en de volgende waarden door te geven:

      * Het `com.adobe.idp.Document` object dat het PDF-document bevat waarop gebruiksrechten worden toegepast.
      * Een tekenreekswaarde die de alias van de referentie opgeeft waarmee u gebruiksrechten kunt toepassen.
      * Een tekenreekswaarde die de bijbehorende wachtwoordwaarde opgeeft. (Deze parameter wordt momenteel genegeerd. U kunt doorgeven `null`.)
   * Het `ReaderExtensionsOptionSpec` object dat uitvoeringsopties bevat.
   De `applyUsageRights` methode retourneert een `com.adobe.idp.Document` object dat het PDF-document met toegangsrechten bevat.

1. Sla het PDF-document waarvoor rechten zijn ingeschakeld op.

   * Maak een `java.io.File` object en zorg dat de bestandsextensie .pdf is.
   * Roep de `com.adobe.idp.Document` methode van het `copyToFile` object aan om de inhoud van het `com.adobe.idp.Document` object naar het bestand te kopiëren (zorg dat u het `com.adobe.idp.Document` object gebruikt dat door de `applyUsageRights` methode is geretourneerd).

**Zie ook**

[Gebruiksrechten toepassen op PDF-documenten](assigning-usage-rights.md#applying-usage-rights-to-pdf-documents)

[Snel starten (SOAP-modus):gebruiksrechten toepassen met de Java API](/help/forms/developing/acrobat-reader-dc-extensions-service.md#quick-start-soap-mode-applying-usage-rights-using-the-java-api)

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Gebruiksrechten toepassen met de webservice-API {#apply-usage-rights-using-the-web-service-api}

Gebruiksrechten toepassen op een PDF-document met de Acrobat Reader DC Extensions-API (webservice):

1. Inclusief projectbestanden.

   Creeer een project van Microsoft .NET dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/ReaderExtensionsService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een Client-object voor Acrobat Reader DC-extensies.

   * Maak een `ReaderExtensionsServiceClient` object met de standaardconstructor.
   * Maak een `ReaderExtensionsServiceClient.Endpoint.Address` object met de `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde door die de WSDL opgeeft voor de service AEM Forms (bijvoorbeeld `http://localhost:8080/soap/services/ReaderExtensionsService?blob=mtom`). Zorg ervoor dat u opgeeft `?blob=mtom`.)
   * Maak een `System.ServiceModel.BasicHttpBinding` object door de waarde van het `ReaderExtensionsServiceClient.Endpoint.Binding` veld op te halen. Kiezen naar de geretourneerde waarde `BasicHttpBinding`.
   * Stel het `System.ServiceModel.BasicHttpBinding` veld van het `MessageEncoding` object in op `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam voor AEM-formulieren toe aan het veld `ReaderExtensionsServiceClient.ClientCredentials.UserName.UserName`.
      * Wijs de bijbehorende wachtwoordwaarde aan het veld toe `ReaderExtensionsServiceClient.ClientCredentials.UserName.Password`.
      * Wijs de constante waarde toe `HttpClientCredentialType.Basic` aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Wijs de constante waarde toe `BasicHttpSecurityMode.TransportCredentialOnly` aan het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Een PDF-document ophalen.

   * Maak een `BLOB` object met de constructor ervan. Het `BLOB` object wordt gebruikt om een PDF-document op te slaan waarop gebruiksrechten worden toegepast.
   * Maak een `System.IO.FileStream` object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het PDF-document en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van het `System.IO.FileStream` object wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` eigenschap van het `Length` object op te halen.
   * Vul de bytearray met streamgegevens door de `System.IO.FileStream` `Read` methode van het object aan te roepen. Geef de bytearray, de startpositie en de streamlengte door om te lezen.
   * Vul het `BLOB` object door de `MTOM` eigenschap ervan toe te wijzen met de inhoud van de bytearray.

1. Geef de gebruiksrechten op die u wilt toepassen.

   * Maak een `UsageRights` object dat gebruiksrechten vertegenwoordigt met de constructor ervan.
   * Voor elk gebruiksrecht om toe te passen, wijs de waarde `true` aan het overeenkomstige gegevenslid toe dat tot het `UsageRights` voorwerp behoort. Als u bijvoorbeeld het gebruiksrecht wilt toevoegen, wijst u `enableFormFillIn` het toe aan het `true` gegevenslid van het `UsageRights` `enableFormFillIn` object. (Herhaal deze stap voor elk gebruiksrecht dat u wilt toepassen.)

1. Gebruiksrechten toepassen op het PDF-document.

   * Maak een `ReaderExtensionsOptionSpec` object met de constructor ervan. Dit object bevat uitvoeringsopties die worden vereist door de Acrobat Reader DC-extensieservice.
   * Wijs het `UsageRights` object toe aan het `ReaderExtensionsOptionSpec` gegevenslid van het object `usageRights` .
   * Wijs een tekenreekswaarde toe die het bericht aangeeft dat een gebruiker ziet wanneer het PDF-document met toegangsrechten in Adobe Reader wordt geopend voor het `ReaderExtensionsOptionSpec` gegevenslid van het `message` object.
   * Pas gebruiksrechten toe op het PDF-document door de methode van het `ReaderExtensionsServiceClient` `applyUsageRights` object aan te roepen en de volgende waarden door te geven:

      * Het `BLOB` object dat het PDF-document bevat waarop gebruiksrechten worden toegepast.
      * Een tekenreekswaarde die de alias van de referentie opgeeft waarmee u gebruiksrechten kunt toepassen.
      * Een tekenreekswaarde die de bijbehorende wachtwoordwaarde opgeeft. (Deze parameter wordt momenteel genegeerd. U kunt doorgeven `null`.)
   * Het `ReaderExtensionsOptionSpec` object dat uitvoeringsopties bevat.
   De `applyUsageRights` methode retourneert een `BLOB` object dat het PDF-document met toegangsrechten bevat.

1. Sla het PDF-document waarvoor rechten zijn ingeschakeld op.

   * Maak een `System.IO.FileStream` object door de constructor ervan aan te roepen. Geef een tekenreekswaarde door die de bestandslocatie van het PDF-document met toegangsrechten vertegenwoordigt.
   * Maak een bytearray met de gegevensinhoud van het `BLOB` object dat door de `applyUsageRights` methode is geretourneerd. Vul de bytearray met de waarde van het `BLOB` `MTOM` gegevenslid van het object.
   * Maak een `System.IO.BinaryWriter` object door de constructor ervan aan te roepen en het `System.IO.FileStream` object door te geven.
   * Schrijf de inhoud van de bytearray naar een PDF-bestand door de methode van het `System.IO.BinaryWriter` `Write` object aan te roepen en de bytearray door te geven.

**Zie ook**

[Gebruiksrechten toepassen op PDF-documenten](assigning-usage-rights.md#applying-usage-rights-to-pdf-documents)

[AEM-formulieren aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM-formulieren aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Gebruiksrechten verwijderen uit PDF-documenten {#removing-usage-rights-from-pdf-documents}

U kunt gebruiksrechten verwijderen uit een document waarvoor rechten zijn ingeschakeld. U moet ook gebruiksrechten verwijderen uit een PDF-document waarvoor rechten zijn ingeschakeld om andere bewerkingen in AEM Forms uit te voeren. U moet bijvoorbeeld een PDF-document digitaal ondertekenen (of certificeren) voordat u gebruiksrechten instelt. Als u bewerkingen wilt uitvoeren op een document waarvoor rechten zijn ingeschakeld, moet u daarom gebruiksrechten verwijderen uit het PDF-document, de andere bewerkingen uitvoeren, zoals het digitaal ondertekenen van het document, en vervolgens gebruiksrechten opnieuw toepassen op het document.

>[!NOTE]
>
>Zie [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63)voor meer informatie over de Acrobat Reader DC extensions-service.

### Overzicht van de stappen {#summary_of_steps-1}

Voer de volgende stappen uit om gebruiksrechten te verwijderen uit een PDF-document waarvoor rechten zijn ingeschakeld:

1. Inclusief projectbestanden.
1. Maak een Client-object voor Acrobat Reader DC-extensies.
1. Een PDF-document waarvoor rechten zijn ingeschakeld ophalen.
1. Gebruiksrechten verwijderen uit het PDF-document.
1. Sla het PDF-document op.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u ervoor zorgen dat u de proxybestanden opneemt.

**Acrobat Reader DC-extensies maken voor een Client-object**

Voordat u een servicebewerking voor Acrobat Reader DC-extensies programmatisch kunt uitvoeren, moet u een client-object voor de Acrobat Reader DC-extensieservice maken. Als u de Java API gebruikt, maakt u een `ReaderExtensionsServiceClient` object. Als u de webservice-API voor Acrobat Reader DC-extensies gebruikt, maakt u een `ReaderExtensionsServiceService` object.

**Een PDF-document met ingeschakelde rechten ophalen**

U kunt PDF-documenten waarvoor rechten zijn ingeschakeld, ophalen om gebruiksrechten te verwijderen.

**Gebruikersrechten uit het PDF-document verwijderen**

Nadat u een PDF-document met ingeschakelde rechten hebt opgehaald, kunt u gebruiksrechten verwijderen. Nadat u gebruiksrechten hebt verwijderd, beschikt het PDF-document niet meer over extra functionaliteit wanneer het wordt weergegeven in Adobe Reader.

**Het PDF-document opslaan**

U kunt het PDF-document dat geen gebruiksrechten meer bevat, opslaan als een PDF-bestand. Als het PDF-document eenmaal is opgeslagen als een PDF-bestand, kan het worden weergegeven in Adobe Reader of Acrobat.

**Zie ook**

[Gebruiksrechten verwijderen met de Java API](assigning-usage-rights.md#remove-usage-rights-using-the-java-api)

[Gebruiksrechten verwijderen met de webservice-API](assigning-usage-rights.md#remove-usage-rights-using-the-web-service-api)

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Acrobat Reader DC Extensions Service API - Snel starten](/help/forms/developing/acrobat-reader-dc-extensions-service.md#acrobat-reader-dc-extensions-service-java-api-quick-start-soap)

[Gebruiksrechten toepassen op PDF-documenten](assigning-usage-rights.md#applying-usage-rights-to-pdf-documents)

### Gebruiksrechten verwijderen met de Java API {#remove-usage-rights-using-the-java-api}

Gebruiksrechten verwijderen uit een PDF-document waarvoor rechten zijn ingeschakeld, met de API (Java) voor Acrobat Reader DC-extensies:

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-reader-extensions-client.jar, op in het klassenpad van uw Java-project.

1. Maak een Client-object voor Acrobat Reader DC-extensies.

   Maak een `ReaderExtensionsServiceClient` object door de constructor ervan te gebruiken en een `ServiceClientFactory` object door te geven dat verbindingseigenschappen bevat.

1. Een PDF-document ophalen.

   * Maak een `java.io.FileInputStream` object dat staat voor het PDF-document waarvoor rechten zijn ingeschakeld met behulp van de constructor en geef een tekenreekswaarde door die de locatie van het PDF-document aangeeft.
   * Maak een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en het `java.io.FileInputStream` object door te geven.

1. Gebruiksrechten verwijderen uit het PDF-document.

   Verwijder gebruiksrechten uit het PDF-document door de `ReaderExtensionsServiceClient` methode van het `removeUsageRights` object aan te roepen en het `com.adobe.idp.Document` object met het PDF-document waarvoor rechten zijn ingeschakeld door te geven. Deze methode retourneert een `com.adobe.idp.Document` object dat een PDF-document bevat dat geen gebruiksrechten heeft.

1. Gebruiksrechten toepassen op het PDF-document.

   * Maak een `java.io.File` object en zorg dat de bestandsextensie .PDF is.
   * Roep de `Document` methode van het `copyToFile` object aan om de inhoud van het `Document` object naar het bestand te kopiëren (zorg dat u het `Document` object gebruikt dat door de `removeUsageRights` methode is geretourneerd).

**Zie ook**

[Gebruiksrechten verwijderen uit PDF-documenten](assigning-usage-rights.md#removing-usage-rights-from-pdf-documents)

[Snel starten (SOAP-modus): Gebruiksrechten verwijderen uit een PDF-document met de Java API](/help/forms/developing/acrobat-reader-dc-extensions-service.md#quick-start-soap-mode-removing-usage-rights-from-a-pdf-document-using-the-java-api)

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Gebruiksrechten verwijderen met de webservice-API {#remove-usage-rights-using-the-web-service-api}

Verwijder gebruiksrechten uit een PDF-document waarvoor rechten zijn ingeschakeld met de API (webservice) voor Acrobat Reader DC-extensies:

1. Inclusief projectbestanden.

   Creeer een project van Microsoft .NET dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/ReaderExtensionsService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een Client-object voor Acrobat Reader DC-extensies.

   * Maak een `ReaderExtensionsServiceClient` object met de standaardconstructor.
   * Maak een `ReaderExtensionsServiceClient.Endpoint.Address` object met de `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde door die de WSDL opgeeft voor de service AEM Forms (bijvoorbeeld `http://localhost:8080/soap/services/ReaderExtensionsService?blob=mtom`). Zorg ervoor dat u opgeeft `?blob=mtom`.)
   * Maak een `System.ServiceModel.BasicHttpBinding` object door de waarde van het `ReaderExtensionsServiceClient.Endpoint.Binding` veld op te halen. Kiezen naar de geretourneerde waarde `BasicHttpBinding`.
   * Stel het `System.ServiceModel.BasicHttpBinding` veld van het `MessageEncoding` object in op `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam voor AEM-formulieren toe aan het veld `ReaderExtensionsServiceClient.ClientCredentials.UserName.UserName`.
      * Wijs de bijbehorende wachtwoordwaarde aan het veld toe `ReaderExtensionsServiceClient.ClientCredentials.UserName.Password`.
      * Wijs de constante waarde toe `HttpClientCredentialType.Basic` aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Wijs de constante waarde toe `BasicHttpSecurityMode.TransportCredentialOnly` aan het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Een PDF-document ophalen.

   * Maak een `BLOB` object met de constructor ervan. Het `BLOB` object wordt gebruikt om het PDF-document met toegangsrechten op te slaan waaruit gebruiksrechten worden verwijderd.
   * Maak een `System.IO.FileStream` object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het PDF-document en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van het `System.IO.FileStream` object wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` eigenschap van het `Length` object op te halen.
   * Vul de bytearray met streamgegevens door de methode van het `System.IO.FileStream` `Read` object aan te roepen en de bytearray, de startpositie en de lengte van de stream door te geven om te lezen.
   * Vul het `BLOB` object door de `MTOM` eigenschap ervan toe te wijzen met de inhoud van de bytearray.

1. Gebruiksrechten verwijderen uit het PDF-document.

   Verwijder gebruiksrechten uit het PDF-document door de `ReaderExtensionsServiceClient` methode van het `removeUsageRights` object aan te roepen en het `BLOB` object met het PDF-document waarvoor rechten zijn ingeschakeld door te geven. Deze methode retourneert een `BLOB` object dat een PDF-document bevat dat geen gebruiksrechten heeft.

1. Gebruiksrechten toepassen op het PDF-document.

   * Maak een `System.IO.FileStream` object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de locatie van het PDF-bestand vertegenwoordigt.
   * Maak een bytearray met de gegevensinhoud van het `BLOB` object dat door de `removeUsageRights` methode is geretourneerd. Vul de bytearray met de waarde van het `BLOB` `MTOM` gegevenslid van het object.
   * Maak een `System.IO.BinaryWriter` object door de constructor ervan aan te roepen en het `System.IO.FileStream` object door te geven.

**Zie ook**

[Gebruiksrechten verwijderen uit PDF-documenten](assigning-usage-rights.md#removing-usage-rights-from-pdf-documents)

[AEM-formulieren aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM-formulieren aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Referentiegegevens ophalen {#retrieving-credential-information}

U kunt informatie ophalen over de referentie die is gebruikt om gebruiksrechten toe te passen op een PDF-document waarvoor rechten zijn ingeschakeld. Door informatie over een referentie op te halen, kunt u informatie zoals de datum opvragen waarna het certificaat niet meer geldig is.

>[!NOTE]
>
>Zie [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63)voor meer informatie over de Acrobat Reader DC extensions-service.

### Overzicht van de stappen {#summary_of_steps-2}

Voer de volgende stappen uit om informatie op te halen over de referentie die is gebruikt om gebruiksrechten toe te passen op een PDF-document:

1. Inclusief projectbestanden.
1. Maak een Client-object voor Acrobat Reader DC-extensies.
1. Een PDF-document waarvoor rechten zijn ingeschakeld ophalen.
1. Haal informatie op over de referentie.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u ervoor zorgen dat u de proxybestanden opneemt.

**Acrobat Reader DC-extensies maken voor een Client-object**

Voordat u een servicebewerking voor Acrobat Reader DC-extensies programmatisch kunt uitvoeren, moet u een client-object voor de Acrobat Reader DC-extensieservice maken. Als u de Java API gebruikt, maakt u een `ReaderExtensionsServiceClient` object. Als u de webservice-API voor Acrobat Reader DC-extensies gebruikt, maakt u een `ReaderExtensionsServiceService` object.

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

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Acrobat Reader DC Extensions Service API - Snel starten](/help/forms/developing/acrobat-reader-dc-extensions-service.md#acrobat-reader-dc-extensions-service-java-api-quick-start-soap)

### Crediteringsgegevens ophalen met de Java API {#retrieve-credential-information-using-the-java-api}

U kunt met de API voor Acrobat Reader DC-extensies (Java) de referentie-informatie ophalen:

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-reader-extensions-client.jar, op in het klassenpad van uw Java-project.

1. Maak een Client-object voor Acrobat Reader DC-extensies.

   Maak een `ReaderExtensionsServiceClient` object door de constructor ervan te gebruiken en een `ServiceClientFactory` object door te geven dat verbindingseigenschappen bevat.

1. Een PDF-document ophalen.

   * Maak een `java.io.FileInputStream` object dat staat voor het PDF-document waarvoor rechten zijn ingeschakeld met behulp van de constructor en geef een tekenreekswaarde door die de locatie van het PDF-document waarvoor rechten zijn ingeschakeld aangeeft.
   * Maak een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en het `java.io.FileInputStream` object door te geven.

1. Gebruiksrechten verwijderen uit het PDF-document.

   * Haal informatie op over de referentie die wordt gebruikt om gebruiksrechten toe te passen op het PDF-document door de methode van het `ReaderExtensionsServiceClient` object aan te roepen en het `getDocumentUsageRights` `com.adobe.idp.Document` object met het PDF-document waarvoor rechten zijn ingeschakeld door te geven. Deze methode retourneert een `GetUsageRightsResult` object dat referentie-informatie bevat.
   * Haal de datum op waarna de referentie niet meer geldig is door de methode van het `GetUsageRightsResult` `getNotAfter` object aan te roepen. Deze methode retourneert een `java.util.Date` object dat de datum vertegenwoordigt waarna de referentie niet meer geldig is.
   * Haal het bericht op dat in Adobe Reader wordt weergegeven wanneer het PDF-document waarvoor rechten zijn ingeschakeld, wordt geopend door de `GetUsageRightsResult` methode van het `getMessage` object aan te roepen. Deze methode retourneert een tekenreekswaarde die het bericht vertegenwoordigt.

**Zie ook**

[Referentiegegevens ophalen](assigning-usage-rights.md#retrieving-credential-information)

[Snel starten (SOAP-modus): Crediteringsgegevens ophalen met de Java API](/help/forms/developing/acrobat-reader-dc-extensions-service.md#quick-start-soap-mode-retrieving-credential-information-using-the-java-api)

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Crediteringsgegevens ophalen met de webservice-API {#retrieve-credential-information-using-the-web-service-api}

Retrificatiegegevens ophalen met de API (webservice) voor Acrobat Reader DC-extensies:

1. Inclusief projectbestanden.

   Creeer een project van Microsoft .NET dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/ReaderExtensionsService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een Client-object voor Acrobat Reader DC-extensies.

   * Maak een `ReaderExtensionsServiceClient` object met de standaardconstructor.
   * Maak een `ReaderExtensionsServiceClient.Endpoint.Address` object met de `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde door die de WSDL opgeeft voor de service AEM Forms (bijvoorbeeld `http://localhost:8080/soap/services/ReaderExtensionsService?blob=mtom`). Zorg ervoor dat u opgeeft `?blob=mtom`.)
   * Maak een `System.ServiceModel.BasicHttpBinding` object door de waarde van het `ReaderExtensionsServiceClient.Endpoint.Binding` veld op te halen. Kiezen naar de geretourneerde waarde `BasicHttpBinding`.
   * Stel het `System.ServiceModel.BasicHttpBinding` veld van het `MessageEncoding` object in op `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam voor AEM-formulieren toe aan het veld `ReaderExtensionsServiceClient.ClientCredentials.UserName.UserName`.
      * Wijs de bijbehorende wachtwoordwaarde aan het veld toe `ReaderExtensionsServiceClient.ClientCredentials.UserName.Password`.
      * Wijs de constante waarde toe `HttpClientCredentialType.Basic` aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * Wijs de constante waarde toe `BasicHttpSecurityMode.TransportCredentialOnly` aan het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Een PDF-document ophalen.

   * Maak een `BLOB` object met de constructor ervan. Met dit `BLOB` object wordt een PDF-document met toegangsrechten opgeslagen.
   * Maak een `System.IO.FileStream` object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie vertegenwoordigt van het PDF-document waarvoor rechten zijn ingeschakeld en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van het `System.IO.FileStream` object wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` eigenschap van het `Length` object op te halen.
   * Vul de bytearray met streamgegevens door de methode van het `System.IO.FileStream` `Read` object aan te roepen en de bytearray, de startpositie en de lengte van de stream door te geven om te lezen.
   * Vul het `BLOB` object door de `MTOM` eigenschap ervan toe te wijzen met de inhoud van de bytearray.

1. Gebruiksrechten verwijderen uit het PDF-document.

   * Haal informatie op over de referentie die wordt gebruikt om gebruiksrechten toe te passen op het PDF-document door de methode van het `ReaderExtensionsServiceClient` object aan te roepen en het `getDocumentUsageRights` `com.adobe.idp.Document` object met het PDF-document waarvoor rechten zijn ingeschakeld door te geven. Deze methode retourneert een `GetUsageRightsResult` object dat referentie-informatie bevat.
   * Haal de datum op waarna de referentie niet meer geldig is door de waarde van het `GetUsageRightsResult` `notAfter` gegevenslid van het object op te halen. Het gegevenstype van dit gegevenslid is `System.DateTime`.
   * Haal het bericht op dat wordt weergegeven wanneer het PDF-document waarvoor rechten zijn ingeschakeld in Adobe Reader wordt geopend door de waarde van het `GetUsageRightsResult` gegevenslid van het `message` object op te halen. Het gegevenstype van dit gegevenslid is een tekenreeks.
   * Haal het aantal keren op dat de referentie wordt gebruikt door de waarde van het `GetUsageRightsResult` `useCount` gegevenslid van het object op te halen. Het gegevenstype van dit gegevenslid is een geheel getal.

**Zie ook**

[Referentiegegevens ophalen](assigning-usage-rights.md#retrieving-credential-information)

[AEM-formulieren aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM-formulieren aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)
