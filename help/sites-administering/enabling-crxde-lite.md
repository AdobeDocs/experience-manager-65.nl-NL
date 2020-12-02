---
title: CRXDE Lite inschakelen in AEM
seo-title: CRXDE Lite inschakelen in AEM
description: Leer hoe u CRXDE Lite in AEM kunt inschakelen.
seo-description: Leer hoe u CRXDE Lite in AEM kunt inschakelen.
uuid: d7a3db67-6384-463b-9aa9-f08ecc6c99c6
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
discoiquuid: 72df3ece-badf-466b-8f9a-0ec985d87741
translation-type: tm+mt
source-git-commit: a833a34bbeb938c72cdb851a46b2ffd97aee9f6d
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---


# CRXDE Lite inschakelen in AEM{#enabling-crxde-lite-in-aem}

Om ervoor te zorgen dat AEM installaties zo veilig mogelijk zijn, raadt de beveiligingscontrolelijst [aan WebDAV](/help/sites-administering/security-checklist.md#disable-webdav) uit te schakelen in productieomgevingen.

Nochtans, hangt CRXDE Lite van de `org.apache.sling.jcr.davex` bundel om behoorlijk te functioneren af, zodat zal het onbruikbaar maken WebDAV effectief CRXDE Lite ook onbruikbaar maken.

Wanneer dit gebeurt, zal het doorbladeren aan `https://serveraddress:4502/crx/de/index.jsp` een leeg wortelknoop tonen, en alle HTTP- verzoeken aan de middelen van CRXDE Lite zullen ontbreken:

```xml
404 Resource at '/crx/server/crx.default/jcr:root/.1.json' not found: No resource found
```

Hoewel deze aanbeveling bedoeld is om aanvalsoppervlakken zoveel mogelijk te beperken, hebben systeembeheerders soms toegang tot CRXDE Lite nodig om inhoud te kunnen doorbladeren of problemen met betrekking tot productieinstanties op te sporen.

Als deze optie is uitgeschakeld, kunt u CRXDE Lite inschakelen door de onderstaande procedure te volgen:

1. Ga naar de console van Componenten OSGi bij `http://localhost:4502/system/console/components`
1. Zoek naar de volgende component:

   * `org.apache.sling.jcr.davex.impl.servlets.SlingDavExServlet`

1. Klik op het moersleutelpictogram naast het pictogram om de configuratieopties te bekijken:

   ![chlimage_1-80](assets/chlimage_1-80a.png)

1. Maak de volgende configuratie:

   * **Hoofdpad:** `/crx/server`
   * Tik op het vak onder **Absolute URI&#39;s gebruiken**.

1. Als u klaar bent met het gebruik van CRXDE Lite, moet u WebDAV opnieuw uitschakelen.

U kunt CRXDE Lite ook inschakelen via cURL door deze opdracht uit te voeren:

```shell
curl -u admin:admin -F "jcr:primaryType=sling:OsgiConfig" -F "alias=/crx/server" -F "dav.create-absolute-uri=true" -F "dav.create-absolute-uri@TypeHint=Boolean" http://localhost:4502/apps/system/config/org.apache.sling.jcr.davex.impl.servlets.SlingDavExServlet
```

## Overige bronnen {#other-resources}

Raadpleeg de volgende pagina&#39;s voor meer informatie over AEM 6 beveiligingsfuncties:

* [De lijst AEM beveiligingscontrole](/help/sites-administering/security-checklist.md)
* [AEM uitvoeren in productielocatie](/help/sites-administering/production-ready.md)

