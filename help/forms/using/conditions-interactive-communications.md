---
title: Voorwaarden voor interactieve communicatie
seo-title: Voorwaarden voor interactieve communicatie
description: Het creëren en het uitgeven van voorwaardelementen die in Interactieve Mededelingen moeten worden gebruikt - de voorwaarde is één van de vier soorten documentfragmenten die worden gebruikt om Interactieve Mededelingen te bouwen. De andere drie zijn teksten, lijsten, en lay-outfragmenten.
seo-description: Het creëren van en het uitgeven van voorwaarden die in Interactieve Mededelingen moeten worden gebruikt
uuid: c98f02d5-1769-46dd-ab35-6e8145a24939
topic-tags: interactive-communications
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: fe59d260-d392-4d6f-bb7e-2f2a1d701f51
docset: aem65
feature: Interactieve communicatie
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '1471'
ht-degree: 0%

---


# Voorwaarden in interactieve communicatie{#conditions-in-interactive-communications}

Het creëren en het uitgeven van voorwaardelementen die in Interactieve Mededelingen moeten worden gebruikt - de voorwaarde is één van de vier soorten documentfragmenten die worden gebruikt om Interactieve Mededelingen te bouwen. De andere drie zijn teksten, lijsten, en lay-outfragmenten.

## Overzicht {#overview}

Voorwaarde is een documentfragment dat u kunt opnemen in een interactieve communicatie. De andere documentfragmenten zijn [text](../../forms/using/texts-interactive-communications.md), list, en lay-outfragment. De voorwaarden laten u toe om één of meerdere contextafhankelijke activa te bepalen die in een Interactieve Mededeling inbegrepen worden die op de verstrekte gegevens en de regels wordt gebaseerd.

Voorbeelden:

* Geef in een creditcardafschrift de jaarlijkse kosten van de creditcard en de afbeelding van de creditcard weer op basis van het type creditcard van de klant.
* In een herinnering voor de verzekeringspremie kunt u berekeningen van de belasting weergeven op basis van de belastingen van de staat van de klant.

De elementen in de voorwaarden die worden gerenderd op basis van de toegepaste regels en de waarden die aan de regel worden doorgegeven. De regels in de voorwaarden kunnen waarden in de volgende soorten gegevens controleren:

* Eigenschap van gekoppeld formuliergegevensmodel
* Alle variabelen die u in de voorwaarde maakt
* Tekenreeksen
* Getallen
* Wiskundige expressies
* Datums

## Voorwaarde {#createcondition} maken

1. Selecteer **[!UICONTROL Forms]** > **[!UICONTROL Document Fragments]**.
1. Selecteer **[!UICONTROL Create]** > **[!UICONTROL Condition]**.
1. Geef de volgende informatie op:

   * **[!UICONTROL Title]**: (Optioneel) Voer de titel voor de voorwaarde in. Titels hoeven niet uniek te zijn en kunnen speciale tekens en niet-Engelse tekens bevatten. De voorwaarden worden verwezen door hun titels (indien beschikbaar) zoals in duimnagels en eigenschappen.
   * **[!UICONTROL Name]**: De unieke naam voor de voorwaarde, in een map. Geen twee documentfragmenten (tekst, voorwaarde of lijst) in een staat kunnen bestaan met dezelfde naam in een map. In het veld Naam kunt u alleen Engelse tekens, cijfers en afbreekstreepjes invoeren. Het veld Naam wordt automatisch ingevuld op basis van het veld Titel. De speciale tekens, spaties, getallen en niet-Engelse tekens die in het veld Titel zijn ingevoerd, worden vervangen door afbreekstreepjes in het veld Naam. Hoewel de waarde in het veld Titel automatisch naar de naam wordt gekopieerd, kunt u de waarde bewerken.

   * **[!UICONTROL Description]**: Typ een beschrijving van het documentfragment.
   * **[!UICONTROL Form Data Model]**: Selecteer desgewenst het keuzerondje Formuliergegevensmodel om de voorwaarde te maken op basis van een formuliergegevensmodel. Wanneer u het keuzerondje Formuliergegevensmodel selecteert, wordt het veld **[!UICONTROL Form Data Model]** weergegeven. Blader naar een formuliergegevensmodel en selecteer dit. Zorg tijdens het creëren van voorwaarde voor een Interactieve Communicatie, dat u het zelfde gegevensmodel gebruikt dat u in Interactieve Communicatie van plan bent te gebruiken. Zie [Gegevensintegratie](../../forms/using/data-integration.md) voor meer informatie over het formuliergegevensmodel.

   * **[!UICONTROL Tags]**: Als u een aangepaste tag wilt maken, typt u een waarde in het tekstveld en tikt u op Enter. Wanneer u deze voorwaarde opslaat, worden de nieuwe tags gemaakt.

1. Tik op **[!UICONTROL Next]**.

   De pagina Voorwaarde maken wordt weergegeven.

   ![schepping](assets/createcondition.png)

1. Tik op **[!UICONTROL Add Assets]**.

   De pagina Elementen selecteren wordt weergegeven en hierin worden de beschikbare teksten, lijsten, voorwaarden en afbeeldingen weergegeven die u in de voorwaarde kunt toevoegen.

   >[!NOTE]
   >
   >Alleen op basis van geen gemaakte, nieuw gemaakte elementen en op FDM gebaseerde elementen (die zijn gemaakt met dezelfde FDM als de voorwaarde die wordt gemaakt) worden weergegeven op de pagina Elementen selecteren.

1. Tik op de desbetreffende elementen om deze te selecteren en tik vervolgens op **[!UICONTROL Done]**.

   De pagina Voorwaarde maken wordt weergegeven met de toegevoegde elementen.

   ![createconditionassetsadd](assets/createconditionassetsadd.png)

   U kunt de volgende opties gebruiken om elementen in een bepaalde situatie te beheren:

   ![createconditionscreenassetsaddedannoted](assets/createconditionscreenassetsaddedannotated.png)

   **[Wijziging van ] AReject.** Tik op dit pictogram om de wijzigingen in het element en de regel in de voorwaarde af te wijzen.
   **[Wijziging ] van BAcept.** Tik op dit pictogram om de wijzigingen te accepteren die u hebt aangebracht in het element en de regel in de voorwaarde.
   **[] CDuplicate Asset.** Tik op dit pictogram om een kopie van het element te maken, samen met de eventuele toegepaste regel in de voorwaarde. Vervolgens kunt u doorgaan met het bewerken van de regel en het element voor gedupliceerde elementen. Het dupliceren van een element is handig voor het maken van vergelijkbare regels voor het weergeven van alternatieve elementen op basis van een bepaalde context.
   **[Voorvertoning ] DShow.** Tik op dit pictogram om een voorvertoning van het element weer te geven op de pagina Voorwaarde maken\bewerken.
   **&#39;server&#39; opnieuw ordenen.** Tik op dit pictogram en houd dit ingedrukt om elementen te slepen en neer te zetten om ze binnen een voorwaarde opnieuw te ordenen.

   U kunt de volgende opties selecteren om op te geven hoe de voorwaarde zich gedraagt bij uitvoering:

   * **Meerdere resultaten evaluatie uitgeschakeld\Meerdere resultaten evaluatie ingeschakeld**: Wanneer deze optie wordt toegelaten (verschijnt als &quot;Meerdere Resultaten Toegelaten Evaluatie), worden alle regels geëvalueerd en het resultaat is de som van alle ware regels. Als deze optie is uitgeschakeld (wordt &#39;&#39;Multiple Results Evaluation Disabled&#39; weergegeven), wordt alleen de eerste regel die waar wordt gevonden, geëvalueerd en wordt deze de uitvoer van de voorwaarde.

   * **Pagina-einde**: Selecteer deze optie ( ![onderbreking](assets/break.png)) om een pagina-einde tussen de elementen van de voorwaarden toe te voegen. Als deze optie niet is geselecteerd ( ![nobreak](assets/nobreak.png)) en een voorwaarde overloopt naar de volgende pagina in de afgedrukte uitvoer, wordt de hele voorwaarde verplaatst naar de volgende pagina in plaats van de pagina te verbreken tussen de elementen in de voorwaarde.

1. Tik **[!UICONTROL Create Rule]** om regels toe te voegen om de elementen weer te geven of te verbergen. Zie [Variabelen maken](#variables) om variabelen in de regels te gebruiken. Zie [Regels toevoegen aan voorwaarde](#ruleeditor) voor meer informatie.

   De gemaakte regels worden weergegeven in de kolom REGEL in het scherm Voorwaarde maken.

   ![createconditionscreenrulings toegevoegd](assets/createconditionscreenrulesadded.png)

   >[!NOTE]
   >
   >U kunt elementen in uw voorwaarde invoegen waarop al regels of herhalingen zijn toegepast.

1. Tik op **[!UICONTROL Save]**.

   De voorwaarde wordt gemaakt. Nu kunt u aan het gebruiken van de voorwaarde als bouwsteen verdergaan terwijl het creëren van een Interactieve Communicatie.

   >[!NOTE]
   >
   >Als u een nieuwe of bewerkte voorwaarde wilt opslaan, moet u ten minste één regel hebben voor elk element dat in de voorwaarde is toegevoegd.

## Een voorwaarde {#edit-a-condition} bewerken

U kunt een voorwaarde bewerken door de volgende stappen uit te voeren. U kunt een voorwaarde ook bewerken vanuit een interactieve communicatie door Fragment bewerken te selecteren in het pop-upmenu.

1. Selecteer **[!UICONTROL Forms]** > **[!UICONTROL Document Fragments]**.
1. Navigeer naar de voorwaarde en selecteer deze.
1. Tik op **[!UICONTROL Edit]**.
1. Breng de gewenste wijzigingen aan in de voorwaarde. Zie [Voorwaarde maken](#createcondition) voor meer informatie over de informatie die u in een voorwaarde kunt wijzigen.
1. Tik **[!UICONTROL Save]** en tik **[!UICONTROL Close]**.

## Regels maken in voorwaarde {#ruleeditor}

Gebruikend regelredacteur in een voorwaarde, kunt u regels tot stand brengen om activa te tonen of te verbergen die op **vooraf ingestelde voorwaarden** worden gebaseerd. Deze voorwaarden kunnen worden geconstrueerd op basis van:

* Tekenreeksen
* Getallen
* Wiskundige expressies
* Datums
* Eigenschappen van gekoppeld formuliergegevensmodel
* Eventuele [variabelen](#variables) die u hebt gemaakt

### Regel maken in voorwaarde {#create-rule-in-condition}

1. Tik tijdens het maken of bewerken van een voorwaarde op ![ruleeditorpictogram](assets/ruleeditoricon.png) (Regeleditor)-pictogram voor het desbetreffende element.

   Het dialoogvenster Regel maken wordt weergegeven. Naast tekenreeks, nummer, wiskundige expressie en datum zijn in de Regeleditor ook de volgende opties beschikbaar voor het maken van instructies van de regels:

   * Eigenschappen van gekoppeld formuliergegevensmodel
   * Eventuele [variabelen](#variables) die u hebt gemaakt.

   ![createruleus](assets/createruledialog.png)

   Selecteer de gewenste optie die u wilt evalueren.

   >[!NOTE]
   >
   >Inzamelingseigenschap wordt niet ondersteund voor het maken van regels voor het weergeven van elementen.

1. Selecteer de juiste operator om de regel te evalueren, zoals Is gelijk aan, Bevat en Begint met.
1. Voeg de evaluatiereferentie, tekenreeks, gegevensmodeleigenschap, variabele of datum in.

   ![Regel om een element te tonen wanneer het beleidstype standaard is](assets/ruleincondition.png)

   Regel om een element te tonen wanneer het beleidstype standaard is

   * Tijdens het creëren van of het uitgeven van een regel, kunt u ![icon_resize](assets/icon_resize.png) (Resize) ook tikken om de Create Regel/Edit dialoog van de Regel uit te breiden. Met het uitgebreide dialoogvenster voor een volledig venster kunt u [variabelen](#variables) maken om regels samen te stellen. Tik nogmaals op Vergroten/verkleinen om terug te keren naar het normale dialoogvenster Regel maken.

   * U kunt ook meerdere voorwaarden in een regel maken.

1. Tik op **[!UICONTROL Done]**.

   De regel wordt toegepast op het element.

## Variabelen maken en gebruiken in een voorwaarde {#variables}

Tijdens het creëren van of het uitgeven van een regel in een voorwaarde, kunt u ![icon_resize](assets/icon_resize.png) (Resize) tikken om de Create Regel uit te breiden \ geeft de dialoog van de Regel uit. Met het uitgebreide dialoogvenster voor een volledig venster kunt u:

* Variabelen in de regel maken en gebruiken
* De eigenschappen en variabelen van het formuliergegevensmodel slepen en neerzetten in de regel

Tik nogmaals op Vergroten/verkleinen om terug te keren naar het dialoogvenster Regel maken.\Bewerk regel.

### Variabelen {#create-variables} maken

1. Tijdens het creëren van of het uitgeven van een regel in een voorwaarde, kunt u ![icon_resize](assets/icon_resize.png) (Resize) tikken om de Create Regel uit te breiden \ geeft de dialoog van de Regel uit.

   Het dialoogvenster Uitgebreid en volledig venster wordt weergegeven.

   ![uitgebreide dialoog](assets/expandededitruledialog.png)

1. Tik in het linkervenster op **[!UICONTROL Variables]**.

   Het deelvenster Variabelen wordt weergegeven.

   ![expandeverschuivende variabelen](assets/expandededitrulevariables.png)

1. Tik op **[!UICONTROL Create]**.

   Het deelvenster Variabelen maken wordt weergegeven.

1. Voer de volgende informatie in en tik **[!UICONTROL Create]**:

   * **[!UICONTROL Name]**: Naam van de variabele.
   * **[!UICONTROL Description]**: Voer desgewenst een beschrijving van de variabele in.
   * **[!UICONTROL Type]**: Selecteer een type variabele: Tekenreeks, Aantal, Boolean of Datum.
   * **[!UICONTROL Allow Specific Values Only]**: Voor de variabelen van het Koord en van het Aantal, kunt u ervoor zorgen dat de agent van een specifieke reeks waarden voor placeholder in de Agent UI kiest. Als u de reeks waarden wilt opgeven, selecteert u deze optie en geeft u door komma&#39;s gescheiden waarden op die zijn toegestaan in het veld **[!UICONTROL Values]**.

1. Tik op **[!UICONTROL Create]**.

   De variabele wordt gemaakt en vermeld in het deelvenster Variabelen.

1. Als u een variabele in de regel wilt invoegen, sleept u de variabele naar een tijdelijke aanduiding voor een optie in de regel.
1. Tik **[!UICONTROL Done]** nadat u een geldige regel hebt gemaakt.

   Ga zo nodig verder met het aanbrengen van wijzigingen in de voorwaarde en sla deze op.

