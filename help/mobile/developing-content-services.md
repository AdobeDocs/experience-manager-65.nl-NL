---
title: Inhoudsservices
description: Leer hoe u AEM Mobile Content Services gebruikt om inhoud aan te vragen die door AEM wordt beheerd.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
exl-id: 955ffb1c-4fa9-43bb-8e5b-2df7f2d17951
solution: Experience Manager
feature: Mobile
role: Developer
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 0%

---

# Inhoudsservices{#content-services}

>[!NOTE]
>
>De Adobe adviseert het gebruiken van de SPARedacteur voor projecten die op kader-gebaseerde cliënt-zijteruggeven van enige paginatoepassing (bijvoorbeeld, Reageren) vereisen. [Meer informatie](/help/sites-developing/spa-overview.md).

>[!CAUTION]
>
>De functie Inhoudsservices wordt alleen voor voorvertoningen beschreven.
>
>Het is onderhevig aan verandering met de versie van 6.3 Service Pack 1.

AEM Mobile Content Services is een lichtgewicht functie voor het aanvragen van inhoud die door AEM wordt beheerd. Dit biedt alle ontwikkelaars van apps een krachtige manier om inhoud op te halen zonder dat ze diepgaande kennis hoeven te hebben van AEM opslagplaats voor inhoud (JCR) en webframework (Sling). Hierdoor kunnen de toepassingen die u aanvraagt, worden losgekoppeld van de opslagplaats voor inhoud.

De Diensten van de inhoud introduceert verscheidene nieuwe AEM constructies die een ontwikkelaar toegang AEM-beheerde inhoud zonder kennis van de bewaarplaatstructuur van die inhoud laten.

Deze constructies zijn nodig om flexibiliteit te behouden en toekomstige uitbreiding mogelijk te maken door een abstractielaag te maken tussen de inhoud met AEM beheer en de mobiele apps die de inhoud verbruiken. Hierdoor kunnen AEM Content Services werken als een abstractielaag tussen de inhoudsvereisten van de native toepassing en de opslagplaats voor AEM inhoud.

Content Services kan de inhoud leveren als elementen, verpakte HTML (HTML/CSS/JS) of als kanaalonafhankelijke inhoud.

>[!CAUTION]
>
>**Vereisten:**
>
>Alvorens u met de Diensten van de Inhoud begint, zorg ervoor dat u de vlag van de Diensten van de Inhoud toelaat. Als u het maken en beheren van modellen in uw app wilt inschakelen, schakelt u gegevensmodellen in de configuratiegrowser in.
>
>Zie **[Inhoudsservices beheren](/help/mobile/developing-content-services.md)** en de [Configuratiebrowser](/help/sites-administering/configurations.md) documentatie voor meer informatie.

![chlimage_1-143](assets/chlimage_1-143.png)

Nadat u de vlag van de Diensten van de Inhoud, en toegelaten gegevensmodellen in Browser van de Configuratie hebt geplaatst, zie de middelen hieronder om met de Diensten van de Inhoud van AEM Mobile te beginnen. Word vertrouwd met de Concepten van de Diensten van de Inhoud zoals modelbeheer, entiteitbeheer gevolgd door inhoudlevering/het teruggeven voor de Diensten van de Inhoud van AEM Mobile.

* Modellen in opslagplaats
* Rendering en levering
