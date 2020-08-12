---
title: De CDN-cache ongeldig maken door middel van Dynamic Media Classic
description: Door de inhoud van de CDN-cache (Content Delivery Network) ongeldig te maken, kunt u snel elementen bijwerken die door Dynamic Media Classic worden geleverd, in plaats van te wachten tot de cache verloopt.
uuid: 0fd88e31-9745-4c98-a245-9f5d0766cad4
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5.5/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: e6c9b50b-c27c-48bf-b3c0-9994e7bf6d7e
translation-type: tm+mt
source-git-commit: 3eacfe8a79d155dddde8908d05b05790d048b0c5
workflow-type: tm+mt
source-wordcount: '652'
ht-degree: 19%

---


# De CDN-cache ongeldig maken door middel van Dynamic Media Classic {#invalidating-your-cdn-cached-content}

Dynamische media-elementen worden door de CDN in cache geplaatst voor snelle levering. Wanneer u echter updates aan een element aanbrengt, wilt u deze wijzigingen mogelijk direct van kracht laten worden. Door de CDN-inhoud (Content Delivery Network) in de cache te ongeldig te maken, kunt u snel elementen bijwerken die door Dynamic Media worden geleverd, in plaats van te wachten tot de cache verloopt.

>[!IMPORTANT]
>
>De volgende stappen zijn slechts op Dynamische Media in AEM 6.5, Service Pack 5 of vroeger van toepassing.

Zie ook Overzicht van [cache in Dynamic Media Classic (Scene7)](https://helpx.adobe.com/experience-manager/scene7/kb/base/caching-questions/scene7-caching-overview.html).

**Om het CDN geheime voorgeheugen door Dynamic Media Classic ongeldig te maken:**

1. Voer een van de volgende handelingen uit:

   * Meld u in uw webbrowser aan bij uw Dynamic Media Classic-account:

      [https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html)

      Uw geloofsbrieven en opening van een sessie werden verstrekt door Adobe op het tijdstip van levering. Neem contact op met Technische ondersteuning als u deze informatie niet hebt.

   * Open de Dynamic Media Classic-toepassing en meld u vervolgens aan bij uw account.

1. Near the upper-right corner of the page, tap **[!UICONTROL Setup > Application Setup > General Settings.]**
1. Ga naar het **[!UICONTROL CDN Invalidation Template]** tekstvak op de pagina Algemene instellingen toepassing onder de kop Servers.

1. Geef de sjabloon op die wordt gebruikt voor het ongeldig maken van de CDN-cache (Content Delivery Network).

   Stel bijvoorbeeld dat u een URL voor een afbeelding (inclusief voorinstellingen of wijzigingstoetsen) opgeeft die verwijst `<ID>`in plaats van een specifieke afbeelding-id, zoals in het volgende voorbeeld:

   `https://server.com/is/image/Company/<ID>?$product$`

   Als de sjabloon alleen bevat `<ID>`, vult Dynamic Media in `https://<server>/is/image` waar `<server>` de naam van de publicatieserver is die is gedefinieerd in Algemene instellingen en &lt;ID> de middelen zijn die zijn geselecteerd om ongeldig te worden gemaakt.

1. Klik in de rechterbenedenhoek van de pagina op **[!UICONTROL Close.]**
1. Selecteer een of meer elementen in de gebruikersinterface Dynamic Media Classic (Scene7) en klik op **[!UICONTROL File > Invalidate CDN.]** U ziet een lijst met een of meer URL&#39;s die zijn gegenereerd op basis van de sjabloon die u hebt gemaakt en het element dat u hebt geselecteerd. De URL van de server wordt gebruikt onder &quot;Gepubliceerde servernaam&quot; onder Algemene instellingen van toepassing.

   Stel dat u, terwijl de CDN-validatiesjabloon in de vorige stap is ingesteld, één afbeelding met afbeeldingselementen hebt geselecteerd met de naam `Backpack_B`. Wanneer u klikt, resulteert dit in **[!UICONTROL File > Invalidate CDN]** de volgende gegenereerde URL in de gebruikersinterface voor CDN-validatie:

   `https://server.com/is/image/Company/Backpack_B?$product$`

1. Klik in de keuzelijst URL **[!UICONTROL Continue]** om de cache voor elke specifieke URL te wissen. U kunt een URL bewerken of u kunt een URL toevoegen door deze in het vak URL-lijst te typen of te plakken. u hoeft CDN niet vooraf in te stellen om sjabloon ongeldig te maken.

   Nadat u klikt **[!UICONTROL Continue]**, wordt een indicator getoond die u een schatting van geeft hoe lang het zal duren om het geheime voorgeheugen te ontruimen.

   Als u meerdere elementen hebt geselecteerd en vervolgens op elk element hebt geklikt, wordt er naar verwezen in het opgeslagen bestand. **[!UICONTROL File > Invalidate CDN]** Daarom kunt u een verwijzing definiëren **[!UICONTROL Template URL.]** **[!UICONTROL CDN Invalidate Template]** naar elke voorinstelling voor URL-afbeeldingen waarnaar op uw website wordt verwezen (zoals productdetails, zoekresultaten enzovoort). Wanneer u vervolgens een of meer afbeeldingen selecteert om ongeldig te worden gemaakt door het cachegeheugen, vullen de URL&#39;s automatisch de interface in.

   >[!NOTE]
   >
   >Wanneer u assets selecteert en vervolgens op **[!UICONTROL File > Invalidate CDN]** klikt, gebruikt Dynamische media een ongeldige CDN-sjabloon om automatisch URL&#39;s te maken om ongeldig te maken vanaf het CDN (Content Delivery Network). Als het tekstvak **[!UICONTROL CDN Invalidate Template]** leeg is, wordt er een lege URL-lijst weergegeven. Caching bij CDN is niet gebaseerd op assets; het is gebaseerd op URL. Daarom moet u de volledige URL&#39;s die op uw website staan, kennen. Nadat u deze URL&#39;s hebt bepaald, kunt u ze eerder in de stappen toevoegen aan het tekstvak **[!UICONTROL Invalidate CDN Template]**. Vervolgens kunt u deze assets selecteren en de URL&#39;s in één stap ongeldig maken.
   >
   >U kunt ook volledige URL&#39;s aan de **[!UICONTROL Invalidate CDN]** lijst toevoegen. Als u deze aanpak volgt, is het niet nodig elementen te selecteren in Dynamic Media Classic voordat u naar de **[!UICONTROL File > Invalidate CDN]** optie gaat.

