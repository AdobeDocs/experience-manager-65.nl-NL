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

De console van het Beleid van Websites kan worden uitgebreid om douanekolommen te tonen. De console is gebaseerd op een JSON-object dat kan worden uitgebreid door een SDAB-service te maken die het `ListInfoProvider` interface. Zulk de dienst wijzigt het voorwerp JSON dat naar de cliënt wordt verzonden om de console te bouwen.

Dit geleidelijke leerprogramma verklaart hoe te om een nieuwe kolom in de console van het Beleid van Websites te tonen door uit te voeren `ListInfoProvider` interface. Het bestaat uit de volgende stappen:

1. [De dienst OSGI aanmaken](#creating-the-osgi-service) en de bundel die het bevat op de AEM server te implementeren.
1. (optioneel) [De nieuwe service testen](#testing-the-new-service) door een JSON-aanroep uit te voeren om het JSON-object aan te vragen dat wordt gebruikt om de console te maken.
1. [De nieuwe kolom weergeven](#displaying-the-new-column) door de nodestructuur van de console in de bewaarplaats uit te breiden.

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

De voorbeeldimplementatie is hieronder:

* Hiermee voegt u een *uitgehongerd* eigenschap voor elk item, dat `true` als de paginanaam begint met een *e*, en `false` anders.

* Hiermee voegt u een *starredCount* eigenschap, die globaal is voor de lijst en het aantal starre lijstitems bevat.

Om de dienst te creëren OSGI:

1. In CRXDE Lite, [een bundel maken](/help/sites-developing/developing-with-crxde-lite.md#managing-a-bundle).
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
>* Als uw `ListInfoProvider` de implementatie definieert een eigenschap die bestaat in het reactieobject, de waarde ervan wordt overschreven door de eigenschap die u opgeeft.
>
>  U kunt [servicerangschikking](https://docs.osgi.org/javadoc/r2/org/osgi/framework/Constants.html#SERVICE_RANKING) om de uitvoeringsvolgorde van meerdere `ListInfoProvider` implementaties.

### De nieuwe service testen {#testing-the-new-service}

Wanneer u de console van het Beleid van Websites opent en door uw plaats doorbladert, geeft browser een vraag van Ajax uit om het voorwerp te krijgen JSON dat wordt gebruikt om de console te bouwen. Wanneer u bijvoorbeeld naar de `/content/geometrixx` De volgende aanvraag wordt naar de AEM server verzonden om de console te maken:

[https://localhost:4502/content/geometrixx.pages.json?start=0&amp;limit=30&amp;predicate=siteadmin](https://localhost:4502/content/geometrixx.pages.json?start=0&amp;limit=30&amp;predicate=siteadmin)

Om ervoor te zorgen dat de nieuwe dienst na het hebben opgesteld de bundel die het bevat loopt:

1. Verwijs uw browser naar de volgende URL:
   [https://localhost:4502/content/geometrixx.pages.json?start=0&amp;limit=30&amp;predicate=siteadmin](https://localhost:4502/content/geometrixx.pages.json?start=0&amp;limit=30&amp;predicate=siteadmin)

1. In de reactie moeten de nieuwe eigenschappen als volgt worden weergegeven:

![screen_shot_2012-02-13at163046](assets/screen_shot_2012-02-13at163046.png)

### De nieuwe kolom weergeven {#displaying-the-new-column}

De laatste stap bestaat uit het aanpassen van de knooppuntstructuur van de console van het Beleid van Websites om het nieuwe bezit voor alle pagina&#39;s van de Geometrixx te tonen door te bedekken `/libs/wcm/core/content/siteadmin`. Ga als volgt te werk:

1. Maak in CRXDE Lite de knooppuntstructuur `/apps/wcm/core/content` met knooppunten van type `sling:Folder` om de structuur weer te geven `/libs/wcm/core/content`.

1. Het knooppunt kopiëren `/libs/wcm/core/content/siteadmin` en plak deze hieronder `/apps/wcm/core/content`.

1. Het knooppunt kopiëren `/apps/wcm/core/content/siteadmin/grid/assets` tot `/apps/wcm/core/content/siteadmin/grid/geometrixx` en wijzigt de eigenschappen ervan:

   * Verwijderen **pageText**

   * Set **pathRegex** tot `/content/geometrixx(/.*)?`
Hierdoor wordt de rasterconfiguratie actief voor alle websites van Geometrixx.

   * Set **storeProxySuffix** tot `.pages.json`

   * Bewerk de **storeReaderFields** multigevalueerde eigenschap en voeg de `starred` waarde.

   * Als u de MSM-functionaliteit wilt activeren, voegt u de volgende MSM-parameters toe aan de eigenschap multi-String **storeReaderFields**:

      * **msm:isSource**
      * **msm:isInBluprint**
      * **msm:isLiveCopy**

1. Voeg een `starred` node (type) **nt:ongestructureerd**) hieronder `/apps/wcm/core/content/siteadmin/grid/geometrixx/columns` met de volgende eigenschappen:

   * **dataIndex**: `starred` van het type String

   * **header**: `Starred` van het type String

   * **xtype**: `gridcolumn` van het type String

1. (optioneel) Verplaats de kolommen die u niet wilt weergeven `/apps/wcm/core/content/siteadmin/grid/geometrixx/columns`

1. `/siteadmin` is een pad met ijdelheid dat standaard wijst naar `/libs/wcm/core/content/siteadmin`.
Dit doorsturen naar uw versie van sitebeheerder op `/apps/wcm/core/content/siteadmin`, definieert u de eigenschap `sling:vanityOrder` een waarde hebben die hoger is dan de waarde die op `/libs/wcm/core/content/siteadmin`. De standaardwaarde is 300, dus om het even wat hoger is is geschikt.

1. Ga naar de console van het Beleid van Websites en navigeer aan de plaats van de Geometrixx:
   [https://localhost:4502/siteadmin#/content/geometrixx](https://localhost:4502/siteadmin#/content/geometrixx).

1. De nieuwe kolom **Gestart** is beschikbaar, waarbij aangepaste informatie als volgt wordt weergegeven:

![screen_shot_2012-02-14at104602](assets/screen_shot_2012-02-14at104602.png)

>[!CAUTION]
>
>Als meerdere rasterconfiguraties overeenkomen met het gevraagde pad dat is gedefinieerd door de **pathRegex** eigenschap, wordt de eerste gebruikt, en niet de meest specifieke, wat betekent dat de volgorde van de configuraties belangrijk is.

### Voorbeeldpakket {#sample-package}

Het resultaat van deze zelfstudie is beschikbaar in het gedeelte [De beheerconsole voor websites aanpassen](https://localhost:4502/crx/packageshare/index.html/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/helper/customizing-siteadmin) pakket op Pakket delen.
