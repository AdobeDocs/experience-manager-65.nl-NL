---
title: AEM-formulieren voorbereiden voor back-up
seo-title: AEM-formulieren voorbereiden voor back-up
description: 'null'
seo-description: 'null'
uuid: b8ef2bed-62e2-4000-b55a-30d2fc398a5f
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: e747147e-e96d-43c7-87b3-55947eef81f5
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# AEM-formulieren voorbereiden voor back-up {#preparing-aem-forms-for-backup}

## Over de service Back-up en herstel {#about-the-backup-and-restore-service}

Met de service Back-up en herstel kunt u AEM Forms in de *back-upmodus* plaatsen, zodat hot back-ups kunnen worden uitgevoerd. De service Back-up en herstel voert geen back-up van AEM Forms uit of herstelt uw systeem. In plaats daarvan wordt de server in een status gezet voor consistente en betrouwbare back-ups, terwijl de server verder kan worden uitgevoerd. U bent verantwoordelijk voor de acties om een back-up te maken van de Global Document Storage (GDS) en de database die is verbonden met de formulierserver. De GDS is een map waarin bestanden worden opgeslagen die worden gebruikt in een langlevend proces.

De back-upmodus is een toestand die de server invoert zodat bestanden in de GDS niet worden gewist terwijl een back-upprocedure plaatsvindt. In plaats daarvan worden submappen gemaakt onder de GDS-map om een record bij te houden van bestanden die moeten worden gewist nadat de back-upmodus is beëindigd. Een bestand is bedoeld om het systeem opnieuw te laten opstarten en kan dagen, of zelfs jaren, beslaan. Deze bestanden vormen een essentieel onderdeel van de algemene status van de formulierserver en kunnen PDF-bestanden, beleidsregels of formuliersjablonen bevatten. Als een van deze bestanden verloren gaat of beschadigd raakt, kunnen de processen op de formulierserver instabiel worden en kunnen er gegevens verloren gaan.

U kunt ervoor kiezen back-ups van momentopnamen uit te voeren, waarbij u doorgaans de back-upmodus gedurende een periode start en vervolgens de back-upmodus verlaat nadat u de back-upactiviteiten hebt voltooid. Het verlaten van reservewijze wordt vereist zodat de dossiers van GDS kunnen worden gezuiverd om ervoor te zorgen dat het niet onnodig groot groeit. U kunt of reservewijze uitdrukkelijk verlaten of op de tijd wachten om op een reservewijzesessie te verlopen.

U kunt de server ook in de modus voor onbeperkte back-up laten. Dit is standaard het geval bij back-upstrategieën voor rolback-ups of continue systeemdekking. Rolling backup mode wijst erop dat het systeem altijd in reservewijze is, met een nieuwe reservewijzesessie die wordt geïnitieerd zodra de vorige zitting wordt vrijgegeven. In de modus voor continue back-up wordt een bestand na twee back-upmodussessies gewist en wordt er niet langer naar verwezen.

Met de service Back-up en herstel kunt u bestaande of nieuwe toepassingen uitbreiden die u maakt om back-ups te maken van de GDS of database die is verbonden met de formulierserver.

>[!NOTE]
>
>Net als bij elk ander aspect van de implementatie van AEM Forms, moet uw back-up- en herstelstrategie worden ontwikkeld en getest in een ontwikkelings- of testomgeving voordat deze in de productie wordt gebruikt om ervoor te zorgen dat de volledige oplossing naar behoren werkt, zonder gegevensverlies.

U kunt deze taken uitvoeren met behulp van de service Back-up en herstel:

* Ga reservewijze in.
* Laat de back-upmodus staan.

>[!NOTE]
>
>Voor meer informatie over wat te overwegen wanneer het uitvoeren van steunen voor Vormen AEM, zie [beleidshulp](https://www.adobe.com/go/learn_aemforms_admin_63).

>[!NOTE]
>
>Zie [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63)voor meer informatie over de service Back-up en herstel.

## Back-upmodus invoeren op de formulierserver {#entering-backup-mode-on-the-forms-server}

U gaat reservewijze in om voor hete steunen van een vormenserver toe te staan. Als u de back-upmodus activeert, geeft u de volgende informatie op op basis van de back-upprocedures van uw organisatie:

* Een uniek label om de back-upmodussessie te identificeren die nuttig kan zijn voor uw back-upprocessen.
* De tijd voor de reserveprocedure om te voltooien.
* Een vlag om erop te wijzen of om op ononderbroken reservewijze te zijn, die slechts nuttig is als u het rollen steunen uitvoert.

Voordat u toepassingen gaat schrijven om de back-upmodus te activeren, is het raadzaam de back-upprocedures te begrijpen die worden gebruikt nadat u de formulierserver in de back-upmodus hebt gezet. Voor meer informatie over wat te overwegen wanneer het uitvoeren van steunen voor Vormen AEM, zie [beleidshulp](https://www.adobe.com/go/learn_aemforms_admin_63).

>[!NOTE]
>
>Zie [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63)voor meer informatie over de service Back-up en herstel.

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

Zie [Including AEM Forms Java library files](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)voor informatie over de locatie van deze bestanden.

**Een BackupService Client API-object maken**

Als u de back-upmodus programmatisch wilt verlaten, maakt u een BackupService-clientobject om de API voor back-up en herstel te gebruiken.

**Beslissen op een uniek etiket, bepalen de hoeveelheid tijd om de steun uit te voeren, en beslissen of om op ononderbroken reservewijze te zijn**

Voordat u de back-upmodus activeert, moet u een uniek label kiezen, bepalen hoeveel tijd u wilt toewijzen om de back-up uit te voeren en bepalen of de formulierserver in de back-upmodus moet blijven. Deze overwegingen zijn belangrijk om met de reserveprocedures te integreren die door uw organisatie worden gevestigd. (Zie [Help bij](https://www.adobe.com/go/learn_aemforms_admin_63)de administratie.)

**Back-upmodus openen**

Ga reservewijze met de parameters in die met de reserveprocedures bij uw organisatie verenigbaar zijn.

**Informatie ophalen over de back-upmodussessie op de server**

Nadat u de back-upmodus hebt geactiveerd, kunt u informatie over de sessie ophalen. Deze informatie kan worden gebruikt om met uw reserveprocedures te integreren

**Maak een back-up van de GDS en de database**

Nadat u de back-upmodus hebt geactiveerd, kunt u een back-up maken van de GDS (Global Document Storage) en de database waarmee de formulierserver is verbonden. Deze stap is specifiek voor uw organisatie, aangezien u deze stap manueel kunt uitvoeren of u andere hulpmiddelen kunt in werking stellen om de reserveprocedure uit te voeren.

### Back-upmodus starten met de Java API {#enter-backup-mode-using-the-java-api}

Voer de back-upmodus in met de API voor back-up- en herstelservice:

1. Projectbestanden opnemen

   Neem de benodigde client-JAR-bestanden op, zoals adobe-backup-restore-client-sdk.jar, in het klassenpad van uw Java-project. Als u de Java-clienttoepassing wilt maken, moeten de volgende JAR-bestanden worden toegevoegd aan het klassepad van uw project:

   * adobe-backup-restore-client-sdk.jar
   * adobe-livecycle-client.jar
   * adobe-usermanager-client.jar
   * adobe-utilities.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss Application Server)
   * jbossall-client.jar (vereist als AEM-formulieren worden geïmplementeerd op JBoss Application Server)

1. Een BackupService Client API-object maken

   U gebruikt een `ServiceClientFactory` object en het client-API-object BackupService samen.

   * Maak een `ServiceClientFactory` object dat verbindingseigenschappen bevat. (Zie Verbindingseigenschappen [instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)
   * Maak een `BackupService` object door de constructor ervan te gebruiken en het `ServiceClientFactory` object door te geven.

1. Beslissen op een uniek etiket, bepalen de hoeveelheid tijd om de steun uit te voeren, en beslissen of om op ononderbroken reservewijze te zijn

   Bepaal de hoeveelheid tijd die u wilt toewijzen om de back-up uit te voeren en bepaal of de formulierserver in de continue back-upmodus moet blijven.

1. Back-upmodus openen

   Ga reservewijze door de `enterBackupMode` methode met de volgende parameters aan te halen:

   * Een `String` waarde die een uniek, leesbaar label opgeeft dat de back-upmodussessie identificeert. U wordt aangeraden geen spaties of tekens te gebruiken die niet in XML-indeling kunnen worden gecodeerd.
   * Een `int` waarde die aangeeft hoeveel minuten er in de back-upmodus blijven. U kunt een waarde opgeven van `1` tot `10080` (het aantal minuten in een week). Deze waarde wordt genegeerd bij gebruik van de modus voor continue back-up.
   * Een `Boolean` waarde die aangeeft of de modus voor continue back-up moet worden geactiveerd. De waarde van `True` geeft aan dat de back-upmodus is geactiveerd. In de modus voor continue back-up wordt de waarde die u opgeeft voor het aantal minuten dat u in de back-upmodus wilt blijven, genegeerd.

      In de modus Continue back-up wordt een nieuwe back-upmodus gestart nadat de huidige sessie is voltooid. Een waarde van `False` betekent dat de continue back-upmodus niet wordt gebruikt en dat na het verlaten van de back-upmodus de bestanden uit de GDS worden gewist.

1. Informatie ophalen over de back-upmodussessie op de server

   Haal informatie op met het `BackupModeEntryResult` object dat wordt geretourneerd nadat u de `enterBackupMode` methode hebt aangeroepen. De informatie die u kunt terugwinnen nadat u reservewijze ingaat kan nuttig zijn om met uw reserveprocedures te integreren. Het label, de back-up-id en de begintijd kunnen bijvoorbeeld handig zijn als invoer voor bestandsnamen voor de back-upprocedure.

1. Maak een back-up van de GDS en de database

   Maak een back-up van de GDS (Global Document Storage) en de database waarmee de formulierserver is verbonden. De acties die u wilt uitvoeren voor de back-up maken geen deel uit van de AEM Forms SDK en kunnen zelfs handmatige stappen bevatten die specifiek zijn voor de back-upprocedures in uw organisatie.

### Back-upmodus starten met de webservice-API {#enter-backup-mode-using-the-web-service-api}

Voer de back-upmodus in met behulp van de webservice van de API voor back-up en herstel:

1. Projectbestanden opnemen

   * Creeer een de cliëntassemblage van Microsoft .NET die de Steun en herstelt de Dienst API WSDL gebruikt.
   * Verwijs naar de cliëntassemblage van Microsoft .NET.

1. Een BackupService Client API-object maken

   Gebruikend de de cliëntassemblage van Microsoft .NET, creeer een `BackupServiceService` voorwerp door zijn standaardaannemer aan te halen en specificeer de geloofsbrieven gebruikend de `Credentials` methode.

1. Beslissen op een uniek etiket, bepalen de hoeveelheid tijd om de steun uit te voeren, en beslissen of om op ononderbroken reservewijze te zijn

   Bepaal de hoeveelheid tijd die u wilt toewijzen om de back-up uit te voeren en bepaal of de formulierserver in de continue back-upmodus moet blijven.

1. Back-upmodus openen

   Als u de back-upmodus wilt inschakelen, roept u de methode enterBackupMode aan en geeft u de volgende waarden door:

   * Een `String` waarde die een uniek, leesbaar label opgeeft dat de back-upmodussessie identificeert. U wordt aangeraden geen spaties of tekens te gebruiken die niet in XML-indeling kunnen worden gecodeerd.
   * Een `Uint32` waarde die het aantal minuten aangeeft dat u in de back-upmodus wilt blijven. U kunt een waarde opgeven van `1` tot `10080` (aantal minuten in een week). Deze waarde wordt genegeerd bij gebruik van de modus voor continue back-up.
   * Een `Boolean` waarde die aangeeft of de modus voor continue back-up moet worden geactiveerd. De waarde van `True` geeft aan dat de back-upmodus is geactiveerd. In de modus voor continue back-up wordt de waarde die u opgeeft voor het aantal minuten dat u in de back-upmodus wilt blijven, genegeerd. In de modus Continue back-up wordt een nieuwe back-upmodus gestart nadat de huidige sessie is voltooid.

      Een waarde van `False` betekent dat de continue back-upmodus niet wordt gebruikt en dat na het verlaten van de back-upmodus de bestanden uit de GDS worden gewist.

1. Informatie ophalen over de back-upmodussessie op de server

   Haal informatie op over de back-upmodussessie nadat u de enterBackupMode-methode hebt aangeroepen vanuit de BackupModeEntryResult die is geretourneerd om te controleren of deze is gelukt. De informatie die u kunt terugwinnen nadat u reservewijze ingaat kan nuttig zijn om met uw reserveprocedures te integreren. Het label, de back-up-id en de begintijd kunnen bijvoorbeeld handig zijn als invoer voor bestandsnamen voor de back-upprocedure.

1. Maak een back-up van de GDS en de database

   Maak een back-up van de GDS (Global Document Storage) en de database waarmee de formulierserver is verbonden. De acties die u wilt uitvoeren voor de back-up maken geen deel uit van de AEM Forms SDK en kunnen zelfs handmatige stappen bevatten die specifiek zijn voor de back-upprocedures in uw organisatie.

## Back-upmodus op de formulierserver laten staan {#leaving-backup-mode-on-the-forms-server}

U verlaat de back-upmodus, zodat de formulierserver bestanden hervat van de GDS (Global Document Storage) op de formulierserver.

Voordat u toepassingen schrijft om naar de modus Verlaten te gaan, is het raadzaam de back-upprocedures te begrijpen die met AEM Forms worden gebruikt. Voor meer informatie over wat te overwegen wanneer het uitvoeren van steunen voor Vormen AEM, zie [beleidshulp](https://www.adobe.com/go/learn_aemforms_admin_63).

>[!NOTE]
>
>Zie [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63)voor meer informatie over de service Back-up en herstel.

### Overzicht van de stappen {#summary_of_steps-1}

Voer de volgende stappen uit om de back-upmodus te verlaten:

1. Inclusief projectbestanden.
1. Maak een BackupService-clientobject.
1. Laat de back-upmodus staan.
1. (Optioneel) Haal informatie op over de back-upmodussessie die op de formulierserver werd uitgevoerd.

**Projectbestanden opnemen**

Neem alle benodigde bestanden op in uw ontwikkelingsproject. Deze bestanden zijn belangrijk voor het correct compileren van uw code en het gebruik van de API voor back-up- en herstelservice.

Zie [Including AEM Forms Java library files](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)voor informatie over de locatie van deze bestanden.

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
   * jbossall-client.jar (vereist als AEM-formulieren worden geïmplementeerd op JBoss Application Server)

1. Een BackupService Client API-object maken

   U gebruikt een `ServiceClientFactory` object en het client-API-object BackupService samen.

   * Maak een `ServiceClientFactory` object dat verbindingseigenschappen bevat. (Zie Verbindingseigenschappen [instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)
   * Maak een `BackupService` object door de constructor ervan te gebruiken en het `ServiceClientFactory` object als parameter door te geven.

1. Back-upmodus openen

   Laat de back-upmodus staan door de `leaveBackupMode` methode aan te roepen.

1. Informatie ophalen over de back-upmodussessie op de server

   Haal informatie op over de bewerking met het `BackupModeResult` object dat wordt geretourneerd. De informatie die u kunt terugwinnen nadat u reservewijze ingaat kan nuttig zijn om met uw reserveprocedures te integreren. Het label, de back-up-id en de begintijd kunnen bijvoorbeeld handig zijn als invoer voor bestandsnamen voor de back-upprocedure.

### Back-upmodus verlaten met de webservice-API {#leave-backup-mode-using-the-web-service-api}

Maak een back-upmodus met de API voor back-up en herstel (webservice):

1. Projectbestanden opnemen

   Als u webservices wilt gebruiken, moet u ervoor zorgen dat u de proxybestanden opneemt. Voer de volgende stappen uit om uw project te configureren voor het gebruik van de API voor back-up en herstel als webservice.

   * Creeer een de cliëntassemblage van Microsoft .NET die de Steun en herstelt de Dienst API WSDL gebruikt.
   * Verwijs naar de cliëntassemblage van Microsoft .NET.

1. Een BackupService Client API-object maken

   Gebruikend de de cliëntassemblage van Microsoft .NET, creeer een `BackupServiceService` voorwerp door zijn standaardaannemer aan te halen.

1. Back-upmodus openen

   Maak een back-upmodus door de bewerking voor de `leaveBackupMode` webservice aan te roepen.

1. Informatie ophalen over de back-upmodussessie op de server

   Haal de id van de back-upmodus na de bewerking op om te controleren of deze is gelukt. De informatie die u kunt terugwinnen nadat u reservewijze verlaat kan nuttig zijn om met uw reserveprocedures te integreren.

