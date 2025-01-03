---
title: Servicemontages configureren
description: Leer hoe te om de dienstmontages te vormen. U kunt de pagina van het Beheer van de Dienst voor het vormen van de montages voor elk van de diensten gebruiken die deel van AEM vormen uitmaken.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_services
products: SG_EXPERIENCEMANAGER/6.4/FORMS
exl-id: a6a10ff0-6f4d-42df-9b4e-f98a53cf1806
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Workbench
role: User, Developer
source-git-commit: 6a9806d8f40f711a610c130c63d9ab9b2460d075
workflow-type: tm+mt
source-wordcount: '10836'
ht-degree: 0%

---

# Servicemontages configureren {#configure-service-settings}

>[!NOTE]
> 
> Zorg ervoor dat de gebruiker beheerdersrechten heeft om toegang te krijgen tot de beheerdersconsole.

U kunt de pagina van het Beheer van de Dienst gebruiken om montages voor elk van de diensten te vormen die deel van AEM vormen uitmaken. De beschikbare montages variëren afhankelijk van de dienst die wordt gevormd.

1. Klik in de beheerconsole op Services > Toepassingen en services > Servicebeheer.
1. Stop de service voordat u deze wijzigt. (Zie [ Beginnend en tegenhoudend de diensten ](/help/forms/using/admin-help/starting-stopping-services.md#starting-and-stopping-services).)
1. Klik de naam van de dienst die u wilt vormen.
1. Als de dienst een lusje van de Configuratie heeft, gebruik het om de montages voor de dienst te veranderen. Zie de onderstaande lijst met koppelingen voor meer informatie.

   >[!NOTE]
   >
   >Niet hebben alle diensten die op de pagina van het Beheer van de Dienst worden vermeld een Configuratie tabel. Voor processen die u hebt gecreeerd, verschijnt het lusje van de Configuratie slechts als u een configuratieparameter aan het proces in Workbench hebt toegevoegd. (Zie &quot;de parameters van de Configuratie&quot;in de [ Hulp Workbench ](https://www.adobe.com/go/learn_aemforms_workbench_63).)


1. Klik op het tabblad Beveiliging en stel de beveiligingsinstellingen voor de service in. Zie [ Wijzigend veiligheidsmontages voor de dienst ](configure-service-settings.md#modifying-security-settings-for-a-service).
1. Als de dienst een lusje van Eindpunten heeft, gebruik het om de eindpuntmontages te veranderen. Zie [ het Leiden Eindpunten ](/help/forms/using/admin-help/adding-enabling-modifying-or-removing.md).
1. Klik op het tabblad Pooling en stel de instellingen voor pooling in. Zie [ het Vormen het groeperen voor de dienst ](configure-service-settings.md#configuring-pooling-for-a-service).
1. Klik op Opslaan om de wijzigingen op te slaan of klik op Annuleren om de wijzigingen te verwijderen.
1. Schakel het selectievakje naast de servicenaam in en klik op Start om de service opnieuw te starten.

## Instellingen voor workflowservice controleren {#audit-workflow-service-settings}

Workbench biedt de mogelijkheid om procesinstanties op te nemen terwijl ze bij uitvoering worden uitgevoerd en deze vervolgens af te spelen om het gedrag van het proces te observeren. (Zie [ Hulp Workbench ](https://www.adobe.com/go/learn_aemforms_workbench_63).) om ruimte op het het dossiersysteem van de Server van Forms te besparen, kunt u de hoeveelheid gegevens van de procesopname beperken die wordt opgeslagen. U kunt de volgende eigenschappen van de service Audit Workflow Service ( `AuditWorkflowService` ) configureren:

**maxNumberOfRecordingInstances:** het maximumaantal opnamen dat wordt opgeslagen. Wanneer het maximumaantal wordt opgeslagen, wordt de oudste opname verwijderd uit het dossiersysteem wanneer een nieuwe opname wordt gecreeerd. Deze eigenschap is handig als u veel opnamen wilt maken en oude opnamen automatisch wilt verwijderen. De standaardwaarde is 50.

**MaxNumberOfRecordingEntry:** het maximumaantal gegevensingangen die voor elke opname kunnen worden opgeslagen. Gegevensinvoer is informatie over bewerkingen in het proces. Verschillende ingangen worden opgeslagen voor elke uitvoering van een verrichting, zoals of de verrichting begon, of de verrichting voltooide, en of de route die tot de verrichting leidt volledig is. Deze eigenschap is nuttig wanneer processen veel bewerkingen kunnen bevatten, bijvoorbeeld wanneer een eindeloze lus wordt aangetroffen. De standaardwaarde is 50.

## service-instellingen voor streepjescodes {#barcoded-forms-service-settings}

Met de service voor streepjescodes `(BarcodedFormsService)` haalt u streepjescodegegevens uit gescande afbeeldingen. De service accepteert een formulier met streepjescodes (TIFF of PDF) als invoer en extraheert de machinale weergave van de gegevens die door de streepjescode zijn gecodeerd.

De volgende instellingen zijn beschikbaar voor de service voor formulieren met streepjescodes.

**Gelezen Linker:** wanneer geselecteerd, worden de beelden van de streepjescode horizontaal van rechts naar links gescand.

**Gelezen Rechts:** wanneer geselecteerd, worden de beelden van de streepjescode horizontaal van links naar rechts gescand.

**Lees omhoog:** wanneer geselecteerd, worden de streepjescodebeelden verticaal gescand van onder aan bovenkant.

**Gelezen neer:** wanneer geselecteerd, worden de beelden van de streepjescode verticaal gescand van boven naar onder.

>[!NOTE]
>
>Standaard zijn alle opties geselecteerd. Schakel een optie alleen uit als u zeker weet dat er op uw formulieren geen streepjescodes voorkomen.

**Weg van het Dossier van de Basis:** de dossierweg met betrekking tot waarvan de parameters van de partijinput en van het outputdossier voor de Baan van het Dossier van de Looppas van XML en de verrichtingen van de Baan van het Dossier van de Looppas worden opgelost. In gegroepeerde configuraties, moet de weg van het basisdossier een gedeelde plaats zijn van het dossiersysteem waaraan alle clusterknopen lees-schrijftoegang hebben.

**Naam van Gegevens Source:** De naam van gegevensbron wordt gebruikt om staat en geschiedenisinformatie over de banen van de partijverwerking te handhaven die. De opgegeven gegevensbron moet algemene (XA) transacties ondersteunen.

## Bridge-service voor centrale migratie (verouderd), instellingen {#central-migration-bridge-service-settings}

De Central Migration Bridge-service ( `CentralMigrationBridge` ) roept een subset van de Adobe Central Pro Output Server-functionaliteit (Central) aan, die de opdrachten JFMERGE, JFTRANS en XMLIMPORT bevat. Met Bridge-services voor centrale migratie kunt u de volgende Central-elementen opnieuw gebruiken in AEM formulieren:

* sjabloonontwerp (&amp;ast;.ifd)
* uitvoersjablonen (&amp;ast;.mdf)
* gegevensbestanden (&amp;ast;.dat-bestanden)
* preambule, bestanden (&amp;ast;.pre-bestanden)
* gegevensdefinitiebestanden (&amp;ast;.tdf)

De volgende instelling is beschikbaar voor de Central Migration Bridge-service.

**Centraal installeert Folder:** de folder waar Adobe Centraal 5.7 geïnstalleerd is.

## Content Repository Connector voor EMC Documentum service settings {#content-repository-connector-for-emc-documentum-service-settings}

Met de Content Repository Connector voor EMC Documentum Service ( `EMCDocumentumContentRepositoryConnector`) kunt u processen maken die interageren met inhoud die is opgeslagen in een Documentum repository.

De volgende instelling is beschikbaar voor de Content Repository Connector voor EMC Documentum service.

**Van de Objecten van de Verbinding van activa StandaardWeg:** het standaardgedeelte van de weg in de Documentum bewaarplaats voor het opslaan van het voorwerp van de Verbinding van Activa. Het feitelijke pad bestaat uit het standaardpad en de locatie van de formuliersjabloon in de opslagplaats voor AEM formulieren.

Als het standaardpad bijvoorbeeld is ingesteld op `/LiveCycleES/ConnectorforEMCDocumentum/AssetLinkObjects` en de formuliersjabloon is opgeslagen in een map `/Docbase/forms/` , wordt het object Asset Link opgeslagen op de volgende locatie:

`/LiveCycleES/ConnectorforEMCDocumentum/AssetLinkObjects/Docbase/forms/`

De standaardwaarde van deze instelling is `/LiveCycleES/ConnectorforEMCDocumentum/AssetLinkObjects` .

## Content Repository Connector voor IBM FileNet service settings {#content-repository-connector-for-ibm-filenet-service-settings}

Met de Content Repository Connector voor IBM FileNet kunt u processen maken die communiceren met inhoud die is opgeslagen in een IBM FileNet-opslagruimte.

De volgende instelling is beschikbaar voor de Content Repository Connector voor de IBM FileNet-service.

**Van de Objecten van de Verbinding van activa StandaardWeg:** het standaardgedeelte van de weg in de bewaarplaats FileNet van IBM voor het opslaan van het voorwerp van de Verbinding van Activa. Het feitelijke pad bestaat uit het standaardpad en de locatie van de formuliersjabloon in de opslagplaats voor AEM formulieren.

Als het standaardpad bijvoorbeeld is ingesteld op `/LiveCycleES/ConnectorforIBMFileNet/AssetLinkObjects` en de formuliersjabloon is opgeslagen in een map `/Docbase/forms/` , wordt het object Asset Link opgeslagen op de volgende locatie:

`/LiveCycleES/ConnectorforIBMFileNet/AssetLinkObjects/Docbase/forms/`

De standaardwaarde van deze instelling is `/LiveCycleES/ConnectorforIBMFileNet/AssetLinkObjects` .

## PDF-service-instellingen converteren {#convert-pdf-service-settings}

Met de service PDF converteren ( `ConvertPdfService` ) worden PDF-documenten geconverteerd naar PostScript en naar verschillende indelingen voor afbeeldingen (JPEG, JPEG 2000, PNG en TIFF). Het converteren van een PDF-document naar PostScript is handig voor afdrukken op basis van een onbeheerde server op elke PostScript-printer. Het omzetten van een PDF-document in een TIFF-bestand met meerdere pagina&#39;s is handig bij het archiveren van documenten in inhoudsbeheersystemen die geen ondersteuning bieden voor PDF-documenten.

De volgende instellingen zijn beschikbaar voor de service PDF converteren.

**Type van Transactie:** specificeert hoe een transactiecontext aan een verrichting zou moeten worden verspreid.

**Vereist:** steunt een transactiecontext als één bestaat; anders, wordt een nieuwe transactiecontext gecreeerd. Dit is de standaardwaarde.

**vereist Nieuw:** leidt altijd tot een nieuwe transactiecontext. Als er een actieve transactiecontext bestaat, wordt deze opgeschort.

**Tijd van de Transactie uit (in sec):** Het aantal seconden dat de onderliggende transactieleverancier zou moeten wachten alvorens een transactie terug te rollen die deze verrichting verpakt. Deze waarde wordt genegeerd als een bestaande transactiecontext wordt doorgegeven. De standaardwaarde is 180.

**de Resolutie van de Drempel voor Vloeiend maken (in dpi):** de beeldresolutie waaronder het gladmaken (of anti-aliasing) wordt toegepast op tekst, lijnkunst en beelden, als u &quot;toepast het Vloeiend maken aan&quot;opties voor die elementen hebt geselecteerd.

**ben het gladmaken op tekst toe:** controleert anti-aliasing van tekst. Schakel dit selectievakje uit als u het vloeiend maken van tekst wilt uitschakelen en tekst scherper en beter leesbaar wilt maken met een schermvergroting.

**past het gladmaken op LineArt toe:** past het gladmaken toe om abrupte hoeken in lijnen te verwijderen.

**ben het gladmaken op beelden toe:** past het gladmaken toe om abrupte veranderingen in beelden te minimaliseren.

## Distiller-service-instellingen {#distiller-service-settings}

Met de Distiller-service ( `DistillerService` ) worden PostScript-, Encapsulated PostScript- (EPS) en PRN-bestanden via een netwerk omgezet in PDF-bestanden.

De volgende instellingen zijn beschikbaar voor de Distiller-service.

**de Montages van Adobe PDF:** De volgende vooraf geconfigureerde montages worden toegepast op de geproduceerde PDF:

* Afdrukken met hoge kwaliteit
* Grote pagina&#39;s
* PDFA1b 2005 CMYK
* PDFA1b 2005 RGB
* PDFX1a 2001
* PDFX3 2002
* Drukperskwaliteit
* Kleinste bestandsgrootte
* Standaard

U kunt nieuwe instellingen maken via de gebruikersinterface van de PDF Generator.

**de Montages van de Veiligheid:** vooraf geconfigureerde veiligheidsmontages die op de geproduceerde documenten van de PDF worden toegepast. De standaardwaarde is Geen beveiliging. Maak beveiligingsinstellingen met PDF Generator en voer hier de instelling in.

**Grootte van de pool:** de aanvankelijke grootte van de pool. Wanneer de dienst van Distiller wordt opgesteld, wordt dit aantal gebruikt om het aantal instanties van de de dienstimplementatie te bepalen die worden gecreeerd en aan de vrije pool toegewezen wachtend op aanroepingsverzoeken. De de dienstcontainer kan dan onmiddellijk aan aanroepingsverzoeken antwoorden zonder het moeten een de dienstinstantie eerst initialiseren.

## Documentbeheerservice-instellingen {#document-management-service-settings}

>[!NOTE]
>
>Adobe® LiveCycle® Content Services ES (Afgekeurd) is een contentbeheersysteem dat met LiveCycle is geïnstalleerd. Hiermee kunnen gebruikers processen ontwerpen, beheren, bewaken en optimaliseren die op mensen zijn gericht. De ondersteuning voor Content Services (Afgekeurd) eindigt op 31-12-2014. Zie {het document van de de levenscyclus van het 0} product van de Adobe ](https://www.adobe.com/support/products/enterprise/eol/eol_matrix.html).[

Met de service Documentbeheer ( `DocumentManagementService` ) kunnen processen de functionaliteit voor inhoudsbeheer gebruiken die wordt geboden door Content Services (Afgekeurd). De verrichtingen van het Beheer van het document verstrekken basistaken die worden vereist om ruimten en inhoud in het systeem van het inhoudsbeheer te handhaven. Voorbeelden van dergelijke taken zijn kopiëren, verwijderen, verplaatsen, ophalen en opslaan, spaties en koppelingen maken en inhoudskenmerken ophalen en instellen.

De volgende instellingen zijn beschikbaar voor de service Documentbeheer.

**Regeling van de Opslag:** de regeling van de opslag waarin de inhoud wordt gevestigd. De standaardwaarde is de werkruimte.

**de Haven van HTTP:** de haven die wordt gebruikt om tot de Diensten van de Inhoud (Vervangen) toegang te hebben. De standaardwaarde is 8080.

## E-mailservice-instellingen {#email-service-settings}

E-mail wordt doorgaans gebruikt om inhoud te verspreiden of statusinformatie te verstrekken als onderdeel van een geautomatiseerd proces. Met de e-mailservice ( `EmailService` ) kunnen processen e-mailberichten ontvangen van een POP3- of IMAP-server en e-mailberichten verzenden naar een SMTP-server.

Een proces gebruikt bijvoorbeeld de e-mailservice om een e-mailbericht met een PDF-formulierbijlage te verzenden. De e-mailservice maakt verbinding met een SMTP-server om het e-mailbericht met de bijlage te verzenden. Het formulier PDF is zo ontworpen dat de ontvanger op Indienen klikt nadat het formulier is ingevuld. Door deze actie wordt het formulier als bijlage teruggestuurd naar de opgegeven e-mailserver. De e-mailservice haalt het geretourneerde e-mailbericht op en slaat het ingevulde formulier op in een formuliervariabele met procesgegevens.

De volgende instellingen zijn beschikbaar voor de e-mailservice.

**SMTP Gastheer:** Het IP adres of URL van de server SMTP voor het verzenden van e-mail te gebruiken.

**SMTP Aantal van de Haven:** de haven wordt gebruikt om met de server te verbinden SMTP.

**SMTP verklaart voor authentiek:** selecteer als de gebruikersauthentificatie wordt vereist om met de server te verbinden SMTP.

**Gebruiker SMTP:** De gebruikersnaam van de gebruikersrekening aan login aan de server SMTP te gebruiken.

**Wachtwoord SMTP:** het wachtwoord dat met de SMTP gebruikersrekening wordt geassocieerd.

**SMTP de Veiligheid van het Vervoer:** het veiligheidsprotocol voor het verbinden met de server te gebruiken SMTP:

* Selecteer Geen als er geen protocol wordt gebruikt (gegevens worden in duidelijke tekst verzonden)
* Selecteer SSL als het Secure Sockets Layer-protocol wordt gebruikt.
* Selecteer TLS als de Veiligheid van de Laag van het Vervoer wordt gebruikt.

**POP3/IMAP Gastheer:** Het IP adres of URL van de POP3 of server IMAP voor het verzenden van e-mail te gebruiken.

**POP3/IMAP Gebruikersnaam:** De gebruikersnaam van de gebruikersrekening aan gebruik om in POP3 of server te registreren IMAP.

**POP3/IMAP Wachtwoord:** het wachtwoord dat met POP3 of IMAP gebruikersrekening wordt geassocieerd.

**POP3/IMAP het Aantal van de Haven:** de haven wordt gebruikt om met POP3 te verbinden of server IMAP.

**POP3/IMAP:** het protocol voor het verzenden van en het ontvangen van e-mail te gebruiken.

**ontvang de Veiligheid van het Vervoer:** het veiligheidsprotocol om voor het verbinden met de server te gebruiken SMTP:

* Selecteer Geen als er geen protocol wordt gebruikt (gegevens worden in duidelijke tekst verzonden).
* Selecteer SSL als het Secure Sockets Layer-protocol wordt gebruikt.
* Selecteer TLS als de Veiligheid van de Laag van het Vervoer wordt gebruikt.

## Instellingen voor versleutelingsservice {#encryption-service-settings}

Met de coderingsservice ( `EncryptionService` ) kunt u documenten versleutelen en decoderen. Wanneer een document wordt versleuteld, wordt de inhoud ervan onleesbaar. Een geautoriseerde gebruiker kan het document decoderen om toegang tot de inhoud te krijgen. Als een PDF-document met een wachtwoord is versleuteld, moet de gebruiker het wachtwoord voor openen opgeven voordat het document in Adobe Reader of Adobe Acrobat kan worden weergegeven. Als een PDF-document met een certificaat is versleuteld, moet de gebruiker het PDF-document decoderen met de openbare sleutel die overeenkomt met het certificaat (de persoonlijke sleutel) waarmee het PDF-document is versleuteld.

De volgende instellingen zijn beschikbaar voor de coderingsservice.

**StandaardServer LDAP om met te verbinden:** de naam van de Gastheer LDAP die wordt gebruikt om certificaten voor documentencryptie terug te winnen.

**StandaardHaven LDAP om met te verbinden:** Aantal van de Haven van LDAP server.

**StandaardNaam van Gebruiker LDAP:** als de server LDAP authentificatie vereist, specificeer de gebruikersnaam die moet worden gebruikt om met de server te verbinden LDAP.

**StandaardWachtwoord LDAP:** als de server LDAP authentificatie vereist, specificeer het wachtwoord dat met de gebruikersnaam beantwoordt die moet worden gebruikt om met de server te verbinden LDAP.

>[!NOTE]
>
>Gebruik alleen eenvoudige verificatie (gebruikersnaam en wachtwoord) wanneer de verbinding is beveiligd via SSL (met LDAPS).

<!-- **Compatibility Mode:**-->

## FTP-service-instellingen {#ftp-service-settings}

Met de FTP-service ( `FTP` ) kunnen processen communiceren met een FTP-server. Met FTP-services kunnen bestanden worden opgehaald van de FTP-server, bestanden op de FTP-server worden geplaatst en bestanden van de FTP-server worden verwijderd. Documenten, zoals rapporten die zijn gegenereerd op basis van een proces, kunnen bijvoorbeeld worden opgeslagen op een FTP-server voor distributie. Een extern systeem kan ook bestanden genereren op basis van eerdere stappen in een proces. In een volgende stap in het proces kunnen de bestanden naar een externe locatie worden overgebracht.

De volgende instellingen zijn beschikbaar voor de FTP-service.

**Standaardgastheer:** Het IP adres of URL van de server van FTP.

**Standaardhaven:** de haven die wordt gebruikt om met de server van FTP te verbinden. De standaardwaarde is 21.

**Standaard gebruikersbenaming:** de naam van de gebruikersrekening die u kunt gebruiken om tot de server van FTP toegang te hebben. De gebruikersaccount moet voldoende rechten hebben om de FTP-bewerkingen uit te voeren die deze service vereist.

**Standaardwachtwoord:** het wachtwoord met de gespecificeerde gebruikersnaam voor het voor authentiek verklaren met de server van FTP te gebruiken.

## Instellingen voor PDF-service genereren {#generate-pdf-service-settings}

Met de service PDF genereren ( `GeneratePDFService` ) worden bestanden in verschillende native indelingen geconverteerd naar PDF-documenten en worden PDF-documenten geconverteerd naar verschillende bestandsindelingen.

De volgende montages zijn beschikbaar voor de Generate dienst van PDF.

**de Montages van Adobe PDF:** De naam van de vooraf geconfigureerde montages van Adobe PDF om op een omzettingsbaan van toepassing te zijn, als deze montages niet als deel van de API oproepingsparameters worden gespecificeerd. De Adobe PDF-instellingen worden geconfigureerd in de beheerconsole door te klikken op Services > PDF Generator > Adobe PDF Settings. Deze instellingen zijn alleen van toepassing op conversies op basis van PDFMaker.

**de Montages van de Veiligheid:** De naam van de pre-gevormde veiligheidsmontages om op een omzettingsbaan van toepassing te zijn, als deze montages niet als deel van de API oproepingsparameters worden gespecificeerd. De beveiligingsinstellingen worden geconfigureerd in de beheerconsole door te klikken op Services > PDF Generator > Beveiligingsinstellingen.

**het type van Dossier Montages:** De naam van het vooraf gevormde Type dat van Dossier plaatst om op een omzettingsbaan van toepassing te zijn, als deze montages niet als deel van de API aanroepingsparameters worden gespecificeerd. De instellingen voor bestandstypen worden geconfigureerd in de beheerconsole door te klikken op Services > PDF Generator > Instellingen voor bestandstypen.

**WebCapture van het Gebruik (Vensters slechts):** wanneer dit het plaatsen waar is, produceert de dienst van PDF Acrobat voor alle HTML aan PDF omzettingen gebruikt. Dit kan de kwaliteit van de PDF dossiers verbeteren die van HTML worden geproduceerd, hoewel de prestaties lichtjes kunnen lager zijn. De standaardwaarde is false.

**Primaire omzetter voor HTML in de omzettingen van PDF:** de Generate dienst van PDF verstrekt veelvoudige routes om de dossiers van HTML naar de documenten van PDF om te zetten: Webkit, WebCapture (Vensters slechts), en WebToPDF. Met deze instelling kan de gebruiker de primaire converter selecteren die HTML in PDF omzet. De WebToPDF is standaard geselecteerd.

**omzetter van de Fallback voor HTML aan PDF omzettingen:** specificeer omzetter voor HTML aan PDF omzettingen als de primaire omzetter ontbreekt. Standaard is WebCapture (alleen Windows) geselecteerd.

**Conversie van het Beeld van Acrobat van het Gebruik (Vensters slechts):** wanneer dit het plaatsen waar is, produceert de dienst van de PDF Acrobat voor al Beeld aan PDF conversies gebruikt. Deze instelling is alleen handig als het standaard conversiemechanisme voor zuiver Java een aanzienlijk deel van de invoerafbeeldingen niet kan converteren. De standaardwaarde is false.

**laat op Acrobat-Gebaseerde Conversies AutoCAD (Vensters slechts) toe:** wanneer dit het plaatsen waar is, produceert de dienst van de PDF Acrobat voor alle DWG aan PDF omzettingen gebruikt. Deze instelling is alleen handig als AutoCAD niet op de server is geïnstalleerd of als het conversiemechanisme van AutoCAD bestanden niet kan converteren.

**regelmatige uitdrukkingen voor het vinden van verboden speciaal
Tekens in de Naam van de Gebruiker (Vensters slechts):** Specificeert karakters die zich in de Export PDF en de verrichtingen van de Optimize PDF mengen wanneer de karakters in de naam van een gebruiker verschijnen.

**grootte van de Pool ImageToPDF:** de poolgrootte van standaard (zuivere Java) beeld-aan-PDF converter in de Generate dienst van de PDF. Met deze instelling bepaalt u de maximale gelijktijdige omzetting van afbeelding in PDF die de service PDF genereren kan uitvoeren. De standaardwaarde van deze instelling (aanbevolen voor systemen met één processor) is 3, die u kunt verhogen voor systemen met meerdere processors.

**HTML aan de Grootte van de Pool van de PDF:** de poolgrootte van HTML aan-PDF converter in de Generate dienst van PDF. Deze instelling bepaalt de maximale gelijktijdige HTML-naar-PDF-omzettingen die de dienst PDF genereren kan uitvoeren. De standaardwaarde van deze instelling (aanbevolen voor systemen met één processor) is 3, die u kunt verhogen voor systemen met meerdere processors.

**OCR Pool Grootte:** de poolgrootte van PaperCaptureService die de PDF Generator voor OCR gebruikt. De standaardwaarde van deze instelling (aanbevolen voor systemen met één processor) is 3, die u kunt verhogen voor systemen met meerdere processors. Deze instelling is alleen geldig op Windows-systemen.

**ImageToPDF maximum pagina&#39;s in geheugen voor de omzettingen van TIFF:** Dit het plaatsen bepaalt het maximumaantal pagina&#39;s van een beeld van TIFF dat in geheugen kan blijven alvorens aan schijf tijdens omzetting in PDF wordt gespoeld. De standaardwaarde voor deze instelling is 500, die kan worden verhoogd als meer geheugen wordt toegewezen aan het ImageToPDF-converterproces.

**Familie van de Font van de Terugval voor HTML aan de Conversies van PDF:** De naam van de doopvontfamilie aan gebruik in de documenten van PDF wanneer de doopvont die in originele HTML wordt gebruikt niet beschikbaar aan de Server van AEM Forms is. Geef een lettertypefamilie op als u HTML-pagina&#39;s wilt converteren waarin niet-beschikbare lettertypen worden gebruikt. Pagina&#39;s die zijn geschreven in regionale talen kunnen bijvoorbeeld niet-beschikbare lettertypen gebruiken.

**probeert Logica voor Inheemse Omzettingen** opnieuw van de Generatie van PDF als de eerste poging tot omzetting heeft ontbroken:

* **niet opnieuw probeert**

  Voer de PDF-conversie niet opnieuw uit als de eerste omzetpoging is mislukt

* **opnieuw**

  Voer de PDF-conversie opnieuw uit, ongeacht of de time-outdrempel is bereikt. De standaardtijdsduur voor de eerste poging is 270 seconden.

* **probeer opnieuw als de tijd** toelaat

  Voer de PDF-conversie opnieuw uit als de tijd die voor de eerste omzetpoging is verbruikt, korter was dan de opgegeven time-outduur. Als de time-outduur bijvoorbeeld 270 seconden is en de eerste poging 200 seconden heeft geduurd, zal de PDF Generator de conversie hervatten. Als de eerste poging zelf 270 seconden heeft geduurd, wordt de conversie niet opnieuw uitgevoerd.

## Instellingen voor hulplijnen ES4-hulpprogramma&#39;s {#guides-es4-utilities-service-settings}

Wanneer u een Guide maakt, worden sommige bronnen, zoals de definitie van de Guide, ingesloten in de Guide. Bronnen kunnen ook bestaan als verwijzingen naar toepassingselementen die lokaal of op de AEM Forms-server zijn opgeslagen. De Guide bevat geen gegevens en de waarden voor de verzendlocatie en -invoer zijn niet geschikt voor alle externe omgevingen.

In de meeste gevallen zijn de standaardservices voor het weergeven van hulplijnen voldoende om een hulplijn voor te bereiden voor gebruik in Workspace of andere externe omgevingen. (In de mening van de Diensten, in Workbench, is de standaarddienst Gidsen (systeem)/Processes/Gids van de Rendering - 1.0.) Met de Guide Utilities Service ( `GuidesUtility` ) kunt u, indien nodig, een aangepast proces maken voor het renderen van een Guide.

Met de bewerkingen Hulplijnhulpprogramma kunt u de volgende renderingstaken voor hulplijnen aan een proces toevoegen:

* Bepaal of er gegevens beschikbaar zijn om de Guide te vullen
* De gegevens van de Guide insluiten of converteren naar een koppeling
* Inhoud waarnaar wordt verwezen, converteren naar URL&#39;s die extern toegankelijk zijn
* Vervangende waarden in een HTML-document of andere omslag, of zet ze om in extern toegankelijke URL&#39;s
* Verzendlocatie instellen
* Invoerwaarden opgeven
* Een parameter maken om inhoud waarnaar wordt verwezen te vertegenwoordigen
* Als er variaties beschikbaar zijn, stelt u een variatie in

De standaardwaarden voor de Guide Utilities-service ondersteunen de meeste gevallen van gebruik. Indien nodig kunt u echter de volgende waarden wijzigen.

**publicPaths:** Deze optie is afgekeurd. Gebruik deze optie niet bij AEM formulieren.

**pathInfoExpiryInSeconds:** het interval waarna een verzoek om weginformatie van een cliënt verloopt. De standaardwaarde is 1.

**gebruikt_alsExpiryInSeconds:** Het interval waarna een verzoek om onderpand van een cliënt verloopt. De standaardwaarde is 315576000.

**mismatchExpiryInSeconds:** het interval waarna een verzoek om onderpand van een cliënt verloopt, wanneer eTag (entiteitmarkering) niet aanpast. (Een eTag is een HTTP-antwoordheader.) De standaardwaarde is 1.

**guideContext:** de contextwortel van de het Webtoepassing van Gidsen. Komt overeen met de waarde die is ingesteld met de webtoepassing Hulplijnen. Standaard is /Guides/.

**secureRandomAlgorithm:** het algoritme om te gebruiken wanneer het produceren van sleutels en herkenningstekens. Deze waarde wordt overgegaan tot de getInstance methode van de SecureRandom klasse van Java. Standaard is SHA1PRNG.

**idBytes:** het aantal willekeurige bytes aan gebruik voor een zeer belangrijke herkenningsteken. De standaardwaarde is 6.

**macAlgorithm:** het algoritme van MAC (de code van de berichtauthentificatie) voor onderpandURL controle te gebruiken. Deze methode wordt doorgegeven aan de methode getInstance van de klasse Mac. Standaard is HmacSHA1.

**macRefreshIntervalInMinutes:** De hoeveelheid tijd een sleutel actief is. Wanneer een sleutel voor dit interval actief is geweest, wordt een nieuwe sleutel geproduceerd. De nieuwe toets wordt de actieve toets. De eerder actieve sleutel wordt bewaard voor 10% van het vernieuwingsinterval. Dit gedrag staat URLs toe die door de oude sleutel te gebruiken worden geproduceerd om over de belangrijkste schakelaar te blijven werken. De standaardwaarde is 144000.

**macOverlapIntervalInMinutes:** Tijdsduur dat de vorige sleutel geldig zal blijven nadat nieuwe wordt geproduceerd. De standaardwaarde is 1440 minuten (1 dag).

**macKeySeed:** een zaadwaarde voor het produceren van veilige URL. Wanneer deze optie is, wordt de sleutel nooit verfrist. Als u hetzelfde zaad op verschillende servers instelt, genereren die servers veilige URL&#39;s die compatibel zijn. Dit kan handig zijn als er meerdere formulierservers worden gebruikt achter een taakverdelingsmechanisme. Voer een willekeurige reeks tekens en getallen in als het zaad.

### Hulplijnen gebruiken in een servercluster {#using-guides-in-a-server-cluster}

Het renderen van een Guide in een servercluster die geen kleverige sessies gebruikt, mislukt met een NullPointerException. Een verzoek van Gidsen gebruikt veilige URLs die, door gebrek, aan de server uniek zijn zij worden geproduceerd. In een cluster die kleverige zittingen gebruikt, nadat een verzoek een knoop in de cluster raakt, worden alle verdere verzoeken voor die zitting of gebruiker verpletterd exclusief aan die server, en alles is ok. In een cluster waarin geen kleverige sessies worden gebruikt, kunnen volgende aanvragen worden uitgevoerd op elke server in de cluster. Als de server waarop de aanvragen betrekking hebben, niet de oorspronkelijke server is, wordt de beveiligde URL niet opgelost.

Als u Gidsen in een servercluster gebruikt die geen kleverige zittingen gebruikt, plaats de macKeySeed waarde voor de dienst GuidesUtility, en stop en begin dan de cluster.

De macKeySeed-waarde is het zaad voor de random number generator die wordt gebruikt om de veilige URL&#39;s te genereren. Het plaatsen van deze waarde veroorzaakt elke clusterknoop om de willekeurige aantalgenerator op de zelfde manier te initialiseren, en toegang tot zelfde veilige URLs te hebben. U kunt elke willekeurige tekenreeks voor deze zaadwaarde gebruiken.

Wijzig de macKeySeed-waarde wanneer u de beveiligde URL&#39;s moet vernieuwen. Het vernieuwen van veilige URLs hangt van uw veiligheidsbeleid af, en is gelijkaardig aan verfrist beleid voor het veranderen van het hoofdwortelwachtwoord van de server. De macSeedValue is analoog aan het hoofdwachtwoord voor veilige URLs, omdat het wordt gebruikt om een nieuw uniek willekeurig aantal voor gebruik in veilige het produceren van URL en herwinning te produceren.

Start de cluster opnieuw omdat macSeedValue alleen-lezen is bij het opstarten van het systeem. Alle knopen moeten opnieuw beginnen om de waarde te lezen, omdat zij het onafhankelijk gebruiken om hun interne willekeurige aantallen met de zaadwaarde te initialiseren.

## JDBC-service-instellingen {#jdbc-service-settings}

Met de JDBC-service ( `JdbcService` ) kunnen processen communiceren met databases.

De volgende instelling is beschikbaar voor de JDBC-service.

**datasourceName:** een koordwaarde die de naam JNDI van de gegevensbron vertegenwoordigt om met de gegevensbestandserver te gebruiken te verbinden. De gegevensbron moet op de toepassingsserver worden bepaald die gastheren de Server van Forms. De standaardwaarde is de JNDI-naam van de gegevensbron voor de AEM formulierdatabase.

## JMS-service-instellingen {#jms-service-settings}

De dienst JMS ( `JMS`) laat interactie met de leveranciers van het Systeem van het Overseinen van Java (JMS) toe die zowel punt-aan-punt overseinen uitvoeren als overseinen publiceren/intekenen.

Configureer de JMS-service met standaardeigenschappen, zodat de servicebewerkingen verbinding kunnen maken met een JMS-provider en een bijbehorende JNDI-service. De waarden van de de diensteigenschappen worden geplaatst aan standaardwaarden die op de Server van de Toepassing JBoss worden gebaseerd. Wijzig deze waarden als u een andere toepassingsserver gebruikt om AEM formulieren te hosten.

De volgende instellingen zijn beschikbaar voor de JMS-service.

**Leverancier URL:** URL van de JNDI dienstverlener. De standaardwaarde is gebaseerd op de Server van de Toepassing JBoss. De volgende URL zijn standaardwaarden voor de toepassingsservers die AEM formulieren ondersteunen:

**JBoss:** `<server name>:1099`

**WebLogic:** `<server name>:7001`

**WebSphere:** `<server name>:2809`

**JNDI Gebruikersnaam:** De gebruikersnaam van de rekening om voor het voor authentiek verklaren met de JNDI dienstverlener te gebruiken die voor het opzoeken van rij en onderwerpnamen wordt gebruikt. De standaardwaarde is gast.

**JNDI Wachtwoord:** het wachtwoord dat met de gebruikersnaam wordt geassocieerd die voor Gebruikersnaam JNDI wordt gespecificeerd. De standaardwaarde is gast.

**Aanvankelijke Factory van de Context:** de klasse van Java als aanvankelijke contextfabriek te gebruiken. De dienst JMS gebruikt deze klasse om een aanvankelijke context tot stand te brengen, die het uitgangspunt voor het oplossen van namen van onderwerpen en rijen is. De standaardwaarde is de aanvankelijke contextfabriek voor de dienst JMS op JBoss. De volgende klassen zijn de eerste contextfabrieken voor de toepassingsservers die AEM formulieren ondersteunen:

**JBoss:** org.jnp.interfaces.NamingContextFactory

**weblogic.jndi.WLInitialContextFactory**

**WebSphere:** com.ibm.websphere.naming.WsnInitialContextFactory

**Gebruikersnaam van de Verbinding:** Het wachtwoord dat met de gebruikersnaam wordt geassocieerd die voor de Gebruikersnaam van de Verbinding wordt gespecificeerd. De standaardwaarde is gast.

**Wachtwoord van de Verbinding:** het wachtwoord dat met de gebruikersnaam wordt geassocieerd die voor de Gebruikersnaam van de Verbinding wordt gespecificeerd. De standaardwaarde is gast.

**Andere Eigenschappen:** de naam en waardeparen van het Bezit die u tot de JNDI dienstverlener kunt overgaan. Deze eigenschappen hangen van de implementatie en de configuratie van de leverancier af die u gebruikt.

De eigenschappen naam en waardeparen worden gescheiden door puntkomma&#39;s **;**. De volgende tekst toont bijvoorbeeld de waarde die zou worden opgegeven voor twee eigenschappen met de naam name1 en name2, met respectievelijk de waarden value1 en value2:

`name1=value1;name2=value2`

## LDAP-service-instellingen {#ldap-service-settings}

De LDAP-service ( `LDAPService` ) biedt bewerkingen voor het opvragen van LDAP-directory&#39;s. LDAP-directory&#39;s worden doorgaans gebruikt voor het opslaan van gegevens over de personen, groepen en services in een organisatie.

De volgende instellingen zijn beschikbaar voor de LDAP-service.

**Aanvankelijke Factory van de Context:** de klasse van Java als contextfabriek te gebruiken. Deze klasse wordt gebruikt om een verbinding met de LDAP-server te maken. De standaardwaarde is com.sun.jndi.ldap.LDAPCtxFactory, die geschikt is voor de meeste LDAP-servers.

**Leverancier URL:** URL om met de dienst te gebruiken te verbinden LDAP. De notatie van de waarde is `ldap://server name:port`

*servernaam* is de naam van de computer die gastheren de server LDAP

*haven* is de communicatie haven die de dienst LDAP gebruikt. De standaardwaarde is 389. Dit is de standaardpoort die wordt gebruikt voor LDAP-verbindingen.

**Naam van de Gebruiker:** De gebruikersnaam van de gebruikersrekening aan login aan de server LDAP te gebruiken. De gebruikersaccount moet toestemming hebben om verbinding te maken met de server en de gegevens in de LDAP-directory te lezen.

Afhankelijk van de LDAP-server kan de gebruikersnaam een eenvoudige gebruikersnaam zijn, zoals `myname` of een DN, zoals `cn=myname,cn=users,dc=myorg` .

**Wachtwoord:** het wachtwoord dat met de gebruikersnaam beantwoordt die voor het plaatsen van de Gebruikersnaam wordt verstrekt.

**Andere Eigenschappen:** een koordwaarde die andere eigenschappen en hun overeenkomstige waarden vertegenwoordigt die u aan de server kunt verstrekken LDAP. De waarde heeft de volgende notatie:

`property=value;property=value;...`

## Microsoft SharePoint-configuratieservice {#microsoft-sharepoint-configuration-service-settings}

Met de Microsoft SharePoint-configuratieservice `(MSSharePointConfigService)` kunt u referenties opgeven voor de gebruiker van AEM formulieren die imitatierechten heeft. Voor informatie over imitatierechten, zie [ Vormend de Schakelaar voor Microsoft SharePoint ](https://help.adobe.com/en_US/AEMForms/6.1/SharePointConfig/index.html).

De volgende instellingen zijn beschikbaar voor de Microsoft SharePoint-configuratieservice:

* Gebruikersnaam voor een gebruiker met imitatierechten
* Wachtwoord voor de bovenstaande gebruiker

**laat SSL (HTTPS) toe:**

**Tijd aan Levend:** Lengte van tijd, in seconden, dat dit inrichtingsprofiel geldig is en in het voorgeheugen ondergebracht op de cliënt. De standaardwaarde is 86400 (24 uur). Wanneer een clienttoepassing synchroniseert met de server en de opgegeven hoeveelheid tijd is verstreken, vraagt de clienttoepassing een nieuw inrichtingsprofiel aan bij de server.

**Encryptie:** specificeert of om gegevens te coderen die op het mobiele apparaat worden opgeslagen.

**Toepassing van Forms:** laat de eigenschap van Forms in de mobiele cliënttoepassingen toe. Als deze optie is geselecteerd, kunnen gebruikers formulieren openen en processen starten vanaf hun mobiele apparaten.

**Toepassing van Taken:** laat de eigenschap van Taken in de mobiele cliënttoepassingen toe. Als deze optie is geselecteerd, kunnen gebruikers hun taaklijsten openen en taken uitvoeren vanaf hun mobiele apparaten.

**de Toepassing van de Diensten van de Inhoud:** laat de eigenschap van de Diensten van de Inhoud in de mobiele cliënttoepassing toe. Deze functie is alleen beschikbaar voor iOS. Als deze optie is geselecteerd, hebben iPhone- en iPad-gebruikers toegang tot bestanden die zijn opgeslagen op de WebDAV-server van uw organisatie.

**Off-line Steun:** laat gebruikers toe om het gebruiken van de mobiele cliënttoepassingen voort te zetten zelfs wanneer zij geen verbinding aan de server hebben (bijvoorbeeld, wanneer zij uit celwaaier of op vliegtuigwijze zijn). Gebruikers moeten ook de instelling Offlineondersteuning op hun mobiele apparaten inschakelen. Deze functie is beschikbaar voor Android- en iOS-apparaten. Deze functie is standaard uitgeschakeld.

>[!NOTE]
>
>Als Offlineondersteuning is ingeschakeld en u deze vervolgens uitschakelt, worden de inrichtingsprofielen van de gebruikers direct of zodra ze online zijn, bijgewerkt. Als een gebruiker offline heeft gewerkt, worden alle hangende taken geretourneerd naar de lijst Taken en worden alle items in de wachtrij, inclusief formulieren, taken en formulieren met validatiefouten die in behandeling zijn, verwijderd uit de wachtrij.

**Android:** staat de apparaten van Android toe om met de server te verbinden.

**Apple iOS:** staat iPhones en iPads toe om met de server te verbinden.

**AIR:** staat apparaten die apps in werking stellen toe op Adobe AIR® worden gebaseerd om met de server te verbinden die.

**BlackBerry:** staat apparaten BlackBerry toe om met de server te verbinden.

**Android Microsoft Vereiste Uitwisseling ActiveSync:** specificeert of de het beleidsmanager van ActiveSync van de Uitwisseling ActiveSync van de Uitwisseling van Microsoft (EA) moet worden geïnstalleerd en op de apparaten van Android actief zijn. Als deze optie is geselecteerd, moet EA worden afgedwongen op het Android-apparaat. Wanneer deze optie niet is geselecteerd, wordt geen controle uitgevoerd, hoewel andere vereisten nog steeds worden afgedwongen.

**Minimale Lengte van de SPELD van Android:** de apparaten van Android moeten het globale plaatsen hebben die afdwingt dat de SPELD of het wachtwoord minstens deze lengte is. Het hebben van een SPELD van de gespecificeerde lengte is slechts niet voldoende. De lengte van de SPELD moet door het systeem worden afgedwongen zodat de gebruikers niet de SPELD kunnen later verwijderen of verkorten. De standaardwaarde is 4.

**het Maximumwachtwoord van Android wint voor Wipe opnieuw:** de apparaten van Android hebben het globale plaatsen die het systeem na een gespecificeerd aantal ongeldige wachtwoordpogingen veegt. Deze globale instelling ingeschakeld en gelijk aan of lager dan de hier opgegeven waarde. De standaardwaarde is 5.

**Sluitereffect van Android op Verwijdering:** specificeert wat gebeurt wanneer een beleidsschending op een apparaat van Android voorkomt. Als u deze optie selecteert, wordt het account verwijderd. Als deze optie niet is geselecteerd, worden het wachtwoord voor de opgeslagen account en de gegevens in de cache verwijderd. Er worden geen synchronisatiepogingen meer uitgevoerd totdat de gebruiker de beleidsovertreding heeft opgelost.

## Instellingen voor uitvoerservice {#output-service-settings}

Met de uitvoerservice `(OutputService)` kunt u XML-formuliergegevens samenvoegen met een formulierontwerp dat is gemaakt in AEM Designer, zodat een uitvoerstroom van het document in een van de volgende indelingen wordt gemaakt:

* Een PDF- of PDF/A-documentuitvoerstroom.
* Een Adobe PostScript-uitvoerstroom.
* Een PCL-uitvoerstroom (Printer Control Language).
* Een ZPL-uitvoerstroom (Zebra Programming Language).

De uitvoerstream kan naar een netwerkprinter, een lokale printer of een schijfbestand worden verzonden. Wanneer u de uitvoerservice gebruikt als onderdeel van een proces, kunt u de uitvoerstream ook als bestandsbijlage naar een e-mailontvanger verzenden.

De volgende instellingen zijn beschikbaar voor de service Uitvoer.

**Type van Transactie:** specificeert hoe een transactiecontext aan een verrichting zou moeten worden verspreid:

**Vereist:** steunt een transactiecontext als reeds bestaat; anders, wordt een nieuwe transactiecontext gecreeerd. Dit is de standaardwaarde.

**vereist Nieuw:** leidt altijd tot een nieuwe transactiecontext. Als er een actieve transactiecontext bestaat, wordt deze opgeschort.

**Tijd van de Transactie uit (in sec):** Het aantal seconden dat de onderliggende transactieleverancier wacht alvorens een transactie terug te rollen die deze verrichting verpakt. Deze waarde wordt genegeerd als een bestaande transactiecontext wordt verspreid.

Wanneer het verwerken van grote gegevensdossiers of werkend op een bezige server, kan het noodzakelijk zijn om de de diensttijd van de Output uit te verhogen. Als u de time-outwaarde wilt wijzigen, moet u ervoor zorgen dat de hardwareservers over voldoende geheugen beschikken en dat het geheugen beschikbaar is voor de Java Application Server-heap. De standaardwaarde is `180` .

## Instellingen van PDFG Config-service {#pdfg-config-service-settings}

De volgende instellingen zijn beschikbaar voor de service PDFG Config ( `PDFGConfigService` ).

**Folder van de Opties van de Baan van de Gebruiker:** De weg van de dossier-systeem omslag waar de dienst c de dossiers schrijft van baanopties die aan Acrobat Pro Uitgebreid toegankelijk zijn. De standaardwaarde is [ user.home ]/Application Data/Adobe/Adobe PDF/Settings.

**PS Opstartfolder:** De weg van de dossier-systeem omslag waar de startdossiers die door Adobe Acrobat Distiller worden vereist worden bewaard. De standaardwaarde is [ user.home ]/Application Data/Adobe/Adobe PDF/Distiller/Startup.

**PS Opstartdossier:** De naam van het startdossier dat door Adobe Acrobat Distiller wordt vereist. De standaardwaarde is example.ps.

**de Onderbreking van de Omzetting van de Server:** de maximumonderbreking van de baanomzetting (in seconden) voor de Generate dienst van PDF en de dienst van Distiller. Dit het plaatsen beperkt de maximumomzettingstijd die in het config.xml- dossier en in de pagina&#39;s van de beleidsconsole voor PDF Generator kan worden gespecificeerd. De standaardwaarde is 270.

**Globale Onderbreking van de Server:** terwijl het uitvoeren van PDF omzettingen, neemt een Server van Forms rekening met de onderbrekingsgrens. Vorm de onderbrekingswaarde om de kwestie op te lossen.

**Prefix van de Opties van de Baan:** Een prefix die door de Generate dienst van de PDF wordt gebruikt om een kort koord aan de dossiers van baanopties voor te bereiden die het tijdelijk voor gebruik door Acrobat Distiller leidt. De standaardwaarde is pdfg.

**nietUnicode Apps:** a komma-gescheiden lijst van toepassingsnamen die om Unicode-onbekwaam bekend zijn te zijn. Deze lijst is vooraf bevolkt met de namen van verscheidene toepassingen, steun waarvoor vooraf in PDF Generator wordt gevormd. Als u ervoor kiest ondersteuning voor PDF-conversies toe te voegen via andere toepassingen van derden die Unicode-niet kunnen gebruiken, moet u deze toevoegen aan deze lijst. De standaardwaarde is Autocad, Excel, PowerPoint, Project, Publisher, Visio, Word, WordPerfect.

**Aantal van de Verbinding van de Server Threadpool:** controleert de grootte van de draadpool die de dienst van de PDF intern aan de dienst HTML-aan-PDF omzettingsverzoeken gebruikt die het spinnen impliceren (het omzetten van verbonden pagina&#39;s toegankelijk van de belangrijkste pagina). De standaardwaarde is 20.

**Seconden van het Scannen PDFG van het Scannen:** zie de Sectie van de Verlopen van de Baan voor details.

**Seconden van de Vervalsing van de Baan:** de Generate dienst van PDF schrapt inputdossiers zodra zij worden omgezet. De uitvoerbestanden worden tijdelijk opgeslagen, gedurende een periode die wordt bepaald door de instellingen Seconden van PDFG-opschoning en Seconden voor taakvervaldatum.

Met de instelling Seconden voor taakvervaldatum bepaalt u hoe oud een bestand of lege map moet zijn voordat het bestand kan worden verwijderd. Met de instelling Seconden van PDFG Cleanup Scan bepaalt u hoe vaak de tijdelijke mappen door een opschoonthread worden gescand op bestanden die kunnen worden verwijderd.

Bijvoorbeeld, als de Seconden van de Vervalsing van de Baan aan 100 wordt geplaatst en de Seconden van het Scannen PDFG van de Schoonmaakbeurt aan 200 wordt geplaatst, stelt de schoonmaakdraad om de 200 seconden in werking en schrapt dossiers die 100 seconden of ouder zijn.

De standaardwaarde van de seconden van PDFG Cleanup Scan is `43200` (12 uur). De standaardwaarde van Seconden van de Vervaltijd van de Baan is `86400` (24 uren).

**StandaardLandinstelling:** Gebruikt om de standaardlandinstelling (land + taal) van de server met voeten te treden waar de dienst Generate PDF wordt opgesteld. Als deze parameter niet gespecificeerd is, dan wordt de standaardscène bepaald van het werkende systeem waarop de dienst wordt opgesteld. Deze parameter bestuurt de taal waarin de foutenmeldingen aan APIs zijn teruggekeerd.

## formulierworkflows voor Data Services-services {#forms-workflow-data-services-service-settings}

De volgende diensten breiden de Diensten van Gegevens uit en stellen assembleurs bloot die Workspace gebruikt om met de server te spreken. Wijzig de configuratieopties voor deze services niet, tenzij u hiervoor de instructie krijgt van de Adobe Support. Deze diensten zijn niet bedoeld voor directe toegang:

* `ProcessManagementLcdsAttachmentService`
* `ProcessManagementLcdsPropertyService`
* `ProcessManagementLcdsTaskService`

## Service-instellingen verwijderen {#remoting-service-settings}

De meeste services zijn zo geconfigureerd dat u ze kunt openen via het verwijderen van formulieren (Verouderd voor AEM formulieren) AEM formulieren. Voor informatie over (Vervangen voor AEM vormen) AEM vormen het Verwijderen, zie [ Programmerend met AEM vormen ](https://adobe.com/go/learn_aemforms_programming_63).

De volgende instellingen zijn beschikbaar voor de service Remoting.

**Methode van de Authentificatie van de Cliënt van Flex:** bepaalt het type van reactie dat de server terug naar de cliënt verzendt wanneer de aangehaalde dienst veiligheid toegelaten is, steunt de aangehaalde verrichting geen anonieme aanroepen, en de cliënt gaat in of geen of ongeldige geloofsbrieven over. Kies een optie in Aangepast of Standaard. De standaardwaarde is Standaard.

**staat rangschikking van niet-Serializable Klassen toe:** de meeste AEM vormeindpunten staan slechts Serializable klassen toe om voor aanroeping worden gebruikt. In oudere versies, stond het Remoting eindpunt niet-Serializable klassen toe om voor aanroeping van op Flex-Gebaseerde cliënten worden gebruikt. Om een beveiligingskwetsbaarheid te voorkomen die in APS11-15 wordt beschreven, is deze kwetsbaarheid gewijzigd. Als u niet-Serializable klassen met het Flex Remoting eindpunt wilt blijven gebruiken, selecteer dit checkbox.

## Instellingen voor opslagplaats {#repository-service-settings}

De dienst van de Bewaarplaats ( `RepositoryService`) verleent de opslag van middelen en beheersdiensten aan AEM vormen. Wanneer ontwikkelaars een toepassing maken, kunnen ze de elementen in de opslagplaats implementeren in plaats van in een bestandssysteem. De elementen kunnen elk type onderpand bevatten, zoals XML-formulieren, PDF forms (inclusief Acrobat-formulieren), formulierfragmenten, afbeeldingen, profielen, beleid, SWF-bestanden, DDX-bestanden, XML-schema&#39;s, WSDL-bestanden en testgegevens.

U kunt de standaardopslagplaats gebruiken die bij AEM formulieren wordt geleverd, of een externe opslagplaats gebruiken (EMC Documentum Content Server, IBM FileNet Content Manager of IBM Content Manager).

De dienst van de Leverancier van de opslagplaats is een de dienstafgevaardigde die als interface aan een leveranciersdienst dienst dienst dienst dienst doet. Hierdoor kunt u verbinding maken met een gemeenschappelijke API en hoeft u zich niet te realiseren welke provider de opslagmogelijkheden implementeert. De dienst van de Leverancier van de Bewaarplaats verstrekt gegevensbestandopslag voor de de dienstmiddelen van de Bewaarplaats.

De volgende instelling is beschikbaar voor de Repository-service.

**Dienst van de Leverancier:** De naam van de dienst die als opslagleverancier wordt gebruikt. De standaardwaarde is RepositoryProviderService.

## Instellingen voor handtekeningenservice {#signature-service-settings}

Met de service Handtekening ( `SignatureService` ) kan uw organisatie de beveiliging en privacy beschermen van Adobe PDF-documenten die worden gedistribueerd en ontvangen. Deze service gebruikt digitale handtekeningen en certificering om ervoor te zorgen dat documenten niet worden gewijzigd. Als u een document wijzigt, wordt de handtekening verbroken. Omdat de veiligheidseigenschappen op het document zelf worden toegepast, blijft het document veilig en gecontroleerd voor zijn volledige levenscyclus; voorbij de firewall, wanneer het off-line wordt gedownload, en wanneer het terug naar uw organisatie wordt voorgelegd.

De volgende instellingen zijn beschikbaar voor de service Handtekening.

**Naam van de Verre Dienst HSM SPI:** Deze optie is voor gebruik wanneer HSM op een verre computer geïnstalleerd is. Geef deze optie op wanneer AEM formulieren op een 64-bits Windows zijn geïnstalleerd en u HSM-apparaten gebruikt voor ondertekening.

**URL van de Verre Dienst van het Web HSM:** specificeer deze optie wanneer AEM vormen op Vensters met 64 bits geïnstalleerd zijn en u apparaten HSM voor het ondertekenen gebruikt.

**Certificatie om de Veranderingen van de Lading van de Vorm te omvatten:** wanneer deze optie wordt geselecteerd, wordt de XFA Staat van de Vorm verklaard naast het malplaatje XFA. Houd er rekening mee dat het inschakelen van deze optie negatieve gevolgen kan hebben voor de prestaties. De standaardwaarde is true.

**voert de manuscripten van JavaScript van het Document uit:** specificeert of om de manuscripten van JavaScript van het Document tijdens handtekeningsverrichtingen uit te voeren. De standaardwaarde is false.

**documenten van het Proces met de verenigbaarheid van Acrobat 9:** specificeert of om de verenigbaarheid van Acrobat 9 toe te laten. Als deze optie bijvoorbeeld is ingeschakeld, wordt Zichtbare certificering in dynamische PDF ingeschakeld. De standaardwaarde is false.

**bedt Informatie van de Intrekking tijdens het Ondertekenen in:** specificeert of de intrekkingsinformatie terwijl het ondertekenen van het document van de PDF wordt ingebed. De standaardwaarde is false.

**bedt Info van de Intrekking terwijl het Certificeren in:** specificeert of de intrekkingsinformatie terwijl het certificeren van het document van de PDF wordt ingebed. De standaardwaarde is false.

**Insluiten van intrekkingsinformatie voor alle certificaten afdwingen
Tijdens het Ondertekenen/Certificeren:** geeft aan of een ondertekenings- of certificeringsbewerking mislukt als geldige intrekkingsinformatie voor alle certificaten niet is ingesloten. Als een certificaat geen CRL- of OCSP-informatie bevat, wordt het als geldig beschouwd, zelfs als er geen intrekkingsinformatie wordt opgehaald. De standaardwaarde is false.

**de Orde van de Controle van de Intrekking:** specificeert de orde van herroepingscontrole wanneer het controleren mogelijk door zowel de mechanismen van de Lijst van de Intrekking van het Certificaat (CRL) als van het Online Protocol van de Status van het Certificaat (OCSP) is. De standaardwaarde is OCSPFirst.

**Maximale Grootte van Info van het Archief van de Intrekking:** de maximumgrootte van de informatie van het intrekkingsarchief in kilobytes. AEM formulieren proberen zoveel mogelijk intrekkingsgegevens op te slaan zonder de limiet te overschrijden. De standaardwaarde is 10 kB.

**steun handtekeningen die van preRelease-gebouwen van worden gecreeerd
Producten van de Adobe:** wanneer deze optie wordt geselecteerd, zal de handtekening die gebruikend pre-versieversie van de producten van de Adobe wordt gecreeerd correct bevestigen. De standaardwaarde is false.

**Optie van de Tijd van de Verificatie:** specificeert de tijd van controle van het certificaat van een ondertekenaar. De standaardwaarde is Beveiligde tijd anders dan huidige tijd.

**Intrekkingsgegevens van het Gebruik die in Handtekening tijdens wordt gearchiveerd
Validatie:** specificeert of de intrekkingsinformatie die met de handtekening wordt gearchiveerd, wordt gebruikt voor intrekkingscontrole. De standaardwaarde is true.

**de informatie van de Bevestiging van het gebruik die in het document voor wordt opgeslagen
Validatie van handtekeningen:** als deze optie is geselecteerd, worden validatiegegevens (inclusief intrekkingsgegevens en tijdstempelgegevens) die in het document zijn ingesloten, gebruikt om handtekeningen te valideren. De standaardwaarde is true.

**Maximum Genestelde Toegestane Versies van de Verificatie:** het maximumaantal genestelde verificatiesessies die worden toegestaan. AEM formulieren gebruiken deze waarde om een oneindige lus te voorkomen wanneer de OCSP- of CRL-ondertekenaarcertificaten worden gecontroleerd wanneer het OCSP- of CRL-certificaat niet correct is ingesteld. De standaardwaarde is 10.

**Maximale Scheeftrekking van de Klok voor Verificatie:** de maximumtijd, in notulen, dat de ondertekeningstijd na de bevestigingstijd kan zijn. Als de klok meer schuin is dan deze waarde, is de handtekening niet geldig. De standaardwaarde is 65 minuten.

**Geheime voorgeheugen van het Certificaat van het Leven:** Het leven van een certificaat, online of door andere middelen, in het geheime voorgeheugen wordt teruggewonnen. De standaardwaarde is 1 dag.

### Vervoersopties {#transport-options}

**Gastheer van de Volmacht:** URL van de volmachtsgastheer. Wordt alleen gebruikt als er een geldige waarde is opgegeven. Geen standaardwaarde.

**de Haven van de Volmacht:** de volmachtshaven. Typ een geldig poortnummer tussen 0 en 65535. De standaardwaarde is 80.

**Login van de Volmacht Gebruikersnaam:** de volmachtslogin gebruikersnaam. Wordt alleen gebruikt als er een geldige waarde is opgegeven voor de proxyhost en -poort. Geen standaardwaarde.

**Wachtwoord van de Login van de Volmacht:** het wachtwoord van volmachtslogin. Wordt alleen gebruikt als een geldige waarde is opgegeven voor de gebruikersnaam van de proxyhost, proxypoort en proxyaanmelding. Geen standaardwaarde.

**Maximale Grens van de Download:** de maximumhoeveelheid gegevens, in MBs, die per verbinding kan worden ontvangen. De minimumwaarde is 1 MB en de maximumwaarde is 1024 MB. De standaardwaarde is 16 MB.

**Tijd van de Verbinding uit:** De maximumtijd om, in seconden, voor het vestigen van een nieuwe verbinding te wachten. De minimumwaarde is 1 en de maximumwaarde is 300. De standaardwaarde is 5.

**Tijd van de Zak uit:** de maximumtijd om, in seconden te wachten, alvorens een contactdoosonderbreking (terwijl het wachten op gegevensoverdracht) voorkomt. De minimumwaarde is 1 en de maximumwaarde is 3600. De standaardwaarde is 30.

### Opties voor padvalidatie {#path-validation-options}

**vereist Expliciet Beleid:** specificeert of de weg voor minstens één van het certificaatbeleid geldig moet zijn dat met het vertrouwensanker van het ondertekenaarcertificaat wordt geassocieerd. De standaardwaarde is false.

**belemmert OM HET EVEN WELK Beleid:** specificeert of het beleid objecten herkenningsteken (OID) zou moeten worden verwerkt als het in een certificaat inbegrepen is. De standaardwaarde is false.

**belemmert het Toewijzing van het Beleid:** specificeert of de beleidstoewijzing in de certificatieweg wordt toegestaan. De standaardwaarde is false.

**Controle Alle Wegen:** specificeert of alle wegen zouden moeten worden bevestigd of de bevestiging zou moeten ophouden na het vinden van de eerste geldige weg. Selecteer waar of onwaar. De standaardwaarde is false.

**LDAP Server:** De server LDAP die wordt gebruikt om certificaten voor wegbevestiging op te zoeken. Geen standaardwaarde.

**volgt URIs in Certificaat AIA:** specificeert of de Uniform Herkenningstekens van het Middel (URIs) in Certificaat AIA tijdens wegontdekking worden verwerkt. De standaardwaarde is false.

**Basis de Uitbreiding van Beperkingen die in de Certificaten van CA wordt vereist:** specificeert of de het certificaatuitbreiding van de het certificaatgezag (CA) Basis van Beperkingen voor de certificaten van CA moet aanwezig zijn. Sommige vroege Duitse gecertificeerde basiscertificaten (7 en eerder) zijn niet compatibel met RFC 3280 en bevatten niet de basisbeperkingsextensie. Schakel dit selectievakje uit als u weet dat het EE-certificaat van een gebruiker is gekoppeld aan een dergelijk Duits basiscertificaat. De standaardwaarde is true.

**vereist Geldige Handtekening van het Certificaat tijdens de Bouw van de Keten:** specificeert of de ketenbouwer geldige handtekeningen op certificaten vereist die worden gebruikt om ketens te bouwen. Wanneer deze controledoos wordt geselecteerd, zal de kettingaannemer geen ketens met ongeldige handtekeningen van RSA op certificaten bouwen. Overweeg keten CA > ICA > EE waar de handtekening van CA op een ICA niet geldig is. Als dit het plaatsen waar is, zal het ketengebouw bij ICA ophouden, en CA zal niet in de ketting worden omvat. Als deze instelling onwaar is, wordt de volledige certificaatketen van drie pixels geproduceerd. Deze instelling heeft geen invloed op DSA-handtekeningen. De standaardwaarde is false.

### Opties tijdstempelprovider {#timestamp-provider-options}

**TSP Server URL:** URL van de standaardtimestamp leverancier. Wordt alleen gebruikt als er een geldige waarde is opgegeven. Geen standaardwaarde.

**de Gebruikersnaam van de Server TSP:** De gebruikersnaam indien nodig door de timestamp leverancier. Wordt alleen gebruikt als er een geldige waarde voor de URL is opgegeven. Geen standaardwaarde.

**TSP het Wachtwoord van de Server:** het wachtwoord voor de bovengenoemde gebruikersnaam indien nodig door de timestamp leverancier. Wordt alleen gebruikt als er een geldige waarde voor de URL en de gebruikersnaam is opgegeven. Geen standaardwaarde.

**Algoritme van de Hash van het Verzoek:** specificeert het het hakken algoritme dat terwijl het creëren van het verzoek voor de timestamp leverancier moet worden gebruikt. De standaardwaarde is SHA1.

**Stijl van de Controle van de Intrekking:** specificeert de herroepings controlerende stijl die voor het bepalen van het vertrouwensstatuut van het certificaat van de tijdstempelleverancier van zijn waargenomen intrekkingsstatus wordt gebruikt. De standaardwaarde is BestEfficient.

**verzendt Nonce:** specificeert of nonce met het tijdstempelleveranciersverzoek wordt verzonden. Een nonce kan een tijdstempel, een bezoekersteller op een webpagina zijn of een speciale markering die bedoeld is om het ongeoorloofd afspelen of het reproduceren van een bestand te beperken of te voorkomen. De standaardwaarde is true.

**Verlopen Tijdstempels van het Gebruik tijdens Bevestiging:** Wanneer deze optie wordt geselecteerd, kunnen de verlopen tijdstempels worden gebruikt om bevestigingstijden van handtekeningen terug te winnen. De standaardwaarde is true.

**TSP Grootte van de Reactie:** Geschatte grootte, in bytes, van de reactie TSP. Deze waarde moet de maximale grootte vertegenwoordigen van de tijdstempelreactie die de geconfigureerde tijdstempelprovider kan retourneren. Wijzig dit alleen als u er absoluut zeker van bent. De minimumwaarde is 60B en de maximumwaarde is 10240B. De standaardwaarde is 4096B.

**negeert de Uitbreiding van de Server TimeStamp**: Selecteer **negeren de optie van de Uitbreiding van de Server van de Tijdstempel** om de server van AEM Forms tegen te houden van het contacteren van de gespecificeerde tijdstempelserver. Als u deze optie selecteert, voorkomt u procesfouten die optreden als gevolg van een time-out van de verbinding tussen AEM Forms en tijdstempelservers.

### Opties voor certificaatintrekkingslijst {#certificate-revocation-list-options}

**raadpleeg Lokale URI eerst:** specificeert of de plaats CRL die in Lokale URI of CRL Opzoeken wordt verstrekt voorkeur over om het even welke plaats zou moeten worden gegeven die binnen een certificaat voor het doel van herroepingscontrole wordt gespecificeerd. De standaardwaarde is false.

**Lokale URI voor CRL Opzoeken:** URL van de lokale leverancier CRL. Deze waarde wordt alleen geraadpleegd als de instelling Eerst lokale URI raadplegen is ingesteld op true. Geen standaardwaarde.

**Stijl van de Controle van de Intrekking:** specificeert de herroepings controlerende stijl die voor het bepalen van het vertrouwensstatuut van het certificaat van de leverancier CRL van zijn waargenomen intrekkingsstatus wordt gebruikt. De standaardwaarde is BestEfficient.

**Server LDAP voor CRL Opzoeken:** De Server LDAP die wordt gebruikt om CRLs (als www.ldap.com) te krijgen. Alle op DN gebaseerde vragen voor CRLs zullen aan deze server worden geleid. Geen standaardwaarde.

**ga Online:** specificeert of online te gaan om CRL te halen. Indien onwaar worden alleen in de cache opgeslagen CRL&#39;s (op de lokale schijf of op de ingesloten CRL&#39;s) geraadpleegd. De standaardwaarde is true.

**negeert de Datums van de Geldigheid:** specificeert of om de tijden van thisUpdate en nextUpdate van de reactie te negeren, die deze tijden verhindert een negatief effect op reactiegeldigheid te hebben. De standaardwaarde is false.

**vereist AKI uitbreiding in CRL:** specificeert of de Zeer belangrijke uitbreiding van het Herkenningsteken van de Autoriteit in een CRL moet worden omvat. De standaardwaarde is false.

### Opties online certificaatstatusprotocol {#online-certificate-status-protocol-options}

**URL van de Server OCSP:** URL voor de standaardOCSP server. Of de OCSP-server die via deze URL is opgegeven, wordt gebruikt, is afhankelijk van de instelling van de optie URL naar advies. Geen standaardwaarde.

**URL om Optie te raadplegen:** controleert de lijst en de orde van de servers OCSP die voor het uitvoeren van de statuscontrole worden gebruikt. De standaardwaarde is UseAIAInCert.

**Stijl van de Controle van de Intrekking:** specificeert de herroepings controlerende stijl die terwijl het verifiëren van het certificaat van de OCSP server wordt gebruikt. De standaardwaarde is CheckIfAvailable.

**verzendt Nonce:** specificeert of nonce met het OCSP verzoek wordt verzonden. Een nonce kan een tijdstempel, een bezoekersteller op een webpagina zijn of een speciale markering die bedoeld is om het ongeoorloofd afspelen of het reproduceren van een bestand te beperken of te voorkomen. De standaardwaarde is true.

**Max de Tijd van het Schuintrekken van het Klok:** Maximum toegestane schuine streep, in notulen, tussen reactietijd en lokale tijd. De minimumwaarde is 0 en de maximumwaarde is 2147483647m. De standaardwaarde is 5 m.

**de Tijd van de Vrachtheid van de Reactie:** Maximale tijd, in notulen, waarvoor een preconstrueerde reactie OCSP als geldig wordt beschouwd. De minimumwaarde is 1 m en de maximaal toegestane waarde is 2147483647. De standaardwaarde is 525600 (één jaar).

**OCSP van het Teken Verzoek:** specificeert of het OCSP- verzoek zou moeten worden ondertekend. De standaardwaarde is false.

**de ReferentieAlias van de Ondertekenaar van het Verzoek:** specificeert de referentie alias voor het ondertekenen van het OCSP verzoek als het ondertekenen wordt toegelaten. Wordt alleen gebruikt als de ondertekening van een OCSP-aanvraag is ingeschakeld. Geen standaardwaarde.

**ga Online:** specificeert of online gaan om intrekkingscontrole te doen. De standaardwaarde is true.

**negeert de tijden van thisUpdate en nextUpdate van de reactie:** specificeert of om de tijden thisUpdate en nextUpdate van de reactie te negeren, die deze tijden verhindert een negatief effect op reactiegeldigheid te hebben. De standaardwaarde is false.

**staat uitbreiding OCSPNoCheck toe:** specificeert of de uitbreiding OCSPNoCheck in het reactie ondertekenende certificaat wordt toegestaan. De standaardwaarde is true.

**Vereis OCSP ISIS-MTT Uitbreiding CertHash:** specificeert of een de knoeiboeluitbreiding van de certificaatopenbare sleutel in reacties moet worden omvat OCSP. De standaardwaarde is false.

### Opties voor foutafhandeling {#error-handling-options-for-debugging}

**wis het Geheime voorgeheugen van het Certificaat op volgende API vraag:** specificeert of om het Geheime voorgeheugen van het Certificaat te zuiveren wanneer de volgende Verrichting van de Dienst van de Handtekening wordt geroepen. Nadat de bewerking is aangeroepen, wordt deze optie teruggezet op false. De standaardwaarde is false.

**wis CRL Geheime voorgeheugen op volgende API vraag:** specificeert of om het Geheime voorgeheugen te zuiveren CRL wanneer de volgende Verrichting van de Dienst van de Handtekening wordt geroepen. Nadat de bewerking is aangeroepen, wordt deze optie teruggezet op false. De standaardwaarde is false.

**wis OCSP Geheime voorgeheugen op volgende API vraag:** specificeert of om het Geheime voorgeheugen te zuiveren OCSP wanneer de volgende Verrichting van de Dienst van de Ondertekening wordt geroepen. Nadat de bewerking is aangeroepen, wordt deze optie teruggezet op false. De standaardwaarde is false.

## Instellingen voor gecontroleerde mapservice {#watched-folder-service-settings}

Met de service Gecontroleerde map ( `WatchedFolder` ) configureert u kenmerken die algemeen gelden voor alle gecontroleerde eindpunten van mappen. De klasse biedt ook standaardwaarden voor gecontroleerde eindpunten van mappen. (Zie [ Vormend gecontroleerde omslageindpunten ](/help/forms/using/admin-help/configuring-watched-folder-endpoints.md#configuring-watched-folder-endpoints).) Het wordt niet aangehaald door externe cliënttoepassingen of gebruikt in processen die in Workbench worden gecreeerd.

De volgende instellingen zijn beschikbaar voor de service Gecontroleerde map.

**Uitsnede Uitdrukking:** de uitsnijduitdrukking zoals die door kwarts wordt gebruikt om het opiniepeilen van de inputfolder te plannen.

**Aantal van de Herhaling:** het aantal tijden de inputfolder wordt gepolled. De standaardherhalingstelling om te gebruiken als deze waarde niet in de eindpuntconfiguratie wordt gespecificeerd. De waarde -1 geeft aan dat de map voor onbepaalde tijd wordt gescand. De standaardwaarde is -1.

**Herhaal Interval:** het standaardaantal als seconden tussen elke opiniepeiling. Deze waarde wordt gebruikt als herhalingsinterval tenzij een verschillende waarde in de gecontroleerde configuratie van het omslageindpunt wordt gespecificeerd. De standaardwaarde is 5. Zie de beschrijving van de instelling Batchgrootte voor meer informatie.

**Asynchroon:** identificeert het aanroepingstype als asynchroon of synchroon. De voorbijgaande en synchrone processen kunnen slechts synchroon worden aangehaald. De standaardwaarde is asynchroon.

**wacht Tijd:** de standaardwaarde voor tijd, in seconden, waarna de dossiers van de inputomslagen worden teruggewonnen. Als het bestand of de map ouder is dan de in de wachttijd opgegeven tijd, wordt het bestand of de map opgehaald voor verwerking. De standaardwaarde is 0.

**Grootte van de Partij:** De standaardwaarde voor het aantal dossiers of omslag die per aftasten worden verwerkt. De standaardwaarde is 2.

Met de instellingen voor Interval herhalen en Batchgrootte bepaalt u hoeveel bestanden in Gecontroleerde map worden opgehaald bij elke scan. De gecontroleerde Omslag gebruikt een de draadpool van het Kwartz om de inputomslag af te tasten. De draadpool wordt gedeeld met andere diensten. Als het scaninterval klein is, scannen de threads de invoermap vaak. Als bestanden vaak in de controlemap worden geplaatst, moet u het scaninterval klein houden. Als de dossiers niet vaak worden gelaten vallen, gebruik een groter aftasteninterval zodat de andere diensten de draden kunnen gebruiken.

Als er een groot volume bestanden verloren gaat, maakt u de batch groot. Als de service die wordt aangeroepen door het gecontroleerde mapeindpunt bijvoorbeeld 700 bestanden per minuut kan verwerken en gebruikers bestanden naar dezelfde snelheid in de invoermap kunnen neerzetten, helpt het instellen van Batchgrootte op 350 en Herhalingsinterval op 30 seconden de prestaties van gecontroleerde mappen te controleren zonder de kosten voor het te vaak doorzoeken van de gecontroleerde map op te lopen.

Wanneer bestanden in de controlemap worden neergezet, worden de bestanden in de invoer weergegeven. Hierdoor kunnen de prestaties afnemen wanneer elke seconde wordt gescand. Het verhogen van het aftasteninterval kan prestaties verbeteren. Als het volume van de dossiers dat klein is wordt gelaten vallen, pas de Grootte van de Partij en Interval dienovereenkomstig aan. Als er bijvoorbeeld elke seconde 10 bestanden worden verwijderd, stelt u het interval voor herhalen in op 1 seconde en de waarde voor Batchgrootte op 10.

In een clusterconfiguratie, schrapt de partijgrootte voor een gecontroleerd omslageindpunt niet aan veelvoudige clusterknopen. Als de batchgrootte bijvoorbeeld is ingesteld op `2` voor een cluster met twee knooppunten en de optie Throttle is geselecteerd, verwerken de knooppunten gezamenlijk bestanden in batches van twee in plaats van elk knooppunt dat twee bestanden tegelijk verwerkt.

**overschrijft Dubbele Namen van het Dossier:** Een koord Van Boole dat specificeert of de gecontroleerde omslag dubbele resultaatfilenames en of de bewaarde documenten van de zelfde naam zou moeten worden beschreven.

**Behoud Omslag:** de standaardwaarde voor bewaart omslag. Deze map wordt gebruikt om de bronbestanden naar te kopiëren als de invoer met succes is verwerkt. Deze waarde kan een leeg, relatief of absoluut pad zijn met een bestandspatroon zoals beschreven voor de instelling Map met resultaten.

**Omslag van de Mislukking:** de naam van de omslag waar de mislukkingsdossiers worden gekopieerd. Deze waarde kan een leeg, relatief of absoluut pad zijn met een bestandspatroon zoals beschreven voor de instelling Map met resultaten.

**Omslag van het Resultaat:** de standaardnaam voor de resultaatomslag. Deze map wordt gebruikt om de resultatenbestanden naar te kopiëren. Deze waarde kan een leeg, relatief of absoluut pad zijn met het volgende bestandspatroon.

* %F = voorvoegsel bestandsnaam
* %E = bestandsnaamextensie
* %Y = jaar (volledig)
* %y = jaar (laatste twee cijfers)
* %M = maand
* %D = dag van de maand
* %d = dag van het jaar
* %H = uur (24-uurs klok)
* %h = uur (12-uurs klok)
* %m = minuut
* %s = seconde
* %l = millisecond
* %R = willekeurig getal (tussen 0 en 9)
* %P = proces- of taak-id

Als de waarde op 17 juli 2009 bijvoorbeeld 20:00 is en u geeft `C:/Test/WF0/failure/%Y/%M/%D/%H/` op, is de resultaatmap `C:/Test/WF0/failure/2009/07/17/20` .

Als het pad niet absoluut maar relatief is, wordt de map in de controlemap gemaakt. Voor meer informatie over dossierpatronen, zie [ Ongeveer dossierpatronen ](/help/forms/using/admin-help/configuring-watched-folder-endpoints.md#about-file-patterns).

>[!NOTE]
>
>Hoe kleiner de resulterende mappen, hoe beter Gecontroleerde mappen. Als het geschatte laden voor de gecontroleerde map bijvoorbeeld 1000 bestanden per uur is, probeert u een patroon als `result/%Y%M%D%H` , zodat er elk uur een nieuwe submap wordt gemaakt. Als het laden kleiner is (bijvoorbeeld 1000 bestanden per dag), kunt u een patroon gebruiken zoals `result/%Y%M%D` .

**de Omslag van het Stadium:** de standaardnaam voor de werkgebiedomslag binnen de gecontroleerde omslag.

**de Omslag van de Input:** de standaardnaam voor de inputomslag binnen de gecontroleerde omslag.

**Behoud op Mislukking:** als waar, worden de originele dossiers bewaard in de mislukkingsomslag op mislukking.

**Schommel:** wanneer deze optie wordt geselecteerd, beperkt het het aantal gelete op omslagbanen die op om het even welk bepaald ogenblik vormen AEM. De waarde voor Batchgrootte bepaalt het maximale aantal taken (zie Informatie over vertragen).

## Instellingen webservice {#web-service-service-settings}

De dienst van de Dienst van het Web ( `WebService`) laat processen toe om de verrichtingen van de Webdienst aan te halen.

De dienst van de Dienst van het Web laat processen toe om de verrichtingen van de Webdienst aan te halen. Een organisatie kan bijvoorbeeld een proces voor het opslaan en ophalen van informatie, zoals contact- en accountgegevens, willen integreren door de onzichtbare webservices van een serviceprovider aan te roepen. De dienst van de Dienst van het Web haalt een gespecificeerde Webdienst aan en gaat door waarden voor elk van zijn parameters over. Vervolgens worden de geretourneerde waarden van de bewerking opgeslagen in een toegewezen variabele binnen een proces.

De dienst van de Dienst van het Web communiceert met Webdiensten door SOAP berichten te verzenden en te ontvangen. De dienst steunt ook het verzenden MIME, MTOM, en de gehechtheid SwaRef met SOAP berichten door het WS-Bijlage protocol te gebruiken. De de dienstinteractie van de Dienst van het Web is compatibel met de systemen van SAP en .NET Webdiensten.

De volgende montages zijn beschikbaar voor de dienst van de Dienst van het Web.

**Zeer belangrijke Opslag:** de volledige weg van het keystore dossier dat de privé sleutel bevat voor authentificatie te gebruiken. De Forms-server moet toegang hebben tot het bestand.

**Zeer belangrijk Wachtwoord van de Opslag:** het wachtwoord voor het keystore dossier.

**Zeer belangrijke Type van Opslag:** het type van keystore. Verstrek geen waarde om het standaardsleutelarchieftype te gebruiken dat voor JVM wordt gevormd die de Server van Forms in werking stelt. Geef anders een van de volgende waarden op:

* jks
* pkcs12
* cms
* jceks

**Opslag van het Vertrouwen:** de volledige weg van het dossier van de vertrouwensopslag dat de openbare sleutel van de server van de Webdienst bevat.

**Wachtwoord van de Opslag van het Vertrouwen:** het wachtwoord voor het truststore dossier.

**Type van Opslag van het Vertrouwen:** Het type van truststore. Verstrek geen waarde om het standaardsleutelarchieftype te gebruiken dat voor JVM wordt gevormd die de Server van Forms in werking stelt. Geef anders een van de volgende waarden op:

* jks
* pkcs12
* cms
* jceks

## XSLT Transformation Service Settings {#xslt-transformation-service-settings}

Met de XSLT Transformation Service ( `XSLTService` ) kunnen processen Extensible Stylesheet Language Transformations (XSLT) toepassen op XML-documenten.

De volgende instelling is beschikbaar voor de service XSLT-transformatie.

**Naam van de Fabriek:** volledig - gekwalificeerde naam van de klasse van Java voor het uitvoeren van transformaties van XSLT te gebruiken. Als geen waarde wordt gespecificeerd, wordt de standaardfabriek die in de Virtuele Machine van Java wordt gevormd die de Server van Forms in werking stelt gebruikt.

## Beveiligingsinstellingen voor een service wijzigen {#modifying-security-settings-for-a-service}

De Server van Forms laat u toe om veiligheidsmontages voor elke dienst te vormen, die u verfijnd toegangsbeheer op een dienst-door-dienst niveau laat vormen.

Er zijn standaardbeveiligingsprofielen geïnstalleerd, die vervolgens kunnen worden geconfigureerd om aan uw systeembehoeften te voldoen. Elk beveiligingsprofiel heeft een gekoppeld domein en wordt op gebruikersniveau of groepsniveau gemaakt.

### Beveiligingsinstellingen wijzigen voor een service {#modify-security-settings-for-a-service}

1. Klik in de beheerconsole op Services > Toepassingen en services > Servicebeheer.
1. Voor de pagina van het Beheer van de Dienst, klik de dienst om te vormen.
1. Klik op het tabblad Beveiliging.
1. In de Vereisen Vraag om lijst voor authentiek te verklaren, selecteer of ja of Nr om te specificeren of de dienst met of zonder geloofsbrieven kan worden aangehaald.

   Als u ja selecteert, moet de bezoeker van de dienst voor authentiek worden verklaard en het gebruikershoofd voor die bezoeker moet worden gemachtigd om de dienst aan te halen; anders, zal de aanroepende poging worden geweigerd.

   Als u Nr selecteert, kan de bezoeker van de dienst al dan niet voor authentiek worden verklaard. De aanroeping van de dienst zal altijd slagen omdat er geen vergunningscontrole is.

1. Voor de diensten die één of meerdere verrichtingen bevatten die voor anonieme toegang worden gemarkeerd, selecteer of schrap Anoniem Toegelaten Toegang. Wanneer de anonieme toegang wordt toegelaten, kan om het even welke gebruiker binnen het systeem verrichtingen op de dienst aanhalen. Als anonieme toegang gehandicapt is, moeten de gebruikers toestemming worden verleend om de dienst te roepen en verrichtingen aan te halen. Gebruikers krijgen deze machtigingen direct of als onderdeel van een groep met dergelijke machtigingen.
1. Voor sommige services beïnvloedt de gebruikersaccount die de bewerking uitvoert de resultaten. Bijvoorbeeld, in de (Vervangen) Diensten van de Inhoud, wordt de gebruiker die inhoud opslaat gemaakt tot eigenaar van de inhoud, die beïnvloedt wie tot de inhoud kan later toegang hebben. Als u een proces gebruikt om inhoud op te slaan, denk over welke gebruiker wordt gebruikt om de dienst van het Beheer van het Document uit te voeren, omdat die gebruiker de opgeslagen inhoud zal bezitten.

   Als u de runtime-identiteit wilt opgeven die door de service wordt gebruikt om bewerkingen uit te voeren, selecteert u Uitvoeren als opgeven, selecteert u een optie in de bijbehorende lijst en klikt u op Opslaan. Kies een van de volgende opties:

   **Invoker:** gebruikt de zelfde identiteit zoals de gebruiker die de dienst aanhaalde.

   **Systeem:** gebruikt de gebruiker van het Systeem om de dienst met volledige voorrechten in werking te stellen.

   **Benoemde Gebruiker:** laat u toe om de dienst als specifieke gebruiker in werking te stellen. Wanneer u deze optie selecteert, klikt u op Gebruiker selecteren om de pagina Afzonderlijk kapitaal selecteren weer te geven. Hier kunt u de gebruiker zoeken en selecteren.

   Als u Uitvoeren als opgeven niet selecteert, wordt het standaardgedrag gebruikt.

   >[!NOTE]
   >
   >De diensten die met xfaForm, de Vorm van het Document, en de variabelen van de Vorm worden gebruikt worden teruggeven en voorleggen altijd uitgevoerd gebruikend de de gebruikersrekening van het Systeem.

1. Klik toevoegen Belangrijker om de toestemmingen te specificeren die de gebruikers en de groepen voor deze dienst hebben.
1. Het Uitgezochte Belangrijkste scherm toont de gebruikers en de groepen die in het Beheer van de Gebruiker worden gevormd. Als de gewenste gebruiker of groep niet wordt weergegeven, gebruikt u de zoekfunctie om deze te zoeken. Klik op de naam van een gebruiker of groep.
1. Voor het Add scherm van Toestemmingen, selecteer de toestemmingen om aan de gebruiker of de groep voor deze dienst toe te wijzen:

   * **INVOKE_PERM:** om alle verrichtingen op de dienst aan te halen
   * **MODIFY_CONFIG_PERM:** om de configuratie van de dienst te wijzigen
   * **SUPERVISOR_PERM:** om procesinstantiegegevens voor de dienst te bekijken die van een proces wordt gecreeerd
   * **START_STOP_PERM:** om de dienst te beginnen en tegen te houden
   * **ADD_REMOVE_ENDPOINTS_PERM:** om, eindpunten voor de dienst toe te voegen te verwijderen en te wijzigen
   * **CREATE_VERSION_PERM:** om een versie van de dienst te creëren
   * **DELETE_VERSION_PERM:** om een versie van de dienst te schrappen
   * **MODIFY_VERSION_PERM:** om een versie van de dienst te wijzigen
   * **READ_PERM:** om de dienst te bekijken
   * **PROCESS_OWNER_PERM:** voor gebruik in een toekomstige versie van AEM vormen. Gebruik deze machtiging niet.
   * **SERVICE_MANAGER_PERM:** voor gebruik in een toekomstige versie van AEM vormen. Gebruik deze machtiging niet.
   * **SERVICE_AGENT_PERM:** voor gebruik in een toekomstige versie van AEM vormen. Gebruik deze machtiging niet.

1. Klik toevoegen.

### De principal verwijderen uit een beveiligingsprofiel {#remove-the-principal-from-a-security-profile}

1. Voor de pagina van het Beheer van de Dienst, selecteer de dienst om te vormen.
1. Klik het **lusje van de Veiligheid**, selecteer het te verwijderen veiligheidsprofiel, en klik **verwijderen**.

## Het vormen het groeperen voor de dienst {#configuring-pooling-for-a-service}

Elke dienst kan uit de het groeperen mogelijkheden voordeel halen om inkomende aanroepingsverzoeken te behandelen. Het gebruiken van een de dienstpool zorgt ervoor dat de de dienstinstanties door één enkele draad tegelijkertijd worden aangehaald en over aanroepingsverzoeken opnieuw gebruikt, die in betere prestaties kunnen resulteren. U kunt het groeperen ook gebruiken om de Maximum Asynchrone optie van de Instanties van de Dienst te specificeren, die de diensten toestaat om het aantal verzoeken te beperken die parallel worden behandeld.

### pooling inschakelen {#enable-pooling}

1. Klik in de beheerconsole op Services > Toepassingen en services > Servicebeheer.
1. Voor de pagina van het Beheer van de Dienst, klik de dienst om te vormen.
1. Klik op het tabblad Pooling.
1. Selecteer Samengevoegde instanties voor alle verzoeken in de lijst Verwerkingsstrategie aanvragen.
1. In het Aanvankelijke vakje van de Grootte van de Pool van de Instantie van de Dienst, ga de aanvankelijke grootte van de pool in. Wanneer de dienst wordt opgesteld, wordt dit aantal gebruikt om het aantal instanties van de de dienstimplementatie te bepalen die worden gecreeerd en aan de vrije pool toegewezen, wachtend aanroepingsverzoeken. Dit laat de dienstcontainer toe om aan aanroepingsverzoeken onmiddellijk te antwoorden zonder het moeten een de dienstinstantie eerst initialiseren.
1. In het Maximale vakje van de Grootte van de Pool van de Instantie van de Dienst, ga het maximumaantal instanties in de pool voor de bepaalde dienst in. Dit het plaatsen controleert het aantal draden die een bepaalde dienst in een bepaalde tijd kunnen uitvoeren. De standaardwaarde is 0, wat in onbeperkte poolgrootte resulteert.
1. In het Maximale Asynchrone vakje van de Instanties van de Dienst, ga het maximumaantal instanties van de pool in die aan de dienst asynchrone verzoeken op om het even welk bepaald tijdstip kunnen worden gebruikt. Met deze instelling kan de service het aantal aanvragen beperken dat tegelijk kan worden afgehandeld.
1. In het vakje van de Onderbreking van de Wacht van de Inroeping, ga het aantal milliseconden in te wachten op de dienst om voor een aanroepingsverzoek beschikbaar te worden. Als u geen waarde voor deze instelling opgeeft, is de standaardwaarde 0, wat geen wachttijd tot gevolg heeft.
1. Klik op Opslaan.

### pooling verwijderen {#remove-pooling}

1. Klik in de beheerconsole op Services > Toepassingen en services > Servicebeheer.
1. Voor de pagina van het Beheer van de Dienst, klik de dienst om te vormen.
1. Klik op het tabblad Pooling.
1. Selecteer in de lijst Verwerkingsstrategie aanvragen de optie Nieuwe instantie voor elk verzoek of Eén instantie voor alle verzoeken.

   **Enige Instantie voor Alle Verzoeken:** de dienstinstantie van A wordt gecreeerd en in het voorgeheugen ondergebracht wanneer het eerste verzoek in de container komt. Elk verzoek na dat verzoek gebruikt de zelfde de dienstinstantie om het verzoek te behandelen.

   **Nieuwe Instantie voor Elk Verzoek:** Een nieuwe de dienstinstantie wordt gecreeerd voor elke ontvangen aanroeping.

1. Klik op Opslaan.
