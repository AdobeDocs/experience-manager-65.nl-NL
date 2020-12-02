---
title: Leden en groepen beheerconsoles
seo-title: Leden en groepen beheerconsoles
description: Toegang tot leden en groepen beheerconsoles
seo-description: Toegang tot leden en groepen beheerconsoles
uuid: 2e93e861-a066-4189-91db-f8b784bc5aea
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: ccabf301-b417-48aa-8501-8360fd9f3e36
translation-type: tm+mt
source-git-commit: f375b40c084ee363757b78c602091f38524b8b03
workflow-type: tm+mt
source-wordcount: '917'
ht-degree: 0%

---


# Leden en groepen beheerconsoles {#members-groups-management-consoles}

## Overzicht {#overview}

Voor AEM Communities-functies moeten bezoekers van de site vaak worden geregistreerd en aangemeld voordat ze kunnen deelnemen aan een community in de publicatieomgeving. Hun gebruikersregistratie hoeft alleen te bestaan in de publicatieomgeving en wordt meestal *leden* genoemd om ze te onderscheiden van *gebruikers* die zijn geregistreerd in de auteursomgeving.

### Leden (gebruikers) bij publicatie {#members-users-on-publish}

Met behulp van de communityleden en -groepen kunnen leden en lidgroepen die zijn geregistreerd in de *publish*-omgeving worden gemaakt en beheerd vanuit de *auteur*-omgeving. Dit is alleen mogelijk wanneer de [tunnelservice](deploy-communities.md#tunnel-service-on-author) is ingeschakeld.

### Gebruikers op auteur {#users-on-author}

Voor het beheer van gebruikers en groepen die zijn geregistreerd in de *auteur*-omgeving, is het nodig om de beveiligingsconsole van het platform te gebruiken:

* Selecteer **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Users]** bij globale navigatie.
* Selecteer **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Groups]** bij globale navigatie.

>[!NOTE]
>
>Als voorbeeldinhoud is geïmplementeerd en ingeschakeld, zijn er veel voorbeeldgebruikers in zowel de auteur- als de publicatieomgeving. Deze gebruikers zullen niet aanwezig zijn wanneer het lopen met [nosamplcontent runmode](../../help/sites-administering/production-ready.md).

## Ledenconsole {#members-console}

In het auteursmilieu, om de console van Leden te bereiken voor het beheren van leden die in het publicatiemilieu worden geregistreerd:

* Selecteer **[!UICONTROL Navigation]** > **[!UICONTROL Communities]** > **[!UICONTROL Members]**

>[!CAUTION]
>
>Het zal niet mogelijk zijn om de console van Leden te gebruiken als [tunneldienst](deploy-communities.md#tunnel-service-on-author) niet wordt toegelaten.

![member-console1](assets/member-console1.png)

### Zoeken {#search-features}

Selecteer het pictogram van het zijpaneel aan de linkerkant van de kopbal `Members` om het onderzoek zijpaneel van een knevel te voorzien.

![](assets/leftpanel-icon.png)


![member-console2](assets/member-console2.png)

Selecteer het zoekpictogram aan de linkerkant van de koptekst `Members` om het venster met de zoekzijde gesloten te schakelen.

### Lid-statistieken {#member-statistics}

De kolommen `Views`, `Posts`, `Follows` en `Likes` worden bijgewerkt wanneer de gebruiker lid is van één of meerdere communitysites met Adobe Analytics [enabled](sites-console.md#analytics).

### CSV {#export-csv} exporteren

Als u de koppeling `Export CSV` selecteert, worden alle leden gedownload als een lijst met door komma&#39;s gescheiden waarden, die geschikt zijn voor importeren in een spreadsheet.

De kolomkoppen zijn

`| Screen Name |Last Name |First Name |Status |Views |Posts |Follows |Likes |`

## Nieuw lid {#create-new-member} maken

Selecteer `Create Member` om een gebruiker in het publicatiemilieu tot stand te brengen.

![create-member1](assets/create-member1.png)

### ALGEMEEN - Details lid {#general-member-details}

De meeste velden zijn optionele velden die leden later kunnen invullen in hun profiel.

* **[!UICONTROL ID]**

(*Required*) Authorizable identiteitskaart is login identiteitskaart van het lid.
Standaard wordt de id ingesteld op de waarde van het vereiste e-mailadres.
*Nadat de id is gemaakt, kan deze niet meer worden gewijzigd*.

* **[!UICONTROL Email Address]**

(*Required*) Het e-mailadres van het lid.
Het lid kan zijn e-mailadres wijzigen bij het bijwerken van zijn profiel.I
Als de id standaard is ingesteld op het e-mailadres, verandert de id *niet* wanneer het e-mailadres wordt gewijzigd.

* **[!UICONTROL Password]**

   (*Required*) het login wachtwoord.

* **[!UICONTROL Retype Password]**

   (*Required*) ga het wachtwoord voor controle opnieuw in.

* **[!UICONTROL Add Member to Sites]**

   (*Optioneel*) Selecteer een van de bestaande communitysites om het lid toe te voegen aan de ledengroep van de community.

* **[!UICONTROL Add Member to Groups]**

   (*Facultatief*) Uitgezocht van bestaande lidgroepen om het lid aan die groep toe te voegen.

* Selecteer **[!UICONTROL Save]**

### ALGEMEEN - Accountinstellingen {#general-account-settings}

Onder de montages van de Rekening is het mogelijk voor een communautaire beheerder:

* **[!UICONTROL Status]**
   * Verboden
Een lid kan zich niet aanmelden, waardoor het geen pagina&#39;s kan weergeven of kan deelnemen aan activiteiten waarvoor aanmelden vereist is. Ze kunnen nog steeds anoniem een open communitysite bezoeken.

   * Niet verboden
Een lid heeft volledige toegang tot de site van de community.

   De standaardwaarde is `Not Banned`.

* **[!UICONTROL Contribution Limits]**

   Als deze optie is ingeschakeld, is de mogelijkheid voor leden om inhoud te posten beperkt.
Het gebrek hangt van de configuratie van bijdragegrenzen af.
Zie [Limieten voor bijdragen van leden](limits.md).

* **[!UICONTROL Change Password]**

   Een koppeling die aanwezig is wanneer een bestaand lid wordt gewijzigd. Verstrekt de capaciteit voor een communautaire beheerder om een wachtwoord voor een lid terug te stellen.

### ALGEMEEN - Foto {#general-photo}

Als u een avatar voor het lid wilt opgeven, selecteert u eerst **[!UICONTROL Upload Image]** en kiest u een afbeelding van het type .jpg, .png, .tif of .gif. De voorkeursgrootte voor een afbeelding is 240 x 240 pixels bij 72 dpi.

### ALGEMEEN - Lid toevoegen aan sites {#general-add-member-to-sites}

Het lid kan worden toegevoegd aan een of meer groepen van leden van sites van de community. Voer eerst tekst in het tekstvak in.

### ALGEMEEN - Lid toevoegen aan groepen {#general-add-member-to-groups}

Het lid kan aan een of meer ledengroepen worden toegevoegd. Voer eerst tekst in het tekstvak in.

### Tabblad BADGES {#badges-tab}

Met het deelvenster `BADGES` kunt u badges handmatig toewijzen en intrekken. De badges kunnen voor toegewezen rollen evenals badges typisch worden verdiend.

Zie ook [Scores en Badges](implementing-scoring.md).

![create-member2](assets/create-member2.png)

* **[!UICONTROL Add badges]**
   * Begin te typen om uit [beschikbare badges](badges.md) te selecteren. Wanneer een badge is geselecteerd, kiest u elke site of alle sites waarop de badge samen met de avatar van het lid moet worden weergegeven.
   * Er kunnen meerdere badges en sites worden gekozen.
* **[!UICONTROL Remove badges]**
   * Selecteer het prullenbakpictogram naast een badge om het te verwijderen.

## Groepenconsole {#groups-console}

De console van Groepen, beschikbaar bij het auteursmilieu, staat voor de verwezenlijking en het beheer van lidgroepen toe die in het publicatiemilieu worden geregistreerd. Het is met name nuttig voor:
* [Geprivilegieerde ledengroepen](users.md#privilegedmembersgroups)
* Groepse toewijzing van [enablement resources](resources.md)

De console Groepen openen:
* Selecteer **[!UICONTROL Navigation]** > **[!UICONTROL Communities]** > **[!UICONTROL Groups]** bij globale navigatie.

>[!CAUTION]
>
>Het zal niet mogelijk zijn om de console van Groepen te gebruiken als [tunneldienst](deploy-communities.md#tunnel-service-on-author) niet wordt toegelaten.

### Nieuwe groep maken {#create-new-group}

Selecteer `Add Group` om een groep in het publicatiemilieu tot stand te brengen.

![group-console1](assets/group-console1.png)

De vereiste gebieden voor het creëren van een nieuwe publish-side lidgroep zijn:

* **[!UICONTROL ID]**

   (*Required*) De unieke identiteitskaart van de groep

   *Nadat de id is gemaakt, kan deze niet meer worden gewijzigd.*

* **[!UICONTROL Name]**

   (*Optioneel*) De weergavenaam voor de groep.

   De standaardwaarde is ID.

* **[!UICONTROL Description]**

   (*Optioneel*) Een beschrijving van het doel en de machtigingen van de groep.

* **[!UICONTROL Add Members To Group]**

   (*Optioneel*) Selecteer leden aan de publiczijde die u wilt opnemen als eerste leden van de groep.

* Selecteer **[!UICONTROL Save]**

## Geautoriseerde beheerders {#authorized-administrators}

Wanneer het werken met leden in de console van de Leden van Gemeenschappen, is het noodzakelijk om binnen als gebruiker met aangewezen toestemmingen worden ondertekend, en voor de replicatieagent die door [tunneldienst ](deploy-communities.md#tunnel-service-on-author) wordt gebruikt correct worden gevormd.

Als u zich niet hebt aangemeld als `admin`, moet de aangemelde gebruiker lid zijn van de gebruikersgroep `administrators`.

Zie ook [Replication Agents on Author](deploy-communities.md#replication-agents-on-author).
