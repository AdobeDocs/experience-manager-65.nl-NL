---
title: Variaties - Authoring van content voor fragmenten
description: Begrijp hoe de variaties uw inhoud zonder kop in AEM nog flexibeler kunnen maken door u toe te staan om inhoud voor het fragment te ontwerpen en dan variaties van die inhoud volgens doel tot stand te brengen.
feature: Content Fragments
role: User
source-git-commit: 251bf0ac672d516dd6b2018fc9cc804822f48e4c
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Variaties - Authoring van content voor fragmenten{#variations-authoring-fragment-content}

[](/help/assets/content-fragments/content-fragments.md#constituent-parts-of-a-content-fragment) Variaties zijn een belangrijk kenmerk van AEM inhoudsfragmenten, omdat u hiermee kopieën van de master inhoud kunt maken en bewerken voor gebruik op specifieke kanalen en/of scenario&#39;s, waardoor de levering van inhoud zonder kop nog flexibeler wordt.

Op het tabblad **Variaties** kunt u:

* [Voer de ](#authoring-your-content) inhoud voor het fragment in.
* [Creeer en beheer ](#managing-variations) variaties van de  **** Mastercontent,

Voer een reeks andere acties uit afhankelijk van het gegevenstype dat wordt uitgegeven; bijvoorbeeld:

* [Visuele elementen in het fragment](#inserting-assets-into-your-fragment)  invoegen (afbeeldingen)

* Selecteer tussen [RTF](#rich-text), [Onbewerkte tekst](#plain-text) en [Markdown](#markdown) voor bewerking

* [Inhoud uploaden](#uploading-content)

* [Belangrijke statistieken](#viewing-key-statistics)  weergeven (over tekst met meerdere regels)

* [Tekst samenvatten](#summarizing-text)

* [Variaties synchroniseren met Master inhoud](#synchronizing-with-master)

>[!CAUTION]
>
>Nadat een fragment is gepubliceerd en/of waarnaar wordt verwezen, geeft AEM een waarschuwing weer wanneer een auteur het fragment opent om opnieuw te bewerken. Hiermee wordt u gewaarschuwd dat wijzigingen in het fragment ook van invloed zijn op de pagina&#39;s waarnaar wordt verwezen.

## Inhoud ontwerpen {#authoring-your-content}

Wanneer u het inhoudsfragment opent voor bewerking, wordt het tabblad **Variaties** standaard geopend. Hier kunt u de inhoud ontwerpen, voor Master of andere variaties. Het gestructureerde fragment bevat verschillende velden van diverse gegevenstypen die zijn gedefinieerd in het inhoudsmodel.

Bijvoorbeeld:

![full screen ](assets/cfm-variations-02.png)
editorU kunt:

* direct wijzigingen aanbrengen op het tabblad **Variaties**

   * elk gegevenstype biedt verschillende bewerkingsopties

* voor **Meerdere-regeltekst**-velden kunt u ook de [volledige-schermeditor](#full-screen-editor) openen om:

   * Selecteer [Format](#formats)
   * zie meer het uitgeven opties (voor [Rich Text](#rich-text) formaat)
   * toegang tot een waaier van [acties](#actions)

* Voor **Fragmentverwijzing**-velden kan de optie **[Inhoudsfragment bewerken](#fragment-references-edit-content-fragment)** beschikbaar zijn, afhankelijk van de modeldefinitie.

### Volledige schermeditor {#full-screen-editor}

Als u een tekstveld met meerdere regels bewerkt, kunt u de volledige schermeditor openen. Tik of klik in de werkelijke tekst en selecteer vervolgens het volgende handelingspictogram:

![pictogram van volledige schermeditor](assets/cfm-variations-03.png)

Hiermee wordt de teksteditor voor het volledige scherm geopend:

![volledige schermeditor](assets/cfm-variations-fullscreentexteditor.png)

De teksteditor voor volledig scherm biedt:

* Toegang tot verschillende [acties](#actions)
* Afhankelijk van de [indeling](#formats), aanvullende opmaakopties ([RTF](#rich-text))

### Acties {#actions}

De volgende acties zijn ook beschikbaar (voor alle [formaten](#formats)) wanneer de volledige het schermredacteur (d.w.z. multi-line tekst) open is:

* Selecteer de [indeling](#formats) ([RTF-tekst](#rich-text), [Onbewerkte tekst,](#plain-text) [Markering](#markdown))

* [Inhoud uploaden](#uploading-content)

* [Tekststatistieken tonen](#viewing-key-statistics)

* [Synchroniseren met Master](#synchronizing-with-master)  (bij het bewerken van een variatie)

* [Tekst samenvatten](#summarizing-text)

### Indelingen {#formats}

De opties voor het bewerken van tekst met meerdere regels zijn afhankelijk van de geselecteerde indeling:

* [RTF](#rich-text)
* [Onbewerkte tekst](#plain-text)
* [Markering](#markdown)

De indeling kan worden geselecteerd in de schermvullende editor.

### RTF {#rich-text}

Met RTF-bewerkingen kunt u de volgende opmaken:

* Vet
* Cursief
* Onderstrepen
* Uitlijning: links, midden, rechts
* Lijst met opsommingstekens
* Genummerde lijst
* Inspringing: toename, afname
* Hyperlinks maken/verbreken
* Tekst/tekst uit Word plakken
* Een tabel invoegen
* Alineastijl: Alinea, kopje 1/2/3
* [Element invoegen](#inserting-assets-into-your-fragment)
* Open de volledige-schermredacteur, waar de volgende het formatteren opties beschikbaar zijn:
   * Zoeken
   * Zoeken/vervangen
   * Spellingcontrole
   * [Annotaties](/help/assets/content-fragments/content-fragments-variations.md#annotating-a-content-fragment)
* [Inhoudsfragment](#inserting-content-fragment-into-your-fragment) invoegen; beschikbaar als uw  **tekstveld met meerdere regels is geconfigureerd met** Fragmentverwijzing **** toestaan.

De [acties](#actions) zijn ook toegankelijk van de volledig-schermredacteur.

### Onbewerkte tekst {#plain-text}

Met platte tekst kunt u snel inhoud invoeren zonder opmaak- of markeringsgegevens. U kunt de volledige het schermredacteur voor verdere [acties](#actions) ook openen.

>[!CAUTION]
>
>Als u **Tekst zonder opmaak** selecteert, gaan opmaak, markdown en/of assets die u hebt ingevoegd in **Tekst met opmaak** of **Markdown** verloren.

### Markering {#markdown}

>[!NOTE]
>
>Zie de documentatie [Markdown](/help/assets/content-fragments/content-fragments-markdown.md) voor volledige informatie.

Hierdoor kunt u de tekst opmaken met behulp van een markering. U kunt het volgende definiëren:

* Koppen
* Alinea&#39;s en regeleinden
* Koppelingen
* Afbeeldingen
* Aanhalingstekens blokkeren
* Lijsten
* Nadruk
* Codeblokken
* backslash-eces

U kunt de volledige het schermredacteur voor verdere [acties](#actions) ook openen.

>[!CAUTION]
>
>Als u tussen **Tekst met opmaak** en **Markdown** schakelt, kunt u onverwachte effecten met Blokcitaten en Codeblokken ervaren, aangezien deze twee opmaakindelingen verschillen in hoe zij worden behandeld.

### Fragmentverwijzingen {#fragment-references}

Als het Content Fragment-model fragmentverwijzingen bevat, hebben de auteurs van het fragment mogelijk aanvullende opties:

* [Inhoudsfragment bewerken](#fragment-references-edit-content-fragment)
* [Nieuw inhoudsfragment](#fragment-references-new-content-fragment)

![Fragmentverwijzingen](assets/cfm-variations-12.png)

#### Inhoudsfragment bewerken {#fragment-references-edit-content-fragment}

Met de optie **Inhoudsfragment bewerken** wordt dat fragment geopend in een nieuw venstertabblad.

<!--
The option **Edit Content Fragment** will open that fragment in a new editor tab (within the same browser tab).

Selecting the original tab again (for example, **Little Pony Inc.**), will close this secondary tab (in this case, **Adam Smith**).

![Fragment References](assets/cfm-variations-editreference.png)
-->

#### Nieuw inhoudsfragment {#fragment-references-new-content-fragment}

Met de optie **Nieuw inhoudsfragment** kunt u een volledig nieuw fragment maken. Hiervoor wordt een variant van de wizard voor het maken van inhoudsfragmenten geopend in de editor.

U kunt dan een nieuw fragment maken door:

1. Navigeer naar en selecteer de gewenste map.
1. Selecteren **Next**.
1. Eigenschappen specificeren; bijvoorbeeld **Title**.
1. Selecteren **Create**.
1. Tot slot:
   1. **Hiermee** wordt het oorspronkelijke fragment hersteld en wordt naar het nieuwe fragment verwezen.
   1. **Met** Openwill wordt naar het nieuwe fragment verwezen en wordt het nieuwe fragment geopend voor bewerking op een nieuw browsertabblad.

### Belangrijkste statistieken weergeven {#viewing-key-statistics}

Wanneer de volledige-schermeditor open is, zal de actie **Tekststatistieken** allerlei informatie over de tekst tonen.

Bijvoorbeeld:

![statistieken](assets/cfm-variations-04.png)

### Inhoud uploaden {#uploading-content}

Als u het maken van inhoudsfragmenten wilt vereenvoudigen, kunt u tekst uploaden die is voorbereid in een externe editor en deze rechtstreeks aan het fragment toevoegen.

### Tekst samenvatten {#summarizing-text}

Samenvattende tekst is ontworpen om gebruikers te helpen de lengte van hun tekst te beperken tot een vooraf gedefinieerd aantal woorden, terwijl de hoofdpunten en de algemene betekenis behouden blijven.

>[!NOTE]
>
>Op technisch niveau houdt het systeem de zinnen bij die het als het verstrekken van *beste verhouding van informatiedichtheid en uniciteit* volgens specifieke algoritmen beschouwt.

>[!CAUTION]
>
>Het inhoudsfragment moet een geldige taalmap (ISO-code) hebben als voorouder. dit wordt gebruikt om het te gebruiken taalmodel te bepalen.
>
>Bijvoorbeeld `en/` zoals in het volgende pad:
>
>  `/content/dam/my-brand/en/path-down/my-content-fragment`

>[!CAUTION]
Engels is beschikbaar buiten de box.
Andere talen zijn beschikbaar als Pakketten van het Model van de Taal van het Aandeel van het Pakket:
* [Frans (fr)](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-fr)
* [Duits (de)](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-de)
* [Italiaans (it)](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-it)
* [Spaans (es)](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-es)


1. Selecteer **Master** of de vereiste variatie.
1. Open de editor voor het volledige scherm.

1. Selecteer **Samenvatting tekst** van de toolbar.

   ![samenvatting](assets/cfm-variations-05.png)

1. Geef het doelaantal woorden op en selecteer **Start**:
1. De oorspronkelijke tekst wordt naast de voorgestelde samenvatting weergegeven:

   * Alle zinnen die moeten worden verwijderd, worden rood gemarkeerd met doorhaling.
   * Klik op een gemarkeerde zin om deze in de samengevatte inhoud te houden.
   * Klik op een niet-gemarkeerde zin om deze te verwijderen.

1. Selecteer **Samenvatten** om de veranderingen te bevestigen.

1. De oorspronkelijke tekst wordt naast de voorgestelde samenvatting weergegeven:

   * Alle zinnen die moeten worden verwijderd, worden rood gemarkeerd met doorhaling.
   * Klik op een gemarkeerde zin om deze in de samengevatte inhoud te houden.
   * Klik op een niet-gemarkeerde zin om deze te verwijderen.
   * De samenvattingsstatistieken worden weergegeven: **Werkelijk** en **Doel**-
   * U kunt de wijzigingen **Voorvertoning**.

   ![samenvattingsvergelijking](assets/cfm-variations-06.png)

### Een inhoudsfragment annoteren {#annotating-a-content-fragment}

Een fragment annoteren:

1. Selecteer **Master** of de vereiste variatie.

1. Open de editor voor het volledige scherm.

1. Het pictogram **Annoteren** is beschikbaar in de bovenste werkbalk. U kunt desgewenst tekst selecteren.

   ![annoteren](assets/cfm-variations-07.png)

1. Er wordt een dialoogvenster geopend. Hier kunt u uw annotatie invoeren.

   ![annoteren](assets/cfm-variations-07a.png)

1. Selecteer **Toepassen** in het dialoogvenster.

   ![annoteren](assets/cfm-variations-annotations-apply-icon.png)

   Als de annotatie is toegepast op geselecteerde tekst, blijft die tekst gemarkeerd.

   ![annoteren](assets/cfm-variations-07b.png)

1. Sluit de volledige-schermredacteur, de annotaties worden nog benadrukt. Als deze optie is geselecteerd, wordt een dialoogvenster geopend waarin u de annotatie verder kunt bewerken.

1. Selecteer **Opslaan**.

1. Sluit de volledige-schermredacteur, de annotaties worden nog benadrukt. Als deze optie is geselecteerd, wordt een dialoogvenster geopend waarin u de annotatie verder kunt bewerken.

   ![annoteren](assets/cfm-variations-07c.png)

### Annotaties weergeven, bewerken, verwijderen {#viewing-editing-deleting-annotations}

Annotaties:

* Deze worden aangegeven door de markering in de tekst, zowel in de modus Volledig scherm als in de normale modus van de editor. Alle details van een annotatie kunnen vervolgens worden weergegeven, bewerkt en/of verwijderd door op de gemarkeerde tekst te klikken, waarna het dialoogvenster opnieuw wordt geopend.

   >[!NOTE]
   Er is een keuzekiezer beschikbaar als er meerdere annotaties zijn toegepast op één stuk tekst.

* Wanneer u de volledige tekst verwijdert waarop de annotatie is toegepast, wordt de annotatie ook verwijderd.

* Kan worden vermeld en verwijderd door het tabblad **Annotaties** in de fragmenteditor te selecteren.

   ![annotaties](assets/cfm-variations-08.png)

* Kan worden weergegeven en verwijderd in [Tijdlijn](/help/assets/content-fragments/content-fragments-managing.md#timeline-for-content-fragments) voor het geselecteerde fragment.

### Elementen invoegen in uw fragment {#inserting-assets-into-your-fragment}

Als u het ontwerpen van inhoudsfragmenten wilt vereenvoudigen, kunt u [Middelen](/help/assets/manage-assets.md) (afbeeldingen) rechtstreeks aan het fragment toevoegen.

Ze worden zonder opmaak toegevoegd aan de alineasequentie van het fragment. opmaak kan worden toegepast wanneer het [fragment wordt gebruikt/ernaar wordt verwezen op een pagina](/help/sites-authoring/content-fragments.md).

>[!CAUTION]
Deze elementen kunnen niet worden verplaatst of verwijderd op een pagina waarnaar wordt verwezen. Dit moet gebeuren in de fragmenteditor.
Opmaak van het element (bijvoorbeeld grootte) moet echter worden uitgevoerd in de [pagina-editor](/help/sites-authoring/content-fragments.md). De representatie van het element in de fragmenteditor is uitsluitend bedoeld voor het ontwerpen van de inhoudsstroom.

>[!NOTE]
Er zijn verschillende methoden om [afbeeldingen](/help/assets/content-fragments/content-fragments.md#fragments-with-visual-assets) aan het fragment en/of de pagina toe te voegen.

1. Plaats de cursor op de positie waar u de afbeelding wilt toevoegen.
1. Gebruik het pictogram **Asset invoegen** om het zoekdialoogvenster te openen.

   ![middelenpictogram invoegen](assets/cfm-variations-09.png)

1. In het dialoogvenster kunt u:

   * navigeren naar het vereiste element in DAM
   * zoeken naar de middelen in DAM

   Selecteer het gewenste element door op de miniatuur te klikken.

1. Gebruik **Selecteren** om de asset op de huidige locatie toe te voegen aan het alineasysteem van het contentfragment.

   >[!CAUTION]
   Als u na het toevoegen van een asset de indeling wijzigt in:
   * **Tekst zonder opmaak**: wordt de asset volledig uit het fragment verwijderd.
   * **Markdown**: is de asset niet zichtbaar, maar blijft deze aanwezig wanneer u terugkeert naar **Tekst met opmaak**.


### Een inhoudsfragment invoegen in uw fragment {#inserting-content-fragment-into-your-fragment}

U kunt ook een ander inhoudsfragment aan het fragment toevoegen om het maken van inhoudsfragmenten te vereenvoudigen.

Deze worden als referentie toegevoegd op de huidige locatie in het fragment.

>[!NOTE]
Deze optie is beschikbaar wanneer uw **Tekst met meerdere regels** is geconfigureerd met **Fragmentverwijzing toestaan**.

>[!CAUTION]
Deze elementen kunnen niet worden verplaatst of verwijderd op een pagina waarnaar wordt verwezen. Dit moet gebeuren in de fragmenteditor.
Opmaak van het element (bijvoorbeeld grootte) moet echter worden uitgevoerd in de [pagina-editor](/help/sites-authoring/content-fragments.md). De representatie van het element in de fragmenteditor is uitsluitend bedoeld voor het ontwerpen van de inhoudsstroom.

>[!NOTE]
Er zijn verschillende methoden om [afbeeldingen](/help/assets/content-fragments/content-fragments.md#fragments-with-visual-assets) aan het fragment en/of de pagina toe te voegen.

1. Plaats de cursor op de positie waar u het fragment wilt toevoegen.
1. Gebruik het pictogram **Inhoudsfragment invoegen** om het dialoogvenster Zoeken te openen.

   ![pictogram Inhoudsfragment invoegen](assets/cfm-variations-13.png)

1. In het dialoogvenster kunt u:

   * navigeer naar het gewenste fragment in de map Middelen
   * zoeken naar het fragment

   Selecteer het gewenste fragment door op de miniatuur te klikken.

1. Gebruik **Selecteer** om een verwijzing naar het geselecteerde inhoudsfragment toe te voegen aan het huidige inhoudsfragment (op de huidige locatie).

   >[!CAUTION]
   Als u na het toevoegen van een verwijzing naar een ander fragment de opmaak wijzigt in:
   * **Onbewerkte tekst**: de verwijzing gaat volledig verloren uit het fragment.
   * **Markering**: de referentie blijft .


## Variaties beheren {#managing-variations}

### Een variatie maken {#creating-a-variation}

Met behulp van variaties kunt u de **Master**-inhoud innemen en deze afhankelijk van het doel variëren (indien nodig).

Een nieuwe variatie maken:

1. Open het fragment en controleer of het zijpaneel zichtbaar is.
1. Selecteer **Variaties** in de pictogrambalk in het zijpaneel.
1. Selecteer **Variatie maken**.
1. Er wordt een dialoogvenster geopend waarin u de **titel** en de **beschrijving** voor de nieuwe variatie kunt opgeven.
1. Selecteer **Toevoegen**. De **fragmentmaster** wordt gekopieerd naar de nieuwe variatie, die nu kan worden [bewerkt](#editing-a-variation).

   >[!NOTE]
   Wanneer u een nieuwe variant maakt, wordt deze altijd **Master** gekopieerd en niet de variant die momenteel is geopend.

### Een variatie bewerken {#editing-a-variation}

U kunt wijzigingen aanbrengen in de inhoud van de variatie nadat:

* [Uw variatie](#creating-a-variation) maken.
* Een bestaand fragment openen en vervolgens de gewenste variant in het zijpaneel selecteren.

![bewerken van een variatie](assets/cfm-variations-10.png)

### De naam van een variatie wijzigen {#renaming-a-variation}

Een bestaande variatie een andere naam geven:

1. Open het fragment en selecteer **Variaties** in het zijpaneel.
1. Selecteer de gewenste variatie.
1. Selecteer **Naam wijzigen** in de vervolgkeuzelijst **Acties**.

1. Voer in het dialoogvenster dat verschijnt de nieuwe **titel** en/of **beschrijving** in.

1. Bevestig de handeling **Naam wijzigen**.

>[!NOTE]
Dit beïnvloedt slechts de variatie **Titel**.

### Een variatie verwijderen {#deleting-a-variation}

Een bestaande wijziging verwijderen:

1. Open het fragment en selecteer **Variaties** in het zijpaneel.
1. Selecteer de gewenste variatie.
1. Selecteer **Delete** van **Acties** drop down.

1. Bevestig de handeling **Delete** in het dialoogvenster.

>[!NOTE]
U kunt **Master** niet schrappen.

### Synchroniseren met Master {#synchronizing-with-master}

**** Masteris is een integraal onderdeel van een inhoudsfragment en bevat per definitie de master kopie van de inhoud, terwijl de variaties de afzonderlijke bijgewerkte en op maat gemaakte versies van die inhoud bevatten. Wanneer Master wordt bijgewerkt, is het mogelijk dat deze wijzigingen ook relevant zijn voor de variaties en daarom aan hen moeten worden doorgegeven.

Wanneer u een variatie bewerkt, hebt u toegang tot de handeling voor het synchroniseren van het huidige element van de variatie met Master. Op deze manier kunt u automatisch wijzigingen kopiëren die u hebt aangebracht in de Master variatie.

>[!CAUTION]
De synchronisatie is alleen beschikbaar om wijzigingen *van **Master**naar de variatie* te kopiëren.
Alleen het huidige element van de variatie wordt gesynchroniseerd.
Synchronisatie werkt alleen op het datatype **Tekst met meerdere regels**.
Het overbrengen van wijzigingen *van een variatie naar **master*** is niet beschikbaar als optie.

<!-- needs new screenshot for synchronize effect -->

1. Open het inhoudsfragment in de fragmenteditor. Zorg ervoor dat **Master** is uitgegeven.

1. Selecteer een specifieke variant en kies vervolgens de gewenste synchronisatiehandeling uit:

   * de **Handelingen** keuzelijst - **Huidig element synchroniseren met master**

      ![synchroniseren met master](assets/cfm-variations-11a.png)

   * de werkbalk van de schermvullende editor - **Synchroniseren met master**

      ![synchroniseren met master](assets/cfm-variations-11b.png)

1. Master en de variatie wordt naast elkaar weergegeven:

   * groen geeft de inhoud aan die is toegevoegd (aan de variatie)
   * rood geeft aan dat inhoud is verwijderd (uit de variatie)
   * blauw geeft vervangen tekst aan

   ![synchroniseren met master](assets/cfm-variations-11c.png)

1. Selecteer **Synchronize**, zal de variatie worden bijgewerkt en getoond.
