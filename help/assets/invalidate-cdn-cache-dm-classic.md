---
title: De cache van het Content Delivery Network ongeldig maken via Dynamic Media Classic
description: Door de CDN-inhoud (Content Delivery Network) in de cache te ongeldig te maken, kunt u snel elementen bijwerken die door Dynamic Media Classic worden geleverd, in plaats van te wachten op het verlopen van de cache.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5.5/ASSETS
topic-tags: dynamic-media
content-type: reference
feature: CDN Cache,Dynamic Media Classic
role: User, Admin
exl-id: 7020343a-b556-4091-9717-93fcc55e623b
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '677'
ht-degree: 12%

---

# De cache van het Content Delivery Network ongeldig maken via Dynamic Media Classic {#invalidating-your-cdn-cached-content}

Dynamic Media-elementen worden door de CDN (Content Delivery Network) in cache geplaatst voor snelle levering. Wanneer u echter updates aan een element aanbrengt, wilt u dat deze wijzigingen onmiddellijk van kracht worden. Als u de CDN-inhoud in de cache ongeldig maakt, kunt u snel elementen bijwerken die door Dynamic Media worden geleverd, in plaats van te wachten tot de cache verloopt.

>[!NOTE]
>
>Voor deze functie is het vereist dat u de CDN uit de doos gebruikt die bij Adobe Experience Manager Dynamic Media is gebundeld. Een andere aangepaste CDN wordt niet ondersteund met deze functie.

>[!IMPORTANT]
>
>De volgende stappen zijn alleen van toepassing op Dynamic Media in Adobe Experience Manager 6.5, Service Pack 5 (Experience Manager 6.5.5) of eerder.<br>Als u Dynamic Media in Experience Manager 6.5, Service Pack 6 (Experience Manager 6.5.6) of later gebruikt, volg de stappen die in [De CDN-cache ongeldig maken via Dynamic Media](/help/assets/invalidate-cdn-cache-dynamic-media.md).

<!-- REMOVED MARCH 28, 2022 BECAUSE OF 404; NO REDIRECT WAS PUT IN PLACE BY SUPPORT See also [Cache overview in Dynamic Media Classic (Scene7)](https://helpx.adobe.com/experience-manager/scene7/kb/base/caching-questions/scene7-caching-overview.html). -->

**De CDN-cache ongeldig maken via Dynamic Media Classic:**

1. Open de [Dynamic Media Classic-bureaubladtoepassing](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/intro/dynamic-media-classic-desktop-app.html#system-requirements-dmc-app)en meld u vervolgens aan bij uw account.

   Uw geloofsbrieven en opening van een sessie werden verstrekt door Adobe op het tijdstip van levering. Neem contact op met de Klantenondersteuning van de Adobe als u deze informatie niet hebt.

1. Navigeer in de rechterbovenhoek van de pagina naar **[!UICONTROL Setup]** > **[!UICONTROL Application Setup]** > **[!UICONTROL General Settings]**.
1. Zoek op de pagina Algemene instellingen van toepassing onder de kop Servers van de groep de locatie **[!UICONTROL CDN Invalidation Template]** tekstvak.

1. Geef de sjabloon op die wordt gebruikt voor het ongeldig maken van de CDN-cache (Content Delivery Network).

   Stel dat u bijvoorbeeld een afbeeldings-URL invoert (inclusief voorinstellingen of wijzigingstoetsen voor afbeeldingen) die verwijst naar `<ID>`in plaats van een specifieke afbeelding-id zoals in het volgende voorbeeld:

   `https://server.com/is/image/Company/<ID>?$product$`

   Als de sjabloon alleen bevat `<ID>`en vervolgens vult Dynamic Media in `https://<server>/is/image` waar `<server>` is de naam van de publicatieserver die is gedefinieerd in Algemene instellingen en &lt;id> De geselecteerde elementen worden ongeldig gemaakt.

1. Selecteer in de rechterbenedenhoek van de pagina de optie **[!UICONTROL Close]**.
1. Selecteer in de Dynamic Media Classic-gebruikersinterface een of meer elementen en ga vervolgens naar **[!UICONTROL File]** > **[!UICONTROL Invalidate CDN]**. Er wordt een lijst weergegeven met een of meer URL&#39;s die zijn gegenereerd op basis van de sjabloon die u hebt gemaakt en de elementen die u hebt geselecteerd. De URL van de server wordt gebruikt onder &quot;Gepubliceerde servernaam&quot; onder Algemene instellingen van toepassing.

   Stel dat u, terwijl de CDN-validatiesjabloon in de vorige stap is ingesteld, één afbeeldingselement hebt geselecteerd met de naam `Backpack_B`. Wanneer u gaat naar **[!UICONTROL File]** > **[!UICONTROL Invalidate CDN]** resulteert dit in de volgende gegenereerde URL in de gebruikersinterface voor CDN-validatie:

   `https://server.com/is/image/Company/Backpack_B?$product$`

1. Selecteer in de keuzelijst URL de optie **[!UICONTROL Continue]** om de cache voor elke specifieke URL te wissen. U kunt een URL bewerken of u kunt een URL toevoegen door deze in het vak URL-lijst te typen of te plakken. U hoeft CDN niet vooraf in te stellen om de sjabloon ongeldig te maken.

   Nadat u **[!UICONTROL Continue]** Er wordt een indicator weergegeven die u een schatting geeft van hoe lang het duurt om de cache te wissen.

   Als u meerdere elementen hebt geselecteerd, gaat u naar **[!UICONTROL File]** > **[!UICONTROL Invalidate CDN]**, wordt naar elk element verwezen in de opgeslagen **[!UICONTROL Template URL]**. Daarom kunt u een **[!UICONTROL CDN Invalidate Template]** verwijzen naar elke URL-voorinstelling voor afbeeldingen waarnaar op uw website wordt verwezen (zoals productdetails en zoekresultaten). Wanneer u vervolgens een of meer afbeeldingen selecteert om ongeldig te worden gemaakt door het cachegeheugen, vullen de URL&#39;s automatisch de interface in.

   >[!NOTE]
   >
   >Wanneer u elementen selecteert en vervolgens naar **[!UICONTROL File]** > **[!UICONTROL Invalidate CDN]** Dynamic Media gebruikt een CDN-sjabloon voor ongeldig maken om automatisch URL&#39;s te maken die ongeldig worden gemaakt via de CDN (Content Delivery Network). Als het tekstvak **[!UICONTROL CDN Invalidate Template]** leeg is, wordt er een lege URL-lijst weergegeven. Caching bij CDN is niet gebaseerd op assets; het is gebaseerd op URL. Daarom moet u de volledige URL&#39;s die op uw website staan, kennen. Nadat u deze URL&#39;s hebt bepaald, kunt u ze eerder in de stappen toevoegen aan het tekstvak **[!UICONTROL Invalidate CDN Template]**. Vervolgens kunt u deze assets selecteren en de URL&#39;s in één stap ongeldig maken.
   >
   >U kunt ook volledige URL&#39;s toevoegen aan de **[!UICONTROL Invalidate CDN]** lijst. Als u deze aanpak volgt, is het niet nodig om elementen in Dynamic Media Classic te selecteren voordat u naar de **[!UICONTROL File > Invalidate CDN]** -optie.
