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

De forumfunctie biedt een ruimte voor ingetekende sitebezoekers (leden van de gemeenschap) in de Publish-omgeving voor:

* Onderwerpen maken
* Onderwerpen weergeven en antwoorden
* Een onderwerp volgen
* Een forum zoeken
* De foruminhoud helpen matigen
* Forumonderwerpen van de ene pagina naar de andere verplaatsen

In dit gedeelte van de documentatie wordt het volgende beschreven:

* De forumfunctie toevoegen aan een AEM-site.
* Configuration settings for the `Forum` component.

### Een forum toevoegen aan een pagina {#adding-a-forum-to-a-page}

Als u een component `Forum` in de ontwerpmodus aan een pagina wilt toevoegen, gebruikt u de componentbrowser om te zoeken naar

* `Communities / Forum`

En sleep het naar zijn plaats op een pagina waar het forum zou moeten verschijnen.

Voor noodzakelijke informatie, bezoek {de Grondbeginselen van de Componenten van 0} Gemeenschappen [&#128279;](/help/communities/basics.md).

Wanneer de [ vereiste cliënt-zijbibliotheken ](/help/communities/essentials-forum.md#essentials-for-client-side) inbegrepen zijn, is dit hoe de `Forum` component verschijnt:

![ forum-component ](assets/forum-component.png)

### Een forum configureren {#configuring-a-forum}

Selecteer de geplaatste component `Forum` , zodat u het pictogram `Configure` kunt openen en selecteren waarmee het dialoogvenster Bewerken wordt geopend.

![ vorm-nieuw ](assets/configure-new.png)

![ forum-config ](assets/forum-config.png)

#### Het tabblad Instellingen {#settings-tab}

Onder het **lusje van Montages**, specificeer montages voor onderwerpen en antwoorden:

* **staat de Duimnagel van de Bijlage** toe

  Als deze optie is ingeschakeld, wordt een miniatuur van de bijgevoegde afbeelding gemaakt.

* **Max de Grootte van de Duimnagel van de Band**

  Maximale grootte (in pixels) van de miniatuurafbeelding van de bijlage. De standaardwaarde is 800 x 800.

* **Min. grootte van het Beeld voor Duimnagel**
* **Max de Grootte van de Duimnagel**

  Maximale grootte (in pixels) van de miniatuurafbeelding voor inline-afbeelding. De standaardwaarde is 800 x 800.

* **Onderwerpen per Pagina**

  Hiermee definieert u het aantal onderwerpen/posts dat per pagina wordt weergegeven. De standaardwaarde is 10.

* **Gematigd**

  Als deze optie is ingeschakeld, moet het posten van onderwerpen en opmerkingen worden goedgekeurd voordat ze op een publicatiesite kunnen worden weergegeven. De optie Standaard is uitgeschakeld.

* **Gesloten**

  Als deze optie ingeschakeld is, is het forum gesloten voor nieuwe onderwerpen en opmerkingen. De optie Standaard is uitgeschakeld.

* **Rich Text Editor**

  Als deze optie is ingeschakeld, kunnen onderwerpen en opmerkingen worden ingevoerd met een markering. De optie Standaard is uitgeschakeld.

* **Toestaan Tags**

  Als gecontroleerd, sta leden toe om markeringsetiketten aan hun posten toe te voegen (zie &lbrace;het gebied van de Markering **tabel).** De optie Standaard is uitgeschakeld.

* **staat Dossier toe uploadt**

  Als deze optie ingeschakeld is, staat u toe dat bestandsbijlagen worden toegevoegd aan het onderwerp of de opmerking. De optie Standaard is uitgeschakeld.

* **toestaat na**

  Als gecontroleerd, omvat de volgende eigenschap voor forumposten, die leden [ toestaat om ](/help/communities/notifications.md) van nieuwe posten worden op de hoogte gebracht. De optie Standaard is uitgeschakeld.

* **het Draaien** toestaan

  Als deze optie ingeschakeld is, kunnen forumonderwerpen boven aan de lijst met onderwerpen worden vastgezet. De optie Standaard is uitgeschakeld.

* **sta Aanbevolen Inhoud** toe

  Als gecontroleerd, is het idee identificeerbaar als [ gekenmerkte inhoud ](/help/communities/featured.md). De optie Standaard is uitgeschakeld.

* **staat E-mailAbonnementen** toe

  Als gecontroleerd, sta leden toe om van nieuwe posten door e-mail ([ abonnement ](/help/communities/subscriptions.md)) op de hoogte te worden gebracht. Vereist `Allow Following` worden gecontroleerd en [ gevormde e-mail ](/help/communities/email.md). De optie Standaard is uitgeschakeld.

* **Max de Grootte van het Dossier**

  Alleen relevant als `Allow File Uploads` is gecontroleerd. Dit veld beperkt de grootte (in bytes) van een geüpload bestand. De standaardwaarde is 104857600 (10 MB).

* **Toegestane Types van Dossier**

  Alleen relevant als `Allow File Uploads` is gecontroleerd. Een door komma&#39;s gescheiden lijst met bestandsextensies met het scheidingsteken &#39;punt&#39;. Bijvoorbeeld .jpg, .jpeg, .png, .doc, .docx, .pdf. Als er bestandstypen zijn opgegeven, kunnen deze niet worden geüpload. De standaardinstelling is niet opgegeven, zodat alle bestandstypen zijn toegestaan.

* **Max de Grootte van het Dossier van het Beeld van de Band**
Alleen relevant als Uploaden van bestand toestaan is ingeschakeld. Het maximum aantal bytes dat een geüploade afbeeldingsbestand kan hebben. De standaardwaarde is 2097152 (2 MB).

* **staat Verbonden Antwoorden** toe

  Als deze optie is ingeschakeld, kunt u reacties op opmerkingen die naar het onderwerp zijn gepost toestaan. De optie Standaard is uitgeschakeld.

* **Toestaan het Stemmen**

  Indien ingeschakeld, neemt u de functie Stemmen op met een onderwerp. De optie Standaard is uitgeschakeld.

* **staat Gebruikers toe om Commentaren en Onderwerpen te schrappen**

  Als deze optie is ingeschakeld, kunnen leden de opmerkingen en onderwerpen die ze hebben geplaatst verwijderen. De optie Standaard is uitgeschakeld.

* **toon Broodkruimels**

  Indien aangekruist, toon navigatiebroodkruimels op onderwerppagina&#39;s. Standaard is ingeschakeld.

* **Badges van de Vertoning**

  Als gecontroleerd, vertoning verdiende en toegewezen [ badges ](/help/communities/implementing-scoring.md) met de blogingang van een lid. De optie Standaard is uitgeschakeld.

* **staat Geprivilegieerde Leden** toe

  Als deze optie is ingeschakeld, mogen alleen leden met Geprivilegieerde inhoud maken.

* **Toegelaten Geprivilegieerde Leden**

  Voeg de geprivilegieerde leden toe die inhoud mogen maken.

* **Blok gebruiker-Gegenereerde Inhoud in Auteur geeft Wijze** uit

  Als deze optie is ingeschakeld, wordt door de gebruiker gegenereerde inhoud geblokkeerd tijdens het bewerken in de auteurmodus.

* **laat Mentie** toe

  Als deze optie is ingeschakeld, kunnen geregistreerde gebruikers in de gemeenschap andere geregistreerde leden identificeren (met voornaam, achternaam, gebruikersnaam) en ze tags toewijzen met behulp van de algemene syntaxis voor @user-name. De getagde gebruikers ontvangen meldingen over hun berichten.

* **Maximale Onthulpingen**

  Beperk het maximum aantal berichten dat in een bericht is toegestaan. De standaardwaarde is 10.

* **het Patroon van de Mentie UI**

  Geef de patroontekenreeks op die de geregistreerde gebruiker in een bericht mag labelen (@genoemd). Bijvoorbeeld `~{{familyName}}{{givenName}}` .

>[!NOTE]
>
>Het kan nodig zijn om zowel `AllowThreaded Replies` als `Allow users to Delete Comments and Topics` te controleren om commentaren op een onderwerp toe te laten.

#### Tabblad Gebruikersmodernisering {#user-moderation-tab}

Onder het **lusje van de Moderatie van de Gebruiker**, specificeer hoe de geposte onderwerpen en de antwoorden (user-generated inhoud) worden beheerd. Voor meer informatie, zie [ het Matigen van Gebruiker-Gegenereerde Inhoud ](/help/communities/moderate-ugc.md).

* **ontken Post**

  Indien deze optie is ingeschakeld, mogen de verantwoordelijken voor het lid die hun functie hebben erkend, posten ontkennen en voorkomen dat de functie op het openbare forum verschijnt. De optie Standaard is uitgeschakeld.

* **dicht/heropen Onderwerpen**

  Indien gecontroleerd, kunnen de vertrouwde op lidmoderatoren een onderwerp aan verdere uitgeeft en commentaren sluiten, en kunnen een onderwerp ook heropenen. De optie Standaard is uitgeschakeld.

* **Onderwerpen van de Beweging**

  Indien gecontroleerd, sta moderators op toe publiceren kant om onderwerpen te bewegen. Standaard is ingeschakeld.

* **Punten van de Vlag**

  Als deze optie is ingeschakeld, kunnen leden onderwerpen of opmerkingen van anderen als ongeschikt markeren. De optie Standaard is uitgeschakeld.

* **Lijst van de Reden van de Vlag**

  Als deze optie is ingeschakeld, kunnen leden in een vervolgkeuzelijst kiezen waarom een onderwerp of opmerking niet als ongepast wordt gemarkeerd. De optie Standaard is uitgeschakeld.

* **Reden van de Vlag van de Douane**

  Als deze optie is ingeschakeld, kunnen leden hun eigen reden opgeven om een onderwerp of opmerking als ongeschikt te bestempelen. De optie Standaard is uitgeschakeld.

* **Drempel van de Moderatie**

  Ga het aantal tijden in een onderwerp of een commentaar moet door leden worden gemarkeerd alvorens moderators worden meegedeeld. De standaardwaarde is 1 (één keer).

* **het Vlaggen Grens**

  Voer het aantal keren in dat een onderwerp of opmerking moet worden gemarkeerd voordat het wordt verborgen in de openbare weergave. Indien ingesteld op -1, wordt het gemarkeerde onderwerp of de opmerking nooit verborgen in de openbare weergave. Anders, moet dit aantal groter dan of gelijk aan de Drempel van de Moderatie zijn. De standaardwaarde is 5.

#### Tabblad Tagveld {#tag-field-tab}

Onder het **gebied van de Markering** lusje, zijn de markeringen die kunnen worden toegepast, indien toegestaan onder het **3&rbrace; lusje van Montages &lbrace;, beperkt volgens gekozen namespaces.**

* **Toegestane Namespaces**

  Relevant als `Allow Tagging` onder de **Montages** tabel wordt gecontroleerd. De tags die kunnen worden toegepast, zijn beperkt tot de tags binnen de geselecteerde naamruimtecategorieën. De lijst met naamruimten bevat &quot;Standaardtags&quot; (de standaardnaamruimte) en &quot;Alle tags opnemen&quot;. De standaardwaarde is niet ingeschakeld, hetgeen betekent dat alle naamruimten zijn toegestaan.

* **de Grens van de Suggestie**

  Voer het aantal tags in dat moet worden weergegeven als suggestie aan het lid dat naar het forum post. De standaardwaarde is **-**&#x200B;1 (geen limieten).

#### Tabblad Vertaling {#translation-tab}

Onder het **Vertaal** lusje, als de vertaling voor de communautaire plaats wordt toegelaten, kan de vertaling worden geplaatst om het volledige onderwerp of geselecteerde posten te vertalen.

* **vertaal allen**

  Indien gecontroleerd, wordt de forumdraad vertaald in de aangewezen taal van de gebruiker. De optie Standaard is uitgeschakeld.

#### Tabblad Instellingen sorteren {#sort-settings-tab}

Onder het **lusje van de Montages van de Soort**, specificeer hoe de geposte commentaren wanneer getoond worden gesorteerd.

* **Soort door**

  Controleer alle toegestane sorteerselecties: `Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed and Most Liked` . De standaardwaarde is `Newest, Oldest, Last Updated` .

* **Reeks als Gebrek**

  Trek naar beneden om een van de geselecteerde sorteeropties te selecteren die als standaard moeten worden weergegeven. De standaardwaarde is `Newest` .

* **Uitgezochte Opties van de Tijd voor Analytics die** sorteren

  Trek omlaag om een van de volgende opties te selecteren: `All, Last 24 Hours, Last 7 Days, Last 30 Days` .

  De standaardwaarde is `All` .

### Aanvullende informatie {#additional-information}

Meer informatie kan op de [&#128279;](/help/communities/essentials-forum.md) pagina van de Hoofdzaak van het Forum  voor ontwikkelaars worden gevonden.

Voor moderatie van geposte onderwerpen en commentaren, zie [ het Modereren van Gebruiker-Gegenereerde Inhoud ](/help/communities/moderate-ugc.md).

Voor het etiketteren van geposte onderwerpen en commentaren, zie [ Tags Gebruiker-Gegenereerde Inhoud ](/help/communities/tag-ugc.md).

Voor vertaling van geposte onderwerpen en commentaren, zie [ Vertaal Gebruiker-Gegenereerde Inhoud ](/help/communities/translate-ugc.md).
