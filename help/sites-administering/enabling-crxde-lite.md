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

---


# CRXDE Lite inschakelen in AEM{#enabling-crxde-lite-in-aem}

Om ervoor te zorgen dat AEM-installaties zo veilig mogelijk zijn, wordt in de beveiligingschecklist aanbevolen WebDAV [uit te schakelen in productieomgevingen](/help/sites-administering/security-checklist.md#disable-webdav) .

CRXDE Lite hangt echter af van de `org.apache.sling.jcr.davex` bundel om correct te functioneren, zodat het onbruikbaar maken van WebDAV CRXDE Lite ook effectief onbruikbaar zal maken.

Wanneer dit gebeurt, `https://serveraddress:4502/crx/de/index.jsp` zal het doorbladeren aan een leeg wortelknoop tonen, en alle HTTP- verzoeken aan middelen CRXDE Lite zullen ontbreken:

```xml
404 Resource at '/crx/server/crx.default/jcr:root/.1.json' not found: No resource found
```

Hoewel deze aanbeveling bedoeld is om aanvalsoppervlakken zoveel mogelijk te beperken, hebben systeembeheerders soms toegang tot CRXDE Lite nodig om te bladeren in inhoud of problemen met de foutopsporing op productieinstanties.

Indien uitgeschakeld, kunt u CRXDE Lite inschakelen door de onderstaande procedure te volgen:

1. Ga naar de console van Componenten OSGi bij `http://localhost:4502/system/console/components`
1. Zoek naar de volgende component:

   * `org.apache.sling.jcr.davex.impl.servlets.SlingDavExServlet`

1. Klik op het moersleutelpictogram naast het pictogram om de configuratieopties te bekijken:

   ![chlimage_1-80](assets/chlimage_1-80a.png)

1. Maak de volgende configuratie:

   * **** Hoofdpad: `/crx/server`
   * Vink het vakje aan onder Absolute URI&#39;s **gebruiken**.

1. Als u klaar bent met het gebruik van CRXDE Lite, moet u WebDAV opnieuw uitschakelen.

U kunt CRXDE Lite via cURL ook toelaten, door dit bevel in werking te stellen:

```shell
curl -u admin:admin -F "jcr:primaryType=sling:OsgiConfig" -F "alias=/crx/server" -F "dav.create-absolute-uri=true" -F "dav.create-absolute-uri@TypeHint=Boolean" http://localhost:4502/apps/system/config/org.apache.sling.jcr.davex.impl.servlets.SlingDavExServlet
```

## Overige bronnen {#other-resources}

Raadpleeg de volgende pagina&#39;s voor meer informatie over de beveiligingsfuncties van AEM 6:

* [De AEM-beveiligingscontrolelijst](/help/sites-administering/security-checklist.md)
* [AEM wordt uitgevoerd in productiekaartmodus](/help/sites-administering/production-ready.md)

