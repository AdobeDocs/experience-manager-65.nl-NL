---
title: Functie bestandsbibliotheek
seo-title: Functie bestandsbibliotheek
description: Met de functie Bestandsbibliotheek kunnen aangemelde sitebezoekers bestanden uploaden, beheren en downloaden
seo-description: Met de functie Bestandsbibliotheek kunnen aangemelde sitebezoekers bestanden uploaden, beheren en downloaden
uuid: e78a90bd-f1d3-44f8-98eb-1498a55e8217
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: ea2b23af-49c3-409b-a041-43c42d846f21
docset: aem65
translation-type: tm+mt
source-git-commit: 27a054cc5d502d95c664c3b414d0066c6c120b65

---


# Functie bestandsbibliotheek{#file-library-feature}

## Inleiding {#introduction}

De functie voor bestandsbibliotheek biedt een plaats voor ingetekende sitebezoekers (leden van de community) voor het uploaden, beheren en downloaden van bestanden binnen de site van de gebruikersgemeenschap.

In deze sectie van de documentatie wordt beschreven

* toevoegen van de bestandsbibliotheekfunctie aan een AEM-site
* configuratie-instellingen voor de `File Library` component

### Een bestandsbibliotheek toevoegen aan een pagina {#adding-a-file-library-to-a-page}

Als u een `File Library` component aan een pagina wilt toevoegen in de ontwerpmodus, zoekt u de component

* `Communities / File Library`

en sleep het naar de juiste plaats op een pagina.

Ga voor de benodigde informatie naar [Community Components Basics](/help/communities/basics.md).

Wanneer de [vereiste client-side bibliotheken](/help/communities/essentials-file-library.md#essentials-for-client-side) worden opgenomen, ziet u zo de `File Library` component eruit:

![chlimage_1-145](assets/chlimage_1-145.png)

### Bestandsbibliotheek configureren {#configuring-file-library}

Selecteer de geplaatste `File Library` component die u wilt openen en selecteer het `Configure` pictogram waarmee het dialoogvenster Bewerken wordt geopend.

![chlimage_1-146](assets/chlimage_1-146.png) ![forum-config-1](assets/forum-config-1.png)

#### Tabblad Opmerkingen {#comments-tab}

Geef onder het tabblad **Opmerkingen **op of en hoe opmerkingen voor geüploade bestanden worden weergegeven:

* **Opmerkingen over bestanden** toestaan Als deze optie is ingeschakeld, kunt u opmerkingen over geüploade bestanden toestaan. De optie Standaard is uitgeschakeld.

* **Met Opmerkingen per pagina** beperkt u het aantal opmerkingen dat per pagina wordt weergegeven en het aantal reacties dat wordt weergegeven. De standaardwaarde is **10**.

* **Maximale bestandsgrootte** Deze waarde beperkt de grootte van het geüploade bestand. Standaardlimiet is 104857600 (10 MB).

* **Maximale berichtlengte** Maximum aantal tekens dat in het tekstvak mag worden ingevoerd. De standaardwaarde is 4096 tekens.

* **Toegestane bestandstypen** Een door komma&#39;s gescheiden lijst met bestandsextensies met het &quot;punt&quot;-scheidingsteken. Bijvoorbeeld: .jpg, .jpeg, .png, .doc, .docx, .pdf. Als er bestandstypen worden opgegeven, zijn deze niet toegestaan. De standaardinstelling is niet zodanig opgegeven dat** **alle bestandstypen zijn toegestaan.

* **De Rich Text Editor** Als deze optie is ingeschakeld, kunnen opmerkingen worden ingevoerd met een markering. De optie Standaard is uitgeschakeld.

* **Opmerkingen** verwijderen Als deze optie is ingeschakeld, mogen gebruikers hun eigen opmerkingen verwijderen. Standaard is ingeschakeld.

* **Labelen** toestaan Als deze optie is ingeschakeld, wordt de mogelijkheid ingeschakeld om een tag aan het bestand toe te voegen. De optie Standaard is uitgeschakeld.

* **Toegestane naamruimten** als Tags toestaan is ingeschakeld, worden de beschikbare tags beperkt tot de geselecteerde naamruimten. Als er geen optie is geselecteerd, zijn alle opties toegestaan. Standaard zijn alle naamruimten.

* **Suggestielimiet** Als Tags toestaan is ingeschakeld, wordt met deze instelling het aantal voorgestelde tags dat wordt weergegeven, beperkt. Indien ingesteld op -1, is er geen limiet. De standaardwaarde is -1.

* **Stemmen** toestaan Als deze optie is ingeschakeld, wordt de mogelijkheid om voor een bestand te stemmen ingeschakeld. De optie Standaard is uitgeschakeld.

* **Volgend** toestaan Als deze optie is ingeschakeld, neemt u de volgende functie op voor blogartikelen, waarmee leden op de [hoogte](/help/communities/notifications.md) kunnen worden gesteld van nieuwe berichten. De optie Standaard is uitgeschakeld.

* **Mentie** inschakelen indien ingeschakeld, kunnen geregistreerde gebruikers uit de gebruikersgemeenschap andere geregistreerde leden identificeren (met voornaam, achternaam, gebruikersnaam) en ze labelen met de gebruikelijke syntaxis voor @user-name. De getagde gebruikers ontvangen meldingen over hun vermeldingen.

* **Max. aantal meldingen** Beperk het maximum aantal in een artikel toegestane vermeldingen. De standaardwaarde is 10.

* **UI-menatiepatroon** Geef de toegestane patroontekenreeks op om de geregistreerde gebruiker in een bericht te labelen (@vermeld). Bijvoorbeeld ~{{familyName}}{{givenName}}.

* **Reacties** met verbindingen toestaan Als deze optie is ingeschakeld, toestaan dat reacties op gepost opmerkingen worden ontvangen. De optie Standaard is uitgeschakeld.

#### Tabblad Gebruikersmodernisering {#user-moderation-tab}

Onder het tabblad **Gebruikersmodernisering** configureert u de moderatie van opmerkingen als opmerkingen zijn toegestaan:

* **Pre-Moderation** Als deze optie is ingeschakeld, moeten opmerkingen worden goedgekeurd voordat ze op een publicatiesite worden weergegeven. De optie Standaard is uitgeschakeld.

* **Opmerkingen** verwijderen Als deze optie is ingeschakeld, kan de bezoeker die de opmerking heeft geplaatst deze verwijderen. Standaard is ingeschakeld.

* **Ontken Commentaren** Indien gecontroleerd, sta vertrouwde op lidmoderatoren toe om commentaren te ontkennen. De optie Standaard is uitgeschakeld.

* **Sluit/open Commentaren** opnieuw als gecontroleerd, sta vertrouwde op lidmoderatoren toe om commentaren te sluiten en opnieuw te openen. De optie Standaard is uitgeschakeld.

* **Opmerkingen** markeren Als deze optie is ingeschakeld, kunnen bezoekers opmerkingen als ongepast markeren. De optie Standaard is uitgeschakeld.

* **Lijst** met redenen voor vlag Geef bezoekers de mogelijkheid om in een vervolgkeuzelijst de reden te kiezen waarom een opmerking niet geschikt is als gemarkeerd. De optie Standaard is uitgeschakeld.

* **Reden** voor aangepaste markering Als dit selectievakje is ingeschakeld, kunnen bezoekers hun eigen reden opgeven om een opmerking te markeren als ongeschikt. De optie Standaard is uitgeschakeld.

* **De Drempel** van de modernisering gaat het aantal tijden in een commentaar moet door bezoekers worden gemarkeerd alvorens de moderatoren op de hoogte worden gebracht. De standaardwaarde is één keer (**1**).

* **Markeringslimiet** Voer het aantal keren in dat een opmerking moet worden gemarkeerd voordat deze wordt verborgen in de openbare weergave. Dit getal moet groter zijn dan of gelijk zijn aan de **moderatiedrempel**. De standaardwaarde is 5.

### Tabblad Instellingen sorteren {#sort-settings-tab}

Sorteren op

Instellen als standaard

### Additional Information {#additional-information}

Meer informatie vindt u op de pagina Essentiële elementen [van](/help/communities/essentials-file-library.md) bestandsbibliotheek voor ontwikkelaars.

Voor moderatie van geposte onderwerpen en commentaren, zie het [Modereren van Door Gebruiker Gegenereerde Inhoud](/help/communities/moderate-ugc.md).

Zie Door gebruiker gegenereerde inhoud [](/help/communities/tag-ugc.md)labelen voor informatie over het labelen van geposte onderwerpen en opmerkingen.
