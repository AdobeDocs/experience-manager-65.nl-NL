---
title: Configuratie Microsoft Dynamics OData
description: Leer gebruiken, integreren, en werken met online en op-gebouw de diensten van de Dynamica van Microsoft door vorm gegevensmodel.
topic-tags: integration
products: SG_EXPERIENCEMANAGER/6.5/FORMS
docset: aem65
feature: Form Data Model
exl-id: 90cc9452-e107-4e57-80a3-f44f0bde132e
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '1195'
ht-degree: 0%

---

# Configuratie Microsoft Dynamics OData{#microsoft-dynamics-odata-configuration}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/integrate/use-form-data-model/ms-dynamics-odata-configuration.html) |
| AEM 6,5 | Dit artikel |

![gegevensintegratie](assets/data-integeration.png)

Microsoft Dynamics is een ERP-software (Customer Relationship Management) en Enterprise Resource Planning (Enterprise Resource Planning) die bedrijfsoplossingen biedt voor het maken en beheren van klantaccounts, contactpersonen, leads, kansen en gevallen. [AEM Forms-gegevensintegratie](../../forms/using/data-integration.md) biedt een OData-cloudserviceconfiguratie om Forms te integreren met zowel de online server als de server voor Microsoft Dynamics op locatie. Hiermee kunt u een formuliergegevensmodel maken op basis van de entiteiten, kenmerken en services die zijn gedefinieerd in de service Microsoft Dynamics. Met het gegevensmodel van het formulier kunt u adaptieve formulieren maken die interageren met de Microsoft Dynamics-server om bedrijfsworkflows mogelijk te maken. Bijvoorbeeld:

* Query Microsoft Dynamics-server voor gegevens en aangepaste formulieren vooraf invullen
* Gegevens naar Microsoft Dynamics schrijven bij het verzenden van aangepaste formulieren
* Gegevens schrijven in Microsoft Dynamics via aangepaste entiteiten die zijn gedefinieerd in het formuliergegevensmodel en omgekeerd

Het AEM Forms-add-on-pakket bevat ook een referentie OData-configuratie waarmee u Microsoft Dynamics snel kunt integreren met AEM Forms.

Wanneer het pakket is geïnstalleerd, zijn de volgende entiteiten en services beschikbaar op uw AEM Forms-exemplaar:

* MS Dynamics OData Cloud Service (OData Service)
* Formuliergegevensmodel met vooraf geconfigureerde Microsoft Dynamics-entiteiten en -services.

De vooraf geconfigureerde entiteiten en services van Microsoft Dynamics in een formuliergegevensmodel zijn alleen beschikbaar in uw AEM Forms-exemplaar als de uitvoermodus voor de AEM-instantie is ingesteld als `samplecontent` (standaard). MS Dynamics OData Cloud Service (OData Service) is ook beschikbaar in andere uitvoeringsmodi. Voor meer informatie bij het vormen van looppaswijzen voor een AEM instantie, zie [Modi uitvoeren](/help/sites-deploying/configure-runmodes.md).

## Vereisten {#prerequisites}

Voordat u begint met het instellen en configureren van Microsoft Dynamics, moet u ervoor zorgen dat:

* De [AEM Forms-invoegtoepassing](../../forms/using/installing-configuring-aem-forms-osgi.md)
* Configured Microsoft Dynamics 365 online of installeerde een exemplaar van een van de volgende Microsoft Dynamics-versies:

   * Microsoft Dynamics 365 on-premisse
   * Microsoft Dynamics 2016 on-premisse

* [Registreerde de toepassing voor de online service Microsoft Dynamics met Microsoft Azure Active Directory](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/walkthrough-register-dynamics-365-app-azure-active-directory). Noteer de waarden voor de client-id (ook toepassings-id genoemd) en het clientgeheim voor de geregistreerde service. Deze waarden worden gebruikt terwijl [configureren van cloudservice voor uw Microsoft Dynamics-service](../../forms/using/ms-dynamics-odata-configuration.md#configure-cloud-service-for-your-microsoft-dynamics-service).

## Reactie-URL instellen voor geregistreerde toepassing Microsoft Dynamics {#set-reply-url-for-registered-microsoft-dynamics-application}

Ga als volgt te werk om de antwoordURL voor geregistreerde Microsoft Dynamics-toepassing in te stellen:

>[!NOTE]
>
>Gebruik deze procedure alleen tijdens de integratie van AEM Forms met de online Microsoft Dynamics-server.

1. Ga naar Microsoft Azure Active Directory-account en voeg de volgende URL voor de configuratie van de cloudservice toe in **URL&#39;s beantwoorden** instellingen voor uw geregistreerde toepassing:

   `https://'[server]:[port]'/libs/fd/fdm/gui/components/admin/fdmcloudservice/createcloudconfigwizard/cloudservices.html`

   ![Azure-directory](assets/azure_directory_new.png)

1. Sla de configuratie op.

## Microsoft Dynamics voor IFD configureren {#configure-microsoft-dynamics-for-ifd}

Microsoft Dynamics gebruikt op basis van claims om externe gebruikers toegang te bieden tot gegevens op de Microsoft Dynamics CRM-server. Om dit toe te laten, doe het volgende om de Dynamica van Microsoft voor Internet-Onder ogen ziet plaatsing (IFD) te vormen en claimmontages te vormen.

>[!NOTE]
>
>Gebruik deze procedure slechts terwijl het integreren van AEM Forms met de server van de Dynamiek van Microsoft op-gebouw.

1. Microsoft Dynamics on-premisse instantie voor IFD configureren, zoals beschreven in [IFD configureren voor Microsoft Dynamics](https://technet.microsoft.com/en-us/library/dn609803.aspx).
1. Stel de volgende bevelen in werking gebruikend Vensters PowerShell om claimmontages op IFD-Toegelaten Dynamiek van Microsoft te vormen:

   ```shell
   Add-PSSnapin Microsoft.Crm.PowerShell
    $ClaimsSettings = Get-CrmSetting -SettingType OAuthClaimsSettings
    $ClaimsSettings.Enabled = $true
    Set-CrmSetting -Setting $ClaimsSettings
   ```

   Zie [Toepassingsregistratie voor CRM op locatie (IFD)](https://msdn.microsoft.com/sl-si/library/dn531010(v=crm.7).aspx#bkmk_ifd) voor meer informatie.

## OAuth-client configureren op AD FS-computer {#configure-oauth-client-on-ad-fs-machine}

Doe het volgende om een cliënt OAuth op de Actieve machine van de Diensten van de Federatie van de Folder (AD FS) te registreren en toegang op de machine van het ADS te verlenen:

>[!NOTE]
>
>Gebruik deze procedure slechts terwijl het integreren van AEM Forms met de server van de Dynamiek van Microsoft op-gebouw.

1. Voer de volgende opdracht uit:

   `Add-AdfsClient -ClientId "<Client-ID>" -Name "<name>" -RedirectUri "<redirect-uri>" -GenerateClientSecret`

   Waarbij:

   * `Client-ID` is een cliëntidentiteitskaart u het gebruiken van om het even welke generator kunt produceren GUID.
   * `redirect-uri` is de URL naar de Microsoft Dynamics OData cloud service op AEM Forms. De standaardcloudservice die wordt geïnstalleerd met het AEM Forms-pakket, wordt geïmplementeerd op de volgende URL:
     `https://'[server]:[port]'/libs/fd/fdm/gui/components/admin/fdmcloudservice/createcloudconfigwizard/cloudservices.html`

1. Voer de volgende opdracht uit om toegang te verlenen op de AD FS-computer:

   `Grant-AdfsApplicationPermission -ClientRoleIdentifier "<Client-ID>" -ServerRoleIdentifier <resource> -ScopeNames openid`

   Waarbij:

   * `resource` is de URL van de Microsoft Dynamics-organisatie.

1. Microsoft Dynamics gebruikt HTTPS-protocol. Als u AD FS-eindpunten wilt aanroepen vanaf de Forms-server, installeert u het Microsoft Dynamics-sitecertificaat in het Java-certificaatarchief met de `keytool` op de computer waarop AEM Forms wordt uitgevoerd.

## Cloudservice configureren voor uw Microsoft Dynamics-service {#configure-cloud-service-for-your-microsoft-dynamics-service}

De **MS Dynamics OData Cloud Service (OData Service)** de configuratie komt met standaard configuratie OData. Ga als volgt te werk om de instantie te configureren voor verbinding met uw Microsoft Dynamics.

1. Navigeren naar **[!UICONTROL Tools > Cloud Services > Data Sources]** en selecteert u de `global` configuratiemap.
1. Selecteren **MS Dynamics OData Cloud Service (OData Service)** configuratie en selecteer **[!UICONTROL Properties]**. Het dialoogvenster voor de configuratie-eigenschap van de cloudservice wordt geopend.

   In de **Verificatie-instellingen** tab:

   1. Voer de waarde in voor de **Serviceruimte** veld. Ga naar de instantie Dynamics en navigeer naar **Bronnen voor ontwikkelaars** om de waarde voor het gebied van de Wortel van de Dienst te bekijken. Bijvoorbeeld https://&lt;tenant-name>/api/data/v9.1/

   1. De standaardwaarden vervangen in het dialoogvenster **Client-id**(ook aangeduid als **Toepassings-id**), **Clientgeheim**, **OAuth URL**, **Token-URL vernieuwen**, **Toegang tot token-URL**, en **Bron** velden met waarden uit de configuratie van de Microsoft Dynamics. Het is verplicht de URL van de dynamische instantie op te geven in het dialoogvenster **Bron** veld voor het configureren van Microsoft Dynamics met een formuliergegevensmodel. Gebruik de URL van de hoofdmap van de service om de URL van de dynamische instantie af te leiden. Bijvoorbeeld: [https://org.crm.dynamics.com](https://org.crm.dynamics.com/).

   1. Opgeven **openhartig** in de **Autorisatiebereik** veld voor autorisatieproces op Microsoft Dynamics.

   ![Verificatie-instellingen](assets/dynamics_authentication_settings_new.png)

1. Klik op **[!UICONTROL Connect to OAuth]**. U wordt omgeleid naar de aanmeldingspagina van Microsoft Dynamics.
1. Meld u aan met uw Microsoft Dynamics-referenties en accepteer dit om de configuratie van de cloudservice in staat te stellen verbinding te maken met de service Microsoft Dynamics. Het is een eenmalige taak om verbinding tot stand te brengen tussen de cloudservice en de service.

   Vervolgens wordt u omgeleid naar de configuratiepagina van de cloudservice, die een bericht weergeeft dat de OData-configuratie is opgeslagen.

De de wolkendienst van de Cloud Service van de Dynamica van MS (OData Service) wordt gevormd en met uw dienst van de Dynamica verbonden.

## Formuliergegevensmodel maken {#create-form-data-model}

Wanneer u het AEM Forms-pakket installeert, een formuliergegevensmodel **Microsoft Dynamics FDM**, wordt geïmplementeerd op uw AEM. Door gebrek, gebruikt het model van vormgegevens de dienst van de Dynamiek van Microsoft die in de Cloud Service van de Dynamiek van MS (OData Service) als zijn gegevensbron wordt gevormd.

Als u het gegevensmodel van het formulier voor het eerst opent, wordt verbinding gemaakt met de geconfigureerde Microsoft Dynamics-service en worden entiteiten opgehaald van de instantie van Microsoft Dynamics. De &#39;contact&#39;- en &#39;lead&#39;-entiteiten van Microsoft Dynamics worden al toegevoegd aan het formuliergegevensmodel.

Ga naar **[!UICONTROL Forms > Data Integrations]**. Selecteren **Microsoft Dynamics FDM** en klik op **Bewerken** om het formuliergegevensmodel te openen in de bewerkingsmodus. U kunt het formuliergegevensmodel ook rechtstreeks openen via de volgende URL:

`https://'[server]:[port]'/aem/fdm/editor.html/content/dam/formsanddocuments-fdm/ms-dynamics-fdm`

![default-fdm-1](assets/default-fdm-1.png)

Vervolgens kunt u een adaptief formulier maken op basis van het formuliergegevensmodel en dit gebruiken in verschillende aangepaste gevallen voor formuliergebruik, zoals:

* Het adaptieve formulier vooraf invullen door informatie op te vragen bij Microsoft Dynamics entities and services
* Microsoft Dynamics-serverbewerkingen aanroepen die zijn gedefinieerd in een formuliergegevensmodel met behulp van adaptieve formulierregels
* Verzonden formuliergegevens naar Microsoft Dynamics-entiteiten schrijven

Het wordt aanbevolen een kopie te maken van het formuliergegevensmodel dat bij het AEM Forms-pakket wordt geleverd en gegevensmodellen en -services naar wens te configureren. Zo weet u zeker dat toekomstige updates van het pakket het gegevensmodel van het formulier niet overschrijven.

Voor meer informatie over het creëren van en het gebruiken van het model van vormgegevens in bedrijfswerkschema&#39;s, zie [Gegevensintegratie](../../forms/using/data-integration.md).
