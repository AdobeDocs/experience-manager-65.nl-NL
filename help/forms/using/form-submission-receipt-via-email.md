---
title: Een bevestiging van het verzenden van een formulier verzenden via e-mail
seo-title: Een bevestiging van het verzenden van een formulier verzenden via e-mail
description: Met AEM Forms kunt u de handeling voor het verzenden van e-mail configureren. Hiermee wordt een bevestiging verzonden naar een gebruiker bij het verzenden van het formulier.
seo-description: Met AEM Forms kunt u de handeling voor het verzenden van e-mail configureren. Hiermee wordt een bevestiging verzonden naar een gebruiker bij het verzenden van het formulier.
uuid: c80b1ef4-8fe3-48e0-8fc6-3032dc022a38
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: publish
discoiquuid: 574de3d5-69ba-4e2f-a8ab-c59f357e4386
docset: aem65
translation-type: tm+mt
source-git-commit: acc2a3977353386d7e1dfd1344a61d78812fe3fc
workflow-type: tm+mt
source-wordcount: '528'
ht-degree: 0%

---


# Een bevestiging van het verzenden van een formulier verzenden via e-mail {#sending-a-form-submission-acknowledgement-via-email}

## Aangepaste verzending van formuliergegevens {#adaptive-form-data-submission}

Aangepaste formulieren bieden verschillende workflows voor het verzenden van formuliergegevens naar verschillende eindpunten voor het verzenden van [acties](../../forms/using/configuring-submit-actions.md).

Met de verzendactie **[!UICONTROL Send email]** wordt bijvoorbeeld een e-mail verzonden wanneer een adaptief formulier met succes is verzonden. Het kan ook worden geconfigureerd om de formuliergegevens en de PDF in de e-mail te verzenden.

In dit artikel worden de stappen beschreven die nodig zijn om de e-mailactie in te schakelen voor een adaptief formulier en voor verschillende configuraties.

>[!NOTE]
>
>Met de optie **[!UICONTROL Send PDF via email]** kunt u het ingevulde formulier ook per e-mail verzenden als PDF-bijlage. De configuratieopties die beschikbaar zijn voor deze actie zijn gelijk aan de opties die beschikbaar zijn voor de handeling **[!UICONTROL Send email]**. De actie PDF-bestand via e-mail is alleen beschikbaar voor op XFA gebaseerde adaptieve formulieren

## E-mailactie {#email-action} verzenden

Met de handeling E-mail verzenden kan een auteur automatisch e-mail verzenden naar een of meer ontvangers wanneer een adaptief formulier is verzonden.

>[!NOTE]
>
>Om de Send e-mailactie te gebruiken, moet u de AEM e-maildienst vormen zoals die in [wordt beschreven het Vormen van de postdienst](/help/sites-administering/notification.md#configuring-the-mail-service).

### E-mailactie verzenden inschakelen op een adaptief formulier {#enabling-email-action-on-an-adaptive-form}

1. Open een adaptief formulier in de modus **[!UICONTROL edit]**.

1. Tik op het tabblad **[!UICONTROL Content]** op **[!UICONTROL Form Container]** en tik ![configure](assets/configure-icon.svg) om de adaptieve formuliereigenschappen weer te geven.

1. Selecteer in de sectie **[!UICONTROL Submission]** **[!UICONTROL Send email]** in de vervolgkeuzelijst **[!UICONTROL Submit Action]**.

   ![Handelingen verzenden](assets/submission-actions.png)

1. Geef geldige e-mailadressen op in de velden **[!UICONTROL To]**, **[!UICONTROL CC]** en **[!UICONTROL BCC]**.

   Geef het onderwerp en de hoofdtekst van de e-mail op in respectievelijk de velden **[!UICONTROL Subject]** en **[!UICONTROL Email Template]**.

   U kunt ook variabele plaatsaanduidingen opgeven in de velden. In dat geval worden de waarden van de velden verwerkt wanneer het formulier met succes wordt verzonden door een eindgebruiker. Zie [Aangepaste formulierveldnamen gebruiken om dynamisch e-mailinhoud te maken](../../forms/using/form-submission-receipt-via-email.md#p-using-adaptive-form-field-names-to-dynamically-create-email-content-p) voor meer informatie.

   Selecteer **[!UICONTROL Include attachments]** als het formulier bestandsbijlagen bevat en u deze bestanden in de e-mail wilt bijvoegen.

   >[!NOTE]
   >
   >Als u de optie **[!UICONTROL Send PDF via Email]** kiest, moet u de optie Inclusief bijlagen selecteren.

1. Klik ![save](assets/save_icon.svg) om de wijzigingen op te slaan.

### Aangepaste formulierveldnamen gebruiken om e-mailinhoud dynamisch te maken {#using-adaptive-form-field-names-to-dynamically-create-email-content}

De veldnamen in een adaptief formulier worden plaatsaanduidingen genoemd die worden vervangen door de waarde van dat veld nadat een gebruiker het formulier heeft verzonden.

In de **[!UICONTROL Send email]** actie, kunt u placeholders gebruiken die worden verwerkt wanneer de actie wordt uitgevoerd. Dit betekent dat de kopteksten van de e-mail (zoals **[!UICONTROL To]**, **[!UICONTROL CC]**, **[!UICONTROL BCC]**, **[!UICONTROL Subject]**) worden gegenereerd wanneer de gebruiker het formulier verzendt.

Als u een tijdelijke aanduiding wilt definiëren, geeft u `${<field name>}` in een veld op nadat u **[!UICONTROL Send email]** hebt geselecteerd als Verzendhandeling.

Als het formulier bijvoorbeeld het veld **[!UICONTROL Email address]** bevat met de naam `email_addr` voor het vastleggen van de e-mailadres van een gebruiker, kunt u het volgende opgeven in de velden **[!UICONTROL To]**, **[!UICONTROL CC]** of **[!UICONTROL BCC]**.

`${email_addr}`

Wanneer een gebruiker het formulier verzendt, wordt een e-mail verzonden naar de e-mailid die is ingevoerd in het veld `email_addr` van het formulier.

>[!NOTE]
>
>U kunt de naam van een veld vinden in het dialoogvenster **[!UICONTROL Edit]** voor het veld.

U kunt ook plaatsaanduidingen voor variabelen gebruiken in de velden **[!UICONTROL Subject]** en **[!UICONTROL Email Template]**.

Bijvoorbeeld:

`Hi ${first_name} ${last_name},`

`Your form has been received by our department. It usually takes ten business days to process the request.`

`Regards`

`Administrator`

>[!NOTE]
>
>Velden in herhaalbare deelvensters kunnen niet worden gebruikt als plaatsaanduidingen voor variabelen.

