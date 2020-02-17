---
title: SAP Commerce Cloud
seo-title: SAP Commerce Cloud
description: Leer hoe u eCommerce kunt implementeren met SAP Commerce Cloud.
seo-description: Leer hoe u eCommerce kunt implementeren met SAP Commerce Cloud.
uuid: a16ae42b-9c33-4da8-a130-52b72a779ec7
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: e-commerce
content-type: reference
discoiquuid: 44dfa10f-497e-473f-95d4-8dccae7ebf8e
pagetitle: Deploying eCommerce with SAP Commerce Cloud
translation-type: tm+mt
source-git-commit: 328e13eb2ce034b0b1ec7e5e0fb184de9435d1bc

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

De implementatie van de [noodzakelijke e-commercepakketten](#packages-needed-for-ecommerce-with-hybris) zal de volledige functionaliteit van het eCommerce-kader bieden, samen met een referentie-implementatie van de eCommerce-functionaliteit zoals voorzien van een hybris-implementatie (inclusief een demonstratiecatalogus)

Dit is beschikbaar onder de Engelse (Amerikaanse) tak ( `/content/geometrixx-outdoors/en_US`) van de Geometrixx-site Buiten:

* [Productinformatie](#productinformationwithcolorvariants) (eventueel met kleurvarianten)

* [Overzichten van winkelwagentinhoud](#shoppingcartcontentoverview)
* [Aanmelden bij](#customersignup) de klant en aanmelden bij de [klant](#customersignin)

* [Toegang tot de hybris Management Console](#accesstothehybrismanagementconsole)

### Technische vereisten - hybrusserver {#technical-requirements-hybris-server}

De hybris-uitbreiding van het eCommerce Integration Framework is bijgewerkt om Hybris 5 (standaard) te ondersteunen, terwijl achterwaartse compatibiliteit met [Hybris 4](/help/sites-developing/sap-commerce-cloud.md#developing-for-hybris)behouden blijft.

>[!NOTE]
>
>* Ondersteunt versies 18.11 en hoger.
>* U hebt Java 7 nodig om de [hybris 5-server uit te voeren.](https://www.hybris.com/en/architecture-technology)
>* De hybris-invoegtoepassing, de [Telco Accelerator](https://www.hybris.com/en/products/telecommunication), wordt niet ondersteund door de AEM-extensie.
>



### Pakketten die nodig zijn voor e-handel met hybris {#packages-needed-for-ecommerce-with-hybris}

Voor de installatie van eCommerce-functionaliteit hebt u het volgende nodig:

* Uw hybrusserver
* AEM e-Commerce-kader:

   * dit is onderdeel van een standaard AEM-installatie

* AEM Geometrixx-all-pakket:

   * `cq-geometrixx-all-pkg`

* AEM-hybris-inhoudspakketten:

   * `cq-hybris-content-6.3.2`
   * hybrisspecifieke API-implementatie
   * `cq-geometrixx-hybris-content-6.3.2`
   * een referentie-implementatie om het gebruik van hybris te illustreren ( `geometrixx-outdoors/en_US`)

### Installatie van eCommerce met hybris {#installation-of-ecommerce-with-hybris}

Voor het installeren van een volledige configuratie (met de demonstratiecatalogus, Geometrixx Buiten) zijn de basisstappen:

1. [Installeer AEM](/help/sites-deploying/deploy.md).
1. Het Geometrixx-pakket installeren

   1. ` [cq-geometrixx-all-pkg](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq60/product/cq-geometrixx-all-pkg)`

1. Installeer de pakketten met demonstratieinhoud met behulp van [pakketbeheer](/help/sites-administering/package-manager.md):

   1. ` [cq-hybris-content-6.3.2](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq630/product/cq-hybris-content)`
   1. ` [cq-geometrixx-hybris-content-6.3.2](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq630/product/cq-geometrixx-hybris-content)`

1. [Download en maak uw hybris Server](#download-and-build-your-hybris-server).
1. Construeer uw catalogus in uw eCommerce-engine:

   1. [Stel de Geometrixx buitenwinkel](#setup-the-geometrixx-outdoors-store)in.

1. [Maak](/help/sites-authoring/qg-page-authoring.md) aanvullende pagina&#39;s die u in AEM nodig hebt.

>[!CAUTION]
>
>Voor het gebruik van de hybrisserver is een aparte licentie voor hybris vereist.

>[!NOTE]
>
>Voor ontwikkelaars is ook de [API-documentatie](/help/sites-developing/ecommerce.md#api-documentation) beschikbaar voor downloaden.

### Uw hybrisserver downloaden en samenstellen {#download-and-build-your-hybris-server}

De stappen in deze procedure zullen de hybrisserver downloaden en bouwen. Het zal ook de aanvankelijke configuraties die voor de verbindingen tussen hybris en cq worden vereist maken. De extensie kan dan worden gebruikt met de standaardinstellingen.

>[!CAUTION]
>
>Hybrusversies ouder dan 5.5.1 worden niet ondersteund.

>[!NOTE]
>
>Om dit te voltooien, moet [Groovy](https://groovy-lang.org/) op uw systeem zijn geïnstalleerd.

1. Download de **hybris Commerce Suite** -distributie van de hybris downloadsite.

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
   >Druk `Return` indien nodig op.

1. Download de volgende bestanden naar de hoofdmap van de geëxtraheerde hybrisdistributie,

   ```
       <hybris-root-directory>
   ```


   [Bestand ophalen](assets/setup.groovy)

   >[!NOTE]
   >
   >Gebruik voor hybris 5.6.0 en hoger de volgende setup.groovy.

   5.6.0 en hoger

   [Bestand ophalen](assets/setup-1.groovy)

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

1. In uw browser, navigeer aan de **hybris beleidsconsole** bij:

   [http://localhost:9002](http://localhost:9002)

1. Klik op **Initialiseren** en bevestig vervolgens de initialisatiehandeling (omdat bestaande gegevens worden verwijderd).

   De voortgang wordt weergegeven op de console, met `FINISHED` aanduiding van de voltooiing.

   >[!NOTE]
   >
   >Afhankelijk van uw systeem kan het enkele minuten duren voordat de bewerking is voltooid.

### De Geometrixx buitenshuis opslaan {#setup-the-geometrixx-outdoors-store}

Deze procedure zal de demonstratieopslag - Geometrixx Online uploaden en vormen.

1. Start de hybris-instantie. Voer de volgende handelingen uit vanaf de opdrachtregel:

   ```shell
   cd <hybris-root-directory>/bin/platform
   sh hybrisserver.sh
   ```

1. In uw browser, navigeer aan de **hybris beheersconsole** bij:

   [https://localhost:9002/backoffice](https://localhost:9002/backoffice)

   Gebruik de volgende referenties:
   * gebruikersnaam: beheerder
   * wachtwoord: nimda

1. Van de zijbalknavigatie, breid **Systeem** en **Hulpmiddelen** uit. Selecteer vervolgens **Importeren** om de **wizard te openen: Het venster CSV-import** .
1. Upload **op het tabblad** Configuratie **het volgende** importbestand ****:

   [Bestand ophalen](assets/geometrixx-outdoors-export.csv)

1. Stel de **landinstelling** in op:

   `en_US - English (United States)`

1. Open het tabblad **Bronnen** .
1. **Upload** de volgende **media-Zip**:

   [Bestand ophalen](assets/geometrixx-outdoors-images.zip)

1. Klik op **Start** om de opgegeven bestanden te importeren. Op het tabblad **Resultaat** worden alle logbestandvermeldingen weergegeven.

1. Klik op **Gereed** om het importvenster te sluiten.

1. Kies in het zijpaneel eerst **Systeem** en daarna **Gereedschappen** en **Importeer**.

1. **Upload** het volgende **importbestand**:

   [Bestand ophalen](assets/base-store.csv)

   Gebruik voor hybris 5.7 het volgende:

   [Bestand ophalen](assets/base-store-5_7.csv)

1. Stel de **landinstelling** in op:

   `en_US - English (United States)`

1. Klik op **Start** om de opgegeven bestanden te importeren. Op het tabblad **Resultaat** worden alle logbestandvermeldingen weergegeven.

1. Klik op **Gereed** om het importvenster te sluiten.

1. U kunt nu de cockpit met producten gebruiken om de geïmporteerde catalogi en producten weer te geven:

   [http://localhost:9002/productcockpit](http://localhost:9002/productcockpit)

