---
title: CIF kerncomponenten aanpassen
description: Leer hoe u Adobe Experience Manager CIF Core Components (Onderdelen van) kunt aanpassen. In de zelfstudie wordt uitgelegd hoe u een CIF Core-component veilig kunt uitbreiden om aan bedrijfsspecifieke vereisten te voldoen. Leer hoe u een GraphQL-query kunt uitbreiden om een aangepast kenmerk te retourneren en het nieuwe kenmerk in een CIF Core-component weer te geven.
exl-id: 8933942e-be49-49d3-bf0a-7225257e2803
feature: Commerce Integration Framework
solution: Experience Manager,Commerce
role: Admin, Developer
source-git-commit: ddd411a5dde57cf66cbcb458578b0aa32139b649
workflow-type: tm+mt
source-wordcount: '2302'
ht-degree: 0%

---

# Adobe Experience Manager CIF Core-componenten aanpassen {#customize-cif-components}

Het [ CIF Project van Venia ](https://github.com/adobe/aem-cif-guides-venia) is een basis van de verwijzingscode voor het gebruiken van [ CIF de Componenten van de Kern ](https://github.com/adobe/aem-core-cif-components). In dit leerprogramma, breidt u verder de ](https://github.com/adobe/aem-core-cif-components/tree/master/ui.apps/src/main/content/jcr_root/apps/core/cif/components/commerce/productteaser/v1/productteaser) component van Teaser van het 0} Product uit om een douanekenmerk van Adobe Commerce te tonen. [ U leert ook meer over de GraphQL-integratie tussen Adobe Experience Manager (AEM) en Adobe Commerce en de uitbreidingshaken die worden geleverd door de CIF Core Components.

>[!TIP]
>
>Gebruik [ AEM archetype van het Project ](https://github.com/adobe/aem-project-archetype) wanneer het beginnen van uw eigen handelsimplementatie.

## Wat u gaat maken

Het merk van Venia begon onlangs met de productie van sommige producten die duurzame materialen gebruiken en de zaken zouden een **Eco Friendly** badge als deel van de Teaser van het Product willen tonen. Een nieuw douaneattribuut wordt gecreeerd in Adobe Commerce om erop te wijzen als een product het **vriendschappelijke** materiaal gebruikt. Dit douanekenmerk wordt toegevoegd als deel van de vraag van GraphQL en getoond op de Teaser van het Product voor gespecificeerde producten.

![ Eco Friendly de Definitieve Implementatie van de Band ](../assets/customize-cif-components/final-product-teaser-eco-badge.png)

## Vereisten {#prerequisites}

U hebt een lokale ontwikkelomgeving nodig om deze zelfstudie te voltooien. Dit omvat een lopende instantie van AEM die wordt gevormd en met een instantie van Adobe Commerce verbonden. Herzie de vereisten en de stappen voor [ vestiging een lokale ontwikkeling met AEM ](../develop.md). Om het leerprogramma volledig te volgen, hebt u toestemming nodig om [ Attributen aan een Product ](https://docs.magento.com/user-guide/catalog/product-attributes-add.html) in Adobe Commerce toe te voegen.

U hebt ook winde van GraphQL zoals [ GraphiQL ](https://github.com/graphql/graphiql) of een browser uitbreiding nodig om de codesteekproeven en leerprogramma&#39;s in werking te stellen. Als u een browserextensie installeert, moet u de aanvraagheaders kunnen instellen. Op Google Chrome, _de Cliënt van GraphQL van Altair_ is één uitbreiding die de baan kan doen.

## Het Venia-project klonen {#clone-venia-project}

U kloont het [ Project van Venia ](https://github.com/adobe/aem-cif-guides-venia) en treedt dan de standaardstijlen met voeten.

>[!NOTE]
>
>**voelt vrij om een bestaand project** (gebaseerd op het AEM Archieftype van Project met inbegrepen CIF) te gebruiken en deze sectie over te slaan.

1. Voer de volgende git-opdracht uit, zodat u het project kunt klonen:

   ```shell
   $ git clone git@github.com:adobe/aem-cif-guides-venia.git
   ```

1. Bouw en stel het project aan een lokaal geval van AEM op:

   ```shell
   $ cd aem-cif-guides-venia/
   $ mvn clean install -PautoInstallSinglePackage -Pclassic
   ```

1. Voeg de noodzakelijke configuraties OSGi toe zodat kunt u uw AEM instantie met een instantie van Adobe Commerce verbinden of de configuraties toevoegen aan het onlangs gecreeerd project.

1. Op dit moment hebt u een werkende versie van een winkel die is verbonden met een Adobe Commerce-instantie. Navigeer aan `US` > `Home` pagina bij: [ http://localhost:4502/editor.html/content/venia/us/en.html ](http://localhost:4502/editor.html/content/venia/us/en.html).

   Je moet zien dat de winkel het Venia-thema gebruikt. Als u het hoofdmenu van de winkel uitbreidt, ziet u verschillende categorieën die aangeven dat de verbinding met Adobe Commerce werkt.

   ![ Storefront die met het Thema van Venia wordt gevormd ](../assets/customize-cif-components/venia-store-configured.png)

## Auteur van de producttaser {#author-product-teaser}

De component Product Teaser wordt tijdens deze zelfstudie uitgebreid. Als eerste stap voegt u een exemplaar van de Product Teaser toe aan de startpagina om de basislijnfunctionaliteit te begrijpen.

1. Navigeer aan de **Pagina van het Huis** van de plaats: [ http://localhost:4502/editor.html/content/acme/us/en.html ](http://localhost:4502/editor.html/content/acme/us/en.html)

2. Tussenvoegsel een nieuwe **Component van het Teaser van het 0} Product in de belangrijkste lay-outcontainer op de pagina.**

   ![ Taser van het Product van het Tussenvoegsel ](../assets/customize-cif-components/product-teaser-add-component.png)

3. Breid het Zijpaneel (als niet reeds) van een knevel voorzien en schakelaar de activa finder dropdown aan **Producten**. Dit zou een lijst van beschikbare producten van een verbonden instantie van Adobe Commerce moeten tonen. Selecteer een product en **belemmering+drop** het op de **component van de Taser van het Product** op de pagina.

   ![ Belemmering + Taser van het Product van de Daling ](../assets/customize-cif-components/drag-drop-product-teaser.png)

   >[!NOTE]
   >
   >Nota, kunt u het getoonde product ook vormen door de component te vormen gebruikend de dialoog (klikkend het _moersleutel_ pictogram).

4. Er wordt nu een product weergegeven door de Product Teaser. De naam van het product en de prijs van het product zijn standaardkenmerken die worden weergegeven.

   ![ Teaser van het Product - standaardstijl ](../assets/customize-cif-components/product-teaser-default-style.png)

## Een aangepast kenmerk toevoegen in Adobe Commerce {#add-custom-attribute}

De in AEM weergegeven producten en productgegevens worden opgeslagen in Adobe Commerce. Daarna, voeg een attribuut voor **vriendschappelijk Eco** als deel van de productattributen toe die door Adobe Commerce UI worden geplaatst te gebruiken.

>[!TIP]
>
>Hebt reeds een douane **ja/Neen** attribuut als deel van uw reeks van productattributen? Voel u vrij om het te gebruiken en sla deze sectie over.

1. Meld u aan bij uw Adobe Commerce-exemplaar.
1. Navigeer aan **Catalogus** > **Producten**.
1. Werk het onderzoeksfilter bij zodat kunt u het **Configurable Product** vinden dat wanneer toegevoegd aan de component van het Teaser in de vorige oefening wordt gebruikt. Open het product in de bewerkingsmodus.

   ![ Onderzoek naar Product Valeria ](../assets/customize-cif-components/search-valeria-product.png)

1. Van de productmening, klik **toevoegen Attribuut** > **Nieuw Attribuut** creëren.
1. Vul de **Nieuwe vorm van Attributen** met de volgende waarden (verlaten standaardmontages voor andere waarden) uit

   | Veldset | Veldlabel | Waarde |
   | ----------------------------- | ------------------ | ---------------- |
   | Eigenschappen van kenmerk | Kenmerklabel | **Milieuvriendelijk** |
   | Eigenschappen van kenmerk | Invoertype catalogus | **ja/Neen** |
   | Geavanceerde kenmerkeigenschappen | Kenmerkcode | **eco_Vriendelijk** |

   ![ Nieuwe vorm van Attributen ](../assets/customize-cif-components/attribute-new-form.png)

   Klik **sparen Attribuut** wanneer gebeëindigd.

1. De rol aan de bodem van het product en breidt de **rubriek van Attributen** uit. U zou het nieuwe **Eco Friendly** gebied moeten zien. Schakelaar de knevel aan **ja**.

   ![ knevel van de Schakelaar aan ja ](../assets/customize-cif-components/eco-friendly-toggle-yes.png)

   **sparen** de veranderingen in het product.

   >[!TIP]
   >
   >Meer details over het beheren van [ Attributen van het Product kunnen in de gebruikersgids van Adobe Commerce ](https://docs.magento.com/user-guide/catalog/attribute-best-practices.html) worden gevonden.

1. Navigeer aan **Systeem** > **Hulpmiddelen** > **het Beheer van het Geheime voorgeheugen**. Omdat het gegevensschema is bijgewerkt, moet u enkele soorten cache in Adobe Commerce ongeldig maken.
1. Controle de doos naast **Configuratie** en voorlegt het geheim voorgeheugentype voor **verfrissen**

   ![ verfrist het Type van Geheime voorgeheugen van de Configuratie ](../assets/customize-cif-components/refresh-configuration-cache-type.png)

   >[!TIP]
   >
   >Meer details over [ het Beheer van het Geheime voorgeheugen kunnen in de de gebruikersgids van Adobe Commerce ](https://docs.magento.com/user-guide/system/cache-management.html) worden gevonden.

## GraphQL IDE gebruiken om kenmerk te verifiëren {#use-graphql-ide}

Alvorens in AEM code te springen, is het nuttig om [ Adobe Commerce GraphQL ](https://devdocs.magento.com/guides/v2.4/graphql/) te onderzoeken gebruikend GraphQL winde. De Adobe Commerce-integratie met AEM gebeurt voornamelijk via een reeks GraphQL-query&#39;s. Het begrijpen en wijzigen van de vragen van GraphQL is één van de belangrijkste manieren waarop de Componenten van de CIFKern kunnen worden uitgebreid.

Gebruik vervolgens een GraphQL IDE om te controleren of het kenmerk `eco_friendly` is toegevoegd aan de set met productkenmerken. De beelden van het scherm in dit leerprogramma gebruiken de uitbreiding van Google Chrome _de Cliënt van GraphQL van Altair_.

1. Open GraphQL IDE en ga URL `http://<server>/graphql` in de bar URL van uw winde of uitbreiding in.
2. Voeg de volgende [ productvraag ](https://devdocs.magento.com/guides/v2.4/graphql/queries/products.html) toe waar `YOUR_SKU` **SKU** van het product is dat in de vorige oefening wordt gebruikt:

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

   ![ de reactie van GraphQL van de Steekproef ](../assets/customize-cif-components/sample-graphql-query.png)

De waarde van **ja** is een geheel van **1**. Dit is handig wanneer u de GraphQL-query in Java™ schrijft.

>[!TIP]
>
>Meer gedetailleerde documentatie over [ Adobe Commerce GraphQL kan hier ](https://devdocs.magento.com/guides/v2.4/graphql/index.html) worden gevonden.

## Het verkoopmodel voor de producttaser bijwerken {#updating-sling-model-product-teaser}

Daarna, breidt u de bedrijfslogica van de Teaser van het Product door een het Verkopen Model uit te voeren uit. [ het Verdelen Modellen ](https://sling.apache.org/documentation/bundles/models.html) zijn annotatie gedreven &quot;POJOs&quot;(Duidelijk Oude Voorwerpen Java™) die om het even welke bedrijfslogica uitvoeren die door de component nodig is. Sling Models worden gebruikt met de manuscripten HTML als deel van de component. Volg het [ delegatiepatroon voor het Verdelen Modellen ](https://github.com/adobe/aem-core-wcm-components/wiki/Delegation-Pattern-for-Sling-Models) zodat u delen van het bestaande model van de Teaser van het Product kunt uitbreiden.

Het verkopen Modellen wordt uitgevoerd als Java™ en kan in de **kern** module van het geproduceerde project worden gevonden.

Gebruik [ winde van uw keus ](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/development-tools.html#set-up-the-development-ide) om het project van Venia in te voeren. De gebruikte schermafbeeldingen zijn van [ winde van de Code van Visual Studio ](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/development-tools.html?#microsoft-visual-studio-code).

1. In uw winde, navigeer onder de **kern** module aan: `core/src/main/java/com/venia/core/models/commerce/MyProductTeaser.java`.

   {IDE van de plaatsIDE van 0} Kern ](../assets/customize-cif-components/core-location-ide.png)![

   `MyProductTeaser.java` is een Interface Java™ die de CIF [ ProductTeaser ](https://github.com/adobe/aem-core-cif-components/blob/master/bundles/core/src/main/java/com/adobe/cq/commerce/core/components/models/productteaser/ProductTeaser.java) interface uitbreidt.

   Er is al een nieuwe methode met de naam `isShowBadge()` toegevoegd om een badge weer te geven als het product als &quot;Nieuw&quot; wordt beschouwd.

1. Voeg een methode `isEcoFriendly()` aan de interface toe:

   ```java
   @ProviderType
   public interface MyProductTeaser extends ProductTeaser {
       // Extend the existing interface with the additional properties which you
       // want to expose to the HTL template.
       public Boolean isShowBadge();
   
       public Boolean isEcoFriendly();
   }
   ```

Dit is een nieuwe methode om de logica in te kapselen om erop te wijzen als het product de `eco_friendly` attributen heeft die aan **worden geplaatst ja** of **Nr**.

1. Controleer vervolgens de `MyProductTeaserImpl.java` at `core/src/main/java/com/venia/core/models/commerce/MyProductTeaserImpl.java` .

   Het [ delegatiepatroon voor het Verdelen Modellen ](https://github.com/adobe/aem-core-wcm-components/wiki/Delegation-Pattern-for-Sling-Models) staat `MyProductTeaserImpl` toe om `ProductTeaser` model via het `sling:resourceSuperType` bezit van verwijzingen te voorzien:

   ```java
   @Self
   @Via(type = ResourceSuperType.class)
   private ProductTeaser productTeaser;
   ```

   Voor alle methoden die niet worden overschreven of gewijzigd, kunt u de waarde retourneren die de `ProductTeaser` retourneert. Bijvoorbeeld:

   ```java
   @Override
   public String getImage() {
       return productTeaser.getImage();
   }
   ```

   Dit minimaliseert de hoeveelheid code Java™ die een implementatie moet schrijven.

1. Een van de extra extensiepunten die AEM Core Components biedt, is de `AbstractProductRetriever` die toegang biedt tot specifieke productkenmerken. Inspect de methode `initModel()` :

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

   De `@PostConstruct` -annotatie zorgt ervoor dat deze methode wordt aangeroepen wanneer het Sling-model wordt geïnitialiseerd.

   De product-GraphQL-query is al uitgebreid met de methode `extendProductQueryWith` om het extra `created_at` -kenmerk op te halen. Dit kenmerk wordt later gebruikt als onderdeel van de methode `isShowBadge()` .

1. Werk de GraphQL-query bij om het kenmerk `eco_friendly` op te nemen in de gedeeltelijke query:

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

   Toevoegen aan de methode `extendProductQueryWith` is een krachtige manier om ervoor te zorgen dat extra productkenmerken beschikbaar zijn voor de rest van het model. Het minimaliseert ook het aantal uitgevoerde vragen.

   In de bovenstaande code, wordt `addCustomSimpleField` gebruikt om het `eco_friendly` attribuut terug te winnen. Dit illustreert hoe u kunt zoeken naar aangepaste kenmerken die deel uitmaken van het Adobe Commerce-schema.

   >[!NOTE]
   >
   >De `createdAt()` methode is uitgevoerd als deel van de [ Interface van het Product ](https://github.com/adobe/commerce-cif-magento-graphql/blob/master/src/main/java/com/adobe/cq/commerce/magento/graphql/ProductInterface.java). De meeste algemeen gevonden schemakenmerken zijn uitgevoerd, zodat gebruik slechts `addCustomSimpleField` voor echt douanekenmerken.

1. Voeg een logger toe zodat u hiermee fouten in de Java™-code kunt opsporen:

   ```java
   import org.slf4j.Logger;
   import org.slf4j.LoggerFactory;
   ...
   @Model(adaptables = SlingHttpServletRequest.class, adapters = MyProductTeaser.class, resourceType = MyProductTeaserImpl.RESOURCE_TYPE)
   public class MyProductTeaserImpl implements MyProductTeaser {
   
   private static final Logger LOGGER = LoggerFactory.getLogger(MyProductTeaserImpl.class);
   ```

1. Implementeer vervolgens de methode `isEcoFriendly()` :

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

   In de bovenstaande methode wordt `productRetriever` gebruikt om het product op te halen en wordt de methode `getAsInteger()` gebruikt om de waarde van het kenmerk `eco_friendly` op te halen. Gebaseerd op de vragen van GraphQL u vroeger in werking stelde, weet u dat de verwachte waarde wanneer het `eco_friendly` attribuut aan &quot;**ja**&quot;wordt geplaatst eigenlijk een geheel van **1** is.

   Nu het het Verdelen Model wordt bijgewerkt, werk de prijsverhoging van de Component bij om een indicator van **Eco Friendly** te tonen die op het het Verdelen Model wordt gebaseerd.

## De opmaak van de producttaser aanpassen {#customize-markup-product-teaser}

Een algemene uitbreiding van AEM componenten is het wijzigen van de markering die door de component wordt gegenereerd. Dit wordt gedaan door het [ manuscript van HTML ](https://experienceleague.adobe.com/docs/experience-manager-htl/content/overview.html) met voeten te treden dat de component gebruikt om zijn prijsverhoging terug te geven. De Taal van het Malplaatje van de HTML (HTL), is een lichtgewichtmalplaatjetaal die AEM componenten gebruiken om prijsverhoging dynamisch terug te geven die op authored inhoud wordt gebaseerd, toestaand de componenten om worden opnieuw gebruikt. De producttaser kan bijvoorbeeld steeds opnieuw worden gebruikt om verschillende producten weer te geven.

In dit geval, wilt u een banner op de teaser teruggeven om erop te wijzen dat het product &quot;Milieuvriendelijk&quot;gebaseerd op een douaneattribuut is. Het ontwerppatroon voor [ die de prijsverhoging ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/customizing.html#customizing-the-markup) van een component aanpassen is standaard voor alle AEM Componenten, niet alleen voor de AEM Componenten van de Kern CIF.

>[!NOTE]
>
>Als u een component aanpast met de CIF product- en categoriekiezers zoals deze productcode of de CIF paginacomponent, moet u de vereiste `cif.shell.picker` clientlib voor de deeldialoogvensters opnemen. Zie [ Gebruik van CIF product &amp; categoriekiezer ](use-cif-pickers.md) voor details.

1. Navigeer in de IDE naar de module `ui.apps` en vouw de maphiërarchie uit naar: `ui.apps/src/main/content/jcr_root/apps/venia/components/commerce/productteaser` en inspecteer het bestand `.content.xml` .

   ![ de Teaser ui.apps van het Product Taser ](../assets/customize-cif-components/product-teaser-ui-apps-ide.png)

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0" xmlns:cq="https://www.day.com/jcr/cq/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0"
       jcr:description="Product Teaser Component"
       jcr:primaryType="cq:Component"
       jcr:title="Product Teaser"
       sling:resourceSuperType="core/cif/components/commerce/productteaser/v1/productteaser"
       componentGroup="Venia - Commerce"/>
   ```

   De componentdefinitie voor de Product Teaser Component in dit project is hierboven. Let op de eigenschap `sling:resourceSuperType="core/cif/components/commerce/productteaser/v1/productteaser"` . Dit is een voorbeeld van het creëren van de component van de Volmacht van de a [ ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/get-started/using.html#create-proxy-components). In plaats van alle HTML-scripts van de Product Teaser te kopiëren en te plakken van de AEM CIF Core Components, kunt u de `sling:resourceSuperType` gebruiken om alle functionaliteit over te nemen.

1. Open het bestand `productteaser.html` . Dit is een exemplaar van het `productteaser.html` dossier van de [ CIF Taser van het Product ](https://github.com/adobe/aem-core-cif-components/blob/master/ui.apps/src/main/content/jcr_root/apps/core/cif/components/commerce/productteaser/v1/productteaser/productteaser.html)

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

   Het Sling-model voor `MyProductTeaser` wordt gebruikt en toegewezen aan de variabele `product` .

1. Bewerk `productteaser.html` zodanig dat dit de methode `isEcoFriendly` aanroept die in de vorige exercitie is geïmplementeerd:

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

   Wanneer u een methode van het Sling Model in HTML aanroept, wordt het `get` - en `is` -gedeelte van de methode verwijderd en wordt de eerste letter verlaagd. Dus `isShowBadge()` wordt `.showBadge` en `isEcoFriendly` wordt `.ecoFriendly` . Op basis van de Booleaanse waarde die door `.isEcoFriendly()` wordt geretourneerd, wordt bepaald of de `<span>Eco Friendly</span>` wordt weergegeven.

   Meer informatie over `data-sly-test` en andere [ het blokverklaringen van HTML kan hier ](https://experienceleague.adobe.com/docs/experience-manager-htl/content/specification.html) worden gevonden.

1. Sparen de veranderingen en stel de updates in om AEM te gebruiken uw Maven vaardigheden, van een bevel-lijn terminal op te stellen:

   ```shell
   $ cd aem-cif-guides-venia/
   $ mvn clean install -PautoInstallSinglePackage -Pclassic
   ```

1. Open een nieuw browser venster en navigeer aan AEM en de **console OSGi** > **Status** > **Sling Models**: [ http://localhost:4502/system/console/status-slingmodels ](http://localhost:4502/system/console/status-slingmodels)

1. Zoek naar `MyProductTeaserImpl` en u zou een lijn als het volgende moeten zien:

   ```plain
   com.venia.core.models.commerce.MyProductTeaserImpl - venia/components/commerce/productteaser
   ```

   Dit wijst erop dat het het Verdelen Model behoorlijk is opgesteld en aan de correcte component in kaart gebracht.

1. Vernieuwen aan de **Homepage van Venia** in [ http://localhost:4502/editor.html/content/venia/us/en.html ](http://localhost:4502/editor.html/content/venia/us/en.html) waar de Teaser van het Product is toegevoegd.

   ![ Eco Friendly getoonde bericht ](../assets/customize-cif-components/eco-friendly-text-displayed.png)

   Als het product de `eco_friendly` attributen heeft die aan **worden geplaatst ja**, zou u de tekst &quot;vriendschappelijk&quot;op de pagina moeten zien. Probeer over te schakelen op verschillende producten om de gedragswijziging te zien.

1. Open vervolgens de AEM `error.log` om de loginstructies te zien die zijn toegevoegd. De `error.log` bevindt zich op `<AEM SDK Install Location>/crx-quickstart/logs/error.log` .

   Zoek in de AEM logboeken naar de logboekinstructies die in het Sling-model zijn toegevoegd:

   ```plain
   2020-08-28 12:57:03.114 INFO [com.venia.core.models.commerce.MyProductTeaserImpl] *** Product is Eco Friendly**
   ...
   2020-08-28 13:01:00.271 INFO [com.venia.core.models.commerce.MyProductTeaserImpl] *** Product is not Eco Friendly**
   ...
   ```

   >[!CAUTION]
   >
   >U kunt ook enkele stacksporen zien als het product dat in de teaser wordt gebruikt, het kenmerk `eco_friendly` niet heeft als onderdeel van de kenmerkset.

## Stijlen toevoegen voor de milieuvriendelijke badge {#add-styles}

Op dit punt werkt de logica voor wanneer om **vriendschappelijk Eco** badge te tonen, nochtans kon de gewone tekst sommige stijlen gebruiken. Voeg vervolgens een pictogram en stijlen toe aan de module `ui.frontend` om de implementatie te voltooien.

1. Download het {](../assets/customize-cif-components/eco_friendly.svg) dossier 0} eco_Vriendelijk.svg. [ Dit wordt gebruikt als **Milieuvriendelijk** badge.
1. Ga terug naar de IDE en navigeer naar de map `ui.frontend` .
1. Voeg het bestand `eco_friendly.svg` toe aan de map `ui.frontend/src/main/resources/images` :

   ![ Eco Friendly SVG toegevoegd ](../assets/customize-cif-components/eco-friendly-svg-added.png)

1. Open het bestand `productteaser.scss` om `ui.frontend/src/main/styles/commerce/_productteaser.scss` .
1. Voeg de volgende regels van de Klasse binnen de `.productteaser` klasse toe:

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
   >Controle uit [ het Stijlen CIF de Componenten van de Kern ](./style-cif-component.md) voor meer details rond front-end werkschema&#39;s.

1. Sparen de veranderingen en stel de updates in om AEM te gebruiken uw Maven vaardigheden, van een bevel-lijn terminal op te stellen:

   ```shell
   $ cd aem-cif-guides-venia/
   $ mvn clean install -PautoInstallSinglePackage -Pclassic
   ```

1. Vernieuwen aan de **Homepage van Venia** in [ http://localhost:4502/editor.html/content/venia/us/en.html ](http://localhost:4502/editor.html/content/venia/us/en.html) waar de Teaser van het Product is toegevoegd.

   ![ Eco Friendly de Definitieve Implementatie van de Band ](../assets/customize-cif-components/final-product-teaser-eco-badge.png)

## Gefeliciteerd {#congratulations}

U hebt uw eerste AEM CIF component aangepast! Download de [ gebeëindigde oplossingsdossiers hier ](../assets/customize-cif-components/customize-cif-component-SOLUTION_FILES.zip).

## Bonus Challenge {#bonus-challenge}

Herzie de functionaliteit van de **Nieuwe** badge die reeds in de Teaser van het Product is uitgevoerd. Probeer om extra checkbox voor auteurs toe te voegen om te controleren wanneer **Milieuvriendelijk** badge zou moeten worden getoond. Werk het componentendialoogvenster bij op `ui.apps/src/main/content/jcr_root/apps/venia/components/commerce/productteaser/_cq_dialog/.content.xml` .

![ Nieuwe uitdaging van de Implementatie van de Badge ](../assets/customize-cif-components/new-badge-implementation-challenge.png)

## Aanvullende bronnen {#additional-resources}

- [AEM Archetype ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html)
- [ AEM CIF de Componenten van de Kern ](https://github.com/adobe/aem-core-cif-components)
- [ Aanpassen AEM CIF de Componenten van de Kern ](https://github.com/adobe/aem-core-cif-components)
- [ het Aanpassen van de Componenten van de Kern ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/customizing.html)
- [ Begonnen het worden met AEM Sites ](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html)
- [Gebruik van CIF product- en rubriekkiezer](use-cif-pickers.md)
