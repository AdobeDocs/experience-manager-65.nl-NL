---
title: Configuratie Microsoft Dynamics OData
seo-title: Configuratie van Microsoft Dynamics ODtata
description: De diensten van de Dynamiek van Microsoft van de hefboomwerking, integreren, en werken met online en op-gebouw door het model van vormgegevens.
seo-description: Leer hoe u met het model van formuliergegevens de services online en op locatie van Microsoft Dynamics kunt integreren en werken.
uuid: 37e59633-484b-4a20-808d-2a0bc0d336cc
topic-tags: integration
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 627507f5-1ffc-48f8-8cc9-5dbc5e409ae3
docset: aem65
translation-type: tm+mt
source-git-commit: 1343cc33a1e1ce26c0770a3b49317e82353497ab
workflow-type: tm+mt
source-wordcount: '1205'
ht-degree: 0%

---


# Configuratie Microsoft Dynamics OData{#microsoft-dynamics-odata-configuration}

![gegevensintegratie](assets/data-integeration.png)

De Dynamiek van Microsoft is een software van het Beheer van de Verhouding van de Klant (CRM) en van het Middel van de Onderneming van de Planning (ERP) die ondernemingsoplossingen voor het creëren van en het beheren van klantenrekeningen, contacten, lood, kansen, en gevallen verstrekt. [De Integratie](../../forms/using/data-integration.md) van Gegevens van AEM Forms verstrekt een configuratie van de wolkendienst OData om Vormen met zowel online als op-gebouw de server van de Dynamiek van Microsoft te integreren. Het laat u toe om vormgegevensmodel tot stand te brengen dat op de entiteiten, de attributen, en de diensten wordt gebaseerd die in de dienst van de Dynamiek van Microsoft worden bepaald. Met het gegevensmodel van het formulier kunt u adaptieve formulieren maken die interageren met de Microsoft Dynamics-server om werkstromen van bedrijven mogelijk te maken. Bijvoorbeeld:

* Query uitvoeren op Microsoft Dynamics-server voor gegevens en aangepaste formulieren vooraf invullen
* Gegevens naar Microsoft Dynamics schrijven bij het verzenden van aangepaste formulieren
* Schrijf gegevens in de Dynamiek van Microsoft door douaneentiteiten die in het model van vormgegevens worden bepaald en vice versa

Het add-on pakket van AEM Forms omvat ook verwijzingsOData configuratie die u hefboomwerking kunt om de Dynamiek van Microsoft met AEM Forms snel te integreren.

Wanneer het pakket is geïnstalleerd, zijn de volgende entiteiten en de diensten beschikbaar op uw instantie van AEM Forms:

* MS Dynamics OData Cloud Service (OData Service)
* Formuliergegevensmodel met vooraf geconfigureerde entiteiten en services voor dynamiek van Microsoft.

De Cloud Service OData en het model van vormgegevens met vooraf geconfigureerde entiteiten en de diensten van de Dynamica van Microsoft zijn beschikbaar op uw instantie van AEM Forms slechts als de looppaswijze voor de instantie AEM als `samplecontent`(gebrek) wordt geplaatst. Voor meer informatie bij het vormen looppaswijzen voor een instantie AEM, zie de Wijzen van de [Looppas](/help/sites-deploying/configure-runmodes.md).

## Vereisten {#prerequisites}

Alvorens u begint opstelling en vormt de Dynamica van Microsoft, zorg ervoor dat u hebt:

* Het invoegpakket [AEM Forms is geïnstalleerd](../../forms/using/installing-configuring-aem-forms-osgi.md)
* De gevormde Dynamica 365 van Microsoft online of installeerde een geval van één van de volgende versies van de Dynamica van Microsoft:

   * Microsoft Dynamics 365 op locatie
   * Microsoft Dynamics 2016 op locatie

* [Registered the application for Microsoft Dynamics online service with Microsoft Azure Active Directory](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/walkthrough-register-dynamics-365-app-azure-active-directory). Noteer de waarden voor de client-id (ook toepassings-id genoemd) en het clientgeheim voor de geregistreerde service. Deze waarden worden gebruikt terwijl het [vormen van de wolkendienst voor uw dienst](../../forms/using/ms-dynamics-odata-configuration.md#configure-cloud-service-for-your-microsoft-dynamics-service)van de Dynamiek van Microsoft.

## Reactie-URL instellen voor geregistreerde toepassing Microsoft Dynamics {#set-reply-url-for-registered-microsoft-dynamics-application}

Ga als volgt te werk om Reactie URL voor geregistreerde toepassing van de Dynamiek van Microsoft te plaatsen:

>[!NOTE]
>
>Gebruik deze procedure slechts terwijl het integreren van AEM Forms met de online server van de Dynamiek van Microsoft.

1. Ga naar Microsoft Azure Active Directory-account en voeg de volgende URL voor de configuratie van de cloudservice toe in de instellingen voor URL&#39;s **beantwoorden** voor uw geregistreerde toepassing:

   `https://'[server]:[port]'/libs/fd/fdm/gui/components/admin/fdmcloudservice/createcloudconfigwizard/cloudservices.html`

   ![Azure-directory](assets/azure_directory_new.png)

1. Sla de configuratie op.

## Microsoft Dynamics voor IFD configureren {#configure-microsoft-dynamics-for-ifd}

De Dynamiek van Microsoft gebruikt op beweringen-gebaseerde authentificatie om toegang tot gegevens op de server van CRM van de Dynamica van Microsoft aan externe gebruikers te verlenen. Om dit toe te laten, doe het volgende om de Dynamica van Microsoft voor Internet-Onder ogen ziet plaatsing (IFD) te vormen en claimmontages te vormen.

>[!NOTE]
>
>Gebruik deze procedure slechts terwijl het integreren van AEM Forms met de server van de Dynamiek van Microsoft op-gebouw.

1. Vorm de Dynamica van Microsoft op-gebouw instantie voor IFD zoals die in IFD voor de Dynamica [van Microsoft wordt beschreven](https://technet.microsoft.com/en-us/library/dn609803.aspx)vormt.
1. Stel de volgende bevelen in werking gebruikend Vensters PowerShell om claimmontages op IFD-Toegelaten Dynamiek van Microsoft te vormen:

   ```shell
   Add-PSSnapin Microsoft.Crm.PowerShell
    $ClaimsSettings = Get-CrmSetting -SettingType OAuthClaimsSettings
    $ClaimsSettings.Enabled = $true
    Set-CrmSetting -Setting $ClaimsSettings
   ```

   Zie [Toepassingsregistratie voor CRM on-premisse (IFD)](https://msdn.microsoft.com/sl-si/library/dn531010(v=crm.7).aspx#bkmk_ifd) voor meer informatie.

## OAuth-client configureren op AD FS-computer {#configure-oauth-client-on-ad-fs-machine}

Doe het volgende om een cliënt OAuth op de Actieve machine van de Diensten van de Federatie van de Folder (AD FS) te registreren en toegang op de machine van het ADS te verlenen:

>[!NOTE]
>
>Gebruik deze procedure slechts terwijl het integreren van AEM Forms met de server van de Dynamiek van Microsoft op-gebouw.

1. Voer de volgende opdracht uit:

   `Add-AdfsClient -ClientId “<Client-ID>” -Name "<name>" -RedirectUri "<redirect-uri>" -GenerateClientSecret`

   Waar:

   * `Client-ID` is een cliëntidentiteitskaart u het gebruiken van om het even welke generator kunt produceren GUID.
   * `redirect-uri` is URL aan de de wolkendienst van de Dynamiek van Microsoft OData op AEM Forms. De standaardcloudservice die samen met het AEM Forms-pakket wordt geïnstalleerd, wordt geïmplementeerd op de volgende URL:
      `https://'[server]:[port]'/libs/fd/fdm/gui/components/admin/fdmcloudservice/createcloudconfigwizard/cloudservices.html`

1. Voer de volgende opdracht uit om toegang te verlenen op de AD FS-computer:

   `Grant-AdfsApplicationPermission -ClientRoleIdentifier “<Client-ID>” -ServerRoleIdentifier <resource> -ScopeNames openid`

   Waar:

   * `resource` is de organisatie URL van de Dynamiek van Microsoft.

1. Microsoft Dynamics gebruikt HTTPS-protocol. Als u AD FS-eindpunten wilt aanroepen vanaf Forms Server, moet u het certificaat van de Microsoft Dynamics-site installeren in het Java-certificaatarchief met de `keytool` opdracht op de computer waarop AEM Forms worden uitgevoerd.

## De cloudservice voor uw Microsoft Dynamics configureren {#configure-cloud-service-for-your-microsoft-dynamics-service}

De configuratie van de Cloud Service van de  van de Dynamica van **MS (OData Service)** komt met standaard configuratie OData. Om het te vormen om met uw dienst van de Dynamiek van Microsoft te verbinden, doe het volgende.

1. Navigeer naar **[!UICONTROL Tools > Cloud Services > Data Sources]** en tik op de `global` configuratiemap.
1. Selecteer de configuratie van de Cloud Service van de Dynamica OData van **MS (OData Service)** en tik **[!UICONTROL Properties]**. Het dialoogvenster voor de configuratie-eigenschap van de cloudservice wordt geopend.

   Op het tabblad **Verificatie-instellingen** :

   1. Voer de waarde in voor het veld **Serviceruimte** . Ga naar de instantie van de Dynamiek en navigeer aan de Middelen **van de** Ontwikkelaar om de waarde voor het gebied van de Wortel van de Dienst te bekijken. Bijvoorbeeld https://&lt;huurder-name>/api/data/v9.1/

   1. Vervang de standaardwaarden in **Cliënt ID**(die ook als **Toepassings identiteitskaart** wordt bedoeld), Geheim **van de** Cliënt, **OAuth URL**, **Vernieuwt Symbolische URL********** , Symbolische URLToegangstoken, en Resource gebieden met waarden van uw de dienstconfiguratie van de Dynamiek van Microsoft. Het is verplicht de URL van de dynamische instantie op te geven in het veld **Resource** om Microsoft Dynamics te configureren met een formuliergegevensmodel. Gebruik de URL van de hoofdmap van de service om de URL van de dynamische instantie af te leiden. Bijvoorbeeld [https://org.crm.dynamics.com](https://org.crm.dynamics.com/).

   1. Specificeer **openid** op het gebied van het Toepassingsgebied **van de** Vergunning voor vergunningsproces op de Dynamica van Microsoft.

   ![Verificatie-instellingen](assets/dynamics_authentication_settings_new.png)

1. Klik op **[!UICONTROL Connect to OAuth]**. U wordt opnieuw gericht aan de login van de Dynamica van Microsoft pagina.
1. Meld u aan met de referenties voor Microsoft Dynamics en accepteer de configuratie van de cloudservice om verbinding te maken met de Microsoft Dynamics-service. Het is een eenmalige taak om verbinding tot stand te brengen tussen de cloudservice en de service.

   Vervolgens wordt u omgeleid naar de configuratiepagina van de cloudservice, die een bericht weergeeft dat de OData-configuratie is opgeslagen.

De de wolkendienst van de Cloud Service van de Dynamica van MS (OData Service) wordt gevormd en met uw dienst van de Dynamica verbonden.

## Formuliergegevensmodel maken {#create-form-data-model}

Wanneer u het pakket AEM Forms installeert, wordt een model van vormgegevens, de Dynamica FDM **van** Microsoft, opgesteld op uw instantie AEM. Door gebrek, gebruikt het model van vormgegevens de dienst van de Dynamiek van Microsoft die in de Cloud Service van de Dynamiek van MS (OData Dienst) als zijn gegevensbron wordt gevormd.

Bij het openen van het model van vormgegevens voor het eerst, verbindt het met de gevormde dienst van de Dynamiek van Microsoft en haalt entiteiten van uw instantie van de Dynamiek van Microsoft. De &quot;contact&quot;en &quot;lood&quot;entiteiten van de Dynamiek van Microsoft worden reeds toegevoegd in het model van vormgegevens.

Ga naar **[!UICONTROL Forms > Data Integrations]** om het formuliergegevensmodel te bekijken. Selecteer FDM voor **Microsoft Dynamics** en klik op **Bewerken** om het model met formuliergegevens te openen in de bewerkingsmodus. U kunt het formuliergegevensmodel ook rechtstreeks openen via de volgende URL:

`https://'[server]:[port]'/aem/fdm/editor.html/content/dam/formsanddocuments-fdm/ms-dynamics-fdm`

![default-fdm-1](assets/default-fdm-1.png)

Vervolgens kunt u een adaptief formulier maken op basis van het formuliergegevensmodel en dit gebruiken in verschillende aangepaste gevallen voor formuliergebruik, zoals:

* Aanpasbaar formulier vooraf invullen door informatie op te vragen bij Microsoft Dynamics entities and services
* De serverbewerkingen van Microsoft Dynamics aanroepen die zijn gedefinieerd in een formuliergegevensmodel met behulp van adaptieve formulierregels
* Verzonden formuliergegevens naar Microsoft Dynamics-entiteiten schrijven

Het wordt aanbevolen een kopie te maken van het formuliergegevensmodel dat bij het AEM Forms-pakket wordt geleverd en gegevensmodellen en -services naar wens te configureren. Zo weet u zeker dat toekomstige updates van het pakket het gegevensmodel van het formulier niet overschrijven.

Voor meer informatie over het creëren van en het gebruiken van het model van vormgegevens in bedrijfswerkschema&#39;s, zie de Integratie [van](../../forms/using/data-integration.md)Gegevens.
