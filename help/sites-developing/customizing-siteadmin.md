---
title: De websiteconsole aanpassen (klassieke gebruikersinterface)
description: De console van het Beleid van Websites kan worden uitgebreid om douanekolommen te tonen
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
docset: aem65
exl-id: 2b9b4857-821c-4f2f-9ed9-78a1c9f5ac67
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '720'
ht-degree: 0%

---

# De websiteconsole aanpassen (klassieke gebruikersinterface){#customizing-the-websites-console-classic-ui}

## Een aangepaste kolom toevoegen aan de console Websites (sitebeheerder) {#adding-a-custom-column-to-the-websites-siteadmin-console}

De console van het Beleid van Websites kan worden uitgebreid om douanekolommen te tonen. De console is gebaseerd op een JSON-object dat kan worden uitgebreid door een OSGI-service te maken die de `ListInfoProvider` -interface implementeert. Zulk de dienst wijzigt het voorwerp JSON dat naar de cliënt wordt verzonden om de console te bouwen.

Deze geleidelijke zelfstudie verklaart hoe te om een nieuwe kolom in de console van het Beleid van Websites te tonen door de `ListInfoProvider` interface uit te voeren. Het bestaat uit de volgende stappen:

1. [&#x200B; Creërend de dienst OSGI &#x200B;](#creating-the-osgi-service) en opstellend de bundel die het aan de AEM server bevat.
1. (facultatief) [&#x200B; Testen de nieuwe dienst &#x200B;](#testing-the-new-service) door een vraag uit te geven JSON om het voorwerp te verzoeken JSON dat wordt gebruikt om de console te bouwen.
1. [&#x200B; Weergevend de nieuwe kolom &#x200B;](#displaying-the-new-column) door de knoopstructuur van de console in de bewaarplaats uit te breiden.

>[!NOTE]
>
>Deze zelfstudie kan ook worden gebruikt om de volgende toedieningsconsoles uit te breiden:
>
>* de Digital Assets-console
>* de Community console
>

### De OSGI-service maken {#creating-the-osgi-service}

De interface `ListInfoProvider` definieert twee methoden:

* `updateListGlobalInfo` als u algemene eigenschappen van de lijst wilt bijwerken,
* `updateListItemInfo` als u één lijstitem wilt bijwerken.

De argumenten voor beide methoden zijn:

* `request` , het bijbehorende Sling HTTP request object,
* `info` , het JSON-object dat moet worden bijgewerkt. Dit is respectievelijk de algemene lijst of het huidige lijstitem.
* `resource` , a Sling resource.

De voorbeeldimplementatie is hieronder:

* Voegt a *begonnen* bezit voor elk punt toe, dat `true` is als de paginanaam met a *e* begint, en `false` anders.

* Voegt a *starredCount* bezit toe, dat voor de lijst globaal is en het aantal begonnen lijstitems bevat.

Om de dienst te creëren OSGI:

1. In CRXDE Lite, [&#x200B; creeer een bundel &#x200B;](/help/sites-developing/developing-with-crxde-lite.md#managing-a-bundle).
1. Voeg de voorbeeldcode hieronder toe.
1. Bouw de bundel.

De nieuwe dienst is in gebruik.

```java
package com.test;

import com.day.cq.commons.ListInfoProvider;
import com.day.cq.i18n.I18n;
import com.day.cq.wcm.api.Page;
import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Service;
import org.apache.sling.api.SlingHttpServletRequest;
import org.apache.sling.api.resource.Resource;
import org.apache.sling.commons.json.JSONException;
import org.apache.sling.commons.json.JSONObject;

@Component(metatype = false)
@Service(value = ListInfoProvider.class)
public class StarredListInfoProvider implements ListInfoProvider {

    private int count = 0;

    public void updateListGlobalInfo(SlingHttpServletRequest request, JSONObject info, Resource resource) throws JSONException {
        info.put("starredCount", count);
        count = 0; // reset for next execution
    }

    public void updateListItemInfo(SlingHttpServletRequest request, JSONObject info, Resource resource) throws JSONException {
        Page page = resource.adaptTo(Page.class);
        if (page != null) {
            // Consider starred if page name starts with 'e'
            boolean starred = page.getName().startsWith("e");
            if (starred) {
                count++;
            }
            I18n i18n = new I18n(request);
            info.put("starred", starred ? i18n.get("Yes") : i18n.get("No"));
        }
    }

}
```

>[!CAUTION]
>
>* Uw implementatie moet op basis van het ingediende verzoek en/of de bron beslissen of de informatie al dan niet aan het JSON-object moet worden toegevoegd.
>* Als uw `ListInfoProvider` -implementatie een eigenschap definieert die bestaat in het reactieobject, wordt de waarde ervan overschreven door de eigenschap die u opgeeft.
>
>  U kunt [&#x200B; dienst gebruiken rangschikkend &#x200B;](https://docs.osgi.org/javadoc/r2/org/osgi/framework/Constants.html#SERVICE_RANKING) om de uitvoeringsorde van veelvoudige `ListInfoProvider` implementaties te beheren.

### De nieuwe service testen {#testing-the-new-service}

Wanneer u de console van het Beleid van Websites opent en door uw plaats doorbladert, geeft browser een vraag van Ajax uit om het voorwerp te krijgen JSON dat wordt gebruikt om de console te bouwen. Wanneer u bijvoorbeeld naar de map `/content/geometrixx` bladert, wordt het volgende verzoek naar de AEM server verzonden om de console te maken:

[&#x200B; https://localhost:4502/content/geometrixx.pages.json?start=0&amp;limit=30&amp;predicate=siteadmin](https://localhost:4502/content/geometrixx.pages.json?start=0&amp;limit=30&amp;predicate=siteadmin)

Om ervoor te zorgen dat de nieuwe dienst na het hebben opgesteld de bundel die het bevat loopt:

1. Verwijs uw browser naar de volgende URL:
   [&#x200B; https://localhost:4502/content/geometrixx.pages.json?start=0&amp;limit=30&amp;predicate=siteadmin](https://localhost:4502/content/geometrixx.pages.json?start=0&amp;limit=30&amp;predicate=siteadmin)

1. In de reactie moeten de nieuwe eigenschappen als volgt worden weergegeven:

![&#x200B; screen_shot_2012-02-13at163046 &#x200B;](assets/screen_shot_2012-02-13at163046.png)

### De nieuwe kolom weergeven {#displaying-the-new-column}

De laatste stap bestaat uit het aanpassen van de knooppuntstructuur van de console van het Beleid Websites om het nieuwe bezit voor alle pagina&#39;s van de Geometrixx te tonen door `/libs/wcm/core/content/siteadmin` te bedekken. Ga als volgt te werk:

1. Maak in CRXDE Lite de knooppuntstructuur `/apps/wcm/core/content` met knooppunten van het type `sling:Folder` om de structuur `/libs/wcm/core/content` te weerspiegelen.

1. Kopieer het knooppunt `/libs/wcm/core/content/siteadmin` en plak het onder `/apps/wcm/core/content` .

1. Kopieer het knooppunt `/apps/wcm/core/content/siteadmin/grid/assets` naar `/apps/wcm/core/content/siteadmin/grid/geometrixx` en wijzig de eigenschappen ervan:

   * Verwijder **pageText**

   * Plaats **pathRegex** aan `/content/geometrixx(/.*)?`
Hierdoor wordt de rasterconfiguratie actief voor alle websites van Geometrixx.

   * Plaats **storeProxySuffix** aan `.pages.json`

   * Bewerk het **storeReaderFields** multivaluated bezit en voeg de `starred` waarde toe.

   * Om functionaliteit te activeren MSM, voeg de volgende parameters MSM aan het bezit multi-Koord **storeReaderFields** toe:

      * **msm:isSource**
      * **msm:isInBlueprint**
      * **msm:isLiveCopy**

1. Voeg a `starred` knoop (van type **toe:niet-gestructureerd**) hieronder `/apps/wcm/core/content/siteadmin/grid/geometrixx/columns` met de volgende eigenschappen:

   * **dataIndex**: `starred` van typeKoord

   * **kopbal**: `Starred` van typeKoord

   * **xtype**: `gridcolumn` van typeKoord

1. (optioneel) Verplaats de kolommen die u niet wilt weergeven bij `/apps/wcm/core/content/siteadmin/grid/geometrixx/columns`

1. `/siteadmin` is een ijdelingspad dat standaard naar `/libs/wcm/core/content/siteadmin` wijst.
Als u dit wilt doorsturen naar uw versie van sitebeheerder op `/apps/wcm/core/content/siteadmin` , definieert u de eigenschap `sling:vanityOrder` voor een hogere waarde dan die welke is gedefinieerd op `/libs/wcm/core/content/siteadmin` . De standaardwaarde is 300, dus om het even wat hoger is is geschikt.

1. Ga naar de console van het Beleid van Websites en navigeer aan de plaats van de Geometrixx:
   [&#x200B; https://localhost:4502/siteadmin#/content/geometrixx &#x200B;](https://localhost:4502/siteadmin#/content/geometrixx).

1. De nieuwe kolom riep **Begonnen** is beschikbaar, tonend douaneinformatie als volgt:

![&#x200B; screen_shot_2012-02-14at104602 &#x200B;](assets/screen_shot_2012-02-14at104602.png)

>[!CAUTION]
>
>Als de veelvoudige die netconfiguraties de gevraagde weg aanpassen door het **wordt bepaald pathRegex** bezit, eerste wordt gebruikt, en niet meest specifieke, zo betekent het dat de orde van de configuraties belangrijk is.

### Voorbeeldpakket {#sample-package}

Het resultaat van dit leerprogramma is beschikbaar in [&#x200B; het Aanpassen van het pakket van de Console van het Beleid van Websites &#x200B;](https://localhost:4502/crx/packageshare/index.html/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/helper/customizing-siteadmin) op het Aandeel van het Pakket.
