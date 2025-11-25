---
title: Programmaticaal het leiden Eindpunten
description: Gebruik de dienst van de Registratie van het Eindpunt om EJB eindpunten toe te voegen, het eindpunt van SOAP toe te voegen, gecontroleerde Omslageindpunten toe te voegen, E-maileindpunten toe te voegen, verwijderende eindpunten van de Manager van de Taak toe te voegen, eindpunten te wijzigen, eindpunten te verwijderen en informatie van de eindpuntschakelaar terug te winnen.
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
exl-id: b94dcca2-136b-4b7d-b5ce-544804575876
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,APIs & Integrations
source-git-commit: 07289e891399a78568dcac957bc089cc08c7898c
workflow-type: tm+mt
source-wordcount: '10799'
ht-degree: 0%

---

# Programmaticaal het leiden Eindpunten {#programmatically-managing-endpoints}

**de Steekproeven en de voorbeelden in dit document zijn slechts voor AEM Forms op milieu JEE.**

**Ongeveer de Dienst van de Registratie van het Eindpunt**

De dienst van de Registratie van het Eindpunt verstrekt de capaciteit om eindpunten programmatically te beheren. U kunt, bijvoorbeeld, de volgende types van eindpunten aan de dienst toevoegen:

* EJB
* SOAP
* Gecontroleerde map
* E-mail
* (Verouderd voor AEM-formulieren) Verwijderen
* Taakbeheer

>[!NOTE]
>
>SOAP, EJB en (Verouderd voor AEM-formulieren op JEE) Het verwijderen van eindpunten wordt automatisch gemaakt voor elke geactiveerde service. De eindpunten SOAP en EJB laten SOAP en EJB voor alle de dienstverrichtingen toe.

Een Remoting eindpunt laat de cliënten van Flex toe om verrichtingen op de dienst van AEM Forms aan te halen die het eindpunt aan wordt toegevoegd. Een bestemming van Flex met de zelfde naam zoals het eindpunt wordt gecreeerd en de cliënten van Flex kunnen tot RemoteObjects leiden die aan deze bestemming richten om verrichtingen op de relevante dienst aan te halen.

De e-mail, de Manager van de Taak, en de Gecontroleerde eindpunten van de Omslag stellen slechts een specifieke verrichting van de dienst bloot. Het toevoegen van deze eindpunten vereist een tweede configuratiestap om een methode te selecteren om te roepen, configuratieparameters te plaatsen, en input en outputparameterafbeeldingen te specificeren.

U kunt eindpunten TaskManager in groepen organiseren genoemd *categorieën*. Deze categorieën worden dan blootgesteld aan Workspace door TaskManager, met eind - de gebruikers zien de eindpunten TaskManager aangezien zij worden gecategoriseerd. In Workspace zien eindgebruikers deze categorieën in het navigatievenster. De eindpunten binnen elke categorie worden weergegeven als proceskaarten op de pagina Processen starten in Workspace.

U kunt deze taken verwezenlijken gebruikend de dienst van de Registratie van het Eindpunt:

* EJB-eindpunten toevoegen. (Zie [&#x200B; Toevoegend EJB Eindpunten &#x200B;](programmatically-endpoints.md#adding-ejb-endpoints).)
* SOAP-eindpunten toevoegen. (Zie [&#x200B; Toevoegend SOAP Eindpunten &#x200B;](programmatically-endpoints.md#adding-soap-endpoints).)
* Voeg gecontroleerde eindpunten van de Omslag toe (zie [&#x200B; toevoegend Gecontroleerde Eindpunten van de Omslag &#x200B;](programmatically-endpoints.md#adding-watched-folder-endpoints).)
* E-maileindpunten toevoegen. (Zie [&#x200B; Toevoegend E-maileindpunten &#x200B;](programmatically-endpoints.md#adding-email-endpoints).)
* Voeg eindpunten voor verwijderen toe. (Zie [&#x200B; toevoegend het Verwijderen Eindpunten &#x200B;](programmatically-endpoints.md#adding-remoting-endpoints).)
* Voeg eindpunten TaskManager toe (zie [&#x200B; Toevoegend Eindpunten TaskManager &#x200B;](programmatically-endpoints.md#adding-taskmanager-endpoints).)
* Wijzig eindpunten (zie [&#x200B; Wijzend Eindpunten &#x200B;](programmatically-endpoints.md#modifying-endpoints).)
* Verwijder eindpunten (zie [&#x200B; Verwijderend Eindpunten &#x200B;](programmatically-endpoints.md#removing-endpoints).)
* Haal informatie van de eindpuntschakelaar terug (zie [&#x200B; het Terugwinnen van de Informatie van de Verbinding van Eindpunten &#x200B;](programmatically-endpoints.md#retrieving-endpoint-connector-information).)

## EJB-eindpunten toevoegen {#adding-ejb-endpoints}

U kunt programmatically een eindpunt EJB aan de dienst toevoegen door AEM Forms Java API te gebruiken. Door een eindpunt EJB aan de dienst toe te voegen, laat u een cliënttoepassing toe om de dienst aan te halen door de wijze te gebruiken EJB. Met andere woorden, wanneer u verbindingseigenschappen instelt die nodig zijn om AEM Forms aan te roepen, kunt u de EJB-modus selecteren. (Zie [&#x200B; Plaatsende verbindingseigenschappen &#x200B;](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)

>[!NOTE]
>
>U kunt geen EJB eindpunt toevoegen door de Webdiensten te gebruiken.

>[!NOTE]
>
>Typisch, wordt een eindpunt EJB toegevoegd aan de dienst door gebrek, echter, kan een eindpunt EJB aan een proces worden toegevoegd dat programmatically wordt opgesteld of wanneer een eindpunt EJB werd verwijderd en opnieuw moet worden toegevoegd.

### Overzicht van de stappen {#summary-of-steps}

Om een eindpunt EJB aan de dienst toe te voegen, voer de volgende taken uit:

1. Inclusief projectbestanden.
1. Maak een `EndpointRegistry Client` -object.
1. EJB-eindpuntkenmerken instellen.
1. Maak een EJB-eindpunt.
1. Laat het eindpunt toe.

**omvat projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-utilities.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss Application Server)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss Application Server)

Voor informatie over de plaats van deze JAR dossiers, zie [&#x200B; Inclusief de bibliotheekdossiers van AEM Forms Java &#x200B;](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**creeer een voorwerp van de Cliënt EndpointRegistry**

Voordat u via programmacode een EJB-eindpunt kunt toevoegen, moet u een `EndpointRegistryClient` -object maken.

**plaats EJB eindpuntattributen**

Om een EJB eindpunt voor de dienst tot stand te brengen, specificeer de volgende waarden:

* **herkenningsteken van de Schakelaar**: Specificeert het type van eindpunt om tot stand te brengen. Als u een EJB-eindpunt wilt maken, geeft u `EJB` op.
* **Beschrijving**: Specificeert de eindpuntbeschrijving.
* **Naam**: Specificeert de naam van het eindpunt.
* **herkenningsteken van de Dienst**: Specificeert de dienst waartot het eindpunt behoort.
* **de naam van de Verrichting**: Specificeert de naam van de verrichting die door het eindpunt te gebruiken wordt aangehaald. Geef bij het maken van een EJB-eindpunt een jokerteken op ( `*` ). Als u echter een specifieke bewerking wilt opgeven in plaats van alle servicebewerkingen aan te roepen, geeft u de naam van de bewerking op in plaats van het jokerteken ( `*` ).

**creeer een EJB eindpunt**

Nadat u EJB eindpuntattributen plaatst, kunt u een eindpunt EJB voor de dienst tot stand brengen.

**laat het eindpunt** toe

Nadat u een eindpunt creeert, moet u het toelaten. Nadat u het eindpunt toelaat, kan het worden gebruikt om de dienst aan te halen. Nadat u het eindpunt toelaat, kunt u het binnen beleidsconsole bekijken.

**zie ook**

[Een EJB-eindpunt toevoegen met de Java API](programmatically-endpoints.md#adding-an-ejb-endpoint-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Een EJB-eindpunt toevoegen met de Java API {#adding-an-ejb-endpoint-using-the-java-api}

Voeg een EJB eindpunt toe door Java API te gebruiken:

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-livecycle-client.jar, op in het klassenpad van uw Java-project. (

1. Creeer een voorwerp van de Cliënt EndpointRegistry.

   * Maak een `ServiceClientFactory` -object dat verbindingseigenschappen bevat.
   * Maak een `EndpointRegistryClient` -object door de constructor ervan te gebruiken en het `ServiceClientFactory` -object door te geven.

1. EJB-eindpuntkenmerken instellen.

   * Maak een `CreateEndpointInfo` -object met behulp van de constructor.
   * Geef de waarde van de connector-id op door de methode `CreateEndpointInfo` van het object `setConnectorId` aan te roepen en de tekenreekswaarde door te geven `EJB` .
   * Geef de beschrijving van het eindpunt op door de methode `CreateEndpointInfo` van het object `setDescription` aan te roepen en een tekenreekswaarde door te geven die het eindpunt beschrijft.
   * Geef de naam van het eindpunt op door de methode `CreateEndpointInfo` van het object `setName` aan te roepen en een tekenreekswaarde door te geven die de naam opgeeft.
   * Geef de service op waartoe het eindpunt behoort door de methode `CreateEndpointInfo` van het object `setServiceId` aan te roepen en een tekenreekswaarde door te geven die de servicenaam opgeeft.
   * Geef de bewerking op die wordt aangeroepen door de methode `CreateEndpointInfo` van het object `setOperationName` aan te roepen en geef een tekenreekswaarde door die de naam van de bewerking opgeeft. Voor SOAP- en EJB-eindpunten geeft u een jokerteken ( `*` ) op. Dit houdt in dat alle bewerkingen worden uitgevoerd.

1. Maak een EJB-eindpunt.

   Maak het eindpunt door de methode `EndpointRegistryClient` van het object `createEndpoint` aan te roepen en het object `CreateEndpointInfo` door te geven. Deze methode retourneert een `Endpoint` -object dat het nieuwe EJB-eindpunt vertegenwoordigt.

1. Laat het eindpunt toe.

   Schakel het eindpunt in door de methode enable van het object `EndpointRegistryClient` aan te roepen en het object `Endpoint` door te geven dat door de methode `createEndpoint` is geretourneerd.

**zie ook**

[Overzicht van de stappen](programmatically-endpoints.md#summary-of-steps)

[QuickStart: een EJB-eindpunt toevoegen met de Java API](/help/forms/developing/endpoint-registry-java-api-quick.md#quickstart-adding-an-ejb-endpoint-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## SOAP-eindpunten toevoegen {#adding-soap-endpoints}

U kunt programmatically een eindpunt van SOAP aan de dienst toevoegen door AEM Forms Java API te gebruiken. Door een eindpunt van SOAP toe te voegen, laat u een cliënttoepassing toe om de dienst aan te halen door de wijze van SOAP te gebruiken. Met andere woorden, wanneer u verbindingseigenschappen instelt die nodig zijn om AEM Forms aan te roepen, kunt u de SOAP-modus selecteren.

>[!NOTE]
>
>U kunt geen eindpunt van SOAP toevoegen door de Webdiensten te gebruiken.

>[!NOTE]
>
>Typisch, wordt een eindpunt van SOAP toegevoegd aan de dienst door gebrek, Nochtans, kan een eindpunt van SOAP aan een proces worden toegevoegd dat programmatically wordt opgesteld of wanneer een eindpunt van SOAP werd verwijderd en opnieuw moet worden toegevoegd.

### Overzicht van de stappen {#summary_of_steps-1}

Om een eindpunt van SOAP aan de dienst toe te voegen, voer de volgende taken uit:

1. Inclusief projectbestanden.
1. Maak een `EndpointRegistryClient` -object.
1. Eindpuntkenmerken van SOAP instellen.
1. Maak een SOAP-eindpunt.
1. Laat het eindpunt toe.

**omvat projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u de proxybestanden opnemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-utilities.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss Application Server)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss Application Server)

Deze JAR-bestanden zijn vereist om een SOAP-eindpunt te maken. U hebt echter wel JAR-bestanden nodig als u het SOAP-eindpunt gebruikt om de service aan te roepen. Voor informatie over de dossiers van AEM Forms JAR, zie [&#x200B; Inclusief de bibliotheekdossiers van AEM Forms Java &#x200B;](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**creeer een voorwerp van de Cliënt EndpointRegistry**

Als u programmatisch een SOAP-eindpunt aan een service wilt toevoegen, moet u een `EndpointRegistryClient` -object maken.

**plaats SOAP eindpuntattributen**

Om een eindpunt van SOAP aan de dienst toe te voegen, specificeer de volgende waarden:

* **waarde van het herkenningsteken van de Schakelaar**: Specificeert het type van eindpunt om tot stand te brengen. Als u een SOAP-eindpunt wilt maken, geeft u `SOAP` op.
* **Beschrijving**: Specificeert de eindpuntbeschrijving.
* **Naam**: Specificeert de eindpuntnaam.
* **het herkenningsteken van de Dienst**: Specificeert de dienst waartot het eindpunt behoort.
* **de naam van de Verrichting**: Specificeert de naam van de verrichting die door het eindpunt te gebruiken wordt aangehaald. Geef bij het maken van een SOAP-eindpunt een jokerteken op ( `*` ). Als u echter een specifieke bewerking wilt opgeven in plaats van alle servicebewerkingen aan te roepen, geeft u de naam van de bewerking op in plaats van het jokerteken ( `*` ).

**creeer een eindpunt van SOAP**

Nadat u de eindpuntattributen van SOAP plaatst, kunt u een eindpunt van SOAP tot stand brengen.

**laat het eindpunt** toe

Nadat u een eindpunt creeert, moet u het toelaten. Wanneer het eindpunt wordt toegelaten, kan het worden gebruikt om de dienst aan te halen. Nadat u het eindpunt toelaat, kunt u het binnen beleidsconsole bekijken.

**zie ook**

[Een SOAP-eindpunt toevoegen met de Java API](programmatically-endpoints.md#add-a-soap-endpoint-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Een SOAP-eindpunt toevoegen met de Java API {#add-a-soap-endpoint-using-the-java-api}

Voeg een eindpunt van SOAP aan de dienst toe door Java API te gebruiken:

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-livecycle-client.jar, op in het klassenpad van uw Java-project.

1. Creeer een voorwerp van de Cliënt EndpointRegistry.

   * Maak een `ServiceClientFactory` -object dat verbindingseigenschappen bevat.
   * Maak een `EndpointRegistryClient` -object door de constructor ervan te gebruiken en het `ServiceClientFactory` -object door te geven.

1. Eindpuntkenmerken van SOAP instellen.

   * Maak een `CreateEndpointInfo` -object met behulp van de constructor.
   * Geef de waarde van de connector-id op door de methode `CreateEndpointInfo` van het object `setConnectorId` aan te roepen en de tekenreekswaarde door te geven `SOAP` .
   * Geef de beschrijving van het eindpunt op door de methode `CreateEndpointInfo` van het object `setDescription` aan te roepen en een tekenreekswaarde door te geven die het eindpunt beschrijft.
   * Geef de naam van het eindpunt op door de methode `CreateEndpointInfo` van het object `setName` aan te roepen en een tekenreekswaarde door te geven die de naam opgeeft.
   * Geef de service op waartoe het eindpunt behoort door de methode `CreateEndpointInfo` van het object `setServiceId` aan te roepen en een tekenreekswaarde door te geven die de servicenaam opgeeft.
   * Geef de bewerking op die wordt aangeroepen door de methode `CreateEndpointInfo` van het object `setOperationName` aan te roepen en een tekenreekswaarde door te geven die de naam van de bewerking aangeeft. Voor SOAP- en EJB-eindpunten geeft u een jokerteken ( `*` ) op. Dit houdt in dat alle bewerkingen worden uitgevoerd.

1. Maak een SOAP-eindpunt.

   Maak het eindpunt door de methode `EndpointRegistryClient` van het object `createEndpoint` aan te roepen en het object `CreateEndpointInfo` door te geven. Deze methode retourneert een `Endpoint` -object dat het nieuwe SOAP-eindpunt vertegenwoordigt.

1. Laat het eindpunt toe.

   Schakel het eindpunt in door de methode enable van het object `EndpointRegistryClient` aan te roepen en geef het object `Endpoint` door dat door de methode `createEndpoint` is geretourneerd.

**zie ook**

[Overzicht van de stappen](programmatically-endpoints.md#summary-of-steps)

[QuickStart: een SOAP-eindpunt toevoegen met de Java API](/help/forms/developing/endpoint-registry-java-api-quick.md#quickstart-adding-a-soap-endpoint-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Eindpunten van gecontroleerde mappen toevoegen {#adding-watched-folder-endpoints}

U kunt programmatically een Gecontroleerd eindpunt van de Omslag aan de dienst toevoegen door AEM Forms Java API te gebruiken. Als u een eindpunt van een gecontroleerde map toevoegt, kunnen gebruikers een bestand (zoals een PDF-bestand) in een map plaatsen. Wanneer het dossier in de omslag wordt geplaatst, wordt de gevormde dienst dan aangehaald en manipuleert het dossier. Nadat de service de opgegeven bewerking heeft uitgevoerd, wordt het gewijzigde bestand opgeslagen in een opgegeven uitvoermap. Een gecontroleerde map is geconfigureerd om te worden gescand met een vast interval of met een uitsnijdschema, zoals elke maandag, woensdag en vrijdag om 12.00 uur.

Voor de doeleinden van programmatically het toevoegen van een Gecontroleerd eindpunt van de Omslag aan de dienst, overweeg het volgende kortstondig proces genoemd *EncryptDocument*. (Zie [&#x200B; Begrijpend de Processen van AEM Forms &#x200B;](/help/forms/developing/aem-forms-processes.md#understanding-aem-forms-processes).)

![&#x200B; aw_aw_encryptdocumentprocess &#x200B;](assets/aw_aw_encryptdocumentprocess.png)

Dit proces accepteert een onbeveiligd PDF-document als een invoerwaarde en geeft het onbeveiligde PDF-document vervolgens door aan de `EncryptPDFUsingPassword` -bewerking van de Encryption-service. Het PDF-document wordt versleuteld met een wachtwoord en het met een wachtwoord gecodeerde PDF-document is de uitvoerwaarde van dit proces. De naam van de invoerwaarde (het onbeveiligde PDF-document) is `InDoc` en het gegevenstype is `com.adobe.idp.Document` . De naam van de uitvoerwaarde (het met wachtwoord gecodeerde PDF-document) is `SecuredDoc` en het gegevenstype is `com.adobe.idp.Document` .

>[!NOTE]
>
>U kunt geen Gecontroleerd eindpunt van de Omslag toevoegen door de Webdiensten te gebruiken.

### Overzicht van de stappen {#summary_of_steps-2}

Voer de volgende taken uit om een eindpunt van een gecontroleerde map aan de service toe te voegen:

1. Inclusief projectbestanden.
1. Maak een `EndpointRegistryClient` -object.
1. Attributen voor het eindpunt van gecontroleerde map instellen.
1. Geef configuratiewaarden op.
1. Definieer invoerparameterwaarden.
1. Definieer een uitvoerparameterwaarde.
1. Maak een eindpunt van een gecontroleerde map.
1. Laat het eindpunt toe.

**omvat projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u de proxybestanden opnemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-utilities.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss Application Server)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss Application Server)

Voor informatie over de plaats van deze JAR dossiers, zie [&#x200B; Inclusief de bibliotheekdossiers van AEM Forms Java &#x200B;](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**creeer een voorwerp van de Cliënt EndpointRegistry**

Als u programmatisch een eindpunt van een gecontroleerde map wilt toevoegen, moet u een `EndpointRegistryClient` -object maken.

**plaats de Gecontroleerde attributen van het Omslageindpunt**

Om een Gecontroleerd eindpunt van de Omslag voor de dienst tot stand te brengen, specificeer de volgende waarden:

* **herkenningsteken van de Schakelaar**: Specificeert het type van eindpunt dat wordt gecreeerd. Geef `WatchedFolder` op als u een eindpunt van een gecontroleerde map wilt maken.
* **Beschrijving**: Specificeert de beschrijving van het eindpunt.
* **Naam**: Specificeert de naam van het eindpunt.
* **herkenningsteken van de Dienst**: Specificeert de dienst waartot het eindpunt behoort. Als u bijvoorbeeld een eindpunt van een gecontroleerde map wilt toevoegen aan het proces dat in deze sectie wordt geïntroduceerd (een proces wordt een service wanneer het wordt geactiveerd met Workbench), geeft u `EncryptDocument` op.
* **de naam van de Verrichting**: Specificeert de naam van de verrichting die door het eindpunt te gebruiken wordt aangehaald. Typisch, wanneer het creëren van een Gecontroleerd eindpunt van de Omslag voor de dienst die uit een proces voortkwam dat in Workbench wordt gecreeerd, is de naam van de verrichting `invoke`.

**specificeer configuratiewaarden**

Specificeer configuratiewaarden voor een Gecontroleerd eindpunt van de Omslag wanneer programmatically het toevoegen van een Gecontroleerd eindpunt van de Omslag aan de dienst. Deze configuratiewaarden worden gespecificeerd door een beheerder als een Gecontroleerd eindpunt van de Omslag door beleidsconsole wordt toegevoegd te gebruiken.

De volgende lijst specificeert configuratiewaarden die wanneer programmatically het toevoegen van een Gecontroleerd eindpunt van de Omslag aan de dienst worden geplaatst:

* **url**: Specificeert de gecontroleerde omslagplaats. In een gegroepeerd milieu, moet deze waarde aan een gedeelde netwerkomslag richten die van elke computer in de cluster toegankelijk is.
* **asynchroon**: Identificeert het aanroepingstype als asynchroon of synchroon. De voorbijgaande en synchrone processen kunnen slechts synchroon worden aangehaald. De standaardwaarde is true. Asynchroon wordt aanbevolen.
* **cronExpression**: Gebruikt door kwarts om de opiniepeiling van de inputfolder te plannen.
* **purgeDuration**: Dit is een verplicht attribuut. Bestanden en mappen in de resultaatmap worden gewist wanneer ze ouder zijn dan deze waarde. Deze waarde wordt gemeten in dagen. Dit kenmerk is handig om ervoor te zorgen dat de resultaatmap niet vol wordt. De waarde -1 dagen geeft aan dat u de resultatenmap nooit wilt verwijderen. De standaardwaarde is -1.
* **repeatInterval**: Het interval, in seconden, voor het aftasten van de Gecontroleerde Omslag voor input. Tenzij de vertraging wordt toegelaten, zou deze waarde langer dan de tijd moeten zijn om een gemiddelde baan te verwerken; anders, kan het systeem overbelast worden. De standaardwaarde is 5.
* **repeatCount**: Het aantal tijden een Gecontroleerde Omslag scant de omslag of de folder. De waarde -1 geeft aan dat een scanbewerking voor onbepaalde tijd wordt uitgevoerd. De standaardwaarde is -1.
* **throttleOn**: Beperkt het aantal Gecontroleerde banen van de Omslag die op een bepaald ogenblik kunnen worden verwerkt. Het maximumaantal banen wordt bepaald door de batchSize waarde.
* **userName**: De gebruikersnaam die wanneer het aanhalen van een doeldienst van de Gecontroleerde Omslag wordt gebruikt. Deze waarde is verplicht. De standaardwaarde is SuperAdmin.
* **domainName**: Het domein van de gebruiker. Deze waarde is verplicht. De standaardwaarde is DefaultDom.
* **batchSize**: Het aantal dossiers of omslagen dat per aftasten moet worden opgenomen. Gebruik deze waarde om overbelasting op het systeem te voorkomen. Als u te veel bestanden tegelijk scant, kan dit tot gevolg hebben dat de toepassing vastloopt. De standaardwaarde is 2.
* **waitTime**: De tijd, in milliseconden, te wachten alvorens een omslag of een dossier na verwezenlijking af te tasten. Als de wachttijd bijvoorbeeld 36.000.000 milliseconden (één uur) is en het bestand een minuut geleden is gemaakt, wordt dit bestand opgepakt nadat 59 minuten zijn verstreken. Dit kenmerk is handig om ervoor te zorgen dat een bestand of map volledig naar de invoermap wordt gekopieerd. Als u bijvoorbeeld een groot bestand hebt dat moet worden verwerkt en het downloaden van het bestand duurt tien minuten, stelt u de wachttijd in op 10&ast;60 &ast;1000 milliseconden. Met deze instelling voorkomt u dat de gecontroleerde map het bestand scant als het nog tien minuten niet heeft gewacht. De standaardwaarde is 0.
* **excludeFilePattern**: Het patroon dat een gecontroleerde omslag gebruikt om te bepalen welke dossiers en omslagen aan aftasten en op te nemen. Bestanden of mappen met dit patroon worden niet gescand voor verwerking. Deze instelling is handig wanneer de invoer een map is die meerdere bestanden bevat. De inhoud van de map kan worden gekopieerd naar een map met een naam die wordt opgepakt door de gecontroleerde map. Met deze stap wordt voorkomen dat de gecontroleerde map een map opneemt die moet worden verwerkt voordat de map volledig is gekopieerd naar de invoermap. Als de waarde excludeFilePattern bijvoorbeeld `data*` is, worden niet alle bestanden en mappen opgehaald die overeenkomen met `data*` . Dit omvat bestanden en mappen met de naam `data1` , `data2` , enzovoort. Bovendien kan het patroon met vervangingspatronen worden aangevuld om dossierpatronen te specificeren. De gecontroleerde map wijzigt de reguliere expressie om jokertekenpatronen zoals `*.*` en `*.pdf` te ondersteunen. Deze jokertekenpatronen worden niet ondersteund door reguliere expressies.
* **includeFilePattern**: Het patroon dat de gecontroleerde omslag gebruikt om te bepalen welke omslagen en dossiers aan aftasten en op te nemen. Als deze waarde bijvoorbeeld `*` is, worden alle bestanden en mappen opgehaald die overeenkomen met `input*` . Dit omvat bestanden en mappen met de naam `input1` , `input2` , enzovoort. De standaardwaarde is `*` . Deze waarde geeft alle bestanden en mappen aan. Bovendien kan het patroon met vervangingspatronen worden aangevuld om dossierpatronen te specificeren. De gecontroleerde map wijzigt de reguliere expressie om jokertekenpatronen zoals `*.*` en `*.pdf` te ondersteunen. Deze jokertekenpatronen worden niet ondersteund door reguliere expressies. Deze waarde is verplicht.
* **resultFolderName**: De omslag waar de bewaarde resultaten worden opgeslagen. Deze locatie kan een absoluut of relatief mappad zijn. Als de resultaten niet in deze map worden weergegeven, controleert u de map met foutmeldingen. Alleen-lezen bestanden worden niet verwerkt en worden opgeslagen in de map met foutmeldingen. De standaardwaarde is `result/%Y/%M/%D/` . Dit is de resultatenmap in de controlemap.
* **preserveFolderName**: De plaats waar de dossiers na succesvol aftasten en oppikken worden opgeslagen. Deze locatie kan een absoluut, relatief of null-mappad zijn. De standaardwaarde is `preserve/%Y/%M/%D/` .
* **failureFolderName**: De omslag waar de mislukkingsdossiers worden bewaard. Deze locatie is altijd relatief ten opzichte van de gecontroleerde map. Alleen-lezen bestanden worden niet verwerkt en worden opgeslagen in de map met foutmeldingen. De standaardwaarde is `failure/%Y/%M/%D/` .
* **preserveOnFailed**: Behoud inputdossiers als er een mislukking is om de verrichting op de dienst in werking te stellen. De standaardwaarde is true.
* **overwriteDuplicateFilename**: Wanneer reeks aan waar, worden de dossiers in de resultatenomslag en bewaren omslag beschreven. Als deze optie is ingesteld op false, worden bestanden en mappen met een numeriek indexachtervoegsel gebruikt voor de naam. De standaardwaarde is false.

**bepalen de waarden van de inputparameter**

Wanneer u een eindpunt van een gecontroleerde map maakt, moet u parameterwaarden voor invoer definiëren. Dat wil zeggen dat u de invoerwaarden moet beschrijven die worden doorgegeven aan de bewerking die wordt aangeroepen door de gecontroleerde map. Neem bijvoorbeeld het proces dat in dit onderwerp is geïntroduceerd. Het heeft één invoerwaarde genoemd `InDoc` en zijn gegevenstype is `com.adobe.idp.Document`. Wanneer u een eindpunt van een gecontroleerde map voor dit proces maakt (nadat een proces is geactiveerd, wordt het een service), moet u de waarde van de invoerparameter definiëren.

Als u parameterwaarden voor invoer wilt definiëren die vereist zijn voor het eindpunt van een gecontroleerde map, geeft u de volgende waarden op:

**de parameternaam van de Input**: De naam van de inputparameter. De naam van een inputwaarde wordt gespecificeerd in Workbench voor een proces. Als de inputwaarde tot een de dienstverrichting (de dienst behoort die geen proces is dat in Workbench wordt gecreeerd), wordt de inputnaam gespecificeerd in het component.xml- dossier. De naam van de invoerparameter voor het in deze sectie geïntroduceerde proces is bijvoorbeeld `InDoc` .

**Type van Toewijzing**: Gebruikt om de inputwaarden te vormen die worden vereist om de de dienstverrichting aan te halen. Er zijn twee typen toewijzingen:

* `Literal`: Het eindpunt van de gecontroleerde map gebruikt de waarde die in het veld wordt ingevoerd terwijl deze wordt weergegeven. Alle basistypen van Java worden ondersteund. Als een API bijvoorbeeld invoer gebruikt zoals String, long, int en Boolean, wordt de tekenreeks omgezet in het juiste type en wordt de service aangeroepen.
* `Variable`: De ingevoerde waarde is een bestandspatroon waarmee de gecontroleerde map de invoer kan selecteren. Als u bijvoorbeeld Variabele selecteert voor het toewijzingstype en het invoerdocument een PDF-bestand moet zijn, kunt u `*.pdf` opgeven als toewijzingswaarde.

**Waarde van de Toewijzing**: Specificeert de waarde van het toewijzingstype. Als u bijvoorbeeld een toewijzingstype `Variable` selecteert, kunt u `*.pdf` opgeven als bestandspatroon.

**Type van Gegevens**: Specificeert het gegevenstype van de inputwaarde(s). Het gegevenstype van de invoerwaarde van het proces dat in deze sectie wordt geïntroduceerd, is bijvoorbeeld `com.adobe.idp.Document` .

**bepaal een waarde van de outputparameter**

Wanneer u een eindpunt van een gecontroleerde map maakt, moet u een uitvoerparameterwaarde definiëren. Namelijk moet u de outputwaarde beschrijven die door de dienst is teruggekeerd die door het Gecontroleerde eindpunt van de Omslag wordt aangehaald. Neem bijvoorbeeld het proces dat in dit onderwerp is geïntroduceerd. Het heeft een outputwaarde genoemd `SecuredDoc` en zijn gegevenstype is `com.adobe.idp.Document`. Wanneer het creëren van een Gecontroleerd eindpunt van de Omslag voor dit proces (nadat een proces wordt geactiveerd, wordt het een dienst), moet u de waarde van de outputparameter bepalen.

Geef de volgende waarden op om een uitvoerparameterwaarde te definiëren die voor het eindpunt van een gecontroleerde map is vereist:

**de parameternaam van de Output**: De naam van de outputparameter. De naam van een waarde voor de procesuitvoer wordt opgegeven in Workbench. Als de outputwaarde tot een de dienstverrichting (de dienst behoort die geen proces is dat in Workbench wordt gecreeerd), wordt de outputnaam gespecificeerd in het component.xml- dossier. De naam van de uitvoerparameter voor het proces dat in deze sectie wordt geïntroduceerd, is bijvoorbeeld `SecuredDoc` .

**Type van Toewijzing**: Gebruikt om de output van de dienst en de verrichting te vormen. De volgende opties zijn beschikbaar:

* Als de service één object (één document) retourneert, is het patroon `%F.pdf` en is de bronbestemming sourcefilename.pdf. Het in deze sectie geïntroduceerde proces retourneert bijvoorbeeld één document. Het toewijzingstype kan daarom worden gedefinieerd als `%F.pdf` ( `%F` betekent dat de opgegeven bestandsnaam wordt gebruikt). Met het patroon `%E` geeft u de extensie van het invoerdocument op.
* Als de service een lijst retourneert, is het patroon `Result\%F\` en is de bronbestemming Result\sourcefilename\source1 (uitvoer 1) en Result\sourceName\source2 (uitvoer 2).
* Als de service een kaart retourneert, is het patroon `Result\%F\` en is de bronbestemming Result\sourcefilename\file1 en Result\sourcefilename\file2. Als de kaart meerdere objecten bevat, is het patroon `Result\%F.pdf` en is de bronbestemming Result\sourcefilename1.pdf (uitvoer 1), Result\sourcefilenam2.pdf (uitvoer 2), enzovoort.

**Type van Gegevens**: Specificeert het gegevenstype van de terugkeerwaarde. Het gegevenstype van de geretourneerde waarde van het proces dat in deze sectie wordt geïntroduceerd, is bijvoorbeeld `com.adobe.idp.Document` .

**creeer een Gecontroleerd eindpunt van de Omslag**

Nadat u de attributen, de configuratiewaarden van het eindpunt plaatst, en input en outputparameterwaarden bepaalt, moet u het Gecontroleerde eindpunt van de Omslag tot stand brengen.

**laat het eindpunt** toe

Nadat u een Gecontroleerd eindpunt van de Omslag creeert, moet u het toelaten. Wanneer het eindpunt wordt toegelaten, kan het worden gebruikt om de dienst aan te halen. Nadat u het eindpunt toelaat, kunt u het binnen beleidsconsole bekijken.

**zie ook**

[Het eindpunt van een gecontroleerde map toevoegen met de Java API](programmatically-endpoints.md#add-a-watched-folder-endpoint-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Het eindpunt van een gecontroleerde map toevoegen met de Java API {#add-a-watched-folder-endpoint-using-the-java-api}

Voeg een Gecontroleerd eindpunt van de Omslag toe door AEM Forms Java API te gebruiken:

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-livecycle-client.jar, op in het klassenpad van uw Java-project.

1. Creeer een voorwerp van de Cliënt EndpointRegistry.

   * Maak een `ServiceClientFactory` -object dat verbindingseigenschappen bevat.
   * Maak een `EndpointRegistryClient` -object door de constructor ervan te gebruiken en het `ServiceClientFactory` -object door te geven.

1. Attributen voor het eindpunt van gecontroleerde map instellen.

   * Maak een `CreateEndpointInfo` -object met behulp van de constructor.
   * Geef de waarde van de connector-id op door de methode `CreateEndpointInfo` van het object `setConnectorId` aan te roepen en de tekenreekswaarde door te geven `WatchedFolder` .
   * Geef de beschrijving van het eindpunt op door de methode `CreateEndpointInfo` van het object `setDescription` aan te roepen en een tekenreekswaarde door te geven die het eindpunt beschrijft.
   * Geef de naam van het eindpunt op door de methode `CreateEndpointInfo` van het object `setName` aan te roepen en een tekenreekswaarde door te geven die de naam opgeeft.
   * Geef de service op waartoe het eindpunt behoort door de methode `CreateEndpointInfo` van het object `setServiceId` aan te roepen en een tekenreekswaarde door te geven die de servicenaam opgeeft.
   * Geef de bewerking op die wordt aangeroepen door de methode `CreateEndpointInfo` van het object `setOperationName` aan te roepen en een tekenreekswaarde door te geven die de naam van de bewerking aangeeft. Typisch, wanneer het creëren van een Gecontroleerd eindpunt van de Omslag voor de dienst die uit een proces voortkwam dat in Workbench wordt gecreeerd, wordt de naam van de verrichting aangeroepen.

1. Geef configuratiewaarden op.

   Voor elke configuratiewaarde die moet worden ingesteld voor het eindpunt van de gecontroleerde map, moet u de methode `CreateEndpointInfo` van het object `setConfigParameterAsText` aanroepen. Als u bijvoorbeeld de configuratiewaarde `url` wilt instellen, roept u de methode `CreateEndpointInfo` object `setConfigParameterAsText` aan en geeft u de volgende tekenreekswaarden door:

   * Een tekenreekswaarde die de naam van de configuratiewaarde opgeeft. Geef `url` op wanneer u de configuratiewaarde van `url` instelt.
   * Een tekenreeks die de waarde van de configuratiewaarde opgeeft. Geef bij het instellen van de configuratiewaarde van `url` de locatie van de gecontroleerde map op.

   >[!NOTE]
   >
   >Om alle configuratiewaarden te zien die voor de dienst EncryptDocument worden geplaatst, zie het de codevoorbeeld van Java dat bij [&#x200B; wordt gevestigd QuickStart: het toevoegen van een Gecontroleerd eindpunt van de Omslag gebruikend Java API &#x200B;](/help/forms/developing/endpoint-registry-java-api-quick.md#quickstart-adding-a-watched-folder-endpoint-using-the-java-api).

1. Definieer invoerparameterwaarden.

   Definieer een invoerparameterwaarde door de methode `CreateEndpointInfo` van het object `setInputParameterMapping` aan te roepen en de volgende waarden door te geven:

   * Een tekenreekswaarde die de naam van de invoerparameter opgeeft. De naam van de invoerparameter voor de EncryptDocument-service is bijvoorbeeld `InDoc` .
   * Een tekenreeks die het gegevenstype van de invoerparameter opgeeft. Het gegevenstype van de invoerparameter `InDoc` is bijvoorbeeld `com.adobe.idp.Document` .
   * Een tekenreekswaarde die het toewijzingstype aangeeft. U kunt bijvoorbeeld `variable` opgeven.
   * Een tekenreekswaarde die de toewijzingswaarde opgeeft. U kunt bijvoorbeeld &ast;.pdf opgeven als bestandspatroon.

   >[!NOTE]
   >
   >Roep de methode `setInputParameterMapping` aan voor elke invoerparameterwaarde die moet worden gedefinieerd. Omdat het EncryptDocument-proces slechts één invoerparameter heeft, moet u deze methode eenmaal aanroepen.

1. Definieer een uitvoerparameterwaarde.

   Definieer een uitvoerparameterwaarde door de methode `CreateEndpointInfo` van het object `setOutputParameterMapping` aan te roepen en de volgende waarden door te geven:

   * Een tekenreekswaarde die de naam van de uitvoerparameter opgeeft. De naam van de uitvoerparameter voor de EncryptDocument-service is bijvoorbeeld `SecuredDoc` .
   * Een tekenreeks die het gegevenstype van de uitvoerparameter opgeeft. Het gegevenstype van de uitvoerparameter `SecuredDoc` is bijvoorbeeld `com.adobe.idp.Document` .
   * Een tekenreekswaarde die het toewijzingstype aangeeft. U kunt bijvoorbeeld `%F.pdf` opgeven.

1. Maak een eindpunt van een gecontroleerde map.

   Maak het eindpunt door de methode `EndpointRegistryClient` van het object `createEndpoint` aan te roepen en het object `CreateEndpointInfo` door te geven. Deze methode retourneert een `Endpoint` -object dat het eindpunt van de gecontroleerde map vertegenwoordigt.

1. Laat het eindpunt toe.

   Schakel het eindpunt in door de methode `EndpointRegistryClient` van het object `enable` aan te roepen en het object `Endpoint` door te geven dat door de methode `createEndpoint` is geretourneerd.

**zie ook**

[Overzicht van de stappen](programmatically-endpoints.md#summary-of-steps)

[QuickStart: een eindpunt voor een gecontroleerde map toevoegen met de Java API](/help/forms/developing/endpoint-registry-java-api-quick.md#quickstart-adding-a-watched-folder-endpoint-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Configuratiewaarden van gecontroleerde map, constant bestand {#watched-folder-configuration-values-constant-file}

[&#x200B; QuickStart: Het toevoegen van een Gecontroleerd eindpunt van de Omslag gebruikend Java API &#x200B;](/help/forms/developing/endpoint-registry-java-api-quick.md#quickstart-adding-a-watched-folder-endpoint-using-the-java-api) gebruikt een constant dossier dat deel van uw project van Java moet uitmaken om het snelle begin te compileren. Dit constante dossier vertegenwoordigt configuratiewaarden die moeten worden geplaatst wanneer het toevoegen van een Gecontroleerd eindpunt van de Omslag. De volgende Java-code vertegenwoordigt het constante bestand.

```java
 /**
     * This class contains constants that can be used when setting Watched Folder
     * configuration values
     */

 public final class WatchedFolderEndpointConfigConstants {

         public static final String PROPERTY_FILEPROVIDER_URL = "url";
         public static final String PROPERTY_PROPERTY_ASYNCHRONOUS = "asynchronous";
         public static final String PROPERTY_CRON_EXPRESSION = "cronExpression";
         public static final String PROPERTY_PURGE_DURATION = "purgeDuration";
         public static final String PROPERTY_REPEAT_INTERVAL = "repeatInterval";
         public static final String PROPERTY_REPEAT_COUNT = "repeatCount";
         public static final String PROPERTY_THROTTLE = "throttleOn";
         public static final String PROPERTY_USERNAMER = "userName";
         public static final String PROPERTY_DOMAINNAME = "domainName";
         public static final String PROPERTY_FILEPROVIDER_BATCH_SIZE = "batchSize";
         public static final String PROPERTY_FILEPROVIDER_WAIT_TIME = "waitTime";
         public static final String PROPERTY_EXCLUDE_FILE_PATTERN = "excludeFilePattern";
         public static final String PROPERTY_INCLUDE_FILE_PATTERN = "excludeFilePattern";
         public static final String PROPERTY_FILEPROVIDER_RESULT_FOLDER_NAME =  "resultFolderName";
         public static final String PROPERTY_FILEPROVIDER_PRESERVE_FOLDER_NAME = "preserveFolderName";
         public static final String PROPERTY_FILEPROVIDER_FAILURE_FOLDER_NAME = "failureFolderName";
         public static final String PROPERTY_FILEPROVIDER_PRESERVE_ON_FAILURE = "preserveOnFailure";
         public static final String PROPERTY_FILEPROVIDER_OVERWRITE_DUPLICATE_FILENAME = "overwriteDuplicateFilename";
        }
```

## E-maileindpunten toevoegen {#adding-email-endpoints}

U kunt programmatically een eindpunt E-mail aan de dienst toevoegen door AEM Forms Java API te gebruiken. Door een e-maileindpunt toe te voegen, laat u gebruikers toe om een e-mailbericht met één of meerdere dossiergehechtheid naar een gespecificeerde e-mailrekening te verzenden. Dan vormen de de dienstverrichting wordt aangehaald en manipuleert de dossiers. Nadat de service de opgegeven bewerking heeft uitgevoerd, stuurt het een e-mailbericht naar de afzender met de gewijzigde bestanden als bestandsbijlagen.

Voor het programmatically toevoegen van een E-mail eindpunt aan de dienst, overweeg het volgende kortstondig proces genoemd *MyApplication \ EncryptDocument*. Voor informatie over kortstondige processen, zie [&#x200B; Begrijpend de Processen van AEM Forms &#x200B;](/help/forms/developing/aem-forms-processes.md#understanding-aem-forms-processes).

![&#x200B; ae_ae_encryptdocumentprocess &#x200B;](assets/ae_ae_encryptdocumentprocess.png)

Dit proces accepteert een onbeveiligd PDF-document als een invoerwaarde en geeft het onbeveiligde PDF-document vervolgens door aan de `EncryptPDFUsingPassword` -bewerking van de Encryption-service. Dit proces codeert het PDF-document met een wachtwoord en retourneert het met een wachtwoord gecodeerde PDF-document als de uitvoerwaarde. De naam van de invoerwaarde (het onbeveiligde PDF-document) is `InDoc` en het gegevenstype is `com.adobe.idp.Document` . De naam van de uitvoerwaarde (het met wachtwoord gecodeerde PDF-document) is `SecuredDoc` en het gegevenstype is `com.adobe.idp.Document` .

>[!NOTE]
>
>U kunt geen eindpunt E-mail toevoegen door de Webdiensten te gebruiken.

### Overzicht van de stappen {#summary_of_steps-3}

Om een E-maileindpunt aan de dienst toe te voegen, voer de volgende taken uit:

1. Inclusief projectbestanden.
1. Maak een `EndpointRegistryClient` -object.
1. Emaileindpuntkenmerken instellen.
1. Geef configuratiewaarden op.
1. Definieer invoerparameterwaarden.
1. Definieer een uitvoerparameterwaarde.
1. Maak het eindpunt E-mail.
1. Laat het eindpunt toe.

**omvat projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u de proxybestanden opnemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-utilities.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss Application Server)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss Application Server)

Voor informatie over de plaats van deze JAR dossiers, zie [&#x200B; Inclusief de bibliotheekdossiers van AEM Forms Java &#x200B;](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**creeer een voorwerp van de Cliënt EndpointRegistry**

Voordat u een e-maileindpunt kunt toevoegen, moet u een `EndpointRegistryClient` -object maken.

**vastgestelde E-mail eindpuntattributen**

Om een E-maileindpunt voor de dienst tot stand te brengen, specificeer de volgende waarden:

* **waarde van het herkenningsteken van de Schakelaar**: Specificeert het type van eindpunt dat wordt gecreeerd. Geef `Email` op om een e-maileindpunt te maken.
* **Beschrijving**: Specificeert een beschrijving voor het eindpunt.
* **Naam**: Specificeert de naam van het eindpunt.
* **het herkenningsteken van de Dienst**: Specificeert de dienst waartot het eindpunt behoort. Als u bijvoorbeeld een e-maileindpunt wilt toevoegen aan het proces dat in deze sectie wordt geïntroduceerd (een proces wordt een service wanneer het wordt geactiveerd met Workbench), geeft u `EncryptDocument` op.
* **de naam van de Verrichting**: Specificeert de naam van de verrichting die door het eindpunt te gebruiken wordt aangehaald. Typisch, wanneer het creëren van een E-mail eindpunt voor de dienst die van een proces voortkwam dat in Workbench wordt gecreeerd, is de naam van de verrichting `invoke`.

**specificeer configuratiewaarden**

Specificeer configuratiewaarden voor een E-mail eindpunt wanneer programmatically het toevoegen van een E-mail eindpunt aan de dienst. Deze configuratiewaarden worden gespecificeerd door een beheerder als een E-maileindpunt gebruikend beleidsconsole wordt toegevoegd.

>[!NOTE]
>
>De e-mailrekening die wordt gecontroleerd is een speciale rekening die voor het E-maileindpunt slechts wordt gebruikt. Dit account is geen gewoon e-mailaccount voor gebruikers. Een e-mailaccount van een normale gebruiker mag niet worden geconfigureerd als de account die de e-mailprovider gebruikt, omdat de e-mailprovider e-mailberichten verwijdert uit het Postvak IN nadat deze zijn voltooid met de berichten.

De volgende configuratiewaarden worden geplaatst wanneer programmatically het toevoegen van een E-maileindpunt aan de dienst:

* **cronExpression**: Een uitsnijduitdrukking als e-mail door een uitsnijduitdrukking te gebruiken moet worden gepland.
* **repeatCount**: Aantal tijden het e-maileindpunt scant de omslag of de folder. De waarde -1 geeft aan dat een scanbewerking voor onbepaalde tijd wordt uitgevoerd. De standaardwaarde is -1.
* **repeatInterval**: Het aftastentarief in seconden dat de ontvanger voor het controleren van inkomende post gebruikt. De standaardwaarde is 10.
* **startDelay**: De tijd te wachten om na het plannerbegin af te tasten. De standaardtijd is 0.
* **batchSize**: Het aantal e-mailberichten de ontvanger verwerkt per aftasten voor optimale prestaties. De waarde -1 geeft alle e-mails aan. De standaardwaarde is 2.
* **userName**: De gebruikersnaam die wanneer het aanhalen van een doeldienst van e-mail wordt gebruikt. De standaardwaarde is `SuperAdmin` .
* **domainName**: Een verplichte configuratiewaarde. De standaardwaarde is `DefaultDom` .
* **domainPattern**: Specificeert de domeinpatronen van inkomende e-mail die de leverancier goedkeurt. Als `adobe.com` bijvoorbeeld wordt gebruikt, wordt alleen e-mail van adobe.com verwerkt en wordt e-mail van andere domeinen genegeerd.
* **filePattern**: Specificeert de inkomende patronen van de dossiergehechtheid die de leverancier goedkeurt. Hiertoe behoren bestanden met specifieke bestandsextensies (&ast;.dat, &ast;.xml), bestanden met specifieke namen (gegevens) en bestanden met samengestelde expressies in de naam en extensie (&ast;..``[dD][aA]`` &#39;port&#39;). De standaardwaarde is `*` .
* **receivingSuccessfulJob**: Een e-mailadres waarnaar de berichten worden verzonden om op succesvolle banen te wijzen. Standaard wordt altijd een bericht met een geslaagde taak naar de afzender verzonden. Als u `sender` typt, worden de e-mailresultaten verzonden naar de afzender. Er worden maximaal 100 ontvangers ondersteund. Geef extra ontvangers op met e-mailadressen, die elk worden gescheiden door een komma. Laat deze waarde leeg als u deze optie wilt uitschakelen. In sommige gevallen wilt u wellicht een proces activeren en geen e-mailmelding van het resultaat. De standaardwaarde is `sender` .
* **receivingFailedJob**: Een e-mailadres waarnaar de berichten worden verzonden om ontbroken banen te wijzen. Standaard wordt een mislukte taakbericht altijd naar de afzender verzonden. Als u `sender` typt, worden de e-mailresultaten verzonden naar de afzender. Er worden maximaal 100 ontvangers ondersteund. Geef extra ontvangers op met e-mailadressen, die elk worden gescheiden door een komma. Laat deze waarde leeg als u deze optie wilt uitschakelen. De standaardwaarde is `sender` .
* **inboxHost**: De naam van de inbox gastheer of IP adres voor de e-mailleverancier om af te tasten.
* **inboxPort**: De haven die de e-mailserver gebruikt. De standaardwaarde voor POP3 is 110 en de standaardwaarde voor IMAP is 143. Als SSL wordt toegelaten, is de standaardwaarde voor POP3 995 en de standaardwaarde voor IMAP is 993.
* **inboxProtocol**: Het e-mailprotocol voor het e-maileindpunt te gebruiken om inbox af te tasten. De opties zijn `IMAP` of `POP3` . De postserver van de inbox gastheer moet deze protocollen steunen.
* **inboxTimeOut**: Tijd-uit in seconden voor de e-mailleverancier om op inbox reacties te wachten. De standaardwaarde is 60.
* **inboxUser**: De gebruikersnaam die aan login aan de e-mailrekening wordt vereist. Afhankelijk van de e-mailserver en configuratie is dit mogelijk alleen het gedeelte met de gebruikersnaam van de e-mail of het volledige e-mailadres.
* **inboxPassword**: Het wachtwoord voor de inbox gebruiker.
* **inboxSSLEnabled**: Plaats deze waarde om de e-mailleverancier te dwingen om SSL te gebruiken wanneer het verzenden van berichtberichten van resultaten of fouten. Zorg ervoor dat de IMAP- of POP3-host SSL ondersteunt.
* **smtpHost**: De gastheernaam van de postserver die de e-mailleverancier resultaten en foutenmeldingen naar verzendt.
* **smtpPort**: De standaardwaarde voor de haven SMTP is 25.
* **smtpUser**: De gebruikersrekening voor de e-mailleverancier aan gebruik wanneer het e-mailberichten van resultaten en fouten verzendt.
* **smtpPassword**: Het wachtwoord voor de rekening SMTP. Voor sommige mailservers is geen SMTP-wachtwoord vereist.
* **charSet**: Het karakter plaatste dat door de e-mailleverancier wordt gebruikt. De standaardwaarde is `UTF-8` .
* **smtpSSLEnabled**: Plaats deze waarde om de e-mailleverancier te dwingen om SSL te gebruiken wanneer het verzenden van berichtberichten van resultaten of fouten. Zorg ervoor dat de SMTP-host SSL ondersteunt.
* **failedJobFolder**: Specificeert een folder waarin om resultaten op te slaan wanneer de SMTP postserver niet operationeel is.
* **asynchroon**: Wanneer reeks aan synchroon, worden alle inputdocumenten verwerkt en één enkele reactie is teruggekeerd. Wanneer ingesteld op asynchroon, wordt een reactie verzonden voor elk invoerdocument dat wordt verwerkt. Bijvoorbeeld, wordt een E-mail eindpunt gecreeerd voor het proces dat in dit onderwerp wordt geïntroduceerd, en een e-mailbericht wordt verzonden naar inbox van het eindpunt dat veelvoudige onbeveiligde documenten van PDF bevat. Wanneer alle PDF-documenten met een wachtwoord zijn gecodeerd en als het eindpunt synchroon is geconfigureerd, wordt één e-mailbericht met reacties verzonden met alle beveiligde PDF-documenten bijgevoegd. Als het eindpunt asynchroon wordt gevormd, wordt een afzonderlijk reactie-e-mailbericht verzonden voor elk beveiligd PDF-document. Elk e-mailbericht bevat één PDF-document als bijlage. De standaardwaarde is asynchroon.

**bepalen de waarden van de inputparameter**

Wanneer u een e-maileindpunt maakt, moet u parameterwaarden voor invoer definiëren. Namelijk moet u de inputwaarden beschrijven die tot de verrichting worden overgegaan die door het E-maileindpunt wordt aangehaald. Neem bijvoorbeeld het proces dat in dit onderwerp is geïntroduceerd. Het heeft één invoerwaarde genoemd `InDoc` en zijn gegevenstype is `com.adobe.idp.Document`. Wanneer het creëren van een E-mail eindpunt voor dit proces (nadat een proces wordt geactiveerd, wordt het de dienst), moet u de waarde van de inputparameter bepalen.

Als u parameterwaarden voor invoer wilt definiëren die vereist zijn voor een e-maileindpunt, geeft u de volgende waarden op:

**de parameternaam van de Input**: De naam van de inputparameter. De naam van een inputwaarde wordt gespecificeerd in Workbench voor een proces. Als de inputwaarde tot een de dienstverrichting (de dienst van Forms die geen proces is in Workbench wordt gecreeerd) behoort, wordt de inputnaam gespecificeerd in het component.xml- dossier. De naam van de invoerparameter voor het in deze sectie geïntroduceerde proces is bijvoorbeeld `InDoc` .

**Type van Toewijzing**: Gebruikt om de inputwaarden te vormen die worden vereist om de de dienstverrichting aan te halen. Er zijn twee soorten toewijzingstypen:

* `Literal`: Het eindpunt E-mail gebruikt de waarde die in het veld wordt ingevoerd terwijl deze wordt weergegeven. Alle basistypen van Java worden ondersteund. Als een API bijvoorbeeld invoer gebruikt zoals String, long, int en Boolean, wordt de tekenreeks omgezet in het juiste type en wordt de service aangeroepen.
* `Variable`: De ingevoerde waarde is een bestandspatroon waarmee het e-maileindpunt de invoer kiest. Als u bijvoorbeeld Variabele selecteert voor het toewijzingstype en het invoerdocument moet een PDF-bestand zijn, kunt u `*.pdf` opgeven als toewijzingswaarde.

**Waarde van de Toewijzing**: Specificeert de waarde van het toewijzingstype. Als u bijvoorbeeld een toewijzingstype Variabele selecteert, kunt u `*.pdf` opgeven als bestandspatroon.

**Type van Gegevens**: Specificeert het gegevenstype van de inputwaarden. Het gegevenstype van de invoerwaarde van het proces dat in deze sectie wordt geïntroduceerd, is bijvoorbeeld com.adobe.idp.Document.

**bepaal een waarde van de outputparameter**

Wanneer u een e-maileindpunt maakt, moet u een uitvoerparameterwaarde definiëren. Namelijk moet u de outputwaarde beschrijven die door de dienst is teruggekeerd die door het E-maileindpunt wordt aangehaald. Neem bijvoorbeeld het proces dat in dit onderwerp is geïntroduceerd. Het heeft een outputwaarde genoemd `SecuredDoc` en zijn gegevenstype is `com.adobe.idp.Document`. Wanneer het creëren van een E-mail eindpunt voor dit proces (nadat een proces wordt geactiveerd, wordt het de dienst), moet u de waarde van de outputparameter bepalen.

Als u een uitvoerparameterwaarde wilt definiëren die voor een e-maileindpunt is vereist, geeft u de volgende waarden op:

**de parameternaam van de Output**: De naam van de outputparameter. De naam van een waarde voor de procesuitvoer wordt opgegeven in Workbench. Als de outputwaarde tot een de dienstverrichting (de dienst behoort die geen proces is dat in Workbench wordt gecreeerd), wordt de outputnaam gespecificeerd in het component.xml- dossier. De naam van de uitvoerparameter voor het proces dat in deze sectie wordt geïntroduceerd, is bijvoorbeeld `SecuredDoc` .

**Type van Toewijzing**: Gebruikt om de output van de dienst en de verrichting te vormen. De volgende opties zijn beschikbaar:

* Als de service één object (één document) retourneert, is het patroon `%F.pdf` en is de bronbestemming sourcefilename.pdf. Het in deze sectie geïntroduceerde proces retourneert bijvoorbeeld één document. Het toewijzingstype kan daarom worden gedefinieerd als `%F.pdf` ( `%F` betekent dat de opgegeven bestandsnaam wordt gebruikt). Met het patroon `%E` geeft u de extensie van het invoerdocument op.
* Als de service een lijst retourneert, is het patroon `Result\%F\` en is de bronbestemming Result\sourcefilename\source1 (uitvoer 1) en Result\sourceName\source2 (uitvoer 2).
* Als de service een kaart retourneert, is het patroon `Result\%F\` en is de bronbestemming Result\sourcefilename\file1 en Result\sourcefilename\file2. Als de kaart meerdere objecten bevat, is het patroon `Result\%F.pdf` en is de bronbestemming Result\sourcefilename1.pdf (uitvoer 1), Result\sourcefilenam2.pdf (uitvoer 2), enzovoort.

**Type van Gegevens**: Specificeert het gegevenstype van de terugkeerwaarde. Het gegevenstype van de geretourneerde waarde van het proces dat in deze sectie wordt geïntroduceerd, is bijvoorbeeld `com.adobe.idp.Document` .

**creeer het E-maileindpunt**

Nadat u de kenmerken en configuratiewaarden van het e-maileindpunt hebt ingesteld en invoer- en uitvoerparameters hebt gedefinieerd, moet u het eindpunt E-mail maken.

**laat het eindpunt** toe

Nadat u een eindpunt E-mail creeert, moet u het toelaten. Wanneer het eindpunt wordt toegelaten, kan het worden gebruikt om de dienst aan te halen. Nadat u het eindpunt toelaat, kunt u het binnen beleidsconsole bekijken.

**zie ook**

[Een e-maileindpunt toevoegen met de Java API](programmatically-endpoints.md#add-an-email-endpoint-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Een e-maileindpunt toevoegen met de Java API {#add-an-email-endpoint-using-the-java-api}

Voeg een eindpunt E-mail toe door Java API te gebruiken:

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-livecycle-client.jar, op in het klassenpad van uw Java-project.

1. Creeer een voorwerp van de Cliënt EndpointRegistry.

   * Maak een `ServiceClientFactory` -object dat verbindingseigenschappen bevat.
   * Maak een `EndpointRegistryClient` -object door de constructor ervan te gebruiken en het `ServiceClientFactory` -object door te geven.

1. Emaileindpuntkenmerken instellen.

   * Maak een `CreateEndpointInfo` -object met behulp van de constructor.
   * Geef de waarde van de connector-id op door de methode `CreateEndpointInfo` van het object `setConnectorId` aan te roepen en de tekenreekswaarde door te geven `Email` .
   * Geef de beschrijving van het eindpunt op door de methode `CreateEndpointInfo` van het object `setDescription` aan te roepen en een tekenreekswaarde door te geven die het eindpunt beschrijft.
   * Geef de naam van het eindpunt op door de methode `CreateEndpointInfo` van het object `setName` aan te roepen en een tekenreekswaarde door te geven die de naam opgeeft.
   * Geef de service op waartoe het eindpunt behoort door de methode `CreateEndpointInfo` van het object `setServiceId` aan te roepen en een tekenreekswaarde door te geven die de servicenaam opgeeft.
   * Geef de bewerking op die wordt aangeroepen door de methode `CreateEndpointInfo` van het object `setOperationName` aan te roepen en een tekenreekswaarde door te geven die de naam van de bewerking aangeeft. Typisch, wanneer het creëren van een E-mail eindpunt voor de dienst die van een proces voortkwam dat in Workbench wordt gecreeerd, wordt de naam van de verrichting gefactureerd.

1. Geef configuratiewaarden op.

   Voor elke configuratiewaarde die voor het eindpunt E-mail moet worden ingesteld, moet u de methode `CreateEndpointInfo` van het object `setConfigParameterAsText` aanroepen. Als u bijvoorbeeld de configuratiewaarde `smtpHost` wilt instellen, roept u de methode `CreateEndpointInfo` object `setConfigParameterAsText` aan en geeft u de volgende waarden door:

   * Een tekenreekswaarde die de naam van de configuratiewaarde opgeeft. Geef `smtpHost` op wanneer u de configuratiewaarde van `smtpHost` instelt.
   * Een tekenreeks die de waarde van de configuratiewaarde opgeeft. Wanneer u de configuratiewaarde `smtpHost` instelt, geeft u een tekenreekswaarde op die de naam van de SMTP-server opgeeft.

   >[!NOTE]
   >
   >Om alle configuratiewaarden te zien die voor de dienst EncryptDocument worden geplaatst die in deze sectie wordt geïntroduceerd, zie het de codevoorbeeld van Java dat bij [&#x200B; wordt gevestigd QuickStart: het toevoegen van een E-maileindpunt gebruikend Java API &#x200B;](/help/forms/developing/endpoint-registry-java-api-quick.md#quickstart-adding-an-email-endpoint-using-the-java-api).

1. Definieer invoerparameterwaarden.

   Definieer een invoerparameterwaarde door de methode `CreateEndpointInfo` van het object `setInputParameterMapping` aan te roepen en de volgende waarden door te geven:

   * Een tekenreekswaarde die de naam van de invoerparameter opgeeft. De naam van de invoerparameter voor de EncryptDocument-service is bijvoorbeeld `InDoc` .
   * Een tekenreeks die het gegevenstype van de invoerparameter opgeeft. Het gegevenstype van de invoerparameter `InDoc` is bijvoorbeeld `com.adobe.idp.Document` .
   * Een tekenreekswaarde die het toewijzingstype aangeeft. U kunt bijvoorbeeld `variable` opgeven.
   * Een tekenreekswaarde die de toewijzingswaarde opgeeft. U kunt bijvoorbeeld &ast;.pdf opgeven als bestandspatroon.

   >[!NOTE]
   >
   >Roep de methode `setInputParameterMapping` aan voor elke invoerparameterwaarde die moet worden gedefinieerd. Omdat het EncryptDocument-proces slechts één invoerparameter heeft, moet u deze methode eenmaal aanroepen.

1. Definieer een uitvoerparameterwaarde.

   Definieer een uitvoerparameterwaarde door de methode `CreateEndpointInfo` van het object `setOutputParameterMapping` aan te roepen en de volgende waarden door te geven:

   * Een tekenreekswaarde die de naam van de uitvoerparameter opgeeft. De naam van de uitvoerparameter voor de EncryptDocument-service is bijvoorbeeld `SecuredDoc` .
   * Een tekenreeks die het gegevenstype van de uitvoerparameter opgeeft. Het gegevenstype van de uitvoerparameter `SecuredDoc` is bijvoorbeeld `com.adobe.idp.Document` .
   * Een tekenreekswaarde die het toewijzingstype aangeeft. U kunt bijvoorbeeld `%F.pdf` opgeven.

1. Maak het eindpunt E-mail.

   Maak het eindpunt door de methode `EndpointRegistryClient` van het object `createEndpoint` aan te roepen en het object `CreateEndpointInfo` door te geven. Deze methode retourneert een `Endpoint` -object dat het eindpunt E-mail vertegenwoordigt.

1. Laat het eindpunt toe.

   Schakel het eindpunt in door de methode `EndpointRegistryClient` van het object `enable` aan te roepen en het object `Endpoint` door te geven dat door de methode `createEndpoint` is geretourneerd.

**zie ook**

[Overzicht van de stappen](programmatically-endpoints.md#summary-of-steps)

[QuickStart: een eindpunt voor een gecontroleerde map toevoegen met de Java API](/help/forms/developing/endpoint-registry-java-api-quick.md#quickstart-adding-a-watched-folder-endpoint-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Constante bestand voor waarden van e-mailconfiguratie {#email-configuration-values-constant-file}

[&#x200B; QuickStart: Het toevoegen van een E-maileindpunt gebruikend Java API &#x200B;](/help/forms/developing/endpoint-registry-java-api-quick.md#quickstart-adding-an-email-endpoint-using-the-java-api) gebruikt een constant dossier dat deel van uw project van Java moet uitmaken om het snelle begin te compileren. Dit constante dossier vertegenwoordigt configuratiewaarden die moeten worden geplaatst wanneer het toevoegen van een e-maileindpunt. De volgende Java-code vertegenwoordigt het constante bestand.

```java
 /**
     * This class contains constants that can be used when setting email endpoint
     * configuration values
     */
 public class EmailEndpointConfigConstants {

     public static final String PROPERTY_EMAILPROVIDER_CRON_EXPRESSION = "cronExpression";
     public static final String PROPERTY_EMAILPROVIDER_REPREAT_COUNT = "repeatCount";
     public static final String PROPERTY_EMAILPROVIDER_REPREAT_INTERVAL = "repeatInterval";
     public static final String PROPERTY_EMAILPROVIDER_START_DELAY = "startDelay";
     public static final String PROPERTY_EMAILPROVIDER_BATCH_SIZE = "batchSize";
     public static final String PROPERTY_EMAILPROVIDER_USERNAME = "userName";
     public static final String PROPERTY_EMAILPROVIDER_DOMAINNAME = "domainName";
     public static final String PROPERTY_EMAILPROVIDER_DOMAINPATTERN = "domainPattern";
     public static final String PROPERTY_EMAILPROVIDER_FILEPATTERN = "filePattern";
     public static final String PROPERTY_EMAILPROVIDER_RECIPIENT_SUCCESSFUL_JOB = "recipientSuccessfulJob";
     public static final String PROPERTY_EMAILPROVIDER_RECIPIENT_FAILED_JOB = "recipientFailedJob";
     public static final String PROPERTY_EMAILPROVIDER_INBOX_HOST = "inboxHost";
     public static final String PROPERTY_EMAILPROVIDER_INBOX_PORT = "inboxPort";
     public static final String PROPERTY_EMAILPROVIDER_PROTOCOL = "inboxProtocol";
     public static final String PROPERTY_EMAILPROVIDER_INBOX_TIMEOUT = "inboxTimeOut";
     public static final String PROPERTY_EMAILPROVIDER_INBOX_USER = "inboxUser";
     public static final String PROPERTY_EMAILPROVIDER_INBOX_PASSWORD = "inboxPassword";
     public static final String PROPERTY_EMAILPROVIDER_INBOX_SSL = "inboxSSLEnabled";
     public static final String PROPERTY_EMAILPROVIDER_SMTP_HOST = "smtpHost";
     public static final String PROPERTY_EMAILPROVIDER_SMTP_PORT = "smtpPort";
     public static final String PROPERTY_EMAILPROVIDER_SMTP_USER = "smtpUser";
     public static final String PROPERTY_EMAILPROVIDER_SMTP_PASSWORD = "smtpPassword";
     public static final String PROPERTY_EMAILPROVIDER_CHARSET = "charSet";
     public static final String PROPERTY_EMAILPROVIDER_SMTP_SSL = "smtpSSLEnabled";
     public static final String PROPERTY_EMAILPROVIDER_FAILED_FOLDER = "failedJobFolder";
     public static final String PROPERTY_EMAILPROVIDER_ASYNCHRONOUS = "asynchronous";
 }
```

## Eindpunten verwijderen toevoegen {#adding-remoting-endpoints}

>[!NOTE]
>
>API&#39;s van LiveCycle Remoting zijn verouderd voor AEM-formulieren op JEE.

U kunt programmatically een Remoting eindpunt aan de dienst toevoegen door AEM Forms Java API te gebruiken. Door een Remoting eindpunt toe te voegen, laat u een toepassing van Flex toe om de dienst aan te halen door het remoting te gebruiken. (Zie [&#x200B; het Aanhalen van AEM Forms die (voor de vormen van AEM wordt afgekeurd) AEM Forms verwijdert &#x200B;](/help/forms/developing/invoking-aem-forms-using-remoting.md#invoking-aem-forms-using-remoting).)

Voor de doeleinden van programmatically het toevoegen van een Verwijderend eindpunt aan de dienst, overweeg het volgende kortstondige proces genoemd *EncryptDocument*.

![&#x200B; ar_ar_encryptdocumentprocess &#x200B;](assets/ar_ar_encryptdocumentprocess.png)

Dit proces accepteert een onbeveiligd PDF-document als een invoerwaarde en geeft het onbeveiligde PDF-document vervolgens door aan de `EncryptPDFUsingPassword` -bewerking van de Encryption-service. Het PDF-document wordt versleuteld met een wachtwoord en het met een wachtwoord gecodeerde PDF-document is de uitvoerwaarde van dit proces. De naam van de invoerwaarde (het onbeveiligde PDF-document) is `InDoc` en het gegevenstype is `com.adobe.idp.Document` . De naam van de uitvoerwaarde (het met wachtwoord gecodeerde PDF-document) is `SecuredDoc` en het gegevenstype is `com.adobe.idp.Document` .

Om aan te tonen hoe te om een Remoting eindpunt aan de dienst toe te voegen, voegt deze sectie een Remoting eindpunt aan de dienst genoemd EncryptDocument toe.

>[!NOTE]
>
>U kunt geen eindpunt Remoting toevoegen door de Webdiensten te gebruiken.

### Overzicht van de stappen {#summary_of_steps-4}

Om een eindpunt uit de dienst te verwijderen, voer de volgende taken uit:

1. Inclusief projectbestanden.
1. Maak een `EndpointRegistryClient` -object.
1. Eindpuntkenmerken voor verwijderen instellen.
1. Maak een eindpunt Verwijderen.
1. Laat het eindpunt toe.

**omvat projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u de proxybestanden opnemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-utilities.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss Application Server)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss Application Server)

Voor informatie over de plaats van deze JAR dossiers, zie [&#x200B; Inclusief de bibliotheekdossiers van AEM Forms Java &#x200B;](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**creeer een voorwerp van de Cliënt EndpointRegistry**

Als u programmatisch een eindpunt Remoting wilt toevoegen, moet u een object `EndpointRegistryClient` maken.

**plaats het Verwijderen eindpuntattributen**

Om een Remoting eindpunt voor de dienst tot stand te brengen, specificeer de volgende waarden:

* **waarde van het herkenningsteken van de Schakelaar**: Specificeert het type van eindpunt dat wordt gecreeerd. Geef `Remoting` op als u een eindpunt voor verwijderen wilt maken.
* **Beschrijving**: Specificeert de beschrijving van het eindpunt.
* **Naam**: Specificeert de naam van het eindpunt.
* **het herkenningsteken van de Dienst**: Specificeert de dienst waartot het eindpunt behoort. Als u bijvoorbeeld een eindpunt Verwijderen wilt toevoegen aan het proces dat in deze sectie wordt geïntroduceerd (een proces wordt een service wanneer het binnen Workbench wordt geactiveerd), geeft u `EncryptDocument` op.
* **de naam van de Verrichting**: Specificeert de naam van de verrichting die door het eindpunt te gebruiken wordt aangehaald. Geef bij het maken van een eindpunt Remoting een jokerteken op (&ast;).

**creeer een Verwijderend eindpunt**

Nadat u het Verwijderen eindpuntattributen plaatst, kunt u een Remoting eindpunt voor de dienst tot stand brengen.

**laat het eindpunt** toe

Nadat u een eindpunt creeert, moet u het toelaten. Wanneer een Remoting eindpunt wordt toegelaten, laat het een cliënt van Flex toe om de dienst aan te halen.

**zie ook**

[Een eindpunt voor Verwijderen toevoegen met de Java API](programmatically-endpoints.md#add-a-remoting-endpoint-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Een eindpunt voor Verwijderen toevoegen met de Java API {#add-a-remoting-endpoint-using-the-java-api}

Voeg een Remoting eindpunt toe door Java API te gebruiken:

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-livecycle-client.jar, op in het klassenpad van uw Java-project.

1. Creeer een voorwerp van de Cliënt EndpointRegistry.

   * Maak een `ServiceClientFactory` -object dat verbindingseigenschappen bevat.
   * Maak een `EndpointRegistryClient` -object door de constructor ervan te gebruiken en het `ServiceClientFactory` -object door te geven.

1. Eindpuntkenmerken voor verwijderen instellen.

   * Maak een `CreateEndpointInfo` -object met behulp van de constructor.
   * Geef de waarde van de connector-id op door de methode `CreateEndpointInfo` van het object `setConnectorId` aan te roepen en de tekenreekswaarde door te geven `Remoting` .
   * Geef de beschrijving van het eindpunt op door de methode `CreateEndpointInfo` van het object `setDescription` aan te roepen en een tekenreekswaarde door te geven die het eindpunt beschrijft.
   * Geef de naam van het eindpunt op door de methode `CreateEndpointInfo` van het object `setName` aan te roepen en een tekenreekswaarde door te geven die de naam opgeeft.
   * Geef de service op waartoe het eindpunt behoort door de methode `CreateEndpointInfo` van het object `setServiceId` aan te roepen en een tekenreekswaarde door te geven die de servicenaam opgeeft.
   * Geef de bewerking op die wordt aangeroepen door de methode `CreateEndpointInfo` van het object `setOperationName` en geef een tekenreekswaarde door die de naam van de bewerking aangeeft. Geef voor een eindpunt Verwijderen een jokerteken op (&ast;).

1. Maak een eindpunt Verwijderen.

   Maak het eindpunt door de methode `EndpointRegistryClient` van het object `createEndpoint` aan te roepen en het object `CreateEndpointInfo` door te geven. Deze methode retourneert een `Endpoint` -object dat het nieuwe eindpunt Remoting vertegenwoordigt.

1. Laat het eindpunt toe.

   Schakel het eindpunt in door de methode `EndpointRegistryClient` van het object `enable` aan te roepen en het object `Endpoint` door te geven dat door de methode `createEndpoint` is geretourneerd.

**zie ook**

[Overzicht van de stappen](programmatically-endpoints.md#summary-of-steps)

[QuickStart: een eindpunt voor verwijderen toevoegen met de Java API](/help/forms/developing/endpoint-registry-java-api-quick.md#quickstart-adding-a-remoting-endpoint-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## TaskManager-eindpunten toevoegen {#adding-taskmanager-endpoints}

U kunt programmatically een eindpunt TaskManager aan de dienst toevoegen door AEM Forms Java API te gebruiken. Door een eindpunt TaskManager aan de dienst toe te voegen, laat u een gebruiker van Workspace toe om de dienst aan te halen. Namelijk kan een gebruiker die in Workspace werkt een proces aanhalen dat een overeenkomstig eindpunt TaskManager heeft.

>[!NOTE]
>
>U kunt geen eindpunt TaskManager toevoegen door de Webdiensten te gebruiken.

### Overzicht van de stappen {#summary_of_steps-5}

Om een eindpunt TaskManager aan de dienst toe te voegen, voer de volgende taken uit:

1. Inclusief projectbestanden.
1. Maak een `EndpointRegistryClient` -object.
1. Maak een categorie voor het eindpunt.
1. Stel de eindpuntkenmerken van TaskManager in.
1. Creeer een eindpunt TaskManager.
1. Laat het eindpunt toe.

**omvat projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u de proxybestanden opnemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-utilities.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss Application Server)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss Application Server)

Voor informatie over de plaats van deze JAR dossiers, zie [&#x200B; Inclusief de bibliotheekdossiers van AEM Forms Java &#x200B;](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**creeer een voorwerp van de Cliënt EndpointRegistry**

Voordat u via programmacode een TaskManager-eindpunt kunt toevoegen, moet u een `EndpointRegistryClient` -object maken.

**creeer een categorie voor het eindpunt**

Categorieën worden gebruikt om services in Workspace te organiseren. Namelijk kan een gebruiker van Workspace de dienst aanhalen die een eindpunt TaskManager door een categorie binnen Workspace te selecteren heeft. Wanneer het creëren van een eindpunt TaskManager, kunt u of van verwijzingen voorzien een bestaande categorie of programmatically tot een categorie leiden.

>[!NOTE]
>
>Deze sectie leidt tot een nieuwe categorie als deel van het toevoegen van een eindpunt TaskManager aan de dienst.

**plaats TaskManager eindpuntattributen**

Om een eindpunt TaskManager voor de dienst tot stand te brengen, specificeer de volgende waarden:

* **herkenningsteken van de Schakelaar**: Specificeert het type van eindpunt dat wordt gecreeerd. Om een eindpunt tot stand te brengen TaskManager, specificeer `TaskManagerConnector`.
* **Beschrijving**: Specificeert de beschrijving van het eindpunt.
* **Naam**: Specificeert de naam van het eindpunt.
* **herkenningsteken van de Dienst**: Specificeert de dienst waartot het eindpunt behoort.
* **Categorie**: Specificeert een waarde van categoridentificatiecode die met het eindpunt TaskManager wordt geassocieerd.
* **naam van de Verrichting**: Typisch, wanneer het creëren van een eindpunt TaskManager voor de dienst die van een proces voortkwam dat in Workbench wordt gecreeerd, is de naam van de verrichting `invoke`.

**creeer een eindpunt TaskManager**

Nadat u een taakmanager eindpuntattributen plaatst, kunt u een eindpunt TaskManager voor de dienst tot stand brengen.

**laat het eindpunt** toe

Nadat u een eindpunt creeert, moet u het toelaten. Wanneer het eindpunt wordt toegelaten, kan het worden gebruikt om de dienst van binnen Workspace aan te halen. Nadat u het eindpunt toelaat, kunt u het binnen beleidsconsole bekijken.

**zie ook**

[Een TaskManager-eindpunt toevoegen met de Java API](programmatically-endpoints.md#add-a-taskmanager-endpoint-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Een TaskManager-eindpunt toevoegen met de Java API {#add-a-taskmanager-endpoint-using-the-java-api}

Voeg een eindpunt TaskManager door Java API toe te gebruiken:

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-livecycle-client.jar, op in het klassenpad van uw Java-project.

1. Creeer een voorwerp van de Cliënt EndpointRegistry.

   * Maak een `ServiceClientFactory` -object dat verbindingseigenschappen bevat.
   * Maak een `EndpointRegistryClient` -object door de constructor ervan te gebruiken en het `ServiceClientFactory` -object door te geven.

1. Maak een categorie voor het eindpunt.

   * Maak een `CreateEndpointCategoryInfo` -object door de constructor ervan te gebruiken en de volgende waarden door te geven:

      * Een tekenreekswaarde die de id-waarde van de categorie opgeeft
      * Een tekenreekswaarde die de beschrijving van de categorie opgeeft

   * Maak de categorie door de methode `EndpointRegistryClient` van het object `createEndpointCategory` aan te roepen en het object `CreateEndpointCategoryInfo` door te geven. Deze methode retourneert een `EndpointCategory` -object dat de nieuwe categorie vertegenwoordigt.

1. Stel de eindpuntkenmerken van TaskManager in.

   * Maak een `CreateEndpointInfo` -object met behulp van de constructor.
   * Geef de waarde van de connector-id op door de methode `CreateEndpointInfo` van het object `setConnectorId` aan te roepen en de tekenreekswaarde door te geven `TaskManagerConnector` .
   * Geef de beschrijving van het eindpunt op door de methode `CreateEndpointInfo` van het object `setDescription` aan te roepen en een tekenreekswaarde door te geven die het eindpunt beschrijft.
   * Geef de naam van het eindpunt op door de methode `CreateEndpointInfo` van het object `setName` aan te roepen en een tekenreekswaarde door te geven die de naam opgeeft.
   * Geef de service op waartoe het eindpunt behoort door de methode `CreateEndpointInfo` van het object `setServiceId` aan te roepen en een tekenreekswaarde door te geven die de servicenaam opgeeft.
   * Geef de categorie op waartoe het eindpunt behoort door de methode `CreateEndpointInfo` van het `setCategoryId` -object aan te roepen en een tekenreekswaarde door te geven die de categorie-id-waarde opgeeft. U kunt de methode `EndpointCategory` van het `getId` -object aanroepen om de id-waarde van deze categorie op te halen.
   * Geef de bewerking op die wordt aangeroepen door de methode `CreateEndpointInfo` van het object `setOperationName` aan te roepen en een tekenreekswaarde door te geven die de naam van de bewerking aangeeft. Doorgaans is de naam van de bewerking `TaskManager` wanneer u een `invoke` -eindpunt maakt voor een service die afkomstig is van een proces dat in Workbench is gemaakt.

1. Creeer een eindpunt TaskManager.

   Maak het eindpunt door de methode `EndpointRegistryClient` van het object `createEndpoint` aan te roepen en het object `CreateEndpointInfo` door te geven. Deze methode retourneert een `Endpoint` -object dat het nieuwe TaskManager-eindpunt vertegenwoordigt.

1. Laat het eindpunt toe.

   Schakel het eindpunt in door de methode `EndpointRegistryClient` van het object `enable` aan te roepen en het object `Endpoint` door te geven dat door de methode `createEndpoint` is geretourneerd.

**zie ook**

[Overzicht van de stappen](programmatically-endpoints.md#summary-of-steps)

[QuickStart: een TaskManager-eindpunt toevoegen met de Java API](/help/forms/developing/endpoint-registry-java-api-quick.md#quickstart-adding-a-taskmanager-endpoint-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Eindpunten wijzigen {#modifying-endpoints}

U kunt een bestaand eindpunt programmatically wijzigen door AEM Forms Java API te gebruiken. Door een eindpunt te wijzigen, kunt u het gedrag van het eindpunt veranderen. Denk bijvoorbeeld aan een eindpunt van een gecontroleerde map dat een map opgeeft die als controlemap wordt gebruikt. U kunt configuratiewaarden programmatically wijzigen die tot het Gecontroleerde eindpunt van de Omslag behoren, resulterend in een andere omslag die als gecontroleerde omslag functioneert. Voor informatie over configuratiewaarden die tot een Gecontroleerd eindpunt van de Omslag behoren, zie [&#x200B; Toevoegend Gecontroleerde Eindpunten van de Omslag &#x200B;](programmatically-endpoints.md#adding-watched-folder-endpoints).

Om aan te tonen hoe te om een eindpunt te wijzigen, wijzigt deze sectie een Gecontroleerd eindpunt van de Omslag door de omslag te veranderen die zich als gecontroleerde omslag gedraagt.

>[!NOTE]
>
>U kunt een eindpunt niet wijzigen door de Webdiensten te gebruiken.

### Overzicht van de stappen {#summary_of_steps-6}

Om een eindpunt te wijzigen, voer de volgende taken uit:

1. Inclusief projectbestanden.
1. Maak een `EndpointRegistryClient` -object.
1. Haal het eindpunt op.
1. Geef nieuwe configuratiewaarden op.

**omvat projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u de proxybestanden opnemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-utilities.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss Application Server)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss Application Server)

Voor informatie over de plaats van deze JAR dossiers, zie [&#x200B; Inclusief de bibliotheekdossiers van AEM Forms Java &#x200B;](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**creeer een voorwerp van de Cliënt EndpointRegistry**

Als u een eindpunt programmatisch wilt wijzigen, moet u een `EndpointRegistryClient` -object maken.

**wint het eindpunt terug om** te wijzigen

Alvorens u een eindpunt kunt wijzigen, moet u het terugwinnen. Om een eindpunt terug te winnen, moet u als gebruiker verbinden die tot een eindpunt kan toegang hebben. U wordt aangeraden verbinding te maken als beheerder. (Zie [&#x200B; Plaatsende verbindingseigenschappen &#x200B;](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)).

U kunt een eindpunt terugwinnen door een lijst van eindpunten terug te winnen. U kunt dan door de lijst herhalen, zoekend naar het specifieke eindpunt om te verwijderen. Bijvoorbeeld, kunt u van een eindpunt de plaats bepalen door de dienst te bepalen die aan het eindpunt en het type van eindpunt beantwoordt. Wanneer u van het eindpunt de plaats bepaalt, kunt u het wijzigen.

**specificeer nieuwe configuratiewaarden**

Wanneer het wijzigen van een eindpunt, specificeer nieuwe configuratiewaarden. Bijvoorbeeld, om een Gecontroleerd eindpunt van de Omslag te wijzigen, terugstel alle Gecontroleerde waarden van de de eindpuntconfiguratie van de Omslag, niet alleen degenen die u wilt wijzigen. Voor informatie over configuratiewaarden die tot een Gecontroleerd eindpunt van de Omslag behoren, zie [&#x200B; Toevoegend Gecontroleerde Eindpunten van de Omslag &#x200B;](programmatically-endpoints.md#adding-watched-folder-endpoints).

>[!NOTE]
>
>Voor informatie over configuratiewaarden die tot een E-mail- eindpunt behoren, zie [&#x200B; Toevoegend E-mail Eindpunten &#x200B;](programmatically-endpoints.md#adding-email-endpoints).

>[!NOTE]
>
>U kunt niet de dienst wijzigen die door het eindpunt wordt aangehaald. Als u probeert om de dienst te wijzigen, wordt een uitzondering geworpen. Om de dienst te wijzigen verbonden aan een bepaald eindpunt, verwijder het eindpunt en creeer één. (Zie [&#x200B; Verwijderend Eindpunten &#x200B;](programmatically-endpoints.md#removing-endpoints).)

**zie ook**

[Een eindpunt wijzigen met de Java API](programmatically-endpoints.md#modifying-an-endpoint-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Een eindpunt wijzigen met de Java API {#modifying-an-endpoint-using-the-java-api}

Wijzig een eindpunt door Java API te gebruiken:

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-livecycle-client.jar, op in het klassenpad van uw Java-project.

1. Creeer een voorwerp van de Cliënt EndpointRegistry.

   * Maak een `ServiceClientFactory` -object dat verbindingseigenschappen bevat.
   * Maak een `EndpointRegistryClient` -object door de constructor ervan te gebruiken en het `ServiceClientFactory` -object door te geven.

1. Haal het eindpunt op dat u wilt wijzigen.

   * Haal een lijst op van alle eindpunten waartoe de huidige gebruiker (opgegeven in de eigenschappen van de verbinding) toegang heeft door de methode `EndpointRegistryClient` van het object `getEndpoints` aan te roepen en een object `PagingFilter` door te geven dat als filter fungeert. U kunt een `(PagingFilter)null` -waarde doorgeven om alle eindpunten te retourneren. Deze methode retourneert een `java.util.List` -object waarbij elk element een `Endpoint` -object is. Voor informatie over a `PagingFilter` voorwerp, zie [&#x200B; AEM Forms API Verwijzing &#x200B;](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).
   * Doorloop het `java.util.List` -object om te bepalen of het eindpunten heeft. Als er eindpunten zijn, is elk element een `EndPoint` -instantie.
   * Bepaal de service die overeenkomt met een eindpunt door de methode `EndPoint` van het object `getServiceId` aan te roepen. Deze methode retourneert een tekenreekswaarde die de servicenaam opgeeft.
   * Bepaal het type eindpunt door de methode `EndPoint` van het object `getConnectorId` aan te roepen. Deze methode retourneert een tekenreekswaarde die het type eindpunt opgeeft. Als het eindpunt bijvoorbeeld een Gecontroleerd mapeindpunt is, retourneert deze methode `WatchedFolder` .

1. Geef nieuwe configuratiewaarden op.

   * Maak een `ModifyEndpointInfo` -object door de constructor ervan aan te roepen.
   * Roep voor elke configuratiewaarde die moet worden ingesteld de methode `ModifyEndpointInfo` van het `setConfigParameterAsText` -object aan. Als u bijvoorbeeld de waarde voor de url-configuratie wilt instellen, roept u de methode `ModifyEndpointInfo` van het `setConfigParameterAsText` -object op en geeft u de volgende waarden door:

      * Een tekenreekswaarde die de naam van de configuratiewaarde opgeeft. Als u bijvoorbeeld de configuratiewaarde `url` wilt instellen, geeft u `url` op.
      * Een tekenreeks die de waarde van de configuratiewaarde opgeeft. Als u een waarde voor de configuratiewaarde `url` wilt definiëren, geeft u de locatie van de gecontroleerde map op.

   * Roep de methode `EndpointRegistryClient` van het object `modifyEndpoint` aan en geef het object `ModifyEndpointInfo` door.

**zie ook**

[Overzicht van de stappen](programmatically-endpoints.md#summary-of-steps)

[QuickStart: een eindpunt wijzigen met de Java API](/help/forms/developing/endpoint-registry-java-api-quick.md#quickstart-modifying-an-endpoint-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Eindpunten verwijderen {#removing-endpoints}

U kunt een eindpunt uit de dienst programmatically verwijderen door AEM Forms Java API te gebruiken. Nadat u een eindpunt verwijdert, kan de dienst niet worden aangehaald door de aanroepingsmethode te gebruiken die het eindpunt toeliet. Bijvoorbeeld, als u een eindpunt van SOAP uit de dienst verwijdert, kunt u niet de dienst aanhalen door de wijze van SOAP te gebruiken.

Om aan te tonen hoe te om een eindpunt uit de dienst te verwijderen, verwijdert deze sectie een eindpunt EJB uit de dienst genoemd *EncryptDocument*.

>[!NOTE]
>
>U kunt geen eindpunt verwijderen door de Webdiensten te gebruiken.

### Overzicht van de stappen {#summary_of_steps-7}

Om een eindpunt uit de dienst te verwijderen, voer de volgende taken uit:

1. Inclusief projectbestanden.
1. Maak een `EndpointRegistryClient` -object.
1. Haal het eindpunt op.
1. Verwijder het eindpunt.

**omvat projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u de proxybestanden opnemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-utilities.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss Application Server)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss Application Server)

Voor informatie over de plaats van deze JAR dossiers, zie [&#x200B; Inclusief de bibliotheekdossiers van AEM Forms Java &#x200B;](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**creeer een voorwerp van de Cliënt EndpointRegistry**

Als u een eindpunt programmatisch wilt verwijderen, moet u een `EndpointRegistryClient` -object maken.

**wint het eindpunt terug om** te verwijderen

Voordat u een eindpunt kunt verwijderen, moet u het ophalen. Om een eindpunt terug te winnen, moet u als gebruiker verbinden die tot een eindpunt kan toegang hebben. U wordt aangeraden verbinding te maken als beheerder. (Zie [&#x200B; Plaatsende verbindingseigenschappen &#x200B;](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)).

U kunt een eindpunt terugwinnen door een lijst van eindpunten terug te winnen. U kunt dan door de lijst herhalen, zoekend naar het specifieke eindpunt om te verwijderen. Bijvoorbeeld, kunt u van een eindpunt de plaats bepalen door de dienst te bepalen die aan het eindpunt en het type van eindpunt beantwoordt. Wanneer u het eindpunt zoekt, kunt u het verwijderen.

**verwijder het eindpunt**

Nadat u een eindpunt creeert, moet u het toelaten. Wanneer het eindpunt wordt toegelaten, kan het worden gebruikt om de dienst aan te halen. Nadat u het eindpunt toelaat, kunt u het binnen beleidsconsole bekijken.

**zie ook**

[Een eindpunt verwijderen met de Java API](programmatically-endpoints.md#removing-an-endpoint-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Een eindpunt verwijderen met de Java API {#removing-an-endpoint-using-the-java-api}

Een eindpunt verwijderen met de Java API:

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-livecycle-client.jar, op in het klassenpad van uw Java-project.

1. Creeer een voorwerp van de Cliënt EndpointRegistry.

   * Maak een `ServiceClientFactory` -object dat verbindingseigenschappen bevat.
   * Maak een `EndpointRegistryClient` -object door de constructor ervan te gebruiken en het `ServiceClientFactory` -object door te geven.

1. Haal het te verwijderen eindpunt op.

   * Haal een lijst op van alle eindpunten waartoe de huidige gebruiker (opgegeven in de eigenschappen van de verbinding) toegang heeft door de methode `EndpointRegistryClient` van het object `getEndpoints` aan te roepen en een object `PagingFilter` door te geven dat als filter fungeert. U kunt `(PagingFilter)null` doorgeven om alle eindpunten te retourneren. Deze methode retourneert een `java.util.List` -object waarbij elk element een `Endpoint` -object is.
   * Doorloop het `java.util.List` -object om te bepalen of het eindpunten heeft. Als er eindpunten zijn, is elk element een `EndPoint` -instantie.
   * Bepaal de service die overeenkomt met een eindpunt door de methode `EndPoint` van het object `getServiceId` aan te roepen. Deze methode retourneert een tekenreekswaarde die de servicenaam opgeeft.
   * Bepaal het type eindpunt door de methode `EndPoint` van het object `getConnectorId` aan te roepen. Deze methode retourneert een tekenreekswaarde die het type eindpunt opgeeft. Als het eindpunt bijvoorbeeld een EJB-eindpunt is, retourneert deze methode `EJB` .

1. Verwijder het eindpunt.

   Verwijder het eindpunt door de methode `EndpointRegistryClient` van het object `remove` aan te roepen en het object `EndPoint` door te geven dat het eindpunt vertegenwoordigt dat moet worden verwijderd.

**zie ook**

[Overzicht van de stappen](programmatically-endpoints.md#summary-of-steps)

[QuickStart: een eindpunt verwijderen met de Java API](/help/forms/developing/endpoint-registry-java-api-quick.md#quickstart-removing-an-endpoint-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Gegevens eindpuntconnector ophalen {#retrieving-endpoint-connector-information}

U kunt informatie over eindpuntschakelaars programmatically terugwinnen gebruikend AEM Forms API. Een schakelaar laat een eindpunt toe om de dienst aan te halen gebruikend diverse aanroepingsmethodes. Bijvoorbeeld, laat een Gecontroleerde schakelaar van de Omslag een eindpunt toe om de dienst aan te halen gebruikend gecontroleerde omslagen. Door programmatically het terugwinnen van informatie over eindpuntschakelaars, kunt u configuratiewaarden terugwinnen verbonden aan een schakelaar zoals welke configuratiewaarden worden vereist en welke facultatieve zijn.

Om aan te tonen hoe te om informatie over eindpuntschakelaars terug te winnen, wint deze sectie informatie over een Gecontroleerde schakelaar van de Omslag terug. (Zie [&#x200B; Toevoegend Gecontroleerde Eindpunten van de Omslag &#x200B;](programmatically-endpoints.md#adding-watched-folder-endpoints).)

>[!NOTE]
>
>U kunt geen informatie over eindpunten terugwinnen door de Webdiensten te gebruiken.

>[!NOTE]
>
>Dit onderwerp gebruikt `ConnectorRegistryClient` API om informatie over eindpuntschakelaars terug te winnen. (Zie [&#x200B; AEM Forms API Verwijzing &#x200B;](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).)

### Overzicht van de stappen {#summary_of_steps-8}

Om de informatie van de eindpuntschakelaar terug te winnen, voer de volgende taken uit:

1. Inclusief projectbestanden.
1. Maak een `ConnectorRegistryClient` -object.
1. Geef het type aansluiting op.
1. Haal configuratiewaarden op.

**omvat projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u de proxybestanden opnemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-utilities.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss Application Server)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss Application Server)

Als AEM Forms wordt geïmplementeerd op een ondersteunde J2EE-toepassingsserver die geen JBoss is, vervangt u adobe-utilities.jar en jbossall-client.jar door JAR-bestanden die specifiek zijn voor de J2EE-toepassingsserver waarop AEM Forms wordt geïmplementeerd. Voor informatie over de plaats van alle dossiers van AEM Forms JAR, zie [&#x200B; Inclusief de bibliotheekdossiers van AEM Forms Java &#x200B;](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**creeer een voorwerp van de Cliënt ConnectorRegistry**

Maak een `ConnectorRegistryClient` -object om de informatie over de eindpuntaansluiting programmatisch op te halen.

**specificeer het schakelaartype**

Specificeer het type van schakelaar waarvan om informatie terug te winnen. De volgende types van schakelaars bestaan:

* **EJB**: Laat een cliënttoepassing toe om de dienst aan te halen gebruikend de wijze EJB.
* **SOAP**: Laat een cliënttoepassing toe om de dienst aan te halen gebruikend de wijze van SOAP.
* **Gecontroleerde Omslag**: Laat gecontroleerde omslagen toe om de dienst aan te halen.
* **E-mail**: Laat e-mailberichten toe om de dienst aan te halen.
* **het Verwijderen**: Laat een de cliënttoepassing van Flex toe om de dienst aan te halen.
* **TaskManagerConnector**: Laat een gebruiker van Workspace toe om de dienst van binnen Workspace aan te halen.

**wint configuratiewaarden** terug

Nadat u het schakelaartype specificeert, kunt u informatie over de schakelaar zoals gesteunde configuratiewaarde terugwinnen. Bijvoorbeeld, voor om het even welke schakelaar, kunt u bepalen welke configuratiewaarden worden vereist en die facultatief zijn.

**zie ook**

[Gegevens van eindpuntconnector ophalen met de Java API](programmatically-endpoints.md#retrieve-endpoint-connector-information-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Gegevens van eindpuntconnector ophalen met de Java API {#retrieve-endpoint-connector-information-using-the-java-api}

Haal de informatie van de eindpuntschakelaar door Java API te gebruiken terug:

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-livecycle-client.jar, op in het klassenpad van uw Java-project.

1. Creeer een voorwerp van de Cliënt ConnectorRegistry.

   * Maak een `ServiceClientFactory` -object dat verbindingseigenschappen bevat.
   * Maak een `ConnectorRegistryClient` -object door de constructor ervan te gebruiken en het `ServiceClientFactory` -object door te geven.

1. Geef het type aansluiting op.

   Geef het type connector op door de methode `ConnectorRegistryClient` van het object `getEndpointDefinition` aan te roepen en een tekenreekswaarde door te geven die het type connector aangeeft. Als u bijvoorbeeld het verbindingstype Gecontroleerde map wilt opgeven, geeft u de tekenreekswaarde `WatchedFolder` door. Deze methode retourneert een `Endpoint` -object dat overeenkomt met het type connector.

1. Haal configuratiewaarden op.

   * Haal configuratiewaarden op die binnen dit eindpunt zijn gekoppeld door de methode `Endpoint` van het object `getConfigParameters` aan te roepen. Deze methode retourneert een array van `ConfigParameter` -objecten.
   * Haal informatie over elke configuratiewaarde op door elk element binnen de serie terug te winnen. Elk element is een `ConfigParameter` -object. U kunt bijvoorbeeld bepalen of de configuratiewaarde verplicht of optioneel is door de methode `ConfigParameter` van het object `isRequired` aan te roepen. Als de configuratiewaarde wordt vereist, dan keert deze methode `true` terug.

**zie ook**

[Overzicht van de stappen](programmatically-endpoints.md#summary-of-steps)

[QuickStart: informatie over eindpuntaansluiting ophalen met de Java API](/help/forms/developing/endpoint-registry-java-api-quick.md#quickstart-retrieving-endpoint-connector-information-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)
