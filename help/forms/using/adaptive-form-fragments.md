---
title: Adaptieve formulierfragmenten
seo-title: Adaptieve formulierfragmenten
description: Aangepaste formulieren bieden een mechanisme om een formuliersegment te maken, zoals een deelvenster of een groep velden, zoals het in elk adaptief formulier wordt gebruikt. U kunt een bestaand deelvenster ook opslaan als fragment.
seo-description: Aangepaste formulieren bieden een mechanisme om een formuliersegment te maken, zoals een deelvenster of een groep velden, zoals het in elk adaptief formulier wordt gebruikt. U kunt een bestaand deelvenster ook opslaan als fragment.
uuid: bb4830b5-82a0-4026-9dae-542daed10e6f
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
discoiquuid: 1a32eb24-db3b-4fad-b1c7-6326b5af4e5e
docset: aem65
feature: Adaptive Forms
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '2076'
ht-degree: 0%

---


# Adaptieve formulierfragmenten{#adaptive-form-fragments}

Hoewel elk formulier voor een bepaald doel is ontworpen, zijn er in de meeste vormen enkele gangbare segmenten, zoals het verstrekken van persoonlijke gegevens zoals naam en adres, familiedetails, inkomstengegevens enzovoort. Formulierontwikkelaars moeten deze algemene segmenten telkens maken wanneer een nieuw formulier wordt gemaakt.

Adaptieve formulieren bieden een handig mechanisme om slechts eenmaal een formuliersegment als een deelvenster of een groep velden te maken en deze in adaptieve formulieren opnieuw te gebruiken. Deze herbruikbare en standalone segmenten worden adaptieve formulierfragmenten genoemd.

## Een fragment maken {#create-a-fragment}

U kunt een volledig aangepast formulierfragment maken of een deelvenster in een bestaand adaptief formulier opslaan als fragment.

### Geheel fragment maken {#create-fragment-from-scratch}

1. Meld u aan bij de AEM Forms-auteur-instantie op https://[*hostnaam*]:[*port*]/aem/forms.html.
1. Klik **Maken > Adaptief formulierfragment**.
1. Geef een titel, naam, beschrijving en tags voor het fragment op.

   >[!NOTE]
   >
   >Zorg ervoor dat u een unieke naam voor het fragment opgeeft. Als er al een ander fragment met dezelfde naam bestaat, kan het fragment niet worden gemaakt.

1. Klik om het tabblad **Formuliermodel** te openen en selecteer in het vervolgkeuzemenu **Selecteren uit** een van de volgende modellen voor het fragment:

   * **Geen**: Hiermee geeft u op het fragment helemaal opnieuw te maken zonder een formuliermodel te gebruiken.
   * **Formuliersjabloon**: Geeft op om het fragment te maken met een XDP-sjabloon die naar AEM Forms is geüpload. Selecteer de juiste XDP-sjabloon als het formuliermodel voor het fragment.

   ![Een adaptief formulier maken met een formuliersjabloon als model](assets/form-template-model.png)

   De subformulieren die als fragmenten zijn gemarkeerd in de geselecteerde formuliersjabloon, worden ook weergegeven. U kunt een subformulier voor adaptief formulierfragment selecteren in de vervolgkeuzelijst.

   ![Subformulieren selecteren uit de opgegeven formuliersjabloon](assets/fragment-subform.png)

   Daarnaast kunt u een adaptief formulierfragment maken met subformulieren die niet zijn gemarkeerd als fragmenten in de formuliersjabloon door de SOM-expressie voor het subformulier op te geven in de vervolgkeuzelijst.

   * **XML-schema**: Hiermee geeft u op het fragment te maken met een XML-schema dat naar AEM Forms is geüpload. U kunt een van de beschikbare XML-schema&#39;s uploaden of selecteren als het formuliermodel voor het fragment.

   ![Een adaptief formulierfragment maken op basis van een XML-schema als model](assets/xml-schema-model.png)

   U kunt ook een adaptief formulierfragment maken door in de vervolgkeuzelijst een complexType te selecteren dat aanwezig is in het geselecteerde schema.

   ![Selecteer een complex type van het gespecificeerde het schemamodel van XML](assets/complex-type.png)

1. Klik **Maken** en klik vervolgens **Openen** om het fragment met een standaardsjabloon te openen in de bewerkingsmodus.

In de bewerkingsmodus kunt u elke adaptieve formuliercomponent van het AEM hulpstuk naar het fragment slepen en neerzetten. Zie [Inleiding tot het ontwerpen van adaptieve formulieren](../../forms/using/introduction-forms-authoring.md) voor informatie over adaptieve formuliercomponenten.

Als u bovendien een XML-schema of XDP-formuliersjabloon hebt geselecteerd als het formuliermodel voor uw fragment, wordt een nieuw tabblad met de hiërarchie van het formuliermodel weergegeven in de zoeker naar inhoud. Hiermee kunt u formuliermodelelementen naar het fragment slepen en neerzetten. De toegevoegde formuliermodelelementen worden geconverteerd naar formuliercomponenten, terwijl de oorspronkelijke eigenschappen van de gekoppelde XDP of XSD behouden blijven.

### Deelvenster opslaan als een fragment {#save-panel-as-a-fragment}

1. Open een adaptief formulier met het deelvenster dat u wilt opslaan als adaptief formulierfragment.
1. Klik op **[!UICONTROL Save as Fragment]** in de werkbalk van het deelvenster. Het dialoogvenster Opslaan als fragment wordt geopend.

   >[!NOTE]
   >
   >Als het deelvenster dat u opslaat als fragment een onderliggend deelvenster bevat, worden deze opgenomen in het resulterende fragment.

1. Geef in het dialoogvenster Fragment maken de volgende informatie op:

   * **Naam**: Naam van het fragment. De standaardwaarde is de elementnaam van het deelvenster. Het is een verplicht veld.
      >[!NOTE]
      >
      >Zorg ervoor dat u een unieke naam voor het fragment opgeeft. Als er al een ander fragment met dezelfde naam bestaat, kan het fragment niet worden gemaakt.

   * **Titel**: Titel van het fragment. De standaardwaarde is de titel van het deelvenster.

   * **Omschrijving**: Beschrijving van het fragment.

   * **Tags**: Hiermee worden metagegevens voor het fragment gecodeerd.

   * **Doelpad**: Pad naar opslagplaats waar het fragment wordt opgeslagen. Als u geen pad opgeeft, wordt een knooppunt met dezelfde naam als dat van het fragment gemaakt naast het knooppunt dat het adaptieve formulier bevat. Het fragment wordt opgeslagen in dit knooppunt.

   * **Formuliermodel**: Afhankelijk van het formuliermodel voor het aangepaste formulier wordt in dit veld het  **XML-schema**, de  **formuliersjabloon** of  **Geen** weergegeven. Het is een niet-bewerkbaar veld.

   * **Hoofdmap** fragmentmodel: Wordt alleen weergegeven in op XSD gebaseerde adaptieve formulieren. Hiermee geeft u de basis voor het fragmentmodel op. U kunt **/** of het complexe type van XSD van drop-down kiezen. U kunt het fragment alleen opnieuw gebruiken in een ander adaptief formulier als u het complexe type selecteert als hoofdknooppunt van het fragmentmodel.
Als u **/** als hoofdmap van het fragmentmodel kiest, is de volledige XSD-structuur van het basismodel zichtbaar op het tabblad van het adaptieve formuliergegevensmodel. Voor een complexe hoofdmap van een fragmentmodel zijn alleen de afstammingen van het geselecteerde complexe type zichtbaar op het tabblad van het adaptieve formuliergegevensmodel.

   * **XSD-verwijzing**: Wordt alleen weergegeven in op XSD gebaseerde adaptieve formulieren. De locatie van het XML-schema wordt weergegeven.

   * **XDP Verwijzing**: Wordt alleen weergegeven in op XDP gebaseerde adaptieve formulieren. De locatie van de XDP-formuliersjabloon wordt weergegeven.

   ![save-fragment](assets/save-fragment.png)

   Dialoogvenster Opslaan als fragment

1. Klik **OK**.

   Het deelvenster wordt opgeslagen op de opgegeven of standaardlocatie in de opslagplaats. In het adaptieve formulier wordt het deelvenster vervangen door een momentopname van het fragment. Zoals hieronder wordt weergegeven, worden het deelvenster Algemene informatie en de onderliggende deelvensters Persoonlijke gegevens en Adres als een fragment opgeslagen.

   Als u het fragment wilt bewerken, klikt u op **[!UICONTROL Edit Asset]** op de werkbalk van het deelvenster. Het fragment wordt in de bewerkingsmodus op een nieuw tabblad of in een nieuw venster geopend.

   ![Fragment bewerken](assets/edit-fragment.png)

## Werken met fragmenten {#working-with-fragments}

### Fragmentweergave {#configure-fragment-appearance} configureren

Elk fragment dat u in adaptieve formulieren invoegt, wordt weergegeven als een voorlopige afbeelding. De plaatsaanduiding bevat titels van maximaal tien onderliggende deelvensters in het fragment. U kunt AEM Forms zo configureren dat het volledige fragment wordt weergegeven in plaats van de voorlopige afbeelding.

Voer de volgende stappen uit om volledige fragmenten in formulieren weer te geven:

1. Ga naar AEM webconsoleconfiguratiepagina op https:[*host*]:[*port*]/system/console/configMgr.

1. Zoek en klik op **[!UICONTROL Adaptive Form and Interactive Communication Web Channel Configuration]** om het te openen in bewerkingsmodus.
1. Schakel het selectievakje **[!UICONTROL Enable Placeholder in place of Fragment]** uit om volledige fragmenten te tonen in plaats van de voorlopige afbeelding.

### Een fragment invoegen in een adaptief formulier {#insert-a-fragment-in-an-adaptive-form}

De adaptieve formulierfragmenten die u maakt, worden weergegeven op het tabblad Adaptieve formulierfragmenten van de zoeker AEM inhoud. Een adaptief formulierfragment invoegen in een adaptief formulier:

1. Open het adaptieve formulier in de bewerkingsmodus waarin u een adaptief formulierfragment wilt invoegen.
1. Klik **Middelen** ![middelen-browser](assets/assets-browser.png) in de zijbalk. Selecteer **Adaptieve formulierfragmenten** in de elementenbrowser.

   U kunt er ook voor kiezen om alle adaptieve formulierfragmenten of filters weer te geven op basis van het formuliermodel (Formuliersjabloon, XML-schema of Standaard).

1. Sleep een adaptief formulierfragment naar het adaptieve formulier.

   >[!NOTE]
   >
   >Het adaptieve formulierfragment is niet ingeschakeld voor ontwerpen vanuit het adaptieve formulier. Bovendien kunt u een XSD-fragment niet gebruiken in een JSON-gebaseerd adaptief formulier en omgekeerd.

Het adaptieve formulierfragment wordt door verwijzing ingevoegd in het adaptieve formulier en wordt gesynchroniseerd met het standalone adaptieve formulierfragment. Dit betekent dat wanneer u het adaptieve formulierfragment bijwerkt, de wijzigingen worden doorgevoerd in alle adaptieve formulieren waarin het fragment wordt gebruikt.

### Een fragment in adaptieve vorm insluiten {#embed-a-fragment-in-adaptive-form}

U kunt een adaptief formulierfragment insluiten in een adaptief formulier door op **Element insluiten te klikken: &lt;*fragmentName*>** knoop op de paneeltoolbar van het toegevoegde fragment, zoals aangetoond in het volgende voorbeeldbeeld.

![Een formulierfragment insluiten in adaptieve vorm](assets/embed-fragment.png)

>[!NOTE]
>
>Het ingesloten fragment is niet meer gekoppeld aan het zelfstandige fragment. U kunt de componenten in het ingesloten fragment bewerken vanuit het adaptieve formulier.

### Fragmenten gebruiken in fragmenten {#using-fragments-within-fragments}

U kunt geneste adaptieve formulierfragmenten maken, wat betekent dat u een fragment naar een ander fragment kunt slepen en neerzetten en dat u een geneste fragmentstructuur kunt hebben.

### Fragmenten {#change-fragments} wijzigen

U kunt een adaptief formulierfragment vervangen of wijzigen door een ander fragment met de eigenschap **Fragmentelement selecteren** in het dialoogvenster Component bewerken voor een adaptief deelvenster met formulierfragmenten.

## Automatische toewijzing van fragmenten voor gegevensbinding {#auto-mapping-of-fragments-for-data-binding}

Wanneer u een adaptief formulierfragment maakt met een XFA-formuliersjabloon of een XSD-complex type en het fragment naar een adaptief formulier sleept, wordt het XFA-fragment of het XSD-complexe type automatisch vervangen door het bijbehorende adaptieve formulierfragment waarvan de hoofdmap van het fragmentmodel is toegewezen aan het XFA-fragment of het XSD-complexe type.

U kunt het fragmentelement en de bijbehorende bindingen wijzigen in het dialoogvenster Component bewerken.

>[!NOTE]
>
>U kunt een gebonden adaptief formulierfragment ook slepen en neerzetten vanuit de bibliotheek met adaptief formulierfragment in AEM zoekfunctie voor inhoud en de juiste bindingsverwijzing opgeven in het dialoogvenster Component bewerken van het adaptieve deelvenster voor formulierfragmenten.

## Fragmenten {#manage-fragments} beheren

U kunt verschillende bewerkingen uitvoeren op adaptieve formulierfragmenten met de gebruikersinterface van AEM Forms.

1. Ga naar `https://[hostname]:'port'/aem/forms.html`.

1. Klik op **Selecteer** op de werkbalk van de gebruikersinterface van AEM Forms en selecteer een adaptief formulierfragment. Op de werkbalk worden de volgende bewerkingen weergegeven die u kunt uitvoeren op het geselecteerde adaptieve formulierfragment.

<table>
 <tbody>
  <tr>
   <td><p><strong>Bewerking</strong></p> </td>
   <td><p><strong>Beschrijving</strong></p> </td>
  </tr>
  <tr>
   <td><p>Open</p> </td>
   <td><p>Hiermee opent u het geselecteerde adaptieve formulierfragment in de bewerkingsmodus.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Eigenschappen weergeven</p> </td>
   <td><p>Hiermee opent u het deelvenster Eigenschappen. In het deelvenster Eigenschappen kunt u eigenschappen weergeven en bewerken, een voorvertoning genereren en een miniatuurafbeelding voor het geselecteerde fragment uploaden. Zie <a href="../../forms/using/manage-form-metadata.md" target="_blank">Metagegevens beheren</a>.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Kopiëren</p> </td>
   <td><p>Hiermee kopieert u het geselecteerde fragment. De knop Plakken wordt weergegeven in de werkbalk.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Downloaden</p> </td>
   <td><p>Hiermee downloadt u het geselecteerde fragment.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Voorvertoning</p> </td>
   <td><p>Hiermee kunt u opties instellen om een voorvertoning van het fragment weer te geven als HTML of als aangepaste voorvertoning door gegevens uit een XML-bestand samen te voegen met het fragment. Zie <a href="/help/forms/using/previewing-forms.md" target="_blank">Een voorbeeld van een formulier bekijken</a>.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Revisie starten/Revisie beheren</p> </td>
   <td><p>Hiermee kunt u een revisie van het geselecteerde fragment starten en beheren. Zie <a href="../../forms/using/create-reviews-forms.md" target="_blank">Revisies maken en beheren</a>.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Woordenboek maken</p> </td>
   <td><p>Hiermee genereert u een woordenboek voor het lokaliseren van het geselecteerde fragment. Zie <a href="/help/forms/using/lazy-loading-adaptive-forms.md" target="_blank">Aangepaste formulieren lokaliseren</a>.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Publiceren/Publiceren ongedaan maken</p> </td>
   <td><p>Hiermee publiceert u het geselecteerde fragment of maakt u de publicatie ervan ongedaan.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Verwijderen</p> </td>
   <td><p>Hiermee verwijdert u het geselecteerde fragment.<br /> <br /> </p> </td>
  </tr>
 </tbody>
</table>

## Adaptief formulier met fragmenten lokaliseren {#localizing-adaptive-form-containing-fragments}

Als u een adaptief formulier met adaptieve formulierfragmenten wilt lokaliseren, moet u het fragment en het formulier afzonderlijk lokaliseren. Het is de bedoeling een fragment één keer te lokaliseren en opnieuw te gebruiken in meerdere adaptieve formulieren.

>[!NOTE]
>
>De lokalisatietoetsen in het fragment worden niet weergegeven in het XLIFF-bestand voor een adaptief formulier.

## Belangrijke punten die u moet onthouden wanneer u werkt met fragmenten {#key-points-to-remember-when-working-with-fragments}

* Zorg ervoor dat de fragmentnaam uniek is. Het fragment kan niet worden gemaakt als er een bestaand fragment met dezelfde naam bestaat.
* Als u in een op XDP gebaseerd adaptief formulier een deelvenster opslaat als fragment dat een ander XDP-fragment bevat, wordt het resulterende fragment automatisch gebonden aan het onderliggende XDP-fragment. In het geval van een adaptief XSD-formulier wordt het resulterende fragment gebonden aan de hoofdmap van het schema.
* Wanneer u een adaptief formulierfragment maakt, wordt in CRXDe Lite een fragmentknooppunt gemaakt, dat vergelijkbaar is met het knooppunt guideContainer voor een adaptief formulier.
* Een fragment in een adaptief formulier dat een ander formuliergegevensmodel gebruikt, wordt niet ondersteund. Een op XDP gebaseerd fragment wordt bijvoorbeeld niet ondersteund in een adaptief XSD-formulier en omgekeerd.
* Adaptieve formulierfragmenten zijn beschikbaar voor gebruik via het tabblad Adaptieve formulierfragmenten in AEM zoekfunctie.
* Expressies, scripts of stijlen in een op zichzelf staand adaptief formulierfragment blijven behouden wanneer deze via verwijzing worden ingevoegd of in een adaptieve vorm worden ingesloten.
* U kunt een adaptief formulierfragment, dat via verwijzing wordt ingevoegd, niet bewerken vanuit een adaptief formulier. Als u het fragment wilt bewerken, bewerkt u het zelfstandige, adaptieve formulierfragment of sluit u het fragment in het adaptieve formulier in.
* Wanneer u een adaptief formulier publiceert, moet u de stand-alone adaptieve formulierfragmenten publiceren die door verwijzing in het adaptieve formulier zijn ingevoegd.
* Wanneer u een bijgewerkt adaptief formulierfragment opnieuw publiceert, worden de wijzigingen weerspiegeld in de gepubliceerde exemplaren van het adaptieve formulier waarin het fragment wordt gebruikt.
* Het adaptieve formulier met de component Verify ondersteunt geen anonieme gebruikers. Het wordt ook niet aanbevolen om de component Verify te gebruiken in een adaptief formulierfragment.
* (**Alleen Mac**) Voeg de volgende vermelding toe aan het bestand /private/etc/hosts om ervoor te zorgen dat de functionaliteit van formulierfragmenten perfect werkt in alle scenario&#39;s:
   `127.0.0.1 <Host machine>` **Hostcomputer**: De Apple Mac-computer waarop AEM Forms is geïmplementeerd.

## Referentiefragmenten {#reference-fragments}

Aangepaste formulierfragmenten voor verwijzingen die u kunt gebruiken om uw formulier te maken, zijn beschikbaar. Zie [Referentiefragmenten](../../forms/using/reference-adaptive-form-fragments.md) voor meer informatie.
