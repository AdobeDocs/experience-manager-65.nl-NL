---
title: 'Stijl uw adaptieve formulier '
seo-title: 'Stijl uw adaptieve formulier '
description: 'Leer hoe u een aangepast thema maakt, afzonderlijke componenten opmaakt en weblettertypen in een thema gebruikt '
seo-description: 'Leer hoe u een aangepast thema maakt, afzonderlijke componenten opmaakt en weblettertypen in een thema gebruikt '
page-status-flag: de-activated
uuid: ffb2cc22-baaf-4525-a2e3-29f39271c670
topic-tags: introduction
discoiquuid: 655303a4-99bb-4ba3-9d50-a178f5edcf85
feature: Adaptive Forms
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '1949'
ht-degree: 5%

---


# Stijl uw adaptieve formulier {#do-not-publish-style-your-adaptive-form}

Leer hoe u een aangepast thema maakt, afzonderlijke componenten opmaakt en weblettertypen in een thema gebruikt

![](do-not-localize/08-style_your_adaptiveformmain.png)

Deze zelfstudie is een stap in de serie [Uw eerste adaptieve vorm maken](https://helpx.adobe.com/experience-manager/6-3/forms/using/create-your-first-adaptive-form.html). U wordt aangeraden de reeks in chronologische volgorde te volgen om het volledige gebruik van de zelfstudie te begrijpen, uit te voeren en aan te tonen.

## Informatie over de zelfstudie {#about-the-tutorial}

U kunt thema&#39;s gebruiken om een adaptief formulier een unieke vormgeving en stijl te geven. U kunt thema&#39;s uit de doos toepassen die van de adaptieve redacteur van vormen worden voorzien of douanethema&#39;s van uw tot stand brengen. AEM [!DNL Forms] verstrekt [themaredacteur](https://helpx.adobe.com/experience-manager/6-3/forms/using/themes.html) om douanethema&#39;s tot stand te brengen. Met één thema kunt u hetzelfde adaptieve formulier weergeven dat u op mobiele apparaten, tablets of desktops hebt geopend. Eerdere kennis van CSS of LESS is niet vereist voor het gebruik van de themaeditor, maar is wel gewenst.

Aan het einde van de zelfstudie leert u:

* Een thema uit het vak toepassen op een adaptief formulier
* Een thema maken voor een adaptief formulier met de themaeditor
* Afzonderlijke componenten opmaken
* Bonussectie: Weblettertypen gebruiken in een aangepast thema

Het formulier ziet er ongeveer als volgt uit nadat u de zelfstudie hebt voltooid:

![Formulier met een aangepast thema](assets/styled-adaptive-form.png)

## Voordat u begint {#before-you-start}

Download de koptekst- en logo-afbeeldingen hieronder op uw lokale computer. De koptekst van het aangepaste formulier `shipping-address-add-update-form` gebruikt de koptekst- en logoafbeeldingen. De koptekstafbeelding wordt rechts van de koptekst weergegeven.

[Bestand ophalen](assets/header-style.png)

[Bestand ophalen](assets/logo-1.png)

## Stap 1: Een thema toepassen op uw aangepaste formulier {#step-apply-a-theme-to-your-adaptive-form}

De adaptieve vormenredacteur verstrekt veelvoudige uit-van-de-doos thema&#39;s. Als u geen aangepaste stijl wilt gebruiken voor het aangepaste formulier, kunt u ook uw aangepaste formulieren publiceren met een thema dat buiten de verpakking valt. Thema&#39;s zijn onafhankelijk van adaptieve vormen. U kunt hetzelfde thema toepassen op meerdere adaptieve formulieren. Een thema toepassen op een adaptief formulier:

1. Open het aangepaste formulier voor bewerking.

   [http://localhost:4502/editor.html/content/forms/af/shipping-address-add-update-form.html](http://localhost:4502/editor.html/content/forms/af/shipping-address-add-update-form.html)

1. Open eigenschappen van **[!UICONTROL Adaptive Form container]**. Navigeer in de eigenschappenbrowser naar **[!UICONTROL Basic]** > **[!UICONTROL Adaptive Form Theme]**. In het veld **[!UICONTROL Adaptive Form Theme]** worden alle kant-en-klare en aangepaste thema&#39;s weergegeven. Standaard wordt het thema Canvas toegepast.
1. Selecteer een thema in het veld **[!UICONTROL Adaptive Form Theme]**. Bijvoorbeeld **Beoordelingsthema**. Tik ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png) om het geselecteerde thema toe te passen.

   ![Aangepast formulier met het standaardthema](assets/default-adaptive-form.png)

   **Afbeelding:** *Adaptief formulier met standaardthema*

   ![Aangepast formulier met het thema Beoordeling](assets/adaptive-form-with-survey-theme.png)

   **Afbeelding:** *Adaptief formulier met het thema Beoordeling*

## Stap 2: Het aangepaste formulier {#step-update-your-adaptive-form} bijwerken

Voor het hierboven weergegeven ontwerp zijn wijzigingen vereist in de plaatsaanduidingstekst en het logo van het bestaande adaptieve formulier. Voer de volgende stappen uit om de vereiste wijzigingen aan te brengen:

1. Wijzig het bestaande logo en de tekst van de koptekst. Het logo verwijderen:

   1. Open het formulier in de formuliereditor.

      [http://localhost:4502/editor.html/content/forms/af/shipping-address-add-update-form.html](http://localhost:4502/editor.html/content/forms/af/shipping-address-add-update-form.html)

   1. Tik op de afbeelding met het logo in de [!UICONTROL header]-component en tik ![cmppr](assets/cmppr.png) **[!UICONTROL properties]**. Tik in de eigenschap [!UICONTROL image] op X om de bestaande logoafbeelding te verwijderen.
   1. Tik **[!UICONTROL upload]**, selecteer het logo.png en tik ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png) om de wijzigingen op te slaan. De afbeelding is gedownload in de sectie [Voordat u ](/help/forms/using/style-your-adaptive-form.md#before-you-start) start.
   1. Tik op koptekst, `We.Retail` en tik ![aem_6_3_edit](assets/aem_6_3_edit.png) **[!UICONTROL edit]**. Wijzig de koptekst in `we retail`. Pas vette opmaak alleen toe op `we`in `we retail`.

      ![we-retail-logo-text](assets/we-retail-logo-text.png)

1. Titel verwijderen en plaatsaanduidingstekst toevoegen:

   1. Tik op het veld Klantnummer en tik op ![cmpr](assets/cmppr.png) eigenschappen.
   1. Kopieer de inhoud van het veld **[!UICONTROL Title]** naar het veld **[!UICONTROL Placeholder Text]**.
   1. Verwijder de inhoud van het veld **[!UICONTROL Title]** en tik ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).
   1. Herhaal de vorige drie stappen voor alle tekstvakken, het numerieke vak en het e-mailveld in het formulier.

      ![aangepast-vorm](assets/updated-adaptive-form.png)

## Stap 3: Een aangepast thema maken voor uw aangepaste formulier {#step-create-a-custom-theme-for-your-adaptive-form}

U kunt [themaeditor](/help/forms/using/themes.md) gebruiken om aangepaste thema&#39;s te maken. De themaredacteur is een almachtige redacteur WYSIWYG. Het is een visuele methode om CSS op diverse componenten van een adaptieve vorm toe te passen. Het biedt fijnere besturingselementen voor stijlcomponenten en deelvensters van een adaptieve vorm.

Een thema is een afzonderlijke entiteit, zoals adaptieve formulieren. Deze bevat stijlen (CSS) voor de componenten en deelvensters van een adaptief formulier. Stijlen omvatten CSS-eigenschappen zoals achtergrondkleuren, statuskleuren, transparantie, uitlijning en grootte. Wanneer u een thema toepast, wordt de opgegeven stijl toegepast op de corresponderende componenten van een adaptief formulier.

In deze zelfstudie maakt u een stijl van de kop- en voettekst, tekst en numerieke componenten, de bijlage en knoppen. Laten we beginnen met het maken van een thema:

### Een thema {#create-a-theme} maken

1. Meld u aan bij de AEM auteur en navigeer naar **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Themes]**. De standaard-URL is [http://localhost:4502/aem/forms.html/content/dam/formsanddocuments-themes](http://localhost:4502/aem/forms.html/content/dam/formsanddocuments-themes).
1. Tik **[!UICONTROL Create]** en selecteer **[!UICONTROL Theme]**. De pagina [!UICONTROL Create Theme] met de velden die nodig zijn om een thema te maken, wordt weergegeven. De velden **[!UICONTROL Title]** en **[!UICONTROL Name]** zijn verplicht:

   * **Titel:** Geef een titel van het thema op. Bijvoorbeeld **Globaal thema.** Met de titel kunt u het thema herkennen aan de lijst met thema&#39;s.
   * **Naam:** geef de naam van het thema op. Bijvoorbeeld **Global-Theme.** Er wordt een knooppunt met de opgegeven naam gemaakt in de repository. Wanneer u een titel begint te typen, wordt automatisch een waarde voor het naamveld gegenereerd. U kunt de voorgestelde waarde wijzigen. Het naamveld mag alleen alfanumerieke tekens, afbreekstreepjes en onderstrepingstekens bevatten. Alle ongeldige invoer wordt vervangen door een afbreekstreepje.

1. Tik op **[!UICONTROL Create]**. Er wordt een thema gemaakt en er verschijnt een dialoogvenster waarin u het formulier kunt openen om het te bewerken. Tik **[!UICONTROL Open]** om het nieuwe thema op een nieuw tabblad te openen. Het thema wordt geopend in de themaeditor. Voor het opmaken gebruikt de themaeditor een adaptief formulier dat buiten de box wordt geleverd met AEM [!DNL Forms].

   Voor informatie over het gebruiken van thema redacteur UI, zie [Ongeveer de themaredacteur](/help/forms/using/themes.md#aboutthethemeeditor).

1. Tik **[!UICONTROL Theme Options]** ![theme-options](assets/theme-options.png) > **[!UICONTROL Configure]**. Selecteer in het veld **[!UICONTROL Preview Form]** het adaptieve formulier **Shipping-address-add-update-form**, tik ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png) en tik **[!UICONTROL Save]**. De themaeditor is nu geconfigureerd voor het gebruik van uw eigen adaptieve formulier in plaats van het standaard adaptieve formulier. Tik op **[!UICONTROL Cancel]** om terug te keren naar de themaeditor.

   ![aangepast thema](assets/custom-theme.png)

   **Afbeelding:** *Thema-editor met het adaptieve formulier voor het verzendadres-add-update*

   ![thema maken](assets/create-a-theme.png)

   **Afbeelding:** *Adaptief formulier met standaardformulier*

### Stijlkop- en voettekst {#style-header-and-footer}

Koptekst en voettekst geven een consistent en duidelijk beeld van een adaptief formulier. Over het algemeen bevat de koptekst het logo en de naam van de organisatie, bevat de voettekst copyrightinformatie en deze blijven in meerdere vormen van een organisatie identiek. De kop- en voettekst van het adaptieve formulier voor het verzendadres-add-update-formulier opmaken:

1. Navigeer in het deelvenster Kiezers naar de optie **[!UICONTROL Header]** > **[!UICONTROL Text]**. Het deelvenster Kiezers bevindt zich links van de themaeditor. Tik ![in-/uitschakelen van zijpaneel](assets/toggle-side-panel.png) Zijpaneel in-/uitschakelen als het deelvenster niet zichtbaar is.

1. Stel de volgende eigenschappen in de accordeon **[!UICONTROL Text]** in en tik ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

   | Eigenschap | Waarde |
   |---|---|
   | Lettertypefamilie | Arial |
   | Lettertypekleur | FFFFFF |
   | Fontgrootte | 54 px |

1. Tik op de [!UICONTROL header]-widget en tik **[!UICONTROL Header]**. De opties voor het opmaken van de koptekstwidget worden links weergegeven. Breid **[!UICONTROL Dimensions & Position]** accordeon uit, plaats **[!UICONTROL Height]** aan `120px`, en tik ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).
1. Breid **[!UICONTROL Background]** accordeon van kopbalwidget uit, plaats **[!UICONTROL Background Color]** aan `F6921E.`

   Houd de cursor boven **[!UICONTROL Image & Gradient]** > **[!UICONTROL + Add]** en tik **[!UICONTROL Image]**. Stel de volgende eigenschappen in en tik op ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

   | Eigenschap | Waarde |
   |---|---|
   | afbeelding | Upload header-style.png. De afbeelding is gedownload in de sectie [Voordat u ](/help/forms/using/style-your-adaptive-form.md#before-you-start) start. |
   | Positie | Rechts onder |
   | Naast elkaar | Niet herhalen |

1. Tik in de themaeditor op het logo in de koptekst en tik op **[!UICONTROL Header Logo]**. Vouw de accordeon Dimension en positie uit, stel de volgende eigenschappen in en tik ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

   <table> 
    <tbody> 
     <tr> 
      <td><b>Marge</b></td> 
      <td><b>Waarde</b></td> 
     </tr> 
     <tr> 
      <td>Marge</td> 
      <td> 
       <ul> 
        <li>Boven: 1.5 rem</li> 
        <li>Onder: -35 px</li> 
        <li>Links: 1rem<strong><br /> </strong></li> 
       </ul> <p><strong>Tip:</strong> Tik op het  <img src="assets/link.png"> koppelingspictogram om voor elk veld een andere waarde in te stellen.<br /> </p> </td> 
     </tr> 
     <tr> 
      <td>Hoogte</td> 
      <td>4.75 rem</td> 
     </tr> 
    </tbody> 
   </table>

1. Tik op de voettekstwidget en tik **[!UICONTROL Footer]**. Breid **[!UICONTROL Background]** accordeon uit, plaats **[!UICONTROL Background Color]** aan `F6921E`, en tik ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

### Maak de component voor gegevensvastlegging op en pas een achtergrond toe op het adaptieve formulier {#style-the-data-capture-component-and-apply-a-background-to-the-adaptive-form}

U kunt meerdere componenten in een adaptief formulier gebruiken om gegevens vast te leggen. Bijvoorbeeld tekstvak en numeriek vak. U kunt identieke stijl aan alle gegevens verstrekken vangt componenten of afzonderlijke stijl voor elke component. In deze zelfstudie wordt een identieke stijl toegepast op numerieke vakken (Customer ID, ZIP Code) en tekstvakken (Customer ID, Name, Shipping Address, State, Email). De componenten voor gegevensvastlegging opmaken:

1. Tik op het veld **[!UICONTROL Customer ID]** en tik op de optie **[!UICONTROL Field Widget]**. Stel de volgende eigenschappen in en tik op ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

   <table> 
    <tbody> 
     <tr> 
      <td><b>Accordeon</b></td> 
      <td><b>Eigenschap</b></td> 
      <td><b>Waarde</b></td> 
     </tr> 
     <tr> 
      <td>Rand</td> 
      <td>Randkleur</td> 
      <td>A7A9AC</td> 
     </tr> 
     <tr> 
      <td>Rand</td> 
      <td>Straal rand </td> 
      <td> 
       <ul> 
        <li>Boven: 7px<br /> </li> 
        <li>Rechts: 7px<br /> </li> 
        <li>Onder: 7px<br /> </li> 
        <li>Links: 7px<br /> </li> 
       </ul> </td> 
     </tr> 
     <tr> 
      <td>Tekst</td> 
      <td>Lettertypefamilie</td> 
      <td>Arial</td> 
     </tr> 
     <tr> 
      <td>Tekst</td> 
      <td>Lettertypekleur</td> 
      <td>939598<br /> </td> 
     </tr> 
     <tr> 
      <td>Tekst</td> 
      <td>Fontgrootte</td> 
      <td>18 px</td> 
     </tr> 
     <tr> 
      <td>Dimension en positie</td> 
      <td>Breedte</td> 
      <td>60%</td> 
     </tr> 
     <tr> 
      <td>Dimension en positie</td> 
      <td>Marge</td> 
      <td> 
       <ul> 
        <li>Links: 10rem</li> 
       </ul> </td> 
     </tr> 
    </tbody> 
    </table>

1. Tik op het lege gebied boven het veld **[!UICONTROL Customer ID]** en tik **[!UICONTROL Responsive Panel Container]**. Stel **[!UICONTROL Background]** > **[!UICONTROL Background Color]** in op F1F2F2. Tik ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

   ![](do-not-localize/responsive-panel-container.png)

### De knoppen opmaken {#style-the-buttons}

U kunt een aangepast thema gebruiken om een identieke stijl toe te passen op alle knoppen van het adaptieve formulier en [inline styling](/help/forms/using/inline-style-adaptive-forms.md) om een stijl toe te passen op een specifieke knop. De knoppen opmaken:

1. Tik op de knop **[!UICONTROL Submit]** en tik op de optie **[!UICONTROL Button]**. Stel de volgende eigenschappen in en tik op ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

   <table> 
    <tbody> 
     <tr> 
      <td><b>Accordeon</b></td> 
      <td><b>Eigenschap</b></td> 
      <td><b>Waarde</b></td> 
     </tr> 
     <tr> 
      <td>Achtergrond</td> 
      <td>Achtergrondkleur</td> 
      <td>F6921E</td> 
     </tr> 
     <tr> 
      <td>Rand<br /> </td> 
      <td>Randkleur</td> 
      <td>F6921E</td> 
     </tr> 
     <tr> 
      <td>Rand</td> 
      <td>Straal rand </td> 
      <td> 
       <ul> 
        <li>Boven: 7px<br /> </li> 
        <li>Rechts: 7px<br /> </li> 
        <li>Onder: 7px<br /> </li> 
        <li>Links: 7 px</li> 
       </ul> </td> 
     </tr> 
     <tr> 
      <td>Tekst<br /> </td> 
      <td>Lettertypefamilie</td> 
      <td>Arial</td> 
     </tr> 
     <tr> 
      <td>Tekst</td> 
      <td>Lettertypekleur</td> 
      <td>FFFFFF</td> 
     </tr> 
     <tr> 
      <td>Tekst</td> 
      <td>Fontgrootte</td> 
      <td>18 px</td> 
     </tr> 
    </tbody> 
   </table>

1. [Pas het aangepaste thema](/help/forms/using/style-your-adaptive-form.md#step-apply-a-theme-to-your-adaptive-form) Global Theme toe op het aangepaste formulier. Als de stijl niet op het adaptieve formulier wordt weerspiegeld, maakt u de cache van de browser leeg en probeert u het opnieuw.

   ![style-data-capture-components](assets/style-data-capture-components.png)

## Stap 4: Afzonderlijke componenten opmaken {#step-style-individual-components}

Sommige stijlen zijn alleen van toepassing op een bepaalde component. Dergelijke componenten worden opgemaakt in de editor voor adaptieve formulieren.

1. Open het aangepaste formulier voor bewerking. [http://localhost:4502/editor.html/content/forms/af/shipping-address-add-update-form.html](http://localhost:4502/editor.html/content/forms/af/change-billing-shipping-address.html)
1. Selecteer op de bovenste balk de optie **[!UICONTROL Style]**.

   ![style-option](assets/style-option.png)

1. Tik op de knop **[!UICONTROL Attach]** en tik op het pictogram ![aem_6_3_edit](assets/aem_6_3_edit.png). Stel de volgende eigenschappen in de accordeon **[!UICONTROL Dimensions and Position]** in:

   | Eigenschap | Waarde |
   |---|---|
   | Zwevend | Links |
   | Breedte | 10% |

1. Tik op de optie **[!UICONTROL Government approved address proof]** en tik op het pictogram ![aem_6_3_edit](assets/aem_6_3_edit.png). Stel de volgende eigenschappen in:

   <table> 
    <tbody> 
     <tr> 
      <td><b>Accordeon</b></td> 
      <td><b>Eigenschap</b></td> 
      <td><b>Waarde</b></td> 
     </tr> 
     <tr> 
      <td>Dimension en positie</td> 
      <td>Zwevend</td> 
      <td>Links</td> 
     </tr> 
     <tr> 
      <td>Dimension en positie</td> 
      <td>Breedte</td> 
      <td>73%</td> 
     </tr> 
     <tr> 
      <td>Dimension en positie</td> 
      <td>Opvulling</td> 
      <td> 
       <ul> 
        <li>Links: 10 px</li> 
       </ul> </td> 
     </tr> 
     <tr> 
      <td>Dimension en positie</td> 
      <td>Hoogte</td> 
      <td>40 px</td> 
     </tr> 
     <tr> 
      <td>Dimension en positie<br /> </td> 
      <td>Marge</td> 
      <td><br /> 
       <ul> 
        <li>Rechts: 2rem</li> 
        <li>Links: 10rem </li> 
       </ul> </td> 
     </tr> 
     <tr> 
      <td>Achtergrond</td> 
      <td>Achtergrondkleur</td> 
      <td>FFFFFF</td> 
     </tr> 
     <tr> 
      <td>Rand</td> 
      <td>Randbreedte</td> 
      <td>1 px</td> 
     </tr> 
     <tr> 
      <td>Rand</td> 
      <td>Randstijl</td> 
      <td>Een ononderbroken lijn</td> 
     </tr> 
     <tr> 
      <td>Rand</td> 
      <td>Randkleur</td> 
      <td>A7A9AC</td> 
     </tr> 
     <tr> 
      <td>Rand</td> 
      <td>Straal rand</td> 
      <td>7 px</td> 
     </tr> 
     <tr> 
      <td>Tekst</td> 
      <td>Lettertypefamilie</td> 
      <td>Arial</td> 
     </tr> 
     <tr> 
      <td>Tekst</td> 
      <td>Lettertypekleur</td> 
      <td>BCBEC0</td> 
     </tr> 
     <tr> 
      <td>Tekst</td> 
      <td>Fontgrootte</td> 
      <td>18 px</td> 
     </tr> 
     <tr> 
      <td>Tekst</td> 
      <td>Lijnhoogte</td> 
      <td>2</td> 
     </tr> 
     </tr> 
    </tbody> 
   </table>

1. Tik op de knop **[!UICONTROL Submit]** en tik op het pictogram ![aem_6_3_edit](assets/aem_6_3_edit.png). Stel de volgende eigenschappen in:

   <table> 
    <tbody> 
     <tr> 
      <td><b>Accordeon</b></td> 
      <td><b>Eigenschap</b></td> 
      <td><b>Waarde</b></td> 
     </tr> 
     <tr> 
      <td>Dimension en positie</td> 
      <td>Zwevend</td> 
      <td>Rechts</td> 
     </tr> 
     <tr> 
      <td>Dimension en positie</td> 
      <td>Marge</td> 
      <td> 
       <ul> 
        <li>Boven: 5rem</li> 
        <li>Rechts: 14rem</li> 
        <li>Onder: 20 px</li> 
        <li>Links: 20px<br /> </li> 
       </ul> </td> 
     </tr> 
     <tr> 
      <td>Achtergrond</td> 
      <td>Achtergrondkleur</td> 
      <td>F6921E</td> 
     </tr> 
     <tr> 
      <td>Rand</td> 
      <td>Randkleur</td> 
      <td>F6921E</td> 
     </tr> 
    </tbody> 
   </table>

   ![styled-adaptive-form-1](assets/styled-adaptive-form-1.png)

## Stap 5: Bonussectie: Weblettertypen gebruiken in een aangepast thema {#step-bonus-section-using-web-fonts-in-a-custom-theme}

U kunt verschillende lettertypen gebruiken om een adaptief formulier te ontwerpen. Op alle apparaten waarop het adaptieve formulier wordt weergegeven, worden mogelijk niet de fonts gebruikt om het adaptieve formulier te ontwerpen. U kunt een service voor weblettertypen gebruiken om de vereiste lettertypen aan het doelapparaat te leveren.

[!DNL Adobe Fonts] is een service voor weblettertypen. U kunt de service configureren en gebruiken met adaptieve formulieren. [!DNL Adobe Fonts] in een adaptieve vorm gebruiken:

>[!NOTE]
>
>![typekit-to-adobe-](assets/typekit-to-adobe-fonts.png) [!DNL Typekit] fontsis heet nu Adobe Fonts en wordt meegeleverd bij Creative Cloud- en andere abonnementen. [Meer](https://fonts.adobe.com/) informatie.

1. Maak een [Adobe Fonts](https://typekit.com/)-account, maak een kit, voeg Myriad Pro-lettertype toe aan de kit, publiceer de kit en verkrijg de kit-id. [!DNL Adobe Fonts] (weblettertypen) moet in een adaptieve vorm worden gebruikt.
1. Navigeer op de AEM [!DNL Forms]-server naar ![adobeexperienceManager](assets/adobeexperiencemanager.png) **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Tools]** ![hammer](assets/hammer.png) > **[!UICONTROL Adobe Fonts]**. Open nu een configuratiemap. Als er al een configuratie beschikbaar is, klikt u op de knop **[!UICONTROL Create]** om een nieuwe instantie te maken.

   Voor de Create dialoog van de Configuratie, specificeer **Titel** voor de configuratie, en klik **[!UICONTROL Create]**. U wordt opnieuw gericht aan de configuratiepagina. Geef in het dialoogvenster [!UICONTROL Edit Component] dat wordt weergegeven uw **kit-id** op en klik op **[!UICONTROL OK]**.

1. Vorm uw thema om de [!DNL Adobe Fonts] configuratie te gebruiken. Voor de auteurinstantie, open **[!UICONTROL Global Theme]** in de themaredacteur. Navigeer in de themaeditor naar **[!UICONTROL Theme Options]** ![theme-options](assets/theme-options.png) > **[!UICONTROL Configure]**. Selecteer de kit in het veld **[!UICONTROL Adobe Fonts Configuration]** en klik op **[!UICONTROL Save]**.

   De lettertypen die worden toegevoegd aan de **[!UICONTROL Adobe Fonts]** zijn beschikbaar voor selectie in de **[!UICONTROL Text]**-accordeon van alle componenten.

