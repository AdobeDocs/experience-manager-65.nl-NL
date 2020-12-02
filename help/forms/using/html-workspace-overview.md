---
title: Werken met de werkruimte van AEM Forms
seo-title: Werken met de werkruimte van AEM Forms
description: Ga aan de slag met de AEM Forms-werkruimte met dit korte overzicht van de procesworkflows.
seo-description: Ga aan de slag met de AEM Forms-werkruimte met dit korte overzicht van de procesworkflows.
uuid: 36381e7b-1533-459c-80de-92e806a49cd5
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: 866cd9cb-6661-4b0f-a3af-e39453e6e51b
docset: aem65
translation-type: tm+mt
source-git-commit: 21efe30c6a69d04c737bc523aeaab504db8f605b
workflow-type: tm+mt
source-wordcount: '1062'
ht-degree: 0%

---


# Werken met de AEM Forms-werkruimte{#working-with-aem-forms-workspace}

## Inleiding {#introduction}

De AEM Forms-werkruimte maakt deel uit van AEM Forms. De werkruimte vergemakkelijkt de uitvoering van HTML Forms naast PDF forms. Nu kunt u aan bedrijfsprocessen van mobiele interfaces en Webtoepassingen in dienst nemen.

Bovendien is de AEM Forms-werkruimte in hoge mate aanpasbaar met de standaard HTML- en JavaScript™-ontwikkelingsmethoden. Het is software op basis van componenten die eenvoudig kan worden geïntegreerd met andere webtoepassingen.

Zie [Inleiding tot de AEM Forms-werkruimte](/help/forms/using/introduction-html-workspace.md) voor meer informatie.

## {#getting-familiar} vertrouwd maken

Om vertrouwd met het proces van begin tot eind te zijn om een vormtoepassing te creëren om een bedrijfsproces te automatiseren, volg de analyse. U kunt een toepassing maken, beheren en testen met Workbench, Designer en AEM Forms nadat u de stappen hebt uitgevoerd. Voor implementatiedetails, zie [Creërend Uw Eerste Toepassing van AEM Forms](https://help.adobe.com/en_US/livecycle/11.0/CreateFirstApp/index.html).

## Functioneel overzicht {#functional-overview}

U kunt de werkruimte van AEM Forms gebruiken om de volgende taken uit te voeren:

**Start een bedrijfsproces:** AEM Forms-werkruimte categoriseert uw processen zoals deze door uw organisatie zijn ontworpen en ingesteld. U kunt de veelgebruikte categorieën als favoriet gebruiken om snel tot de categorieën toegang te hebben. Wanneer u een proces start, vult u doorgaans een formulier in om een bedrijfsproces te starten dat de werkstroom van formulieren beheert. Zie [Processen starten](/help/forms/using/starting-processes.md) voor meer informatie.

**De mening en handelt op taken:** Wanneer u uw te doen lijsten bekijkt, ziet u taken van een bedrijfsproces die aan u, of aan om het even welke groepen worden toegewezen die u tot behoort, of zijn de gedeelde taken van andere gebruikers. U kunt de taken naar wens openen, bewerken en voltooien. Het uitvoeren van een taak omvat meestal het verstrekken van informatie, het goedkeuren van een formulier of het afwijzen van een formulier. Voor meer informatie, zie [Werken met lijsten ](/help/forms/using/todo-lists.md).

**Taken** bijhouden: Als u uw taken wilt bijhouden, gebruikt u het tabblad Bijhouden van de AEM Forms-werkruimte. U kunt zoeken naar actieve of voltooide processen waaraan u bent begonnen of deelgenomen. U kunt de taken, toewijzingen en formulieren weergeven die deel uitmaakten van het proces. U kunt ook nieuwe processen starten met formuliergegevens uit een proces dat u eerder hebt gestart. Zie [Processen bijhouden](/help/forms/using/tracking-processes.md) voor meer informatie.

## Nieuwe aanbieding van de werkruimte van AEM Forms {#new-offering-of-aem-forms-workspace}

**Steun voor bulkgoedkeuring van taken**:

U kunt meerdere taken van hetzelfde type goedkeuren. Zodra u één taak voor goedkeuring selecteert, slechts blijven de taken met het zelfde proces, met de zelfde taaknamen, en de zelfde routeopties toegelaten. Zie [Werken met lijsten van taken](/help/forms/using/todo-lists.md) voor implementatiedetails.

## Migreren van Flex Workspace naar AEM Forms-werkruimte {#migrating-from-flex-workspace-to-aem-forms-workspace}

Flex Workspace wordt niet ondersteund voor AEM Forms-klanten. Alle klanten die de Flex Workspace gebruiken, moeten naar de AEM Forms Workspace gaan.

In de werkruimte van AEM Forms zijn de standaardservices voor renderen en verzenden, in het standaardactieprofiel, gewijzigd die zijn gekoppeld aan XDP-formulieren en zijn nieuwe services geïntroduceerd. Zie [Nieuwe renderservice en verzendservice](/help/forms/using/new-render-submit-service.md) voor meer informatie. Als u uw bestaande processen, die werken met XDP-formulieren, wilt migreren om van deze services gebruik te maken, kunt u [deze stappen](new-render-submit-service.md) volgen.

**Flex Workspace-aanpassingen toewijzen met de AEM Forms-werkruimte**

De toewijzing tussen diverse soorten aanpassingen in beide werkruimten is als volgt.

<table>
 <tbody>
  <tr>
   <td><strong>Type aanpassing </strong></td>
   <td><strong>Bedekte aanpassingen </strong></td>
   <td><strong>Overeenkomende AEM Forms-workspace-aanpassingsscenario</strong></td>
  </tr>
  <tr>
   <td>Lokalisatie aanpassen</td>
   <td>
    <ol>
     <li>Landinstelling van werkruimte wijzigen</li>
    </ol> </td>
   <td>
    <ol>
     <li><a href="/help/forms/using/changing-locale-user-interface.md">Landinstelling van AEM Forms-werkruimte wijzigen</a></li>
    </ol> </td>
  </tr>
  <tr>
   <td>Aanpassing thema</td>
   <td>
    <ol>
     <li>Afbeeldingen vervangen</li>
     <li>Kleuren wijzigen</li>
    </ol> </td>
   <td>
    <ol>
     <li><a href="/help/forms/using/changing-organization-logo-branding.md">Organisatie-logo wijzigen</a> </li>
     <li><a href="/help/forms/using/changing-color-scheme-interface.md">Kleurenschema wijzigen</a></li>
    </ol> </td>
  </tr>
  <tr>
   <td>Layout aanpassen</td>
   <td>
    <ol>
     <li>Het vereenvoudigen van het gebruikersinterface van de Werkruimte<br /> </li>
     <li>Een nieuw aanmeldingsscherm maken</li>
     <li>Een aangepaste goedkeuringscontainer maken</li>
    </ol> </td>
   <td>
    <ol>
     <li><a href="/help/forms/using/description-reusable-components.md">Werken met herbruikbare componenten</a></li>
     <li><a href="/help/forms/using/creating-new-login-screen.md">Een nieuw aanmeldingsscherm maken</a></li>
     <li>Goedkeuringscontainer is afgekeurd.</li>
    </ol> </td>
  </tr>
 </tbody>
</table>

Enkele functies van de Flex Workspace die niet beschikbaar zijn in de AEM Forms-werkruimte zijn onder andere: berichten en meldingen, welkomstpagina, goedkeuringscontainer en optie voor het beheren van kolomkoppen. Zie [Functies van Flex Workspace niet beschikbaar in de AEM Forms-werkruimte](/help/forms/using/features-flex-workspace-available-html.md) voor een complete lijst.

## Ontwikkelen met AEM Forms-werkruimte {#developing-with-aem-forms-workspace}

### Architectuur {#architecture}

De AEM Forms-werkruimte is een op HTML en JavaScript™ gebaseerde webtoepassing die wordt gehost op CRX™. Wanneer de werkruimte-URL wordt geopend in een browser, wordt een CRX™-bron benaderd en wordt de toepassing weergegeven als een HTML-pagina in de browser. De JavaScript-bibliotheken en de aangepaste JavaScript-code beheren het interne en externe gedrag van de toepassing, zoals gebruikersinterface, gebruikersinteractie en communicatie met de AEM Forms-server. Zie de AEM Forms-werkruimte [architectuur](/help/forms/using/html-workspace-architecture.md) voor meer informatie.

### AEM Forms-werkruimte aanpassen {#aem-forms-workspace-customization}

De AEM Forms-werkruimte ondersteunt een groot aantal aanpassingen waarmee de lay-out van de gebruikersinterface, de weergave, functionaliteit en nog veel meer kunnen worden bijgewerkt. Bij de aanpassingen moet u een of meer van de volgende handelingen bijwerken:

* Weergaven van de gebruikersinterface
* Functionaliteit met semantische aanpassingen
* HTML-componenten opnieuw gebruiken in andere webtoepassingen

In het artikel [customization](introduction-customizing-html-workspace.md#types-of-customizations) worden de typen van dergelijke aanpassingen uitgelegd.

### De ontwikkelomgeving instellen {#set-up-the-developer-environment}

De werkruimtematerialen van AEM Forms omvatten een CRX-pakket dat op CRX wordt opgesteld, een archief van SDK dat de volledige broncode, derdebibliotheken JavaScript bevat, en manuscripten van de werkruimte van AEM Forms bouwt. Gebruik deze opties om de ontwikkelomgeving in te stellen voor het uitvoeren van de hierboven vermelde aanpassingen. Zie [AEM Forms-werkruimtecode maken](introduction-customizing-html-workspace.md#building-html-workspace-code) voor meer informatie.

U kunt een groot deel van de interface en kernfunctionaliteit aanpassen, zoals lettertypen, kleurenschema, logo, aanmeldingsscherm, foutmeldingen, integratie met toepassingen van derden en hergebruik van componenten in toepassingen van derden. U kunt ook de inhoud verbeteren die op de pagina van het Overzicht van de Taak wordt getoond, beelden voor de acties van de taakroute tonen, en zelfs de laag-vlakke Modellen van de Backbone en Weergaven wijzigen die tot de de werkruimtetoepassing van AEM Forms leiden.

### HTML-rendering van XDP Forms {#html-rendering-of-xdp-forms}

Voor een nieuw proces wordt een XDP-formulier standaard weergegeven in PDF-indeling op een bureaublad en in HTML-indeling op een tablet. Het is mogelijk om een XDP-formulier altijd in HTML-indeling te genereren. Zie [Nieuwe services renderen en verzenden](/help/forms/using/new-render-submit-service.md) voor meer informatie.

[Met de functie Mobiele ](https://helpx.adobe.com/livecycle/help/mobile-forms/introduction.html) formaten, die werkt met  [profielen](https://helpx.adobe.com/livecycle/help/mobile-forms/creating-profile.html), wordt HTML-uitvoering van XDP-formulieren ingeschakeld. Standaard gebruikt het profiel &#39;Nieuw HTML-formulier renderen&#39; het profiel `default.html`, dat u kunt wijzigen. U kunt ook aangepaste wijzigingen toevoegen die plaatsvinden voordat een XDP-formulier in HTML-indeling wordt weergegeven.

## AEM Forms-werkruimte-app {#aem-forms-workspace-app}

Als u aan uw bedrijfsprocessen op een mobiel apparaat wilt werken, kunt u de AEM Forms-app voor werkruimte van AEM Forms gebruiken. Zie [Overzicht van de AEM Forms-werkruimte app](https://helpx.adobe.com/livecycle/help/mobile-workspace/mobile-workspace-overview.html) voor meer informatie.
