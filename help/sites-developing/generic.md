---
title: Ontwikkelen (algemeen)
seo-title: Ontwikkelen (algemeen)
description: Het integratieframework bevat een integratielaag met een API, waarmee u AEM-componenten kunt maken voor eCommerce-mogelijkheden
seo-description: Het integratieframework bevat een integratielaag met een API, waarmee u AEM-componenten kunt maken voor eCommerce-mogelijkheden
uuid: 393bb28a-9744-44f4-9796-09228fcd466f
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: platform
discoiquuid: d8ee3b57-633a-425e-bf36-646f0e0bad52
translation-type: tm+mt
source-git-commit: ebf3f34af7da6b1a659ac8d8843152b97f30b652
workflow-type: tm+mt
source-wordcount: '1886'
ht-degree: 0%

---


# Ontwikkelen (algemeen){#developing-generic}

>[!NOTE]
>
>[API-documentatie](/help/sites-developing/ecommerce.md#api-documentation) is ook beschikbaar.

Het integratieframework bevat een integratielaag met een API. Hierdoor kunt u AEM-componenten voor eCommerce-mogelijkheden maken (onafhankelijk van uw specifieke eCommerce-engine). Het staat u ook toe om het interne gegevensbestand van CRX te gebruiken of in een systeem van de eCommerce te stoppen en productgegevens in AEM te trekken.

Voor het gebruik van de integratielaag wordt een aantal AEM-componenten buiten de doos meegeleverd. Deze zijn momenteel:

* Een product weergavecomponent
* Een winkelwagentje
* Promoties en vouchers
* Blauwdrukken voor catalogus en secties
* Uitchecken
* Zoeken

Voor onderzoek wordt een integratiehaak verstrekt die u toestaat om het AEM onderzoek, een derderdesonderzoek (zoals Search&amp;Promote) of een combinatie van daarvan te gebruiken.

## Selectie van eCommerce-engine {#ecommerce-engine-selection}

Het eCommerce-kader kan met elke eCommerce-oplossing worden gebruikt, waarbij de gebruikte motor door AEM moet worden geïdentificeerd - zelfs wanneer de algemene AEM-motor wordt gebruikt:

* eCommerce Engines zijn OSGi-services die de `CommerceService` interface ondersteunen

   * Motoren kunnen worden onderscheiden door een `commerceProvider` service-eigenschap

* AEM ondersteunt `Resource.adaptTo()` voor `CommerceService` en `Product`

   * De `adaptTo` implementatie zoekt naar een `cq:commerceProvider` eigenschap in de hiërarchie van de bron:

      * Indien gevonden, wordt de waarde gebruikt om de raadpleging van de handelsdienst te filtreren.
      * Indien niet gevonden, wordt de hoogste commerciële dienst gebruikt.
   * Een `cq:Commerce` mixin wordt gebruikt zodat `cq:commerceProvider` kan aan sterk-getypte middelen worden toegevoegd.


* De `cq:commerceProvider` eigenschap wordt ook gebruikt om naar de juiste definitie van de handelsfabriek te verwijzen.

   * Bijvoorbeeld, zal een `cq:commerceProvider` bezit met de waardegeometrixx met de configuratie OSGi voor de Factory van de Handel van **Dag CQ voor Geometrixx-Buiten** (`com.adobe.cq.commerce.hybris.impl.GeoCommerceServiceFactory`) correleren - waar de parameter `commerceProvider` ook de waarde `geometrixx`heeft.
   * Hier kunnen verdere eigenschappen worden gevormd (wanneer aangewezen en beschikbaar).

In een standaard AEM-installatie is een specifieke implementatie vereist, bijvoorbeeld:

|  |  |
|---|---|
| `cq:commerceProvider = geometrixx` | geometrixx-voorbeeld; dit omvat minimale uitbreidingen van de algemene API |

### Voorbeeld {#example}

```shell
/etc/commerce/products/geometrixx-outdoors
+ cq:commerceProvider = geometrixx
  + adobe-logo-shirt
    + cq:commerceType = product
    + price = 12.50
  + adobe-logo-shirt_S
    + cq:commerceType = variant
    + size = S
  + adobe-logo-shirt_XL
    + cq:commerceType = variant
    + size = XL
    + price = 14.50
```

>[!NOTE]
>
>Gebruikend CRXDE Lite kunt u zien hoe dit in de productcomponent voor de algemene implementatie AEM wordt behandeld:
>
>`/apps/geometrixx-outdoors/components/product`

### Sessieafhandeling {#session-handling}

Een sessie voor het opslaan van informatie over het winkelwagentje van de klant.

De **CommerceSession**:

* Heeft **winkelwagentje**

   * toevoegen/verwijderen/enz. uitvoeren
   * de verschillende berekeningen op het karretje uitvoert;

      `commerceSession.getProductPriceInfo(Product product, Predicate filter)`

* Persistentie van de **ordergegevens** :

   `CommerceSession.getUserContext()`

* Kan leveringsdetails ophalen/bijwerken met behulp van `updateOrder(Map<String, Object> delta)`
* Is ook eigenaar van de **betalingsverwerkingsverbinding**
* Heeft ook de **uitvoeringsverbinding**

### Architectuur {#architecture}

#### Architectuur van product en varianten {#architecture-of-product-and-variants}

Eén product kan meerdere variaties hebben; kan bijvoorbeeld variëren per kleur en/of grootte. Een product moet bepalen welke eigenschappen de variatie aansturen; we noemen deze *variantassen*.

Niet alle eigenschappen zijn echter variantassen. Variaties kunnen ook andere eigenschappen beïnvloeden; de prijs kan bijvoorbeeld afhankelijk zijn van de omvang . Deze eigenschappen kunnen niet door de verkoopster worden geselecteerd en worden daarom niet als variantassen beschouwd.

Elk product en/of elke variant wordt vertegenwoordigd door een middel, en daarom kaarten 1:1 aan een gegevensopslagknoop. Het gevolg is dat een specifiek product en/of specifieke variant op unieke wijze kan worden geïdentificeerd door het pad ervan.

Elke productbron kan worden vertegenwoordigd door een `Product API`. De meeste aanroepen in de product-API zijn variatiespecifiek (hoewel variaties gedeelde waarden kunnen overerven van een voorouder), maar er zijn ook aanroepen die de set variaties vermelden ( `getVariantAxes()`, `getVariants()`, enz.).

>[!NOTE]
>
>In feite wordt een variant as bepaald door wat er `Product.getVariantAxes()` terugkeert:
>
>* voor de generieke implementatie leest AEM het uit een bezit in de productgegevens ( `cq:productVariantAxes`)
>
>
Hoewel producten (in het algemeen) vele variantassen kunnen hebben, behandelt de uit-van-de-doos productcomponent slechts twee:
>
>1. `size`
>1. plus één of meer
>
>   
Deze extra variant wordt geselecteerd via de `variationAxis` eigenschap van de productreferentie (gewoonlijk `color` voor Geometrixx Buiten).

#### Productverwijzingen en PIM-gegevens {#product-references-and-pim-data}

In het algemeen:

* PIM-gegevens bevinden zich onder `/etc`

* Productreferenties onder `/content`.

Er moet een 1:1-kaart zijn tussen productvariaties en productgegevensknooppunten.

Productverwijzingen moeten ook een knooppunt hebben voor elke gepresenteerde variatie - maar er is geen verplichting om alle variaties weer te geven. Als een product bijvoorbeeld S, M, L-variaties heeft, kunnen de productgegevens als volgt zijn:

```shell
etc
  commerce
    products
      shirt
        shirt-s
        shirt-m
        shirt-l
```

Een catalogus van het type &quot;Big and Tall&quot; kan alleen het volgende bevatten:

```shell
content
  big-and-tall
    shirt
      shirt-l
```

Tot slot is er geen verplichting om productgegevens te gebruiken. U kunt alle productgegevens onder de verwijzingen in de catalogus plaatsen; maar dan kunt u niet echt meerdere catalogi hebben zonder alle productgegevens te dupliceren.

**API**

#### com.adobe.cq.commerce.api.Product interface {#com-adobe-cq-commerce-api-product-interface}

```java
public interface Product extends Adaptable {

    public String getPath();            // path to specific variation
    public String getPagePath();        // path to presentation page for all variations
    public String getSKU();             // unique ID of specific variation

    public String getTitle();           // shortcut to getProperty(TITLE)
    public String getDescription();     // shortcut to getProperty(DESCRIPTION)
    public String getImageUrl();        // shortcut to getProperty(IMAGE_URL)
    public String getThumbnailUrl();    // shortcut to getProperty(THUMBNAIL_URL)

    public <T> T getProperty(String name, Class<T> type);

    public Iterator<String> getVariantAxes();
    public boolean axisIsVariant(String axis);
    public Iterator<Product> getVariants(VariantFilter filter) throws CommerceException;
}
```

#### com.adobe.cq.commerce.api.VariantFilter  {#com-adobe-cq-commerce-api-variantfilter}

```java
/**
 * Interface for filtering variants and AxisFilter provided as common implementation
 *
 * The <code>VariantFilter</code> is used to filter variants,
 * e.g. when using {@link Product#getVariants(VariantFilter filter)}.
 */
public interface VariantFilter {
    public boolean includes(Product product);
}

/**
 * A {@link VariantFilter} for filtering variants by the given
 * axis and value. The following example returns a list of
 * variant products that have a value of <i>blue</i> on the
 * <i>color</i> axis.
 *
 * <p>
 * <code>product.getVariants(new AxisFilter("color", "blue"));</code>
 */
public class AxisFilter implements VariantFilter {

    private String axis;
    private String value;

    public AxisFilter(String axis, String value) {
        this.axis = axis;
        this.value = value;
    }

    /**
     * {@inheritDoc}
     */
    public boolean includes(Product product) {
        ValueMap values = product.adaptTo(ValueMap.class);

        if(values != null) {
            String v = values.get(axis, String.class);

            return v != null && v == value;
        }

        return false;
    }
}
```

* **Algemeen opslagmechanisme**

   * Productknooppunten zijn niet:ongestructureerd.
   * Een productknooppunt kan:

      * Een verwijzing, met de elders opgeslagen productgegevens:

         * Productverwijzingen bevatten een `productData` eigenschap die verwijst naar de productgegevens (doorgaans onder `/etc/commerce/products`).
         * De productgegevens zijn hiërarchisch; productkenmerken worden overgenomen van de voorouders van een productgegevensknooppunt.
         * De verwijzingen van het product kunnen lokale eigenschappen ook bevatten, die die in hun productgegevens worden gespecificeerd met voeten treden.
      * Een product zelf:

         * Zonder een `productData` eigenschap.
         * Een productknooppunt dat alle eigenschappen lokaal bevat (en geen eigenschap productData bevat), neemt productkenmerken rechtstreeks van zijn eigen voorouders over.


* **AEM-algemene productstructuur**

   * Elke variant moet een eigen bladnode hebben.
   * De interface van het product vertegenwoordigt zowel producten als varianten, maar het verwante gegevensopslagknooppunt is specifiek waarover het is.
   * Het productknooppunt beschrijft de productkenmerken en de variantassen.

#### Voorbeeld {#example-1}

```shell
+ banyan_shirt
    - cq:commerceType = product
    - cq:productAttributes = [jcr:title, jcr:description, size, price, color]
    - cq:productVariantAxes = [color, size]
    - jcr:title = Banyan Shirt
    - jcr:description = Flowery, all-cotton shirt.
    - price = 14.00
    + banyan_shirt_s
        - cq:commerceType = variant
        - size = S
        + banyan_shirt_s_red
            - cq:commerceType = variant
            - color = red
        + banyan_shirt_s_blue
            - cq:commerceType = variant
            - color = blue
    + banyan_shirt_m
        - cq:commerceType = variant
        - size = M
        + banyan_shirt_m_red
            - cq:commerceType = variant
            - color = red
        + banyan_shirt_m_blue
            - cq:commerceType = variant
            - color = blue
    + banyan_shirt_l
        - cq:commerceType = variant
        - size = L
        + banyan_shirt_l_red
            - cq:commerceType = variant
            - color = red
        + banyan_shirt_l_blue
            - cq:commerceType = variant
            - color = blue
    + banyan_shirt_xl
        - cq:commerceType = variant
        - size = XL
        - price = 18.00
```

#### Architectuur van het winkelwagentje {#architecture-of-the-shopping-cart}

**Onderdelen**

* Het winkelwagentje is eigendom van de `CommerceSession:`

   * De `CommerceSession` functie voegt toe, verwijdert, enzovoort.
   * De Commissie voert `CommerceSession` ook de verschillende berekeningen op het winkelwagentje uit.
   * De code past `CommerceSession` ook vouchers en promoties toe die op de wagen zijn geactiveerd.

* Hoewel zij niet rechtstreeks verband houden met het winkelwagentje, `CommerceSession` moet zij ook informatie over catalogusprijzen verstrekken (aangezien zij eigenaar is van prijzen)

   * Prijzen kunnen verschillende opties hebben:

      * Kwantiseringen.
      * Verschillende valuta&#39;s.
      * BTW-plichtig en btw-vrij.
   * De modifiers zijn volledig open-eind met de volgende interface:

      * `int CommerceSession.getQuantityBreakpoints(Product product)`
      * `String CommerceSession.getProductPrice(Product product)`


**Opslag**

* Opslag

   * In de AEM-generische gevalskaarten van worden opgeslagen in [ClientContext](/help/sites-administering/client-context.md)

**Personalisatie**

* De aanpassing zou altijd door [ClientContext](/help/sites-administering/client-context.md)moeten worden aangedreven.
* In alle gevallen wordt een ClientContext `/version/` van het winkelwagentje gemaakt:

   * De producten moeten volgens de `CommerceSession.addCartEntry()` methode worden toegevoegd.

* In het volgende voorbeeld ziet u een voorbeeld van winkelwageninformatie in het ClientContext-winkelwagentje:

![chlimage_1-33](assets/chlimage_1-33a.png)

#### Architectuur van uitchecken {#architecture-of-checkout}

**Gegevens van winkelwagentjes en bestellingen**

De `CommerceSession` eigenaar van de drie elementen:

1. **Inhoud winkelwagentje**

   Het schema voor de inhoud van het winkelwagentje wordt bepaald door de API:

   ```java
       public void addCartEntry(Product product, int quantity);
       public void modifyCartEntry(int entryNumber, int quantity);
       public void deleteCartEntry(int entryNumber);
   ```

1. **Prijzen**

   Het prijsschema wordt ook bepaald door de API:

   ```java
       public String getCartPreTaxPrice();
       public String getCartTax();
       public String getCartTotalPrice();
       public String getOrderShipping();
       public String getOrderTotalTax();
       public String getOrderTotalPrice();
   ```

1. **Bestelgegevens**

   orderdetails worden echter *niet* door de API vastgelegd:

   ```java
       public void updateOrderDetails(Map<String, String> orderDetails);
       public Map<String, String> getOrderDetails();
       public void submitOrder();
   ```

**Verzendberekeningen**

* Vaak moeten bestelformulieren meerdere verzendopties (en prijzen) bieden.
* De prijzen kunnen gebaseerd zijn op artikelen en gegevens van de bestelling, zoals gewicht en/of bezorgadres.
* Het `CommerceSession` heeft toegang tot alle afhankelijkheden, zodat het op een vergelijkbare manier kan worden behandeld als productprijzen:

   * De `CommerceSession` eigenaar van de verzendprijs.
   * Gebruik deze optie `updateOrder(Map<String, Object> delta)` om leveringsgegevens op te halen/bij te werken.

### Zoekdefinitie {#search-definition}

Na het standaard dienstAPI model, verstrekt het eCommerce-project een reeks op onderzoek betrekking hebbende APIs die door individuele handelsmotoren kunnen worden uitgevoerd.

>[!NOTE]
>
>Momenteel implementeert alleen de hybris-engine de API voor zoeken buiten de box.
>
>Nochtans, is het onderzoek API generisch en kan door elke CommerceService individueel worden uitgevoerd.
>
>Hoewel de algemene implementatie die u hebt opgegeven deze API niet implementeert, kunt u deze wel uitbreiden en de zoekfunctionaliteit toevoegen.

Het eCommerce-project bevat een standaardzoekcomponent, die zich bevindt in:

`/libs/commerce/components/search`

![chlimage_1-34](assets/chlimage_1-34a.png)

Dit maakt gebruik van onderzoek API om de geselecteerde handelingsmotor (zie de Selectie [van de Motor van de](#ecommerce-engine-selection)Handel) te vragen:

#### Zoeken in API {#search-api}

Het kernproject bevat verschillende algemene klassen/hulpklassen:

1. `CommerceQuery`

   Wordt gebruikt om een zoekquery te beschrijven (bevat informatie over de querytekst, de huidige pagina, het paginaformaat, de sortering en de geselecteerde facetten). Alle eCommerce-services die de zoek-API implementeren, ontvangen instanties van deze klasse om hun zoekopdracht uit te voeren. Een `CommerceQuery` instructie kan worden gegeven vanuit een aanvraagobject ( `HttpServletRequest`).

1. `FacetParamHelper`

   Is een hulpprogrammaklasse die één statische methode - `toParams` - verstrekt die voor het produceren van `GET` parameterkoorden van een lijst van facetten en één knevelwaarde wordt gebruikt. Dit is handig aan de UI-zijde, waar u een hyperlink moet weergeven voor elke waarde van elk facet, zodat wanneer de gebruiker op de hyperlink klikt, de desbetreffende waarde wordt in- en uitgeschakeld (als deze is geselecteerd, wordt deze verwijderd uit de query, anders toegevoegd). Hierbij wordt rekening gehouden met alle logica van het omgaan met meerdere/enkele facetten, overschrijvende waarden, enzovoort.

Het ingangspunt voor zoekAPI is de `CommerceService#search` methode die een `CommerceResult` object retourneert. Zie de API Documentatie voor meer informatie over dit onderwerp.

### Promoties en vouchers ontwikkelen {#developing-promotions-and-vouchers}

* Vouchers:

   * Een Voucher is een op pagina&#39;s gebaseerde component die met de console van Websites wordt gecreeerd/uitgegeven en onder wordt opgeslagen:

      `/content/campaigns`

   * Levering aan vouchers:

      * Een vouchercode (die door de verkoper in de winkelwagen moet worden getypt).
      * Een voucherlabel (dat moet worden weergegeven nadat de gebruiker het in de winkelwagen heeft ingevoerd).
      * Een promotiepad (dat de actie definieert die de voucher toepast).
   * Vouchers hebben geen eigen datum/tijd, maar gebruiken die van hun bovenliggende campagnes.
   * ook motoren voor externe handel kunnen vouchers leveren; deze vereisen een minimum van :

      * Een vouwcode
      * Een `isValid()` methode
   * De **component Voucher** ( `/libs/commerce/components/voucher`) biedt:

      * Een renderer voor voucherbeheer; hieruit blijkt welke vouchers zich momenteel in de kar bevinden .
      * De bewerkingsdialoogvensters (formulier) voor het beheren (toevoegen/verwijderen) van de vouchers.
      * De handelingen die vereist zijn voor het toevoegen/verwijderen van vouchers aan/uit de kar.



* Promoties:

   * Een bevordering is een op pagina-gebaseerde component die met de console van Websites wordt gecreeerd/wordt uitgegeven en onder wordt opgeslagen:

      `/content/campaigns`

   * Aanbod voor promoties:

      * Een prioriteit
      * Een pad voor promotiemandschappen
   * U kunt promoties verbinden met een campagne om de aan/uit-datum of -tijden te definiëren.
   * U kunt promoties aan een ervaring verbinden om hun segmenten te bepalen.
   * Promoties die geen verband houden met een ervaring, worden niet op zichzelf afgegaan, maar kunnen nog steeds door een Voucher worden geactiveerd.
   * De component Bevordering ( `/libs/commerce/components/promotion`) bevat:

      * renderers en dialoogvensters voor bevorderingsbeheer
      * subcomponenten voor het teruggeven en het uitgeven configuratieparameters specifiek voor de bevorderingsmanagers
   * Er worden twee promotiehandlers uit de verpakking geleverd:

      * `DiscountPromotionHandler`, waarbij een absolute of percentagekorting voor het hele winkelwagentje wordt toegepast
      * `PerfectPartnerPromotionHandler`, die een absolute productkorting of een percentagekorting toepast als het partnerproduct ook in de kar is
   * ClientContext lost segmenten op en ClientContext `SegmentMgr` `CartMgr` lost bevorderingen op. Elke bevordering die aan minstens één opgelost segment onderworpen is zal worden in werking gesteld.

      * De gecreeerde Bevorderingen worden teruggestuurd naar de server via een vraag AJAX om het karretje opnieuw te berekenen.
      * Geactiveerde promoties (en toegevoegde vouchers) worden ook weergegeven in het deelvenster ClientContext.




Het toevoegen/verwijderen van een voucher uit een winkelwagentje gebeurt via de `CommerceSession` API:

```java
/**
 * Apply a voucher to this session's cart.
 *
 * @param code the voucher's code
 * @throws CommerceException
 */
public void addVoucher(String code) throws CommerceException;

/**
 * Remove a voucher that was previously added with {@link #addVoucher(String)}.
 *
 * @param code the voucher's code
 * @throws CommerceException
 */
public void removeVoucher(String code) throws CommerceException;

/**
 * Get a list of vouchers that were added to this cart via {@link #addVoucher(String)}.
 *
 * @throws CommerceException
 */
public List<Voucher> getVouchers() throws CommerceException;
```

Op deze manier `CommerceSession` controleert de gebruiker of een voucher bestaat en of deze kan worden toegepast. Dit kan het geval zijn voor vouchers die alleen kunnen worden toegepast als aan een bepaalde voorwaarde is voldaan; bijvoorbeeld wanneer de totale winkelwagenprijs hoger is dan $100). Als een voucher om welke reden dan ook niet kan worden toegepast, genereert de `addVoucher` methode een uitzondering. De klant `CommerceSession` is ook verantwoordelijk voor het bijwerken van de prijs/prijzen van het winkelwagentje nadat een voucher is toegevoegd/verwijderd.

De klasse `Voucher` is een boonachtige klasse die velden bevat voor:

* Code voucher
* Een korte beschrijving
* Verwijzen naar de verwante bevordering die op het disconteringstype en de waarde wijst

Met de `AbstractJcrCommerceSession` meegeleverde gegevens kunt u vouchers toepassen. De vouchers die door de klasse worden geretourneerd, `getVouchers()` zijn instanties van het `cq:Page` bevatten van een JCR:content-knooppunt met de volgende eigenschappen (onder andere):

* `sling:resourceType` (String) - dit moet `commerce/components/voucher`

* `jcr:title` (String) - voor de beschrijving van de voucher
* `code` (String) - de code die de gebruiker moet invoeren om deze voucher toe te passen
* `promotion` (String) - de promotie die moet worden toegepast; bijv. `/content/campaigns/geometrixx-outdoors/article/10-bucks-off`

Promotiehandlers zijn OSGi-services die het winkelwagentje wijzigen. De kar zal verscheidene haken steunen die in de `PromotionHandler` interface zullen worden bepaald.

```java
/**
 * Apply promotion to a cart line item. The method returns a discount
 * <code>PriceInfo</code> instance or <code>null</code> if no discount
 * was applied.
 * @param commerceSession The commerce session
 * @param promotion The configured promotion
 * @param cartEntry The cart line item
 * @return A discounted <code>PriceInfo</code> or <code>null</code>
 */
public PriceInfo applyCartEntryPromotion(CommerceSession commerceSession,
                                         Promotion promotion, CartEntry cartEntry)
    throws CommerceException;

/**
 * Apply promotion to an order. The method returns a discount
 * <code>PriceInfo</code> instance or <code>null</code> if no discount
 * was applied.
 * @param commerceSession The commerce session
 * @param promotion The configured promotion
 * @return A discounted <code>PriceInfo</code> or <code>null</code>
 */
public PriceInfo applyOrderPromotion(CommerceSession commerceSession, Promotion promotion)
    throws CommerceException;

public PriceInfo applyShippingPromotion(CommerceSession commerceSession, Promotion promotion)
    throws CommerceException;

/**
 * Allows a promotion handler to define a custom, author-oriented message for a promotion.
 * The {@link com.adobe.cq.commerce.common.promotion.PerfectPartnerPromotionHandler}, for instance,
 * uses this to list the qualifying pairs of products in the current cart.
 * @param commerceSession
 * @param promotion
 * @return A message to display
 * @throws CommerceException
 */
public String getMessage(SlingHttpServletRequest request, CommerceSession commerceSession, Promotion promotion) throws CommerceException;

/**
 * Informs the promotion handler that something under the promotions root has been edited, and the handler
 * should invalidate any caches it might be keeping.
 */
public void invalidateCaches();
```

Er zijn drie afhandelingen voor speciale acties beschikbaar:

* `DiscountPromotionHandler` past een absolute of percentagekorting voor het hele winkelwagentje toe
* `PerfectPartnerPromotionHandler` past een absolute of percentagekorting van het product toe als de productpartner ook in de kar is
* `FreeShippingPromotionHandler` past gratis verzending toe

