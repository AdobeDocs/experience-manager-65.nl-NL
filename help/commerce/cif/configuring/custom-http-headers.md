---
title: Aangepaste HTTP-headers
description: Aangepaste HTTP-headers configureren
source-git-commit: 7d174be35cb99d802e4aeff6f4d955b1b92cab74
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%

---


# Aangepaste HTTP-headers {#custom-http-headers}

## Overzicht {#overview}

Om meer controle over hun achterkant te verkrijgen, kunnen de auteurs de kopballen van douaneHTTP vormen die naar de handelingsmotor, samen met degenen zouden worden verzonden die reeds door CIF worden verzonden. Veelvoorkomende gebruiks-gevallen omvatten multi-store montages waarin u de kopballen van HTTP kunt gebruiken om de reactie van de handel achterste-eind te controleren.

>[!NOTE]
>
>De ontwikkelaars kunnen de kopballen van douaneHTTP altijd vormen gebruikend de de cliëntconfiguratie GraphQL.


## Configuratie {#configuration}

Om de kopballen van douaneHTTP te vormen, moet men hen eerst bepalen. De kopballen van douaneHTTP moeten eerst worden bepaald door hen aan de `com.adobe.cq.cif.http.internal.HttpHeadersConfigProviderImpl` de dienstconfiguratie toe te voegen gebruikend een OSGi config.

U kunt de waarden van de kopballen van HTTP in de pagina van de Configuratie van de Cloud Service voor uw project vormen:

1. Ga naar de configuratiepagina van de Cloud Service in Hulpmiddelen -> Cloud Services -> Configuratie CIF
1. Een bestaande configuratie openen of een nieuwe configuratie maken
1. Ga naar het tabblad &quot;Geavanceerd&quot; en zoek het multiveld &quot;Aangepaste HTTP-headers&quot;. U kunt de eerder gedefinieerde kopteksten selecteren en er waarden aan toewijzen.

De componenten die de bovengenoemde configuratie van de wolkendienst gebruiken zullen deze kopballen van HTTP met elk verzoek GraphQL verzenden.

## Beperkingen {#restrictions}

Terwijl de dienst voor om het even welke kopbalnamen om toestaat worden bepaald, met inbegrip van de standaarddegenen, zullen zij niet voor het vormen beschikbaar zijn. Met andere woorden, u kunt de standaard HTTP-headers niet overschrijven met deze functie. Een lijst met beperkte koptekstnamen vindt u [hier](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers). Daarnaast zijn er nog twee headers die niet kunnen worden gebruikt:

* &quot;Store&quot; - gebruikt door CIF om de Magento store te identificeren
* &quot;Voorvertoning-versie&quot; - wordt gebruikt door CIF om gefaseerde producten op te halen
