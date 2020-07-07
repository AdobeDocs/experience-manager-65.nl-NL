---
title: De websiteconsole aanpassen (klassieke gebruikersinterface)
seo-title: De websiteconsole aanpassen (klassieke gebruikersinterface)
description: De console van het Beleid van Websites kan worden uitgebreid om douanekolommen te tonen
seo-description: De console van het Beleid van Websites kan worden uitgebreid om douanekolommen te tonen
uuid: 9163fdff-5351-477d-b91c-8a74f8b41d34
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: aeb37103-541d-4235-8a78-980b78c8de66
docset: aem65
translation-type: tm+mt
source-git-commit: ebf3f34af7da6b1a659ac8d8843152b97f30b652
workflow-type: tm+mt
source-wordcount: '798'
ht-degree: 0%

---


# De websiteconsole aanpassen (klassieke gebruikersinterface){#customizing-the-websites-console-classic-ui}

## Een aangepaste kolom toevoegen aan de console Websites (sitebeheerder) {#adding-a-custom-column-to-the-websites-siteadmin-console}

De console van het Beleid van Websites kan worden uitgebreid om douanekolommen te tonen. De console wordt gebouwd gebaseerd op een voorwerp JSON dat kan worden uitgebreid door de dienst te creëren OSGI die de `ListInfoProvider` interface uitvoert. Zulk de dienst wijzigt het voorwerp JSON dat naar de cliënt wordt verzonden om de console te bouwen.

Dit geleidelijke leerprogramma verklaart hoe te om een nieuwe kolom in de console van het Beleid van Websites te tonen door de `ListInfoProvider` interface uit te voeren. Het bestaat uit de volgende stappen:

1. [Creërend de dienst](#creating-the-osgi-service) OSGI en plaatsend de bundel die het aan de server AEM bevat.
1. (facultatief) [Testen van de nieuwe dienst](#testing-the-new-service) door een vraag uit te geven JSON om het voorwerp te verzoeken JSON dat wordt gebruikt om de console te bouwen.
1. [De nieuwe kolom](#displaying-the-new-column) weergeven door de knooppuntstructuur van de console in de opslagplaats uit te breiden.

>[!NOTE]
>
>Deze zelfstudie kan ook worden gebruikt om de volgende toedieningsconsoles uit te breiden:
>
>* de Digital Assets-console
>* de Community console
>



### De OSGI-service maken {#creating-the-osgi-service}

De `ListInfoProvider` interface definieert twee methoden:

* `updateListGlobalInfo`om de algemene eigenschappen van de lijst bij te werken,
* `updateListItemInfo`, om één lijstitem bij te werken.

De argumenten voor beide methoden zijn:

* `request`, het bijbehorende Sling HTTP request object,
* `info`, het JSON-object dat moet worden bijgewerkt. Dit is respectievelijk de algemene lijst of het huidige lijstitem.
* `resource`, een Sling resource.

De volgende voorbeeldimplementatie:

* Voegt een *starred* bezit voor elk punt toe, dat is `true` als de paginanaam met *e* begint, en `false` anders.

* Voegt een *starredCount* bezit toe, dat voor de lijst globaal is en het aantal begonnen lijstitems bevat.

Om de dienst te creëren OSGI:

1. In CRXDE Lite, [creeer een bundel](/help/sites-developing/developing-with-crxde-lite.md#managing-a-bundle).
1. Voeg de voorbeeldcode hieronder toe.
1. Maak de bundel.

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
>* Als uw `ListInfoProvider` implementatie een eigenschap definieert die al in het reactieobject bestaat, wordt de waarde ervan overschreven door de eigenschap die u opgeeft.
>
>  
U kunt [de dienstrangschikking](https://www.osgi.org/javadoc/r2/org/osgi/framework/Constants.html#SERVICE_RANKING) gebruiken om de uitvoeringsorde van veelvoudige `ListInfoProvider` implementaties te beheren.

### De nieuwe service testen {#testing-the-new-service}

Wanneer u de console van het Beleid van Websites opent en door uw plaats doorbladert, geeft browser een ajax vraag uit om het voorwerp te krijgen JSON dat wordt gebruikt om de console te bouwen. Wanneer u bijvoorbeeld naar de `/content/geometrixx` map bladert, wordt het volgende verzoek naar de AEM-server verzonden om de console te maken:

[https://localhost:4502/content/geometrixx.pages.json?start=0&amp;limit=30&amp;predicate=siteadmin](https://localhost:4502/content/geometrixx.pages.json?start=0&amp;limit=30&amp;predicate=siteadmin)

Om ervoor te zorgen dat de nieuwe dienst na het hebben opgesteld de bundel die het bevat loopt:

1. Verwijs uw browser naar de volgende URL:
   [https://localhost:4502/content/geometrixx.pages.json?start=0&amp;limit=30&amp;predicate=siteadmin](https://localhost:4502/content/geometrixx.pages.json?start=0&amp;limit=30&amp;predicate=siteadmin)

1. In de reactie moeten de nieuwe eigenschappen als volgt worden weergegeven:

![screen_shot_2012-02-13at163046](assets/screen_shot_2012-02-13at163046.png)

### De nieuwe kolom weergeven {#displaying-the-new-column}

De laatste stap bestaat uit het aanpassen van de knooppuntenstructuur van de console van het Beleid Websites om het nieuwe bezit voor alle pagina&#39;s van Geometrixx te tonen door te bedekken `/libs/wcm/core/content/siteadmin`. Ga als volgt te werk:

1. In CRXDE Lite, creeer de knoopstructuur `/apps/wcm/core/content` met knopen van type `sling:Folder` om op de structuur te wijzen `/libs/wcm/core/content`.

1. Kopieer het knooppunt `/libs/wcm/core/content/siteadmin` en plak het hieronder `/apps/wcm/core/content`.

1. Kopieer het knooppunt `/apps/wcm/core/content/siteadmin/grid/assets` naar de eigenschappen `/apps/wcm/core/content/siteadmin/grid/geometrixx` en wijzig deze:

   * Pagina- **tekst verwijderen**

   * Stel **pathRegex** in op `/content/geometrixx(/.*)?`This will make the grid configuration active for all geometrixx websites.

   * Achtervoegsel **storeProxy** instellen op `.pages.json`

   * Bewerk de **multigetaxeerde eigenschap storeReaderFields** en voeg de `starred` waarde toe.

   * Als u de MSM-functionaliteit wilt activeren, voegt u de volgende MSM-parameters toe aan de eigenschap **storeReaderFields** met meerdere tekenreeksen:

      * **msm:isSource**
      * **msm:isInBlueprint**
      * **msm:isLiveCopy**

1. Voeg hieronder een `starred` knooppunt (van het type **nt:ongestructureerd**) toe `/apps/wcm/core/content/siteadmin/grid/geometrixx/columns` met de volgende eigenschappen:

   * **dataIndex**: `starred` van het type String

   * **header**: `Starred` van het type String

   * **xtype**: `gridcolumn` van het type String

1. (optioneel) Verplaats de kolommen waarop u niet wilt weergeven `/apps/wcm/core/content/siteadmin/grid/geometrixx/columns`

1. `/siteadmin` is een ijdelingspad waarnaar standaard wordt verwezen `/libs/wcm/core/content/siteadmin`.
Om dit aan uw versie van plaatsadmin op te leiden `/apps/wcm/core/content/siteadmin` bepaal het bezit `sling:vanityOrder` om een waarde te hebben hoger dan die bepaald op `/libs/wcm/core/content/siteadmin`. De standaardwaarde is 300, dus om het even wat hoger is is geschikt.

1. Ga naar de console van het Beleid van Websites en navigeer aan de plaats van Geometrixx:
   [https://localhost:4502/siteadmin#/content/geometrixx](https://localhost:4502/siteadmin#/content/geometrixx).

1. De nieuwe kolom genoemd **Gestart** is beschikbaar, tonend douaneinformatie als volgt:

![screen_shot_2012-02-14at104602](assets/screen_shot_2012-02-14at104602.png)

>[!CAUTION]
>
>Als meerdere rasterconfiguraties overeenkomen met het gevraagde pad dat is gedefinieerd door de eigenschap **pathRegex** , wordt het eerste pad gebruikt en niet het meest specifieke, wat betekent dat de volgorde van de configuraties belangrijk is.

### Voorbeeldpakket {#sample-package}

Het resultaat van deze zelfstudie is beschikbaar in het pakket [De beheerconsole](https://localhost:4502/crx/packageshare/index.html/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/helper/customizing-siteadmin) van websites aanpassen bij het delen van pakketten.
