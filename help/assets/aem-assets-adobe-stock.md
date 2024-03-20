---
title: Beheren [!DNL Adobe Stock] elementen
description: Zoeken, ophalen, licentie en beheren [!DNL Adobe Stock] activa van binnen [!DNL Adobe Experience Manager]. Gebruik de in licentie gegeven activa als elk ander digitaal actief.
contentOwner: Vishabh Gupta
feature: Search, Adobe Stock
role: User, Admin
exl-id: 8ec597df-bb64-4768-bf9c-e8cca4fea25b
hide: true
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '2291'
ht-degree: 2%

---

# Gebruiken [!DNL Adobe Stock] activa in [!DNL Adobe Experience Manager Assets] {#use-adobe-stock-assets-in-aem-assets}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/aem-assets-adobe-stock.html?lang=en) |
| AEM 6,5 | Dit artikel |

<!-- old content

[!DNL Experience Manager Assets] provides users the ability to search, preview, save, and license [!DNL Adobe Stock] assets directly from [!DNL Experience Manager]. 

Organizations can integrate their [!DNL Adobe Stock] enterprise plan with [!DNL Experience Manager Assets] to ensure that licensed assets are broadly available for their creative and marketing projects, with the powerful asset management capabilities of [!DNL Experience Manager].

[!DNL Adobe Stock] service provides designers and businesses with access to millions of high-quality, curated, royalty-free photos, vectors, illustrations, videos, templates, and 3D assets for all their creative projects. [!DNL Experience Manager] users are able to quickly find, preview, and license [!DNL Adobe Stock] assets that are saved in [!DNL Experience Manager], without leaving the [!DNL Experience Manager] interface.
-->

<!-- New overview content
-->

[!DNL Adobe Stock] biedt ontwerpers en bedrijven toegang tot miljoenen hoogwaardige, gekrulde, royaltyvrije foto&#39;s, vectoren, illustraties, video&#39;s, sjablonen en 3D-middelen voor al hun creatieve projecten.

[!DNL Adobe Stock] voor het aanbieden van een bedrijf, door gebrek, omvat het delen van rechten over de organisatie. Zodra een middel door een gebruiker van uw organisatie is vergunning gegeven, kunnen andere gebruikers van uw organisatie, dit middel identificeren downloaden en gebruiken zonder het moeten het opnieuw vergunning geven. Zodra een activa door uw organisatie zijn vergunning gegeven, is het recht om het te gebruiken onvoorwaardelijk.

Organisaties kunnen hun bedrijf integreren [!DNL Adobe Stock] plannen met [!DNL Experience Manager Assets] om ervoor te zorgen dat gelicentieerde middelen breed beschikbaar zijn voor hun creatieve en marketingprojecten, met de krachtige mogelijkheden voor middelenbeheer van [!DNL Experience Manager]. [!DNL Experience Manager] gebruikers kunnen snel Adobe Stock-middelen zoeken, voorvertonen en licentiëren die zijn opgeslagen in [!DNL Experience Manager], zonder de [!DNL Experience Manager] interface.

<!-- Old content
## Prerequisites {#prerequisites}

The integration requires an [enterprise [!DNL Adobe Stock] plan](https://stockenterprise.adobe.com/).
-->

## Integreren [!DNL Experience Manager] en [!DNL Adobe Stock] {#integrate-aem-and-adobe-stock}

[!DNL Experience Manager Assets] biedt gebruikers de mogelijkheid te zoeken, een voorbeeld te bekijken, op te slaan en een licentie te maken [!DNL Adobe Stock] activa rechtstreeks van [!DNL Experience Manager].

**Vereisten**

De integratie vereist:

* An [bedrijf [!DNL Adobe Stock] plan](https://stockenterprise.adobe.com/)
* Een gebruiker met machtigingen in Admin Console naar het standaardprofiel voor het product Stock
* Een gebruiker met machtigingen voor het Developer Access-profiel voor het maken van integratie in Adobe Developer Console

Een onderneming [!DNL Adobe Stock] plan,

* Biedt productrechten voor [!DNL Adobe Stock] (Met Experience Manager verbonden voorraden)
* Crediteringen die zijn aangeschaft in de [!DNL Adobe Admin Console] voor je aandelenrecht
* Maakt verificatie voor serviceaccount (JWT) binnen mogelijk [!DNL Adobe Developer Console] voor je aandelenrecht
* Maakt het beheer van de credits en licenties wereldwijd mogelijk vanuit de [!DNL Adobe Admin Console]

Binnen de machtiging wordt een standaardproductprofiel voor [!DNL Adobe Stock] bestaat in [!DNL Admin Console]. Er kunnen meerdere profielen worden gemaakt en deze profielen bepalen wie een licentie voor de activa van Stock kan verkrijgen. Een gebruiker die rechtstreeks toegang heeft tot het productprofiel heeft toegang tot [https://stock.adobe.com/](https://stock.adobe.com/) en de activa van de vergunning van de Voorraad. Terwijl er een andere methode is om de toegang van de Ontwikkelaar te gebruiken om integratie (API) tot stand te brengen voor authentiek communicatie tussen [!DNL Experience Manager] en [!DNL Adobe Stock].

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

## Stappen om te integreren [!DNL Experience Manager] en [!DNL Adobe Stock] {#integration-steps}

Om te integreren [!DNL Experience Manager] en [!DNL Adobe Stock]voert u de volgende stappen uit in de vermelde reeks:

1. [Openbaar certificaat verkrijgen](#public-certificate)

   In [!DNL Experience Manager], maakt u een IMS-account en genereert u een openbaar certificaat (openbare sleutel).

1. [Verbinding voor serviceaccount (JWT) maken](#createnewintegration)

   In [!DNL Adobe Developer Console], maakt u een project voor uw [!DNL Adobe Stock] organisatie. Onder het project, vorm API gebruikend de openbare sleutel om een verbinding van de de dienstrekening (JWT) tot stand te brengen. Krijg de geloofsbrieven van de de dienstrekening en JWT payload informatie.

1. [IMS-account configureren](#create-ims-account-configuration)

   In [!DNL Experience Manager], configureert u de IMS-account met de gegevens van de serviceaccount en de JWT-payload.

1. [Cloudservice configureren](#configure-the-cloud-service)

   In [!DNL Experience Manager], een [!DNL Adobe Stock] cloudservice met behulp van het IMS-account.


### Een IMS-configuratie maken {#create-an-ims-configuration}

De configuratie IMS verifieert uw [!DNL Experience Manager Assets] auteur instantie met [!DNL Adobe Stock] machtiging.

De IMS-configuratie omvat twee stappen:

* [Openbaar certificaat verkrijgen](#public-certificate)
* [IMS-account configureren](#create-ims-account-configuration)

### Openbaar certificaat verkrijgen {#public-certificate}

Met de openbare sleutel (certificaat) wordt uw productprofiel geverifieerd in Adobe Developer Console.

1. Aanmelden bij uw [!DNL Experience Manager Assets] instantie van auteur. De standaard-URL is `http://localhost:4502/aem/start.html`.

1. Van de **[!UICONTROL Tools]** deelvenster, navigeren naar **[!UICONTROL Security]** > **[!UICONTROL Adobe IMS Configurations]**.

1. Klik op de pagina Adobe IMS Configurations op **[!UICONTROL Create]**. De **[!UICONTROL Adobe IMS Technical Account Configuration]** pagina wordt geopend.

1. In de **[!UICONTROL Certificate]** tab, selecteert u **[!UICONTROL Adobe Stock]** van de **[!UICONTROL Cloud Solution]** vervolgkeuzelijst.

1. U kunt een certificaat maken of een bestaand certificaat opnieuw gebruiken voor de configuratie.

   Als u een certificaat wilt maken, selecteert u de **[!UICONTROL Create new certificate]** selectievakje en geef een **alias** voor de openbare sleutel. De alias fungeert als naam voor de openbare sleutel.

1. Klik op **[!UICONTROL Create certificate]**. Klik vervolgens op **[!UICONTROL OK]** om de openbare sleutel te produceren.

1. Klik op de knop **[!UICONTROL Download Public Key]** en sla het bestand met de openbare sleutel (.crt) op uw computer op. De openbare sleutel wordt later gebruikt om API voor uw Brand Portal huurder te vormen en de geloofsbrieven van de de dienstrekening in de Console van Adobe Developer te produceren.

   Klik op **[!UICONTROL Next]**.

   ![certificaat genereren](assets/stock-integration-ims-account.png)

1. In de **Account** wordt een Adobe IMS-account gemaakt waarvoor de gegevens van de serviceaccount zijn vereist.

   Open een nieuw tabblad en [een JWT-verbinding (Service Account) maken in Adobe Developer Console](#createnewintegration).

### Verbinding voor serviceaccount (JWT) maken {#createnewintegration}

In Adobe Developer Console, worden de projecten en APIs gevormd op organisatieniveau. Als u een API configureert, wordt een JWT-verbinding (Service Account) gemaakt. Er zijn twee methodes om API te vormen, door een zeer belangrijk paar (privé en openbare sleutels) te produceren of door een openbare sleutel te uploaden. In dit voorbeeld worden de gegevens van de serviceaccount gegenereerd door de openbare sleutel te uploaden.

Om de geloofsbrieven van de de dienstrekening en JWT lading te produceren:

1. Meld u aan bij de Adobe Developer-console met systeembeheerdersrechten. De standaard-URL is [https://www.adobe.com/go/devs_console_ui](https://www.adobe.com/go/devs_console_ui).


   Controleer of u de juiste IMS-organisatie (Stock Entitlement) hebt geselecteerd in de vervolgkeuzelijst (organisatie).

1. Klik op **[!UICONTROL Create new project]**. Er wordt een leeg project met een door het systeem gegenereerde naam gemaakt voor uw organisatie.

   Klik op **[!UICONTROL Edit project]**. Werk de **[!UICONTROL Project Title]** en **[!UICONTROL Description]** en klik vervolgens op **[!UICONTROL Save]**.

1. In de **[!UICONTROL Project overview]** tabblad, klikt u op **[!UICONTROL Add API]**.

1. In de **[!UICONTROL Add an API window]**, selecteert u **[!UICONTROL Adobe Stock]**. Klik op **[!UICONTROL Next]**.

1. In de **[!UICONTROL Configure API]** venster, selecteert u **[!UICONTROL Service Account (JWT)]** verificatie. Klik op **[!UICONTROL Next]**.

   ![create-jwt-credentials](assets/aem-stock-jwt.png)

1. Klik op **[!UICONTROL Upload your public key]**. Klikken **[!UICONTROL Select a File]** en uploadt u de openbare sleutel (.crt-bestand) die u in het dialoogvenster [openbare verklaring verkrijgen](#public-certificate) sectie. Klik op **[!UICONTROL Next]**.

1. De openbare sleutel controleren en klikken **[!UICONTROL Next]**.

1. De standaardinstelling selecteren **[!UICONTROL Adobe Stock]** productprofiel en klik op **[!UICONTROL Save configured API]**.

1. Nadat de API is geconfigureerd, wordt u omgeleid naar de API-overzichtspagina. Vanaf de linkernavigatie onder **[!UICONTROL Credentials]** klikt u op de knop **[!UICONTROL Service Account (JWT)]** -optie. Hier, kunt u de geloofsbrieven bekijken en acties uitvoeren zoals produceren JWT tokens, exemplaar credentiedetails, en terugwinnen cliëntgeheim.

1. Van de **[!UICONTROL Client Credentials]** -tabblad, kopieert u de **[!UICONTROL client ID]**.

   Klikken **[!UICONTROL Retrieve Client Secret]** en kopieer de **[!UICONTROL client secret]**.

   ![generate-jwt-credentials](assets/aem-stock-jwt-credential.png)

1. Ga naar de **[!UICONTROL Generate JWT]** en kopieer de **[!UICONTROL JWT Payload]** informatie.

U kunt nu de client-id (API-sleutel), het clientgeheim en de JWT-payload gebruiken naar [IMS-account configureren](#create-ims-account-configuration) in [!DNL Experience Manager Assets].

### IMS-account configureren {#create-ims-account-configuration}

U moet beschikken over [certificaat](#public-certificate) en [JWT-referenties (Service Account)](#createnewintegration) om de IMS-account te configureren.

De IMS-account configureren:

1. Open de IMS-configuratie en navigeer naar de **[!UICONTROL Account]** tab. U hebt de pagina geopend gehouden terwijl [verkrijgen van het openbare certificaat](#public-certificate).

1. Geef een **[!UICONTROL Title]** op voor het IMS-account.

   In de **[!UICONTROL Authorization Server]** veld, voer de URL in: [https://ims-na1.adobelogin.com/](https://ims-na1.adobelogin.com/).

   Voer de client-id in het dialoogvenster **[!UICONTROL API key]** veld, **[!UICONTROL Client Secret]**, en **[!UICONTROL Payload]** (JWT-lading) die u hebt gekopieerd terwijl [maken van de verbinding van de serviceaccount (JWT)](#createnewintegration).

1. Klik op **[!UICONTROL Create]**. Er wordt een IMS-accountconfiguratie gemaakt.

   ![configure-ims-account](assets/aem-stock-ims-config.png)

1. Selecteer de IMS-accountconfiguratie en klik op **[!UICONTROL Check Health]**.

   Klikken **[!UICONTROL Check]** in het dialoogvenster. Bij een geslaagde configuratie verschijnt het bericht dat de *Token is opgehaald*.

   ![gezondheidscontrole](assets/aem-stock-healthcheck.png)


### Cloudservice configureren {#configure-the-cloud-service}

Om te vormen [!DNL Adobe Stock] cloudservice:

1. In de [!DNL Experience Manager] gebruikersinterface, navigeren naar **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Adobe Stock]**.

1. In de [!DNL Adobe Stock Configurations] pagina, klikt u **[!UICONTROL Create]**.

1. Geef een **[!UICONTROL Title]** voor de cloudconfiguratie.

   Selecteer de IMS-configuratie die u hebt gemaakt terwijl u [configureren van IMS-account](#create-ims-account-configuration).

   Selecteer de landinstelling in de vervolgkeuzelijst.

   ![aem-stock-cloud-config](assets/aem-stock-cloud-config.png)

1. Klik op **[!UICONTROL Save & Close]**.

   Uw [!DNL Experience Manager Assets] schrijverinstantie is nu geïntegreerd met [!DNL Adobe Stock]. U kunt meerdere [!DNL Adobe Stock] configuraties (bijvoorbeeld configuraties op basis van landinstellingen). U kunt nu de opdracht [!DNL Adobe Stock] activa van binnen [!DNL Experience Manager] gebruikersinterface.

   ![zoekmiddelen](assets/aem-stock-searchstocks.png)

   >[!NOTE]
   >
   >In deze fase van integratie hebben alleen de beheerders toegang tot de [!DNL Adobe Stock] activa, activa van de onderzoeksVoorraad (gebruikend alwetzoekend), en vergunning het [!DNL Adobe Stock] activa.
   >
   >Beheerders kunnen gebruikers of groepen verder toevoegen aan de [!DNL Adobe Stock] cloudservice en geef machtigingen aan deze gebruikers die geen beheerder zijn in [!DNL Experience Manager] om tot de configuratie van de Voorraad toegang te hebben.

1. Als u gebruikers of groepen wilt toevoegen, selecteert u de [!DNL Adobe Stock] cloudconfiguratie en klik op **[!UICONTROL Properties]**.

1. Zoek om de gebruikers of de groepen toe te voegen aan wie u toestemmingen hebt toegewezen om tot de configuratie van Adobe Stock toegang te hebben. Zie [machtigingen toewijzen aan gebruikersgroep](#assign-permissions-to-group).


## Machtigingen toewijzen aan gebruikersgroep {#assign-permissions-to-group}

Beheerders kunnen gebruikersgroepen maken en bepaalde gebruikers of groepen machtigingen geven om toegang te krijgen tot de [!DNL Adobe Stock] cloudservice.

Hieronder vindt u de machtigingen die een gebruiker nodig heeft om Adobe Stock-middelen te zoeken en te licentiëren:

* Vorm de weg: `/conf/global/settings/stock`
* Rechten: `jcr:read`
* Type machtiging: `Allow`

U kunt een gebruikersgroep maken of machtigingen toewijzen aan een bestaande gebruikersgroep. Machtigingen kunnen worden toegewezen via de [!DNL Experience Manager Assets] of van de [!DNL User Admin] Console.

**Om toegang tot een gebruikersgroep van te verlenen [!DNL Experience Manager]:**

1. In de [!DNL Experience Manager] gebruikersinterface, navigeren naar **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Groups]**. Een gebruikersgroep maken voor [!DNL Adobe Stock].

1. Navigeren naar **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Permissions]**.

1. Zoeken naar de gebruikersgroep in het linkerdeelvenster en nieuwe gebruikersgroep toevoegen **[!UICONTROL Access Control Entry (ACE)]** voor Adobe Stock.

   * Vorm de weg: `/conf/global/settings/stock`
   * Rechten: `jcr:read`
   * Type machtiging: `Allow`

   Klik op **[!UICONTROL Add]**.

   ![gebruikersmachtigingen](assets/aem-stock-user-permissions.png)

1. Ga naar **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Adobe Stock]**. Selecteer de [!DNL Adobe Stock] cloudconfiguratie en klik op **[!UICONTROL Properties]**.

1. De nieuwe gebruikersgroep toevoegen aan de [!DNL Adobe Stock] configuratie. Klik op **[!UICONTROL Save & Close]**.

   ![assign-user](assets/aem-stock-adduser.png)

**Om toegang tot een gebruiker van te verlenen [!DNL User Admin Console]:**

1. Open de [!DNL Experience Manager] Admin Console gebruiker. De standaard-URL is `http://localhost:4502/userdamin`.

1. Zoek in het linkerdeelvenster naar de gebruiker door het dialoogvenster `user_id` of `name`. Dubbelklik om de gebruikerseigenschappen te openen.

1. Ga naar de **[!UICONTROL Permissions]** tab en allow `read` machtigingen voor de [!DNL Adobe Stock] cloudconfiguratie: `/conf/global/settings/stock`.

   >[!CAUTION]
   >
   >Als de wolkenconfiguratie niet wordt toegestaan, kan de gebruiker slechts tot **[!UICONTROL Assets]** in de [!DNL Experience Manager] interface.
   >
   >Toegang verlenen tot [!UICONTROL Assets] en [!DNL Adobe Stock] middelen, zorgt u ervoor dat de cloudconfiguratie is toegestaan voor de gebruiker.

1. Klikken **[!UICONTROL Save]** om de machtigingen bij te werken.

   ![assign-user-in-user-admin](assets/aem-stock-user-admin-console.png)

1. Voeg de gebruiker of de groep toe aan de [!DNL Adobe Stock] cloudconfiguratie.


## Adobe Stock-middelen openen {#access-stock-assets}

Een gebruiker die geen beheerder is en over machtigingen beschikt voor de [!DNL Adobe Stock] de wolkenconfiguratie kan zoeken en vergunning geven [!DNL Adobe Stock] activa van de [!DNL Experience Manager] interface.

De gebruiker moet een extra stap uitvoeren om het [!DNL Adobe Stock] cloudconfiguratie voor toegang tot [!DNL Adobe Stock] activa. Het is een eenmalige activiteit. Als aan de gebruiker machtigingen worden toegewezen voor meerdere [!DNL Adobe Stock] wolkenconfiguraties, kan de gebruiker de gewenste configuratie van de **[!UICONTROL User Preferences]**.

Als u het dialoogvenster [!DNL Adobe Stock] cloudconfiguratie:

1. Aanmelden bij [!DNL Experience Manager].

1. Klik op het gebruikerspictogram in de rechterbovenhoek en klik vervolgens op **[!UICONTROL My Preferences]**. De **[!UICONTROL User Preferences]** wordt geopend.

1. Selecteer het gewenste **[!UICONTROL Stock Configuration]** in de vervolgkeuzelijst en klik op **[!UICONTROL Accept]** de configuratie activeren.

   ![gebruikersvoorkeuren](assets/aem-stock-preferences.png)

1. Navigeren naar **[!UICONTROL Assets]** > **[!UICONTROL Adobe Stock]**. U kunt nu een licentie bekijken, zoeken en licentiëren [!DNL Adobe Stock] activa.

In de volgende tabel wordt uitgelegd hoe de gebruikersmachtigingen werken bij het openen van de [!DNL Adobe Stock] activa:

| Gebruiker | Groep | Machtigingen | Stock-configuratie accepteren in de gebruikersvoorkeuren | Toegangsmiddelen | Toegang tot Adobe Stock |
| --- | --- | --- | --- | --- | --- |
| admin | NVT | Alles | NVT | Ja | Ja |
| test-doc1 | DAM-gebruiker | /conf/global/settings/stock/cloud-config | Ja | Ja | Ja |
| test-doc1 | DAM-gebruiker | /conf/global/settings/stock/cloud-config | Nee | Fout: kan gegevens niet laden | Nee |
| test-doc1 | DAM-gebruiker | **toestaan**: /conf/global/settings/stock     **ontkennen**: /cloud-config | De voorraadconfiguratie is niet zichtbaar | Ja | Nee |


## Gebruiken en beheren [!DNL Adobe Stock] activa in [!DNL Experience Manager] {#usemanage}

Met behulp van deze mogelijkheid kunnen organisaties hun gebruikers toestaan te werken met [!DNL Adobe Stock] activa in [!DNL Experience Manager Assets]. Van binnen [!DNL Experience Manager] gebruikersinterface, gebruikers kunnen zoeken [!DNL Adobe Stock] activa en de vereiste activa in licentie geven.

Eenmaal [!DNL Adobe Stock] actief in licentie gegeven [!DNL Experience Manager], kan het als typisch activa worden gebruikt en worden beheerd. In [!DNL Experience Manager], kunnen de gebruikers de elementen zoeken en voorvertonen, de elementen kopiëren en publiceren, de elementen delen op [!DNL Brand Portal]; toegang tot en gebruik van de activa door [!DNL Experience Manager] bureaubladtoepassing, enzovoort.

![Zoeken naar [!DNL Adobe Stock] elementen en filterresultaten van uw [!DNL Adobe Experience Manager] werkruimte](assets/adobe-stock-search-results-workspace.png)

**A.** Zoeken naar elementen die vergelijkbaar zijn met de elementen waarvan [!DNL Adobe Stock] ID is opgegeven. **B.** Zoek naar assets die overeenkomen met de vorm of afdrukstand die u hebt geselecteerd. **C.** Een of meer ondersteunde elementtypen zoeken **D.** Het venster Filters openen of samenvouwen **E.** Licentie toewijzen en het geselecteerde element opslaan in [!DNL Experience Manager] **F.** Middel opslaan in [!DNL Experience Manager] met watermerk **G.** Middelen verkennen op [!DNL Adobe Stock] website die vergelijkbaar is met het geselecteerde element **H.** Geselecteerde elementen weergeven op [!DNL Adobe Stock] website **I.** Aantal geselecteerde elementen uit de zoekresultaten **J.** Schakelen tussen de kaartweergave en de lijstweergave

### Elementen zoeken {#find-assets}

Uw [!DNL Experience Manager] gebruikers, naar elementen in beide kunnen zoeken, [!DNL Experience Manager] en [!DNL Adobe Stock]. Wanneer de zoeklocatie niet beperkt is tot [!DNL Adobe Stock], de zoekresultaten van [!DNL Experience Manager] en [!DNL Adobe Stock] worden weergegeven.

* Als u wilt zoeken naar [!DNL Adobe Stock] elementen, klik op **[!UICONTROL Navigation]** > **[!UICONTROL Assets]** > **[!UICONTROL Search Adobe Stock]**.

* Zoeken naar elementen over [!DNL Adobe Stock] en [!DNL Experience Manager Assets], klikt u op Zoeken ![zoeken](assets/do-not-localize/search_icon.png).

U kunt ook beginnen met typen `Location: Adobe Stock` in de zoekbalk om [!DNL Adobe Stock] activa. [!DNL Experience Manager] biedt geavanceerde filtermogelijkheden voor de gezochte middelen, die gebruikers toestaan om op de vereiste activa snel nul-binnen op de filters te gebruiken, zoals types van gesteunde activa, beeldrichtlijn, en vergunning gegeven staat.

>[!NOTE]
>
>Middelen die zijn doorzocht van [!DNL Adobe Stock] worden weergegeven in [!DNL Experience Manager]. [!DNL Adobe Stock] elementen worden opgehaald en opgeslagen in [!DNL Experience Manager] alleen na een gebruiker [een element opslaan](/help/assets/aem-assets-adobe-stock.md#saveassets) of [licenties en slaat een middel op](/help/assets/aem-assets-adobe-stock.md#licenseassets). Elementen die al zijn opgeslagen in [!DNL Experience Manager] worden weergegeven en gemarkeerd voor eenvoudige referentie en toegang. Ook de [!DNL Stock] elementen worden met enkele aanvullende metagegevens opgeslagen om de bron aan te geven als [!DNL Stock].

![Filters zoeken in [!DNL Experience Manager] en gemarkeerd [!DNL Adobe Stock] elementen in zoekresultaten](assets/aem-search-filters2.jpg)

### De vereiste elementen opslaan en weergeven {#saveassets}

Selecteer een middel waarin u wilt opslaan [!DNL Experience Manager]. Klikken [!UICONTROL Save] in de werkbalk bovenaan en geef de naam en locatie van het element op. De elementen zonder licentie worden lokaal met een watermerk opgeslagen.

De volgende keer dat u naar elementen zoekt, worden de opgeslagen elementen gemarkeerd met een badge om aan te geven dat dergelijke elementen beschikbaar zijn in [!DNL Experience Manager Assets].

>[!NOTE]
>
>De onlangs toegevoegde elementen geven een nieuwe badge weer in plaats van een badge met licentie.

### Licentie-elementen {#licenseassets}

Gebruikers kunnen licenties [!DNL Adobe Stock] activa door gebruik te maken van het quotum van hun [!DNL Adobe Stock] ondernemingsplan. Wanneer u een licentie voor een element aanschaft, wordt het zonder watermerk opgeslagen en is het beschikbaar voor zoeken en gebruiken in [!DNL Experience Manager Assets].

![Dialoogvenster voor licentie en opslaan [!DNL Adobe Stock] activa in [!DNL Experience Manager Assets]](assets/aem-stock_licenseandsave.jpg)


### Metagegevens en elementen openen {#access-metadata-and-asset-properties}

Gebruikers kunnen de metagegevens openen en voorvertonen, inclusief de [!DNL Adobe Stock] eigenschappen van metagegevens voor de elementen die zijn opgeslagen in [!DNL Experience Manager]en toevoegen **[!UICONTROL License References]** voor een actief. De updates voor de licentieverwijzing worden echter niet gesynchroniseerd tussen [!DNL Experience Manager] en [!DNL Adobe Stock] website.

Gebruikers kunnen de eigenschappen van zowel gelicentieerde als niet-gelicentieerde activa zien.

![Metagegevens en licentieverwijzingen van opgeslagen elementen weergeven en openen](assets/metadata_properties.jpg)


## Bekende beperkingen {#known-limitations}

* **Problemen met integratie met [!DNL Experience Manager] Service Pack 6.5.7.0 en hoger**: Tijdens de integratie met [!DNL Experience Manager] 6.5.7.0 en hoger Het probleem wordt momenteel getest en zal naar verwachting beschikbaar zijn in [!DNL Experience Manager] 6.5.11.0. Contactpersoon [!DNL Customer Support] voor een directe hotfix.

* **Functies om gebruikers te beperken tot het verlenen van licenties werken niet correct**: Alle gebruikers die `read` machtigingen voor de voorraadconfiguratie mogen de [!DNL Adobe Stock] activa.

* **Gebruikers die geen beheerder zijn, moeten het [!DNL Adobe Stock] cloudconfiguratie**: In de **[!UICONTROL User Preferences]** venster, het **[!UICONTROL Stock Configuration]** toont de [!DNL Adobe Stock] cloudconfiguratie is ingeschakeld, maar werkt niet voor gebruikers die geen beheerder zijn. De gebruiker moet op de knop **[!UICONTROL Accept]** om de voorraadconfiguratie te activeren. Als deze stap ontbreekt, geeft het systeem een foutbericht weer over de toegang tot **[!UICONTROL Assets]**.

* **Waarschuwing voor redactionele afbeelding wordt niet weergegeven**: Wanneer gebruikers een licentie voor een afbeelding verlenen, kunnen ze niet controleren of een afbeelding alleen voor gebruik als redactie is. Om mogelijk misbruik te voorkomen, kunnen de beheerders de toegang tot redactionele activa van de Admin Console uitzetten.

* **Onjuist licentietype wordt weergegeven**: Het is mogelijk dat een onjuist licentietype wordt weergegeven in [!DNL Experience Manager] voor een actief. Gebruikers kunnen zich aanmelden bij de [!DNL Adobe Stock] website om het licentietype te zien.

* **Referentievelden en metagegevens zijn niet gesynchroniseerd**: Wanneer een gebruiker een veld met een licentieverwijzing bijwerkt, wordt de informatie over de licentieverwijzing bijgewerkt in [!DNL Experience Manager] maar niet op de [!DNL Adobe Stock] website. Op dezelfde manier als de gebruiker de verwijzingsgebieden op de [!DNL Adobe Stock] website, worden de updates niet gesynchroniseerd in [!DNL Experience Manager].

>[!MORELIKETHIS]
>
>* [Videozelfstudie bij gebruik [!DNL Adobe Stock] activa met [!DNL Experience Manager Assets]](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/creative-workflows/adobe-stock.html)
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

