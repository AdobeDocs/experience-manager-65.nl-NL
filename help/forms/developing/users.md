---
title: Gebruikers beheren
description: Gebruik de API voor gebruikersbeheer om clienttoepassingen te maken die rollen, machtigingen en principes (die gebruikers of groepen kunnen zijn) kunnen beheren en gebruikers kunnen verifiëren.
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
exl-id: d7c5bb84-a988-4b2e-a587-f4e5b50fea58
solution: Experience Manager, Experience Manager Forms
source-git-commit: 872e2de411f51b5f0b26a2ff47cb49f01313d39f
workflow-type: tm+mt
source-wordcount: '6201'
ht-degree: 0%

---

# Gebruikers beheren {#managing-users}

**Voorbeelden en voorbeelden in dit document gelden alleen voor AEM Forms in JEE-omgeving.**

**Over Gebruikersbeheer**

U kunt de API voor gebruikersbeheer gebruiken om clienttoepassingen te maken die rollen, machtigingen en principes (die gebruikers of groepen kunnen zijn) kunnen beheren en gebruikers kunnen verifiëren. Gebruikersbeheer-API bestaat uit de volgende AEM Forms API&#39;s:

* Directory Manager-service-API
* API voor verificatiebeheer
* Authorization Manager Service API

Met Gebruikersbeheer kunt u rollen en machtigingen toewijzen, verwijderen en bepalen. Het laat u ook toe om, domeinen, gebruikers, en groepen toe te wijzen te verwijderen en te vragen. Tot slot kunt u Gebruikersbeheer gebruiken om gebruikers voor authentiek te verklaren.

In [Gebruikers toevoegen](users.md#adding-users) u zult begrijpen hoe te om gebruikers programmatically toe te voegen. In deze sectie wordt de directoryservice-API gebruikt.

In [Gebruikers verwijderen](users.md#deleting-users) u zult begrijpen hoe te om gebruikers programmatically te schrappen. In deze sectie wordt de directoryservice-API gebruikt.

In [Gebruikers en groepen beheren](users.md#managing-users-and-groups) U zult het verschil tussen een lokale gebruiker en een foldergebruiker begrijpen, en voorbeelden van zien hoe te om Java en de dienst APIs van het Web te gebruiken om gebruikers en groepen programmatically te beheren. In deze sectie wordt de directoryservice-API gebruikt.

In [Rollen en machtigingen beheren](users.md#managing-roles-and-permissions) u zult over de systeemrollen en de toestemmingen leren en wat u programmatically kunt doen om hen te versterken, en voorbeelden van zien hoe te om Java en de dienst APIs van het Web te gebruiken om rollen en toestemmingen programmatically te beheren. Deze sectie gebruikt zowel de API van de Dienst van de Manager van de Folder als de Dienst API van de Manager van de Vergunning.

In [Gebruikers verifiëren](users.md#authenticating-users) U ziet voorbeelden van hoe u de Java- en webservice-API&#39;s kunt gebruiken om gebruikers programmatisch te verifiëren. Deze sectie gebruikt de Service API van de Manager van de Vergunning.

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
   <td><p>Het Beheer van de gebruiker verzendt de gebruikersnaam en het wachtwoord, en configuratieinformatie, naar de authentificatieleverancier.</p></td>
  </tr>
  <tr>
   <td><p>3</p></td>
   <td><p>De verificatieprovider maakt verbinding met de opslag van de gebruiker en verifieert de gebruiker.</p></td>
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
>Als de streek van de servertijd van de cliënttijdzone verschillend is, wanneer het verbruiken van WSDL voor AEM Forms de dienst van PDF op een inheemse SOAP stapel gebruikend een .NET cliënt op een cluster van de Server van de Toepassing WebSphere, kan de volgende de authentificatiefout van het Beheer van de Gebruiker voorkomen:

`[com.adobe.idp.um.webservices.WSSecurityHandler] errorCode:12803 errorCodeHEX:0x3203 message:WSSecurityHandler: UM authenticate returns exception : An error was discovered processing the <wsse:Security> header. (WSSecurityEngine: Invalid timestamp The security semantics of message have expired).`

**Directorybeheer**

Gebruikersbeheer wordt verpakt met een directoryserviceprovider (de DirectoryManagerService) die verbindingen met LDAP-directory&#39;s ondersteunt. Als uw organisatie een niet-LDAP-opslagplaats gebruikt om gebruikersverslagen op te slaan, kunt u uw eigen folder dienstverlener tot stand brengen die met uw bewaarplaats werkt.

De dienstverleners van de folder winnen verslagen van een gebruikersopslag op verzoek van het Beheer van de Gebruiker terug. Gebruikersbeheer slaat gebruikers- en groepsrecords in de database regelmatig in de cache op om de prestaties te verbeteren.

De provider van de directoryservice kan worden gebruikt om de gebruikersbeheerdatabase te synchroniseren met de opslag van de gebruiker. Deze stap zorgt ervoor dat alle informatie van de gebruikersfolder en alle gebruiker en groepsverslagen bijgewerkt zijn.

Bovendien voorziet DirectoryManagerService u van de capaciteit om domeinen tot stand te brengen en te beheren. Domeinen definiëren verschillende gebruikersbasen. De grens van een domein wordt gewoonlijk bepaald volgens de manier uw organisatie gestructureerd is of hoe uw gebruikersopslag opstelling is. De domeinen van het Beheer van de gebruiker verstrekken configuratiemontages die de authentificatieleveranciers en de leveranciers van de folderdienst gebruiken.

In de configuratie XML die het Beheer van de Gebruiker uitvoert, de wortelknoop die de attributenwaarde van heeft `Domains` bevat een XML-element voor elk domein dat is gedefinieerd voor Gebruikersbeheer. Elk van deze elementen bevat andere elementen die aspecten van het domein verbonden aan specifieke dienstverleners bepalen.

**Werken met objectSID-waarden**

Wanneer het gebruiken van Actieve Folder, is het belangrijk om te begrijpen dat een `objectSID` value is geen uniek kenmerk in meerdere domeinen. Met deze waarde wordt de beveiligings-id van een object opgeslagen. In een omgeving met meerdere domeinen (bijvoorbeeld een boomstructuur met domeinen) kan de instelling `objectSID` waarde kan verschillend zijn.

An `objectSID` De waarde zou veranderen als een voorwerp van één Actief domein van de Folder aan een ander domein wordt bewogen. Sommige objecten hebben hetzelfde `objectSID` waarde overal in het domein. Bijvoorbeeld, zouden de groepen zoals de Beheerders van BUILTIN \, de Gebruikers van de Macht van BUILTIN \, etc. het zelfde hebben `objectSID` waarde ongeacht de domeinen. Deze `objectSID` de waarden zijn bekend .

## Gebruikers toevoegen {#adding-users}

U kunt de API voor directoryservice (Java en webservice) gebruiken om gebruikers programmatisch aan AEM Forms toe te voegen. Nadat u een gebruiker hebt toegevoegd, kunt u die gebruiker gebruiken wanneer u een servicebewerking uitvoert waarvoor een gebruiker nodig is. U kunt bijvoorbeeld een taak toewijzen aan de nieuwe gebruiker.

### Overzicht van de stappen {#summary-of-steps}

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

* **Domeinnaam**: Het domein waartoe de gebruiker behoort (bijvoorbeeld `DefaultDom`).
* **Waarde van gebruikersidentificatie**: De id-waarde van de gebruiker (bijvoorbeeld `wblue`).
* **Principal type**: Het type gebruiker (bijvoorbeeld `USER)`.
* **Voornaam**: Een opgegeven naam voor de gebruiker (bijvoorbeeld `Wendy`).
* **Familienaam**: De familienaam voor de gebruiker (bijvoorbeeld `Blue)`.
* **Landinstelling**: Lokale informatie voor de gebruiker.

**De gebruiker toevoegen aan AEM Forms**

Nadat u gebruikersgegevens hebt gedefinieerd, kunt u de gebruiker aan AEM Forms toevoegen. Als u een gebruiker wilt toevoegen, roept u de `DirectoryManagerServiceClient` object `createLocalUser` methode.

**Controleren of de gebruiker is toegevoegd**

U kunt controleren of de gebruiker is toegevoegd om ervoor te zorgen dat er geen problemen zijn opgetreden. Zoek de nieuwe gebruiker met de waarde van de gebruikersidentificatie.

**Zie ook**

[Gebruikers toevoegen met de Java API](users.md#add-users-using-the-java-api)

[Gebruikers toevoegen met de webservice-API](users.md#add-users-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Gebruikers verwijderen](users.md#deleting-users)

### Gebruikers toevoegen met de Java API {#add-users-using-the-java-api}

Voeg gebruikers toe met de API voor directoryservice (Java):

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-usermanager-client.jar, op in het klassenpad van uw Java-project.

1. Creeer een cliënt DirectoryManagerServices.

   Een `DirectoryManagerServiceClient` object door de constructor ervan te gebruiken en een `ServiceClientFactory` object dat verbindingseigenschappen bevat.

1. Gebruikersgegevens definiëren.

   * Een `UserImpl` object met behulp van de constructor.
   * Stel de naam van het domein in door de `UserImpl` object `setDomainName` methode. Geef een tekenreekswaarde door die de domeinnaam opgeeft.
   * Stel het hoofdtype in door het `UserImpl` object `setPrincipalType` methode. Geef een tekenreekswaarde door die het type gebruiker aangeeft. U kunt bijvoorbeeld `USER`.
   * Stel de waarde van de gebruikersidentificatie in door de `UserImpl` object `setUserid` methode. Geef een tekenreekswaarde door die de waarde van de gebruikersidentificatie aangeeft. U kunt bijvoorbeeld `wblue`.
   * Stel de canonieke naam in door de `UserImpl` object `setCanonicalName` methode. Geef een tekenreekswaarde door die de canonieke naam van de gebruiker aangeeft. U kunt bijvoorbeeld `wblue`.
   * Stel de opgegeven naam in door de `UserImpl` object `setGivenName` methode. Geef een tekenreekswaarde door die de opgegeven naam van de gebruiker aangeeft. U kunt bijvoorbeeld `Wendy`.
   * Stel de familienaam in door de `UserImpl` object `setFamilyName` methode. Geef een tekenreekswaarde door die de familienaam van de gebruiker aangeeft. U kunt bijvoorbeeld `Blue`.

   >[!NOTE]
   >
   >Roep een methode aan die tot de `UserImpl` -object om andere waarden in te stellen. U kunt bijvoorbeeld de waarde van de landinstelling instellen door de `UserImpl` object `setLocale` methode.

1. Voeg de gebruiker toe aan AEM Forms.

   De `DirectoryManagerServiceClient` object `createLocalUser` en geeft de volgende waarden door:

   * De `UserImpl` object dat de nieuwe gebruiker vertegenwoordigt
   * Een tekenreekswaarde die het wachtwoord van de gebruiker vertegenwoordigt

   De `createLocalUser` Deze methode retourneert een tekenreekswaarde die de waarde van de lokale gebruikers-id opgeeft.

1. Controleer of de gebruiker is toegevoegd.

   * Een `PrincipalSearchFilter` object met behulp van de constructor.
   * Stel de waarde van de gebruikersidentificatie in door de `PrincipalSearchFilter` object `setUserId` methode. Geef een tekenreekswaarde door die de waarde van de gebruikersidentificatie vertegenwoordigt.
   * De `DirectoryManagerServiceClient` object `findPrincipals` en geeft de `PrincipalSearchFilter` object. Deze methode retourneert een `java.util.List` instantie, waarbij elk element een `User` object. Doorlopen `java.util.List` -instantie om de gebruiker te zoeken.

**Zie ook**

[Overzicht van de stappen](users.md#summary-of-steps)

[Snel starten (SOAP modus): gebruikers toevoegen met de Java API](/help/forms/developing/user-manager-java-api-quick.md#quick-start-soap-mode-adding-users-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Gebruikers toevoegen met de webservice-API {#add-users-using-the-web-service-api}

Voeg gebruikers toe met de API (webservice) van Directory Manager:

1. Inclusief projectbestanden.

   Creeer een Microsoft .NET project dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL voor de de dienstverwijzing gebruikt: `http://localhost:8080/soap/services/DirectoryManagerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` met het IP-adres van de server die als host fungeert voor AEM Forms.

1. Creeer een cliënt DirectoryManagerService.

   * Een `DirectoryManagerServiceClient` object met de standaardconstructor.
   * Een `DirectoryManagerServiceClient.Endpoint.Address` object door het `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/DirectoryManagerService?blob=mtom`). U hoeft de `lc_version` kenmerk. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt. Zorg ervoor dat u `?blob=mtom`.
   * Een `System.ServiceModel.BasicHttpBinding` object door de waarde van het object op te halen `DirectoryManagerServiceClient.Endpoint.Binding` veld. De geretourneerde waarde omzetten in `BasicHttpBinding`.
   * Stel de `System.ServiceModel.BasicHttpBinding` object `MessageEncoding` veld naar `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld toe `DirectoryManagerServiceClient.ClientCredentials.UserName.UserName`.
      * De bijbehorende wachtwoordwaarde aan het veld toewijzen `DirectoryManagerServiceClient.ClientCredentials.UserName.Password`.
      * De constante waarde toewijzen `HttpClientCredentialType.Basic` naar het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * De constante waarde toewijzen `BasicHttpSecurityMode.TransportCredentialOnly` naar het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Gebruikersgegevens definiëren.

   * Een `UserImpl` object met behulp van de constructor.
   * Stel de naam van het domein in door een tekenreekswaarde toe te wijzen aan de `UserImpl` object `domainName` veld.
   * Stel het hoofdtype in door een tekenreekswaarde toe te wijzen aan de `UserImpl` object `principalType` veld. U kunt bijvoorbeeld `USER`.
   * Stel de waarde van de gebruikersidentificatie in door een tekenreekswaarde toe te wijzen aan de `UserImpl` object `userid` veld.
   * Stel de canonieke naamwaarde in door een tekenreekswaarde toe te wijzen aan de `UserImpl` object `canonicalName` veld.
   * Stel de opgegeven naamwaarde in door een tekenreekswaarde toe te wijzen aan de `UserImpl` object `givenName` veld.
   * Stel de naam van de familie in door een tekenreekswaarde toe te wijzen aan de `UserImpl` object `familyName` veld.

1. Voeg de gebruiker toe aan AEM Forms.

   De `DirectoryManagerServiceClient` object `createLocalUser` en geeft de volgende waarden door:

   * De `UserImpl` object dat de nieuwe gebruiker vertegenwoordigt
   * Een tekenreekswaarde die het wachtwoord van de gebruiker vertegenwoordigt

   De `createLocalUser` Deze methode retourneert een tekenreekswaarde die de waarde van de lokale gebruikers-id opgeeft.

1. Controleer of de gebruiker is toegevoegd.

   * Een `PrincipalSearchFilter` object met behulp van de constructor.
   * Stel de waarde van de gebruikersidentificatie in door een tekenreekswaarde toe te wijzen die de waarde van de gebruikersidentificatie vertegenwoordigt `PrincipalSearchFilter` object `userId` veld.
   * De `DirectoryManagerServiceClient` object `findPrincipals` en geeft de `PrincipalSearchFilter` object. Deze methode retourneert een `MyArrayOfUser` verzamelingsobject, waarbij elk element een `User` object. Doorlopen `MyArrayOfUser` verzameling om de gebruiker te zoeken.

**Zie ook**

[Overzicht van de stappen](users.md#summary-of-steps)

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Gebruikers verwijderen {#deleting-users}

U kunt de API voor directoryservice (Java en webservice) gebruiken om gebruikers via programmacode uit AEM Forms te verwijderen. Nadat u een gebruiker schrapt, kan de gebruiker niet meer worden gebruikt om een de dienstverrichting uit te voeren die een gebruiker vereist. U kunt bijvoorbeeld geen taak toewijzen aan een verwijderde gebruiker.

### Overzicht van de stappen {#summary_of_steps-1}

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

Als u een gebruiker wilt verwijderen, roept u de `DirectoryManagerServiceClient` object `deleteLocalUser` methode.

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

   Een `DirectoryManagerServiceClient` object door de constructor ervan te gebruiken en een `ServiceClientFactory` object dat verbindingseigenschappen bevat.

1. Geef de gebruiker op die u wilt verwijderen.

   * Een `PrincipalSearchFilter` object met behulp van de constructor.
   * Stel de waarde van de gebruikersidentificatie in door de `PrincipalSearchFilter` object `setUserId` methode. Geef een tekenreekswaarde door die de waarde van de gebruikersidentificatie vertegenwoordigt.
   * De `DirectoryManagerServiceClient` object `findPrincipals` en geeft de `PrincipalSearchFilter` object. Deze methode retourneert een `java.util.List` instantie, waarbij elk element een `User` object. Doorlopen `java.util.List` -instantie om de te verwijderen gebruiker te zoeken.

1. Verwijder de gebruiker uit AEM Forms.

   De `DirectoryManagerServiceClient` object `deleteLocalUser` en geeft u de waarde van de `User` object `oid` veld. De `User` object `getOid` methode. Gebruik de `User` object opgehaald uit het `java.util.List` -instantie.

**Zie ook**

[Overzicht van de stappen](users.md#summary-of-steps)

[Snel starten (EJB-modus): gebruikers verwijderen met de Java API](/help/forms/developing/user-manager-java-api-quick.md#quick-start-soap-mode-deleting-users-using-the-java-api)

[Snel starten (SOAP modus): gebruikers verwijderen met de Java API](/help/forms/developing/user-manager-java-api-quick.md#quick-start-soap-mode-deleting-users-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Gebruikers verwijderen met de webservice-API {#delete-users-using-the-web-service-api}

Gebruikers verwijderen met de API voor directoryservice (webservice):

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-usermanager-client.jar, op in het klassenpad van uw Java-project.

1. Creeer een cliënt DirectoryManagerService.

   * Een `DirectoryManagerServiceClient` object met de standaardconstructor.
   * Een `DirectoryManagerServiceClient.Endpoint.Address` object door het `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/DirectoryManagerService?blob=mtom`). U hoeft de `lc_version` kenmerk. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt. Zorg ervoor dat u `blob=mtom.`
   * Een `System.ServiceModel.BasicHttpBinding` object door de waarde van het object op te halen `DirectoryManagerServiceClient.Endpoint.Binding` veld. De geretourneerde waarde omzetten in `BasicHttpBinding`.
   * Stel de `System.ServiceModel.BasicHttpBinding` object `MessageEncoding` veld naar `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld toe `DirectoryManagerServiceClient.ClientCredentials.UserName.UserName`.
      * De bijbehorende wachtwoordwaarde aan het veld toewijzen `DirectoryManagerServiceClient.ClientCredentials.UserName.Password`.
      * De constante waarde toewijzen `HttpClientCredentialType.Basic` naar het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * De constante waarde toewijzen `BasicHttpSecurityMode.TransportCredentialOnly` naar het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Geef de gebruiker op die u wilt verwijderen.

   * Een `PrincipalSearchFilter` object met behulp van de constructor.
   * Stel de waarde van de gebruikersidentificatie in door een tekenreekswaarde toe te wijzen aan de `PrincipalSearchFilter` object `userId` veld.
   * De `DirectoryManagerServiceClient` object `findPrincipals` en geeft de `PrincipalSearchFilter` object. Deze methode retourneert een `MyArrayOfUser` verzamelingsobject, waarbij elk element een `User` object. Doorlopen `MyArrayOfUser` verzameling om de gebruiker te zoeken. De `User` object opgehaald uit het `MyArrayOfUser` verzamelingsobject wordt gebruikt om de gebruiker te verwijderen.

1. Verwijder de gebruiker uit AEM Forms.

   Verwijder de gebruiker door de `User` object `oid` veldwaarde voor de `DirectoryManagerServiceClient` object `deleteLocalUser` methode.

**Zie ook**

[Overzicht van de stappen](users.md#summary-of-steps)

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Groepen maken {#creating-groups}

U kunt de API voor directoryservice (Java en webservice) gebruiken om AEM Forms-groepen programmatisch te maken. Nadat u een groep creeert, kunt u die groep gebruiken om een de dienstverrichting uit te voeren die een groep vereist. U kunt bijvoorbeeld een gebruiker aan de nieuwe groep toewijzen. (Zie [Gebruikers en groepen beheren](users.md#managing-users-and-groups).)

### Overzicht van de stappen {#summary_of_steps-2}

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

Voor informatie over de locatie van deze JAR-bestanden raadpleegt u [Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Een DirectoryManagerService-client maken**

Alvorens u een de dienstverrichting van de Manager van de Folder programmatically kunt uitvoeren, creeer een cliënt van de Dienst API van de Manager van de Folder.

**Bepalen of de groep bestaat**

Wanneer u een groep maakt, moet u ervoor zorgen dat de groep niet in hetzelfde domein bestaat. Twee groepen kunnen dus niet dezelfde naam binnen hetzelfde domein hebben. Voor deze taak voert u een zoekopdracht uit en filtert u de zoekresultaten op basis van twee waarden. Het hoofdtype instellen op `com.adobe.idp.um.api.infomodel.Principal.PRINCIPALTYPE_GROUP` om ervoor te zorgen dat alleen groepen worden geretourneerd. Zorg er ook voor dat u de domeinnaam opgeeft.

**De groep maken**

Nadat u hebt bepaald dat de groep niet bestaat in het domein, maakt u de groep en geeft u de volgende kenmerken op:

* **CommonName**: De naam van de groep.
* **Domein**: Het domein waarin de groep wordt toegevoegd.
* **Beschrijving**: Een beschrijving van de groep.

**Een handeling uitvoeren met de groep**

Nadat u een groep hebt gemaakt, kunt u een actie uitvoeren met de groep. U kunt bijvoorbeeld een gebruiker aan de groep toevoegen. Als u een gebruiker aan een groep wilt toevoegen, haalt u de unieke id-waarde van zowel de gebruiker als de groep op. Geef deze waarden door aan `addPrincipalToLocalGroup` methode.

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

   Een `DirectoryManagerServiceClient` object door de constructor ervan te gebruiken en een `ServiceClientFactory` object dat verbindingseigenschappen bevat.

1. Bepaal of de groep bestaat.

   * Een `PrincipalSearchFilter` object met behulp van de constructor.
   * Stel het hoofdtype in door het `PrincipalSearchFilter` object `setPrincipalType` object. Geef de waarde door `com.adobe.idp.um.api.infomodel.Principal.PRINCIPALTYPE_GROUP`.
   * Stel het domein in door het `PrincipalSearchFilter` object `setSpecificDomainName` object. Geef een tekenreekswaarde door die de domeinnaam opgeeft.
   * Als u een groep wilt zoeken, roept u de `DirectoryManagerServiceClient` object `findPrincipals` methode (een principal kan een groep zijn). Geef de `PrincipalSearchFilter` object dat het hoofdtype en de domeinnaam opgeeft. Deze methode retourneert een `java.util.List` instantie waarbij elk element een `Group` -instantie. Elke groepsinstantie is in overeenstemming met het filter dat is opgegeven met het `PrincipalSearchFilter` object.
   * Doorlopen `java.util.List` -instantie. Haal voor elk element de groepsnaam op. Zorg ervoor dat de groepsnaam niet gelijk is aan de nieuwe groepsnaam.

1. Maak de groep.

   * Als de groep niet bestaat, roept u `Group` object `setCommonName` methode en geef een tekenreekswaarde door die de groepsnaam opgeeft.
   * De `Group` object `setDescription` methode en geef een tekenreekswaarde door die de groepsbeschrijving aangeeft.
   * De `Group` object `setDomainName` en geeft een tekenreekswaarde door die de domeinnaam opgeeft.
   * De `DirectoryManagerServiceClient` object `createLocalGroup` en geeft de `Group` -instantie.

   De `createLocalUser` Deze methode retourneert een tekenreekswaarde die de waarde van de lokale gebruikers-id opgeeft.

1. Voer een handeling uit met de groep.

   * Een `PrincipalSearchFilter` object met behulp van de constructor.
   * Stel de waarde van de gebruikersidentificatie in door de `PrincipalSearchFilter` object `setUserId` methode. Geef een tekenreekswaarde door die de waarde van de gebruikersidentificatie vertegenwoordigt.
   * De `DirectoryManagerServiceClient` object `findPrincipals` en geeft de `PrincipalSearchFilter` object. Deze methode retourneert een `java.util.List` instantie, waarbij elk element een `User` object. Doorlopen `java.util.List` -instantie om de gebruiker te zoeken.
   * Voeg een gebruiker aan de groep toe door het `DirectoryManagerServiceClient` object `addPrincipalToLocalGroup` methode. Geef de geretourneerde waarde van het dialoogvenster door `User` object `getOid` methode. Geef de geretourneerde waarde van het dialoogvenster door `Group` objecten `getOid` methode (gebruik de `Group` -instantie die de nieuwe groep vertegenwoordigt).

**Zie ook**

[Overzicht van de stappen](users.md#summary-of-steps)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Gebruikers en groepen beheren {#managing-users-and-groups}

Dit onderwerp beschrijft hoe u (Java) kunt gebruiken om, domeinen, gebruikers, en groepen programmatically toe te wijzen te verwijderen.

>[!NOTE]
>
>Wanneer het vormen van een domein, moet u het unieke herkenningsteken voor groepen en gebruikers plaatsen. Het kenmerk dat wordt gekozen, moet niet alleen uniek zijn binnen de LDAP-omgeving, maar moet ook onveranderlijk zijn en niet worden gewijzigd binnen de directory. Dit attribuut moet ook van een eenvoudig type van koordgegevens zijn (de enige uitzondering momenteel toegestaan voor Actieve Folder 2000/2003 is `"objectsid"`, wat een binaire waarde is). Het kenmerk Novell eDirectory `"GUID"`Dit is bijvoorbeeld geen eenvoudig gegevenstype voor tekenreeksen en werkt dus niet.

* Voor Actieve Folder, gebruik `"objectsid"`.
* Gebruik voor SunOne `"nsuniqueid"`.

>[!NOTE]
>
>Het maken van meerdere lokale gebruikers en groepen terwijl een LDAP-directorysynchronisatie wordt uitgevoerd, wordt niet ondersteund. Als u dit proces probeert uit te voeren, kunnen fouten optreden.

### Overzicht van de stappen {#summary_of_steps-3}

Voer de volgende stappen uit om gebruikers en groepen te beheren:

1. Inclusief projectbestanden.
1. Creeer een cliënt DirectoryManagerService.
1. Roep de juiste gebruikers- of groepsbewerkingen aan.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u ervoor zorgen dat u de proxybestanden opneemt.

**Een DirectoryManagerService-client maken**

Alvorens u een de dienstverrichting van de Manager van de Folder programmatically kunt uitvoeren, moet u een de dienstcliënt van de Manager van de Folder creëren. Met de Java API wordt dit bereikt door een `DirectoryManagerServiceClient` object. Met de webservice-API kunt u dit bereiken door een `DirectoryManagerServiceService` object.

**De juiste gebruikers- of groepsbewerkingen aanroepen**

Zodra u de de dienstcliënt hebt gecreeerd, kunt u de gebruiker of de verrichtingen van het groepsbeheer dan aanhalen. De de dienstcliënt laat u, domeinen, gebruiker, en groepen toewijzen verwijderen. Merk op dat het of een folderhoofd of een lokale hoofd aan een lokale groep kan toevoegen, maar het is niet mogelijk om een lokale hoofd aan een foldergroep toe te voegen.

**Zie ook**

[Gebruikers en groepen beheren met de Java API](users.md#managing-users-and-groups-using-the-java-api)

[Gebruikers en groepen beheren met de webservice-API](users.md#managing-users-and-groups-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[API voor gebruikersbeheer - Snel aan de slag](/help/forms/developing/user-manager-java-api-quick.md#user-manager-java-api-quick-start-soap)

### Gebruikers en groepen beheren met de Java API {#managing-users-and-groups-using-the-java-api}

Voer de volgende taken uit om gebruikers, groepen en domeinen programmatisch te beheren met behulp van de map (Java):

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-usermanager-client.jar, op in het klassenpad van uw Java-project. Voor informatie over de locatie van deze bestanden raadpleegt u [Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

1. Creeer een cliënt DirectoryManagerService.

   Een `DirectoryManagerServiceClient` object door de constructor ervan te gebruiken en een `ServiceClientFactory` object dat verbindingseigenschappen bevat. Zie voor meer informatie [Verbindingseigenschappen instellen ](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)*.*

1. Roep de juiste gebruikers- of groepsbewerkingen aan.

   Als u een gebruiker of groep wilt zoeken, roept u een van de `DirectoryManagerServiceClient` de methodes van objecten om hoofden (aangezien een hoofd een gebruiker of een groep kan zijn) te vinden. In het onderstaande voorbeeld wordt `findPrincipals` methode wordt aangeroepen met een zoekfilter (een `PrincipalSearchFilter` object).

   Aangezien de geretourneerde waarde in dit geval een `java.util.List` bevattende `Principal` objecten, doorloopt het resultaat en cast het `Principal` objecten naar `User` of `Group` objecten.

   Het resultaat gebruiken `User` of `Group` object (dat beide van het `Principal` ), haalt u de informatie op die u in uw workflows nodig hebt. De domeinnaam en canonieke naamwaarden vormen samen bijvoorbeeld een unieke identificatie van een principal. Deze worden teruggewonnen door te halen `Principal` object `getDomainName` en `getCanonicalName` methoden, respectievelijk.

   Als u een lokale gebruiker wilt verwijderen, roept u de `DirectoryManagerServiceClient` object `deleteLocalUser` en geeft u de id van de gebruiker door.

   Als u een lokale groep wilt verwijderen, roept u de opdracht `DirectoryManagerServiceClient` object `deleteLocalGroup` en geeft u de id van de groep door.

**Zie ook**

[Overzicht van de stappen](users.md#summary-of-steps)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Gebruikers en groepen beheren met de webservice-API {#managing-users-and-groups-using-the-web-service-api}

Om gebruikers, groepen, en domeinen programmatically te beheren gebruikend de Dienst API van de Manager van de Folder (Webdienst), voer de volgende taken uit:

1. Inclusief projectbestanden.

   * Creeer een Microsoft .NET cliëntassemblage die de Manager WSDL van de Folder verbruikt. (Zie [AEM Forms aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding).)
   * Verwijs naar de Microsoft .NET cliëntassemblage. (Zie [Creërend een .NET cliëntassemblage die het coderen Base64 gebruikt](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding).)

1. Creeer een cliënt DirectoryManagerService.

   Een `DirectoryManagerServiceService` object met de constructor van de proxyklasse.

1. Roep de juiste gebruikers- of groepsbewerkingen aan.

   Als u een gebruiker of groep wilt zoeken, roept u een van de `DirectoryManagerServiceService` de methodes van objecten om hoofden (aangezien een hoofd een gebruiker of een groep kan zijn) te vinden. In het onderstaande voorbeeld wordt `findPrincipalsWithFilter` methode wordt aangeroepen met een zoekfilter (een `PrincipalSearchFilter` object). Wanneer u een `PrincipalSearchFilter` object, lokale hoofden worden alleen geretourneerd als de `isLocal` eigenschap is ingesteld op `true`. Dit gedrag verschilt van wat er zou gebeuren met de Java API.

   >[!NOTE]
   >
   >Als het maximale aantal resultaten niet is opgegeven in het zoekfilter (via de `PrincipalSearchFilter.resultsMax` (veld), worden maximaal 1000 resultaten geretourneerd. Dit gedrag is anders dan wat er gebeurt met de Java API, waarbij 10 resultaten het standaardmaximum zijn. Ook de zoekmethoden, zoals `findGroupMembers` geen resultaten oplevert, tenzij het maximale aantal resultaten is opgegeven in het zoekfilter (bijvoorbeeld via `GroupMembershipSearchFilter.resultsMax` veld). Dit is van toepassing op alle zoekfilters die overerven van de `GenericSearchFilter` klasse. Zie voor meer informatie [AEM Forms API-naslag](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

   Aangezien de geretourneerde waarde in dit geval een `object[]` bevattende `Principal` objecten, doorloopt het resultaat en cast het `Principal` objecten naar `User` of `Group` objecten.

   Het resultaat gebruiken `User` of `Group` object (dat beide van het `Principal` ), haalt u de informatie op die u in uw workflows nodig hebt. De domeinnaam en canonieke naamwaarden vormen samen bijvoorbeeld een unieke identificatie van een principal. Deze worden teruggewonnen door te halen `Principal` object `domainName` en `canonicalName` respectievelijk velden.

   Als u een lokale gebruiker wilt verwijderen, roept u de `DirectoryManagerServiceService` object `deleteLocalUser` en geeft u de id van de gebruiker door.

   Als u een lokale groep wilt verwijderen, roept u de opdracht `DirectoryManagerServiceService` object `deleteLocalGroup` en geeft u de id van de groep door.

**Zie ook**

[Overzicht van de stappen](users.md#summary-of-steps)

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

## Rollen en machtigingen beheren {#managing-roles-and-permissions}

Dit onderwerp beschrijft hoe u de Dienst API van de Manager van de Vergunning (Java) kunt gebruiken om, rollen en toestemmingen programmatically toe te wijzen te verwijderen en te bepalen.

In AEM Forms *rol* is een groep toestemmingen voor de toegang tot van één of meerdere systeem-vlakke middelen. Deze toestemmingen worden gecreeerd door het Beheer van de Gebruiker en door de de dienstcomponenten afgedwongen. Een beheerder kan bijvoorbeeld de rol &quot;Policy Set Author&quot; aan een groep gebruikers toewijzen. Het Rights Management zou dan de gebruikers van die groep met die rol toestaan om beleidsreeksen door beleidsconsole tot stand te brengen.

Er zijn twee soorten rollen: *standaardrollen* en *aangepaste rollen*. Standaardrollen (*systeemrollen)* reeds in AEM Forms woonachtig zijn. Aangenomen wordt dat standaardrollen niet door de beheerder kunnen worden verwijderd of gewijzigd en dus onveranderlijk zijn. Aangepaste rollen die door de beheerder zijn gemaakt en die vervolgens kunnen worden gewijzigd of verwijderd, zijn dus veranderbaar.

Rollen maken het eenvoudiger om machtigingen te beheren. Wanneer een rol aan een hoofd wordt toegewezen, wordt een reeks toestemmingen automatisch toegewezen aan dat hoofd, en alle specifieke op toegang betrekking hebbende besluiten voor het hoofd zijn gebaseerd op die algemene reeks toegewezen toestemmingen.

### Overzicht van de stappen {#summary_of_steps-4}

Voer de volgende stappen uit om rollen en machtigingen te beheren:

1. Inclusief projectbestanden.
1. Maak een AuthorizationManagerService-client.
1. Roep de juiste rol- of machtigingsbewerkingen aan.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u ervoor zorgen dat u de proxybestanden opneemt.

**Een AuthorizationManagerService-client maken**

Alvorens u een verrichting van AuthorizationManagerService van het Beheer van de Gebruiker programmatically kunt uitvoeren, moet u een cliënt AuthorizationManagerService tot stand brengen. Met de Java API wordt dit bereikt door een `AuthorizationManagerServiceClient` object.

**De juiste rol- of machtigingsbewerkingen aanroepen**

Zodra u de de dienstcliënt hebt gecreeerd, kunt u de rol of toestemmingsverrichtingen dan aanhalen. De de dienstcliënt laat u, rollen en toestemmingen toewijzen verwijderen en bepalen.

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

   Een `AuthorizationManagerServiceClient` object door de constructor ervan te gebruiken en een `ServiceClientFactory` object dat verbindingseigenschappen bevat.

1. Roep de juiste rol- of machtigingsbewerkingen aan.

   Om een rol aan een hoofd toe te wijzen, haal `AuthorizationManagerServiceClient` object `assignRole` en geeft de volgende waarden door:

   * A `java.lang.String` object dat de rol-id bevat
   * Een array van `java.lang.String` objecten met de belangrijkste id&#39;s.

   Om een rol uit een hoofd te verwijderen, haal aan `AuthorizationManagerServiceClient` object `unassignRole` en geeft de volgende waarden door:

   * A `java.lang.String` object dat de rol-id bevat.
   * Een array van `java.lang.String` objecten met de belangrijkste id&#39;s.

**Zie ook**

[Overzicht van de stappen](users.md#summary-of-steps)

[Snel starten (SOAP modus): Rollen en machtigingen beheren met de Java API](/help/forms/developing/user-manager-java-api-quick.md#quick-start-soap-mode-managing-roles-and-permissions-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Rollen en machtigingen beheren met de webservice-API {#managing-roles-and-permissions-using-the-web-service-api}

Rollen en machtigingen beheren met behulp van de API (webservice) voor machtigingsbeheer:

1. Inclusief projectbestanden.

   Creeer een Microsoft .NET project dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/AuthorizationManagerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` met het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een AuthorizationManagerService-client.

   * Een `AuthorizationManagerServiceClient` object met de standaardconstructor.
   * Een `AuthorizationManagerServiceClient.Endpoint.Address` object door het `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/AuthorizationManagerService?blob=mtom`.) U hoeft de `lc_version` kenmerk. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.
   * Een `System.ServiceModel.BasicHttpBinding` object door de waarde van het object op te halen `AuthorizationManagerServiceClient.Endpoint.Binding` veld. De geretourneerde waarde omzetten in `BasicHttpBinding`.
   * Stel de `System.ServiceModel.BasicHttpBinding` object `MessageEncoding` veld naar `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld toe `AuthorizationManagerServiceClient.ClientCredentials.UserName.UserName`.
      * De bijbehorende wachtwoordwaarde aan het veld toewijzen `AuthorizationManagerServiceClient.ClientCredentials.UserName.Password`.
      * De constante waarde toewijzen `HttpClientCredentialType.Basic` naar het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
      * De constante waarde toewijzen `BasicHttpSecurityMode.TransportCredentialOnly` naar het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Roep de juiste rol- of machtigingsbewerkingen aan.

   Om een rol aan een hoofd toe te wijzen, haal `AuthorizationManagerServiceClient` object `assignRole` en geeft de volgende waarden door:

   * A `string` object dat de rol-id bevat
   * A `MyArrayOf_xsd_string` object dat de belangrijkste id&#39;s bevat.

   Om een rol uit een hoofd te verwijderen, haal aan `AuthorizationManagerServiceService` object `unassignRole` en geeft de volgende waarden door:

   * A `string` object dat de rol-id bevat.
   * Een array van `string` objecten met de belangrijkste id&#39;s.

**Zie ook**

[Overzicht van de stappen](users.md#summary-of-steps)

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

## Gebruikers verifiëren {#authenticating-users}

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
   <td><p>3</p></td>
   <td><p>Gebruikersgegevens en een formulierontwerp worden opgehaald uit een beveiligde ondernemingsdatabase. </p></td>
  </tr>
  <tr>
   <td><p>4</p></td>
   <td><p>Gebruikersgegevens worden samengevoegd met een formulierontwerp en het formulier wordt weergegeven aan de gebruiker. </p></td>
  </tr>
 </tbody>
</table>

### Overzicht van de stappen {#summary_of_steps-5}

Voer de volgende stappen uit om een gebruiker programmatisch te verifiëren:

1. Inclusief projectbestanden.
1. Maak een AuthenticationManagerService-client.
1. Roep de verificatiebewerking aan.
1. Indien nodig, wint de context terug zodat de cliënttoepassing het aan een andere dienst van AEM Forms voor authentificatie kan door:sturen.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u ervoor zorgen dat u de proxybestanden opneemt.

**Een AuthenticationManagerService-client maken**

Alvorens u een gebruiker programmatically kunt voor authentiek verklaren, moet u een cliënt tot stand brengen AuthenticationManagerService. Als u de Java API gebruikt, maakt u een `AuthenticationManagerServiceClient` object.

**De verificatiebewerking aanroepen**

Zodra u de de dienstcliënt hebt gecreeerd, kunt u de authentificatieverrichting dan aanhalen. Voor deze bewerking is informatie over de gebruiker nodig, zoals de naam en het wachtwoord van de gebruiker. Als de gebruiker niet verifieert, wordt een uitzondering geworpen.

**De verificatiecontext ophalen**

Nadat u de gebruiker hebt geverifieerd, kunt u een context maken op basis van de geverifieerde gebruiker. Vervolgens kunt u de inhoud gebruiken om een andere AEM Forms-service aan te roepen. U kunt de context bijvoorbeeld gebruiken om een `EncryptionServiceClient` en versleutelen van een PDF-document met een wachtwoord. Zorg ervoor dat de gebruiker die voor authentiek werd verklaard de genoemde rol heeft `Services User` die vereist is om een AEM Forms-service aan te roepen.

**Zie ook**

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[API voor gebruikersbeheer - Snel aan de slag](/help/forms/developing/user-manager-java-api-quick.md#user-manager-java-api-quick-start-soap)

[PDF-documenten versleutelen met een wachtwoord](/help/forms/developing/encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-a-password)

### Gebruikers verifiëren met de Java API {#authenticate-a-user-using-the-java-api}

Verifieer een gebruiker gebruikend de Dienst API van de Manager van de Authentificatie (Java):

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-usermanager-client.jar, op in het klassenpad van uw Java-project.

1. Creeer een cliënt AuthenticationManagerServices.

   Een `AuthenticationManagerServiceClient` object door de constructor ervan te gebruiken en een `ServiceClientFactory` object dat verbindingseigenschappen bevat.

1. Roep de verificatiebewerking aan.

   De `AuthenticationManagerServiceClient` object `authenticate` en geeft de volgende waarden door:

   * A `java.lang.String` object dat de naam van de gebruiker bevat.
   * Een bytearray (a `byte[]` object) met het wachtwoord van de gebruiker. U kunt de `byte[]` door het object aan te roepen `java.lang.String` object `getBytes` methode.

   De methode authenticate retourneert een `AuthResult` object, dat informatie bevat over de geverifieerde gebruiker.

1. Haal de verificatiecontext op.

   De `ServiceClientFactory` object `getContext` methode, die een `Context` object.

   Roep vervolgens het `Context` object `initPrincipal` en geeft de `AuthResult`.

### Gebruikers verifiëren met de webservice-API {#authenticate-a-user-using-the-web-service-api}

Verifieer een gebruiker gebruikend de Dienst API van de Manager van de Authentificatie (Webdienst):

1. Inclusief projectbestanden.

   * Creeer een Microsoft .NET cliëntassemblage die de Manager WSDL van de Authentificatie verbruikt. (Zie [AEM Forms aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding).)
   * Verwijs naar de Microsoft .NET cliëntassemblage. (Zie &quot;Verwijzen van de .NET cliëntassemblage&quot;in [AEM Forms aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding).)

1. Maak een AuthenticationManagerService-client.

   Een `AuthenticationManagerServiceService` object met de constructor van de proxyklasse.

1. Roep de verificatiebewerking aan.

   De `AuthenticationManagerServiceClient` object `authenticate` en geeft de volgende waarden door:

   * A `string` object dat de gebruikersnaam bevat
   * Een bytearray (a `byte[]` object) met het wachtwoord van de gebruiker. U kunt de `byte[]` object door een `string` object met het wachtwoord naar een `byte[]` met behulp van de logica die in het onderstaande voorbeeld wordt getoond.
   * De geretourneerde waarde is een `AuthResult` -object, dat kan worden gebruikt om informatie over de gebruiker op te halen. In het onderstaande voorbeeld wordt de informatie van de gebruiker opgehaald door eerst het `AuthResult` object `authenticatedUser` en vervolgens het resultaat te verkrijgen `User` object `canonicalName` en `domainName` velden.

**Zie ook**

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Gebruikers programmatisch synchroniseren {#programmatically-synchronizing-users}

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
   <td><p>AEM Forms voert een synchronisatie uit.</p></td>
  </tr>
  <tr>
   <td><p>3</p></td>
   <td><p>Gebruikersgegevens worden bijgewerkt.</p></td>
  </tr>
  <tr>
   <td><p>4</p></td>
   <td><p>Een gebruiker kan de bijgewerkte gebruikersinformatie bekijken. </p></td>
  </tr>
 </tbody>
</table>

### Overzicht van de stappen {#summary_of_steps-6}

Voer de volgende stappen uit om gebruikers programmatisch te synchroniseren:

1. Inclusief projectbestanden.
1. Maak een UserManagerUtilServiceClient-client.
1. Geef het ondernemingsdomein op.
1. Roep de verificatiebewerking aan.
1. Bepalen of de synchronisatiebewerking is voltooid

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u ervoor zorgen dat u de proxybestanden opneemt.

**Een UserManagerUtilServiceClientclient maken**

Voordat u gebruikers programmatisch kunt synchroniseren, moet u een `UserManagerUtilServiceClient` object.

**Het ondernemingsdomein opgeven**

Voordat u een synchronisatiebewerking uitvoert met de API voor gebruikersbeheer, geeft u het ondernemingsdomein op waartoe gebruikers behoren. U kunt een of meerdere ondernemingsdomeinen opgeven. Alvorens u een synchronisatieverrichting programmatically kunt uitvoeren, moet u een ondernemingsdomein opstelling gebruikend de Console van het Beleid. (Zie [administratie Help](https://www.adobe.com/go/learn_aemforms_admin_63).)

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

   Een `UserManagerUtilServiceClient` object door de constructor ervan te gebruiken en een `ServiceClientFactory` object dat verbindingseigenschappen bevat.

1. Geef het ondernemingsdomein op.

   * De `UserManagerUtilServiceClient` object `scheduleSynchronization` methode om de gebruikerssynchronisatiebewerking te starten.
   * Een `java.util.Set` instantie door een `HashSet` constructor. Zorg ervoor dat u `String` als het gegevenstype. Dit `Java.util.Set` slaat de instantie de domeinnamen op waarop de synchronisatiebewerking van toepassing is.
   * Voor elke domeinnaam die moet worden toegevoegd, roept u het `java.util.Set` voegt methode toe en geeft de domeinnaam door.

1. Roep de synchronisatiebewerking aan.

   De `ServiceClientFactory` object `getContext` methode, die een `Context` object.

   Roep vervolgens het `Context` object `initPrincipal` en geeft de `AuthResult`.

**Zie ook**

[Gebruikers programmatisch synchroniseren](users.md#programmatically-synchronizing-users)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)
