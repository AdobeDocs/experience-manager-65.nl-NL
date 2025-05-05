---
title: Functie Vragen en antwoorden op forum
description: Leer hoe u de functie voor het QnA-forum toevoegt aan een pagina waarop ingetekende communityleden vragen kunnen stellen en beantwoorden.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
docset: aem65
exl-id: 17081710-35e0-4f5b-9485-1f85c065fd70
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '1389'
ht-degree: 0%

---

# Functie Vragen en antwoorden op forum{#q-a-forum-feature}

## Inleiding {#introduction}

De functie van het QnA-forum (vragen en antwoorden) biedt leden van de gemeenschap de mogelijkheid vragen te stellen en te beantwoorden. Leden kunnen:

* Vragen maken
* Inline-afbeeldingen toevoegen (met ondersteuning voor slepen en neerzetten)
* Vragen weergeven en beantwoorden
* Zoeken naar een vraag
* De QnA-inhoud helpen matigen
* Beste antwoorden identificeren
* QnA-vragen van de ene pagina naar de andere verplaatsen

In de documentatie wordt beschreven:

* Het toevoegen van de QnA forumeigenschap aan een AEM plaats.
* De montages van de configuratie voor de `QnA` component.

## Een forum voor vragen en antwoorden toevoegen aan een pagina {#adding-a-q-a-forum-to-a-page}

Als u een component `QnA` in de ontwerpmodus aan een pagina wilt toevoegen, gebruikt u de componentbrowser om `Communities / QnA` te zoeken en sleept u deze naar de juiste plaats op een pagina waarop het forum QnA moet worden weergegeven.

Voor noodzakelijke informatie, bezoek {de Grondbeginselen van de Componenten van 0} Gemeenschappen [&#128279;](/help/communities/basics.md).

Wanneer de [ vereiste cliënt-zijbibliotheken ](/help/communities/qna-essentials.md#essentials-for-client-side) inbegrepen zijn, is dit hoe de `QnA` component verschijnt:

![ qna-component ](assets/qna-component.png)

### QnA configureren {#configuring-qna}

Selecteer de geplaatste component `QnA` , zodat u het pictogram `Configure` kunt openen en selecteren waarmee het dialoogvenster Bewerken wordt geopend.

![ vormen ](assets/configure-new.png)

![ qna-config ](assets/qna-config.png)

#### Het tabblad Instellingen {#settings-tab}

Onder het **lusje van Montages**, specificeer montages voor onderwerpen (vragen) en antwoorden (antwoorden):

* **staat de Duimnagel van de Bijlage** toe

  Als deze optie is ingeschakeld, wordt een miniatuur van de bijgevoegde afbeelding gemaakt.

* **Max de Grootte van de Duimnagel van de Band**

  Maximale grootte (in pixels) van de miniatuurafbeelding van de bijlage. De standaardwaarde is 800 x 800.

* **Min de Grootte van het Beeld voor Duimnagel**

  Minimale afbeeldingsgrootte (in bytes) voor het genereren van miniaturen voor inline-afbeeldingen. De standaardwaarde is 100000 bytes (100 kB).

* **Max de Grootte van de Duimnagel**

  Maximale grootte (in pixels) van de miniatuurafbeelding voor inline-afbeelding. De standaardwaarde is 800 x 800.

* **Onderwerpen per Pagina**

  Hiermee definieert u het aantal vragen/berichten dat per pagina wordt weergegeven. De standaardwaarde is 10.

* **Gematigd**

  Als deze optie is ingeschakeld, moet het posten van onderwerpen en opmerkingen worden goedgekeurd voordat ze op een publicatiesite worden weergegeven. De optie Standaard is uitgeschakeld.

* **Gesloten**

  Als het forum wordt gecontroleerd, is het gesloten voor nieuwe vragen en commentaren. De optie Standaard is uitgeschakeld.

* **Rich Text Editor**

  Als deze optie is ingeschakeld, kunnen onderwerpen en opmerkingen worden ingevoerd met een markering. De optie Standaard is uitgeschakeld.

* **Toestaan Tags**

  Als gecontroleerd, sta leden toe om markeringsetiketten aan hun posten toe te voegen (zie &lbrace;het gebied van de Markering **tabel).** De optie Standaard is uitgeschakeld.

* **staat Dossier toe uploadt**

  Als deze optie is ingeschakeld, kunt u bestandsbijlagen toevoegen aan de vraag of opmerking. De optie Standaard is uitgeschakeld.

* **toestaat na**

  Als gecontroleerd, omvat de volgende eigenschap voor forumposten, die leden [ toestaat om ](/help/communities/notifications.md) van nieuwe posten worden op de hoogte gebracht. De optie Standaard is uitgeschakeld.

* **het Draaien** toestaan

  Indien gecontroleerd, kunnen de forumonderwerpen aan de bovenkant van de lijst van onderwerpen worden vastgezet. De optie Standaard is uitgeschakeld.

* **staat E-mailAbonnementen** toe

  Als gecontroleerd, sta leden toe om van nieuwe posten door e-mail ([ abonnement ](/help/communities/subscriptions.md)) op de hoogte te worden gebracht. Vereist toestaan na worden gecontroleerd en [ gevormde e-mail ](/help/communities/email.md). De optie Standaard is uitgeschakeld.

* **Max de Grootte van het Dossier**

  Alleen relevant als `Allow File Uploads` is gecontroleerd. Dit veld beperkt de grootte (in bytes) van een geüpload bestand. De standaardwaarde is 104857600 (10 MB).

* **Toegestane Types van Dossier**

  Alleen relevant als `Allow File Uploads` is gecontroleerd. Een door komma&#39;s gescheiden lijst met bestandsextensies met het scheidingsteken &#39;punt&#39;. Bijvoorbeeld: .jpg, .jpeg, .png, .doc, .docx, .pdf. Als er bestandstypen zijn opgegeven, kunnen deze niet worden geüpload. Het gebrek is niets gespecificeerd dusdanig dat **alle** dossiertypes worden toegestaan.

* **Max de Grootte van het Dossier van het Beeld van de Band**

  Alleen relevant als Uploaden van bestand toestaan is ingeschakeld. Het maximum aantal bytes dat een geüploade afbeeldingsbestand kan hebben. De standaardwaarde is 2097152 (2 MB).

* **sta Antwoorden** toe

  Als deze optie is ingeschakeld, kunt u reacties op opmerkingen op de vraag toestaan. De optie Standaard is uitgeschakeld.

* **Toestaan het Stemmen**

  Als deze optie is ingeschakeld, voegt u de functie Stemmen toe aan een vraag. De optie Standaard is uitgeschakeld.

* **staat Gebruikers toe om Commentaren en Onderwerpen te schrappen**

  Als deze optie is ingeschakeld, kunnen leden de opmerkingen en vragen verwijderen die ze hebben geplaatst. De optie Standaard is uitgeschakeld.

* **staat Geprivilegieerde Leden** toe

  Als deze optie is ingeschakeld, mogen alleen leden met Geprivilegieerde inhoud maken.

* **Geproduceerde Inhoud van het Blok Gebruiker in Auteur geeft Wijze** uit

  Als deze optie is ingeschakeld, wordt door de gebruiker gegenereerde inhoud geblokkeerd tijdens het bewerken in de ontwerpmodus.

* **Beweeg Geselecteerd Antwoord aan de bovenkant**

  Als deze optie ingeschakeld is, wordt een eerste weergegeven antwoord geselecteerd. De optie Standaard is uitgeschakeld.
* **Badges van de Vertoning**

  Als gecontroleerd, vertoning verdiende en toegewezen [ badges ](/help/communities/implementing-scoring.md) met de blogingang van een lid. De optie Standaard is uitgeschakeld.

* **sta Aanbevolen Inhoud** toe

  Als gecontroleerd, is het idee identificeerbaar als [ gekenmerkte inhoud ](/help/communities/featured.md). De optie Standaard is uitgeschakeld.

* **laat Mentie** toe

  Als deze optie is ingeschakeld, kunnen geregistreerde gebruikers in de gemeenschap andere geregistreerde leden identificeren (met voornaam, achternaam, gebruikersnaam) en ze tags toewijzen met behulp van de algemene syntaxis voor @user-name. De getagde gebruikers ontvangen meldingen over hun berichten.

* **Maximale Onthulpingen**

  Beperk het maximum aantal berichten dat in een bericht is toegestaan. De standaardwaarde is 10.

* **het Patroon van de Mentie UI**

  Geef de patroontekenreeks op die de geregistreerde gebruiker in een bericht mag labelen (@genoemd). Bijvoorbeeld `~{{familyName}}{{givenName}}` .

#### Tabblad Gebruikersmodernisering {#user-moderation-tab}

Onder het **lusje van de Moderatie van de Gebruiker**, specificeer hoe de geposte onderwerpen (vragen) en de antwoorden (gebruiker geproduceerde inhoud) worden beheerd. Voor meer informatie, zie [ het Matigen van Gebruiker Gegenereerde Inhoud ](/help/communities/moderate-ugc.md).

* **ontken Antwoorden**

  Als deze optie is ingeschakeld, mogen vertrouwde moderatoren van leden geposte antwoorden weigeren en voorkomen dat de antwoorden op het openbare forum met vragen en antwoorden verschijnen. De optie Standaard is uitgeschakeld.

* **dicht/heropen Onderwerpen**

  Indien gecontroleerd, kunnen de vertrouwde op lidmoderatoren een vraag (onderwerp) aan verdere uitgeeft en antwoorden sluiten, en ook een vraag heropenen. De optie Standaard is uitgeschakeld.

* **Onderwerpen van de Beweging**
Als deze optie ingeschakeld is, stelt u moderatoren aan de publiczijde in staat vragen te verplaatsen. De optie Standaard is uitgeschakeld.

* **Punten van de Vlag**

  Als deze optie is ingeschakeld, kunnen leden de vragen of antwoorden van anderen als ongeschikt markeren. De optie Standaard is uitgeschakeld.

* **Lijst van de Reden van de Vlag**

  Als deze optie is ingeschakeld, kunnen leden in een vervolgkeuzelijst kiezen waarom een vraag of antwoord onjuist is. De optie Standaard is uitgeschakeld.

* **Reden van de Vlag van de Douane**

  Als deze optie is ingeschakeld, kunnen leden hun eigen reden opgeven om een vraag of antwoord als ongeschikt te bestempelen. De optie Standaard is uitgeschakeld.

* **Drempel van de Moderatie**

  Voer het aantal keren in dat een vraag of antwoord moet worden gemarkeerd door leden voordat moderatoren op de hoogte worden gesteld. De standaardwaarde is 1 (één keer).

* **het Vlaggen Grens**

  Voer het aantal keren in dat een vraag of antwoord moet worden gemarkeerd voordat deze wordt verborgen in de openbare weergave. Indien ingesteld op -1, wordt de gemarkeerde vraag of het gemarkeerde antwoord nooit verborgen voor de openbare weergave. Anders, moet dit aantal groter dan of gelijk aan de Drempel van de Moderatie zijn. De standaardwaarde is 5.

#### Tabblad Tagveld {#tag-field-tab}

Onder het **gebied van de Markering** lusje, zijn de markeringen die kunnen worden toegepast, indien toegestaan onder het **3&rbrace; lusje van Montages &lbrace;, beperkt volgens gekozen namespaces.**

* **Toegestane Namespaces**

  Relevant als `Allow Tagging` onder de **Montages** tabel wordt gecontroleerd. De tags die kunnen worden toegepast, zijn beperkt tot de tags binnen de geselecteerde naamruimtecategorieën. De lijst met naamruimten bevat &quot;Standaardtags&quot; (de standaardnaamruimte) en &quot;Alle tags opnemen&quot;. De standaardwaarde is niet ingeschakeld, hetgeen betekent dat alle naamruimten zijn toegestaan.

* **de Grens van de Suggestie**

  Voer het aantal tags in dat moet worden weergegeven als suggestie aan het lid dat naar het forum post. De waarde **-**&#x200B;1 betekent geen limieten. De standaardwaarde is 0.

#### Tabblad Instellingen sorteren {#sort-settings-tab}

Onder het **lusje van de Montages van de Soort**, specificeer hoe de geposte commentaren wanneer getoond worden gesorteerd.

* **Soort door**

  Alle toegestane sorteerselecties controleren: `Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed and Most Liked`. De standaardwaarde is `Newest, Oldest, Last Updated` .

* **Reeks als Gebrek**

  Trek naar beneden om een van de geselecteerde sorteeropties te selecteren die als standaard moeten worden weergegeven. De standaardwaarde is `Newest` .

* **Uitgezochte Opties van de Tijd voor Analytics die** sorteren

  Vervolgkeuzelijst om een van de opties `All, Last 24 Hours, Last 7 Days, Last 30 Days` te selecteren. De standaardwaarde is `All` .

## Ervaring met sitebezoekers {#site-visitor-experience}

### Antwoorden identificeren {#identifying-answers}

Een antwoord kan met de knop `Select Answer` worden gemarkeerd als een correct of nuttig antwoord. Als een vraag is gemarkeerd als Beantwoord, kan een ander antwoord pas worden geselecteerd als de eerste is uitgeschakeld met de knop `Unmark Chosen Answer` .

Als deze optie is geselecteerd als een handig antwoord, kunt u de selectie opheffen met de knop `Unmark Chosen Answer` .

Zodra een antwoord als levensvatbaar antwoord wordt geselecteerd, wordt een aanwijzing dat de vraag `Answered` is getoond naast het vraagonderwerp op de belangrijkste pagina QnA.

#### Moderatoren en beheerders {#moderators-and-administrators}

Wanneer de ondertekende binnen gebruiker moderator of beheerdervoorrechten heeft, kunnen zij de matigingstaken uitvoeren die door de configuratie van de component worden toegestaan, ongeacht wie de vraag of het antwoord authored.

Ze kunnen ook antwoorden identificeren.

#### Leden {#members}

Afhankelijk van de configuratie kunnen bezoekers zich aanmelden bij de site:

* Post een nieuwe vraag.
* Bewerk of verwijder de vragen die ze hebben geschreven.
* Vlagvragen of antwoorden van andere leden.
* Antwoorden identificeren voor vragen die ze hebben geschreven.

#### Anoniem {#anonymous}

Sitebezoekers die niet zijn aangemeld, kunnen alleen geposte vragen en antwoorden lezen, deze vertalen als ze hiervoor ondersteuning krijgen, maar ze kunnen geen vraag of antwoord toevoegen, noch vlagberichten van anderen.

## Aanvullende informatie {#additional-information}

Meer informatie kan op de [ QnA Hoofdzaak ](/help/communities/qna-essentials.md) pagina voor ontwikkelaars worden gevonden.

Voor moderatie van geposte onderwerpen en commentaren, zie [ het Modereren van Gebruiker Gegenereerde Inhoud ](/help/communities/moderate-ugc.md).

Voor het etiketteren van geposte onderwerpen en commentaren, zie [ Tags Gebruiker Gegenereerde Inhoud ](/help/communities/tag-ugc.md).
