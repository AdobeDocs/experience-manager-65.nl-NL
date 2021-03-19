---
title: Een HTML5-formulier opslaan als concept
seo-title: Een HTML5-formulier opslaan als concept
description: Sla een HTML5-formulier op als concept en hervat het invullen van het formulier in een later stadium.
seo-description: Sla een HTML5-formulier op als concept en hervat het invullen van het formulier in een later stadium.
uuid: 70cd5f6f-f125-470c-8cee-ee14d2127713
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
discoiquuid: 445e24af-cd1a-414d-bd01-9feb6631bbef
feature: Mobile Forms
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 2%

---


# Een HTML5-formulier opslaan als concept {#saving-an-html-form-as-a-draft}

U kunt een HTML5-formulier opslaan als concept en het invullen van het formulier later hervatten. Met Forms Portal kan elke gebruiker een HTML5-formulier opslaan en herstellen. Voeg de volgende configuraties toe aan het profielknooppunt om de functie Opslaan als concept in te schakelen:

## Aangepast profiel om de functie Opslaan als concept toe te staan {#custom-profile-to-allow-save-as-draft-feature}

AEM Forms geeft een profiel **Opslaan als concept** op. U kunt een formulier weergeven met het profiel Opslaan als concept om de conceptfunctionaliteit in te schakelen voor een HTML5-formulier. U kunt het HTML-renderprofiel voor een formulier opgeven in [Forms Manager](/help/forms/using/introduction-managing-forms.md).

Als u de functie Opslaan als concept wilt inschakelen voor uw bestaande [aangepast profiel](/help/forms/using/custom-profile.md), voegt u de volgende eigenschappen toe aan uw aangepaste profielnode:

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
   <td>Tekenreeks</td>
   <td>true</td>
   <td><p>Hiermee wordt de functie Opslaan als concept ingeschakeld</p> <p>voor dit profiel.</p> </td>
  </tr>
  <tr>
   <td>mfAllowAttachments</td>
   <td>Tekenreeks</td>
   <td>true</td>
   <td><p>Hiermee kunt u bijlagen uploaden</p> <p>met dit profiel.</p> </td>
  </tr>
 </tbody>
</table>

## Opslag en aanbieding {#drafts-storage-and-listing}

Nadat u de functie Opslaan als concept hebt ingeschakeld voor een formulier; wanneer het formulier wordt opgeslagen, wordt het weergegeven in de [component Concepten en verzending](/help/forms/using/draft-submission-component.md). U kunt het opgeslagen formulier ophalen en invullen met de component Concept en Verzending.

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
   <td>Tekenreeks</td>
   <td>true</td>
   <td>Concepten en formulieren na verzending weergeven in<br /> Forms Portal-concepten en -verzendingen</td>
  </tr>
 </tbody>
</table>

Standaard slaat AEM Forms de gebruikersgegevens die zijn gekoppeld aan het concept en de verzending van een formulier op in het knooppunt /content/forms/fp in het exemplaar Publish. U kunt uw leverancier van de douaneopslag toevoegen, voor details zie [Aangepaste opslag voor de component van Concepten en van Verzending](/help/forms/using/adding-custom-storage-provider-forms.md).
