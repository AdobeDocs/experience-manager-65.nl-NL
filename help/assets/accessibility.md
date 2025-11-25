---
title: Toegankelijke eigenschappen en interfaces van  [!DNL Experience Manager Assets]
description: Weet hoe de toegankelijkheidseigenschappen in  [!DNL Adobe Experience Manager]  6.5  [!DNL Assets]  hulpgebruikers met handicaps.
contentOwner: AG
feature: Asset Management
role: User, Developer, Leader
exl-id: 15555941-99a2-4586-8d7b-b22f3ec17805
solution: Experience Manager, Experience Manager Assets
source-git-commit: 07289e891399a78568dcac957bc089cc08c7898c
workflow-type: tm+mt
source-wordcount: '1879'
ht-degree: 0%

---

<!--
Possible topics to cover in this article are below.

* Compile a list of enhancements done in the last ~1 year.
* Showcase a few prominent use cases (search?) in a screencast.
* Top-level actions supported, such as clickable UI elements, keyboard shortcuts, popup dialogs, and so on.
* List all UIs that are keyboard navigable.
* Unified list of the product tasks supported, such as, search assets, download assets, add or editing metadata, use DM Viewers, and so on.
* Do we need to add support matrix of user tasks with browser and screen reader combinations. Everything may not work in all browsers and/or using all screen readers.
* Any exceptions that users should be aware of. It may help to call out (it may be done in ACR) what tasks are NOT supported.
* CTAs – what's next and more info from AEM team:
  * Link to ACRs on a.com.
  * Generic a11y info by Adobe to begin with.
  * Link to a11y-specific online methods to report issues, seek support, or request enhancements, if any. Asked the a11y team on Slack.
-->

# Toegankelijkheidsfuncties in [!DNL Adobe Experience Manager Assets] {#accessibility-in-aem-assets}

Met [!DNL Adobe Experience Manager] kunnen makers van inhoud en uitgevers op internet fantastische ervaringen bieden. Adobe streeft ernaar de makers met een handicap op te nemen door de toegankelijkheid van [!DNL Experience Manager] te verbeteren. De software wordt voortdurend uitgebreid om te voldoen aan de behoeften van alle soorten gebruikers en voldoet aan de wereldwijde standaarden, waaronder personen met een visuele, auditieve, mobiliteitsfunctie of andere handicap.

[!DNL Experience Manager] publiceert conformiteitsinformatie met een beschrijving van de standaarden die het hanteert, geeft een overzicht van de toegankelijkheidsfuncties in het product en beschrijft het compatibiliteitsniveau. Met de compatibiliteitsrapporten voor toegankelijkheid kunnen [!DNL Experience Manager] -gebruikers begrijpen in welke mate aan verschillende standaarden wordt voldaan. Dankzij de verbeteringen in [!DNL Assets] kunnen alle gebruikers de interfaces eenvoudig gebruiken via toetsenbord, schermlezer, vergrotingen en andere ondersteunende hulpmiddelen.

[!DNL Experience Manager] biedt verschillende ondersteuningsniveaus voor de volgende standaarden:

* [ de Richtlijnen van de Toegankelijkheid van de Inhoud van het Web (WCAG) 2.1 ](https://www.w3.org/TR/WCAG/).
* [ Herzien Sectie 508 van de Wet van de Herstel ](https://www.access-board.gov/guidelines-and-standards/communications-and-it/about-the-ict-refresh/final-rule/text-of-the-standards-and-guidelines).
* [ Initiatief van de Toegankelijkheid - Toegankelijke Rijke Toepassingen van Internet (WAI-ARIA) door W3C ](https://www.w3.org/WAI/standards-guidelines/aria/).
* [ EN 301 549 ](https://en.wikipedia.org/wiki/EN_301_549).

Om een rapport met details van het niveau van naleving te lezen, zie [ het rapport van de Overeenstemming van de Toegankelijkheid ](https://www.adobe.com/accessibility/compliance.html) (ACR) pagina.

Om te weten hoe [!DNL Dynamic Media] toegankelijk is, zie [ toegankelijkheid in  [!DNL Dynamic Media]](/help/assets/accessibility-dm.md).

## Hulptechnologieën {#at-support}

Gebruikers met een handicap vertrouwen vaak op hardware en software om toegang te krijgen tot webinhoud en softwareproducten te gebruiken. Deze gereedschappen worden hulptechnologieën genoemd. [!DNL Experience Manager Assets] kan met de volgende soorten ondersteunende hulpmiddelen (AT) werken wanneer het gebruiken van de kernfunctionaliteit van de software:

* Schermlezers en schermvergroting.
* Software voor spraakherkenning.
* Toetsenbordgebruik - navigatie en sneltoetsen.
* Hulpapparatuur, inclusief besturingselementen voor switches, vernieuwbare braillebeeldschermen en andere invoerapparaten voor de computer.
* Gereedschappen voor het vergroten van de gebruikersinterface.

## [!DNL Experience Manager Assets] Gebruik toegankelijke gevallen {#accessible-assets-use-cases}

In [!DNL Experience Manager] voldoen de toegankelijkheidsfuncties aan twee belangrijke vereisten van [!DNL Experience Manager] -gebruikers en hun klanten.

* Voor inhoudsontwerpers en makers zijn er functies om toegankelijke inhoud te maken en te publiceren die op hun beurt door hun klanten en websitebezoekers wordt gebruikt. Personen met een handicap gebruiken de inhoud met behulp van ondersteunende hulpmiddelen. Voor details, zie [ richtlijnen van de Webtoegankelijkheid ](/help/managing/web-accessibility.md).
* Met [!DNL Experience Manager] hebben gebruikers en beheerders met een handicap ook toegang tot de gebruikersinterface en besturingselementen voor het maken en beheren van inhoud. Personen met een handicap kunnen ondersteunende hulpmiddelen gebruiken om door de [!DNL Assets] -mogelijkheden te navigeren, te gebruiken en deze te beheren.

De kernfuncties in [!DNL Assets] zijn toegankelijker dan voorheen en worden regelmatig bijgewerkt om de naleving van wereldwijde standaarden te verbeteren. De CRUD-bewerkingen in [!DNL Assets] hebben een bepaalde mate van toegankelijkheid die in deze bewerkingen is ingebouwd. DAM-workflows, zoals het toevoegen, beheren, zoeken en distribueren van elementen, zijn toegankelijk via sneltoetsen, schermlezertekst, kleurcontrast, enzovoort.

## Ondersteuning voor toetsenbord {#keyboard-use}

Veel elementen van de gebruikersinterface die kunnen worden aangeklikt of geactiveerd met een aanwijzer, kunnen ook worden gebruikt met het toetsenbord. Met een toetsenbord kunnen gebruikers zich richten op UI-elementen en de juiste actie ondernemen. Gebruikers kunnen rechtstreeks sneltoetsen gebruiken om een opdracht of handeling te activeren zonder dat ze zich hoeven te richten op UI-elementen en deze met het toetsenbord hoeven te activeren. Gebruikers kunnen bijvoorbeeld de tijdlijn van een element aan de linkerkant van de gebruikersinterface openen door via het toetsenbord naar het besturingselement voor de gebruikersinterface te bladeren en `Return` te selecteren en `Alt + 2` sneltoets te selecteren.

<!-- TBD items:

* The option to toggle between list view and card view exposes relevant info to the screen readers. What about column view option? This info can go into 'basic handling' info aka article to 'understand and use the workspace'.
* How to open and browse through the profile popup dialog in [!DNL Experience Manager] UI using a keyboard? The navigation does not match the order of visual display of options on the UI. This info can go into 'basic handling' info aka article to 'understand and use the workspace'. What about setting preferences and impersonating a user?
* Using the [!DNL Experience Manager] tag browser and operating the options like delete tag? This info can go into 'basic handling' info aka article to 'understand and use the workspace'.
* Read-only form fields can be focused with the keyboard. Can users tab to these fields to understand the contents and are they able to copy text from the fields?
-->

### Sneltoetsen in [!DNL Assets] {#keyboard-shortcuts}

De volgende handelingen in [!DNL Assets] werken met de vermelde sneltoetsen. De meeste sneltoetsen die van toepassing zijn op [!DNL Experience Manager] consoles, zijn ook van toepassing op [!DNL Assets] . Zie [ toetsenbordkortere weg voor Consoles ](/help/sites-authoring/keyboard-shortcuts.md#keyboard-shortcuts). Zie [ toelaten of onbruikbaar maken de toetsenbordkortere weg ](/help/sites-authoring/keyboard-shortcuts.md#deactivating-keyboard-shortcuts).

| Gebruikersinterface of scenario | Sneltoets | Handeling |
|---|---|---|
| Kolomweergave in de gebruikersinterface van [!DNL Assets] | Pijl-omhoog en Pijl-omlaag | Navigeer naar bestanden en mappen in dezelfde hiërarchie. |
| Kolomweergave in de gebruikersinterface van [!DNL Assets] | Pijl-links en Pijl-rechts | Navigeer naar bestanden en mappen boven of onder de huidige map. |
| Door mappen bladeren in [!DNL Assets] | `/` | Roep zoekopdracht aan door het vak Onderzoek te openen. |
| [!DNL Assets] Console | &grave; | Zijrails in-/uitschakelen |
| [!DNL Assets] Console | `Alt + 1` | Open de inhoudsstructuur. |
| [!DNL Assets] Console | `Alt + 2` | Open [!UICONTROL Navigation] linkerrails. |
| [!DNL Assets] Console | `Alt + 3` | Weergave [!UICONTROL Timeline] van een geselecteerd element. |
| [!DNL Assets] Console | `Alt + 4` | Open Live Copy-referenties van het geselecteerde element. |
| [!DNL Assets] Console | `Alt + 5` | Begin met zoeken en zoek in de geselecteerde map. |
| Element of map is geselecteerd | Backspace | Verwijder het geselecteerde element of de geselecteerde map. |
| Element of map is geselecteerd | `p` | Open de pagina Eigenschappen van het geselecteerde element. |
| Element of map is geselecteerd | `e` | Het geselecteerde element bewerken. |
| Element of map is geselecteerd | `m` | Verplaats het geselecteerde element. |
| Element of map is geselecteerd | `Ctrl + c` | Kopieer het geselecteerde element. |
| Element of map is geselecteerd | `Esc` | De selectie annuleren. |
| Dialoogvenster wordt geopend en heeft de focus | `Esc` | Dialoogvenster Sluiten. |
| In een map in DAM | `Ctrl + v` | Plak het gekopieerde element. |
| [!DNL Assets] Console | `Ctrl + A` | Selecteer alle elementen. |
| Elementeigenschappenpagina&#39;s | `Ctrl + S` | Wijzigingen opslaan. |
| [!DNL Assets] Console | `?` | Zie een lijst met sneltoetsen. |

## Aanmelden en navigeren in de gebruikersinterface van [!DNL Assets] {#login}

Gebruikers kunnen met het toetsenbord naar het aanmeldingsveld navigeren en dit invullen om zich aan te melden. De foutberichten vanwege onjuiste combinaties van gebruikersnaam en wachtwoord op de aanmeldingspagina worden door schermlezers gemeld wanneer de fout optreedt.

Nadat u zich hebt aangemeld, kunnen DAM-gebruikers via het toetsenbord navigeren binnen de gebruikersinterface van [!DNL Assets] . U kunt met het toetsenbord navigeren naar de elementen van de gebruikersinterface, zoals linkerspoor, menu&#39;s, gebruikersprofiel, zoekbalk, bestanden en mappen en instellingen voor beheer en configuratie. De volgorde van de toetsenbordnavigatie is van links naar rechts en van boven naar beneden. Wanneer u navigeert met een toetsenbord, wordt een optie die kan worden geactiveerd wanneer de focus wordt geplaatst, gemarkeerd met een beter kleurcontrast en door een schermlezer van commentaar voorzien. Indien van toepassing, wordt de status — bijvoorbeeld uitgevouwen, samengevouwen en gemengde staat — van de opties voor focus in het menu aangekondigd door een schermlezer. Bovendien kondigt de schermlezer het doel van de optie waarop actie kan worden uitgevoerd aan in plaats van de vormgeving of interfacepositie.

Als een gebruiker de optie Help of gebruikersprofiel in het menu uitbreidt, wordt de juiste optie of status door de schermlezer aangekondigd. Als een gebruiker de optie voor het gebruikersprofiel uitbreidt, kunnen de beschikbare opties met een toetsenbord worden geselecteerd. Een beheerder kan zich bijvoorbeeld een andere gebruiker voorstellen. Als een gebruiker een tekenreeks zoekt via de optie [!UICONTROL Help] , wordt &#39;&#39;Help zoeken&#39;&#39; weergegeven om aan te geven dat er een zoekopdracht wordt uitgevoerd.

<!-- TBD: Removing for now. Add a more informative video later. Host it on tv.adobe

![Keyboard navigation of top options in [!DNL Experience Manager] user interface](assets/keyboard-navigation-in-aem.gif)

*Figure: Navigating through the options at the top of [!DNL Experience Manager] user interface using `Tab` key.*
-->

## Blader door elementen en bekijk de bijbehorende informatie {#browse}

In de gebruikersinterface van [!DNL Assets] kunnen gebruikers met het toetsenbord door de lijst met bestaande digitale elementen in de DAM-gegevensopslagruimte bladeren, een voorvertoning van een element bekijken of dit downloaden, gegenereerde uitvoeringen bekijken, overschakelen op weergaven, de gegenereerde uitvoeringen bekijken, de tijdlijn en versiegeschiedenis bekijken, opmerkingen en verwijzingen bekijken en metagegevens beheren.

<!-- TBD: Not sure about the following list items mean:

In [!DNL Experience Manager] header section, when navigating in browse mode, screen reader now announces,
  
  * Suggestions to search in Omnisearch.
  * The state as expanded or collapsed for Solutions, Help, Inbox and User options.
  * The Searching Help status message that is displayed when user enters a search string in Search for Help field under Help option
  * The error message if incorrect value is entered in Impersonate as field under User option and focus correctly moves to the text field (NPR-33804).

Review CQ-4282133 before adding - Close option in a coral-dialog was not accessible through keyboard, due to which user cannot trigger close option through keyboard press in version preview dialog. After fix, user can close dialog through close option using keyboard.

* CQ-4273122 - Assets of video/audio type will have aria-label in format "Multimedia player: <Title>" so users relying on screen-reader will get to know that they are video/audio assets.
-->

Wanneer u in de gegevensopslagruimte bladert, verbetert de volgende functionaliteit de toegankelijkheid:

* Schermlezer kondigt tekstopties aan die het doel of de functionaliteit van de pictogrammen in plaats van hun namen weergeven.
* Gebruikers kunnen de interactieve gebruikersinterface-opties in de lijst met verwijzingen openen en activeren met behulp van toetsenbordtoetsen.
* De elementen in elke rij in de lijstweergave worden door schermlezers aangekondigd als de elementen van dezelfde rij.
* Wanneer u navigeert met de `Tab` -toets, kunt u de focus verplaatsen naar de sluitoptie in de versievoorvertoning.
* Wanneer u met het toetsenbord bladert, hebben de gemarkeerde opties voor een actiefunctie een prominentere visuele focus met een verbeterd contrast. Hierdoor wordt het gefocuste gebied beter herkenbaar voor de gebruiker.
* Als u de toets `Esc` gebruikt om de snelactiepictogrammen uit de miniatuurweergave te verwijderen, wordt de toetsenbordfocus niet verwijderd van het laatste item dat de focus heeft.
* Als een element is geselecteerd en u `Alt + 4` -sneltoets selecteert, wordt de lijst met [!UICONTROL References] geopend in de linkertrack. Met de `Tab` -toets kunnen gebruikers door de niet-nulreferentie-items navigeren. Door alleen de referentie-items te doorbladeren die niet gelijk zijn aan nul, bespaart u ook moeite en toetsaanslagen.
* Opmerkingen over een element zijn beschikbaar in de tijdlijn van het element. Het is toegankelijk als linkerspoor wordt betreden gebruikend een toetsenbord of een toetsenbordkortere weg.
* [!UICONTROL View Settings] in [!DNL Experience Manager] zijn toegankelijk via een toetsenbord. Gebruikers kunnen met de pijltoetsen door de beschikbare kaartgrootten navigeren en door de pijltoetsen bladeren en door de muis bladeren en andere elementen instellen in de bestaande weergave Weergave-instellingen.

<!-- TBD: Gradually, as more enhancements are done in these categories, add more content.

## Add and upload digital assets {#upload}

## Configure and administer [!DNL Assets] {#config-admin}

* List the a11y fixes in workflows to configure and administer [!DNL Experience Manager Assets]?
* Some enhancements in Processing profiles creation or application to a folder?
* Some enhancements to metadata properties UI?
-->

## Digitale middelen beheren {#manage-assets}

Veel taken voor middelenbeheer, zoals CRUD-bewerkingen, het downloaden van middelen en het toevoegen van metagegevens, zijn in verschillende mate toegankelijk. Met [!DNL Assets] kunt u de taken uitvoeren met behulp van verschillende ondersteunende hulpmiddelen, zoals een schermlezer en een toetsenbord.

Zie een videodemonstratie van hoe te om een toetsenbord te gebruiken om [ de bewaarplaats te doorbladeren en activa ](https://youtu.be/K3dgqMRQJys) te downloaden.

Voor meta-gegevensverrichtingen die typisch door rollen zoals marketers en beheerders worden gedaan verbeteren de volgende eigenschappen toegankelijkheid:

* [!UICONTROL Save & Close] -optie op de elementpagina [!UICONTROL Properties] is nu toegankelijk via het toetsenbord.
* Schermlezers kondigen de opties aan om de geselecteerde labels te verwijderen op de tab [!UICONTROL Basic] van het element [!UICONTROL Properties] .
* Gebruikers kunnen het pop-updialoogvenster Datumkiezer gebruiken met een toetsenbord. Het Datepicker-gebruikersinterface-element wordt gebruikt om de gegevens in- en uit-tijden in te stellen en de datum te selecteren.
* De sleepfunctionaliteit met het toetsenbord werkt in [!UICONTROL Metadata Schema Editor] in de bladermodus van schermlezers correct.
* Een gebruiker kan de focus verplaatsen met het toetsenbord naar het veld Gebruiker toevoegen of Groep onder [!UICONTROL Closed User Group] op het [!UICONTROL Permissions] tabblad van de map [!UICONTROL Properties] .

## Digitale middelen zoeken {#search-assets}

Een snelle en naadloze zoekervaring met middelen verhoogt de snelheid van de inhoud. De gebruiksgevallen voor snelheid van inhoud maken deel uit van de kernfunctionaliteit van [!DNL Assets] . Als u een zoekopdracht wilt starten vanaf de zoekbalk, kunnen gebruikers de sneltoets `/` gebruiken of `Tab` samen met schermlezers gebruiken om snel de zoekoptie te zoeken. De het schermlezer beperkt de naam van de optie als &quot;Knoop van het Onderzoek&quot;wanneer de nadruk op de onderzoeksoptie ![ onderzoeksoptie ](assets/do-not-localize/search_icon.png) is. Gebruikers kunnen `Return` selecteren om het vak Onderzoek te openen. De schermlezer vertelt niet alleen over het trefwoord dat in het zoekvak is getypt, maar vertelt ook over de suggesties die door [!DNL Experience Manager Assets] worden aangeboden. Gebruikers kunnen een combinatie van pijltoetsen, `Return` en `Tab` gebruiken om toegang te krijgen tot de verschillende opties om een zoekopdracht te activeren.

De zoekfunctionaliteit is toegankelijk via de volgende functies:

* De paginatitel, die beschikbaar is voor een schermlezer, helpt de pagina te identificeren als de zoekpagina van elementen.
* Gebruikers zoeken elementen vanuit het veld Zoeken. Gebruikers kunnen het venster openen met de toetsenbordnavigatie of de sneltoets `/` .
* Gebruikers kunnen het trefwoord zoeken en de automatische suggesties selecteren met de pijltoetsen. Gemarkeerde suggestie kan worden geselecteerd met de sleutel `Return` en de middelen worden gezocht naar de geselecteerde suggestie.
* Schermlezers kunnen de selectievakjes met gemengde status (waarin de selectievakjes op het eerste niveau niet zijn geselecteerd en zijn doorgehaald) identificeren en aankondigen in het deelvenster Filters wanneer u de zoekresultaten filtert. Dit geldt alleen voor geneste voorspelling als u alle selectievakjes op het eerste niveau selecteert.
* Wanneer het vak Onderzoek is gesloten, wordt de focus van de gebruiker naar de zoekopties verplaatst.

Bij het filteren van zoekresultaten:

* De pagina met zoekresultaten heeft een informatieve titel voor een beter begrip van schermlezers.
* Een schermlezer kondigt de opties in het zoekfilter aan als uitbreidbare accordeons.
* Voorvertoningen met opties voor verschillende statussen worden door schermlezers aangekondigd.

## Elementen delen {#share-assets}

<!-- TBD: Anything about accessibility in DA, BP? AAL team confirmed that there's no content for AAL a11y on helpx.
-->

Bij het delen van elementen verbeteren de volgende functies de toegankelijkheid:

* Een gebruiker kan de focus verplaatsen met het toetsenbord in het veld Zoeken en E-mailadres toevoegen in het dialoogvenster voor het delen van koppelingen.

* In het dialoogvenster voor het delen van koppelingen kunnen de schermlezers tijdens het navigeren in de bladermodus:

   * Commentaar de tabelinformatie niet wanneer het dialoogvenster wordt geladen.
   * Kan naar alle vermelde suggesties navigeren.
   * Beschrijf de weergegeven suggesties voor de velden E-mailadres en Zoeken toevoegen.

## Toegankelijke documentatie {#accessible-docs}

[!DNL Experience Manager] biedt toegankelijke documentatie voor gebruik door mensen met een handicap. Met de volgende instructies kunt u de inhoud die nu wordt aangeboden, toegankelijk maken, terwijl Adobe de sjabloon en de inhoud blijft verbeteren:

* Schermlezers kunnen de tekst lezen.
* Afbeeldingen en illustraties hebben alternatieve tekst.
* Toetsenbordnavigatie is mogelijk.
* Contrastverhoudingen helpen u bepaalde onderdelen van de documentatiewebsite te markeren.

## Feedback geven {#a11y-feedback}

Gebruik de volgende methoden om feedback te geven, vragen te stellen en productverbeteringen aan te vragen met betrekking tot toegankelijkheid:

* Vul de vorm in [ www.adobe.com/accessibility/feedback.html ](https://www.adobe.com/accessibility/feedback.html).
* E-mail ons op access@adobe.com.

>[!MORELIKETHIS]
>
>* [ eigenschappen van de Toegankelijkheid in  [!DNL Dynamic Media]](/help/assets/accessibility-dm.md).
>* [ nota&#39;s van de Versie van verhogingen die in elke versie van Service Pack ](/help/release-notes/release-notes.md) worden gedaan.
>* [[!DNL Adobe Experience Manager]  toegankelijkheidsbegeleiding ](/help/managing/web-accessibility.md).
>* [ de rapporten van de Overeenstemming (ACR) en VPAT lijst voor de oplossingen van Adobe ](https://www.adobe.com/accessibility/compliance.html).
