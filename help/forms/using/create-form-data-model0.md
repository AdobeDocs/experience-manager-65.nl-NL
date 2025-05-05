---
title: 'Zelfstudie: Een formuliergegevensmodel maken in AEM Forms'
description: Formuliergegevensmodel maken voor interactieve communicatie
contentOwner: anujkapo
products: SG_EXPERIENCEMANAGER/6.5/FORMS
docset: aem65
feature: Interactive Communication
exl-id: c8a6037c-46bd-4058-8314-61cb925ba5a8
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '2684'
ht-degree: 0%

---

# Zelfstudie: Een formuliergegevensmodel maken in AEM Forms{#tutorial-create-form-data-model}

![ 04-creeer-vorm-gegeven-model-hoofd ](assets/04-create-form-data-model-main.png)

Dit leerprogramma is een stap in [ creeer uw eerste Interactieve Communicatie ](/help/forms/using/create-your-first-interactive-communication.md) reeks. U wordt aangeraden de reeks in chronologische volgorde te volgen om het volledige gebruik van de zelfstudie te begrijpen, uit te voeren en aan te tonen.

## Over de zelfstudie {#about-the-tutorial}

Met de AEM Forms-module voor gegevensintegratie kunt u een formuliergegevensmodel maken op basis van verschillende bronnen van back-endgegevens, zoals AEM gebruikersprofiel, RESTful-webservices, op SOAP gebaseerde webservices, OData-services en relationele databases. U kunt gegevensmodelobjecten en -services configureren in een formuliergegevensmodel en deze koppelen aan een adaptief formulier. Adaptieve formuliervelden zijn gebonden aan objecteigenschappen van gegevensmodellen. Met deze services kunt u het adaptieve formulier vooraf invullen en verzonden formuliergegevens terugschrijven naar het gegevensmodelobject.

Voor meer informatie over de integratie van vormgegevens en model van vormgegevens, zie [ de Integratie van Gegevens van AEM Forms ](https://helpx.adobe.com/nl/experience-manager/6-3/forms/using/data-integration.html).

Deze zelfstudie begeleidt u door de stappen om een formuliergegevensmodel voor te bereiden, te maken, te configureren en aan een interactieve communicatie te koppelen. Aan het einde van deze zelfstudie kunt u het volgende doen:

* [De database instellen](../../forms/using/create-form-data-model0.md#step-set-up-the-database)
* [MySQL-database configureren als gegevensbron](../../forms/using/create-form-data-model0.md#step-configure-mysql-database-as-data-source)
* [Formuliergegevensmodel maken](../../forms/using/create-form-data-model0.md#step-create-form-data-model)
* [Formuliergegevensmodel configureren](../../forms/using/create-form-data-model0.md#step-configure-form-data-model)
* [Formuliergegevensmodel testen](../../forms/using/create-form-data-model0.md#step-test-form-data-model-and-services)

Het formuliergegevensmodel ziet er ongeveer als volgt uit:

![ het gegevensmodel van de Vorm ](assets/form_data_model_callouts_new.png)

**A.** Vormde gegevensbronnen **B.** De schema&#39;s van de Gegevensbron **C.** Beschikbare diensten **D.** de modelvoorwerpen van Gegevens **E.** Vormde diensten

## Vereisten {#prerequisites}

Voordat u begint, moet u het volgende doen:

* MySQL gegevensbestand met steekproefgegevens zoals die in [ worden verklaard opstelling de gegevensbestand ](../../forms/using/create-form-data-model0.md#step-set-up-the-database) sectie.
* OSGi bundel voor MySQL JDBC bestuurder zoals die in [ wordt verklaard die de Bestuurder van het Gegevensbestand JDBC bundelt ](https://helpx.adobe.com/nl/experience-manager/6-3/help/sites-developing/jdbc.html#bundling-the-jdbc-database-driver)

## Stap 1: De database instellen {#step-set-up-the-database}

Een gegevensbestand is essentieel om een Interactieve Mededeling tot stand te brengen. Deze zelfstudie gebruikt een database voor het weergeven van het formuliergegevensmodel en persistentiemogelijkheden van interactieve communicatie. Opstelling een gegevensbestand dat klant, rekeningen, en vraaglijsten bevat.
De volgende afbeelding illustreert voorbeeldgegevens voor de klantentabel:

![ sample_data_cust ](assets/sample_data_cust.png)

Gebruik de volgende verklaring DDL om de **klant** lijst in gegevensbestand tot stand te brengen.

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

Gebruik de volgende verklaring DDL om de **rekeningen** lijst in gegevensbestand tot stand te brengen.

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

Gebruik de volgende verklaring DDL om de **vraag** lijst in gegevensbestand tot stand te brengen.

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

De **vraag** lijst omvat de vraagdetails zoals vraagdatum, vraagtijd, vraagaantal, vraagduur, en vraaglasten. De **klant** lijst is verbonden met de vraaglijst gebruikend het Mobiele gebied van het Aantal (mobilenum). Voor elk mobiel aantal dat in de **wordt vermeld klant** lijst, zijn er veelvoudige verslagen in de **vraag** lijst. Bijvoorbeeld, kunt u de vraagdetails voor **terugwinnen 1457892541** mobiel aantal door naar de **vraag** lijst te verwijzen.

De **rekeningen** lijst omvat de rekeningsdetails zoals rekeningsdatum, rekeningsperiode, maandelijkse lasten, en vraagkosten. De **klant** lijst is verbonden met de **rekeningen** lijst gebruikend het gebied van het Plan van de Rekening. Er is een plan verbonden aan elke klant in de **klant** lijst. De **rekeningen** lijst omvat de het tarief details voor alle bestaande plannen. Bijvoorbeeld, kunt u de plandetails voor **Sarah** van de **klant** lijst terugwinnen en die details gebruiken om prijsdetails van de **rekeningen** lijst terug te winnen.

## Stap 2: Vorm MySQL gegevensbestand als gegevensbron {#step-configure-mysql-database-as-data-source}

U kunt verschillende typen gegevensbronnen configureren om een formuliergegevensmodel te maken. Voor dit leerprogramma, zult u het gegevensbestand vormen MySQL dat met steekproefgegevens wordt gevormd en bevolkt. Voor informatie over andere gesteunde gegevensbronnen en hoe te om hen te vormen, zie [ de Integratie van Gegevens van AEM Forms ](https://helpx.adobe.com/nl/experience-manager/6-3/forms/using/data-integration.html).

Ga als volgt te werk om uw MySQL-database te configureren:

1. Installeer het JDBC-stuurprogramma voor MySQL-database als een OSGi-bundel:

   1. Meld u als beheerder aan bij AEM Forms Author Instance en ga naar AEM bundels voor webconsoles. Het gebrek URL is [ https://localhost:4502/system/console/bundles ](https://localhost:4502/system/console/bundles).
   1. Selecteer **installeren/bijwerken**. Een **uploadt/installeert bundels** dialoog verschijnt.

   1. Selecteer **verkies Dossier** om te doorbladeren en de MySQL JDBC bestuurder OSGi bundel te selecteren. Selecteer **Bundel van het Begin** en **verfrissen Pakketten**, en selecteren **installeer** of **Update**. Zorg ervoor dat het JDBC-stuurprogramma voor MySQL van de Oracle Corporation actief is. Het stuurprogramma is geïnstalleerd.

1. MySQL-database configureren als gegevensbron:

   1. Ga naar AEM Webconsole in [ https://localhost:4502/system/console/configMgr ](https://localhost:4502/system/console/configMgr).
   1. Bepaal de plaats van **Apache die Verbinding Gepoold DataSource** configuratie. Selecteer deze optie om de configuratie te openen in de bewerkingsmodus.
   1. Geef in het dialoogvenster Configuratie de volgende gegevens op:

      * **naam Datasource:** u kunt om het even welke naam specificeren. Bijvoorbeeld, specificeer **MySQL**.

      * **Naam van het de dienstbezit DataSource**: specificeer naam van het de dienstbezit die de naam DataSource bevat. Het wordt gespecificeerd terwijl het registreren van de gegevensbroninstantie als dienst OSGi. Bijvoorbeeld, **datasource.name**.

      * **JDBC bestuurdersklasse**: specificeer de klassennaam van Java van de bestuurder JDBC. Voor MySQL gegevensbestand, specificeer **com.mysql.jdbc.Driver**.

      * **JDBC verbinding URI**: specificeer verbinding URL van het gegevensbestand. Voor MySQL-database die wordt uitgevoerd op poort 3306 en schema teleca, is de URL: `jdbc:mysql://'server':3306/teleca?autoReconnect=true&useUnicode=true&characterEncoding=utf-8`
      * **Gebruikersnaam:** Gebruikersnaam van het gegevensbestand. Het is vereist om JDBC-stuurprogramma in staat te stellen een verbinding met de database tot stand te brengen.
      * **Wachtwoord:** Wachtwoord van het gegevensbestand. Het is vereist om JDBC-stuurprogramma in staat te stellen een verbinding met de database tot stand te brengen.
      * **Test op Krediet:** laat de **Testen op Krediet** optie toe.

      * **Test op Terugkeer:** laat de **Test op Terugkeer** optie toe.

      * **Vraag van de Bevestiging:** specificeer een SQL UITGEZOCHTE vraag om verbindingen van de pool te bevestigen. De query moet ten minste één rij retourneren. Bijvoorbeeld, **uitgezocht &#42; van klant**.

      * **Isolatie van de Transactie**: Plaats de waarde aan **READ_COMTED**.

   Verlaat andere eigenschappen met standaard [ waarden ](https://tomcat.apache.org/tomcat-7.0-doc/jdbc-pool.html) en selecteer **sparen**.

   Er wordt een configuratie gemaakt die lijkt op de volgende configuratie.

   ![ configuratie Apache ](assets/apache_configuration_new.png)

## Stap 3: Een formuliergegevensmodel maken {#step-create-form-data-model}

AEM Forms verstrekt een intuïtief gebruikersinterface om [ tot een wijze van vormgegevens ](https://helpx.adobe.com/nl/experience-manager/6-3/forms/using/data-integration.html#main-pars_header_1524967585) l van gevormde gegevensbronnen te leiden. U kunt meerdere gegevensbronnen gebruiken in een formuliergegevensmodel. Voor het gebruiksgeval in deze zelfstudie, zult u MySQL als gegevensbron gebruiken.

Ga als volgt te werk om het formuliergegevensmodel te maken:

1. In AEM auteursinstantie, navigeer aan **Forms** > **Integraties van Gegevens**.
1. Selecteer **creëren** > **Model van de Gegevens van de Vorm**.
1. In de Create Tovenaar van het Gegevensmodel van de Vorm, specificeer a **naam** voor het model van vormgegevens. Bijvoorbeeld, **FDM_Create_First_IC**. Selecteer **daarna**.
1. Het uitgezochte scherm van gegevensbron maakt een lijst van alle gevormde gegevensbronnen. Selecteer **MySQL** gegevensbron en selecteer **creeer**.

   ![ MYSQL datasource ](assets/fdm_mysql_data_source_new.png)

1. Klik **Gedaan**. Het **FDM_Create_First_IC** model van vormgegevens wordt gecreeerd.

## Stap 4: Formuliergegevensmodel configureren {#step-configure-form-data-model}

Het formuliergegevensmodel configureren omvat:

* [gegevensmodelobjecten en services toevoegen](#add-data-model-objects-and-services)
* [berekende onderliggende eigenschappen maken voor gegevensmodelobject](#create-computed-child-properties-for-data-model-object)
* [koppelingen tussen gegevensmodelobjecten toevoegen](#add-associations-between-data-model-objects)
* [bewerken van objecteigenschappen van gegevensmodellen](#edit-data-model-object-properties)
* [configureren van services voor gegevensmodelobjecten](#configure-services)

### Objecten en services voor gegevensmodellen toevoegen {#add-data-model-objects-and-services}

1. Op AEM auteursinstantie, navigeer aan **Forms** > **Integraties van Gegevens**. Het gebrek URL is [ https://localhost:4502/aem/forms.html/content/dam/formsanddocuments-fdm ](https://localhost:4502/aem/forms.html/content/dam/formsanddocuments-fdm).
1. Het **FDM_Create_First_IC** model van vormgegevens u vroeger creeerde is hier vermeld. Selecteer het en selecteer **uitgeven**.

   De geselecteerde gegevensbron **MySQL** wordt getoond in de **Bronnen van Gegevens** ruit.

   ![ MYSQL gegevensbron voor FDM ](assets/mysql_fdm_new.png)

1. Breid **MySQL** gegevensbronboom uit. Selecteer de volgende voorwerpen en de diensten van het gegevensmodel van **teleca** schema:

   * **modelvoorwerpen van Gegevens**:

      * biljet
      * oproepen
      * klant

   * **de Diensten:**

      * get
      * update

   Selecteer **toevoegen Geselecteerde** om geselecteerde voorwerpen en de diensten van het gegevensmodel aan het model van vormgegevens toe te voegen.

   ![ Uitgezochte de objecten van het gegevensmodel diensten ](assets/select_data_model_object_services_new.png)

   De rekeningen, de vraag, en het modelvoorwerpen van klantengegevens worden getoond in de juiste ruit in het **Model** lusje. De krijgen en bijwerken diensten worden getoond in de **Diensten** tabel.

   ![ modelvoorwerpen van Gegevens ](assets/data_model_objects_new.png)

### Berekende onderliggende eigenschappen maken voor gegevensmodelobject {#create-computed-child-properties-for-data-model-object}

Een berekende eigenschap is de eigenschap waarvan de waarde wordt berekend op basis van een regel of expressie. Met behulp van een regel kunt u de waarde van een berekende eigenschap instellen op een letterlijke tekenreeks, een getal, het resultaat van een wiskundige expressie of de waarde van een andere eigenschap in het formuliergegevensmodel.

Gebaseerd op het gebruiksgeval, creeer het **gebruiksheadingen** kind gegevens verwerkt bezit in het **rekeningen** gegevensmodelvoorwerp gebruikend de volgende wiskundige uitdrukking:

* gebruikskosten = gesprekskosten + gesprekskosten + sms-tarieven + mobiele internettarieven + roaming nationaal + roaming internationaal + VAS (al deze eigenschappen zijn te vinden in het factuurgegevensmodelobject)
Voor meer informatie over het **kind gegevens verwerkte bezit 0&rbrace; gebruikslasten &lbrace;, zie [ Plan de Interactieve Mededeling ](/help/forms/using/planning-interactive-communications.md).**

Voer de volgende stappen uit om berekende onderliggende eigenschappen voor het modelobject van rekeningen te maken:

1. Selecteer de controledoos bij de bovenkant van het **rekeningen** gegevensmodelvoorwerp om het te selecteren en te selecteren **creeer het Bezit van het Kind**.
1. In **creeer de ruit van het Bezit van het Kind**:

   1. Ga **gebruikslasten** als naam van het kindbezit in.
   1. Laat **Berekend** toe.
   1. Selecteer **Vloeiend** als type en selecteer **Gedaan** om het kindbezit aan het **rekeningen** gegevensmodelvoorwerp toe te voegen.

   ![ creeer kindbezit ](assets/create_child_property_new.png)

1. Selecteer **uitgeven Regel** om de Redacteur van de Regel te openen.
1. Selecteer **Maken**. Het **Vastgestelde de regelvenster van de Waarde** opent.
1. Van Uitgezochte drop-down Optie, uitgezochte **Wiskundige Uitdrukking**.

   ![ de ladingsregel van het Gebruik redacteur ](assets/usage_charges_rule_editor_new.png)

1. In de wiskundige uitdrukking, uitgezochte **callloads** en **confcallladings** als eerste en tweede voorwerpen, respectievelijk. Selecteer **plus** als exploitant. Selecteer binnen de wiskundige uitdrukking en selecteer **Uitdrukking** uitbreiden om **vlekken** toe te voegen, **onderlinge verbindings van netwerkenheffingen**, **roamingnational**, **roamingintnl**, en **vas** voorwerpen aan de uitdrukking.

   De volgende afbeelding toont de wiskundige expressie in de regeleditor:

   ![ de ladingsregel van het Gebruik ](assets/usage_charges_rule_all_new.png)

1. Selecteer **Gereed**. De regel wordt gecreeerd in de Redacteur van de Regel.
1. Selecteer **dicht** om het venster van de Redacteur van de Regel te sluiten.

### Koppelingen tussen gegevensmodelobjecten toevoegen {#add-associations-between-data-model-objects}

Nadat de gegevensmodelobjecten zijn gedefinieerd, kunt u koppelingen tussen deze objecten maken. De koppeling kan een-op-een of een-op-een zijn. Bijvoorbeeld, kunnen er veelvoudige gebiedsdelen verbonden aan een werknemer zijn. Het wordt bedoeld als één-aan-vele vereniging en afgebeeld door 1:n op de lijn die bijbehorende voorwerpen van het gegevensmodel verbindt. Nochtans, als een vereniging een unieke werknemersnaam voor een bepaalde werknemersidentiteitskaart terugkeert, wordt het bedoeld als één-op-één vereniging.

Wanneer u gekoppelde gegevensmodelobjecten in een gegevensbron toevoegt aan een formuliergegevensmodel, blijven de koppelingen behouden en worden ze weergegeven als verbonden door pijllijnen.

Op basis van het gebruiksgeval kunt u de volgende koppelingen maken tussen de gegevensmodelobjecten:

| Associatie | Gegevensmodelobjecten |
|---|---|
| 1:n | klant:vraag (De veelvoudige vraag kan met een klant in een maandelijkse rekening worden geassocieerd) |
| 1:1 | klant:rekeningen (één rekening wordt geassocieerd met een klant voor een bepaalde maand) |

Voer de volgende stappen uit om koppelingen te maken tussen gegevensmodelobjecten:

1. Selecteer de controledoos bij de bovenkant van het **klant** gegevensmodelvoorwerp om het te selecteren en **te selecteren voeg Vereniging** toe. **voegt het bezitsruit van de Vereniging** toe opent.
1. In **voeg de ruit van de Vereniging** toe:

   * Geef een titel op voor de koppeling. Het is een optioneel veld.
   * Selecteer **Één aan Vele** van de **drop-down lijst van het Type**.

   * Selecteer **vraag** van de **ModelVoorwerp** drop-down lijst.

   * Selecteer **krijgen** van de **drop-down lijst van de Dienst**.

   * Selecteer **toevoegen** om het **klant** gegevensmodelvoorwerp aan **vraag** gegevensmodelvoorwerp te verbinden gebruikend een bezit. Gebaseerd op het gebruiksgeval, moet het modelvoorwerp van vraaggegevens met het mobiele aantalbezit in het voorwerp van het klantengegevensmodel worden verbonden. Het **toevoegt Argument** dialoogvakje opent.

   ![ voeg vereniging ](assets/add_association_new.png) toe

1. In **voeg de dialoogdoos van het Argument** toe:

   * Selecteer **mobiel** van de **Naam** drop-down lijst. De eigenschap mobile number is een algemene eigenschap die beschikbaar is in de klant en die gegevensmodelobjecten aanroept. Dientengevolge, wordt het gebruikt om een verband tussen klant en vraag tot stand te brengen modelvoorwerpen van gegevens.
Voor elk mobiel aantal beschikbaar in het modelvoorwerp van klantengegevens, zijn er veelvoudige vraagverslagen beschikbaar in de vraaglijst.

   * Geef een optionele titel en beschrijving voor het argument op.
   * Selecteer **klant** van **Bindend aan** drop-down lijst.

   * Selecteer **mobiel** van de **Bindende drop-down lijst van de Waarde**.

   * Selecteer **toevoegen**.

   ![ voeg vereniging voor een argument ](assets/add_association_argument_new.png) toe

   Het mobilenumbezitsvertoningen in de **sectie van Argumenten**.

   ![ voeg argumentvereniging ](assets/add_argument_association_new.png) toe

1. Selecteer **Gedaan** om een 1:n vereniging tussen klant en vraag de modelvoorwerpen van gegevens tot stand te brengen.

   Zodra u een vereniging tussen klant en vraag de modelvoorwerpen van gegevens hebt gecreeerd, creeer een 1:1 vereniging tussen de klant en de modelvoorwerpen van rekeningen.

1. Selecteer de controledoos bij de bovenkant van het **klant** gegevensmodelvoorwerp om het te selecteren en **te selecteren voeg Vereniging** toe. **voegt het bezitsruit van de Vereniging** toe opent.
1. In **voeg de ruit van de Vereniging** toe:

   * Geef een titel op voor de koppeling. Het is een optioneel veld.
   * Selecteer **Één aan Één** van de **drop-down lijst van het Type**.

   * Selecteer **rekeningen** van de **ModelVoorwerp** drop-down lijst.

   * Selecteer **krijgen** van de **drop-down lijst van de Dienst**. Het **billplan** bezit, dat de primaire sleutel voor de rekeningen lijst is, is reeds beschikbaar in de **Argumenten** sectie.
De rekeningen en de objecten van het klantengegevensmodel zijn verbonden gebruikend billplan (rekeningen) en klant (klant) eigenschappen. Creeer een band tussen deze eigenschappen om de plandetails voor om het even welke klant terug te winnen beschikbaar in het gegevensbestand MySQL.

   * Selecteer **klant** van **Bindend aan** drop-down lijst.

   * Selecteer **klantplan** van de **Bindende drop-down lijst van de Waarde**.

   * Selecteer **Gedaan** om een band tussen het billplan en de eigenschappen van het klantplan tot stand te brengen.

   ![ voeg vereniging voor klantenrekening ](assets/add_association_customer_bills_new.png) toe

   In de volgende afbeelding ziet u de koppelingen tussen de gegevensmodelobjecten en de eigenschappen die worden gebruikt om koppelingen tussen deze objecten te maken:

   ![ fdm_association ](assets/fdm_associations.gif)

### Eigenschappen van gegevensmodelobjecten bewerken {#edit-data-model-object-properties}

Nadat het creëren van verbindingen tussen de klant en andere voorwerpen van het gegevensmodel, geef de klanteneigenschappen uit om het bezit te bepalen dat wordt gebaseerd waarop de gegevens van het voorwerp van het gegevensmodel worden teruggewonnen. Gebaseerd op het gebruiksgeval, wordt het mobiele aantal gebruikt als bezit om gegevens van het voorwerp van het klantengegevensmodel terug te winnen.

1. Selecteer de controledoos bij de bovenkant van het **klant** gegevensmodelvoorwerp om het te selecteren en **te selecteren geeft Eigenschappen** uit. Het **geeft Eigenschappen** ruit uit opent.
1. Specificeer **klant** als **Hoogste modelvoorwerp van het Niveau**.
1. Selecteer **krijgen** van **Gelezen de drop-down lijst van de Dienst**.
1. In de **sectie van Argumenten**:

   * Selecteer **Attribuut van het Verzoek** van **Bindend aan** drop-down lijst.

   * Specificeer **mobiel** als Bindende Waarde.

1. Selecteer **update** van **schrijven** drop-down lijst van de Dienst.
1. In de **sectie van Argumenten**:

   * Voor **mobiel** bezit, uitgezochte **klant** van **Bindend aan** drop-down lijst.

   * Selecteer **mobiel** van de **Bindende drop-down lijst van de Waarde**.

1. Selecteer **Gedaan** om de eigenschappen te bewaren.

   ![ vormt de diensten ](assets/configure_services_customer_new.png)

1. Selecteer de controledoos bij de bovenkant van **vraag** gegevensmodelvoorwerp om het te selecteren en **te selecteren geeft Eigenschappen** uit. Het **geeft Eigenschappen** ruit uit opent.
1. Maak het **Hoogste Modelvoorwerp van het Niveau** voor **vraag** gegevensmodelvoorwerp onbruikbaar.
1. Selecteer **Gereed**.

   Herhaal stappen 8 - 10 om de eigenschappen voor **rekeningen** gegevensmodelvoorwerp te vormen.

### Services configureren {#configure-services}

1. Ga naar de **Diensten** tabel.
1. Selecteer de **krijgen** dienst en selecteren **Eigenschappen** uitgeven. Het **geeft Eigenschappen** ruit uit opent.
1. In **geef Eigenschappen** ruit uit:

   * Voer een optionele titel en beschrijving in.
   * Selecteer **klant** van de **drop-down lijst van de Objecten van het Model van de Output**.

   * Selecteer **Gedaan** om de eigenschappen te bewaren.

   ![ geeft eigenschappen ](assets/edit_properties_get_details_new.png) uit

1. Selecteer de **update** dienst en selecteer **Eigenschappen** uitgeven. Het **geeft Eigenschappen** ruit uit opent.
1. In **geef Eigenschappen** ruit uit:

   * Voer een optionele titel en beschrijving in.
   * Selecteer **klant** van de **drop-down lijst van het ModelVoorwerp van de Input**.

   * Selecteer **Gereed**.
   * Selecteer **sparen** om het model van vormgegevens te bewaren.

   ![&#128279;](assets/update_service_properties_new.png) de diensteigenschappen van 0&rbrace; Update

## Stap 5: Model en services voor het testen van formuliergegevens {#step-test-form-data-model-and-services}

U kunt het gegevensmodelobject en de services testen om te controleren of het formuliergegevensmodel correct is geconfigureerd.

Voer de volgende handelingen uit om de test uit te voeren:

1. Ga naar het **Model** lusje, selecteer het **klant** gegevensmodelvoorwerp, en selecteer **ModelVoorwerp van de Test**.
1. In het **venster van de Gegevens van de Vorm van de Test Model**, lees **modelvoorwerp** van de **Uitgezochte Model/Dienst** drop-down lijst.
1. In de **sectie van de Input**, specificeer een waarde voor het **mobilenum** bezit dat in het gevormde gegevensbestand MySQL bestaat en **Test** selecteert.

   De klantgegevens die aan de opgegeven eigenschap mobileEnum zijn gekoppeld, worden opgehaald en weergegeven in de sectie Uitvoer, zoals hieronder wordt weergegeven. Sluit het dialoogvenster.

   ![ het gegevensmodel van de Test ](assets/test_data_model_new.png)

1. Ga naar de **Diensten** tabel.
1. Selecteer **krijgen** dienst en selecteren **de Dienst van de Test.**
1. In de **sectie van de Input**, specificeer een waarde voor het **mobilenum** bezit dat in het gevormde gegevensbestand MySQL bestaat en **Test** selecteert.

   De klantgegevens die aan de opgegeven eigenschap mobileEnum zijn gekoppeld, worden opgehaald en weergegeven in de sectie Uitvoer, zoals hieronder wordt weergegeven. Sluit het dialoogvenster.

   ![ de dienst van de Test ](assets/test_service_new.png)

### Voorbeeldgegevens bewerken en opslaan {#edit-and-save-sample-data}

Met de formuliergegevensmodeleditor kunt u voorbeeldgegevens genereren voor alle eigenschappen van gegevensmodelobjecten, inclusief berekende eigenschappen, in een formuliergegevensmodel. Het is een reeks willekeurige waarden die met het gegevenstype voldoen dat voor elk bezit wordt gevormd. U kunt ook gegevens bewerken en opslaan. Deze blijven behouden, zelfs als u de voorbeeldgegevens opnieuw genereert.

Voer de volgende handelingen uit om voorbeeldgegevens te genereren, te bewerken en op te slaan:

1. Voor de pagina van het vormgegevensmodel, uitgezocht **geef de Gegevens van de Steekproef** uit. De voorbeeldgegevens worden gegenereerd en weergegeven in het venster Voorbeeldgegevens bewerken.

   ![ geef steekproefgegevens ](assets/edit_sample_data_new.png) uit

1. In **geef het venster van de Gegevens van de Steekproef** uit, geef gegevens, zoals vereist uit, en selecteer **sparen**. Sluit het venster.
