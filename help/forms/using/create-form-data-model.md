---
title: "Zelfstudie: Formuliergegevensmodel maken "
seo-title: Create Form Data Model Tutorial
description: Formuliergegevensmodel maken
seo-description: Create form data model
uuid: b9d2bb1b-90f0-44f4-b1e3-0603cdf5f5b8
contentOwner: khsingh
products: SG_EXPERIENCEMANAGER/6.3/FORMS
discoiquuid: 12e6c325-ace0-4a57-8ed4-6f7ceee23099
docset: aem65
exl-id: 40bc5af6-9023-437e-95b0-f85d3df7d8aa
source-git-commit: c3178eefb5aca3afea2f3df8381b52461247d6f3
workflow-type: tm+mt
source-wordcount: '1448'
ht-degree: 1%

---

# Zelfstudie: Formuliergegevensmodel maken {#tutorial-create-form-data-model}

![04-create-form-data-model-main](assets/04-create-form-data-model-main.png)

Deze zelfstudie is een stap in de [Uw eerste adaptieve formulier maken](../../forms/using/create-your-first-adaptive-form.md) reeks. U wordt aangeraden de reeks in chronologische volgorde te volgen om het volledige gebruik van de zelfstudie te begrijpen, uit te voeren en aan te tonen.

## Over de zelfstudie {#about-the-tutorial}

AEM [!DNL Forms] Met de module voor gegevensintegratie kunt u een formuliergegevensmodel maken op basis van verschillende bronnen van back-endgegevens, zoals AEM gebruikersprofiel, RESTful-webservices, SOAP-webservices, OData-services en relationele databases. U kunt gegevensmodelobjecten en -services configureren in een formuliergegevensmodel en deze koppelen aan een adaptief formulier. Adaptieve formuliervelden zijn gebonden aan objecteigenschappen van gegevensmodellen. Met deze services kunt u het adaptieve formulier vooraf invullen en verzonden formuliergegevens terugschrijven naar het gegevensmodelobject.

Voor meer informatie over de integratie van formuliergegevens en het formuliergegevensmodel raadpleegt u [AEM Forms-gegevensintegratie](../../forms/using/data-integration.md).

Deze zelfstudie begeleidt u door de stappen voor het voorbereiden, maken, configureren en koppelen van een formuliergegevensmodel aan een adaptief formulier. Aan het einde van deze zelfstudie kunt u het volgende doen:

* [MySQL-database configureren als gegevensbron](#config-database)
* [Formuliergegevensmodel maken met MySQL-database](#create-fdm)
* [Formuliergegevensmodel configureren](#config-fdm)
* [Formuliergegevensmodel testen](#test-fdm)

Het formuliergegevensmodel ziet er ongeveer als volgt uit:

![form-data-model_l](assets/form-data-model_l.png)

**A.** Gevormde gegevensbronnen **B.** Gegevensbronschema&#39;s **C.** Beschikbare services **D.** Gegevensmodelobjecten **E.** Gevormde services

## Vereisten {#prerequisites}

Voordat u begint, moet u het volgende doen:

* [!DNL MySQL] database met voorbeeldgegevens zoals vermeld in de sectie Voorwaarden van [Uw eerste adaptieve formulier maken](../../forms/using/create-your-first-adaptive-form.md)
* OSGi-bundel voor [!DNL MySQL] JDBC-stuurprogramma zoals wordt uitgelegd in [Het JDBC-databasestuurprogramma bundelen](/help/sites-developing/jdbc.md#bundling-the-jdbc-database-driver)
* Adaptief formulier, zoals uitgelegd in de eerste zelfstudie [Een adaptief formulier maken](/help/forms/using/create-adaptive-form.md)

## Stap 1: MySQL-database configureren als gegevensbron {#config-database}

U kunt verschillende typen gegevensbronnen configureren om een formuliergegevensmodel te maken. Voor dit leerprogramma, zullen wij het gegevensbestand vormen MySQL dat u met steekproefgegevens vormde en bevolkt. Voor informatie over andere gesteunde gegevensbronnen en hoe te om hen te vormen, zie [AEM Forms-gegevensintegratie](../../forms/using/data-integration.md).

Doe het volgende uw vormen [!DNL MySQL] database:

1. JDBC-stuurprogramma installeren voor [!DNL MySQL] database als een OSGi-bundel:

   1. Downloaden [[!DNL MySQL] JDBC Driver OSGi Bundle](http://www.java2s.com/ref/jar/download-orgosgiservicejdbc100jar-file.html).
   1. Aanmelden bij AEM [!DNL Forms] Instantie van auteur als beheerder en ga naar AEM bundels van de Webconsole. De standaard-URL is [https://localhost:4502/system/console/bundles](https://localhost:4502/system/console/bundles).

   1. Tik op **[!UICONTROL Install/Update]**. An [!UICONTROL Upload / Install Bundles] wordt weergegeven.

   1. Tikken **[!UICONTROL Choose File]** om te bladeren en selecteren [!DNL MySQL] JDBC-stuurprogramma OSGi-bundel. Selecteren **[!UICONTROL Start Bundle]** en **[!UICONTROL Refresh Packages]** en tikken **[!UICONTROL Install or Update]**. Zorg ervoor dat de [!DNL Oracle Corporation's] JDBC-stuurprogramma voor [!DNL MySQL] is actief. Het stuurprogramma is geïnstalleerd.

1. Configureren [!DNL MySQL] database als gegevensbron:

   1. Ga naar AEM webconsole op [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr).
   1. Zoeken **Apache Sling Connection Pooled DataSource** configuratie. Tik om de configuratie te openen in de bewerkingsmodus.
   1. Geef in het dialoogvenster Configuratie de volgende gegevens op:

      * **Naam gegevensbron:** U kunt elke gewenste naam opgeven. Geef bijvoorbeeld **WeRetailMySQL**.
      * **Eigenschapnaam van DataSource-service**: Specificeer naam van het de dienstbezit die de naam DataSource bevat. Het wordt gespecificeerd terwijl het registreren van de gegevensbroninstantie als dienst OSGi. Bijvoorbeeld: **datasource.name**.
      * **JDBC-stuurprogrammaklasse**: Geef de Java-klassenaam van het JDBC-stuurprogramma op. Voor [!DNL MySQL] database, specificeren **com.mysql.jdbc.Driver**.
      * **URI voor JDBC-verbinding**: Geef de verbindings-URL van de database op. Voor [!DNL MySQL] database die wordt uitgevoerd op poort 3306 en schema weretail, is de URL: `jdbc:mysql://'server':3306/weretail?autoReconnect=true&useUnicode=true&characterEncoding=utf-8`

      >[!NOTE]
      >
      > Wanneer de [!DNL MySQL] database bevindt zich achter een firewall, maar de hostnaam van de database is geen openbare DNS. IP adres van het gegevensbestand moet in worden toegevoegd */etc/hosts* bestand van de AEM hostcomputer.

      * **Gebruikersnaam:** Gebruikersnaam van de database. Het is vereist om JDBC-stuurprogramma in staat te stellen een verbinding met de database tot stand te brengen.
      * **Wachtwoord:** Wachtwoord van de database. Het is vereist om JDBC-stuurprogramma in staat te stellen een verbinding met de database tot stand te brengen.

      >[!NOTE]
      >
      >AEM Forms biedt geen ondersteuning voor NT-verificatie voor [!DNL MySQL]. Ga naar AEM webconsole op [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr) en zoek &quot;Apache Sling Connection Pooled Datasource&quot;.Voor de eigenschap &quot;JDBC connection URI&quot; stelt u de waarde van &quot;IntegratedSecurity&quot; in als Onwaar en gebruikt u de gemaakte gebruikersnaam en het wachtwoord voor verbinding met [!DNL MySQL] database.

      * **Testen op lenen:** De optie **[!UICONTROL Test on Borrow]** optie.
      * **Testen op rendement:** De optie **[!UICONTROL Test on Return]** optie.
      * **Validatiezoekopdracht:** Geef een SQL SELECT-query op om verbindingen vanuit de pool te valideren. De query moet ten minste één rij retourneren. Bijvoorbeeld: **selecteren &#42; van klantgegevens**.
      * **Transactieisolatie**: Stel de waarde in op **READ_COMTED**.

         Andere eigenschappen standaard laten staan [waarden](https://tomcat.apache.org/tomcat-7.0-doc/jdbc-pool.html) en tikken **[!UICONTROL Save]**.

         Er wordt een configuratie gemaakt die lijkt op de volgende configuratie.

         ![relationele database-data-source-configuration](assets/relational-database-data-source-configuration.png)



## Stap 2: Formuliergegevensmodel maken {#create-fdm}

AEM [!DNL Forms] biedt een intuïtieve gebruikersinterface voor [een formuliergegevensmodel maken](data-integration.md) van gevormde gegevensbronnen. U kunt meerdere gegevensbronnen gebruiken in een formuliergegevensmodel. Voor ons gebruiksgeval, zullen wij gevormd gebruiken [!DNL MySQL] gegevensbron.

Ga als volgt te werk om het formuliergegevensmodel te maken:

1. Navigeer in AEM auteurinstantie naar **[!UICONTROL Forms]** > **[!UICONTROL Data Integrations]**.
1. Tik op **[!UICONTROL Create]** > **[!UICONTROL Form Data Model]**.
1. Geef in het dialoogvenster Formuliergegevensmodel maken een **name** voor het formuliergegevensmodel. Bijvoorbeeld: **klant-verzend-facturerings-details**. Tik op **[!UICONTROL Next]**.
1. Het uitgezochte scherm van gegevensbron maakt een lijst van alle gevormde gegevensbronnen. Selecteren **WeRetailMySQL** gegevensbron en tik **[!UICONTROL Create]**.

   ![gegevensbron-selectie](assets/data-source-selection.png)

De **klant-verzend-facturerings-details** formuliergegevensmodel wordt gemaakt.

## Stap 3: Formuliergegevensmodel configureren {#config-fdm}

Het configureren van het formuliergegevensmodel omvat:

* toevoegen, gegevensmodelobject en -services
* het vormen lees en schrijf de diensten voor de voorwerpen van het gegevensmodel

Voer de volgende handelingen uit om het formuliergegevensmodel te configureren:

1. Navigeer bij AEM instantie van de auteur naar **[!UICONTROL Forms]** > **[!UICONTROL Data Integrations]**. De standaard-URL is [https://localhost:4502/aem/forms.html/content/dam/formsanddocuments-fdm](https://localhost:4502/aem/forms.html/content/dam/formsanddocuments-fdm).
1. De **klant-verzend-facturerings-details** Hier wordt het formuliergegevensmodel weergegeven dat u eerder hebt gemaakt. Open het in bewerkingsmodus.

   De geselecteerde gegevensbron **WeRetailMySQL** is geconfigureerd in het formuliergegevensmodel.

   ![default-fdm](assets/default-fdm.png)

1. Vouw de WebRailMySQL-gegevensbronstructuur uit. Selecteer de volgende gegevensmodelvoorwerpen en de diensten van **wieg** > **klantgegevens** schema naar formuliergegevensmodel:

   * **Gegevensmodelobjecten**:

      * id
      * name
      * ShippingAddress
      * stad
      * state
      * postcode
   * **Services:**

      * get
      * update

   Tikken **Geselecteerde toevoegen** Hiermee voegt u geselecteerde gegevensmodelobjecten en -services toe aan het formuliergegevensmodel.

   ![WeRetail-schema](assets/weretail_schema_new.png)

   >[!NOTE]
   >
   >De standaard krijgt, update, en neemt de diensten voor JDBC- gegevensbronnen op uit-van-de-doos met het model van vormgegevens.

1. Configureer lees- en schrijfservices voor het gegevensmodelobject.

   1. Selecteer **klantgegevens** gegevensmodelobject en tik **[!UICONTROL Edit Properties]**.
   1. Selecteren **[!UICONTROL get]** in de vervolgkeuzelijst Leesservice. De **id** argument, de primaire sleutel in het gegevensmodelobject van de klant is, wordt automatisch toegevoegd. Tikken ![aem_6_3_edit](assets/aem_6_3_edit.png) en configureer het argument als volgt.

      ![standaard lezen](assets/read-default.png)

   1. Selecteer op dezelfde manier **[!UICONTROL update]** als de schrijfservice. De **klantgegevens** object automatisch als een argument toegevoegd. Het argument is als volgt geconfigureerd.

      ![standaard schrijven](assets/write-default.png)

      Voeg en vorm toe **id** als volgt.

      ![id-arg](assets/id-arg.png)

   1. Tikken **[!UICONTROL Done]** om de objecteigenschappen van het gegevensmodel op te slaan. Tik vervolgens op **[!UICONTROL Save]** om het formuliergegevensmodel op te slaan.

      De **[!UICONTROL get]** en **[!UICONTROL update]** de diensten worden toegevoegd als standaarddiensten voor het voorwerp van het gegevensmodel.

      ![data-model-object](assets/data-model-object.png)

1. Ga naar de **[!UICONTROL Services]** tab en configure **[!UICONTROL get]** en **[!UICONTROL update]** diensten.

   1. Selecteer **[!UICONTROL get]** service en tikken **[!UICONTROL Edit Properties]**. Het dialoogvenster Eigenschappen wordt geopend.
   1. Geef het volgende op in het dialoogvenster Eigenschappen bewerken:

      * **Titel**: Geef de titel van de service op. Bijvoorbeeld: Verzendadres ophalen.
      * **Beschrijving**: Geef een beschrijving op met een gedetailleerde werking van de service. Bijvoorbeeld:

         Deze service haalt het verzendadres en andere klantgegevens op van [!DNL MySQL] database

      * **Uitvoermodelobject**: Selecteer schema met klantgegevens. Bijvoorbeeld:

         customerdetail-schema

      * **Retourarray**: De opdracht **Retourarray** optie.
      * **Argumenten**: Benoemd argument selecteren **ID**.

      Tik op **[!UICONTROL Done]**. De dienst om klantendetails van het gegevensbestand terug te winnen MySQL wordt gevormd.

      ![verzendadres-herwinning](assets/shiiping-address-retrieval.png)

   1. Selecteer **[!UICONTROL update]** service en tikken **[!UICONTROL Edit Properties]**. Het dialoogvenster Eigenschappen wordt geopend.

   1. Geef het volgende op in het dialoogvenster [!UICONTROL Edit Properties] dialoogvenster:

      * **Titel**: Geef de titel van de service op. Bijvoorbeeld Verzendadres bijwerken.
      * **Beschrijving**: Geef een beschrijving op met een gedetailleerde werking van de service. Bijvoorbeeld:

         Deze service werkt het verzendadres en verwante velden in de MySQL-database bij

      * **Invoermodelobject**: Selecteer schema met klantgegevens. Bijvoorbeeld:

         customerdetail-schema

      * **Uitvoertype**: Selecteren **BOOLEAN**.

      * **Argumenten**: Benoemd argument selecteren **ID** en **klantgegevens**.
      Tik op **[!UICONTROL Done]**. De **[!UICONTROL update]** service voor het bijwerken van klantgegevens in de [!DNL MySQL] database is geconfigureerd.

      ![send-address-update](assets/shiiping-address-update.png)



Het gegevensmodelvoorwerp en de diensten in het model van vormgegevens worden gevormd. U kunt nu het formuliergegevensmodel testen.

## Stap 4: Formuliergegevensmodel testen {#test-fdm}

U kunt het gegevensmodelobject en de services testen om te controleren of het formuliergegevensmodel correct is geconfigureerd.

Voer de volgende handelingen uit om de test uit te voeren:

1. Ga naar de **[!UICONTROL Model]** selecteert u de **klantgegevens** gegevensmodelobject en tik **[!UICONTROL Test Model Object]**.
1. In de [!UICONTROL Test Model/Service] venster, selecteert u **[!UICONTROL Read model object]** van de **[!UICONTROL Select Model/Service]** vervolgkeuzelijst.
1. In de **klantgegevens** -sectie, geeft u een waarde op voor de **id** argument dat in gevormd bestaat [!DNL MySQL] database en tik **[!UICONTROL Test]**.

   De klantgegevens die aan opgegeven id zijn gekoppeld, worden opgehaald en weergegeven in het dialoogvenster **[!UICONTROL Output]** zoals hieronder weergegeven.

   ![testmodel](assets/test-read-model.png)

1. Op dezelfde manier kunt u het Schrijven modelvoorwerp en de diensten testen.

   In het volgende voorbeeld werkt de updateservice de adresgegevens voor de id 7102715 in de database bij.

   ![test-schrijven-model](assets/test-write-model.png)

   Nu, als u de gelezen modeldienst opnieuw voor identiteitskaart 7107215 test, zal het de bijgewerkte klantendetails terugwinnen en tonen zoals hieronder getoond.

   ![lezen-bijgewerkt](assets/read-updated.png)
