---
title: Voorwaarden voor interactieve communicatie
description: Het creëren en het uitgeven van voorwaardelementen die in Interactieve Mededelingen moeten worden gebruikt - de voorwaarde is één van de vier soorten documentfragmenten die worden gebruikt om Interactieve Mededelingen te bouwen. De andere drie zijn teksten, lijsten, en lay-outfragmenten.
topic-tags: interactive-communications
products: SG_EXPERIENCEMANAGER/6.5/FORMS
docset: aem65
feature: Interactive Communication
exl-id: 0c0dc6a2-b889-4516-8e08-1e9d31be2cce
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1452'
ht-degree: 0%

---

# Voorwaarden voor interactieve communicatie{#conditions-in-interactive-communications}

Het creëren en het uitgeven van voorwaardelementen die in Interactieve Mededelingen moeten worden gebruikt - de voorwaarde is één van de vier soorten documentfragmenten die worden gebruikt om Interactieve Mededelingen te bouwen. De andere drie zijn teksten, lijsten, en lay-outfragmenten.

## Overzicht {#overview}

Voorwaarde is een documentfragment dat u kunt opnemen in een interactieve communicatie. De andere documentfragmenten zijn [text](../../forms/using/texts-interactive-communications.md), lijst en lay-outfragment. De voorwaarden laten u toe om één of meerdere contextafhankelijke activa te bepalen die in een Interactieve Mededeling inbegrepen worden die op de verstrekte gegevens en de regels wordt gebaseerd.

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

## Voorwaarde maken {#createcondition}

1. Selecteren **[!UICONTROL Forms]** > **[!UICONTROL Document Fragments]**.
1. Selecteren **[!UICONTROL Create]** > **[!UICONTROL Condition]**.
1. Geef de volgende informatie op:

   * **[!UICONTROL Title]**: (Optioneel) Voer de titel voor de voorwaarde in. Titels hoeven niet uniek te zijn en kunnen speciale tekens en niet-Engelse tekens bevatten. De voorwaarden worden verwezen door hun titels (indien beschikbaar) zoals in duimnagels en eigenschappen.
   * **[!UICONTROL Name]**: De unieke naam voor de voorwaarde, in een map. Geen twee documentfragmenten (tekst, voorwaarde of lijst) in een staat kunnen bestaan met dezelfde naam in een map. In het veld Naam kunt u alleen Engelse tekens, cijfers en afbreekstreepjes invoeren. Het veld Naam wordt automatisch ingevuld op basis van het veld Titel. De speciale tekens, spaties, getallen en niet-Engelse tekens die in het veld Titel zijn ingevoerd, worden vervangen door afbreekstreepjes in het veld Naam. Hoewel de waarde in het veld Titel automatisch naar de naam wordt gekopieerd, kunt u de waarde bewerken.

   * **[!UICONTROL Description]**: Typ een beschrijving van het documentfragment.
   * **[!UICONTROL Form Data Model]**: Selecteer desgewenst het keuzerondje Formuliergegevensmodel om de voorwaarde te maken op basis van een formuliergegevensmodel. Wanneer u het keuzerondje Formuliergegevensmodel selecteert, **[!UICONTROL Form Data Model]** wordt weergegeven. Blader naar een formuliergegevensmodel en selecteer dit. Zorg tijdens het creëren van voorwaarde voor een Interactieve Communicatie, dat u het zelfde gegevensmodel gebruikt dat u in Interactieve Communicatie van plan bent te gebruiken. Zie voor meer informatie over het formuliergegevensmodel [Gegevensintegratie](../../forms/using/data-integration.md).

   * **[!UICONTROL Tags]**: Als u een aangepaste tag wilt maken, typt u desgewenst een waarde in het tekstveld en selecteert u Enter. Wanneer u deze voorwaarde opslaat, worden de nieuwe tags gemaakt.

1. Selecteren **[!UICONTROL Next]**.

   De pagina Voorwaarde maken wordt weergegeven.

   ![schepping](assets/createcondition.png)

1. Selecteren **[!UICONTROL Add Assets]**.

   De pagina Elementen selecteren wordt weergegeven en hierin worden de beschikbare teksten, lijsten, voorwaarden en afbeeldingen weergegeven die u in de voorwaarde kunt toevoegen.

   >[!NOTE]
   >
   >Alleen op basis van geen gemaakte, nieuw gemaakte elementen en op FDM gebaseerde elementen (gemaakt met dezelfde FDM als de voorwaarde die wordt gemaakt) worden weergegeven op de pagina Elementen selecteren.

1. Selecteer de desbetreffende elementen die u in de voorwaarde wilt opnemen en selecteer vervolgens **[!UICONTROL Done]**.

   De pagina Voorwaarde maken wordt weergegeven met de toegevoegde elementen.

   ![createconditionassetsadd](assets/createconditionassetsadd.png)

   U kunt de volgende opties gebruiken om elementen in een bepaalde situatie te beheren:

   ![createconditionscreenassetsaddedannoted](assets/createconditionscreenassetsaddedannotated.png)

   **[A] Wijziging negeren.** Selecteer dit pictogram om de wijzigingen in het element en de regel in de voorwaarde af te wijzen.
   **[B] Wijziging accepteren.** Selecteer dit pictogram om de wijzigingen te accepteren die u hebt aangebracht in het element en de regel in de voorwaarde.
   **[C] Item dupliceren.** Selecteer dit pictogram om een kopie van het element te maken samen met de eventueel toegepaste regel in de voorwaarde. Vervolgens kunt u doorgaan met het bewerken van de regel en het element voor gedupliceerde elementen. Het dupliceren van een element is handig voor het maken van vergelijkbare regels voor het weergeven van alternatieve elementen op basis van een bepaalde context.
   **[D] Voorvertoning weergeven.** Selecteer dit pictogram om een voorvertoning van het element weer te geven op de pagina Voorwaarde maken\bewerken.
   **&#39;server&#39; opnieuw ordenen.** Selecteer dit pictogram en houd het ingedrukt om elementen te slepen en neer te zetten om ze binnen een voorwaarde opnieuw te rangschikken.

   U kunt de volgende opties selecteren om op te geven hoe de voorwaarde zich gedraagt bij uitvoering:

   * **Meerdere resultaten evaluatie uitgeschakeld\Meerdere resultaten evaluatie ingeschakeld**: Wanneer deze optie is ingeschakeld (wordt weergegeven als &quot;Meerdere resultaten met evaluatie ingeschakeld&quot;), worden alle regels geëvalueerd en is het resultaat de som van alle werkelijke regels. Als deze optie is uitgeschakeld (wordt &#39;&#39;Multiple Results Evaluation Disabled&#39; weergegeven), wordt alleen de eerste regel die waar wordt gevonden, geëvalueerd en wordt deze de uitvoer van de voorwaarde.

   * **Pagina-einde**: Selecteer deze optie ( ![break](assets/break.png)) om een pagina-einde toe te voegen tussen de elementen van de voorwaarden. Wanneer deze optie niet is geselecteerd ( ![noord](assets/nobreak.png)), als een voorwaarde overloopt naar de volgende pagina in de afdrukuitvoer, wordt de hele voorwaarde verplaatst naar de volgende pagina in plaats van de pagina tussen de elementen in de voorwaarde te verbreken.

1. Selecteren **[!UICONTROL Create Rule]** om regels toe te voegen om de elementen weer te geven of te verbergen. Als u variabelen in de regels wilt gebruiken, raadpleegt u [variabelen maken](#variables). Zie voor meer informatie [Regels toevoegen aan voorwaarde](#ruleeditor).

   De gemaakte regels worden weergegeven in de kolom REGEL in het scherm Voorwaarde maken.

   ![createconditionscreenrulings toegevoegd](assets/createconditionscreenrulesadded.png)

   >[!NOTE]
   >
   >U kunt elementen in uw voorwaarde invoegen waarop al regels of herhalingen zijn toegepast.

1. Selecteren **[!UICONTROL Save]**.

   De voorwaarde wordt gemaakt. Nu kunt u aan het gebruiken van de voorwaarde als bouwsteen te werk gaan terwijl het creëren van een Interactieve Communicatie.

   >[!NOTE]
   >
   >Als u een nieuwe of bewerkte voorwaarde wilt opslaan, moet u ten minste één regel hebben voor elk element dat in de voorwaarde is toegevoegd.

## Een voorwaarde bewerken {#edit-a-condition}

U kunt een voorwaarde bewerken door de volgende stappen uit te voeren. U kunt een voorwaarde ook bewerken vanuit een interactieve communicatie door Fragment bewerken te selecteren in het pop-upmenu.

1. Selecteren **[!UICONTROL Forms]** > **[!UICONTROL Document Fragments]**.
1. Navigeer naar de voorwaarde en selecteer deze.
1. Selecteren **[!UICONTROL Edit]**.
1. Breng de gewenste wijzigingen aan in de voorwaarde. Voor meer informatie over de informatie kunt u in een voorwaarde veranderen, zie [Voorwaarde maken](#createcondition).
1. Selecteren **[!UICONTROL Save]** en selecteer vervolgens **[!UICONTROL Close]**.

## Voorwaardelijke regels maken {#ruleeditor}

Met regeleditor in een voorwaarde kunt u regels maken om elementen weer te geven of te verbergen op basis van **vooraf ingestelde voorwaarden**. Deze voorwaarden kunnen worden geconstrueerd op basis van:

* Tekenreeksen
* Getallen
* Wiskundige expressies
* Datums
* Eigenschappen van gekoppeld formuliergegevensmodel
* Alle [variabelen](#variables) die u hebt gemaakt

### Regel maken in voorwaarde {#create-rule-in-condition}

1. Selecteer tijdens het maken of bewerken van een voorwaarde ![ruleeditoricon](assets/ruleeditoricon.png) (Redacteur van de Regel) pictogram voor de relevante activa.

   Het dialoogvenster Regel maken wordt weergegeven. Naast tekenreeks, nummer, wiskundige expressie en datum zijn in de Regeleditor ook de volgende opties beschikbaar voor het maken van instructies van de regels:

   * Eigenschappen van gekoppeld formuliergegevensmodel
   * Alle [variabelen](#variables) die u hebt gemaakt.

   ![createruleus](assets/createruledialog.png)

   Selecteer de gewenste optie die u wilt evalueren.

   >[!NOTE]
   >
   >Inzamelingseigenschap wordt niet ondersteund voor het maken van regels voor het weergeven van elementen.

1. Selecteer de juiste operator om de regel te evalueren, zoals Is gelijk aan, Bevat en Begint met.
1. Voeg de evaluatiereferentie, tekenreeks, gegevensmodeleigenschap, variabele of datum in.

   ![Regel om een element te tonen wanneer het beleidstype standaard is](assets/ruleincondition.png)

   Regel om een element te tonen wanneer het beleidstype standaard is

   * Tijdens het maken of bewerken van een regel kunt u ook ![icon_resize](assets/icon_resize.png) (Formaat wijzigen) om het dialoogvenster Regel maken/regel bewerken uit te vouwen. Met het uitgebreide dialoogvenster voor een volledig venster kunt u [variabelen](#variables) om regels samen te stellen. Selecteer Opnieuw vergroten/verkleinen om terug te keren naar het normale dialoogvenster Regel maken.

   * U kunt ook meerdere voorwaarden in een regel maken.

1. Selecteren **[!UICONTROL Done]**.

   De regel wordt toegepast op het element.

## Variabelen in een voorwaarde maken en gebruiken {#variables}

Tijdens het maken of bewerken van een regel in een voorwaarde kunt u ![icon_resize](assets/icon_resize.png) (Formaat wijzigen) om het dialoogvenster Regel maken uit te vouwen.\n Met het uitgebreide dialoogvenster van een volledig venster kunt u het volgende doen:

* Variabelen in de regel maken en gebruiken
* De eigenschappen en variabelen van het formuliergegevensmodel slepen en neerzetten in de regel

Selecteer Opnieuw vergroten/verkleinen om terug te gaan naar het dialoogvenster Regel maken.\nRegel bewerken.

### Variabelen maken {#create-variables}

1. Tijdens het maken of bewerken van een regel in een voorwaarde kunt u ![icon_resize](assets/icon_resize.png) (Formaat wijzigen) om het dialoogvenster Regel maken uit te vouwen.\n

   Het dialoogvenster Uitgebreid en volledig venster wordt weergegeven.

   ![uitgebreide dialoog](assets/expandededitruledialog.png)

1. Selecteer in het linkerdeelvenster de optie **[!UICONTROL Variables]**.

   Het deelvenster Variabelen wordt weergegeven.

   ![expandeverschuivende variabelen](assets/expandededitrulevariables.png)

1. Selecteren **[!UICONTROL Create]**.

   Het deelvenster Variabelen maken wordt weergegeven.

1. Voer de volgende gegevens in en selecteer **[!UICONTROL Create]**:

   * **[!UICONTROL Name]**: Naam van de variabele.
   * **[!UICONTROL Description]**: Voer optioneel een beschrijving van de variabele in.
   * **[!UICONTROL Type]**: Selecteer een type variabele: String, Number, Boolean of Date.
   * **[!UICONTROL Allow Specific Values Only]**: Voor de variabelen van het Koord en van het Aantal, kunt u ervoor zorgen dat de agent van een specifieke reeks waarden voor placeholder in de Agent UI kiest. Als u de reeks waarden wilt opgeven, selecteert u deze optie en geeft u door komma&#39;s gescheiden waarden op die zijn toegestaan in het dialoogvenster **[!UICONTROL Values]** veld.

1. Selecteren **[!UICONTROL Create]**.

   De variabele wordt gemaakt en vermeld in het deelvenster Variabelen.

1. Als u een variabele in de regel wilt invoegen, sleept u de variabele naar een tijdelijke aanduiding voor een optie in de regel.
1. Nadat u een geldige regel hebt samengesteld, selecteert u **[!UICONTROL Done]**.

   Ga zo nodig verder met het aanbrengen van wijzigingen in de voorwaarde en sla deze op.
