---
title: Werken met de werkruimte van AEM Forms
description: Ga aan de slag met de AEM Forms-werkruimte met dit korte overzicht van de procesworkflows.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
docset: aem65
exl-id: 0bedcbd9-2cf8-47da-9440-c773982e550c
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '1019'
ht-degree: 0%

---

# Werken met de werkruimte van AEM Forms{#working-with-aem-forms-workspace}

## Inleiding {#introduction}

De AEM Forms-werkruimte maakt deel uit van AEM Forms. De werkruimte vergemakkelijkt de uitvoering van HTML Forms naast PDF forms. Nu kunt u aan bedrijfsprocessen van mobiele interfaces en Webtoepassingen in dienst nemen.

Bovendien is de AEM Forms-werkruimte in hoge mate aanpasbaar met de standaard HTML en JavaScript™-ontwikkelingsmethoden. Het is software op basis van componenten die eenvoudig kan worden geïntegreerd met andere webtoepassingen.

Zie voor meer informatie [Inleiding tot de AEM Forms-werkruimte](/help/forms/using/introduction-html-workspace.md).

## Kennis krijgen {#getting-familiar}

Om vertrouwd met het proces van begin tot eind te zijn om een vormtoepassing tot stand te brengen om een bedrijfsproces te automatiseren, volg de analyse. U kunt een toepassing maken, beheren en testen met Workbench, Designer en AEM Forms nadat u de stappen hebt uitgevoerd. Zie voor meer informatie over de implementatie [Uw eerste AEM Forms-toepassing maken](https://help.adobe.com/en_US/livecycle/11.0/CreateFirstApp/index.html).

## Functioneel overzicht {#functional-overview}

U kunt de werkruimte van AEM Forms gebruiken om de volgende taken uit te voeren:

**Een bedrijfsproces starten:** De AEM Forms-werkruimte categoriseert uw processen zoals deze door uw organisatie zijn ontworpen en ingesteld. U kunt de veelgebruikte categorieën als favoriet gebruiken om snel tot de categorieën toegang te hebben. Wanneer u een proces start, vult u doorgaans een formulier in om een bedrijfsproces te starten dat de werkstroom van formulieren beheert. Zie voor meer informatie [Processen starten](/help/forms/using/starting-processes.md).

**Taken weergeven en uitvoeren:** Wanneer u uw lijst te doen bekijkt, ziet u taken van een bedrijfsproces die aan u, of aan om het even welke groepen worden toegewezen die u tot behoort, of zijn de gedeelde taken van andere gebruikers. U kunt de taken naar wens openen, bewerken en voltooien. Het uitvoeren van een taak omvat meestal het verstrekken van informatie, het goedkeuren van een formulier of het afwijzen van een formulier. Zie voor meer informatie [Werken met to-do-lijsten](/help/forms/using/todo-lists.md).

**Taken bijhouden**: Als u uw taken wilt bijhouden, gebruikt u het tabblad Bijhouden van de AEM Forms-werkruimte. U kunt zoeken naar actieve of voltooide processen waaraan u bent begonnen of deelgenomen. U kunt de taken, toewijzingen en formulieren weergeven die deel uitmaakten van het proces. U kunt ook nieuwe processen starten met formuliergegevens uit een proces dat u eerder hebt gestart. Zie voor meer informatie [Traceringsprocessen](/help/forms/using/tracking-processes.md).

## Nieuwe AEM Forms-werkruimte {#new-offering-of-aem-forms-workspace}

**Steun voor bulkgoedkeuring van taken**:

U kunt meerdere taken van hetzelfde type goedkeuren. Zodra u één taak voor goedkeuring selecteert, slechts blijven de taken met het zelfde proces, met de zelfde taaknamen, en de zelfde routeopties toegelaten. Zie [Werken met lijsten van taken](/help/forms/using/todo-lists.md) voor details over de uitvoering.

## Migreren van Flex Workspace naar AEM Forms-werkruimte {#migrating-from-flex-workspace-to-aem-forms-workspace}

Flex Workspace wordt niet ondersteund voor AEM Forms-klanten. Alle klanten die de Flex Workspace gebruiken, moeten naar de AEM Forms Workspace gaan.

In de werkruimte van AEM Forms zijn de standaardservices voor renderen en verzenden, in het standaardactieprofiel, gewijzigd die zijn gekoppeld aan XDP-formulieren en zijn nieuwe services geïntroduceerd. Zie voor meer informatie [Nieuwe renderservice en verzendservice](/help/forms/using/new-render-submit-service.md). Als u uw bestaande processen, die werken met XDP-formulieren, wilt migreren om deze services te gebruiken, kunt u de volgende [deze stappen](new-render-submit-service.md).

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
     <li>De gebruikersinterface van de werkruimte vereenvoudigen<br /> </li>
     <li>Een nieuw aanmeldingsscherm maken</li>
     <li>Een aangepaste Goedkeuringscontainer maken</li>
    </ol> </td>
   <td>
    <ol>
     <li><a href="/help/forms/using/description-reusable-components.md">Werken met herbruikbare componenten</a></li>
     <li><a href="/help/forms/using/creating-new-login-screen.md">Aanmeldingsscherm maken</a></li>
     <li>Goedkeuringscontainer is afgekeurd.</li>
    </ol> </td>
  </tr>
 </tbody>
</table>

Enkele functies van de Flex Workspace die niet beschikbaar zijn in de AEM Forms-werkruimte zijn onder andere: berichten en meldingen, welkomstpagina, goedkeuringscontainer en optie voor het beheer van kolomkoppen. Zie voor een volledige lijst [Functies van Flex Workspace zijn niet beschikbaar in de AEM Forms-werkruimte](/help/forms/using/features-flex-workspace-available-html.md).

## Ontwikkelen met de AEM Forms-werkruimte {#developing-with-aem-forms-workspace}

### Architectuur {#architecture}

De AEM Forms-werkruimte is een op HTML en JavaScript™ gebaseerde webtoepassing die wordt gehost op CRX™. Wanneer de werkruimte-URL wordt geopend in een browser, wordt een CRX™-bron benaderd en wordt de toepassing weergegeven als een HTML-pagina in de browser. De JavaScript-bibliotheken en de aangepaste JavaScript-code beheren het interne en externe gedrag van de toepassing, zoals gebruikersinterface, gebruikersinteractie en communicatie met de AEM Forms-server. Zie de AEM Forms-werkruimte voor meer informatie [architectuur](/help/forms/using/html-workspace-architecture.md).

### AEM Forms-werkruimte aanpassen {#aem-forms-workspace-customization}

De AEM Forms-werkruimte ondersteunt een groot aantal aanpassingen waarmee de lay-out van de gebruikersinterface, de weergave, functionaliteit en nog veel meer kunnen worden bijgewerkt. Bij de aanpassingen moet u een of meer van de volgende handelingen bijwerken:

* Vormgeving van de gebruikersinterface
* Functionaliteit met semantische aanpassingen
* HTML-componenten opnieuw gebruiken in andere webtoepassingen

De [aanpassing](introduction-customizing-html-workspace.md#types-of-customizations) in artikel worden de typen van dergelijke aanpassingen uitgelegd.

### De ontwikkelomgeving instellen {#set-up-the-developer-environment}

De werkruimtematerialen van AEM Forms omvatten een CRX-pakket dat op CRX wordt opgesteld, een archief van SDK dat de volledige broncode, derdebibliotheken JavaScript bevat, en manuscripten van de werkruimte van AEM Forms bouwt. Gebruik deze opties om de ontwikkelomgeving in te stellen voor het uitvoeren van de hierboven vermelde aanpassingen. Zie voor meer informatie [AEM Forms-werkruimtecode samenstellen](introduction-customizing-html-workspace.md#building-html-workspace-code).

U kunt een groot deel van de interface en kernfunctionaliteit aanpassen, zoals lettertypen, kleurenschema, logo, aanmeldingsscherm, foutmeldingen, integratie met toepassingen van derden en hergebruik van componenten in toepassingen van derden. U kunt ook de inhoud verbeteren die op de pagina van het Overzicht van de Taak wordt getoond, beelden voor de acties van de taakroute tonen, en zelfs de laag-vlakke Modellen van de Backbone en Weergaven wijzigen die tot de de werkruimtetoepassing van AEM Forms leiden.

### HTML-rendering van XDP Forms {#html-rendering-of-xdp-forms}

Voor een nieuw proces wordt een XDP-formulier standaard weergegeven in de PDF-indeling op een bureaublad en in de HTML-indeling op een tablet. Het is mogelijk om een XDP-formulier altijd in HTML-indeling te genereren. Zie voor meer informatie [Nieuwe services renderen en verzenden](/help/forms/using/new-render-submit-service.md).

[Mobile Forms](https://helpx.adobe.com/livecycle/help/mobile-forms/introduction.html) functie, die werkt met [profielen](https://helpx.adobe.com/livecycle/help/mobile-forms/creating-profile.html), schakelt HTML-uitvoering van XDP-formulieren in. Standaard gebruikt de optie &#39;Nieuw HTML-formulier renderen&#39; `default.html` die u kunt wijzigen. U kunt ook aangepaste wijzigingen toevoegen die plaatsvinden voordat een XDP-formulier in HTML-indeling wordt weergegeven.

## AEM Forms-app voor werkruimte {#aem-forms-workspace-app}

Als u aan uw bedrijfsprocessen op een mobiel apparaat wilt werken, kunt u de AEM Forms-app voor werkruimte van AEM Forms gebruiken. Zie de klasse [Overzicht van de AEM Forms-werkruimte](https://helpx.adobe.com/livecycle/help/mobile-workspace/mobile-workspace-overview.html).
