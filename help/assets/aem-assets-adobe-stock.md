---
title: Beheren [!DNL Adobe Stock] middelen
description: Zoek, haal, vergunning, en beheer [!DNL Adobe Stock] activa van binnen [!DNL Adobe Experience Manager]. Gebruik de in licentie gegeven activa als elk ander digitaal actief.
contentOwner: Vishabh Gupta
feature: Search, Adobe Stock
role: User, Admin
exl-id: 8ec597df-bb64-4768-bf9c-e8cca4fea25b
source-git-commit: 6d1073003c1b78be848652be0b387889eedbc193
workflow-type: tm+mt
source-wordcount: '2288'
ht-degree: 3%

---

# [!DNL Adobe Stock]-elementen gebruiken in [!DNL Adobe Experience Manager Assets] {#use-adobe-stock-assets-in-aem-assets}

<!-- old content

[!DNL Experience Manager Assets] provides users the ability to search, preview, save, and license [!DNL Adobe Stock] assets directly from [!DNL Experience Manager]. 

Organizations can integrate their [!DNL Adobe Stock] enterprise plan with [!DNL Experience Manager Assets] to ensure that licensed assets are broadly available for their creative and marketing projects, with the powerful asset management capabilities of [!DNL Experience Manager].

[!DNL Adobe Stock] service provides designers and businesses with access to millions of high-quality, curated, royalty-free photos, vectors, illustrations, videos, templates, and 3D assets for all their creative projects. [!DNL Experience Manager] users are able to quickly find, preview, and license [!DNL Adobe Stock] assets that are saved in [!DNL Experience Manager], without leaving the [!DNL Experience Manager] interface.
-->

<!-- New overview content
-->

[!DNL Adobe Stock] biedt ontwerpers en bedrijven toegang tot miljoenen kwalitatief hoogstaande, gekrulde, royaltyvrije foto&#39;s, vectoren, illustraties, video&#39;s, sjablonen en 3D-middelen voor al hun creatieve projecten.

[!DNL Adobe Stock] voor het aanbieden van een bedrijf, door gebrek, omvat het delen van rechten over de organisatie. Zodra een middel door een gebruiker van uw organisatie is vergunning gegeven, kunnen andere gebruikers van uw organisatie, dit middel identificeren downloaden en gebruiken zonder het moeten het opnieuw vergunning geven. Zodra een activa door uw organisatie zijn vergunning gegeven, is het recht om het te gebruiken onvoorwaardelijk.

Organisaties kunnen hun [!DNL Adobe Stock]-plan integreren met [!DNL Experience Manager Assets] om ervoor te zorgen dat gelicentieerde middelen breed beschikbaar zijn voor hun creatieve en marketingprojecten, met de krachtige mogelijkheden voor middelenbeheer van [!DNL Experience Manager]. [!DNL Experience Manager] gebruikers kunnen snel Adobe Stock-elementen zoeken, voorvertonen en licentiëren die zijn opgeslagen in  [!DNL Experience Manager], zonder de  [!DNL Experience Manager] interface te verlaten.

<!-- Old content
## Prerequisites {#prerequisites}

The integration requires an [enterprise [!DNL Adobe Stock] plan](https://stockenterprise.adobe.com/).
-->

## [!DNL Experience Manager] en [!DNL Adobe Stock] integreren {#integrate-aem-and-adobe-stock}

[!DNL Experience Manager Assets] biedt gebruikers de mogelijkheid  [!DNL Adobe Stock] middelen rechtstreeks te zoeken, voor te vertonen, op te slaan en te licentiëren vanuit  [!DNL Experience Manager].

**Vereisten**

De integratie vereist:
* An [enterprise [!DNL Adobe Stock] plan](https://stockenterprise.adobe.com/)
* Een gebruiker met machtigingen in Admin Console naar het standaardprofiel voor het product Stock
* Een gebruiker met machtigingen voor het profiel Developer Access voor het maken van integratie in de Adobe Developer Console

Een bedrijfsplan [!DNL Adobe Stock]
* Biedt productmachtigingen voor [!DNL Adobe Stock] (bestanden die zijn verbonden met Experience Manager)
* Crediteringen die zijn aangeschaft in de [!DNL Adobe Admin Console] voor uw aandelenrechten
* Laat de authentificatie van de Rekening van de Dienst (JWT) binnen [!DNL Adobe Developer Console] voor uw aandelenrecht toe
* Hiermee kunt u de credits en licenties globaal beheren vanuit [!DNL Adobe Admin Console]

Binnen de machtiging bestaat een standaardproductprofiel voor [!DNL Adobe Stock] in [!DNL Admin Console]. U kunt meerdere profielen maken en deze profielen bepalen wie een licentie voor de middelen van Stock kan verkrijgen. Een gebruiker die rechtstreeks toegang heeft tot het productprofiel heeft toegang tot [https://stock.adobe.com/](https://stock.adobe.com/) en een licentie voor Stock-elementen. Terwijl er een andere methode is om de Toegang van de Ontwikkelaar te gebruiken om integratie (API) tot stand te brengen om communicatie tussen [!DNL Experience Manager] en [!DNL Adobe Stock] voor authentiek te verklaren.

>[!NOTE]
>
>De beurswaarde van de &quot;Stock Service Account&quot; (JWT) wordt geleverd met de beurswaarde van de onderneming.
>
>De integratie ondersteunt geen Oauth-authenticatie voor aandelenrechten voor bedrijven.

<!-- old content
To allow communication between [!DNL Experience Manager] and [!DNL Adobe Stock], create an IMS configuration and an [!DNL Adobe Stock] configuration in [!DNL Experience Manager].

>[!NOTE]
>
>Only [!DNL Experience Manager] administrators and [!DNL Admin Console] administrators for an organization can perform the integration as it requires administrator privileges.
-->

## Stappen om [!DNL Experience Manager] en [!DNL Adobe Stock] te integreren {#integration-steps}

Om [!DNL Experience Manager] en [!DNL Adobe Stock] te integreren, voer de volgende stappen in de vermelde opeenvolging uit:

1. [Openbaar certificaat verkrijgen](#public-certificate)

   Maak in [!DNL Experience Manager] een IMS-account en genereren een openbaar certificaat (openbare sleutel).

1. [Verbinding voor serviceaccount (JWT) maken](#createnewintegration)

   Maak in [!DNL Adobe Developer Console] een project voor uw [!DNL Adobe Stock]-organisatie. Onder het project, vorm API gebruikend de openbare sleutel om een verbinding van de de dienstrekening (JWT) tot stand te brengen. Krijg de geloofsbrieven van de de dienstrekening en JWT payload informatie.

1. [IMS-account configureren](#create-ims-account-configuration)

   In [!DNL Experience Manager], vorm de rekening IMS gebruikend de geloofsbrieven van de de dienstrekening en JWT lading.

1. [Cloudservice configureren](#configure-the-cloud-service)

   Configureer in [!DNL Experience Manager] een [!DNL Adobe Stock]-cloudservice met behulp van de IMS-account.


### Een IMS-configuratie maken {#create-an-ims-configuration}

De configuratie IMS verifieert uw [!DNL Experience Manager Assets] auteursinstantie met [!DNL Adobe Stock] recht.

De IMS-configuratie omvat twee stappen:

* [Openbaar certificaat verkrijgen](#public-certificate)
* [IMS-account configureren](#create-ims-account-configuration)

### Openbaar certificaat verkrijgen {#public-certificate}

Met de openbare sleutel (certificaat) wordt uw productprofiel geverifieerd in de Adobe Developer Console.

1. Meld u aan bij de auteur [!DNL Experience Manager Assets]. De standaard-URL is `http://localhost:4502/aem/start.html`.

1. Navigeer in het deelvenster **[!UICONTROL Tools]** naar **[!UICONTROL Security]** > **[!UICONTROL Adobe IMS Configurations]**.

1. Klik op **[!UICONTROL Create]** op de pagina Adobe IMS-configuraties. De pagina **[!UICONTROL Adobe IMS Technical Account Configuration]** wordt geopend.

1. Selecteer op het tabblad **[!UICONTROL Certificate]** **[!UICONTROL Adobe Stock]** in de vervolgkeuzelijst **[!UICONTROL Cloud Solution]**.

1. U kunt een certificaat maken of een bestaand certificaat opnieuw gebruiken voor de configuratie.

   Als u een certificaat wilt maken, schakelt u het selectievakje **[!UICONTROL Create new certificate]** in en geeft u een **alias** op voor de openbare sleutel. De alias fungeert als naam voor de openbare sleutel.

1. Klik op **[!UICONTROL Create certificate]**. Klik vervolgens op **[!UICONTROL OK]** om de openbare sleutel te genereren.

1. Klik op het pictogram **[!UICONTROL Download Public Key]** en sla het bestand met de openbare sleutel (.crt) op uw computer op. De openbare sleutel wordt later gebruikt om API voor uw Brand Portal huurder te vormen en de geloofsbrieven van de de dienstrekening in de Console van de Ontwikkelaar van Adobe te produceren.

   Klik op **[!UICONTROL Next]**.

   ![certificaat genereren](assets/stock-integration-ims-account.png)

1. Op het tabblad **Account** wordt een Adobe IMS-account gemaakt waarvoor de gegevens van de serviceaccount vereist zijn.

   Open een nieuw lusje en [creeer een verbinding van de de dienstrekening (JWT) in de Console van de Ontwikkelaar van Adobe](#createnewintegration).

### Verbinding voor serviceaccount (JWT) maken {#createnewintegration}

In de Console van de Ontwikkelaar van Adobe, worden de projecten en APIs gevormd op organisatieniveau. Als u een API configureert, wordt een JWT-verbinding (Service Account) gemaakt. Er zijn twee methodes om API te vormen, door een zeer belangrijk paar (privé en openbare sleutels) te produceren of door een openbare sleutel te uploaden. In dit voorbeeld worden de gegevens van de serviceaccount gegenereerd door de openbare sleutel te uploaden.

Om de geloofsbrieven van de de dienstrekening en JWT lading te produceren:

1. Meld u aan bij de Adobe Developer Console met systeembeheerdersrechten. De standaard-URL is [https://www.adobe.com/go/devs_console_ui](https://www.adobe.com/go/devs_console_ui).


   Controleer of u de juiste IMS-organisatie (Stock Entitlement) hebt geselecteerd in de vervolgkeuzelijst (organisatie).

1. Klik op **[!UICONTROL Create new project]**. Er wordt een leeg project met een door het systeem gegenereerde naam gemaakt voor uw organisatie.

   Klik op **[!UICONTROL Edit project]**. Werk **[!UICONTROL Project Title]** en **[!UICONTROL Description]** bij, en klik dan **[!UICONTROL Save]**.

1. Klik op het tabblad **[!UICONTROL Project overview]** op **[!UICONTROL Add API]**.

1. Selecteer **[!UICONTROL Adobe Stock]** in **[!UICONTROL Add an API window]**. Klik op **[!UICONTROL Next]**.

1. Selecteer **[!UICONTROL Service Account (JWT)]** verificatie in het venster **[!UICONTROL Configure API]**. Klik op **[!UICONTROL Next]**.

   ![create-jwt-credentials](assets/aem-stock-jwt.png)

1. Klik op **[!UICONTROL Upload your public key]**. Klik **[!UICONTROL Select a File]** en upload de openbare sleutel (.crt dossier) die u in [verkrijg openbare certificaat](#public-certificate) sectie hebt gedownload. Klik op **[!UICONTROL Next]**.

1. Verifieer de openbare sleutel en klik **[!UICONTROL Next]**.

1. Selecteer het standaardproductprofiel **[!UICONTROL Adobe Stock]** en klik **[!UICONTROL Save configured API]**.

1. Nadat de API is geconfigureerd, wordt u omgeleid naar de API-overzichtspagina. Klik in de linkernavigatie onder **[!UICONTROL Credentials]** op de optie **[!UICONTROL Service Account (JWT)]**. Hier, kunt u de geloofsbrieven bekijken en acties uitvoeren zoals produceren JWT tokens, exemplaar credentiedetails, en terugwinnen cliëntgeheim.

1. Kopieer op het tabblad **[!UICONTROL Client Credentials]** de **[!UICONTROL client ID]**.

   Klik **[!UICONTROL Retrieve Client Secret]** en kopieer **[!UICONTROL client secret]**.

   ![generate-jwt-credentials](assets/aem-stock-jwt-credential.png)

1. Navigeer naar het tabblad **[!UICONTROL Generate JWT]** en kopieer de informatie **[!UICONTROL JWT Payload]**.

U kunt nu de client-id (API-sleutel), het clientgeheim en de JWT-payload gebruiken om de IMS-account [te configureren in [!DNL Experience Manager Assets].](#create-ims-account-configuration)

### IMS-account configureren {#create-ims-account-configuration}

U moet de [certificate](#public-certificate) en [serviceaccount (JWT) referenties](#createnewintegration) hebben om de IMS-account te configureren.

De IMS-account configureren:

1. Open de Configuratie IMS en navigeer aan **[!UICONTROL Account]** tabel. U hield de pagina open terwijl [het openbare certificaat verkrijgen](#public-certificate).

1. Geef een **[!UICONTROL Title]** op voor het IMS-account.

   Voer in het veld **[!UICONTROL Authorization Server]** de URL in: [https://ims-na1.adobelogin.com/](https://ims-na1.adobelogin.com/).

   Typ de client-id in het veld **[!UICONTROL API key]**, **[!UICONTROL Client Secret]** en **[!UICONTROL Payload]** (JWT-payload) die u hebt gekopieerd tijdens het maken van de JWT-verbinding (Service Account)](#createnewintegration).[

1. Klik op **[!UICONTROL Create]**. Er wordt een IMS-accountconfiguratie gemaakt.

   ![configure-ims-account](assets/aem-stock-ims-config.png)

1. Selecteer de IMS-accountconfiguratie en klik op **[!UICONTROL Check Health]**.

   Klik **[!UICONTROL Check]** in de dialoogdoos. Bij succesvolle configuratie, lijkt een bericht dat *Token met succes* wordt teruggewonnen.

   ![gezondheidscontrole](assets/aem-stock-healthcheck.png)


### Cloudservice configureren {#configure-the-cloud-service}

De [!DNL Adobe Stock]-cloudservice configureren:

1. Navigeer in de gebruikersinterface [!DNL Experience Manager] naar **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Adobe Stock]**.

1. Klik op [!DNL Adobe Stock Configurations] op de pagina.**[!UICONTROL Create]**

1. Geef een **[!UICONTROL Title]** op voor de cloudconfiguratie.

   Selecteer de IMS-configuratie die u hebt gemaakt terwijl u [de IMS-account](#create-ims-account-configuration) configureert.

   Selecteer de landinstelling in de vervolgkeuzelijst.

   ![aem-stock-cloud-config](assets/aem-stock-cloud-config.png)

1. Klik op **[!UICONTROL Save & Close]**.

   Uw [!DNL Experience Manager Assets] auteurinstantie is nu geïntegreerd met [!DNL Adobe Stock]. U kunt meerdere [!DNL Adobe Stock] configuraties maken (bijvoorbeeld configuraties op basis van landinstellingen). U kunt de [!DNL Adobe Stock] elementen nu openen, zoeken en in licentie geven vanuit de gebruikersinterface van [!DNL Experience Manager].

   ![search-stock-assets](assets/aem-stock-searchstocks.png)

   >[!NOTE]
   >
   >In deze fase van integratie hebben alleen beheerders toegang tot de [!DNL Adobe Stock]-elementen, kunnen ze zoeken op Stock-elementen (met behulp van &#39;zonder onderzoek&#39;) en een licentie voor de [!DNL Adobe Stock]-elementen aanschaffen.
   >
   >Beheerders kunnen gebruikers of groepen verder toevoegen aan de [!DNL Adobe Stock]-cloudservice en deze gebruikers zonder beheer in [!DNL Experience Manager] machtigingen geven om toegang te krijgen tot de voorraadconfiguratie.

1. Als u gebruikers of groepen wilt toevoegen, selecteert u de [!DNL Adobe Stock]-cloudconfiguratie en klikt u op **[!UICONTROL Properties]**.

1. Zoek om de gebruikers of de groepen toe te voegen aan wie u toestemmingen hebt toegewezen om tot de configuratie van Adobe Stock toegang te hebben. Zie [Machtigingen toewijzen aan gebruikersgroep](#assign-permissions-to-group).


## Machtigingen toewijzen aan gebruikersgroep {#assign-permissions-to-group}

Beheerders kunnen gebruikersgroepen maken en bepaalde gebruikers of groepen machtigingen geven om toegang te krijgen tot de [!DNL Adobe Stock]-cloudservice.

Hieronder vindt u de machtigingen die een gebruiker nodig heeft om Adobe Stock-middelen te zoeken en te licentiëren:

* Vorm de weg: `/conf/global/settings/stock`
* Bevoegdheden: `jcr:read`
* Machtigingstype: `Allow`

U kunt een gebruikersgroep maken of machtigingen toewijzen aan een bestaande gebruikersgroep. Machtigingen kunnen worden toegewezen via de [!DNL Experience Manager Assets]-interface of via de [!DNL User Admin]-console.

**Toegang tot een gebruikersgroep bieden via  [!DNL Experience Manager]:**

1. Navigeer in de gebruikersinterface [!DNL Experience Manager] naar **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Groups]**. Maak een gebruikersgroep voor [!DNL Adobe Stock].

1. Ga naar **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Permissions]**.

1. Zoek naar de gebruikersgroep in het linkerpaneel en voeg nieuwe **[!UICONTROL Access Control Entry (ACE)]** voor Adobe Stock toe.

   * Vorm de weg: `/conf/global/settings/stock`
   * Bevoegdheden: `jcr:read`
   * Machtigingstype: `Allow`

   Klik op **[!UICONTROL Add]**.

   ![gebruikersmachtigingen](assets/aem-stock-user-permissions.png)

1. Ga naar **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Adobe Stock]**. Selecteer de [!DNL Adobe Stock] wolkenconfiguratie en klik **[!UICONTROL Properties]**.

1. Voeg de nieuw gecreëerde gebruikersgroep aan de [!DNL Adobe Stock] configuratie toe. Klik op **[!UICONTROL Save & Close]**.

   ![assign-user](assets/aem-stock-adduser.png)

**Toegang verlenen aan een gebruiker vanaf  [!DNL User Admin Console]:**

1. Open [!DNL Experience Manager] de Admin Console van de Gebruiker. De standaard-URL is `http://localhost:4502/userdamin`.

1. Zoek in het linkerdeelvenster naar de gebruiker door `user_id` of `name` in te voeren. Dubbelklik om de gebruikerseigenschappen te openen.

1. Navigeer naar het tabblad **[!UICONTROL Permissions]** en sta `read` machtigingen toe voor de [!DNL Adobe Stock]-cloudconfiguratie: `/conf/global/settings/stock`.

   >[!CAUTION]
   >
   >Als de wolkenconfiguratie niet wordt toegestaan, kan de gebruiker tot **[!UICONTROL Assets]** in de [!DNL Experience Manager] interface slechts toegang hebben.
   >
   >Om toegang tot [!UICONTROL Assets] en [!DNL Adobe Stock] activa toe te staan, zorg ervoor dat de wolkenconfiguratie voor de gebruiker wordt toegestaan.

1. Klik **[!UICONTROL Save]** om de toestemmingen bij te werken.

   ![assign-user-in-user-admin](assets/aem-stock-user-admin-console.png)

1. Voeg de gebruiker of de groep toe aan de [!DNL Adobe Stock] wolkenconfiguratie.


## Adobe Stock-middelen openen {#access-stock-assets}

Een niet-admin gebruiker die toestemmingen aan de [!DNL Adobe Stock] wolkenconfiguratie heeft kan [!DNL Adobe Stock] activa van [!DNL Experience Manager] van de interface zoeken en vergunning geven.

De gebruiker moet een extra stap uitvoeren om de [!DNL Adobe Stock] wolkenconfiguratie te activeren alvorens tot [!DNL Adobe Stock] activa toegang te hebben. Het is een eenmalige activiteit. Als aan de gebruiker machtigingen zijn toegewezen voor meerdere [!DNL Adobe Stock]-cloudconfiguraties, kan de gebruiker de gewenste configuratie selecteren in de **[!UICONTROL User Preferences]**.

De [!DNL Adobe Stock]-cloudconfiguratie activeren:

1. Meld u aan bij [!DNL Experience Manager].

1. Klik op het gebruikerspictogram in de rechterbovenhoek en klik vervolgens op **[!UICONTROL My Preferences]**. Het venster **[!UICONTROL User Preferences]** wordt geopend.

1. Selecteer gewenste **[!UICONTROL Stock Configuration]** van de dropdown lijst en klik **[!UICONTROL Accept]** om de configuratie te activeren.

   ![gebruikersvoorkeuren](assets/aem-stock-preferences.png)

1. Ga naar **[!UICONTROL Assets]** > **[!UICONTROL Adobe Stock]**. U kunt nu [!DNL Adobe Stock]-middelen weergeven, zoeken en licentiëren.

In de volgende tabel wordt uitgelegd hoe de gebruikersmachtigingen werken wanneer de elementen [!DNL Adobe Stock] worden geopend:

| Gebruiker | Groeperen | Machtigingen | Stock-configuratie accepteren in de gebruikersvoorkeuren | Toegangsmiddelen | Toegang tot Adobe Stock |
| --- | --- | --- | --- | --- | --- |
| beheerder | N.v.t. | Alles | N.v.t. | Ja | Ja |
| test-doc1 | DAM-gebruiker | `/conf/global/settings/stock/cloud-config` | Ja | Ja | Ja |
| test-doc1 | DAM-gebruiker | `/conf/global/settings/stock/cloud-config` | Nee | Fout: Kan gegevens niet laden | Nee |
| test-doc1 | DAM-gebruiker | toestaan: `/conf/global/settings/stock` ontkennen: `/cloud-config` | De voorraadconfiguratie is niet zichtbaar | Ja | Nee |


## [!DNL Adobe Stock]-elementen gebruiken en beheren in [!DNL Experience Manager] {#usemanage}

Met behulp van deze mogelijkheid kunnen organisaties hun gebruikers toestaan te werken met [!DNL Adobe Stock] middelen in [!DNL Experience Manager Assets]. Vanuit de [!DNL Experience Manager]-gebruikersinterface kunnen gebruikers zoeken in [!DNL Adobe Stock]-middelen en een licentie voor de vereiste middelen aanschaffen.

Zodra een [!DNL Adobe Stock] element in [!DNL Experience Manager] vergunning wordt gegeven, kan het als typisch activa worden gebruikt en worden beheerd. In [!DNL Experience Manager] kunnen de gebruikers de elementen zoeken en voorvertonen; de elementen kopiëren en publiceren; delen van de activa op [!DNL Brand Portal]; toegang tot en gebruik de middelen via [!DNL Experience Manager] desktop app; enzovoort.

![Zoeken naar  [!DNL Adobe Stock] elementen en filterresultaten vanuit uw  [!DNL Adobe Experience Manager] werkruimte](assets/adobe-stock-search-results-workspace.png)

**A.Elementen** zoeken die vergelijkbaar zijn met de elementen waarvan de  [!DNL Adobe Stock] id is opgegeven. **B.** Zoek naar assets die overeenkomen met de vorm of afdrukstand die u hebt geselecteerd. **C.** Zoeken naar een of meer ondersteunde elementtypen  **D.** Het deelvenster  **E.** Licentie openen of samenvouwen en het geselecteerde element opslaan in  [!DNL Experience Manager] **F.** Het element opslaan in  [!DNL Experience Manager] het watermerk  **G.**   [!DNL Adobe Stock]   ****   [!DNL Adobe Stock]   ****   **** Elementen op de website ontdekken die vergelijkbaar zijn met het geselecteerde element.H.De geselecteerde middelen op de websiteI.ZoekresultatenAantal geselecteerde middelen op J.Switch tussen de kaartweergave en de lijstweergave

### Elementen zoeken {#find-assets}

Uw [!DNL Experience Manager] gebruikers, kunnen activa in zowel [!DNL Experience Manager] als [!DNL Adobe Stock] zoeken. Wanneer de zoeklocatie niet beperkt is tot [!DNL Adobe Stock], worden de zoekresultaten van [!DNL Experience Manager] en [!DNL Adobe Stock] weergegeven.

* Als u naar [!DNL Adobe Stock] elementen wilt zoeken, klikt u op **[!UICONTROL Navigation]** > **[!UICONTROL Assets]** > **[!UICONTROL Search Adobe Stock]**.

* Als u wilt zoeken naar elementen in [!DNL Adobe Stock] en [!DNL Experience Manager Assets], klikt u op Zoeken ![search](assets/do-not-localize/search_icon.png).

U kunt ook `Location: Adobe Stock` in de zoekbalk typen om [!DNL Adobe Stock] elementen te selecteren. [!DNL Experience Manager] biedt geavanceerde filtermogelijkheden voor de gezochte middelen, die gebruikers toestaan om op de vereiste activa snel nul-binnen op de filters te gebruiken, zoals types van gesteunde activa, beeldrichtlijn, en vergunning gegeven staat.

>[!NOTE]
>
>Elementen die worden doorzocht vanuit [!DNL Adobe Stock], worden weergegeven in [!DNL Experience Manager]. [!DNL Adobe Stock] elementen worden pas opgehaald en opgeslagen in de  [!DNL Experience Manager] opslagplaats nadat een gebruiker een  [assetor-](/help/assets/aem-assets-adobe-stock.md#saveassets) licentie  [heeft opgeslagen en een middel](/help/assets/aem-assets-adobe-stock.md#licenseassets) heeft opgeslagen. Elementen die al zijn opgeslagen in [!DNL Experience Manager] worden weergegeven en gemarkeerd voor eenvoudige referentie en toegang. Bovendien worden de [!DNL Stock]-elementen met extra metagegevens opgeslagen om de bron aan te geven als [!DNL Stock].

![Filters zoeken in  [!DNL Experience Manager] en gemarkeerde  [!DNL Adobe Stock] elementen in zoekresultaten](assets/aem-search-filters2.jpg)

### De vereiste elementen opslaan en weergeven {#saveassets}

Selecteer een middel dat u in [!DNL Experience Manager] wilt bewaren. Klik [!UICONTROL Save] in de toolbar bij de bovenkant en verstrek de naam en de plaats van de activa. De elementen zonder licentie worden lokaal met een watermerk opgeslagen.

De volgende keer dat u naar elementen zoekt, worden de opgeslagen elementen gemarkeerd met een badge om aan te geven dat dergelijke elementen beschikbaar zijn in [!DNL Experience Manager Assets].

>[!NOTE]
>
>De onlangs toegevoegde elementen geven een nieuwe badge weer in plaats van een badge met licentie.

### Licentie-elementen {#licenseassets}

Gebruikers kunnen [!DNL Adobe Stock]-middelen in licentie geven door gebruik te maken van de quota van hun [!DNL Adobe Stock]-ondernemingsplan. Wanneer u een licentie voor een element aanschaft, wordt het zonder watermerk opgeslagen en is het beschikbaar voor zoeken en gebruiken in [!DNL Experience Manager Assets].

![Dialoogvenster voor het in licentie geven en opslaan van  [!DNL Adobe Stock] middelen in  [!DNL Experience Manager Assets]](assets/aem-stock_licenseandsave.jpg)


### Metagegevens en elementen openen {#access-metadata-and-asset-properties}

Gebruikers kunnen de metagegevens openen en voorvertonen, inclusief de metagegevenseigenschappen [!DNL Adobe Stock] voor de elementen die zijn opgeslagen in [!DNL Experience Manager], en **[!UICONTROL License References]** toevoegen voor een element. De updates voor de licentieverwijzing worden echter niet gesynchroniseerd tussen [!DNL Experience Manager]- en [!DNL Adobe Stock]-website.

Gebruikers kunnen de eigenschappen van zowel gelicentieerde als niet-gelicentieerde activa zien.

![Metagegevens en licentieverwijzingen van opgeslagen elementen weergeven en openen](assets/metadata_properties.jpg)


## Bekende beperkingen {#known-limitations}

* **Problemen in integratie met  [!DNL Experience Manager] Service Pack 6.5.7.0 en hoger**: Tijdens de integratie met  [!DNL Experience Manager] 6.5.7.0 en hoger is een onverwacht probleem geïdentificeerd. Het probleem wordt momenteel getest en zal naar verwachting beschikbaar zijn in [!DNL Experience Manager] 6.5.11.0. Neem contact op met [!DNL Customer Support] voor een directe hotfix.

* **De functionaliteit om gebruikers te beperken tot het verlenen van licenties werkt niet correct**: Alle gebruikers met  `read` machtigingen voor de voorraadconfiguratie mogen de  [!DNL Adobe Stock] elementen doorzoeken en een licentie geven.

* **Gebruikers die geen beheerder zijn, moeten de  [!DNL Adobe Stock] cloudconfiguratie** handmatig activeren: In het  **[!UICONTROL User Preferences]** venster  **[!UICONTROL Stock Configuration]** ziet u de ingeschakelde  [!DNL Adobe Stock] cloudconfiguratie, maar deze werkt niet voor gebruikers die geen beheerder zijn. De gebruiker moet op **[!UICONTROL Accept]** knoop klikken om de configuratie van de Voorraad te activeren. Als deze stap ontbreekt, weerspiegelt het systeem een foutenmelding bij de toegang tot van **[!UICONTROL Assets]**.

* **Waarschuwing voor redactionele afbeelding wordt niet weergegeven**: Wanneer gebruikers een licentie voor een afbeelding verlenen, kunnen ze niet controleren of een afbeelding alleen voor gebruik als redactie is. Om mogelijk misbruik te voorkomen, kunnen de beheerders de toegang tot redactionele activa van de Admin Console uitschakelen.

* **Er wordt een onjuist licentietype weergegeven**: Het is mogelijk dat een onjuist licentietype wordt weergegeven  [!DNL Experience Manager] voor een element. Gebruikers kunnen zich aanmelden bij de [!DNL Adobe Stock]-website om het type licentie te zien.

* **Referentievelden en metagegevens worden niet gesynchroniseerd**: Wanneer een gebruiker een veld met een licentieverwijzing bijwerkt, wordt de informatie over de licentieverwijzing bijgewerkt in  [!DNL Experience Manager] maar niet op de  [!DNL Adobe Stock] website. Als de gebruiker de referentievelden op de [!DNL Adobe Stock]-website bijwerkt, worden de updates niet gesynchroniseerd in [!DNL Experience Manager].

>[!MORELIKETHIS]
>
>* [Videozelfstudie over het  [!DNL Adobe Stock] gebruik van middelen met [!DNL Experience Manager Assets]](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/creative-workflows/adobe-stock.html)
>* [[!DNL Adobe Stock] Help bij bedrijfsplan](https://helpx.adobe.com/enterprise/using/adobe-stock-enterprise.html)
>* [[!DNL Adobe Stock] Veelgestelde vragen](https://helpx.adobe.com/stock/faq.html)



<!--old content

### Create an IMS configuration {#create-an-ims-configuration}

1. In the [!DNL Experience Manager] user interface, navigate to **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Adobe IMS Configurations]**. Click **[!UICONTROL Create]** and select **[!UICONTROL Cloud Solution]** > **[!UICONTROL Adobe Stock]**.
1. Either reuse an existing certificate or select **[!UICONTROL Create new certificate]**.
1. Click **[!UICONTROL Create certificate]**. Once created, download the public key. Click **[!UICONTROL Next]**. Leave the [!UICONTROL Adobe IMS Technical Account Configuration] screen open to provide the required values shortly.
1. Access [Adobe Developer Console](https://console.adobe.io). Ensure that your account has administrator permissions for the organization for which the integration is required.
1. Click **[!UICONTROL Create new project]** and click **[!UICONTROL Add API]**. Select **[!UICONTROL Adobe Stock]** from the list of APIs that are available to you. Select [!UICONTROL OAUTH 2.0 Web].
1. Provide **[!UICONTROL Default redirect URI]** and **[!UICONTROL Redirect URI pattern]** values. Click **[!UICONTROL Save configured API]**. Copy the generated ID and secret.
1. In [!UICONTROL Adobe IMS Technical Account Configuration] screen, provide the values in the boxes titled **[!UICONTROL Title]**, **[!UICONTROL Authorization Server]**, **[!UICONTROL API Key]**, **[!UICONTROL Client Secret]**, and **[!UICONTROL Payload]**. For detailed information about these values, see [JWT authentication quick start](https://www.adobe.io/authentication/auth-methods.html#!AdobeDocs/adobeio-auth/master/JWT/JWT.md).

-->

<!-- TBD: Update the URL to update the terminology when AIO team updates their documentation URL. Logged issue github.com/AdobeDocs/adobeio-auth/issues/63.
-->

<!--
### Create [!DNL Adobe Stock] configuration in [!DNL Experience Manager] {#create-adobe-stock-configuration-in-aem}

1. In the [!DNL Experience Manager], navigate to **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Adobe Stock]**.
1. Click **[!UICONTROL Create]** to create a configuration and associate it with your existing IMS Configuration. Select `PROD` as the environment parameter.
1. In **[!UICONTROL Licensed Assets Path]** field, leave a location as is. Do not change the location where you want to store the [!DNL Adobe Stock] assets.
1. Complete creation by adding all the required properties. Click **[!UICONTROL Save & Close]**.
1. Add [!DNL Experience Manager] users or groups, who can license the assets.

>[!NOTE]
>
>If there are multiple [!DNL Adobe Stock] configurations, select the desired configuration in [!UICONTROL User Preferences] panel. To access the panel from [!DNL Experience Manager] home page, click the user icon and then click **[!UICONTROL User Preferences]** > **[!UICONTROL Stock Configuration]**.

-->