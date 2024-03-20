---
title: Adobe Sign in een adaptieve vorm gebruiken
description: Workflows voor e-handtekeningen (Adobe Sign) inschakelen voor een adaptief formulier om ondertekeningsworkflows te automatiseren, processen met één en meerdere handtekeningen te vereenvoudigen en formulieren van mobiele apparaten elektronisch te ondertekenen.
contentOwner: khsingh
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop
feature: Adaptive Forms, Foundation Components, Acrobat Sign
discoiquuid: f79828d8-2230-4477-8ffa-eeb6a0413acd
docset: aem65
exl-id: a8decba9-229d-40a2-992a-3cc8ebefdd6d
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '3673'
ht-degree: 0%

---

# Gebruiken [!DNL Adobe Sign] in een adaptieve vorm{#using-adobe-sign-in-an-adaptive-form}

<span class="preview"> Adobe beveelt aan moderne en uitbreidbare gegevensvastlegging te gebruiken [Kernonderdelen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html) for [nieuwe Adaptieve Forms maken](/help/forms/using/create-an-adaptive-form-core-components.md) of [Aangepaste Forms toevoegen aan AEM Sites-pagina&#39;s](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor de auteur Adaptive Forms die gebruikmaakt van stichtingscomponenten. </span>

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/use-adobe-sign/working-with-adobe-sign.html) |
| AEM 6,5 | Dit artikel |


[!DNL Adobe Sign] maakt workflows voor e-handtekeningen mogelijk voor adaptieve formulieren. E-handtekeningen verbeteren werkstromen om documenten voor wettig, verkoop, loonlijst, personeelsbeheer, en meer gebieden te verwerken.

Normaal [!DNL Adobe Sign] en het adaptieve formulierscenario, vult een gebruiker een adaptief formulier om een service aan te vragen. Een hypotheek- en creditcardaanvraag vereist bijvoorbeeld wettelijke handtekeningen van alle kredietnemers en medekredietnemers. Als u workflows voor elektronische handtekeningen wilt inschakelen voor vergelijkbare scenario&#39;s, kunt u [!DNL Adobe Sign] met AEM [!DNL Forms]. U kunt nog een paar voorbeelden gebruiken [!DNL Adobe Sign] tot:

* Sluit overeenkomsten van om het even welk apparaat met volledig geautomatiseerde voorstel, citaat, en contractprocessen.
* Voltooi processen voor menselijke hulpbronnen sneller en geef uw werknemers de digitale ervaring.
* Verkort de duur van de contractcyclus en neem sneller aan boord van uw leveranciers.
* Maak digitale workflows die algemene processen automatiseren.

[!DNL Adobe Sign] integratie met AEM [!DNL Forms] ondersteunt:

* Workflows voor ondertekening van enkelvoudige en meervoudige gebruikers
* Workflows voor opeenvolgende en gelijktijdige ondertekening
* Ondertekeningservaringen in formulieren en in formulieren
* Formulieren ondertekenen als anonieme of aangemelde gebruiker
* Dynamische ondertekeningsprocessen (integratie met AEM [!DNL Forms] workflow)
* Verificatie via een kennisbasis, telefoon en sociale profielen

Meer informatie over [Aanbevolen procedures voor het gebruik van Adobe Sign met adaptieve formulieren](https://medium.com/adobetech/using-adobe-sign-to-e-sign-an-adaptive-form-heres-the-best-way-to-do-it-dc3e15f9b684) om betere ondertekeningservaringen te maken.

## Vereisten {#prerequisites}

Voor gebruik [!DNL Adobe Sign] in adaptieve vorm:

* AEM [!DNL Forms] cloudservice is geconfigureerd voor gebruik [!DNL Adobe Sign]. Zie voor meer informatie [Adobe Sign integreren met AEM Forms](../../forms/using/adobe-sign-integration-adaptive-forms.md).
* Behoud de lijst met ondertekenaars klaar. U hebt voor elke ondertekenaar ten minste een e-mailadres nodig.

## Configureren [!DNL Adobe Sign] voor een adaptief formulier {#configure-adobe-sign-for-an-adaptive-form}

Voer de volgende stappen uit om te vormen [!DNL Adobe Sign] voor een adaptief formulier:

1. [Aangepaste formuliereigenschappen bewerken voor Adobe ondertekenen](../../forms/using/working-with-adobe-sign.md#enableadobesign)
1. [Adobe Sign-velden toevoegen aan een adaptief formulier](../../forms/using/working-with-adobe-sign.md#addadobesignfieldstoanadaptiveform)
1. [Adobe Sign inschakelen voor een adaptief formulier](../../forms/using/working-with-adobe-sign.md#enableadobsignforanadaptiveform)
1. [Selecteer Adobe Sign Cloud Service voor een adaptief formulier](../../forms/using/working-with-adobe-sign.md#selectadobesigncloudserviceforanadaptiveform)

1. [Adobe Sign-ondertekenaars toevoegen aan een adaptief formulier](../../forms/using/working-with-adobe-sign.md#addsignerstoanadaptiveform)
1. [Selecteer Handeling verzenden voor een adaptief formulier](../../forms/using/working-with-adobe-sign.md#selectsubmitactionforanadaptiveform)

![Details ondertekenaar](assets/signer_details_new.png)

### Aangepaste formuliereigenschappen bewerken voor [!DNL Adobe Sign] {#enableadobesign}

Aangepaste formuliereigenschappen configureren voor [!DNL Adobe Sign] voor een bestaand of een nieuw adaptief formulier.

[Een adaptief formulier maken voor Adobe Sign](../../forms/using/working-with-adobe-sign.md#create-an-adaptive-form-for-adobe-sign) beschrijft de stappen voor het maken van een adaptief basisformulier. Zie [Een adaptief formulier maken](../../forms/using/creating-adaptive-form.md) voor andere opties beschikbaar wanneer u een adaptief formulier maakt.

#### Een adaptief formulier maken voor [!DNL Adobe Sign] {#create-an-adaptive-form-for-adobe-sign}

Voer de volgende stappen uit om een adaptief formulier te maken dat geschikt is voor ondertekenen:

1. Navigeren naar **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]**.
1. Selecteren **[!UICONTROL Create]** en selecteert u **[!UICONTROL Adaptive Form]**. Er wordt een lijst met sjablonen weergegeven. Selecteer de sjabloon en selecteer **[!UICONTROL Next]**.
1. In de **[!UICONTROL Basic]** tab:

   1. Geef de **[!UICONTROL Name]** en **[!UICONTROL Title]** voor het adaptieve formulier.

   1. Selecteer de [configuratieconsole](../../forms/using/adobe-sign-integration-adaptive-forms.md#configure-adobe-sign-with-aem-forms) gemaakt tijdens configureren [!DNL Adobe Sign] met AEM [!DNL Forms].

      >[!NOTE]
      >
      >De **[!UICONTROL Adobe Sign Cloud Service]** in de vervolgkeuzelijst worden de cloudservices weergegeven die zijn geconfigureerd in de configuratiecontainer die u in dit veld selecteert. De **[!UICONTROL Adobe Sign Cloud Service]** de vervolgkeuzelijst is beschikbaar in het dialoogvenster **[!UICONTROL Electronic Signature]** van de adaptieve formuliereigenschappen wanneer u de optie **[!UICONTROL Enable Adobe Sign]** -optie.

1. In de **[!UICONTROL Form Model]** selecteert u een van de volgende opties:

   * Selecteer de **[!UICONTROL Associate form template as the Document of Record template]** en selecteert u een Document of Record-sjabloon. Als u een op een formuliersjabloon gebaseerd adaptief formulier gebruikt, worden alleen de velden weergegeven die zijn gebaseerd op de bijbehorende formuliersjabloon. Niet alle velden van het adaptieve formulier worden weergegeven.

   * Selecteer de **[!UICONTROL Generate Document of Record]** -optie. Als u een adaptief formulier met de optie Document of Record gebruikt, worden in het document dat wordt verzonden voor ondertekening alle velden van het adaptieve formulier weergegeven.

1. Selecteren **[!UICONTROL Create.]** Er wordt een adaptief formulier gemaakt dat geschikt is voor ondertekenen en dat kan worden gebruikt voor het toevoegen van [!DNL Adobe Sign] velden.

#### Een adaptief formulier bewerken voor [!DNL Adobe Sign] {#editafsign}

Voer de volgende stappen uit om te gebruiken [!DNL Adobe Sign] in een bestaande adaptieve vorm:

1. Navigeren naar **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]**.
1. Selecteer het aangepaste formulier en selecteer **[!UICONTROL Properties]**.
1. In de **[!UICONTROL Basic]** selecteert u de [configuratieconsole](../../forms/using/adobe-sign-integration-adaptive-forms.md#configure-adobe-sign-with-aem-forms) gemaakt tijdens configureren [!DNL Adobe Sign] met AEM [!DNL Forms].
1. In de **[!UICONTROL Form Model]** selecteert u een van de volgende opties:

   * Selecteer de **[!UICONTROL Associate form template as the Document of Record template]** en selecteert u een Document of Record-sjabloon. Als u een op een formuliersjabloon gebaseerd adaptief formulier gebruikt, worden alleen de velden weergegeven die zijn gebaseerd op de bijbehorende formuliersjabloon. Niet alle velden van het adaptieve formulier worden weergegeven.

   * Selecteer de **[!UICONTROL Generate Document of Record]** -optie. Als u een adaptief formulier met de optie Document of Record gebruikt, worden in het document dat wordt verzonden voor ondertekening alle velden van het adaptieve formulier weergegeven.

1. Selecteer **[!UICONTROL Save & Close]**. Het adaptieve formulier is ingeschakeld voor [!DNL Adobe Sign].

### Adobe Sign-velden toevoegen aan een adaptief formulier {#addadobesignfieldstoanadaptiveform}

[!DNL Adobe Sign] heeft verschillende velden die op een adaptief formulier kunnen worden geplaatst. Deze velden accepteren verschillende gegevenstypen, zoals handtekeningen, initialen, bedrijf of titel, en helpen bij het verzamelen van extra informatie tijdens het ondertekenen, samen met de handtekeningen. U kunt de [!DNL Adobe Sign] Component blokkeren om te plaatsen [!DNL Adobe Sign] velden op verschillende locaties in een adaptief formulier.

Voer de volgende stappen uit om velden toe te voegen aan een adaptief formulier en verschillende opties aan te passen met betrekking tot deze velden:

1. Slepen en neerzetten **[!UICONTROL Adobe Sign Block]** van de deelbrowser naar het aangepaste formulier. De [!DNL Adobe Sign] De component Block bevat alle ondersteunde [!DNL Adobe Sign] velden. Standaard wordt een **Handtekening** aan het adaptieve formulier.

   ![Blok ondertekenen](assets/sign_block_new.png)

   Standaard worden de [!DNL Adobe Sign] Blok is niet zichtbaar in het gepubliceerde adaptieve formulier. Deze is alleen zichtbaar in de ondertekenende documenten. U kunt de zichtbaarheid van [!DNL Adobe Sign] Blok van de eigenschappen van de [!DNL Adobe Sign] De component Blok.

   >[!NOTE]
   >
   >    * Gebruiken [!DNL Adobe Sign] blok is niet verplicht [!DNL Adobe Sign] in een adaptieve vorm. Als u het niet gebruikt [!DNL Adobe Sign] blok en voeg gebieden voor de ondertekenaars toe, dan wordt het standaardhandtekeningsgebied getoond bij de bodem van de het ondertekenen documenten.
   >    * Gebruiken [!DNL Adobe Sign] alleen blokkeren voor de adaptieve formulieren die automatisch een Document of Record genereren. Als u een aangepaste XDP gebruikt voor het genereren van het Document of een op een formuliersjabloon gebaseerd adaptief formulier, [!DNL Adobe Sign] blok wordt niet ondersteund.
   >
   >

1. Selecteer de **[!UICONTROL Adobe Sign Block]** en selecteert u de **Bewerken** ![aem_6_3_edit](assets/aem_6_3_edit.png) pictogram. Er worden opties weergegeven voor het toevoegen van velden en het opmaken van de weergave van een veld.

   ![adobe-sign-block-select-fields](assets/adobe-sign-block-select-fields.png)

   **A.** Selecteren en toevoegen [!DNL Adobe Sign] velden. **B.** Breid uit [!DNL Adobe Sign] blokkeren naar volledige schermweergave

1. Selecteer de **[!UICONTROL Adobe Sign]Veld** ![aem_6_3_adobesign](assets/aem_6_3_adobesign.png) pictogram. Er worden opties weergegeven om te selecteren en toe te voegen [!DNL Adobe Sign] velden.

   Breid uit **[!UICONTROL Type]** vervolgkeuzeveld om een [!DNL Adobe Sign] en selecteer Gereed ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png) pictogram om het geselecteerde veld toe te voegen aan [!DNL Adobe Sign] blokkeren. De **[!UICONTROL Type]** Het vervolgkeuzeveld bevat de typen Handtekening, Ondertekenaarinformatie en Gegevensveld. [!DNL Adobe Sign] integratie met AEM [!DNL Forms] ondersteuningsvelden die worden vermeld in het dialoogvenster [!UICONTROL Type] alleen vervolgkeuzelijst. Voor gedetailleerde informatie over [!DNL Adobe Sign] velden, zie [Adobe Sign-documentatie](https://helpx.adobe.com/sign/help/field-types.html).

   ![adobe-sign-block-fields-options](assets/adobe-sign-block-fields-options.png)

   U moet een unieke naam opgeven voor een veld. U kunt ook de vereiste optie selecteren om een verplicht veld te markeren. Naast de **[!UICONTROL Name]** en **[!UICONTROL Required]** optie, sommige [!DNL Adobe Sign] veld bevat meer opties. Bijvoorbeeld masker en meerdere regels. Geef bovendien een unieke naam voor elke [!DNL Adobe Sign] veld of de velden zich in hetzelfde of een ander veld bevinden [!DNL Adobe Sign] blokken.

   Als u **[!UICONTROL Digital Signature]** in de vervolgkeuzelijst kunt u digitale handtekeningen toepassen op het adaptieve formulier:

   * Online met cloudhandtekeningen voor ondertekening met een [digitale id](https://helpx.adobe.com/sign/kb/digital-certificate-providers.html) gehost door een vertrouwde serviceprovider.
   * Lokaal door het document te downloaden met Adobe Acrobat of Reader met een smartcard, USB-token of een op een bestand gebaseerde digitale id.

### Inschakelen [!DNL Adobe Sign] voor een adaptief formulier {#enableadobsignforanadaptiveform}

Uit de doos, [!DNL Adobe Sign] is niet ingeschakeld voor een adaptief formulier. Voer de volgende stappen uit om het in te schakelen:

1. Selecteer in de inhoudbrowser de optie **[!UICONTROL Form Container]** en selecteert u de **[!UICONTROL Configure]** ![vormen](assets/configure.png) pictogram. De eigenschappenbrowser wordt geopend en de eigenschappen van de container Adaptief formulier worden weergegeven.
1. Vouw in de eigenschappenbrowser de optie **[!UICONTROL Electronic Signature]** en selecteert u de **[!UICONTROL Enable Adobe Sign]** -optie. Het maakt [!DNL Adobe Sign] voor een adaptief formulier.

### Selecteren [!DNL Adobe Sign] Cloud Service en handtekeningvolgorde {#selectadobesigncloudserviceforanadaptiveform}

U kunt meerdere [!DNL Adobe Sign] diensten voor een AEM [!DNL Forms]. Het is raadzaam voor elke functie een aparte reeks diensten te hebben (Human Resource, Finance, enzovoort). Hierdoor kunt u ondertekende documenten gemakkelijker bijhouden en rapporteren. Een bank heeft bijvoorbeeld meerdere afdelingen. U kunt een afzonderlijke configuratie voor elke afdeling hebben voor het beter volgen van de documenten.

Een document kan ook meerdere ondertekenaars hebben. Een creditcardtoepassing kan bijvoorbeeld meerdere aanvragers hebben. Een bank vereist handtekeningen van alle aanvragers voordat de aanvraag wordt verwerkt. Voor scenario&#39;s met meerdere ondertekenaars kunt u ervoor kiezen het document in volgorde van opeenvolgende of gelijktijdige ondertekening te ondertekenen.

Voer de volgende stappen uit om een cloudservice en de volgorde van ondertekening te selecteren:

![cloudservice](assets/cloud-service.png)

1. Selecteer in de inhoudbrowser de optie **[!UICONTROL Form Container]** en selecteert u de **[!UICONTROL Configure]** ![vormen](assets/configure.png) pictogram. De eigenschappenbrowser wordt geopend en de eigenschappen van de container Adaptief formulier worden weergegeven.
1. Vouw in de eigenschappenbrowser de optie **[!UICONTROL Electronic Signature]** en selecteert u de **[!UICONTROL Enable Adobe Sign]** -optie. Het maakt [!DNL Adobe Sign] voor een adaptief formulier.
1. Selecteer een cloudservice in de lijst met reeds geconfigureerde [!DNL Adobe Sign] Cloud Servicen.

   Als de **[!UICONTROL Adobe Sign Cloud Service]** lijst is leeg, volgt de [Adobe Sign configureren met AEM Forms](../../forms/using/adobe-sign-integration-adaptive-forms.md) artikel om de dienst te vormen.

   In het vervolgkeuzemenu worden de cloudservices weergegeven die in het dialoogvenster `global` map in Gereedschappen > **[!UICONTROL Cloud Services]** > **[!UICONTROL Adobe Sign]**. Daarnaast worden in het vervolgkeuzemenu ook de cloudservices weergegeven die aanwezig zijn in de map die u selecteert in het dialoogvenster **[!UICONTROL Configuration Container]** wanneer u een adaptief formulier maakt.

1. Selecteer de handtekeningvolgorde in het menu **[!UICONTROL Signers can Sign]** in. [!DNL Adobe Sign] zangers kunnen een adaptief formulier ondertekenen **[!UICONTROL Sequentially]** - een na een andere ondertekenaar, of **[!UICONTROL Simultaneously]** - in willekeurige volgorde.

   Eén ondertekenaar ontvangt het formulier in volgorde voor ondertekening. Nadat een ondertekenaar het ondertekenen van het document heeft voltooid, wordt het formulier verzonden naar de volgende ondertekenaar, enzovoort.

   Meerdere ondertekenaars kunnen tegelijkertijd een formulier ondertekenen.

1. [Ondertekenaars toevoegen aan een adaptief formulier](../../forms/using/working-with-adobe-sign.md#addsignerstoanadaptiveform) en selecteer Gereed ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png) om de wijzigingen op te slaan.


### Ondertekenaars toevoegen aan een adaptief formulier {#addsignerstoanadaptiveform}

U kunt slechts één ondertekenaar of meerdere ondertekenaars hebben voor een adaptief formulier. Wanneer u een ondertekenaar toevoegt, kunt u ook verificatiedetails voor de ondertekenaar configureren. U kunt ook selecteren of de invuller en zanger van het formulier dezelfde persoon zijn. Voer de volgende stappen uit om diverse details over een ondertekenaar toe te voegen en te verstrekken:

1. Selecteer in de inhoudbrowser de optie **[!UICONTROL Form Container]** en selecteert u de **[!UICONTROL Configure]** ![vormen](assets/configure.png) pictogram. De eigenschappenbrowser wordt geopend met de eigenschappen van de container Adaptief formulier.
1. Vouw in de eigenschappenbrowser de optie **[!UICONTROL Electronic Signature]** en selecteert u de **[!UICONTROL Enable Adobe Sign]** -optie. Het maakt [!DNL Adobe Sign] voor een adaptief formulier.
1. Selecteren **[!UICONTROL Add Signer]** krachtens **[!UICONTROL Signer Configuration]**. Er wordt een ondertekenaar toegevoegd aan het adaptieve formulier. U kunt meerdere [!DNL Adobe Sign] ondertekenaars van een adaptief formulier.
   ![telefoongegevens](assets/phone-details.png)

1. Klik op de knop **Bewerken** ![aem_6_3_edit](assets/aem_6_3_edit.png) pictogram om de volgende informatie over de ondertekenaar op te geven:

   * **[!UICONTROL Title]:** Geef een titel op om een ondertekenaar op unieke wijze te identificeren.

   * **[!UICONTROL Is the signer and the person filling the form same?]:** Selecteren **Ja**, als de invuller van het formulier en de eerste ondertekenaar dezelfde persoon zijn. Als de optie is ingesteld op **Nee,** gebruikt u de component voor de stap Handtekening vervolgens niet in het adaptieve formulier. Als het formulier een component Handtekeningstap bevat, wordt het veld automatisch ingesteld op Ja.

   * **[!UICONTROL Signer Email address]:** Geef het e-mailadres van de ondertekenaar op. Ondertekenaar ontvangt om ondertekende documenten/formulier te zijn op het opgegeven e-mailadres. U kunt een e-mailadres gebruiken dat wordt opgegeven in een formulierveld, in AEM gebruikersprofiel van de aangemelde gebruiker, of handmatig een e-mailadres invoeren. Het is een verplichte stap. Zorg ervoor dat het e-mailadres van de eerste ondertekenaar of de enige ondertekenaar (als er één ondertekenaar is) niet hetzelfde is als [!DNL Adobe Sign] account gebruikt om AEM cloudservices te configureren.

   * **[!UICONTROL Signer Authentication Method]:** Geef de methode op voor het verifiëren van een gebruiker voordat u een formulier voor ondertekening opent. U kunt tussen telefoon, kennisbasis, en sociale op identiteit-gebaseerde authentificatie kiezen. Voor Adobe Acrobat Sign Solutions for Government zijn alleen opties voor telefoon en verificatie op basis van kennis beschikbaar.

   >[!NOTE]
   >
   >    * Standaard biedt verificatie op basis van sociale identiteit een optie voor verificatie met behulp van Facebook, Google en LinkedIn. U kunt contact [!DNL Adobe Sign] ondersteuning om andere aanbieders van sociale authenticatie mogelijk te maken.
   >
   >

   * **[!DNL Adobe Sign]velden die moeten worden ingevuld of ondertekend:** Selecteren [!DNL Adobe Sign] velden voor de ondertekenaar. Een adaptief formulier kan meerdere [!DNL Adobe Sign] velden. U kunt specifieke velden inschakelen voor een ondertekenaar. In het veld worden alle beschikbare [!DNL Adobe Sign] Blokken. Wanneer u een blok selecteert, worden alle velden van het blok geselecteerd. U kunt het X-pictogram gebruiken om een veld te deselecteren.

   ![ondertekenaar-details](assets/signer-details.png)

   De bovenstaande afbeelding heeft twee voorbeelden [!DNL Adobe Sign] Blokken: Personal-Information en Office-details

   Selecteer Gereed ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png) pictogram. De ondertekenaar wordt toegevoegd en geconfigureerd.

### Selecteer Handeling verzenden voor een adaptief formulier {#selectsubmitactionforanadaptiveform}

Voeg [!DNL Adobe Sign] velden in een adaptief formulier inschakelen [!DNL Adobe Sign] vanuit formuliercontainer selecteren [!DNL Adobe Sign] Cloud Servicen en toevoegen [!DNL Adobe Sign] Ondertekenaars, selecteer een geschikte verzendactie voor het adaptieve formulier. Voor meer informatie over adaptieve formulieren die acties verzenden, raadpleegt u [De handeling Verzenden configureren](../../forms/using/configuring-submit-actions.md).

Ook, en [!DNL Adobe Sign] Het ingeschakelde adaptieve formulier wordt alleen verzonden nadat alle ondertekenaars het formulier hebben ondertekend. Gedeeltelijk ondertekend formulier vindt u in de sectie Ondertekenen in behandeling van de portal Formulieren. [!DNL Adobe Sign] Configuratieservice blijft stemmen [!DNL Adobe Sign] server op [regelmatige intervallen](../../forms/using/adobe-sign-integration-adaptive-forms.md) om de status van handtekeningen te verifiëren. Als alle ondertekenaars het ondertekenen van het formulier hebben voltooid, wordt de verzendactieservice gestart en wordt het formulier verzonden. Als u een aangepaste verzendactie gebruikt en het formulier gebruikt [!DNL Adobe Sign]werkt u de aangepaste verzendactie bij om de verzendactieservice te gebruiken.

<!-- Remove when forms portal goes live
>[!NOTE]
>
>Data of the adaptive form is stored temporarily on Forms Portal. Use [custom storage for Forms Portal](/help/forms/using/configuring-draft-submission-storage.md). It ensures that the PII (personally identifiable information) data is not stored on AEM servers. 
-->

Uw ervaring voor het ondertekenen van formulieren is gereed. U kunt een voorbeeld van het formulier bekijken om de ondertekeningservaring te verifiëren. Op het gepubliceerde formulier: [!DNL Adobe Sign] Blokvelden worden weergegeven wanneer een ondertekenaar het formulier ontvangt voor ondertekening via een e-mail. Deze ervaring wordt ook wel bekend als een ondertekeningservaring in de vorm van een out-of-form. U kunt ook een ondertekeningservaring in formulieren configureren voor de eerste ondertekenaar. Zie voor meer informatie [Ervaring voor ondertekenen in formulieren maken](../../forms/using/working-with-adobe-sign.md#create-in-form-signing-experience).

## Cloud-handtekeningen configureren voor een adaptief formulier {#configure-cloud-signatures-for-an-adaptive-form}

Digitale handtekeningen op basis van cloud of externe handtekeningen zijn een nieuwe generatie digitale handtekeningen die op verschillende computers, mobiele apparaten en het web werken en voldoen aan de hoogste standaarden en waarborgen voor ondertekenaarsverificatie. U kunt een adaptief formulier ondertekenen met digitale handtekeningen op basis van de cloud.

Na [adaptieve formuliereigenschappen bewerken voor Adobe ondertekenen](../../forms/using/working-with-adobe-sign.md#enableadobesign), voert u de volgende stappen uit om het veld voor een cloudhandtekening toe te voegen aan een adaptief formulier:

1. Slepen en neerzetten **[!UICONTROL Adobe Sign Block]** van de deelbrowser naar het aangepaste formulier. De [!UICONTROL Adobe Sign Block] alle ondersteunde componenten [!DNL Adobe Sign] velden. Standaard wordt een **[!UICONTROL Signature]** aan het adaptieve formulier.

   ![Blok ondertekenen](assets/sign-block-new.png)

1. Selecteer de **[!UICONTROL Adobe Sign Block]** en selecteert u de **Bewerken** ![aem_6_3_edit](assets/aem_6_3_edit.png) pictogram. Er worden opties weergegeven voor het toevoegen van velden en het opmaken van de weergave van een veld.

   ![adobe-sign-block-select-fields](assets/adobe-sign-block-select-fields.png)

   **A.** Selecteren en toevoegen [!DNL Adobe Sign] velden. **B.** Breid uit [!DNL Adobe Sign] blokkeren naar volledige schermweergave

1. Selecteer de **[!UICONTROL Adobe Sign Field]** ![aem_6_3_adobesign](assets/aem_6_3_adobesign.png) pictogram. Er worden opties weergegeven om te selecteren en toe te voegen [!DNL Adobe Sign] velden.

   Breid uit **[!UICONTROL Type]** vervolgkeuzelijst die moet worden geselecteerd **[!UICONTROL Digital Signature]** en selecteert u de **Gereed** pictogram om het geselecteerde veld toe te voegen aan [!DNL Adobe Sign] blokkeren.

   ![Digitale handtekeningen](assets/digital_signatures_new.png)

   U moet een unieke naam opgeven voor een veld.

   Digitale handtekeningen toepassen op het adaptieve formulier met:

   * Cloud-handtekeningen: ondertekenen met een [digitale id](https://helpx.adobe.com/sign/kb/digital-certificate-providers.html) gehost door een vertrouwde serviceprovider. De optie Cloud Signature is niet beschikbaar voor Adobe Acrobat Sign Solutions for Government.

   * Adobe Acrobat of Reader: Download en open het document met Adobe Acrobat of Reader om het te ondertekenen met een smartcard, USB-token of digitale id op basis van een bestand.

   Nadat u het handtekeningveld voor de cloud aan het adaptieve formulier hebt toegevoegd, voert u de volgende stappen uit om het configuratieproces te voltooien:

   * [Adobe Sign inschakelen voor een adaptief formulier](../../forms/using/working-with-adobe-sign.md#enableadobsignforanadaptiveform)
   * [Selecteer Adobe Sign Cloud Service voor een adaptief formulier](../../forms/using/working-with-adobe-sign.md#selectadobesigncloudserviceforanadaptiveform)
   * [Adobe Sign-ondertekenaars toevoegen aan een adaptief formulier](../../forms/using/working-with-adobe-sign.md#addsignerstoanadaptiveform)
   * [Selecteer Handeling verzenden voor een adaptief formulier](../../forms/using/working-with-adobe-sign.md#selectsubmitactionforanadaptiveform)

## Ervaring voor ondertekenen in formulieren maken {#create-in-form-signing-experience}

Een gebruiker kan ook een adaptief formulier ondertekenen terwijl het formulier wordt ingevuld. Deze ervaring wordt ook wel &#39;in-form signing experience&#39; genoemd. De ondertekeningservaring in formulieren is alleen beschikbaar voor de eerste ondertekenaar in een omgeving met meerdere ondertekenaars. Voer de volgende stappen uit om een ondertekeningservaring in formulieren te maken voor een adaptief formulier:

1. [De component voor de stap Handtekening toevoegen en configureren](../../forms/using/working-with-adobe-sign.md#add-and-configure-the-signature-step-component).
1. [De component Summiere stap toevoegen](../../forms/using/working-with-adobe-sign.md#configure-the-thank-you-page-or-summary-step-component).

![Ervaring voor in-form ondertekenen](assets/in_form_signing_experience_new.png)

### De component voor de stap Handtekening toevoegen en configureren {#add-and-configure-the-signature-step-component}

Gebruik de component Handtekeningstap om een gebied op te geven voor de elektronische ondertekening van het ingevulde formulier. Wanneer de sectie met de component Signature Step wordt weergegeven, wordt een ondertekenbare PDF-versie van het ingevulde formulier weergegeven. De component voor de stap Handtekening gebruikt de volledige breedte die beschikbaar is voor het formulier. Het wordt aanbevolen geen andere component op te nemen in de sectie die de component voor de stap Handtekening bevat.

Voer de volgende stappen uit om de component van de Stap van de Handtekening te vormen:

1. Sleep de **[!UICONTROL Signature Step]** van de browser Componenten naar het formulier.
1. Selecteer de nieuwe component voor de stap Handtekening en selecteer de optie **Configureren** ![vormen](assets/configure.png) pictogram. De eigenschappenbrowser wordt geopend en de eigenschappen voor stap Handtekening worden weergegeven. Configureer de volgende eigenschappen:

   * **[!UICONTROL Name]**: Geef de naam van de component op.

   * **[!UICONTROL Title]:** Geef de unieke titel van de component op.
   * **[!UICONTROL Template message]:** Geef het bericht op dat moet worden weergegeven wanneer de PDF van de handtekening wordt geladen. [!DNL Adobe Sign] de diensten nemen wat tijd om handtekening PDF voor te bereiden en te laden.
   * **[!UICONTROL Signing Service]:** Selecteer de **[!DNL Adobe Sign]** -optie.

   * **[!UICONTROL Use legacy E-sign component]**: Als u het betreffende adaptieve formulier gebruikt in [AEM Forms Workspace](../../forms/using/introduction-html-workspace.md), AEM [!DNL Forms] of het onderliggende adaptieve formulier een oudere e-sign-component heeft, selecteert u de **Verouderde E-sign component gebruiken** -optie.

   * **[!UICONTROL Configuration]**: Selecteer een configuratie ([!DNL Adobe Sign] Cloud Service). De vervolgkeuzelijst is alleen beschikbaar als de **Verouderde E-sign component gebruiken** is ingeschakeld.

   * **[!UICONTROL CSS Class]**: Geef de CSS-klasse voor de component op.

   Selecteer Gereed ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png) om de wijzigingen op te slaan.

   ![Handtekeningstap](assets/signature_step_new.png)

   >[!NOTE]
   >
   >* Wanneer u de **[!UICONTROL Signature Step]** aan het formulier, de **[!UICONTROL Is the signer and the person filling the form same?]** optie wordt automatisch ingesteld op **Ja**. U moet het formulier blijven gebruiken.
   >* Gebruik de component Samenvattingsstap na de component Handtekeningstap voor een optimale ervaring. De stap Overzicht verzendt het formulier automatisch en direct nadat u het ondertekenen van een formulier hebt voltooid in de component Stap handtekening. Als u de overzichtsstap niet gebruikt, wordt een automatische voorlegging teweeggebracht slechts na het interval dat wordt geplaatst gebruikend [Adobe Sign Configuration Service](../../forms/using/adobe-sign-integration-adaptive-forms.md#configure-adobe-sign-scheduler-to-sync-the-signing-status).
   >
   >Enkele aanbevolen procedures zijn:
   >
   >* Het deelvenster Adaptief formulier met de stap Handtekening bevindt zich altijd in het laatste of tweede laatste deelvenster van een adaptief formulier. Dit kan alleen het tweede laatste deelvenster zijn wanneer het laatste deelvenster de stap Overzicht bevat.
   >* Het deelvenster met de stapcomponent Handtekening of Samenvatting mag geen andere component bevatten.
   >* Adaptieve formulieren met de stap Handtekening kunnen niet worden verzonden.
   >* De verzending van de adaptieve formulieren met de stap Handtekening wordt afgehandeld via een achtergrondservice of de stap Samenvatting. Als er één geconfigureerde ondertekenaar is die het formulier ook invult, heeft de verwerking van het adaptieve formulier via de stap Samenvatting als voordeel dat deze direct evalueert dat de ondertekenaar het formulier heeft ondertekend en de actie Verzenden heeft geactiveerd. Een achtergrondservice heeft meer tijd nodig om te beoordelen of alle geconfigureerde ondertekenaars het formulier hebben ondertekend en de verzending van het adaptieve formulier vertragen.
   >* Ontwerp het formulier zodanig dat een gebruiker niet kan terugnavigeren vanuit een deelvenster dat de stap Handtekening of Overzicht bevat.


### De component voor de prullenbak of overzichtsstap configureren {#configure-the-thank-you-page-or-summary-step-component}

De **Samenvattingsstap** wordt het formulier automatisch verzonden, wordt de informatie in de aangepaste overzichtspagina ingevuld en wordt de samenvatting van het verzonden formulier weergegeven. Het krijgt ook de vereiste informatie in de terugkeerkaart. De component SummaryStep gebruikt de volledige breedte die beschikbaar is voor het formulier. Men adviseert om geen andere component op de sectie te hebben die de Summiere component van de Stap bevat.

De ervaring voor het ondertekenen van formulieren is nu gereed. U kunt een voorbeeld van het formulier bekijken om de ondertekeningservaring te verifiëren.

## Veelgestelde vragen {#frequently-asked-questions}

**V:** U kunt een adaptief formulier insluiten in een ander adaptief formulier. Kan het ingesloten adaptieve formulier worden [!DNL Adobe Sign] ingeschakeld?
**Ans:** Nee, AEM [!DNL Forms] biedt geen ondersteuning voor het gebruik van een adaptief formulier dat een [!DNL Adobe Sign] Aangepast formulier voor ondertekenen ingeschakeld

**V:** Wanneer ik een adaptief formulier maak met de geavanceerde sjabloon en dit open voor bewerking, wordt het foutbericht &quot;Elektronische handtekening of Ondertekenaars zijn niet correct geconfigureerd&quot; weergegeven. wordt weergegeven. Hoe kan ik het foutbericht oplossen?
**Ans:** Aangepast formulier dat is gemaakt met de geavanceerde sjabloon is geconfigureerd voor gebruik [!DNL Adobe Sign]. U lost de fout op door een [!DNL Adobe Sign] cloudconfiguratie en [!DNL Adobe Sign] ondertekenaar voor het adaptieve formulier.

**V:** Kan ik gebruiken [!DNL Adobe Sign] tekstcodes in een statisch tekstonderdeel van een adaptief formulier?
**Ans:** Ja, u kunt tekstcodes in een tekstcomponent gebruiken om toe te voegen [!DNL Adobe Sign] velden naar een [Document van record](../../forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md) (Alleen automatisch gegenereerd document met opnameoptie) Aangepast formulier ingeschakeld. Ga voor meer informatie over de procedure en regels voor het maken van een tekstlabel naar [Adobe Sign-documentatie](https://helpx.adobe.com/sign/using/text-tag.html). Houd er rekening mee dat adaptieve formulieren beperkte ondersteuning bieden voor tekstcodes. U kunt de tekstlabels gebruiken om alleen die velden te maken die [Adobe Sign Block](../../forms/using/working-with-adobe-sign.md#configure-cloud-signatures-for-an-adaptive-form) ondersteunt.

**V:** AEM [!DNL Forms] biedt beide [!UICONTROL Adobe Sign block] en componenten van de Handtekeningstap. Kunnen deze gelijktijdig in een adaptieve vorm worden gebruikt?
**Ans:** U kunt beide componenten tegelijkertijd in een formulier gebruiken. Hier volgen enkele aanbevelingen voor het gebruik van deze componenten:

**Adobe Sign-blok:** U kunt de [!UICONTROL Adobe Sign Block] toevoegen [!UICONTROL Adobe Sign] velden op het adaptieve formulier. Het helpt ook om specifieke gebieden aan ondertekenaars toe te wijzen. Wanneer een adaptief formulier wordt voorvertoond of gepubliceerd [!UICONTROL Adobe Sign] Blok is standaard niet zichtbaar. Deze blokken zijn alleen beschikbaar in het ondertekenende document. In het ondertekenende document worden alleen de velden ingeschakeld die zijn toegewezen aan een ondertekenaar. [!UICONTROL Adobe Sign] blok kan met eerste en verdere ondertekenaars worden gebruikt.

**Ondertekeningsstapcomponent:** U kunt de component voor het verzenden van handtekeningen gebruiken om in formulieren ondertekenen te maken. Hiermee kan alleen de eerste ondertekenaar ondertekenen terwijl het formulier wordt ingevuld. Wanneer de sectie met de component Signature Step wordt weergegeven, wordt een ondertekenbare PDF-versie van het formulier weergegeven. Het is doorgaans de laatste of voorlaatste sectie, gevolgd door een overzichtscomponent van een formulier.

## Problemen oplossen {#troubleshoot}

### [!DNL Adobe Sign] fouten in overeenkomst {#adobe-sign-agreement-failures}

**Probleem**
Wanneer [!DNL Adobe Sign] de service is geconfigureerd voor een adaptief formulier, kan de service geen [!DNL Adobe Sign] akkoord voor het onderliggende adaptieve formulier.

**Resolutie**

* Controleer de [configuratie van de Adobe Sign-cloudservice](../../forms/using/adobe-sign-integration-adaptive-forms.md) in het adaptieve formulier worden gebruikt.
* Zorg ervoor dat de API-toepassing ingeschakeld is [!DNL Adobe Sign] server gebruikt om te vormen [!DNL Adobe Sign] Cloud-service heeft vereiste machtigingen.
* Als u meerdere [!DNL Adobe Sign] Cloudservices, wijs naar de **[!UICONTROL oAuth URL]** van alle diensten **[!UICONTROL Adobe Sign Shard]**.

* Afzonderlijke e-mailadressen gebruiken om te configureren [!DNL Adobe Sign] account en voor de eerste ondertekenaar en één ondertekenaar. Het e-mailadres van de eerste ondertekenaar of de enige ondertekenaar (als er één ondertekenaar is) mag niet hetzelfde zijn als [!DNL Adobe Sign] account gebruikt om AEM cloudservices te configureren.

### AEM [!DNL Forms] workflow geconfigureerd voor een [!DNL Adobe Sign] ingeschakeld adaptief formulier wordt niet gestart {#adobe-sign-aem-form-workflow-failures}

**Probleem**
Wanneer [!DNL Adobe Sign] is geconfigureerd voor een adaptief formulier, de workflow geconfigureerd met Invoke [!DNL Forms] Workflowoptie wordt niet gestart.

**Resolutie**

* Wanneer u [!DNL Adobe Sign] zonder de stap Handtekening of het formulier handtekeningen van meerdere personen vereist, AEM [!DNL Forms] De server wacht op de planner om te bevestigen dat alle personen het formulier hebben ondertekend. De planner dient het adaptieve formulier alleen in nadat alle persoon de ondertekening heeft voltooid en de workflow pas begint nadat het adaptieve formulier met succes is verzonden. U kunt het interval van de [planner](adobe-sign-integration-adaptive-forms.md) om de status van het ondertekenen van formulieren snel te controleren en het verzenden van formulieren te versnellen.


## Verwante artikelen {#related-articles}

* [Adobe Sign integreren met AEM Forms](../../forms/using/adobe-sign-integration-adaptive-forms.md)
* [Aanbevolen procedures voor het gebruik van Adobe Sign met adaptieve formulieren](https://medium.com/adobetech/using-adobe-sign-to-e-sign-an-adaptive-form-heres-the-best-way-to-do-it-dc3e15f9b684)
* [Adobe Sign gebruiken met AEM Forms (video)](https://helpx.adobe.com/experience-manager/kt/forms/using/adobe-sign-integration-feature-video.html)
