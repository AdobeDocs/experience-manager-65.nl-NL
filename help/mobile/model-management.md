---
title: Modellen - overzicht
seo-title: Models Overview
description: Modellen - overzicht
seo-description: null
uuid: e09dac52-9515-43f7-9d3b-6637e2283d59
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
discoiquuid: c8281f98-9811-42f7-9a31-f82dd0f09319
exl-id: 50785534-5784-4354-b123-5e640b7c0242
source-git-commit: 259f257964829b65bb71b5a46583997581a91a4e
workflow-type: tm+mt
source-wordcount: '784'
ht-degree: 0%

---

# Modellen - overzicht{#models-overview}

>[!NOTE]
>
>Adobe raadt aan de SPA Editor te gebruiken voor projecten die renderen op basis van één pagina voor toepassingsframework nodig hebben (bijvoorbeeld Reageren). [Meer informatie](/help/sites-developing/spa-overview.md).

Modelbeheer omvat het maken en beheren van modellen om deze aan eventuele gegevensobjecten te koppelen. Elk model bevat alle eigenschappen en velddefinities die nodig zijn om het maken en renderen van objecten te vergemakkelijken.

Modelbeheer houdt in dat **modellen**, **entiteiten**, en **spaties**. Het volgende diagram illustreert de relatie tussen de AEM Inhoud en de modellen.

![chlimage_1-81](assets/chlimage_1-81.png)

## Het inhoudsmodel {#the-content-model}

Een model beschrijft het type inhoud en geeft aan welke informatie beschikbaar is voor de native toepassing. Het is een beschrijving van wat uit een stuk van inhoud bestaat. Een inhoudsmodel is de regels voor het bouwen van inhoud. Het inhoudsmodel bevat welke gegevens beschikbaar zijn, welke elementen kunnen worden gebruikt, de relatie tussen elementen en gegevens, de relatie met andere inhoudsmodellen en de beschikbare metagegevens.

Modellen dienen ook als een manier om bestaande AEM-inhoud te transformeren in objecten die gemakkelijk kunnen worden gebruikt door systeemeigen mobiele apps.

Content Services biedt een aantal out-of-the-box-modellen voor veelvoorkomende objecten, zoals elementen, verzamelingen van middelen, pagina&#39;s met HTML, toepassingsconfiguraties en pagina&#39;s die onafhankelijk zijn van kanalen. Deze zullen configureerbaar zijn zodat zullen zij aan specifieke klantenbehoeften zonder een AEM ontwikkelingsinspanning vereisen.

De gebruiker kan zijn of haar eigen modellen tot stand brengen. Hierdoor kunnen nieuwe inhoudstypen worden gemaakt die nog niet door AEM worden beheerd. Het maken van modellen gebeurt via een gebruikersinterface met behulp van bestaande primitieve typen.

In het volgende diagram ziet u het inhoudsmodel voor AEM Mobile Apps en hoe entiteiten, mappen en spaties worden toegewezen aan een app.

![chlimage_1-82](assets/chlimage_1-82.png)

### De modellen {#the-models}

Modellen worden gebruikt om te bepalen hoe entiteiten worden gemaakt. Zij bepalen wat in een entiteit beschikbaar is en hoe dat gegeven van AEM inhoud wordt geproduceerd. Voordat u begint te werken met ruimten, mappen en entiteiten, moet u vertrouwd zijn met het maken en beheren van modellen.

>[!NOTE]
>
>Een model bestaat buiten een app omdat meerdere apps het kunnen gebruiken.
>

Zie **[Modellen](/help/mobile/administer-mobile-apps.md)** om modellen in het dashboard en de gegevensopslagplaats tot stand te brengen en te beheren.

### Entiteiten in inhoudsmodel {#entities-in-content-model}

Een entiteit is een instantie van een inhoudsmodel. Een entiteit wordt via de Content Services API blootgesteld aan de bibliotheek aan de clientzijde en biedt een manier voor een native app om inhoud op een kanaalonafhankelijke manier te benaderen.

In het geval van bestaande AEM wordt een entiteit gegenereerd met behulp van een model en de AEM inhoudsbron. Een pagina-entiteit is bijvoorbeeld een kanaal- en indelingsonafhankelijk object dat wordt gegenereerd op basis van een AEM pagina en het paginamodel.

Wijzigingen in de inhoud van een entiteit waarnaar wordt verwezen, resulteren in een wijziging van de entiteit. Als een *cq:pagina* wordt bijgewerkt, worden de entiteiten die op die pagina zijn gebaseerd, ook bijgewerkt.

Zie **[Werken met entiteiten](/help/mobile/spaces-and-entities.md)** om aangepaste entiteiten te maken van modellen.

>[!NOTE]
>
>Als het model niet aan bestaande AEM inhoud beantwoordt, zoals de klant creeerde een nieuw model, dan zal er een UI zijn zodat kan een klant een nieuwe entiteit tot stand brengen.
>

### Spaties in inhoudsmodel {#spaces-in-content-model}

Een spatie wordt gebruikt om entiteiten te organiseren voor eenvoudige toegang. Een spatie kan een of meer eenheidstypes bevatten en kan submappen bevatten.

Aan de AEM kant is een spatie een handige manier om verwante entiteiten te beheren. Het kan ook worden gebruikt om toestemmingen toe te wijzen. Er kan toestemming worden gegeven aan een ruimte, die dan de entiteiten in die ruimte beschermt.

*Bijvoorbeeld*,

Een gebruiker heeft drie algemene classificaties van entiteiten. Het ene is alleen voor intern gebruik, het andere is goedgekeurd voor openbaar gebruik en het derde is nog steeds voor algemene entiteiten die door veel apps worden gebruikt. Om het gemakkelijk te maken te leiden, creeert de gebruiker drie ruimten, namelijk *internal*, *publiek* ( zowel in het engels als in het frans ) , en *gemeenschappelijk* voor het beheer van de betrokken entiteiten als hieronder vermeld:

* /content/entities/internal
* /content/entities/public/nl
* /content/entities/public/fr
* /content/entities/common

Een de diensteindpunt zal aan de ruimte worden verstrekt zodat kan de inheemse cliëntbibliotheek om een lijst van de inhoud van een ruimte verzoeken. Deze &#39;aanbieding&#39; wordt geretourneerd als een JSON-object.

Zie **[Spaties en entiteiten](/help/mobile/spaces-and-entities.md)** voor het maken en publiceren van spaties.

>[!NOTE]
>
>Een spatie kan door veel apps worden gebruikt en een app kan veel spaties gebruiken.

### Mappen in inhoudsmodel {#folders-in-content-model}

De omslagen staan gebruikers toe om entiteiten te organiseren zoals vereist en vergemakkelijkt fijnere ACL controle. Spaties kunnen mappen bevatten voor een betere organisatie van de inhoud en elementen van de ruimte. Een gebruiker kan een eigen hiërarchie onder een spatie maken.

Zie **[Werken met mappen in een spatie](/help/mobile/spaces-and-entities.md)** om mappen binnen een ruimte te maken en te beheren.
