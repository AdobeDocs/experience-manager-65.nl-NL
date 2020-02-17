---
title: Inhoudsservices
seo-title: Inhoudsservices
description: 'null'
seo-description: 'null'
uuid: 7bd09c91-3931-400b-bdfc-b064b9ca9668
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
discoiquuid: 6a7e5472-cb57-4c78-b183-7c6dcac11a4e
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Inhoudsservices{#content-services}

>[!NOTE]
>
>Adobe adviseert gebruikend de Redacteur van het KUUROORD voor projecten die op kader-gebaseerde cliënt-zijteruggeven van enige paginatoepassing (b.v. Reageren) vereisen. [Meer](/help/sites-developing/spa-overview.md)informatie.

>[!CAUTION]
>
>De functie Inhoudsservices wordt alleen voor voorvertoningen beschreven.
>
>Deze kan worden gewijzigd met de release van 6.3 GA Service Pack 1.

AEM Mobile Content Services is een lichtgewicht functie voor het aanvragen van inhoud die door AEM wordt beheerd. Dit biedt alle ontwikkelaars van apps een krachtige manier om inhoud op te halen zonder dat ze diepgaande kennis hoeven te hebben van de JCR (Content repository) en het webframework (Sling) van AEM. Hierdoor kunnen de toepassingen die u aanvraagt, worden losgekoppeld van de opslagplaats voor inhoud.

Content Services introduceert verschillende nieuwe AEM-constructies waarmee een ontwikkelaar toegang heeft tot door AEM beheerde inhoud zonder kennis van de opslagstructuur van die inhoud.

Deze constructies zijn nodig om flexibiliteit te behouden en toekomstige uitbreiding mogelijk te maken door een abstractielaag te maken tussen de door AEM beheerde inhoud en de mobiele apps die de inhoud verbruiken. Hierdoor kunnen AEM Content Services werken als een abstractielaag tussen de inhoudseisen van de native toepassing en de AEM content-opslagplaats.

Content Services kan de inhoud leveren als elementen, verpakte HTML (HTML/CSS/JS) of als kanaalonafhankelijke inhoud.

>[!CAUTION]
>
>**Vereisten:**
>
>Voordat u aan de slag gaat met Content Services, moet u ervoor zorgen dat de vlag Content Services is ingeschakeld. Als u het maken en beheren van modellen in uw app wilt inschakelen, moet u gegevensmodellen inschakelen in de configuratiegrowser.
>
>Zie **[Inhoudsservices](/help/mobile/developing-content-services.md)**beheren voor meer informatie.

![chlimage_1-143](assets/chlimage_1-143.png)

Zodra u de vlag van de Diensten van de Inhoud en toegelaten gegevensmodellen in Browser van de Configuratie hebt geplaatst, zie de middelen hieronder beginnen met de Diensten van de Inhoud van AEM Mobiele Inhoud, vertrouwd worden met Concepten van de Diensten van de Inhoud zoals modelbeheer, entiteitbeheer dat door tevreden levering/het teruggeven voor de Diensten van de Inhoud van AEM Mobiele wordt gevolgd.

* Modellen in opslagplaats
* Rendering en levering

