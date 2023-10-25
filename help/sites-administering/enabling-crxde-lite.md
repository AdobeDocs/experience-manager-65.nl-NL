---
title: CRXDE Lite inschakelen in AEM
seo-title: Enabling CRXDE Lite in AEM
description: Leer hoe u CRXDE Lite inschakelt in Adobe Experience Manager.
seo-description: Learn how to enable CRXDE Lite in AEM.
uuid: d7a3db67-6384-463b-9aa9-f08ecc6c99c6
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
discoiquuid: 72df3ece-badf-466b-8f9a-0ec985d87741
exl-id: bf51def2-1dd4-4bd3-b989-685058f0ead8
source-git-commit: e54c1d422f2bf676e8a7b0f50a101e495c869c96
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---

# CRXDE Lite inschakelen in AEM{#enabling-crxde-lite-in-aem}

Om ervoor te zorgen dat AEM installaties zo veilig mogelijk zijn, wordt in de beveiligingscontrolelijst aanbevolen [WebDAV uitschakelen](/help/sites-administering/security-checklist.md#disable-webdav) in productieomgevingen.

CRXDE Lite is echter afhankelijk van de `org.apache.sling.jcr.davex` bundel om behoorlijk te functioneren, zodat zal onbruikbaar makend WebDAV effectief CRXDE Lite ook onbruikbaar maken.

Wanneer dit gebeurt, bladert u naar `https://serveraddress:4502/crx/de/index.jsp` zal een leeg wortelknooppunt tonen, en alle HTTP- verzoeken aan de middelen van CRXDE Lite zullen ontbreken:

```xml
404 Resource at '/crx/server/crx.default/jcr:root/.1.json' not found: No resource found
```

Hoewel deze aanbeveling bedoeld is om aanvalsoppervlakken zoveel mogelijk te beperken, hebben systeembeheerders soms toegang tot CRXDE Lite nodig om inhoud te kunnen doorbladeren of problemen met betrekking tot productieinstanties op te sporen.

U kunt CRXDE Lite inschakelen met beide [OSGi-instellingen](#enabling-crxde-lite-osgi) of met [cURL, opdracht](#enabling-crxde-lite-curl).

>[!WARNING]
>
>Wegens kleine verschillen in de werking van deze methoden moet u ***ofwel*** OSGI ***of*** cURL.
>
>De twee methoden zijn ***niet*** onderling verwisselbaar.

## CRXDE Lite inschakelen met OSGI {#enabling-crxde-lite-osgi}

Als deze optie is uitgeschakeld, kunt u CRXDE Lite inschakelen door de onderstaande procedure te volgen:

1. Ga naar de console van Componenten OSGi bij `http://localhost:4502/system/console/components`
1. Zoek naar de volgende component:

   * `org.apache.sling.jcr.davex.impl.servlets.SlingDavExServlet`

1. Klik op het moersleutelpictogram naast het pictogram om de configuratieopties te bekijken:

   ![chlimage_1-80](assets/chlimage_1-80a.png)

1. Maak de volgende configuratie:

   * **Hoofdpad:** `/crx/server`
   * Vink het vakje onder aan **Absolute URI&#39;s gebruiken**.

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
