---
title: Kalenderfunctie
seo-title: Kalenderfunctie
description: Biedt informatie over een communautaire gebeurtenis in een kalenderindeling
seo-description: Biedt informatie over een communautaire gebeurtenis in een kalenderindeling
uuid: 262f6afa-d8aa-4815-8440-a8ed5668c76d
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 70fa0b9c-cb98-45c4-9c94-bef4a9f3741e
docset: aem65
translation-type: tm+mt
source-git-commit: f375b40c084ee363757b78c602091f38524b8b03
workflow-type: tm+mt
source-wordcount: '1170'
ht-degree: 0%

---


# Kalenderfunctie {#calendar-feature}

## Inleiding {#introduction}

De kalenderfunctie biedt ondersteuning voor het verschaffen van informatie over gebeurtenissen van de gebruikersgemeenschap in een kalendernotatie aan alle bezoekers van de site of alleen aangemeld bij bezoekers van de site (leden van de gemeenschap), terwijl alleen geautoriseerde leden gebeurtenissen mogen toevoegen.

In deze sectie van de documentatie wordt beschreven

* De kalenderfunctie toevoegen aan een AEM-site
* Configuratie-instellingen voor `Calendar`-componenten

## Een kalender toevoegen aan een pagina {#adding-a-calendar-to-a-page}

Als u een `Calendar`-component in de ontwerpmodus aan een pagina wilt toevoegen, gebruikt u de componentbrowser om te zoeken naar

* `Communities / Calendar`

en sleep het naar de juiste positie op een pagina, zoals een positie ten opzichte van de functie die gebruikers kunnen bekijken.

Voor noodzakelijke informatie, bezoek [de Grondbeginselen van Componenten van Gemeenschappen](/help/communities/basics.md).

Als de [vereiste client-side bibliotheken](/help/communities/calendar-basics-for-developers.md#essentials-for-client-side) worden opgenomen, wordt de `Calendar`-component op deze manier weergegeven.

![agendacomponent](assets/calendar-component.png)

### Kalender {#configuring-calendar} configureren

Selecteer de geplaatste `Calendar` component en selecteer `Configure` pictogram dat het Edit dialoog opent.

![vormen](assets/configure-new.png)

![configure-Kalender](assets/configure-calendar1.png)

#### Tabblad Instellingen {#settings-tab}

Geef op het tabblad **Instellingen** op of labels mogen worden toegepast op kalenderitems.

* **Gebeurtenissen per pagina**

   Hiermee definieert u het aantal gebeurtenissen dat per pagina wordt weergegeven. De standaardwaarde is 10.

* **Gematigd**

   Als deze optie is ingeschakeld, moet het posten van kalendergebeurtenissen en opmerkingen worden goedgekeurd voordat deze op een publicatiesite worden weergegeven. De optie Standaard is uitgeschakeld.

* **Gesloten**

   Als deze optie is ingeschakeld, wordt de kalender gesloten voor nieuwe gebeurtenisitems en opmerkingen. De optie Standaard is uitgeschakeld.

* **RTF-editor**

   Als deze optie is ingeschakeld, kunnen kalendergebeurtenissen en opmerkingen worden ingevoerd met een markering. Standaard is ingeschakeld.

* **Tags toestaan**

   Als deze optie is ingeschakeld, kunnen leden labellabels toevoegen aan de gebeurtenissen die ze posten (zie **Tagveld** tabblad). Standaard is ingeschakeld.

* **Uploaden van bestanden toestaan**

   Als deze optie is ingeschakeld, staat u toe dat bestandsbijlagen worden toegevoegd aan een agendagebeurtenis of -opmerking. Standaard is ingeschakeld.

* **Volgen toestaan**

   Als deze optie is ingeschakeld, kunnen leden gebeurtenissen volgen die naar de kalender zijn gepost. Standaard is ingeschakeld.

* **Max. bestandsgrootte**

   Alleen relevant als `Allow File Uploads` is ingeschakeld. Met dit veld wordt de grootte (in bytes) van een ge??pload bestand beperkt. De standaardwaarde is 104857600 (10 MB).

* **Toegestane bestandstypen**

   Alleen relevant als `Allow File Uploads` is ingeschakeld. Een door komma&#39;s gescheiden lijst met bestandsextensies met het &quot;punt&quot;-scheidingsteken. Bijvoorbeeld: .jpg, .jpeg, .png, .doc, .docx, .pdf. Als er bestandstypen zijn opgegeven, mogen de niet opgegeven bestandstypen niet worden ge??pload. De standaardinstelling is niet opgegeven, zodat alle bestandstypen zijn toegestaan.

* **Maximale bestandsgrootte afbeelding bijvoegen**

   Alleen relevant als Uploaden van bestand toestaan is ingeschakeld. Het maximum aantal bytes dat een ge??ploade afbeeldingsbestand kan hebben. De standaardwaarde is 2097152****(2 MB).

* **Toegestane omslagafbeeldingstypen**

   Een door komma&#39;s gescheiden lijst met extensies voor afbeeldingsbestanden met het &quot;punt&quot;-scheidingsteken. De standaardwaarde is `.jpg,.jpeg,.png,.gif,.bmp`.

* **Reacties met verbindingen toestaan**

   Als deze optie is ingeschakeld, kunt u reacties op opmerkingen die zijn geplaatst voor de agendagebeurtenis toestaan. Standaard is ingeschakeld.

* **Gebruikers toestaan opmerkingen en gebeurtenissen te verwijderen**

   Als deze optie is ingeschakeld, kunnen leden de opmerkingen en kalendergebeurtenissen die ze hebben gepost, verwijderen. De standaardinstelling is** ** ingeschakeld.

* **Stemmen toestaan**

   Indien ingeschakeld, neemt u de functie Stemmen op met een agendagebeurtenis. Standaard is ingeschakeld.

* **Broodkruimels tonen**

   Breedkruimels tonen op gebeurtenispagina. Standaard is ingeschakeld.

* **Filter datumbereik**

   Definieert het aantal dagen dat aan de huidige datum wordt toegevoegd om de waarde &quot;Aan&quot; van het filter voor de paginalijst van kalendergebeurtenissen te berekenen. Het standaardnummer is 30.

* **Aanbevolen inhoud toestaan**

   Als deze optie is ingeschakeld, kan het idee worden ge??dentificeerd als [aanbevolen inhoud](/help/communities/featured.md). De optie Standaard is uitgeschakeld.

Onder **De Moderatie van de Gebruiker** lusje, specificeer hoe de geposte onderwerpen en de antwoorden (gebruiker geproduceerde inhoud) worden beheerd. Zie [Door gebruiker gegenereerde inhoud modereren](/help/communities/moderate-ugc.md) voor meer informatie.

#### Tabblad Gebruikersmodernisering {#user-moderation-tab}

* **Posten weigeren**

   Als deze optie wordt ingeschakeld, zullen de verantwoordelijken van de leden hun functie kunnen ontkennen en voorkomen dat de functie op het openbare forum verschijnt. Standaard is ingeschakeld.

* **Gebeurtenissen sluiten/opnieuw openen**

   Als deze optie ingeschakeld is, kunnen vertrouwde moderatoren van leden een gebeurtenis sluiten voor verdere bewerkingen en opmerkingen, en kunnen ze ook een gebeurtenis opnieuw openen. Standaard is ingeschakeld.

* **Vlagberichten**

   Als deze optie is ingeschakeld, kunnen leden gebeurtenissen of opmerkingen van anderen als ongeschikt markeren. Standaard is ingeschakeld.

* **Lijst met redenen voor vlag**

   Als deze optie is ingeschakeld, kunnen leden in een vervolgkeuzelijst kiezen waarom zij een gebeurtenis of opmerking als ongeschikt aanmerken. De optie Standaard is uitgeschakeld.

* **Reden voor aangepaste vlag**

   Als deze optie is ingeschakeld, kunnen leden hun eigen reden opgeven om een gebeurtenis of opmerking als ongeschikt aan te duiden. De optie Standaard is uitgeschakeld.

* **Moderniseringsdrempel**

   Voer het aantal keren in dat een gebeurtenis of opmerking moet worden gemarkeerd door leden voordat moderatoren op de hoogte worden gesteld. De standaardwaarde is 1 (????n keer).

* **Limiet voor markering**

   Voer het aantal keren in dat een gebeurtenis of opmerking moet worden gemarkeerd voordat deze wordt verborgen in de openbare weergave. Indien ingesteld op -1, wordt het gemarkeerde onderwerp of de opmerking nooit verborgen in de openbare weergave. Anders, moet dit aantal groter dan of gelijk aan de Drempel van de Moderatie zijn. De standaardwaarde is 5.

#### Tabblad {#tag-field-tab} voor tagveld

Onder het tabblad **Tagveld** worden de tags die kunnen worden toegepast, indien toegestaan onder het tabblad **Instellingen**, beperkt op basis van de gekozen naamruimten.

* **Toegestane naamruimten**

   Relevant als `Allow Tagging` is ingeschakeld onder het tabblad **Instellingen**. De tags die kunnen worden toegepast, zijn beperkt tot de tags binnen de geselecteerde naamruimtecategorie??n. De lijst met naamruimten bevat &#39;Standaardtags&#39; (de standaardnaamruimte) en &#39;Alle tags opnemen&#39;. De standaardwaarde is niet ingeschakeld, hetgeen betekent dat alle naamruimten zijn toegestaan.

* **Suggestiegrenswaarde**

   Voer het aantal tags in dat moet worden weergegeven als suggestie aan het lid dat naar het forum post. De standaardwaarde is **-**1 (geen limieten).

>[!NOTE]
>
>Bezoek [Tags beheren](/help/sites-administering/tags.md) voor informatie over het toevoegen van een nieuwe naamruimte voor tags (taxonomie).

#### Tabblad Vertaling {#translation-tab}

Als op het tabblad **Vertaling** vertaling is ingeschakeld voor de site van de gebruikersgemeenschap, kan de vertaling zo worden ingesteld dat de volledige thread (gebeurtenis en opmerkingen) wordt vertaald in plaats van specifieke posts.

* **Alles vertalen**

   Als deze optie is ingeschakeld, worden de gebeurtenis en de opmerkingen vertaald naar de voorkeurstaal van de gebruiker. Standaard is ingeschakeld.

## Ervaring {#site-visitor-experience} voor bezoekers van site

In de publicatieomgeving wordt met de kalenderfunctie een zoekveld weergegeven met een standaarddatumbereik en alle kalendergebeurtenissen die binnen dat bereik vallen.

Wanneer een agendagebeurtenis is geselecteerd, worden de details, beschrijving en opmerkingen van de kalendergebeurtenis weergegeven.

Andere vaardigheden hangen af van het feit of de bezoeker van de site een moderator, beheerder, lid van de gemeenschap, geprivilegieerd lid of anoniem is.

### Moderatoren en beheerders {#moderators-and-administrators}

Wanneer de ondertekende binnen gebruiker moderator of beheerdervoorrechten heeft, kunnen zij [moderatietaken](/help/communities/moderate-ugc.md) (zoals toegelaten door de configuratie van de component) op alle kalendergebeurtenissen en commentaren uitvoeren die aan een gebeurtenis worden gepost.

![moderatorvisie](assets/moderators-view.png)

#### Leden {#members}

Wanneer de aangemelde gebruiker een communitylid of [geprivilegieerd lid](/help/communities/users.md#privileged-members-group) is (afhankelijk van de configuratie), kunnen ze `New Event` selecteren om een nieuwe agendagebeurtenis te maken en te plaatsen.

Zij kunnen met name:

* Een nieuwe agendagebeurtenis maken
* Opmerkingen verzenden naar een agendagebeurtenis
* Een eigen agendagebeurtenis of commentaar bewerken
* Verwijder hun eigen agendagebeurtenis of commentaar
* Andere kalendergebeurtenissen of opmerkingen markeren

![create-event](assets/configure-calendar2.png)

![gebeurtenis-post](assets/configure-calendar3.png)

#### Anonieme {#anonymous}

Sitebezoekers die niet zijn aangemeld, kunnen alleen geposte kalendergebeurtenissen lezen, deze vertalen indien deze worden ondersteund, maar kunnen geen gebeurtenis of opmerking toevoegen en de gebeurtenissen of opmerkingen van anderen niet markeren.

![anonieme gebruikersweergave](assets/anonymous-user-view1.png)

## Aanvullende informatie {#additional-information}

Meer informatie vindt u op de pagina [Kalender Essentials](/help/communities/calendar-basics-for-developers.md) voor ontwikkelaars.

Zie [Door gebruiker gegenereerde inhoud modereren](/help/communities/moderate-ugc.md) voor de moderatie van kalendergebeurtenissen en opmerkingen.

Zie [Door gebruiker gegenereerde inhoud labelen](/help/communities/tag-ugc.md) voor het labelen van agendagebeurtenissen en opmerkingen.

Zie [Door gebruiker gegenereerde inhoud omzetten](/help/communities/translate-ugc.md) voor een vertaling van kalendergebeurtenissen en opmerkingen.
