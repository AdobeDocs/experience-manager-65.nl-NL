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
feature: Adaptive Forms
source-git-commit: 6a9806d8f40f711a610c130c63d9ab9b2460d075
workflow-type: tm+mt
source-wordcount: '2495'
ht-degree: 0%

---

# Rollen maken en configureren{#creating-and-configuring-roles}

Gebruikend de Web-pagina&#39;s van het Beheer van de Gebruiker, kunt u gebruikers en groepen met rollen associëren die reeds deel van het gegevensbestand van het Beheer van de Gebruiker uitmaken. U kunt ook rollen maken, bewerken en verwijderen.

Gebruikersbeheer heeft twee soorten rollen:

**Mutable rollen:** Dit type van rol kan worden uitgegeven en worden geschrapt, en de roltoestemmingen kunnen van deze roltypes worden toegevoegd en worden geschrapt. Elke rol die u maakt, wordt beschouwd als een veranderlijke rol. U kunt gebruikers en groepen toevoegen of verwijderen die aan veranderlijke rollen worden toegewezen.

**Immuable rollen:** De standaardrollen die met het Beheer van de Gebruiker inbegrepen zijn zijn onveranderlijke rollen. Deze rollen kunnen niet worden bewerkt of verwijderd. U kunt echter gebruikers en groepen toevoegen of verwijderen die aan onveranderlijke rollen zijn toegewezen.

Zowel veranderlijke als onveranderlijke rollen kunnen ook door de AEM vormen APIs worden gecreeerd.

## Standaardrollen {#default-roles}

De volgende standaardrollen zijn inbegrepen in het gegevensbestand van het Beheer van de Gebruiker.

**gebruiker van de beleidsconsole:** kan tot beleidsconsole toegang hebben.

**Beheerder van de Toepassing:** kan alle eigenschappen gebruiken Workbench. Kan de pagina&#39;s van Toepassingen en van de Diensten in beleidsconsole gebruiken om de eigenschappen van de de dienstruntime, eindpunten, en veiligheid te vormen.

**AEM vormBeheerder:** kan alle taken voor alle geïnstalleerde diensten uitvoeren.

**Beheerder van de Veiligheid:** controleert de montages van het Beheer van de Gebruiker, en beheert gebruikers en groepen die met om het even welk domein van de Manager van de Gebruiker worden geassocieerd

**Gebruiker van de Diensten:** kan de dienst bekijken en aanhalen

**Beheerder van de Leverancier:** heeft toegang tot alle administratieve functionaliteit in het systeem, met inbegrip van de diensten

**Beheerder van het Vertrouwen:** kan de PKI vertrouwensmontages en geloofsbrieven beheren PKI die van de pagina van het Beheer van de Opslag van het Vertrouwen in beleidsconsole worden beheerd

### Aanvullende standaardrollen {#additional-default-roles}

De volgende aanvullende standaardrollen kunnen worden opgenomen, afhankelijk van de AEM formuliercomponenten die u hebt geïnstalleerd

**Document uploadt de Gebruiker van de Toepassing:** kan documenten uploaden gebruikend Flex Remoting.

**Beheerder van Forms:** kan montages van de pagina van Forms in de Console van het Beleid bekijken en wijzigen

**AEM de Beheerder van de Formulierruimte:** kan montages van de (Vervangen) pagina van de Diensten van de Inhoud in beleidsconsole bekijken en wijzigen

**AEM de Gebruiker van de inhoudsruimte van vormen:** kan login aan de (Vervangen) Inhoudsruimte Web-pagina&#39;s

**Documentum Connector Administrator:** Kan instellingen van de Connector voor EMC Documentum pagina bekijken en wijzigen in beheerconsole

**AEM de Beheerder van de Schakelaar van het DossierNet van vormen:** kan montages van de Schakelaar voor de pagina van IBM FileNet in beleidsconsole bekijken en wijzigen

**AEM formulieren IBM CM Connector Administrator:** Kan instellingen van de Connector voor IBM Content Manager-pagina weergeven en wijzigen in beheerconsole

**Beheerder van het Rights Management:** voert alle taken uit die voor alle serverconfiguraties op de relevante pagina&#39;s van het Rights Management worden vereist

**EindGebruiker van het Rights Management:** kan tot de eindgebruikerWeb-pagina&#39;s van het Rights Management toegang hebben

**Rights Management nodigt Gebruiker uit:** kan gebruikers uitnodigen

**Rights Management beheert Uitgenodigde en Lokale Gebruikers:** kan taken uitvoeren die worden vereist om alle uitgenodigde en lokale gebruikers op de relevante pagina&#39;s van het Rights Management te beheren

**Vastgestelde Beheerder van het Beleid van het Rights Management:** voert alle taken uit die voor alle beleidsreeksen op de relevante pagina&#39;s van het Rights Management worden vereist

**Rights Management Super Beheerder:** voert alle taken uit die van de pagina van het Rights Management worden vereist

**AEM vormen Workspace Beheerder:** kan montages van de pagina van Workspace in de Console van het Beleid bekijken en wijzigen

***nota **: De Werkruimte van Flex wordt afgekeurd voor AEM vormenversie.*

**Gebruiker van Workspace:** kan login aan de eindgebruikertoepassing van Workspace

**Beheerder van de Output:** kan montages van de pagina van de Output in de Console van het Beleid bekijken en wijzigen

**Beheerder PDFG:** kan montages van de pagina van de PDF Generator in beleidsconsole bekijken en wijzigen

**Gebruiker PDFG:** kan tot alle niet-administratieve functionaliteit voor PDF Generator toegang hebben

**de Toepassing van het Web van uitbreidingen van Acrobat Reader DC:** kan de toepassing van het de uitbreidingenWeb van Acrobat Reader DC gebruiken

>[!NOTE]
>
>Gebruikers met bepaalde beheerdersrechten hebben uit veiligheidsoverwegingen geen toegang tot de Workspace-webpagina&#39;s voor eindgebruikers. Omdat deze pagina&#39;s buiten een firewall kunnen bestaan, zou het toestaan van beleid-vlakke taken een veiligheidsrisico kunnen vormen. Alleen gebruikers die beschikken over de AEM Workspace Administrator of AEM formulieren van Workspace User hebben toegang tot de Workspace-webpagina&#39;s voor eindgebruikers.

>[!NOTE]
>
>De Flex-werkruimte is verouderd voor AEM formulierrelease.

## Een rol maken {#create-a-role}

>[!NOTE]
> 
> Zorg ervoor dat de gebruiker beheerdersrechten heeft om toegang te krijgen tot de beheerdersconsole.

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

**ADD_REMOVE_ENDPOINT_PERM:** voeg, verwijder, en wijzig eindpunten voor de dienst toe

**Login van de Admin Console:** Bekijk de beleidsconsole

**Certificaat wijzigt:** wijzig de vertrouwensmontages van om het even welk certificaat in het Opslag van het Vertrouwen

**Gelezen Certificaat:** las om het even welk certificaat in de Opslag van het Vertrouwen

**Certificaat schrijft:** voeg een certificaat aan de Opslag van het Vertrouwen toe

**Component voegt toe:** installeer een nieuwe component in het systeem

**Schrapping van de Component:** schrap om het even welke component in het systeem

**Gelezen Component:** las om het even welke component in het systeem

**Beheerder van de Inhoudsruimte:** Toestemming voor (Vervangen) Beheerder Inhoudsruimte

**Login van de Console van de inhoudsruimte:** Toestemming voor (Vervangen) Login van de Console van de Console van de Inhoud

**Controle van de Montages van de Kern:** beheer de montages op de pagina van de Montages van het Systeem van de Kern in de Console van het Beleid

**CREATE_VERSION_PERM:** creeer een versie van de dienst

**Referentie wijzigt zich:** wijzig om het even welke ondertekenende referentie in de Opslag van het Vertrouwen

**Gelezen Referentie:** las om het even welke ondertekenende referentie in de Opslag van het Vertrouwen

**Credential schrijft:** voeg een ondertekenende referentie aan de Opslag van het Vertrouwen toe

**CRL wijzigt zich:** wijzig om het even welke CRL (de Lijst van de Intrekking van het Certificaat) in de Opslag van het Vertrouwen

**CRL Gelezen:** las om het even welke CRL in de Opslag van het Vertrouwen

**CRL schrijft:** voeg een CRL aan de Opslag van het Vertrouwen toe

**Afgevaardigde:** plaats ACL op een middel

**DELETE_VERSION_PERM:** schrap een versie van de dienst

**Document uploadt:** uploadt documenten in AEM vormen

**Controle van het Domein:** creeer, schrap, of wijzig montages voor om het even welk domein van het Beheer van de Gebruiker, met inbegrip van zijn authentificatie en folderleveranciers

**Het Type van Gebeurtenis geeft uit:** geeft aan gebeurtenistypen uit

**Controle van de Imitatie van de Identiteit:** imiteer identiteit in de Manager van de Gebruiker

**INVOKE_PERM:** Roep alle verrichtingen op de dienst aan

**LCDS ModelControle van Gegevens:** leest en stelt gegevensmodellen in de Diensten van Gegevens op

**Update van de Manager van de Vergunning:** Update van de vergunningsinformatie

**MODIFY_CONFIG_PERM:** wijzig de configuratie van de dienst

**TERM** wijzig de versie van de dienst

**PDFGAdminPermission:** beheerder PDFG

**PDFGUserPermission:** gebruiker PDFG

**PERM_DCTM_ADMIN:** Documentum Connector beheerder

**PERM_FILENET_ADMIN:** de beheerder van de Verbinding van FileNet

**PERM_FORMS_ADMIN:** beheerder van Forms

**PERM_IBMCM_ADMIN:** de Schakelaar van IBM CM

**PERM_OUTPUT_ADMIN:** beheerder van de Output

**PERM_READER_EXTENSIONS_WEB_APPLICATION:** Gebruik de de uitbreidingen van Acrobat Reader DC Webtoepassing

**PERM_SP_ADMIN:** beheer de montages van de Verbinding van SharePoint

**PERM_WORKSPACE_ADMIN:** beheer de montages van Workspace

**PERM_WORKSPACE_USER:** Login aan de eindgebruikertoepassing van Workspace

**Belangrijkste Controle:** beheer gebruikers en groepen voor om het even welk domein, en beheer roltaken voor alle gebruikers en groepen in om het even welk domein

**Opname van het Proces Gelezen/Schrapping:** Lijst en wint werkschemacontroleinstanties terug

**PROCESS_OWNER_PERM:** de trendgegevens van de mening en voert administratieve acties op de dienst uit die van een proces wordt gecreeerd

**gelezen:** las de inhoud van een middel

**READ_PERM:** las of bekijk de dienst

**Verlenging bewering:** vernieuw beweringen in het Beheer van de Gebruiker

**Afgevaardigde van de Bewaarplaats:** plaats ACL op een middel

**Gelezen Bewaarplaats:** las de inhoud van een middel

**Verkeer van de Bewaarplaats:** omvat een middel in een verzoek van lijstmiddelen of leest de meta-gegevens van een middel

**Repository schrijft:** schrijft bewaarplaats meta-gegevens en inhoud

**de Eigenaar van het Beleid van de Verandering van het Rights Management:** het beleidseigenaar van de Verandering

**Login van de Console van het Eind van het Eind van het Rights Management:** Login aan de gebruikersinterface van het Eind van het Rights Management

**Rights Management beheert Configuratie:** beheer serverconfiguratie

**Rights Management beheert Uitgenodigde en Lokale Gebruikers:** beheer uitgenodigde en lokale gebruikers

**Rights Management beheert de Reeksen van het Beleid:** beheer alle beleid en documenten binnen om het even welke beleidreeks

**Reeks van het Beleid van het Rights Management voegt Coördinator toe:** voeg, verwijder, en verander toestemmingen voor beleidsplaatste coördinatoren toe

**Reeks van het Beleid van het Rights Management leidt tot Beleid:** creeer een beleid voor een beleidsreeks

**Reeks van het Beleid van het Rights Management het Beleid van de Schrapping:** verwijdert een beleid uit een beleidsreeks

**Reeks van het Beleid van het Rights Management geeft Beleid uit:** geef een beleid in een beleidsreeks uit

**Reeks van het Beleid van de Rights Management leidt de Uitgever van het Document:** wanneer u beleidsreeksen creeert, wijst u gebruikers de rol van documentuitgever toe. De uitgever van het document is de gebruiker die het document met een beleid beschermt.

**Reeks van het Beleid van het Rights Management verwijdert Coördinator:** verwijdert een coördinator van de beleidsreeks uit een beleidsreeks

**Revoed Document van het Beleid van het Rights Management Revoke:** Revoe toegang tot documenten in een beleidsreeks

**Beleid van de Schakelaar van het Beleid van het Rights Management plaatste Beleid:** Het beleid van de Schakelaar voor een document

**geplaatst het Beleid van het Rights Management unrevoke Document:** trekt een document ongedaan

**de Gebeurtenis van de Mening van de Reeks van het Beleid van het Rights Management:** het beleid en documentgebeurtenissen van de Mening voor om het even welk beleid of document binnen een beleidsreeks

**de Gebeurtenissen van de Server van de Mening van het Rights Management:** Onderzoek en bekijk alle controlegebeurtenissen

**Controle van de Rol:** creeer, schrap, en wijzig rollen in het Beheer van de Gebruiker

**de Dienst activeert:** Begin om het even welke dienst, die het voor aanroeping ter beschikking stelt

**de Dienst voegt toe:** stelt een nieuwe dienst aan de de dienstregistratie op. Dit omvat het toevoegen van nieuwe processen en procesvarianten

**Deactivate van de Dienst:** Stop om het even welke dienst in het systeem

**Schrapping van de Dienst:** schrap om het even welke dienst in het systeem, met inbegrip van processen en procesvarianten

**Invoed van de Dienst:** Roep om het even welke dienst in de dienstregistratie beschikbaar bij runtime aan

**de Dienst wijzigt:** wijzigt de configuratieeigenschappen van om het even welke dienst in het systeem. Dit omvat het sluiten van en het ontgrendelen van de dienst in winde, en het toevoegen van of het verwijderen van eindpunten uit de dienst

**Gelezen de Dienst:** las om het even welke diensten in het systeem. Dit omvat alle processen en procesvarianten

**SERVICE_AGENT_PERM:** de gegevens van de Mening en interactie met procesinstanties voor de dienst die van een proces wordt gecreeerd

**SERVICE_MANAGER_PERM:** voer lading het in evenwicht brengen en andere administratieve acties op de dienst uit die van een proces wordt gecreeerd

**START_STOP_PERM:** Begin of stop de dienst

**SUPERVISOR_PERM:** de gegevens van de procesinstantie van de Mening voor de dienst die van een proces wordt gecreeerd

**Omkeren:** omvat een middel in een verzoek van lijstmiddelen of leest de meta-gegevens van een middel

**schrijft:** schrijft bewaarplaats meta-gegevens en inhoud

**Openend dossiers in Workbench**

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
