---
title: Functie bestandsbibliotheek
description: Met de functie Bestandsbibliotheek kunnen aangemelde sitebezoekers bestanden uploaden, beheren en downloaden.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
docset: aem65
exl-id: 05cfaab5-a12d-475f-9095-a9fb13571d0a
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '741'
ht-degree: 0%

---

# Functie bestandsbibliotheek{#file-library-feature}

## Inleiding {#introduction}

De functie voor bestandsbibliotheek biedt een plaats voor ingetekende sitebezoekers (leden van de community) voor het uploaden, beheren en downloaden van bestanden binnen de communitysite.

In dit gedeelte van de documentatie wordt het volgende beschreven:

* De functie voor de bestandsbibliotheek toevoegen aan een AEM site.
* De montages van de configuratie voor de `File Library` component.

### Een bestandsbibliotheek toevoegen aan een pagina {#adding-a-file-library-to-a-page}

Als u een `File Library` naar een pagina in de auteursmodus, zoek de component:

* `Communities / File Library`

En sleep het naar de juiste plaats op een pagina.

Voor de nodige informatie gaat u naar [Grondbeginselen van Community-componenten](/help/communities/basics.md).

Wanneer de [vereiste clientbibliotheken](/help/communities/essentials-file-library.md#essentials-for-client-side) worden opgenomen, is het hoe `File Library` wordt weergegeven:

![file-library1](assets/file-library1.png)

### Bestandsbibliotheek configureren {#configuring-file-library}

Selecteer de geplaatste `File Library` zodat u toegang hebt tot `Configure` Het pictogram waarmee het dialoogvenster Bewerken wordt geopend.

![configure-new](assets/configure-new.png)

![file-library2](assets/file-library2.png)

#### Tabblad Opmerkingen {#comments-tab}

Onder de **Opmerkingen** , geeft u op of en hoe opmerkingen voor geüploade bestanden worden weergegeven:

* **Opmerkingen bij bestanden toestaan**

  Als deze optie is ingeschakeld, kunt u opmerkingen op geüploade bestanden toestaan. De optie Standaard is uitgeschakeld.

* **Opmerkingen per pagina**

  Hiermee beperkt u het aantal opmerkingen dat per pagina wordt weergegeven en het aantal reacties dat wordt weergegeven. Standaard is **10**.

* **Max. bestandsgrootte**

  Deze waarde beperkt de grootte van het geüploade bestand. De standaardwaarde is 104857600 (10 MB).

* **Max. berichtlengte**

  Maximumaantal tekens dat in het tekstvak kan worden ingevoerd. De standaardwaarde is 4096 tekens.

* **Toegestane bestandstypen**

  Een door komma&#39;s gescheiden lijst met bestandsextensies met het scheidingsteken &#39;punt&#39;. Bijvoorbeeld .jpg, .jpeg, .png, .doc, .docx, .pdf. Als er bestandstypen zijn opgegeven, zijn bestandstypen die niet zijn opgegeven niet toegestaan. De standaardinstelling is niet zo opgegeven dat alle bestandstypen zijn toegestaan.

* **RTF-editor**

  Als deze optie is ingeschakeld, kunnen opmerkingen worden ingevoerd met een markering. De optie Standaard is uitgeschakeld.

* **Opmerkingen verwijderen**

  Als deze optie is ingeschakeld, mogen gebruikers hun eigen opmerkingen verwijderen. Standaard is ingeschakeld.

* **Tags toestaan**

  Als deze optie is ingeschakeld, wordt de mogelijkheid ingeschakeld om een tag aan het bestand toe te voegen. De optie Standaard is uitgeschakeld.

* **Toegestane naamruimten**

  Als Tags toestaan is ingeschakeld, zijn de beschikbare tags beperkt tot de naamruimten die zijn gecontroleerd. Als er geen naamruimten zijn gecontroleerd, zijn alle toegestaan. Standaard zijn alle naamruimten.

* **Suggestiegrenswaarde**

  Als u Tags toestaan inschakelt, beperkt deze instelling het aantal voorgestelde tags dat wordt weergegeven. Indien ingesteld op -1, is er geen limiet. De standaardwaarde is -1.

* **Stemmen toestaan**

  Als deze optie is ingeschakeld, is de mogelijkheid om op een bestand te stemmen ingeschakeld. De optie Standaard is uitgeschakeld.

* **Volgen toestaan**

  Indien ingeschakeld, neemt u de volgende functie voor blogartikelen op, waardoor leden kunnen worden [aangemeld](/help/communities/notifications.md) van nieuwe posten. De optie Standaard is uitgeschakeld.

* **Menu inschakelen**

  Als deze optie is ingeschakeld, kunnen geregistreerde gebruikers in de gemeenschap andere geregistreerde leden identificeren (met voornaam, achternaam, gebruikersnaam) en ze tags toewijzen met behulp van de algemene syntaxis voor @user-name. De getagde gebruikers ontvangen meldingen over hun berichten.

* **Max. aantal meldingen**

  Beperk het maximum aantal berichten dat in een bericht is toegestaan. De standaardwaarde is 10.

* **Menatiepatroon gebruikersinterface**

  Geef de toegestane patroontekenreeks op, zodat u de geregistreerde gebruiker in een advertentie kunt voorzien van een tag (@genoemd). Bijvoorbeeld: `~{{familyName}}{{givenName}}`.

* **Reacties met verbindingen toestaan**

  Als deze optie is ingeschakeld, kunt u reacties op geposte opmerkingen toestaan. De optie Standaard is uitgeschakeld.

#### Tabblad Gebruikersmodernisering {#user-moderation-tab}

Onder de **Moderatie gebruiker** tab, configureer de moderatie van opmerkingen als opmerkingen zijn toegestaan:

* **Pre-moderatie**

  Als deze optie is ingeschakeld, moeten opmerkingen worden goedgekeurd voordat ze op een publicatiesite worden weergegeven. De optie Standaard is uitgeschakeld.

* **Opmerkingen verwijderen**

  Als deze optie is ingeschakeld, kan de bezoeker die de opmerking heeft geplaatst deze desgewenst verwijderen. Standaard is ingeschakeld.

* **Opmerkingen weigeren**

  Als deze optie is ingeschakeld, staat u vertrouwde moderatoren toe opmerkingen te weigeren. De optie Standaard is uitgeschakeld.

* **Opmerkingen sluiten/opnieuw openen**

  Als deze optie is ingeschakeld, moet u vertrouwde moderatoren van leden toestaan opmerkingen te sluiten en opnieuw te openen. De optie Standaard is uitgeschakeld.

* **Opmerkingen markeren**

  Als deze optie is ingeschakeld, kunnen bezoekers opmerkingen als ongeschikt markeren. De optie Standaard is uitgeschakeld.

* **Lijst met redenen voor vlag**

  Als deze optie is ingeschakeld, kunnen bezoekers in een vervolgkeuzelijst de reden kiezen waarom een opmerking als onjuist is gemarkeerd. De optie Standaard is uitgeschakeld.

* **Reden voor aangepaste vlag**

  Als deze optie is ingeschakeld, kunnen bezoekers hun eigen reden opgeven om een opmerking als ongeschikt te markeren. De optie Standaard is uitgeschakeld.

* **Moderniseringsdrempel**

  Voer het aantal keren in dat een opmerking moet worden gemarkeerd door bezoekers voordat moderatoren op de hoogte worden gesteld. Standaard is dit één keer (**1**).

* **Limiet voor markering**

  Voer het aantal keren in dat een opmerking moet worden gemarkeerd voordat deze wordt verborgen in de openbare weergave. Dit getal moet groter zijn dan of gelijk zijn aan het **Moderniseringsdrempel**. De standaardwaarde is 5.

### Tabblad Instellingen sorteren {#sort-settings-tab}

Sorteren op

Instellen als standaard

### Aanvullende informatie {#additional-information}

Meer informatie is te vinden op de [Essentiële elementen bestandsbibliotheek](/help/communities/essentials-file-library.md) pagina voor ontwikkelaars.

Voor moderatie van geposte onderwerpen en commentaren, zie [Door de gebruiker gegenereerde inhoud moderniseren](/help/communities/moderate-ugc.md).

Voor het etiketteren van geposte onderwerpen en commentaren, zie [Door de gebruiker gegenereerde inhoud labelen](/help/communities/tag-ugc.md).
