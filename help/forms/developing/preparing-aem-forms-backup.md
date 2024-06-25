---
title: AEM Forms for Backup voorbereiden
description: Leer hoe u de service Back-up en herstel kunt gebruiken om de back-upmodus voor de AEM Forms-server in te schakelen en te verlaten met de Java API en de webservice-API.
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
exl-id: aeab003d-ba64-4760-9c56-44638501e9ff
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,APIs & Integrations
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '2484'
ht-degree: 0%

---

# AEM Forms for Backup voorbereiden {#preparing-aem-forms-for-backup}

**Voorbeelden en voorbeelden in dit document gelden alleen voor AEM Forms in JEE-omgeving.**

## Over de service Back-up en herstel {#about-the-backup-and-restore-service}

Met de service Back-up en Herstellen kunt u AEM Forms in *back-upmodus*, waardoor hot back-ups kunnen worden uitgevoerd. De service Back-up en herstel voert geen back-up van AEM Forms uit of herstelt uw systeem niet. In plaats daarvan wordt de server in een status gezet voor consistente en betrouwbare back-ups, terwijl de server verder kan worden uitgevoerd. U bent verantwoordelijk voor de acties om een back-up te maken van de Global Document Storage (GDS) en de database die is verbonden met de Forms Server. De GDS is een map waarin bestanden worden opgeslagen die worden gebruikt in een langlevend proces.

De back-upmodus is een toestand die de server invoert zodat bestanden in de GDS niet worden gewist terwijl een back-upprocedure plaatsvindt. In plaats daarvan worden submappen gemaakt onder de GDS-map om een record bij te houden van bestanden die moeten worden gewist nadat de back-upmodus is beëindigd. Een bestand is bedoeld om het systeem opnieuw te laten opstarten en kan dagen, of zelfs jaren, beslaan. Deze bestanden vormen een essentieel onderdeel van de algemene status van de Forms Server en kunnen PDF-bestanden, beleidsregels of formuliersjablonen bevatten. Als een van deze bestanden verloren gaat of beschadigd raakt, kunnen de processen op de Forms-server instabiel worden en kunnen gegevens verloren gaan.

U kunt ervoor kiezen back-ups van momentopnamen uit te voeren, waarbij u doorgaans de back-upmodus gedurende een periode start en vervolgens de back-upmodus verlaat nadat u de back-upactiviteiten hebt voltooid. Het verlaten van reservewijze wordt vereist zodat de dossiers van GDS kunnen worden gezuiverd om ervoor te zorgen dat het niet onnodig groot groeit. U kunt of reservewijze uitdrukkelijk verlaten of op de tijd wachten om op een reservewijzesessie te verlopen.

U kunt de server ook in de modus voor onbeperkte back-up laten. Dit is standaard het geval bij back-upstrategieën voor rolback-ups of continue systeemdekking. Rolling backup mode wijst erop dat het systeem altijd in reservewijze is, met een nieuwe reservewijzesessie die wordt geïnitieerd zodra de vorige zitting wordt vrijgegeven. In de modus voor continue back-up wordt een bestand na twee back-upmodussessies gewist en wordt er niet langer naar verwezen.

Met de service Back-up en herstel kunt u bestaande of nieuwe toepassingen uitbreiden die u maakt voor het maken van back-ups van de GDS of database die op de Forms-server is aangesloten.

>[!NOTE]
>
>Net als bij elk ander aspect van uw AEM Forms-implementatie, moet uw back-up- en herstelstrategie worden ontwikkeld en getest in een ontwikkelings- of testomgeving voordat deze in de productie wordt gebruikt om ervoor te zorgen dat de volledige oplossing werkt zoals u had verwacht zonder gegevensverlies.

U kunt deze taken uitvoeren met behulp van de service Back-up en herstel:

* Ga reservewijze in.
* Laat de back-upmodus staan.

>[!NOTE]
>
>Ga voor meer informatie over wat u moet overwegen wanneer u back-ups maakt voor AEM Forms naar [administratie Help](https://www.adobe.com/go/learn_aemforms_admin_63).

>[!NOTE]
>
>Ga voor meer informatie over de service Back-up en herstel naar [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Back-upmodus activeren op de Forms-server {#entering-backup-mode-on-the-forms-server}

U gaat reservewijze in om voor hete steunen van een Server van Forms toe te staan. Wanneer u de back-upmodus activeert, geeft u de volgende informatie op op basis van de back-upprocedures van uw organisatie:

* Een uniek label om de back-upmodussessie te identificeren die nuttig kan zijn voor uw back-upprocessen.
* De tijd voor de reserveprocedure om te voltooien.
* Een vlag om erop te wijzen of om op ononderbroken reservewijze te zijn, die slechts nuttig is als u het rollen steunen uitvoert.

Voordat u toepassingen gaat schrijven om in de back-upmodus te gaan, is het raadzaam de back-upprocedures te begrijpen die worden gebruikt nadat u de Forms-server in de back-upmodus hebt gezet. Ga voor meer informatie over wat u moet overwegen wanneer u back-ups maakt voor AEM Forms naar [administratie Help](https://www.adobe.com/go/learn_aemforms_admin_63).

>[!NOTE]
>
>Ga voor meer informatie over de service Back-up en herstel naar [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary-of-steps}

Voer de volgende stappen uit om een toepassing te maken die de back-upmodus activeert:

1. Inclusief projectbestanden.
1. Maak een BackupService-clientobject.
1. Bepaal een uniek etiket, de hoeveelheid tijd om de steun uit te voeren, en of om op ononderbroken reservewijze te zijn.
1. Ga reservewijze in.
1. (Optioneel) Haal informatie op over de back-upmodussessie op de server.
1. Maak een back-up van de GDS (Global Data Store) en de database.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Deze bestanden zijn belangrijk om in uw project op te nemen voor het correct compileren van uw code en het gebruik van de API voor back-up- en herstelservice.

Voor informatie over de locatie van deze bestanden raadpleegt u [Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Een BackupService Client API-object maken**

Als u de back-upmodus programmatisch wilt verlaten, maakt u een BackupService-clientobject om de API voor back-up en herstel te gebruiken.

**Beslissen op een uniek etiket, bepalen de hoeveelheid tijd om de steun uit te voeren, en beslissen of om op ononderbroken reservewijze te zijn**

Voordat u de back-upmodus activeert, moet u een uniek label kiezen, bepalen hoeveel tijd u wilt toewijzen om de back-up uit te voeren en bepalen of u de Forms-server in de back-upmodus wilt laten staan. Deze overwegingen zijn belangrijk om met de reserveprocedures te integreren die door uw organisatie worden gevestigd. (Zie [administratie Help](https://www.adobe.com/go/learn_aemforms_admin_63).)

**Back-upmodus openen**

Ga reservewijze met de parameters in die met de reserveprocedures bij uw organisatie verenigbaar zijn.

**Informatie ophalen over de back-upmodussessie op de server**

Nadat u de back-upmodus hebt geactiveerd, kunt u informatie over de sessie ophalen. Deze informatie kan worden gebruikt om met uw reserveprocedures te integreren

**Maak een back-up van de GDS en de database**

Nadat u met succes de reservewijze ingaat, kunt u een steun van de Globale Opslag van het Document (GDS) en het gegevensbestand uitvoeren dat de Server van Forms met wordt verbonden. Deze stap is specifiek voor uw organisatie, aangezien u deze stap manueel kunt uitvoeren of u andere hulpmiddelen kunt in werking stellen om de reserveprocedure uit te voeren.

### Back-upmodus starten met de Java API {#enter-backup-mode-using-the-java-api}

Voer de back-upmodus in met de API voor back-up- en herstelservice:

1. Projectbestanden opnemen

   Neem de benodigde client-JAR-bestanden op, zoals adobe-backup-restore-client-sdk.jar, in het klassenpad van uw Java-project. Als u de Java-clienttoepassing wilt maken, moeten de volgende JAR-bestanden worden toegevoegd aan het klassepad van uw project:

   * adobe-backup-restore-client-sdk.jar
   * adobe-livecycle-client.jar
   * adobe-usermanager-client.jar
   * adobe-utilities.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss Application Server)
   * jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss Application Server)

1. Een BackupService Client API-object maken

   U gebruikt een `ServiceClientFactory` -object en het BackupService client-API-object samen.

   * Een `ServiceClientFactory` object dat verbindingseigenschappen bevat. (Zie [Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)
   * Een `BackupService` object door de constructor ervan te gebruiken en de `ServiceClientFactory` object.

1. Beslissen op een uniek etiket, bepalen de hoeveelheid tijd om de steun uit te voeren, en beslissen of om op ononderbroken reservewijze te zijn

   Beslis op een uniek etiket, bepaal de hoeveelheid tijd die u wilt toewijzen om de steun uit te voeren, en besluit of u de Server van Forms op ononderbroken reservewijze wilt blijven.

1. Back-upmodus openen

   Ga reservewijze door aan te halen binnen `enterBackupMode` methode met de volgende parameters:

   * A `String` waarde die een uniek, leesbaar label opgeeft dat de back-upmodussessie identificeert. U wordt aangeraden geen spaties of tekens te gebruiken die niet in XML-indeling kunnen worden gecodeerd.
   * An `int` waarde die het aantal minuten aangeeft dat moet worden bewaard in de back-upmodus. U kunt een waarde opgeven vanuit `1` tot `10080` (het aantal minuten in een week). Deze waarde wordt genegeerd bij gebruik van de modus voor continue back-up.
   * A `Boolean` waarde die aangeeft of de modus voor continue back-up moet worden geactiveerd. Een waarde van `True` geeft aan dat de modus voor continue back-up moet worden geactiveerd. In de modus voor continue back-up wordt de waarde die u opgeeft voor het aantal minuten dat u in de back-upmodus wilt blijven, genegeerd.

     In de modus Continue back-up wordt een nieuwe back-upmodus gestart nadat de huidige sessie is voltooid. Een waarde van `False` betekent dat de continue back-upmodus niet wordt gebruikt en dat, nadat de back-upmodus is verlaten, de bestanden uit de GDS opnieuw worden gezuiverd.

1. Informatie ophalen over de back-upmodussessie op de server

   Gegevens ophalen met de opdracht `BackupModeEntryResult` object dat wordt geretourneerd nadat het object is aangeroepen `enterBackupMode` methode. De informatie die u kunt terugwinnen nadat u reservewijze ingaat kan nuttig zijn om met uw reserveprocedures te integreren. Het label, de back-up-id en de begintijd kunnen bijvoorbeeld handig zijn als invoer voor bestandsnamen voor de back-upprocedure.

1. Maak een back-up van de GDS en de database

   Maak een back-up van de Global Document Storage (GDS) en de database waarmee uw Forms Server is verbonden. De acties om de back-up uit te voeren maken geen deel uit van de SDK van AEM Forms en kunnen zelfs handmatige stappen bevatten die specifiek zijn voor de back-upprocedures in uw organisatie.

### Back-upmodus starten met de webservice-API {#enter-backup-mode-using-the-web-service-api}

Voer de back-upmodus in met behulp van de webservice van de API voor back-up en herstel:

1. Projectbestanden opnemen

   * Creeer een Microsoft .NET cliëntassemblage die de Reserve en Terugzetdienst API WSDL verbruikt.
   * Verwijs naar de Microsoft .NET cliëntassemblage.

1. Een BackupService Client API-object maken

   Gebruikend de de cliëntassemblage van Microsoft .NET, creeer een `BackupServiceService` object door de standaardconstructor aan te roepen en de referenties op te geven met de `Credentials` methode.

1. Beslissen op een uniek etiket, bepalen de hoeveelheid tijd om de steun uit te voeren, en beslissen of om op ononderbroken reservewijze te zijn

   Beslis op een uniek etiket, bepaal de hoeveelheid tijd die u wilt toewijzen om de steun uit te voeren, en besluit of u de Server van Forms op ononderbroken reservewijze wilt blijven.

1. Back-upmodus openen

   Als u de back-upmodus wilt inschakelen, roept u de methode enterBackupMode aan en geeft u de volgende waarden door:

   * A `String` waarde die een uniek, leesbaar label opgeeft dat de back-upmodussessie identificeert. U wordt aangeraden geen spaties of tekens te gebruiken die niet in XML-indeling kunnen worden gecodeerd.
   * A `Uint32` waarde die het aantal minuten aangeeft dat moet worden bewaard in de back-upmodus. U kunt een waarde opgeven vanuit `1` tot `10080` (aantal minuten in één week). Deze waarde wordt genegeerd bij gebruik van de modus voor continue back-up.
   * A `Boolean` waarde die aangeeft of de modus voor continue back-up moet worden geactiveerd. Een waarde van `True` geeft aan dat de modus voor continue back-up moet worden geactiveerd. In de modus voor continue back-up wordt de waarde die u opgeeft voor het aantal minuten dat u in de back-upmodus wilt blijven, genegeerd. In de modus Continue back-up wordt een nieuwe back-upmodus gestart nadat de huidige sessie is voltooid.

     Een waarde van `False` betekent dat de continue back-upmodus niet wordt gebruikt en dat, nadat de back-upmodus is verlaten, de bestanden uit de GDS opnieuw worden gezuiverd.

1. Informatie ophalen over de back-upmodussessie op de server

   Haal informatie op over de back-upmodussessie nadat u de enterBackupMode-methode hebt aangeroepen vanuit de BackupModeEntryResult die is geretourneerd om te controleren of deze is gelukt. De informatie die u kunt terugwinnen nadat u reservewijze ingaat kan nuttig zijn om met uw reserveprocedures te integreren. Het label, de back-up-id en de begintijd kunnen bijvoorbeeld handig zijn als invoer voor bestandsnamen voor de back-upprocedure.

1. Maak een back-up van de GDS en de database

   Maak een back-up van de Global Document Storage (GDS) en de database waarmee uw Forms Server is verbonden. De acties om de back-up uit te voeren maken geen deel uit van de SDK van AEM Forms en kunnen zelfs handmatige stappen bevatten die specifiek zijn voor de back-upprocedures in uw organisatie.

## Back-upmodus op de Forms-server laten staan {#leaving-backup-mode-on-the-forms-server}

U verlaat de back-upmodus, zodat de Forms-server de bestanden hervat van de GDS (Global Document Storage) op de Forms-server.

Voordat u toepassingen schrijft om in de modus Verlaten te gaan, is het raadzaam de back-upprocedures te begrijpen die bij AEM Forms worden gebruikt. Ga voor meer informatie over wat u moet overwegen wanneer u back-ups maakt voor AEM Forms naar [administratie Help](https://www.adobe.com/go/learn_aemforms_admin_63).

>[!NOTE]
>
>Ga voor meer informatie over de service Back-up en herstel naar [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary_of_steps-1}

Voer de volgende stappen uit om de back-upmodus te verlaten:

1. Inclusief projectbestanden.
1. Maak een BackupService-clientobject.
1. Laat de back-upmodus staan.
1. (Optioneel) Haal informatie op over de back-upmodussessie die op de Forms-server werd uitgevoerd.

**Projectbestanden opnemen**

Neem alle benodigde bestanden op in uw ontwikkelingsproject. Deze bestanden zijn belangrijk voor het correct compileren van uw code en het gebruik van de API voor back-up- en herstelservice.

Voor informatie over de locatie van deze bestanden raadpleegt u [Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Een BackupService Client API-object maken**

Als u de back-upmodus programmatisch wilt verlaten, maakt u een BackupService-clientobject om de API voor back-up en herstel te gebruiken.

**Back-upmodus verlaten**

Laat de back-upmodus ingeschakeld om bestanden van de Global Document Storage (GDS) weer op de normale manier te wissen. Voordat u de back-upmodus verlaat, moet u controleren of de back-upprocedures zijn voltooid.

**Informatie ophalen over de sessie in de back-upmodus die is beëindigd**

Nadat u de back-upmodus hebt verlaten, kunt u informatie over de sessie ophalen. Deze informatie kan worden gebruikt om met uw reserveprocedures te integreren.

### Back-upmodus verlaten met de Java API {#leave-backup-mode-using-the-java-api}

Maak een back-upmodus met de API voor back-up en herstel (Java):

1. Projectbestanden opnemen

   Neem de benodigde client-JAR-bestanden op, zoals adobe-backup-restore-client-sdk.jar, in het klassenpad van uw Java-project. Als u een Java-clienttoepassing wilt maken, moeten de volgende JAR-bestanden worden toegevoegd aan het klassepad van uw project:

   * adobe-backup-restore-client-sdk.jar
   * adobe-livecycle-client.jar
   * adobe-usermanager-client.jar
   * adobe-utilities.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss Application Server)
   * jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss Application Server)

1. Een BackupService Client API-object maken

   U gebruikt een `ServiceClientFactory` -object en het BackupService client-API-object samen.

   * Een `ServiceClientFactory` object dat verbindingseigenschappen bevat. (Zie [Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)
   * Een `BackupService` object door de constructor ervan te gebruiken en de `ServiceClientFactory` object als parameter.

1. Back-upmodus openen

   De back-upmodus verlaten door de `leaveBackupMode` methode.

1. Informatie ophalen over de back-upmodussessie op de server

   Hiermee wordt informatie over de bewerking opgehaald met de opdracht `BackupModeResult` object dat wordt geretourneerd. De informatie die u kunt terugwinnen nadat u reservewijze ingaat kan nuttig zijn om met uw reserveprocedures te integreren. Het label, de back-up-id en de begintijd kunnen bijvoorbeeld handig zijn als invoer voor bestandsnamen voor de back-upprocedure.

### Back-upmodus verlaten met de webservice-API {#leave-backup-mode-using-the-web-service-api}

Maak een back-upmodus met de API voor back-up en herstel (webservice):

1. Projectbestanden opnemen

   Als u webservices wilt gebruiken, moet u ervoor zorgen dat u de proxybestanden opneemt. Voer de volgende stappen uit om uw project te configureren voor het gebruik van de API voor back-up en herstel als webservice.

   * Creeer een Microsoft .NET cliëntassemblage die de Reserve en Terugzetdienst API WSDL verbruikt.
   * Verwijs naar de Microsoft .NET cliëntassemblage.

1. Een BackupService Client API-object maken

   Gebruikend de de cliëntassemblage van Microsoft .NET, creeer een `BackupServiceService` object door de standaardconstructor aan te roepen.

1. Back-upmodus openen

   De back-upmodus verlaten door de `leaveBackupMode` bewerking met webservices.

1. Informatie ophalen over de back-upmodussessie op de server

   Haal de id van de back-upmodus na de bewerking op om te controleren of deze is gelukt. De informatie die u kunt terugwinnen nadat u reservewijze verlaat kan nuttig zijn om met uw reserveprocedures te integreren.
