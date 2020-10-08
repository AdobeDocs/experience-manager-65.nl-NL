---
title: Eerste instelling voor inschakelen
seo-title: Eerste instelling
description: Eerste instelling voor inschakelen
seo-description: Eerste instelling voor inschakelen
uuid: 873ec41d-c088-41d9-a535-de5300661de6
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: introduction
content-type: reference
discoiquuid: f2ac3d66-cc79-498f-83fb-dd96feb88de2
translation-type: tm+mt
source-git-commit: f375b40c084ee363757b78c602091f38524b8b03
workflow-type: tm+mt
source-wordcount: '857'
ht-degree: 0%

---


# Eerste instelling voor inschakelen  {#initial-setup-for-enablement}

## Auteur- en publicatie-instanties starten {#start-author-and-publish-instances}

Voor ontwikkelings- en demonstratiedoeleinden is het nodig één auteur en één publicatieexemplaar uit te voeren.

Volg de standaard AEM [Aan de slag](../../help/sites-deploying/deploy.md#getting-started) instructies die resulteren in

* Authoromgeving op [localhost:4502](http://localhost:4502/)
* Publicatie-omgeving op [localhost:4503](http://localhost:4503/)

Voor AEM Communities:

* De auteursomgeving is voor:

   * De ontwikkeling van plaatsen, malplaatjes, componenten, enablement middelen en het leren wegen.
   * Toewijzing van leden en groepen leden aan activering van bronnen en leerpaden.
   * Rapporten genereren over toewijzingen, weergaven en posten.
   * Administratieve en configuratietaken.

* De publicatieomgeving is bedoeld voor:

   * Leren/training op basis van onderwerpen die worden beheerd door de Enablement Manager.
   * Opmerkingen en beoordelingsmogelijkheden en leerpaden.
   * Het krijgen van contact met de middelcontacten.

>[!NOTE]
>
>Als u niet bekend bent met AEM, bekijkt u de documentatie over [basisverwerking](../../help/sites-authoring/basic-handling.md) en een [handleiding voor het ontwerpen van pagina](../../help/sites-authoring/qg-page-authoring.md)&#39;s.

## Laatste versie van Gemeenschappen installeren {#install-latest-communities-release}

Deze zelfstudie maakt een [community-site](overview.md#enablement-community)voor activering. Ga voor de installatie van het nieuwste functiepakket naar:

* [Laatste releases](deploy-communities.md#latest-releases)

Ga naar [Aan de slag met AEM Communities](overview.md#engagement-community)voor een zelfstudie waarmee een community-site [voor](getting-started.md)betrokkenheid wordt gemaakt.

## Functies van Enablement configureren {#configure-enablement-features}

Om deze zelfstudie te volgen, is het nodig om enablement [correct te installeren en](enablement.md)te vormen, die derdeproducten, zoals MySQL en Mopeg vereist.

## Analyses configureren {#configure-analytics}

Wanneer [Adobe Analytics voor de communautaire plaats](analytics.md)wordt gevormd, is meer informatie beschikbaar in de [rapporten](reports.md) die over de middelen van het toelaten en leerwegen worden geproduceerd die aan communautaire leden (studenten) worden toegewezen.

## E-mail voor meldingen configureren {#configure-email-for-notifications}

De functie voor meldingen, die standaard beschikbaar is voor alle sites die met de `Communities Sites` console zijn gemaakt, biedt een e-mailkanaal voor meldingen.

Het is nodig dat e-mail correct is geconfigureerd voor de site.

Zie E-mail [configureren](email.md).

## De tunnelservice inschakelen {#enable-the-tunnel-service}

Wanneer het creëren van een communautaire plaats in het auteursmilieu, maakt de tunneldienst de capaciteit mogelijk om gebruikers en gebruikersgroepen tot stand te brengen en te beheren die in het publicatiemilieu (leden) worden geregistreerd, rollen aan vertrouwde op communautaire leden toe te wijzen, en inhoud aan studenten toe te wijzen.

Zie Gebruikers en gebruikersgroepen [](users.md)beheren voor meer informatie.

Voor eenvoudige instructies om de tunneldienst toe te laten, zie de Dienst van de [Tunnel](deploy-communities.md#tunnel-service-on-author).

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

1. [Tagmachtigingen instellen](../../help/sites-administering/tags.md#setting-tag-permissions)
1. [De labels publiceren](../../help/sites-administering/tags.md#publishing-tags)

Voorbeeld van pakket met tags die zijn gemaakt voor de Tutorials Aan de slag van AEM Communities

[Bestand ophalen](assets/communities_tutorialtags-10.zip)

## Leden en groepen inschakelen maken {#create-enablement-members-and-groups}

Voor een community-site voor activering mogen bezoekers van de site zich niet [zelf registreren of aanmelden](sites-console.md#user-management)via een sociaal netwerk gebruiken.

In plaats daarvan, met de toegelaten [tunneldienst](#enable-the-tunnel-service) , wordt de console [van](members.md) Leden gebruikt om nieuwe leden in het publicatiemilieu te registreren.

In deze zelfstudie worden drie leden gemaakt in de publicatieomgeving. Twee leden zullen lid van een gebruikersgroep worden die aan een het leren weg wordt toegewezen, terwijl het derde lid een contactpunt van het enablement middel wordt.

Een vierde gebruiker wordt gecreeerd in het auteursmilieu en toegewezen de rollen van de Beheerder van de Gemeenschappen en Communautaire Manager van Enablement.

>[!NOTE]
>
>Deze leden worden gemaakt voordat de website van de *zelfstudie* Enablement wordt gemaakt.
>
>Als ze later zijn gemaakt, kunnen ze tijdens het maken van leden worden toegevoegd als leden van de groep ** leden van de zelfstudie voor Enablement.
>
>In plaats daarvan, later, zullen zij aan de lidgroep [worden](enablement-create-site.md#assignuserstocommunityenablemembersgroup)toegewezen.

### Riley Taylor - Ingeschreven {#riley-taylor-enrollee}

[Creeer een lid](members.md#create-new-member) die aan een groep Leerlingen - de Gemeenschap Ski Klasse zal worden toegevoegd.

* **ID**: riley
* **E-mail**: riley.taylor@mailinator.com
* **Wachtwoord**: password
* **Wachtwoord** bevestigen: password
* **Voornaam**: Riley
* **Achternaam**: Taylor

### Sidney Croft - Ingeschreven {#sidney-croft-enrollee}

[Maak een tweede lid](members.md#create-new-member) dat wordt toegevoegd aan de groep SKI van de Gemeenschap.

* **ID**: sidney
* **E-mail**: sidney.croft@mailinator.com
* **Wachtwoord**: password
* **Wachtwoord** bevestigen: password
* **Voornaam**: Sidney
* **Achternaam**: Uitsnijden

### Quinn Harper - Enablement Resource Contact and Moderator {#quinn-harper-enablement-resource-contact-and-moderator}

[Maak een lid](members.md#create-new-member) dat wordt toegevoegd aan de lidgroep van de Community Site nadat de site is gemaakt. Dit lidmaatschap zal het lid toestaan om als het contact [van het](resources.md#settings) Middel van enablement worden toegewezen wanneer een enablement middel voor de plaats wordt gecreeerd.

* **ID**: quin
* **E-mail**: quinn.harper@mailinator.com
* **Wachtwoord**: password
* **Wachtwoord** bevestigen: password
* **Voornaam**: Quinn
* **Achternaam**: Harper

### Gebruikersgroep toevoegen - Klasse SKI voor community {#add-a-user-group-community-ski-class}

[Voeg een nieuwe groep](members.md#create-new-group) toe genoemd de Klasse van SKI Gemeenschap.

* **ID**: community-ski-klasse
* **Naam**: Community Ski-klasse
* **Omschrijving**: een steekproefgroep voor het toewijzen van enablement middelen
* **Leden toevoegen aan groep** &#39;toevoegen&#39;:

   * riley
   * sidney

* Selecteer **[!UICONTROL Save]**

### Eigenschappen van de communautaire klasse Ski {#community-ski-class-properties}

![ski-klasse-eigenschappen](assets/ski-class-properties.png)

>[!NOTE]
>
>Tijdens het creëren van de communautaire plaats, kunnen de bestaande leden en de groepen aan de groep van leden van de communautaire plaats worden toegevoegd.

## Rol van communautaire beheerder {#community-administrator-role}

De leden van de groep van Beheerders van de Gemeenschap kunnen communautaire plaatsen tot stand brengen, plaatsen beheren, leden beheren (zij kunnen leden van de gemeenschap verbieden), en gematigde inhoud.

### Gebruiker maken {#create-user}

Maak een gebruiker op de *auteur* die de rol van communautaire beheerder krijgt toegewezen:

* Instantie van auteur

   * Bijvoorbeeld: [http://localhost:4502/](http://localhost:4503/)

* Aanmelden met beheerdersrechten

   * Bijvoorbeeld gebruikersnaam &#39;admin&#39; / wachtwoord &#39;admin&#39;

* Navigeer vanuit de hoofdconsole naar **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Security]** > **[!UICONTROL Users]**.
* From the **[!UICONTROL Edit]** menu, select **[!UICONTROL Add User]**.

* In the `Create New User` dialog enter:

   * **ID&amp;ast;**: sirius
   * **E-mailadres**: sirius.nilson@mailinator.com
   * **Wachtwoord&amp;ast;**: password
   * **Wachtwoord&amp;amp bevestigen;ten;**: password
   * **Voornaam**: Sirius
   * **Achternaam&amp;ast;**: Nilson

### Sirius toewijzen aan de groep met communautaire beheerders {#assign-sirius-to-community-administrators-group}

Omlaag schuiven naar `Add User to Groups`:

* Voer C in om te zoeken

   * Selecteer `Community Administrators`
   * Selecteer `Community Enablement Managers`

* Selecteer **[!UICONTROL Save]**

![admin-rol](assets/admin-role.png)

