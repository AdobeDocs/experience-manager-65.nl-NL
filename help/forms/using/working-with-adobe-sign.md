---
title: Adobe Sign in een adaptieve vorm gebruiken
description: Workflows voor e-handtekeningen (Adobe Sign) inschakelen voor een adaptief formulier om ondertekeningsworkflows te automatiseren, processen met één en meerdere handtekeningen te vereenvoudigen en formulieren van mobiele apparaten elektronisch te ondertekenen.
contentOwner: khsingh
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop
feature: Adaptive Forms,Foundation Components,Acrobat Sign
discoiquuid: f79828d8-2230-4477-8ffa-eeb6a0413acd
docset: aem65
exl-id: a8decba9-229d-40a2-992a-3cc8ebefdd6d
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '3673'
ht-degree: 0%

---

# [!DNL Adobe Sign] gebruiken in een adaptieve vorm{#using-adobe-sign-in-an-adaptive-form}

<span class="preview"> de Adobe adviseert gebruikend de moderne en verlengbare gegevens vangen [ Componenten van de Kern ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=nl-NL) voor [ het creëren van nieuwe Aangepaste Forms ](/help/forms/using/create-an-adaptive-form-core-components.md) of [ het toevoegen van Aangepaste Forms aan de pagina&#39;s van AEM Sites ](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor de auteur Adaptive Forms die gebruikmaakt van stichtingscomponenten. </span>

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/use-adobe-sign/working-with-adobe-sign.html?lang=nl-NL) |
| AEM 6,5 | Dit artikel |


Met [!DNL Adobe Sign] kunt u workflows voor e-handtekeningen inschakelen voor adaptieve formulieren. E-handtekeningen verbeteren werkstromen om documenten voor wettig, verkoop, loonlijst, personeelsbeheer, en meer gebieden te verwerken.

In een typisch [!DNL Adobe Sign] en adaptief formulierscenario vult een gebruiker een adaptief formulier om een service aan te vragen. Een hypotheek- en creditcardaanvraag vereist bijvoorbeeld wettelijke handtekeningen van alle kredietnemers en medekredietnemers. Als u workflows voor elektronische handtekeningen wilt inschakelen voor vergelijkbare scenario&#39;s, kunt u [!DNL Adobe Sign] integreren met AEM [!DNL Forms] . U kunt [!DNL Adobe Sign] nog enkele voorbeelden gebruiken om:

* Sluit overeenkomsten van om het even welk apparaat met volledig geautomatiseerde voorstel, citaat, en contractprocessen.
* Voltooi processen voor menselijke hulpbronnen sneller en geef uw werknemers de digitale ervaring.
* Verkort de duur van de contractcyclus en neem sneller aan boord van uw leveranciers.
* Maak digitale workflows die algemene processen automatiseren.

[!DNL Adobe Sign] integratie met AEM [!DNL Forms] ondersteunt:

* Workflows voor ondertekening van enkelvoudige en meervoudige gebruikers
* Workflows voor opeenvolgende en gelijktijdige ondertekening
* Ondertekeningservaringen in formulieren en in formulieren
* Formulieren ondertekenen als anonieme of aangemelde gebruiker
* Dynamische ondertekeningsprocessen (integratie met AEM [!DNL Forms] -workflow)
* Verificatie via een kennisbasis, telefoon en sociale profielen

Leer de [ beste praktijken om Adobe Sign met adaptieve vormen ](https://medium.com/adobetech/using-adobe-sign-to-e-sign-an-adaptive-form-heres-the-best-way-to-do-it-dc3e15f9b684) te gebruiken om betere het ondertekenen ervaringen tot stand te brengen.

## Vereisten {#prerequisites}

Voordat u [!DNL Adobe Sign] in een adaptieve vorm gebruikt:

* Zorg ervoor dat AEM [!DNL Forms] cloudservice is geconfigureerd voor gebruik van [!DNL Adobe Sign] . Voor details, zie [ Adobe Sign met AEM Forms ](../../forms/using/adobe-sign-integration-adaptive-forms.md) integreren.
* Behoud de lijst met ondertekenaars klaar. U hebt voor elke ondertekenaar ten minste een e-mailadres nodig.

## [!DNL Adobe Sign] configureren voor een adaptief formulier {#configure-adobe-sign-for-an-adaptive-form}

Voer de volgende stappen uit om [!DNL Adobe Sign] voor een adaptief formulier te configureren:

1. [Aangepaste formuliereigenschappen bewerken voor Adobe ondertekenen](../../forms/using/working-with-adobe-sign.md#enableadobesign)
1. [Adobe Sign-velden toevoegen aan een adaptief formulier](../../forms/using/working-with-adobe-sign.md#addadobesignfieldstoanadaptiveform)
1. [Adobe Sign inschakelen voor een adaptief formulier](../../forms/using/working-with-adobe-sign.md#enableadobsignforanadaptiveform)
1. [Selecteer Adobe Sign Cloud Service voor een adaptief formulier](../../forms/using/working-with-adobe-sign.md#selectadobesigncloudserviceforanadaptiveform)

1. [Adobe Sign-ondertekenaars toevoegen aan een adaptief formulier](../../forms/using/working-with-adobe-sign.md#addsignerstoanadaptiveform)
1. [Selecteer Handeling verzenden voor een adaptief formulier](../../forms/using/working-with-adobe-sign.md#selectsubmitactionforanadaptiveform)

![ Details van de Ondertekenaar ](assets/signer_details_new.png)

### Aangepaste formuliereigenschappen bewerken voor [!DNL Adobe Sign] {#enableadobesign}

Configureer adaptieve formuliereigenschappen voor [!DNL Adobe Sign] voor een bestaand of een nieuw adaptief formulier.

[ creeer een adaptieve vorm voor Adobe Sign ](../../forms/using/working-with-adobe-sign.md#create-an-adaptive-form-for-adobe-sign) beschrijft de stappen om een basisadaptieve vorm tot stand te brengen. Zie [ Creërend een adaptieve vorm ](../../forms/using/creating-adaptive-form.md) voor andere beschikbare opties terwijl het creëren van een adaptieve vorm.

#### Een adaptief formulier maken voor [!DNL Adobe Sign] {#create-an-adaptive-form-for-adobe-sign}

Voer de volgende stappen uit om een adaptief formulier te maken dat geschikt is voor ondertekenen:

1. Navigeer naar **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]** .
1. Selecteer **[!UICONTROL Create]** en selecteer **[!UICONTROL Adaptive Form]** . Er wordt een lijst met sjablonen weergegeven. Selecteer de sjabloon en selecteer **[!UICONTROL Next]** .
1. Op het tabblad **[!UICONTROL Basic]** :

   1. Geef de **[!UICONTROL Name]** en **[!UICONTROL Title]** op voor het adaptieve formulier.

   1. Selecteer de [ gemaakte configuratiecontainer ](../../forms/using/adobe-sign-integration-adaptive-forms.md#configure-adobe-sign-with-aem-forms) terwijl het vormen [!DNL Adobe Sign] met AEM [!DNL Forms].

      >[!NOTE]
      >
      >In de vervolgkeuzelijst **[!UICONTROL Adobe Sign Cloud Service]** worden de cloudservices weergegeven die zijn geconfigureerd in de configuratiecontainer die u in dit veld selecteert. De vervolgkeuzelijst **[!UICONTROL Adobe Sign Cloud Service]** is beschikbaar in de sectie **[!UICONTROL Electronic Signature]** van de adaptieve formuliereigenschappen wanneer u de optie **[!UICONTROL Enable Adobe Sign]** selecteert.

1. Selecteer op het tabblad **[!UICONTROL Form Model]** een van de volgende opties:

   * Selecteer de optie **[!UICONTROL Associate form template as the Document of Record template]** en selecteer een Document van het malplaatje van het Verslag. Als u een op een formuliersjabloon gebaseerd adaptief formulier gebruikt, worden alleen de velden weergegeven die zijn gebaseerd op de bijbehorende formuliersjabloon. Niet alle velden van het adaptieve formulier worden weergegeven.

   * Selecteer de optie **[!UICONTROL Generate Document of Record]** . Als u een adaptief formulier met de optie Document of Record gebruikt, worden in het document dat wordt verzonden voor ondertekening alle velden van het adaptieve formulier weergegeven.

1. Selecteer **[!UICONTROL Create.]** Er wordt een adaptief formulier gemaakt dat geschikt is voor ondertekening en dat kan worden gebruikt om [!DNL Adobe Sign] -velden toe te voegen.

#### Een adaptief formulier bewerken voor [!DNL Adobe Sign] {#editafsign}

Voer de volgende stappen uit om [!DNL Adobe Sign] in een bestaande adaptieve vorm te gebruiken:

1. Navigeer naar **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]** .
1. Selecteer het aangepaste formulier en selecteer **[!UICONTROL Properties]** .
1. In het **[!UICONTROL Basic]** lusje, selecteer de [ gemaakte configuratiecontainer ](../../forms/using/adobe-sign-integration-adaptive-forms.md#configure-adobe-sign-with-aem-forms) terwijl het vormen [!DNL Adobe Sign] met AEM [!DNL Forms].
1. Selecteer op het tabblad **[!UICONTROL Form Model]** een van de volgende opties:

   * Selecteer de optie **[!UICONTROL Associate form template as the Document of Record template]** en selecteer een Document van het malplaatje van het Verslag. Als u een op een formuliersjabloon gebaseerd adaptief formulier gebruikt, worden alleen de velden weergegeven die zijn gebaseerd op de bijbehorende formuliersjabloon. Niet alle velden van het adaptieve formulier worden weergegeven.

   * Selecteer de optie **[!UICONTROL Generate Document of Record]** . Als u een adaptief formulier met de optie Document of Record gebruikt, worden in het document dat wordt verzonden voor ondertekening alle velden van het adaptieve formulier weergegeven.

1. Selecteer **[!UICONTROL Save & Close]**. Het adaptieve formulier is ingeschakeld voor [!DNL Adobe Sign] .

### Adobe Sign-velden toevoegen aan een adaptief formulier {#addadobesignfieldstoanadaptiveform}

[!DNL Adobe Sign] heeft verschillende velden die op een adaptief formulier kunnen worden geplaatst. Deze velden accepteren verschillende gegevenstypen, zoals handtekeningen, initialen, bedrijf of titel, en helpen bij het verzamelen van extra informatie tijdens het ondertekenen, samen met de handtekeningen. Met de component [!DNL Adobe Sign] Blokkeren kunt u [!DNL Adobe Sign] -velden op verschillende locaties in een adaptief formulier plaatsen.

Voer de volgende stappen uit om velden toe te voegen aan een adaptief formulier en verschillende opties aan te passen met betrekking tot deze velden:

1. Sleep de component **[!UICONTROL Adobe Sign Block]** van de componentbrowser naar het aangepaste formulier. De [!DNL Adobe Sign] Block-component heeft alle ondersteunde [!DNL Adobe Sign] -velden. Door gebrek, voegt het a **gebied van de Handtekening** aan de adaptieve vorm toe.

   ![ blok van het Teken ](assets/sign_block_new.png)

   Standaard is het blok [!DNL Adobe Sign] niet zichtbaar in het gepubliceerde adaptieve formulier. Deze is alleen zichtbaar in de ondertekenende documenten. U kunt de zichtbaarheid van [!DNL Adobe Sign] Block wijzigen in de eigenschappen van de [!DNL Adobe Sign] Block-component.

   >[!NOTE]
   >
   >    * Het gebruik van [!DNL Adobe Sign] -blok is niet verplicht om [!DNL Adobe Sign] in een adaptieve vorm te gebruiken. Als u [!DNL Adobe Sign] -blok niet gebruikt en geen velden toevoegt voor de ondertekenaars, wordt het standaardhandtekeningveld onder aan de ondertekenende documenten weergegeven.
   >    * Gebruik [!DNL Adobe Sign] alleen voor adaptieve formulieren die automatisch een Document of Record genereren. Als u een aangepaste XDP gebruikt voor het genereren van een Document of een adaptief formulier op basis van een formuliersjabloon, wordt [!DNL Adobe Sign] -blok niet ondersteund.
   >
   >

1. Selecteer de **[!UICONTROL Adobe Sign Block]** component en selecteer **uitgeven** ![ aem_6_3_edit ](assets/aem_6_3_edit.png) pictogram. Er worden opties weergegeven voor het toevoegen van velden en het opmaken van de weergave van een veld.

   ![ adobe-sign-block-select-fields ](assets/adobe-sign-block-select-fields.png)

   **A.** selecteer en voeg [!DNL Adobe Sign] gebieden toe. **B.** breid het [!DNL Adobe Sign] blok aan volledige het schermmening uit

1. Selecteer het **[!UICONTROL Adobe Sign]Gebied** ![ aem_6_3_adobesign ](assets/aem_6_3_adobesign.png) pictogram. Er worden opties weergegeven voor het selecteren en toevoegen van [!DNL Adobe Sign] -velden.

   Vouw het **[!UICONTROL Type]** drop-down gebied uit om een [!DNL Adobe Sign] gebied te selecteren en het Gedaan ![ te selecteren aem_6_3_forms_save ](assets/aem_6_3_forms_save.png) pictogram om het geselecteerde gebied aan [!DNL Adobe Sign] blok toe te voegen. Het vervolgkeuzeveld **[!UICONTROL Type]** bevat de typen Handtekening, Ondertekenaarinformatie en Gegevensveld. [!DNL Adobe Sign] integratie met AEM [!DNL Forms] -ondersteuningsvelden die alleen in de vervolgkeuzelijst [!UICONTROL Type] worden weergegeven. Voor gedetailleerde informatie over [!DNL Adobe Sign] gebieden, zie [ documentatie van Adobe Sign ](https://helpx.adobe.com/nl/sign/help/field-types.html).

   ![ adobe-sign-block-fields-options ](assets/adobe-sign-block-fields-options.png)

   U moet een unieke naam opgeven voor een veld. U kunt ook de vereiste optie selecteren om een verplicht veld te markeren. Naast de opties **[!UICONTROL Name]** en **[!UICONTROL Required]** , hebben sommige [!DNL Adobe Sign] velden meer opties. Bijvoorbeeld masker en meerdere regels. Geef bovendien voor elk [!DNL Adobe Sign] -veld een unieke naam, ongeacht of de velden zich in dezelfde of in andere [!DNL Adobe Sign] -blokken bevinden.

   Als u **[!UICONTROL Digital Signature]** selecteert in de vervolgkeuzelijst, kunt u digitale handtekeningen toepassen op het aangepaste formulier:

   * Online gebruikend wolkenhandtekeningen om met a [ digitale identiteitskaart ](https://helpx.adobe.com/nl/sign/kb/digital-certificate-providers.html) te ondertekenen die door een vertrouwde dienstverlener wordt ontvangen.
   * Lokaal door het document te downloaden met Adobe Acrobat of Reader met een smartcard, USB-token of een op een bestand gebaseerde digitale id.

### [!DNL Adobe Sign] inschakelen voor een adaptief formulier {#enableadobsignforanadaptiveform}

Uit het vak is [!DNL Adobe Sign] niet ingeschakeld voor een adaptief formulier. Voer de volgende stappen uit om het in te schakelen:

1. In browser van de Inhoud, selecteer **[!UICONTROL Form Container]**, en selecteer **[!UICONTROL Configure]** ![ vormen ](assets/configure.png) pictogram. De eigenschappenbrowser wordt geopend en de eigenschappen van de container Adaptief formulier worden weergegeven.
1. Vouw in de eigenschappenbrowser de accordeon **[!UICONTROL Electronic Signature]** uit en selecteer de optie **[!UICONTROL Enable Adobe Sign]** . Hiermee wordt [!DNL Adobe Sign] ingeschakeld voor een adaptief formulier.

### Cloud Service en handtekeningvolgorde selecteren [!DNL Adobe Sign] {#selectadobesigncloudserviceforanadaptiveform}

U kunt meerdere [!DNL Adobe Sign] -services configureren voor een instantie van AEM [!DNL Forms] . Het is raadzaam voor elke functie een aparte reeks diensten te hebben (Human Resource, Finance, enzovoort). Hierdoor kunt u ondertekende documenten gemakkelijker bijhouden en rapporteren. Een bank heeft bijvoorbeeld meerdere afdelingen. U kunt een afzonderlijke configuratie voor elke afdeling hebben voor het beter volgen van de documenten.

Een document kan ook meerdere ondertekenaars hebben. Een creditcardtoepassing kan bijvoorbeeld meerdere aanvragers hebben. Een bank vereist handtekeningen van alle aanvragers voordat de aanvraag wordt verwerkt. Voor scenario&#39;s met meerdere ondertekenaars kunt u ervoor kiezen het document in volgorde van opeenvolgende of gelijktijdige ondertekening te ondertekenen.

Voer de volgende stappen uit om een cloudservice en de volgorde van ondertekening te selecteren:

![ wolk-dienst ](assets/cloud-service.png)

1. In browser van de Inhoud, selecteer **[!UICONTROL Form Container]**, en selecteer **[!UICONTROL Configure]** ![ vormen ](assets/configure.png) pictogram. De eigenschappenbrowser wordt geopend en de eigenschappen van de container Adaptief formulier worden weergegeven.
1. Vouw in de eigenschappenbrowser de accordeon **[!UICONTROL Electronic Signature]** uit en selecteer de optie **[!UICONTROL Enable Adobe Sign]** . Hiermee wordt [!DNL Adobe Sign] ingeschakeld voor een adaptief formulier.
1. Selecteer een cloudservice in de lijst met [!DNL Adobe Sign] Cloud Servicen die al is geconfigureerd.

   Als de **[!UICONTROL Adobe Sign Cloud Service]** lijst leeg is, volg [ Adobe Sign met AEM Forms ](../../forms/using/adobe-sign-integration-adaptive-forms.md) artikel vormen om de dienst te vormen.

   Het vervolgkeuzemenu bevat een lijst met de cloudservices die in de map `global` staan in Opties > **[!UICONTROL Cloud Services]** > **[!UICONTROL Adobe Sign]** . Bovendien worden in het vervolgkeuzemenu ook de cloudservices weergegeven die aanwezig zijn in de map die u in het veld **[!UICONTROL Configuration Container]** selecteert wanneer u een adaptief formulier maakt.

1. Selecteer de handtekeningvolgorde in het dialoogvenster **[!UICONTROL Signers can Sign]** . [!DNL Adobe Sign] zangers kunnen een adaptief formulier ondertekenen **[!UICONTROL Sequentially]** , een na een andere ondertekenaar, of **[!UICONTROL Simultaneously]** , in willekeurige volgorde.

   Eén ondertekenaar ontvangt het formulier in volgorde voor ondertekening. Nadat een ondertekenaar het ondertekenen van het document heeft voltooid, wordt het formulier verzonden naar de volgende ondertekenaar, enzovoort.

   Meerdere ondertekenaars kunnen tegelijkertijd een formulier ondertekenen.

1. [ voeg Ondertekenaars aan een adaptieve vorm ](../../forms/using/working-with-adobe-sign.md#addsignerstoanadaptiveform) toe en selecteer het Gedaan ![ aem_6_3_forms_save ](assets/aem_6_3_forms_save.png) pictogram om de veranderingen te bewaren.


### Ondertekenaars toevoegen aan een adaptief formulier {#addsignerstoanadaptiveform}

U kunt slechts één ondertekenaar of meerdere ondertekenaars hebben voor een adaptief formulier. Wanneer u een ondertekenaar toevoegt, kunt u ook verificatiedetails voor de ondertekenaar configureren. U kunt ook selecteren of de invuller en zanger van het formulier dezelfde persoon zijn. Voer de volgende stappen uit om diverse details over een ondertekenaar toe te voegen en te verstrekken:

1. In browser van de Inhoud, selecteer **[!UICONTROL Form Container]**, en selecteer **[!UICONTROL Configure]** ![ vormen ](assets/configure.png) pictogram. De eigenschappenbrowser wordt geopend met de eigenschappen van de container Adaptief formulier.
1. Vouw in de eigenschappenbrowser de accordeon **[!UICONTROL Electronic Signature]** uit en selecteer de optie **[!UICONTROL Enable Adobe Sign]** . Hiermee wordt [!DNL Adobe Sign] ingeschakeld voor een adaptief formulier.
1. Selecteer **[!UICONTROL Add Signer]** onder **[!UICONTROL Signer Configuration]** . Er wordt een ondertekenaar toegevoegd aan het adaptieve formulier. U kunt meerdere [!DNL Adobe Sign] -ondertekenaars toevoegen aan een adaptief formulier.
   ![ telefoon-details ](assets/phone-details.png)

1. Klik **uitgeven** ![ aem_6_3_geef ](assets/aem_6_3_edit.png) pictogram uit om de volgende informatie over de ondertekenaar te specificeren:

   * **[!UICONTROL Title]:** specificeer een titel om een ondertekenaar uniek te identificeren.

   * **[!UICONTROL Is the signer and the person filling the form same?]:** Uitgezochte **ja**, als de vorminvuller en eerste ondertekenaar de zelfde persoon zijn. Als de optie aan **Nr wordt geplaatst,** dan gebruikt niet de component van de handtekeningsstap in de adaptieve vorm. Als het formulier een component Handtekeningstap bevat, wordt het veld automatisch ingesteld op Ja.

   * **[!UICONTROL Signer Email address]:** geef een e-mailadres van de ondertekenaar op. Ondertekenaar ontvangt om ondertekende documenten/formulier te zijn op het opgegeven e-mailadres. U kunt een e-mailadres gebruiken dat wordt opgegeven in een formulierveld, in AEM gebruikersprofiel van de aangemelde gebruiker, of handmatig een e-mailadres invoeren. Het is een verplichte stap. Zorg ervoor dat het e-mailadres van de eerste ondertekenaar of de enige ondertekenaar (als er één ondertekenaar is) niet hetzelfde is als het e-mailadres van [!DNL Adobe Sign] dat wordt gebruikt om AEM cloudservices te configureren.

   * **[!UICONTROL Signer Authentication Method]:** geef de methode op voor het verifiëren van een gebruiker voordat u een formulier voor ondertekening opent. U kunt tussen telefoon, kennisbasis, en sociale op identiteit-gebaseerde authentificatie kiezen. Voor Adobe Acrobat Sign Solutions for Government zijn alleen opties voor telefoon en verificatie op basis van kennis beschikbaar.

   >[!NOTE]
   >
   >    * Standaard biedt verificatie op basis van sociale identiteit een optie voor verificatie met behulp van Facebook, Google en LinkedIn. U kunt contact opnemen met de ondersteuning van [!DNL Adobe Sign] om andere providers van sociale verificatie in te schakelen.
   >
   >

   * **[!DNL Adobe Sign]velden die moeten worden ingevuld of ondertekend:** Selecteer [!DNL Adobe Sign] velden voor de ondertekenaar. Een adaptief formulier kan meerdere [!DNL Adobe Sign] velden hebben. U kunt specifieke velden inschakelen voor een ondertekenaar. In het veld worden alle beschikbare [!DNL Adobe Sign] blokken weergegeven. Wanneer u een blok selecteert, worden alle velden van het blok geselecteerd. U kunt het X-pictogram gebruiken om een veld te deselecteren.

   ![ ondertekenaar-details ](assets/signer-details.png)

   De bovenstaande afbeelding heeft twee voorbeelden [!DNL Adobe Sign] Blokken: Persoonlijke informatie en Office-details

   Selecteer het Gedaan ![ a_6_3_forms_save ](assets/aem_6_3_forms_save.png) pictogram. De ondertekenaar wordt toegevoegd en geconfigureerd.

### Selecteer Handeling verzenden voor een adaptief formulier {#selectsubmitactionforanadaptiveform}

Voeg vervolgens [!DNL Adobe Sign] -velden toe aan een adaptief formulier, schakel [!DNL Adobe Sign] in vanuit de formuliercontainer, selecteer [!DNL Adobe Sign] -Cloud Service en voeg [!DNL Adobe Sign] Ondertekenaars toe en selecteer een geschikte verzendactie voor het adaptieve formulier. Voor gedetailleerde informatie over adaptieve vormen legt acties voor, zie [ Vormend de Submit actie ](../../forms/using/configuring-submit-actions.md).

Bovendien wordt een adaptief formulier met [!DNL Adobe Sign] alleen verzonden nadat alle ondertekenaars het formulier hebben ondertekend. Gedeeltelijk ondertekend formulier vindt u in de sectie Ondertekenen in behandeling van de portal Formulieren. [!DNL Adobe Sign] de Dienst van de Configuratie houdt opiniepeilend [!DNL Adobe Sign] server bij [ regelmatige intervallen ](../../forms/using/adobe-sign-integration-adaptive-forms.md) om het statuut van handtekeningen te verifiëren. Als alle ondertekenaars het ondertekenen van het formulier hebben voltooid, wordt de verzendactieservice gestart en wordt het formulier verzonden. Als u een aangepaste verzendactie gebruikt en het formulier [!DNL Adobe Sign] gebruikt, werkt u de aangepaste verzendactie bij om de verzendactieservice te gebruiken.

<!-- Remove when forms portal goes live
>[!NOTE]
>
>Data of the adaptive form is stored temporarily on Forms Portal. Use [custom storage for Forms Portal](/help/forms/using/configuring-draft-submission-storage.md). It ensures that the PII (personally identifiable information) data is not stored on AEM servers. 
-->

Uw ervaring voor het ondertekenen van formulieren is gereed. U kunt een voorbeeld van het formulier bekijken om de ondertekeningservaring te verifiëren. In het gepubliceerde formulier worden [!DNL Adobe Sign] blokvelden weergegeven wanneer een ondertekenaar het formulier ontvangt voor ondertekening via een e-mail. Deze ervaring wordt ook wel bekend als een ondertekeningservaring in de vorm van een out-of-form. U kunt een in-vorm het ondertekenen ervaring voor de eerste ondertekenaar, voor gedetailleerde stappen ook vormen zie [ in-vorm het ondertekenen ervaring ](../../forms/using/working-with-adobe-sign.md#create-in-form-signing-experience) creëren.

## Cloud-handtekeningen configureren voor een adaptief formulier {#configure-cloud-signatures-for-an-adaptive-form}

Digitale handtekeningen op basis van cloud of externe handtekeningen zijn een nieuwe generatie digitale handtekeningen die op verschillende computers, mobiele apparaten en het web werken en voldoen aan de hoogste standaarden en waarborgen voor ondertekenaarsverificatie. U kunt een adaptief formulier ondertekenen met digitale handtekeningen op basis van de cloud.

Na [ het uitgeven van adaptieve vormeigenschappen voor het teken van de Adobe ](../../forms/using/working-with-adobe-sign.md#enableadobesign), voer de volgende stappen uit om het gebied van de wolkenhandtekening aan een adaptieve vorm toe te voegen:

1. Sleep de component **[!UICONTROL Adobe Sign Block]** van de componentbrowser naar het aangepaste formulier. De component [!UICONTROL Adobe Sign Block] heeft alle ondersteunde [!DNL Adobe Sign] -velden. Standaard wordt een veld **[!UICONTROL Signature]** toegevoegd aan het aangepaste formulier.

   ![ blok van het Teken ](assets/sign-block-new.png)

1. Selecteer de **[!UICONTROL Adobe Sign Block]** component en selecteer **uitgeven** ![ aem_6_3_edit ](assets/aem_6_3_edit.png) pictogram. Er worden opties weergegeven voor het toevoegen van velden en het opmaken van de weergave van een veld.

   ![ adobe-sign-block-select-fields ](assets/adobe-sign-block-select-fields.png)

   **A.** selecteer en voeg [!DNL Adobe Sign] gebieden toe. **B.** breid het [!DNL Adobe Sign] blok aan volledige het schermmening uit

1. Selecteer het **[!UICONTROL Adobe Sign Field]** ![ aem_6_3_adobesign ](assets/aem_6_3_adobesign.png) pictogram. Er worden opties weergegeven voor het selecteren en toevoegen van [!DNL Adobe Sign] -velden.

   Vouw het **[!UICONTROL Type]** drop-down gebied uit om **[!UICONTROL Digital Signature]** te selecteren en **te selecteren Gedaan** pictogram om het geselecteerde gebied aan [!DNL Adobe Sign] blok toe te voegen.

   ![ Digitale handtekeningen ](assets/digital_signatures_new.png)

   U moet een unieke naam opgeven voor een veld.

   Digitale handtekeningen toepassen op het adaptieve formulier met:

   * De handtekeningen van de wolk: Teken met a [ digitale identiteitskaart ](https://helpx.adobe.com/nl/sign/kb/digital-certificate-providers.html) die door een vertrouwde dienstverlener wordt ontvangen. De optie Cloud Signature is niet beschikbaar voor Adobe Acrobat Sign Solutions for Government.

   * Adobe Acrobat of Reader: Download en open het document met Adobe Acrobat of Reader om het te ondertekenen met een smartcard, USB-token of digitale id op basis van een bestand.

   Nadat u het handtekeningveld voor de cloud aan het adaptieve formulier hebt toegevoegd, voert u de volgende stappen uit om het configuratieproces te voltooien:

   * [Adobe Sign inschakelen voor een adaptief formulier](../../forms/using/working-with-adobe-sign.md#enableadobsignforanadaptiveform)
   * [Selecteer Adobe Sign Cloud Service voor een adaptief formulier](../../forms/using/working-with-adobe-sign.md#selectadobesigncloudserviceforanadaptiveform)
   * [Adobe Sign-ondertekenaars toevoegen aan een adaptief formulier](../../forms/using/working-with-adobe-sign.md#addsignerstoanadaptiveform)
   * [Selecteer Handeling verzenden voor een adaptief formulier](../../forms/using/working-with-adobe-sign.md#selectsubmitactionforanadaptiveform)

## Ervaring voor ondertekenen in formulieren maken {#create-in-form-signing-experience}

Een gebruiker kan ook een adaptief formulier ondertekenen terwijl het formulier wordt ingevuld. Deze ervaring wordt ook wel &#39;in-form signing experience&#39; genoemd. De ondertekeningservaring in formulieren is alleen beschikbaar voor de eerste ondertekenaar in een omgeving met meerdere ondertekenaars. Voer de volgende stappen uit om een ondertekeningservaring in formulieren te maken voor een adaptief formulier:

1. [ voeg en vorm de component van de Stap van de Handtekening toe ](../../forms/using/working-with-adobe-sign.md#add-and-configure-the-signature-step-component).
1. [ voeg de Samenvattende component van de Stap ](../../forms/using/working-with-adobe-sign.md#configure-the-thank-you-page-or-summary-step-component) toe.

![ In-form het Ondertekenen Ervaring ](assets/in_form_signing_experience_new.png)

### De component voor de stap Handtekening toevoegen en configureren {#add-and-configure-the-signature-step-component}

Gebruik de component Handtekeningstap om een gebied op te geven voor de elektronische ondertekening van het ingevulde formulier. Wanneer de sectie met de component Signature Step wordt weergegeven, wordt een ondertekenbare PDF-versie van het ingevulde formulier weergegeven. De component voor de stap Handtekening gebruikt de volledige breedte die beschikbaar is voor het formulier. Het wordt aanbevolen geen andere component op te nemen in de sectie die de component voor de stap Handtekening bevat.

Voer de volgende stappen uit om de component van de Stap van de Handtekening te vormen:

1. Sleep de component **[!UICONTROL Signature Step]** van de browser Components naar het formulier.
1. Selecteer de onlangs toegevoegde component van de stap van de Handtekening en selecteer **vormen** ![ ](assets/configure.png) pictogram. De eigenschappenbrowser wordt geopend en de eigenschappen voor stap Handtekening worden weergegeven. Configureer de volgende eigenschappen:

   * **[!UICONTROL Name]** - Geef de naam van de component op.

   * **[!UICONTROL Title]:** specificeer de unieke titel van de component.
   * **[!UICONTROL Template message]:** Geef het bericht op dat moet worden weergegeven terwijl de PDF van de handtekening wordt geladen. [!DNL Adobe Sign] -services nemen enige tijd in beslag om de PDF van handtekeningen voor te bereiden en te laden.
   * **[!UICONTROL Signing Service]:** selecteer de optie **[!DNL Adobe Sign]** .

   * **[!UICONTROL Use legacy E-sign component]**: Als u de respectieve adaptieve vorm in [ AEM Forms Workspace ](../../forms/using/introduction-html-workspace.md) gebruikt, AEM [!DNL Forms] app, of de onderliggende adaptieve vorm heeft erfenis e-sign component, selecteer **de erfenis E-sign componentenoptie van het Gebruik**.

   * **[!UICONTROL Configuration]**: selecteer een configuratie ([!DNL Adobe Sign] Cloud Service). De drop-down doos is beschikbaar slechts als het **Gebruik erfenis E-sign component** optie wordt toegelaten.

   * **[!UICONTROL CSS Class]**: geef de CSS-klasse voor de component op.

   Selecteer het Gedaan ![ a_6_3_forms_save ](assets/aem_6_3_forms_save.png) pictogram om de veranderingen te bewaren.

   ![ stap van de Handtekening ](assets/signature_step_new.png)

   >[!NOTE]
   >
   >* Wanneer u sleept-en-daling de **[!UICONTROL Signature Step]** component aan de vorm, wordt de **[!UICONTROL Is the signer and the person filling the form same?]** optie automatisch geplaatst aan **ja**. U moet het formulier blijven gebruiken.
   >* Gebruik de component Samenvattingsstap na de component Handtekeningstap voor een optimale ervaring. De stap Overzicht verzendt het formulier automatisch en direct nadat u het ondertekenen van een formulier hebt voltooid in de component Stap handtekening. Als u niet de summiere stap gebruikt, wordt een automatische voorlegging teweeggebracht slechts na het interval dat wordt geplaatst gebruikend de [ Dienst van de Configuratie van Adobe Sign ](../../forms/using/adobe-sign-integration-adaptive-forms.md#configure-adobe-sign-scheduler-to-sync-the-signing-status).
   >
   >Enkele aanbevolen procedures zijn:
   >
   >* Het deelvenster Adaptief formulier met de stap Handtekening bevindt zich altijd in het laatste of tweede laatste deelvenster van een adaptief formulier. Dit kan alleen het tweede laatste deelvenster zijn wanneer het laatste deelvenster de stap Overzicht bevat.
   >* Het deelvenster met de stapcomponent Handtekening of Samenvatting mag geen andere component bevatten.
   >* Adaptieve formulieren met de stap Handtekening kunnen niet worden verzonden.
   >* De verzending van de adaptieve formulieren met de stap Handtekening wordt afgehandeld via een achtergrondservice of de stap Samenvatting. Als er één geconfigureerde ondertekenaar is die het formulier ook invult, heeft de verwerking van het adaptieve formulier via de stap Samenvatting als voordeel dat deze direct evalueert dat de ondertekenaar het formulier heeft ondertekend en de actie Verzenden heeft geactiveerd. Een achtergrondservice heeft meer tijd nodig om te beoordelen of alle geconfigureerde ondertekenaars het formulier hebben ondertekend en de verzending van het adaptieve formulier vertragen.
   >* Ontwerp het formulier zodanig dat een gebruiker niet kan terugnavigeren vanuit een deelvenster dat de stap Handtekening of Overzicht bevat.


### De component voor de prullenbak of overzichtsstap configureren {#configure-the-thank-you-page-or-summary-step-component}

De **Summiere component van de Stap van de Stap** legt automatisch de vorm voor, bevolkt de informatie binnen de aangepaste Summiere pagina, en toont de samenvatting van de voorgelegde vorm. Het krijgt ook de vereiste informatie in de terugkeerkaart. De component SummaryStep gebruikt de volledige breedte die beschikbaar is voor het formulier. Men adviseert om geen andere component op de sectie te hebben die de Summiere component van de Stap bevat.

De ervaring voor het ondertekenen van formulieren is nu gereed. U kunt een voorbeeld van het formulier bekijken om de ondertekeningservaring te verifiëren.

## Veelgestelde vragen {#frequently-asked-questions}

**Q:** U kunt een adaptieve vorm in een andere adaptieve vorm inbedden. Kan het ingesloten adaptieve formulier worden [!DNL Adobe Sign] ingeschakeld?
**Ans:** Nr, AEM [!DNL Forms] steunt het gebruiken van geen adaptieve vorm die een [!DNL Adobe Sign] toegelaten adaptieve vorm voor ondertekening inbedt

**Q:** wanneer ik een adaptieve vorm gebruikend het geavanceerde malplaatje creeer en het voor het uitgeven open, wordt een foutenmelding &quot;Elektronische Handtekening of Ondertekenaars niet correct gevormd.&quot; wordt weergegeven. Hoe kan ik het foutbericht oplossen?
**Ans:** de adaptieve vorm die gebruikend het geavanceerde malplaatje wordt gecreeerd wordt gevormd om te gebruiken [!DNL Adobe Sign]. U lost de fout op door een [!DNL Adobe Sign] cloud-configuratie te maken en te selecteren en een [!DNL Adobe Sign] -ondertekenaar voor het aangepaste formulier te configureren.

**Q:** Kan ik [!DNL Adobe Sign] tekstmarkeringen in een statische tekstcomponent van een adaptieve vorm gebruiken?
**Ans:** ja, kunt u tekstmarkeringen in een tekstcomponent gebruiken om [!DNL Adobe Sign] gebieden aan a [ Document van Verslag ](../../forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md) (Auto geproduceerde document van verslagoptie slechts) toe te voegen toegelaten adaptieve vorm. Om over de procedure en de regels te leren om een tekstmarkering tot stand te brengen, zie [ Documentatie van Adobe Sign ](https://helpx.adobe.com/nl/sign/using/text-tag.html). Houd er rekening mee dat adaptieve formulieren beperkte ondersteuning bieden voor tekstcodes. U kunt de tekstmarkeringen gebruiken om slechts die gebieden tot stand te brengen die [ het Blok van Adobe Sign ](../../forms/using/working-with-adobe-sign.md#configure-cloud-signatures-for-an-adaptive-form) steunt.

**Q:** AEM [!DNL Forms] verstrekt zowel [!UICONTROL Adobe Sign block] als de stapcomponenten van de Handtekening. Kunnen deze gelijktijdig in een adaptieve vorm worden gebruikt?
**Ans:** u kunt beide componenten gelijktijdig in een vorm gebruiken. Hier volgen enkele aanbevelingen voor het gebruik van deze componenten:

**Blok van Adobe Sign:** u kunt [!UICONTROL Adobe Sign Block] gebruiken om [!UICONTROL Adobe Sign] gebieden overal op de adaptieve vorm toe te voegen. Het helpt ook om specifieke gebieden aan ondertekenaars toe te wijzen. Wanneer een adaptief formulier wordt voorvertoond of gepubliceerd, is [!UICONTROL Adobe Sign] Blok standaard niet zichtbaar. Deze blokken zijn alleen beschikbaar in het ondertekenende document. In het ondertekenende document worden alleen de velden ingeschakeld die zijn toegewezen aan een ondertekenaar. [!UICONTROL Adobe Sign] -blok kan worden gebruikt met eerste en volgende ondertekenaars.

**de stapcomponent van de Handtekening:** u kunt de component van de handtekeningsstap gebruiken om in-vorm het ondertekenen ervaring tot stand te brengen. Hiermee kan alleen de eerste ondertekenaar ondertekenen terwijl het formulier wordt ingevuld. Wanneer de sectie met de component Signature Step wordt weergegeven, wordt een ondertekenbare PDF-versie van het formulier weergegeven. Het is doorgaans de laatste of voorlaatste sectie, gevolgd door een overzichtscomponent van een formulier.

## Problemen oplossen {#troubleshoot}

### [!DNL Adobe Sign] mislukte overeenkomsten {#adobe-sign-agreement-failures}

**Uitgave**
Wanneer de service [!DNL Adobe Sign] is geconfigureerd voor een adaptief formulier, kan de service geen [!DNL Adobe Sign] -overeenkomst maken voor het onderliggende adaptieve formulier.

**Resolutie**

* Controleer de [ configuratie van de wolkendienst van Adobe Sign ](../../forms/using/adobe-sign-integration-adaptive-forms.md) die in de adaptieve vorm wordt gebruikt.
* Controleer of de API-toepassing op de [!DNL Adobe Sign] -server die wordt gebruikt om de [!DNL Adobe Sign] Cloud-service te configureren, de vereiste machtigingen heeft.
* Als u meerdere [!DNL Adobe Sign] Cloud-services gebruikt, wijst u de **[!UICONTROL oAuth URL]** van alle services naar hetzelfde **[!UICONTROL Adobe Sign Shard]** .

* Gebruik afzonderlijke e-mailadressen om [!DNL Adobe Sign] -account en voor de eerste ondertekenaar en één ondertekenaar te configureren. Het e-mailadres van de eerste ondertekenaar of de enige ondertekenaar (als er één ondertekenaar is) kan niet hetzelfde zijn als het [!DNL Adobe Sign] -account dat wordt gebruikt om AEM cloudservices te configureren.

### AEM [!DNL Forms] -workflow geconfigureerd voor een [!DNL Adobe Sign] ingeschakeld adaptief formulier wordt niet gestart {#adobe-sign-aem-form-workflow-failures}

**Uitgave**
Wanneer [!DNL Adobe Sign] is geconfigureerd voor een adaptief formulier, wordt de workflow die is geconfigureerd met de optie Invoke [!DNL Forms] Workflow niet gestart.

**Resolutie**

* Wanneer u [!DNL Adobe Sign] zonder de stap Handtekening gebruikt of het formulier handtekeningen van meerdere personen vereist, wacht AEM [!DNL Forms] de server tot de planner heeft bevestigd dat alle personen het formulier hebben ondertekend. De planner dient het adaptieve formulier alleen in nadat alle persoon de ondertekening heeft voltooid en de workflow pas begint nadat het adaptieve formulier met succes is verzonden. U kunt het interval van de [ planner ](adobe-sign-integration-adaptive-forms.md) verkorten om status van vorm te controleren die met snelle intervallen ondertekent en de vormvoorlegging versnelt.


## Verwante artikelen {#related-articles}

* [Adobe Sign integreren met AEM Forms](../../forms/using/adobe-sign-integration-adaptive-forms.md)
* [ Beste praktijken voor het gebruiken van Adobe Sign met adaptieve vormen ](https://medium.com/adobetech/using-adobe-sign-to-e-sign-an-adaptive-form-heres-the-best-way-to-do-it-dc3e15f9b684)
* [ Gebruikend Adobe Sign met AEM Forms (Video) ](https://helpx.adobe.com/experience-manager/kt/forms/using/adobe-sign-integration-feature-video.html)
