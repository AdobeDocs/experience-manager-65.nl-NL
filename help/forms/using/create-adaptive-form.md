---
title: 'Lesbestand: een adaptief formulier maken'
description: Leer een adaptief formulier te maken, in te delen en voor te vertonen. Leer ook verzendhandelingen te configureren.
feature: Adaptive Forms
exl-id: c0a2adcd-528a-41af-99b5-d8b423cd6605
source-git-commit: 9d497413d0ca72f22712581cf7eda1413eb8d643
workflow-type: tm+mt
source-wordcount: '1258'
ht-degree: 0%

---

# Lesbestand: een adaptief formulier maken {#do-not-publish-tutorial-create-an-adaptive-form}

![02-create-adaptive-form-main-image](assets/02-create-adaptive-form-main-image.png)

Deze zelfstudie is een stap in de [Uw eerste adaptieve formulier maken](/help/forms/using/create-your-first-adaptive-form.md) reeks. U wordt aangeraden de reeks in chronologische volgorde te volgen om het volledige gebruik van de zelfstudie te begrijpen, uit te voeren en aan te tonen.

## Over de zelfstudie {#about-the-tutorial}

Adaptieve formulieren zijn formulieren van de nieuwe generatie die dynamisch zijn en reageren. U kunt adaptieve formulieren gebruiken om persoonlijke ervaringen te bieden. U kunt adaptieve formulieren ook integreren met [!DNL Adobe Analytics] voor gebruiksstatistieken en [!DNL Adobe Campaign] voor campagnebeheer. Zie voor meer informatie over adaptieve formuliermogelijkheden [Inleiding tot het ontwerpen van adaptieve formulieren](/help/forms/using/introduction-forms-authoring.md).

Het is eenvoudiger om formulieren te maken en te beheren wanneer een correct proces wordt gevolgd. In dit artikel leert u hoe u:

* [Een adaptief formulier maken waarmee een klant een verzendadres kan toevoegen](/help/forms/using/create-adaptive-form.md#step-create-the-adaptive-form)

* [Indelingsvelden van een adaptief formulier voor het weergeven en accepteren van informatie van een klant](/help/forms/using/create-adaptive-form.md#step-add-header-and-footer)

* [Verzendactie maken om een e-mail met formulierinhoud te verzenden](/help/forms/using/create-adaptive-form.md#step-add-components-to-capture-and-display-information)
* [Een adaptief formulier voorvertonen en verzenden](/help/forms/using/create-adaptive-form.md)

Aan het einde van het artikel hebt u een formulier dat vergelijkbaar is met het volgende:\
[![Formuliervoorbeeld in mobiele apparaten](do-not-localize/form-preview-mobile.gif)](do-not-localize/form-preview-mobile.gif)

## Stap 1: Maak het adaptieve formulier {#step-create-the-adaptive-form}

1. Meld u aan bij de AEM auteur en navigeer naar **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]**. De standaard-URL is [http://localhost:4502/aem/forms.html/content/dam/formsanddocuments](http://localhost:4502/aem/forms.html/content/dam/formsanddocuments).
1. Selecteren **[!UICONTROL Create]** en selecteert u **[!UICONTROL Adaptive Form]**. Er verschijnt een optie voor het selecteren van een sjabloon. Selecteer de **[!UICONTROL Blank]** sjabloon om het te selecteren en te selecteren **[!UICONTROL Next]**.

1. Een optie voor **[!UICONTROL Add Properties]** wordt weergegeven. De **[!UICONTROL Title]** en **[!UICONTROL Name]** velden zijn verplicht:

   * **Titel:** Opgeven `Add new or update shipping address` in de **[!UICONTROL Title]** veld. In het titelveld wordt de weergavenaam van het formulier opgegeven. Met de titel kunt u het formulier identificeren in de AEM [!DNL Forms] gebruikersinterface.
   * **Naam:** Opgeven `shipping-address-add-update-form` in de **[!UICONTROL Name]** veld. In het veld Naam wordt de naam van het formulier opgegeven. Er wordt een knooppunt met de opgegeven naam gemaakt in de repository. Wanneer u een titel begint te typen, wordt automatisch een waarde voor het naamveld gegenereerd. U kunt de voorgestelde waarde wijzigen. Het naamveld mag alleen alfanumerieke tekens, afbreekstreepjes en onderstrepingstekens bevatten. Alle ongeldige invoer wordt vervangen door een afbreekstreepje.

1. Selecteer **[!UICONTROL Create]**. Er wordt een adaptief formulier gemaakt en er wordt een dialoogvenster weergegeven om het formulier te openen voor bewerking. Selecteren **[!UICONTROL Open]** om het nieuwe formulier te openen op een nieuw tabblad. Het formulier wordt geopend voor bewerking. De zijbalk wordt ook weergegeven om het nieuwe formulier aan te passen aan de behoeften.

   Voor informatie over de adaptieve interface voor formulierontwerp en de beschikbare componenten raadpleegt u [Inleiding tot het ontwerpen van adaptieve formulieren](/help/forms/using/creating-adaptive-form.md).

   ![Een nieuw, adaptief formulier.](assets/newly-created-adaptive-form.png)

## Stap 2: kop- en voettekst toevoegen {#step-add-header-and-footer}

AEM [!DNL Forms] biedt veel componenten om informatie weer te geven op een adaptief formulier. De componenten Koptekst en Voettekst geven een formulier een consistent uiterlijk. Een koptekst bevat doorgaans het logo van een bedrijf, de titel van het formulier en het overzicht. Een voettekst bevat doorgaans copyrightinformatie en koppelingen naar andere pagina&#39;s.

1. Selecteren ![schakelen tussen zijpaneel](assets/toggle-side-panel.png) > ![uitvouwen](assets/treeexpandall.png). De componentbrowser wordt geopend. Sleep de **[!UICONTROL Header]** van componentbrowser naar het adaptieve formulier.
1. Selecteer **[!UICONTROL Logo]**. De werkbalk wordt weergegeven. Selecteren ![aem_6_3_edit](assets/aem_6_3_edit.png) op de werkbalk typt u **Wij.Detailhandel** en selecteert u ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

1. Selecteer Afbeelding. De werkbalk wordt weergegeven. Selecteren ![cmppr](assets/cmppr.png). De eigenschappenbrowser wordt links van het scherm geopend. **[!UICONTROL Browse]** en uploadt u de logoafbeelding. Selecteren ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png). De afbeelding wordt in de koptekst weergegeven.

   U kunt de optie Bestand ophalen selecteren om het logo te downloaden dat in dit artikel wordt gebruikt als u er geen hebt.

[Bestand ophalen](assets/logo.png)

1. Sleep de **[!UICONTROL Footer]** component van ![uitvouwen](assets/treeexpandall.png) op het adaptieve formulier. In dit stadium ziet het formulier er als volgt uit:

   ![adaptieve vorm met kop- en voetteksten](assets/adaptive-form-with-headers-and-footers.png)

## Stap 3: Voeg componenten toe aan het vastleggen en weergeven van informatie {#step-add-components-to-capture-and-display-information}

Componenten zijn bouwstenen van een adaptief formulier. AEM [!DNL Forms] biedt veel componenten voor het vastleggen en weergeven van informatie in een adaptieve vorm. U kunt de componenten slepen vanuit ![uitvouwen](assets/treeexpandall.png) op een formulier. Zie voor meer informatie over beschikbare componenten en de bijbehorende functionaliteit [Inleiding tot het ontwerpen van adaptieve formulieren](/help/forms/using/introduction-forms-authoring.md).

1. Sleep de **[!UICONTROL Numeric Box component]** op het adaptieve formulier. Plaats het voor de voettekstcomponent. Eigenschappen van component openen, wijzigen **[!UICONTROL Title]** van de component aan **`Customer ID`**, wijzigen **[!UICONTROL Element Name]** tot **`customer_ID`** de **[!UICONTROL Required Field]** optie, inschakelen **[!UICONTROL Use HTML5 Number Input Type]** en selecteert u ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).
1. Sleep drie tekstvakcomponenten naar het aangepaste formulier. Plaats deze voor de voettekstcomponent. Stel de volgende eigenschappen in voor deze tekstvakken.:

   <table> 
    <tbody> 
     <tr> 
      <td><b>Eigenschap</b></td> 
      <td><b>Tekstvak 1<br/></b></td> 
      <td><b>Tekstvak 2<br/></b></td> 
      <td><b>Tekstvak 3</b></td> 
     </tr> 
     <tr> 
      <td>Titel</td> 
      <td>Naam<br /> </td> 
      <td>Verzendadres</td> 
      <td>Staat</td> 
     </tr> 
     <tr> 
      <td>Elementnaam</td> 
      <td>customer_Name<br /> </td> 
      <td>customer_Shipping_Address</td> 
      <td>customer_State</td> 
     </tr> 
     <tr> 
      <td>Vereist veld</td> 
      <td>Ingeschakeld</td> 
      <td>Ingeschakeld</td> 
      <td>Ingeschakeld</td> 
     </tr> 
     <tr> 
      <td>Meerdere regels toestaan<br /> </td> 
      <td>Uitgeschakeld</td> 
      <td>Ingeschakeld</td> 
      <td>Uitgeschakeld</td> 
     </tr> 
    </tbody> 
   </table>

1. Sleep een **[!UICONTROL Numeric Box]** voor de voettekstcomponent. Open eigenschappen van de component, stel waarden in die in de onderstaande tabel worden vermeld, selecteer ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

   | Eigenschap | Waarde |
   |---|---|
   | Titel | Postcode |
   | Elementnaam | customer_ZIPCode |
   | Maximum aantal cijfers | 6 |
   | Vereist veld | Ingeschakeld |
   | Type weergavepatroon | Geen patroon |

1. Sleep een **[!UICONTROL Email]** voor de voettekstcomponent. Open eigenschappen van de component, stel waarden in die in de onderstaande tabel worden vermeld en selecteer ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

   | Eigenschap | Waarde |
   |---|---|
   | Titel | E-mail |
   | Elementnaam | customer_Email |
   | Vereist veld | Ingeschakeld |

1. Sleep een **[!UICONTROL File Attachment]** voor de voettekstcomponent. Open eigenschappen van de component, stel waarden in die in de onderstaande tabel worden vermeld en selecteer ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

   <table> 
    <tbody> 
     <tr> 
      <td><b>Eigenschap</b></td> 
      <td><b>Waarde</b></td> 
     </tr> 
     <tr> 
      <td>Titel</td> 
      <td>Door de overheid goedgekeurd adresbewijs<br /> </td> 
     </tr> 
     <tr> 
      <td>Elementnaam</td> 
      <td>customer_Address_Proof</td> 
     </tr> 
     <tr> 
      <td>Vereist veld</td> 
      <td>Ingeschakeld</td> 
     </tr> 
    </tbody> 
   </table>

1. Sleep een **[!UICONTROL Submit Button]** aan het adaptieve formulier. Plaats het voor de voettekstcomponent. Eigenschappen van component openen, elementnaam wijzigen in `address_addition_update_submit`, selecteert u ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png). De indeling van het formulier is voltooid en het formulier ziet er als volgt uit:

   ![adaptief-form-with-all-the-components](assets/adaptive-form-with-all-the-components.png)

## Stap 4: de verzendactie voor het aangepaste formulier configureren {#step-configure-submit-action-for-the-adaptive-form}

Een verzendactie wordt geactiveerd wanneer een gebruiker op de knop Verzenden tikt op een adaptief formulier. Met een verzendactie kunt u formuliergegevens opslaan in de lokale gegevensopslagruimte, formuliergegevens verzenden naar een REST-eindpunt, formuliergegevens verzenden als e-mail, enzovoort. Aangepaste formulieren bieden een paar extra verzendacties die buiten de box vallen. Zie voor meer informatie [De handeling Verzenden configureren](/help/forms/using/configuring-submit-actions.md).

Met de volgende stappen kunt u de handeling voor het verzenden van e-mail configureren en demo-verzendactie van het formulier configureren:

1. De e-mailserver configureren. Zie voor meer informatie [E-mailmelding configureren](/help/sites-administering/notification.md).


1. Selecteren **[!UICONTROL Form Container]** in de Inhoudsbrowser en selecteer ![cmppr](assets/cmppr.png). De eigenschappenbrowser wordt aan de linkerkant geopend.
1. Ga naar **[!UICONTROL Submission]** >  **[!UICONTROL Submit Action]**. Selecteer **[!UICONTROL Send Email]**. Geef de volgende waarden op en selecteer ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

   | Eigenschap | Waarde |
   |--- |--- |
   | Van | `donotreply@weretail.com` |
   | Naar | `${customer_Email}` |
   | Onderwerp | Bevestiging: je hebt verzendadres toegevoegd op de website We.Retail. |
   | E-mailsjabloon | Hallo `${customer_Name}`, Het volgende adres wordt toegevoegd als het verzendadres voor je account: <br>`${customer_Name}`, `${customer_Shipping_Address}`, `${customer_State}`, `${customer_ZIPCode}`<br> Met vriendelijke groeten, wij.Retail |
   | Bijlagen opnemen | Ingeschakeld |

   Uw formulier is klaar. U kunt nu een voorbeeld van het formulier bekijken en de functionaliteit testen. Als u de naam hebt gebruikt die in de zelfstudie wordt genoemd en als u het formulier hebt geopend op de computer waarop AEM [!DNL Forms] server, dan is het formulier beschikbaar op [http://localhost:4502/editor.html/content/forms/af/shipping-address-add-update-form.html](http://localhost:4502/editor.html/content/forms/af/shipping-address-add-update-form.html).

## Stap 5: Het adaptieve formulier voorvertonen en verzenden {#step-preview-and-submit-the-adaptive-form}

U kunt de **[!UICONTROL Preview option]** om de weergave en het gedrag van een formulier te evalueren. U kunt een formulier verzenden in de voorbeeldmodus en ook de validaties controleren die op een formulier zijn toegepast. Als bijvoorbeeld een fout wordt weergegeven wanneer een verplicht veld leeg blijft.

Aangepaste formulieren bieden ook een optie om een formulier voor verschillende apparaten te emuleren. Bijvoorbeeld iPhone, iPad en Desktop. U kunt beide gebruiken **[!UICONTROL Preview]** en **[!UICONTROL Emulator]** ![liniaal](assets/ruler.png) in combinatie met elkaar een voorbeeld van een formulier bekijken voor apparaten van verschillende schermgrootten.

1. Selecteer de **[!UICONTROL Preview]** aan de rechterkant van de formuliereditor. Het formulier wordt geopend in de voorbeeldmodus. Als u de in de zelfstudie vermelde naam hebt gebruikt, wordt een voorbeeld van de URL van het formulier weergegeven met [http://localhost:4502/content/dam/formsanddocuments/shipping-address-add-update-form/jcr:content?wcmmode=disabled](http://localhost:4502/content/dam/formsanddocuments/shipping-address-addition-updation-form/jcr:content?wcmmode=disabled)
1. Gebruiken ![liniaal](assets/ruler.png) om te zien hoe het formulier er op verschillende apparaten uitziet.
1. Vul velden van het formulier in en selecteer **[!UICONTROL Submit]**. Het formulier wordt verzonden en u wordt omgeleid naar de standaardversie **Bedankt** pagina. U kunt ook een aangepaste pagina voor bedankt opgeven. Zie voor meer informatie [Omleidingspagina configureren](/help/forms/using/configuring-redirect-page.md).

Het aangepaste formulier voor het toevoegen van een adres is gereed. Als u de in de zelfstudie vermelde naam hebt gebruikt en het formulier hebt geopend op de computer waarop de AEM Forms-server wordt uitgevoerd, is het formulier beschikbaar op [http://localhost:4502/editor.html/content/forms/af/shipping-address-add-update-form.html](http://localhost:4502/editor.html/content/forms/af/shipping-address-add-update-form.html).
