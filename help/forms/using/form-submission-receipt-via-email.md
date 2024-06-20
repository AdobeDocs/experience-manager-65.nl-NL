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

Adaptieve formulieren bieden verschillende mogelijkheden [acties verzenden](../../forms/using/configuring-submit-actions.md) workflows voor het verzenden van de formuliergegevens naar verschillende eindpunten.

Bijvoorbeeld de **[!UICONTROL Send email]** Met een handeling verzenden wordt een e-mail verzonden wanneer een adaptief formulier met succes is verzonden. Het kan ook worden geconfigureerd om de formuliergegevens en de PDF in de e-mail te verzenden.

In dit artikel worden de stappen beschreven die nodig zijn om de e-mailactie in te schakelen voor een adaptief formulier en voor verschillende configuraties.

>[!NOTE]
>
>U kunt ook de opdracht **[!UICONTROL Send PDF via email]** om het ingevulde formulier per e-mail te verzenden als een PDF-bijlage. De configuratieopties die beschikbaar zijn voor deze actie zijn gelijk aan de opties die beschikbaar zijn voor de **[!UICONTROL Send email]** handeling. De actie Email PDF is alleen beschikbaar voor op XFA gebaseerde adaptieve formulieren

## E-mailactie verzenden {#email-action}

Met de handeling E-mail verzenden kan een auteur automatisch e-mail verzenden naar een of meer ontvangers wanneer een adaptief formulier is verzonden.

>[!NOTE]
>
>Als u de actie E-mail verzenden wilt gebruiken, moet u de AEM e-mailservice configureren zoals beschreven in [De mailservice configureren](/help/sites-administering/notification.md#configuring-the-mail-service).

### E-mailactie verzenden inschakelen op een adaptief formulier {#enabling-email-action-on-an-adaptive-form}

1. Een adaptief formulier openen in **[!UICONTROL edit]** -modus.

1. In de **[!UICONTROL Content]** tab, selecteert u **[!UICONTROL Form Container]** en selecteert u ![vormen](assets/configure-icon.svg) om de adaptieve formuliereigenschappen weer te geven.

1. In de **[!UICONTROL Submission]** sectie, selecteert u **[!UICONTROL Send email]** van de **[!UICONTROL Submit Action]** vervolgkeuzelijst.

   ![Handelingen verzenden](assets/submission-actions.png)

1. Geef geldige e-mailadressen op in het dialoogvenster **[!UICONTROL To]**, **[!UICONTROL CC]**, en **[!UICONTROL BCC]** velden.

   Geef het onderwerp en de inhoud van de e-mail op in het dialoogvenster **[!UICONTROL Subject]** en **[!UICONTROL Email Template]** respectievelijk velden.

   U kunt ook variabele plaatsaanduidingen opgeven in de velden. In dat geval worden de waarden van de velden verwerkt wanneer het formulier met succes wordt verzonden door een eindgebruiker. Zie voor meer informatie [Aangepaste formulierveldnamen gebruiken om e-mailinhoud dynamisch te maken](../../forms/using/form-submission-receipt-via-email.md#p-using-adaptive-form-field-names-to-dynamically-create-email-content-p).

   Selecteren **[!UICONTROL Include attachments]** als het formulier bestandsbijlagen bevat en u deze bestanden in de e-mail wilt bijvoegen.

   >[!NOTE]
   >
   >Als u **[!UICONTROL Send PDF via Email]** selecteert u de optie Bijlagen opnemen.

1. Klikken ![opslaan](assets/save_icon.svg) om de wijzigingen op te slaan

### Aangepaste formulierveldnamen gebruiken om e-mailinhoud dynamisch te maken {#using-adaptive-form-field-names-to-dynamically-create-email-content}

De veldnamen in een adaptief formulier worden plaatsaanduidingen genoemd die worden vervangen door de waarde van dat veld nadat een gebruiker het formulier heeft verzonden.

In de **[!UICONTROL Send email]** gebruiken, kunt u plaatsaanduidingen gebruiken die worden verwerkt wanneer de handeling wordt uitgevoerd. Dit betekent dat de kopteksten van de e-mail (zoals **[!UICONTROL To]**, **[!UICONTROL CC]**, **[!UICONTROL BCC]**, **[!UICONTROL Subject]**) worden gegenereerd wanneer de gebruiker het formulier verzendt.

Als u een tijdelijke aanduiding wilt definiëren, geeft u `${<field name>}` in een veld na het selecteren **[!UICONTROL Send email]** als handeling verzenden.

Als het formulier bijvoorbeeld het **[!UICONTROL Email address]** veld, naam `email_addr`Voor het vastleggen van de e-mailadres van een gebruiker kunt u het volgende opgeven in het dialoogvenster **[!UICONTROL To]**, **[!UICONTROL CC]**, of **[!UICONTROL BCC]** velden.

`${email_addr}`

Wanneer een gebruiker het formulier verzendt, wordt een e-mailbericht verzonden naar de e-mailid die is ingevoerd in het dialoogvenster `email_addr` veld van het formulier.

>[!NOTE]
>
>U kunt de naam van een veld vinden in het dialoogvenster **[!UICONTROL Edit]** voor het veld.

U kunt ook plaatsaanduidingen voor variabelen gebruiken in het dialoogvenster **[!UICONTROL Subject]** en **[!UICONTROL Email Template]** velden.

Bijvoorbeeld:

`Hi ${first_name} ${last_name},`

`Your form has been received by our department. It usually takes ten business days to process the request.`

`Regards`

`Administrator`

>[!NOTE]
>
>Velden in herhaalbare deelvensters kunnen niet worden gebruikt als plaatsaanduidingen voor variabelen.
