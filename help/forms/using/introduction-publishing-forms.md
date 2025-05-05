---
title: Inleiding tot het publiceren van formulieren op een portal
description: Adobe Experience Manager Forms biedt componenten die u kunt gebruiken om uw Forms Portal te maken. In dit artikel wordt u kennisgemaakt met de beschikbare Forms Portal-componenten.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: publish
docset: aem65
exl-id: 240ed4d8-b21b-46eb-80a9-9e8093b77235
solution: Experience Manager, Experience Manager Forms
feature: Forms Portal
role: Admin, User, Developer
source-git-commit: 539da06db98395ae6eaee8103a3e4b31204abbb8
workflow-type: tm+mt
source-wordcount: '1043'
ht-degree: 0%

---

# Inleiding tot het publiceren van formulieren op een portal{#introduction-to-publishing-forms-on-a-portal}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/configure-forms-portal.html?lang=nl-NL) |
| AEM 6,5 | Dit artikel |


## Overzicht van AEM Forms Portal-componenten {#aem-forms-portal-components-overview}

In een typisch vorm-centric portaalplaatsingsscenario, vormen ontwikkeling en portaalontwikkeling zijn twee gescheiden activiteiten. Terwijl formulierontwerpers formulieren ontwerpen en opslaan in een gegevensopslagruimte, maken webontwikkelaars een webtoepassing om formulieren weer te geven en de verzending van formulieren af te handelen. Forms wordt naar de weblaag gekopieerd omdat er geen communicatie is tussen de formulieropslagplaats en de webtoepassing.

Dergelijke scenario&#39;s leiden vaak tot beheerproblemen en productievertragingen. Als er bijvoorbeeld een nieuwere versie van een formulier beschikbaar is in de gegevensopslagruimte, moet u het formulier op de weblaag vervangen, de webtoepassing wijzigen en het formulier opnieuw distribueren op de openbare site. Als u de webtoepassing opnieuw implementeert, kan dit leiden tot serverdowntime. Doorgaans is de serverdowntime een geplande activiteit en daarom kunnen de wijzigingen niet onmiddellijk naar de openbare site worden doorgevoerd.

AEM Forms biedt portalcomponenten die de beheerkosten en productievertragingen verminderen. Met deze componenten kunnen webontwikkelaars een Forms Portal maken en aanpassen op websites die zijn gemaakt met Adobe Experience Manager (AEM).

![ portaal van AEM Forms ](assets/aem-forms-portal.png)

Met de onderdelen van het formulierportaal kunt u de volgende functionaliteit toevoegen:

* Formulieren weergeven in aangepaste indelingen. De lay-outs Lijstweergave, Kaart en Deelvensterweergave zijn beschikbaar in het vak. U kunt uw eigen aangepaste lay-outs maken.
* Hiermee kunt u aangepaste metagegevens en aangepaste handelingen weergeven terwijl u deze aanbiedt.
* Formulieren weergeven die door de gebruikersinterface van AEM Forms zijn gepubliceerd op de publicatie-instantie waar Forms Portal-componenten worden gebruikt.
* Eindgebruikers toestaan formulieren te genereren in de indeling HTML en PDF.
* Gebruik een aangepast HTML-profiel om formulieren te genereren.
* U kunt zoeken op formulieren op basis van verschillende criteria inschakelen, zoals formuliereigenschappen, metagegevens en codes.
* Formuliergegevens verzenden naar een servlet.
* Gebruik aangepaste CSS om het uiterlijk van de portal aan te passen.
* Koppelingen naar formulieren maken.
* Hier worden concepten en verzendingen weergegeven die betrekking hebben op een adaptief formulier dat door de eindgebruiker is gemaakt.

## Beschikbare AEM Forms Portal-componenten {#available-aem-forms-portal-components}

AEM Forms verstrekt de volgende poortcomponenten uit de doos, gegroepeerd onder **de Diensten van het Document** en **Predicates van de Diensten van het Document** componentengroepen:

### Zoeken en registreren {#search-amp-lister}

Met de component Zoeken en register kunt u formulieren vanuit de formulieropslagplaats op de portalpagina weergeven en configuratieopties voor het weergeven van formulieren op basis van opgegeven criteria. U kunt hiermee ook zoekcriteria opgeven waarmee gebruikers van uw portal kunnen zoeken in de lijst met formulieren.

### Concepten en verzendingen {#drafts-amp-submissions}

In het onderdeel Zoeken en opslaan worden formulieren weergegeven die door de auteur van Forms openbaar zijn gemaakt, maar in het onderdeel Concepten en verzendingen worden formulieren weergegeven die zijn opgeslagen als concept voor het later invullen van formulieren en die zijn verzonden. Deze component verstrekt gepersonaliseerde ervaring aan om het even welke aangemelde gebruiker.

### Koppeling {#link}

Met de component Koppeling kunt u overal op de pagina een koppeling naar een formulier maken. Overweeg een scenario waarin u een trainingsprogramma aanbiedt en u wilt dat uw gebruikers een formulier indienen om zich te registreren voor de training. Op uw website hebt u de programmagegevens geplaatst. Onder de details wilt u een koppeling naar het registratieformulier opgeven. De component Link kan u helpen die koppeling te maken.

## Forms Portal Workflow {#forms-portal-workflow}

Met Forms Portal kunt u formulieren vanuit de formulieropslagplaats op uw portalpagina weergeven. U kunt hiermee ook zoekcriteria opgeven waarmee gebruikers van uw portal kunnen zoeken in de lijst met formulieren. U kunt ook de component Concepten en verzendingen gebruiken om formulieren weer te geven die zijn opgeslagen als concept voor het later invullen van formulieren en die zijn verzonden. U voert een bepaalde reeks bewerkingen uit voordat deze functies beschikbaar komen op een sitepagina. Voer de stappen in de vermelde opeenvolging uit om de componenten en respectieve functionaliteit op een plaatspagina beschikbaar te maken:

1. **laat de Poortcomponenten van Forms** toe: Uit de doos, zijn de Poortcomponenten van Forms niet beschikbaar voor gebruik. [ laat de componenten van AEM sidekick ](/help/forms/using/enabling-forms-portal-components.md) voor een pagina van AEM Sites toe.
1. **de vormen van de Lijst op een pagina (creeer Forms Portal pagina):** u kunt van vormen op zowel AEM Sites als niet-AEM pagina&#39;s van de Plaats een lijst maken. De lijst bevat formulieren die beschikbaar zijn in de publicatie-instantie. Een gebruiker kan formulieren openen en invullen. Wanneer een gebruiker een formulier opent, wordt er een nieuw exemplaar van het formulier gemaakt:

   1. **de vormen van de Lijst op een pagina van AEM Sites**: Voeg de **[Onderzoek &amp; van het Registreertoestel](../../forms/using/creating-form-portal-page.md)** component aan de pagina toe en vorm de **[Ruit van de Lijst](../../forms/using/creating-form-portal-page.md#p-list-pane-p)** in het, om vormen op een pagina van een lijst te maken. Voeg en vorm de **component van de Ruit van het 0&rbrace; Onderzoek &lbrace;aan de** Onderzoek &amp; van het Registreertoestel **toe ook om onderzoeksfunctionaliteit aan de pagina toe te voegen.** De pagina met de Poortcomponent van Forms is gekend als [ Poortpagina van Forms ](../../forms/using/creating-form-portal-page.md).

   1. **de vormen van de Lijst op een niet-AEM Sites pagina:** Gebruik [ Poortonderzoek APIs van Forms ](/help/forms/using/listing-forms-webpage-using-apis.md) aan vraag, wint, en lijstvormen op niet-AEM Sites pagina&#39;s terug.

1. **het ontwerp van de Lijst en voorgelegde vormen op een Poortpagina van Forms**: voeg en vorm de componenten Concepten &amp; van Verzending aan de Poortpagina van Forms toe. De component bevat een lijst met alle formulieren in het concept en de formulieren die al zijn verzonden.

   Om een voorgelegde adaptieve vorm toe te laten om in het voorleggingslusje te verschijnen, plaats **voorlegt actie** aan **[het Portaal van Forms Actie ](configuring-submit-actions.md) voorlegt.** U kunt ook de optie Forms Portal verzenden inschakelen. Wanneer een gebruiker het formulier verzendt, wordt het formulier toegevoegd aan het tabblad Verzending.

1. **vormt opslag voor het ontwerp en voorgelegde vormengegevens:** door gebrek, ontwerp en voorleggingsgegevens wordt opgeslagen in de AEM bewaarplaats. In een productieomgeving wordt aanbevolen geen concept- of verzonden formuliergegevens in AEM opslagplaats op te slaan. [ vorm de Poortcomponent van Forms om gegevens aan een veilige plaats ](../../forms/using/draft-submission-component.md#customizing-the-storage) op te slaan.
1. **(Facultatief) Aanpassen van de Poortcomponenten van Forms:** [ pas uw Poortpaginasjablonen van Forms ](../../forms/using/customizing-templates-forms-portal-components.md) aan om een onderscheidende verschijning aan de componenten te verstrekken.
1. **(Facultatief) voeg douanemetagegevens aan vormen toe:** [ voeg douanemetagegevens aan vormen ](../../forms/using/customizing-templates-forms-portal-components.md) toe om lijst en onderzoekservaring te verbeteren.
1. **Publish de Poortpagina van Forms:** Uw Portaalpagina van Forms is nu klaar. Publish de pagina.

## Verwante artikelen {#related-articles}

* [Forms Portal-componenten inschakelen](/help/forms/using/enabling-forms-portal-components.md)
* [Forms Portal-pagina maken](../../forms/using/creating-form-portal-page.md)
* [Formulieren op een webpagina weergeven met API&#39;s](/help/forms/using/listing-forms-webpage-using-apis.md)
* [Concepten en verzendingscomponent gebruiken](../../forms/using/draft-submission-component.md)
* [Opslag van concepten en verzonden formulieren aanpassen](../../forms/using/draft-submission-component.md#customizing-the-storage)
* [Voorbeeld voor het integreren van concepten en verzendingen in de database](integrate-draft-submission-database.md)
* [Sjablonen aanpassen voor Forms Portal-componenten](../../forms/using/customizing-templates-forms-portal-components.md)
* [Inleiding tot het publiceren van formulieren op een portal](../../forms/using/introduction-publishing-forms.md)
