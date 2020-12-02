---
title: Mappen configureren
seo-title: Mappen configureren
description: Leer hoe u mappen toevoegt, bewerkt en verwijdert en gebruikersbeheer configureert om de weergave van virtuele lijsten te gebruiken.
seo-description: Leer hoe u mappen toevoegt, bewerkt en verwijdert en gebruikersbeheer configureert om de weergave van virtuele lijsten te gebruiken.
uuid: 0bf1a8a7-c917-4248-9937-d24e31c5ba17
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/setting_up_and_managing_domains
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 1f15f028-aa81-478e-97eb-f83a4dc0418c
translation-type: tm+mt
source-git-commit: 1343cc33a1e1ce26c0770a3b49317e82353497ab
workflow-type: tm+mt
source-wordcount: '3246'
ht-degree: 0%

---


# Mappen {#configuring-directories} configureren

Voor elk ondernemingsdomein u vormt, specificeer de folders die de authentificatieleverancier voor gebruikersinformatie vraagt. U kunt meerdere mappen voor een domein configureren.

## Mappen of aangepaste SPI&#39;s {#adding-directories-or-custom-spis} toevoegen

Voor elk ondernemingsdomein u vormt, specificeer de folders die de authentificatieleverancier voor gebruikersinformatie vraagt. U kunt een folder aan een bestaand ondernemingsdomein of aan een nieuw ondernemingsdomein toevoegen dat u toevoegt. U kunt meerdere mappen voor een domein configureren. U kunt een domein ook vormen om een interface van de douaneleverancier van de Dienst (SPI) voor synchronisatie te gebruiken.

### Een map {#add-a-directory} toevoegen

1. Klik in de beheerconsole op Instellingen > Gebruikersbeheer > Domeinbeheer.
1. Klik op Nieuw Enterprise-domein of selecteer een bestaand ondernemingsdomein.
1. Klik op Map toevoegen.
1. Typ in het vak Profielnaam een naam om deze map van elkaar te onderscheiden en klik op Volgende.
1. Configureer de instellingen van de directoryserver. (Zie [Directory settings](configuring-directories.md#directory-settings).)
1. Klik op Testen om te controleren of er verbinding kan worden gemaakt met de LDAP-server. Als de test ontbreekt, herzie de uitzondering in het het logboekdossier van de Server van de Toepassing om de worteloorzaak van de mislukking te bepalen. Klik op Sluiten en vervolgens op Volgende.
1. Selecteer Gebruikersinstellingen en configureer de instellingen naar wens. (Zie [Directory settings](configuring-directories.md#directory-settings).)
1. Om te verifiëren dat basis DN en andere gevormde attributen de correcte partij van gebruikers verzamelen, klik Test. LDAP probeert de eerste 200 records op te halen met behulp van de opgegeven instellingen (zoals de basis-DN, het zoekfilter en alle kenmerken).

   Als gebruikers worden geretourneerd, geven de resultaten de waarden weer die aan elk veld zijn toegewezen volgens de kenmerkset. Als de test mislukt als gevolg van een niet-bestaande servernaam, onjuiste autorisatiegegevens of onjuiste kenmerken, wordt het volgende foutbericht weergegeven: &quot;De opgegeven zoekcriteria hebben geen resultaat opgeleverd&quot;. Om de worteloorzaak van de mislukking te bepalen, herzie de uitzondering in het het logboekdossier van de Server van de Toepassing. Klik op Sluiten en vervolgens op Volgende.

1. Selecteer Groepsinstellingen en configureer de instellingen naar wens. (Zie [Directory settings](configuring-directories.md#directory-settings).)
1. Om te verifiëren dat basis DN en andere gevormde attributen de correcte partij van groepen verzamelen, klik Test. Als groepen worden geretourneerd, geven de resultaten de waarden weer die aan elk veld zijn toegewezen volgens de kenmerkset. Klik op Sluiten.

### Een aangepaste SPI {#add-a-custom-spi} toevoegen

Voor informatie over het creëren van een douaneSPI, zie &quot;het Ontwikkelen van SPIs voor AEM vormen&quot;in [Programmering met AEM vormen](https://www.adobe.com/go/learn_aemforms_programming_63). Start de server opnieuw om een nieuw geïmplementeerde aangepaste SPI beschikbaar te maken voor associatie met het domein.

1. Klik in de beheerconsole op Instellingen > Gebruikersbeheer > Domeinbeheer.
1. Klik op Nieuw Enterprise-domein of selecteer een bestaand ondernemingsdomein.
1. Klik op Map toevoegen.
1. Typ een naam in het vak Profielnaam, selecteer Aangepaste SPI-provider en klik op Volgende.
1. Selecteer een aangepaste gebruikersprovider in de lijst en klik op Volgende.
1. Selecteer een aangepaste groepsprovider in de lijst en klik op Voltooien.

## Een map {#edit-a-directory} bewerken

U kunt de details van een folder uitgeven die u eerder vormde.

1. Klik in de beheerconsole op Instellingen > Gebruikersbeheer > Domeinbeheer.
1. Klik op het juiste domein in de lijst en selecteer op de pagina die wordt weergegeven de juiste map in de lijst.
1. Configureer de directory-, gebruikers- en groepsinstellingen naar wens. (Zie [Directory settings](configuring-directories.md#directory-settings).)
1. Klik op OK.

## Een map {#delete-a-directory} verwijderen

Wanneer u domeinen synchroniseert nadat u een map hebt verwijderd, worden alle gebruikers en groepen in die map gemarkeerd als verouderd in de database. Deze worden niet geretourneerd in een zoekopdracht vanuit de beheerconsole.

>[!NOTE]
>
>Voor bedrijfsdomeinen is ten minste één verificatieprovider en directoryprovider vereist.

1. Klik in de beheerconsole op Instellingen > Gebruikersbeheer > Domeinbeheer.
1. Klik op het desbetreffende domein in de lijst.
1. Schakel het selectievakje voor de juiste map in en klik op Verwijderen.
1. Klik op OK op de bevestigingspagina die wordt weergegeven en klik nogmaals op OK.

## Directoryinstellingen {#directory-settings}

Wanneer u een map aan een domein toevoegt, geeft u de volgende directoryinstellingen op.

**Server:** (Verplicht) Volledig gekwalificeerde domeinnaam (FQDN) van de directoryserver. Voor een computer met de naam x in het netwerk corp.adobe.com is de FQDN bijvoorbeeld x.corp.adobe.com. U kunt een IP-adres gebruiken in plaats van de naam van de FQDN-server.

**Poort:** (verplicht) De poort die de directoryserver gebruikt. Typisch 389, of 636 als het Veilige protocol van de Laag van Contactdozen (SSL) wordt gebruikt voor het verzenden van authentificatieinformatie over het netwerk.

**SSL:**  (verplicht) Geeft aan of de directoryserver SSL gebruikt wanneer gegevens via het netwerk worden verzonden. De standaardwaarde is Nee. Als u Ja instelt, moet het bijbehorende LDAP-servercertificaat worden vertrouwd door de JRE (Java™ runtime environment) van de toepassingsserver.

**Binding**  (verplicht) geeft aan hoe u toegang tot de map wilt krijgen.

**Anoniem:** Geen gebruikersnaam of wachtwoord vereist. Een anonieme gebruiker kan slechts een beperkte hoeveelheid gegevens ophalen. Deze optie kan handig zijn voor de eerste test.

**Gebruiker:** Verificatie is vereist. Geef in het vak Naam de naam op van de gebruikersrecord die toegang kan krijgen tot de map. U kunt het beste de volledige DN (Distinguished Name) van de gebruikersaccount invoeren, zoals cn=Jane Doe, ou=user, dc=can, dc=com. Geef in het vak Wachtwoord het bijbehorende wachtwoord op. Deze instellingen zijn vereist wanneer u de optie Gebruiker binden selecteert.

**Naam:** Naam die kan worden gebruikt om met het gegevensbestand te verbinden LDAP wanneer de anonieme toegang niet wordt toegelaten. Voor Actieve Folder 2003, specificeer `[domain name]\[userid]`. Voor Sun™ One, eDirectory of IBM Tivoli Directory Server geeft u de volledig gekwalificeerde naam van de gebruiker op, zoals uid=lcuser,ou=it,o=company.com.

**Wachtwoord:** Wachtwoord dat overeenkomt met de naam die u hebt opgegeven om verbinding te maken met de LDAP-database wanneer anonieme toegang niet is ingeschakeld.

**Pagina vullen met:** Wanneer deze optie is geselecteerd, worden de kenmerken op de pagina&#39;s met gebruikersinstellingen en groepsinstellingen gevuld met de bijbehorende LDAP-waarden.

**Basis-DN&#39;s ophalen:** haalt de basis-DN&#39;s op en geeft deze weer in de vervolgkeuzelijst. Deze instelling is handig wanneer u meerdere basis-DN&#39;s hebt en een waarde moet selecteren.

**Verwijzing inschakelen:** Deze instelling is van toepassing wanneer uw organisatie meerdere Active Directory-domeinen gebruikt die in een hiërarchische structuur zijn ingedeeld en u mapinstellingen voor alleen het bovenliggende domein hebt opgegeven. In deze situatie, wanneer u deze optie selecteert, kan het Beheer van de Gebruiker tot gebruiker en groepdetails van de kinddomeinen toegang hebben.

>[!NOTE]
>
>Klik op Testen om te controleren of er verbinding kan worden gemaakt met de LDAP-server. Om de worteloorzaak van om het even welke mislukkingen te bepalen, herzie de uitzondering in het het logboekdossier van de Server van de Toepassing.

### Gebruikersinstellingen {#user-settings}

**Unieke id:** (verplicht) Een uniek en constant kenmerk dat wordt gebruikt om gebruikers te identificeren. Gebruik een niet-DN-kenmerk als de unieke id omdat de DN van een gebruiker kan veranderen als deze naar een ander deel van de organisatie wordt verplaatst. Deze instelling is afhankelijk van de directoryserver. De waarde is objectGUID voor Actieve Folder 2003, nsuniqueID voor Sun™ One, en guid voor eDirectory.

>[!NOTE]
>
>Zorg ervoor dat u een attribuut ingaat dat gegarandeerd om in uw organisatie uniek is te zijn. Het invoeren van een onjuiste waarde kan ernstige systeemproblemen veroorzaken.

**Basis-DN:** Instellen als beginpunt voor het synchroniseren van gebruikers en groepen vanuit de LDAP-hiërarchie. Het is best om een basis DN op het laagste niveau van de hiërarchie te specificeren die alle gebruikers en groepen omvat die voor de diensten moeten worden gesynchroniseerd.

Als u de Enable verwijzingsoptie in de montages van de Folder selecteerde, plaats de optie van de Basis DN aan het *dc* deel van DN. De verwijzing werkt alleen als het zoekbereik zowel bovenliggende als onderliggende domeinen bevat.

>[!NOTE]
>
>Neem de DN van de gebruiker niet op in deze instelling. Als u een bepaalde gebruiker wilt synchroniseren, gebruikt u de instelling Zoekfilter.

Hoewel Base-DN een verplichte instelling is in de beheerconsole, vereisen sommige directoryservers, zoals IBM Domino Enterprise Server, mogelijk een lege BaseDN. Als u een lege basis-DN wilt opgeven, exporteert u het bestand config.xml, bewerkt u de instelling in het bestand config.xml en importeert u deze vervolgens opnieuw. (Zie [Het configuratiebestand importeren en exporteren](/help/forms/using/admin-help/importing-exporting-configuration-file.md#importing-and-exporting-the-configuration-file).)

**Zoekfilter:**  (verplicht) Het zoekfilter dat moet worden gebruikt om de record te zoeken die aan de gebruiker is gekoppeld. U kunt een zoekopdracht op één niveau of een zoekopdracht op subniveau uitvoeren. (Zie Syntaxis van de Filter van het Onderzoek of RFC 2254.) Aanvullende informatie voor het schema van Microsoft AD, zie het Actieve Schema van de Folder.

**Beschrijving:** Schema, kenmerk voor beschrijving van de gebruiker

**Volledige naam:** (Verplicht) Schema-kenmerk voor de volledige naam van de gebruiker

**Aanmeldings-id:** (verplicht) Schema-kenmerk voor de aanmeldings-id van de gebruiker

**Achternaam:** (verplicht) Schema-kenmerk voor achternaam van de gebruiker

**Voornaam:** (verplicht) Schema-kenmerk voor voornaam van gebruiker

**Initialen:kenmerk** Schema voor initialen van de gebruiker

**Bedrijfs Kalender:** Laat u toe om een bedrijfskalender aan een gebruiker in kaart te brengen, die op de waarde voor dit het plaatsen (de sleutel van de bedrijfkalender) wordt gebaseerd. Zakelijke kalenders definiëren zakelijke en niet-zakelijke dagen. AEM formulieren kunnen zakelijke kalenders gebruiken voor het berekenen van toekomstige datums en tijden voor gebeurtenissen zoals herinneringen, deadlines en escalaties. De manier u zaken kalendersleutels aan gebruikers toewijst hangt af van of u een onderneming, lokaal, of hybride domein gebruikt. (Zie Business Calendars configureren.)

Als u een ondernemingsdomein gebruikt, kunt u het BedrijfsKalender plaatsen aan een gebied in de folder in kaart brengen LDAP. Als bijvoorbeeld elk gebruikersrecord in uw map een veld *country* bevat en u bedrijfscalenders wilt toewijzen op basis van het land waar de gebruiker zich bevindt, geeft u de veldnaam *country* op als de waarde voor de instelling van de Business Calendar. Vervolgens kunt u de zakelijke kalendersleutels (de waarden die zijn gedefinieerd voor het veld *country* in de LDAP-directory) toewijzen aan zakelijke kalenders in de formulierworkflow.

De hoeveelheid ruimte die wordt gebruikt voor het weergeven van de naam van de zakelijke kalendersleutel in de pagina&#39;s van de formulierwerkstroom is beperkt. Beperk de naam van de zakelijke kalendersleutel tot minder dan 53 tekens om te voorkomen dat deze op deze pagina&#39;s wordt afgekapt.

**Tijdstempel wijzigen:** Als u synchronisatie van de deltapmap wilt inschakelen, stelt u deze waarde in op Tijdstempel wijzigen. (Zie Synchronisatie van delta-directory inschakelen.)

**Organisatie:** Schema-kenmerk voor de naam van de organisatie waartoe de gebruiker behoort.

**Primaire e-mail:** Schema, kenmerk voor het primaire e-mailadres van de gebruiker.

**Secundaire e-mail:** Schema, kenmerk voor het secundaire e-mailadres van de gebruiker.

**Telefoon:** Schema-kenmerk voor het telefoonnummer van de gebruiker.

**Postadres:** Schemakenmerk voor het postadres van de gebruiker.

**Locale:** Schema-kenmerk dat de ISO-landinstellingsinformatie bevat. De waarde bestaat uit een taalcode van twee letters of een taal- en landcode.

**Tijdzone:kenmerk** Schema dat de tijdzone bevat waar de gebruiker zich bevindt. De waarde bestaat uit een tekenreeks zoals Plaats/Land.

**Enable Virtual List View (VLV) Control:** Een LDAP-besturingselement waarmee AEM formulieren gegevens in batches kunnen ophalen van de directoryserver. Als u Sun One gebruikt als uw LDAP-directory en de map veel gebruikers bevat, maakt u met VLV een index die door Gebruikersbeheer kan worden gebruikt bij het zoeken naar gebruikers. Deze functie is handig wanneer u een normale gebruikersaccount gebruikt die slechts een beperkte hoeveelheid gegevens kan synchroniseren. U kunt VLV voor groepen ook toelaten. Als u VLV-controle (Virtual List View) inschakelen selecteert, geeft u een naam op in het vak Sorteerveld.

>[!NOTE]
>
>Om VLV toe te laten, vorm Zon Één. Zie [Gebruikersbeheer configureren voor het gebruik van de Virtual List View (VLV)](configuring-directories.md#configure-user-management-to-use-virtual-list-view-vlv).

**Sorteerveld:** Als u VLV-controle (Virtual List View) inschakelen hebt geselecteerd, geeft u de kenmerknaam op die wordt gebruikt om de index te sorteren. Deze kenmerknaam (zoals uid) is de naam die u hebt opgegeven bij het maken van een index voor VLV op de directoryserver.

### Groepsinstellingen {#group-settings}

**Unieke id:** (verplicht) Een uniek en constant kenmerk dat wordt gebruikt om groepen te identificeren. Gebruik een niet-DN-kenmerk als de unieke id. Deze instelling is afhankelijk van de directoryserver. De waarde is objectGUID voor Actieve Folder 2003, nsuniqueID voor Zon Één, en gids voor eDirectory.

>[!NOTE]
>
>Zorg ervoor dat u een attribuut ingaat dat gegarandeerd om in uw organisatie uniek is te zijn. Het invoeren van een onjuiste waarde kan ernstige systeemproblemen veroorzaken.

**Basis-DN:** (verplicht) Standaard DN, Distinguished Name van de directory.

Hoewel Base-DN een verplichte instelling is in de beheerconsole, vereisen sommige directoryservers, zoals IBM Domino Enterprise Server, een lege BaseDN. Als u een lege basis-DN wilt opgeven, exporteert u het bestand config.xml, bewerkt u de instelling in het bestand config.xml en importeert u deze vervolgens opnieuw. (Zie [Het configuratiebestand importeren en exporteren](/help/forms/using/admin-help/importing-exporting-configuration-file.md#importing-and-exporting-the-configuration-file).)

**Zoekfilter:**  (verplicht) Het zoekfilter dat moet worden gebruikt om de record te zoeken die aan de groep is gekoppeld. U kunt een zoekopdracht op één niveau of een zoekopdracht op subniveau uitvoeren.

**Beschrijving:** Schema, kenmerk voor beschrijving van de groep

**Volledige naam:** (Verplicht) Schema-kenmerk voor de volledige naam van de groep

**DN:** (verplicht) Schema-kenmerk voor de DN-naam van leden binnen een groep

**Unieke id van lid:** Unieke herkenningsteken voor een gebruiker of een groep die een lid van de geselecteerde groep is. Deze waarde is afhankelijk van de directoryserver. De waarde is objectSID voor AD2003, nsuniqueID voor Zon Één, en gids voor eDirectory.

Als Member DN wordt gespecificeerd met een niet-DN attribuut, gebruikt het Beheer van de Gebruiker het Unieke Herkenningsteken van het Lid om LDAP te vragen om DN van de gebruiker te verzamelen aangezien het aan een unieke herkenningstekenwaarde beantwoordt.

Als DN als uniek herkenningsteken wordt gespecificeerd, te hoeven u niet om het Unieke Herkenningsteken van het Lid te vormen.

**Organisatie:** Schema, kenmerk voor de naam van de organisatie waartoe de groep behoort

**Primaire e-mail:** Schema, kenmerk voor het primaire e-mailadres van de groep

**Secundaire e-mail:** Schema, kenmerk voor het secundaire e-mailadres van de groep

**Tijdstempel wijzigen:** Als u synchronisatie van de deltapmap wilt inschakelen, stelt u deze waarde in op Tijdstempel wijzigen. (Zie Synchronisatie van delta-directory inschakelen.)

**Enable Virtual List View (VLV) Control:** Een LDAP-besturingselement waarmee AEM formulieren gegevens in batches kunnen ophalen van de directoryserver. Als u Sun One gebruikt als uw LDAP-directory en de directory vele groepen bevat, maakt u met VLV een index die door Gebruikersbeheer kan worden gebruikt bij het zoeken naar groepen. Deze functie is handig wanneer u een normale gebruikersaccount gebruikt die slechts een beperkte hoeveelheid gegevens kan synchroniseren. U kunt VLV ook inschakelen voor gebruikers. Als u Enable Virtual List View (VLV) Control selecteert, geeft u een naam voor het veld Sorteren op.

>[!NOTE]
>
>Om VLV toe te laten, vorm Zon Één. Zie [Gebruikersbeheer configureren voor het gebruik van de Virtual List View (VLV)](configuring-directories.md#configure-user-management-to-use-virtual-list-view-vlv).

**Veldnaam sorteren:** Als u VLV-controle inschakelen hebt geselecteerd, geeft u de kenmerknaam op die wordt gebruikt om de index te sorteren. Deze kenmerknaam is de naam die u hebt opgegeven bij het maken van een index voor VLV op de directoryserver.

>[!NOTE]
>
>Klik op Testen om te controleren of de instellingen van de gebruiker en groep worden verzameld op basis van de basis-DN en de zoekcriteria.

Als gebruikers en groepen worden geretourneerd, geven de resultaten de waarden weer die aan elk veld zijn toegewezen volgens de kenmerkset.

>[!NOTE]
>
>Gebruikersbeheer ondersteunt geen dubbele gebruikers-id&#39;s binnen een domein; er wordt slechts één gebruiker met de gebruikersnaam gesynchroniseerd.

## Gebruikersbeheer configureren voor gebruik van VLV (Virtual List View) {#configure-user-management-to-use-virtual-list-view-vlv}

De synchronisatie van de folder is een belangrijke vereiste voor Gebruikersbeheer. De gebruikers en de groepen worden gesynchroniseerd van een ondernemingsfolder aan het AEM vormengegevensbestand voor het toewijzen van rollen en toestemmingen. Het aantal gebruikers varieert van 100 tot 100000+ afhankelijk van de vereisten, en het stelt een technische uitdaging om gegevens efficiënt te synchroniseren.

Het protocol LDAP verstrekt een mechanisme om grote gegevensreeksen op een gepagineerde manier te vragen door verzoekcontroles te gebruiken. Als u Microsoft Active Directory gebruikt, gebruikt LDAP om de synchronisatie van de formulierdatabase te AEM PagedResultsControl voor het ophalen van gegevens in batches van een bepaalde grootte. De Zon ONE Server van de Folder steunt deze controle niet. Om een gepagineerde vraag tegen de Server van de Folder van de Zon te voltooien ONE, gebruik de Virtuele controle van de Mening van de Lijst (VLV). Deze controle impliceert zowel folder server-zijconfiguratie als cliënt-zijimplementatie.

>[!NOTE]
>
>Deze sectie beschrijft het gebruiken van de controle VLV voor de Server van de Folder van Zon ONE. Nochtans, kunt u deze controle voor om het even welke folderserver gebruiken die controle VLV steunt.

1. Wanneer het vormen van de folder, laat de uitgezochte Virtuele Controle van de Lijstmening (VLV) op zowel de pagina van de Montages van de Gebruiker als de pagina van de Montages van de Groep toe. Wanneer u het selectievakje inschakelt, moet u ook een sorteernaam opgeven in het vak Sorteerveld. De standaardwaarde is uid. (Zie [Mappen of aangepaste SPI&#39;s toevoegen](configuring-directories.md#adding-directories-or-custom-spis) of [Een map bewerken](configuring-directories.md#edit-a-directory).)
1. Gebruik Sun ONE-beheerconsole of een opdrachtregelscript om de LDAP VLV-ingangen voor gebruikers en groepen te maken. Als u een opdrachtregelscript gebruikt, kunt u de voorbeeldgebruikers en groepen LDIF-bestanden gebruiken. (Zie [Het vormen van de Zon ONE Server van de Folder voor VLV](configuring-directories.md#configuring-the-sun-one-directory-server-for-vlv).)
1. Stop de server en creeer de vereiste index. (Zie [De index van de Server van de Folder voor VLV](configuring-directories.md#create-the-directory-server-index-for-vlv) tot stand brengen.)

### Sun ONE Directory Server voor VLV {#configuring-the-sun-one-directory-server-for-vlv} configureren

Voor het maken van een VLV is een paar items vereist die de objectklassen `vlvSearch` en `vlvIndex` bevatten. Het vlvSearch-item bevat een zoekbasis en het kenmerk `vlvFilter`, dat de objectklasse opgeeft die de kenmerken bevat die u wilt sorteren. De objectklasse `vlvIndex` bevat het kenmerk `vlvSort`, dat een of meer kenmerken opgeeft die moeten worden gesorteerd en de volgorde waarin ze moeten worden gesorteerd. (A minteken (-) geeft de omgekeerde alfabetische volgorde aan.) Voor het gebruik van VLV met AEM formulieren zijn aparte vermeldingen voor gebruikers en groepen vereist.

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

**Objecten met een script maken**

1. Het voorbeeldscript heeft een LDAP-item met de naam `lcuser`. Dit item is bedoeld voor VLV-gerelateerde configuratie voor gebruikerssynchronisatie in AEM formulieren. Pas de volgende eigenschappen dienovereenkomstig aan:

   **Invoernaam:** de naam van het item in dit voorbeeld is  `lcuser`. Als `lcuser` wordt veranderd, moet het op alle gebieden van het steekproefmanuscript worden veranderd.

   **vlvBase:** De basis-DN die is opgegeven op de pagina Gebruikersinstellingen.

   **vlvFilter:** Het zoekfilter dat is opgegeven op de pagina Gebruikersinstellingen.

   **vlvSort:** Het veld Sorteren dat is opgegeven in het gedeelte VLV-instellingen van de pagina Gebruikersinstellingen. Een controle VLV vereist u om een soortcontrole te specificeren. Dit veld wordt gebruikt als de sorteerparameter voor de gemaakte vlv-index.

   **aci:** Het toegangsbeheer dat in het steekproefmanuscript wordt gespecificeerd verleent om het even welke voor authentiek verklaarde gebruiker het recht om tot de indexen VLV voor lees, onderzoek, en vergelijkingsverrichtingen toegang te hebben. De beheerder kan toegang tot een bindende gebruiker beperken, die op de pagina van de Montages van de Server van de Folder wordt gevormd die in het gebruikersinterface van het Gebruikersbeheer wordt gespecificeerd. Als er geen machtigingen worden gegeven, kan bij het zoeken van gebruikers de VLV niet worden gebruikt en genereert de LDAP-server een machtigingsuitzondering.

   >[!NOTE]
   >
   >Als conventie wordt de naam van het vlvIndex-item ook ingesteld op `lcuser`, maar u kunt deze een andere naam geven. Gebruik dezelfde naam in het vlvindex-gereedschap. (Zie [De index van de Server van de Folder voor VLV ](configuring-directories.md#create-the-directory-server-index-for-vlv)*.)* creëren

1. Met het gereedschap `ldapmodify` dat bij Sun ONE Server wordt geleverd, maakt u een vergelijkbare vermelding voor groepen met behulp van respectievelijk de Basis-DN van de groep, de Zoekfilter en het Sorteerveld:

   `server directory\shared\bin>ldapmodify -v -a -h host -p port -D "admin user" -w "password" -f "LDIF file location"`

   Typ bijvoorbeeld de volgende tekst:

   `D:\tools\ldap\sun\shared\bin> -v -a -h localhost -p 55850 -D "uid=admin,ou=administrators,ou=topologymanagement,o=netscaperoot" -w "admin" -f "D:\tools\ldap\data\vlv feature\users.ldif"`

### De indexserverindex voor VLV maken {#create-the-directory-server-index-for-vlv}

Nadat u de directoryinstellingen hebt geconfigureerd en de LDAP VLV-items voor gebruikers en groepen hebt gemaakt, stopt u de server en maakt u de vereiste index.

1. Na het creëren van objecten ingangen, stop Zon ONE Server.
1. Met het gereedschap Vlvindex genereert u de index door de volgende tekst te typen:

   *directoryserverinstantie* `\vlvindex.bat -n userRoot -T lcuser`

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

   Het vlvindex-gereedschap bevindt zich in de map met de directoryserverinstanties. Als de Zon ONE Server twee instanties heeft die server1 en server2 in werking stellen, wordt het vlvindex hulpmiddel gevestigd in *Zon ONE serverfolder* \ server1 folder. De waarde voor parameter `-T` is de waarde van het `cn` attribuut van de vlvindex ingang die eerder in de steekproef LDIF wordt gecreeerd. In dit geval is dit `lcuser`.

1. Als VLV ook voor groepen wordt toegelaten, creeer de overeenkomstige index voor de groepen. Verifieer of de indexen door het volgende bevel in werking te stellen worden gecreeerd:

   *sun one server* `\shared\bin>ldapsearch -h`** `-p`*directory hostname port* `-s base -b "" objectclass=*`

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

