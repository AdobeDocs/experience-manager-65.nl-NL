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
translation-type: tm+mt
source-git-commit: 00e14be8a0775149b3ee7ce8cd781dd7f1e49e4f
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---


# Bijlagen inschakelen voor een HTML5-formulier {#enabling-attachments-for-an-html-form}

U kunt bijlagen uploaden, bekijken en verzenden met HTML5-formulieren. Standaard is de ondersteuning voor bijlagen uitgeschakeld. De ondersteuning voor bijlagen inschakelen:

1. Maak een [aangepast profiel](/help/forms/using/custom-profile.md) met multiselect-tekenreekseigenschap `mfAttachmentOptions`.
1. Geef in het aangepaste profiel de eigenschappen `fileSizeLimit`, `multiSelect` en `buttonTex`t op om opties voor de bestandsbijlage-widget te configureren. Desgewenst kunt u ook meer aangepaste eigenschappen opgeven.

1. Gebruik de volgende configuraties in het aangepaste profiel:

   * **multiSelect** -> true of false (standaard true)
   * **fileSizeLimit** -> value_in_mb (say 5) (standaard 2 MB)
   * **buttonText** -> Knoptekst voor pop-upvenster (&quot;Bijvoegen&quot; standaard)
   * **Accepteren** -> bestandstypen die worden geaccepteerd (&quot;audio/&amp;ast;, video/&amp;ast;, afbeelding/&amp;ast;, tekst/&amp;ast;, standaard .pdf&quot;)

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

## Indeling {#attachment-submission-format} voor het verzenden van bijlagen

Als bijlagen zijn ingeschakeld, verzendt het HTML5-formulier meerdelige gegevens. De uit meerdere delen bestaande verzendingsgegevens bestaan uit twee delen **dataXml** en **bijlagen**.

>[!NOTE]
>
>Als de optie `mfAllowAttachments` voor achterwaartse compatibiliteit is uitgeschakeld, worden de meerdelige gegevens niet verzonden door de HTML5-formulieren. Het verzendt eenvoudige gegevens-xml in **application/xml** formaat.

Als de markering mfAllowAttachments is ingeschakeld, plaatst de [service voor serviceproxy verzenden](/help/forms/using/service-proxy.md) ook meerdelige gegevens met dataXml en bijlagen.
