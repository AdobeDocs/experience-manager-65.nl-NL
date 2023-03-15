---
title: Aanbevolen procedures voor het vertalen van middelen
description: Aanbevolen procedures voor efficiënt beheer van middelen om verschillende vertaalde versies te synchroniseren en vertaalworkflows te stroomlijnen.
contentOwner: AG
role: Admin
feature: Asset Management
exl-id: e632dcdb-b2b9-45bc-89e7-337b44b6fc61
source-git-commit: bb46b0301c61c07a8967d285ad7977514efbe7ab
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 1%

---

# Aanbevolen procedures voor het vertalen van middelen {#best-practices-for-translating-assets-efficiently}

[!DNL Adobe Experience Manager Assets] biedt ondersteuning voor meertalige workflows voor het vertalen van binaire bestanden, metagegevens en tags voor digitale elementen naar meerdere landinstellingen en het beheren van de vertaalde middelen. Zie voor meer informatie [Meertalige activa](multilingual-assets.md).

Voor een efficiënt beheer van middelen, zodat verschillende vertaalde versies gesynchroniseerd blijven, kunt u [taalkopieën](preparing-assets-for-translation.md) van elementen voordat u vertaalworkflows uitvoert.

Een taalkopie van een element of een groep elementen is een op hetzelfde niveau staande taal (of een versie van het element of de elementen in een cognattaal) met een vergelijkbare inhoudshiërarchie.

Elke taalkopie is een onafhankelijk middel. Daarom kan het omzetten van middelen in meerdere landinstellingen de grootte van de CRX-opslagplaats drastisch verhogen. Bijvoorbeeld, kan het vertalen van activa met een gecombineerde grootte van 10 GB in twee talen de bewaarplaatgrootte met ongeveer 20 GB (10 GB voor elke taal) verhogen.

Middelenbinaire getallen nemen veel meer opslagruimte in beslag dan metagegevens en tags. Als het vertalen van metagegevens en tags alleen uw doel dient, laat u daarom weg om de binaire getallen te vertalen. U kunt de originele kopie van de binaire bestanden in de opslagplaats behouden, zodat u ze kunt koppelen aan metagegevens en tags die naar verschillende landinstellingen zijn vertaald. Door één kopie van binaire bestanden te onderhouden in plaats van meerdere vertaalde versies, wordt de invloed op de grootte van de opslagplaats tot een minimum beperkt.

Bestandsgegevensopslag en Amazon S3 Data Store bieden een opslaginfrastructuur die het meest geschikt is voor deze scenario&#39;s. In deze opslagopslagopslagruimten wordt één kopie van de binaire elementen (inclusief uitvoeringen) opgeslagen die door metagegevens en tags in meerdere landinstellingen kunnen worden gedeeld. Daarom heeft het maken van kopieën van de taal van het middel en het vertalen van metagegevens en tags geen invloed op de grootte van de opslagplaats.

U kunt ook enkele configuratiewijzigingen aanbrengen in een aantal workflows en het vertaalintegratieframework om het proces verder te stroomlijnen.

1. Voer een van de volgende handelingen uit:

   * [Bestandsgegevensopslag instellen](/help/sites-deploying/data-store-config.md)
   * [Amazon S3 Data Store instellen](/help/sites-deploying/data-store-config.md)

<!--
1. Disable the [DAM MetaData Write-back](/help/sites-administering/workflow-offloader.md#disable-offloading) workflow.

   As the name suggests, the [!UICONTROL DAM Metadata Writeback] workflow rewrites the metadata to the binary file. Because the metadata changes after translation, writing it back to the binary file generates a different binary for a language copy.

   >[!NOTE]
   >
   >Disabling the [!UICONTROL DAM MetaData Writeback] workflow turns off XMP metadata write-back on asset binaries. Consequently, future metadata changes are no longer be saved within the assets. Evaluate the consequences before disabling this workflow.
-->

1. De optie [!UICONTROL Set last modified date] workflow.

   De [!UICONTROL DAM MetaData Writeback] wordt de datum van de laatste wijziging voor een element geconfigureerd. Omdat u deze workflow in stap 2 uitschakelt, [!DNL Assets] kan de laatste gewijzigde datum van de activa niet meer actueel houden. Daarom moet de *Laatst gewijzigde datum instellen* workflow om ervoor te zorgen dat de laatste gewijzigde datums van de elementen up-to-date zijn. Elementen met verouderde datums die als laatste zijn gewijzigd, kunnen fouten veroorzaken.

1. [Het vertaalintegratieframework configureren](/help/sites-administering/tc-tic.md) om het vertalen van binaire elementen te stoppen. De selectie van **[!UICONTROL Translate Assets]** optie onder de [!UICONTROL Assets] om de vertaling van binaire elementen te stoppen.
1. Metagegevens/tags van elementen vertalen met [Meertalige workflows voor bedrijfsmiddelen](multilingual-assets.md).
