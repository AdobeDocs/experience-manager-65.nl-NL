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
source-git-commit: 9e941ce092f7d3248c11886d6bf1e54f2e726362
workflow-type: tm+mt
source-wordcount: '1226'
ht-degree: 0%

---


# Functie van forum{#forum-feature}

## Inleiding {#introduction}

De functie Forum biedt een gebied voor ingetekende sitebezoekers (leden van de community) in de publicatieomgeving voor:

* Nieuwe onderwerpen maken
* Onderwerpen weergeven en antwoorden
* Een onderwerp volgen
* Een forum zoeken
* Help de inhoud van het forum te matigen
* Forumonderwerpen van de ene pagina naar de andere verplaatsen

In dit gedeelte van de documentatie wordt het volgende beschreven:

* De forumfunctie toevoegen aan een AEM-site.
* De montages van de configuratie voor de `Forum` component.

### Een forum toevoegen aan een pagina {#adding-a-forum-to-a-page}

Als u een `Forum` component aan een pagina wilt toevoegen in de ontwerpmodus, gebruikt u de componentbrowser om te zoeken naar

* `Communities / Forum`

en sleep het naar zijn plaats op een pagina waar het forum zou moeten verschijnen.

Ga voor de benodigde informatie naar [Community Components Basics](/help/communities/basics.md).

Wanneer de [vereiste client-side bibliotheken](/help/communities/essentials-forum.md#essentials-for-client-side) worden opgenomen, wordt de `Forum` component als volgt weergegeven:

![chlimage_1-60](assets/chlimage_1-60.png)

### Een forum configureren {#configuring-a-forum}

Selecteer de geplaatste `Forum` component die u wilt openen en selecteer het `Configure` pictogram waarmee het dialoogvenster Bewerken wordt geopend.

![chlimage_1-61](assets/chlimage_1-61.png)

![forum-config](assets/forum-config.png)

#### Het tabblad Instellingen {#settings-tab}

Geef op het tabblad **Instellingen** instellingen op voor onderwerpen en antwoorden:

* **Miniatuur van bijlage toestaan**

   Als deze optie is ingeschakeld, wordt een miniatuur van de bijgevoegde afbeelding gemaakt.

* **Maximale grootte miniatuur bijvoegen**

   Maximale grootte (in pixels) van de miniatuurafbeelding van de bijlage. De standaardwaarde is 800 x 800.

* **Minimale afbeeldingsgrootte voor miniatuur**
* **Maximale miniatuurgrootte**

   Maximale grootte (in pixels) van de miniatuurafbeelding voor inline-afbeelding. De standaardwaarde is 800 x 800.

* **Onderwerpen per pagina**

   Hiermee definieert u het aantal onderwerpen/posts dat per pagina wordt weergegeven. De standaardwaarde is 10.

* **Gematigd**

   Als deze optie is ingeschakeld, moet het posten van onderwerpen en opmerkingen worden goedgekeurd voordat ze op een publicatiesite worden weergegeven. De optie Standaard is uitgeschakeld.

* **Gesloten**

   Als deze optie ingeschakeld is, is het forum gesloten voor nieuwe onderwerpen en opmerkingen. De optie Standaard is uitgeschakeld.

* **RTF-editor**

   Als deze optie is ingeschakeld, kunnen onderwerpen en opmerkingen worden ingevoerd met een markering. De optie Standaard is uitgeschakeld.

* **Tags toestaan**

   Als deze optie is ingeschakeld, kunnen leden labellabels aan hun post toevoegen (zie tabblad **Tagveld** ). De optie Standaard is uitgeschakeld.

* **Uploaden van bestanden toestaan**

   Als deze optie ingeschakeld is, staat u toe dat bestandsbijlagen worden toegevoegd aan het onderwerp of de opmerking. De optie Standaard is uitgeschakeld.

* **Volgen toestaan**

   Indien deze optie is ingeschakeld, dient u de volgende functie voor forumposten op te nemen, waardoor leden op de [hoogte kunnen worden gebracht](/help/communities/notifications.md) van nieuwe posten. De optie Standaard is uitgeschakeld.

* **Vastzetten toestaan**

   Als deze optie ingeschakeld is, kunnen forumonderwerpen boven aan de lijst met onderwerpen worden vastgezet. De optie Standaard is uitgeschakeld.

* **Aanbevolen inhoud toestaan**

   Als deze optie is ingeschakeld, kan het idee worden geïdentificeerd als [aanbevolen inhoud](/help/communities/featured.md). De optie Standaard is uitgeschakeld.

* **E-mailabonnementen toestaan**

   Als deze optie is ingeschakeld, kunnen leden via e-mail op de hoogte worden gesteld van nieuwe berichten ([abonnement](/help/communities/subscriptions.md)). Moet `Allow Following` worden gecontroleerd en [e-mail wordt gevormd](/help/communities/email.md). De optie Standaard is uitgeschakeld.

* **Max. bestandsgrootte**

   Alleen relevant als `Allow File Uploads` is gecontroleerd. Met dit veld wordt de grootte (in bytes) van een geüpload bestand beperkt. De standaardwaarde is 104857600 (10 MB).

* **Toegestane bestandstypen**

   Alleen relevant als `Allow File Uploads` is gecontroleerd. Een door komma&#39;s gescheiden lijst met bestandsextensies met het &quot;punt&quot;-scheidingsteken. Bijvoorbeeld: .jpg, .jpeg, .png, .doc, .docx, .pdf. Als er bestandstypen zijn opgegeven, mogen de niet opgegeven bestandstypen niet worden geüpload. De standaardinstelling is niet opgegeven, zodat alle bestandstypen zijn toegestaan.

* **Maximale bestandsgrootte** van afbeelding alleen relevant koppelen als Uploaden van bestand toestaan is ingeschakeld. Het maximum aantal bytes dat een geüploade afbeeldingsbestand kan hebben. De standaardwaarde is 2097152 (2 MB).

* **Reacties met verbindingen toestaan**

   Als deze optie is ingeschakeld, kunt u reacties op opmerkingen die naar het onderwerp zijn verzonden toestaan. De optie Standaard is uitgeschakeld.

* **Stemmen toestaan**

   Indien ingeschakeld, neemt u de functie Stemmen op met een onderwerp. De optie Standaard is uitgeschakeld.

* **Gebruikers toestaan opmerkingen en onderwerpen te verwijderen**

   Als deze optie is ingeschakeld, kunnen leden de opmerkingen en onderwerpen die ze hebben geplaatst verwijderen. De optie Standaard is uitgeschakeld.

* **Broodkruimels tonen**

   Indien aangekruist, toon navigatiebroodkruimels op onderwerppagina&#39;s. Standaard is ingeschakeld.

* **Badges weergeven**

   Indien ingeschakeld, verdiende en toegewezen [badges](/help/communities/implementing-scoring.md) bij het blogbericht van een lid weergeven. De optie Standaard is uitgeschakeld.

* **Geprivilegieerde leden toestaan**

   Als deze optie is ingeschakeld, mogen alleen leden met Geprivilegieerde inhoud maken.

* **Toegestane geprivilegieerde leden**

   Voeg de geprivilegieerde leden toe die inhoud mogen maken.

* **Door gebruiker gegenereerde inhoud blokkeren in de bewerkingsmodus van auteur**

   Als deze optie is ingeschakeld, wordt door de gebruiker gegenereerde inhoud geblokkeerd tijdens het bewerken in de ontwerpmodus.

* **Menu inschakelen**

   Als deze optie is ingeschakeld, kunnen geregistreerde gebruikers in de gemeenschap andere geregistreerde leden identificeren (met voornaam, achternaam, gebruikersnaam) en ze tags toewijzen met behulp van de algemene syntaxis voor @user-name. De getagde gebruikers ontvangen meldingen over hun vermeldingen.

* **Max. aantal meldingen**

   Beperk het maximum aantal berichten dat in een bericht is toegestaan. De standaardwaarde is 10.

* **Menatiepatroon gebruikersinterface**

   Geef de toegestane patroontekenreeks op om de geregistreerde gebruiker in een bericht te labelen (@genoemd). Bijvoorbeeld `~{{familyName}}{{givenName}}`.

>[!NOTE]
>
>Het kan nodig zijn om zowel `AllowThreaded Replies` als `Allow users to Delete Comments and Topics` om opmerkingen over een onderwerp mogelijk te maken.


#### Tabblad Gebruikersmodernisering {#user-moderation-tab}

Onder het lusje van de Moderatie **van de** Gebruiker, specificeer hoe de geposte onderwerpen en de antwoorden (gebruiker geproduceerde inhoud) worden beheerd. Voor meer informatie, zie het [Modereren van Gebruiker Gegenereerde Inhoud](/help/communities/moderate-ugc.md).

* **Posten weigeren**

   Als deze optie wordt ingeschakeld, zullen de verantwoordelijken van de leden hun functie kunnen ontkennen en voorkomen dat de functie op het openbare forum verschijnt. De optie Standaard is uitgeschakeld.

* **Onderwerpen sluiten/opnieuw openen**

   Indien gecontroleerd, kunnen de vertrouwde op lidmoderatoren een onderwerp aan verdere uitgeeft en commentaren sluiten, en kunnen een onderwerp ook heropenen. De optie Standaard is uitgeschakeld.

* **Onderwerpen verplaatsen**

   Indien gecontroleerd, sta toe publiceert-zijmoderators om onderwerpen te bewegen. Standaard is ingeschakeld.

* **Vlagberichten**

   Als deze optie is ingeschakeld, kunnen leden onderwerpen of opmerkingen van anderen als ongeschikt markeren. De optie Standaard is uitgeschakeld.

* **Lijst met redenen voor vlag**

   Als deze optie is ingeschakeld, kunnen leden in een vervolgkeuzelijst kiezen waarom een onderwerp of opmerking niet als ongepast wordt gemarkeerd. De optie Standaard is uitgeschakeld.

* **Reden voor aangepaste vlag**

   Als deze optie is ingeschakeld, kunnen leden hun eigen reden opgeven om een onderwerp of opmerking als ongeschikt te bestempelen. De optie Standaard is uitgeschakeld.

* **Moderniseringsdrempel**

   Ga het aantal tijden in een onderwerp of een commentaar moet door leden worden gemarkeerd alvorens moderators worden meegedeeld. De standaardwaarde is 1 (één keer).

* **Limiet voor markering**

   Voer het aantal keren in dat een onderwerp of opmerking moet worden gemarkeerd voordat het wordt verborgen in de openbare weergave. Indien ingesteld op -1, wordt het gemarkeerde onderwerp of de opmerking nooit verborgen in de openbare weergave. Anders, moet dit aantal groter dan of gelijk aan de Drempel van de Moderatie zijn. De standaardwaarde is 5.

#### Tabblad Tagveld {#tag-field-tab}

Onder het tabblad **Tagveld** zijn de tags die kunnen worden toegepast, indien toegestaan op het tabblad **Instellingen** , beperkt op basis van de gekozen naamruimten.

* **Toegestane naamruimten**

   Relevant als `Allow Tagging` is ingeschakeld onder het tabblad **Instellingen** . De tags die kunnen worden toegepast, zijn beperkt tot de tags binnen de geselecteerde naamruimtecategorieën. De lijst met naamruimten bevat &#39;Standaardtags&#39; (de standaardnaamruimte) en &#39;Alle tags opnemen&#39;. De standaardwaarde is niet ingeschakeld, hetgeen betekent dat alle naamruimten zijn toegestaan.

* **Suggestiegrenswaarde**

   Voer het aantal tags in dat moet worden weergegeven als suggestie aan het lid dat naar het forum post. De standaardwaarde is **-**1 (geen limieten).

#### Tabblad Vertaling {#translation-tab}

Als op het tabblad **Vertaling** vertaling is ingeschakeld voor de site van de gebruikersgemeenschap, kan de vertaling worden ingesteld op het vertalen van het gehele onderwerp of van geselecteerde artikelen.

* **Alles vertalen**

   Indien gecontroleerd, wordt de forumdraad vertaald in de aangewezen taal van de gebruiker. De optie Standaard is uitgeschakeld.

#### Tabblad Instellingen sorteren {#sort-settings-tab}

Geef op onder het tabblad **Sorteerinstellingen** op hoe de geposte opmerkingen worden gesorteerd wanneer ze worden weergegeven.

* **Sorteren op**

   Alle toegestane sorteerselecties controleren: `Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed and Most Liked`. Standaard is dit `Newest, Oldest, Last Updated`.

* **Instellen als standaard**

   Trek naar beneden om een van de geselecteerde sorteeropties te selecteren die als standaard moeten worden weergegeven. Standaard is dit `Newest`.

* **Tijdopties selecteren voor Analytics-sortering**

   Trek naar beneden om een van de volgende opties te selecteren: `All, Last 24 Hours, Last 7 Days, Last 30 Days`.

   Standaard is dit `All`.

### Additional Information {#additional-information}

Meer informatie kunt u vinden op de pagina [Forum Essentials](/help/communities/essentials-forum.md) voor ontwikkelaars.

Voor moderatie van geposte onderwerpen en commentaren, zie het [Modereren van Door Gebruiker Gegenereerde Inhoud](/help/communities/moderate-ugc.md).

Zie Door gebruiker gegenereerde inhoud [](/help/communities/tag-ugc.md)labelen voor informatie over het labelen van geposte onderwerpen en opmerkingen.

Zie Door gebruiker gegenereerde inhoud [vertalen voor een vertaling van geposte onderwerpen en opmerkingen](/help/communities/translate-ugc.md).
