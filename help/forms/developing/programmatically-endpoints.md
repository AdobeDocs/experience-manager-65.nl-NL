---
title: Programmaticaal het leiden Eindpunten
seo-title: Programmaticaal het leiden Eindpunten
description: 'null'
seo-description: 'null'
uuid: 5dc50946-3323-4c5d-a43b-31c1c980bd04
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 076889a7-9c9f-4b6f-a45b-67a9b3923c36
translation-type: tm+mt
source-git-commit: 1343cc33a1e1ce26c0770a3b49317e82353497ab
workflow-type: tm+mt
source-wordcount: '10781'
ht-degree: 0%

---


# Programmaticaal het leiden Eindpunten {#programmatically-managing-endpoints}

**Info over Endpoint Registry Service**

De dienst van de Registratie van het Eindpunt verstrekt de capaciteit om eindpunten programmatically te beheren. U kunt, bijvoorbeeld, de volgende types van eindpunten aan de dienst toevoegen:

* EJB
* SOAP
* Controlemap
* E-mail
* (Verouderd voor AEM-formulieren) Verwijderen
* Taakbeheer

>[!NOTE]
>
>SOAP, EJB en (Verouderd voor AEM-formulieren op JEE) Eindpunten verwijderen worden automatisch gemaakt voor elke geactiveerde service. De eindpunten SOAP en EJB laten ZEEP en EJB voor alle de dienstverrichtingen toe.

Een Remoting eindpunt laat Flex cliënten toe om verrichtingen op de dienst van AEM Forms aan te halen die het eindpunt aan wordt toegevoegd. Een Flex bestemming met de zelfde naam zoals het eindpunt wordt gecreeerd en Flex cliënten kunnen tot RemoteObjects leiden die aan deze bestemming richten om verrichtingen op de relevante dienst aan te halen.

De e-mail, de Manager van de Taak, en de Gecontroleerde eindpunten van de Omslag stellen slechts een specifieke verrichting van de dienst bloot. Het toevoegen van deze eindpunten vereist een tweede configuratiestap om een methode te selecteren om te roepen, configuratieparameters te plaatsen, en input en outputparameterafbeeldingen te specificeren.

U kunt eindpunten TaskManager in groepen organiseren genoemd *categorieën*. Deze categorieën worden dan blootgesteld aan Werkruimte door TaskManager, met eind - de gebruikers zien de eindpunten TaskManager aangezien zij worden gecategoriseerd. In Workspace zien eindgebruikers deze categorieën in het navigatievenster. De eindpunten binnen elke categorie worden weergegeven als proceskaarten op de pagina Processen starten in Workspace.

U kunt deze taken verwezenlijken gebruikend de dienst van de Registratie van het Eindpunt:

* EJB-eindpunten toevoegen. (Zie EJB-eindpunten [toevoegen](programmatically-endpoints.md#adding-ejb-endpoints).)
* Voeg de eindpunten van de ZEEP toe. (Zie [SOAP-eindpunten](programmatically-endpoints.md#adding-soap-endpoints)toevoegen.)
* Eindpunten van gecontroleerde mappen toevoegen (zie [Gecontroleerde eindpunten](programmatically-endpoints.md#adding-watched-folder-endpoints)van mappen toevoegen)
* E-maileindpunten toevoegen. (Zie E-maileindpunten [toevoegen](programmatically-endpoints.md#adding-email-endpoints).)
* Voeg eindpunten voor verwijderen toe. (Zie Eindpunten [verwijderen](programmatically-endpoints.md#adding-remoting-endpoints)toevoegen.)
* Voeg eindpunten TaskManager toe (zie het [Toevoegen van Eindpunten](programmatically-endpoints.md#adding-taskmanager-endpoints)TaskManager.)
* Eindpunten wijzigen (Zie Eindpunten [wijzigen](programmatically-endpoints.md#modifying-endpoints).)
* Eindpunten verwijderen (zie Eindpunten [verwijderen](programmatically-endpoints.md#removing-endpoints).)
* Haal de informatie van de eindpuntschakelaar terug (zie het [Terugwinnen van de Informatie](programmatically-endpoints.md#retrieving-endpoint-connector-information)van de Verbinding van het Eindpunt.)

## EJB-eindpunten toevoegen {#adding-ejb-endpoints}

U kunt een eindpunt EJB aan de dienst programmatically toevoegen door AEM Forms Java API te gebruiken. Door een eindpunt EJB aan de dienst toe te voegen, laat u een cliënttoepassing toe om de dienst aan te halen door de wijze te gebruiken EJB. Met andere woorden, wanneer u verbindingseigenschappen instelt die nodig zijn om AEM Forms aan te roepen, kunt u de EJB-modus selecteren. (Zie Verbindingseigenschappen [instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)

>[!NOTE]
>
>U kunt geen EJB eindpunt toevoegen door de Webdiensten te gebruiken.

>[!NOTE]
>
>Typisch, wordt een eindpunt EJB toegevoegd aan de dienst door gebrek, echter, kan een eindpunt EJB aan een proces worden toegevoegd dat programmatically wordt opgesteld of wanneer een eindpunt EJB werd verwijderd en opnieuw moet worden toegevoegd.

### Overzicht van de stappen {#summary-of-steps}

Om een eindpunt EJB aan de dienst toe te voegen, voer de volgende taken uit:

1. Inclusief projectbestanden.
1. Maak een `EndpointRegistry Client` object.
1. EJB-eindpuntkenmerken instellen.
1. Maak een EJB-eindpunt.
1. Laat het eindpunt toe.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-utilities.jar (vereist als AEM Forms worden geïmplementeerd op JBoss Application Server)
* jbossall-client.jar (vereist als AEM Forms worden geïmplementeerd op JBoss Application Server)

Zie [Including AEM Forms Java library files](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)voor informatie over de locatie van deze JAR-bestanden.

**Een EndpointRegistry-client-object maken**

Voordat u via programmacode een EJB-eindpunt kunt toevoegen, moet u een `EndpointRegistryClient` object maken.

**EJB-eindpuntkenmerken instellen**

Om een EJB eindpunt voor de dienst tot stand te brengen, specificeer de volgende waarden:

* **Connector-id**: Geeft het type eindpunt op dat moet worden gemaakt. Om een EJB eindpunt tot stand te brengen, specificeer `EJB`.
* **Omschrijving**: Specificeert de eindpuntbeschrijving.
* **Naam**: Specificeert de naam van het eindpunt.
* **Service-id**: Specificeert de dienst waartot het eindpunt behoort.
* **Bewerkingsnaam**: Specificeert de naam van de verrichting die door het eindpunt te gebruiken wordt aangehaald. Wanneer het creëren van een eindpunt EJB, specificeer een vervangingskarakter ( `*`). Nochtans, als u een specifieke verrichting in tegenstelling tot het aanhalen van alle de dienstverrichtingen wilt specificeren, specificeer de naam van de verrichting in plaats van het gebruiken van het vervangingskarakter ( `*`).

**Een EJB-eindpunt maken**

Nadat u EJB eindpuntattributen plaatst, kunt u een eindpunt EJB voor de dienst tot stand brengen.

**Het eindpunt inschakelen**

Nadat u een nieuw eindpunt creeert, moet u het toelaten. Nadat u het eindpunt toelaat, kan het worden gebruikt om de dienst aan te halen. Nadat u het eindpunt toelaat, kunt u het binnen beleidsconsole bekijken.

**Zie ook**

[Een EJB-eindpunt toevoegen met de Java API](programmatically-endpoints.md#adding-an-ejb-endpoint-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Een EJB-eindpunt toevoegen met de Java API {#adding-an-ejb-endpoint-using-the-java-api}

Voeg een EJB eindpunt toe door Java API te gebruiken:

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-livecycle-client.jar, op in het klassenpad van uw Java-project. (

1. Creeer een voorwerp van de Cliënt EndpointRegistry.

   * Maak een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Maak een `EndpointRegistryClient` object door de constructor ervan te gebruiken en het `ServiceClientFactory` object door te geven.

1. EJB-eindpuntkenmerken instellen.

   * Maak een `CreateEndpointInfo` object met de constructor ervan.
   * Geef de waarde van de connector-id op door de methode van het `CreateEndpointInfo` object aan te roepen en de tekenreekswaarde door te geven `setConnectorId` `EJB`.
   * Geef de beschrijving van het eindpunt op door de methode van het `CreateEndpointInfo` `setDescription` object aan te roepen en een tekenreekswaarde door te geven die het eindpunt beschrijft.
   * Geef de naam van het eindpunt op door de methode van het `CreateEndpointInfo` `setName` object aan te roepen en een tekenreekswaarde door te geven die de naam opgeeft.
   * Geef de service op waartoe het eindpunt behoort door de methode van het `CreateEndpointInfo` `setServiceId` object aan te roepen en een tekenreekswaarde door te geven die de servicenaam opgeeft.
   * Geef de bewerking op die wordt aangeroepen door de methode van het `CreateEndpointInfo` `setOperationName` object aan te roepen en geef een tekenreekswaarde door die de naam van de bewerking opgeeft. Geef voor SOAP- en EJB-eindpunten een jokerteken ( `*`) op, wat alle bewerkingen impliceert.

1. Maak een EJB-eindpunt.

   Maak het eindpunt door de methode van het `EndpointRegistryClient` object aan te roepen `createEndpoint` en het `CreateEndpointInfo` object door te geven. Deze methode retourneert een `Endpoint` object dat het nieuwe EJB-eindpunt vertegenwoordigt.

1. Laat het eindpunt toe.

   Schakel het eindpunt in door de methode enable van het `EndpointRegistryClient` object aan te roepen en het `Endpoint` object door te geven dat door de `createEndpoint` methode is geretourneerd.

**Zie ook**

[Overzicht van de stappen](programmatically-endpoints.md#summary-of-steps)

[QuickStart: Een EJB-eindpunt toevoegen met de Java API](/help/forms/developing/endpoint-registry-java-api-quick.md#quickstart-adding-an-ejb-endpoint-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## SOAP-eindpunten toevoegen {#adding-soap-endpoints}

U kunt een eindpunt van de ZEEP aan de dienst programmatically toevoegen door AEM Forms Java API te gebruiken. Door een eindpunt van de ZEEP toe te voegen, laat u een cliënttoepassing toe om de dienst aan te halen door de wijze van de ZEEP te gebruiken. Met andere woorden, wanneer u verbindingseigenschappen instelt die nodig zijn om AEM Forms aan te roepen, kunt u de SOAP-modus selecteren.

>[!NOTE]
>
>U kunt geen eindpunt van de ZEEP toevoegen door de Webdiensten te gebruiken.

>[!NOTE]
>
>Typisch, wordt een eindpunt van de ZEEP toegevoegd aan de dienst door gebrek, echter, kan een eindpunt van de ZEEP aan een proces worden toegevoegd dat programmatically wordt opgesteld of wanneer een eindpunt van de ZEEP werd verwijderd en opnieuw moet worden toegevoegd.

### Overzicht van de stappen {#summary_of_steps-1}

Om een eindpunt van de ZEEP aan de dienst toe te voegen, voer de volgende taken uit:

1. Inclusief projectbestanden.
1. Maak een `EndpointRegistryClient` object.
1. Stel de kenmerken voor het SOAP-eindpunt in.
1. Creeer een eindpunt van de ZEEP.
1. Laat het eindpunt toe.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u de proxybestanden opnemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-utilities.jar (vereist als AEM Forms worden geïmplementeerd op JBoss Application Server)
* jbossall-client.jar (vereist als AEM Forms worden geïmplementeerd op JBoss Application Server)

Deze JAR-bestanden zijn vereist om een SOAP-eindpunt te maken. Nochtans, vereist u toevoegingsJAR dossiers als u het eindpunt van de ZEEP gebruikt om de dienst aan te halen. Zie [Including AEM Forms Java library files](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)voor informatie over AEM Forms JAR-bestanden.

**Een EndpointRegistry-client-object maken**

Om een eindpunt van de ZEEP aan de dienst programmatically toe te voegen, moet u een `EndpointRegistryClient` voorwerp tot stand brengen.

**Kenmerken van SOAP-eindpunt instellen**

Om een eindpunt van de ZEEP aan de dienst toe te voegen, specificeer de volgende waarden:

* **Waarde** koppelings-id: Geeft het type eindpunt op dat moet worden gemaakt. Om een eindpunt van de ZEEP tot stand te brengen, specificeer `SOAP`.
* **Omschrijving**: Specificeert de eindpuntbeschrijving.
* **Naam**: Hiermee geeft u de eindpuntnaam op.
* **Service-id-waarde**: Specificeert de dienst waartot het eindpunt behoort.
* **Bewerkingsnaam**: Specificeert de naam van de verrichting die door het eindpunt te gebruiken wordt aangehaald. Wanneer het creëren van een eindpunt van de ZEEP, specificeer een vervangingskarakter ( `*`). Nochtans, als u een specifieke verrichting in tegenstelling tot het aanhalen van alle de dienstverrichtingen wilt specificeren, specificeer de naam van de verrichting in plaats van het gebruiken van het vervangingskarakter ( `*`).

**Een SOAP-eindpunt maken**

Nadat u de eigenschappen van het eindpunt van de ZEEP plaatst, kunt u een eindpunt van de ZEEP tot stand brengen.

**Het eindpunt inschakelen**

Nadat u een nieuw eindpunt creeert, moet u het toelaten. Wanneer het eindpunt wordt toegelaten, kan het worden gebruikt om de dienst aan te halen. Nadat u het eindpunt toelaat, kunt u het binnen beleidsconsole bekijken.

**Zie ook**

[Een SOAP-eindpunt toevoegen met de Java API](programmatically-endpoints.md#add-a-soap-endpoint-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Een SOAP-eindpunt toevoegen met de Java API {#add-a-soap-endpoint-using-the-java-api}

Voeg een eindpunt van de ZEEP aan de dienst toe door Java API te gebruiken:

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-livecycle-client.jar, op in het klassenpad van uw Java-project.

1. Creeer een voorwerp van de Cliënt EndpointRegistry.

   * Maak een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Maak een `EndpointRegistryClient` object door de constructor ervan te gebruiken en het `ServiceClientFactory` object door te geven.

1. Stel de kenmerken voor het SOAP-eindpunt in.

   * Maak een `CreateEndpointInfo` object met de constructor ervan.
   * Geef de waarde van de connector-id op door de methode van het `CreateEndpointInfo` object aan te roepen en de tekenreekswaarde door te geven `setConnectorId` `SOAP`.
   * Geef de beschrijving van het eindpunt op door de methode van het `CreateEndpointInfo` `setDescription` object aan te roepen en een tekenreekswaarde door te geven die het eindpunt beschrijft.
   * Geef de naam van het eindpunt op door de methode van het `CreateEndpointInfo` `setName` object aan te roepen en een tekenreekswaarde door te geven die de naam opgeeft.
   * Geef de service op waartoe het eindpunt behoort door de methode van het `CreateEndpointInfo` `setServiceId` object aan te roepen en een tekenreekswaarde door te geven die de servicenaam opgeeft.
   * Geef de bewerking op die wordt aangeroepen door de methode van het `CreateEndpointInfo` `setOperationName` object aan te roepen en een tekenreekswaarde door te geven die de naam van de bewerking aangeeft. Geef voor SOAP- en EJB-eindpunten een jokerteken ( `*`) op, wat alle bewerkingen impliceert.

1. Creeer een eindpunt van de ZEEP.

   Maak het eindpunt door de methode van het `EndpointRegistryClient` object aan te roepen `createEndpoint` en het `CreateEndpointInfo` object door te geven. Deze methode keert een `Endpoint` voorwerp terug dat het nieuwe eindpunt van de ZEEP vertegenwoordigt.

1. Laat het eindpunt toe.

   Schakel het eindpunt in door de methode Enable van het `EndpointRegistryClient` object aan te roepen en geef het `Endpoint` object door dat door de `createEndpoint` methode is geretourneerd.

**Zie ook**

[Overzicht van de stappen](programmatically-endpoints.md#summary-of-steps)

[QuickStart: Een SOAP-eindpunt toevoegen met de Java API](/help/forms/developing/endpoint-registry-java-api-quick.md#quickstart-adding-a-soap-endpoint-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Eindpunten van gecontroleerde mappen toevoegen {#adding-watched-folder-endpoints}

U kunt programmatically een Gecontroleerd eindpunt van de Omslag aan de dienst toevoegen door AEM Forms Java API te gebruiken. Als u een eindpunt van een gecontroleerde map toevoegt, kunnen gebruikers een bestand (zoals een PDF-bestand) in een map plaatsen. Wanneer het dossier in de omslag wordt geplaatst, wordt de gevormde dienst dan aangehaald en manipuleert het dossier. Nadat de service de opgegeven bewerking heeft uitgevoerd, wordt het gewijzigde bestand opgeslagen in een opgegeven uitvoermap. Een gecontroleerde map is geconfigureerd om te worden gescand met een vast interval of met een uitsnijdschema, zoals elke maandag, woensdag en vrijdag om 12.00 uur.

Voor het programmatically toevoegen van een Gecontroleerd eindpunt van de Omslag aan de dienst, overweeg het volgende kortstondige proces genoemd *EncryptDocument*. (Zie [Werken](/help/forms/developing/aem-forms-processes.md#understanding-aem-forms-processes)met AEM Forms begrijpen.)

![aw_aw_encryptdocumentprocess](assets/aw_aw_encryptdocumentprocess.png)

Dit proces accepteert een onbeveiligd PDF-document als een invoerwaarde en geeft het onbeveiligde PDF-document vervolgens door aan de `EncryptPDFUsingPassword` bewerking van de Coderingsservice. Het PDF-document wordt versleuteld met een wachtwoord en het PDF-document met een wachtwoord is de uitvoerwaarde van dit proces. De naam van de invoerwaarde (het onbeveiligde PDF-document) is `InDoc` en het gegevenstype is `com.adobe.idp.Document`. De naam van de uitvoerwaarde (het met een wachtwoord gecodeerde PDF-document) is `SecuredDoc` en het gegevenstype is `com.adobe.idp.Document`.

>[!NOTE]
>
>U kunt geen Gecontroleerd eindpunt van de Omslag toevoegen door de Webdiensten te gebruiken.

### Overzicht van de stappen {#summary_of_steps-2}

Voer de volgende taken uit om een eindpunt van een gecontroleerde map aan de service toe te voegen:

1. Inclusief projectbestanden.
1. Maak een `EndpointRegistryClient` object.
1. Attributen voor het eindpunt van gecontroleerde map instellen.
1. Geef configuratiewaarden op.
1. Definieer invoerparameterwaarden.
1. Definieer een uitvoerparameterwaarde.
1. Creeer een Gecontroleerd eindpunt van de Omslag.
1. Laat het eindpunt toe.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u de proxybestanden opnemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-utilities.jar (vereist als AEM Forms worden geïmplementeerd op JBoss Application Server)
* jbossall-client.jar (vereist als AEM Forms worden geïmplementeerd op JBoss Application Server)

Zie [Including AEM Forms Java library files](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)voor informatie over de locatie van deze JAR-bestanden.

**Een EndpointRegistry-client-object maken**

Als u programmatisch een eindpunt van een gecontroleerde map wilt toevoegen, moet u een `EndpointRegistryClient` object maken.

**Kenmerken voor het eindpunt van gecontroleerde mappen instellen**

Om een Gecontroleerd eindpunt van de Omslag voor de dienst tot stand te brengen, specificeer de volgende waarden:

* **Connector-id**: Geeft het type eindpunt op dat wordt gemaakt. Als u een eindpunt van een gecontroleerde map wilt maken, geeft u op `WatchedFolder`.
* **Omschrijving**: Specificeert de beschrijving van het eindpunt.
* **Naam**: Specificeert de naam van het eindpunt.
* **Service-id**: Specificeert de dienst waartot het eindpunt behoort. Bijvoorbeeld, om een Gecontroleerd eindpunt van de Omslag aan het proces toe te voegen dat in deze sectie wordt geïntroduceerd (een proces wordt de dienst wanneer geactiveerd gebruikend Workbench), specificeer `EncryptDocument`.
* **Bewerkingsnaam**: Specificeert de naam van de verrichting die door het eindpunt te gebruiken wordt aangehaald. Typisch, wanneer het creëren van een Gecontroleerd eindpunt van de Omslag voor de dienst die uit een proces voortkwam dat in Workbench wordt gecreeerd, is de naam van de verrichting `invoke`.

**Configuratiewaarden opgeven**

U moet configuratiewaarden voor een Gecontroleerd eindpunt van de Omslag specificeren wanneer programmatically het toevoegen van een Gecontroleerd eindpunt van de Omslag aan de dienst. Deze configuratiewaarden worden gespecificeerd door een beheerder als een Gecontroleerd eindpunt van de Omslag door beleidsconsole wordt toegevoegd te gebruiken.

De volgende lijst specificeert configuratiewaarden die wanneer programmatically het toevoegen van een Gecontroleerd eindpunt van de Omslag aan de dienst worden geplaatst:

* **URL**: Hier geeft u de locatie van de gecontroleerde map op. In een gegroepeerd milieu, moet deze waarde aan een gedeelde netwerkomslag richten die van elke computer in de cluster toegankelijk is.
* **asynchroon**: Identificeert het aanroepingstype als asynchroon of synchroon. De voorbijgaande en synchrone processen kunnen slechts synchroon worden aangehaald. De standaardwaarde is true. Asynchroon wordt aanbevolen.
* **cronExpression**: Wordt gebruikt door kwarts om de opiniepeiling van de invoermap te plannen. Zie [https://quartz.sourceforge.net/javadoc/org/quartz/CronTrigger.html](https://quartz.sourceforge.net/javadoc/org/quartz/CronTrigger.html)voor meer informatie over het configureren van de expressie voor uitsnijden.
* **purgeDuration**: Dit is een verplicht kenmerk. Bestanden en mappen in de resultaatmap worden gewist wanneer ze ouder zijn dan deze waarde. Deze waarde wordt gemeten in dagen. Dit kenmerk is handig om ervoor te zorgen dat de resultaatmap niet vol wordt. De waarde -1 dagen geeft aan dat u de resultatenmap nooit wilt verwijderen. De standaardwaarde is -1.
* **repeatInterval**: Het interval, in seconden, voor het scannen van de gecontroleerde map op invoer. Als vertraging niet is ingeschakeld, moet deze waarde langer zijn dan de tijd die nodig is om een gemiddelde taak te verwerken. anders kan het systeem overbelast raken . De standaardwaarde is 5.
* **repeatCount**: Het aantal keren dat een gecontroleerde map de map of map scant. De waarde -1 geeft aan dat een scanbewerking voor onbepaalde tijd wordt uitgevoerd. De standaardwaarde is -1.
* **throttleOn**: Hiermee beperkt u het aantal taken voor gecontroleerde mappen dat op een bepaald moment kan worden verwerkt. Het maximumaantal banen wordt bepaald door de batchSize waarde.
* **userName**: De gebruikersnaam die wordt gebruikt wanneer een doelservice wordt aangeroepen vanuit de gecontroleerde map. Deze waarde is verplicht. De standaardwaarde is SuperAdmin.
* **domainName**: Het domein van de gebruiker. Deze waarde is verplicht. De standaardwaarde is DefaultDom.
* **batchSize**: Het aantal bestanden of mappen dat per scan moet worden opgehaald. Gebruik deze waarde om overbelasting op het systeem te voorkomen; te veel bestanden tegelijk scannen kan tot gevolg hebben dat de toepassing vastloopt. De standaardwaarde is 2.
* **waitTime**: De tijd, in milliseconden, om te wachten alvorens een omslag of een dossier na verwezenlijking af te tasten. Als de wachttijd bijvoorbeeld 36.000.000 milliseconden (één uur) is en het bestand een minuut geleden is gemaakt, wordt dit bestand opgepakt nadat 59 minuten zijn verstreken. Dit kenmerk is handig om ervoor te zorgen dat een bestand of map volledig naar de invoermap wordt gekopieerd. Als u bijvoorbeeld een groot bestand hebt dat moet worden verwerkt en het downloaden van het bestand duurt tien minuten, stelt u de wachttijd in op 10&amp;ast;60 &amp;ast;1000 milliseconden. Met deze instelling voorkomt u dat de gecontroleerde map het bestand scant als het nog tien minuten niet heeft gewacht. De standaardwaarde is 0.
* **excludeFilePattern**: Het patroon dat in een gecontroleerde map wordt gebruikt om te bepalen welke bestanden en mappen moeten worden gescand en opgehaald. Bestanden of mappen met dit patroon worden niet gescand voor verwerking. Deze instelling is handig wanneer de invoer een map is die meerdere bestanden bevat. De inhoud van de map kan worden gekopieerd naar een map met een naam die wordt opgepakt door de gecontroleerde map. Met deze stap wordt voorkomen dat de gecontroleerde map een map opneemt die moet worden verwerkt voordat de map volledig is gekopieerd naar de invoermap. Als de waarde excludeFilePattern bijvoorbeeld is `data*`, worden niet alle bestanden en mappen opgehaald die overeenkomen met de waarde `data*` excludeFilePattern. Dit omvat bestanden en mappen met de naam `data1`, `data2`enzovoort. Bovendien kan het patroon met vervangingspatronen worden aangevuld om dossierpatronen te specificeren. De gecontroleerde omslag wijzigt de regelmatige uitdrukking om vervangingspatronen zoals `*.*` en `*.pdf`te steunen. Deze jokertekenpatronen worden niet ondersteund door reguliere expressies.
* **includeFilePattern**: Het patroon dat in de gecontroleerde map wordt gebruikt om te bepalen welke mappen en bestanden worden gescand en opgehaald. Als deze waarde bijvoorbeeld is, `*`worden alle overeenkomende bestanden en mappen `input*` opgepakt. Dit omvat bestanden en mappen met de naam `input1`, `input2`enzovoort. De standaardwaarde is `*`. Deze waarde geeft alle bestanden en mappen aan. Bovendien kan het patroon met vervangingspatronen worden aangevuld om dossierpatronen te specificeren. De gecontroleerde omslag wijzigt de regelmatige uitdrukking om vervangingspatronen zoals `*.*` en `*.pdf`te steunen. Deze jokertekenpatronen worden niet ondersteund door reguliere expressies. Deze waarde is verplicht.
* **resultFolderName**: De map waarin de opgeslagen resultaten worden opgeslagen. Deze locatie kan een absoluut of relatief mappad zijn. Als de resultaten niet in deze map worden weergegeven, controleert u de map met foutmeldingen. Alleen-lezen bestanden worden niet verwerkt en worden opgeslagen in de map met foutmeldingen. De standaardwaarde is `result/%Y/%M/%D/`. Dit is de resultatenmap in de controlemap.
* **preserveFolderName**: De locatie waar bestanden worden opgeslagen nadat bestanden zijn gescand en opgehaald. Deze locatie kan een absoluut, relatief of null-mappad zijn. De standaardwaarde is `preserve/%Y/%M/%D/`.
* **failureFolderName**: De map waarin bestanden met fouten worden opgeslagen. Deze locatie is altijd relatief ten opzichte van de gecontroleerde map. Alleen-lezen bestanden worden niet verwerkt en worden opgeslagen in de map met foutmeldingen. De standaardwaarde is `failure/%Y/%M/%D/`.
* **preserveOnFailed**: Invoerbestanden behouden als de bewerking niet op een service wordt uitgevoerd. De standaardwaarde is true.
* **overwriteDuplicateFilename**: Als deze optie is ingesteld op true, worden bestanden in de resultatenmap en de bewaarmap overschreven. Als deze optie is ingesteld op false, worden bestanden en mappen met een numeriek indexachtervoegsel gebruikt voor de naam. De standaardwaarde is false.

**Invoerparameterwaarden definiëren**

Wanneer u een eindpunt van een gecontroleerde map maakt, moet u parameterwaarden voor invoer definiëren. U moet dus de invoerwaarden beschrijven die worden doorgegeven aan de bewerking die wordt aangeroepen door de gecontroleerde map. Neem bijvoorbeeld het proces dat in dit onderwerp is geïntroduceerd. Er is één invoerwaarde met de naam `InDoc` en het gegevenstype is `com.adobe.idp.Document`. Wanneer u een eindpunt van een gecontroleerde map voor dit proces maakt (nadat een proces is geactiveerd, wordt het een service), moet u de waarde van de invoerparameter definiëren.

Als u parameterwaarden voor invoer wilt definiëren die vereist zijn voor het eindpunt van een gecontroleerde map, geeft u de volgende waarden op:

**Naam** invoerparameter: De naam van de invoerparameter. De naam van een inputwaarde wordt gespecificeerd in Workbench voor een proces. Als de inputwaarde tot een de dienstverrichting (de dienst behoort die geen proces is dat in Workbench wordt gecreeerd), wordt de inputnaam gespecificeerd in het component.xml- dossier. De naam van de invoerparameter voor het in deze sectie geïntroduceerde proces is bijvoorbeeld `InDoc`.

**Type** toewijzing: Gebruikt om de inputwaarden te vormen die worden vereist om de de dienstverrichting aan te halen. Er zijn twee typen toewijzingen:

* `Literal`: Het eindpunt van de Gecontroleerde Omslag gebruikt de waarde ingegaan op het gebied aangezien het wordt getoond. Alle basistypen van Java worden ondersteund. Als een API bijvoorbeeld invoer gebruikt zoals String, long, int en Boolean, wordt de tekenreeks omgezet in het juiste type en wordt de service aangeroepen.
* `Variable`: De ingevoerde waarde is een bestandspatroon waarmee de gecontroleerde map de invoer kan selecteren. Als u bijvoorbeeld Variabele selecteert voor het toewijzingstype en het invoerdocument moet een PDF-bestand zijn, kunt u de toewijzingswaarde opgeven. `*.pdf`

**Toewijzingswaarde**: Hiermee wordt de waarde van het toewijzingstype opgegeven. Als u bijvoorbeeld een `Variable` `*.pdf` toewijzingstype selecteert, kunt u het bestandspatroon opgeven.

**Gegevenstype**: Hiermee wordt het gegevenstype van de invoerwaarde(n) opgegeven. Het gegevenstype van de invoerwaarde van het proces dat in deze sectie wordt geïntroduceerd, is bijvoorbeeld `com.adobe.idp.Document`.

**Een uitvoerparameterwaarde definiëren**

Wanneer u een eindpunt van een gecontroleerde map maakt, moet u een uitvoerparameterwaarde definiëren. Namelijk moet u de outputwaarde beschrijven die door de dienst is teruggekeerd die door het Gecontroleerde eindpunt van de Omslag wordt aangehaald. Neem bijvoorbeeld het proces dat in dit onderwerp is geïntroduceerd. Het heeft een genoemde outputwaarde `SecuredDoc` en zijn gegevenstype is `com.adobe.idp.Document`. Wanneer het creëren van een Gecontroleerd eindpunt van de Omslag voor dit proces (nadat een proces wordt geactiveerd, wordt het een dienst), moet u de waarde van de outputparameter bepalen.

Geef de volgende waarden op om een uitvoerparameterwaarde te definiëren die vereist is voor het eindpunt van een gecontroleerde map:

**Naam uitvoerparameter**: De naam van de uitvoerparameter. De naam van een waarde voor de procesuitvoer wordt opgegeven in Workbench. Als de outputwaarde tot een de dienstverrichting (de dienst behoort die geen proces is dat in Workbench wordt gecreeerd), wordt de outputnaam gespecificeerd in het component.xml- dossier. De naam van de uitvoerparameter voor het proces dat in deze sectie wordt geïntroduceerd, is bijvoorbeeld `SecuredDoc`.

**Type** toewijzing: Gebruikt om de output van de dienst en de verrichting te vormen. De volgende opties zijn beschikbaar:

* Als de service één object (één document) retourneert, is het patroon `%F.pdf` en is de bronbestemming sourcefilename.pdf. Het in deze sectie geïntroduceerde proces retourneert bijvoorbeeld één document. Hierdoor kan het toewijzingstype worden gedefinieerd als `%F.pdf` ( `%F` gebruik de opgegeven bestandsnaam). Met het patroon wordt de extensie van het invoerdocument `%E` opgegeven.
* Als de dienst een lijst terugkeert, is het patroon, `Result\%F\`en de bronbestemming is Result\sourcefilename\source1 (output 1) en Result\sourcefilename\source2 (output 2).
* Als de dienst een kaart terugkeert, is het patroon, `Result\%F\`en de bronbestemming is Result\sourcefilename\file1 and Result\sourcefilename\file2. Als de kaart meer dan één voorwerp heeft, is het patroon `Result\%F.pdf` en de bronbestemming is Result\sourcefilename1.pdf (output 1), Result\sourcefilenam2.pdf (output 2), etc.

**Gegevenstype**: Hiermee wordt het gegevenstype van de geretourneerde waarde opgegeven. Het gegevenstype van de geretourneerde waarde van het proces dat in deze sectie wordt geïntroduceerd, is bijvoorbeeld `com.adobe.idp.Document`.

**Een eindpunt van een gecontroleerde map maken**

Nadat u de attributen van het eindpunt, configuratiewaarden, en de waarden van input en outputparameter plaatst, moet u het Gecontroleerde eindpunt van de Omslag tot stand brengen.

**Het eindpunt inschakelen**

Nadat u een Gecontroleerd eindpunt van de Omslag creeert, moet u het toelaten. Wanneer het eindpunt wordt toegelaten, kan het worden gebruikt om de dienst aan te halen. Nadat u het eindpunt toelaat, kunt u het binnen beleidsconsole bekijken.

**Zie ook**

[Het eindpunt van een gecontroleerde map toevoegen met de Java API](programmatically-endpoints.md#add-a-watched-folder-endpoint-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Het eindpunt van een gecontroleerde map toevoegen met de Java API {#add-a-watched-folder-endpoint-using-the-java-api}

Voeg een Gecontroleerd eindpunt van de Omslag toe door AEM Forms Java API te gebruiken:

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-livecycle-client.jar, op in het klassenpad van uw Java-project.

1. Creeer een voorwerp van de Cliënt EndpointRegistry.

   * Maak een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Maak een `EndpointRegistryClient` object door de constructor ervan te gebruiken en het `ServiceClientFactory` object door te geven.

1. Attributen voor het eindpunt van gecontroleerde map instellen.

   * Maak een `CreateEndpointInfo` object met de constructor ervan.
   * Geef de waarde van de connector-id op door de methode van het `CreateEndpointInfo` object aan te roepen en de tekenreekswaarde door te geven `setConnectorId` `WatchedFolder`.
   * Geef de beschrijving van het eindpunt op door de methode van het `CreateEndpointInfo` `setDescription` object aan te roepen en een tekenreekswaarde door te geven die het eindpunt beschrijft.
   * Geef de naam van het eindpunt op door de methode van het `CreateEndpointInfo` `setName` object aan te roepen en een tekenreekswaarde door te geven die de naam opgeeft.
   * Geef de service op waartoe het eindpunt behoort door de methode van het `CreateEndpointInfo` `setServiceId` object aan te roepen en een tekenreekswaarde door te geven die de servicenaam opgeeft.
   * Geef de bewerking op die wordt aangeroepen door de methode van het `CreateEndpointInfo` `setOperationName` object aan te roepen en een tekenreekswaarde door te geven die de naam van de bewerking aangeeft. Typisch, wanneer het creëren van een Gecontroleerd eindpunt van de Omslag voor de dienst die uit een proces voortkwam dat in Workbench wordt gecreeerd, wordt de naam van de verrichting aangeroepen.

1. Geef configuratiewaarden op.

   Voor elke configuratiewaarde die voor het Gecontroleerde eindpunt van de Omslag moet worden geplaatst, moet u de `CreateEndpointInfo` methode van de `setConfigParameterAsText` objecten aanhalen. Als u bijvoorbeeld de `url` configuratiewaarde wilt instellen, roept u de `CreateEndpointInfo` methode van het `setConfigParameterAsText` object op en geeft u de volgende tekenreekswaarden door:

   * Een tekenreekswaarde die de naam van de configuratiewaarde opgeeft. Geef bij het instellen van de `url` configuratiewaarde op `url`.
   * Een tekenreekswaarde die de waarde van de configuratiewaarde opgeeft. Geef bij het instellen van de `url` configuratiewaarde de locatie van de gecontroleerde map op.

   >[!NOTE]
   >
   >Als u alle configuratiewaarden wilt zien die zijn ingesteld voor de EncryptDocument-service, raadpleegt u het Java-codevoorbeeld in [QuickStart: Het toevoegen van een Gecontroleerd Punt van de Omslag gebruikend Java API](/help/forms/developing/endpoint-registry-java-api-quick.md#quickstart-adding-a-watched-folder-endpoint-using-the-java-api).

1. Definieer invoerparameterwaarden.

   Definieer een invoerparameterwaarde door de methode van het `CreateEndpointInfo` `setInputParameterMapping` object aan te roepen en de volgende waarden door te geven:

   * Een tekenreekswaarde die de naam van de invoerparameter opgeeft. De naam van de invoerparameter voor de EncryptDocument-service is bijvoorbeeld `InDoc`.
   * Een tekenreekswaarde die het gegevenstype van de invoerparameter opgeeft. Het gegevenstype van de `InDoc` invoerparameter is bijvoorbeeld `com.adobe.idp.Document`.
   * Een tekenreekswaarde die het toewijzingstype aangeeft. U kunt bijvoorbeeld opgeven `variable`.
   * Een tekenreekswaarde die de waarde van het toewijzingstype opgeeft. U kunt bijvoorbeeld &amp;ast;.pdf opgeven als bestandspatroon.

   >[!NOTE]
   >
   >Roep de `setInputParameterMapping` methode aan voor elke invoerparameterwaarde die moet worden gedefinieerd. Omdat het EncryptDocument-proces slechts één invoerparameter heeft, moet u deze methode eenmaal aanroepen.

1. Definieer een uitvoerparameterwaarde.

   Definieer een uitvoerparameterwaarde door de methode van het `CreateEndpointInfo` `setOutputParameterMapping` object aan te roepen en de volgende waarden door te geven:

   * Een tekenreekswaarde die de naam van de uitvoerparameter opgeeft. Bijvoorbeeld, is de naam van de outputparameter voor de dienst EncryptDocument `SecuredDoc`.
   * Een tekenreekswaarde die het gegevenstype van de uitvoerparameter opgeeft. Het gegevenstype van de `SecuredDoc` uitvoerparameter is bijvoorbeeld `com.adobe.idp.Document`.
   * Een tekenreekswaarde die het toewijzingstype aangeeft. U kunt bijvoorbeeld opgeven `%F.pdf`.

1. Creeer een Gecontroleerd eindpunt van de Omslag.

   Maak het eindpunt door de methode van het `EndpointRegistryClient` object aan te roepen `createEndpoint` en het `CreateEndpointInfo` object door te geven. Deze methode retourneert een `Endpoint` object dat het eindpunt van de gecontroleerde map vertegenwoordigt.

1. Laat het eindpunt toe.

   Schakel het eindpunt in door de `EndpointRegistryClient` methode van het `enable` object aan te roepen en het `Endpoint` object door te geven dat door de `createEndpoint` methode is geretourneerd.

**Zie ook**

[Overzicht van de stappen](programmatically-endpoints.md#summary-of-steps)

[QuickStart: Een eindpunt van een gecontroleerde map toevoegen met de Java API](/help/forms/developing/endpoint-registry-java-api-quick.md#quickstart-adding-a-watched-folder-endpoint-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Configuratiewaarden van gecontroleerde map, constant bestand {#watched-folder-configuration-values-constant-file}

De [QuickStart: Als u een eindpunt van een gecontroleerde map toevoegt met de Java API](/help/forms/developing/endpoint-registry-java-api-quick.md#quickstart-adding-a-watched-folder-endpoint-using-the-java-api) , wordt een constant bestand gebruikt dat deel moet uitmaken van uw Java-project om de snelle start te kunnen compileren. Dit constante dossier vertegenwoordigt configuratiewaarden die moeten worden geplaatst wanneer het toevoegen van een Gecontroleerd eindpunt van de Omslag. De volgende Java-code vertegenwoordigt het constante bestand.

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

Voor het programmatically toevoegen van een E-maileindpunt aan de dienst, overweeg het volgende kortstondige proces genoemd *MyApplication \ EncryptDocument*. Voor informatie over kortstondige processen, zie het [Begrijpen van de Processen](/help/forms/developing/aem-forms-processes.md#understanding-aem-forms-processes)van AEM Forms.

![ae_ae_encryptdocumentprocess](assets/ae_ae_encryptdocumentprocess.png)

Dit proces accepteert een onbeveiligd PDF-document als een invoerwaarde en geeft het onbeveiligde PDF-document vervolgens door aan de `EncryptPDFUsingPassword` bewerking van de Coderingsservice. Met dit proces wordt het PDF-document versleuteld met een wachtwoord en wordt het met een wachtwoord gecodeerde PDF-document als de uitvoerwaarde geretourneerd. De naam van de invoerwaarde (het onbeveiligde PDF-document) is `InDoc` en het gegevenstype is `com.adobe.idp.Document`. De naam van de uitvoerwaarde (het met een wachtwoord gecodeerde PDF-document) is `SecuredDoc` en het gegevenstype is `com.adobe.idp.Document`.

>[!NOTE]
>
>U kunt geen eindpunt E-mail toevoegen door de Webdiensten te gebruiken.

### Overzicht van de stappen {#summary_of_steps-3}

Om een E-maileindpunt aan de dienst toe te voegen, voer de volgende taken uit:

1. Inclusief projectbestanden.
1. Maak een `EndpointRegistryClient` object.
1. Emaileindpuntkenmerken instellen.
1. Geef configuratiewaarden op.
1. Definieer invoerparameterwaarden.
1. Definieer een uitvoerparameterwaarde.
1. Maak het eindpunt E-mail.
1. Laat het eindpunt toe.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u de proxybestanden opnemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-utilities.jar (vereist als AEM Forms worden geïmplementeerd op JBoss Application Server)
* jbossall-client.jar (vereist als AEM Forms worden geïmplementeerd op JBoss Application Server)

Zie [Including AEM Forms Java library files](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)voor informatie over de locatie van deze JAR-bestanden.

**Een EndpointRegistry-client-object maken**

Voordat u een e-maileindpunt kunt toevoegen, moet u eerst een `EndpointRegistryClient` object maken.

**Kenmerken voor e-maileindpunten instellen**

Om een E-maileindpunt voor de dienst tot stand te brengen, specificeer de volgende waarden:

* **Waarde** koppelings-id: Geeft het type eindpunt op dat wordt gemaakt. Om een E-maileindpunt tot stand te brengen, specificeer `Email`.
* **Omschrijving**: Specificeert een beschrijving voor het eindpunt.
* **Naam**: Specificeert de naam van het eindpunt.
* **Service-id-waarde**: Specificeert de dienst waartot het eindpunt behoort. Bijvoorbeeld, om een E-maileindpunt aan het proces toe te voegen dat in deze sectie wordt geïntroduceerd (een proces wordt de dienst wanneer geactiveerd gebruikend Workbench), specificeer `EncryptDocument`.
* **Bewerkingsnaam**: Specificeert de naam van de verrichting die door het eindpunt te gebruiken wordt aangehaald. Typisch, wanneer het creëren van een E-mail eindpunt voor de dienst die van een proces voortkwam dat in Workbench wordt gecreeerd, is de naam van de verrichting `invoke`.

**Configuratiewaarden opgeven**

U moet configuratiewaarden voor een E-mail eindpunt specificeren wanneer programmatically het toevoegen van een E-mail eindpunt aan de dienst. Deze configuratiewaarden worden gespecificeerd door een beheerder als een E-maileindpunt gebruikend beleidsconsole wordt toegevoegd.

>[!NOTE]
>
>De e-mailrekening die wordt gecontroleerd is een speciale rekening die voor het E-maileindpunt slechts wordt gebruikt. Dit account is geen gewoon e-mailaccount voor gebruikers. Een e-mailaccount van een normale gebruiker mag niet worden geconfigureerd als de account die de e-mailprovider gebruikt, omdat de e-mailprovider e-mailberichten verwijdert uit het Postvak IN nadat deze zijn voltooid met de berichten.

De volgende configuratiewaarden worden geplaatst wanneer programmatically het toevoegen van een E-maileindpunt aan de dienst:

* **cronExpression**: Een uitsnede als de e-mail moet worden gepland door een uitsnijduitdrukking te gebruiken.
* **repeatCount**: Aantal tijden het e-maileindpunt scant de omslag of de folder. De waarde -1 geeft aan dat een scanbewerking voor onbepaalde tijd wordt uitgevoerd. De standaardwaarde is -1.
* **repeatInterval**: De scansnelheid in seconden die de ontvanger gebruikt om te controleren op inkomende e-mail. De standaardwaarde is 10.
* **startDelay**: De tijd om te wachten om na de planner begint te aftasten. De standaardtijd is 0.
* **batchSize**: Het aantal e-mailberichten dat de ontvanger verwerkt per scan voor optimale prestaties. De waarde -1 geeft alle e-mails aan. De standaardwaarde is 2.
* **userName**: De gebruikersnaam die wordt gebruikt wanneer een doelservice wordt aangeroepen via e-mail. De standaardwaarde is `SuperAdmin`.
* **domainName**: Een verplichte configuratiewaarde. De standaardwaarde is `DefaultDom`.
* **domainPattern**: Geeft de domeinpatronen aan van binnenkomende e-mailberichten die de provider accepteert. Als u bijvoorbeeld alleen e-mail van adobe.com `adobe.com` gebruikt, wordt e-mail van andere domeinen genegeerd.
* **filePattern**: Hiermee worden de inkomende patronen voor bestandsbijlagen opgegeven die de provider accepteert. Hiertoe behoren bestanden met specifieke bestandsextensies (&amp;ast;.dat, &amp;ast;.xml), bestanden met specifieke namen (gegevens) en bestanden met samengestelde expressies in de naam en extensie (&amp;ast;..[dD][aA]&#39;port&#39;). De standaardwaarde is `*`.
* **receivingSuccessfulJob**: Een e-mailadres waarnaar berichten worden verzonden om aan te geven dat taken zijn gelukt. Standaard wordt altijd een bericht met een geslaagde taak naar de afzender verzonden. Als u typt, worden de e-mailresultaten verzonden naar de afzender. `sender` Er worden maximaal 100 ontvangers ondersteund. Geef extra ontvangers op met e-mailadressen, die elk worden gescheiden door een komma. Laat deze waarde leeg als u deze optie wilt uitschakelen. In sommige gevallen wilt u wellicht een proces activeren en geen e-mailmelding van het resultaat. De standaardwaarde is `sender`.
* **receivingFailedJob**: Een e-mailadres waarnaar berichten worden verzonden om mislukte taken aan te geven. Standaard wordt een mislukte taakbericht altijd naar de afzender verzonden. Als u typt, worden de e-mailresultaten verzonden naar de afzender. `sender` Er worden maximaal 100 ontvangers ondersteund. Geef extra ontvangers op met e-mailadressen, die elk worden gescheiden door een komma. Laat deze waarde leeg als u deze optie wilt uitschakelen. De standaardwaarde is `sender`.
* **inboxHost**: De hostnaam of het IP-adres in het Postvak IN van de e-mailprovider die moet worden gescand.
* **inboxPort**: De poort die de e-mailserver gebruikt. De standaardwaarde voor POP3 is 110 en de standaardwaarde voor IMAP is 143. Als SSL wordt toegelaten, is de standaardwaarde voor POP3 995 en de standaardwaarde voor IMAP is 993.
* **inboxProtocol**: Het e-mailprotocol voor het e-maileindpunt dat moet worden gebruikt om inbox te scannen. De opties zijn `IMAP` of `POP3`. De postserver van de inbox gastheer moet deze protocollen steunen.
* **inboxTimeOut**: De time-out (in seconden) die de e-mailprovider nodig heeft om te wachten op reacties in het Postvak IN. De standaardwaarde is 60.
* **inboxUser**: De gebruikersnaam die is vereist om u aan te melden bij de e-mailaccount. Afhankelijk van de e-mailserver en configuratie is dit mogelijk alleen het gedeelte met de gebruikersnaam van de e-mail of het volledige e-mailadres.
* **inboxPassword**: Het wachtwoord voor de inbox-gebruiker.
* **inboxSSLEnabled**: Stel deze waarde in om de e-mailprovider te dwingen SSL te gebruiken bij het verzenden van berichten over resultaten of fouten. Zorg ervoor dat de IMAP- of POP3-host SSL ondersteunt.
* **smtpHost**: De hostnaam van de mailserver waarnaar de e-mailprovider resultaten en foutberichten verzendt.
* **smtpPort**: De standaardwaarde voor de haven SMTP is 25.
* **smtpUser**: De gebruikersaccount voor de e-mailprovider die moet worden gebruikt wanneer deze e-mailmeldingen met resultaten en fouten verzendt.
* **smtpPassword**: Het wachtwoord voor de SMTP-account. Voor sommige mailservers is geen SMTP-wachtwoord vereist.
* **charSet**: De tekenset die door het e-mailprovider wordt gebruikt. De standaardwaarde is `UTF-8`.
* **smtpSSLEnabled**: Stel deze waarde in om de e-mailprovider te dwingen SSL te gebruiken bij het verzenden van berichten over resultaten of fouten. Zorg ervoor dat de SMTP-host SSL ondersteunt.
* **failedJobFolder**: Specificeert een folder waarin om resultaten op te slaan wanneer de SMTP postserver niet operationeel is.
* **asynchroon**: Wanneer deze optie is ingesteld op synchroon, worden alle invoerdocumenten verwerkt en wordt één reactie geretourneerd. Wanneer ingesteld op asynchroon, wordt een reactie verzonden voor elk invoerdocument dat wordt verwerkt. Bijvoorbeeld, wordt een E-maileindpunt gecreeerd voor het proces dat in dit onderwerp wordt geïntroduceerd, en een e-mailbericht wordt verzonden naar inbox van het eindpunt dat veelvoudige onbeveiligde PDF documenten bevat. Wanneer alle PDF-documenten met een wachtwoord zijn versleuteld en als het eindpunt synchroon is geconfigureerd, wordt één e-mailbericht met reacties verzonden met alle beveiligde PDF-documenten als bijlage. Als het eindpunt asynchroon is geconfigureerd, wordt voor elk beveiligd PDF-document een afzonderlijk e-mailantwoordbericht verzonden. Elk e-mailbericht bevat één PDF-document als bijlage. De standaardwaarde is asynchroon.

**Invoerparameterwaarden definiëren**

Wanneer u een e-maileindpunt maakt, moet u parameterwaarden voor invoer definiëren. Namelijk moet u de inputwaarden beschrijven die tot de verrichting worden overgegaan die door het E-maileindpunt wordt aangehaald. Neem bijvoorbeeld het proces dat in dit onderwerp is geïntroduceerd. Er is één invoerwaarde met de naam `InDoc` en het gegevenstype is `com.adobe.idp.Document`. Wanneer het creëren van een E-mail eindpunt voor dit proces (nadat een proces wordt geactiveerd, wordt het de dienst), moet u de waarde van de inputparameter bepalen.

Als u parameterwaarden voor invoer wilt definiëren die vereist zijn voor een e-maileindpunt, geeft u de volgende waarden op:

**Naam** invoerparameter: De naam van de invoerparameter. De naam van een inputwaarde wordt gespecificeerd in Workbench voor een proces. Als de invoerwaarde bij een servicebewerking hoort (een Forms-service die geen proces is dat in Workbench is gemaakt), wordt de invoernaam opgegeven in het bestand component.xml. De naam van de invoerparameter voor het in deze sectie geïntroduceerde proces is bijvoorbeeld `InDoc`.

**Type** toewijzing: Gebruikt om de inputwaarden te vormen die worden vereist om de de dienstverrichting aan te halen. Er zijn twee soorten toewijzingstypen:

* `Literal`: Het eindpunt E-mail gebruikt de waarde ingegaan in het gebied aangezien het wordt getoond. Alle basistypen van Java worden ondersteund. Als een API bijvoorbeeld invoer gebruikt zoals String, long, int en Boolean, wordt de tekenreeks omgezet in het juiste type en wordt de service aangeroepen.
* `Variable`: De ingevoerde waarde is een bestandspatroon waarmee het e-maileindpunt de invoer kiest. Als u bijvoorbeeld Variabele selecteert voor het toewijzingstype en het invoerdocument moet een PDF-bestand zijn, kunt u de toewijzingswaarde opgeven. `*.pdf`

**Toewijzingswaarde**: Hiermee wordt de waarde van het toewijzingstype opgegeven. Als u bijvoorbeeld een toewijzingstype Variabele selecteert, kunt u het bestandspatroon opgeven. `*.pdf`

**Gegevenstype**: Hiermee geeft u het gegevenstype van de invoerwaarden op. Het gegevenstype van de invoerwaarde van het proces dat in deze sectie wordt geïntroduceerd, is bijvoorbeeld com.adobe.idp.Document.

**Een uitvoerparameterwaarde definiëren**

Wanneer u een e-maileindpunt maakt, moet u een uitvoerparameterwaarde definiëren. Namelijk moet u de outputwaarde beschrijven die door de dienst is teruggekeerd die door het E-maileindpunt wordt aangehaald. Neem bijvoorbeeld het proces dat in dit onderwerp is geïntroduceerd. Het heeft een genoemde outputwaarde `SecuredDoc` en zijn gegevenstype is `com.adobe.idp.Document`. Wanneer het creëren van een E-mail eindpunt voor dit proces (nadat een proces wordt geactiveerd, wordt het de dienst), moet u de waarde van de outputparameter bepalen.

Als u een uitvoerparameterwaarde wilt definiëren die voor een e-maileindpunt is vereist, geeft u de volgende waarden op:

**Naam uitvoerparameter**: De naam van de uitvoerparameter. De naam van een waarde voor de procesuitvoer wordt opgegeven in Workbench. Als de outputwaarde tot een de dienstverrichting (de dienst behoort die geen proces is dat in Workbench wordt gecreeerd), wordt de outputnaam gespecificeerd in het component.xml- dossier. De naam van de uitvoerparameter voor het proces dat in deze sectie wordt geïntroduceerd, is bijvoorbeeld `SecuredDoc`.

**Type** toewijzing: Gebruikt om de output van de dienst en de verrichting te vormen. De volgende opties zijn beschikbaar:

* Als de service één object (één document) retourneert, is het patroon `%F.pdf` en is de bronbestemming sourcefilename.pdf. Het in deze sectie geïntroduceerde proces retourneert bijvoorbeeld één document. Hierdoor kan het toewijzingstype worden gedefinieerd als `%F.pdf` ( `%F` gebruik de opgegeven bestandsnaam). Met het patroon wordt de extensie van het invoerdocument `%E` opgegeven.
* Als de dienst een lijst terugkeert, is het patroon, `Result\%F\`en de bronbestemming is Result\sourcefilename\source1 (output 1) en Result\sourcefilename\source2 (output 2).
* Als de dienst een kaart terugkeert, is het patroon, `Result\%F\`en de bronbestemming is Result\sourcefilename\file1 and Result\sourcefilename\file2. Als de kaart meer dan één voorwerp heeft, is het patroon `Result\%F.pdf` en de bronbestemming is Result\sourcefilename1.pdf (output 1), Result\sourcefilenam2.pdf (output 2), etc.

**Gegevenstype**: Hiermee wordt het gegevenstype van de geretourneerde waarde opgegeven. Het gegevenstype van de geretourneerde waarde van het proces dat in deze sectie wordt geïntroduceerd, is bijvoorbeeld `com.adobe.idp.Document`.

**Het e-maileindpunt maken**

Nadat u de kenmerken en configuratiewaarden van het e-maileindpunt hebt ingesteld en invoer- en uitvoerparameters hebt gedefinieerd, moet u het eindpunt E-mail maken.

**Het eindpunt inschakelen**

Nadat u een eindpunt E-mail creeert, moet u het toelaten. Wanneer het eindpunt wordt toegelaten, kan het worden gebruikt om de dienst aan te halen. Nadat u het eindpunt toelaat, kunt u het binnen beleidsconsole bekijken.

**Zie ook**

[Een e-maileindpunt toevoegen met de Java API](programmatically-endpoints.md#add-an-email-endpoint-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Een e-maileindpunt toevoegen met de Java API {#add-an-email-endpoint-using-the-java-api}

Voeg een eindpunt E-mail toe door Java API te gebruiken:

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-livecycle-client.jar, op in het klassenpad van uw Java-project.

1. Creeer een voorwerp van de Cliënt EndpointRegistry.

   * Maak een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Maak een `EndpointRegistryClient` object door de constructor ervan te gebruiken en het `ServiceClientFactory` object door te geven.

1. Emaileindpuntkenmerken instellen.

   * Maak een `CreateEndpointInfo` object met de constructor ervan.
   * Geef de waarde van de connector-id op door de methode van het `CreateEndpointInfo` object aan te roepen en de tekenreekswaarde door te geven `setConnectorId` `Email`.
   * Geef de beschrijving van het eindpunt op door de methode van het `CreateEndpointInfo` `setDescription` object aan te roepen en een tekenreekswaarde door te geven die het eindpunt beschrijft.
   * Geef de naam van het eindpunt op door de methode van het `CreateEndpointInfo` `setName` object aan te roepen en een tekenreekswaarde door te geven die de naam opgeeft.
   * Geef de service op waartoe het eindpunt behoort door de methode van het `CreateEndpointInfo` `setServiceId` object aan te roepen en een tekenreekswaarde door te geven die de servicenaam opgeeft.
   * Geef de bewerking op die wordt aangeroepen door de methode van het `CreateEndpointInfo` `setOperationName` object aan te roepen en een tekenreekswaarde door te geven die de naam van de bewerking aangeeft. Typisch, wanneer het creëren van een E-mail eindpunt voor de dienst die van een proces voortkwam dat in Workbench wordt gecreeerd, wordt de naam van de verrichting gefactureerd.

1. Geef configuratiewaarden op.

   Voor elke configuratiewaarde die voor het e-maileindpunt moet worden ingesteld, moet u de `CreateEndpointInfo` methode van het `setConfigParameterAsText` object aanroepen. Als u bijvoorbeeld de `smtpHost` configuratiewaarde wilt instellen, roept u de `CreateEndpointInfo` methode van het `setConfigParameterAsText` object op en geeft u de volgende waarden door:

   * Een tekenreekswaarde die de naam van de configuratiewaarde opgeeft. Geef bij het instellen van de `smtpHost` configuratiewaarde op `smtpHost`.
   * Een tekenreekswaarde die de waarde van de configuratiewaarde opgeeft. Wanneer het plaatsen van de `smtpHost` configuratiewaarde, specificeer een koordwaarde die de naam van de server SMTP specificeert.

   >[!NOTE]
   >
   >Om alle configuratiewaarden te zien die voor de dienst EncryptDocument worden geplaatst die in deze sectie wordt geïntroduceerd, zie het de codevoorbeeld van Java dat bij [QuickStart wordt gevestigd: Een e-maileindpunt toevoegen met de Java API](/help/forms/developing/endpoint-registry-java-api-quick.md#quickstart-adding-an-email-endpoint-using-the-java-api).

1. Definieer invoerparameterwaarden.

   Definieer een invoerparameterwaarde door de methode van het `CreateEndpointInfo` `setInputParameterMapping` object aan te roepen en de volgende waarden door te geven:

   * Een tekenreekswaarde die de naam van de invoerparameter opgeeft. De naam van de invoerparameter voor de EncryptDocument-service is bijvoorbeeld `InDoc`.
   * Een tekenreekswaarde die het gegevenstype van de invoerparameter opgeeft. Het gegevenstype van de `InDoc` invoerparameter is bijvoorbeeld `com.adobe.idp.Document`.
   * Een tekenreekswaarde die het toewijzingstype aangeeft. U kunt bijvoorbeeld opgeven `variable`.
   * Een tekenreekswaarde die de waarde van het toewijzingstype opgeeft. U kunt bijvoorbeeld &amp;ast;.pdf opgeven als bestandspatroon.

   >[!NOTE]
   >
   >Roep de `setInputParameterMapping` methode aan voor elke invoerparameterwaarde die moet worden gedefinieerd. Omdat het EncryptDocument-proces slechts één invoerparameter heeft, moet u deze methode eenmaal aanroepen.

1. Definieer een uitvoerparameterwaarde.

   Definieer een uitvoerparameterwaarde door de methode van het `CreateEndpointInfo` `setOutputParameterMapping` object aan te roepen en de volgende waarden door te geven:

   * Een tekenreekswaarde die de naam van de uitvoerparameter opgeeft. Bijvoorbeeld, is de naam van de outputparameter voor de dienst EncryptDocument `SecuredDoc`.
   * Een tekenreekswaarde die het gegevenstype van de uitvoerparameter opgeeft. Het gegevenstype van de `SecuredDoc` uitvoerparameter is bijvoorbeeld `com.adobe.idp.Document`.
   * Een tekenreekswaarde die het toewijzingstype aangeeft. U kunt bijvoorbeeld opgeven `%F.pdf`.

1. Maak het eindpunt E-mail.

   Maak het eindpunt door de methode van het `EndpointRegistryClient` object aan te roepen `createEndpoint` en het `CreateEndpointInfo` object door te geven. Deze methode retourneert een `Endpoint` object dat het eindpunt E-mail vertegenwoordigt.

1. Laat het eindpunt toe.

   Schakel het eindpunt in door de `EndpointRegistryClient` methode van het `enable` object aan te roepen en het `Endpoint` object door te geven dat door de `createEndpoint` methode is geretourneerd.

**Zie ook**

[Overzicht van de stappen](programmatically-endpoints.md#summary-of-steps)

[QuickStart: Een eindpunt van een gecontroleerde map toevoegen met de Java API](/help/forms/developing/endpoint-registry-java-api-quick.md#quickstart-adding-a-watched-folder-endpoint-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Constante bestand voor waarden van e-mailconfiguratie {#email-configuration-values-constant-file}

De [QuickStart: Als u een e-maileindpunt toevoegt met de Java API](/help/forms/developing/endpoint-registry-java-api-quick.md#quickstart-adding-an-email-endpoint-using-the-java-api) , wordt een constant bestand gebruikt dat deel moet uitmaken van uw Java-project om de snelle start te kunnen compileren. Dit constante dossier vertegenwoordigt configuratiewaarden die moeten worden geplaatst wanneer het toevoegen van een e-maileindpunt. De volgende Java-code vertegenwoordigt het constante bestand.

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

U kunt programmatically een Remoting eindpunt aan de dienst toevoegen door AEM Forms Java API te gebruiken. Door een Remoting eindpunt toe te voegen, laat u een Flex toepassing toe om de dienst aan te halen door remoting te gebruiken. (Zie AEM Forms [aanroepen met (Vervangen voor AEM-formulieren) AEM Forms verwijderen](/help/forms/developing/invoking-aem-forms-using-remoting.md#invoking-aem-forms-using-remoting).)

Voor programmatically het toevoegen van een Remoting eindpunt aan de dienst, overweeg het volgende kortstondige proces genoemd *EncryptDocument*.

![ar_ar_encryptdocumentprocess](assets/ar_ar_encryptdocumentprocess.png)

Dit proces accepteert een onbeveiligd PDF-document als een invoerwaarde en geeft het onbeveiligde PDF-document vervolgens door aan de `EncryptPDFUsingPassword` bewerking van de Coderingsservice. Het PDF-document wordt versleuteld met een wachtwoord en het PDF-document met een wachtwoord is de uitvoerwaarde van dit proces. De naam van de invoerwaarde (het onbeveiligde PDF-document) is `InDoc` en het gegevenstype is `com.adobe.idp.Document`. De naam van de uitvoerwaarde (het met een wachtwoord gecodeerde PDF-document) is `SecuredDoc` en het gegevenstype is `com.adobe.idp.Document`.

Om aan te tonen hoe te om een Remoting eindpunt aan de dienst toe te voegen, voegt deze sectie een Remoting eindpunt aan de dienst genoemd EncryptDocument toe.

>[!NOTE]
>
>U kunt geen eindpunt Remoting toevoegen door de Webdiensten te gebruiken.

### Overzicht van de stappen {#summary_of_steps-4}

Om een eindpunt uit de dienst te verwijderen, voer de volgende taken uit:

1. Inclusief projectbestanden.
1. Maak een `EndpointRegistryClient` object.
1. Eindpuntkenmerken voor verwijderen instellen.
1. Maak een eindpunt Verwijderen.
1. Laat het eindpunt toe.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u de proxybestanden opnemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-utilities.jar (vereist als AEM Forms worden geïmplementeerd op JBoss Application Server)
* jbossall-client.jar (vereist als AEM Forms worden geïmplementeerd op JBoss Application Server)

Zie [Including AEM Forms Java library files](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)voor informatie over de locatie van deze JAR-bestanden.

**Een EndpointRegistry-client-object maken**

Als u programmatisch een eindpunt Remoting wilt toevoegen, moet u een `EndpointRegistryClient` object maken.

**Kenmerken voor verwijderen van eindpunten instellen**

Om een Remoting eindpunt voor de dienst tot stand te brengen, specificeer de volgende waarden:

* **Waarde** koppelings-id: Geeft het type eindpunt op dat wordt gemaakt. Om een Remoting eindpunt tot stand te brengen, specificeer `Remoting`.
* **Omschrijving**: Specificeert de beschrijving van het eindpunt.
* **Naam**: Specificeert de naam van het eindpunt.
* **Service-id-waarde**: Specificeert de dienst waartot het eindpunt behoort. Bijvoorbeeld, om een Remoting eindpunt aan het proces toe te voegen dat in deze sectie wordt geïntroduceerd (een proces wordt de dienst wanneer het binnen Workbench wordt geactiveerd), specificeer `EncryptDocument`.
* **Bewerkingsnaam**: Specificeert de naam van de verrichting die door het eindpunt te gebruiken wordt aangehaald. Geef bij het maken van een eindpunt Remoting een jokerteken op (&amp;ast;).

**Een eindpunt voor verwijderen maken**

Nadat u het Verwijderen eindpuntattributen plaatst, kunt u een Remoting eindpunt voor de dienst tot stand brengen.

**Het eindpunt inschakelen**

Nadat u een nieuw eindpunt creeert, moet u het toelaten. Wanneer een Remoting eindpunt wordt toegelaten, laat het een Flex cliënt toe om de dienst aan te halen.

**Zie ook**

[Een eindpunt voor Verwijderen toevoegen met de Java API](programmatically-endpoints.md#add-a-remoting-endpoint-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Een eindpunt voor Verwijderen toevoegen met de Java API {#add-a-remoting-endpoint-using-the-java-api}

Voeg een Remoting eindpunt toe door Java API te gebruiken:

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-livecycle-client.jar, op in het klassenpad van uw Java-project.

1. Creeer een voorwerp van de Cliënt EndpointRegistry.

   * Maak een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Maak een `EndpointRegistryClient` object door de constructor ervan te gebruiken en het `ServiceClientFactory` object door te geven.

1. Eindpuntkenmerken voor verwijderen instellen.

   * Maak een `CreateEndpointInfo` object met de constructor ervan.
   * Geef de waarde van de connector-id op door de methode van het `CreateEndpointInfo` object aan te roepen en de tekenreekswaarde door te geven `setConnectorId` `Remoting`.
   * Geef de beschrijving van het eindpunt op door de methode van het `CreateEndpointInfo` `setDescription` object aan te roepen en een tekenreekswaarde door te geven die het eindpunt beschrijft.
   * Geef de naam van het eindpunt op door de methode van het `CreateEndpointInfo` `setName` object aan te roepen en een tekenreekswaarde door te geven die de naam opgeeft.
   * Geef de service op waartoe het eindpunt behoort door de methode van het `CreateEndpointInfo` `setServiceId` object aan te roepen en een tekenreekswaarde door te geven die de servicenaam opgeeft.
   * Geef de bewerking op die wordt aangeroepen door de `CreateEndpointInfo` `setOperationName` methode van het object en geef een tekenreekswaarde door die de naam van de bewerking opgeeft. Geef voor een eindpunt Verwijderen een jokerteken op (&amp;ast;).

1. Maak een eindpunt Verwijderen.

   Maak het eindpunt door de methode van het `EndpointRegistryClient` object aan te roepen `createEndpoint` en het `CreateEndpointInfo` object door te geven. Deze methode retourneert een `Endpoint` object dat het nieuwe eindpunt Remoting vertegenwoordigt.

1. Laat het eindpunt toe.

   Schakel het eindpunt in door de `EndpointRegistryClient` methode van het `enable` object aan te roepen en het `Endpoint` object door te geven dat door de `createEndpoint` methode is geretourneerd.

**Zie ook**

[Overzicht van de stappen](programmatically-endpoints.md#summary-of-steps)

[QuickStart: Een eindpunt voor Verwijderen toevoegen met de Java API](/help/forms/developing/endpoint-registry-java-api-quick.md#quickstart-adding-a-remoting-endpoint-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## TaskManager-eindpunten toevoegen {#adding-taskmanager-endpoints}

U kunt een eindpunt TaskManager aan de dienst programmatically toevoegen door AEM Forms Java API te gebruiken. Door een eindpunt TaskManager aan de dienst toe te voegen, laat u een gebruiker van de Werkruimte toe om de dienst aan te halen. Namelijk kan een gebruiker die in Werkruimte werkt een proces aanhalen dat een overeenkomstig eindpunt TaskManager heeft.

>[!NOTE]
>
>U kunt geen eindpunt TaskManager toevoegen door de Webdiensten te gebruiken.

### Overzicht van de stappen {#summary_of_steps-5}

Om een eindpunt TaskManager aan de dienst toe te voegen, voer de volgende taken uit:

1. Inclusief projectbestanden.
1. Maak een `EndpointRegistryClient` object.
1. Maak een categorie voor het eindpunt.
1. Stel de eindpuntkenmerken van TaskManager in.
1. Creeer een eindpunt TaskManager.
1. Laat het eindpunt toe.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u de proxybestanden opnemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-utilities.jar (vereist als AEM Forms worden geïmplementeerd op JBoss Application Server)
* jbossall-client.jar (vereist als AEM Forms worden geïmplementeerd op JBoss Application Server)

Zie [Including AEM Forms Java library files](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)voor informatie over de locatie van deze JAR-bestanden.

**Een EndpointRegistry-client-object maken**

Alvorens u een eindpunt kunt programmatically toevoegen TaskManager, moet u een `EndpointRegistryClient` voorwerp tot stand brengen.

**Een categorie voor het eindpunt maken**

Categorieën worden gebruikt om services in Workspace te organiseren. Namelijk kan een gebruiker van de Werkruimte de dienst aanhalen die een eindpunt TaskManager door een categorie binnen Werkruimte te selecteren heeft. Wanneer het creëren van een eindpunt TaskManager, kunt u of van verwijzingen voorzien een bestaande categorie of programmatically tot een nieuwe categorie leiden.

>[!NOTE]
>
>Deze sectie leidt tot een nieuwe categorie als deel van het toevoegen van een eindpunt TaskManager aan de dienst.

**De eindpuntattributen van TaskManager plaatsen**

Om een eindpunt TaskManager voor de dienst tot stand te brengen, specificeer de volgende waarden:

* **Connector-id**: Geeft het type eindpunt op dat wordt gemaakt. Om een eindpunt tot stand te brengen TaskManager, specificeer `TaskManagerConnector`.
* **Omschrijving**: Specificeert de beschrijving van het eindpunt.
* **Naam**: Specificeert de naam van het eindpunt.
* **Service-id**: Specificeert de dienst waartot het eindpunt behoort.
* **Categorie**: Specificeert een waarde van categorieherkenningsteken die met het eindpunt TaskManager wordt geassocieerd.
* **Bewerkingsnaam**: Typisch, wanneer het creëren van een eindpunt TaskManager voor de dienst die uit een proces voortkwam dat in Workbench wordt gecreeerd, is de naam van de verrichting `invoke`.

**Creeer een eindpunt TaskManager**

Nadat u een taakmanager eindpuntattributen plaatst, kunt u een eindpunt TaskManager voor de dienst tot stand brengen.

**Het eindpunt inschakelen**

Nadat u een nieuw eindpunt creeert, moet u het toelaten. Wanneer het eindpunt wordt toegelaten, kan het worden gebruikt om de dienst van binnen Werkruimte aan te halen. Nadat u het eindpunt toelaat, kunt u het binnen beleidsconsole bekijken.

**Zie ook**

[Een TaskManager-eindpunt toevoegen met de Java API](programmatically-endpoints.md#add-a-taskmanager-endpoint-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Een TaskManager-eindpunt toevoegen met de Java API {#add-a-taskmanager-endpoint-using-the-java-api}

Voeg een eindpunt TaskManager door Java API toe te gebruiken:

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-livecycle-client.jar, op in het klassenpad van uw Java-project.

1. Creeer een voorwerp van de Cliënt EndpointRegistry.

   * Maak een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Maak een `EndpointRegistryClient` object door de constructor ervan te gebruiken en het `ServiceClientFactory` object door te geven.

1. Maak een categorie voor het eindpunt.

   * Maak een `CreateEndpointCategoryInfo` object door de constructor ervan te gebruiken en de volgende waarden door te geven:

      * Een tekenreekswaarde die de id-waarde van de categorie opgeeft
      * Een tekenreekswaarde die de beschrijving van de categorie opgeeft
   * Maak de categorie door de methode van het `EndpointRegistryClient` object aan te roepen `createEndpointCategory` en het `CreateEndpointCategoryInfo` object door te geven. Deze methode retourneert een `EndpointCategory` object dat de nieuwe categorie vertegenwoordigt.


1. Stel de eindpuntkenmerken van TaskManager in.

   * Maak een `CreateEndpointInfo` object met de constructor ervan.
   * Geef de waarde van de connector-id op door de methode van het `CreateEndpointInfo` object aan te roepen en de tekenreekswaarde door te geven `setConnectorId` `TaskManagerConnector`.
   * Geef de beschrijving van het eindpunt op door de methode van het `CreateEndpointInfo` `setDescription` object aan te roepen en een tekenreekswaarde door te geven die het eindpunt beschrijft.
   * Geef de naam van het eindpunt op door de methode van het `CreateEndpointInfo` `setName` object aan te roepen en een tekenreekswaarde door te geven die de naam opgeeft.
   * Geef de service op waartoe het eindpunt behoort door de methode van het `CreateEndpointInfo` `setServiceId` object aan te roepen en een tekenreekswaarde door te geven die de servicenaam opgeeft.
   * Geef de categorie op waartoe het eindpunt behoort door de methode van het `CreateEndpointInfo` `setCategoryId` object aan te roepen en een tekenreekswaarde door te geven die de categorie-id-waarde opgeeft. U kunt de methode van het `EndpointCategory` `getId` object aanroepen om de id-waarde van deze categorie op te halen.
   * Geef de bewerking op die wordt aangeroepen door de methode van het `CreateEndpointInfo` `setOperationName` object aan te roepen en een tekenreekswaarde door te geven die de naam van de bewerking aangeeft. Typisch, wanneer het creëren van een `TaskManager` eindpunt voor de dienst die uit een proces voortkwam dat in Workbench wordt gecreeerd, is de naam van de verrichting `invoke`.

1. Creeer een eindpunt TaskManager.

   Maak het eindpunt door de methode van het `EndpointRegistryClient` object aan te roepen `createEndpoint` en het `CreateEndpointInfo` object door te geven. Deze methode keert een `Endpoint` voorwerp terug dat het nieuwe eindpunt TaskManager vertegenwoordigt.

1. Laat het eindpunt toe.

   Schakel het eindpunt in door de `EndpointRegistryClient` methode van het `enable` object aan te roepen en het `Endpoint` object door te geven dat door de `createEndpoint` methode is geretourneerd.

**Zie ook**

[Overzicht van de stappen](programmatically-endpoints.md#summary-of-steps)

[QuickStart: Het toevoegen van een eindpunt TaskManager gebruikend Java API](/help/forms/developing/endpoint-registry-java-api-quick.md#quickstart-adding-a-taskmanager-endpoint-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Eindpunten wijzigen {#modifying-endpoints}

U kunt een bestaand eindpunt programmatically wijzigen door AEM Forms Java API te gebruiken. Door een eindpunt te wijzigen, kunt u het gedrag van het eindpunt veranderen. Denk bijvoorbeeld aan een eindpunt van een gecontroleerde map dat een map opgeeft die als controlemap wordt gebruikt. U kunt configuratiewaarden programmatically wijzigen die tot het Gecontroleerde eindpunt van de Omslag behoren, resulterend in een andere omslag die als gecontroleerde omslag functioneert. Voor informatie over configuratiewaarden die tot een Gecontroleerd eindpunt van de Omslag behoren, zie het [Toevoegen van Gecontroleerde Eindpunten](programmatically-endpoints.md#adding-watched-folder-endpoints)van de Omslag.

Om aan te tonen hoe te om een eindpunt te wijzigen, wijzigt deze sectie een Gecontroleerd eindpunt van de Omslag door de omslag te veranderen die zich als gecontroleerde omslag gedraagt.

>[!NOTE]
>
>U kunt een eindpunt niet wijzigen door de Webdiensten te gebruiken.

### Overzicht van de stappen {#summary_of_steps-6}

Om een eindpunt te wijzigen, voer de volgende taken uit:

1. Inclusief projectbestanden.
1. Maak een `EndpointRegistryClient` object.
1. Haal het eindpunt op.
1. Geef nieuwe configuratiewaarden op.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u de proxybestanden opnemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-utilities.jar (vereist als AEM Forms worden geïmplementeerd op JBoss Application Server)
* jbossall-client.jar (vereist als AEM Forms worden geïmplementeerd op JBoss Application Server)

Zie [Including AEM Forms Java library files](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)voor informatie over de locatie van deze JAR-bestanden.

**Een EndpointRegistry-client-object maken**

Als u een eindpunt programmatisch wilt wijzigen, moet u een `EndpointRegistryClient` object maken.

**Win het te wijzigen eindpunt terug**

Alvorens u een eindpunt kunt wijzigen, moet u het terugwinnen. Om een eindpunt terug te winnen, moet u als gebruiker verbinden die tot een eindpunt kan toegang hebben. U wordt aangeraden verbinding te maken als beheerder. (Zie Verbindingseigenschappen [instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)

U kunt een eindpunt terugwinnen door een lijst van eindpunten terug te winnen. U kunt dan door de lijst herhalen, zoekend naar het specifieke eindpunt om te verwijderen. Bijvoorbeeld, kunt u van een eindpunt de plaats bepalen door de dienst te bepalen die aan het eindpunt en het type van eindpunt beantwoordt. Wanneer u van het eindpunt de plaats bepaalt, kunt u het wijzigen.

**Nieuwe configuratiewaarden opgeven**

Wanneer het wijzigen van een eindpunt, specificeer nieuwe configuratiewaarden. Bijvoorbeeld, om een Gecontroleerd eindpunt van de Omslag te wijzigen, terugstel alle Gecontroleerde waarden van de de eindpuntconfiguratie van de Omslag, niet alleen degenen die u wilt wijzigen. Voor informatie over configuratiewaarden die tot een Gecontroleerd eindpunt van de Omslag behoren, zie het [Toevoegen van Gecontroleerde Eindpunten](programmatically-endpoints.md#adding-watched-folder-endpoints)van de Omslag.

>[!NOTE]
>
>Voor informatie over configuratiewaarden die tot een E-maileindpunt behoren, zie het [Toevoegen E-maileindpunten](programmatically-endpoints.md#adding-email-endpoints).

>[!NOTE]
>
>U kunt niet de dienst wijzigen die door het eindpunt wordt aangehaald. Als u probeert om de dienst te wijzigen, wordt een uitzondering geworpen. Om de dienst te wijzigen verbonden aan een bepaald eindpunt, verwijder het eindpunt en creeer nieuwe. (Zie Eindpunten [verwijderen](programmatically-endpoints.md#removing-endpoints).)

**Zie ook**

[Een eindpunt wijzigen met de Java API](programmatically-endpoints.md#modifying-an-endpoint-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Een eindpunt wijzigen met de Java API {#modifying-an-endpoint-using-the-java-api}

Wijzig een eindpunt door Java API te gebruiken:

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-livecycle-client.jar, op in het klassenpad van uw Java-project.

1. Creeer een voorwerp van de Cliënt EndpointRegistry.

   * Maak een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Maak een `EndpointRegistryClient` object door de constructor ervan te gebruiken en het `ServiceClientFactory` object door te geven.

1. Haal het eindpunt op dat u wilt wijzigen.

   * Hiermee wordt een lijst opgehaald met alle eindpunten waartoe de huidige gebruiker (opgegeven in de eigenschappen van de verbinding) toegang heeft door de methode van het `EndpointRegistryClient` object aan te roepen en een `getEndpoints` `PagingFilter` object door te geven dat als filter fungeert. U kunt een `(PagingFilter)null` waarde doorgeven om alle eindpunten te retourneren. Deze methode retourneert een `java.util.List` object waarbij elk element een `Endpoint` object is. Zie `PagingFilter` AEM Forms API Reference [voor meer informatie over een](https://www.adobe.com/go/learn_aemforms_javadocs_63_en)object.
   * Doorloop het `java.util.List` object om te bepalen of het eindpunten heeft. Als er eindpunten zijn, is elk element een `EndPoint` instantie.
   * Bepaal de dienst die aan een eindpunt beantwoordt door de methode van `EndPoint` `getServiceId` objecten aan te halen. Deze methode retourneert een tekenreekswaarde die de servicenaam opgeeft.
   * Bepaal het type eindpunt door de `EndPoint` methode van het `getConnectorId` object aan te roepen. Deze methode retourneert een tekenreekswaarde die het type eindpunt opgeeft. Bijvoorbeeld, als het eindpunt een Gecontroleerd eindpunt van de Omslag is, keert deze methode terug `WatchedFolder`.

1. Geef nieuwe configuratiewaarden op.

   * Maak een `ModifyEndpointInfo` object door de constructor ervan aan te roepen.
   * Roep voor elke configuratiewaarde die moet worden ingesteld de `ModifyEndpointInfo` methode van het `setConfigParameterAsText` object aan. Als u bijvoorbeeld de waarde voor de url-configuratie wilt instellen, roept u de methode van het `ModifyEndpointInfo` `setConfigParameterAsText` object op en geeft u de volgende waarden door:

      * Een tekenreekswaarde die de naam van de configuratiewaarde opgeeft. Als u bijvoorbeeld de `url` configuratiewaarde wilt instellen, geeft u op `url`.
      * Een tekenreekswaarde die de waarde van de configuratiewaarde opgeeft. Als u een waarde voor de `url` configuratiewaarde wilt definiëren, geeft u de locatie van de gecontroleerde map op.
   * Roep de `EndpointRegistryClient` methode van het `modifyEndpoint` object aan en geef het `ModifyEndpointInfo` object door.


**Zie ook**

[Overzicht van de stappen](programmatically-endpoints.md#summary-of-steps)

[QuickStart: Een eindpunt wijzigen met de Java API](/help/forms/developing/endpoint-registry-java-api-quick.md#quickstart-modifying-an-endpoint-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Eindpunten verwijderen {#removing-endpoints}

U kunt een eindpunt uit de dienst programmatically verwijderen door AEM Forms Java API te gebruiken. Nadat u een eindpunt verwijdert, kan de dienst niet worden aangehaald door de aanroepingsmethode te gebruiken die het eindpunt toeliet. Bijvoorbeeld, als u een eindpunt van de ZEEP uit de dienst verwijdert, kunt u niet de dienst aanhalen door de wijze van de ZEEP te gebruiken.

Om aan te tonen hoe te om een eindpunt uit de dienst te verwijderen, verwijdert deze sectie een eindpunt EJB uit de dienst genoemd *EncryptDocument*.

>[!NOTE]
>
>U kunt geen eindpunt verwijderen door de Webdiensten te gebruiken.

### Overzicht van de stappen {#summary_of_steps-7}

Om een eindpunt uit de dienst te verwijderen, voer de volgende taken uit:

1. Inclusief projectbestanden.
1. Maak een `EndpointRegistryClient` object.
1. Haal het eindpunt op.
1. Verwijder het eindpunt.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u de proxybestanden opnemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-utilities.jar (vereist als AEM Forms worden geïmplementeerd op JBoss Application Server)
* jbossall-client.jar (vereist als AEM Forms worden geïmplementeerd op JBoss Application Server)

Zie [Including AEM Forms Java library files](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)voor informatie over de locatie van deze JAR-bestanden.

**Een EndpointRegistry-client-object maken**

Als u een eindpunt programmatisch wilt verwijderen, moet u een `EndpointRegistryClient` object maken.

**Het te verwijderen eindpunt ophalen**

Voordat u een eindpunt kunt verwijderen, moet u het ophalen. Om een eindpunt terug te winnen, moet u als gebruiker verbinden die tot een eindpunt kan toegang hebben. U wordt aangeraden verbinding te maken als beheerder. (Zie Verbindingseigenschappen [instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)

U kunt een eindpunt terugwinnen door een lijst van eindpunten terug te winnen. U kunt dan door de lijst herhalen, zoekend naar het specifieke eindpunt om te verwijderen. Bijvoorbeeld, kunt u van een eindpunt de plaats bepalen door de dienst te bepalen die aan het eindpunt en het type van eindpunt beantwoordt. Wanneer u het eindpunt zoekt, kunt u het verwijderen.

**Het eindpunt verwijderen**

Nadat u een nieuw eindpunt creeert, moet u het toelaten. Wanneer het eindpunt wordt toegelaten, kan het worden gebruikt om de dienst aan te halen. Nadat u het eindpunt toelaat, kunt u het binnen beleidsconsole bekijken.

**Zie ook**

[Een eindpunt verwijderen met de Java API](programmatically-endpoints.md#removing-an-endpoint-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Een eindpunt verwijderen met de Java API {#removing-an-endpoint-using-the-java-api}

Een eindpunt verwijderen met de Java API:

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-livecycle-client.jar, op in het klassenpad van uw Java-project.

1. Creeer een voorwerp van de Cliënt EndpointRegistry.

   * Maak een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Maak een `EndpointRegistryClient` object door de constructor ervan te gebruiken en het `ServiceClientFactory` object door te geven.

1. Haal het te verwijderen eindpunt op.

   * Haal een lijst op van alle eindpunten waartoe de huidige gebruiker (opgegeven in de verbindingseigenschappen) toegang heeft door de methode van het `EndpointRegistryClient` object aan te roepen en een `getEndpoints` `PagingFilter` object door te geven dat als filter fungeert. U kunt doorgeven `(PagingFilter)null` om alle eindpunten te retourneren. Deze methode retourneert een `java.util.List` object waarbij elk element een `Endpoint` object is.
   * Doorloop het `java.util.List` object om te bepalen of het eindpunten heeft. Als er eindpunten zijn, is elk element een `EndPoint` instantie.
   * Bepaal de dienst die aan een eindpunt beantwoordt door de methode van `EndPoint` `getServiceId` objecten aan te halen. Deze methode retourneert een tekenreekswaarde die de servicenaam opgeeft.
   * Bepaal het type eindpunt door de `EndPoint` methode van het `getConnectorId` object aan te roepen. Deze methode retourneert een tekenreekswaarde die het type eindpunt opgeeft. Als het eindpunt bijvoorbeeld een EJB-eindpunt is, retourneert deze methode `EJB`.

1. Verwijder het eindpunt.

   Verwijder het eindpunt door de methode van het `EndpointRegistryClient` voorwerp aan te halen `remove` en het `EndPoint` voorwerp over te gaan dat het te verwijderen eindpunt vertegenwoordigt.

**Zie ook**

[Overzicht van de stappen](programmatically-endpoints.md#summary-of-steps)

[QuickStart: Een eindpunt verwijderen met de Java API](/help/forms/developing/endpoint-registry-java-api-quick.md#quickstart-removing-an-endpoint-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Gegevens eindpuntconnector ophalen {#retrieving-endpoint-connector-information}

U kunt informatie over eindpuntschakelaars programmatically terugwinnen gebruikend AEM Forms API. Een schakelaar laat een eindpunt toe om de dienst aan te halen gebruikend diverse aanroepingsmethodes. Bijvoorbeeld, laat een Gecontroleerde schakelaar van de Omslag een eindpunt toe om de dienst aan te halen gebruikend gecontroleerde omslagen. Door programmatically het terugwinnen van informatie over eindpuntschakelaars, kunt u configuratiewaarden terugwinnen verbonden aan een schakelaar zoals welke configuratiewaarden worden vereist en welke facultatieve zijn.

Om aan te tonen hoe te om informatie over eindpuntschakelaars terug te winnen, wint deze sectie informatie over een Gecontroleerde schakelaar van de Omslag terug. (Zie [Gecontroleerde mapeindpunten](programmatically-endpoints.md#adding-watched-folder-endpoints)toevoegen.)

>[!NOTE]
>
>U kunt geen informatie over eindpunten terugwinnen door de Webdiensten te gebruiken.

>[!NOTE]
>
>Dit onderwerp gebruikt `ConnectorRegistryClient` API om informatie over eindpuntschakelaars terug te winnen. (Zie [API-naslaggids](https://www.adobe.com/go/learn_aemforms_javadocs_63_en)voor AEM Forms.)

### Overzicht van de stappen {#summary_of_steps-8}

Om de informatie van de eindpuntschakelaar terug te winnen, voer de volgende taken uit:

1. Inclusief projectbestanden.
1. Maak een `ConnectorRegistryClient` object.
1. Geef het type aansluiting op.
1. Haal configuratiewaarden op.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u de proxybestanden opnemen.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-utilities.jar (vereist als AEM Forms worden geïmplementeerd op JBoss Application Server)
* jbossall-client.jar (vereist als AEM Forms worden geïmplementeerd op JBoss Application Server)

Als AEM Forms worden geïmplementeerd op een ondersteunde J2EE-toepassingsserver die geen JBoss is, vervangt u adobe-utilities.jar en jbossall-client.jar door JAR-bestanden die specifiek zijn voor de J2EE-toepassingsserver waarop AEM Forms worden geïmplementeerd. Zie [Including AEM Forms Java library files](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)voor informatie over de locatie van alle JAR-bestanden voor AEM Forms.

**Creeer een voorwerp van de Cliënt ConnectorRegistry**

Om de informatie van de eindpuntschakelaar programmatically terug te winnen, creeer een `ConnectorRegistryClient` voorwerp.

**Geef het type aansluiting op**

Specificeer het type van schakelaar waarvan om informatie terug te winnen. De volgende types van schakelaars bestaan:

* **EJB**: Laat een cliënttoepassing toe om de dienst aan te halen gebruikend de wijze EJB.
* **SOAP**: Laat een cliënttoepassing toe om de dienst aan te halen gebruikend de wijze van de ZEEP.
* **Gecontroleerde map**: Hiermee kunnen gecontroleerde mappen een service aanroepen.
* **E-mail**: Laat e-mailberichten toe om de dienst aan te halen.
* **Verwijderen**: Laat een Flex cliënttoepassing toe om de dienst aan te halen.
* **TaskManagerConnector**: Laat een gebruiker van de Werkruimte toe om de dienst van binnen Werkruimte aan te halen.

**Configuratiewaarden ophalen**

Nadat u het schakelaartype specificeert, kunt u informatie over de schakelaar zoals gesteunde configuratiewaarde terugwinnen. Bijvoorbeeld, voor om het even welke schakelaar, kunt u bepalen welke configuratiewaarden worden vereist en die facultatief zijn.

**Zie ook**

[Gegevens van eindpuntconnector ophalen met de Java API](programmatically-endpoints.md#retrieve-endpoint-connector-information-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Gegevens van eindpuntconnector ophalen met de Java API {#retrieve-endpoint-connector-information-using-the-java-api}

Haal de informatie van de eindpuntschakelaar door Java API te gebruiken terug:

1. Inclusief projectbestanden. .

   Neem client-JAR-bestanden, zoals adobe-livecycle-client.jar, op in het klassenpad van uw Java-project.

1. Creeer een voorwerp van de Cliënt ConnectorRegistry.

   * Maak een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Maak een `ConnectorRegistryClient` object door de constructor ervan te gebruiken en het `ServiceClientFactory` object door te geven.

1. Geef het type aansluiting op.

   Specificeer het schakelaartype door de methode van het `ConnectorRegistryClient` `getEndpointDefinition` voorwerp aan te halen en een koordwaarde over te gaan die het schakelaartype specificeert. Als u bijvoorbeeld het verbindingstype Gecontroleerde map wilt opgeven, geeft u de tekenreekswaarde door `WatchedFolder`. Deze methode retourneert een `Endpoint` object dat overeenkomt met het type connector.

1. Haal configuratiewaarden op.

   * Haal configuratiewaarden op die binnen dit eindpunt door de methode van de `Endpoint` objecten aan te halen worden geassocieerd `getConfigParameters` . Deze methode retourneert een array met `ConfigParameter` objecten.
   * Haal informatie over elke configuratiewaarde op door elk element binnen de serie terug te winnen. Elk element is een `ConfigParameter` object. U kunt bijvoorbeeld bepalen of de configuratiewaarde verplicht of optioneel is door de `ConfigParameter` methode van het `isRequired` object aan te roepen. Als de configuratiewaarde wordt vereist, dan keert deze methode `true`.

**Zie ook**

[Overzicht van de stappen](programmatically-endpoints.md#summary-of-steps)

[QuickStart: Gegevens van eindpuntconnector ophalen met de Java API](/help/forms/developing/endpoint-registry-java-api-quick.md#quickstart-retrieving-endpoint-connector-information-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)
