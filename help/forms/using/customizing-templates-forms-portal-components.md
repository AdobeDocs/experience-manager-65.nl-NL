---
title: Sjablonen aanpassen voor componenten van een formulierportal
seo-title: Sjablonen aanpassen voor componenten van een formulierportal
description: Aangepaste metagegevens weergeven in formulierlijst
seo-description: Aangepaste metagegevens weergeven in formulierlijst
uuid: 212109ca-85c8-4915-82e5-a18a0443be1b
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: customization
discoiquuid: 7566203f-2f80-4ce7-bff9-073d67119f64
docset: aem65
feature: Forms Portal
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '1241'
ht-degree: 0%

---


# Sjablonen aanpassen voor componenten van een formulierportal{#customizing-templates-for-forms-portal-components}

## Vereisten {#prerequisites}

[Metagegevens van formulieren beheren](../../forms/using/manage-form-metadata.md)

Werken met kennis van HTML en CSS

## Overzicht {#overview}

In de AEM Forms-gebruikersinterface kunt u metagegevens toevoegen aan elk formulier. Aangepaste metagegevens kunnen de gebruikerservaring verbeteren wanneer u formulieren van uw organisatie aanbiedt en zoekt.

Met Forms Portal kunt u aangepaste metagegevens gebruiken in formulierlijsten. Wanneer u aangepaste sjablonen voor elementen maakt, kunt u de lay-out van deze sjablonen wijzigen en aangepaste metagegevens gebruiken met de CSS-stijlset.

Voer de volgende stappen uit om een aangepaste sjabloon te maken voor verschillende Forms Portal-componenten.

## Een aangepaste sjabloon maken {#creating-a-nbsp-custom-template}

1. Een sling maken:mapknooppunt onder /apps

   Voeg een eigenschap &quot;fpContentType&quot; toe. Geef de juiste waarden voor de eigenschap op, afhankelijk van de component waarvoor u de aangepaste sjabloon definieert.

   * Onderdeel Zoeken en register: &quot;/libs/fd/fp/formTemplate&quot;
   * Component Concepten en verzendingen:

      * Sectie Concepten: /libs/fd/fp/conceptsTemplate
      * Sectie Verzending: /libs/fd/fp/submissionTemplate
   * Koppelingscomponent: /libs/fd/fp/linkTemplate

   Voeg een titel toe die u wilt weergeven tijdens het selecteren van lay-outsjablonen.

   >[!NOTE]
   >
   >De titel kan verschillen van de knooppuntnaam van sling:Folder u creeerde.

   In de volgende afbeelding ziet u de configuratie voor de component Search &amp; Lister.
   ![Een tekenreeks maken:map](assets/1.png)

1. Maak een bestandssjabloon.html in deze map om als aangepaste sjabloon te dienen.
1. Schrijf de aangepaste sjabloon en gebruik aangepaste metagegevens zoals hieronder beschreven.

## Werkvoorbeeld {#working-example}

Hieronder volgt een voorbeeldimplementatie van een aangepaste sjabloon waarbij Forms Portal een aangepaste Geometrixx Gov Card Layout voor de component Search &amp; Lister verkrijgt.

```html
<div class="__FP_boxes-container __FP_single-color">
    <div class="boxes __FP_boxes __FP_single-color" data-repeatable="true">
 <div class="__FP_boxes-thumbnail">
     <img src ="${path}/jcr:content/renditions/cq5dam.thumbnail.319.319.png"/>
        </div>
        <h3 class="__FP_single-color" title="${name}" tabindex="0">${name}</h3>
        <p>${description}</p>
        <div class="boxes-icon-cont __FP_boxes-icon-cont">
            <div class="op-dow">
                <a href="${formUrl}" target="_blank" class="__FP_button ${htmlStyle}" title="${config-htmlLinkText}">${localize-Apply}</a>
                <a href="${pdfUrl}" class="__FP_button ${pdfStyle}" title="${config-pdfLinkText}">${localize-Download}</a>
            </div>
        </div>
    </div>
</div>
```

## Technische specificaties voor aangepaste sjablonen {#technical-specifications-for-custom-templates}

Een douanemalplaatje voor om het even welke component van Forms Portal omvat herhaalbare en niet-herhaalbare ingangen. Herhaalbare vermeldingen zijn basisentiteiten voor plaatsing op de lijst. Voorbeelden van herhaalbare items zijn Zoeken en registreren, Concepten en verzenden en Koppelingscomponenten.

Forms Portal biedt een syntaxis waarmee plaatsaanduidingen aangepaste/OTB-metagegevens kunnen weergeven. De plaatsaanduidingen worden gevuld nadat de resultaten van formulieren, concepten of verzendingen zijn weergegeven.

Om een herhaalbare ingang op te nemen, vorm de waarde van het attribuut **data-repeatable** aan **true**.

*In het besproken voorbeeld, zijn twee elementen Div aanwezig bij de bovenkant in het douanemalplaatje. De eerste, met de CSS-klasse &quot;__FP_boxes-container&quot;, werkt als een containerelement voor de formulieren die worden weergegeven. De tweede, met de CSS-klasse &quot;__FP_boxes&quot;, is een sjabloon voor de basisentiteiten, in dit geval een Form. Het **data-repeatable**attribuut aanwezig in het element Div heeft de waarde **true**.*

Elke plaatsaanduiding heeft een exclusieve OTB-metagegevensset. Als u aangepaste metagegevens op een bepaalde plaats in het formulier wilt weergeven, voegt u de eigenschap **${metadata_prop}** op de plaats toe.

*In het voorbeeld wordt de eigenschap metadata in meerdere instanties gebruikt. Bijvoorbeeld, wordt het gebruikt in **description**,**name**,**formUrl**,**htmlStyle**,**pdfUrl**,**pdfStyle**, en &lt;a 12/>pad **op de voorgeschreven wijze.***

## Metagegevens {#out-of-the-box-metadata} uit het vak

Verschillende Forms Portal-componenten bieden exclusieve sets OOTB-metagegevens die u voor een aanbieding kunt gebruiken.

### Onderdeel {#search-amp-lister-component} zoeken

* **Titel:** Titel van het formulier
* **naam**: Naam van het formulier (meestal gelijk aan de titel)
* **beschrijving**: Beschrijving van het formulier
* **formUrl**: URL om het formulier te genereren als HTML
* **pdfUrl**: URL om het formulier te genereren als PDF
* **assetType**: Type van het element. Geldige waarden zijn **Form**,**PDF Form**, **Print Form** en **Adaptive Form**

* **htmlStyle**&amp;  **pdfStyle**: Weergavestijl voor respectievelijk HTML- en PDF-pictogrammen die worden gebruikt voor rendering. Geldige waarden zijn &quot;**__FP_display_none**&quot; of leeg.

>[!NOTE]
>
>Vergeet niet de klasse __FP_display_none in uw aangepaste stijlblad te gebruiken.

* **downloadUrl**: URL om een middel te downloaden.

Ondersteuning voor lokalisatie, sorteren en het gebruik van configuratie-eigenschappen in de gebruikersinterface (alleen zoeken en registreren):

1. **Ondersteuning voor** lokalisatie: Als u statische tekst wilt lokaliseren, gebruikt u het kenmerk  `${localize-YOUR_TEXT}` en stelt u de gelokaliseerde waarde beschikbaar als dat nog niet het geval is.
   *In het besproken voorbeeld worden de kenmerken  `${localize-Apply}` en  `${localize-Download}` worden gebruikt om de tekst Toepassen en downloaden te lokaliseren.*

1. **Ondersteuning voor sorteren**: Klik op het HTML-element om de zoekresultaten te sorteren. Als u sorteren in een ingediende lay-out wilt implementeren, voegt u het kenmerk &quot;data-sortKey&quot; toe aan de desbetreffende tabelkoptekst. Voeg ook de waarde ervan toe als de metagegevens waarvoor u wilt sorteren.
Voor de koptekst &#39;Titel&#39; in de rasterweergave is de waarde van de header &#39;data-sortKey&#39; bijvoorbeeld &#39;title&#39;. Klik op de kop om de waarden in een bepaalde kolom te sorteren.

1. **Configuratie-eigenschappen** gebruiken: De component Search &amp; Lister heeft verscheidene configuraties die u op het gebruikersinterface kunt gebruiken. Als u bijvoorbeeld HTML ToolTip-tekst wilt weergeven die is opgeslagen via het dialoogvenster Bewerken, gebruikt u het kenmerk `${config-htmlLinkText}`. **Gebruik ook voor tekst in de knopinfo voor PDF** `${config-pdfLinkText}` het kenmerk.

### Koppelingscomponent {#link-component}

* **Titel:** Titel van het formulier
* **formUrl**: URL om het formulier te genereren als HTML
* **doel**: Doelkenmerk van de koppeling. Geldige waarden zijn &quot;_blank&quot; en &quot;_self&quot;.
* **linkText**: Bijschrift koppelen

### Component Concepten en verzendingen {#drafts-amp-submissions-component}

* **Pad**: Pad van het metagegevensknooppunt voor concept/verzending. Gebruik deze extensie met de extensie .HTML als een URL om een concept of verzending te openen.
* **contextPath**: Contextpad van AEM instantie
* **firstLetter**: Eerste letter (hoofdletters) van de titel van het adaptieve formulier, die als concept is opgeslagen of is ingediend.
* **formName**: De titel van het adaptieve formulier, dat als concept is opgeslagen of is verzonden.
* **conceptID**: Id voor het concept dat wordt weergegeven (alleen gebruiken in de sjabloon voor de sectie Concept).
* **submitID**: Id voor de verzending die wordt vermeld (alleen gebruiken in de sjabloon voor de sectie Verzending).
* **status**: Status van het ingediende formulier. (Alleen gebruiken in de sjabloon voor de sectie Verzending).
* **beschrijving**: Beschrijving van het aan het ontwerp of de indiening verbonden adaptieve formulier.
* **diffTime**: Verschil tussen de huidige tijd en de laatste opslagactie voor het concept. U kunt ook een verschil maken tussen de huidige tijd en de laatste verzendactie voor de verzending.
* **iconClass**: CSS-klasse die wordt gebruikt om de eerste letter van het concept/de verzending weer te geven. Forms Portal bevat de volgende klassen, die verschillende gekleurde achtergronden bieden.
* **eigenaar**: Gebruiker die het concept/de verzending heeft gemaakt.
* **Vandaag**: Datum waarop het concept of de verzending is gemaakt in de indeling DD:MM:YYYY.
* **TijdNu**: Tijdstip van aanmaak of verzending in UU:MM:SS 24-uursnotatie

*Opmerking:*

1. Geef de CSS-klasse &quot;__FP_deleteDraft&quot; een naam voor de verwijderoptie in de sectie Concepten onder de component Concepten en verzendingen. Bovendien omvat het attribuut &quot;draftID&quot;met de waarde **${draftID}**, die conceptidentidentiteitskaart van het overeenkomstige ontwerp is.

1. Tijdens het cre??ren van verbindingen aan open ontwerpen en bijdragen, kunt u **${path}.html** als waarde van **href** attributen voor de ankermarkering specificeren.

![Concepten en verzendknooppunt](assets/raw-image-with-index.png)

**A**. Containerelement

**Metagegevens van B.** &quot;pad&quot; met een vaste hi??rarchie om de voor elk formulier opgeslagen miniatuur te verkrijgen.

**C.** Data-herhaalbaar kenmerk gebruikt voor de sjabloonsectie voor elk formulier

**D.** De tekenreeks Toepassen lokaliseren

**E.** De configuratie-eigenschap pdfLinkText gebruiken

**F.** De metagegevens &quot;pdfUrl&quot; gebruiken

## Tips, trucs en bekende problemen {#tips-tricks-and-known-issues}

1. Gebruik geen enkel aanhalingsteken (&#39;) in enige douanemalplaatje.
1. Voor aangepaste metagegevens slaat u deze eigenschap alleen op het knooppunt **jcr:content/metadata** op. Als u het op een andere plaats opslaat, kan Forms Portal de meta-gegevens niet tonen.
1. Zorg ervoor dat de naam van aangepaste metagegevens of bestaande metagegevens geen dubbele punt bevat ( : ). Als dit het geval is, kunt u het niet weergeven in de gebruikersinterface.
1. **gegeven-** herhaalbaar heeft geen betekenis voor een  **** Linkcomponent. Adobe raadt u aan deze eigenschap niet te gebruiken in de sjabloon voor een koppelingscomponent.

## Verwante artikelen

* [Formulierportonderdelen inschakelen](/help/forms/using/enabling-forms-portal-components.md)
* [Pagina Formulierportal maken](/help/forms/using/creating-form-portal-page.md)
* [Formulieren op een webpagina weergeven met API&#39;s](/help/forms/using/listing-forms-webpage-using-apis.md)
* [Concepten en verzendingscomponent gebruiken](/help/forms/using/draft-submission-component.md)
* [Opslag van concepten en verzonden formulieren aanpassen](/help/forms/using/draft-submission-component.md)
* [Voorbeeld voor het integreren van concepten en verzendingen in de database](/help/forms/using/integrate-draft-submission-database.md)
* [Sjablonen aanpassen voor componenten van een formulierportal](/help/forms/using/customizing-templates-forms-portal-components.md)
* [Inleiding tot het publiceren van formulieren op een portal](/help/forms/using/introduction-publishing-forms.md)