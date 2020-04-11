---
title: Werken met de werkruimte van AEM-formulieren
seo-title: Werken met de werkruimte van AEM-formulieren
description: Ga aan de slag met de AEM Forms-werkruimte met dit korte overzicht van de procesworkflows.
seo-description: Ga aan de slag met de AEM Forms-werkruimte met dit korte overzicht van de procesworkflows.
uuid: 36381e7b-1533-459c-80de-92e806a49cd5
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: 866cd9cb-6661-4b0f-a3af-e39453e6e51b
docset: aem65
translation-type: tm+mt
source-git-commit: 56c6cfd437ef185336e81373bd5f758205b96317

---


# Werken met de werkruimte van AEM-formulieren{#working-with-aem-forms-workspace}

## Inleiding {#introduction}

De werkruimte van AEM-formulieren maakt deel uit van AEM-formulieren. De werkruimte vereenvoudigt de uitvoering van HTML-formulieren in aanvulling op PDF-formulieren. Nu kunt u aan bedrijfsprocessen van mobiele interfaces en Webtoepassingen in dienst nemen.

De werkruimte van AEM Forms is bovendien in hoge mate aanpasbaar met de standaard HTML- en JavaScript™-ontwikkelingsmethoden. Het is software op basis van componenten die eenvoudig kan worden geïntegreerd met andere webtoepassingen.

Zie [Inleiding tot de werkruimte](/help/forms/using/introduction-html-workspace.md)van AEM Forms voor meer informatie.

## Kennis krijgen {#getting-familiar}

Om vertrouwd met het proces van begin tot eind te zijn om een vormtoepassing te creëren om een bedrijfsproces te automatiseren, volg de analyse. U kunt een toepassing maken, beheren en testen met Workbench, Designer en AEM Forms werkruimte nadat u de doorlichting hebt uitgevoerd. Voor implementatiedetails, zie het [Creëren van Uw Eerste Toepassing](https://help.adobe.com/en_US/livecycle/11.0/CreateFirstApp/index.html)van Vormen AEM.

## Functioneel overzicht {#functional-overview}

U kunt de werkruimte van Vormen AEM gebruiken om de volgende taken uit te voeren:

**Een bedrijfsproces starten:** De werkruimte van de Vormen AEM categoriseert uw processen zoals ontworpen en opstelling door uw organisatie. U kunt de veelgebruikte categorieën als favoriet gebruiken om snel tot de categorieën toegang te hebben. Wanneer u een proces start, vult u doorgaans een formulier in om een bedrijfsproces te starten dat de werkstroom van formulieren beheert. Zie Processen [starten voor meer informatie](/help/forms/using/starting-processes.md).

**Taken weergeven en uitvoeren:** Wanneer u uw lijst te doen bekijkt, ziet u taken van een bedrijfsproces die aan u, of aan om het even welke groepen worden toegewezen die u tot behoort, of zijn de gedeelde taken van andere gebruikers. U kunt de taken naar wens openen, bewerken en voltooien. Het uitvoeren van een taak omvat meestal het verstrekken van informatie, het goedkeuren van een formulier of het afwijzen van een formulier. Voor meer informatie, zie het [Werken met te doen lijsten](/help/forms/using/todo-lists.md).

**Taken** bijhouden: Als u uw taken wilt bijhouden, gebruikt u het tabblad Bijhouden van de werkruimte van AEM-formulieren. U kunt zoeken naar actieve of voltooide processen waaraan u bent begonnen of deelgenomen. U kunt de taken, toewijzingen en formulieren weergeven die deel uitmaakten van het proces. U kunt ook nieuwe processen starten met formuliergegevens uit een proces dat u eerder hebt gestart. Zie [Trackingprocessen](/help/forms/using/tracking-processes.md)voor meer informatie.

## Nieuwe aanbieding voor de werkruimte van AEM-formulieren {#new-offering-of-aem-forms-workspace}

**Steun voor bulkgoedkeuring van taken**:

U kunt meerdere taken van hetzelfde type goedkeuren. Zodra u één taak voor goedkeuring selecteert, slechts blijven de taken met het zelfde proces, met de zelfde taaknamen, en de zelfde routeopties toegelaten. Zie [Werken met lijsten](/help/forms/using/todo-lists.md) van taken voor implementatiedetails.

## Migreren van Flex Workspace naar AEM Forms Workspace {#migrating-from-flex-workspace-to-aem-forms-workspace}

Flex Workspace wordt niet ondersteund voor klanten van AEM Forms. Alle klanten die de Flex-werkruimte gebruiken, moeten naar de AEM Forms Workspace gaan.

In de werkruimte van Vormen AEM, de gebrek geeft en legt de diensten, in het standaardactieprofiel, verbonden aan XDP vormen zijn veranderd en de nieuwe diensten zijn geïntroduceerd. Voor details, zie [Nieuw teruggeven en de dienst](/help/forms/using/new-render-submit-service.md)voorleggen. Als u bestaande processen die werken met XDP-formulieren wilt migreren en gebruik wilt maken van deze services, kunt u [deze stappen](/help/forms/using/new-render-submit-service.md#main-pars-faq)volgen.

**Flex Workspace-aanpassingen toewijzen aan de AEM Forms-werkruimte**

De toewijzing tussen diverse soorten aanpassingen in beide werkruimten is als volgt.

<table>
 <tbody>
  <tr>
   <td><strong>Type aanpassing </strong></td>
   <td><strong>Bedekte aanpassingen </strong></td>
   <td><strong>Overeenkomende aanpassingsscenario van de AEM-werkruimte</strong></td>
  </tr>
  <tr>
   <td>Lokalisatie aanpassen</td>
   <td>
    <ol>
     <li>Landinstelling van werkruimte wijzigen</li>
    </ol> </td>
   <td>
    <ol>
     <li><a href="/help/forms/using/changing-locale-user-interface.md">Landinstelling AEM-werkruimte voor formulieren wijzigen</a></li>
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
     <li>De gebruikersinterface van de werkruimte vereenvoudigen<br /> </li>
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

Enkele functies van de Flex-werkruimte die niet beschikbaar zijn in de werkruimte van AEM-formulieren zijn: berichten en meldingen, welkomstpagina, goedkeuringscontainer en optie voor het beheren van kolomkoppen. Voor een volledige lijst raadpleegt u de [functies van de Flex-werkruimte die niet beschikbaar zijn in de werkruimte](/help/forms/using/features-flex-workspace-available-html.md)van AEM-formulieren.

## Ontwikkelen met de werkruimte AEM Forms {#developing-with-aem-forms-workspace}

### Architectuur {#architecture}

De werkruimte van AEM-formulieren is een op HTML en JavaScript™ gebaseerde webtoepassing die wordt gehost op CRX™. Wanneer de werkruimte-URL wordt geopend in een browser, wordt een CRX™-bron benaderd en wordt de toepassing weergegeven als een HTML-pagina in de browser. De JavaScript-bibliotheken en de aangepaste JavaScript-code beheren het interne en externe gedrag van de toepassing, zoals gebruikersinterface, gebruikersinteractie en communicatie met de AEM Forms-server. Zie de [architectuur](/help/forms/using/html-workspace-architecture.md)van de AEM Forms-werkruimte voor meer informatie.

### Aanpassing van de AEM-werkruimte {#aem-forms-workspace-customization}

De werkruimte van de Vormen van AEM steunt een grote verscheidenheid van aanpassingen om de lay-out van het gebruikersinterface, zijn verschijning, functionaliteit, en veel meer bij te werken. Bij de aanpassingen moet u een of meer van de volgende handelingen bijwerken:

* Weergaven van de gebruikersinterface
* Functionaliteit met semantische aanpassingen
* HTML-componenten opnieuw gebruiken in andere webtoepassingen

In het [aanpassingsartikel](/help/forms/using/introduction-customizing-html-workspace.md#main-pars-heading-0) worden de typen van dergelijke aanpassingen uitgelegd.

### Set up the developer environment {#set-up-the-developer-environment}

Tot de te leveren items voor de AEM Forms-werkruimte behoren een CRX-pakket dat is geïmplementeerd op CRX, een SDK-archief met de volledige broncode, JavaScript-bibliotheken van derden en het samenstellen van scripts voor de AEM Forms-werkruimte. Gebruik deze opties om de ontwikkelomgeving in te stellen voor het uitvoeren van de hierboven vermelde aanpassingen. Zie De werkruimtecode [](/help/forms/using/introduction-customizing-html-workspace.md#main-pars-heading-3)van AEM-formulieren maken voor meer informatie.

U kunt een groot deel van de interface en kernfunctionaliteit aanpassen, zoals lettertypen, kleurenschema, logo, aanmeldingsscherm, foutmeldingen, integratie met toepassingen van derden en hergebruik van componenten in toepassingen van derden. U kunt ook de inhoud verbeteren die op de pagina van het Overzicht van de Taak wordt getoond, beelden voor de acties van de taakroute tonen, en zelfs de laag-vlakke Modellen en Weergaven wijzigen van de Backbone die tot de de werkruimtetoepassing van Vormen AEM leiden.

### HTML-rendering van XDP-formulieren {#html-rendering-of-xdp-forms}

Voor een nieuw proces wordt een XDP-formulier standaard weergegeven in PDF-indeling op een bureaublad en in HTML-indeling op een tablet. Het is mogelijk om een XDP-formulier altijd in HTML-indeling te genereren. Voor details, zie [Nieuw teruggeven en de Diensten](/help/forms/using/new-render-submit-service.md)voorleggen.

[Met de functie voor mobiele formulieren](https://helpx.adobe.com/livecycle/help/mobile-forms/introduction.html) , die werkt met [profielen](https://helpx.adobe.com/livecycle/help/mobile-forms/creating-profile.html), wordt HTML-uitvoering van XDP-formulieren ingeschakeld. Standaard gebruikt het bestand &#39;Nieuw HTML-formulier renderen&#39; een `default.html` profiel dat u kunt wijzigen. U kunt ook aangepaste wijzigingen toevoegen die plaatsvinden voordat een XDP-formulier in HTML-indeling wordt weergegeven.

## AEM Forms-werkruimte-app {#aem-forms-workspace-app}

Als u aan uw bedrijfsprocessen op een mobiel apparaat wilt werken, kunt u de AEM Forms-werkruimte-app van AEM Forms gebruiken. Zie het overzicht [van de](https://helpx.adobe.com/livecycle/help/mobile-workspace/mobile-workspace-overview.html)AEM Forms-werkruimte voor meer informatie.
