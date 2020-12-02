---
title: Gebruikers beheren
seo-title: Gebruikers beheren
description: 'null'
seo-description: 'null'
uuid: 68d8a0bc-6e3d-4286-ba5c-534dcf58cb84
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 95804bff-9e6f-4807-aae4-790bd9e7cb57
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '6191'
ht-degree: 0%

---


# Gebruikers {#managing-users} beheren

**Over Gebruikersbeheer**

U kunt de API voor gebruikersbeheer gebruiken om clienttoepassingen te maken die rollen, machtigingen en hoofden (die gebruikers of groepen kunnen zijn) kunnen beheren en om gebruikers te verifiëren. Gebruikersbeheer-API bestaat uit de volgende AEM Forms API&#39;s:

* Directory Manager-service-API
* API voor verificatiebeheer
* Authorization Manager Service API

Het Beheer van de gebruiker laat u toe om, rollen en toestemmingen toe te wijzen te verwijderen en te bepalen. Het laat u ook toe om, domeinen, gebruikers, en groepen toe te wijzen te verwijderen. Tot slot kunt u Gebruikersbeheer gebruiken om gebruikers voor authentiek te verklaren.

In [Het toevoegen van Gebruikers](users.md#adding-users) zult u begrijpen hoe te om gebruikers programmatically toe te voegen. In deze sectie wordt de directoryservice-API gebruikt.

In [Het schrappen van Gebruikers](users.md#deleting-users) zult u begrijpen hoe te om gebruikers programmatically te schrappen. In deze sectie wordt de directoryservice-API gebruikt.

In [Gebruikers en groepen beheren](users.md#managing-users-and-groups) zult u het verschil tussen een lokale gebruiker en een foldergebruiker begrijpen, en zult voorbeelden van zien hoe te om Java en de dienst APIs van het Web te gebruiken om gebruikers en groepen programmatically te beheren. In deze sectie wordt de directoryservice-API gebruikt.

In [Managing Roles and Permissions](users.md#managing-roles-and-permissions) zult u over de systeemrollen en toestemmingen leren en wat u programmatically kunt doen om hen te verhogen, en voorbeelden zien van hoe te om Java en de Webdienst APIs te gebruiken om rollen en toestemmingen programmatically te beheren. Deze sectie gebruikt zowel de API van de Dienst van de Manager van de Folder als de Dienst API van de Manager van de Vergunning.

In [Gebruikers verifiëren](users.md#authenticating-users) zult u voorbeelden zien van hoe te om Java en de dienst APIs van het Web te gebruiken om gebruikers programmatically voor authentiek te verklaren. Deze sectie gebruikt de Service API van de Manager van de Vergunning.

**Het verificatieproces begrijpen**

Gebruikersbeheer biedt ingebouwde verificatiefunctionaliteit en biedt u ook de mogelijkheid om deze te verbinden met uw eigen verificatieprovider. Wanneer het Beheer van de Gebruiker een authentificatieverzoek ontvangt (bijvoorbeeld, probeert een gebruiker om binnen te registreren), gaat het gebruikersinformatie tot de authentificatieleverancier over om voor authentiek te verklaren. Gebruikersbeheer ontvangt de resultaten van de verificatieprovider nadat de gebruiker is geverifieerd.

Het volgende diagram toont de interactie onder een eind - gebruiker die aan login, Gebruikersbeheer, en de authentificatieleverancier probeert.

![mu_mu_umauth_process](assets/mu_mu_umauth_process.png)

De volgende lijst beschrijft elke stap van het authentificatieproces.

<table>
 <thead>
  <tr>
   <th><p>Stap</p></th>
   <th><p>Beschrijving</p></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p>1</p></td>
   <td><p>Een gebruiker probeert om in de dienst te registreren die Gebruikersbeheer aanhaalt. De gebruiker geeft een gebruikersnaam en wachtwoord op. </p></td>
  </tr>
  <tr>
   <td><p>2</p></td>
   <td><p>Het Beheer van de gebruiker verzendt de gebruikersnaam en het wachtwoord, evenals configuratieinformatie, naar de authentificatieleverancier.</p></td>
  </tr>
  <tr>
   <td><p>3</p></td>
   <td><p>De verificatieprovider maakt verbinding met de gebruikerswinkel en verifieert de gebruiker.</p></td>
  </tr>
  <tr>
   <td><p>4</p></td>
   <td><p>De verificatieprovider retourneert de resultaten naar Gebruikersbeheer.</p></td>
  </tr>
  <tr>
   <td><p>5</p></td>
   <td><p>Met Gebruikersbeheer kan de gebruiker zich aanmelden of toegang tot het product weigeren.</p></td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Als de servertijdzone van de cliënttijdzone verschillend is, wanneer het verbruiken van WSDL voor AEM Forms produceert de dienst PDF op een inheemse stapel van de ZEEP gebruikend een .NET cliënt op een cluster van de Server van de Toepassing WebSphere, kan de volgende de authentificatiefout van het Beheer van de Gebruiker voorkomen:

`[com.adobe.idp.um.webservices.WSSecurityHandler] errorCode:12803 errorCodeHEX:0x3203 message:WSSecurityHandler: UM authenticate returns exception : An error was discovered processing the <wsse:Security> header. (WSSecurityEngine: Invalid timestamp The security semantics of message have expired).`

**Directorybeheer**

Gebruikersbeheer wordt verpakt met een directoryserviceprovider (de DirectoryManagerService) die verbindingen met LDAP-directory&#39;s ondersteunt. Als uw organisatie een niet-LDAP-opslagplaats gebruikt om gebruikersverslagen op te slaan, kunt u uw eigen folder dienstverlener tot stand brengen die met uw bewaarplaats werkt.

De dienstverleners van de folder winnen verslagen van een gebruikersopslag op verzoek van het Beheer van de Gebruiker terug. Gebruikersbeheer slaat gebruikers- en groepsrecords in de database regelmatig in de cache op om de prestaties te verbeteren.

De provider van de directoryservice kan worden gebruikt om de gebruikersbeheerdatabase te synchroniseren met de opslag van de gebruiker. Deze stap zorgt ervoor dat alle informatie van de gebruikersfolder en alle gebruiker en groepsverslagen bijgewerkt zijn.

Bovendien voorziet DirectoryManagerService u van de capaciteit om domeinen tot stand te brengen en te beheren. Domeinen definiëren verschillende gebruikersbasen. De grens van een domein wordt gewoonlijk bepaald volgens de manier uw organisatie gestructureerd is of hoe uw gebruikersopslag opstelling is. De domeinen van het Beheer van de gebruiker verstrekken configuratiemontages die de authentificatieleveranciers en de leveranciers van de folderdienst gebruiken.

In de configuratie XML die het Beheer van de Gebruiker uitvoert, bevat de wortelknoop die de attributenwaarde van `Domains` heeft een element van XML voor elk domein dat voor Gebruikersbeheer wordt bepaald. Elk van deze elementen bevat andere elementen die aspecten van het domein verbonden aan specifieke dienstverleners bepalen.

**Werken met objectSID-waarden**

Wanneer het gebruiken van Actieve Folder, is het belangrijk om te begrijpen dat een `objectSID` waarde geen uniek attribuut over veelvoudige domeinen is. Met deze waarde wordt de beveiligings-id van een object opgeslagen. In een omgeving met meerdere domeinen (bijvoorbeeld een structuur met domeinen) kan de waarde `objectSID` verschillend zijn.

Een `objectSID` waarde zou veranderen als een voorwerp van één Actief domein van de Folder aan een ander domein wordt bewogen. Sommige objecten hebben overal in het domein dezelfde `objectSID`-waarde. Groepen zoals BUILTIN\Administrators, BUILTIN\Power Users enzovoort zouden bijvoorbeeld dezelfde `objectSID`-waarde hebben, ongeacht de domeinen. Deze `objectSID` waarden zijn bekend.

## Gebruikers {#adding-users} toevoegen

U kunt de API voor directoryservice (Java en webservice) gebruiken om gebruikers programmatisch aan AEM Forms toe te voegen. Nadat u een gebruiker hebt toegevoegd, kunt u die gebruiker gebruiken wanneer u een servicebewerking uitvoert waarvoor een gebruiker nodig is. U kunt bijvoorbeeld een taak toewijzen aan de nieuwe gebruiker.

### Overzicht van stappen {#summary-of-steps}

Voer de volgende stappen uit om een gebruiker toe te voegen:

1. Inclusief projectbestanden.
1. Creeer een cliënt DirectoryManagerService.
1. Gebruikersgegevens definiëren.
1. Voeg de gebruiker toe aan AEM Forms.
1. Controleer of de gebruiker is toegevoegd.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, neemt u de proxybestanden op.

**Een DirectoryManagerService-client maken**

Alvorens u een de dienstverrichting van de Manager van de Folder programmatically kunt uitvoeren, creeer een cliënt van de Dienst API van de Manager van de Folder.

**Gebruikersgegevens definiëren**

Wanneer u een nieuwe gebruiker door de Dienst API van de Manager van de Folder te gebruiken toevoegt, bepaal informatie voor die gebruiker. Wanneer u een nieuwe gebruiker toevoegt, definieert u doorgaans de volgende waarden:

* **Domeinnaam**: Het domein waartoe de gebruiker behoort (bijvoorbeeld  `DefaultDom`).
* **Waarde** van gebruikersnaam: De id-waarde van de gebruiker (bijvoorbeeld  `wblue`).
* **Principal type**: Het type gebruiker (u kunt bijvoorbeeld opgeven  `USER)`.
* **Voornaam**: Een bepaalde naam voor de gebruiker (bijvoorbeeld  `Wendy`).
* **Familienaam**: De familienaam voor de gebruiker (bijvoorbeeld,  `Blue)`.
* **Landinstelling**: Lokale informatie voor de gebruiker.

**De gebruiker toevoegen aan AEM Forms**

Nadat u gebruikersgegevens hebt gedefinieerd, kunt u de gebruiker aan AEM Forms toevoegen. Als u een gebruiker wilt toevoegen, roept u de methode `createLocalUser` van het object `DirectoryManagerServiceClient` aan.

**Controleren of de gebruiker is toegevoegd**

U kunt controleren of de gebruiker is toegevoegd om ervoor te zorgen dat er geen problemen zijn opgetreden. Zoek de nieuwe gebruiker met de waarde van de gebruikersidentificatie.

**Zie ook**

[Gebruikers toevoegen met de Java API](users.md#add-users-using-the-java-api)

[Gebruikers toevoegen met de webservice-API](users.md#add-users-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Gebruikers verwijderen](users.md#deleting-users)

### Gebruikers toevoegen met de Java-API {#add-users-using-the-java-api}

Voeg gebruikers toe met de API voor directoryservice (Java):

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-usermanager-client.jar, op in het klassenpad van uw Java-project.

1. Creeer een cliënt DirectoryManagerServices.

   Maak een `DirectoryManagerServiceClient`-object door de constructor ervan te gebruiken en een `ServiceClientFactory`-object door te geven dat verbindingseigenschappen bevat.

1. Gebruikersgegevens definiëren.

   * Maak een `UserImpl`-object met de constructor ervan.
   * Stel de naam van het domein in door de methode `setDomainName` van het object `UserImpl` aan te roepen. Geef een tekenreekswaarde door die de domeinnaam opgeeft.
   * Stel het hoofdtype in door de methode `setPrincipalType` van het object `UserImpl` aan te roepen. Geef een tekenreekswaarde door die het type gebruiker aangeeft. U kunt bijvoorbeeld `USER` opgeven.
   * Stel de waarde van de gebruikersidentificatie in door de methode `setUserid` van het object `UserImpl` aan te roepen. Geef een tekenreekswaarde door die de waarde van de gebruikersidentificatie aangeeft. U kunt bijvoorbeeld `wblue` opgeven.
   * Stel de canonieke naam in door de methode `setCanonicalName` van het object `UserImpl` aan te roepen. Geef een tekenreekswaarde door die de canonieke naam van de gebruiker aangeeft. U kunt bijvoorbeeld `wblue` opgeven.
   * Stel de opgegeven naam in door de methode `setGivenName` van het object `UserImpl` aan te roepen. Geef een tekenreekswaarde door die de opgegeven naam van de gebruiker aangeeft. U kunt bijvoorbeeld `Wendy` opgeven.
   * Stel de familienaam in door de methode `setFamilyName` van het object `UserImpl` aan te roepen. Geef een tekenreekswaarde door die de familienaam van de gebruiker aangeeft. U kunt bijvoorbeeld `Blue` opgeven.

   >[!NOTE]
   >
   >Roep een methode aan die bij het object `UserImpl` hoort om andere waarden in te stellen. U kunt bijvoorbeeld de waarde van de landinstelling instellen door de methode `setLocale` van het object `UserImpl` aan te roepen.

1. Voeg de gebruiker toe aan AEM Forms.

   Roep de methode `createLocalUser` van het object `DirectoryManagerServiceClient` aan en geef de volgende waarden door:

   * Het `UserImpl`-object dat de nieuwe gebruiker vertegenwoordigt
   * Een tekenreekswaarde die het wachtwoord van de gebruiker vertegenwoordigt

   De methode `createLocalUser` retourneert een tekenreekswaarde die de lokale waarde van de gebruikersidentificatie opgeeft.

1. Controleer of de gebruiker is toegevoegd.

   * Maak een `PrincipalSearchFilter`-object met de constructor ervan.
   * Stel de waarde van de gebruikersidentificatie in door de methode `setUserId` van het object `PrincipalSearchFilter` aan te roepen. Geef een tekenreekswaarde door die de waarde van de gebruikersidentificatie vertegenwoordigt.
   * Roep de methode `DirectoryManagerServiceClient` van het object `findPrincipals` aan en geef het object `PrincipalSearchFilter` door. Deze methode retourneert een `java.util.List`-instantie, waarbij elk element een `User`-object is. Doorloop de instantie `java.util.List` om de gebruiker te zoeken.

**Zie ook**

[Overzicht van de stappen](users.md#summary-of-steps)

[Snel starten (SOAP-modus): Gebruikers toevoegen met de Java API](/help/forms/developing/user-manager-java-api-quick.md#quick-start-soap-mode-adding-users-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Gebruikers toevoegen met de webservice-API {#add-users-using-the-web-service-api}

Voeg gebruikers toe met de API (webservice) van Directory Manager:

1. Inclusief projectbestanden.

   Creeer een project van Microsoft .NET dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL voor de de dienstverwijzing gebruikt: `http://localhost:8080/soap/services/DirectoryManagerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervang `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Creeer een cliënt DirectoryManagerService.

   * Maak een `DirectoryManagerServiceClient`-object met de standaardconstructor.
   * Maak een `DirectoryManagerServiceClient.Endpoint.Address`-object met de constructor `System.ServiceModel.EndpointAddress`. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/DirectoryManagerService?blob=mtom`). U hoeft het `lc_version`-kenmerk niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt. Zorg ervoor dat u `?blob=mtom` specificeert.
   * Maak een `System.ServiceModel.BasicHttpBinding`-object door de waarde van het veld `DirectoryManagerServiceClient.Endpoint.Binding` op te halen. Cast de terugkeerwaarde aan `BasicHttpBinding`.
   * Stel het veld `System.ServiceModel.BasicHttpBinding` van het object `MessageEncoding` in op `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam voor het AEM aan het veld `DirectoryManagerServiceClient.ClientCredentials.UserName.UserName` toe.
      * Wijs de overeenkomstige wachtwoordwaarde aan het gebied `DirectoryManagerServiceClient.ClientCredentials.UserName.Password` toe.
      * Wijs de constante waarde `HttpClientCredentialType.Basic` aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType` toe.
      * Wijs de constante waarde `BasicHttpSecurityMode.TransportCredentialOnly` aan het veld `BasicHttpBindingSecurity.Security.Mode` toe.

1. Gebruikersgegevens definiëren.

   * Maak een `UserImpl`-object met de constructor ervan.
   * Stel de naam van het domein in door een tekenreekswaarde toe te wijzen aan het veld `UserImpl` van het object.`domainName`
   * Stel het hoofdtype in door een tekenreekswaarde toe te wijzen aan het veld `UserImpl` van het object. `principalType` U kunt bijvoorbeeld `USER` opgeven.
   * Stel de waarde van de gebruikersidentificatie in door een tekenreekswaarde toe te wijzen aan het veld `UserImpl` van het object.`userid`
   * Stel de canonieke naamwaarde in door een tekenreekswaarde toe te wijzen aan het veld `UserImpl` van het object.`canonicalName`
   * Stel de opgegeven naamwaarde in door een tekenreekswaarde toe te wijzen aan het veld `UserImpl` van het object.`givenName`
   * Stel de naam van de familie in door een tekenreekswaarde toe te wijzen aan het veld `UserImpl` van het object.`familyName`

1. Voeg de gebruiker toe aan AEM Forms.

   Roep de methode `createLocalUser` van het object `DirectoryManagerServiceClient` aan en geef de volgende waarden door:

   * Het `UserImpl`-object dat de nieuwe gebruiker vertegenwoordigt
   * Een tekenreekswaarde die het wachtwoord van de gebruiker vertegenwoordigt

   De methode `createLocalUser` retourneert een tekenreekswaarde die de lokale waarde van de gebruikersidentificatie opgeeft.

1. Controleer of de gebruiker is toegevoegd.

   * Maak een `PrincipalSearchFilter`-object met de constructor ervan.
   * Stel de waarde van de gebruikersidentificatie van de gebruiker in door een tekenreekswaarde toe te wijzen die de waarde van de gebruikersidentificatie vertegenwoordigt aan het veld `PrincipalSearchFilter` van het object `userId`.
   * Roep de methode `DirectoryManagerServiceClient` van het object `findPrincipals` aan en geef het object `PrincipalSearchFilter` door. Deze methode keert een `MyArrayOfUser` inzamelingsvoorwerp terug, waar elk element een `User` voorwerp is. Doorloop de verzameling `MyArrayOfUser` om de gebruiker te zoeken.

**Zie ook**

[Overzicht van de stappen](users.md#summary-of-steps)

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Gebruikers {#deleting-users} verwijderen

U kunt de API voor directoryservice (Java en webservice) gebruiken om gebruikers via programmacode uit AEM Forms te verwijderen. Nadat u een gebruiker schrapt, kan de gebruiker niet meer worden gebruikt om een de dienstverrichting uit te voeren die een gebruiker vereist. U kunt bijvoorbeeld geen taak toewijzen aan een verwijderde gebruiker.

### Overzicht van stappen {#summary_of_steps-1}

Voer de volgende stappen uit om een gebruiker te verwijderen:

1. Inclusief projectbestanden.
1. Creeer een cliënt DirectoryManagerService.
1. Geef de gebruiker op die u wilt verwijderen.
1. Verwijder de gebruiker uit AEM Forms.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, neemt u de proxybestanden op.

**Een DirectoryManagerService-client maken**

Alvorens u programmatically een verrichting van de Dienst API van de Manager van de Folder kunt uitvoeren, creeer een de dienstcliënt van de Manager van de Folder.

**De gebruiker opgeven die moet worden verwijderd**

U kunt opgeven dat een gebruiker moet worden verwijderd met de id-waarde van de gebruiker.

**De gebruiker verwijderen uit AEM Forms**

Als u een gebruiker wilt verwijderen, roept u de methode `deleteLocalUser` van het object `DirectoryManagerServiceClient` aan.

**Zie ook**

[Gebruikers verwijderen met de Java API](users.md#delete-users-using-the-java-api)

[Gebruikers verwijderen met de webservice-API](users.md#delete-users-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Gebruikers toevoegen](users.md#adding-users)

### Gebruikers verwijderen met de Java API {#delete-users-using-the-java-api}

Gebruikers verwijderen met de API voor directoryservice (Java):

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-usermanager-client.jar, op in het klassenpad van uw Java-project.

1. Creeer een cliënt DirectoryManagerService.

   Maak een `DirectoryManagerServiceClient`-object door de constructor ervan te gebruiken en een `ServiceClientFactory`-object door te geven dat verbindingseigenschappen bevat.

1. Geef de gebruiker op die u wilt verwijderen.

   * Maak een `PrincipalSearchFilter`-object met de constructor ervan.
   * Stel de waarde van de gebruikersidentificatie in door de methode `setUserId` van het object `PrincipalSearchFilter` aan te roepen. Geef een tekenreekswaarde door die de waarde van de gebruikersidentificatie vertegenwoordigt.
   * Roep de methode `DirectoryManagerServiceClient` van het object `findPrincipals` aan en geef het object `PrincipalSearchFilter` door. Deze methode retourneert een `java.util.List`-instantie, waarbij elk element een `User`-object is. Doorloop de instantie `java.util.List` om te zoeken naar de gebruiker die u wilt verwijderen.

1. Verwijder de gebruiker uit AEM Forms.

   Roep de methode `DirectoryManagerServiceClient` van het object `deleteLocalUser` aan en geef de waarde van het veld `User` van het object `oid` door. Roep de methode `User` van het object `getOid` aan. Gebruik het `User`-object dat is opgehaald uit de instantie `java.util.List`.

**Zie ook**

[Overzicht van de stappen](users.md#summary-of-steps)

[Snel starten (EJB-modus): Gebruikers verwijderen met de Java API](/help/forms/developing/user-manager-java-api-quick.md#quick-start-soap-mode-deleting-users-using-the-java-api)

[Snel starten (SOAP-modus): Gebruikers verwijderen met de Java API](/help/forms/developing/user-manager-java-api-quick.md#quick-start-soap-mode-deleting-users-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Gebruikers verwijderen met de webservice-API {#delete-users-using-the-web-service-api}

Gebruikers verwijderen met de API voor directoryservice (webservice):

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-usermanager-client.jar, op in het klassenpad van uw Java-project.

1. Creeer een cliënt DirectoryManagerService.

   * Maak een `DirectoryManagerServiceClient`-object met de standaardconstructor.
   * Maak een `DirectoryManagerServiceClient.Endpoint.Address`-object met de constructor `System.ServiceModel.EndpointAddress`. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/DirectoryManagerService?blob=mtom`). U hoeft het `lc_version`-kenmerk niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt. Zorg ervoor dat u `blob=mtom.` specificeert
   * Maak een `System.ServiceModel.BasicHttpBinding`-object door de waarde van het veld `DirectoryManagerServiceClient.Endpoint.Binding` op te halen. Cast de terugkeerwaarde aan `BasicHttpBinding`.
   * Stel het veld `System.ServiceModel.BasicHttpBinding` van het object `MessageEncoding` in op `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam voor het AEM aan het veld `DirectoryManagerServiceClient.ClientCredentials.UserName.UserName` toe.
      * Wijs de overeenkomstige wachtwoordwaarde aan het gebied `DirectoryManagerServiceClient.ClientCredentials.UserName.Password` toe.
      * Wijs de constante waarde `HttpClientCredentialType.Basic` aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType` toe.
      * Wijs de constante waarde `BasicHttpSecurityMode.TransportCredentialOnly` aan het veld `BasicHttpBindingSecurity.Security.Mode` toe.

1. Geef de gebruiker op die u wilt verwijderen.

   * Maak een `PrincipalSearchFilter`-object met de constructor ervan.
   * Stel de waarde van de gebruikersidentificatie in door een tekenreekswaarde toe te wijzen aan het veld `PrincipalSearchFilter` van het object.`userId`
   * Roep de methode `DirectoryManagerServiceClient` van het object `findPrincipals` aan en geef het object `PrincipalSearchFilter` door. Deze methode keert een `MyArrayOfUser` inzamelingsvoorwerp terug, waar elk element een `User` voorwerp is. Doorloop de verzameling `MyArrayOfUser` om de gebruiker te zoeken. Het object `User` dat is opgehaald uit het verzamelingsobject `MyArrayOfUser` wordt gebruikt om de gebruiker te verwijderen.

1. Verwijder de gebruiker uit AEM Forms.

   Verwijder de gebruiker door de `User`-veldwaarde van het `oid`-object door te geven aan de `DirectoryManagerServiceClient`-methode van het `deleteLocalUser`-object.

**Zie ook**

[Overzicht van de stappen](users.md#summary-of-steps)

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Groepen maken {#creating-groups}

Met de API voor directorybeheer (Java en webservice) kunt u programmatisch AEM Forms-groepen maken. Nadat u een groep creeert, kunt u die groep gebruiken om een de dienstverrichting uit te voeren die een groep vereist. U kunt bijvoorbeeld een gebruiker aan de nieuwe groep toewijzen. (Zie [Gebruikers en groepen beheren](users.md#managing-users-and-groups).)

### Overzicht van stappen {#summary_of_steps-2}

Voer de volgende stappen uit om een groep te maken:

1. Inclusief projectbestanden.
1. Creeer een cliënt DirectoryManagerService.
1. Bepaal of de groep niet bestaat.
1. Maak de groep.
1. Voer een handeling uit met de groep.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-utilities.jar (Vereist als AEM Forms wordt geïmplementeerd op JBoss)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)

Zie [Including AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files) voor informatie over de locatie van deze JAR-bestanden.

**Een DirectoryManagerService-client maken**

Alvorens u een de dienstverrichting van de Manager van de Folder programmatically kunt uitvoeren, creeer een cliënt van de Dienst API van de Manager van de Folder.

**Bepalen of de groep bestaat**

Wanneer u een groep maakt, moet u ervoor zorgen dat de groep niet in hetzelfde domein bestaat. Twee groepen kunnen dus niet dezelfde naam binnen hetzelfde domein hebben. Voor deze taak voert u een zoekopdracht uit en filtert u de zoekresultaten op basis van twee waarden. Plaats het belangrijkste type aan `com.adobe.idp.um.api.infomodel.Principal.PRINCIPALTYPE_GROUP` om ervoor te zorgen dat slechts de groepen zijn teruggekeerd. Zorg er ook voor dat u de domeinnaam opgeeft.

**De groep maken**

Nadat u hebt bepaald dat de groep niet bestaat in het domein, maakt u de groep en geeft u de volgende kenmerken op:

* **CommonName**: De naam van de groep.
* **Domein**: Het domein waarin de groep wordt toegevoegd.
* **Omschrijving**: Een beschrijving van de groep.

**Een handeling uitvoeren met de groep**

Nadat u een groep hebt gemaakt, kunt u een actie uitvoeren met de groep. U kunt bijvoorbeeld een gebruiker aan de groep toevoegen. Als u een gebruiker aan een groep wilt toevoegen, haalt u de unieke id-waarde van zowel de gebruiker als de groep op. Geef deze waarden door aan de methode `addPrincipalToLocalGroup`.

**Zie ook**

[Groepen maken met de Java API](users.md#create-groups-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Gebruikers toevoegen](users.md#adding-users)

[Gebruikers verwijderen](users.md#deleting-users)

### Groepen maken met de Java API {#create-groups-using-the-java-api}

Maak een groep met de API voor directoryservice (Java):

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-usermanager-client.jar, op in het klassenpad van uw Java-project.

1. Creeer een cliënt DirectoryManagerService.

   Maak een `DirectoryManagerServiceClient`-object door de constructor ervan te gebruiken en een `ServiceClientFactory`-object door te geven dat verbindingseigenschappen bevat.

1. Bepaal of de groep bestaat.

   * Maak een `PrincipalSearchFilter`-object met de constructor ervan.
   * Stel het hoofdtype in door het object `setPrincipalType` van het object `PrincipalSearchFilter` aan te roepen. Geef de waarde `com.adobe.idp.um.api.infomodel.Principal.PRINCIPALTYPE_GROUP` door.
   * Stel het domein in door het object `setSpecificDomainName` van het object `PrincipalSearchFilter` aan te roepen. Geef een tekenreekswaarde door die de domeinnaam opgeeft.
   * Als u een groep wilt zoeken, roept u de methode `findPrincipals` van het object `DirectoryManagerServiceClient` aan (een principal kan een groep zijn). Geef het object `PrincipalSearchFilter` door dat het hoofdtype en de domeinnaam opgeeft. Deze methode retourneert een `java.util.List`-instantie waarbij elk element een `Group`-instantie is. Elke groepsinstantie past zich aan het filter aan dat is opgegeven met het object `PrincipalSearchFilter`.
   * Doorloop de instantie `java.util.List`. Haal voor elk element de groepsnaam op. Zorg ervoor dat de groepsnaam niet gelijk is aan de nieuwe groepsnaam.

1. Maak de groep.

   * Als de groep niet bestaat, roept u de methode `setCommonName` van het object `Group` aan en geeft u een tekenreekswaarde door die de groepsnaam opgeeft.
   * Roep de methode `Group` van het object `setDescription` aan en geef een tekenreekswaarde door die de beschrijving van de groep aangeeft.
   * Roep de methode `setDomainName` van het object `Group` aan en geef een tekenreekswaarde door die de domeinnaam opgeeft.
   * Roep de methode `DirectoryManagerServiceClient` van het object `createLocalGroup` aan en geef de instantie `Group` door.

   De methode `createLocalUser` retourneert een tekenreekswaarde die de lokale waarde van de gebruikersidentificatie opgeeft.

1. Voer een handeling uit met de groep.

   * Maak een `PrincipalSearchFilter`-object met de constructor ervan.
   * Stel de waarde van de gebruikersidentificatie in door de methode `setUserId` van het object `PrincipalSearchFilter` aan te roepen. Geef een tekenreekswaarde door die de waarde van de gebruikersidentificatie vertegenwoordigt.
   * Roep de methode `DirectoryManagerServiceClient` van het object `findPrincipals` aan en geef het object `PrincipalSearchFilter` door. Deze methode retourneert een `java.util.List`-instantie, waarbij elk element een `User`-object is. Doorloop de instantie `java.util.List` om de gebruiker te zoeken.
   * Voeg een gebruiker aan de groep toe door de `DirectoryManagerServiceClient` methode van het voorwerp `addPrincipalToLocalGroup` aan te halen. Geef de geretourneerde waarde van de methode `User` van het object door. `getOid` Geef de geretourneerde waarde van de methode `Group` van de objecten door (gebruik de instantie `getOid` die de nieuwe groep vertegenwoordigt).`Group`

**Zie ook**

[Overzicht van de stappen](users.md#summary-of-steps)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Gebruikers en groepen beheren {#managing-users-and-groups}

Dit onderwerp beschrijft hoe u (Java) kunt gebruiken om, domeinen, gebruikers, en groepen programmatically toe te wijzen te verwijderen.

>[!NOTE]
>
>Wanneer het vormen van een domein, moet u het unieke herkenningsteken voor groepen en gebruikers plaatsen. Het kenmerk dat wordt gekozen, moet niet alleen uniek zijn binnen de LDAP-omgeving, maar moet ook onveranderlijk zijn en niet worden gewijzigd binnen de directory. Dit attribuut moet ook van een eenvoudig type van koordgegevens zijn (de enige uitzondering momenteel toegestaan voor Actieve Folder 2000/2003 is `"objectsid"`, die een binaire waarde is). Het kenmerk Novell eDirectory `"GUID"` is bijvoorbeeld geen eenvoudig gegevenstype voor tekenreeksen en werkt daarom niet.

* Voor Actieve Folder, gebruik `"objectsid"`.
* Gebruik `"nsuniqueid"` voor SunOne.

>[!NOTE]
>
>Het maken van meerdere lokale gebruikers en groepen terwijl een LDAP-directorysynchronisatie wordt uitgevoerd, wordt niet ondersteund. Als u dit proces probeert uit te voeren, kunnen er fouten optreden.

### Overzicht van stappen {#summary_of_steps-3}

Voer de volgende stappen uit om gebruikers en groepen te beheren:

1. Inclusief projectbestanden.
1. Creeer een cliënt DirectoryManagerService.
1. Roep de juiste gebruikers- of groepsbewerkingen aan.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u ervoor zorgen dat u de proxybestanden opneemt.

**Een DirectoryManagerService-client maken**

Alvorens u een de dienstverrichting van de Manager van de Folder programmatically kunt uitvoeren, moet u een de dienstcliënt van de Manager van de Folder creëren. Met de Java API wordt dit verwezenlijkt door een `DirectoryManagerServiceClient` voorwerp te creëren. Met de webservice-API wordt dit bereikt door een `DirectoryManagerServiceService`-object te maken.

**De juiste gebruikers- of groepsbewerkingen aanroepen**

Zodra u de de dienstcliënt hebt gecreeerd, kunt u de gebruiker of de verrichtingen van het groepsbeheer dan aanhalen. De de dienstcliënt staat u toe om, domeinen, gebruiker, en groepen toe te wijzen te verwijderen. Merk op dat het of een folderhoofd of een lokale hoofd aan een lokale groep kan toevoegen, maar het is niet mogelijk om een lokale hoofd aan een foldergroep toe te voegen.

**Zie ook**

[Gebruikers en groepen beheren met de Java API](users.md#managing-users-and-groups-using-the-java-api)

[Gebruikers en groepen beheren met de webservice-API](users.md#managing-users-and-groups-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[API voor gebruikersbeheer - Snel aan de slag](/help/forms/developing/user-manager-java-api-quick.md#user-manager-java-api-quick-start-soap)

### Gebruikers en groepen beheren met de Java API {#managing-users-and-groups-using-the-java-api}

Voer de volgende taken uit om gebruikers, groepen en domeinen programmatisch te beheren met behulp van de map (Java):

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-usermanager-client.jar, op in het klassenpad van uw Java-project. Zie [Including AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files) voor informatie over de locatie van deze bestanden.

1. Creeer een cliënt DirectoryManagerService.

   Maak een `DirectoryManagerServiceClient`-object door de constructor ervan te gebruiken en een `ServiceClientFactory`-object door te geven dat verbindingseigenschappen bevat. Zie [Verbindingseigenschappen instellen ](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)*.*

1. Roep de juiste gebruikers- of groepsbewerkingen aan.

   Als u een gebruiker of groep wilt zoeken, roept u een van de methoden van het object `DirectoryManagerServiceClient` aan om principes te zoeken (aangezien een principal een gebruiker of een groep kan zijn). In het onderstaande voorbeeld wordt de methode `findPrincipals` aangeroepen met behulp van een zoekfilter (een object `PrincipalSearchFilter`).

   Aangezien de geretourneerde waarde in dit geval een `java.util.List` is met `Principal`-objecten, doorloopt u het resultaat en cast u de `Principal`-objecten naar `User`- of `Group`-objecten.

   Met het resulterende `User`- of `Group`-object (dat beide overerft van de `Principal`-interface) haalt u de informatie op die u in uw workflows nodig hebt. De domeinnaam en canonieke naamwaarden vormen samen bijvoorbeeld een unieke identificatie van een principal. Deze worden teruggewonnen door de `Principal` methode `getDomainName` en `getCanonicalName` van objecten aan te halen, respectievelijk.

   Als u een lokale gebruiker wilt verwijderen, roept u de methode `deleteLocalUser` van het object `DirectoryManagerServiceClient` aan en geeft u de id van de gebruiker door.

   Als u een lokale groep wilt verwijderen, roept u de methode `deleteLocalGroup` van het object `DirectoryManagerServiceClient` aan en geeft u de id van de groep door.

**Zie ook**

[Overzicht van de stappen](users.md#summary-of-steps)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Gebruikers en groepen beheren met de webservice-API {#managing-users-and-groups-using-the-web-service-api}

Om gebruikers, groepen, en domeinen programmatically te beheren gebruikend de Dienst API van de Manager van de Folder (Webdienst), voer de volgende taken uit:

1. Inclusief projectbestanden.

   * Creeer een de cliëntassemblage van Microsoft .NET die de Manager WSDL van de Folder verbruikt. (Zie [AEM Forms aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding).)
   * Verwijs naar de cliëntassemblage van Microsoft .NET. (Zie [Creërend een .NET cliëntassemblage die Base64 het coderen](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding) gebruikt.)

1. Creeer een cliënt DirectoryManagerService.

   Maak een `DirectoryManagerServiceService`-object met de constructor van de proxyklasse.

1. Roep de juiste gebruikers- of groepsbewerkingen aan.

   Als u een gebruiker of groep wilt zoeken, roept u een van de methoden van het object `DirectoryManagerServiceService` aan om principes te zoeken (aangezien een principal een gebruiker of een groep kan zijn). In het onderstaande voorbeeld wordt de methode `findPrincipalsWithFilter` aangeroepen met behulp van een zoekfilter (een object `PrincipalSearchFilter`). Wanneer u een `PrincipalSearchFilter`-object gebruikt, worden lokale hoofdbeginselen alleen geretourneerd als de eigenschap `isLocal` is ingesteld op `true`. Dit gedrag is anders dan wat er zou gebeuren met de Java API.

   >[!NOTE]
   >
   >Als het maximale aantal resultaten niet is opgegeven in het zoekfilter (via het veld `PrincipalSearchFilter.resultsMax`), worden maximaal 1000 resultaten geretourneerd. Dit gedrag is anders dan wat er gebeurt met de Java API, waarbij 10 resultaten het standaardmaximum zijn. De zoekmethoden zoals `findGroupMembers` leveren ook geen resultaten op, tenzij het maximale aantal resultaten is opgegeven in het zoekfilter (bijvoorbeeld via het veld `GroupMembershipSearchFilter.resultsMax`). Dit geldt voor alle zoekfilters die overerven van de klasse `GenericSearchFilter`. Zie [AEM Forms API Reference](https://www.adobe.com/go/learn_aemforms_javadocs_63_en) voor meer informatie.

   Aangezien de geretourneerde waarde in dit geval een `object[]` is met `Principal`-objecten, doorloopt u het resultaat en cast u de `Principal`-objecten naar `User`- of `Group`-objecten.

   Met het resulterende `User`- of `Group`-object (dat beide overerft van de `Principal`-interface) haalt u de informatie op die u in uw workflows nodig hebt. De domeinnaam en canonieke naamwaarden vormen samen bijvoorbeeld een unieke identificatie van een principal. Deze worden teruggewonnen door `Principal` de gebieden `domainName` en `canonicalName` van objecten, respectievelijk aan te halen.

   Als u een lokale gebruiker wilt verwijderen, roept u de methode `deleteLocalUser` van het object `DirectoryManagerServiceService` aan en geeft u de id van de gebruiker door.

   Als u een lokale groep wilt verwijderen, roept u de methode `deleteLocalGroup` van het object `DirectoryManagerServiceService` aan en geeft u de id van de groep door.

**Zie ook**

[Overzicht van de stappen](users.md#summary-of-steps)

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

## Rollen en machtigingen {#managing-roles-and-permissions} beheren

Dit onderwerp beschrijft hoe u de Dienst API van de Manager van de Vergunning (Java) kunt gebruiken om, rollen en toestemmingen programmatically toe te wijzen te verwijderen en te bepalen.

In AEM Forms is een *rol* een groep machtigingen voor toegang tot een of meer systeembronnen. Deze toestemmingen worden gecreeerd door het Beheer van de Gebruiker en door de de dienstcomponenten afgedwongen. Een beheerder kan bijvoorbeeld de rol &quot;Policy Set Author&quot; aan een groep gebruikers toewijzen. Het Rights Management zou dan de gebruikers van die groep met die rol toestaan om beleidsreeksen door beleidsconsole tot stand te brengen.

Er zijn twee soorten rollen: *standaardrollen* en *aangepaste rollen*. Standaardrollen (*systeemrollen)* zijn reeds ingezeten in AEM Forms. Aangenomen wordt dat standaardrollen niet door de beheerder kunnen worden verwijderd of gewijzigd en dus onveranderlijk zijn. Aangepaste rollen die door de beheerder zijn gemaakt en die vervolgens kunnen worden gewijzigd of verwijderd, zijn dus veranderbaar.

Rollen maken het eenvoudiger om machtigingen te beheren. Wanneer een rol aan een hoofd wordt toegewezen, wordt een reeks toestemmingen automatisch toegewezen aan dat hoofd, en alle specifieke op toegang betrekking hebbende besluiten voor het hoofd zijn gebaseerd op die algemene reeks toegewezen toestemmingen.

### Overzicht van stappen {#summary_of_steps-4}

Voer de volgende stappen uit om rollen en machtigingen te beheren:

1. Inclusief projectbestanden.
1. Maak een AuthorizationManagerService-client.
1. Roep de juiste rol- of machtigingsbewerkingen aan.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u ervoor zorgen dat u de proxybestanden opneemt.

**Een AuthorizationManagerService-client maken**

Alvorens u een verrichting van AuthorizationManagerService van het Beheer van de Gebruiker programmatically kunt uitvoeren, moet u een cliënt AuthorizationManagerService tot stand brengen. Met de Java API wordt dit verwezenlijkt door een `AuthorizationManagerServiceClient` voorwerp te creëren.

**De juiste rol- of machtigingsbewerkingen aanroepen**

Zodra u de de dienstcliënt hebt gecreeerd, kunt u de rol of toestemmingsverrichtingen dan aanhalen. De de dienstcliënt staat u toe om, rollen en toestemmingen toe te wijzen te verwijderen en te bepalen.

**Zie ook**

[Rollen en machtigingen beheren met de Java API](users.md#managing-roles-and-permissions-using-the-java-api)

[Rollen en machtigingen beheren met de webservice-API](users.md#managing-roles-and-permissions-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[API voor gebruikersbeheer - Snel aan de slag](/help/forms/developing/user-manager-java-api-quick.md#user-manager-java-api-quick-start-soap)

### Rollen en machtigingen beheren met de Java API {#managing-roles-and-permissions-using-the-java-api}

Voer de volgende taken uit om rollen en machtigingen te beheren met de API (Java) voor machtigingsbeheer:

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-usermanager-client.jar, op in het klassenpad van uw Java-project.

1. Maak een AuthorizationManagerService-client.

   Maak een `AuthorizationManagerServiceClient`-object door de constructor ervan te gebruiken en een `ServiceClientFactory`-object door te geven dat verbindingseigenschappen bevat.

1. Roep de juiste rol- of machtigingsbewerkingen aan.

   Als u een rol wilt toewijzen aan een principal, roept u de methode `assignRole` van het object `AuthorizationManagerServiceClient` op en geeft u de volgende waarden door:

   * Een `java.lang.String`-object dat de rol-id bevat
   * Een array van `java.lang.String`-objecten met de belangrijkste id&#39;s.

   Als u een rol wilt verwijderen uit een principal, roept u de methode `unassignRole` van het object `AuthorizationManagerServiceClient` op en geeft u de volgende waarden door:

   * Een object `java.lang.String` dat de rol-id bevat.
   * Een array van `java.lang.String`-objecten met de belangrijkste id&#39;s.


**Zie ook**

[Overzicht van de stappen](users.md#summary-of-steps)

[Snel starten (SOAP-modus): Rollen en machtigingen beheren met de Java API](/help/forms/developing/user-manager-java-api-quick.md#quick-start-soap-mode-managing-roles-and-permissions-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Rollen en machtigingen beheren met de webservice-API {#managing-roles-and-permissions-using-the-web-service-api}

Rollen en machtigingen beheren met behulp van de API (webservice) voor machtigingsbeheer:

1. Inclusief projectbestanden.

   Creeer een project van Microsoft .NET dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/AuthorizationManagerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervang `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een AuthorizationManagerService-client.

   * Maak een `AuthorizationManagerServiceClient`-object met de standaardconstructor.
   * Maak een `AuthorizationManagerServiceClient.Endpoint.Address`-object met de constructor `System.ServiceModel.EndpointAddress`. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/AuthorizationManagerService?blob=mtom`). U hoeft het `lc_version`-kenmerk niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.
   * Maak een `System.ServiceModel.BasicHttpBinding`-object door de waarde van het veld `AuthorizationManagerServiceClient.Endpoint.Binding` op te halen. Cast de terugkeerwaarde aan `BasicHttpBinding`.
   * Stel het veld `System.ServiceModel.BasicHttpBinding` van het object `MessageEncoding` in op `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam voor het AEM aan het veld `AuthorizationManagerServiceClient.ClientCredentials.UserName.UserName` toe.
      * Wijs de overeenkomstige wachtwoordwaarde aan het gebied `AuthorizationManagerServiceClient.ClientCredentials.UserName.Password` toe.
      * Wijs de constante waarde `HttpClientCredentialType.Basic` aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType` toe.
      * Wijs de constante waarde `BasicHttpSecurityMode.TransportCredentialOnly` aan het veld `BasicHttpBindingSecurity.Security.Mode` toe.

1. Roep de juiste rol- of machtigingsbewerkingen aan.

   Als u een rol wilt toewijzen aan een principal, roept u de methode `assignRole` van het object `AuthorizationManagerServiceClient` op en geeft u de volgende waarden door:

   * Een `string`-object dat de rol-id bevat
   * Een object `MyArrayOf_xsd_string` dat de belangrijkste id&#39;s bevat.

   Als u een rol wilt verwijderen uit een principal, roept u de methode `unassignRole` van het object `AuthorizationManagerServiceService` op en geeft u de volgende waarden door:

   * Een object `string` dat de rol-id bevat.
   * Een array van `string`-objecten met de belangrijkste id&#39;s.


**Zie ook**

[Overzicht van de stappen](users.md#summary-of-steps)

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

## Gebruikers {#authenticating-users} verifiëren

In dit onderwerp wordt beschreven hoe u de API (Java) voor verificatiebeheer kunt gebruiken om uw clienttoepassingen in staat te stellen gebruikers programmatisch te verifiëren.

Mogelijk is gebruikersverificatie vereist voor interactie met een ondernemingsdatabase of andere opslagruimten voor bedrijfsgegevens die beveiligde gegevens opslaan.

Neem bijvoorbeeld een scenario waarin een gebruiker een gebruikersnaam en wachtwoord invoert op een webpagina en de waarden verzendt naar een J2EE-toepassingsserver die als host fungeert voor Forms. Een aangepaste Forms-toepassing kan de gebruiker verifiëren met de service Verificatiebeheer.

Als de authentificatie succesvol is, heeft de toepassing toegang tot een beveiligd ondernemingsgegevensbestand. Anders wordt een bericht naar de gebruiker verzonden waarin wordt aangegeven dat de gebruiker geen geautoriseerde gebruiker is.

Het volgende diagram toont de logische stroom van de toepassing.

![au_au_umauth_process](assets/au_au_umauth_process.png)

De volgende lijst beschrijft de stappen in dit diagram

<table>
 <thead>
  <tr>
   <th><p>Stap</p></th>
   <th><p>Beschrijving</p></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p>1</p></td>
   <td><p>De gebruiker heeft toegang tot een website en geeft een gebruikersnaam en wachtwoord op. Deze informatie wordt verzonden naar een J2EE-toepassingsserver die als host fungeert voor AEM Forms.</p></td>
  </tr>
  <tr>
   <td><p>2</p></td>
   <td><p>De gebruikersgegevens worden geverifieerd met de service Verificatiebeheer. Als de gebruikersgegevens geldig zijn, gaat de workflow naar stap 3. Anders wordt een bericht naar de gebruiker verzonden waarin wordt aangegeven dat de gebruiker geen geautoriseerde gebruiker is.</p></td>
  </tr>
  <tr>
   <td><p>1</p></td>
   <td><p>Gebruikersgegevens en een formulierontwerp worden opgehaald uit een beveiligde ondernemingsdatabase. </p></td>
  </tr>
  <tr>
   <td><p>4</p></td>
   <td><p>Gebruikersgegevens worden samengevoegd met een formulierontwerp en het formulier wordt weergegeven aan de gebruiker. </p></td>
  </tr>
 </tbody>
</table>

### Overzicht van stappen {#summary_of_steps-5}

Voer de volgende stappen uit om een gebruiker programmatisch te verifiëren:

1. Inclusief projectbestanden.
1. Maak een AuthenticationManagerService-client.
1. Roep de verificatiebewerking aan.
1. Indien nodig, wint de context terug zodat de cliënttoepassing het aan een andere dienst van AEM Forms voor authentificatie kan door:sturen.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u ervoor zorgen dat u de proxybestanden opneemt.

**Een AuthenticationManagerService-client maken**

Alvorens u een gebruiker programmatically kunt voor authentiek verklaren, moet u een cliënt tot stand brengen AuthenticationManagerService. Wanneer u de Java API gebruikt, maakt u een `AuthenticationManagerServiceClient`-object.

**De verificatiebewerking aanroepen**

Zodra u de de dienstcliënt hebt gecreeerd, kunt u de authentificatieverrichting dan aanhalen. Voor deze bewerking is informatie over de gebruiker nodig, zoals de naam en het wachtwoord van de gebruiker. Als de gebruiker niet verifieert, wordt een uitzondering geworpen.

**De verificatiecontext ophalen**

Nadat u de gebruiker hebt geverifieerd, kunt u een context maken op basis van de geverifieerde gebruiker. Vervolgens kunt u de inhoud gebruiken om een andere AEM Forms-service aan te roepen. U kunt de context bijvoorbeeld gebruiken om een `EncryptionServiceClient` te maken en een PDF-document met een wachtwoord te versleutelen. Zorg ervoor dat de gebruiker die voor authentiek werd verklaard de rol genoemd `Services User` heeft die wordt vereist om de dienst van AEM Forms aan te halen.

**Zie ook**

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[API voor gebruikersbeheer - Snel aan de slag](/help/forms/developing/user-manager-java-api-quick.md#user-manager-java-api-quick-start-soap)

[PDF-documenten versleutelen met een wachtwoord](/help/forms/developing/encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-a-password)

### Gebruikers verifiëren met de Java-API {#authenticate-a-user-using-the-java-api}

Verifieer een gebruiker gebruikend de Dienst API van de Manager van de Authentificatie (Java):

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-usermanager-client.jar, op in het klassenpad van uw Java-project.

1. Creeer een cliënt AuthenticationManagerServices.

   Maak een `AuthenticationManagerServiceClient`-object door de constructor ervan te gebruiken en een `ServiceClientFactory`-object door te geven dat verbindingseigenschappen bevat.

1. Roep de verificatiebewerking aan.

   Roep de methode `authenticate` van het object `AuthenticationManagerServiceClient` aan en geef de volgende waarden door:

   * Een object `java.lang.String` dat de naam van de gebruiker bevat.
   * Een bytearray (een object `byte[]`) met het wachtwoord van de gebruiker. U kunt het `byte[]` voorwerp verkrijgen door de `java.lang.String` methode `getBytes` van objecten aan te halen.

   De methode authenticate retourneert een `AuthResult`-object dat informatie bevat over de geverifieerde gebruiker.

1. Haal de verificatiecontext op.

   Roep de methode `ServiceClientFactory` van het object `getContext` aan, die een object `Context` retourneert.

   Roep vervolgens de methode `Context` van het object `initPrincipal` aan en geef `AuthResult` door.

### Gebruikers verifiëren met de webservice-API {#authenticate-a-user-using-the-web-service-api}

Verifieer een gebruiker gebruikend de Dienst API van de Manager van de Authentificatie (Webdienst):

1. Inclusief projectbestanden.

   * Creeer een de cliëntassemblage van Microsoft .NET die de Manager WSDL van de Authentificatie verbruikt. (Zie [AEM Forms aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding).)
   * Verwijs naar de cliëntassemblage van Microsoft .NET. (Zie &quot;Verwijzen van de .NET cliëntassemblage&quot;in [het Aanhalen van AEM Forms gebruikend Base64 het coderen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding).)

1. Maak een AuthenticationManagerService-client.

   Maak een `AuthenticationManagerServiceService`-object met de constructor van de proxyklasse.

1. Roep de verificatiebewerking aan.

   Roep de methode `authenticate` van het object `AuthenticationManagerServiceClient` aan en geef de volgende waarden door:

   * Een object `string` dat de naam van de gebruiker bevat
   * Een bytearray (een object `byte[]`) met het wachtwoord van de gebruiker. U kunt het object `byte[]` verkrijgen door een object `string` met het wachtwoord om te zetten in een array `byte[]` met de logica in het onderstaande voorbeeld.
   * De geretourneerde waarde is een `AuthResult`-object dat kan worden gebruikt om informatie over de gebruiker op te halen. In het onderstaande voorbeeld wordt de informatie van de gebruiker opgehaald door eerst het veld `AuthResult` van het object `authenticatedUser` te verkrijgen en vervolgens de velden `canonicalName` en `domainName` van het resulterende object te verkrijgen.`User`

**Zie ook**

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Gebruikers {#programmatically-synchronizing-users} programmatisch synchroniseren

U kunt gebruikers programmatically synchroniseren door de API van het Beheer van de Gebruiker te gebruiken. Wanneer u gebruikers synchroniseert, werkt u AEM Forms bij met gebruikersgegevens in uw gegevensopslagruimte. Stel bijvoorbeeld dat u nieuwe gebruikers toevoegt aan de gegevensopslagruimte van uw gebruiker. Nadat u een synchronisatiebewerking hebt uitgevoerd, worden de nieuwe gebruikers AEM formuliergebruikers. Ook gebruikers die niet meer in je gebruikerslijst staan, worden uit AEM Forms verwijderd.

In het volgende diagram ziet u hoe AEM Forms synchroniseert met een gebruikersinterface.

![ps_ps_umauth_sync](assets/ps_ps_umauth_sync.png)

De volgende lijst beschrijft de stappen in dit diagram

<table>
 <thead>
  <tr>
   <th><p>Stap</p></th>
   <th><p>Beschrijving</p></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p>1</p></td>
   <td><p>Een clienttoepassing vraagt of AEM Forms een synchronisatiebewerking uitvoert.</p></td>
  </tr>
  <tr>
   <td><p>2</p></td>
   <td><p>AEM Forms voert een synchronisatiebewerking uit.</p></td>
  </tr>
  <tr>
   <td><p>1</p></td>
   <td><p>Gebruikersgegevens worden bijgewerkt.</p></td>
  </tr>
  <tr>
   <td><p>4</p></td>
   <td><p>Een gebruiker kan de bijgewerkte gebruikersinformatie bekijken. </p></td>
  </tr>
 </tbody>
</table>

### Overzicht van stappen {#summary_of_steps-6}

Voer de volgende stappen uit om gebruikers programmatisch te synchroniseren:

1. Inclusief projectbestanden.
1. Maak een UserManagerUtilServiceClient-client.
1. Geef het ondernemingsdomein op.
1. Roep de verificatiebewerking aan.
1. Bepalen of de synchronisatiebewerking is voltooid

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u ervoor zorgen dat u de proxybestanden opneemt.

**Een UserManagerUtilServiceClientclient maken**

Voordat u gebruikers programmatisch kunt synchroniseren, moet u een `UserManagerUtilServiceClient`-object maken.

**Het ondernemingsdomein opgeven**

Voordat u een synchronisatiebewerking uitvoert met de API voor gebruikersbeheer, geeft u het ondernemingsdomein op waartoe gebruikers behoren. U kunt een of meerdere ondernemingsdomeinen opgeven. Alvorens u een synchronisatieverrichting programmatically kunt uitvoeren, moet u een ondernemingsdomein opstelling gebruikend de Console van het Beleid. (Zie [administration help](https://www.adobe.com/go/learn_aemforms_admin_63).)

**De synchronisatiebewerking aanroepen**

Nadat u een of meer ondernemingsdomeinen hebt opgegeven, kunt u de synchronisatiebewerking uitvoeren. De tijd die nodig is om deze bewerking uit te voeren, is afhankelijk van het aantal gebruikersrecords in de gegevensopslagruimte van de gebruiker.

**Bepalen of de synchronisatiebewerking is voltooid**

Nadat u programmatically een synchronisatieverrichting uitvoert, kunt u bepalen als de verrichting volledig is.

**Zie ook**

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[API voor gebruikersbeheer - Snel aan de slag](/help/forms/developing/user-manager-java-api-quick.md#user-manager-java-api-quick-start-soap)

[PDF-documenten versleutelen met een wachtwoord](/help/forms/developing/encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-a-password)

### Gebruikers programmatisch synchroniseren met de Java API {#programmatically-synchronizing-users-using-the-java-api}

Gebruikers synchroniseren met de API voor gebruikersbeheer (Java):

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-usermanager-client.jar en adobe-usermanager-util-client.jar, op in het klassenpad van uw Java-project.

1. Maak een UserManagerUtilServiceClient-client.

   Maak een `UserManagerUtilServiceClient`-object door de constructor ervan te gebruiken en een `ServiceClientFactory`-object door te geven dat verbindingseigenschappen bevat.

1. Geef het ondernemingsdomein op.

   * Roep de methode `UserManagerUtilServiceClient` van het object `scheduleSynchronization` aan om de gebruikerssynchronisatiebewerking te starten.
   * Maak een `java.util.Set`-instantie met een `HashSet`-constructor. Zorg ervoor dat u `String` als gegevenstype specificeert. In deze `Java.util.Set`-instantie worden de domeinnamen opgeslagen waarop de synchronisatiebewerking van toepassing is.
   * Voor elke domeinnaam die moet worden toegevoegd, roept u de methode add van het object `java.util.Set` aan en geeft u de domeinnaam door.

1. Roep de synchronisatiebewerking aan.

   Roep de methode `ServiceClientFactory` van het object `getContext` aan, die een object `Context` retourneert.

   Roep vervolgens de methode `Context` van het object `initPrincipal` aan en geef `AuthResult` door.

**Zie ook**

[Gebruikers programmatisch synchroniseren](users.md#programmatically-synchronizing-users)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)
