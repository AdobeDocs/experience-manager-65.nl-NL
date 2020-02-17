---
title: Metagegevens van formulieren beheren
seo-title: Metagegevens van formulieren beheren
description: Met metagegevens kunt u elementen gemakkelijker indelen en ordenen en gebruikers die op zoek zijn naar een bepaald middel helpen.
seo-description: Met metagegevens kunt u elementen gemakkelijker indelen en ordenen en gebruikers die op zoek zijn naar een bepaald middel helpen.
uuid: d982df6f-a256-4bad-868f-74fcd08350f8
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-manager
discoiquuid: ba571f8e-8bd3-48eb-82e1-c93b14ffe44a
docset: aem65
translation-type: tm+mt
source-git-commit: 06335b9a85414b6b1141dd19c863dfaad0812503

---


# Metagegevens van formulieren beheren{#manage-form-metadata}

## Overzicht  {#overview-nbsp}

Met metagegevens kunt u elementen gemakkelijker indelen en ordenen en gebruikers die op zoek zijn naar een bepaald middel helpen.

AEM Forms biedt standaard een gedefinieerde set metagegevens voor elk elementtype. Naast de standaardmetagegevens kunt u ook aangepaste metagegevens toevoegen aan elk elementtype. Met AEM Forms beschikt u ook over de juiste middelen om al deze metagegevens efficiënt voor uw formulieren te maken, beheren en uit te wisselen.

Als u een ontwikkelaar of site-eigenaar bent, kunt u Forms Portal, de gebruikersinterface voor AEM Forms aanpassen aan de metagegevens die u in uw organisatie gebruikt. Zie [Inleiding tot het publiceren van formulieren op een portal](../../forms/using/introduction-publishing-forms.md)voor meer informatie over Forms Portal.

## Metagegevens in AEM-formulieren {#metadata-in-aem-forms}

In AEM Forms is de lijst met eigenschappen van metagegevens die aan een element zijn gekoppeld, afhankelijk van het type. Als u bovendien een aangepaste eigenschap voor metagegevens toevoegt, wordt deze toegevoegd aan alle elementen van het type waarop de aangepaste metagegevens zijn toegevoegd.

### Elementen {#asset-types}

De volgende elementtypen worden ondersteund in AEM-formulieren:

* Formuliersjablonen (XFA-formulieren)
* PDF-formulieren
* Document (vlakke PDF&#39;s)
* Aangepaste formulieren
* Bronnen
* XFS

#### Uitgebreide lijst met metagegevens {#extensive-list-of-metadata}

Hieronder volgt een uitgebreide lijst met metagegevenseigenschappen die worden ondersteund in AEM Forms:

<table>
 <tbody> 
  <tr> 
   <td><strong>Eigenschapnaam</strong></td> 
   <td><strong>Type element</strong></td> 
   <td><strong>Beschrijving</strong><br /> </td> 
  </tr> 
  <tr> 
   <td>Titel</td> 
   <td>Alles behalve bron</td> 
   <td>De naam van het formulier weergeven.<br /> </td> 
  </tr> 
  <tr> 
   <td>Beschrijving</td> 
   <td>Alles behalve bron</td> 
   <td>Beschrijving van het formulier. De gebruiker kan deze waarde opgeven.<br /> </td> 
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
     <li>Resource</li> 
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
   <td>Author</td> 
   <td>Alles behalve bron</td> 
   <td><p>Een alleen-lezen waarde die automatisch wordt berekend op basis van het formuliertype.</p> 
    <ul> 
     <li>PDF/Form-sjabloon/Document - opgehaald uit het geüploade binaire bestand.</li> 
     <li>Adaptief formulier - Wordt bij het maken van het formulier door de gebruiker aangemeld.</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Status</td> 
   <td>Alles behalve bron</td> 
   <td><p> Een alleen-lezen waarde die een van de volgende statussen van een formulier definieert:</p> 
    <ul> 
     <li>Geen waarde: Als een formulier nog nooit is gepubliceerd.</li> 
     <li>Gepubliceerd: Wanneer een formulier wordt gepubliceerd.</li> 
     <li>Gewijzigd: Wanneer een formulier is gewijzigd nadat het eenmaal is gepubliceerd.</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Laatste publicatiedatum</td> 
   <td>Alles behalve bron</td> 
   <td>Een alleen-lezen waarde die aangeeft op welk tijdstip het formulier het laatst is gepubliceerd.</td> 
  </tr> 
  <tr> 
   <td>Aan/uit-tijd publiceren</td> 
   <td>Alles behalve bron</td> 
   <td><p>Tijdstip waarop het formulier volgens de planning automatisch moet worden gepubliceerd/gepubliceerd. De gebruiker stelt deze waarde in bij het bewerken van metagegevens.</p> 
    <ul> 
     <li>Zowel de functie Publiceren aan als de functie Uittijd moet na de huidige datum vallen. </li> 
     <li>Publiceren buiten de tijd moet na publicatie op tijd plaatsvinden. </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>URL verzenden</td> 
   <td><p>Formuliersjabloon</p> <p>PDF-formulier</p> </td> 
   <td><p>Een door de gebruiker opgegeven URL configureren voor het verzenden van formuliergegevens naar een servlet.</p> <p>Verzenden van URL kan worden geconfigureerd met een van de volgende methoden, vermeld in volgorde van prioriteit:</p> 
    <ul> 
     <li>Geef een verzendURL rechtstreeks op in een formuliersjabloon met de knop HTTP verzenden terwijl u een XFA-formulier maakt in AEM Forms Designer.</li> 
     <li>Selecteer een formulier in de gebruikersinterface van AEM Forms en geef een verzendURL op bij het bewerken van de metagegevenseigenschappen.</li> 
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
   <td><p>Aangepast formulier</p> <p>Formuliersjabloon</p> <p>Resource</p> </td> 
   <td><p>Lijst met elementen (andere formulieren of bronnen) waarmee dit formulier is gerelateerd. Deze activa kunnen in de volgende twee categorieën vallen:</p> 
    <ul> 
     <li>Verwijst naar: Elementen waarnaar het huidige formulier verwijst.</li> 
     <li>Verwezen door: Activa die verwijzen naar het huidige actief.</li> 
    </ul> <p>Deze elementen worden als koppelingen weergegeven en de bijbehorende metagegevens zijn rechtstreeks toegankelijk door erop te klikken.<br /> </p> </td> 
  </tr> 
  <tr> 
   <td>Selectie van formuliermodel (XDP/XSD)</td> 
   <td>Aangepast formulier</td> 
   <td><p>Hiermee geeft u aan welk formuliermodel wordt gebruikt bij het ontwerpen van het adaptieve formulier. Deze eigenschap kan de volgende waarden hebben:</p> 
    <ul> 
     <li>Formuliersjabloon: Een formuliersjabloon wordt geselecteerd uit de sjablonen die in de gegevensopslagruimte aanwezig zijn. Deze waarde kan worden bijgewerkt.</li> 
     <li>XML-schema: Er wordt een XSD-bestand geüpload. Deze waarde kan worden bijgewerkt.</li> 
     <li>Geen</li> 
    </ul> 
    <div>
      Een formuliermodel dat is geselecteerd, kan worden bijgewerkt, maar niet worden verwijderd. 
    </div> </td> 
  </tr> 
 </tbody> 
</table>

## Metagegevens van formulieren weergeven {#view-form-metadata}

Elementen hebben bestaande eigenschapswaarden, die kunnen worden weergegeven in de alleen-lezen modus. Deze metagegevens zijn afkomstig bij het uploaden van het formulier of het maken van het formulier.

1. Navigeer naar de locatie van het element waarvan u de metagegevens wilt weergeven.

1. Open de eigenschappenpagina op een van de volgende manieren:

   1. Klik op het pictogram Eigenschappen van weergave ![e_reviewmode_properties_n](assets/e_reviewmode_properties_n.png) vanuit Snelle handelingen.

      >[!NOTE]
      >
      >Snelle acties zijn de actiepunten die over een duimnagel worden getoond wanneer de muiswijzer.

   1. Selecteer het formulier en klik op het pictogram Eigenschappen van weergave ![e_reviewmode_properties_n](assets/e_reviewmode_properties_n.png) op de werkbalk.
   1. Navigeer naar de pagina met formulierdetails door op de miniatuur van het formulier te klikken wanneer u niet in de selectiemodus werkt. Klik nu op het oogpictogram ![aem6forms_eye_viewon](assets/aem6forms_eye_viewon.png) rechtsboven en klik vervolgens op Eigenschappen in de lijst eronder.

1. De bezitspagina die opent toont een schema dat slechts die meta-gegevenseigenschappen bevat die één of andere waarde houden.

   De eigenschappenpagina heeft een werkbalk met twee actiepictogrammen:

   * Bewerken: ![aaem6forms_edit](assets/aem6forms_edit.png) geef de waarden van het meta-gegevensbezit uit
   * Weergave: Met ![naam6forms_eye_viewon](assets/aem6forms_eye_viewon.png) navigeert u naar de pagina met formulierdetails. Hiermee wordt het formulier geopend in de voorbeeldmodus.
   Het inhoudgedeelte wordt in twee delen verdeeld:

   * Het linkerdeelvenster bevat een miniatuur van het formulier
   * Het rechterdeelvenster bevat eigenschappen van metagegevens in de alleen-lezen modus, verdeeld over verschillende tabbladen.


## Waarden van metagegevens van formulieren toevoegen/bijwerken {#add-update-form-metadata-values}

U kunt de waarde van bestaande eigenschappen van metagegevens bewerken of nieuwe waarden toevoegen aan een bestaand veld voor eigenschappen van metagegevens (bijvoorbeeld wanneer een metagegevensveld leeg is).

### Waarden voor metagegevenseigenschappen bijwerken {#update-metadata-property-values}

1. Voer de stappen in de vorige sectie uit om de eigenschappenpagina te openen waarop bestaande metagegevens van het geselecteerde formulier kunnen worden weergegeven.

1. Klik op het bewerkingspictogram ![aaem6forms_edit](assets/aem6forms_edit.png) op de werkbalk om de modus van de pagina te wijzigen van alleen-lezen in lezen/schrijven.

1. De eigenschappenpagina die wordt geopend, bevat een schema dat een combinatie bevat van bewerkbare invoervelden en statische tekst.

1. De eigenschappen die worden weergegeven in statische tekst zijn de eigenschappen die u niet kunt bewerken.

1. U kunt naar andere tabbladen navigeren om invoervelden te zoeken voor eigenschappen van metagegevens die onder deze tabbladen worden geplaatst.

   Deze pagina heeft een werkbalk met twee actiepictogrammen die afwijken van die in de weergavemodus:

   * Annuleren: ![aem6forms_close](assets/aem6forms_close.svg_w24.png) Alle wijzigingen in eigenschapswaarden van metagegevens tot nu toe annuleren
   * Gereed: ![aem6forms_check](assets/aem6forms_check.png) Alle wijzigingen opslaan die tot nu toe in eigenschapswaarden voor metagegevens zijn aangebracht
   Met beide handelingen wordt de gebruiker weer naar de alleen-lezen modus geleid van de eigenschappenpagina die de bijgewerkte waarden bevat.

### De miniatuur van het formulier bijwerken {#update-the-form-thumbnail}

In het linkerdeelvenster op de pagina Eigenschappen wordt de miniatuur van het formulier weergegeven. Standaard wordt de miniatuur weergegeven die wordt gegenereerd bij het maken van het formulier (adaptief formulier) of bij het uploaden van het formulier.

Voor alle formuliertypen kunt u een afbeelding uploaden door op Afbeelding **** uploaden te klikken en naar een afbeeldingsbestand in de lokale map te bladeren. De geselecteerde afbeelding wordt gebruikt als een miniatuur in plaats van de standaardafbeelding.

Voor adaptieve formulieren is extra functionaliteit beschikbaar, waarmee de gebruiker een miniatuur kan genereren als momentopname van de huidige aangepaste formuliervoorvertoning. Aangezien AEM Forms ook het ontwerpen van adaptieve formulieren ondersteunt, kan het voorbeeld van het adaptieve formulier elke keer dat u het adaptieve formulier wijzigt, veranderen. Met deze functie voor het genereren van een miniatuur krijgt u een nieuwe miniatuur voor het adaptieve formulier op basis van de huidige voorbeeldstatus. Klik op Voorvertoning **** genereren om deze handeling uit te voeren.

>[!NOTE]
>
>* Gebruik een vierkante afbeelding voor de miniatuur. Wanneer u een niet-vierkante afbeelding gebruikt en de miniatuur in de lijstweergave weergeeft, wordt de miniatuur afgekapt weergegeven.
>* Nadat een nieuwe afbeelding is geüpload of gegenereerd, wordt de miniatuur vervangen door deze afbeelding en kan deze niet opnieuw worden ingesteld op de vorige afbeelding.
>



## Aangepaste metagegevens toevoegen {#add-custom-metadata}

Naast de metagegevens die in het tekstvak worden vermeld, ondersteunt AEM Forms nieuwe aangepaste metagegevens.

Er is een hulpmiddel (de Editor voor het metagegevensschema) beschikbaar waarmee u het schema voor de indeling van metagegevens kunt definiëren. Dit is de indeling van wat wordt weergegeven op de pagina **[!UICONTROL Eigenschappen]** van een formulier. Met de Metagegevensschemaeditor kunt u een aangepast schema voor uw elementen toevoegen of wijzigen.

In AEM Forms worden de metagegevensschema&#39;s van de ondersteunde formuliertypen in dit gereedschap weergegeven. Op deze manier hebt u toegang tot deze schema&#39;s en kunt u aangepaste eigenschappen toevoegen met gebruik van de functionaliteit in de editor voor het metagegevensschema.

### Navigeren door de editor voor het metagegevensschema {#navigate-the-metadata-schema-editor}

1. Ga naar **[!UICONTROL Gereedschappen > Middelen > Metagegevensschema&#39;s]**.

1. Klik op **[!UICONTROL formulieren]** in de lijst met schemaformulieren.

1. Klik in de lijst die wordt geopend op het elementtype waarvoor u aangepaste metagegevens wilt toevoegen.

   >[!NOTE]
   >
   >Deze schema&#39;s bevatten eigenschappen van meta-gegevens die buiten doos worden verstrekt en moeten niet worden veranderd/worden uitgegeven (het selecteren van controledoos en het klikken geeft van toolbar uit) om functionele kwesties te vermijden.

1. Elk type element waarop u klikt, opent een lijst met de `extendedmetadata` optie. Bewerk dit schema.

1. Schakel het selectievakje naast `extendedmetadata` en klik op het pictogram ![Aem6forms_edit](assets/aem6forms_edit.png) bewerken op de werkbalk.

1. Met AEM Forms opent u de editor/formulierbuilder voor metagegevens van het geselecteerde elementtype (in dit geval een adaptief formulier).

   ![Schema-editor voor metagegevens voor adaptief formuliertype](assets/metadata-schema-editor-for-adaptive-form-type.png)

   Metagegevenseditor

   1. Het linkerdeelvenster bevat secties met tabbladen waarin de velden zijn geplaatst en in het rechterdeelvenster worden alle beschikbare UI-componenten en de eigenschappen van het veld weergegeven die in het linkerdeelvenster zijn geselecteerd.

   1. De vergrendelde sectie kan niet worden bewerkt en bevat velden voor alle metagegevenseigenschappen die in het vak worden opgegeven.

   1. U kunt extra tabbladen toevoegen door op het plus-symbool te klikken.

   1. U kunt een aangepast veld van het gewenste type toevoegen door de veldcomponent vanuit de sectie Formulier **** samenstellen naar de schemapagina te slepen.
   1. U kunt de specificaties voor dit veld opgeven in de sectie **[!UICONTROL Instellingen]** nadat u op het veld hebt geklikt.

### Aangepaste metagegevenseigenschap toevoegen in schema-editor {#add-custom-metadata-property-in-schema-editor}

1. Navigeer naar het tabblad (bestaand of nieuw) waar u de aangepaste eigenschap wilt toevoegen.

1. Sleep een component van het gewenste type van de sectie van de Vorm **[!UICONTROL van de]** Bouwstijl aan linkerpaneel en plaats bij een geschikte plaats.

   >[!NOTE]
   >
   >U kunt de vergrendelde secties niet verplaatsen, maar u kunt de component in een van de lege ruimten plaatsen.

1. Klik op een component die u net hebt gesleept. Vul op het tabblad Instellingen dat in het rechterdeelvenster wordt geopend de gegevens in voor de volgende velden:

   1. Geef een veldlabel op dat wordt gebruikt als een weergavenaam boven het veld dat in het schema wordt geplaatst (bijvoorbeeld: Afdeling)
   1. Onder Kaart aan bezitsgebied, kunt u een vooraf ingevulde waarde zien **&#39;./jcr:content/metadata/default&#39;**. Verander de &quot;**gebrek**&quot;in een gewenste bezitsnaam, die wordt gebruikt om het bezit in crx bewaarplaats op te slaan (bijvoorbeeld: &quot;./jcr:content/metadata/department&#39;)

      >[!NOTE]
      >
      >Wijzig het voorvoegsel ‘ niet./jcr:content/metadata/’ as it define the path where the property is stored.
      >
      >De eigenschapsnaam moet ook uniek zijn om te voorkomen dat waarden worden geschreven voor twee of meer eigenschappen op dezelfde locatie in de opslagplaats. Het wordt daarom aanbevolen de waarde &#39;default&#39; te wijzigen.

   1. Vul andere instellingen in op basis van vereisten. Bijvoorbeeld: Selecteer de optie Vereist als u het veld verplicht wilt maken.
   1. Als u een toegevoegd veld wilt verwijderen, selecteert u het veld en klikt u op het pictogram ![delete-1](assets/delete-1.png) .

1. Voer indien nodig stap 1-3 uit om een andere eigenschap toe te voegen.
1. Klik op **Gereed** nadat u alle wijzigingen hebt aangebracht.

   U hebt een aangepaste eigenschap voor metagegevens toegevoegd.

Alle adaptieve formulieren in AEM Forms bevatten nu deze extra eigenschap voor metagegevens. U kunt het van de eigenschappen pagina uitgeven.
