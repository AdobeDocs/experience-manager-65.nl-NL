---
title: Aangepaste HTTP-headers
description: Aangepaste HTTP-headers configureren
exl-id: 834aadac-c3be-4e7a-a3cb-349608810b40
source-git-commit: a467009851937c4a10b165a3d253c47bf990bbc5
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# Aangepaste HTTP-headers {#custom-http-headers}

## Overzicht {#overview}

Om meer controle over hun achterkant te verkrijgen, kunnen de auteurs de kopballen van douaneHTTP vormen die naar de handelingsmotor, samen met degenen zouden worden verzonden die reeds door CIF worden verzonden. Veelvoorkomende gebruiks-gevallen omvatten multi-store montages waarin u de kopballen van HTTP kunt gebruiken om de reactie van de handel achterste-eind te controleren.

>[!NOTE]
>
>Ontwikkelaars kunnen aangepaste HTTP-headers altijd configureren met de GraphQL-clientconfiguratie.

## Configuratie {#configuration}

Om de kopballen van douaneHTTP te vormen, moet men hen eerst bepalen. De aangepaste HTTP-headers moeten eerst worden gedefinieerd door ze toe te voegen aan de `com.adobe.cq.cif.http.internal.HttpHeadersConfigProviderImpl` de dienstconfiguratie die een OSGi config gebruikt.

U kunt de waarden van de kopballen van HTTP in de pagina van de Configuratie van de Cloud Service voor uw project vormen:

1. Ga naar de configuratiepagina van de Cloud Service in Hulpmiddelen -> Cloud Services -> Configuratie CIF
1. Een bestaande configuratie openen of een nieuwe configuratie maken
1. Ga naar het tabblad &quot;Geavanceerd&quot; en zoek het multiveld &quot;Aangepaste HTTP-headers&quot;. U kunt de eerder gedefinieerde kopteksten selecteren en er waarden aan toewijzen.

De componenten die de bovenstaande cloudserviceconfiguratie gebruiken, verzenden deze HTTP-headers met elke GraphQL-aanvraag.

## Beperkingen {#restrictions}

Terwijl de dienst voor om het even welke kopbalnamen om toestaat worden bepaald, met inbegrip van de standaarddegenen, zullen zij niet voor het vormen beschikbaar zijn. Met andere woorden, u kunt de standaard HTTP-headers niet overschrijven met deze functie. Een lijst met beperkte koptekstnamen vindt u [hier](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers). Daarnaast zijn er nog twee headers die niet kunnen worden gebruikt:

* &quot;Winkel&quot; - wordt door CIF gebruikt om de Adobe Commerce-winkel te identificeren
* &quot;Voorvertoning-versie&quot; - wordt gebruikt door CIF om gefaseerde producten op te halen
