---
title: Gesloten gebruikersgroepen in AEM
seo-title: Gesloten gebruikersgroepen in AEM
description: Meer informatie over gesloten gebruikersgroepen in AEM.
seo-description: Meer informatie over gesloten gebruikersgroepen in AEM.
uuid: 83396163-86ce-406b-b797-2457ed975ccd
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
discoiquuid: a2bd7045-970f-4245-ad5d-a272a654df0a
docset: aem65
translation-type: tm+mt
source-git-commit: 2142df4f7579e052e18879b437fc43911010b475
workflow-type: tm+mt
source-wordcount: '6890'
ht-degree: 0%

---


# Gesloten gebruikersgroepen in AEM{#closed-user-groups-in-aem}

## Inleiding {#introduction}

Sinds AEM 6.3, is er een nieuwe gesloten implementatie van de Groep van de Gebruiker bedoeld om de prestaties, scalability en veiligheidskwesties te behandelen die met de bestaande implementatie worden voorgesteld.

>[!NOTE]
>
>Ter wille van de eenvoud wordt de CUG-afkorting in deze documentatie gebruikt.

Het doel van de nieuwe implementatie is om waar nodig bestaande functionaliteit te bestrijken en tegelijkertijd problemen en ontwerpbeperkingen van oudere versies aan te pakken. Het resultaat is een nieuw ontwerp van CUG met de volgende kenmerken:

* een duidelijke scheiding tussen authenticatie- en autorisatieelementen, die afzonderlijk of in combinatie kunnen worden gebruikt;
* Het specifieke vergunningsmodel om op de beperkte leestoegang bij de gevormde bomen van de GG te wijzen zonder andere opstelling en toestemmingsvereisten van de toegangscontrole te storen;
* Scheiding tussen de opstelling van het toegangsbeheer van de beperkte gelezen toegang, die gewoonlijk op auteursinstanties, en toestemmingsevaluatie nodig is die gewoonlijk slechts bij publiceren is;
* Bewerken van beperkte leestoegang zonder escalatie met bevoegdheden;
* Specifieke uitbreiding van knooppunttype om de authenticatievereiste te markeren;
* Optioneel aanmeldpad dat is gekoppeld aan de verificatievereiste.

### De nieuwe Implementatie van de Gebruikersgroep van de Douane {#the-new-custom-user-group-implementation}

Een CUG zoals deze in de context van AEM bekend is, bestaat uit de volgende stappen:

* Beperk leestoegang op de boom die moet worden beschermd en sta slechts lezen voor hoofden toe die of met een bepaalde instantie van de GG vermeld zijn of van de evaluatie van de GG helemaal worden uitgesloten. Dit wordt het **authentication** element genoemd.
* Verificatie afdwingen voor een bepaalde structuur en optioneel een specifieke aanmeldingspagina opgeven voor die structuur die vervolgens wordt uitgesloten. Dit wordt het **authenticatie** element genoemd.

De nieuwe implementatie is ontworpen om een lijn te trekken tussen de authenticatie en de autorisatieonderdelen. Met ingang van AEM 6.3 is het mogelijk leestoegang te beperken zonder expliciet een verificatievereiste toe te voegen. Bijvoorbeeld, als een bepaalde instantie authentificatie helemaal vereist of een bepaalde boom verblijft reeds in een subboom die authentificatie reeds vereist.

Eveneens, kan een bepaalde boom met een authentificatievereiste worden gemerkt zonder de efficiënte toestemmingsopstelling te veranderen. De combinaties en de resultaten zijn vermeld in [Combinerend het Beleid van de GING en de sectie van de Authentificatie ](/help/sites-administering/closed-user-groups.md#combining-cug-policies-and-the-authentication-requirement).

## Overzicht {#overview}

### Autorisatie: Leestoegang beperken {#authorization-restricting-read-access}

De belangrijkste eigenschap van een CUG beperkt leestoegang op een bepaalde boom in de inhoudsbewaarplaats voor iedereen behalve geselecteerde hoofden. In plaats van het manipuleren van de standaardtoegangsbeheerinhoud op de vlucht neemt de nieuwe implementatie een verschillende benadering door een specifiek type van toegangsbeheerbeleid te bepalen dat een KUG vertegenwoordigt.

#### Beleid voor toegangsbeheer voor CUG {#access-control-policy-for-cug}

Dit nieuwe type beleid heeft de volgende kenmerken:

* Toegangscontrolebeleid van het type org.apache.jackrabbit.api.security.authentication.PrincipalSetPolicy (gedefinieerd door de Apache Jackrabbit-API);
* PrincipalSetPolicy verleent voorrechten aan een wijzigbare reeks principes;
* De toegekende bevoegdheden en de reikwijdte van het beleid zijn een detail van de uitvoering.

De implementatie van PrincipalSetPolicy die wordt gebruikt om CUGs te vertegenwoordigen bepaalt daarnaast:

* Het beleid van CUG verleent slechts leestoegang tot regelmatige punten JCR (bijvoorbeeld, wordt de inhoud van de toegangscontrole uitgesloten);
* Het werkingsgebied wordt bepaald door de toegang gecontroleerde knoop die het beleid van de KUG houdt;
* Het beleid van de CUG kan worden genesteld, begint een genestelde KUG een nieuwe KUG zonder de belangrijkste reeks van &quot;ouder&quot;KUG over te nemen;
* Het effect van het beleid, als de evaluatie wordt toegelaten, wordt geërft aan volledige subtree neer aan volgende genestelde KUG.

Dit beleid van CUG wordt opgesteld aan een AEM instantie door een afzonderlijke vergunningsmodule genoemd oak-vergunning-insect. Deze module komt met zijn eigen beheer van toegangsbeheer en toestemmingsevaluatie. Met andere woorden, de standaard AEM installatie verzendt een configuratie van de opslagplaats voor eik-inhoud die meerdere machtigingsmechanismen combineert. Zie [deze pagina op de Apache Oak-documentatie](https://jackrabbit.apache.org/oak/docs/security/authorization/composite.html) voor meer informatie.

In deze samengestelde opstelling vervangt een nieuwe KUG niet de bestaande inhoud van het toegangsbeheer in bijlage aan de doelknoop, maar wordt ontworpen om een aanvulling te zijn die ook later kan worden verwijderd zonder het originele toegangsbeheer te beïnvloeden, dat door gebrek in AEM een toegangsbeheerlijst zou zijn.

In tegenstelling tot de vorige implementatie worden het nieuwe beleid van de GG altijd erkend en behandeld als inhoud van de toegangscontrole. Dit houdt in dat ze worden gemaakt en bewerkt met de API voor toegangsbeheer van de JCR. Voor meer informatie, zie [het Beheren van het Beleid van de GIDS](#managing-cug-policies) sectie.

#### Evaluatie van machtigingen voor CUG-beleid {#permission-evaluation-of-cug-policies}

Naast een specifiek toegangsbeheerbeheer voor CUGs, staat het nieuwe vergunningsmodel toe om toestemmingsevaluatie voor zijn beleid voorwaardelijk toe te laten. Dit staat aan opstelling toe het beleid van CUG in een het opvoeren milieu, en laat slechts evaluatie van de efficiënte toestemmingen toe zodra herhaald aan het productiemilieu.

De evaluatie van de toestemming voor het beleid van de CUG en de interactie met het gebrek of om het even welk extra vergunningsmodel volgt het patroon dat voor veelvoudige vergunningsmechanismen in Apache Jackrabbit Oak wordt ontworpen: een bepaalde reeks toestemmingen wordt verleend als en slechts als alle modellen toegang verlenen. Zie [deze pagina](https://jackrabbit.apache.org/oak/docs/security/authorization/composite.html) voor meer informatie.

De volgende kenmerken zijn voor de toestemmingsevaluatie verbonden aan het vergunningsmodel van toepassing dat wordt ontworpen om het beleid van de CUG te behandelen en te evalueren:

* Het behandelt slechts gelezen toestemmingen voor regelmatige knopen en eigenschappen, maar het lezen van toegangsbeheerinhoud
* Deze behandelt geen schrijfmachtigingen en geen machtigingen die vereist zijn voor de wijziging van beveiligde JCR-inhoud (toegangsbeheer, informatie over knooppunttypen, versioning, vergrendeling of gebruikersbeheer, enz.); Deze toestemmingen worden niet beïnvloed door een beleid van de CUG en zullen niet door het bijbehorende vergunningsmodel worden geëvalueerd. Of deze toestemmingen al dan niet worden verleend hangt van de andere modellen af die in de veiligheidsopstelling worden gevormd.

Het effect van één enkel beleid van CUG op toestemmingsevaluatie kan als volgt worden samengevat:

* Leestoegang wordt ontzegd voor iedereen behalve onderwerpen die uitgesloten hoofden of hoofden bevatten die in het beleid worden vermeld;
* Het beleid wordt van kracht op de toegang gecontroleerde knoop die het beleid en zijn eigenschappen houdt;
* Het effect wordt bovendien geërft onderaan de hiërarchie - namelijk de puntenboom die door de toegang gecontroleerde knoop wordt bepaald;
* Nochtans, beïnvloedt het noch siblings noch voorouders van de toegang gecontroleerde knoop;
* De overerving van een bepaalde CUG houdt bij genestelde KUG tegen.

#### Best practices voor {#best-practices}

Bij het definiëren van beperkte leestoegang via CUG&#39;s moet rekening worden gehouden met de volgende aanbevolen procedures:

* Bespreek bewust of uw behoefte aan een KUUG over het beperken van lees toegang of een authentificatievereiste is. In het geval van de laatste of in het geval dat beide nodig zijn, raadpleegt u de paragraaf over beste praktijken voor nadere informatie over de authenticatievereisten
* Creeer een bedreigingsmodel voor de gegevens of de inhoud die moeten worden beschermd om bedreigingsgrenzen te identificeren en een duidelijk beeld over de gevoeligheid van de gegevens en de rollen te krijgen verbonden aan erkende toegang
* Model de inhoud van de opslagplaats en CUGs met inachtneming van algemene vergunningsgerelateerde aspecten en beste praktijken in mening:

   * Herinner dat de lees toestemming slechts zal worden verleend als bepaalde CUG en de evaluatie van andere modules die in de opstellingssubsidie worden opgesteld een bepaalde onderwerp toestaan om een bepaald bewaarplaatspunt te lezen
   * Vermijd het creëren van overtollige KUGs waar de gelezen toegang reeds door andere vergunningsmodules wordt beperkt
   * Bij buitensporige behoefte aan geneste CUG&#39;s kunnen problemen in het inhoudsontwerp mogelijk worden gemarkeerd
   * De zeer buitensporige behoefte aan GGs (bijvoorbeeld, op elke enige pagina) kan op de behoefte aan een model van de douanevergunning wijzen dat potentieel beter geschikt is om de specifieke veiligheidsbehoeften van de toepassing en de inhoud in kwestie aan te passen.

* Beperk de paden die worden ondersteund voor CUG-beleid tot een paar bomen in de opslagplaats, zodat u de prestaties kunt optimaliseren. Bijvoorbeeld, sta slechts CUGs onder de /content knoop toe zoals verscheept als standaardwaarde sinds AEM 6.3.
* Het beleid van de CUG wordt ontworpen om gelezen toegang tot een kleine reeks principes te verlenen. De behoefte aan een enorm aantal principes kan kwesties in de inhoud of toepassingsontwerp benadrukken en zou moeten worden herzien.

### Verificatie: Het Auth-voorschrift {#authentication-defining-the-auth-requirement} definiëren

De authentificatie verwante delen van de eigenschap van CUG staan toe om bomen te merken die authentificatie vereisen en naar keuze een specifieke login pagina specificeren. In overeenstemming met de vorige versie, staat de nieuwe implementatie toe om bomen te merken die authentificatie in de inhoudsbewaarplaats vereisen en voorwaardelijk synchronisatie met `Sling org.apache.sling.api.auth.Authenticator`verantwoordelijk voor uiteindelijk het handhaven van het vereiste en het opnieuw richten aan een login middel toelaten.

Deze vereisten worden geregistreerd met de Authenticator door middel van de dienst OSGi die `sling.auth.requirements` registratiebezit verstrekt. Deze eigenschappen worden dan gebruikt om de authentificatievereisten dynamisch uit te breiden. Raadpleeg de [Sling-documentatie](https://sling.apache.org/apidocs/sling7/org/apache/sling/auth/core/AuthConstants.html#AUTH_REQUIREMENTS) voor meer informatie.

#### Het bepalen van de Vereisten van de Authentificatie met een Specifiek Type {#defining-the-authentication-requirement-with-a-dedicated-mixin-type}

Om veiligheidsredenen vervangt de nieuwe implementatie het gebruik van een residuele eigenschap JCR door een specifiek mixintype genoemd `granite:AuthenticationRequired`, die één enkele facultatieve bezit van typeSTRING voor de login weg `granite:loginPath` bepaalt. Alleen inhoudswijzigingen met betrekking tot dit mixintype leiden tot het bijwerken van de vereisten die zijn geregistreerd bij Apache Sling Authenticator. De wijzigingen worden bijgehouden bij het aanhouden van eventuele tijdelijke wijzigingen en vereisen daarom een `javax.jcr.Session.save()` oproep om effectief te worden.

Hetzelfde geldt voor de eigenschap `granite:loginPath`. Er wordt alleen aan voldaan als het wordt gedefinieerd door het aan de auteisen gerelateerde mengtype. Het toevoegen van een restbezit met deze zeer naam bij een ongestructureerde knoop JCR zal niet het gewenste effect tonen en het bezit zal door de manager verantwoordelijk voor het bijwerken van de registratie worden genegeerd OSGi.

>[!NOTE]
>
>Het instellen van de eigenschap voor het aanmeldingspad is optioneel en alleen nodig als de structuur waarvoor verificatie is vereist, niet kan terugvallen op de standaardaanmeldingspagina of een andere overgeërfde aanmeldingspagina. Zie [Evaluatie van aanmeldingspad](/help/sites-administering/closed-user-groups.md#evaluation-of-login-path) hieronder.

#### Registreren van de Vereiste van de Authentificatie en Login Weg met de Verschuivende Authenticator {#registering-the-authentication-requirement-and-login-path-with-the-sling-authenticator}

Aangezien dit type van authentificatievereiste naar verwachting tot bepaalde looppaswijzen en tot een kleine ondergroep van bomen binnen de inhoudsbewaarplaats zal worden beperkt, is het volgen van het vereiste mixintype en de login wegeigenschappen voorwaardelijk en verbindend aan een overeenkomstige configuratie die de gesteunde wegen bepaalt (zie de Opties van de Configuratie hieronder). Bijgevolg zullen alleen wijzigingen binnen het bereik van deze ondersteunde paden een update van de OSGi-registratie activeren, elders worden zowel het mixintype als de eigenschap genegeerd.

De standaard AEM opstelling maakt nu gebruik van deze configuratie door toe te staan om de mixin op de wijze van de auteurslooppas te plaatsen maar het slechts van kracht te hebben op replicatie aan te publiceren instantie. Zie [deze pagina](https://sling.apache.org/documentation/the-sling-engine/authentication/authenticationframework.html) voor meer informatie over hoe Sling de vereiste voor verificatie afdwingt.

Als u het mixintype `granite:AuthenticationRequired` toevoegt binnen de geconfigureerde ondersteunde paden, wordt de OSGi-registratie van de verantwoordelijke handler bijgewerkt met een nieuwe, aanvullende vermelding met de eigenschap `sling.auth.requirements`. Als een bepaalde authentificatievereiste de facultatieve `granite:loginPath` bezit specificeert, wordt de waarde additioneel geregistreerd met de Authenticator met een &#39;-&#39; prefix om van authentificatievereiste te worden uitgesloten.

#### Evaluatie en overerving van de authenticatievereiste {#evaluation-and-inheritance-of-the-authentication-requirement}

Van Apache Sling-verificatievereisten wordt verwacht dat deze worden overgeërfd via de pagina- of knooppunthiërarchie. De details zelf van de erfenis en de evaluatie van de authentificatievereisten zoals orde en belangrijkheid worden beschouwd als implementatiedetails en zullen niet in dit artikel worden gedocumenteerd.

#### Evaluatie van aanmeldingspad {#evaluation-of-login-path}

De evaluatie van de login weg en het omleiden aan het overeenkomstige middel op authentificatie is momenteel een implementatiedetails van de Behandelaar van de Authentificatie van de Selecteur van de Registratie van de Adobe Granite ( `com.day.cq.auth.impl.LoginSelectorHandler`), die een Apache Sling AuthenticationHandler is die met AEM door gebrek wordt gevormd.

Bij het aanroepen van `AuthenticationHandler.requestCredentials` doet deze handler een poging om de aanmeldingspagina voor toewijzingen te bepalen waarnaar de gebruiker wordt omgeleid. Dit omvat de volgende stappen:

* Onderscheid tussen verlopen wachtwoord en behoefte aan regelmatige login als reden voor omleiding;
* In het geval van een regelmatige login, test als een login weg in de volgende orde kan worden verkregen:

   * vanuit de LoginPathProvider zoals geïmplementeerd door de nieuwe `com.adobe.granite.auth.requirement.impl.RequirementService`,
   * van de oude, afgekeurde implementatie van de GOS,
   * in de aanmeldingspagina-toewijzingen, zoals gedefinieerd met de `LoginSelectorHandler`,
   * en tenslotte, fallback aan de Standaard Login Pagina, zoals bepaald met `LoginSelectorHandler`.

* Zodra een geldig login weg door de hierboven vermelde vraag werd verkregen, zal het verzoek van de gebruiker aan die pagina worden opnieuw gericht.

Het doel van deze documentatie is de evaluatie van de login weg zoals die door de interne `LoginPathProvider` interface wordt blootgesteld. De implementatie die sinds AEM 6.3 wordt verzonden, functioneert als volgt:

* Registratie van aanmeldingspaden is afhankelijk van het onderscheid tussen verlopen wachtwoord en de behoefte aan regelmatige aanmelding als reden voor omleiding
* In het geval van regelmatige login, test als een login weg in de volgende orde kan worden verkregen:

   * van de `LoginPathProvider` zoals geïmplementeerd door de nieuwe `com.adobe.granite.auth.requirement.impl.RequirementService`,
   * van de oude, afgekeurde implementatie van de GOS,
   * in de aanmeldingspagina-toewijzingen zoals gedefinieerd met de `LoginSelectorHandler`,
   * en tenslotte fallback aan de StandaardAanmeldingspagina zoals bepaald met `LoginSelectorHandler`.

* Zodra een geldig login weg door de hierboven vermelde vraag werd verkregen, zal het verzoek van de gebruiker aan die pagina worden opnieuw gericht.

`LoginPathProvider` zoals uitgevoerd door de nieuwe auth-required steun in Granite stelt login wegen zoals die door de `granite:loginPath` eigenschappen worden bepaald, die beurtelings door het mixintype zoals hierboven beschreven worden bepaald. De afbeelding van de middelweg die de login weg en de bezitswaarde zelf houdt wordt gehouden in geheugen en zal worden geëvalueerd om een geschikte login weg voor andere knopen in de hiërarchie te vinden.

>[!NOTE]
>
>De evaluatie wordt slechts uitgevoerd voor verzoeken verbonden aan middelen die met in de gevormde gesteunde wegen worden gevestigd. Voor andere verzoeken zullen de alternatieve manieren om de login weg te bepalen worden geëvalueerd.

#### Best practices voor {#best-practices-1}

Bij het bepalen van de verificatievereisten moet rekening worden gehouden met de volgende beste praktijken:

* Vermijd vereisten voor nestverificatie: het plaatsen van één enkele auth-required teller aan het begin van een boom zou moeten voldoende zijn en aan de volledige subtree geërft die door de doelknoop wordt bepaald. Aanvullende verificatievereisten binnen die structuur moeten als overbodig worden beschouwd en kunnen leiden tot prestatieproblemen bij de evaluatie van de verificatievereisten binnen Apache Sling. Met de scheiding van vergunning en authentificatiegerelateerde gebieden van de GG is het mogelijk om gelezen toegang door middel van KUG of ander type van beleid te beperken terwijl tezelfdertijd het handhaven van authentificatie voor de volledige boom.
* Inhoud van een modelopslagplaats zodanig dat de verificatievereisten van toepassing zijn op de gehele boomstructuur zonder dat geneste substructuren opnieuw van de vereiste hoeven te worden uitgesloten.
* U voorkomt als volgt het opgeven en vervolgens registreren van redundante aanmeldingspaden:

   * vertrouwen op overerving en vermijd het definiëren van geneste aanmeldingspaden;
   * Stel het optionele aanmeldingspad niet in op een waarde die overeenkomt met de standaardwaarde of een overgeërfde waarde,
   * de toepassingsontwikkelaars zouden moeten identificeren welke login wegen in de globale login-weg configuraties (zowel gebrek als afbeeldingen) verbonden aan `LoginSelectorHandler` zouden moeten worden gevormd.

## Vertegenwoordiging in de opslagplaats {#representation-in-the-repository}

### Beleidsrepresentatie CUG in de opslagplaats {#cug-policy-representation-in-the-repository}

De documentatie van het Eak behandelt hoe het nieuwe beleid van CUG in de bewaarplaats inhoud wordt weerspiegeld. Zie [deze pagina](https://jackrabbit.apache.org/oak/docs/security/authorization/cug.html#Representation_in_the_Repository) voor meer informatie.

### Verificatievereiste in de opslagplaats {#authentication-requirement-in-the-repository}

De behoefte aan een afzonderlijk authentificatievereiste wordt weerspiegeld in de inhoud van de bewaarplaats met een specifiek mixinknooptype dat bij de doelknoop wordt geplaatst. Het mixintype bepaalt een facultatieve bezit om een specifieke login pagina voor de boom te specificeren die door de doelknoop wordt bepaald.

De pagina die aan het aanmeldingspad is gekoppeld, kan zich binnen of buiten die structuur bevinden. Het zal van de authentificatievereiste worden uitgesloten.

```java
[granite:AuthenticationRequired]
      mixin
      - granite:loginPath (STRING)
```

## Het beheren van het Beleid van de CUG en de Vereiste van de Authentificatie {#managing-cug-policies-and-authentication-requirement}

### CUG-beleid beheren {#managing-cug-policies}

Het nieuwe type toegangsbeheerbeleid om leestoegang voor een CUG te beperken wordt beheerd gebruikend JCR toegangsbeheer API en volgt de mechanismen die met [JCR 2.0 specificatie](https://docs.adobe.com/content/docs/en/spec/jcr/2.0/16_Access_Control_Management.html) worden beschreven.

#### Een nieuw CUG-beleid instellen {#set-a-new-cug-policy}

Code om een nieuw beleid van de GECG op een knoop toe te passen die geen KUG had eerder geplaatst. Houd er rekening mee dat `getApplicablePolicies` alleen nieuwe beleidsregels retourneert die nog niet eerder zijn ingesteld. Uiteindelijk moet het beleid worden teruggeschreven en moeten de veranderingen worden voortgezet.

```java
String path = [...] // needs to be a supported, absolute path

Principal toAdd1 = [...]
Principal toAdd2 = [...]
Principal toRemove = [...]

AccessControlManager acMgr = session.getAccessControlManager();
PrincipalSetPolicy cugPolicy = null;

AccessControlPolicyIterator it = acMgr.getApplicablePolicies(path);
while (it.hasNext()) {
        AccessControlPolicy policy = it.nextAccessControlPolicy();
        if (policy instanceof PrincipalSetPolicy) {
           cugPolicy = (PrincipalSetPolicy) policy;
           break;
        }
}

if (cugPolicy == null) {
   log.debug("no applicable policy"); // path not supported or no applicable policy (e.g.
                                                   // the policy was set before)
   return;
}

cugPolicy.addPrincipals(toAdd1, toAdd2);
cugPolicy.removePrincipals(toRemove));

acMgr.setPolicy(path, cugPolicy); // as of this step the policy can be edited/removed
session.save();
```

#### Bewerk een bestaand CUG-beleid {#edit-an-existing-cug-policy}

De volgende stappen zijn nodig om een bestaand beleid van CUG uit te geven. Houd er rekening mee dat het gewijzigde beleid moet worden teruggeschreven en dat wijzigingen moeten worden voortgezet met `javax.jcr.Session.save()`.

```java
String path = [...] // needs to be a supported, absolute path

Principal toAdd1 = [...]
Principal toAdd2 = [...]
Principal toRemove = [...]

AccessControlManager acMgr = session.getAccessControlManager();
PrincipalSetPolicy cugPolicy = null;

for (AccessControlPolicy policy : acMgr.getPolicies(path)) {
     if (policy instanceof PrincipalSetPolicy) {
        cugPolicy = (PrincipalSetPolicy) policy;
        break;
     }
}

if (cugPolicy == null) {
   log.debug("no policy to edit"); // path not supported or policy not set before
   return;
}

if (cugPolicy.addPrincipals(toAdd1, toAdd2) || cugPolicy.removePrincipals(toRemove)) {
   acMgr.setPolicy(path, cugPolicy);
   session.save();
} else {
     log.debug("cug policy not modified");
}
```

### Effectief CUG-beleid ophalen {#retrieve-effective-cug-policies}

Het beheer van het toegangsbeheer JCR bepaalt een beste inspanningsmethode om het beleid terug te winnen dat op een bepaalde weg van kracht wordt. Wegens het feit dat de evaluatie van het beleid van de CUG voorwaardelijk is en van de overeenkomstige configuratie afhangt om worden toegelaten, is het roepen `getEffectivePolicies` een geschikte manier om te verifiëren of een bepaald beleid van de CUG in een bepaalde installatie van kracht wordt.

>[!NOTE]
>
>Gelieve te merken het verschil tussen `getEffectivePolicies` en het verdere codevoorbeeld op dat omhoog de hiërarchie loopt om te vinden als een bepaalde weg reeds deel van bestaande GG uitmaakt.

```java
String path = [...] // needs to be a supported, absolute path

AccessControlManager acMgr = session.getAccessControlManager();
PrincipalSetPolicy cugPolicy = null;

// log an debug message of all CUG policies that take effect at the given path
// there could be zero, one or many (creating nested CUGs is possible)
for (AccessControlPolicy policy : acMgr.getEffectivePolicies(path) {
     if (policy instanceof PrincipalSetPolicy) {
        String policyPath = "-";
        if (policy instanceof JackrabbitAccessControlPolicy) {
           policyPath = ((JackrabbitAccessControlPolicy) policy).getPath();
        }
        log.debug("Found effective CUG for path '{}' at '{}', path, policyPath);
     }
}
```

#### Overerfd CUG-beleid {#retrieve-inherited-cug-policies} ophalen

Alle geneste CUG&#39;s zoeken die op een bepaald pad zijn gedefinieerd, ongeacht of ze van kracht worden of niet. Zie de sectie [Configuratieopties](/help/sites-administering/closed-user-groups.md#configuration-options) voor meer informatie.

```java
String path = [...]

List<AccessControlPolicy> cugPolicies = new ArrayList<AccessControlPolicy>();
while (isSupportedPath(path)) {
     for (AccessControlPolicy policy : acMgr.getPolicies(path)) {
         if (policy instanceof PrincipalSetPolicy) {
            cugPolicies.add(policy);
         }
      }
      path = (PathUtils.denotesRoot(path)) ? null : PathUtils.getAncestorPath(path, 1);
}
```

#### CUG-beleid beheren door Pincipal {#managing-cug-policies-by-pincipal}

De uitbreidingen die door `JackrabbitAccessControlManager` worden bepaald die toestaan om toegangsbeheerbeleid door hoofd uit te geven worden niet uitgevoerd met het beheer van de toegangscontrole van de CUG, aangezien een beleid van de CUG altijd alle hoofden beïnvloedt: degenen die met `PrincipalSetPolicy` worden vermeld lees toegang terwijl alle andere hoofden zullen worden verhinderd om inhoud in de boom te lezen die door de doelknoop wordt bepaald.

De bijbehorende methoden retourneren altijd een lege beleidsarray, maar genereren geen uitzonderingen.

### Het beheren van het Vereiste van de Authentificatie {#managing-the-authentication-requirement}

Het creëren, de wijziging of de verwijdering van een nieuwe authentificatievereisten worden bereikt door het efficiënte knooptype van de doelknoop te veranderen. De eigenschap voor het optionele aanmeldingspad kan vervolgens worden geschreven met de gewone JCR API.

>[!NOTE]
>
>De wijzigingen aan een opgegeven hierboven vermelde doelnode worden alleen weerspiegeld in de Apache Sling Authenticator als `RequirementHandler` is geconfigureerd en het doel is opgenomen in de bomen die door de ondersteunde paden worden gedefinieerd (zie Opties voor sectie Configuration).
>
>Voor meer informatie, zie [Toewijzend de Types van Knoop van Mixin] (https://docs.adobe.com/docs/en/spec/jcr/2.0/10_Writing.html#10.10.3 Toewijzend de Types van Knoop van Mixin) en [Toevoegend Nodes en Plaatsende Eigenschappen] (https://docs.adobe.com/docs/en/spec/jcr/2.0/10_Writing.html#10.4 toevoegend Nodes en plaatsende Eigenschappen)

#### Nieuwe auteisen {#adding-a-new-auth-requirement} toevoegen

De stappen om een nieuw authentificatievereiste tot stand te brengen zijn hieronder gedetailleerd. Merk op dat het vereiste slechts met Apache Sling Authenticator zal worden geregistreerd als `RequirementHandler` voor de boom is gevormd die de doelknoop bevat.

```java
Node targetNode = [...]

targetNode.addMixin("granite:AuthenticationRequired");
session.save();
```

#### Voeg een Nieuwe Vereiste van de Auth met Login Weg {#add-a-new-auth-requirement-with-login-path} toe

Stappen om een nieuw authentificatievereiste met inbegrip van een login weg tot stand te brengen. Merk op, dat het vereiste en de uitsluiting voor de login weg slechts met Apache Sling Authenticator zullen worden geregistreerd als `RequirementHandler` voor de boom is gevormd die de doelknoop bevat.

```java
Node targetNode = [...]
String loginPath = [...] // STRING property

Node targetNode = session.getNode(path);
targetNode.addMixin("granite:AuthenticationRequired");

targetNode.setProperty("granite:loginPath", loginPath);
session.save();
```

#### Een bestaand aanmeldingspad wijzigen {#modify-an-existing-login-path}

De stappen om een bestaand login weg te veranderen zijn hieronder gedetailleerd. De wijziging wordt alleen geregistreerd bij de Apache Sling Authenticator als `RequirementHandler` is geconfigureerd voor de structuur die het doelknooppunt bevat. De vorige waarde van het aanmeldingspad wordt uit de registratie verwijderd. Deze wijziging heeft geen invloed op de vereiste auth die aan het doelknooppunt is gekoppeld.

```java
Node targetNode = [...]
String newLoginPath = [...] // STRING property

if (targetNode.isNodeType("granite:AuthenticationRequired")) {
   targetNode.setProperty("granite:loginPath", newLoginPath);
   session.save();
} else {
     log.debug("cannot modify login path property; mixin type missing");
}
```

#### Een bestaand aanmeldingspad verwijderen {#remove-an-existing-login-path}

Stappen om een bestaand aanmeldingspad te verwijderen. De ingang van de login weg zal slechts van Apache Sling Authenticator zijn niet geregistreerd als `RequirementHandler` voor de boom is gevormd die de doelknoop bevat. De auth-vereiste die aan het doelknooppunt is gekoppeld, wordt niet beïnvloed.

```java
Node targetNode = [...]

if (targetNode.hasProperty("granite:loginPath") &&
   targetNode.isNodeType("granite:AuthenticationRequired")) {
   targetNode.setProperty("granite:loginPath", null);
   session.save();
} else {
     log.debug("cannot remove login path property; mixin type missing");
}
```

U kunt ook de onderstaande methode gebruiken om hetzelfde doel te bereiken:

```java
String path = [...] // absolute path to target node

String propertyPath = PathUtils.concat(path, "granite:loginPath");
if (session.propertyExists(propertyPath)) {
    session.getProperty(propertyPath).remove();
    // or: session.removeItem(propertyPath);
    session.save();
}
```

#### Een auteitsvereiste {#remove-an-auth-requirement} verwijderen

Stappen om een bestaand authentificatievereiste te verwijderen. Het vereiste zal slechts van Apache Sling Authenticator niet worden geregistreerd als `RequirementHandler` voor de boom is gevormd die de doelknoop bevat.

```java
Node targetNode = [...]
targetNode.removeMixin("granite:AuthenticationRequired");

session.save();
```

#### Effectieve auteisen {#retrieve-effective-auth-requirements} ophalen

Er is geen speciale openbare API om alle effectieve verificatievereisten te lezen zoals die zijn geregistreerd bij de Apache Sling Authenticator. Nochtans, wordt de lijst blootgesteld in de systeemconsole bij `https://<serveraddress>:<serverport>/system/console/slingauth` onder &quot;**de sectie van de Vereiste van de Authentificatie Configuratie**&quot;.

In de volgende afbeelding ziet u de verificatievereisten van een AEM-publicatie-instantie met demo-inhoud. Het gemarkeerde pad van de communitypagina toont hoe een vereiste die wordt toegevoegd door de implementatie die in dit document wordt beschreven, wordt weerspiegeld in de Apache Sling Authenticator.

>[!NOTE]
>
>In dit voorbeeld is de eigenschap voor het optionele aanmeldingspad niet ingesteld. Bijgevolg is er geen tweede vermelding geregistreerd bij de authenticator.

![chlimage_1-24](assets/chlimage_1-24.jpeg)

#### Het effectieve aanmeldingspad ophalen {#retrieve-the-effective-login-path}

Er is momenteel geen openbare API om de login weg terug te winnen die op anoniem toegang tot van een middel zal ingaan dat authentificatie vereist. Zie sectieEvaluatie van Login Weg voor implementatiedetails op hoe de login weg wordt teruggewonnen.

Naast de aanmeldingspaden die met deze functie zijn gedefinieerd, zijn er echter andere manieren om het omleiden naar de aanmelding op te geven. Hiermee moet rekening worden gehouden bij het ontwerpen van het inhoudsmodel en de verificatievereisten van een bepaalde AEM.

#### De overgenomen auteisen {#retrieve-the-inherited-auth-requirement} ophalen

Net als bij het aanmeldingspad is er geen openbare API om de overgenomen verificatievereisten op te halen die in de inhoud zijn gedefinieerd. Het volgende voorbeeld laat zien hoe u alle verificatievereisten kunt weergeven die zijn gedefinieerd met een bepaalde hiërarchie, ongeacht of deze van kracht worden of niet. Zie [Configuratieopties](/help/sites-administering/closed-user-groups.md#configuration-options) voor meer informatie.

>[!NOTE]
>
>Men adviseert om zich op het overervingsmechanisme zowel voor authentificatievereisten als login weg te baseren en verwezenlijking van genestelde auteisen te vermijden.
>
>Zie [Evaluatie en overerving van verificatievereisten](#evaluation-and-inheritance-of-the-authentication-requirement), [Evaluatie van aanmeldingspad](#evaluation-of-login-path) en [Beste praktijken](#best-practices) voor meer informatie.

```java
String path = [...]
Node node = session.getNode(path);

Map<String, String> authRequirements = new ArrayList<String, String>();
while (isSupported(node)) {
     if (node.isNodeType("granite:AuthenticationRequired")) {
         String loginPath = (node.hasProperty("granite:loginPath") ?
                                     node.getProperty("granite:loginPath").getString() :
                                     "";
        authRequirements.put(node.getPath(), loginPath);
        node = node.getParent();
     }
}
```

### Het combineren van het Beleid van de KUG en de Vereiste {#combining-cug-policies-and-the-authentication-requirement} van de Authentificatie

De volgende lijst maakt een lijst van de geldige combinaties beleid van de CUG en het authentificatievereiste in een AEM instantie die beide modules heeft die door configuratie worden toegelaten.

| **Verificatie vereist** | **Aanmeldingspad** | **Beperkte leestoegang** | **Verwacht effect** |
|---|---|---|---|
| Ja | Ja | Ja | Een bepaalde gebruiker zal slechts de subtree kunnen bekijken duidelijk met het beleid van de GECG als de efficiënte toestemmingsevaluatie toegang verleent. Een niet-geverifieerde gebruiker wordt omgeleid naar de opgegeven aanmeldingspagina. |
| Ja | Nee | Ja | Een bepaalde gebruiker zal slechts de subtree kunnen bekijken duidelijk met het beleid van de GECG als de efficiënte toestemmingsevaluatie toegang verleent. Een niet-geverifieerde gebruiker wordt omgeleid naar een overgeërfde standaardaanmeldingspagina. |
| Ja | Ja | Nee | Een niet-geverifieerde gebruiker wordt omgeleid naar de opgegeven aanmeldingspagina. Of het al dan niet wordt toegestaan om de boom te bekijken duidelijk met auth-required hangt van de efficiënte toestemmingen van de individuele punten in die subtree af. Geen specifieke CUG die de leestoegang beperkt. |
| Ja | Nee | Nee | Een niet-geverifieerde gebruiker wordt omgeleid naar een overgeërfde standaardaanmeldingspagina. Of het al dan niet wordt toegestaan om de boom te bekijken duidelijk met de auteigenschap hangt van de efficiënte toestemmingen van de individuele punten in die subtree af. Geen specifieke CUG die de leestoegang beperkt. |
| Nee | Nee | Ja | Een bepaalde voor authentiek verklaarde of niet voor authentiek verklaarde gebruiker zal slechts de subboom kunnen bekijken duidelijk met het beleid van de GIDS als de efficiënte toestemmingsevaluatie toegang verleent. Een niet-geverifieerde gebruiker wordt gelijk behandeld en wordt niet omgeleid naar de aanmelding. |

>[!NOTE]
>
>De combinatie van &#39;Vereisten voor verificatie&#39; = Nee en &#39;Aanmeldingspad&#39; = Ja wordt hierboven niet vermeld omdat het &#39;Aanmeldingspad&#39; een optioneel kenmerk is dat is gekoppeld aan een Auth-Requirement. Het specificeren van een bezit JCR met die naam zonder het het bepalen mixintype toe te voegen zal geen effect hebben en zal door de overeenkomstige manager worden genegeerd.

## OSGi-componenten en -configuratie {#osgi-components-and-configuration}

Deze secties verstrekken een overzicht aan de componenten OSGi en de individuele configuratieopties die met de nieuwe implementatie van de CUG worden geïntroduceerd.

Zie ook de de afbeeldingsdocumentatie van de KUG voor een uitvoerige afbeelding van de configuratieopties tussen oude en nieuwe implementatie.

### Autorisatie: {#authorization-setup-and-configuration} instellen en configureren

De nieuwe, machtigingsgerelateerde onderdelen zijn opgenomen in de bundel **Oak CUG Authorization** ( `org.apache.jackrabbit.oak-authorization-cug`), die deel uitmaakt van de AEM standaardinstallatie. De bundel bepaalt een gescheiden vergunningsmodel dat wordt opgesteld als extra manier om gelezen toegang te beheren.

#### CUG-autorisatie {#setting-up-cug-authorization} instellen

Het instellen van CUG-autorisatie wordt gedetailleerd beschreven in de [relevante Apache-documentatie](https://jackrabbit.apache.org/oak/docs/security/authorization/cug.html#pluggability). Door gebrek, AEM heeft de vergunning van de GECG die in alle looppaswijzen wordt opgesteld. De stapsgewijze instructies kunnen ook worden gebruikt om de CUG-autorisatie uit te schakelen in die installaties waarvoor een andere instelling van de autorisatie vereist is.

#### Filter Referrer {#configuring-the-referrer-filter} configureren

U moet ook [het Verdelen Filter van de Referateur ](/help/sites-administering/security-checklist.md#the-sling-referrer-filter) met alle hostnames vormen die aan toegang tot AEM kunnen worden gebruikt; bijvoorbeeld via CDN, Load Balancer en andere.

Als het verwijzingsfilter niet wordt gevormd, dan worden de fouten, gelijkend op het volgende, gezien wanneer een gebruiker probeert om aan te melden bij een plaats van de CUG:

```shell
31.01.2017 13:49:42.321 *INFO* [qtp1263731568-346] org.apache.sling.security.impl.ReferrerFilter Rejected referrer header for POST request to /libs/granite/core/content/login.html/j_security_check : https://hostname/libs/granite/core/content/login.html?resource=%2Fcontent%2Fgeometrixx%2Fen%2Ftest-site%2Ftest-page.html&$$login$$=%24%24login%24%24&j_reason=unknown&j_reason_code=unknown
```

#### Kenmerken van OSGi-componenten {#characteristics-of-osgi-components}

De volgende twee componenten OSGi zijn geïntroduceerd om authentificatievereisten te bepalen en specifieke login wegen te specificeren:

* `org.apache.jackrabbit.oak.spi.security.authorization.cug.impl.CugConfiguration`
* `org.apache.jackrabbit.oak.spi.security.authorization.cug.impl.CugExcludeImpl`

**org.apache.jackrabbit.oak.spi.security.authentication.cug.impl.CugConfiguration**

<table>
 <tbody>
  <tr>
   <td>Label</td>
   <td>Apache Jackrabbit Oak CUG Configuration</td>
  </tr>
  <tr>
   <td>Beschrijving</td>
   <td>De configuratie van de vergunning specifiek aan opstelling en evalueert de toestemmingen van de KUG.</td>
  </tr>
  <tr>
   <td>Configuratieeigenschappen</td>
   <td>
    <ul>
     <li><code>cugSupportedPaths</code></li>
     <li><code>cugEnabled</code></li>
     <li><code>configurationRanking</code></li>
    </ul> <p>Zie ook <a href="#configuration-options">Configuratieopties</a> hieronder.</p> </td>
  </tr>
  <tr>
   <td>Configuratiebeleid</td>
   <td><code>ConfigurationPolicy.REQUIRE</code></td>
  </tr>
  <tr>
   <td>Verwijzingen</td>
   <td><code>CugExclude (ReferenceCardinality.OPTIONAL_UNARY)</code></td>
  </tr>
 </tbody>
</table>

**org.apache.jackrabbit.oak.spi.security.authentication.cug.impl.CugExcludeImpl**

<table>
 <tbody>
  <tr>
   <td>Label</td>
   <td>Apache Jackrabbit Oak CUG Exclusive List</td>
  </tr>
  <tr>
   <td>Beschrijving</td>
   <td>Staat toe om principaal(s) met de samengeperste naam (namen) van de evaluatie van de GG uit te sluiten.</td>
  </tr>
  <tr>
   <td>Configuratieeigenschappen</td>
   <td>
    <ul>
     <li><code>principalNames</code></li>
    </ul> <p>Zie ook de volgende sectie Configuration Options.</p> </td>
  </tr>
  <tr>
   <td>Configuratiebeleid</td>
   <td><code>ConfigurationPolicy.REQUIRE</code></td>
  </tr>
  <tr>
   <td>Verwijzingen</td>
   <td>NA</td>
  </tr>
 </tbody>
</table>

#### Configuratieopties {#configuration-options}

De belangrijkste configuratieopties zijn:

* `cugSupportedPaths`: Geef de substructuren op die CUG&#39;s kunnen bevatten. Er is geen standaardwaarde ingesteld
* `cugEnabled`: configuratieoptie om toestemmingsevaluatie voor het huidige beleid van CUG toe te laten.

De beschikbare configuratieopties verbonden aan de CUG-vergunning module zijn vermeld en meer gedetailleerd beschreven bij [Apache Oak Documentation](https://jackrabbit.apache.org/oak/docs/security/authorization/cug.html#configuration).

#### Exclusief princiepen van CUG-evaluatie {#excluding-principals-from-cug-evaluation}

Van de vorige uitvoering zijn individuele beginselen van de CUG-evaluatie vrijgesteld. De nieuwe vergunning van de GECG behandelt dit met een specifieke interface genoemd CugExclude. Apache Jackrabbit Oak 1.4 schepen met een standaardimplementatie die een vaste reeks principes evenals een uitgebreide implementatie uitsluit die individuele belangrijkste namen toestaat te vormen. De laatste is geconfigureerd in AEM publicatieinstanties.

Het gebrek sinds AEM 6.3 verhindert de volgende hoofden door beleid van de CG worden beïnvloed:

* beheerprincipes (beheerder, groep beheerders)
* servicegebruikersprincipes
* interne systeemprincipal in opslagplaats

Zie de tabel in de sectie [Standaardconfiguratie sinds AEM 6.3](#default-configuration-since-aem) hieronder voor meer informatie.

De uitsluiting van de groep &#39;beheerders&#39; kan worden gewijzigd of uitgebreid in de systeemconsole in de configuratiesectie van **Apache Jackrabbit Oak CUG Exclude List**.

Alternatief, is het mogelijk om een douaneimplementatie van de interface te verstrekken en op te stellen CugExclude om de reeks uitgesloten hoofden in het geval van speciale behoeften aan te passen. Zie de documentatie over [KUSTplukbaarheid](https://jackrabbit.apache.org/oak/docs/security/authorization/cug.html#pluggability) voor details en een voorbeeldimplementatie.

### Verificatie: {#authentication-setup-and-configuration} instellen en configureren

De nieuwe, aan verificatie gerelateerde onderdelen zijn opgenomen in de bundel **Adobe Granite Authentication Handler** ( `com.adobe.granite.auth.authhandler` versie 5.6.48). Deze bundel maakt deel uit van de AEM standaardinstallatie.

Om de vervanging van het authentificatievereiste voor de verouderde steun van de GN te plaatsen, moeten sommige componenten OSGi aanwezig en actief in een bepaalde AEM installatie zijn. Zie **Kenmerken van OSGi-componenten** hieronder voor meer informatie.

>[!NOTE]
>
>Wegens de verplichte configuratieoptie met RequirementHandler, zullen de authentificatie verwante delen slechts actief zijn als de eigenschap door een reeks gesteunde wegen te specificeren is toegelaten. Bij een standaard AEM installatie is de functie uitgeschakeld in de modus voor het uitvoeren van de auteur en ingeschakeld voor /content in de modus voor publiceren.

**Kenmerken van OSGi-componenten**

De volgende 2 componenten OSGi zijn geïntroduceerd om authentificatievereisten te bepalen en specifieke login wegen te specificeren:

* `com.adobe.granite.auth.requirement.impl.RequirementService`
* `com.adobe.granite.auth.requirement.impl.DefaultRequirementHandler`

**com.adobe.granite.auth.requirements.impl.RequirementService**

<table>
 <tbody>
  <tr>
   <td>Label</td>
   <td>-</td>
  </tr>
  <tr>
   <td>Beschrijving</td>
   <td>Speciale OSGi-service voor verificatievereisten die een waarnemer registreert voor inhoudswijzigingen die van invloed zijn op de auth-requirements (via het mixintype <code>granite:AuthenticationRequirement</code>) en aanmeldingspaden met, worden blootgesteld aan <code>LoginSelectorHandler</code>. </td>
  </tr>
  <tr>
   <td>Configuratieeigenschappen</td>
   <td>-</td>
  </tr>
  <tr>
   <td>Configuratiebeleid</td>
   <td><code>ConfigurationPolicy.OPTIONAL</code></td>
  </tr>
  <tr>
   <td>Verwijzingen</td>
   <td>
    <ul>
     <li><code>RequirementHandler (ReferenceCardinality.MANDATORY_UNARY)</code></li>
     <li><code>Executor (ReferenceCardinality.MANDATORY_UNARY)</code></li>
    </ul> </td>
  </tr>
 </tbody>
</table>

**com.adobe.granite.auth.requirements.impl.DefaultRequirementHandler**

| Label | Adobe Granite-verificatie vereist en Aanmeldingspad-handler |
|---|---|
| Beschrijving | `RequirementHandler` implementatie die de vereisten voor Apache Sling-verificatie en de bijbehorende uitsluiting voor de bijbehorende aanmeldingspaden bijwerkt. |
| Configuratieeigenschappen | `supportedPaths` |
| Configuratiebeleid | `ConfigurationPolicy.REQUIRE` |
| Verwijzingen | NA |

#### Configuratieopties {#configuration-options-1}

De authentificatiegerelateerde delen van CUG herschrijven slechts met één enkele configuratieoptie verbonden aan de Vereiste van de Authentificatie van de Adobe Granite en de Bediener van de Weg van de Login komen:

**&quot;De Vereiste van de authentificatie en de Bediener van de Weg van de Login&quot;**

<table>
 <tbody>
  <tr>
   <td>Eigenschap</td>
   <td>Type</td>
   <td>Standaardwaarde</td>
   <td>Beschrijving</td>
  </tr>
  <tr>
   <td><p>Label = ondersteunde paden</p> <p>Name = 'supportedPaths'</p> </td>
   <td>Set&lt;String&gt;</td>
   <td>-</td>
   <td>Paden waaronder de authentificatievereisten door deze manager zullen worden geëerbiedigd. Verlaat deze configuratie unset als u <code>granite:AuthenticationRequirement</code> mixintype aan knopen wilt toevoegen zonder hen (bijvoorbeeld, op auteursinstanties) te hebben afgedwongen. Als deze optie ontbreekt, wordt de functie uitgeschakeld. </td>
  </tr>
 </tbody>
</table>

## Standaardconfiguratie sinds AEM 6.3 {#default-configuration-since-aem}

De nieuwe installaties van AEM zullen door gebrek de nieuwe implementaties zowel voor de vergunning als authentificatiegerelateerde delen van de eigenschap van CUG gebruiken. De oude implementatie &quot;Adobe Granite Closed User Group (CUG) Support&quot; is vervangen en wordt standaard uitgeschakeld in alle AEM installaties. De nieuwe implementaties zullen in plaats daarvan als volgt worden toegelaten:

### Auteurinstanties {#author-instances}

| **&quot;Apache Jackrabbit Oak CUG Configuration&quot;** | **Toelichting** |
|---|---|
| Ondersteunde paden `/content` | Toegangsbeheer voor CUGpolicies is ingeschakeld. |
| FALSE CUG-evaluatie ingeschakeld | Evaluatie van machtigingen is uitgeschakeld. CUG-beleid heeft geen effect. |
| Rangorde | 200 | Zie documentatie van eikel. |

>[!NOTE]
>
>Geen configuratie voor **Apache Jackrabbit Oak CUG Exclude List** en **Adobe granite Authentication Requirement and Login Path Handler** is aanwezig op standaard ontwerpinstanties.

### Exemplaren {#publish-instances} publiceren

| **&quot;Apache Jackrabbit Oak CUG Configuration&quot;** | **Toelichting** |
|---|---|
| Ondersteunde paden `/content` | Toegangsbeheer voor CUG-beleid wordt ingeschakeld onder de geconfigureerde paden. |
| WAAR VOOR CUG-evaluatie ingeschakeld | De evaluatie van de toestemming wordt toegelaten onder de gevormde wegen. CUG-beleid wordt van kracht op `Session.save()`. |
| Rangorde | 200 | Zie documentatie van eikel. |

| **&quot;Apache Jackrabbit Oak CUG Exclusive List&quot;** | **Toelichting** |
|---|---|
| Hoofdnaambeheerders | Sluit beheerders hoofd van de evaluatie van de KUG uit. |

| **&quot;Adobe Granite Authentication Required and Login Path Handler&quot;** | **Toelichting** |
|---|---|
| Ondersteunde paden `/content` | Verificatievereisten zoals gedefinieerd in de repository door middel van het `granite:AuthenticationRequired` mixintype worden van kracht onder `/content` op `Session.save()`. Verschuivende verificator wordt bijgewerkt. Het toevoegen van het mixintype buiten de ondersteunde paden wordt genegeerd. |

## Vereiste {#disabling-cug-authorization-and-authentication-requirement} voor CUG-autorisatie en -verificatie uitschakelen

De nieuwe implementatie kan volledig worden uitgeschakeld als een bepaalde installatie geen gebruik maakt van CUG&#39;s of andere middelen gebruikt voor verificatie en autorisatie.

### CUG-autorisatie {#disable-cug-authorization} uitschakelen

Raadpleeg de [CUG pluggability](https://jackrabbit.apache.org/oak/docs/security/authorization/cug.html#pluggability) documentatie voor meer informatie over het verwijderen van het CUG-machtigingsmodel uit de samengestelde machtigingsinstellingen.

### Verificatievereiste {#disable-the-authentication-requirement} uitschakelen

Om steun voor het authentificatievereiste zoals voorzien door de `granite.auth.authhandler` module onbruikbaar te maken is het voldoende om de configuratie verbonden aan **de Vereiste van de Authentificatie van de Adobe graniet en de Handler van de Weg van de Login** te verwijderen.

>[!NOTE]
>
>Houd er echter rekening mee dat als u de configuratie verwijdert, het mixintype niet wordt verwijderd. Dit type was nog steeds van toepassing op knooppunten zonder dat dit effect had.

## Interactie met andere modules {#interaction-with-other-modules}

### Apache Jackrabbit API {#apache-jackrabbit-api}

Om het nieuwe type toegangsbeheerbeleid te weerspiegelen dat door het de vergunningsmodel van de GG wordt gebruikt, is API die door Apache Jackrabbit wordt bepaald uitgebreid. Aangezien versie 2.11.0 van de `jackrabbit-api` module een nieuwe interface genoemd `org.apache.jackrabbit.api.security.authorization.PrincipalSetPolicy` bepaalt, die zich van `javax.jcr.security.AccessControlPolicy` uitbreidt.

### Apache Jackrabbit FileVault {#apache-jackrabbit-filevault}

Het importmechanisme van Apache Jackrabbit FileVault is aangepast aan het toegangsbeheerbeleid van het type `PrincipalSetPolicy`.

### Apache Sling Content Distribution {#apache-sling-content-distribution}

Zie de bovenstaande [sectie Apache Jackrabbit FileVault](/help/sites-administering/closed-user-groups.md#apache-jackrabbit-filevault).

### Adobe granietreplicatie {#adobe-granite-replication}

De replicatiemodule is lichtjes aangepast om het beleid van de CUG tussen verschillende AEM instanties te kunnen herhalen:

* `DurboImportConfiguration.isImportAcl()` wordt letterlijk geïnterpreteerd en heeft alleen invloed op de uitvoering van het toegangsbeheerbeleid  `javax.jcr.security.AccessControlList`

* `DurboImportTransformer` zal slechts deze configuratie voor ware ACLs respecteren
* Ander beleid zoals `org.apache.jackrabbit.api.security.authorization.PrincipalSetPolicy` instanties die door het de vergunningsmodel van de GG worden gecreeerd zal altijd worden herhaald en de configuratieoptie `DurboImportConfiguration.isImportAcl` () zal worden genegeerd.

Er is één beperking van het repliceren van beleid van CUG. Als een bepaald beleid van de KUG wordt verwijderd zonder het overeenkomstige mixin knooptype `rep:CugMixin,` te verwijderen zal de verwijdering niet op replicatie worden weerspiegeld. Dit probleem is opgelost door de mix bij het verwijderen van het beleid altijd te verwijderen. De beperking kan desondanks opduiken als het mixintype handmatig wordt toegevoegd.

### Adobe graniet-verificatiehandler {#adobe-granite-authentication-handler}

De verificatiehandler **Adobe Granite HTTP Header Authentication Handler** die wordt geleverd met de bundel `com.adobe.granite.auth.authhandler` bevat een verwijzing naar de `CugSupport`-interface die door dezelfde module is gedefinieerd. Het wordt gebruikt om het &quot;domein&quot;in bepaalde omstandigheden te berekenen, die terug naar het domein vallen dat met de manager wordt gevormd.

Dit is aangepast om de verwijzing naar `CugSupport` facultatief te maken om maximale achterwaartse verenigbaarheid te verzekeren als een bepaalde opstelling besluit om de vervangen implementatie opnieuw toe te laten. Installaties die de implementatie gebruiken, krijgen niet langer het domein dat uit de CUG-implementatie wordt geëxtraheerd, maar geven altijd het domein weer zoals gedefinieerd met **Adobe Granite HTTP Header Authentication Handler**.

>[!NOTE]
>
>Standaard is de **Adobe Granite HTTP Header Authentication Handler** alleen geconfigureerd in de publicatiemodus voor uitvoering met de optie &quot;Aanmeldingspagina uitschakelen&quot; ( `auth.http.nologin`) ingeschakeld.

### AEM LiveCopy {#aem-livecopy}

Het configureren van CUG&#39;s in combinatie met LiveCopy wordt in de opslagplaats vertegenwoordigd door toevoeging van één extra knooppunt en één extra eigenschap, en wel als volgt:

* `/content/we-retail/us/en/blueprint/rep:cugPolicy`
* `/content/we-retail/us/en/LiveCopy@granite:loginPath`

Beide elementen worden gemaakt onder `cq:Page`. Met het huidige ontwerp, behandelt MSM slechts knopen en eigenschappen die onder `cq:PageContent` (`jcr:content`) knoop zijn.

Daarom kunnen CUG-groepen niet worden teruggedraaid van een blauwdruk naar een Live Copy. Houd hier rekening mee wanneer u een Live kopie instelt.

## Veranderingen met de Nieuwe Implementatie van de GUG {#changes-with-the-new-cug-implementation}

Het doel van deze sectie is een overzicht te geven van de wijzigingen die in de CUG-functie zijn aangebracht, en een vergelijking te maken tussen de oude en de nieuwe implementatie. Het maakt een lijst van de veranderingen die van invloed zijn op de manier de steun van CUG wordt gevormd en beschrijft hoe en door wie CUGs in de bewaarplaats inhoud wordt beheerd.

### Verschillen in de Opstelling en de Configuratie {#differences-in-cug-setup-and-configuration} van de KUG

De vervangen OSGi-component **Adobe granite Closed User Group (CUG) Support** ( `com.day.cq.auth.impl.cug.CugSupportImpl`) is vervangen door nieuwe componenten om delen van de voormalige CUG-functionaliteit die betrekking hebben op autorisatie en verificatie afzonderlijk te kunnen verwerken.

## Verschillen in het beheren van CUG&#39;s in de inhoud van de opslagplaats {#differences-in-managing-cugs-in-the-repository-content}

In de volgende secties worden de verschillen tussen de oude en de nieuwe implementaties vanuit het perspectief van implementatie en veiligheid beschreven. Terwijl de nieuwe implementatie de zelfde functionaliteit probeert te verstrekken, zijn er subtiele veranderingen die belangrijk zijn om te weten wanneer het gebruiken van nieuwe CUG.

### Verschillen met betrekking tot vergunningen {#differences-with-regards-to-authorization}

De belangrijkste verschillen vanuit het oogpunt van vergunningverlening zijn samengevat in de onderstaande lijst:

**Specifieke inhoud van het Toegangsbeheer voor CUGs**

In de oude implementatie werd het model van de standaardvergunning gebruikt om het beleid van de toegangsbeheerlijst te manipuleren bij publiceren, die om het even welke bestaande ACEs door de opstelling vervangen die door CUG wordt gemachtigd. Dit werd geactiveerd door het schrijven van reguliere, resterende JCR-eigenschappen die tijdens de publicatie werden geïnterpreteerd.

Met de nieuwe implementatie wordt de opstelling van het toegangsbeheer van het standaard vergunningsmodel niet beïnvloed door enige KUG die wordt gecreeerd, wordt gewijzigd of wordt verwijderd. In plaats daarvan wordt een nieuw type beleid genoemd `PrincipalSetPolicy` toegepast als extra inhoud van de toegangscontrole op de doelknoop. Dit extra beleid zal als kind van de doelknoop worden gevestigd en zou een sibling van de standaardbeleidsknoop zijn indien aanwezig.

**CUG-beleid bewerken in Access Control Management**

Deze beweging van resterende eigenschappen JCR aan een specifiek toegangsbeheerbeleid heeft een invloed op de toestemming nodig om het vergunningsdeel van de eigenschap van de GG tot stand te brengen of te wijzigen. Aangezien dit als een wijziging wordt beschouwd om toegang te krijgen tot inhoud, vereist het `jcr:readAccessControl` en `jcr:modifyAccessControl` voorrechten om aan de bewaarplaats te worden geschreven. Daarom kunnen alleen inhoudsauteurs die gemachtigd zijn om de inhoud van het toegangsbeheer van een pagina te wijzigen, deze inhoud instellen of wijzigen. Dit staat in schril contrast met de oude implementatie waar de capaciteit om regelmatige eigenschappen te schrijven JCR voldoende was, resulterend in een voorrechtescalatie.

**Doelknooppunt gedefinieerd door beleid**

Van het beleid van de CUG wordt verwacht om bij de knoop worden gecreeerd JCR die de subboom bepaalt aan beperkte lees toegang te worden onderworpen. Dit is waarschijnlijk een AEM pagina als de CUG wordt verwacht voor de gehele boom.

Merk op dat het plaatsen van het beleid van de GIDS slechts bij jcr:inhoudsknoop onder een bepaalde pagina wordt gevestigd slechts toegang tot de inhoud s.str van een bepaalde pagina zal beperken maar niet op om het even welke siblings of kindpagina&#39;s van kracht zal worden. Dit kan een geldig gebruiksgeval zijn en het is mogelijk om met een bewaargegevensopslagredacteur te bereiken die toestaat om fijnkorrelige inhoud van de toegangsinhoud toe te passen. Nochtans, contrasteert het de vroegere implementatie waar het plaatsen van een cq:cugEnabled bezit op jcr:content knoop intern aan de paginaknooppunt werd opnieuw in kaart gebracht. Deze toewijzing wordt niet meer uitgevoerd.

**Evaluatie van machtigingen met CUG-beleid**

De beweging van de oude steun van de GIDS aan een extra vergunningsmodel, verandert de manier efficiënte gelezen toestemmingen worden geëvalueerd. Zoals beschreven in de [Jackrabbit documentatie](https://jackrabbit.apache.org/oak/docs/security/authorization/composite.html), zal een bepaalde aangever die wordt toegestaan om `CUGcontent` te bekijken slechts leestoegang worden verleend als de toestemmingsevaluatie van alle modellen die in de Oak bewaarplaats worden gevormd leestoegang verleent.

Met andere woorden, voor de evaluatie van de efficiënte toestemmingen, zowel `CUGPolicy` als de standaardingangen van het toegangsbeheer zullen in aanmerking worden genomen en de lees toegang op de inhoud van de GIDS zal slechts worden verleend als het door beide types van beleid wordt verleend. In een standaard AEM publiceer installatie waar leestoegang tot de volledige `/content` boom voor iedereen wordt verleend, zal het effect van het beleid van CUG het zelfde als met de oude implementatie zijn.

**Evaluatie op aanvraag**

Met het machtigingsmodel CUG kunt u het beheer van toegangsbeheer en de evaluatie van machtigingen afzonderlijk inschakelen:

* toegangsbeheerbeheer wordt toegelaten als de module één of vele gesteunde wegen heeft waar de KUGs kan worden gecreeerd
* De toestemmingsevaluatie wordt slechts toegelaten als de optie **CUG Evaluatie Toegelaten** extra wordt gecontroleerd.

In de nieuwe AEM standaardopstellingsevaluatie van het beleid van de GIDS wordt het slechts toegelaten met &quot;publiceer&quot;looppaswijze. Zie de details op [standaardconfiguratie sinds AEM 6.3](#default-configuration-since-aem) voor meer details. Dit kan worden geverifieerd door het effectieve beleid voor een bepaald pad te vergelijken met het beleid dat in de inhoud is opgeslagen. Het efficiënte beleid zal slechts worden getoond in het geval de toestemmingsevaluatie voor CUGs wordt toegelaten.

Zoals hierboven verklaard wordt het beleid van de toegangscontrole van de GG nu altijd opgeslagen in de inhoud maar de evaluatie van de efficiënte toestemmingen die uit dat beleid voortvloeien zal slechts worden afgedwongen als **CUG Evaluatie Toegelaten** in de systeemconsole bij Apache Jackrabbit Oak **CUG Configuration wordt aangezet.** Deze optie is standaard alleen beschikbaar in de uitvoermodus Publiceren.

### Verschillen met betrekking tot verificatie {#differences-with-regards-to-authentication}

De verschillen in authenticatie worden hieronder beschreven.

#### Speciaal mixintype voor verificatievereisten {#dedicated-mixin-type-for-authentication-requirement}

In de vorige implementatie werden zowel de verificatie- als de verificatieaspecten van een CUG geactiveerd door één JCR-eigenschap ( `cq:cugEnabled`). Wat de authentificatie betreft, resulteerde dit in een bijgewerkte lijst van authentificatievereisten zoals die met de implementatie van de Authenticator van Apache Sling wordt opgeslagen. Met de nieuwe implementatie wordt hetzelfde resultaat bereikt door het doelknooppunt te markeren met een toegewezen mixintype ( `granite:AuthenticationRequired`).

#### Eigenschap voor het uitsluiten van aanmeldingspad {#property-for-excluding-login-path}

Het mixintype bepaalt één enkele, facultatieve bezit genoemd `granite:loginPath`, die fundamenteel aan het `cq:cugLoginPage` bezit beantwoordt. In tegenstelling tot de vorige implementatie zal het login wegbezit slechts worden gerespecteerd als zijn verklarend knooptype de vermelde mixin is. Het toevoegen van een eigenschap met die naam zonder het mixintype in te stellen, heeft geen effect en er wordt noch een nieuwe vereiste, noch een uitsluiting voor het aanmeldingspad gerapporteerd aan de authenticator.

#### Voorrecht voor verificatievereisten {#privilege-for-authentication-requirement}

Voor het toevoegen of verwijderen van een mixintype moet `jcr:nodeTypeManagement`-bevoegdheid worden verleend. In de vorige implementatie, wordt `jcr:modifyProperties` voorrecht gebruikt om het resterende bezit uit te geven.

Wat de `granite:loginPath` betreft wordt het zelfde voorrecht vereist om het bezit toe te voegen, te wijzigen of te verwijderen.

#### Doelknooppunt gedefinieerd door mixintype {#target-node-defined-by-mixin-type}

Er worden verificatievereisten verwacht die worden gemaakt op het JCR-knooppunt dat de subboomstructuur definieert voor gedwongen aanmelding. Dit zal waarschijnlijk een AEM Pagina zijn voor het geval dat de CUG naar verwachting de volledige boom zal beïnvloeden en UI voor de nieuwe implementatie zal bijgevolg het auto-vereiste mixintype op de paginaknooppunt toevoegen.

Het plaatsen van het beleid van de GIDS slechts bij jcr:inhoudsknoop die onder een bepaalde pagina wordt gevestigd zal slechts toegang tot de inhoud beperken, maar zal niet op de paginaknoop zelf noch op om het even welke kindpagina&#39;s van invloed zijn.

Dit kan een geldig scenario zijn en is mogelijk met een bewaargegevensverwerker die toestaat om de mixin bij om het even welk knooppunt te plaatsen. Nochtans, contrasteert het gedrag de vroegere implementatie, waar het plaatsen van een bezit cq:cugEnabled of cq:cugLoginPage op jcr:content intern werd opnieuw in kaart gebracht uiteindelijk aan de paginaknooppunt. Deze toewijzing wordt niet meer uitgevoerd.

#### Gevormde Gesteunde Wegen {#configured-supported-paths}

Zowel zal `granite:AuthenticationRequired` mixintype als granite:loginPath bezit slechts binnen het werkingsgebied worden gerespecteerd dat door de reeks van **Ondersteunde Wegen** configuratieoptie aanwezig met **de Vereisten van de Authentificatie van de Graniet van de Adobe en de Handler van de Weg van de Login** wordt bepaald. Als er geen paden zijn opgegeven, is de functie voor de vereiste verificatie geheel uitgeschakeld. In dit geval wordt het mixintype en de eigenschap van kracht wanneer het wordt toegevoegd aan of ingesteld op een bepaald JCR-knooppunt.

### Toewijzing van JCR-inhoud, OSGi-services en configuraties {#mapping-of-jcr-content-osgi-services-and-configurations}

Het document hieronder verstrekt een uitvoerige afbeelding van de diensten OSGi, configuraties en bewaarplaats inhoud tussen de oude en nieuwe implementatie.

CUG-toewijzing sinds AEM 6.3

[Bestand ophalen](assets/cug-mapping.pdf)

## CUG {#upgrade-cug} bijwerken

### Bestaande installaties die de afgekeurde CUG {#existing-installations-using-the-deprecated-cug} gebruiken

De oude implementatie van de CUG-ondersteuning is vervangen en wordt in toekomstige versies verwijderd. Het wordt aanbevolen over te schakelen op de nieuwe implementaties wanneer u een upgrade uitvoert van een lagere versie dan AEM 6.3.

Voor bijgewerkte AEM installatie, is het belangrijk om ervoor te zorgen dat slechts één implementatie van CUG wordt toegelaten. De combinatie van de nieuwe en de oude, verouderde ondersteuning van CUG wordt niet getest en kan ongewenste werking veroorzaken:

* botsingen in de Stijlauthenticator met betrekking tot authentificatievereisten
* ontkende leestoegang wanneer de ACL opstelling verbonden aan de oude collides van de CUG met een nieuw beleid van de CUG.

### Bestaande CUG-inhoud {#migrating-existing-cug-content} migreren

Adobe biedt een hulpmiddel voor het migreren naar de nieuwe CUG-implementatie. Voer de volgende stappen uit om het te gebruiken:

1. Ga naar `https://<serveraddress>:<serverport>/system/console/cug-migration` om het gereedschap te openen.
1. Voer het hoofdpad in waarop u CUG&#39;s wilt controleren en druk op de knop **Droge run** uitvoeren. Hiermee wordt gescand op CUG&#39;s die in aanmerking komen voor conversie op de geselecteerde locatie.
1. Nadat u de resultaten hebt herzien, druk **voer migratie** knoop uit om aan de nieuwe implementatie te migreren.

>[!NOTE]
>
>Als u problemen tegenkomt, is het mogelijk om een specifiek logger op **DEBUG** niveau op `com.day.cq.auth.impl.cug` op te zetten om de output van het migratiehulpmiddel te krijgen. Zie [Logboekregistratie](/help/sites-deploying/configure-logging.md) voor meer informatie over hoe te om dit te doen.

