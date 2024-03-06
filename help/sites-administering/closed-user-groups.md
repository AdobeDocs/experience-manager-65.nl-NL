---
title: Gesloten gebruikersgroepen in AEM
description: Leer over Gesloten Gebruikersgroepen en de voordelen die zij aan scalability en veiligheid in AEM brengen.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
docset: aem65
exl-id: 39e35a07-140f-4853-8f0d-8275bce27a65
feature: Security
source-git-commit: 9d497413d0ca72f22712581cf7eda1413eb8d643
workflow-type: tm+mt
source-wordcount: '6650'
ht-degree: 0%

---

# Gesloten gebruikersgroepen in AEM{#closed-user-groups-in-aem}

## Inleiding {#introduction}

Sinds AEM 6.3, is er een nieuwe gesloten implementatie van de Groep van de Gebruiker bedoeld om de prestaties, scalability, en veiligheidskwesties te behandelen die met de bestaande implementatie worden voorgesteld.

>[!NOTE]
>
>Ter wille van de eenvoud wordt in deze documentatie de afkorting CUG gebruikt.

Het doel van de nieuwe implementatie is om waar nodig bestaande functionaliteit te bestrijken en tegelijk problemen en ontwerpbeperkingen van oudere versies aan te pakken. Het resultaat is een nieuw ontwerp van CUG met de volgende kenmerken:

* een duidelijke scheiding tussen authenticatie- en autorisatieelementen, die afzonderlijk of in combinatie kunnen worden gebruikt;
* Het specifieke vergunningsmodel om op de beperkte leestoegang bij de gevormde bomen van de GG te wijzen zonder andere opstelling en toestemmingsvereisten van de toegangscontrole te storen;
* Scheiding tussen de opstelling van het toegangsbeheer van beperkte gelezen toegang, die op auteursinstanties, en toestemmingsevaluatie nodig is die slechts bij publiceren is;
* Bewerken van beperkte leestoegang zonder escalatie met bevoegdheden;
* Specifieke uitbreiding van knooppunttype om de authenticatievereiste te markeren;
* Optioneel aanmeldpad dat is gekoppeld aan de verificatievereiste.

### De nieuwe implementatie van de aangepaste gebruikersgroep {#the-new-custom-user-group-implementation}

Een CUG zoals deze in de context van AEM bekend is, bestaat uit de volgende stappen:

* Beperk leestoegang op de boom die moet worden beschermd en sta slechts lezen voor hoofden toe die of met een bepaalde instantie van de GG vermeld zijn of van de evaluatie van de GG helemaal worden uitgesloten. Dit wordt de **autorisatie** element.
* Afdwingen van verificatie op een bepaalde structuur en optioneel een specifieke aanmeldingspagina opgeven voor die structuur die vervolgens wordt uitgesloten. Dit wordt de **verificatie** element.

De nieuwe implementatie is ontworpen om een lijn te trekken tussen de authenticatie en de autorisatieonderdelen. Met ingang van AEM 6.3 is het mogelijk leestoegang te beperken zonder expliciet een verificatievereiste toe te voegen. Bijvoorbeeld, als een bepaalde instantie volledig authentificatie vereist of een bepaalde boom verblijft reeds in een subboom die authentificatie reeds vereist.

Eveneens, kan een bepaalde boom met een authentificatievereiste worden gemerkt zonder de efficiënte toestemmingsopstelling te veranderen. De combinaties en resultaten worden vermeld in de [Het combineren van het Beleid van de KUG en de Vereisten van de Authentificatie](/help/sites-administering/closed-user-groups.md#combining-cug-policies-and-the-authentication-requirement) sectie.

## Overzicht {#overview}

### Autorisatie: Leestoegang beperken {#authorization-restricting-read-access}

De belangrijkste eigenschap van een CUG beperkt leestoegang op een bepaalde boom in de inhoudsbewaarplaats voor iedereen behalve geselecteerde hoofden. In plaats van het manipuleren van de standaardtoegangsbeheerinhoud op de vlucht neemt de nieuwe implementatie een verschillende benadering door een specifiek type van toegangsbeheerbeleid te bepalen dat een KUG vertegenwoordigt.

#### Toegangscontrolebeleid voor CUG {#access-control-policy-for-cug}

Dit nieuwe type beleid heeft de volgende kenmerken:

* Toegangscontrolebeleid van het type org.apache.jackrabbit.api.security.authentication.PrincipalSetPolicy (gedefinieerd door de Apache Jackrabbit-API);
* PrincipalSetPolicy verleent voorrechten aan een wijzigbare reeks principes;
* De toegekende bevoegdheden en de reikwijdte van het beleid zijn een detail van de uitvoering.

De implementatie van PrincipalSetPolicy die wordt gebruikt om CUGs te vertegenwoordigen bepaalt daarnaast:

* Het beleid van CUG verleent slechts leestoegang tot regelmatige punten JCR (bijvoorbeeld, wordt de inhoud van de toegangscontrole uitgesloten);
* Het werkingsgebied wordt bepaald door de toegang-gecontroleerde knoop die het beleid van de GECG houdt;
* Het beleid van de CUG kan worden genesteld, begint een genestelde KUG een nieuwe KUG zonder de belangrijkste reeks van &quot;ouder&quot;KUG over te nemen;
* Het effect van het beleid, als de evaluatie wordt toegelaten, wordt geërft aan volledige subtree neer aan volgende genestelde KUG.

Dit beleid van CUG wordt opgesteld aan een AEM instantie door een afzonderlijke vergunningsmodule genoemd oak-vergunning-insect. Deze module komt met zijn eigen beheer van toegangsbeheer en toestemmingsevaluatie. Met andere woorden, de standaard AEM installatie verzendt een configuratie van de opslagplaats voor eik-inhoud die meerdere machtigingsmechanismen combineert. Zie voor meer informatie [deze pagina op de Apache Oak-documentatie](https://jackrabbit.apache.org/oak/docs/security/authorization/composite.html).

In deze samengestelde opstelling, vervangt een nieuwe KUG niet de bestaande inhoud van het toegangsbeheer in bijlage aan de doelknoop. In plaats daarvan, is het een aanvulling die ook later kan worden verwijderd zonder het originele toegangsbeheer te beïnvloeden, dat door gebrek in AEM een toegangsbeheerlijst zou zijn.

In tegenstelling tot de vorige implementatie, worden het nieuwe beleid van CUG altijd erkend en behandeld als inhoud van de toegangscontrole. Dit houdt in dat ze worden gemaakt en bewerkt met de API voor toegangsbeheer van de JCR. Zie de klasse [CUG-beleid beheren](#managing-cug-policies) sectie.

#### Evaluatie van machtigingen voor CUG-beleid {#permission-evaluation-of-cug-policies}

Naast een specifiek toegangsbeheerbeheer voor CUGs, laat het nieuwe vergunningsmodel u voorwaardelijk toestemmingsevaluatie voor zijn beleid toelaten. Dit laat u opstelling het beleid van de GIDS in een het opvoeren milieu, en laat slechts evaluatie van de efficiënte toestemmingen toe zodra herhaald aan het productiemilieu.

De evaluatie van de toestemming voor het beleid van de CUG en de interactie met het gebrek of om het even welk extra vergunningsmodel volgt het patroon dat voor veelvoudige vergunningsmechanismen in Apache Jackrabbit Oak wordt ontworpen. Dat wil zeggen dat een bepaalde set machtigingen alleen wordt verleend als en alleen als alle modellen toegang verlenen. Zie [deze pagina](https://jackrabbit.apache.org/oak/docs/security/authorization/composite.html) voor meer informatie .

De volgende kenmerken zijn voor de toestemmingsevaluatie verbonden aan het vergunningsmodel van toepassing dat wordt ontworpen om het beleid van de CUG te behandelen en te evalueren:

* Het behandelt slechts gelezen toestemmingen voor regelmatige knopen en eigenschappen, maar het lezen van toegangsbeheerinhoud
* Het behandelt geen schrijftoestemmingen noch om het even welk soort toestemmingen die voor wijziging van beschermde inhoud JCR (toegangsbeheer, knooptypeinformatie, versioning, sluiting, of gebruikersbeheer worden vereist). Deze toestemmingen worden niet beïnvloed door een beleid van de CUG en zullen niet door het bijbehorende vergunningsmodel worden geëvalueerd. Of deze toestemmingen worden verleend hangt van de andere modellen af die in de veiligheidsopstelling worden gevormd.

Het effect van één enkel beleid van CUG op toestemmingsevaluatie kan als volgt worden samengevat:

* Leestoegang wordt ontzegd voor iedereen behalve onderwerpen die uitgesloten hoofden of hoofden bevatten die in het beleid worden vermeld;
* Het beleid wordt van kracht op de toegang-gecontroleerde knoop die het beleid en zijn eigenschappen houdt;
* Het effect wordt ook geërft onderaan de hiërarchie - dat wil zeggen, de puntboom die door de toegang-gecontroleerde knoop wordt bepaald;
* Nochtans, beïnvloedt het noch siblings noch voorouders van de toegang-gecontroleerde knoop;
* De overerving van een bepaalde CUG houdt bij genestelde KUG tegen.

#### Aanbevolen procedures {#best-practices}

De volgende beste praktijken zouden voor het bepalen van beperkte gelezen toegang door CUGs met rekening moeten brengen:

* Bespreek bewust of uw behoefte aan een KUUG over het beperken van lees toegang of een authentificatievereiste is. Als het laatste, of als er behoefte aan allebei is, raadpleeg de sectie over Beste praktijken voor details betreffende het vereiste van de Authentificatie
* Creeer een bedreigingsmodel voor de gegevens of de inhoud die moeten worden beschermd om bedreigingsgrenzen te identificeren en een duidelijk beeld over de gevoeligheid van de gegevens en de rollen te krijgen verbonden aan erkende toegang
* Model de inhoud van de opslagplaats en CUGs die algemene toestemmingsgerelateerde aspecten en beste praktijken in mening houden:

   * Herinner dat de lees toestemming slechts wordt verleend als bepaalde CUG en de evaluatie van andere modules die in de opstellingssubsidie worden opgesteld een bepaalde onderwerp toestaan om een bepaald bewaarplaatspunt te lezen
   * Vermijd het creëren van overtollige KUGs waar de gelezen toegang reeds door andere vergunningsmodules wordt beperkt
   * Bij buitensporige behoefte aan geneste CUG&#39;s kunnen problemen in het inhoudsontwerp mogelijk worden gemarkeerd
   * De bovenmatige behoefte aan CUGs (bijvoorbeeld, op elke pagina) kan op de behoefte aan een model van de douanevergunning wijzen dat potentieel beter geschikt is om de specifieke veiligheidsbehoeften van de toepassing en de inhoud te passen.

* Beperk de paden die worden ondersteund voor CUG-beleid tot een paar bomen in de opslagplaats, zodat u de prestaties kunt optimaliseren. Bijvoorbeeld, sta slechts CUGs onder de /content knoop toe zoals verscheept als standaardwaarde sinds AEM 6.3.
* Het beleid van de CUG wordt ontworpen om gelezen toegang tot een kleine reeks principes te verlenen. De behoefte aan een enorm aantal principes kan kwesties in de inhoud of toepassingsontwerp benadrukken en zou moeten worden herzien.

### Verificatie: de auteitsvereisten definiëren {#authentication-defining-the-auth-requirement}

De authentificatie-verwante delen van de eigenschap van CUG laten u bomen merken die authentificatie vereisen en naar keuze een specifieke login pagina specificeren. Conform de vorige versie kunt u met de nieuwe implementatie structuren markeren die verificatie vereisen in de opslagplaats voor inhoud. Het maakt synchronisatie met de `Sling org.apache.sling.api.auth.Authenticator`verantwoordelijk voor uiteindelijk het handhaven van het vereiste en het opnieuw richten aan een login middel.

Deze vereisten worden geregistreerd met de Authenticator door de dienst OSGi die verstrekt `sling.auth.requirements` registration, eigenschap. Deze eigenschappen worden dan gebruikt om de authentificatievereisten dynamisch uit te breiden. Voor meer informatie raadpleegt u de [Verkoopdocumentatie](https://sling.apache.org/apidocs/sling7/org/apache/sling/auth/core/AuthConstants.html#AUTH_REQUIREMENTS).

#### De verificatievereiste definiëren met een specifiek mixertype {#defining-the-authentication-requirement-with-a-dedicated-mixin-type}

Om veiligheidsredenen vervangt de nieuwe implementatie het gebruik van een resterende JCR-eigenschap door een speciaal mixintype dat wordt aangeroepen `granite:AuthenticationRequired`, die één facultatieve bezit van type STRING voor de login weg bepaalt `granite:loginPath`. Alleen wijzigingen in de inhoud met betrekking tot dit type mix leiden tot een update van de vereisten die zijn geregistreerd bij Apache Sling Authenticator. De wijzigingen worden bijgehouden bij het aanhouden van eventuele tijdelijke wijzigingen en vereisen dus een `javax.jcr.Session.save()` oproep om effectief te worden.

Hetzelfde geldt voor de `granite:loginPath` eigenschap. Er wordt alleen aan voldaan als het wordt gedefinieerd door het aan de auteisen gerelateerde mengtype. Het toevoegen van een restbezit met deze zeer naam bij een ongestructureerde knoop JCR toont niet het gewenste effect en het bezit wordt genegeerd door de manager verantwoordelijk voor het bijwerken van de registratie OSGi.

>[!NOTE]
>
>Het instellen van de eigenschap voor het aanmeldingspad is optioneel en alleen nodig als de structuur waarvoor verificatie is vereist, niet kan terugvallen op de standaardaanmeldingspagina of een andere overgeërfde aanmeldingspagina. Zie de [Evaluatie van aanmeldingspad](/help/sites-administering/closed-user-groups.md#evaluation-of-login-path) hieronder.

#### Registreren van de Vereiste van de Authentificatie en Login Weg met de Verschuivende Authenticator {#registering-the-authentication-requirement-and-login-path-with-the-sling-authenticator}

Aangezien dit type van authentificatievereiste naar verwachting tot bepaalde looppaswijzen en tot een kleine ondergroep van bomen binnen de inhoudsbewaarplaats zal worden beperkt, is het volgen van het vereiste mixintype en de login wegeigenschappen voorwaardelijk. En, is het gebonden aan een overeenkomstige configuratie die de gesteunde wegen bepaalt (zie de Opties van de Configuratie hieronder). Daarom veroorzaken slechts veranderingen binnen het werkingsgebied van deze gesteunde wegen een update van de registratie OSGi, elders zowel het mixintype als het bezit worden genegeerd.

De standaard AEM opstelling maakt nu gebruik van deze configuratie door toe te staan om de mixin op de wijze van de auteurslooppas te plaatsen maar het slechts van kracht te hebben op replicatie aan te publiceren instantie. Zie [deze pagina](https://sling.apache.org/documentation/the-sling-engine/authentication/authenticationframework.html) voor details hoe Sling de authentificatievereiste afdwingt.

De `granite:AuthenticationRequired` mixintype binnen de gevormde gesteunde wegen veroorzaakt de registratie OSGi van de verantwoordelijke manager om worden bijgewerkt die een nieuwe, extra ingang met bevat `sling.auth.requirements` eigenschap. Als een bepaalde vereiste voor verificatie de optionele `granite:loginPath` eigenschap, wordt de waarde ook geregistreerd bij de authenticator met een &#39;-&#39; prefix dat van authentificatievereiste moet worden uitgesloten.

#### Evaluatie en overerving van de authenticatievereiste {#evaluation-and-inheritance-of-the-authentication-requirement}

De verificatievereisten voor Apache Sling worden overgenomen door de pagina- of knooppunthiërarchie. De details zelf van de erfenis en de evaluatie van de authentificatievereisten zoals orde en belangrijkheid worden beschouwd als implementatiedetails en zullen niet in dit artikel worden gedocumenteerd.

#### Evaluatie van aanmeldingspad {#evaluation-of-login-path}

De evaluatie van de login weg en redirect aan het overeenkomstige middel op authentificatie is een implementatiedetail van de Afhandeling van de Authentificatie van de Selecteur van de Aanmelden van de Adobe Granite ( `com.day.cq.auth.impl.LoginSelectorHandler`), wat een Apache Sling AuthenticationHandler is die standaard met AEM is geconfigureerd.

Bij aanroepen `AuthenticationHandler.requestCredentials` deze manager probeert om de kaartlogin pagina te bepalen waaraan de gebruiker wordt opnieuw gericht. Dit omvat de volgende stappen:

* Onderscheid tussen verlopen wachtwoord en behoefte aan regelmatige login als reden voor omleiding;
* Als u zich regelmatig aanmeldt, wordt getest of een aanmeldingspad in de volgende volgorde kan worden verkregen:

   * vanuit de LoginPathProvider, zoals geïmplementeerd door de nieuwe `com.adobe.granite.auth.requirement.impl.RequirementService`,
   * van de oude, afgekeurde implementatie van de GOS,
   * in de toewijzingen van aanmeldingspagina&#39;s, zoals gedefinieerd met de `LoginSelectorHandler`,
   * en ten slotte, vallen terug naar de StandaardAanmeldingspagina, zoals bepaald met `LoginSelectorHandler`.

* Wanneer een geldig login weg door de hierboven vermelde vraag werd verkregen, wordt het verzoek van de gebruiker opnieuw gericht aan die pagina.

Het doel van deze documentatie is de evaluatie van het aanmeldingspad zoals dit door de interne `LoginPathProvider` interface. De implementatie die sinds AEM 6.3 wordt verzonden, functioneert als volgt:

* Registratie van aanmeldingspaden is afhankelijk van het onderscheid tussen verlopen wachtwoord en de behoefte aan regelmatige aanmelding als reden voor omleiding
* Als u zich regelmatig aanmeldt, wordt getest of een aanmeldingspad in de volgende volgorde kan worden verkregen:

   * van de `LoginPathProvider` zoals geïmplementeerd door de nieuwe `com.adobe.granite.auth.requirement.impl.RequirementService`,
   * van de oude, afgekeurde implementatie van de GOS,
   * in de toewijzingen van aanmeldingspagina&#39;s, zoals gedefinieerd met de `LoginSelectorHandler`,
   * en ten slotte terugvallen naar de standaardaanmeldingspagina zoals gedefinieerd met de `LoginSelectorHandler`.

* Wanneer een geldig login weg door de hierboven vermelde vraag werd verkregen, wordt het verzoek van de gebruiker opnieuw gericht aan die pagina.

De `LoginPathProvider` zoals geïmplementeerd door de nieuwe ondersteuning voor auteisen in Granite stelt aanmeldingspaden beschikbaar zoals gedefinieerd door de `granite:loginPath` eigenschappen, die op hun beurt worden gedefinieerd door het hierboven beschreven mixintype. De afbeelding van de middelweg die de login weg en de bezitswaarde zelf houdt wordt gehouden in geheugen en geëvalueerd om een geschikte login weg voor andere knopen in de hiërarchie te vinden.

>[!NOTE]
>
>De evaluatie wordt slechts uitgevoerd voor verzoeken verbonden aan middelen die met in de gevormde gesteunde wegen worden gevestigd. Voor andere verzoeken zullen de alternatieve manieren om de login weg te bepalen worden geëvalueerd.

#### Aanbevolen procedures {#best-practices-1}

Bij het bepalen van de verificatievereisten moet rekening worden gehouden met de volgende beste praktijken:

* Vermijd het nesten authentificatievereisten: het plaatsen van één enkele auth-required teller aan het begin van een boom zou voldoende moeten zijn en aan de volledige subtree worden geërft die door de doelknoop wordt bepaald. Aanvullende verificatievereisten binnen die structuur moeten als overbodig worden beschouwd en kunnen leiden tot prestatieproblemen bij de evaluatie van de verificatievereisten binnen Apache Sling. Met de scheiding van vergunning en authentificatie-verwante gebieden van de GIDS, is het mogelijk om gelezen toegang door GG of andere soorten beleid te beperken terwijl het handhaven van authentificatie voor de volledige boom.
* Inhoud van een modelopslagplaats zodanig dat de verificatievereisten van toepassing zijn op de gehele boomstructuur zonder dat geneste substructuren opnieuw van de vereiste hoeven te worden uitgesloten.
* U voorkomt dat u redundante aanmeldingspaden opgeeft en vervolgens registreert:

   * vertrouwen op overerving en vermijd het definiëren van geneste aanmeldingspaden;
   * het optionele aanmeldingspad niet instellen op een waarde die overeenkomt met de standaardwaarde of een overgeërfde waarde,
   * de toepassingsontwikkelaars zouden moeten identificeren welke login wegen in globale login-weg configuraties (zowel gebrek als afbeeldingen) verbonden aan zouden moeten worden gevormd `LoginSelectorHandler`.

## Vertegenwoordiging in de opslagplaats {#representation-in-the-repository}

### Beleidsvertegenwoordiging CUG in de opslagplaats {#cug-policy-representation-in-the-repository}

De documentatie van het Eak behandelt hoe het nieuwe beleid van CUG in de bewaarplaats inhoud wordt weerspiegeld. Raadpleeg voor meer informatie [deze pagina](https://jackrabbit.apache.org/oak/docs/security/authorization/cug.html#Representation_in_the_Repository).

### Verificatievereiste in de opslagplaats {#authentication-requirement-in-the-repository}

De behoefte aan een afzonderlijk authentificatievereiste wordt weerspiegeld in de inhoud van de bewaarplaats met een specifiek mixinknooptype dat bij de doelknoop wordt geplaatst. Het mixintype bepaalt een facultatieve bezit om een specifieke login pagina voor de boom te specificeren die door de doelknoop wordt bepaald.

De pagina die aan het aanmeldingspad is gekoppeld, kan zich binnen of buiten die structuur bevinden. Het is uitgesloten van de authenticatieverplichting.

```java
[granite:AuthenticationRequired]
      mixin
      - granite:loginPath (STRING)
```

## Het beheren van het Beleid van de CUG en de Vereiste van de Authentificatie {#managing-cug-policies-and-authentication-requirement}

### CUG-beleid beheren {#managing-cug-policies}

Het nieuwe type toegangsbeheerbeleid om gelezen toegang voor een KUG te beperken wordt beheerd gebruikend JCR toegangsbeheer API en volgt de mechanismen die met worden beschreven [JCR 2.0-specificatie](https://developer.adobe.com/experience-manager/reference-materials/spec/jcr/2.0/16_Access_Control_Management.html).

#### Een nieuw CUG-beleid instellen {#set-a-new-cug-policy}

Code om een nieuw beleid van de GECG op een knoop toe te passen die geen KUG eerder plaatste. Let op: `getApplicablePolicies` retourneert alleen nieuw beleid dat nog niet eerder is ingesteld. Uiteindelijk moet het beleid worden teruggeschreven en moeten de veranderingen worden voortgezet.

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
   log.debug("no applicable policy"); // path not supported or no applicable policy (for example,
                                                   // the policy was set before)
   return;
}

cugPolicy.addPrincipals(toAdd1, toAdd2);
cugPolicy.removePrincipals(toRemove));

acMgr.setPolicy(path, cugPolicy); // as of this step the policy can be edited/removed
session.save();
```

#### Een bestaand CUG-beleid bewerken {#edit-an-existing-cug-policy}

De volgende stappen zijn nodig om een bestaand beleid van CUG uit te geven. Het gewijzigde beleid moet worden teruggeschreven en de veranderingen moeten blijven gebruiken `javax.jcr.Session.save()`.

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

Het beheer van het toegangsbeheer JCR bepaalt een best-inspanningsmethode om het beleid terug te winnen dat op een bepaalde weg van kracht wordt. Omdat de evaluatie van het beleid van de KUG voorwaardelijk is en van de overeenkomstige configuratie afhangt om worden toegelaten, roepend `getEffectivePolicies` Dit is een handige manier om te controleren of een bepaald CUG-beleid in een bepaalde installatie van kracht wordt.

>[!NOTE]
>
>Het verschil tussen `getEffectivePolicies` en het verdere codevoorbeeld dat omhoog de hiërarchie loopt om te vinden of maakt een bepaalde weg reeds deel uit van een bestaande KUG.

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

#### Overerfd CUG-beleid ophalen {#retrieve-inherited-cug-policies}

Alle geneste CUG&#39;s zoeken die op een bepaald pad zijn gedefinieerd, ongeacht of ze van kracht worden of niet. Zie de klasse [Configuratieopties](/help/sites-administering/closed-user-groups.md#configuration-options) sectie.

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

#### Het Beleid van de KUG door Hoofd beheren {#managing-cug-policies-by-pincipal}

De extensies die worden gedefinieerd door `JackrabbitAccessControlManager` die toestaan om toegangsbeheerbeleid door hoofd uit te geven wordt niet uitgevoerd met het beheer van de toegangscontrole van de CUG, aangezien een beleid van de KUG altijd alle hoofden beïnvloedt: die vermeld met het `PrincipalSetPolicy` worden verleend lees toegang terwijl alle andere hoofden worden verhinderd om inhoud in de boom te lezen die door de doelknoop wordt bepaald.

De bijbehorende methoden retourneren altijd een lege beleidsarray, maar genereren geen uitzonderingen.

### De verificatievereiste beheren {#managing-the-authentication-requirement}

Het creëren, de wijziging, of de verwijdering van een nieuw authentificatievereiste wordt bereikt door het efficiënte knooptype van de doelknoop te veranderen. De eigenschap voor het optionele aanmeldingspad kan vervolgens worden geschreven met de gewone JCR API.

>[!NOTE]
>
>De wijzigingen in een opgegeven doelknooppunt hierboven worden alleen weerspiegeld in de Apache Sling Authenticator als de `RequirementHandler` is gevormd en het doel is bevat in de bomen die door de gesteunde wegen worden bepaald (zie de Opties van de SectieConfiguratie).
>
>Zie voor meer informatie [Mixinknooppunttypen toewijzen](https://docs.adobe.com/docs/en/spec/jcr/2.0/10_Writing.html#10.10.3) en [Nodes toevoegen en eigenschappen instellen](https://docs.adobe.com/docs/en/spec/jcr/2.0/10_Writing.html#10.4) Nodes toevoegen en eigenschappen instellen

#### Nieuwe auteisen toevoegen {#adding-a-new-auth-requirement}

De stappen om een authentificatievereiste tot stand te brengen zijn hieronder gedetailleerd. De vereiste wordt alleen geregistreerd bij de Apache Sling Authenticator als de `RequirementHandler` is gevormd voor de boom die de doelknoop bevatten.

```java
Node targetNode = [...]

targetNode.addMixin("granite:AuthenticationRequired");
session.save();
```

#### Voeg een Nieuwe Vereiste van de Auth met Login Weg toe {#add-a-new-auth-requirement-with-login-path}

Stappen om een authentificatievereiste met inbegrip van een login weg tot stand te brengen. Het vereiste en de uitsluiting voor het aanmeldingspad zijn alleen geregistreerd bij de Apache Sling Authenticator als de `RequirementHandler` is gevormd voor de boom die de doelknoop bevatten.

```java
Node targetNode = [...]
String loginPath = [...] // STRING property

Node targetNode = session.getNode(path);
targetNode.addMixin("granite:AuthenticationRequired");

targetNode.setProperty("granite:loginPath", loginPath);
session.save();
```

#### Een bestaand aanmeldingspad wijzigen {#modify-an-existing-login-path}

De stappen om een bestaand login weg te veranderen zijn hieronder gedetailleerd. De wijziging wordt alleen geregistreerd bij de Apache Sling Authenticator als de `RequirementHandler` is gevormd voor de boom die de doelknoop bevatten. De vorige waarde van het aanmeldingspad wordt uit de registratie verwijderd. Deze wijziging heeft geen invloed op de vereiste auth die aan het doelknooppunt is gekoppeld.

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

Stappen om een bestaand aanmeldingspad te verwijderen. De invoer van het aanmeldingspad wordt alleen niet geregistreerd bij de Apache Sling Authenticator als de `RequirementHandler` is gevormd voor de boom die de doelknoop bevatten. De auth-vereiste die aan het doelknooppunt is gekoppeld, wordt niet beïnvloed.

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

#### Een Auth-vereiste verwijderen {#remove-an-auth-requirement}

Stappen om een bestaand authentificatievereiste te verwijderen. De vereiste wordt alleen niet geregistreerd bij de Apache Sling Authenticator als de `RequirementHandler` is gevormd voor de boom die de doelknoop bevatten.

```java
Node targetNode = [...]
targetNode.removeMixin("granite:AuthenticationRequired");

session.save();
```

#### Effectieve Auth Requirements ophalen {#retrieve-effective-auth-requirements}

Er is geen speciale openbare API om alle effectieve verificatievereisten te lezen zoals die zijn geregistreerd bij de Apache Sling Authenticator. Nochtans, wordt de lijst blootgesteld in de systeemconsole bij `https://<serveraddress>:<serverport>/system/console/slingauth` onder &quot;**Configuratie van verificatievereisten**&quot;.

In de volgende afbeelding ziet u de verificatievereisten van een AEM-publicatie-instantie met demo-inhoud. Het gemarkeerde pad van de communitypagina toont hoe een vereiste die wordt toegevoegd door de implementatie die in dit document wordt beschreven, wordt weerspiegeld in de Apache Sling Authenticator.

>[!NOTE]
>
>In dit voorbeeld is de eigenschap voor het optionele aanmeldingspad niet ingesteld. Daarom is er geen tweede vermelding geregistreerd bij de authenticator.

![chlimage_1-24](assets/chlimage_1-24.jpeg)

#### Het effectieve aanmeldingspad ophalen {#retrieve-the-effective-login-path}

Er is momenteel geen openbare API om de login weg terug te winnen die bij anoniem het toegang tot van een middel van kracht wordt dat authentificatie vereist. Zie sectieEvaluatie van Login Weg voor implementatiedetails op hoe de login weg wordt teruggewonnen.

Naast de aanmeldingspaden die met deze functie zijn gedefinieerd, zijn er echter andere manieren om het omleiden naar de aanmelding op te geven. Hiermee moet rekening worden gehouden bij het ontwerpen van het inhoudsmodel en de verificatievereisten van een bepaalde AEM.

#### De overerfde Auth-vereiste ophalen {#retrieve-the-inherited-auth-requirement}

Net als bij het aanmeldingspad is er geen openbare API om de overgenomen verificatievereisten op te halen die in de inhoud zijn gedefinieerd. Het volgende voorbeeld laat zien hoe u alle verificatievereisten kunt weergeven die zijn gedefinieerd met een bepaalde hiërarchie, ongeacht of deze van kracht worden of niet. Zie voor meer informatie [Configuratieopties](/help/sites-administering/closed-user-groups.md#configuration-options).

>[!NOTE]
>
>Men adviseert om zich op het overervingsmechanisme zowel voor authentificatievereisten als login weg te baseren en verwezenlijking van genestelde auteisen te vermijden.
>
>Zie voor meer informatie [Evaluatie en overerving van de authenticatievereiste](#evaluation-and-inheritance-of-the-authentication-requirement), [Evaluatie van aanmeldingspad](#evaluation-of-login-path) en [Aanbevolen procedures](#best-practices).

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

### Het combineren van het Beleid van de KUG en de Vereisten van de Authentificatie {#combining-cug-policies-and-the-authentication-requirement}

De volgende lijst maakt een lijst van de geldige combinaties beleid van de CUG en het authentificatievereiste in een AEM instantie die beide modules heeft die door configuratie worden toegelaten.

| **Verificatie vereist** | **Aanmeldingspad** | **Beperkte leestoegang** | **Verwacht effect** |
|---|---|---|---|
| Ja | Ja | Ja | Een bepaalde gebruiker zal slechts de subtree kunnen bekijken duidelijk met het beleid van de GECG als de efficiënte toestemmingsevaluatie toegang verleent. Een niet-geverifieerde gebruiker wordt omgeleid naar de opgegeven aanmeldingspagina. |
| Ja | Nee | Ja | Een bepaalde gebruiker zal slechts de subtree kunnen bekijken duidelijk met het beleid van de GECG als de efficiënte toestemmingsevaluatie toegang verleent. Een niet-geverifieerde gebruiker wordt omgeleid naar een overgenomen standaardaanmeldingspagina. |
| Ja | Ja | Nee | Een niet-geverifieerde gebruiker wordt omgeleid naar de opgegeven aanmeldingspagina. Of het wordt toegestaan om de boom te bekijken duidelijk met auth-required hangt van de efficiënte toestemmingen van de individuele punten in die subtree af. Geen specifieke CUG die de leestoegang beperkt. |
| Ja | Nee | Nee | Een niet-geverifieerde gebruiker wordt omgeleid naar een overgenomen standaardaanmeldingspagina. Of het wordt toegestaan om de boom te bekijken duidelijk met de auteigenschap hangt van de efficiënte toestemmingen van de individuele punten in die subtree af. Geen specifieke CUG die de leestoegang beperkt. |
| Nee | Nee | Ja | Een bepaalde voor authentiek verklaarde of niet voor authentiek verklaarde gebruiker kan de subtree slechts bekijken duidelijk met het beleid van de GIDS als de efficiënte toestemmingsevaluatie toegang verleent. Een niet-geverifieerde gebruiker wordt gelijk behandeld en wordt niet omgeleid naar aanmelding. |

>[!NOTE]
>
>De combinatie van &#39;Vereisten voor verificatie&#39; = Nee en &#39;Aanmeldingspad&#39; = Ja wordt hierboven niet vermeld omdat het &#39;Aanmeldingspad&#39; een optioneel kenmerk is dat is gekoppeld aan een Auth-Requirement. Het opgeven van een JCR-eigenschap met die naam zonder het definiërende mixintype toe te voegen, heeft geen effect en wordt genegeerd door de corresponderende handler.

## OSGi-componenten en -configuratie {#osgi-components-and-configuration}

Deze sectie verstrekt een overzicht aan de componenten OSGi en de individuele configuratieopties die met de nieuwe implementatie van de KUG worden geïntroduceerd.

Zie ook de CUG-afbeelding documentatie voor een uitvoerige afbeelding van de configuratieopties tussen oude en nieuwe implementatie.

### Autorisatie: Instellen en configureren {#authorization-setup-and-configuration}

De nieuwe, vergunningsgerelateerde onderdelen zijn opgenomen in de **Oak CUG Authorization** bundel ( `org.apache.jackrabbit.oak-authorization-cug`), dat onderdeel is van de AEM standaardinstallatie. De bundel bepaalt een gescheiden vergunningsmodel dat wordt opgesteld als extra manier om gelezen toegang te beheren.

#### CUG-autorisatie instellen {#setting-up-cug-authorization}

De CUG-autorisatie instellen wordt in het gedeelte [relevante Apache-documentatie](https://jackrabbit.apache.org/oak/docs/security/authorization/cug.html#pluggability). Door gebrek, AEM heeft de vergunning van de GECG die in alle looppaswijzen wordt opgesteld. De stapsgewijze instructies kunnen ook worden gebruikt om de vergunning van het KUG in die installaties onbruikbaar te maken die een verschillende vergunningsopstelling vereisen.

#### Filter Referrer configureren {#configuring-the-referrer-filter}

U moet ook de [Filter Verschuivingsverwijzing](/help/sites-administering/security-checklist.md#the-sling-referrer-filter) met alle hostnames die kunnen worden gebruikt om toegang te krijgen tot AEM, bijvoorbeeld via CDN, Load Balancer en andere.

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
   <td>Laat u hoofden met de gevormde namen van de evaluatie van de KUG uitsluiten.</td>
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

* `cugSupportedPaths`: geef de substructuren op die CUG&#39;s kunnen bevatten. Geen standaardwaarde ingesteld
* `cugEnabled`: configuratieoptie om toestemmingsevaluatie voor het huidige beleid van CUG toe te laten.

De beschikbare configuratieopties verbonden aan de CUG-vergunningsmodule zijn vermeld en meer gedetailleerd beschreven bij [Documentatie voor Apache Oak](https://jackrabbit.apache.org/oak/docs/security/authorization/cug.html#configuration).

#### Exclusief de hoofden van de CUG-evaluatie {#excluding-principals-from-cug-evaluation}

Van de vorige uitvoering zijn individuele beginselen van de CUG-evaluatie vrijgesteld. De nieuwe vergunning van de GECG behandelt dit met een specifieke interface genoemd CugExclude. Apache Jackrabbit Oak 1.4 wordt geleverd met een standaardimplementatie die een vaste reeks principes en een uitgebreide implementatie uitsluit waarmee u afzonderlijke hoofdnamen kunt configureren. De laatste is geconfigureerd in AEM publicatieinstanties.

Het gebrek sinds AEM 6.3 verhindert de volgende hoofden door beleid van de GN worden beïnvloed:

* beheerprincipes (beheerder, beheerdersgroep)
* servicegebruikersprincipes
* interne systeemprincipal in opslagplaats

Zie de tabel in het dialoogvenster [Standaardconfiguratie sinds AEM 6.3](#default-configuration-since-aem) hieronder.

De uitsluiting van de groep &#39;beheerders&#39; kan worden gewijzigd of uitgebreid in de systeemconsole in de configuratiesectie van **Apache Jackrabbit Oak CUG Exclusive List**.

Alternatief, is het mogelijk om een douaneimplementatie van de interface te verstrekken en op te stellen CugExclude om de reeks uitgesloten hoofden aan te passen als er speciale behoeften zijn. Zie de documentatie op [CUG-pluggable](https://jackrabbit.apache.org/oak/docs/security/authorization/cug.html#pluggability) voor details en een voorbeeldimplementatie.

### Verificatie: Instellen en configureren {#authentication-setup-and-configuration}

De nieuwe, aan authenticatie gerelateerde onderdelen zijn opgenomen in de **Adobe graniet-verificatiehandler** bundel ( `com.adobe.granite.auth.authhandler` versie 5.6.4). Deze bundel maakt deel uit van de AEM standaardinstallatie.

Om de vervanging van het authentificatievereiste voor de verouderde steun van de CUG te plaatsen, moeten sommige componenten OSGi aanwezig en actief in een bepaalde AEM installatie zijn. Zie voor meer informatie **Kenmerken van OSGi-componenten** hieronder.

>[!NOTE]
>
>Wegens de verplichte configuratieoptie met RequirementHandler, zullen de op authentificatie betrekking hebbende delen slechts actief zijn als de eigenschap door een reeks gesteunde wegen te specificeren is toegelaten. Bij een standaard AEM installatie is de functie uitgeschakeld in de modus voor het uitvoeren van de auteur en ingeschakeld voor /content in de modus voor publiceren.

**Kenmerken van OSGi-componenten**

De volgende twee componenten OSGi zijn geïntroduceerd om authentificatievereisten te bepalen en specifieke login wegen te specificeren:

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
   <td>Speciale OSGi-service voor verificatievereisten die een waarnemer registreert voor wijzigingen in inhoud die van invloed zijn op de auteisen (via de <code>granite:AuthenticationRequirement</code> mixingtype) en aanmeldingspaden met worden blootgesteld aan de <code>LoginSelectorHandler</code>. </td>
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

| Label | Vereiste van de Authentificatie van Granite van de Adobe en de Bediener van de Weg van de Login |
|---|---|
| Beschrijving | `RequirementHandler` implementatie die de vereisten voor Apache Sling-verificatie en de bijbehorende uitsluiting voor de bijbehorende aanmeldingspaden bijwerkt. |
| Configuratieeigenschappen | `supportedPaths` |
| Configuratiebeleid | `ConfigurationPolicy.REQUIRE` |
| Verwijzingen | NA |

#### Configuratieopties {#configuration-options-1}

De authentificatie-verwante delen van CUG herschrijven slechts met één enkele configuratieoptie verbonden aan de Vereiste van de Authentificatie van de Adobe Granite en de Bediener van de Weg van de Login:

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
   <td>Set&lt;string&gt;</td>
   <td>-</td>
   <td>Paden waaronder de authentificatievereisten door deze manager zullen worden geëerbiedigd. Laat deze configuratie ongedaan als u de <code>granite:AuthenticationRequirement</code> mixin type aan knopen zonder hen (bijvoorbeeld, op auteursinstanties) te hebben afgedwongen. Als deze optie ontbreekt, wordt de functie uitgeschakeld. </td>
  </tr>
 </tbody>
</table>

## Standaardconfiguratie sinds AEM 6.3 {#default-configuration-since-aem}

De nieuwe installaties van AEM zullen door gebrek de nieuwe implementaties zowel voor de vergunning als op authentificatie betrekking hebbende delen van de eigenschap van CUG gebruiken. De oude implementatie &quot;Adobe granite Closed User Group (CUG) Support&quot; is vervangen en wordt standaard uitgeschakeld in alle AEM installaties. De nieuwe implementaties zullen in plaats daarvan als volgt worden toegelaten:

### Auteursinstanties {#author-instances}

| **&quot;Apache Jackrabbit Oak CUG Configuration&quot;** | **Toelichting** |
|---|---|
| Ondersteunde paden `/content` | Toegangsbeheer voor CUGpolicies is ingeschakeld. |
| FALSE CUG-evaluatie ingeschakeld | Evaluatie van machtigingen is uitgeschakeld. CUG-beleid heeft geen effect. |
| Rangschikking | 200 | Zie documentatie van eikel. |

>[!NOTE]
>
>Geen configuratie voor **Apache Jackrabbit Oak CUG Exclusive List** en **Vereiste van de Authentificatie van Granite van de Adobe en de Bediener van de Weg van de Login** is aanwezig op standaardontwerpinstanties.

### Exemplaren publiceren {#publish-instances}

| **&quot;Apache Jackrabbit Oak CUG Configuration&quot;** | **Toelichting** |
|---|---|
| Ondersteunde paden `/content` | Toegangsbeheer voor CUG-beleid wordt ingeschakeld onder de geconfigureerde paden. |
| WAAR VOOR CUG-evaluatie ingeschakeld | De evaluatie van de toestemming wordt toegelaten onder de gevormde wegen. CUG-beleid wordt van kracht op `Session.save()`. |
| Rangschikking | 200 | Zie documentatie van eikel. |

| **&quot;Apache Jackrabbit Oak CUG Exclusive List&quot;** | **Toelichting** |
|---|---|
| Hoofdnaambeheerders | Sluit beheerders hoofd van de evaluatie van de KUG uit. |

| **&quot;Vereiste van de Authentificatie van Granite van de Adobe en de Bediener van de Weg van de Login&quot;** | **Toelichting** |
|---|---|
| Ondersteunde paden  `/content` | Verificatievereisten zoals gedefinieerd in de gegevensopslagruimte door de `granite:AuthenticationRequired` mixtype wordt hieronder van kracht `/content` op `Session.save()`. Verschuivende verificator wordt bijgewerkt. Het toevoegen van het mixintype buiten de ondersteunde paden wordt genegeerd. |

## Het onbruikbaar maken van de Vereiste van de Authorificatie en van de Authentificatie van de CUG {#disabling-cug-authorization-and-authentication-requirement}

De nieuwe implementatie kan volledig worden uitgeschakeld als een bepaalde installatie geen gebruik maakt van CUG&#39;s of andere middelen gebruikt voor verificatie en autorisatie.

### CUG-autorisatie uitschakelen {#disable-cug-authorization}

Raadpleeg de [CUG-pluggable](https://jackrabbit.apache.org/oak/docs/security/authorization/cug.html#pluggability) documentatie voor details over hoe te om het de vergunningsmodel van de GIDS van de samengestelde vergunningsopstelling te verwijderen.

### De verificatievereiste uitschakelen {#disable-the-authentication-requirement}

Om steun voor het authentificatievereiste zoals voorzien door onbruikbaar te maken `granite.auth.authhandler` het volstaat om de configuratie te verwijderen die is gekoppeld aan **Vereiste van de Authentificatie van Granite van de Adobe en de Bediener van de Weg van de Login**.

>[!NOTE]
>
>Houd er echter rekening mee dat als u de configuratie verwijdert, het mixintype niet wordt verwijderd. Dit type was nog steeds van toepassing op knooppunten zonder dat dit van kracht wordt.

## Interactie met andere modules {#interaction-with-other-modules}

### Apache Jackrabbit API {#apache-jackrabbit-api}

Om op het nieuwe type van toegangsbeheerbeleid te wijzen dat door het de vergunningsmodel van de CUG wordt gebruikt, is API die door Apache Jackrabbit wordt bepaald uitgebreid. Sinds versie 2.11.0 van het `jackrabbit-api` module bepaalt een nieuwe geroepen interface `org.apache.jackrabbit.api.security.authorization.PrincipalSetPolicy`, die zich uitstrekt van `javax.jcr.security.AccessControlPolicy`.

### Apache Jackrabbit FileVault {#apache-jackrabbit-filevault}

Het importmechanisme van Apache Jackrabbit FileVault is aangepast aan het type toegangsbeheerbeleid `PrincipalSetPolicy`.

### Apache Sling Content Distribution {#apache-sling-content-distribution}

Zie het bovenstaande [Apache Jackrabbit FileVault](/help/sites-administering/closed-user-groups.md#apache-jackrabbit-filevault) sectie.

### Graniet-replicatie van Adobe {#adobe-granite-replication}

De replicatiemodule is lichtjes aangepast om het beleid van de CUG tussen verschillende AEM instanties te kunnen herhalen:

* `DurboImportConfiguration.isImportAcl()` wordt letterlijk geïnterpreteerd en heeft alleen invloed op de uitvoering van het toegangsbeheerbeleid `javax.jcr.security.AccessControlList`

* `DurboImportTransformer` zal slechts deze configuratie voor ware ACLs respecteren
* Overige beleidsvormen zoals `org.apache.jackrabbit.api.security.authorization.PrincipalSetPolicy` instanties die door het de vergunningsmodel van de KUG worden gecreeerd zullen altijd worden herhaald en de configuratieoptie `DurboImportConfiguration.isImportAcl`() wordt genegeerd.

Er is één beperking van het repliceren van beleid van CUG. Als een bepaald beleid van de KUG wordt verwijderd zonder het overeenkomstige mixinknooppunttype te verwijderen `rep:CugMixin,` de verwijdering zal niet op replicatie worden weerspiegeld. Dit probleem is opgelost door de mix bij het verwijderen van het beleid altijd te verwijderen. De beperking kan desondanks opduiken als het mixintype handmatig wordt toegevoegd.

### Adobe graniet-verificatiehandler {#adobe-granite-authentication-handler}

De verificatiehandler **Adobe Granite HTTP Header Authentication Handler** meegeleverd bij `com.adobe.granite.auth.authhandler` bundel bevat een verwijzing naar de `CugSupport` interface die door de zelfde module wordt bepaald. Het wordt gebruikt om het &quot;domein&quot;in bepaalde omstandigheden te berekenen, die terug naar het domein vallen dat met de manager wordt gevormd.

Dit is aangepast om de verwijzing naar `CugSupport` optioneel om maximale achterwaartse compatibiliteit te garanderen als een bepaalde instelling besluit de vervangen implementatie opnieuw in te schakelen. Installaties die gebruikmaken van de implementatie krijgen niet langer het domein dat wordt opgehaald uit de CUG-implementatie, maar geven altijd het domein weer zoals gedefinieerd met **Adobe Granite HTTP Header Authentication Handler**.

>[!NOTE]
>
>Standaard worden de **Adobe Granite HTTP Header Authentication Handler** is alleen geconfigureerd in de publicatieuitvoeringsmodus met de optie Aanmeldingspagina uitschakelen ( `auth.http.nologin`) ingeschakeld.

### AEM LiveCopy {#aem-livecopy}

Het configureren van CUG&#39;s met LiveCopy wordt in de opslagplaats vertegenwoordigd door toevoeging van één extra knooppunt en één extra eigenschap, en wel als volgt:

* `/content/we-retail/us/en/blueprint/rep:cugPolicy`
* `/content/we-retail/us/en/LiveCopy@granite:loginPath`

Beide elementen worden gemaakt onder de `cq:Page`. Met het huidige ontwerp, behandelt MSM slechts knopen en eigenschappen die onder zijn `cq:PageContent` (`jcr:content`) node.

CUG-groepen kunnen daarom niet worden geïmplementeerd in Actieve kopieën van blauwdrukken. Plan dit rond wanneer het vormen van Levend Exemplaar.

## Wijzigingen aanbrengen in de nieuwe CUG-implementatie {#changes-with-the-new-cug-implementation}

Het doel van deze sectie is een overzicht te geven van de wijzigingen die in de CUG-functie zijn aangebracht en een vergelijking te maken tussen de oude en de nieuwe implementatie. Het maakt een lijst van de veranderingen die van invloed zijn op de manier de steun van CUG wordt gevormd en beschrijft hoe en door wie CUGs in de bewaarplaats inhoud wordt beheerd.

### Verschillen in de Opstelling en de Configuratie van de CUG {#differences-in-cug-setup-and-configuration}

De vervangen OSGi-component **Ondersteuning voor gebruikersgroep voor gesloten gebruikersgroep (CUG) met Adobe** ( `com.day.cq.auth.impl.cug.CugSupportImpl`) is vervangen door nieuwe componenten die op autorisatie en authenticatie betrekking hebbende delen van de vroegere CUG-functionaliteit afzonderlijk kunnen verwerken.

## Verschillen in het beheren van CUG&#39;s in de inhoud van de opslagplaats {#differences-in-managing-cugs-in-the-repository-content}

In de volgende secties worden de verschillen tussen de oude en de nieuwe implementaties vanuit het perspectief van implementatie en veiligheid beschreven. Terwijl de nieuwe implementatie de zelfde functionaliteit probeert te verstrekken, zijn er subtiele veranderingen die belangrijk zijn om te weten wanneer het gebruiken van nieuwe CUG.

### Verschillen ten aanzien van vergunningen {#differences-with-regards-to-authorization}

De belangrijkste verschillen vanuit het oogpunt van vergunningverlening zijn samengevat in de onderstaande lijst:

**Specifieke inhoud van het Toegangsbeheer voor CUGs**

In de oude implementatie werd het model van de standaardvergunning gebruikt om het beleid van de toegangsbeheerlijst te manipuleren bij publiceren, die om het even welke bestaande ACEs door de opstelling vervangen die door CUG wordt gemachtigd. Dit werd geactiveerd door het schrijven van reguliere, resterende JCR-eigenschappen die tijdens de publicatie werden geïnterpreteerd.

Met de nieuwe implementatie wordt de opstelling van het toegangsbeheer van het standaard vergunningsmodel niet beïnvloed door enige KUG die, wordt gecreeerd gewijzigd of wordt verwijderd. In plaats daarvan wordt een nieuw type beleid aangeroepen `PrincipalSetPolicy` wordt toegepast als extra inhoud van het toegangsbeheer aan de doelknoop. Dit extra beleid wordt gevestigd als kind van de doelknoop en zou een sibling van de standaardbeleidsknoop zijn indien aanwezig.

**CUG-beleid bewerken in Access Control Management**

Deze beweging van resterende eigenschappen JCR aan een specifiek toegangsbeheerbeleid heeft een invloed op de toestemming nodig om het vergunningsdeel van de eigenschap van de GG tot stand te brengen of te wijzigen. Aangezien dit als een wijziging van de inhoud van de toegangscontrole wordt beschouwd, vereist het `jcr:readAccessControl` en `jcr:modifyAccessControl` rechten die naar de opslagplaats moeten worden geschreven. Daarom kunnen alleen inhoudsauteurs die gemachtigd zijn om de inhoud van het toegangsbeheer van een pagina te wijzigen, deze inhoud instellen of wijzigen. Dit staat in schril contrast met de oude implementatie waar de capaciteit om regelmatige eigenschappen te schrijven JCR voldoende was, resulterend in een voorrechtescalatie.

**Doelknooppunt gedefinieerd door beleid**

Creeer het beleid van de GECG bij de knoop JCR die de subboom bepaalt aan beperkte lees toegang te worden onderworpen. Dit is waarschijnlijk een AEM pagina als de CUG naar verwachting de gehele boom beïnvloedt.

Door het CUG-beleid alleen op het knooppunt jcr:content onder een bepaalde pagina te plaatsen, beperkt u alleen de toegang tot de inhoud s.str van een bepaalde pagina, maar dit heeft geen invloed op broers en zussen of onderliggende pagina&#39;s. Dit kan een geldig gebruiksgeval zijn en het is mogelijk om met een bewaargegevensopslagredacteur te bereiken die u fijne korrelige toegangsinhoud laat toepassen. Nochtans, contrasteert het de vroegere implementatie waar het plaatsen van een cq:cugEnabled bezit op jcr:content knoop intern aan de paginaknooppunt werd opnieuw in kaart gebracht. Deze toewijzing wordt niet meer uitgevoerd.

**Evaluatie van machtigingen met CUG-beleid**

De beweging van de oude steun van de GIDS aan een extra vergunningsmodel, verandert de manier efficiënte gelezen toestemmingen worden geëvalueerd. Zoals beschreven in het [Jackrabbit-documentatie](https://jackrabbit.apache.org/oak/docs/security/authorization/composite.html), een bepaalde aangever die de `CUGcontent` alleen leestoegang wordt verleend als de machtigingsevaluatie van alle modellen die in de Oak-opslagplaats zijn geconfigureerd leestoegang verleent.

Met andere woorden, voor de evaluatie van de effectieve machtigingen `CUGPolicy` en de standaardingangen van het toegangsbeheer worden in aanmerking genomen en de gelezen toegang op de inhoud van de GIDS wordt slechts verleend als het door beide soorten beleid wordt verleend. In een standaard AEM publiceer installatie waar gelezen toegang tot het volledige `/content` De boom wordt verleend voor iedereen, is het effect van het beleid van de CUG het zelfde als met de oude implementatie.

**Evaluatie op aanvraag**

Met het machtigingsmodel CUG kunt u het beheer en de evaluatie van toegangsbeheer afzonderlijk inschakelen:

* toegangsbeheerbeheer wordt toegelaten als de module één of vele gesteunde wegen heeft waar de KUGs kan worden gecreeerd
* de toestemmingsevaluatie wordt toegelaten slechts als optie **CUG-evaluatie ingeschakeld** wordt ook gecontroleerd.

In de nieuwe AEM standaardopstellingsevaluatie van het beleid van de GIDS, wordt het slechts toegelaten met &quot;publiceer&quot;looppaswijze. Zie de details op de [standaardconfiguratie sinds AEM 6.3](#default-configuration-since-aem) voor meer informatie . Dit kan worden geverifieerd door het effectieve beleid voor een bepaald pad te vergelijken met het beleid dat in de inhoud is opgeslagen. Het efficiënte beleid zal slechts worden getoond in het geval de toestemmingsevaluatie voor CUGs wordt toegelaten.

Zoals hierboven verklaard wordt het beleid van de toegangscontrole van de CUG nu altijd opgeslagen in de inhoud maar de evaluatie van de efficiënte toestemmingen die uit dat beleid voortvloeien zal slechts afdwingen als **CUG-evaluatie ingeschakeld** is ingeschakeld in de systeemconsole van Apache Jackrabbit Oak **CUG Configuration.** Deze optie is standaard alleen beschikbaar in de uitvoermodus Publiceren.

### Verschillen met betrekking tot verificatie {#differences-with-regards-to-authentication}

De verschillen met betrekking tot authentificatie worden hieronder beschreven.

#### Specifiek mixintype voor verificatievereiste {#dedicated-mixin-type-for-authentication-requirement}

In de vorige implementatie werden zowel de autorisatie- als de authenticatieaspecten van een CUG geactiveerd door één JCR-eigenschap ( `cq:cugEnabled`). Wat de authentificatie betreft, resulteerde dit in een bijgewerkte lijst van authentificatievereisten zoals die met de implementatie van de Authenticator van Apache Sling wordt opgeslagen. Met de nieuwe implementatie wordt hetzelfde resultaat bereikt door het doelknooppunt te markeren met een speciaal mixintype ( `granite:AuthenticationRequired`).

#### Eigenschap voor exclusief aanmeldingspad {#property-for-excluding-login-path}

Het mixintype definieert een enkele, optionele eigenschap, genaamd `granite:loginPath`, die in wezen overeenkomt met de `cq:cugLoginPage` eigenschap. In tegenstelling tot de vorige implementatie, wordt het login wegbezit slechts gerespecteerd als zijn verklarend knooptype de vermelde mixin is. Het toevoegen van een eigenschap met die naam zonder het mixintype in te stellen, heeft geen effect en er wordt geen nieuwe vereiste noch een uitsluiting voor het aanmeldingspad gerapporteerd aan de authenticator.

#### Bevoegdheid voor verificatievereiste {#privilege-for-authentication-requirement}

Voor het toevoegen of verwijderen van een mixintype is het vereist `jcr:nodeTypeManagement` het verlenen van een voorrecht. Bij de vorige uitvoering `jcr:modifyProperties` wordt gebruikt om de resterende eigenschap te bewerken.

Wat de `granite:loginPath` heeft betrekking op het zelfde recht wordt vereist om, het bezit toe te voegen te wijzigen of te verwijderen.

#### Doelknooppunt gedefinieerd door mixintype {#target-node-defined-by-mixin-type}

Creeer authentificatievereisten bij de knoop JCR die de subboom bepaalt te worden onderworpen aan gedwongen login. Dit is waarschijnlijk een AEM Pagina voor het geval dat de CUG naar verwachting de gehele boom zal beïnvloeden en UI voor de nieuwe implementatie voegt daarom het auto-vereiste mixintype op de paginaknooppunt toe.

Door het CUG-beleid alleen op het knooppunt jcr:content onder een bepaalde pagina te plaatsen, beperkt u alleen de toegang tot de inhoud. Het heeft echter geen invloed op het paginaknooppunt zelf of op onderliggende pagina&#39;s.

Dit kan een geldig scenario zijn en is mogelijk met een bewaargegevensverwerker die u de mixin bij om het even welk knooppunt laat plaatsen. Nochtans, contrasteert het gedrag de vroegere implementatie, waar het plaatsen van een bezit cq:cugEnabled of cq:cugLoginPage op jcr:content intern werd opnieuw in kaart gebracht uiteindelijk aan de paginaknooppunt. Deze toewijzing wordt niet meer uitgevoerd.

#### Geconfigureerde ondersteunde paden {#configured-supported-paths}

Beide `granite:AuthenticationRequired` mixintype en granite:loginPath bezit zullen slechts binnen het werkingsgebied worden gerespecteerd dat door de reeks wordt bepaald **Ondersteunde paden** configuratieoptie aanwezig met de **Vereiste van de Authentificatie van Granite van de Adobe en de Bediener van de Weg van de Login**. Als er geen paden zijn opgegeven, is de functie voor de verificatie-eisen volledig uitgeschakeld. In dit geval wordt het mixintype en de eigenschap van kracht wanneer het wordt toegevoegd aan of ingesteld op een bepaald JCR-knooppunt.

### Toewijzing van JCR-inhoud, OSGi-services en configuraties {#mapping-of-jcr-content-osgi-services-and-configurations}

Het document hieronder verstrekt een uitvoerige afbeelding van de diensten OSGi, configuraties, en bewaarplaatsinhoud tussen de oude en nieuwe implementatie.

CUG-toewijzing sinds AEM 6.3

[Bestand ophalen](assets/cug-mapping.pdf)

## CUG bijwerken {#upgrade-cug}

### Bestaande installaties die de afgekeurde CUG gebruiken {#existing-installations-using-the-deprecated-cug}

De oude implementatie van de CUG-ondersteuning is vervangen en wordt in toekomstige versies verwijderd. Het wordt aanbevolen over te schakelen op de nieuwe implementaties wanneer u een upgrade uitvoert van een lagere versie dan AEM 6.3.

Voor bijgewerkte AEM installatie, is het belangrijk om ervoor te zorgen dat slechts één implementatie van CUG wordt toegelaten. De combinatie van de nieuwe en de oude, verouderde ondersteuning van CUG wordt niet getest en kan ongewenste werking veroorzaken:

* botsingen in de Verschuivende Authenticator betreffende authentificatievereisten
* ontkende leestoegang wanneer de ACL opstelling verbonden aan de oude collides van de CUG met een nieuw beleid van de CUG.

### Bestaande CUG-inhoud migreren {#migrating-existing-cug-content}

Adobe biedt een hulpmiddel voor het migreren naar de nieuwe CUG-implementatie. Voer de volgende stappen uit om het te gebruiken:

1. Ga naar `https://<serveraddress>:<serverport>/system/console/cug-migration` om het gereedschap te openen.
1. Voer het hoofdpad in waarop u CUG&#39;s wilt controleren en druk op de knop **Tijdens de uitvoering drogen** knop. Dit scant naar CUG&#39;s die in aanmerking komen voor conversie op de geselecteerde locatie.
1. Nadat u de resultaten hebt bekeken, drukt u op de knop **Migratie uitvoeren** om naar de nieuwe implementatie te migreren.

>[!NOTE]
>
>Als u problemen ondervindt, is het mogelijk om een specifieke registreerfunctie in te stellen op **DEBUG** niveau `com.day.cq.auth.impl.cug` om de uitvoer van het migratiehulpprogramma te verkrijgen. Zie [Logboekregistratie](/help/sites-deploying/configure-logging.md) voor meer informatie over hoe dit te doen.
