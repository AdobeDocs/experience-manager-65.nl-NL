---
title: Ideatiefunctie
seo-title: Ideatiefunctie
description: De functie Ideatie toevoegen en configureren
seo-description: De functie Ideatie toevoegen en configureren
uuid: 38468290-6d00-4ee4-91d8-7c2e8ae32712
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: a3f5a21d-2df6-4663-a1ea-3a067c46f860
docset: aem65
translation-type: tm+mt
source-git-commit: f62fb1eb760ddd7baee9ba5a631ff4b921e2d08b
workflow-type: tm+mt
source-wordcount: '1113'
ht-degree: 0%

---


# Ideeigenschap {#ideation-feature}

## Inleiding {#introduction}

De functie Ideatie biedt een gebied voor ingetekende sitebezoekers (leden van de community) in de publicatieomgeving voor:

* Creëer ideeën om met de gemeenschap te delen.
* Bekijk en becommentariëer ideeën.
* Volg een idee.
* Stem op een idee.

In dit gedeelte van de documentatie wordt het volgende beschreven:

* De ideatiefunctie toevoegen aan een AEM site.
* De montages van de configuratie voor de component van de Ideatie.

### Een idee toevoegen aan een pagina {#adding-a-ideation-to-a-page}

Als u een `Ideation`-component in de ontwerpmodus aan een pagina wilt toevoegen, gebruikt u de componentbrowser om te zoeken naar

* `Communities / Ideation`

en sleep het naar de gewenste plaats op een pagina.

Voor noodzakelijke informatie, bezoek [de Grondbeginselen van Componenten van Gemeenschappen](/help/communities/basics.md).

Wanneer de [vereiste client-side bibliotheken](/help/communities/ideation.md#essentials-for-client-side) worden opgenomen, wordt de `Ideation`-component op deze manier weergegeven:

![ideatie](assets/ideation.png)

### Een idee {#configuring-an-ideation} configureren

Selecteer de geplaatste `Ideation` component en selecteer `Configure` pictogram dat het Edit dialoog opent.

![configure-new](assets/configure-new.png)

![video-instellingen](assets/ideation-settings.png)

#### Tabblad Instellingen {#settings-tab}

Geef onder het tabblad **[!UICONTROL Settings]** instellingen voor ideeën en opmerkingen op:

* **Miniatuur van bijlage toestaan**
* **Maximale grootte miniatuur bijvoegen**
* **Minimale afbeeldingsgrootte voor miniatuur**
* **Maximale miniatuurgrootte**
* **Geprivilegieerde leden toestaan**
* **Toegestane geprivilegieerde leden**
* **Door gebruiker gegenereerde inhoud blokkeren in de bewerkingsmodus van auteur**
* **Titel van idee**

* De weergavetitel voor het idee. De standaardwaarde is `Ideation`.
* **Beschrijving van idee**

   Een beschrijving die als ondertitel voor het idee moet worden weergegeven. Standaard is geen beschrijving.

* **Onderwerpen per pagina**

   Hiermee definieert u het aantal ideeën/posts dat per pagina wordt weergegeven. De standaardwaarde is 10.

* **Gematigd**

   Als deze optie is ingeschakeld, moet het posten van ideeën en opmerkingen worden goedgekeurd voordat ze op een publicatiesite worden weergegeven. De optie Standaard is uitgeschakeld.

* **Gesloten**

   Als het wordt gecontroleerd, is het ideatieforum gesloten voor nieuwe ideeën en commentaren. De optie Standaard is uitgeschakeld.

* **RTF-editor**

   Als deze optie is ingeschakeld, kunnen ideeën en opmerkingen worden ingevoerd met een markering. De optie Standaard is uitgeschakeld.

* **Tags toestaan**

   Als deze optie is ingeschakeld, kunnen leden labellabels aan hun post toevoegen (zie **[!UICONTROL Tag field]** tabblad). De optie Standaard is uitgeschakeld.

* **Uploaden van bestanden toestaan**

   Als deze optie is ingeschakeld, kunt u bestandsbijlagen toevoegen aan het idee of de opmerking. De optie Standaard is uitgeschakeld.

* **Max. bestandsgrootte**

   Alleen relevant als `Allow File Uploads` is ingeschakeld. Met dit veld wordt de grootte (in bytes) van een geüpload bestand beperkt. De standaardwaarde is 104857600 (10 MB).

* **Toegestane bestandstypen**

   Alleen relevant als `Allow File Uploads` is ingeschakeld. Een door komma&#39;s gescheiden lijst met bestandsextensies met het &quot;punt&quot;-scheidingsteken. Bijvoorbeeld: .jpg, .jpeg, .png, .doc, .docx, .pdf. Als er bestandstypen zijn opgegeven, mogen de niet opgegeven bestandstypen niet worden geüpload. De standaardinstelling is niet opgegeven, zodat alle bestandstypen zijn toegestaan.

* **Maximale bestandsgrootte afbeelding bijvoegen**

   Alleen relevant als Uploaden van bestand toestaan is ingeschakeld. Het maximum aantal bytes dat een geüploade afbeeldingsbestand kan hebben. De standaardwaarde is 2097152 (2 MB).

* **Reacties toestaan**

   Als deze optie is ingeschakeld, kunt u reacties op opmerkingen op het idee toestaan. De optie Standaard is uitgeschakeld.

* **Stemmen toestaan**

   Als deze optie ingeschakeld is, kunt u stemmen over de opmerkingen van een idee. De optie Standaard is uitgeschakeld.

* **Gebruikers toestaan opmerkingen en onderwerpen te verwijderen**

   Als deze optie is ingeschakeld, kunnen leden de opmerkingen en ideeën die ze hebben geplaatst verwijderen. De optie Standaard is uitgeschakeld.

* **Volgen toestaan**

   Als deze optie is ingeschakeld, neemt u de volgende functie op voor ideeënposts, waardoor leden [op de hoogte kunnen worden gesteld](/help/communities/notifications.md) van nieuwe posten. De optie Standaard is uitgeschakeld.

* **E-mailabonnementen toestaan**

   Als deze optie is ingeschakeld, kunnen leden via e-mail op de hoogte worden gesteld van nieuwe berichten ([abonnement](/help/communities/subscriptions.md)). `Allow Following` moet worden gecontroleerd en [e-mail geconfigureerd](/help/communities/email.md). De optie Standaard is uitgeschakeld.

* **Stemmen toestaan**

   Als deze optie ingeschakeld is, kunt u stemmen over de opmerkingen van een idee. De optie Standaard is uitgeschakeld.

* **Badges weergeven**

   Als deze optie is ingeschakeld, wordt de weergave verdiend en [badges](/help/communities/implementing-scoring.md) toegewezen aan het idee van een lid. De optie Standaard is uitgeschakeld.

* **Geen reacties ophalen op aanbiedingspagina**

* **Aanbevolen inhoud toestaan**

   Als deze optie is ingeschakeld, kan het idee worden geïdentificeerd als [aanbevolen inhoud](/help/communities/featured.md). De optie Standaard is uitgeschakeld.

* **Menu inschakelen**
* **Max. aantal meldingen**
* **Menatiepatroon gebruikersinterface**

#### Tabblad Gebruikersmodernisering {#user-moderation-tab}

Geef onder het tabblad **[!UICONTROL User Moderation]** op hoe de geposte ideeën en opmerkingen (door de gebruiker gegenereerde inhoud) worden beheerd. Zie [Door gebruiker gegenereerde inhoud modereren](/help/communities/moderate-ugc.md) voor meer informatie.

* **Posten weigeren**

   Als deze optie wordt ingeschakeld, zullen de verantwoordelijken van de leden hun functie kunnen ontkennen en voorkomen dat de functie op het openbare forum verschijnt. De optie Standaard is uitgeschakeld.

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

#### Tabblad {#tag-field-tab} voor tagveld

Onder het tabblad **[!UICONTROL Tag field]** zijn de tags die kunnen worden toegepast, indien toegestaan onder het tabblad **[!UICONTROL Settings]**, beperkt op basis van de gekozen naamruimten.

* **Toegestane naamruimten**

   Relevant als `Allow Tagging` wordt gecontroleerd onder **[!UICONTROL Settings]** tabel. De tags die kunnen worden toegepast, zijn beperkt tot de tags binnen de geselecteerde naamruimtecategorieën. De lijst met naamruimten bevat &#39;Standaardtags&#39; (de standaardnaamruimte) en &#39;Alle tags opnemen&#39;. De standaardwaarde is niet ingeschakeld, hetgeen betekent dat alle naamruimten zijn toegestaan.

* **Suggestiegrenswaarde**

   Voer het aantal tags in dat moet worden weergegeven als suggestie aan het lid dat naar het forum post. De waarde **-1** betekent geen limiet. De standaardwaarde is 0.

#### Tabblad Instellingen sorteren {#sort-settings-tab}

Geef onder het tabblad **[!UICONTROL Sort Settings]** op hoe de geposte opmerkingen worden gesorteerd wanneer ze worden weergegeven.

* **Sorteren op**

   Alle toegestane sorteerselecties controleren: `Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed and Most Liked`. De standaardwaarde is `Newest, Oldest, Last Updated`.

* **Instellen als standaard**

   Trek naar beneden om een van de geselecteerde sorteeropties te selecteren die als standaard moeten worden weergegeven. De standaardwaarde is `Newest`.

* **Tijdopties selecteren voor het sorteren van analysemogelijkheden**

   Trek naar beneden om een van `All, Last 24 Hours, Last 7 Days, Last 30 Days` te selecteren. De standaardwaarde is `All`.

## Ervaring {#site-visitor-experience} voor bezoekers van site

### Ideaal maken {#creating-idea}

Net als bij alle andere communautaire kenmerken kan een bezoeker van de site alleen ideeën lezen en andere meningen bekijken (door opmerkingen en stemmen/houden) als hij niet is aangemeld.

Na aanmelding kan een lid een nieuw idee maken.

![creatief-nieuw-idee](assets/create-new-idea.png)

Voordat het idee wordt verzonden, kan het lid een concept opslaan.

Als u de knop `Save as Draft` selecteert, wordt een concept opgeslagen.

![sparen-idee](assets/save-idea.png)

Als u opgeslagen concepten weergeeft op het tabblad `My Drafts`, selecteert u `Read More` om de bewerkingsmodus opnieuw in te schakelen:

![bewerken-idee](assets/edit-idea.png)

#### Feedback geven {#providing-feedback}

Als het idee eenmaal is gepubliceerd, kunnen andere leden zich aanmelden, het idee openen ( `Read More`) en het idee zo weergeven, waardoor het aantal stemmen wordt vergroot en opmerkingen worden gemaakt.

![feedback](assets/feedback-idea.png)

### Aanvullende informatie {#additional-information}

Meer informatie vindt u op de pagina [Essentiële elementen voor ideeën](/help/communities/ideation.md) voor ontwikkelaars.

Zie [Door gebruiker gegenereerde inhoud modereren](/help/communities/moderate-ugc.md) voor de moderatie van geposte onderwerpen en opmerkingen.

Zie [Door gebruiker gegenereerde inhoud labelen](/help/communities/tag-ugc.md) voor het labelen van geposte onderwerpen en opmerkingen.
