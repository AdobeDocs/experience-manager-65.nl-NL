---
title: CRXDE Lite inschakelen in AEM
description: Leer hoe u CRXDE Lite inschakelt in Adobe Experience Manager.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
exl-id: bf51def2-1dd4-4bd3-b989-685058f0ead8
solution: Experience Manager, Experience Manager Sites
feature: Administering
role: Admin
source-git-commit: 48d12388d4707e61117116ca7eb533cea8c7ef34
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 0%

---

# CRXDE Lite inschakelen in AEM{#enabling-crxde-lite-in-aem}

Om ervoor te zorgen dat AEM installaties zo veilig mogelijk zijn, adviseert de veiligheid controlelijst [ onbruikbaar makend WebDAV ](/help/sites-administering/security-checklist.md#disable-webdav) in productiemilieu&#39;s.

CRXDE Lite is echter afhankelijk van de juiste werking van de `org.apache.sling.jcr.davex` -bundel. Als u WebDAV uitschakelt, wordt CRXDE Lite ook uitgeschakeld.

Wanneer dit gebeurt, wordt bij het bladeren naar `https://serveraddress:4502/crx/de/index.jsp` een leeg hoofdknooppunt weergegeven en mislukken alle HTTP-aanvragen naar CRXDE Lite-bronnen:

```xml
404 Resource at '/crx/server/crx.default/jcr:root/.1.json' not found: No resource found
```

Hoewel deze aanbeveling bedoeld is om aanvalsoppervlakken zoveel mogelijk te beperken, hebben systeembeheerders soms toegang tot CRXDE Lite nodig om door inhoud te bladeren of problemen met betrekking tot productieinstanties op te sporen.

U kunt CRXDE Lite met of [ montages OSGi ](#enabling-crxde-lite-osgi) of met het bevel van a [ cURL ](#enabling-crxde-lite-curl) toelaten.

>[!WARNING]
>
>Wegens lichte verschillen in hoe deze methodes werken zou u ***of*** OSGI ***of*** cURL moeten gebruiken.
>
>De twee methodes zijn ***niet*** onderling verwisselbaar.

## CRXDE Lite inschakelen met OSGI {#enabling-crxde-lite-osgi}

Als deze optie is uitgeschakeld, kunt u CRXDE Lite inschakelen door de onderstaande procedure te volgen:

1. Ga naar de console OSGi Components op `http://localhost:4502/system/console/components`
1. Zoek naar de volgende component:

   * `org.apache.sling.jcr.davex.impl.servlets.SlingDavExServlet`

1. Klik op het moersleutelpictogram naast het pictogram om de configuratieopties weer te geven:

   ![ chlimage_1-80 ](assets/chlimage_1-80a.png)

1. Maak de volgende configuratie:

   * **Wortingspad:** `/crx/server`
   * Tik de doos onder **absolute URIs van het Gebruik**.

1. Als u klaar bent met het gebruik van CRXDE Lite, schakelt u WebDAV opnieuw uit.

## CRXDE Lite inschakelen met cURL {#enabling-crxde-lite-curl}

U kunt CRXDE Lite ook inschakelen via cURL door deze opdracht uit te voeren:

```shell
curl -u admin:admin -F "jcr:primaryType=sling:OsgiConfig" -F "alias=/crx/server" -F "dav.create-absolute-uri=true" -F "dav.create-absolute-uri@TypeHint=Boolean" http://localhost:4502/apps/system/config/org.apache.sling.jcr.davex.impl.servlets.SlingDavExServlet
```

## Overige bronnen {#other-resources}

Raadpleeg de volgende pagina&#39;s voor meer informatie over AEM 6 beveiligingsfuncties:

* [De lijst AEM beveiligingscontrole](/help/sites-administering/security-checklist.md)
* [AEM uitvoeren in productielocatie](/help/sites-administering/production-ready.md)
