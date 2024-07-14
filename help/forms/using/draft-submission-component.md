---
title: Concepten en verzendingen
description: De concepten en de verzendingscomponent maken een lijst van vormen die in de ontwerpstaat zijn en reeds voorgelegd. U kunt de vormgeving en stijl van de component aanpassen.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: publish
docset: aem65
exl-id: f3f013a7-a399-4178-a901-d4a8c65ddbd3
solution: Experience Manager, Experience Manager Forms
feature: Forms Portal
role: Admin, User, Developer
source-git-commit: e821be5233fd5f6688507096790d219d25903892
workflow-type: tm+mt
source-wordcount: '744'
ht-degree: 0%

---

# Concepten en verzendingen{#drafts-and-submissions-component}

In de component Concepten en verzendingen worden alle formulieren weergegeven die zich in de conceptstatus bevinden en de formulieren die al zijn verzonden. De component heeft afzonderlijke secties (tabbladen) voor concepten en verzonden formulieren. De gebruikers kunnen alleen hun concepten en verzonden formulieren bekijken.

## De component configureren {#configuring-the-component}

De component Concepten en verzendingen heeft twee tabbladen: Concepten en verzendingen.

Om voorlegging van een adaptieve vorm toe te laten om in het voorleggingslusje te verschijnen, plaats **voorlegt actie** aan **[het Portaal van Forms Actie ](../../forms/using/configuring-submit-actions.md) voorlegt. U kunt ook** de optie Forms Portal verzenden inschakelen. Telkens wanneer een gebruiker het formulier verzendt, wordt het formulier toegevoegd aan het tabblad Verzending.

De conceptfunctionaliteit is uit het vak ingeschakeld. Wanneer een gebruiker **sparen** op een adaptieve vorm klikt, wordt de vorm toegevoegd aan de concepten tabel.

Voer de volgende stappen uit om een component Concepten en verzendingen toe te voegen en te configureren:

1. De belemmering-en-daling de **componenten van Concepten &amp; van Verzending** onder de categorie van de Diensten van het Document in componentenbrowser op uw pagina.
1. Selecteer de component en selecteer dan ![ settings_icon ](assets/settings_icon.png) om de Edit dialoog voor de component te openen.

   ![ Concepten &amp; component van de Verzending ](assets/drafts-submissions-edit.png)

1. In de Edit dialoog, specificeer de volgende details en selecteer **Gedaan** om de montages te bewaren.

<table>
 <tbody>
  <tr>
   <th>Tab</th>
   <th>Configuratie</th>
   <th>Beschrijving</th>
  </tr>
  <tr>
   <td>Algemeen</td>
   <td>Totaal resultaat</td>
   <td>Hiermee geeft u het maximale aantal resultaten op dat moet worden weergegeven. Als de telling van resultaten de Totale grens van het Resultaat verhoogt, verschijnt a <strong> Meer </strong> verbinding bij de bodem van de component. Het klikken <strong> meer </strong> toont alle vormen. </td>
  </tr>
  <tr>
   <td> </td>
   <td>Stijltype</td>
   <td>Hiermee wordt de stijl van de component opgegeven. U kunt <strong> Geen Stijl </strong> specificeren, <strong> StandaardStijl </strong>, of <strong> de Stijl van de Douane </strong> voor het van een lijst maken van de vormen. Voor de Optie van de Stijl van de Douane, kunt u de weg van douaneCSS dossier op het </strong> gebied van de Weg van de Stijl 0} specificeren <strong>.</strong><strong></td>
  </tr>
  <tr>
   <td> </td>
   <td>Pad aangepaste stijl</td>
   <td>Als u </strong> optie van de Stijl van 0} Douane op het <strong> 3} gebied van het Type van Stijl {kiest, gebruik het <strong> Pad van de Stijl van de Douane </strong> gebied om de weg van douaneCSS dossier te specificeren.<strong></strong> </td>
  </tr>
  <tr>
   <td> </td>
   <td>Weergaveopties</td>
   <td><p>Hiermee geeft u de tabbladen op die u wilt weergeven. U kunt ervoor kiezen om conceptformulieren, verzonden formulieren of beide weer te geven. </p> <p><strong> Nota </strong>:<em> voor <strong> de opties van de Vertoning </strong>, als u een optie buiten <strong> allebei </strong> selecteert, wordt de <strong> StandaardOptie van het Lusje </strong> gebied niet gebruikt.</em></p> </td>
  </tr>
  <tr>
   <td> </td>
   <td>Standaardtabblad</td>
   <td>Hiermee geeft u het tabblad op dat moet worden weergegeven wanneer de pagina voor het portal Formulieren wordt geladen. U kunt tussen <strong> het Lusje van Forms van het Ontwerp </strong> en <strong> Voorgelegde Lusje van Forms kiezen </strong>.</td>
  </tr>
  <tr>
   <td>Concept configuratie Forms-tabblad</td>
   <td>Aangepaste titel</td>
   <td>Specificeert titel van het <strong> Ontwerp Forms </strong> tabel. De standaardwaarde is <strong> Ontwerp Forms.</strong></td>
  </tr>
  <tr>
   <td> </td>
   <td>Lay-outsjabloon</td>
   <td>Hiermee geeft u de lay-out op die moet worden gebruikt voor de lijst Concept Forms.</td>
  </tr>
  <tr>
   <td>Ingediende Forms Tab-configuratie</td>
   <td>Aangepaste titel </td>
   <td>Specificeert titel van <strong> Voorgelegde Forms </strong> tabel. De standaardwaarde is <strong> Voorgelegde Forms.</strong></td>
  </tr>
  <tr>
   <td> </td>
   <td>Lay-outsjabloon</td>
   <td>Specificeert de lay-out voor Voorgelegde Forms <strong> </strong> lijst te gebruiken. </td>
  </tr>
 </tbody>
</table>

## De opslag aanpassen {#customizing-the-storage}

Wanneer u de verzendactie Forms Portal gebruikt of de optie voor het opslaan van gegevens in het formulierportaal in een adaptieve vorm inschakelt, worden de formuliergegevens opgeslagen in AEM opslagplaats. In een productieomgeving wordt aanbevolen geen concept- of verzonden formuliergegevens in AEM opslagplaats op te slaan. In plaats daarvan moet u de concepten en verzendingscomponent integreren met een beveiligde opslag, zoals een bedrijfsdatabase, om concepten en verzonden formuliergegevens op te slaan.

Met Forms Portal kunt u gegevens opslaan in een lokale AEM opslagplaats, een externe AEM opslagplaats of een database. Met AEM Forms kunt u de implementatie van het opslaan van gebruikersgegevens voor concepten en verzendingen aanpassen. U kunt standaardmethoden negeren om op te geven hoe concepten en verzendgegevens worden opgeslagen bij een door u gekozen opslaglocatie. U kunt de gegevens bijvoorbeeld opslaan in een gegevensopslagruimte die momenteel in uw organisatie is geïmplementeerd.

Forms Portal biedt vanuit de boxservices (API&#39;s) voor het opslaan van gegevens in de crx-opslagruimte van lokale en externe AEM Forms-publicatie-instanties. U kunt de standaardimplementaties vervangen, die in [ worden beschreven het Vormen de opslagdiensten voor concepten en voorlegging ](/help/forms/using/configuring-draft-submission-storage.md) artikel, met douaneimplementaties worden beschreven om standaardfunctionaliteit te vervangen. Voor gedetailleerde informatie over de methodes die in een douaneimplementatie worden vereist om inhoud op een beveiligde plaats op te slaan, zie [ Aanpassen van de diensten van het Ontwerp en van de Gegevens van de Verzending ](/help/forms/using/custom-draft-submission-data-services.md) en [ de opslag van de Douane voor concepten en verzendingscomponent.](/help/forms/using/adding-custom-storage-provider-forms.md)

De documentatie van AEM Forms verstrekt a [ Steekproef voor het integreren van concepten &amp; verzendingscomponent met gegevensbestand ](integrate-draft-submission-database.md). Met de voorbeeldimplementatie kunt u uw eigen aangepaste implementatie ontwikkelen.

## Verwante artikelen

* [Formulierportonderdelen inschakelen](/help/forms/using/enabling-forms-portal-components.md)
* [Pagina Formulierportal maken](/help/forms/using/creating-form-portal-page.md)
* [Formulieren op een webpagina weergeven met API&#39;s](/help/forms/using/listing-forms-webpage-using-apis.md)
* [Concepten en verzendingscomponent gebruiken](/help/forms/using/draft-submission-component.md)
* [Opslag van concepten en verzonden formulieren aanpassen](/help/forms/using/draft-submission-component.md)
* [Voorbeeld voor het integreren van concepten en verzendingen in de database](/help/forms/using/integrate-draft-submission-database.md)
* [Sjablonen aanpassen voor componenten van een formulierportal](/help/forms/using/customizing-templates-forms-portal-components.md)
* [Inleiding tot het publiceren van formulieren op een portal](/help/forms/using/introduction-publishing-forms.md)
