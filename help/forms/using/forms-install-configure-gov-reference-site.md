---
title: De referentiesite We.Gov en We.Finance instellen en configureren
seo-title: Set up and configure We.Gov reference site
description: Een AEM Forms-demopakket installeren, configureren en aanpassen.
seo-description: Install, configure, and customize an AEM Forms demo package.
uuid: 0a6ad8f9-0d38-40c3-ad8d-e705edef55f8
contentOwner: anujkapo
discoiquuid: fe5da0aa-d3a8-4b77-a447-9e429fdc2816
docset: aem65
exl-id: 1fee474e-7da5-4ab2-881a-34b8e055aa29
source-git-commit: ce6d24e53a27b64a5d0a9db2e4b6672bd77cf9ec
workflow-type: tm+mt
source-wordcount: '4662'
ht-degree: 1%

---

# De referentiesite We.Gov en We.Finance instellen en configureren {#set-up-and-configure-we-gov-reference-site}

## Details demopakket {#demo-package-details}

### Installatievereisten {#installation-prerequisites}

Dit pakket is gemaakt voor **AEM Forms 6.4 OSGI-auteur**, is getest en wordt daarom ondersteund op de volgende platformversies:

| AEM | AEM Forms PACKAGE VERSION | STATUS |
|---|---|---|
| 6.4 | 5.0.86 | **Ondersteund** |
| 6.5 | 6.0.80 | **Ondersteund** |
| 6.5.3 | 6.0.122 | **Ondersteund** |

Dit pakket bevat cloudconfiguratie die de volgende platformversies ondersteunt:

| PROVIDER CLOUD | SERVICEVERSIE | STATUS |
|---|---|---|
| Adobe Sign | v5 API | **Ondersteund** |
| Microsoft Dynamics 365 | 1710 (9.1.0.3020) | **Ondersteund** |
| Adobe Analytics | v1.4 Rest-API | **Ondersteund** |
**Overwegingen bij de installatie van pakketten:**

* Het pakket wordt naar verwachting geïnstalleerd op een schone server, zonder andere demopakketten of oudere demopakketversies
* Het pakket wordt naar verwachting geïnstalleerd op een OSGI-server, die wordt uitgevoerd in de modus Auteur

### Wat bevat dit pakket {#what-does-this-package-include}

De [AEM Forms We.Gov-demopakket](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/featurepack/we-gov-forms.pkg.all-2.0.2.zip) (**we-gov-formulieren.pkg.all-&lt;version>.zip**) wordt geleverd als een pakket dat diverse andere subpakketten en diensten omvat. Het pakket bevat de volgende modules:

* **we-gov-formulieren.pkg.all-&lt;version>.zip** - *Volledig demopakket*

   * **we-gov-forms.ui.apps-&lt;version>.zip** *- Bevat alle componenten, clientbibliotheken, voorbeeldgebruikers, workflowmodellen, enz.*

      * **we-gov-forms.core-&lt;version>.jar** - *Bevat alle diensten OSGI, de implementatie van de douanewerkschemasstap, enz.*

      * **we-gov-forms.derby&lt;version>.jar** - *Bevat alle diensten OSGI, gegevensbestandschema, enz.*

      * **core.wcm.components.all-2.0.4.zip** - *Verzameling van WCM-monsters*

      * **grid-aem.ui.apps-1.0-SNAPSHOT.zip** - *AEM Sites Grid-lay-outpakket voor het kolombesturingselement voor sites*
   * **we-gov-forms.ui.content-&lt;version>.zip** - *Bevat alle inhoud, pagina&#39;s, afbeeldingen, formulieren, interactieve communicatiemiddelen, enzovoort.*

   * **we-gov-forms.ui.analytics-&lt;version>.zip** - *Bevat alle gegevens van We.Gov Forms Analytics die in de opslagplaats moeten worden opgeslagen.*

   * **we-gov-forms.config.public-&lt;version>.zip** - *Bevat alle standaardconfiguratieknooppunten, inclusief de configuraties van de plaatsaanduidingswolk, om problemen met het gegevensmodel van formulieren en servicebinding te helpen voorkomen.*


De elementen die in dit pakket zijn opgenomen, zijn:

* Sitepagina&#39;s AEM met bewerkbare sjablonen
* AEM Forms Adaptive Forms
* Interactieve AEM Forms-communicatie (Afdrukken en Webkanaal)
* AEM Forms XDP-document van record
* AEM Forms MS Dynamics Forms-gegevensmodel
* Adobe Sign-integratie
* AEM workflowmodel
* AEM Assets-voorbeeldafbeeldingen
* Voorbeeld (in geheugen) Apache Derby Database
* Apache Derby Data Source (voor gebruik met formuliergegevensmodel)

## Installatie van demopakket {#demo-package-installation}

Deze sectie bevat informatie over het installeren van het demopakket.

### Van softwaredistributie {#from-software-distribution}

1. Openen [Softwaredistributie](https://experience.adobe.com/downloads). U hebt een Adobe ID nodig om u aan te melden bij de softwaredistributie.
1. Tikken **[!UICONTROL Adobe Experience Manager]** beschikbaar in het koptekstmenu.
1. In de **[!UICONTROL Filters]** sectie:
   1. Selecteren **[!UICONTROL Forms]** van de **[!UICONTROL Solution]** vervolgkeuzelijst.
   2. Selecteer de versie en typ voor het pakket. U kunt ook de opdracht **[!UICONTROL Search Downloads]** om de resultaten te filteren.
1. Tik op de knop **we-gov-formulieren.pkg.all-&lt;version>.zip** pakketnaam, selecteren **[!UICONTROL Accept EULA Terms]** en tikken **[!UICONTROL Download]**.
1. Openen [Pakketbeheer](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html)  en klik op **[!UICONTROL Upload Package]** om het pakket te uploaden.
1. Selecteer het pakket en klik op **[!UICONTROL Install]**.

   ![we gov - formulierpakket](assets/wegov_forms_package.jpg)

1. De installatie kan worden voltooid.
1. Navigeren naar *https://&lt;aemserver>:&lt;port>/content/we-gov/home.html?wcmmode=disabled* om ervoor te zorgen dat de installatie is gelukt.

### Vanuit een lokaal ZIP-bestand {#from-a-local-zip-file}

1. Download en zoek de **we-gov-formulieren.pkg.all-&lt;version>.zip** bestand.
1. Navigeren naar *https://&lt;aemserver>:&lt;port>/crx/packmgr/index.jsp*.
1. Selecteer de optie Pakket uploaden.

   ![Pakketoptie uploaden](assets/upload_package.jpg)

1. Gebruik de bestandsbrowser om naar het gedownloade ZIP-bestand te navigeren en dit te selecteren.
1. Klik op Openen om te uploaden.
1. Nadat u het pakket hebt geüpload, selecteert u de optie &quot;Installeren&quot; om het pakket te installeren.

   ![WeGov Forms-pakket installeren](assets/wegov_forms_package-1.jpg)

1. De installatie kan worden voltooid.
1. Navigeren naar *https://&lt;aemserver>:&lt;port>/content/we-gov/home.html?wcmmode=disabled* om ervoor te zorgen dat de installatie is gelukt.

### Nieuwe pakketversies installeren {#installing-new-package-versions}

Voer de stappen in 4.1 en 4.2 uit om een nieuwe pakketversie te installeren. U kunt een nieuwere pakketversie installeren terwijl al een ander ouder pakket is geïnstalleerd, maar u wordt aangeraden de oudere pakketversie eerst te verwijderen. Volg de onderstaande stappen om dit te doen.

1. Navigeren naar *https://&lt;aemserver>:&lt;port>/crx/packmgr/index.jsp*
1. De map zoeken **we-gov-formulieren.pkg.all-&lt;version>.zip** bestand.
1. Selecteer de optie Meer.
1. Selecteer in het vervolgkeuzemenu de optie Verwijderen.

   ![WeGov-pakket verwijderen](assets/uninstall_wegov_forms_package.jpg)

1. Selecteer na bevestiging nogmaals &quot;Verwijderen&quot; en voer de procedure voor het verwijderen uit.

## Configuratie demopakket {#demo-package-configuration}

Deze sectie bevat details en instructies over de configuratie na implementatie van het demopakket vóór de presentatie.

### Facultatieve gebruikersconfiguratie {#fictional-user-configuration}

1. Navigeren naar *https://&lt;aemserver>:&lt;port>/libs/granite/security/content/groupadmin.html*
1. Meld u aan als beheerder om de onderstaande taken uit te voeren.
1. Schuif omlaag naar het einde van de pagina om alle gebruikersgroepen te laden.
1. Zoeken naar &quot;**werkstroom**&quot;.
1. Selecteer &quot;**workflowgebruikers**&quot; en klik op &quot;Eigenschappen&quot;.
1. Navigeer naar het tabblad &quot;Leden&quot;.
1. Type in **wegov** in het veld Gebruiker of groep selecteren.
1. Selecteren in het vervolgkeuzemenu &quot;**We.Gov Forms-gebruikers**&quot;.

   ![Groepsinstellingen bewerken voor workflowgebruikers](assets/edit_group_settings.jpg)

1. Klik op &quot;Opslaan en sluiten&quot; in de menubalk.
1. Herhaal stap 2-7 door te zoeken naar &quot;**analyse**&quot;, selecteert u de &quot;**Analysebeheerders**&quot;, en voegt &quot;**We.Gov Forms-gebruikers**&quot;groeperen als lid.
1. Herhaal stap 2-7 door te zoeken naar &quot;**formuliergebruikers**&quot;, selecteert u de &quot;**formulieren-grootgebruikers**&quot;, en voegt &quot;**We.Gov Forms-gebruikers**&quot;groeperen als lid.
1. Herhaal stap 2-7 door te zoeken naar &quot;**formulieren-gebruikers**&quot;, selecteert u de &quot;**formulieren-gebruikers**&quot; en voegt nu &quot;**Wij.Gov-gebruikers**&quot;groeperen als lid.

### Configuratie van e-mailserver {#email-server-configuration}

1. Documentatie voor het instellen van revisies [E-mailmelding configureren](/help/sites-administering/notification.md)
1. Meld u aan als beheerder om deze taak uit te voeren.
1. Navigeren naar *https://&lt;aemserver>:&lt;port>/system/console/configMgr*
1. Zoek en klik op de knop **CQ-mailservice op dag** service voor configureren.

   ![CQ-mailservice op dag configureren](assets/day_cq_mail_service.jpg)

1. Vorm de dienst om met de server SMTP van uw keus te verbinden:

   1. **hostnaam SMTP-server**: bijv. (smtp.gmail.com)
   1. **Serverpoort**: bijv. (465) voor gmail met SSL
   1. **SMTP-gebruiker:** demo@ &lt;companyname> .com
   1. **Adres &quot;Van&quot;**: aemformsdemo@adobe.com

   ![SMTP configureren](assets/configure_smtp.jpg)

1. Klik &quot;sparen&quot;om de configuratie te bewaren.

### (Optioneel) AEM SSL-configuratie {#aemsslconfig}

Deze sectie bevat informatie over het configureren van SSL op de AEM-instantie om de Adobe Sign Cloud-configuratie te kunnen configureren.

**Referenties:**

1. [Standaard SSL](/help/sites-administering/ssl-by-default.md)

**Opmerkingen:**

1. Ga naar https://&lt;aemserver>:&lt;port>/aem/inbox waarin u het proces kunt voltooien dat in de bovenstaande koppeling naar de referentiedocumentatie wordt uitgelegd.
1. De `we-gov-forms.pkg.all-[version].zip` pakket bevat een voorbeeld-SSL-sleutel en -certificaat dat u kunt openen door het pakket uit te pakken `we-gov-forms.pkg.all-[version].zip/ssl` map die deel uitmaakt van het pakket.

1. SSL-certificaat en sleutelgegevens:

   1. uitgegeven aan &quot;CN=localhost&quot;
   1. 10 jaar geldigheid
   1. password value of &quot;password&quot;
1. De persoonlijke sleutel is *localhostprivate.der*.
1. Het certificaat is *localhost.crt*.
1. Klik op Next.
1. HTTPS Hostname zou moeten worden geplaatst aan *localhost*.
1. De haven zou aan een haven moeten worden geplaatst die het systeem heeft blootgesteld.

### (Optioneel) Adobe Sign-cloudconfiguratie {#adobe-sign-cloud-configuration}

Deze sectie bevat informatie en instructies over de Adobe Sign Cloud Configuration.

**Referenties:**

1. [Adobe Sign integreren met AEM Forms](adobe-sign-integration-adaptive-forms.md)

#### Cloudconfiguratie {#cloud-configuration}

1. Controleer de voorwaarden. Zie [SSL-configuratie AEM](../../forms/using/forms-install-configure-gov-reference-site.md#aemsslconfig) voor vereiste SSL-configuratie.
1. Ga naar:

   *https://&lt;aemserver>:&lt;port>/libs/adobesign/cloudservices/adobesign.html/conf/we-gov*

   >[!NOTE]
   >
   >De URL die wordt gebruikt voor toegang tot de AEM server moet overeenkomen met de URL die is geconfigureerd in de Adobe Sign OAuth Redirect URI om configuratieproblemen te voorkomen (bijvoorbeeld *https://&lt;aemserver>:&lt;port>/mnt/overlay/adobesign/cloudservices/adobesign/properties.html*)

1. Selecteer de configuratie &quot;We.gov Adobe Sign&quot;.
1. Klik op &quot;Eigenschappen&quot;.
1. Navigeer naar het tabblad &quot;Instellingen&quot;.
1. Voer de URL van Auth in, bijvoorbeeld: [https://secure.na1.echosign.com/public/oauth](https://secure.na1.echosign.com/public/oauth)
1. Verstrek gevormde identiteitskaart van de Cliënt en Geheime cliënt van de gevormde instantie van Adobe Sign.
1. Klik op &quot;Verbinding maken met Adobe Sign&quot;.
1. Klik na een geslaagde verbinding op &quot;Opslaan en sluiten&quot; om de integratie te voltooien.

### (Optioneel) Configuratie van de cloud voor MS Dynamics {#ms-dynamics-cloud-configuration}

Deze sectie bevat details en instructies over de Configuratie van de Wolk van de Dynamica van MS.

**Referenties:**

1. [Configuratie Microsoft Dynamics OData](https://experienceleague.adobe.com/docs/experience-manager-64/forms/form-data-model/ms-dynamics-odata-configuration.html)
1. [Microsoft Dynamics for AEM Forms configureren](https://helpx.adobe.com/experience-manager/kt/forms/using/config-dynamics-for-aem-forms.html)

#### MS Dynamics OData cloudservice {#ms-dynamics-odata-cloud-service}

1. Ga naar:

   https://&lt;aemserver>:&lt;port>/libs/fd/fdm/gui/components/admin/fdmcloudservice/fdm.html/conf/we-gov

   1. Zorg ervoor dat u de server opent met dezelfde omleidings-URL als die is geconfigureerd in de toepassingsregistratie van MS Dynamics.

1. Selecteer de configuratie &quot;Microsoft Dynamics OData Cloud Service&quot;.
1. Klik op &quot;Eigenschappen&quot;.

   ![Eigenschappen voor Microsoft OData Cloud Service](assets/properties_odata_cloud_service.jpg)

1. Navigeer naar het tabblad &#39;Verificatie-instellingen&#39;.
1. Voer de volgende gegevens in:

   1. **Hoofdmap service:** bijv. `https://msdynamicsserver.api.crm3.dynamics.com/api/data/v9.1/`
   1. **Type verificatie:** OAuth 2.0
   1. **Verificatie-instellingen** (zie [Configuratie-instellingen voor MS Dynamics-cloud](../../forms/using/forms-install-configure-gov-reference-site.md#dynamicsconfig) om deze informatie te verzamelen):

      1. Client-id - ook wel toepassings-id genoemd
      1. Clientgeheim
      1. OAuth-URL, bijvoorbeeld [https://login.windows.net/common/oauth2/authorize](https://login.windows.net/common/oauth2/authorize)
      1. Token-URL vernieuwen - bijvoorbeeld [https://login.windows.net/common/oauth2/token](https://login.windows.net/common/oauth2/token)
      1. Toegang krijgen tot token-URL, bijvoorbeeld [https://login.windows.net/common/oauth2/token](https://login.windows.net/common/oauth2/token)
      1. Autorisatiebereik - **openhartig**
      1. Verificatieheader - **Vergunninghouder**
      1. Bron - bijv. `https://msdynamicsserver.api.crm3.dynamics.com`
   1. Klik op &quot;Verbinding maken met OAuth&quot;.


1. Na succesvolle verificatie klikt u op &quot;Opslaan en sluiten&quot; om de integratie te voltooien.

#### Configuratie-instellingen voor MS Dynamics-cloud {#dynamicsconfig}

De stappen die in deze sectie worden beschreven zijn inbegrepen om u van Cliënt ID, Geheime cliënt en details van uw instantie van de Cloud van de Dynamica van MS te helpen de plaats bepalen.

1. Navigeren naar [https://portal.azure.com/](https://portal.azure.com/) en aanmelden.
1. Selecteer in het linkermenu de optie Alle services.
1. Zoek of navigeer naar &quot;Toepassingsregistratie&quot;.
1. Maak of selecteer een bestaande toepassingsregistratie.
1. Kopieer de **Toepassings-id** te gebruiken als OAuth **Client-id** in de AEM cloudconfiguratie
1. Klik op &quot;Instellingen&quot; of &quot;Manifest&quot; om de **Reageer URL&#39;s.**

   1. Deze URL moet overeenkomen met de URL die wordt gebruikt om toegang te krijgen tot uw AEM server wanneer de OData-service wordt geconfigureerd.

1. Klik in de weergave Instelling op &quot;Toetsen&quot; om een nieuwe sleutel weer te geven (dit wordt gebruikt als de Client Secret in AEM ).

   1. Zorg ervoor dat u een kopie van de sleutel bewaart, omdat u deze later niet in Azure of AEM kunt bekijken.

1. Navigeer naar het dashboard voor de instantie van MS Dynamics om de URL van de hoofdmap van de bron/service te zoeken.
1. Klik in de bovenste navigatiebalk op &quot;Verkoop&quot; of op uw eigen instantietype en &quot;Instellingen selecteren&quot;.
1. Klik rechts onderaan op Aanpassingen en Developer Resources.
1. Hier vindt u de hoofdmap van de service: bijv.

   *`https://msdynamicsserver.api.crm3.dynamics.com/api/data/v9.1/`

1. Hier vindt u meer informatie over de URL van het token Vernieuwen en Toegangstoken:

   *[https://docs.microsoft.com/en-us/rest/api/datacatalog/authenticate-a-client-app](https://docs.microsoft.com/en-us/rest/api/datacatalog/authenticate-a-client-app)*

#### Het Forms-gegevensmodel testen (Dynamics) {#testing-the-form-data-model}

Nadat de cloudconfiguratie is voltooid, wilt u mogelijk het gegevensmodel van het formulier testen.

1. Ga naar

   *https://&lt;aemserver>:&lt;port>/aem/forms.html/content/dam/formsanddocuments-fdm/we-gov*

1. Selecteer &quot;We.gov Microsoft Dynamics CRM FDM&quot; en selecteer &quot;Eigenschappen&quot;.

   ![Eigenschappen van Dynamics CRM FDM](assets/properties_dynamics_crm.jpg)

1. Navigeer naar het tabblad Bron bijwerken.
1. Zorg ervoor dat de &quot;Context-Aware Configuratie&quot;aan &quot;/conf/wij-gov&quot;wordt geplaatst en dat de gevormde gegevensbron &quot;ms-dynamics-odata-cloud-dienst is&quot;.

   ![Gevormde gegevensbron](assets/configured_data_source.jpg)

1. Bewerk het formuliergegevensmodel.

1. Test de diensten om ervoor te zorgen zij met succes met de gevormde Gegevensbron verbinden.

   >[!NOTE]
   Nadat u de services hebt getest, klikt u op **Annuleren** om ervoor te zorgen dat onvrijwillige wijzigingen niet worden doorgegeven aan het formuliergegevensmodel.

   >[!NOTE]
   Er is gemeld dat een AEM Server opnieuw opstarten vereist was voor de gegevensbron om met succes aan FDM te binden.

#### Het Forms-gegevensmodel testen (Derby) {#test-fdm-derby}

Nadat de cloudconfiguratie is voltooid, wilt u mogelijk het gegevensmodel van het formulier testen.

1. Navigeren naar *https://&lt;aemserver>:&lt;port>/aem/forms.html/content/dam/formsanddocuments-fdm/we-gov*

1. Selecteer **We.gov-inschrijving voor FDM** en selecteert u **Eigenschappen**.

   ![Eigenschappen van Dynamics CRM FDM](assets/aftia-enrollment-fdm.jpg)

1. Ga naar de **Bron bijwerken** tab.

1. Zorg ervoor dat de **Contextbewuste configuratie** is ingesteld op `/conf/we-gov` en dat de gevormde gegevensbron is **We.Gov Derby DS**.

   ![Eigenschappen van Dynamics CRM FDM](assets/aftia-update-data-source.jpg)

1. Klikken op **Opslaan en sluiten**.

1. [De services testen](work-with-form-data-model.md#test-data-model-objects-and-services) om ervoor te zorgen dat deze verbinding maken met de geconfigureerde gegevensbron

   * Selecteer de optie **HOMEMORTGAGEACCOUNT** en geef het een dienst. Test de dienst en de systeembeheerders kunnen gegevens zien die worden teruggewonnen.

### Adobe Analytics-configuratie (optioneel) {#adobe-analytics-configuration}

Deze sectie bevat details en instructies over de Configuratie van Adobe Analytics Cloud.

**Referenties:**

* [Integreren met Adobe Analytics](../../sites-administering/adobeanalytics.md)

* [Verbinding maken met Adobe Analytics en frameworks maken](../../sites-administering/adobeanalytics-connect.md)

* [Gegevens van paginaanalyse bekijken](../../sites-authoring/pa-using.md)

* [Analyses en rapporten configureren](configure-analytics-forms-documents.md)

* [AEM Forms-analyserapporten weergeven en begrijpen](view-understand-aem-forms-analytics-reports.md)

### Configuratie van Adobe Analytics-cloudservice {#adobe-analytics-cloud-service-configuration}

Dit pakket wordt vooraf geconfigureerd voor verbinding met Adobe Analytics. De onderstaande stappen zijn beschikbaar om deze configuratie te kunnen bijwerken.

1. Navigeren naar *https://&lt;aemserver>:&lt;port>/libs/cq/core/content/tools/cloudservices.html*
1. Zoek de sectie Adobe Analytics en selecteer de koppeling &quot;Configuraties tonen&quot;.
1. Selecteer de configuratie &quot;We.Gov Adobe Analytics (Analytics Configuration)&quot;.

   ![Configuratie van cloudservices voor analyse](assets/analytics_config.jpg)

1. Klik op de knop Bewerken om de Adobe Analytics-configuratie bij te werken (u moet het Gedeelde geheim opgeven). Klik op &quot;Verbinding maken met Analytics&quot; om verbinding te maken en op &quot;OK&quot; om de verbinding te voltooien.

   ![We.Gov Adobe Analytics](assets/wegov_adobe_analytics.jpg)

1. Klik op dezelfde pagina op &quot;We.Gov Adobe Analytics Framework (Analytics Framework)&quot; als u de frameworkconfiguraties wilt bijwerken (zie [AEM maken inschakelen](../../forms/using/forms-install-configure-gov-reference-site.md#enableauthoring) om Authoring in te schakelen).

#### Adobe Analytics Locating User Credentials {#analytics-locating-user-credentials}

Om de gebruikersgegevens voor een Adobe Analytics-account te vinden, moet de accountbeheerder de volgende taken uitvoeren.

1. Navigeer naar de Adobe Experience Cloud-portal.
   * Aanmelden met uw beheerdersreferenties
1. Selecteer het Adobe Analytics-pictogram in het hoofddashboard.
   ![Snelle toegang](assets/aftia-quick-access.jpg)
1. Navigeer naar het tabblad Beheer en selecteer de optie Gebruikersbeheer (Verouderd)
   ![Rapporten](assets/aftia-reports.jpg)
1. Selecteer **Gebruikers** tab.
   ![Gebruikersbeheer](assets/aftia-user-management.jpg)
1. Selecteer de gewenste gebruiker in de lijst met gebruikers.
1. Blader naar de onderkant van de pagina en de verificatiegegevens van de gebruikers worden onder aan de pagina weergegeven.
   ![Toegang beheren](assets/aftia-admin-user-access.jpg)
1. De gebruikersnaam en de gedeelde geheime informatie worden rechts in het vak met machtigingen weergegeven.
1. Merk op dat de gebruikersbenaming een dubbelepunt binnen de naam zal hebben al informatie op de linkerzijde van de dubbelepunt de gebruikersbenaming is, en alle informatie op het recht van de dubbelepunt zal de bedrijfsnaam zijn.
   * Hier is een voorbeeld van: *username : bedrijfsnaam*

#### Gebruikersverificatie instellen in Adobe Analytics {#setup-user-authentication}

Beheerders kunnen gebruikers AEM analysebevoegdheden verlenen door de volgende handelingen uit te voeren.

1. Navigeer naar de Adobe Admin Console.

1. Klik op de instantie Analytics die aan de Admin console wordt blootgesteld.

   * Deze bevindt zich op de hoofdpagina van de beheerpagina.

1. Selecteer Analytics voor volledige beheerdersrechten.

1. Voeg een gebruiker aan het Profiel toe.

   ![Analyse van volledige beheertoegang](assets/aftia-full-admin-access.jpg)

1. Klik op het tabblad Machtigingen nadat de gebruiker-id is toegewezen aan het profiel.

1. Controleer of alle machtigingen zijn toegewezen aan het profiel.

   ![Machtigingen bewerken](assets/aftia-admin-access-edit.jpg)

1. Wanneer de machtigingen eenmaal zijn toegewezen over de mogelijkheid voor een gebruiker om zich aan te melden, kan dit enkele uren duren.

### Adobe Analytics-rapportage {#adobe-analytics-reporting}

#### Adobe Analytics-sites weergeven {#view-adobe-analytics-sites-reporting}

>[!NOTE]
AEM Forms Analytics-gegevens zijn offline beschikbaar of zonder Adobe Analytics Cloud Configuration als de `we-gov-forms.ui.analytics-<version>.zip` -pakket is geïnstalleerd, maar voor AEM Sites-gegevens is een actieve cloudconfiguratie vereist.

1. Navigeren naar *https://&lt;aemserver>:&lt;port>/sites.html/content*
1. Selecteer de &quot;AEM Forms We.Gov-site&quot; om de sitepagina&#39;s weer te geven.
1. Selecteer een van de sitepagina (bijvoorbeeld Home) en kies &quot;Analytics &amp; Recommendations&quot;.

   ![Analyse en Recommendations](assets/analytics_recommendations.jpg)

1. Op deze pagina wordt opgehaalde informatie van Adobe Analytics weergegeven die betrekking heeft op de AEM Sites-pagina (opmerking: Deze informatie wordt door het ontwerp periodiek vernieuwd vanuit Adobe Analytics en wordt niet in real-time weergegeven).

   ![AEM Sites-analyse](assets/sites_analysis.jpg)

1. Terug op de pagina van de paginamening (betreden in stap 3.), kunt u de informatie van de paginamening ook bekijken door de vertoning te veranderen die punten in de &quot;Mening van de Lijst&quot;plaatst te bekijken.
1. Zoek het vervolgkeuzemenu Weergave en selecteer Lijstweergave.

   ![Lijstweergave](assets/list_view.jpg)

1. Selecteer in hetzelfde menu de optie Weergave-instelling en selecteer de kolommen die u wilt weergeven in de sectie Analytics.

   ![Kolommen configureren](assets/configure_columns.jpg)

1. Klik op &quot;Bijwerken&quot; om de nieuwe kolommen beschikbaar te maken.

   ![Weergave van nieuwe kolommen](assets/new_columns_display.jpg)

#### Rapporten van Adobe Analytics-formulieren weergeven {#view-adobe-analytics-forms-reporting}

>[!NOTE]
AEM Forms Analytics-gegevens zijn offline beschikbaar of zonder Adobe Analytics Cloud Configuration als de `we-gov-forms.ui.analytics-<version>.zip` -pakket is geïnstalleerd, maar voor AEM Sites-gegevens is een actieve cloudconfiguratie vereist.

1. Ga naar

   *https://&lt;aemserver>:&lt;port>/aem/forms.html/content/dam/formsanddocuments/adobe-gov-forms*

1. Selecteer het adaptieve formulier &quot;Inschrijvingsaanvraag voor gezondheidsvoordelen&quot; en selecteer de optie &quot;Analyserapport&quot;.

   ![Analyserapport](assets/analytics_report.jpg)

1. Wacht tot de pagina is geladen en bekijk de gegevens in het Analysapport.

   ![Rapportgegevens voor Analyses weergeven](assets/analytics_report_data.jpg)

### Adobe Automated Forms Configuration Enablement {#automated-forms-enablement}

Gebruikers van het gereedschap Conversie moeten het volgende hebben om AEM Forms te kunnen installeren en configureren met de Adobe Forms.

1. Toegang tot Adobe I/O.

1. Toestemming om een integratie met de dienst van de Omzetting van Adobe Forms tot stand te brengen.

1. Adobe AEM 6.5 nieuwste servicepack die als auteur wordt uitgevoerd.

Lees het volgende voordat u verdere instructies leest:

* [De service voor automatische conversie van formulieren configureren](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/configure-service.html)

#### Een IMS-configuratie maken, deel 1 {#creating-ims-config}

Om de service zodanig te configureren dat correct wordt gecommuniceerd met het gereedschap voor het converteren van formulieren, moeten gebruikers de service Identity Management System (IMS) configureren om zich bij Adobe I/O te kunnen registreren.

1. Ga naar https://&lt;aemserver>:&lt;port> > Klik linksboven op Adobe Experience Manager > Gereedschappen > Beveiliging > Adobe IMS-configuratie.

1. Klik op Maken.

1. Voer de handelingen uit in de onderstaande afbeelding.

   ![Configuratie van technische IMS-account](assets/aftia-technical-account-configuration.jpg)

1. Zorg ervoor dat u het certificaat downloadt.

1. Ga niet verder met de rest van de configuratie - revisiesectie [Integratie in Adobe I/O maken](#create-integration-adobeio)

>[!NOTE]
Het certificaat dat in deze sectie wordt gemaakt, wordt gebruikt om de integratieservice in Adobe I/O te maken. Zodra de gebruikers in de integratieservice hebben gecreeerd kunnen de gebruikers die informatie van Adobe I/O gebruiken om de configuratie te beëindigen.

#### Integratie in Adobe I/O maken {#create-integration-adobeio}

Zorg ervoor u de capaciteit hebt om een integratie binnen uw domein van de Adobe tot stand te brengen als u niet uw systeembeheerder contacteert dit.

1. Ga naar de [Adobe I/O-console](https://console.adobe.io/).

1. Klik op Integratie maken.

1. Selecteer Toegang tot een API.

1. Zorg ervoor dat u zich in de juiste groep bevindt (vervolgkeuzelijst rechtsboven).

1. Selecteer in de sectie Experience Cloud het gereedschap Forms-omzetting.

1. Klik op Doorgaan.

1. Voer de naam en beschrijving van uw integratie in.

1. Als u de openbare sleutel uit paragraaf 2.1 gebruikt, plaatst u deze in de integratie van de sleutel.

1. Selecteer een profiel voor uw automatede form conversion.

   ![Nieuwe integratie maken](assets/aftia-create-new-integration.jpg)

#### IMS-configuratiedeel 2 maken {#create-ims-config-part-next}

Nu u een integratie hebt gecreeerd laten ons de installatie van de configuratie voltooien IMS.

1. Klik op de integratie in Adobe I/O om de verbindingsgegevens weer te geven.

1. Navigeer naar de IMS-configuratie in AEM (Gereedschappen > Beveiliging > IMS)

1. Klik op Volgende in het scherm IMS Configuration.

1. Voer de verificatieserver in (de waarde die in de schermafbeelding wordt weergegeven).

1. Voer de API-sleutel in.

1. Ga het cliëntgeheim in (moet klikken blootstellen op de Integratie in Adobe I/O om het te onthullen).

1. Klik op het tabblad JWT in Adobe I/O om de JWT-payload op te halen en plak deze in de payload van de IMS-configuratie.

   ![Payload IMS-configuratie](assets/aftia-payload-ims-config.jpg)

1. Nadat u de IMS-configuratie hebt gemaakt, klikt u op de IMS-configuratie en selecteert u Health Check, zodat gebruikers het volgende resultaat zien.

   ![Gezondheidsbevestiging](assets/aftia-health-confirmation.jpg)

#### Cloud Configuration (Wij.Gov AFC-productie) configureren {#configure-cloud-configuration}

Nadat de IMS-configuratie is voltooid, kunnen we de cloudconfiguratie in AEM bekijken. Als de configuratie niet bestaat, gebruikt u de volgende stappen om de wolkenconfiguratie in AEM tot stand te brengen:

1. Open uw browser en navigeer naar de URL van het systeem https://&lt;domain_name>:&lt;system_port>

1. Klik op Adobe Experience Manager in de linkerbovenhoek van het scherm > Gereedschappen > Cloud Services > Geautomatiseerde configuratie van Forms-gesprek.

1. Selecteer de configuratiemap waarin u de configuratie wilt plaatsen.

1. Klik op Maken.

1. Voer de gegevens in de onderstaande schermafbeelding in.

   ![AFC-productie](assets/aftia-afc-production.jpg)

1. Geef de configuratie een titel en een naam.

1. De service-URL voor het systeem is ingesteld op https://aemformsconversion.adobe.io/.

1. Sjabloon-URL */conf/we-gov/settings/wcm/templates/we-gov-flamingo-template*.

1. Thema-URL: */content/dam/formsanddocuments-themes/adobe-gov-forms-themes/we-gov-theme*

1. Klik op Next.

1. Voor deze configuratie, verlaten wij de twee checkbox waarden leeg.

   * Voor meer informatie over deze opties raadpleegt u [De cloudservice configureren](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/configure-service.html#configure-the-cloud-service).

#### Cloud Configuration (wij.Finance AFC Production) configureren {#configure-cloud-configuration-wefinance}

Zodra de configuratie IMS volledig is, kunnen wij te werk gaan om de wolkenconfiguratie in AEM tot stand te brengen.

1. Open uw browser en navigeer naar de URL van het systeem https://&lt;domain_name>:&lt;system_port>

1. Klik op Adobe Experience Manager in de linkerbovenhoek van het scherm > Gereedschappen > Cloud Services > Geautomatiseerde configuratie van Forms-gesprek.

1. Selecteer de configuratiemap waarin u de configuratie wilt plaatsen.

1. Klik op Maken.

1. Voer de gegevens in de onderstaande schermafbeelding in.

   ![We.AFC-productie financieren](assets/aftia-wefinance-afc-prod.jpg)

1. Geef de configuratie een titel en een naam.

1. De service-URL voor het systeem is ingesteld op https://aemformsconversion.adobe.io/

1. Sjabloon-URL: */conf/we-finance/settings/wcm/templates/we-finance-adaptive-form*

1. Thema-URL: */content/dam/formsanddocuments-themes/adobe-finance-forms-themes/we-finance-theme*

1. Klik op Next.

1. Voor deze configuratie, verlaten wij de twee checkbox waarden leeg.

   * Voor meer informatie over deze opties raadpleegt u [De cloudservice configureren](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/configure-service.html#configure-the-cloud-service).

#### De formulierconversie testen (Web.Gov-inschrijvingstoepassing) {#test-forms-conversion}

Wanneer de configuratie is ingesteld, kunnen gebruikers deze testen door een PDF-document te uploaden.

1. Ga naar het AEM https://&lt;domain_name>:&lt;system_port>

1. Klik op Forms > Forms &amp; Documents > AEM Forms Web.gov Forms > AFC.

1. Selecteer de PDF van de Toepassing van de Inschrijving Web.Gov.

1. Klik op de knop **Geautomatiseerde conversie starten** in de rechterbovenhoek.

1. Gebruikers moeten de optie kunnen zien zoals hieronder wordt weergegeven.

   ![Omgezet adaptief formulier](assets/aftia-converted-adaptive-form.jpg)

1. Zodra de knop is geselecteerd, krijgen gebruikers de volgende opties te zien

   * Zorg ervoor dat gebruikers de optie *We.GOV AFC-productie* configuratie

   ![Conversie-instellingen](assets/aftia-conversion-settings.jpg)

   ![Geavanceerde conversie-instellingen](assets/aftia-conversion-settings-2.jpg)

1. Selecteer de beginomzetting zodra u alle opties hebt gevormd die u zou willen gebruiken.

1. Wanneer het conversieproces begint, moeten gebruikers het volgende scherm zien:

   ![Conversie-instellingen](assets/aftia-conversion-in-progress.jpg)

1. Wanneer de conversie is voltooid, zien gebruikers het volgende scherm:

   ![Omgezet adaptief formulier](assets/aftia-converted-adaptive-form-2.jpg)

   Klik op de knop **Uitvoer** om het gegenereerde adaptieve formulier weer te geven.

#### Bekende problemen en notities {#known-issues-notes}

De dienst van de Automatede form conversion omvat bepaalde [best practices, bekende complexe patronen](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/styles-and-pattern-considerations-and-best-practices.html), en [bekende problemen](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/known-issues.html). Bekijk deze voordat je AEM Forms Automatede form conversion-service gaat gebruiken.

1. Genereer het formulier met adaptieve formulieren genereren zonder gegevensbindingen ingeschakeld als u het formulier na conversie aan een FDM wilt binden.

1. Zorg ervoor dat de sjabloonmap jcr:read voor iedereen machtiging heeft ingeschakeld, anders kan de gebruiker de sjabloon niet lezen uit de opslagplaats en mislukt de conversie.

## Aanpassing van demopakket {#demo-package-customizations}

Deze sectie bevat instructies voor het aanpassen van de demo.

### Aanpassing sjablonen {#templates-customization}

Bewerkbare sjablonen vindt u op de volgende locatie:

*https://&lt;aemserver>:&lt;port>/libs/wcm/core/content/sites/templates.html/conf/we-gov*

Deze sjablonen bevatten de sjablonen AEM Site, Adaptief formulier en Interactieve communicatie, die zijn gemaakt en samengesteld met componenten die u kunt vinden op:

*https://&lt;aemserver>:&lt;port>/crx/de/index.jsp#/apps/we-gov/components*

#### Stijlsysteem {#customizetemplates}

Deze site bevat ook clientbibliotheken, waarvan er één Bootstrap 4 importeert ( [https://getbootstrap.com/](https://getbootstrap.com/) ). Deze clientbibliotheek is beschikbaar op

*https://&lt;aemserver>:&lt;port>/crx/de/index.jsp#/apps/we-gov/clientlibs/clientlib-base/css/bootstrap*

De bewerkbare sjablonen in dit pakket worden ook vooraf geconfigureerd met sjabloon-/paginabeleid dat de CSS-klassen Bootstrap 4 gebruikt voor paginering, opmaak, enzovoort. Niet alle klassen zijn toegevoegd aan het sjabloonbeleid, maar elke klasse die door Bootstrap 4 wordt ondersteund, kan aan het beleid worden toegevoegd. Zie de pagina Aan de slag voor een lijst met beschikbare klassen:

[https://getbootstrap.com/docs/4.1/getting-started/introduction/](https://getbootstrap.com/docs/4.1/getting-started/introduction/)

De malplaatjes inbegrepen in dit pakket steunen ook het Systeem van de Stijl:

[Stijlsysteem](../../sites-authoring/style-system.md)

#### Sjabloonlogo&#39;s {#template-logos}

DAM-projectelementen omvatten onder andere Wij.Gov-logo&#39;s en -afbeeldingen. Deze activa zijn beschikbaar op:

*https://&lt;aemserver>:&lt;port>/assets.html/content/dam/we-gov*

Wanneer u de pagina- en formuliersjablonen bewerkt, kunt u de logo&#39;s van een merk bijwerken door de navigatie- en voettekstcomponenten te bewerken. Deze componenten bieden een configureerbaar merk- en logodialoogvenster dat kan worden gebruikt om logo&#39;s bij te werken:

![Sjabloonlogo&#39;s](assets/template_logos.jpg)

Zie Pagina-inhoud bewerken voor meer informatie:

[Paginacontent bewerken](../../sites-authoring/editing-content.md)

### Aanpassing sitepagina&#39;s {#sites-pages-customization}

Alle sitepagina&#39;s zijn beschikbaar via: *https://&lt;aemserver>:&lt;port>/sites.html/content/we-gov*

Deze sitepagina&#39;s maken ook gebruik van het pakket AEM raster om de lay-out van een paar componenten te bepalen.

#### Stijlsysteem {#style-system}

Pagina&#39;s die in dit pakket zijn opgenomen, ondersteunen ook het stijlsysteem:

[Stijlsysteem](../../sites-authoring/style-system.md)

U kunt ook verwijzen naar [Sjablonen aanpassen, stijlsysteem](../../forms/using/forms-install-configure-gov-reference-site.md#customizetemplates) voor documentatie over ondersteunde stijlen.

### Aanpassing van adaptieve formulieren {#adaptive-forms-customization}

Alle adaptieve formulieren zijn beschikbaar op:

*https://&lt;aemserver>:&lt;port>/aem/forms.html/content/dam/formsanddocuments/adobe-gov-forms*

Deze formulieren kunnen worden aangepast aan bepaalde gebruiksgevallen. Houd er rekening mee dat bepaalde velden en verzendlogica niet moeten worden gewijzigd om ervoor te zorgen dat het formulier correct blijft functioneren. Dit omvat:

**Inschrijvingsaanvraag voor gezondheidsvoordelen:**

* contact_id - Verborgen gebied dat wordt gebruikt om identiteitskaart van de Vraag van de Dynamica van MS tijdens voorlegging te ontvangen
* Verzenden - Voor verzenden is aanpassing van knoplogica vereist ter ondersteuning van callbacks. De aanpassing wordt gedocumenteerd, maar een groot manuscript werd vereist om de vorm voor te leggen terwijl het uitvoeren van zowel een POST als GET verrichting aan de Dynamica van MS via het Model van Gegevens van Forms.
* Het Comité van de wortel - de gebeurtenis initialiseert wordt gebruikt om een knoop van de Dynamiek van MS aan AEM Inbox op de minst indringende manier toe te voegen mogelijk aangezien alle AEM componenten van de SPRITE van Inbox niet-wijzigbaar zijn.

#### Adaptieve formulieropmaak {#adaptive-form-styling}

U kunt adaptieve formulieren ook opmaken met de Stijleditor of de themaeditor:

* [Inline styling van adaptieve formuliercomponenten](inline-style-adaptive-forms.md)
* [Thema&#39;s maken en gebruiken](themes.md)

### Workflowaanpassing {#workflow-customization}

Het Aangepaste formulier voor inschrijving wordt voor verwerking naar een OSGI-workflow verzonden. Deze workflow is te vinden op *https://&lt;aemserver>:&lt;port>/conf/we-gov/settings/models/we-gov-process.html*.

Vanwege bepaalde beperkingen bevat deze workflow diverse scripts en aangepaste stappen voor het proces van de OSGI-workflow. Deze workflowstappen zijn gemaakt als algemene stappen en zijn niet gemaakt met configuratievensters. Op dit moment is de configuratie van de workflowstappen afhankelijk van procesargumenten.

Alle Java-code voor workflowstap is opgenomen in de **we-gov-forms.core-&lt;version>.jar** bundel.

## Demomogelijkheden en bekende problemen {#demo-considerations-and-known-issues}

Deze sectie bevat informatie over demo-functies en ontwerpbeslissingen die tijdens het demonstratieproces speciale aandacht behoeven.

### Demooverwegingen {#demo-considerations}

* Conform AGRS-159, zorg ervoor dat de naam (eerste, midden, en laatste) van het contact in de Aangepaste Vorm van de Inschrijving wordt gebruikt uniek is.
* Met het adaptieve inschrijvingsformulier wordt de e-mail van de Adobe Sign verzonden naar de e-mail die is opgegeven in het e-mailveld van het formulier. Dit e-mailadres mag niet hetzelfde e-mailadres zijn als het e-mailadres dat wordt gebruikt om de configuratie van de Adobe Sign-cloud te configureren.

### Bekende problemen {#known-issues}

* (AGRS-120) De component van de Navigatie van de Plaats steunt momenteel geen genestelde kindpagina&#39;s die meer dan 2 niveaus diep zijn.
* (AGRS-159) De huidige FDM van de Dynamiek van MS moet twee handelingen eerst uitvoeren, de Adaptieve gegevens van de Vorm van de Inschrijving aan Dynamiek POSTEN, en dan het gebruikersverslag ophalen om identiteitskaart van het Contact terug te winnen. In zijn huidige staat, zal het halen van identiteitskaart van het Contact ontbreken als meer dan twee gebruikers met de zelfde naam in Dynamiek aanwezig zijn, die niet de Aangepaste Vorm van de Inschrijving zal toestaan om voor te leggen.

## Toegankelijkheidstests configureren {#configure-accessibility-testing}

### Chrome voor toegankelijkheidstest inschakelen bij {#enable-chrome-add-on}

Installeer de gevonden Chrome-plug-in om de toegankelijkheid te testen [hier](https://chrome.google.com/webstore/detail/accessibility-developer-t/fpkknkljclfencbdbgkenhalefipecmb?hl=en). <!-- This URL is a 404. Please fix and update this topic. We ought not to be writing about third-party software that we have no control over to avoid these 404s. Consider making this topic entirely generic and leaving it up to the user to choose their own Accessibility Testing add-on. -->

Nadat de pagina is geïnstalleerd, laadt u de pagina die u wilt testen in de Chrome-browser (Opmerking: Als er meerdere tabbladen zijn geopend, heeft dit mogelijk invloed op de score. Het is aan te raden slechts één tab open te hebben.) Nadat de pagina is geladen
**rechtsklikken** op de pagina en selecteer **Audits** -tabblad. Er kunnen ontwikkelaars het type controle selecteren dat door de insteekmodule Toegankelijkheid moet worden uitgevoerd. Nadat alle gewenste opties zijn geselecteerd, kan de gebruiker op de knop Rapport genereren klikken. Hiermee wordt een PDF-document gegenereerd met de algemene toegankelijkheidsscore en de functies die kunnen worden gebruikt om de score voor toegankelijkheid in het algemeen te verhogen.

Nadat het rapport in werking wordt gesteld, kunnen de gebruikers het volgende verwachten te zien:

![Toegankelijkheidsrapport](assets/aftia-accessibility.jpg)

Het nummer dat voor gebruikers wordt weergegeven, is de algemene toegankelijkheidsscore die ze hebben behaald. Er is ook een beschrijving van hoe dit na de score werd berekend.

Als gebruikers dit willen exporteren, kunnen ze op de drie knoppen aan de rechterkant van het scherm klikken en een van de andere opties voor de plug-in selecteren.

![Toegankelijkheidsrapport](assets/aftia-accessibility-report.jpg)

### Ultramarijnthema {#ultramarine-theme}

Het algemeen beschikbare Ultramarinesthema dat door Adobe wordt onderhouden, is opgenomen in het
`we-gov-forms.pkg.all-<version>.zip` installeerbaar ZIP-bestand. Zodra dit pakket is geïnstalleerd met behulp van CRX.

Pakketbeheer, gebruikers hebben toegang tot het Ultramarine-thema in AEM Forms door naar **Forms** > **Thema&#39;s** > **Referentiethema&#39;s** > **Ultramarijntoegankelijk**.

![Ultramarijnthema](assets/aftia-ultramarine-theme.jpg)

## Configuratieopties {#configuration-options}

Gebruikers kunnen verschillende workflowserviceopties configureren, waaronder:

1. Microsoft Dynamics Entry
1. Adobe Sign
1. Aangepast communicatiebeheer AEM
1. Adobe Analytics

Om hen te vormen om binnen het Werkschema worden toegelaten moeten de gebruikers de volgende taken uitvoeren.

1. Ga naar https://&#39;[server]:[poort]&quot;/system/console/configMgr.

1. Zoek de *WeGov-configuraties*.

1. Open de de dienstdefinitie en laat de geselecteerde diensten toe om binnen het werkschema worden aangehaald.

   >[!NOTE]
   Enkel omdat een gebruiker de dienst binnen de pagina van de Manager van de Configuratie toelaat, worden de gebruikers nog vereist om een de dienstconfiguratie op te zetten om met de externe gevraagde diensten te communiceren.

   ![we gov - formulierpakket](assets/aftia-configuration-options.jpg)

1. Klik op de knop Opslaan als u klaar bent om de instellingen op te slaan.

## Volgende stappen {#next-steps}

Nu bent u allen klaar om de Web.Gov verwijzingsplaats te onderzoeken. Voor meer informatie over de workflow en stappen van de website Web.Gov raadpleegt u [We.Gov-referentiesite doorloopt](../../forms/using/forms-gov-reference-site-user-demo.md).
