---
title: Kalenderfunctie
description: Leer hoe de functie Kalender informatie over gebeurtenissen van de gebruikersgemeenschap in een kalenderformaat verstrekt.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
docset: aem65
exl-id: c9b34b00-525d-4ca3-bd18-11bb7ce66787
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '1158'
ht-degree: 0%

---

# Kalenderfunctie {#calendar-feature}

## Inleiding {#introduction}

De kalenderfunctie biedt ondersteuning voor het verschaffen van informatie over gebeurtenissen van de gebruikersgemeenschap in een kalendernotatie aan alle bezoekers van de site of alleen aangemeld bij bezoekers van de site (leden van de gemeenschap), terwijl alleen geautoriseerde leden gebeurtenissen mogen toevoegen.

In deze sectie van de documentatie wordt beschreven

* De kalenderfunctie toevoegen aan een AEM-site
* Configuratie-instellingen voor `Calendar` componenten

## Een kalender toevoegen aan een pagina {#adding-a-calendar-to-a-page}

Als u een `Calendar` van een component aan een pagina op auteurswijze, gebruik componentenbrowser om van

* `Communities / Calendar`

En sleep het op zijn plaats op een pagina, zoals een positie met betrekking tot de eigenschap voor gebruikers om te herzien.

Voor de nodige informatie gaat u naar [Grondbeginselen van Community-componenten](/help/communities/basics.md).

Wanneer de [vereiste clientbibliotheken](/help/communities/calendar-basics-for-developers.md#essentials-for-client-side) worden opgenomen, is dit hoe `Calendar` wordt weergegeven.

![agendacomponent](assets/calendar-component.png)

### Kalender configureren {#configuring-calendar}

Selecteer de geplaatste `Calendar` zodat u toegang hebt tot `Configure` wordt het dialoogvenster Bewerken geopend.

![vormen](assets/configure-new.png)

![configure-Kalender](assets/configure-calendar1.png)

#### Het tabblad Instellingen {#settings-tab}

Onder de **Instellingen** , geeft u op of labels mogen worden toegepast op kalenderitems.

* **Gebeurtenissen per pagina**

  Hiermee definieert u het aantal gebeurtenissen dat per pagina wordt weergegeven. De standaardwaarde is 10.

* **Gematigd**

  Als deze optie is ingeschakeld, moet het posten van kalendergebeurtenissen en opmerkingen worden goedgekeurd voordat ze op een publicatiesite worden weergegeven. De optie Standaard is uitgeschakeld.

* **Gesloten**

  Als deze optie is ingeschakeld, wordt de kalender gesloten voor nieuwe gebeurtenisitems en opmerkingen. De optie Standaard is uitgeschakeld.

* **RTF-editor**

  Als deze optie is ingeschakeld, kunnen kalendergebeurtenissen en opmerkingen worden ingevoerd met een markering. Standaard is ingeschakeld.

* **Tags toestaan**

  Als deze optie is ingeschakeld, kunnen leden labels toevoegen aan de gebeurtenissen die ze posten (zie **Veld code** ). Standaard is ingeschakeld.

* **Uploaden van bestanden toestaan**

  Als deze optie is ingeschakeld, staat u toe dat bestandsbijlagen worden toegevoegd aan een agendagebeurtenis of -opmerking. Standaard is ingeschakeld.

* **Volgen toestaan**

  Als deze optie is ingeschakeld, kunnen leden gebeurtenissen volgen die naar de kalender zijn gepost. Standaard is ingeschakeld.

* **Max. bestandsgrootte**

  Alleen relevant als `Allow File Uploads` is ingeschakeld. Dit veld beperkt de grootte (in bytes) van een geüpload bestand. De standaardwaarde is 104857600 (10 MB).

* **Toegestane bestandstypen**

  Alleen relevant als `Allow File Uploads` is ingeschakeld. Een door komma&#39;s gescheiden lijst met bestandsextensies met het scheidingsteken &#39;punt&#39;. Bijvoorbeeld .jpg, .jpeg, .png, .doc, .docx, .pdf. Als er bestandstypen zijn opgegeven, kunnen deze niet worden geüpload. De standaardinstelling is niet opgegeven, zodat alle bestandstypen zijn toegestaan.

* **Maximale bestandsgrootte afbeelding bijvoegen**

  Alleen relevant als Uploaden van bestand toestaan is ingeschakeld. Het maximum aantal bytes dat een geüploade afbeeldingsbestand kan hebben. De standaardwaarde is 2097152****(2 MB).

* **Toegestane omslagafbeeldingstypen**

  Een door komma&#39;s gescheiden lijst met extensies voor afbeeldingsbestanden met het puntscheidingsteken. Standaard is `.jpg,.jpeg,.png,.gif,.bmp`.

* **Reacties met verbindingen toestaan**

  Als deze optie is ingeschakeld, kunt u reacties op opmerkingen die zijn geplaatst voor de agendagebeurtenis toestaan. Standaard is ingeschakeld.

* **Gebruikers toestaan opmerkingen en gebeurtenissen te verwijderen**

  Als deze optie is ingeschakeld, kunnen leden de opmerkingen en kalendergebeurtenissen verwijderen die ze hebben gepost. Standaard is ingeschakeld.

* **Stemmen toestaan**

  Indien ingeschakeld, neemt u de functie Stemmen op met een agendagebeurtenis. Standaard is ingeschakeld.

* **Broodkruimels tonen**

  Breedkruimels tonen op gebeurtenispagina. Standaard is ingeschakeld.

* **Filter datumbereik**

  Definieert het aantal dagen dat aan de huidige datum wordt toegevoegd om de waarde &quot;Aan&quot; van het filter voor de paginanummering van kalendergebeurtenissen te berekenen. Het standaardnummer is 30.

* **Aanbevolen inhoud toestaan**

  Als deze optie ingeschakeld is, kan het idee worden herkend als [aanbevolen inhoud](/help/communities/featured.md). De optie Standaard is uitgeschakeld.

Onder de **Moderatie gebruiker** tabblad, geeft u op hoe de geposte onderwerpen en antwoorden (door de gebruiker gegenereerde inhoud) worden beheerd. Zie voor meer informatie [Door gebruiker gegenereerde inhoud modereren](/help/communities/moderate-ugc.md).

#### Tabblad Gebruikersmodernisering {#user-moderation-tab}

* **Posten weigeren**

  Indien deze optie is ingeschakeld, mogen de moderatoren van de leden die vertrouwen, posten ontkennen en voorkomen dat de post op het openbare forum verschijnt. Standaard is ingeschakeld.

* **Gebeurtenissen sluiten/opnieuw openen**

  Als deze optie ingeschakeld is, kunnen vertrouwde moderatoren van leden een gebeurtenis sluiten voor verdere bewerkingen en opmerkingen, en kunnen ze ook een gebeurtenis opnieuw openen. Standaard is ingeschakeld.

* **Vlagberichten**

  Als deze optie is ingeschakeld, kunnen leden gebeurtenissen of opmerkingen van anderen als ongeschikt markeren. Standaard is ingeschakeld.

* **Lijst met redenen voor vlag**

  Als deze optie is ingeschakeld, kunnen leden in een vervolgkeuzelijst kiezen waarom zij een gebeurtenis of opmerking als ongeschikt aanmerken. De optie Standaard is uitgeschakeld.

* **Reden voor aangepaste vlag**

  Als deze optie is ingeschakeld, kunnen leden hun eigen reden opgeven om een gebeurtenis of opmerking als ongeschikt aan te duiden. De optie Standaard is uitgeschakeld.

* **Moderniseringsdrempel**

  Voer het aantal keren in dat een gebeurtenis of opmerking moet worden gemarkeerd door leden voordat moderatoren op de hoogte worden gesteld. De standaardwaarde is 1 (één keer).

* **Limiet voor markering**

  Voer het aantal keren in dat een gebeurtenis of opmerking moet worden gemarkeerd voordat deze wordt verborgen in de openbare weergave. Indien ingesteld op -1, wordt het gemarkeerde onderwerp of de opmerking nooit verborgen in de openbare weergave. Anders, moet dit aantal groter dan of gelijk aan de Drempel van de Moderatie zijn. De standaardwaarde is 5.

#### Tabblad Tagveld {#tag-field-tab}

Onder de **Veld code** , de tags die kunnen worden toegepast, indien toegestaan onder de **Instellingen** zijn beperkt op basis van de gekozen naamruimten.

* **Toegestane naamruimten**

  Relevant indien `Allow Tagging` wordt gecontroleerd onder de **Instellingen** tab. De tags die kunnen worden toegepast, zijn beperkt tot de tags binnen de geselecteerde naamruimtecategorieën. De lijst met naamruimten bevat &quot;Standaardtags&quot; (de standaardnaamruimte) en &quot;Alle tags opnemen&quot;. De standaardwaarde is niet ingeschakeld, hetgeen betekent dat alle naamruimten zijn toegestaan.

* **Suggestiegrenswaarde**

  Voer het aantal tags in dat moet worden weergegeven als suggestie aan het lid dat naar het forum post. De standaardwaarde is **-**1 (geen limieten).

>[!NOTE]
>
>Bezoek [Tags beheren](/help/sites-administering/tags.md) Hier kunt u leren hoe u een naamruimte voor tags (taxonomie) kunt toevoegen.

#### Tabblad Vertaling {#translation-tab}

Onder de **Vertaling** tab, als vertaling voor de communautaire plaats wordt toegelaten, kan de vertaling worden geplaatst om de volledige draad (gebeurtenis en commentaren) in plaats van specifieke posten te vertalen.

* **Alles vertalen**

  Als deze optie is ingeschakeld, worden de gebeurtenis en de opmerkingen vertaald naar de voorkeurstaal van de gebruiker. Standaard is ingeschakeld.

## Ervaring met sitebezoekers {#site-visitor-experience}

In de publicatieomgeving wordt met de kalenderfunctie een zoekveld weergegeven met een standaarddatumbereik en alle kalendergebeurtenissen die binnen dat bereik vallen.

Wanneer een agendagebeurtenis is geselecteerd, worden de details, beschrijving en opmerkingen van de kalendergebeurtenis weergegeven.

Andere vaardigheden hangen af van het feit of de bezoeker van de site een moderator, beheerder, lid van de gemeenschap, geprivilegieerd lid of anoniem is.

### Moderatoren en beheerders {#moderators-and-administrators}

Wanneer de ondertekende in gebruiker moderator of beheerdervoorrechten heeft, kunnen zij uitvoeren [matigingstaken](/help/communities/moderate-ugc.md) (zoals toegestaan door de configuratie van de component) voor alle kalendergebeurtenissen en opmerkingen die naar een gebeurtenis zijn gepost.

![moderatorvisie](assets/moderators-view.png)

#### Leden {#members}

Wanneer de gebruiker met de aanmelding lid is van de gemeenschap of [bevoorrecht lid](/help/communities/users.md#privileged-members-group) (afhankelijk van de configuratie), kunnen zij selecteren `New Event` om een nieuwe agendagebeurtenis te maken en te plaatsen.

Zij kunnen met name:

* Een agendagebeurtenis maken
* Opmerkingen verzenden naar een kalendergebeurtenis
* Een eigen agendagebeurtenis of commentaar bewerken
* Verwijder hun eigen agendagebeurtenis of commentaar
* Andere kalendergebeurtenissen of opmerkingen markeren

![create-event](assets/configure-calendar2.png)

![gebeurtenis-post](assets/configure-calendar3.png)

#### Anoniem {#anonymous}

Sitebezoekers die niet zijn aangemeld, kunnen alleen geposte kalendergebeurtenissen lezen, deze vertalen indien deze worden ondersteund, maar kunnen geen gebeurtenis of opmerking toevoegen en de gebeurtenissen of opmerkingen van anderen niet markeren.

![anonieme gebruikersweergave](assets/anonymous-user-view1.png)

## Aanvullende informatie {#additional-information}

Meer informatie is te vinden op de [Essentiële elementen van agenda](/help/communities/calendar-basics-for-developers.md) pagina voor ontwikkelaars.

Zie voor de moderatie van kalendergebeurtenissen en opmerkingen [Door gebruiker gegenereerde inhoud modereren](/help/communities/moderate-ugc.md).

Zie voor het labelen van kalendergebeurtenissen en opmerkingen [Door gebruiker gegenereerde inhoud labelen](/help/communities/tag-ugc.md).

Zie voor een vertaling van agendagebeurtenissen en opmerkingen [Door de gebruiker gegenereerde inhoud vertalen](/help/communities/translate-ugc.md).
