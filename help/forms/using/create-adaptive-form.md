---
title: '"Zelfstudie: Een adaptief formulier maken"'
seo-title: '"Een adaptief formulier maken"'
description: Leer een adaptief formulier te maken, in te delen en voor te vertonen. Leer ook verzendhandelingen te configureren.
seo-description: Leer een adaptief formulier te maken, in te delen en voor te vertonen. Leer ook verzendhandelingen te configureren.
page-status-flag: de-activated
uuid: 0010d274-a683-499e-9fa6-ce355d7898a0
discoiquuid: 55c08940-8c25-4938-8e49-25bce20aaf22
feature: Adaptive Forms
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '1341'
ht-degree: 1%

---


# Zelfstudie: Een adaptief formulier maken {#do-not-publish-tutorial-create-an-adaptive-form}

![02-create-adaptive-form-main-image](assets/02-create-adaptive-form-main-image.png)

Deze zelfstudie is een stap in de serie [Uw eerste adaptieve vorm maken](/help/forms/using/create-your-first-adaptive-form.md). U wordt aangeraden de reeks in chronologische volgorde te volgen om het volledige gebruik van de zelfstudie te begrijpen, uit te voeren en aan te tonen.

## Informatie over de zelfstudie {#about-the-tutorial}

Adaptieve formulieren zijn formulieren van de nieuwe generatie die dynamisch zijn en reageren. U kunt adaptieve formulieren gebruiken om persoonlijke ervaringen te bieden. U kunt ook adaptieve formulieren integreren met [!DNL Adobe Analytics] voor gebruiksstatistieken en [!DNL Adobe Campaign] voor campagnebeheer. Zie [Inleiding tot het ontwerpen van adaptieve formulieren](/help/forms/using/introduction-forms-authoring.md) voor meer informatie over adaptieve formuliermogelijkheden.

Het is eenvoudiger om formulieren te maken en te beheren wanneer een correct proces wordt gevolgd. In dit artikel leert u hoe u:

* [Een adaptief formulier maken waarmee een klant een verzendadres kan toevoegen](/help/forms/using/create-adaptive-form.md#step-create-the-adaptive-form)

* [Indelingsvelden van een adaptief formulier voor het weergeven en accepteren van informatie van een klant](/help/forms/using/create-adaptive-form.md#step-add-header-and-footer)

* [Verzendactie maken om een e-mail met formulierinhoud te verzenden](/help/forms/using/create-adaptive-form.md#step-add-components-to-capture-and-display-information)
* [Een adaptief formulier voorvertonen en verzenden](/help/forms/using/create-adaptive-form.md)

Aan het einde van het artikel hebt u een formulier dat vergelijkbaar is met het volgende:\
[![](do-not-localize/form-preview-mobile.gif)](do-not-localize/form-preview-mobile.gif)

## Stap 1: Het adaptieve formulier {#step-create-the-adaptive-form} maken

1. Meld u aan bij de AEM auteur en navigeer naar **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]**. De standaard-URL is [http://localhost:4502/aem/forms.html/content/dam/formsanddocuments](http://localhost:4502/aem/forms.html/content/dam/formsanddocuments).
1. Tik **[!UICONTROL Create]** en selecteer **[!UICONTROL Adaptive Form]**. Er verschijnt een optie voor het selecteren van een sjabloon. Tik op de sjabloon **[!UICONTROL Blank]** om deze te selecteren en **[!UICONTROL Next]** te tikken.

1. Er wordt een optie voor **[!UICONTROL Add Properties]** weergegeven. De velden **[!UICONTROL Title]** en **[!UICONTROL Name]** zijn verplicht:

   * **Titel:** Opgeven  `Add new or update shipping address` in het  **[!UICONTROL Title]** veld. In het titelveld wordt de weergavenaam van het formulier opgegeven. Met de titel kunt u het formulier identificeren in de AEM [!DNL Forms]-gebruikersinterface.
   * **Naam:** Opgeven  `shipping-address-add-update-form` in het  **[!UICONTROL Name]** veld. In het veld Naam wordt de naam van het formulier opgegeven. Er wordt een knooppunt met de opgegeven naam gemaakt in de repository. Wanneer u een titel begint te typen, wordt automatisch een waarde voor het naamveld gegenereerd. U kunt de voorgestelde waarde wijzigen. Het naamveld mag alleen alfanumerieke tekens, afbreekstreepjes en onderstrepingstekens bevatten. Alle ongeldige invoer wordt vervangen door een afbreekstreepje.

1. Tik op **[!UICONTROL Create]**. Er wordt een adaptief formulier gemaakt en er wordt een dialoogvenster weergegeven om het formulier te openen voor bewerking. Tik op **[!UICONTROL Open]** om het nieuwe formulier te openen op een nieuw tabblad. Het formulier wordt geopend voor bewerking. De zijbalk wordt ook weergegeven om het nieuwe formulier aan te passen aan de behoeften.

   Zie [Inleiding tot het ontwerpen van adaptieve formulieren](/help/forms/using/creating-adaptive-form.md) voor informatie over de adaptieve ontwerpinterface en de beschikbare componenten.

   ![nieuw aanpasbare vorm](assets/newly-created-adaptive-form.png)

## Stap 2: Kop- en voettekst {#step-add-header-and-footer} toevoegen

AEM [!DNL Forms] verstrekt vele componenten om informatie op een adaptief vorm te tonen. De componenten Koptekst en Voettekst geven een formulier een consistent uiterlijk. Een koptekst bevat doorgaans het logo van een bedrijf, de titel van het formulier en het overzicht. Een voettekst bevat doorgaans copyrightinformatie en koppelingen naar andere pagina&#39;s.

1. Tik ![in-/uitschakelen van zijpaneel](assets/toggle-side-panel.png) > ![treeexpandall](assets/treeexpandall.png). De componentbrowser wordt geopend. Sleep de **[!UICONTROL Header]** component van componentenbrowser aan de adaptieve vorm.
1. Tik op **[!UICONTROL Logo]**. De werkbalk wordt weergegeven. Tik ![aem_6_3_edit](assets/aem_6_3_edit.png) op de werkbalk, typ **We.Retail** en tik ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

1. Tik op de afbeelding. De werkbalk wordt weergegeven. Tik ![cmp](assets/cmppr.png). De eigenschappenbrowser wordt links van het scherm geopend. **[!UICONTROL Browse]** en uploadt u de logoafbeelding. Tik ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png). De afbeelding wordt in de koptekst weergegeven.

   Tik op Bestand ophalen om het logo te downloaden dat in dit artikel wordt gebruikt als u er geen hebt.

   [Bestand ophalen](assets/logo.png)

1. Sleep de **[!UICONTROL Footer]** component van ![treeexpandall](assets/treeexpandall.png) naar het adaptieve formulier. In dit stadium ziet het formulier er als volgt uit:

   ![adaptieve vorm met kop- en voetteksten](assets/adaptive-form-with-headers-and-footers.png)

## Stap 3: Componenten toevoegen voor het vastleggen en weergeven van informatie {#step-add-components-to-capture-and-display-information}

Componenten zijn bouwstenen van een adaptief formulier. AEM [!DNL Forms] verstrekt vele componenten om informatie in een adaptieve vorm te vangen en te tonen. U kunt de componenten van ![treeexpandall](assets/treeexpandall.png) aan een vorm slepen. Zie [Inleiding tot het ontwerpen van adaptieve formulieren](/help/forms/using/introduction-forms-authoring.md) voor meer informatie over beschikbare componenten en de bijbehorende functionaliteit.

1. Sleep de **[!UICONTROL Numeric Box component]** naar het aangepaste formulier. Plaats het voor de voettekstcomponent. Open eigenschappen van de component, wijzig **[!UICONTROL Title]** van de component in **`Customer ID`**, wijzig **[!UICONTROL Element Name]** in **`customer_ID`**, schakel de optie **[!UICONTROL Required Field]** in, schakel de optie **[!UICONTROL Use HTML5 Number Input Type]** in en tik ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).
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

1. Sleep een **[!UICONTROL Numeric Box]** component v????r de voettekstcomponent. Open eigenschappen van de component, stel waarden in die in de onderstaande tabel worden vermeld, en tik ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

   | Eigenschap | Waarde |
   |---|---|
   | Titel | Postcode |
   | Elementnaam | customer_ZIPCode |
   | Maximum aantal cijfers | 6 |
   | Vereist veld | Ingeschakeld |
   | Type weergavepatroon | Geen patroon |

1. Sleep een **[!UICONTROL Email]** component v????r de voettekstcomponent. Open eigenschappen van de component, stel waarden in die in de onderstaande tabel worden vermeld en tik ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

   | Eigenschap | Waarde |
   |---|---|
   | Titel | E-mail |
   | Elementnaam | customer_Email |
   | Vereist veld | Ingeschakeld |

1. Sleep een **[!UICONTROL File Attachment]** component v????r de voettekstcomponent. Open eigenschappen van de component, stel waarden in die in de onderstaande tabel worden vermeld en tik ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

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

1. Sleep een **[!UICONTROL Submit Button]** component aan de adaptieve vorm. Plaats het voor de voettekstcomponent. Open eigenschappen van de component, wijzig de elementnaam in `address_addition_update_submit`, tik ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png). De indeling van het formulier is voltooid en het formulier ziet er als volgt uit:

   ![adaptief-form-with-all-the-components](assets/adaptive-form-with-all-the-components.png)

## Stap 4: Verzendactie configureren voor het aangepaste formulier {#step-configure-submit-action-for-the-adaptive-form}

Een verzendactie wordt geactiveerd wanneer een gebruiker op de knop Verzenden tikt op een adaptief formulier. Met een verzendactie kunt u formuliergegevens opslaan in de lokale gegevensopslagruimte, formuliergegevens verzenden naar een REST-eindpunt, formuliergegevens verzenden als e-mail, enzovoort. Aangepaste formulieren bieden een paar extra verzendacties die buiten de box vallen. Voor gedetailleerde informatie, zie [Vormend de Submit actie](/help/forms/using/configuring-submit-actions.md).

Met de volgende stappen kunt u de handeling voor het verzenden van e-mail configureren en demo-verzendactie van het formulier configureren:

1. Configureer de e-mailserver. Zie [E-mailmelding configureren](/help/sites-administering/notification.md) voor meer informatie.


1. Tik **[!UICONTROL Form Container]** in de Inhoudsbrowser en tik ![cmpr](assets/cmppr.png). De eigenschappenbrowser wordt aan de linkerkant geopend.
1. Ga naar **[!UICONTROL Submission]** > **[!UICONTROL Submit Action]**. Selecteer **[!UICONTROL Send Email]**. Geef de volgende waarden op en tik ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

   | Eigenschap | Waarde |
   |--- |--- |
   | Van | `donotreply@weretail.com` |
   | Naar | `${customer_Email}` |
   | Subject | Bevestiging: Je hebt een verzendadres toegevoegd op de website We.Retail. |
   | E-mailsjabloon | Hallo `${customer_Name}`, het volgende adres wordt toegevoegd als het verzendadres voor uw account: <br>`${customer_Name}`, `${customer_Shipping_Address}`, `${customer_State}`, `${customer_ZIPCode}`<br> Regards, We.Retail |
   | Bijlagen opnemen | Ingeschakeld |

   Uw formulier is klaar. U kunt nu een voorbeeld van het formulier bekijken en de functionaliteit testen. Als u de naam gebruikt die in de zelfstudie wordt genoemd en het formulier opent op de computer waarop AEM [!DNL Forms]-server wordt uitgevoerd, is het formulier beschikbaar op [http://localhost:4502/editor.html/content/forms/af/shipping-address-add-update-form.html](http://localhost:4502/editor.html/content/forms/af/shipping-address-add-update-form.html).

## Stap 5: Het adaptieve formulier {#step-preview-and-submit-the-adaptive-form} voorvertonen en verzenden

Met de **[!UICONTROL Preview option]** kunt u de weergave en het gedrag van een formulier evalueren. U kunt een formulier verzenden in de voorbeeldmodus en ook de validaties controleren die op een formulier zijn toegepast. Als bijvoorbeeld een fout wordt weergegeven wanneer een verplicht veld leeg blijft.

Aangepaste formulieren bieden ook een optie om een formulier voor verschillende apparaten te emuleren. Bijvoorbeeld iPhone, iPad en Desktop. U kunt zowel de **[!UICONTROL Preview]**- als **[!UICONTROL Emulator]** ![liniaal](assets/ruler.png)-opties in combinatie met elkaar gebruiken om een voorbeeld van een formulier te bekijken voor apparaten met verschillende schermgrootten.

1. Tik op de optie **[!UICONTROL Preview]** aan de rechterkant van de formuliereditor. Het formulier wordt geopend in de voorbeeldmodus. Als u de naam hebt gebruikt die in de zelfstudie wordt vermeld, is de voorbeeld-URL van het formulier [http://localhost:4502/content/dam/formsanddocuments/shipping-address-add-update-form/jcr:content?wcmmode=disabled](http://localhost:4502/content/dam/formsanddocuments/shipping-address-addition-updation-form/jcr:content?wcmmode=disabled)
1. Met ![liniaal](assets/ruler.png) kunt u zien hoe het formulier er op verschillende apparaten uitziet.
1. Vul de velden van het formulier in en tik **[!UICONTROL Submit]**. Het formulier wordt verzonden en u wordt omgeleid naar de standaardpagina **Dankuwel**. U kunt ook een aangepaste pagina voor bedankt opgeven. Voor details, zie [Het vormen opnieuw richten pagina](/help/forms/using/configuring-redirect-page.md).

Het aangepaste formulier voor het toevoegen van een adres is gereed. Als u de naam gebruikt die in de zelfstudie wordt vermeld en het formulier opent op de computer waarop de AEM Forms-server wordt uitgevoerd, is het formulier beschikbaar op [http://localhost:4502/editor.html/content/forms/af/shipping-address-add-update-form.html](http://localhost:4502/editor.html/content/forms/af/shipping-address-add-update-form.html).
