---
title: Leden en groepen beheerconsoles
description: Toegang tot leden en groepen beheerconsoles
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
role: Admin
exl-id: b64e24d2-8407-484c-8216-8d328ef5fa4f
solution: Experience Manager
feature: Communities
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '913'
ht-degree: 0%

---


# Leden en groepen beheerconsoles {#members-groups-management-consoles}

## Overzicht {#overview}

Voor AEM Communities-functies moeten bezoekers van de site vaak worden geregistreerd en aangemeld voordat ze kunnen deelnemen aan een community in de publicatieomgeving. De gebruikersregistratie hoeft alleen te bestaan in de publicatieomgeving en wordt meestal aangeduid als *leden* om ze van elkaar te onderscheiden *gebruikers* geregistreerd in de auteursomgeving.

### Leden (gebruikers) voor publicatie {#members-users-on-publish}

Gebruikend de leden en de Groepen van de Gemeenschappen consoles, leden en lidgroepen die in *publish* milieu kan van het *auteur* milieu. Dit is alleen mogelijk wanneer de [tunneldienst](deploy-communities.md#tunnel-service-on-author) is ingeschakeld.

### Gebruikers op auteur {#users-on-author}

Voor het beheer van gebruikers en groepen die zijn geregistreerd in het *auteur* -omgeving, is het noodzakelijk de beveiligingsconsole van het platform te gebruiken:

* Selecteer bij globale navigatie de optie **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Users]**.
* Selecteer bij globale navigatie de optie **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Groups]**.

>[!NOTE]
>
>Als voorbeeldinhoud is geïmplementeerd en ingeschakeld, zijn er veel voorbeeldgebruikers in zowel de auteur- als de publicatieomgeving. Deze gebruikers zijn niet aanwezig wanneer ze met [nosamplcontent-runmode](../../help/sites-administering/production-ready.md).

## Ledenconsole {#members-console}

In het auteursmilieu, om de console van Leden te bereiken voor het beheren van leden die in het publicatiemilieu worden geregistreerd:

* Selecteer bij globale navigatie de optie **[!UICONTROL Navigation]** > **[!UICONTROL Communities]** > **[!UICONTROL Members]**

>[!CAUTION]
>
>Het zal niet mogelijk zijn om de console van Leden te gebruiken als [tunneldienst](deploy-communities.md#tunnel-service-on-author) is niet ingeschakeld.

![De lidconsole](assets/member-console1.png)

### Zoeken {#search-features}

Selecteer het pictogram van het zijpaneel aan de linkerkant van het deelvenster `Members` om het deelvenster met de zoekzijde te openen.

![Pictogram van zijpaneel zoeken.](assets/leftpanel-icon.png)


![Filteropties voor de lidconsole](assets/member-console2.png)

Selecteer het zoekpictogram aan de linkerkant van het dialoogvenster `Members` om het venster met de zoekzijde te sluiten.

### Statistieken van de lidstaten {#member-statistics}

De kolommen weergeven `Views`, `Posts`, `Follows` en `Likes` worden bijgewerkt wanneer de gebruiker lid is van een of meer communitysites met Adobe Analytics [enabled](sites-console.md#analytics).

### CSV exporteren {#export-csv}

De `Export CSV` Als u een koppeling maakt, worden alle leden gedownload als een lijst met door komma&#39;s gescheiden waarden die u kunt importeren in een spreadsheet.

De kolomkoppen zijn

`| Screen Name |Last Name |First Name |Status |Views |Posts |Follows |Likes |`

## Nieuw lid maken {#create-new-member}

Selecteren `Create Member` om een gebruiker te maken in de publicatieomgeving.

![Het venster Nieuw lid maken](assets/create-member1.png)

### ALGEMEEN - Gegevens van de leden {#general-member-details}

De meeste velden zijn optionele velden die leden later kunnen invullen in hun profiel.

* **[!UICONTROL ID]**

(*Vereist*) De autoriseerbare id is de aanmeldings-id van het lid.
Standaard wordt de id ingesteld op de waarde van het vereiste e-mailadres.
*Nadat de id is gemaakt, kan deze niet meer worden gewijzigd*.

* **[!UICONTROL Email Address]**

(*Vereist*) Het e-mailadres van het lid.
Het lid kan zijn e-mailadres wijzigen bij het bijwerken van zijn profiel.I Als de id standaard op het e-mailadres is ingesteld, wordt de id *niet* wijzigen wanneer het e-mailadres wordt gewijzigd.

* **[!UICONTROL Password]**

  (*Vereist*) Het aanmeldingswachtwoord.

* **[!UICONTROL Retype Password]**

  (*Vereist*) Voer het wachtwoord opnieuw in ter verificatie.

* **[!UICONTROL Add Member to Sites]**

  (*Optioneel*) Maak een keuze uit bestaande gemeenschapssites om het lid toe te voegen aan de groep leden van de site van de community.

* **[!UICONTROL Add Member to Groups]**

  (*Optioneel*) Selecteer uit bestaande lidgroepen om het lid aan die groep toe te voegen.

* Selecteren **[!UICONTROL Save]**

### ALGEMEEN - Accountinstellingen {#general-account-settings}

Onder de montages van de Rekening is het mogelijk voor een communautaire beheerder:

* **[!UICONTROL Status]**
   * Een lid met een verbod kan zich niet aanmelden, zodat het geen pagina&#39;s kan weergeven of kan deelnemen aan activiteiten waarvoor aanmelden vereist is. Ze kunnen nog steeds anoniem een open communitysite bezoeken.

   * Niet verboden Een lid heeft volledige toegang tot de site van de community.

  Standaard is `Not Banned`.

* **[!UICONTROL Contribution Limits]**

  Als deze optie is ingeschakeld, is de mogelijkheid voor leden om inhoud te posten beperkt.
Het gebrek hangt van de configuratie van bijdragegrenzen af.
Zie [Limieten voor bijdragen van de lidstaten](limits.md).

* **[!UICONTROL Change Password]**

  Een koppeling die aanwezig is wanneer een bestaand lid wordt gewijzigd. Verstrekt de capaciteit voor een communautaire beheerder om een wachtwoord voor een lid terug te stellen.

### ALGEMEEN - Foto {#general-photo}

Om een avatar voor het lid te verstrekken, begin door te selecteren **[!UICONTROL Upload Image]** en kiest u een afbeelding van het type .jpg, .png, .tif of .gif. De voorkeursgrootte voor een afbeelding is 240 x 240 pixels bij 72 dpi.

### ALGEMEEN - Lid toevoegen aan sites {#general-add-member-to-sites}

Het lid kan worden toegevoegd aan een of meer groepen van leden van sites van de community. Voer eerst tekst in het tekstvak in.

### ALGEMEEN - Lid toevoegen aan groepen {#general-add-member-to-groups}

Het lid kan aan een of meer ledengroepen worden toegevoegd. Voer eerst tekst in het tekstvak in.

### Tabblad BADGES {#badges-tab}

De `BADGES` kunt u handmatig badges toewijzen en intrekken. De badges kunnen voor toegewezen rollen en badges zijn typisch verdiend.

Zie ook [Scores en badges](implementing-scoring.md).

![Het venster Membership Settings bewerken](assets/create-member2.png)

* **[!UICONTROL Add badges]**
   * Begin te typen om te selecteren uit [beschikbare badges](badges.md). Wanneer een badge is geselecteerd, kiest u elke site of alle sites waarop de badge samen met de avatar van het lid moet worden weergegeven.
   * Er kunnen meerdere badges en sites worden gekozen.
* **[!UICONTROL Remove badges]**
   * Selecteer het prullenbakpictogram naast een badge om het te verwijderen.

## Groepsconsole {#groups-console}

De console van Groepen, beschikbaar bij het auteursmilieu, staat voor de verwezenlijking en het beheer van lidgroepen toe die in het publicatiemilieu worden geregistreerd. Het is bijzonder nuttig om [Geprivilegieerde ledengroepen](users.md#privilegedmembersgroups).

De console Groepen openen:
* Selecteer bij globale navigatie de optie **[!UICONTROL Navigation]** > **[!UICONTROL Communities]** > **[!UICONTROL Groups]**.

>[!CAUTION]
>
>Het zal niet mogelijk zijn om de console van Groepen te gebruiken als [tunneldienst](deploy-communities.md#tunnel-service-on-author) is niet ingeschakeld.

### Nieuwe groep maken {#create-new-group}

Selecteren `Add Group` om een groep te maken in de publicatieomgeving.

![Het venster Nieuwe groep maken](assets/group-console1.png)

De vereiste gebieden voor het creëren van een publish-zij lidgroep zijn:

* **[!UICONTROL ID]**

  (*Vereist*) De unieke groep-id.

  *Nadat de id is gemaakt, kan deze niet meer worden gewijzigd.*

* **[!UICONTROL Name]**

  (*Optioneel*) De weergavenaam voor de groep.

  De standaardwaarde is ID.

* **[!UICONTROL Description]**

  (*Optioneel*) Een beschrijving van het doel en de machtigingen van de groep.

* **[!UICONTROL Add Members To Group]**

  (*Optioneel*) Selecteer leden aan de publiczijde die u wilt opnemen als eerste leden van de groep.

* Selecteren **[!UICONTROL Save]**

## Geautoriseerde beheerders {#authorized-administrators}

Wanneer het werken met leden in de console van de Leden van Gemeenschappen, is het noodzakelijk om binnen als gebruiker met aangewezen toestemmingen worden ondertekend, en voor de replicatieagent die door wordt gebruikt [tunneldienst](deploy-communities.md#tunnel-service-on-author) correct worden geconfigureerd.

Indien niet aangemeld als `admin`, dan moet de ingetekende gebruiker lid zijn van de `administrators` gebruikersgroep.

Zie ook [Replicatieagents op auteur](deploy-communities.md#replication-agents-on-author).
