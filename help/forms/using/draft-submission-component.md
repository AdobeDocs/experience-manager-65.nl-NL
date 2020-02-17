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

---


# Concepten en verzendingen{#drafts-and-submissions-component}

In de component Concepten en verzendingen worden alle formulieren weergegeven die zich in de conceptstatus bevinden en de formulieren die al zijn verzonden. De component heeft afzonderlijke secties (tabbladen) voor concepten en verzonden formulieren. De gebruikers kunnen alleen hun concepten en verzonden formulieren bekijken.

## De component configureren {#configuring-the-component}

De component Concepten en verzendingen heeft twee tabbladen: Concepten en verzendingen.

Als u het verzenden van een adaptief formulier wilt weergeven op het tabblad Verzending, stelt u de handeling **** Verzenden in op **[Forms Portal Handeling](../../forms/using/configuring-submit-actions.md)verzenden. U kunt ook **de optie Formulierportal verzenden inschakelen. Wanneer een gebruiker het formulier verzendt, wordt het formulier toegevoegd aan het tabblad Verzending.

De conceptfunctionaliteit is uit het vak ingeschakeld. Wanneer een gebruiker op een adaptief formulier op **Opslaan** klikt, wordt het formulier toegevoegd aan het tabblad Concepten.

Voer de volgende stappen uit om een component Concepten en verzendingen toe te voegen en te configureren:

1. Sleep de component **Concepten en verzendingen** onder de categorie Document Services in de componentenbrowser op de pagina.
1. Tik op de component en tik vervolgens op ![settings_icon](assets/settings_icon.png) om het dialoogvenster Bewerken voor de component te openen.

   ![Concepten en verzendingscomponent](assets/drafts-submissions-edit.png)

1. Geef in het dialoogvenster Bewerken de volgende gegevens op en tik op **Gereed** om de instellingen op te slaan.

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
   <td>Hiermee geeft u het maximale aantal resultaten op dat moet worden weergegeven. Als het aantal resultaten de maximale totale resultaten verhoogt, wordt onder aan de component een <strong>meer </strong>koppeling weergegeven. Klik op <strong>Meer om alle formulieren </strong>weer te geven. </td>
  </tr>
  <tr>
   <td> </td>
   <td>Stijltype</td>
   <td>Hiermee wordt de stijl van de component opgegeven. U kunt <strong>Geen stijl</strong>, <strong>Standaardstijl</strong>of <strong>Aangepaste stijl</strong> opgeven voor het weergeven van de formulieren. Bij de optie Aangepaste stijl kunt u het pad van een aangepast CSS-bestand opgeven in het <strong>veld </strong><strong>Aangepast stijlpad.</strong></td>
  </tr>
  <tr>
   <td> </td>
   <td>Pad aangepaste stijl</td>
   <td>Als u de optie <strong>Aangepaste stijl</strong> kiest in het veld <strong>Stijltype</strong> , gebruikt u het veld <strong>Aangepast stijlpad</strong> om het pad van een aangepast CSS-bestand op te geven. </td>
  </tr>
  <tr>
   <td> </td>
   <td>Weergaveopties</td>
   <td><p>Hiermee geeft u de tabbladen op die u wilt weergeven. U kunt ervoor kiezen om conceptformulieren, verzonden formulieren of beide weer te geven. </p> <p><strong></strong> Opmerking<em>: Als u voor <strong>weergaveopties</strong>een andere optie dan <strong>Beide</strong>selecteert, wordt de optie <strong>Standaardtabblad</strong> niet gebruikt.</em></p> </td>
  </tr>
  <tr>
   <td> </td>
   <td>Standaardtabblad</td>
   <td>Hiermee geeft u het tabblad op dat moet worden weergegeven wanneer de pagina voor het portal Formulieren wordt geladen. U kunt kiezen tussen het tabblad <strong>Formulieren</strong> in concept en het tabblad <strong>Formulieren</strong>in verzending.</td>
  </tr>
  <tr>
   <td>Configuratie van tabblad Conceptformulieren</td>
   <td>Aangepaste titel</td>
   <td>Hiermee geeft u de titel op van het tabblad <strong>Conceptformulieren</strong> . De standaardwaarde is <strong>Conceptformulieren.</strong></td>
  </tr>
  <tr>
   <td> </td>
   <td>Lay-outsjabloon</td>
   <td>Hiermee geeft u de indeling op die u wilt gebruiken voor de lijst Conceptformulieren.</td>
  </tr>
  <tr>
   <td>Tabconfiguratie verzonden formulieren</td>
   <td>Aangepaste titel </td>
   <td>Hiermee geeft u de titel op van het <strong>tabblad </strong>Ingediende formulieren. De standaardwaarde is <strong>Verzendformulieren.</strong></td>
  </tr>
  <tr>
   <td> </td>
   <td>Lay-outsjabloon</td>
   <td>Hiermee geeft u de indeling op die u wilt gebruiken voor de<strong> lijst Verzendformulieren </strong>. </td>
  </tr>
 </tbody>
</table>

## De opslag aanpassen {#customizing-the-storage}

Wanneer u de verzendactie Formulierportaal gebruikt of de optie Gegevens opslaan in formulierportaal in adaptieve vorm inschakelt, worden de formuliergegevens opgeslagen in de AEM-opslagruimte. In een productieomgeving wordt aanbevolen geen concept- of verzonden formuliergegevens op te slaan in een AEM-opslagplaats. In plaats daarvan moet u de concepten en verzendingscomponent integreren met een beveiligde opslag, zoals een bedrijfsdatabase, om concepten en verzonden formuliergegevens op te slaan.

Met Forms Portal kunt u gegevens opslaan in een lokale AEM-opslagruimte, een externe AEM-opslagruimte of een database. Met AEM Forms kunt u de implementatie aanpassen van het opslaan van gebruikersgegevens voor concepten en verzendingen. U kunt standaardmethoden negeren om op te geven hoe concepten en verzendgegevens worden opgeslagen bij een door u gekozen opslaglocatie. U kunt de gegevens bijvoorbeeld opslaan in een gegevensopslagruimte die momenteel in uw organisatie is geïmplementeerd.

Forms Portal biedt vanuit de boxservices (API&#39;s) gegevens op in de crx-opslagruimte van lokale en externe AEM Forms-publicatieexemplaren. U kunt de standaardimplementaties, die in het [Vormen van de opslagdiensten voor concepten en voorleggingsartikel worden beschreven, met douaneimplementaties vervangen om standaardfunctionaliteit te vervangen](/help/forms/using/configuring-draft-submission-storage.md) . Voor gedetailleerde informatie over de methodes die in een douaneimplementatie worden vereist om inhoud op een beveiligde plaats op te slaan, zie het [Aanpassen van de Diensten](/help/forms/using/custom-draft-submission-data-services.md) van de Gegevens van het Ontwerp en van de Verzending en de Opslag van de [Douane voor concepten en verzendingscomponent.](/help/forms/using/adding-custom-storage-provider-forms.md)

De documentatie van de Vormen AEM verstrekt een [Steekproef voor het integreren van concepten &amp; verzendingscomponent met gegevensbestand](integrate-draft-submission-database.md). Met de voorbeeldimplementatie kunt u uw eigen aangepaste implementatie ontwikkelen.

## Verwante artikelen

* [Formulierportonderdelen inschakelen](/help/forms/using/enabling-forms-portal-components.md)
* [Pagina Formulierportal maken](/help/forms/using/creating-form-portal-page.md)
* [Formulieren op een webpagina weergeven met API&#39;s](/help/forms/using/listing-forms-webpage-using-apis.md)
* [Concepten en verzendingscomponent gebruiken](/help/forms/using/draft-submission-component.md)
* [Opslag van concepten en verzonden formulieren aanpassen](/help/forms/using/draft-submission-component.md)
* [Voorbeeld voor het integreren van concepten en verzendingen in de database](/help/forms/using/integrate-draft-submission-database.md)
* [Sjablonen aanpassen voor componenten van een formulierportal](/help/forms/using/customizing-templates-forms-portal-components.md)
* [Inleiding tot het publiceren van formulieren op een portal](/help/forms/using/introduction-publishing-forms.md)
