---
title: "Zelfstudie: Formuliergegevensmodel maken"
description: Leer hoe u MySQL als gegevensbron configureert, FDM (form data model) maakt, configureert en test voor AEM Forms.
contentOwner: khsingh
products: SG_EXPERIENCEMANAGER/6.3/FORMS
docset: aem65
exl-id: 40bc5af6-9023-437e-95b0-f85d3df7d8aa
solution: Experience Manager, Experience Manager Forms
feature: Form Data Model
role: Admin, User, Developer
source-git-commit: 539da06db98395ae6eaee8103a3e4b31204abbb8
workflow-type: tm+mt
source-wordcount: '1463'
ht-degree: 0%

---

# Zelfstudie: Formuliergegevensmodel maken {#tutorial-create-form-data-model}

![04-create-form-data-model-main](assets/04-create-form-data-model-main.png)

Deze zelfstudie is een stap in de [Uw eerste adaptieve formulier maken](../../forms/using/create-your-first-adaptive-form.md) reeks. De Adobe raadt u aan de reeks in chronologische volgorde te volgen om de volledige Gebruikszaak van de zelfstudie te begrijpen, uit te voeren en te demonstreren.

## Over de zelfstudie {#about-the-tutorial}

AEM [!DNL Forms] Met de module voor gegevensintegratie kunt u een formuliergegevensmodel maken op basis van verschillende bronnen met back-endgegevens, zoals AEM gebruikersprofiel, RESTful-webservices, SOAP webservices, OData-services en relationele databases. U kunt gegevensmodelobjecten en -services configureren in een formuliergegevensmodel en deze koppelen aan een adaptief formulier. Adaptieve formuliervelden zijn gebonden aan objecteigenschappen van gegevensmodellen. Met deze services kunt u het adaptieve formulier vooraf invullen en verzonden formuliergegevens terugschrijven naar het gegevensmodelobject.

Zie voor meer informatie over de integratie van formuliergegevens en het formuliergegevensmodel [AEM Forms-gegevensintegratie](../../forms/using/data-integration.md).

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

## Stap 1: Vorm MySQL gegevensbestand als gegevensbron {#config-database}

U kunt verschillende typen gegevensbronnen configureren om een formuliergegevensmodel te maken. Voor deze zelfstudie configureert u de MySQL-database die u hebt geconfigureerd en gevuld met voorbeeldgegevens. Voor informatie over andere gesteunde gegevensbronnen en hoe te om hen te vormen, zie [AEM Forms-gegevensintegratie](../../forms/using/data-integration.md).

Doe het volgende uw vormen [!DNL MySQL] database:

1. JDBC-stuurprogramma installeren voor [!DNL MySQL] database als een OSGi-bundel:

   1. Downloaden [!DNL MySQL] JDBC Driver OSGi Bundle van `http://www.java2s.com/ref/jar/download-orgosgiservicejdbc100jar-file.html`. <!-- This URL is an insecure link but using https is not possible -->
   1. Meld u aan bij AEM [!DNL Forms] Author Instance als beheerder en ga naar bundels met AEM-webconsoles. De standaard-URL is [https://localhost:4502/system/console/bundles](https://localhost:4502/system/console/bundles).

   1. Selecteer **[!UICONTROL Install/Update]**. Er wordt een [!UICONTROL Upload / Install Bundles] dialoogvenster weergegeven.

   1. Selecteren **[!UICONTROL Choose File]** om te bladeren en selecteren [!DNL MySQL] JDBC-stuurprogramma OSGi-bundel. Selecteren **[!UICONTROL Start Bundle]** en **[!UICONTROL Refresh Packages]** en selecteert u **[!UICONTROL Install or Update]**. Zorg ervoor dat de [!DNL Oracle Corporation's] JDBC-stuurprogramma voor [!DNL MySQL] is actief. Het stuurprogramma is geïnstalleerd.

1. Configureren [!DNL MySQL] database als gegevensbron:

   1. Ga naar AEM webconsole op [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr).
   1. Zoeken **Apache Sling Connection Pooled DataSource** configuratie. Selecteer deze optie om de configuratie te openen in de bewerkingsmodus.
   1. Geef in het dialoogvenster Configuratie de volgende gegevens op:

      * **Naam gegevensbron:** U kunt elke gewenste naam opgeven. Geef bijvoorbeeld **WeRetailMySQL**.
      * **Eigenschapnaam van DataSource-service**: Geef een naam op van de eigenschap service die de naam DataSource bevat. Het wordt gespecificeerd terwijl het registreren van de gegevensbroninstantie als dienst OSGi. Bijvoorbeeld: **datasource.name**.
      * **JDBC-stuurprogrammaklasse**: Geef de Java™-klassenaam van het JDBC-stuurprogramma op. Geef [!DNL MySQL] **voor database com.mysql.jdbc.Driver op**.
      * **URI voor JDBC-verbinding**: Geef de verbindings-URL van de database op. Voor [!DNL MySQL] database die wordt uitgevoerd op poort 3306 en schema `weretail`, is de URL: `jdbc:mysql://'server':3306/weretail?autoReconnect=true&useUnicode=true&characterEncoding=utf-8`

      >[!NOTE]
      >
      > Wanneer de [!DNL MySQL] database bevindt zich achter een firewall, maar de hostnaam van de database is geen openbare DNS. Het IP-adres van de database moet worden toegevoegd aan het */etc/hosts-bestand* van de AEM-hostcomputer.

      * **Gebruikersnaam:** Gebruikersnaam van de database. U moet het JDBC-stuurprogramma inschakelen om een verbinding met de database tot stand te brengen.
      * **Wachtwoord:** Wachtwoord van de database. Het is vereist om JDBC-stuurprogramma in staat te stellen een verbinding met de database tot stand te brengen.

      >[!NOTE]
      >
      >AEM Forms ondersteunt geen NT-verificatie voor [!DNL MySQL]. Ga naar AEM webconsole op [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr) en zoek &quot;Apache Sling Connection Pooled Datasource&quot;. Voor de eigenschap &quot;JDBC connection URI&quot; stelt u de waarde van &quot;IntegratedSecurity&quot; in op False en gebruikt u de gemaakte gebruikersnaam en het wachtwoord voor verbinding met [!DNL MySQL] database.

      * **Testen op lenen:** De optie **[!UICONTROL Test on Borrow]** -optie.
      * **Testen op rendement:** De optie **[!UICONTROL Test on Return]** -optie.
      * **Validatiezoekopdracht:** Geef een SQL SELECT-query op om verbindingen vanuit de pool te valideren. De query moet ten minste één rij retourneren. Bijvoorbeeld: **selecteren &#42; van klantgegevens**.
      * **Transactieisolatie**: Stel de waarde in op **READ_COMTED**.

        Andere eigenschappen standaard laten staan [waarden](https://tomcat.apache.org/tomcat-7.0-doc/jdbc-pool.html) en selecteert u **[!UICONTROL Save]**.

        Er wordt een configuratie gemaakt die lijkt op de volgende configuratie.

        ![relationele database-data-source-configuration](assets/relational-database-data-source-configuration.png)

## Stap 2: Formuliergegevensmodel maken {#create-fdm}

AEM [!DNL Forms] biedt een intuïtieve gebruikersinterface om een formuliergegevensmodel](data-integration.md) te [maken op basis van geconfigureerde gegevensbronnen. U kunt meerdere gegevensbronnen in een formuliergegevensmodel gebruiken. In dit geval kunt u de geconfigureerde [!DNL MySQL] gegevensbron gebruiken.

Ga als volgt te werk om een formuliergegevensmodel te maken:

1. Navigeer in AEM auteurinstantie naar **[!UICONTROL Forms]** > **[!UICONTROL Data Integrations]**.
1. Selecteren **[!UICONTROL Create]** > **[!UICONTROL Form Data Model]**.
1. Geef in het dialoogvenster Formuliergegevensmodel maken een **name** voor het formuliergegevensmodel. Bijvoorbeeld: **klant-verzendkosten-factureringsgegevens**. Selecteren **[!UICONTROL Next]**.
1. Het uitgezochte scherm van gegevensbron maakt een lijst van alle gevormde gegevensbronnen. Selecteren **WeRetailMySQL** gegevensbron en selecteer **[!UICONTROL Create]**.

   ![gegevensbron-selectie](assets/data-source-selection.png)

De **klant-verzendkosten-factureringsgegevens** formuliergegevensmodel wordt gemaakt.

## Stap 3: Formuliergegevensmodel configureren {#config-fdm}

Het configureren van het formuliergegevensmodel omvat:

* toevoegen, gegevensmodelobject en -services
* het vormen lees en schrijf de diensten voor de voorwerpen van het gegevensmodel

Voer de volgende handelingen uit om het formuliergegevensmodel te configureren:

1. Navigeer in AEM auteurinstantie naar **[!UICONTROL Forms]** > **[!UICONTROL Data Integrations]**. De standaard-URL is [https://localhost:4502/aem/forms.html/content/dam/formsanddocuments-fdm](https://localhost:4502/aem/forms.html/content/dam/formsanddocuments-fdm).
1. De **klant-verzendkosten-factureringsgegevens** Hier wordt het formuliergegevensmodel weergegeven dat u eerder hebt gemaakt. Open het in de bewerkingsmodus.

   De geselecteerde gegevensbron **WeRetailMySQL** is geconfigureerd in het formuliergegevensmodel.

   ![default-fdm](assets/default-fdm.png)

1. Vouw de WebRailMySQL-gegevensbronstructuur uit. Selecteer de volgende gegevensmodelvoorwerpen en de diensten van **wieg** > **klantgegevens** schema zodat u het gegevensmodel kunt vormen:

   * **Gegevensmodelobjecten**:

      * id
      * name
      * ShippingAddress
      * stad
      * state
      * postcode

   * **Diensten:**

      * Toevoegen
      * update

   Selecteren **Geselecteerde toevoegen** Hiermee voegt u geselecteerde gegevensmodelobjecten en -services toe aan het formuliergegevensmodel.

   ![WeRetail-schema](assets/weretail_schema_new.png)

   >[!NOTE]
   >
   >De standaard krijgt, update, en neemt de diensten voor JDBC- gegevensbronnen op uit-van-de-doos met het model van vormgegevens.

1. Configureer lees- en schrijfservices voor het gegevensmodelobject.

   1. Selecteer de **klantgegevens** gegevensmodelobject en selecteer **[!UICONTROL Edit Properties]**.
   1. Selecteren **[!UICONTROL get]** in de vervolgkeuzelijst Leesservice. De **id** argument, de primaire sleutel in het gegevensmodelobject van de klant is, wordt automatisch toegevoegd. Selecteren ![aem_6_3_edit](assets/aem_6_3_edit.png) en configureer het argument als volgt.

      ![standaard lezen](assets/read-default.png)

   1. Selecteer op dezelfde manier **[!UICONTROL update]** als de schrijfservice. De **klantgegevens** object automatisch als een argument toegevoegd. Het argument is als volgt geconfigureerd.

      ![standaard schrijven](assets/write-default.png)

      Voeg en vorm toe **id** als volgt.

      ![id-arg](assets/id-arg.png)

   1. Selecteren **[!UICONTROL Done]** om de eigenschappen van het gegevensmodel op te slaan. Selecteer **[!UICONTROL Save]** vervolgens om het formuliergegevensmodel op te slaan.

      De **[!UICONTROL get]** en **[!UICONTROL update]** services worden toegevoegd als standaardservices voor het gegevensmodelobject.

      ![data-model-object](assets/data-model-object.png)

1. Ga naar de **[!UICONTROL Services]** tab en configure **[!UICONTROL get]** en **[!UICONTROL update]** diensten.

   1. Selecteer de **[!UICONTROL get]** service en selecteer **[!UICONTROL Edit Properties]**. Het dialoogvenster Eigenschappen wordt geopend.
   1. Geef het volgende op in het dialoogvenster Eigenschappen bewerken:

      * **Titel**: Geef de titel van de service op. Bijvoorbeeld: Verzendadres ophalen.
      * **Beschrijving**: Geef een beschrijving op met een gedetailleerde werking van de service. Bijvoorbeeld:

        Met deze service haalt u het verzendadres en andere klantgegevens op van de [!DNL MySQL] database

      * **Uitvoermodelobject**: Selecteer een schema dat klantgegevens bevat. Bijvoorbeeld:

        klantdetailschema

      * **Retourarray**: Schakel het dialoogvenster **Retourarray** -optie.
      * **Argumenten**: selecteer het argument id ****.

      Selecteer **[!UICONTROL Done]**. De service voor het ophalen van klantgegevens uit de MySQL-database is geconfigureerd.

      ![verzendadres-herwinning](assets/shiiping-address-retrieval.png)

   1. Selecteer de **[!UICONTROL update]** service en selecteer **[!UICONTROL Edit Properties]**. Het dialoogvenster Eigenschappen wordt geopend.

   1. Geef het volgende op in het dialoogvenster [!UICONTROL Edit Properties] dialoogvenster:

      * **Titel**: Geef de titel van de service op. Bijvoorbeeld Verzendadres bijwerken.
      * **Beschrijving**: Geef een beschrijving op met een gedetailleerde werking van de service. Bijvoorbeeld:

        Deze service werkt het verzendadres en verwante velden in de MySQL-database bij

      * **Invoermodelobject**: Selecteer een schema dat klantgegevens bevat. Bijvoorbeeld:

        klantdetailschema

      * **Uitvoertype**: Select **BOOLEAN**.

      * **Argumenten**: Selecteer argumentnaam **ID** en **klantgegevens**.

      Selecteer **[!UICONTROL Done]**. De **[!UICONTROL update]** service voor het bijwerken van klantgegevens in de [!DNL MySQL] database is geconfigureerd.

      ![send-address-update](assets/shiiping-address-update.png)

Het gegevensmodelvoorwerp en de diensten in het model van vormgegevens worden gevormd. U kunt nu het formuliergegevensmodel testen.

## Stap 4: Model voor formuliergegevens testen {#test-fdm}

U kunt het gegevensmodelobject en de services testen om te controleren of het formuliergegevensmodel correct is geconfigureerd.

Voer de volgende handelingen uit om de test uit te voeren:

1. Ga naar de **[!UICONTROL Model]** selecteert u de **klantgegevens** gegevensmodelobject en selecteer **[!UICONTROL Test Model Object]**.
1. In de [!UICONTROL Test Model/Service] venster, selecteert u **[!UICONTROL Read model object]** van de **[!UICONTROL Select Model/Service]** vervolgkeuzelijst.
1. In de **klantgegevens** -sectie, geeft u een waarde op voor de **id** argument dat in gevormd bestaat [!DNL MySQL] database en selecteer **[!UICONTROL Test]**.

   De klantdetails verbonden aan gespecificeerde identiteitskaart worden gehaald en in getoond **[!UICONTROL Output]** zoals hieronder weergegeven.

   ![testmodel](assets/test-read-model.png)

1. Op dezelfde manier kunt u het Schrijven modelvoorwerp en de diensten testen.

   In het volgende voorbeeld werkt de updateservice de adresgegevens voor de id 7102715 in de database bij.

   ![test-schrijven-model](assets/test-write-model.png)

   Nu, als u de gelezen modeldienst opnieuw voor identiteitskaart 7107215 test, haalt het en toont de bijgewerkte klantendetails zoals hieronder getoond.

   ![lezen-bijgewerkt](assets/read-updated.png)


>[!NOTE]
>
> U kunt de configuratie SharePoint List maken en gebruiken met het formuliergegevensmodel in een adaptief formulier, om gegevens of gegenereerd document met record op te slaan in een SharePoint-lijst. Zie [Een adaptief formulier verbinden met de Microsoft® SharePoint-lijst](/help/forms/using/configuring-submit-actions.md#create-a-sharepoint-list-configuration)voor gedetailleerde stappen.