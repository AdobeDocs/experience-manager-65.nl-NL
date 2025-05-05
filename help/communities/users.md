---
title: Gebruikers en gebruikersgroepen beheren
description: Gebruikers van AEM Communities kunnen zichzelf registreren en hun profielen bewerken
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
role: Admin
exl-id: 4237085a-d70d-41de-975d-153f58336daa
solution: Experience Manager
feature: Communities
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '1901'
ht-degree: 0%

---

# Gebruikers en gebruikersgroepen beheren {#managing-users-and-user-groups}

## Overzicht {#overview}

In AEM Communities kunnen gebruikers zichzelf registreren en hun profielen bewerken in de publicatieomgeving. Op basis van de juiste machtigingen kunnen zij ook:

* Creeer sub-gemeenschappen binnen de communautaire plaats (zie [ communautaire groepen ](creating-groups.md)).

* [ Gematigde ](moderation.md) gebruiker produceerde inhoud (UGC).

* Ben [ bevoorrecht ](#privileged-members-group) om ingangen voor blogs, kalenders, QnA, en forums tot stand te brengen.

De gebruikers in publiceren milieu worden geregistreerd worden over het algemeen bedoeld als *communautaire leden (leden)* om hen van *gebruikers* in het auteursmilieu te onderscheiden.

De toestemmingen worden verleend door leden aan één van de [ lid (gebruiker) groepen ](#publish-group-roles) toe te wijzen dynamisch gecreeerd wanneer de communautaire plaats [&#128279;](sites-console.md) of [ gewijzigd ](sites-console.md#modifying-site-properties) van het auteursmilieu wordt gecreeerd. Wanneer het werken van het auteursmilieu, zijn de leden zichtbaar van het publicatiemilieu door middel van de [ tunneldienst ](#tunnel-service).

Door ontwerp, leden en lidgroepen die in het publicatiemilieu worden gecreeerd zouden niet in het auteursmilieu moeten verschijnen. Gebruikers en gebruikersgroepen die in de auteursomgeving zijn gemaakt, moeten ook in de auteursomgeving blijven.

Wanneer gebruikers op auteur en leden die publiceren uit dezelfde lijst met gebruikers komen, zoals die vanuit dezelfde LDAP-directory zijn gesynchroniseerd, worden ze niet beschouwd als dezelfde gebruiker met dezelfde machtigingen en groepslidmaatschap in zowel de auteur- als de publicatieomgeving. De rol(en) van leden en gebruikers moet(en) afzonderlijk worden vastgesteld bij publicatie en auteur, al naargelang het geval.

Voor a [ publiceer landbouwbedrijf ](topologies.md), moeten de registratie en de wijzigingen die op één worden aangebracht publiceren instantie met andere worden gesynchroniseerd publiceren instanties opdat zij toegang tot de zelfde gebruikersgegevens hebben. Voor details zie [ Synchronisatie van de Gebruiker ](sync.md), die een sectie omvat die [ beschrijft wat gebeurt wanneer... ](sync.md#what-happens-when).

### Bijdragelimieten {#contribution-limits}

Ter bescherming tegen spam is het mogelijk de frequentie van het plaatsen van inhoud door leden te beperken. Bovendien is het mogelijk de bijdragen van nieuw geregistreerde leden automatisch te beperken.

Voor details, zie {de Limieten van de Bijdrage van 0} Lid [&#128279;](limits.md).

### Dynamisch gemaakte gebruikersgroepen {#dynamically-created-user-groups}

Wanneer een nieuwe communautaire plaats wordt gecreeerd, worden de nieuwe gebruikersgroepen dynamisch gecreeerd met unieke identiteitskaart (uid) en toestemmingen aangewezen voor diverse administratieve functies noodzakelijk om de communautaire plaats of in het auteursmilieu (zie {de Rollen van de Groep van de 0} Auteur [&#128279;](#author-group-roles)) of het publicatiemilieu (zie [ Rollen van de Groep van Publish ](#publish-group-roles)) te beheren.

De namen van de groepen worden geproduceerd van de naam die de plaats tijdens [ wordt gegeven de verwezenlijking van de communautaire plaats ](sites-console.md#step13asitetemplate). Unieke id&#39;s vermijden naamgevingsconflicten voor sites met dezelfde naam en groepen van gemeenschappen op dezelfde server.

Bijvoorbeeld, als de plaatsnaam &quot;**&quot;voor een plaats genoemd &quot;Ingenieur&quot;was in dienst nemen, dan zou één van de gemaakte gebruikersgroepen zijn:

* Communautaire *Betrokkenheid* Leden

## Auteursomgeving {#author-environment}

### Tunnelservice {#tunnel-service}

Wanneer het gebruiken van het auteursmilieu om plaatsen [&#128279;](sites-console.md) te creëren, [ wijzig plaatseigenschappen ](sites-console.md#modifying-site-properties) en [ beheer communautaire leden en lidgroepen ](members.md), is het noodzakelijk om tot gebruikers en gebruikersgroepen toegang te hebben die in het publicatiemilieu worden geregistreerd.

De tunneldienst verleent deze toegang gebruikend de replicatieagent op auteur.

* Voor details, zie [ configuratieinstructies ](deploy-communities.md#tunnel-service-on-author) op de plaatsingspagina.

De [ leden van Gemeenschappen en de Groepen consoles ](members.md) zijn voor het enige doel van het beheren van gebruikers (leden) en gebruikersgroepen (lidgroepen) die slechts in het publicatiemilieu worden geregistreerd.

Om gebruikers en gebruikersgroepen te beheren die in het auteursmilieu worden geregistreerd, gebruik de [ console van de Veiligheid ](../../help/sites-administering/security.md)

### Auteursgroeprollen {#author-group-roles}

| Indien lid van de groep... | Primaire rol |
|---|---|
| beheerders | De beheerdersgroep bestaat uit systeembeheerders die alle capaciteiten van een communautaire beheerder en de capaciteit hebben om de groep van Communautaire Beheerders te beheren. |
| Community-beheerders | De communautaire groep van Beheerders wordt automatisch een lid van alle communautaire plaatsen en om het even welke communautaire groepen die op de plaats worden gecreeerd. Een aanvankelijk lid van de groep van Communautaire Beheerders is de beheerdersgroep. In de auteursomgeving, kunnen de Communautaire Beheerders communautaire plaatsen tot stand brengen, plaatsen beheren, leden beheren (zij kunnen leden van de gemeenschap verbieden), en gematigde inhoud. |
| Communautaire &lt;*plaatsnaam*> Sitecontentmanager | Met Community Site Content Manager kunt u traditionele AEM ontwerpen, inhoud maken en pagina&#39;s voor een communitysite wijzigen. |
| Geen | Een anonieme sitebezoeker heeft mogelijk geen toegang tot de auteursomgeving. |

### Systeembeheerders {#system-administrators}

De leden van de beheerdersgroep zijn systeembeheerders die de aanvankelijke opstelling van een AEM installatie voor zowel de auteur als publicatiemilieu&#39;s kunnen uitvoeren.

Voor demonstratie en ontwikkelingsdoeleinden, heeft de beheerdersgroep een lid de waarvan gebruikersbenaming *admin* is en het wachtwoord is *admin*.

Voor productieomgevingen moet de standaardbeheerdersgroep worden gewijzigd.

Ben zeker om de [ Controlelijst van de Veiligheid te volgen ](../../help/sites-administering/security-checklist.md).

## Publish-omgeving {#publish-environment}

### Lid worden {#becoming-a-member}

In publiceer milieu, afhankelijk van de [ montages ](sites-console.md#user-management) van de communautaire plaats, kan een plaatsbezoeker een communautair lid worden:

* Wanneer de site van de community privé is (gesloten):
   * Op uitnodiging
   * Op handelingen van een beheerder

* Wanneer de site van de community openbaar is (open):
   * Op zelfregistratie
   * Op sociale aanmelding met Facebook en Twitter

>[!NOTE]
>
>Als een bezoeker van een site zich registreert als lid van één open communitysite, worden deze automatisch lid van andere open communitysites in dezelfde publicatieomgeving.

### Publish-groeprollen {#publish-group-roles}

| Indien lid van de groep... | Primaire rol |
|---|---|
| Communautaire &lt;*plaatsnaam*> Leden | Een lid van de community is een geregistreerde gebruiker. Ze kunnen zich aanmelden, hun profiel wijzigen, deelnemen aan een open community-groep, inhoud posten naar de community, berichten verzenden naar andere leden en activiteiten op de site volgen. |
| Communautaire &lt;*plaatsnaam*> Moderatoren | Een moderator van de communautaire plaats is een vertrouwd communautair lid dat UGC of in bulk, gebruikend de moderatieconsole, of in context, op de pagina kan matigen waar de inhoud wordt gepost. |
| Communautaire &lt;*plaatsnaam*> &lt;*groepsnaam*> Leden | Een lid van een communautaire groep is een lid van de gemeenschap dat zich heeft aangesloten bij een open communautaire groep of is uitgenodigd voor een gesloten communautaire groep. Zij hebben de capaciteiten van een lid voor die communautaire groep binnen de plaats. |
| Communautaire &lt;*plaatsnaam*> Groepbeheerders | Een beheerder van een community-sitegroep is een vertrouwd communitylid dat is toegewezen aan het maken en beheren van subgemeenschappen (groepen) binnen een communitysite. Omvat is het vermogen om in-context matiging te verstrekken. |
| *Geprivilegieerde Groep van de Veiligheid van Leden* | Een handmatig gemaakte en onderhouden gebruikersgroep om het maken van inhoud te beperken. Zie [ Geprivilegieerde Groep van Leden ](#privileged-members-group). |
| Geen | Een anonieme sitebezoeker, die de site ontdekt, kan gemeenschapssites weergeven en doorzoeken die anonieme toegang toestaan. Om deel te nemen en inhoud te posten, moet de gebruiker zich (indien toegestaan) registreren en een lid van de gemeenschap worden. |

### Leden toewijzen aan Publish-groepsrollen {#assigning-members-to-publish-group-roles}

Wanneer [ creërend een communautaire plaats ](sites-console.md) in het auteursmilieu, of wanneer [ het wijzigen van plaatseigenschappen, ](sites-console.md#modifying-site-properties) leden diverse rollen kunnen worden toegewezen die in het publicatiemilieu, zoals moderators, groepsbeheerders, middelcontacten, of bevoorrechte leden worden uitgevoerd.

[ toelatend de tunneldienst ](sync.md#accessingpublishusersfromauthor) resulteert in taakkeuzen die van leden op worden voorgesteld publiceren in plaats van gebruikers op auteur.

De geselecteerde leden zullen automatisch aan de [ aangewezen groep ](#publish-group-roles) worden toegewezen en hun lidmaatschap zal inbegrepen zijn wanneer de communautaire plaats (opnieuw) wordt gepubliceerd.

### Groep met geprivilegieerde leden {#privileged-members-group}

Het doel van een bevoorrechte groep van de ledenveiligheid is de verwezenlijking van inhoud voor bepaalde communautaire functies tot een bevoorrechte ondergroep van de leden van een communautaire plaats te beperken.

De bevoorrechte ledengroep is een lidgroep die wordt gecreeerd en wordt geleid gebruikend de [ console van de Groepen van Gemeenschappen ](members.md).

Nadat een bevoorrechte ledengroep wordt gecreeerd, en met de [ toegelaten tunneldienst ](sync.md#accessingpublishusersfromauthor), kan de structuur van een bestaande communautaire plaats [ worden gewijzigd ](sites-console.md#modify-structure) om de configuratie van zijn communautaire functies uit te geven om &quot;Geprivilegieerde Leden&quot;toe te staan en de gecreeerde groep toe te voegen.

De communautaire functies die de specificatie van een of meer bevoorrechte ledengroepen mogelijk maken, zijn:

* [ functie Blog ](functions.md#blog-function) - om verwezenlijking van nieuwe artikelen te beperken.
* [ functie van de Kalender ](functions.md#calendar-function) - om verwezenlijking van nieuwe gebeurtenissen te beperken.
* [ functie van het Forum ](functions.md#forum-function) - om verwezenlijking van nieuwe onderwerpen te beperken.
* [ functie QnA ](functions.md#qna-function) - om verwezenlijking van nieuwe vragen te beperken.

Wanneer een communautaire functie niet wordt beveiligd (geen bevoorrechte toegewezen lidgroep), dan kunnen alle leden van de communautaire plaats eigenschapinhoud (artikelen, gebeurtenissen, onderwerpen, vragen) tot stand brengen.

>[!NOTE]
>
>Als u een gebruiker toevoegt aan een geprivilegieerde ledengroep voor een communitysite, worden er alleen privileges toegekend aan gebruikers die ook lid zijn van dezelfde communitysite.

## Communautaire leden creëren {#creating-community-members}

### Locatie opslagplaats {#repository-location}

Bepaalde functies werken alleen correct als u gebruikers en gebruikersgroepen met de juiste rechten maakt.

Wanneer leden in `/home/users/community` worden gecreeerd, erven zij juiste ACLs die gelezen voorrechten aan de profielen van leden geven.

Op dezelfde manier moeten aangepaste gebruikersgroepen (zoals groepen van geprivilegieerde leden) worden gemaakt in `/home/groups/community` .

Gebruikend de [ leden van Gemeenschappen en de Groepen consoles ](members.md) zullen tot gebruikers en groepen in deze wegen leiden.

Om een douanepad te specificeren vereist gebruik van de klassieke veiligheid UI, die in [ https://&lt;server>:&lt;port>/useradmin ](http://localhost:4503/useradmin) toegankelijk is.

Om leesvoorrechten voor de wegen van het douanelid te geven, op alle publiceer instanties plaats ACLs gelijkend op `/home/users/community`:

```xml
<allow
  jcr:primaryType="rep:GrantACE"
  rep:principalName="everyone"
  rep:privileges="{Name}[jcr:read]" >
  <rep:restrictions
    jcr:primaryType="rep:Restrictions"
    rep:glob="*/profile*" />
</allow>
```

Om de juiste voorrechten voor de wegen van de douanelidgroep, zoals /home/groups/mijnbedrijf te geven, op alle publiceer instanties vastgestelde ACLs gelijkend op `/home/groups/community`:

```xml
<allow
  jcr:primaryType="rep:GrantACE"
  rep:principalName="community-administrators"
  rep:privileges="{Name}[jcr:read]"  />
```

### Consoles {#consoles}

Er zijn vier afzonderlijke consoles beschikbaar slechts in het auteursmilieu:

| console | Gereedschappen, beveiliging, gebruikers | Gereedschappen, Beveiliging, Groepen | Gemeenschappen, leden | Gemeenschappen, groepen |
|----------|-----------------------|------------------------|------------------------------------------------------------|------------------------------------------------------------|
| beheert | gebruikers op auteur | gebruikersgroepen bij auteur | leden die publiceren | lidgroepen die worden gepubliceerd |
| vereist | beheerdersbevoegdheid | beheerdersbevoegdheid | beheerdersrechten, tunnelservice, gebruikerssynchronisatie voor publicatiefarm | beheerdersrechten, tunnelservice, gebruikerssynchronisatie voor publicatiefarm |

### Rol van communautaire beheerders {#community-administrators-role}

Zoals vermeld in de [&#128279;](#author-group-roles) grafiek van de Rollen van de Groep van de Auteur , kunnen de leden van de groep van Communautaire Beheerders communautaire plaatsen tot stand brengen, plaatsen beheren, leden beheren (zij kunnen leden van de gemeenschap), en gematigde inhoud verbieden.

Voer dezelfde stappen uit als het maken en toewijzen van een gebruiker aan de rol van enablement Manager, maar voeg C `ommunity-administrators` -groep toe onder het tabblad Groepen van de gebruiker.

### LDAP-integratie {#ldap-integration}

AEM ondersteunt het gebruik van LDAP voor verificatie van gebruikers en het maken van gebruikersaccounts. Dit wordt gedetailleerd in [ Vormend LDAP met AEM 6 ](../../help/sites-administering/ldap-config.md).

Hier volgt een aantal configuratiedetails die specifiek zijn voor leden van de gemeenschap en lidgroepen.

1. Configureer LDAP voor elke AEM-publicatie-instantie.
2. [De LDAP-identiteitsprovider](../../help/sites-administering/ldap-config.md#configuring-the-ldap-identity-provider)

   * Geen speciale instructies

3. [De Synchronisatie-handler](../../help/sites-administering/ldap-config.md#configuring-the-synchronization-handler)

   * Stel de volgende eigenschappen in:

      * **[!UICONTROL User auto membership]**: `community-<site name>-<uid>-members`
      * **[!UICONTROL User Path Prefix]**: `/community`
      * **[!UICONTROL Group Path Prefix]**: `/community`

4. [De externe aanmeldingsmodule](../../help/sites-administering/ldap-config.md#the-external-login-module)

   * geen speciale instructies

Dit betekent dat gebruikers automatisch worden toegewezen aan de groep leden van de site van de community en dat de locatie in de repository `/home/users/community` en `/home/groups/community` is, zodat ze de juiste machtigingen overnemen om elkaars profiel te zien.

* De waarde `User auto membership` moet de eigenschap `rep:authorizableId` zijn, niet de eigenschap `givenName` (weergavenaam) van het profiel.

## Gebruikers synchroniseren tussen AEM instanties {#synchronizing-users-among-aem-instances}

Wanneer het gebruiken van a [ landbouwbedrijf ](topologies.md) publiceert, zorg ervoor gebruikers de zelfde weg op elke publiceer instantie hebben door de gebruikers eerst aan één instantie in te voeren en [ toelatend gebruikerssynchronisatie ](sync.md) aan Sling te verdelen de gebruikers aan andere publiceer instanties.

Als het invoeren van gebruikersgroepen, om de gebruikersgroepen te verzekeren hebben de zelfde weg op elke publiceer instantie, de invoer in één instantie, dan [ creeert een pakket ](../../help/sites-administering/package-manager.md#creating-a-new-package) voor de uitvoer, en installeert dat pakket op alle andere publiceer instanties.

Terwijl het synchroniseren van gebruikersgroepen door gebruikerssynchronisatie in een toekomstige versie zal worden omvat, momenteel slechts zal het *lidmaatschap* van een gebruikersgroep synchroniseren wanneer de looppas van de gebruikerssynchronisatie.

## Informatie over communautaire groepen {#about-community-groups}

Wanneer het bespreken van groepen, zijn er twee verschillende onderwerpen:

* **[Communautaire groepen](overview.md#communitygroups)**

  Communautaire groepen zijn de subgemeenschappen die kunnen worden gecreëerd in de publicatieomgeving voor een communautaire site die de oprichting van groepen van gemeenschappen ondersteunt. Als u een community maakt, worden er meer pagina&#39;s toegevoegd aan de website en worden deze beheerd op een manier die vergelijkbaar is met de bovenliggende community-site. Voor meer informatie bezoekt {de Hoofdzaak van de Groep van de Gemeenschap 0} [&#128279;](essentials-groups.md) voor ontwikkelaars en [ Communautaire Groep ](creating-groups.md) voor auteurs.

* **[de groepen van het Lid](../../help/sites-administering/security.md)**

  De groepen van de leden zijn de groepen waartot de leden kunnen behoren en door de console van Groepen worden geleid. Een groot deel van de discussie over deze pagina is gewijd aan de leden van de fracties. De groepen leden die automatisch voor een communitysite worden gemaakt en vooraf aan *`Community`* zijn toegewezen, kunnen als een community-groep worden aangeduid. Daarom moet de context van de discussie in overweging worden genomen.
