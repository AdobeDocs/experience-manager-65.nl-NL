---
title: eCommerce distribueren met SAP-Commerce Cloud
description: Leer hoe u Adobe Experience Manager eCommerce kunt implementeren met SAP-Commerce Cloud.
contentOwner: Guillaume Carlino
topic-tags: e-commerce
content-type: reference
exl-id: ecbd0097-c407-4581-bab2-4729a71df4a3
solution: Experience Manager,Commerce
feature: Commerce Integration Framework
role: Admin, Developer
source-git-commit: 10268f617b8a1bb22f1f131cfd88236e7d5beb47
workflow-type: tm+mt
source-wordcount: '712'
ht-degree: 0%

---

# SAP-Commerce Cloud{#sap-commerce-cloud}

>[!NOTE]
>
>Deze pagina bevat koppelingen naar de website van de hybris. Voor bepaalde pagina&#39;s hebt u een account nodig voor aanmelding.

## eCommerce implementeren met SAP-Commerce Cloud {#deploying-ecommerce-with-sap-commerce-cloud}

>[!NOTE]
>
>De volgende procedures gebruiken de volgende demonstratiecatalogus om de plaatsing te illustreren:
>
>`Geometrixx Outdoors Site English (US)`

Het opstellen van de [ noodzakelijke eCommerce pakketten ](#packages-needed-for-ecommerce-with-hybris) verstrekt de volledige functionaliteit van het kader van eCommerce, samen met een verwijzingsimplementatie van de functionaliteit van eCommerce zoals voorzien van een hybris implementatie (met inbegrip van een demonstratiecatalogus)

Dit is beschikbaar onder de Engelse vertakking ( `/content/geometrixx-outdoors/en_US`) van de site Geometrixx Outdoors:

* [ Informatie van het Product ](#productinformationwithcolorvariants) (met kleurenvarianten waar aangewezen)

* [Overzichten van winkelwagentinhoud](#shoppingcartcontentoverview)
* [ Klantaanmelding ](#customersignup) en [ Klantaanmelding ](#customersignin)

* [Toegang tot de hybris-beheerconsole](#accesstothehybrismanagementconsole)

### Technische vereisten - hybrusserver {#technical-requirements-hybris-server}

De hybris uitbreiding van het Kader van de Integratie van de eHandel is bijgewerkt om Hybris 5 (als gebrek) te steunen, terwijl het handhaven van achterwaartse verenigbaarheid met [ Hybris 4 ](/help/commerce/cif-classic/developing/sap-commerce-cloud.md#developing-for-hybris).

>[!NOTE]
>
>* Ondersteunt versies 18.11 en hoger.
>* U hebt Java™ 7 nodig om [ hybris 5 server in werking te stellen.](https://www.sap.com/products/crm.html)
>* De hybris toe:voegen-op, de [ Versneller van Telco ](https://www.sap.com/products/crm.html), wordt niet gesteund door de AEM uitbreiding.
>

### Pakketten die nodig zijn voor e-handel met hybris {#packages-needed-for-ecommerce-with-hybris}

Voor de installatie van eCommerce-functionaliteit hebt u het volgende nodig:

* Uw hybrusserver
* AEM kader e-handel:

   * dit maakt deel uit van een standaard AEM installatie

* Geometrixx-alle AEM:

   * `cq-geometrixx-all-pkg`

* AEM hybris-inhoudspakketten:

   * `cq-hybris-content-6.3.2`
   * hybrisspecifieke API-implementatie
   * `cq-geometrixx-hybris-content-6.3.2`
   * een referentie-implementatie om het gebruik van hybris te illustreren ( `geometrixx-outdoors/en_US`)

### Installatie van eCommerce met hybris {#installation-of-ecommerce-with-hybris}

Voor het installeren van een volledige configuratie (met de demonstratiecatalogus, Geometrixx Outdoors) zijn de basisstappen:

1. [ installeer AEM ](/help/sites-deploying/deploy.md).
1. Het Geometrixx-all-pakket installeren

   1. ` [cq-geometrixx-all-pkg](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq60/product/cq-geometrixx-all-pkg)`

1. Installeer de pakketten van de demonstratieinhoud gebruikend de [ Manager van het Pakket ](/help/sites-administering/package-manager.md):

   1. ` [cq-hybris-content-6.3.2](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq630/product/cq-hybris-content)`
   1. ` [cq-geometrixx-hybris-content-6.3.2](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq630/product/cq-geometrixx-hybris-content)`

1. [ Download en bouwt uw hybrisServer ](#download-and-build-your-hybris-server).
1. Construeer uw catalogus in uw eCommerce-engine:

   1. [ opstelling de Geometrixx Outdooropslag ](#setup-the-geometrixx-outdoors-store).

1. [ Auteur ](/help/sites-authoring/qg-page-authoring.md) om het even welke extra pagina&#39;s die u in AEM nodig hebt.

>[!CAUTION]
>
>Voor het gebruik van de hybrisserver is een aparte licentie voor hybris vereist.

>[!NOTE]
>
>Voor ontwikkelaars, [ API documentatie ](/help/commerce/cif-classic/developing/ecommerce.md#api-documentation) is ook beschikbaar voor download.

### Uw computerserver downloaden en samenstellen {#download-and-build-your-hybris-server}

De stappen in deze procedure downloaden en bouwen de hybrisserver. Het maakt ook de aanvankelijke configuraties die voor de verbindingen tussen hybris en cq worden vereist. De extensie kan vervolgens worden gebruikt met de standaardinstellingen.

>[!CAUTION]
>
>Hybrusversies ouder dan 5.5.1 worden niet ondersteund.

>[!NOTE]
>
>Om dit te voltooien, hebt u [ Groovy ](https://groovy-lang.org/) geïnstalleerd op uw systeem nodig.

1. Download de **hybris Commerce Suite** distributie van de hybris downloadplaats.

   >[!CAUTION]
   >
   >U hebt een account (van hybris) nodig om toegang te krijgen tot deze account.

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
   >Druk indien nodig op `Return` .

1. Download de volgende bestanden naar de hoofdmap van de geëxtraheerde hybrisdistributie,

   ```
       <hybris-root-directory>
   ```


[Bestand ophalen](/help/sites-deploying/assets/setup.groovy)

   >[!NOTE]
   >
   >Voor hybris 5.6.0 en later, gebruik volgende setup.groovy.

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

1. In uw browser, navigeer aan de **hybris beleidsconsole** bij:

   [ http://localhost:9002](http://localhost:9002)

1. Klik **initialiseren** en bevestig dan de initialiseringsactie (aangezien het bestaande gegevens) schrapt.

   De voortgang wordt weergegeven op de console, waarbij `FINISHED` aangeeft dat de bewerking is voltooid.

   >[!NOTE]
   >
   >Afhankelijk van uw systeem kan het enkele minuten duren voordat de bewerking is voltooid.

### De Geometrixx Outdoors Store instellen {#setup-the-geometrixx-outdoors-store}

Deze procedure uploadt en configureert de demonstratiewinkel - Geometrixx Online.

1. Start de hybris-instantie. Voer de volgende handelingen uit vanaf de opdrachtregel:

   ```shell
   cd <hybris-root-directory>/bin/platform
   sh hybrisserver.sh
   ```

1. In uw browser, navigeer aan de **hybris beheersconsole** bij:

   [ https://localhost:9002/backoffice](https://localhost:9002/backoffice)

   Gebruik de volgende referenties:
   * gebruikersnaam: admin
   * wachtwoord: nimda

1. Van de sidebar navigatie, breid **Systeem &lbrace;en** Hulpmiddelen **uit.** Dan uitgezochte **Invoer** om de **Tovenaar te openen: CSV Importeert** venster.
1. In het **lusje van de Configuratie**, **upload** het volgende **dossier van de Invoer**:

[Bestand ophalen](/help/sites-deploying/assets/geometrixx-outdoors-export.csv)

1. Plaats het **Plaatsen van de Landinstelling** aan:

   `en_US - English (United States)`

1. Open het **Middelen** lusje.
1. **uploadt** volgende **media-Zip**:

[Bestand ophalen](/help/sites-deploying/assets/geometrixx-outdoors-images.zip)

1. Klik **Begin** om de gespecificeerde dossiers in te voeren. Het **lusje van het Resultaat** toont om het even welke logboekingangen.

1. Klik **Gedaan** om het de invoervenster te sluiten.

1. Van sidebar, uitgezochte **Systeem**, toen **Hulpmiddelen**, toen **de Invoer**.

1. **uploadt** het volgende **dossier van de Invoer**:

[Bestand ophalen](/help/sites-deploying/assets/base-store.csv)

   Gebruik voor hybris 5.7 het volgende:

[Bestand ophalen](/help/sites-deploying/assets/base-store-5_7.csv)

1. Plaats het **Plaatsen van de Landinstelling** aan:

   `en_US - English (United States)`

1. Klik **Begin** om de gespecificeerde dossiers in te voeren. Het **lusje van het Resultaat** toont om het even welke logboekingangen.

1. Klik **Gedaan** om het de invoervenster te sluiten.

1. U kunt nu de cockpit met producten gebruiken om de geïmporteerde catalogi en producten weer te geven:

   [ http://localhost:9002/productcockpit](http://localhost:9002/productcockpit)
