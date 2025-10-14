---
title: Salesforce-integratie met AEM Forms via OAuth 2.0-clientaanmeldingsgegevens
description: Stappen om de integratie van Salesforce met AEM Forms te integreren gebruikend OAuth 2.0 cliëntgeloofsbrieven stroom
exl-id: 4c356aa6-ebd4-40b9-89e3-bc4519e4a7c5
solution: Experience Manager, Experience Manager Forms
feature: Form Data Model
role: Admin, User, Developer
source-git-commit: e821be5233fd5f6688507096790d219d25903892
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 1%

---

# Integratie van Salesforce met gebruik van OAuth 2.0 client credentials flow {#configure-salesforce-with-ouath-2.0-client-credential}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [&#x200B; klik hier &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/integrate/use-form-data-model/oauth2-client-credentials-flow-for-server-to-server-integration.html?lang=nl-NL) |
| AEM 6,5 | Dit artikel |

U kunt OAuth 2.0 cliëntgeloofsbrieven gebruiken om AEM Forms met de toepassing van Salesforce te integreren. OAuth 2.0 cliëntgeloofsbrieven zijn een standaard en veilige methode voor directe mededeling zonder gebruikersbetrokkenheid.

![&#x200B; Werkschema terwijl het plaatsen van mededeling tussen AEM Forms en toepassing Salesforce &#x200B;](/help/forms/using/assets/salesforce-workflow.png)

AEM Forms wisselt de aanmeldingsgegevens van de client uit (de sleutel van de consument en het consumentengeheim), die zijn gedefinieerd in de toepassing Salesforce waarmee verbinding wordt gemaakt, om een toegangstoken te verkrijgen.

Er zijn veelvoudige voordelen om OAuth 2.0 cliëntgeloofsbrieven voor authentificatie over de authentificatie van de Stroom van de Code van de Vergunning te gebruiken:

* OAuth 2.0 de authentificatie van de cliëntgeloofsbrieven staat meer dan vijf verbindingen per gebruiker toe.
* AEM gegevensbronconfiguratie werkt verder aan deactivering, toegangsveranderingen, wachtwoordupdate voor een AEM gebruiker.

## Vereisten {#prerequisites}

Voordat u de communicatie tussen een Salesforce-toepassing en een AEM omgeving instelt:

* Creeer a [&#x200B; Salesforce verbonden app met OAuth 2.0 stroom van de cliëntcredentie &#x200B;](https://help.salesforce.com/s/articleView?id=sf.connected_app_client_credentials_setup.htm&type=5) en een slechts API-gebruiker voor uw organisatie en verkrijg de sleutel van de consument en het consumentengeheim voor app.

* Zorg ervoor dat het Swagger-bestand op de juiste wijze is geconfigureerd zodat het overeenkomt met de API&#39;s van uw organisatie. Alternatief, kunt u verkiezen om [&#x200B; tot een dossier van de Swagger &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/forms/integrate-with-salesforce/describe-rest-api.html?lang=nl-NL) van het kras te leiden, dat voor gebruik in uw AEM milieu wordt gemaakt.
>[!NOTE]
>
> AEM 6.5 ondersteunt alleen Swagger 2.0-bestandsspecificaties.

+++

## Stappen om Salesforce met de stroom van de Verantwoording van de Cliënt te vormen {#steps-to-create-aem-datasource-configuration}

1. Meld u aan bij de instantie Auteur.
1. Ga naar **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Data Sources]** .
1. Selecteer de configuratiemap.
1. Klik op **[!UICONTROL Create]** en **[!UICONTROL Create Data Source Configuration]** verschijnt.
1. Geef de waarde **[!UICONTROL Title]** op en selecteer de waarde **[!UICONTROL Service Type]** as **[!UICONTROL RESTful Service]** .
1. Klik op **[!UICONTROL Next]**.
1. Selecteer **[!UICONTROL Swagger Source]** als **[!UICONTROL File].**
   >[!NOTE]
   >
   > Zodra het wagerbestand is geselecteerd, worden het schema, de hostnaam en het basispad automatisch ingevuld.

1. Upload het gemaakte wagerbestand van uw lokale computer door op **[!UICONTROL Browse]** te klikken.
1. Selecteer **[!UICONTROL Authentication Type]** as **[!UICONTROL OAuth 2.0]** en het deelvenster **[!UICONTROL Authentication Settings]** verschijnt.
1. Selecteer **[!UICONTROL Grant Type]** als **[!UICONTROL Client Credentials]** .
1. Geef de **[!UICONTROL Client Id]** en **[!UICONTROL Client Secret]** op die u wilt ophalen uit de met Salesforce verbonden app.
1. De **[!UICONTROL Access Token URL]** opgeven in de notatie
   `https://[MyDomainName].my.salesforce.com/services/oauth2/token`.

   >[!NOTE]
   >
   > Elke organisatie heeft een eigen specifieke domeinnaam.

1. Klik op **[!UICONTROL Test Connection]**.
1. Klik op de knop **[!UICONTROL Create]** als de verbinding tot stand is gebracht.

Nu, kunt u [&#x200B; tot het Model van de Gegevens van de Vorm &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-65/forms/form-data-model/create-form-data-models.html?lang=nl-NL) leiden om de gevormde gegevensbron met uw Aanpassings Forms te integreren.
