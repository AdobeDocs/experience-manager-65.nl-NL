---
title: Single Sign-On inschakelen in AEM formulieren
seo-title: Single Sign-On inschakelen in AEM formulieren
description: Leer hoe te om enig teken-op (SSO) toe te laten gebruikend de kopballen van HTTP en SPNEGO.
seo-description: Leer hoe te om enig teken-op (SSO) toe te laten gebruikend de kopballen van HTTP en SPNEGO.
uuid: 2bc08b4f-dcbe-4a16-9025-32fc14605e13
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: ee54d9d4-190d-4665-925a-9740ac65fbd5
translation-type: tm+mt
source-git-commit: 998a127ce00c6cbb3db3a81d8a89d97ab9ef7469
workflow-type: tm+mt
source-wordcount: '1538'
ht-degree: 0%

---


# Single Sign-On inschakelen in AEM formulieren{#enabling-single-sign-on-in-aem-forms}

AEM formulieren bieden twee manieren om SSO (Single Sign-On) - HTTP-headers en SPNEGO in te schakelen.

Wanneer SSO is geïmplementeerd, zijn de aanmeldingspagina&#39;s voor AEM formulieren niet vereist en worden deze niet weergegeven als de gebruiker al is geverifieerd via het bedrijfsportaal.

Als AEM formulieren een gebruiker niet kunnen verifiëren met een van deze methoden, wordt de gebruiker omgeleid naar een aanmeldingspagina.

## SSO inschakelen met HTTP-headers {#enable-sso-using-http-headers}

U kunt de Poortconfiguratiepagina gebruiken om enige sign-on (SSO) tussen toepassingen en om het even welke toepassing toe te laten die het overbrengen van de identiteit over de kopbal van HTTP steunt. Wanneer SSO is geïmplementeerd, zijn de aanmeldingspagina&#39;s voor AEM formulieren niet vereist en worden deze niet weergegeven als de gebruiker al is geverifieerd via het bedrijfsportaal.

U kunt SSO ook toelaten door SPNEGO te gebruiken. (Zie [SSO inschakelen met SPNEGO](enabling-single-sign-on-aem.md#enable-sso-using-spnego).)

1. Klik in de beheerconsole op Instellingen > Gebruikersbeheer > Configuratie > Portal kenmerken configureren.
1. Selecteer Ja om SSO in te schakelen. Als u Nee selecteert, zijn de overige instellingen op de pagina niet beschikbaar.
1. Stel de resterende opties op de pagina naar wens in en klik op OK:

   * **Type SSO:** (Verplicht) Selecteer HTTP-koptekst om SSO in te schakelen via HTTP-headers.
   * **HTTP-header voor de id van de gebruiker:** (Verplicht) Naam van de koptekst waarvan de waarde de unieke id van de aangemelde gebruiker bevat. Het Beheer van de gebruiker gebruikt deze waarde om de gebruiker in het gegevensbestand van het Beheer van de Gebruiker te vinden. De waarde die via deze header wordt verkregen, moet overeenkomen met de unieke id van de gebruiker die vanuit de LDAP-directory is gesynchroniseerd. (Zie [Gebruikersinstellingen](/help/forms/using/admin-help/adding-configuring-users.md#user-settings).)
   * **De id-waarde wordt toegewezen aan de gebruikersnaam van de gebruiker in plaats van aan de unieke id van de gebruiker:** Wijst de unieke-id van de gebruiker toe aan de gebruikersnaam. Selecteer deze optie als het unieke herkenningsteken van de gebruiker een binaire waarde is die niet gemakkelijk door de kopballen van HTTP kan worden verspreid (bijvoorbeeld, objectGUID als u gebruikers van Actieve Folder synchroniseert).
   * **HTTP-header voor domein:** (Niet verplicht) Naam van de koptekst waarvan de waarde de domeinnaam bevat. Gebruik deze instelling alleen als geen enkele HTTP-header de gebruiker uniek identificeert. Gebruik deze instelling voor gevallen waarin meerdere domeinen bestaan en de unieke id alleen binnen een domein uniek is. In dit geval geeft u de headernaam op in dit tekstvak en geeft u domeintoewijzing op voor de meerdere domeinen in het vak Domeintoewijzing. (Zie Bestaande domeinen [](/help/forms/using/admin-help/editing-converting-existing-domains.md#editing-and-converting-existing-domains)bewerken en omzetten.)
   * **Domeintoewijzing:** (Verplicht) Geeft toewijzing voor meerdere domeinen in de notatie *header value=domain name*.

      Neem bijvoorbeeld een situatie waarin de HTTP-header voor een domein domain domainName is en waarden van domain1, domain2 of domain3 kan hebben. In dit geval, gebruik domeinafbeelding om de domainName waarden aan de domeinnamen van het Beheer van de Gebruiker in kaart te brengen. Elke toewijzing moet op een andere regel staan:

      domain1=UMdomain1

      domain2=UMdomain2

      domain3=UMdomain3

### Toegestane verwijzingen configureren {#configure-allowed-referers}

Voor de stappen om toegestane verwijzers te vormen, zie toegestane verwijzingen [vormen](/help/forms/using/admin-help/preventing-csrf-attacks.md#configure-allowed-referers).

## SSO inschakelen met SPNEGO {#enable-sso-using-spnego}

U kunt het Eenvoudige en Beschermde Mechanisme van de Onderhandeling van GSSAPI (SPNEGO) gebruiken om enige sign-on (SSO) toe te laten wanneer het gebruiken van Actieve Folder als uw server LDAP in een milieu van Vensters. Als SSO is ingeschakeld, zijn de aanmeldingspagina&#39;s voor AEM formulieren niet vereist en worden deze niet weergegeven.

U kunt SSO ook toelaten door de kopballen van HTTP te gebruiken. (Zie [SSO inschakelen met HTTP-headers](enabling-single-sign-on-aem.md#enable-sso-using-http-headers).)

>[!NOTE]
>
>AEM Forms op JEE steunen het vormen SSO gebruikend Kerberos/SPNEGO in een veelvoudige milieu&#39;s van het kinddomein niet.

1. Bepaal welk domein om SSO toe te laten te gebruiken. De AEM formulierserver en de gebruikers moeten deel uitmaken van hetzelfde Windows-domein of vertrouwde domein.
1. In Actieve Folder, creeer een gebruiker die de AEM vormenserver vertegenwoordigt. (Zie [Een gebruikersaccount](enabling-single-sign-on-aem.md#create-a-user-account)maken.) Als u meer dan één domein om SPNEGO te gebruiken vormt, zorg ervoor dat de wachtwoorden voor elk van deze gebruikers verschillend zijn. Als de wachtwoorden niet verschillend zijn, werkt SPNEGO SSO niet.
1. Wijs de de dienstbelangrijkste naam toe. (Zie [Een serviceprecitenaam (SPN)](enabling-single-sign-on-aem.md#map-a-service-principal-name-spn)toewijzen.)
1. Configureer de domeincontroller. (Zie [Kerberos integriteit-controle mislukkingen](enabling-single-sign-on-aem.md#prevent-kerberos-integrity-check-failures)verhinderen.)
1. Voeg of bewerk een ondernemingsdomein toe zoals beschreven in het [Toevoegen van domeinen](/help/forms/using/admin-help/adding-domains.md#adding-domains) of het [Bewerken en het omzetten van bestaande domeinen](/help/forms/using/admin-help/editing-converting-existing-domains.md#editing-and-converting-existing-domains). Wanneer u creeert of het ondernemingsdomein uitgeeft, voer deze taken uit:

   * Voeg of geef een folder uit die uw Actieve informatie van de Folder bevat.
   * Voeg LDAP toe als verificatieprovider.
   * Voeg Kerberos als authentificatieleverancier toe. Verstrek de volgende informatie over de Nieuwe pagina of geef de pagina van de Authentificatie voor Kerberos uit:

      * **Verificatieprovider:** Kerberos
      * **DNS IP:** Het DNS IP-adres van de server waarop AEM formulieren worden uitgevoerd. U kunt dit IP adres bepalen door `ipconfig/all` op de bevellijn te lopen.
      * **KDC-host:** Volledig - gekwalificeerde gastheernaam of IP adres van de Actieve server van de Folder die voor authentificatie wordt gebruikt
      * **Servicegebruiker:** De service principal name (SPN) die wordt doorgegeven aan het gereedschap KtPass. In het voorbeeld dat eerder wordt gebruikt, is de de dienstgebruiker `HTTP/lcserver.um.lc.com`.
      * **Servicerealm:** Domeinnaam voor Active Directory. In het eerder gebruikte voorbeeld is de domeinnaam `UM.LC.COM.`
      * **Servicewachtwoord:** Wachtwoord van de gebruiker van de dienst. In het voorbeeld dat eerder wordt gebruikt, is het de dienstwachtwoord `password`.
      * **SPNEGO inschakelen:** Hiermee wordt het gebruik van SPNEGO voor Single Sign-On (SSO) ingeschakeld. Selecteer deze optie.

1. Configureer de instellingen van de SPNEGO-clientbrowser. (Zie [Instellingen](enabling-single-sign-on-aem.md#configuring-spnego-client-browser-settings)van SPNEGO-clientbrowser configureren.)

### Een gebruikersaccount maken {#create-a-user-account}

1. In SPNEGO, registreer de dienst als gebruiker in Actieve Folder op het domeincontrolemechanisme om AEM vormen te vertegenwoordigen. Voor het domeincontrolemechanisme, ga het Menu van het Begin > Administratieve Hulpmiddelen > de Actieve Gebruikers en Computers van de Folder. Als de Administratieve Hulpmiddelen niet in het menu van het Begin is, gebruik het Controlebord.
1. Klik op de map Users om een lijst met gebruikers weer te geven.
1. Klik met de rechtermuisknop op de gebruikersmap en selecteer Nieuw > Gebruiker.
1. Typ de voornaam/achternaam en de gebruikersnaam en klik op Volgende. Stel bijvoorbeeld de volgende waarden in:

   * **Voornaam**: umspnego
   * **Gebruikersnaam** aanmelding: spnegodemo

1. Typ een wachtwoord. Stel het bijvoorbeeld in op *wachtwoord*. Zorg ervoor dat de optie Wachtwoord nooit verloopt is geselecteerd en dat er geen andere opties zijn geselecteerd.
1. Klik op Volgende en vervolgens op Voltooien.

### Wijs een Belangrijkste Naam van de Dienst (SPN) toe {#map-a-service-principal-name-spn}

1. Haal het hulpprogramma KtPass op. Dit nut wordt gebruikt om SPN aan REALM in kaart te brengen. U kunt het nut KtPass als deel van het pak van het Hulpmiddel van de Server van Vensters of het Uitrusting van het Middel verkrijgen. (Zie [Windows Server 2003 Service Pack 1 Support Tools](https://support.microsoft.com/kb/892777).)
1. Voer een opdrachtprompt uit `ktpass` met de volgende argumenten:

   `ktpass -princ HTTP/`*host *`@`*REALM* - `-mapuser`*gebruiker *

   Typ bijvoorbeeld de volgende tekst:

   `ktpass -princ HTTP/lcserver.um.lc.com@UM.LC.COM -mapuser spnegodemo`

   De waarden die u moet verstrekken worden beschreven als volgt:

   **host:** Volledig gekwalificeerde naam van de formulierserver of elke unieke URL. In dit voorbeeld is deze ingesteld op lcserver.um.lc.com.

   **REALM:** Het Actieve domein van de Folder voor het domeincontrolemechanisme. In dit voorbeeld is deze ingesteld op UM.LC.COM. Zorg ervoor dat u het domein in hoofdletters invoert. Voer de volgende stappen uit om het domein voor Windows 2003 te bepalen:

   * Klik met de rechtermuisknop op Deze computer en selecteer Eigenschappen
   * Klik op het tabblad Computernaam. De waarde van de Naam van het Domein is de domeinnaam.

   **gebruiker:** De aanmeldnaam van de gebruikersaccount die u in de vorige taak hebt gemaakt. In dit voorbeeld is deze ingesteld op spnegodemo.

Als deze fout optreedt:

```shell
DsCrackNames returned 0x2 in the name entry for spnegodemo.
ktpass:failed getting target domain for specified user.
```

Geef de gebruiker op als spnegodemo@um.lc.com:

```shell
ktpass -princ HTTP/lcserver.um.lc.com@UM.LC.COM -mapuser spnegodemo
```

### Vermijd Kerberos integriteit-controle mislukkingen {#prevent-kerberos-integrity-check-failures}

1. Voor het domeincontrolemechanisme, ga het Menu van het Begin > Administratieve Hulpmiddelen > de Actieve Gebruikers en Computers van de Folder. Als de Administratieve Hulpmiddelen niet in het menu van het Begin is, gebruik het Controlebord.
1. Klik op de map Users om een lijst met gebruikers weer te geven.
1. Klik met de rechtermuisknop op de gebruikersaccount die u in een vorige taak hebt gemaakt. In dit voorbeeld is de gebruikersaccount `spnegodemo`.
1. Klik op Wachtwoord opnieuw instellen.
1. Typ en bevestig hetzelfde wachtwoord dat u eerder hebt getypt. In dit voorbeeld is deze ingesteld op `password`.
1. Schakel de optie Wachtwoord wijzigen bij volgende aanmelding uit en klik op OK.

### Instellingen van SPNEGO-clientbrowser configureren {#configuring-spnego-client-browser-settings}

Voor op SPNEGO-Gebaseerde authentificatie om te werken, moet de cliëntcomputer deel van het domein uitmaken de gebruikersrekening wordt gecreeerd in. U moet cliëntbrowser ook vormen om op SPNEGO-Gebaseerde authentificatie toe te staan. Ook moet de site die verificatie op basis van SPNEGO vereist, een vertrouwde site zijn.

Als de server wordt betreden door de computernaam, zoals https://lcserver:8080 te gebruiken, worden geen montages vereist voor Internet Explorer. Als u een URL invoert die geen punten (&quot;.&quot;) bevat, behandelt Internet Explorer de site als een lokale intranetsite. Als u een volledig gekwalificeerde naam voor de site gebruikt, moet de site worden toegevoegd als een vertrouwde site.

**Internet Explorer 6.x configureren**

1. Ga naar Extra > Internetopties en klik op het tabblad Beveiliging.
1. Klik op het pictogram Lokaal intranet en klik vervolgens op Sites.
1. Klik op Geavanceerd en typ in het vak Deze website toevoegen aan zone de URL van de formulierserver. For example, type `https://lcserver.um.lc.com`
1. Klik op OK totdat alle dialoogvensters zijn gesloten.
1. Test de configuratie door de URL van uw AEM formulierserver te openen. Typ bijvoorbeeld in het vak URL van de browser `https://lcserver.um.lc.com:8080/um/login?um_no_redirect=true`

**Mozilla Firefox configureren**

1. Typ in het vak URL van de browser `about:config`

   Het dialoogvenster Info:config - Mozilla Firefox wordt weergegeven.

1. Typ in het vak Filter `negotiate`
1. In de getoonde lijst, klik network.onderhandelingen-auth.trusted-uri en typ één van de volgende bevelen zoals aangewezen voor uw milieu:

   `.um.lc.com`- Vormt Firefox om SPNEGO voor om het even welke URL toe te staan die met um.lc.com beëindigt. Zorg ervoor dat u de punt (&quot;.&quot;) aan het begin.

   `lcserver.um.lc.com` - Vormt Firefox om SPNEGO voor uw specifieke server slechts toe te staan. Begin deze waarde niet met een punt (&quot;.&quot;).

1. Test de configuratie door de toepassing te openen. De welkomstpagina voor de doeltoepassing moet worden weergegeven.

