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


# Eerste instelling voor activering {#initial-setup-for-enablement}

## Auteur- en publicatie-instanties starten {#start-author-and-publish-instances}

Voor ontwikkelings- en demonstratiedoeleinden is het nodig één auteur en één publicatieexemplaar uit te voeren.

Volg de standaard AEM [Aan de slag](../../help/sites-deploying/deploy.md#getting-started) instructies die in

* Auteursomgeving op [localhost:4502](http://localhost:4502/)
* Publiceer milieu op [localhost:4503](http://localhost:4503/)

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
>Als u niet bekend bent met AEM, bekijkt u de documentatie over [basisverwerking](../../help/sites-authoring/basic-handling.md) en een [handleiding voor het schrijven van pagina&#39;s](../../help/sites-authoring/qg-page-authoring.md).

## Nieuwste communityrelease {#install-latest-communities-release} installeren

Deze zelfstudie maakt een [communitysite inschakelen](overview.md#enablement-community). Ga voor de installatie van het nieuwste functiepakket naar:

* [Laatste releases](deploy-communities.md#latest-releases)

Voor een zelfstudie waarmee een [communitysite](overview.md#engagement-community) wordt gemaakt, gaat u naar [Aan de slag met AEM Communities](getting-started.md).

## Functies inschakelen {#configure-enablement-features} configureren

Om deze zelfstudie te volgen, is het nodig om enablement](enablement.md) correct te installeren en [vormen, die derdeproducten, zoals MySQL en MPEG vereist.

## Analyses {#configure-analytics} configureren

Wanneer [Adobe Analytics is geconfigureerd voor de communitysite](analytics.md), is meer informatie beschikbaar in de [rapporten](reports.md) die worden gegenereerd op actiemiddelen en leerpaden die zijn toegewezen aan leden van de community (studenten).

## E-mail voor meldingen configureren {#configure-email-for-notifications}

De functie voor meldingen, die standaard beschikbaar is voor alle sites die zijn gemaakt met de console `Communities Sites`, biedt een e-mailkanaal voor meldingen.

Het is nodig dat e-mail correct is geconfigureerd voor de site.

Zie [E-mail configureren](email.md).

## De tunnelservice {#enable-the-tunnel-service} inschakelen

Wanneer het creëren van een communautaire plaats in het auteursmilieu, maakt de tunneldienst de capaciteit mogelijk om gebruikers en gebruikersgroepen tot stand te brengen en te beheren die in het publicatiemilieu (leden) worden geregistreerd, rollen aan vertrouwde op communautaire leden toe te wijzen, en inhoud aan studenten toe te wijzen.

Zie [Gebruikers en gebruikersgroepen beheren](users.md) voor meer informatie.

Voor eenvoudige instructies om de tunneldienst toe te laten, zie [Tunnel Service](deploy-communities.md#tunnel-service-on-author).

## Zelfstudietags maken {#create-tutorial-tags}

Maak tags die u wilt gebruiken voor de zelfstudies voor toegang en activering met de naamruimte tag van `Tutorial`.

Gebruik de [Tagingconsole](../../help/sites-administering/tags.md#tagging-console) om de volgende tags te maken:

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

## Leden en groepen voor inschakelen maken {#create-enablement-members-and-groups}

Voor een community-site voor activering mogen sitebezoekers zich niet [zelf registreren of aanmelden via een sociaal netwerk](sites-console.md#user-management) gebruiken.

In plaats daarvan, met [tunneldienst](#enable-the-tunnel-service) toegelaten, wordt [Leden console](members.md) gebruikt om nieuwe leden in het publicatiemilieu te registreren.

In deze zelfstudie worden drie leden gemaakt in de publicatieomgeving. Twee leden zullen lid van een gebruikersgroep worden die aan een het leren weg wordt toegewezen, terwijl het derde lid een contactpunt van het enablement middel wordt.

Een vierde gebruiker wordt gecreeerd in het auteursmilieu en toegewezen de rollen van de Beheerder van de Gemeenschappen en Communautaire Manager van Enablement.

>[!NOTE]
>
>Deze leden worden gemaakt voordat de *Zelfstudie voor inschakelen*-communitysite wordt gemaakt.
>
>Als deze naderhand zijn gemaakt, kunnen ze tijdens het maken van leden worden toegevoegd als leden van de groep *Leerleden inschakelen*.
>
>In plaats daarvan, later, zullen zij [worden toegewezen aan de lidgroep](enablement-create-site.md#assignuserstocommunityenablemembersgroup).

### Riley Taylor - Ingeschreven {#riley-taylor-enrollee}

[Creeer een ](members.md#create-new-member) lid dat aan een groep Leerlingen zal worden toegevoegd - de Communautaire Groep van de Klasse van de Ski.

* **ID**: riley
* **E-mail**: riley.taylor@mailinator.com
* **Wachtwoord**: password
* **Wachtwoord** bevestigen: password
* **Voornaam**: Riley
* **Achternaam**: Taylor

### Sidney Croft - Ingeschreven {#sidney-croft-enrollee}

[Creeer een tweede ](members.md#create-new-member) lid dat aan de Communautaire Groep van de Klasse van de Ski zal worden toegevoegd.

* **ID**: sidney
* **E-mail**: sidney.croft@mailinator.com
* **Wachtwoord**: password
* **Wachtwoord** bevestigen: password
* **Voornaam**: Sidney
* **Achternaam**: Uitsnijden

### Quinn Harper - Enablement Resource Contact and Moderator {#quinn-harper-enablement-resource-contact-and-moderator}

[Creeer een ](members.md#create-new-member) lid dat aan de de lidgroep van de Plaats van de Gemeenschap zal worden toegevoegd zodra de plaats is gecreeerd. Dit lidmaatschap zal het lid om als enablement [Contact van het Middel ](resources.md#settings) toestaan worden toegewezen wanneer een enablement middel voor de plaats wordt gecreeerd.

* **ID**: quin
* **E-mail**: quinn.harper@mailinator.com
* **Wachtwoord**: password
* **Wachtwoord** bevestigen: password
* **Voornaam**: Quinn
* **Achternaam**: Harper

### Een gebruikersgroep toevoegen - Community Ski-klasse {#add-a-user-group-community-ski-class}

[Voeg een nieuwe ](members.md#create-new-group) groep toe genoemd de Klasse van SKI Gemeenschap.

* **ID**: community-ski-klasse
* **Naam**: Community Ski-klasse
* **Omschrijving**: een steekproefgroep voor het toewijzen van enablement middelen
* **Leden toevoegen aan groep**  &#39;toevoegen&#39;:

   * riley
   * sidney

* Selecteer **[!UICONTROL Save]**

### Eigenschappen van de communautaire Ski-klasse {#community-ski-class-properties}

![ski-klasse-eigenschappen](assets/ski-class-properties.png)

>[!NOTE]
>
>Tijdens het creëren van de communautaire plaats, kunnen de bestaande leden en de groepen aan de groep van leden van de communautaire plaats worden toegevoegd.

## Rol van communautaire beheerder {#community-administrator-role}

De leden van de groep van Beheerders van de Gemeenschap kunnen communautaire plaatsen tot stand brengen, plaatsen beheren, leden beheren (zij kunnen leden van de gemeenschap verbieden), en gematigde inhoud.

### Gebruiker {#create-user} maken

Creeer een gebruiker op *auteur*, die de rol van Communautaire Beheerder wordt toegewezen:

* Instantie van auteur

   * Bijvoorbeeld [http://localhost:4502/](http://localhost:4503/)

* Aanmelden met beheerdersrechten

   * Bijvoorbeeld gebruikersnaam &#39;admin&#39; / wachtwoord &#39;admin&#39;

* Navigeer vanuit de hoofdconsole naar **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Security]** > **[!UICONTROL Users]**.
* Selecteer **[!UICONTROL Add User]** in het menu **[!UICONTROL Edit]**.

* Voer in het dialoogvenster `Create New User`:

   * **ID&amp;ast;**: sirius
   * **E-mailadres**: sirius.nilson@mailinator.com
   * **Wachtwoord&amp;ast;**: password
   * **Wachtwoord&amp;ast bevestigen;**: password
   * **Voornaam**: Sirius
   * **Achternaam&amp;st:**: Nilson

### Sirius toewijzen aan groep Beheerders uit Gemeenschap {#assign-sirius-to-community-administrators-group}

Omlaag schuiven naar `Add User to Groups`:

* Voer C in om te zoeken

   * Selecteer `Community Administrators`
   * Selecteer `Community Enablement Managers`

* Selecteer **[!UICONTROL Save]**

![admin-rol](assets/admin-role.png)

