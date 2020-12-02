---
title: Concepten en verzendingen
seo-title: Concepten en verzendingen
description: De concepten en de verzendingscomponent maken een lijst van vormen die in de ontwerpstaat zijn en reeds voorgelegd. U kunt de vormgeving en stijl van de component aanpassen.
seo-description: De concepten en de verzendingscomponent maken een lijst van vormen die in de ontwerpstaat zijn en reeds voorgelegd. U kunt de vormgeving en stijl van de component aanpassen.
uuid: 42c205b5-3141-4b80-85d9-dad921e223a2
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: publish
discoiquuid: ad71b423-02e1-4476-9c7c-f832cea6b0a6
docset: aem65
translation-type: tm+mt
source-git-commit: 23252989bb8649b2f0b96a58972c831257e0c5dc
workflow-type: tm+mt
source-wordcount: '776'
ht-degree: 0%

---


# Concepten en verzendingscomponent{#drafts-and-submissions-component}

In de component Concepten en verzendingen worden alle formulieren weergegeven die zich in de conceptstatus bevinden en de formulieren die al zijn verzonden. De component heeft afzonderlijke secties (tabbladen) voor concepten en verzonden formulieren. De gebruikers kunnen alleen hun concepten en verzonden formulieren bekijken.

## De component {#configuring-the-component} configureren

De component Concepten en verzendingen heeft twee tabbladen: Concepten en verzendingen.

Als u het verzenden van een adaptief formulier wilt weergeven op het verzendtabblad, stelt u de handeling **Verzenden** in op **[Forms Portal Handeling verzenden](../../forms/using/configuring-submit-actions.md). Of u schakelt** de optie Forms Portal verzenden in. Wanneer een gebruiker het formulier verzendt, wordt het formulier toegevoegd aan het tabblad Verzending.

De conceptfunctionaliteit is uit het vak ingeschakeld. Wanneer een gebruiker op een adaptief formulier **Opslaan** klikt, wordt het formulier toegevoegd aan het tabblad Concepten.

Voer de volgende stappen uit om een component Concepten en verzendingen toe te voegen en te configureren:

1. Sleep de component **Concepten en verzenden** onder de categorie Document Services in de componentenbrowser op de pagina.
1. Tik op de component en tik vervolgens op ![settings_icon](assets/settings_icon.png) om het dialoogvenster Bewerken voor de component te openen.

   ![Concepten en verzendingscomponent](assets/drafts-submissions-edit.png)

1. Geef in het dialoogvenster Bewerken de volgende gegevens op en tik op **Done** om de instellingen op te slaan.

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
   <td>Hiermee geeft u het maximale aantal resultaten op dat moet worden weergegeven. Als het aantal resultaten de Totale resultaatgrens verhoogt, verschijnt een <strong>Meer </strong>verbinding bij de bodem van de component. Als u op <strong>Meer </strong>klikt, worden alle formulieren weergegeven. </td>
  </tr>
  <tr>
   <td> </td>
   <td>Stijltype</td>
   <td>Hiermee wordt de stijl van de component opgegeven. U kunt <strong>Geen stijl</strong>, <strong>Standaardstijl</strong> of <strong>Aangepaste stijl</strong> opgeven om de formulieren weer te geven. Voor de Optie van de Stijl van de Douane, kunt u de weg van douaneCSS dossier in <strong>de Weg van de Stijl van de Douane </strong>field<strong> specificeren.</strong></td>
  </tr>
  <tr>
   <td> </td>
   <td>Pad aangepaste stijl</td>
   <td>Als u de optie <strong>Aangepaste stijl</strong> kiest in het veld <strong>Stijltype</strong>, gebruikt u het veld <strong>Aangepast stijlpad</strong> om het pad van een aangepast CSS-bestand op te geven. </td>
  </tr>
  <tr>
   <td> </td>
   <td>Weergaveopties</td>
   <td><p>Hiermee geeft u de tabbladen op die u wilt weergeven. U kunt ervoor kiezen om conceptformulieren, verzonden formulieren of beide weer te geven. </p> <p><strong>Opmerking</strong>:<em> Voor  <strong>weergaveopties</strong> wordt de optie  <strong>Standaardveld </strong>niet gebruikt als u een andere optie dan  <strong>Beide</strong>  selecteert.</em></p> </td>
  </tr>
  <tr>
   <td> </td>
   <td>Standaardtabblad</td>
   <td>Hiermee geeft u het tabblad op dat moet worden weergegeven wanneer de pagina voor het portal Formulieren wordt geladen. U kunt kiezen tussen <strong>Concept Forms Tab</strong> en <strong>Ingediend Forms Tab</strong>.</td>
  </tr>
  <tr>
   <td>Concept configuratie Forms-tabblad</td>
   <td>Aangepaste titel</td>
   <td>Geeft de titel op van het tabblad <strong>Concept Forms</strong>. De standaardwaarde is <strong>Concept Forms.</strong></td>
  </tr>
  <tr>
   <td> </td>
   <td>Lay-outsjabloon</td>
   <td>Hiermee geeft u de lay-out op die moet worden gebruikt voor de lijst Concept Forms.</td>
  </tr>
  <tr>
   <td>Ingediende Forms Tab-configuratie</td>
   <td>Aangepaste titel </td>
   <td>Geeft de titel aan van het <strong>Ingediende Forms </strong>tabblad. De standaardwaarde is <strong>Ingediende Forms.</strong></td>
  </tr>
  <tr>
   <td> </td>
   <td>Lay-outsjabloon</td>
   <td>Geeft de lay-out op die moet worden gebruikt voor de lijst Verzenden Forms<strong> </strong>. </td>
  </tr>
 </tbody>
</table>

## De opslag aanpassen {#customizing-the-storage}

Wanneer u de verzendactie Forms Portal gebruikt of de optie voor het opslaan van gegevens in het formulierportaal in een adaptieve vorm inschakelt, worden de formuliergegevens opgeslagen in AEM opslagplaats. In een productieomgeving wordt aanbevolen geen concept- of verzonden formuliergegevens in AEM opslagplaats op te slaan. In plaats daarvan moet u de concepten en verzendingscomponent integreren met een beveiligde opslag, zoals een bedrijfsdatabase, om concepten en verzonden formuliergegevens op te slaan.

Met Forms Portal kunt u gegevens opslaan in een lokale AEM, externe AEM opslagplaats of in een database. Met AEM Forms kunt u de implementatie van het opslaan van gebruikersgegevens voor concepten en verzendingen aanpassen. U kunt standaardmethoden negeren om op te geven hoe concepten en verzendgegevens worden opgeslagen bij een door u gekozen opslaglocatie. U kunt de gegevens bijvoorbeeld opslaan in een gegevensopslagruimte die momenteel in uw organisatie is geïmplementeerd.

Forms Portal biedt vanuit de boxservices (API&#39;s) voor het opslaan van gegevens in de crx-opslagruimte van lokale en externe AEM Forms-publicatie-instanties. U kunt de standaardimplementaties, die in [het Vormen van de opslagdiensten voor concepten en bijdragen](/help/forms/using/configuring-draft-submission-storage.md) artikel worden beschreven, met douaneimplementaties vervangen om standaardfunctionaliteit te vervangen. Zie [Services voor conceptgegevens en verzendgegevens aanpassen](/help/forms/using/custom-draft-submission-data-services.md) en [Aangepaste opslag voor concepten en verzendingscomponenten voor gedetailleerde informatie over de methoden die in een aangepaste implementatie worden vereist om inhoud op een beveiligde locatie op te slaan.](/help/forms/using/adding-custom-storage-provider-forms.md)

De documentatie van AEM Forms verstrekt een [Steekproef voor het integreren van concepten &amp; verzendingscomponent met gegevensbestand](integrate-draft-submission-database.md). Met de voorbeeldimplementatie kunt u uw eigen aangepaste implementatie ontwikkelen.

## Verwante artikelen

* [Formulierportonderdelen inschakelen](/help/forms/using/enabling-forms-portal-components.md)
* [Pagina Formulierportal maken](/help/forms/using/creating-form-portal-page.md)
* [Formulieren op een webpagina weergeven met API&#39;s](/help/forms/using/listing-forms-webpage-using-apis.md)
* [Concepten en verzendingscomponent gebruiken](/help/forms/using/draft-submission-component.md)
* [Opslag van concepten en verzonden formulieren aanpassen](/help/forms/using/draft-submission-component.md)
* [Voorbeeld voor het integreren van concepten en verzendingen in de database](/help/forms/using/integrate-draft-submission-database.md)
* [Sjablonen aanpassen voor componenten van een formulierportal](/help/forms/using/customizing-templates-forms-portal-components.md)
* [Inleiding tot het publiceren van formulieren op een portal](/help/forms/using/introduction-publishing-forms.md)
