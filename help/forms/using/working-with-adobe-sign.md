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
feature: Adaptive Forms, Adobe Sign
translation-type: tm+mt
source-git-commit: 2e734041bdad7332c35ab41215069ee696f786f4
workflow-type: tm+mt
source-wordcount: '3661'
ht-degree: 0%

---


# Het gebruiken van [!DNL Adobe Sign] in een adaptieve vorm{#using-adobe-sign-in-an-adaptive-form}

[!DNL Adobe Sign] maakt workflows voor e-handtekeningen mogelijk voor adaptieve formulieren. E-handtekeningen verbeteren werkstromen om documenten voor wettig, verkoop, loonlijst, personeelsbeheer, en meer gebieden te verwerken.

In een standaard [!DNL Adobe Sign]- en adaptief-formulierscenario vult een gebruiker een adaptief formulier om een service aan te vragen. Een hypotheek- en creditcardaanvraag vereist bijvoorbeeld wettelijke handtekeningen van alle kredietnemers en medekredietnemers. Als u workflows voor elektronische handtekeningen wilt inschakelen voor vergelijkbare scenario&#39;s, kunt u [!DNL Adobe Sign] integreren met AEM [!DNL Forms]. Een paar andere voorbeelden zijn: u kunt [!DNL Adobe Sign] gebruiken om:

* Sluit overeenkomsten van om het even welk apparaat met volledig geautomatiseerde voorstel, citaat, en contractprocessen.
* Voltooi processen voor menselijke hulpbronnen sneller en geef uw werknemers de digitale ervaring.
* Verkort de duur van de contractcyclus en neem sneller aan boord van uw leveranciers.
* Maak digitale workflows waarmee algemene processen worden geautomatiseerd.

[!DNL Adobe Sign] integratie met AEM  [!DNL Forms] ondersteuning :

* Workflows voor ondertekening van enkelvoudige en meervoudige gebruikers
* Workflows voor opeenvolgende en gelijktijdige ondertekening
* In-form en out-of-form ondertekeningservaringen
* Formulieren ondertekenen als anonieme of aangemelde gebruiker
* Dynamische ondertekeningsprocessen (integratie met AEM [!DNL Forms]-workflow)
* Verificatie via een kennisbasis, telefoon en sociale profielen

Leer de [beste praktijken van het gebruiken van Adobe Sign met adaptieve vormen](https://medium.com/adobetech/using-adobe-sign-to-e-sign-an-adaptive-form-heres-the-best-way-to-do-it-dc3e15f9b684) om betere ondertekeningservaringen tot stand te brengen.

## Vereisten {#prerequisites}

Vóór gebruik van [!DNL Adobe Sign] in een adaptieve vorm:

* Zorg ervoor dat AEM [!DNL Forms] cloudservice is geconfigureerd voor gebruik van [!DNL Adobe Sign]. Zie [Adobe Sign integreren met AEM Forms](../../forms/using/adobe-sign-integration-adaptive-forms.md) voor meer informatie.
* Behoud de lijst met ondertekenaars klaar. U hebt voor elke ondertekenaar ten minste een e-mailadres nodig.

## [!DNL Adobe Sign] configureren voor een adaptief formulier {#configure-adobe-sign-for-an-adaptive-form}

Voer de volgende stappen uit om [!DNL Adobe Sign] voor een adaptief formulier te configureren:

1. [Aangepaste formuliereigenschappen bewerken voor Adobe-teken](../../forms/using/working-with-adobe-sign.md#enableadobesign)
1. [Adobe Sign-velden toevoegen aan een adaptief formulier](../../forms/using/working-with-adobe-sign.md#addadobesignfieldstoanadaptiveform)
1. [Adobe Sign inschakelen voor een adaptief formulier](../../forms/using/working-with-adobe-sign.md#enableadobsignforanadaptiveform)
1. [Adobe Sign-Cloud Service selecteren voor een adaptief formulier](../../forms/using/working-with-adobe-sign.md#selectadobesigncloudserviceforanadaptiveform)

1. [Adobe Sign-ondertekenaars toevoegen aan een adaptief formulier](../../forms/using/working-with-adobe-sign.md#addsignerstoanadaptiveform)
1. [Selecteer Handeling verzenden voor een adaptief formulier](../../forms/using/working-with-adobe-sign.md#selectsubmitactionforanadaptiveform)

![Details ondertekenaar](assets/signer_details_new.png)

### Aangepaste formuliereigenschappen bewerken voor [!DNL Adobe Sign] {#enableadobesign}

Configureer adaptieve formuliereigenschappen voor [!DNL Adobe Sign] voor een bestaand of een nieuw adaptief formulier.

[Maak een adaptief formulier voor Adobe ](../../forms/using/working-with-adobe-sign.md#create-an-adaptive-form-for-adobe-sign) Signing beschrijft de stappen voor het maken van een adaptief basisformulier. Zie [Een adaptief formulier maken](../../forms/using/creating-adaptive-form.md) voor andere opties die beschikbaar zijn wanneer u een adaptief formulier maakt.

#### Een adaptief formulier maken voor [!DNL Adobe Sign] {#create-an-adaptive-form-for-adobe-sign}

Voer de volgende stappen uit om een adaptief formulier te maken dat geschikt is voor ondertekenen:

1. Ga naar **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]**.
1. Tik **[!UICONTROL Create]** en selecteer **[!UICONTROL Adaptive Form]**. Er wordt een lijst met sjablonen weergegeven. Selecteer de sjabloon en tik **[!UICONTROL Next]**.
1. Op het tabblad **[!UICONTROL Basic]**:

   1. Geef **[!UICONTROL Name]** en **[!UICONTROL Title]** op voor het adaptieve formulier.

   1. Selecteer [configuratiecontainer](../../forms/using/adobe-sign-integration-adaptive-forms.md#configure-adobe-sign-with-aem-forms) gecreeerd terwijl het vormen [!DNL Adobe Sign] met AEM [!DNL Forms].

      >[!NOTE]
      >
      >De **[!UICONTROL Adobe Sign Cloud Service]** dropdown lijst toont de wolkendiensten die in de configuratiecontainer worden gevormd die u op dit gebied selecteert. De vervolgkeuzelijst **[!UICONTROL Adobe Sign Cloud Service]** is beschikbaar in de sectie **[!UICONTROL Electronic Signature]** van de adaptieve formuliereigenschappen wanneer u de optie **[!UICONTROL Enable Adobe Sign]** selecteert.

1. Selecteer op het tabblad **[!UICONTROL Form Model]** een van de volgende opties:

   * Selecteer de optie **[!UICONTROL Associate form template as the Document of Record template]** en selecteer een Document van het malplaatje van het Verslag. Als u een op een formuliersjabloon gebaseerd adaptief formulier gebruikt, worden alleen de velden weergegeven die zijn gebaseerd op de bijbehorende formuliersjabloon. Niet alle velden van het adaptieve formulier worden weergegeven.

   * Selecteer de optie **[!UICONTROL Generate Document of Record]**. Als u een adaptief formulier met de optie Document of Record gebruikt, worden in het document dat wordt verzonden voor ondertekening alle velden van het adaptieve formulier weergegeven.

1. Tik **[!UICONTROL Create.]** Er wordt een adaptief formulier voor gebarentaal gemaakt, dat kan worden gebruikt om [!DNL Adobe Sign] velden toe te voegen.

#### Een adaptief formulier bewerken voor [!DNL Adobe Sign] {#editafsign}

Voer de volgende stappen uit om [!DNL Adobe Sign] in een bestaande adaptieve vorm te gebruiken:

1. Ga naar **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]**.
1. Selecteer het adaptieve formulier en tik **[!UICONTROL Properties]**.
1. Selecteer op het tabblad **[!UICONTROL Basic]** de [configuratiecontainer](../../forms/using/adobe-sign-integration-adaptive-forms.md#configure-adobe-sign-with-aem-forms) die is gemaakt tijdens het configureren van [!DNL Adobe Sign] met AEM [!DNL Forms].
1. Selecteer op het tabblad **[!UICONTROL Form Model]** een van de volgende opties:

   * Selecteer de optie **[!UICONTROL Associate form template as the Document of Record template]** en selecteer een Document van het malplaatje van het Verslag. Als u een op een formuliersjabloon gebaseerd adaptief formulier gebruikt, worden alleen de velden weergegeven die zijn gebaseerd op de bijbehorende formuliersjabloon. Niet alle velden van het adaptieve formulier worden weergegeven.

   * Selecteer de optie **[!UICONTROL Generate Document of Record]**. Als u een adaptief formulier met de optie Document of Record gebruikt, worden in het document dat wordt verzonden voor ondertekening alle velden van het adaptieve formulier weergegeven.

1. Tik op **[!UICONTROL Save & Close]**. Het adaptieve formulier is ingeschakeld voor [!DNL Adobe Sign].

### Adobe Sign-velden toevoegen aan een adaptief formulier {#addadobesignfieldstoanadaptiveform}

[!DNL Adobe Sign] heeft verschillende velden die op een adaptief formulier kunnen worden geplaatst. Deze velden accepteren verschillende gegevenstypen, zoals handtekeningen, initialen, bedrijf of titel, en helpen bij het verzamelen van extra informatie tijdens het ondertekenen, samen met de handtekeningen. Met de component [!DNL Adobe Sign] Blok kunt u [!DNL Adobe Sign] velden op verschillende locaties in een adaptief formulier plaatsen.

Voer de volgende stappen uit om velden toe te voegen aan een adaptief formulier en verschillende opties aan te passen met betrekking tot deze velden:

1. Sleep **[!UICONTROL Adobe Sign Block]** component van componentenbrowser aan de adaptieve vorm. De [!DNL Adobe Sign] Blokcomponent heeft alle ondersteunde [!DNL Adobe Sign] velden. Standaard wordt het veld **Handtekening** toegevoegd aan het aangepaste formulier.

   ![Blok ondertekenen](assets/sign_block_new.png)

   Standaard is het blok [!DNL Adobe Sign] niet zichtbaar in het gepubliceerde adaptieve formulier. Deze is alleen zichtbaar in de ondertekenende documenten. U kunt de zichtbaarheid van [!DNL Adobe Sign] Blok wijzigen in de eigenschappen van de component [!DNL Adobe Sign] Blok.

   >[!NOTE]
   >
   >    * Het gebruik van [!DNL Adobe Sign]-blok is niet verplicht om [!DNL Adobe Sign] in een adaptieve vorm te gebruiken. Als u geen [!DNL Adobe Sign] blok gebruikt en gebieden voor de ondertekenaars toevoegt, dan wordt het standaardhandtekeningsgebied getoond bij de bodem van de het ondertekenen documenten.
   >    * Gebruik [!DNL Adobe Sign] alleen voor de adaptieve formulieren die automatisch Document of Record genereren. Als u een aangepaste XDP gebruikt voor het genereren van Document of een adaptief formulier op basis van een formuliersjabloon, wordt [!DNL Adobe Sign]-blok niet ondersteund.


1. Selecteer de **[!UICONTROL Adobe Sign Block]** component en tik **Edit** ![aem_6_3_edit](assets/aem_6_3_edit.png) pictogram. Er worden opties weergegeven voor het toevoegen van velden en het opmaken van de weergave van een veld.

   ![adobe-sign-block-select-fields](assets/adobe-sign-block-select-fields.png)

   **A.** Selecteer en voeg  [!DNL Adobe Sign] gebieden toe. **B.** Vouw het  [!DNL Adobe Sign] blok uit naar de volledige schermweergave

1. Tik op het pictogram **[!UICONTROL Adobe Sign]Veld** ![aem_6_3_adobesign](assets/aem_6_3_adobesign.png). Er worden opties weergegeven voor het selecteren en toevoegen van [!DNL Adobe Sign] velden.

   Vouw het vervolgkeuzeveld **[!UICONTROL Type]** uit om een [!DNL Adobe Sign]-veld te selecteren en tik op het pictogram Gereed ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png) om het geselecteerde veld toe te voegen aan [!DNL Adobe Sign]-blok. Het vervolgkeuzeveld **[!UICONTROL Type]** bevat de typen Handtekening, Ondertekenaarinformatie en Gegevensveld. [!DNL Adobe Sign] integratie met AEM  [!DNL Forms] steungebieden die in de  [!UICONTROL Type] drop-down doos slechts worden vermeld. Zie [Adobe Sign-documentatie](https://helpx.adobe.com/sign/help/field-types.html) voor gedetailleerde informatie over [!DNL Adobe Sign]-velden.

   ![adobe-sign-block-fields-options](assets/adobe-sign-block-fields-options.png)

   U moet een unieke naam opgeven voor een veld. U kunt ook de vereiste optie selecteren om een verplicht veld te markeren. Naast de opties **[!UICONTROL Name]** en **[!UICONTROL Required]**, hebben sommige [!DNL Adobe Sign] gebieden meer opties. Bijvoorbeeld masker en meerdere regels. Geef bovendien een unieke naam voor elk [!DNL Adobe Sign]-veld op of de velden zich in dezelfde of in andere [!DNL Adobe Sign]-blokken bevinden.

   Als u **[!UICONTROL Digital Signature]** selecteert in de vervolgkeuzelijst, kunt u digitale handtekeningen toepassen op het aangepaste formulier:

   * Online met cloudhandtekeningen voor ondertekening met een [digitale id](https://helpx.adobe.com/sign/kb/digital-certificate-providers.html) die wordt gehost door een vertrouwde serviceprovider.
   * Lokaal door het document te downloaden met Adobe Acrobat of Reader met een smartcard, USB-token of een op een bestand gebaseerde digitale id.

### [!DNL Adobe Sign] inschakelen voor een adaptief formulier {#enableadobsignforanadaptiveform}

Buiten het vak is [!DNL Adobe Sign] niet ingeschakeld voor een adaptief formulier. Voer de volgende stappen uit om het in te schakelen:

1. Tik in de Inhoudsbrowser op **[!UICONTROL Form Container]** en tik op het pictogram **[!UICONTROL Configure]** ![configure](assets/configure.png). De eigenschappenbrowser wordt geopend en de eigenschappen van de container Adaptief formulier worden weergegeven.
1. Vouw in de eigenschappenbrowser de accordeon **[!UICONTROL Electronic Signature]** uit en selecteer de optie **[!UICONTROL Enable Adobe Sign]**. Hiermee schakelt u [!DNL Adobe Sign] in voor een adaptief formulier.

### Selecteer [!DNL Adobe Sign] Cloud Service- en handtekeningvolgorde {#selectadobesigncloudserviceforanadaptiveform}

U kunt veelvoudige [!DNL Adobe Sign] diensten voor een geval van AEM [!DNL Forms] vormen. Het is raadzaam voor elke functie een aparte reeks diensten te hebben (Human Resource, Finance, enzovoort). Hierdoor kunt u ondertekende documenten gemakkelijker bijhouden en rapporteren. Een bank heeft bijvoorbeeld meerdere afdelingen. U kunt een afzonderlijke configuratie voor elke afdeling hebben voor het beter volgen van de documenten.

Een document kan ook meerdere ondertekenaars hebben. Een creditcardtoepassing kan bijvoorbeeld meerdere aanvragers hebben. Een bank vereist handtekeningen van alle aanvragers voordat de aanvraag wordt verwerkt. Voor scenario&#39;s met meerdere ondertekenaars kunt u ervoor kiezen het document in volgorde van opeenvolgende of gelijktijdige ondertekening te ondertekenen.

Voer de volgende stappen uit om een cloudservice en de volgorde van ondertekening te selecteren:

![cloudservice](assets/cloud-service.png)

1. Tik in de Inhoudsbrowser op **[!UICONTROL Form Container]** en tik op het pictogram **[!UICONTROL Configure]** ![configure](assets/configure.png). De eigenschappenbrowser wordt geopend en de eigenschappen van de container Adaptief formulier worden weergegeven.
1. Vouw in de eigenschappenbrowser de accordeon **[!UICONTROL Electronic Signature]** uit en selecteer de optie **[!UICONTROL Enable Adobe Sign]**. Hiermee schakelt u [!DNL Adobe Sign] in voor een adaptief formulier.
1. Selecteer een wolkendienst van de reeds gevormde lijst van [!DNL Adobe Sign] Cloud Services.

   Als de lijst **[!UICONTROL Adobe Sign Cloud Service]** leeg is, volgt [Adobe Sign configureren met AEM Forms](../../forms/using/adobe-sign-integration-adaptive-forms.md) artikel om de service te configureren.

   In het vervolgkeuzemenu worden de cloudservices weergegeven die in de map `global` in Gereedschappen > **[!UICONTROL Cloud Services]** > **[!UICONTROL Adobe Sign]** staan. Daarnaast bevat het vervolgkeuzemenu ook een lijst met de cloudservices die aanwezig zijn in de map die u selecteert in het veld **[!UICONTROL Configuration Container]** wanneer u een adaptief formulier maakt.

1. Selecteer de ondertekeningsvolgorde in het dialoogvenster **[!UICONTROL Signers can Sign]**. [!DNL Adobe Sign] zangers kunnen een adaptief formulier ondertekenen  **[!UICONTROL Sequentially]** - een na een andere ondertekenaar of  **[!UICONTROL Simultaneously]** - in willekeurige volgorde.

   Eén ondertekenaar ontvangt het formulier voor ondertekening achtereenvolgens in de volgorde. Nadat een ondertekenaar het ondertekenen van het document heeft voltooid, wordt het formulier verzonden naar de volgende ondertekenaar, enzovoort.

   Meerdere ondertekenaars kunnen tegelijkertijd een formulier ondertekenen.

1. [Voeg ondertekenaars toe aan een aangepast ](../../forms/using/working-with-adobe-sign.md#addsignerstoanadaptiveform) formulier en tik op het pictogram Done  ![aem_6_3_forms_](assets/aem_6_3_forms_save.png) saveicon om de wijzigingen op te slaan.


### Ondertekenaars toevoegen aan een adaptief formulier {#addsignerstoanadaptiveform}

U kunt slechts één ondertekenaar of meerdere ondertekenaars hebben voor een adaptief formulier. Wanneer u een ondertekenaar toevoegt, kunt u ook verificatiedetails voor de ondertekenaar configureren. U kunt ook selecteren of de invuller en zanger van het formulier dezelfde persoon zijn. Voer de volgende stappen uit om diverse details over een ondertekenaar toe te voegen en te verstrekken:

1. Tik in de Inhoudsbrowser op **[!UICONTROL Form Container]** en tik op het pictogram **[!UICONTROL Configure]** ![configure](assets/configure.png). De eigenschappenbrowser wordt geopend met de eigenschappen van de container Adaptief formulier.
1. Vouw in de eigenschappenbrowser de accordeon **[!UICONTROL Electronic Signature]** uit en selecteer de optie **[!UICONTROL Enable Adobe Sign]**. Hiermee schakelt u [!DNL Adobe Sign] in voor een adaptief formulier.
1. Tik **[!UICONTROL Add Signer]** onder **[!UICONTROL Signer Configuration]**. Er wordt een ondertekenaar toegevoegd aan het adaptieve formulier. U kunt meerdere [!DNL Adobe Sign] ondertekenaars toevoegen aan een adaptief formulier.
   ![telefoongegevens](assets/phone-details.png)

1. Klik op het pictogram **Bewerken** ![aem_6_3_edit](assets/aem_6_3_edit.png) om de volgende informatie over de ondertekenaar op te geven:

   * **[!UICONTROL Title]:** Geef een titel op om een ondertekenaar op unieke wijze te identificeren.

   * **[!UICONTROL Is the signer and the person filling the form same?]:** Selecteer  **Ja** als de invuller en de eerste ondertekenaar dezelfde persoon zijn. Als de optie is ingesteld op **Nee,**, gebruikt u de component voor de handtekeningstap niet in het adaptieve formulier. Als het formulier een component Handtekeningstap bevat, wordt het veld automatisch ingesteld op Ja.

   * **[!UICONTROL Signer Email address]:** Geef het e-mailadres van de ondertekenaar op. Ondertekenaar ontvangt om ondertekende documenten/formulier te zijn op het opgegeven e-mailadres. U kunt een e-mailadres gebruiken dat wordt opgegeven in een formulierveld, in AEM gebruikersprofiel van de aangemelde gebruiker, of handmatig een e-mailadres invoeren. Het is een verplichte stap. Zorg ervoor dat het e-mailadres van de eerste ondertekenaar of de enige ondertekenaar (in het geval van één ondertekenaar) niet hetzelfde is als het [!DNL Adobe Sign]-account dat wordt gebruikt om AEM-cloudservices te configureren.

   * **[!UICONTROL Signer Authentication Method]:** Geef de methode op voor het verifiëren van een gebruiker voordat u een formulier voor ondertekening opent. U kunt tussen telefoon, kennisbasis, en sociale op identiteit-gebaseerde authentificatie kiezen.
   >[!NOTE]
   >
   >    * Standaard biedt verificatie op basis van sociale identiteiten een optie voor verificatie via Facebook, Google en LinkedIn. U kunt contact opnemen met ondersteuning [!DNL Adobe Sign] om andere providers van sociale verificatie in te schakelen.


   * **[!DNL Adobe Sign]velden die moeten worden ingevuld of ondertekend:** Selecteer  [!DNL Adobe Sign] velden voor de ondertekenaar. Een adaptief formulier kan meerdere [!DNL Adobe Sign] velden hebben. U kunt specifieke velden inschakelen voor een ondertekenaar. In het veld worden alle beschikbare [!DNL Adobe Sign] blokken weergegeven. Wanneer u een blok selecteert, worden alle velden van het blok geselecteerd. U kunt het X-pictogram gebruiken om de selectie van een veld op te heffen.

   ![ondertekenaar-details](assets/signer-details.png)

   De bovenstaande afbeelding heeft twee voorbeelden [!DNL Adobe Sign] Blokken: Persoonlijke gegevens en kantoorgegevens

   Tik op het pictogram Gereed ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png). De ondertekenaar wordt toegevoegd en geconfigureerd.

### Selecteer Handeling verzenden voor een adaptief formulier {#selectsubmitactionforanadaptiveform}

Voeg vervolgens [!DNL Adobe Sign] velden toe aan een adaptief formulier, schakel [!DNL Adobe Sign] in vanuit de formuliercontainer, selecteer [!DNL Adobe Sign] Cloud Service en voeg [!DNL Adobe Sign] Ondertekenaars toe en selecteer een geschikte verzendactie voor het adaptieve formulier. Zie [De handeling Verzenden configureren](../../forms/using/configuring-submit-actions.md) voor gedetailleerde informatie over adaptieve formulieren die handelingen verzenden.

Bovendien wordt een adaptief formulier met [!DNL Adobe Sign] alleen verzonden nadat alle ondertekenaars het formulier hebben ondertekend. Gedeeltelijk ondertekend formulier vindt u in de sectie Ondertekenen in behandeling van de portal Formulieren. [!DNL Adobe Sign] De Dienst van de configuratie houdt het opiniepeilen  [!DNL Adobe Sign] server bij  [regelmatige ](../../forms/using/adobe-sign-integration-adaptive-forms.md) intervalstaties om de status van handtekeningen te verifiëren. Als alle ondertekenaars het ondertekenen van het formulier hebben voltooid, wordt de verzendactieservice gestart en wordt het formulier verzonden. Als u een aangepaste verzendactie gebruikt en het formulier [!DNL Adobe Sign] gebruikt, werkt u de aangepaste verzendactie bij om de verzendactieservice te gebruiken.

<!-- Remove when forms portal goes live
>[!NOTE]
>
>Data of the adaptive form is stored temporarily on Forms Portal. It is recommended to use [custom storage for Forms Portal](/help/forms/using/configuring-draft-submission-storage.md). It ensures that the PII (personally identifiable information) data is not stored on AEM servers. 
-->

Uw ervaring voor het ondertekenen van formulieren is gereed. U kunt een voorbeeld van het formulier bekijken om de ondertekeningservaring te verifiëren. Op het gepubliceerde formulier worden de velden [!DNL Adobe Sign] Blokkeren weergegeven wanneer een ondertekenaar het formulier ontvangt voor ondertekening via een e-mail. Deze ervaring wordt ook wel bekend als een ondertekeningservaring in de vorm van een out-of-form. U kunt ook een ondertekeningservaring in formulieren configureren voor de eerste ondertekenaar. Zie [In-form ondertekeningservaring maken](../../forms/using/working-with-adobe-sign.md#create-in-form-signing-experience) voor gedetailleerde stappen.

## Cloud-handtekeningen configureren voor een adaptief formulier {#configure-cloud-signatures-for-an-adaptive-form}

Digitale handtekeningen op basis van cloud of externe handtekeningen zijn een nieuwe generatie digitale handtekeningen die op verschillende computers, mobiele apparaten en het web werken en voldoen aan de hoogste standaarden en waarborgen voor ondertekenaarsverificatie. U kunt een adaptief formulier ondertekenen met digitale handtekeningen op basis van de cloud.

Nadat [adaptieve formuliereigenschappen voor Adobe sign](../../forms/using/working-with-adobe-sign.md#enableadobesign) is bewerkt, voert u de volgende stappen uit om een veld voor een cloudhandtekening toe te voegen aan een adaptief formulier:

1. Sleep **[!UICONTROL Adobe Sign Block]** component van componentenbrowser aan de adaptieve vorm. De [!UICONTROL Adobe Sign Block] component heeft alle gesteunde [!DNL Adobe Sign] gebieden. Standaard wordt het veld **[!UICONTROL Signature]** toegevoegd aan het aangepaste formulier.

   ![Blok ondertekenen](assets/sign-block-new.png)

1. Selecteer de **[!UICONTROL Adobe Sign Block]** component en tik **Edit** ![aem_6_3_edit](assets/aem_6_3_edit.png) pictogram. Er worden opties weergegeven voor het toevoegen van velden en het opmaken van de weergave van een veld.

   ![adobe-sign-block-select-fields](assets/adobe-sign-block-select-fields.png)

   **A.** Selecteer en voeg  [!DNL Adobe Sign] gebieden toe. **B.** Vouw het  [!DNL Adobe Sign] blok uit naar de volledige schermweergave

1. Tik op het pictogram **[!UICONTROL Adobe Sign Field]** ![aem_6_3_adobesign](assets/aem_6_3_adobesign.png). Er worden opties weergegeven voor het selecteren en toevoegen van [!DNL Adobe Sign] velden.

   Vouw het vervolgkeuzeveld **[!UICONTROL Type]** uit om **[!UICONTROL Digital Signature]** te selecteren en tik op het pictogram **Done** om het geselecteerde veld toe te voegen aan [!DNL Adobe Sign]-blok.

   ![Digitale handtekeningen](assets/digital_signatures_new.png)

   U moet een unieke naam opgeven voor een veld.

   Digitale handtekeningen toepassen op het adaptieve formulier met:

   * Wolkhandtekeningen: Onderteken met een [digitale id](https://helpx.adobe.com/sign/kb/digital-certificate-providers.html) die wordt gehost door een vertrouwde serviceprovider.
   * Adobe Acrobat of Reader: Download en open het document met Adobe Acrobat of Reader om het te ondertekenen met een smartcard, USB-token of een digitale id op basis van een bestand.

   Nadat u het handtekeningveld voor de cloud aan het adaptieve formulier hebt toegevoegd, voert u de volgende stappen uit om het configuratieproces te voltooien:

   * [Adobe Sign inschakelen voor een adaptief formulier](../../forms/using/working-with-adobe-sign.md#enableadobsignforanadaptiveform)
   * [Adobe Sign-Cloud Service selecteren voor een adaptief formulier](../../forms/using/working-with-adobe-sign.md#selectadobesigncloudserviceforanadaptiveform)
   * [Adobe Sign-ondertekenaars toevoegen aan een adaptief formulier](../../forms/using/working-with-adobe-sign.md#addsignerstoanadaptiveform)
   * [Selecteer Handeling verzenden voor een adaptief formulier](../../forms/using/working-with-adobe-sign.md#selectsubmitactionforanadaptiveform)


## Ondertekeningservaring in formulieren maken {#create-in-form-signing-experience}

Een gebruiker kan ook een adaptief formulier ondertekenen terwijl het formulier wordt ingevuld. Deze ervaring wordt ook wel &#39;in-form signing experience&#39; genoemd. De ondertekeningservaring in formulieren is alleen beschikbaar voor de eerste ondertekenaar in een omgeving met meerdere ondertekenaars. Voer de volgende stappen uit om een ondertekeningservaring in formulieren te maken voor een adaptief formulier:

1. [Voeg en vorm de component](../../forms/using/working-with-adobe-sign.md#add-and-configure-the-signature-step-component) van de Stap van de Handtekening toe.
1. [Voeg de component](../../forms/using/working-with-adobe-sign.md#configure-the-thank-you-page-or-summary-step-component) Samenvattingsstap toe.

![Ervaring voor in-form ondertekenen](assets/in_form_signing_experience_new.png)

### De component voor de stap Handtekening toevoegen en configureren {#add-and-configure-the-signature-step-component}

Gebruik de component Handtekeningstap om een gebied op te geven voor de elektronische ondertekening van het ingevulde formulier. Wanneer de sectie met de component Signature Step wordt weergegeven, wordt een ondertekenbare PDF-versie van het ingevulde formulier weergegeven. De component voor de stap Handtekening gebruikt de volledige breedte die beschikbaar is voor het formulier. Het wordt aanbevolen geen andere component op te nemen in de sectie die de component voor de stap Handtekening bevat.

Voer de volgende stappen uit om de component van de Stap van de Handtekening te vormen:

1. Sleep de component **[!UICONTROL Signature Step]** van de Componentbrowser naar het formulier.
1. Selecteer de zojuist toegevoegde component van de Handtekeningstap en tik **Configure** ![configure](assets/configure.png) pictogram. De eigenschappenbrowser wordt geopend en de eigenschappen voor stap Handtekening worden weergegeven. Configureer de volgende eigenschappen:

   * **[!UICONTROL Name]**: Geef de naam van de component op.

   * **[!UICONTROL Title]:** Geef de unieke titel van de component op.
   * **[!UICONTROL Template message]:** Geef het bericht op dat moet worden weergegeven terwijl de PDF van de handtekening wordt geladen. [!DNL Adobe Sign] Het voorbereiden en laden van PDF-handtekeningen duurt enige tijd.
   * **[!UICONTROL Signing Service]:** Selecteer de  **[!DNL Adobe Sign]** optie.

   * **[!UICONTROL Use legacy E-sign component]**: Als u het respectieve adaptieve formulier in de  [AEM Forms Workspace](../../forms/using/introduction-html-workspace.md), AEM  [!DNL Forms] app gebruikt of als het onderliggende adaptieve formulier een oudere e-sign component heeft, selecteert u de optie Oude E-sign  **component** gebruiken.

   * **[!UICONTROL Configuration]**: Selecteer een configuratie ([!DNL Adobe Sign] Cloud Service). De vervolgkeuzelijst is alleen beschikbaar als de optie **Use legacy E-sign component** is ingeschakeld.

   * **[!UICONTROL CSS Class]**: Geef de CSS-klasse voor de component op.

   Tik op het pictogram Gereed ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png) om de wijzigingen op te slaan.

   ![Handtekeningstap](assets/signature_step_new.png)

   >[!NOTE]
   >
   > * Wanneer u de **[!UICONTROL Signature Step]**-component naar het formulier sleept, wordt de optie **[!UICONTROL Is the signer and the person filling the form same?]** automatisch ingesteld op **Yes**. U moet het formulier blijven gebruiken.
      >
      > 
   * Gebruik de component Samenvattingsstap na de component Handtekeningstap voor een optimale ervaring. De stap Overzicht verzendt het formulier automatisch en direct nadat u het ondertekenen van een formulier hebt voltooid in de component Stap handtekening. Als u de summiere stap niet gebruikt, wordt een automatische voorlegging teweeggebracht slechts na het interval dat wordt geplaatst gebruikend [de Dienst van de Configuratie van Adobe Sign](../../forms/using/adobe-sign-integration-adaptive-forms.md#configure-adobe-sign-scheduler-to-sync-the-signing-status).
      > Enkele aanbevolen procedures zijn:
   > * Het deelvenster Adaptief formulier met de stap Handtekening bevindt zich altijd in het laatste of tweede laatste deelvenster van een adaptief formulier. Dit kan alleen het tweede laatste deelvenster zijn wanneer het laatste deelvenster de stap Overzicht bevat.
   > * Het deelvenster met de stapcomponent Handtekening of Samenvatting mag geen andere component bevatten.
   > * Adaptieve formulieren met de stap Handtekening kunnen niet worden verzonden.
   > * De verzending van de adaptieve formulieren met de stap Handtekening wordt afgehandeld via een achtergrondservice of de stap Samenvatting. Als er één geconfigureerde ondertekenaar is die het formulier ook invult, heeft de verwerking van het adaptieve formulier via de stap Samenvatting als voordeel dat deze direct evalueert dat de ondertekenaar het formulier heeft ondertekend en de actie Verzenden heeft geactiveerd. Een achtergrondservice heeft meer tijd nodig om te beoordelen of alle geconfigureerde ondertekenaars het formulier hebben ondertekend en de verzending van het adaptieve formulier vertragen.
   > * Ontwerp het formulier zodanig dat een gebruiker niet kan terugnavigeren vanuit een deelvenster dat de stap Handtekening of Overzicht bevat.



### De component {#configure-the-thank-you-page-or-summary-step-component} voor de pagina Hartelijk dank of de overzichtsstap configureren

Met de component **Summiere stap** wordt het formulier automatisch verzonden, wordt de informatie binnen de aangepaste overzichtspagina gevuld en wordt de samenvatting van het verzonden formulier weergegeven. Het krijgt ook de vereiste informatie in de terugkeerkaart. De component SummaryStep gebruikt de volledige breedte die beschikbaar is voor het formulier. Men adviseert om geen andere component op de sectie te hebben die de Summiere component van de Stap bevat.

De ervaring voor het ondertekenen van formulieren is nu gereed. U kunt een voorbeeld van het formulier bekijken om de ondertekeningservaring te verifiëren.

## Veelgestelde vragen {#frequently-asked-questions}

**Q:** U kunt een adaptief formulier insluiten in een ander adaptief formulier. Kan het ingesloten adaptieve formulier [!DNL Adobe Sign] ingeschakeld zijn?
**Ans:** Nee, AEM  [!DNL Forms] ondersteunt het gebruik van een adaptief formulier waarin een  [!DNL Adobe Sign] geschikt adaptief formulier voor ondertekening wordt ingesloten

**Q:** Wanneer ik een adaptief formulier maak met de geavanceerde sjabloon en dit open voor bewerking, wordt het foutbericht &quot;Elektronische handtekening of Ondertekenaars zijn niet correct geconfigureerd.&quot; wordt weergegeven. Hoe kan ik het foutbericht oplossen?
**Ans:** Adaptief formulier dat is gemaakt met de geavanceerde sjabloon is geconfigureerd voor gebruik  [!DNL Adobe Sign]. Als u de fout wilt verhelpen, maakt en selecteert u een [!DNL Adobe Sign]-cloudconfiguratie en configureert u een [!DNL Adobe Sign]-ondertekenaar voor het aangepaste formulier.

**V:** Kan ik  [!DNL Adobe Sign] tekstcodes gebruiken in een statische tekstcomponent van een adaptief formulier?
**Ans:** Ja, u kunt tekstmarkeringen in een tekstcomponent gebruiken om  [!DNL Adobe Sign] gebieden aan een  [Document van Verslag](../../forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md)  toe te voegen (Auto geproduceerde document van verslagoptie slechts) toegelaten adaptieve vorm. Zie [Adobe Sign Documentation](https://helpx.adobe.com/sign/using/text-tag.html) voor meer informatie over de procedure en regels voor het maken van een tekstcode. Houd er rekening mee dat adaptieve formulieren beperkte ondersteuning bieden voor tekstcodes. Met de tekstcodes kunt u alleen die velden maken die [Adobe Sign Block](../../forms/using/working-with-adobe-sign.md#configure-cloud-signatures-for-an-adaptive-form) ondersteunt.

**Q:** AEM  [!DNL Forms] verstrekt zowel  [!UICONTROL Adobe Sign block] als de stapcomponenten van de Handtekening. Kunnen deze gelijktijdig in een adaptieve vorm worden gebruikt?
**Ans:** U kunt beide componenten tegelijkertijd in een formulier gebruiken. Hier volgen enkele aanbevelingen voor het gebruik van deze componenten:

**Adobe Sign Block:** U kunt de velden gebruiken  [!UICONTROL Adobe Sign Block] om overal op het adaptieve formulier  [!UICONTROL Adobe Sign] velden toe te voegen. Het helpt ook om specifieke gebieden aan ondertekenaars toe te wijzen. Wanneer een adaptief formulier wordt voorvertoond of gepubliceerd [!UICONTROL Adobe Sign] Blok is standaard niet zichtbaar. Deze blokken zijn alleen beschikbaar in het ondertekenende document. In het ondertekenende document worden alleen de velden ingeschakeld die zijn toegewezen aan een ondertekenaar. [!UICONTROL Adobe Sign] blok kan met eerste en verdere ondertekenaars worden gebruikt.

**Ondertekeningsstap, component:** u kunt de component Handtekeningstap gebruiken om in formulieren te ondertekenen. Hiermee kan alleen de eerste ondertekenaar ondertekenen terwijl het formulier wordt ingevuld. Wanneer de sectie met de component Signature Step wordt weergegeven, wordt een ondertekenbare PDF-versie van het formulier weergegeven. Het is doorgaans de laatste of voorlaatste sectie, gevolgd door een overzichtscomponent van een formulier.

## Problemen oplossen {#troubleshoot}

### [!DNL Adobe Sign] fouten in overeenkomst  {#adobe-sign-agreement-failures}

****
IssueWhen  [!DNL Adobe Sign] service is configured for an adaptive form, the service failed to create an  [!DNL Adobe Sign] agreement for the onderliggende adaptive form.

**Resolutie**

* Controleer de [configuratie van de Adobe Sign-cloudservice](../../forms/using/adobe-sign-integration-adaptive-forms.md) die in het adaptieve formulier wordt gebruikt.
* Zorg ervoor dat de API-toepassing op de [!DNL Adobe Sign]-server die wordt gebruikt om de [!DNL Adobe Sign] Cloud-service te configureren, de vereiste machtigingen heeft.
* Als u meerdere [!DNL Adobe Sign] Cloud-services gebruikt, wijst u **[!UICONTROL oAuth URL]** van alle services naar dezelfde **[!UICONTROL Adobe Sign Shard]**.

* Gebruik afzonderlijke e-mailadressen om [!DNL Adobe Sign]-account en voor de eerste ondertekenaar en één ondertekenaar te configureren. Het e-mailadres van de eerste ondertekenaar of de enige ondertekenaar (in het geval van de enkele ondertekenaar) mag niet hetzelfde zijn als het [!DNL Adobe Sign]-account dat wordt gebruikt om AEM-cloudservices te configureren.

### AEM [!DNL Forms]-workflow geconfigureerd voor een [!DNL Adobe Sign]-compatibel adaptief formulier start {#adobe-sign-aem-form-workflow-failures} niet

****
ProbleemWanneer  [!DNL Adobe Sign] een adaptief formulier is geconfigureerd, wordt de workflow die met de optie Invoke  [!DNL Forms] Workflow is geconfigureerd, niet gestart.

**Resolutie**

* Wanneer u [!DNL Adobe Sign] zonder de stap van de Handtekening gebruikt of het formulier handtekeningen van meerdere personen vereist, wacht AEM [!DNL Forms] server tot de planner bevestigt dat alle personen het formulier hebben ondertekend. De planner dient het adaptieve formulier alleen in nadat alle persoon de ondertekening heeft voltooid en de workflow pas begint nadat het adaptieve formulier met succes is verzonden. U kunt het interval van [planner](adobe-sign-integration-adaptive-forms.md) verkorten om de status van het ondertekenen van formulieren met snelle intervallen te controleren en het verzenden van formulieren te versnellen.


## Verwante artikelen {#related-articles}

* [Adobe Sign integreren met AEM Forms](../../forms/using/adobe-sign-integration-adaptive-forms.md)
* [Aanbevolen procedures voor het gebruik van Adobe Sign met adaptieve formulieren](https://medium.com/adobetech/using-adobe-sign-to-e-sign-an-adaptive-form-heres-the-best-way-to-do-it-dc3e15f9b684)
* [Adobe Sign gebruiken met AEM Forms (video)](https://helpx.adobe.com/experience-manager/kt/forms/using/adobe-sign-integration-feature-video.html)
