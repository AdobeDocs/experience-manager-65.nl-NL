---
title: CDN-inhoud in cache ongeldig maken
description: Door de CDN-inhoud (Content Delivery Network) in de cache te ongeldig te maken, kunt u snel elementen bijwerken die door Dynamic Media worden geleverd, in plaats van te wachten tot de cache verloopt.
uuid: 0fd88e31-9745-4c98-a245-9f5d0766cad4
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: e6c9b50b-c27c-48bf-b3c0-9994e7bf6d7e
translation-type: tm+mt
source-git-commit: 0595d89409e0ca21f771be5c55c3ec9548a8449f

---


# CDN-inhoud in cache ongeldig maken {#invalidating-your-cdn-cached-content}

Dynamische media-elementen worden door de CDN in cache geplaatst voor snelle levering. Wanneer u echter updates aan een element aanbrengt, wilt u deze wijzigingen mogelijk direct van kracht laten worden. Door de CDN-inhoud (Content Delivery Network) in de cache te ongeldig te maken, kunt u snel elementen bijwerken die door Dynamic Media worden geleverd, in plaats van te wachten tot de cache verloopt.

Zie ook [Cacheoverzicht in Dynamische Klassieke Media (Scene7)](https://helpx.adobe.com/experience-manager/scene7/kb/base/caching-questions/scene7-caching-overview.html).

**Om uw CDN caching inhoud ongeldig te maken:**

1. Logon aan uw Dynamische Klassieke (Scene7) rekening van Media:

   [https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html)

   Adobe heeft uw gegevens en aanmeldingsgegevens opgegeven op het moment van de provisioning. Neem contact op met Technische ondersteuning als u deze informatie niet hebt.

1. Klik op **[!UICONTROL Setup > Application Setup > General Settings]**.
1. Zoek op de pagina Algemene instellingen van toepassing onder de kop Groep Servers het tekstvak **[!UICONTROL CDN-validatiesjabloon]** .

1. Geef de sjabloon op die wordt gebruikt voor het ongeldig maken van de CDN-cache (Content Delivery Network).

   Stel bijvoorbeeld dat u een URL voor een afbeelding (inclusief voorinstellingen of wijzigingstoetsen) opgeeft `<ID>`in plaats van een specifieke afbeeldings-id, zoals in het volgende voorbeeld:

   `https://server.com/is/image/Company/<ID>?$product$`

   Als de sjabloon alleen bevat `<ID>`, vult Dynamic Media in `https://<server>/is/image` waar `<server>` de naam van de publicatieserver is die is gedefinieerd in Algemene instellingen en &lt;ID> de middelen zijn die zijn geselecteerd om ongeldig te worden gemaakt.

1. Klik in de rechterbenedenhoek van de pagina op **[!UICONTROL Sluiten]**.
1. In Dynamische Media Klassieke (Scene7) UI, selecteer één of meerdere activa, dan klik **[!UICONTROL Dossier > ongeldig maakt CDN]**. Er wordt een lijst weergegeven met een of meer URL&#39;s die zijn gegenereerd op basis van de sjabloon die u hebt gemaakt en de elementen die u hebt geselecteerd. De URL van de server wordt gebruikt onder &quot;Gepubliceerde servernaam&quot; onder Algemene instellingen van toepassing.

   Stel dat u, terwijl de CDN-validatiesjabloon in de vorige stap is ingesteld, één afbeelding met afbeeldingselementen hebt geselecteerd met de naam `Backpack_B`. Wanneer u klikt op **[!UICONTROL Bestand > CDN]** ongeldig maken, resulteert dit in de volgende gegenereerde URL in de gebruikersinterface voor CDN-validatie:

   `https://server.com/is/image/Company/Backpack_B?$product$`

1. Klik in de keuzelijst URL op **[!UICONTROL Doorgaan]** om de cache voor elke specifieke URL te wissen. U kunt een URL bewerken of u kunt een URL toevoegen door deze in het vak URL-lijst te typen of te plakken. u hoeft CDN niet vooraf in te stellen om sjabloon ongeldig te maken.

   Nadat u op **[!UICONTROL Doorgaan]** hebt geklikt, wordt een indicator weergegeven waarmee u kunt inschatten hoe lang het duurt om de cache te wissen.

   Als u meerdere elementen hebt geselecteerd en u vervolgens op **[!UICONTROL Bestand > CDN]** ongeldig maken hebt geklikt, wordt naar elk element verwezen in de opgeslagen **[!UICONTROL sjabloon-URL]**. Daarom kunt u een **[!UICONTROL CDN definiëren voor het ongeldig maken van een sjabloon]** die verwijst naar elke voorinstelling voor een URL-afbeelding waarnaar op uw website wordt verwezen (zoals productdetails, zoekresultaten enzovoort). Wanneer u vervolgens een of meer afbeeldingen selecteert om te worden geannuleerd door het cachegeheugen, vullen de URL&#39;s automatisch de interface in.

   >[!NOTE]
   >
   >Wanneer u elementen selecteert en vervolgens op **[!UICONTROL Bestand > CDN]** ongeldig maken klikt, gebruikt Dynamic Media een CDN-sjabloon voor ongeldig maken om automatisch URL&#39;s te maken die ongeldig worden gemaakt via het CDN (Content Delivery Network). Als het tekstvak Sjabloon **[!UICONTROL ongeldig maken niets bevat in het tekstvak]** CDN, wordt er een lege URL-lijst weergegeven. Caching bij CDN is geen op activa-gebaseerd; het is gebaseerd op URL. Daarom is het nodig om op de hoogte te zijn van de volledige URL&#39;s die op uw website staan. Nadat u die URLs bepaalt, kunt u hen toevoegen aan **[!UICONTROL ongeldig maken CDN Sjabloon]** vroeger in de stappen. Vervolgens kunt u deze elementen selecteren en de URL&#39;s in één stap ongeldig maken.
   >
   >U kunt ook volledige URL&#39;s toevoegen aan de lijst **[!UICONTROL Ongeldige CDN]** . Als u deze benadering volgt, is het onnodig om activa in Dynamische Media Klassiek te selecteren alvorens naar het **[!UICONTROL Dossier > CDN]** ongeldig te maken optie te gaan.

