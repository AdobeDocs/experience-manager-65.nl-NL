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

## Auteur- en publicatie-instanties starten {#start-author-and-publish-instances}

Voor ontwikkelings- en demonstratiedoeleinden is het nodig één auteur en één publicatie-instantie uit te voeren.

Volg hiervoor de basis-Adobe Experience Manager (AEM) [Aan de slag](../../help/sites-deploying/deploy.md#getting-started) instructies die het volgende opleveren:

* Auteursomgeving op [localhost:4502](http://localhost:4502/)
* Publicatie-omgeving op [localhost:4503](http://localhost:4503/)

Voor AEM Communities:

* De auteur-omgeving is bedoeld voor:

   * Ontwikkeling van sites, sjablonen en componenten.
   * Administratieve en configuratietaken.

* De publicatie-omgeving is bedoeld voor:

   * De ervaring van de gemeenschap met het plaatsen en moderniseren van inhoud.
   * Creëren van groepen van gemeenschappen, leden en leden.

>[!NOTE]
>
>Als u niet bekend bent met AEM, kunt u de documentatie raadplegen op [basisbehandeling](../../help/sites-authoring/basic-handling.md) en [snelle handleiding voor het ontwerpen van pagina&#39;s](../../help/sites-authoring/qg-page-authoring.md).

## Laatste versie van Gemeenschappen installeren {#install-latest-communities-release}

Deze zelfstudie maakt een [community-site voor betrokkenheid](overview.md#engagement-community) en is gebaseerd op AEM Communities 6.2 feature pack versie 1.10.

Ga voor de installatie van het nieuwste functiepakket naar:

* [Laatste releases](deploy-communities.md#latest-releases)

## Analyses configureren {#configure-analytics}

Wanneer [Adobe Analytics is geconfigureerd voor de communitysite](analytics.md)Er is informatie beschikbaar over de activiteiten van de community die de ervaring van het lid van de community vergroot en feedback geeft aan beheerders van de site.

Integratie met Adobe Analytics is optioneel.

## E-mail voor meldingen configureren {#configure-email-for-notifications}

De functie voor meldingen is standaard beschikbaar voor alle sites die zijn gemaakt met de `Communities Sites` -console, biedt een e-mailkanaal voor meldingen.

Het is nodig dat e-mail correct is geconfigureerd voor de site.

Zie [E-mail configureren](email.md).

## De tunnelservice inschakelen {#enable-the-tunnel-service}

Wanneer het creëren van een communautaire plaats in het milieu van de Auteur, maakt de tunneldienst de capaciteit mogelijk om rollen aan vertrouwde op communautaire leden toe te wijzen die in het Publish milieu worden geregistreerd. De tunneldienst verleent ook toegang aan leden van de gemeenschap van de [Samenstellingen van leden en groepen](members.md) in de ontwerpomgeving.

De conventie is voor leden en ledengroepen die in de publicatieomgeving zijn gemaakt, *niet* opnieuw worden gemaakt in de auteursomgeving. Zie voor meer informatie [Gebruikers en gebruikersgroepen beheren](users.md).

Voor eenvoudige instructies om de tunneldienst op een **Auteur** -instantie, zie [Tunnelservice](deploy-communities.md#tunnel-service-on-author).

## Rol van communautaire beheerder {#community-administrator-role}

De leden van de groep van Beheerders van de Gemeenschap kunnen communautaire plaatsen tot stand brengen, plaatsen beheren, leden beheren (zij kunnen leden van de gemeenschap verbieden), en gematigde inhoud.

### Gebruiker maken {#create-user}

Een gebruiker maken op *auteur*, die de rol van communautaire administrateur krijgt toegewezen:

* Instantie van auteur

   * Bijvoorbeeld: [http://localhost:4502/](http://localhost:4503/)

* Aanmelden met beheerdersrechten

   * Bijvoorbeeld gebruikersnaam &#39;admin&#39; / wachtwoord &#39;admin&#39;

* Navigeer vanuit de hoofdconsole naar **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Security]** > **[!UICONTROL Users]**.
* Van de **Bewerken** menu, selecteert u **[!UICONTROL Add User]**

* In de `Create New User` dialoogvenster openen:

   * **[!UICONTROL ID]**: sirius
   * **[!UICONTROL Email Address]**: sirius.nilson@mailinator.com
   * **[!UICONTROL Password]**: password
   * **[!UICONTROL Confirm Password&ast;]**: password
   * **[!UICONTROL First Name]**: Sirius
   * **[!UICONTROL Last Name]**: Nilson

### Sirius toewijzen aan de groep met communautaire beheerders {#assign-sirius-to-community-administrators-group}

Omlaag schuiven naar `Add User to Groups`:

* Voer C in om te zoeken

   * Selecteren `Community Administrators`
   * Selecteren `Community Enablement Managers`

* Selecteren **[!UICONTROL Save]**.

![aanmaken](assets/create-user.png)

## Sociale aanmelding inschakelen {#enable-social-login}

Voordat de demonstratieversies van de aanmelding bij Facebook en de Twitter kunnen worden gebruikt, moet

1. Installeer een fixpack of [nieuwste functiepakket](deploy-communities.md#latestfeaturepack) (voor wijzigingen in de Facebook API van maart 2017).
1. [De OAuth-provider inschakelen](social-login.md#adobe-granite-oauth-authentication-handler) in de publicatieomgeving.

Voor productieservers is het nodig de cloudservices te maken die nodig zijn voor het aanbieden van sociale aanmeldingsgegevens.

Zie [Sociale aanmelding met Facebook en Twitter](social-login.md).

## Zelfstudietags maken {#create-tutorial-tags}

Tags maken, zodat u deze kunt gebruiken voor zelfstudies voor deelname met behulp van de naamruimte tag van `Tutorial`.

Gebruik de [Tagingconsole](../../help/sites-administering/tags.md#tagging-console) om de volgende labels te maken:

* `Tutorial: Sports / Baseball`
* `Tutorial: Sports / Gymnastics`
* `Tutorial: Sports / Skiing`
* `Tutorial: Arts / Visual`
* `Tutorial: Arts / Auditory`
* `Tutorial: Arts / History`

![zelfstudielabels](assets/tutorial-tags.png)

Volg vervolgens de instructies op:

1. [Tagmachtigingen instellen](../../help/sites-administering/tags.md#setting-tag-permissions).
1. [De labels publiceren](../../help/sites-administering/tags.md#publishing-tags).

Voorbeeldpakket met tags gemaakt voor de Tutorials Aan de slag van AEM Communities

[Bestand ophalen](assets/tutorial_tags-v63.zip)

## MongoDB voor UGC Common Store {#mongodb-for-ugc-common-store}

U kunt het beste, maar optioneel, instellen [MSRP](msrp.md) (MongoDB) [gemeenschappelijk archief](working-with-srp.md) om de flexibiliteit te ervaren van het moderniseren van al UGC van of publiceren en/of auteursmilieu&#39;s.

Voor instructies gaat u naar [MongoDB voor demo instellen](demo-mongo.md).

Standaard wordt door de installatie van de auteur en de publicatie AEM instanties door de gebruiker gegenereerde inhoud (UGC) opgeslagen in [JCR Tar-opslag](../../help/sites-deploying/platform.md) die toegankelijk zijn via [JSRP](jsrp.md). JSRP is geen gemeenschappelijke opslag, wat betekent UGC slechts op de instantie zichtbaar is waarop het was ingegaan. Normaal, is UGC ingegaan op een publicatie instantie en zou niet zichtbaar in het auteursmilieu zijn, resulterend in alle matigingstaken die de publicatieinstantie moeten gebruiken.
