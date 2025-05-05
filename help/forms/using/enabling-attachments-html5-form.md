---
title: Bijlagen inschakelen voor een HTML5-formulier
description: Standaard is de ondersteuning voor bijlagen voor HTML5-formulieren uitgeschakeld.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
discoiquuid: 8eebfcd6-0597-44ed-b718-bf9a1baa6c12
feature: HTML5 Forms,Mobile Forms
exl-id: 68912260-179a-4d1b-b944-0a1777c021ac
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# Bijlagen inschakelen voor een HTML5-formulier {#enabling-attachments-for-an-html-form}

U kunt bijlagen uploaden, een voorbeeld bekijken en verzenden met HTML5-formulieren. Standaard is de ondersteuning voor bijlagen uitgeschakeld. De ondersteuning voor bijlagen inschakelen:

1. Creeer a [ douaneprofiel ](/help/forms/using/custom-profile.md) met a `mfAttachmentOptions` multiselect koordbezit. Elke tekenreeks in de eigenschap `mfAttachmentOptions` moet een `property=value` -indeling hebben om opties voor de bestandsbijlage-widget te configureren. De waarden `property` en `value` kunnen een van de volgende waarden hebben:

   | Eigenschap | Waarde |
   |--- |---|
   | multiSelect | true of false (standaard true) |
   | fileSizeLimit | Aantal in MBs (2 MBs door gebrek). Bijvoorbeeld 5. |
   | buttonText | Knoptekst voor pop-upvenster (&quot;Bijvoegen&quot; standaard) |
   | accepteren | door komma&#39;s gescheiden lijst met bestandstypen die moeten worden geaccepteerd (&quot;audio/&ast;, video/&ast;, image/&ast;, text/&ast;, .pdf&quot; standaard) |

   Bijvoorbeeld:

   ![ vormt opties ](assets/mfAttachmentOptions.png)

   Desgewenst kunt u ook meer aangepaste opties voor de eigenschap `mfAttachmentOptions` opgeven.

   >[!NOTE]
   >
   >In Microsoft Internet Explorer 9 kunnen gebruikers bestanden bijvoegen die groter zijn dan de opgegeven limiet. Het is een bekend probleem.

1. Gebruik de [ meta-gegevensredacteur ](/help/forms/using/manage-form-metadata.md) om het douaneprofiel te selecteren dat u hierboven voor HTML 5 vormen hebt gecreeerd.
1. U geeft de formuliersjabloon weer met een aangepast profiel en het pictogram Bijlagen wordt weergegeven op de werkbalk Formulieren.

   >[!NOTE]
   >
   >Het portal Formulieren bevat een aangepast profiel met de mogelijkheden voor concepten en bijlagen ingeschakeld. Voor meer informatie over **sparen als Ontwerp** profiel, zie [ het Opslaan van vormen HTML5 als ontwerp ](/help/forms/using/saving-html5-form-draft.md).

1. Klik op het pictogram voor bijlagen en er verschijnt een dialoogvenster voor het selecteren van bijlagen. Blader en selecteer de gehechtheid en klik **Band**.

   >[!NOTE]
   >
   >Klik op de naam van een bijlage om een voorbeeld van een bijlage weer te geven.

   >[!NOTE]
   >
   >De optie voor het voorvertonen van bestanden is niet beschikbaar voor anonieme gebruikers.

## Indeling voor het verzenden van bijlagen {#attachment-submission-format}

Als bijlagen zijn ingeschakeld, verzendt HTML5-formulier meerdelige gegevens. De multipart voorleggingsgegevens hebben twee delen **dataXml** en **gehechtheid**.

>[!NOTE]
>
>Als de optie `mfAllowAttachments` is uitgeschakeld, verzendt de HTML5-formulieren de meerdelige gegevens niet voor achterwaartse compatibiliteit. Het verzendt eenvoudige gegevens xml in **toepassing/xml** formaat.

Als de vlag mfAllowAttachments wordt aangezet, [ voorlegt de dienst van de de dienstvolmacht ](/help/forms/using/service-proxy.md) ook posten multipart gegevens met dataXml en gehechtheid.
