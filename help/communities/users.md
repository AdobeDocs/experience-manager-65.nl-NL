---
title: Gebruikers en gebruikersgroepen beheren
seo-title: Gebruikers en gebruikersgroepen beheren
description: Gebruikers van AEM Communities kunnen zichzelf registreren en hun profielen bewerken
seo-description: Gebruikers van AEM Communities kunnen zichzelf registreren en hun profielen bewerken
uuid: aeba424e-ea7e-4da5-b94f-ea8af4caa7d2
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 774c2553-b629-456b-afa7-5713490f4a0a
translation-type: tm+mt
source-git-commit: c190d5f223c85f6c49fea1391d8a3d2baff20192
workflow-type: tm+mt
source-wordcount: '2168'
ht-degree: 0%

---


# Managing Users and User Groups {#managing-users-and-user-groups}

## Overzicht {#overview}

In AEM Communities kunnen gebruikers zichzelf registreren en hun profielen bewerken in de publicatieomgeving. Op basis van de juiste machtigingen kunnen zij ook:

* Subgemeenschappen maken op de site van de community (zie [groepen](creating-groups.md)van gemeenschappen).

* [Door de gebruiker gegenereerde inhoud (UGC) is matig](moderation.md) .

* Ben [enablement middelcontacten](resources.md) .

* U kunt [](#privileged-members-group) vermeldingen maken voor blogs, kalenders, QnA en forums.

Gebruikers die in de publicatieomgeving zijn geregistreerd, worden doorgaans leden van de *community (leden)* genoemd om ze te onderscheiden van *gebruikers* in de auteursomgeving.

De toestemmingen worden verleend door leden aan één van de [lid (gebruiker) groepen](#publish-group-roles) toe te wijzen dynamisch gecreeerd wanneer de communautaire plaats wordt [gecreeerd](sites-console.md) of [gewijzigd](sites-console.md#modifying-site-properties) van het auteursmilieu. Wanneer het werken van het auteursmilieu, zijn de leden zichtbaar van het publicatiemilieu door de [tunneldienst](#tunnel-service).

Door ontwerp, leden en lidgroepen die in het publicatiemilieu worden gecreeerd zouden niet in het auteursmilieu moeten verschijnen. Gebruikers en gebruikersgroepen die in de auteursomgeving zijn gemaakt, moeten ook in de auteursomgeving blijven.

Wanneer gebruikers op auteur en leden die publiceren uit dezelfde lijst met gebruikers komen, zoals die vanuit dezelfde LDAP-directory zijn gesynchroniseerd, worden ze niet beschouwd als dezelfde gebruiker met dezelfde machtigingen en groepslidmaatschap in zowel de auteur- als de publicatieomgeving. De rol(en) van leden en gebruikers moet(en) afzonderlijk worden vastgesteld bij publicatie en auteur, al naargelang het geval.

Voor een [publicatielandbouwbedrijf](topologies.md), moeten de registratie en de wijzigingen die op één publicatiegeval worden aangebracht met andere publicatieinstanties worden gesynchroniseerd om hen toegang tot de zelfde gebruikersgegevens te hebben. Zie [Gebruikerssynchronisatie](sync.md), die een sectie bevat waarin wordt beschreven [wat er gebeurt als...](sync.md#what-happens-when).

### Bijdragelimieten {#contribution-limits}

Ter bescherming tegen spam is het mogelijk de frequentie van het plaatsen van inhoud door de leden te beperken. Bovendien is het mogelijk de bijdragen van nieuw geregistreerde leden automatisch te beperken.

Zie bijdragelimieten voor [leden voor meer informatie](limits.md).

### Dynamisch gemaakte gebruikersgroepen {#dynamically-created-user-groups}

Wanneer een nieuwe communautaire plaats wordt gecreeerd, worden de nieuwe gebruikersgroepen dynamisch gecreeerd met unieke identiteitskaart (uid) en toestemmingen aangewezen voor diverse administratieve functies noodzakelijk om de communautaire plaats of in het auteursmilieu (zie de Rollen [van de Groep van de](#author-group-roles)Auteur) of het publicatiemilieu (zie de Rollen [van de Groep van de](#publish-group-roles)Publish) te beheren.

De namen van de groepen worden gegenereerd op basis van de naam die de site tijdens het maken [van](sites-console.md#step13asitetemplate)gemeenschapssites krijgt. Unieke id&#39;s vermijden naamgevingsconflicten voor sites met dezelfde naam en groepen van gemeenschappen op dezelfde server.

Als de sitenaam bijvoorbeeld &quot;*engageren*&quot; was voor een site met de naam &quot;We.Retail Engage&quot;, zou een van de gemaakte gebruikersgroepen zijn:

* Community *Engineering* -leden

## Auteursomgeving {#author-environment}

### Tunnelservice {#tunnel-service}

Wanneer het gebruiken van het auteursmilieu om plaatsen [te](sites-console.md)creëren, [plaatseigenschappen](sites-console.md#modifying-site-properties) te wijzigen en communityleden en lidgroepen [te](members.md)beheren, is het noodzakelijk om tot gebruikers en gebruikersgroepen toegang te hebben die in het publicatiemilieu worden geregistreerd.

De tunneldienst verleent deze toegang gebruikend de replicatieagent op auteur.

* Voor details, zie [configuratieinstructies](deploy-communities.md#tunnel-service-on-author) op de plaatsingspagina.

De leden van de [Gemeenschappen en de Groepen consoles](members.md) zijn uitsluitend voor het beheren van gebruikers (leden) en gebruikersgroepen (lidgroepen) die slechts in het publicatiemilieu worden geregistreerd.

Om gebruikers en gebruikersgroepen te beheren die in het auteursmilieu worden geregistreerd, gebruik de console van de [Veiligheid](../../help/sites-administering/security.md)

### Auteursgroeprollen {#author-group-roles}

| Indien lid van de groep... | Primaire rol |
|---|---|
| beheerders | De groep van beheerders bestaat uit systeembeheerders die alle capaciteiten van een communautaire Beheerder evenals de capaciteit hebben om de groep van Communautaire Beheerders te beheren. |
| Communautaire administrateurs | De communautaire groep van Beheerders wordt automatisch een lid van alle communautaire plaatsen en om het even welke communautaire groepen die op de plaats worden gecreeerd. Een aanvankelijk lid van de groep van Communautaire Beheerders is de beheerdersgroep. In de auteursomgeving, kunnen de Communautaire Beheerders communautaire plaatsen tot stand brengen, plaatsen beheren, leden beheren (zij kunnen leden van de gemeenschap verbieden), en gematigde inhoud. |
| Community &lt;naam *site*> Sitecontentmanager | Met Community Site Content Manager kunt u traditionele AEM ontwerpen, inhoud maken en pagina&#39;s voor een communitysite wijzigen. |
| Community Enablement Managers | De groep van de Managers van Enablement van de Gemeenschap bestaat uit gebruikers die voor taak beschikbaar zijn om de groep van de Managers van Enablement van een communautaire plaats te beheren. |
| Community &lt;naam *site* > Siteenablementmanagers | De groep van de Managers van Enablement van de Plaats van de Gemeenschap bestaat uit gebruikers die zijn toegewezen om de [middelen](resources.md)van de plaatsing van een communautaire plaats te beheren. |
| Geen | Een anonieme sitebezoeker heeft mogelijk geen toegang tot de auteursomgeving. |

### Systeembeheerders {#system-administrators}

De leden van de beheerdersgroep zijn systeembeheerders die de aanvankelijke opstelling van een AEM installatie voor zowel de auteur als publicatiemilieu&#39;s kunnen uitvoeren.

Voor demonstratie- en ontwikkelingsdoeleinden heeft de beheerdersgroep een lid waarvan de gebruikers-id *admin* is en het wachtwoord *admin*.

Voor productieomgevingen moet de standaardbeheerdersgroep worden gewijzigd.

Volg de [beveiligingscontrolelijst](../../help/sites-administering/security-checklist.md).

## Publicatie-omgeving {#publish-environment}

### Lid worden {#becoming-a-member}

Afhankelijk van de [instellingen](sites-console.md#user-management) van de site kan een bezoeker van de site in de publicatieomgeving lid worden van de gemeenschap:

* Wanneer de site van de community privé is (gesloten):
   * Op uitnodiging
   * Op handelingen van een beheerder

* Wanneer de site van de community openbaar is (open):
   * Op zelfregistratie
   * Via sociale aanmelding bij Facebook en Twitter

>[!NOTE]
>
>Als een bezoeker van een site zich registreert als lid van één open communitysite, worden deze automatisch lid van andere open communitysites in dezelfde publicatieomgeving.


### Groeprollen publiceren {#publish-group-roles}

| Indien lid van de groep... | Primaire rol |
|---|---|
| Community &lt;naam *site*> leden | Een lid van de community is een geregistreerde gebruiker. Ze kunnen zich aanmelden, hun profiel wijzigen, deelnemen aan een open community-groep, inhoud posten naar de community, berichten verzenden naar andere leden en activiteiten op de site volgen. |
| Community &lt;naam *site*> moderatoren | Een moderator van de communautaire plaats is een vertrouwd communautair lid dat UGC of in bulk, gebruikend de moderatieconsole, of in context, op de pagina kan matigen waar de inhoud wordt gepost. |
| Community &lt;naam *site*> &lt;naam *groep*> leden | Een lid van een communautaire groep is een lid van de gemeenschap dat zich heeft aangesloten bij een open communautaire groep of is uitgenodigd voor een gesloten communautaire groep. Zij hebben de capaciteiten van een lid voor die communautaire groep binnen de plaats. |
| Community &lt;*sitenaam*> Groupbeheerders | Een beheerder van een community-sitegroep is een vertrouwd communitylid dat is toegewezen aan het maken en beheren van subgemeenschappen (groepen) binnen een communitysite. Omvat is het vermogen om in-context matiging te verstrekken. |
| *Bevoorrechte ledenbeveiligingsgroep* | Een handmatig gemaakte en onderhouden gebruikersgroep om het maken van inhoud te beperken. Zie [Geprivilegieerde ledengroep](#privileged-members-group). |
| Geen | Een anonieme sitebezoeker, die de site ontdekt, kan gemeenschapssites weergeven en doorzoeken die anonieme toegang toestaan. Om te kunnen deelnemen en inhoud te kunnen plaatsen, moet de gebruiker zich zelf registreren (indien toegestaan) en lid worden van de gemeenschap. |

### Leden toewijzen aan rollen van groepen publiceren {#assigning-members-to-publish-group-roles}

Wanneer het [creëren van een communautaire plaats](sites-console.md) in het auteursmilieu, of wanneer het [wijzigen van plaatseigenschappen,](sites-console.md#modifying-site-properties) kunnen de leden diverse rollen worden toegewezen die in het publicatiemilieu, zoals moderators, groepsbeheerders, middelcontacten, of bevoorrechte leden worden uitgevoerd.

[Als u de tunnelservice](sync.md#accessingpublishusersfromauthor) inschakelt, worden er toewijzingsopties voorgesteld door leden die publiceren in plaats van gebruikers op auteur.

De geselecteerde leden worden automatisch toegewezen aan de [desbetreffende groep](#publish-group-roles) en hun lidmaatschap wordt opgenomen wanneer de site van de community (opnieuw) wordt gepubliceerd.

### Groep met geprivilegieerde leden {#privileged-members-group}

Het doel van een bevoorrechte groep van de ledenveiligheid is de verwezenlijking van inhoud voor bepaalde communautaire functies tot een bevoorrechte ondergroep van de leden van een communautaire plaats te beperken.

De bevoorrechte ledengroep is een lidgroep die wordt gecreeerd en wordt beheerd gebruikend de console [van de Groepen van](members.md)Gemeenschappen.

Nadat een bevoorrechte ledengroep wordt gecreeerd, en met de toegelaten [](sync.md#accessingpublishusersfromauthor)tunneldienst, kan de structuur van een bestaande communautaire plaats worden [gewijzigd](sites-console.md#modify-structure) om de configuratie van zijn communautaire functies uit te geven om &quot;Geprivilegieerde Leden&quot;toe te staan en de gecreeerde groep toe te voegen.

De communautaire functies die de specificatie van een of meer bevoorrechte ledengroepen mogelijk maken, zijn:

* [Blogfunctie](functions.md#blog-function) - Het maken van nieuwe artikelen beperken.
* [Kalenderfunctie](functions.md#calendar-function) - Het maken van nieuwe gebeurtenissen beperken.
* [Functie](functions.md#forum-function) van het forum - om het creëren van nieuwe onderwerpen te beperken.
* [QnA functie](functions.md#qna-function) - Het creëren van nieuwe vragen beperken.

Wanneer een communautaire functie niet wordt beveiligd (geen bevoorrechte toegewezen lidgroep), dan kunnen alle leden van de communautaire plaats eigenschapinhoud (artikelen, gebeurtenissen, onderwerpen, vragen) tot stand brengen.

>[!NOTE]
>
>Als u een gebruiker toevoegt aan een geprivilegieerde ledengroep voor een communitysite, worden er alleen privileges toegekend aan gebruikers die ook lid zijn van dezelfde communitysite.


## Communautaire leden creëren {#creating-community-members}

### Locatie opslagplaats {#repository-location}

Bepaalde functies werken alleen correct als u gebruikers en gebruikersgroepen met de juiste rechten maakt.

Wanneer de leden binnen worden gecreeerd `/home/users/community`, erven zij juiste ACLs die gelezen voorrechten aan de profielen van leden geven.

Op dezelfde manier zouden de gebruikersgroepen van de douanegemeenschap (zoals bevoorrechte ledengroepen) in moeten worden gecreeerd `/home/groups/community`.

Als u de consoles [leden en groepen van](members.md) Gemeenschappen gebruikt, worden gebruikers en groepen in deze paden gemaakt.

Als u een aangepast pad wilt opgeven, moet u de klassieke beveiligingsinterface gebruiken. Deze kan worden geraadpleegd op [https://&lt;server>:&lt;port>/useradmin](http://localhost:4503/useradmin).

Om leesvoorrechten voor de wegen van het douanelidlid te geven, op alle publiceer instanties plaats ACLs gelijkend op `/home/users/community`:

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
| beheer | gebruikers op auteur | gebruikersgroepen bij auteur | leden die worden gepubliceerd | lidgroepen die worden gepubliceerd |
| vereist | machtiging beheerder | machtiging beheerder | beheerdersrechten, tunnelservice, gebruikerssynchronisatie voor publicatiefarm | beheerdersrechten, tunnelservice, gebruikerssynchronisatie voor publicatiefarm |

### Rol van Community Enablement Manager {#community-enablement-manager-role}

De mogelijkheid voor een bezoeker van een site om zich te registreren is doorgaans niet toegestaan voor een [activeringscommunity](overview.md#enablement-community) omdat er kosten aan elk lid zijn verbonden. Studenten en bronnen van Enablement worden beheerd door een gebruiker waaraan de [rol](#author-group-roles) van gebruiker is toegewezen `enablement manager` tijdens het maken [van de site op de auteur (toegevoegd als lid van de groep](sites-console.md#enablement) `Community <site-name> Siteenablementmanagers`). Het `enablement manager` is ook verantwoordelijk voor het [toewijzen van leermiddelen](resources.md) aan leden van de gemeenschap aan auteur.

Alleen gebruikers die lid zijn van de algemene `Community Enablement Managers` groep kunnen worden geselecteerd als een `enablement manager` specifieke community-site.

Om een gebruiker te creëren die de rol van kan worden toegewezen, gebruik de klassieke UI veiligheidsconsole om de weg te specificeren: `Community Site Enablement Manager`

Op een instantie van de auteur:

1. Aangemeld met beheerdersrechten, surf naar de klassieke UI-beveiligingsconsole.

   Bijvoorbeeld: [http://localhost:4502/useradmin](http://localhost:4502/useradmin)

2. From the Edit menu, select **[!UICONTROL Create User]**.
3. Vul het `Create User` dialoogvenster in.
   * Pad moet `/home/users/community`zijn.
4. Selecteer **[!UICONTROL Create]**.

   ![create-community-user](assets/create-community-user.png)

* Zoek in het linkerdeelvenster naar de nieuwe gebruiker en selecteer deze in het rechterdeelvenster.

   ![community-user](assets/view-community-user.png)

In het linkervenster:

1. Wis het zoekvak en selecteer **[!UICONTROL Hide Users]**.
2. Zoek en sleep `community-enablementmanagers` naar het **[!UICONTROL Groups]** tabblad van de nieuwe gebruiker in het rechterdeelvenster.

   ![assign-group](assets/assign-group.png)

### Rol van communautaire administrateurs {#community-administrators-role}

Zoals vermeld in het diagram Rollen [van de Groep van de](#author-group-roles) Auteur, kunnen de leden van de groep van Beheerders Community plaatsen tot stand brengen, plaatsen beheren, leden beheren (zij kunnen leden van de gemeenschap), en gematigde inhoud verbieden.

Voer dezelfde stappen uit als het maken en toewijzen van een gebruiker aan de rol van [enablement Manager](#communitysiteenablementmanagerrole), maar voeg een c- `ommunity-administrators` groep toe onder het tabblad Groepen van de gebruiker.

### LDAP-integratie {#ldap-integration}

AEM ondersteunt het gebruik van LDAP voor verificatie van gebruikers en het maken van gebruikersaccounts. Dit wordt gedetailleerd beschreven in [LDAP configureren met AEM 6](../../help/sites-administering/ldap-config.md).

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

Dit leidt ertoe dat gebruikers automatisch worden toegewezen aan de groep leden van de site van de community en dat de locatie van de opslagplaats wordt `/home/users/community` en `/home/groups/community`, zodat ze de juiste machtigingen overnemen om elkaars profiel te zien.

* De `User auto membership` waarde moet de `rep:authorizableId` eigenschap zijn en niet de `givenName` (weergavenaam) uit het profiel.

## Gebruikers synchroniseren tussen AEM instanties {#synchronizing-users-among-aem-instances}

Wanneer het gebruiken van [publiceer landbouwbedrijf](topologies.md), zorg ervoor de gebruikers de zelfde weg op elke publicatieinstantie hebben door de gebruikers eerst aan één instantie in te voeren en [toelatend gebruikerssynchronisatie](sync.md) aan Sling te verdelen de gebruikers aan andere publicatieinstanties.

Als u gebruikersgroepen importeert, om ervoor te zorgen dat de gebruikersgroepen op elke publicatie-instantie hetzelfde pad hebben, importeert u naar één instantie en [maakt u vervolgens een pakket](../../help/sites-administering/package-manager.md#creating-a-new-package) voor export en installeert u dat pakket op alle andere publicatie-instanties.

Hoewel het synchroniseren van gebruikersgroepen via gebruikerssynchronisatie in een toekomstige release wordt opgenomen, wordt momenteel alleen het *lidmaatschap* van een gebruikersgroep gesynchroniseerd wanneer gebruikerssynchronisatie wordt uitgevoerd.

## Informatie over communautaire groepen {#about-community-groups}

Wanneer het bespreken van groepen, zijn er twee verschillende onderwerpen:

* **[Communautaire groepen](overview.md#communitygroups)**

   Communautaire groepen zijn de subgemeenschappen die kunnen worden gecreëerd in de publicatieomgeving voor een communautaire site die de oprichting van groepen van gemeenschappen ondersteunt. Als u een community maakt, worden er meer pagina&#39;s toegevoegd aan de website en worden deze beheerd op een manier die vergelijkbaar is met de bovenliggende community-site. Ga voor meer informatie naar [Community Group Essentials](essentials-groups.md) for developers en [Community Group](creating-groups.md) for authors.

* **[Leden](../../help/sites-administering/security.md)**

   De groepen van de leden zijn de groepen waartot de leden kunnen behoren en door de console van Groepen worden geleid. Een groot deel van de discussie over deze pagina is gewijd aan de leden van de fracties. De automatisch voor een communautaire site opgerichte ledengroepen, die vooraf zijn vastgesteld, *`Community`* kunnen als een communautaire groep worden aangeduid; daarom moet de context van de discussie in overweging worden genomen.
