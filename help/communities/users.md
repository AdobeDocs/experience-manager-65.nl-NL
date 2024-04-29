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

* Subgemeenschappen maken binnen de communitysite (zie [communautaire groepen](creating-groups.md)).

* [Gemiddeld](moderation.md) door de gebruiker gegenereerde inhoud (UGC).

* zijn [bevoorrecht](#privileged-members-group) om berichten voor blogs, kalenders, QnA en forums te maken.

In de publicatieomgeving geregistreerde gebruikers worden doorgaans *leden van de gemeenschap ( leden )* om ze van elkaar te onderscheiden *gebruikers* in de ontwerpomgeving.

Machtigingen worden verleend door leden toe te wijzen aan een van de [leden (gebruikersgroepen)](#publish-group-roles) dynamisch gemaakt wanneer de communitysite wordt [gemaakt](sites-console.md) of [gewijzigd](sites-console.md#modifying-site-properties) van de auteur-omgeving. Wanneer het werken van het auteursmilieu, zijn de leden zichtbaar van het publicatiemilieu door [tunneldienst](#tunnel-service).

Door ontwerp, leden en lidgroepen die in het publicatiemilieu worden gecreeerd zouden niet in het auteursmilieu moeten verschijnen. Gebruikers en gebruikersgroepen die in de auteursomgeving zijn gemaakt, moeten ook in de auteursomgeving blijven.

Wanneer gebruikers op auteur en leden die publiceren uit dezelfde lijst met gebruikers komen, zoals die vanuit dezelfde LDAP-directory zijn gesynchroniseerd, worden ze niet beschouwd als dezelfde gebruiker met dezelfde machtigingen en groepslidmaatschap in zowel de auteur- als de publicatieomgeving. De rol(en) van leden en gebruikers moet(en) afzonderlijk worden vastgesteld bij publicatie en auteur, al naargelang het geval.

Voor een [publicatiebedrijf](topologies.md), moeten registratie en wijzigingen die op één publicatie-instantie zijn aangebracht, worden gesynchroniseerd met andere publicatie-instanties, zodat deze toegang hebben tot dezelfde gebruikersgegevens. Zie voor meer informatie [Gebruikerssynchronisatie](sync.md), dat een sectie bevat die een beschrijving bevat [Wat gebeurt er als...](sync.md#what-happens-when).

### Bijdragelimieten {#contribution-limits}

Ter bescherming tegen spam is het mogelijk de frequentie van het plaatsen van inhoud door leden te beperken. Bovendien is het mogelijk de bijdragen van nieuw geregistreerde leden automatisch te beperken.

Zie voor meer informatie [Limieten voor bijdragen van de lidstaten](limits.md).

### Dynamisch gemaakte gebruikersgroepen {#dynamically-created-user-groups}

Wanneer een nieuwe communautaire plaats wordt gecreeerd, worden de nieuwe gebruikersgroepen dynamisch gecreeerd met unieke identiteitskaart (uid) en toestemmingen aangewezen voor diverse administratieve functies noodzakelijk om de communautaire plaats of in het auteursmilieu te beheren (zie [Auteursgroeprollen](#author-group-roles)) of de publicatieomgeving (zie [Groeprollen publiceren](#publish-group-roles)).

De namen van de groepen worden gegenereerd op basis van de naam die de site tijdens [site maken](sites-console.md#step13asitetemplate). Unieke id&#39;s vermijden naamgevingsconflicten voor sites met dezelfde naam en groepen van gemeenschappen op dezelfde server.

Als de naam van de site bijvoorbeeld &quot;*aangaan*&quot; voor een site met de naam &quot; Inschakelen&quot;, wordt een van de volgende gebruikersgroepen gemaakt:

* Gemeenschap *Inschakelen* Leden

## Auteursomgeving {#author-environment}

### Tunnelservice {#tunnel-service}

Wanneer u de ontwerpomgeving gebruikt voor [sites maken](sites-console.md), [site-eigenschappen wijzigen](sites-console.md#modifying-site-properties) en [leden van de gemeenschap en leden beheren](members.md), is het noodzakelijk om toegang te krijgen tot gebruikers en gebruikersgroepen die in de publicatieomgeving zijn geregistreerd.

De tunneldienst verleent deze toegang gebruikend de replicatieagent op auteur.

* Zie voor meer informatie [configuratieinstructies](deploy-communities.md#tunnel-service-on-author) op de implementatiepagina.

De [Samenstellingen van leden en groepen](members.md) uitsluitend ten behoeve van het beheer van gebruikers (leden) en gebruikersgroepen (lidgroepen) die alleen in de publicatieomgeving zijn geregistreerd.

Als u gebruikers en gebruikersgroepen wilt beheren die zijn geregistreerd in de ontwerpomgeving, gebruikt u de opdracht [Beveiligingsconsole](../../help/sites-administering/security.md)

### Auteursgroeprollen {#author-group-roles}

| Indien lid van de groep... | Primaire rol |
|---|---|
| beheerders | De beheerdersgroep bestaat uit systeembeheerders die alle capaciteiten van een communautaire beheerder en de capaciteit hebben om de groep van Communautaire Beheerders te beheren. |
| Community-beheerders | De communautaire groep van Beheerders wordt automatisch een lid van alle communautaire plaatsen en om het even welke communautaire groepen die op de plaats worden gecreeerd. Een aanvankelijk lid van de groep van Communautaire Beheerders is de beheerdersgroep. In de auteursomgeving, kunnen de Communautaire Beheerders communautaire plaatsen tot stand brengen, plaatsen beheren, leden beheren (zij kunnen leden van de gemeenschap verbieden), en gematigde inhoud. |
| Community &lt;*sitenaam*> Sitecontentmanager | Met Community Site Content Manager kunt u traditionele AEM ontwerpen, inhoud maken en pagina&#39;s voor een communitysite wijzigen. |
| Geen | Een anonieme sitebezoeker heeft mogelijk geen toegang tot de auteursomgeving. |

### Systeembeheerders {#system-administrators}

De leden van de beheerdersgroep zijn systeembeheerders die de aanvankelijke opstelling van een AEM installatie voor zowel de auteur als publicatiemilieu&#39;s kunnen uitvoeren.

Voor demonstratie- en ontwikkelingsdoeleinden heeft de groep met beheerders een lid waarvan de gebruiker *admin* en wachtwoord is *admin*.

Voor productieomgevingen moet de standaardbeheerdersgroep worden gewijzigd.

Zorg ervoor dat u de [Beveiligingscontrolelijst](../../help/sites-administering/security-checklist.md).

## Publicatie-omgeving {#publish-environment}

### Lid worden {#becoming-a-member}

Afhankelijk van de [instellingen](sites-console.md#user-management) van de communautaire site kan een bezoeker van de site lid worden van de gemeenschap :

* Wanneer de site van de community privé is (gesloten):
   * Op uitnodiging
   * Op handelingen van een beheerder

* Wanneer de site van de community openbaar is (open):
   * Op zelfregistratie
   * Op sociale aanmelding met Facebook en Twitter

>[!NOTE]
>
>Als een bezoeker van een site zich registreert als lid van één open communitysite, worden deze automatisch lid van andere open communitysites in dezelfde publicatieomgeving.

### Groeprollen publiceren {#publish-group-roles}

| Indien lid van de groep... | Primaire rol |
|---|---|
| Community &lt;*sitenaam*> Leden | Een lid van de community is een geregistreerde gebruiker. Ze kunnen zich aanmelden, hun profiel wijzigen, deelnemen aan een open community-groep, inhoud posten naar de community, berichten verzenden naar andere leden en activiteiten op de site volgen. |
| Community &lt;*sitenaam*> Moderatoren | Een moderator van de communautaire plaats is een vertrouwd communautair lid dat UGC of in bulk, gebruikend de moderatieconsole, of in context, op de pagina kan matigen waar de inhoud wordt gepost. |
| Community &lt;*sitenaam*> &lt;*groepsnaam*> Leden | Een lid van een communautaire groep is een lid van de gemeenschap dat zich heeft aangesloten bij een open communautaire groep of is uitgenodigd voor een gesloten communautaire groep. Zij hebben de capaciteiten van een lid voor die communautaire groep binnen de plaats. |
| Community &lt;*sitenaam*> Groepbeheerders | Een beheerder van een community-sitegroep is een vertrouwd communitylid dat is toegewezen aan het maken en beheren van subgemeenschappen (groepen) binnen een communitysite. Omvat is het vermogen om in-context matiging te verstrekken. |
| *Bevoorrechte ledenbeveiligingsgroep* | Een handmatig gemaakte en onderhouden gebruikersgroep om het maken van inhoud te beperken. Zie [Groep met geprivilegieerde leden](#privileged-members-group). |
| Geen | Een anonieme sitebezoeker, die de site ontdekt, kan gemeenschapssites weergeven en doorzoeken die anonieme toegang toestaan. Om deel te nemen en inhoud te posten, moet de gebruiker zich (indien toegestaan) registreren en een lid van de gemeenschap worden. |

### Leden toewijzen aan rollen van groepen publiceren {#assigning-members-to-publish-group-roles}

Wanneer [het creëren van een communautaire plaats](sites-console.md) in de ontwerpomgeving, of wanneer [site-eigenschappen wijzigen;](sites-console.md#modifying-site-properties) leden kunnen diverse rollen worden toegewezen die in het publicatiemilieu, zoals moderatoren, groepsbeheerders, middelcontacten, of bevoorrechte leden worden uitgevoerd.

[Het toelaten van de tunneldienst](sync.md#accessingpublishusersfromauthor) resulteert in toewijzingskeuzen die door leden bij publicatie worden voorgesteld in plaats van gebruikers bij auteur.

De geselecteerde leden worden automatisch toegewezen aan de [passende groep](#publish-group-roles) en hun lidmaatschap zal worden opgenomen wanneer de site van de gemeenschap ( opnieuw ) wordt gepubliceerd .

### Groep met geprivilegieerde leden {#privileged-members-group}

Het doel van een bevoorrechte groep van de ledenveiligheid is de verwezenlijking van inhoud voor bepaalde communautaire functies tot een bevoorrechte ondergroep van de leden van een communautaire plaats te beperken.

De bevoorrechte ledengroep is een lidgroep die wordt gecreeerd en wordt beheerd gebruikend [console Gemeenschappen/Groepen](members.md).

Nadat een bevoorrechte ledengroep wordt gecreeerd, en met [tunnelservice ingeschakeld](sync.md#accessingpublishusersfromauthor)kan een bestaande structuur van een communautaire site [gewijzigd](sites-console.md#modify-structure) om de configuratie van zijn communityfuncties te bewerken naar &#39;Geprivilegieerde leden toestaan&#39; en de gemaakte groep toe te voegen.

De communautaire functies die de specificatie van een of meer bevoorrechte ledengroepen mogelijk maken, zijn:

* [Blogfunctie](functions.md#blog-function) - Het maken van nieuwe artikelen beperken.
* [Kalenderfunctie](functions.md#calendar-function) - Het creëren van nieuwe evenementen beperken.
* [Forum, functie](functions.md#forum-function) - Het creëren van nieuwe onderwerpen beperken.
* [QnA-functie](functions.md#qna-function) - Het creëren van nieuwe vragen beperken.

Wanneer een communautaire functie niet wordt beveiligd (geen bevoorrechte toegewezen lidgroep), dan kunnen alle leden van de communautaire plaats eigenschapinhoud (artikelen, gebeurtenissen, onderwerpen, vragen) tot stand brengen.

>[!NOTE]
>
>Als u een gebruiker toevoegt aan een geprivilegieerde ledengroep voor een communitysite, worden er alleen privileges toegekend aan gebruikers die ook lid zijn van dezelfde communitysite.

## Communautaire leden creëren {#creating-community-members}

### Locatie opslagplaats {#repository-location}

Bepaalde functies werken alleen correct als u gebruikers en gebruikersgroepen met de juiste rechten maakt.

Wanneer leden worden gemaakt in `/home/users/community`, erven zij juiste ACLs die gelezen voorrechten aan de profielen van leden geven.

Op dezelfde manier zouden de gebruikersgroepen van de douanegemeenschap (zoals bevoorrechte ledengroepen) in moeten worden gecreeerd `/home/groups/community`.

Met de [Samenstellingen van leden en groepen](members.md) Hiermee maakt u gebruikers en groepen in deze paden.

Als u een aangepast pad wilt opgeven, moet u de klassieke beveiligingsinterface gebruiken. Deze interface is toegankelijk op [https://&lt;server>:&lt;port>/useradmin](http://localhost:4503/useradmin).

Om gelezen voorrechten voor de wegen van het douanelidje te geven, op alle publiceer instanties vastgestelde ACLs gelijkend op `/home/users/community`:

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

Om de juiste voorrechten voor de wegen van de douanelidgroep, zoals /home/groups/mycompany, op alle te geven publiceer instanties plaatsen ACLs gelijkend op `/home/groups/community`:

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

Zoals vermeld in het [Auteursgroeprollen](#author-group-roles) in kaart brengen, kunnen de leden van de groep van Beheerders Gemeenschap communautaire plaatsen tot stand brengen, plaatsen beheren, leden beheren (zij kunnen leden van de gemeenschap verbieden), en gematigde inhoud.

Voer dezelfde stappen uit als het maken en toewijzen van een gebruiker aan de rol van enablement Manager, maar voeg c toe `ommunity-administrators` onder het tabblad Groepen van de gebruiker.

### LDAP-integratie {#ldap-integration}

AEM ondersteunt het gebruik van LDAP voor verificatie van gebruikers en het maken van gebruikersaccounts. Dit wordt nader beschreven in [LDAP configureren met AEM 6](../../help/sites-administering/ldap-config.md).

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

Dit leidt ertoe dat gebruikers automatisch worden toegewezen aan de groep leden van de site van de community en dat de locatie van de opslagplaats `/home/users/community` en `/home/groups/community`, zodat ze de juiste machtigingen overnemen om elkaars profiel te zien.

* De `User auto membership` waarde moet `rep:authorizableId` eigenschap, niet de `givenName` (weergavenaam) uit het profiel.

## Gebruikers synchroniseren tussen AEM instanties {#synchronizing-users-among-aem-instances}

Wanneer u een [publicatiebedrijf](topologies.md), zorgt u ervoor dat gebruikers op elke publicatie-instantie hetzelfde pad hebben door de gebruikers eerst in één instantie te importeren en [gebruikerssynchronisatie inschakelen](sync.md) om de gebruikers naar de andere publicatieinstanties te distribueren.

Als u gebruikersgroepen importeert, importeert u naar één instantie om ervoor te zorgen dat de gebruikersgroepen op elk publicatie-exemplaar hetzelfde pad hebben. [een pakket maken](../../help/sites-administering/package-manager.md#creating-a-new-package) voor export en installeer dat pakket op alle andere publicatieinstanties.

Hoewel het synchroniseren van gebruikersgroepen via gebruikerssynchronisatie in een toekomstige release wordt opgenomen, worden momenteel alleen de *lidmaatschap* van een gebruikersgroep synchroniseren wanneer de gebruikerssynchronisatie wordt uitgevoerd.

## Informatie over communautaire groepen {#about-community-groups}

Wanneer het bespreken van groepen, zijn er twee verschillende onderwerpen:

* **[Communautaire groepen](overview.md#communitygroups)**

  Communautaire groepen zijn de subgemeenschappen die kunnen worden gecreëerd in de publicatieomgeving voor een communautaire site die de oprichting van groepen van gemeenschappen ondersteunt. Als u een community maakt, worden er meer pagina&#39;s toegevoegd aan de website en worden deze beheerd op een manier die vergelijkbaar is met de bovenliggende community-site. Voor meer informatie gaat u naar [Essentiële elementen van gebruikersgroepen](essentials-groups.md) voor ontwikkelaars en [Communautaire groep](creating-groups.md) voor auteurs.

* **[Leden](../../help/sites-administering/security.md)**

  De groepen van de leden zijn de groepen waartot de leden kunnen behoren en door de console van Groepen worden geleid. Een groot deel van de discussie over deze pagina is gewijd aan de leden van de fracties. De ledengroepen die automatisch voor een communitysite worden gemaakt, worden vooraf ingesteld op *`Community`*, kan worden aangeduid als een communautaire groep, zodat de context van de discussie moet worden overwogen.
