---
title: Gepubliceerde formulieren openen en invullen
seo-title: Gepubliceerde formulieren openen en invullen
description: Forms Portal beschikt over componenten waarmee webontwikkelaars een formulierportal kunnen maken en aanpassen op websites die zijn gemaakt met Adobe Experience Manager (AEM).
seo-description: Forms Portal beschikt over componenten waarmee webontwikkelaars een formulierportal kunnen maken en aanpassen op websites die zijn gemaakt met Adobe Experience Manager (AEM).
uuid: 44731604-5d97-46fa-baa9-0c020c634fa7
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: publish
discoiquuid: 88dc8ef2-95ce-4906-ac28-eecc3a32a64e
docset: aem65
translation-type: tm+mt
source-git-commit: 27a054cc5d502d95c664c3b414d0066c6c120b65
workflow-type: tm+mt
source-wordcount: '962'
ht-degree: 0%

---


# Gepubliceerde formulieren openen en invullen{#accessing-and-filling-published-forms}

In een vorm-centric poortplaatsingsopstelling, vormen ontwikkeling en poortontwikkeling zijn twee verschillende activiteiten. Terwijl formulierontwerpers formulieren ontwerpen en opslaan in een gegevensopslagruimte, maken webontwikkelaars een webtoepassing voor die lijstformulieren en verwerken ze verzendingen. Forms wordt vervolgens naar de weblaag gekopieerd omdat er geen communicatie is tussen de formulieropslagplaats en de webtoepassing.

Dit leidt vaak tot problemen met het beheer van de installatie- en productievertragingen. Als bijvoorbeeld een nieuwere versie van een formulier beschikbaar is in de gegevensopslagruimte, vervangt de formulierontwerper het formulier op de weblaag, wijzigt de webtoepassing en implementeert deze opnieuw op de openbare site. Als u de webtoepassing opnieuw implementeert, kan de server enige downtime veroorzaken. Aangezien de serveronderbreking een geplande activiteit is, kunnen de veranderingen niet aan de openbare plaats onmiddellijk worden geduwd.

Forms Portal verlaagt beheerkosten en productievertragingen. Webontwikkelaars beschikken over componenten om een formulierportal te maken en aan te passen op websites die zijn gemaakt met Adobe Experience Manager (AEM).

Zie [Inleiding tot het publiceren van formulieren op een portal](/help/forms/using/introduction-publishing-forms.md) voor meer informatie over het portal Formulieren en de bijbehorende functies.

## Aan de slag met formulierportal {#getting-started-with-forms-portal}

Navigeer naar de pagina van de portal voor gepubliceerde formulieren. Zie [Een pagina voor een formulierportal maken](../../forms/using/creating-form-portal-page.md) voor meer informatie over het maken van een pagina voor een formulierportal.

De component Search en Lister van het portaal van Rems toont de vormen beschikbaar op het Publish geval van de AEM server. Deze lijst bevat alle formulieren of formulieren die in het filter zijn gedefinieerd op het moment dat de pagina met de portal Formulieren wordt gemaakt. Een pagina voor een portal Formulieren ziet er ongeveer hetzelfde uit als in de volgende afbeelding:

![Een voorbeeldpagina voor formulierportalen  ](assets/forms-portal-page.png)

Een voorbeeldpagina voor formulierportalen

### {#search-and-lister} zoeken en registreren

Met de component Zoeken en register kunt u de volgende functionaliteit toevoegen aan uw formulierportal:

* Formulieren weergeven die in het vak beschikbaar zijn in de deelvenster-, kaart- of rasterweergave. Deze functie ondersteunt ook aangepaste sjablonenList-formulieren uit specifieke mappen in Forms Manager.
* Geef op hoe formulieren worden gegenereerd: HTML5, PDF of beide.
* Geef op hoe PDF- en XFA-formulieren worden gegenereerd - HTML5, PDF of beide. Niet-XFA-formulieren als HTML5.
* U kunt zoeken op formulieren op basis van criteria inschakelen, zoals formuliereigenschappen, metagegevens en codes.
* Formuliergegevens verzenden naar een servlet.
* Gebruik aangepaste stijlbladen (CSS) om de vormgeving van de portal aan te passen.
* Koppelingen naar formulieren maken.

U kunt op de pagina Forms Portal naar formulieren zoeken met de volgende opties:

* Volledige tekst zoeken
* Geavanceerd zoeken

Met zoeken in volledige tekst kunt u formulieren zoeken en weergeven op basis van de opgegeven trefwoorden.

![Een geavanceerd zoekdialoogvenster](assets/search-panel.png)

Een geavanceerd zoekdialoogvenster

Met Geavanceerd zoeken kunt u formulieren doorzoeken op basis van opgegeven formuliereigenschappen. Dit levert specifiekere resultaten op dan full-text onderzoek. De geavanceerde zoekopdracht omvat zoeken op basis van labels, eigenschappen (zoals Auteur, Beschrijving en Titel), wijzigingsdatum en volledige tekst.

In het register worden formulieren weergegeven op basis van de zoekparameters. Elk formulier in het zoekresultaat wordt weergegeven met een pictogram dat is gekoppeld aan het bijbehorende formulier. U kunt op het pictogram klikken om het bijbehorende formulier te openen en ermee te werken.

### Formulieren {#filling-a-form} invullen

![Een voorbeeldadaptief formulier](assets/filling_a_form.png)

Een voorbeeldadaptief formulier

De formulieren zijn toegankelijk via de koppeling die bij het formulier hoort in de component Zoeken en Registreren op de pagina.

Elk formulier bevat Help-informatie waarmee een gebruiker het formulier kan invullen.

#### Concepten en indiening {#drafts-and-submission}

Een gebruiker kan een concept van een formulier opslaan door op de knop Opslaan te klikken. Hierdoor kan de gebruiker gedurende een bepaalde periode aan een formulier werken voordat het formulier wordt verzonden.

De gegevens die in het formulier zijn ingevuld (inclusief bijlagen), worden opgeslagen als concept op de server. Het concept van een formulier kan een willekeurig aantal keren worden opgeslagen. Het opgeslagen formulier wordt weergegeven op het tabblad Concepten van de component Concept en verzending van de pagina.

Nadat het invullen van het formulier is voltooid, verzendt de gebruiker de formulieren door op de knop Verzenden op het formulier te klikken. De verzonden formulieren worden weergegeven op het tabblad Verzending van de component Concept en verzending van de pagina.

>[!NOTE]
>
>Verzonden formulieren worden alleen weergegeven op het tabblad Verzonden Forms als de verzendactie voor het adaptieve formulier is geconfigureerd als Forms Portal Handeling verzenden. Zie [De handeling Verzenden configureren](../../forms/using/configuring-submit-actions.md) voor meer informatie over het verzenden van handelingen.

![Concepten en verzendingen](assets/draft-submission.png)

Concepten en verzendingen

## Een nieuw formulier starten met ingediende formuliergegevens {#start-a-new-form-using-submitted-form-data}

Er zijn bepaalde formulieren die u vaak moet invullen en verzenden. Het formulier voor het indienen van een individuele belastingaangifte wordt bijvoorbeeld elk jaar ingediend. In dergelijke gevallen verandert een deel van de informatie telkens wanneer u het formulier invult, maar het grootste deel ervan, zoals de persoonlijke gegevens en de familiedetails, verandert niet. U moet echter nog steeds het volledige formulier helemaal opnieuw invullen.

AEM Forms kan u helpen het invullen van formulieren te optimaliseren en de tijd die nodig is om een formulier in te vullen en opnieuw te verzenden, aanzienlijk te verkorten. Eindgebruikers kunnen een nieuw formulier starten met gegevens uit een verzonden formulier. Deze functionaliteit is ingebouwd in [Concepten en Submissies component](../../forms/using/draft-submission-component.md). Wanneer u concepten en verzendingscomponenten toevoegt aan de pagina van uw portal Formulieren en deze publiceert, vinden eindgebruikers een optie op de tabbladen Verzonden Forms en Concept Forms om een nieuw formulier te starten met gegevens uit een verzonden formulier. Deze optie wordt in de volgende afbeelding gemarkeerd.

![start-a-new-form](assets/start-a-new-form.png)

Wanneer u op de knop klikt om een nieuw formulier te starten, wordt een nieuw formulier geopend met gegevens uit het bijbehorende verzonden formulier. U kunt de gegevens nu naar wens controleren en bijwerken en het formulier verzenden.
