---
title: Bijlagen inschakelen voor een HTML5-formulier
seo-title: Bijlagen inschakelen voor een HTML5-formulier
description: Standaard is de ondersteuning voor bijlagen voor HTML5-formulieren uitgeschakeld.
seo-description: Standaard is de ondersteuning voor bijlagen voor HTML5-formulieren uitgeschakeld.
uuid: 2c62ac3e-4b27-46c7-a61d-a805fb5d26fb
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
discoiquuid: 8eebfcd6-0597-44ed-b718-bf9a1baa6c12
feature: Mobile Forms
exl-id: 68912260-179a-4d1b-b944-0a1777c021ac
source-git-commit: 6e2a0f053a1f6989524e9ae2b1dcb001b0397ac6
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 1%

---

# Bijlagen inschakelen voor een HTML5-formulier {#enabling-attachments-for-an-html-form}

U kunt bijlagen uploaden, bekijken en verzenden met HTML5-formulieren. Standaard is de ondersteuning voor bijlagen uitgeschakeld. De ondersteuning voor bijlagen inschakelen:

1. Creeer een [douaneprofiel](/help/forms/using/custom-profile.md) met een `mfAttachmentOptions` multiselect koordbezit. Elke tekenreeks in de eigenschap `mfAttachmentOptions` moet een `property=value`-indeling hebben om opties voor de bestandsbijlage-widget te configureren. De `property` en `value` kunnen om het even welke volgende waarden hebben:

   | Eigenschap | Waarde |
   |--- |---|
   | multiSelect | true of false (standaard true) |
   | fileSizeLimit | Aantal in MBs (2 MBs door gebrek). Bijvoorbeeld 5. |
   | buttonText | Knoptekst voor pop-upvenster (&quot;Bijvoegen&quot; standaard) |
   | accepteren | door komma&#39;s gescheiden lijst met bestandstypen die moeten worden geaccepteerd (&quot;audio/&amp;ast;, video/&amp;ast;, image/&amp;ast;, text/&amp;ast;, .pdf&quot; standaard) |

   Bijvoorbeeld:

   ![configureren, opties](assets/mfAttachmentOptions.png)

   Desgewenst kunt u ook meer aangepaste opties voor de eigenschap `mfAttachmentOptions` opgeven.

   >[!NOTE]
   >
   >In Microsoft Internet Explorer 9 kunnen gebruikers bestanden bijvoegen die groter zijn dan de opgegeven limiet. Het is een bekend probleem.

1. Gebruik de [metagegevenseditor](/help/forms/using/manage-form-metadata.md) om het aangepaste profiel te selecteren dat u hierboven hebt gemaakt voor HTML 5-formulieren.
1. U geeft de formuliersjabloon weer met een aangepast profiel en het pictogram Bijlagen wordt weergegeven op de werkbalk Formulieren.

   >[!NOTE]
   >
   >Het portal Formulieren bevat een aangepast profiel met de mogelijkheden voor concepten en bijlagen ingeschakeld. Zie [HTML5-formulieren opslaan als concept](/help/forms/using/saving-html5-form-draft.md) voor meer informatie over het profiel **Opslaan als concept**.

1. Klik op het pictogram voor bijlagen en er verschijnt een dialoogvenster voor het selecteren van bijlagen. Blader naar de bijlage en selecteer deze en klik op **Bijvoegen**.

   >[!NOTE]
   >
   >Klik op de naam van een bijlage om een voorbeeld van een bijlage weer te geven.

   >[!NOTE]
   >
   >De optie voor het voorvertonen van bestanden is niet beschikbaar voor anonieme gebruikers.

## Indeling voor het verzenden van bijlagen {#attachment-submission-format}

Als bijlagen zijn ingeschakeld, verzendt het HTML5-formulier meerdelige gegevens. De uit meerdere delen bestaande verzendingsgegevens bestaan uit twee delen **dataXml** en **bijlagen**.

>[!NOTE]
>
>Als de optie `mfAllowAttachments` voor achterwaartse compatibiliteit is uitgeschakeld, worden de meerdelige gegevens niet verzonden door de HTML5-formulieren. Het verzendt eenvoudige gegevens-xml in **application/xml** formaat.

Als de markering mfAllowAttachments is ingeschakeld, plaatst de [service voor serviceproxy verzenden](/help/forms/using/service-proxy.md) ook meerdelige gegevens met dataXml en bijlagen.
