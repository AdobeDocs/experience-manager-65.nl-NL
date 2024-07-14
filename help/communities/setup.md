---
title: Eerste instelling
description: Leer hoe u eerst Adobe Experience Manager Communities instelt.
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: introduction
content-type: reference
exl-id: 6bda0f09-7ae5-4540-b035-9dd249ac3186
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '666'
ht-degree: 0%

---

# Eerste instelling {#initial-setup}

## Auteur- en Publish-instanties starten {#start-author-and-publish-instances}

Voor ontwikkelings- en demonstratiedoeleinden is het nodig één auteur en één publicatie-instantie uit te voeren.

Om dit te doen, volg de basisAdobe Experience Manager (AEM) [ Begonnen ](../../help/sites-deploying/deploy.md#getting-started) instructies, die in het volgende resulteren:

* Het milieu van de auteur op [ localhost:4502 ](http://localhost:4502/)
* Het milieu van Publish op [ localhost:4503 ](http://localhost:4503/)

Voor AEM Communities:

* De auteur-omgeving is bedoeld voor:

   * Ontwikkeling van sites, sjablonen en componenten.
   * Administratieve en configuratietaken.

* De Publish-omgeving is bedoeld voor:

   * De ervaring van de gemeenschap met het plaatsen en moderniseren van inhoud.
   * Creëren van groepen van gemeenschappen, leden en leden.

>[!NOTE]
>
>Als niet vertrouwd met AEM, bekijk de documentatie over [ basisbehandeling ](../../help/sites-authoring/basic-handling.md) en a [ snelle gids aan auteurspagina&#39;s ](../../help/sites-authoring/qg-page-authoring.md).

## Laatste versie van Gemeenschappen installeren {#install-latest-communities-release}

Dit leerprogramma leidt tot een [ plaats van de betrokkenheidsgemeenschap ](overview.md#engagement-community) en is gebaseerd op AEM Communities 6.2 versie van het eigenschapspak 1.10.

Ga voor de installatie van het nieuwste functiepakket naar:

* [Laatste releases](deploy-communities.md#latest-releases)

## Analyses configureren {#configure-analytics}

Wanneer [ Adobe Analytics voor de communautaire plaats ](analytics.md) wordt gevormd, is de informatie over communautaire activiteit beschikbaar die de ervaring van het communautaire lid verbetert en aan beheerders van de plaats terugkoppelt verstrekt.

Integratie met Adobe Analytics is optioneel.

## E-mail voor meldingen configureren {#configure-email-for-notifications}

De functie voor meldingen, die standaard beschikbaar is voor alle sites die zijn gemaakt met de `Communities Sites` -console, biedt een e-mailkanaal voor meldingen.

Het is nodig dat e-mail correct is geconfigureerd voor de site.

Zie [ Vormend E-mail ](email.md).

## De tunnelservice inschakelen {#enable-the-tunnel-service}

Wanneer het creëren van een communautaire plaats in het milieu van de Auteur, maakt de tunneldienst de capaciteit mogelijk om rollen aan vertrouwde op communautaire leden toe te wijzen die in het milieu van Publish worden geregistreerd. De tunneldienst verleent ook toegang tot communautaire leden van de [ leden en Groepen consoles ](members.md) in het auteursmilieu.

De conventie is voor leden en lidgroepen die in het milieu van Publish worden gecreeerd ** niet worden ontspannen in het auteursmilieu. Voor meer informatie, zie [ het Leiden Gebruikers en de Groepen van de Gebruiker ](users.md).

Voor eenvoudige instructies om de tunneldienst op een **instantie van de Auteur** toe te laten, zie [ Dienst van de Tunnel ](deploy-communities.md#tunnel-service-on-author).

## Rol van communautaire beheerder {#community-administrator-role}

De leden van de groep van Beheerders van de Gemeenschap kunnen communautaire plaatsen tot stand brengen, plaatsen beheren, leden beheren (zij kunnen leden van de gemeenschap verbieden), en gematigde inhoud.

### Gebruiker maken {#create-user}

Creeer een gebruiker op *auteur*, die de rol van Communautaire Beheerder wordt toegewezen:

* Instantie van auteur

   * Bijvoorbeeld, [ http://localhost:4502/](http://localhost:4503/)

* Aanmelden met beheerdersrechten

   * Bijvoorbeeld gebruikersnaam &#39;admin&#39; / wachtwoord &#39;admin&#39;

* Navigeer vanuit de hoofdconsole naar **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Security]** > **[!UICONTROL Users]** .
* Van **geef** menu uit, uitgezocht **[!UICONTROL Add User]**

* In het dialoogvenster `Create New User` voert u het volgende in:

   * **[!UICONTROL ID]**: sirius
   * **[!UICONTROL Email Address]**: sirius.nilson@mailinator.com
   * **[!UICONTROL Password]**: wachtwoord
   * **[!UICONTROL Confirm Password&ast;]**: wachtwoord
   * **[!UICONTROL First Name]**: Sirius
   * **[!UICONTROL Last Name]**: Nilson

### Sirius toewijzen aan de groep met communautaire beheerders {#assign-sirius-to-community-administrators-group}

Omlaag schuiven naar `Add User to Groups` :

* Voer C in om te zoeken

   * Selecteren `Community Administrators`
   * Selecteren `Community Enablement Managers`

* Selecteer **[!UICONTROL Save]** .

![ creeer-gebruiker ](assets/create-user.png)

## Sociale aanmelding inschakelen {#enable-social-login}

Voordat de demonstratieversies van de aanmelding bij Facebook en de Twitter kunnen worden gebruikt, moet

1. Installeer een fixpak of [ recentste eigenschappak ](deploy-communities.md#latestfeaturepack) (voor Maart 2017 verandert Facebook API).
1. [ laat de leverancier OAuth ](social-login.md#adobe-granite-oauth-authentication-handler) in toe publiceert milieu.

Voor productieservers is het nodig de cloudservices te maken die nodig zijn voor het aanbieden van sociale aanmeldingsgegevens.

Zie [ Sociale Login met Facebook en Twitter ](social-login.md).

## Zelfstudietags maken {#create-tutorial-tags}

Maak tags, zodat u deze kunt gebruiken voor zelfstudies voor deelname met behulp van de naamruimte van tags van `Tutorial` .

Gebruik de [ Tagingconsole ](../../help/sites-administering/tags.md#tagging-console) om de volgende markeringen tot stand te brengen:

* `Tutorial: Sports / Baseball`
* `Tutorial: Sports / Gymnastics`
* `Tutorial: Sports / Skiing`
* `Tutorial: Arts / Visual`
* `Tutorial: Arts / Auditory`
* `Tutorial: Arts / History`

![ zelfstudie-markeringen ](assets/tutorial-tags.png)

Volg vervolgens de instructies op:

1. [ plaats de markeringstoestemmingen ](../../help/sites-administering/tags.md#setting-tag-permissions).
1. [ Publish de markeringen ](../../help/sites-administering/tags.md#publishing-tags).

Voorbeeldpakket met tags gemaakt voor de Tutorials Aan de slag van AEM Communities

[Bestand ophalen](assets/tutorial_tags-v63.zip)

## MongoDB voor UGC Common Store {#mongodb-for-ugc-common-store}

Het wordt geadviseerd, maar facultatief, om [ MSRP ](msrp.md) (MongoDB) als [ gemeenschappelijke opslag ](working-with-srp.md) te plaatsen om de flexibiliteit te ervaren om al UGC van of publiceren en/of auteursmilieu&#39;s te matigen.

Voor instructies bezoek [ hoe te Opstelling MongoDB voor Manifestatie ](demo-mongo.md).

Door gebrek, resulteert de installatie van de auteur en publiceert AEM instanties in gebruiker geproduceerde inhoud (UGC) die in ](../../help/sites-deploying/platform.md) wordt opgeslagen de opslag van de Tar van 0} JCR {die gebruikend [ JSRP ](jsrp.md) wordt betreden. [ JSRP is geen gemeenschappelijke opslag, wat betekent UGC slechts op de instantie zichtbaar is waarop het was ingegaan. Normaal, is UGC ingegaan op een publicatie instantie en zou niet zichtbaar in het auteursmilieu zijn, resulterend in alle matigingstaken die de publicatieinstantie moeten gebruiken.
