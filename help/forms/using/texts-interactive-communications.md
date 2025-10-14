---
title: Teksten in interactieve communicatie
description: Het creëren en het uitgeven van tekstdocumentfragmenten die in Interactieve Mededelingen moeten worden gebruikt - de tekst is één van de vier soorten documentfragmenten die worden gebruikt om Interactieve Mededelingen te bouwen. De andere drie zijn voorwaarden, lijsten en layoutfragmenten.
topic-tags: interactive-communications
products: SG_EXPERIENCEMANAGER/6.5/FORMS
docset: aem65
feature: Interactive Communication
exl-id: b8e84c5d-2ec8-4575-9eed-6b37b04e5d66
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '2420'
ht-degree: 0%

---

# Teksten in interactieve communicatie{#texts-in-interactive-communications}

## Overzicht {#overview}

Een tekstdocumentfragment bestaat uit een of meer tekstalinea&#39;s. Een alinea kan statisch of dynamisch zijn. Een dynamische alinea kan eigenschappen en variabelen van het formuliergegevensmodel bevatten. U kunt ook regels toepassen en herhalen binnen een tekstdocumentfragment. Bijvoorbeeld, zou de klantennaam in een aanhef een bezit van het Model van de Gegevens van de Vorm (FDM) kunnen zijn met zijn waarde die bij runtime ter beschikking wordt gesteld. Door deze waarden te veranderen, kan de zelfde Interactieve Communicatie worden gebruikt om Interactieve Mededeling voor verschillende klanten voor te bereiden gebruikend de Agent UI.

Het tekstdocumentfragment in Interactive Communication ondersteunt het volgende type dynamische gegevens:

* **modelvoorwerpen van Gegevens**: De gegevenseigenschappen gebruiken een achtereind gegevensbron.
* **regel gebaseerde inhoud**: De delen van inhoud in een tekst die verschijnen of verborgen gebaseerd op een regel worden. Een regel kan ook worden gebaseerd op eigenschappen en variabelen van het formuliergegevensmodel.
* **Variabelen**: In het fragment van het tekstdocument, zijn de variabelen niet verbindend aan een achterste gegevensbron. De agent vult in/selecteert waarden in variabelen of bindt de variabelen aan gegevensbronnen terwijl het voorbereiden van de Interactieve Mededeling voor het voorleggen van het aan een postproces.
* **Herhaal**: U kunt dynamische informatie in uw Interactieve Mededeling, zoals transacties in een verklaring van de creditcard hebben, waarvan het aantal voorkomen met elke geproduceerde Interactieve Mededeling kan blijven veranderen. Met Herhaling kunt u dergelijke dynamische informatie opmaken en structureren. Voor meer informatie, zie [&#x200B; Gealigneerde voorwaarde en herhaal &#x200B;](https://helpx.adobe.com/nl/experience-manager/6-3/forms/using/cm-inline-condition.html).

## Tekst maken {#createtext}

1. Selecteer **[!UICONTROL Forms]** > **[!UICONTROL Document Fragments]** .
1. Selecteer **[!UICONTROL Create]** > **[!UICONTROL Text]** .
1. Geef de volgende informatie op:

   * **[!UICONTROL Title]**: (Optioneel) Voer de titel in voor het tekstdocumentfragment. Titels hoeven niet uniek te zijn en kunnen speciale tekens en niet-Engelse tekens bevatten. De teksten worden bedoeld door hun titels (indien beschikbaar) zoals in duimnagels en eigenschappen.
   * **[!UICONTROL Name]**: De unieke naam voor de tekst in een map. Geen twee documentfragmenten (tekst, voorwaarde of lijst) in een staat kunnen bestaan met dezelfde naam in een map. In het veld Naam kunt u alleen Engelse tekens, cijfers en afbreekstreepjes invoeren. Het veld Naam wordt automatisch ingevuld op basis van het veld Titel. De speciale tekens, spaties, getallen en niet-Engelse tekens die in het veld Titel zijn ingevoerd, worden vervangen door afbreekstreepjes in het veld Naam. Hoewel de waarde in het veld Titel automatisch naar de naam wordt gekopieerd, kunt u de waarde bewerken.

   * **[!UICONTROL Description]**: typ een beschrijving van de tekst.
   * **[!UICONTROL Form Data Model]**: Selecteer desgewenst het keuzerondje Formuliergegevensmodel om de tekst te maken op basis van een formuliergegevensmodel. Wanneer u het keuzerondje Formuliergegevensmodel selecteert, wordt het veld **[!UICONTROL Form Data Model]** weergegeven. Blader naar een formuliergegevensmodel en selecteer dit. Zorg er tijdens het maken van tekst en een voorwaarde voor interactieve communicatie voor dat u hetzelfde gegevensmodel gebruikt dat u in de interactieve communicatie wilt gebruiken. Voor meer informatie over het Model van de Gegevens van de Vorm, zie [&#x200B; Integratie van Gegevens &#x200B;](/help/forms/using/data-integration.md).

   * **[!UICONTROL Tags]**: Als u een aangepaste tag wilt maken, typt u een waarde in het tekstveld en drukt u op Enter. Wanneer u deze tekst opslaat, worden de nieuwe tags gemaakt.

1. Selecteer **[!UICONTROL Next]** .

   De pagina Tekst maken wordt weergegeven. Als u ervoor hebt gekozen om een op een formuliergegevensmodel gebaseerde tekst te maken, worden de eigenschappen van het formuliergegevensmodel weergegeven in het linkerdeelvenster.

1. Typ de tekst en gebruik de volgende opties voor het opmaken, conditionaliseren en invoegen van eigenschappen en variabelen van het gegevensmodel van het formulier in de tekst:

   * [Formuliergegevensmodel](#formdatamodel)
   * [Variabelen](#variables)
   * [Regeleditor](#rules)
   * [Opmaakopties](#formatting)

      * [&#x200B; geformatteerde tekst van het Exemplaar van andere toepassingen &#x200B;](#paste)

      * [Tekstgedeelten markeren](#highlight)

   * [Herhalen](/help/forms/using/cm-inline-condition.md)
   * [Speciale tekens](#special)
   * [Tekst zoeken en vervangen](#searching)
   * [Sneltoetsen](/help/forms/using/keyboard-shortcuts.md)

   >[!NOTE]
   >
   >U kunt formuliergegevensmodelelementen, gegevenswoordenboekelementen en variabelen toevoegen met het @-symbool in de teksteditor. Wanneer u een tekenreeks opgeeft die wordt voorafgegaan door @ in de teksteditor, worden alle elementen van het gegevensmodel, gegevenswoordenboek en variabelen doorzocht en worden elementen of variabelen met de doorzochte tekenreeks weergegeven. U kunt door de onderzoeksresultaten navigeren en een element of een variabele selecteren. Als er geen passend resultaat is, wordt het *Geen gevonden passende resultaten* bericht getoond.

1. Selecteer **[!UICONTROL Save]** .

   De tekst wordt gemaakt. Nu kunt u doorgaan met het gebruik van de tekst als een bouwsteen tijdens het maken van een interactieve communicatie.

## Tekst bewerken {#edittext}

U kunt een bestaand tekstdocumentfragment bewerken met de volgende stappen. U kunt ook een tekstdocumentfragment bewerken in een interactieve communicatie-editor.

1. Selecteer **[!UICONTROL Forms]** > **[!UICONTROL Document Fragments]** .
1. Navigeer naar een tekstdocumentfragment en selecteer het.
1. Selecteer **[!UICONTROL Edit]** .
1. Breng de gewenste wijzigingen aan. Voor meer informatie over opties in tekst, zie [&#x200B; tekst &#x200B;](#createtext) creëren.
1. Selecteer **[!UICONTROL Save]** en selecteer vervolgens **[!UICONTROL Close]** .

## Een tekstdocumentfragment aanpassen met eigenschappen van het formuliergegevensmodel {#formdatamodel}

U kunt tekstdocumentfragmenten personaliseren door de eigenschappen van het formuliergegevensmodel in te voegen. Door eigenschappen van het formuliergegevensmodel in tekst in te voegen, kunt u specifieke gegevens voor ontvangers ophalen en vullen vanuit de bijbehorende gegevensbron terwijl u een voorbeeld van een interactieve communicatie bekijkt. Voor meer informatie over het model van vormgegevens, zie [&#x200B; de Integratie van Gegevens van AEM Forms &#x200B;](/help/forms/using/data-integration.md).

Als u een formuliergegevensmodel hebt opgegeven tijdens het maken van een tekst, worden de eigenschappen in het formuliergegevensmodel weergegeven in het linkerdeelvenster van de teksteditor. Het opgegeven formuliergegevensmodel moet hetzelfde zijn voor het tekstdocumentfragment en de interactieve communicatie die het fragment bevat.

![&#x200B; insertFDFmelementtext &#x200B;](assets/insertfdmelementtext.png)

* Om een modelbezit van vormgegevens in tekst op te nemen, plaats de curseur waar u het bezit wilt opnemen, dan het **[bezit A]** in de linkerruit selecteren door op het te tikken, en **[!UICONTROL [B] Add Selected]** te selecteren. U kunt het bezit ook enkel tweemaal selecteren om het bij de **[C]** cursorpositie op te nemen. Eigenschappen van het formuliergegevensmodel worden gemarkeerd in een bruine achtergrondkleur.

U kunt ook de eigenschap van het formuliergegevensmodel zoeken en toevoegen met het symbool @ in de teksteditor. Plaats de cursor op de plaats waar u de eigenschap wilt invoegen. Typ @ gevolgd door de zoekreeks. De zoekbewerking wordt uitgevoerd op alle eigenschappen en variabelen van het formuliergegevensmodel in het documentfragment. De eigenschappen of variabelen die de zoekreeks bevatten, worden opgehaald en weergegeven als een vervolgkeuzelijst. Navigeer door de onderzoeksresultaten en klik het bezit dat u bij de cursorplaats wilt opnemen. Druk op Esc om de zoekresultaten te verbergen.

* Om de agenten toe te staan om de waarde van een modelbezit van vormgegevens in de agent UI uit te geven terwijl [&#x200B; Interactieve Communicatie &#x200B;](/help/forms/using/prepare-send-interactive-communication.md) gebruikend de Agent UI voorbereidt en verzendt, selecteert het **[D]** slotpictogram voor dat bezit en verzekert het in een ontgrendelde staat is. De standaardstaat van het bezit is gesloten en een agent kan niet het bezit in de Agent UI uitgeven.

U kunt ook eigenschappen van het gegevensmodel van het formulier gebruiken om regels samen te stellen voor het weergeven of verbergen van delen van inhoud. Voor meer informatie, zie [&#x200B; regels in tekst &#x200B;](#rules) creëren.

## Variabelen in een tekstdocumentfragment maken en gebruiken {#variables}

Variabelen zijn plaatsaanduidingen die tijdens het maken van een interactieve communicatie kunnen worden gebonden. Variabelen kunnen worden gebonden aan een eigenschap van een formuliergegevensmodel of een tekstfragment. De variabelen kunnen ook voor de agent worden verlaten om te vullen.

U kunt variabelen gebruiken in plaats van eigenschappen van het formuliergegevensmodel wanneer:

* Een tekstdocumentfragment moet in veelvoudige Interactieve Mededelingen worden gebruikt waar de band voor verschillende Interactieve Mededelingen verschillend moet zijn.
* Fragment van tekstdocument heeft geen formuliergegevensmodel op het moment dat het wordt gemaakt. U kunt variabelen invoegen en deze later binden aan de eigenschappen van het formuliergegevensmodel op het moment dat de interactieve communicatie wordt gemaakt.
* U moet tekst van een tekstdocumentfragment binden en ophalen. Alleen tekstdocumentfragmenten kunnen worden gebonden aan variabelen die geen variabelen bevatten.

Tijdens het maken of bewerken van een tekstdocumentfragment kunt u variabelen maken en invoegen. De variabelen u creeert verschijnen in het lusje van Gegevens van de Agent UI. De agent specificeert de waarden voor de variabelen terwijl [&#x200B; voorbereidt en Interactieve Communicatie gebruikend de Agent UI &#x200B;](/help/forms/using/prepare-send-interactive-communication.md) verzendt.

### Variabelen maken {#createvariables}

1. Selecteer **[!UICONTROL Variables]** in het linkerdeelvenster.

   Het deelvenster Variabelen wordt weergegeven.

   ![&#x200B; veranderlijke ruit &#x200B;](assets/variablespane.png)

1. Selecteer **[!UICONTROL Create]** .

   Het deelvenster Variabelen maken wordt weergegeven.

1. Voer de volgende informatie in en selecteer **[!UICONTROL Create]** :

   * **[!UICONTROL Name]** : naam van de variabele.
   * **[!UICONTROL Description]** : voer optioneel een beschrijving van de variabele in.
   * **[!UICONTROL Type]** : selecteer een type variabele: String, Number, Boolean of Date.
   * **[!UICONTROL Allow Specific Values Only]** : Voor de variabelen van het Koord en van het Aantal, kunt u ervoor zorgen dat de agent van een specifieke reeks waarden voor placeholder in de Agent UI kiest. Als u de reeks waarden wilt opgeven, selecteert u deze optie en geeft u door komma&#39;s gescheiden waarden op die zijn toegestaan in het veld **[!UICONTROL Values]** .

1. Selecteer **[!UICONTROL Create]** .

   De variabele wordt gemaakt en vermeld in het deelvenster Variabelen.

1. Als u een variabele in de tekst wilt invoegen, plaatst u de cursor op de juiste plaats, selecteert u de variabele en selecteert u **[!UICONTROL Add Selected]** .

   ![&#x200B; variableinserted &#x200B;](assets/variableinserted.png)

   Variabelen worden gemarkeerd in lichtblauwe achtergrondkleur, terwijl eigenschappen van het formuliergegevensmodel worden gemarkeerd in een bruine kleur.

   U kunt ook variabelen zoeken en toevoegen met het @-symbool in de teksteditor. Plaats de cursor op de plaats waar u de variabele wilt invoegen. Typ @ gevolgd door de zoekreeks. De zoekbewerking wordt uitgevoerd op alle eigenschappen en variabelen van het formuliergegevensmodel in het documentfragment. De eigenschappen en variabelen die de zoekreeks bevatten, worden opgehaald en weergegeven als een vervolgkeuzelijst. Navigeer door de onderzoeksresultaten en klik de variabele die u bij de cursorplaats wilt opnemen. Druk op Esc om de zoekresultaten te verbergen.

1. Selecteer **[!UICONTROL Save]** .

## Regels maken in tekst {#rules}

Gebruikend regelredacteur in een tekst, kunt u regels tot stand brengen om koorden van tekst of stukken van inhoud te tonen of te verbergen die op **worden gebaseerd vooraf ingestelde voorwaarden**. Deze voorwaarden kunnen worden geconstrueerd op basis van:

* Tekenreeksen
* Getallen
* Wiskundige expressie
* Datums
* Eigenschappen van gekoppeld formuliergegevensmodel
* Alle variabelen die u in de tekst hebt gemaakt

### Regels maken in tekst {#create-rules-in-text}

1. Selecteer tijdens het maken of bewerken van een tekst de tekenreeks, alinea of inhoud die u wilt conditionaliseren met de regel.

   ![&#x200B; selectcontentapplyrule &#x200B;](assets/selectcontentapplyrule.png)

1. Selecteer **[!UICONTROL Create Rule]** .

   Het dialoogvenster Regel maken wordt weergegeven. Naast tekenreeks, nummer, wiskundige expressie en datum zijn in de Regeleditor ook de volgende opties beschikbaar voor het maken van instructies van de regels:

   * Eigenschappen van gekoppeld formuliergegevensmodel
   * Alle variabelen die u hebt gemaakt

   Selecteer de gewenste optie die u wilt evalueren.

   ![&#x200B; ruleeditor &#x200B;](assets/ruleeditor.png) ![&#x200B; ruleeditorfdm &#x200B;](assets/ruleeditorfdm.png)

   >[!NOTE]
   >
   >Verzamelingseigenschap wordt niet ondersteund voor het maken van regels voor het conditionaliseren en weergeven van tekst.

1. Selecteer de juiste operator om de regel te evalueren, zoals Is gelijk aan, Bevat en Begint met.

   ![&#x200B; ruleeditorfdm-1 &#x200B;](assets/ruleeditorfdm-1.png)

1. Voeg de evaluerende expressie, waarde, eigenschap gegevensmodel of variabele in.

   ![&#x200B; Regel om de geselecteerde tekst te tonen als de plaats van de ontvanger US volgens de brongegevens van FDM &#x200B;](assets/ruleeditorfdm-1-1.png) is

   Regel om de geselecteerde tekst te tonen als de plaats van de ontvanger volgens de brongegevens van FDM US is

   * Terwijl het creëren van of het uitgeven van een regel, kunt u ![&#x200B; icon_resize &#x200B;](assets/icon_resize.png) (Resize) ook selecteren om de Create lijn uit te breiden/geef de dialoog van de Regel uit. Met het dialoogvenster Uitgebreide en volledig venster kunt u eigenschappen en variabelen van het formuliergegevensmodel slepen en neerzetten om regels samen te stellen. Selecteer Opnieuw vergroten/verkleinen om terug te gaan naar het dialoogvenster Regel maken.
   * U kunt ook meerdere voorwaarden in een regel maken.
   * U kunt ook overlappende regels maken, waarin een regel wordt toegepast op een deel van een inhoud waarop al een regel is toegepast.

1. Selecteer **[!UICONTROL Done]** .

   De regel wordt toegepast. De tekst of inhoud waarop de regel wordt toegepast, wordt groen gemarkeerd. Wanneer u de cursor boven de linkergreep van de markering houdt, wordt de toegepaste regel weergegeven.

   ![&#x200B; toegepaste heersetekst &#x200B;](assets/appliedruletext.png)

   Als u op de linkerhandgreep van de toegepaste regel klikt, kunt u de regel bewerken of verwijderen.

## Tekst opmaken {#formatting}

Tijdens het maken of bewerken van tekst verandert de werkbalk afhankelijk van het type bewerkingen dat u wilt uitvoeren: Alinea, Uitlijning of Lijst:

![&#x200B; Uitgezochte type van toolbar &#x200B;](do-not-localize/toolbarselection.png)

Selecteer het type werkbalk: Alinea, Uitlijning of Lijst

![&#x200B; Doopvont het uitgeven toolbar &#x200B;](do-not-localize/paragraphtoolbar.png)

Werkbalk voor bewerken van lettertypen

![&#x200B; de toolbar van de Groepering &#x200B;](assets/alignmenttoolbar.png)

Uitlijning, werkbalk

![&#x200B; van de Lijst toolbar &#x200B;](do-not-localize/listingtoolbar.png)

Aanbiedingswerkbalk

### Tekstgedeelten markeren/benadrukken {#highlight}

Als u delen van tekst in een bewerkbaar documentfragment\benadrukt, selecteert u de tekst en selecteert u Markeringskleur.

![&#x200B; textbackgroundcolorapplied-1 &#x200B;](assets/textbackgroundcolorapplied-1.png)

U kunt of een basiskleur `**[A]**` direct selecteren in het Basispalet van Kleuren of **Uitgezocht** selecteren na het gebruiken van de schuif `**[B]**` om de aangewezen schaduw van de kleur te kiezen.

U kunt ook naar het tabblad Geavanceerd gaan om de juiste kleurtoon, helderheid en verzadiging `**[C]**` te selecteren en vervolgens Selecteren `**[D]**` selecteren om de tekst te markeren.

![&#x200B; textbackgroundcolor-2 &#x200B;](assets/textbackgroundcolor-2.png)

### Opgemaakte tekst plakken {#paste}

Als u een of meer tekstalinea&#39;s wilt hergebruiken die in een andere toepassing voorkomen, zoals Microsoft® Word- of HTML-pagina&#39;s, kopieert en plakt u de tekst in de teksteditor. De opmaak van de gekopieerde tekst blijft behouden in de teksteditor.

U kunt een of meer alinea&#39;s tekst in een bewerkbaar tekstdocumentfragment kopiëren en plakken. U hebt bijvoorbeeld een Microsoft® Word-document met een lijst met geldige verblijfstitels, zoals:

![&#x200B; pastetextmsword-2 &#x200B;](assets/pastetextmsword-2.png)

U kunt de tekst rechtstreeks vanuit het Microsoft® Word-document naar een bewerkbaar tekstdocumentfragment kopiëren en plakken. De opmaak, zoals een lijst met opsommingstekens, lettertype en tekstkleur, blijft behouden in het tekstdocumentfragment.

![&#x200B; pastetexteditablemodule-1 &#x200B;](assets/pastetexteditablemodule-1.png)

>[!NOTE]
>
>Het formatteren van gekleefde tekst, echter, heeft sommige [&#x200B; beperkingen &#x200B;](https://helpx.adobe.com/aem-forms/kb/cm-copy-paste-text-limitations.html).

## Speciale tekens in tekst invoegen {#special}

Voeg zo nodig speciale tekens in het documentfragment in. U kunt bijvoorbeeld het palet Speciale tekens gebruiken om het volgende in te voegen:

* Valutasymbolen zoals €, ¥ en £
* Wiskundige symbolen zoals A, Ö, ∂ en ^
* Interpunctiesymbolen zoals ‟ en &quot;

![&#x200B; specicharacters-2 &#x200B;](assets/specialcharacters-2.png)

Teksteditor heeft ingebouwde ondersteuning voor 210 speciale tekens. Admin kan [&#x200B; steun voor meer/douane speciale karakters door aanpassing &#x200B;](/help/forms/using/custom-special-characters.md) toevoegen.

## Tekst zoeken en vervangen {#searching}

Wanneer u werkt met tekstdocumentfragmenten die een grote hoeveelheid tekst bevatten, moet u zoeken naar een specifieke tekstreeks. U moet mogelijk ook een specifieke tekenreeks vervangen door een alternatieve tekenreeks.

Met de functie Zoeken en vervangen kunt u elke tekenreeks in een tekstdocumentfragment zoeken en vervangen. De functie bevat ook een krachtige zoekopdracht met een reguliere expressie.

1. Open een fragment van het tekstdocument voor [&#x200B; het uitgeven &#x200B;](#edittext).
1. Selecteer **[!UICONTROL Find & Replace]** .

1. Typ de tekst die u wilt doorzoeken in het tekstvak **[!UICONTROL Find]** en de nieuwe tekst (vervangende tekst) in het tekstvak **[!UICONTROL Replace]** en selecteer **[!UICONTROL Replace]** .

1. Als de gezochte tekst wordt gevonden, wordt de tekst vervangen door de vervangingstekst.

   * Als er een ander exemplaar van de zoektekst wordt gevonden, wordt dat exemplaar gemarkeerd in het tekstdocumentfragment. Als u nogmaals **[!UICONTROL Replace]** selecteert, wordt de gemarkeerde instantie vervangen en gaat de cursor verder als een derde instantie wordt gevonden.
   * Als er geen andere instantie wordt gevonden, wordt in het dialoogvenster Zoeken en vervangen een bericht weergegeven: Einde van module bereikt.

   U kunt ook Alles vervangen selecteren om alle overeenkomsten in één keer te vervangen.

   Zoeken en vervangen bevat ook een krachtige zoekopdracht voor reguliere expressies. Als u regex wilt gebruiken in uw zoekopdracht, selecteert u **[!UICONTROL Reg ex]** en selecteert u vervolgens **[!UICONTROL Find]** of **[!UICONTROL Replace]** .
