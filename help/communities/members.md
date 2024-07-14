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

Voor AEM Communities-functies moeten bezoekers van de site vaak worden geregistreerd en aangemeld voordat ze kunnen deelnemen aan een community in de publicatieomgeving. Hun gebruikersregistratie heeft slechts in het publicatiemilieu nodig en zij worden algemeen bedoeld als *leden* om hen van *gebruikers* te onderscheiden die in het auteursmilieu worden geregistreerd.

### Leden (gebruikers) op Publish {#members-users-on-publish}

Gebruikend de leden van Gemeenschappen en de Groepen consoles, leden en lidgroepen die in *worden geregistreerd publiceren* milieu kunnen van het *auteur* milieu worden gecreeerd en worden geleid. Dit is slechts mogelijk wanneer de [ tunneldienst ](deploy-communities.md#tunnel-service-on-author) wordt toegelaten.

### Gebruikers op auteur {#users-on-author}

Voor het beheren van gebruikers en groepen die in het *auteur* milieu worden geregistreerd, is het noodzakelijk om de de veiligheidsconsole van het platform te gebruiken:

* Selecteer **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Users]** bij globale navigatie.
* Selecteer **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Groups]** bij globale navigatie.

>[!NOTE]
>
>Als voorbeeldinhoud is geïmplementeerd en ingeschakeld, zijn er veel voorbeeldgebruikers in zowel de auteur- als de publicatieomgeving. Deze gebruikers zullen niet aanwezig zijn wanneer het lopen met [ geen runtimeContent ](../../help/sites-administering/production-ready.md).

## Ledenconsole {#members-console}

In het auteursmilieu, om de console van Leden te bereiken voor het beheren van leden die in het publicatiemilieu worden geregistreerd:

* Selecteer **[!UICONTROL Navigation]** > **[!UICONTROL Communities]** > **[!UICONTROL Members]** bij globale navigatie

>[!CAUTION]
>
>Het zal niet mogelijk zijn om de console van Leden te gebruiken als de [ tunneldienst ](deploy-communities.md#tunnel-service-on-author) niet wordt toegelaten.

![ De lidconsole ](assets/member-console1.png)

### Zoeken {#search-features}

Selecteer het pictogram van het zijpaneel aan de linkerkant van de koptekst van `Members` om het paneel van de onderzoekskant van knevel te voorzien.

![ het zijpaneelpictogram van het Onderzoek.](assets/leftpanel-icon.png)


![ de opties van de Filter voor de lidconsole ](assets/member-console2.png)

Selecteer het zoekpictogram aan de linkerkant van de koptekst van `Members` om het venster met de zoekzijde te sluiten.

### Statistieken van de lidstaten {#member-statistics}

De kolommen die `Views`, `Posts`, `Follows` en `Likes` tonen worden bijgewerkt wanneer de gebruiker een lid van één of meerdere communautaire plaatsen met Adobe Analytics [ ](sites-console.md#analytics) toegelaten is.

### CSV exporteren {#export-csv}

Als u de koppeling `Export CSV` selecteert, worden alle leden gedownload als een lijst met door komma&#39;s gescheiden waarden die u kunt importeren in een spreadsheet.

De kolomkoppen zijn

`| Screen Name |Last Name |First Name |Status |Views |Posts |Follows |Likes |`

## Nieuw lid maken {#create-new-member}

Selecteer `Create Member` om een gebruiker in de publicatieomgeving te maken.

![ het Create Nieuwe venster van het Lid ](assets/create-member1.png)

### ALGEMEEN - Gegevens van de leden {#general-member-details}

De meeste velden zijn optionele velden die leden later kunnen invullen in hun profiel.

* **[!UICONTROL ID]**

(*Vereiste*) Vergunnbare identiteitskaart is login identiteitskaart van het lid.
Standaard wordt de id ingesteld op de waarde van het vereiste e-mailadres.
*Zodra gecreeerd, kan identiteitskaart niet worden gewijzigd*.

* **[!UICONTROL Email Address]**

(*Vereist*) Het e-mailadres van het lid.
Het lid kan zijn e-mailadres wijzigen bij het bijwerken van zijn profiel.I
Als identiteitskaart aan het e-mailadres in gebreke bleef, zal identiteitskaart *niet* veranderen wanneer het e-mailadres wordt veranderd.

* **[!UICONTROL Password]**

  (*Vereiste*) het login wachtwoord.

* **[!UICONTROL Retype Password]**

  (*Vereiste*) neem het wachtwoord voor controle opnieuw op.

* **[!UICONTROL Add Member to Sites]**

  (*Facultatieve*) Uitgezocht van bestaande communautaire plaatsen om het lid aan de de ledengroep van de communautaire plaats toe te voegen.

* **[!UICONTROL Add Member to Groups]**

  (*Facultatieve*) Uitgezocht van bestaande lidgroepen om het lid aan die groep toe te voegen.

* Selecteren **[!UICONTROL Save]**

### ALGEMEEN - Accountinstellingen {#general-account-settings}

Onder de montages van de Rekening is het mogelijk voor een communautaire beheerder:

* **[!UICONTROL Status]**
   * Verboden
Een lid kan zich niet aanmelden, waardoor het geen pagina&#39;s kan weergeven of kan deelnemen aan activiteiten waarvoor aanmelden vereist is. Ze kunnen nog steeds anoniem een open communitysite bezoeken.

   * Niet verboden
Een lid heeft volledige toegang tot de site van de community.

  De standaardwaarde is `Not Banned` .

* **[!UICONTROL Contribution Limits]**

  Als deze optie is ingeschakeld, is de mogelijkheid voor leden om inhoud te posten beperkt.
Het gebrek hangt van de configuratie van bijdragegrenzen af.
Zie {de grenzen van de Bijdrage van 0} Lid ](limits.md).[

* **[!UICONTROL Change Password]**

  Een koppeling die aanwezig is wanneer een bestaand lid wordt gewijzigd. Verstrekt de capaciteit voor een communautaire beheerder om een wachtwoord voor een lid terug te stellen.

### ALGEMEEN - Foto {#general-photo}

Als u een avatar voor het lid wilt opgeven, selecteert u eerst **[!UICONTROL Upload Image]** en kiest u een afbeelding van het type .jpg, .png, .tif of .gif. De voorkeursgrootte voor een afbeelding is 240 x 240 pixels bij 72 dpi.

### ALGEMEEN - Lid toevoegen aan sites {#general-add-member-to-sites}

Het lid kan worden toegevoegd aan een of meer groepen van leden van sites van de community. Voer eerst tekst in het tekstvak in.

### ALGEMEEN - Lid toevoegen aan groepen {#general-add-member-to-groups}

Het lid kan aan een of meer ledengroepen worden toegevoegd. Voer eerst tekst in het tekstvak in.

### Tabblad BADGES {#badges-tab}

Met het deelvenster `BADGES` kunt u handmatig badges toewijzen en intrekken. De badges kunnen voor toegewezen rollen en badges zijn typisch verdiend.

Zie ook [ het Scoren en Badges ](implementing-scoring.md).

![ het Edit venster van de Montages van het Lidmaatschap ](assets/create-member2.png)

* **[!UICONTROL Add badges]**
   * Begin het typen om van [ beschikbare badges ](badges.md) te selecteren. Wanneer een badge is geselecteerd, kiest u elke site of alle sites waarop de badge samen met de avatar van het lid moet worden weergegeven.
   * Er kunnen meerdere badges en sites worden gekozen.
* **[!UICONTROL Remove badges]**
   * Selecteer het prullenbakpictogram naast een badge om het te verwijderen.

## Groepsconsole {#groups-console}

De console van Groepen, beschikbaar bij het auteursmilieu, staat voor de verwezenlijking en het beheer van lidgroepen toe die in het publicatiemilieu worden geregistreerd. Het is met name nuttig voor [ Geprivilegieerde lidgroepen ](users.md#privilegedmembersgroups).

De console Groepen openen:
* Selecteer **[!UICONTROL Navigation]** > **[!UICONTROL Communities]** > **[!UICONTROL Groups]** bij globale navigatie.

>[!CAUTION]
>
>Het zal niet mogelijk zijn om de console van Groepen te gebruiken als de [ tunneldienst ](deploy-communities.md#tunnel-service-on-author) niet wordt toegelaten.

### Nieuwe groep maken {#create-new-group}

Selecteer `Add Group` om een groep te maken in de publicatieomgeving.

![ het Create Nieuwe venster van de Groep ](assets/group-console1.png)

De vereiste gebieden voor het creëren van een publish-zij lidgroep zijn:

* **[!UICONTROL ID]**

  (*Vereiste*) unieke identiteitskaart van de groep.

  *Zodra gecreeerd, identiteitskaart kan niet worden gewijzigd.*

* **[!UICONTROL Name]**

  (*Facultatieve*) de vertoningsnaam voor de groep.

  De standaardwaarde is ID.

* **[!UICONTROL Description]**

  (*Facultatieve*) een beschrijving van het doel en de toestemmingen van de groep.

* **[!UICONTROL Add Members To Group]**

  (*Facultatieve*) Uitgezocht publiceer-zijleden die als aanvankelijke leden van de groep moeten worden omvat.

* Selecteren **[!UICONTROL Save]**

## Geautoriseerde beheerders {#authorized-administrators}

Wanneer het werken met leden in de de ledenconsole van Gemeenschappen, is het noodzakelijk om binnen als gebruiker met aangewezen toestemmingen worden ondertekend, en voor de replicatieagent die door de [ tunneldienst ](deploy-communities.md#tunnel-service-on-author) wordt gebruikt correct worden gevormd.

Als u zich niet hebt aangemeld als `admin` , moet de aangemelde gebruiker lid zijn van de gebruikersgroep van `administrators` .

Zie ook [ de Agenten van de Replicatie op Auteur ](deploy-communities.md#replication-agents-on-author).
