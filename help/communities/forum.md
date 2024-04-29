---
title: Functie van forum
description: Leer hoe te om de forumeigenschap toe te voegen en te vormen die een gebied voor ondertekende communautaire leden verstrekt om, onderwerpen tot stand te brengen te bekijken, te volgen, te zoeken of te antwoorden.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
docset: aem65
exl-id: 2b1a4917-9db6-436a-a5fd-c102fe41fb9d
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '1233'
ht-degree: 0%

---

# Functie van forum{#forum-feature}

## Inleiding {#introduction}

De forumfunctie biedt een gebied voor ingetekende sitebezoekers (leden van de community) in de publicatieomgeving voor:

* Onderwerpen maken
* Onderwerpen weergeven en antwoorden
* Een onderwerp volgen
* Een forum zoeken
* De foruminhoud helpen matigen
* Forumonderwerpen van de ene pagina naar de andere verplaatsen

In dit gedeelte van de documentatie wordt het volgende beschreven:

* De forumfunctie toevoegen aan een AEM-site.
* De montages van de configuratie voor de `Forum` component.

### Een forum toevoegen aan een pagina {#adding-a-forum-to-a-page}

Als u een `Forum` van een component aan een pagina op auteurswijze, gebruik componentenbrowser om van

* `Communities / Forum`

En sleep het naar zijn plaats op een pagina waar het forum zou moeten verschijnen.

Voor de nodige informatie gaat u naar [Grondbeginselen van Community-componenten](/help/communities/basics.md).

Wanneer de [vereiste clientbibliotheken](/help/communities/essentials-forum.md#essentials-for-client-side) worden opgenomen, is dit hoe `Forum` wordt weergegeven:

![forum-component](assets/forum-component.png)

### Een forum configureren {#configuring-a-forum}

Selecteer de geplaatste `Forum` zodat u toegang hebt tot `Configure` wordt het dialoogvenster Bewerken geopend.

![configure-new](assets/configure-new.png)

![forum-config](assets/forum-config.png)

#### Het tabblad Instellingen {#settings-tab}

Onder de **Instellingen** tabblad, geeft u instellingen voor onderwerpen en antwoorden op:

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

  Als deze optie is ingeschakeld, moet het posten van onderwerpen en opmerkingen worden goedgekeurd voordat ze op een publicatiesite kunnen worden weergegeven. De optie Standaard is uitgeschakeld.

* **Gesloten**

  Als deze optie ingeschakeld is, is het forum gesloten voor nieuwe onderwerpen en opmerkingen. De optie Standaard is uitgeschakeld.

* **RTF-editor**

  Als deze optie is ingeschakeld, kunnen onderwerpen en opmerkingen worden ingevoerd met een markering. De optie Standaard is uitgeschakeld.

* **Tags toestaan**

  Als deze optie is ingeschakeld, kunnen leden labels toevoegen aan hun berichten (zie **Veld code** ). De optie Standaard is uitgeschakeld.

* **Uploaden van bestanden toestaan**

  Als deze optie ingeschakeld is, staat u toe dat bestandsbijlagen worden toegevoegd aan het onderwerp of de opmerking. De optie Standaard is uitgeschakeld.

* **Volgen toestaan**

  Indien deze optie is ingeschakeld, neemt u de volgende functie op voor forumposten, waardoor leden kunnen worden [aangemeld](/help/communities/notifications.md) van nieuwe posten. De optie Standaard is uitgeschakeld.

* **Vastzetten toestaan**

  Als deze optie ingeschakeld is, kunnen forumonderwerpen boven aan de lijst met onderwerpen worden vastgezet. De optie Standaard is uitgeschakeld.

* **Aanbevolen inhoud toestaan**

  Als deze optie ingeschakeld is, kan het idee worden herkend als [aanbevolen inhoud](/help/communities/featured.md). De optie Standaard is uitgeschakeld.

* **E-mailabonnementen toestaan**

  Als deze optie ingeschakeld is, kunnen leden per e-mail op de hoogte worden gesteld van nieuwe berichten ([abonnement](/help/communities/subscriptions.md)). Vereisten `Allow Following` te controleren en [e-mail geconfigureerd](/help/communities/email.md). De optie Standaard is uitgeschakeld.

* **Max. bestandsgrootte**

  Alleen relevant als `Allow File Uploads` is ingeschakeld. Dit veld beperkt de grootte (in bytes) van een geüpload bestand. De standaardwaarde is 104857600 (10 MB).

* **Toegestane bestandstypen**

  Alleen relevant als `Allow File Uploads` is ingeschakeld. Een door komma&#39;s gescheiden lijst met bestandsextensies met het scheidingsteken &#39;punt&#39;. Bijvoorbeeld .jpg, .jpeg, .png, .doc, .docx, .pdf. Als er bestandstypen zijn opgegeven, kunnen deze niet worden geüpload. De standaardinstelling is niet opgegeven, zodat alle bestandstypen zijn toegestaan.

* **Maximale bestandsgrootte afbeelding bijvoegen**
Alleen relevant als Uploaden van bestand toestaan is ingeschakeld. Het maximum aantal bytes dat een geüploade afbeeldingsbestand kan hebben. De standaardwaarde is 2097152 (2 MB).

* **Reacties met verbindingen toestaan**

  Als deze optie is ingeschakeld, kunt u reacties op opmerkingen die naar het onderwerp zijn gepost toestaan. De optie Standaard is uitgeschakeld.

* **Stemmen toestaan**

  Indien ingeschakeld, neemt u de functie Stemmen op met een onderwerp. De optie Standaard is uitgeschakeld.

* **Gebruikers toestaan opmerkingen en onderwerpen te verwijderen**

  Als deze optie is ingeschakeld, kunnen leden de opmerkingen en onderwerpen die ze hebben geplaatst verwijderen. De optie Standaard is uitgeschakeld.

* **Broodkruimels tonen**

  Indien aangekruist, toon navigatiebroodkruimels op onderwerppagina&#39;s. Standaard is ingeschakeld.

* **Badges weergeven**

  Indien ingeschakeld, verdiende en toegewezen weergave [badges](/help/communities/implementing-scoring.md) met het blogbericht van een lid. De optie Standaard is uitgeschakeld.

* **Geprivilegieerde leden toestaan**

  Als deze optie is ingeschakeld, mogen alleen leden met Geprivilegieerde inhoud maken.

* **Toegestane geprivilegieerde leden**

  Voeg de geprivilegieerde leden toe die inhoud mogen maken.

* **Door gebruiker gegenereerde inhoud blokkeren in de bewerkingsmodus van auteur**

  Als deze optie is ingeschakeld, wordt door de gebruiker gegenereerde inhoud geblokkeerd tijdens het bewerken in de auteurmodus.

* **Menu inschakelen**

  Als deze optie is ingeschakeld, kunnen geregistreerde gebruikers in de gemeenschap andere geregistreerde leden identificeren (met voornaam, achternaam, gebruikersnaam) en ze tags toewijzen met behulp van de algemene syntaxis voor @user-name. De getagde gebruikers ontvangen meldingen over hun berichten.

* **Max. aantal meldingen**

  Beperk het maximum aantal berichten dat in een bericht is toegestaan. De standaardwaarde is 10.

* **Menatiepatroon gebruikersinterface**

  Geef de patroontekenreeks op die de geregistreerde gebruiker in een bericht mag labelen (@genoemd). Bijvoorbeeld: `~{{familyName}}{{givenName}}`.

>[!NOTE]
>
>Het kan nodig zijn om `AllowThreaded Replies` en `Allow users to Delete Comments and Topics` om commentaar op een onderwerp toe te laten.

#### Tabblad Gebruikersmodernisering {#user-moderation-tab}

Onder de **Moderatie gebruiker** , geeft u op hoe de geposte onderwerpen en antwoorden (door de gebruiker gegenereerde inhoud) worden beheerd. Zie voor meer informatie [Door de gebruiker gegenereerde inhoud moderniseren](/help/communities/moderate-ugc.md).

* **Posten weigeren**

  Indien deze optie is ingeschakeld, mogen de verantwoordelijken voor het lid die hun functie hebben erkend, posten ontkennen en voorkomen dat de functie op het openbare forum verschijnt. De optie Standaard is uitgeschakeld.

* **Onderwerpen sluiten/opnieuw openen**

  Indien gecontroleerd, kunnen de vertrouwde op lidmoderatoren een onderwerp aan verdere uitgeeft en commentaren sluiten, en kunnen een onderwerp ook heropenen. De optie Standaard is uitgeschakeld.

* **Onderwerpen verplaatsen**

  Indien gecontroleerd, sta moderators op toe publiceren kant om onderwerpen te bewegen. Standaard is ingeschakeld.

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

Onder de **Veld code** , de tags die kunnen worden toegepast, indien toegestaan onder de **Instellingen** zijn beperkt op basis van de gekozen naamruimten.

* **Toegestane naamruimten**

  Relevant indien `Allow Tagging` wordt gecontroleerd onder de **Instellingen** tab. De tags die kunnen worden toegepast, zijn beperkt tot de tags binnen de geselecteerde naamruimtecategorieën. De lijst met naamruimten bevat &quot;Standaardtags&quot; (de standaardnaamruimte) en &quot;Alle tags opnemen&quot;. De standaardwaarde is niet ingeschakeld, hetgeen betekent dat alle naamruimten zijn toegestaan.

* **Suggestiegrenswaarde**

  Voer het aantal tags in dat moet worden weergegeven als suggestie aan het lid dat naar het forum post. De standaardwaarde is **-**1 (geen limieten).

#### Tabblad Vertaling {#translation-tab}

Onder de **Vertaling** tab, als vertaling voor de communautaire plaats wordt toegelaten, kan de vertaling worden geplaatst om het volledige onderwerp of geselecteerde posten te vertalen.

* **Alles vertalen**

  Indien gecontroleerd, wordt de forumdraad vertaald in de aangewezen taal van de gebruiker. De optie Standaard is uitgeschakeld.

#### Tabblad Instellingen sorteren {#sort-settings-tab}

Onder de **Instellingen sorteren** , geeft u op hoe de geposte opmerkingen worden gesorteerd wanneer deze worden weergegeven.

* **Sorteren op**

  Alle toegestane sorteerselecties controleren: `Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed and Most Liked`. Standaard is `Newest, Oldest, Last Updated`.

* **Instellen als standaard**

  Trek naar beneden om een van de geselecteerde sorteeropties te selecteren die als standaard moeten worden weergegeven. Standaard is `Newest`.

* **Tijdopties selecteren voor het sorteren van analysemogelijkheden**

  Trek naar beneden om een van de volgende opties te selecteren: `All, Last 24 Hours, Last 7 Days, Last 30 Days`.

  Standaard is `All`.

### Aanvullende informatie {#additional-information}

Meer informatie is te vinden op de [Essentiële elementen van forum](/help/communities/essentials-forum.md) pagina voor ontwikkelaars.

Voor moderatie van geposte onderwerpen en commentaren, zie [Door de gebruiker gegenereerde inhoud moderniseren](/help/communities/moderate-ugc.md).

Voor het etiketteren van geposte onderwerpen en commentaren, zie [Door de gebruiker gegenereerde inhoud labelen](/help/communities/tag-ugc.md).

Zie voor een vertaling van geposte onderwerpen en opmerkingen [Door de gebruiker gegenereerde inhoud vertalen](/help/communities/translate-ugc.md).
