---
title: Snelstartgids voor mappen zonder middelenkoppen maken
description: Met Modellen AEM inhoudsfragmenten kunt u de structuur van inhoudsfragmenten definiëren als de basis voor inhoud zonder kop.
exl-id: 8d913056-fcfa-4cdd-b40a-771f13dfd0f4
source-git-commit: 7355c149500f9e5044c9ff78af208d36ee681f56
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# Snelstartgids voor mappen zonder middelenkoppen maken {#creating-an-assets-folder}

Met Modellen AEM inhoudsfragmenten kunt u de structuur van inhoudsfragmenten definiëren als de basis voor inhoud zonder kop. Inhoudsfragmenten worden vervolgens in mappen met elementen opgeslagen.

## Wat is een middelenmap? {#what-is-an-assets-folder}

[Nu u modellen voor inhoudsfragmenten hebt gemaakt](create-content-model.md) waarmee u de gewenste structuur voor toekomstige inhoudsfragmenten definieert, kunt u waarschijnlijk bepaalde fragmenten maken.

U moet echter eerst een map met middelen maken waarin u deze wilt opslaan.

Elementenmappen worden gebruikt om [traditionele inhoudselementen ordenen](/help/assets/manage-assets.md) zoals afbeeldingen en video en als inhoudsfragmenten.

## Een middelenmap maken {#how-to-create-an-assets-folder}

Een beheerder hoeft alleen maar af en toe mappen te maken om de inhoud te ordenen terwijl deze wordt gemaakt. Voor deze gids Aan de slag hoeven we slechts één map te maken.

1. Meld u aan bij AEM en selecteer in het hoofdmenu **Navigation -> Middelen -> Bestanden**.
1. Tik of klik op **Maken -> Map**.
1. Een **Titel** en **Naam** voor uw map.
   * De **Titel** moeten beschrijvend zijn.
   * De **Naam** wordt de knooppuntnaam in de repository.
      * Het wordt automatisch gegenereerd op basis van de titel en aangepast op basis van [AEM naamconventies.](/help/sites-developing/naming-conventions.md)
      * Deze kan zo nodig worden aangepast.

   ![Map maken](assets/assets-folder-create.png)
1. Selecteer de map die u net hebt gemaakt en selecteer **Eigenschappen** van de werkbalk (of gebruik de `p` [sneltoets.](/help/sites-authoring/keyboard-shortcuts.md))
1. In de **Eigenschappen** venster, selecteert u de **Cloud Services** tab.
1. Voor de **Cloud Configuration** Selecteer [configuratie die u eerder hebt gemaakt.](create-configuration.md)

   ![Map met middelen configureren](assets/assets-folder-configure.png)
1. Tik of klik op **Opslaan en sluiten**.
1. Tik of klik op **OK** in het bevestigingsvenster.

   ![Bevestigingsvenster](assets/assets-folder-confirmation.png)

U kunt extra submappen maken in de map die u net hebt gemaakt. De submappen nemen de **Cloud Configuration** van de bovenliggende map. Dit kan echter worden genegeerd als u modellen uit een andere configuratie wilt gebruiken.

Als u een gelokaliseerde sitestructuur gebruikt, kunt u [een hoofdmap voor een taal maken](/help/assets/multilingual-assets.md) onder uw nieuwe map.

## Volgende stappen {#next-steps}

Nu u een map voor de inhoudsfragmenten hebt gemaakt, kunt u verdergaan naar het vierde gedeelte van de gids Aan de slag en [Maak inhoudsfragmenten.](create-content-fragment.md)

>[!TIP]
>
>Voor volledige details over het beheren van Inhoudsfragmenten raadpleegt u de [Documentatie over inhoudsfragmenten](/help/assets/content-fragments/content-fragments.md)
