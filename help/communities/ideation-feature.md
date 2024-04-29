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

De functie Ideatie biedt een gebied voor ingetekende sitebezoekers (leden van de community) in de omgeving Publiceren voor:

* Creëer ideeën om met de gemeenschap te delen.
* Bekijk en becommentariëer ideeën.
* Volg een idee.
* Stem op een idee.

In dit gedeelte van de documentatie wordt het volgende beschreven:

* De ideatiefunctie toevoegen aan een AEM site.
* De montages van de configuratie voor de component van de Ideatie.

### Een idee toevoegen aan een pagina {#adding-a-ideation-to-a-page}

Als u een `Ideation` van een component aan een pagina op auteurswijze, gebruik componentenbrowser om van

* `Communities / Ideation`

En sleep het naar zijn plaats op een pagina waar het idee zou moeten verschijnen.

Voor de nodige informatie gaat u naar [Grondbeginselen van Community-componenten](/help/communities/basics.md).

Wanneer de [vereiste clientbibliotheken](/help/communities/ideation.md#essentials-for-client-side) worden opgenomen, is dit hoe `Ideation` wordt weergegeven:

![ideatie](assets/ideation.png)

### Een idee configureren {#configuring-an-ideation}

Selecteer de geplaatste `Ideation` zodat u toegang hebt tot `Configure` wordt het dialoogvenster Bewerken geopend.

![configure-new](assets/configure-new.png)

![video-instellingen](assets/ideation-settings.png)

#### Het tabblad Instellingen {#settings-tab}

Onder de **[!UICONTROL Settings]** tabblad, geeft u instellingen voor ideeën en opmerkingen op:

* **Miniatuur van bijlage toestaan**
* **Maximale grootte miniatuur bijvoegen**
* **Minimale afbeeldingsgrootte voor miniatuur**
* **Maximale miniatuurgrootte**
* **Geprivilegieerde leden toestaan**
* **Toegestane geprivilegieerde leden**
* **Door gebruiker gegenereerde inhoud blokkeren in de bewerkingsmodus van auteur**
* **Titel van idee**

* De weergavetitel voor het idee. Standaard is `Ideation`.
* **Beschrijving van idee**

  Een beschrijving die als ondertitel voor het idee moet worden weergegeven. Standaard is geen beschrijving.

* **Onderwerpen per pagina**

  Hiermee definieert u het aantal ideeën/posts dat per pagina wordt weergegeven. De standaardwaarde is 10.

* **Gematigd**

  Als deze optie is ingeschakeld, moet het posten van ideeën en opmerkingen worden goedgekeurd voordat ze op een publicatiesite kunnen worden weergegeven. De optie Standaard is uitgeschakeld.

* **Gesloten**

  Als het wordt gecontroleerd, is het ideatieforum gesloten voor nieuwe ideeën en commentaren. De optie Standaard is uitgeschakeld.

* **RTF-editor**

  Als deze optie is ingeschakeld, kunnen ideeën en opmerkingen worden ingevoerd met een markering. De optie Standaard is uitgeschakeld.

* **Tags toestaan**

  Als deze optie is ingeschakeld, kunnen leden labels toevoegen aan hun berichten (zie **[!UICONTROL Tag field]** ). De optie Standaard is uitgeschakeld.

* **Uploaden van bestanden toestaan**

  Als deze optie is ingeschakeld, kunt u bestandsbijlagen toevoegen aan het idee of de opmerking. De optie Standaard is uitgeschakeld.

* **Max. bestandsgrootte**

  Alleen relevant als `Allow File Uploads` is ingeschakeld. Dit veld beperkt de grootte (in bytes) van een geüpload bestand. De standaardwaarde is 104857600 (10 MB).

* **Toegestane bestandstypen**

  Alleen relevant als `Allow File Uploads` is ingeschakeld. Een door komma&#39;s gescheiden lijst met bestandsextensies met het scheidingsteken &#39;punt&#39;. Bijvoorbeeld .jpg, .jpeg, .png, .doc, .docx, .pdf. Als er bestandstypen zijn opgegeven, kunnen deze niet worden geüpload. De standaardinstelling is niet opgegeven, zodat alle bestandstypen zijn toegestaan.

* **Maximale bestandsgrootte afbeelding bijvoegen**

  Alleen relevant als Uploaden van bestand toestaan is ingeschakeld. Het maximum aantal bytes dat een geüploade afbeeldingsbestand kan hebben. De standaardwaarde is 2097152 (2 MB).

* **Reacties toestaan**

  Als deze optie is ingeschakeld, kunt u reacties op opmerkingen op het idee toestaan. De optie Standaard is uitgeschakeld.

* **Stemmen toestaan**

  Als deze optie ingeschakeld is, kunt u stemmen over de opmerkingen van een idee. De optie Standaard is uitgeschakeld.

* **Gebruikers toestaan opmerkingen en onderwerpen te verwijderen**

  Als deze optie is ingeschakeld, kunnen leden de opmerkingen en ideeën die ze hebben geplaatst verwijderen. De optie Standaard is uitgeschakeld.

* **Volgen toestaan**

  Als deze optie is ingeschakeld, neemt u de volgende functie op voor ideeënposts, waardoor leden kunnen worden [aangemeld](/help/communities/notifications.md) van nieuwe posten. De optie Standaard is uitgeschakeld.

* **E-mailabonnementen toestaan**

  Als deze optie ingeschakeld is, kunnen leden per e-mail op de hoogte worden gesteld van nieuwe berichten ([abonnement](/help/communities/subscriptions.md)). Vereisten `Allow Following` te controleren en [e-mail geconfigureerd](/help/communities/email.md). De optie Standaard is uitgeschakeld.

* **Stemmen toestaan**

  Als deze optie ingeschakeld is, kunt u stemmen over de opmerkingen van een idee. De optie Standaard is uitgeschakeld.

* **Badges weergeven**

  Indien ingeschakeld, verdiende en toegewezen weergave [badges](/help/communities/implementing-scoring.md) met het idee van een lid. De optie Standaard is uitgeschakeld.

* **Geen reacties ophalen op aanbiedingspagina**

* **Aanbevolen inhoud toestaan**

  Als deze optie ingeschakeld is, kan het idee worden herkend als [aanbevolen inhoud](/help/communities/featured.md). De optie Standaard is uitgeschakeld.

* **Menu inschakelen**
* **Max. aantal meldingen**
* **Menatiepatroon gebruikersinterface**

#### Tabblad Gebruikersmodernisering {#user-moderation-tab}

Onder de **[!UICONTROL User Moderation]** , geeft u op hoe de geposte ideeën en opmerkingen (door de gebruiker gegenereerde inhoud) worden beheerd. Zie voor meer informatie [Door gebruiker gegenereerde inhoud modereren](/help/communities/moderate-ugc.md).

* **Posten weigeren**

  Indien gecontroleerd, kunnen de vertrouwde leden functies ontkennen en voorkomen dat de post op het openbare forum verschijnt. De optie Standaard is uitgeschakeld.

* **Onderwerpen sluiten/opnieuw openen**

  Indien gecontroleerd, kunnen de vertrouwde op lidmoderatoren een onderwerp aan verdere uitgeeft en commentaren sluiten, en kunnen een onderwerp ook heropenen. De optie Standaard is uitgeschakeld.

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

Onder de **[!UICONTROL Tag field]** , de tags die kunnen worden toegepast, indien toegestaan onder de **[!UICONTROL Settings]** zijn beperkt op basis van de gekozen naamruimten.

* **Toegestane naamruimten**

  Relevant indien `Allow Tagging` wordt gecontroleerd onder de **[!UICONTROL Settings]** tab. De tags die kunnen worden toegepast, zijn beperkt tot de tags binnen de geselecteerde naamruimtecategorieën. De lijst met naamruimten bevat &quot;Standaardtags&quot; (de standaardnaamruimte) en &quot;Alle tags opnemen&quot;. De standaardwaarde is niet ingeschakeld, hetgeen betekent dat alle naamruimten zijn toegestaan.

* **Suggestiegrenswaarde**

  Voer het aantal tags in dat moet worden weergegeven als suggestie aan het lid dat naar het forum post. Een waarde van **-1** betekent geen limiet. De standaardwaarde is 0.

#### Tabblad Instellingen sorteren {#sort-settings-tab}

Onder de **[!UICONTROL Sort Settings]** , geeft u op hoe de geposte opmerkingen worden gesorteerd wanneer deze worden weergegeven.

* **Sorteren op**

  Alle toegestane sorteerselecties controleren: `Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed and Most Liked`. Standaard is `Newest, Oldest, Last Updated`.

* **Instellen als standaard**

  Trek naar beneden om een van de geselecteerde sorteeropties te selecteren die als standaard moeten worden weergegeven. Standaard is `Newest`.

* **Tijdopties selecteren voor het sorteren van analysemogelijkheden**

  Omlaag trekken om een van de `All, Last 24 Hours, Last 7 Days, Last 30 Days`. Standaard is `All`.

## Ervaring met sitebezoekers {#site-visitor-experience}

### Idea maken {#creating-idea}

Net als bij alle andere communautaire kenmerken kan een bezoeker van de site alleen ideeën lezen en andere meningen bekijken (door opmerkingen en stemmen/houden) als hij niet is aangemeld.

Na aanmelding kan een lid een idee maken.

![creatief-nieuw-idee](assets/create-new-idea.png)

Voordat het idee wordt verzonden, kan het lid een concept opslaan.

Als u `Save as Draft` wordt een concept opgeslagen.

![sparen-idee](assets/save-idea.png)

Bij weergave van opgeslagen concepten in de `My Drafts` tab, selecteert u `Read More` om de bewerkingsmodus opnieuw in te schakelen:

![bewerken-idee](assets/edit-idea.png)

#### Feedback geven {#providing-feedback}

Als het idee eenmaal is gepubliceerd, kunnen andere leden zich aanmelden, het idee openen ( `Read More`) en het idee, waardoor het aantal stemmen wordt vergroot en er opmerkingen over worden gemaakt.

![feedback](assets/feedback-idea.png)

### Aanvullende informatie {#additional-information}

Meer informatie is te vinden op de [Essentiële elementen voor ideeën](/help/communities/ideation.md) pagina voor ontwikkelaars.

Voor moderatie van geposte onderwerpen en commentaren, zie [Door gebruiker gegenereerde inhoud modereren](/help/communities/moderate-ugc.md).

Voor het etiketteren van geposte onderwerpen en commentaren, zie [Door gebruiker gegenereerde inhoud labelen](/help/communities/tag-ugc.md).
