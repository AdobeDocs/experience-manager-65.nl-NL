---
title: Beleid maken en beheren
description: Een beleid is een reeks vertrouwelijkheidsmontages en gebruikers die tot een document kunnen toegang hebben waarop het beleid wordt toegepast. U kunt verschillende soorten beleid maken en beheren met behulp van AEM.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_document_security
products: SG_EXPERIENCEMANAGER/6.5/FORMS
feature: Document Security
exl-id: 5e57451c-1a89-442c-8404-841e95d5ceff
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: 6a9806d8f40f711a610c130c63d9ab9b2460d075
workflow-type: tm+mt
source-wordcount: '4725'
ht-degree: 0%

---

# Beleid maken en beheren {#creating-and-managing-policies}

>[!NOTE]
> 
> Zorg ervoor dat de gebruiker beheerdersrechten heeft om toegang te krijgen tot de beheerdersconsole.

A *beleid* bepaalt een reeks vertrouwelijkheidsmontages en gebruikers die tot een document kunnen toegang hebben waarop het beleid wordt toegepast. A *beleidsreeks* wordt gebruikt om een reeks beleid te groeperen dat een gemeenschappelijk bedrijfsdoel heeft. Deze beleidsreeksen worden dan ter beschikking gesteld aan een ondergroep van gebruikers in het systeem. Voor details over beleid, zie [ Beleid en beleid-beschermde documenten ](/help/forms/using/admin-help/document-security.md#policies-and-policy-protected-documents).

## Soorten beleid {#types-of-policies}

Documentbeveiliging biedt de volgende typen beleid.

**Persoonlijk beleid**

Gebruikers kunnen hun eigen beleid maken, bewerken, kopiëren, verwijderen en toepassen met instellingen die geschikt zijn voor een bepaalde situatie. Alleen de persoon die een beleid maakt en de beheerder hebben toegang tot dat persoonlijke beleid. Het persoonlijke beleid verschijnt op het Mijn lusje van Beleid van de pagina van Beleid.

Uitgenodigde gebruikers kunnen ook persoonlijke beleidsregels maken, bewerken, kopiëren en verwijderen als de beheerder deze mogelijkheid inschakelt.

**Gedeeld beleid**

Beheerders en beleidssetcoördinatoren maken gezamenlijk beleid op basis van de vertrouwelijkheidsvereisten die uw organisatie voor verschillende typen documenten en gebruikers identificeert. Het gedeelde beleid is bevat binnen beleidsreeksen en is beschikbaar aan alle erkende gebruikers (documentuitgevers, beleidssetcoördinatoren, en documentontvangers) voor een bepaalde beleidsreeks. Beheerders en beleidssetcoördinatoren kunnen gedeeld beleid in- en uitschakelen. Gedeeld beleid wordt weergegeven in beleidssets op het tabblad Beleidssets van de pagina Beleid.

Wanneer u eerst documentveiligheid installeert, bevat het één gedeeld beleid, genoemd *Beperkt tot Alle Belangrijkste Belanghebbenden*. Wanneer dit beleid op een document wordt toegepast, kan om het even welke gebruiker die login aan documentveiligheid kan toegang hebben tot het document. Dit beleid is in de genoemde beleidsreeks *Globale Reeks van het Beleid*. Dit beleid is standaard niet ingeschakeld. U kunt de toepassing inschakelen als deze aan de behoeften van uw organisatie voldoet.

**Microsoft® Vooruitzichten auto-geproduceerd beleid**

Met Acrobat kunt u beleid toepassen op documenten die u als e-mailbijlagen verzendt in Microsoft® Outlook. In Vooruitzichten, kunt u een document beschermen door een bestaand beleid te gebruiken. U kunt ook een automatisch gegenereerd beleid gebruiken dat door Acrobat wordt gegenereerd met standaardinstellingen voor vertrouwelijkheid en dat van toepassing is op het document dat aan een e-mailbericht is gekoppeld. (Zie *[Hulp van Acrobat ](https://help.adobe.com/en_US/acrobat/pro/using/index.html)*.)

>[!NOTE]
>
>Een beleid beschikbaar in Vooruitzichten te zijn, moet u het beleid als favoriet in Acrobat plaatsen. Alle andere beleid, met inbegrip van die daar u de Uitgever bent, wordt niet getoond in Vooruitzichten.

## Wie beleid en beleidssets kan maken en beheren {#who-can-create-and-manage-policies-and-policy-sets}

De manier waarop u met beleid en beleidsreeksen in wisselwerking staat hangt van uw rol binnen de organisatie af:

**Gebruikers:** de Gebruikers kunnen, hun persoonlijk beleid tot stand brengen uitgeven en schrappen. Uitgenodigde gebruikers kunnen ook een persoonlijk beleid maken als de beheerder deze mogelijkheid inschakelt.

**de vastgestelde coördinatoren van het Beleid:** de vastgestelde coördinatoren van het Beleid kunnen gedeelde beleid binnen de beleidsreeksen tot stand brengen en leiden waar zij als coördinator worden aangewezen. Een beleidssetcoördinator is gewoonlijk een specialist in de organisatie die het beleid in een bepaalde beleidsreeks het best kan ontwerpen.

**Beheerders:** de Beheerders kunnen het persoonlijke beleid van om het even welke gebruiker uitgeven. Ze kunnen een gezamenlijk beleid maken. Ze kunnen ook beleidssets maken, bewerken en verwijderen en beleidssetcoördinatoren aanwijzen.

Voor details op de diverse rollen van de documentveiligheid, zie [ Ongeveer de gebruikers van de documentveiligheid ](/help/forms/using/admin-help/document-security.md#about-document-security-users).

## Beleid maken en bewerken {#creating-and-editing-policies}

Gebruikers kunnen een persoonlijk beleid voor eigen gebruik maken of bewerken. Beheerders en beleidssetcoördinatoren kunnen gedeelde beleidsregels voor uw organisatie maken of bewerken.

### Overwegingen bij het bewerken van beleidsregels {#considerations-for-editing-policies}

Wanneer u een beleid uitgeeft, beïnvloeden de veranderingen documenten die het beleid momenteel beschermt, en documenten die het beleid daarna beschermt. Als u bijvoorbeeld ontvangers verwijdert uit een beleid dat wordt toegepast op een document, kunnen de ontvangers het document niet meer openen.

De status van het document bepaalt wanneer de wijziging van kracht wordt:

* Als het document online is, worden de wijzigingen direct toegepast, tenzij het document voor de gebruiker is geopend. In dit geval moet de gebruiker het document sluiten voordat de wijzigingen van kracht worden.
* Als een ontvanger het document offline gebruikt (bijvoorbeeld op een laptop), worden de wijzigingen van kracht wanneer de ontvanger het document weer online plaatst. Het synchroniseert vervolgens met documentbeveiliging door een document te openen dat met een beleid is beveiligd.

>[!NOTE]
>
>Het beleid dat Acrobat automatisch genereert voor de ontvangers van documenten die zijn gekoppeld aan e-mailberichten in Microsoft® Outlook, komt niet voor in de beleidslijst. U kunt dit beleid alleen weergeven door de pagina Documentdetails voor het bijbehorende document te openen.

Wanneer u beleid bewerkt, gelden de volgende beperkingen:

* Uitgenodigde gebruikers kunnen beleid alleen bewerken als de beheerder deze mogelijkheid inschakelt. Als u het beleid niet kunt bewerken, is de optie Bewerken niet beschikbaar.
* Coördinatoren van beleidssets kunnen beleid binnen beleidssets alleen bewerken als ze de juiste machtigingen hebben. De beheerder van de super-gebruiker of van de beleidsreeks plaatst deze toestemmingen in het de beheerderinterface van de documentveiligheid.
* Als het beleid een watermerk heeft gevormd dat de beheerder schrapte aangezien het beleid werd gecreeerd, zal dit watermerk niet meer op documenten worden toegepast als u het beleid uitgeeft en bewaart. Verwijderde watermerken blijven alleen van kracht voor bestaand beleid zolang u het beleid niet bewerkt. Als u het beleid bewerkt, moet u een ander watermerk selecteren om het verwijderde watermerk te vervangen.
* U kunt geen anonieme toegang tot een document verlenen door het beleid uit te geven dat wordt toegepast. Als u het beleid bewerkt, moeten gebruikers zich nog steeds aanmelden om het document te openen. Om anonieme toegang tot dit document toe te passen, verwijder eerst het beleid in de cliënttoepassing en pas dan een ander beleid toe dat anonieme toegang toestaat.
* Het beleid dat Acrobat automatisch genereert voor de ontvangers van een document dat in Microsoft Outlook is gekoppeld aan een e-mailbericht, wordt niet weergegeven in de beleidslijst. Als u dit beleid wilt openen, zoekt u het document op de pagina Documenten, opent u de pagina Documentdetails en klikt u op de naam van het beleid in de lijst met documentdetails.

**creeer of geef een beleid** uit

1. Klik op de pagina Documentbeveiliging op Beleid en klik op een van de volgende tabbladen:

   * Als u een persoonlijk beleid wilt maken of bewerken, klikt u op het tabblad Mijn beleid.
   * Als u een gedeeld beleid wilt maken of bewerken, klikt u op het tabblad Beleidssets en klikt u op de naam van de desbetreffende beleidsset en vervolgens op het tabblad Beleid.

1. Klik op Nieuw of selecteer het beleid dat u wilt bewerken in de lijst.
1. Typ in het vak Naam een naam die het beleid uniek identificeert. Beschrijf in het vak Beschrijving wat het beleid doet en wanneer het moet worden gebruikt. Als het beleid binnen een beleidsreeks is, verschijnen de naam en de beschrijving in de beleidslijst voor alle gespecificeerde gebruikers. Het persoonlijke beleid is beschikbaar slechts aan de gebruiker en de beheerders.

   De volgende tekens kunnen niet in de naam of beschrijving worden gebruikt:

   * kleiner dan teken (&lt;)
   * groter dan-teken (>)
   * en-teken (&amp;)
   * enkel aanhalingsteken (&#39;)
   * dubbel aanhalingsteken (&quot;)
   * backslash (\)
   * slash (/)

   Als u het volgende teken in de naam of beschrijving hebt gebruikt, worden deze omgezet in spaties:

   * regelterugloop (ASCII-teken 13)
   * nieuwe regel (ASCII-teken 10).

   >[!NOTE]
   >
   >U kunt een beleidsnaam maken die uitgebreide tekens bevat. Wanneer echter een vergelijking wordt gemaakt tussen twee tekenreeksen, worden tekens met en zonder accent, zoals &quot;e&quot; en &quot;é&quot;, als hetzelfde beschouwd. Wanneer iemand een beleid maakt, wordt een vergelijking gemaakt om te controleren of een beleid met dezelfde naam bestaat. De vergelijking kan geen onderscheid maken tussen namen die hetzelfde zijn, behalve voor tekens met accent. Aangenomen wordt dat het beleid al aan de database is toegevoegd en dat het nieuwe beleid niet wordt toegevoegd.

1. Voeg gebruikers en groepen aan het beleid toe en plaats de aangewezen toestemmingen. (Zie [ Gebruikers en Groepen ](creating-policies.md#users-and-groups).)
1. Selecteer onder Algemene instellingen de gewenste opties. (Zie [ Algemene Montages ](creating-policies.md#general-settings).)
1. (Optioneel) Selecteer, indien van toepassing, een externe vergunningverlener en geef de eigenschappen ervan op. Als u geen externe vergunningsleverancier wilt gebruiken, verwijdert de klik StandaardLeverancier.

   Een externe vergunningverlener wordt gebruikt aan opstellingseigenschappen binnen het beleid en wanneer geselecteerd, gebruikt de externe vergunningsleverancier deze informatie om het beleid te evalueren. De beschikbare eigenschappen worden gevormd door de beheerder en de persoon die de software installeert.

1. Selecteer onder Geavanceerde instellingen de gewenste opties. (Zie [ Geavanceerde Montages ](creating-policies.md#advanced-settings).)
1. Selecteer onder Onveranderbare Geavanceerde instellingen de gewenste opties. (Zie [ Onveranderlijke Geavanceerde Montages ](creating-policies.md#unchangeable-advanced-settings).)
1. Klik op Opslaan. Het beleid wordt weergegeven in de lijst met beleidsitems. Naast het nieuwe beleid wordt een pictogram met een rode cirkel weergegeven om aan te geven dat het nog steeds is uitgeschakeld.

   Schakel het beleid in om het beschikbaar te maken voor gebruikers. (Zie [ toelaten of onbruikbaar maken gedeeld beleid ](creating-policies.md#enable-or-disable-shared-policies).)

### Gebruikers en groepen {#users-and-groups}

In het gebied Gebruikers en groepen geeft u de gebruikers op die toegang hebben tot documenten die met het beleid zijn beveiligd. Voor elke gebruiker of groep die u opgeeft, stelt u ook de gebruiksrechten voor het document in.

>[!NOTE]
>
>De uitgever van het document is de gebruiker die het document met het beleid beschermt. Deze gebruiker is altijd inbegrepen door gebrek op een beleid, met volledige toegangsrechten, met inbegrip van herroeping en beleid-omschakeling mogelijkheden. Beheerders kunnen echter de toegangsrechten van de uitgever van het document voor gedeeld beleid wijzigen. De beheerder kan bijvoorbeeld de documentuitgever beperken om de toegang tot het document in te trekken of het beleid te wijzigen.

**voeg Gebruiker of Groep toe:** om een gebruiker of een groep gebruikers toe te voegen, voegt de klik Gebruiker of Groep toe en klikt dan Geavanceerd Onderzoek zodat kunt u gebruikers of groepen vinden. De gebruikers omvatten de interne gebruikers van uw organisatie en uitgenodigde gebruikers die met documentveiligheid hebben geregistreerd. Wanneer u deze optie selecteert, wordt de pagina Gebruiker of Groep toevoegen weergegeven:

* Typ de naam of het e-mailadres van de gebruiker of groep in het vak Zoeken.
* Selecteer Naam of E-mail in de lijst Gebruiken.
* Selecteer Gebruiker of Groep in de lijst Type.
* Selecteer in de lijst In het domein dat u wilt zoeken en klik op Zoeken.
* Wanneer de resultaten worden geretourneerd, selecteert u de gebruiker of groep die u wilt toevoegen en klikt u op Toevoegen.

>[!NOTE]
>
>Als u een correcte uitgenodigde gebruikersnaam of e-mailadres ingaat en geen resultaat is teruggekeerd, kan de gebruiker nog niet geregistreerd hebben, of de rekening kan worden geschrapt. U kunt proberen de gebruiker toe te voegen als uitgenodigd gebruikerstype of uw beheerder contacteren.

**nodigt Nieuwe Gebruiker uit:** om een uitgenodigde gebruiker toe te voegen, nodigt de klik Nieuwe Gebruiker uit, typt het e-mailadres van de gebruiker in de doos die verschijnt, en klikt Uitnodigen. Deze optie is alleen beschikbaar als de beheerder deze heeft ingeschakeld. Wanneer u nieuwe uitgenodigde gebruikers aan een beleid toevoegt, verzendt de documentveiligheid een registratieuitnodiging e-mail als de gebruikers niet reeds worden uitgenodigd om zich te registreren. De gebruikers moeten de koppeling in de e-mail gebruiken om een account te maken en vervolgens het account activeren.

Nadat gebruikers zich hebben geregistreerd, kunnen ze met een beleid beveiligde documenten gebruiken waarvoor ze toestemming hebben. Afhankelijk van de mogelijkheden die de beheerder inschakelt, kunnen de externe gebruikers toestemming hebben om beleid toe te passen op documenten, beleid te maken, te bewerken en te verwijderen en andere externe gebruikers aan het beleid toe te voegen.

**voeg Anonieme Gebruiker toe:** om anonieme gebruikerstoegang toe te staan, voegt de klik Anonieme Gebruiker toe. Deze optie is alleen beschikbaar als de beheerder anonieme gebruikerstoegang heeft ingeschakeld voor documentbeveiliging. (Zie De documentbeveiligingsserver configureren.) Met deze optie krijgt iedereen toegang tot documenten die door dit beleid worden beveiligd, ongeacht of hij een account voor documentbeveiliging heeft. Als u deze optie selecteert, kunt u geen andere soorten gebruikers aan het beleid toevoegen.

>[!NOTE]
>
>Om anonieme toegang tot een beleid-beschermd document toe te laten dat het momenteel niet heeft, verwijder het bestaande beleid en pas dan een beleid toe dat anonieme toegang toestaat. Als u het bestaande beleid schakelt of wijzigt, moeten de gebruikers zich nog aanmelden om toegang te krijgen tot het document.

#### Documentmachtigingen opgeven voor gebruikers en groepen {#specify-the-document-permissions-for-users-and-groups}

U kunt documentmachtigingen voor één gebruiker of groep tegelijk opgeven, of u kunt meerdere gebruikers en groepen in de lijst selecteren en hun machtigingen wijzigen met de opties in het gebied met kolomkoppen.

Standaard hebben alle documenten die met een beleid zijn beveiligd een machtiging waarmee gebruikers ze online kunnen openen.

Het tabblad Machtigingen en opties wordt weergegeven in documentbeveiliging.

Deze documentmachtigingen zijn beschikbaar op het tabblad Machtigingen. U kunt deze machtigingen toepassen op PDF-, PTC Pro/E- en Microsoft Office-bestanden.

**Druk:** laat de gebruiker toe om een document te drukken dat met dit beleid wordt beschermd. Voor Office- en Pro/E-bestanden kunt u het selectievakje Afdrukken inschakelen om afdrukken toe te staan of uitschakelen om afdrukken te voorkomen. Als u het selectievakje Aangepaste machtigingen voor PDF tonen inschakelt, kunt u uit de volgende opties kiezen:

**niet Toegestaan:** de Gebruiker wordt niet toegestaan om PDF te drukken.

**Toegestaan:** de Gebruiker wordt toegestaan om PDF te drukken.

**Lage restanten. alleen:** De gebruiker mag de PDF met een lage resolutie afdrukken.

**wijzigt:** laat de gebruiker toe om een document te wijzigen dat met dit beleid wordt beschermd. Voor Office- en Pro/E-bestanden kunt u het selectievakje Wijzigen inschakelen om wijzigingen toe te staan of het selectievakje wissen om wijzigingen te voorkomen. Als u het selectievakje Aangepaste machtigingen voor PDF tonen inschakelt, kunt u uit de volgende opties kiezen:

**niet Toegestaan:** de Gebruiker wordt niet toegestaan om de PDF te wijzigen.

**om het even welk:** de Gebruiker kan de PDF wijzigen.

**Samenwerken:** de Gebruiker wordt toegestaan om met anderen samen te werken, gebruikend de Collaborate opties in Adobe Acrobat. Met deze machtiging kan de gebruiker formuliergegevens kopiëren, zelfs als de machtiging Kopiëren niet expliciet in het beleid is opgegeven.

**Veranderende Pagina&#39;s:** de Gebruiker wordt toegestaan om pagina&#39;s toe te voegen en te verwijderen en inhoud in de PDF uit te geven.

**Fill &amp; Sign:** de Gebruiker wordt toegestaan om vormgebieden op de PDF te vullen en het te ondertekenen.

**Exemplaar:** staat de gebruiker toe om tekst van een document te kopiëren dat met dit beleid wordt beschermd.

**de Reader van het Scherm:** Deze toestemming wordt getoond als u de Toon de Toon de Toon Toon de Toestemmingen van de Douane voor de controledoos van PDF selecteert. Als deze optie is ingeschakeld, heeft Adobe Acrobat toestemming om tijdelijke codes toe te voegen aan de PDF om de leesbaarheid met een schermlezer te verbeteren.

Deze documentmachtigingen zijn beschikbaar op het tabblad Opties. U kunt deze machtigingen toepassen op PDF-, PTC Pro/E- en Microsoft Office-bestanden:

**Off line:** staat de gebruiker toe om een document offline te bekijken dat met dit beleid wordt beschermd.

**Geldigheid van de Toestemming:** Uitgezochte Toestemmingen zijn altijd geldig of plaats een periode van de documenttoestemmingsgeldigheid. Als u een geldigheidsperiode selecteert, klikt u op het kalenderpictogram om een datum te selecteren en gebruikt u de pijlen om de tijd op te geven in de 24-uursnotatie.

Voor gedeelde beleidsregels kunnen beheerders de volgende bevoegdheden uitschakelen voor de documentuitgever (de gebruiker die het beleid toepast op een document):

**Intrekken:** laat de documentuitgever toe om de voorrechten van de documenttoegang in te trekken.

**Schakelaar:** laat de documentuitgever toe om beleidsvoorrechten te schakelen.

### Algemene instellingen {#general-settings}

Het gebied Algemene instellingen bevat de volgende instellingen:

**Periode van de Geldigheid:** de tijdspanne waarin het beleid-beschermde document aan erkende ontvangers toegankelijk is. U kunt uit deze opties voor de geldigheidsperiode kiezen:

**het Document zal niet geldig na zijn:** het document is toegankelijk voor het gespecificeerde aantal dagen vanaf toen het document werd beveiligd.

**het Document zal niet geldig na deze datum zijn:** het document is geldig van de datum het beleid wordt toegepast op het document tot de einddatum die wordt gespecificeerd.

**Geldig van, aan:** het document is geldig tijdens de data u specificeerde. U kunt de kalender gebruiken om een datum te selecteren, waar van toepassing, door het kalenderpictogram te klikken.

**Document is altijd geldig:** de periode van de documentgeldigheid verloopt niet.

>[!NOTE]
>
>De geldigheidsdata zijn gebaseerd op de tijdzone van het documentbeveiligingssysteem, niet op de tijdzone van uw lokale computer.

**Controle:** laat of maakt controle van de gebeurtenissen toe onbruikbaar die met een beleid-beschermd document worden geassocieerd. Documentbeveiliging kan bijvoorbeeld gebeurtenissen opnemen, zoals pogingen om een document te openen. Gecontroleerde gebeurtenissen worden weergegeven in de lijst op de pagina Gebeurtenissen. Als u deze optie niet selecteert, worden in documentbeveiliging geen gebeurtenissen vastgelegd voor documenten die aan het beleid zijn gekoppeld.

>[!NOTE]
>
>De beheerder moet server controle op de de configuratiepagina van de Montages van de Controle en van de Privacy ook toelaten om de controleeigenschap te werken.

**Uitgebreid Gebruik het Volgen:** laat of maakt het Uitgebreide Gebruik het Volgen onbruikbaar. Documentbeveiliging ondersteunt het bijhouden van gebruikersgebeurtenissen die zijn gekoppeld aan verschillende bewerkingen die op een PDF-bestand worden uitgevoerd. U kunt het documenthandbeveiligingsobject openen met behulp van een JavaScript. Een klik op een knop, een multimediabestand dat wordt afgespeeld of het opslaan van een bestand zijn enkele voorbeelden van gebeurtenissen die worden geactiveerd door een PDF die met een beleid is beveiligd. Met behulp van het beveiligingsobject van het document kunt u ook gebruikersgegevens ophalen. Het bijhouden van gebeurtenissen kan op algemeen niveau of op beleidsniveau worden ingeschakeld op de documentbeveiligingsserver.

**auto-Off-line Periode van de Verhuur:** het maximumaantal dagen de ontvanger het beleid-beschermde document offline (zonder actieve Internet of netwerkverbinding) kan gebruiken. Wanneer de huurperiode verloopt, moet de ontvanger het document opnieuw synchroniseren om het te blijven gebruiken.

### Externe machtigingsproviders {#external-authorization-providers}

Selecteer de externe verificatieproviders als u al een configuratie hebt geconfigureerd. Beschikbare providers worden vermeld.

### Verificatie-instellingen {#authentication-settings}

U kunt de authentificatiemontages met voeten treden die u op de server vormde en de authentificatieopties relevant voor dit beleid specificeren. Selecteer Globale authentificatie-instellingen overschrijven en selecteer dan de authentificatieopties relevant voor dit beleid. De volgende verificatieopties zijn beschikbaar:

**staat de Authentificatie van het Wachtwoord van de Gebruikersnaam toe:** selecteer deze optie als u cliënttoepassingen wilt toelaten om gebruikersnaam/wachtwoordauthentificatie te gebruiken wanneer het verbinden met de server.

**staat Authentificatie Kerberos toe:** selecteer deze optie als u cliënttoepassingen wilt toelaten om authentificatie te gebruiken Kerberos wanneer het verbinden met de server.

**staat de Authentificatie van het Certificaat van de Cliënt toe:** selecteer deze optie als u cliënttoepassingen wilt toelaten om certificaatauthentificatie te gebruiken wanneer het verbinden met de server.

**staat Uitgebreide Authentificatie** Uitgebreide Uitgezochte toe om uitgebreide authentificatie toe te laten. Als u deze optie selecteert, kunnen clienttoepassingen uitgebreide verificatie gebruiken. Uitgebreide verificatie biedt aangepaste verificatieprocessen en verschillende verificatieopties die zijn geconfigureerd op de Document Security-server

Als u de globale authentificatiemontages met voeten treedt, kunt u de authentificatieopties relevant voor dit beleid kiezen. Bijvoorbeeld, als u drie authentificatieopties (gebruikersbenaming en wachtwoord, cliëntcertificaat, en uitgebreide authentificatie) op de server had toegelaten, kunt u dat globale plaatsen met voeten treden en slechts uitgebreide authentificatie voor dit beleid selecteren. Zorg ervoor dat de verificatieoptie die u hier selecteert, al op de server is geconfigureerd. In dit voorbeeld, kunt u geen Kerberos als authentificatieoptie selecteren omdat het niet op de server wordt gevormd.

>[!NOTE]
>
>Uitgebreide verificatie wordt ondersteund op Apple Mac OS X met Adobe Acrobat versie 11.0.6 en hoger.

### Geavanceerde instellingen {#advanced-settings}

Het gebied Geavanceerde instellingen bevat de volgende instellingen:

**Dynamisch Watermerk:** selecteer een watermerk dat dynamisch op de pagina&#39;s van een document (bijvoorbeeld, wanneer een ontvanger het document drukt) moet worden getoond. Dynamische watermerken identificeren op unieke wijze een document, waardoor de vertrouwelijkheid van het document wordt gewaarborgd en inbreuk op het auteursrecht wordt voorkomen. De beheerder kan bijvoorbeeld een dynamisch watermerk configureren dat de huidige datum, de gebruikersnaam of id weergeeft van de persoon die het document gebruikt. Of de naam van het beleid waarmee het document is beveiligd. Een watermerk kan ook aangepaste tekst of grafische elementen weergeven, indien geconfigureerd. De beheerders vormen de watermerkopties, en de beheerders en de gebruikers kunnen hen op beleid toepassen.

(Zie [ dynamische watermerken ](/help/forms/using/admin-help/configuring-client-server-options.md#configure-dynamic-watermarks) vormen.)

Als u een beleid uitgeeft en de beheerder een gevormd watermerk schrapte dat u eerder voor dit beleid selecteerde, verschijnt een nota op de Edit pagina van het Beleid. In dit geval selecteert u een nieuw watermerk als u het bewerkte document wilt opslaan.

>[!NOTE]
>
>Voor beleid dat anonieme gebruikerstoegang verleent, worden de gebruikersnaam en het herkenningsteken van een anonieme gebruiker niet getoond als watermerk zelfs als u dit type van watermerk selecteert.

**Gebruik slechts Verklaarde stop-ins van Acrobat voor PDF:** wanneer geselecteerd voor een beleid, specificeert deze optie dat Acrobat 8.0 en later op verklaarde wijze moeten lopen wanneer het openen van documenten die met het beleid worden beveiligd. Als Acrobat wordt uitgevoerd in de gecertificeerde modus, worden er geen plug-ins van derden geladen.

Selecteer deze optie als u zich zorgen maakt over het schrijven van een insteekmodule door een ontvanger van een document die de documentbeveiliging in Acrobat 8.0 en hoger kan omzeilen. Selecteer deze optie niet als ontvangers van het document plug-ins van derden in Acrobat moeten gebruiken om te communiceren met documenten.

Met deze optie wordt alleen de gecertificeerde modus in Acrobat 8.0 of hoger ingeschakeld. De beheerder moet de toegang voor Acrobat 7.0 uitschakelen.

(Zie [ de server van de documentveiligheid ](/help/forms/using/admin-help/configuring-client-server-options.md#configure-the-document-security-server) vormen.)

Deze optie is niet van toepassing op Adobe Reader.

**Toegang ontkende de Bericht van de Fout:** Een bericht dat aan iedereen verschijnt die probeert om een beleid-beschermd document zonder toestemming te openen. Dit bericht wordt weergegeven in Acrobat. Clients die dit bericht niet kunnen weergeven, geven een standaardbericht weer om aan te geven dat toegang wordt geweigerd.

### Onverwisselbare geavanceerde instellingen {#unchangeable-advanced-settings}

Het gedeelte Onveranderbare geavanceerde instellingen bevat de volgende instellingen. U kunt deze instellingen niet wijzigen nadat u het beleid hebt opgeslagen.

**Algoritme van de Encryptie en Zeer belangrijke Lengte:** Gebruikt om uw documenten te beschermen. U kunt uit de volgende opties kiezen:

* AES 128-bits
* AES 256-bits. Alleen Acrobat 9.0 en hoger ondersteunen deze optie. Als u AES 256-versleuteling wilt gebruiken voor PDF-bestanden, moet u de JCE-bestanden (Unlimited Strength Rechtdiction Policy) (Java Cryptography Extension) ophalen en installeren. Deze dossiers vervangen de local_policy.jar en US_export_policy.jar dossiers in [ JAVE_HOME ] /lib/security omslag. Bijvoorbeeld, als u Zon JDK 1.6 gebruikt, kopieer de gedownloade dossiers aan de [ dep wortel ]/Java/jdk1.6.0_26/lib/security omslag. U kunt deze dossiers van [ downloaden de Downloads van SE van Java ](https://java.sun.com/javase/downloads/index.jsp).
* Geen versleuteling. Acrobat 9.0 en hoger ondersteunen deze optie momenteel. Als u deze optie selecteert, zijn de opties voor documentbeperkingen uitgeschakeld. Deze optie kan handig zijn als u documentbeveiliging wilt gebruiken voor documentcontrole of versiebeheer, maar het document niet wilt versleutelen.

**de Beperkingen van het Document:** selecteer de het documentcomponenten van de PDF om te coderen. Met andere clienttoepassingen wordt het gehele document versleuteld, maar niet de gekoppelde of ingesloten bestanden. U kunt uit de volgende opties kiezen:

* Het gehele document, inclusief de bijlagen en metagegevens. *Meta-gegevens* is informatie over het document en zijn inhoud die u door het de dialoogvakje van de Eigenschappen van het document of het Geavanceerde menu van Acrobat kunt bekijken. In Acrobat kunt u bestanden van verschillende typen (bijvoorbeeld tekst-, audio- en videobestanden) aan PDF-documenten koppelen.
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

De reeksen van het beleid die de beheerders creëren zijn vermeld op het lusje van de Reeksen van het Beleid van de pagina van Beleid. Zij bevatten informatie over de beleidsreeks, met inbegrip van zijn naam, de gecreeerde en gewijzigde datum, en een beschrijving. Klik op de naam van een beleidsset, zodat u de details kunt zien. Coördinatoren met beleidssets die gemachtigd zijn om beleid te beheren, kunnen gezamenlijk beleid maken binnen een bepaalde beleidsset.

Wanneer u creeert of een beleid uitgeeft, wordt een pagina getoond waar u de beleidsnaam, toestemmingsniveaus, vertrouwelijkheidsmontages, en de ontvangers kunt vormen om in het beleid te omvatten.

De beheerder kan de volgende vertrouwelijkheidsmontages voor een beleid vormen:

* Algemene vertrouwelijkheidsopties voor documenten, zoals de geldigheidsperiode van het document en de offline leaseperiode
* De geautoriseerde gebruikers en de documentbeperkingen en -rechten voor elk van deze gebruikers
* Geavanceerde opties voor documentvertrouwelijkheid, waaronder dynamische watermerken en documentversleuteling

Gebruikers kunnen het beleid bekijken dat ze hebben gemaakt en elk gedeeld beleid waartoe ze toegang hebben. Beheerders kunnen al het gedeelde en persoonlijke beleid weergeven dat zich in documentbeveiliging bevindt.

U kunt meer gedetailleerde informatie over een beleid bekijken dat in de lijst verschijnt, met inbegrip van de gebruikers of de groepen die op het beleid en de vertrouwelijkheidsmontages inbegrepen zijn die voor die gebruikers worden gespecificeerd.

>[!NOTE]
>
>Het beleid dat Acrobat automatisch genereert voor de ontvangers van documenten die in Microsoft Outlook zijn gekoppeld aan e-mailberichten, wordt niet weergegeven in de beleidslijst. U kunt dit beleid alleen weergeven door de pagina Documentdetails voor het bijbehorende document te openen.

1. Voor de pagina van de documentveiligheid, klik Beleid en klik dan het Mijn lusje van Beleid.
1. Voltooi de zoekgegevens zodat u naar persoonlijk beleid kunt zoeken.
1. Selecteer het gewenste beleid in de lijst.
1. Op de pagina van het Detail van het Beleid, kunt u details over het beleid zien, het beleid uitgeven, of gebeurtenissen met betrekking tot het beleid bekijken.

## Zoeken naar beleidsregels {#search-for-policies}

Beheerders kunnen zoeken naar gedeeld beleid en naar persoonlijk beleid dat door andere gebruikers is gemaakt.

1. Als u naar een gedeeld beleid wilt zoeken, klikt u op Beleid en vervolgens op het tabblad Beleidssets. Klik op een beleidsset in de lijst en klik vervolgens op het tabblad Beleid.

   Om naar een persoonlijk beleid, op de pagina van de documentveiligheid te zoeken, klik Beleid en klik dan het Mijn lusje van Beleid.

1. Selecteer een van de volgende opties in de lijst Zoeken:

   **identiteitskaart van het Beleid:** het aantal van beleidsidentificatie dat wordt geproduceerd wanneer de gebruiker het beleid leidt. Typ de exacte beleids-id.

   **Naam van het Beleid:** De naam van het beleid. U kunt naar een deel van de beleidsnaam of het geheel zoeken.

1. Typ in het tekstvak de corresponderende waarde. Als u bijvoorbeeld Beleidsnaam hebt geselecteerd, typt u de naam van het beleid waarnaar u zoekt.
1. Selecteer in de lijst Weergave het aantal resultaten dat u wilt weergeven en klik op Zoeken. De zoekresultaten worden weergegeven.
1. (Optioneel) Klik op het beleid om de beleidsdetails weer te geven.

## Een beleid kopiëren {#copy-a-policy}

U kunt een bestaand beleid kopiëren en opslaan met een nieuwe naam en beschrijving. Het kopiëren van beleid is een efficiënte manier om beleid tot stand te brengen door bestaande montages te gebruiken.

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

   Als u het volgende teken in de naam of beschrijving hebt gebruikt, worden deze omgezet in spaties:

   * regelterugloop (ASCII-teken 13)
   * nieuwe regel (ASCII-teken 10).

   >[!NOTE]
   >
   >U kunt een beleidsnaam maken die uitgebreide tekens bevat. Wanneer echter een vergelijking wordt gemaakt tussen twee tekenreeksen, worden tekens met en zonder accent, zoals &quot;e&quot; en &quot;é&quot;, als hetzelfde beschouwd. Wanneer iemand een beleid maakt, wordt een vergelijking gemaakt om te controleren of een beleid met dezelfde naam bestaat. De vergelijking kan geen onderscheid maken tussen namen die hetzelfde zijn, behalve voor tekens met accent. Aangenomen wordt dat het beleid al aan de database is toegevoegd en dat het nieuwe beleid niet wordt toegevoegd.

1. Klik op OK.

## Een beleid verwijderen {#delete-a-policy}

U kunt beleid verwijderen dat u hebt gemaakt. Beheerders kunnen beleid verwijderen dat door elke gebruiker is gemaakt. Coördinatoren van beleidssets kunnen beleid in hun beleidssets verwijderen. Een beleid dat u schrapt wordt nog afgedwongen voor documenten die met dat beleid worden beschermd. U kunt meerdere beleidsregels tegelijk verwijderen.

Uitgenodigde gebruikers kunnen beleid slechts schrappen als de beheerder dit vermogen toelaat. Als u geen beleid kunt verwijderen, is de verwijderingsoptie niet beschikbaar.

1. Klik op de pagina Documentbeveiliging op Beleid.
1. Klik op het tabblad Mijn beleid.
1. Als u een gedeeld beleid wilt verwijderen, klikt u op het tabblad Beleidssets en klikt u op de naam van de desbetreffende beleidsset.
1. Schakel het selectievakje naast het desbetreffende beleid in en klik op Verwijderen. Klik vervolgens op OK.

>[!NOTE]
>
>Gebruik de clienttoepassing om beleid uit documenten te verwijderen. (Zie de Help bij Acrobat of de desbetreffende Help bij Acrobat Reader DC-extensies.)

## De beleidslijst sorteren {#sort-the-policy-list}

U kunt de beleidslijst sorteren op kolomkop om beleid gemakkelijker te vinden. Een driehoekje naast de kolomkop geeft aan met welke kolom momenteel wordt gesorteerd. Een naar boven wijzend driehoekje geeft de oplopende volgorde aan, terwijl een naar beneden wijzend driehoekje de aflopende volgorde aangeeft.

1. Voor de pagina van de documentveiligheid, klik Beleid en klik het Geplaatste lusje van het Beleid.
1. Selecteer een beleidsset en klik op het tabblad Beleid.
1. Klik op de gewenste kolomkop.
1. Klik nogmaals op de kolom om de sorteervolgorde te wijzigen.
