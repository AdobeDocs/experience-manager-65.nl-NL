---
title: Overzicht van revisies en revisies gebruiken (weergave)
seo-title: Overzicht van revisies en revisies gebruiken (weergave)
description: De componenten Revisies en Revisies Summary toevoegen aan een pagina
seo-description: De componenten Revisies en Revisies Summary toevoegen aan een pagina
uuid: bd1ccee7-b26b-4a27-b1ea-89609f5080af
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: bf4e7809-8def-4647-aaa6-3ac36865511f
translation-type: tm+mt
source-git-commit: 62f2a11491e427a13cecae75c225ed41a44783cd

---


# Overzicht van revisies en revisies gebruiken (weergave) {#using-reviews-and-reviews-summary-display}

De `Reviews` component is een samenstelling van [Commentaren](comments.md) en [Beoordelingscomponenten](rating.md) klaar voor gebruik.

De `Reviews Summary (Display)` component geeft een overzicht van een actieve of gesloten instantie van een `Reviews` component voor weergave elders op de site.

>[!NOTE]
>
>Anonieme publicatie van een revisie wordt niet ondersteund. Site-bezoekers moeten zich registreren (lid worden) en zich aanmelden om deel te nemen. De ondertekende bezoeker kan zijn of haar revisie op elk gewenst moment bijwerken.


## Een revisie toevoegen aan een pagina {#adding-a-review-to-a-page}

Als u een `Reviews` component aan een pagina wilt toevoegen in de ontwerpmodus, gebruikt u de componentbrowser om de component te zoeken `Communities / Reviews` en naar de juiste positie op een pagina te slepen, zoals een positie ten opzichte van de functie die gebruikers kunnen controleren.

Ga voor de benodigde informatie naar [Community Components Basics](basics.md).

Wanneer de [vereiste client-side bibliotheken](reviews-basics.md#essentials-for-client-side) worden opgenomen, wordt de `Reviews`component op deze manier weergegeven.

![chlimage_1-340](assets/chlimage_1-340.png)

## Revisies configureren {#configuring-reviews}

Selecteer de geplaatste `Reviews` component die u wilt openen en selecteer het `Configure` pictogram waarmee het dialoogvenster Bewerken wordt geopend.

![chlimage_1-341](assets/chlimage_1-341.png)

Geef onder het tabblad **[!UICONTROL Toegestane beoordelingen]** de volledige lijst met classificaties op die aan de leden moet worden weergegeven. De eerste rating moet een algemene/algemene rating zijn, aangezien de rating de gemiddelde rating voor de `Review Summary (Display)` component vormt. De volgende twee classificaties in de standaardconfiguratie moeten een andere titel krijgen dan &quot;Subrating 1&quot; of &quot;Subrating 2&quot;.

![chlimage_1-342](assets/chlimage_1-342.png)

* **[!UICONTROL Toegestane waarderingen]**

   Een lijst met waarderingen waaruit een lid kan kiezen.

   Gebruik de toetsen Pijl-omhoog, Pijl-omlaag en Pijl-verwijderen om de zichtbare selecties te wijzigen.

   Klik op Item **** toevoegen om een andere beoordelingskeuze toe te voegen.

Voer onder het tabblad **[!UICONTROL Vereiste beoordelingen]** opnieuw items in uit de lijst **[!UICONTROL Toegestane beoordelingen]** die moeten worden beoordeeld. Als een item alleen wordt opgegeven op het tabblad Toegestane waarderingen, kan het item niet worden gemarkeerd wanneer het door het lid wordt verzonden.

Op de website worden vereiste classificaties gemarkeerd met een sterretje. Als een item vereist is en niet is gemarkeerd, wordt een bericht weergegeven aan het lid en wordt de verzending geweigerd totdat alle vereiste beoordelingen zijn gemarkeerd.

![chlimage_1-343](assets/chlimage_1-343.png)

* **[!UICONTROL Vereiste beoordelingen]**

   Een subset van toegestane ratings die aangeeft welke ratings vereist zijn.

   Gebruik de toetsen Pijl-omhoog, Pijl-omlaag en Pijl-verwijderen om de zichtbare selecties te wijzigen.

   Klik op Item **** toevoegen om een andere antwoordkeuze toe te voegen.

>[!NOTE]
>
>Als een item wordt ingevoerd op het tabblad **[!UICONTROL Vereiste waarderingen]** dat niet is opgegeven op het tabblad **[!UICONTROL Toegestane waarderingen]** , wordt het item niet opgenomen in de te beoordelen items.


Geef op onder het tabblad **[!UICONTROL Revisies]** op hoe revisies worden verwerkt.

![chlimage_1-340](assets/chlimage_1-344.png)

* **[!UICONTROL Reacties toestaan]**

   Als deze optie is ingeschakeld, kunt u reacties op revisies toestaan. De optie Standaard is uitgeschakeld.

* **[!UICONTROL Gesloten]**

   Als deze optie is ingeschakeld, wordt de revisie afgesloten voor nieuwe revisies en antwoorden. De optie Standaard is uitgeschakeld.

* **[!UICONTROL Uploaden van bestanden toestaan]**

   Als deze optie is ingeschakeld, mogen bestandsbijlagen worden geüpload voor de revisie. De optie Standaard is uitgeschakeld.

* **Max. bestandsgrootte **

   Alleen relevant als **[!UICONTROL Uploaden]** van bestand toestaan is ingeschakeld. Dit veld beperkt de grootte (in bytes) van een geüpload bestand. De standaardwaarde is 10 MB.

* **[!UICONTROL Max. berichtlengte]**

   Maximumaantal tekens dat in het tekstvak kan worden ingevoerd. De standaardwaarde is 4096 tekens.

* **[!UICONTROL Toegestane bestandstypen]**

   Alleen relevant als **[!UICONTROL Uploaden]** van bestand toestaan is ingeschakeld. Een door komma&#39;s gescheiden lijst met bestandsextensies met het &quot;punt&quot;-scheidingsteken. Bijvoorbeeld: .jpg, .jpeg, .png, .doc, .docx, .pdf. Als er bestandstypen worden opgegeven, zijn deze niet toegestaan. De standaardinstelling is niet opgegeven, zodat alle bestandstypen zijn toegestaan.

* **[!UICONTROL RTF-editor]**

   Als deze optie ingeschakeld is, kunnen er berichten met markeringen worden ingevoerd. De optie Standaard is uitgeschakeld.

* **[!UICONTROL Stemmen toestaan]**

   Indien ingeschakeld, neemt u de functie Stemmen op voor een onderwerp. De optie Standaard is uitgeschakeld.

Geef op onder het tabblad **[!UICONTROL Gebruikersmodernisering]** op hoe de geposte revisies worden beheerd. Voor meer informatie, zie het [Modereren van Gebruiker Gegenereerde Inhoud](moderate-ugc.md).

![chlimage_1-345](assets/chlimage_1-345.png)

* **[!UICONTROL Pre-moderatie]**

   Als deze optie is ingeschakeld, moeten revisies worden goedgekeurd voordat ze op een publicatiesite worden weergegeven. De optie Standaard is uitgeschakeld.

* **[!UICONTROL Revisies verwijderen]**

   Als deze optie is ingeschakeld, kan het lid dat de revisie heeft geplaatst deze verwijderen. De optie Standaard is uitgeschakeld.

* **[!UICONTROL Revisies weigeren]**

   Als gecontroleerd, sta moderators toe om overzichten te ontkennen. De optie Standaard is uitgeschakeld.

* **[!UICONTROL Revisies sluiten/opnieuw openen]**

   Als deze optie ingeschakeld is, kan de moderator de revisies sluiten en opnieuw openen. De optie Standaard is uitgeschakeld.

* **[!UICONTROL Revisies markeren]**

   Als deze optie is ingeschakeld, kunnen leden beoordelingen als onjuist markeren. De optie Standaard is uitgeschakeld.

* **[!UICONTROL Lijst met redenen voor vlag]**

   Als deze optie is ingeschakeld, kunnen leden in een vervolgkeuzelijst de reden kiezen waarom een revisie als onjuist is gemarkeerd. De optie Standaard is uitgeschakeld.

* **[!UICONTROL Reden voor aangepaste vlag]**

   Als deze optie is ingeschakeld, kunnen leden hun eigen reden opgeven om een revisie als ongeschikt te bestempelen. De optie Standaard is uitgeschakeld.

* **[!UICONTROL Moderniseringsdrempel]**

   Voer het aantal keren in dat een revisie door leden moet worden gemarkeerd voordat moderatoren op de hoogte worden gesteld. De standaardwaarde is één keer (1).

* **[!UICONTROL Limiet voor markering]**

   Voer het aantal keren in dat een revisie moet worden gemarkeerd voordat deze wordt verborgen in de openbare weergave. Dit getal moet groter zijn dan of gelijk zijn aan de **[!UICONTROL moderatiedrempel]**. De standaardwaarde is 5.

### Een revisieoverzicht (weergave) toevoegen aan een pagina {#adding-a-review-summary-display-to-a-page}

Als u een `Reviews Summary (Display)` component aan een pagina wilt toevoegen in de ontwerpmodus, zoekt u de component

* `Communities / Reviews Summary (Display)`

en sleep de revisie naar de juiste plaats op een pagina waarop een overzicht van een actieve of gesloten revisie moet worden weergegeven.

Ga voor de benodigde informatie naar [Community Components Basics](basics.md).

Wanneer de [vereiste client-side bibliotheken](reviews-basics.md#essentials-for-client-side) worden opgenomen, wordt de `Reviews Summary (Display)`component op deze manier weergegeven.

![chlimage_1-346](assets/chlimage_1-346.png)

>[!NOTE]
>
>Het &quot;gemiddelde&quot; stemt overeen met de stemmen voor het eerste item op de tabbladen Toegestane ratings van de te beoordelen evaluatie.


### Overzicht van revisies configureren (weergave) {#configuring-reviews-summary-display}

Selecteer de geplaatste `Reviews Summary (Display)` component die u wilt openen en selecteer het `Configure` pictogram waarmee het dialoogvenster Bewerken wordt geopend.

![chlimage_1-347](assets/chlimage_1-347.png)

Onder het tabblad Overzicht **** revisie

![chlimage_1-348](assets/chlimage_1-348.png)

* `Review Path`

   ga of doorblader aan de geplaatste instantie van de `reviews`component in om samen te vatten, bijvoorbeeld, als toegevoegd aan de Web-pagina van de plaats van de [Ingenieur Geometrixx,](getting-started.md) de weg zou zijn:

   `/content/sites/engage/en/page/jcr:content/content/primary/reviews`

* `Include histogram`

   Als deze optie is ingeschakeld, neemt u de weergave op van een staafgrafiek die aangeeft hoeveel van elke sterwaardering de overzichten bevatten. De optie Standaard is uitgeschakeld.

### Wijzigen in Type aangepaste revisie {#changing-to-a-custom-review-type}

De component Reviews gebruikt het opmerkingensysteem.

Door het Type van Middel van Commentaar te veranderen, zal het commentaarsysteem niet meer een geval van een commentaar gebruikend het gebrek, maar eerder een produceren die (uitgebreid) door ontwikkelaars is aangepast.

Zodra de types van douanemiddel bekend zijn, ga de Wijze [van het](../../help/sites-authoring/default-components-designmode.md) Ontwerp in en klik op de geplaatste `Comments` component tweemaal om een dialoog met een extra lusje te openen.

Onder het lusje van de Types **[!UICONTROL van Middel, specificeer douane resourceType voor nieuwe instanties van de]** `Comments or Voting`componenten:

![chlimage_1-349](assets/chlimage_1-349.png)

* **[!UICONTROL Type bron van opmerking]**

   Navigeer naar het resourceType van een uitgebreide `comment`component (enige commentaar) in /apps. Bijvoorbeeld, `/apps/social/commons/components/hbs/comments/comment`.

   Deze bron identificeert het resourceType van de UGC die is gemaakt wanneer een bezoeker een opmerking plaatst.

* **[!UICONTROL Type stembron]**

   Navigeer aan resourceType van een uitgebreide `voting`component in /apps. Bijvoorbeeld, `/apps/social/components/hbs/voting`.

   Met deze bron wordt het bronnentype van de UGC geïdentificeerd die wordt gemaakt wanneer een bezoeker een stem plaatst.

* **[!UICONTROL Brontype voor opmerkingensysteem]**

   Navigeer aan resourceType van een uitgebreide `comments`component (het Systeem van de Commentaar) in /apps. Leeg laten tenzij het paginasjabloon het opmerkingensysteem [dynamisch in het onderliggende script bevat](scf.md#add-or-include-a-communities-component) in plaats van als bron (knooppunt comments) aan de pagina te worden toegevoegd. Lees meer over de [{include} helper](handlebars-helpers.md#include).

## Ervaring met sitebezoekers {#site-visitor-experience}

### Moderatoren en beheerders {#moderators-and-administrators}

Wanneer de ondertekende binnen gebruiker moderator of beheerdervoorrechten heeft, kunnen zij de matigingstaken uitvoeren die door de configuratie van de component worden toegelaten, ongeacht wie de controle authored.

### Leden {#members}

Wanneer de bezoeker van de site zich heeft aangemeld, kunnen deze, afhankelijk van de configuratie

* Publiceer een nieuwe revisie.
* Bewerk hun eigen revisie.
* Verwijder hun eigen revisie.
* Geef revisieopmerkingen van anderen een markering.

Er is slechts één score per lid toegestaan. Het lid kan zijn rating te allen tijde wijzigen.

### Anoniem {#anonymous}

Sitebezoekers die niet zijn aangemeld, kunnen alleen geposte revisies lezen, deze vertalen indien deze worden ondersteund, maar mogen geen score of revisie toevoegen en de revisieopmerkingen van anderen niet markeren.

## Additional Information {#additional-information}

Meer informatie vindt u op de pagina Essentiële elementen [voor](reviews-basics.md) revisie voor ontwikkelaars.

Zie Door gebruiker gegenereerde inhoud [modereren voor moderatie van geposte opmerkingen](moderate-ugc.md).

Zie Door gebruiker gegenereerde inhoud [vertalen voor een vertaling van geposte opmerkingen](translate-ugc.md).
