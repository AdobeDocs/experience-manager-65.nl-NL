---
title: Rollen maken en configureren
description: Leer hoe te om gebruikers en groepen met rollen te associëren die reeds deel van het gegevensbestand van het Beheer van de Gebruiker uitmaken. U kunt ook rollen maken, bewerken en verwijderen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/setting_up_and_organizing_users
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: b447e545-f73e-4fde-a001-86e0e1cf4a12
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '2483'
ht-degree: 0%

---

# Rollen maken en configureren{#creating-and-configuring-roles}

Gebruikend de Web-pagina&#39;s van het Beheer van de Gebruiker, kunt u gebruikers en groepen met rollen associëren die reeds deel van het gegevensbestand van het Beheer van de Gebruiker uitmaken. U kunt ook rollen maken, bewerken en verwijderen.

Gebruikersbeheer heeft twee soorten rollen:

**Tabelrollen:** Dit type rol kan worden uitgegeven en worden geschrapt, en de roltoestemmingen kunnen van deze roltypes worden toegevoegd en worden geschrapt. Elke rol die u maakt, wordt beschouwd als een veranderlijke rol. U kunt gebruikers en groepen toevoegen of verwijderen die aan veranderlijke rollen worden toegewezen.

**Onveranderbare rollen:** De standaardrollen die met het Beheer van de Gebruiker inbegrepen zijn zijn onveranderlijke rollen. Deze rollen kunnen niet worden bewerkt of verwijderd. U kunt echter gebruikers en groepen toevoegen of verwijderen die aan onveranderlijke rollen zijn toegewezen.

Zowel veranderlijke als onveranderlijke rollen kunnen ook door de AEM vormen APIs worden gecreeerd.

## Standaardrollen {#default-roles}

De volgende standaardrollen zijn inbegrepen in het gegevensbestand van het Beheer van de Gebruiker.

**Gebruiker van beheerconsole:** Kan beheerconsole openen.

**Toepassingsbeheerder:** Kan alle Workbench-functies gebruiken. Kan de pagina&#39;s van Toepassingen en van de Diensten in beleidsconsole gebruiken om de eigenschappen van de de dienstruntime, eindpunten, en veiligheid te vormen.

**AEM beheerder van formulieren:** Kan alle taken voor alle geïnstalleerde diensten uitvoeren.

**Beveiligingsbeheerder:** Controleert de montages van het Beheer van de Gebruiker, en beheert gebruikers en groepen die met om het even welk domein van de Manager van de Gebruiker worden geassocieerd

**Gebruikers van services:** Kan elke service weergeven en aanroepen

**Super Administrator:** Heeft toegang tot alle administratieve functies in het systeem, met inbegrip van de diensten

**Betrouwbaarheidsbeheerder:** Kan de PKI-vertrouwensinstellingen en PKI-referenties beheren die worden beheerd via de pagina Betrouwbaarheidsopslagbeheer in de beheerconsole

### Aanvullende standaardrollen {#additional-default-roles}

De volgende aanvullende standaardrollen kunnen worden opgenomen, afhankelijk van de AEM formuliercomponenten die u hebt geïnstalleerd

**Gebruiker van toepassing voor uploaden van document:** Kan documenten uploaden met Flex Remoting.

**Forms-beheerder:** Kan instellingen van de Forms-pagina weergeven en wijzigen in de beheerconsole

**Inhoudsruimtebeheerder AEM formulieren:** Kan instellingen van de pagina Content Services (Afgekeurd) in de beheerconsole weergeven en wijzigen

**Formulieren AEM Inhoudsruimte gebruiker:** Kan zich aanmelden bij de pagina&#39;s van de inhoudsruimte (Afgekeurd)

**Documentum Connector Administrator:** Kan instellingen bekijken en wijzigen van de Connector voor EMC Documentum pagina in beheerconsole

**Bestandsnetwerkbeheerder AEM formulieren:** Kan instellingen van de Connector voor IBM FileNet-pagina weergeven en wijzigen in beheerconsole

**AEM IBM CM Connector Administrator:** Kan instellingen weergeven en wijzigen op de pagina Connector voor IBM Content Manager in de beheerconsole

**Beheerder Rights Management:** Voert alle taken uit die voor alle serverconfiguraties op de relevante pagina&#39;s van het Rights Management worden vereist

**Eindgebruiker Rights Management:** Eindgebruikerwebpagina&#39;s van Rights Managementen kunnen worden geopend

**Gebruiker uitnodigen Rights Management:** Kan gebruikers uitnodigen

**Uitgenodigde en lokale gebruikers beheren van Rights Management:** Kan taken uitvoeren die vereist zijn om alle uitgenodigde en lokale gebruikers op de relevante pagina&#39;s van het Rights Management te beheren

**Beheerder voor beleidsset voor Rights Management:** Voert alle taken uit die voor alle beleidsreeksen op de relevante pagina&#39;s van het Rights Management worden vereist

**Extra beheerder Rights Management:** Voert alle taken uit die van de pagina van het Rights Management worden vereist

**AEM werkruimtebeheerder:** Kan instellingen weergeven en wijzigen vanaf de pagina Werkruimte in de beheerconsole

***notitie **: De Flex-werkruimte is vervangen voor AEM formulierrelease.*

**Gebruiker werkruimte:** Kan zich aanmelden bij de Workspace-toepassing voor eindgebruikers

**Uitvoerbeheerder:** Kan instellingen weergeven en wijzigen via de uitvoerpagina in de beheerconsole

**PDFG-beheerder:** Kan instellingen van de pagina PDF Generator weergeven en wijzigen in de beheerconsole

**PDFG-gebruiker:** Kan toegang krijgen tot alle niet-beheerfuncties voor PDF Generator

**Acrobat Reader DC-extensies - webtoepassing:** Kan de webtoepassing voor Acrobat Reader DC-extensies gebruiken

>[!NOTE]
>
>Gebruikers met bepaalde beheerdersrechten hebben uit veiligheidsoverwegingen geen toegang tot de webpagina&#39;s van eindgebruikers in Workspace. Omdat deze pagina&#39;s buiten een firewall kunnen bestaan, zou het toestaan van beleid-vlakke taken een veiligheidsrisico kunnen vormen. Alleen gebruikers met de AEM Workspace Administrator of AEM formulierwerkruimte Gebruikersrechten hebben toegang tot de webpagina&#39;s van de eindgebruiker van de Workspace.

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

## Een rol bewerken {#edit-a-role}

1. Klik in de beheerconsole op Instellingen > Gebruikersbeheer > Rolbeheer en klik vervolgens op Rolnaam.

   Door gebrek, toont de pagina van het Beheer van de Rol alle rollen in het gegevensbestand van het Gebruikersbeheer. Als de lijst met rollen groot is, gebruikt u het zoekgebied boven aan de pagina om naar een specifieke rolnaam te zoeken.

1. Klik op de rol die u wilt bewerken, bewerk de algemene instellingen en klik op Opslaan.
1. Als u machtigingen voor rollen wilt bewerken, klikt u op het tabblad Machtigingen en voert u de volgende taken uit:

   * Als u nieuwe machtigingen wilt toevoegen, klikt u op Machtigingen zoeken, schakelt u de selectievakjes in waarin de machtigingen moeten worden toegevoegd, klikt u op OK en vervolgens op Opslaan.
   * Als u een machtiging wilt verwijderen uit de rol, schakelt u het selectievakje voor de machtiging in, klikt u op Verwijderen en vervolgens op Opslaan.

1. Als u wilt bepalen aan wie de rol is toegewezen, klikt u op het tabblad Rolgebruikers en voert u de volgende taken uit:

   * Als u de rol aan nieuwe gebruikers en groepen wilt toewijzen, klikt u op Gebruikers/groepen zoeken en vult u de zoekinformatie in. Schakel het selectievakje in voor elke gebruiker en groep waaraan u deze rol wilt toewijzen, en klik op OK. Klik vervolgens op Opslaan.
   * Als u de rol wilt verwijderen, schakelt u het selectievakje voor de gebruikers of groep in, klikt u op Toewijzing ongedaan maken en vervolgens op Opslaan.

## Een rol verwijderen {#delete-a-role}

U kunt alle rollen verwijderen die u hebt gemaakt, maar niet de standaardrollen AEM formulieren die in het product zijn opgenomen.

1. Klik in de beheerconsole op Instellingen > Gebruikersbeheer > Rolbeheer en klik vervolgens op Rolnaam.

   Door gebrek, toont de pagina van het Beheer van de Rol alle rollen in het gegevensbestand van het Gebruikersbeheer. Als de lijst met rollen groot is, gebruikt u het zoekgebied boven aan de pagina om naar een specifieke rolnaam te zoeken.

1. Schakel het selectievakje voor de rol die u wilt verwijderen in, klik op Verwijderen en klik op OK.

## Een rol toewijzen aan gebruikers en groepen {#assign-a-role-to-users-and-groups}

1. Klik in de beheerconsole op Instellingen > Gebruikersbeheer > Gebruikers en groepen.
1. Geef informatie op om de zoekopdracht te verfijnen en klik op Zoeken. De resultaten van de zoekopdracht worden onder aan de pagina weergegeven. U kunt de lijst sorteren door op een van de kolomkoppen te klikken.
1. Schakel de selectievakjes naast de gebruikers en groepen in die u aan een rol wilt koppelen en klik op Rol toewijzen.
1. Selecteer de rol die u aan de gebruiker of groep wilt toewijzen en klik op OK.

U kunt rollen ook toewijzen door de pagina Rolbeheer te gebruiken.

## Bepaal wie aan een rol wordt toegewezen {#determine-who-is-assigned-to-a-role}

1. Klik in de beheerconsole op Instellingen > Gebruikersbeheer > Rolbeheer en klik vervolgens op Rolnaam.

   Door gebrek, toont de pagina van het Beheer van de Rol alle rollen in het gegevensbestand van het Gebruikersbeheer. Als de lijst met rollen groot is, gebruikt u het zoekgebied boven aan de pagina om naar een specifieke rolnaam te zoeken.

1. Klik op het tabblad Rolgebruikers op de pagina Roldetails. Er wordt een lijst weergegeven met gebruikers en groepen die rechtstreeks aan de rol zijn gekoppeld.

## Rolmachtigingen wijzigen {#change-role-permissions}

U kunt de toestemmingen voor om het even welke rollen veranderen die u creeerde. U kunt de machtigingen voor de standaardrollen AEM formulieren die in het product zijn opgenomen, niet wijzigen.

1. Klik in de beheerconsole op Instellingen > Gebruikersbeheer > Rolbeheer en klik vervolgens op Rolnaam.

   Door gebrek, toont de pagina van het Beheer van de Rol alle rollen in het gegevensbestand van het Gebruikersbeheer. Als de lijst met rollen groot is, gebruikt u het zoekgebied boven aan de pagina om naar een specifieke rolnaam te zoeken.

1. Selecteer de rol om toestemmingen voor te bekijken en de Toestemmingen te klikken tabel.
1. Als u deze machtigingen wilt wijzigen, klikt u op Machtigingen zoeken, schakelt u de selectievakjes in voor de machtigingen die u aan de rol wilt toevoegen, klikt u op OK en vervolgens op Opslaan.
1. Als u een machtiging wilt verwijderen, selecteert u de machtiging, klikt u op Verwijderen en vervolgens op Opslaan.

### Formuliermachtigingen AEM {#aem-forms-permissions}

**ADD_REMOVE_ENDPOINT_PERM:** Voeg, verwijder en wijzig eindpunten voor de dienst toe

**Aanmelden bij Admin Console:** De beheerconsole weergeven

**Certificaat wijzigen:** De instellingen voor vertrouwen van certificaten in het vertrouwde archief wijzigen

**Leescertificaat:** Elk certificaat lezen in de Trust Store

**Schrijven certificaat:** Een certificaat toevoegen aan de Trust Store

**Component toevoegen:** Een nieuwe component in het systeem installeren

**Verwijderen van component:** Een component in het systeem verwijderen

**Component gelezen:** Een component in het systeem lezen

**Inhoudsruimtebeheerder:** Machtiging voor beheerder inhoudruimte (afgekeurd)

**Aanmelden bij inhoudsruimteconsole:** Machtiging voor aanmelding van inhoudsruimte (afgekeurd) console

**Core Settings Control:** De instellingen op de pagina Core System Settings in de beheerconsole beheren

**CREATE_VERSION_PERM:** Een versie van een service maken

**Credentials wijzigen:** Ondertekeningsreferentie wijzigen in de Trust Store

**Gelezen referentie:** Alle ondertekeningsreferenties lezen in de Trust Store

**Credentijd:** Een ondertekeningsreferentie toevoegen aan de Trust Store

**CRL wijzigen:** CRL (Certificate Revocation List) wijzigen in het Trust Store

**CRL-lezen:** Een CRL lezen in de Trust Store

**Schrijven van CRL:** Een CRL toevoegen aan de Trust Store

**Delegeren:** Plaats ACL op een middel

**DELETE_VERSION_PERM:** Een versie van een service verwijderen

**Document uploaden:** Documenten uploaden in AEM formulieren

**Domeinbesturing:** Instellingen maken, verwijderen of wijzigen voor elk gebruikersbeheerdomein, inclusief verificatie- en directoryproviders

**Type gebeurtenis bewerken:** Bewerken naar gebeurtenistypen

**Naamimitatiebeheer:** Identiteit imiteren in Gebruikersbeheer

**INVOKE_PERM:** Alle bewerkingen op een service aanroepen

**Besturing LCDS-gegevensmodel:** Lees en stel gegevensmodellen in de Diensten van Gegevens op

**Update voor licentiebeheer:** Licentiegegevens bijwerken

**MODIFY_CONFIG_PERM:** De configuratie van een service wijzigen

**TERM** De versie van een service wijzigen

**PDFGAdminPermission:** PDFG-beheerder

**PDFGUserPermission:** PDFG-gebruiker

**PERM_DCTM_ADMIN:** Documentum Connector-beheerder

**PERM_FILENET_ADMIN:** Bestuurder FileNet-connector

**PERM_FORMS_ADMIN:** Forms-beheerder

**PERM_IBMCM_ADMIN:** IBM CM Connector-beheerder

**PERM_OUTPUT_ADMIN:** Uitvoerbeheerder

**PERM_READER_EXTENSIONS_WEB_APPLICATION:** De webtoepassing Acrobat Reader DC-extensies gebruiken

**PERM_SP_ADMIN:** SharePoint-verbindingsinstellingen beheren

**PERM_WORKSPACE_ADMIN:** Werkruimte-instellingen beheren

**PERM_WORKSPACE_USER:** Aanmelden bij de toepassing voor eindgebruikers van Workspace

**Hoofdcontrole:** Gebruikers en groepen beheren voor elk domein en roltoewijzingen beheren voor alle gebruikers en groepen in elk domein

**Opname lezen/verwijderen verwerken:** Workflowauditinstanties weergeven en ophalen

**PROCESS_OWNER_PERM:** De trendgegevens van de mening en voert administratieve acties op de dienst uit die van een proces wordt gecreeerd

**Lezen:** De inhoud van een bron lezen

**READ_PERM:** Een service lezen of weergeven

**Verlenging van bewering:** Berichten in Gebruikersbeheer vernieuwen

**Delegatie opslagplaats:** Plaats ACL op een middel

**Leesruimte opslagplaats:** De inhoud van een bron lezen

**Repository traverse:** Neem een bron op in een verzoek om lijstbronnen of lees de metagegevens van een bron

**Schrijven naar opslagplaats:** Metagegevens en inhoud van opslagplaatsen schrijven

**Eigenaar wijzigingsbeleid Rights Management:** Beleidseigenaar wijzigen

**Aanmelden bij Eindgebruikersconsole van Rights Management:** Aanmelden bij de gebruikersinterface van de eindgebruiker van het Rights Management

**Configuratie Rights Management beheren:** Serverconfiguratie beheren

**Uitgenodigde en lokale gebruikers beheren van Rights Management:** Uitgenodigde en lokale gebruikers beheren

**Rights Management beheert beleidssets:** Alle beleid en documenten binnen een willekeurige beleidsset beheren

**Beleidsset Rights Management coördinator toevoegen:** Machtigingen voor beleidssetcoördinatoren toevoegen, verwijderen en wijzigen

**Beleid instellen voor maken van Rights Management:** Een beleid maken voor een beleidsset

**Beleid voor Rights Managementen instellen Verwijderbeleid:** Een beleid verwijderen uit een beleidsset

**Beleid voor bewerken van Rights Management instellen:** Een beleid in een beleidsset bewerken

**Beleidsset Rights Management > Documentuitgever beheren:** Wanneer u beleidssets maakt, wijst u gebruikers de rol van documentuitgever toe. De uitgever van het document is de gebruiker die het document met een beleid beschermt.

**Beleidsset Rights Management verwijderen coördinator:** Een beleidssetcoördinator verwijderen uit een beleidsset

**Document intrekken door beleidsset Rights Management:** Toegang tot documenten in een beleidsset intrekken

**Beleid van de Vastgestelde Schakelaar van het Rights Management:** Van beleid wisselen voor een document

**Document intrekken ongedaan maken beleidsset Rights Management:** Een document intrekken

**Weergavegebeurtenis voor Beleidsset Rights Management:** Beleid en documentgebeurtenissen weergeven voor beleid of document binnen een beleidsset

**Gebeurtenissen weergaveserver Rights Management:** Alle auditgebeurtenissen zoeken en weergeven

**Rolbesturing:** Rollen maken, verwijderen en wijzigen in Gebruikersbeheer

**Service activeren:** De dienst van begin om het even welke dienst, die het voor oproeping ter beschikking stelt

**Service toevoegen:** Stel een nieuwe dienst aan de de dienstregistratie op. Dit omvat het toevoegen van nieuwe processen en procesvarianten

**Service uitgeschakeld:** De dienst in het systeem tegenhouden

**Service verwijderen:** Alle services in het systeem verwijderen, inclusief processen en procesvarianten

**Service aanroepen:** Alle services in het serviceregister die beschikbaar zijn bij uitvoering aanroepen

**Service wijzigen:** Wijzig de configuratieeigenschappen van om het even welke dienst in het systeem. Dit omvat het sluiten van en het ontgrendelen van de dienst in winde, en het toevoegen van of het verwijderen van eindpunten uit de dienst

**Service-lezen:** Lees om het even welke diensten in het systeem. Dit omvat alle processen en procesvarianten

**SERVICE_AGENT_PERM:** Gegevens bekijken en met procesinstanties voor de dienst in wisselwerking staan die van een proces wordt gecreeerd

**SERVICE_MANAGER_PERM:** Het in evenwicht brengen van lading en andere administratieve acties op de dienst uitvoeren die van een proces wordt gecreeerd

**START_STOP_PERM:** Een service starten of stoppen

**SUPERVISOR_PERM:** De gegevens van de procesinstantie van de mening voor de dienst die van een proces wordt gecreeerd

**Gekanteld:** Neem een bron op in een verzoek om lijstbronnen of lees de metagegevens van een bron

**Schrijven:** Metagegevens en inhoud van opslagplaatsen schrijven

**Bestanden openen in Workbench**

Om de inhoud van de mening van Middelen in Workbench en open dossiers voor het bekijken te bekijken, vereist een gebruiker de volgende toestemmingen:

* Lezen opslagplaats
* Repository Traverse
* Service aanroepen
* Service Read

## Een gebruiker of groep uit een rol verwijderen {#remove-a-user-or-group-from-a-role}

Gebruik de pagina Rolbeheer om gebruikers en groepen uit een bepaalde rol te verwijderen. Als de gebruiker of de groep de roltaak heeft overgeërfd, kunt u de rol op gebruiker of groepsniveau niet verwijderen. Verwijder de gebruiker of groep uit de overervingstructuur of verwijder de rol uit het bovenliggende element.

1. Klik in de beheerconsole op Instellingen > Gebruikersbeheer > Rolbeheer en klik vervolgens op Rolnaam.

   Door gebrek, toont de pagina van het Beheer van de Rol alle rollen in het gegevensbestand van het Gebruikersbeheer. Als de lijst met rollen groot is, gebruikt u het zoekgebied boven aan de pagina om naar een specifieke rolnaam te zoeken.

1. Klik in de lijst met rollen op de naam van de rol die u wilt bijwerken en klik vervolgens op het tabblad Rolgebruikers. Er wordt een lijst weergegeven met gebruikers en groepen die aan de rol zijn gekoppeld.
1. Schakel de selectievakjes in voor de gebruikers en groepen die u uit de rol wilt verwijderen en klik op Toewijzen ongedaan maken.
1. Klik op Opslaan en vervolgens op OK.
