---
title: 'Gebruikers toevoegen en configureren '
seo-title: 'Gebruikers toevoegen en configureren '
description: Met de instellingen voor gebruikersbeheer in de beheerconsole kunt u gebruikers maken of verwijderen en andere gebruikersinstellingen configureren.
seo-description: Met de instellingen voor gebruikersbeheer in de beheerconsole kunt u gebruikers maken of verwijderen en andere gebruikersinstellingen configureren.
uuid: fe650cdb-7d0d-4f38-9899-e5349559ed32
contentOwner: admin
geptopics: SG_AEMFORMS/categories/setting_up_and_organizing_users
discoiquuid: 20ca99e3-4843-4254-b3e9-0255cc752363
translation-type: tm+mt
source-git-commit: a929252a13f66da8ac3e52aea0655b12bdd1425f
workflow-type: tm+mt
source-wordcount: '1675'
ht-degree: 0%

---


# Gebruikers toevoegen en configureren {#adding-and-configuring-users}

Gebruiker- en groepsgegevens worden bijgehouden in een opslagsysteem van derden, zoals een LDAP-directory. Gebruikersbeheer schrijft niet naar het opslagsysteem van derden. In plaats daarvan synchroniseert Gebruikersbeheer de gebruikers- en groepsgegevens met een eigen database

## Een gebruiker maken {#create-a-user}

Wanneer u gebruikers creeert, kunt u hen aan groepen toevoegen en rollen toewijzen aan hen.

1. Klik in de beheerconsole **[!UICONTROL Settings > User Management > Users and Groups]** en klik op **[!UICONTROL New User]**.
.
1. Geef onder **[!UICONTROL General Settings]** desgewenst informatie op en klik op **[!UICONTROL Next]**. Zie [Gebruikersinstellingen](adding-configuring-users.md#user-settings)voor meer informatie over de instellingen.
1. (Optioneel) Als u de gebruiker aan een groep wilt toevoegen, klikt u op **[!UICONTROL Find Groups]** en voert u de volgende taken uit:

   * Typ in het **[!UICONTROL Find]** vak de naam van de groep geheel of gedeeltelijk.
   * Selecteer het domein waarnaar u wilt zoeken, selecteer het aantal items dat u wilt weergeven en klik op **[!UICONTROL Find]**.
   * (Optioneel) Als u groepdetails wilt weergeven, selecteert u de groepsnaam en klikt u op de pagina met zoekresultaten **[!UICONTROL OK]** om deze weer te geven.
   * Schakel het selectievakje voor de groep in en klik op **[!UICONTROL OK]**.
   * Klik op **[!UICONTROL Next]**.

1. (Optioneel) Als u rollen wilt toewijzen aan de gebruiker, klikt u op **[!UICONTROL Find Roles]** het selectievakje voor de rollen die u wilt toewijzen en klikt u op **[!UICONTROL OK]**.
1. Klik op **[!UICONTROL Finish]**.

   >[!NOTE]
   >
   >Als er een aanmeldingsprobleem optreedt met de gebruiker, raadpleegt u [AEM Forms on JEE user failed to login on AEM Forms on OSGi side](https://helpx.adobe.com/aem-forms/kb/AEM-users-fails-to-login.html).

## Gebruikersinstellingen {#user-settings}

Geef de volgende instellingen op wanneer u een gebruiker maakt of bewerkt.

**Canonieke naam:** (Verplicht) Unieke identificatiecode voor de gebruiker. Elke gebruiker en groep in een domein moet een unieke canonieke naam hebben. Schakel het selectievakje Door systeem gegenereerd in als u wilt dat gebruikersbeheer een unieke waarde toewijst of schakel het selectievakje uit en geef een aangepaste waarde op voor Canonical Name.

Gebruik bijvoorbeeld geen onderstrepingstekens (_) in canonieke namen `sample_user`. Wanneer u naar gebruikers zoekt op basis van hun canonieke naam, worden de gebruikers met onderstrepingstekens niet geretourneerd.

**Voornaam:** (Verplicht) Gebruikersnaam

**Achternaam:** (Verplicht) Familienaam van de gebruiker

**Algemene naam:** Volledige naam of weergavenaam voor de gebruiker. Bijvoorbeeld, als Voornaam = Gloria en Achternaam = Rios, dan Gemeenschappelijke Naam = Gloria Rios.

**E-mail:** E-mailadres van gebruiker

**Telefoon:** Telefoonnummer van gebruiker

**Omschrijving:** Optionele beschrijving. U kunt dit veld gebruiken in overeenstemming met de behoeften van uw organisatie.

**Adres:** E-mailadres van gebruiker

**Organisatie:** Organisatie waartoe de gebruiker behoort

**E-mailaliassen:** E-mailaliassen van de gebruiker. Scheid de e-mailaliassen met komma&#39;s.

**Domein:** Domein waartoe de gebruiker behoort

**Landinstelling:** Landinstelling ISO van gebruiker

**Sleutel zakelijke agenda:** Laat u toe om een bedrijfskalender aan een gebruiker in kaart te brengen, die op de waarde voor dit het plaatsen wordt gebaseerd. Zakelijke kalenders definiëren zakelijke en niet-zakelijke dagen. AEM formulieren kunnen zakelijke kalenders gebruiken voor het berekenen van toekomstige datums en tijden voor gebeurtenissen zoals herinneringen, deadlines en escalaties. De manier waarop u zakelijke kalendersleutels toewijst aan gebruikers hangt af van of u een onderneming, lokaal, of hybride domein gebruikt. (Zie [Domeinen](/help/forms/using/admin-help/adding-domains.md#adding-domains)toevoegen.)

Als u een lokaal of hybride domein gebruikt, wordt de informatie over gebruikers opgeslagen slechts in het gegevensbestand van het Beheer van de Gebruiker. Stel voor deze gebruikers de Business Calendar Key in op een tekenreeks. Wijs vervolgens de agenda-key van het bedrijf (de tekenreeks) toe aan een zakelijke kalender in de formulierworkflow.

Als u een ondernemingsdomein gebruikt, verblijft de informatie over gebruikers in een derdesopslagsysteem, zoals een folder LDAP. Het Beheer van de gebruiker synchroniseert gebruikersinformatie van de folder met het gegevensbestand van het Beheer van de Gebruiker. Met deze functie kunt u een agenda-toets toewijzen aan een veld in de LDAP-directory. Neem bijvoorbeeld een scenario waarin elk gebruikersrecord in uw map een landveld bevat en u bedrijfsplannen wilt toewijzen op basis van het land waar de gebruiker zich bevindt. In dit geval geeft u de naam van het landveld op als de waarde voor de instelling Key Business Calendar. Vervolgens kunt u de agenda-sleutels voor het bedrijf (de waarden die zijn gedefinieerd voor het landveld in de LDAP-lijst) toewijzen aan de agenda&#39;s voor het bedrijf in de formulierworkflow.

Voor extra informatie over bedrijfscalendars, met inbegrip van hoe te om bedrijfskalendersleutels aan bedrijfscalendars in kaart te brengen, zie het [Vormen Bedrijfscalendars](/help/forms/using/admin-help/configuring-business-calendars.md#configuring-business-calendars).

Beperk de naam tot minder dan 53 tekens. Een kortere naam helpt problemen verhinderen tonend de bedrijfskalendersleutel in de pagina&#39;s van het Beheer van het Proces in beleidsconsole.

**Gebruikersnaam:** (Verplicht) Gebruikersnaam die de gebruiker gebruikt om zich aan te melden. De gebruikersnaam is niet hoofdlettergevoelig en moet in het hele domein uniek zijn.

In ondernemingsdomeinen, gebruik een niet-DN attribuut als gebruiker - identiteitskaart omdat DN van een gebruiker kan veranderen als zij naar een ander deel van de organisatie bewegen. Deze instelling is afhankelijk van de directoryserver. De waarde is `objectGUID` voor Actieve Folder 2003, `nsuniqueID` voor Sun™ Één, en `guid` voor eDirectory.

Controleer of de gebruikersnaam uniek is. Gebruik geen code die is toegewezen aan een verwijderde gebruiker.

AEM formulieren kunnen geen onderscheid maken tussen gebruikersaccounts die identieke gebruikers-id&#39;s en wachtwoorden hebben, maar tot verschillende domeinen behoren. Maak geen accounts met dezelfde gebruikersnaam op meerdere domeinen om dit probleem te voorkomen.

Wanneer u SQL Server als uw database gebruikt, kunt u geen gebruikers-id maken die meer dan 255 tekens bevat.

Wanneer u MySQL gebruikt, kan de gebruikersnaam uitgebreide tekens bevatten. Wanneer echter een vergelijking wordt gemaakt tussen twee tekenreeksen, zoals abcde en âbcdè, worden deze als hetzelfde beschouwd. Als bij het synchroniseren bijvoorbeeld een nieuwe gebruiker aan de database is toegevoegd, wordt een vergelijking gemaakt om te controleren of een gebruiker met dezelfde gebruikersnaam in de database aanwezig is. Als de gebruiker *abcde* reeds in het gegevensbestand bestaat wanneer de nieuwe gebruiker *âbcdè* wordt toegevoegd, kan de vergelijking niet tussen de twee namen onderscheiden. Aangenomen wordt dat de gebruiker al in de database bestaat en de nieuwe gebruiker wordt genegeerd en niet toegevoegd.

Maak geen gebruikersnamen die met een hekje (#) beginnen. Het uitvoeren van taakonderzoeken keert geen resultaten voor die gebruikersnamen terug. (See [Working with tasks](/help/forms/using/admin-help/tasks.md#working-with-tasks).)

**Wachtwoord en wachtwoord bevestigen:** Wachtwoord dat de gebruiker gebruikt om zich aan te melden. Het moet minimaal acht tekens hebben. Een wachtwoord is niet vereist voor een gebruiker die deel uitmaakt van een hybride domein.

## Details van een gebruiker weergeven {#view-details-about-a-user}

1. Klik in de beheerconsole op Instellingen > Gebruikersbeheer > Gebruikers en groepen.
1. Geef informatie op om de zoekopdracht te beperken en selecteer Gebruikers in de lijst In en klik vervolgens op Zoeken. De resultaten van de zoekopdracht worden onder aan de pagina weergegeven. U kunt de lijst sorteren door op een van de kolomkoppen te klikken.
1. Klik op de naam van de gebruiker om details weer te geven over. Op de pagina Gebruiker bewerken worden de volgende gegevens over de gebruiker weergegeven:

   * Algemene identificatiegegevens, zoals naam, e-mail, adres, domein en organisatie
   * Rollen die aan de gebruiker zijn toegewezen
   * Groepen de gebruiker een lid van is

## Het wachtwoord voor een lokale gebruiker wijzigen {#change-the-password-for-a-local-user}

1. Klik in de beheerconsole op **[!UICONTROL Settings > User Management > Users and Groups]**.
1. Geef informatie op om de zoekopdracht naar een bepaalde gebruiker te beperken en klik op **[!UICONTROL Find]**. De resultaten van de zoekopdracht worden onder aan de pagina weergegeven. U kunt de lijst sorteren door op een van de kolomkoppen te klikken.
1. Klik op de naam van de gebruiker en klik vervolgens op **[!UICONTROL Change Password]**.
1. Typ en bevestig het nieuwe wachtwoord en klik op **[!UICONTROL OK]**. Het wachtwoord moet minimaal acht tekens lang zijn.

## De eigenschappen van een gebruiker bewerken {#edit-a-user-s-properties}

1. Klik in de beheerconsole op **[!UICONTROL Settings > User Management > Users and Groups]**.
1. Voer de volgende taken uit om te zoeken naar de gebruiker die u wilt bewerken:

   * Typ uw zoekcriteria in het **[!UICONTROL Find]** vak.
   * Selecteer in de **[!UICONTROL Using]** lijst **[!UICONTROL Name]**, **[!UICONTROL Email]** of **[!UICONTROL User ID]**.
   * Selecteer in het **[!UICONTROL In list]** vak **[!UICONTROL Users]**.
   * Selecteer het domein, selecteer het aantal items dat u wilt weergeven en klik op **[!UICONTROL Find]**.

1. Klik op de gebruiker die u wilt bewerken.
1. Voor een gebruiker die deel van een lokaal of hybride domein uitmaakt, op het **[!UICONTROL Detail]** lusje, geef **[!UICONTROL General Settings]** en **[!UICONTROL Login Settings]** uit, en klik **[!UICONTROL Save]**. Zie [Gebruikersinstellingen](adding-configuring-users.md#user-settings)voor meer informatie over de instellingen. U kunt de algemene instellingen en aanmeldingsinstellingen niet bewerken voor een gebruiker die tot een ondernemingsdomein behoort.
1. Als u de groepsinstellingen voor de gebruiker wilt bewerken, klikt u op het **[!UICONTROL Group Membership]** tabblad en voert u de volgende taken uit:

   * Klik op de zoekgegevens **[!UICONTROL Find Group]** en vul deze in.
   * Als u de gebruiker aan een nieuwe groep wilt toevoegen, schakelt u het selectievakje voor de groep in, klikt u **[!UICONTROL OK]** en klikt u op **[!UICONTROL Save]**.

   >[!NOTE]
   >
   >Lokale gebruikers kunnen niet worden toegevoegd aan directorygroepen. Directorygebruikers kunnen echter wel aan lokale groepen worden toegevoegd.

   * Als u de gebruiker uit een groep wilt verwijderen, schakelt u het selectievakje voor de groep in, klikt u **[!UICONTROL Delete]** en klikt u op **[!UICONTROL Save]**.


1. Als u de rollen van de gebruiker wilt bewerken, klikt u op het **[!UICONTROL Role Assignments]** tabblad en voert u de volgende taken uit:

   * Als u een lijst met rollen wilt weergeven, klikt u **[!UICONTROL Find Roles]**.
   * Als u een rol wilt toevoegen, schakelt u het selectievakje voor de rol in, klikt u **[!UICONTROL OK]** en klikt u op **[!UICONTROL Save]**.
   * Als u een rol wilt verwijderen, schakelt u het selectievakje voor de rol in, klikt u **[!UICONTROL Unassign]** en klikt u op **[!UICONTROL Save]**.

## Een gebruiker verwijderen {#delete-a-user}

1. Klik in de beheerconsole op **[!UICONTROL Settings > User Management > Users and Groups]**.
1. Voer de volgende taken uit om te zoeken naar de gebruiker die u wilt verwijderen:

   * Typ uw zoekcriteria in het **[!UICONTROL Find]** vak.
   * Selecteer in de **[!UICONTROL Using]** lijst **[!UICONTROL Name]**, **[!UICONTROL Email]** of **[!UICONTROL User ID]**.
   * Selecteer in het **[!UICONTROL In list]** vak **[!UICONTROL Users]**.
   * Selecteer het domein, selecteer het aantal items dat u wilt weergeven en klik op **[!UICONTROL Find]**.

1. Selecteer het selectievakje voor de gebruiker, klik **[!UICONTROL Delete]** en klik op **[!UICONTROL OK]**.

>[!NOTE]
>
>Met AEM Forms on JEE kunnen gebruikers van de add-on AEM formulieren die op een OSGi worden uitgevoerd, ook worden herkend als AEM gebruikers. Dit is vereist voor scenario&#39;s waarbij een eenmalige aanmelding tussen AEM Forms op JEE en AEM formulieren invoegtoepassing op een OSGi vereist is (bijvoorbeeld HTML-werkruimte). Met bovengenoemde verwijderingsbewerking wordt alleen een gebruiker uit AEM Forms op JEE verwijderd. De gebruiker wordt niet geschrapt van AEM Forms toe:voegen-op lopend op milieu OSGi. Maar om het even welke login poging die na het schrappen van de gebruiker wordt gemaakt (een login poging aan de server van AEM Forms toe:voegen-op JEE of toe:voegen-on AEM Forms op milieu OSGi) wordt ontkend.

## Aangepaste handler voor aanmeldingsfouten maken {#create-custom-login-error-handler}

Als een gebruiker zonder de vereiste AEM en CQ-machtigingen zich probeert aan te melden bij de volgende toepassingen die zijn ingesloten in CQ, wordt de gebruiker omgeleid naar de standaard CQ 404-pagina met de fouttrace:

* Correspondentenbeheeroplossing
* Werkruimte AEM formulieren

   ***opmerking **: De Flex-werkruimte is verouderd voor AEM formulierrelease.*

* formulierbeheer
* Procesrapportage

CQ verstrekt een mechanisme om standaard 404 manager jsp met voeten te treden.

Zie Pagina&#39;s [aanpassen die worden weergegeven door de foutafhandeling](https://docs.adobe.com/docs/en/cq/current/developing/customizing_error_handler_pages.html) in de Adobe Experience Manager-documentatie voor meer informatie over het aanpassen van de pagina voor foutafhandeling.
