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
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '1655'
ht-degree: 0%

---

# Een pagina met een portal voor formulieren maken{#creating-a-forms-portal-page}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/configure-forms-portal.html) |
| AEM 6,5 | Dit artikel |

Met Forms Portal-componenten kunnen webontwikkelaars componenten gebruiken voor het maken en aanpassen van een formulierportal op websites die zijn ontworpen met Adobe Experience Manager (AEM). Voor een snel overzicht van vormenportaal, zie [ Inleiding aan het publiceren van vormen op een portaal ](../../forms/using/introduction-publishing-forms.md).

## Vereisten {#prerequisites}

Forms Portal-componenten zijn niet standaard beschikbaar voor gebruik. Zorg ervoor dat de volgende categorieën van de vormenportcomponent zoals die in [ worden beschreven toelatend vormen portalcomponenten ](/help/forms/using/enabling-forms-portal-components.md) worden toegelaten.

**de Diensten van het Document** omvat Onderzoek &amp; van de Registratie, Verbinding, en de componenten van Concepten en van Verzending.

**de Voorspelden van de Diensten van het Document** omvatten Voorspelt van de Datum, Volledige Voorkeur van de Tekst, Voorspelt Eigenschappen, en de Predicate componenten van Markeringen. Deze componenten worden gebruikt om onderzoek in het Onderzoek &amp; component van de Registratie te vormen.

Zodra zij op een AEM plaatspagina worden toegelaten, zijn deze componentencategorieën beschikbaar voor gebruik in componentenbrowser.

![ de poortcomponenten van AEM Forms in componentenbrowser ](assets/component-categories.png)

Componentcategorieën van Forms Portal

## Zoeken &amp; listercomponent {#search-amp-lister-component}

De component Search &amp; Lister, beschikbaar onder de componentencategorie van de Diensten van het Document, wordt gebruikt om vormen op een pagina een lijst te maken en onderzoek op de vermelde vormen uit te voeren. De component bevat twee deelvensters:

* Het deelvenster Lijst waarin de formulieren worden weergegeven.
* Het paneel van het onderzoek waar u de onderzoeksfunctionaliteit toevoegt.

U kunt de component Search &amp; Lister van de de componentencategorie van de Diensten van het Document in componentenbrowser op de pagina slepen. Wanneer de component wordt toegevoegd, ziet deze er ongeveer als volgt uit.

![ Onderzoek &amp; de Component van de Registratie in een pagina ](assets/fp-grid-viw.png)

Component zoeken en labelen op een pagina met rasterlay-out

### Lijstvenster {#list-pane}

Het deelvenster Lijst is een gebied waarin uw formulieren worden weergegeven. De component Zoeken en register bevat verschillende configuratieopties waarmee u de weergave van formulieren in het deelvenster Lijst kunt bepalen.

Om de ruit van de Lijst te vormen, selecteer de component van het Onderzoek en van de Registratie en selecteer dan ![ settings_icon ](assets/settings_icon.png). Het dialoogvenster **[!UICONTROL &#x200B; Edit Component]** wordt geopend.

![ ruit van de Lijst op geeft wijze uit ](assets/edit-list.png)

Het deelvenster Lijst in de bewerkingsmodus

Het **geeft** dialoog uit omvat verscheidene lusjes die configuratieopties verstrekken die in de lijst hieronder worden beschreven. Selecteer **O.K.** om de configuratie te bewaren, wanneer gedaan.

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
   <td>Hiermee configureert u de mappen waarin elementen worden geüpload met de gebruikersinterface van AEM Forms. Standaard worden alle geüploade elementen weergegeven. Voor meer informatie over AEM Forms UI, zie <a href="../../forms/using/introduction-managing-forms.md" target="_blank"> Inleiding aan het beheren van vormen </a>.</td>
  </tr>
  <tr>
   <td><p><span class="uicontrol"><strong>Weergave</strong></code></p> </td>
   <td>Titeltekst</td>
   <td>Titel voor de component Search &amp; Lister. De standaardtitel is <strong> Portaal van Forms.</strong></td>
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
   <td><p>Vormt de resultaattekst (bijvoorbeeld, 1-12 van 601 <strong> Resultaten </strong>). De standaardwaarde is <strong> Resultaten </strong>.</p> <p>Bijvoorbeeld, als u <strong> Forms </strong> op dit gebied specificeert en er een totaal van 601 vormen zijn, verandert de resultaattekst in 1-12 van 601 <strong> Forms.</strong></p> </td>
  </tr>
  <tr>
   <td> </td>
   <td>Paginatype</td>
   <td><p>Vormt de paginatekst (bijvoorbeeld, <strong> Pagina </strong> 1 van 51). De standaardwaarde is <strong> Pagina </strong>.</p> <p>Bijvoorbeeld, als u <strong> Vorm van de Toepassing </strong> op dit gebied specificeert en er 51 pagina's zijn, verandert de paginatekst in <strong> Vorm van de Toepassing </strong> 1 van 51.</p> </td>
  </tr>
  <tr>
   <td> </td>
   <td>Van tekst</td>
   <td><p>Vervangt het woord <strong> van </strong> met de gespecificeerde tekst (Pagina 1 <strong> van </strong> 51). De standaardwaarde is <strong> van </strong>.</p> <p>Bijvoorbeeld, als u <strong> van </strong> op dit gebied specificeert, verandert de tekst in Pagina 1 <strong> van </strong> 51.</p> </td>
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
   <td><p>Vormt een servlet waar de vormgegevens worden voorgelegd.</p> <p><strong> Nota:</strong> <em> legt URL voor een vorm kan op verscheidene plaatsen worden gespecificeerd en zijn orde van belangrijkheid is als volgt:</em></p>
    <ol>
     <li><em>VerzendURL die is ingesloten in het formulier (in de knop Verzenden) heeft de hoogste prioriteit.</em></li>
     <li><em>VerzendURL die wordt vermeld in de gebruikersinterface van AEM Forms heeft de op een na hoogste prioriteit.</em></li>
     <li><em>De laagste prioriteit voor het verzenden van een URL die in het formulierportaal wordt vermeld.</em></li>
    </ol> </td>
  </tr>
  <tr>
   <td> </td>
   <td>Knopinfo voor HTML renderen</td>
   <td>Hiermee configureert u de tekst voor de knopinfo, die wordt weergegeven wanneer u de aanwijzer boven <img height="16" src="assets/aem6forms_panel-html.png" width="13" /> houdt (het pictogram HTML5).</td>
  </tr>
  <tr>
   <td> </td>
   <td>Knopinfo voor PDF renderen</td>
   <td>Hiermee configureert u de tekst voor de knopinfo, die wordt weergegeven wanneer u de aanwijzer boven <img height="16" src="assets/aem6forms_panel-pdf.png" width="14" /> houdt (het pictogram PDF).</td>
  </tr>
  <tr>
   <td><span class="uicontrol"><strong>Stijl</strong></code></td>
   <td>Stijltype</td>
   <td>Laat u <strong> specificeren Geen Stijl, StandaardStijl </strong>, of <strong> de Stijl van de Douane </strong> om van de vormen een lijst te maken.</td>
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

**Uiteinde:** *u kunt de lijst van vormen controleren die op uw vormenportaal op vooraf ingestelde criteria wordt getoond en de onderzoeksfunctionaliteit voor eind - gebruikers verbergen. Als u de lijst met formulieren wilt beheren, gebruikt u de componenten Predicate om zoekfilters toe te passen. U kunt de standaardfilterwaarden ook specificeren en het onderzoek van het lusje van de Vertoning van de Edit dialoog van de Component onbruikbaar maken.*

![ het Comité van het Onderzoek met Datum, Volledige Tekst, Eigenschappen, en het Predicate van Markeringen ](assets/search-with-predicates.png)

Deelvenster Zoeken met datum, volledige tekst, eigenschappen en voorspelling van tags

#### Datumvoorspelling {#date-predicate}

Met de component Datumvoorspelling kunt u zoeken op de weergegeven formulieren die tijdens een bepaalde periode zijn gewijzigd.

De component Date Predicate configureren:

1. Selecteer de component en selecteer dan ![ settings_icon ](assets/settings_icon.png). Het dialoogvenster Bewerken wordt geopend.
1. Geef het volgende op:

   * **Type:** de enige beschikbare optie is **Laatste Gewijzigde Datum**

   * **Tekst:** Etiket of titel voor de Voorspelende Component van de Datum. De standaardwaarde is **Laatste Gewijzigde Datum.**

   * **het Etiket van de Datum van het Begin:** Etiket of titel van het gebied van de begindatum
   * **Eind DatumEtiket:** Etiket of titel voor einddatumgebied
   * **Verbergen:** om standaarddatumfilter af te dwingen om formulieren te vermelden

1. Selecteer **OK**

#### Voorspelling van volledige tekst {#full-text-predicate}

De component Full Text Predicate implementeert het zoeken naar volledige tekst op formuliergegevens, zoals naam en beschrijving. Gebruikers kunnen elke tekenreeks doorzoeken om formulieren te retourneren die de tekst in hun naam of beschrijving bevatten.

De component Full Text Predicate configureren:

1. Selecteer de component en selecteer dan ![ settings_icon ](assets/settings_icon.png). Het dialoogvenster Bewerken wordt geopend.
1. Specificeer de titel op het **Belangrijkste gebied van de Titel**.
1. Selecteer **O.K.**

#### Predicate eigenschappen {#properties-predicate}

De component Properties Predicate implementeert het zoeken naar formulieren op basis van formuliereigenschappen, zoals titel, auteur en beschrijving.

De component Properties Predicate configureren:

1. Selecteer de component en selecteer dan ![ settings_icon ](assets/settings_icon.png). Het dialoogvenster Bewerken wordt geopend.
1. Geef op het tabblad Algemeen het zoeklabel op. De standaardwaarde is **Eigenschappen**

1. In het lusje van Opties, voeg **Punt toe.**
1. Selecteer een eigenschap in de vervolgkeuzelijst en geef een zoeklabel voor de eigenschap op in het veld onder de vervolgkeuzelijst.
1. Herhaal stap 4 om meer eigenschappen toe te voegen. U kunt ook een standaardfilterwaarde opgeven om formulieren weer te geven op basis van de opgegeven criteria en de eigenschap verbergen om door eindgebruikers te worden gezocht. Schakel het selectievakje Verbergen voor een eigenschap in en geef de standaardwaarde voor het filter op.
Als u bijvoorbeeld formulieren met &quot;Reizen&quot; in de titels wilt weergeven, selecteert u Verbergen naast de eigenschap Titel. Geef bovendien het tekstvak Reizen op als standaardfilterwaarde.

1. Selecteer **OK**

#### Voorspelfunctie voor tags {#tags-predicate}

De component Voorspelfunctie voor tags implementeert het zoeken naar formulieren op basis van tags die zijn gedefinieerd in Forms Manager.

U configureert als volgt de component Tags voorspellen:

1. Selecteer de component en selecteer dan ![ settings_icon ](assets/settings_icon.png). Het dialoogvenster Bewerken wordt geopend.
1. Selecteer de knop met de pijl omlaag naast het veld Codes.
1. Selecteer de juiste tags
1. Selecteer **OK**

De geselecteerde labels worden samen met de selectievakjes voor selectie weergegeven in het deelvenster Zoeken. Gebruikers kunnen hun zoekopdracht nu beperken op basis van de tags.

## Formulieren weergeven op een pagina {#list-forms-on-a-page-br}

Als u formulieren op een pagina wilt weergeven, voegt u de component **[!UICONTROL Search & Lister]** toe aan de pagina en configureert u de component **[!UICONTROL List Pane]** . Als u wilt dat eindgebruikers formulieren met datum, tekst en tags kunnen doorzoeken, voegt u een **[!UICONTROL Search Pane]** -component toe.

Als u een formulier vanaf een willekeurige locatie op de pagina wilt koppelen, gebruikt u de component Koppeling. Voor meer informatie over verbindingscomponent, zie [ Inbeddend verbindingscomponent in een pagina ](../../forms/using/embedding-link-component-page.md).

Gebruik de component **[!UICONTROL Drafts and Submissions]** als u de formulieren in een concept-status en de formulieren die al zijn verzonden, wilt weergeven. Voor meer informatie, zie [ Aanpassen Concepten en de component van Verzending ](../../forms/using/draft-submission-component.md).

## Geschikt voor mobiele apparaten {#mobile-device-friendliness}

De component Forms Portal Search &amp; Lister is gebruiksvriendelijk voor mobiele apparaten en past deze dienovereenkomstig aan. Alle drie de standaardweergaven: raster, kaart, deelvensterlay-outs op basis van het apparaat waarin de site wordt geopend, worden meegeleverd met het feit dat de webpagina ook wordt aangepast. Het eenvoudige feit is dat Zoeken &amp; register alleen een onderdeel is en geen stijl op paginaniveau reguleert.

In de volgende afbeelding ziet u de component Search &amp; Lister wanneer deze wordt geopend op een mobiel apparaat:

![ Schermafbeelding van de component van het Onderzoek en van het ister ](assets/search_lister.png)

Onderdeel Zoeken en bibliotheken

## De pagina&#39;s van een portal voor formulieren aanpassen {#customizing-a-forms-portal-page-br}

U kunt een pagina voor een portal Formulieren aanpassen om de pagina een andere weergave te geven. U kunt ook metagegevens toevoegen om de zoekervaring te verbeteren, de lay-out van de pagina te wijzigen en aangepaste CSS-stijlen toe te voegen. Voor meer informatie, zie [ Aanpassende malplaatjes voor de Componenten van Forms Portal ](../../forms/using/customizing-templates-forms-portal-components.md).

Met de gebruikersinterface van AEM Forms kunt u aangepaste metagegevens toevoegen aan formulieren. Aangepaste metagegevens zijn handig voor het weergeven van lijsten en het zoeken in formulieren voor eindgebruikers. Voor meer informatie over meta-gegevens van de Douane, zie [ Aanpassende malplaatjes voor de Componenten van Forms Portal ](../../forms/using/customizing-templates-forms-portal-components.md).

Het portal Formulieren biedt renderacties. U kunt de portal Formulieren aanpassen om meer acties toe te voegen. Voor gedetailleerde informatie, zie [ Toevoegend douaneactie op de punten van de vormlijst.](../../forms/using/add-custom-action-form-lister.md)

## Verwante artikelen

* [Formulierportonderdelen inschakelen](/help/forms/using/enabling-forms-portal-components.md)
* [Pagina Formulierportal maken](/help/forms/using/creating-form-portal-page.md)
* [Formulieren op een webpagina weergeven met API&#39;s](/help/forms/using/listing-forms-webpage-using-apis.md)
* [Concepten en verzendingscomponent gebruiken](/help/forms/using/draft-submission-component.md)
* [Opslag van concepten en verzonden formulieren aanpassen](/help/forms/using/draft-submission-component.md)
* [Voorbeeld voor het integreren van concepten en verzendingen in de database](/help/forms/using/integrate-draft-submission-database.md)
* [Sjablonen aanpassen voor componenten van een formulierportal](/help/forms/using/customizing-templates-forms-portal-components.md)
* [Inleiding tot het publiceren van formulieren op een portal](/help/forms/using/introduction-publishing-forms.md)
