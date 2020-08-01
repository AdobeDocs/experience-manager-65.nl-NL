---
title: Slimme tags en zoekopdrachten beheren
description: Onnauwkeurige slimme tags bijwerken of verwijderen om de relevantie van tags te verbeteren
contentOwner: AG
translation-type: tm+mt
source-git-commit: 9fc1201db83ae0d3bb902d4dc3ab6d78cc1dc251
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 0%

---


# Slimme tags en zoekopdrachten beheren {#manage-smart-tags-and-searches}

<!--
TBD: This article should be merged into a new, uber article for Smart Tags. Delete this article then. Cloud service article is merged.
-->

U kunt slimme tags beheren om eventuele onjuiste tags te verwijderen die aan uw merkafbeeldingen zijn toegewezen, zodat alleen de meest relevante tags worden weergegeven.

Als u slimme tags modereert, kunt u zoekopdrachten op basis van tags naar afbeeldingen verder verfijnen door ervoor te zorgen dat de afbeelding in de zoekresultaten wordt weergegeven voor de meest relevante tags. In feite wordt hiermee de kans dat niet-verwante afbeeldingen in zoekresultaten worden weergegeven, verkleind.

U kunt ook een hogere rangorde aan een tag toewijzen om de relevantie ervan voor een afbeelding te vergroten. Door een tag voor een afbeelding te promoten, neemt de kans toe dat de afbeelding in de zoekresultaten wordt weergegeven wanneer een zoekopdracht op basis van de desbetreffende tag wordt uitgevoerd.

1. Zoek in het vak Onderzoek naar elementen op basis van een tag.
1. Inspect de zoekresultaten om een afbeelding te identificeren die je niet relevant vindt voor je zoekopdracht.
1. Select the image, and click **[!UICONTROL Manage Tags]** from the toolbar.
1. Controleer de tags op de **[!UICONTROL Manage Tags]** pagina. Als u niet wilt dat de afbeelding wordt doorzocht op basis van een specifiek label, selecteert u het label en klikt u vervolgens op **[!UICONTROL Delete]** de werkbalk. U kunt ook op het `X` symbool naast het label klikken.
1. Als u een hogere rangorde aan een tag wilt toewijzen, selecteert u de tag en klikt u op **[!UICONTROL Promote]** de werkbalk. De tag die u promoot, wordt verplaatst naar de **[!UICONTROL Tags]** sectie.
1. Click **[!UICONTROL Save]**, and then click **[!UICONTROL OK]** to close the Success dialog.
1. Navigeer naar de pagina met eigenschappen voor de afbeelding. Let erop dat de tag die u hebt bevorderd een grote relevantie krijgt en daarom hoger wordt weergegeven in de zoekresultaten.

## De [!DNL Experience Manager] zoekresultaten begrijpen met slimme tags {#understandsearch}

Standaard combineert [!DNL Experience Manager] zoeken de zoektermen met een `AND` component. Het gebruik van slimme tags verandert dit standaardgedrag niet. Als u slimme tags gebruikt, voegt u een extra `OR` component toe om te zoeken naar zoektermen in de lijst, worden slimme tags toegepast. For example, consider searching for `woman running`. Elementen met alleen `woman` of alleen `running` trefwoorden in de metagegevens worden niet standaard in de zoekresultaten weergegeven. Een element dat is gelabeld met slimme tags `woman` `running` of met slimme tags, wordt echter weergegeven in een dergelijke zoekopdracht. De zoekresultaten zijn dus een combinatie van:

* elementen met `woman` en `running` trefwoorden in de metagegevens.

* elementen die zijn gelabeld met een van de trefwoorden.

De zoekresultaten die overeenkomen met alle zoektermen in metagegevensvelden worden eerst weergegeven, gevolgd door de zoekresultaten die overeenkomen met een van de zoektermen in de slimme tags. In het bovenstaande voorbeeld is de weergavevolgorde van zoekresultaten bij benadering:

1. komt overeen met `woman running` de waarden in de verschillende metagegevensvelden.
1. overeenkomende waarden `woman running` in slimme tags.
1. overeenkomende met `woman` of van `running` in slimme tags.
