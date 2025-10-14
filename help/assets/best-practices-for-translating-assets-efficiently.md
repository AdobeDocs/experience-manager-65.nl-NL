---
title: Aanbevolen procedures voor het vertalen van middelen
description: Aanbevolen procedures voor efficiënt beheer van middelen om verschillende vertaalde versies te synchroniseren en vertaalworkflows te stroomlijnen.
contentOwner: AG
role: Admin
feature: Asset Management
exl-id: e632dcdb-b2b9-45bc-89e7-337b44b6fc61
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# Aanbevolen procedures voor het vertalen van middelen {#best-practices-for-translating-assets-efficiently}

[!DNL Adobe Experience Manager Assets] ondersteunt meertalige workflows om binaire gegevens, metagegevens en tags voor digitale elementen naar meerdere landinstellingen te vertalen en de vertaalde elementen te beheren. Voor details, zie [&#x200B; Meertalige Assets &#x200B;](multilingual-assets.md).

Voor efficiënt beheer van activa om ervoor te zorgen dat de verschillende vertaalde versies gesynchroniseerd blijven, creeer [&#x200B; taalexemplaren &#x200B;](preparing-assets-for-translation.md) van activa alvorens vertaalwerkschema&#39;s in werking te stellen.

Een taalkopie van een element of een groep elementen is een op hetzelfde niveau staande taal (of een versie van de elementen in een cognattaal) met een vergelijkbare inhoudshiërarchie.

Elke taalkopie is een onafhankelijk middel. Daarom kan het omzetten van middelen in meerdere landinstellingen de grootte van de CRX-opslagplaats drastisch verhogen. Bijvoorbeeld, kan het vertalen van activa met een gecombineerde grootte van 10 GB in twee talen de bewaarplaatgrootte met ongeveer 20 GB (10 GB voor elke taal) verhogen.

Middelenbinaire getallen nemen veel meer opslagruimte in beslag dan metagegevens en tags. Als het vertalen van metagegevens en tags alleen uw doel dient, laat u daarom weg om de binaire getallen te vertalen. U kunt de originele kopie van de binaire bestanden in de opslagplaats behouden, zodat u ze kunt koppelen aan metagegevens en tags die naar verschillende landinstellingen zijn vertaald. Door één kopie van binaire bestanden te onderhouden in plaats van meerdere vertaalde versies, wordt de invloed op de grootte van de opslagplaats beperkt.

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

1. Schakel de [!UICONTROL Set last modified date] -workflow in.

   De workflow van [!UICONTROL DAM MetaData Writeback] configureert de datum die als laatste is gewijzigd voor een element. Omdat u deze workflow in stap 2 uitschakelt, kan [!DNL Assets] de laatste gewijzigde datum van de elementen niet meer up-to-date houden. Daarom laat *reeks laatste gewijzigde datum* werkschema toe om ervoor te zorgen dat de laatste gewijzigde data van activa bijgewerkt zijn. Assets met verouderde datums die als laatste zijn gewijzigd, kan fouten veroorzaken.

1. [&#x200B; vorm het kader van de vertaalintegratie &#x200B;](/help/sites-administering/tc-tic.md) ophouden vertalend activa binaries. Schakel de optie **[!UICONTROL Translate Assets]** onder het tabblad [!UICONTROL Assets] uit om het vertalen van binaire elementen te stoppen.
1. Vertaal activa meta-gegevens/markeringen gebruikend [&#x200B; Meertalige activawerkschema&#39;s &#x200B;](multilingual-assets.md).
