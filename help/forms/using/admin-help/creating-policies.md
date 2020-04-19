---
title: Beleid maken en beheren
seo-title: Beleid maken en beheren
description: Een beleid is een reeks vertrouwelijkheidsmontages en gebruikers die tot een document kunnen toegang hebben waarop het beleid wordt toegepast. U kunt verschillende soorten beleid maken en beheren met AEM-formulieren.
seo-description: Een beleid is een reeks vertrouwelijkheidsmontages en gebruikers die tot een document kunnen toegang hebben waarop het beleid wordt toegepast. U kunt verschillende soorten beleid maken en beheren met AEM-formulieren.
uuid: 72be06f3-3e90-495e-8425-72380d95704a
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_document_security
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: fa054d30-c7dc-4b64-acf1-cbcbe8827df5
translation-type: tm+mt
source-git-commit: 2cf9dcf2e9cf71c54e19e2c6ee825c9a8f00a9b7

---


# Beleid maken en beheren {#creating-and-managing-policies}

Een *beleid* bepaalt een reeks vertrouwelijkheidsmontages en gebruikers die tot een document kunnen toegang hebben waarop het beleid wordt toegepast. Een *beleidsreeks* wordt gebruikt om een reeks beleid te groeperen dat een gemeenschappelijk bedrijfsdoel heeft. Deze beleidsreeksen worden dan ter beschikking gesteld aan een ondergroep van gebruikers in het systeem. Zie [Beleid en documenten](/help/forms/using/admin-help/document-security.md#policies-and-policy-protected-documents)die met beleid zijn beveiligd voor meer informatie over beleid.

## Soorten beleid {#types-of-policies}

Documentbeveiliging biedt de volgende typen beleid.

**Persoonlijk beleid**

Gebruikers kunnen hun eigen beleid maken, bewerken, kopiëren, verwijderen en toepassen met instellingen die geschikt zijn voor een bepaalde situatie. Alleen de persoon die een beleid maakt en de beheerders hebben toegang tot dat persoonlijke beleid. Het persoonlijke beleid verschijnt op het Mijn lusje van Beleid van de pagina van Beleid.

Uitgenodigde gebruikers kunnen ook persoonlijke beleidsregels maken, bewerken, kopiëren en verwijderen als de beheerder deze mogelijkheid inschakelt.

**Gedeeld beleid**

Beheerders en beleidssetcoördinatoren maken gezamenlijk beleid op basis van de vertrouwelijkheidsvereisten die uw organisatie voor verschillende typen documenten en gebruikers identificeert. Het gedeelde beleid is bevat binnen beleidsreeksen en is beschikbaar aan alle erkende gebruikers (documentuitgevers, beleidssetcoördinatoren, en documentontvangers) voor een bepaalde beleidsreeks. Beheerders en beleidssetcoördinatoren kunnen gedeeld beleid in- en uitschakelen. Gedeeld beleid wordt weergegeven in beleidssets op het tabblad Beleidssets van de pagina Beleid.

Wanneer u de documentbeveiliging voor het eerst installeert, bevat deze één gedeeld beleid met de naam *Beperken tot alle principal*. Wanneer dit beleid op een document wordt toegepast, kan om het even welke gebruiker die login aan documentveiligheid kan toegang hebben tot het document. Dit beleid wordt gevestigd in de beleidsreeks genoemd *Globale Reeks* van het Beleid. Dit beleid is standaard niet ingeschakeld. U kunt deze functie inschakelen als deze aan de behoeften van uw organisatie voldoet.

**Microsoft Outlook-beleid dat automatisch wordt gegenereerd**

Met Acrobat kunt u beleid toepassen op documenten die u als e-mailbijlagen verzendt in Microsoft Outlook. In Outlook kunt u een document beveiligen met behulp van een bestaand beleid of met behulp van een automatisch gegenereerd beleid dat Acrobat genereert met standaardinstellingen voor vertrouwelijkheid en dat van toepassing is op het document dat aan een e-mailbericht is gekoppeld. (Zie *[Acrobat Help](https://help.adobe.com/en_US/acrobat/pro/using/index.html)*.)

>[!NOTE]
>
>Een beleid is alleen beschikbaar in Outlook als u dit beleid instelt als een favoriet in Acrobat. Alle andere beleid, met inbegrip van die daar u de Uitgever bent, wordt niet getoond in Vooruitzichten.

## Wie beleid en beleidssets kan maken en beheren {#who-can-create-and-manage-policies-and-policy-sets}

De manier waarop u met beleid en beleidsreeksen in wisselwerking staat hangt van uw rol binnen de organisatie af:

**Gebruikers:** Gebruikers kunnen hun persoonlijke beleid maken, bewerken en verwijderen. Uitgenodigde gebruikers kunnen ook een persoonlijk beleid maken als de beheerder deze mogelijkheid inschakelt.

**Beleidssetcoördinatoren:** Coördinatoren van beleidssets kunnen gezamenlijk beleid maken en beheren binnen de beleidsgroepen waar zij als coördinator zijn aangewezen. Een beleidssetcoördinator is gewoonlijk een specialist in de organisatie die het beleid in een bepaalde beleidsreeks het best kan ontwerpen.

**Beheerders:** Beheerders kunnen het persoonlijke beleid van elke gebruiker bewerken. Ze kunnen een gezamenlijk beleid maken. Ze kunnen ook beleidssets maken, bewerken en verwijderen en beleidssetcoördinatoren aanwijzen.

Zie [Informatie over gebruikers](/help/forms/using/admin-help/document-security.md#about-document-security-users)voor documentbeveiliging voor meer informatie over de verschillende documentbeveiligingsrollen.

## Beleid maken en bewerken {#creating-and-editing-policies}

Gebruikers kunnen een persoonlijk beleid voor eigen gebruik maken of bewerken. Beheerders en beleidssetcoördinatoren kunnen gezamenlijk beleid voor uw organisatie maken of bewerken.

### Overwegingen bij het bewerken van beleidsregels {#considerations-for-editing-policies}

Wanneer u een beleid uitgeeft, beïnvloeden de veranderingen documenten die het beleid momenteel beschermt, evenals documenten die het beleid daarna beschermt. Als u bijvoorbeeld ontvangers verwijdert uit een beleid dat momenteel op een document wordt toegepast, kunnen de ontvangers het document niet meer openen.

De status van het document bepaalt wanneer de wijziging van kracht wordt:

* Als het document online is, worden de wijzigingen direct toegepast, tenzij het document voor de gebruiker is geopend. In dit geval moet de gebruiker het document sluiten voordat de wijzigingen van kracht worden.
* Als een ontvanger het document offline gebruikt (bijvoorbeeld op een laptop), worden de wijzigingen van kracht wanneer de ontvanger het document online neemt en synchroniseert met documentbeveiliging door een document te openen dat met een beleid is beveiligd.

>[!NOTE]
>
>Beleid dat door Acrobat automatisch wordt gegenereerd voor ontvangers van documenten die in Microsoft Outlook zijn gekoppeld aan e-mailberichten, wordt niet weergegeven in de beleidslijst. U kunt dit beleid alleen weergeven door de pagina Documentdetails voor het bijbehorende document te openen.

Wanneer u beleid bewerkt, gelden de volgende beperkingen:

* Uitgenodigde gebruikers kunnen beleid alleen bewerken als de beheerder deze mogelijkheid inschakelt. Als u het beleid niet kunt bewerken, is de optie Bewerken niet beschikbaar.
* Coördinatoren van beleidssets kunnen beleid binnen beleidssets alleen bewerken als ze de juiste machtigingen hebben. De beheerder van de supergebruiker of van de beleidsreeks plaatst deze toestemmingen in het de beheerderinterface van de documentveiligheid.
* Als het beleid een watermerk heeft gevormd dat de beheerder schrapte aangezien het beleid werd gecreeerd, zal dit watermerk niet meer op documenten worden toegepast als u het beleid uitgeeft en bewaart. Verwijderde watermerken blijven alleen van kracht voor bestaand beleid zolang u het beleid niet bewerkt. Als u het beleid bewerkt, moet u een ander watermerk selecteren om het verwijderde watermerk te vervangen.
* U kunt geen anonieme toegang tot een document verlenen door het beleid uit te geven dat momenteel wordt toegepast. Als u het beleid bewerkt, moeten gebruikers zich nog steeds aanmelden om het document te openen. Om anonieme toegang tot dit document toe te passen, verwijder eerst het beleid in de cliënttoepassing en pas dan een ander beleid toe dat anonieme toegang toestaat.
* Het beleid dat Acrobat automatisch genereert voor de ontvangers van een document dat in Microsoft Outlook is gekoppeld aan een e-mailbericht, wordt niet weergegeven in de beleidslijst. Als u dit beleid wilt openen, zoekt u het document op de pagina Documenten, opent u de pagina Documentdetails en klikt u op de naam van het beleid in de lijst met documentdetails.

**Een beleid maken of bewerken**

1. Klik op de pagina Documentbeveiliging op Beleid en klik op een van de volgende tabbladen:

   * Als u een persoonlijk beleid wilt maken of bewerken, klikt u op het tabblad Mijn beleid.
   * Als u een gedeeld beleid wilt maken of bewerken, klikt u op het tabblad Beleidssets en klikt u op de naam van de desbetreffende beleidsset en vervolgens op het tabblad Beleid.

1. Klik op Nieuw of selecteer het beleid dat u wilt bewerken in de lijst.
1. Typ in het vak Naam een naam die het beleid op unieke wijze identificeert. Beschrijf in het vak Beschrijving wat het beleid doet en wanneer het moet worden gebruikt. Als het beleid binnen een beleidsreeks is, verschijnen de naam en de beschrijving in de beleidslijst voor alle gespecificeerde gebruikers. Het persoonlijke beleid is beschikbaar slechts aan de gebruiker en de beheerders.

   De volgende tekens kunnen niet in de naam of beschrijving worden gebruikt:

   * kleiner dan teken (&lt;)
   * groter dan-teken (>)
   * en-teken (&amp;)
   * enkel aanhalingsteken (&#39;)
   * dubbel aanhalingsteken (&quot;)
   * backslash (\)
   * slash (/)
   Als u het volgende teken in de naam of beschrijving gebruikt, worden deze omgezet in spaties:

   * regelterugloop (ASCII-teken 13)
   * nieuwe regel (ASCII-teken 10).
   >[!NOTE]
   >
   >U kunt een beleidsnaam maken die uitgebreide tekens bevat. wanneer echter een vergelijking wordt gemaakt tussen twee tekenreeksen, worden tekens met en zonder accent, zoals &quot;e&quot; en &quot;é&quot;, als identiek beschouwd. Wanneer iemand een beleid maakt, wordt een vergelijking gemaakt om te controleren of er al een beleid met dezelfde naam bestaat. De vergelijking kan geen onderscheid maken tussen namen die hetzelfde zijn, behalve voor tekens met accent. Aangenomen wordt dat het beleid al aan de database is toegevoegd en dat het nieuwe beleid niet wordt toegevoegd.

1. Voeg gebruikers en groepen aan het beleid toe en plaats de aangewezen toestemmingen. (Zie [Gebruikers en groepen](creating-policies.md#users-and-groups).)
1. Selecteer onder Algemene instellingen de gewenste opties. (Zie [Algemene instellingen](creating-policies.md#general-settings).)
1. (Optioneel) Selecteer, indien van toepassing, een externe vergunningverlener en geef de eigenschappen ervan op. Als u geen externe vergunningsleverancier wilt gebruiken, verwijdert de klik StandaardLeverancier.

   Een externe vergunningverlener wordt gebruikt aan opstellingseigenschappen binnen het beleid en wanneer geselecteerd, gebruikt de externe vergunningsleverancier deze informatie om het beleid te evalueren. De beschikbare eigenschappen worden gevormd door de beheerder en de persoon die de software installeert.

1. Selecteer onder Geavanceerde instellingen de gewenste opties. (Zie [Geavanceerde instellingen](creating-policies.md#advanced-settings).)
1. Selecteer onder Onveranderbare Geavanceerde instellingen de gewenste opties. (Zie [Onveranderbare Geavanceerde instellingen](creating-policies.md#unchangeable-advanced-settings).)
1. Klik op Opslaan. Het beleid wordt weergegeven in de lijst met beleidsitems. Naast het nieuwe beleid wordt een pictogram met een rode cirkel weergegeven om aan te geven dat het nog steeds is uitgeschakeld.

   Schakel het beleid in om het beschikbaar te maken voor gebruikers. (Zie Gedeeld beleid [in- of uitschakelen](creating-policies.md#enable-or-disable-shared-policies).)

### Gebruikers en groepen {#users-and-groups}

In het gebied Gebruikers en groepen geeft u de gebruikers op die toegang hebben tot documenten die met het beleid zijn beveiligd. Voor elke gebruiker of groep die u opgeeft, stelt u ook de gebruiksrechten voor het document in.

>[!NOTE]
>
>De uitgever van het document is de gebruiker die het document met het beleid beschermt. Deze gebruiker is altijd inbegrepen door gebrek op een beleid, met volledige toegangsrechten, met inbegrip van herroeping en beleid-omschakeling mogelijkheden. Beheerders kunnen echter de toegangsrechten van de uitgever van het document voor gedeeld beleid wijzigen. De beheerder kan bijvoorbeeld de documentuitgever beperken om de toegang tot het document in te trekken of het beleid te wijzigen.

**Gebruiker of groep toevoegen:** Als u een gebruiker of groep gebruikers wilt toevoegen, klikt u op Gebruiker of Groep toevoegen en klikt u vervolgens op Geavanceerd zoeken om gebruikers of groepen te zoeken. De gebruikers omvatten de interne gebruikers van uw organisatie en uitgenodigde gebruikers die met documentveiligheid hebben geregistreerd. Wanneer u deze optie selecteert, wordt de pagina Gebruiker of Groep toevoegen weergegeven:

* Typ de naam of het e-mailadres van de gebruiker of groep in het vak Zoeken.
* Selecteer Naam of E-mail in de lijst Gebruiken.
* Selecteer Gebruiker of Groep in de lijst Type.
* Selecteer in de lijst In het domein dat u wilt zoeken en klik op Zoeken.
* Wanneer de resultaten worden geretourneerd, selecteert u de gebruiker of groep die u wilt toevoegen en klikt u op Toevoegen.

>[!NOTE]
>
>Als u een correcte uitgenodigde gebruikersnaam of e-mailadres ingaat en geen resultaat is teruggekeerd, kan de gebruiker nog niet geregistreerd hebben, of de rekening kan worden geschrapt. U kunt proberen de gebruiker toe te voegen als uitgenodigd gebruikerstype of uw beheerder contacteren.

**Nieuwe gebruiker uitnodigen:** Als u een uitgenodigde gebruiker wilt toevoegen, klikt u op Nieuwe gebruiker uitnodigen, typt u het e-mailadres van de gebruiker in het vak dat verschijnt en klikt u op Uitnodigen. Deze optie is alleen beschikbaar als de beheerder deze heeft ingeschakeld. Wanneer u nieuwe uitgenodigde gebruikers aan een beleid toevoegt, verzendt de documentveiligheid een registratieuitnodiging e-mail als de gebruikers niet reeds worden uitgenodigd om zich te registreren. De gebruikers moeten de koppeling in de e-mail gebruiken om een account te maken en vervolgens het account activeren.

Nadat gebruikers zich hebben geregistreerd, kunnen ze met een beleid beveiligde documenten gebruiken waarvoor ze toestemming hebben. Afhankelijk van de mogelijkheden die de beheerder inschakelt, kunnen de externe gebruikers toestemming hebben om beleid toe te passen op documenten, beleid te maken, te bewerken en te verwijderen en andere externe gebruikers aan het beleid toe te voegen.

**Anonieme gebruiker toevoegen:** Als u anonieme gebruikerstoegang wilt toestaan, klikt u op Anonieme gebruiker toevoegen. Deze optie is alleen beschikbaar als de beheerder anonieme gebruikerstoegang heeft ingeschakeld voor documentbeveiliging. (Zie De documentbeveiligingsserver configureren.) Met deze optie krijgt iedereen toegang tot documenten die door dit beleid worden beveiligd, ongeacht of hij een account voor documentbeveiliging heeft. Als u deze optie selecteert, kunt u geen andere soorten gebruikers aan het beleid toevoegen.

>[!NOTE]
>
>Om anonieme toegang tot een beleid-beschermd document toe te laten dat het momenteel niet heeft, verwijder het bestaande beleid en pas dan een beleid toe dat anonieme toegang toestaat. Als u het bestaande beleid schakelt of wijzigt, moeten de gebruikers zich nog aanmelden om het document te openen.

#### Documentmachtigingen opgeven voor gebruikers en groepen {#specify-the-document-permissions-for-users-and-groups}

U kunt documentmachtigingen voor één gebruiker of groep tegelijk opgeven, of u kunt meerdere gebruikers en groepen in de lijst selecteren en hun machtigingen wijzigen met de opties in het gebied met kolomkoppen.

Standaard hebben alle documenten die met een beleid zijn beveiligd een machtiging waarmee gebruikers ze online kunnen openen.

Het tabblad Machtigingen en Opties wordt weergegeven in documentbeveiliging.

Deze documentmachtigingen zijn beschikbaar op het tabblad Machtigingen. U kunt deze machtigingen toepassen op PDF-, PTC Pro/E- en Microsoft Office-bestanden.

**Afdrukken:** Hiermee kan de gebruiker een document afdrukken dat met dit beleid is beveiligd. Voor Office- en Pro/E-bestanden kunt u het selectievakje Afdrukken inschakelen om afdrukken toe te staan of uitschakelen om afdrukken te voorkomen. Als u het selectievakje Aangepaste machtigingen voor PDF tonen inschakelt, kunt u een van de volgende opties selecteren:

**Niet toegestaan:** De gebruiker mag de PDF niet afdrukken.

**Toegestaan:** De gebruiker mag de PDF afdrukken.

**Lage resolutie. alleen:** De gebruiker mag de PDF met een lage resolutie afdrukken.

**Wijzigen:** Hiermee kan de gebruiker een document wijzigen dat met dit beleid is beveiligd. Voor Office- en Pro/E-bestanden kunt u het selectievakje Wijzigen inschakelen om wijzigingen toe te staan of het selectievakje wissen om wijzigingen te voorkomen. Als u het selectievakje Aangepaste machtigingen voor PDF tonen inschakelt, kunt u een van de volgende opties selecteren:

**Niet toegestaan:** De gebruiker mag de PDF niet wijzigen.

**Willekeurig:** De gebruiker kan de PDF wijzigen.

**Samenwerken:** De gebruiker mag met anderen samenwerken, gebruikend de Collaborate opties in de Acrobaat van Adobe. Met deze machtiging kan de gebruiker formuliergegevens kopiëren, zelfs als de machtiging Kopiëren niet expliciet in het beleid is opgegeven.

**Pagina&#39;s wijzigen:** Gebruiker mag pagina&#39;s toevoegen en verwijderen en inhoud bewerken in de PDF.

**Vullen en ondertekenen:** De gebruiker mag formuliervelden in de PDF invullen en ondertekenen.

**Kopiëren:** Hiermee kan de gebruiker tekst kopiëren uit een document dat met dit beleid is beveiligd.

**Schermlezer:** Deze machtiging wordt weergegeven als u het selectievakje Aangepaste machtigingen voor PDF tonen inschakelt. Als deze optie is geselecteerd, heeft Adobe Acrobat toestemming om tijdelijke codes toe te voegen aan de PDF om de leesbaarheid met een schermlezer te verbeteren.

Deze documentmachtigingen zijn beschikbaar op het tabblad Opties. U kunt deze machtigingen toepassen op PDF-, PTC Pro/E- en Microsoft Office-bestanden:

**Off line:** Hiermee kan de gebruiker een document offline bekijken dat met dit beleid is beveiligd.

**Geldigheid machtiging:** Selecteer Machtigingen zijn altijd geldig of stel een geldigheidsperiode voor documentmachtigingen in. Als u een geldigheidsperiode selecteert, klikt u op de kalenderpictogrammen om een datum te selecteren en gebruikt u de pijlen om de tijd op te geven in de 24-uursnotatie.

Voor gedeelde beleidsregels kunnen beheerders de volgende bevoegdheden uitschakelen voor de documentuitgever (de gebruiker die het beleid toepast op een document):

**Intrekken:** Hiermee kan de uitgever van het document de toegangsrechten voor het document intrekken.

**Overschakelen:** Laat de documentuitgever toe om beleidsvoorrechten te schakelen.

### Algemene instellingen {#general-settings}

Het gebied Algemene instellingen bevat de volgende instellingen:

**Geldigheidsperiode:** De periode waarin het document met beleidsbescherming toegankelijk is voor geautoriseerde ontvangers. U kunt uit deze opties voor de geldigheidsperiode kiezen:

**Document is niet geldig na:** Het document is toegankelijk gedurende het opgegeven aantal dagen vanaf het moment dat het document is beveiligd.

**Document is na deze datum niet geldig:** Het document is geldig vanaf de datum waarop het beleid is toegepast op het document tot de opgegeven einddatum.

**Geldig van, tot en met:** Het document is geldig gedurende de opgegeven datums. U kunt de kalender gebruiken om een datum te selecteren, waar van toepassing, door het kalenderpictogram te klikken.

**Document is altijd geldig:** De geldigheidsperiode van het document loopt niet af.

>[!NOTE]
>
>De geldigheidsdata zijn gebaseerd op de tijdzone van het documentbeveiligingssysteem, niet op de tijdzone van uw lokale computer.

**Controle:** Het controleren van gebeurtenissen die aan een document met beleidsbeveiliging zijn gekoppeld, in- of uitschakelen. Documentbeveiliging kan bijvoorbeeld gebeurtenissen opnemen, zoals pogingen om een document te openen. Gecontroleerde gebeurtenissen worden weergegeven in de lijst op de pagina Gebeurtenissen. Als u deze optie niet selecteert, worden in documentbeveiliging geen gebeurtenissen vastgelegd voor documenten die aan het beleid zijn gekoppeld.

>[!NOTE]
>
>De beheerder moet server controle op de de configuratiepagina van de Montages van de Controle en van de Privacy ook toelaten om de controleeigenschap te werken.

**Uitgebreide gebruiksregistratie:** Het bijhouden van gebruik in- of uitschakelen Met documentbeveiliging kunt u gebruikersgebeurtenissen bijhouden die zijn gekoppeld aan verschillende bewerkingen die op een PDF-bestand worden uitgevoerd. U kunt het documenthandbeveiligingsobject openen met behulp van een JavaScript. Een klik op een knop, een multimediabestand dat wordt afgespeeld of het opslaan van een bestand zijn enkele voorbeelden van gebeurtenissen die kunnen worden gestart vanuit een PDF die met een beleid is beveiligd. Met behulp van het beveiligingsobject van het document kunt u ook gebruikersgegevens ophalen. Het bijhouden van gebeurtenissen kan op algemeen niveau of op beleidsniveau worden ingeschakeld op de documentbeveiligingsserver.

**Automatische offline leaseperiode:** Het maximumaantal dagen dat de ontvanger het document met beleidsbeveiliging offline kan gebruiken (zonder actieve internet- of netwerkverbinding). Wanneer de huurperiode verloopt, moet de ontvanger het document opnieuw synchroniseren om het te blijven gebruiken.

### Externe machtigingsproviders {#external-authorization-providers}

Selecteer de externe verificatieproviders als u al een configuratie hebt geconfigureerd. Beschikbare providers worden vermeld.

### Verificatie-instellingen {#authentication-settings}

U kunt de authentificatiemontages met voeten treden die u op de server vormde en de authentificatieopties relevant voor dit beleid specificeren. Selecteer Globale authentificatie-instellingen overschrijven en selecteer dan de authentificatieopties relevant voor dit beleid. De volgende verificatieopties zijn beschikbaar:

**Verificatie van wachtwoord gebruikersnaam toestaan:** Selecteer deze optie als clienttoepassingen bij het maken van een verbinding met de server gebruik moeten kunnen maken van gebruikersnaam-/wachtwoordverificatie.

**Kerberos-verificatie toestaan:** Selecteer deze optie om cliënttoepassingen toe te laten om authentificatie te gebruiken Kerberos wanneer het verbinden met de server.

**Client-certificaatverificatie toestaan:** Selecteer deze optie als u wilt dat clienttoepassingen certificaatverificatie kunnen gebruiken wanneer ze verbinding maken met de server.

**Uitgebreide verificatie** selecteren toestaan om uitgebreide verificatie in te schakelen. Als u deze optie selecteert, kunnen clienttoepassingen uitgebreide verificatie gebruiken. Uitgebreide verificatie biedt aangepaste verificatieprocessen en verschillende verificatieopties die zijn geconfigureerd op de Document Security-server

Als u de globale authentificatiemontages met voeten treedt, kunt u de authentificatieopties relevant voor dit beleid kiezen. Bijvoorbeeld, als u drie authentificatieopties (gebruikersbenaming en wachtwoord, cliëntcertificaat, en uitgebreide authentificatie) op de server had toegelaten, kunt u dat globale plaatsen met voeten treden en slechts uitgebreide authentificatie voor dit beleid selecteren. U moet ervoor zorgen dat de authentificatieoptie die u hier selecteert reeds op de server wordt gevormd. In dit voorbeeld, kunt u geen Kerberos als authentificatieoptie selecteren omdat het niet op de server wordt gevormd.

>[!NOTE]
>
>Uitgebreide verificatie wordt ondersteund op Apple Mac OS X met Adobe Acrobat versie 11.0.6 en hoger.

### Geavanceerde instellingen {#advanced-settings}

Het gebied Geavanceerde instellingen bevat de volgende instellingen:

**Dynamisch watermerk:** Selecteer een watermerk dat dynamisch moet worden weergegeven op de pagina&#39;s van een document (bijvoorbeeld wanneer een ontvanger het document afdrukt). Dynamische watermerken identificeren op unieke wijze een document, waardoor de vertrouwelijkheid van het document wordt gewaarborgd en inbreuk op het auteursrecht wordt voorkomen. Bijvoorbeeld, kan de beheerder een dynamisch watermerk vormen dat de huidige datum, de gebruikersnaam of herkenningsteken van de persoon toont die het document, of de naam van het beleid gebruikt gebruikt om het document te beschermen. Een watermerk kan aangepaste tekst of grafische elementen ook weergeven als dit is geconfigureerd. De beheerders vormen de watermerkopties, en de beheerders en de gebruikers kunnen hen op beleid toepassen.

(Zie Dynamische watermerken [configureren](/help/forms/using/admin-help/configuring-client-server-options.md#configure-dynamic-watermarks).)

Als u een beleid uitgeeft en de beheerder een gevormd watermerk schrapte dat u eerder voor dit beleid selecteerde, verschijnt een nota op de Edit pagina van het Beleid. In dit geval selecteert u een nieuw watermerk als u het bewerkte document wilt opslaan.

>[!NOTE]
>
>Voor beleid dat anonieme gebruikerstoegang verleent, worden de gebruikersnaam en het herkenningsteken van een anonieme gebruiker niet getoond als watermerk zelfs als u dit type van watermerk selecteert.

**Alleen gecertificeerde insteekmodules van Acrobat gebruiken voor PDF:** Als deze optie is geselecteerd voor een beleid, moet Acrobat 8.0 en hoger worden uitgevoerd in de gecertificeerde modus wanneer documenten worden geopend die zijn beveiligd met het beleid. Wanneer Acrobat wordt uitgevoerd in de gecertificeerde modus, worden er geen plug-ins van derden geladen.

Selecteer deze optie als u zich zorgen maakt over het schrijven van een insteekmodule door een ontvanger van een document die de documentbeveiliging in Acrobat 8.0 en hoger kan omzeilen. Selecteer deze optie niet als ontvangers van het document plug-ins van derden in Acrobat moeten gebruiken om te communiceren met documenten.

Met deze optie wordt alleen de gecertificeerde modus in Acrobat 8.0 of hoger ingeschakeld. de beheerder moet de toegang voor Acrobat 7.0 uitschakelen.

(Zie De documentbeveiligingsserver [](/help/forms/using/admin-help/configuring-client-server-options.md#configure-the-document-security-server)configureren.)

Deze optie is niet van toepassing op Adobe Reader.

**Foutbericht toegang geweigerd:** Een bericht dat wordt weergegeven aan iedereen die een document probeert te openen dat met een beleid is beveiligd zonder toestemming. Dit bericht wordt weergegeven in Acrobat. Clients die dit bericht niet kunnen weergeven, geven een standaardbericht weer om aan te geven dat toegang wordt geweigerd.

### Onverwisselbare geavanceerde instellingen {#unchangeable-advanced-settings}

Het gedeelte Onveranderbare geavanceerde instellingen bevat de volgende instellingen. U kunt deze instellingen niet wijzigen nadat u het beleid hebt opgeslagen.

**Versleutelingsalgoritme en sleutellengte:** Wordt gebruikt om uw documenten te beveiligen. U kunt uit deze opties kiezen:

* AES 128-bits
* AES 256-bits. Alleen Acrobat 9.0 en hoger ondersteunen deze optie. Als u AES 256-versleuteling wilt gebruiken voor PDF-bestanden, moet u de JCE-bestanden (Unlimited Strength Jurdiction Policy) (Java Cryptography Extension) ophalen en installeren. Deze bestanden vervangen de bestanden local_policy.jar en US_export_policy.jar in de map [JAVE_HOME]/lib/security. Als u bijvoorbeeld Sun JDK 1.6 gebruikt, kopieert u de gedownloade bestanden naar de map [dep root]/Java/jdk1.6.0_26/lib/security. U kunt deze bestanden downloaden van [Java SE-downloads](https://java.sun.com/javase/downloads/index.jsp).
* Geen versleuteling. Deze optie wordt momenteel ondersteund in Acrobat 9.0 en hoger. Als u deze optie selecteert, zijn de opties voor documentbeperkingen uitgeschakeld. Deze optie kan handig zijn als u documentbeveiliging wilt gebruiken voor documentcontrole of versiebeheer, maar het document niet wilt versleutelen.

**Documentbeperkingen:** Selecteer de PDF-documentcomponenten die u wilt versleutelen. Met andere clienttoepassingen wordt het gehele document versleuteld, maar niet de gekoppelde of ingesloten bestanden. U kunt uit deze opties kiezen:

* Het gehele document, inclusief de bijlagen en metagegevens. *Metagegevens* zijn gegevens over het document en de inhoud ervan die u kunt weergeven via het dialoogvenster Documenteigenschappen of het menu Geavanceerd van Acrobat. In Acrobat kunt u bestanden van verschillende typen (bijvoorbeeld tekst-, audio- en videobestanden) aan PDF-documenten koppelen.
* Het document en de bijlagen, maar niet de metagegevens.
* Alleen de documentbijlagen. U kunt de bijlagen versleutelen naar een PDF-bestand zonder de documentinhoud te versleutelen.

## Gedeeld beleid in- of uitschakelen {#enable-or-disable-shared-policies}

Om een gedeeld beleid beschikbaar te maken, moet de beheerder of de coördinator van de beleidsreeks het toelaten. U kunt nieuw beleid of eerder onbruikbaar gemaakt beleid toelaten. Een gedeeld beleid dat u onbruikbaar maakt wordt nog afgedwongen voor documenten die met dat beleid worden beschermd.

Er verschijnt een rode X naast een uitgeschakeld beleid.

>[!NOTE]
>
>Beheerders kunnen persoonlijk beleid niet uitschakelen en gebruikers kunnen hun eigen beleid niet in- en uitschakelen.

1. Voor de pagina van de documentveiligheid, klik Beleid en klik dan de Reeksen van het Beleid tabel.
1. Klik op de naam van de desbetreffende beleidsset en klik op het tabblad Beleid.
1. Schakel het selectievakje naast het desbetreffende beleid in, klik op Inschakelen of Uitschakelen en klik op OK.

## Informatie over een beleid weergeven {#view-information-about-a-policy}

Gebruikend het Mijn lusje van Beleid, kunt u persoonlijk beleid zoeken.

De reeksen van het beleid die de beheerders creëren zijn vermeld op het lusje van de Reeksen van het Beleid van de pagina van Beleid met informatie over de beleidsreeks, met inbegrip van zijn naam, de gecreeerde en gewijzigde datum, en een beschrijving. Klik op de naam van een beleidsset om de details weer te geven. Coördinatoren met beleidssets die gemachtigd zijn om beleid te beheren, kunnen gezamenlijk beleid maken binnen een bepaalde beleidsset.

Wanneer u creeert of een beleid uitgeeft, wordt een pagina getoond waar u details zoals beleidsnaam, toestemmingsniveaus, vertrouwelijkheidsmontages, en de ontvangers kunt vormen om in het beleid te omvatten.

De beheerder kan de volgende vertrouwelijkheidsmontages voor een beleid vormen:

* Algemene vertrouwelijkheidsopties voor documenten, zoals de geldigheidsperiode van het document en de offline leaseperiode
* De geautoriseerde gebruikers en de documentbeperkingen en -rechten voor elk van deze gebruikers
* Geavanceerde opties voor documentvertrouwelijkheid, waaronder dynamische watermerken en documentversleuteling

Gebruikers kunnen het beleid bekijken dat ze hebben gemaakt en elk gedeeld beleid waartoe ze toegang hebben. Beheerders kunnen al het gedeelde en persoonlijke beleid weergeven dat zich in documentbeveiliging bevindt.

U kunt meer gedetailleerde informatie over een beleid bekijken dat in de lijst verschijnt, met inbegrip van de gebruikers of de groepen die op het beleid en de vertrouwelijkheidsmontages inbegrepen zijn die voor die gebruikers worden gespecificeerd.

>[!NOTE]
>
>Beleid dat door Acrobat automatisch wordt gegenereerd voor ontvangers van documenten die in Microsoft Outlook zijn gekoppeld aan e-mailberichten, wordt niet weergegeven in de beleidslijst. U kunt dit beleid alleen weergeven door de pagina Documentdetails voor het bijbehorende document te openen.

1. Voor de pagina van de documentveiligheid, klik Beleid en klik dan het Mijn lusje van Beleid.
1. Voltooi de zoekinformatie om te zoeken naar persoonlijk beleid.
1. Selecteer het gewenste beleid in de lijst.
1. Op de pagina van het Detail van het Beleid, kunt u details over het beleid zien, het beleid uitgeven, of gebeurtenissen met betrekking tot het beleid bekijken.

## Zoeken naar beleid {#search-for-policies}

Beheerders kunnen zoeken naar gedeeld beleid en naar persoonlijk beleid dat door andere gebruikers is gemaakt.

1. Als u naar een gedeeld beleid wilt zoeken, klikt u op Beleid en vervolgens op het tabblad Beleidssets. Klik op een beleidsset in de lijst en klik vervolgens op het tabblad Beleid.

   Om naar een persoonlijk beleid, op de pagina van de documentveiligheid te zoeken, klik Beleid en klik dan het Mijn lusje van Beleid.

1. Selecteer een van de volgende opties in de lijst Zoeken:

   **Beleid-id:** Het beleidsidentificatienummer dat wordt geproduceerd wanneer de gebruiker het beleid creeert. U moet de exacte beleids-id typen.

   **Beleidsnaam:** De naam van het beleid. U kunt de naam van het beleid geheel of gedeeltelijk zoeken.

1. Typ in het tekstvak de bijbehorende waarde. Als u bijvoorbeeld Beleidsnaam hebt geselecteerd, typt u de naam van het beleid waarnaar u zoekt.
1. Selecteer in de lijst Weergave het aantal resultaten dat u wilt weergeven en klik op Zoeken. De zoekresultaten worden weergegeven.
1. (Optioneel) Klik op het beleid om de beleidsdetails weer te geven.

## Een beleid kopiëren {#copy-a-policy}

U kunt een bestaand beleid kopiëren en opslaan met een nieuwe naam en beschrijving. Het kopiëren van beleid is een efficiënte manier om nieuw beleid tot stand te brengen door bestaande montages te gebruiken.

Externe gebruikers kunnen beleid alleen kopiëren als de beheerder deze mogelijkheid inschakelt. Als u geen beleid kunt maken, is de optie Kopiëren niet beschikbaar.

1. Voor de pagina van de documentveiligheid, klik Beleid en klik dan het Mijn lusje van het Beleid.
1. Selecteer het gewenste beleid in de lijst.
1. Voor de pagina van het Detail van het Beleid, klik Exemplaar.
1. Typ in het vak Nieuwe beleidsnaam de nieuwe beleidsnaam. Typ desgewenst een nieuwe beschrijving.

   De volgende tekens kunnen niet in de naam of beschrijving worden gebruikt:

   * kleiner dan teken (&lt;)
   * groter dan-teken (>)
   * en-teken (&amp;)
   * enkel aanhalingsteken (&#39;)
   * dubbel aanhalingsteken (&quot;)
   * backslash (\)
   * slash (/)
   Als u het volgende teken in de naam of beschrijving gebruikt, worden deze omgezet in spaties:

   * regelterugloop (ASCII-teken 13)
   * nieuwe regel (ASCII-teken 10).
   >[!NOTE]
   >
   >U kunt een beleidsnaam maken die uitgebreide tekens bevat. wanneer echter een vergelijking wordt gemaakt tussen twee tekenreeksen, worden tekens met en zonder accent, zoals &quot;e&quot; en &quot;é&quot;, als identiek beschouwd. Wanneer iemand een beleid maakt, wordt een vergelijking gemaakt om te controleren of er al een beleid met dezelfde naam bestaat. De vergelijking kan geen onderscheid maken tussen namen die hetzelfde zijn, behalve voor tekens met accent. Aangenomen wordt dat het beleid al aan de database is toegevoegd en dat het nieuwe beleid niet wordt toegevoegd.

1. Klik op OK.

## Een beleid verwijderen {#delete-a-policy}

U kunt beleid verwijderen dat u hebt gemaakt. Beheerders kunnen beleid verwijderen dat door elke gebruiker is gemaakt. Coördinatoren van beleidssets kunnen beleid in hun beleidssets verwijderen. Een beleid dat u schrapt wordt nog afgedwongen voor documenten die met dat beleid worden beschermd. U kunt meerdere beleidsregels tegelijk verwijderen.

Uitgenodigde gebruikers kunnen beleid slechts schrappen als de beheerder dit vermogen toelaat. Als u geen beleid kunt verwijderen, is de verwijderingsoptie niet beschikbaar.

1. Klik op de pagina Documentbeveiliging op Beleid.
1. Klik op het tabblad Mijn beleid.
1. Als u een gedeeld beleid wilt verwijderen, klikt u op het tabblad Beleidssets en klikt u op de naam van de desbetreffende beleidsset.
1. Schakel het selectievakje naast het desbetreffende beleid in en klik op Verwijderen. Klik vervolgens op OK.

>[!NOTE]
>
>U moet de clienttoepassing gebruiken om het beleid uit documenten te verwijderen. (Zie Acrobat Help of de juiste Help bij Acrobat Reader DC-extensies.)

## De beleidslijst sorteren {#sort-the-policy-list}

U kunt de beleidslijst sorteren op kolomkop om beleid gemakkelijker te vinden. Een driehoekje naast de kolomkop geeft aan welke kolom momenteel wordt gebruikt om te sorteren. Een naar boven wijzend driehoekje geeft de oplopende volgorde aan, terwijl een naar beneden wijzend driehoekje de aflopende volgorde aangeeft.

1. Voor de pagina van de documentveiligheid, klik Beleid en klik het Geplaatste lusje van het Beleid.
1. Selecteer een beleidsset en klik op het tabblad Beleid.
1. Klik op de gewenste kolomkop.
1. Klik nogmaals op de kolom om de sorteervolgorde te wijzigen.

