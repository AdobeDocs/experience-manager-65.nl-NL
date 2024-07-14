---
title: Componenten weergeven die zijn gebaseerd op de gebruikte sjabloon
description: Wanneer u een formulier maakt, leert u hoe u componenten in het zijpaneel kunt inschakelen op basis van de geselecteerde sjabloon.
contentOwner: sashanka
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: customization
content-type: reference
docset: aem65
exl-id: 1fc56829-db81-4450-b1d8-b4a31110199e
solution: Experience Manager, Experience Manager Forms
role: User, Developer
feature: Adaptive Forms,Foundation Components
source-git-commit: 8a77756e8ba771c8de9950c2323bef8f23cc59b4
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 0%

---

# Componenten weergeven die zijn gebaseerd op de gebruikte sjabloon{#displaying-components-based-on-the-template-used}

Wanneer een vormauteur tot een adaptieve vorm gebruikend a [ malplaatje ](../../forms/using/template-editor.md) leidt, kan de vormauteur specifieke componenten zien en gebruiken die op malplaatjebeleid worden gebaseerd. U kunt een beleid voor sjablooninhoud opgeven waarmee u een groep componenten kunt kiezen die de auteur van het formulier ziet op het moment van het ontwerpen van het formulier.

## Het inhoudsbeleid van een sjabloon wijzigen {#changing-the-content-policy-of-a-template}

Wanneer u een sjabloon maakt, wordt deze onder `/conf` gemaakt in de inhoudsopslagplaats. Op basis van de mappen die u in de map `/conf` hebt gemaakt, is het pad naar de sjabloon: `/conf/<your-folder>/settings/wcm/templates/<your-template>` .

Voer de volgende stappen uit om de componenten in de zijbalk weer te geven op basis van het inhoudsbeleid van een sjabloon:

1. CRXDE-lijst openen.\
   URL: `https://<server>:<port>/crx/de/index.jsp`
1. Navigeer in CRXDE naar de map waarin de sjabloon is gemaakt.

   Bijvoorbeeld: `/conf/<your-folder>/`

1. Navigeer in CRXDE naar: `/conf/<your-folder>/settings/wcm/policies/fd/af/layouts/gridFluidLayout/`

   Voor het selecteren van een groep componenten is een nieuw inhoudsbeleid vereist. Om een beleid tot stand te brengen, kopieer-kleef het standaardbeleid, en noem het anders.

   Het pad naar het standaardbeleid voor inhoud is: `/conf/<your-folder>/settings/wcm/policies/fd/af/layouts/gridFluidLayout/default`

   Kopieer het standaardbeleid in de map `gridFluidLayout` en plak het onder een andere naam. Bijvoorbeeld `myPolicy` .

   ![ het Kopiëren standaardbeleid ](assets/crx-default1.png)

1. Selecteer het nieuwe beleid u creeert, en selecteer het **componenten** bezit in het rechterzijpaneel met type `string[]`.

   Wanneer u het componentenbezit selecteert en opent, ziet u het Edit de dialoogvakje van Componenten. In het dialoogvenster Componenten bewerken kunt u componentgroepen toevoegen of verwijderen met de knoppen **+** en **-** . U kunt componentengroep toevoegen die componenten omvat die vorm u auteurs aan gebruik wilt.

   ![ voeg of verwijder componenten in het beleid toe ](assets/add-components-list1.png)

   Nadat u een componentengroep toevoegt, klik **O.K.** om de lijst bij te werken, en dan **te klikken sparen allen** boven CRXDE adresbar en verfrist zich.

1. Wijzig in de sjabloon het inhoudsbeleid van standaard in het nieuwe beleid dat u hebt gemaakt. ( `myPolicy` in dit voorbeeld.)

   Navigeer naar `/conf/<your-folder>/settings/wcm/templates/<your-template>/policies/jcr:content/guideContainer/rootPanel/items` om het beleid in CRXDE te wijzigen.

   Wijzig `default` in de eigenschap `cq:policy` in de nieuwe beleidsnaam ( `myPolicy` ).

   ![ Bijgewerkt beleid van de malplaatjeinhoud ](assets/updated-policy.png)

   Wanneer u een formulier ontwerpt dat u met de sjabloon maakt, kunt u de toegevoegde componenten in het zijpaneel zien.
