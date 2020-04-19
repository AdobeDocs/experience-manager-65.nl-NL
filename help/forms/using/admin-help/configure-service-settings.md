---
title: Servicemontages configureren
seo-title: Servicemontages configureren
description: Leer hoe te om de dienstmontages te vormen.
seo-description: Leer hoe te om de dienstmontages te vormen.
uuid: e95425a4-62f6-473e-b21b-d081c432e02d
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_services
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 2fab4b0c-e5db-47cd-b85a-4ff5ad6eb178
translation-type: tm+mt
source-git-commit: 2cf9dcf2e9cf71c54e19e2c6ee825c9a8f00a9b7

---


# Servicemontages configureren {#configure-service-settings}

U kunt de pagina van het Beheer van de Dienst gebruiken om montages voor elk van de diensten te vormen die deel van AEM vormen. De beschikbare montages variëren afhankelijk van de dienst die wordt gevormd.

1. Klik in de beheerconsole op Services > Toepassingen en services > Servicebeheer.
1. Stop de service voordat u deze wijzigt. (Zie [Starten en stoppen van services](/help/forms/using/admin-help/starting-stopping-services.md#starting-and-stopping-services).)
1. Klik de naam van de dienst die u wilt vormen.
1. Als de dienst een lusje van de Configuratie heeft, gebruik het om de montages voor de dienst te veranderen. Zie de onderstaande lijst met koppelingen voor meer informatie.

   >[!NOTE]
   >
   >Niet hebben alle diensten die op de pagina van het Beheer van de Dienst worden vermeld een Configuratie tabel. Voor processen die u hebt gecreeerd, verschijnt het lusje van de Configuratie slechts als u een configuratieparameter aan het proces in Workbench hebt toegevoegd. (Zie &quot;Configuratieparameters&quot; in de [Workbench Help](https://www.adobe.com/go/learn_aemforms_workbench_63) .)


1. Klik op het tabblad Beveiliging en stel de beveiligingsinstellingen voor de service in. Zie Beveiligingsinstellingen [wijzigen voor een service](configure-service-settings.md#modifying-security-settings-for-a-service).
1. Als de dienst een lusje van Eindpunten heeft, gebruik het om de eindpuntmontages te veranderen. Zie Eindpunten [beheren](/help/forms/using/admin-help/adding-enabling-modifying-or-removing.md).
1. Klik op het tabblad Pooling en stel de instellingen voor pooling in. Zie het [Vormen het groeperen voor de dienst](configure-service-settings.md#configuring-pooling-for-a-service).
1. Klik op Opslaan om de wijzigingen op te slaan of klik op Annuleren om de wijzigingen te verwijderen.
1. Schakel het selectievakje naast de servicenaam in en klik op Start om de service opnieuw te starten.

## Instellingen voor workflowservice controleren {#audit-workflow-service-settings}

Workbench biedt de mogelijkheid om procesinstanties op te nemen terwijl ze bij uitvoering worden uitgevoerd en deze vervolgens af te spelen om het gedrag van het proces te observeren. (Zie [Workbench Help](https://www.adobe.com/go/learn_aemforms_workbench_63).) Als u ruimte wilt besparen op het bestandssysteem van de formulierserver, kunt u de hoeveelheid opgeslagen procesopnamegegevens beperken. U kunt de volgende eigenschappen van de dienst van de Dienst van het Werkschema van de Controle vormen ( `AuditWorkflowService`):

**maxNumberOfRecordingInstances:** Het maximumaantal opnamen dat wordt opgeslagen. Wanneer het maximumaantal wordt opgeslagen, wordt de oudste opname verwijderd uit het dossiersysteem wanneer een nieuwe opname wordt gecreeerd. Deze eigenschap is handig als u veel opnamen wilt maken en oude opnamen automatisch wilt verwijderen. De standaardwaarde is 50.

**MaxNumberOfRecordingEntry:** Het maximum aantal gegevensitems dat voor elke opname kan worden opgeslagen. Gegevensinvoer is informatie over bewerkingen in het proces. Verschillende ingangen worden opgeslagen voor elke uitvoering van een verrichting, zoals of de verrichting begon, of de verrichting voltooide, en of de route die tot de verrichting leidt volledig is. Deze eigenschap is nuttig wanneer processen veel bewerkingen kunnen bevatten, bijvoorbeeld wanneer een eindeloze lus wordt aangetroffen. De standaardwaarde is 50.

## service-instellingen voor streepjescodes {#barcoded-forms-service-settings}

De service voor streepjescodes extraheert streepjescodegegevens `(BarcodedFormsService)` uit gescande afbeeldingen. De service accepteert een formulier met streepjescodes (TIFF of PDF) als invoer en extraheert de machinerepresentatie van de gegevens die door de streepjescode zijn gecodeerd.

De volgende instellingen zijn beschikbaar voor de service voor formulieren met streepjescodes.

**Links lezen:** Als deze optie is geselecteerd, worden de streepjescodeafbeeldingen horizontaal van rechts naar links gescand.

**Rechts lezen:** Als deze optie is geselecteerd, worden de streepjescodeafbeeldingen horizontaal van links naar rechts gescand.

**Omhoog lezen:** Als deze optie is geselecteerd, worden de streepjescodeafbeeldingen verticaal van beneden naar boven gescand.

**Omlaag lezen:** Als deze optie is geselecteerd, worden de streepjescodeafbeeldingen verticaal van boven naar beneden gescand.

>[!NOTE]
>
>Standaard zijn alle opties geselecteerd. Schakel een optie alleen uit als u zeker weet dat er op uw formulieren geen streepjescodes voorkomen.

**Basisbestandspad:** Het bestandspad waarvoor de parameters van het invoer- en uitvoerbestand voor de bestandstaken XML uitvoeren en de taken voor een vast bestand uitvoeren zijn opgelost. In gegroepeerde configuraties, moet de weg van het basisdossier een gedeelde plaats zijn van het dossiersysteem waaraan alle clusterknopen lees-schrijftoegang hebben.

**Naam gegevensbron:** De naam van gegevensbron die wordt gebruikt om staat en geschiedenisinformatie over de banen van de partijverwerking te handhaven. De opgegeven gegevensbron moet algemene (XA) transacties ondersteunen.

## Instellingen voor Central Migration Bridge Service (Verouderd) {#central-migration-bridge-service-settings}

De Central Migration Bridge-service ( `CentralMigrationBridge`) roept een subset van de functionaliteit van Adobe Central Pro Output Server (Central) aan, die de opdrachten JFMERGE, JFTRANS en XMLIMPORT bevat. Met de Central Migration Bridge-service kunt u de volgende Central-elementen opnieuw gebruiken in AEM-formulieren:

* sjabloonontwerp (&amp;ast;.ifd)
* uitvoersjablonen (&amp;ast;.mdf)
* gegevensbestanden (&amp;ast;.dat-bestanden)
* preambule, bestanden (&amp;ast;.pre-bestanden)
* gegevensdefinitiebestanden (&amp;ast;.tdf)

De volgende instelling is beschikbaar voor de Central Migration Bridge-service.

**Centrale installatiemap:** De map waarin Adobe Central 5.7 is geïnstalleerd.

## Content Repository Connector voor EMC Documentum service settings {#content-repository-connector-for-emc-documentum-service-settings}

Met de Content Repository Connector voor EMC Documentum Service ( `EMCDocumentumContentRepositoryConnector`) kunt u processen maken die interageren met inhoud die is opgeslagen in een Documentum repository.

De volgende instelling is beschikbaar voor de Content Repository Connector voor EMC Documentum service.

**Standaardpad voor elementkoppelingsobject:** Het standaardgedeelte van het pad in de Documentum repository voor het opslaan van het Asset Link-object. Het feitelijke pad bestaat uit het standaardpad en de locatie van de formuliersjabloon in de opslagplaats voor AEM-formulieren.

Als het standaardpad bijvoorbeeld is ingesteld op `/LiveCycleES/ConnectorforEMCDocumentum/AssetLinkObjects`en de formuliersjabloon is opgeslagen in een map `/Docbase/forms/`, wordt het Asset Link-object opgeslagen op de volgende locatie:

`/LiveCycleES/ConnectorforEMCDocumentum/AssetLinkObjects/Docbase/forms/`

De standaardwaarde van deze instelling is `/LiveCycleES/ConnectorforEMCDocumentum/AssetLinkObjects`.

## Content Repository Connector voor IBM FileNet service settings {#content-repository-connector-for-ibm-filenet-service-settings}

Met de Content Repository Connector voor IBM FileNet kunt u processen maken die communiceren met inhoud die is opgeslagen in een IBM FileNet-opslagplaats.

De volgende instelling is beschikbaar voor de Content Repository Connector voor IBM FileNet-service.

**Standaardpad voor elementkoppelingsobject:** Het standaardgedeelte van het pad in de IBM FileNet-opslagruimte voor het opslaan van het Asset Link-object. Het feitelijke pad bestaat uit het standaardpad en de locatie van de formuliersjabloon in de opslagplaats voor AEM-formulieren.

Als het standaardpad bijvoorbeeld is ingesteld op `/LiveCycleES/ConnectorforIBMFileNet/AssetLinkObjects`en de formuliersjabloon is opgeslagen in een map `/Docbase/forms/`, wordt het Asset Link-object opgeslagen op de volgende locatie:

`/LiveCycleES/ConnectorforIBMFileNet/AssetLinkObjects/Docbase/forms/`

De standaardwaarde van deze instelling is `/LiveCycleES/ConnectorforIBMFileNet/AssetLinkObjects`.

## Instellingen van PDF-service converteren {#convert-pdf-service-settings}

Met de service PDF converteren ( `ConvertPdfService`) worden PDF-documenten geconverteerd naar PostScript en naar een aantal afbeeldingsindelingen (JPEG, JPEG 2000, PNG en TIFF). Het converteren van een PDF-document naar PostScript is handig voor afdrukken op basis van een server zonder toezicht op elke PostScript-printer. Het converteren van een PDF-document naar een TIFF-bestand met meerdere pagina&#39;s is handig bij het archiveren van documenten in inhoudsbeheersystemen die geen ondersteuning bieden voor PDF-documenten.

De volgende instellingen zijn beschikbaar voor de service PDF converteren.

**Transactietype:** Specificeert hoe een transactiecontext aan een verrichting zou moeten worden verspreid.

**Vereist:** steunt een transactiecontext als één bestaat; anders wordt een nieuwe transactiecontext gecreëerd. Dit is de standaardwaarde.

**Nieuwe vereisten:** Creeert altijd een nieuwe transactiecontext. Als er een actieve transactiecontext bestaat, wordt deze opgeschort.

**Tijd van transactie uit (in sec.):** Het aantal seconden dat de onderliggende transactieleverancier zou moeten wachten alvorens een transactie terug te rollen die deze verrichting verpakt. Deze waarde wordt genegeerd als een bestaande transactiecontext wordt doorgegeven. De standaardwaarde is 180.

**Drempelresolutie voor vloeiend maken (in dpi):** De afbeeldingsresolutie waaronder het vloeiend maken (of anti-aliasing) wordt toegepast op tekst, lijntekeningen en afbeeldingen, als u de opties &quot;Vloeiend maken toepassen op&quot; voor deze elementen hebt geselecteerd.

**Vloeiend maken op tekst toepassen:** Hiermee regelt u anti-aliasing van tekst. Schakel dit selectievakje uit als u het vloeiend maken van tekst wilt uitschakelen en tekst scherper en beter leesbaar wilt maken met een schermvergroting.

**Vloeiend maken toepassen op LineArt:** Hiermee kunt u abrupte hoeken in lijnen verwijderen.

**Vloeiend maken toepassen op afbeeldingen:** Hiermee minimaliseert u abrupte wijzigingen in afbeeldingen.

## Instellingen voor Distiller-service {#distiller-service-settings}

De Distiller-service ( `DistillerService`) converteert via een netwerk PostScript-, Encapsulated PostScript- (EPS) en PRN-bestanden naar PDF-bestanden.

De volgende instellingen zijn beschikbaar voor de Distiller-service.

**Adobe PDF-instellingen:** De volgende vooraf geconfigureerde instellingen worden toegepast op de gegenereerde PDF:

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

**Beveiligingsinstellingen:** Vooraf geconfigureerde beveiligingsinstellingen die worden toegepast op gegenereerde PDF-documenten. De standaardwaarde is Geen beveiliging. U moet beveiligingsinstellingen maken met de PDF Generator en de instelling hier invoeren.

**Poolgrootte:** De aanvankelijke grootte van de pool. Wanneer de dienst Distiller wordt opgesteld, wordt dit aantal gebruikt om het aantal instanties van de de dienstimplementatie te bepalen die en aan de vrije pool in afwachting van aanroepingsverzoeken worden gecreeerd en toegewezen. De de dienstcontainer kan dan onmiddellijk aan aanroepingsverzoeken antwoorden zonder het moeten een de dienstinstantie eerst initialiseren.

## Documentbeheerservice-instellingen {#document-management-service-settings}

>[!NOTE]
>
>Adobe® LiveCycle® Content Services ES (Afgekeurd) is een inhoudsbeheersysteem dat met LiveCycle is geïnstalleerd. Hiermee kunnen gebruikers processen ontwerpen, beheren, bewaken en optimaliseren die op mensen zijn gericht. De ondersteuning voor Content Services (Afgekeurd) eindigt op 31-12-2014. Zie [Adobe-productlevenscyclusdocument](https://www.adobe.com/support/products/enterprise/eol/eol_matrix.html). Zie [Inhoudsservices](https://help.adobe.com/en_US/livecycle/9.0/admin_contentservices.pdf)beheren voor informatie over het configureren van Inhoudsservices (afgekeurd).

Met de service Documentbeheer ( `DocumentManagementService`) kunnen processen de functionaliteit voor inhoudsbeheer gebruiken die door Content Services (Afgekeurd) wordt geboden. De verrichtingen van het Beheer van het document verstrekken basistaken die worden vereist om ruimten en inhoud in het systeem van het inhoudsbeheer te handhaven. Voorbeelden van dergelijke taken zijn kopiëren, verwijderen, verplaatsen, ophalen en opslaan, spaties en koppelingen maken en inhoudskenmerken ophalen en instellen.

De volgende instellingen zijn beschikbaar voor de service Documentbeheer.

**Winkelschema:** Het schema van de winkel waarin de inhoud zich bevindt. De standaardwaarde is de werkruimte.

**HTTP-poort:** De poort die wordt gebruikt om toegang te krijgen tot Content Services (Afgekeurd). De standaardwaarde is 8080.

## E-mailservice-instellingen {#email-service-settings}

E-mail wordt doorgaans gebruikt om inhoud te verspreiden of statusinformatie te verstrekken als onderdeel van een geautomatiseerd proces. Met de e-mailservice ( `EmailService`) kunnen processen e-mailberichten ontvangen van een POP3- of IMAP-server en e-mailberichten verzenden naar een SMTP-server.

Een proces gebruikt bijvoorbeeld de e-mailservice om een e-mailbericht met een PDF-formulierbijlage te verzenden. De e-mailservice maakt verbinding met een SMTP-server om het e-mailbericht met de bijlage te verzenden. Het PDF-formulier is zo ontworpen dat de ontvanger op Indienen klikt nadat het formulier is ingevuld. Door deze actie wordt het formulier als bijlage teruggestuurd naar de opgegeven e-mailserver. De e-mailservice haalt het geretourneerde e-mailbericht op en slaat het ingevulde formulier op in een formuliervariabele met procesgegevens.

De volgende instellingen zijn beschikbaar voor de e-mailservice.

**SMTP-host:** Het IP-adres of de URL van de SMTP-server die moet worden gebruikt voor het verzenden van e-mail.

**SMTP-poortnummer:** De poort die wordt gebruikt om verbinding te maken met de SMTP-server.

**SMTP-verificatie:** Selecteer als gebruikersauthentificatie wordt vereist om met de server te verbinden SMTP.

**SMTP-gebruiker:** De gebruikersnaam van de gebruikersaccount die moet worden gebruikt om zich aan te melden bij de SMTP-server.

**SMTP-wachtwoord:** Het wachtwoord dat aan de SMTP gebruikersrekening wordt geassocieerd.

**SMTP-transportbeveiliging:** Het veiligheidsprotocol voor het verbinden met de server SMTP te gebruiken:

* Selecteer Geen als er geen protocol wordt gebruikt (gegevens worden in duidelijke tekst verzonden)
* Selecteer SSL als het Secure Sockets Layer-protocol wordt gebruikt.
* Selecteer TLS als de Veiligheid van de Laag van het Vervoer wordt gebruikt.

**POP3/IMAP-host:** Het IP-adres of de URL van de POP3- of IMAP-server die moet worden gebruikt voor het verzenden van e-mail.

**POP3/IMAP-gebruikersnaam:** De gebruikersnaam van de gebruikersaccount die moet worden gebruikt om u aan te melden bij de POP3- of IMAP-server.

**POP3/IMAP-wachtwoord:** Het wachtwoord dat is gekoppeld aan de POP3- of IMAP-gebruikersaccount.

**POP3/IMAP-poortnummer:** De poort die wordt gebruikt om verbinding te maken met de POP3- of IMAP-server.

**POP3/IMAP:** Het protocol dat moet worden gebruikt voor het verzenden en ontvangen van e-mail.

**Beveiliging van transport ontvangen:** Het veiligheidsprotocol voor het verbinden met de server SMTP te gebruiken:

* Selecteer Geen als er geen protocol wordt gebruikt (gegevens worden in duidelijke tekst verzonden).
* Selecteer SSL als het Secure Sockets Layer-protocol wordt gebruikt.
* Selecteer TLS als de Veiligheid van de Laag van het Vervoer wordt gebruikt.

## Instellingen voor versleutelingsservice {#encryption-service-settings}

Met de coderingsservice ( `EncryptionService`) kunt u documenten coderen en decoderen. Wanneer een document wordt versleuteld, wordt de inhoud ervan onleesbaar. Een geautoriseerde gebruiker kan het document decoderen om toegang tot de inhoud te krijgen. Als een PDF-document is versleuteld met een wachtwoord, moet de gebruiker het wachtwoord voor openen opgeven voordat het document kan worden weergegeven in Adobe Reader of Adobe Acrobat. Als een PDF-document met een certificaat is versleuteld, moet de gebruiker het PDF-document decoderen met de openbare sleutel die overeenkomt met het certificaat (persoonlijke sleutel) dat is gebruikt om het PDF-document te versleutelen.

De volgende instellingen zijn beschikbaar voor de coderingsservice.

**Standaard LDAP-server waarmee verbinding moet worden gemaakt:** Hostnaam van de LDAP-server waarmee certificaten voor documentversleuteling worden opgehaald.

**Standaard LDAP-poort voor verbinding met:** Poortnummer van de LDAP-server.

**Standaard LDAP-gebruikersnaam:** Als verificatie voor de LDAP-server vereist is, geeft u de gebruikersnaam op die moet worden gebruikt om verbinding te maken met de LDAP-server.

**Standaard LDAP-wachtwoord:** Als de LDAP-server verificatie vereist, geeft u het wachtwoord op dat overeenkomt met de gebruikersnaam die moet worden gebruikt om verbinding te maken met de LDAP-server.

>[!NOTE]
>
>Gebruik alleen eenvoudige verificatie (gebruikersnaam en wachtwoord) wanneer de verbinding is beveiligd via SSL (met LDAPS).

**Compatibiliteitsmodus:**

## FTP-service-instellingen {#ftp-service-settings}

Met de FTP-service ( `FTP`) kunnen processen communiceren met een FTP-server. Met FTP-services kunnen bestanden worden opgehaald van de FTP-server, bestanden op de FTP-server worden geplaatst en bestanden van de FTP-server worden verwijderd. Documenten, zoals rapporten die zijn gegenereerd op basis van een proces, kunnen bijvoorbeeld worden opgeslagen op een FTP-server voor distributie. Een extern systeem kan ook bestanden genereren op basis van eerdere stappen in een proces. In een volgende stap in het proces kunnen de bestanden naar een externe locatie worden overgebracht.

De volgende instellingen zijn beschikbaar voor de FTP-service.

**Standaardhost:** Het IP-adres of de URL van de FTP-server.

**Standaardpoort:** De poort die wordt gebruikt om verbinding te maken met de FTP-server. De standaardwaarde is 21.

**Standaardgebruikersnaam:** De naam van de gebruikersaccount die u kunt gebruiken om toegang te krijgen tot de FTP-server. De gebruikersaccount moet voldoende rechten hebben om de FTP-bewerkingen uit te voeren die deze service vereist.

**Standaardwachtwoord:** Het wachtwoord dat met de opgegeven gebruikersnaam moet worden gebruikt voor verificatie met de FTP-server.

## PDF-service-instellingen genereren {#generate-pdf-service-settings}

Met de service PDF genereren ( `GeneratePDFService`) converteert u bestanden in verschillende oorspronkelijke indelingen naar PDF-documenten en converteert u PDF-documenten naar een aantal bestandsindelingen.

De volgende instellingen zijn beschikbaar voor de service PDF genereren.

**Adobe PDF-instellingen:** De naam van de vooraf geconfigureerde Adobe PDF-instellingen die op een conversietaak moeten worden toegepast, als deze instellingen niet zijn opgegeven als onderdeel van de API-oproepparameters. De Adobe PDF-instellingen worden geconfigureerd in de beheerconsole door te klikken op Services > PDF Generator > Adobe PDF-instellingen. Deze instellingen zijn alleen van toepassing op conversies op basis van PDFMaker.

**Beveiligingsinstellingen:** De naam van de vooraf geconfigureerde beveiligingsinstellingen die op een conversietaak moeten worden toegepast, als deze instellingen niet zijn opgegeven als onderdeel van de API-oproepparameters. De beveiligingsinstellingen worden geconfigureerd in de beheerconsole door te klikken op Services > PDF Generator > Beveiligingsinstellingen.

**Instellingen voor bestandstypen:** De naam van de vooraf geconfigureerde instelling voor het bestandstype die op een conversietaak moet worden toegepast, als deze instellingen niet zijn opgegeven als onderdeel van de API-oproepparameters. De instellingen voor bestandstypen worden geconfigureerd in de beheerconsole door te klikken op Services > PDF Generator > Instellingen voor bestandstypen.

**Acrobat WebCapture gebruiken (alleen Windows):** Als deze instelling true is, gebruikt de service PDF genereren Acrobat X Pro voor alle conversies van HTML naar PDF. Dit kan de kwaliteit van de PDF-bestanden die met HTML worden gemaakt verbeteren, maar de prestaties kunnen iets lager zijn. De standaardwaarde is false.

**Acrobat-afbeeldingsconversie gebruiken (alleen Windows):** Als deze instelling true is, gebruikt de service PDF genereren Acrobat X Pro voor alle conversies van afbeeldingen naar PDF. Deze instelling is alleen handig als het standaard conversiemechanisme voor zuiver Java een aanzienlijk deel van de invoerafbeeldingen niet kan converteren. De standaardwaarde is false.

**AutoCAD-conversies op Acrobat inschakelen (alleen Windows):** Als deze instelling true is, gebruikt de service PDF genereren Acrobat X Pro voor alle conversies van DWG naar PDF. Deze instelling is alleen handig als AutoCAD niet op de server is geïnstalleerd of als het conversiemechanisme van AutoCAD bestanden niet kan converteren.

**Reguliere expressies voor het zoeken naar verboden SpecialCharacters in gebruikersnaam (alleen Windows):** Hiermee geeft u tekens op die invloed hebben op de bewerkingen PDF exporteren en PDF optimaliseren wanneer de tekens in de naam van een gebruiker worden weergegeven.

**Poolgrootte van ImageToPDF:** De groepsgrootte van de standaard (zuivere Java) convertor voor afbeeldingen naar PDF in de service PDF genereren. Met deze instelling bepaalt u de maximale gelijktijdige conversies van afbeeldingen naar PDF die de service PDF genereren kan uitvoeren. De standaardwaarde van deze instelling (aanbevolen voor systemen met één processor) is 3, die u kunt verhogen voor systemen met meerdere processors.

**HTML naar PDF-groepsgrootte:** De groepsgrootte van de HTML-naar-PDF-converter in de service PDF genereren. Deze instelling bepaalt de maximale gelijktijdige HTML-naar-PDF-conversies die de service PDF genereren kan uitvoeren. De standaardwaarde van deze instelling (aanbevolen voor systemen met één processor) is 3, die u kunt verhogen voor systemen met meerdere processors.

**Grootte OCR-pool:** De poolgrootte van de PaperCaptureService die de PDF Generator voor OCR gebruikt. De standaardwaarde van deze instelling (aanbevolen voor systemen met één processor) is 3, die u kunt verhogen voor systemen met meerdere processors. Deze instelling is alleen geldig op Windows-systemen.

**Lettertypefamilie voor conversie van HTML naar PDF:** De naam van de lettertypefamilie die in PDF-documenten wordt gebruikt wanneer het lettertype dat in de oorspronkelijke HTML wordt gebruikt, niet beschikbaar is op de AEM-formulierserver. Geef een lettertypefamilie op als u HTML-pagina&#39;s wilt converteren waarin niet-beschikbare lettertypen worden gebruikt. Pagina&#39;s die zijn geschreven in regionale talen kunnen bijvoorbeeld niet-beschikbare lettertypen gebruiken.

**Opnieuw Logica voor native conversies** controleert PDF-generatiepogingen als de eerste poging tot conversie is mislukt:

**Niet opnieuw proberen**

Voer de PDF-conversie niet opnieuw uit als de eerste conversiepoging is mislukt

**Opnieuw**

Voer de PDF-conversie opnieuw uit, ongeacht of de time-outdrempel is bereikt. De standaardtijdsduur voor de eerste poging is 270 seconden.

**Opnieuw proberen indien tijd dit toelaat**

Voer de PDF-conversie opnieuw uit als de tijd die voor de eerste omzetpoging is verbruikt, korter is dan de opgegeven time-outduur. Als de time-outduur bijvoorbeeld 270 jaar is en de eerste poging 200 seconden heeft geduurd, wordt de conversie opnieuw uitgevoerd door PDF Generator. Als de eerste poging zelf 270 seconden verbruikte, zal de omzetting niet opnieuw worden geprobeerd.

## Instellingen voor hulplijnen ES4-hulpprogramma&#39;s {#guides-es4-utilities-service-settings}

Wanneer u een Guide maakt, worden sommige bronnen, zoals de definitie van de Guide, ingesloten in de Guide. Bronnen kunnen ook bestaan als verwijzingen naar toepassingselementen die lokaal zijn opgeslagen of op de AEM-formulierserver. De Guide bevat geen gegevens en de waarden voor de verzendlocatie en -invoer zijn niet geschikt voor alle externe omgevingen.

In de meeste gevallen zijn de standaardservices voor het weergeven van hulplijnen voldoende om een hulplijn voor te bereiden voor gebruik in Workspace of andere externe omgevingen. (In de mening van de Diensten, in Workbench, is de standaarddienst Gidsen (systeem)/Processes/Gids van de Rendering - 1.0.) Met de Guide Utilities Service ( `GuidesUtility`) kunt u, indien nodig, een aangepast proces maken voor het renderen van een Guide.

Met behulp van de Guide-hulpprogramma&#39;s kunt u de volgende rendering van hulplijnen aan een proces toevoegen:

* Bepaal of er gegevens beschikbaar zijn om de Guide te vullen
* De gegevens van de Guide insluiten of converteren naar een koppeling
* Inhoud waarnaar wordt verwezen, converteren naar URL&#39;s die extern toegankelijk zijn
* Vervangende waarden in een HTML-document of andere omslag, of zet ze om in extern toegankelijke URL&#39;s
* Verzendlocatie instellen
* Invoerwaarden opgeven
* Een parameter maken om inhoud waarnaar wordt verwezen te vertegenwoordigen
* Als er variaties beschikbaar zijn, stelt u een variatie in

De standaardwaarden voor de Guide Utilities-service ondersteunen de meeste gevallen van gebruik. Indien nodig kunt u echter de volgende waarden wijzigen.

**publicPaths:** Deze optie is vervangen. Gebruik deze optie niet bij AEM-formulieren.

**pathInfoExpiryInSeconds:** Het interval waarna een verzoek om weginformatie van een cliënt verloopt. De standaardwaarde is 1.

**lateraleExpiryInSeconds:** Het interval waarna een verzoek om onderpand van een cliënt verloopt. De standaardwaarde is 315576000.

**mismatchExpiryInSeconds:** Het interval waarna een verzoek om onderpand van een cliënt verloopt, wanneer eTag (entiteitmarkering) niet aanpast. (Een eTag is een HTTP-antwoordheader.) De standaardwaarde is 1.

**guideContext:** De basis van de context van de webtoepassing Hulplijnen. Komt overeen met de waarde die is ingesteld met de webtoepassing Hulplijnen. Standaard is /Guides/.

**secureRandomAlgorithm:** Het algoritme dat moet worden gebruikt bij het genereren van sleutels en id&#39;s. Deze waarde wordt overgegaan tot de getInstance methode van de SecureRandom klasse van Java. Standaard is SHA1PRNG.

**idBytes:** Het aantal willekeurige bytes dat voor een toetsidentificatie moet worden gebruikt. De standaardwaarde is 6.

**macAlgorithm:** Het MAC-algoritme (berichtverificatiecode) dat moet worden gebruikt voor URL-verificatie van onderpand. Deze methode wordt doorgegeven aan de methode getInstance van de Mac-klasse. Standaard is HmacSHA1.

**macRefreshIntervalInMinutes:** De hoeveelheid tijd een sleutel actief is. Wanneer een sleutel voor dit interval actief is geweest, wordt een nieuwe sleutel geproduceerd. De nieuwe toets wordt de actieve toets. De eerder actieve sleutel wordt bewaard voor 10% van het vernieuwingsinterval. Dit gedrag staat URLs toe die door de oude sleutel te gebruiken worden geproduceerd om over de belangrijkste schakelaar te blijven werken. De standaardwaarde is 144000.

**macOverlapIntervalInMinutes:** Tijdsduur dat de vorige sleutel geldig blijft nadat een nieuwe wordt gegenereerd. De standaardwaarde is 1440 minuten (1 dag).

**macKeySeed:** Een zaadwaarde voor het produceren van veilige URL. Wanneer deze optie is, wordt de sleutel nooit verfrist. Als u hetzelfde zaad op verschillende servers instelt, genereren die servers veilige URL&#39;s die compatibel zijn. Dit kan handig zijn als er meerdere formulierservers worden gebruikt achter een taakverdelingsmechanisme. Voer een willekeurige reeks tekens en cijfers in als het zaad.

### Hulplijnen gebruiken in een servercluster {#using-guides-in-a-server-cluster}

Het renderen van een Guide in een servercluster die geen kleverige sessies gebruikt, mislukt met een NullPointerException. Een verzoek van Gidsen gebruikt veilige URLs die, door gebrek, aan de server uniek zijn zij worden geproduceerd. In een cluster die kleverige zittingen gebruikt, nadat een verzoek een knoop in de cluster raakt, worden alle verdere verzoeken voor die zitting of gebruiker verpletterd exclusief aan die server, en alles is ok. In een cluster waarin geen kleverige sessies worden gebruikt, kunnen volgende aanvragen worden uitgevoerd op elke server in de cluster. Als de server waarop de aanvragen betrekking hebben, niet de oorspronkelijke server is, wordt de beveiligde URL niet opgelost.

Als u Gidsen in een servercluster gebruikt die geen kleverige zittingen gebruikt, plaats de macKeySeed waarde voor de dienst GuidesUtility, en stop en begin dan de cluster.

De macKeySeed-waarde is het zaad voor de random number generator die wordt gebruikt om de veilige URL&#39;s te genereren. Het plaatsen van deze waarde veroorzaakt elke clusterknoop om de willekeurige aantalgenerator op de zelfde manier te initialiseren, en toegang tot zelfde veilige URLs te hebben. U kunt elke willekeurige tekenreeks voor deze zaadwaarde gebruiken.

Wijzig de macKeySeed-waarde wanneer u de beveiligde URL&#39;s moet vernieuwen. Het vernieuwen van veilige URLs hangt van uw veiligheidsbeleid af, en is gelijkaardig aan verfrist beleid voor het veranderen van het hoofdwortelwachtwoord van de server. De macSeedValue is analoog aan het hoofdwachtwoord voor veilige URLs, omdat het wordt gebruikt om een nieuw uniek willekeurig aantal voor gebruik in veilige het produceren van URL en herwinning te produceren.

U moet de cluster opnieuw starten omdat macSeedValue alleen-lezen is bij het opstarten van het systeem. Alle knopen moeten opnieuw beginnen om de waarde te lezen, omdat zij het onafhankelijk gebruiken om hun interne willekeurige aantallen met de zaadwaarde te initialiseren.

## JDBC-service-instellingen {#jdbc-service-settings}

De dienst JDBC ( `JdbcService`) laat processen toe om met gegevensbestanden in wisselwerking te staan.

De volgende instelling is beschikbaar voor de JDBC-service.

**datasourceName:** Een tekenreekswaarde die de JNDI-naam vertegenwoordigt van de gegevensbron die moet worden gebruikt om verbinding te maken met de databaseserver. De gegevensbron moet worden gedefinieerd op de toepassingsserver waarop de formulierserver wordt gehost. De standaardwaarde is de JNDI-naam van de gegevensbron voor de AEM-formulierdatabase.

## JMS-service-instellingen {#jms-service-settings}

De dienst JMS ( `JMS`) laat interactie met de leveranciers van het Systeem van het Overseinen van Java (JMS) toe die zowel punt-aan-punt overseinen uitvoeren als overseinen publiceren/intekenen.

Configureer de JMS-service met standaardeigenschappen, zodat de servicebewerkingen verbinding kunnen maken met een JMS-provider en een bijbehorende JNDI-service. De waarden van de de diensteigenschappen worden geplaatst aan standaardwaarden die op de Server van de Toepassing JBoss worden gebaseerd. Wijzig deze waarden als u een andere toepassingsserver gebruikt om AEM-formulieren te hosten.

De volgende instellingen zijn beschikbaar voor de JMS-service.

**URL provider:** De URL van de JNDI-serviceprovider. De standaardwaarde is gebaseerd op de Server van de Toepassing JBoss. De volgende URL zijn standaardwaarden voor de toepassingsservers die door AEM-formulieren worden ondersteund:

**JBoss:** `<server name>:1099`

**WebLogic:** `<server name>:7001`

**WebSphere:** `<server name>:2809`

**JNDI-gebruikersnaam:** De gebruikersnaam van de account die moet worden gebruikt voor verificatie bij de JNDI-serviceprovider die wordt gebruikt voor het opzoeken van wachtrijen en onderwerpnamen. De standaardwaarde is gast.

**JNDI-wachtwoord:** Het wachtwoord dat is gekoppeld aan de gebruikersnaam die is opgegeven voor JNDI-gebruikersnaam. De standaardwaarde is gast.

**Oorspronkelijke contextfabriek:** De Java-klasse die als eerste contextfabriek moet worden gebruikt. De dienst JMS gebruikt deze klasse om een aanvankelijke context tot stand te brengen, die het uitgangspunt voor het oplossen van namen van onderwerpen en rijen is. De standaardwaarde is de aanvankelijke contextfabriek voor de dienst JMS op JBoss. De volgende klassen zijn de eerste contextfabrieken voor de toepassingsservers die door AEM-formulieren worden ondersteund:

**JBoss:** org.jnp.interfaces.NamingContextFactory

**WebLogic:** weblogic.jndi.WLInitialContextFactory

**WebSphere:** com.ibm.websphere.naming.WsnInitialContextFactory

**Gebruikersnaam verbinding:** Het wachtwoord dat aan de gebruikersnaam wordt geassocieerd voor de Gebruikersnaam van de Verbinding wordt gespecificeerd. De standaardwaarde is gast.

**Verbindingswachtwoord:** Het wachtwoord dat is gekoppeld aan de gebruikersnaam die is opgegeven voor de gebruikersnaam van de Verbinding. De standaardwaarde is gast.

**Andere eigenschappen:** De naam van het bezit en waardeparen die u aan de JNDI dienstverlener kunt overgaan. Deze eigenschappen hangen van de implementatie en de configuratie van de leverancier af die u gebruikt.

De naam- en waardeparen van de eigenschap worden gescheiden door puntkomma&#39;s **;**. De volgende tekst toont bijvoorbeeld de waarde die zou worden opgegeven voor twee eigenschappen met de naam name1 en name2, met respectievelijk waarde1 en waarde2:

`name1=value1;name2=value2`

## LDAP-service-instellingen {#ldap-service-settings}

De LDAP-service ( `LDAPService`) biedt bewerkingen voor het opvragen van LDAP-directory&#39;s. LDAP-directory&#39;s worden doorgaans gebruikt voor het opslaan van gegevens over de personen, groepen en services in een organisatie.

De volgende instellingen zijn beschikbaar voor de LDAP-service.

**Oorspronkelijke contextfabriek:** De klasse Java die als contextfabriek moet worden gebruikt. Deze klasse wordt gebruikt om een verbinding met de LDAP-server te maken. De standaardwaarde is com.sun.jndi.ldap.LDAPCtxFactory, die geschikt is voor de meeste LDAP-servers.

**URL provider:** De URL die moet worden gebruikt om verbinding te maken met de LDAP-service. De notatie van de waarde is `ldap://server name:port`

*servernaam* is de naam van de computer die als host fungeert voor de LDAP-server

*poort* is de communicatiepoort die de LDAP-service gebruikt. De standaardwaarde is 389. Dit is de standaardpoort die wordt gebruikt voor LDAP-verbindingen.

**Gebruikersnaam:** De gebruikersnaam van de gebruikersaccount die moet worden gebruikt om zich aan te melden bij de LDAP-server. De gebruikersaccount moet toestemming hebben om verbinding te maken met de server en de gegevens in de LDAP-directory te lezen.

Afhankelijk van de LDAP-server kan de gebruikersnaam een eenvoudige gebruikersnaam zijn, zoals `myname` of een DN, zoals `cn=myname,cn=users,dc=myorg`.

**Wachtwoord:** Het wachtwoord dat overeenkomt met de gebruikersnaam die is opgegeven voor de instelling Gebruikersnaam.

**Andere eigenschappen:** Een tekenreekswaarde die andere eigenschappen vertegenwoordigt en de bijbehorende waarden die u aan de LDAP-server kunt opgeven. De waarde heeft de volgende notatie:

`property=value;property=value;...`

## Microsoft SharePoint-configuratieservice-instellingen {#microsoft-sharepoint-configuration-service-settings}

Met de Microsoft SharePoint-configuratieservice `(MSSharePointConfigService)`kunt u referenties opgeven voor de gebruiker van AEM-formulieren die imitatierechten heeft. Voor informatie over imitatierechten, zie het [Vormen van de Schakelaar voor Microsoft SharePoint](https://help.adobe.com/en_US/AEMForms/6.1/SharePointConfig/index.html).

De volgende montages zijn beschikbaar voor de de configuratieservice van Microsoft SharePoint:

* Gebruikersnaam voor een gebruiker met imitatierechten
* Wachtwoord voor de bovenstaande gebruiker

**SSL inschakelen (HTTPS):**

**Tijd om te leven:** Lengte van de tijd, in seconden, dat dit inrichtingsprofiel geldig is en in het voorgeheugen ondergebracht op de cliënt. De standaardwaarde is 86400 (24 uur). Wanneer een clienttoepassing synchroniseert met de server en de opgegeven hoeveelheid tijd is verstreken, vraagt de clienttoepassing een nieuw inrichtingsprofiel aan bij de server.

**Versleuteling:** Geeft aan of gegevens die op het mobiele apparaat zijn opgeslagen, moeten worden gecodeerd.

**Forms-toepassing:** Hiermee schakelt u de functie Formulieren in de mobiele clienttoepassingen in. Als deze optie is geselecteerd, kunnen gebruikers formulieren openen en processen starten vanaf hun mobiele apparaten.

**Taken:** Hiermee schakelt u de functie Taken in de mobiele clienttoepassingen in. Als deze optie is geselecteerd, kunnen gebruikers hun taaklijsten openen en taken uitvoeren vanaf hun mobiele apparaten.

**Toepassing van Content Services:** Hiermee schakelt u de functie Content Services in de mobiele clienttoepassing in. Deze functie is alleen beschikbaar voor iOS. Als deze optie is geselecteerd, hebben gebruikers van de iPhone en de iPad toegang tot bestanden die zijn opgeslagen op de WebDAV-server van uw organisatie.

**Offlineondersteuning:** Hiermee kunnen gebruikers de mobiele clienttoepassingen blijven gebruiken, zelfs als ze geen verbinding met de server hebben (bijvoorbeeld als ze buiten het celbereik of in de vliegtuigmodus staan). Gebruikers moeten ook de instelling Offlineondersteuning op hun mobiele apparaten inschakelen. Deze functie is beschikbaar voor Android- en iOS-apparaten. Deze functie is standaard uitgeschakeld.

>[!NOTE]
>
>Als Offlineondersteuning is ingeschakeld en u deze vervolgens uitschakelt, worden de inrichtingsprofielen van de gebruikers direct of zodra ze online zijn, bijgewerkt. Als een gebruiker offline heeft gewerkt, worden alle hangende taken geretourneerd naar de lijst Taken en worden alle items in de wachtrij, inclusief formulieren, taken en formulieren met validatiefouten die in behandeling zijn, verwijderd uit de wachtrij.

**Android:** Hiermee kunnen Android-apparaten verbinding maken met de server.

**Apple iOS:** Hiermee kunnen iPhones en iPads verbinding maken met de server.

**AIR:** Hiermee kunnen apparaten die toepassingen uitvoeren op basis van Adobe AIR® verbinding maken met de server.

**BlackBerry:** Hiermee kunnen BlackBerry-apparaten verbinding maken met de server.

**Android Microsoft Exchange ActiveSync vereist:** Geeft aan of Microsoft Exchange ActiveSync beleidsmanager (EAS) moet worden geïnstalleerd en actief moet zijn op Android-apparaten. Als deze optie is geselecteerd, moet EAS worden afgedwongen op het Android-apparaat. Wanneer deze optie niet is geselecteerd, wordt geen controle uitgevoerd, hoewel andere vereisten nog steeds worden afgedwongen.

**Minimale lengte pincode voor Android:** Android-apparaten moeten een algemene instelling hebben die bepaalt dat de pincode of het wachtwoord ten minste deze lengte heeft. Het hebben van een SPELD van de gespecificeerde lengte is slechts niet voldoende. De lengte van de SPELD moet door het systeem worden afgedwongen zodat de gebruikers niet de SPELD kunnen later verwijderen of verkorten. De standaardwaarde is 4.

**Maximumwachtwoord voor Android wordt opnieuw ingevoerd voordat het programma wordt gewist:** Android-apparaten hebben een algemene instelling waarmee het systeem wordt gewist nadat een opgegeven aantal ongeldige wachtwoorden is geprobeerd. Deze globale instelling ingeschakeld en gelijk aan of lager dan de hier opgegeven waarde. De standaardwaarde is 5.

**Sluitereffect Android bij verwijderen:** Hiermee geeft u op wat er moet gebeuren als er een beleidsovertreding plaatsvindt op een Android-apparaat. Als u deze optie selecteert, wordt het account verwijderd. Als deze optie niet is geselecteerd, worden het wachtwoord voor de opgeslagen account en de gegevens in de cache verwijderd. Er worden geen synchronisatiepogingen meer uitgevoerd totdat de gebruiker de beleidsovertreding heeft opgelost.

## Instellingen voor uitvoerservice {#output-service-settings}

Met de Output-service `(OutputService)`kunt u XML-formuliergegevens samenvoegen met een formulierontwerp dat is gemaakt in AEM-formulierontwerper om een uitvoerstroom van het document in een van de volgende indelingen te maken:

* Een PDF- of PDF/A-documentuitvoerstroom.
* Een Adobe PostScript-uitvoerstroom.
* Een PCL-uitvoerstroom (Printer Control Language).
* Een ZPL-uitvoerstroom (Zebra Programming Language).

De uitvoerstream kan naar een netwerkprinter, een lokale printer of een schijfbestand worden verzonden. Wanneer u de uitvoerservice gebruikt als onderdeel van een proces, kunt u de uitvoerstream ook als bestandsbijlage naar een e-mailontvanger verzenden.

De volgende instellingen zijn beschikbaar voor de service Uitvoer.

**Transactietype:** Geeft aan hoe een transactiecontext aan een bewerking moet worden doorgegeven:

**Vereist:** steunt een transactiecontext als die reeds bestaat; anders wordt een nieuwe transactiecontext gecreëerd. Dit is de standaardwaarde.

**Nieuwe vereisten:** Creeert altijd een nieuwe transactiecontext. Als er een actieve transactiecontext bestaat, wordt deze opgeschort.

**Tijd van transactie uit (in sec.):** Het aantal seconden dat de onderliggende transactieleverancier wacht alvorens een transactie terug te rollen die deze verrichting verpakt. Deze waarde wordt genegeerd als een bestaande transactiecontext wordt verspreid.

Wanneer het verwerken van grote gegevensdossiers of werkend op een bezige server, kan het noodzakelijk zijn om de de diensttijd van de Output uit te verhogen. Als u de time-outwaarde wilt wijzigen, moet u ervoor zorgen dat de hardwareservers over voldoende geheugen beschikken en dat het geheugen beschikbaar is voor de Java Application Server-heap. De standaardwaarde is `180`.

## Instellingen van PDFG Config-service {#pdfg-config-service-settings}

De volgende instellingen zijn beschikbaar voor de service PDFG Config ( `PDFGConfigService`).

**Map met taakopties gebruiker:** Het pad van de bestandssysteemmap waarin de C-service de bestanden met taakopties schrijft die toegankelijk zijn voor Acrobat Pro Extended. De standaardwaarde is [user.home]/Application Data/Adobe/Adobe PDF/Settings.

**Opstartmap van PS:** Het pad van de bestandssysteemmap waarin de opstartbestanden zijn opgeslagen die door Adobe Acrobat Distiller worden vereist. De standaardwaarde is [user.home]/Application Data/Adobe/Adobe PDF/Distiller/Startup.

**PS Opstartbestand:** De naam van het opstartbestand dat door Adobe Acrobat Distiller wordt vereist. De standaardwaarde is example.ps.

**Time-out serverconversie:** De maximale time-out voor taakconversie (in seconden) voor de service PDF genereren en Distiller. Met deze instelling wordt de maximale time-out voor conversie beperkt die kan worden opgegeven in het bestand config.xml en in de beheerconsolepagina&#39;s voor PDF Generator. De standaardwaarde is 270.

**Globale time-out server:** Tijdens het uitvoeren van PDF-conversies houdt een formulierserver rekening met de time-outlimiet. Configureer de time-outwaarde om het probleem op te lossen.

**Voorvoegsel taakopties:** Een voorvoegsel dat door de service PDF genereren wordt gebruikt om een korte tekenreeks aan te vullen met de bestanden met taakopties die tijdelijk worden gemaakt voor gebruik door Acrobat Distiller. De standaardwaarde is pdfg.

**Niet-Unicode-toepassingen:** Een door komma&#39;s gescheiden lijst met toepassingsnamen waarvan bekend is dat ze Unicode-niet kunnen bevatten. Deze lijst is vooraf ingevuld met de namen van verschillende toepassingen, waarvoor de ondersteuning vooraf is geconfigureerd in PDF Generator. Als u ondersteuning voor PDF-conversies wilt toevoegen via andere toepassingen van derden die Unicode-niet kunnen gebruiken, moet u deze toevoegen aan deze lijst. De standaardwaarde is Autocad, Excel, PowerPoint, Project, Publisher, Visio, Word, WordPerfect.

**Aantal serverthreadpool:** Hiermee regelt u de grootte van de thread-pool die de Generate PDF-service intern gebruikt voor de service van HTML-naar-PDF-conversieverzoeken die spidering vereisen (gekoppelde pagina&#39;s die toegankelijk zijn vanaf de hoofdpagina converteren). De standaardwaarde is 20.

**Seconden van PDFG-opschoning:** Zie de sectie Seconden voor taakvervaldatums voor meer informatie.

**Seconden van taakvervaldatum:** Met de service PDF genereren verwijdert u invoerbestanden zodra deze worden geconverteerd. De uitvoerbestanden worden tijdelijk opgeslagen, gedurende een periode die wordt bepaald door de instellingen Seconden van PDFG-opschoning en Seconden voor taakvervaldatum.

Met de instelling Seconden voor taakvervaldatum bepaalt u hoe oud een bestand of lege map moet zijn voordat het bestand kan worden verwijderd. Met de instelling Seconden van PDFG Cleanup Scan bepaalt u hoe vaak de tijdelijke mappen door een opschoonthread worden gescand op bestanden die kunnen worden verwijderd.

Bijvoorbeeld, als de Seconden van de Vervalsing van de Baan aan 100 wordt geplaatst en de Seconden van het Scannen PDFG van de Schoonmaakbeurt aan 200 wordt geplaatst, stelt de schoonmaakdraad om de 200 seconden in werking en schrapt dossiers die 100 seconden of ouder zijn.

De standaardwaarde voor seconden van PDFG Cleanup Scan is `43200` (12 uur). De standaardwaarde van Seconden van de Vervaltijd van de Baan is `86400` (24 uren).

**Standaardlandinstelling:** Hiermee overschrijft u de standaardlandinstelling (land + taal) van de server waarop de service PDF genereren is geïmplementeerd. Als deze parameter niet gespecificeerd is, dan wordt de standaardscène bepaald van het werkende systeem waarop de dienst wordt opgesteld. Deze parameter bestuurt de taal waarin de foutenmeldingen aan APIs zijn teruggekeerd.

## formulierworkflows voor Data Services-services {#forms-workflow-data-services-service-settings}

De volgende diensten breiden de Diensten van Gegevens uit en stellen assembleurs bloot die de Werkruimte gebruikt om met de server te spreken. Wijzig de configuratieopties voor deze services alleen als u hiervoor instructies hebt gekregen van de ondersteuning van Adobe. Deze diensten zijn niet bedoeld voor directe toegang:

* `ProcessManagementLcdsAttachmentService`
* `ProcessManagementLcdsPropertyService`
* `ProcessManagementLcdsTaskService`

## Service-instellingen verwijderen {#remoting-service-settings}

De meeste services zijn zo geconfigureerd dat u toegang hebt tot deze services via AEM-formulieren (afgekeurd voor AEM-formulieren) verwijderen. Zie [Programmeren met AEM-formulieren](https://adobe.com/go/learn_aemforms_programming_63)voor informatie over (Vervangen voor AEM-formulieren) AEM-formulieren Verwijderen.

De volgende instellingen zijn beschikbaar voor de service Remoting.

**Flex-clientverificatiemethode:** Bepaalt het type van reactie dat de server terug naar de cliënt verzendt wanneer de aangehaalde dienst toegelaten veiligheid is, steunt de aangehaalde verrichting geen anonieme aanroepen, en de cliënt gaat of in geen of ongeldige geloofsbrieven over. Kies Aangepast of Standaard. De standaardwaarde is Standaard.

**Serienummering van klassen zonder serienummering toestaan:** Bij de meeste eindpunten van AEM-formulieren kunnen alleen klassen met serienummering worden gebruikt voor aanroepen. In oudere versies, stond het Remoting eindpunt niet-Serializable klassen toe om voor aanroeping van op Flex-Gebaseerde cliënten worden gebruikt. Om een beveiligingskwetsbaarheid te voorkomen die in APS11-15 wordt beschreven, is deze kwetsbaarheid gewijzigd. Als u niet-Serializable klassen met het Flex Remoting eindpunt wilt blijven gebruiken, selecteer dit checkbox.

## Instellingen voor opslagplaats {#repository-service-settings}

De dienst van de Bewaarplaats ( `RepositoryService`) verleent de opslag van middelen en beheersdiensten aan AEM vormen. Wanneer ontwikkelaars een toepassing maken, kunnen ze de elementen in de opslagplaats implementeren in plaats van in een bestandssysteem. De elementen kunnen elk type element bevatten, zoals XML-formulieren, PDF-formulieren (inclusief Acrobat-formulieren), formulierfragmenten, afbeeldingen, profielen, beleid, SWF-bestanden, DDX-bestanden, XML-schema&#39;s, WSDL-bestanden en testgegevens.

U kunt de standaardopslagplaats gebruiken die bij AEM-formulieren wordt geleverd, of een externe opslagplaats gebruiken (EMC Documentum Content Server, IBM FileNet Content Manager of IBM Content Manager).

De dienst van de Leverancier van de opslagplaats is een de dienstafgevaardigde die als interface aan een leveranciersdienst dienst dienst dienst dienst doet. Hierdoor kunt u verbinding maken met een gemeenschappelijke API en hoeft u zich niet te realiseren welke provider de opslagmogelijkheden implementeert. De dienst van de Leverancier van de Bewaarplaats verstrekt gegevensbestandopslag voor de de dienstmiddelen van de Bewaarplaats.

De volgende instelling is beschikbaar voor de Repository-service.

**Provider-service:** De naam van de service die als opslagprovider wordt gebruikt. De standaardwaarde is RepositoryProviderService.

## Instellingen voor handtekeningenservice {#signature-service-settings}

Met de service Handtekening ( `SignatureService`) kan uw organisatie de beveiliging en privacy beschermen van Adobe PDF-documenten die worden gedistribueerd en ontvangen. Deze service gebruikt digitale handtekeningen en certificering om ervoor te zorgen dat documenten niet worden gewijzigd. Als u een document wijzigt, wordt de handtekening verbroken. Aangezien beveiligingsfuncties op het document zelf worden toegepast, blijft het document gedurende de gehele levenscyclus beveiligd en beheerd. buiten de firewall, wanneer het offline wordt gedownload, en wanneer het terug naar uw organisatie wordt voorgelegd.

De volgende instellingen zijn beschikbaar voor de service Handtekening.

**Naam van de externe HSM SPI-service:** Deze optie is voor gebruik wanneer HSM op een verre computer wordt geïnstalleerd. Geef deze optie op wanneer AEM-formulieren op een 64-bits Windows zijn geïnstalleerd en u HSM-apparaten gebruikt voor ondertekening.

**URL van de externe HSM-webservice:** Geef deze optie op wanneer AEM-formulieren zijn geïnstalleerd op 64-bits Windows en u HSM-apparaten gebruikt voor ondertekening.

**Certificering om wijzigingen in het laden van formulieren op te nemen:** Als deze optie is geselecteerd, wordt de XFA-formulierstatus gecertificeerd in aanvulling op de XFA-sjabloon. Houd er rekening mee dat het inschakelen van deze optie negatieve gevolgen kan hebben voor de prestaties. De standaardwaarde is true.

**JavaScript-scripts voor documenten uitvoeren:** Hiermee wordt opgegeven of JavaScript-scripts voor documenten moeten worden uitgevoerd tijdens handtekeningbewerkingen. De standaardwaarde is false.

**Documenten verwerken met Acrobat 9-compatibiliteit:** Hiermee geeft u aan of Acrobat 9-compatibiliteit moet worden ingeschakeld. Als deze optie bijvoorbeeld is geselecteerd, wordt Zichtbare certificering in dynamische PDF&#39;s ingeschakeld. De standaardwaarde is false.

**Intrekkingsgegevens insluiten tijdens ondertekenen:** Hiermee geeft u aan of intrekkingsinformatie wordt ingesloten tijdens het ondertekenen van het PDF-document. De standaardwaarde is false.

**Intrekkingsgegevens insluiten tijdens certificering:** Hiermee geeft u aan of de intrekkingsinformatie wordt ingesloten tijdens de certificering van het PDF-document. De standaardwaarde is false.

**Insluiten van intrekkingsinformatie voor alle certificaten afdwingenTijdens ondertekening/certificering:** Geeft aan of een ondertekenings- of certificeringsbewerking mislukt als geldige intrekkingsgegevens voor alle certificaten niet zijn ingesloten. Als een certificaat geen CRL- of OCSP-informatie bevat, wordt het als geldig beschouwd, zelfs als er geen intrekkingsinformatie wordt opgehaald. De standaardwaarde is false.

**Intrekkingscontrole:** Hiermee geeft u de volgorde op van de intrekkingscontrole wanneer controle mogelijk is via de mechanismen certificaatintrekkingslijst (CRL) en het online certificaatstatusprotocol (OCSP). De standaardwaarde is OCSPFirst.

**Maximale grootte archiveringsgegevens voor intrekking:** De maximale grootte van de archiefgegevens voor intrekking in kilobytes. AEM-formulieren proberen zoveel mogelijk intrekkingsgegevens op te slaan zonder de limiet te overschrijden. De standaardwaarde is 10 kB.

**Ondertekeningen ondersteunen die zijn gemaakt op basis van prerelease-build van Adobe-producten:** Als deze optie is geselecteerd, wordt een handtekening die is gemaakt met de pre-releaseversie van Adobe-producten correct gevalideerd. De standaardwaarde is false.

**Optie voor controletijd:** Hiermee geeft u de tijd op waarop het certificaat van een ondertekenaar wordt geverifieerd. De standaardwaarde is Beveiligde tijd anders dan huidige tijd.

**Intrekkingsgegevens gearchiveerd in handtekening gebruiken tijdens validatie:** Hiermee wordt opgegeven of de intrekkingsinformatie die met de handtekening wordt gearchiveerd, wordt gebruikt voor intrekkingscontrole. De standaardwaarde is true.

**Gebruik de validatiegegevens die in het document zijn opgeslagen voor de validatie van handtekeningen:** Als deze optie is geselecteerd, worden validatiegegevens (waaronder informatie over intrekking en tijdstempel) die in het document zijn ingesloten, gebruikt om handtekeningen te valideren. De standaardwaarde is true.

**Maximaal aantal geneste verificatiesessies toegestaan:** Het maximum aantal geneste verificatiesessies dat is toegestaan. AEM-formulieren gebruiken deze waarde om een oneindige lus te voorkomen bij het controleren van de OCSP- of CRL-ondertekenaarcertificaten wanneer het OCSP- of CRL-certificaat niet correct is ingesteld. De standaardwaarde is 10.

**Maximale schuintrekken klok voor verificatie:** De maximale tijd, in minuten, die de ondertekeningstijd na de validatietijd kan zijn. Als de klok meer schuin is dan deze waarde, is de handtekening niet geldig. De standaardwaarde is 65 minuten.

**Certificaatlevenscache:** De levensduur van een certificaat, dat online of via andere middelen wordt opgehaald, in de cache. De standaardwaarde is 1 dag.

### Vervoersopties {#transport-options}

**Host proxy:** De URL van de proxyhost. Wordt alleen gebruikt als er een geldige waarde is opgegeven. Geen standaardwaarde.

**Proxypoort:** De proxypoort. Typ een geldig poortnummer tussen 0 en 65535. De standaardwaarde is 80.

**Gebruikersnaam inlognaam proxy:** De gebruikersnaam voor de proxyaanmelding. Wordt alleen gebruikt als er een geldige waarde is opgegeven voor de proxyhost en -poort. Geen standaardwaarde.

**Wachtwoord voor aanmelding bij proxy:** Het wachtwoord voor proxyaanmelding. Wordt alleen gebruikt als een geldige waarde is opgegeven voor de gebruikersnaam van de proxyhost, proxypoort en proxyaanmelding. Geen standaardwaarde.

**Maximale downloadlimiet:** De maximale hoeveelheid gegevens, in MBs, die per verbinding kan worden ontvangen. De minimumwaarde is 1 MB en de maximumwaarde is 1024 MB. De standaardwaarde is 16 MB.

**Verwerkingstijd:** De maximumtijd om, in seconden, voor het vestigen van een nieuwe verbinding te wachten. De minimumwaarde is 1 en de maximumwaarde is 300. De standaardwaarde is 5.

**Time-out socket:** De maximale tijd die in seconden moet worden gewacht voordat een time-out van de socket (tijdens het wachten op gegevensoverdracht) optreedt. De minimumwaarde is 1 en de maximumwaarde is 3600. De standaardwaarde is 30.

### Opties voor padvalidatie {#path-validation-options}

**Expliciet beleid vereisen:** Geeft aan of het pad geldig moet zijn voor ten minste een van de certificaatbeleidsregels die is gekoppeld aan het vertrouwensanker van het ondertekenaarcertificaat. De standaardwaarde is false.

**Elk beleid blokkeren:** Geeft aan of de OID (beleidsobject-id) moet worden verwerkt als deze in een certificaat is opgenomen. De standaardwaarde is false.

**Beleidstoewijzing onderdrukken:** Geeft aan of beleidstoewijzing is toegestaan in het certificeringspad. De standaardwaarde is false.

**Alle paden controleren:** Hiermee geeft u aan of alle paden moeten worden gevalideerd of dat validatie moet worden gestopt nadat het eerste geldige pad is gevonden. Selecteer waar of onwaar. De standaardwaarde is false.

**LDAP-server:** De LDAP-server die wordt gebruikt voor het opzoeken van certificaten voor padvalidatie. Geen standaardwaarde.

**URI&#39;s in Certificate AIA volgen:** Geeft aan of URI&#39;s (Uniform Resource Identifiers) in Certificate AIA worden verwerkt tijdens paddetectie. De standaardwaarde is false.

**Basic Restrictions Extension required in CA Certificates:** Bepaalt of de certificaatextensie voor basisbeperkingen van de certificeringsinstantie (CA) aanwezig moet zijn voor CA-certificaten. Sommige vroege Duitse gecertificeerde basiscertificaten (7 en eerder) zijn niet compatibel met RFC 3280 en bevatten niet de basisbeperkingsextensie. Schakel dit selectievakje uit als u weet dat het EE-certificaat van een gebruiker is gekoppeld aan een dergelijk Duits basiscertificaat. De standaardwaarde is true.

**Geldige certificaatondertekening vereisen tijdens het opbouwen van de keten:** Geeft aan of de ketenontwikkelaar geldige handtekeningen vereist op certificaten die worden gebruikt om ketens te bouwen. Wanneer deze controledoos wordt geselecteerd, zal de ketenbouwer geen ketens met ongeldige RSA handtekeningen op certificaten bouwen. Overweeg keten CA > ICA > EE waar de handtekening van CA op een ICA niet geldig is. Als dit het plaatsen waar is, zal het ketengebouw bij ICA ophouden, en CA zal niet in de ketting worden omvat. Als deze instelling onwaar is, wordt de volledige certificaatketen van drie pixels geproduceerd. Deze instelling heeft geen invloed op DSA-handtekeningen. De standaardwaarde is false.

### Opties tijdstempelprovider {#timestamp-provider-options}

**URL TSP-server:** De URL van de standaardtijdstempelprovider. Wordt alleen gebruikt als er een geldige waarde is opgegeven. Geen standaardwaarde.

**Gebruikersnaam TSP-server:** De gebruikersnaam indien vereist door het tijdstempelbureau. Wordt alleen gebruikt als er een geldige waarde voor de URL is opgegeven. Geen standaardwaarde.

**Wachtwoord TSP-server:** Het wachtwoord voor de bovenstaande gebruikersnaam indien vereist door de tijdstempelprovider. Wordt alleen gebruikt als er een geldige waarde voor de URL en de gebruikersnaam is opgegeven. Geen standaardwaarde.

**Hash-algoritme aanvragen:** Geeft aan welk hash-algoritme moet worden gebruikt bij het maken van de aanvraag voor de tijdstempelprovider. De standaardwaarde is SHA1.

**Stijl intrekkingscontrole:** Geeft de stijl van de intrekkingscontrole aan die wordt gebruikt om de vertrouwensstatus van het certificaat van de tijdstempelprovider te bepalen op basis van de waargenomen intrekkingsstatus. De standaardwaarde is BestEfficient.

**Nonce verzenden:** Geeft aan of een nonce wordt verzonden met de aanvraag voor de tijdstempelprovider. Een nonce kan een tijdstempel, een bezoekersteller op een webpagina zijn of een speciale markering die bedoeld is om het ongeoorloofd afspelen of het reproduceren van een bestand te beperken of te voorkomen. De standaardwaarde is true.

**Verlopen tijdstempels gebruiken tijdens validatie:** Als deze optie is geselecteerd, kunnen verlopen tijdstempels worden gebruikt om validatietijden van handtekeningen op te halen. De standaardwaarde is true.

**Grootte TSP-respons:** Geschatte grootte, in bytes, van de TSP-respons. Deze waarde moet de maximale grootte vertegenwoordigen van de tijdstempelreactie die de geconfigureerde tijdstempelprovider kan retourneren. Wijzig dit alleen als u er absoluut zeker van bent. De minimumwaarde is 60B en de maximumwaarde is 10240B. De standaardwaarde is 4096B.

**Tijdstempelserverextensie** negeren: Schakel de optie **Tijdstempelserverextensie** negeren in om te voorkomen dat de AEM Forms-server verbinding maakt met de opgegeven tijdstempelserver. Als u deze optie selecteert, voorkomt u procesfouten die optreden als gevolg van een time-out van de verbinding tussen AEM Forms en tijdstempelservers.

### Opties voor certificaatintrekkingslijst {#certificate-revocation-list-options}

**Raadpleeg eerst lokale URI:** Geeft aan of de CRL-locatie die wordt opgegeven in Lokale URI of CRL Opzoeken, voor de intrekkingscontrole de voorkeur moet krijgen boven elke locatie die is opgegeven in een certificaat. De standaardwaarde is false.

**Lokale URI voor CRL Opzoeken:** URL van de lokale CRL-provider. Deze waarde wordt alleen geraadpleegd als de instelling Eerst lokale URI raadplegen is ingesteld op true. Geen standaardwaarde.

**Stijl intrekkingscontrole:** Hiermee geeft u de stijl voor intrekkingscontrole op die wordt gebruikt om de vertrouwensstatus van het certificaat van de CRL-provider te bepalen op basis van de waargenomen intrekkingsstatus. De standaardwaarde is BestEfficient.

**LDAP-server voor opzoeken van CRL:** De LDAP-server die wordt gebruikt om de CRL&#39;s op te halen (als www.ldap.com). Alle op DN gebaseerde vragen voor CRLs zullen aan deze server worden geleid. Geen standaardwaarde.

**Online gaan:** Geeft aan of u online wilt gaan om een CRL op te halen. Indien onwaar worden alleen in de cache opgeslagen CRL&#39;s (op de lokale schijf of op de ingesloten CRL&#39;s) geraadpleegd. De standaardwaarde is true.

**Geldigheidsdatums negeren:** Geeft aan of de tijden thisUpdate en nextUpdate van de reactie moeten worden genegeerd, waardoor wordt voorkomen dat deze tijden een negatief effect hebben op de geldigheid van de reactie. De standaardwaarde is false.

**AKI-extensie vereisen in CRL:** Geeft aan of de extensie Hoofd-id moet worden opgenomen in een CRL. De standaardwaarde is false.

### Opties online certificaatstatusprotocol {#online-certificate-status-protocol-options}

**URL OCSP-server:** URL voor de standaard OCSP server. Of de OCSP-server die via deze URL is opgegeven, wordt gebruikt, is afhankelijk van de instelling van de optie URL naar advies. Geen standaardwaarde.

**URL voor raadpleging, optie:** Beheert de lijst en de orde van de servers OCSP die voor het uitvoeren van de statuscontrole worden gebruikt. De standaardwaarde is UseAIAInCert.

**Stijl intrekkingscontrole:** Hiermee wordt de stijl voor intrekkingscontrole opgegeven die wordt gebruikt bij het controleren van het certificaat van de OCSP-server. De standaardwaarde is CheckIfAvailable.

**Nonce verzenden:** Geeft aan of een nonce wordt verzonden met de OCSP-aanvraag. Een nonce kan een tijdstempel, een bezoekersteller op een webpagina zijn of een speciale markering die bedoeld is om het ongeoorloofd afspelen of het reproduceren van een bestand te beperken of te voorkomen. De standaardwaarde is true.

**Maximale scheeftrektijd klok:** Maximaal toegestane scheeftrekking, in minuten, tussen responstijd en lokale tijd. De minimumwaarde is 0 en de maximumwaarde is 2147483647m. De standaardwaarde is 5 m.

**Vrachttijd reactie:** Maximale tijd, in minuten, waarvoor een vooraf geconstrueerde OCSP-respons als geldig wordt beschouwd. De minimumwaarde is 1 m en de maximaal toegestane waarde is 2147483647. De standaardwaarde is 525600 (één jaar).

**OCSP-aanvraag ondertekenen:** Geeft aan of het OCSP-verzoek moet worden ondertekend. De standaardwaarde is false.

**Referentiealias ondertekenaar aanvragen:** Specificeert de referentie alias voor het ondertekenen van het OCSP verzoek als het ondertekenen wordt toegelaten. Wordt alleen gebruikt als de ondertekening van een OCSP-aanvraag is ingeschakeld. Geen standaardwaarde.

**Online gaan:** Hiermee geeft u aan of u online wilt gaan om intrekkingscontroles uit te voeren. De standaardwaarde is true.

**Negeer de reactietijden thisUpdate en nextUpdate:** Geeft aan of de tijden thisUpdate en nextUpdate van de reactie moeten worden genegeerd, waardoor wordt voorkomen dat deze tijden een negatief effect hebben op de geldigheid van de reactie. De standaardwaarde is false.

**OCSPNoCheck-extensie toestaan:** Hiermee wordt opgegeven of de OCSPNoCheck-extensie is toegestaan in het handtekeningcertificaat voor het antwoord. De standaardwaarde is true.

**OCSP ISIS-MTT CertHash-extensie vereisen:** Geeft aan of een hash-extensie voor een openbare-sleutelcertificaat moet worden opgenomen in OCSP-reacties. De standaardwaarde is false.

### Opties voor foutafhandeling {#error-handling-options-for-debugging}

**Certificaatcache wissen bij volgende API-aanroep:** Geeft aan of de Certificaatcache moet worden gewist wanneer de volgende Handtekeningsservice-bewerking wordt aangeroepen. Nadat de bewerking is aangeroepen, wordt deze optie teruggezet op false. De standaardwaarde is false.

**CRL-cache wissen bij volgende API-aanroep:** Geeft aan of de CRL-cache moet worden gewist wanneer de volgende Handtekeningsservice-bewerking wordt aangeroepen. Nadat de bewerking is aangeroepen, wordt deze optie teruggezet op false. De standaardwaarde is false.

**OCSP-cache wissen bij volgende API-aanroep:** Geeft aan of de OCSP-cache moet worden gewist wanneer de volgende Handtekeningsservice-bewerking wordt aangeroepen. Nadat de bewerking is aangeroepen, wordt deze optie teruggezet op false. De standaardwaarde is false.

## Instellingen voor gecontroleerde mapservice {#watched-folder-service-settings}

Met de service Gecontroleerde map ( `WatchedFolder`) configureert u kenmerken die veel voorkomen in alle gecontroleerde eindpunten van mappen. De klasse biedt ook standaardwaarden voor gecontroleerde eindpunten van mappen. (Zie [Gecontroleerde mapeindpunten](/help/forms/using/admin-help/configuring-watched-folder-endpoints.md#configuring-watched-folder-endpoints)configureren.) Het wordt niet aangehaald door externe cliënttoepassingen of gebruikt in processen die in Workbench worden gecreeerd.

De volgende instellingen zijn beschikbaar voor de service Gecontroleerde map.

**Uitsnijduitdrukking:** De expressie voor uitsnijden, zoals gebruikt door kwarts om de opiniepeiling van de invoermap te plannen.

**Aantal herhalingen:** Het aantal keren dat de invoermap wordt gepolled. De standaardherhalingstelling om te gebruiken als deze waarde niet in de eindpuntconfiguratie wordt gespecificeerd. De waarde -1 geeft aan dat de map voor onbepaalde tijd wordt gescand. De standaardwaarde is -1.

**Interval herhalen:** Het standaardaantal als seconden tussen elke opiniepeiling. Deze waarde wordt gebruikt als herhalingsinterval tenzij een verschillende waarde in de gecontroleerde configuratie van het omslageindpunt wordt gespecificeerd. De standaardwaarde is 5. Zie de beschrijving van de instelling Batchgrootte voor meer informatie.

**Asynchroon:** Identificeert het aanroepingstype als asynchroon of synchroon. De voorbijgaande en synchrone processen kunnen slechts synchroon worden aangehaald. De standaardwaarde is asynchroon.

**Wacht tijd:** De standaardwaarde voor tijd, in seconden, waarna de bestanden uit de invoermappen worden opgehaald. Als het bestand of de map ouder is dan de in de wachttijd opgegeven tijd, wordt het bestand of de map opgehaald voor verwerking. De standaardwaarde is 0.

**Batchgrootte:** De standaardwaarde voor het aantal bestanden of mappen dat per scan wordt verwerkt. De standaardwaarde is 2.

Met de instellingen voor Interval herhalen en Batchgrootte bepaalt u hoeveel bestanden in Gecontroleerde map worden opgehaald bij elke scan. De gecontroleerde Omslag gebruikt een de draadpool van het Kwartz om de inputomslag af te tasten. De draadpool wordt gedeeld met andere diensten. Als het scaninterval klein is, scannen de threads de invoermap vaak. Als bestanden vaak in de controlemap worden geplaatst, moet u het scaninterval klein houden. Als de dossiers niet vaak worden gelaten vallen, gebruik een groter aftasteninterval zodat de andere diensten de draden kunnen gebruiken.

Als er een groot volume bestanden verloren gaat, maakt u de batch groot. Als de service die wordt aangeroepen door het gecontroleerde mapeindpunt bijvoorbeeld 700 bestanden per minuut kan verwerken en gebruikers bestanden naar dezelfde snelheid in de invoermap kunnen neerzetten, helpt het instellen van Batchgrootte op 350 en Herhalingsinterval op 30 seconden de prestaties van gecontroleerde mappen te controleren zonder de kosten voor het te vaak doorzoeken van de gecontroleerde map op te lopen.

Wanneer bestanden in de controlemap worden neergezet, worden de bestanden in de invoer weergegeven. Hierdoor kunnen de prestaties afnemen wanneer elke seconde wordt gescand. Het verhogen van het aftasteninterval kan prestaties verbeteren. Als het volume van de dossiers dat klein is wordt gelaten vallen, pas de Grootte van de Partij en Interval dienovereenkomstig aan. Als er bijvoorbeeld elke seconde 10 bestanden worden verwijderd, stelt u het interval voor herhalen in op 1 seconde en de waarde voor Batchgrootte op 10.

In een clusterconfiguratie, schrapt de partijgrootte voor een gecontroleerd omslageindpunt niet aan veelvoudige clusterknopen. Als de batchgrootte bijvoorbeeld is ingesteld op `2` voor een cluster met twee knooppunten en de optie Throttle is geselecteerd, verwerken de knooppunten gezamenlijk bestanden in batches van twee in plaats van elk knooppunt dat twee bestanden tegelijk verwerkt.

**Dubbele bestandsnamen overschrijven:** Een Booleaanse tekenreeks die aangeeft of de gecontroleerde map dubbele resultaatbestandsnamen overschrijft en of behouden documenten met dezelfde naam moeten worden overschreven.

**Map behouden:** De standaardwaarde voor de map preserve. Deze map wordt gebruikt om de bronbestanden te kopiëren naar in geval van een geslaagde verwerking van de invoer. Deze waarde kan een leeg, relatief of absoluut pad zijn met een bestandspatroon zoals beschreven voor de instelling Map met resultaten.

**Map mislukt:** De naam van de map waarnaar de foutbestanden worden gekopieerd. Deze waarde kan een leeg, relatief of absoluut pad zijn met een bestandspatroon zoals beschreven voor de instelling Map met resultaten.

**Map met resultaten:** De standaardnaam voor de resultaatmap. Deze map wordt gebruikt om de resultatenbestanden naar te kopiëren. Deze waarde kan een leeg, relatief of absoluut pad zijn met het volgende bestandspatroon.

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
* %R = willekeurig getal (van 0 tot en met 9)
* %P = proces- of taak-id

Als de waarde op 17 juli 2009 bijvoorbeeld 8 uur is en u opgeeft `C:/Test/WF0/failure/%Y/%M/%D/%H/`, is de resultatenmap `C:/Test/WF0/failure/2009/07/17/20`.

Als het pad niet absoluut maar relatief is, wordt de map in de controlemap gemaakt. Zie [Bestandspatronen](/help/forms/using/admin-help/configuring-watched-folder-endpoints.md#about-file-patterns)voor meer informatie over bestandspatronen.

>[!NOTE]
>
>Hoe kleiner de resulterende mappen, hoe beter Gecontroleerde mappen. Als het geschatte laden voor de gecontroleerde map bijvoorbeeld 1000 bestanden per uur is, probeert u een patroon als `result/%Y%M%D%H` zodat er elk uur een nieuwe submap wordt gemaakt. Als het laden kleiner is (bijvoorbeeld 1000 bestanden per dag), kunt u een patroon gebruiken zoals `result/%Y%M%D`.

**Werkgebiedmap:** De standaardnaam voor de werkgebiedmap in de controlemap.

**Invoermap:** De standaardnaam voor de invoermap in de controlemap.

**Behouden bij fout:** Indien waar (true), blijven de oorspronkelijke bestanden behouden in de map met foutmeldingen.

**Throttle:** Als deze optie is geselecteerd, wordt het aantal controletaken dat door AEM-formulieren op een bepaald moment wordt verwerkt, beperkt. De waarde voor Batchgrootte bepaalt het maximale aantal taken (zie Informatie over vertragen).

## Instellingen webservice {#web-service-service-settings}

De dienst van de Dienst van het Web ( `WebService`) laat processen toe om de verrichtingen van de Webdienst aan te halen.

De dienst van de Dienst van het Web laat processen toe om de verrichtingen van de Webdienst aan te halen. Een organisatie kan bijvoorbeeld een proces voor het opslaan en ophalen van informatie, zoals contact- en accountgegevens, willen integreren door de onzichtbare webservices van een serviceprovider aan te roepen. De dienst van de Dienst van het Web haalt een gespecificeerde Webdienst aan en gaat door waarden voor elk van zijn parameters over. Vervolgens worden de geretourneerde waarden van de bewerking opgeslagen in een toegewezen variabele binnen een proces.

De dienst van de Dienst van het Web wisselt met Webdiensten door de berichten van de ZEEP te verzenden en te ontvangen. De dienst steunt ook het verzenden MIME, MTOM, en de gehechtheid SwaRef met de berichten van de ZEEP door het WS-Bijlage protocol te gebruiken. De de dienstinteractie van de Dienst van het Web is compatibel met de systemen van SAP en .NET Webdiensten.

De volgende montages zijn beschikbaar voor de dienst van de Dienst van het Web.

**Topwinkel:** Het volledige pad van het sleutelarchiefbestand dat de persoonlijke sleutel bevat die voor verificatie moet worden gebruikt. De formulierserver moet toegang hebben tot het bestand.

**Wachtwoord sleutelarchief:** Het wachtwoord voor het sleutelarchiefbestand.

**Type sleutelwinkel:** Het type sleutelarchief. Geef geen waarde op om het standaardsleutelarchieftype te gebruiken dat is geconfigureerd voor de JVM die de formulierserver uitvoert. Geef anders een van de volgende waarden op:

* jks
* pkcs12
* cms
* jceks

**Betrouwbaarheidswinkel:** Het volledige pad van het vertrouwde opslagbestand dat de openbare sleutel van de webserviceserver bevat.

**Wachtwoord voor winkel vertrouwen:** Het wachtwoord voor het bestand truststore.

**Type vertrouwde winkel:** Het type van truststore. Geef geen waarde op om het standaardsleutelarchieftype te gebruiken dat is geconfigureerd voor de JVM die de formulierserver uitvoert. Geef anders een van de volgende waarden op:

* jks
* pkcs12
* cms
* jceks

## XSLT Transformation Service Settings {#xslt-transformation-service-settings}

Met de XSLT Transformation Service ( `XSLTService`) kunnen processen Extensible Stylesheet Language Transformations (XSLT) toepassen op XML-documenten.

De volgende instelling is beschikbaar voor de service XSLT-transformatie.

**Fabrieksnaam:** De volledig gekwalificeerde naam van de Java-klasse die moet worden gebruikt voor het uitvoeren van XSLT-transformaties. Als er geen waarde is opgegeven, wordt de standaardfabriek gebruikt die is geconfigureerd in de Java Virtual Machine die de formulierserver uitvoert.

## Beveiligingsinstellingen voor een service wijzigen {#modifying-security-settings-for-a-service}

De server van vormen laat u toe om veiligheidsmontages voor elke dienst te vormen, die u toestaat om fijnkorrelig toegangsbeheer op een dienst-door-dienst niveau te vormen.

Er zijn standaardbeveiligingsprofielen geïnstalleerd, die vervolgens kunnen worden geconfigureerd om aan uw systeembehoeften te voldoen. Elk beveiligingsprofiel heeft een gekoppeld domein en wordt op gebruikersniveau of groepsniveau gemaakt.

### Beveiligingsinstellingen wijzigen voor een service {#modify-security-settings-for-a-service}

1. Klik in de beheerconsole op Services > Toepassingen en services > Servicebeheer.
1. Voor de pagina van het Beheer van de Dienst, klik de dienst om te vormen.
1. Klik op het tabblad Beveiliging.
1. In de Vereisen Vraag om lijst voor authentiek te verklaren, selecteer of ja of Nr om te specificeren of de dienst met of zonder geloofsbrieven kan worden aangehaald.

   Als u ja selecteert, moet de bezoeker van de dienst voor authentiek worden verklaard en het gebruikershoofd voor die bezoeker moet worden gemachtigd om de dienst aan te halen; anders wordt de oproeping geweigerd .

   Als u Nr selecteert, kan de bezoeker van de dienst al dan niet voor authentiek worden verklaard. De aanroeping van de dienst zal altijd slagen omdat er geen vergunningscontrole is.

1. Voor de diensten die één of meerdere verrichtingen bevatten die voor anonieme toegang worden gemarkeerd, selecteer of schrap Anoniem Toegelaten Toegang. Wanneer de anonieme toegang wordt toegelaten, kan om het even welke gebruiker binnen het systeem verrichtingen op de dienst aanhalen. Als anonieme toegang gehandicapt is, moeten de gebruikers toestemming worden verleend om de dienst te roepen en verrichtingen aan te halen. Gebruikers krijgen deze machtigingen direct of als onderdeel van een groep met dergelijke machtigingen.
1. Voor sommige services beïnvloedt de gebruikersaccount die de bewerking uitvoert de resultaten. Bijvoorbeeld, in de (Vervangen) Diensten van de Inhoud, wordt de gebruiker die inhoud opslaat gemaakt tot eigenaar van de inhoud, die beïnvloedt wie tot de inhoud kan later toegang hebben. Als u een proces gebruikt om inhoud op te slaan, denk over welke gebruiker wordt gebruikt om de dienst van het Beheer van het Document uit te voeren, omdat die gebruiker de opgeslagen inhoud zal bezitten.

   Als u de runtime-identiteit wilt opgeven die door de service wordt gebruikt om bewerkingen uit te voeren, selecteert u Uitvoeren als opgeven, selecteert u een optie in de bijbehorende lijst en klikt u op Opslaan. Kies een van de volgende opties:

   **Invoker:** Gebruikt de zelfde identiteit zoals de gebruiker die de dienst aanhaalde.

   **Systeem:** Gebruikt de gebruiker van het Systeem om de dienst met volledige voorrechten in werking te stellen.

   **Benoemde gebruiker:** Laat u toe om de dienst als specifieke gebruiker in werking te stellen. Wanneer u deze optie selecteert, klikt u op Gebruiker selecteren om de pagina Afzonderlijk kapitaal selecteren weer te geven, waar u naar de gebruiker kunt zoeken en deze kunt selecteren.

   Als u Uitvoeren als opgeven niet selecteert, wordt het standaardgedrag gebruikt.

   >[!NOTE]
   >
   >De diensten die met xfaForm, de Vorm van het Document, en de variabelen van de Vorm worden gebruikt worden teruggeven en voorleggen altijd uitgevoerd gebruikend de de gebruikersrekening van het Systeem.

1. Klik toevoegen Belangrijker om de toestemmingen te specificeren die de gebruikers en de groepen voor deze dienst hebben.
1. Het Uitgezochte Belangrijkste scherm toont de gebruikers en de groepen die in het Beheer van de Gebruiker worden gevormd. Als de gewenste gebruiker of groep niet wordt weergegeven, gebruikt u de zoekfunctie om deze te zoeken. Klik op de naam van een gebruiker of groep.
1. Voor het Add scherm van Toestemmingen, selecteer de toestemmingen om aan de gebruiker of de groep voor deze dienst toe te wijzen:

   * **INVOKE_PERM:** Om alle verrichtingen op de dienst aan te halen
   * **MODIFY_CONFIG_PERM:** Om de configuratie van de dienst te wijzigen
   * **SUPERVISOR_PERM:** Om de gegevens van de procesinstantie voor de dienst te bekijken die van een proces wordt gecreeerd
   * **START_STOP_PERM:** Om de dienst te beginnen en te stoppen
   * **ADD_REMOVE_ENDPOINTS_PERM:** Om, eindpunten voor de dienst toe te voegen te verwijderen en te wijzigen
   * **CREATE_VERSION_PERM:** Een nieuwe versie van de service maken
   * **DELETE_VERSION_PERM:** Een versie van de service verwijderen
   * **MODIFY_VERSION_PERM:** Om een versie van de dienst te wijzigen
   * **READ_PERM:** De service weergeven
   * **PROCESS_OWNER_PERM:** Voor gebruik in een toekomstige versie van AEM-formulieren. Gebruik deze machtiging niet.
   * **SERVICE_MANAGER_PERM:** Voor gebruik in een toekomstige versie van AEM-formulieren. Gebruik deze machtiging niet.
   * **SERVICE_AGENT_PERM:** Voor gebruik in een toekomstige versie van AEM-formulieren. Gebruik deze machtiging niet.

1. Klik op Toevoegen.

### De principal verwijderen uit een beveiligingsprofiel {#remove-the-principal-from-a-security-profile}

1. Voor de pagina van het Beheer van de Dienst, selecteer de dienst om te vormen.
1. Klik op het tabblad **Beveiliging** , selecteer het beveiligingsprofiel dat u wilt verwijderen en klik op **Verwijderen**.

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

   **Eén instantie voor alle aanvragen:** Een de dienstinstantie wordt gecreeerd en in het voorgeheugen ondergebracht wanneer het eerste verzoek in de container komt. Elk verzoek na dat verzoek gebruikt de zelfde de dienstinstantie om het verzoek te behandelen.

   **Nieuwe instantie voor elke aanvraag:** Voor elke ontvangen aanroep wordt een nieuwe service-instantie gemaakt.

1. Klik op Opslaan.

