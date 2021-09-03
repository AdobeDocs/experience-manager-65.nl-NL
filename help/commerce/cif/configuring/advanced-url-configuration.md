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
source-git-commit: fd973cb3693872e4850f860a625cab70553d2754
workflow-type: tm+mt
source-wordcount: '784'
ht-degree: 4%

---

# Geavanceerde URL-configuraties {#url}

>[!NOTE]
>
> SEO (Search Engine Optimization, zoekmachineoptimalisatie) is voor veel marketeers een belangrijke zorg geworden. Daarom moet bij veel AEM projecten rekening worden gehouden met de bezorgdheid van de ZOO. Lees [SEO en URL Management Best Practices](https://experienceleague.adobe.com/docs/experience-manager-65/managing/managing-further-reference/seo-and-url-management.html) voor meer informatie.

[AEM CIF Core-](https://github.com/adobe/aem-core-cif-components) componenten biedt geavanceerde configuraties om de URL&#39;s voor product- en categoriepagina&#39;s aan te passen. In veel implementaties worden deze URL&#39;s aangepast voor SEO-doeleinden (Search Engine Optimization, optimalisatie van zoekprogramma&#39;s). In de volgende video ziet u hoe u de `UrlProvider`-service en functies van [Sling Mapping](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html) configureert om de URL&#39;s voor product- en categoriepagina&#39;s aan te passen.

>[!VIDEO](https://video.tv.adobe.com/v/34350/?quality=12)

## Configuratie {#configuration}

Om de `UrlProvider` dienst volgens de SEO vereisten te vormen en een project moet een configuratie OSGI voor de &quot;configuratie van de Leverancier CIF verstrekken URL&quot;.

>[!NOTE]
>
> Sinds versie 2.0.0 van de AEM CIF Core Components, verstrekt de configuratie van de Leverancier URL slechts vooraf bepaalde url formaten, in plaats van vrij-tekst configureerbare formaten die van 1.x versies worden gekend. Bovendien is het gebruik van kiezers voor het doorgeven van gegevens in URL&#39;s vervangen door achtervoegsels.

### URL-indeling van productpagina {#product}

Hiermee configureert u de URL&#39;s van de productpagina&#39;s en ondersteunt u de volgende opties:

* `{{page}}.html/{{sku}}.html#{{variant_sku}}` (standaardwaarde)
* `{{page}}.html/{{url_key}}.html#{{variant_sku}}`
* `{{page}}.html/{{sku}}/{{url_key}}.html#{{variant_sku}}`
* `{{page}}.html/{{url_path}}.html#{{variant_sku}}`
* `{{page}}.html/{{sku}}/{{url_path}}.html#{{variant_sku}}`

In het geval van het [Referentiearchief van Venia](https://github.com/adobe/aem-cif-guides-venia):

* `{{page}}` wordt vervangen door  `/content/venia/us/en/products/product-page`
* `{{sku}}` worden vervangen door de sku van het product, bijvoorbeeld  `VP09`
* `{{url_key}}` worden vervangen door de  `url_key` eigenschap van het product, bijvoorbeeld  `lenora-crochet-shorts`
* `{{url_path}}` worden vervangen door het product,  `url_path`bijvoorbeeld  `venia-bottoms/venia-pants/lenora-crochet-shorts`
* `{{variant_sku}}` worden vervangen door de momenteel geselecteerde variant, bijvoorbeeld  `VP09-KH-S`

Met de bovenstaande voorbeeldgegevens ziet een product-variant-URL die is opgemaakt met de standaard-URL-indeling eruit als `/content/venia/us/en/products/product-page.html/VP09.html#VP09-KH-S`.

### Categorie Pagina-URL-indeling {#product-list}

Hiermee configureert u de URL&#39;s van de pagina&#39;s in de categorie- of productlijst en ondersteunt u de volgende opties:

* `{{page}}.html/{{url_path}}.html` (standaardwaarde)
* `{{page}}.html/{{url_key}}.html`

In het geval van het [Referentiearchief van Venia](https://github.com/adobe/aem-cif-guides-venia):

* `{{page}}` wordt vervangen door  `/content/venia/us/en/products/category-page`
* `{{url_key}}` wordt vervangen door de  `url_key` eigenschap van de categorie
* `{{url_path}}` worden vervangen door de categorie  `url_path`

Met de bovenstaande voorbeeldgegevens ziet een categoriepagina-URL die is opgemaakt met de standaard-URL-indeling eruit als `/content/venia/us/en/products/category-page.html/venia-bottoms/venia-pants.html`.

>[!NOTE]
> 
> De `url_path` is een samenvoeging van de `url_keys` van een product of categorie en het product of de categorie `url_key` gescheiden door `/` schuine streep.

## Aangepaste URL-indelingen {#custom-url-format}

Om een formaat van douaneURL te verstrekken kan een project [`UrlFormat` interface ](https://javadoc.io/doc/com.adobe.commerce.cif/core-cif-components-core/latest/com/adobe/cq/commerce/core/components/services/urls/UrlFormat.html) uitvoeren en de implementatie als dienst registreren OSGI, gebruikend het of als categorie pagina of het formaat van de productpagina url. Het `UrlFormat#PROP_USE_AS` de dienstbezit wijst op, welke van de gevormde vooraf bepaalde formaten te vervangen:

* `useAs=productPageUrlFormat`, vervangt de geconfigureerde URL-indeling van de productpagina
* `useAs=categoryPageUrlFormat`, vervangt de geconfigureerde URL-indeling voor de categoriepagina

Als er meerdere implementaties zijn van de `UrlFormat` die als OSGI-services zijn geregistreerd, vervangt de implementatie met de hogere servicerangschikking de één of meerdere implementaties door de lagere servicerangschikking.

`UrlFormat` moet een paar methodes uitvoeren om een URL van een bepaalde Kaart van parameters te bouwen en een URL te ontleden om de zelfde Kaart van parameters terug te keren. De parameters zijn hetzelfde als hierboven beschreven, alleen voor categorieën wordt een extra `{{uid}}`-parameter aan `UrlFormat` gegeven.

## Combineren met Sling Mappings {#sling-mapping}

Naast `UrlProvider` is het ook mogelijk om [Sling Mappings](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html) te vormen om URLs te herschrijven en te verwerken. Het project van Archetype van het AEM verstrekt ook [een voorbeeldconfiguratie](https://github.com/adobe/aem-cif-project-archetype/tree/master/src/main/archetype/samplecontent/src/main/content/jcr_root/etc/map.publish) om sommige Toewijzingen Sling voor haven 4503 (publiceren) en 80 (verzender) te vormen.

## Combineren met AEM Dispatcher {#dispatcher}

URL herschrijft kan ook worden bereikt door AEM server van HTTP van de Verzender met `mod_rewrite` module te gebruiken. [AEM Projectarchetype](https://github.com/adobe/aem-project-archetype) verstrekt een verwijzing AEM de config van de Verzender die reeds basisregels [herschrijven ](https://github.com/adobe/aem-project-archetype/tree/master/src/main/archetype/dispatcher.cloud) voor de geproduceerde grootte omvat.

## Voorbeeld

Het project [Venia Reference store](https://github.com/adobe/aem-cif-guides-venia) bevat voorbeeldconfiguraties om het gebruik van aangepaste URL&#39;s voor product- en categoriepagina&#39;s aan te tonen. Hierdoor kan elk project afzonderlijke URL-patronen instellen voor product- en categoriepagina&#39;s op basis van hun SEO-behoeften. Er wordt een combinatie van CIF `UrlProvider` en Sling Mappings zoals hierboven beschreven gebruikt.

>[!NOTE]
>
>Deze configuratie moet met het externe domein worden aangepast dat door het project wordt gebruikt. Sling Mappings werkt gebaseerd op hostname en domein. Daarom is deze configuratie onbruikbaar gemaakt door gebrek en moet vóór plaatsing worden toegelaten. Om dit te doen anders noem de het Verschuiven omslag `hostname.adobeaemcloud.com` in `ui.content/src/main/content/jcr_root/etc/map.publish/https` volgens de gebruikte domeinnaam en laat dit config toe door `resource.resolver.map.location="/etc/map.publish"` aan &lt;a3 toe te voegen/> config van het project.`JcrResourceResolver`

## Aanvullende bronnen

* [Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia)
* [Brontoewijzing AEM](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/resource-mapping.html)
* [Sling Mappings](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html)
