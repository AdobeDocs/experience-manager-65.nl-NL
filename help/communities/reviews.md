---
title: Overzicht van revisies en revisies gebruiken (weergave)
description: Leer hoe u de componenten Revisies en Revisies Summary aan een pagina toevoegt.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
exl-id: 170414a6-c40b-4ad2-9294-7c2266850c3d
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '1210'
ht-degree: 0%

---

# Overzicht van revisies en revisies gebruiken (weergave) {#using-reviews-and-reviews-summary-display}

De `Reviews` component is een samenstelling van [ Commentaren ](comments.md) en [ de componenten van de Classificatie ](rating.md) klaar voor gebruik.

De component `Reviews Summary (Display)` geeft een overzicht van een actieve of gesloten instantie van een component `Reviews` voor weergave elders op de site.

>[!NOTE]
>
>Anonieme terbeschikkingstelling van een revisie wordt niet ondersteund. Site-bezoekers moeten zich registreren (lid worden) en zich aanmelden om deel te nemen. De aangemelde bezoeker kan zijn of haar revisie op elk gewenst moment bijwerken.

## Een revisie toevoegen aan een pagina {#adding-a-review-to-a-page}

Als u een `Reviews` -component in de ontwerpmodus aan een pagina wilt toevoegen, gebruikt u de componentbrowser om `Communities / Reviews` te zoeken en sleept u deze naar de juiste positie op een pagina, zoals een positie ten opzichte van de functie die gebruikers kunnen bekijken.

Voor noodzakelijke informatie, bezoek {de Grondbeginselen van de Componenten van 0} Gemeenschappen ](basics.md).[

Wanneer de [ vereiste cliënt-zijbibliotheken ](reviews-basics.md#essentials-for-client-side) inbegrepen zijn, is dit hoe de `Reviews` component verschijnt.

![ creeer-overzicht ](assets/create-review.png)

## Revisies configureren {#configuring-reviews}

Selecteer de geplaatste component `Reviews` , zodat u het pictogram `Configure` kunt openen en selecteren waarmee het dialoogvenster Bewerken wordt geopend.

![ vorm-nieuw ](assets/configure-new.png)

Geef onder het tabblad **[!UICONTROL Allowed Ratings]** de volledige lijst met classificaties op die aan de leden moeten worden weergegeven. De eerste classificatie moet een algemene/algemene classificatie zijn, aangezien het de classificatie is die de gemiddelde classificatie voor de `Review Summary (Display)` component verstrekt. De volgende twee classificaties in de standaardconfiguratie moeten een andere titel krijgen dan &quot;Subrating 1&quot; of &quot;Subrating 2&quot;.

![ toegestaan-classificatie ](assets/configure-review1.png)

* **[!UICONTROL Allowed Ratings]**

  Een lijst met waarderingen waaruit een lid kan kiezen.

  Gebruik de toetsen Pijl-omhoog, Pijl-omlaag en Pijl-verwijderen om de zichtbare selecties te wijzigen.

  Klik op **[!UICONTROL Add Item]** om een andere beoordelingskeuze toe te voegen.

Voer onder het tabblad **[!UICONTROL Required Ratings]** opnieuw items in uit de lijst met **[!UICONTROL Allowed Ratings]** die vereist zijn voor de classificatie. Als een item alleen wordt opgegeven op het tabblad Toegestane waarderingen, kan het item niet worden gemarkeerd wanneer het door het lid wordt verzonden.

Op de website worden vereiste classificaties gemarkeerd met een sterretje. Als een item vereist is en niet is gemarkeerd, wordt een bericht weergegeven aan het lid en wordt de verzending geweigerd totdat alle vereiste beoordelingen zijn gemarkeerd.

![ vereiste-classificatie ](assets/configure-review2.png)

* **[!UICONTROL Required Ratings]**

  Een subset van toegestane ratings die aangeeft welke ratings vereist zijn.

  Gebruik de toetsen Pijl-omhoog, Pijl-omlaag en Pijl-verwijderen om de zichtbare selecties te wijzigen.

  Klik op **[!UICONTROL Add Item]** om een andere reactieoptie toe te voegen.

>[!NOTE]
>
>Als een item wordt ingevoerd op het tabblad **[!UICONTROL Required Ratings]** dat niet is opgegeven op het tabblad **[!UICONTROL Allowed Ratings]** , wordt het item niet opgenomen in de items die moeten worden beoordeeld.

Geef onder het tabblad **[!UICONTROL Reviews]** op hoe revisies worden verwerkt.

![ overzichten ](assets/configure-review3.png)

* **[!UICONTROL Allow Replies]**

  Als deze optie is ingeschakeld, kunt u reacties op revisies toestaan. De optie Standaard is uitgeschakeld.

* **[!UICONTROL Closed]**

  Als deze optie is ingeschakeld, wordt de revisie afgesloten voor nieuwe revisies en antwoorden. De optie Standaard is uitgeschakeld.

* **[!UICONTROL Allow File Uploads]**

  Als deze optie is ingeschakeld, mogen bestandsbijlagen worden geüpload voor de revisie. De optie Standaard is uitgeschakeld.

* **Max de Grootte van het Dossier**

  Alleen relevant als **[!UICONTROL Allow File Uploads]** is gecontroleerd. Dit veld beperkt de grootte (in bytes) van een geüpload bestand. De standaardwaarde is 10 MB.

* **[!UICONTROL Max Message Length]**

  Maximumaantal tekens dat in het tekstvak kan worden ingevoerd. De standaardwaarde is 4096 tekens.

* **[!UICONTROL Allowed File Types]**

  Alleen relevant als **[!UICONTROL Allow File Uploads]** is gecontroleerd. Een door komma&#39;s gescheiden lijst met bestandsextensies met het scheidingsteken &#39;punt&#39;. Bijvoorbeeld .jpg, .jpeg, .png, .doc, .docx, .pdf. Als er bestandstypen zijn opgegeven, zijn deze niet toegestaan. De standaardinstelling is niet opgegeven, zodat alle bestandstypen zijn toegestaan.

* **[!UICONTROL Rich Text Editor]**

  Als deze optie ingeschakeld is, kunnen er berichten met opmaakcodes worden ingevoerd. De optie Standaard is uitgeschakeld.

* **[!UICONTROL Allow Voting]**

  Indien ingeschakeld, neemt u de functie Stemmen op voor een onderwerp. De optie Standaard is uitgeschakeld.

Geef onder het tabblad **[!UICONTROL User Moderation]** op hoe de geposte revisies worden beheerd. Voor meer informatie, zie [ het Matigen van Gebruiker Gegenereerde Inhoud ](moderate-ugc.md).

![ gebruiker-moderatie ](assets/configure-review4.png)

* **[!UICONTROL Pre-Moderation]**

  Als deze optie is ingeschakeld, moeten revisies worden goedgekeurd voordat ze op een publicatiesite worden weergegeven. De optie Standaard is uitgeschakeld.

* **[!UICONTROL Delete Reviews]**

  Als deze optie is ingeschakeld, kan het lid dat de revisie heeft geplaatst deze verwijderen. De optie Standaard is uitgeschakeld.

* **[!UICONTROL Deny Reviews]**

  Als gecontroleerd, sta moderators toe om overzichten te ontkennen. De optie Standaard is uitgeschakeld.

* **[!UICONTROL Close / Reopen Reviews]**

  Als deze optie ingeschakeld is, kan de moderator de revisies sluiten en opnieuw openen. De optie Standaard is uitgeschakeld.

* **[!UICONTROL Flag Reviews]**

  Als deze optie is ingeschakeld, kunnen leden beoordelingen als onjuist markeren. De optie Standaard is uitgeschakeld.

* **[!UICONTROL Flag Reason List]**

  Als deze optie is ingeschakeld, kunnen leden in een vervolgkeuzelijst de reden kiezen waarom een revisie als onjuist is gemarkeerd. De optie Standaard is uitgeschakeld.

* **[!UICONTROL Custom Flag Reason]**

  Als deze optie is ingeschakeld, kunnen leden hun eigen reden opgeven om een revisie als ongeschikt te bestempelen. De optie Standaard is uitgeschakeld.

* **[!UICONTROL Moderation Threshold]**

  Voer het aantal keren in dat een revisie door leden moet worden gemarkeerd voordat moderatoren op de hoogte worden gesteld. De standaardwaarde is één keer (1).

* **[!UICONTROL Flagging Limit]**

  Voer het aantal keren in dat een revisie moet worden gemarkeerd voordat deze wordt verborgen in de openbare weergave. Dit getal moet groter zijn dan of gelijk zijn aan de **[!UICONTROL Moderation Threshold]** . De standaardwaarde is 5.

### Een revisieoverzicht (weergave) toevoegen aan een pagina {#adding-a-review-summary-display-to-a-page}

Als u een component `Reviews Summary (Display)` in de ontwerpmodus aan een pagina wilt toevoegen, zoekt u de component

* `Communities / Reviews Summary (Display)`

En sleep de revisie naar de juiste plaats op een pagina waarop een overzicht van een actieve of gesloten revisie moet worden weergegeven.

Voor noodzakelijke informatie, bezoek {de Grondbeginselen van de Componenten van 0} Gemeenschappen ](basics.md).[

Wanneer de [ vereiste cliënt-zijbibliotheken ](reviews-basics.md#essentials-for-client-side) inbegrepen zijn, is dit hoe de `Reviews Summary (Display)` component verschijnt.

![ overzicht-samenvatting ](assets/configure-review5.png)

>[!NOTE]
>
>Het &quot;gemiddelde&quot; stemt overeen met de stemmen voor het eerste item op de tabbladen Toegestane ratings van de te beoordelen evaluatie.

### Overzicht van revisies configureren (weergave) {#configuring-reviews-summary-display}

Selecteer de geplaatste component `Reviews Summary (Display)` , zodat u het pictogram `Configure` kunt openen en selecteren waarmee het dialoogvenster Bewerken wordt geopend.

![ vormen ](assets/configure-new.png)

Onder de tab **[!UICONTROL Review Summary]**

![ overzicht-samenvatting ](assets/configure-review6.png)

* `Review Path`

  Ga of doorblader aan de geplaatste instantie van de `reviews` component in zodat kunt u, bijvoorbeeld, als toegevoegd aan de Web-pagina van de [ plaats van de Ingenieur van de Geometrixx, ](getting-started.md) de weg zijn:

  `/content/sites/engage/en/page/jcr:content/content/primary/reviews`

* `Include histogram`

  Als deze optie is ingeschakeld, neemt u de weergave op van een staafgrafiek die aangeeft hoeveel sterrenwaarderingen er in de overzichten staan. De optie Standaard is uitgeschakeld.

### Wijzigen in Type aangepaste revisie {#changing-to-a-custom-review-type}

De component Reviews gebruikt het opmerkingensysteem.

Door het Type van Middel van de Commentaar te veranderen, produceert het commentaarsysteem niet meer een geval van een commentaar gebruikend het gebrek, maar eerder die is aangepast (uitgebreid) door ontwikkelaars.

Wanneer de types van douanemiddel gekend zijn, ga [ Wijze van het Ontwerp ](../../help/sites-authoring/default-components-designmode.md) in en klik de geplaatste `Comments` component tweemaal om een dialoog met een extra tabel te openen.

Geef onder het tabblad **[!UICONTROL Resource Types]** het aangepaste resourceType op voor nieuwe instanties van de `Comments or Voting` -componenten:

![ commentaren-stemgerechtigde ](assets/configure-review7.png)

* **[!UICONTROL Comment Resource Type]**

  Navigeer aan resourceType van een uitgebreide `comment` component (enige commentaar) in /apps. Bijvoorbeeld `/apps/social/commons/components/hbs/comments/comment` .

  Deze bron identificeert het resourceType van UGC die wordt gecreeerd wanneer een bezoeker een commentaar plaatst.

* **[!UICONTROL Voting Resource Type]**

  Navigeer aan resourceType van een uitgebreide `voting` component in /apps. Bijvoorbeeld `/apps/social/components/hbs/voting` .

  Dit middel identificeert het middeltype van UGC die wordt gecreeerd wanneer een bezoeker een stem plaatst.

* **[!UICONTROL Comment System Resource Type]**

  Navigeer aan resourceType van een uitgebreide `comments` component (het Systeem van de Commentaar) in /apps. Laat leeg tenzij het paginamalplaatje [ ](scf.md#add-or-include-a-communities-component) dynamisch omvat het Systeem van de Commentaar in het onderliggende manuscript in plaats van wordt toegevoegd aan de pagina als middel (commentaarknoop). Lees meer over de [`{{include}}` helper ](handlebars-helpers.md#include) .

## Ervaring met sitebezoekers {#site-visitor-experience}

### Moderatoren en beheerders {#moderators-and-administrators}

Wanneer de ondertekende binnen gebruiker moderator of beheerdervoorrechten heeft, kunnen zij de matigingstaken uitvoeren die door de configuratie van de component worden toegelaten, ongeacht wie de controle authored.

### Leden {#members}

Wanneer de bezoeker van de site zich aanmeldt, is het mogelijk dat:

* Post: een nieuwe revisie
* Een eigen revisie bewerken
* Een eigen revisie verwijderen
* Opmerkingen van anderen markeren

Er is slechts één score per lid toegestaan. Het lid kan zijn rating te allen tijde wijzigen.

### Anoniem {#anonymous}

Sitebezoekers die niet zijn aangemeld, kunnen alleen geposte revisies lezen, deze vertalen indien deze worden ondersteund, maar mogen geen score of revisie toevoegen en de revisieopmerkingen van anderen niet markeren.

## Aanvullende informatie {#additional-information}

Meer informatie kan op de ](reviews-basics.md) pagina van de Hoofdzaak van het Overzicht [ {voor ontwikkelaars worden gevonden.

Voor moderatie van geposte commentaren, zie [ het Modereren van Gebruiker Gegenereerde Inhoud ](moderate-ugc.md).

Voor vertaling van geposte commentaren, zie [ Vertaal Door de Gebruiker Gegenereerde Inhoud ](translate-ugc.md).
