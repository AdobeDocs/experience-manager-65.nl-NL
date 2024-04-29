---
title: Opmerkingen gebruiken
description: Met de functie Opmerkingen kunnen aangemelde bezoekers hun mening en kennis delen
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
docset: aem65
exl-id: 30baebd9-13c5-4fde-a494-85601abc32a5
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '983'
ht-degree: 0%

---

# Opmerkingen gebruiken {#using-comments}

## Inleiding {#introduction}

De functie voor opmerkingen wordt gebruikt om bezoekers die zich hebben aangemeld (leden) in staat te stellen hun mening en kennis over de inhoud van de site te delen. Deze functie is vaak al aanwezig in andere functies, maar kan aan elke website worden toegevoegd.

In het document wordt beschreven:

* Toevoegen `Comments` naar een pagina.
* De montages van de configuratie voor de `Comments` component.

>[!NOTE]
>
>Anoniem plaatsen van een opmerking wordt niet ondersteund. Site-bezoekers moeten zich registreren (lid worden) en zich aanmelden om deel te nemen.

### Opmerkingen toevoegen aan een pagina {#adding-comments-to-a-page}

Als u een `Comments` van een component aan een pagina op auteurswijze, gebruik componentenbrowser om van

* `Communities / Comments`

en sleep het naar de juiste positie op een pagina, zoals een positie ten opzichte van de functie waar gebruikers opmerkingen over kunnen plaatsen, of gewoon onder aan de pagina.

Voor de nodige informatie gaat u naar [Grondbeginselen van Community-componenten](/help/communities/basics.md).

Wanneer de [vereiste clientbibliotheken](/help/communities/essentials-comments.md#essentials-for-client-side) worden opgenomen, is dit hoe `Comments` wordt weergegeven.

![comments-component](assets/comments-component.png)

>[!NOTE]
>
>Slechts één `Comments` kan op een pagina voorkomen. Houd er rekening mee dat diverse functies van een Gemeenschappen al opmerkingen bevatten, zoals een blog, agenda, forum, QnA en revisies.

### Opmerkingen configureren {#configuring-comments}

Selecteer de geplaatste `Comments` te openen en te selecteren `Configure` wordt het dialoogvenster Bewerken geopend.

![Configuratiepictogram](assets/configure.png)

![commentaarinstellingen](assets/commentssettings.png)

#### Tabblad Opmerkingen {#comments-tab}

Onder de **Opmerkingen** , geeft u op hoe bezoekers opmerkingen invoeren.

* **Antwoorden toestaan**

  Als deze optie is ingeschakeld, kunnen leden reageren op bestaande opmerkingen. De optie Standaard is uitgeschakeld.

* **Opmerkingen per pagina**

  Hiermee beperkt u het aantal opmerkingen dat per pagina wordt weergegeven en het aantal reacties dat wordt weergegeven. De standaardwaarde is 10.

* **Uploaden van bestanden toestaan**

  Als deze optie is ingeschakeld, wordt de optie voor het uploaden van een bestand weergegeven in het tekstinvoervak. De optie Standaard is uitgeschakeld.

* **Max. bestandsgrootte**

  Alleen relevant als Uploaden van bestand toestaan is ingeschakeld. Deze waarde beperkt de grootte van het geüploade bestand. Standaardlimiet is 10 MB.

* **Max. berichtlengte**

  Maximumaantal tekens dat in het tekstvak kan worden ingevoerd. De standaardwaarde is 4096 tekens.

* **Toegestane bestandstypen**

  Alleen relevant als Uploaden van bestand toestaan is ingeschakeld. Een door komma&#39;s gescheiden lijst met bestandsextensies met het puntscheidingsteken. Bijvoorbeeld: .jpg, .jpeg, .png, .doc, .docx, .pdf. Als er bestandstypen zijn opgegeven, zijn deze niet toegestaan. De standaardinstelling is niet opgegeven, zodat alle bestandstypen zijn toegestaan.

* **RTF-editor**

  Als deze optie is ingeschakeld, worden opmerkingen ingevoerd met een markering. De optie Standaard is uitgeschakeld.

* **Stemmen toestaan**

  Als deze optie is ingeschakeld, wordt de optie om omhoog of omlaag te stemmen weergegeven met het tekstinvoervak. De optie Standaard is uitgeschakeld.

* **Volgen toestaan**

  Als deze optie is ingeschakeld, kunnen leden opmerkingen volgen. De optie Standaard is uitgeschakeld.

* **Badges weergeven**

  Als deze optie is ingeschakeld, kunnen verdiende en toegekende badges worden weergegeven. De optie Standaard is uitgeschakeld.

#### Tabblad Gebruikersmodernisering {#user-moderation-tab}

Onder de **Moderatie gebruiker** , geeft u op hoe de geposte opmerkingen worden beheerd. Zie voor meer informatie [Door gebruiker gegenereerde inhoud modereren](/help/communities/moderate-ugc.md).

* **Pre-moderatie**

  Als deze optie is ingeschakeld, moeten opmerkingen worden goedgekeurd voordat ze op een publicatiesite worden weergegeven. De optie Standaard is uitgeschakeld.

* **Opmerkingen verwijderen**

  Als deze optie is ingeschakeld, kan het lid dat de opmerking heeft geplaatst deze verwijderen. De optie Standaard is uitgeschakeld.

* **Opmerkingen weigeren**

  Indien gecontroleerd, sta moderators toe om commentaren te ontkennen. De optie Standaard is uitgeschakeld.

* **Opmerkingen sluiten/opnieuw openen**

  Als deze optie ingeschakeld is, kan de moderator opmerkingen sluiten en opnieuw openen. De optie Standaard is uitgeschakeld.

* **Opmerkingen markeren**

  Als deze optie is ingeschakeld, kunnen leden opmerkingen als onjuist markeren. De optie Standaard is uitgeschakeld.

* **Lijst met redenen voor vlag**

  Als deze optie is ingeschakeld, kunnen leden in een vervolgkeuzelijst de reden kiezen waarom een opmerking als onjuist wordt gemarkeerd. De optie Standaard is uitgeschakeld.

* **Reden voor aangepaste vlag**

  Als deze optie is ingeschakeld, kunnen leden hun eigen reden opgeven om een opmerking als ongeschikt te markeren. De optie Standaard is uitgeschakeld.

* **Moderniseringsdrempel**

  Voer het aantal keren in dat een opmerking moet worden gemarkeerd door de leden voordat de moderatoren op de hoogte worden gesteld. De standaardwaarde is één keer (1).

* **Limiet voor markering**

  Voer het aantal keren in dat een opmerking moet worden gemarkeerd voordat deze wordt verborgen in de openbare weergave. Dit getal moet groter zijn dan of gelijk zijn aan het **Moderniseringsdrempel**. De standaardwaarde is 5.

#### Tabblad Instellingen sorteren {#sort-settings-tab}

Onder de **Instellingen sorteren** , geeft u op hoe de geposte opmerkingen worden gesorteerd wanneer deze worden weergegeven.

* **Veld sorteren**

  Omlaag trekken om een van de `Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed`, of `Most Liked`.

* **Sorteervolgorde**

  Omlaag trekken om een van de `Ascending` of `Descending`.

### Wijzigen in type aangepaste opmerking {#changing-to-a-custom-comment-type}

Door het Type van Middel van de Commentaar te veranderen, produceert het commentaarsysteem niet meer een geval van een commentaar gebruikend het gebrek, maar eerder die is aangepast (uitgebreid) door ontwikkelaars.

Zodra de types van douanemiddel gekend zijn, ga binnen [Ontwerpmodus](/help/sites-authoring/default-components-designmode.md) en dubbelklikt u op de geplaatste `Comments` om een dialoogvenster met een extra tabblad te openen.

Onder de **Brontypen** tab, specificeer het custom resourceType voor nieuwe instanties van `Comments or Voting` componenten:

![hulpbrontype](assets/resource-type.png)

* **Type bron van opmerking**

  Navigeer naar het resourceType van uitgebreid `comment` component (enkele opmerking) in /apps. Bijvoorbeeld: `/apps/social/commons/components/hbs/comments/comment`

  Deze bron identificeert het resourceType van UGC die wordt gecreeerd wanneer een bezoeker een commentaar plaatst.

* **Type stembron**

  Navigeer naar het resourceType van uitgebreid `voting` in /apps. Bijvoorbeeld: `/apps/social/components/hbs/voting`

  Dit middel identificeert het middeltype van UGC die wordt gecreeerd wanneer een bezoeker een stem plaatst.

* **Brontype voor opmerkingensysteem**

  Navigeer naar het resourceType van uitgebreid `comments`component (Opmerkingssysteem) in /apps. Leeg laten, tenzij de paginasjabloon [dynamisch omvat](/help/communities/scf.md#add-or-include-a-communities-component) het Systeem van de Commentaar in het onderliggende manuscript in plaats van wordt toegevoegd aan de pagina als middel (commentaarknoop). Lees meer over de [`{{include}}` helper](/help/communities/handlebars-helpers.md#include).

### Ervaring met sitebezoekers {#site-visitor-experience}

#### Moderatoren en beheerders {#moderators-and-administrators}

Wanneer de ondertekende binnen gebruiker moderator of beheerdervoorrechten heeft, kunnen zij de matigingstaken uitvoeren die door de configuratie van de component worden toegelaten, ongeacht wie de commentaar authored.

#### Leden {#members}

Wanneer de bezoeker van de site zich heeft aangemeld, kunnen deze, afhankelijk van de configuratie

* Een nieuwe opmerking plaatsen
* Een eigen opmerking bewerken
* Een eigen opmerking verwijderen
* Opmerkingen van anderen markeren

#### Anoniem {#anonymous}

Sitebezoekers die niet zijn aangemeld, kunnen alleen geposte opmerkingen lezen, deze vertalen indien deze worden ondersteund, maar kunnen geen opmerking toevoegen of opmerkingen van anderen markeren.

### Aanvullende informatie {#additional-information}

Meer informatie is te vinden op de [Essentiële opmerkingen](/help/communities/essentials-comments.md) pagina voor ontwikkelaars.

Zie voor een moderatie van gepubliceerde opmerkingen [Door gebruiker gegenereerde inhoud modereren](/help/communities/moderate-ugc.md).

Zie voor een vertaling van geposte opmerkingen [Door de gebruiker gegenereerde inhoud vertalen](/help/communities/translate-ugc.md).
