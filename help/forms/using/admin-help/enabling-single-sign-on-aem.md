---
title: Single Sign-On inschakelen in AEM formulieren
description: Leer hoe te om enig teken-op (SSO) toe te laten gebruikend de kopballen van HTTP en SPNEGO.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 89561ed0-d094-4ef7-9bc1-bde11f3c5bc3
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Document Security
role: User, Developer
source-git-commit: c941de0b069b5bea9edb822eca0ebbb5483ae9ed
workflow-type: tm+mt
source-wordcount: '1704'
ht-degree: 0%

---

# Single Sign-On inschakelen in AEM formulieren{#enabling-single-sign-on-in-aem-forms}

AEM formulieren bieden twee manieren om SSO (Single Sign-On) - HTTP-headers en SPNEGO in te schakelen.

Wanneer SSO is geïmplementeerd, zijn de aanmeldingspagina&#39;s voor AEM formulieren niet vereist en worden deze niet weergegeven als de gebruiker al is geverifieerd via het bedrijfsportaal.

Als AEM formulieren een gebruiker niet kunnen verifiëren met een van deze methoden, wordt de gebruiker omgeleid naar een aanmeldingspagina.

* [SSO inschakelen met HTTP-headers](#enable-sso-using-http-headers)
* [SSO inschakelen met SPNEGO](#enable-sso-using-spnego)
* [Rollen toewijzen aan gebruikers en groepen](#assign-roles-to-users-groups)

## SSO inschakelen met HTTP-headers {#enable-sso-using-http-headers}

U kunt de Poortconfiguratiepagina gebruiken om enige sign-on (SSO) tussen toepassingen en om het even welke toepassing toe te laten die het overbrengen van de identiteit over een kopbal van HTTP steunt. Wanneer SSO is geïmplementeerd, zijn de aanmeldingspagina&#39;s voor AEM formulieren niet vereist en worden deze niet weergegeven als de gebruiker al is geverifieerd via het bedrijfsportaal.

U kunt SSO ook toelaten door SPNEGO te gebruiken. (Zie [ SSO toelaten gebruikend SPNEGO ](enabling-single-sign-on-aem.md#enable-sso-using-spnego).)

1. Klik in de beheerconsole op Instellingen > Gebruikersbeheer > Configuration > Configure Portal Attributes.
1. Selecteer Ja om SSO in te schakelen. Als u Nee selecteert, zijn de overige instellingen op de pagina niet beschikbaar.
1. Stel de resterende opties op de pagina naar wens in en klik op OK:

   * **type SSO:** (Verplicht) Uitgezochte Kopbal van HTTP om SSO toe te laten gebruikend de kopballen van HTTP.
   * **HTTP- kopbal voor herkenningsteken van de gebruiker:** (Verplicht) Naam van de kopbal de waarvan waarde het het programma geopende herkenningsteken van de gebruiker bevat. Het Beheer van de gebruiker gebruikt deze waarde om de gebruiker in het gegevensbestand van het Gebruikersbeheer te vinden. De waarde die via deze header wordt verkregen, moet overeenkomen met de unieke id van de gebruiker die vanuit de LDAP-directory is gesynchroniseerd. (Zie [ montages van de Gebruiker ](/help/forms/using/admin-help/adding-configuring-users.md#user-settings).)
   * **de waardekaarten van het herkenningsteken aan Gebruiker - identiteitskaart in plaats van unieke herkenningsteken van de gebruiker:** Keert de unieke herkenningstekenwaarde van de gebruiker aan identiteitskaart van de Gebruiker in kaart. Selecteer deze optie als het unieke herkenningsteken van de gebruiker een binaire waarde is die niet gemakkelijk door de kopballen van HTTP kan worden verspreid (bijvoorbeeld, objectGUID als u gebruikers van Actieve Folder synchroniseert).
   * **HTTP- kopbal voor domein:** (Niet verplicht) Naam van de kopbal de waarvan waarde de domeinnaam bevat. Gebruik deze instelling alleen als geen enkele HTTP-header de gebruiker uniek identificeert. Gebruik deze instelling voor gevallen waarin meerdere domeinen bestaan en de unieke id alleen binnen een domein uniek is. In dit geval geeft u de headernaam op in dit tekstvak en geeft u domeintoewijzing op voor de meerdere domeinen in het vak Domeintoewijzing. (Zie [ het Uitgeven en het omzetten van bestaande domeinen ](/help/forms/using/admin-help/editing-converting-existing-domains.md#editing-and-converting-existing-domains).)
   * **afbeelding van het Domein:** (Verplicht) specificeert afbeelding voor veelvoudige domeinen in het formaat *kopbal value=domain naam*.

     Neem bijvoorbeeld een situatie waarin de HTTP-header voor een domein domain domainName is en waarden van domain1, domain2 of domain3 kan hebben. In dit geval, gebruik domeinafbeelding om de domainName waarden aan de domeinnamen van het Beheer van de Gebruiker in kaart te brengen. Elke toewijzing moet op een andere regel staan:

     domain1=UMdomain1

     domain2=UMdomain2

     domain3=UMdomain3

### Toegestane verwijzingen configureren {#configure-allowed-referers}

Voor de stappen om toegestane verwijzers te vormen, zie [ toegelaten verwijzers ](/help/forms/using/admin-help/preventing-csrf-attacks.md#configure-allowed-referers) vormen.

### Rollen toewijzen aan gebruikers en groepen

Klik om de stappen te kennen om [ rollen aan gebruikers en groepen ](/help/forms/using/admin-help/enabling-single-sign-on-aem.md#assign-roles-to-users-and-groups-assign-roles-to-users-groups) toe te wijzen.

## SSO inschakelen met SPNEGO {#enable-sso-using-spnego}

U kunt het Eenvoudige en Beschermde Mechanisme van de Onderhandeling van GSSAPI (SPNEGO) gebruiken om enige sign-on (SSO) toe te laten wanneer het gebruiken van Actieve Folder als uw server LDAP in een milieu van Vensters. Als SSO is ingeschakeld, zijn de aanmeldingspagina&#39;s voor AEM formulieren niet vereist en worden deze niet weergegeven.

U kunt SSO ook toelaten door de kopballen van HTTP te gebruiken. (Zie [ SSO gebruikend de kopballen van HTTP ](enabling-single-sign-on-aem.md#enable-sso-using-http-headers) toelaten.)

>[!NOTE]
>
>AEM Forms op JEE steunt het vormen SSO gebruikend Kerberos/SPNEGO in een veelvoudige milieu&#39;s van het kinddomein niet.

1. Bepaal welk domein om SSO toe te laten te gebruiken. De AEM Forms-server en de gebruikers moeten deel uitmaken van hetzelfde Windows-domein of vertrouwde domein.
1. In Actieve Folder, creeer een gebruiker die de Server van AEM Forms vertegenwoordigt. (Zie [ een gebruikersrekening ](enabling-single-sign-on-aem.md#create-a-user-account) creëren.) Als u meer dan één domein om SPNEGO te gebruiken vormt, zorg ervoor dat de wachtwoorden voor elk van deze gebruikers verschillend zijn. Als de wachtwoorden niet verschillend zijn, werkt SPNEGO SSO niet.
1. Wijs de de dienstbelangrijkste naam toe. (Zie [ een Belangrijkste Naam van de Dienst in kaart brengen (SPN) ](enabling-single-sign-on-aem.md#map-a-service-principal-name-spn).)
1. Configureer de domeincontroller. (Zie [ verhinderen Kerberos integriteit-controle mislukkingen ](enabling-single-sign-on-aem.md#prevent-kerberos-integrity-check-failures).)
1. Voeg of geef een ondernemingsdomein toe zoals die in [ wordt beschreven Toevoegend domeinen ](/help/forms/using/admin-help/adding-domains.md#adding-domains) of [ het Uitgeven en het omzetten van bestaande domeinen ](/help/forms/using/admin-help/editing-converting-existing-domains.md#editing-and-converting-existing-domains). Wanneer u creeert of het ondernemingsdomein uitgeeft, voer deze taken uit:

   * Voeg of geef een folder uit die uw Actieve informatie van de Folder bevat.
   * Voeg LDAP toe als verificatieprovider.
   * Voeg Kerberos als authentificatieleverancier toe. Verstrek de volgende informatie over de Nieuwe pagina of geef de pagina van de Authentificatie voor Kerberos uit:

      * **Leverancier van de Authentificatie:** Kerberos
      * **DNS IP:** het DNS IP adres van de server waar de AEM vormen lopen. U kunt dit IP adres bepalen door `ipconfig/all` op de bevellijn in werking te stellen.
      * **KDC Gastheer:** Fully Qualified gastheernaam of IP adres van de Actieve server van de Folder die voor authentificatie wordt gebruikt
      * **Gebruiker van de Dienst:** De dienst belangrijkste naam (SPN) ging tot het hulpmiddel KtPass over. In het eerder gebruikte voorbeeld is de servicegebruiker `HTTP/lcserver.um.lc.com` .
      * **Realm van de Dienst:** Naam van het Domein voor Actieve Folder. In het eerder gebruikte voorbeeld is de domeinnaam `UM.LC.COM.`
      * **Wachtwoord van de Dienst:** het wachtwoord van de gebruiker van de Dienst. In het eerder gebruikte voorbeeld is het servicewachtwoord `password` .
      * **laat SPNEGO toe:** laat het gebruik van SPNEGO voor enig teken-op (SSO) toe. Selecteer deze optie.

1. Configureer de instellingen van de SPNEGO-clientbrowser. (Zie [ Vormend SPNEGO cliëntbrowser montages ](enabling-single-sign-on-aem.md#configuring-spnego-client-browser-settings).)

### Een gebruikersaccount maken {#create-a-user-account}

1. In SPNEGO, registreer de dienst als gebruiker in Actieve Folder op het domeincontrolemechanisme om AEM vormen te vertegenwoordigen. Voor het domeincontrolemechanisme, ga het Menu van het Begin > Administratieve Hulpmiddelen > de Actieve Gebruikers en Computers van de Folder. Als de Administratieve Hulpmiddelen niet in het menu van het Begin is, gebruik het Controlebord.
1. Klik op de map Users om een lijst met gebruikers weer te geven.
1. Klik met de rechtermuisknop op de gebruikersmap en selecteer Nieuw > Gebruiker.
1. Typ de voornaam/achternaam en de gebruikersnaam en klik op Volgende. Stel bijvoorbeeld de volgende waarden in:

   * **Voornaam**: umspnego
   * **Logon van de Gebruiker Naam**: spnegodemo

1. Typ een wachtwoord. Bijvoorbeeld, plaats het aan *wachtwoord*. Zorg ervoor dat de optie Wachtwoord nooit verloopt is geselecteerd en dat er geen andere opties zijn geselecteerd.
1. Klik op Volgende en vervolgens op Voltooien.

### Wijs een Belangrijkste Naam van de Dienst (SPN) toe {#map-a-service-principal-name-spn}

1. Haal het hulpprogramma KtPass op. Dit nut wordt gebruikt om SPN aan REALM in kaart te brengen. U kunt het nut KtPass als deel van het pak van het Hulpmiddel van de Server van Vensters of het Uitrusting van het Middel verkrijgen. (Zie [ Server 2003 Service Pack 1 Ondersteuningsmiddelen van Vensters ](https://support.microsoft.com/kb/892777).)
1. Voer `ktpass` bij een opdrachtprompt uit met de volgende argumenten:

   `ktpass -princ HTTP/`*gastheer* `@`*REALM* `-mapuser`*gebruiker*

   Typ bijvoorbeeld de volgende tekst:

   `ktpass -princ HTTP/lcserver.um.lc.com@UM.LC.COM -mapuser spnegodemo`

   De waarden die u moet verstrekken worden beschreven als volgt:

   **gastheer:** volledig - gekwalificeerde naam van de Server van Forms of om het even welke unieke URL. In dit voorbeeld is deze ingesteld op lcserver.um.lc.com.

   **REALM:** het Actieve domein van de Folder voor het domeincontrolemechanisme. In dit voorbeeld is deze ingesteld op UM.LC.COM. Zorg ervoor dat u het domein in hoofdletters invoert. Voer de volgende stappen uit om het domein voor Windows 2003 te bepalen:

   * Klik met de rechtermuisknop op Deze computer en selecteer Eigenschappen
   * Klik op het tabblad Computernaam. De waarde van de Naam van het Domein is de domeinnaam.

   **gebruiker:** De login naam van de gebruikersrekening u in de vorige taak creeerde. In dit voorbeeld is deze ingesteld op spnegodemo.

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
1. Klik met de rechtermuisknop op de gebruikersaccount die u in een vorige taak hebt gemaakt. In dit voorbeeld is de gebruikersaccount `spnegodemo` .
1. Klik op Wachtwoord opnieuw instellen.
1. Typ en bevestig hetzelfde wachtwoord dat u eerder hebt getypt. In dit voorbeeld wordt deze ingesteld op `password` .
1. Schakel Wachtwoord wijzigen bij volgende aanmelding uit en klik op OK.

### Instellingen van SPNEGO-clientbrowser configureren {#configuring-spnego-client-browser-settings}

Voor op SPNEGO-Gebaseerde authentificatie om te werken, moet de cliëntcomputer deel van het domein uitmaken de gebruikersrekening wordt gecreeerd in. U moet cliëntbrowser ook vormen om op SPNEGO-Gebaseerde authentificatie toe te staan. Ook moet de site die verificatie op basis van SPNEGO vereist, een vertrouwde site zijn.

Als de server wordt betreden door de computernaam, zoals https://lcserver:8080 te gebruiken, worden geen montages vereist voor Internet Explorer. Als u een URL invoert die geen punten (&quot;.&quot;) bevat, behandelt Internet Explorer de site als een lokale intranetsite. Als u een volledig gekwalificeerde naam voor de site gebruikt, moet de site worden toegevoegd als een vertrouwde site.

**vorm Internet Explorer 6.x**

1. Ga naar Extra > Internetopties en klik op het tabblad Beveiliging.
1. Klik op het pictogram Lokaal intranet en klik vervolgens op Sites.
1. Klik op Geavanceerd en typ in het vak Deze website toevoegen aan zone de URL van uw Forms-server. Typ bijvoorbeeld: `https://lcserver.um.lc.com`
1. Klik op OK totdat alle dialoogvensters zijn gesloten.
1. Test de configuratie door de URL van uw AEM Forms-server te openen. Typ bijvoorbeeld in het vak URL van de browser `https://lcserver.um.lc.com:8080/um/login?um_no_redirect=true`

**vorm Mozilla Firefox**

1. Typ `about:config` in het vak URL van de browser

   Het dialoogvenster Info:config - Mozilla Firefox wordt weergegeven.

1. Typ `negotiate` in het vak Filter
1. In de getoonde lijst, klik network.onderhandelingen-auth.trusted-uri en typ één van de volgende bevelen zoals aangewezen voor uw milieu:

   `.um.lc.com` - Vormt Firefox om SPNEGO voor om het even welke URL toe te staan die met um.lc.com beëindigt. Zorg ervoor dat u de punt (&quot;.&quot;) opneemt aan het begin.

   `lcserver.um.lc.com` - Vormt Firefox om SPNEGO voor uw specifieke server slechts toe te staan. Begin deze waarde niet met een punt (&quot;.&quot;).

1. Test de configuratie door de toepassing te openen. De welkomstpagina voor de doeltoepassing moet worden weergegeven.

Klik om de stappen te kennen om [ rollen aan gebruikers en groepen ](/help/forms/using/admin-help/enabling-single-sign-on-aem.md#assign-roles-to-users-and-groups-assign-roles-to-users-groups) toe te wijzen.

## Rollen toewijzen aan gebruikers en groepen {#assign-roles-to-users-groups}

1. Meld u aan bij uw AEM Forms op JEE Environment.
1. Klik in de beheerconsole op Instellingen > Gebruikersbeheer > Domeinbeheer.
1. Selecteer uw domeinconfiguratie, bijvoorbeeld, LDAP, en klik op het. U vindt alle gecreeerde gebruikers en groepen in de Folder. Indien nodig kunt u nieuwe gebruikers of groepen maken.
   ![ het beheerspagina van het Domein ](/help/forms/using/assets/domain-mgmt-page.png)
1. Klik op Verificatie en selecteer op de nieuwe pagina een verificatieprovider, zoals LDAP.
1. Navigeer aan de pagina van het Beheer van het Domein, uitgezochte LDAP, en klik **nu SYN**, om de folder met de authentificatieregeling te synchroniseren u, voor AEM toegang vormde.
   ![ synchroniseer ldap ](/help/forms/using/assets/sync-ldap.png)
1. Ga naar Gebruikersbeheer en klik op Gebruikers en groepen.
1. Zoek naar gebruikers of groepen met hun namen, zoals aangetoond in hieronder beeld.
   ![ de gebruikersgroep van het Onderzoek ](/help/forms/using/assets/search-user-group.png)
1. Wijs de rollen aan de gebruikers of de groepen toe zoals vereist.
   ![ de roltaak van de Gebruiker ](/help/forms/using/assets/user-role-assign.png)

