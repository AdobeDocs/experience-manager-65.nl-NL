---
title: Domeinen toevoegen
seo-title: Domeinen toevoegen
description: Leer hoe te om een onderneming, lokaal, of hybride domein toe te voegen gebruikend de montages van het Beheer van het Domein en algemene overwegingen voor domeinnamen en identiteitskaarts.
seo-description: Leer hoe te om een onderneming, lokaal, of hybride domein toe te voegen gebruikend de montages van het Beheer van het Domein en algemene overwegingen voor domeinnamen en identiteitskaarts.
uuid: 3ae1e5d4-ea5b-4e0b-be97-3957c3702d5f
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/setting_up_and_managing_domains
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: d4004ffe-c981-487d-b803-dc4492ae5998
translation-type: tm+mt
source-git-commit: d3719a9ce2fbb066f99445475af8e1f1e7476f4e

---


# Domeinen toevoegen {#adding-domains}

## Een ondernemingsdomein toevoegen {#add-an-enterprise-domain}

1. Klik in de beheerconsole op Instellingen > Gebruikersbeheer > Domeinbeheer.
1. Klik op Nieuw Enterprise-domein.
1. Typ in het vak Id een unieke id voor het domein en typ in het vak Naam een beschrijvende naam voor het domein. (Zie [Belangrijke overwegingen voor domeinnamen en id&#39;s](adding-domains.md#important-considerations-for-domain-names-and-ids).)
1. Geef op of accountvergrendeling moet worden ingeschakeld. (Zie [De instellingen](/help/forms/using/admin-help/configure-account-locking-settings.md#configure-account-locking-settings)voor het vergrendelen van accounts configureren.) Standaard is het selectievakje Account vergrendelen inschakelen ingeschakeld.
1. Klik op Verificatie toevoegen en selecteer in de lijst Verificatieprovider een provider, afhankelijk van het verificatiemechanisme dat uw organisatie gebruikt. Mogelijke waarden zijn LDAP, Kerberos, SAML, of een leverancier van de douaneauthentificatie.

   Als u LDAP selecteert, kunt u de in uw directoryconfiguratie opgegeven LDAP-server gebruiken of kunt u een andere LDAP-server kiezen die u voor verificatie wilt gebruiken. Als u een andere server kiest, moeten uw gebruikers op beide LDAP-servers bestaan.

1. Geef aanvullende informatie op die op de pagina vereist is. (Zie [Verificatie-instellingen](/help/forms/using/admin-help/configuring-authentication-providers.md#authentication-settings).)
1. Voeg een directory of een aangepaste Service Provider Interface (SPI) toe. (Zie [Mappen of aangepaste SPI&#39;s toevoegen](/help/forms/using/admin-help/configuring-directories.md#adding-directories-or-custom-spis).)
1. Klik op Voltooien en vervolgens op OK.

Na het creëren van een ondernemingsdomein, synchroniseer manueel de folder of creeer een trekker om een synchronisatie uit te voeren alvorens het Beheer van de Gebruiker het kan gebruiken. Vervolgens kunt u een schema voor directorysynchronisatie instellen en indien nodig handmatige synchronisatie uitvoeren. (Zie [Mappen](/help/forms/using/admin-help/synchronizing-directories.md#synchronizing-directories)synchroniseren.)

## Een lokaal domein toevoegen {#add-a-local-domain}

1. Klik in de beheerconsole op Instellingen > Gebruikersbeheer > Domeinbeheer.
1. Klik op Nieuw lokaal domein.
1. Typ in het vak Id een unieke id voor het domein en typ in het vak Naam een beschrijvende naam voor het domein. (Zie [Belangrijke overwegingen voor domeinnamen en id&#39;s](adding-domains.md#important-considerations-for-domain-names-and-ids).)
1. Geef op of u accountvergrendeling wilt inschakelen en klik op OK. (Zie [De instellingen](/help/forms/using/admin-help/configure-account-locking-settings.md#configure-account-locking-settings)voor het vergrendelen van accounts configureren.) Standaard is het selectievakje Account vergrendelen inschakelen ingeschakeld.

## Een hybride domein toevoegen {#add-a-hybrid-domain}

1. Klik in de beheerconsole op Instellingen > Gebruikersbeheer > Domeinbeheer.
1. Klik op Nieuw hybride domein.
1. Typ in het vak Id een unieke id voor het domein en typ in het vak Naam een beschrijvende naam voor het domein. (Zie [Belangrijke overwegingen voor domeinnamen en id&#39;s](adding-domains.md#important-considerations-for-domain-names-and-ids).)
1. Klik op Verificatie toevoegen en selecteer in de lijst Verificatieprovider een provider, afhankelijk van het verificatiemechanisme dat uw organisatie gebruikt. Mogelijke waarden zijn LDAP, Kerberos, SAML, of een leverancier van de douaneauthentificatie.
1. Geef aanvullende informatie op die op de pagina vereist is. (Zie [Verificatie-instellingen](/help/forms/using/admin-help/configuring-authentication-providers.md#authentication-settings).)
1. Klik op OK en vervolgens nogmaals op OK.

## Belangrijke overwegingen voor domeinnamen en id&#39;s {#important-considerations-for-domain-names-and-ids}

Houd rekening met het volgende wanneer u een domeinnaam en id kiest:

### Algemene overwegingen {#general-considerations}

* Als u een andere databaseprovider dan DB2 gebruikt, kan de domein-id maximaal 50 bytes bevatten. Als u ASCII-tekens van één byte gebruikt, is de limiet 50 tekens. Als de domein-id multibyte-tekens bevat, wordt deze limiet verlaagd. Als u bijvoorbeeld een domein maakt waarvan de id 3-byte tekens bevat, is de limiet 16 tekens. Bovendien kunt u geen domeinen maken die 4-byte tekens bevatten. Als u een domein-id maakt die deze limiet overschrijdt, zijn AEM-formulieren in een onstabiele status. Als u wilt herstellen van deze instabiele status, raadpleegt u &quot; [Een domein verwijderen dat uitgebreide of multibyte-tekens](adding-domains.md#remove-a-domain-that-contains-extended-or-multi-byte-characters)bevat&quot; op deze pagina.
* Het aantal ondernemingsdomeinen en lokale domeinen die binnen vormen kunnen worden tot stand gebracht AEM hangt van de lengte van elk van de domein IDs af. Wanneer u een onderneming of hybride domein toevoegt, werkt het Beheer van de Gebruiker het configInstance koord in de knoop AuthProviders van het AEM dossier van de vormenconfiguratie (config.xml) bij. De configInstance-tekenreeks bevat een door dubbele punten gescheiden lijst met de absolute paden van alle domeinen die aan de machtigingsprovider zijn gekoppeld. Deze tekenreeks mag niet groter zijn dan 8192 tekens. Wanneer deze limiet is bereikt, kunt u geen extra domeinen maken.

### Overwegingen bij het gebruik van DB2 {#considerations-when-using-db2}

Wanneer u DB2 gebruikt voor uw AEM-formulierdatabase, hangt de maximaal toegestane lengte van de domein-id af van het gebruikte type tekens:

* 100 single-byte (ASCII) (bijvoorbeeld tekens die worden gebruikt in het Engels, Frans of Duits)
* 50 double-byte (bijvoorbeeld tekens die worden gebruikt in Chinese, Japanse of Koreaanse talen)
* 25 vierbyte (bijvoorbeeld tekens die worden gebruikt in de taal Traditioneel Chinees)

### Overwegingen bij het gebruik van MySQL {#considerations-when-using-mysql}

Wanneer u MySQL gebruikt als uw AEM-formulierdatabase, gelden de volgende beperkingen:

* Gebruik alleen single-byte (ASCII)-tekens voor de domein-id en domeinnaam. Als u uitgebreide ASCII-tekens gebruikt, zijn AEM-formulieren niet stabiel en kan er een uitzondering optreden als u probeert het domein te verwijderen. Om van deze instabiele staat terug te krijgen, zie &quot; een domein [verwijderen dat uitgebreide of multi-byte karakters](adding-domains.md#remove-a-domain-that-contains-extended-or-multi-byte-characters)&quot;onderwerp op deze pagina bevat.
* U kunt geen twee domeinen tot stand brengen die de zelfde naam hebben maar in geval verschillen. Als u bijvoorbeeld een domein met de naam *Adobe* probeert te maken terwijl er al een domein met de naam *adobe* bestaat, treedt er een fout op.
* Gebruikersbeheer kan geen onderscheid maken tussen twee domeinnamen die alleen verschillen in het gebruik van uitgebreide tekens. Als u bijvoorbeeld een domein maakt met de naam *abcde* en een domein met de naam *âbcdè*, worden deze als hetzelfde beschouwd.

### Een domein verwijderen dat uitgebreide of multi-byte tekens bevat {#remove-a-domain-that-contains-extended-or-multi-byte-characters}

1. Exporteer het configuratiebestand, zoals beschreven in het configuratiebestand [](/help/forms/using/admin-help/importing-exporting-configuration-file.md#importing-and-exporting-the-configuration-file)importeren en exporteren.
1. Open het configuratiebestand en zoek onder het knooppunt Domains het knooppunt waarvan het naamkenmerk overeenkomt met de naam van het domein dat met uitgebreide tekens of multi-byte tekens is gemaakt. Verwijder het gehele knooppunt dat betrekking heeft op dat domein.
1. Zoek in uw database naar het domein in de PrincippaldomainInentity-tabel:

   * Selecteer `*` een optie in het veld Princippaldomainentiteit.
   * Zoek de domeinnaam die uitgebreide of multi-byte karakters bevat en plaats zijn status aan OBSOLETE.

1. Importeer het bijgewerkte configuratiebestand, zoals beschreven in het configuratiebestand [](/help/forms/using/admin-help/importing-exporting-configuration-file.md#importing-and-exporting-the-configuration-file)importeren en exporteren.

