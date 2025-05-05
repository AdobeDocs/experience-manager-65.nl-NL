---
title: Gegevensbronnen configureren
description: Leer hoe u verschillende typen gegevensbronnen configureert, zodat u formuliergegevensmodellen kunt maken.
topic-tags: integration
products: SG_EXPERIENCEMANAGER/6.5/FORMS
docset: aem65
feature: Form Data Model
exl-id: 7a1d9d57-66f4-4f20-91c2-ace5a71a52f2
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '1896'
ht-degree: 0%

---

# Gegevensbronnen configureren{#configure-data-sources}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/integrate/use-form-data-model/configure-data-sources.html?lang=nl-NL) |
| AEM 6,5 | Dit artikel |


![ de Integratie van Gegevens ](do-not-localize/data-integeration.png)

Met AEM Forms Data Integration kunt u verschillende gegevensbronnen configureren en verbinden. De volgende types worden gesteund uit-van-de-doos. Met weinig aanpassing kunt u echter ook andere gegevensbronnen integreren.

* Relationele databases - MySQL, Microsoft SQL Server, IBM DB2, Oracle RDBMS, postgreSQL en Sybase
* Gebruikersprofiel AEM
* RESTful-webservices
* SOAP webservices
* OData-diensten

De integratie van gegevens steunt OAuth2.0 ([ Code van de Vergunning ](https://oauth.net/2/grant-types/authorization-code/), [ de Verantwoordelijkheden van de Cliënt ](https://oauth.net/2/grant-types/client-credentials/)), Basisauthentificatie, en API Zeer belangrijke authentificatietypen uit-van-de-doos, en staat het uitvoeren van douaneauthentificatie voor de toegang tot van de Webdiensten toe. Terwijl RESTful, op SOAP-Gebaseerd, en de diensten OData in AEM Cloud Servicen worden gevormd, wordt JDBC voor relationele gegevensbestanden en schakelaar voor AEM gebruikersprofiel gevormd in AEM Webconsole.

## Relationele database configureren {#configure-relational-database}

U kunt relationele gegevensbestanden vormen gebruikend AEM de Configuratie van de Console van het Web. Ga als volgt te werk:

1. Ga naar AEM webconsole op `https://server:host/system/console/configMgr` .
1. Zoek naar **[!UICONTROL Apache Sling Connection Pooled DataSource]** configuratie. Selecteer deze optie om de configuratie te openen in de bewerkingsmodus.
1. In de configuratiedialoog, specificeer de details voor het gegevensbestand u, zoals wilt vormen:

   * Naam van de gegevensbron
   * Het bezit van de gegevensbrondienst dat de naam van de gegevensbron opslaat
   * Java-klassenaam voor het JDBC-stuurprogramma
   * URI voor JDBC-verbinding
   * Gebruikersnaam en wachtwoord voor verbinding met het JDBC-stuurprogramma

   >[!NOTE]
   >
   >Zorg ervoor dat u gevoelige informatie zoals wachtwoorden codeert alvorens de gegevensbron te vormen. Coderen:
   >
   > 1. Ga naar https://&#39; [ server ]:[ haven ]&#39;/system/console/crypto.
   > 1. Geef in het veld **[!UICONTROL Plain Text]** het wachtwoord of een willekeurige tekenreeks op die u wilt versleutelen en selecteer **[!UICONTROL Protect]** .
   >
   >De gecodeerde tekst wordt weergegeven in het veld Beveiligde tekst dat u in de configuratie kunt opgeven.

1. Schakel **[!UICONTROL Test on Borrow]** of **[!UICONTROL Test on Return]** in om op te geven dat de objecten worden gevalideerd voordat ze van en naar de pool worden geleend of geretourneerd.
1. Geef een SQL SELECT-query op in het veld **[!UICONTROL Validation Query]** om verbindingen vanuit de pool te valideren. De query moet ten minste één rij retourneren. Geef op basis van uw database een van de volgende opties op:

   * SELECT 1 (MySQL en MS SQL)
   * SELECTEER 1 uit twee items (Oracle)

1. Selecteer **[!UICONTROL Save]** om de configuratie op te slaan.

   >[!NOTE]
   >
   > Als uw Forms-gegevensmodel een object bevat dat een gereserveerd trefwoord is voor uw relationele database, kan dit leiden tot problemen met het toevoegen, bijwerken of ophalen van gegevens. Vermijd dus het gebruik van dergelijke objecten in uw formuliergegevensmodel.

## Gebruikersprofiel AEM configureren {#configure-aem-user-profile}

U kunt AEM gebruikersprofiel vormen gebruikend de Configuratie van de Verbinding van het Profiel van de Gebruiker in AEM Console van het Web. Ga als volgt te werk:

1. Ga naar AEM Webconsole in https://&#39; [ server ]:[ haven ] systeem/console/configMgr.
1. Zoek **[!UICONTROL AEM Forms Data Integrations - User Profile Connector Configuration]** en selecteer om de configuratie in Edit wijze te openen.
1. In het dialoogvenster Configuratie gebruikersprofiel-aansluiting kunt u eigenschappen van gebruikersprofielen toevoegen, verwijderen of bijwerken. De opgegeven eigenschappen zijn beschikbaar voor gebruik in het formuliergegevensmodel. Gebruik de volgende indeling om gebruikersprofieleigenschappen op te geven:

   `name=[property_name_with_location_in_user_profile],type=[property_type]`

   Voorbeelden:

   * `name=profile/phoneNumber,type=string`
   * `name=profile/empLocation/*/city,type=string`

   >[!NOTE]
   >
   >In het bovenstaande voorbeeld geeft **&#42;** alle knooppunten onder het knooppunt `profile/empLocation/` in AEM gebruikersprofiel in de CRXDE-structuur aan. Dit betekent dat het formuliergegevensmodel toegang heeft tot de eigenschap `city` van het type `string` in elk knooppunt onder het knooppunt `profile/empLocation/` . Nochtans, moeten de knopen die het gespecificeerde bezit bevatten een verenigbare structuur volgen.

1. Selecteer **[!UICONTROL Save]** om de configuratie op te slaan.

## Map configureren voor configuraties van cloudservices {#cloud-folder}

>[!NOTE]
>
>Configuratie voor map met cloudservices is vereist voor het configureren van cloudservices voor RESTful-, SOAP- en OData-services.

Alle configuraties van de cloudservice in AEM worden geconsolideerd in de map `/conf` in AEM opslagplaats. Standaard bevat de map `conf` de map `global` waarin u cloudserviceconfiguraties kunt maken. U moet deze optie echter handmatig inschakelen voor cloudconfiguraties. U kunt ook extra mappen maken in `conf` om configuraties voor cloudservices te maken en in te delen.

De map configureren voor configuraties van cloudservices:

1. Ga naar **[!UICONTROL Tools > General > Configuration Browser]** .
   * Zie Browser van de Configuratie [&#128279;](/help/sites-administering/configurations.md) documentatie 0&rbrace; &lbrace;voor meer informatie.
1. Ga als volgt te werk om de algemene map voor cloudconfiguraties in te schakelen of sla deze stap over om een andere map voor cloudserviceconfiguraties te maken en te configureren.

   1. Selecteer in **[!UICONTROL Configuration Browser]** de map `global` en selecteer **[!UICONTROL Properties]** .

   1. Schakel **[!UICONTROL Cloud Configurations]** in het dialoogvenster **[!UICONTROL Configuration Properties]** in.

   1. Selecteer **[!UICONTROL Save & Close]** om de configuratie op te slaan en het dialoogvenster af te sluiten.

1. Selecteer **[!UICONTROL Create]** in de **[!UICONTROL Configuration Browser]** .
1. Geef in het dialoogvenster **[!UICONTROL Create Configuration]** een titel op voor de map en schakel **[!UICONTROL Cloud Configurations]** in.
1. Selecteer **[!UICONTROL Create]** om de map te maken die is ingeschakeld voor cloudserviceconfiguraties.

## RESTful-webservices configureren {#configure-restful-web-services}

De RESTful Webdienst kan worden beschreven gebruikend [ de specificaties van de Wagger ](https://swagger.io/specification/) in formaat JSON of YAML in een de definitiedossier van de Wagger. Als u de RESTful-webservice in AEM cloudservices wilt configureren, dient u ervoor te zorgen dat het Swagger-bestand zich op uw bestandssysteem bevindt of de URL waar het bestand wordt gehost.

Doe het volgende de diensten RESTful vormen:

1. Ga naar **[!UICONTROL Tools > Cloud Services > Data Sources]** . Selecteer deze optie om de map te selecteren waarin u een cloudconfiguratie wilt maken.

   Zie [ omslag voor de configuraties van de wolkendienst ](../../forms/using/configure-data-sources.md#cloud-folder) voor informatie over het creëren van en het vormen van een omslag voor de configuraties van de wolkendienst vormen.

1. Selecteer **[!UICONTROL Create]** om **[!UICONTROL Create Data Source Configuration wizard]** te openen. Geef een naam en eventueel een titel voor de configuratie op, selecteer **[!UICONTROL RESTful Service]** in de vervolgkeuzelijst **[!UICONTROL Service Type]** , blader optioneel naar een miniatuurafbeelding en selecteer een miniatuurafbeelding voor de configuratie en selecteer **[!UICONTROL Next]** .
1. Specificeer de volgende details voor de RESTful dienst:

   * Selecteer URL of Dossier van Swagger Source drop-down, en specificeer dienovereenkomstig Swagger URL aan het de definitiedossier van de Swagger of upload het dossier van de Swagger van uw lokaal dossiersysteem.
   * Op basis van de invoer van Swagger Source worden de volgende velden vooraf gevuld met waarden:

      * Schema: de overdrachtprotocollen die door de REST API worden gebruikt. Het aantal schematypen die in de drop-down lijst worden getoond hangt van de regelingen af die in de bron van de Swagger worden bepaald.
      * Host: de domeinnaam of het IP-adres van de host die de REST API aanbiedt. Het is een verplicht veld.
      * Basispad: het URL-voorvoegsel voor alle API-paden. Het is een optioneel veld.\
        Bewerk indien nodig de vooraf ingevulde waarden voor deze velden.

   * Selecteer het authentificatietype — niets, OAuth2.0 ([ Code van de Vergunning ](https://oauth.net/2/grant-types/authorization-code/), [ de Verantwoordelijkheden van de Cliënt ](https://oauth.net/2/grant-types/client-credentials/)), Basisauthentificatie, Sleutel API, Douane Authentificatie, of Wederzijdse Authentificatie — om tot de RESTful dienst toegang te hebben, en dienovereenkomstig details voor authentificatie te verstrekken.

   Als u **[!UICONTROL API Key]** selecteert als verificatietype, geeft u de waarde voor de API-sleutel op. De API-sleutel kan als aanvraagheader of als queryparameter worden verzonden. Selecteer een van deze opties in de vervolgkeuzelijst **[!UICONTROL Location]** en geef de naam van de header of de queryparameter dienovereenkomstig op in het veld **[!UICONTROL Parameter Name]** .

   Als u **[!UICONTROL Mutual Authentication]** als authentificatietype selecteert, zie [ Op certificaat-gebaseerde wederzijdse authentificatie voor RESTful en SOAP Webdiensten ](#mutual-authentication).

1. Selecteer **[!UICONTROL Create]** om de wolkenconfiguratie voor de RESTful dienst tot stand te brengen.

### Het model van de gegevens van de vormHTTP cliëntconfiguratie om prestaties te optimaliseren {#fdm-http-client-configuration}

[!DNL Experience Manager Forms] -formuliergegevensmodel wanneer integratie met RESTful-webservices als gegevensbron HTTP-clientconfiguraties bevat voor optimalisatie van prestaties.
Voer de volgende stappen uit om de HTTP-client van het formuliergegevensmodel te configureren:

1. Meld u aan bij [!DNL Experience Manager Forms] Instantie auteur als beheerder en ga naar [!DNL Experience Manager] -bundels voor webconsoles. Het gebrek URL is [ https://localhost:4502/system/console/configMgr ](https://localhost:4502/system/console/configMgr).

1. Selecteer **[!UICONTROL Form Data Model Http Client Configuration for REST data source]** .

1. In het dialoogvenster [!UICONTROL Form Data Model Http Client Configuration for REST data source] :

   * Geef het maximale aantal toegestane verbindingen op tussen het gegevensmodel van het formulier en de RESTful-webservices in het veld **[!UICONTROL Connection limit in total]** . De standaardwaarde is 20 verbindingen.

   * Geef het maximale aantal toegestane verbindingen voor elke route op in het veld **[!UICONTROL Connection limit on per route basis]** . De standaardwaarde is 2 verbindingen.

   * Geef in het veld **[!UICONTROL Keep alive]** de duur op waarvoor een permanente HTTP-verbinding in leven blijft. De standaardwaarde is 15 seconden.

   * Geef in het veld **[!UICONTROL Connection timeout]** de tijdsduur op waarvoor de [!DNL Experience Manager Forms] -server wacht tot een verbinding tot stand is gebracht. De standaardwaarde is 10 seconden.

   * Geef in het veld **[!UICONTROL Socket timeout]** de maximale periode voor inactiviteit op tussen twee gegevenspakketten. De standaardwaarde is 30 seconden.

## Webservices configureren SOAP {#configure-soap-web-services}

Op SOAP gebaseerde Webdiensten worden beschreven gebruikend {de specificaties van de Beschrijving van de Diensten van het Web van 0} van de Taal (WSDL) [&#128279;](https://www.w3.org/TR/wsdl).  Als u op SOAP gebaseerde webservice wilt configureren in AEM cloudservices, moet u de WSDL-URL voor de webservice hebben en het volgende doen:

1. Ga naar **[!UICONTROL Tools > Cloud Services > Data Sources]** . Selecteer deze optie om de map te selecteren waarin u een cloudconfiguratie wilt maken.

   Zie [ omslag voor de configuraties van de wolkendienst ](../../forms/using/configure-data-sources.md#cloud-folder) voor informatie over het creëren van en het vormen van een omslag voor de configuraties van de wolkendienst vormen.

1. Selecteer **[!UICONTROL Create]** om **[!UICONTROL Create Data Source Configuration wizard]** te openen. Geef een naam en eventueel een titel voor de configuratie op, selecteer **[!UICONTROL SOAP Web Service]** in de vervolgkeuzelijst **[!UICONTROL Service Type]** , blader optioneel naar een miniatuurafbeelding en selecteer een miniatuurafbeelding voor de configuratie en selecteer **[!UICONTROL Next]** .
1. Geef het volgende op voor de SOAP webservice:

   * WSDL-URL voor de webservice.
   * Service Endpoint. Specificeer een waarde op dit gebied om het de diensteindpunt met voeten te treden dat in WSDL wordt vermeld.
   * Selecteer het authentificatietype — niets, OAuth2.0 ([ Code van de Vergunning ](https://oauth.net/2/grant-types/authorization-code/), [ de Verantwoordelijkheden van de Cliënt ](https://oauth.net/2/grant-types/client-credentials/)), Basisauthentificatie, de Authentificatie van de Douane, Symbolische X509, of Wederzijdse Authentificatie — om tot de SOAP dienst toegang te hebben, en dienovereenkomstig de details voor authentificatie te verstrekken.

     Als u **[!UICONTROL X509 Token]** selecteert als het verificatietype, configureert u het X509-certificaat. Voor meer informatie, zie [ de certificaten van de Opstelling ](install-configure-document-services.md#set-up-certificates-for-reader-extension-and-encryption-service).
Geef de alias KeyStore voor het X509-certificaat op in het veld **[!UICONTROL Key Alias]** . Geef de tijd in seconden op totdat de verificatieaanvraag geldig blijft in het veld **[!UICONTROL Time To Live]** . Selecteer desgewenst om de berichttekst, de tijdstempelkop of beide te ondertekenen.

     Als u **[!UICONTROL Mutual Authentication]** als authentificatietype selecteert, zie [ Op certificaat-gebaseerde wederzijdse authentificatie voor RESTful en SOAP Webdiensten ](#mutual-authentication).

1. Selecteer **[!UICONTROL Create]** om de cloudconfiguratie voor de SOAP webservice te maken.

## OData-services configureren {#config-odata}

De dienst OData wordt geïdentificeerd door zijn de dienstwortel URL. Als u een OData-service in AEM cloudservices wilt configureren, moet u ervoor zorgen dat u over de URL van de servicehoofdmap voor de service beschikt en moet u het volgende doen:

>[!NOTE]
>
>Het gegevensmodel van de vorm steunt [ OData versie 4 ](https://www.odata.org/documentation/).
>Voor geleidelijke gids om Dynamiek 365 van Microsoft, online of op-gebouw te vormen, zie {de Configuratie van de Dynamica OData van 0} Microsoft [&#128279;](/help/forms/using/ms-dynamics-odata-configuration.md).

1. Ga naar **[!UICONTROL Tools > Cloud Services > Data Sources]** . Selecteer deze optie om de map te selecteren waarin u een cloudconfiguratie wilt maken.

   Zie [ omslag voor de configuraties van de wolkendienst ](../../forms/using/configure-data-sources.md#cloud-folder) voor informatie over het creëren van en het vormen van een omslag voor de configuraties van de wolkendienst vormen.

1. Selecteer **[!UICONTROL Create]** om **[!UICONTROL Create Data Source Configuration wizard]** te openen. Geef een naam en eventueel een titel voor de configuratie op, selecteer **[!UICONTROL OData Service]** in de vervolgkeuzelijst **[!UICONTROL Service Type]** , blader optioneel naar een miniatuurafbeelding en selecteer een miniatuurafbeelding voor de configuratie en selecteer **[!UICONTROL Next]** .
1. Specificeer de volgende details voor de dienst OData:

   * Service Root URL voor de OData-service die moet worden geconfigureerd.
   * Selecteer het authentificatietype — niets, OAuth2.0 ([ de Code van de Vergunning ](https://oauth.net/2/grant-types/authorization-code/), [ de Verantwoordelijkheden van de Cliënt ](https://oauth.net/2/grant-types/client-credentials/)), BasisAuthentificatie, of de Authentificatie van de Douane — om tot de dienst toegang te hebben OData, en dienovereenkomstig de details voor authentificatie te verstrekken.

   >[!NOTE]
   >
   >Selecteer OAuth 2.0 authentificatietype om met de diensten van de Dynamiek van Microsoft te verbinden gebruikend eindpunt OData als de de dienstwortel.

1. Selecteer **creeer** om de wolkenconfiguratie voor de dienst te creëren OData.

## Wederzijdse verificatie op basis van certificaten voor RESTful- en SOAP-webservices {#mutual-authentication}

Wanneer u wederzijdse verificatie inschakelt voor het gegevensmodel van het formulier, wordt elkaars identiteit geverifieerd door zowel het gegevensbrongegevensmodel als het gegevensgegevensmodel van AEM server waarop formuliergegevens worden uitgevoerd, voordat gegevens worden gedeeld. U kunt wederzijdse authentificatie voor REST en SOAP gebaseerde verbindingen (gegevensbronnen) gebruiken. Om wederzijdse authentificatie voor een model van vormgegevens op uw milieu van AEM Forms te vormen:

1. Upload de persoonlijke sleutel (certificaat) naar de [!DNL AEM Forms] -server. De persoonlijke sleutel uploaden:
   1. Meld u als beheerder aan bij uw [!DNL AEM Forms] -server.
   1. Ga naar **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Users]**. Selecteer de gebruiker `fd-cloudservice` en selecteer **[!UICONTROL Properties]** .
   1. Open het tabblad **[!UICONTROL Keystore]** , vouw de optie **[!UICONTROL Add Private Key from KeyStore file]** uit, upload het KeyStore-bestand, geef de aliassen, wachtwoorden op en selecteer **[!UICONTROL Submit]** . Het certificaat wordt geüpload.  De alias van de persoonlijke sleutel wordt vermeld in het certificaat en ingesteld tijdens het maken van het certificaat.
1. Upload vertrouwenscertificaat naar Global Trust Store. Het certificaat uploaden:
   1. Navigeer naar **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Trust Store]** .
   1. Vouw de optie **[!UICONTROL Add Certificate from CER file]** uit, selecteer **[!UICONTROL Select Certificate File]** , upload het certificaat en selecteer **[!UICONTROL Submit]** .
1. Vorm [ SOAP ](#configure-soap-web-services) of [ RESTful ](#configure-restful-web-services) Webdiensten als gegevensbron en selecteer **[!UICONTROL Mutual authentication]** als authentificatietype. Als u meerdere zelfondertekende certificaten configureert voor de gebruiker van `fd-cloudservice` , geeft u de naam van de sleutelalias voor het certificaat op.

## Volgende stappen {#next-steps}

U hebt de gegevensbronnen geconfigureerd. Vervolgens kunt u een formuliergegevensmodel maken of als u al een formuliergegevensmodel zonder gegevensbron hebt gemaakt, kunt u dit koppelen aan de gegevensbronnen die u hebt geconfigureerd. Zie [ het model van vormgegevens ](/help/forms/using/create-form-data-models.md) voor details creëren.
