---
title: Stijl uw adaptieve formulier
seo-title: Style your adaptive form
description: Leer hoe u een aangepast thema maakt, afzonderlijke componenten opmaakt en weblettertypen in een thema gebruikt
seo-description: Learn to create a custom theme, style individual components, and use web fonts in a theme
page-status-flag: de-activated
uuid: ffb2cc22-baaf-4525-a2e3-29f39271c670
topic-tags: introduction
discoiquuid: 655303a4-99bb-4ba3-9d50-a178f5edcf85
feature: Adaptive Forms
exl-id: 7742c3ca-1755-44c5-b70f-61309f09d1b8
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1927'
ht-degree: 5%

---

# Stijl uw adaptieve formulier {#do-not-publish-style-your-adaptive-form}

Leer hoe u een aangepast thema maakt, afzonderlijke componenten opmaakt en weblettertypen in een thema gebruikt

![](do-not-localize/08-style_your_adaptiveformmain.png)

Deze zelfstudie is een stap in de [Uw eerste adaptieve formulier maken](https://helpx.adobe.com/experience-manager/6-3/forms/using/create-your-first-adaptive-form.html) reeks. U wordt aangeraden de reeks in chronologische volgorde te volgen om het volledige gebruik van de zelfstudie te begrijpen, uit te voeren en aan te tonen.

## Over de zelfstudie  {#about-the-tutorial}

U kunt thema&#39;s gebruiken om een adaptief formulier een unieke vormgeving en stijl te geven. U kunt thema&#39;s uit de doos toepassen die van de adaptieve redacteur van vormen worden voorzien of douanethema&#39;s van uw tot stand brengen. AEM [!DNL Forms] een [themaeditor](https://helpx.adobe.com/experience-manager/6-3/forms/using/themes.html) om aangepaste thema&#39;s te maken. Met één thema kunt u hetzelfde adaptieve formulier weergeven dat u op mobiele apparaten, tablets of desktops hebt geopend. Eerdere kennis van CSS of LESS is niet vereist voor het gebruik van de themaeditor, maar is wel gewenst.

Aan het einde van de zelfstudie leert u:

* Een thema uit het vak toepassen op een adaptief formulier
* Een thema maken voor een adaptief formulier met de themaeditor
* Afzonderlijke componenten opmaken
* Bonussectie: Weblettertypen gebruiken in een aangepast thema

Het formulier ziet er ongeveer als volgt uit nadat u de zelfstudie hebt voltooid:

![Formulier met een aangepast thema](assets/styled-adaptive-form.png)

## Voordat u begint {#before-you-start}

Download de koptekst- en logo-afbeeldingen hieronder op uw lokale computer. De koptekst van de `shipping-address-add-update-form` Het adaptieve formulier gebruikt de koptekst- en logo-afbeeldingen. De koptekstafbeelding wordt rechts van de koptekst weergegeven.

[Bestand ophalen](assets/header-style.png)

[Bestand ophalen](assets/logo-1.png)

## Stap 1: Een thema toepassen op het aangepaste formulier {#step-apply-a-theme-to-your-adaptive-form}

De adaptieve vormenredacteur verstrekt veelvoudige uit-van-de-doos thema&#39;s. Als u geen aangepaste stijl wilt gebruiken voor het aangepaste formulier, kunt u ook uw aangepaste formulieren publiceren met een thema dat buiten de verpakking valt. Thema&#39;s zijn onafhankelijk van adaptieve vormen. U kunt hetzelfde thema toepassen op meerdere adaptieve formulieren. Een thema toepassen op een adaptief formulier:

1. Open het aangepaste formulier voor bewerking.

   [http://localhost:4502/editor.html/content/forms/af/shipping-address-add-update-form.html](http://localhost:4502/editor.html/content/forms/af/shipping-address-add-update-form.html)

1. Open eigenschappen van **[!UICONTROL Adaptive Form container]**. Navigeer in de eigenschappenbrowser naar **[!UICONTROL Basic]** > **[!UICONTROL Adaptive Form Theme]**. De **[!UICONTROL Adaptive Form Theme]** worden alle kant-en-klare thema&#39;s en aangepaste thema&#39;s weergegeven. Standaard wordt het thema Canvas toegepast.
1. Selecteer een thema in het menu **[!UICONTROL Adaptive Form Theme]** veld. Bijvoorbeeld: **Onderzoeken**. Tikken ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png) om het geselecteerde thema toe te passen.

   ![Aangepast formulier met het standaardthema](assets/default-adaptive-form.png)

   **Afbeelding:** *Aangepast formulier met het standaardthema*

   ![Aangepast formulier met het thema Beoordeling](assets/adaptive-form-with-survey-theme.png)

   **Afbeelding:** *Aangepast formulier met het thema Beoordeling*

## Stap 2: Het aangepaste formulier bijwerken {#step-update-your-adaptive-form}

Voor het hierboven weergegeven ontwerp zijn wijzigingen vereist in de plaatsaanduidingstekst en het logo van het bestaande adaptieve formulier. Voer de volgende stappen uit om de vereiste wijzigingen aan te brengen:

1. Wijzig het bestaande logo en de tekst van de koptekst. Het logo verwijderen:

   1. Open het formulier in de formuliereditor.

      [http://localhost:4502/editor.html/content/forms/af/shipping-address-add-update-form.html](http://localhost:4502/editor.html/content/forms/af/shipping-address-add-update-form.html)

   1. Tik op de afbeelding met het logo in het dialoogvenster [!UICONTROL header] component en tik ![cmppr](assets/cmppr.png) **[!UICONTROL properties]**. In de [!UICONTROL image] tikt u op X om de bestaande logoafbeelding te verwijderen.
   1. Tikken **[!UICONTROL upload]** selecteert u het bestand logo.png en tikt u op ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png) om de wijzigingen op te slaan. De afbeelding is gedownload in het dialoogvenster [Voordat u begint](/help/forms/using/style-your-adaptive-form.md#before-you-start) sectie.
   1. Tikkoptekst, `We.Retail`en tikken ![aem_6_3_edit](assets/aem_6_3_edit.png) **[!UICONTROL edit]**. Koptekst wijzigen in `we retail`. Alleen vette opmaak toepassen op `we`in `we retail`.

      ![we-retail-logo-text](assets/we-retail-logo-text.png)

1. Titel verwijderen en plaatsaanduidingstekst toevoegen:

   1. Tik op het veld Customer ID en tik op ![cmppr](assets/cmppr.png) eigenschappen.
   1. Kopieer de inhoud van de **[!UICONTROL Title]** aan de **[!UICONTROL Placeholder Text]** veld.
   1. De inhoud van het dialoogvenster **[!UICONTROL Title]** veld en tik ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).
   1. Herhaal de vorige drie stappen voor alle tekstvakken, het numerieke vak en het e-mailveld in het formulier.

      ![aangepast-vorm](assets/updated-adaptive-form.png)

## Stap 3: Een aangepast thema maken voor uw aangepaste formulier {#step-create-a-custom-theme-for-your-adaptive-form}

U kunt [themaeditor](/help/forms/using/themes.md) om aangepaste thema&#39;s te maken. De themaredacteur is een almachtige redacteur WYSIWYG. Het is een visuele methode om CSS op diverse componenten van een adaptieve vorm toe te passen. Het biedt fijnere besturingselementen voor stijlcomponenten en deelvensters van een adaptieve vorm.

Een thema is een afzonderlijke entiteit, zoals adaptieve formulieren. Deze bevat stijlen (CSS) voor de componenten en deelvensters van een adaptief formulier. Stijlen omvatten CSS-eigenschappen zoals achtergrondkleuren, statuskleuren, transparantie, uitlijning en grootte. Wanneer u een thema toepast, wordt de opgegeven stijl toegepast op de corresponderende componenten van een adaptief formulier.

In deze zelfstudie maakt u een stijl van de kop- en voettekst, tekst en numerieke componenten, de bijlage en knoppen. Laten we beginnen met het maken van een thema:

### Een thema maken {#create-a-theme}

1. Meld u aan bij de AEM auteur en navigeer naar **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Themes]**. De standaard-URL is [http://localhost:4502/aem/forms.html/content/dam/formsanddocuments-themes](http://localhost:4502/aem/forms.html/content/dam/formsanddocuments-themes).
1. Tikken **[!UICONTROL Create]** en selecteert u **[!UICONTROL Theme]**. De [!UICONTROL Create Theme] Er verschijnt een pagina met de velden die u nodig hebt om een thema te maken. De **[!UICONTROL Title]** en **[!UICONTROL Name]** velden zijn verplicht:

   * **Titel:** Geef een titel van het thema op. Bijvoorbeeld: **Globaal thema.** Met de titel kunt u het thema herkennen aan de lijst met thema&#39;s.
   * **Naam:** Geef de naam van het thema op. Bijvoorbeeld: **Globaal thema.** Er wordt een knooppunt met de opgegeven naam gemaakt in de repository. Wanneer u een titel begint te typen, wordt automatisch een waarde voor het naamveld gegenereerd. U kunt de voorgestelde waarde wijzigen. Het naamveld mag alleen alfanumerieke tekens, afbreekstreepjes en onderstrepingstekens bevatten. Alle ongeldige invoer wordt vervangen door een afbreekstreepje.

1. Tik op **[!UICONTROL Create]**. Er wordt een thema gemaakt en er verschijnt een dialoogvenster waarin u het formulier kunt openen om het te bewerken. Tikken **[!UICONTROL Open]** om het nieuwe thema op een nieuw tabblad te openen. Het thema wordt geopend in de themaeditor. Voor het opmaken gebruikt de themaeditor een adaptief formulier dat niet in de doos is meegeleverd en dat wordt geleverd met AEM [!DNL Forms].

   Voor informatie over het gebruiken van thema redacteur UI, zie [Informatie over de themaeditor](/help/forms/using/themes.md#aboutthethemeeditor).

1. Tikken **[!UICONTROL Theme Options]** ![thema-opties](assets/theme-options.png) > **[!UICONTROL Configure]**. In de **[!UICONTROL Preview Form]** veld selecteert u de **verzendadres-add-update-form** adaptief formulier, tikken ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png), tikken **[!UICONTROL Save]**. De themaeditor is nu geconfigureerd voor het gebruik van uw eigen adaptieve formulier in plaats van het standaard adaptieve formulier. Tikken **[!UICONTROL Cancel]** om terug te keren naar de themaeditor.

   ![aangepast thema](assets/custom-theme.png)

   **Afbeelding:** *Thema-editor met het adaptieve formulier voor het verzendadres-add-update*

   ![thema maken](assets/create-a-theme.png)

   **Afbeelding:** *Adaptief formulier met het standaardformulier*

### Stijlkop- en voettekst {#style-header-and-footer}

Koptekst en voettekst geven een consistent en duidelijk beeld van een adaptief formulier. Over het algemeen bevat de koptekst het logo en de naam van de organisatie, bevat de voettekst copyrightinformatie en deze blijven in meerdere vormen van een organisatie identiek. De kop- en voettekst van het adaptieve formulier voor het verzendadres-add-update-formulier opmaken:

1. Navigeren door de **[!UICONTROL Header]** > **[!UICONTROL Text]** in het deelvenster Kiezers. Het deelvenster Kiezers bevindt zich links van de themaeditor. Tik op ![schakelen tussen zijpaneel](assets/toggle-side-panel.png) Zijpaneel in-/uitschakelen.

1. Stel de volgende eigenschappen in in het dialoogvenster **[!UICONTROL Text]** accordeon en tik ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

   | Eigenschap | Waarde |
   |---|---|
   | Lettertypefamilie | Arial |
   | Lettertypekleur | FFFFFF |
   | Fontgrootte | 54px |

1. Tik op de knop [!UICONTROL header] widget en tik **[!UICONTROL Header]**. De opties voor het opmaken van de koptekstwidget worden links weergegeven. Breid uit **[!UICONTROL Dimensions & Position]** accordeon instellen **[!UICONTROL Height]** tot `120px`en tikken ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).
1. Breid uit **[!UICONTROL Background]** stelt de accordeon van de koptekstwidget in **[!UICONTROL Background Color]** tot `F6921E.`

   Overslaan **[!UICONTROL Image & Gradient]** > **[!UICONTROL + Add]**, tikken **[!UICONTROL Image]**. Stel de volgende eigenschappen in en tik op ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

   | Eigenschap | Waarde |
   |---|---|
   | afbeelding | Upload header-style.png. De afbeelding is gedownload in het dialoogvenster [Voordat u begint](/help/forms/using/style-your-adaptive-form.md#before-you-start) sectie. |
   | Positie | Rechts onder |
   | Naast elkaar | Niet herhalen |

1. Tik in de themaeditor op het logo in de koptekst en tik op **[!UICONTROL Header Logo]**. Breid de Dimension en Positie accordeon uit, plaats de volgende eigenschappen en tik ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

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
       </ul> <p><strong>Tip:</strong> Tik op de knop <img src="assets/link.png"> koppelingspictogram om een andere waarde aan elk veld te geven.<br /> </p> </td> 
     </tr> 
     <tr> 
      <td>Hoogte</td> 
      <td>4.75rem</td> 
     </tr> 
    </tbody> 
   </table>

1. Tik op de voettekstwidget en tik op **[!UICONTROL Footer]**. Breid uit **[!UICONTROL Background]** accordeon instellen **[!UICONTROL Background Color]** tot `F6921E`en tikken ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

### De component voor gegevensvastlegging opmaken en een achtergrond op het adaptieve formulier toepassen {#style-the-data-capture-component-and-apply-a-background-to-the-adaptive-form}

U kunt meerdere componenten in een adaptief formulier gebruiken om gegevens vast te leggen. Bijvoorbeeld tekstvak en numeriek vak. U kunt identieke stijl aan alle gegevens verstrekken vangt componenten of afzonderlijke stijl voor elke component. In deze zelfstudie wordt een identieke stijl toegepast op numerieke vakken (Customer ID, ZIP Code) en tekstvakken (Customer ID, Name, Shipping Address, State, Email). De componenten voor gegevensvastlegging opmaken:

1. Tik op de knop **[!UICONTROL Customer ID]** en tik op **[!UICONTROL Field Widget]** optie. Stel de volgende eigenschappen in en tik op ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

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
        <li>Boven: 7 px<br /> </li> 
        <li>Rechts: 7 px<br /> </li> 
        <li>Onder: 7 px<br /> </li> 
        <li>Links: 7 px<br /> </li> 
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
      <td>18px</td> 
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

1. Tik op het lege gebied boven de **[!UICONTROL Customer ID]** veld en tik **[!UICONTROL Responsive Panel Container]**. Stel de **[!UICONTROL Background]** > **[!UICONTROL Background Color]** tot F1F2F2. Tikken ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

   ![](do-not-localize/responsive-panel-container.png)

### De knoppen opmaken {#style-the-buttons}

U kunt een aangepast thema gebruiken om een identieke stijl toe te passen op alle knoppen van het aangepaste formulier en [inline styling](/help/forms/using/inline-style-adaptive-forms.md) om een stijl op een specifieke knoop toe te passen. De knoppen opmaken:

1. Tik op de knop **[!UICONTROL Submit]** en tikken op **[!UICONTROL Button]** optie. Stel de volgende eigenschappen in en tik op ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

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
        <li>Boven: 7 px<br /> </li> 
        <li>Rechts: 7 px<br /> </li> 
        <li>Onder: 7 px<br /> </li> 
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
      <td>18px</td> 
     </tr> 
    </tbody> 
   </table>

1. [Het aangepaste thema toepassen](/help/forms/using/style-your-adaptive-form.md#step-apply-a-theme-to-your-adaptive-form), Global Theme, in uw adaptieve vorm. Als de stijl niet op het adaptieve formulier wordt weerspiegeld, maakt u de cache van de browser leeg en probeert u het opnieuw.

   ![style-data-capture-components](assets/style-data-capture-components.png)

## Stap 4: Afzonderlijke componenten opmaken {#step-style-individual-components}

Sommige stijlen zijn alleen van toepassing op een bepaalde component. Dergelijke componenten worden opgemaakt in de editor voor adaptieve formulieren.

1. Open het aangepaste formulier voor bewerking. [http://localhost:4502/editor.html/content/forms/af/shipping-address-add-update-form.html](http://localhost:4502/editor.html/content/forms/af/change-billing-shipping-address.html)
1. Selecteer op de bovenste balk de optie **[!UICONTROL Style]** optie.

   ![style-option](assets/style-option.png)

1. Tik op de knop **[!UICONTROL Attach]** en tikken op ![aem_6_3_edit](assets/aem_6_3_edit.png)pictogram. Stel de volgende eigenschappen in in het dialoogvenster **[!UICONTROL Dimensions and Position]** accordeon:

   | Eigenschap | Waarde |
   |---|---|
   | Zwevend | Links |
   | Breedte | 10% |

1. Tik op de knop **[!UICONTROL Government approved address proof]** tikken en tikken op de knop ![aem_6_3_edit](assets/aem_6_3_edit.png)pictogram. Stel de volgende eigenschappen in:

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
      <td>40px</td> 
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
      <td>1px</td> 
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
      <td>7px</td> 
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
      <td>18px</td> 
     </tr> 
     <tr> 
      <td>Tekst</td> 
      <td>Lijnhoogte</td> 
      <td>2</td> 
     </tr> 
     </tr> 
    </tbody> 
   </table>

1. Tik op de knop **[!UICONTROL Submit]** en tikken op ![aem_6_3_edit](assets/aem_6_3_edit.png) pictogram. Stel de volgende eigenschappen in:

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
        <li>Links: 20 px<br /> </li> 
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

[!DNL Adobe Fonts] is een service voor weblettertypen. U kunt de service configureren en gebruiken met adaptieve formulieren. Te gebruiken [!DNL Adobe Fonts] in adaptieve vorm:

>[!NOTE]
>
>![typekit-to-adobe-fonts](assets/typekit-to-adobe-fonts.png) [!DNL Typekit] wordt nu Adobe Fonts genoemd en wordt opgenomen bij Creative Cloud en andere abonnementen. [Meer informatie](https://fonts.adobe.com/).

1. Een [Adobe Fonts](https://typekit.com/) -account, een kit maken, lettertype Myriad Pro aan de kit toevoegen, de kit publiceren en de kit-id ophalen. Het is verplicht [!DNL Adobe Fonts] (Weblettertypen) in een adaptieve vorm.
1. In de AEM [!DNL Forms] server, navigeren naar ![adobeexperienceManager](assets/adobeexperiencemanager.png) **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Tools]** ![hamer](assets/hammer.png) > **[!UICONTROL Adobe Fonts]**. Open nu een configuratiemap. Als er al een configuratie beschikbaar is, klikt u op de knop **[!UICONTROL Create]** om een nieuwe instantie te maken.

   Geef in het dialoogvenster Configuratie maken een **Titel** voor de configuratie en klik op **[!UICONTROL Create]**. U wordt opnieuw gericht aan de configuratiepagina. In de [!UICONTROL Edit Component] wordt weergegeven, geeft u uw **Kit-id** en klik op **[!UICONTROL OK]**.

1. Vorm uw thema om te gebruiken [!DNL Adobe Fonts] configuratie. Open in de instantie van de auteur **[!UICONTROL Global Theme]** in de themaeditor. Navigeer in de themaeditor naar **[!UICONTROL Theme Options]** ![thema-opties](assets/theme-options.png) > **[!UICONTROL Configure]**. In **[!UICONTROL Adobe Fonts Configuration]** , selecteert u de kit en klikt u op **[!UICONTROL Save]**.

   De lettertypen die aan de **[!UICONTROL Adobe Fonts]** zijn beschikbaar voor selectie in **[!UICONTROL Text]** van alle componenten.
