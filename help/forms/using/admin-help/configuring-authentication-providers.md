---
title: Verificatieproviders configureren
description: Voeg, geef, of schrap authentificatieleveranciers uit, verander authentificatiemontages, en lees over just-in-time levering van gebruikers.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/setting_up_and_managing_domains
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: d72a3977-1423-49e0-899b-234bb76be378
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: e821be5233fd5f6688507096790d219d25903892
workflow-type: tm+mt
source-wordcount: '1580'
ht-degree: 0%

---

# Verificatieproviders configureren {#configuring-authentication-providers}

Voor hybride domeinen is minstens één verificatieprovider vereist en voor ondernemingsdomeinen is minstens één verificatieprovider of directoryprovider vereist.

Als u SSO gebruikend SPNEGO toelaat, voeg een Kerberos authentificatieleverancier met toegelaten SPNEGO en een leverancier LDAP als steun toe. Deze configuratie laat gebruikersauthentificatie met een gebruiker toe - identiteitskaart en wachtwoord als SPNEGO niet werkt. (Zie [ SSO toelaten gebruikend SPNEGO ](/help/forms/using/admin-help/enabling-single-sign-on-aem.md#enable-sso-using-spnego).)

## Een verificatieprovider toevoegen {#add-an-authentication-provider}

1. Klik in de beheerconsole op Instellingen > Gebruikersbeheer > Domeinbeheer.
1. Klik op een bestaand domein in de lijst. Als u authentificatie voor een nieuw domein toevoegt, zie [ een ondernemingsdomein ](/help/forms/using/admin-help/adding-domains.md#add-an-enterprise-domain) toevoegen of [ een hybride domein ](/help/forms/using/admin-help/adding-domains.md#add-a-hybrid-domain) toevoegen.
1. Klik op Verificatie toevoegen en selecteer in de lijst Verificatieprovider een provider, afhankelijk van het verificatiemechanisme dat uw organisatie gebruikt.
1. Geef aanvullende informatie op die op de pagina vereist is. (Zie [ montages van de Authentificatie ](configuring-authentication-providers.md#authentication-settings).)
1. (Optioneel) Klik op Testen om de configuratie te testen.
1. Klik op OK en vervolgens nogmaals op OK.

## Een bestaande verificatieprovider bewerken {#edit-an-existing-authentication-provider}

1. Klik in de beheerconsole op Instellingen > Gebruikersbeheer > Domeinbeheer.
1. Klik op het desbetreffende domein in de lijst.
1. Selecteer op de pagina die wordt weergegeven de juiste verificatieprovider in de lijst en breng de gewenste wijzigingen aan. (Zie [ montages van de Authentificatie ](configuring-authentication-providers.md#authentication-settings).)
1. Klik op OK.

## Een verificatieprovider verwijderen {#delete-an-authentication-provider}

1. Klik in de beheerconsole op Instellingen > Gebruikersbeheer > Domeinbeheer.
1. Klik op het desbetreffende domein in de lijst.
1. Schakel de selectievakjes voor de te verwijderen verificatieproviders in en klik op Verwijderen.
1. Klik op OK op de bevestigingspagina die wordt weergegeven en klik nogmaals op OK.

## Verificatieinstellingen {#authentication-settings}

De volgende instellingen zijn beschikbaar, afhankelijk van het type domein en het type verificatie dat u hebt gekozen.

### LDAP-instellingen {#ldap-settings}

Als u verificatie configureert voor een onderneming of een hybride domein en LDAP-verificatie selecteert, kunt u de in uw directoryconfiguratie opgegeven LDAP-server gebruiken of een andere LDAP-server kiezen die u voor verificatie wilt gebruiken. Als u een andere server kiest, moeten uw gebruikers op beide LDAP-servers bestaan.

Als u de LDAP-server wilt gebruiken die in uw directoryconfiguratie is opgegeven, selecteert u LDAP als de verificatieprovider en klikt u op OK.

Als u een andere LDAP-server wilt gebruiken om verificatie uit te voeren, selecteert u LDAP als de verificatieprovider en schakelt u het selectievakje Aangepaste LDAP-verificatie in. De volgende configuratie-instellingen worden weergegeven.

**Server:** (Verplicht) volledig - gekwalificeerde domeinnaam (FQDN) van de folderserver. Voor een computer die x heet in het netwerk example.com, is de FQDN bijvoorbeeld x.example.com. Een IP-adres kan worden gebruikt in plaats van de FQDN-servernaam.

**Haven:** (Verplicht) de haven de folderserver gebruikt. Typisch 389, of 636 als het Veilige protocol van de Laag van Contactdozen (SSL) wordt gebruikt voor het verzenden van authentificatieinformatie over het netwerk.

**SSL:** (Verplicht) specificeert of de folderserver SSL gebruikt wanneer het verzenden van gegevens over het netwerk. De standaardwaarde is Nee. Als u Ja instelt, moet het bijbehorende LDAP-servercertificaat worden vertrouwd door de JRE (Java™ runtime environment) van de toepassingsserver.

**Bindend** (Verplicht) specificeert hoe te om tot de folder toegang te hebben.

**Anoniem:** Geen gebruikersnaam of wachtwoord wordt vereist.

**Gebruiker:** de Authentificatie wordt vereist. Geef in het vak Naam de naam op van de gebruikersrecord die toegang kan krijgen tot de map. U kunt het beste de volledige DN (Distinguished Name) van de gebruikersaccount invoeren, zoals cn=Jane Doe, ou=user, dc=can, dc=com. Geef in het vak Wachtwoord het bijbehorende wachtwoord op. Deze instellingen zijn vereist wanneer u Gebruiker selecteert als de optie Binding.

**wint Basis DNs terug:** (Niet verplicht) wint basis DNs terug en toont hen in de drop-down lijst. Deze instelling is handig wanneer u meerdere basis-DN&#39;s hebt en een waarde moet selecteren.

**Basis DN:** (Verplicht) Gebruikt als uitgangspunt voor het synchroniseren van gebruikers en groepen van de hiërarchie LDAP. Het is best om een basis DN op het laagste niveau van de hiërarchie te specificeren die alle gebruikers en groepen omvat die voor de diensten moeten worden gesynchroniseerd. Neem de DN van de gebruiker niet op in deze instelling. Gebruik de instelling Zoekfilter om een bepaalde gebruiker te synchroniseren.

**bevolkt pagina met:** (Niet verplicht) wanneer geselecteerd, bevolkt attributen op de de montagespagina&#39;s van de Gebruiker en van de Groep met overeenkomstige standaardLDAP waarden.

**de Filter van het Onderzoek:** (Verplicht) de onderzoeksfilter om het verslag te gebruiken te vinden dat met de gebruiker wordt geassocieerd. Zie Syntaxis zoekfilter.

### Kerberos-instellingen {#kerberos-settings}

Als u authentificatie voor een onderneming of een hybride domein vormt en authentificatie Kerberos selecteert, zijn de volgende montages beschikbaar.

**DNS IP:** het DNS IP adres van de server waar de AEM vormen lopen. Op Vensters, kunt u dit IP adres bepalen door ipconfig /all bij de bevellijn in werking te stellen.

**KDC Gastheer:** volledig - gekwalificeerde gastheernaam of IP adres van de Actieve server van de Folder die voor authentificatie wordt gebruikt.

**Gebruiker van de Dienst:** als u Actieve Folder 2003 gebruikt, is deze waarde de afbeelding die voor het de diensthoofd in de vorm `HTTP/<server name>` wordt gecreeerd. Als u Actieve Folder 2008 gebruikt, is deze waarde login identiteitskaart van het de diensthoofd. Bijvoorbeeld, veronderstel dat het de diensthoofd wordt genoemd um spnego, gebruiker - identiteitskaart is spnegodemo, en de afbeelding is HTTP/example.yourcompany.com. Met Actieve Folder 2003, plaatst u de Gebruiker van de Dienst aan HTTP/example.yourcompany.com. Met Actieve Folder 2008, plaatst u de Gebruiker van de Dienst aan spnegodemo. (Zie SSO inschakelen met SPNEGO.)

**Realm van de Dienst:** Naam van het Domein voor Actieve Folder

**Wachtwoord van de Dienst:** het wachtwoord van de gebruiker van de Dienst

**laat SPNEGO toe:** laat het gebruik van SPNEGO voor enig teken-op (SSO) toe. (Zie SSO inschakelen met SPNEGO.)

### SAML-instellingen {#saml-settings}

Als u authentificatie voor een onderneming of een hybride domein vormt en authentificatie van SAML selecteert, zijn de volgende montages beschikbaar. Voor informatie over extra montages SAML, zie [ de dienstleveranciersmontages van SAML ](/help/forms/using/admin-help/configure-saml-service-provider-settings.md#configure-saml-service-provider-settings) vormen.

**Selecteer een SAML-identiteitsprovider-metagegevens
te importeren bestand:** klik op Bladeren om een metagegevensbestand voor een SAML-identiteitsprovider te selecteren dat is gegenereerd van uw IDP en klik vervolgens op Importeren. De details van IDP worden getoond.

**Titel:** alias aan URL die door EntityID wordt vermeld. De titel wordt ook weergegeven op de aanmeldingspagina voor ondernemingen en lokale gebruikers.

**Identiteitsprovider steunt de BasisAuthentificatie van de Cliënt:** De BasisAuthentificatie van de Cliënt wordt gebruikt wanneer IDP een profiel van de Resolutie van het Artefact van SAML gebruikt. In dit profiel, verbindt het Beheer van de Gebruiker terug met de Webdienst die bij IDP loopt om de daadwerkelijke bevestiging van SAML terug te winnen. IDP kan authentificatie vereisen. Als de IDP authentificatie vereist, selecteer deze optie en specificeer een gebruikersnaam en een wachtwoord in de vakjes verstrekt.

**Eigenschappen van de Douane:** laat u toe om extra eigenschappen te specificeren. De extra eigenschappen zijn name=value paren die door nieuwe lijnen worden gescheiden.

De volgende aangepaste eigenschappen zijn vereist als artefactbinding wordt gebruikt.

* Voeg het volgende douanebezit toe om een gebruikersbenaming te specificeren die de AEM vormen Service Provider vertegenwoordigt, die wordt gebruikt om aan de dienst van de Resolutie van het Artefact IDP voor authentiek te verklaren.
  `saml.idp.resolve.username=<username>`

* Voeg de volgende aangepaste eigenschap toe om het wachtwoord op te geven voor de gebruiker die is opgegeven in `saml.idp.resolve.username` .
  `saml.idp.resolve.password=<password>`

* Voeg de volgende aangepaste eigenschap toe zodat de serviceprovider de certificaatvalidatie kan negeren terwijl de verbinding met de Artefactresolutie via SSL tot stand wordt gebracht.
  `saml.idp.resolve.ignorecert=true`

### Aangepaste instellingen {#custom-settings}

Als u authentificatie voor een onderneming of een hybride domein vormt en de uitgezochte authentificatie van de Douane selecteert, selecteer de naam van de leverancier van de douaneauthentificatie.

## Just-in-Time provisioning van gebruikers {#just-in-time-provisioning-of-users}

De just-in-time levering leidt automatisch tot een gebruiker in het gegevensbestand van het Beheer van de Gebruiker nadat de gebruiker door middel van een authentificatieleverancier met succes voor authentiek wordt verklaard. Relevante rollen en groepen worden ook dynamisch toegewezen aan de nieuwe gebruiker. U kunt just-in-time levering voor onderneming en hybride domeinen toelaten.

Deze procedure beschrijft de manier de traditionele authentificatie in AEM vormen werkt:

1. Wanneer een gebruiker zich aanmeldt bij AEM formulieren, geeft Gebruikersbeheer zijn gegevens opeenvolgend door aan alle beschikbare verificatieproviders. (De login geloofsbrieven omvatten gebruikersbenaming/wachtwoordcombinatie, kaartje Kerberos, handtekening PKCS7, etc.)
1. De verificatieprovider valideert de referenties.
1. De authentificatieleverancier controleert dan of de gebruiker in het gegevensbestand van het Beheer van de Gebruiker bestaat. De volgende statussen zijn mogelijk:

   **bestaat** als de gebruiker huidig en ontgrendeld is, keert het Beheer van de Gebruiker authentificatiesucces terug. Als de gebruiker echter niet actief is of is vergrendeld, retourneert het Gebruikersbeheer een verificatiefout.

   **bestaat niet** de terugkeringsmislukking van het Beheer van de Gebruiker.

   **Ongeldige** de terugkeringsmislukking van het Beheer van de Gebruiker.

1. Het resultaat dat door de authentificatieleverancier is teruggekeerd wordt geëvalueerd. Als de verificatieprovider het succes van de verificatie heeft geretourneerd, mag de gebruiker zich aanmelden. Anders, controleert het Beheer van de Gebruiker met de volgende authentificatieleverancier (stappen 2-3).
1. Verificatiefout wordt geretourneerd als geen enkele verificatieprovider de gebruikersgegevens valideert.

Wanneer just-in-time levering wordt toegelaten, worden de nieuwe gebruikers dynamisch gecreeerd in het Beheer van de Gebruiker als één van de authentificatieleveranciers hun geloofsbrieven bevestigt. (Na stap 3 van de bovenstaande procedure.)

Zonder just-in-time levering, wanneer een gebruiker met succes voor authentiek wordt verklaard maar niet in het gegevensbestand van het Beheer van de Gebruiker wordt gevonden, ontbreekt de authentificatie. De just-in-time levering voegt een stap in de authentificatieprocedure toe om de gebruiker tot stand te brengen en rollen en groepen aan de gebruiker toe te wijzen.

### Eenmalige provisioning voor een domein inschakelen {#enable-just-in-time-provisioning-for-a-domain}

1. Schrijf een de dienstcontainer die de interfaces IdentityCreator en AssignmentProvider uitvoert. (Zie [ Programmering met AEM vormen ](https://www.adobe.com/go/learn_aemforms_programming_63).)
1. Implementeer de servicecontainer op de Forms-server.
1. Klik in de beheerconsole op Instellingen > Gebruikersbeheer > Domeinbeheer.

   Selecteer een bestaand domein of klik op Nieuw Enterprise-domein.

1. Als u een domein wilt maken, klikt u op Nieuw Enterprise-domein of Nieuw hybride domein. Als u een bestaand domein wilt bewerken, klikt u op de naam van het domein.
1. Selecteer Enable Just In Time Provisioning.

   ***nota **: Als Enable enkel in checkbox van de Levering van de Tijd mist, klik Huis > Montages > de Configuratie van het Beheer van de Gebruiker > de Geavanceerde Attributen van het Systeem en klik dan opnieuw laden.*

1. Voeg verificatieproviders toe. Tijdens het toevoegen van authentificatieleveranciers, op het Nieuwe scherm van de Authentificatie, selecteer een geregistreerde Maker van de Identiteit en een Leverancier van de Toewijzing. (Zie [ het Vormen authentificatieleveranciers ](configuring-authentication-providers.md#configuring-authentication-providers).)
1. Sla het domein op.
