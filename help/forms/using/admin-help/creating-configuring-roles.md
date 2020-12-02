---
title: Rollen maken en configureren
seo-title: Rollen maken en configureren
description: Leer hoe te om gebruikers en groepen met rollen te associëren die reeds deel van het gegevensbestand van het Beheer van de Gebruiker uitmaken. U kunt ook rollen maken, bewerken en verwijderen.
seo-description: Leer hoe te om gebruikers en groepen met rollen te associëren die reeds deel van het gegevensbestand van het Beheer van de Gebruiker uitmaken. U kunt ook rollen maken, bewerken en verwijderen.
uuid: e8e4331d-48e1-4fa9-8f44-f885f4ab1a54
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/setting_up_and_organizing_users
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 737fb4d1-adef-47e1-9a0d-8cddd13132cb
translation-type: tm+mt
source-git-commit: 413af4ef9bc3652e05da78d622183bcf20a8bee7
workflow-type: tm+mt
source-wordcount: '2556'
ht-degree: 0%

---


# Rollen maken en configureren{#creating-and-configuring-roles}

Gebruikend de Web-pagina&#39;s van het Beheer van de Gebruiker, kunt u gebruikers en groepen met rollen associëren die reeds deel van het gegevensbestand van het Beheer van de Gebruiker uitmaken. U kunt ook rollen maken, bewerken en verwijderen.

Gebruikersbeheer heeft twee soorten rollen:

**Meerdere rollen:** Dit type rol kan worden bewerkt en verwijderd en rolinstellingen kunnen worden toegevoegd en verwijderd uit deze rolindelingen. Elke rol die u maakt, wordt beschouwd als een veranderlijke rol. U kunt gebruikers en groepen toevoegen of verwijderen die aan veranderlijke rollen worden toegewezen.

**Onveranderbare rollen:** De standaardrollen die met het Beheer van de Gebruiker inbegrepen zijn zijn onveranderlijke rollen. Deze rollen kunnen niet worden bewerkt of verwijderd. U kunt echter gebruikers en groepen toevoegen of verwijderen die aan onveranderlijke rollen zijn toegewezen.

Zowel veranderlijke als onveranderlijke rollen kunnen ook door de AEM vormen APIs worden gecreeerd.

## Standaardrollen {#default-roles}

De volgende standaardrollen zijn inbegrepen in het gegevensbestand van het Beheer van de Gebruiker.

**Beheerconsole Gebruiker:** kan toegang krijgen tot beheerconsole.

**Toepassingsbeheerder:** kan alle Workbench-functies gebruiken. Kan de pagina&#39;s van Toepassingen en van de Diensten in beleidsconsole gebruiken om de eigenschappen van de de dienstruntime, eindpunten, en veiligheid te vormen.

**AEM formulierbeheerder:** kan alle taken uitvoeren voor alle geïnstalleerde services.

**Beveiligingsbeheerder:** beheert de instellingen voor gebruikersbeheer en beheert gebruikers en groepen die zijn gekoppeld aan een gebruikersbeheerdomein

**Gebruikers van services:** kan elke service weergeven en aanroepen

**Superbeheerder:** heeft toegang tot alle administratieve functionaliteit in het systeem, met inbegrip van de diensten

**Betrouwbaarheidsbeheerder:** Kan de PKI-vertrouwensinstellingen en PKI-referenties beheren die worden beheerd via de pagina Betrouwbaarheidsopslagbeheer in de beheerconsole

### Aanvullende standaardrollen {#additional-default-roles}

De volgende aanvullende standaardrollen kunnen worden opgenomen, afhankelijk van de AEM formuliercomponenten die u hebt geïnstalleerd

**Toepassingsgebruiker voor uploaden van document:** kan documenten uploaden met Flex Remoting.

**Forms Administrator:** Kan instellingen weergeven en wijzigen op de Forms-pagina in de beheerconsole

**AEM formulieren Inhoudsruimtebeheerder:** Kan instellingen van de pagina Content Services (Afgekeurd) weergeven en wijzigen in beheerconsole

**Formulieren AEM Inhoudsruimte gebruiker:** kan zich aanmelden bij de pagina&#39;s in de inhoudsruimte (afgekeurd)

**Documentum Connector Administrator:** Kan instellingen bekijken en wijzigen van de Connector voor EMC Documentum pagina in beheerconsole

**AEM formulier FileNet Connector Administrator:** Kan instellingen van de Connector voor IBM FileNet-pagina weergeven en wijzigen in beheerconsole

**AEM formulieren IBM CM Connector Administrator:** Kan instellingen bekijken en wijzigen via de pagina Connector voor IBM Content Manager op de beheerconsole

**Beheerder van Rights Management:** voert alle taken uit die voor alle serverconfiguraties op de relevante pagina&#39;s van het Rights Management worden vereist

**Eindgebruiker van Rights Management:** Kan toegang krijgen tot eindgebruikerwebpagina&#39;s van Rights Management

**Rights Management uitnodigen gebruiker:** kan gebruikers uitnodigen

**Rights Management Uitgenodigde en lokale gebruikers beheren:** kan taken uitvoeren die vereist zijn om alle uitgenodigde en lokale gebruikers op de desbetreffende pagina&#39;s van het Rights Management te beheren

**Beheerder voor beleidsset voor Rights Management:** voert alle taken uit die vereist zijn voor alle beleidssets op de relevante pagina&#39;s van het Rights Management

**Rights Management Super Administrator:** voert alle taken uit die van de pagina van het Rights Management worden vereist

**AEM formulieren, werkruimtebeheerder:** kan instellingen weergeven en wijzigen op de pagina Werkruimte in beheerconsole

***opmerking **: De Flex-werkruimte is verouderd voor AEM formulierrelease.*

**Gebruiker van werkruimte:** kan zich aanmelden bij de toepassing voor eindgebruikers van Workspace

**Uitvoerbeheerder:instellingen** kunnen weergeven en wijzigen op de uitvoerpagina in de beheerconsole

**PDFG-beheerder:instellingen** kunnen worden weergegeven en gewijzigd op de pagina PDF Generator in de beheerconsole

**PDFG-gebruiker:** heeft toegang tot alle niet-beheerfuncties voor PDF Generator

**Acrobat Reader DC-extensies, webtoepassing:** kan de webtoepassing voor Acrobat Reader DC-extensies gebruiken

>[!NOTE]
>
>Gebruikers met bepaalde beheerdersrechten hebben uit veiligheidsoverwegingen geen toegang tot de webpagina&#39;s van eindgebruikers in Workspace. Omdat deze pagina&#39;s buiten een firewall kunnen bestaan, zou het toestaan van beleid-vlakke taken een veiligheidsrisico kunnen vormen. Alleen gebruikers met de AEM Workspace Administrator of AEM formulierwerkruimte Gebruikersrechten hebben toegang tot de eindgebruikerwebpagina&#39;s van de Workspace.

>[!NOTE]
>
>De Flex-werkruimte is verouderd voor AEM formulierrelease.

## Een rol maken {#create-a-role}

1. Klik in de beheerconsole op Instellingen > Gebruikersbeheer > Rolbeheer en klik vervolgens op Nieuwe rol.
1. Typ in het vak Rolnaam een naam voor de rol en typ desgewenst een beschrijving van de rol en klik op Volgende.

   >[!NOTE]
   >
   >Wanneer u MySQL gebruikt, kunt u geen twee rollen maken die dezelfde naam hebben maar verschillen in het gebruik van uitgebreide tekens. Als u bijvoorbeeld probeert een rol met de naam abcde te maken terwijl de naam âbcdè al bestaat, treedt er een fout op.

1. Klik op Machtigingen zoeken en selecteer de machtigingen die u aan de rol wilt toevoegen.
1. Klik op OK en vervolgens op Volgende.
1. Deze rol toewijzen aan gebruikers en groepen:

   * Klik op Gebruikers/groepen zoeken.
   * Typ uw zoekcriteria in het vak Zoeken.
   * Selecteer Naam, E-mail of Gebruikersnaam en selecteer Gebruikers, Groepen of Gebruikers en Groepen.
   * Selecteer het domein, selecteer het aantal resultaten dat u wilt weergeven en klik op Zoeken.
   * Schakel de selectievakjes in voor de gebruikers en groepen waaraan u deze rol wilt toewijzen en klik op OK.

1. Als u gebruikers- en groepsgegevens wilt weergeven, selecteert u de entiteit.
1. Klik op OK en vervolgens op Voltooien.

## Rollen {#edit-a-role} bewerken

1. Klik in de beheerconsole op Instellingen > Gebruikersbeheer > Rolbeheer en klik vervolgens op Rolnaam.

   Door gebrek, toont de pagina van het Beheer van de Rol alle rollen in het gegevensbestand van het Beheer van de Gebruiker. Als de lijst met rollen groot is, gebruikt u het zoekgebied boven aan de pagina om naar een specifieke rolnaam te zoeken.

1. Klik op de rol die u wilt bewerken, bewerk de algemene instellingen en klik op Opslaan.
1. Als u machtigingen voor rollen wilt bewerken, klikt u op het tabblad Machtigingen en voert u de volgende taken uit:

   * Als u nieuwe machtigingen wilt toevoegen, klikt u op Machtigingen zoeken, schakelt u de selectievakjes in waarin de machtigingen moeten worden toegevoegd, klikt u op OK en vervolgens op Opslaan.
   * Als u een machtiging wilt verwijderen uit de rol, schakelt u het selectievakje voor de machtiging in, klikt u op Verwijderen en vervolgens op Opslaan.

1. Als u wilt bepalen aan wie de rol is toegewezen, klikt u op het tabblad Rolgebruikers en voert u de volgende taken uit:

   * Als u de rol aan nieuwe gebruikers en groepen wilt toewijzen, klikt u op Gebruikers/groepen zoeken en vult u de zoekinformatie in. Schakel het selectievakje in voor elke gebruiker en groep waaraan u deze rol wilt toewijzen, en klik op OK. Klik vervolgens op Opslaan.
   * Als u de rol wilt verwijderen, schakelt u het selectievakje voor de gebruikers of groep in, klikt u op Toewijzing ongedaan maken en vervolgens op Opslaan.

## Een rol {#delete-a-role} verwijderen

U kunt alle rollen verwijderen die u hebt gemaakt, maar niet de standaardrollen AEM formulieren die in het product zijn opgenomen.

1. Klik in de beheerconsole op Instellingen > Gebruikersbeheer > Rolbeheer en klik vervolgens op Rolnaam.

   Door gebrek, toont de pagina van het Beheer van de Rol alle rollen in het gegevensbestand van het Beheer van de Gebruiker. Als de lijst met rollen groot is, gebruikt u het zoekgebied boven aan de pagina om naar een specifieke rolnaam te zoeken.

1. Schakel het selectievakje voor de rol die u wilt verwijderen in, klik op Verwijderen en klik op OK.

## Een rol toewijzen aan gebruikers en groepen {#assign-a-role-to-users-and-groups}

1. Klik in de beheerconsole op Instellingen > Gebruikersbeheer > Gebruikers en groepen.
1. Geef informatie op om de zoekopdracht te verfijnen en klik op Zoeken. De resultaten van de zoekopdracht worden onder aan de pagina weergegeven. U kunt de lijst sorteren door op een van de kolomkoppen te klikken.
1. Schakel de selectievakjes naast de gebruikers en groepen in die u aan een rol wilt koppelen en klik op Rol toewijzen.
1. Selecteer de rol die u aan de gebruiker of groep wilt toewijzen en klik op OK.

U kunt rollen ook toewijzen door de pagina Rolbeheer te gebruiken.

## Bepaal wie aan een rol {#determine-who-is-assigned-to-a-role} wordt toegewezen

1. Klik in de beheerconsole op Instellingen > Gebruikersbeheer > Rolbeheer en klik vervolgens op Rolnaam.

   Door gebrek, toont de pagina van het Beheer van de Rol alle rollen in het gegevensbestand van het Beheer van de Gebruiker. Als de lijst met rollen groot is, gebruikt u het zoekgebied boven aan de pagina om naar een specifieke rolnaam te zoeken.

1. Klik op het tabblad Rolgebruikers op de pagina Roldetails. Er wordt een lijst weergegeven met gebruikers en groepen die rechtstreeks aan de rol zijn gekoppeld.

## Rolmachtigingen wijzigen {#change-role-permissions}

U kunt de toestemmingen voor om het even welke rollen veranderen die u creeerde. U kunt de machtigingen voor de standaardrollen AEM formulieren die in het product zijn opgenomen, niet wijzigen.

1. Klik in de beheerconsole op Instellingen > Gebruikersbeheer > Rolbeheer en klik vervolgens op Rolnaam.

   Door gebrek, toont de pagina van het Beheer van de Rol alle rollen in het gegevensbestand van het Beheer van de Gebruiker. Als de lijst met rollen groot is, gebruikt u het zoekgebied boven aan de pagina om naar een specifieke rolnaam te zoeken.

1. Selecteer de rol om toestemmingen voor te bekijken en de Toestemmingen te klikken tabel.
1. Als u deze machtigingen wilt wijzigen, klikt u op Machtigingen zoeken, schakelt u de selectievakjes in voor de machtigingen die u aan de rol wilt toevoegen, klikt u op OK en vervolgens op Opslaan.
1. Als u een machtiging wilt verwijderen, selecteert u de machtiging, klikt u op Verwijderen en vervolgens op Opslaan.

### Formuliermachtigingen {#aem-forms-permissions} AEM

**ADD_REMOVE_ENDPOINT_PERM:** Voeg, verwijder en wijzig eindpunten voor de dienst toe

**Aanmelden bij Admin Console:de beheerconsole** weergeven

**Certificaat wijzigen:de vertrouwensinstellingen van een certificaat** wijzigen in het Betrouwbaarheidsarchief

**Certificaat gelezen:certificaten** lezen in het Betrouwbaarheidsarchief

**Certificaat schrijven:certificaat** toevoegen aan vertrouwde opslag

**Component toevoegen:** Installeer een nieuwe component in het systeem

**Component verwijderen:component in systeem** verwijderen

**Component Read:** Lees om het even welke component in het systeem

**Inhoudsruimtebeheerder:** Machtiging voor (afgekeurde) inhoudsbeheerder

**Aanmelden bij inhoudsruimteconsole:Aanmelding** voor inhoudsruimte (afgekeurd) console

**Core Settings Control:** Manage the settings on the Core System Settings page in Administration Console

**CREATE_VERSION_PERM:** Een nieuwe versie van een service maken

**Credentials wijzigen:** ondertekeningsreferenties wijzigen in Vertrouwensarchief

**Credentials gelezen:eventuele ondertekeningsreferenties** lezen in de Trust Store

**Credentijd:** Voeg een ondertekeningsreferentie toe aan de Trust Store

**CRL wijzigen:CRL (Certificate Revocation List) in de Trust Store** wijzigen

**CRL-lezen:CRL&#39;s in de vertrouwde opslag** lezen

**CRL schrijven:CRL** toevoegen aan vertrouwde opslag

**Delegeren:ACL op een middel** instellen

**DELETE_VERSION_PERM:een versie van een service** verwijderen

**Document uploaden:documenten** uploaden in AEM

**Domeincontrole:instellingen** maken, verwijderen of wijzigen voor een willekeurig gebruikersbeheerdomein, inclusief verificatie- en directoryproviders

**Gebeurtenistype bewerken:** Bewerken naar gebeurtenistypen

**identiteitscontrole:identiteit** imiteren in gebruikersbeheer

**INVOKE_PERM:** Alle bewerkingen op een service aanroepen

**LCDS-gegevensmodelbesturing:gegevensmodellen** lezen en implementeren in Data Services

**Licentiebeheer bijwerken:licentiegegevens** bijwerken

**MODIFY_CONFIG_PERM:De configuratie van een service** wijzigen

**** TERMModify de versie van de dienst

**PDFGAdminPermission:** PDFG-beheerder

**PDFGUserPermission:** PDFG-gebruiker

**PERM_DCTM_ADMIN:** Documentum Connector-beheerder

**PERM_FILENET_ADMIN:** Besturingselement voor FileNet-aansluiting

**PERM_FORMS_ADMIN:** Forms-beheerder

**PERM_IBMCM_ADMIN:** IBM CM-connectorbeheerder

**PERM_OUTPUT_ADMIN:** Uitvoerbeheerder

**PERM_READER_EXTENSIONS_WEB_APPLICATION:** De webtoepassing voor Acrobat Reader DC-extensies gebruiken

**PERM_SP_ADMIN:SharePoint-verbindingsinstellingen** beheren

**PERM_WORKSPACE_ADMIN:Werkruimte-instellingen** beheren

**PERM_WORKSPACE_USER:** Meld u aan bij de eindgebruikerstoepassing van de Werkruimte

**Hoofdcontrole:gebruikers en groepen voor om het even welk domein** beheren, en roltaken voor alle gebruikers en groepen in om het even welk domein beheren

**Opname verwerken, lezen/verwijderen:** workflowauditinstanties weergeven en ophalen

**PROCESS_OWNER_PERM:De tendensen van de** mening gegevens en voeren administratieve acties op de dienst uit die van een proces wordt gecreeerd

**Lezen:De inhoud van een bron** lezen

**READ_PERM:een service** lezen of weergeven

**Verlenging, bevestiging:** Verlenging, beweringen in Gebruikersbeheer

**Delegatie opslagplaats:ACL op een bron** instellen

**Bewaarplaats gelezen:de inhoud van een bron** lezen

**Repository traverse:bron** opnemen in verzoek om lijstbronnen of de metagegevens van een bron lezen

**Schrijven in opslagplaats:metagegevens en inhoud van opslagplaats** schrijven

**Eigenaar wijzigingsbeleid Rights Management:** beleidseigenaar wijzigen

**Aanmelden bij Eindgebruikersconsole van Rights Management:** aanmelden bij eindgebruikersinterface van Rights Management

**Rights Management beheren configuratie:serverconfiguratie** beheren

**Rights Management Uitgenodigde en lokale gebruikers beheren:uitgenodigde en lokale gebruikers** beheren

**Rights Management beheert beleidssets:alle beleid en documenten** beheren binnen elke willekeurige beleidsset

**Rights Management beleidsset coördinator toevoegen:machtigingen voor beleidssetcoördinatoren** toevoegen, verwijderen en wijzigen

**Beleid instellen voor Rights Managementen: beleid maken:een nieuw beleid** maken voor een beleidsset

**Beleid voor Rights Managementen instellen Beleid verwijderen:beleid** verwijderen uit een beleidsset

**Beleid voor Rights Managementen instellen Bewerkbeleid:beleid** bewerken in een beleidsset

**Met de Beleidsset Rights Managementen Document Publisher beheren:** wanneer u beleidssets maakt, wijst u gebruikers de rol van documentuitgever toe. De uitgever van het document is de gebruiker die het document met een beleid beschermt.

**Rights Management beleidsset verwijderen coördinator:** beleidssetcoördinator verwijderen uit een beleidsset

**Rights Management beleidsset document intrekken:toegang** tot documenten in een beleidsset intrekken

**Beleid van de Reeks van de Schakelaar van het Rights Management Beleid:** Van beleid schakelen voor een document

**Beleid voor Rights Managementen instellen Document intrekken ongedaan maken:** document intrekken

**Weergavegebeurtenis Beleidsset Rights Managementen:** Beleid en documentgebeurtenissen weergeven voor beleid of document binnen een beleidsset

**Gebeurtenissen van de Server van de Mening van het Rights Management:** Onderzoek en bekijk alle controlegebeurtenissen

**Rolbesturing:rollen** maken, verwijderen en wijzigen in Gebruikersbeheer

**Service activeren:service** starten, beschikbaar maken voor oproepen

**De dienst voegt toe:** stelt een nieuwe dienst aan het de dienstregister op. Dit omvat het toevoegen van nieuwe processen en procesvarianten

**Service deactiveren:service in systeem** stoppen

**Service verwijderen:alle services in het systeem** verwijderen, inclusief processen en procesvarianten

**Service aanroepen:elke service** aanroepen in het serviceregister die beschikbaar is bij uitvoering

**De dienst wijzigt:** wijzigt de configuratieeigenschappen van om het even welke dienst in het systeem. Dit omvat het sluiten van en het ontgrendelen van de dienst in winde, en het toevoegen van of het verwijderen van eindpunten uit de dienst

**Service gelezen:services in het systeem** lezen. Dit omvat alle processen en procesvarianten

**SERVICE_AGENT_PERM:Gegevens** bekijken en met procesinstanties voor de dienst interactie aangaan die van een proces wordt gecreeerd

**SERVICE_MANAGER_PERM:** taakverdeling en andere beheeracties uitvoeren op een service die is gemaakt op basis van een proces

**START_STOP_PERM:een service** starten of stoppen

**SUPERVISOR_PERM:** Gegevens van procesinstanties weergeven voor een service die is gemaakt op basis van een proces

**Omkeren:** Neem een bron op in een verzoek om lijstbronnen of lees de metagegevens van een bron

**Schrijven:metagegevens en inhoud van opslagplaats** schrijven

**Bestanden openen in Workbench**

Om de inhoud van de mening van Middelen in Workbench en open dossiers voor het bekijken te bekijken, vereist een gebruiker de volgende toestemmingen:

* Lezen opslagplaats
* Repository Traverse
* Service aanroepen
* Service Read

## Een gebruiker of groep verwijderen uit een rol {#remove-a-user-or-group-from-a-role}

Gebruik de pagina Rolbeheer om gebruikers en groepen uit een bepaalde rol te verwijderen. Als de gebruiker of de groep de roltaak heeft overgeërfd, kunt u de rol op gebruiker of groepsniveau niet verwijderen. Verwijder de gebruiker of groep uit de overervingstructuur of verwijder de rol uit het bovenliggende element.

1. Klik in de beheerconsole op Instellingen > Gebruikersbeheer > Rolbeheer en klik vervolgens op Rolnaam.

   Door gebrek, toont de pagina van het Beheer van de Rol alle rollen in het gegevensbestand van het Beheer van de Gebruiker. Als de lijst met rollen groot is, gebruikt u het zoekgebied boven aan de pagina om naar een specifieke rolnaam te zoeken.

1. Klik in de lijst met rollen op de naam van de rol die u wilt bijwerken en klik vervolgens op het tabblad Rolgebruikers. Er wordt een lijst weergegeven met gebruikers en groepen die aan de rol zijn gekoppeld.
1. Schakel de selectievakjes in voor de gebruikers en groepen die u uit de rol wilt verwijderen en klik op Toewijzen ongedaan maken.
1. Klik op Opslaan en vervolgens op OK.

