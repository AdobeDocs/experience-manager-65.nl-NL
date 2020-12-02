---
title: Console van groepen Gemeenschap
seo-title: Console van groepen Gemeenschap
description: Met de console Groepen kunt u groepen van groepen maken
seo-description: Met de console Groepen kunt u groepen van groepen maken
uuid: 21e2bde3-7354-4193-bcb3-c672c6342252
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: d381ea40-fe49-4d32-bfad-1379c7a02aba
docset: aem65
pagetitle: Community Groups Console
translation-type: tm+mt
source-git-commit: 807a81045fca19ab83b9d7872684a5f8a9ed70f1
workflow-type: tm+mt
source-wordcount: '1676'
ht-degree: 0%

---


# Console {#community-groups-console} voor groepen van gemeenschappen

De console van Groepen verleent toegang tot het creëren van communautaire groepen wanneer [malplaatjestructuur](/help/communities/sites-console.md#step1) [groepenfunctie](/help/communities/functions.md#groups-function) omvat.

* AEM Communities ondersteunt het nesten van groepen binnen andere groepen. Groepnesting is mogelijk wanneer de [structuur van de nieuwe groep](/help/communities/tools-groups.md) de groepfunctie bevat.
* Alleen voor de auteursomgeving is er een wizard voor het maken van groepen die lijkt op de wizard voor het maken van sites.
* Of (of niet) de leden groepen in publiceren milieu kunnen tot stand brengen is het configureerbaar wanneer het toevoegen van een functie van Groepen aan een communautaire plaatsstructuur of een communautaire groepsstructuur.

Van de drie meegeleverde groepssjablonen bevat alleen de sjabloon `Reference Group` een groepfunctie in de structuur.

De verschillende facetten van de communautaire groepen zijn:

* **Maken**: U kunt een nieuwe groep maken op auteur en optioneel op een publicatie-instantie.
* **Besturingselement**: groep kan open of geheim zijn.
* **Nesten**: groep kan nul of meer groepen bevatten.

<!-- This is a 404 on helpx. Please update or remove.
>[!NOTE]
>
>Community groups, created in the publish environment before the [existence of the Community Groups console](/help/communities/version-history.md#featurepack1fp1), will not be listed in the Community Groups console, and thus, are not modifiable using the console.
-->

>[!NOTE]
>
>Deze console van Groepen, slechts toegankelijk van de console van de Plaatsen van Gemeenschappen, moet niet met het lid [console van Groepen](/help/communities/members.md) voor het beheren van lidgroepen worden verward.
>
>Gebruikersgroepen zijn gebruikersgroepen die zijn geregistreerd in de publicatieomgeving en die vanuit de auteursomgeving worden benaderd met de [tunnelservice](/help/communities/deploy-communities.md#tunnel-service-on-author).

## Groep maken {#group-creation}

De console Groepen openen:

* Meld u aan bij de auteur met beheerdersrechten.
* Vanuit globale navigatie: **[!UICONTROL Communities]** > **[!UICONTROL Sites]**.
* Selecteer een bestaande map op de communitysite om deze te openen.
* Selecteer een exemplaar van een communautaire plaats binnen de omslag.

   * De structuur van de site van de community moet een groepfunctie bevatten.
   * Deze schermafbeeldingen zijn afkomstig uit de zelfstudie Aan de slag nadat u [groepen hebt gemaakt voor publicatie](/help/communities/published-site.md).

   ![createGroup](assets/create-group.png)

* Selecteer de map **Groepen** om deze te openen.

   Als deze groep wordt geopend, worden alle bestaande groepen weergegeven, ongeacht of deze groepen bij de auteur of bij de publicatie zijn gemaakt.

   Van deze console van Groepen, is het mogelijk om nieuwe groepen te ontwerpen.

   ![create-new-group](assets/create-new-group.png)

* Selecteer de **Create Group** knoop.

### Stap 1: Communitygroepsjabloon {#step-community-group-template}

![Meertalige groepen van gemeenschappen](assets/multi-lingual-group.png)

* **Titel van communautaire groep**

   Een weergavetitel voor de groep.
De titel wordt op de gepubliceerde site voor de groep weergegeven.

* **Omschrijving van de communautaire groep**

   Een beschrijving van de groep.

* **Hoofdmap van communautaire groep**

   Het hoofdpad naar de groep.
De standaardhoofdmap is de bovenliggende site, maar de hoofdmap kan naar elke locatie binnen de website worden verplaatst. Het wordt afgeraden dit te wijzigen.

* **Extra beschikbaar** menu Talen/talen voor groepen van gemeenschappen

   Gebruik de vervolgkeuzelijst om de beschikbare taal of talen van groepen in de gebruikersgemeenschap te selecteren. In het menu worden alle talen weergegeven waarin de bovenliggende communitysite is gemaakt. Gebruikers kunnen in deze ene stap uit deze talen kiezen om groepen te maken in meerdere landinstellingen. De zelfde groep wordt gecreeerd in veelvoudige gespecificeerde talen in de console van Groepen van de respectieve communautaire plaatsen.

* **Naam van communautaire groep**

   De naam van de basispagina van de groep die in URL verschijnt.

   * Controleer de naam nogmaals omdat deze niet gemakkelijk kan worden gewijzigd nadat de groep is gemaakt.
   * De basis-URL wordt onder `Community Group Name` weergegeven.
   * Voor een geldige URL voegt u &quot;.html&quot; toe
      *bijvoorbeeld*,  `https://localhost:4502/content/sites/mysight/en/mygroup.html`.

* **Community Group** Templatemenu

   Gebruik drop-down om beschikbare [communitygroepmalplaatje](/help/communities/tools.md) te kiezen.

### Stap 2: Ontwerp {#step-design}

### THEMA VAN DE COMMUNAUTAIRE GROEP {#community-group-theme}

![communitygroepthema](assets/communitygrouptheme.png)

Het framework gebruikt [Twitter Bootstrap](https://twitterbootstrap.org/) om de site een responsief, flexibel ontwerp te geven. Een van de vele vooraf geladen Bootstrap-thema&#39;s kan worden geselecteerd om de geselecteerde communitygroepsjabloon op te maken, anders kan een Bootstrap-thema worden geüpload.

Als deze optie is geselecteerd, wordt het thema bedekt met een ondoorzichtig blauw vinkje.

Het is mogelijk een thema te selecteren dat afwijkt van het thema van de bovenliggende site.

Nadat de communitysite is gepubliceerd, is het mogelijk om de eigenschappen [te bewerken en een ander thema te selecteren.](#modifyinggroupproperties)

### COMMUNAUTAIRE GROEPSVERDELING {#community-group-branding}

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

   Indien geselecteerd, is de communautaire groep een open groep. Leden van een Community-site kunnen de inhoud van de groep bekijken, maar moeten zich bij de groep voegen om inhoud te posten. Leden kunnen deelnemen door de knop `Join` in de publicatieomgeving te selecteren. Standaard is niet geselecteerd.

* **Beperkt lidmaatschap**

   Indien geselecteerd, is de communautaire groep een geheime groep. De leden van de Gemeenschap moeten uitdrukkelijk worden uitgenodigd. Uitgenodigde leden worden ingevoerd in het zoekvak. Leden kunnen later worden toegevoegd met de consoles [Leden en Groepen](/help/communities/members.md) van de auteursomgeving. Standaard is niet geselecteerd.

**THUMBNAIL**

![community-group-miniatuur](assets/community-group-thumbnail.png)

De miniatuur is een afbeelding die bij het ontwerpen en publiceren voor de groep moet worden weergegeven.

De optimale grootte voor een groepsafbeelding is 170 x 90 pixels in een ondersteunde afbeeldingsindeling (zoals JPG of PNG).

Als er geen afbeelding wordt toegevoegd, wordt een standaardafbeelding weergegeven.

![miniatuurafbeelding](assets/thumbnail-image.png)

### Stap 4: Groep {#step-create-group} maken

![community-create-group](assets/community-create-group.png)

Als er aanpassingen nodig zijn, gebruikt u de knop **Terug** om deze aan te brengen.

Wanneer **Create** is geselecteerd en gestart, kan het proces voor het maken van de groep niet worden onderbroken.

Wanneer het proces is voltooid, wordt de kaart voor de nieuwe subcommunity-site (groep) weergegeven in de console Sites Group van Communities, vanwaar auteurs pagina-inhoud kunnen toevoegen of beheerders de eigenschappen van de site kunnen wijzigen.

![community-groep maken](assets/create-community-groups.png)

>[!NOTE]
>
>De groep wordt gecreeerd in alle talen, zoals gespecificeerd in [Stap 1: Template](/help/communities/groups.md#step-community-group-template) van de Groep van de Gemeenschap in de Extra Beschikbare Talen van de Groep van de Gemeenschap, in de console van de Groepen Gemeenschap van de respectieve communautaire plaatsen.

## Inhoud auteurgroep {#author-group-content}

![open-site](assets/open-site.png)

De pagina-inhoud van een groep kan met dezelfde gereedschappen worden gemaakt als elke andere AEM. Als u de groep wilt openen voor ontwerpen, selecteert u het pictogram Site openen dat wordt weergegeven wanneer u de muisaanwijzer op de groepskaart plaatst.

## Groepseigenschappen wijzigen {#modify-group-properties}

De eigenschappen van een bestaande subcommunitysite die tijdens het maken van een community zijn opgegeven, kunnen worden gewijzigd door het pictogram Site bewerken te selecteren dat wordt weergegeven wanneer u de muisaanwijzer op de groepskaart plaatst:

![site bewerken](assets/edit-site.png)

De details van de volgende eigenschappen komen overeen met de beschrijvingen in de sectie [Groep maken](#group-creation). Alle geneste groepen kunnen worden gewijzigd, ongeacht of ze zijn gemaakt in de publicatieomgeving of in de auteursomgeving.

![communautaristisch](assets/community-group-basic.png)

### Basis {#modify-basic} wijzigen

Met het BASIC-deelvenster kunt u

* Titel van communautaire groep
* Omschrijving van de communautaire groep

De naam van de communautaire groep mag niet worden gewijzigd.

Het kiezen van een verschillend malplaatje van de communautaire groep zou geen invloed op een bestaande communautaire groepsplaats hebben aangezien geen verbinding tussen malplaatjes en plaatsen blijft.

In plaats daarvan kan de [STRUCTUUR](#modify-structure) van de subcommunity worden gewijzigd.

### Structuur {#modify-structure} wijzigen

Met het deelvenster STRUCTUUR kunt u de structuur wijzigen die u aanvankelijk hebt gemaakt op basis van de sjabloon voor een groep met gemeenschappen die u hebt geselecteerd bij het maken van de subcommunity-site vanuit de auteur- of publicatieomgeving. Vanuit het deelvenster kunt u het volgende doen:

* Sleep extra [communityfuncties](/help/communities/functions.md) naar de sitestructuur.
* Bij een instantie van een communautaire functie in de sitestructuur:

   * **`Gear icon`**
Bewerk instellingen, zoals de titel van de weergave, de URL en  [geprivilegieerde ledengroepen](/help/communities/users.md#privilegedmembersgroups).

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
>De groepsfunctie moet *niet* eerst of de enige functie *in de sitestructuur zijn.*
>
>Elke andere functie, zoals de [paginafunctie](/help/communities/functions.md#page-function), moet worden opgenomen en als eerste worden vermeld.

**Voorbeeld: Een kalenderfunctie toevoegen aan een subcommunautaire (Groep) structuur**

![community-group-add-agenda](assets/community-group-add-calendar.png)

### Ontwerp {#modify-design} wijzigen

In het deelvenster ONTWERP kunt u het thema wijzigen:

* [Communautair groepsthema](#community-group-theme)
* [Community Group Branding](#community-group-branding)

   * Schuif naar de onderkant van het deelvenster om de afbeelding van het merk te wijzigen.

### Instellingen {#modify-settings} wijzigen

Met het deelvenster INSTELLINGEN kunt u community [moderators](#moderation) toevoegen.

### Lidmaatschap {#modify-membership} wijzigen

Het deelvenster [LIDMAATSCHAP](#membership) is alleen ter informatie. Het is niet mogelijk om het type groepslidmaatschap dat is ingesteld, te wijzigen, ongeacht of het optioneel, vereist of beperkt is.

### Miniatuur {#modify-thumbnail} wijzigen

Met het deelvenster [MINIATUUR](#thumbnail) kan een afbeelding worden geüpload om de community-groep weer te geven voor sitebezoekers in de publicatieomgeving en in de console Groepen van de Communitysite in de auteuromgeving.

## De groep {#publish-the-group} publiceren

![publicatiesite](assets/publish-site.png)

Nadat u een community-groep hebt gemaakt of gewijzigd, kunt u de groep publiceren (activeren) door het pictogram `Publish Site` te selecteren.

Zodra de groep met succes wordt gepubliceerd, zal een bericht verschijnen:

![in groep gepubliceerd](assets/group-published.png)

>[!CAUTION]
>
>De bovenliggende communitysite en bovenliggende groepen hadden al gepubliceerd moeten zijn.
>
>De site van de community en geneste groepen moeten van boven naar beneden worden gepubliceerd.

## De groep {#delete-the-group} verwijderen

![verwijderpictogram](assets/deleteicon.png)

Verwijder een groep uit de console van de Groepen van de gemeenschap door het pictogram van de Groep van de Schrapping te selecteren, dat wanneer het hangen van muis over de groep verschijnt.

Hierdoor worden alle aan de groep gekoppelde items verwijderd. Alle inhoud van de groep wordt bijvoorbeeld permanent verwijderd en gebruikerslidmaatschappen worden uit het systeem verwijderd.
