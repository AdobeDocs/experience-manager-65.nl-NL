---
title: Aanbevolen procedures voor het vertalen van middelen
description: Aanbevolen procedures voor efficiënt beheer van middelen om verschillende vertaalde versies te synchroniseren en vertaalworkflows te stroomlijnen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 566add37d6dd7efe22a99fc234ca42878f050aee
workflow-type: tm+mt
source-wordcount: '482'
ht-degree: 1%

---


# Aanbevolen procedures voor het vertalen van middelen {#best-practices-for-translating-assets-efficiently}

Adobe Experience Manager-middelen ondersteunen meertalige workflows om binaire gegevens, metagegevens en tags voor digitale middelen naar meerdere landinstellingen te vertalen en de vertaalde middelen te beheren. Zie [Meertalige elementen](multilingual-assets.md)voor meer informatie.

Voor efficiënt beheer van middelen om ervoor te zorgen dat verschillende vertaalde versies gesynchroniseerd blijven, creeer [taalexemplaren](preparing-assets-for-translation.md) van activa alvorens vertaalwerkschema&#39;s in werking te stellen.

Een taalkopie van een element of een groep elementen is een op hetzelfde niveau staande taal (of een versie van het element of de elementen in een cognattaal) met een vergelijkbare inhoudshiërarchie.

Elke taalkopie is een onafhankelijk middel. Daarom kan het omzetten van middelen in meerdere landinstellingen de grootte van de CRX-opslagplaats drastisch verhogen. Bijvoorbeeld, kan het vertalen van activa met een gecombineerde grootte van 10 GB in twee talen de bewaarplaatgrootte met ongeveer 20 GB (10 GB voor elke taal) verhogen.

Middelenbinaire getallen nemen veel meer opslagruimte in beslag dan metagegevens en tags. Als het vertalen van metagegevens en tags alleen uw doel dient, laat u daarom weg om de binaire getallen te vertalen. U kunt de originele kopie van de binaire bestanden in de opslagplaats behouden, zodat u ze kunt koppelen aan metagegevens en tags die naar verschillende landinstellingen zijn vertaald. Door één kopie van binaire bestanden te onderhouden in plaats van meerdere vertaalde versies, wordt de invloed op de grootte van de opslagplaats tot een minimum beperkt.

Bestandsgegevensopslag en Amazon S3 Data Store bieden een opslaginfrastructuur die het meest geschikt is voor deze scenario&#39;s. In deze opslagopslagopslagruimten wordt één kopie van de binaire elementen (inclusief uitvoeringen) opgeslagen die door metagegevens en tags in meerdere landinstellingen kunnen worden gedeeld. Daarom heeft het maken van kopieën van de taal van het middel en het vertalen van metagegevens en tags geen invloed op de grootte van de opslagplaats.

U kunt ook enkele configuratiewijzigingen aanbrengen in een aantal workflows en het vertaalintegratieframework om het proces verder te stroomlijnen.

1. Voer een van de volgende handelingen uit:

   * [Bestandsgegevensopslag instellen](/help/sites-deploying/data-store-config.md)
   * [Amazon S3 Data Store instellen](/help/sites-deploying/data-store-config.md)

1. Schakel de [DAM MetaData Write-back](/help/sites-administering/workflow-offloader.md#disable-offloading) workflow uit.

   Zoals de naam al aangeeft, worden de metagegevens in de [!UICONTROL DAM Metadata Writeback] workflow opnieuw genoteerd naar het binaire bestand. Omdat de metagegevens na de vertaling veranderen, wordt bij het terugschrijven naar het binaire bestand een andere binaire waarde voor een taalkopie gegenereerd.

   >[!NOTE]
   >
   >Als u de [!UICONTROL DAM MetaData Writeback] workflow uitschakelt, wordt het wegschrijven van XMP-metagegevens naar binaire bestanden met elementen uitgeschakeld. Daarom worden toekomstige wijzigingen in metagegevens niet meer opgeslagen in de elementen. Evalueer de gevolgen voordat u deze workflow uitschakelt.

1. Schakel de [!UICONTROL Set last modified date] workflow in.

   De [!UICONTROL DAM MetaData Writeback] workflow configureert de laatste gewijzigde datum voor een element. Omdat u deze workflow in stap 2 uitschakelt, kunnen elementen de laatste gewijzigde datum van de elementen niet meer up-to-date houden. Schakel daarom de workflow Laatste gewijzigde datum ** instellen in om ervoor te zorgen dat de laatste gewijzigde datums van de elementen up-to-date zijn. Elementen met verouderde datums die als laatste zijn gewijzigd, kunnen fouten veroorzaken.

1. [Configureer het vertaalintegratieframework](/help/sites-administering/tc-tic.md) om te stoppen met het vertalen van binaire elementen. Hef de selectie van de **[!UICONTROL Translate Assets]** optie onder het tabblad Middelen op om de vertaling van binaire elementen te stoppen.
1. Metagegevens/tags van elementen vertalen met behulp van [meertalige middelenworkflows](multilingual-assets.md).
