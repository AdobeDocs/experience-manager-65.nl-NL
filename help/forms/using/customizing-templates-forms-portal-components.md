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
   ![Een tekenreeks maken:map](assets/1.png)

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

Om een herhaalbare ingang te omvatten, vorm de waarde van de attributen **data-herhaalbaar** tot **true**.

*In het besproken voorbeeld, zijn twee elementen Div aanwezig bij de bovenkant in het douanemalplaatje. De eerste, met de CSS-klasse &quot;__FP_boxes-container&quot;, werkt als een containerelement voor de formulieren die worden weergegeven. De tweede, met de CSS-klasse &quot;__FP_boxes&quot;, is een sjabloon voor de basisentiteiten, in dit geval een Form. De **data-herhaalbaar**kenmerk aanwezig in Div-element heeft de waarde **true**.*

Elke plaatsaanduiding heeft een exclusieve set metagegevens die buiten het vak vallen. Als u aangepaste metagegevens wilt weergeven op een bepaalde plaats op het formulier, voegt u de opdracht **${metadata_prop} eigenschap** ter plekke.

*In het voorbeeld wordt de eigenschap metadata in meerdere instanties gebruikt. Het wordt bijvoorbeeld gebruikt in **beschrijving**,**name**,**formUrl**,**htmlStyle**,**pdfUrl**,**pdfStyle**, en **pad**op de voorgeschreven wijze.*

## Metagegevens uit het vak {#out-of-the-box-metadata}

Verschillende Forms Portal-componenten bieden exclusieve sets van metagegevens die u kunt gebruiken voor lijsten.

### Onderdeel Zoeken en bibliotheken {#search-amp-lister-component}

* **Titel:** Titel van het formulier
* **name**: Naam van het formulier (meestal gelijk aan de titel)
* **beschrijving**: Beschrijving van het formulier
* **formUrl**: URL om het formulier weer te geven als HTML
* **pdfUrl**: URL om het formulier weer te geven als PDF
* **assetType**: Type van het element. Geldige waarden zijn **Formulier**, **PDF-formulier**, **Formulier afdrukken**, en **Adaptief formulier**

* **htmlStyle**&amp; **pdfStyle**: Weergavestijl voor HTML- en PDF-pictogrammen die respectievelijk worden gebruikt voor rendering. Geldige waarden zijn &quot;**__FP_display_none**&quot; of leeg.

>[!NOTE]
>
>Vergeet niet de klasse __FP_display_none in uw aangepaste stijlblad te gebruiken.

* **downloadUrl**: URL om een middel te downloaden.

Ondersteuning voor lokalisatie, sorteren en het gebruik van configuratie-eigenschappen in de gebruikersinterface (alleen zoeken en registreren):

1. **Ondersteuning voor lokalisatie**: Gebruik het kenmerk om statische tekst te lokaliseren `${localize-YOUR_TEXT}` en maak de gelokaliseerde waarde beschikbaar, als nog niet bestaat.
   *In het besproken voorbeeld, de attributen `${localize-Apply}` en `${localize-Download}` worden gebruikt om de tekst Toepassen en downloaden te lokaliseren.*

1. **Ondersteuning voor sorteren**: Klik op het element HTML om de zoekresultaten te sorteren. Als u sorteren in een tabellay-out wilt implementeren, voegt u het kenmerk &quot;data-sortKey&quot; toe aan de desbetreffende tabelkoptekst. Voeg ook de waarde ervan toe als de metagegevens waarvoor u wilt sorteren.
Voor de koptekst &#39;Titel&#39; in de rasterweergave is de waarde van de header &#39;data-sortKey&#39; bijvoorbeeld &#39;title&#39;. Klik op de kop, zodat u de waarden in een bepaalde kolom kunt sorteren.

1. **Configuratieeigenschappen gebruiken**: De component Search &amp; Lister heeft diverse configuraties die u in de gebruikersinterface kunt gebruiken. Als u bijvoorbeeld HTML ToolTip-tekst wilt weergeven die is opgeslagen via het dialoogvenster Bewerken, gebruikt u de opdracht `${config-htmlLinkText}` kenmerk. **Op dezelfde manier kunt u voor knopinfo-tekst de opdracht** `${config-pdfLinkText}` kenmerk.

### Component Koppelen {#link-component}

* **Titel:** Titel van het formulier
* **formUrl**: URL om het formulier weer te geven als HTML
* **target**: Het kenmerk Doel van de koppeling. Geldige waarden zijn &quot;_blank&quot; en &quot;_self&quot;.
* **linkText**: Bijschrift koppelen

### Component Concepten en verzendingen {#drafts-amp-submissions-component}

* **Pad**: Het pad van het metagegevensknooppunt concept/verzending. Gebruik deze extensie met de extensie .HTML als een URL, zodat u een concept of verzending kunt openen.
* **contextPath**: Contextpad van AEM instantie
* **firstLetter**: Eerste letter (in hoofdletters) van de titel van het adaptieve formulier, die als concept is opgeslagen of is ingediend.
* **formName**: De titel van het adaptieve formulier, dat als concept is opgeslagen of is ingediend.
* **conceptID**: ID voor het concept dat wordt weergegeven (alleen gebruiken in de sjabloon voor de sectie Concept).
* **submitID**: ID voor de verzending die wordt vermeld (alleen gebruiken in de sjabloon voor de sectie Verzending).
* **status**: Status van het ingediende formulier. (Alleen gebruiken in de sjabloon voor de sectie Verzending).
* **beschrijving**: Beschrijving van het aan het ontwerp of de indiening verbonden adaptieve formulier.
* **diffTime**: Verschil tussen de huidige tijd en de laatste opslagactie voor het concept. Het verschil tussen de huidige tijd en de laatst ingediende actie voor de indiening.
* **iconClass**: CSS-klasse die wordt gebruikt om de eerste letter van het concept/de verzending weer te geven. Forms Portal bevat de volgende klassen, die verschillende gekleurde achtergronden bieden.
* **eigenaar**: Gebruiker die het concept/de verzending heeft gemaakt.
* **Vandaag**: Datum van aanmaak of indiening van het ontwerp in `DD:MM:YYYY` gebruiken.
* **TimeNow**: Tijdstip van aanmaak of indiening van het ontwerp in `HH:MM:SS` 24-uurs formaat

*Opmerking:*

1. Geef de CSS-klasse &quot;__FP_deleteDraft&quot; een naam voor de verwijderoptie in de sectie Concepten onder de component Concepten en verzendingen. Voeg ook het kenmerk &quot;draftID&quot; toe aan de waarde **${draftID}**, de ontwerp-id van het corresponderende ontwerp.

1. Tijdens het maken van koppelingen naar open concepten en verzendingen kunt u **${path}.html** als de waarde van de **href** -kenmerk voor de ankertag.

![Concepten en verzendknooppunt](assets/raw-image-with-index.png)

**A**. Containerelement

**B.** &#39;path&#39;-metagegevens met een vaste hiërarchie om de voor elk formulier opgeslagen miniatuur te verkrijgen.

**C.** Kenmerk dat kan worden herhaald voor de sjabloonsectie voor elk formulier

**D.** Tekenreeks &quot;Toepassen&quot; lokaliseren

**E.** De configuratieeigenschap pdfLinkText gebruiken

**F.** De metagegevens &quot;pdfUrl&quot; gebruiken

## Tips, trucs en bekende problemen {#tips-tricks-and-known-issues}

1. Gebruik geen enkel aanhalingsteken (&#39;) in enige douanemalplaatje.
1. Voor aangepaste metagegevens slaat u deze eigenschap op het tabblad **jcr:inhoud/metagegevens** alleen knooppunt. Als u de metagegevens op een andere plaats opslaat, kunnen ze niet worden weergegeven op Forms Portal.
1. Zorg ervoor dat de naam van aangepaste metagegevens of bestaande metagegevens geen dubbele punt ( : ) bevat. Als dit het geval is, kunt u het niet weergeven in de gebruikersinterface.
1. **data-herhaalbaar** heeft geen betekenis voor een **Koppeling** component. De Adobe adviseert dat u vermijdt gebruikend dit bezit in het malplaatje voor een component van de Verbinding.

## Verwante artikelen

* [Forms Portal-componenten inschakelen](/help/forms/using/enabling-forms-portal-components.md)
* [Forms Portal-pagina maken](/help/forms/using/creating-form-portal-page.md)
* [Formulieren op een webpagina weergeven met API&#39;s](/help/forms/using/listing-forms-webpage-using-apis.md)
* [Concepten en verzendingscomponent gebruiken](/help/forms/using/draft-submission-component.md)
* [Opslag van concepten en verzonden formulieren aanpassen](/help/forms/using/draft-submission-component.md)
* [Voorbeeld voor het integreren van concepten en verzendingscomponenten met database](/help/forms/using/integrate-draft-submission-database.md)
* [Sjablonen aanpassen voor Forms Portal-componenten](/help/forms/using/customizing-templates-forms-portal-components.md)
* [Inleiding tot het publiceren van formulieren op een portal](/help/forms/using/introduction-publishing-forms.md)
