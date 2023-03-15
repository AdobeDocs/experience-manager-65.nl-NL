---
title: CIF Core-componenten aanpassen
description: Leer hoe u AEM CIF Core-componenten aanpast. In de zelfstudie wordt uitgelegd hoe u een CIF Core-component veilig kunt uitbreiden om aan bedrijfsspecifieke vereisten te voldoen. Leer hoe te om een vraag van GraphQL uit te breiden om een douanekenmerk terug te keren en de nieuwe attributen in een Component van de Kern van CIF te tonen.
sub-product: Commerce
topics: Development
version: Cloud Service
doc-type: tutorial
activity: develop
audience: developer
feature: Commerce Integration Framework
kt: 4279
thumbnail: customize-aem-cif-core-component.jpg
exl-id: 8933942e-be49-49d3-bf0a-7225257e2803
source-git-commit: b886844dc80482ae4aae5fc7ce09e466efecc3bd
workflow-type: tm+mt
source-wordcount: '2592'
ht-degree: 0%

---

# AEM CIF Core-componenten aanpassen {#customize-cif-components}

De [CIF Venia-project](https://github.com/adobe/aem-cif-guides-venia) is een referentiecode die als basis kan dienen voor [CIF Core-componenten](https://github.com/adobe/aem-core-cif-components). In deze zelfstudie breidt u de [Productteam](https://github.com/adobe/aem-core-cif-components/tree/master/ui.apps/src/main/content/jcr_root/apps/core/cif/components/commerce/productteaser/v1/productteaser) om een aangepast kenmerk van Adobe Commerce weer te geven. U leert ook meer over de GraphQL-integratie tussen AEM en Adobe Commerce en de extensiekoppels die door de CIF Core Components worden geleverd.

>[!TIP]
>
>Gebruik de [Project archetype AEM](https://github.com/adobe/aem-project-archetype) wanneer het beginnen van uw eigen handelsimplementatie.

## Wat u gaat maken

Het merk Venia is onlangs begonnen met de productie van bepaalde producten met behulp van duurzame materialen en het bedrijf wil graag een **Eco Friendly** badge als onderdeel van de Product Teaser. In Adobe Commerce wordt een nieuw aangepast kenmerk gemaakt om aan te geven of een product het **Milieuvriendelijk** materiaal. Dit douanekenmerk zal dan als deel van de vraag van GraphQL worden toegevoegd en op de Teaser van het Product voor gespecificeerde producten getoond.

![Eco-vriendelijke badge - definitieve implementatie](../assets/customize-cif-components/final-product-teaser-eco-badge.png)

## Vereisten {#prerequisites}

U hebt een lokale ontwikkelomgeving nodig om deze zelfstudie te voltooien. Dit omvat een lopende instantie van AEM die wordt gevormd en met een instantie van Adobe Commerce verbonden. De vereisten en stappen voor [een plaatselijke ontwikkeling opzetten met AEM](../develop.md). Als u de zelfstudie volledig wilt volgen, hebt u machtigingen nodig om toe te voegen [Kenmerken van een product](https://docs.magento.com/user-guide/catalog/product-attributes-add.html) in Adobe Commerce.

U hebt ook GraphQL IDE nodig, zoals [GraphiQL](https://github.com/graphql/graphiql) of een browserextensie om de codevoorbeelden en zelfstudies uit te voeren. Als u een browserextensie installeert, moet u ervoor zorgen dat deze de mogelijkheid heeft om aanvraagheaders in te stellen. In Google Chrome: [Altair GraphQL Client](https://chrome.google.com/webstore/detail/altair-graphql-client/flnheeellpciglgpaodhkhmapeljopja) is één extensie die de taak kan uitvoeren.

## Het Venia-project klonen {#clone-venia-project}

We klonen de [Venia-project](https://github.com/adobe/aem-cif-guides-venia) en overschrijf vervolgens de standaardstijlen.

>[!NOTE]
>
>**Voel u vrij om een bestaand project te gebruiken** (gebaseerd op het AEM Projectarchetype met CIF inbegrepen) en sla deze sectie over.

1. Voer de volgende git-opdracht uit om het project te klonen:

   ```shell
   $ git clone git@github.com:adobe/aem-cif-guides-venia.git
   ```

1. Bouw en stel het project aan een lokaal geval van AEM op:

   ```shell
   $ cd aem-cif-guides-venia/
   $ mvn clean install -PautoInstallSinglePackage,cloud
   ```

1. Voeg de noodzakelijke configuraties OSGi toe om uw AEM instantie met een instantie van Adobe Commerce te verbinden of de configuraties aan het onlangs gecreeerd project toe te voegen.

1. Op dit moment hebt u een werkende versie van een winkel die is verbonden met een Adobe Commerce-instantie. Ga naar de `US` > `Home` pagina bij: [http://localhost:4502/editor.html/content/venia/us/en.html](http://localhost:4502/editor.html/content/venia/us/en.html).

   Je moet zien dat de winkel het thema Venia gebruikt. Als u het hoofdmenu van de winkel uitbreidt, ziet u verschillende categorieën die aangeven dat de verbinding met Adobe Commerce werkt.

   ![Storefront geconfigureerd met Venia-thema](../assets/customize-cif-components/venia-store-configured.png)

## Auteur van de producttaser {#author-product-teaser}

De component Product Teaser wordt tijdens deze zelfstudie uitgebreid. Als eerste stap voegt u een nieuw exemplaar van de Product Teaser toe aan de startpagina om de basislijnfunctionaliteit te begrijpen.

1. Ga naar de **Startpagina** van het gebied: [http://localhost:4502/editor.html/content/acme/us/en.html](http://localhost:4502/editor.html/content/acme/us/en.html)

2. Een nieuwe invoegtoepassing **Productteam** Component in de hoofdlay-outcontainer op de pagina.

   ![Productteam invoegen](../assets/customize-cif-components/product-teaser-add-component.png)

3. Vouw het zijpaneel uit (indien nog niet in-/uitgeschakeld) en schakel het vervolgkeuzemenu voor het zoeken van elementen naar **Producten**. Dit zou een lijst van beschikbare producten van een verbonden instantie van Adobe Commerce moeten tonen. Selecteer een product en **slepen+neerzetten** het op **Productteam** op de pagina.

   ![Slepen en productteam neerzetten](../assets/customize-cif-components/drag-drop-product-teaser.png)

   >[!NOTE]
   >
   >Nota, kunt u het getoonde product ook vormen door de component te vormen gebruikend de dialoog (klikkend _moersleutel_ pictogram).

4. Er wordt nu een product weergegeven door de Product Teaser. De naam van het product en de prijs van het product zijn standaardkenmerken die worden weergegeven.

   ![Productteam - standaardstijl](../assets/customize-cif-components/product-teaser-default-style.png)

## Een aangepast kenmerk toevoegen in Adobe Commerce {#add-custom-attribute}

De in AEM weergegeven producten en productgegevens worden opgeslagen in Adobe Commerce. Voeg vervolgens een nieuw kenmerk toe voor **Eco Friendly** als onderdeel van het kenmerk product dat is ingesteld met de gebruikersinterface van Adobe Commerce.

>[!TIP]
>
>Hebt u al een aangepaste **Ja/Nee** kenmerk als onderdeel van de set productkenmerken? Voel u vrij om het te gebruiken en sla deze sectie over.

1. Meld u aan bij uw Adobe Commerce-exemplaar.
1. Navigeren naar **Catalogus** > **Producten**.
1. Werk het zoekfilter bij om de **Configureerbaar product** gebruikt wanneer toegevoegd aan de component Teaser in de vorige oefening. Open het product in de bewerkingsmodus.

   ![Zoeken naar Valeria-product](../assets/customize-cif-components/search-valeria-product.png)

1. Klik in de productweergave op **Kenmerk toevoegen** > **Nieuw kenmerk maken**.
1. Vul de **Nieuw kenmerk** formulier met de volgende waarden (standaardinstellingen voor andere waarden behouden)

   | Veldset | Veldlabel | Waarde |
   | ----------------------------- | ------------------ | ---------------- |
   | Eigenschappen van kenmerk | Kenmerklabel | **Eco Friendly** |
   | Eigenschappen van kenmerk | Invoertype catalogus | **Ja/Nee** |
   | Geavanceerde kenmerkeigenschappen | Kenmerkcode | **ecovriendelijk** |

   ![Nieuw kenmerkformulier](../assets/customize-cif-components/attribute-new-form.png)

   Klikken **Kenmerk opslaan** wanneer gereed.

1. Ga naar de onderkant van het product en vouw de **Attributen** kop. U moet de nieuwe **Eco Friendly** veld. Schakelen tussen **Ja**.

   ![Overschakelen op ja](../assets/customize-cif-components/eco-friendly-toggle-yes.png)

   **Opslaan** de veranderingen in het product.

   >[!TIP]
   >
   >Meer informatie over het beheren [Productkenmerken vindt u in de gebruikershandleiding van Adobe Commerce](https://docs.magento.com/user-guide/catalog/attribute-best-practices.html).

1. Navigeren naar **Systeem** > **Gereedschappen** > **Cachebeheer**. Aangezien een update aan het gegevensschema is gemaakt moeten wij sommige Types van Geheime voorgeheugen in Adobe Commerce ongeldig maken.
1. Schakel het selectievakje naast **Configuratie** en verzend het cachetype voor **Vernieuwen**

   ![Type configuratiecache vernieuwen](../assets/customize-cif-components/refresh-configuration-cache-type.png)

   >[!TIP]
   >
   >Meer informatie over [Cache Management vindt u in de Adobe Commerce-gebruikershandleiding](https://docs.magento.com/user-guide/system/cache-management.html).

## GraphQL IDE gebruiken om kenmerk te verifiëren {#use-graphql-ide}

Voordat u in AEM code gaat, is het handig om de [Adobe Commerce GraphQL](https://devdocs.magento.com/guides/v2.4/graphql/) een GraphQL-IDE gebruiken. De Adobe Commerce-integratie met AEM gebeurt voornamelijk via een reeks GraphQL-query&#39;s. Het begrip van en het wijzigen van de vragen van GraphQL is één van de belangrijkste manieren waarin de Componenten van de Kern CIF kunnen worden uitgebreid.

Gebruik vervolgens een GraphQL-IDE om te controleren of de `eco_friendly` kenmerk is toegevoegd aan de set productkenmerken. Screenshots in deze zelfstudie gebruiken de [Altair GraphQL Client](https://chrome.google.com/webstore/detail/altair-graphql-client/flnheeellpciglgpaodhkhmapeljopja).

1. GraphQL-IDE openen en URL invoeren `http://<server>/graphql` in de bar URL van uw winde of uitbreiding.
2. Voeg het volgende toe [productquery](https://devdocs.magento.com/guides/v2.4/graphql/queries/products.html) waar `YOUR_SKU` is de **SKU** van het product dat bij de vorige exercitie werd gebruikt:

   ```json
     {
       products(
       filter: { sku: { eq: "YOUR_SKU" } }
       ) {
           items {
           name
           sku
           eco_friendly
           }
       }
   }
   ```

3. Voer de vraag uit en u zou een reactie als het volgende moeten krijgen:

   ```json
   {
     "data": {
       "products": {
         "items": [
           {
             "name": "Valeria Two-Layer Tank",
             "sku": "VT11",
             "eco_friendly": 1
           }
         ]
       }
     }
   }
   ```

   ![Voorbeeld GraphQL-reactie](../assets/customize-cif-components/sample-graphql-query.png)

   De waarde van **Ja** is een geheel getal van **1**. Dit is handig wanneer we de GraphQL-query in Java schrijven.

   >[!TIP]
   >
   >Meer gedetailleerde documentatie over [Adobe Commerce GraphQL is hier te vinden](https://devdocs.magento.com/guides/v2.4/graphql/index.html).

## Het verkoopmodel voor de producttaser bijwerken {#updating-sling-model-product-teaser}

Daarna, zullen wij de bedrijfslogica van de Teaser van het Product uitbreiden door een het Verkopen Model uit te voeren. [Verkoopmodellen](https://sling.apache.org/documentation/bundles/models.html), zijn annotatiegestuurde &quot;POJO&#39;s&quot; (normale oude Java-objecten) die een van de bedrijfslogica implementeren die nodig is voor de component. Sling Models worden gebruikt in combinatie met de HTML-scripts als onderdeel van de component. We zullen de [delegatiepatroon voor verkoopmodellen](https://github.com/adobe/aem-core-wcm-components/wiki/Delegation-Pattern-for-Sling-Models) zodat we alleen onderdelen van het bestaande productassortiment kunnen uitbreiden.

Verkoopmodellen worden geïmplementeerd als Java en staan in het dialoogvenster **kern** module van het gegenereerde project.

Gebruiken [de IDE van uw keuze](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/development-tools.html?lang=en#set-up-the-development-ide) het Venia-project in te voeren. De gebruikte screenshots zijn afkomstig van de [Visual Studio Code IDE](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/development-tools.html?#microsoft-visual-studio-code).

1. In uw winde, navigeer onder **kern** module naar: `core/src/main/java/com/venia/core/models/commerce/MyProductTeaser.java`.

   ![Core location IDE](../assets/customize-cif-components/core-location-ide.png)

   `MyProductTeaser.java` is een interface van Java die CIF uitbreidt [ProductTeaser](https://github.com/adobe/aem-core-cif-components/blob/master/bundles/core/src/main/java/com/adobe/cq/commerce/core/components/models/productteaser/ProductTeaser.java) interface.

   Er is al een nieuwe methode toegevoegd met de naam `isShowBadge()` om een badge weer te geven als het product als &quot;Nieuw&quot; wordt beschouwd.

1. Voeg een nieuwe methode toe, `isEcoFriendly()` aan de interface:

   ```java
   @ProviderType
   public interface MyProductTeaser extends ProductTeaser {
       // Extend the existing interface with the additional properties which you
       // want to expose to the HTL template.
       public Boolean isShowBadge();
   
       public Boolean isEcoFriendly();
   }
   ```

   Dit is een nieuwe methode die we zullen introduceren om de logica in te kapselen om aan te geven of het product het `eco_friendly` kenmerk ingesteld op **Ja** of **Nee**.

1. Controleer vervolgens de `MyProductTeaserImpl.java` om `core/src/main/java/com/venia/core/models/commerce/MyProductTeaserImpl.java`.

   De [delegatiepatroon voor verkoopmodellen](https://github.com/adobe/aem-core-wcm-components/wiki/Delegation-Pattern-for-Sling-Models) toestaat `MyProductTeaserImpl` verwijzing `ProductTeaser` model via de `sling:resourceSuperType` eigenschap:

   ```java
   @Self
   @Via(type = ResourceSuperType.class)
   private ProductTeaser productTeaser;
   ```

   Voor alle methodes die wij niet willen met voeten treden of veranderen, kunnen wij eenvoudig de waarde terugkeren die `ProductTeaser` retourneert. Bijvoorbeeld:

   ```java
   @Override
   public String getImage() {
       return productTeaser.getImage();
   }
   ```

   Hierdoor minimaliseert u de hoeveelheid Java-code die een implementatie moet schrijven.

1. Een van de extra extensiepunten die door AEM CIF Core Components wordt geboden, is de `AbstractProductRetriever` die toegang biedt tot specifieke productkenmerken. Inspect the `initModel()` methode:

   ```java
   import javax.annotation.PostConstruct;
   ...
   @Model(adaptables = SlingHttpServletRequest.class, adapters = MyProductTeaser.class, resourceType = MyProductTeaserImpl.RESOURCE_TYPE)
   public class MyProductTeaserImpl implements MyProductTeaser {
       ...
       private AbstractProductRetriever productRetriever;
   
       /* add this method to intialize the proudctRetriever */
       @PostConstruct
       public void initModel() {
           productRetriever = productTeaser.getProductRetriever();
   
           if (productRetriever != null) {
               productRetriever.extendProductQueryWith(p -> p.createdAt());
           }
   
       }
   ...
   ```

   De `@PostConstruct` De aantekening zorgt ervoor dat deze methode wordt geroepen zodra het het Verdelen Model wordt geïnitialiseerd.

   De productvraag van GraphQL is al uitgebreid via de `extendProductQueryWith` methode om de extra `created_at` kenmerk. Dit kenmerk wordt later gebruikt als onderdeel van het dialoogvenster `isShowBadge()` methode.

1. Werk de GraphQL-query bij en voeg de `eco_friendly` kenmerk in de gedeeltelijke query:

   ```java
   //MyProductTeaserImpl.java
   
   private static final String ECO_FRIENDLY_ATTRIBUTE = "eco_friendly";
   
   @PostConstruct
   public void initModel() {
       productRetriever = productTeaser.getProductRetriever();
   
       if (productRetriever != null) {
           productRetriever.extendProductQueryWith(p -> p
               .createdAt()
               .addCustomSimpleField(ECO_FRIENDLY_ATTRIBUTE)
           );
       }
   }
   ```

   Toevoegen aan de `extendProductQueryWith` deze methode is een krachtige manier om ervoor te zorgen dat aanvullende productkenmerken beschikbaar zijn voor de rest van het model. Het minimaliseert ook het aantal uitgevoerde vragen.

   In de bovenstaande code wordt`addCustomSimpleField` wordt gebruikt om de `eco_friendly` kenmerk. Dit illustreert hoe u kunt zoeken naar aangepaste kenmerken die deel uitmaken van het Adobe Commerce-schema.

   >[!NOTE]
   >
   >De `createdAt()` de methode is daadwerkelijk uitgevoerd als onderdeel van de [Productinterface](https://github.com/adobe/commerce-cif-magento-graphql/blob/master/src/main/java/com/adobe/cq/commerce/magento/graphql/ProductInterface.java). De meeste algemeen gevonden schemakenmerken zijn uitgevoerd, zo slechts gebruik `addCustomSimpleField` voor werkelijk aangepaste kenmerken.

1. Voeg een registreerapparaat toe voor foutopsporing in de Java-code:

   ```java
   import org.slf4j.Logger;
   import org.slf4j.LoggerFactory;
   ...
   @Model(adaptables = SlingHttpServletRequest.class, adapters = MyProductTeaser.class, resourceType = MyProductTeaserImpl.RESOURCE_TYPE)
   public class MyProductTeaserImpl implements MyProductTeaser {
   
   private static final Logger LOGGER = LoggerFactory.getLogger(MyProductTeaserImpl.class);
   ```

1. Voer vervolgens de `isEcoFriendly()` methode:

   ```java
   @Override
   public Boolean isEcoFriendly() {
   
       Integer ecoFriendlyValue;
       try {
           ecoFriendlyValue = productRetriever.fetchProduct().getAsInteger(ECO_FRIENDLY_ATTRIBUTE);
           if(ecoFriendlyValue != null && ecoFriendlyValue.equals(Integer.valueOf(1))) {
               LOGGER.info("*** Product is Eco Friendly**");
               return true;
           }
       } catch (SchemaViolationError e) {
           LOGGER.error("Error retrieving eco friendly attribute");
       }
       LOGGER.info("*** Product is not Eco Friendly**");
       return false;
   }
   ```

   In de bovenstaande methode wordt `productRetriever` wordt gebruikt om het product en de `getAsInteger()` wordt gebruikt om de waarde van `eco_friendly` kenmerk. Op basis van de GraphQL query&#39;s die we eerder hebben uitgevoerd, weten we dat de verwachte waarde `eco_friendly` kenmerk is ingesteld op &quot;**Ja**&quot; is eigenlijk een geheel getal van **1**.

   Nu het Sling Model is bijgewerkt, moet de prijsverhoging van de Component worden bijgewerkt om daadwerkelijk een indicator van te tonen van **Eco Friendly** op basis van het verkoopmodel.

## De opmaak van de producttaser aanpassen {#customize-markup-product-teaser}

Een algemene uitbreiding van AEM componenten is het wijzigen van de markering die door de component wordt gegenereerd. Dit wordt gedaan door met voeten te treden [HTML-script](https://experienceleague.adobe.com/docs/experience-manager-htl/content/overview.html) dat de component gebruikt om zijn prijsverhoging terug te geven. De Taal van het Malplaatje van de HTML (HTL), is een lichtgewichtmalplaatjetaal die AEM componenten gebruiken om prijsverhoging dynamisch terug te geven die op authored inhoud wordt gebaseerd, toestaand de componenten om worden opnieuw gebruikt. De producttaser kan bijvoorbeeld steeds opnieuw worden gebruikt om verschillende producten weer te geven.

In ons geval willen we een banner boven op het gummetje weergeven om aan te geven dat het product &quot;Eco Friendly&quot; is op basis van een aangepast kenmerk. Het ontwerppatroon voor [de markering aanpassen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/customizing.html#customizing-the-markup) van een component is in feite standaard voor alle AEM componenten, niet alleen voor de AEM CIF Core-componenten.

>[!NOTE]
>
>Als u een component aanpast met gebruik van de CIF product &amp; categoriekiezers zoals deze Teaser van het Product of de CIF paginacomponent zorg ervoor u de vereiste omvat `cif.shell.picker` clientlib voor de componentdialoogvensters. Zie [Gebruik van CIF-product en rubriekkiezer](use-cif-pickers.md) voor meer informatie.

1. In winde, navigeer en breid uit `ui.apps` en breid de maphiërarchie uit naar: `ui.apps/src/main/content/jcr_root/apps/venia/components/commerce/productteaser` en inspecteer de `.content.xml` bestand.

   ![Productieteams ui.apps](../assets/customize-cif-components/product-teaser-ui-apps-ide.png)

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0" xmlns:cq="https://www.day.com/jcr/cq/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0"
       jcr:description="Product Teaser Component"
       jcr:primaryType="cq:Component"
       jcr:title="Product Teaser"
       sling:resourceSuperType="core/cif/components/commerce/productteaser/v1/productteaser"
       componentGroup="Venia - Commerce"/>
   ```

   Hierboven vindt u de componentdefinitie voor de component Product Teaser in ons project. Let op de eigenschap `sling:resourceSuperType="core/cif/components/commerce/productteaser/v1/productteaser"`. Dit is een voorbeeld van het maken van een [Proxycomponent](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/get-started/using.html#create-proxy-components). In plaats van alle HTML-scripts van de Product Teaser te kopiëren en te plakken van de AEM CIF Core Components, kunnen we de `sling:resourceSuperType` om alle functionaliteit over te nemen.

1. Het bestand openen `productteaser.html`. Dit is een kopie van het `productteaser.html` bestand van de [CIF Product Teaser](https://github.com/adobe/aem-core-cif-components/blob/master/ui.apps/src/main/content/jcr_root/apps/core/cif/components/commerce/productteaser/v1/productteaser/productteaser.html)

   ```html
   <!--/* productteaser.html */-->
   <sly
     data-sly-use.product="com.venia.core.models.commerce.MyProductTeaser"
     data-sly-use.templates="core/wcm/components/commons/v1/templates.html"
     data-sly-use.actionsTpl="actions.html"
     data-sly-test.isConfigured="${properties.selection}"
     data-sly-test.hasProduct="${product.url}"
   ></sly>
   ```

   Let op: het verkoopmodel voor `MyProductTeaser` wordt gebruikt en toegewezen aan `product` variabele.

1. Wijzigen `productteaser.html` om een oproep te doen aan de `isEcoFriendly` in de vorige exercitie toegepaste methode:

   ```html
   ...
   <div
     data-sly-test="${isConfigured && hasProduct}"
     class="item__root"
     data-cmp-is="productteaser"
     data-virtual="${product.virtualProduct}"
   >
     <div data-sly-test="${product.showBadge}" class="item__badge">
       <span>${properties.text || 'New'}</span>
     </div>
     <!--/* Insert call to Eco Friendly here */-->
     <div data-sly-test="${product.ecoFriendly}" class="item__eco">
       <span>Eco Friendly</span>
     </div>
     ...
   </div>
   ```

   Bij het aanroepen van een Sling Model-methode in HTML wordt de `get` en `is` Het gedeelte van de methode wordt verwijderd en de eerste letter wordt ingekort. Dus `isShowBadge()` wordt `.showBadge` en `isEcoFriendly` wordt `.ecoFriendly`. Gebaseerd op de booleaanse waarde die is geretourneerd van `.isEcoFriendly()` bepaalt of de `<span>Eco Friendly</span>` wordt weergegeven.

   Meer informatie over `data-sly-test` en andere [HTML-blokinstructies vindt u hier](https://experienceleague.adobe.com/docs/experience-manager-htl/content/specification.html).

1. Sparen de veranderingen en stel de updates in om het gebruiken van uw Maven vaardigheden, van een terminal van de bevellijn te AEM:

   ```shell
   $ cd aem-cif-guides-venia/
   $ mvn clean install -PautoInstallSinglePackage,cloud
   ```

1. Open een nieuw browservenster en navigeer naar AEM **OSGi-console** > **Status** > **Verkoopmodellen**: [http://localhost:4502/system/console/status-slingmodels](http://localhost:4502/system/console/status-slingmodels)

1. Zoeken naar `MyProductTeaserImpl` en u zou een lijn als het volgende moeten zien:

   ```plain
   com.venia.core.models.commerce.MyProductTeaserImpl - venia/components/commerce/productteaser
   ```

   Dit wijst erop dat het het Verdelen Model behoorlijk is opgesteld en aan de correcte component in kaart gebracht.

1. Vernieuwen naar de **Introductiepagina van Venia** om [http://localhost:4502/editor.html/content/venia/us/en.html](http://localhost:4502/editor.html/content/venia/us/en.html) waarbij de producttaser is toegevoegd.

   ![Eco Friendly message displayed](../assets/customize-cif-components/eco-friendly-text-displayed.png)

   Als het product de `eco_friendly` kenmerk ingesteld op **Ja**, moet u de tekst &quot;Eco Friendly&quot; op de pagina zien. Probeer over te schakelen op verschillende producten om de gedragswijziging te zien.

1. De AEM openen `error.log` om de logboekverklaringen te zien wij toevoegden. De `error.log` bevindt zich op `<AEM SDK Install Location>/crx-quickstart/logs/error.log`.

   Zoek in de AEM logboeken naar de logboekinstructies die in het Sling-model zijn toegevoegd:

   ```plain
   2020-08-28 12:57:03.114 INFO [com.venia.core.models.commerce.MyProductTeaserImpl] *** Product is Eco Friendly**
   ...
   2020-08-28 13:01:00.271 INFO [com.venia.core.models.commerce.MyProductTeaserImpl] *** Product is not Eco Friendly**
   ...
   ```

   >[!CAUTION]
   >
   >Het kan ook voorkomen dat er enkele stapelsporen worden weergegeven als het in de teaser gebruikte product niet de `eco_friendly` kenmerk als onderdeel van de kenmerkenset van het object.

## Stijlen toevoegen voor de milieuvriendelijke badge {#add-styles}

Op dit punt is de logica voor wanneer de **Eco Friendly** badge werkt al, maar de onbewerkte tekst kan enkele stijlen gebruiken. Voeg vervolgens een pictogram en stijlen toe aan het dialoogvenster `ui.frontend` om de implementatie te voltooien.

1. Download de [eco_Vriendelijk.svg](../assets/customize-cif-components/eco_friendly.svg) bestand. Dit wordt gebruikt als de **Eco Friendly** badge.
1. Terugkeer aan winde en navigeer aan winde `ui.frontend` map.
1. Voeg de `eco_friendly.svg` aan de `ui.frontend/src/main/resources/images` map:

   ![Eco Friendly SVG toegevoegd](../assets/customize-cif-components/eco-friendly-svg-added.png)

1. Het bestand openen `productteaser.scss` om `ui.frontend/src/main/styles/commerce/_productteaser.scss`.
1. Voeg de volgende regels van de Klasse binnen toe `.productteaser` klasse:

   ```scss
   .productteaser {
       ...
       .item__eco {
           width: 60px;
           height: 60px;
           left: 0px;
           overflow: hidden;
           position: absolute;
           padding: 5px;
   
       span {
           display: block;
           position: absolute;
           width: 45px;
           height: 45px;
           text-indent: -9999px;
           background: no-repeat center center url('../resources/images/eco_friendly.svg');
           }
       }
   ...
   }
   ```

   >[!NOTE]
   >
   >Uitchecken [Stijlvolle CIF Core-componenten](./style-cif-component.md) voor meer informatie over front-end workflows.

1. Sparen de veranderingen en stel de updates in om het gebruiken van uw Maven vaardigheden, van een terminal van de bevellijn te AEM:

   ```shell
   $ cd aem-cif-guides-venia/
   $ mvn clean install -PautoInstallSinglePackage,cloud
   ```

1. Vernieuwen naar de **Introductiepagina van Venia** om [http://localhost:4502/editor.html/content/venia/us/en.html](http://localhost:4502/editor.html/content/venia/us/en.html) waarbij de producttaser is toegevoegd.

   ![Eco-vriendelijke badge - definitieve implementatie](../assets/customize-cif-components/final-product-teaser-eco-badge.png)

## Gefeliciteerd {#congratulations}

U hebt zojuist uw eerste AEM CIF-component aangepast! Download de [hier voltooide oplossingsbestanden](../assets/customize-cif-components/customize-cif-component-SOLUTION_FILES.zip).

## Bonus Challenge {#bonus-challenge}

Controleer de functionaliteit van de **Nieuw** badge die al is geïmplementeerd in de Product Teaser. Probeer een extra selectievakje voor auteurs toe te voegen om te bepalen wanneer de **Eco Friendly** badge moet worden weergegeven. U moet het dialoogvenster voor componenten bijwerken op `ui.apps/src/main/content/jcr_root/apps/venia/components/commerce/productteaser/_cq_dialog/.content.xml`.

![Nieuwe uitdaging voor Badge-implementatie](../assets/customize-cif-components/new-badge-implementation-challenge.png)

## Aanvullende bronnen {#additional-resources}

- [AEM Archetype](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html)
- [AEM CIF Core-componenten](https://github.com/adobe/aem-core-cif-components)
- [Aanpassen AEM CIF Core-componenten](https://github.com/adobe/aem-core-cif-components/wiki/Customizing-CIF-Core-Components)
- [Kerncomponenten aanpassen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/customizing.html)
- [Aan de slag met AEM Sites](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html)
- [Gebruik van CIF-product en rubriekkiezer](use-cif-pickers.md)
