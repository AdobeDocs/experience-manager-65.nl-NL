---
title: Een bevestiging van het verzenden van een formulier verzenden via e-mail
seo-title: Een bevestiging van het verzenden van een formulier verzenden via e-mail
description: Met AEM Forms kunt u de handeling voor het verzenden van e-mail configureren waarmee een bevestiging naar een gebruiker wordt verzonden bij het verzenden van het formulier.
seo-description: Met AEM Forms kunt u de handeling voor het verzenden van e-mail configureren waarmee een bevestiging naar een gebruiker wordt verzonden bij het verzenden van het formulier.
uuid: c80b1ef4-8fe3-48e0-8fc6-3032dc022a38
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: publish
discoiquuid: 574de3d5-69ba-4e2f-a8ab-c59f357e4386
docset: aem65
translation-type: tm+mt
source-git-commit: acc2a3977353386d7e1dfd1344a61d78812fe3fc

---


# Een bevestiging van het verzenden van een formulier verzenden via e-mail {#sending-a-form-submission-acknowledgement-via-email}

## Aangepaste verzending van formuliergegevens {#adaptive-form-data-submission}

Aangepaste formulieren bieden verschillende workflows voor het [verzenden van acties](../../forms/using/configuring-submit-actions.md) buiten de box voor het verzenden van de formuliergegevens naar verschillende eindpunten.

Met de handeling E-mail **** verzenden wordt bijvoorbeeld een e-mail verzonden wanneer een adaptief formulier met succes is verzonden. Het kan ook worden geconfigureerd om de formuliergegevens en de PDF in de e-mail te verzenden.

In dit artikel worden de stappen beschreven die nodig zijn om de e-mailactie in te schakelen voor een adaptief formulier en voor verschillende configuraties.

>[!NOTE]
>
>U kunt ook de optie PDF **[!UICONTROL verzenden via e-mail]** gebruiken om het ingevulde formulier per e-mail te verzenden als PDF-bijlage. De configuratieopties die beschikbaar zijn voor deze actie zijn dezelfde als de opties die beschikbaar zijn voor de actie E-mail **** verzenden. De actie PDF-bestand via e-mail is alleen beschikbaar voor op XFA gebaseerde adaptieve formulieren

## E-mailactie verzenden {#email-action}

Met de handeling E-mail verzenden kan een auteur automatisch e-mail verzenden naar een of meer ontvangers wanneer een adaptief formulier is verzonden.

>[!NOTE]
>
>Als u de actie E-mail verzenden wilt gebruiken, moet u de AEM-mailservice configureren zoals wordt beschreven in [De mailservice](/help/sites-administering/notification.md#configuring-the-mail-service)configureren.

### E-mailactie verzenden inschakelen op een adaptief formulier {#enabling-email-action-on-an-adaptive-form}

1. Open een adaptief formulier in de **[!UICONTROL bewerkingsmodus]** .

1. Tik op het tabblad **[!UICONTROL Inhoud]** op **[!UICONTROL Formuliercontainer]** en tik op ![configureren](assets/configure-icon.svg) om de adaptieve formuliereigenschappen weer te geven.

1. Selecteer in de sectie **[!UICONTROL Verzending]** de optie E-mail **** verzenden in de vervolgkeuzelijst Handeling **** verzenden.

   ![Handelingen verzenden](assets/submission-actions.png)

1. Geef geldige e-mailadressen op in de velden **[!UICONTROL Aan]**, **[!UICONTROL CC]** en **[!UICONTROL BCC]** .

   Geef het onderwerp en de inhoud van de e-mail op in respectievelijk de velden **[!UICONTROL Onderwerp]** en **[!UICONTROL E-mailsjabloon]** .

   U kunt ook variabele plaatsaanduidingen opgeven in de velden. In dat geval worden de waarden van de velden verwerkt wanneer het formulier met succes wordt verzonden door een eindgebruiker. Zie Aangepaste formulierveldnamen [gebruiken om dynamisch e-mailinhoud](../../forms/using/form-submission-receipt-via-email.md#p-using-adaptive-form-field-names-to-dynamically-create-email-content-p)te maken voor meer informatie.

   Selecteer **[!UICONTROL Bijlagen]** opnemen als het formulier bestandsbijlagen bevat en u deze bestanden in de e-mail wilt bijvoegen.

   >[!NOTE]
   >
   >Als u de optie PDF **[!UICONTROL verzenden via e-mail]** kiest, moet u de optie Bijlagen opnemen selecteren.

1. Click ![save](assets/save_icon.svg) to save the changes.

### Aangepaste formulierveldnamen gebruiken om e-mailinhoud dynamisch te maken {#using-adaptive-form-field-names-to-dynamically-create-email-content}

De veldnamen in een adaptief formulier worden plaatsaanduidingen genoemd die worden vervangen door de waarde van dat veld nadat een gebruiker het formulier heeft verzonden.

In de actie E-mail **** verzenden kunt u plaatsaanduidingen gebruiken die worden verwerkt wanneer de handeling wordt uitgevoerd. Dit betekent dat de kopteksten van de e-mail (zoals **[!UICONTROL Aan]**, **[!UICONTROL CC]**, **[!UICONTROL BCC]**, **[!UICONTROL Onderwerp]**) worden gegenereerd wanneer de gebruiker het formulier verzendt.

Als u een tijdelijke aanduiding wilt definiëren, geeft u `${<field name>}` in een veld op nadat u E-mail **** verzenden hebt geselecteerd als Handeling verzenden.

Als het formulier bijvoorbeeld het veld **[!UICONTROL E-mailadres]** bevat met de naam `email_addr`, voor het vastleggen van de e-mailadres van een gebruiker, kunt u het volgende opgeven in de velden **[!UICONTROL Aan]**, **[!UICONTROL CC]** of **[!UICONTROL BCC]** .

`${email_addr}`

Wanneer een gebruiker het formulier verzendt, wordt een e-mail verzonden naar de e-mailid die is ingevoerd in het `email_addr` veld van het formulier.

>[!NOTE]
>
>U kunt de naam van een veld vinden in het dialoogvenster **[!UICONTROL Bewerken]** voor het veld.

U kunt ook plaatsaanduidingen voor variabelen gebruiken in de velden **[!UICONTROL Onderwerp]** en **[!UICONTROL E-mailsjabloon]** .

Bijvoorbeeld:

`Hi ${first_name} ${last_name},`

`Your form has been received by our department. It usually takes ten business days to process the request.`

`Regards`

`Administrator`

>[!NOTE]
>
>Velden in herhaalbare deelvensters kunnen niet worden gebruikt als plaatsaanduidingen voor variabelen.

