---
title: Een Assets-map zonder koppen en een snelstartgids maken
description: Met Modellen AEM inhoudsfragmenten kunt u de structuur van inhoudsfragmenten definiëren als de basis voor inhoud zonder kop.
exl-id: 8d913056-fcfa-4cdd-b40a-771f13dfd0f4
solution: Experience Manager, Experience Manager Sites
feature: Headless,Content Fragments,GraphQL,Persisted Queries,Developing
role: Admin,Architect,Data Architect,Developer
source-git-commit: 9a3008553b8091b66c72e0b6c317573b235eee24
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# Een Assets-map zonder koppen en een snelstartgids maken {#creating-an-assets-folder}

Met Modellen AEM inhoudsfragmenten kunt u de structuur van inhoudsfragmenten definiëren als de basis voor inhoud zonder kop. Inhoudsfragmenten worden vervolgens in mappen met elementen opgeslagen.

## Wat is een Assets-map? {#what-is-an-assets-folder}

[&#x200B; nu u de Modellen van het Fragment van de Inhoud &#x200B;](create-content-model.md) hebt gecreeerd die de structuur bepalen die u voor uw toekomstige Fragmenten van de Inhoud wilt, bent u waarschijnlijk opgewekt om sommige fragmenten tot stand te brengen.

U moet echter eerst een map met middelen maken waarin u deze wilt opslaan.

De omslagen van Assets worden gebruikt om [&#x200B; traditionele inhoudsactiva &#x200B;](/help/assets/manage-assets.md) als beelden en video en de Fragmenten van de Inhoud te organiseren.

## Een Assets-map maken {#how-to-create-an-assets-folder}

Een beheerder hoeft alleen maar af en toe mappen te maken om de inhoud te ordenen terwijl deze wordt gemaakt. Voor deze gids Aan de slag hoeven we slechts één map te maken.

1. Logboek in AEM en van het belangrijkste menu selecteert **Navigatie > Assets > Dossiers**.
1. Klik **creëren > Omslag**.
1. Verstrek a **Titel** en a **Naam** voor uw omslag.
   * De **Titel** zou beschrijvend moeten zijn.
   * De **Naam** zal de knoopnaam in de bewaarplaats worden.
      * Het zal automatisch worden geproduceerd gebaseerd op de titel en aangepast volgens [&#x200B; AEM noemende overeenkomsten.](/help/sites-developing/naming-conventions.md)
      * Deze kan zo nodig worden aangepast.

   ![&#x200B; creeer omslag &#x200B;](assets/assets-folder-create.png)
1. Selecteer de omslag u creeerde en selecteer dan **Eigenschappen** van de toolbar (of gebruik de `p` [&#x200B; toetsenbordkortere weg.](/help/sites-authoring/keyboard-shortcuts.md))
1. In het **venster van Eigenschappen**, selecteer de **Cloud Servicen** tabel.
1. Voor de **Configuratie van de Wolk** selecteer de [&#x200B; configuratie u eerder creeerde.](create-configuration.md)
   ![&#x200B; vorm activa omslag &#x200B;](assets/assets-folder-configure.png)
1. Klik **sparen &amp; Sluiten**.
1. Klik **O.K.** in het bevestigingsvenster.

   ![&#x200B; Bevestigingsvenster &#x200B;](assets/assets-folder-confirmation.png)

U kunt aanvullende submappen maken in de map die u hebt gemaakt. De subfolders zullen de **Configuratie van de Wolk** van de ouderomslag erven. Dit kan echter worden genegeerd als u modellen uit een andere configuratie wilt gebruiken.

Als u een gelokaliseerde plaatsstructuur gebruikt, kunt u [&#x200B; tot een taalwortel &#x200B;](/help/assets/multilingual-assets.md) onder uw nieuwe omslag leiden.

## Volgende stappen {#next-steps}

Nu u een omslag voor uw Fragmenten van de Inhoud hebt gecreeerd, kunt u zich op het vierde deel van begonnen gids bewegen en [&#x200B; creeer inhoudsfragmenten.](create-content-fragment.md)

>[!TIP]
>
>Voor volledige details over het beheren van de Fragmenten van de Inhoud, zie de [&#x200B; documentatie van de Fragmenten van de Inhoud &#x200B;](/help/assets/content-fragments/content-fragments.md)
