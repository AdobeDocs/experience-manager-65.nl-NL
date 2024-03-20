---
title: Beheer van gebruikers-, groep- en toegangsrechten
description: Meer informatie over gebruikers-, groep- en toegangsrechtenbeheer in Adobe Experience Manager.
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
docset: aem65
exl-id: 5808b8f9-9b37-4970-b5c1-4d33404d3a8b
feature: Security
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '3073'
ht-degree: 0%

---

# Gebruiker, Groep en het Beleid van de Rechten van de Toegang{#user-group-and-access-rights-administration}

Het toelaten van toegang tot een gegevensopslagplaats CRX impliceert verscheidene onderwerpen:

* [Toegangsrechten](#how-access-rights-are-evaluated) - de begrippen hoe zij worden gedefinieerd en geëvalueerd;
* [Gebruikersbeheer](#user-administration) - beheer van de individuele rekeningen die voor toegang worden gebruikt;
* [Groepsbeheer](#group-administration) - gebruikersbeheer vereenvoudigen door groepen te vormen
* [Toegangsbeheer](#access-right-management) - het bepalen van beleid dat controleert hoe deze gebruikers en groepen tot middelen kunnen toegang hebben

De basiselementen zijn:

**Gebruikersaccounts** - CRX verifieert toegang door een gebruiker (door die persoon, of een andere toepassing) te identificeren en te verifiëren volgens details in de gebruikersrekening.

In CRX, is elke gebruikersrekening een knoop in de werkruimte. Een CRX-gebruikersaccount heeft de volgende eigenschappen:

* Eén gebruiker van CRX.
* Deze bevat een gebruikersnaam en wachtwoord.
* Van toepassing op die werkruimte.
* Het kan geen subgebruikers hebben. Voor hiërarchische toegangsrechten, zou u groepen moeten gebruiken.

* U kunt toegangsrechten opgeven voor de gebruikersaccount.

  Om het beheer te vereenvoudigen, beveelt de Adobe echter aan (in de meeste gevallen) toegangsrechten toe te wijzen aan groepsaccounts. Het toewijzen van toegangsrechten voor elke individuele gebruiker wordt snel moeilijk te beheren (de uitzonderingen zijn bepaalde systeemgebruikers wanneer slechts één of twee instanties bestaan).

**Groepsaccounts** - Groepsaccounts zijn verzamelingen van gebruikers en/of andere groepen. Deze worden gebruikt om beheer te vereenvoudigen aangezien een verandering in de toegangsrechten die aan een groep worden toegewezen automatisch op alle gebruikers in die groep wordt toegepast. Een gebruiker hoeft niet tot een groep te behoren, maar behoort vaak tot een groep.

In CRX heeft een groep de volgende eigenschappen:

* Het vertegenwoordigt een groep gebruikers met gemeenschappelijke toegangsrechten. Bijvoorbeeld auteurs of ontwikkelaars.
* Van toepassing op die werkruimte.
* Het kan leden hebben; dit kunnen individuele gebruikers of andere groepen zijn.
* U kunt een hiërarchische groepering maken met lidrelaties. U kunt een groep niet direct onder een andere groep in de repository plaatsen.
* U kunt de toegangsrechten voor alle groepsleden bepalen.

**Toegangsrechten** - CRX gebruikt toegangsrechten om de toegang tot specifieke gebieden van de gegevensopslagplaats te controleren.

Dit wordt gedaan door voorrechten toe te wijzen om of toegang tot een middel (knoop of weg) in de bewaarplaats toe te staan of te ontkennen. Aangezien verschillende voorrechten kunnen worden toegewezen, moeten zij worden geëvalueerd om te bepalen welke combinatie voor het huidige verzoek van toepassing is.

CRX laat u de toegangsrechten voor zowel gebruiker als groepsrekeningen vormen. Vervolgens worden dezelfde basisbeginselen voor de evaluatie toegepast op beide.

## Hoe de Rechten van de Toegang worden geëvalueerd {#how-access-rights-are-evaluated}

>[!NOTE]
>
>CRX-implementaties [toegangsbeheer zoals gedefinieerd in JSR-283](https://developer.adobe.com/experience-manager/reference-materials/spec/jcr/2.0/16_Access_Control_Management.html).
>
>Een standaardinstallatie van een CRX bewaarplaats wordt gevormd om op middel-gebaseerde toegangsbeheerlijsten te gebruiken. Dit is één mogelijke implementatie van JSR-283 toegangsbeheer en één van de implementaties heden met Jackrabbit.

### Onderwerpen en Opdrachten {#subjects-and-principals}

CRX gebruikt twee zeer belangrijke concepten wanneer het evalueren van toegangsrechten:

* A **principal** is een entiteit die toegangsrechten heeft. Belangrijkste punten zijn:

   * Een gebruikersaccount
   * Een groepsaccount

     Als een gebruikersaccount tot een of meer groepen behoort, wordt deze ook aan elk van die groepshoofden gekoppeld.

* A **onderwerp** wordt gebruikt om de bron van een verzoek te vertegenwoordigen.

  Het wordt gebruikt om de toegangsrechten die op dat verzoek van toepassing zijn, te consolideren. Deze zijn afkomstig van:

   * De principal van de gebruiker

     De rechten die u rechtstreeks aan de gebruikersaccount toewijst.

   * Alle groepshoofden verbonden aan die gebruiker

     Alle rechten worden toegewezen aan een van de groepen waartoe de gebruiker behoort.

  Het resultaat wordt dan gebruikt om toegang tot het gevraagde middel toe te staan of te ontkennen.

#### Opstellen van de lijst van toegangsrechten voor een onderwerp {#compiling-the-list-of-access-rights-for-a-subject}

In CRX hangt het onderwerp af van:

* de principal van de gebruiker
* alle groepshoofden die aan die gebruiker worden geassocieerd

De lijst van toegangsrechten die van toepassing zijn op het onderwerp is samengesteld uit:

* de rechten die u rechtstreeks aan de gebruikersaccount toewijst
* plus alle rechten die zijn toegewezen aan een groep waartoe de gebruiker behoort

![chlimage_1-56](assets/chlimage_1-56.png)

>[!NOTE]
>
>* CRX houdt geen rekening met enige gebruikershiërarchie wanneer het de lijst compileert.
>* CRX gebruikt een groepshiërarchie slechts wanneer u een groep als lid van een andere groep omvat. Er is geen automatische overerving van groepsmachtigingen.
>* De volgorde waarin u de groepen opgeeft, heeft geen invloed op de toegangsrechten.
>

### Aanvraag- en toegangsrechten oplossen {#resolving-request-and-access-rights}

Wanneer CRX het verzoek behandelt, vergelijkt het het toegangsverzoek van het onderwerp met de toegangsbeheerlijst op de gegevensopslaggegevensopslagknoop:

Dus als Linda vraagt om de `/features` knooppunt in de volgende repository structuur:

![chlimage_1-57](assets/chlimage_1-57.png)

### Volgorde van voorrang {#order-of-precedence}

Toegangsrechten in CRX worden als volgt beoordeeld:

* De hoofden van de gebruiker nemen altijd belangrijkheid over groepshoofden ongeacht:

   * hun orde in de toegangsbeheerlijst
   * hun positie in de knooppunthiërarchie

* Voor een bepaald hoofd, bestaat er (hoogstens) ontkent en 1 staat ingang op een bepaalde knoop toe. De implementatie ontruimt altijd overtollige ingangen en zorgt ervoor dat het zelfde voorrecht niet in zowel toestaat als ontkent ingangen vermeld is.

>[!NOTE]
>
>Dit evaluatieproces is aangewezen voor het op middel-gebaseerde toegangsbeheer van een standaardCRX installatie.

Twee voorbeelden nemen waarbij de gebruiker `aUser` lid is van de groep `aGroup`:

```xml
   + parentNode
     + acl
       + ace: aUser - deny - write
     + childNode
       + acl
         + ace: aGroup - allow - write
       + grandChildNode
```

In het bovenstaande geval:

* `aUser` geen schrijfmachtiging is verleend op `grandChildNode`.

```xml
   + parentNode
     + acl
       + ace: aUser - deny - write
     + childNode
       + acl
         + ace: aGroup - allow - write
         + ace: aUser - deny - write
       + grandChildNode
```

In dit geval:

* `aUser` geen schrijfmachtiging is verleend op `grandChildNode`.
* De tweede ACE voor `aUser` is overbodig.

De rechten van de toegang van veelvoudige groepshoofden worden geëvalueerd gebaseerd op hun orde, zowel binnen de hiërarchie als binnen één enkele toegangsbeheerlijst.

### Aanbevolen procedures {#best-practices}

In de volgende tabel vindt u een aantal aanbevelingen en aanbevolen procedures:

<table>
 <tbody>
  <tr>
   <td>Aanbeveling..</td>
   <td>Reden...</td>
  </tr>
  <tr>
   <td><i>Groepen gebruiken</i></td>
   <td><p>Vermijd het toewijzen van toegangsrechten per gebruiker. Hiervoor zijn verschillende redenen:</p>
    <ul>
     <li>U hebt veel meer gebruikers dan groepen, zodat vereenvoudigen de groepen de structuur.</li>
     <li>Groepen bieden een overzicht van alle accounts.</li>
     <li>Overerving is eenvoudiger bij groepen.</li>
     <li>Gebruikers komen en gaan. Groepen zijn langdurig.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><i>Positief zijn</i></td>
   <td><p>Gebruik altijd Allow verklaringen om de toegangsrechten van het groepshoofd te specificeren (waar mogelijk). Vermijd het gebruik van een Deny-instructie.</p> <p>De hoofden van de groep worden geëvalueerd in orde, zowel binnen de hiërarchie als orde binnen één enkele toegangsbeheerlijst.</p> </td>
  </tr>
  <tr>
   <td><i>Eenvoudig houden</i></td>
   <td><p>Het investeren van wat tijd en gedachte wanneer het vormen van een nieuwe installatie wordt goed terugbetaald.</p> <p>Het toepassen van een duidelijke structuur vereenvoudigt het doorlopende onderhoud en de administratie, zodat zowel uw huidige collega's als toekomstige opvolgers gemakkelijk kunnen begrijpen wat er wordt geïmplementeerd.</p> </td>
  </tr>
  <tr>
   <td><i>Testen</i></td>
   <td>Gebruik een testinstallatie om te oefenen en ervoor te zorgen dat u de relaties tussen de verschillende gebruikers en groepen begrijpt.</td>
  </tr>
  <tr>
   <td><i>Standaardgebruikers/groepen</i></td>
   <td>Werk de standaardgebruikers en -groepen altijd direct na de installatie bij om beveiligingsproblemen te voorkomen.</td>
  </tr>
 </tbody>
</table>

## Gebruikersbeheer {#user-administration}

Er wordt een standaarddialoogvenster gebruikt voor **Gebruikersbeheer**.

U moet in de aangewezen werkruimte worden geregistreerd, dan kunt u tot de dialoog van allebei toegang hebben:

* de **Gebruikersbeheer** koppeling in de hoofdconsole van CRX
* de **Beveiliging** menu van de CRX Explorer

![chlimage_1-58](assets/chlimage_1-58.png)

**Eigenschappen**

* **GebruikerID**

  De korte naam voor de rekening wordt gebruikt wanneer het toegang tot CRX.

* **Hoofdnaam**

  Een volledige tekstnaam voor het account.

* **Wachtwoord**

  Nodig wanneer u toegang wilt tot CRX met dit account.

* **ntlmhash**

  Automatisch toegewezen voor elke nieuwe account en bijgewerkt wanneer het wachtwoord wordt gewijzigd.

* U kunt nieuwe eigenschappen toevoegen door een naam, type en waarde te definiëren. Klik op Opslaan (groen verdeelstreepje) voor elke nieuwe eigenschap.

**Groepslidmaatschap**

Hiermee worden alle groepen weergegeven waartoe de account behoort. De kolom Overgenomen geeft het lidmaatschap aan dat is overgeërfd als gevolg van het lidmaatschap van een andere groep.

Als u op een GroupID klikt (indien beschikbaar), wordt het dialoogvenster [Groepsbeheer](#group-administration) voor die groep.

**Imitators**

Met de functie Imiteren kan een gebruiker namens een andere gebruiker werken.

Dit betekent dat een gebruikersaccount andere accounts (gebruiker of groep) kan opgeven die met hun account kunnen werken. Met andere woorden, als gebruiker-B wordt toegestaan om gebruiker-A te nadoen, dan kan gebruiker-B het gebruiken van de volledige rekeningsdetails van gebruiker-A (met inbegrip van identiteitskaart, naam, en toegangsrechten) handelen.

Hierdoor kunnen imitatoraccounts taken uitvoeren alsof ze de account gebruiken die ze nadoen, bijvoorbeeld tijdens afwezigheid, of een buitensporige last op korte termijn delen.

Als een account een andere account nastreeft, is het moeilijk te zien. De logboekdossiers houden geen informatie over het feit dat de imitatie op de gebeurtenissen is voorgekomen. Dus als user-B zich gebruiker-A imiteert, kunnen alle gebeurtenissen kijken alsof zij door gebruiker-A persoonlijk werden uitgevoerd.

### Een gebruikersaccount maken {#creating-a-user-account}

1. Open de **Gebruikersbeheer** in.
1. Klikken **Gebruiker maken**.
1. Vervolgens kunt u de eigenschappen invoeren:

   * **GebruikerID** gebruikt als de accountnaam.
   * **Wachtwoord** nodig bij het aanmelden.
   * **Hoofdnaam** om een volledige tekstnaam op te geven.
   * **Intermediair pad** die kunnen worden gebruikt om een boomstructuur te vormen.

1. Klik op Opslaan (groen verdeelstreepje).
1. Het dialoogvenster wordt uitgebreid, zodat u het volgende kunt doen:

   1. Configureren **Eigenschappen**.
   1. Zie **Groepslidmaatschap**.
   1. Definiëren **Imitators**.

>[!NOTE]
>
>Soms kunnen de prestaties verloren gaan wanneer nieuwe gebruikers worden geregistreerd in installaties met een groot aantal van beide:
>
>* gebruikers
>* groepen met veel leden
>

### Een gebruikersaccount bijwerken {#updating-a-user-account}

1. Met de **Gebruikersbeheer** opent u de lijstweergave van alle accounts.
1. Navigeer door de boomstructuur.
1. Klik op de gewenste account zodat u deze kunt openen voor bewerking.
1. Breng een wijziging aan en klik vervolgens op Opslaan (groen verdeelstreepje) voor die vermelding.
1. Klikken **Sluiten** om te voltooien, of **Lijst...** om terug te keren naar de lijst met alle gebruikersaccounts.

### Een gebruikersaccount verwijderen {#removing-a-user-account}

1. Met de **Gebruikersbeheer** opent u de lijstweergave van alle accounts.
1. Navigeer door de boomstructuur.
1. Selecteer de vereiste account en klik op **Gebruiker verwijderen**; de rekening wordt onmiddellijk verwijderd.

>[!NOTE]
>
>Dit verwijdert de knoop voor dit hoofd uit de bewaarplaats.
>
>Toegangsrechten worden niet verwijderd. Dit garandeert de historische integriteit.

### Eigenschappen definiëren {#defining-properties}

U kunt **Eigenschappen** voor nieuwe of bestaande rekeningen:

1. Open de **Gebruikersbeheer** voor de juiste account.
1. Een **Eigenschap** naam.
1. Selecteer de **Type** in de vervolgkeuzelijst.
1. Definieer de **Waarde**.
1. Klik op Opslaan (groen kliksymbool) voor de nieuwe eigenschap.

Bestaande eigenschappen kunnen met het prullenbaksymbool worden verwijderd.

Met uitzondering van het wachtwoord kunnen eigenschappen niet worden bewerkt, maar moeten ze worden verwijderd en opnieuw gemaakt.

#### Het wachtwoord wijzigen {#changing-the-password}

De **Wachtwoord** is een speciale eigenschap die kan worden gewijzigd door op de knop **Wachtwoord wijzigen** koppeling.

U kunt het wachtwoord ook wijzigen in uw eigen gebruikersaccount via het dialoogvenster **Beveiliging** in de CRX Explorer.

### Een imitator definiëren {#defining-an-impersonator}

U kunt imitators definiëren voor nieuwe of bestaande accounts:

1. Open de **Gebruikersbeheer** voor de juiste account.
1. Geef op welk account u als lid van dat account wilt gebruiken.

   Met Bladeren... kunt u een bestaand account selecteren.

1. Klik op Opslaan (groen verdeelstreepje) voor de nieuwe eigenschap.

## Groepsbeheer {#group-administration}

Er wordt een standaarddialoogvenster gebruikt voor **Groepsbeheer**.

U moet in de aangewezen werkruimte worden geregistreerd, dan kunt u tot de dialoog van allebei toegang hebben:

* de **Groepsbeheer** koppeling in de hoofdconsole van CRX
* de **Beveiliging** menu van de CRX Explorer

![chlimage_1-8](assets/chlimage_1-8.jpeg)

**Eigenschappen**

* **GroupID**

  Korte naam voor de groepsaccount.

* **Hoofdnaam**

  Een volledige tekstnaam voor het groepsaccount.

* U kunt nieuwe eigenschappen toevoegen door een naam, type en waarde te definiëren. Klik op Opslaan (groen verdeelstreepje) voor elke nieuwe eigenschap.

* **Leden**

  U kunt gebruikers of andere groepen toevoegen als leden van deze groep.

**Groepslidmaatschap**

Hiermee worden alle groepen weergegeven waartoe de huidige groepsaccount behoort. De kolom Overgenomen geeft het lidmaatschap aan dat is overgeërfd als gevolg van het lidmaatschap van een andere groep.

Wanneer u op een GroupID klikt, wordt het dialoogvenster voor die groep geopend.

**Leden**

Hiermee geeft u alle accounts (gebruikers en/of groepen) weer die lid zijn van de huidige groep.

De **Overgenomen** de kolom wijst op lidmaatschap dat als resultaat van lidmaatschap van een andere groep is geërft.

>[!NOTE]
>
>Wanneer de rol Eigenaar, Editor of Viewer wordt toegewezen aan een gebruiker in een willekeurige map met middelen, wordt een nieuwe groep gemaakt. De groepsnaam heeft de indeling `mac-default-<foldername>` voor elke map waarin de rollen zijn gedefinieerd.

### Een groepsaccount maken {#creating-a-group-account}

1. Open de **Groepsbeheer** in.
1. Klikken **Groep maken**.
1. Vervolgens kunt u de eigenschappen invoeren:

   * **Hoofdnaam** om een volledige tekstnaam op te geven.
   * **Intermediair pad** die kunnen worden gebruikt om een boomstructuur te vormen.

1. Klik op Opslaan (groen verdeelstreepje).
1. Het dialoogvenster wordt uitgebreid, zodat u:

   1. Configureren **Eigenschappen**.
   1. Zie **Groepslidmaatschap**.
   1. Beheren **Leden**.

### Een groepsaccount bijwerken {#updating-a-group-account}

1. Met de **Groepsbeheer** opent u de lijstweergave van alle accounts.
1. Navigeer door de boomstructuur.
1. Klik op de gewenste account zodat u deze kunt openen voor bewerking.
1. Breng een wijziging aan en klik vervolgens op Opslaan (groen verdeelstreepje) voor die vermelding.
1. Klikken **Sluiten** om te voltooien, of **Lijst...** om terug te keren naar de lijst van alle groepsrekeningen.

### Een groepsaccount verwijderen {#removing-a-group-account}

1. Met de **Groepsbeheer** opent u de lijstweergave van alle accounts.
1. Navigeer door de boomstructuur.
1. Selecteer de vereiste account en klik op **Groep verwijderen**; de rekening wordt onmiddellijk verwijderd.

>[!NOTE]
>
>Dit verwijdert de knoop voor dit hoofd uit de bewaarplaats.
>
>Toegangsrechten worden niet verwijderd. Dit garandeert de historische integriteit.

### Eigenschappen definiëren {#defining-properties-1}

U kunt Eigenschappen definiëren voor nieuwe of bestaande accounts:

1. Open de **Groepsbeheer** voor de juiste account.
1. Een **Eigenschap** naam.
1. Selecteer de **Type** in de vervolgkeuzelijst.
1. Definieer de **Waarde**.
1. Klik op Opslaan (groen verdeelstreepje) voor de nieuwe eigenschap.

Bestaande eigenschappen kunnen met het prullenbaksymbool worden verwijderd.

### Leden {#members}

U kunt leden toevoegen aan de huidige groep:

1. Open de **Groepsbeheer** voor de juiste account.
1. Ofwel:

   * Voer de naam in van het vereiste lid (gebruiker- of groepsaccount).
   * of gebruiken **Bladeren...** om te zoeken naar de principal (gebruiker- of groepsaccount) die u wilt toevoegen en deze te selecteren.

1. Klik op Opslaan (groen verdeelstreepje) voor de nieuwe eigenschap.

Of verwijder een bestaand lid met het prullenbaksymbool.

## Toegangsbeheer {#access-right-management}

Met de **Toegangsbeheer** tabblad CRXDE Lite, kunt u het beleid voor toegangsbeheer definiëren en de bijbehorende rechten toewijzen.

Bijvoorbeeld: **Huidig pad** Selecteer de vereiste bron in het linkerdeelvenster, het tabblad Toegangsbeheer in het deelvenster rechtsonder:

![crx_accesscontrol_tab](assets/crx_accesscontrol_tab.png)

Het beleid wordt ingedeeld volgens:

* **Toepasselijk beleid voor toegangscontrole**

  Dit beleid kan worden toegepast.

  Dit zijn beleid dat beschikbaar is voor het creëren van een lokaal beleid. Wanneer u een toepasselijk beleid selecteert en toevoegt, wordt het een lokaal beleid.

* **Lokaal beleid voor toegangsbeheer**

  Dit zijn toegangsbeheerbeleid dat u hebt toegepast. U kunt deze vervolgens bijwerken, bestellen of verwijderen.

  Een lokaal beleid negeert beleid dat van de ouder wordt geërft.

* **Effectief beleid voor toegangscontrole**

  Dit zijn het beleid van de toegangscontrole dat nu voor om het even welke toegangsverzoeken van kracht is. Zij tonen het samengevoegde beleid dat uit zowel het lokale beleid als om het even welk wordt afgeleid die van de ouder wordt geërft.

### Beleidsselectie {#policy-selection}

Het beleid kan worden geselecteerd voor:

* **Huidig pad**

  Zoals in het bovenstaande voorbeeld, selecteer een middel binnen de bewaarplaats. Het beleid voor dit &quot;huidige pad&quot; wordt weergegeven.

* **Bewaarplaats**

  Hiermee selecteert u toegangsbeheer op archiefniveau. Als u bijvoorbeeld de opdracht `jcr:namespaceManagement` privilege, dat alleen relevant is voor de gegevensopslagruimte, niet voor een knooppunt.

* **Opdrachtgever**

  Een principal die in de repository is geregistreerd.

  U kunt in het dialoogvenster **Opdrachtgever** naam of klik op het pictogram rechts van het veld om het dialoogvenster **Principal selecteren** in.

  Hiermee kunt u **Zoeken** voor een **Gebruiker** of **Groep**. Selecteer de vereiste principal in de lijst die u opmaakt, en klik vervolgens op **OK** om de waarde terug naar het vorige dialoogvenster te brengen.

![crx_accesscontrol_selectprincipal](assets/crx_accesscontrol_selectprincipal.png)

>[!NOTE]
>
>Om de Adobe van het beheer te vereenvoudigen, adviseert u toegangsrechten aan groepsrekeningen, niet individuele gebruikersrekeningen toe te wijzen.
>
>Het is eenvoudiger om een paar groepen te beheren in plaats van veel gebruikersaccounts.

### Rechten {#privileges}

De volgende rechten zijn beschikbaar voor selectie wanneer u een toegangsbeheeritem toevoegt (zie de [Security API](https://developer.adobe.com/experience-manager/reference-materials/spec/javax.jcr/javadocs/jcr-2.0/javax/jcr/security/Privilege.html) voor nadere bijzonderheden ) :

<table>
 <tbody>
  <tr>
   <th><strong>Naam bevoegdheid</strong></th>
   <th><strong>Welke controle heeft over het recht op...</strong></th>
  </tr>
  <tr>
   <td><code>jcr:read</code></td>
   <td>Hiermee wordt een knooppunt opgehaald en worden de eigenschappen en waarden van het knooppunt gelezen.</td>
  </tr>
  <tr>
   <td><code>rep:write</code></td>
   <td>Dit is een geaggregeerd voorrecht voor jcr:write en jcr:nodeTypeManagement dat specifiek is voor het hoesje.<br /> </td>
  </tr>
  <tr>
   <td><code>jcr:all</code></td>
   <td>Dit is een geaggregeerd voorrecht dat alle andere vooraf gedefinieerde bevoegdheden bevat.</td>
  </tr>
  <tr>
   <td><strong>Geavanceerd</strong></td>
   <td> </td>
  </tr>
  <tr>
   <td><code>crx:replicate</code></td>
   <td>Voer replicatie van een knoop uit.</td>
  </tr>
  <tr>
   <td><code>jcr:addChildNodes</code></td>
   <td>Maak onderliggende knooppunten van een knooppunt.</td>
  </tr>
  <tr>
   <td><code>jcr:lifecycleManagement</code></td>
   <td>Levenscyclusbewerkingen uitvoeren op een knooppunt.</td>
  </tr>
  <tr>
   <td><code>jcr:lockManagement</code></td>
   <td>Een knooppunt vergrendelen en ontgrendelen; een vergrendeling vernieuwen.</td>
  </tr>
  <tr>
   <td><code>jcr:modifyAccessControl</code></td>
   <td>Wijzig het toegangsbeheerbeleid van een knoop.</td>
  </tr>
  <tr>
   <td><code>jcr:modifyProperties</code></td>
   <td>Maak, wijzig en verwijder de eigenschappen van een knooppunt.</td>
  </tr>
  <tr>
   <td><code>jcr:namespaceManagement</code></td>
   <td>Naamruimtedefinities registreren, verwijderen en wijzigen.</td>
  </tr>
  <tr>
   <td><code>jcr:nodeTypeDefinitionManagement</code></td>
   <td>Importeer knooppunttypedefinities naar de repository.</td>
  </tr>
  <tr>
   <td><code>jcr:nodeTypeManagement</code></td>
   <td>Voeg en verwijder mixinknooptypes toe en verander het primaire knooptype van een knoop. Dit omvat ook om het even welke vraag aan Node.addNode en het invoeren van XML methodes waar de mixin of het primaire type van nieuwe knoop uitdrukkelijk wordt gespecificeerd.</td>
  </tr>
  <tr>
   <td><code>jcr:readAccessControl</code></td>
   <td>Lees het beleid van de toegangscontrole van een knoop.</td>
  </tr>
  <tr>
   <td><code>jcr:removeChildNodes</code></td>
   <td>Verwijder onderliggende knooppunten van een knooppunt.</td>
  </tr>
  <tr>
   <td><code>jcr:removeNode</code></td>
   <td>Een knooppunt verwijderen.</td>
  </tr>
  <tr>
   <td><code>jcr:retentionManagement</code></td>
   <td>Voer verrichtingen van het bewaarbeheer op een knoop uit.</td>
  </tr>
  <tr>
   <td><code>jcr:versionManagement</code></td>
   <td>Voer versioning bewerkingen uit op een knooppunt.</td>
  </tr>
  <tr>
   <td><code>jcr:workspaceManagement</code></td>
   <td>Het maken en verwijderen van werkruimten via de JCR API.</td>
  </tr>
  <tr>
   <td><code>jcr:write</code></td>
   <td>Dit is een geaggregeerd voorrecht dat het volgende bevat:<br /> - jcr:modifyProperties<br /> - jcr:addChildNodes<br /> - jcr:removeNode<br /> - jcr:removeChildNodes</td>
  </tr>
  <tr>
   <td><code>rep:privilegeManagement</code></td>
   <td>Registreer een nieuw voorrecht.</td>
  </tr>
 </tbody>
</table>

### Registreren van nieuwe rechten {#registering-new-privileges}

U kunt ook nieuwe rechten registreren:

1. Selecteer op de werkbalk de optie **Gereedschappen** vervolgens **Rechten** om de momenteel geregistreerde rechten weer te geven.

   ![ac_privileges](assets/ac_privileges.png)

1. Gebruik de **Rechten registreren** icon (**+**), zodat u een bevoegdheid kunt definiëren:

   ![ac_privilegesRegister](assets/ac_privilegeregister.png)

1. Klikken **OK** opslaan. Het voorrecht is nu beschikbaar voor selectie.

### Een toegangsbeheeritem toevoegen {#adding-an-access-control-entry}

1. Selecteer uw bron en open de **Toegangsbeheer** tab.

1. Een nieuwe **Lokaal beleid voor toegangsbeheer** klikt u op de knop **+** pictogram rechts van **Toepasselijk toegangsbeheerbeleid** lijst:

   ![crx_accesscontrol_applicable](assets/crx_accesscontrol_applicable.png)

1. Een nieuwe vermelding wordt weergegeven onder **Beleid voor lokaal toegangsbeheer:**

   ![crx_accesscontrol_newlocal](assets/crx_accesscontrol_newlocal.png)

1. Klik op de knop **+** pictogram zodat u een item kunt toevoegen:

   ![crx_accesscontrol_addentry](assets/crx_accesscontrol_addentry.png)

   >[!NOTE]
   >
   >Er is momenteel een tijdelijke oplossing nodig om een lege tekenreeks op te geven.
   >
   >Hiervoor moet u `""`.

1. Bepaal uw toegangsbeheerbeleid en klik **OK** opslaan. Uw nieuwe beleid is:

   * vermeld onder **Lokaal toegangsbeheerbeleid**
   * wijzigingen worden weerspiegeld in de **Effectief beleid voor toegangscontrole**.

CRX valideert uw selectie; voor een bepaald hoofd bestaat er (hoogstens) één ontkent en één toelaat ingang op een bepaalde knoop. De implementatie ontruimt altijd overtollige ingangen en zorgt ervoor dat het zelfde voorrecht niet in zowel toestaat als ontkent ingangen vermeld is.

### Plaatselijk beleid voor toegangsbeheer bestellen {#ordering-local-access-control-policies}

De volgorde in de lijst geeft de volgorde aan waarin het beleid wordt toegepast.

1. In de tabel **Lokaal beleid voor toegangsbeheer** selecteert u de gewenste vermelding en sleept u deze naar de nieuwe positie in de tabel.

   ![crx_accesscontrol_reorder](assets/crx_accesscontrol_reorder.png)

1. De wijzigingen worden weergegeven in beide tabellen voor de **Lokaal** en de **Effectief beleid voor toegangscontrole**.

### Een toegangsbeheerbeleid verwijderen {#removing-an-access-control-policy}

1. In de tabel **Lokaal beleid voor toegangsbeheer** klikt u op het rode pictogram (-) rechts van de vermelding.
1. Het item wordt verwijderd uit beide tabellen voor de **Lokaal** en de **Effectief beleid voor toegangscontrole**.

### Het testen van een Beleid van het Toegangsbeheer {#testing-an-access-control-policy}

1. Selecteer op de werkbalk CRXDE Lite de optie **Gereedschappen** vervolgens **Toegangsbeheer testen...**.
1. Er wordt een nieuw dialoogvenster geopend in het deelvenster rechtsboven. Selecteer de **Pad** en/of **Opdrachtgever** die u wilt testen.
1. Klikken **Testen** om de resultaten voor uw selectie te zien:

   ![crx_accesscontrol_test](assets/crx_accesscontrol_test.png)
