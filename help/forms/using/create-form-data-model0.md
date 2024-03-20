---
title: "Lesbestand: formuliergegevensmodel maken in AEM Forms"
description: Formuliergegevensmodel maken voor interactieve communicatie
contentOwner: anujkapo
products: SG_EXPERIENCEMANAGER/6.5/FORMS
docset: aem65
feature: Interactive Communication
exl-id: c8a6037c-46bd-4058-8314-61cb925ba5a8
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '2684'
ht-degree: 0%

---

# Zelfstudie: Een formuliergegevensmodel maken in AEM Forms{#tutorial-create-form-data-model}

![04-create-form-data-model-main](assets/04-create-form-data-model-main.png)

Deze zelfstudie is een stap in de [Maak uw eerste interactieve communicatie](/help/forms/using/create-your-first-interactive-communication.md) reeks. U wordt aangeraden de reeks in chronologische volgorde te volgen om het volledige gebruik van de zelfstudie te begrijpen, uit te voeren en aan te tonen.

## Over de zelfstudie {#about-the-tutorial}

Met de AEM Forms-module voor gegevensintegratie kunt u een formuliergegevensmodel maken op basis van verschillende bronnen van back-endgegevens, zoals AEM gebruikersprofiel, RESTful-webservices, SOAP-webservices, OData-services en relationele databases. U kunt gegevensmodelobjecten en -services configureren in een formuliergegevensmodel en deze koppelen aan een adaptief formulier. Adaptieve formuliervelden zijn gebonden aan objecteigenschappen van gegevensmodellen. Met deze services kunt u het adaptieve formulier vooraf invullen en verzonden formuliergegevens terugschrijven naar het gegevensmodelobject.

Zie voor meer informatie over de integratie van formuliergegevens en het formuliergegevensmodel [AEM Forms-gegevensintegratie](https://helpx.adobe.com/experience-manager/6-3/forms/using/data-integration.html).

Deze zelfstudie begeleidt u door de stappen om een formuliergegevensmodel voor te bereiden, te maken, te configureren en aan een interactieve communicatie te koppelen. Aan het einde van deze zelfstudie kunt u het volgende doen:

* [De database instellen](../../forms/using/create-form-data-model0.md#step-set-up-the-database)
* [MySQL-database configureren als gegevensbron](../../forms/using/create-form-data-model0.md#step-configure-mysql-database-as-data-source)
* [Formuliergegevensmodel maken](../../forms/using/create-form-data-model0.md#step-create-form-data-model)
* [Formuliergegevensmodel configureren](../../forms/using/create-form-data-model0.md#step-configure-form-data-model)
* [Formuliergegevensmodel testen](../../forms/using/create-form-data-model0.md#step-test-form-data-model-and-services)

Het formuliergegevensmodel ziet er ongeveer als volgt uit:

![Formuliergegevensmodel](assets/form_data_model_callouts_new.png)

**A.** Gevormde gegevensbronnen **B.** Gegevensbronschema&#39;s **C.** Beschikbare services **D.** Gegevensmodelobjecten **E.** Gevormde services

## Vereisten {#prerequisites}

Voordat u begint, moet u het volgende doen:

* MySQL-database met voorbeeldgegevens zoals vermeld in de [De database instellen](../../forms/using/create-form-data-model0.md#step-set-up-the-database) sectie.
* OSGi-bundel voor MySQL JDBC-stuurprogramma, zoals wordt uitgelegd in [Het JDBC-databasestuurprogramma bundelen](https://helpx.adobe.com/experience-manager/6-3/help/sites-developing/jdbc.html#bundling-the-jdbc-database-driver)

## Stap 1: De database instellen {#step-set-up-the-database}

Een gegevensbestand is essentieel om een Interactieve Mededeling tot stand te brengen. Deze zelfstudie gebruikt een database voor het weergeven van het formuliergegevensmodel en persistentiemogelijkheden van interactieve communicatie. Opstelling een gegevensbestand dat klant, rekeningen, en vraaglijsten bevat.
De volgende afbeelding illustreert voorbeeldgegevens voor de klantentabel:

![sample_data_cust](assets/sample_data_cust.png)

Gebruik de volgende verklaring DDL om tot de **klant** tabel in de database.

```sql
CREATE TABLE `customer` (
   `mobilenum` int(11) NOT NULL,
   `name` varchar(45) NOT NULL,
   `address` varchar(45) NOT NULL,
   `alternatemobilenumber` int(11) DEFAULT NULL,
   `relationshipnumber` int(11) DEFAULT NULL,
   `customerplan` varchar(45) DEFAULT NULL,
   PRIMARY KEY (`mobilenum`),
   UNIQUE KEY `mobilenum_UNIQUE` (`mobilenum`)
 ) ENGINE=InnoDB DEFAULT CHARSET=utf8
```

Gebruik de volgende verklaring DDL om tot de **biljet** tabel in de database.

```sql
CREATE TABLE `bills` (
   `billplan` varchar(45) NOT NULL,
   `latepayment` decimal(4,2) NOT NULL,
   `monthlycharges` decimal(4,2) NOT NULL,
   `billdate` date NOT NULL,
   `billperiod` varchar(45) NOT NULL,
   `prevbal` decimal(4,2) NOT NULL,
   `callcharges` decimal(4,2) NOT NULL,
   `confcallcharges` decimal(4,2) NOT NULL,
   `smscharges` decimal(4,2) NOT NULL,
   `internetcharges` decimal(4,2) NOT NULL,
   `roamingnational` decimal(4,2) NOT NULL,
   `roamingintnl` decimal(4,2) NOT NULL,
   `vas` decimal(4,2) NOT NULL,
   `discounts` decimal(4,2) NOT NULL,
   `tax` decimal(4,2) NOT NULL,
   PRIMARY KEY (`billplan`)
 ) ENGINE=InnoDB DEFAULT CHARSET=utf8
```

Gebruik de volgende verklaring DDL om tot de **oproepen** tabel in de database.

```sql
CREATE TABLE `calls` (
   `mobilenum` int(11) DEFAULT NULL,
   `calldate` date DEFAULT NULL,
   `calltime` varchar(45) DEFAULT NULL,
   `callnumber` int(11) DEFAULT NULL,
   `callduration` varchar(45) DEFAULT NULL,
   `callcharges` decimal(4,2) DEFAULT NULL,
   `calltype` varchar(45) DEFAULT NULL
 ) ENGINE=InnoDB DEFAULT CHARSET=utf8
```

De **oproepen** de lijst omvat de vraagdetails zoals vraagdatum, vraagtijd, vraagaantal, vraagduur, en vraaglasten. De **klant** de lijst is verbonden met de vraaglijst gebruikend het Mobiele gebied van het Aantal (mobilenum). Voor elk mobiel nummer dat wordt vermeld in het dialoogvenster **klant** de tabel bevat meerdere records in de **oproepen** tabel. U kunt bijvoorbeeld de vraagdetails voor de **1457892541** mobiel nummer door te verwijzen naar de **oproepen** tabel.

De **biljet** de tabel bevat de gegevens van de rekening, zoals de datum van de rekening, de factuurperiode, de maandelijkse kosten en de kosten van de oproep. De **klant** tabel is gekoppeld aan de **biljet** tabel met het veld Bill Plan. Er is een plan verbonden aan elke klant in **klant** tabel. De **biljet** de tabel bevat de prijsgegevens voor alle bestaande plannen . U kunt bijvoorbeeld de abonnementsdetails ophalen voor **Sarah** van de **klant** tabel en gebruik deze gegevens om prijsgegevens op te halen uit de **biljet** tabel.

## Stap 2: Vorm MySQL gegevensbestand als gegevensbron {#step-configure-mysql-database-as-data-source}

U kunt verschillende typen gegevensbronnen configureren om een formuliergegevensmodel te maken. Voor dit leerprogramma, zult u het gegevensbestand vormen MySQL dat met steekproefgegevens wordt gevormd en bevolkt. Voor informatie over andere gesteunde gegevensbronnen en hoe te om hen te vormen, zie [AEM Forms-gegevensintegratie](https://helpx.adobe.com/experience-manager/6-3/forms/using/data-integration.html).

Ga als volgt te werk om uw MySQL-database te configureren:

1. Installeer het JDBC-stuurprogramma voor MySQL-database als een OSGi-bundel:

   1. Meld u als beheerder aan bij AEM Forms Author Instance en ga naar AEM bundels voor webconsoles. De standaard-URL is [https://localhost:4502/system/console/bundles](https://localhost:4502/system/console/bundles).
   1. Selecteren **Installeren/bijwerken**. An **Bundels uploaden/installeren** wordt weergegeven.

   1. Selecteren **Bestand kiezen** om te doorbladeren en de MySQL JDBC bestuurder OSGi bundel te selecteren. Selecteren **Bundel starten** en **Pakketten vernieuwen** en selecteert u **Installeren** of **Bijwerken**. Zorg ervoor dat het JDBC-stuurprogramma voor MySQL van de Oracle Corporation actief is. Het stuurprogramma is geïnstalleerd.

1. MySQL-database configureren als gegevensbron:

   1. Ga naar AEM webconsole op [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr).
   1. Zoeken **Apache Sling Connection Pooled DataSource** configuratie. Selecteer deze optie om de configuratie te openen in de bewerkingsmodus.
   1. Geef in het dialoogvenster Configuratie de volgende gegevens op:

      * **Naam gegevensbron:** U kunt elke gewenste naam opgeven. Geef bijvoorbeeld **MySQL**.

      * **Eigenschapnaam van DataSource-service**: Geef een naam op van de eigenschap service die de naam DataSource bevat. Het wordt gespecificeerd terwijl het registreren van de gegevensbroninstantie als dienst OSGi. Bijvoorbeeld: **datasource.name**.

      * **JDBC-stuurprogrammaklasse**: Geef de Java-klassenaam van het JDBC-stuurprogramma op. Voor MySQL-database geeft u **com.mysql.jdbc.Driver**.

      * **URI voor JDBC-verbinding**: Geef de verbindings-URL van de database op. Voor MySQL-database die wordt uitgevoerd op poort 3306 en schema-teleca, is de URL: `jdbc:mysql://'server':3306/teleca?autoReconnect=true&useUnicode=true&characterEncoding=utf-8`
      * **Gebruikersnaam:** Gebruikersnaam van de database. Het is vereist om JDBC-stuurprogramma in staat te stellen een verbinding met de database tot stand te brengen.
      * **Wachtwoord:** Wachtwoord van de database. Het is vereist om JDBC-stuurprogramma in staat te stellen een verbinding met de database tot stand te brengen.
      * **Testen op lenen:** De optie **Testen op lenen** -optie.

      * **Testen op rendement:** De optie **Testen op rendement** -optie.

      * **Validatiezoekopdracht:** Geef een SQL SELECT-query op om verbindingen vanuit de pool te valideren. De query moet ten minste één rij retourneren. Bijvoorbeeld: **selecteren &#42; van klant**.

      * **Transactieisolatie**: Stel de waarde in op **READ_COMTED**.

   Andere eigenschappen standaard laten staan [waarden](https://tomcat.apache.org/tomcat-7.0-doc/jdbc-pool.html) en selecteert u **Opslaan**.

   Er wordt een configuratie gemaakt die lijkt op de volgende configuratie.

   ![Apache-configuratie](assets/apache_configuration_new.png)

## Stap 3: Een formuliergegevensmodel maken {#step-create-form-data-model}

AEM Forms biedt een intuïtieve gebruikersinterface voor [Een modus voor formuliergegevens maken](https://helpx.adobe.com/experience-manager/6-3/forms/using/data-integration.html#main-pars_header_1524967585)l van gevormde gegevensbronnen. U kunt meerdere gegevensbronnen gebruiken in een formuliergegevensmodel. Voor het gebruiksgeval in deze zelfstudie, zult u MySQL als gegevensbron gebruiken.

Ga als volgt te werk om het formuliergegevensmodel te maken:

1. Navigeer in AEM auteurinstantie naar **Forms** > **Gegevensintegratie**.
1. Selecteren **Maken** > **Formuliergegevensmodel**.
1. Geef in de wizard Formuliergegevensmodel maken een **name** voor het formuliergegevensmodel. Bijvoorbeeld: **FDM_Create_First_IC**. Selecteren **Volgende**.
1. Het uitgezochte scherm van gegevensbron maakt een lijst van alle gevormde gegevensbronnen. Selecteren **MySQL** gegevensbron en selecteer **Maken**.

   ![MYSQL-gegevensbron](assets/fdm_mysql_data_source_new.png)

1. Klikken **Gereed**. De **FDM_Create_First_IC** formuliergegevensmodel wordt gemaakt.

## Stap 4: Formuliergegevensmodel configureren {#step-configure-form-data-model}

Het formuliergegevensmodel configureren omvat:

* [gegevensmodelobjecten en services toevoegen](#add-data-model-objects-and-services)
* [berekende onderliggende eigenschappen maken voor gegevensmodelobject](#create-computed-child-properties-for-data-model-object)
* [koppelingen tussen gegevensmodelobjecten toevoegen](#add-associations-between-data-model-objects)
* [bewerken van objecteigenschappen van gegevensmodellen](#edit-data-model-object-properties)
* [configureren van services voor gegevensmodelobjecten](#configure-services)

### Objecten en services voor gegevensmodellen toevoegen {#add-data-model-objects-and-services}

1. Navigeer in AEM auteurinstantie naar **Forms** > **Gegevensintegratie**. De standaard-URL is [https://localhost:4502/aem/forms.html/content/dam/formsanddocuments-fdm](https://localhost:4502/aem/forms.html/content/dam/formsanddocuments-fdm).
1. De **FDM_Create_First_IC** Hier wordt het formuliergegevensmodel weergegeven dat u eerder hebt gemaakt. Selecteer het en selecteer **Bewerken**.

   De geselecteerde gegevensbron **MySQL** wordt weergegeven in het dialoogvenster **Gegevensbronnen** venster.

   ![MYSQL-gegevensbron voor FDM](assets/mysql_fdm_new.png)

1. Breid uit **MySQL** gegevensbronstructuur. Selecteer de volgende gegevensmodelvoorwerpen en de diensten van **teleca** schema:

   * **Gegevensmodelobjecten**:

      * biljet
      * oproepen
      * klant

   * **Services:**

      * get
      * update

   Selecteren **Geselecteerde toevoegen** Hiermee voegt u geselecteerde gegevensmodelobjecten en -services toe aan het formuliergegevensmodel.

   ![Objectservices voor gegevensmodellen selecteren](assets/select_data_model_object_services_new.png)

   De rekeningen, de vraag, en de objecten van het klantengegevensmodel worden getoond in de juiste ruit in **Model** tab. De get- en updateservices worden weergegeven in het dialoogvenster **Services** tab.

   ![Gegevensmodelobjecten](assets/data_model_objects_new.png)

### Berekende onderliggende eigenschappen maken voor gegevensmodelobject {#create-computed-child-properties-for-data-model-object}

Een berekende eigenschap is de eigenschap waarvan de waarde wordt berekend op basis van een regel of expressie. Met behulp van een regel kunt u de waarde van een berekende eigenschap instellen op een letterlijke tekenreeks, een getal, het resultaat van een wiskundige expressie of de waarde van een andere eigenschap in het formuliergegevensmodel.

Maak op basis van het gebruiksgeval de **gebruikskosten** onderliggende berekende eigenschap in de **biljet** gegevensmodelobject met de volgende wiskundige expressie:

* gebruikskosten = gesprekstarieven + conferentiegesprekstarieven + sms-tarieven + mobiele internettarieven + roaming nationaal + roaming internationaal + VAS (al deze eigenschappen bestaan in het object van het factureringsgegevensmodel) Voor meer informatie over **gebruikskosten** onderliggende berekende eigenschap, zie [De interactieve communicatie plannen](/help/forms/using/planning-interactive-communications.md).

Voer de volgende stappen uit om berekende onderliggende eigenschappen voor het modelobject van rekeningen te maken:

1. Schakel het selectievakje boven aan het dialoogvenster **biljet** gegevensmodelobject om het te selecteren en te selecteren **Eigenschap voor onderliggende elementen maken**.
1. In de **Eigenschap voor onderliggende elementen maken** deelvenster:

   1. Enter **gebruikskosten** als de naam van de onderliggende eigenschap.
   1. Inschakelen **Berekend**.
   1. Selecteren **Float** als het type en selecteer **Gereed** om de eigenschap child toe te voegen aan de **biljet** gegevensmodelobject.

   ![Eigenschap voor onderliggende elementen maken](assets/create_child_property_new.png)

1. Selecteren **Regel bewerken** om de Regeleditor te openen.
1. Selecteer **Maken**. De **Waarde instellen** regelvenster wordt geopend.
1. Selecteer in het keuzemenu Optie selecteren de optie **Wiskundige expressie**.

   ![Redacteur voor gebruiksrechten](assets/usage_charges_rule_editor_new.png)

1. Selecteer in de wiskundige expressie **opvragingskosten** en **samenvattingskosten** als respectievelijk eerste en tweede object. Selecteren **plus** als de operator. Selecteren in de wiskundige expressie en selecteren **Expressie uitbreiden** toevoegen **schaarste**, **onderlinge verbinding**, **landelijk**, **roamingintnl**, en **vas** objecten naar de expressie.

   De volgende afbeelding toont de wiskundige expressie in de regeleditor:

   ![regel voor gebruiksrechten](assets/usage_charges_rule_all_new.png)

1. Selecteren **Gereed**. De regel wordt gecreeerd in de Redacteur van de Regel.
1. Selecteren **Sluiten** om het venster van de Redacteur van de Regel te sluiten.

### Koppelingen tussen gegevensmodelobjecten toevoegen {#add-associations-between-data-model-objects}

Nadat de gegevensmodelobjecten zijn gedefinieerd, kunt u koppelingen tussen deze objecten maken. De koppeling kan een-op-een of een-op-een zijn. Bijvoorbeeld, kunnen er veelvoudige gebiedsdelen verbonden aan een werknemer zijn. Het wordt bedoeld als één-aan-vele vereniging en afgebeeld door 1:n op de lijn die bijbehorende voorwerpen van het gegevensmodel verbindt. Nochtans, als een vereniging een unieke werknemersnaam voor een bepaalde werknemersidentiteitskaart terugkeert, wordt het bedoeld als één-op-één vereniging.

Wanneer u gekoppelde gegevensmodelobjecten in een gegevensbron toevoegt aan een formuliergegevensmodel, blijven de koppelingen behouden en worden ze weergegeven als verbonden door pijllijnen.

Op basis van het gebruiksgeval kunt u de volgende koppelingen maken tussen de gegevensmodelobjecten:

| Associatie | Gegevensmodelobjecten |
|---|---|
| 1:n | klant:vraag (De veelvoudige vraag kan met een klant in een maandelijkse rekening worden geassocieerd) |
| 1:1 | klant:rekeningen (één rekening wordt geassocieerd met een klant voor een bepaalde maand) |

Voer de volgende stappen uit om koppelingen te maken tussen gegevensmodelobjecten:

1. Schakel het selectievakje boven aan het dialoogvenster **klant** gegevensmodelobject om het te selecteren en te selecteren **Koppeling toevoegen**. De **Koppeling toevoegen** eigenschappenvenster wordt geopend.
1. In de **Koppeling toevoegen** deelvenster:

   * Geef een titel op voor de koppeling. Het is een optioneel veld.
   * Selecteren **Eén naar vele** van de **Type** vervolgkeuzelijst.

   * Selecteren **oproepen** van de **Modelobject** vervolgkeuzelijst.

   * Selecteren **get** van de **Service** vervolgkeuzelijst.

   * Selecteren **Toevoegen** om de **klant** gegevensmodelobject naar **oproepen** gegevensmodelobject dat een eigenschap gebruikt. Gebaseerd op het gebruiksgeval, moet het modelvoorwerp van vraaggegevens met het mobiele aantalbezit in het voorwerp van het klantengegevensmodel worden verbonden. De **Argument toevoegen** wordt geopend.

   ![Koppeling toevoegen](assets/add_association_new.png)

1. In de **Argument toevoegen** dialoogvenster:

   * Selecteren **mobilenum** van de **Naam** vervolgkeuzelijst. De eigenschap mobile number is een algemene eigenschap die beschikbaar is in de klant en die gegevensmodelobjecten aanroept. Dientengevolge, wordt het gebruikt om een verband tussen klant en vraag tot stand te brengen modelvoorwerpen van gegevens.
Voor elk mobiel aantal beschikbaar in het modelvoorwerp van klantengegevens, zijn er veelvoudige vraagverslagen beschikbaar in de vraaglijst.

   * Geef een optionele titel en beschrijving voor het argument op.
   * Selecteren **klant** van de **Binding aan** vervolgkeuzelijst.

   * Selecteren **mobilenum** van de **Bindingswaarde** vervolgkeuzelijst.

   * Selecteren **Toevoegen**.

   ![Koppeling toevoegen voor een argument](assets/add_association_argument_new.png)

   De eigenschap mobilenum wordt weergegeven in het dialoogvenster **Argumenten** sectie.

   ![Woordkoppeling toevoegen](assets/add_argument_association_new.png)

1. Selecteren **Gereed** om een verbinding 1:n tussen klant en roept gegevensmodelvoorwerpen tot stand te brengen.

   Zodra u een vereniging tussen klant en vraag de modelvoorwerpen van gegevens hebt gecreeerd, creeer een 1:1 vereniging tussen de klant en de modelvoorwerpen van rekeningen.

1. Schakel het selectievakje boven aan het dialoogvenster **klant** gegevensmodelobject om het te selecteren en te selecteren **Koppeling toevoegen**. De **Koppeling toevoegen** eigenschappenvenster wordt geopend.
1. In de **Koppeling toevoegen** deelvenster:

   * Geef een titel op voor de koppeling. Het is een optioneel veld.
   * Selecteren **Eén op één** van de **Type** vervolgkeuzelijst.

   * Selecteren **biljet** van de **Modelobject** vervolgkeuzelijst.

   * Selecteren **get** van de **Service** vervolgkeuzelijst. De **bladerplan** eigenschap, de primaire sleutel voor de tabel met rekeningen, is al beschikbaar in de **Argumenten** sectie.
De rekeningen en de objecten van het klantengegevensmodel zijn verbonden gebruikend billplan (rekeningen) en klant (klant) eigenschappen. Creeer een band tussen deze eigenschappen om de plandetails voor om het even welke klant terug te winnen beschikbaar in het gegevensbestand MySQL.

   * Selecteren **klant** van de **Binding aan** vervolgkeuzelijst.

   * Selecteren **klantplan** van de **Bindingswaarde** vervolgkeuzelijst.

   * Selecteren **Gereed** om een band tussen het billplan en de eigenschappen van het klantplan te creëren.

   ![Koppeling toevoegen aan klantrekening](assets/add_association_customer_bills_new.png)

   In de volgende afbeelding ziet u de koppelingen tussen de gegevensmodelobjecten en de eigenschappen die worden gebruikt om koppelingen tussen deze objecten te maken:

   ![fdm_verenigingen](assets/fdm_associations.gif)

### Eigenschappen van gegevensmodelobjecten bewerken {#edit-data-model-object-properties}

Nadat het creëren van verbindingen tussen de klant en andere voorwerpen van het gegevensmodel, geef de klanteneigenschappen uit om het bezit te bepalen dat wordt gebaseerd waarop de gegevens van het voorwerp van het gegevensmodel worden teruggewonnen. Gebaseerd op het gebruiksgeval, wordt het mobiele aantal gebruikt als bezit om gegevens van het voorwerp van het klantengegevensmodel terug te winnen.

1. Schakel het selectievakje boven aan het dialoogvenster **klant** gegevensmodelobject om het te selecteren en te selecteren **Eigenschappen bewerken**. De **Eigenschappen bewerken** wordt geopend.
1. Opgeven **klant** als de **Model op hoofdniveau, object**.
1. Selecteren **get** van de **Leesservice** vervolgkeuzelijst.
1. In de **Argumenten** sectie:

   * Selecteren **Aanvraagkenmerk** van de **Binding aan** vervolgkeuzelijst.

   * Opgeven **mobilenum** als de bindingswaarde.

1. Selecteren **update** van de **Schrijven** Vervolgkeuzelijst Service.
1. In de **Argumenten** sectie:

   * Voor **mobilenum** eigenschap, selecteren **klant** van de **Binding aan** vervolgkeuzelijst.

   * Selecteren **mobilenum** van de **Bindingswaarde** vervolgkeuzelijst.

1. Selecteren **Gereed** om de eigenschappen op te slaan.

   ![Services configureren](assets/configure_services_customer_new.png)

1. Schakel het selectievakje boven aan het dialoogvenster **oproepen** gegevensmodelobject om het te selecteren en te selecteren **Eigenschappen bewerken**. De **Eigenschappen bewerken** wordt geopend.
1. Schakel het dialoogvenster **Model op hoofdniveau, object** for **oproepen** gegevensmodelobject.
1. Selecteren **Gereed**.

   Herhaal stap 8 - 10 om de eigenschappen voor te configureren **biljet** gegevensmodelobject.

### Services configureren {#configure-services}

1. Ga naar de **Services** tab.
1. Selecteer de **get** service en selecteer **Eigenschappen bewerken**. De **Eigenschappen bewerken** wordt geopend.
1. In de **Eigenschappen bewerken** deelvenster:

   * Voer een optionele titel en beschrijving in.
   * Selecteren **klant** van de **Uitvoermodelobject** vervolgkeuzelijst.

   * Selecteren **Gereed** om de eigenschappen op te slaan.

   ![Eigenschappen bewerken](assets/edit_properties_get_details_new.png)

1. Selecteer de **update** service en selecteer **Eigenschappen bewerken**. De **Eigenschappen bewerken** wordt geopend.
1. In de **Eigenschappen bewerken** deelvenster:

   * Voer een optionele titel en beschrijving in.
   * Selecteren **klant** van de **Invoermodelobject** vervolgkeuzelijst.

   * Selecteren **Gereed**.
   * Selecteren **Opslaan** om het formuliergegevensmodel op te slaan.

   ![Service-eigenschappen bijwerken](assets/update_service_properties_new.png)

## Stap 5: Model en services voor het testen van formuliergegevens {#step-test-form-data-model-and-services}

U kunt het gegevensmodelobject en de services testen om te controleren of het formuliergegevensmodel correct is geconfigureerd.

Voer de volgende handelingen uit om de test uit te voeren:

1. Ga naar de **Model** selecteert u de **klant** gegevensmodelobject en selecteer **Model-object testen**.
1. In de **Formuliergegevensmodel testen** venster, selecteert u **Model-object lezen** van de **Model/service selecteren** vervolgkeuzelijst.
1. In de **Invoer** -sectie, geeft u een waarde op voor de **mobilenum** bezit dat in het gevormde gegevensbestand MySQL bestaat en uitgezocht **Testen**.

   De klantgegevens die aan de opgegeven eigenschap mobileEnum zijn gekoppeld, worden opgehaald en weergegeven in de sectie Uitvoer, zoals hieronder wordt weergegeven. Sluit het dialoogvenster.

   ![Testgegevensmodel](assets/test_data_model_new.png)

1. Ga naar de **Services** tab.
1. Selecteer de **get** service en selecteer **Testservice.**
1. In de **Invoer** -sectie, geeft u een waarde op voor de **mobilenum** bezit dat in het gevormde gegevensbestand MySQL bestaat en uitgezocht **Testen**.

   De klantgegevens die aan de opgegeven eigenschap mobileEnum zijn gekoppeld, worden opgehaald en weergegeven in de sectie Uitvoer, zoals hieronder wordt weergegeven. Sluit het dialoogvenster.

   ![Testservice](assets/test_service_new.png)

### Voorbeeldgegevens bewerken en opslaan {#edit-and-save-sample-data}

Met de formuliergegevensmodeleditor kunt u voorbeeldgegevens genereren voor alle eigenschappen van gegevensmodelobjecten, inclusief berekende eigenschappen, in een formuliergegevensmodel. Het is een reeks willekeurige waarden die met het gegevenstype voldoen dat voor elk bezit wordt gevormd. U kunt ook gegevens bewerken en opslaan. Deze blijven behouden, zelfs als u de voorbeeldgegevens opnieuw genereert.

Voer de volgende handelingen uit om voorbeeldgegevens te genereren, te bewerken en op te slaan:

1. Selecteer op de pagina met het formuliergegevensmodel **Voorbeeldgegevens bewerken**. De voorbeeldgegevens worden gegenereerd en weergegeven in het venster Voorbeeldgegevens bewerken.

   ![Voorbeeldgegevens bewerken](assets/edit_sample_data_new.png)

1. In **Voorbeeldgegevens bewerken** venster, gegevens naar wens bewerken en **Opslaan**. Sluit het venster.
