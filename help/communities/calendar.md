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
source-git-commit: 27a054cc5d502d95c664c3b414d0066c6c120b65

---


# Kalenderfunctie{#calendar-feature}

## Inleiding {#introduction}

De kalenderfunctie biedt ondersteuning voor het verschaffen van informatie over gebeurtenissen van de gebruikersgemeenschap in een kalendernotatie aan alle bezoekers van de site of alleen aangemeld bij bezoekers van de site (leden van de gemeenschap), terwijl alleen geautoriseerde leden gebeurtenissen mogen toevoegen.

In deze sectie van de documentatie wordt beschreven

* het toevoegen van de kalendereigenschap aan een plaats AEM
* configuratie-instellingen voor `Calendar`componenten

## Een kalender toevoegen aan een pagina {#adding-a-calendar-to-a-page}

Als u een `Calendar` component aan een pagina wilt toevoegen in de ontwerpmodus, gebruikt u de componentbrowser om te zoeken naar

* `Communities / Calendar`

en sleep het naar de juiste positie op een pagina, zoals een positie ten opzichte van de functie die gebruikers kunnen bekijken.

Ga voor de benodigde informatie naar [Community Components Basics](/help/communities/basics.md).

Wanneer de [vereiste client-side bibliotheken](/help/communities/calendar-basics-for-developers.md#essentials-for-client-side) worden opgenomen, wordt de `Calendar` component op deze manier weergegeven.

![chlimage_1-147](assets/chlimage_1-147.png)

### Kalender configureren {#configuring-calendar}

Selecteer de geplaatste `Calendar`component die u wilt openen en selecteer het `Configure` pictogram waarmee het dialoogvenster Bewerken wordt geopend.

![chlimage_1-148](assets/chlimage_1-148.png) ![chlimage_1-149](assets/chlimage_1-149.png)

#### Het tabblad Instellingen {#settings-tab}

Geef op onder het tabblad **Instellingen **of tags mogen worden toegepast op kalenderitems.

* **Gebeurtenissen per pagina** bepalen het aantal gebeurtenissen dat per pagina wordt weergegeven. De standaardwaarde is 10.

* **Gemoderniseerd** Als deze optie is ingeschakeld, moet het posten van kalendergebeurtenissen en opmerkingen worden goedgekeurd voordat deze op een publicatiesite worden weergegeven. De optie Standaard is uitgeschakeld.

* **Gesloten** Als deze optie is ingeschakeld, wordt de kalender gesloten voor nieuwe gebeurtenisitems en opmerkingen. De optie Standaard is uitgeschakeld.

* **De Rich Text Editor** Als deze optie is ingeschakeld, kunnen kalendergebeurtenissen en opmerkingen worden ingevoerd met markering. Standaard is ingeschakeld.

* **Labelen** toestaan Als deze optie is ingeschakeld, kunnen leden labels toevoegen aan de gebeurtenissen die ze posten (zie tabblad **Tagveld** ). Standaard is ingeschakeld.

* **Bestand uploaden** toestaan Als ingeschakeld, toestaan dat bestandsbijlagen worden toegevoegd aan een agendagebeurtenis of -opmerking. Standaard is ingeschakeld.

* **Na** inschakelen toestaan Als deze optie is ingeschakeld, kunnen leden gebeurtenissen volgen die naar de kalender zijn gepost. Standaard is ingeschakeld.

* **Maximale bestandsgrootte** alleen relevant als deze `Allow File Uploads` is ingeschakeld. Met dit veld wordt de grootte (in bytes) van een geüpload bestand beperkt. De standaardwaarde is 104857600 (10 MB).

* **Alleen toegestane bestandstypen** relevant als deze `Allow File Uploads` is ingeschakeld. Een door komma&#39;s gescheiden lijst met bestandsextensies met het &quot;punt&quot;-scheidingsteken. Bijvoorbeeld: .jpg, .jpeg, .png, .doc, .docx, .pdf. Als er bestandstypen zijn opgegeven, mogen de niet opgegeven bestandstypen niet worden geüpload. De standaardinstelling is niet opgegeven, zodat alle bestandstypen zijn toegestaan.

* **Maximale bestandsgrootte** van afbeelding alleen relevant koppelen als Uploaden van bestand toestaan is ingeschakeld. Het maximum aantal bytes dat een geüploade afbeeldingsbestand kan hebben. De standaardwaarde is 2097152****(2 MB).

* **Afbeeldingstypen** met omslag toegestaan Een door komma&#39;s gescheiden lijst met extensies voor afbeeldingsbestanden met het &quot;punt&quot;-scheidingsteken. Standaard is dit `.jpg,.jpeg,.png,.gif,.bmp`.

* **Reacties met verbindingen** toestaanAls deze optie is ingeschakeld, kunt u reacties op opmerkingen die zijn geplaatst voor de agendagebeurtenis toestaan. Standaard is ingeschakeld.

* **Gebruikers toestaan opmerkingen en gebeurtenissen** te verwijderen Als deze optie is ingeschakeld, kunnen leden de opmerkingen en kalendergebeurtenissen die ze hebben geplaatst, verwijderen. De standaardinstelling is** ** ingeschakeld.

* **Stemmen** toestaan Indien ingeschakeld, neemt u de functie Stemmen op met een agendagebeurtenis. Standaard is ingeschakeld.

* **Breedkruimels** tonen op gebeurtenispagina Standaard is ingeschakeld.

* **Filter** Datumbereik definieert het aantal dagen dat aan de huidige datum wordt toegevoegd om de waarde &#39;Aan&#39; van het paginafilter voor kalendergebeurtenislijsten te berekenen. Het standaardnummer is 30.

* **Aanbevolen inhoud** toestaan als deze optie is ingeschakeld, kan het idee worden geïdentificeerd als [aanbevolen inhoud](/help/communities/featured.md). De optie Standaard is uitgeschakeld.

Geef onder het tabblad **Moderatie gebruiker ** op hoe de geposte onderwerpen en antwoorden (door de gebruiker gegenereerde inhoud) worden beheerd. Voor meer informatie, zie het [Modereren van Gebruiker Gegenereerde Inhoud](/help/communities/moderate-ugc.md).

#### Tabblad Gebruikersmodernisering {#user-moderation-tab}

* **Posten** weigeren Als deze optie is ingeschakeld, mogen gematigde leden posten weigeren en voorkomen dat de post op het openbare forum verschijnt. Standaard is ingeschakeld.

* **Gebeurtenissen** sluiten/opnieuw openen Als deze optie is ingeschakeld, kunnen moderatoren van vertrouwde leden een gebeurtenis sluiten voor verdere bewerkingen en opmerkingen, en kunnen ze ook een gebeurtenis opnieuw openen. Standaard is ingeschakeld.

* **Vlagberichten** Als deze optie is ingeschakeld, kunnen leden gebeurtenissen of opmerkingen van anderen als ongeschikt markeren. Standaard is ingeschakeld**.*

* **Lijst** met redenen voor vlagAls deze optie is ingeschakeld, kunnen leden in een vervolgkeuzelijst kiezen waarom een gebeurtenis of opmerking als ongeschikt wordt gemarkeerd. De optie Standaard is uitgeschakeld.

* **Reden** voor aangepaste vlag Als dit selectievakje is ingeschakeld, kunnen leden hun eigen reden opgeven om een gebeurtenis of opmerking als ongeschikt te bestempelen. Standaard is uitgeschakeld**.*

* **De Drempel** van de modernisering gaat het aantal tijden in een gebeurtenis of een commentaar moet door leden worden gemarkeerd alvorens moderators worden op de hoogte gebracht. De standaardwaarde is 1 (één keer).

* **Markeringslimiet** Voer het aantal keren in dat een gebeurtenis of opmerking moet worden gemarkeerd voordat deze wordt verborgen in de openbare weergave. Indien ingesteld op -1, wordt het gemarkeerde onderwerp of de opmerking nooit verborgen in de openbare weergave. Anders, moet dit aantal groter dan of gelijk aan de Drempel van de Moderatie zijn. De standaardwaarde is 5.

#### Tabblad Tagveld {#tag-field-tab}

Onder het tabblad **Tagveld** zijn de tags die kunnen worden toegepast, indien toegestaan onder het tabblad **Instellingen **beperkt afhankelijk van de gekozen naamruimten.

* **Toegestane naamruimten** relevant als deze `Allow Tagging` is ingeschakeld op het tabblad **Instellingen **tab. De tags die kunnen worden toegepast, zijn beperkt tot de tags binnen de geselecteerde naamruimtecategorieën. De lijst met naamruimten bevat &#39;Standaardtags&#39; (de standaardnaamruimte) en &#39;Alle tags opnemen&#39;. De standaardwaarde is niet ingeschakeld, hetgeen betekent dat alle naamruimten zijn toegestaan.

* **Suggestielimiet** Voer het aantal tags in dat moet worden weergegeven als suggestie aan het lid dat naar het forum post. De standaardwaarde is **-**1 (geen limieten).

>[!NOTE]
>
>Ga naar [Tags](/help/sites-administering/tags.md) beheren voor meer informatie over het toevoegen van een nieuwe naamruimte voor tags (taxonomie).

#### Tabblad Vertaling {#translation-tab}

Als vertaling is ingeschakeld voor de communitysite op de tab **Translation **, kan de vertaling worden ingesteld om de gehele thread (gebeurtenis en opmerkingen) te vertalen in plaats van specifieke posts.

* **Alles** indien ingeschakeld, worden de gebeurtenis en de opmerkingen vertaald naar de voorkeurstaal van de gebruiker. Standaard is ingeschakeld.

## Ervaring met sitebezoekers {#site-visitor-experience}

In de publicatieomgeving wordt met de kalenderfunctie een zoekveld weergegeven met een standaarddatumbereik en alle kalendergebeurtenissen die binnen dat bereik vallen.

Wanneer een agendagebeurtenis is geselecteerd, worden de details, beschrijving en opmerkingen van de kalendergebeurtenis weergegeven.

Andere vaardigheden hangen af van het feit of de bezoeker van de site een moderator, beheerder, lid van de gemeenschap, geprivilegieerd lid of anoniem is.

### Moderatoren en beheerders {#moderators-and-administrators}

Wanneer de ondertekende in gebruiker moderator of beheerdervoorrechten heeft, kunnen zij [matigingstaken](/help/communities/moderate-ugc.md) (zoals toegelaten door de configuratie van de component) op alle kalendergebeurtenissen en commentaren uitvoeren die aan een gebeurtenis worden gepost.

![chlimage_1-150](assets/chlimage_1-150.png)

#### Leden {#members}

Wanneer de ondertekende in gebruiker een lid van de gemeenschap of een [geprivilegieerd lid](/help/communities/users.md#privileged-members-group) (afhankelijk van configuratie) is, kunnen zij selecteren `New Event` om een nieuwe kalendergebeurtenis tot stand te brengen en te posten.

Specifiek kunnen zij

* een nieuwe agendagebeurtenis maken
* een opmerking plaatsen voor een agendagebeurtenis
* hun eigen agendagebeurtenis of commentaar bewerken
* hun eigen agendagebeurtenis of commentaar verwijderen
* andere kalendergebeurtenissen of opmerkingen markeren

![chlimage_1-151](assets/chlimage_1-151.png) ![chlimage_1-152](assets/chlimage_1-152.png)

#### Anoniem {#anonymous}

Sitebezoekers die niet zijn aangemeld, kunnen alleen geposte kalendergebeurtenissen lezen, deze vertalen indien deze worden ondersteund, maar kunnen geen gebeurtenis of opmerking toevoegen en de gebeurtenissen of opmerkingen van anderen niet markeren.

![chlimage_1-153](assets/chlimage_1-153.png)

## Additional Information {#additional-information}

Meer informatie vindt u op de pagina [Kalender Essentials](/help/communities/calendar-basics-for-developers.md) voor ontwikkelaars.

Voor moderatie van kalendergebeurtenissen en commentaren, zie het [Modereren van Door Gebruiker Gegenereerde Inhoud](/help/communities/moderate-ugc.md).

Zie Door gebruiker gegenereerde inhoud [](/help/communities/tag-ugc.md)labelen voor informatie over het labelen van agendagebeurtenissen en opmerkingen.

Zie Door gebruiker gegenereerde inhoud [vertalen voor meer informatie over kalendergebeurtenissen en opmerkingen](/help/communities/translate-ugc.md).
