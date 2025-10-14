---
title: Geavanceerde URL-configuraties
description: Leer hoe u de URL's voor product- en categoriepagina's aanpast. Hiermee kunnen implementaties URL's optimaliseren voor zoekprogramma's en detectie bevorderen.
sub-product: Commerce
doc-type: technical-video
activity: setup
audience: administrator
feature: Commerce Integration Framework
kt: 4933
thumbnail: 34350.jpg
exl-id: 0125021a-1c00-4ea3-b7fb-1533b7b9f4f2
solution: Experience Manager,Commerce
role: Admin, Developer
source-git-commit: 10268f617b8a1bb22f1f131cfd88236e7d5beb47
workflow-type: tm+mt
source-wordcount: '805'
ht-degree: 2%

---

# Geavanceerde URL-configuraties {#url}

>[!NOTE]
>
>SEO (Search Engine Optimization, zoekmachineoptimalisatie) is voor veel marketeers een belangrijke zorg geworden. Daarom moeten de zorgen van de SEO over vele AEM projecten worden aangepakt. Zie [&#x200B; SEO en de Beste praktijken van het Beheer URL &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-65/managing/managing-further-reference/seo-and-url-management.html?lang=nl-NL) voor extra informatie.

[&#x200B; AEM CIF de Componenten van de Kern &#x200B;](https://github.com/adobe/aem-core-cif-components) verstrekt geavanceerde configuraties om URLs voor product en categoriepagina&#39;s aan te passen. In veel implementaties worden deze URL&#39;s aangepast voor SEO-doeleinden (Search Engine Optimization, optimalisatie van zoekprogramma&#39;s). De volgende videodetails hoe te om de `UrlProvider` Dienst en eigenschappen van [&#x200B; het Schipen Afbeelding &#x200B;](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html) te vormen om URLs voor product en categoriepagina&#39;s aan te passen.

>[!VIDEO](https://video.tv.adobe.com/v/34350/?quality=12)

## Configuratie {#configuration}

Om de `UrlProvider` dienst volgens de SEO vereisten te vormen en een project moet een configuratie OSGI voor de &quot;CIF configuratie van de Leverancier URL&quot;verstrekken.

>[!NOTE]
>
>Sinds versie 2.0.0 van de AEM CIF Core Components, verstrekt de configuratie van de Leverancier URL slechts vooraf bepaalde formaten url, in plaats van vrij-tekst configureerbare formaten die van 1.x versies bekend worden. Bovendien is het gebruik van kiezers voor het doorgeven van gegevens in URL&#39;s vervangen door achtervoegsels.

### URL-indeling van productpagina {#product}

Hiermee configureert u de URL&#39;s van de productpagina&#39;s en ondersteunt u de volgende opties:

* `{{page}}.html/{{sku}}.html#{{variant_sku}}` (standaardwaarde)
* `{{page}}.html/{{url_key}}.html#{{variant_sku}}`
* `{{page}}.html/{{sku}}/{{url_key}}.html#{{variant_sku}}`
* `{{page}}.html/{{url_path}}.html#{{variant_sku}}`
* `{{page}}.html/{{sku}}/{{url_path}}.html#{{variant_sku}}`

Als er de [&#x200B; opslag van de Verwijzing van Venia &#x200B;](https://github.com/adobe/aem-cif-guides-venia) is:

* `{{page}}` wordt vervangen door `/content/venia/us/en/products/product-page`
* `{{sku}}` wordt bijvoorbeeld vervangen door de SKU van het product `VP09`
* `{{url_key}}` wordt bijvoorbeeld vervangen door de eigenschap `url_key` van het product. `lenora-crochet-shorts`
* `{{url_path}}` wordt bijvoorbeeld vervangen door `url_path` van het product `venia-bottoms/venia-pants/lenora-crochet-shorts`
* `{{variant_sku}}` wordt vervangen door de geselecteerde variant, bijvoorbeeld `VP09-KH-S`

Aangezien de `url_path` is vervangen, gebruiken de vooraf gedefinieerde product-URL-indelingen de indeling van een product `url_rewrites` en kiezen de indeling met de meeste padsegmenten als alternatief als de `url_path` niet beschikbaar is.

Met de bovenstaande voorbeeldgegevens ziet een URL voor een productvariant die is opgemaakt met de standaard-URL-indeling eruit als `/content/venia/us/en/products/product-page.html/VP09.html#VP09-KH-S` .

### Categorie Pagina-URL-indeling {#product-list}

Hiermee configureert u de URL&#39;s van de pagina&#39;s in de categorie- of productlijst en ondersteunt u de volgende opties:

* `{{page}}.html/{{url_path}}.html` (standaardwaarde)
* `{{page}}.html/{{url_key}}.html`

Als er de [&#x200B; opslag van de Verwijzing van Venia &#x200B;](https://github.com/adobe/aem-cif-guides-venia) is:

* `{{page}}` wordt vervangen door `/content/venia/us/en/products/category-page`
* `{{url_key}}` wordt vervangen door de eigenschap `url_key` van de categorie
* `{{url_path}}` wordt vervangen door de categorie `url_path`

Met de bovenstaande voorbeeldgegevens ziet een categoriepagina-URL die is opgemaakt met de standaard-URL-indeling eruit als `/content/venia/us/en/products/category-page.html/venia-bottoms/venia-pants.html` .

>[!NOTE]
> 
>`url_path` is een samenvoeging van de `url_keys` van de voorouders van een product of categorie en de `url_key` van het product of de categorie gescheiden door `/` slash.

### Specifieke categorie-/productpagina&#39;s {#specific-pages}

Het is mogelijk om [&#x200B; veelvoudige categorie en productpagina&#39;s &#x200B;](multi-template-usage.md) voor slechts een specifieke ondergroep van categorieën of producten van een catalogus tot stand te brengen.

`UrlProvider` is vooraf geconfigureerd om diepgaande koppelingen naar dergelijke pagina&#39;s te genereren op instanties van de auteurslaag. Dit is handig voor editors die in de modus Voorbeeld door een site bladeren, naar een specifiek product of een bepaalde categoriepagina navigeren en terugschakelen naar de modus Bewerken om de pagina te bewerken.

Bij publicatie-klasseninstanties daarentegen moeten URL&#39;s van cataloguspagina&#39;s stabiel worden gehouden om bijvoorbeeld geen winsten op beoordelingen van zoekprogramma&#39;s te verliezen. Vanwege deze publicatie-tier-instanties worden er geen diepgaande koppelingen naar specifieke cataloguspagina&#39;s per standaard weergegeven. Om dit gedrag te veranderen, kan de _CIF URL Provider Specifieke Strategie van de Pagina_ worden gevormd om specifieke pagina-URL&#39;s altijd te produceren.

## Aangepaste URL-indelingen {#custom-url-format}

Om een formaat van douaneURL te verstrekken dat een project of [`ProductUrlFormat` &#x200B;](https://javadoc.io/doc/com.adobe.commerce.cif/core-cif-components-core/latest/com/adobe/cq/commerce/core/components/services/urls/ProductUrlFormat.html) of de [`CategoryUrlFormat` &#x200B;](https://javadoc.io/doc/com.adobe.commerce.cif/core-cif-components-core/latest/com/adobe/cq/commerce/core/components/services/urls/CategoryUrlFormat.html) de dienstinterface kan uitvoeren en de implementatie als dienst kan registreren OSGI. Deze implementaties, indien beschikbaar, vervangen de geconfigureerde, vooraf gedefinieerde indeling. Als er veelvoudige geregistreerde implementaties zijn, vervangt één met de hogere de dienstrangschikking degenen met de lagere de dienstrangschikking.

De de formaatimplementaties van douaneURL moeten een paar methodes uitvoeren om een URL van bepaalde parameters te bouwen, en een URL te ontleden om de zelfde parameters respectievelijk terug te keren.

## Combineren met Sling Mappings {#sling-mapping}

Naast `UrlProvider`, is het ook mogelijk om [&#x200B; het Schuiven Mappings &#x200B;](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html) te vormen om URLs te herschrijven en te verwerken. Het project van Archetype van de AEM verstrekt ook [&#x200B; een voorbeeldconfiguratie &#x200B;](https://github.com/adobe/aem-cif-project-archetype/tree/master/src/main/archetype/samplecontent/src/main/content/jcr_root/etc/map.publish) om sommige Wijzen voor haven 4503 (te vormen publiceert) en 80 (Dispatcher).

## Combineren met AEM Dispatcher {#dispatcher}

URL herschrijft kan ook worden bereikt door AEM Dispatcher HTTP-server met `mod_rewrite` module te gebruiken. Het [&#x200B; AEM Archieftype van het Project &#x200B;](https://github.com/adobe/aem-project-archetype) verstrekt een verwijzing AEM Dispatcher config die reeds basis[&#x200B; omvat herschrijft regels &#x200B;](https://github.com/adobe/aem-project-archetype/tree/master/src/main/archetype/dispatcher.cloud) voor de geproduceerde grootte.

## Voorbeeld

Het [&#128279;](https://github.com/adobe/aem-cif-guides-venia) project van de opslag van de Verwijzing van 0&rbrace; Venia &lbrace;omvat steekproefconfiguraties om het gebruik van douane URLs voor product en categoriepagina&#39;s aan te tonen.  Hierdoor kan elk project afzonderlijke URL-patronen instellen voor product- en categoriepagina&#39;s op basis van hun SEO-behoeften. Er wordt een combinatie van CIF `UrlProvider` en Sling Mappings gebruikt, zoals hierboven beschreven.

>[!NOTE]
>
>Deze configuratie moet met het externe domein worden aangepast dat door het project wordt gebruikt. Sling Mappings werkt gebaseerd op hostname en domein. Daarom is deze configuratie onbruikbaar gemaakt door gebrek en moet vóór plaatsing worden toegelaten. Wijzig hiertoe de naam van de map Sling Mapping `hostname.adobeaemcloud.com` in `ui.content/src/main/content/jcr_root/etc/map.publish/https` volgens de gebruikte domeinnaam en schakel deze configuratie in door `resource.resolver.map.location="/etc/map.publish"` toe te voegen aan de `JcrResourceResolver` config van het project.

## Aanvullende bronnen

* [&#x200B; de opslag van de Verwijzing van Venia &#x200B;](https://github.com/adobe/aem-cif-guides-venia)
* [&#x200B; AEM Middel in kaart brengen &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/resource-mapping.html?lang=nl-NL)
* [&#x200B; Sling Mappings &#x200B;](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html)
