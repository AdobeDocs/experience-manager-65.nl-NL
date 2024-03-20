---
title: Gegevensbronnen configureren
description: Leer hoe u verschillende typen gegevensbronnen configureert, zodat u formuliergegevensmodellen kunt maken.
topic-tags: integration
products: SG_EXPERIENCEMANAGER/6.5/FORMS
docset: aem65
feature: Form Data Model
exl-id: 7a1d9d57-66f4-4f20-91c2-ace5a71a52f2
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1896'
ht-degree: 0%

---

# Gegevensbronnen configureren{#configure-data-sources}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/integrate/use-form-data-model/configure-data-sources.html) |
| AEM 6,5 | Dit artikel |


![Gegevensintegratie](do-not-localize/data-integeration.png)

Met AEM Forms Data Integration kunt u verschillende gegevensbronnen configureren en verbinden. De volgende types worden gesteund uit-van-de-doos. Met weinig aanpassing kunt u echter ook andere gegevensbronnen integreren.

* Relationele databases - MySQL, Microsoft SQL Server, IBM DB2, Oracle RDBMS, postgreSQL en Sybase
* Gebruikersprofiel AEM
* RESTful-webservices
* SOAP-webservices
* OData-diensten

Gegevensintegratie ondersteunt OAuth2.0([Autorisatiecode](https://oauth.net/2/grant-types/authorization-code/), [Client Credentials](https://oauth.net/2/grant-types/client-credentials/)), Basic Authentication, en API Key authentication types out-of-the-box, en staat het uitvoeren van douaneauthentificatie voor de toegang tot van de Webdiensten toe. Terwijl RESTful, op SOAP-Gebaseerde, en de diensten OData in AEM Cloud Servicen worden gevormd, wordt JDBC voor relationele gegevensbestanden en schakelaar voor AEM gebruikersprofiel gevormd in AEM Webconsole.

## Relationele database configureren {#configure-relational-database}

U kunt relationele gegevensbestanden vormen gebruikend AEM de Configuratie van de Console van het Web. Ga als volgt te werk:

1. Ga naar AEM webconsole op `https://server:host/system/console/configMgr`.
1. Zoeken naar **[!UICONTROL Apache Sling Connection Pooled DataSource]** configuratie. Selecteer deze optie om de configuratie te openen in de bewerkingsmodus.
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
   > 1. Ga naar https://&#39;[server]:[poort]&quot;/systeem/console/crypto.
   > 1. In de **[!UICONTROL Plain Text]** veld, geef het wachtwoord of een tekenreeks op die u wilt versleutelen en selecteer **[!UICONTROL Protect]**.
   >
   >De gecodeerde tekst wordt weergegeven in het veld Beveiligde tekst dat u in de configuratie kunt opgeven.

1. Inschakelen **[!UICONTROL Test on Borrow]** of **[!UICONTROL Test on Return]** om te specificeren dat de voorwerpen alvorens worden geleend of van en aan de pool teruggegeven, worden gevalideerd.
1. Geef een SQL SELECT-query op in het dialoogvenster **[!UICONTROL Validation Query]** veld voor het valideren van verbindingen vanuit de pool. De query moet ten minste één rij retourneren. Geef op basis van uw database een van de volgende opties op:

   * SELECT 1 (MySQL en MS SQL)
   * SELECTEER 1 uit twee items (Oracle)

1. Selecteren **[!UICONTROL Save]** om de configuratie op te slaan.

   >[!NOTE]
   >
   > Als uw Forms-gegevensmodel een object bevat dat een gereserveerd trefwoord is voor uw relationele database, kan dit leiden tot problemen met het toevoegen, bijwerken of ophalen van gegevens. Vermijd dus het gebruik van dergelijke objecten in uw formuliergegevensmodel.

## Gebruikersprofiel AEM configureren {#configure-aem-user-profile}

U kunt AEM gebruikersprofiel vormen gebruikend de Configuratie van de Verbinding van het Profiel van de Gebruiker in AEM Console van het Web. Ga als volgt te werk:

1. Ga naar AEM webconsole op https://&#39;[server]:[poort]&#39;system/console/configMgr.
1. Zoeken naar **[!UICONTROL AEM Forms Data Integrations - User Profile Connector Configuration]** en selecteer deze optie om de configuratie te openen in de bewerkingsmodus.
1. In het dialoogvenster Configuratie gebruikersprofiel-aansluiting kunt u eigenschappen van gebruikersprofielen toevoegen, verwijderen of bijwerken. De opgegeven eigenschappen zijn beschikbaar voor gebruik in het formuliergegevensmodel. Gebruik de volgende indeling om gebruikersprofieleigenschappen op te geven:

   `name=[property_name_with_location_in_user_profile],type=[property_type]`

   Voorbeelden:

   * `name=profile/phoneNumber,type=string`
   * `name=profile/empLocation/*/city,type=string`

   >[!NOTE]
   >
   >De **&#42;** in het bovenstaande voorbeeld worden alle knooppunten onder de `profile/empLocation/` knooppunt in AEM gebruikersprofiel in CRXDE-structuur. Dit betekent dat het formuliergegevensmodel toegang heeft tot het dialoogvenster `city` eigenschap of type `string` aanwezig in een knooppunt onder `profile/empLocation/` knooppunt. Nochtans, moeten de knopen die het gespecificeerde bezit bevatten een verenigbare structuur volgen.

1. Selecteren **[!UICONTROL Save]** om de configuratie op te slaan.

## Map configureren voor configuraties van cloudservices {#cloud-folder}

>[!NOTE]
>
Configuratie voor map met cloudservices is vereist voor het configureren van cloudservices voor RESTful-, SOAP- en OData-services.

Alle configuraties van de cloudservice in AEM worden geconsolideerd in de `/conf` in AEM opslagplaats. Standaard worden de `conf` map bevat de `global` map waar u configuraties voor cloudservices kunt maken. U moet deze optie echter handmatig inschakelen voor cloudconfiguraties. U kunt ook extra mappen maken in `conf` om cloudserviceconfiguraties te maken en te organiseren.

De map configureren voor configuraties van cloudservices:

1. Ga naar **[!UICONTROL Tools > General > Configuration Browser]**.
   * Zie de [Configuratiebrowser](/help/sites-administering/configurations.md) documentatie voor meer informatie.
1. Ga als volgt te werk om de algemene map voor cloudconfiguraties in te schakelen of sla deze stap over om een andere map voor cloudserviceconfiguraties te maken en te configureren.

   1. In de **[!UICONTROL Configuration Browser]**, selecteert u de `global` map en selecteer **[!UICONTROL Properties]**.

   1. In de **[!UICONTROL Configuration Properties]** dialoogvenster, inschakelen **[!UICONTROL Cloud Configurations]**.

   1. Selecteren **[!UICONTROL Save & Close]** om de configuratie op te slaan en het dialoogvenster af te sluiten.

1. In de **[!UICONTROL Configuration Browser]**, selecteert u **[!UICONTROL Create]**.
1. In de **[!UICONTROL Create Configuration]** een titel voor de map opgeven en inschakelen **[!UICONTROL Cloud Configurations]**.
1. Selecteren **[!UICONTROL Create]** om de map te maken die is ingeschakeld voor configuraties van de cloudservice.

## RESTful-webservices configureren {#configure-restful-web-services}

RESTful-webservice kan worden beschreven met [Specificaties van de wagon](https://swagger.io/specification/) in JSON- of YAML-indeling in een Swagger-definitiebestand. Als u de RESTful-webservice in AEM cloudservices wilt configureren, dient u ervoor te zorgen dat het Swagger-bestand zich op uw bestandssysteem bevindt of de URL waar het bestand wordt gehost.

Doe het volgende de diensten RESTful vormen:

1. Ga naar **[!UICONTROL Tools > Cloud Services > Data Sources]**. Selecteer deze optie om de map te selecteren waarin u een cloudconfiguratie wilt maken.

   Zie [Map configureren voor configuraties van cloudservices](../../forms/using/configure-data-sources.md#cloud-folder) voor informatie over het maken en configureren van een map voor cloudserviceconfiguraties.

1. Selecteren **[!UICONTROL Create]** om de **[!UICONTROL Create Data Source Configuration wizard]**. Geef een naam en eventueel een titel voor de configuratie op. Selecteer **[!UICONTROL RESTful Service]** van de **[!UICONTROL Service Type]** vervolgkeuzelijst, bladert u optioneel naar een miniatuurafbeelding voor de configuratie en selecteert u **[!UICONTROL Next]**.
1. Specificeer de volgende details voor de RESTful dienst:

   * Selecteer URL of Dossier van de Bron van de Wagger drop-down, en specificeer dienovereenkomstig Swagger URL aan het de definitiedossier van de Swagger of upload het dossier van de Swagger van uw lokaal dossiersysteem.
   * Op basis van de invoer van de bron van de wagen worden de volgende velden vooraf gevuld met waarden:

      * Schema: de overdrachtprotocollen die door de REST API worden gebruikt. Het aantal schematypen die in de drop-down lijst worden getoond hangt van de regelingen af die in de bron van de Swagger worden bepaald.
      * Host: de domeinnaam of het IP-adres van de host die de REST API aanbiedt. Het is een verplicht veld.
      * Basispad: het URL-voorvoegsel voor alle API-paden. Het is een optioneel veld.\
        Bewerk indien nodig de vooraf ingevulde waarden voor deze velden.

   * Selecteer het verificatietype: None, OAuth2.0([Autorisatiecode](https://oauth.net/2/grant-types/authorization-code/), [Client Credentials](https://oauth.net/2/grant-types/client-credentials/)), Basic Authentication, API Key, Custom Authentication, of Mutual Authentication, om toegang te krijgen tot de RESTful-service en dienovereenkomstig gegevens te verstrekken voor verificatie.

   Als u **[!UICONTROL API Key]** Geef als verificatietype de waarde voor de API-sleutel op. De API-sleutel kan als aanvraagheader of als queryparameter worden verzonden. Selecteer een van deze opties in het menu **[!UICONTROL Location]** vervolgkeuzelijst en geef de naam van de header of de parameter query op in de **[!UICONTROL Parameter Name]** veld dienovereenkomstig.

   Als u **[!UICONTROL Mutual Authentication]** als authentificatietype, zie [Op certificaten gebaseerde wederzijdse verificatie voor RESTful- en SOAP-webservices](#mutual-authentication).

1. Selecteren **[!UICONTROL Create]** om de wolkenconfiguratie voor de RESTful dienst te creëren.

### Het model van de gegevens van de vormHTTP cliëntconfiguratie om prestaties te optimaliseren {#fdm-http-client-configuration}

[!DNL Experience Manager Forms] formuliergegevensmodel bij integratie met RESTful-webservices als gegevensbron bevat HTTP-clientconfiguraties voor optimalisatie van prestaties.
Voer de volgende stappen uit om de HTTP-client van het formuliergegevensmodel te configureren:

1. Aanmelden bij [!DNL Experience Manager Forms] Instantie van auteur als beheerder en ga naar [!DNL Experience Manager] bundels voor webconsoles. De standaard-URL is [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr).

1. Selecteren **[!UICONTROL Form Data Model Http Client Configuration for REST data source]**.

1. In de [!UICONTROL Form Data Model Http Client Configuration for REST data source] dialoogvenster:

   * Geef het maximale aantal toegestane verbindingen op tussen het gegevensmodel van het formulier en de RESTful-webservices in het dialoogvenster **[!UICONTROL Connection limit in total]** veld. De standaardwaarde is 20 verbindingen.

   * Specificeer het maximumaantal toegestane verbindingen voor elke route in **[!UICONTROL Connection limit on per route basis]** veld. De standaardwaarde is 2 verbindingen.

   * Geef de duur op, gedurende welke een blijvende HTTP-verbinding in leven blijft in het dialoogvenster **[!UICONTROL Keep alive]** veld. De standaardwaarde is 15 seconden.

   * Geef de duur op waarvoor de [!DNL Experience Manager Forms] server wacht tot een verbinding tot stand is gebracht, in de **[!UICONTROL Connection timeout]** veld. De standaardwaarde is 10 seconden.

   * Geef de maximale periode voor inactiviteit op tussen twee gegevenspakketten in het dialoogvenster **[!UICONTROL Socket timeout]** veld. De standaardwaarde is 30 seconden.

## SOAP-webservices configureren {#configure-soap-web-services}

SOAP-webservices worden beschreven met [Web Services Description Language (WSDL)-specificaties](https://www.w3.org/TR/wsdl). Als u op SOAP gebaseerde webservice wilt configureren in AEM cloudservices, moet u ervoor zorgen dat u over de WSDL-URL voor de webservice beschikt en het volgende doen:

1. Ga naar **[!UICONTROL Tools > Cloud Services > Data Sources]**. Selecteer deze optie om de map te selecteren waarin u een cloudconfiguratie wilt maken.

   Zie [Map configureren voor configuraties van cloudservices](../../forms/using/configure-data-sources.md#cloud-folder) voor informatie over het maken en configureren van een map voor cloudserviceconfiguraties.

1. Selecteren **[!UICONTROL Create]** om de **[!UICONTROL Create Data Source Configuration wizard]**. Geef een naam en eventueel een titel voor de configuratie op. Selecteer **[!UICONTROL SOAP Web Service]** van de **[!UICONTROL Service Type]** vervolgkeuzelijst, bladert u optioneel naar een miniatuurafbeelding voor de configuratie en selecteert u **[!UICONTROL Next]**.
1. Geef het volgende op voor de SOAP-webservice:

   * WSDL-URL voor de webservice.
   * Service Endpoint. Specificeer een waarde op dit gebied om het de diensteindpunt met voeten te treden dat in WSDL wordt vermeld.
   * Selecteer het verificatietype: None, OAuth2.0([Autorisatiecode](https://oauth.net/2/grant-types/authorization-code/), [Client Credentials](https://oauth.net/2/grant-types/client-credentials/)), Basisverificatie, Aangepaste verificatie, Token X509 of Wederzijdse verificatie — voor toegang tot de SOAP-service en dienovereenkomstig de gegevens voor verificatie opgeven.

     Als u **[!UICONTROL X509 Token]** Als het type van Authentificatie, vorm het X509- certificaat. Zie voor meer informatie [Certificaten instellen](install-configure-document-services.md#set-up-certificates-for-reader-extension-and-encryption-service).
Geef de alias KeyStore voor het X509-certificaat op in het dialoogvenster **[!UICONTROL Key Alias]** veld. Geef de tijd in seconden op totdat de verificatieaanvraag geldig blijft in het dialoogvenster **[!UICONTROL Time To Live]** veld. Selecteer desgewenst om de berichttekst, de tijdstempelkop of beide te ondertekenen.

     Als u **[!UICONTROL Mutual Authentication]** als authentificatietype, zie [Op certificaten gebaseerde wederzijdse verificatie voor RESTful- en SOAP-webservices](#mutual-authentication).

1. Selecteren **[!UICONTROL Create]** om de cloudconfiguratie voor de SOAP-webservice te maken.

## OData-services configureren {#config-odata}

De dienst OData wordt geïdentificeerd door zijn de dienstwortel URL. Als u een OData-service in AEM cloudservices wilt configureren, moet u ervoor zorgen dat u over de URL van de servicehoofdmap voor de service beschikt en moet u het volgende doen:

>[!NOTE]
>
Formuliergegevensmodel ondersteunt [OData versie 4](https://www.odata.org/documentation/).
Voor geleidelijke gids om Dynamica 365 van Microsoft, online of op-gebouw te vormen, zie [Configuratie Microsoft Dynamics OData](/help/forms/using/ms-dynamics-odata-configuration.md).

1. Ga naar **[!UICONTROL Tools > Cloud Services > Data Sources]**. Selecteer deze optie om de map te selecteren waarin u een cloudconfiguratie wilt maken.

   Zie [Map configureren voor configuraties van cloudservices](../../forms/using/configure-data-sources.md#cloud-folder) voor informatie over het maken en configureren van een map voor cloudserviceconfiguraties.

1. Selecteren **[!UICONTROL Create]** om de **[!UICONTROL Create Data Source Configuration wizard]**. Geef een naam en eventueel een titel voor de configuratie op. Selecteer **[!UICONTROL OData Service]** van de **[!UICONTROL Service Type]** vervolgkeuzelijst, bladert u optioneel naar een miniatuurafbeelding voor de configuratie en selecteert u **[!UICONTROL Next]**.
1. Specificeer de volgende details voor de dienst OData:

   * Service Root URL voor de OData-service die moet worden geconfigureerd.
   * Selecteer het verificatietype: None, OAuth2.0([Autorisatiecode](https://oauth.net/2/grant-types/authorization-code/), [Client Credentials](https://oauth.net/2/grant-types/client-credentials/)), Basisverificatie of Aangepaste verificatie — toegang tot de OData-service en dienovereenkomstig de gegevens voor verificatie te verstrekken.

   >[!NOTE]
   >
   Selecteer OAuth 2.0 authentificatietype om met de diensten van de Dynamiek van Microsoft te verbinden gebruikend eindpunt OData als de de dienstwortel.

1. Selecteren **Maken** om de wolkenconfiguratie voor de dienst te creëren OData.

## Op certificaten gebaseerde wederzijdse verificatie voor RESTful- en SOAP-webservices {#mutual-authentication}

Wanneer u wederzijdse verificatie inschakelt voor het gegevensmodel van het formulier, wordt elkaars identiteit geverifieerd door zowel het gegevensbrongegevensmodel als het gegevensgegevensmodel van AEM server waarop formuliergegevens worden uitgevoerd, voordat gegevens worden gedeeld. U kunt wederzijdse authentificatie voor REST en SOAP gebaseerde verbindingen (gegevensbronnen) gebruiken. Om wederzijdse authentificatie voor een model van vormgegevens op uw milieu van AEM Forms te vormen:

1. De persoonlijke sleutel (certificaat) uploaden naar [!DNL AEM Forms] server. De persoonlijke sleutel uploaden:
   1. Aanmelden bij uw [!DNL AEM Forms] als beheerder.
   1. Ga naar **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Users]**. Selecteer de `fd-cloudservice` gebruiker en selecteer **[!UICONTROL Properties]**.
   1. Open de **[!UICONTROL Keystore]** tabblad, vouwt u de **[!UICONTROL Add Private Key from KeyStore file]** , uploadt u het KeyStore-bestand, geeft u de aliassen, wachtwoorden en selecteert u **[!UICONTROL Submit]**. Het certificaat wordt geüpload.  De alias van de persoonlijke sleutel wordt vermeld in het certificaat en ingesteld tijdens het maken van het certificaat.
1. Upload vertrouwenscertificaat naar Global Trust Store. Het certificaat uploaden:
   1. Navigeren naar **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Trust Store]**.
   1. Breid uit **[!UICONTROL Add Certificate from CER file]** selecteert u **[!UICONTROL Select Certificate File]**, uploadt u het certificaat en selecteert u **[!UICONTROL Submit]**.
1. Configureren [SOAP](#configure-soap-web-services) of [RESTful](#configure-restful-web-services) webservices als gegevensbron en selecteer **[!UICONTROL Mutual authentication]** als het verificatietype. Als u meerdere zelfondertekende certificaten configureert voor `fd-cloudservice` -gebruiker, geeft u de naam van de sleutelalias voor het certificaat op.

## Volgende stappen {#next-steps}

U hebt de gegevensbronnen geconfigureerd. Vervolgens kunt u een formuliergegevensmodel maken of als u al een formuliergegevensmodel zonder gegevensbron hebt gemaakt, kunt u dit koppelen aan de gegevensbronnen die u hebt geconfigureerd. Zie [Formuliergegevensmodel maken](/help/forms/using/create-form-data-models.md) voor meer informatie.
