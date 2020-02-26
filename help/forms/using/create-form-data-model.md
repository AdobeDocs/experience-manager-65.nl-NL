---
title: '"Zelfstudie: Formuliergegevensmodel maken "'
seo-title: Zelfstudie formuliergegevensmodel maken
description: Formuliergegevensmodel maken
seo-description: Formuliergegevensmodel maken
uuid: b9d2bb1b-90f0-44f4-b1e3-0603cdf5f5b8
contentOwner: khsingh
products: SG_EXPERIENCEMANAGER/6.3/FORMS
discoiquuid: 12e6c325-ace0-4a57-8ed4-6f7ceee23099
docset: aem65
translation-type: tm+mt
source-git-commit: 70350add185b932ee604e190aabaf972ff994ba2

---


# Zelfstudie:Formuliergegevensmodel maken {#tutorial-create-form-data-model}

![04-create-form-data-model-main](assets/04-create-form-data-model-main.png)

Deze zelfstudie is een stap in de [serie Uw eerste adaptieve formulier](../../forms/using/create-your-first-adaptive-form.md) maken. U wordt aangeraden de reeks in chronologische volgorde te volgen om het volledige gebruik van de zelfstudie te begrijpen, uit te voeren en aan te tonen.

## Over de zelfstudie {#about-the-tutorial}

Met de gegevensintegratiemodule van AEM Forms kunt u een formuliergegevensmodel maken op basis van verschillende bronnen van back-endgegevens, zoals het AEM-gebruikersprofiel, RESTful-webservices, SOAP-webservices, OData-services en relationele databases. U kunt gegevensmodelobjecten en -services configureren in een formuliergegevensmodel en deze koppelen aan een adaptief formulier. Adaptieve formuliervelden zijn gebonden aan objecteigenschappen van gegevensmodellen. Met deze services kunt u het adaptieve formulier vooraf invullen en verzonden formuliergegevens terugschrijven naar het gegevensmodelobject.

Zie [AEM Forms Data Integration](../../forms/using/data-integration.md)voor meer informatie over de integratie van formuliergegevens en het formuliergegevensmodel.

Deze zelfstudie begeleidt u door de stappen voor het voorbereiden, maken, configureren en koppelen van een formuliergegevensmodel aan een adaptief formulier. Aan het einde van deze zelfstudie kunt u het volgende doen:

* [MySQL-database configureren als gegevensbron](#config-database)
* [Formuliergegevensmodel maken met MySQL-database](#create-fdm)
* [Formuliergegevensmodel configureren](#config-fdm)
* [Formuliergegevensmodel testen](#test-fdm)

Het formuliergegevensmodel ziet er ongeveer als volgt uit:

![form-data-model_l](assets/form-data-model_l.png)

**********A. Gevormde gegevensbronnen** B. Gegevensbronschema&#39;s **C.** Beschikbare diensten **D. Gegevensmodelobjecten** E. Gevormde services

## Vereisten {#prerequisites}

Voordat u begint, moet u het volgende doen:

* MySQL-database met voorbeeldgegevens zoals vermeld in de sectie Voorwaarden van [Create your first adaptive form](../../forms/using/create-your-first-adaptive-form.md)
* OSGi-bundel voor MySQL JDBC-stuurprogramma, zoals wordt uitgelegd in [Bundling the JDBC Database Driver](/help/sites-developing/jdbc.md#bundling-the-jdbc-database-driver)
* Adaptief formulier zoals uitgelegd in de eerste zelfstudie Een adaptief formulier [maken](/help/forms/using/create-adaptive-form.md)

## Stap 1: MySQL-database configureren als gegevensbron {#config-database}

U kunt verschillende typen gegevensbronnen configureren om een formuliergegevensmodel te maken. Voor dit leerprogramma, zullen wij het gegevensbestand vormen MySQL dat u met steekproefgegevens vormde en bevolkt. Voor informatie over andere gesteunde gegevensbronnen en hoe te om hen te vormen, zie de Integratie [van de Gegevens van](../../forms/using/data-integration.md)Vormen AEM.

Ga als volgt te werk om uw MySQL-database te configureren:

1. Installeer het JDBC-stuurprogramma voor MySQL-database als een OSGi-bundel:

   1. Meld u als beheerder aan bij AEM Forms Author Instance en ga naar AEM-webconsolesbundels. De standaard-URL is [https://localhost:4502/system/console/bundles](https://localhost:4502/system/console/bundles).

   1. Tik op **Installeren/bijwerken**. Het dialoogvenster **Bundels** uploaden/installeren wordt weergegeven.

   1. Tik op Bestand **** kiezen om door de OSGi-bundel van het MySQL-stuurprogramma te bladeren en deze te selecteren. Selecteer **Bundel** starten en Pakketten **** vernieuwen en tik op **Installeren of Bijwerken**. Zorg ervoor dat het JDBC-stuurprogramma voor MySQL van Oracle Corporation actief is. Het stuurprogramma is geïnstalleerd.

1. MySQL-database configureren als gegevensbron:

   1. Ga naar AEM-webconsole op [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr).
   1. Zoek de configuratie **van Apache Sling Connection Pooled DataSource** . Tik om de configuratie te openen in de bewerkingsmodus.
   1. Geef in het dialoogvenster Configuratie de volgende gegevens op:

      * **** Naam gegevensbron: U kunt elke gewenste naam opgeven. Geef bijvoorbeeld **WeRetailMySQL** op.
      * **Naam** van de de diensteigenschap DataSource: Specificeer naam van het de dienstbezit die de naam DataSource bevat. Het wordt gespecificeerd terwijl het registreren van de gegevensbroninstantie als dienst OSGi. Bijvoorbeeld, **datasource.name**.
      * **JDBC-stuurprogrammaklasse**: Geef de Java-klassenaam van het JDBC-stuurprogramma op. Geef voor MySQL-database **com.mysql.jdbc.Driver** op.
      * **URI** JDBC-verbinding: Geef de verbindings-URL van de database op. Voor MySQL-database die wordt uitgevoerd op poort 3306 en schema weretail, is de URL: `jdbc:mysql://[server]:3306/weretail?autoReconnect=true&useUnicode=true&characterEncoding=utf-8`
      * **** Gebruikersnaam: Gebruikersnaam van de database. Het is vereist om JDBC-stuurprogramma in staat te stellen een verbinding met de database tot stand te brengen.
      * **** Wachtwoord: Wachtwoord van de database. Het is vereist om JDBC-stuurprogramma in staat te stellen een verbinding met de database tot stand te brengen.
      * **** Testen op lenen: Schakel de optie **Testen op lening** in.
      * **** Testen op rendement: Schakel de optie **Testen op terugkeer** in.
      * **** Validatiezoekopdracht: Geef een SQL SELECT-query op om verbindingen vanuit de pool te valideren. De query moet ten minste één rij retourneren. Bijvoorbeeld, **selecteer * van douanedetails**.
      * **Transactieisolatie**: Stel de waarde in op **READ_COMTED**.
      Laat andere eigenschappen de [standaardwaarden](https://tomcat.apache.org/tomcat-7.0-doc/jdbc-pool.html) behouden en tik op **Opslaan**.
   Er wordt een configuratie gemaakt die lijkt op de volgende configuratie.

   ![relationele database-data-source-configuration](assets/relational-database-data-source-configuration.png)

## Stap 2:Formuliergegevensmodel maken {#create-fdm}

AEM Forms biedt een intuïtieve gebruikersinterface voor het [maken van een](../../forms/using/data-integration.md#main-pars-header-1524967585)formuliergegevensmodel op basis van geconfigureerde gegevensbronnen. U kunt meerdere gegevensbronnen gebruiken in een formuliergegevensmodel. Voor ons gebruiksgeval, zullen wij de gevormde gegevensbron gebruiken MySQL.

Ga als volgt te werk om het formuliergegevensmodel te maken:

1. Navigeer in de auteur van AEM naar **Forms** > **Gegevensintegratie**.
1. Tik op **Maken** > **Formuliergegevensmodel**.
1. Geef in het dialoogvenster Formuliergegevensmodel een **naam** op voor het formuliergegevensmodel. Bijvoorbeeld **klant-verzend-facturerings-details**. Tik op **Volgende**.
1. Het uitgezochte scherm van gegevensbron maakt een lijst van alle gevormde gegevensbronnen. Selecteer **WeRetailMySQL** -gegevensbron en tik op **Maken**.

   ![gegevensbron-selectie](assets/data-source-selection.png)

Het gegevensmodel voor **klantverzendgegevens** wordt gemaakt.

## Stap 3: Formuliergegevensmodel configureren {#config-fdm}

Het configureren van het formuliergegevensmodel omvat:

* toevoegen, gegevensmodelobject en -services
* het vormen lees en schrijf de diensten voor de voorwerpen van het gegevensmodel

Voer de volgende handelingen uit om het formuliergegevensmodel te configureren:

1. Navigeer in de auteur van AEM naar **Forms** > **Gegevensintegratie**. De standaard-URL is [https://localhost:4502/aem/forms.html/content/dam/formsanddocuments-fdm](https://localhost:4502/aem/forms.html/content/dam/formsanddocuments-fdm).
1. Hier wordt het formuliergegevensmodel weergegeven dat u eerder hebt gemaakt en waarin de **klant gegevens over** de facturering opgeeft. Open het in bewerkingsmodus.

   De geselecteerde gegevensbron **WeRetailMySQL** wordt gevormd in het model van vormgegevens.

   ![default-fdm](assets/default-fdm.png)

1. Vouw de WebRailMySQL-gegevensbronstructuur uit. Selecteer de volgende gegevensmodelobjecten en -services van **Origineel** > **details** -schema voor de klant naar het formuliergegevensmodel:

   * **Objecten** gegevensmodel:

      * id
      * name
      * ShippingAddress
      * stad
      * state
      * postcode
   * **Services:**

      * get
      * update
   Tik op Geselecteerde **gegevensmodelobjecten en -services** toevoegen aan het formuliergegevensmodel.

   ![WeRetail-schema](assets/weretail_schema_new.png)

   >[!NOTE]
   >
   >De standaard krijgt, update, en neemt de diensten voor JDBC- gegevensbronnen op uit-van-de-doos met het model van vormgegevens.

1. Configureer lees- en schrijfservices voor het gegevensmodelobject.

   1. Selecteer het **gegevensmodelobject voor de klantgegevens** en tik op Eigenschappen **** bewerken.
   1. Selecteer **krijgen** van de Gelezen drop-down Dienst. Het **id** -argument, de primaire sleutel in het gegevensmodel van de klant, wordt automatisch toegevoegd. Tik op ![name_6_3_edit](assets/aem_6_3_edit.png) en configureer het argument als volgt.

      ![standaard lezen](assets/read-default.png)

   1. Op dezelfde manier selecteer **update** als de Write Dienst. Het object **customerdetails** wordt automatisch als een argument toegevoegd. Het argument is als volgt geconfigureerd.

      ![standaard schrijven](assets/write-default.png)

      Voeg als volgt het argument **id** toe en vorm.

      ![id-arg](assets/id-arg.png)

   1. Tik op **Gereed** om de objecteigenschappen van het gegevensmodel op te slaan. Tik vervolgens op **Opslaan** om het formuliergegevensmodel op te slaan.

      De **ophalen** en **bijwerken** services worden toegevoegd als standaardservices voor het gegevensmodelobject.

      ![data-model-object](assets/data-model-object.png)

1. Ga naar het tabblad **Services** en configureer **get** - en **updateservices** .

   1. Selecteer de **get** service en tik op Eigenschappen **** bewerken. Het dialoogvenster Eigenschappen wordt geopend.
   1. Geef het volgende op in het dialoogvenster Eigenschappen bewerken:

      * **Titel**: Geef de titel van de service op. Bijvoorbeeld: Verzendadres ophalen.
      * **Omschrijving**: Geef een beschrijving op met een gedetailleerde werking van de service. Bijvoorbeeld:

         Deze service haalt het verzendadres en andere klantgegevens op uit MySQL-database

      * **Uitvoermodelobject**: Selecteer schema met klantgegevens. Bijvoorbeeld:

         customerdetail-schema

      * **Retourarray**: Schakel de optie **Retourarray** uit.
      * **Argumenten**: Selecteer een argument met de naam **ID**.
      Tik **op Gereed**. De dienst om klantendetails van het gegevensbestand terug te winnen MySQL wordt gevormd.

      ![verzendadres-herwinning](assets/shiiping-address-retrieval.png)

   1. Selecteer de **updateservice** en tik op **Eigenschappen** bewerken. Het dialoogvenster Eigenschappen wordt geopend.

   1. Geef het volgende op in het dialoogvenster Eigenschappen bewerken:

      * **Titel**: Geef de titel van de service op. Bijvoorbeeld Verzendadres bijwerken.
      * **Omschrijving**: Geef een beschrijving op met een gedetailleerde werking van de service. Bijvoorbeeld:

         Deze service werkt het verzendadres en verwante velden in de MySQL-database bij

      * **Invoermodelobject**: Selecteer schema met klantgegevens. Bijvoorbeeld:

         customerdetail-schema

      * **Uitvoertype**: Selecteer **BOOLEAN**.

      * **Argumenten**: Selecteer een argument met de naam **ID** en **klantgegevens**.
      Tik **op Gereed**. De **updateservice** om klantendetails in het gegevensbestand bij te werken MySQL wordt gevormd.

      ![send-address-update](assets/shiiping-address-update.png)



Het gegevensmodelvoorwerp en de diensten in het model van vormgegevens worden gevormd. U kunt nu het formuliergegevensmodel testen.

## Stap 4: Formuliergegevensmodel testen {#test-fdm}

U kunt het gegevensmodelobject en de services testen om te controleren of het formuliergegevensmodel correct is geconfigureerd.

Voer de volgende handelingen uit om de test uit te voeren:

1. Ga naar het tabblad **Model** , selecteer het **gegevensmodelobject CustomDetails** en tik op **Testmodelobject**.
1. Selecteer in het venster **Testmodel/service** de optie **Model-object** lezen in de vervolgkeuzelijst **Selecteer model/service** .
1. In de sectie **customerdetails** , specificeer een waarde voor het **id** argument dat in het gevormde gegevensbestand MySQL bestaat en tikt **Test**.

   De klantgegevens die aan de opgegeven id zijn gekoppeld, worden opgehaald en weergegeven in de sectie **Uitvoer** , zoals hieronder wordt weergegeven.

   ![testmodel](assets/test-read-model.png)

1. Op dezelfde manier kunt u het Schrijven modelvoorwerp en de diensten testen.

   In het volgende voorbeeld werkt de updateservice de adresgegevens voor de id 7102715 in de database bij.

   ![test-schrijven-model](assets/test-write-model.png)

   Nu, als u de gelezen modeldienst opnieuw voor identiteitskaart 7107215 test, zal het de bijgewerkte klantendetails terugwinnen en tonen zoals hieronder getoond.

   ![lezen-bijgewerkt](assets/read-updated.png)
