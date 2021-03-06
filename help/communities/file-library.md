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
source-git-commit: cdbe098ada0b6c50952284f92cc2063435034a38
workflow-type: tm+mt
source-wordcount: '753'
ht-degree: 0%

---


# Functie bestandsbibliotheek{#file-library-feature}

## Inleiding {#introduction}

De functie voor bestandsbibliotheek biedt een plaats voor ingetekende sitebezoekers (leden van de community) voor het uploaden, beheren en downloaden van bestanden binnen de site van de gebruikersgemeenschap.

In dit gedeelte van de documentatie wordt het volgende beschreven:

* De functie voor de bestandsbibliotheek toevoegen aan een AEM site.
* De montages van de configuratie voor `File Library` component.

### Een bestandsbibliotheek toevoegen aan een pagina {#adding-a-file-library-to-a-page}

Als u een `File Library`-component wilt toevoegen aan een pagina in de modus Ontwerpen, zoekt u de component:

* `Communities / File Library`

en sleep het naar de juiste plaats op een pagina.

Voor noodzakelijke informatie, bezoek [de Grondbeginselen van Componenten van Gemeenschappen](/help/communities/basics.md).

Wanneer de [vereiste client-side bibliotheken](/help/communities/essentials-file-library.md#essentials-for-client-side) worden opgenomen, wordt de `File Library`-component op deze manier weergegeven:

![file-library1](assets/file-library1.png)

### Bestandsbibliotheek {#configuring-file-library} configureren

Selecteer de geplaatste `File Library` component en selecteer `Configure` pictogram dat het Edit dialoog opent.

![configure-new](assets/configure-new.png)

![file-library2](assets/file-library2.png)

#### Tabblad Opmerkingen {#comments-tab}

Geef onder het tabblad **Opmerkingen** op of en hoe opmerkingen voor ge??ploade bestanden worden weergegeven:

* **Opmerkingen bij bestanden toestaan**

   Als deze optie is ingeschakeld, kunt u opmerkingen op ge??ploade bestanden toestaan. De optie Standaard is uitgeschakeld.

* **Opmerkingen per pagina**

   Hiermee beperkt u het aantal opmerkingen dat per pagina wordt weergegeven en het aantal reacties dat wordt weergegeven. De standaardwaarde is **10**.

* **Max. bestandsgrootte**

   Met deze waarde beperkt u de grootte van het ge??ploade bestand. Standaardlimiet is 104857600 (10 MB).

* **Max. berichtlengte**

   Maximumaantal tekens dat in het tekstvak kan worden ingevoerd. De standaardwaarde is 4096 tekens.

* **Toegestane bestandstypen**

   Een door komma&#39;s gescheiden lijst met bestandsextensies met het &quot;punt&quot;-scheidingsteken. Bijvoorbeeld: .jpg, .jpeg, .png, .doc, .docx, .pdf. Als er bestandstypen worden opgegeven, zijn deze niet toegestaan. De standaardinstelling is niet zo opgegeven dat alle bestandstypen zijn toegestaan.

* **RTF-editor**

   Als deze optie is ingeschakeld, kunnen opmerkingen worden ingevoerd met een markering. De optie Standaard is uitgeschakeld.

* **Opmerkingen verwijderen**

   Als deze optie is ingeschakeld, mogen gebruikers hun eigen opmerkingen verwijderen. Standaard is ingeschakeld.

* **Tags toestaan**

   Als deze optie is ingeschakeld, wordt de mogelijkheid ingeschakeld om een tag aan het bestand toe te voegen. De optie Standaard is uitgeschakeld.

* **Toegestane naamruimten**

   Als Tags toestaan is ingeschakeld, worden de beschikbare tags beperkt tot de geselecteerde naamruimten. Als er geen optie is geselecteerd, zijn alle opties toegestaan. Standaard zijn alle naamruimten.

* **Suggestiegrenswaarde**

   Als u Tags toestaan inschakelt, beperkt deze instelling het aantal voorgestelde tags dat wordt weergegeven. Indien ingesteld op -1, is er geen limiet. De standaardwaarde is -1.

* **Stemmen toestaan**

   Als deze optie is ingeschakeld, wordt de mogelijkheid om voor een bestand te stemmen ingeschakeld. De optie Standaard is uitgeschakeld.

* **Volgen toestaan**

   Als deze optie is ingeschakeld, neemt u de volgende functie op voor blogartikelen. Hiermee kunnen leden [op de hoogte worden gesteld](/help/communities/notifications.md) van nieuwe berichten. De optie Standaard is uitgeschakeld.

* **Menu inschakelen**

   Als deze optie is ingeschakeld, kunnen geregistreerde gebruikers in de gemeenschap andere geregistreerde leden identificeren (met voornaam, achternaam, gebruikersnaam) en ze tags toewijzen met behulp van de algemene syntaxis voor @user-name. De getagde gebruikers ontvangen meldingen over hun vermeldingen.

* **Max. aantal meldingen**

   Beperk het maximum aantal berichten dat in een bericht is toegestaan. De standaardwaarde is 10.

* **Menatiepatroon gebruikersinterface**

   Geef de toegestane patroontekenreeks op om de geregistreerde gebruiker in een bericht te labelen (@genoemd). Bijvoorbeeld ~{{familyName}}{{givenName}}.

* **Reacties met verbindingen toestaan**

   Als deze optie is ingeschakeld, kunt u reacties op geposte opmerkingen toestaan. De optie Standaard is uitgeschakeld.

#### Tabblad Gebruikersmodernisering {#user-moderation-tab}

Configureer onder het tabblad **Moderatie van gebruiker** de moderatie van opmerkingen als opmerkingen zijn toegestaan:

* **Pre-moderatie**

   Als deze optie is ingeschakeld, moeten opmerkingen worden goedgekeurd voordat ze op een publicatiesite worden weergegeven. De optie Standaard is uitgeschakeld.

* **Opmerkingen verwijderen**

   Als deze optie is ingeschakeld, kan de bezoeker die de opmerking heeft geplaatst deze verwijderen. Standaard is ingeschakeld.

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

   Voer het aantal keren in dat een opmerking moet worden gemarkeerd door bezoekers voordat moderatoren op de hoogte worden gesteld. De standaardwaarde is ????n keer (**1**).

* **Limiet voor markering**

   Voer het aantal keren in dat een opmerking moet worden gemarkeerd voordat deze wordt verborgen in de openbare weergave. Dit getal moet groter dan of gelijk zijn aan de **Moderatiedrempel**. De standaardwaarde is 5.

### Tabblad Instellingen sorteren {#sort-settings-tab}

Sorteren op

Instellen als standaard

### Aanvullende informatie {#additional-information}

Meer informatie vindt u op de pagina [Essenti??le elementen bestandsbibliotheek](/help/communities/essentials-file-library.md) voor ontwikkelaars.

Zie [Door gebruiker gegenereerde inhoud modereren](/help/communities/moderate-ugc.md) voor de moderatie van geposte onderwerpen en opmerkingen.

Zie [Door gebruiker gegenereerde inhoud labelen](/help/communities/tag-ugc.md) voor het labelen van geposte onderwerpen en opmerkingen.
