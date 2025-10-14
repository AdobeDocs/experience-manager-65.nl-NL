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
| AEM as a Cloud Service | [&#x200B; klik hier &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/integrate/use-form-data-model/ms-dynamics-odata-configuration.html?lang=nl-NL) |
| AEM 6,5 | Dit artikel |

![&#x200B; gegeven-integratie &#x200B;](assets/data-integeration.png)

Microsoft Dynamics is een ERP-software (Customer Relationship Management) en Enterprise Resource Planning (Enterprise Resource Planning) die bedrijfsoplossingen biedt voor het maken en beheren van klantaccounts, contactpersonen, leads, kansen en gevallen. [&#x200B; de Integratie van Gegevens van AEM Forms &#x200B;](../../forms/using/data-integration.md) verstrekt een configuratie van de wolkendienst OData om Forms met zowel online als op-gebouw de server van de Dynamica van Microsoft te integreren. Hiermee kunt u een formuliergegevensmodel maken op basis van de entiteiten, kenmerken en services die zijn gedefinieerd in de service Microsoft Dynamics. Met het gegevensmodel van het formulier kunt u adaptieve formulieren maken die interageren met de Microsoft Dynamics-server om bedrijfsworkflows mogelijk te maken. Bijvoorbeeld:

* Query Microsoft Dynamics-server voor gegevens en aangepaste formulieren vooraf invullen
* Gegevens naar Microsoft Dynamics schrijven bij het verzenden van aangepaste formulieren
* Gegevens schrijven in Microsoft Dynamics via aangepaste entiteiten die zijn gedefinieerd in het formuliergegevensmodel en omgekeerd

Het AEM Forms-add-on-pakket bevat ook een referentie OData-configuratie waarmee u Microsoft Dynamics snel kunt integreren met AEM Forms.

Wanneer het pakket is geïnstalleerd, zijn de volgende entiteiten en services beschikbaar op uw AEM Forms-exemplaar:

* MS Dynamics OData Cloud Service (OData Service)
* Formuliergegevensmodel met vooraf geconfigureerde Microsoft Dynamics-entiteiten en -services.

De vooraf geconfigureerde entiteiten en services van Microsoft Dynamics in een formuliergegevensmodel zijn alleen beschikbaar in uw AEM Forms-exemplaar als de uitvoermodus voor de AEM-instantie is ingesteld op `samplecontent` (standaard). MS Dynamics OData Cloud Service (OData Service) is ook beschikbaar in andere uitvoeringsmodi. Voor meer informatie bij het vormen looppas wijzen voor een AEM instantie, zie [&#x200B; Wijzen van de Looppas &#x200B;](/help/sites-deploying/configure-runmodes.md).

## Vereisten {#prerequisites}

Voordat u begint met het instellen en configureren van Microsoft Dynamics, moet u ervoor zorgen dat:

* Geïnstalleerd het [&#x200B; toe:voegen-op pakket van AEM Forms &#x200B;](../../forms/using/installing-configuring-aem-forms-osgi.md)
* Configured Microsoft Dynamics 365 online of installeerde een exemplaar van een van de volgende Microsoft Dynamics-versies:

   * Microsoft Dynamics 365 on-premisse
   * Microsoft Dynamics 2016 on-premisse

* [&#x200B; registreerde de toepassing voor de Online dienst van de Dynamica van Microsoft met Microsoft Azure Actieve Folder &#x200B;](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/walkthrough-register-dynamics-365-app-azure-active-directory). Noteer de waarden voor de client-id (ook toepassings-id genoemd) en het clientgeheim voor de geregistreerde service. Deze waarden worden gebruikt terwijl [&#x200B; het vormen de wolkendienst voor uw dienst van de Dynamiek van Microsoft &#x200B;](../../forms/using/ms-dynamics-odata-configuration.md#configure-cloud-service-for-your-microsoft-dynamics-service).

## Reactie-URL instellen voor geregistreerde toepassing Microsoft Dynamics {#set-reply-url-for-registered-microsoft-dynamics-application}

Ga als volgt te werk om de antwoordURL voor geregistreerde Microsoft Dynamics-toepassing in te stellen:

>[!NOTE]
>
>Gebruik deze procedure alleen tijdens de integratie van AEM Forms met de online Microsoft Dynamics-server.

1. Ga naar Microsoft Azure Actieve rekening van de Folder en voeg de volgende URL van de de dienstconfiguratie van de wolk in **Reageer URLs** montages voor uw geregistreerde toepassing toe:

   `https://'[server]:[port]'/libs/fd/fdm/gui/components/admin/fdmcloudservice/createcloudconfigwizard/cloudservices.html`

   ![&#x200B; Azure folder &#x200B;](assets/azure_directory_new.png)

1. Sla de configuratie op.

## Microsoft Dynamics voor IFD configureren {#configure-microsoft-dynamics-for-ifd}

Microsoft Dynamics gebruikt op basis van claims om externe gebruikers toegang te bieden tot gegevens op de Microsoft Dynamics CRM-server. Om dit toe te laten, doe het volgende om de Dynamica van Microsoft voor Internet-Onder ogen ziet plaatsing (IFD) te vormen en claimmontages te vormen.

>[!NOTE]
>
>Gebruik deze procedure slechts terwijl het integreren van AEM Forms met de server van de Dynamiek van Microsoft op-gebouw.

1. Vorm de Dynamiek van Microsoft op-gebouw instantie voor IFD zoals die in [&#x200B; wordt beschreven vorm IFD voor de Dynamica van Microsoft &#x200B;](https://technet.microsoft.com/en-us/library/dn609803.aspx).
1. Stel de volgende bevelen in werking gebruikend Vensters PowerShell om claimmontages op IFD-Toegelaten Dynamiek van Microsoft te vormen:

   ```shell
   Add-PSSnapin Microsoft.Crm.PowerShell
    $ClaimsSettings = Get-CrmSetting -SettingType OAuthClaimsSettings
    $ClaimsSettings.Enabled = $true
    Set-CrmSetting -Setting $ClaimsSettings
   ```

   Zie [&#x200B; registratie van de app voor CRM op-gebouw (IFD) &#x200B;](https://msdn.microsoft.com/sl-si/library/dn531010(v=crm.7).aspx#bkmk_ifd) voor details.

## OAuth-client configureren op AD FS-computer {#configure-oauth-client-on-ad-fs-machine}

Doe het volgende om een cliënt OAuth op de Actieve machine van de Diensten van de Federatie van de Folder (AD FS) te registreren en toegang op de machine van het ADS te verlenen:

>[!NOTE]
>
>Gebruik deze procedure slechts terwijl het integreren van AEM Forms met de server van de Dynamiek van Microsoft op-gebouw.

1. Voer de volgende opdracht uit:

   `Add-AdfsClient -ClientId "<Client-ID>" -Name "<name>" -RedirectUri "<redirect-uri>" -GenerateClientSecret`

   Waarbij:

   * `Client-ID` is een cliëntID u het gebruiken van om het even welke generator kunt produceren GUID.
   * `redirect-uri` is de URL naar de Microsoft Dynamics OData-cloudservice op AEM Forms. De standaardcloudservice die wordt geïnstalleerd met het AEM Forms-pakket, wordt geïmplementeerd op de volgende URL:

     `https://'[server]:[port]'/libs/fd/fdm/gui/components/admin/fdmcloudservice/createcloudconfigwizard/cloudservices.html`

1. Voer de volgende opdracht uit om toegang te verlenen op de AD FS-computer:

   `Grant-AdfsApplicationPermission -ClientRoleIdentifier "<Client-ID>" -ServerRoleIdentifier <resource> -ScopeNames openid`

   Waarbij:

   * `resource` is de URL van de Microsoft Dynamics.

1. Microsoft Dynamics gebruikt HTTPS-protocol. Als u AD FS-eindpunten wilt aanroepen vanaf de Forms-server, installeert u het Microsoft Dynamics-sitecertificaat naar het Java-certificaatarchief met de opdracht `keytool` op de computer waarop AEM Forms wordt uitgevoerd.

## Cloudservice configureren voor uw Microsoft Dynamics-service {#configure-cloud-service-for-your-microsoft-dynamics-service}

De **Cloud Service van de Dynamiek van MS OData (Dienst OData)** configuratie komt met standaard configuratie OData. Ga als volgt te werk om de instantie te configureren voor verbinding met uw Microsoft Dynamics.

1. Navigeer naar **[!UICONTROL Tools > Cloud Services > Data Sources]** en selecteer de configuratiemap van `global` .
1. Selecteer {de Cloud Service van de Dynamiek van 0} MS OData (Dienst OData) **configuratie en selecteer &#x200B;** [!UICONTROL Properties]&#x200B;**.** Het dialoogvenster voor de configuratie-eigenschap van de cloudservice wordt geopend.

   In het **lusje van de Montages van de Authentificatie**:

   1. Ga de waarde voor het **gebied van de Wortel van de Dienst 0&rbrace; in.** Ga naar de instantie van de Dynamiek en navigeer aan **Middelen van de Ontwikkelaar** om de waarde voor het gebied van de Wortel van de Dienst te bekijken. Bijvoorbeeld https://&lt;huurder-name>/api/data/v9.1/

   1. Vervang de standaardwaarden in **Identiteitskaart van de Cliënt** (ook als **identiteitskaart van de Toepassing** wordt bedoeld), **Geheime Cliënt**, **OAuth URL**, **verfrist Symbolische URL**, **Symbolische URL van de Toegang**, en **gebieden van het Middel met waarden van uw de dienstconfiguratie van de Dynamiek van Microsoft.** Het is verplicht om de dynamische instantie URL op het **gebied van het Middel** te specificeren om de Dynamiek van Microsoft met een model van vormgegevens te vormen. Gebruik de URL van de hoofdmap van de service om de URL van de dynamische instantie af te leiden. Bijvoorbeeld, [&#x200B; https://org.crm.dynamics.com &#x200B;](https://org.crm.dynamics.com/).

   1. Specificeer **openid** in het **gebied van het Toepassingsgebied van de Vergunning** voor vergunningsproces op de Dynamiek van Microsoft.

   ![&#x200B; Montages van de Authentificatie &#x200B;](assets/dynamics_authentication_settings_new.png)

1. Klik op **[!UICONTROL Connect to OAuth]**. U wordt omgeleid naar de aanmeldingspagina van Microsoft Dynamics.
1. Meld u aan met uw Microsoft Dynamics-referenties en accepteer dit om de configuratie van de cloudservice in staat te stellen verbinding te maken met de service Microsoft Dynamics. Het is een eenmalige taak om verbinding tot stand te brengen tussen de cloudservice en de service.

   Vervolgens wordt u omgeleid naar de configuratiepagina van de cloudservice, die een bericht weergeeft dat de OData-configuratie is opgeslagen.

De de wolkendienst van de Cloud Service van de Dynamica van MS (OData Service) wordt gevormd en met uw dienst van de Dynamica verbonden.

## Formuliergegevensmodel maken {#create-form-data-model}

Wanneer u het pakket van AEM Forms installeert, wordt een model van vormgegevens, {de Dynamica FDM van 0} Microsoft **, opgesteld op uw AEM instantie.** Door gebrek, gebruikt het model van vormgegevens de dienst van de Dynamiek van Microsoft die in de Cloud Service van de Dynamiek van MS (OData Service) als zijn gegevensbron wordt gevormd.

Als u het gegevensmodel van het formulier voor het eerst opent, wordt verbinding gemaakt met de geconfigureerde Microsoft Dynamics-service en worden entiteiten opgehaald van de instantie van Microsoft Dynamics. De &#39;contact&#39;- en &#39;lead&#39;-entiteiten van Microsoft Dynamics worden al toegevoegd aan het formuliergegevensmodel.

Ga naar **[!UICONTROL Forms > Data Integrations]** om het formuliergegevensmodel te bekijken. Selecteer **de Dynamica FDM van Microsoft** en klik **uitgeven** om het model van vormgegevens op uit te geven wijze te openen. U kunt het formuliergegevensmodel ook rechtstreeks openen via de volgende URL:

`https://'[server]:[port]'/aem/fdm/editor.html/content/dam/formsanddocuments-fdm/ms-dynamics-fdm`

![&#x200B; gebrek-fdm-1 &#x200B;](assets/default-fdm-1.png)

Vervolgens kunt u een adaptief formulier maken op basis van het formuliergegevensmodel en dit gebruiken in verschillende aangepaste gevallen voor formuliergebruik, zoals:

* Het adaptieve formulier vooraf invullen door informatie op te vragen bij Microsoft Dynamics entities and services
* Microsoft Dynamics-serverbewerkingen aanroepen die zijn gedefinieerd in een formuliergegevensmodel met behulp van adaptieve formulierregels
* Verzonden formuliergegevens naar Microsoft Dynamics-entiteiten schrijven

Het wordt aanbevolen een kopie te maken van het formuliergegevensmodel dat bij het AEM Forms-pakket wordt geleverd en gegevensmodellen en -services naar wens te configureren. Zo weet u zeker dat toekomstige updates van het pakket het gegevensmodel van het formulier niet overschrijven.

Voor meer informatie over het creëren van en het gebruiken van het model van vormgegevens in bedrijfswerkschema&#39;s, zie {de Integratie van 0} Gegevens [&#128279;](../../forms/using/data-integration.md).
