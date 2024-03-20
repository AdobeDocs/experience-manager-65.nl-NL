---
title: Bijlagen inschakelen voor een HTML5-formulier
description: Standaard is de ondersteuning voor bijlagen voor HTML5-formulieren uitgeschakeld.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
discoiquuid: 8eebfcd6-0597-44ed-b718-bf9a1baa6c12
feature: HTML5 Forms
exl-id: 68912260-179a-4d1b-b944-0a1777c021ac
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# Bijlagen inschakelen voor een HTML5-formulier {#enabling-attachments-for-an-html-form}

U kunt bijlagen uploaden, een voorbeeld bekijken en verzenden met HTML5-formulieren. Standaard is de ondersteuning voor bijlagen uitgeschakeld. De ondersteuning voor bijlagen inschakelen:

1. Een [aangepast profiel](/help/forms/using/custom-profile.md) met een `mfAttachmentOptions` multiselect, tekenreekseigenschap. Elke tekenreeks in de `mfAttachmentOptions` eigenschap moet een `property=value` indeling voor het configureren van opties voor de bestandsbijlage-widget. De `property` en `value` kan een van de volgende waarden hebben:

   | Eigenschap | Waarde |
   |--- |---|
   | multiSelect | true of false (standaard true) |
   | fileSizeLimit | Aantal in MBs (2 MBs door gebrek). Bijvoorbeeld 5. |
   | buttonText | Knoptekst voor pop-upvenster (&quot;Bijvoegen&quot; standaard) |
   | accepteren | door komma&#39;s gescheiden lijst met bestandstypen die moeten worden geaccepteerd (&quot;audio/&amp;ast;, video/&amp;ast;, afbeelding/&amp;ast;, tekst/&amp;ast; standaard .pdf&quot;) |

   Bijvoorbeeld:

   ![configureren, opties](assets/mfAttachmentOptions.png)

   U kunt desgewenst ook meer aangepaste opties voor de `mfAttachmentOptions` eigenschap.

   >[!NOTE]
   >
   >In Microsoft Internet Explorer 9 kunnen gebruikers bestanden bijvoegen die groter zijn dan de opgegeven limiet. Het is een bekend probleem.

1. Gebruik de [metagegevenseditor](/help/forms/using/manage-form-metadata.md) om het aangepaste profiel te selecteren dat u hierboven hebt gemaakt voor HTML 5-formulieren.
1. U geeft de formuliersjabloon weer met een aangepast profiel en het pictogram Bijlagen wordt weergegeven op de werkbalk Formulieren.

   >[!NOTE]
   >
   >Het portal Formulieren bevat een aangepast profiel met de mogelijkheden voor concepten en bijlagen ingeschakeld. Voor meer informatie over de **Opslaan als concept** profiel, zie [HTML5-formulieren opslaan als concept](/help/forms/using/saving-html5-form-draft.md).

1. Klik op het pictogram voor bijlagen en er verschijnt een dialoogvenster voor het selecteren van bijlagen. Blader en selecteer de bijlage en klik op **Koppelen**.

   >[!NOTE]
   >
   >Klik op de naam van een bijlage om een voorbeeld van een bijlage weer te geven.

   >[!NOTE]
   >
   >De optie voor het voorvertonen van bestanden is niet beschikbaar voor anonieme gebruikers.

## Indeling voor het verzenden van bijlagen {#attachment-submission-format}

Als bijlagen zijn ingeschakeld, verzendt HTML5-formulier meerdelige gegevens. De uit meerdere delen bestaande indieningsgegevens bestaan uit twee delen **dataXml** en **bijlagen**.

>[!NOTE]
>
>Voor achterwaartse compatibiliteit, als `mfAllowAttachments` is uitgeschakeld, worden de meerdelige gegevens niet verzonden door de HTML5-formulieren. Het verzendt eenvoudige gegevens-xml in **application/xml** gebruiken.

Als de markering mfAllowAttachments is ingeschakeld, [service-proxy verzenden](/help/forms/using/service-proxy.md) Hiermee worden ook meerdelige gegevens gepost met dataXml en bijlagen.
