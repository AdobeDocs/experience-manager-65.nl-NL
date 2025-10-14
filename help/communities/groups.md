---
title: Console van groepen Gemeenschap
description: Leer over de console van de Groepen van de Gemeenschap die u communautaire groepen laat tot stand brengen wanneer de de malplaatjestructuur van een communautaire plaats de groepsfunctie omvat.
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
docset: aem65
pagetitle: Community Groups Console
role: Admin
exl-id: ef371ff8-6b4f-4e5a-98fb-d7c274927c46
solution: Experience Manager
feature: Communities
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '1696'
ht-degree: 0%

---

# Console van groepen Gemeenschap {#community-groups-console}

De console van Groepen verleent toegang tot het creëren van communautaire groepen wanneer de het malplaatjestructuur van een communautaire plaats [&#128279;](/help/communities/sites-console.md#step1) de [&#x200B; groepsfunctie &#x200B;](/help/communities/functions.md#groups-function) omvat.

* AEM Communities ondersteunt het nesten van groepen binnen andere groepen. Het nesten van de groep is mogelijk wanneer de [&#x200B; structuur van de nieuwe groep &#x200B;](/help/communities/tools-groups.md) de groepsfunctie bevat.
* Alleen voor de auteursomgeving is er een wizard voor het maken van groepen die lijkt op de wizard voor het maken van sites.
* Of (of niet) de leden groepen in publiceren milieu kunnen tot stand brengen is het configureerbaar wanneer het toevoegen van een functie van Groepen aan een communautaire plaatsstructuur of een communautaire groepsstructuur.

Van de drie groepssjablonen die worden opgenomen, bevat alleen de `Reference Group` -sjabloon een groepfunctie in de structuur.

De verschillende facetten van de communautaire groepen zijn:

* **Creatie**: de nieuwe groep kan op auteur en naar keuze op publiceer instantie worden gecreeerd.
* **Controle**: de groep kan open of geheim zijn.
* **het Nesten**: de groep kan nul of meer groepen bevatten.

<!-- This is a 404 on helpx. Update or remove.
>[!NOTE]
>
>Community groups, created in the publish environment before the [existence of the Community Groups console](/help/communities/version-history.md#featurepack1fp1), is not listed in the Community Groups console, and thus, are not modifiable using the console.
-->

>[!NOTE]
>
>Deze console van Groepen, slechts toegankelijk van de console van de Plaatsen van Gemeenschappen, moet niet met de console van de lid [&#x200B; Groepen &#x200B;](/help/communities/members.md) voor het beheren van lidgroepen worden verward.
>
>De groepen van het lid zijn gebruikersgroepen die in publiceren milieu worden geregistreerd en van het auteursmilieu worden betreden gebruikend de [&#x200B; tunneldienst &#x200B;](/help/communities/deploy-communities.md#tunnel-service-on-author).

## Groep maken {#group-creation}

De console Groepen openen:

* Meld u bij Auteur aan met beheerdersrechten.
* Vanuit globale navigatie: **[!UICONTROL Communities]** > **[!UICONTROL Sites]** .
* Selecteer een bestaande community-sitemap zodat u deze kunt openen.
* Selecteer een exemplaar van een communautaire plaats binnen de omslag.

   * De structuur van de site van de community moet een groepfunctie bevatten.
   * Deze schermafbeeldingen zijn van het Begonnen Worden leerprogramma na [&#x200B; creërend groepen op publiceren &#x200B;](/help/communities/published-site.md).

  ![&#x200B; creeer-groep &#x200B;](assets/create-group.png)

* Selecteer de **omslag van Groepen** zodat kunt u het openen.

  Als deze groep wordt geopend, worden alle bestaande groepen weergegeven, ongeacht of deze zijn gemaakt op Auteur of Publish.

  Van deze console van Groepen, is het mogelijk om nieuwe groepen te ontwerpen.

  ![&#x200B; creeer-new-group &#x200B;](assets/create-new-group.png)

* Selecteer de **Create knoop van de Groep**.

### Stap 1: template voor de communautaire groep {#step-community-group-template}

![&#x200B; Meertalige communautaire groepen &#x200B;](assets/multi-lingual-group.png)

* **Titel van de Groep van de Gemeenschap**

  Een weergavetitel voor de groep.
De titel wordt op de gepubliceerde site voor de groep weergegeven.

* **Beschrijving van de Groep van de Gemeenschap**

  Een beschrijving van de groep.

* **Hoofdmap van de Groep van de Gemeenschap**

  Het hoofdpad naar de groep.
De standaardhoofdmap is de bovenliggende site, maar de hoofdmap kan naar elke locatie binnen de website worden verplaatst. Het wordt afgeraden dit te wijzigen.

* **extra Beschikbare de Talen(s) van de Communautaire Groep** menu

  Gebruik de drop-down om de beschikbare talen van de communautaire groep te selecteren. In het menu worden alle talen weergegeven waarin de bovenliggende communitysite is gemaakt. Gebruikers kunnen in deze ene stap uit deze talen kiezen om groepen te maken in meerdere landinstellingen. De zelfde groep wordt gecreeerd in veelvoudige gespecificeerde talen in de console van Groepen van de respectieve communautaire plaatsen.

* **Communautaire Naam van de Groep**

  De naam van de basispagina van de groep die in URL verschijnt. Gebruik geen onderstrepingstekens (_) en trefwoorden zoals bronnen en configuratie in groepsnaam.

   * Controleer de naam nogmaals omdat deze niet gemakkelijk kan worden gewijzigd nadat de groep is gemaakt.
   * De basis-URL wordt onder de `Community Group Name` weergegeven.
   * Voor een geldige URL voegt u &quot;.html&quot; toe

     *bijvoorbeeld*, `https://localhost:4502/content/sites/mysight/en/mygroup.html`.

* **menu van het Malplaatje van de Groep van 0&rbrace; Gemeenschap**

  Gebruik drop-down om een beschikbaar [&#x200B; malplaatje van de communautaire groep &#x200B;](/help/communities/tools.md) te kiezen.

### Stap 2: Ontwerp {#step-design}

### THEMA VAN DE COMMUNAUTAIRE GROEP {#community-group-theme}

![&#x200B; communitygrouptheme &#x200B;](assets/communitygrouptheme.png)

Het framework gebruikt `Twitter Bootstrap` om een responsief, flexibel ontwerp naar de site te brengen. Een van de vele vooraf geladen thema&#39;s van de Bootstrap kan worden geselecteerd om de geselecteerde communitygroepsjabloon op te maken, of een thema van de Bootstrap kan worden geüpload.

Als deze optie is geselecteerd, wordt het thema bedekt met een ondoorzichtig blauw vinkje.

Het is mogelijk een thema te selecteren dat afwijkt van het thema van de bovenliggende site.

Nadat de communautaire plaats wordt gepubliceerd, is het mogelijk om [&#x200B; de eigenschappen &#x200B;](#modifyinggroupproperties) uit te geven en een verschillend thema te selecteren.

### COMMUNAUTAIRE GROEPSBRANDING {#community-group-branding}

![&#x200B; gemeenschap-groep-branding &#x200B;](assets/community-group-branding.png)

De branding van de communautaire plaats is een beeld dat als kopbal over de bovenkant van elke pagina wordt getoond. Het is mogelijk om een banner voor de groep weer te geven die afwijkt van andere sitepagina&#39;s.

Het formaat van de afbeelding moet zo breed zijn als de verwachte weergave van de pagina in de browser en 120 pixels hoog.

Houd rekening met het volgende wanneer u een afbeelding maakt of selecteert:

* De afbeeldingshoogte wordt bijgesneden tot 120 pixels, gemeten vanaf de bovenrand van de afbeelding
* De afbeelding is vastgezet aan de linkerrand van het browservenster
* De afbeelding wordt niet vergroot of verkleind. Dit betekent dat de afbeeldingsbreedte als volgt is:

   * Bij een kleinere breedte dan de breedte van de browser wordt de afbeelding horizontaal herhaald.
   * Als de breedte van de browser groter is, wordt de afbeelding uitgesneden.

### Stap 3: Instellingen {#step-settings}

**MODERATION**

![&#x200B; uitgezochte rollen van het groepslid van de gemeenschap &#x200B;](assets/group-admin.png)

**Communautaire Moderatoren van de Groep**

Door gebrek, wordt de lijst van moderatoren van de oudercommunautaire plaats geërft.

Het is mogelijk om moderatoren specifiek aan de groep toe te voegen. Zoeken naar leden (vanuit publicatieomgeving) om deze toe te voegen als moderatoren

**Beheerders van de Groep**

Door gebrek, is de beheerder van de oudercommunautaire plaats de beheerder voor groepen ook.

Het is echter mogelijk om onafhankelijke groepsbeheerders toe te wijzen. De beheerders van de groep kunnen hun groep (bijvoorbeeld, G1) beheren, en tot een subgroep leiden die onder G1 wordt genest. Zij kunnen verschillende beheerders voor subgroup verder toewijzen.

Een gebruiker U1, daarom, kan een beheerder in een groep G1 en een regelmatige gebruiker in zijn genestelde groep G2 zijn.

**LIDMAATSCHAP**

Met de instelling voor lidmaatschap kunt u een van de drie manieren selecteren om een community-groep te beveiligen.

![&#x200B; gemeenschap-groep-lidmaatschap &#x200B;](assets/community-group-membership.png)

* **Facultatief Lidmaatschap**

  Indien geselecteerd, is de communautaire groep een openbare groep. Siteleden kunnen deelnemen aan de groep en posten zonder expliciet deel te nemen aan de groep. Standaard is geselecteerd.

* **Vereist Lidmaatschap**

  Indien geselecteerd, is de communautaire groep een open groep. Leden van een Community-site kunnen de inhoud van de groep bekijken, maar moeten zich wel bij de groep voegen om inhoud te posten. Leden kunnen deelnemen door de knop `Join` in de publicatieomgeving te selecteren. Standaard is niet geselecteerd.

* **Beperkt Lidmaatschap**

  Indien geselecteerd, is de communautaire groep een geheime groep. De leden van de Gemeenschap moeten uitdrukkelijk worden uitgenodigd. Uitgenodigde leden worden ingevoerd in het zoekvak. De leden kunnen later worden toegevoegd gebruikend de [&#x200B; leden en Groepen consoles &#x200B;](/help/communities/members.md) het auteursmilieu. Standaard is niet geselecteerd.

**MINIATUUR**

![&#x200B; gemeenschap-groep-duimnagel &#x200B;](assets/community-group-thumbnail.png)

De miniatuur is een afbeelding die bij het ontwerpen en publiceren voor de groep moet worden weergegeven.

De optimale grootte voor een groepsafbeelding is 170 x 90 pixels in een ondersteunde afbeeldingsindeling (zoals JPG of PNG).

Als er geen afbeelding wordt toegevoegd, wordt een standaardafbeelding weergegeven.

![&#x200B; duimnagel-beeld &#x200B;](assets/thumbnail-image.png)

### Stap 4: Groep maken {#step-create-group}

![&#x200B; gemeenschap-creeer-groep &#x200B;](assets/community-create-group.png)

Als om het even welke aanpassingen nodig zijn, gebruik de **Achtergrond** knoop om hen te maken.

Zodra **creeer** wordt geselecteerd en begonnen, kan het proces om de groep tot stand te brengen niet worden onderbroken.

Wanneer het proces voltooit, wordt de kaart voor de nieuwe subcommunityplaats (groep) getoond in de console van de Groepen van Plaatsen van Gemeenschappen, waarvan de auteurs pagina inhoud kunnen toevoegen, of de beheerders kunnen de eigenschappen van de plaats wijzigen.

![&#x200B; creeer communautaire groep &#x200B;](assets/create-community-groups.png)

>[!NOTE]
>
>De groep wordt gecreeerd in alle talen, zoals die in [&#x200B; wordt gespecificeerd Stap 1: Het Malplaatje van de Groep van de Gemeenschap &#x200B;](/help/communities/groups.md#step-community-group-template) in de Extra Beschikbare Talen van de Communautaire Groep, in de console van Communautaire Groepen van de respectieve communautaire plaatsen.

## Inhoud groep auteurs {#author-group-content}

![&#x200B; open-plaats &#x200B;](assets/open-site.png)

De pagina-inhoud van een groep kan met dezelfde gereedschappen worden gemaakt als elke andere AEM. Als u de groep wilt openen voor ontwerpen, selecteert u het pictogram Site openen dat wordt weergegeven wanneer u de muisaanwijzer op de groepskaart plaatst.

## Groepseigenschappen wijzigen {#modify-group-properties}

De eigenschappen van een bestaande subcommunitysite die tijdens het maken van een community zijn opgegeven, kunnen worden gewijzigd door het pictogram Site bewerken te selecteren dat wordt weergegeven wanneer u de muisaanwijzer op de groepskaart plaatst:

![&#x200B; geef-plaats uit &#x200B;](assets/edit-site.png)

De details van de volgende eigenschappen passen de beschrijvingen aan die in de [&#x200B; sectie van de Aanmaak van de Groep &#x200B;](#group-creation) worden verstrekt. Alle geneste groepen kunnen worden gewijzigd, ongeacht of ze zijn gemaakt in de publicatieomgeving of in de auteursomgeving.

![&#x200B; gemeenschap-groep-fundamenteel &#x200B;](assets/community-group-basic.png)

### Basis wijzigen {#modify-basic}

Met het BASIC-deelvenster kunt u

* Titel van communautaire groep
* Omschrijving van de communautaire groep

De naam van de communautaire groep mag niet worden gewijzigd.

Het kiezen van een verschillend malplaatje van de communautaire groep zou geen effect op een bestaande communautaire groepsplaats hebben aangezien geen verbinding tussen malplaatjes en plaatsen blijft.

In plaats daarvan, kan de [&#x200B; STRUCTUUR &#x200B;](#modify-structure) van subcommunity worden gewijzigd.

### Structuur wijzigen {#modify-structure}

In het deelvenster STRUCTUUR kunt u de structuur wijzigen die oorspronkelijk is gemaakt op basis van de sjabloon voor een groep met gemeenschappen die is geselecteerd wanneer u de subcommunity-site maakt vanuit de auteur- of publicatieomgeving. Vanuit het deelvenster kunt u het volgende doen:

* De belemmering-en-daling extra [&#x200B; communautaire functies &#x200B;](/help/communities/functions.md) in de plaatsstructuur.
* Bij een instantie van een communautaire functie in de sitestructuur:

   * **`Gear icon`**
Geef montages, met inbegrip van de vertoningstitel, URL, en [&#x200B; bevoorrechte ledengroepen &#x200B;](/help/communities/users.md#privilegedmembersgroups) uit.

   * **`Trashcan icon`**
Verwijder (verwijder) functies uit de sitestructuur.

   * **`Grid icon`**
Wijzig de volgorde van de functies die wordt weergegeven in de navigatiebalk op het hoogste niveau van de site.

>[!CAUTION]
>
>Hoewel de titel van de weergave kan worden gewijzigd zonder neveneffecten, wordt het niet aanbevolen de URL-naam te bewerken van een community-functie die bij een community-site hoort.
>
>Als u bijvoorbeeld de naam van de URL wijzigt, wordt de bestaande UGC niet verplaatst en heeft dit het effect van UGC &#39;verliezen&#39;.

>[!CAUTION]
>
>De groepsfunctie moet ** niet *eerst of de enige* functie in de plaatsstructuur zijn.
>
>Om het even welke andere functie, zoals de [&#x200B; paginafunctie &#x200B;](/help/communities/functions.md#page-function), moet worden omvat en eerst vermeld.

**Voorbeeld: Het toevoegen van een Functie van de Kalender aan een SubCommunity (Groep) Structuur**

![&#x200B; gemeenschap-groep-toe:voegen-kalender &#x200B;](assets/community-group-add-calendar.png)

### Ontwerp wijzigen {#modify-design}

In het deelvenster ONTWERP kunt u het thema wijzigen:

* [Communautair groepsthema](#community-group-theme)
* [Community Group Branding](#community-group-branding)

   * Blader naar de onderkant van het deelvenster, zodat u de afbeelding van het merk kunt wijzigen.

### Instellingen wijzigen {#modify-settings}

Het paneel van Montages staat de capaciteit toe om gemeenschap [&#x200B; moderators &#x200B;](#moderation) toe te voegen.

### Lidmaatschap wijzigen {#modify-membership}

Het [&#x200B; paneel van het LIDMAATSCHAP &#x200B;](#membership) is slechts informatie. Het is niet mogelijk het type van het ingestelde groepslidmaatschap te veranderen, of het facultatief, vereist, of beperkt is.

### Miniatuur wijzigen {#modify-thumbnail}

Het [&#x200B; deelvenster MINIATUUR &#x200B;](#thumbnail) staat toe dat een afbeelding wordt geüpload om de communautaire groep te vertegenwoordigen voor sitebezoekers in de Publish-omgeving en in de console Groepen van de Plaats van Gemeenschappen in de auteursomgeving.

## Publish the Group {#publish-the-group}

![&#x200B; publiceren-plaats &#x200B;](assets/publish-site.png)

Nadat u een community-groep hebt gemaakt of gewijzigd, kunt u de groep publiceren (activeren) door het pictogram `Publish Site` te selecteren.

Nadat de groep is gepubliceerd, wordt het volgende bericht weergegeven:

![&#x200B; groep-gepubliceerde &#x200B;](assets/group-published.png)

>[!CAUTION]
>
>De bovenliggende communitysite en bovenliggende groepen hadden al gepubliceerd moeten zijn.
>
>De site van de community en geneste groepen moeten van boven naar beneden worden gepubliceerd.

## De groep verwijderen {#delete-the-group}

![&#x200B; schrappingspictogram &#x200B;](assets/deleteicon.png)

Verwijder een groep uit de console van de Groepen van de gemeenschap door het pictogram van de Groep van de Schrapping te selecteren, dat wanneer het hangen van muis over de groep verschijnt.

Hierdoor worden alle aan de groep gekoppelde items verwijderd. Alle inhoud van de groep wordt bijvoorbeeld permanent verwijderd en gebruikerslidmaatschappen worden uit het systeem verwijderd.
