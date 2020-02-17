---
title: Bedrijfskalenders configureren
seo-title: Bedrijfskalenders configureren
description: Zakelijke kalenders definiëren zakelijke en niet-zakelijke dagen voor uw organisatie. Leer hoe u de bedrijfskalenders configureert.
seo-description: Zakelijke kalenders definiëren zakelijke en niet-zakelijke dagen voor uw organisatie. Leer hoe u de bedrijfskalenders configureert.
uuid: 0ba610b8-72a8-480c-8783-70d98cbe890a
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms_workflow
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 7a85e13d-4800-47c4-812a-5c6e2355298a
translation-type: tm+mt
source-git-commit: 58fa0f05bae7ab5ba51491be3171b5c6ffbe870d

---


# Bedrijfskalenders configureren {#configuring-business-calendars}

*Zakelijke kalenders* definiëren de zakelijke en niet-zakelijke dagen (bijvoorbeeld wettelijke feestdagen, weekends en dagen waarop het bedrijf wordt afgesloten) voor uw organisatie. Bij het gebruik van zakelijke kalenders slaat AEM-formulieren niet-werkdagen over wanneer bepaalde datumberekeningen worden uitgevoerd. In Workbench, kunt u specificeren of om bedrijfskalenders voor gebruiker-bijbehorende gebeurtenissen zoals taakherinneringen, termijnen, en escalaties te gebruiken of voor acties niet verbonden aan gebruikers, zoals de Gebeurtenissen van de Tijdopnemer en de Wacht Dienst.

Een taakherinnering is bijvoorbeeld geconfigureerd voor drie werkdagen nadat de taak aan een gebruiker is toegewezen. De taak wordt op donderdag toegewezen. De volgende drie dagen zijn echter geen werkdagen omdat de vrijdag een nationale feestdag is en de volgende twee dagen weekenddagen. De herinnering wordt daarom verzonden op woensdag van de volgende week.

>[!NOTE]
>
>Bij het berekenen van datums en tijden met zakelijke kalenders worden in AEM-formulieren de datum en tijd gebruikt van de server waarop deze wordt uitgevoerd en wordt het verschil tussen tijdzones niet gecorrigeerd. Bijvoorbeeld, als een taakherinnering om 10:00 uur op een server gepland is die in Londen loopt, maar de gebruiker die de herinnering ontvangt wordt gevestigd in de Stad van New York, zou de gebruiker de herinnering om 5:00 lokale tijd ontvangen.

## De standaardagenda voor het bedrijf gebruiken {#using-the-default-business-calendar}

AEM-formulieren bieden een standaardagenda voor het bedrijf ( *ingebouwde kalender*) die zaterdag en zondag aanduidt als niet-werkdagen. Als alle gebruikers in uw organisatie dezelfde niet-werkdagen hebben, kunt u de standaard bedrijfsagenda bijwerken zodat deze bij uw organisatie past. Wanneer het gebruiken van slechts de standaard bedrijfskalender, te hoeven u niet bedrijfscalendars in het Beheer van de Gebruiker toe te laten of om het even welke afbeeldingen te verstrekken. Als er geen andere zakelijke kalenders zijn gedefinieerd, gebruiken AEM-formulieren de standaard zakelijke kalender.

## Meerdere zakelijke kalenders instellen {#setting-up-multiple-business-calendars}

Als sommige gebruikers in uw organisatie verschillende niet-bedrijfsdagen hebben, kunt u veelvoudige bedrijfsplannen bepalen en afbeeldingen vormen die een runtime resolutie van een bedrijfskalender voor een gebruiker toestaan.

### Meerdere zakelijke kalenders definiëren {#define-multiple-business-calendars}

1. Bepaal hoe u de aangewezen bedrijfskalender met een gebruiker zult associëren. Er zijn twee manieren om een bedrijfskalender met een gebruiker te associëren:

   **** Groepslidmaatschap: U kunt een bedrijfskalender aan een gebruiker toewijzen die op het de groepslidmaatschap van de gebruiker wordt gebaseerd. In dit geval gebruikt elke gebruiker in de groep dezelfde agenda voor het bedrijf.

   Als een gebruiker lid is van twee verschillende groepen en deze groepen zijn toegewezen aan twee verschillende zakelijke kalenders, gebruiken AEM-formulieren de eerste kalender die wordt gevonden in de zoekresultaten. Overweeg in dit geval het gebruik van agenda&#39;s voor zakelijk gebruik om gebruikers te koppelen aan zakelijke kalenders.

   **** Zakelijke kalender-sleutels: U kunt een zakelijke kalender toewijzen aan een gebruiker op basis van een zakelijke kalendersleutel. Dit is een instelling die is opgegeven in Gebruikersbeheer. Vervolgens wijst u de agenda-toets toe aan een zakelijke kalender in de werkstroom voor formulieren.

   De manier waarop u zakelijke kalendersleutels toewijst aan gebruikers hangt af van of u een onderneming, lokaal, of hybride domein gebruikt. Zie [Domeinen](/help/forms/using/admin-help/adding-domains.md#adding-domains)toevoegen voor meer informatie over het instellen van domeinen.

   Als u een lokaal of hybride domein gebruikt, wordt de informatie over gebruikers opgeslagen slechts in het gegevensbestand van het Beheer van de Gebruiker. Als u de agenda-toets voor deze gebruikers wilt instellen, voert u in het veld Business Calendar Key een tekenreeks in bij het toevoegen of bewerken van een gebruiker in Gebruikersbeheer. (Zie Gebruikers [toevoegen en configureren](/help/forms/using/admin-help/adding-configuring-users.md#adding-and-configuring-users).) Vervolgens wijst u de zakelijke kalendersleutels (de tekenreeksen) toe aan zakelijke kalenders in de formulierwerkstroom. (Zie Gebruikers en groepen [toewijzen aan een zakelijke kalender](configuring-business-calendars.md#mapping-users-and-groups-to-a-business-calendar).)

   Als u een ondernemingsdomein gebruikt, verblijft de informatie over gebruikers in een derdesopslagsysteem, zoals een folder LDAP, die het Beheer van de Gebruiker met het gegevensbestand van het Beheer van de Gebruiker synchroniseert. Op deze manier kunt u een zakelijke kalendersleutel toewijzen aan een veld in de LDAP-directory. Als bijvoorbeeld elk gebruikersrecord in uw map een veld &quot;Land&quot; bevat en u bedrijfscalenders wilt toewijzen op basis van het land waar de gebruiker zich bevindt, geeft u de veldnaam &quot;Land&quot; op in het veld Bedrijfscalenderoets wanneer u de gebruikersinstellingen voor de map opgeeft. (Zie [Mappen](/help/forms/using/admin-help/configuring-directories.md#configuring-directories)configureren.) Vervolgens kunt u de agenda-sleutels voor het bedrijf (de waarden die zijn gedefinieerd voor het veld &quot;Land&quot; in de LDAP-lijst) toewijzen aan de agenda&#39;s voor het bedrijf in de formulierworkflow. (Zie Gebruikers en groepen [toewijzen aan een zakelijke kalender](configuring-business-calendars.md#mapping-users-and-groups-to-a-business-calendar).)

1. Definieer in de formulierwerkstroom een kalender voor elke set gebruikers die dezelfde niet-werkdagen delen. (Zie Een [agenda](configuring-business-calendars.md#create-or-update-a-business-calendar)maken of bijwerken.)
1. Wijs in de formulierwerkstroom de agenda- of groepslidmaatschappen voor elke kalender toe. (Zie Gebruikers en groepen [toewijzen aan een zakelijke kalender](configuring-business-calendars.md#mapping-users-and-groups-to-a-business-calendar).)
1. In Workbench kiest de ontwikkelaar of zakelijke kalenders moeten worden gebruikt voor herinneringen, deadlines en escalaties. (Zie [Workbench Help](https://www.adobe.com/go/learn_aemforms_workbench_63).)

   Als de procesontwikkelaar verkiest om bedrijfskalenders te gebruiken, zullen de vormen AEM dynamisch de aangewezen bedrijfskalender selecteren die op het Beheer van de Gebruiker wordt gebaseerd en de bedrijfskalendertoewijzingen die in de Console van het Beleid worden bepaald, of, als geen afbeeldingen bestaan, de standaardkalender zullen gebruiken.

   Als de procesontwikkelaar geen bedrijfskalenders gebruikt, behandelt de datumberekening voor de gebeurtenis elke dag als een bedrijfsdag. Een taakdeadline is bijvoorbeeld ingesteld op drie dagen nadat de taak aan een gebruiker is toegewezen. De taak wordt op donderdag toegewezen. De deadline van de taak komt op zondag voor, ook al is het een weekend.

## Een zakelijke kalender maken of bijwerken {#create-or-update-a-business-calendar}

Als uw organisatie verschillende reeksen gebruikers bevat die verschillende niet-bedrijfsdagen hebben, kunt u veelvoudige bedrijfskalenders bepalen. U kunt ook bestaande kalenders wijzigen, inclusief de standaard ingebouwde kalender die bij AEM-formulieren wordt geleverd.

>[!NOTE]
>
>Als u geen nieuwe bedrijfskalender creeert, dan zal de standaardkalender worden gebruikt.

1. Klik in de beheerconsole op Services > Forms workflow > Business Calendars.
1. Om een nieuwe bedrijfskalender toe te voegen, klik ![bus_cal_plus](assets/bus_cal_plus.png). De tekst *Nieuw Kalender* verschijnt in de drop-down lijst. Selecteer de tekst en typ een andere naam voor de kalender.

   Als u een bestaande agenda wilt bewerken, selecteert u deze in de vervolgkeuzelijst.

1. Selecteer onder Standaard niet-werkdagen elke weekdag, zoals weekends.
1. [Optioneel] Selecteer Business Hours gebruiken en geef de begin- en eindtijd voor de werkdagen op.

   Als u deze optie selecteert, wordt een gebeurtenis die vóór de gespecificeerde tijdwaaier voorkomt verplaatst naar het begin van de tijdwaaier, en een gebeurtenis die voorkomt nadat de tijdwaaier wordt verplaatst naar de begintijd van de volgende werkdag.

   Neem bijvoorbeeld een situatie waarin een gebruiker een taak krijgt toegewezen om 2:00 uur &#39;s middags op een dinsdag en de herinnering voor die taak is ingesteld op twee werkdagen. Zonder kantooruren zou de herinnering om 2:00 uur op donderdag plaatsvinden. Als de kantooruren op 8:00 tot 17:00 uur worden geplaatst, zou de herinnering op donderdag worden verschoven naar 8:00 uur. Zonder kantooruren, als een herinneringsgebeurtenis om 18.00 uur op Dinsdag werd gecreeerd, zou de herinnering na kantooruren op Donderdag voorkomen. Als de kantooruren op 8:00 tot 17:00 worden geplaatst, zou de herinnering om 8:00 uur op vrijdag plaatsvinden.

1. Dubbelklik in de kalender aan de linkerkant op andere niet-werkdagen, zoals feestdagen. Je kunt geen dagen in het verleden selecteren. De niet-werkdagen die u selecteert, worden weergegeven in een lijst aan de rechterkant, waarbij de datum twee keer op één regel wordt weergegeven. Selecteer links de datum waarop u een naam of beschrijving voor de niet-werkdag wilt typen.

   Als u een niet-werkdag uit de lijst wilt verwijderen, klikt u naast de dag op ![bus_cal_prullenbak](assets/bus_cal_trash.png) .

1. [Optioneel] Als deze kalender de standaardkalender moet zijn, selecteert u Standaardkalender. De standaardkalender wordt gebruikt wanneer geen andere kalenderafbeelding voor gebruiker-bijbehorende gebeurtenissen bestaat of geen bedrijfskalender voor de Gebeurtenis van de Tijdopnemer of de Wacht Dienst wordt gespecificeerd. U kunt de standaardkalender niet verwijderen.
1. Wanneer u klaar bent met het definiëren van de niet-werkdagen, selecteert u Kalender ingeschakeld om deze actief te maken en klikt u op Opslaan.

   Als u een bestaande kalender bijwerkt, wordt de nieuwe versie onmiddellijk van kracht en gebruikt voor alle bedrijfskalenderberekeningen, met inbegrip van taken die reeds lopen.

   >[!NOTE]
   >
   >Als u de kalender niet inschakelt, wordt de standaardkalender gebruikt.

## Gebruikers en groepen toewijzen aan een zakelijke kalender {#mapping-users-and-groups-to-a-business-calendar}

Er zijn twee methodes die u kunt gebruiken om een bedrijfskalender met een gebruiker te associëren. U kunt zakelijke kalenders toewijzen aan gebruikers op basis van een zakelijke kalendersleutel of op basis van de directorygroep waartoe de gebruiker behoort. U gebruikt het lusje van de Afbeelding om de methode te specificeren die de vormen AEM zullen gebruiken, en ook om de sleutels en de groepen van de bedrijfskalender aan bedrijfscalendars in kaart te brengen. Voor details bij het associëren van de sleutels van de bedrijfkalender met gebruikers, zie [Vestiging veelvoudige bedrijfscalendars](configuring-business-calendars.md#setting-up-multiple-business-calendars).

### Zakelijke kalenders koppelen aan gebruikers op basis van zakelijke kalendersleutels {#associate-business-calendars-with-users-based-on-business-calendar-keys}

1. Klik in de beheerconsole op Services > Formulierwerkstroom > Zakelijke kalenders en klik vervolgens op het tabblad Toewijzing.
1. Kies in de lijst Gebruikt systeem de optie Sleutelresolutie van de Business Calendar-service van User Manager.
1. Selecteer Bedrijfs van de Kalender van de Manager van de Vertoning Sleutel. Er wordt een lijst weergegeven met een unieke set agenda-sleutels voor het bedrijf die zijn gedefinieerd in Gebruikersbeheer.

   Voor lokale en hybride domeinen, toont de lijst de waarden ingegaan in het Belangrijkste gebied van de Kalender van de Zaken in Gebruikersbeheer. Voor bedrijfsdomeinen (LDAP) geeft de lijst de unieke set weer die wordt geretourneerd vanuit het LDAP-veld (bijvoorbeeld &quot;land&quot;) dat is geconfigureerd in de LDAP-domeininstellingen.

   Als de beheerder van het Beheer van de Gebruiker geen bedrijfskalendersleutels heeft bepaald, zal de lijst leeg zijn.

1. Selecteer een kalender voor elk item in de hoofdlijst UM Business Calendar.
1. Klik op Opslaan.

### Zakelijke kalenders koppelen aan gebruikers en groepen op basis van directoryservicegroepen {#associate-business-calendars-with-users-and-groups-based-on-directory-service-groups}

1. Klik in de beheerconsole op Services > Formulierwerkstroom > Zakelijke kalenders en klik vervolgens op het tabblad Toewijzing.
1. InSystem gebruikt de lijst, uitgezochte Groepen die door de Server van de Folder worden bepaald.
1. Selecteer op het tabblad Toewijzing de optie Groepen van directoryservice weergeven. Er wordt een lijst weergegeven met de groepen die zijn gedefinieerd in Gebruikersbeheer. (Zie [Directoryinstellingen](/help/forms/using/admin-help/configuring-directories.md#directory-settings).)

   >[!NOTE]
   >
   >In Workbench, als u de dienst van de Gebruiker hebt gevormd om bedrijfskalenders te gebruiken en de dienst wordt toegewezen aan een groep, gebruiken de vormen AEM de hier gespecificeerde groepstoewijzingen om de kalender voor de groep op te lossen. In AEM-formulieren worden altijd groepstoewijzingen gebruikt om de kalender voor groepen op te lossen, zelfs wanneer u kalender-sleutels gebruikt om de kalender voor gebruikers op te lossen. Als er geen groepstoewijzing wordt gevonden, wordt de standaardagenda voor het bedrijf gebruikt.

1. Voor elk punt in de lijst van de Groep van de Dienst van de Folder, selecteer een Kalender.
1. Klik op Opslaan.

## Zakelijke kalenders exporteren en importeren {#exporting-and-importing-business-calendars}

Met AEM-formulieren kunt u uw bedrijfsplannen exporteren en importeren als XML-bestanden. Met deze functie kunt u kalenders van een testsysteem naar een productiesysteem verplaatsen.

>[!NOTE]
>
>Met deze functie worden alle gedefinieerde bedrijfscalenders geëxporteerd en geïmporteerd, inclusief de standaardagenda voor bedrijven die door AEM-formulieren wordt verschaft. Een geïmporteerde agenda voor bedrijven met dezelfde naam als een bestaande kalender overschrijft de bestaande kalender.

### Zakelijke kalenders exporteren {#export-business-calendars}

1. Klik in de beheerconsole op Services > Formulierworkflow > Business Calendars.
1. Klik op Exporteren en sla het XML-bestand op.

### Zakelijke kalenders importeren {#import-business-calendars}

1. Klik in de beheerconsole op Services > Formulierworkflow > Business Calendars.
1. Klik op Importeren.
1. Selecteer het XML-bestand met de geëxporteerde zakelijke kalenders en klik op Openen.

## Een agenda voor een bedrijf verwijderen {#delete-a-business-calendar}

U kunt bedrijfsplannen verwijderen die uw organisatie niet meer nodig heeft. Als u een bedrijfskalender schrapt die nog aan gebruikers en groepen in kaart wordt gebracht, zal de standaardkalender worden gebruikt.

1. Klik in de beheerconsole op Services > Forms workflow > Business Calendars.
1. Selecteer de kalender.
1. Klik op Verwijderen.

