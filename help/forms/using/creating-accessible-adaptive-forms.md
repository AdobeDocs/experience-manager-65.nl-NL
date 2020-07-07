---
title: Toegankelijke adaptieve formulieren maken
seo-title: Toegankelijke adaptieve formulieren maken
description: Met AEM Forms kunt u gereedschappen gebruiken en toegankelijke adaptieve formulieren maken en voldoen aan toegankelijkheidsnormen.
seo-description: Met AEM Forms kunt u gereedschappen gebruiken en toegankelijke adaptieve formulieren maken en voldoen aan toegankelijkheidsnormen.
uuid: 6472bc2d-47ca-4883-88b7-5de0b758fd00
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
discoiquuid: 1e95c66b-d132-4c44-a1dc-31fd09af8113
docset: aem65
translation-type: tm+mt
source-git-commit: ebf3f34af7da6b1a659ac8d8843152b97f30b652
workflow-type: tm+mt
source-wordcount: '1780'
ht-degree: 0%

---


# Toegankelijke adaptieve formulieren maken{#creating-accessible-adaptive-forms}

## Inleiding {#introduction}

Een toegankelijk formulier is een formulier dat iedereen kan gebruiken, inclusief gebruikers met speciale behoeften. Adaptieve formulieren bevatten een aantal functies en mogelijkheden die de bruikbaarheid voor gebruikers met verschillende mogelijkheden verbeteren. Door toegankelijkheid in adaptieve formulieren te creëren, kan niet alleen een zo breed mogelijk publiek voor inhoud worden bereikt, maar is het ook een vereiste bij het verstrekken van documenten in geografische gebieden waar naleving van toegankelijkheidsnormen verplicht is. AEM Forms helpen formulierontwikkelaars om te voldoen aan de toegankelijkheidsstandaarden.

Tijdens het ontwerpen van een adaptief formulier moet de auteur de volgende punten in overweging nemen om een toegankelijke adaptieve vorm te maken:

* Controleer het formulier met het hulpprogramma voor toegankelijkheidstests voor de ANDI (Accessible Name and Description Inspector)
* Geef juiste labels voor formulierbesturingselementen
* Verstrek tekstequivalenten voor beelden
* Geef voldoende kleurcontrast op
* Zorg ervoor dat formulierbesturingselementen via het toetsenbord toegankelijk zijn

## Vereiste

U hebt een toegankelijkheidstool nodig, zoals ANDI ( **Accessible Name and Description Inspector)** en een **adaptief formulierthema dat is ontwikkeld om toegankelijkheidsgerelateerde problemen** te verhelpen en zo een toegankelijk adaptief formulier te maken.

### Gereedschap voor toegankelijkheidstesten downloaden en installeren

Met het hulpprogramma ANDI (Accessible Name and Description Inspector) kunt u compatibiliteitsproblemen met betrekking tot toegankelijkheid in webinhoud opsporen en verhelpen. Dit is het aanbevolen gereedschap onder de richtlijnen Trusted Tester v5 van het Department of Homeland Security. Het is ontwikkeld door de afdeling Sociale &#x200B; van de Verenigde Staten om te controleren of Section 508 de webinhoud in acht neemt. Het gereedschap:

* Hiermee kunt u toegankelijkheidsproblemen &#x200B; op een webpagina detecteren
* Biedt suggesties voor het verbeteren van &#x200B;
* Detecteert problemen met toetsenbordtoegankelijkheid en kleurcontrast
* Geeft duidelijk aan welke inhoud van de schermlezer voldoet aan de normen

ANDI werkt met alle grote internetbrowsers. Zie de documentatie [van](https://www.ssa.gov/accessibility/andi/help/install.html) ANDI voor gedetailleerde instructies om het hulpmiddel te vormen en te gebruiken.

### Download en installeer het Ultramarine-Toegankelijke thema

Het Ultramarijn-Toegankelijke thema is een verwijzingsthema. Hiermee kunt u demonstreren hoe u kleurcontrast en andere toegankelijkheidsgerelateerde problemen in een adaptieve vorm kunt oplossen. Adobe raadt u aan een aangepast thema voor de productieomgeving te maken op basis van de stijlen die door uw organisatie zijn goedgekeurd. Voer de volgende stappen uit om het thema te uploaden naar uw AEM-instantie:

1. Download het themapakket.
1. Ga naar **[!UICONTROL Experience Manager]** > **[!UICONTROL Navigation]**![ Navigatie](assets/Smock_Compass_18_N.svg) > **[!UICONTROL Forms]** op uw AEM-instantie.
1. Tik op **[!UICONTROL Create]** > **[!UICONTROL File Upload]**. Selecteer en upload het bestand x Ultramarine-Accessible-Theme.zip. Het thema wordt geüpload naar uw AEM-instantie.

## Een adaptief formulier toegankelijk maken

U moet zich op vier belangrijke aspecten concentreren: toetsenbordnavigatie, kleurcontrast, betekenisvolle alternatieve tekst voor afbeeldingen en geschikte labels voor formulierbesturingselementen om een adaptief formulier toegankelijk te maken. Voer de volgende stappen uit om uw bestaande adaptieve formulieren toegankelijk te maken:

### 1. Een toegankelijk thema toepassen en aanvullende oplossingen uitvoeren

Pas het Ultramarijn-Toegankelijke thema toe op uw bestaande adaptieve vorm. Het thema toepassen:

1. Open het aangepaste formulier voor bewerking.
1. Selecteer een component en tik op het bovenliggende pictogram. Tik in het contextmenu op het configuratiepictogram **[!UICONTROL Adaptive Form Container]** en tik vervolgens op dit pictogram.
1. Selecteer het thema Ultramarijn-Toegankelijk in de eigenschappenbrowser en tik op **[!UICONTROL Save]** het pictogram.
1. Vernieuw het browservenster. Het thema wordt toegepast op het adaptieve formulier.

Nadat u een toegankelijk thema hebt toegepast, voert u de onderstaande aanvullende oplossingen uit. De oplossingen zijn naast toegankelijkheidsoplossingen die in het toegankelijke thema worden behandeld:

1. Voeg een betekenisvolle alternatieve tekst voor de logoafbeelding toe in het adaptieve formulier.

   Geef een betekenisvolle alternatieve tekst op voor afbeeldingen in kop- en voettekstcomponenten van de adaptieve formuliersjabloon. Wanneer u de sjabloon herstelt en gebruikt om een adaptief formulier te maken, nemen de adaptieve formulieren alle correcties over die betrekking hebben op toegankelijkheid en die worden toegepast op de kop- en voettekst van de sjabloon.  Breng voor een bestaand adaptief formulier wijzigingen aan op het niveau van het adaptieve formulier. Wijzigingen in een adaptief formuliersjabloon worden niet automatisch doorgevoerd in een bestaand adaptief formulier.

1. Voeg een koptekstcomponent met formuliernaam toe aan het adaptieve formulier. Als in uw formulierontwerp een bedrijfsnaam is opgegeven, voegt u ook een aparte kopcomponent voor de bedrijfsnaam toe.

   De meeste toegankelijkheidsfuncties informeren gebruikers over de hiërarchie van de inhoud, zodat ze de structuur van de webpagina beter kunnen begrijpen. Stel verschillende kopniveaus in voor de naam van de organisatie en de tekst voor de naam van het formulier op het adaptieve formulier, zodat deze tekst een hiërarchische structuur krijgt. Gebruik bovendien een tekstcomponent voor elk deelvenster en elke sectie met een geschikt kopniveau om een hiërarchie te maken.

   ![Een koptekststijl toepassen](assets/apply-style.gif)

1. Wijzig de achtergrondkleur van de voettekst om het juiste contrast te gebruiken in overeenstemming met de toegankelijkheidsnormen om de zichtbaarheid en leesbaarheid van de tekst te verbeteren. U kunt ANDI gebruiken om problemen met kleurcontrast in uw formulier te zoeken. Gebruik ook geen erg klein lettertype. Kleine lettertypen zijn moeilijk leesbaar.

1. Vervang de onderdelen switch en imagekeuze in het bestaande adaptieve formulier door keuzeselectie (radio).

1. Vervang de numerieke stepper-component in het bestaande adaptieve formulier door een numerieke box-component.

1. Datuminvoerveld vervangen door datumkiezerveld.

1. Stel de weergave-, validatie- en bewerkingspatronen in voor de component met de datumkiezer. Stel ook een aangepast foutbericht voor validatie in. U hebt bijvoorbeeld een ongeldige datum opgegeven. De juiste notatie voor de datum is YYYY-MM-DD.

1. Stel aangepaste toegankelijkheidstekst in voor de component met de datumkiezer. Voer bijvoorbeeld uw geboortedatum in. Schermlezers lezen deze aangepaste toegankelijkheidsteksten.

1. Gebruik een korte beschrijving in plaats van een lange beschrijving voor adaptieve formuliercomponenten. Een lange beschrijving voegt hulpknoop toe. Zorg ervoor dat het adaptieve formulier geen knop Help heeft.

1. Voeg aangepaste toegankelijkheidstekst toe aan alle alleen-lezen cellen in tabellen. Schakel ook alle alleen-lezen cellen van tabellen uit.

1. Eventuele scripthandtekeningvelden uit het adaptieve formulier verwijderen. Configureer het adaptieve formulier zodat u Adobe Sign kunt gebruiken voor een naadloze digitale ondertekeningservaring.

### 2. Geef juiste labels voor formulierbesturingselementen {#provide-proper-labels-for-form-controls}

Met het label of de titel van een component wordt aangegeven wat de formuliercomponent vertegenwoordigt. De tekst Voornaam geeft bijvoorbeeld aan dat gebruikers hun voornaam in een tekstveld moeten invoeren. Om door schermlezers toegankelijk te zijn, wordt het label programmatisch gekoppeld aan een formuliercomponent. Alternatief, wordt de vormcontrole gevormd met extra toegankelijkheidsinformatie.

Het label dat door schermlezers wordt waargenomen, hoeft niet noodzakelijkerwijs hetzelfde te zijn als het visuele bijschrift. In sommige gevallen, kunt u specifieker over het doel van de controle willen zijn. Voor elk veldobject in een formulier kunnen de toegankelijkheidsopties worden gebruikt om op te geven wat de schermlezer aankondigt om het specifieke formulierveld te identificeren.

Voer de volgende stappen uit om de optie Toegankelijkheid te gebruiken:

1. Selecteer een component en tik op ![cmp](assets/cmppr.png).
1. Klik **[!UICONTROL Accessibility]** in de zijbalk om de gewenste toegankelijkheidsoptie te kiezen.

### Toegankelijkheidsopties in formuliercomponenten {#accessibility-options-in-form-components}

![Toegankelijkheidsopties in formuliercomponenten](assets/accessibility-options.png)

**Auteurs van aangepaste tekstformulieren** leveren de inhoud in het tekstveld Aangepaste tekst voor de toegankelijkheidsoptie. De ondersteunende hulpmiddelen, zoals schermlezers, gebruiken deze aangepaste tekst. Het gebruiken van het plaatsen van de Titel is de beste optie in een meerderheid van de scenario&#39;s. U kunt overwegen alleen aangepaste schermlezertekst te maken als de titel of een korte beschrijving niet mogelijk is.

**Korte beschrijving** Voor de meeste componenten wordt de korte beschrijving weergegeven wanneer de gebruiker de aanwijzer op de component plaatst. U kunt deze optie instellen in het veld Korte beschrijving onder de optie Help-inhoud.

**Titel** Gebruik deze optie als u wilt dat AEM Forms het visuele label dat aan het formulierveld is gekoppeld, gebruiken als schermlezertekst.

**Naam** U kunt een waarde opgeven in het veld Naam van het tabblad Binding. De naam mag geen spaties bevatten.

**Als u Geen** selecteert, krijgt het formulierobject geen naam in het gepubliceerde formulier. Geen is een aanbevolen instelling voor formulierbesturingselementen.

>[!NOTE]
>
>* Keuzerondje en selectievakje kunnen slechts twee toegankelijkheidsopties hebben, namelijk Aangepaste tekst en Titel.
>* Voor op XFA gebaseerde adaptieve formulieren wordt de toegankelijkheidsoptie overgenomen van de toegankelijkheidsopties die zijn ingesteld in de XDP. Knopinfo van XDP wordt toegewezen aan Korte beschrijving en Bijschrift wordt toegewezen aan Titel. De andere opties werken zoals is.


### 3. Verstrek tekstequivalenten voor beelden {#provide-text-equivalents-for-images}

Afbeeldingen kunnen sommige gebruikers helpen het begrip te verbeteren. Voor gebruikers die schermlezers gebruiken, verminderen afbeeldingen echter de toegankelijkheid van het formulier. Als u ervoor kiest om afbeeldingen te gebruiken, geef dan tekstbeschrijvingen op voor alle afbeeldingen.

Zorg ervoor dat in de tekst het object en het doel ervan in het formulier worden beschreven. Een schermlezer leest deze alternatieve tekst wanneer een afbeelding wordt aangetroffen. Voor een afbeelding moet altijd een alternatieve tekst worden opgegeven.

Selecteer een afbeeldingscomponent en tik op ![cmp](assets/cmppr.png). Geef in het zijpaneel onder Eigenschappen alternatieve tekst op voor een afbeelding.

![Alternatieve tekst voor een afbeelding](assets/image-properties.png)

### 4. Geef voldoende kleurcontrast op {#provide-sufficient-color-contrast}

Bij het ontwerpen van toegankelijkheid moet u rekening houden met aanvullende richtlijnen voor kleurgebruik. Auteurs van formulieren kunnen kleuren gebruiken om de weergave van formulieren te verbeteren door verschillende formuliercomponenten te markeren. Onjuist gebruik van kleur kan een formulier echter moeilijk of onmogelijk leesbaar maken voor mensen met verschillende mogelijkheden.

Gebruikers met een visuele handicap vertrouwen op een hoog contrast tussen tekst en de achtergrond voor het lezen van digitale inhoud. Zonder voldoende contrast kan een formulier moeilijk, zo niet onmogelijk, leesbaar worden voor sommige gebruikers.

U wordt aangeraden het standaardfont en de standaardachtergrondkleuren te gebruiken, namelijk de zwarte inhoud op een witte achtergrond. Als u de standaardkleuren wijzigt, kiest u een donkere voorgrondkleur op een lichte achtergrondkleur of andersom.

Zie Aangepaste thema&#39;s [maken voor adaptieve formulieren](/help/forms/using/creating-custom-adaptive-form-themes.md)voor meer informatie over het wijzigen van het kleurcontrast en het thema voor adaptieve formulieren.

### 5. Zorg ervoor dat formulierbesturingselementen via het toetsenbord toegankelijk zijn {#ensure-that-form-controls-are-keyboard-accessible}

Een toegankelijk formulier kan volledig worden ingevuld met alleen het toetsenbord of een vergelijkbaar invoerapparaat. Gebruikers met een beperkte mobiliteit of een visuele handicap hebben wellicht geen andere keuze dan het toetsenbord te gebruiken en veel gebruikers die een muis kunnen gebruiken, geven de voorkeur aan invoer via het toetsenbord. Door de verschillende invoermethoden toe te staan, maakt u niet alleen toegankelijke formulieren, maar ook formulieren die beter zijn afgestemd op de voorkeuren van alle gebruikers.

De volgende sneltoetsen zijn beschikbaar in AEM Forms.

| Actie | Sneltoets |
|---|---|
| De cursor door een formulier verplaatsen | Tab |
| De cursor achterwaarts door een formulier verplaatsen | Shift+Tab |
| Naar volgend deelvenster gaan | Alt+Pijl-rechts |
| Naar het vorige deelvenster gaan | Alt+Pijl-links |
| De gevulde gegevens in een formulier opnieuw instellen | Alt+R |
| Een formulier verzenden | Alt+Z |

## Gebruik het gereedschap Toegankelijkheid om resterende toegankelijkheidsproblemen te zoeken

Met de Toegankelijke ANDI (Name and Description Inspector) kunt u problemen met toegankelijkheidseisen in een adaptieve vorm identificeren en corrigeren. Met ANDI de toegankelijkheidsproblemen in een adaptieve vorm zoeken:

1. Open het adaptieve formulier in de voorbeeldmodus.
1. Klik op het pictogram van het gereedschap ANDI met bladwijzer. Het ANDI-gereedschap analyseert het adaptieve formulier en geeft toegankelijkheidsproblemen weer. Raadpleeg de documentatie [van](https://www.ssa.gov/accessibility/andi/help/howtouse.html)ANDI voor meer informatie over het gebruik van het hulpprogramma.
1. De door ANDI gemelde problemen beoordelen en oplossen.