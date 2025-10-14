---
title: Metagegevens van formulieren beheren
description: Met metagegevens kunt u elementen gemakkelijker indelen en ordenen en gebruikers die op zoek zijn naar een bepaald middel helpen.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-manager
docset: aem65
role: Admin,User
exl-id: f82bbd39-b655-47a9-bca9-21d7cd30c082
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
source-git-commit: 539da06db98395ae6eaee8103a3e4b31204abbb8
workflow-type: tm+mt
source-wordcount: '1952'
ht-degree: 0%

---

# Metagegevens van formulieren beheren{#manage-form-metadata}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [&#x200B; klik hier &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/manage-metadata/manage-form-metadata.html?lang=nl-NL) |
| AEM 6,5 | Dit artikel |

## Overzicht  {#overview-nbsp}

Met metagegevens kunt u elementen gemakkelijker indelen en ordenen en gebruikers die op zoek zijn naar een bepaald middel helpen.

AEM Forms biedt standaard een gedefinieerde set metagegevens voor elk elementtype. Naast de standaardmetagegevens kunt u ook aangepaste metagegevens toevoegen aan elk elementtype. AEM Forms biedt u ook de juiste middelen om al deze metagegevens efficiënt voor uw formulieren te maken, te beheren en uit te wisselen.

Als u een ontwikkelaar of site-eigenaar bent, kunt u Forms Portal, de gebruikersinterface voor AEM Forms, aanpassen aan de metagegevens die u in uw organisatie gebruikt. Voor meer informatie over het Portaal van Forms, zie [&#x200B; Inleiding aan het publiceren van vormen op een portaal &#x200B;](../../forms/using/introduction-publishing-forms.md).

## Metagegevens in AEM Forms {#metadata-in-aem-forms}

In AEM Forms is de lijst met metagegevenseigenschappen die aan een element zijn gekoppeld, afhankelijk van het type. Als u bovendien een aangepaste eigenschap voor metagegevens toevoegt, wordt deze toegevoegd aan alle elementen van het type waarop de aangepaste metagegevens zijn toegevoegd.

### Elementen {#asset-types}

De volgende elementtypen worden ondersteund in AEM Forms:

* Formuliersjablonen (XFA-formulieren)
* PDF forms
* Document (platte PDF)
* Aangepaste formulieren
* Bronnen
* XFS

#### Uitgebreide lijst met metagegevens {#extensive-list-of-metadata}

Hieronder volgt een uitgebreide lijst met metagegevenseigenschappen die in AEM Forms worden ondersteund:

<table>
 <tbody> 
  <tr> 
   <td><strong>Eigenschapnaam</strong></td> 
   <td><strong>Type element</strong></td> 
   <td><strong> Beschrijving </strong><br /> </td> 
  </tr> 
  <tr> 
   <td>Titel</td> 
   <td>Alles behalve bron</td> 
   <td>Naam van formulier weergeven.<br /> </td> 
  </tr> 
  <tr> 
   <td>Beschrijving</td> 
   <td>Alles behalve bron</td> 
   <td>Beschrijving van het formulier. De gebruiker kan deze waarde specificeren.<br /> </td> 
  </tr> 
  <tr> 
   <td>Type</td> 
   <td>Alles</td> 
   <td><p>Een alleen-lezen waarde die het type element aangeeft. Deze kan een van de volgende waarden hebben:</p> 
    <ul> 
     <li>Formuliersjabloon</li> 
     <li>PDF-formulier, PDF-formulier (Acrobat) of PDF-formulier (ondertekend)</li> 
     <li>Document, document (ondertekend)</li> 
     <li>Aangepast formulier</li> 
     <li>Bron</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Gemaakt</td> 
   <td>Alles</td> 
   <td>Een alleen-lezen waarde die de tijd van het maken van het element aangeeft.</td> 
  </tr> 
  <tr> 
   <td>Laatste wijzigingsdatum</td> 
   <td>Alles</td> 
   <td>Een alleen-lezen waarde die de tijd aangeeft waarop het element voor het laatst is gewijzigd.</td> 
  </tr> 
  <tr> 
   <td>Auteur</td> 
   <td>Alles behalve bron</td> 
   <td><p>Een alleen-lezen waarde die automatisch wordt berekend op basis van het formuliertype.</p> 
    <ul> 
     <li>PDF/Formuliersjabloon/Document - opgehaald uit het geüploade binaire bestand.</li> 
     <li>Adaptief formulier - Wordt bij het maken van het formulier door de gebruiker aangemeld.</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Status</td> 
   <td>Alles behalve bron</td> 
   <td><p> Een alleen-lezen waarde die een van de volgende statussen van een formulier definieert:</p> 
    <ul> 
     <li>Geen waarde: als een formulier nog nooit is gepubliceerd.</li> 
     <li>Gepubliceerd: wanneer een formulier wordt gepubliceerd.</li> 
     <li>Gewijzigd: wanneer een formulier is gewijzigd nadat het eenmaal is gepubliceerd.</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Laatste publicatiedatum</td> 
   <td>Alles behalve bron</td> 
   <td>Een alleen-lezen waarde die aangeeft op welk tijdstip het formulier het laatst is gepubliceerd.</td> 
  </tr> 
  <tr> 
   <td>Publish aan/uit-tijd</td> 
   <td>Alles behalve bron</td> 
   <td><p>Tijdstip waarop het formulier volgens de planning automatisch moet worden gepubliceerd/gepubliceerd. De gebruiker stelt deze waarde in bij het bewerken van metagegevens.</p> 
    <ul> 
     <li>Zowel Publish Aan als Uit moet langer zijn dan de huidige datum. </li> 
     <li>Publish Off time dient na publicatie On time te zijn. </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>URL verzenden</td> 
   <td><p>Formuliersjabloon</p> <p>PDF-formulier</p> </td> 
   <td><p>Een door de gebruiker opgegeven URL configureren voor het verzenden van formuliergegevens naar een servlet.</p> <p>Verzenden van URL kan worden geconfigureerd met een van de volgende methoden, vermeld in volgorde van prioriteit:</p> 
    <ul> 
     <li>Geef een verzend-URL rechtstreeks op in een formuliersjabloon met de knop HTTP verzenden tijdens het maken van een XFA-formulier in AEM Forms Designer.</li> 
     <li>Selecteer in de gebruikersinterface van AEM Forms een formulier en geef een verzendURL op bij het bewerken van de eigenschappen van metagegevens.</li> 
     <li>Bewerk in Forms Portal de component Search &amp; Lister en geef een verzendURL op onder het tabblad Formulierkoppeling.</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>HTML-renderprofiel</td> 
   <td>Formuliersjabloon</td> 
   <td>Het HTML-renderprofiel dat wordt gebruikt bij het renderen van een formuliersjabloon in HTML-indeling.</td> 
  </tr> 
  <tr> 
   <td>Renderindeling</td> 
   <td><p>Formuliersjabloon</p> <p>Aangepast formulier</p> </td> 
   <td><p>Met deze optie kan de gebruiker de renderindeling van het formulier opgeven wanneer de formulieren worden gepubliceerd:</p> 
    <ul> 
     <li>HTML</li> 
     <li>PDF</li> 
     <li>Beide</li> 
    </ul> <p>Deze optie wordt gebruikt om de weergave-indeling van de formulieren alleen te beperken op het formulierportaal waar deze zichtbaar zijn voor de eindgebruiker.</p> </td> 
  </tr> 
  <tr> 
   <td>Tags</td> 
   <td>Alles behalve bron</td> 
   <td>Labels die aan het formulier zijn gekoppeld, zodat u snel en gemakkelijk kunt zoeken.</td> 
  </tr> 
  <tr> 
   <td>Verwijzingen</td> 
   <td><p>Aangepast formulier</p> <p>Formuliersjabloon</p> <p>Bron</p> </td> 
   <td><p>Lijst met elementen (andere formulieren of bronnen) waarmee dit formulier is gerelateerd. Deze activa kunnen in de volgende twee categorieën vallen:</p> 
    <ul> 
     <li>Zie: Assets waarnaar het huidige formulier verwijst.</li> 
     <li>Verwezen door: Assets die naar het huidige element verwijzen.</li> 
    </ul> <p>Deze activa worden getoond als verbindingen en hun meta-gegevens kunnen direct worden betreden door hen te klikken.<br /> </p> </td> 
  </tr> 
  <tr> 
   <td>Selectie van formuliermodel (XDP/XSD)</td> 
   <td>Aangepast formulier</td> 
   <td><p>Hiermee geeft u aan welk formuliermodel wordt gebruikt bij het ontwerpen van het adaptieve formulier. Deze eigenschap kan de volgende waarden hebben:</p> 
    <ul> 
     <li>Formuliersjabloon: een formuliersjabloon is geselecteerd uit de formuliersjablonen in de gegevensopslagruimte. Deze waarde kan worden bijgewerkt.</li> 
     <li>XML-schema: er wordt een XSD-bestand geüpload. Deze waarde kan worden bijgewerkt.</li> 
     <li>Geen</li> 
    </ul> 
    <div>
      Een formuliermodel dat is geselecteerd, kan worden bijgewerkt, maar niet worden verwijderd. 
    </div> </td> 
  </tr> 
 </tbody> 
</table>

## Metagegevens van formulieren weergeven {#view-form-metadata}

Assets heeft bestaande eigenschapswaarden die kunnen worden weergegeven in de alleen-lezen modus. Deze metagegevens zijn afkomstig bij het uploaden van het formulier of het maken van het formulier.

1. Navigeer naar de locatie van het element waarvan u de metagegevens wilt weergeven.

1. Open de eigenschappenpagina op een van de volgende manieren:

   1. Klik het pictogram van de Eigenschappen van de Mening ![&#x200B; e_reviewmode_properties_n &#x200B;](assets/e_reviewmode_properties_n.png) van Snelle Acties.

      >[!NOTE]
      >
      >Snelle acties zijn de actiepunten die over een duimnagel worden getoond wanneer de muiswijzer.

   1. Selecteer de vorm en klik het pictogram van de Eigenschappen van de Mening ![&#x200B; e_reviewmode_properties_n &#x200B;](assets/e_reviewmode_properties_n.png) dat in de toolbar verschijnt.
   1. Navigeer naar de pagina met formulierdetails door op de miniatuur van het formulier te klikken wanneer u niet in de selectiemodus werkt. Nu, klik het {![&#128279;](assets/aem6forms_eye_viewon.png) oogpictogram 0} aem6forms_eye_viewon op het hogere recht, en klik dan Eigenschappen in de lijst onder het.

1. De bezitspagina die opent toont een schema dat slechts die meta-gegevenseigenschappen bevat die één of andere waarde houden.

   De eigenschappenpagina heeft een werkbalk met twee actiepictogrammen:

   * Bewerken: ![&#x200B; aem6forms_edit &#x200B;](assets/aem6forms_edit.png) geeft de waarden van het meta-gegevensbezit uit
   * Mening: ![&#x200B; aem6forms_eye_viewon &#x200B;](assets/aem6forms_eye_viewon.png) navigeer aan de pagina van de vormdetails, die de vorm op de voorproefwijze opent.

   Het inhoudgedeelte wordt in twee delen verdeeld:

   * Het linkerdeelvenster bevat een miniatuur van het formulier
   * Het rechterdeelvenster bevat eigenschappen van metagegevens in de alleen-lezen modus, verdeeld over verschillende tabbladen.

## Waarden van metagegevens van formulieren toevoegen/bijwerken {#add-update-form-metadata-values}

U kunt de waarde van bestaande eigenschappen van metagegevens bewerken of nieuwe waarden toevoegen aan een bestaand veld voor eigenschappen van metagegevens (bijvoorbeeld wanneer een metagegevensveld leeg is).

### Waarden voor metagegevenseigenschappen bijwerken {#update-metadata-property-values}

1. Voer de stappen in de vorige sectie uit om de eigenschappenpagina te openen waarop bestaande metagegevens van het geselecteerde formulier kunnen worden weergegeven.

1. Van de toolbar, klik uitgeven pictogram ![&#x200B; aem6forms_edit &#x200B;](assets/aem6forms_edit.png) om de wijze van de pagina van read-only te veranderen in lees-schrijf.

1. De eigenschappenpagina die wordt geopend, bevat een schema dat een combinatie bevat van bewerkbare invoervelden en statische tekst.

1. De eigenschappen die worden weergegeven in statische tekst zijn de eigenschappen die u niet kunt bewerken.

1. U kunt naar andere tabbladen navigeren om invoervelden te zoeken voor eigenschappen van metagegevens die onder deze tabbladen worden geplaatst.

   Deze pagina heeft een werkbalk met twee actiepictogrammen die afwijken van die in de weergavemodus:

   * Annuleren: ![&#x200B; aem6forms_close &#x200B;](assets/aem6forms_close.svg_w24.png) annuleert om het even welke veranderingen die aan waarden van het meta-gegevensbezit tot nu toe worden aangebracht
   * Gereed: ![&#x200B; aem6forms_check &#x200B;](assets/aem6forms_check.png) sparen alle veranderingen die aan waarden van het meta-gegevensbezit tot dusver worden aangebracht

   Met beide handelingen wordt de gebruiker weer naar de alleen-lezen modus geleid van de eigenschappenpagina die de bijgewerkte waarden bevat.

### De miniatuur van het formulier bijwerken {#update-the-form-thumbnail}

In het linkerdeelvenster op de pagina Eigenschappen wordt de miniatuur van het formulier weergegeven. Standaard wordt de miniatuur weergegeven die wordt gegenereerd bij het maken van het formulier (adaptief formulier) of bij het uploaden van het formulier.

Voor alle formuliertypen kunt u een afbeelding uploaden door op **[!UICONTROL Upload Image]** te klikken en naar een afbeeldingsbestand in de lokale map te bladeren. De geselecteerde afbeelding wordt gebruikt als een miniatuur in plaats van de standaardafbeelding.

Voor adaptieve formulieren is extra functionaliteit beschikbaar, waarmee de gebruiker een miniatuur kan genereren als momentopname van de huidige aangepaste formuliervoorvertoning. Aangezien AEM Forms ook het schrijven van adaptieve formulieren ondersteunt, kan het voorbeeld van het adaptieve formulier elke keer dat u het adaptieve formulier wijzigt, veranderen. Met deze functie voor het genereren van een miniatuur krijgt u een nieuwe miniatuur voor het adaptieve formulier op basis van de huidige voorbeeldstatus. Klik op **[!UICONTROL Generate Preview]** om deze handeling uit te voeren.

>[!NOTE]
>
>* Gebruik een vierkante afbeelding voor de miniatuur. Wanneer u een niet-vierkante afbeelding gebruikt en de miniatuur in de lijstweergave weergeeft, wordt de miniatuur afgekapt weergegeven.
>* Nadat een nieuwe afbeelding is geüpload of gegenereerd, wordt de miniatuur vervangen door deze afbeelding en kan deze niet opnieuw worden ingesteld op de vorige afbeelding.
>

## Aangepaste metagegevens toevoegen {#add-custom-metadata}

Naast de metagegevens die in het tekstvak worden vermeld, ondersteunt AEM Forms nieuwe aangepaste metagegevens.

Er is een hulpprogramma (de Editor voor metagegevensschema&#39;s) beschikbaar waarmee u het schema voor de indeling van metagegevens kunt definiëren. Dit is de indeling van wat wordt weergegeven op de pagina **[!UICONTROL Properties]** van een formulier. Met de Metagegevensschemaeditor kunt u een aangepast schema voor uw elementen toevoegen of wijzigen.

AEM Forms stelt de metagegevensschema&#39;s van de ondersteunde formuliertypen in dit gereedschap beschikbaar. Op deze manier hebt u toegang tot deze schema&#39;s en kunt u aangepaste eigenschappen toevoegen met gebruik van de functionaliteit in de editor voor het metagegevensschema.

### Navigeren door de editor voor het metagegevensschema {#navigate-the-metadata-schema-editor}

1. Navigeer naar **[!UICONTROL Tools > Assets > Metadata Schemas]** .

1. Klik op **[!UICONTROL forms]** in de lijst met schemaformulieren.

1. Klik in de lijst die wordt geopend op het elementtype waarvoor u aangepaste metagegevens wilt toevoegen.

   >[!NOTE]
   >
   >Deze schema&#39;s bevatten eigenschappen van meta-gegevens die buiten doos worden verstrekt en moeten niet worden veranderd/worden uitgegeven (het selecteren van controledoos en het klikken geeft van toolbar uit) om functionele kwesties te vermijden.

1. Elk type element waarop u klikt, opent een lijst met de optie `extendedmetadata` . Bewerk dit schema.

1. Selecteer checkbox naast `extendedmetadata` en klik dan uitgeven ![&#x200B; aem6forms_edit &#x200B;](assets/aem6forms_edit.png) pictogram dat in de toolbar verschijnt.

1. AEM Forms opent de editor/formulierbuilder voor metagegevens van het geselecteerde elementtype (in dit geval adaptief formulier).

   ![&#x200B; het schemaredacteur van Meta-gegevens voor het Adaptieve type van Vorm &#x200B;](assets/metadata-schema-editor-for-adaptive-form-type.png)

   Metagegevenseditor

   1. Het linkerdeelvenster bevat secties met tabbladen waarin de velden zijn geplaatst en in het rechterdeelvenster worden alle beschikbare UI-componenten en de eigenschappen van het veld weergegeven die in het linkerdeelvenster zijn geselecteerd.

   1. De vergrendelde sectie kan niet worden bewerkt en bevat velden voor alle metagegevenseigenschappen die in het vak worden opgegeven.

   1. U kunt extra tabbladen toevoegen door op het plus-symbool te klikken.

   1. U kunt een aangepast veld van het gewenste type toevoegen door de veldcomponent van de sectie **[!UICONTROL Build Form]** naar de schemapagina te slepen.
   1. U kunt de specificaties voor dit veld opgeven in de sectie **[!UICONTROL Settings]** nadat u op het veld hebt geklikt.

### Aangepaste metagegevenseigenschap toevoegen in schema-editor {#add-custom-metadata-property-in-schema-editor}

1. Navigeer naar het tabblad (bestaand of nieuw) waar u de aangepaste eigenschap wilt toevoegen.

1. Sleep een component van het gewenste type van de **[!UICONTROL Build Form]** sectie aan linkerpaneel en plaats bij een geschikte plaats.

   >[!NOTE]
   >
   >U kunt de vergrendelde secties niet verplaatsen, maar u kunt de component in een van de lege ruimten plaatsen.

1. Klik op een component die u net hebt gesleept. Vul op het tabblad Instellingen dat in het rechterdeelvenster wordt geopend de gegevens in voor de volgende velden:

   1. Geef een veldlabel op dat wordt gebruikt als een weergavenaam boven het veld dat in het schema wordt geplaatst (bijvoorbeeld: Department)
   1. Onder Kaart aan bezitsgebied, kunt u een vooraf ingevulde waarde zien **&#39;./jcr:content/metadata/default&#39;**. Verander het &quot;**gebrek**&quot;in een gewenste bezitsnaam, die wordt gebruikt om het bezit in crx bewaarplaats (bijvoorbeeld: &quot;./jcr:content/metadata/department&#39;)

      >[!NOTE]
      >
      >Wijzig het voorvoegsel ‘ niet./jcr:content/metadata/’ as it define the path where the property is stored.
      >
      >De eigenschapsnaam moet ook uniek zijn om te voorkomen dat waarden worden geschreven voor twee of meer eigenschappen op dezelfde locatie in de opslagplaats. Het wordt daarom aanbevolen de waarde &#39;default&#39; te wijzigen.

   1. Vul andere instellingen in op basis van vereisten. Selecteer bijvoorbeeld de optie Vereist als u het veld verplicht wilt maken.
   1. Om een gebied te schrappen u toevoegde, selecteer het gebied en klik dan schrapping ![&#x200B; schrapping-1 &#x200B;](assets/delete-1.png) pictogram.

1. Voer indien nodig stap 1-3 uit om een andere eigenschap toe te voegen.
1. Klik **Gedaan** na het aanbrengen van alle veranderingen.

   U hebt een aangepaste eigenschap voor metagegevens toegevoegd.

Alle adaptieve formulieren in AEM Forms bevatten nu deze extra eigenschap voor metagegevens. U kunt het van de eigenschappen pagina uitgeven.
