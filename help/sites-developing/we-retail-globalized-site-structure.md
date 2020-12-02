---
title: De geglobaliseerde sitestructuur in 'We' uitproberen.Handelsversie
seo-title: De geglobaliseerde sitestructuur in 'We' uitproberen.Handelsversie
description: 'null'
seo-description: 'null'
uuid: 5e5a809d-578f-4171-8226-cb65aa995754
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: d674458c-d5f3-4dee-a673-b0777c02ad30
translation-type: tm+mt
source-git-commit: b3e1493811176271ead54bae55b1cd0cf759fe71
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---


# Het proberen van de Globalized Structuur van de Plaats in Wij.Retail{#trying-out-the-globalized-site-structure-in-we-retail}

We.Retail is gebouwd met een geglobaliseerde sitestructuur die een taalstramien biedt die live kan worden gekopieerd naar landspecifieke websites. Alles is ingesteld op een &#39;out-of-the-box&#39; zodat u kunt experimenteren met deze structuur en de ingebouwde vertaalmogelijkheden.

## Uitproberen {#trying-it-out}

1. Open de siteconsole vanuit **Algemene navigatie -> Sites**.
1. Schakelaar aan kolommening (als niet reeds actief) en selecteer Wij.Retail. Neem nota van de voorbeeldlandstructuur met Zwitserland, de Verenigde Staten, Frankrijk, enz., langs de taalmeesters.

   ![chlimage_1-87](assets/chlimage_1-87a.png)

1. Selecteer Zwitserland en bekijk de taalwortels voor de talen van dat land. Er is nog geen inhoud onder deze wortels.

   ![chlimage_1-88](assets/chlimage_1-88a.png)

1. Ga naar de lijstweergave en controleer of de taalkopieën voor de landen allemaal live kopieën zijn.

   ![chlimage_1-89](assets/chlimage_1-89a.png)

1. Ga terug naar de kolomweergave, klik op de Master taal en bekijk de master taalbasis met inhoud. Alleen Engels heeft inhoud.

   Wij.Retail wordt niet geleverd met vertaalde inhoud, maar de structuur en configuratie zijn zodanig ingesteld dat u de vertaalservices kunt demonstreren.

   ![chlimage_1-90](assets/chlimage_1-90a.png)

1. Zorg dat de Engelse taal is Master en open de **References** rail in de siteconsole en selecteer **Taalkopieën**.

   ![chlimage_1-91](assets/chlimage_1-91.png)

1. Schakel het selectievakje naast het label **Taalkopieën** in om alle taalkopieën te selecteren. Selecteer in het gedeelte **Taalkopieën bijwerken** van de track de optie **Een nieuw vertaalproject maken**. Geef een naam op voor het project en klik op **Bijwerken**.

   ![chlimage_1-92](assets/chlimage_1-92.png)

1. Voor elke taalvertaling wordt een project gemaakt. Bekijk hen onder **Navigatie -> Projecten**.

   ![chlimage_1-93](assets/chlimage_1-93.png)

1. Klik op het Duits om de details van het vertaalproject te bekijken. De status bevindt zich in **Draft**. Als u de vertaling wilt starten met de vertaalservice van Microsoft, klikt u op het chevron naast de kop **Vertaaltaak** en selecteert u **Start**.

   ![chlimage_1-94](assets/chlimage_1-94.png)

1. Het vertaalproject begint. Klik op de ovaal onder aan de kaart met het label Vertaaltaak om de details weer te geven. Pagina&#39;s met de status **Klaar voor revisie** zijn al vertaald door de vertaalservice.

   ![chlimage_1-95](assets/chlimage_1-95.png)

1. Als u een van de pagina&#39;s in de lijst selecteert en vervolgens **Voorvertoning in sites** in de werkbalk selecteert, wordt de vertaalde pagina in de pagina-editor geopend.

   ![chlimage_1-96](assets/chlimage_1-96.png)

>[!NOTE]
>
>Deze procedure toonde de ingebouwde integratie met de machinevertaling van Microsoft aan. Met het [AEM Translation Integration Framework](/help/sites-administering/translation.md) kunt u met veel standaardvertaalservices de vertaling van AEM ordenen.

## Aanvullende informatie {#further-information}

Raadpleeg voor meer informatie het ontwerpdocument [Inhoud vertalen voor meertalige sites](/help/sites-administering/translation.md) voor volledige technische details.
