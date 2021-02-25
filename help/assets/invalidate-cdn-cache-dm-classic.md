---
title: De CDN-cache ongeldig maken via Dynamic Media Classic
description: Door de CDN-inhoud (Content Delivery Network) in de cache te ongeldig te maken, kunt u snel elementen bijwerken die door Dynamic Media Classic worden geleverd, in plaats van te wachten tot de cache verloopt.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5.5/ASSETS
topic-tags: dynamic-media
content-type: reference
translation-type: tm+mt
source-git-commit: 729fbf3a97d3ae3bc91204f8831fd115d9d77f20
workflow-type: tm+mt
source-wordcount: '671'
ht-degree: 18%

---


# De CDN-cache ongeldig maken door middel van Dynamic Media Classic {#invalidating-your-cdn-cached-content}

Dynamic Media-elementen worden in cache geplaatst door de CDN (Content Delivery Network) voor snelle levering. Wanneer u echter updates aan een element aanbrengt, wilt u dat deze wijzigingen onmiddellijk van kracht worden. Als u de CDN-inhoud in de cache ongeldig maakt, kunt u snel elementen bijwerken die door Dynamic Media worden geleverd, in plaats van te wachten tot de cache verloopt.

>[!NOTE]
>
>Klanten moeten de CDN gebruiken die is gebundeld met Adobe Experience Manager Dynamic Media om te profiteren van CDN-cachevalidatie.

>[!IMPORTANT]
>
>De volgende stappen zijn alleen van toepassing op Dynamic Media in AEM 6.5, Service Pack 5 (AEM 6.5.5) of eerder.<br>Als u Dynamic Media in AEM 6.5, Service Pack 6 (AEM 6.5.6) of later gebruikt, volg de stappen die in het  [ongeldig maken van het CDN geheime voorgeheugen door middel van Dynamic Media worden gevonden.](/help/assets/invalidate-cdn-cache-dynamic-media.md)

Zie ook [Overzicht van cache in Dynamic Media Classic (Scene7)](https://helpx.adobe.com/experience-manager/scene7/kb/base/caching-questions/scene7-caching-overview.html).

**De CDN-cache ongeldig maken met Dynamic Media Classic:**

1. Open [Dynamic Media Classic desktop application](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/intro/dynamic-media-classic-desktop-app.html?lang=en#system-requirements-dmc-app) en meld u vervolgens aan bij uw account.

   Uw geloofsbrieven en opening van een sessie werden verstrekt door Adobe op het tijdstip van levering. Neem contact op met Technische ondersteuning als u deze informatie niet hebt.

1. Tik in de rechterbovenhoek van de pagina op **[!UICONTROL Setup > Application Setup > General Settings.]**
1. Zoek op de pagina Algemene instellingen toepassing onder de kop Servers het tekstvak **[!UICONTROL CDN Invalidation Template]**.

1. Geef de sjabloon op die wordt gebruikt voor het ongeldig maken van de CDN-cache (Content Delivery Network).

   Stel bijvoorbeeld dat u een URL voor een afbeelding (inclusief voorinstellingen of modifiers voor afbeeldingen) opgeeft die verwijst naar `<ID>`, in plaats van een specifieke afbeeldings-id zoals in het volgende voorbeeld:

   `https://server.com/is/image/Company/<ID>?$product$`

   Als de sjabloon alleen `<ID>` bevat, vult Dynamic Media `https://<server>/is/image` in, waarbij `<server>` de naam van de publicatieserver is die is gedefinieerd in Algemene instellingen en &lt;ID> de elementen zijn die zijn geselecteerd om ongeldig te worden gemaakt.

1. Klik in de rechterbenedenhoek van de pagina op **[!UICONTROL Close.]**
1. Selecteer een of meer elementen in de Klassieke gebruikersinterface van Dynamic Media en klik op **[!UICONTROL File > Invalidate CDN.]**. U ziet een lijst met een of meer URL&#39;s die zijn gegenereerd op basis van de sjabloon die u hebt gemaakt en de elementen die u hebt geselecteerd. De URL van de server wordt gebruikt onder &quot;Gepubliceerde servernaam&quot; onder Algemene instellingen van toepassing.

   Stel dat u, terwijl de CDN-validatiesjabloon in de vorige stap is ingesteld, één afbeelding met afbeeldingselementen hebt geselecteerd met de naam `Backpack_B`. Wanneer u **[!UICONTROL File > Invalidate CDN]** tikt, resulteert dit in de volgende gegenereerde URL in de gebruikersinterface voor CDN-validatie:

   `https://server.com/is/image/Company/Backpack_B?$product$`

1. Tik in de keuzelijst URL op **[!UICONTROL Continue]** om de cache voor elke specifieke URL te wissen. U kunt een URL bewerken of u kunt een URL toevoegen door deze in het vak URL-lijst te typen of te plakken. u hoeft CDN niet vooraf in te stellen om sjabloon ongeldig te maken.

   Nadat u **[!UICONTROL Continue]** klikt, wordt een indicator getoond die u een schatting geeft van hoe lang het zal duren om het geheime voorgeheugen te ontruimen.

   Als u meerdere elementen hebt geselecteerd en op **[!UICONTROL File > Invalidate CDN]** tikt, wordt naar elk element verwezen in het opgeslagen **[!UICONTROL Template URL.]**. Daarom kunt u een **[!UICONTROL CDN Invalidate Template]** definiëren die verwijst naar elke URL-voorinstelling voor afbeeldingen waarnaar op uw website wordt verwezen (zoals productdetails en zoekresultaten). Wanneer u vervolgens een of meer afbeeldingen selecteert om ongeldig te worden gemaakt door het cachegeheugen, vullen de URL&#39;s automatisch de interface in.

   >[!NOTE]
   >
   >Wanneer u assets selecteert en vervolgens op **[!UICONTROL File > Invalidate CDN]** klikt, gebruikt Dynamische media een ongeldige CDN-sjabloon om automatisch URL&#39;s te maken om ongeldig te maken vanaf het CDN (Content Delivery Network). Als het tekstvak **[!UICONTROL CDN Invalidate Template]** leeg is, wordt er een lege URL-lijst weergegeven. Caching bij CDN is niet gebaseerd op assets; het is gebaseerd op URL. Daarom moet u de volledige URL&#39;s die op uw website staan, kennen. Nadat u deze URL&#39;s hebt bepaald, kunt u ze eerder in de stappen toevoegen aan het tekstvak **[!UICONTROL Invalidate CDN Template]**. Vervolgens kunt u deze assets selecteren en de URL&#39;s in één stap ongeldig maken.
   >
   >Een andere optie is het toevoegen van volledige URL&#39;s aan de lijst **[!UICONTROL Invalidate CDN]**. Als u deze benadering volgt, is het niet nodig om activa in de Klassiek van Dynamic Media te selecteren alvorens naar **[!UICONTROL File > Invalidate CDN]** optie te gaan.

