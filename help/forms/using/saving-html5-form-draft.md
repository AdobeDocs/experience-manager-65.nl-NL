---
title: Een HTML5-formulier opslaan als concept
description: Sla een HTML5-formulier op als concept en hervat het invullen van het formulier in een later stadium.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
discoiquuid: 445e24af-cd1a-414d-bd01-9feb6631bbef
feature: HTML5 Forms
exl-id: a9879445-d626-4279-8a95-a9009294b483
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# Een HTML5-formulier opslaan als concept {#saving-an-html-form-as-a-draft}

U kunt een HTML5-formulier opslaan als concept en het invullen van het formulier later hervatten. Met Forms Portal kunnen gebruikers een HTML5-formulier opslaan en herstellen. Voeg de volgende configuraties toe aan het profielknooppunt om de functie Opslaan als concept in te schakelen:

## Aangepast profiel om de functie Opslaan als concept toe te staan {#custom-profile-to-allow-save-as-draft-feature}

AEM Forms biedt een **Opslaan als concept** profiel. U kunt een formulier weergeven met het profiel Opslaan als concept om de conceptfunctionaliteit voor een HTML5-formulier in te schakelen. U kunt het HTML-renderprofiel voor een formulier opgeven in [Forms Manager](/help/forms/using/introduction-managing-forms.md).

Opslaan als concept inschakelen voor uw bestaande [aangepast profiel](/help/forms/using/custom-profile.md)voegt u de volgende eigenschappen toe aan het aangepaste profielknooppunt:

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschapnaam</strong></td>
   <td><strong>Type</strong></td>
   <td><strong>Waarde</strong></td>
   <td><strong>Beschrijving</strong></td>
  </tr>
  <tr>
   <td>mfAllowFPDraft</td>
   <td>String</td>
   <td>true</td>
   <td><p>Hiermee wordt het opslaan als concept ingeschakeld</p> <p>voor dit profiel.</p> </td>
  </tr>
  <tr>
   <td>mfAllowAttachments</td>
   <td>String</td>
   <td>true</td>
   <td><p>Hiermee kunt u bijlagen uploaden</p> <p>met dit profiel.</p> </td>
  </tr>
 </tbody>
</table>

## Opslag en aanbieding opstellen {#drafts-storage-and-listing}

Nadat u de functie Opslaan als concept hebt ingeschakeld voor een formulier, wordt het formulier weergegeven in het dialoogvenster [Concepten en verzendingscomponent](/help/forms/using/draft-submission-component.md). U kunt het opgeslagen formulier ophalen en invullen met de component Concept en Verzending.

Voeg de volgende eigenschap toe aan het profielknooppunt om formuliervermelding in te schakelen voor de component Concept en Verzending:

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschapnaam</strong></td>
   <td><strong>Type</strong></td>
   <td><strong>Waarde</strong></td>
   <td><strong>Beschrijving</strong></td>
  </tr>
  <tr>
   <td>fp.enablePortalSubmit</td>
   <td>String</td>
   <td>true</td>
   <td>Concepten en formulieren weergeven in<br /> Forms Portal Concepten en verzendingen na verzending</td>
  </tr>
 </tbody>
</table>

Standaard slaat AEM Forms de gebruikersgegevens die zijn gekoppeld aan het concept en de verzending van een formulier op in het knooppunt /content/forms/fp in het exemplaar Publish. U kunt uw aangepaste opslagprovider toevoegen. Zie voor meer informatie [Aangepaste opslag voor component Concepten en verzendingen](/help/forms/using/adding-custom-storage-provider-forms.md).
