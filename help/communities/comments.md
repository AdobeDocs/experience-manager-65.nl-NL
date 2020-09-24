---
title: Opmerkingen gebruiken
seo-title: Opmerkingen gebruiken
description: Met de functie Opmerkingen kunnen aangemelde bezoekers hun mening en kennis delen
seo-description: Met de functie Opmerkingen kunnen aangemelde bezoekers hun mening en kennis delen
uuid: 40acd962-846c-483c-b789-aab3a7d2b31b
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 216cfb3e-777e-4773-afba-749debdca000
docset: aem65
translation-type: tm+mt
source-git-commit: 6be0aa7c3f6b21ad26221289a6cca2b4615ed3f4
workflow-type: tm+mt
source-wordcount: '994'
ht-degree: 0%

---


# Opmerkingen gebruiken {#using-comments}

## Inleiding {#introduction}

De functie voor opmerkingen wordt gebruikt om bezoekers die zich hebben aangemeld (leden) in staat te stellen hun mening en kennis over de inhoud van de site te delen. Deze functie is vaak al aanwezig in andere functies, maar kan aan elke website worden toegevoegd.

In het document wordt beschreven:

* Toevoegen `Comments` aan een pagina.
* De montages van de configuratie voor de `Comments` component.

>[!NOTE]
>
>Anonieme berichten over opmerkingen worden niet ondersteund. Site-bezoekers moeten zich registreren (lid worden) en zich aanmelden om deel te nemen.


### Opmerkingen toevoegen aan een pagina {#adding-comments-to-a-page}

Als u een `Comments` component aan een pagina wilt toevoegen in de ontwerpmodus, gebruikt u de componentbrowser om te zoeken naar

* `Communities / Comments`

en sleep het naar de juiste positie op een pagina, zoals een positie ten opzichte van de functie waar gebruikers opmerkingen over kunnen plaatsen, of gewoon onder aan de pagina.

Ga voor de benodigde informatie naar [Community Components Basics](/help/communities/basics.md).

Wanneer de [vereiste clientbibliotheken](/help/communities/essentials-comments.md#essentials-for-client-side) worden opgenomen, wordt de `Comments` component op deze manier weergegeven.

![comments-component](assets/comments-component.png)

>[!NOTE]
>
>Er mag slechts één `Comments` component op een pagina voorkomen. Houd er rekening mee dat diverse functies van een Gemeenschappen al opmerkingen bevatten, zoals een blog, agenda, forum, QnA en revisies.


### Opmerkingen configureren {#configuring-comments}

Selecteer de geplaatste `Comments` component die u wilt openen en selecteer het `Configure` pictogram waarmee het dialoogvenster Bewerken wordt geopend.

![Configuratiepictogram](assets/configure.png)

![commentaarinstellingen](assets/commentssettings.png)

#### Tabblad Opmerkingen {#comments-tab}

Geef op onder het tabblad **Opmerkingen** op hoe bezoekers opmerkingen invoeren.

* **Antwoorden toestaan**

   Als deze optie is ingeschakeld, kunnen leden reageren op bestaande opmerkingen. Standaard is uitgeschakeld.

* **Opmerkingen per pagina**

   Hiermee beperkt u het aantal opmerkingen dat per pagina wordt weergegeven en het aantal reacties dat wordt weergegeven. De standaardwaarde is 10.

* **Uploaden van bestanden toestaan**

   Als deze optie is ingeschakeld, wordt de optie voor het uploaden van een bestand weergegeven in het tekstinvoervak. Standaard is uitgeschakeld.

* **Max. bestandsgrootte**

   Alleen relevant als Uploaden van bestand toestaan is ingeschakeld. Deze waarde beperkt de grootte van het geüploade bestand. Standaardlimiet is 10 MB.

* **Max. berichtlengte**

   Maximumaantal tekens dat in het tekstvak kan worden ingevoerd. De standaardwaarde is 4096 tekens.

* **Toegestane bestandstypen**

   Alleen relevant als Uploaden van bestand toestaan is ingeschakeld. Een door komma&#39;s gescheiden lijst met bestandsextensies met het puntscheidingsteken. Bijvoorbeeld: .jpg, .jpeg, .png, .doc, .docx, .pdf. Als er bestandstypen zijn opgegeven, zijn deze niet toegestaan. De standaardinstelling is niet opgegeven, zodat alle bestandstypen zijn toegestaan.

* **RTF-editor**

   Als deze optie is ingeschakeld, worden opmerkingen ingevoerd met een markering. Standaard is uitgeschakeld.

* **Stemmen toestaan**

   Als deze optie is ingeschakeld, wordt de optie om omhoog of omlaag te stemmen weergegeven met het tekstinvoervak. Standaard is uitgeschakeld.

* **Volgen toestaan**

   Als deze optie is ingeschakeld, kunnen leden opmerkingen volgen. Standaard is uitgeschakeld.

* **Badges weergeven**

   Als deze optie is ingeschakeld, kunnen verdiende en toegekende badges worden weergegeven. Standaard is uitgeschakeld.

#### Tabblad Gebruikersmodernisering {#user-moderation-tab}

Geef op onder het tabblad **Gebruikersmodernisering** op hoe de geposte opmerkingen worden beheerd. Voor meer informatie, zie het [Modereren van Gebruiker Gegenereerde Inhoud](/help/communities/moderate-ugc.md).

* **Pre-moderatie**

   Als deze optie is ingeschakeld, moeten opmerkingen worden goedgekeurd voordat ze op een publicatiesite worden weergegeven. Standaard is uitgeschakeld.

* **Opmerkingen verwijderen**

   Als deze optie is ingeschakeld, kan het lid dat de opmerking heeft geplaatst deze verwijderen. Standaard is uitgeschakeld.

* **Opmerkingen weigeren**

   Indien gecontroleerd, sta moderators toe om commentaren te ontkennen. Standaard is uitgeschakeld.

* **Opmerkingen sluiten/opnieuw openen**

   Als deze optie ingeschakeld is, kan de moderator opmerkingen sluiten en opnieuw openen. Standaard is uitgeschakeld.

* **Opmerkingen markeren**

   Als deze optie is ingeschakeld, kunnen leden opmerkingen als onjuist markeren. Standaard is uitgeschakeld.

* **Lijst met redenen voor vlag**

   Als deze optie is ingeschakeld, kunnen leden in een vervolgkeuzelijst de reden kiezen waarom een opmerking als onjuist wordt gemarkeerd. Standaard is uitgeschakeld.

* **Reden voor aangepaste vlag**

   Als deze optie is ingeschakeld, kunnen leden hun eigen reden opgeven om een opmerking als ongeschikt te markeren. Standaard is uitgeschakeld.

* **Moderniseringsdrempel**

   Voer het aantal keren in dat een opmerking moet worden gemarkeerd door de leden voordat de moderatoren op de hoogte worden gesteld. De standaardwaarde is één keer (1).

* **Limiet voor markering**

   Voer het aantal keren in dat een opmerking moet worden gemarkeerd voordat deze wordt verborgen in de openbare weergave. Dit getal moet groter zijn dan of gelijk zijn aan de **moderatiedrempel**. De standaardwaarde is 5.

#### Tabblad Instellingen sorteren {#sort-settings-tab}

Geef op onder het tabblad **Sorteerinstellingen** op hoe de geposte opmerkingen worden gesorteerd wanneer ze worden weergegeven.

* **Veld sorteren**

   Trek omlaag om een van `Newest, Oldest, Last Updated, Most Viewed, Most Active, Most Followed`, of `Most Liked`te selecteren.

* **Sorteervolgorde**

   Trek omlaag om een van `Ascending` of `Descending`te selecteren.

### Wijzigen in type aangepaste opmerking {#changing-to-a-custom-comment-type}

Door het Type van Middel van de Commentaar te veranderen, produceert het commentaarsysteem niet meer een geval van een commentaar gebruikend het gebrek, maar eerder die is aangepast (uitgebreid) door ontwikkelaars.

Zodra de types van douanemiddelen gekend zijn, ga de Wijze [van het](/help/sites-authoring/default-components-designmode.md) Ontwerp in en klik de geplaatste `Comments` component tweemaal om een dialoog met een extra lusje te openen.

Onder het lusje van de Types **van Middel, specificeer douane resourceType voor nieuwe instanties van de** `Comments or Voting` componenten:

![hulpbrontype](assets/resource-type.png)

* **Type bron van opmerking**

   Navigeer naar het resourceType van een uitgebreide `comment` component (enige commentaar) in /apps. Bijvoorbeeld, `/apps/social/commons/components/hbs/comments/comment`

   Deze bron identificeert het resourceType van UGC die wordt gecreeerd wanneer een bezoeker een commentaar plaatst.

* **Type stembron**

   Navigeer naar het resourceType van een uitgebreide `voting` component in /apps. Bijvoorbeeld, `/apps/social/components/hbs/voting`

   Dit middel identificeert het middeltype van UGC die wordt gecreeerd wanneer een bezoeker een stem plaatst.

* **Brontype voor opmerkingensysteem**

   Navigeer aan resourceType van een uitgebreide `comments`component (het Systeem van de Commentaar) in /apps. Leeg laten tenzij het paginasjabloon het opmerkingensysteem [dynamisch in het onderliggende script bevat](/help/communities/scf.md#add-or-include-a-communities-component) in plaats van als bron (knooppunt comments) aan de pagina te worden toegevoegd. Lees meer over de [{include} helper](/help/communities/handlebars-helpers.md#include).

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

### Additional Information {#additional-information}

Meer informatie vindt u op de pagina [Comments Essentials](/help/communities/essentials-comments.md) voor ontwikkelaars.

Zie Door gebruiker gegenereerde inhoud [modereren voor moderatie van geposte opmerkingen](/help/communities/moderate-ugc.md).

Zie Door gebruiker gegenereerde inhoud [vertalen voor een vertaling van geposte opmerkingen](/help/communities/translate-ugc.md).
