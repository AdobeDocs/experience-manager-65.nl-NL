---
title: Eerste instelling
seo-title: Eerste instelling
description: Oprichting van Gemeenschappen
seo-description: Oprichting van Gemeenschappen
uuid: c53d280c-c5ae-47cf-8038-f0dea68e15ff
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: introduction
content-type: reference
discoiquuid: 0d462ad1-5619-4bb6-9609-bc8987c40a0c
translation-type: tm+mt
source-git-commit: 6ab91667ad668abf80ccf1710966169b3a187928
workflow-type: tm+mt
source-wordcount: '678'
ht-degree: 0%

---


# Eerste instelling {#initial-setup}

## Auteur- en publicatie-instanties starten {#start-author-and-publish-instances}

Voor ontwikkelings- en demonstratiedoeleinden is het nodig één auteur en één publicatieexemplaar uit te voeren.

Hiervoor volgt u de AEM [Aan de slag](../../help/sites-deploying/deploy.md#getting-started) -instructies, die resulteren in:

* Authoromgeving op [localhost:4502](http://localhost:4502/)
* Publicatie-omgeving op [localhost:4503](http://localhost:4503/)

Voor AEM Communities:

* De auteursomgeving is voor:

   * Ontwikkeling van sites, sjablonen en componenten.
   * Administratieve en configuratietaken.

* De publicatieomgeving is bedoeld voor:

   * De ervaring van de gemeenschap met het plaatsen en moderniseren van inhoud.
   * Creëren van groepen van gemeenschappen, leden en leden.

>[!NOTE]
>
>Als u niet bekend bent met AEM, bekijkt u de documentatie over [basisverwerking](../../help/sites-authoring/basic-handling.md) en een [handleiding voor het ontwerpen van pagina](../../help/sites-authoring/qg-page-authoring.md)&#39;s.


## Laatste versie van Gemeenschappen installeren {#install-latest-communities-release}

Deze zelfstudie maakt een [betrokkenheidscommunity-site](overview.md#engagement-community) en is gebaseerd op AEM Communities 6.2-functiepakket versie 1.10.

Ga voor de installatie van het nieuwste functiepakket naar:

* [Laatste releases](deploy-communities.md#latest-releases)

Voor een zelfstudie waarmee een community-site [voor](overview.md#enablement-community)activering wordt gemaakt, gaat u naar [Aan de slag met AEM Communities for Enablement](getting-started-enablement.md).

## Analyses configureren {#configure-analytics}

Wanneer [Adobe Analytics voor de communautaire plaats](analytics.md)wordt gevormd, is de informatie over communautaire activiteit beschikbaar die de ervaring van het communautaire lid verbetert evenals terugkoppelt aan beheerders van de plaats verstrekt.

Integratie met Adobe Analytics is optioneel.

## E-mail voor meldingen configureren {#configure-email-for-notifications}

De functie voor meldingen, die standaard beschikbaar is voor alle sites die met de `Communities Sites` console zijn gemaakt, biedt een e-mailkanaal voor meldingen.

Het is nodig dat e-mail correct is geconfigureerd voor de site.

Zie E-mail [configureren](email.md).

## De tunnelservice inschakelen {#enable-the-tunnel-service}

Wanneer het creëren van een communautaire plaats in het auteursmilieu, maakt de tunneldienst de capaciteit mogelijk om rollen aan vertrouwde op communautaire leden toe te wijzen die in het publicatiemilieu worden geregistreerd. De tunneldienst verleent ook toegang tot communautaire leden van de [Leden en Groepen consoles](members.md) in het auteursmilieu.

De conventie is dat leden en ledengroepen die in de publicatieomgeving zijn gemaakt, *niet* opnieuw worden gemaakt in de ontwerpomgeving. Zie Gebruikers en gebruikersgroepen [](users.md)beheren voor meer informatie.

Voor eenvoudige instructies om de tunneldienst op een **auteursinstantie** toe te laten, zie de Dienst [van de](deploy-communities.md#tunnel-service-on-author)Tunnel.

## Rol van communautaire beheerder {#community-administrator-role}

De leden van de groep van Beheerders van de Gemeenschap kunnen communautaire plaatsen tot stand brengen, plaatsen beheren, leden beheren (zij kunnen leden van de gemeenschap verbieden), en gematigde inhoud.

### Gebruiker maken {#create-user}

Maak een gebruiker op de *auteur* die de rol van communautaire beheerder krijgt toegewezen:

* Instantie van auteur

   * Bijvoorbeeld: [http://localhost:4502/](http://localhost:4503/)

* Aanmelden met beheerdersrechten

   * Bijvoorbeeld gebruikersnaam &#39;admin&#39; / wachtwoord &#39;admin&#39;

* Navigeer vanuit de hoofdconsole naar **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Security]** > **[!UICONTROL Users]**.
* Selecteer in het menu **Bewerken **de optie **[!UICONTROL Add User]**

* In the `Create New User` dialog enter:

   * **[!UICONTROL ID]**: sirius
   * **[!UICONTROL Emai Address]**: sirius.nilson@mailinator.com
   * **[!UICONTROL Password]**: password
   * **[!UICONTROL Confirm Password&ast;]**: password
   * **[!UICONTROL First Name]**: Sirius
   * **[!UICONTROL Last Name]**: Nilson

### Sirius toewijzen aan de groep met communautaire beheerders {#assign-sirius-to-community-administrators-group}

Omlaag schuiven naar `Add User to Groups`:

* Voer C in om te zoeken

   * Selecteer `Community Administrators`
   * Selecteer `Community Enablement Managers`

* Selecteer **[!UICONTROL Save]**.

![aanmaken-gebruiker](assets/create-user.png)

## Sociale aanmelding inschakelen {#enable-social-login}

Voordat de demonstratieversies van sociale aanmelding bij Facebook en Twitter kunnen worden gebruikt, is het noodzakelijk

1. Installeer een reparatiepakket of een [nieuwste functiepakket](deploy-communities.md#latestfeaturepack) (voor wijzigingen in de Facebook-API van maart 2017).
1. [Schakel de OAuth-provider](social-login.md#adobe-granite-oauth-authentication-handler) in de publicatieomgeving in.

Voor productieservers is het nodig de cloudservices te maken die nodig zijn voor het aanbieden van sociale aanmeldingsgegevens.

Zie [Sociale aanmelding bij Facebook en Twitter](social-login.md).

## Zelfstudietags maken {#create-tutorial-tags}

Maak tags voor de zelfstudies voor toegang en activering met behulp van de naamruimte tag van `Tutorial`.

Met de [tagconsole](../../help/sites-administering/tags.md#tagging-console) kunt u de volgende tags maken:

* `Tutorial: Sports / Baseball`
* `Tutorial: Sports / Gymnastics`
* `Tutorial: Sports / Skiing`
* `Tutorial: Arts / Visual`
* `Tutorial: Arts / Auditory`
* `Tutorial: Arts / History`

![zelfstudielabels](assets/tutorial-tags.png)

Volg vervolgens de instructies op:

1. [Stel de tagmachtigingen](../../help/sites-administering/tags.md#setting-tag-permissions)in.
1. [Publiceer de labels](../../help/sites-administering/tags.md#publishing-tags).

Voorbeeld van pakket met tags die zijn gemaakt voor de Tutorials Aan de slag van AEM Communities

[Bestand ophalen](assets/tutorial_tags-v63.zip)

## MongoDB voor UGC Common Store {#mongodb-for-ugc-common-store}

Het wordt geadviseerd, maar facultatief, om [MSRP](msrp.md) (MongoDB) als [gemeenschappelijke opslag](working-with-srp.md) te plaatsen om de flexibiliteit te ervaren om al UGC van of publiceren en/of auteursmilieu&#39;s te modereren.

Voor instructies gaat u naar [Hoe te MongoDB instellen voor demo](demo-mongo.md).

Door gebrek, resulteert de installatie van de auteur en publiceert AEM instanties in gebruiker geproduceerde inhoud (UGC) die in de opslag [van Tar](../../help/sites-deploying/platform.md) JCR wordt opgeslagen die gebruikend [JSRP](jsrp.md)wordt betreden. JSRP is geen gemeenschappelijke opslag, wat betekent UGC slechts op de instantie zichtbaar is waarop het was ingegaan. Normaal, is UGC ingegaan op een publiceer instantie en zou niet zichtbaar in het auteursmilieu zijn, resulterend in alle matigingstaken die de publiceer instantie moeten gebruiken.