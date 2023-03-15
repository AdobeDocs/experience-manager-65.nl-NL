---
title: SAP Commerce Cloud
seo-title: SAP Commerce Cloud
description: Leer hoe te om eCommerce met SAP Commerce Cloud op te stellen.
seo-description: Learn how to deploy eCommerce with SAP Commerce Cloud.
contentOwner: Guillaume Carlino
topic-tags: e-commerce
content-type: reference
exl-id: ecbd0097-c407-4581-bab2-4729a71df4a3
source-git-commit: 78359fb8ecbcc0227ab5a3910175aed73d823902
workflow-type: tm+mt
source-wordcount: '721'
ht-degree: 0%

---

# SAP Commerce Cloud{#sap-commerce-cloud}

>[!NOTE]
>
>Deze pagina bevat koppelingen naar de website van de hybris. Voor bepaalde pagina&#39;s hebt u een account nodig om u aan te melden.

## eCommerce implementeren met SAP Commerce Cloud {#deploying-ecommerce-with-sap-commerce-cloud}

>[!NOTE]
>
>De volgende procedures gebruiken de volgende demonstratiecatalogus om de plaatsing te illustreren:
>
>`Geometrixx Outdoors Site English (US)`

De [noodzakelijke eCommerce-pakketten](#packages-needed-for-ecommerce-with-hybris) zal de volledige functionaliteit van het eCommerce-kader bieden, samen met een referentie-implementatie van de eCommerce-functionaliteit zoals voorzien in een hybris-implementatie (inclusief een demonstratiecatalogus)

Dit is beschikbaar onder de Engelse (Amerikaanse) tak ( `/content/geometrixx-outdoors/en_US`) van de site Geometrixx Outdoors:

* [Productinformatie](#productinformationwithcolorvariants) (eventueel met kleurvarianten)

* [Overzichten van winkelwagentinhoud](#shoppingcartcontentoverview)
* [Aanmelden bij klant](#customersignup) en [Aanmelden bij klant](#customersignin)

* [Toegang tot de hybris Management Console](#accesstothehybrismanagementconsole)

### Technische vereisten - hybrusserver {#technical-requirements-hybris-server}

De hybris-uitbreiding van het eCommerce Integration Framework is bijgewerkt om Hybris 5 (als standaard) te ondersteunen, terwijl achterwaartse compatibiliteit met [Hybris 4](/help/commerce/cif-classic/developing/sap-commerce-cloud.md#developing-for-hybris).

>[!NOTE]
>
>* Ondersteunt versies 18.11 en hoger.
>* U hebt Java 7 nodig om de [hybris 5-server.](https://www.hybris.com/en/architecture-technology)
>* De hybris-invoegtoepassing, de [Telco Accelerator](https://www.hybris.com/en/products/telecommunication), wordt niet ondersteund door de AEM extensie.
>


### Pakketten die nodig zijn voor e-handel met hybris {#packages-needed-for-ecommerce-with-hybris}

Voor de installatie van eCommerce-functionaliteit hebt u het volgende nodig:

* Uw hybrusserver
* AEM eCommerce-kader:

   * dit maakt deel uit van een standaard AEM installatie

* AEM Geometrixx-all-pakket:

   * `cq-geometrixx-all-pkg`

* AEM hybris-inhoudspakketten:

   * `cq-hybris-content-6.3.2`
   * hybrisspecifieke API-implementatie
   * `cq-geometrixx-hybris-content-6.3.2`
   * een referentie-implementatie om het gebruik van hybris te illustreren ( `geometrixx-outdoors/en_US`)

### Installatie van eCommerce met hybris {#installation-of-ecommerce-with-hybris}

Voor het installeren van een volledige configuratie (met de demonstratiecatalogus, Geometrixx Outdoors) zijn de basisstappen:

1. [AEM installeren](/help/sites-deploying/deploy.md).
1. Het Geometrixx-all-pakket installeren

   1. ` [cq-geometrixx-all-pkg](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq60/product/cq-geometrixx-all-pkg)`

1. Installeer de demonstratieinhoudpakketten met de [pakketbeheer](/help/sites-administering/package-manager.md):

   1. ` [cq-hybris-content-6.3.2](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq630/product/cq-hybris-content)`
   1. ` [cq-geometrixx-hybris-content-6.3.2](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq630/product/cq-geometrixx-hybris-content)`

1. [Uw hybrusserver downloaden en bouwen](#download-and-build-your-hybris-server).
1. Construeer uw catalogus in uw eCommerce-engine:

   1. [De buitenwinkel van de Geometrixx instellen](#setup-the-geometrixx-outdoors-store).

1. [Auteur](/help/sites-authoring/qg-page-authoring.md) aanvullende pagina&#39;s die u nodig hebt in AEM.

>[!CAUTION]
>
>Voor het gebruik van de hybrisserver is een aparte licentie voor hybris vereist.

>[!NOTE]
>
>Voor ontwikkelaars [API-documentatie](/help/commerce/cif-classic/developing/ecommerce.md#api-documentation) kan ook worden gedownload.

### Uw hybrisserver downloaden en samenstellen {#download-and-build-your-hybris-server}

De stappen in deze procedure zullen de hybrisserver downloaden en bouwen. Het zal ook de aanvankelijke configuraties die voor de verbindingen tussen hybris en cq worden vereist maken. De extensie kan dan worden gebruikt met de standaardinstellingen.

>[!CAUTION]
>
>Hybrusversies ouder dan 5.5.1 worden niet ondersteund.

>[!NOTE]
>
>Om dit te voltooien, zult u nodig hebben [Groovy](https://groovy-lang.org/) op uw systeem geïnstalleerd.

1. Download de **hybris Commerce Suite** distributie via de hybris - downloadsite .

   >[!CAUTION]
   >
   >U hebt een account (van hybris) nodig om dit te kunnen openen.

1. Pak het distributiebestand uit op de gewenste locatie (doorverwijzen naar &lt;hybris-root-directory>).
1. Voer de volgende handelingen uit vanaf de opdrachtregel:

   ```shell
   cd <hybris-root-directory>/bin/platform
   . ./setantenv.sh
   ant clean all
   cd ../..
   ```

   >[!NOTE]
   >
   >Bij uitvoering:
   >
   >`ant clean all`
   >
   >Druk `Return` indien vereist.

1. Download de volgende bestanden naar de hoofdmap van de geëxtraheerde hybrisdistributie,

   ```
       <hybris-root-directory>
   ```


[Bestand ophalen](/help/sites-deploying/assets/setup.groovy)

   >[!NOTE]
   >
   >Gebruik voor hybris 5.6.0 en hoger de volgende setup.groovy.

   5.6.0 en hoger

[Bestand ophalen](/help/sites-deploying/assets/setup-1.groovy)

1. Voer vanaf de opdrachtregel de volgende handelingen uit:

   * update de configuratie van de hybrisserver (zoals vereist door de extensie)
   * herbouwt de hybrisserver met de gewijzigde configuratie
   * de server starten

   ```shell
   groovy setup.groovy
   cd bin/platform
   ant clean all
   sh hybrisserver.sh
   ```

   >[!NOTE]
   >
   >Afhankelijk van uw systeem kunnen verschillende van deze stappen enkele minuten duren.

1. Navigeer in uw browser naar de **hybris-beheerconsole** om:

   [http://localhost:9002](http://localhost:9002)

1. Klikken **Initialiseren** en bevestig vervolgens de initialisatieactie (aangezien bestaande gegevens worden verwijderd).

   De voortgang wordt weergegeven op de console, met `FINISHED` afwerking aangeven.

   >[!NOTE]
   >
   >Afhankelijk van uw systeem kan het enkele minuten duren voordat de bewerking is voltooid.

### De Geometrixx Outdoors Store instellen {#setup-the-geometrixx-outdoors-store}

Deze procedure zal de demonstratieopslag - Geometrixx Online uploaden en vormen.

1. Start de hybris-instantie. Voer de volgende handelingen uit vanaf de opdrachtregel:

   ```shell
   cd <hybris-root-directory>/bin/platform
   sh hybrisserver.sh
   ```

1. Navigeer in uw browser naar de **hybrusbeheerconsole** om:

   [https://localhost:9002/backoffice](https://localhost:9002/backoffice)

   Gebruik de volgende referenties:
   * gebruikersnaam: beheerder
   * wachtwoord: nimda

1. Vouw vanuit de zijbalknavigatie uit **Systeem** en **Gereedschappen**. Selecteer vervolgens **Importeren** om de **Wizard: CSV-import** venster.
1. In de **Configuratie** tab, **Uploaden** het volgende **Bestand importeren**:

[Bestand ophalen](/help/sites-deploying/assets/geometrixx-outdoors-export.csv)

1. Stel de **Landinstelling** tot:

   `en_US - English (United States)`

1. Open de **Bronnen** tab.
1. **Uploaden** het volgende **Media-Zip**:

[Bestand ophalen](/help/sites-deploying/assets/geometrixx-outdoors-images.zip)

1. Klikken **Start** om de opgegeven bestanden te importeren. De **Resultaat** worden alle logbestandvermeldingen weergegeven.

1. Klikken **Gereed** om het importvenster te sluiten.

1. Selecteer in het zijpaneel de optie **Systeem** vervolgens **Gereedschappen** vervolgens **Importeren**.

1. **Uploaden** het volgende **Bestand importeren**:

[Bestand ophalen](/help/sites-deploying/assets/base-store.csv)

   Gebruik voor hybris 5.7 het volgende:

[Bestand ophalen](/help/sites-deploying/assets/base-store-5_7.csv)

1. Stel de **Landinstelling** tot:

   `en_US - English (United States)`

1. Klikken **Start** om de opgegeven bestanden te importeren. De **Resultaat** worden alle logbestandvermeldingen weergegeven.

1. Klikken **Gereed** om het importvenster te sluiten.

1. U kunt nu de cockpit met producten gebruiken om de geïmporteerde catalogi en producten weer te geven:

   [http://localhost:9002/productcockpit](http://localhost:9002/productcockpit)
