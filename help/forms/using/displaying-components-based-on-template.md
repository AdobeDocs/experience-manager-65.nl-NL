---
title: Componenten weergeven die zijn gebaseerd op de gebruikte sjabloon
seo-title: Componenten weergeven die zijn gebaseerd op de gebruikte sjabloon
description: Wanneer u een formulier maakt, leert u hoe u componenten in het zijpaneel kunt inschakelen op basis van de geselecteerde sjabloon.
seo-description: Wanneer u een formulier maakt, leert u hoe u componenten in het zijpaneel kunt inschakelen op basis van de geselecteerde sjabloon.
uuid: 790d201b-318d-4d02-9bc5-9d6bc41d057a
contentOwner: sashanka
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: customization
content-type: reference
discoiquuid: f658da57-0134-4458-9ef9-a99787b66742
docset: aem65
translation-type: tm+mt
source-git-commit: 76908a565bf9e6916db39d7db23c04d2d40b3247
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 1%

---


# Componenten weergeven die zijn gebaseerd op de gebruikte sjabloon{#displaying-components-based-on-the-template-used}

Wanneer een auteur van een formulier een adaptief formulier maakt met een [sjabloon](../../forms/using/template-editor.md), kan de auteur van het formulier specifieke componenten zien en gebruiken die zijn gebaseerd op sjabloonbeleid. U kunt een beleid voor sjablooninhoud opgeven waarmee u een groep componenten kunt kiezen die de auteur van het formulier ziet op het moment van het ontwerpen van het formulier.

## Het inhoudsbeleid van een sjabloon wijzigen {#changing-the-content-policy-of-a-template}

Wanneer u een sjabloon maakt, wordt deze onder `/conf` in de inhoudgegevensopslagruimte gemaakt. Gebaseerd op de omslagen u in `/conf` folder hebt gecreeerd, is de weg aan uw malplaatje: `/conf/<your-folder>/settings/wcm/templates/<your-template>`.

Voer de volgende stappen uit om de componenten in de zijbalk weer te geven op basis van het inhoudsbeleid van een sjabloon:

1. CRXDE-lijst openen.\
   URL: `https://<server>:<port>/crx/de/index.jsp`
1. Navigeer in CRXDE naar de map waarin de sjabloon is gemaakt.

   Bijvoorbeeld: `/conf/<your-folder>/`

1. Navigeer in CRXDE naar: `/conf/<your-folder>/settings/wcm/policies/fd/af/layouts/gridFluidLayout/`

   Voor het selecteren van een groep componenten is een nieuw inhoudsbeleid vereist. Om een nieuw beleid tot stand te brengen, kopieer-kleef het standaardbeleid, en noem het anders.

   Het pad naar het standaard inhoudsbeleid is: `/conf/<your-folder>/settings/wcm/policies/fd/af/layouts/gridFluidLayout/default`

   In de `gridFluidLayout` omslag, kopieer-kleef het standaardbeleid en noem het anders. Bijvoorbeeld, `myPolicy`.

   ![Standaardbeleid kopiëren](assets/crx-default1.png)

1. Selecteer het nieuwe beleid u creeert, en selecteer **components** bezit in het rechterpaneel met type `string[]`.

   Wanneer u het componentenbezit selecteert en opent, ziet u het Edit dialoog van Componenten. In het dialoogvenster Componenten bewerken kunt u componentgroepen toevoegen of verwijderen met de knoppen **+** en **-**. U kunt componentengroep toevoegen die componenten omvat die vorm u auteurs aan gebruik wilt.

   ![Componenten toevoegen aan of verwijderen uit het beleid](assets/add-components-list1.png)

   Nadat u een componentengroep toevoegt, klik **OK** om de lijst bij te werken, en dan **sparen allen** boven CRXDE adresbar te klikken en te verfrissen.

1. Wijzig in de sjabloon het inhoudsbeleid van standaard in het nieuwe beleid dat u hebt gemaakt. ( `myPolicy` in dit voorbeeld.)

   Navigeer naar `/conf/<your-folder>/settings/wcm/templates/<your-template>/policies/jcr:content/guideContainer/rootPanel/items` om het beleid in CRXDE te wijzigen.

   Wijzig `default` in de eigenschap `cq:policy` in de nieuwe beleidsnaam ( `myPolicy`).

   ![Beleid voor bijgewerkte sjablooninhoud](assets/updated-policy.png)

   Wanneer u een formulier ontwerpt dat u met de sjabloon maakt, kunt u de toegevoegde componenten in het zijpaneel zien.

