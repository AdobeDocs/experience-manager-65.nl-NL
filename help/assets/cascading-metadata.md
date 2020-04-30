---
title: Trapsgewijze metagegevens in [!DNL Adobe Experience Manager Assets].
description: In dit artikel wordt beschreven hoe u trapsgewijze metagegevens voor elementen definieert.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 90f9c0b60d4b0878f56eefea838154bb7627066d

---


# Trapsgewijze metadata {#cascading-metadata}

Wanneer gebruikers de metagegevens van een element vastleggen, verschaffen ze informatie in de verschillende beschikbare velden. U kunt specifieke metagegevensvelden of veldwaarden weergeven die afhankelijk zijn van de opties die in de andere velden zijn geselecteerd. Een dergelijke voorwaardelijke weergave van metagegevens wordt trapsgewijze metagegevens genoemd. Met andere woorden, u kunt een afhankelijkheid maken tussen een bepaald metagegevensveld/een bepaalde waarde en een of meer velden en/of hun waarden.

Gebruik schema&#39;s voor metagegevens om regels voor de weergave van trapsgewijze metagegevens te definiëren. Als uw metagegevensschema bijvoorbeeld een elementtypeveld bevat, kunt u een relevante set velden definiëren die moet worden weergegeven op basis van het type element dat de gebruiker selecteert.

Hier volgen enkele gebruiksgevallen waarvoor u trapsgewijze metagegevens kunt definiëren:

* Indien een gebruikerslocatie is vereist, relevante plaatsnaam weergeven op basis van de keuze van het land en de staat van de gebruiker.
* Laad relevante merknamen in een lijst op basis van de door de gebruiker gekozen productcategorie.
* Schakel de zichtbaarheid van een bepaald veld in of uit op basis van de waarde die in een ander veld is opgegeven. Geef bijvoorbeeld afzonderlijke velden voor het verzendadres weer als de gebruiker de verzending op een ander adres wil laten uitvoeren.
* Wijs een veld aan als verplicht op basis van de waarde die in een ander veld is opgegeven.
* Opties wijzigen die voor een bepaald veld worden weergegeven op basis van de waarde die in een ander veld is opgegeven.
* Stel de standaardwaarde voor metagegevens in een bepaald veld in op basis van de waarde die in een ander veld is opgegeven.

## Metagegevens met trapsgewijze opmaak configureren in [!DNL Experience Manager]{#configure-cascading-metadata-in-aem}

Overweeg een scenario waarin u trapsgewijze metagegevens wilt weergeven op basis van het geselecteerde type element. Enkele voorbeelden

* Geef voor een video toepasselijke velden weer, zoals indeling, codec, duur, enzovoort.
* Voor een Word- of PDF-document geeft u velden weer, zoals het aantal pagina&#39;s, de auteur, enzovoort.

Geef de copyrightinformatie, ongeacht het gekozen elementtype, weer als een verplicht veld.

1. Ga in de [!DNL Experience Manager] interface naar **[!UICONTROL Gereedschappen]** > **[!UICONTROL Elementen]** > **[!UICONTROL Metagegevensschema&#39;s]**.
1. In the **[!UICONTROL Schema Forms]** page, select a schema form and then click **[!UICONTROL Edit]** from the toolbar to edit the schema.

   ![select_form](assets/select_form.png)

1. (Optioneel) Maak in de Schema-editor voor metagegevens een nieuw veld dat u wilt conditionaliseren. Geef een naam- en eigenschappenpad op het tabblad **[!UICONTROL Instellingen]** .

   Als u een nieuw tabblad wilt maken, klikt u `+` om een tabblad toe te voegen en voegt u vervolgens een metagegevensveld toe.

   ![add_tab](assets/add_tab.png)

1. Voeg een vervolgkeuzeveld toe voor het elementtype. Geef een naam- en eigenschappenpad op het tabblad **[!UICONTROL Instellingen]** . Voeg een optionele beschrijving toe.

   ![asset_type_field](assets/asset_type_field.png)

1. Sleutelwaardeparen zijn de opties die aan een gebruiker van een formulier worden verstrekt. U kunt de sleutel-waardeparen of manueel of van een JSON dossier verstrekken.

   * Als u de waarden handmatig wilt opgeven, selecteert u Handmatig **** toevoegen en klikt u op Keuze **** toevoegen en geeft u de optietekst en -waarde op. Geef bijvoorbeeld de elementtypen Video, PDF, Word en Afbeelding op.

   * Als u de waarden van een JSON-bestand dynamisch wilt ophalen, selecteert u **[!UICONTROL Toevoegen via JSON-pad]** en geeft u het pad van het JSON-bestand op. [!DNL Experience Manager] Hiermee haalt u de sleutelwaardeparen op in real-time wanneer het formulier aan de gebruiker wordt gepresenteerd.
   Beide opties sluiten elkaar uit. U kunt de opties niet importeren uit een JSON-bestand en handmatig bewerken.

   ![add_choice](assets/add_choice.png)

   >[!NOTE]
   >
   >Wanneer u een JSON-bestand toevoegt, worden de sleutel-waardeparen niet weergegeven in de Schema-editor voor metagegevens, maar wel in het gepubliceerde formulier.

   >[!NOTE]
   >
   >Als u keuzen toevoegt en u op het veld Vervolgkeuzelijst klikt, wordt de interface vervormd en werkt het pictogram Verwijderen voor de keuzen niet meer. Klik niet op het vervolgkeuzemenu totdat u de wijzigingen opslaat. Sla het schema op en open het opnieuw om door te gaan met bewerken als dit probleem zich voordoet.

1. (Optioneel) Voeg de andere vereiste velden toe. U kunt bijvoorbeeld de indeling, codec en duur van de video met het elementtype opgeven.

   Op dezelfde manier voegt u afhankelijke velden toe voor andere elementtypen. Voeg bijvoorbeeld het aantal pagina&#39;s en de auteur van velden toe voor documentelementen, zoals PDF- en Word-bestanden.

   ![video_dependent_fields](assets/video_dependent_fields.png)

1. Als u een afhankelijkheid wilt maken tussen het elementtypeveld en andere velden, kiest u het afhankelijke veld en opent u het tabblad **[!UICONTROL Regels]** .

   ![select_dependentfield](assets/select_dependentfield.png)

1. Kies onder **[!UICONTROL Vereiste]** de optie **[!UICONTROL Vereist op basis van de optie Nieuwe regel]** .
1. Klik op Regel **** toevoegen en kies het veld **[!UICONTROL Elementtype]** om een afhankelijkheid te maken. Kies ook de veldwaarde waarop u de afhankelijkheid wilt maken. In this case, choose **[!UICONTROL Video]**. Click **[!UICONTROL Done]** to save the changes.

   ![define_rule](assets/define_rule.png)

   >[!NOTE]
   >
   >U kunt regels gebruiken voor vervolgkeuzelijsten met handmatig vooraf gedefinieerde waarden. Vervolgkeuzemenu&#39;s met geconfigureerd JSON-pad kunnen niet worden gebruikt met regels die vooraf gedefinieerde waarden gebruiken om voorwaarden toe te passen. Als de waarden bij uitvoering vanuit JSON worden geladen, is het niet mogelijk een vooraf gedefinieerde regel toe te passen.

1. Kies onder **[!UICONTROL Zichtbaarheid]** de optie **[!UICONTROL Zichtbaar op basis van de nieuwe regeloptie]** .

1. Klik op Regel **** toevoegen en kies het veld **[!UICONTROL Elementtype]** om een afhankelijkheid te maken. Kies ook de veldwaarde waarop u de afhankelijkheid wilt maken. In this case, choose **[!UICONTROL Video]**. Click **[!UICONTROL Done]** to save the changes.

   ![define_visibilityrule](assets/define_visibilityrule.png)

   >[!NOTE]
   >
   >Als u op een witruimte klikt (of op een andere plaats dan de waarden), worden de waarden opnieuw ingesteld. Als dit gebeurt, selecteert u de waarden opnieuw.

   >[!NOTE]
   >
   >You can apply **[!UICONTROL Requirement]** condition and **[!UICONTROL Visibility]** condition independent of each other.

1. Op dezelfde manier creeer een gebiedsdeel tussen de waarde Video op het gebied van het Type van Activa en andere gebieden, zoals Codec en Duur.
1. Herhaal de stappen om documentelementen (PDF en Word) afhankelijk te maken in het veld [!UICONTROL Elementtype] en velden zoals Aantal  pagina&#39;s en [!UICONTROL Auteur].
1. Click **[!UICONTROL Save]**. Pas het metagegevensschema toe op een map.

1. Navigeer naar de map waarop u het metagegevensschema hebt toegepast en open de pagina met eigenschappen van een element. Afhankelijk van uw keuze in het veld Type element worden relevante trapsgewijze metagegevensvelden weergegeven.

   ![Trapsgewijze metagegevens voor video-elementen](assets/video_asset.png)

   *Afbeelding: Trapsgewijze metagegevens voor een video.*

   ![Trapsgewijze metagegevens voor documentelementen](assets/doc_type_fields.png)

   *Afbeelding: Trapsgewijze metagegevens voor een document.*
