---
title: Functie van forum
seo-title: Functie van forum
description: Hoe te om de forumeigenschap toe te voegen en te vormen
seo-description: Hoe te om de forumeigenschap toe te voegen en te vormen
uuid: e69be4e1-c9d5-4d51-8e7e-609e5460e378
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: d936cef5-ad76-482d-97bf-c40137185812
docset: aem65
translation-type: tm+mt
source-git-commit: 27a054cc5d502d95c664c3b414d0066c6c120b65

---


# Functie van forum{#forum-feature}

## Inleiding {#introduction}

De functie Forum biedt een gebied voor ingetekende sitebezoekers (leden van de community) in de publicatieomgeving voor:

* nieuwe onderwerpen maken
* onderwerpen bekijken en beantwoorden
* volgen
* zoeken naar een forum
* de foruminhoud helpen verminderen
* forumonderwerpen van de ene pagina naar de andere verplaatsen

In deze sectie van de documentatie wordt beschreven

* toevoegen van de forumfunctie aan een AEM-site
* configuratie-instellingen voor de `Forum`component

### Een forum toevoegen aan een pagina {#adding-a-forum-to-a-page}

Als u een `Forum` component aan een pagina wilt toevoegen in de ontwerpmodus, gebruikt u de componentbrowser om te zoeken naar

* `Communities / Forum`

en sleep het naar zijn plaats op een pagina waar het forum zou moeten verschijnen.

Ga voor de benodigde informatie naar [Community Components Basics](/help/communities/basics.md).

Wanneer de [vereiste client-side bibliotheken](/help/communities/essentials-forum.md#essentials-for-client-side) worden opgenomen, ziet u zo de `Forum`component eruit:

![chlimage_1-104](assets/chlimage_1-104.png)

### Een forum configureren {#configuring-a-forum}

Selecteer de geplaatste `Forum` component die u wilt openen en selecteer het `Configure` pictogram waarmee het dialoogvenster Bewerken wordt geopend.

![chlimage_1-105](assets/chlimage_1-105.png) ![forum-config](assets/forum-config.png)

#### Het tabblad Instellingen {#settings-tab}

Geef onder het tabblad **Instellingen **instellingen instellingen instellingen op voor onderwerpen en antwoorden:

* **Miniatuur van bijlage toestaan**Als deze optie is ingeschakeld, wordt een miniatuur van de bijgevoegde afbeelding gemaakt.
* **Maximale grootte miniatuur** koppelen Maximale grootte (in pixels) van de miniatuurafbeelding in de bijlage. De standaardwaarde is 800 x 800.

* **Minimale afbeeldingsgrootte voor miniatuur**
* **Maximale miniatuurgrootte** Maximale grootte (in pixels) van de miniatuurafbeelding voor inline-afbeelding. De standaardwaarde is 800 x 800.

* **Onderwerpen per pagina**Definieert het aantal onderwerpen/posten dat per pagina wordt getoond. De standaardwaarde is 10.
* **Gemoderniseerd** Als deze optie is ingeschakeld, moet het posten van onderwerpen en opmerkingen worden goedgekeurd voordat ze op een publicatiesite worden weergegeven. De optie Standaard is uitgeschakeld.

* **Gesloten** Als deze optie ingeschakeld is, is het forum gesloten voor nieuwe onderwerpen en opmerkingen. De optie Standaard is uitgeschakeld.

* **De rijke Redacteur** van de Tekst als gecontroleerd, onderwerpen en commentaren kunnen met prijsverhoging zijn ingegaan. De optie Standaard is uitgeschakeld.

* **Labelen** toestaan Als deze optie is ingeschakeld, kunnen leden labellabels aan hun post toevoegen (zie tabblad **Tagveld** ). De optie Standaard is uitgeschakeld.

* **Bestand uploaden** toestaan Als deze optie is ingeschakeld, mogen bestandsbijlagen worden toegevoegd aan het onderwerp of de opmerking. De optie Standaard is uitgeschakeld.

* **Volgend** toestaan Indien ingeschakeld, neemt u de volgende functie voor forumfuncties op, waardoor leden op de [hoogte](/help/communities/notifications.md) kunnen worden gesteld van nieuwe posten. De optie Standaard is uitgeschakeld.

* **Vastzetten** toestaan Indien ingeschakeld, kunnen forumonderwerpen boven aan de lijst met onderwerpen worden vastgezet. De optie Standaard is uitgeschakeld.

* **Aanbevolen inhoud** toestaan als deze optie is ingeschakeld, kan het idee worden geïdentificeerd als [aanbevolen inhoud](/help/communities/featured.md). De optie Standaard is uitgeschakeld.

* **E-mailabonnementen** toestaan Als deze optie is ingeschakeld, kunnen leden per e-mail op de hoogte worden gesteld van nieuwe berichten ([abonnement](/help/communities/subscriptions.md)). Moet `Allow Following` worden gecontroleerd en [e-mail wordt gevormd](/help/communities/email.md). De optie Standaard is uitgeschakeld.

* **Maximale bestandsgrootte** alleen relevant als deze `Allow File Uploads` is ingeschakeld. Met dit veld wordt de grootte (in bytes) van een geüpload bestand beperkt. De standaardwaarde is 104857600 (10 MB).

* **Alleen toegestane bestandstypen** relevant als deze `Allow File Uploads` is ingeschakeld. Een door komma&#39;s gescheiden lijst met bestandsextensies met het &quot;punt&quot;-scheidingsteken. Bijvoorbeeld: .jpg, .jpeg, .png, .doc, .docx, .pdf. Als er bestandstypen zijn opgegeven, mogen de niet opgegeven bestandstypen niet worden geüpload. De standaardinstelling is niet zodanig opgegeven dat** **alle bestandstypen zijn toegestaan.

* **Maximale bestandsgrootte** van afbeelding alleen relevant koppelen als Uploaden van bestand toestaan is ingeschakeld. Het maximum aantal bytes dat een geüploade afbeeldingsbestand kan hebben. De standaardwaarde is 2097152****(2 MB).

* **Reacties** met verbindingen toestaan Als deze optie is ingeschakeld, kunt u reacties op opmerkingen die naar het onderwerp zijn gepost toestaan. De optie Standaard is uitgeschakeld.

* **Stemmen** toestaan Indien ingeschakeld, neemt u de functie Stemmen op met een onderwerp. De optie Standaard is uitgeschakeld.

* **Gebruikers toestaan opmerkingen en onderwerpen** te verwijderen Als deze optie is ingeschakeld, kunnen leden de opmerkingen en onderwerpen die ze hebben geplaatst verwijderen. De optie Standaard is uitgeschakeld.

* **Breadcrumbs** tonen Indien ingeschakeld, blanco overzichten weergeven op onderwerppagina&#39;s. Standaard is ingeschakeld.

* **Badges** weergeven Indien ingeschakeld, verdiende en toegewezen [badges](/help/communities/implementing-scoring.md) bij het blogbericht van een lid weergeven. De optie Standaard is uitgeschakeld.

* **Geprivilegieerde leden** toestaanAls deze optie is ingeschakeld, mogen alleen geprivilegieerde leden inhoud maken.

* **Toegestane geprivilegieerde leden**Voeg de geprivilegieerde leden toe die u hebt gemachtigd om inhoud te maken.
* **Door de gebruiker gegenereerde inhoud blokkeren in de bewerkingsmodus** Auteur (indien ingeschakeld), wordt door de gebruiker gegenereerde inhoud tijdens het bewerken in de auteurmodus geblokkeerd.

* **Mentie** inschakelen indien ingeschakeld, kunnen geregistreerde gebruikers uit de gebruikersgemeenschap andere geregistreerde leden identificeren (met voornaam, achternaam, gebruikersnaam) en ze labelen met de gebruikelijke syntaxis voor @user-name. De getagde gebruikers ontvangen meldingen over hun vermeldingen.

* **Max. aantal meldingen** Beperk het maximum aantal in een artikel toegestane vermeldingen. De standaardwaarde is 10.

* **UI-menatiepatroon** Geef de toegestane patroontekenreeks op om de geregistreerde gebruiker in een bericht te labelen (@vermeld). Bijvoorbeeld `~{{familyName}}{{givenName}}`.

>[!NOTE]
>
>Het kan nodig zijn om zowel `AllowThreaded Replies` als `Allow users to Delete Comments and Topics` om opmerkingen over een onderwerp mogelijk te maken.

#### Tabblad Gebruikersmodernisering {#user-moderation-tab}

Geef onder het tabblad **Moderatie gebruiker ** op hoe de geposte onderwerpen en antwoorden (door de gebruiker gegenereerde inhoud) worden beheerd. Voor meer informatie, zie het [Modereren van Gebruiker Gegenereerde Inhoud](/help/communities/moderate-ugc.md).

* **Posten** weigeren Als deze optie is ingeschakeld, mogen gematigde leden posten weigeren en voorkomen dat de post op het openbare forum verschijnt. De optie Standaard is uitgeschakeld.

* **Sluit/heropen Onderwerpen** Indien gecontroleerd, kunnen de vertrouwde op lidmoderatoren een onderwerp aan verdere uitgeeft en commentaren sluiten, en kunnen een onderwerp ook heropenen. De optie Standaard is uitgeschakeld.

* **Onderwerpen** van de beweging indien gecontroleerd, sta toe publiceert-zijmoderators om onderwerpen te bewegen. Standaard is ingeschakeld.

* **Vlagberichten** Als deze optie is ingeschakeld, kunnen leden onderwerpen of opmerkingen van anderen als ongeschikt markeren. De optie Standaard is uitgeschakeld.

* **Lijst** met redenen voor vlagAls deze optie is ingeschakeld, kunnen leden in een vervolgkeuzelijst kiezen waarom zij een onderwerp of opmerking als ongeschikt aanmerken. De optie Standaard is uitgeschakeld.

* **Reden** voor aangepaste vlag Als dit selectievakje is ingeschakeld, kunnen leden hun eigen reden opgeven om een onderwerp of opmerking als ongeschikt te bestempelen. De optie Standaard is uitgeschakeld.

* **De Drempel** van de modernisering gaat het aantal tijden in een onderwerp of een commentaar moet door leden worden gemarkeerd alvorens de moderatoren op de hoogte worden gebracht. De standaardwaarde is 1 (één keer).

* **Laginglimiet** Voer het aantal keren in dat een onderwerp of opmerking moet worden gemarkeerd voordat het wordt verborgen in de openbare weergave. Indien ingesteld op -1, wordt het gemarkeerde onderwerp of de opmerking nooit verborgen in de openbare weergave. Anders, moet dit aantal groter dan of gelijk aan de Drempel van de Moderatie zijn. De standaardwaarde is 5.

#### Tabblad Tagveld {#tag-field-tab}

Onder het tabblad **Tagveld** zijn de tags die kunnen worden toegepast, indien toegestaan onder het tabblad **Instellingen **beperkt afhankelijk van de gekozen naamruimten.

* **Toegestane naamruimten** relevant als deze `Allow Tagging` is ingeschakeld op het tabblad **Instellingen **tab. De tags die kunnen worden toegepast, zijn beperkt tot de tags binnen de geselecteerde naamruimtecategorieën. De lijst met naamruimten bevat &#39;Standaardtags&#39; (de standaardnaamruimte) en &#39;Alle tags opnemen&#39;. De standaardwaarde is niet ingeschakeld, hetgeen betekent dat alle naamruimten zijn toegestaan.

* **Suggestielimiet** Voer het aantal tags in dat moet worden weergegeven als suggestie aan het lid dat naar het forum post. De standaardwaarde is **-**1 (geen limieten).

#### Tabblad Vertaling {#translation-tab}

Onder het tabblad **Vertaling **Als vertaling is ingeschakeld voor de site van de gebruikersgemeenschap, kan de vertaling worden ingesteld om het gehele onderwerp of de geselecteerde artikelen te vertalen.

* **Vertaal allen** indien gecontroleerd, wordt de forumdraad vertaald in de aangewezen taal van de gebruiker. De optie Standaard is uitgeschakeld.

#### Tabblad Instellingen sorteren {#sort-settings-tab}

Geef onder het tabblad **Instellingen sorteren **op hoe de geposte opmerkingen moeten worden gesorteerd wanneer ze worden weergegeven.

* **Sorteren op** Alle toegestane sorteerselecties controleren: `Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed and Most Liked`. Standaard is dit `Newest, Oldest, Last Updated`.

* **Als Standaard** omlaag schuiven instellen om een van de geselecteerde sorteeropties te selecteren die als standaardopties moeten worden weergegeven. Standaard is dit `Newest`.

* **Selecteer Tijdopties voor Analytische sortering** Pull omlaag om een van `All, Last 24 Hours, Last 7 Days, Last 30 Days`deze opties te selecteren. Standaard is dit `All`.

### Additional Information {#additional-information}

Meer informatie kunt u vinden op de pagina [Forum Essentials](/help/communities/essentials-forum.md) voor ontwikkelaars.

Voor moderatie van geposte onderwerpen en commentaren, zie het [Modereren van Door Gebruiker Gegenereerde Inhoud](/help/communities/moderate-ugc.md).

Zie Door gebruiker gegenereerde inhoud [](/help/communities/tag-ugc.md)labelen voor informatie over het labelen van geposte onderwerpen en opmerkingen.

Zie Door gebruiker gegenereerde inhoud [vertalen voor een vertaling van geposte onderwerpen en opmerkingen](/help/communities/translate-ugc.md).
