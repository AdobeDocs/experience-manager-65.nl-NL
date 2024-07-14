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
feature: Adaptive Forms
source-git-commit: 9f59606bb58b9e90f07bd22e89f3213afb54a697
workflow-type: tm+mt
source-wordcount: '6201'
ht-degree: 0%

---

# Gebruikers beheren {#managing-users}

**de Steekproeven en de voorbeelden in dit document zijn slechts voor AEM Forms op milieu JEE.**

**Ongeveer Gebruikersbeheer**

U kunt de API voor gebruikersbeheer gebruiken om clienttoepassingen te maken die rollen, machtigingen en principes (die gebruikers of groepen kunnen zijn) kunnen beheren en gebruikers kunnen verifiëren. Gebruikersbeheer-API bestaat uit de volgende AEM Forms API&#39;s:

* Directory Manager-service-API
* API voor verificatiebeheer
* Authorization Manager Service API

Met Gebruikersbeheer kunt u rollen en machtigingen toewijzen, verwijderen en bepalen. Het laat u ook toe om, domeinen, gebruikers, en groepen toe te wijzen te verwijderen en te vragen. Tot slot kunt u Gebruikersbeheer gebruiken om gebruikers voor authentiek te verklaren.

In [ Toevoegend Gebruikers ](users.md#adding-users) u zult begrijpen hoe te gebruikers programmatically toe te voegen. In deze sectie wordt de directoryservice-API gebruikt.

In [ het Schrappen van Gebruikers ](users.md#deleting-users) zult u begrijpen hoe te gebruikers programmatically te schrappen. In deze sectie wordt de directoryservice-API gebruikt.

In [ het Leiden Gebruikers en Groepen ](users.md#managing-users-and-groups) zult u het verschil tussen een lokale gebruiker en een foldergebruiker begrijpen, en voorbeelden van zien hoe te om Java en de Webdienst APIs te gebruiken om gebruikers en groepen programmatically te beheren. In deze sectie wordt de directoryservice-API gebruikt.

In [ het Leiden Rollen en Toestemmingen ](users.md#managing-roles-and-permissions) zult u over de systeemrollen en toestemmingen leren en wat u programmatically kunt doen om hen te verhogen, en voorbeelden van zien hoe te om Java en de Webdienst APIs te gebruiken om rollen en toestemmingen programmatically te beheren. Deze sectie gebruikt zowel de API van de Dienst van de Manager van de Folder als de Dienst API van de Manager van de Vergunning.

In [ voor authentiek verklaren Gebruikers ](users.md#authenticating-users) zult u voorbeelden van zien hoe te om Java en de Webdienst APIs te gebruiken om gebruikers programmatically voor authentiek te verklaren. Deze sectie gebruikt de Service API van de Manager van de Vergunning.

**Begrijpend het authentificatieproces**

Gebruikersbeheer biedt ingebouwde verificatiefunctionaliteit en biedt u ook de mogelijkheid om deze te verbinden met uw eigen verificatieprovider. Wanneer het Beheer van de Gebruiker een authentificatieverzoek ontvangt (bijvoorbeeld, probeert een gebruiker om binnen te registreren), gaat het gebruikersinformatie tot de authentificatieleverancier over om voor authentiek te verklaren. Gebruikersbeheer ontvangt de resultaten van de verificatieprovider nadat de gebruiker is geverifieerd.

Het volgende diagram toont de interactie onder een eind - gebruiker die aan login, Gebruikersbeheer, en de authentificatieleverancier probeert.

![ mu_mu_umauth_process ](assets/mu_mu_umauth_process.png)

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

**Begrijpend folderbeheer**

Gebruikersbeheer wordt verpakt met een directoryserviceprovider (de DirectoryManagerService) die verbindingen met LDAP-directory&#39;s ondersteunt. Als uw organisatie een niet-LDAP-opslagplaats gebruikt om gebruikersverslagen op te slaan, kunt u uw eigen folder dienstverlener tot stand brengen die met uw bewaarplaats werkt.

De dienstverleners van de folder winnen verslagen van een gebruikersopslag op verzoek van het Beheer van de Gebruiker terug. Gebruikersbeheer slaat gebruikers- en groepsrecords in de database regelmatig in de cache op om de prestaties te verbeteren.

De provider van de directoryservice kan worden gebruikt om de gebruikersbeheerdatabase te synchroniseren met de opslag van de gebruiker. Deze stap zorgt ervoor dat alle informatie van de gebruikersfolder en alle gebruiker en groepsverslagen bijgewerkt zijn.

Bovendien voorziet DirectoryManagerService u van de capaciteit om domeinen tot stand te brengen en te beheren. Domeinen definiëren verschillende gebruikersbasen. De grens van een domein wordt gewoonlijk bepaald volgens de manier uw organisatie gestructureerd is of hoe uw gebruikersopslag opstelling is. De domeinen van het Beheer van de gebruiker verstrekken configuratiemontages die de authentificatieleveranciers en de leveranciers van de folderdienst gebruiken.

In de configuratie XML die het Beheer van de Gebruiker uitvoert, bevat de wortelknoop die de attributenwaarde van `Domains` heeft een element van XML voor elk domein dat voor Gebruikersbeheer wordt bepaald. Elk van deze elementen bevat andere elementen die aspecten van het domein verbonden aan specifieke dienstverleners bepalen.

**Begrijpend objectenSID waarden**

Wanneer het gebruiken van Actieve Folder, is het belangrijk om te begrijpen dat een `objectSID` waarde geen uniek attribuut over veelvoudige domeinen is. Met deze waarde wordt de beveiligings-id van een object opgeslagen. In een omgeving met meerdere domeinen (bijvoorbeeld een structuur met domeinen) kan de waarde van `objectSID` anders zijn.

Een `objectSID` -waarde verandert als een object van het ene Active Directory-domein naar het andere wordt verplaatst. Sommige objecten hebben overal in het domein dezelfde `objectSID` waarde. Groepen zoals BUILTIN\Administrators, BUILTIN\Power Users, enzovoort, zouden bijvoorbeeld dezelfde `objectSID` -waarde hebben, ongeacht de domeinen. Deze `objectSID` -waarden zijn bekend.

## Gebruikers toevoegen {#adding-users}

U kunt de API voor directoryservice (Java en webservice) gebruiken om gebruikers programmatisch aan AEM Forms toe te voegen. Nadat u een gebruiker hebt toegevoegd, kunt u die gebruiker gebruiken wanneer u een servicebewerking uitvoert waarvoor een gebruiker nodig is. U kunt bijvoorbeeld een taak toewijzen aan de nieuwe gebruiker.

### Overzicht van de stappen {#summary-of-steps}

Voer de volgende stappen uit om een gebruiker toe te voegen:

1. Inclusief projectbestanden.
1. Creeer een cliënt DirectoryManagerService.
1. Gebruikersgegevens definiëren.
1. Voeg de gebruiker toe aan AEM Forms.
1. Controleer of de gebruiker is toegevoegd.

**omvat projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, neemt u de proxybestanden op.

**creeer een cliënt DirectoryManagerService**

Alvorens u een de dienstverrichting van de Manager van de Folder programmatically kunt uitvoeren, creeer een cliënt van de Dienst API van de Manager van de Folder.

**bepalen gebruikersinformatie**

Wanneer u een nieuwe gebruiker door de Dienst API van de Manager van de Folder te gebruiken toevoegt, bepaal informatie voor die gebruiker. Wanneer u een nieuwe gebruiker toevoegt, definieert u doorgaans de volgende waarden:

* **naam van het Domein**: Het domein waartot de gebruiker (bijvoorbeeld, `DefaultDom`) behoort.
* **waarde van het herkenningsteken van de Gebruiker**: De herkenningstekenwaarde van de gebruiker (bijvoorbeeld, `wblue`).
* **Belangrijkste type**: Het type van gebruiker (bijvoorbeeld, kunt u specificeren `USER)`.
* **Gegeven naam**: Een bepaalde naam voor de gebruiker (bijvoorbeeld, `Wendy`).
* **Naam van de Familie**: De familienaam voor de gebruiker (bijvoorbeeld, `Blue)`.
* **Landinstelling**: De informatie van de Plaats voor de gebruiker.

**voeg de gebruiker aan AEM Forms** toe

Nadat u gebruikersgegevens hebt gedefinieerd, kunt u de gebruiker aan AEM Forms toevoegen. Als u een gebruiker wilt toevoegen, roept u de methode `createLocalUser` van het object `DirectoryManagerServiceClient` aan.

**verifieer dat de gebruiker** werd toegevoegd

U kunt controleren of de gebruiker is toegevoegd om ervoor te zorgen dat er geen problemen zijn opgetreden. Zoek de nieuwe gebruiker met de waarde van de gebruikersidentificatie.

**zie ook**

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

   Maak een `DirectoryManagerServiceClient` -object door de constructor ervan te gebruiken en een `ServiceClientFactory` -object door te geven dat verbindingseigenschappen bevat.

1. Gebruikersgegevens definiëren.

   * Maak een `UserImpl` -object met behulp van de constructor.
   * Stel de naam van het domein in door de methode `setDomainName` van het object `UserImpl` aan te roepen. Geef een tekenreekswaarde door die de domeinnaam opgeeft.
   * Stel het hoofdtype in door de methode `setPrincipalType` van het object `UserImpl` aan te roepen. Geef een tekenreekswaarde door die het type gebruiker aangeeft. U kunt bijvoorbeeld `USER` opgeven.
   * Stel de waarde van de gebruikersidentificatie in door de methode `setUserid` van het object `UserImpl` aan te roepen. Geef een tekenreekswaarde door die de waarde van de gebruikersidentificatie aangeeft. U kunt bijvoorbeeld `wblue` opgeven.
   * Stel de canonieke naam in door de methode `setCanonicalName` van het object `UserImpl` aan te roepen. Geef een tekenreekswaarde door die de canonieke naam van de gebruiker aangeeft. U kunt bijvoorbeeld `wblue` opgeven.
   * Stel de opgegeven naam in door de methode `setGivenName` van het object `UserImpl` aan te roepen. Geef een tekenreekswaarde door die de opgegeven naam van de gebruiker aangeeft. U kunt bijvoorbeeld `Wendy` opgeven.
   * Stel de familienaam in door de methode `setFamilyName` van het object `UserImpl` aan te roepen. Geef een tekenreekswaarde door die de familienaam van de gebruiker aangeeft. U kunt bijvoorbeeld `Blue` opgeven.

   >[!NOTE]
   >
   >Roep een methode aan die tot het `UserImpl` -object behoort om andere waarden in te stellen. U kunt bijvoorbeeld de waarde van de landinstelling instellen door de methode `setLocale` van het object `UserImpl` aan te roepen.

1. Voeg de gebruiker toe aan AEM Forms.

   Roep de methode `createLocalUser` van het object `DirectoryManagerServiceClient` aan en geef de volgende waarden door:

   * Het `UserImpl` -object dat de nieuwe gebruiker vertegenwoordigt
   * Een tekenreekswaarde die het wachtwoord van de gebruiker vertegenwoordigt

   De methode `createLocalUser` retourneert een tekenreekswaarde die de lokale id-waarde van de gebruiker opgeeft.

1. Controleer of de gebruiker is toegevoegd.

   * Maak een `PrincipalSearchFilter` -object met behulp van de constructor.
   * Stel de waarde van de gebruikersidentificatie in door de methode `setUserId` van het object `PrincipalSearchFilter` aan te roepen. Geef een tekenreekswaarde door die de waarde van de gebruikersidentificatie vertegenwoordigt.
   * Roep de methode `findPrincipals` van het object `DirectoryManagerServiceClient` aan en geef het object `PrincipalSearchFilter` door. Deze methode retourneert een `java.util.List` -instantie, waarbij elk element een `User` -object is. Doorloop de instantie van `java.util.List` om de gebruiker te zoeken.

**zie ook**

[Overzicht van de stappen](users.md#summary-of-steps)

[Snel starten (SOAP modus): gebruikers toevoegen met de Java API](/help/forms/developing/user-manager-java-api-quick.md#quick-start-soap-mode-adding-users-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Gebruikers toevoegen met de webservice-API {#add-users-using-the-web-service-api}

Voeg gebruikers toe met de API (webservice) van Directory Manager:

1. Inclusief projectbestanden.

   Creeer een Microsoft .NET project dat MTOM gebruikt. Controleer of u de volgende WSDL-definitie gebruikt voor de serviceverwijzing: `http://localhost:8080/soap/services/DirectoryManagerService?WSDL&lc_version=9.0.1` .

   >[!NOTE]
   >
   >Vervang `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Creeer een cliënt DirectoryManagerService.

   * Maak een `DirectoryManagerServiceClient` -object met de standaardconstructor.
   * Maak een `DirectoryManagerServiceClient.Endpoint.Address` -object met de `System.ServiceModel.EndpointAddress` -constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/DirectoryManagerService?blob=mtom` ). U hoeft het attribuut `lc_version` niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt. Zorg ervoor dat u `?blob=mtom` opgeeft.
   * Maak een `System.ServiceModel.BasicHttpBinding` -object door de waarde van het `DirectoryManagerServiceClient.Endpoint.Binding` -veld op te halen. De geretourneerde waarde wordt gecast naar `BasicHttpBinding` .
   * Stel het veld `MessageEncoding` van het `System.ServiceModel.BasicHttpBinding` -object in op `WSMessageEncoding.Mtom` . Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld `DirectoryManagerServiceClient.ClientCredentials.UserName.UserName` toe.
      * Wijs de bijbehorende wachtwoordwaarde toe aan het veld `DirectoryManagerServiceClient.ClientCredentials.UserName.Password` .
      * Wijs de constante waarde `HttpClientCredentialType.Basic` toe aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType` .
      * Wijs de constante waarde `BasicHttpSecurityMode.TransportCredentialOnly` toe aan het veld `BasicHttpBindingSecurity.Security.Mode` .

1. Gebruikersgegevens definiëren.

   * Maak een `UserImpl` -object met behulp van de constructor.
   * Stel de naam van het domein in door een tekenreekswaarde toe te wijzen aan het veld `domainName` van het `UserImpl` -object.
   * Stel het hoofdtype in door een tekenreekswaarde toe te wijzen aan het veld `principalType` van het `UserImpl` -object. U kunt bijvoorbeeld `USER` opgeven.
   * Stel de waarde van de gebruikersidentificatie in door een tekenreekswaarde toe te wijzen aan het veld `userid` van het `UserImpl` -object.
   * Stel de canonieke naamwaarde in door een tekenreekswaarde toe te wijzen aan het veld `canonicalName` van het `UserImpl` -object.
   * Stel de opgegeven naamwaarde in door een tekenreekswaarde toe te wijzen aan het veld `givenName` van het `UserImpl` -object.
   * Stel de naam van de familie in door een tekenreekswaarde toe te wijzen aan het veld `familyName` van het `UserImpl` -object.

1. Voeg de gebruiker toe aan AEM Forms.

   Roep de methode `createLocalUser` van het object `DirectoryManagerServiceClient` aan en geef de volgende waarden door:

   * Het `UserImpl` -object dat de nieuwe gebruiker vertegenwoordigt
   * Een tekenreekswaarde die het wachtwoord van de gebruiker vertegenwoordigt

   De methode `createLocalUser` retourneert een tekenreekswaarde die de lokale id-waarde van de gebruiker opgeeft.

1. Controleer of de gebruiker is toegevoegd.

   * Maak een `PrincipalSearchFilter` -object met behulp van de constructor.
   * Stel de gebruiker-id-waarde van de gebruiker in door een tekenreekswaarde toe te wijzen die de gebruiker-id-waarde vertegenwoordigt aan het veld `userId` van het `PrincipalSearchFilter` -object.
   * Roep de methode `findPrincipals` van het object `DirectoryManagerServiceClient` aan en geef het object `PrincipalSearchFilter` door. Deze methode retourneert een `MyArrayOfUser` -verzamelingsobject, waarbij elk element een `User` -object is. Doorloop de `MyArrayOfUser` -verzameling om de gebruiker te zoeken.

**zie ook**

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

**omvat projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, neemt u de proxybestanden op.

**creeer een cliënt DirectoryManagerService**

Alvorens u programmatically een verrichting van de Dienst API van de Manager van de Folder kunt uitvoeren, creeer een de dienstcliënt van de Manager van de Folder.

**specificeer de te schrappen gebruiker**

U kunt opgeven dat een gebruiker moet worden verwijderd met de id-waarde van de gebruiker.

**Schrap de gebruiker van AEM Forms**

Als u een gebruiker wilt verwijderen, roept u de methode `deleteLocalUser` van het object `DirectoryManagerServiceClient` aan.

**zie ook**

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

   Maak een `DirectoryManagerServiceClient` -object door de constructor ervan te gebruiken en een `ServiceClientFactory` -object door te geven dat verbindingseigenschappen bevat.

1. Geef de gebruiker op die u wilt verwijderen.

   * Maak een `PrincipalSearchFilter` -object met behulp van de constructor.
   * Stel de waarde van de gebruikersidentificatie in door de methode `setUserId` van het object `PrincipalSearchFilter` aan te roepen. Geef een tekenreekswaarde door die de waarde van de gebruikersidentificatie vertegenwoordigt.
   * Roep de methode `findPrincipals` van het object `DirectoryManagerServiceClient` aan en geef het object `PrincipalSearchFilter` door. Deze methode retourneert een `java.util.List` -instantie, waarbij elk element een `User` -object is. Doorloop de instantie van `java.util.List` om te zoeken naar de gebruiker die u wilt verwijderen.

1. Verwijder de gebruiker uit AEM Forms.

   Roep de methode `deleteLocalUser` van het object `DirectoryManagerServiceClient` aan en geef de waarde van het veld `oid` van het object `User` door. Roep de methode `getOid` van het object `User` aan. Gebruik het `User` -object dat is opgehaald uit de `java.util.List` -instantie.

**zie ook**

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

   * Maak een `DirectoryManagerServiceClient` -object met de standaardconstructor.
   * Maak een `DirectoryManagerServiceClient.Endpoint.Address` -object met de `System.ServiceModel.EndpointAddress` -constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/DirectoryManagerService?blob=mtom` ). U hoeft het attribuut `lc_version` niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt. Zorg ervoor dat u opgeeft `blob=mtom.`
   * Maak een `System.ServiceModel.BasicHttpBinding` -object door de waarde van het `DirectoryManagerServiceClient.Endpoint.Binding` -veld op te halen. De geretourneerde waarde wordt gecast naar `BasicHttpBinding` .
   * Stel het veld `MessageEncoding` van het `System.ServiceModel.BasicHttpBinding` -object in op `WSMessageEncoding.Mtom` . Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld `DirectoryManagerServiceClient.ClientCredentials.UserName.UserName` toe.
      * Wijs de bijbehorende wachtwoordwaarde toe aan het veld `DirectoryManagerServiceClient.ClientCredentials.UserName.Password` .
      * Wijs de constante waarde `HttpClientCredentialType.Basic` toe aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType` .
      * Wijs de constante waarde `BasicHttpSecurityMode.TransportCredentialOnly` toe aan het veld `BasicHttpBindingSecurity.Security.Mode` .

1. Geef de gebruiker op die u wilt verwijderen.

   * Maak een `PrincipalSearchFilter` -object met behulp van de constructor.
   * Stel de waarde van de gebruikersidentificatie in door een tekenreekswaarde toe te wijzen aan het veld `userId` van het `PrincipalSearchFilter` -object.
   * Roep de methode `findPrincipals` van het object `DirectoryManagerServiceClient` aan en geef het object `PrincipalSearchFilter` door. Deze methode retourneert een `MyArrayOfUser` -verzamelingsobject, waarbij elk element een `User` -object is. Doorloop de `MyArrayOfUser` -verzameling om de gebruiker te zoeken. Het `User` -object dat is opgehaald uit het `MyArrayOfUser` -verzamelingsobject, wordt gebruikt om de gebruiker te verwijderen.

1. Verwijder de gebruiker uit AEM Forms.

   Verwijder de gebruiker door de veldwaarde `oid` van het `User` -object door te geven aan de methode `DirectoryManagerServiceClient` van het object `deleteLocalUser` .

**zie ook**

[Overzicht van de stappen](users.md#summary-of-steps)

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Groepen maken {#creating-groups}

U kunt de API voor directoryservice (Java en webservice) gebruiken om AEM Forms-groepen programmatisch te maken. Nadat u een groep creeert, kunt u die groep gebruiken om een de dienstverrichting uit te voeren die een groep vereist. U kunt bijvoorbeeld een gebruiker aan de nieuwe groep toewijzen. (Zie [ het Leiden Gebruikers en Groepen ](users.md#managing-users-and-groups).)

### Overzicht van de stappen {#summary_of_steps-2}

Voer de volgende stappen uit om een groep te maken:

1. Inclusief projectbestanden.
1. Creeer een cliënt DirectoryManagerService.
1. Bepaal of de groep niet bestaat.
1. Maak de groep.
1. Voer een handeling uit met de groep.

**omvat projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-utilities.jar (Vereist als AEM Forms wordt geïmplementeerd op JBoss)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)

Voor informatie over de plaats van deze JAR dossiers, zie [ Inclusief de bibliotheekdossiers van AEM Forms Java ](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**creeer een cliënt DirectoryManagerService**

Alvorens u een de dienstverrichting van de Manager van de Folder programmatically kunt uitvoeren, creeer een cliënt van de Dienst API van de Manager van de Folder.

**bepaalt of de groep** bestaat

Wanneer u een groep maakt, moet u ervoor zorgen dat de groep niet in hetzelfde domein bestaat. Twee groepen kunnen dus niet dezelfde naam binnen hetzelfde domein hebben. Voor deze taak voert u een zoekopdracht uit en filtert u de zoekresultaten op basis van twee waarden. Stel het hoofdtype in op `com.adobe.idp.um.api.infomodel.Principal.PRINCIPALTYPE_GROUP` om ervoor te zorgen dat alleen groepen worden geretourneerd. Zorg er ook voor dat u de domeinnaam opgeeft.

**creeer de groep**

Nadat u hebt bepaald dat de groep niet bestaat in het domein, maakt u de groep en geeft u de volgende kenmerken op:

* **CommonName**: De naam van de groep.
* **Domein**: Het domein waarin de groep wordt toegevoegd.
* **Beschrijving**: Een beschrijving van de groep.

**voer een actie met de groep** uit

Nadat u een groep hebt gemaakt, kunt u een actie uitvoeren met de groep. U kunt bijvoorbeeld een gebruiker aan de groep toevoegen. Als u een gebruiker aan een groep wilt toevoegen, haalt u de unieke id-waarde van zowel de gebruiker als de groep op. Geef deze waarden door aan de methode `addPrincipalToLocalGroup` .

**zie ook**

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

   Maak een `DirectoryManagerServiceClient` -object door de constructor ervan te gebruiken en een `ServiceClientFactory` -object door te geven dat verbindingseigenschappen bevat.

1. Bepaal of de groep bestaat.

   * Maak een `PrincipalSearchFilter` -object met behulp van de constructor.
   * Stel het hoofdtype in door het object `setPrincipalType` van het object `PrincipalSearchFilter` aan te roepen. Geef de waarde `com.adobe.idp.um.api.infomodel.Principal.PRINCIPALTYPE_GROUP` door.
   * Stel het domein in door het `PrincipalSearchFilter` -object `setSpecificDomainName` van het object aan te roepen. Geef een tekenreekswaarde door die de domeinnaam opgeeft.
   * Als u een groep wilt zoeken, roept u de methode `findPrincipals` van het `DirectoryManagerServiceClient` -object aan (een principal kan een groep zijn). Geef het `PrincipalSearchFilter` -object door dat het hoofdtype en de domeinnaam opgeeft. Deze methode retourneert een `java.util.List` -instantie waarbij elk element een `Group` -instantie is. Elke groepsinstantie past zich aan het filter aan dat is opgegeven met het object `PrincipalSearchFilter` .
   * Doorloop de instantie `java.util.List` . Haal voor elk element de groepsnaam op. Zorg ervoor dat de groepsnaam niet gelijk is aan de nieuwe groepsnaam.

1. Maak de groep.

   * Als de groep niet bestaat, roept u de methode `setCommonName` van het `Group` -object aan en geeft u een tekenreekswaarde door die de groepsnaam opgeeft.
   * Roep de methode `setDescription` van het object `Group` aan en geef een tekenreekswaarde door die de beschrijving van de groep aangeeft.
   * Roep de methode `setDomainName` van het object `Group` aan en geef een tekenreekswaarde door die de domeinnaam opgeeft.
   * Roep de methode `createLocalGroup` van het object `DirectoryManagerServiceClient` aan en geef de instantie `Group` door.

   De methode `createLocalUser` retourneert een tekenreekswaarde die de lokale id-waarde van de gebruiker opgeeft.

1. Voer een handeling uit met de groep.

   * Maak een `PrincipalSearchFilter` -object met behulp van de constructor.
   * Stel de waarde van de gebruikersidentificatie in door de methode `setUserId` van het object `PrincipalSearchFilter` aan te roepen. Geef een tekenreekswaarde door die de waarde van de gebruikersidentificatie vertegenwoordigt.
   * Roep de methode `findPrincipals` van het object `DirectoryManagerServiceClient` aan en geef het object `PrincipalSearchFilter` door. Deze methode retourneert een `java.util.List` -instantie, waarbij elk element een `User` -object is. Doorloop de instantie van `java.util.List` om de gebruiker te zoeken.
   * Voeg een gebruiker aan de groep toe door de methode `addPrincipalToLocalGroup` van het object `DirectoryManagerServiceClient` aan te roepen. Geef de geretourneerde waarde van de methode `getOid` van het object `User` door. Geef de geretourneerde waarde van de methode `getOid` van de `Group` -objecten door (gebruik de `Group` -instantie die de nieuwe groep vertegenwoordigt).

**zie ook**

[Overzicht van de stappen](users.md#summary-of-steps)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Gebruikers en groepen beheren {#managing-users-and-groups}

Dit onderwerp beschrijft hoe u (Java) kunt gebruiken om, domeinen, gebruikers, en groepen programmatically toe te wijzen te verwijderen.

>[!NOTE]
>
>Wanneer het vormen van een domein, moet u het unieke herkenningsteken voor groepen en gebruikers plaatsen. Het kenmerk dat wordt gekozen, moet niet alleen uniek zijn binnen de LDAP-omgeving, maar moet ook onveranderlijk zijn en niet worden gewijzigd binnen de directory. Dit attribuut moet ook van een eenvoudig type van koordgegevens zijn (de enige uitzondering momenteel toegestaan voor Actieve Folder 2000/2003 is `"objectsid"`, die een binaire waarde is). Het kenmerk Novell eDirectory `"GUID"` is bijvoorbeeld geen eenvoudig gegevenstype voor tekenreeksen en werkt daarom niet.

* Gebruik `"objectsid"` voor Active Directory.
* Gebruik `"nsuniqueid"` voor SunOne.

>[!NOTE]
>
>Het maken van meerdere lokale gebruikers en groepen terwijl een LDAP-directorysynchronisatie wordt uitgevoerd, wordt niet ondersteund. Als u dit proces probeert uit te voeren, kunnen fouten optreden.

### Overzicht van de stappen {#summary_of_steps-3}

Voer de volgende stappen uit om gebruikers en groepen te beheren:

1. Inclusief projectbestanden.
1. Creeer een cliënt DirectoryManagerService.
1. Roep de juiste gebruikers- of groepsbewerkingen aan.

**omvat projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u ervoor zorgen dat u de proxybestanden opneemt.

**creeer een cliënt DirectoryManagerService**

Alvorens u een de dienstverrichting van de Manager van de Folder programmatically kunt uitvoeren, moet u een de dienstcliënt van de Manager van de Folder creëren. Met de Java API wordt dit gedaan door een `DirectoryManagerServiceClient` -object te maken. Met de webservice-API wordt dit bereikt door een `DirectoryManagerServiceService` -object te maken.

**Roep de aangewezen gebruiker of groepsverrichtingen** aan

Zodra u de de dienstcliënt hebt gecreeerd, kunt u de gebruiker of de verrichtingen van het groepsbeheer dan aanhalen. De de dienstcliënt laat u, domeinen, gebruiker, en groepen toewijzen verwijderen. Merk op dat het of een folderhoofd of een lokale hoofd aan een lokale groep kan toevoegen, maar het is niet mogelijk om een lokale hoofd aan een foldergroep toe te voegen.

**zie ook**

[Gebruikers en groepen beheren met de Java API](users.md#managing-users-and-groups-using-the-java-api)

[Gebruikers en groepen beheren met de webservice-API](users.md#managing-users-and-groups-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[API voor gebruikersbeheer - Snel aan de slag](/help/forms/developing/user-manager-java-api-quick.md#user-manager-java-api-quick-start-soap)

### Gebruikers en groepen beheren met de Java API {#managing-users-and-groups-using-the-java-api}

Voer de volgende taken uit om gebruikers, groepen en domeinen programmatisch te beheren met behulp van de map (Java):

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-usermanager-client.jar, op in het klassenpad van uw Java-project. Voor informatie over de plaats van deze dossiers, zie [ Inclusief de bibliotheekdossiers van AEM Forms Java ](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

1. Creeer een cliënt DirectoryManagerService.

   Maak een `DirectoryManagerServiceClient` -object door de constructor ervan te gebruiken en een `ServiceClientFactory` -object door te geven dat verbindingseigenschappen bevat. Voor informatie, zie [ Plaatsende verbindingseigenschappen ](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)*.*

1. Roep de juiste gebruikers- of groepsbewerkingen aan.

   Als u een gebruiker of groep wilt zoeken, roept u een van de methoden van het object `DirectoryManagerServiceClient` aan om principes te zoeken (aangezien een principal een gebruiker of een groep kan zijn). In het onderstaande voorbeeld wordt de methode `findPrincipals` aangeroepen met een zoekfilter (een `PrincipalSearchFilter` -object).

   Aangezien de geretourneerde waarde in dit geval een `java.util.List` bevattende `Principal` -objecten is, doorloopt u het resultaat en cast u de `Principal` -objecten naar `User` - of `Group` -objecten.

   Met het resulterende `User` - of `Group` -object (dat beide overerft van de `Principal` -interface) haalt u de informatie op die u in uw workflows nodig hebt. De domeinnaam en canonieke naamwaarden vormen samen bijvoorbeeld een unieke identificatie van een principal. Deze worden opgehaald door respectievelijk de methoden `getDomainName` en `getCanonicalName` van het `Principal` -object aan te roepen.

   Als u een lokale gebruiker wilt verwijderen, roept u de methode `deleteLocalUser` van het object `DirectoryManagerServiceClient` aan en geeft u de id van de gebruiker door.

   Als u een lokale groep wilt verwijderen, roept u de methode `deleteLocalGroup` van het object `DirectoryManagerServiceClient` aan en geeft u de id van de groep door.

**zie ook**

[Overzicht van de stappen](users.md#summary-of-steps)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Gebruikers en groepen beheren met de webservice-API {#managing-users-and-groups-using-the-web-service-api}

Om gebruikers, groepen, en domeinen programmatically te beheren gebruikend de Dienst API van de Manager van de Folder (Webdienst), voer de volgende taken uit:

1. Inclusief projectbestanden.

   * Creeer een Microsoft .NET cliëntassemblage die de Manager WSDL van de Folder verbruikt. (Zie [ het Aanhalen van AEM Forms gebruikend Base64 het coderen ](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding).)
   * Verwijs naar de Microsoft .NET cliëntassemblage. (Zie [ Creërend een .NET cliëntassemblage die het coderen Base64 ](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding) gebruikt.)

1. Creeer een cliënt DirectoryManagerService.

   Maak een `DirectoryManagerServiceService` -object met behulp van de constructor van de proxyklasse.

1. Roep de juiste gebruikers- of groepsbewerkingen aan.

   Als u een gebruiker of groep wilt zoeken, roept u een van de methoden van het object `DirectoryManagerServiceService` aan om principes te zoeken (aangezien een principal een gebruiker of een groep kan zijn). In het onderstaande voorbeeld wordt de methode `findPrincipalsWithFilter` aangeroepen met een zoekfilter (een `PrincipalSearchFilter` -object). Wanneer u een `PrincipalSearchFilter` -object gebruikt, worden lokale hoofdbeginselen alleen geretourneerd als de `isLocal` -eigenschap is ingesteld op `true` . Dit gedrag verschilt van wat er zou gebeuren met de Java API.

   >[!NOTE]
   >
   >Als het maximale aantal resultaten niet is opgegeven in het zoekfilter (via het `PrincipalSearchFilter.resultsMax` -veld), worden maximaal 1000 resultaten geretourneerd. Dit gedrag is anders dan wat er gebeurt met de Java API, waarbij 10 resultaten het standaardmaximum zijn. Zoekmethoden zoals `findGroupMembers` leveren ook alleen resultaten op als het maximale aantal resultaten is opgegeven in het zoekfilter (bijvoorbeeld via het `GroupMembershipSearchFilter.resultsMax` -veld). Dit geldt voor alle zoekfilters die overerven van de klasse `GenericSearchFilter` . Voor meer informatie, zie [ AEM Forms API Verwijzing ](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

   Aangezien de geretourneerde waarde in dit geval een `object[]` bevattende `Principal` -objecten is, doorloopt u het resultaat en cast u de `Principal` -objecten naar `User` - of `Group` -objecten.

   Met het resulterende `User` - of `Group` -object (dat beide overerft van de `Principal` -interface) haalt u de informatie op die u in uw workflows nodig hebt. De domeinnaam en canonieke naamwaarden vormen samen bijvoorbeeld een unieke identificatie van een principal. Deze worden opgehaald door respectievelijk de velden `domainName` en `canonicalName` van het `Principal` -object aan te roepen.

   Als u een lokale gebruiker wilt verwijderen, roept u de methode `deleteLocalUser` van het object `DirectoryManagerServiceService` aan en geeft u de id van de gebruiker door.

   Als u een lokale groep wilt verwijderen, roept u de methode `deleteLocalGroup` van het object `DirectoryManagerServiceService` aan en geeft u de id van de groep door.

**zie ook**

[Overzicht van de stappen](users.md#summary-of-steps)

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

## Rollen en machtigingen beheren {#managing-roles-and-permissions}

Dit onderwerp beschrijft hoe u de Dienst API van de Manager van de Vergunning (Java) kunt gebruiken om, rollen en toestemmingen programmatically toe te wijzen te verwijderen en te bepalen.

In AEM Forms, is de a *rol* een groep toestemmingen voor de toegang tot van één of meerdere systeem-vlakke middelen. Deze toestemmingen worden gecreeerd door het Beheer van de Gebruiker en door de de dienstcomponenten afgedwongen. Een beheerder kan bijvoorbeeld de rol &quot;Policy Set Author&quot; aan een groep gebruikers toewijzen. Het Rights Management zou dan de gebruikers van die groep met die rol toestaan om beleidsreeksen door beleidsconsole tot stand te brengen.

Er zijn twee soorten rollen: *standaardrollen* en *douanerollen*. De standaardrollen (*systeemrollen)* zijn reeds ingezetene in AEM Forms. Aangenomen wordt dat standaardrollen niet door de beheerder kunnen worden verwijderd of gewijzigd en dus onveranderlijk zijn. Aangepaste rollen die door de beheerder zijn gemaakt en die vervolgens kunnen worden gewijzigd of verwijderd, zijn dus veranderbaar.

Rollen maken het eenvoudiger om machtigingen te beheren. Wanneer een rol aan een hoofd wordt toegewezen, wordt een reeks toestemmingen automatisch toegewezen aan dat hoofd, en alle specifieke op toegang betrekking hebbende besluiten voor het hoofd zijn gebaseerd op die algemene reeks toegewezen toestemmingen.

### Overzicht van de stappen {#summary_of_steps-4}

Voer de volgende stappen uit om rollen en machtigingen te beheren:

1. Inclusief projectbestanden.
1. Maak een AuthorizationManagerService-client.
1. Roep de juiste rol- of machtigingsbewerkingen aan.

**omvat projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u ervoor zorgen dat u de proxybestanden opneemt.

**creeer een cliënt AuthorizationManagerService**

Alvorens u een verrichting van AuthorizationManagerService van het Beheer van de Gebruiker programmatically kunt uitvoeren, moet u een cliënt AuthorizationManagerService tot stand brengen. Met de Java API wordt dit gedaan door een `AuthorizationManagerServiceClient` -object te maken.

**voke de aangewezen rol of toestemmingsverrichtingen**

Zodra u de de dienstcliënt hebt gecreeerd, kunt u de rol of toestemmingsverrichtingen dan aanhalen. De de dienstcliënt laat u, rollen en toestemmingen toewijzen verwijderen en bepalen.

**zie ook**

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

   Maak een `AuthorizationManagerServiceClient` -object door de constructor ervan te gebruiken en een `ServiceClientFactory` -object door te geven dat verbindingseigenschappen bevat.

1. Roep de juiste rol- of machtigingsbewerkingen aan.

   Als u een rol wilt toewijzen aan een principal, roept u de methode `assignRole` van het object `AuthorizationManagerServiceClient` op en geeft u de volgende waarden door:

   * Een `java.lang.String` -object dat de rol-id bevat
   * Een array van `java.lang.String` -objecten met de belangrijkste id&#39;s.

   Als u een rol wilt verwijderen uit de principal, roept u de methode `unassignRole` van het object `AuthorizationManagerServiceClient` op en geeft u de volgende waarden door:

   * Een `java.lang.String` -object dat de rol-id bevat.
   * Een array van `java.lang.String` -objecten met de belangrijkste id&#39;s.

**zie ook**

[Overzicht van de stappen](users.md#summary-of-steps)

[Snel starten (SOAP modus): Rollen en machtigingen beheren met de Java API](/help/forms/developing/user-manager-java-api-quick.md#quick-start-soap-mode-managing-roles-and-permissions-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Rollen en machtigingen beheren met de webservice-API {#managing-roles-and-permissions-using-the-web-service-api}

Rollen en machtigingen beheren met behulp van de API (webservice) voor machtigingsbeheer:

1. Inclusief projectbestanden.

   Creeer een Microsoft .NET project dat MTOM gebruikt. Gebruik de volgende WSDL-definitie: `http://localhost:8080/soap/services/AuthorizationManagerService?WSDL&lc_version=9.0.1` .

   >[!NOTE]
   >
   >Vervang `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een AuthorizationManagerService-client.

   * Maak een `AuthorizationManagerServiceClient` -object met de standaardconstructor.
   * Maak een `AuthorizationManagerServiceClient.Endpoint.Address` -object met de `System.ServiceModel.EndpointAddress` -constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/AuthorizationManagerService?blob=mtom` .) U hoeft het attribuut `lc_version` niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.
   * Maak een `System.ServiceModel.BasicHttpBinding` -object door de waarde van het `AuthorizationManagerServiceClient.Endpoint.Binding` -veld op te halen. De geretourneerde waarde wordt gecast naar `BasicHttpBinding` .
   * Stel het veld `MessageEncoding` van het `System.ServiceModel.BasicHttpBinding` -object in op `WSMessageEncoding.Mtom` . Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld `AuthorizationManagerServiceClient.ClientCredentials.UserName.UserName` toe.
      * Wijs de bijbehorende wachtwoordwaarde toe aan het veld `AuthorizationManagerServiceClient.ClientCredentials.UserName.Password` .
      * Wijs de constante waarde `HttpClientCredentialType.Basic` toe aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType` .
      * Wijs de constante waarde `BasicHttpSecurityMode.TransportCredentialOnly` toe aan het veld `BasicHttpBindingSecurity.Security.Mode` .

1. Roep de juiste rol- of machtigingsbewerkingen aan.

   Als u een rol wilt toewijzen aan een principal, roept u de methode `assignRole` van het object `AuthorizationManagerServiceClient` op en geeft u de volgende waarden door:

   * Een `string` -object dat de rol-id bevat
   * Een `MyArrayOf_xsd_string` -object dat de belangrijkste id&#39;s bevat.

   Als u een rol wilt verwijderen uit de principal, roept u de methode `unassignRole` van het object `AuthorizationManagerServiceService` op en geeft u de volgende waarden door:

   * Een `string` -object dat de rol-id bevat.
   * Een array van `string` -objecten met de belangrijkste id&#39;s.

**zie ook**

[Overzicht van de stappen](users.md#summary-of-steps)

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

## Gebruikers verifiëren {#authenticating-users}

In dit onderwerp wordt beschreven hoe u de API (Java) voor verificatiebeheer kunt gebruiken om uw clienttoepassingen in staat te stellen gebruikers programmatisch te verifiëren.

Mogelijk is gebruikersverificatie vereist voor interactie met een ondernemingsdatabase of andere opslagruimten voor bedrijfsgegevens die beveiligde gegevens opslaan.

Neem bijvoorbeeld een scenario waarin een gebruiker een gebruikersnaam en wachtwoord invoert op een webpagina en de waarden verzendt naar een J2EE-toepassingsserver die als host fungeert voor Forms. Een aangepaste Forms-toepassing kan de gebruiker verifiëren met de service Verificatiebeheer.

Als de authentificatie succesvol is, heeft de toepassing toegang tot een beveiligd ondernemingsgegevensbestand. Anders wordt een bericht naar de gebruiker verzonden waarin wordt aangegeven dat de gebruiker geen geautoriseerde gebruiker is.

Het volgende diagram toont de logische stroom van de toepassing.

![ au_au_umauth_process ](assets/au_au_umauth_process.png)

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

**omvat projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u ervoor zorgen dat u de proxybestanden opneemt.

**creeer een cliënt AuthenticationManagerService**

Alvorens u een gebruiker programmatically kunt voor authentiek verklaren, moet u een cliënt tot stand brengen AuthenticationManagerService. Maak een `AuthenticationManagerServiceClient` -object wanneer u de Java API gebruikt.

**Roep de authentificatieverrichting** aan

Zodra u de de dienstcliënt hebt gecreeerd, kunt u de authentificatieverrichting dan aanhalen. Voor deze bewerking is informatie over de gebruiker nodig, zoals de naam en het wachtwoord van de gebruiker. Als de gebruiker niet verifieert, wordt een uitzondering geworpen.

**wint de authentificatiecontext** terug

Nadat u de gebruiker hebt geverifieerd, kunt u een context maken op basis van de geverifieerde gebruiker. Vervolgens kunt u de inhoud gebruiken om een andere AEM Forms-service aan te roepen. U kunt de context bijvoorbeeld gebruiken om een `EncryptionServiceClient` -document te maken en een PDF-document met een wachtwoord te versleutelen. Zorg ervoor dat de gebruiker die is geverifieerd de rol met de naam `Services User` heeft die nodig is om een AEM Forms-service aan te roepen.

**zie ook**

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[API voor gebruikersbeheer - Snel aan de slag](/help/forms/developing/user-manager-java-api-quick.md#user-manager-java-api-quick-start-soap)

[PDF-documenten versleutelen met een wachtwoord](/help/forms/developing/encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-a-password)

### Gebruikers verifiëren met de Java API {#authenticate-a-user-using-the-java-api}

Verifieer een gebruiker gebruikend de Dienst API van de Manager van de Authentificatie (Java):

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-usermanager-client.jar, op in het klassenpad van uw Java-project.

1. Creeer een cliënt AuthenticationManagerServices.

   Maak een `AuthenticationManagerServiceClient` -object door de constructor ervan te gebruiken en een `ServiceClientFactory` -object door te geven dat verbindingseigenschappen bevat.

1. Roep de verificatiebewerking aan.

   Roep de methode `authenticate` van het object `AuthenticationManagerServiceClient` aan en geef de volgende waarden door:

   * Een `java.lang.String` -object dat de gebruikersnaam bevat.
   * Een bytearray (een `byte[]` -object) met het wachtwoord van de gebruiker. U kunt het object `byte[]` verkrijgen door de methode `java.lang.String` object `getBytes` aan te roepen.

   De methode authenticate retourneert een `AuthResult` -object dat informatie bevat over de geverifieerde gebruiker.

1. Haal de verificatiecontext op.

   Roep de methode `getContext` van het object `ServiceClientFactory` aan, die een object `Context` retourneert.

   Roep vervolgens de methode `initPrincipal` van het object `Context` aan en geef de waarde `AuthResult` door.

### Gebruikers verifiëren met de webservice-API {#authenticate-a-user-using-the-web-service-api}

Verifieer een gebruiker gebruikend de Dienst API van de Manager van de Authentificatie (Webdienst):

1. Inclusief projectbestanden.

   * Creeer een Microsoft .NET cliëntassemblage die de Manager WSDL van de Authentificatie verbruikt. (Zie [ het Aanhalen van AEM Forms gebruikend Base64 het coderen ](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding).)
   * Verwijs naar de Microsoft .NET cliëntassemblage. (Zie &quot;Verwijzend de .NET cliëntassemblage&quot;in [ het Aanhalen van AEM Forms gebruikend het Coderen Base64 ](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding).)

1. Maak een AuthenticationManagerService-client.

   Maak een `AuthenticationManagerServiceService` -object met behulp van de constructor van de proxyklasse.

1. Roep de verificatiebewerking aan.

   Roep de methode `authenticate` van het object `AuthenticationManagerServiceClient` aan en geef de volgende waarden door:

   * Een `string` -object dat de naam van de gebruiker bevat
   * Een bytearray (een `byte[]` -object) met het wachtwoord van de gebruiker. U kunt het `byte[]` -object verkrijgen door een `string` -object met het wachtwoord om te zetten in een `byte[]` -array met behulp van de logica in het onderstaande voorbeeld.
   * De geretourneerde waarde is een `AuthResult` -object dat kan worden gebruikt om informatie over de gebruiker op te halen. In het onderstaande voorbeeld wordt de informatie van de gebruiker opgehaald door eerst het veld `authenticatedUser` van het object `AuthResult` te verkrijgen en vervolgens de velden `canonicalName` en `domainName` van het resulterende object `User` .

**zie ook**

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Gebruikers programmatisch synchroniseren {#programmatically-synchronizing-users}

U kunt gebruikers programmatically synchroniseren door de API van het Beheer van de Gebruiker te gebruiken. Wanneer u gebruikers synchroniseert, werkt u AEM Forms bij met gebruikersgegevens in uw gegevensopslagruimte. Stel bijvoorbeeld dat u nieuwe gebruikers toevoegt aan de gegevensopslagruimte van uw gebruiker. Nadat u een synchronisatiebewerking hebt uitgevoerd, worden de nieuwe gebruikers AEM formuliergebruikers. Ook gebruikers die niet meer in je gebruikerslijst staan, worden uit AEM Forms verwijderd.

In het volgende diagram ziet u hoe AEM Forms synchroniseert met een gebruikersinterface.

![ ps_ps_umauth_sync ](assets/ps_ps_umauth_sync.png)

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

**omvat projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u ervoor zorgen dat u de proxybestanden opneemt.

**creeer een UserManagerUtilServiceClientclient**

Voordat u gebruikers programmatisch kunt synchroniseren, moet u een `UserManagerUtilServiceClient` -object maken.

**specificeer het ondernemingsdomein**

Voordat u een synchronisatiebewerking uitvoert met de API voor gebruikersbeheer, geeft u het ondernemingsdomein op waartoe gebruikers behoren. U kunt een of meerdere ondernemingsdomeinen opgeven. Alvorens u een synchronisatieverrichting programmatically kunt uitvoeren, moet u een ondernemingsdomein opstelling gebruikend de Console van het Beleid. (Zie [ beleidshulp ](https://www.adobe.com/go/learn_aemforms_admin_63).)

**haalt de synchronisatieverrichting** aan

Nadat u een of meer ondernemingsdomeinen hebt opgegeven, kunt u de synchronisatiebewerking uitvoeren. De tijd die nodig is om deze bewerking uit te voeren, is afhankelijk van het aantal gebruikersrecords in de gegevensopslagruimte van de gebruiker.

**bepaalt als de synchronisatieverrichting volledig is**

Nadat u programmatically een synchronisatieverrichting uitvoert, kunt u bepalen als de verrichting volledig is.

**zie ook**

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[API voor gebruikersbeheer - Snel aan de slag](/help/forms/developing/user-manager-java-api-quick.md#user-manager-java-api-quick-start-soap)

[PDF-documenten versleutelen met een wachtwoord](/help/forms/developing/encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-a-password)

### Gebruikers programmatisch synchroniseren met de Java API {#programmatically-synchronizing-users-using-the-java-api}

Gebruikers synchroniseren met de API voor gebruikersbeheer (Java):

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-usermanager-client.jar en adobe-usermanager-util-client.jar, op in het klassenpad van uw Java-project.

1. Maak een UserManagerUtilServiceClient-client.

   Maak een `UserManagerUtilServiceClient` -object door de constructor ervan te gebruiken en een `ServiceClientFactory` -object door te geven dat verbindingseigenschappen bevat.

1. Geef het ondernemingsdomein op.

   * Roep de methode `scheduleSynchronization` van het object `UserManagerUtilServiceClient` aan om de gebruikerssynchronisatie te starten.
   * Maak een `java.util.Set` -instantie met een `HashSet` -constructor. Zorg ervoor dat u `String` opgeeft als gegevenstype. Deze `Java.util.Set` -instantie slaat de domeinnamen op waarop de synchronisatiebewerking van toepassing is.
   * Roep voor elke domeinnaam die u wilt toevoegen de methode add van het `java.util.Set` -object aan en geef de domeinnaam door.

1. Roep de synchronisatiebewerking aan.

   Roep de methode `getContext` van het object `ServiceClientFactory` aan, die een object `Context` retourneert.

   Roep vervolgens de methode `initPrincipal` van het object `Context` aan en geef de waarde `AuthResult` door.

**zie ook**

[Gebruikers programmatisch synchroniseren](users.md#programmatically-synchronizing-users)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)
