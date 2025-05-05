---
title: Stijl uw adaptieve formulier
description: Leer een aangepast thema te maken, afzonderlijke onderdelen op te maken en Webben Fonts in een thema te gebruiken.
topic-tags: introduction
feature: Adaptive Forms
exl-id: 7742c3ca-1755-44c5-b70f-61309f09d1b8
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '1948'
ht-degree: 0%

---

# Stijl uw adaptieve formulier {#do-not-publish-style-your-adaptive-form}

Leer een aangepast thema te maken, afzonderlijke onderdelen op te maken en Webben Fonts in een thema te gebruiken.

![ held-beeld ](do-not-localize/08-style_your_adaptiveformmain.png)

Dit leerprogramma is een stap in [ creeert Uw Eerste AanpassingsVorm ](https://helpx.adobe.com/nl/experience-manager/6-3/forms/using/create-your-first-adaptive-form.html) reeksen. De Adobe raadt u aan de reeks in chronologische volgorde te volgen om de volledige Gebruikszaak van de zelfstudie te begrijpen, uit te voeren en te demonstreren.

## Over de zelfstudie  {#about-the-tutorial}

U kunt thema&#39;s gebruiken om een adaptief formulier een unieke vormgeving en stijl te geven. U kunt kant-en-klare thema&#39;s toepassen die worden geleverd met de adaptieve formuliereditor of zelf aangepaste thema&#39;s maken. AEM [!DNL Forms] verstrekken a [ themaredacteur ](https://helpx.adobe.com/nl/experience-manager/6-3/forms/using/themes.html) om douanethema&#39;s tot stand te brengen. Met één thema kunt u hetzelfde adaptieve formulier weergeven dat u op mobiele apparaten, tablets of desktops hebt geopend. Eerdere kennis van CSS of LESS is niet vereist voor het gebruik van de themaeditor, maar is wel gewenst.

Aan het einde van de zelfstudie moet u het volgende kunnen doen:

* Een thema uit het vak toepassen op een adaptief formulier
* Een thema maken voor een adaptief formulier met de themaeditor
* Afzonderlijke componenten opmaken
* Bonussectie: Webben Fonts gebruiken in een aangepast thema

Het formulier moet er ongeveer als volgt uitzien nadat u de zelfstudie hebt voltooid:

![ Vorm met een douanethema ](assets/styled-adaptive-form.png)

## Voordat u begint {#before-you-start}

Download de koptekst- en logo-afbeeldingen hieronder op uw lokale computer. De koptekst van het `shipping-address-add-update-form` adaptieve formulier gebruikt de koptekst- en logo-afbeeldingen. De koptekstafbeelding wordt rechts van de koptekst weergegeven.

[Bestand ophalen](assets/header-style.png)

[Bestand ophalen](assets/logo-1.png)

## Stap 1: Een thema toepassen op het aangepaste formulier {#step-apply-a-theme-to-your-adaptive-form}

De adaptieve vormenredacteur verstrekt veelvoudige uit-van-de-doos thema&#39;s. Als u geen aangepaste stijl wilt gebruiken voor het aangepaste formulier, kunt u ook uw aangepaste formulieren publiceren met een thema dat buiten de verpakking valt. Thema&#39;s zijn onafhankelijk van adaptieve vormen. U kunt hetzelfde thema toepassen op meerdere adaptieve formulieren.

**om een thema op uw adaptieve vorm toe te passen:**

1. Open het aangepaste formulier voor bewerking.

   [ http://localhost:4502/editor.html/content/forms/af/shipping-address-add-update-form.html](http://localhost:4502/editor.html/content/forms/af/shipping-address-add-update-form.html)

1. Open eigenschappen van **[!UICONTROL Adaptive Form container]** . Navigeer in de eigenschappenbrowser naar **[!UICONTROL Basic]** > **[!UICONTROL Adaptive Form Theme]** . In het veld **[!UICONTROL Adaptive Form Theme]** worden alle kant-en-klare thema&#39;s en aangepaste thema&#39;s weergegeven. Standaard wordt het thema Canvas toegepast.
1. Selecteer een thema in het veld **[!UICONTROL Adaptive Form Theme]** . Bijvoorbeeld, **het thema van het Onderzoek**. Selecteer ![ name_6_3_forms_save ](assets/aem_6_3_forms_save.png) zodat kunt u het geselecteerde thema toepassen.

   ![ Aangepaste vorm met het standaardthema ](assets/default-adaptive-form.png)

   **Cijfer:** *Aangepaste vorm met het standaardthema*

   ![ Aangepaste vorm met het thema van het Onderzoek ](assets/adaptive-form-with-survey-theme.png)

   **Figuur:** *Aangepaste vorm met het thema van het Onderzoek*

## Stap 2: Werk het aangepaste formulier bij {#step-update-your-adaptive-form}

Voor het hierboven weergegeven ontwerp zijn wijzigingen vereist in de plaatsaanduidingstekst en het logo van het bestaande adaptieve formulier.

**om uw adaptieve vorm bij te werken:**

1. Wijzig het bestaande logo en de tekst van de koptekst. Het logo verwijderen:

   1. Open het formulier in de formuliereditor.

      [ http://localhost:4502/editor.html/content/forms/af/shipping-address-add-update-form.html](http://localhost:4502/editor.html/content/forms/af/shipping-address-add-update-form.html)

   1. Selecteer het embordbeeld in de [!UICONTROL header] component en selecteer ![ cmp ](assets/cmppr.png) **[!UICONTROL properties]**. Selecteer in de eigenschap [!UICONTROL image] de optie X om de bestaande logoafbeelding te verwijderen.
   1. Selecteer **[!UICONTROL upload]**, selecteer logo.png, en selecteer ![ aem_6_3_forms_save ](assets/aem_6_3_forms_save.png) om de veranderingen te bewaren. Het beeld werd gedownload in [ alvorens u ](/help/forms/using/style-your-adaptive-form.md#before-you-start) sectie begint.
   1. Selecteer kopbaltekst, `We.Retail`, en selecteer ![ aem_6_3_edit ](assets/aem_6_3_edit.png) **[!UICONTROL edit]**. Wijzig de koptekst in `we retail` . Pas vette opmaak alleen toe op `we` in `we retail` .

      ![ wij-retail-logo-text ](assets/we-retail-logo-text.png)

1. Titel verwijderen en plaatsaanduidingstekst toevoegen:

   1. Selecteer het gebied van identiteitskaart van de Klant en selecteer ![ cmp ](assets/cmppr.png) eigenschappen.
   1. Kopieer de inhoud van het veld **[!UICONTROL Title]** naar het veld **[!UICONTROL Placeholder Text]** .
   1. Schrap de inhoud van het **[!UICONTROL Title]** gebied en selecteer ![ aem_6_3_forms_save ](assets/aem_6_3_forms_save.png).
   1. Herhaal de vorige drie stappen voor alle tekstvakken, het numerieke vak en het e-mailveld in het formulier.

      ![ update-adaptive-form ](assets/updated-adaptive-form.png)

## Stap 3: Een aangepast thema maken voor het aangepaste formulier {#step-create-a-custom-theme-for-your-adaptive-form}

U kunt de [ themaredacteur ](/help/forms/using/themes.md) gebruiken om douanethema&#39;s tot stand te brengen. De themaredacteur is een almachtige redacteur WYSIWYG. Het is een visuele methode om CSS op diverse componenten van een adaptieve vorm toe te passen. Het biedt fijnere besturingselementen voor stijlcomponenten en deelvensters van een adaptieve vorm.

Een thema is een afzonderlijke entiteit, zoals adaptieve formulieren. Deze bevat stijlen (CSS) voor de componenten en deelvensters van een adaptief formulier. Stijlen omvatten CSS-eigenschappen zoals achtergrondkleuren, statuskleuren, transparantie, uitlijning en grootte. Wanneer u een thema toepast, wordt de opgegeven stijl toegepast op de corresponderende componenten van een adaptief formulier.

In deze zelfstudie maakt u een stijl van de kop- en voettekst, tekst en numerieke componenten, de bijlage en knoppen. Laten we beginnen met het maken van een thema:

### Een thema maken {#create-a-theme}

1. Meld u aan bij de AEM auteur en navigeer naar **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Themes]** . Het gebrek URL is [ http://localhost:4502/aem/forms.html/content/dam/formsanddocuments-themes ](http://localhost:4502/aem/forms.html/content/dam/formsanddocuments-themes).
1. Selecteer **[!UICONTROL Create]** en selecteer **[!UICONTROL Theme]** . De pagina [!UICONTROL Create Theme] met de velden die nodig zijn om een thema te maken, wordt weergegeven. De velden **[!UICONTROL Title]** en **[!UICONTROL Name]** zijn verplicht:

   * **Titel:** specificeer een titel van het thema. Bijvoorbeeld, **Globaal Thema.** Met de titel kunt u het thema herkennen aan de lijst met thema&#39;s.
   * **Naam:** specificeer de naam van het thema. Bijvoorbeeld, **globaal-Thema.** Er wordt een knooppunt met de opgegeven naam gemaakt in de repository. Wanneer u een titel begint te typen, wordt automatisch de waarde voor het naamveld gegenereerd. U kunt de voorgestelde waarde wijzigen. Het naamveld mag alleen alfanumerieke tekens, afbreekstreepjes en onderstrepingstekens bevatten. Alle ongeldige invoer wordt vervangen door een afbreekstreepje.

1. Selecteer **[!UICONTROL Create]**. Er wordt een thema gemaakt en er verschijnt een dialoogvenster waarin u het formulier kunt openen om het te bewerken. Selecteer **[!UICONTROL Open]** om het nieuwe thema op een nieuw tabblad te openen. Het thema wordt geopend in de themaeditor. Voor de opmaak gebruikt de themaeditor een adaptief formulier dat niet meer in de doos wordt geleverd bij AEM [!DNL Forms] .

   Voor informatie over het gebruiken van de themaredacteur UI, zie [ Ongeveer de themaredacteur ](/help/forms/using/themes.md#aboutthethemeeditor).

1. Selecteer **[!UICONTROL Theme Options]** ![ thema-opties ](assets/theme-options.png) > **[!UICONTROL Configure]**. Op het **[!UICONTROL Preview Form]** gebied, selecteer **verschepen-adres-toe:voegen-update-vorm** adaptieve vorm, uitgezochte ![ aem_6_3_forms_save ](assets/aem_6_3_forms_save.png), **[!UICONTROL Save]**. De themaeditor is nu geconfigureerd voor het gebruik van uw eigen adaptieve formulier in plaats van het standaard adaptieve formulier. Selecteer **[!UICONTROL Cancel]** om terug te keren naar de themaeditor.

   ![ douane-thema ](assets/custom-theme.png)

   **Cijfer:** *de redacteur van het Thema met het verschepen-adres-toe:voegen-update-vorm adaptieve vorm*

   ![ creeer-a-thema ](assets/create-a-theme.png)

   **Cijfer:** *Aangepaste vorm met de standaardvorm*

### Stijlkop- en voettekst {#style-header-and-footer}

Koptekst en voettekst geven een consistent en duidelijk beeld van een adaptief formulier. Over het algemeen bevat de koptekst het logo en de naam van de organisatie, bevat de voettekst copyrightinformatie en deze blijven in meerdere vormen van een organisatie identiek. De kop- en voettekst van het adaptieve formulier voor het verzendadres-add-update-formulier opmaken:

1. Navigeer in het deelvenster Kiezers naar de optie **[!UICONTROL Header]** > **[!UICONTROL Text]** . Het deelvenster Kiezers bevindt zich links van de themaeditor. Als het paneel niet zichtbaar is, uitgezochte ![ knevel-zij-paneel ](assets/toggle-side-panel.png) Knevel paneel.

1. Plaats de volgende eigenschappen in **[!UICONTROL Text]** accordion en selecteer ![ aem_6_3_forms_save ](assets/aem_6_3_forms_save.png).

   | Eigenschap | Waarde |
   |---|---|
   | Lettertypefamilie | Arial® |
   | Lettertypekleur | FFFFFF |
   | Tekengrootte | 54 px |

1. Selecteer de [!UICONTROL header] -widget en selecteer **[!UICONTROL Header]** . De opties voor het opmaken van de koptekstwidget worden aan de linkerkant weergegeven. Breid **[!UICONTROL Dimensions & Position]** accordion uit, plaats **[!UICONTROL Height]** aan `120px`, en selecteer ![ aem_6_3_forms_save ](assets/aem_6_3_forms_save.png).
1. Vouw de accordeon **[!UICONTROL Background]** van de koptekstwidget uit, stel de **[!UICONTROL Background Color]** in op `F6921E.`

   Houd de cursor boven **[!UICONTROL Image & Gradient]** > **[!UICONTROL + Add]** en selecteer **[!UICONTROL Image]** . Plaats de volgende eigenschappen en selecteer ![ aem_6_3_forms_save ](assets/aem_6_3_forms_save.png).

   | Eigenschap | Waarde |
   |---|---|
   | image | Upload header-style.png. Het beeld werd gedownload in [ alvorens u ](/help/forms/using/style-your-adaptive-form.md#before-you-start) sectie begint. |
   | Positie | Rechts onder |
   | Naast elkaar | Niet herhalen |

1. Selecteer in de themaeditor het logo in de koptekst en selecteer **[!UICONTROL Header Logo]** . Breid de Dimensionen &amp; de accordeon van de Positie uit, plaats de volgende eigenschappen en selecteer ![ aem_6_3_forms_save ](assets/aem_6_3_forms_save.png).

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
        <li>Boven: 1,5 rem</li> 
        <li>Onder: -35 px</li> 
        <li>Links: 1rem <strong><br /> </strong></li> 
       </ul> <p><strong> Uiteinde:</strong> selecteer het <img src="assets/link.png"> verbindingspictogram om een verschillende waarde aan elk gebied te verstrekken.<br /> </p> </td> 
     </tr> 
     <tr> 
      <td>Hoogte</td> 
      <td>4.75 rem</td> 
     </tr> 
    </tbody> 
   </table>

1. Selecteer de voettekstwidget en selecteer **[!UICONTROL Footer]** . Breid **[!UICONTROL Background]** accordion uit, plaats **[!UICONTROL Background Color]** aan `F6921E`, en selecteer ![ aem_6_3_forms_save ](assets/aem_6_3_forms_save.png).

### De component voor gegevensvastlegging opmaken en een achtergrond op het adaptieve formulier toepassen {#style-the-data-capture-component-and-apply-a-background-to-the-adaptive-form}

U kunt meerdere componenten in een adaptief formulier gebruiken om gegevens vast te leggen. Bijvoorbeeld tekstvak en numeriek vak. U kunt voor elke component een identieke stijl opgeven voor alle componenten voor het vastleggen van gegevens of een aparte stijl. In deze zelfstudie wordt een identieke stijl toegepast op numerieke vakken (Customer ID, ZIP Code) en tekstvakken (Customer ID, Name, Shipping Address, State, Email). De componenten voor gegevensvastlegging opmaken:

1. Selecteer het veld **[!UICONTROL Customer ID]** en selecteer de optie **[!UICONTROL Field Widget]** . Plaats de volgende eigenschappen en selecteer ![ aem_6_3_forms_save ](assets/aem_6_3_forms_save.png).

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
        <li>Boven: 7 px <br /> </li> 
        <li>Rechts: 7 px <br /> </li> 
        <li>Onder: 7 px <br /> </li> 
        <li>Links: 7 px <br /> </li> 
       </ul> </td> 
     </tr> 
     <tr> 
      <td>Tekst</td> 
      <td>Lettertypefamilie</td> 
      <td>Arial®</td> 
     </tr> 
     <tr> 
      <td>Tekst</td> 
      <td>Lettertypekleur</td> 
      <td>939598 <br /> </td> 
     </tr> 
     <tr> 
      <td>Tekst</td> 
      <td>Tekengrootte</td> 
      <td>18 px</td> 
     </tr> 
     <tr> 
      <td>Dimensionen en positie</td> 
      <td>Breedte</td> 
      <td>60%</td> 
     </tr> 
     <tr> 
      <td>Dimensionen en positie</td> 
      <td>Marge</td> 
      <td> 
       <ul> 
        <li>Links: 10 rem</li> 
       </ul> </td> 
     </tr> 
    </tbody> 
    </table>

1. Selecteer het lege gebied boven het veld **[!UICONTROL Customer ID]** en selecteer **[!UICONTROL Responsive Panel Container]** . Stel **[!UICONTROL Background]** > **[!UICONTROL Background Color]** in op F1F2F2. Selecteer ![ name_6_3_forms_save ](assets/aem_6_3_forms_save.png).

   ![ Responsieve paneelcontainer ](do-not-localize/responsive-panel-container.png)

### De knoppen opmaken {#style-the-buttons}

U kunt een douanethema gebruiken om een identieke stijl op alle knopen van de adaptieve vorm toe te passen en [ gealigneerd het stileren ](/help/forms/using/inline-style-adaptive-forms.md) om een stijl op een specifieke knoop toe te passen. U kunt als volgt de knoppen opmaken:

1. Selecteer de knop **[!UICONTROL Submit]** en selecteer de optie **[!UICONTROL Button]** . Plaats de volgende eigenschappen en selecteer ![ aem_6_3_forms_save ](assets/aem_6_3_forms_save.png).

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
      <td>Rand <br /> </td> 
      <td>Randkleur</td> 
      <td>F6921E</td> 
     </tr> 
     <tr> 
      <td>Rand</td> 
      <td>Straal rand </td> 
      <td> 
       <ul> 
        <li>Boven: 7 px <br /> </li> 
        <li>Rechts: 7 px <br /> </li> 
        <li>Onder: 7 px <br /> </li> 
        <li>Links: 7 px</li> 
       </ul> </td> 
     </tr> 
     <tr> 
      <td>Tekst<br /> </td> 
      <td>Lettertypefamilie</td> 
      <td>Arial®</td> 
     </tr> 
     <tr> 
      <td>Tekst</td> 
      <td>Lettertypekleur</td> 
      <td>FFFFFF</td> 
     </tr> 
     <tr> 
      <td>Tekst</td> 
      <td>Tekengrootte</td> 
      <td>18 px</td> 
     </tr> 
    </tbody> 
   </table>

1. [ pas het douanethema ](/help/forms/using/style-your-adaptive-form.md#step-apply-a-theme-to-your-adaptive-form), Globaal Thema, op uw adaptieve vorm toe. Als de stijl niet op het adaptieve formulier wordt weerspiegeld, maakt u de cache van de browser leeg en probeert u het opnieuw.

   ![ stijl-gegeven-vangst-componenten ](assets/style-data-capture-components.png)

## Stap 4: afzonderlijke onderdelen opmaken {#step-style-individual-components}

Sommige stijlen zijn alleen van toepassing op een bepaalde component. Dergelijke componenten worden opgemaakt in de editor voor adaptieve formulieren.

1. Open het aangepaste formulier voor bewerking. [ http://localhost:4502/editor.html/content/forms/af/shipping-address-add-update-form.html](http://localhost:4502/editor.html/content/forms/af/change-billing-shipping-address.html)
1. Selecteer op de bovenste balk de optie **[!UICONTROL Style]** .

   ![ stijl-optie ](assets/style-option.png)

1. Selecteer de **[!UICONTROL Attach]** knoop en selecteer ![ aem_6_3_edit ](assets/aem_6_3_edit.png) pictogram. Stel de volgende eigenschappen in in de accordeon **[!UICONTROL Dimensions and Position]** :

   | Eigenschap | Waarde |
   |---|---|
   | Float | Links |
   | Breedte | 10% |

1. Selecteer de **[!UICONTROL Government approved address proof]** optie en selecteer ![ aem_6_3_edit ](assets/aem_6_3_edit.png) pictogram. Stel de volgende eigenschappen in:

   <table> 
    <tbody> 
     <tr> 
      <td><b>Accordeon</b></td> 
      <td><b>Eigenschap</b></td> 
      <td><b>Waarde</b></td> 
     </tr> 
     <tr> 
      <td>Dimensionen en positie</td> 
      <td>Float</td> 
      <td>Links</td> 
     </tr> 
     <tr> 
      <td>Dimensionen en positie</td> 
      <td>Breedte</td> 
      <td>73%</td> 
     </tr> 
     <tr> 
      <td>Dimensionen en positie</td> 
      <td>Opvulling</td> 
      <td> 
       <ul> 
        <li>Links: 10 px</li> 
       </ul> </td> 
     </tr> 
     <tr> 
      <td>Dimensionen en positie</td> 
      <td>Hoogte</td> 
      <td>40 px</td> 
     </tr> 
     <tr> 
      <td>Dimensionen en positie <br /> </td> 
      <td>Marge</td> 
      <td><br /> 
       <ul> 
        <li>Recht: 2 rem</li> 
        <li>Links: 10 rem </li> 
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
      <td>Effen</td> 
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
      <td>Arial®</td> 
     </tr> 
     <tr> 
      <td>Tekst</td> 
      <td>Lettertypekleur</td> 
      <td>BCBEC0</td> 
     </tr> 
     <tr> 
      <td>Tekst</td> 
      <td>Tekengrootte</td> 
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

1. Selecteer de **[!UICONTROL Submit]** knoop en selecteer ![ aem_6_3_edit ](assets/aem_6_3_edit.png) pictogram. Stel de volgende eigenschappen in:

   <table> 
    <tbody> 
     <tr> 
      <td><b>Accordeon</b></td> 
      <td><b>Eigenschap</b></td> 
      <td><b>Waarde</b></td> 
     </tr> 
     <tr> 
      <td>Dimensionen en positie</td> 
      <td>Float</td> 
      <td>Rechts</td> 
     </tr> 
     <tr> 
      <td>Dimensionen en positie</td> 
      <td>Marge</td> 
      <td> 
       <ul> 
        <li>Boven: 5 rem</li> 
        <li>Rechts: 14 rem</li> 
        <li>Onder: 20 px</li> 
        <li>Links: 20 px <br /> </li> 
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

   ![ stiled-adaptive-form-1 ](assets/styled-adaptive-form-1.png)

## Stap 5: Sectie van de beurs: Het gebruiken van Webben Fonts in een douanethema {#step-bonus-section-using-web-fonts-in-a-custom-theme}

U kunt verschillende lettertypen gebruiken om een adaptief formulier te ontwerpen. Op alle apparaten waarop het adaptieve formulier wordt weergegeven, worden mogelijk niet de fonts gebruikt om het adaptieve formulier te ontwerpen. U kunt een service voor weblettertypen gebruiken om de vereiste lettertypen aan het doelapparaat te leveren.

[!DNL Adobe Fonts] is een service Webben Fonts. U kunt de service configureren en gebruiken met adaptieve formulieren. U kunt [!DNL Adobe Fonts] als volgt aanpassen:
1. Blader de [ bibliotheek van de doopvonten van de Adobe ](https://fonts.adobe.com/) en kies doopvont om uw vorm te stileren.
<!--
>[!NOTE]
>
>![typekit-to-adobe-fonts](assets/typekit-to-adobe-fonts.png) [!DNL Typekit] is now called Adobe Fonts and is included with Creative Cloud and other subscriptions. [Learn more](https://fonts.adobe.com/).-->

>[!NOTE]
>
> U kunt labels of filters toevoegen om de lijst met lettertypen te verfijnen.

1. Klik op de knop &lt;/> om de familie aan een webproject toe te voegen, voor het geval u een lettertype vindt dat u bevalt.

   ![ selecteren-doopvont-van-doopvont-bibliotheek ](assets/select-font-from-font-library.png)

   Er verschijnt een dialoogvenster Lettertypen toevoegen aan een webproject.

   >[!NOTE]
   >
   > U kunt alleen lettertypen aan uw webproject toevoegen als de knop &lt;/> beschikbaar is.

2. Noem uw Webproject.
3. Schakel de selectievakjes in om de tekendikten en -stijlen te selecteren die u wilt opnemen.

   ![ voeg een doopvontbibliotheek ](assets/add-a-font-window.png) toe

4. Selecteer **klik** om het project tot stand te brengen.
5. Kopieer de insluitcode en de URL van het scherm.
   ![ bed code en URL ](assets/font-add-url.png) in

6. Klik **Gedaan** om het venster van het Webproject te sluiten.
7. Meld u aan bij uw AEM en ga naar de URL `http://server:port/crx/de/index.jsp#`
8. Maak bijvoorbeeld een mapstructuur in CRXDE `/apps/[fontslibrary]/[customlibrary(clientlibrary)]` .
9. Ga naar de nieuwe map `clientlibs` en voeg de eigenschappen `allowProxy` en `categories` toe.
10. Navigeer naar `/apps/[fontslibrary]/[customlibrary(clientlibrary)]` en maak een css-map.
11. Ga naar de gemaakte CSS-map en maak een bestand. Maak bijvoorbeeld een bestand als `fonts.css` en plak de insluitcode samen met de URL.
    ![ de structuur van de Omslag ](/help/forms/using/assets/fonts-add-in-crxde.png)
12. Sla de wijzigingen op.

>[!NOTE]
>
> Als u de toegevoegde aangepaste lettertypen in een adaptief formulier wilt gebruiken, moet u ervoor zorgen dat de naam van de clientbibliotheek in de **[!UICONTROL Client Library Category]** wordt uitgelijnd met de naam die is opgegeven in de categoriesoptie van de clientlib-map.

De opgenomen lettertypen zijn nu toegankelijk voor het adaptieve formulier via de volgende aangepaste clientbibliotheek voor lettertypen.


<!--
Create Adobe Fonts Configuration

1. To create a API Token, go to **login** > **API Token** > **Make me a new API token**.

   ![API token](/help/forms/using/assets/fonts-api-token.png)

2. Once, you click **Make me a new API token**, a new token is generated. 
3. Copy the generated token for future use.
4. Now login to your AEM  author instance. On the author instance, go to **[!UICONTROL Tools]**>**[!UICONTROL Cloud Services]**> **[!UICONTROL Adobe Fonts]**.
5. Select the configuration container and click **Create**. **[UICONTROL Create Adobe Fonts Configuration]** screen appears.
    ![API token](/help/forms/using/adobe-font-configuration-screen.png)

6. Spceify the name and paste the API token in the **[!UICONTROL Kit ID]** textbox.
7. Click **Create**.



The fonts added to the **[!UICONTROL Adobe Fonts]** are available for selection in the **[!UICONTROL Text]** accordion of all the components.
1. In the theme editor, navigate to **[!UICONTROL Theme Options]** ![theme-options](assets/theme-options.png) > **[!UICONTROL Configure]**. 
2. In the **[!UICONTROL Adobe Fonts Configuration]** field, select the kit, and click **[!UICONTROL Save]**.


1. Create an [Adobe Fonts](https://fonts.adobe.com/?ref=tk.com) account, create a kit, add font Myriad Pro to the kit, publish the kit, and obtain the Kit ID. It is required to use [!DNL Adobe Fonts] (Web Fonts) in an adaptive form. 
1. In the AEM [!DNL Forms] Server, navigate to ![adobeexperiencemanager](assets/adobeexperiencemanager.png) **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Tools]** ![hammer](assets/hammer.png) > **[!UICONTROL Adobe Fonts]**. Now, open a configuration folder. If a configuration is already available, click the **[!UICONTROL Create]** button to create an instance.

   On the Create Configuration dialog, specify a **Title** for the configuration, and click **[!UICONTROL Create]**. You are redirected to the configuration page. In the [!UICONTROL Edit Component] dialog that appears, provide your **Kit ID** and click **[!UICONTROL OK]**. -->


