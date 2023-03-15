---
title: Console van groepen Gemeenschap
seo-title: Community Groups Console
description: Met de console Groepen kunt u groepen van groepen maken
seo-description: Groups console lets you create Community groups
uuid: 21e2bde3-7354-4193-bcb3-c672c6342252
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: d381ea40-fe49-4d32-bfad-1379c7a02aba
docset: aem65
pagetitle: Community Groups Console
role: Admin
exl-id: ef371ff8-6b4f-4e5a-98fb-d7c274927c46
source-git-commit: 1074843a0105df39382b64defe66fc262986b9c9
workflow-type: tm+mt
source-wordcount: '1676'
ht-degree: 0%

---

# Console van groepen Gemeenschap {#community-groups-console}

De console van Groepen verleent toegang tot het creëren van communautaire groepen wanneer een communautaire plaats [sjabloonstructuur](/help/communities/sites-console.md#step1) bevat de [group, functie](/help/communities/functions.md#groups-function).

* AEM Communities ondersteunt het nesten van groepen binnen andere groepen. Het nesten van een groep is mogelijk wanneer de [structuur van de nieuwe groep](/help/communities/tools-groups.md) bevat de groepfunctie.
* Alleen voor de auteursomgeving is er een wizard voor het maken van groepen die lijkt op de wizard voor het maken van sites.
* Of (of niet) de leden groepen in publiceren milieu kunnen tot stand brengen is het configureerbaar wanneer het toevoegen van een functie van Groepen aan een communautaire plaatsstructuur of een communautaire groepsstructuur.

Van de drie opgenomen groepssjablonen is alleen het `Reference Group` sjabloon bevat een groepfunctie in de structuur.

De verschillende facetten van de communautaire groepen zijn:

* **Maken**: U kunt een nieuwe groep maken op auteur en optioneel op een publicatie-instantie.
* **Control**: groep kan open of geheim zijn.
* **Nesten**: groep kan nul of meer groepen bevatten.

<!-- This is a 404 on helpx. Please update or remove.
>[!NOTE]
>
>Community groups, created in the publish environment before the [existence of the Community Groups console](/help/communities/version-history.md#featurepack1fp1), will not be listed in the Community Groups console, and thus, are not modifiable using the console.
-->

>[!NOTE]
>
>Deze console van Groepen, slechts toegankelijk van de console van de Plaatsen van Gemeenschappen, moet niet met het lid worden verward [Groepsconsole](/help/communities/members.md) voor het beheren van ledengroepen.
>
>De groepen van het lid zijn gebruikersgroepen die in het publicatiemilieu worden geregistreerd en van het auteursmilieu worden betreden gebruikend [tunneldienst](/help/communities/deploy-communities.md#tunnel-service-on-author).

## Groep maken {#group-creation}

De console Groepen openen:

* Meld u aan bij de auteur met beheerdersrechten.
* Vanuit globale navigatie: **[!UICONTROL Communities]** > **[!UICONTROL Sites]**.
* Selecteer een bestaande map op de communitysite om deze te openen.
* Selecteer een exemplaar van een communautaire plaats binnen de omslag.

   * De structuur van de site van de community moet een groepfunctie bevatten.
   * Deze schermafbeeldingen zijn afkomstig uit de zelfstudie Aan de slag na [groepen maken voor publicatie](/help/communities/published-site.md).

   ![createGroup](assets/create-group.png)

* Selecteer **Map Groepen** om het te openen.

   Als deze groep wordt geopend, worden alle bestaande groepen weergegeven, ongeacht of deze groepen bij de auteur of bij de publicatie zijn gemaakt.

   Van deze console van Groepen, is het mogelijk om nieuwe groepen te ontwerpen.

   ![create-new-group](assets/create-new-group.png)

* Selecteer **Groep maken** knop.

### Stap 1: Template voor communautaire groep {#step-community-group-template}

![Meertalige groepen van gemeenschappen](assets/multi-lingual-group.png)

* **Titel van communautaire groep**

   Een weergavetitel voor de groep.
De titel wordt op de gepubliceerde site voor de groep weergegeven.

* **Omschrijving van de communautaire groep**

   Een beschrijving van de groep.

* **Hoofdmap van communautaire groep**

   Het hoofdpad naar de groep.
De standaardhoofdmap is de bovenliggende site, maar de hoofdmap kan naar elke locatie binnen de website worden verplaatst. Het wordt afgeraden dit te wijzigen.

* **Aanvullende beschikbare talen van de communautaire groep** menu

   Gebruik de vervolgkeuzelijst om de beschikbare taal of talen van groepen in de gebruikersgemeenschap te selecteren. In het menu worden alle talen weergegeven waarin de bovenliggende communitysite is gemaakt. Gebruikers kunnen in deze ene stap uit deze talen kiezen om groepen te maken in meerdere landinstellingen. De zelfde groep wordt gecreeerd in veelvoudige gespecificeerde talen in de console van Groepen van de respectieve communautaire plaatsen.

* **Naam van communautaire groep**

   De naam van de basispagina van de groep die in URL verschijnt. Gebruik geen onderstrepingstekens (_) en trefwoorden zoals bronnen en configuratie in groepsnaam.

   * Controleer de naam nogmaals omdat deze niet gemakkelijk kan worden gewijzigd nadat de groep is gemaakt.
   * De basis-URL wordt onder de `Community Group Name`.
   * Voor een geldige URL voegt u &quot;.html&quot; toe
      *bijvoorbeeld*, `https://localhost:4502/content/sites/mysight/en/mygroup.html`.

* **Template voor communautaire groep** menu

   Kies in het keuzemenu een beschikbare [communitygroepsjabloon](/help/communities/tools.md).

### Stap 2: Ontwerp {#step-design}

### THEMA VAN DE COMMUNAUTAIRE GROEP {#community-group-theme}

![communitygroepthema](assets/communitygrouptheme.png)

Het kader gebruikt `Twitter Bootstrap` om een ontvankelijk, flexibel ontwerp aan de plaats te brengen. Een van de vele vooraf geladen Bootstrap-thema&#39;s kan worden geselecteerd om de geselecteerde communitygroepsjabloon op te maken, anders kan een Bootstrap-thema worden geüpload.

Als deze optie is geselecteerd, wordt het thema bedekt met een ondoorzichtig blauw vinkje.

Het is mogelijk een thema te selecteren dat afwijkt van het thema van de bovenliggende site.

Nadat de communitysite is gepubliceerd, is het mogelijk om [de eigenschappen bewerken](#modifyinggroupproperties) en selecteer een ander thema.

### COMMUNAUTAIRE BRANDBOEK {#community-group-branding}

![gemeenschapsmerk](assets/community-group-branding.png)

De branding van de communautaire plaats is een beeld dat als kopbal over de bovenkant van elke pagina wordt getoond. Het is mogelijk om een banner voor de groep weer te geven die afwijkt van andere sitepagina&#39;s.

Het formaat van de afbeelding moet zo breed zijn als de verwachte weergave van de pagina in de browser en 120 pixels hoog.

Houd rekening met het volgende wanneer u een afbeelding maakt of selecteert:

* De afbeeldingshoogte wordt bijgesneden tot 120 pixels, gemeten vanaf de bovenrand van de afbeelding
* De afbeelding is vastgezet aan de linkerrand van het browservenster
* De afbeelding wordt niet vergroot of verkleind, zodat de volgende afbeeldingsbreedte wordt gebruikt:

   * Bij een lagere breedte dan de breedte van de browser wordt de afbeelding horizontaal herhaald.
   * Als de breedte van de browser groter is, wordt de afbeelding bijgesneden.

### Stap 3: Instellingen {#step-settings}

**MODERING**

![selecteer de rollen van het groepslid van de gemeenschap](assets/group-admin.png)

**Moderatoren van communautaire groepen**

Door gebrek, wordt de lijst van moderatoren van de oudercommunautaire plaats geërft.

Het is mogelijk moderatoren toe te voegen die specifiek zijn voor de groep. Zoeken naar leden (vanuit publicatieomgeving) om deze toe te voegen als moderatoren

**Groepbeheerders**

Door gebrek, is de beheerder van de oudercommunautaire plaats de beheerder voor groepen ook.

Het is echter mogelijk om onafhankelijke groepsbeheerders toe te wijzen. De beheerders van de groep kunnen hun groep (bijvoorbeeld G1) beheren, en tot een subgroep leiden die onder G1 wordt genest. Zij kunnen verschillende beheerders voor subgroep verder toewijzen.

Een gebruiker U1, daarom, kan een beheerder in een groep G1 en een regelmatige gebruiker in zijn genestelde groep G2 zijn.

**LIDMAATSCHAP**

Met de instelling voor lidmaatschap kunt u een van de drie manieren selecteren om een community-groep te beveiligen.

![lidmaatschap van de gemeenschap](assets/community-group-membership.png)

* **Optioneel lidmaatschap**

   Indien geselecteerd, is de communautaire groep een openbare groep. Siteleden kunnen deelnemen aan de groep en posten zonder expliciet deel te nemen aan de groep. Standaard is geselecteerd.

* **Vereist lidmaatschap**

   Indien geselecteerd, is de communautaire groep een open groep. Leden van een Community-site kunnen de inhoud van de groep bekijken, maar moeten zich bij de groep voegen om inhoud te posten. De leden voegen zich bij door te selecteren `Join` in de publicatieomgeving. Standaard is niet geselecteerd.

* **Beperkt lidmaatschap**

   Indien geselecteerd, is de communautaire groep een geheime groep. De leden van de Gemeenschap moeten uitdrukkelijk worden uitgenodigd. Uitgenodigde leden worden ingevoerd in het zoekvak. Leden kunnen later worden toegevoegd met de [Samenstellingen van leden en groepen](/help/communities/members.md) de auteursomgeving. Standaard is niet geselecteerd.

**THUMBNAIL**

![community-group-miniatuur](assets/community-group-thumbnail.png)

De miniatuur is een afbeelding die bij het ontwerpen en publiceren voor de groep moet worden weergegeven.

De optimale grootte voor een groepsafbeelding is 170 x 90 pixels in een ondersteunde afbeeldingsindeling (zoals JPG of PNG).

Als er geen afbeelding wordt toegevoegd, wordt een standaardafbeelding weergegeven.

![miniatuurafbeelding](assets/thumbnail-image.png)

### Stap 4: Groep maken {#step-create-group}

![community-create-group](assets/community-create-group.png)

Als er aanpassingen nodig zijn, gebruikt u de **Vorige** om ze te maken.

Eenmaal **Maken** is geselecteerd en gestart, kan het proces voor het maken van de groep niet worden onderbroken.

Wanneer het proces is voltooid, wordt de kaart voor de nieuwe subcommunity-site (groep) weergegeven in de console Sites Group van Communities, vanwaar auteurs pagina-inhoud kunnen toevoegen of beheerders de eigenschappen van de site kunnen wijzigen.

![community-groep maken](assets/create-community-groups.png)

>[!NOTE]
>
>De groep wordt gemaakt in alle talen, zoals opgegeven in [Stap 1: Template voor communautaire groep](/help/communities/groups.md#step-community-group-template) in de Aanvullende Beschikbare Talen van de Groep van de Gemeenschap, in de console van de Groepen van de Gemeenschap van de respectieve communautaire plaatsen.

## Inhoud groep auteurs {#author-group-content}

![open-site](assets/open-site.png)

De pagina-inhoud van een groep kan met dezelfde gereedschappen worden gemaakt als elke andere AEM. Als u de groep wilt openen voor ontwerpen, selecteert u het pictogram Site openen dat wordt weergegeven wanneer u de muisaanwijzer op de groepskaart plaatst.

## Groepseigenschappen wijzigen {#modify-group-properties}

De eigenschappen van een bestaande subcommunitysite die tijdens het maken van een community zijn opgegeven, kunnen worden gewijzigd door het pictogram Site bewerken te selecteren dat wordt weergegeven wanneer u de muisaanwijzer op de groepskaart plaatst:

![site bewerken](assets/edit-site.png)

De details van de volgende eigenschappen komen overeen met de beschrijvingen in het dialoogvenster [Groep maken](#group-creation) sectie. Alle geneste groepen kunnen worden gewijzigd, ongeacht of ze zijn gemaakt in de publicatieomgeving of in de auteursomgeving.

![communautaristisch](assets/community-group-basic.png)

### Basis wijzigen {#modify-basic}

Met het BASIC-deelvenster kunt u

* Titel van communautaire groep
* Omschrijving van de communautaire groep

De naam van de communautaire groep mag niet worden gewijzigd.

Het kiezen van een verschillend malplaatje van de communautaire groep zou geen invloed op een bestaande communautaire groepsplaats hebben aangezien geen verbinding tussen malplaatjes en plaatsen blijft.

In plaats daarvan [STRUCTUUR](#modify-structure) van de subgemeenschap kan worden gewijzigd.

### Structuur wijzigen {#modify-structure}

Met het deelvenster STRUCTUUR kunt u de structuur wijzigen die u aanvankelijk hebt gemaakt op basis van de sjabloon voor een groep met gemeenschappen die u hebt geselecteerd bij het maken van de subcommunity-site vanuit de auteur- of publicatieomgeving. Vanuit het deelvenster kunt u het volgende doen:

* Aanvullende slepen en neerzetten [communautaire functies](/help/communities/functions.md) in de sitestructuur.
* Bij een instantie van een communautaire functie in de sitestructuur:

   * **`Gear icon`**
Instellingen bewerken, zoals de weergavetoek, URL en [groepen geprivilegieerde leden](/help/communities/users.md#privilegedmembersgroups).

   * **`Trashcan icon`**
Verwijder (verwijder) functies uit de sitestructuur.

   * **`Grid icon`**
Wijzig de volgorde van de functies die wordt weergegeven op de navigatiebalk op het hoogste niveau van de site.

>[!CAUTION]
>
>Hoewel de titel van de weergave kan worden gewijzigd zonder neveneffecten, wordt het niet aanbevolen de URL-naam te bewerken van een community-functie die bij een community-site hoort.
>
>Als u bijvoorbeeld de naam van de URL wijzigt, wordt de bestaande UGC niet verplaatst, waardoor de UGC verloren gaat.

>[!CAUTION]
>
>De groepfunctie moet *niet* zijn *alleen* in de sitestructuur.
>
>Elke andere functie, zoals de [page, functie](/help/communities/functions.md#page-function), moet worden opgenomen en als eerste worden vermeld.

**Voorbeeld: Een kalenderfunctie toevoegen aan een subcommunautaire (Groep) structuur**

![community-group-add-agenda](assets/community-group-add-calendar.png)

### Ontwerp wijzigen {#modify-design}

In het deelvenster ONTWERP kunt u het thema wijzigen:

* [Communautair groepsthema](#community-group-theme)
* [Community Group Branding](#community-group-branding)

   * Schuif naar de onderkant van het deelvenster om de afbeelding van het merk te wijzigen.

### Instellingen wijzigen {#modify-settings}

Met het deelvenster INSTELLINGEN kunt u community toevoegen [moderator](#moderation).

### Lidmaatschap wijzigen {#modify-membership}

De [LIDMAATSCHAP](#membership) is alleen ter informatie. Het is niet mogelijk om het type groepslidmaatschap dat is ingesteld, te wijzigen, ongeacht of het optioneel, vereist of beperkt is.

### Miniatuur wijzigen {#modify-thumbnail}

De [THUMBNAIL](#thumbnail) kan een afbeelding worden geüpload om de community-groep weer te geven voor sitebezoekers in de publicatieomgeving en in de console Groepen van de Community Site in de auteursomgeving.

## De groep publiceren {#publish-the-group}

![publicatiesite](assets/publish-site.png)

Nadat een community-groep opnieuw is gemaakt of gewijzigd, kunt u de groep publiceren (activeren) door de `Publish Site` pictogram.

Zodra de groep met succes wordt gepubliceerd, zal een bericht verschijnen:

![in groep gepubliceerd](assets/group-published.png)

>[!CAUTION]
>
>De bovenliggende communitysite en bovenliggende groepen hadden al gepubliceerd moeten zijn.
>
>De site van de community en geneste groepen moeten van boven naar beneden worden gepubliceerd.

## De groep verwijderen {#delete-the-group}

![verwijderpictogram](assets/deleteicon.png)

Verwijder een groep uit de console van de Groepen van de gemeenschap door het pictogram van de Groep van de Schrapping te selecteren, dat wanneer het hangen van muis over de groep verschijnt.

Hierdoor worden alle aan de groep gekoppelde items verwijderd. Alle inhoud van de groep wordt bijvoorbeeld permanent verwijderd en gebruikerslidmaatschappen worden uit het systeem verwijderd.
