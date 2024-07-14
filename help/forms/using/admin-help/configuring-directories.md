---
title: Mappen configureren
description: Leer hoe u mappen toevoegt, bewerkt en verwijdert en gebruikersbeheer configureert om de weergave van virtuele lijsten te gebruiken.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/setting_up_and_managing_domains
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 30edcef2-e8fa-403a-9850-b8dfeeb9ac65
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: e821be5233fd5f6688507096790d219d25903892
workflow-type: tm+mt
source-wordcount: '3229'
ht-degree: 0%

---

# Mappen configureren {#configuring-directories}

Voor elk ondernemingsdomein u vormt, specificeer de folders die de authentificatieleverancier voor gebruikersinformatie vraagt. U kunt meerdere mappen voor een domein configureren.

## Mappen of aangepaste SPI&#39;s toevoegen {#adding-directories-or-custom-spis}

Voor elk ondernemingsdomein u vormt, specificeer de folders die de authentificatieleverancier voor gebruikersinformatie vraagt. U kunt een folder aan een bestaand ondernemingsdomein of aan een nieuw ondernemingsdomein toevoegen dat u toevoegt. U kunt meerdere mappen voor een domein configureren. U kunt een domein ook vormen om een interface van de douaneleverancier van de Dienst (SPI) voor synchronisatie te gebruiken.

### Een map toevoegen {#add-a-directory}

1. Klik in de beheerconsole op Instellingen > Gebruikersbeheer > Domeinbeheer.
1. Klik op Nieuw Enterprise-domein of selecteer een bestaand ondernemingsdomein.
1. Klik op Map toevoegen.
1. Typ in het vak Profielnaam een naam om deze map van elkaar te onderscheiden en klik op Volgende.
1. Configureer de instellingen van de directoryserver. (Zie [ montages van de Folder ](configuring-directories.md#directory-settings).)
1. Klik op Testen om te controleren of er verbinding kan worden gemaakt met de LDAP-server. Als de test ontbreekt, herzie de uitzondering in het het logboekdossier van de Server van de Toepassing om de worteloorzaak van de mislukking te bepalen. Klik op Sluiten en vervolgens op Volgende.
1. Selecteer Gebruikersinstellingen en configureer de instellingen naar wens. (Zie [ montages van de Folder ](configuring-directories.md#directory-settings).)
1. Om te verifiëren dat basis DN en andere gevormde attributen de correcte partij van gebruikers verzamelen, klik Test. LDAP probeert de eerste 200 records op te halen met behulp van de opgegeven instellingen (zoals de basis-DN, het zoekfilter en alle kenmerken).

   Als gebruikers worden geretourneerd, geven de resultaten de waarden weer die aan elk veld zijn toegewezen volgens de kenmerkset. Als de test mislukt vanwege een niet-bestaande servernaam, onjuiste autorisatiegegevens of onjuiste kenmerken, wordt het volgende foutbericht weergegeven: &quot;De opgegeven zoekcriteria hebben geen resultaat geretourneerd&quot;. Om de worteloorzaak van de mislukking te bepalen, herzie de uitzondering in het het logboekdossier van de Server van de Toepassing. Klik op Sluiten en vervolgens op Volgende.

1. Selecteer Groepsinstellingen en configureer de instellingen naar wens. (Zie [ montages van de Folder ](configuring-directories.md#directory-settings).)
1. Om te verifiëren dat basis DN en andere gevormde attributen de correcte partij van groepen verzamelen, klik Test. Als groepen worden geretourneerd, geven de resultaten de waarden weer die aan elk veld zijn toegewezen volgens de kenmerkset. Klik op Sluiten.

### Een aangepaste SPI toevoegen {#add-a-custom-spi}

Voor informatie over het creëren van een douaneSPI, zie &quot;het Ontwikkelen van SPIs voor AEM vormen&quot;in [ Programmering met AEM vormen ](https://www.adobe.com/go/learn_aemforms_programming_63). Start de server opnieuw om een nieuw geïmplementeerde aangepaste SPI beschikbaar te maken voor associatie met het domein.

1. Klik in de beheerconsole op Instellingen > Gebruikersbeheer > Domeinbeheer.
1. Klik op Nieuw Enterprise-domein of selecteer een bestaand ondernemingsdomein.
1. Klik op Map toevoegen.
1. Typ een naam in het vak Profielnaam, selecteer Aangepaste SPI-provider en klik op Volgende.
1. Selecteer een aangepaste gebruikersprovider in de lijst en klik op Volgende.
1. Selecteer een aangepaste groepsprovider in de lijst en klik op Voltooien.

## Een map bewerken {#edit-a-directory}

U kunt de details van een folder uitgeven die u eerder vormde.

1. Klik in de beheerconsole op Instellingen > Gebruikersbeheer > Domeinbeheer.
1. Klik op het juiste domein in de lijst en selecteer op de pagina die wordt weergegeven de juiste map in de lijst.
1. Configureer de directory-, gebruikers- en groepsinstellingen naar wens. (Zie [ montages van de Folder ](configuring-directories.md#directory-settings).)
1. Klik op OK.

## Een map verwijderen {#delete-a-directory}

Wanneer u domeinen synchroniseert nadat u een map hebt verwijderd, worden alle gebruikers en groepen in die map gemarkeerd als verouderd in de database. Zij zullen niet in om het even welk onderzoek van de Console van het Beleid zijn teruggekeerd.

>[!NOTE]
>
>Voor bedrijfsdomeinen is ten minste één verificatieprovider en directoryprovider vereist.

1. Klik in de beheerconsole op Instellingen > Gebruikersbeheer > Domeinbeheer.
1. Klik op het desbetreffende domein in de lijst.
1. Schakel het selectievakje voor de juiste map in en klik op Verwijderen.
1. Klik op OK op de bevestigingspagina die wordt weergegeven en klik nogmaals op OK.

## Directoryinstellingen {#directory-settings}

Wanneer u een map aan een domein toevoegt, geeft u de volgende directoryinstellingen op.

**Server:** (Verplicht) volledig - gekwalificeerde domeinnaam (FQDN) van de folderserver. Voor een computer die x heet in het netwerk adobe.com, is de FQDN bijvoorbeeld x.adobe.com. Een IP-adres kan worden gebruikt in plaats van de FQDN-servernaam.

**Haven:** (Verplicht) de haven die de folderserver gebruikt. Typisch 389, of 636 als het Veilige protocol van de Laag van Contactdozen (SSL) wordt gebruikt voor het verzenden van authentificatieinformatie over het netwerk.

**SSL:** (Verplicht) specificeert of de folderserver SSL gebruikt wanneer het verzenden van gegevens over het netwerk. De standaardwaarde is Nee. Als u Ja instelt, moet het bijbehorende LDAP-servercertificaat worden vertrouwd door de JRE (Java™ runtime environment) van de toepassingsserver.

**Bindend** (Verplicht) specificeert hoe te om tot de folder toegang te hebben.

**Anoniem:** Geen gebruikersnaam of wachtwoord wordt vereist. Een anonieme gebruiker kan slechts een beperkte hoeveelheid gegevens ophalen. Deze optie kan handig zijn voor de eerste test.

**Gebruiker:** de Authentificatie wordt vereist. Geef in het vak Naam de naam op van de gebruikersrecord die toegang kan krijgen tot de map. U kunt het beste de volledige DN (Distinguished Name) van de gebruikersaccount invoeren, zoals cn=Jane Doe, ou=user, dc=can, dc=com. Geef in het vak Wachtwoord het bijbehorende wachtwoord op. Deze instellingen zijn vereist wanneer u Gebruiker selecteert als de optie Binding.

**Naam:** Naam die kan worden gebruikt om met het gegevensbestand te verbinden LDAP wanneer de anonieme toegang niet wordt toegelaten. Geef voor Active Directory 2003 `[domain name]\[userid]` op. Voor Sun™ One, eDirectory of IBM Tivoli Directory Server geeft u de volledig gekwalificeerde naam van de gebruiker op, zoals uid=lcuser,ou=it,o=company.com.

**Wachtwoord:** Wachtwoord dat met de naam beantwoordt u specificeerde om met het gegevensbestand te verbinden LDAP wanneer de anonieme toegang niet wordt toegelaten.

**vult Pagina met:** wanneer geselecteerd, bevolkt attributen op de de montagespagina&#39;s van de Gebruiker en van de Groep met overeenkomstige standaardLDAP waarden.

**wint Basis DNs terug:** wint basis DNs terug en toont hen in de drop-down lijst. Deze instelling is handig wanneer u meerdere basis-DN&#39;s hebt en een waarde moet selecteren.

**laat verwijzing toe:** Dit het plaatsen is van toepassing wanneer uw organisatie veelvoudige Actieve die domeinen van de Folder in een hiërarchische structuur wordt georganiseerd gebruikt en u foldermontages voor slechts het ouderdomein hebt gespecificeerd. In deze situatie, wanneer u deze optie selecteert, kan het Beheer van de Gebruiker tot gebruiker en groepdetails van de kinddomeinen toegang hebben.

>[!NOTE]
>
>Klik op Testen om te controleren of er verbinding kan worden gemaakt met de LDAP-server. Om de worteloorzaak van om het even welke mislukkingen te bepalen, herzie de uitzondering in het het logboekdossier van de Server van de Toepassing.

### Gebruikersinstellingen {#user-settings}

**Unieke Herkenningsteken:** (Verplicht) een uniek en constant attribuut dat wordt gebruikt om gebruikers te identificeren. Gebruik een niet-DN-kenmerk als de unieke id omdat de DN van een gebruiker kan veranderen als deze naar een ander deel van de organisatie wordt verplaatst. Deze instelling is afhankelijk van de directoryserver. De waarde is objectGUID voor Actieve Folder 2003, nsuniqueID voor Sun™ One, en guid voor eDirectory.

>[!NOTE]
>
>Zorg ervoor dat u een attribuut ingaat dat gegarandeerd om in uw organisatie uniek is te zijn. Het invoeren van een onjuiste waarde kan ernstige systeemproblemen veroorzaken.

**Basis DN:** Reeks als uitgangspunt voor het synchroniseren van gebruikers en groepen van de hiërarchie LDAP. Het is best om een basis DN op het laagste niveau van de hiërarchie te specificeren die alle gebruikers en groepen omvat die voor de diensten moeten worden gesynchroniseerd.

Als u de Enable verwijzingsoptie in de montages van de Folder selecteerde, plaats de optie van basis DN aan het *dc* deel van DN. De verwijzing werkt alleen als het zoekbereik zowel bovenliggende als onderliggende domeinen bevat.

>[!NOTE]
>
>Neem de DN van de gebruiker niet op in deze instelling. Gebruik de instelling Zoekfilter om een bepaalde gebruiker te synchroniseren.

Hoewel Base-DN een verplichte instelling is in de beheerconsole, vereisen sommige directoryservers, zoals IBM Domino Enterprise Server, mogelijk een lege BaseDN. Als u een lege basis-DN wilt opgeven, exporteert u het bestand config.xml, bewerkt u de instelling in het bestand config.xml en importeert u deze vervolgens opnieuw. (Zie [ het Invoeren en het uitvoeren van het configuratiedossier ](/help/forms/using/admin-help/importing-exporting-configuration-file.md#importing-and-exporting-the-configuration-file).)

**de Filter van het Onderzoek:** (Verplicht) de onderzoeksfilter om het verslag te gebruiken te vinden dat met de gebruiker wordt geassocieerd. U kunt een zoekopdracht op één niveau of een zoekopdracht op subniveau uitvoeren. (Zie Syntaxis van de Filter van het Onderzoek of RFC 2254.) Aanvullende informatie voor het Microsoft AD-schema, zie Active Directory Schema.

**Beschrijving:** attribuut van het Schema voor de beschrijving van de gebruiker

**Volledige Naam:** (Verplicht) attribuut van het Schema voor de volledige naam van de gebruiker

**Login identiteitskaart:** (Verplicht) attribuut van het Schema voor login identiteitskaart van de gebruiker

**Achternaam:** (Verplicht) attribuut van het Schema voor achternaam van de gebruiker

**Gegeven Naam:** (Verplicht) attribuut van het Schema voor de voornaam van de gebruiker

**Initialen:** attribuut van het Schema voor de initialen van de gebruiker

**BedrijfsKalender:** laat u toe om een bedrijfskalender aan een gebruiker in kaart te brengen, die op de waarde voor dit het plaatsen (de sleutel van de bedrijfskalender) wordt gebaseerd. Zakelijke kalenders definiëren zakelijke en niet-zakelijke dagen. AEM formulieren kunnen zakelijke kalenders gebruiken voor het berekenen van toekomstige datums en tijden voor gebeurtenissen zoals herinneringen, deadlines en escalaties. De manier u zaken kalendersleutels aan gebruikers toewijst hangt af van of u een onderneming, lokaal, of hybride domein gebruikt. (Zie Business Calendars configureren.)

Als u een ondernemingsdomein gebruikt, kunt u het BedrijfsKalender plaatsen aan een gebied in de folder in kaart brengen LDAP. Bijvoorbeeld, als elk gebruikersverslag in uw folder het gebied van het a *land* bevat, en u zakelijke kalenders wilt toewijzen die op het land worden gebaseerd waar de gebruiker wordt gevestigd, specificeer de *3} gebiedsnaam van het land {als waarde voor het BedrijfsKalender plaatsen.* U kunt de sleutels van de bedrijfskalender (de waarden die voor het *worden bepaald land* gebied in de folder LDAP) aan bedrijfscalendars in vormenwerkschema dan in kaart brengen.

De hoeveelheid ruimte die wordt gebruikt voor het weergeven van de naam van de zakelijke kalendersleutel in de pagina&#39;s van de formulierwerkstroom is beperkt. Beperk de naam van de zakelijke kalendersleutel tot minder dan 53 tekens om te voorkomen dat deze op deze pagina&#39;s wordt afgekapt.

**wijzig Tijdstempel:** om de synchronisatie van de deltafolder toe te laten, plaats deze waarde om TimeStamp te wijzigen. (Zie Synchronisatie van delta-directory inschakelen.)

**Organisatie:** attribuut van het Schema voor de naam van de organisatie waartot de gebruiker behoort.

**Primaire E-mail:** attribuut van het Schema voor het primaire e-mailadres van de gebruiker.

**Secundaire E-mail:** attribuut van het Schema voor het secundaire e-mailadres van de gebruiker.

**Telefoon:** attribuut van het Schema voor het de telefoonaantal van de gebruiker.

**Adres van de Post:** attribuut van het Schema voor het postadres van de gebruiker.

**Scène:** attribuut van het Schema dat de de scèneinformatie van ISO bevat. De waarde bestaat uit een taalcode van twee letters of een taal- en landcode.

**Zone van de Tijd:** attribuut van het Schema dat de tijdzone bevat waar de gebruiker wordt gevestigd. De waarde bestaat uit een tekenreeks zoals Plaats/Land.

**laat Virtuele Controle van de Mening van de Lijst (VLV) toe:** Een controle LDAP die AEM vormen toelaat om gegevens in partijen van de folderserver terug te winnen. Als u Sun One gebruikt als uw LDAP-directory en de map veel gebruikers bevat, maakt u met VLV een index die door Gebruikersbeheer kan worden gebruikt bij het zoeken naar gebruikers. Deze functie is handig wanneer u een normale gebruikersaccount gebruikt die slechts een beperkte hoeveelheid gegevens kan synchroniseren. U kunt VLV voor groepen ook toelaten. Als u VLV-controle (Virtual List View) inschakelen selecteert, geeft u een naam op in het vak Sorteerveld.

>[!NOTE]
>
>Om VLV toe te laten, vorm Zon Één. Zie [ Gebruikersbeheer vormen om de Virtuele Mening van de Lijst te gebruiken (VLV) ](configuring-directories.md#configure-user-management-to-use-virtual-list-view-vlv).

**Gebied van de Sortering:** als u Enable Virtuele Controle van de Mening van de Lijst (VLV) selecteerde, specificeer de attributennaam die wordt gebruikt om de index te sorteren. Deze kenmerknaam (zoals uid) is de naam die u hebt opgegeven bij het maken van een index voor VLV op de directoryserver.

### Groepsinstellingen {#group-settings}

**Unieke Herkenningsteken:** (Verplicht) een uniek en constant attribuut dat wordt gebruikt om groepen te identificeren. Gebruik een niet-DN-kenmerk als de unieke id. Deze instelling is afhankelijk van de directoryserver. De waarde is objectGUID voor Actieve Folder 2003, nsuniqueID voor Zon Één, en gids voor eDirectory.

>[!NOTE]
>
>Zorg ervoor dat u een attribuut ingaat dat gegarandeerd om in uw organisatie uniek is te zijn. Het invoeren van een onjuiste waarde kan ernstige systeemproblemen veroorzaken.

**DN van de Basis:** (Verplicht) Distinguished naam van de basis van de folder.

Hoewel Base-DN een verplichte instelling is in de beheerconsole, vereisen sommige directoryservers, zoals IBM Domino Enterprise Server, een lege BaseDN. Als u een lege basis-DN wilt opgeven, exporteert u het bestand config.xml, bewerkt u de instelling in het bestand config.xml en importeert u deze vervolgens opnieuw. (Zie [ het Invoeren en het uitvoeren van het configuratiedossier ](/help/forms/using/admin-help/importing-exporting-configuration-file.md#importing-and-exporting-the-configuration-file).)

**de Filter van het Onderzoek:** (Verplicht) de onderzoeksfilter om het verslag te gebruiken te vinden dat met de groep wordt geassocieerd. U kunt een zoekopdracht op één niveau of een zoekopdracht op subniveau uitvoeren.

**Beschrijving:** attribuut van het Schema voor de beschrijving van de groep

**Volledige Naam:** (Verplicht) attribuut van het Schema voor de volledige naam van de groep

**DN van het Lid:** (Verplicht) attribuut van het Schema voor de volledige naam van leden binnen een groep

**Unieke Herkenningsteken van het Lid:** Unieke herkenningsteken voor een gebruiker of een groep die een lid van de geselecteerde groep is. Deze waarde is afhankelijk van de directoryserver. De waarde is objectSID voor AD2003, nsuniqueID voor Zon Één, en gids voor eDirectory.

Als DN van Lid met een niet-DN attribuut wordt gespecificeerd, gebruikt het Beheer van de Gebruiker het Unieke Herkenningsteken van het Lid om LDAP te vragen om DN van de gebruiker te verzamelen aangezien het aan een unieke herkenningstekenwaarde beantwoordt.

Als DN als uniek herkenningsteken wordt gespecificeerd, te hoeven u niet om het Unieke Herkenningsteken van het Lid te vormen.

**Organisatie:** attribuut van het Schema voor de naam van de organisatie waartot de groep behoort

**Primaire E-mail:** attribuut van het Schema voor het primaire e-mailadres van de groep

**Secundaire E-mail:** attribuut van het Schema voor het secundaire e-mailadres van de groep

**wijzig Tijdstempel:** om de synchronisatie van de deltafolder toe te laten, plaats deze waarde om TimeStamp te wijzigen. (Zie Synchronisatie van delta-directory inschakelen.)

**laat Virtuele Controle van de Mening van de Lijst (VLV) toe:** Een controle LDAP die AEM vormen toelaat om gegevens in partijen van de folderserver terug te winnen. Als u Sun One gebruikt als uw LDAP-directory en de directory vele groepen bevat, maakt u met VLV een index die door Gebruikersbeheer kan worden gebruikt bij het zoeken naar groepen. Deze functie is handig wanneer u een normale gebruikersaccount gebruikt die slechts een beperkte hoeveelheid gegevens kan synchroniseren. U kunt VLV ook inschakelen voor gebruikers. Als u Enable Virtual List View (VLV) Control selecteert, geeft u een naam voor het veld Sorteren op.

>[!NOTE]
>
>Om VLV toe te laten, vorm Zon Één. Zie [ Gebruikersbeheer vormen om de Virtuele Mening van de Lijst te gebruiken (VLV) ](configuring-directories.md#configure-user-management-to-use-virtual-list-view-vlv).

**de Naam van het Gebied van de Sortering:** als u Enable Virtuele Controle van de Lijstmening (VLV) selecteerde, specificeer de attributennaam die wordt gebruikt om de index te sorteren. Deze kenmerknaam is de naam die u hebt opgegeven bij het maken van een index voor VLV op de directoryserver.

>[!NOTE]
>
>Klik op Testen om te controleren of de instellingen van de gebruiker en groep worden verzameld op basis van de basis-DN en de zoekcriteria.

Als gebruikers en groepen worden geretourneerd, geven de resultaten de waarden weer die aan elk veld zijn toegewezen volgens de kenmerkset.

>[!NOTE]
>
>Gebruikersbeheer ondersteunt geen dubbele gebruikers-id&#39;s binnen een domein; slechts één gebruiker met de gebruikersnaam wordt gesynchroniseerd.

## Gebruikersbeheer configureren voor gebruik van de Virtual List View (VLV) {#configure-user-management-to-use-virtual-list-view-vlv}

De synchronisatie van de folder is een belangrijke vereiste voor Gebruikersbeheer. De gebruikers en de groepen worden gesynchroniseerd van een ondernemingsfolder aan het AEM vormengegevensbestand voor het toewijzen van rollen en toestemmingen. Het aantal gebruikers varieert van 100 tot 100000+ afhankelijk van de vereisten, en het stelt een technische uitdaging om gegevens efficiënt te synchroniseren.

Het protocol LDAP verstrekt een mechanisme om grote gegevensreeksen op een gepagineerde manier te vragen door verzoekcontroles te gebruiken. Als u Microsoft Active Directory gebruikt, gebruikt LDAP om de synchronisatie van de formulierdatabase te AEM PagedResultsControl voor het ophalen van gegevens in batches van een bepaalde grootte. De Zon ONE Server van de Folder steunt deze controle niet. Om een gepagineerde vraag tegen de Server van de Folder van de Zon te voltooien ONE, gebruik de Virtuele controle van de Mening van de Lijst (VLV). Deze controle impliceert zowel folder server-zijconfiguratie als cliënt-zijimplementatie.

>[!NOTE]
>
>Deze sectie beschrijft het gebruiken van de controle VLV voor de Server van de Folder van Zon ONE. Nochtans, kunt u deze controle voor om het even welke folderserver gebruiken die controle VLV steunt.

1. Wanneer het vormen van de folder, laat de uitgezochte Virtuele Controle van de Lijstmening (VLV) op zowel de pagina van de Montages van de Gebruiker als de pagina van de Montages van de Groep toe. Wanneer u het selectievakje inschakelt, moet u ook een sorteernaam opgeven in het vak Sorteerveld. De standaardwaarde is uid. (Zie [ Toevoegend folders of douaneSPIs ](configuring-directories.md#adding-directories-or-custom-spis) of [ geef een folder ](configuring-directories.md#edit-a-directory) uit.)
1. Gebruik Sun ONE-beheerconsole of een opdrachtregelscript om de LDAP VLV-ingangen voor gebruikers en groepen te maken. Als u een opdrachtregelscript gebruikt, kunt u de voorbeeldgebruikers en groepen LDIF-bestanden gebruiken. (Zie [ Vormend de Zon ONE Server van de Folder voor VLV ](configuring-directories.md#configuring-the-sun-one-directory-server-for-vlv).)
1. Stop de server en creeer de vereiste index. (Zie [ de Index van de Server van de Folder voor VLV ](configuring-directories.md#create-the-directory-server-index-for-vlv) tot stand brengen.)

### De Sun ONE Directory Server voor VLV configureren {#configuring-the-sun-one-directory-server-for-vlv}

Voor het maken van een VLV is een paar items vereist die de objectklassen `vlvSearch` en `vlvIndex` bevatten. Het vlvSearch-item bevat een zoekbasis en het `vlvFilter` -kenmerk, dat de objectklasse opgeeft die de kenmerken bevat die u wilt sorteren. De objectklasse `vlvIndex` bevat het `vlvSort` -kenmerk, dat een of meer te sorteren kenmerken opgeeft en de volgorde waarin ze worden gesorteerd. (A minteken (-) geeft de omgekeerde alfabetische volgorde aan.) Voor het gebruik van VLV met AEM formulieren zijn aparte vermeldingen voor gebruikers en groepen vereist.

>[!NOTE]
>
>De ingangen van Objecten kunnen worden tot stand gebracht door de Grafische gebruikersinterface van Zon te gebruiken ONE (GUI) of door een bevel-lijn manuscript. Voor instructies over het creëren van de ingangen van Objecten gebruikend GUI, zie de documentatie van Zon ONE.

Hier volgt een voorbeeldscript voor LDIF voor VLV-invoer voor gebruikers:

```text
 dn: cn=lcuser,cn=userRoot,cn=ldbm database,cn=plugins,cn=config
 objectclass: top
 objectclass: vlvSearch
 cn: lcuser
 vlvBase: dc=corp,dc=adobe,dc=com
 vlvScope: 2
 vlvFilter: (&(objectclass=inetOrgPerson))
 aci: (target="ldap:///cn=lcuser,cn=userRoot,cn=ldbm database,cn=plugins,cn=config")(targetattr="*")(version 3.0; acl "Config"
 ;allow(read,search,compare) userdn="ldap:///all"; )
 dn: cn=lcuser,cn=lcuser,cn=userRoot,cn=ldbm database,cn=plugins,cn=config
 cn: lcuser
 vlvSort: cn
 objectclass: top
 objectclass: vlvIndex
```

**creeer de objecten ingangen gebruikend een manuscript**

1. Het voorbeeldscript heeft een LDAP-item met de naam `lcuser` . Dit item is bedoeld voor VLV-gerelateerde configuratie voor gebruikerssynchronisatie in AEM formulieren. Pas de volgende eigenschappen dienovereenkomstig aan:

   **naam van de Ingang:** de ingangsnaam in deze steekproef is `lcuser`. Als `lcuser` wordt gewijzigd, moet deze in alle gebieden van het voorbeeldscript worden gewijzigd.

   **vlvBase:** Basis DN die op de pagina van de Montages van de Gebruiker wordt gespecificeerd.

   **vlvFilter:** de Filter van het Onderzoek die op de pagina van de Montages van de Gebruiker wordt gespecificeerd.

   **vlvSort:** het Gebied van de Soort dat in de VLV montagessectie van de pagina van de Montages van de Gebruiker wordt gespecificeerd. Een controle VLV vereist u om een soortcontrole te specificeren. Dit veld wordt gebruikt als de sorteerparameter voor de gemaakte vlv-index.

   **aci:** de toegangscontrole die in het steekproefmanuscript wordt gespecificeerd verleent om het even welke voor authentiek verklaarde gebruiker het recht om tot de indexen VLV voor lees toegang te hebben, te zoeken, en verrichtingen te vergelijken. De beheerder kan toegang tot een bindende gebruiker beperken, die op de pagina van de Montages van de Server van de Folder wordt gevormd die in het gebruikersinterface van het Gebruikersbeheer wordt gespecificeerd. Als er geen machtigingen worden gegeven, kan bij het zoeken van gebruikers de VLV niet worden gebruikt en genereert de LDAP-server een machtigingsuitzondering.

   >[!NOTE]
   >
   >De naam van het vlvIndex-item wordt gewoonlijk ook ingesteld op `lcuser` , maar u kunt het een andere naam geven. Gebruik dezelfde naam in het vlvindex-gereedschap. (Zie [ tot de Index van de Server van de Folder voor VLV ](configuring-directories.md#create-the-directory-server-index-for-vlv)*.)*

1. Met het gereedschap `ldapmodify` dat bij Sun ONE Server wordt geleverd, maakt u een vergelijkbare vermelding voor groepen met behulp van respectievelijk de Basis-DN van de groep, de Zoekfilter en het Sorteerveld:

   `server directory\shared\bin>ldapmodify -v -a -h host -p port -D "admin user" -w "password" -f "LDIF file location"`

   Typ bijvoorbeeld de volgende tekst:

   `D:\tools\ldap\sun\shared\bin> -v -a -h localhost -p 55850 -D "uid=admin,ou=administrators,ou=topologymanagement,o=netscaperoot" -w "admin" -f "D:\tools\ldap\data\vlv feature\users.ldif"`

### De index van directoryservers voor VLV maken {#create-the-directory-server-index-for-vlv}

Nadat u de directoryinstellingen hebt geconfigureerd en de LDAP VLV-items voor gebruikers en groepen hebt gemaakt, stopt u de server en maakt u de vereiste index.

1. Na het creëren van objecten ingangen, stop Zon ONE Server.
1. Met het gereedschap Vlvindex genereert u de index door de volgende tekst te typen:

   *instantie van de folderserver* `\vlvindex.bat -n userRoot -T lcuser`

   De volgende uitvoer wordt gegenereerd:

   ```shell
    D:\tools\ldap\sun\shared\bin>..\..\slapd-chetanmeh-xp3\vlvindex.bat -n userRoot -T livecycle
    [21/Nov/2007:16:47:26 +051800] - userRoot: Indexing VLV: livecycle
    [21/Nov/2007:16:47:27 +051800] - userRoot: Indexed 1000 entries (5%).
    [21/Nov/2007:16:47:27 +051800] - userRoot: Indexed 2000 entries (9%).
    ...
    [21/Nov/2007:16:47:29 +051800] - userRoot: Indexed 20000 entries (94%).
    [21/Nov/2007:16:47:29 +051800] - userRoot: Indexed 21000 entries (99%).
    [21/Nov/2007:16:47:29 +051800] - userRoot: Finished indexing.
   ```

   Het vlvindex-gereedschap bevindt zich in de map met de directoryserverinstanties. Als de Zon ONE Server twee instanties heeft die server1 en server2 in werking stellen, is het vlvindex hulpmiddel in *Zon ONE serverfolder* \ server1 folder. De waarde voor parameter `-T` is de waarde van het `cn` -kenmerk van de vlvindex-item die eerder in het voorbeeld LDIF is gemaakt. In dit geval is dit `lcuser` .

1. Als VLV ook voor groepen wordt toegelaten, creeer de overeenkomstige index voor de groepen. Verifieer of de indexen door het volgende bevel in werking te stellen worden gecreeerd:

   *zon één serverfolder* `\shared\bin>ldapsearch -h`*hostname* `-p`*haven nr* `-s base -b "" objectclass=*`

   Uitvoer zoals de volgende voorbeeldgegevens wordt gegenereerd:

   ```shell
    D:\tools\ldap\sun\shared\bin>ldapsearch.exe -h localhost -p 55850 -s base -b "" objectclass=*
    ldapsearch.exe: started Tue Nov 27 16:34:20 2007
    version: 1
    dn:
    objectClass: top
    namingContexts: dc=corp,dc=adobe,dc=com
    supportedExtension: 2.16.840.1.113730.3.5.7
    ...
    vlvsearch: cn=MCC ou=testdata dc=corp dc=adobe dc=com, cn=userRoot,cn=ldbm dat
        abase,cn=plugins,cn=config
    vlvsearch: cn=lcuser,cn=userRoot,cn=ldbm database,cn=plugins,cn=config
    vlvsearch: cn=Browsing ou=testdata,cn=userRoot,cn=ldbm database,cn=plugins,cn=
        config
    1 matches
   ```
