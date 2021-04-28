---
title: SAP Commerce Cloud
seo-title: SAP Commerce Cloud
description: Leer hoe te om eCommerce met SAP Commerce Cloud op te stellen.
seo-description: Leer hoe te om eCommerce met SAP Commerce Cloud op te stellen.
contentOwner: Guillaume Carlino
topic-tags: e-commerce
content-type: reference
translation-type: tm+mt
source-git-commit: da538dac17b4c6182b44801b4c79d6cdbf35f640
workflow-type: tm+mt
source-wordcount: '733'
ht-degree: 0%

---

# SAP Commerce Cloud{#sap-commerce-cloud}

>[!NOTE]
>
>Deze pagina bevat koppelingen naar de website van de hybris. Voor bepaalde pagina&#39;s hebt u een account nodig om u aan te melden.

## Elektronische handel implementeren met SAP Commerce Cloud {#deploying-ecommerce-with-sap-commerce-cloud}

>[!NOTE]
>
>De volgende procedures gebruiken de volgende demonstratiecatalogus om de plaatsing te illustreren:
>
>`Geometrixx Outdoors Site English (US)`

Door de [noodzakelijke eCommerce-pakketten](#packages-needed-for-ecommerce-with-hybris) te implementeren, wordt de volledige functionaliteit van het eCommerce-kader geboden, samen met een referentie-implementatie van de eCommerce-functionaliteit zoals voorzien van een hybris-implementatie (inclusief een demonstratiecatalogus)

Dit is beschikbaar onder de Engelse vertakking ( `/content/geometrixx-outdoors/en_US`) van de site Geometrixx Outdoors:

* [Productinformatie](#productinformationwithcolorvariants)  (eventueel met kleurvarianten)

* [Overzichten van winkelwagentinhoud](#shoppingcartcontentoverview)
* [Aanmelden bij ](#customersignup) klant en aanmelden bij  [klant](#customersignin)

* [Toegang tot de hybris Management Console](#accesstothehybrismanagementconsole)

### Technische vereisten - hybris Server {#technical-requirements-hybris-server}

De hybris uitbreiding van het eCommerce Integration Framework is bijgewerkt om Hybris 5 (als gebrek) te steunen, terwijl het handhaven van achterwaartse verenigbaarheid met [Hybris 4](/help/commerce/cif-classic/developing/sap-commerce-cloud.md#developing-for-hybris).

>[!NOTE]
>
>* Ondersteunt versies 18.11 en hoger.
>* U hebt Java 7 nodig om de [hybris 5-server uit te voeren.](https://www.hybris.com/en/architecture-technology)
>* De hybris add-on, de [Telco Accelerator](https://www.hybris.com/en/products/telecommunication), wordt niet ondersteund door de AEM extensie.

>



### Pakketten nodig voor e-handel met hybris {#packages-needed-for-ecommerce-with-hybris}

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

1. [AEM](/help/sites-deploying/deploy.md) installeren.
1. Het Geometrixx-all-pakket installeren

   1. ` [cq-geometrixx-all-pkg](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq60/product/cq-geometrixx-all-pkg)`

1. Installeer de demonstratie-inhoudpakketten met behulp van [pakketbeheer](/help/sites-administering/package-manager.md):

   1. ` [cq-hybris-content-6.3.2](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq630/product/cq-hybris-content)`
   1. ` [cq-geometrixx-hybris-content-6.3.2](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq630/product/cq-geometrixx-hybris-content)`

1. [Download en maak uw hybris Server](#download-and-build-your-hybris-server).
1. Construeer uw catalogus in uw eCommerce-engine:

   1. [Stel de Geometrixx Outdoorwinkel](#setup-the-geometrixx-outdoors-store) in.

1. [](/help/sites-authoring/qg-page-authoring.md) Geef aanvullende pagina&#39;s op die u in AEM nodig hebt.

>[!CAUTION]
>
>Voor het gebruik van de hybrisserver is een aparte licentie voor hybris vereist.

>[!NOTE]
>
>Voor ontwikkelaars [API documentatie](/help/commerce/cif-classic/developing/ecommerce.md#api-documentation) is ook beschikbaar voor download.

### Uw hybride server {#download-and-build-your-hybris-server} downloaden en samenstellen

De stappen in deze procedure zullen de hybrisserver downloaden en bouwen. Het zal ook de aanvankelijke configuraties die voor de verbindingen tussen hybris en cq worden vereist maken. De extensie kan dan worden gebruikt met de standaardinstellingen.

>[!CAUTION]
>
>Hybrusversies ouder dan 5.5.1 worden niet ondersteund.

>[!NOTE]
>
>Om dit te voltooien, zult u [Groovy](https://groovy-lang.org/) op uw systeem geïnstalleerd nodig hebben.

1. Download de **hybris Commerce Suite** distributie van de hybris downloadsite.

   >[!CAUTION]
   >
   >U hebt een account (van hybris) nodig om dit te kunnen openen.

1. Pak het distributiebestand uit op de gewenste locatie (wordt &lt;hybris-root-directory> genoemd).
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
   >Druk indien nodig op `Return`.

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

1. Navigeer in uw browser naar de **hybris-beheerconsole** op:

   [http://localhost:9002](http://localhost:9002)

1. Klik **Initialiseren** en bevestig vervolgens de initialisatiehandeling (aangezien bestaande gegevens worden verwijderd).

   De voortgang wordt weergegeven op de console, met `FINISHED` als aanduiding voor voltooiing.

   >[!NOTE]
   >
   >Afhankelijk van uw systeem kan het enkele minuten duren voordat de bewerking is voltooid.

### De Geometrixx Outdoors opslaan {#setup-the-geometrixx-outdoors-store} instellen

Deze procedure zal de demonstratieopslag - Geometrixx Online uploaden en vormen.

1. Start de hybris-instantie. Voer de volgende handelingen uit vanaf de opdrachtregel:

   ```shell
   cd <hybris-root-directory>/bin/platform
   sh hybrisserver.sh
   ```

1. Navigeer in uw browser naar de **hybris management console** op:

   [https://localhost:9002/backoffice](https://localhost:9002/backoffice)

   Gebruik de volgende referenties:
   * gebruikersnaam: beheerder
   * wachtwoord: nimda

1. Vouw vanuit de zijbalknavigatie **System** en **Tools** uit. Selecteer vervolgens **Import** om de **Wizard te openen: Het venster CSV-import**.
1. In **Configuration** tabel, **Upload** het volgende **Import file**:

   [Bestand ophalen](/help/sites-deploying/assets/geometrixx-outdoors-export.csv)

1. Stel de **Landinstelling** in op:

   `en_US - English (United States)`

1. Open het tabblad **Bronnen**.
1. **** Uploadt de volgende  **media-Zip**:

   [Bestand ophalen](/help/sites-deploying/assets/geometrixx-outdoors-images.zip)

1. Klik **Start** om de opgegeven bestanden te importeren. Op het tabblad **Resultaat** worden alle logbestandvermeldingen weergegeven.

1. Klik **Done** om het importvenster te sluiten.

1. Selecteer **Systeem** in het zijpaneel, vervolgens **Gereedschappen** en **Importeren**.

1. **** Uploadt het volgende  **importbestand**:

   [Bestand ophalen](/help/sites-deploying/assets/base-store.csv)

   Gebruik voor hybris 5.7 het volgende:

   [Bestand ophalen](/help/sites-deploying/assets/base-store-5_7.csv)

1. Stel de **Landinstelling** in op:

   `en_US - English (United States)`

1. Klik **Start** om de opgegeven bestanden te importeren. Op het tabblad **Resultaat** worden alle logbestandvermeldingen weergegeven.

1. Klik **Done** om het importvenster te sluiten.

1. U kunt nu de cockpit met producten gebruiken om de geïmporteerde catalogi en producten weer te geven:

   [http://localhost:9002/productcockpit](http://localhost:9002/productcockpit)
