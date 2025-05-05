---
title: Ideatiefunctie
description: Leer hoe u de functie Ideatie kunt toevoegen en configureren waarmee leden van de gemeenschap ideeën kunnen maken, weergeven, volgen, stemmen en commentaar kunnen geven op ideeën die met de gemeenschap worden gedeeld.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
docset: aem65
exl-id: e130bab4-524d-4413-ba8b-53d0ed9e8623
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '1121'
ht-degree: 0%

---

# Ideatiefunctie {#ideation-feature}

## Inleiding {#introduction}

De ideatiefunctie biedt een gebied voor aangemelde sitebezoekers (leden van de gebruikersgemeenschap) in de Publish-omgeving voor:

* Creëer ideeën om met de gemeenschap te delen.
* Bekijk en becommentariëer ideeën.
* Volg een idee.
* Stem op een idee.

In dit gedeelte van de documentatie wordt het volgende beschreven:

* De ideatiefunctie toevoegen aan een AEM site.
* De montages van de configuratie voor de component van de Ideatie.

### Een idee toevoegen aan een pagina {#adding-a-ideation-to-a-page}

Als u een component `Ideation` in de ontwerpmodus aan een pagina wilt toevoegen, gebruikt u de componentbrowser om te zoeken naar

* `Communities / Ideation`

En sleep het naar zijn plaats op een pagina waar het idee zou moeten verschijnen.

Voor noodzakelijke informatie, bezoek {de Grondbeginselen van de Componenten van 0} Gemeenschappen [&#128279;](/help/communities/basics.md).

Wanneer de [ vereiste cliënt-zijbibliotheken ](/help/communities/ideation.md#essentials-for-client-side) inbegrepen zijn, is dit hoe de `Ideation` component verschijnt:

![ ideatie ](assets/ideation.png)

### Een idee configureren {#configuring-an-ideation}

Selecteer de geplaatste component `Ideation` , zodat u het pictogram `Configure` kunt openen en selecteren waarmee het dialoogvenster Bewerken wordt geopend.

![ vorm-nieuw ](assets/configure-new.png)

![ plaats-montages ](assets/ideation-settings.png)

#### Het tabblad Instellingen {#settings-tab}

Geef onder het tabblad **[!UICONTROL Settings]** instellingen voor ideeën en opmerkingen op:

* **staat de Duimnagel van de Bijlage** toe
* **Max de Grootte van de Duimnagel van de Band**
* **Min de Grootte van het Beeld voor Duimnagel**
* **Max de Grootte van de Duimnagel**
* **staat Geprivilegieerde Leden** toe
* **Toegelaten Geprivilegieerde Leden**
* **Geproduceerde Inhoud van het Blok Gebruiker in Auteur geeft Wijze** uit
* **Titel van de Ideatie**

* De weergavetitel voor het idee. De standaardwaarde is `Ideation` .
* **Beschrijving van de Ideatie**

  Een beschrijving die als ondertitel voor het idee moet worden weergegeven. Standaard is geen beschrijving.

* **Onderwerpen per Pagina**

  Hiermee definieert u het aantal ideeën/posts dat per pagina wordt weergegeven. De standaardwaarde is 10.

* **Gematigd**

  Als deze optie is ingeschakeld, moet het posten van ideeën en opmerkingen worden goedgekeurd voordat ze op een publicatiesite kunnen worden weergegeven. De optie Standaard is uitgeschakeld.

* **Gesloten**

  Als het wordt gecontroleerd, is het ideatieforum gesloten voor nieuwe ideeën en commentaren. De optie Standaard is uitgeschakeld.

* **Rich Text Editor**

  Als deze optie is ingeschakeld, kunnen ideeën en opmerkingen worden ingevoerd met een markering. De optie Standaard is uitgeschakeld.

* **Toestaan Tags**

  Als deze optie is ingeschakeld, kunnen leden labels toevoegen aan hun posts (zie **[!UICONTROL Tag field]** tab). De optie Standaard is uitgeschakeld.

* **staat Dossier toe uploadt**

  Als deze optie is ingeschakeld, kunt u bestandsbijlagen toevoegen aan het idee of de opmerking. De optie Standaard is uitgeschakeld.

* **Max de Grootte van het Dossier**

  Alleen relevant als `Allow File Uploads` is gecontroleerd. Dit veld beperkt de grootte (in bytes) van een geüpload bestand. De standaardwaarde is 104857600 (10 MB).

* **Toegestane Types van Dossier**

  Alleen relevant als `Allow File Uploads` is gecontroleerd. Een door komma&#39;s gescheiden lijst met bestandsextensies met het scheidingsteken &#39;punt&#39;. Bijvoorbeeld .jpg, .jpeg, .png, .doc, .docx, .pdf. Als er bestandstypen zijn opgegeven, kunnen deze niet worden geüpload. De standaardinstelling is niet opgegeven, zodat alle bestandstypen zijn toegestaan.

* **Max de Grootte van het Dossier van het Beeld van de Band**

  Alleen relevant als Uploaden van bestand toestaan is ingeschakeld. Het maximum aantal bytes dat een geüploade afbeeldingsbestand kan hebben. De standaardwaarde is 2097152 (2 MB).

* **sta Antwoorden** toe

  Als deze optie is ingeschakeld, kunt u reacties op opmerkingen op het idee toestaan. De optie Standaard is uitgeschakeld.

* **Toestaan het Stemmen**

  Als deze optie ingeschakeld is, kunt u stemmen over de opmerkingen van een idee. De optie Standaard is uitgeschakeld.

* **staat Gebruikers toe om Commentaren en Onderwerpen te schrappen**

  Als deze optie is ingeschakeld, kunnen leden de opmerkingen en ideeën die ze hebben geplaatst verwijderen. De optie Standaard is uitgeschakeld.

* **toestaat na**

  Als gecontroleerd, omvat de volgende eigenschap voor ideeënposten, die leden [ toestaat om ](/help/communities/notifications.md) van nieuwe posten op de hoogte worden gebracht. De optie Standaard is uitgeschakeld.

* **staat E-mailAbonnementen** toe

  Als gecontroleerd, sta leden toe om van nieuwe posten door e-mail ([ abonnement ](/help/communities/subscriptions.md)) op de hoogte te worden gebracht. Vereist `Allow Following` worden gecontroleerd en [ gevormde e-mail ](/help/communities/email.md). De optie Standaard is uitgeschakeld.

* **Toestaan het Stemmen**

  Als deze optie ingeschakeld is, kunt u stemmen over de opmerkingen van een idee. De optie Standaard is uitgeschakeld.

* **Badges van de Vertoning**

  Als gecontroleerd, vertoning verdiende en toegewezen [ badges ](/help/communities/implementing-scoring.md) met het idee van een lid. De optie Standaard is uitgeschakeld.

* **krijgt geen Antwoorden op het Lijst van Pagina**

* **sta Aanbevolen Inhoud** toe

  Als gecontroleerd, is het idee identificeerbaar als [ gekenmerkte inhoud ](/help/communities/featured.md). De optie Standaard is uitgeschakeld.

* **laat Mentie** toe
* **Maximale Onthulpingen**
* **het Patroon van de Mentie UI**

#### Tabblad Gebruikersmodernisering {#user-moderation-tab}

Geef onder het tabblad **[!UICONTROL User Moderation]** op hoe de geposte ideeën en opmerkingen (door de gebruiker gegenereerde inhoud) worden beheerd. Voor meer informatie, zie [ het Matigen van Gebruiker Gegenereerde Inhoud ](/help/communities/moderate-ugc.md).

* **ontken Post**

  Indien gecontroleerd, kunnen de vertrouwde leden functies ontkennen en voorkomen dat de post op het openbare forum verschijnt. De optie Standaard is uitgeschakeld.

* **dicht/heropen Onderwerpen**

  Indien gecontroleerd, kunnen de vertrouwde op lidmoderatoren een onderwerp aan verdere uitgeeft en commentaren sluiten, en kunnen een onderwerp ook heropenen. De optie Standaard is uitgeschakeld.

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

Onder het tabblad **[!UICONTROL Tag field]** zijn de tags die kunnen worden toegepast, indien toegestaan onder het tabblad **[!UICONTROL Settings]** , beperkt afhankelijk van de gekozen naamruimten.

* **Toegestane Namespaces**

  Relevant als `Allow Tagging` is ingeschakeld onder de tab **[!UICONTROL Settings]** . De tags die kunnen worden toegepast, zijn beperkt tot de tags binnen de geselecteerde naamruimtecategorieën. De lijst met naamruimten bevat &quot;Standaardtags&quot; (de standaardnaamruimte) en &quot;Alle tags opnemen&quot;. De standaardwaarde is niet ingeschakeld, hetgeen betekent dat alle naamruimten zijn toegestaan.

* **de Grens van de Suggestie**

  Voer het aantal tags in dat moet worden weergegeven als suggestie aan het lid dat naar het forum post. De waarde **- 1** betekent geen grens. De standaardwaarde is 0.

#### Tabblad Instellingen sorteren {#sort-settings-tab}

Geef onder het tabblad **[!UICONTROL Sort Settings]** op hoe de geposte opmerkingen worden gesorteerd wanneer ze worden weergegeven.

* **Soort door**

  Alle toegestane sorteerselecties controleren: `Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed and Most Liked`. De standaardwaarde is `Newest, Oldest, Last Updated` .

* **Reeks als Gebrek**

  Trek naar beneden om een van de geselecteerde sorteeropties te selecteren die als standaard moeten worden weergegeven. De standaardwaarde is `Newest` .

* **Uitgezochte Opties van de Tijd voor Analytics die** sorteren

  Trek omlaag om een van `All, Last 24 Hours, Last 7 Days, Last 30 Days` te selecteren. De standaardwaarde is `All` .

## Ervaring met sitebezoekers {#site-visitor-experience}

### Idea maken {#creating-idea}

Net als bij alle andere communautaire kenmerken kan een bezoeker van de site alleen ideeën lezen en andere meningen bekijken (door opmerkingen en stemmen/houden) als hij niet is aangemeld.

Na aanmelding kan een lid een idee maken.

![ creeer-nieuw-idee ](assets/create-new-idea.png)

Voordat het idee wordt verzonden, kan het lid een concept opslaan.

Door de knop `Save as Draft` te selecteren, wordt een concept opgeslagen.

![ sparen-idee ](assets/save-idea.png)

Als u opgeslagen concepten weergeeft op het tabblad `My Drafts` , selecteert u `Read More` om de bewerkingsmodus opnieuw in te schakelen:

![ geef-idee uit ](assets/edit-idea.png)

#### Feedback geven {#providing-feedback}

Als het idee eenmaal is gepubliceerd, kunnen andere leden zich aanmelden, het idee ( `Read More` ) openen en het idee op deze manier toevoegen, het aantal stemmen verhogen en opmerkingen maken.

![ terugkoppelt ](assets/feedback-idea.png)

### Aanvullende informatie {#additional-information}

Meer informatie kan op de [&#128279;](/help/communities/ideation.md) pagina van de Hoofdzaak van de Ideatie  voor ontwikkelaars worden gevonden.

Voor moderatie van geposte onderwerpen en commentaren, zie [ het Modereren van Gebruiker Gegenereerde Inhoud ](/help/communities/moderate-ugc.md).

Voor het etiketteren van geposte onderwerpen en commentaren, zie [ Tags Gebruiker Gegenereerde Inhoud ](/help/communities/tag-ugc.md).
