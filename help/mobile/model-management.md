---
title: Modellen - overzicht
description: Leer hoe u modelbeheer kunt gebruiken waarbij modellen worden gemaakt en beheerd voor het koppelen aan uiteindelijke gegevensobjecten.
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
exl-id: 50785534-5784-4354-b123-5e640b7c0242
solution: Experience Manager
feature: Mobile
role: Admin
source-git-commit: 2dae56dc9ec66f1bf36bbb24d6b0315a5f5040bb
workflow-type: tm+mt
source-wordcount: '763'
ht-degree: 0%

---

# Modellen - overzicht{#models-overview}

{{ue-over-mobile}}

Modelbeheer omvat het maken en beheren van modellen voor het koppelen aan uiteindelijke gegevensobjecten. Elk model bevat alle eigenschappen en velddefinities die nodig zijn om het maken en renderen van objecten te vergemakkelijken.

Het modelbeheer impliceert de verwezenlijking van **modellen**, **entiteiten**, en **ruimten**. Het volgende diagram illustreert de relatie tussen de AEM Inhoud en de modellen.

![ chlimage_1-81 ](assets/chlimage_1-81.png)

## Het inhoudsmodel {#the-content-model}

Een model beschrijft het type inhoud en geeft aan welke informatie beschikbaar is voor de native toepassing. Het is een beschrijving van wat uit een stuk van inhoud bestaat. Een inhoudsmodel is de regels voor het bouwen van inhoud. Het inhoudsmodel bevat welke gegevens beschikbaar zijn, welke elementen kunnen worden gebruikt, de relatie tussen elementen en gegevens, de relatie met andere inhoudsmodellen en de beschikbare metagegevens.

Modellen dienen ook als een manier om bestaande AEM-inhoud te transformeren in objecten die gemakkelijk kunnen worden gebruikt door systeemeigen mobiele apps.

Content Services biedt een aantal out-of-the-box-modellen voor veelvoorkomende objecten, zoals elementen, verzamelingen van middelen, HTML-pagina&#39;s, toepassingsconfiguraties en pagina&#39;s die onafhankelijk zijn van kanalen. Deze zijn configureerbaar zodat kunnen zij aan specifieke klantenbehoeften voldoen zonder een AEM ontwikkelingsinspanning te vereisen.

Gebruikers kunnen hun eigen modellen maken. Hierdoor kunnen nieuwe inhoudstypen worden gemaakt die nog niet door AEM worden beheerd. Het maken van modellen gebeurt via een gebruikersinterface met behulp van bestaande primitieve typen.

In het volgende diagram ziet u het inhoudsmodel voor AEM Mobile Apps en hoe entiteiten, mappen en spaties worden toegewezen aan een app.

![ chlimage_1-82 ](assets/chlimage_1-82.png)

### De modellen {#the-models}

Modellen worden gebruikt om te bepalen hoe entiteiten worden gemaakt. Zij bepalen wat in een entiteit beschikbaar is en hoe dat gegeven van AEM inhoud wordt geproduceerd. Voordat u begint te werken met ruimten, mappen en entiteiten, moet u vertrouwd zijn met het maken en beheren van modellen.

>[!NOTE]
>
>Een model bestaat buiten een app omdat meerdere apps het kunnen gebruiken.
>

Om modellen in het dashboard en de bewaarplaats tot stand te brengen en te beheren, zie **[Modellen](/help/mobile/administer-mobile-apps.md)**.

### Entiteiten in inhoudsmodel {#entities-in-content-model}

Een entiteit is een instantie van een inhoudsmodel. Een entiteit wordt via de Content Services API blootgesteld aan de bibliotheek aan de clientzijde en biedt een manier voor een native app om inhoud op een kanaalonafhankelijke manier te benaderen.

Als er bestaande AEM inhoud is, wordt een entiteit gegenereerd met behulp van een model en de AEM inhoudsbron. Een pagina-entiteit is bijvoorbeeld een kanaal- en indelingsonafhankelijk object dat wordt gegenereerd op basis van een AEM pagina en het paginamodel.

Wijzigingen in de inhoud waarnaar wordt verwezen van een entiteit leiden tot een wijziging in de entiteit. Bijvoorbeeld, als a *cq:pagina* wordt bijgewerkt, dan worden om het even welke entiteiten die op die pagina gebaseerd zijn bijgewerkt, ook.

Om douaneentiteiten van modellen tot stand te brengen, zie **[Werkend met Entiteiten](/help/mobile/spaces-and-entities.md)**.

>[!NOTE]
>
>Als het model niet aan bestaande AEM inhoud beantwoordt, zoals de klant creeerde een model, dan is er een UI zodat kan een klant een entiteit tot stand brengen.
>

### Spaties in inhoudsmodel {#spaces-in-content-model}

Een spatie wordt gebruikt om entiteiten te organiseren voor eenvoudige toegang. Een spatie kan een of meer eenheidstypes bevatten en kan submappen bevatten.

Aan de AEM kant is een spatie een handige manier om verwante entiteiten te beheren. Het kan ook worden gebruikt om toestemmingen toe te wijzen. U kunt toestemming geven aan een ruimte, die de entiteiten in die ruimte beschermt.

*bijvoorbeeld*,

Een gebruiker heeft drie algemene classificaties van entiteiten. Het ene is alleen voor intern gebruik, het andere is goedgekeurd voor openbaar gebruik en het derde is nog steeds voor algemene entiteiten die door veel apps worden gebruikt. Om het gemakkelijk te maken om te leiden, creeert de gebruiker drie ruimten namelijk *intern*, *openbaar* (met zowel Engelse als Franse inhoud), en *gemeenschappelijk* voor het beheren van de aangewezen entiteiten zoals hieronder vermeld:

* /content/entities/internal
* /content/entities/public/nl
* /content/entities/public/fr
* /content/entities/common

Een de diensteindpunt wordt verstrekt aan de ruimte zodat kan de inheemse cliëntbibliotheek om een lijst van de inhoud van een ruimte verzoeken. Deze &#39;aanbieding&#39; wordt geretourneerd als een JSON-object.

Zie **[Spaties en Entiteiten](/help/mobile/spaces-and-entities.md)** voor het creëren van en het publiceren van ruimten.

>[!NOTE]
>
>Een spatie kan door veel apps worden gebruikt en een app kan veel spaties gebruiken.

### Mappen in inhoudsmodel {#folders-in-content-model}

De omslagen staan gebruikers toe om entiteiten te organiseren zoals vereist en vergemakkelijkt fijnere ACL controle. De ruimten kunnen omslagen omvatten om de inhoud en de activa van de ruimte verder te organiseren. Een gebruiker kan een eigen hiërarchie onder een spatie maken.

Om omslagen binnen een ruimte tot stand te brengen en te beheren, zie **[Werkend met Omslagen in een Ruimte](/help/mobile/spaces-and-entities.md)**.
