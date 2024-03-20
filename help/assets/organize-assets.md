---
title: Uw digitale middelen organiseren
description: Organiseer uw digitale elementen, afbeeldingen, bestanden, mappen enzovoort met Experience Manager.
contentOwner: AG
role: User
feature: Asset Management,Search
exl-id: d6f815b5-e4fc-4f8c-a6c1-9e50035ab9f2
hide: true
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '795'
ht-degree: 0%

---

# Uw digitale middelen organiseren {#organize-digital-assets}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| Adobe Experience Manager (AEM) as a Cloud Service | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/organize-assets.html?lang=en) |
| AEM 6,5 | Dit artikel |

Alle digitale elementen, metagegevens en inhoud van Microsoft® Office- en PDF-documenten worden uitgepakt en doorzoekbaar gemaakt. Bij zoeken is geavanceerd filteren op elementen mogelijk en worden de juiste machtigingen volledig gerespecteerd. Metagegevens worden uitgebreid besproken in metagegevens in Digital Asset Management.

[!DNL Experience Manager Assets] ondersteunt meerdere manieren om inhoud te ordenen. U kunt de mappen hiërarchisch ordenen met behulp van mappen, maar u kunt ze ook ordenen op een ongeordende ad-hocmanier, bijvoorbeeld met tags. Gebruikers kunnen labels bewerken in de DAM Asset Editor, waar submiddelen, uitvoeringen en metagegevens worden weergegeven.

## Elementen in mappen ordenen {#organize-using-folders}

De eenvoudigste manier om elementen te ordenen, is deze in mappen op te slaan. Dit is hetzelfde als het ordenen van bestanden in mappen in uw lokale bestandssysteem. Voor meer informatie over het maken en beheren van mappen raadpleegt u [Elementen beheren](manage-assets.md). Hoe u bestanden en mappen benoemt, hoe u submappen ordent en hoe u de bestanden in deze mappen verwerkt, kan een grote invloed hebben op de manier waarop deze elementen worden verwerkt. Door consistente en geschikte naamgevingsstrategieën voor bestanden en mappen te gebruiken, samen met goede praktijken voor metagegevens, kunt u optimaal gebruikmaken van de opslagplaats voor digitale elementen.

* Gewoonlijk groeit de opslagplaats voor digitale middelen altijd. Daarom is het belangrijk om het gebruik van metagegevens, de mapstructuur en de naamgeving van bestanden vroegtijdig te formaliseren in de cyclus waarin de inhoud wordt gemaakt.
* Gebruik mappen alleen om een consistente opslagstructuur voor uw digitale elementen op te leggen. Deze consistentie helpt uw proces en beheert uw activa beter. Elementen die bijvoorbeeld in de volgende typen mappen worden geplaatst, kunnen u helpen het juiste gebruik te maken [profielen voor verwerking van bedrijfsmiddelen](processing-profiles.md):

   * **Ontwikkelingsmappen**: bevat digitale elementen waaraan u momenteel werkt.
   * **Clientmappen**: bevat digitale elementen die zijn gebaseerd op clients of projectnamen.
   * **Primaire mappen**: bevat originele, brondigitale elementen.
   * **Uitvoermappen**: bevat vertoningen en kopieën van de originele, brondigitale elementen.
   * **Bestandsgrootten, mappen**: bevat digitale elementen die zijn gebaseerd op kleine, middelgrote of grote bestanden.
   * **Mappen stapelen**: bevat digitale elementen die klaar zijn om live op uw website te publiceren.
   * **MIME-tekstmappen**: bevat digitale elementen die specifiek zijn voor MIME-typen, zoals afbeeldingen, documenten en multimedia.
   * **Mappen archiveren**: bevat gepensioneerde digitale elementen.
   * **Op datum gebaseerde mappen**: bevat digitale elementen die zijn gebaseerd op een aanmaakdatum of een datum die als laatste is gewijzigd.

* Maak een map met mappen die waarschijnlijk niet worden gewijzigd, zodat aanpassingen of automatisering gewoon kunnen doorgaan. De toegewezen verwerkingsprofielen werken bijvoorbeeld nog steeds.
* Als een element al is gepubliceerd, gebruikt u [!DNL Experience Manager] om het middel naar een andere omslag te verplaatsen, en van zijn nieuwe plaats opnieuw te publiceren, is de originele gepubliceerde activaplaats nog beschikbaar, samen met het onlangs opnieuw gepubliceerde middel. Het oorspronkelijke gepubliceerde middel is echter *verloren* tot [!DNL Experience Manager] en kan niet ongepubliceerd zijn. Daarom, als beste praktijken, eerst unpublish een middel en dan verplaats het naar een verschillende omslag.

## Elementen ordenen met tags {#use-tags-to-organize-assets}

Met tags kunt u als metagegevens eenvoudig zoeken in elementen, verzamelingen maken met behulp van zoekresultaten, de zoekpositie voor bepaalde elementen verhogen en kunstmatige intelligentiealgoritmen van Adobe Sensei gebruiken voor het detecteren van elementen.

[!DNL Adobe Experience Manager Assets] maakt gebruik van een zelfstudie-algoritme om zeer beschrijvende tags te maken waarmee u het juiste element met slechts een paar klikken kunt vinden. Slimme tags maken gebruik van Adobe Sensei, het kunstmatige intelligentie- en computerleerframework van de Adobe, dat getraind kan worden om zowel standaard- als bedrijfsspecifieke tags te herkennen en toe te passen op afbeeldingen. Met slimme tags kunt u ook inhoud, afzonderlijke woorden of zinsdelen identificeren en automatisch beschrijvende tags toepassen op elementen

Raadpleeg de volgende artikelen voor meer informatie:

* [Tags in Experience Manager](/help/sites-authoring/tags.md)
* [Metagegevens van elementen bewerken](metadata.md)
* [Verbeterde slimme tags in elementen](enhanced-smart-tags.md)

## Indelen als verzamelingen {#organize-as-collections}

Met verzamelingen van middelen in [!DNL Experience Manager Assets], kunt u de mogelijkheid om elementen te maken, te bewerken en te delen tussen gebruikers stroomlijnen. Maak verschillende soorten verzamelingen op basis van de manier waarop u ze gebruikt, waaronder verzamelingen die een statische referentielijst met elementen, mappen en verzamelingen bevatten, en verzamelingen die op basis van zoekcriteria elementen in elementen trekken. U kunt ook verzamelingen maken met elementen van verschillende locaties en deze delen met meerdere gebruikers met verschillende toegangsniveaus, weergavebevoegdheden en bewerkingsbevoegdheden.

Zie voor meer informatie [verzamelingen beheren](manage-collections.md).

<!-- TBD items: add screenshots where applicable
Any hints/recommendations of when to use what method of organizing? Some examples of how organizing helps towards a better taxonomy and improved content velocity.
Add back links to blog posts by marketing?
-->

## Uw elementen ordenen om profielen te gebruiken {#organize-to-use-profiles}

Een verwerkingsprofiel bevat [!DNL Assets] opdrachten verwerken die van toepassing zijn op elementen die worden geüpload naar vooraf gedefinieerde mappen. Profielen worden gebruikt om de verwerking van inhoud van een map of nieuw geüploade elementen te automatiseren. U kunt profielen gebruiken om uw elementen beter te ordenen.

Als u het gebruik van metagegevens, de naamgeving van bestanden en de mapstructuur gestandaardiseerd, bent u er zeker van dat u verwerkingsprofielen met grotere nauwkeurigheid en consistentie kunt toepassen op mappen wanneer de pool met digitale elementen toeneemt.

>[!MORELIKETHIS]
>
>* [Profielen voor het verwerken van metagegevens, afbeeldingen en video&#39;s](processing-profiles.md).
>* [Metagegevensprofielen](/help/assets/metadata-config.md#metadata-profiles).
>* [Videoprofielen](video-profiles.md).
>* [Dynamic Media-afbeeldingsprofielen](image-profiles.md).
