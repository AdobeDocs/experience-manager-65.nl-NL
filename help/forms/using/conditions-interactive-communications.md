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
translation-type: tm+mt
source-git-commit: 317fadfe48724270e59644d2ed9a90fbee95cf9f

---


# Voorwaarden voor interactieve communicatie{#conditions-in-interactive-communications}

Het creëren en het uitgeven van voorwaardelementen die in Interactieve Mededelingen moeten worden gebruikt - de voorwaarde is één van de vier soorten documentfragmenten die worden gebruikt om Interactieve Mededelingen te bouwen. De andere drie zijn teksten, lijsten, en lay-outfragmenten.

## Overzicht {#overview}

Voorwaarde is een documentfragment dat u kunt opnemen in een interactieve communicatie. De andere documentfragmenten zijn [tekst](../../forms/using/texts-interactive-communications.md)-, lijst- en layoutfragmenten. De voorwaarden laten u toe om één of meerdere contextafhankelijke activa te bepalen die in een Interactieve Mededeling inbegrepen worden die op de verstrekte gegevens en de regels wordt gebaseerd.

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

1. Selecteer **[!UICONTROL Formulieren]** > **[!UICONTROL Documentfragmenten]**.
1. Selecteer **[!UICONTROL Maken]** > **[!UICONTROL Voorwaarde]**.
1. Geef de volgende informatie op:

   * **[!UICONTROL Titel]**: (Optioneel) Voer de titel voor de voorwaarde in. Titels hoeven niet uniek te zijn en kunnen speciale tekens en niet-Engelse tekens bevatten. De voorwaarden worden verwezen door hun titels (indien beschikbaar) zoals in duimnagels en eigenschappen.
   * **[!UICONTROL Naam]**: De unieke naam voor de voorwaarde, in een map. Geen twee documentfragmenten (tekst, voorwaarde of lijst) in een staat kunnen bestaan met dezelfde naam in een map. In het veld Naam kunt u alleen Engelse tekens, cijfers en afbreekstreepjes invoeren. Het veld Naam wordt automatisch ingevuld op basis van het veld Titel. De speciale tekens, spaties, getallen en niet-Engelse tekens die in het veld Titel zijn ingevoerd, worden vervangen door afbreekstreepjes in het veld Naam. Hoewel de waarde in het veld Titel automatisch naar de naam wordt gekopieerd, kunt u de waarde bewerken.

   * **[!UICONTROL Omschrijving]**: Typ een beschrijving van het documentfragment.
   * **[!UICONTROL Formuliergegevensmodel]**: Selecteer desgewenst het keuzerondje Formuliergegevensmodel om de voorwaarde te maken op basis van een formuliergegevensmodel. Als u het keuzerondje Formuliergegevensmodel selecteert, wordt het veld **[!UICONTROL Formuliergegevensmodel]** weergegeven. Blader naar een formuliergegevensmodel en selecteer dit. Zorg tijdens het creëren van voorwaarde voor een Interactieve Communicatie, dat u het zelfde gegevensmodel gebruikt dat u in Interactieve Communicatie van plan bent te gebruiken. Zie [Gegevensintegratie](../../forms/using/data-integration.md)voor meer informatie over het formuliergegevensmodel.

   * **[!UICONTROL Tags]**: Als u een aangepaste tag wilt maken, typt u een waarde in het tekstveld en tikt u op Enter. Wanneer u deze voorwaarde opslaat, worden de nieuwe tags gemaakt.

1. Tik op **[!UICONTROL Volgende]**.

   De pagina Voorwaarde maken wordt weergegeven.

   ![schepping](assets/createcondition.png)

1. Tik op Elementen **** toevoegen.

   De pagina Elementen selecteren wordt weergegeven en hierin worden de beschikbare teksten, lijsten, voorwaarden en afbeeldingen weergegeven die u in de voorwaarde kunt toevoegen.

   >[!NOTE]
   >
   >Alleen op basis van geen gemaakte, nieuw gemaakte elementen en op FDM gebaseerde elementen (die zijn gemaakt met dezelfde FDM als de voorwaarde die wordt gemaakt) worden weergegeven op de pagina Elementen selecteren.

1. Tik op de juiste elementen om deze te selecteren en vervolgens op **[!UICONTROL Gereed]** te tikken.

   De pagina Voorwaarde maken wordt weergegeven met de toegevoegde elementen.

   ![createconditionassetsadd](assets/createconditionassetsadd.png)

   U kunt de volgende opties gebruiken om elementen in een bepaalde situatie te beheren:

   ![createconditionscreenassetsaddedannoted](assets/createconditionscreenassetsaddedannotated.png)

   **[Een]wijziging negeren.**Tik op dit pictogram om de wijzigingen in het element en de regel in de voorwaarde af te wijzen.   **[B]Wijziging accepteren.**Tik op dit pictogram om de wijzigingen te accepteren die u hebt aangebracht in het element en de regel in de voorwaarde.   **[Item dupliceren].**Tik op dit pictogram om een kopie van het element te maken, samen met de eventuele toegepaste regel in de voorwaarde. Vervolgens kunt u doorgaan met het bewerken van de regel en het element voor gedupliceerde elementen. Het dupliceren van een element is handig voor het maken van vergelijkbare regels voor het weergeven van alternatieve elementen op basis van een bepaalde context.   **[Voorvertoning weergeven].**Tik op dit pictogram om een voorvertoning van het element weer te geven op de pagina Voorwaarde maken\bewerken.   **&#39;server&#39; opnieuw ordenen.** Tik op dit pictogram en houd dit ingedrukt om elementen te slepen en neer te zetten om ze binnen een voorwaarde opnieuw te ordenen.

   U kunt de volgende opties selecteren om op te geven hoe de voorwaarde zich gedraagt bij uitvoering:

   * **Meerdere resultaten evaluatie uitgeschakeld\Meerdere resultaten evaluatie ingeschakeld**: Wanneer deze optie wordt toegelaten (verschijnt als &quot;Meerdere Resultaten Toegelaten Evaluatie), worden alle regels geëvalueerd en het resultaat is de som van alle ware regels. Als deze optie is uitgeschakeld (wordt &#39;&#39;Multiple Results Evaluation Disabled&#39; weergegeven), wordt alleen de eerste regel die waar wordt gevonden, geëvalueerd en wordt deze de uitvoer van de voorwaarde.

   * **Pagina-einde**: Selecteer deze optie ( ![onderbreking](assets/break.png)) om een pagina-einde tussen de elementen van de voorwaarden toe te voegen. Als deze optie niet is geselecteerd ( ![nobreak](assets/nobreak.png)) en een voorwaarde overloopt naar de volgende pagina in de afgedrukte uitvoer, wordt de hele voorwaarde verschoven naar de volgende pagina in plaats van de pagina te verbreken tussen de elementen in de voorwaarde.

1. Tik op Regel **** maken om regels toe te voegen om de elementen weer te geven of te verbergen. Zie Variabelen [](#variables)maken als u variabelen in de regels wilt gebruiken. Zie [Regels toevoegen aan voorwaarde](#ruleeditor)voor meer informatie.

   De gemaakte regels worden weergegeven in de kolom REGEL in het scherm Voorwaarde maken.

   ![createconditionscreenrulings toegevoegd](assets/createconditionscreenrulesadded.png)

   >[!NOTE]
   >
   >U kunt elementen in uw voorwaarde invoegen waarop al regels of herhalingen zijn toegepast.

1. Tik op **[!UICONTROL Opslaan]**.

   De voorwaarde wordt gemaakt. Nu kunt u aan het gebruiken van de voorwaarde als bouwsteen verdergaan terwijl het creëren van een Interactieve Communicatie.

   >[!NOTE]
   >
   >Als u een nieuwe of bewerkte voorwaarde wilt opslaan, moet u ten minste één regel hebben voor elk element dat in de voorwaarde is toegevoegd.

## Een voorwaarde bewerken {#edit-a-condition}

U kunt een voorwaarde bewerken door de volgende stappen uit te voeren. U kunt een voorwaarde ook bewerken vanuit een interactieve communicatie door Fragment bewerken te selecteren in het pop-upmenu.

1. Selecteer **[!UICONTROL Formulieren]** > **[!UICONTROL Documentfragmenten]**.
1. Navigeer naar de voorwaarde en selecteer deze.
1. Tik op **[!UICONTROL Bewerken]**.
1. Breng de gewenste wijzigingen aan in de voorwaarde. Zie [Voorwaarde](#createcondition)maken voor meer informatie over de informatie die u in een voorwaarde kunt wijzigen.
1. Tik op **[!UICONTROL Opslaan]** en tik vervolgens op **[!UICONTROL Sluiten]**.

## Voorwaardelijke regels maken {#ruleeditor}

Met de regeleditor in een voorwaarde kunt u regels maken om elementen weer te geven of te verbergen op basis van **vooraf ingestelde voorwaarden**. Deze voorwaarden kunnen worden geconstrueerd op basis van:

* Tekenreeksen
* Getallen
* Wiskundige expressies
* Datums
* Eigenschappen van gekoppeld formuliergegevensmodel
* Alle [variabelen](#variables) die u hebt gemaakt

### Regel maken in voorwaarde {#create-rule-in-condition}

1. Tik tijdens het maken of bewerken van een voorwaarde op ![het pictogram](assets/ruleeditoricon.png) Regeleditor (Rule Editor) voor het desbetreffende element.

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

   * Wanneer u een regel maakt of bewerkt, kunt u ook op ![icon_resize](assets/icon_resize.png) (Resize wijzigen) tikken om het dialoogvenster Regel maken/Regel bewerken uit te vouwen. Met het uitgebreide dialoogvenster voor een volledig venster kunt u [variabelen](#variables) maken om regels samen te stellen. Tik nogmaals op Vergroten/verkleinen om terug te keren naar het normale dialoogvenster Regel maken.

   * U kunt ook meerdere voorwaarden in een regel maken.

1. Tik **[!UICONTROL op Gereed]**.

   De regel wordt toegepast op het element.

## Variabelen in een voorwaarde maken en gebruiken {#variables}

Tijdens het maken of bewerken van een regel in een voorwaarde kunt u op ![icon_resize](assets/icon_resize.png) (Resize) tikken om het dialoogvenster Regel maken uit te vouwen\Edit Rule. Met het uitgebreide dialoogvenster voor een volledig venster kunt u:

* Variabelen in de regel maken en gebruiken
* De eigenschappen en variabelen van het formuliergegevensmodel slepen en neerzetten in de regel

Tik nogmaals op Vergroten/verkleinen om terug te keren naar het dialoogvenster Regel maken.\Bewerk regel.

### Variabelen maken {#create-variables}

1. Tijdens het maken of bewerken van een regel in een voorwaarde kunt u op ![icon_resize](assets/icon_resize.png) (Resize) tikken om het dialoogvenster Regel maken uit te vouwen\Edit Rule.

   Het dialoogvenster Uitgebreid en volledig venster wordt weergegeven.

   ![uitgebreide dialoog](assets/expandededitruledialog.png)

1. Tik in het linkerdeelvenster op **[!UICONTROL Variabelen]**.

   Het deelvenster Variabelen wordt weergegeven.

   ![expandeverschuivende variabelen](assets/expandededitrulevariables.png)

1. Tik op **[!UICONTROL Maken]**.

   Het deelvenster Variabelen maken wordt weergegeven.

1. Voer de volgende gegevens in en tik op **[!UICONTROL Maken]**:

   * **[!UICONTROL Naam]**: Naam van de variabele.
   * **[!UICONTROL Omschrijving]**: Voer desgewenst een beschrijving van de variabele in.
   * **[!UICONTROL Type]**: Selecteer een type variabele: Tekenreeks, Aantal, Boolean of Datum.
   * **[!UICONTROL Alleen]** specifieke waarden toestaan: Voor de variabelen van het Koord en van het Aantal, kunt u ervoor zorgen dat de agent van een specifieke reeks waarden voor placeholder in de Agent UI kiest. Als u de reeks waarden wilt opgeven, selecteert u deze optie en geeft u door komma&#39;s gescheiden waarden op die zijn toegestaan in het veld **[!UICONTROL Waarden]** .

1. Tik op **[!UICONTROL Maken]**.

   De variabele wordt gemaakt en vermeld in het deelvenster Variabelen.

1. Als u een variabele in de regel wilt invoegen, sleept u de variabele naar een tijdelijke aanduiding voor een optie in de regel.
1. Tik op **[!UICONTROL Gereed]** nadat u een geldige regel hebt gemaakt.

   Ga zo nodig verder met het aanbrengen van wijzigingen in de voorwaarde en sla deze op.

