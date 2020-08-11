---
title: Adobe Sign in een adaptieve vorm gebruiken
seo-title: Adobe Sign in een adaptieve vorm gebruiken
description: Workflows voor e-handtekeningen (Adobe Sign) inschakelen voor een adaptief formulier om ondertekeningsworkflows te automatiseren, processen met één en meerdere handtekeningen te vereenvoudigen en formulieren van mobiele apparaten elektronisch te ondertekenen.
seo-description: Workflows voor e-handtekeningen (Adobe Sign) inschakelen voor een adaptief formulier om ondertekeningsworkflows te automatiseren, processen met één en meerdere handtekeningen te vereenvoudigen en formulieren van mobiele apparaten elektronisch te ondertekenen.
uuid: cc3012ed-c318-4529-9adc-61aa5b5761a0
contentOwner: khsingh
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop
discoiquuid: f79828d8-2230-4477-8ffa-eeb6a0413acd
docset: aem65
translation-type: tm+mt
source-git-commit: e562ffe229543a1ee93467bcbc1a7be6c12927c6
workflow-type: tm+mt
source-wordcount: '3574'
ht-degree: 0%

---


# Adobe Sign in een adaptieve vorm gebruiken{#using-adobe-sign-in-an-adaptive-form}

Adobe Sign maakt workflows voor e-handtekeningen mogelijk voor adaptieve formulieren. E-handtekeningen verbeteren werkstromen om documenten voor wettig, verkoop, loonlijst, personeelsbeheer, en meer gebieden te verwerken.

In een standaard Adobe Sign- en adaptief formulierscenario vult een gebruiker een adaptief formulier om een service aan te vragen. Een hypotheek- en creditcardaanvraag vereist bijvoorbeeld wettelijke handtekeningen van alle kredietnemers en medekredietnemers. Als u workflows voor elektronische handtekeningen wilt inschakelen voor vergelijkbare scenario&#39;s, kunt u Adobe Sign integreren met AEM Forms. Een paar andere voorbeelden zijn:

* Sluit overeenkomsten van om het even welk apparaat met volledig geautomatiseerde voorstel, citaat, en contractprocessen.
* Voltooi processen voor menselijke hulpbronnen sneller en geef uw werknemers de digitale ervaring.
* Verkort de duur van de contractcyclus en neem sneller aan boord van uw leveranciers.
* Maak digitale workflows waarmee algemene processen worden geautomatiseerd.

Adobe Sign-integratie met AEM Forms ondersteunt:

* Workflows voor ondertekening van enkelvoudige en meervoudige gebruikers
* Workflows voor opeenvolgende en gelijktijdige ondertekening
* In-form en out-of-form ondertekeningservaringen
* Formulieren ondertekenen als anonieme of aangemelde gebruiker
* Dynamische ondertekeningsprocessen (integratie met AEM Forms-workflow)
* Verificatie via een kennisbasis, telefoon en sociale profielen

## Vereisten {#prerequisites}

Voordat u Adobe Sign in een adaptieve vorm gebruikt:

* Zorg ervoor dat de AEM Forms-cloudservice is geconfigureerd voor gebruik van Adobe Sign. Zie Adobe Sign [integreren met AEM Forms](../../forms/using/adobe-sign-integration-adaptive-forms.md)voor meer informatie.
* Behoud de lijst met ondertekenaars klaar. U hebt voor elke ondertekenaar ten minste een e-mailadres nodig.

## Adobe Sign configureren voor een adaptief formulier {#configure-adobe-sign-for-an-adaptive-form}

Voer de volgende stappen uit om Adobe Sign voor een adaptief formulier te configureren:

1. [Aangepaste formuliereigenschappen bewerken voor Adobe-teken](../../forms/using/working-with-adobe-sign.md#enableadobesign)
1. [Adobe Sign-velden toevoegen aan een adaptief formulier](../../forms/using/working-with-adobe-sign.md#addadobesignfieldstoanadaptiveform)
1. [Adobe Sign inschakelen voor een adaptief formulier](../../forms/using/working-with-adobe-sign.md#enableadobsignforanadaptiveform)
1. [Adobe Sign-Cloud Service selecteren voor een adaptief formulier](../../forms/using/working-with-adobe-sign.md#selectadobesigncloudserviceforanadaptiveform)

1. [Adobe Sign-ondertekenaars toevoegen aan een adaptief formulier](../../forms/using/working-with-adobe-sign.md#addsignerstoanadaptiveform)
1. [Selecteer Handeling verzenden voor een adaptief formulier](../../forms/using/working-with-adobe-sign.md#selectsubmitactionforanadaptiveform)

![Details ondertekenaar](assets/signer_details_new.png)

### Aangepaste formuliereigenschappen bewerken voor Adobe Sign {#enableadobesign}

Configureer adaptieve formuliereigenschappen voor Adobe Sign voor een bestaand of een nieuw adaptief formulier.

[Maak een adaptief formulier voor Adobe Sign](../../forms/using/working-with-adobe-sign.md#create-an-adaptive-form-for-adobe-sign) en beschrijf de stappen voor het maken van een adaptief basisformulier. Zie [Een adaptief formulier](../../forms/using/creating-adaptive-form.md) maken voor andere beschikbare opties terwijl u een adaptief formulier maakt.

#### Een adaptief formulier maken voor Adobe Sign {#create-an-adaptive-form-for-adobe-sign}

Voer de volgende stappen uit om een adaptief formulier te maken dat geschikt is voor ondertekenen:

1. Ga naar **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]**.
1. Tik **[!UICONTROL Create]** en selecteer **[!UICONTROL Adaptive Form]**. Er wordt een lijst met sjablonen weergegeven. Selecteer de sjabloon en tik op **[!UICONTROL Next]**.
1. Op het **[!UICONTROL Basic]** tabblad:

   1. Geef de **naam** en de **titel** op voor het adaptieve formulier.

   1. Selecteer de [configuratiecontainer](../../forms/using/adobe-sign-integration-adaptive-forms.md#configure-adobe-sign-with-aem-forms) die u hebt gemaakt tijdens het configureren van Adobe Sign met AEM Forms.

1. In the **[!UICONTROL Form Model]** tab, select one of the following options:

   * Selecteer de **[!UICONTROL Associate form template as the Document of Record template]** optie en selecteer een Document van het malplaatje van het Verslag. Als u een op een formuliersjabloon gebaseerd adaptief formulier gebruikt, worden alleen de velden weergegeven die zijn gebaseerd op de bijbehorende formuliersjabloon. Niet alle velden van het adaptieve formulier worden weergegeven.

   * Selecteer de **[!UICONTROL Generate Document of Record]** optie. Als u een adaptief formulier met de optie Document of Record gebruikt, worden in het document dat wordt verzonden voor ondertekening alle velden van het adaptieve formulier weergegeven.

1. Tik op **[!UICONTROL Create.]** een adaptief formulier voor gebarentaal dat u kunt gebruiken om Adobe Sign-velden toe te voegen.

#### Een adaptief formulier bewerken voor Adobe Sign {#editafsign}

Voer de volgende stappen uit om Adobe Sign in een bestaande adaptieve vorm te gebruiken:

1. Ga naar **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]**.
1. Selecteer het adaptieve formulier en tik op **[!UICONTROL Properties]**.
1. Selecteer op het **[!UICONTROL Basic]** tabblad de [configuratiecontainer](../../forms/using/adobe-sign-integration-adaptive-forms.md#configure-adobe-sign-with-aem-forms) die u hebt gemaakt tijdens de configuratie van Adobe Sign met AEM Forms.
1. In the **[!UICONTROL Form Mode]** tab, select one of the following options:

   * Selecteer de **[!UICONTROL Associate form template as the Document of Record template]** optie en selecteer een Document van het malplaatje van het Verslag. Als u een op een formuliersjabloon gebaseerd adaptief formulier gebruikt, worden alleen de velden weergegeven die zijn gebaseerd op de bijbehorende formuliersjabloon. Niet alle velden van het adaptieve formulier worden weergegeven.

   * Selecteer de **[!UICONTROL Generate Document of Record]** optie. Als u een adaptief formulier met de optie Document of Record gebruikt, worden in het document dat wordt verzonden voor ondertekening alle velden van het adaptieve formulier weergegeven.

1. Tik op **[!UICONTROL Save & Close]**. Het adaptieve formulier is ingeschakeld voor Adobe Sign.

### Adobe Sign-velden toevoegen aan een adaptief formulier {#addadobesignfieldstoanadaptiveform}

Adobe Sign heeft verschillende velden die op een adaptief formulier kunnen worden geplaatst. Deze velden accepteren verschillende gegevenstypen, zoals handtekeningen, initialen, bedrijf of titel, en helpen bij het verzamelen van extra informatie tijdens het ondertekenen, samen met de handtekeningen. Met de Adobe Sign Block-component kunt u Adobe Sign-velden op verschillende locaties in een adaptief formulier plaatsen.

Voer de volgende stappen uit om velden toe te voegen aan een adaptief formulier en verschillende opties aan te passen met betrekking tot deze velden:

1. Sleep de component **Adobe Sign Block** van de componentbrowser naar het aangepaste formulier. De Adobe Sign Block-component heeft alle ondersteunde Adobe Sign-velden. Standaard wordt een veld **Handtekening** toegevoegd aan het aangepaste formulier.

   ![Blok ondertekenen](assets/sign_block_new.png)

   Het Adobe Sign Block is standaard niet zichtbaar in het gepubliceerde adaptieve formulier. Deze is alleen zichtbaar in de ondertekenende documenten. U kunt de zichtbaarheid van Adobe Sign Block wijzigen vanuit de eigenschappen van de Adobe Sign Block-component.

   >[!NOTE]
   >
   >    * Het gebruik van een Adobe Sign-blok is niet verplicht om Adobe Sign in een adaptieve vorm te gebruiken. Als u geen Adobe Sign-blok gebruikt en geen velden toevoegt voor de ondertekenaars, wordt het standaardhandtekeningveld onder aan de ondertekenende documenten weergegeven.
   >    * Gebruik Adobe Sign-blok alleen voor aanvullende formulieren die automatisch Document of Record genereren. Als u een aangepaste XDP gebruikt voor het genereren van een Document of een op een formuliersjabloon gebaseerd adaptief formulier, is een Adobe Sign-blok niet vereist.


1. Selecteer de component **Adobe Sign Block** en tik op het pictogram **Edit** ![aem_6_3_edit](assets/aem_6_3_edit.png) . Er worden opties weergegeven voor het toevoegen van velden en het opmaken van de weergave van een veld.

   ![adobe-sign-block-select-fields](assets/adobe-sign-block-select-fields.png)

   **A.** Selecteer Adobe Sign-velden en voeg deze toe. **B.** Adobe Sign-blok uitbreiden naar volledige schermweergave

1. Tik op het pictogram **Adobe Sign-veld** ![aem_6_3_adobesign](assets/aem_6_3_adobesign.png) . Er worden opties weergegeven voor het selecteren en toevoegen van Adobe Sign-velden.

   Vouw het vervolgkeuzeveld **Type** uit om een Adobe Sign-veld te selecteren en tik op het pictogram Done ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png) om het geselecteerde veld toe te voegen aan het Adobe Sign-blok. Het vervolgkeuzeveld **Type** bevat de typen Handtekening, Ondertekenaarinformatie en Gegevensveld. Adobe Sign-integratie met AEM Forms-ondersteuningsvelden die alleen in de keuzelijst Type worden weergegeven. Raadpleeg de documentatie bij [Adobe Sign voor meer informatie over Adobe Sign-velden](https://helpx.adobe.com/sign/help/field-types.html).

   ![adobe-sign-block-fields-options](assets/adobe-sign-block-fields-options.png)

   U moet een unieke naam opgeven voor een veld. U kunt ook de vereiste optie selecteren om een verplicht veld te markeren. Naast de velden **Naam** en **** Vereiste hebben sommige velden van Adobe Sign meer opties. Bijvoorbeeld masker en meerdere regels. Geef bovendien voor elk Adobe Sign-veld een unieke naam, ongeacht of de velden zich in dezelfde of in verschillende Adobe Sign-blokken bevinden.

   Als u **Digitale handtekening** selecteert in de vervolgkeuzelijst, kunt u digitale handtekeningen toepassen op het adaptieve formulier:

   * Online met cloudhandtekeningen voor ondertekening met een [digitale id](https://helpx.adobe.com/sign/kb/digital-certificate-providers.html) die wordt gehost door een vertrouwde serviceprovider.
   * Lokaal door het document te downloaden met Adobe Acrobat of Reader met een smartcard, USB-token of een op een bestand gebaseerde digitale id.

### Adobe Sign inschakelen voor een adaptief formulier {#enableadobsignforanadaptiveform}

Adobe Sign is niet ingeschakeld voor een adaptief formulier. Voer de volgende stappen uit om het in te schakelen:

1. Tik in de browser Inhoud op **Formuliercontainer** en tik op het pictogram **Configureren** ![configureren](assets/configure.png) . De eigenschappenbrowser wordt geopend en de eigenschappen van de container Adaptief formulier worden weergegeven.
1. Vouw in de eigenschappenbrowser de accordeon **Elektronische handtekening** uit en selecteer de optie Adobe Sign **** inschakelen. Hiermee wordt Adobe Sign ingeschakeld voor een adaptief formulier.

### Adobe Sign-Cloud Service en -handtekeningvolgorde selecteren {#selectadobesigncloudserviceforanadaptiveform}

U kunt meerdere Adobe Sign-services configureren voor een exemplaar van AEM Forms. Het is raadzaam voor elke functie een aparte reeks diensten te hebben (Human Resources, Finance, enzovoort). Hierdoor wordt het bijhouden en rapporteren van ondertekende documenten eenvoudiger. Een bank heeft bijvoorbeeld meerdere afdelingen. U kunt een afzonderlijke configuratie voor elke afdeling hebben voor het beter volgen van de documenten.

Een document kan ook meerdere ondertekenaars hebben. Een creditcardtoepassing kan bijvoorbeeld meerdere aanvragers hebben. Een bank vereist handtekeningen van alle aanvragers voordat de aanvraag wordt verwerkt. Voor scenario&#39;s met meerdere ondertekenaars kunt u ervoor kiezen het document in volgorde van opeenvolgende of gelijktijdige ondertekening te ondertekenen.

Voer de volgende stappen uit om een cloudservice en de volgorde van ondertekening te selecteren:

![cloudservice](assets/cloud-service.png)

1. Tik in de browser Inhoud op **Formuliercontainer** en tik op het pictogram **Configureren** ![configureren](assets/configure.png) . De eigenschappenbrowser wordt geopend en de eigenschappen van de container Adaptief formulier worden weergegeven.
1. Vouw in de eigenschappenbrowser de accordeon **Elektronische handtekening** uit en selecteer de optie Adobe Sign **** inschakelen. Hiermee wordt Adobe Sign ingeschakeld voor een adaptief formulier.
1. Selecteer een cloudservice in de lijst met Adobe Sign-Cloud Services die al is geconfigureerd.

   Als de lijst van de Cloud Service **van** Adobe Sign leeg is, volg Adobe Sign met het artikel van AEM Forms [van de](../../forms/using/adobe-sign-integration-adaptive-forms.md) Vorm om de dienst te vormen.

1. Selecteer de handtekeningvolgorde in het dialoogvenster **Ondertekenaars kunnen ondertekenen** . Adobe Sign-zangers kunnen een adaptief formulier **opeenvolgend** ondertekenen - een voor een andere ondertekenaar of **tegelijkertijd** - in willekeurige volgorde.

   Eén ondertekenaar ontvangt het formulier voor ondertekening achtereenvolgens in de volgorde. Nadat een ondertekenaar het ondertekenen van het document heeft voltooid, wordt het formulier verzonden naar de volgende ondertekenaar, enzovoort.

   Meerdere ondertekenaars kunnen tegelijkertijd een formulier ondertekenen.

1. [Voeg ondertekenaars toe aan een adaptief formulier](../../forms/using/working-with-adobe-sign.md#addsignerstoanadaptiveform) en tik op het pictogram Done [aem_6_3_forms_save](assets/aem_6_3_forms_save.png) om de wijzigingen op te slaan.


### Ondertekenaars toevoegen aan een adaptief formulier {#addsignerstoanadaptiveform}

U kunt slechts één ondertekenaar of meerdere ondertekenaars hebben voor een adaptief formulier. Wanneer u een ondertekenaar toevoegt, kunt u ook verificatiedetails voor de ondertekenaar configureren. U kunt ook selecteren of de invuller en zanger van het formulier dezelfde persoon zijn. Voer de volgende stappen uit om diverse details over een ondertekenaar toe te voegen en te verstrekken:

1. Tik in de browser Inhoud op **Formuliercontainer** en tik op het pictogram **Configureren** ![configureren](assets/configure.png) . De eigenschappenbrowser wordt geopend met de eigenschappen van de container Adaptief formulier.
1. Vouw in de eigenschappenbrowser de accordeon **Elektronische handtekening** uit en selecteer de optie Adobe Sign **** inschakelen. Hiermee wordt Adobe Sign ingeschakeld voor een adaptief formulier.
1. Tik op Ondertekenaar **** toevoegen onder **Ondertekenaarconfiguratie**. Er wordt een ondertekenaar toegevoegd aan het adaptieve formulier. U kunt meerdere Adobe Sign-ondertekenaars toevoegen aan een adaptief formulier.
1. ![telefoongegevens](assets/phone-details.png)

   Klik op het pictogram **Aem_6_3_edit** _ ![](assets/aem_6_3_edit.png) om de volgende informatie over de ondertekenaar op te geven:

   * **Titel:** Geef een titel op om een ondertekenaar op unieke wijze te identificeren.

   * **Is de ondertekenaar en de persoon die het formulier invult hetzelfde?** Selecteer **Ja** als de invuller van het formulier en de eerste ondertekenaar dezelfde persoon zijn. Als de optie is ingesteld op **Nee,** gebruikt u de component voor de handtekeningstap niet in het adaptieve formulier. Als het formulier een component Handtekeningstap bevat, wordt het veld automatisch ingesteld op Ja.

   * **E-mailadres ondertekenaar:** Geef het e-mailadres van de ondertekenaar op. Ondertekenaar ontvangt om ondertekende documenten/formulier te zijn op het opgegeven e-mailadres. U kunt een e-mailadres gebruiken dat wordt opgegeven in een formulierveld, in AEM gebruikersprofiel van de aangemelde gebruiker, of handmatig een e-mailadres invoeren. Het is een verplichte stap. Zorg ervoor dat het e-mailadres van de eerste ondertekenaar of de enige ondertekenaar (in het geval van één ondertekenaar) niet hetzelfde is als het Adobe Sign-account dat wordt gebruikt om AEM-cloudservices te configureren.

   * **Verificatiemethode ondertekenaar:** Geef de methode op voor het verifiëren van een gebruiker voordat u een formulier voor ondertekening opent. U kunt tussen telefoon, kennisbasis, en sociale op identiteit-gebaseerde authentificatie kiezen.
   >[!NOTE]
   >
   >    * Standaard biedt verificatie op basis van sociale identiteiten een optie voor verificatie via Facebook, Google en LinkedIn. U kunt contact opnemen met Adobe Sign-ondersteuning om andere providers van sociale verificatie in te schakelen.


   * **Adobe Sign-velden die moeten worden ingevuld of ondertekend:** Selecteer Adobe Sign-velden voor de ondertekenaar. Een adaptief formulier kan meerdere Adobe Sign-velden hebben. U kunt specifieke velden inschakelen voor een ondertekenaar. In het veld worden alle beschikbare Adobe Sign-blokken weergegeven. Wanneer u een blok selecteert, worden alle velden van het blok geselecteerd. U kunt het X-pictogram gebruiken om de selectie van een veld op te heffen.

   ![ondertekenaar-details](assets/signer-details.png)

   De bovenstaande afbeelding heeft twee voorbeelden van Adobe Sign Blocks: Persoonlijke gegevens en kantoorgegevens

   Tik op het pictogram Done ![name_6_3_forms_save](assets/aem_6_3_forms_save.png) . De ondertekenaar wordt toegevoegd en geconfigureerd.

### Selecteer Handeling verzenden voor een adaptief formulier {#selectsubmitactionforanadaptiveform}

Nadat u Adobe Sign-velden hebt toegevoegd aan een adaptief formulier, Adobe Sign inschakelen vanuit formuliercontainer, Adobe Sign-Cloud Service selecteren en Adobe Sign-ondertekenaars toevoegen, selecteert u een geschikte verzendactie voor het adaptieve formulier. Zie De handeling Verzenden [configureren voor meer informatie over adaptieve formulieren die handelingen verzenden](../../forms/using/configuring-submit-actions.md).

Bovendien wordt een adaptief formulier dat geschikt is voor Adobe Sign alleen verzonden nadat alle ondertekenaars het formulier hebben ondertekend. Gedeeltelijk ondertekend formulier vindt u in de sectie Ondertekenen in behandeling van de portal Formulieren. Adobe Sign Configuration Service houdt regelmatig [](../../forms/using/adobe-sign-integration-adaptive-forms.md) opiniepeilingen over de Adobe Sign-server om de status van handtekeningen te controleren. Als alle ondertekenaars het ondertekenen van het formulier hebben voltooid, wordt de verzendactieservice gestart en wordt het formulier verzonden. Als u een aangepaste verzendactie gebruikt en het formulier Adobe Sign gebruikt, werkt u de aangepaste verzendactie bij om de verzendactieservice te gebruiken.

<!-- Remove when forms portal goes live
>[!NOTE]
>
>Data of the adaptive form is stored temporarily on Forms Portal. It is recommended to use [custom storage for Forms Portal](/help/forms/using/configuring-draft-submission-storage.md). It ensures that the PII (personally identifiable information) data is not stored on AEM servers. -->

Uw ervaring voor het ondertekenen van formulieren is gereed. U kunt een voorbeeld van het formulier bekijken om de ondertekeningservaring te verifiëren. Op het gepubliceerde formulier worden de velden Adobe Sign Block weergegeven wanneer een ondertekenaar het formulier voor ondertekening via een e-mail ontvangt. Deze ervaring wordt ook wel bekend als een ondertekeningservaring in de vorm van een out-of-form. U kunt ook een ondertekeningservaring in formulieren configureren voor de eerste ondertekenaar. Zie Ondertekening in formulieren [maken voor meer informatie](../../forms/using/working-with-adobe-sign.md#create-in-form-signing-experience).

## Cloud-handtekeningen configureren voor een adaptief formulier {#configure-cloud-signatures-for-an-adaptive-form}

Digitale handtekeningen op basis van cloud of externe handtekeningen zijn een nieuwe generatie digitale handtekeningen die op verschillende computers, mobiele apparaten en het web werken en voldoen aan de hoogste standaarden en waarborgen voor ondertekenaarsverificatie. U kunt een adaptief formulier ondertekenen met digitale handtekeningen op basis van de cloud.

Nadat u de adaptieve formuliereigenschappen voor Adobe-teken [hebt](../../forms/using/working-with-adobe-sign.md#enableadobesign)bewerkt, voert u de volgende stappen uit om het handtekeningveld voor de cloud toe te voegen aan een adaptief formulier:

1. Sleep de component **Adobe Sign Block** van de componentbrowser naar het aangepaste formulier. De Adobe Sign Block-component heeft alle ondersteunde Adobe Sign-velden. Standaard wordt een veld **Handtekening** toegevoegd aan het aangepaste formulier.

   ![Blok ondertekenen](assets/sign-block-new.png)

1. Selecteer de component **Adobe Sign Block** en tik op het pictogram **Edit** ![aem_6_3_edit](assets/aem_6_3_edit.png) . Er worden opties weergegeven voor het toevoegen van velden en het opmaken van de weergave van een veld.

   ![adobe-sign-block-select-fields](assets/adobe-sign-block-select-fields.png)

   **A.** Selecteer Adobe Sign-velden en voeg deze toe. **B.** Adobe Sign-blok uitbreiden naar volledige schermweergave

1. Tik op het pictogram **Adobe Sign-veld** ![aem_6_3_adobesign](assets/aem_6_3_adobesign.png) . Er worden opties weergegeven voor het selecteren en toevoegen van Adobe Sign-velden.

   Vouw het vervolgkeuzeveld **Type** uit om **Digitale handtekening** te selecteren en tik op het pictogram Done om het geselecteerde veld toe te voegen aan het Adobe Sign-blok.

   ![Digitale handtekeningen](assets/digital_signatures_new.png)

   U moet een unieke naam opgeven voor een veld.

   Digitale handtekeningen toepassen op het adaptieve formulier met:

   * Wolkhandtekeningen: Onderteken met een [digitale id](https://helpx.adobe.com/sign/kb/digital-certificate-providers.html) die wordt gehost door een vertrouwde serviceprovider.
   * Adobe Acrobat of Reader: Download en open het document met Adobe Acrobat of Reader om het te ondertekenen met behulp van een smartcard, USB-token of een op een bestand gebaseerde digitale id.

   Nadat u het handtekeningveld voor de cloud aan het adaptieve formulier hebt toegevoegd, voert u de volgende stappen uit om het configuratieproces te voltooien:

   * [Adobe Sign inschakelen voor een adaptief formulier](../../forms/using/working-with-adobe-sign.md#enableadobsignforanadaptiveform)
   * [Adobe Sign-Cloud Service selecteren voor een adaptief formulier](../../forms/using/working-with-adobe-sign.md#selectadobesigncloudserviceforanadaptiveform)
   * [Adobe Sign-ondertekenaars toevoegen aan een adaptief formulier](../../forms/using/working-with-adobe-sign.md#addsignerstoanadaptiveform)
   * [Selecteer Handeling verzenden voor een adaptief formulier](../../forms/using/working-with-adobe-sign.md#selectsubmitactionforanadaptiveform)


## Ervaring voor ondertekenen in formulieren maken {#create-in-form-signing-experience}

Een gebruiker kan ook een adaptief formulier ondertekenen terwijl het formulier wordt ingevuld. Deze ervaring wordt ook wel &#39;in-form signing experience&#39; genoemd. De ondertekeningservaring in formulieren is alleen beschikbaar voor de eerste ondertekenaar in een omgeving met meerdere ondertekenaars. Voer de volgende stappen uit om een ondertekeningservaring in formulieren te maken voor een adaptief formulier:

1. [Voeg en vorm de component](../../forms/using/working-with-adobe-sign.md#add-and-configure-the-signature-step-component)van de Stap van de Handtekening toe.
1. [Voeg de component](../../forms/using/working-with-adobe-sign.md#configure-the-thank-you-page-or-summary-step-component)Samenvattingsstap toe.

![Ervaring voor in-form ondertekenen](assets/in_form_signing_experience_new.png)

### De component voor de stap Handtekening toevoegen en configureren {#add-and-configure-the-signature-step-component}

Gebruik de component Handtekeningstap om een gebied op te geven voor de elektronische ondertekening van het ingevulde formulier. Wanneer de sectie met de component Signature Step wordt weergegeven, wordt een ondertekenbare PDF-versie van het ingevulde formulier weergegeven. De component voor de stap Handtekening gebruikt de volledige breedte die beschikbaar is voor het formulier. Het wordt aanbevolen geen andere component op te nemen in de sectie die de component voor de stap Handtekening bevat.

Voer de volgende stappen uit om de component van de Stap van de Handtekening te vormen:

1. Sleep de component **Handtekeningstap** van de browser Components naar het formulier.
1. Selecteer de zojuist toegevoegde component van de stap van de Handtekening en tik het **Configure** ![configure](assets/configure.png) pictogram. De eigenschappenbrowser wordt geopend en de eigenschappen voor stap Handtekening worden weergegeven. Configureer de volgende eigenschappen:

   * **Elementnaam**: Geef de naam van de component op.

   * **Titel:** Geef de unieke titel van de component op.
   * **Sjabloonbericht:** Geef het bericht op dat moet worden weergegeven wanneer de PDF van de handtekening wordt geladen. Het voorbereiden en laden van PDF-handtekeningen duurt enige tijd voor Adobe Sign-services.
   * **Ondertekeningsservice:** Selecteer de optie **Adobe Sign** .

   * **Verouderde E-sign component** gebruiken: Als u het respectievelijke adaptieve formulier gebruikt in de [AEM Forms Workspace](../../forms/using/introduction-html-workspace.md), de AEM Forms-app of als het onderliggende adaptieve formulier een oudere e-sign component heeft, selecteert u de optie **Oude E-sign component** gebruiken.

   * **Configuratie**: Selecteer een configuratie (Adobe Sign Cloud Service). De vervolgkeuzelijst is alleen beschikbaar als de optie **Oude E-sign component** gebruiken is ingeschakeld.

   Tik op het pictogram Done ![name_6_3_forms_save](assets/aem_6_3_forms_save.png) om de wijzigingen op te slaan.

   ![Handtekeningstap](assets/signature_step_new.png)

   >[!NOTE]
   >
   > * Wanneer u de **[!UICONTROL Signature Step]** component naar het formulier sleept, wordt de **[!UICONTROL Is the signer and the person filling the form same?]** optie automatisch ingesteld op **Ja**. U moet het formulier blijven gebruiken.
      >
      > 
   * Gebruik de component Samenvattingsstap na de component Handtekeningstap voor een optimale ervaring. De stap Overzicht verzendt het formulier automatisch en direct nadat u het ondertekenen van een formulier hebt voltooid in de component Stap handtekening. Als u de summiere stap niet gebruikt, wordt een automatische voorlegging teweeggebracht slechts na het interval dat wordt geplaatst gebruikend de Dienst [van de Configuratie van](../../forms/using/adobe-sign-integration-adaptive-forms.md#configure-adobe-sign-scheduler-to-sync-the-signing-status)Adobe Sign.
   > * Enkele aanbevolen procedures zijn:
   > * Het deelvenster Adaptief formulier met de stap Handtekening bevindt zich altijd in het laatste of tweede laatste deelvenster van een adaptief formulier. Dit kan alleen het tweede laatste deelvenster zijn wanneer het laatste deelvenster de stap Overzicht bevat.
   > * Het deelvenster met de stapcomponent Handtekening of Samenvatting mag geen andere component bevatten.
   > * Adaptieve formulieren met de stap Handtekening kunnen niet worden verzonden. De verzending wordt afgehandeld via een achtergrondservice of de stap Overzicht.
   > * Ontwerp het formulier zodanig dat een gebruiker niet kan terugnavigeren vanuit een deelvenster dat de stap Handtekening of Overzicht bevat.



### De component voor de prullenbak of overzichtsstap configureren {#configure-the-thank-you-page-or-summary-step-component}

De component **Samenvattingsstap** verzendt automatisch het formulier, vult de informatie in de aangepaste overzichtspagina in en geeft de samenvatting van het verzonden formulier weer. Het krijgt ook de vereiste informatie in de terugkeerkaart. De component SummaryStep gebruikt de volledige breedte die beschikbaar is voor het formulier. Men adviseert om geen andere component op de sectie te hebben die de Summiere component van de Stap bevat.

De ervaring voor het ondertekenen van formulieren is nu gereed. U kunt een voorbeeld van het formulier bekijken om de ondertekeningservaring te verifiëren.

## Veelgestelde vragen {#frequently-asked-questions}

**Ans:** Nee, AEM Forms biedt geen ondersteuning voor het gebruik van een adaptief formulier waarmee een adaptief formulier dat geschikt is voor Adobe Sign, wordt ingesloten voor ondertekening

**Ans:** Adaptief formulier dat is gemaakt met de geavanceerde sjabloon is geconfigureerd voor gebruik van Adobe Sign. U lost de fout op door een Adobe Sign-cloudconfiguratie te maken en te selecteren en een Adobe Sign-ondertekenaar voor het aangepaste formulier te configureren.

**Ans:** Ja, u kunt tekstcodes in een tekstcomponent gebruiken om Adobe Sign-velden toe te voegen aan een [Document of Record](../../forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md) (alleen automatisch gegenereerd document met de optie Opnemen) voor adaptief formulier. Zie [Adobe Sign-documentatie](https://helpx.adobe.com/sign/using/text-tag.html)voor meer informatie over de procedure en regels voor het maken van een tekstcode. Houd er rekening mee dat adaptieve formulieren beperkte ondersteuning bieden voor tekstcodes. Met de tekstcodes kunt u alleen die velden maken die [Adobe Sign Block](../../forms/using/working-with-adobe-sign.md#configure-cloud-signatures-for-an-adaptive-form) ondersteunt.

**Ans:** U kunt beide componenten tegelijkertijd in een formulier gebruiken. Hier volgen enkele aanbevelingen voor het gebruik van deze componenten:

**Adobe Sign-blok:** Met het Adobe Sign Block kunt u Adobe Sign-velden overal op het adaptieve formulier toevoegen. Het helpt ook om specifieke gebieden aan ondertekenaars toe te wijzen. Wanneer een adaptief formulier wordt voorvertoond of gepubliceerd, is Adobe Sign Block standaard niet zichtbaar. Deze blokken zijn alleen beschikbaar in het ondertekenende document. In het ondertekenende document worden alleen de velden ingeschakeld die zijn toegewezen aan een ondertekenaar. Adobe Sign-blok kan worden gebruikt met eerste en volgende ondertekenaars.

**Ondertekeningsstapcomponent:** U kunt de component voor het verzenden van handtekeningen gebruiken om in formulieren ondertekenen te maken. Hiermee kan alleen de eerste ondertekenaar ondertekenen terwijl het formulier wordt ingevuld. Wanneer de sectie met de component Signature Step wordt weergegeven, wordt een ondertekenbare PDF-versie van het formulier weergegeven. Het is doorgaans de laatste of voorlaatste sectie, gevolgd door een overzichtscomponent van een formulier.

## Problemen oplossen {#troubleshoot}

### Fouten in Adobe Sign-overeenkomst {#adobe-sign-agreement-failures}

**Probleem** Wanneer de Adobe Sign-service is geconfigureerd voor een adaptief formulier, kan de service geen Adobe Sign-overeenkomst maken voor het onderliggende adaptieve formulier.

**Resolutie**

* Controleer de [configuratie van de Adobe Sign-cloudservice](../../forms/using/adobe-sign-integration-adaptive-forms.md) die in het adaptieve formulier wordt gebruikt.
* Controleer of de rechten zijn vereist voor de API-toepassing op de Adobe Sign-server die wordt gebruikt om de Adobe Sign Cloud-service te configureren.
* Als u meerdere Adobe Sign Cloud-services gebruikt, wijst u de services **[!UICONTROL oAuth URL]** van alle services naar hetzelfde nummer **[!UICONTROL Adobe Sign Shard]**.

* Gebruik afzonderlijke e-mailadressen om Adobe Sign-account en voor de eerste ondertekenaar en de enkele ondertekenaar te configureren. Het e-mailadres van de eerste ondertekenaar of de enige ondertekenaar (in het geval van de enkele ondertekenaar) kan niet hetzelfde zijn als het Adobe Sign-account dat wordt gebruikt om AEM-cloudservices te configureren.

## Verwante artikelen {#related-articles}

* [Adobe Sign integreren met AEM Forms](../../forms/using/adobe-sign-integration-adaptive-forms.md)
* [Adobe Sign in een adaptieve vorm gebruiken](../../forms/using/working-with-adobe-sign.md)

* [Adobe Sign gebruiken met AEM Forms (video)
   ](https://helpx.adobe.com/experience-manager/kt/forms/using/adobe-sign-integration-feature-video.html)
