---
title: 'Lesbestand: een adaptief formulier maken'
description: Leer een adaptief formulier te maken, in te delen en voor te vertonen. Leer ook verzendhandelingen te configureren.
feature: Adaptive Forms
exl-id: c0a2adcd-528a-41af-99b5-d8b423cd6605
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '1258'
ht-degree: 0%

---

# Lesbestand: een adaptief formulier maken {#do-not-publish-tutorial-create-an-adaptive-form}

![ 02-creeer-adaptief-vorm-main-beeld ](assets/02-create-adaptive-form-main-image.png)

Dit leerprogramma is een stap in [ creeert Uw Eerste AanpassingsVorm ](/help/forms/using/create-your-first-adaptive-form.md) reeksen. U wordt aangeraden de reeks in chronologische volgorde te volgen om het volledige gebruik van de zelfstudie te begrijpen, uit te voeren en aan te tonen.

## Over de zelfstudie {#about-the-tutorial}

Adaptieve formulieren zijn formulieren van de nieuwe generatie die dynamisch zijn en reageren. U kunt adaptieve formulieren gebruiken om persoonlijke ervaringen te bieden. U kunt ook adaptieve formulieren integreren met [!DNL Adobe Analytics] voor gebruiksstatistieken en [!DNL Adobe Campaign] voor campagnebeheer. Voor meer informatie over adaptieve vormmogelijkheden, zie [ Inleiding aan creatie adaptieve vormen ](/help/forms/using/introduction-forms-authoring.md).

Het is eenvoudiger om formulieren te maken en te beheren wanneer een correct proces wordt gevolgd. In dit artikel leert u hoe u:

* [ creeer een adaptieve vorm die een klant toestaat om een verzendend adres toe te voegen ](/help/forms/using/create-adaptive-form.md#step-create-the-adaptive-form)

* [ de gebieden van de Lay-out van een adaptieve vorm aan vertoning en keur informatie van een klant ](/help/forms/using/create-adaptive-form.md#step-add-header-and-footer) goed

* [Verzendactie maken om een e-mail met formulierinhoud te verzenden](/help/forms/using/create-adaptive-form.md#step-add-components-to-capture-and-display-information)
* [Een adaptief formulier voorvertonen en verzenden](/help/forms/using/create-adaptive-form.md)

Aan het einde van het artikel hebt u een formulier dat vergelijkbaar is met het volgende:\
[![ de voorproef van de Vorm in mobiele ](do-not-localize/form-preview-mobile.gif)](do-not-localize/form-preview-mobile.gif)

## Stap 1: Maak het adaptieve formulier {#step-create-the-adaptive-form}

1. Meld u aan bij de AEM auteur en navigeer naar **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]** . Het gebrek URL is [ http://localhost:4502/aem/forms.html/content/dam/formsanddocuments ](http://localhost:4502/aem/forms.html/content/dam/formsanddocuments).
1. Selecteer **[!UICONTROL Create]** en selecteer **[!UICONTROL Adaptive Form]** . Er verschijnt een optie voor het selecteren van een sjabloon. Selecteer de **[!UICONTROL Blank]** -sjabloon en selecteer **[!UICONTROL Next]** .

1. Er verschijnt een optie voor **[!UICONTROL Add Properties]** . De velden **[!UICONTROL Title]** en **[!UICONTROL Name]** zijn verplicht:

   * **Titel:** specificeer `Add new or update shipping address` op het **[!UICONTROL Title]** gebied. In het titelveld wordt de weergavenaam van het formulier opgegeven. Met de titel kunt u het formulier identificeren in de AEM gebruikersinterface van [!DNL Forms] .
   * **Naam:** specificeer `shipping-address-add-update-form` op het **[!UICONTROL Name]** gebied. In het veld Naam wordt de naam van het formulier opgegeven. Er wordt een knooppunt met de opgegeven naam gemaakt in de repository. Wanneer u een titel begint te typen, wordt automatisch een waarde voor het naamveld gegenereerd. U kunt de voorgestelde waarde wijzigen. Het naamveld mag alleen alfanumerieke tekens, afbreekstreepjes en onderstrepingstekens bevatten. Alle ongeldige invoer wordt vervangen door een afbreekstreepje.

1. Selecteer **[!UICONTROL Create]**. Er wordt een adaptief formulier gemaakt en er wordt een dialoogvenster weergegeven om het formulier te openen voor bewerking. Selecteer **[!UICONTROL Open]** om het nieuwe formulier op een nieuw tabblad te openen. Het formulier wordt geopend voor bewerking. De zijbalk wordt ook weergegeven om het nieuwe formulier aan te passen aan de behoeften.

   Voor informatie over adaptieve vorm auteursinterface en beschikbare componenten, zie [ Inleiding aan creatie adaptieve vormen ](/help/forms/using/creating-adaptive-form.md).

   ![ een pas gecreëerde adaptieve vorm.](assets/newly-created-adaptive-form.png)

## Stap 2: kop- en voettekst toevoegen {#step-add-header-and-footer}

AEM [!DNL Forms] biedt veel componenten om informatie weer te geven op een adaptief formulier. De componenten Koptekst en Voettekst geven een formulier een consistent uiterlijk. Een koptekst bevat doorgaans het logo van een bedrijf, de titel van het formulier en het overzicht. Een voettekst bevat doorgaans copyrightinformatie en koppelingen naar andere pagina&#39;s.

1. Selecteer ![ knevel-zij-paneel ](assets/toggle-side-panel.png) > ![ drievoudig ](assets/treeexpandall.png). De componentbrowser wordt geopend. Sleep de component **[!UICONTROL Header]** van de componentbrowser naar het aangepaste formulier.
1. Selecteer **[!UICONTROL Logo]**. De werkbalk wordt weergegeven. Selecteer ![ aem_6_3_edit ](assets/aem_6_3_edit.png) op de toolbar, type **Wij.Retail**, en selecteer ![ aem_6_3_forms_save ](assets/aem_6_3_forms_save.png).

1. Selecteer Afbeelding. De werkbalk wordt weergegeven. Selecteer ![ cmp ](assets/cmppr.png). De eigenschappenbrowser wordt links van het scherm geopend. **[!UICONTROL Browse]** en uploadt u de afbeelding van het logo. Selecteer ![ name_6_3_forms_save ](assets/aem_6_3_forms_save.png). De afbeelding wordt in de koptekst weergegeven.

   U kunt de optie Bestand ophalen selecteren om het logo te downloaden dat in dit artikel wordt gebruikt als u er geen hebt.

[Bestand ophalen](assets/logo.png)

1. Sleep de **[!UICONTROL Footer]** component van ![ drievoudig ](assets/treeexpandall.png) aan de adaptieve vorm. In dit stadium ziet het formulier er als volgt uit:

   ![ adaptive-form-with-headers-and-footers ](assets/adaptive-form-with-headers-and-footers.png)

## Stap 3: Voeg componenten toe aan het vastleggen en weergeven van informatie {#step-add-components-to-capture-and-display-information}

Componenten zijn bouwstenen van een adaptief formulier. AEM [!DNL Forms] biedt veel componenten om informatie in een adaptieve vorm vast te leggen en weer te geven. U kunt de componenten van ![ drievoudig ](assets/treeexpandall.png) aan een vorm slepen. Om over beschikbare componenten en overeenkomstige functionaliteit te leren, zie [ Inleiding aan auteursadaptieve vormen ](/help/forms/using/introduction-forms-authoring.md).

1. Sleep de **[!UICONTROL Numeric Box component]** naar het aangepaste formulier. Plaats het voor de voettekstcomponent. Open eigenschappen van de component, verander **[!UICONTROL Title]** van de component in **`Customer ID`**, verander **[!UICONTROL Element Name]** in **`customer_ID`**, laat de **[!UICONTROL Required Field]** optie toe, laat de **[!UICONTROL Use HTML5 Number Input Type]** optie toe, en selecteer ![ aem_6_3_forms_save ](assets/aem_6_3_forms_save.png).
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
      <td>Naam <br /> </td> 
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
      <td>Meerdere regels toestaan <br /> </td> 
      <td>Uitgeschakeld</td> 
      <td>Ingeschakeld</td> 
      <td>Uitgeschakeld</td> 
     </tr> 
    </tbody> 
   </table>

1. Sleep een component **[!UICONTROL Numeric Box]** vóór de voettekstcomponent. Open eigenschappen van de component, vastgestelde waarden die in de hieronder lijst, Uitgezochte ![ worden vermeld aem_6_3_forms_save ](assets/aem_6_3_forms_save.png).

   | Eigenschap | Waarde |
   |---|---|
   | Titel | Postcode |
   | Elementnaam | customer_ZIPCode |
   | Maximum aantal cijfers | 6 |
   | Vereist veld | Ingeschakeld |
   | Type weergavepatroon | Geen patroon |

1. Sleep een component **[!UICONTROL Email]** vóór de voettekstcomponent. Open eigenschappen van de component, plaats waarden die in de hieronder lijst worden vermeld, en selecteer ![ aem_6_3_forms_save ](assets/aem_6_3_forms_save.png).

   | Eigenschap | Waarde |
   |---|---|
   | Titel | E-mail |
   | Elementnaam | customer_Email |
   | Vereist veld | Ingeschakeld |

1. Sleep een component **[!UICONTROL File Attachment]** vóór de voettekstcomponent. Open eigenschappen van de component, plaats waarden die in de hieronder lijst worden vermeld, en selecteer ![ aem_6_3_forms_save ](assets/aem_6_3_forms_save.png).

   <table> 
    <tbody> 
     <tr> 
      <td><b>Eigenschap</b></td> 
      <td><b>Waarde</b></td> 
     </tr> 
     <tr> 
      <td>Titel</td> 
      <td>Door de overheid goedgekeurde adresbewijzen <br /> </td> 
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

1. Sleep een component **[!UICONTROL Submit Button]** naar het aangepaste formulier. Plaats het voor de voettekstcomponent. Open eigenschappen van de component, verander de Naam van het Element in `address_addition_update_submit`, uitgezocht ![ aem_6_3_forms_save ](assets/aem_6_3_forms_save.png). De indeling van het formulier is voltooid en het formulier ziet er als volgt uit:

   ![ adaptive-form-with-all-the-components ](assets/adaptive-form-with-all-the-components.png)

## Stap 4: de verzendactie voor het aangepaste formulier configureren {#step-configure-submit-action-for-the-adaptive-form}

Een verzendactie wordt geactiveerd wanneer een gebruiker op de knop Verzenden tikt op een adaptief formulier. Met een verzendactie kunt u formuliergegevens opslaan in de lokale gegevensopslagruimte, formuliergegevens verzenden naar een REST-eindpunt, formuliergegevens verzenden als e-mail, enzovoort. Aangepaste formulieren bieden een paar extra verzendacties die buiten de box vallen. Voor gedetailleerde informatie, zie [ Vormend de Submit actie ](/help/forms/using/configuring-submit-actions.md).

Met de volgende stappen kunt u de handeling voor het verzenden van e-mail configureren en demo-verzendactie van het formulier configureren:

1. De e-mailserver configureren. Voor details, zie [ Vormend E-mailBericht ](/help/sites-administering/notification.md).


1. Selecteer **[!UICONTROL Form Container]** in browser van de Inhoud en selecteer ![ cmp ](assets/cmppr.png). De eigenschappenbrowser wordt aan de linkerkant geopend.
1. Ga naar **[!UICONTROL Submission]** > **[!UICONTROL Submit Action]** . Selecteer **[!UICONTROL Send Email]**. Specificeer de volgende waarden en selecteer ![ aem_6_3_forms_save ](assets/aem_6_3_forms_save.png).

   | Eigenschap | Waarde |
   |--- |--- |
   | Van | `donotreply@weretail.com` |
   | Naar | `${customer_Email}` |
   | Onderwerp | Bevestiging: je hebt verzendadres toegevoegd op de website We.Retail. |
   | E-mailsjabloon | Hallo `${customer_Name}`, het volgende adres wordt toegevoegd als het verzendadres voor uw account: <br>`${customer_Name}`, `${customer_Shipping_Address}`, `${customer_State}`, `${customer_ZIPCode}`<br> Regards, We.Retail |
   | Bijlagen opnemen | Ingeschakeld |

   Uw formulier is klaar. U kunt nu een voorbeeld van het formulier bekijken en de functionaliteit testen. Als u de naam hebt gebruikt die op het leerprogramma wordt vermeld en tot de vorm op de machine toegang heeft die AEM [!DNL Forms] server in werking stelt, dan is de vorm beschikbaar in [ http://localhost:4502/editor.html/content/forms/af/shipping-address-add-update-form.html ](http://localhost:4502/editor.html/content/forms/af/shipping-address-add-update-form.html).

## Stap 5: Het adaptieve formulier voorvertonen en verzenden {#step-preview-and-submit-the-adaptive-form}

Met de **[!UICONTROL Preview option]** kunt u de weergave en het gedrag van een formulier evalueren. U kunt een formulier verzenden in de voorbeeldmodus en ook de validaties controleren die op een formulier zijn toegepast. Als bijvoorbeeld een fout wordt weergegeven wanneer een verplicht veld leeg blijft.

Aangepaste formulieren bieden ook een optie om een formulier voor verschillende apparaten te emuleren. Bijvoorbeeld iPhone, iPad en Desktop. U kunt zowel **[!UICONTROL Preview]** als **[!UICONTROL Emulator]** gebruiken ![ heerser ](assets/ruler.png) opties samen met elkaar om een vorm voor apparaten van verschillende het schermgrootte voor te vertonen.

1. Selecteer de optie **[!UICONTROL Preview]** aan de rechterkant van de formuliereditor. Het formulier wordt geopend in de voorbeeldmodus. Als u de naam gebruikt die op het leerprogramma wordt vermeld, dan voorproef URL van de vorm is [ http://localhost:4502/content/dam/formsanddocuments/shipping-address-add-update-form/jcr:content?wcmmode=disabled ](http://localhost:4502/content/dam/formsanddocuments/shipping-address-addition-updation-form/jcr:content?wcmmode=disabled)
1. Gebruik ![ heerser ](assets/ruler.png) om te bekijken hoe de vorm op diverse apparaten kijkt.
1. Vul velden van het formulier in en selecteer **[!UICONTROL Submit]** . De vorm wordt voorgelegd en u wordt opnieuw gericht aan gebrek **bedankt** pagina. U kunt ook een aangepaste pagina voor bedankt opgeven. Voor details, zie [ Vormend opnieuw richten pagina ](/help/forms/using/configuring-redirect-page.md).

Het aangepaste formulier voor het toevoegen van een adres is gereed. Als u de naam gebruikt die in het leerprogramma wordt vermeld en tot de vorm op de machine toegang heeft die de server van AEM Forms in werking stelt, dan is de vorm beschikbaar in [ http://localhost:4502/editor.html/content/forms/af/shipping-address-add-update-form.html ](http://localhost:4502/editor.html/content/forms/af/shipping-address-add-update-form.html).
