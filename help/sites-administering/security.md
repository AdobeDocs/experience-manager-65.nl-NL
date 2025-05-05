---
title: Gebruikersbeheer en beveiliging
description: Meer informatie over gebruikersbeheer en beveiliging in AEM.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
docset: aem65
exl-id: 53d8c654-8017-4528-a44e-e362d8b59f82
feature: Security
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: 6f3c4f4aa4183552492c6ce5039816896bd67495
workflow-type: tm+mt
source-wordcount: '5412'
ht-degree: 0%

---

# Gebruikersbeheer en beveiliging{#user-administration-and-security}

In dit hoofdstuk wordt beschreven hoe u gebruikersautorisatie configureert en onderhoudt en wordt ook beschreven hoe verificatie en autorisatie in AEM werken.

## Gebruikers en groepen in AEM {#users-and-groups-in-aem}

Deze sectie behandelt de diverse entiteiten en verwante concepten meer in detail om u te helpen een gemakkelijk vormen om gebruikersbeheerconcept te handhaven.

### Gebruikers {#users}

Gebruikers melden zich aan bij AEM account. Elke gebruikersaccount is uniek en bevat de basisaccountgegevens, samen met de toegewezen rechten.

Gebruikers zijn vaak leden van Groepen, waardoor de toewijzing van deze machtigingen en/of bevoegdheden wordt vereenvoudigd.

### Groepen {#groups}

Groepen zijn verzamelingen van gebruikers of andere groepen, of beide. Deze verzamelingen worden allemaal leden van een groep genoemd.

Hun voornaamste doel is het onderhoudsproces te vereenvoudigen door het aantal bij te werken entiteiten te verminderen, aangezien een wijziging van een groep op alle leden van de groep wordt toegepast. Groepen weerspiegelen vaak:

* een rol binnen de toepassing, zoals iemand die de inhoud mag surfen of iemand die inhoud mag toevoegen.
* uw eigen organisatie; u kunt de rollen willen uitbreiden om tussen contribuanten van verschillende afdelingen te onderscheiden wanneer zij tot verschillende takken in de inhoudsboom beperkt zijn.

Groepen blijven daarom over het algemeen stabiel, terwijl gebruikers vaker komen en gaan.

Met planning en een schone structuur kan het gebruik van groepen uw structuur weerspiegelen, waardoor u een duidelijk overzicht krijgt en een efficiënt mechanisme voor updates.

### Ingebouwde gebruikers en groepen {#built-in-users-and-groups}

AEM WCM installeert meerdere gebruikers en groepen. Deze inzamelingen worden gezien wanneer u eerst tot de Console van de Veiligheid na installatie toegang hebt.

In de volgende tabellen wordt elk item vermeld, samen met:

* een korte beschrijving
* eventuele aanbevelingen over noodzakelijke wijzigingen

*Verandering alle standaardwachtwoorden* (als u niet de rekening zelf in bepaalde omstandigheden schrapt).

<table>
 <tbody>
  <tr>
   <td>Gebruikersnaam</td>
   <td>Type</td>
   <td>Beschrijving</td>
   <td>Aanbeveling</td>
  </tr>
  <tr>
   <td><p>admin</p> <p>Standaardwachtwoord: admin</p> </td>
   <td>Gebruiker</td>
   <td><p>Systeembeheeraccount met volledige toegangsrechten.</p> <p>Dit account wordt gebruikt voor de verbinding tussen AEM WCM en CRX.</p> <p>Als u dit account per ongeluk verwijdert, wordt het opnieuw gemaakt nadat de opslagplaats opnieuw is opgestart (in de standaardinstelling).</p> <p>De beheerdersaccount is een vereiste van het AEM platform. Dit betekent dat dit account niet kan worden verwijderd.</p> </td>
   <td><p>Adobe raadt u aan het standaardwachtwoord voor deze gebruikersaccount te wijzigen.</p> <p>Bij voorkeur bij installatie, maar dat kan achteraf gebeuren.</p> <p>Opmerking: verwar dit account niet met de beheerdersaccount van de CQ Servlet Engine.</p> </td>
  </tr>
  <tr>
   <td><p>anoniem</p> <p> </p> </td>
   <td>Gebruiker</td>
   <td><p>Houdt de standaardrechten voor ongeautoriseerde toegang tot een instantie. Per gebrek, bezit deze rekening de minimumtoegangsrechten.</p> <p>Als u dit account per ongeluk verwijdert, wordt het bij het opstarten opnieuw gemaakt. Het kan niet permanent worden geschrapt, maar het kan worden onbruikbaar gemaakt.</p> </td>
   <td>Verwijder of schakel dit account niet uit, omdat dit negatieve gevolgen heeft voor het functioneren van auteur-instanties. Als er beveiligingsvereisten zijn die u verplichten deze te verwijderen, moet u controleren of u de effecten ervan op uw systemen eerst op de juiste wijze test.</td>
  </tr>
  <tr>
   <td><p>auteur</p> <p>Standaardwachtwoord: auteur</p> </td>
   <td>Gebruiker</td>
   <td><p>Een auteursaccount dat naar /content mag schrijven. Omvat contribuant en surfer voorrechten.</p> <p>Kan als webmaster worden gebruikt aangezien het toegang tot de volledige /content boom heeft.</p> <p>Dit account is geen ingebouwde gebruiker, maar een andere demogebruiker van Geometrixx</p> </td>
   <td><p>Adobe raadt aan dat de account volledig wordt verwijderd of dat het standaardwachtwoord wordt gewijzigd.</p> <p>Bij voorkeur bij installatie, maar dat kan achteraf gebeuren.</p> </td>
  </tr>
  <tr>
   <td>beheerders</td>
   <td>Groep</td>
   <td><p>Groep die beheerderrechten aan al zijn leden geeft. Alleen beheerders mogen deze groep bewerken.</p> <p>Heeft volledige toegangsrechten.</p> </td>
   <td>Zelfs als u "ontkent-iedereen"op een knoop plaatst, kunnen de beheerders tot de knoop nog toegang hebben</td>
  </tr>
  <tr>
   <td>content-authors</td>
   <td>Groep</td>
   <td><p>Groep verantwoordelijk voor het bewerken van inhoud. Vereist lees, wijzig, creeer, en schrap toestemmingen.</p> </td>
   <td>U kunt uw eigen tevreden-auteur groepen met project-specifieke toegangsrechten tot stand brengen, op voorwaarde dat u gelezen toevoegt, wijzigt, creeert en, toestemmingen schrapt.</td>
  </tr>
  <tr>
   <td>contribuant</td>
   <td>Groep</td>
   <td><p>Basisrechten waarmee de gebruiker inhoud kan schrijven (zoals in, alleen de rechten die vereist zijn voor de basisfunctionaliteit).</p> <p>Wijst geen voorrechten voor toegang tot de /content boom zelf toe. Deze moeten specifiek worden toegewezen aan de afzonderlijke groepen of gebruikers.</p> </td>
   <td> </td>
  </tr>
  <tr>
   <td>stuwdammen</td>
   <td>Groep</td>
   <td>Buiten-de-doos verwijzingsgroep voor een typische gebruiker van AEM Assets. Leden van deze groep hebben de juiste rechten om het uploaden/delen van elementen en verzamelingen mogelijk te maken.</td>
   <td> </td>
  </tr>
  <tr>
   <td>iedereen</td>
   <td>Groep</td>
   <td><p>Elke gebruiker in AEM is een lid van de groep iedereen, hoewel u de groep of de lidmaatschapsrelatie in alle hulpmiddelen misschien niet ziet.</p> <p>Deze groep kan als standaardrechten worden beschouwd aangezien het kan worden gebruikt om toestemmingen voor iedereen, zelfs gebruikers toe te passen die in de toekomst zullen worden gecreeerd.</p> </td>
   <td><p>Deze groep niet wijzigen of verwijderen.</p> <p>Het wijzigen van deze account heeft extra gevolgen voor de beveiliging.</p> </td>
  </tr>
  <tr>
   <td>tagbeheerders</td>
   <td>Groep</td>
   <td>Groep die tags mag bewerken.</td>
   <td> </td>
  </tr>
  <tr>
   <td>gebruikersbeheerders</td>
   <td>Groep</td>
   <td>Hiermee wordt gebruikersbeheer toegestaan, dat wil zeggen het recht om gebruikers en groepen te maken.</td>
   <td> </td>
  </tr>
  <tr>
   <td>workfloweditors</td>
   <td>Groep</td>
   <td>Groep die workflowmodellen mag maken en wijzigen.</td>
   <td> </td>
  </tr>
  <tr>
   <td>workflowgebruikers</td>
   <td>Groep</td>
   <td><p>Een gebruiker die deelneemt aan een workflow moet lid zijn van een groepswerkstroom-gebruiker. Biedt de gebruiker volledige toegang tot: /etc/workflow/instances zodat deze de werkstroominstantie kunnen bijwerken.</p> <p>De groep is opgenomen in de standaardinstallatie, maar u moet de gebruikers handmatig aan de groep toevoegen.</p> </td>
  </tr>
 </tbody>
</table>

## Machtigingen in AEM {#permissions-in-aem}

AEM gebruikt ACLs om te bepalen welke acties een gebruiker of een groep en kan nemen en waar het die acties kan uitvoeren.

### Machtigingen en ACL&#39;s {#permissions-and-acls}

Machtigingen bepalen wie welke handelingen op een bron kan uitvoeren. De toestemmingen zijn het resultaat van [ toegangsbeheer ](#access-control-lists-and-how-they-are-evaluated) evaluaties.

U kunt de toestemmingen veranderen die aan een bepaalde gebruiker worden verleend/worden ontkend door checkboxes voor de individuele AEM [ acties ](security.md#actions) te selecteren of te ontruimen. Een vinkje geeft aan dat een handeling is toegestaan. Geen vinkje geeft aan dat een handeling wordt geweigerd.

Wanneer het vinkje in het raster staat, geeft dit ook aan welke machtigingen gebruikers hebben op welke locaties binnen AEM (dat wil zeggen, welke paden).

### Handelingen {#actions}

Handelingen kunnen worden uitgevoerd op een pagina (bron). Voor elke pagina in de hiërarchie kunt u opgeven welke actie de gebruiker mag uitvoeren op die pagina. [ Toestemmingen ](#permissions-and-acls) laten u toe om een actie toe te staan of te ontkennen.

<table>
 <tbody>
  <tr>
   <td><strong>Handeling </strong></td>
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
     <li>alinea's maken op de pagina of op een onderliggende pagina.</li>
    </ul> <p>Op JCR-niveau kunnen gebruikers een bron bewerken door de eigenschappen, vergrendeling, versioning, wijzigingen zonder wijzigingen te bewerken. Ze hebben volledige schrijfmachtigingen voor knooppunten die een onderliggende node van jcr:content definiëren. Bijvoorbeeld cq:Page, nt:file, cq:Asset.</p> </td>
  </tr>
  <tr>
   <td>Maken</td>
   <td><p>De gebruiker kan:</p>
    <ul>
     <li>Maak een pagina of onderliggende pagina.</li>
    </ul> <p>Als <strong> wijzigt </strong> wordt ontkend, worden de subbomen onder jcr:inhoud uitgesloten omdat de verwezenlijking van jcr:inhoud en zijn kindknopen als een paginaversie worden beschouwd. Deze regel is alleen van toepassing op knooppunten die een onderliggende node jcr:content definiëren.</p> </td>
  </tr>
  <tr>
   <td>Verwijderen</td>
   <td><p>De gebruiker kan:</p>
    <ul>
     <li>bestaande alinea's van de pagina of een onderliggende pagina verwijderen.</li>
     <li>een pagina of onderliggende pagina verwijderen.</li>
    </ul> <p>Als <strong> wijzigt </strong> wordt ontkend om het even welke subbomen onder jcr:inhoud wordt uitgesloten zoals het verwijderen van jcr:inhoud en zijn kindknopen wordt beschouwd als een paginaversie. Deze regel is alleen van toepassing op knooppunten die een onderliggende node jcr:content definiëren.</p> </td>
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
   <td>De gebruiker kan inhoud naar een andere omgeving (bijvoorbeeld de Publish-omgeving) kopiëren. Het voorrecht wordt ook toegepast op onderliggende pagina's.</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>AEM produceert automatisch gebruikersgroepen voor rol-taak (Eigenaar, Redacteur, Kijker) in [ Inzamelingen ](/help/assets/manage-collections.md). Nochtans, kan manueel het toevoegen van ACLs voor dergelijke groepen veiligheidskwetsbaarheid binnen AEM introduceren. De Adobe adviseert dat u vermijdt manueel toevoegend ACLs.

### De Lijsten van het Toegangsbeheer en hoe zij worden geëvalueerd {#access-control-lists-and-how-they-are-evaluated}

AEM WCM gebruikt de Lijsten van het Toegangsbeheer (ACLs) om de toestemmingen te organiseren die op de diverse pagina&#39;s worden toegepast.

De Lijsten van het Toegangsbeheer worden samengesteld uit de individuele toestemmingen en worden gebruikt om de orde te bepalen waarin deze toestemmingen worden toegepast. De lijst wordt gevormd volgens de hiërarchie van de pagina&#39;s in kwestie. Deze lijst wordt vervolgens van beneden naar boven gescand totdat de eerste juiste machtiging voor het toepassen op een pagina is gevonden.

>[!NOTE]
>
>Er zijn ACLs die met de steekproeven inbegrepen zijn. U wordt aangeraden te controleren en te bepalen wat geschikt is voor uw toepassingen. Om ACLs te herzien die inbegrepen zijn, ga naar **CRXDE** en selecteer het **lusje van het Toegangsbeheer** voor de volgende knopen:
>
>* `/etc/cloudservices`
>* `/home/users/we-retail`
>
>Uw aangepaste toepassing kan toegang instellen voor andere relaties, zoals:
>
>* `*/social/relationships/friend/*`
>* of `*/social/relationships/pending-following/*` .
>
>Wanneer u ACLs specifiek voor gemeenschappen creeert, kunnen de leden die die gemeenschappen aansluiten bij extra toestemmingen worden verleend. Bijvoorbeeld wanneer gebruikers zich aansluiten bij de gemeenschappen op: `/content/we-retail/us/en/community`

### Machtigingsstaten {#permission-states}

>[!NOTE]
>
>Voor gebruikers van CQ 5.3:
>
>In tegenstelling tot vorige versies CQ, **creeer** en **schrapt** niet meer zou moeten worden verleend als een gebruiker pagina&#39;s slechts moet wijzigen. In plaats daarvan, geef **wijzigen** actie slechts toe als u gebruikers, componenten op bestaande pagina&#39;s wilt kunnen tot stand brengen wijzigen of schrappen.
>
>Voor achterwaartse verenigbaarheidsredenen, nemen de tests voor acties niet de speciale behandeling van knopen die **jcr bepalen:inhoud** rekening.

| **Actie** | **Beschrijving** |
|---|---|
| Toestaan (vinkje) | AEM WCM staat de gebruiker toe om de actie op deze pagina of op om het even welke kindpagina uit te voeren. |
| Weigeren (geen vinkje) | AEM WCM staat de gebruiker niet toe de actie op deze pagina of op enige kindpagina&#39;s uit te voeren. |

De machtigingen worden ook toegepast op onderliggende pagina&#39;s.

Als een toestemming niet van de ouderknoop wordt geërft maar minstens één lokaal ingang voor het heeft, dan worden de volgende symbolen toegevoegd aan de controledoos. Een lokale ingang is die in CRX 2.2 interface (ACLs van de Vervanging kan momenteel slechts in CRX worden gecreeerd.)

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

Als u de cursor boven een sterretje of uitroepteken houdt, ziet u knopinfo met meer informatie over de gedeclareerde items. De knopinfo bestaat uit twee delen:

<table>
 <tbody>
  <tr>
   <td>Bovenste deel</td>
   <td><p>Hier worden de effectieve vermeldingen weergegeven.</p> </td>
  </tr>
  <tr>
   <td>Onderste deel</td>
   <td>Maakt een lijst van de noneffective ingangen die elders in de boom (zoals die door een speciaal attribuut wordt vermeld aanwezig met overeenkomstige ACE kan beïnvloeden die het werkingsgebied van de ingang beperken). Het is ook een item waarvan het effect wordt ingetrokken door een ander item dat op het opgegeven pad of op een voorouderknooppunt is gedefinieerd.</td>
  </tr>
 </tbody>
</table>

![ chlimage_1-112 ](assets/chlimage_1-112.png)

>[!NOTE]
>
>Als er geen machtigingen zijn gedefinieerd voor een pagina, worden alle handelingen geweigerd.

Hieronder volgen aanbevelingen voor het beheren van toegangsbeheerlijsten:

* Wijs de machtigingen niet rechtstreeks toe aan gebruikers. Wijs deze alleen toe aan groepen.

  Dit vereenvoudigt het onderhoud, aangezien het aantal groepen veel kleiner is dan het aantal gebruikers, en ook minder volatiel.

* Als u wilt dat een groep/gebruiker pagina&#39;s alleen kan wijzigen, geeft u deze geen rechten. Hiermee geeft u ze alleen bewerkings- en leesrechten.
* Maak spaarzaam gebruik van Weigeren. Gebruik voor zover mogelijk alleen toestaan.

  Het gebruiken ontkent kan onverwachte gevolgen veroorzaken als de toestemmingen in een verschillende orde worden toegepast dan de verwachte orde. Als een gebruiker lid is van meer dan één groep, kunnen de Deny-instructies van de ene groep de Allow-instructie van een andere groep annuleren of op de andere manier. Het is moeilijk om een overzicht te houden wanneer zoiets gebeurt en gemakkelijk tot onvoorziene resultaten kan leiden, terwijl Toewijzingen toestaan dergelijke conflicten niet veroorzaakt.

  De Adobe adviseert dat u met toestaat eerder dan ontkent [ Beste praktijken ](#best-practices) ziet.

Voordat u een van beide machtigingen wijzigt, moet u weten hoe deze werken en hoe ze elkaar beïnvloeden. Zie de documentatie van CRX die illustreert hoe AEM WCM [ toegangsrechten ](/help/sites-administering/user-group-ac-admin.md#how-access-rights-are-evaluated) evalueert, en voorbeelden bij de lijsten van de opstellingstoegangscontrole.

### Machtigingen {#permissions}

Rechten geven gebruikers en groepen toegang tot AEM functionaliteit op AEM pagina&#39;s.

U bladert toestemmingen door weg door de knopen uit te breiden/samen te vouwen en u kunt de toestemmingsovererving tot de wortelknoop volgen.

U staat of ontkent toestemmingen toe door de aangewezen controledozen te selecteren of te ontruimen.

![ cqsecurityPermissionstab ](assets/cqsecuritypermissionstab.png)

### Gedetailleerde machtigingsgegevens weergeven {#viewing-detailed-permission-information}

Samen met de rasterweergave biedt AEM een gedetailleerde weergave van machtigingen voor een geselecteerde gebruiker/groep op een bepaald pad. De detailweergave bevat aanvullende informatie.

Naast het bekijken van informatie, kunt u de huidige gebruiker of de groep van een groep ook omvatten of uitsluiten. Zie [ Toevoegend Gebruikers of Groepen terwijl het Toevoegen van Toestemmingen ](#adding-users-or-groups-while-adding-permissions). Wijzigingen die u hier aanbrengt, worden direct doorgevoerd in het bovenste gedeelte van de gedetailleerde weergave.

Om tot de mening van het Detail, in het **lusje van Toestemmingen** toegang te hebben, klik **Details** voor om het even welke geselecteerde groep/gebruiker en weg.

![ permissiondetails ](assets/permissiondetails.png)

Details worden in twee delen opgesplitst:

<table>
 <tbody>
  <tr>
   <td>Bovenste deel</td>
   <td><p>Herhaalt de informatie die u in het boomraster ziet. Voor elke actie, toont een pictogram of de actie wordt toegestaan of ontkend:</p>
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

Met [ imiteert functionaliteit ](/help/sites-authoring/user-properties.md#user-settings), kan een gebruiker namens een andere gebruiker werken.

Een gebruikersaccount kan dus andere accounts opgeven die met hun account kunnen werken. Bijvoorbeeld, als gebruiker-B wordt toegestaan om gebruiker-A te nadoen, dan kan gebruiker-B het gebruiken van de volledige rekeningsdetails van gebruiker-A handelen.

Met deze functie kunnen imitatoraccounts alle taken uitvoeren alsof ze het account gebruiken dat ze nadoen. Bijvoorbeeld tijdens afwezigheid of om een buitensporige last op korte termijn te delen.

>[!NOTE]
>
>Voor het nadoen van werken voor gebruikers die geen beheerder zijn, moet de imitator (in het bovenstaande geval gebruiker-B) beschikken over leesmachtigingen in het `/home/users` -pad.
>
>Zie [ Toestemmingen in AEM ](/help/sites-administering/security.md#permissions-in-aem).

>[!CAUTION]
>
>Als een account zich als een ander account gedraagt, is het moeilijk te zien. Een ingang wordt gemaakt in het controlelogboek wanneer de imitatie begint en beëindigt, maar de andere logboekdossiers (zoals het toegangslogboek) houden geen informatie dat een imitatie op de gebeurtenissen is voorgekomen. Dus, als gebruiker-B zich gebruiker-A imiteert, kijken alle gebeurtenissen alsof gebruiker-A hen uitvoerde.

>[!CAUTION]
>
>U kunt een pagina vergrendelen wanneer u een gebruiker imiteert. Een pagina die op deze manier is vergrendeld, kan echter alleen dan worden ontgrendeld als de gebruiker die zich heeft voorgedaan of als een gebruiker met beheerdersrechten.
>
>Pagina&#39;s kunnen niet worden ontgrendeld door zich voor te doen als de gebruiker die de pagina heeft vergrendeld.

### Aanbevolen procedures {#best-practices}

Hieronder worden de aanbevolen procedures beschreven wanneer u werkt met machtigingen en bevoegdheden:

| Regel | Reden |
|--- |--- |
| *Groepen van het Gebruik* | Vermijd het toewijzen van toegangsrechten per gebruiker. Er zijn verschillende redenen voor dit advies:<ul><li>U hebt veel meer gebruikers dan groepen, zodat vereenvoudigen de groepen de structuur.</li><li>Groepen bieden een overzicht van alle accounts.</li> <li>Overerving is eenvoudiger bij groepen.</li><li>Gebruikers komen en gaan. Groepen zijn langdurig.</li></ul> |
| *ben Positief* | Gebruik altijd Instructies toestaan om de rechten van de groep op te geven (waar mogelijk). Vermijd het gebruik van een Deny-instructie. Groepen worden op volgorde geëvalueerd en de volgorde kan per gebruiker anders worden gedefinieerd. Met andere woorden: u hebt wellicht weinig controle over de volgorde waarin de instructies worden geïmplementeerd en geëvalueerd. Als u alleen Instructies toestaan gebruikt, is de volgorde niet van belang. |
| *houd het Eenvoudig* | Het investeren van wat tijd en gedachte wanneer het vormen van een nieuwe installatie is het waard. Het toepassen van een duidelijke structuur vereenvoudigt het lopende onderhoud en de administratie, die ervoor zorgen dat zowel uw huidige collega&#39;s als toekomstige opvolgers gemakkelijk kunnen begrijpen wat wordt uitgevoerd. |
| *Test* | Gebruik een testinstallatie om te oefenen en ervoor te zorgen dat u de relaties tussen de verschillende gebruikers en groepen begrijpt. |
| *StandaardGebruikers/Groepen* | Werk de standaardgebruikers en -groepen altijd direct na de installatie bij om beveiligingsproblemen te voorkomen. |

## Gebruikers en groepen beheren {#managing-users-and-groups}

De gebruikers omvatten mensen die het systeem gebruiken en buitenlandse systemen die verzoeken aan het systeem indienen.

Een groep is een set gebruikers.

Beide kunnen worden gevormd gebruikend de functionaliteit van het Beleid van de Gebruiker binnen de Console van de Veiligheid.

### Toegang tot gebruikersbeheer via de beveiligingsconsole {#accessing-user-administration-with-the-security-console}

Met de beveiligingsconsole hebt u toegang tot alle gebruikers, groepen en bijbehorende machtigingen. Alle in deze sectie beschreven procedures worden uitgevoerd in dit venster.

Voer een van de volgende handelingen uit om toegang te krijgen tot AEM WCM-beveiliging:

* Klik in het welkomstscherm of op verschillende locaties in AEM op het beveiligingspictogram:

![ AEM het lusje van de Veiligheid WCM ](do-not-localize/wcmtoolbar.png)

* Navigeer rechtstreeks naar `https://<server>:<port>/useradmin` . Zorg ervoor dat u zich als beheerder aanmeldt bij AEM.

Het volgende venster wordt weergegeven:

![ cqsecurityypage ](assets/cqsecuritypage.png)

In de linkerstructuur worden alle gebruikers en groepen weergegeven die zich momenteel in het systeem bevinden. U kunt de kolommen selecteren die u wilt weergeven, de inhoud van de kolommen sorteren en zelfs de volgorde wijzigen waarin de kolommen worden weergegeven door de kolomkop naar een nieuwe positie te slepen.

![ cqsecurityColumnContext ](assets/cqsecuritycolumncontext.png)

De tabbladen bieden toegang tot verschillende configuraties:

<!-- ??? in table below. -->

| Tab | Beschrijving |
|--- |--- |
| Filter, vak | Een mechanisme voor het filteren van de vermelde gebruikers, groepen of beide. Zie [ Filtrerend Gebruikers en Groepen ](#filtering-users-and-groups). |
| Gebruikers verbergen | Een schakeloptie die alle vermelde gebruikers verbergt, waarbij alleen groepen overblijven. Zie [ Hiding Gebruikers en Groepen ](#hiding-users-and-groups). |
| Groepen verbergen | Een schakeloptie die alle vermelde groepen verbergt, waarbij alleen gebruikers blijven staan. Zie [ Hiding Gebruikers en Groepen ](#hiding-users-and-groups). |
| Bewerken | Een menu waarmee u gebruikers of groepen kunt maken en verwijderen en waarmee u deze kunt activeren en deactiveren. Zie [ Creërend Gebruikers en Groepen ](#creating-users-and-groups) en [ het Schrappen van Gebruikers en Groepen ](#deleting-users-and-groups). |
| Eigenschappen | Hier wordt informatie weergegeven over de gebruiker of groep die e-mailgegevens, een beschrijving en naamgegevens kan bevatten. Hiermee kunt u ook het wachtwoord van een gebruiker wijzigen. Zie [ Creërend Gebruikers en Groepen ](#creating-users-and-groups), [ Wijzend Gebruiker en de Eigenschappen van de Groep ](#modifying-user-and-group-properties) en [ Veranderend een Wachtwoord van de Gebruiker ](#changing-a-user-password). |
| Groepen | Hiermee geeft u alle groepen weer waartoe de geselecteerde gebruiker of groep behoort. U kunt de geselecteerde gebruiker of groepen toewijzen aan extra groepen of deze uit groepen verwijderen. Zie [ Groepen ](#adding-users-or-groups-to-a-group). |
| Leden | Alleen beschikbaar voor groepen. Hiermee geeft u de leden van een bepaalde groep weer. Zie [ Leden ](#members-adding-users-or-groups-to-a-group). |
| Machtigingen | U kunt machtigingen toewijzen aan een gebruiker of groep. Hier kunt u het volgende instellen:<ul><li>Machtigingen voor bepaalde pagina&#39;s/knooppunten. Zie [ Plaatsende Toestemmingen ](#setting-permissions). </li><li>Toestemmingen met betrekking tot het creëren van en het schrappen van pagina&#39;s en hiërarchische wijziging. ??? laat u [ voorrechten ](#settingprivileges) toewijzen, zoals hiërarchische wijziging, die u laat tot stand brengen en schrappen pagina&#39;s schrappen,</li><li>Toestemmingen met betrekking tot [ replicatievoorrechten ](#setting-replication-privileges) (gewoonlijk van auteur om te publiceren) volgens een weg.</li></ul> |
| Imitators | Laat een andere gebruiker zich de rekening voorstellen. Nuttig wanneer u een gebruiker nodig hebt om namens een andere gebruiker te handelen. Zie [ het Imiteren Gebruikers ](#impersonating-another-user). |
| Voorkeuren | Plaatst [ voorkeur voor de groep of de gebruiker ](#setting-user-and-group-preferences). Bijvoorbeeld taalvoorkeuren. |

### Gebruikers en groepen filteren {#filtering-users-and-groups}

U kunt de lijst filteren door een filterexpressie in te voeren, die alle gebruikers en groepen verbergt die niet overeenkomen met de expressie. U kunt gebruikers en groepen ook verbergen door de [ knopen van de Groep van de Verbergen van de Gebruiker te gebruiken en van de Groep ](#hiding-users-and-groups) te verbergen.

Om gebruikers of groepen te filteren:

1. Typ in de linkerstructuurlijst de filterexpressie in de beschikbare ruimte. Bijvoorbeeld, die **admin** ingaan toont alle gebruikers en groepen die dit koord bevatten.
1. Klik op het vergrootglas om de lijst te filteren.

   ![ cqsecurityFilter ](assets/cqsecurityfilter.png)

1. Klik **x** wanneer u alle filters wilt verwijderen.

### Gebruikers en groepen verbergen {#hiding-users-and-groups}

Het verbergen van gebruikers of groepen is een andere manier om de lijst met alle gebruikers en groepen in een systeem te filteren. Er zijn twee schakelmechanismen. Als u op Gebruiker verbergen klikt, worden alle gebruikers verborgen en als u op Groepen verbergen klikt, worden alle groepen verborgen (u kunt niet tegelijkertijd zowel gebruikers als groepen verbergen). Om de lijst te filtreren door een filteruitdrukking te gebruiken, zie [ Filtrerend gebruikers en groepen ](#filtering-users-and-groups).

Gebruikers en groepen verbergen:

1. In de **console van de Veiligheid**, klik **de Gebruikers van de Verbergen** of **Verberg Groepen**. De geselecteerde knop wordt gemarkeerd weergegeven.

   ![ cqsecurityhideusers ](assets/cqsecurityhideusers.png)

1. Als u gebruikers of groepen opnieuw wilt weergeven, klikt u nogmaals op de bijbehorende knop.

### Gebruikers en groepen maken {#creating-users-and-groups}

Een gebruiker of groep maken:

1. In de **lijst van de de consoleboom van de Veiligheid** &lbrace;, geeft de klik **&#x200B;**&#x200B;uit en of **leidt tot Gebruiker** of **tot Groep**.

   ![ cqseruityeditcontextmenu ](assets/cqseruityeditcontextmenu.png)

1. Voer de vereiste gegevens in, afhankelijk van het feit of u een gebruiker of een groep maakt.

   * Als u **uitgezocht creeer Gebruiker,** u login identiteitskaart, voornaam en achternaam, e-mailadres en een wachtwoord ingaat. AEM maakt standaard een pad op basis van de eerste letter van de achternaam, maar u kunt een ander pad selecteren.

   ![ creeert gebruikersdialoog ](assets/createuserdialog.png)

   * Als u **selecteert creeer Groep**, gaat u een groep identiteitskaart en een facultatieve beschrijving in.

   ![ creategroupdialog ](assets/creategroupdialog.png)

1. Klik **creëren**. De gebruiker of groep die u hebt gemaakt, wordt weergegeven in de boomstructuurlijst.

### Gebruikers en groepen verwijderen {#deleting-users-and-groups}

Een gebruiker of groep verwijderen:

1. In de **console van de Veiligheid**, selecteer de gebruiker of de groep u wilt schrappen. Als u meerdere items wilt verwijderen, houdt u Shift of Ctrl ingedrukt en klikt u om deze te selecteren.
1. Klik **uitgeven,** dan uitgezocht Schrapping. AEM WCM vraagt of u de gebruiker of de groep wilt schrappen.
1. Klik op **OK** om te bevestigen of te annuleren.

### Eigenschappen van gebruikers en groepen wijzigen {#modifying-user-and-group-properties}

Gebruikers- en groepseigenschappen wijzigen:

1. In de **console van de Veiligheid**, klik de gebruiker of groepsnaam tweemaal u wilt wijzigen.

1. Klik het **lusje van Eigenschappen**, maak de vereiste veranderingen, en klik **sparen**.

   ![ cqsecurityUserProps ](assets/cqsecurityuserprops.png)

>[!NOTE]
>
>Het pad van de gebruiker wordt onder aan de gebruikerseigenschappen weergegeven. Het kan niet worden gewijzigd.

### Gebruikerswachtwoord wijzigen {#changing-a-user-password}

Gebruik de volgende procedure om het wachtwoord van een gebruiker te wijzigen.

>[!NOTE]
>
>U kunt de beveiligingsconsole niet gebruiken om het beheerderswachtwoord te wijzigen. Om het wachtwoord voor de adminrekening te veranderen, gebruik de [ console van Gebruikers ](/help/sites-administering/granite-user-group-admin.md#changing-the-password-for-an-existing-user) die de Verrichtingen van de Graniet verstrekt.
>
>Als u AEM Forms in JEE gebruikt, moet u onderstaande instructies niet gebruiken om het wachtwoord te wijzigen in plaats van AEM Forms op JEE Admin Console (/adminui) te gebruiken om het wachtwoord te wijzigen.

1. In de **console van de Veiligheid**, klik de gebruikersnaam tweemaal u het wachtwoord voor wilt veranderen.
1. Klik het **lusje van Eigenschappen** (als niet reeds actief).
1. Klik **Vastgesteld Wachtwoord**. Het venster Wachtwoord instellen wordt geopend waar u uw wachtwoord kunt wijzigen.

   ![ cqsecurityuserpassword ](assets/cqsecurityuserpassword.png)

1. Voer het nieuwe wachtwoord twee keer in. Aangezien deze niet in duidelijke tekst worden weergegeven, is deze actie ter bevestiging. Als deze niet overeenkomen, wordt er een fout weergegeven in het systeem.
1. Klik **Reeks** om het nieuwe wachtwoord voor de rekening te activeren.

### Gebruikers of groepen toevoegen aan een groep {#adding-users-or-groups-to-a-group}

AEM biedt drie verschillende manieren om gebruikers of groepen aan een bestaande groep toe te voegen:

* Wanneer u zich in de groep bevindt, kunt u leden (gebruikers of groepen) toevoegen.
* Als u lid bent, kunt u leden toevoegen aan groepen.
* Wanneer u aan Toestemmingen werkt, kunt u leden aan groepen toevoegen.

### Groepen - Gebruikers of groepen toevoegen aan een groep {#groups-adding-users-or-groups-to-a-group}

Het **lusje van Groepen** toont u welke groepen de huidige rekening tot behoort. U kunt het gebruiken om de geselecteerde rekening aan een groep toe te voegen:

1. Dubbelklik op de naam van de account (gebruiker of groep) die u aan een groep wilt toewijzen.
1. Klik de **Groepen** tabel. Er wordt een lijst weergegeven met groepen waartoe de account al behoort.
1. In de boomstructuurlijst, klik de naam van de groep u aan de rekening wilt toevoegen en het aan de **ruit van Groepen** slepen. (Als u meerdere gebruikers wilt toevoegen, houdt u Shift of Ctrl ingedrukt en klikt u op deze namen en sleept u ze.)

   ![ cqsecurityaddusertogroup ](assets/cqsecurityaddusertogroup.png)

1. Klik **sparen** om uw veranderingen te bewaren.

### Leden - Gebruikers of groepen toevoegen aan een groep {#members-adding-users-or-groups-to-a-group}

Het **lusje van Leden** werkt slechts voor groepen en toont u welke gebruikers en groepen tot de huidige groep behoren. U kunt hiermee accounts toevoegen aan een groep:

1. Dubbelklik op de naam van de groep waaraan u leden wilt toevoegen.
1. Klik de **Leden** tabel. Er wordt een lijst weergegeven met leden die al tot deze groep behoren.
1. In de boomlijst, klik de naam van het lid u aan de groep wilt toevoegen en het slepen aan de **ruit van Leden**. (Als u meerdere gebruikers wilt toevoegen, houdt u Shift of Ctrl ingedrukt en klikt u op deze namen en sleept u ze.)

   ![ cqsecurityadduserasmember ](assets/cqsecurityadduserasmember.png)

1. Klik **sparen** om uw veranderingen te bewaren.

### Gebruikers of groepen toevoegen tijdens het toevoegen van machtigingen {#adding-users-or-groups-while-adding-permissions}

Om leden aan een groep bij in een bepaalde weg toe te voegen:

1. Dubbelklik op de naam van de groep of gebruiker waaraan u gebruikers wilt toevoegen.

1. Klik de **Toestemmingen** tabel.

1. Navigeer aan de weg die u toestemmingen aan wilt toevoegen en **Details** klikken. Het onderste gedeelte van het detailvenster bevat informatie over wie machtigingen heeft voor die pagina.

   ![ chlimage_1-113 ](assets/chlimage_1-113.png)

1. Selecteer de controledoos in de **1&rbrace; kolom van het Lid &lbrace;voor de leden die u toestemmingen aan die weg wilt hebben.** Schakel het selectievakje uit voor het lid waarvoor u machtigingen wilt verwijderen. Er verschijnt een rood driehoekje in de cel die u hebt gewijzigd.
1. Klik **O.K.** om uw veranderingen te bewaren.

### Gebruikers of groepen verwijderen uit groepen {#removing-users-or-groups-from-groups}

AEM biedt drie verschillende manieren om gebruikers of groepen uit een groep te verwijderen:

* Wanneer u zich in het groepsprofiel bevindt, kunt u leden (gebruikers of groepen) verwijderen.
* Wanneer u zich in het lidprofiel bevindt, kunt u leden uit groepen verwijderen.
* Wanneer u aan Toestemmingen werkt, kunt u leden uit groepen verwijderen.

### Groepen - Gebruikers of groepen verwijderen uit groepen {#groups-removing-users-or-groups-from-groups}

Een gebruiker- of groepsaccount verwijderen uit een groep:

1. Dubbelklik op de naam van de groep of gebruikersaccount die u uit een groep wilt verwijderen.
1. Klik de **Groepen** tabel. U ziet tot welke groepen het geselecteerde account behoort.
1. In de **ruit van Groepen**, klik de naam van de gebruiker of de groep u uit de groep wilt verwijderen en **klikken verwijdert**. (Als u veelvoudige rekeningen wilt verwijderen, Shift+klikken of Control+klikken die namen en **verwijderen** klikken.)

   ![ cqsecurityremoveuserfromgrp ](assets/cqsecurityremoveuserfromgrp.png)

1. Klik **sparen** om uw veranderingen te bewaren.

### Leden - Gebruikers of groepen verwijderen uit groepen {#members-removing-users-or-groups-from-groups}

Accounts uit een groep verwijderen:

1. Dubbelklik op de naam van de groep waarvan u de leden wilt verwijderen.
1. Klik de **Leden** tabel. Er wordt een lijst weergegeven met leden die al tot deze groep behoren.
1. In de **ruit van Leden**, klik de naam van het lid u uit de groep wilt verwijderen en **klikken verwijdert**. (Als u veelvoudige gebruikers wilt verwijderen, Shift+klikken of Control+klikken die namen en **verwijderen** klikken.)

   ![ cqsecurityremovemember ](assets/cqsecurityremovemember.png)

1. Klik **sparen** om uw veranderingen te bewaren.

### Gebruikers of groepen verwijderen tijdens het toevoegen van machtigingen {#removing-users-or-groups-while-adding-permissions}

Om leden uit een groep bij een bepaalde weg te verwijderen:

1. Dubbelklik op de naam van de groep of gebruiker waarvan u gebruikers wilt verwijderen.

1. Klik de **Toestemmingen** tabel.

1. Navigeer aan de weg die u toestemmingen aan wilt verwijderen en **Details** klikken. Het onderste gedeelte van het detailvenster bevat informatie over wie machtigingen heeft voor die pagina.

   ![ chlimage_1-114 ](assets/chlimage_1-114.png)

1. Selecteer de controledoos in de **1&rbrace; kolom van het Lid &lbrace;voor de leden die u toestemmingen aan die weg wilt hebben.** Schakel het selectievakje uit voor het lid waarvoor u machtigingen wilt verwijderen. Er verschijnt een rood driehoekje in de cel die u hebt gewijzigd.
1. Klik **O.K.** om uw veranderingen te bewaren.

### Gebruikerssynchronisatie {#user-synchronization}

Wanneer de plaatsing a [ landbouwbedrijf ](/help/sites-deploying/recommended-deploys.md#tarmk-farm) publiceert, moeten de gebruikers en de groepen onder allen worden gesynchroniseerd publiceren knopen.

Om over gebruikerssynchronisatie te leren en hoe te om het toe te laten, zie [ Synchronisatie van de Gebruiker ](/help/sites-administering/sync.md).

## Machtigingen beheren {#managing-permissions}

>[!NOTE]
>
>De Adobe heeft een nieuwe Touch UI gebaseerde belangrijkste mening voor toestemmingenbeheer geïntroduceerd. Voor meer details op hoe te om het te gebruiken, zie [ Belangrijkste Mening voor het Beheer van Toestemmingen ](/help/sites-administering/touch-ui-principal-view.md).

In deze sectie wordt beschreven hoe u machtigingen kunt instellen, inclusief replicatiebevoegdheden.

### Machtigingen instellen {#setting-permissions}

De toestemmingen staan gebruikers toe om bepaalde acties op middelen bij bepaalde wegen uit te voeren. Het omvat ook de mogelijkheid om pagina&#39;s te maken of te verwijderen.

Machtigingen toevoegen, wijzigen of verwijderen:

1. In de **console van de Veiligheid**, klik de naam van de gebruiker of de groep tweemaal u toestemmingen voor of [ onderzoek naar knopen ](#searching-for-nodes) wilt plaatsen.

1. Klik de **Toestemmingen** tabel.

   ![ cquserpermissions ](assets/cquserpermissions.png)

1. Schakel in het structuurraster een selectievakje in zodat de geselecteerde gebruiker of groep een handeling kan uitvoeren of een selectievakje kan wissen om te weigeren dat de geselecteerde gebruiker of groep een handeling mag uitvoeren. Voor meer informatie klik **Details**.

1. Wanneer gebeëindigd, klik **sparen**.

### Replicatieprivileges instellen {#setting-replication-privileges}

Het replicatievoorrecht is het recht om inhoud te publiceren, en het kan voor groepen en gebruikers worden geplaatst.

>[!NOTE]
>
>* Alle replicatierechten die op een groep worden toegepast, gelden voor alle gebruikers in die groep.
>* De replicatiebevoegdheden van een gebruiker hebben voorrang op de replicatiebevoegdheden van een groep.
>* De Allow replicatierechten hebben een hogere belangrijkheid dan de Deny replicatierechten. Zie [ Toestemmingen in AEM ](#permissions-in-aem) voor meer informatie.
>

Om replicatievoorrechten te plaatsen:

1. Selecteer de gebruiker of de groep van de lijst, klik tweemaal om te openen, en klik **Toestemmingen**.
1. In het net, navigeer aan de weg waar u de gebruiker replicatievoorrechten of [ onderzoek naar knopen wilt hebben.](#searching-for-nodes)

1. In de **Replicate** kolom bij de geselecteerde weg, selecteer een controledoos om het replicatievoorrecht voor die gebruiker of groep toe te voegen, of de controledoos te ontruimen om het replicatievoorrecht te verwijderen. AEM wordt overal waar u wijzigingen hebt aangebracht een rood driehoekje weergegeven dat nog niet is opgeslagen.

   ![ cquserreplicate toestemmingen ](assets/cquserreplicatepermissions.png)

1. Klik **sparen** om uw veranderingen te bewaren.

### Zoeken naar knooppunten {#searching-for-nodes}

Wanneer u machtigingen toevoegt of verwijdert, kunt u naar het knooppunt bladeren of zoeken.

Er zijn twee verschillende typen padzoekopdrachten:

* Padzoekopdracht - Als de zoektekenreeks begint met een &quot;/&quot;, wordt gezocht naar de directe subknooppunten van het opgegeven pad:

![ cqsecurityPathSearch ](assets/cqsecuritypathsearch.png)

In het zoekvak kunt u het volgende doen:

| Handeling | Wat doet het? |
|--- |--- |
| Pijltoets rechts | Hiermee selecteert u een subknooppunt in het zoekresultaat |
| Pijltoets omlaag | Hiermee wordt de zoekopdracht opnieuw gestart. |
| Enter (Return)-toets | Hiermee wordt een subknooppunt geselecteerd en in het structuurraster geladen |

* FullText-zoekopdracht - Als de zoektekenreeks niet begint met een &#39;/&#39;, wordt een zoekopdracht met volledige tekst uitgevoerd op alle knooppunten onder het pad &#39;/content&#39;.

![ cqsecurityfulltextsearch ](assets/cqsecurityfulltextsearch.png)

Een zoekopdracht uitvoeren op paden of volledige tekst:

1. In de console van de Veiligheid, selecteer een gebruiker of een groep en klik dan de **Toestemmingen** tabel.

1. Voer in het vak Zoeken een zoekterm in.

### Gebruikers imiteren {#impersonating-users}

U kunt één of meerdere gebruikers specificeren die worden toegestaan om zich de huidige gebruiker te verpersoonlijken. Deze mogelijkheid betekent dat ze hun accountinstellingen kunnen overschakelen op die van de huidige gebruiker en namens deze gebruiker kunnen handelen.

Gebruik deze functie met voorzichtigheid omdat het gebruikers kan toestaan om acties uit te voeren die hun eigen gebruiker niet kan. Wanneer het nadoen van een gebruiker, worden de gebruikers op de hoogte gebracht dat zij niet als zelf het programma worden geopend.

Er zijn verschillende scenario&#39;s waarin u deze functionaliteit wilt gebruiken, zoals:

* Als u buiten het kantoor bent, kunt u een andere persoon laten nadoen terwijl u weg bent. Door deze functie te gebruiken, kunt u ervoor zorgen dat iemand uw toegangsrechten heeft en u hoeft een gebruikersprofiel niet te wijzigen of uw wachtwoord uit te geven.
* U kunt het voor het zuiveren doeleinden gebruiken. Bijvoorbeeld, om te zien hoe de Website een gebruiker met beperkte toegangsrechten zoekt. Ook, als een gebruiker over technische problemen klaagt, kunt u zich die gebruiker voorstellen om het probleem te diagnostiseren en te bevestigen.

Een bestaande gebruiker als volgt imiteren:

1. Selecteer in de boomstructuurlijst de naam van de persoon die u aan andere gebruikers wilt toewijzen om zich voor te doen. Dubbelklik om te openen.
1. Klik de **imitators** tabel.
1. Klik op de gebruiker die u als geselecteerde gebruiker wilt kunnen weergeven. Sleep de gebruiker (de imitator) van de lijst aan de ruit van de Imitatie. De naam wordt weergegeven in de lijst.

   ![ chlimage_1-115 ](assets/chlimage_1-115.png)

1. Klik **sparen**.

### Voorkeuren voor gebruikers en groepen instellen {#setting-user-and-group-preferences}

U stelt de gebruikers- en groepsvoorkeuren in, waaronder de taal, het vensterbeheer en de werkbalkvoorkeuren:

1. Selecteer in de linkerstructuur de gebruiker of groep waarvan u de voorkeuren wilt wijzigen. Houd Ctrl of Shift ingedrukt en klik op de gewenste selecties om meerdere gebruikers of groepen te selecteren.
1. Klik de **Voorkeur** tabel.

   ![ cqsecurityypreferences ](assets/cqsecuritypreferences.png)

1. Breng veranderingen aan, zonodig aan de groep of gebruikersvoorkeur en klik **sparen** wanneer gebeëindigd.

### Gebruikers of beheerders het recht geven andere gebruikers te beheren {#setting-users-or-administrators-to-have-the-privilege-to-manage-other-users}

Gebruikers of beheerders de rechten geven om andere gebruikers te verwijderen, activeren/deactiveren:

1. Voeg de gebruiker toe die u rechten wilt geven om andere gebruikers te beheren aan de beheerdersgroep en sla uw wijzigingen op.

   ![ cqsecurityAddDomain ](assets/cqsecurityaddmembertoadmin.png)

1. In het 1&rbrace; lusje van de Toestemmingen van de gebruiker **&lbrace;, navigeer aan &quot;/&quot; en in de kolom van de Replicatie, selecteer de controledoos om replicatie bij &quot;/&quot; toe te staan en** te klikken sparen **.**

   ![ cqsecurityReplicatepermissions ](assets/cqsecurityreplicatepermissions.png)

   De geselecteerde gebruiker kan nu gebruikers deactiveren, activeren, verwijderen en maken.

### Bevoegdheden uitbreiden op projectniveau {#extending-privileges-on-a-project-level}

Als u toepassingsspecifieke voorrechten wilt uitvoeren, beschrijft de volgende informatie wat u moet weten om een douanevoorrecht uit te voeren en hoe te om het door CQ af te dwingen:

Het voorrecht van de hiërarchie-wijziging wordt behandeld door een combinatie jcr-voorrechten. Het replicatievoorrecht wordt genoemd **crx:replicate** die samen met andere voorrechten op de jcr bewaarplaats wordt opgeslagen/geëvalueerd. Het wordt echter niet op jcr-niveau gehandhaafd.

De definitie en de registratie van douanevoorrechten zijn officieel deel van [ Slag API ](https://jackrabbit.apache.org/oak/docs/security/privilege.html) vanaf versie 2.4 (zie ook [ JCR-2887 ](https://issues.apache.org/jira/browse/JCR-2887)). Het verdere gebruik wordt behandeld door het Beheer van het Toegangsbeheer JCR zoals die door [ JSR 283 ](https://jcp.org/en/jsr/detail?id=283) wordt bepaald (sectie 16). Daarnaast definieert de Jackrabbit API een aantal extensies.

Het mechanisme van de voorrechtregistratie wordt weerspiegeld in UI onder **Configuratie van de Bewaarplaats**.

De registratie van nieuwe (aangepaste) rechten wordt zelf beveiligd door een ingebouwd voorrecht dat moet worden toegekend op het niveau van de opslagplaats. In JCR: pass &#39;null&#39; as the &#39;absPath&#39; parameter in the ac mgt api, see jsr 333 for details. Door gebrek, **admin** en alle leden van beheerders hebben dat verleende voorrecht.

>[!NOTE]
>
>Hoewel de implementatie zorg draagt voor het valideren en evalueren van aangepaste privileges, kan de implementatie deze niet afdwingen, tenzij het aggregaten van ingebouwde privileges zijn.
