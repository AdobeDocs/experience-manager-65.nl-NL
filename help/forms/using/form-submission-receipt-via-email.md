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
source-git-commit: b97452eb42275d889a82eb9364b5daf7075fcc41

---


# Een bevestiging van het verzenden van een formulier verzenden via e-mail{#sending-a-form-submission-acknowledgement-via-email}

## Aangepaste verzending van formuliergegevens {#adaptive-form-data-submission}

Aangepaste formulieren bieden verschillende workflows voor het [verzenden van acties](../../forms/using/configuring-submit-actions.md) buiten de box voor het verzenden van de formuliergegevens naar verschillende eindpunten.

Met de handeling **E-mail verzenden** verzendt u bijvoorbeeld een e-mail wanneer een adaptief formulier met succes is verzonden. Het kan ook worden geconfigureerd om de formuliergegevens en de PDF in de e-mail te verzenden.

In dit artikel worden de stappen beschreven die nodig zijn om de e-mailactie in te schakelen voor een adaptief formulier en voor verschillende configuraties.

>[!NOTE]
>
>U kunt de PDF- **actie** e-mailen ook gebruiken om het ingevulde formulier per e-mail te verzenden als PDF-bijlage. De configuratieopties die beschikbaar zijn voor deze actie zijn gelijk aan de opties die beschikbaar zijn voor de e-mailactie. De actie PDF-bestand via e-mail is alleen beschikbaar voor op XFA gebaseerde adaptieve formulieren

## E-mailactie {#email-action}

Met de e-mailactie kan een auteur automatisch e-mail verzenden naar een of meer ontvangers wanneer een adaptief formulier is verzonden.

>[!NOTE]
>
>Als u de actie E-mail wilt gebruiken, moet u de AEM-mailservice configureren zoals wordt beschreven in [De mailservice](/help/sites-administering/notification.md#configuring-the-mail-service)configureren.

### E-mailactie inschakelen op een adaptief formulier {#enabling-email-action-on-an-adaptive-form}

1. Open een adaptief formulier in de bewerkingsmodus.

1. Klik op **Bewerken** naast het **begin van een werkbalk Adaptief formulier** .

   Het dialoogvenster Component bewerken wordt geopend.

   ![Dialoogvenster van component bewerken voor een adaptief formulier](assets/start_of_adp_form.png)

1. Selecteer het tabblad Handelingen **** verzenden en kies **E-mailactie** in de vervolgkeuzelijst Handeling verzenden.

   Op het tabblad vindt u de opties voor het configureren van de e-mailactie voor het huidige formulier.

   ![Tabblad Handelingen verzenden](assets/dialog.png)

1. Geef geldige e-mailadressen op in de velden Mailto, CC en BCC.

   Geef het onderwerp en de inhoud van de e-mail op in de sjabloonvelden Onderwerp en E-mail.

   U kunt ook variabele plaatsaanduidingen opgeven in de velden. In dat geval worden de waarden van de velden verwerkt wanneer het formulier met succes wordt verzonden door een eindgebruiker. Zie Aangepaste formulierveldnamen [gebruiken om dynamisch e-mailinhoud](../../forms/using/form-submission-receipt-via-email.md#p-using-adaptive-form-field-names-to-dynamically-create-email-content-p)te maken voor meer informatie.

   Selecteer Inclusief bijlagen als het formulier bestandsbijlagen bevat en u deze bestanden in de e-mail wilt bijvoegen.

   >[!NOTE]
   >
   >Als u de actie **PDF-** e-mail kiest, moet u de optie Bijlagen opnemen selecteren.

1. Click **OK** to save the changes.

### Aangepaste formulierveldnamen gebruiken om e-mailinhoud dynamisch te maken {#using-adaptive-form-field-names-to-dynamically-create-email-content}

De veldnamen in een adaptief formulier worden plaatsaanduidingen genoemd die worden vervangen door de waarde van dat veld nadat een gebruiker het formulier heeft verzonden.

Op het tabblad E-mailactie kunt u plaatsaanduidingen gebruiken die worden verwerkt wanneer de handeling wordt uitgevoerd. Dit betekent dat de kopteksten van de e-mail (zoals Mailto, CC, BCC, onderwerp) worden gegenereerd wanneer de gebruiker het formulier verzendt.

Als u een tijdelijke aanduiding wilt definiëren, geeft u deze op in een veld op het tabblad Handelingen verzenden. `${<field name>}`

Als het formulier bijvoorbeeld het veld **E-mailadres** bevat met de naam `email_addr`, voor het vastleggen van de e-mailadres van een gebruiker, kunt u het volgende opgeven in de velden Mailto, CC of BCC.

`${email_addr}`

Wanneer een gebruiker het formulier verzendt, wordt een e-mail verzonden naar de e-mailid die is ingevoerd in het `email_addr` veld van het formulier.

>[!NOTE]
>
>U kunt de naam van een veld vinden in het dialoogvenster **Bewerken** voor het veld.

U kunt ook plaatsaanduidingen voor variabelen gebruiken in de sjabloonvelden **Onderwerp** en **E-mail** .

Bijvoorbeeld:

`Hi ${first_name} ${last_name},`

`Your form has been received by our department. It usually takes ten business days to process the request.`

`Regards`

`Administrator`

>[!NOTE]
>
>Velden in herhaalbare deelvensters kunnen niet worden gebruikt als plaatsaanduidingen voor variabelen.

