---
title: Eerste instelling voor inschakelen
seo-title: Initial Setup
description: Eerste instelling voor inschakelen
seo-description: Initial Setup for Enablement
uuid: 873ec41d-c088-41d9-a535-de5300661de6
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: introduction
content-type: reference
discoiquuid: f2ac3d66-cc79-498f-83fb-dd96feb88de2
exl-id: ed494922-3e15-4778-84c1-35c8846ce980
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '851'
ht-degree: 0%

---

# Eerste instelling voor inschakelen  {#initial-setup-for-enablement}

## Auteur- en publicatie-instanties starten {#start-author-and-publish-instances}

Voor ontwikkelings- en demonstratiedoeleinden is het nodig één auteur en één publicatieexemplaar uit te voeren.

Volg de AEM [Aan de slag](../../help/sites-deploying/deploy.md#getting-started) instructies die

* Auteursomgeving op [localhost:4502](http://localhost:4502/)
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
>Als u niet bekend bent met AEM, kunt u de documentatie raadplegen op [basisbehandeling](../../help/sites-authoring/basic-handling.md) en [snelle handleiding voor het ontwerpen van pagina&#39;s](../../help/sites-authoring/qg-page-authoring.md).

## Laatste versie van Gemeenschappen installeren {#install-latest-communities-release}

Deze zelfstudie maakt een [gemeenschapssite inschakelen](overview.md#enablement-community). Ga voor de installatie van het nieuwste functiepakket naar:

* [Laatste releases](deploy-communities.md#latest-releases)

Voor een zelfstudie die een [community-site voor betrokkenheid](overview.md#engagement-community), bezoek [Aan de slag met AEM Communities](getting-started.md).

## Functies van Enablement configureren {#configure-enablement-features}

Als u deze zelfstudie wilt volgen, moet u deze op de juiste manier installeren en [configuratie enablement](enablement.md), waarvoor producten van derden nodig zijn, zoals MySQL en FFmpeg.

## Analyses configureren {#configure-analytics}

Wanneer [Adobe Analytics is geconfigureerd voor de communitysite](analytics.md), meer informatie is beschikbaar in de [rapporten](reports.md) gegenereerd op basis van bronnen voor activering en leerpaden die zijn toegewezen aan leden van de gemeenschap (studenten).

## E-mail voor meldingen configureren {#configure-email-for-notifications}

De functie voor meldingen is standaard beschikbaar voor alle sites die zijn gemaakt met de `Communities Sites` -console, biedt een e-mailkanaal voor meldingen.

Het is nodig dat e-mail correct is geconfigureerd voor de site.

Zie [E-mail configureren](email.md).

## De tunnelservice inschakelen {#enable-the-tunnel-service}

Wanneer het creëren van een communautaire plaats in het auteursmilieu, maakt de tunneldienst de capaciteit mogelijk om gebruikers en gebruikersgroepen tot stand te brengen en te beheren die in het publicatiemilieu (leden) worden geregistreerd, rollen aan vertrouwde op communautaire leden toe te wijzen, en inhoud aan studenten toe te wijzen.

Zie voor meer informatie [Gebruikers en gebruikersgroepen beheren](users.md).

Voor eenvoudige instructies om de tunneldienst toe te laten, zie [Tunnelservice](deploy-communities.md#tunnel-service-on-author).

## Zelfstudietags maken {#create-tutorial-tags}

Tags maken die u wilt gebruiken voor de zelfstudies voor toegang en activering met behulp van de naamruimte tag van `Tutorial`.

Gebruik de [Tagingconsole](../../help/sites-administering/tags.md#tagging-console) om de volgende labels te maken:

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

Voor een site van een community voor activering mogen bezoekers van de site niet in staat zijn [zelf registreren en aanmelden via een sociaal netwerk niet gebruiken](sites-console.md#user-management).

In plaats daarvan, met [tunneldienst](#enable-the-tunnel-service) enabled, de [Ledenconsole](members.md) wordt gebruikt om nieuwe leden te registreren in de publicatieomgeving.

In deze zelfstudie worden drie leden gemaakt in de publicatieomgeving. Twee leden zullen lid van een gebruikersgroep worden die aan een het leren weg wordt toegewezen, terwijl het derde lid een het middelcontact van het toelaat wordt.

Een vierde gebruiker wordt gecreeerd in het auteursmilieu en toegewezen de rollen van de Beheerder van de Gemeenschappen en Communautaire Manager van Enablement.

>[!NOTE]
>
>Deze leden worden gemaakt voordat de *Zelfstudie inschakelen* community-site.
>
>Als ze later worden gemaakt, kunnen ze worden toegevoegd als leden van de *Groep leden van zelfstudie inschakelen* tijdens het maken van leden.
>
>In plaats daarvan worden ze later [toegewezen aan de ledengroep](enablement-create-site.md#assignuserstocommunityenablemembersgroup).

### Riley Taylor - Ingeschreven {#riley-taylor-enrollee}

[Een lid maken](members.md#create-new-member) die worden toegevoegd aan een groep Leerlingen - de Community Ski Class-groep.

* **ID**: riley
* **E-mail**: riley.taylor@mailinator.com
* **Wachtwoord**: password
* **Wachtwoord bevestigen**: password
* **Voornaam**: Riley
* **Achternaam**: Taylor

### Sidney Croft - Ingeschreven {#sidney-croft-enrollee}

[Een tweede lid maken](members.md#create-new-member) die worden toegevoegd aan de communautaire Ski-klassengroep.

* **ID**: sidney
* **E-mail**: sidney.croft@mailinator.com
* **Wachtwoord**: password
* **Wachtwoord bevestigen**: password
* **Voornaam**: Sidney
* **Achternaam**: Uitsnijden

### Quinn Harper - Enablement Resource Contact and Moderator {#quinn-harper-enablement-resource-contact-and-moderator}

[Een lid maken](members.md#create-new-member) die worden toegevoegd aan de lidgroep van de Community Site nadat de site is gemaakt. Met dit lidmaatschap kan het lid worden toegewezen als enablement [Contactpersoon bron](resources.md#settings) wanneer een enablement-bron voor de site wordt gemaakt.

* **ID**: quin
* **E-mail**: quinn.harper@mailinator.com
* **Wachtwoord**: password
* **Wachtwoord bevestigen**: password
* **Voornaam**: Quinn
* **Achternaam**: Harper

### Gebruikersgroep toevoegen - Klasse SKI voor community {#add-a-user-group-community-ski-class}

[Een nieuwe groep toevoegen](members.md#create-new-group) Community Ski Class genoemd.

* **ID**: community-ski-klasse
* **Naam**: Community Ski-klasse
* **Beschrijving**: een steekproefgroep voor het toewijzen van enablement middelen
* **Leden toevoegen aan groep** &quot;add&quot;:

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

Een gebruiker maken op *auteur*, die de rol van communautaire administrateur krijgt toegewezen:

* Instantie van auteur

   * Bijvoorbeeld: [http://localhost:4502/](http://localhost:4503/)

* Aanmelden met beheerdersrechten

   * Bijvoorbeeld gebruikersnaam &#39;admin&#39; / wachtwoord &#39;admin&#39;

* Navigeer vanuit de hoofdconsole naar **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Security]** > **[!UICONTROL Users]**.
* Van de **[!UICONTROL Edit]** menu, selecteert u **[!UICONTROL Add User]**.

* In de `Create New User` dialoogvenster openen:

   * **ID&amp;ast;**: sirius
   * **E-mailadres**: sirius.nilson@mailinator.com
   * **Wachtwoord&amp;ast;**: password
   * **Wachtwoord&amp;ast bevestigen;**: password
   * **Voornaam**: Sirius
   * **Achternaam&amp;ast;**: Nilson

### Sirius toewijzen aan de groep met communautaire beheerders {#assign-sirius-to-community-administrators-group}

Omlaag schuiven naar `Add User to Groups`:

* Voer C in om te zoeken

   * Selecteer `Community Administrators`
   * Selecteer `Community Enablement Managers`

* Selecteer **[!UICONTROL Save]**

![admin-rol](assets/admin-role.png)
