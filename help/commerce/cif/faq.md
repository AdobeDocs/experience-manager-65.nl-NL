---
title: AEM - Veelgestelde vragen over integratie van de handel met behulp van het kader voor integratie van de handel
description: AEM - Veelgestelde vragen over integratie van de handel met behulp van het kader voor integratie van de handel
exl-id: d541607f-c4c9-4dd5-aadf-64d4cb5f9f2a
source-git-commit: a2ababa9dd9115e963b91a7271d204d287557c40
workflow-type: tm+mt
source-wordcount: '963'
ht-degree: 0%

---

# AEM - Veelgestelde vragen over integratie van de handel met behulp van het kader voor integratie van de handel

## 1. Wordt CIF GraphQL alleen gebruikt voor handel of is dit beschikbaar voor het opvragen van inhoud die is geschreven op AEM JCR?

Adobe heeft GraphQL API&#39;s van Adobe Commerce aangenomen als de officiële API voor de handel voor alle handelsgerelateerde gegevens. Daarom gebruikt AEM GraphQL om handelsgegevens met Adobe Commerce en met om het even welke handelmotor via I/O Runtime uit te wisselen. Deze GraphQL API is onafhankelijk van AEM GraphQL API voor toegang tot Content Fragments.

## 2. Kunnen de activa van het Product (beelden) van AEM via Adobe Commerce worden opgeslagen en van verwijzingen voorzien admin? Hoe kunnen activa van Dynamic Media worden verbruikt?

Er is geen officiële AEM Assets - Adobe Commerce-integratie beschikbaar. Er is een partnerschakelaar beschikbaar op [marktplaats](https://marketplace.magento.com/bounteous-dam.html).

Of als tijdelijke oplossing kunt u productelementen (afbeeldingen) opslaan in AEM Assets, maar u moet de URL&#39;s van de middelen handmatig opslaan in Adobe Commerce. Dynamic Media maakt nu deel uit van AEM Assets en zal op dezelfde manier werken.

## 3. Maakt het uit waar de handelsoplossing wordt ingezet? (Op prem of in de cloud)

Nee, het maakt niet uit waar uw handelsoplossing wordt geïmplementeerd. CIF en de AEM zullen werken ongeacht het plaatsingsmodel. Als de oplossing echter wordt geïmplementeerd met de aanbevolen E2E-referentiearchitectuur, kunnen E2E-tests worden uitgevoerd met prestatie-KPI&#39;s die een typisch bedrijfsklantprofiel vertegenwoordigen. Dit zal aanvullende informatie opleveren die als benchmark kan worden gebruikt.

## 4. Hoe worden cataloguspagina&#39;s of productpagina&#39;s in AEM gemaakt? Hoe blijven ze in AEM?

Cataloguspagina&#39;s en productpagina&#39;s worden dynamisch gemaakt en in het cachegeheugen opgeslagen in AEM op basis van algemene catalogussjablonen en productpaginasjablonen. Er worden geen product- of catalogusgegevens geïmporteerd en opgeslagen in AEM.

## 5. Wanneer u productgegevens in uw handelsoplossing bijwerkt, is dat een duw in real time aan AEM? Of is het een batchproces?

CIF toe:voegen-op gebruikt met AEM laat gegevens toe om van de handelsoplossing aan AEM op bestelling te stromen. Daarom is dit geen real-time duw of een partijproces wanneer er een update in uw handelsoplossing is.

## 6. Welke catalogusgrootte AEM CIF-ondersteuning?

Dit hangt af van een paar extra aspecten die u in overweging moet nemen. Wat is de cacheverhouding van uw catalogusgegevens en -pagina&#39;s? Hoeveel gezamenlijke verzoeken verwacht u tijdens piekuren? Hoe scalable zijn APIs van uw handelsoplossingen?

## 7. Hoe speelt PIM in dit kader?

PIM-gegevens worden via GraphQL-verzoeken aan AEM en clients beschikbaar gesteld. Onze aanbeveling is om PIM te integreren met de motor van de handel (Adobe Commerce of anderen) zodat PIM-gegevens kunnen worden opgehaald van de motor van de handel.

## 8. Verzendt u ook de prijzen en andere gegevens in cache via Dispatcher. Vormt dat een veelvuldige uitdaging voor het ongeldig maken van cache?

Dynamische gegevens zoals prijs of voorraad worden niet in de cache opgeslagen op de Dispatcher. Dynamische gegevens worden via GraphQL API&#39;s rechtstreeks via de client-side opgehaald met webcomponenten. Alleen statische gegevens (zoals product- of categoriegegevens) worden in cache geplaatst op de Dispatcher. Als de productgegevens veranderen, zal er een behoefte aan geheim voorgeheugenbevestiging zijn.

## 9. Hoe werkt cachevervalsing voor AEM Dispatcher met AEM en handel?

We raden u aan op TTL gebaseerde cachevalidatie in te stellen voor pagina&#39;s die in cache zijn geplaatst op de Dispatcher. Voor dynamische informatie zoals prijs of voorraad raden we aan de datumclient-kant weer te geven. Voor meer informatie over op TTL-Gebaseerde geheim voorgeheugenongeldigverklaring, gelieve te verwijzen naar [AEM Dispatcher](https://helpx.adobe.com/experience-manager/kb/optimizing-the-dispatcher-cache.html)

## 10 Bestaat er een aanbeveling voor een uniforme zoekopdracht in AEM inhoud met Commerce?

Er is een verwijzingsimplementatie voor productzoekopdrachten beschikbaar, maar er is geen uniforme zoekopdracht met inhoud. Deze eigenschap is gewoonlijk zeer klantspecifiek en beter opgelost op een project-specifiek niveau.

## 11. Hoe werkt Search met AEM en handel die CIF gebruiken?

CIF verstrekt de bar van het Onderzoek en de componenten van het Resultaat van het Onderzoek. De component van de bar van het Onderzoek verzendt een verzoek van GraphQL met de onderzoekstermijn naar de handelsoplossing die dan een productlijst terugkeert die productnaam, prijs, SLUG, enz. omvat. De component van het Resultaat van het Onderzoek toont dan de onderzoeksresultaten in een galeriemening op een pagina van het onderzoeksresultaat die in AEM wordt gecreeerd. De zoekfunctie ondersteunt standaard zoeken in volledige tekst. Wij gebruiken de sleutel SLUG/url om een verwijzing naar PDP te bouwen.

## 12. Hoe kunnen productgegevens in MSM of vertalingen worden gebruikt?

Productgegevens worden meestal al vertaald in PIM of in Adobe Commerce. De integratie AEM - Adobe Commerce ondersteunt de verbinding met meerdere Adobe Commerce-winkels en -winkelweergaven. In een MSM-installatie is doorgaans één AEM site gekoppeld aan één Adobe Commerce-winkelweergave.

## 13. Is er een manier om de productgegevens te verbeteren met commerciële tekst? Waar doe je dit? In AEM of in de handelsoplossing?

We raden u aan marketinggerelateerde gegevens en inhoud in AEM te beheren. Decoreer productgegevens van uw handelsoplossing met extra attributen gebruikend de Fragmenten van de Inhoud of creeer en verbind de Fragmenten van de Ervaring voor ongestructureerde inhoud met uw producten.

## 14. Hoe kunnen wij naleving PCI verzekeren wanneer het gebruiken van AEM voor de volledige presentatielaag?

We raden je aan geabstraheerde betalingsmethoden te gebruiken. Dit zet de browser cliënt in directe communicatie met de leverancier van de betaalgateway zodat noch Adobe of de handelsoplossingen kaarthoudende gegevens houden of overgaan. Deze benadering vereist slechts niveau 3 naleving PCI. Nochtans, zijn er extra dingen om als volledig PCI volgzaam te beschouwen zoals hoe de werknemers met het systeem en de gegevens in wisselwerking staan. Voor meer informatie over Adobe Commerce PCI-compatibiliteit raadpleegt u [PCI-compatibiliteit](https://business.adobe.com/products/magento/pci-compliance.html)

## 15. Als ik gebruik van AEM en Adobe Commerce cloud-versies, is deze gezamenlijke oplossing PCI-compatibel?

Ja, de zelfbeoordelingsvragenlijst D en de verklaring van naleving zijn op verzoek beschikbaar.

## 16. Hoe kan ik om een I/O Runtime proefvergunning verzoeken?

U kunt een proeflicentie aanvragen om I/O Runtime te gebruiken [hier](https://adobeio.typeform.com/to/obqgRm).
