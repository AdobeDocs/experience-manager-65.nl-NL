---
title: Gegevensbronnen configureren
seo-title: Gegevensbronnen configureren
description: Leer hoe u verschillende typen gegevensbronnen configureert en hoe u modellen met formuliergegevens maakt.
seo-description: Leer hoe u verschillende typen gegevensbronnen configureert en hoe u modellen met formuliergegevens maakt.
uuid: 12360c8c-b596-4f9b-837a-10a8ff5c7448
topic-tags: integration
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 9d78a6dc-fc9c-415b-b817-164fe6648b30
docset: aem65
translation-type: tm+mt
source-git-commit: 19ee2722bc73f67b77cc08dd2a634328ba5269ec
workflow-type: tm+mt
source-wordcount: '1843'
ht-degree: 0%

---


# Gegevensbronnen configureren{#configure-data-sources}

![](do-not-localize/data-integeration.png)

Met AEM Forms Data Integration kunt u verschillende gegevensbronnen configureren en verbinden. De volgende types worden gesteund uit-van-de-doos. Met weinig aanpassing kunt u echter ook andere gegevensbronnen integreren.

* Relationele databases - MySQL, Microsoft SQL Server, IBM DB2 en Oracle RDBMS
* Gebruikersprofiel AEM
* RESTful-webservices
* SOAP-webservices
* OData-diensten

De integratie van gegevens steunt OAuth2.0, Basisauthentificatie, en API Zeer belangrijke authentificatietypes out-of-the-box, en staat het uitvoeren van douaneauthentificatie voor de toegang tot van de Webdiensten toe. Terwijl RESTful, op ZEEP-Gebaseerde, en de diensten OData in de Diensten van de Wolk van AEM worden gevormd, JDBC voor relationele gegevensbestanden en schakelaar voor AEM gebruikersprofiel worden gevormd in AEM Webconsole.

## Relationele database {#configure-relational-database} configureren

U kunt relationele gegevensbestanden vormen gebruikend AEM de Configuratie van de Console van het Web. Ga als volgt te werk:

1. Ga naar AEM webconsole op https://server:host/system/console/configMgr.
1. Zoek naar configuratie **[!UICONTROL Apache Sling Connection Pooled DataSource]**. Tik om de configuratie te openen in de bewerkingsmodus.
1. In de configuratiedialoog, specificeer de details voor het gegevensbestand u, zoals wilt vormen:

   * Naam van de gegevensbron
   * Het bezit van de gegevensbrondienst dat de naam van de gegevensbron opslaat
   * Java-klassenaam voor het JDBC-stuurprogramma
   * URI voor JDBC-verbinding
   * Gebruikersnaam en wachtwoord om verbinding te maken met het JDBC-stuurprogramma

   >[!NOTE]
   >
   >Zorg ervoor dat u gevoelige informatie zoals wachtwoorden codeert alvorens de gegevensbron te vormen. Coderen:
   >
   >    
   >    
   >    1. Ga naar https://&#39;[server]:[port]&#39;/system/console/crypto.
   >    1. Geef in het veld **[!UICONTROL Plain Text]** het wachtwoord of een willekeurige tekenreeks op die u wilt coderen en tikken **[!UICONTROL Protect]**.

   >    
   >    
   >    
   >De gecodeerde tekst wordt weergegeven in het veld Beveiligde tekst dat u in de configuratie kunt opgeven.

1. Schakel **[!UICONTROL Test on Borrow]** of **[!UICONTROL Test on Return]** in om op te geven dat de objecten worden gevalideerd voordat ze van en naar de pool worden geleend of geretourneerd.
1. Geef een SQL SELECT-query op in het veld **[!UICONTROL Validation Query]** om verbindingen vanuit de pool te valideren. De query moet ten minste één rij retourneren. Geef op basis van uw database een van de volgende opties op:

   * SELECT 1 (MySQL en MS SQL)
   * SELECTEER 1 vanuit dual (Oracle)

1. Tik **[!UICONTROL Save]** om de configuratie op te slaan.

## AEM gebruikersprofiel {#configure-aem-user-profile} configureren

U kunt AEM gebruikersprofiel vormen gebruikend de Configuratie van de Verbinding van het Profiel van de Gebruiker in AEM Console van het Web. Ga als volgt te werk:

1. Ga naar AEM webconsole op https://&#39;[server]:[poort]&#39;system/console/configMgr.
1. Zoek **[!UICONTROL AEM Forms Data Integrations - User Profile Connector Configuration]** en tik om de configuratie in Edit wijze te openen.
1. In het dialoogvenster Configuratie gebruikersprofiel-aansluiting kunt u eigenschappen van gebruikersprofielen toevoegen, verwijderen of bijwerken. De opgegeven eigenschappen zijn beschikbaar voor gebruik in het formuliergegevensmodel. Gebruik de volgende indeling om gebruikersprofieleigenschappen op te geven:

   `name=[property_name_with_location_in_user_profile],type=[property_type]`

   Voorbeelden:

   * `name=profile/phoneNumber,type=string`
   * `name=profile/empLocation/*/city,type=string`

   >[!NOTE]
   >
   >Met ***** in het bovenstaande voorbeeld worden alle knooppunten onder de `profile/empLocation/`-node in AEM gebruikersprofiel in de CRXDE-structuur aangegeven. Dit betekent dat het formuliergegevensmodel toegang heeft tot de eigenschap `city` van het type `string` in elk knooppunt onder het knooppunt `profile/empLocation/`. Nochtans, moeten de knopen die het gespecificeerde bezit bevatten een verenigbare structuur volgen.

1. Tik **[!UICONTROL Save]** om de configuratie op te slaan.

## Map configureren voor configuraties van cloudservices {#cloud-folder}

>[!NOTE]
Configuratie voor map met cloudservices is vereist voor het configureren van cloudservices voor RESTful-, SOAP- en OData-services.

Alle configuraties van de cloudservice in AEM worden geconsolideerd in de map `/conf` in AEM opslagplaats. Standaard bevat de map `conf` de map `global` waarin u cloudserviceconfiguraties kunt maken. U moet deze echter handmatig inschakelen voor cloudconfiguraties. U kunt ook extra mappen maken in `conf` om configuraties voor cloudservices te maken en in te delen.

De map configureren voor configuraties van cloudservices:

1. Ga naar **[!UICONTROL Tools > General > Configuration Browser]**.
   * Zie de [Configuration Browser](/help/sites-administering/configurations.md) documentatie voor meer informatie.
1. Ga als volgt te werk om de algemene map voor cloudconfiguraties in te schakelen of sla deze stap over om een andere map voor cloudserviceconfiguraties te maken en te configureren.

   1. Selecteer in **[!UICONTROL Configuration Browser]** de map `global` en tik **[!UICONTROL Properties]**.

   1. Schakel in het dialoogvenster **[!UICONTROL Configuration Properties]** **[!UICONTROL Cloud Configurations]** in.

   1. Tik **[!UICONTROL Save & Close]** om de configuratie op te slaan en het dialoogvenster af te sluiten.

1. Tik in **[!UICONTROL Configuration Browser]** op **[!UICONTROL Create]**.
1. Geef in het dialoogvenster **[!UICONTROL Create Configuration]** een titel op voor de map en schakel **[!UICONTROL Cloud Configurations]** in.
1. Tik **[!UICONTROL Create]** om de map te maken die geschikt is voor configuraties van cloudservices.

## RESTful-webservices {#configure-restful-web-services} configureren

RESTful Webdienst kan worden beschreven gebruikend [de Specificaties van de Wager](https://swagger.io/specification/) in formaat JSON of YAML in een Swagger definitiedossier. Als u de RESTful-webservice in AEM-cloudservices wilt configureren, dient u ervoor te zorgen dat het Swagger-bestand zich op uw bestandssysteem bevindt of de URL waar het bestand wordt gehost.

Doe het volgende de diensten RESTful vormen:

1. Ga naar **[!UICONTROL Tools > Cloud Services > Data Sources]**. Tik om de map te selecteren waarin u een cloudconfiguratie wilt maken.

   Zie [Map configureren voor configuraties van cloudservices](../../forms/using/configure-data-sources.md#cloud-folder) voor informatie over het maken en configureren van een map voor configuraties van cloudservices.

1. Tik **[!UICONTROL Create]** om **[!UICONTROL Create Data Source Configuration wizard]** te openen. Geef een naam en eventueel een titel voor de configuratie op, selecteer **[!UICONTROL RESTful Service]** in de vervolgkeuzelijst **[!UICONTROL Service Type]**, blader optioneel naar een miniatuurafbeelding voor de configuratie en selecteer **[!UICONTROL Next]**.
1. Specificeer de volgende details voor de RESTful dienst:

   * Selecteer URL of Dossier van de Bron van de Wagger drop-down, en specificeer dienovereenkomstig Swagger URL aan het de definitiedossier van de Swagger of upload het dossier van de Swagger van uw lokaal dossiersysteem.
   * Op basis van de invoer van de bron van de wagen worden de volgende velden vooraf gevuld met waarden:

      * Schema: De overdrachtprotocollen die door REST API worden gebruikt. Het aantal schematypen die in de drop-down lijst worden getoond hangt van de regelingen af die in de bron van de Swagger worden bepaald.
      * Host: De domeinnaam of het IP-adres van de host die de REST API aanbiedt. Het is een verplicht veld.
      * Basispad: Het URL-voorvoegsel voor alle API-paden. Het is een optioneel veld.\
         Bewerk indien nodig de vooraf ingevulde waarden voor deze velden.
   * Selecteer het authentificatietype — niets, OAuth2.0, Basisauthentificatie, Sleutel API, Douane Authentificatie, of Wederzijdse Authentificatie — om tot de RESTful dienst toegang te hebben, en dienovereenkomstig details voor authentificatie te verstrekken.

   Als u **[!UICONTROL API Key]** als authentificatietype selecteert, specificeer de waarde voor de sleutel van API. De API-sleutel kan als aanvraagheader of als queryparameter worden verzonden. Selecteer een van deze opties in de vervolgkeuzelijst **[!UICONTROL Location]** en geef de naam van de koptekst of de queryparameter dienovereenkomstig op in het veld **[!UICONTROL Parameter Name]**.

   Als u **[!UICONTROL Mutual Authentication]** als authentificatietype selecteert, zie [Op certificaat-gebaseerde wederzijdse authentificatie voor RESTful en de Webdiensten van de ZEEP](#mutual-authentication).

1. Tik **[!UICONTROL Create]** om de cloudconfiguratie voor de RESTful-service te maken.

### Formuliergegevensmodel HTTP-clientconfiguratie om prestaties te optimaliseren {#fdm-http-client-configuration}

[!DNL Experience Manager Forms] formuliergegevensmodel bij integratie met RESTful-webservices als gegevensbron bevat HTTP-clientconfiguraties voor optimalisatie van prestaties.
Voer de volgende stappen uit om de HTTP-client van het formuliergegevensmodel te configureren:

1. Meld u aan bij [!DNL Experience Manager Forms] Instantie auteur als beheerder en ga naar [!DNL Experience Manager] bundels voor webconsole. De standaard-URL is [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr).

1. Tik op **[!UICONTROL Form Data Model Http Client Configuration for REST data source]**.

1. In het dialoogvenster [!UICONTROL Form Data Model Http Client Configuration for REST data source]:

   * Geef het maximale aantal toegestane verbindingen op tussen het formuliergegevensmodel en RESTful-webservices in het veld **[!UICONTROL Connection limit in total]**. De standaardwaarde is 20 verbindingen.

   * Specificeer het maximumaantal toegestane verbindingen voor elke route op het **[!UICONTROL Connection limit on per route basis]** gebied. De standaardwaarde is 2 verbindingen.

   * Geef in het veld **[!UICONTROL Keep alive]** de duur op waarvoor een blijvende HTTP-verbinding in leven blijft. De standaardwaarde is 15 seconden.

   * Geef in het veld **[!UICONTROL Connection timeout]** de duur op waarvoor de [!DNL Experience Manager Forms]-server wacht tot een verbinding tot stand is gebracht. De standaardwaarde is 10 seconden.

   * Geef de maximale periode voor inactiviteit op tussen twee gegevenspakketten in het veld **[!UICONTROL Socket timeout]**. De standaardwaarde is 30 seconden.


## SOAP-webservices configureren {#configure-soap-web-services}

Webservices op basis van SOAP worden beschreven met de [WSDL-specificaties (Web Services Description Language)](https://www.w3.org/TR/wsdl). Als u op SOAP gebaseerde webservice wilt configureren in AEM-cloudservices, moet u de WSDL-URL voor de webservice hebben en het volgende doen:

1. Ga naar **[!UICONTROL Tools > Cloud Services > Data Sources]**. Tik om de map te selecteren waarin u een cloudconfiguratie wilt maken.

   Zie [Map configureren voor configuraties van cloudservices](../../forms/using/configure-data-sources.md#cloud-folder) voor informatie over het maken en configureren van een map voor configuraties van cloudservices.

1. Tik **[!UICONTROL Create]** om **[!UICONTROL Create Data Source Configuration wizard]** te openen. Geef een naam en eventueel een titel voor de configuratie op, selecteer **[!UICONTROL SOAP Web Service]** in de vervolgkeuzelijst **[!UICONTROL Service Type]**, blader optioneel naar een miniatuurafbeelding voor de configuratie en selecteer **[!UICONTROL Next]**.
1. Geef het volgende op voor de SOAP-webservice:

   * WSDL-URL voor de webservice.
   * Service Endpoint. Specificeer een waarde op dit gebied om het de diensteindpunt met voeten te treden dat in WSDL wordt vermeld.
   * Selecteer het authentificatietype — niets, OAuth2.0, Basisauthentificatie, de Authentificatie van de Douane, Symbolische X509, of Wederzijdse Authentificatie — om tot de dienst van de ZEEP toegang te hebben, en dienovereenkomstig de details voor authentificatie te verstrekken.

      Als u **[!UICONTROL X509 Token]** als Type van Authentificatie selecteert, vorm het X509- certificaat. Zie [Certificaten instellen](install-configure-document-services.md#set-up-certificates-for-reader-extension-and-encryption-service) voor meer informatie.
Geef de alias KeyStore voor het X509-certificaat op in het veld **[!UICONTROL Key Alias]**. Geef de tijd in seconden op tot het verificatieverzoek geldig blijft in het veld **[!UICONTROL Time To Live]**. Selecteer desgewenst om de berichttekst, de tijdstempelkop of beide te ondertekenen.

      Als u **[!UICONTROL Mutual Authentication]** als authentificatietype selecteert, zie [Op certificaat-gebaseerde wederzijdse authentificatie voor RESTful en de Webdiensten van de ZEEP](#mutual-authentication).

1. Tik op **[!UICONTROL Create]** om de wolkenconfiguratie voor de SOAP-webservice te maken.

## OData-services configureren {#config-odata}

De dienst OData wordt geïdentificeerd door zijn de dienstwortel URL. Als u een OData-service in AEM-cloudservices wilt configureren, moet u ervoor zorgen dat u over de URL van de servicehoofdmap voor de service beschikt en moet u het volgende doen:

>[!NOTE]
Voor geleidelijke gids om de Dynamica 365 van Microsoft, online of op-gebouw te vormen, zie [Configuratie van de Dynamica OData van Microsoft](/help/forms/using/ms-dynamics-odata-configuration.md).

1. Ga naar **[!UICONTROL Tools > Cloud Services > Data Sources]**. Tik om de map te selecteren waarin u een cloudconfiguratie wilt maken.

   Zie [Map configureren voor configuraties van cloudservices](../../forms/using/configure-data-sources.md#cloud-folder) voor informatie over het maken en configureren van een map voor configuraties van cloudservices.

1. Tik **[!UICONTROL Create]** om **[!UICONTROL Create Data Source Configuration wizard]** te openen. Geef een naam en eventueel een titel voor de configuratie op, selecteer **[!UICONTROL OData Service]** in de vervolgkeuzelijst **[!UICONTROL Service Type]**, blader optioneel naar een miniatuurafbeelding voor de configuratie en selecteer **[!UICONTROL Next]**.
1. Specificeer de volgende details voor de dienst OData:

   * Service Root URL voor de OData-service die moet worden geconfigureerd.
   * Selecteer het authentificatietype — niets, OAuth2.0, Basisauthentificatie, of de Authentificatie van de Douane — om tot de dienst toegang te hebben OData, en dienovereenkomstig de details voor authentificatie te verstrekken.

   >[!NOTE]
   U moet OAuth 2.0 authentificatietype selecteren om met de diensten van de Dynamiek van Microsoft te verbinden gebruikend eindpunt OData als de dienstwortel.

1. Tik **Maak** om de cloudconfiguratie voor de OData-service te maken.

## Op certificaten gebaseerde wederzijdse verificatie voor RESTful- en SOAP-webservices {#mutual-authentication}

Wanneer u wederzijdse verificatie inschakelt voor het gegevensmodel van het formulier, wordt elkaars identiteit geverifieerd door zowel het gegevensbrongegevensmodel als het gegevensgegevensmodel van AEM server waarop formuliergegevens worden uitgevoerd, voordat gegevens worden gedeeld. U kunt wederzijdse authentificatie voor REST en SOAP gebaseerde verbindingen (gegevensbronnen) gebruiken. Om wederzijdse authentificatie voor een model van vormgegevens op uw milieu van AEM Forms te vormen:

1. Upload de persoonlijke sleutel (certificaat) naar de [!DNL AEM Forms]-server. De persoonlijke sleutel uploaden:
   1. Meld u als beheerder aan bij uw [!DNL AEM Forms]-server.
   1. Ga naar **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Users]**. Selecteer de `fd-cloudservice` gebruiker en tik **[!UICONTROL Properties]**.
   1. Open het tabblad **[!UICONTROL Keystore]**, vouw de optie **[!UICONTROL Add Private Key from KeyStore file]** uit, upload het KeyStore-bestand, geef de aliassen, wachtwoorden op en tik **[!UICONTROL Submit]**. Het certificaat wordt geüpload.  De alias van de persoonlijke sleutel wordt vermeld in het certificaat en ingesteld tijdens het maken van het certificaat.
1. Upload vertrouwenscertificaat naar Global Trust Store. Het certificaat uploaden:
   1. Ga naar **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Trust Store]**.
   1. Vouw de optie **[!UICONTROL Add Certificate from CER file]** uit, tik **[!UICONTROL Select Certificate File]**, upload het certificaat en tik **[!UICONTROL Submit]**.
1. Configureer [SOAP](#configure-soap-web-services) of [RESTful](#configure-restful-web-services)-webservices als gegevensbron en selecteer **[!UICONTROL Mutual authentication]** als verificatietype. Als u meerdere zelfondertekende certificaten configureert voor `fd-cloudservice`-gebruiker, geeft u de naam van de sleutelalias voor het certificaat op.

## Volgende stappen {#next-steps}

U hebt de gegevensbronnen geconfigureerd. Vervolgens kunt u een formuliergegevensmodel maken of als u al een formuliergegevensmodel zonder gegevensbron hebt gemaakt, kunt u dit koppelen aan de zojuist geconfigureerde gegevensbronnen. Zie [Formuliergegevensmodel maken](/help/forms/using/create-form-data-models.md) voor meer informatie.
