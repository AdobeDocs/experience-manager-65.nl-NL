---
title: Een bevestiging van het verzenden van een formulier verzenden via e-mail
description: Met AEM Forms kunt u de handeling voor het verzenden van e-mail configureren. Hiermee wordt een bevestiging verzonden naar een gebruiker bij het verzenden van het formulier.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: publish
docset: aem65
exl-id: bca4044a-18a9-4b97-92de-eff1e9a840f9
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: Admin, User, Developer
source-git-commit: e821be5233fd5f6688507096790d219d25903892
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 0%

---

# Een bevestiging van het verzenden van een formulier verzenden via e-mail {#sending-a-form-submission-acknowledgement-via-email}

## Aangepaste verzending van formuliergegevens {#adaptive-form-data-submission}

De adaptieve vormen verstrekken verscheidene uit-van-de-doos [&#x200B; acties &#x200B;](../../forms/using/configuring-submit-actions.md) werkschema&#39;s voor het voorleggen van de vormgegevens aan verschillende eindpunten.

Met de handeling **[!UICONTROL Send email]** Verzenden wordt bijvoorbeeld een e-mail verzonden wanneer een adaptief formulier met succes is verzonden. Het kan ook worden geconfigureerd om de formuliergegevens en de PDF in de e-mail te verzenden.

In dit artikel worden de stappen beschreven die nodig zijn om de e-mailactie in te schakelen voor een adaptief formulier en voor verschillende configuraties.

>[!NOTE]
>
>U kunt de optie **[!UICONTROL Send PDF via email]** ook gebruiken om het ingevulde formulier per e-mail te verzenden als een PDF-bijlage. De configuratieopties die beschikbaar zijn voor deze actie, zijn gelijk aan de opties die beschikbaar zijn voor de **[!UICONTROL Send email]** -actie. De actie Email PDF is alleen beschikbaar voor op XFA gebaseerde adaptieve formulieren

## E-mailactie verzenden {#email-action}

Met de handeling E-mail verzenden kan een auteur automatisch e-mail verzenden naar een of meer ontvangers wanneer een adaptief formulier is verzonden.

>[!NOTE]
>
>Om de Send e-mailactie te gebruiken, moet u de AEM postdienst vormen zoals die in [&#x200B; wordt beschreven het Vormen van de postdienst &#x200B;](/help/sites-administering/notification.md#configuring-the-mail-service).

### E-mailactie verzenden inschakelen op een adaptief formulier {#enabling-email-action-on-an-adaptive-form}

1. Open een adaptief formulier in de modus **[!UICONTROL edit]** .

1. In het **[!UICONTROL Content]** lusje, selecteer **[!UICONTROL Form Container]** en selecteer ![&#x200B; vormen &#x200B;](assets/configure-icon.svg) om de adaptieve vormeigenschappen te bekijken.

1. Selecteer **[!UICONTROL Send email]** in de vervolgkeuzelijst **[!UICONTROL Submit Action]** in de sectie **[!UICONTROL Submission]** .

   ![&#x200B; voorlegt acties &#x200B;](assets/submission-actions.png)

1. Geef geldige e-mailadressen op in de velden **[!UICONTROL To]** , **[!UICONTROL CC]** en **[!UICONTROL BCC]** .

   Geef het onderwerp en de hoofdtekst van de e-mail op in respectievelijk de velden **[!UICONTROL Subject]** en **[!UICONTROL Email Template]** .

   U kunt ook variabele plaatsaanduidingen opgeven in de velden. In dat geval worden de waarden van de velden verwerkt wanneer het formulier met succes wordt verzonden door een eindgebruiker. Voor meer informatie, zie [&#x200B; Gebruikend de adaptieve namen van het vormgebied om e-mailinhoud &#x200B;](../../forms/using/form-submission-receipt-via-email.md#p-using-adaptive-form-field-names-to-dynamically-create-email-content-p) dynamisch tot stand te brengen.

   Selecteer **[!UICONTROL Include attachments]** als het formulier bestandsbijlagen bevat en u deze bestanden in de e-mail wilt bijvoegen.

   >[!NOTE]
   >
   >Als u de optie **[!UICONTROL Send PDF via Email]** kiest, moet u de optie Bijlagen opnemen selecteren.

1. Klik ![&#x200B; sparen &#x200B;](assets/save_icon.svg) om de veranderingen te bewaren.

### Aangepaste formulierveldnamen gebruiken om e-mailinhoud dynamisch te maken {#using-adaptive-form-field-names-to-dynamically-create-email-content}

De veldnamen in een adaptief formulier worden plaatsaanduidingen genoemd die worden vervangen door de waarde van dat veld nadat een gebruiker het formulier heeft verzonden.

In de handeling **[!UICONTROL Send email]** kunt u plaatsaanduidingen gebruiken die worden verwerkt wanneer de handeling wordt uitgevoerd. Dit betekent dat de kopteksten van de e-mail (zoals **[!UICONTROL To]** , **[!UICONTROL CC]** , **[!UICONTROL BCC]** , **[!UICONTROL Subject]** ) worden gegenereerd wanneer de gebruiker het formulier verzendt.

Als u een plaatsaanduiding wilt definiëren, geeft u `${<field name>}` op in een veld nadat u **[!UICONTROL Send email]** hebt geselecteerd als de handeling Verzenden.

Als het formulier bijvoorbeeld het veld **[!UICONTROL Email address]** met de naam `email_addr` bevat voor het vastleggen van de e-mailadres van een gebruiker, kunt u het volgende opgeven in de velden **[!UICONTROL To]** , **[!UICONTROL CC]** of **[!UICONTROL BCC]** .

`${email_addr}`

Wanneer een gebruiker het formulier verzendt, wordt een e-mail verzonden naar de e-mailid die is ingevoerd in het veld `email_addr` van het formulier.

>[!NOTE]
>
>U kunt de naam van een veld vinden in het dialoogvenster **[!UICONTROL Edit]** voor het veld.

U kunt ook plaatsaanduidingen voor variabelen gebruiken in de velden **[!UICONTROL Subject]** en **[!UICONTROL Email Template]** .

Bijvoorbeeld:

`Hi ${first_name} ${last_name},`

`Your form has been received by our department. It usually takes ten business days to process the request.`

`Regards`

`Administrator`

>[!NOTE]
>
>Velden in herhaalbare deelvensters kunnen niet worden gebruikt als plaatsaanduidingen voor variabelen.
