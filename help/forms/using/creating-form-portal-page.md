---
title: Een pagina met een portal voor formulieren maken
description: Forms Portal beschikt over componenten waarmee webontwikkelaars een formulierportal kunnen maken en aanpassen op websites die zijn gemaakt met Adobe Experience Manager (AEM).
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: publish
docset: aem65
feature: Forms Portal
exl-id: 22d7c24e-7a77-4324-afdf-74c1fbf15773
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1655'
ht-degree: 0%

---

# Een pagina met een portal voor formulieren maken{#creating-a-forms-portal-page}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/configure-forms-portal.html) |
| AEM 6,5 | Dit artikel |

Met Forms Portal-componenten kunnen webontwikkelaars componenten gebruiken voor het maken en aanpassen van een formulierportal op websites die zijn ontworpen met Adobe Experience Manager (AEM). Voor een snel overzicht van het formulierportaal raadpleegt u [Inleiding tot het publiceren van formulieren op een portal](../../forms/using/introduction-publishing-forms.md).

## Vereisten {#prerequisites}

Forms Portal-componenten zijn niet standaard beschikbaar voor gebruik. Zorg ervoor dat de volgende categorieën van componenten van het formulierportal zijn ingeschakeld, zoals beschreven in [portalcomponenten voor formulieren inschakelen](/help/forms/using/enabling-forms-portal-components.md).

**Document Services** Omvat Onderzoek &amp; van de Registratie, Verbinding, en de componenten van Concepten en van Verzending.

**Voorspellingen voor documentservices** Bevat de componenten Datumvoorspelling, Volledig voorspeld van tekst, Voorspelde eigenschappen en Voorspelde labels. Deze componenten worden gebruikt om onderzoek in het Onderzoek &amp; component van de Registratie te vormen.

Zodra zij op een AEM plaatspagina worden toegelaten, zijn deze componentencategorieën beschikbaar voor gebruik in componentenbrowser.

![AEM Forms-portalcomponenten in componentbrowser](assets/component-categories.png)

Componentcategorieën van Forms Portal

## Zoeken &amp; listercomponent {#search-amp-lister-component}

De component Search &amp; Lister, beschikbaar onder de componentencategorie van de Diensten van het Document, wordt gebruikt om vormen op een pagina een lijst te maken en onderzoek op de vermelde vormen uit te voeren. De component bevat twee deelvensters:

* Het deelvenster Lijst waarin de formulieren worden weergegeven.
* Het paneel van het onderzoek waar u de onderzoeksfunctionaliteit toevoegt.

U kunt de component Search &amp; Lister van de de componentencategorie van de Diensten van het Document in componentenbrowser op de pagina slepen. Wanneer de component wordt toegevoegd, ziet deze er ongeveer als volgt uit.

![Component zoeken en labelen op een pagina](assets/fp-grid-viw.png)

Component zoeken en labelen op een pagina met rasterlay-out

### Lijstvenster {#list-pane}

Het deelvenster Lijst is een gebied waarin uw formulieren worden weergegeven. De component Zoeken en register bevat verschillende configuratieopties waarmee u de weergave van formulieren in het deelvenster Lijst kunt bepalen.

Om de ruit van de Lijst te vormen, selecteer de component van het Onderzoek en van de Registratie en selecteer dan ![settings_icon](assets/settings_icon.png). De **[!UICONTROL  Edit Component]** wordt geopend.

![Het deelvenster Lijst in de bewerkingsmodus](assets/edit-list.png)

Het deelvenster Lijst in de bewerkingsmodus

De **Bewerken** bevat verschillende tabbladen met configuratieopties die in de onderstaande tabel worden beschreven. Selecteren **OK** om de configuratie te bewaren, wanneer gedaan.

<table>
 <tbody>
  <tr>
   <th>Tab</th>
   <th>Configuratie</th>
   <th>Beschrijving</th>
  </tr>
  <tr>
   <td><span class="uicontrol"><strong>Elementmappen</strong></code></td>
   <td>Item toevoegen</td>
   <td>Hiermee configureert u de mappen waarin elementen worden geüpload met de gebruikersinterface van AEM Forms. Standaard worden alle geüploade elementen weergegeven. Voor meer informatie over de gebruikersinterface van AEM Forms raadpleegt u <a href="../../forms/using/introduction-managing-forms.md" target="_blank">Inleiding tot het beheren van formulieren</a>.</td>
  </tr>
  <tr>
   <td><p><span class="uicontrol"><strong>Weergave</strong></code></p> </td>
   <td>Titeltekst</td>
   <td>Titel voor de component Search &amp; Lister. De standaardtitel is <strong>Forms Portal.</strong></td>
  </tr>
  <tr>
   <td> </td>
   <td>Lay-outsjabloon</td>
   <td>Layout van de elementen. </td>
  </tr>
  <tr>
   <td> </td>
   <td>Geavanceerd zoeken uitschakelen</td>
   <td>Als deze optie is ingeschakeld, wordt het geavanceerde zoekpictogram verborgen.</td>
  </tr>
  <tr>
   <td> </td>
   <td>Tekst zoeken uitschakelen</td>
   <td>Als deze optie is ingeschakeld, wordt de zoekbalk met volledige tekst verborgen.</td>
  </tr>
  <tr>
   <td><span class="uicontrol"><strong>Resultaat</strong></code></td>
   <td>Aantal resultaten per pagina</td>
   <td>Hiermee configureert u het maximumaantal formulieren dat u op een pagina wilt weergeven.</td>
  </tr>
  <tr>
   <td> </td>
   <td>Resultaattekst</td>
   <td><p>Vormt de resultaattekst (bijvoorbeeld, 1-12 van 601) <strong>Resultaten</strong>). De standaardwaarde is <strong>Resultaten</strong>.</p> <p>Als u bijvoorbeeld <strong>Forms </strong>in dit veld en er zijn in totaal 601 formulieren, verandert de resultaattekst in 1-12 van 601 <strong>Forms.</strong></p> </td>
  </tr>
  <tr>
   <td> </td>
   <td>Paginatype</td>
   <td><p>Vormt de paginatekst (bijvoorbeeld <strong>Pagina </strong>1 van 51). De standaardwaarde is <strong>Pagina</strong>.</p> <p>Als u bijvoorbeeld <strong>Toepassingsformulier </strong>in dit veld en er zijn 51 pagina's, verandert de paginatekst in <strong>Toepassingsformulier </strong>1 van 51.</p> </td>
  </tr>
  <tr>
   <td> </td>
   <td>Van tekst</td>
   <td><p>Hiermee vervangt u het woord <strong>van</strong> met de opgegeven tekst (pagina 1 <strong>van </strong>51). De standaardwaarde is <strong>van</strong>.</p> <p>Als u bijvoorbeeld <strong>van </strong>in dit veld wordt de tekst gewijzigd in Pagina 1 <strong>van </strong>51.</p> </td>
  </tr>
  <tr>
   <td><span class="uicontrol"><strong>Formulierkoppeling</strong></code></td>
   <td>Rendertype</td>
   <td>Bepaalt het overzicht met formulieren op basis van het opgegeven rendertype. De beschikbare opties zijn PDF en HTML. Als u bijvoorbeeld alleen HTML selecteert als rendertype, worden de PDF forms uitgefilterd.</td>
  </tr>
  <tr>
   <td> </td>
   <td>HTML-profiel</td>
   <td>Configureert het HTML-profiel dat voor rendering moet worden gebruikt. Alle beschikbare profielen worden vermeld in de vervolgkeuzelijst.</td>
  </tr>
  <tr>
   <td> </td>
   <td>URL verzenden</td>
   <td><p>Vormt een servlet waar de vormgegevens worden voorgelegd.</p> <p><strong>Opmerking:</strong> <em>De verzendURL voor een formulier kan op verschillende plaatsen worden opgegeven en de prioriteitsvolgorde is als volgt:</em></p>
    <ol>
     <li><em>VerzendURL die is ingesloten in het formulier (in de knop Verzenden) heeft de hoogste prioriteit.</em></li>
     <li><em>VerzendURL die wordt vermeld in de gebruikersinterface van AEM Forms heeft de op een na hoogste prioriteit.</em></li>
     <li><em>De laagste prioriteit voor het verzenden van een URL die in het formulierportaal wordt vermeld.</em></li>
    </ol> </td>
  </tr>
  <tr>
   <td> </td>
   <td>Knopinfo voor HTML renderen</td>
   <td>Hiermee configureert u de tekst voor de knopinfo, die wordt weergegeven wanneer u de aanwijzer op de knopinfo plaatst <img height="16" src="assets/aem6forms_panel-html.png" width="13" /> (het pictogram HTML5).</td>
  </tr>
  <tr>
   <td> </td>
   <td>Knopinfo voor PDF renderen</td>
   <td>Hiermee configureert u de tekst voor de knopinfo, die wordt weergegeven wanneer u de aanwijzer op de knopinfo plaatst <img height="16" src="assets/aem6forms_panel-pdf.png" width="14" /> (het PDF-pictogram).</td>
  </tr>
  <tr>
   <td><span class="uicontrol"><strong>Stijl</strong></code></td>
   <td>Stijltype</td>
   <td>Hier kunt u opgeven <strong>Geen stijl, standaardstijl</strong>, of <strong>Aangepaste stijl </strong>voor het weergeven van de formulieren.</td>
  </tr>
  <tr>
   <td> </td>
   <td>Pad aangepaste stijl</td>
   <td>Als u Aangepast hebt geselecteerd als Stijltype, bladert u naar het pad naar de aangepaste CSS, anders selecteert u Standaard.</td>
  </tr>
 </tbody>
</table>

### Zoekvenster {#search-pane}

In het deelvenster Zoeken kunt u de componenten Datumvoorspelling, Volledig voorspelling van tekst, Voorspelling van eigenschappen en Voorspelcode toevoegen uit de categorie Voorspelingen documentservices in AEM Sidekick. Met deze componenten wordt de zoekfunctionaliteit geïmplementeerd die gebruikers kunnen gebruiken om te zoeken op de weergegeven formulieren.

**Tip:** *U kunt de lijst met formulieren die op uw formulierportal worden weergegeven, bepalen op basis van vooraf ingestelde criteria en de zoekfunctionaliteit voor eindgebruikers verbergen. Als u de lijst met formulieren wilt beheren, gebruikt u de componenten Predicate om zoekfilters toe te passen. U kunt ook de standaardfilterwaarden opgeven en de zoekopdracht uitschakelen op het tabblad Weergave van het dialoogvenster Component bewerken.*

![Deelvenster Zoeken met datum, volledige tekst, eigenschappen en voorspelling van tags](assets/search-with-predicates.png)

Deelvenster Zoeken met datum, volledige tekst, eigenschappen en voorspelling van tags

#### Datumvoorspelling {#date-predicate}

Met de component Datumvoorspelling kunt u zoeken op de weergegeven formulieren die tijdens een bepaalde periode zijn gewijzigd.

De component Date Predicate configureren:

1. Selecteer de component en selecteer vervolgens ![settings_icon](assets/settings_icon.png). Het dialoogvenster Bewerken wordt geopend.
1. Geef het volgende op:

   * **Type:** De enige beschikbare optie is **Datum van laatste wijziging**

   * **Tekst:** Label of bijschrift voor de component Date Predicate. De standaardwaarde is **Datum van laatste wijziging.**

   * **Label begindatum:** Label of bijschrift van begindatumveld
   * **Label einddatum:** Label of bijschrift voor einddatumveld
   * **Verbergen:** Standaarddatumfilter toepassen op lijstformulieren

1. Selecteren **OK**

#### Voorspelling van volledige tekst {#full-text-predicate}

De component Full Text Predicate implementeert het zoeken naar volledige tekst op formuliergegevens, zoals naam en beschrijving. Gebruikers kunnen elke tekenreeks doorzoeken om formulieren te retourneren die de tekst in hun naam of beschrijving bevatten.

De component Full Text Predicate configureren:

1. Selecteer de component en selecteer vervolgens ![settings_icon](assets/settings_icon.png). Het dialoogvenster Bewerken wordt geopend.
1. Geef de titel op in het dialoogvenster **Hoofdtitel** veld.
1. Selecteren **OK**

#### Predicate eigenschappen {#properties-predicate}

De component Properties Predicate implementeert het zoeken naar formulieren op basis van formuliereigenschappen, zoals titel, auteur en beschrijving.

De component Properties Predicate configureren:

1. Selecteer de component en selecteer vervolgens ![settings_icon](assets/settings_icon.png). Het dialoogvenster Bewerken wordt geopend.
1. Geef op het tabblad Algemeen het zoeklabel op. De standaardwaarde is **Eigenschappen**

1. Selecteer op het tabblad Opties de optie **Item toevoegen.**
1. Selecteer een eigenschap in de vervolgkeuzelijst en geef een zoeklabel voor de eigenschap op in het veld onder de vervolgkeuzelijst.
1. Herhaal stap 4 om meer eigenschappen toe te voegen. U kunt ook een standaardfilterwaarde opgeven om formulieren weer te geven op basis van de opgegeven criteria en de eigenschap verbergen om door eindgebruikers te worden gezocht. Schakel het selectievakje Verbergen voor een eigenschap in en geef de standaardwaarde voor het filter op.
Als u bijvoorbeeld formulieren met &quot;Reizen&quot; in de titels wilt weergeven, selecteert u Verbergen naast de eigenschap Titel. Geef bovendien het tekstvak Reizen op als standaardfilterwaarde.

1. Selecteren **OK**

#### Voorspelfunctie voor tags {#tags-predicate}

De component Voorspelfunctie voor tags implementeert het zoeken naar formulieren op basis van tags die zijn gedefinieerd in Forms Manager.

U configureert als volgt de component Tags voorspellen:

1. Selecteer de component en selecteer vervolgens ![settings_icon](assets/settings_icon.png). Het dialoogvenster Bewerken wordt geopend.
1. Selecteer de knop met de pijl omlaag naast het veld Codes.
1. Selecteer de juiste tags
1. Selecteren **OK**

De geselecteerde labels worden samen met de selectievakjes voor selectie weergegeven in het deelvenster Zoeken. Gebruikers kunnen hun zoekopdracht nu beperken op basis van de tags.

## Formulieren weergeven op een pagina {#list-forms-on-a-page-br}

Als u formulieren op een pagina wilt weergeven, voegt u de opdracht **[!UICONTROL Search & Lister]** Component aan de pagina en vorm de **[!UICONTROL List Pane]**. Als u wilt dat eindgebruikers formulieren met datum, tekst en tags kunnen doorzoeken, voegt u een **[!UICONTROL Search Pane]** component.

Als u een formulier vanaf een willekeurige locatie op de pagina wilt koppelen, gebruikt u de component Koppeling. Voor meer informatie over verbindingscomponent, zie [Koppelingscomponent insluiten in een pagina](../../forms/using/embedding-link-component-page.md).

Als u de formulieren in een ontwerpstatus en de reeds ingediende formulieren wilt weergeven, gebruikt u de **[!UICONTROL Drafts and Submissions]** component. Zie voor meer informatie [De component Concepten en verzendingen aanpassen](../../forms/using/draft-submission-component.md).

## Geschikt voor mobiele apparaten {#mobile-device-friendliness}

De component Forms Portal Search &amp; Lister is gebruiksvriendelijk voor mobiele apparaten en past deze dienovereenkomstig aan. Alle drie de standaardweergaven: raster, kaart, deelvensterlay-outs op basis van het apparaat waarin de site wordt geopend, worden meegeleverd met het feit dat de webpagina ook wordt aangepast. Het eenvoudige feit is dat Zoeken &amp; register alleen een onderdeel is en geen stijl op paginaniveau reguleert.

In de volgende afbeelding ziet u de component Search &amp; Lister wanneer deze wordt geopend op een mobiel apparaat:

![Screenshot van de component Search and Lister](assets/search_lister.png)

Onderdeel Zoeken en bibliotheken

## De pagina&#39;s van een portal voor formulieren aanpassen {#customizing-a-forms-portal-page-br}

U kunt een pagina voor een portal Formulieren aanpassen om de pagina een andere weergave te geven. U kunt ook metagegevens toevoegen om de zoekervaring te verbeteren, de lay-out van de pagina te wijzigen en aangepaste CSS-stijlen toe te voegen. Zie voor meer informatie [Sjablonen aanpassen voor Forms Portal-componenten](../../forms/using/customizing-templates-forms-portal-components.md).

Met de gebruikersinterface van AEM Forms kunt u aangepaste metagegevens toevoegen aan formulieren. Aangepaste metagegevens zijn handig voor het weergeven van lijsten en het zoeken in formulieren voor eindgebruikers. Zie voor meer informatie over aangepaste metagegevens [Sjablonen aanpassen voor Forms Portal-componenten](../../forms/using/customizing-templates-forms-portal-components.md).

Het portal Formulieren biedt renderacties. U kunt de portal Formulieren aanpassen om meer acties toe te voegen. Zie voor meer informatie [Aangepaste actie toevoegen aan formulieritems.](../../forms/using/add-custom-action-form-lister.md)

## Verwante artikelen

* [Formulierportonderdelen inschakelen](/help/forms/using/enabling-forms-portal-components.md)
* [Pagina Formulierportal maken](/help/forms/using/creating-form-portal-page.md)
* [Formulieren op een webpagina weergeven met API&#39;s](/help/forms/using/listing-forms-webpage-using-apis.md)
* [Concepten en verzendingscomponent gebruiken](/help/forms/using/draft-submission-component.md)
* [Opslag van concepten en verzonden formulieren aanpassen](/help/forms/using/draft-submission-component.md)
* [Voorbeeld voor het integreren van concepten en verzendingen in de database](/help/forms/using/integrate-draft-submission-database.md)
* [Sjablonen aanpassen voor componenten van een formulierportal](/help/forms/using/customizing-templates-forms-portal-components.md)
* [Inleiding tot het publiceren van formulieren op een portal](/help/forms/using/introduction-publishing-forms.md)
