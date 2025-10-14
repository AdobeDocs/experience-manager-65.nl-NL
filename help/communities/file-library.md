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
* Configuration settings for the `File Library` component.

### Een bestandsbibliotheek toevoegen aan een pagina {#adding-a-file-library-to-a-page}

Als u een component `File Library` in de ontwerpmodus aan een pagina wilt toevoegen, gaat u naar de component:

* `Communities / File Library`

En sleep het naar de juiste plaats op een pagina.

Voor noodzakelijke informatie, bezoek {de Grondbeginselen van de Componenten van 0} Gemeenschappen [&#128279;](/help/communities/basics.md).

Wanneer de [&#x200B; vereiste cliënt-zijbibliotheken &#x200B;](/help/communities/essentials-file-library.md#essentials-for-client-side) inbegrepen zijn, is het hoe de `File Library` component verschijnt:

![&#x200B; dossier-library1 &#x200B;](assets/file-library1.png)

### Bestandsbibliotheek configureren {#configuring-file-library}

Selecteer de geplaatste component `File Library` , zodat u het pictogram `Configure` kunt openen en selecteren waarmee het dialoogvenster Bewerken wordt geopend.

![&#x200B; vorm-nieuw &#x200B;](assets/configure-new.png)

![&#x200B; dossier-library2 &#x200B;](assets/file-library2.png)

#### Tabblad Opmerkingen {#comments-tab}

Onder het **lusje van Commentaren**, specificeer als en hoe de commentaren voor geupload dossiers verschijnen:

* **sta Commentaren op Dossiers** toe

  Als deze optie is ingeschakeld, kunt u opmerkingen op geüploade bestanden toestaan. De optie Standaard is uitgeschakeld.

* **Commentaren per Pagina**

  Hiermee beperkt u het aantal opmerkingen dat per pagina wordt weergegeven en het aantal reacties dat wordt weergegeven. Het gebrek is **10**.

* **Max de Grootte van het Dossier**

  Deze waarde beperkt de grootte van het geüploade bestand. De standaardwaarde is 104857600 (10 MB).

* **Maximale Lengte van het Bericht**

  Maximumaantal tekens dat in het tekstvak kan worden ingevoerd. De standaardwaarde is 4096 tekens.

* **Toegestane Types van Dossier**

  Een door komma&#39;s gescheiden lijst met bestandsextensies met het scheidingsteken &#39;punt&#39;. Bijvoorbeeld .jpg, .jpeg, .png, .doc, .docx, .pdf. Als er bestandstypen zijn opgegeven, zijn bestandstypen die niet zijn opgegeven niet toegestaan. De standaardinstelling is niet zo opgegeven dat alle bestandstypen zijn toegestaan.

* **Rich Text Editor**

  Als deze optie is ingeschakeld, kunnen opmerkingen worden ingevoerd met een markering. De optie Standaard is uitgeschakeld.

* **Schrap Commentaren**

  Als deze optie is ingeschakeld, mogen gebruikers hun eigen opmerkingen verwijderen. Standaard is ingeschakeld.

* **Toestaan Tags**

  Als deze optie is ingeschakeld, wordt de mogelijkheid ingeschakeld om een tag aan het bestand toe te voegen. De optie Standaard is uitgeschakeld.

* **Toegestane Namespaces**

  Als Tags toestaan is ingeschakeld, zijn de beschikbare tags beperkt tot de naamruimten die zijn gecontroleerd. Als er geen naamruimten zijn gecontroleerd, zijn alle toegestaan. Standaard zijn alle naamruimten.

* **de Grens van de Suggestie**

  Als u Tags toestaan inschakelt, beperkt deze instelling het aantal voorgestelde tags dat wordt weergegeven. Indien ingesteld op -1, is er geen limiet. De standaardwaarde is -1.

* **Toestaan het Stemmen**

  Als deze optie is ingeschakeld, is de mogelijkheid om op een bestand te stemmen ingeschakeld. De optie Standaard is uitgeschakeld.

* **toestaat na**

  Als gecontroleerd, omvat de volgende eigenschap voor blogartikelen, die leden [&#x200B; toestaat om &#x200B;](/help/communities/notifications.md) van nieuwe posten op de hoogte worden gebracht. De optie Standaard is uitgeschakeld.

* **laat Mentie** toe

  Als deze optie is ingeschakeld, kunnen geregistreerde gebruikers in de gemeenschap andere geregistreerde leden identificeren (met voornaam, achternaam, gebruikersnaam) en ze tags toewijzen met behulp van de algemene syntaxis voor @user-name. De getagde gebruikers ontvangen meldingen over hun berichten.

* **Maximale Onthulpingen**

  Beperk het maximum aantal berichten dat in een bericht is toegestaan. De standaardwaarde is 10.

* **het Patroon van de Mentie UI**

  Geef de toegestane patroontekenreeks op, zodat u de geregistreerde gebruiker in een advertentie kunt voorzien van een tag (@genoemd). Bijvoorbeeld `~{{familyName}}{{givenName}}` .

* **staat Verbonden Antwoorden** toe

  Als deze optie is ingeschakeld, kunt u reacties op geposte opmerkingen toestaan. De optie Standaard is uitgeschakeld.

#### Tabblad Gebruikersmodernisering {#user-moderation-tab}

Onder het **lusje van de Moderatie van de Gebruiker**, vorm moderatie van commentaren, als de commentaren worden toegestaan:

* **pre-Moderatie**

  Als deze optie is ingeschakeld, moeten opmerkingen worden goedgekeurd voordat ze op een publicatiesite worden weergegeven. De optie Standaard is uitgeschakeld.

* **Schrap Commentaren**

  Als deze optie is ingeschakeld, kan de bezoeker die de opmerking heeft geplaatst deze desgewenst verwijderen. Standaard is ingeschakeld.

* **ontken Commentaren**

  Als deze optie is ingeschakeld, staat u vertrouwde moderatoren toe opmerkingen te weigeren. De optie Standaard is uitgeschakeld.

* **dicht/heropen Commentaren**

  Als deze optie is ingeschakeld, moet u vertrouwde moderatoren van leden toestaan opmerkingen te sluiten en opnieuw te openen. De optie Standaard is uitgeschakeld.

* **Commentaren van de Vlag**

  Als deze optie is ingeschakeld, kunnen bezoekers opmerkingen als ongeschikt markeren. De optie Standaard is uitgeschakeld.

* **Lijst van de Reden van de Vlag**

  Als deze optie is ingeschakeld, kunnen bezoekers in een vervolgkeuzelijst de reden kiezen waarom een opmerking als onjuist is gemarkeerd. De optie Standaard is uitgeschakeld.

* **Reden van de Vlag van de Douane**

  Als deze optie is ingeschakeld, kunnen bezoekers hun eigen reden opgeven om een opmerking als ongeschikt te markeren. De optie Standaard is uitgeschakeld.

* **Drempel van de Moderatie**

  Voer het aantal keren in dat een opmerking moet worden gemarkeerd door bezoekers voordat moderatoren op de hoogte worden gesteld. Het gebrek is één keer (**1**).

* **het Vlaggen Grens**

  Voer het aantal keren in dat een opmerking moet worden gemarkeerd voordat deze wordt verborgen in de openbare weergave. Dit aantal moet groter dan of gelijk aan de **Drempel van de Moderatie** zijn. De standaardwaarde is 5.

### Tabblad Instellingen sorteren {#sort-settings-tab}

Sorteren op

Instellen als standaard

### Aanvullende informatie {#additional-information}

Meer informatie kan op de [&#128279;](/help/communities/essentials-file-library.md) pagina van de Hoofdzaak van de Bibliotheek van het 0&rbrace; Dossier &lbrace;voor ontwikkelaars worden gevonden.

Voor moderatie van geposte onderwerpen en commentaren, zie [&#x200B; het Modereren van Gebruiker-Gegenereerde Inhoud &#x200B;](/help/communities/moderate-ugc.md).

Voor het etiketteren van geposte onderwerpen en commentaren, zie [&#x200B; Tags Gebruiker-Gegenereerde Inhoud &#x200B;](/help/communities/tag-ugc.md).
