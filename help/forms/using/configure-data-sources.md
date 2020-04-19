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
source-git-commit: 2cf9dcf2e9cf71c54e19e2c6ee825c9a8f00a9b7

---


# Gegevensbronnen configureren{#configure-data-sources}

![](do-not-localize/data-integeration.png)

Met de integratie van gegevens in AEM-formulieren kunt u verschillende gegevensbronnen configureren en verbinden. De volgende types worden gesteund uit-van-de-doos. Met weinig aanpassing kunt u echter ook andere gegevensbronnen integreren.

* Relationele databases - MySQL, Microsoft SQL Server, IBM DB2 en Oracle RDBMS
* AEM-gebruikersprofiel
* RESTful-webservices
* SOAP-webservices
* OData-diensten

De integratie van gegevens steunt OAuth2.0, Basisauthentificatie, en API Zeer belangrijke authentificatietypes out-of-the-box, en staat het uitvoeren van douaneauthentificatie voor de toegang tot van de Webdiensten toe. Terwijl RESTful, op ZEEP-Gebaseerde, en de diensten OData in de Diensten van de Wolk van AEM worden gevormd, JDBC voor relationele gegevensbestanden en schakelaar voor AEM gebruikersprofiel wordt gevormd in AEM Webconsole.

## Relationele database configureren {#configure-relational-database}

U kunt relationele databases configureren met AEM Web Console Configuration. Ga als volgt te werk:

1. Ga naar AEM-webconsole op https://server:host/system/console/configMgr.
1. Zoek naar **[!UICONTROL Apache het Verdelen Verbinding Gepoolde configuratie DataSource]** . Tik om de configuratie te openen in de bewerkingsmodus.
1. In de configuratiedialoog, specificeer de details voor het gegevensbestand u, zoals wilt vormen:

   * Naam van de gegevensbron
   * Het bezit van de gegevensbrondienst dat de naam van de gegevensbron opslaat
   * Java-klassenaam voor het JDBC-stuurprogramma
   * URI voor JDBC-verbinding
   * Gebruikersnaam en wachtwoord om verbinding te maken met het JDBC-stuurprogramma
   >[!NOTE] {graybox=&quot;true&quot;}
   >
   >Zorg ervoor dat u gevoelige informatie zoals wachtwoorden codeert alvorens de gegevensbron te vormen. Coderen:
   >
   >    
   >    
   >    1. Ga naar https://&#39;[server]:[port]&#39;/system/console/crypto.
   >    1. Geef in het veld **[!UICONTROL Onbewerkte tekst]** het wachtwoord of de tekenreeks op die u wilt versleutelen en klik op **[!UICONTROL Beveiligen]**.
   >    
   >    
   >    
   >De gecodeerde tekst wordt weergegeven in het veld Beveiligde tekst dat u in de configuratie kunt opgeven.

1. Schakel **[!UICONTROL Testen op lenen]** of **[!UICONTROL Testen op rendement]** in om op te geven dat de objecten worden gevalideerd voordat ze van en naar de pool worden geleend of geretourneerd.
1. Geef een SQL SELECT-query op in het veld **[!UICONTROL Validatiequery]** om verbindingen vanuit de pool te valideren. De query moet ten minste één rij retourneren. Geef op basis van uw database een van de volgende opties op:

   * SELECT 1 (MySQL en MS SQL)
   * SELECT 1 uit dual (Oracle)

1. Tik op **[!UICONTROL Opslaan]** om de configuratie op te slaan.

## AEM-gebruikersprofiel configureren {#configure-aem-user-profile}

U kunt het AEM-gebruikersprofiel configureren met de configuratie Gebruikersprofielverbinding in AEM-webconsole. Ga als volgt te werk:

1. Ga naar AEM-webconsole op https://&#39;[server]:[poort]&#39;system/console/configMgr.
1. Zoek naar de Integraties van Gegevens van **[!UICONTROL Vormen AEM - de Configuratie]** van de Verbinding van het Profiel van de Gebruiker en tik om de configuratie op Edit wijze te openen.
1. In het dialoogvenster Configuratie gebruikersprofiel-aansluiting kunt u eigenschappen van gebruikersprofielen toevoegen, verwijderen of bijwerken. De opgegeven eigenschappen zijn beschikbaar voor gebruik in het formuliergegevensmodel. Gebruik de volgende indeling om gebruikersprofieleigenschappen op te geven:

   `name=[property_name_with_location_in_user_profile],type=[property_type]`

   Voorbeelden:

   * `name=profile/phoneNumber,type=string`
   * `name=profile/empLocation/*/city,type=string`
   >[!NOTE] {graybox=&quot;true&quot;}
   >
   >In het bovenstaande voorbeeld ***** worden alle knooppunten onder het `profile/empLocation/` knooppunt in het AEM-gebruikersprofiel in de CRXDE-structuur aangegeven. Dit betekent dat het formuliergegevensmodel toegang heeft tot de `city` eigenschap van het type `string` in elk knooppunt onder het `profile/empLocation/` knooppunt. Nochtans, moeten de knopen die het gespecificeerde bezit bevatten een verenigbare structuur volgen.

1. Tik op **[!UICONTROL Opslaan]** om de configuratie op te slaan.

## Map configureren voor configuraties van cloudservices {#cloud-folder}

>[!NOTE]
Configuratie voor map met cloudservices is vereist voor het configureren van cloudservices voor RESTful-, SOAP- en OData-services.

Alle configuraties van de cloudservice in AEM worden geconsolideerd in de `/conf` map in de AEM-opslagplaats. Standaard bevat de `conf` map de `global` map waarin u cloudserviceconfiguraties kunt maken. U moet deze echter handmatig inschakelen voor cloudconfiguraties. U kunt ook aanvullende mappen maken `conf` om configuraties voor cloudservices te maken en in te delen.

De map configureren voor configuraties van cloudservices:

1. Ga naar **[!UICONTROL Gereedschappen > Algemeen > Configuratiebrowser]**.
1. Ga als volgt te werk om de algemene map voor cloudconfiguraties in te schakelen of sla deze stap over om een andere map voor cloudserviceconfiguraties te maken en te configureren.

   1. Selecteer de **[!UICONTROL map in de]** configuratiegrowser `global` en tik op **[!UICONTROL Eigenschappen]**.

   1. Schakel in het dialoogvenster **[!UICONTROL Configuration Properties]** de optie **[!UICONTROL Cloud Configurations]** in.

   1. Tik op **[!UICONTROL Opslaan en sluiten]** om de configuratie op te slaan en het dialoogvenster te sluiten.

1. Tik in de **[!UICONTROL configuratievenster]** op **[!UICONTROL Maken]**.
1. Geef in het dialoogvenster **[!UICONTROL Configuratie]** maken een titel op voor de map en schakel **[!UICONTROL Cloud Configurations]** in.
1. Tik op **[!UICONTROL Maken]** om de map te maken die geschikt is voor configuraties van de cloudservice.

## RESTful-webservices configureren {#configure-restful-web-services}

RESTful Webdienst kan worden beschreven gebruikend de specificaties [van de](https://swagger.io/specification/) Swagger in formaat JSON of YAML in een Swagger definitiedossier. Als u de RESTful-webservice in AEM-cloudservices wilt configureren, dient u ervoor te zorgen dat het Swagger-bestand zich op uw bestandssysteem bevindt of de URL waar het bestand wordt gehost.

Doe het volgende de diensten RESTful vormen:

1. Ga naar **[!UICONTROL Gereedschappen > Cloud Services > Gegevensbronnen]**. Tik om de map te selecteren waarin u een cloudconfiguratie wilt maken.

   Zie Map [configureren voor configuraties](../../forms/using/configure-data-sources.md#cloud-folder) van cloudservices voor informatie over het maken en configureren van een map voor configuraties van cloudservices.

1. Tik op **[!UICONTROL Maken]** om de wizard **** Gegevensbronconfiguratie maken te openen. Geef een naam en eventueel een titel voor de configuratie op, selecteer **[!UICONTROL RESTful Service]** in de vervolgkeuzelijst **[!UICONTROL Servicetype]** , blader naar keuze en selecteer een miniatuurafbeelding voor de configuratie en tik op **[!UICONTROL Volgende]**.
1. Specificeer de volgende details voor de RESTful dienst:

   * Selecteer URL of Dossier van de Bron van de Wagger drop-down, en specificeer dienovereenkomstig Swagger URL aan het de definitiedossier van de Swagger of upload het dossier van de Swagger van uw lokaal dossiersysteem.
   * Op basis van de invoer van de bron van de wagen worden de volgende velden vooraf gevuld met waarden:

      * Schema: De overdrachtprotocollen die door REST API worden gebruikt. Het aantal schematypen die in de drop-down lijst worden getoond hangt van de regelingen af die in de bron van de Swagger worden bepaald.
      * Host: De domeinnaam of het IP-adres van de host die de REST API aanbiedt. Het is een verplicht veld.
      * Basispad: Het URL-voorvoegsel voor alle API-paden. Het is een optioneel veld.\
         Bewerk indien nodig de vooraf ingevulde waarden voor deze velden.
   * Selecteer het authentificatietype — niets, OAuth2.0, Basisauthentificatie, API Sleutel, of de Authentificatie van de Douane — om tot de dienst toegang te hebben RESTful, en dienovereenkomstig details voor authentificatie te verstrekken.
   Als u **[!UICONTROL API-sleutel]** als verificatietype selecteert, geeft u de waarde voor de API-sleutel op. De API-sleutel kan als aanvraagheader of als queryparameter worden verzonden. Selecteer een van deze opties in de vervolgkeuzelijst **[!UICONTROL Locatie]** en geef de naam van de koptekst of de queryparameter op in het veld **[!UICONTROL Parameternaam]** .

1. Tik op **[!UICONTROL Maken]** om de cloudconfiguratie voor de RESTful-service te maken.

## SOAP-webservices configureren {#configure-soap-web-services}

De op SOAP-Gebaseerde Webdiensten worden beschreven gebruikend de specificaties [van de Beschrijving van de](https://www.w3.org/TR/wsdl)Diensten van het Web van de Taal (WSDL). Als u op SOAP gebaseerde webservice wilt configureren in AEM-cloudservices, moet u de WSDL-URL voor de webservice hebben en het volgende doen:

1. Ga naar **[!UICONTROL Gereedschappen > Cloud Services > Gegevensbronnen]**. Tik om de map te selecteren waarin u een cloudconfiguratie wilt maken.

   Zie Map [configureren voor configuraties](../../forms/using/configure-data-sources.md#cloud-folder) van cloudservices voor informatie over het maken en configureren van een map voor configuraties van cloudservices.

1. Tik op **[!UICONTROL Maken]** om de wizard **** Gegevensbronconfiguratie maken te openen. Specificeer een naam en naar keuze een titel voor de configuratie, de uitgezochte Dienst **[!UICONTROL van het Web van de]** ZEEP van het Type **[!UICONTROL van]** Dienst drop-down, doorbladert en selecteert naar keuze een duimnagelbeeld voor de configuratie, en tikt **[!UICONTROL daarna]**.
1. Geef het volgende op voor de SOAP-webservice:

   * WSDL-URL voor de webservice.
   * Service Endpoint. Specificeer een waarde op dit gebied om het de diensteindpunt met voeten te treden dat in WSDL wordt vermeld.
   * Selecteer het authentificatietype — niets, OAuth2.0, Basisauthentificatie, of de Authentificatie van de Douane — om tot de dienst van de ZEEP toegang te hebben, en dienovereenkomstig de details voor authentificatie te verstrekken.

1. Tik op **[!UICONTROL Maken]** om de cloudconfiguratie voor de SOAP-webservice te maken.

## OData-services configureren {#config-odata}

De dienst OData wordt geïdentificeerd door zijn de dienstwortel URL. Als u een OData-service in AEM-cloudservices wilt configureren, moet u ervoor zorgen dat u over de URL van de servicehoofdmap voor de service beschikt en moet u het volgende doen:

>[!NOTE]
Voor geleidelijke gids om de Dynamica 365 van Microsoft, online of op-gebouw te vormen, zie de Configuratie [van OData van de Dynamica van](/help/forms/using/ms-dynamics-odata-configuration.md)Microsoft.

1. Ga naar **[!UICONTROL Gereedschappen > Cloud Services > Gegevensbronnen]**. Tik om de map te selecteren waarin u een cloudconfiguratie wilt maken.

   Zie Map [configureren voor configuraties](../../forms/using/configure-data-sources.md#cloud-folder) van cloudservices voor informatie over het maken en configureren van een map voor configuraties van cloudservices.

1. Tik op **[!UICONTROL Maken]** om de wizard **** Gegevensbronconfiguratie maken te openen. Geef een naam en eventueel een titel voor de configuratie op, selecteer **[!UICONTROL OData Service]** in de vervolgkeuzelijst **[!UICONTROL Servicetype]** , blader optioneel naar een miniatuurafbeelding voor de configuratie en tik op **[!UICONTROL Volgende]**.
1. Specificeer de volgende details voor de dienst OData:

   * Service Root URL voor de OData-service die moet worden geconfigureerd.
   * Selecteer het authentificatietype — niets, OAuth2.0, Basisauthentificatie, of de Authentificatie van de Douane — om tot de dienst toegang te hebben OData, en dienovereenkomstig de details voor authentificatie te verstrekken.
   >[!NOTE]
   U moet OAuth 2.0 authentificatietype selecteren om met de diensten van de Dynamiek van Microsoft te verbinden gebruikend eindpunt OData als de dienstwortel.

1. Tik op **Maken** om de cloudconfiguratie voor de OData-service te maken.

## Volgende stappen {#next-steps}

U hebt de gegevensbronnen geconfigureerd. Vervolgens kunt u een formuliergegevensmodel maken of als u al een formuliergegevensmodel zonder gegevensbron hebt gemaakt, kunt u dit koppelen aan de zojuist geconfigureerde gegevensbronnen. Zie [Formuliergegevensmodel](/help/forms/using/create-form-data-models.md) maken voor meer informatie.
