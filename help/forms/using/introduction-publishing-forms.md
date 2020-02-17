---
title: Inleiding tot het publiceren van formulieren op een portal
seo-title: Inleiding tot het publiceren van formulieren op een portal
description: AEM Forms beschikt over componenten waarmee u uw formulierportal kunt samenstellen. In deze artikelen wordt u kennisgemaakt met de beschikbare onderdelen van de portal Formulieren.
seo-description: AEM Forms beschikt over componenten waarmee u uw formulierportal kunt samenstellen. In deze artikelen wordt u kennisgemaakt met de beschikbare onderdelen van de portal Formulieren.
uuid: 658de12b-66e5-438b-ae8f-872ec11a9c3e
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: publish
discoiquuid: 9f1beb89-8eb1-4e37-a5e8-19752b21374a
docset: aem65
translation-type: tm+mt
source-git-commit: 5831c173114a5a6f741e0721b55d85a583e52f78

---


# Inleiding tot het publiceren van formulieren op een portal{#introduction-to-publishing-forms-on-a-portal}

## Overzicht van AEM Forms Portal-componenten {#aem-forms-portal-components-overview}

In een typisch vorm-centric portaalplaatsingsscenario, vormen ontwikkeling en poortontwikkeling zijn twee gescheiden activiteiten. Terwijl formulierontwerpers formulieren ontwerpen en opslaan in een gegevensopslagruimte, maken webontwikkelaars een webtoepassing om formulieren weer te geven en de verzending van formulieren af te handelen. Formulieren worden naar de weblaag gekopieerd omdat er geen communicatie is tussen de formulieropslagplaats en de webtoepassing.

Dergelijke scenario&#39;s leiden vaak tot beheerproblemen en productievertragingen. Als er bijvoorbeeld een nieuwere versie van een formulier beschikbaar is in de gegevensopslagruimte, moet u het formulier op de weblaag vervangen, de webtoepassing wijzigen en het formulier opnieuw distribueren op de openbare site. Als u de webtoepassing opnieuw implementeert, kan dit leiden tot serverdowntime. De serverdowntime is doorgaans een geplande activiteit en daarom kunnen de wijzigingen niet onmiddellijk naar de openbare site worden doorgevoerd.

AEM Forms biedt portalcomponenten die beheerkosten en productievertragingen verminderen. Met deze componenten kunnen webontwikkelaars een formulierportal maken en aanpassen op websites die zijn gemaakt met Adobe Experience Manager (AEM).

![AEM Forms Portal](assets/aem-forms-portal.png)

Met de onderdelen van het formulierportaal kunt u de volgende functionaliteit toevoegen:

* Formulieren weergeven in aangepaste indelingen. De lay-outs Lijstweergave, Kaart en Deelvensterweergave zijn beschikbaar in het vak. U kunt uw eigen aangepaste lay-outs maken.
* Hiermee kunt u aangepaste metagegevens en aangepaste handelingen weergeven terwijl u deze weergeeft.
* Formulieren weergeven die door de gebruikersinterface van AEM Forms worden gepubliceerd in het publicatieexemplaar waarin Forms Portal-componenten worden gebruikt.
* Eindgebruikers toestaan formulieren zowel in HTML- als in PDF-indeling te genereren.
* Gebruik een aangepast HTML-profiel om formulieren te genereren.
* U kunt zoeken op formulieren op basis van verschillende criteria inschakelen, zoals formuliereigenschappen, metagegevens en codes.
* Formuliergegevens verzenden naar een servlet.
* Gebruik aangepaste CSS om het uiterlijk van de portal aan te passen.
* Koppelingen naar formulieren maken.
* Hier worden concepten en verzendingen weergegeven die betrekking hebben op een adaptief formulier dat door de eindgebruiker is gemaakt.

## Beschikbare AEM Forms Portal-componenten {#available-aem-forms-portal-components}

AEM Forms verstrekt de volgende poortcomponenten uit de doos, die onder de Diensten **van het** Document en de Voorspelende **componentengroepen van de Diensten van het** Document worden gegroepeerd:

### Zoeken en registreren {#search-amp-lister}

Met de component Zoeken en registreren kunt u formulieren vanuit de formulieropslagplaats op uw portalpagina weergeven en configuratieopties voor het weergeven van formulieren op basis van opgegeven criteria. U kunt hiermee ook zoekcriteria opgeven waarmee gebruikers van uw portal kunnen zoeken in de lijst met formulieren.

### Concepten en verzendingen {#drafts-amp-submissions}

In de component Zoeken en opslaan worden formulieren weergegeven die openbaar zijn gemaakt door de auteur van Forms, maar in de component Concepten en verzendingen worden formulieren weergegeven die zijn opgeslagen als concept voor het later invullen van formulieren en die zijn verzonden. Deze component verstrekt gepersonaliseerde ervaring aan om het even welke het programma geopende gebruiker.

### Link {#link}

Met de component Koppeling kunt u overal op de pagina een koppeling naar een formulier maken. Overweeg een scenario waarin u een trainingsprogramma aanbiedt en u wilt dat uw gebruikers een formulier indienen om zich te registreren voor de training. Op uw website hebt u de programmagegevens geplaatst. Onder de details wilt u een koppeling naar het registratieformulier opgeven. De component Link kan u helpen die koppeling te maken.

## Workflow Forms Portal {#forms-portal-workflow}

Met de portal Formulieren kunt u formulieren vanuit de formulieropslagplaats op uw portalpagina weergeven. U kunt hiermee ook zoekcriteria opgeven waarmee gebruikers van uw portal kunnen zoeken in de lijst met formulieren. U kunt ook de component Concepten en verzendingen gebruiken om formulieren weer te geven die zijn opgeslagen als concept voor het later invullen van formulieren en die zijn verzonden. U moet een bepaalde set bewerkingen uitvoeren voordat deze functies beschikbaar komen op een sitepagina. Voer de stappen in de vermelde opeenvolging uit om de componenten en respectieve functionaliteit op een plaatspagina beschikbaar te maken:

1. **Forms Portal-componenten** inschakelen:De onderdelen van de portal Formulieren zijn niet beschikbaar voor gebruik. [Schakel de componenten van AEM sidekick](/help/forms/using/enabling-forms-portal-components.md) in voor een pagina van AEM-sites.
1. **** Formulieren weergeven op een pagina (pagina Formulierportal maken): U kunt formulieren weergeven op zowel AEM-sites als niet-AEM-sitepagina&#39;s. De lijst bevat formulieren die beschikbaar zijn in de publicatie-instantie. Een gebruiker kan formulieren openen en invullen. Wanneer een gebruiker een formulier opent, wordt er een nieuw exemplaar van het formulier gemaakt:

   1. **Formulieren weergeven op een pagina** met AEM-sites: Voeg de component **[Zoeken en registeren](../../forms/using/creating-form-portal-page.md)**toe aan de pagina en configureer de**[ keuzelijst](../../forms/using/creating-form-portal-page.md#p-list-pane-p)** in deze component om formulieren op een pagina weer te geven. Voeg en vorm de component van de Ruit **van het** Onderzoek aan de component van het **Onderzoek &amp; van het Register** ook om onderzoeksfunctionaliteit aan de pagina toe te voegen. De pagina met de taalcomponent voor formulieren wordt [pagina](../../forms/using/creating-form-portal-page.md)Formulierportal genoemd.

   1. **** Formulieren weergeven op een pagina met niet-AEM-sites: Gebruik de zoekAPI&#39;s [van de](/help/forms/using/listing-forms-webpage-using-apis.md) formulierportal om formulieren op pagina&#39;s van niet-AEM-sites te zoeken, op te halen en weer te geven.

1. **Concepten en ingediende formulieren weergeven op een pagina** van een formulierportal: Voeg de component Concepten en verzendingen toe aan en configureer deze op de pagina Formulierportal. De component bevat een lijst met alle formulieren in het concept en de formulieren die al zijn verzonden.

   Als u wilt dat een ingediend adaptief formulier op het tabblad Verzending wordt weergegeven, stelt u de handeling **** Verzenden in op **[Formulierportaal Handeling](configuring-submit-actions.md)verzenden.**U kunt ook de optie Formulierportal verzenden inschakelen. Wanneer een gebruiker het formulier verzendt, wordt het formulier toegevoegd aan het tabblad Verzending.

1. **** Opslag configureren voor het concept en de verzonden formuliergegevens: Concepten en verzonden gegevens worden standaard opgeslagen in de AEM-opslagplaats. In een productieomgeving wordt aanbevolen geen concept- of verzonden formuliergegevens op te slaan in een AEM-opslagplaats. [Configureer de poortcomponent voor formulieren om gegevens op een beveiligde locatie](../../forms/using/draft-submission-component.md#customizing-the-storage)op te slaan.
1. **** (Optioneel) De onderdelen van de portal Formulieren aanpassen: Pas de paginasjablonen [](../../forms/using/customizing-templates-forms-portal-components.md) van uw formulierportal aan voor een duidelijke weergave van de componenten.
1. **** (Optioneel) Voeg aangepaste metagegevens toe aan formulieren: Voeg aangepaste metagegevens aan formulieren [](../../forms/using/customizing-templates-forms-portal-components.md) toe om de ervaring van lijsten en zoekopdrachten te verbeteren.
1. **** De pagina Formulierportal publiceren: De pagina Formulierportal is nu gereed. Publiceer de pagina.

## Verwante artikelen {#related-articles}

* [Formulierportonderdelen inschakelen](/help/forms/using/enabling-forms-portal-components.md)
* [Pagina Formulierportal maken](../../forms/using/creating-form-portal-page.md)
* [Formulieren op een webpagina weergeven met API&#39;s](/help/forms/using/listing-forms-webpage-using-apis.md)
* [Concepten en verzendingscomponent gebruiken](../../forms/using/draft-submission-component.md)
* [Opslag van concepten en verzonden formulieren aanpassen](../../forms/using/draft-submission-component.md#customizing-the-storage)
* [Voorbeeld voor het integreren van concepten en verzendingen in de database](integrate-draft-submission-database.md)
* [Sjablonen aanpassen voor componenten van een formulierportal](../../forms/using/customizing-templates-forms-portal-components.md)
* [Inleiding tot het publiceren van formulieren op een portal](../../forms/using/introduction-publishing-forms.md)

