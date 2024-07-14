---
title: Sjablonen aanpassen voor Forms Portal-componenten
description: Leer hoe gebruikers in de AEM Forms-gebruikersinterface metagegevens aan formulieren kunnen toevoegen. Aangepaste metagegevens verbeteren de gebruikerservaring bij het weergeven en zoeken van formulieren.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: customization
docset: aem65
feature: Forms Portal
exl-id: f889d996-77f7-4a4f-a637-da43fe1343c5
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '1242'
ht-degree: 0%

---

# Sjablonen aanpassen voor Forms Portal-componenten{#customizing-templates-for-forms-portal-components}

## Vereisten {#prerequisites}

[Metagegevens van formulieren beheren](../../forms/using/manage-form-metadata.md)

Werken met kennis van HTML en CSS

## Overzicht {#overview}

In de AEM Forms-gebruikersinterface kunt u metagegevens toevoegen aan elk formulier. Aangepaste metagegevens kunnen de gebruikerservaring verbeteren wanneer u formulieren van uw organisatie aanbiedt en zoekt.

Met Forms Portal kunt u aangepaste metagegevens gebruiken in formulierlijsten. Wanneer u aangepaste sjablonen voor elementen maakt, kunt u de lay-out van deze sjablonen wijzigen en aangepaste metagegevens gebruiken met de CSS-stijlset.

Ga als volgt te werk, zodat u een aangepaste sjabloon kunt maken voor verschillende Forms Portal-componenten.

## Een aangepaste sjabloon maken {#creating-a-nbsp-custom-template}

1. Een sling maken:mapknooppunt onder /apps

   Voeg een eigenschap &quot;fpContentType&quot; toe. Geef de juiste waarden voor de eigenschap op, afhankelijk van de component waarvoor u de aangepaste sjabloon definieert.

   * component Search &amp; Lister: &quot;/libs/fd/fp/formTemplate&quot;
   * Component Concepten en verzendingen:

      * Concepten, sectie: /libs/fd/fp/ConceptsTemplate
      * Sectie Verzending: /libs/fd/fp/submissionTemplate

   * Koppelingscomponent: /libs/fd/fp/linkTemplate

   Voeg een titel toe die u wilt weergeven tijdens het selecteren van lay-outsjablonen.

   >[!NOTE]
   >
   >De titel kan verschillen van de knooppuntnaam van sling:Folder u creeerde.

   In de volgende afbeelding ziet u de configuratie voor de component Search &amp; Lister.
   ![ Creërend een helling:Omslag ](assets/1.png)

1. Maak een bestandssjabloon.html in deze map zodat deze kan dienen als aangepaste sjabloon.
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

Een aangepaste sjabloon voor elke Forms Portal-component bevat herhaalbare en niet-herhaalbare vermeldingen. Herhaalbare vermeldingen zijn basisentiteiten voor plaatsing op de lijst. Voorbeelden van herhaalbare items zijn Zoeken en registreren, Concepten en verzenden en Koppelingscomponenten.

Forms Portal biedt een syntaxis voor plaatsaanduidingen voor het weergeven van metagegevens die zijn aangepast aan of verwijderd uit de verpakking. De plaatsaanduidingen worden gevuld nadat de resultaten van formulieren, concepten of verzendingen zijn weergegeven.

Om een herhaalbare ingang te omvatten, vorm de waarde van de attributen **gegeven-herhaalbare** aan **waar**.

*in het besproken voorbeeld, zijn twee elementen Div aanwezig bij de bovenkant in het douanemalplaatje. De eerste, met de CSS-klasse &quot;__FP_boxes-container&quot;, werkt als een containerelement voor de formulieren die worden weergegeven. De tweede, met de CSS-klasse &quot;__FP_boxes&quot;, is een sjabloon voor de basisentiteiten, in dit geval een Form. Het **gegeven-herhaalbare**attribuut huidig in het element van Div heeft de waarde **waar**.*

Elke plaatsaanduiding heeft een exclusieve set metagegevens die buiten het vak vallen. Om douanemetagegevens bij een bepaalde plaats op de vorm te tonen, voeg **$ {metadata_prop} bezit** bij de plaats toe.

*in het voorbeeld, wordt het meta-gegevensbezit gebruikt bij veelvoudige instanties. Bijvoorbeeld, wordt het gebruikt in **beschrijving**,**naam**,**formUrl**,**htmlStyle**,**pdfUrl**,**pdfStyle**, en **weg**op de voorgeschreven manier.*

## Metagegevens uit het vak {#out-of-the-box-metadata}

Verschillende Forms Portal-componenten bieden exclusieve sets van metagegevens die u kunt gebruiken voor lijsten.

### Onderdeel Zoeken en bibliotheken {#search-amp-lister-component}

* **Titel:** Titel van de vorm
* **naam**: De naam van de vorm (meestal is het het zelfde als de titel)
* **beschrijving**: Beschrijving van de vorm
* **formUrl**: URL om de vorm als HTML terug te geven
* **pdfUrl**: URL om de vorm als PDF terug te geven
* **assetType**: Type van de activa. De geldige waarden omvatten **Vorm**, **Vorm van de PDF**, **Vorm van de Druk**, en **Aangepaste Vorm**

* **htmlStyle** &amp; **pdfStyle**: De stijl van de vertoning voor de pictogrammen van HTML en van de PDF respectievelijk gebruikt voor het teruggeven. Geldige waarden zijn &quot;**_FP_display_none**&quot; of leeg.

>[!NOTE]
>
>Vergeet niet de klasse __FP_display_none in uw aangepaste stijlblad te gebruiken.

* **downloadUrl**: URL om activa te downloaden.

Ondersteuning voor lokalisatie, sorteren en het gebruik van configuratie-eigenschappen in de gebruikersinterface (alleen zoeken en registreren):

1. **Steun van de Lokalisatie**: Om het even welke statische tekst te lokaliseren gebruik de attributen `${localize-YOUR_TEXT}` en maak de gelokaliseerde waarde beschikbaar, als niet reeds bestaat.
   *In het besproken voorbeeld, worden de attributen `${localize-Apply}` en `${localize-Download}` gebruikt om Toepassen te lokaliseren en tekst te downloaden.*

1. **Steun voor het Sorteren**: Klik het element van de HTML om onderzoeksresultaten te sorteren. Als u sorteren in een tabellay-out wilt implementeren, voegt u het kenmerk &quot;data-sortKey&quot; toe aan de desbetreffende tabelkoptekst. Voeg ook de waarde ervan toe als de metagegevens waarvoor u wilt sorteren.
Voor de koptekst &#39;Titel&#39; in de rasterweergave is de waarde van de header &#39;data-sortKey&#39; bijvoorbeeld &#39;title&#39;. Klik op de kop, zodat u de waarden in een bepaalde kolom kunt sorteren.

1. **Gebruikend configuratieeigenschappen**: De component van het Onderzoek &amp; van het Registreertoestel heeft verscheidene configuraties die u op het gebruikersinterface kunt gebruiken. Als u bijvoorbeeld HTML ToolTip-tekst wilt weergeven die is opgeslagen via het dialoogvenster Bewerken, gebruikt u het kenmerk `${config-htmlLinkText}` . **op dezelfde manier, voor de tekst van het hulpmiddeluiteinde van PDF, gebruik het** `${config-pdfLinkText}` attribuut.

### Component Koppelen {#link-component}

* **Titel:** Titel van de vorm
* **formUrl**: URL om de vorm als HTML terug te geven
* **doel**: Het attribuut van het doel van de verbinding. Geldige waarden zijn &quot;_blank&quot; en &quot;_self&quot;.
* **linkText**: De titel van de verbinding

### Component Concepten en verzendingen {#drafts-amp-submissions-component}

* **Weg**: Weg van de ontwerp/de knoop van voorleggingsmeta-gegevens. Gebruik deze extensie met de extensie .HTML als een URL, zodat u een concept of verzending kunt openen.
* **contextPath**: De weg van de context van de AEM instantie
* **firstLetter**: Eerste brief (in hoofdletters) van de titel van de adaptieve vorm, die als Ontwerp of voorgelegd werd bewaard.
* **formName**: De titel van de adaptieve vorm, die als Ontwerp of voorgelegd werd bewaard.
* **conceptID**: identiteitskaart voor het ontwerp dat vermeld is (Gebruik slechts in het malplaatje voor de sectie van het Ontwerp).
* **submitID**: identiteitskaart voor de voorlegging die (Gebruik slechts in het malplaatje voor de sectie van de Verzending) vermeld is.
* **status**: Status van de voorgelegde vorm. (Alleen gebruiken in de sjabloon voor de sectie Verzending).
* **beschrijving**: Beschrijving van de adaptieve vorm verbonden aan het ontwerp of de voorlegging.
* **diffTime**: Verschil tussen de huidige tijd en laatste sparen actie voor het ontwerp. Het verschil tussen de huidige tijd en de laatst ingediende actie voor de indiening.
* **iconClass**: CSS klasse die wordt gebruikt om de eerste brief van het ontwerp/de voorlegging te tonen. Forms Portal bevat de volgende klassen, die verschillende gekleurde achtergronden bieden.
* **eigenaar**: Gebruiker die tot het ontwerp/de voorlegging leidde.
* **vandaag**: Datum van verwezenlijking van ontwerp of voorlegging in `DD:MM:YYYY` formaat.
* **TimeNow**: Tijd van verwezenlijking van ontwerp of voorlegging in `HH:MM:SS` formaat van 24 uur

*Nota:*

1. Geef de CSS-klasse &quot;__FP_deleteDraft&quot; een naam voor de verwijderoptie in de sectie Concepten onder de component Concepten en verzendingen. Bovendien omvat het attribuut &quot;draftID&quot;met de waarde **$ {draftID}**, die ontwerp identiteitskaart van overeenkomstig ontwerp is.

1. Terwijl het creëren van verbindingen aan open concepten en voorlegging, kunt u **$ {path} $** als waarde van het **href** attribuut voor de ankermarkering specificeren.

![ Concepten en de knoop van de Verzending ](assets/raw-image-with-index.png)

**A**. Containerelement

**B.** &quot;weg&quot;meta-gegevens met een vaste hiërarchie om de duimnagel te verkrijgen die voor elke vorm wordt opgeslagen.

**C.** Gegevens-herhaalbare die attributen voor de malplaatjesectie voor elke vorm worden gebruikt

**D.** lokaliseer &quot;Toepassen&quot;koord

**E.** Gebruikend het configuratiebezit pdfLinkText

**F.** Gebruikend de &quot;pdfUrl&quot;meta-gegevens

## Tips, trucs en bekende problemen {#tips-tricks-and-known-issues}

1. Gebruik geen enkel aanhalingsteken (&#39;) in enige douanemalplaatje.
1. Voor douanemetagegevens, sla dit bezit op **jcr op:inhoud/meta-gegevens** slechts knoop. Als u de metagegevens op een andere plaats opslaat, kunnen ze niet worden weergegeven op Forms Portal.
1. Zorg ervoor dat de naam van aangepaste metagegevens of bestaande metagegevens geen dubbele punt ( : ) bevat. Als dit het geval is, kunt u het niet weergeven in de gebruikersinterface.
1. **gegeven-herhaalbare** heeft geen betekenis voor de component van de Verbinding van de a ****. De Adobe adviseert dat u vermijdt gebruikend dit bezit in het malplaatje voor een component van de Verbinding.

## Verwante artikelen

* [Forms Portal-componenten inschakelen](/help/forms/using/enabling-forms-portal-components.md)
* [Forms Portal-pagina maken](/help/forms/using/creating-form-portal-page.md)
* [Formulieren op een webpagina weergeven met API&#39;s](/help/forms/using/listing-forms-webpage-using-apis.md)
* [Concepten en verzendingscomponent gebruiken](/help/forms/using/draft-submission-component.md)
* [Opslag van concepten en verzonden formulieren aanpassen](/help/forms/using/draft-submission-component.md)
* [Voorbeeld voor het integreren van concepten en verzendingscomponenten met database](/help/forms/using/integrate-draft-submission-database.md)
* [Sjablonen aanpassen voor Forms Portal-componenten](/help/forms/using/customizing-templates-forms-portal-components.md)
* [Inleiding tot het publiceren van formulieren op een portal](/help/forms/using/introduction-publishing-forms.md)
