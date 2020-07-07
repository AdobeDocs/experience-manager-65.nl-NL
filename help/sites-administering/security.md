---
title: Gebruikersbeheer en beveiliging
seo-title: Gebruikersbeheer en beveiliging
description: Meer informatie over gebruikersbeheer en beveiliging in AEM.
seo-description: Meer informatie over gebruikersbeheer en beveiliging in AEM.
uuid: 4512c0bf-71bf-4f64-99f6-f4fa5a61d572
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
discoiquuid: e72da81b-4085-49b0-86c3-11ad48978a8a
docset: aem65
translation-type: tm+mt
source-git-commit: ebf3f34af7da6b1a659ac8d8843152b97f30b652
workflow-type: tm+mt
source-wordcount: '5487'
ht-degree: 0%

---


# Gebruikersbeheer en beveiliging{#user-administration-and-security}

In dit hoofdstuk wordt beschreven hoe u gebruikersautorisatie configureert en onderhoudt en wordt ook beschreven hoe verificatie en autorisatie in AEM werken.

## Gebruikers en groepen in AEM {#users-and-groups-in-aem}

Deze sectie behandelt de diverse entiteiten en verwante concepten meer in detail om u te helpen een gemakkelijk vormen om gebruikersbeheerconcept te handhaven.

### Gebruikers {#users}

Gebruikers zullen zich bij AEM aanmelden met hun account. Elke gebruikersaccount is uniek en bevat de basisaccountgegevens, samen met de toegewezen rechten.

Gebruikers zijn vaak leden van Groepen, waardoor de toewijzing van deze machtigingen en/of bevoegdheden wordt vereenvoudigd.

### Groepen {#groups}

Groepen zijn verzamelingen van gebruikers en/of andere groepen; Dit zijn allemaal leden van een fractie.

Hun voornaamste doel is het onderhoudsproces te vereenvoudigen door het aantal bij te werken entiteiten te verminderen, aangezien een wijziging van een groep op alle leden van de groep wordt toegepast. Groepen weerspiegelen vaak:

* een rol binnen de aanvraag; zoals iemand die op de inhoud mag surfen of iemand die inhoud mag toevoegen.
* uw eigen organisatie; u kunt de rollen willen uitbreiden om tussen contribuanten van verschillende afdelingen te onderscheiden wanneer zij tot verschillende takken in de inhoudsboom beperkt zijn.

Groepen blijven daarom over het algemeen stabiel, terwijl gebruikers vaker komen en gaan.

Met planning en een schone structuur kan het gebruik van groepen uw structuur weerspiegelen, waardoor u een duidelijk overzicht krijgt en een efficiënt mechanisme voor updates.

### Built-in Users and Groups {#built-in-users-and-groups}

AEM WCM installeert een aantal gebruikers en groepen. Deze kunnen worden gezien wanneer u eerst tot de Console van de Veiligheid na installatie toegang hebt.

In de volgende tabellen wordt elk item vermeld, samen met:

* een korte beschrijving
* eventuele aanbevelingen over noodzakelijke wijzigingen

*Wijzig alle standaardwachtwoorden* (als u het account zelf niet verwijdert in bepaalde omstandigheden).

<table>
 <tbody>
  <tr>
   <td>Gebruikersnaam</td>
   <td>Type</td>
   <td>Beschrijving</td>
   <td>Aanbeveling</td>
  </tr>
  <tr>
   <td><p>beheerder</p> <p>Standaardwachtwoord: beheerder</p> </td>
   <td>Gebruiker</td>
   <td><p>Systeembeheeraccount met volledige toegangsrechten.</p> <p>Dit account wordt gebruikt voor de verbinding tussen AEM WCM en CRX.</p> <p>Als u dit account per ongeluk verwijdert, wordt het opnieuw gemaakt nadat de opslagplaats opnieuw is opgestart (in de standaardconfiguratie).</p> <p>De beheerdersaccount is een vereiste voor het AEM-platform. Dit betekent dat dit account niet kan worden verwijderd.</p> </td>
   <td><p>Adobe raadt u ten zeerste aan het wachtwoord voor deze gebruikersaccount te wijzigen.</p> <p>Bij voorkeur na installatie, maar achteraf.</p> <p>Opmerking: Dit account mag niet worden verward met de beheerdersaccount van de CQ Servlet Engine.</p> </td>
  </tr>
  <tr>
   <td><p>anoniem</p> <p> </p> </td>
   <td>Gebruiker</td>
   <td><p>Houdt de standaardrechten voor ongeautoriseerde toegang tot een instantie. Per gebrek houdt dit de minimumtoegangsrechten.</p> <p>Als u dit account per ongeluk verwijdert, wordt het bij het opstarten opnieuw gemaakt. Het kan niet permanent worden geschrapt, maar het kan worden onbruikbaar gemaakt.</p> </td>
   <td>Verwijder of schakel dit account niet uit, omdat dit negatieve gevolgen heeft voor het functioneren van auteur-instanties. Als er beveiligingsvereisten zijn die u verplichten deze te verwijderen, moet u controleren of u de effecten ervan op uw systemen eerst op de juiste wijze test.</td>
  </tr>
  <tr>
   <td><p>author</p> <p>Standaardwachtwoord: auteur</p> </td>
   <td>Gebruiker</td>
   <td><p>Een auteursaccount mag schrijven naar /content. Omvat contribuant en surfer voorrechten.</p> <p>Kan als webmaster worden gebruikt aangezien het toegang tot de volledige /content boom heeft.</p> <p>Dit is geen ingebouwde gebruiker, maar een andere geometrixx demogebruiker</p> </td>
   <td><p>Adobe raadt u aan het account volledig te verwijderen of het wachtwoord in te stellen op de standaardwaarden.</p> <p>Bij voorkeur na installatie, maar achteraf.</p> </td>
  </tr>
  <tr>
   <td>beheerders</td>
   <td>Groeperen</td>
   <td><p>Groep die beheerderrechten aan al zijn leden geeft. Alleen beheerders mogen deze groep bewerken.</p> <p>Heeft volledige toegangsrechten.</p> </td>
   <td>Als u "ontkent-iedereen"op een knoop plaatst, zullen de beheerders slechts toegang hebben als het opnieuw voor die groep wordt toegelaten.</td>
  </tr>
  <tr>
   <td>content-authors</td>
   <td>Groeperen</td>
   <td><p>Groep die verantwoordelijk is voor het bewerken van inhoud. Vereist machtigingen voor lezen, wijzigen, maken en verwijderen.</p> </td>
   <td>U kunt uw eigen groep(en) van inhoudauteurs maken met projectspecifieke toegangsrechten, op voorwaarde dat u machtigingen voor lezen, wijzigen, maken en verwijderen toevoegt.</td>
  </tr>
  <tr>
   <td>contribuant</td>
   <td>Groeperen</td>
   <td><p>Basisrechten waarmee de gebruiker inhoud kan schrijven (zoals alleen in functionaliteit).</p> <p>Wijst geen voorrechten aan de /content boom toe - deze moeten specifiek voor de individuele groepen of de gebruikers worden toegewezen.</p> </td>
   <td> </td>
  </tr>
  <tr>
   <td>stuwdammen</td>
   <td>Groeperen</td>
   <td>Buiten-de-doos verwijzingsgroep voor een typische gebruiker van AEM Assets. Leden van deze groep hebben de juiste rechten om het uploaden/delen van elementen en verzamelingen mogelijk te maken.</td>
   <td> </td>
  </tr>
  <tr>
   <td>iedereen</td>
   <td>Groeperen</td>
   <td><p>Elke gebruiker in AEM is een lid van de groep iedereen, hoewel u de groep of de lidmaatschapsverhouding in alle hulpmiddelen niet kunt zien.</p> <p>Deze groep kan als standaardrechten worden beschouwd aangezien het kan worden gebruikt om toestemmingen voor iedereen, zelfs gebruikers toe te passen die in de toekomst zullen worden gecreeerd.</p> </td>
   <td><p>Wijzig of verwijder deze groep niet.</p> <p>Het wijzigen van deze account heeft extra gevolgen voor de beveiliging.</p> </td>
  </tr>
  <tr>
   <td>tagbeheerders</td>
   <td>Groeperen</td>
   <td>Groep die tags mag bewerken.</td>
   <td> </td>
  </tr>
  <tr>
   <td>gebruikersbeheerders</td>
   <td>Groeperen</td>
   <td>Hiermee wordt gebruikersbeheer toegestaan, dat wil zeggen het recht om gebruikers en groepen te maken.</td>
   <td> </td>
  </tr>
  <tr>
   <td>workfloweditors</td>
   <td>Groeperen</td>
   <td>Groep die workflowmodellen mag maken en wijzigen.</td>
   <td> </td>
  </tr>
  <tr>
   <td>workflowgebruikers</td>
   <td>Groeperen</td>
   <td><p>Een gebruiker die deelneemt aan een workflow moet lid zijn van een groepswerkstroom-gebruiker. Dit geeft hem of haar volledige toegang tot: /etc/workflow/varianten zodat hij of zij de instantie van de workflow kan bijwerken.</p> <p>De groep is opgenomen in de standaardinstallatie, maar u moet de gebruikers handmatig aan de groep toevoegen.</p> </td>
  </tr>
 </tbody>
</table>

## Machtigingen in AEM {#permissions-in-aem}

AEM gebruikt ACLs om te bepalen welke acties een gebruiker of een groep en kan nemen en waar het die acties kan uitvoeren.

### Machtigingen en ACL&#39;s {#permissions-and-acls}

De toestemmingen bepalen wie wordt toegestaan om welke acties op een middel uit te voeren. De toestemmingen zijn het resultaat van [toegangsbeheerevaluaties](#access-control-lists-and-how-they-are-evaluated) .

U kunt de toestemmingen veranderen die aan een bepaalde gebruiker worden verleend/ontkend door checkboxes voor de individuele [acties](security.md#actions)te selecteren of te ontruimen AEM. Een vinkje geeft aan dat een handeling is toegestaan. Geen vinkje geeft aan dat een handeling wordt geweigerd.

Wanneer het vinkje zich in het raster bevindt, geeft dit ook aan welke machtigingen gebruikers hebben op welke locaties binnen AEM (welke paden).

### Acties {#actions}

Handelingen kunnen worden uitgevoerd op een pagina (bron). Voor elke pagina in de hiërarchie kunt u opgeven welke actie de gebruiker mag uitvoeren op die pagina. [De toestemmingen](#permissions-and-acls) laten u toe om een actie toe te staan of te ontkennen.

<table>
 <tbody>
  <tr>
   <td><strong>Actie </strong></td>
   <td><strong>Beschrijving </strong></td>
  </tr>
  <tr>
   <td>Lezen</td>
   <td>De gebruiker mag de pagina en eventuele onderliggende pagina's lezen.</td>
  </tr>
  <tr>
   <td>Wijzigen</td>
   <td><p>De gebruiker kan:</p>
    <ul>
     <li>bestaande inhoud op de pagina en op onderliggende pagina's wijzigen.</li>
     <li>nieuwe alinea's op de pagina of op een onderliggende pagina maken.</li>
    </ul> <p>Op het niveau JCR, kunnen de gebruikers een middel wijzigen door zijn eigenschappen, het sluiten, het versioning, niet-wijzigingen te wijzigen, en zij hebben volledige schrijftoestemming op knopen die een jcr:content kindknoop, bijvoorbeeld cq:Page, nt:file, cq:Asset bepalen.</p> </td>
  </tr>
  <tr>
   <td>Maken</td>
   <td><p>De gebruiker kan:</p>
    <ul>
     <li>Maak een nieuwe pagina of onderliggende pagina.</li>
    </ul> <p>Als <strong>wijzigen</strong> wordt geweigerd, worden de substructuren onder jcr:content specifiek uitgesloten, omdat het maken van jcr:content en de onderliggende knooppunten ervan als een wijziging van de pagina worden beschouwd. Dit geldt alleen voor knooppunten die een onderliggende node jcr:content definiëren.</p> </td>
  </tr>
  <tr>
   <td>Verwijderen</td>
   <td><p>De gebruiker kan:</p>
    <ul>
     <li>bestaande alinea's van de pagina of een onderliggende pagina verwijderen.</li>
     <li>een pagina of onderliggende pagina verwijderen.</li>
    </ul> <p>Als <strong>wijzigen</strong> wordt geweigerd worden om het even welke subbomen onder jcr:inhoud specifiek uitgesloten zoals het verwijderen van jcr:inhoud en zijn kindknopen wordt beschouwd als een paginawijziging. Dit geldt alleen voor knooppunten die een onderliggende node jcr:content definiëren.</p> </td>
  </tr>
  <tr>
   <td>ACL lezen</td>
   <td>De gebruiker kan de toegangsbeheerlijst van de pagina of kindpagina's lezen.</td>
  </tr>
  <tr>
   <td>ACL bewerken</td>
   <td>De gebruiker kan de toegangsbeheerlijst van de pagina of om het even welke kindpagina's wijzigen.</td>
  </tr>
  <tr>
   <td>Repliceren</td>
   <td>De gebruiker kan inhoud naar een andere omgeving (bijvoorbeeld de omgeving Publiceren) repliceren. Het voorrecht wordt ook toegepast op onderliggende pagina's.</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>AEM genereert automatisch gebruikersgroepen voor rollentoewijzing (Eigenaar, Editor, Viewer) in [Verzamelingen](/help/assets/managing-collections-touch-ui.md). Nochtans, kan manueel het toevoegen van ACLs voor dergelijke groepen veiligheidskwetsbaarheid binnen AEM introduceren. Adobe raadt u aan ACL&#39;s niet handmatig toe te voegen.

### De Lijsten van het Toegangsbeheer en hoe zij worden geëvalueerd {#access-control-lists-and-how-they-are-evaluated}

AEM WCM gebruikt de Lijsten van het Toegangsbeheer (ACLs) om de toestemmingen te organiseren die op de diverse pagina&#39;s worden toegepast.

De Lijsten van het Toegangsbeheer worden samengesteld uit de individuele toestemmingen en worden gebruikt om de orde te bepalen waarin deze toestemmingen eigenlijk worden toegepast. De lijst wordt gevormd volgens de hiërarchie van de pagina&#39;s in kwestie. Deze lijst wordt vervolgens van beneden naar boven gescand totdat de eerste juiste machtiging voor het toepassen op een pagina is gevonden.

>[!NOTE]
>
>Er zijn ACLs die met de steekproeven inbegrepen zijn. U wordt aangeraden te controleren en te bepalen wat geschikt is voor uw toepassingen. Om ACLs te herzien die inbegrepen zijn, ga naar **CRXDE **en selecteer het lusje van het Controle **van de** Toegang voor de volgende knopen:
>
>`/etc/cloudservices/facebookconnect/geometrixx-outdoorsfacebookapp`: Hiermee kan iedereen toegang lezen.
>`/etc/cloudservices/twitterconnect/geometrixx-outdoors-twitter-app`: Hiermee kan iedereen toegang lezen.
>`/home/users/geometrixx-outdoors`: Hiermee kan iedereen toegang lezen voor `*/profile*` en
>`*/social/relationships/following/*`.
>
>Uw aangepaste toepassing kan toegang instellen voor andere relaties, zoals `*/social/relationships/friend/*` of `*/social/relationships/pending-following/*`.
>
>Wanneer u ACLs specifiek voor gemeenschappen creeert, kunnen de leden die die gemeenschappen aansluiten bij extra toestemmingen worden verleend. Dit kan bijvoorbeeld het geval zijn wanneer gebruikers zich bij `/content/geometrixx-outdoors/en/community/hiking` of `/content/geometrixx-outdoors/en/community/winter-sports`.

### Machtigingsstaten {#permission-states}

>[!NOTE]
>
>Voor gebruikers van CQ 5.3:
>
>In tegenstelling tot eerdere CQ-versies, **mag het maken** en **verwijderen** niet langer worden toegestaan als een gebruiker alleen pagina&#39;s hoeft te wijzigen. Geef in plaats daarvan de actie **modify** alleen toe als u wilt dat gebruikers componenten op bestaande pagina&#39;s kunnen maken, wijzigen of verwijderen.
>
>Om achterwaartse compatibiliteitsredenen wordt bij de tests voor acties geen rekening gehouden met de speciale behandeling van knooppunten die **jcr:content** definiëren.

| **Actie** | **Beschrijving** |
|---|---|
| Toestaan (vinkje) | Met AEM WCM kan de gebruiker de handeling op deze pagina of op onderliggende pagina&#39;s uitvoeren. |
| Weigeren (geen vinkje) | Met AEM WCM kan de gebruiker de handeling niet uitvoeren op deze pagina of op onderliggende pagina&#39;s. |

De machtigingen worden ook toegepast op onderliggende pagina&#39;s.

Als een toestemming niet van de ouderknoop wordt geërft maar minstens één lokaal ingang voor het heeft, dan worden de volgende symbolen toegevoegd aan de controledoos. Een lokale ingang is één die in de interface CRX 2.2 wordt gecreeerd (De vervanging ACLs kan momenteel slechts in CRX worden gecreeerd.)

Voor een handeling op een bepaald pad:

<table>
 <tbody>
  <tr>
   <td>* (sterretje)</td>
   <td>Er is minstens één lokale ingang (of effectief of ineffectief). Deze vervangingsACLs wordt bepaald in CRX.</td>
  </tr>
  <tr>
   <td>! (uitroepteken)</td>
   <td>Er is ten minste één item dat momenteel geen effect heeft.</td>
  </tr>
 </tbody>
</table>

Als u de cursor boven een sterretje of uitroepteken houdt, ziet u knopinfo met meer informatie over de opgegeven vermeldingen. De knopinfo bestaat uit twee delen:

<table>
 <tbody>
  <tr>
   <td>Bovenste deel</td>
   <td><p>Hier worden de effectieve vermeldingen weergegeven.</p> </td>
  </tr>
  <tr>
   <td>Onderste deel</td>
   <td>Maakt een lijst van de noneffective ingangen die een effect elders in de boom (zoals die door een speciaal kenmerk wordt vermeld aanwezig met overeenkomstige ACE die het werkingsgebied van de ingang beperken) kunnen hebben. Dit is ook een item waarvan het effect is ingetrokken door een andere vermelding die op het opgegeven pad of op een voorouderknooppunt is gedefinieerd.</td>
  </tr>
 </tbody>
</table>

![chlimage_1-112](assets/chlimage_1-112.png)

>[!NOTE]
>
>Als er geen machtigingen zijn gedefinieerd voor een pagina, worden alle handelingen geweigerd.

Hieronder volgen aanbevelingen voor het beheren van toegangsbeheerlijsten:

* Wijs de machtigingen niet rechtstreeks toe aan gebruikers. Alleen aan groepen toewijzen.

   Dit zal het onderhoud vereenvoudigen, aangezien het aantal groepen veel kleiner is dan het aantal gebruikers, en ook minder volatiel.

* Als u wilt dat een groep/gebruiker pagina&#39;s alleen kan wijzigen, geeft u deze geen rechten. Hiermee geeft u ze alleen bewerkings- en leesrechten.
* Maak spaarzaam gebruik van Weigeren. Gebruik voor zover mogelijk alleen toestaan.

   Het gebruiken ontkent kan onverwachte gevolgen veroorzaken als de toestemmingen in een verschillende orde worden toegepast dan de verwachte orde. Als een gebruiker lid is van meer dan één groep, kunnen de Weigeren verklaringen van één groep de Allow verklaring van een andere groep of vice versa annuleren. Het is moeilijk om een overzicht te houden wanneer dit gebeurt en kan gemakkelijk tot onvoorziene resultaten leiden, terwijl Toewijzingen toestaan dergelijke conflicten niet veroorzaakt.

   Adobe raadt u aan om met Allow te werken in plaats van Deny de [Beste praktijken](#best-practices)te zien.

Voordat u een van beide machtigingen wijzigt, moet u weten hoe deze werken en hoe ze elkaar beïnvloeden. Raadpleeg de CRX-documentatie om te illustreren hoe AEM WCM toegangsrechten [en voorbeelden](/help/sites-administering/user-group-ac-admin.md#how-access-rights-are-evaluated) evalueert bij het instellen van toegangsbeheerlijsten.

### Machtigingen {#permissions}

Rechten geven gebruikers en groepen toegang tot AEM-functionaliteit op AEM-pagina&#39;s.

U bladert toestemmingen door weg door de knopen uit te breiden/samen te vouwen en u kunt de toestemmingsovererving tot de wortelknoop volgen.

U staat of ontkent toestemmingen toe door de aangewezen controledozen te selecteren of te ontruimen.

![cqsecuritypermissionstab](assets/cqsecuritypermissionstab.png)

### Gedetailleerde machtigingsgegevens weergeven {#viewing-detailed-permission-information}

Naast de rasterweergave biedt AEM een gedetailleerde weergave van machtigingen voor een geselecteerde gebruiker/groep op een bepaald pad. De detailweergave bevat aanvullende informatie.

Naast het bekijken van informatie, kunt u de huidige gebruiker of de groep van een groep ook omvatten of uitsluiten. Zie Gebruikers of groepen [toevoegen tijdens het toevoegen van machtigingen](#adding-users-or-groups-while-adding-permissions). Wijzigingen die u hier aanbrengt, worden direct doorgevoerd in het bovenste gedeelte van de gedetailleerde weergave.

U opent de detailweergave door op het tabblad **Machtigingen** op **Details** voor een geselecteerde groep/gebruiker en een geselecteerd pad te klikken.

![permissionetails](assets/permissiondetails.png)

Details worden in twee delen opgesplitst:

<table>
 <tbody>
  <tr>
   <td>Bovenste deel</td>
   <td><p>Hiermee herhaalt u de informatie die u in het structuurraster ziet. Voor elke actie, toont een pictogram of de actie wordt toegestaan of ontkend:</p>
    <ul>
     <li>geen pictogram = geen gedeclareerd item</li>
     <li>(tik) = gedeclareerde actie (allow)</li>
     <li>(-) = gedeclareerde actie (weigeren)</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Onderste deel</td>
   <td><p>Hiermee geeft u het raster weer van gebruikers en groepen die het volgende doen:</p>
    <ul>
     <li>Declareert een ingang voor de bepaalde weg AND</li>
     <li>Is de gegeven toegelaten OF een groep?</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

### Een andere gebruiker imiteren {#impersonating-another-user}

Met de functie [Imiteren](/help/sites-authoring/user-properties.md#user-settings) kan een gebruiker namens een andere gebruiker werken.

Dit betekent dat een gebruikersaccount andere accounts kan opgeven die met hun account kunnen werken. Met andere woorden, als gebruiker-B wordt toegestaan om gebruiker-A na te bootsen, dan kan gebruiker-B acties nemen gebruikend de volledige rekeningsdetails van gebruiker-A.

Hierdoor kunnen imitatoraccounts taken uitvoeren alsof ze de account gebruiken die ze nadoen. bijvoorbeeld tijdens afwezigheid of om een buitensporige last op korte termijn te delen.

>[!NOTE]
>
>Voor het nadoen van werken voor gebruikers die geen beheerder zijn, moet de imitator (in het bovenstaande geval gebruiker-B) beschikken over de machtiging LEZEN in het `/home/users` pad.
>
>Zie [Machtigingen in AEM](/help/sites-administering/security.md#permissions-in-aem)voor meer informatie over hoe u dit kunt bereiken.

>[!CAUTION]
>
>Als een account zich als een ander imiteert, is het erg moeilijk te zien. Een ingang wordt gemaakt in het controlelogboek wanneer de imitatie begint en beëindigt, maar de andere logboekdossiers (zoals het toegangslogboek) houden geen informatie over het feit dat de imitatie op de gebeurtenissen is voorgekomen. Dus als user-B zich gebruiker-A imiteert zullen alle gebeurtenissen kijken alsof zij door gebruiker-A persoonlijk werden uitgevoerd.

>[!CAUTION]
>
>U kunt een pagina vergrendelen wanneer u een gebruiker imiteert. Een pagina die op deze manier is vergrendeld, kan echter alleen dan worden ontgrendeld als de gebruiker die zich heeft voorgedaan of als een gebruiker met beheerdersrechten.
>
>De pagina&#39;s kunnen niet worden ontgrendeld door zich als de gebruiker voor te doen die de pagina heeft vergrendeld.

### Best practices voor {#best-practices}

Hieronder worden de aanbevolen procedures beschreven wanneer u werkt met machtigingen en bevoegdheden:

| Regel | Reden |
|--- |--- |
| *Groepen gebruiken* | Vermijd het toewijzen van toegangsrechten per gebruiker. Hiervoor zijn verschillende redenen:<ul><li>U hebt veel meer gebruikers dan groepen, zodat vereenvoudigen de groepen de structuur.</li><li>Groepen bieden een overzicht van alle accounts.</li> <li>Overerving is eenvoudiger bij groepen.</li><li>Gebruikers komen en gaan. Groepen zijn langdurig.</li></ul> |
| *Positief* | Gebruik altijd Instructies toestaan om de rechten van de groep op te geven (waar mogelijk). Vermijd het gebruik van een Deny-instructie. Groepen worden op volgorde geëvalueerd en de volgorde kan per gebruiker anders worden gedefinieerd. Met andere woorden: U hebt wellicht weinig controle over de volgorde waarin de instructies worden geïmplementeerd en geëvalueerd. Als u alleen Instructies toestaan gebruikt, is de volgorde niet van belang. |
| *Eenvoudig houden* | Het investeren van wat tijd en gedachte wanneer het vormen van een nieuwe installatie zal goed worden terugbetaald. Door een duidelijke structuur toe te passen, wordt het permanente onderhoud en de administratie vereenvoudigd, zodat zowel uw huidige collega&#39;s als toekomstige opvolgers gemakkelijk kunnen begrijpen wat er wordt geïmplementeerd. |
| *Testen* | Gebruik een testinstallatie om te oefenen en ervoor te zorgen dat u de relaties tussen de verschillende gebruikers en groepen begrijpt. |
| *Standaardgebruikers/groepen* | Werk de standaardgebruikers en -groepen altijd direct na de installatie bij om beveiligingsproblemen te voorkomen. |

## Managing Users and Groups {#managing-users-and-groups}

De gebruikers omvatten mensen die het systeem gebruiken en buitenlandse systemen die verzoeken aan het systeem indienen.

Een groep is een set gebruikers.

Beide kunnen worden gevormd gebruikend de functionaliteit van het Beleid van de Gebruiker binnen de Console van de Veiligheid.

### Toegang tot gebruikersbeheer via de beveiligingsconsole {#accessing-user-administration-with-the-security-console}

Met de beveiligingsconsole hebt u toegang tot alle gebruikers, groepen en bijbehorende machtigingen. Alle in deze sectie beschreven procedures worden uitgevoerd in dit venster.

Voer een van de volgende handelingen uit om toegang te krijgen tot de AEM WCM-beveiliging:

* Klik in het welkomstscherm of op verschillende locaties in AEM op het beveiligingspictogram:

![](do-not-localize/wcmtoolbar.png)

* Navigeer rechtstreeks naar `https://<server>:<port>/useradmin`. Zorg ervoor dat u zich als beheerder aanmeldt bij AEM.

Het volgende venster wordt weergegeven:

![cqsecurityypage](assets/cqsecuritypage.png)

In de linkerstructuur worden alle gebruikers en groepen weergegeven die zich momenteel in het systeem bevinden. U kunt de kolommen selecteren die u wilt weergeven, de inhoud van de kolommen sorteren en zelfs de volgorde wijzigen waarin de kolommen worden weergegeven door de kolomkop naar een nieuwe positie te slepen.

![cqsecurityColumnContext](assets/cqsecuritycolumncontext.png)

De tabbladen bieden toegang tot verschillende configuraties:

<!-- ??? in table below. -->

| Tab | Beschrijving |
|--- |--- |
| Filter, vak | Een mechanisme voor het filteren van de vermelde gebruikers en/of groepen. Zie Gebruikers en groepen [filteren](#filtering-users-and-groups). |
| Gebruikers verbergen | Een schakeloptie die alle vermelde gebruikers verbergt, waarbij alleen groepen overblijven. Zie [Gebruikers en groepen](#hiding-users-and-groups)verbergen. |
| Groepen verbergen | Een schakeloptie die alle vermelde groepen verbergt, waarbij alleen gebruikers blijven staan. Zie [Gebruikers en groepen](#hiding-users-and-groups)verbergen. |
| Bewerken | Een menu waarmee u gebruikers of groepen kunt maken en verwijderen en waarmee u deze kunt activeren en deactiveren. Zie [Gebruikers en groepen](#creating-users-and-groups) maken en Gebruikers en groepen [](#deleting-users-and-groups)verwijderen. |
| Eigenschappen | Hier wordt informatie weergegeven over de gebruiker of groep die e-mailgegevens, een beschrijving en naamgegevens kan bevatten. Hiermee kunt u ook het wachtwoord van een gebruiker wijzigen. Zie [Gebruikers en groepen](#creating-users-and-groups)maken, Eigenschappen [van gebruikers en groepen](#modifying-user-and-group-properties) wijzigen en een gebruikerswachtwoord [](#changing-a-user-password)wijzigen. |
| Groepen | Hiermee geeft u alle groepen weer waartoe de geselecteerde gebruiker of groep behoort. U kunt de geselecteerde gebruiker of groepen toewijzen aan extra groepen of deze uit groepen verwijderen. Zie [Groepen](#adding-users-or-groups-to-a-group). |
| Leden | Alleen beschikbaar voor groepen. Hiermee geeft u de leden van een bepaalde groep weer. Zie [Leden](#members-adding-users-or-groups-to-a-group). |
| Machtigingen | U kunt machtigingen toewijzen aan een gebruiker of groep. Hier kunt u het volgende instellen:<ul><li>Machtigingen voor bepaalde pagina&#39;s/knooppunten. Zie Machtigingen [instellen](#setting-permissions). </li><li>Machtigingen voor het maken en verwijderen van pagina&#39;s en wijzigingen in de hiërarchie. ??? Hiermee kunt u rechten [](#settingprivileges)toewijzen, zoals wijzigingen in de hiërarchie, waarmee u pagina&#39;s kunt maken en verwijderen.</li><li>Machtigingen met betrekking tot [replicatiebevoegdheden](#setting-replication-privileges) (gewoonlijk van auteur tot publicatie) volgens een pad.</li></ul> |
| Imitators | Laat een andere gebruiker zich de rekening voorstellen. Nuttig wanneer u een gebruiker nodig hebt om namens een andere gebruiker te handelen. Zie Gebruikers [imiteren](#impersonating-another-user). |
| Voorkeuren | Hiermee stelt u [voorkeuren in voor de groep of gebruiker](#setting-user-and-group-preferences). Bijvoorbeeld taalvoorkeuren. |

### Filtering Users and Groups {#filtering-users-and-groups}

U kunt de lijst filteren door een filterexpressie in te voeren, die alle gebruikers en groepen verbergt die niet overeenkomen met de expressie. U kunt gebruikers en groepen ook verbergen met de knoppen Gebruiker [verbergen en Groep](#hiding-users-and-groups) verbergen.

U kunt als volgt gebruikers of groepen filteren:

1. Typ in de linkerstructuurlijst de filterexpressie in de beschikbare ruimte. Als u bijvoorbeeld **admin** invoert, worden alle gebruikers en groepen met deze tekenreeks weergegeven.
1. Klik op het vergrootglas om de lijst te filteren.

   ![cqsecurityFilter](assets/cqsecurityfilter.png)

1. Klik op de **x** wanneer u alle filters wilt verwijderen.

### Hiding Users and Groups {#hiding-users-and-groups}

Het verbergen van gebruikers of groepen is een andere manier om de lijst met alle gebruikers en groepen in een systeem te filteren. Er zijn twee schakelmechanismen. Als u op Gebruiker verbergen klikt, worden alle gebruikers verborgen en als u op Groepen verbergen klikt, worden alle groepen verborgen (u kunt niet tegelijkertijd zowel gebruikers als groepen verbergen). Zie Gebruikers en groepen [](#filtering-users-and-groups)filteren als u de lijst wilt filteren met een filterexpressie.

Gebruikers en groepen verbergen:

1. Klik in de **beveiligingsconsole** op Gebruikers **** verbergen of Groepen **** verbergen. De geselecteerde knop wordt gemarkeerd weergegeven.

   ![cqsecurityhideusers](assets/cqsecurityhideusers.png)

1. Als u gebruikers of groepen opnieuw wilt weergeven, klikt u nogmaals op de bijbehorende knop.

### Creating Users and Groups {#creating-users-and-groups}

Een nieuwe gebruiker of groep maken:

1. In de lijst van de de consoleboom van de **Veiligheid** , geeft de klik **uit** en dan of **leidt tot Gebruiker** of **tot Groep**.

   ![cqseruityeditcontextmenu](assets/cqseruityeditcontextmenu.png)

1. Voer de vereiste gegevens in, afhankelijk van het feit of u een gebruiker of een groep maakt.

   * Als u Gebruiker **maken selecteert,** voert u de aanmeldings-id, de voornaam en achternaam, het e-mailadres en een wachtwoord in. Standaard maakt AEM een pad op basis van de eerste letter van de achternaam, maar u kunt een ander pad selecteren.
   ![gebruikersdialoogvenster maken](assets/createuserdialog.png)

   * Als u Groep **** maken selecteert, voert u een groep-id en een optionele beschrijving in.
   ![creategroupdialog](assets/creategroupdialog.png)

1. Klik op **Maken**. De gebruiker of groep die u hebt gemaakt, wordt weergegeven in de boomstructuurlijst.

### Deleting Users and Groups {#deleting-users-and-groups}

Een gebruiker of groep verwijderen:

1. Selecteer in de **beveiligingsconsole** de gebruiker of groep die u wilt verwijderen. Als u meerdere items wilt verwijderen, houdt u Shift of Ctrl ingedrukt en klikt u om deze te selecteren.
1. Klik op **Bewerken,** selecteer vervolgens Verwijderen. AEM WCM vraagt of u de gebruiker of de groep wilt schrappen.
1. Klik op **OK** om de handeling te bevestigen of op Annuleren om deze te annuleren.

### Eigenschappen van gebruikers en groepen wijzigen {#modifying-user-and-group-properties}

Gebruikers- en groepseigenschappen wijzigen:

1. Dubbelklik in de **beveiligingsconsole** op de naam van de gebruiker of groep die u wilt wijzigen.

1. Klik op het tabblad **Eigenschappen** , breng de gewenste wijzigingen aan en klik op **Opslaan**.

   ![cqsecurityUserProps](assets/cqsecurityuserprops.png)

>[!NOTE]
>
>Het pad van de gebruiker wordt onder aan de gebruikerseigenschappen weergegeven. Het kan niet worden gewijzigd.

### Gebruikerswachtwoord wijzigen {#changing-a-user-password}

Gebruik de volgende procedure om het wachtwoord van een gebruiker te wijzigen.

>[!NOTE]
>
>U kunt de beveiligingsconsole niet gebruiken om het beheerwachtwoord te wijzigen. Als u het wachtwoord voor de beheerdersaccount wilt wijzigen, gebruikt u de [gebruikersconsole](/help/sites-administering/granite-user-group-admin.md#changing-the-password-for-an-existing-user) die Granite Operations biedt.
>
>Als u AEM Forms gebruikt op JEE, gebruik hieronder geen instructies om wachtwoord te veranderen eerder AEM Forms op JEE admin console (/adminui) gebruiken om het wachtwoord te veranderen.

1. Dubbelklik in de **beveiligingsconsole** op de gebruikersnaam waarvoor u het wachtwoord wilt wijzigen.
1. Klik op het tabblad **Eigenschappen** (als dit tabblad nog niet actief is).
1. Klik op Wachtwoord **** instellen. Het venster Wachtwoord instellen wordt geopend waar u uw wachtwoord kunt wijzigen.

   ![cqsecurityUserPassword](assets/cqsecurityuserpassword.png)

1. Voer het nieuwe wachtwoord tweemaal in; omdat ze niet in duidelijke tekst worden weergegeven , is dit ter bevestiging - als ze niet overeenkomen , geeft het systeem een fout weer .
1. Klik op **Instellen** om het nieuwe wachtwoord voor het account te activeren.

### Gebruikers of groepen toevoegen aan een groep {#adding-users-or-groups-to-a-group}

AEM biedt drie verschillende manieren om gebruikers of groepen toe te voegen aan een bestaande groep:

* Wanneer u zich in de groep bevindt, kunt u leden (gebruikers of groepen) toevoegen.
* Als u lid bent, kunt u leden toevoegen aan groepen.
* Wanneer u aan Toestemmingen werkt, kunt u leden aan groepen toevoegen.

### Groepen - Gebruikers of groepen toevoegen aan een groep {#groups-adding-users-or-groups-to-a-group}

Op het tabblad **Groepen** ziet u tot welke groepen de huidige account behoort. U kunt het gebruiken om de geselecteerde rekening aan een groep toe te voegen:

1. Dubbelklik op de naam van de account (gebruiker of groep) die u aan een groep wilt toewijzen.
1. Klik op het tabblad **Groepen** . Er wordt een lijst weergegeven met groepen waartoe de account al behoort.
1. Klik in de boomstructuurlijst op de naam van de groep die u aan de account wilt toevoegen en sleep deze naar het deelvenster **Groepen** . (Als u meerdere gebruikers wilt toevoegen, houdt u Shift of Ctrl ingedrukt en klikt u op deze namen en sleept u ze.)

   ![cqsecurityaddusertogroup](assets/cqsecurityaddusertogroup.png)

1. Klik op **Opslaan** om de wijzigingen op te slaan.

### Leden - Gebruikers of groepen toevoegen aan een groep {#members-adding-users-or-groups-to-a-group}

Het tabblad **Leden** werkt alleen voor groepen en toont u welke gebruikers en groepen tot de huidige groep behoren. U kunt hiermee accounts toevoegen aan een groep:

1. Dubbelklik op de naam van de groep waaraan u leden wilt toevoegen.
1. Klik op het tabblad **Leden** . Er wordt een lijst weergegeven met leden die al tot deze groep behoren.
1. Klik in de boomstructuurlijst op de naam van het lid dat u aan de groep wilt toevoegen en sleep het naar het deelvenster **Leden** . (Als u meerdere gebruikers wilt toevoegen, houdt u Shift of Ctrl ingedrukt en klikt u op deze namen en sleept u ze.)

   ![cqsecurityadduserasmember](assets/cqsecurityadduserasmember.png)

1. Klik op **Opslaan** om de wijzigingen op te slaan.

### Gebruikers of groepen toevoegen tijdens het toevoegen van machtigingen {#adding-users-or-groups-while-adding-permissions}

Om leden aan een groep bij in een bepaalde weg toe te voegen:

1. Dubbelklik op de naam van de groep of gebruiker waaraan u gebruikers wilt toevoegen.

1. Klik op het tabblad **Machtigingen** .

1. Navigeer naar het pad waaraan u machtigingen wilt toevoegen en klik op **Details**. Het onderste gedeelte van het detailvenster bevat informatie over wie machtigingen heeft voor die pagina.

   ![chlimage_1-113](assets/chlimage_1-113.png)

1. Schakel het selectievakje in de kolom **Lid** in voor de leden die u machtigingen voor dat pad wilt hebben. Schakel het selectievakje voor het lid waarvoor u machtigingen wilt verwijderen uit. In de cel waarin u wijzigingen hebt aangebracht, wordt een rood driehoekje weergegeven.
1. Klik op **OK** om de wijzigingen op te slaan.

### Gebruikers of groepen verwijderen uit groepen {#removing-users-or-groups-from-groups}

AEM biedt drie verschillende manieren om gebruikers of groepen uit een groep te verwijderen:

* In het groepsprofiel kunt u leden (gebruikers of groepen) verwijderen.
* In het lidprofiel kunt u leden uit groepen verwijderen.
* Wanneer u aan Toestemmingen werkt, kunt u leden uit groepen verwijderen.

### Groepen - Gebruikers of groepen verwijderen uit groepen {#groups-removing-users-or-groups-from-groups}

Een gebruiker- of groepsaccount verwijderen uit een groep:

1. Dubbelklik op de naam van de groep of gebruikersaccount die u uit een groep wilt verwijderen.
1. Klik op het tabblad **Groepen** . U ziet tot welke groepen het geselecteerde account behoort.
1. Klik in het deelvenster **Groepen** op de naam van de gebruiker of groep die u uit de groep wilt verwijderen en klik op **Verwijderen**. (Als u meerdere accounts wilt verwijderen, houdt u Shift of Ctrl ingedrukt en klikt u op deze namen en klikt u op **Verwijderen**.)

   ![cqsecurityremoveuserfromgrp](assets/cqsecurityremoveuserfromgrp.png)

1. Klik op **Opslaan** om de wijzigingen op te slaan.

### Leden - Gebruikers of groepen verwijderen uit groepen {#members-removing-users-or-groups-from-groups}

Accounts uit een groep verwijderen:

1. Dubbelklik op de naam van de groep waarvan u de leden wilt verwijderen.
1. Klik op het tabblad **Leden** . Er wordt een lijst weergegeven met leden die al tot deze groep behoren.
1. Klik in het deelvenster **Leden** op de naam van het lid dat u uit de groep wilt verwijderen en klik op **Verwijderen**. (Als u meerdere gebruikers wilt verwijderen, houdt u Shift of Ctrl ingedrukt en klikt u op de desbetreffende namen en klikt u op **Verwijderen**.)

   ![cqsecurityremovemember](assets/cqsecurityremovemember.png)

1. Klik op **Opslaan** om de wijzigingen op te slaan.

### Gebruikers of groepen verwijderen tijdens het toevoegen van machtigingen {#removing-users-or-groups-while-adding-permissions}

Om leden uit een groep bij een bepaalde weg te verwijderen:

1. Dubbelklik op de naam van de groep of gebruiker waarvan u gebruikers wilt verwijderen.

1. Klik op het tabblad **Machtigingen** .

1. Navigeer naar het pad waarnaar u machtigingen wilt verwijderen en klik op **Details**. Het onderste gedeelte van het detailvenster bevat informatie over wie machtigingen heeft voor die pagina.

   ![chlimage_1-114](assets/chlimage_1-114.png)

1. Schakel het selectievakje in de kolom **Lid** in voor de leden die u machtigingen voor dat pad wilt hebben. Schakel het selectievakje voor het lid waarvoor u machtigingen wilt verwijderen uit. In de cel waarin u wijzigingen hebt aangebracht, wordt een rood driehoekje weergegeven.
1. Klik op **OK** om de wijzigingen op te slaan.

### Gebruikerssynchronisatie {#user-synchronization}

Wanneer de plaatsing een [publiceerlandbouwbedrijf](/help/sites-deploying/recommended-deploys.md#tarmk-farm)is, moeten de gebruikers en de groepen onder alle publiceren knopen worden gesynchroniseerd.

Zie [Gebruikerssynchronisatie](/help/sites-administering/sync.md)voor meer informatie over gebruikerssynchronisatie en het inschakelen ervan.

## Machtigingen beheren {#managing-permissions}

>[!NOTE]
>
>Adobe heeft een nieuwe, op Touch UI gebaseerde hoofdweergave voor het beheer van machtigingen geïntroduceerd. Zie [deze pagina](/help/sites-administering/touch-ui-principal-view.md)voor meer informatie over het gebruik ervan.

In deze sectie wordt beschreven hoe u machtigingen kunt instellen, inclusief replicatiebevoegdheden.

### Machtigingen instellen {#setting-permissions}

De toestemmingen staan gebruikers toe om bepaalde acties op middelen bij bepaalde wegen uit te voeren. Het omvat ook de mogelijkheid om pagina&#39;s te maken of te verwijderen.

Machtigingen toevoegen, wijzigen of verwijderen:

1. Dubbelklik in de **beveiligingsconsole** op de naam van de gebruiker of groep die u machtigingen wilt instellen voor of [naar knooppunten](#searching-for-nodes)wilt zoeken.

1. Klik op het tabblad **Machtigingen** .

   ![cquserpermissions](assets/cquserpermissions.png)

1. Schakel in het structuurraster een selectievakje in zodat de geselecteerde gebruiker of groep een handeling kan uitvoeren of een selectievakje kan wissen om te weigeren dat de geselecteerde gebruiker of groep een handeling mag uitvoeren. Klik op **Details** voor meer informatie.

1. Klik op **Opslaan** als u klaar bent.

### Replicatiebevoegdheden instellen {#setting-replication-privileges}

Het replicatievoorrecht is het recht om inhoud te publiceren, en het kan voor groepen en gebruikers worden geplaatst.

>[!NOTE]
>
>* Alle replicatierechten die op een groep worden toegepast, gelden voor alle gebruikers in die groep.
>* De replicatiebevoegdheden van een gebruiker hebben voorrang op de replicatiebevoegdheden van een groep.
>* De Allow replicatierechten hebben een hogere belangrijkheid dan de Deny replicatierechten. Zie [Machtigingen in AEM](#permissions-in-aem) voor meer informatie.
>



Om replicatievoorrechten te plaatsen:

1. Selecteer de gebruiker of de groep in de lijst, dubbelklik om te openen en klik op **Machtigingen**.
1. Navigeer in het raster naar het pad waar u wilt dat de gebruiker over replicatiebevoegdheden beschikt of naar knooppunten [zoekt.](#searching-for-nodes)

1. Selecteer in de kolom **Repliceren** bij het geselecteerde pad een selectievakje om de replicatiebevoegdheid voor die gebruiker of groep toe te voegen of schakel het selectievakje uit om de replicatiebevoegdheid te verwijderen. AEM geeft overal waar u wijzigingen hebt aangebracht een rood driehoekje weer dat nog niet is opgeslagen.

   ![cquserreplicateMachtigingen](assets/cquserreplicatepermissions.png)

1. Klik op **Opslaan** om de wijzigingen op te slaan.

### Zoeken naar knooppunten {#searching-for-nodes}

Wanneer u machtigingen toevoegt of verwijdert, kunt u naar het knooppunt bladeren of zoeken.

Er zijn twee verschillende typen padzoekopdrachten:

* Padzoekopdracht - Als de zoektekenreeks begint met een &quot;/&quot;, zoekt de zoekopdracht naar de directe subknooppunten van het opgegeven pad:

![cqsecuritypathsearch](assets/cqsecuritypathsearch.png)

In het zoekvak kunt u het volgende doen:

| Actie | Wat het doet |
|--- |--- |
| Pijltoets rechts | Hiermee selecteert u een subknooppunt in het zoekresultaat |
| Pijltoets omlaag | Hiermee wordt de zoekopdracht opnieuw gestart. |
| Enter (Return)-toets | Hiermee wordt een subknooppunt geselecteerd en in het treegrid geladen |

* FullText-zoekopdracht - Als de zoektekenreeks niet begint met een &#39;/&#39;, wordt een zoekopdracht met volledige tekst uitgevoerd op alle knooppunten onder het pad &#39;/content&#39;.

![cqsecurityfulltextsearch](assets/cqsecurityfulltextsearch.png)

Een zoekopdracht uitvoeren op paden of volledige tekst:

1. Selecteer een gebruiker of groep in de beveiligingsconsole en klik op het tabblad **Machtigingen** .

1. Voer in het vak Zoeken een zoekterm in.

### Gebruikers imiteren {#impersonating-users}

U kunt één of meerdere gebruikers specificeren die worden toegestaan om zich de huidige gebruiker te verpersoonlijken. Dit betekent dat zij hun accountinstellingen kunnen overschakelen op die van de huidige gebruiker en namens deze gebruiker kunnen handelen.

Gebruik deze functie met voorzichtigheid omdat het gebruikers kan toestaan om acties uit te voeren die hun eigen gebruiker niet kan. Wanneer het nadoen van een gebruiker, worden de gebruikers op de hoogte gebracht dat zij niet als zelf het programma worden geopend.

Er zijn verschillende scenario&#39;s waarin u deze functionaliteit wilt gebruiken, zoals:

* Als u buiten het kantoor bent, kunt u een andere persoon laten nadoen terwijl u weg bent. Door deze functie te gebruiken, kunt u ervoor zorgen dat iemand uw toegangsrechten heeft en u te hoeven om geen gebruikersprofiel te wijzigen of uw wachtwoord uit te geven.
* U kunt het voor het zuiveren doeleinden gebruiken. Bijvoorbeeld, om te zien hoe de Website een gebruiker met beperkte toegangsrechten zoekt. Ook, als een gebruiker over technische problemen klaagt, kunt u zich die gebruiker voorstellen om het probleem te diagnostiseren en te bevestigen.

Een bestaande gebruiker als volgt imiteren:

1. Selecteer in de boomstructuurlijst de naam van de persoon die u aan andere gebruikers wilt toewijzen om zich voor te doen. Dubbelklik om te openen.
1. Klik op het tabblad **Imitators** .
1. Klik op de gebruiker die u als geselecteerde gebruiker wilt kunnen weergeven. Sleep de gebruiker (die zich zal nadoen) van de lijst aan de ruit van de Imitatie. De naam wordt weergegeven in de lijst.

   ![chlimage_1-115](assets/chlimage_1-115.png)

1. Click **Save**.

### Voorkeuren voor gebruikers en groepen instellen {#setting-user-and-group-preferences}

U stelt de gebruikers- en groepsvoorkeuren in, waaronder de taal, het vensterbeheer en de werkbalkvoorkeuren:

1. Selecteer in de linkerstructuur de gebruiker of groep waarvan u de voorkeuren wilt wijzigen. Houd Ctrl of Shift ingedrukt en klik op de gewenste selecties om meerdere gebruikers of groepen te selecteren.
1. Klik op het tabblad **Voorkeuren** .

   ![cqsecurityypreferences](assets/cqsecuritypreferences.png)

1. Breng desgewenst wijzigingen aan in de groep- of gebruikersvoorkeuren en klik op **Opslaan** als u klaar bent.

### Gebruikers of beheerders het recht geven andere gebruikers te beheren {#setting-users-or-administrators-to-have-the-privilege-to-manage-other-users}

Gebruikers of beheerders de rechten geven om andere gebruikers te verwijderen, activeren/deactiveren:

1. Voeg de gebruiker toe u voorrechten wilt geven om andere gebruikers aan de beheerdergroep te beheren en uw veranderingen te bewaren.

   ![cqsecurityaddlidToAdmin](assets/cqsecurityaddmembertoadmin.png)

1. Navigeer op het tabblad **Machtigingen** van de gebruiker naar &quot;/&quot; en in de kolom Repliceren naar het selectievakje voor replicatie op &quot;/&quot; en klik op **Opslaan**.

   ![cqsecurityReplicationMachtigingen](assets/cqsecurityreplicatepermissions.png)

   De geselecteerde gebruiker kan nu gebruikers deactiveren, activeren, verwijderen en maken.

### Bevoegdheden uitbreiden op projectniveau {#extending-privileges-on-a-project-level}

Als u toepassingsspecifieke voorrechten wilt uitvoeren, beschrijft de volgende informatie wat u moet weten om een douanevoorrecht uit te voeren en hoe te om het door CQ af te dwingen:

Het voorrecht van de hiërarchie-wijziging wordt behandeld door een combinatie jcr-voorrechten. Het replicatievoorrecht wordt genoemd **crx:replicate** die samen met andere voorrechten op de jcr bewaarplaats wordt opgeslagen/geëvalueerd. Het wordt echter niet op jcr-niveau gehandhaafd.

De definitie en registratie van aangepaste rechten maakt officieel deel uit van de [Jackrabbit API](https://jackrabbit.apache.org/api/2.8/org/apache/jackrabbit/api/security/authorization/PrivilegeManager.html) vanaf versie 2.4 (zie ook [JCR-2887](https://issues.apache.org/jira/browse/JCR-2887)). Het verdere gebruik valt onder het beheer van de toegangscontrole van het JCR, zoals gedefinieerd in [JSR 283](https://jcp.org/en/jsr/detail?id=283) (afdeling 16). Daarnaast definieert de Jackrabbit API een aantal extensies.

Het mechanisme van de voorrechtregistratie wordt weerspiegeld in UI onder de Configuratie **van de** Bewaarplaats.

De registratie van nieuwe (aangepaste) rechten wordt zelf beschermd door een ingebouwd voorrecht dat moet worden toegekend op het niveau van de opslagplaats (in JCR: Als u &#39;null&#39; doorgeeft als de parameter &#39;absPath&#39; in de ac mgt api, zie jsr 333 voor meer informatie). Door gebrek, hebben **admin** en alle leden van beheerders dat voorrecht verleend.

>[!NOTE]
>
>Hoewel de implementatie zorg draagt voor het valideren en evalueren van aangepaste privileges, kan de implementatie deze niet afdwingen, tenzij het aggregaten van ingebouwde privileges zijn.
