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

Dit leerprogramma is een stap in [ creeert Uw Eerste AanpassingsVorm ](../../forms/using/create-your-first-adaptive-form.md) reeksen. De Adobe raadt u aan de reeks in chronologische volgorde te volgen om de volledige Gebruikszaak van de zelfstudie te begrijpen, uit te voeren en te demonstreren.

## Over de zelfstudie {#about-the-tutorial}

AEM de module van de de gegevensintegratie van [!DNL Forms] kunt u een model van vormgegevens tot stand brengen van verschillende achterste gegevensbronnen zoals AEM gebruikersprofiel, RESTful Webdiensten, SOAP-gebaseerde Webdiensten, de diensten van OData, en relationele gegevensbestanden. U kunt gegevensmodelobjecten en -services configureren in een formuliergegevensmodel en deze koppelen aan een adaptief formulier. Adaptieve formuliervelden zijn gebonden aan objecteigenschappen van gegevensmodellen. Met deze services kunt u het adaptieve formulier vooraf invullen en verzonden formuliergegevens terugschrijven naar het gegevensmodelobject.

Voor meer informatie over de integratie van vormgegevens en model van vormgegevens, zie [ de Integratie van Gegevens van AEM Forms ](../../forms/using/data-integration.md).

Deze zelfstudie begeleidt u door de stappen voor het voorbereiden, maken, configureren en koppelen van een formuliergegevensmodel aan een adaptief formulier. Aan het einde van deze zelfstudie kunt u het volgende doen:

* [MySQL-database configureren als gegevensbron](#config-database)
* [Formuliergegevensmodel maken met MySQL-database](#create-fdm)
* [Formuliergegevensmodel configureren](#config-fdm)
* [Formuliergegevensmodel testen](#test-fdm)

Het formuliergegevensmodel ziet er ongeveer als volgt uit:

![ vorm-gegeven-model_l ](assets/form-data-model_l.png)

**A.** Vormde gegevensbronnen **B.** De schema&#39;s van de Gegevensbron **C.** Beschikbare diensten **D.** de modelvoorwerpen van Gegevens **E.** Vormde diensten

## Vereisten {#prerequisites}

Voordat u begint, moet u het volgende doen:

* [!DNL MySQL] gegevensbestand met steekproefgegevens zoals die in de sectie van Vereisten van [ worden verklaard creeer uw eerste adaptieve vorm ](../../forms/using/create-your-first-adaptive-form.md)
* OSGi bundel voor [!DNL MySQL] bestuurder JDBC zoals verklaard in [ Bundling de Bestuurder van het Gegevensbestand JDBC ](/help/sites-developing/jdbc.md#bundling-the-jdbc-database-driver)
* De adaptieve vorm zoals verklaard in het eerste leerprogramma [ leidt tot een adaptieve vorm ](/help/forms/using/create-adaptive-form.md)

## Stap 1: Vorm MySQL gegevensbestand als gegevensbron {#config-database}

U kunt verschillende typen gegevensbronnen configureren om een formuliergegevensmodel te maken. Voor deze zelfstudie configureert u de MySQL-database die u hebt geconfigureerd en gevuld met voorbeeldgegevens. Voor informatie over andere gesteunde gegevensbronnen en hoe te om hen te vormen, zie [ de Integratie van Gegevens van AEM Forms ](../../forms/using/data-integration.md).

Ga als volgt te werk om uw [!DNL MySQL] -database te configureren:

1. Installeer het JDBC-stuurprogramma voor de [!DNL MySQL] -database als een OSGi-bundel:

   1. Download [!DNL MySQL] OSGi-bundel voor JDBC-stuurprogramma van `http://www.java2s.com/ref/jar/download-orgosgiservicejdbc100jar-file.html` . <!-- This URL is an insecure link but using https is not possible -->
   1. Meld u aan bij AEM [!DNL Forms] Author Instance als beheerder en ga naar bundels met AEM-webconsoles. De standaard-URL is [https://localhost:4502/system/console/bundles](https://localhost:4502/system/console/bundles).

   1. Selecteer **[!UICONTROL Install/Update]**. Er wordt een [!UICONTROL Upload / Install Bundles] dialoogvenster weergegeven.

   1. Selecteer **[!UICONTROL Choose File]** om door de bundel [!DNL MySQL] OSGi van het JDBC-stuurprogramma te bladeren en deze te selecteren. Selecteer **[!UICONTROL Start Bundle]** en **[!UICONTROL Refresh Packages]** en selecteer **[!UICONTROL Install or Update]** . Controleer of het [!DNL Oracle Corporation's] JDBC-stuurprogramma voor [!DNL MySQL] actief is. Het stuurprogramma is geïnstalleerd.

1. [!DNL MySQL] -database configureren als gegevensbron:

   1. Ga naar AEM Webconsole in [ https://localhost:4502/system/console/configMgr ](https://localhost:4502/system/console/configMgr).
   1. Bepaal de plaats van **Apache die Verbinding Gepoold DataSource** configuratie. Selecteer deze optie om de configuratie te openen in de bewerkingsmodus.
   1. Geef in het dialoogvenster Configuratie de volgende gegevens op:

      * **naam Datasource:** u kunt om het even welke naam specificeren. Bijvoorbeeld, specificeer **WeRetailMySQL**.
      * **Naam van het de dienstbezit DataSource**: specificeer naam van het de dienstbezit die de naam DataSource bevat. Het wordt gespecificeerd terwijl het registreren van de gegevensbroninstantie als dienst OSGi. Bijvoorbeeld, **datasource.name**.
      * **JDBC bestuurdersklasse**: specificeer Java™ klassennaam van de bestuurder JDBC. Geef [!DNL MySQL] **voor database com.mysql.jdbc.Driver op**.
      * **JDBC verbinding URI**: specificeer verbinding URL van het gegevensbestand. Voor [!DNL MySQL] -database die wordt uitgevoerd op poort 306 en schema `weretail` is de URL: `jdbc:mysql://'server':3306/weretail?autoReconnect=true&useUnicode=true&characterEncoding=utf-8`

      >[!NOTE]
      >
      > Wanneer de [!DNL MySQL] -database zich achter een firewall bevindt, is de hostnaam van de database geen openbare DNS. Het IP-adres van de database moet worden toegevoegd aan het */etc/hosts-bestand* van de AEM-hostcomputer.

      * **Gebruikersnaam:** Gebruikersnaam van de database. U moet het JDBC-stuurprogramma inschakelen om een verbinding met de database tot stand te brengen.
      * **Wachtwoord:** Wachtwoord van het gegevensbestand. Het is vereist om JDBC-stuurprogramma in staat te stellen een verbinding met de database tot stand te brengen.

      >[!NOTE]
      >
      >AEM Forms biedt geen ondersteuning voor NT-verificatie voor [!DNL MySQL] . Ga naar AEM Webconsole in [ https://localhost:4502/system/console/configMgr ](https://localhost:4502/system/console/configMgr) en onderzoek &quot;Apache het Verdelen Verbinding Gepoolde Gegevensbron&quot;. Voor de eigenschap &quot;JDBC connection URI&quot; stelt u de waarde van &quot;IntegratedSecurity&quot; in op False en gebruikt u de gemaakte gebruikersnaam en het gemaakte wachtwoord voor verbinding met de database [!DNL MySQL] .

      * **Test op Krediet:** laat de **[!UICONTROL Test on Borrow]** optie toe.
      * **Test op Terugkeer:** laat de **[!UICONTROL Test on Return]** optie toe.
      * **Vraag van de Bevestiging:** specificeer een SQL UITGEZOCHTE vraag om verbindingen van de pool te bevestigen. De query moet ten minste één rij retourneren. Bijvoorbeeld, **selecteer &#42; van klantdetails**.
      * **Isolatie van de Transactie**: Plaats de waarde aan **READ_COMTED**.

        Verlaat andere eigenschappen met standaard [ waarden ](https://tomcat.apache.org/tomcat-7.0-doc/jdbc-pool.html) en selecteer **[!UICONTROL Save]**.

        Er wordt een configuratie gemaakt die lijkt op de volgende configuratie.

        ![ relationeel-gegevensbestand-gegeven-bron-configuratie ](assets/relational-database-data-source-configuration.png)

## Stap 2: Formuliergegevensmodel maken {#create-fdm}

AEM [!DNL Forms] biedt een intuïtieve gebruikersinterface om een formuliergegevensmodel](data-integration.md) te [maken op basis van geconfigureerde gegevensbronnen. U kunt meerdere gegevensbronnen in een formuliergegevensmodel gebruiken. In dit geval kunt u de geconfigureerde [!DNL MySQL] gegevensbron gebruiken.

Ga als volgt te werk om een formuliergegevensmodel te maken:

1. Navigeer in AEM auteurinstantie naar **[!UICONTROL Forms]** > **[!UICONTROL Data Integrations]** .
1. Selecteer **[!UICONTROL Create]** > **[!UICONTROL Form Data Model]** .
1. In de Create dialoog van het Model van Gegevens van de Vorm, specificeer a **naam** voor het model van vormgegevens. Bijvoorbeeld, **klant-verschepen-facturerend-details**. Selecteer **[!UICONTROL Next]** .
1. Het uitgezochte scherm van gegevensbron maakt een lijst van alle gevormde gegevensbronnen. Selecteer **WijRetailMySQL** gegevensbron en selecteer **[!UICONTROL Create]**.

   ![ gegeven-bron-selectie ](assets/data-source-selection.png)

Het **klant-verschepen-factureren-details** model van vormgegevens wordt gecreeerd.

## Stap 3: Formuliergegevensmodel configureren {#config-fdm}

Het configureren van het formuliergegevensmodel omvat:

* toevoegen, gegevensmodelobject en -services
* het vormen lees en schrijf de diensten voor de voorwerpen van het gegevensmodel

Voer de volgende handelingen uit om het formuliergegevensmodel te configureren:

1. Navigeer in AEM auteurinstantie naar **[!UICONTROL Forms]** > **[!UICONTROL Data Integrations]** . Het gebrek URL is [ https://localhost:4502/aem/forms.html/content/dam/formsanddocuments-fdm ](https://localhost:4502/aem/forms.html/content/dam/formsanddocuments-fdm).
1. Het **klant-verschepen-factureren-details** model van vormgegevens u vroeger creeerde is hier vermeld. Open het in de bewerkingsmodus.

   De geselecteerde gegevensbron **WeRetailMySQL** wordt gevormd in het model van vormgegevens.

   ![ gebrek-fdm ](assets/default-fdm.png)

1. Vouw de WebRailMySQL-gegevensbronstructuur uit. Selecteer de volgende voorwerpen en de diensten van het gegevensmodel van **weretail** > **klantdetails** schema zodat kunt u gegevensmodel vormen:

   * **modelvoorwerpen van Gegevens**:

      * id
      * name
      * ShippingAddress
      * stad
      * state
      * postcode

   * **Diensten:**

      * Toevoegen
      * update

   Selecteer **toevoegen Geselecteerde** om geselecteerde voorwerpen en de diensten van het gegevensmodel aan het model van vormgegevens toe te voegen.

   ![ WijRetail Schema ](assets/weretail_schema_new.png)

   >[!NOTE]
   >
   >De standaard krijgt, update, en neemt de diensten voor JDBC- gegevensbronnen op uit-van-de-doos met het model van vormgegevens.

1. Configureer lees- en schrijfservices voor het gegevensmodelobject.

   1. Selecteer het **klantDetails** voorwerp van het gegevensmodel en selecteer **[!UICONTROL Edit Properties]**.
   1. Selecteer **[!UICONTROL get]** in de vervolgkeuzelijst Leesservice. Het **identiteitskaart** argument, dat de primaire sleutel in het voorwerp van de klantendetails gegevensmodel is wordt automatisch toegevoegd. Selecteer ![ aem_6_3_edit ](assets/aem_6_3_edit.png) en vorm het argument als volgt.

      ![ read-default ](assets/read-default.png)

   1. Selecteer op dezelfde manier **[!UICONTROL update]** als de Write Service. Het **klantdetails** voorwerp wordt automatisch toegevoegd als argument. Het argument is als volgt geconfigureerd.

      ![ schrijven-gebrek ](assets/write-default.png)

      Voeg en vorm het **identiteitskaart** argument als volgt toe.

      ![ id-arg ](assets/id-arg.png)

   1. Selecteer **[!UICONTROL Done]** om de eigenschappen van het gegevensmodel op te slaan. Selecteer **[!UICONTROL Save]** vervolgens om het formuliergegevensmodel op te slaan.

      De **[!UICONTROL get]** en **[!UICONTROL update]** services worden toegevoegd als standaardservices voor het gegevensmodelobject.

      ![data-model-object](assets/data-model-object.png)

1. Ga naar het tabblad **[!UICONTROL Services]** en configureer **[!UICONTROL get]** - en **[!UICONTROL update]** -services.

   1. Selecteer de service **[!UICONTROL get]** en selecteer **[!UICONTROL Edit Properties]** . Het dialoogvenster Eigenschappen wordt geopend.
   1. Geef het volgende op in het dialoogvenster Eigenschappen bewerken:

      * **Titel**: Specificeer titel van de dienst. Bijvoorbeeld: Verzendadres ophalen.
      * **Beschrijving**: Specificeer beschrijving die het gedetailleerde functioneren van de dienst bevatten. Bijvoorbeeld:

        Deze service haalt het verzendadres en andere klantgegevens op uit de [!DNL MySQL] -database

      * **ModelVoorwerp van de Output**: Selecteer schema dat klantengegevens bevat. Bijvoorbeeld:

        klantdetailschema

      * **serie van de Terugkeer**: Maak de **serie van de Terugkeer** optie onbruikbaar.
      * **Argumenten**: selecteer het argument id ****.

      Selecteer **[!UICONTROL Done]**. De service voor het ophalen van klantgegevens uit de MySQL-database is geconfigureerd.

      ![ verzendt-adres-herwinning ](assets/shiiping-address-retrieval.png)

   1. Selecteer de service **[!UICONTROL update]** en selecteer **[!UICONTROL Edit Properties]** . Het dialoogvenster Eigenschappen wordt geopend.

   1. Geef het volgende op in het dialoogvenster [!UICONTROL Edit Properties] :

      * **Titel**: Specificeer titel van de dienst. Bijvoorbeeld Verzendadres bijwerken.
      * **Beschrijving**: Specificeer beschrijving die het gedetailleerde functioneren van de dienst bevatten. Bijvoorbeeld:

        Deze service werkt het verzendadres en verwante velden in de MySQL-database bij

      * **ModelVoorwerp van de Input**: Selecteer schema dat klantengegevens bevat. Bijvoorbeeld:

        klantdetailschema

      * **Type van Output**: Selecteer **BOOLEAN**.

      * **Argumenten**: Selecteer argumentnaam **identiteitskaart** en **klantdetails**.

      Selecteer **[!UICONTROL Done]**. De **[!UICONTROL update]** -service voor het bijwerken van klantgegevens in de [!DNL MySQL] -database is geconfigureerd.

      ![ verzendt-adres-update ](assets/shiiping-address-update.png)

Het gegevensmodelvoorwerp en de diensten in het model van vormgegevens worden gevormd. U kunt nu het formuliergegevensmodel testen.

## Stap 4: Model voor formuliergegevens testen {#test-fdm}

U kunt het gegevensmodelobject en de services testen om te controleren of het formuliergegevensmodel correct is geconfigureerd.

Voer de volgende handelingen uit om de test uit te voeren:

1. Ga naar het **[!UICONTROL Model]** lusje, selecteer het **klantDetails** voorwerp van het gegevensmodel, en selecteer **[!UICONTROL Test Model Object]**.
1. Selecteer in het [!UICONTROL Test Model/Service] -venster **[!UICONTROL Read model object]** in de vervolgkeuzelijst **[!UICONTROL Select Model/Service]** .
1. In de **klantendetails** sectie, specificeer een waarde voor het **identiteitskaart** argument dat in het gevormde [!DNL MySQL] gegevensbestand bestaat en **[!UICONTROL Test]** selecteert.

   De klantgegevens die aan de opgegeven id zijn gekoppeld, worden opgehaald en in de sectie **[!UICONTROL Output]** weergegeven, zoals hieronder wordt weergegeven.

   ![ test-lees-model ](assets/test-read-model.png)

1. Op dezelfde manier kunt u het Schrijven modelvoorwerp en de diensten testen.

   In het volgende voorbeeld werkt de updateservice de adresgegevens voor de id 7102715 in de database bij.

   ![ test-schrijf-model ](assets/test-write-model.png)

   Nu, als u de gelezen modeldienst opnieuw voor identiteitskaart 7107215 test, haalt het en toont de bijgewerkte klantendetails zoals hieronder getoond.

   ![ lees-bijgewerkt ](assets/read-updated.png)


>[!NOTE]
>
> U kunt de configuratie SharePoint List maken en gebruiken met het formuliergegevensmodel in een adaptief formulier, om gegevens of gegenereerd document met record op te slaan in een SharePoint-lijst. Verwijs naar [ verbind een Aangepast Vorm met de Lijst van Microsoft® SharePoint ](/help/forms/using/configuring-submit-actions.md#create-a-sharepoint-list-configuration), voor gedetailleerde stappen.