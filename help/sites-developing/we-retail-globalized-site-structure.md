---
title: De geglobaliseerde sitestructuur in 'We' uitproberen.Handelsversie
description: Leer hoe u een geglobaliseerde sitestructuur kunt uitproberen in Adobe Experience Manager met We.Retail.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
exl-id: e1de20b0-6d7a-4bda-b62f-c2808fd0af28
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# De geglobaliseerde sitestructuur in &#39;We&#39; uitproberen.Handelsversie{#trying-out-the-globalized-site-structure-in-we-retail}

We.Retail is gebouwd met een geglobaliseerde sitestructuur die een taalmaster biedt die live kan worden gekopieerd naar landspecifieke websites. Alles is ingesteld op &#39;out-of-the-box&#39;, zodat u kunt experimenteren met deze structuur en de ingebouwde vertaalmogelijkheden.

## Uitproberen {#trying-it-out}

1. De siteconsole openen vanuit **Algemene navigatie > Sites**.
1. Schakelaar aan kolommening (als niet reeds actief) en selecteer Wij.Retail. Neem nota van de structuur van het voorbeeldland met Zwitserland, de Verenigde Staten, Frankrijk, etc., langs de Meester van de Taal.

   ![chlimage_1-87](assets/chlimage_1-87a.png)

1. Selecteer Zwitserland en bekijk de taalwortels voor de talen van dat land. Er is nog geen inhoud onder deze wortels.

   ![chlimage_1-88](assets/chlimage_1-88a.png)

1. Ga naar de lijstweergave en controleer of de taalkopieën voor de landen allemaal live kopieën zijn.

   ![chlimage_1-89](assets/chlimage_1-89a.png)

1. Ga terug naar de kolomweergave, klik op het stramien Taal en bekijk de hoofdwortels van de taal met inhoud. Alleen Engels heeft inhoud.

   Wij.Retail wordt niet geleverd met vertaalde inhoud, maar de structuur en configuratie zijn aanwezig om u de vertaalservices te laten demonstreren.

   ![chlimage_1-90](assets/chlimage_1-90a.png)

1. Selecteer de Engelse taalmaster en open het dialoogvenster **Verwijzingen** rail in de locatieconsole en selecteer **Taalkopieën**.

   ![chlimage_1-91](assets/chlimage_1-91.png)

1. Schakel het selectievakje naast de optie **Taalkopieën** om alle taalkopieën te selecteren. In de **Taalkopieën bijwerken** van de spoorstaaf de optie om **Een nieuw vertaalproject maken**. Geef een naam op voor het project en klik op **Bijwerken**.

   ![chlimage_1-92](assets/chlimage_1-92.png)

1. Voor elke taalvertaling wordt een project gemaakt. Bekijk ze onder **Navigation > Projecten**.

   ![chlimage_1-93](assets/chlimage_1-93.png)

1. Klik op Duits om de details van het vertaalproject te bekijken. De status bevindt zich in **Concept**. Als u de vertaling wilt starten met de vertaalservice van Microsoft®, klikt u op het chevron naast de **Vertaaltaak** kop en selecteer **Start**.

   ![chlimage_1-94](assets/chlimage_1-94.png)

1. Het vertaalproject begint. Klik op de ovaal onder aan de kaart met het label Vertaaltaak om de details weer te geven. Pagina&#39;s met de status **Gereed voor revisie** zijn al vertaald door de vertaaldienst.

   ![chlimage_1-95](assets/chlimage_1-95.png)

1. Een van de pagina&#39;s in de lijst selecteren en vervolgens **Voorvertoning in sites** opent u de vertaalde pagina in de pagina-editor op de werkbalk.

   ![chlimage_1-96](assets/chlimage_1-96.png)

>[!NOTE]
>
>Deze procedure heeft de ingebouwde integratie met Microsoft®-computervertaling aangetoond. Met de [AEM Omzettingsintegratiekader](/help/sites-administering/translation.md), kunt u met vele standaardvertaaldiensten integreren om de vertaling van AEM te ordenen.

## Meer informatie {#further-information}

Zie het ontwerpdocument voor meer informatie [Inhoud vertalen voor meertalige sites](/help/sites-administering/translation.md) voor volledige technische details.
