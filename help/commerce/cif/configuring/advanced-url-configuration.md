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
>SEO (Search Engine Optimization, zoekmachineoptimalisatie) is voor veel marketeers een belangrijke zorg geworden. Daarom moeten de zorgen van de SEO over vele AEM projecten worden aangepakt. Zie [Aanbevolen werkwijzen voor SEO- en URL-beheer](https://experienceleague.adobe.com/docs/experience-manager-65/managing/managing-further-reference/seo-and-url-management.html) voor aanvullende informatie.

[CIF kerncomponenten AEM](https://github.com/adobe/aem-core-cif-components) biedt geavanceerde configuraties om de URL&#39;s voor product- en categoriepagina&#39;s aan te passen. In veel implementaties worden deze URL&#39;s aangepast voor SEO-doeleinden (Search Engine Optimization, optimalisatie van zoekprogramma&#39;s). De volgende videodetails hoe te om te vormen `UrlProvider` Service en kenmerken van [Sling Mapping](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html) om de URL&#39;s voor product- en categoriepagina&#39;s aan te passen.

>[!VIDEO](https://video.tv.adobe.com/v/34350/?quality=12)

## Configuratie {#configuration}

Om te vormen `UrlProvider` De dienst volgens de eisen van SEO en vereist een project moet een configuratie OSGI voor de &quot;CIF configuratie van de Leverancier URL&quot;verstrekken.

>[!NOTE]
>
>Sinds versie 2.0.0 van de AEM CIF Core Components, verstrekt de configuratie van de Leverancier URL slechts vooraf bepaalde formaten url, in plaats van vrij-tekst configureerbare formaten die van 1.x versies bekend worden. Bovendien is het gebruik van kiezers voor het doorgeven van gegevens in URL&#39;s vervangen door achtervoegsels.

### URL-indeling van productpagina {#product}

Hiermee configureert u de URL&#39;s van de productpagina&#39;s en ondersteunt u de volgende opties:

* `{{page}}.html/{{sku}}.html#{{variant_sku}}` (standaard)
* `{{page}}.html/{{url_key}}.html#{{variant_sku}}`
* `{{page}}.html/{{sku}}/{{url_key}}.html#{{variant_sku}}`
* `{{page}}.html/{{url_path}}.html#{{variant_sku}}`
* `{{page}}.html/{{sku}}/{{url_path}}.html#{{variant_sku}}`

Als er een [Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia):

* `{{page}}` wordt vervangen door `/content/venia/us/en/products/product-page`
* `{{sku}}` wordt bijvoorbeeld vervangen door de SKU van het product, `VP09`
* `{{url_key}}` wordt vervangen door `url_key` eigenschap, bijvoorbeeld `lenora-crochet-shorts`
* `{{url_path}}` wordt vervangen door `url_path`, bijvoorbeeld `venia-bottoms/venia-pants/lenora-crochet-shorts`
* `{{variant_sku}}` wordt vervangen door bijvoorbeeld de geselecteerde variant; `VP09-KH-S`

Aangezien de `url_path` verouderd zijn, de vooraf gedefinieerde product-URL-indelingen gebruiken de indeling van een product `url_rewrites` en kies het pad met de meeste padsegmenten als alternatief `url_path` is niet beschikbaar.

Met de bovenstaande voorbeeldgegevens ziet een product-variant-URL die is opgemaakt met de standaard-URL-indeling eruit als `/content/venia/us/en/products/product-page.html/VP09.html#VP09-KH-S`.

### Categorie Pagina-URL-indeling {#product-list}

Hiermee configureert u de URL&#39;s van de pagina&#39;s in de categorie- of productlijst en ondersteunt u de volgende opties:

* `{{page}}.html/{{url_path}}.html` (standaard)
* `{{page}}.html/{{url_key}}.html`

Als er een [Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia):

* `{{page}}` wordt vervangen door `/content/venia/us/en/products/category-page`
* `{{url_key}}` wordt vervangen door de categorie `url_key` eigenschap
* `{{url_path}}` wordt vervangen door de categorie `url_path`

Met de bovenstaande voorbeeldgegevens ziet een categoriepagina-URL die is opgemaakt met de standaard-URL-indeling eruit als `/content/venia/us/en/products/category-page.html/venia-bottoms/venia-pants.html`.

>[!NOTE]
> 
>De `url_path` is een aaneenschakeling van `url_keys` van een product of categorie en het product of de categorie `url_key` gescheiden door `/` slash.

### Specifieke categorie-/productpagina&#39;s {#specific-pages}

Het is mogelijk [meerdere categorieën en productpagina&#39;s](multi-template-usage.md) alleen voor een specifieke subset van categorieën of producten van een catalogus.

De `UrlProvider` vooraf geconfigureerd is om diepgaande koppelingen naar dergelijke pagina&#39;s te genereren op instanties van de auteurslaag. Dit is handig voor editors die in de modus Voorbeeld door een site bladeren, naar een specifiek product of een bepaalde categoriepagina navigeren en terugschakelen naar de modus Bewerken om de pagina te bewerken.

Bij publicatie-klasseninstanties daarentegen moeten URL&#39;s van cataloguspagina&#39;s stabiel worden gehouden om bijvoorbeeld geen winsten op beoordelingen van zoekprogramma&#39;s te verliezen. Vanwege deze publicatie-tier-instanties worden er geen diepgaande koppelingen naar specifieke cataloguspagina&#39;s per standaard weergegeven. Als u dit gedrag wilt wijzigen, _Specifieke paginastrategie voor URL-provider CIF_ kan worden gevormd om specifieke paginaURL&#39;s altijd te produceren.

## Aangepaste URL-indelingen {#custom-url-format}

Om een formaat van douaneURL te verstrekken dat een project of kan uitvoeren [`ProductUrlFormat`](https://javadoc.io/doc/com.adobe.commerce.cif/core-cif-components-core/latest/com/adobe/cq/commerce/core/components/services/urls/ProductUrlFormat.html) of de [`CategoryUrlFormat`](https://javadoc.io/doc/com.adobe.commerce.cif/core-cif-components-core/latest/com/adobe/cq/commerce/core/components/services/urls/CategoryUrlFormat.html) de dienstinterface en registreert de implementatie als dienst OSGI. Deze implementaties, indien beschikbaar, vervangen de geconfigureerde, vooraf gedefinieerde indeling. Als er veelvoudige geregistreerde implementaties zijn, vervangt één met de hogere de dienstrangschikking degenen met de lagere de dienstrangschikking.

De de formaatimplementaties van douaneURL moeten een paar methodes uitvoeren om een URL van bepaalde parameters te bouwen, en een URL te ontleden om de zelfde parameters respectievelijk terug te keren.

## Combineren met Sling Mappings {#sling-mapping}

Naast de `UrlProvider`is het ook mogelijk om [Sling Mappings](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html) om URL&#39;s te herschrijven en te verwerken. Het project AEM Archetype biedt ook [een voorbeeldconfiguratie](https://github.com/adobe/aem-cif-project-archetype/tree/master/src/main/archetype/samplecontent/src/main/content/jcr_root/etc/map.publish) om sommige Wijzen van het Monteren voor haven 4503 (publiceren) en 80 (Verzender) te vormen.

## Combineren met AEM Dispatcher {#dispatcher}

URL herschrijft kan ook worden bereikt door AEM Dispatcher HTTP-server met `mod_rewrite` -module. De [Projectarchetype AEM](https://github.com/adobe/aem-project-archetype) verstrekt een verwijzing AEM Dispatcher config die reeds basisomvat [herschrijfregels](https://github.com/adobe/aem-project-archetype/tree/master/src/main/archetype/dispatcher.cloud) voor de gegenereerde grootte.

## Voorbeeld

De [Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia) Het project bevat voorbeeldconfiguraties om het gebruik van aangepaste URL&#39;s voor product- en categoriepagina&#39;s aan te tonen. Hierdoor kan elk project afzonderlijke URL-patronen instellen voor product- en categoriepagina&#39;s op basis van hun SEO-behoeften. Een combinatie van CIF `UrlProvider` en Sling Mappings zoals hierboven beschreven wordt gebruikt.

>[!NOTE]
>
>Deze configuratie moet met het externe domein worden aangepast dat door het project wordt gebruikt. Sling Mappings werkt gebaseerd op hostname en domein. Daarom is deze configuratie onbruikbaar gemaakt door gebrek en moet vóór plaatsing worden toegelaten. De naam van de functie voor het toewijzen van objecten wijzigen `hostname.adobeaemcloud.com` map in `ui.content/src/main/content/jcr_root/etc/map.publish/https` volgens de gebruikte domeinnaam en laat dit config toe door toe te voegen `resource.resolver.map.location="/etc/map.publish"` aan de `JcrResourceResolver` config van het project.

## Aanvullende bronnen

* [Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia)
* [Brontoewijzing AEM](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/resource-mapping.html)
* [Sling Mappings](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html)
