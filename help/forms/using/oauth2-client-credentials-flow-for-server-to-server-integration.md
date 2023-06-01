---
title: Salesforce-integratie met AEM Forms via OAuth 2.0-clientaanmeldingsgegevens
seo-title: Salesforce integration with AEM Forms using OAuth 2.0 client credentials flow
description: Stappen om de integratie van Salesforce met AEM Forms te integreren gebruikend OAuth 2.0 cliëntgeloofsbrieven stroom
seo-description: Steps to integrate Salesforce integration with AEM Forms using OAuth 2.0 client credentials flow
source-git-commit: cc0375f5b5616f82a73bd983a9da95225c51db99
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 0%

---


# Integratie van Salesforce met gebruik van OAuth 2.0-clientaanmeldingsgegevens  {#configure-salesforce-with-ouath-2.0-client-credential}

Om AEM Forms met de toepassing van Salesforce te integreren, wordt de OAuth 2.0 cliëntgeloofsstroom gebruikt. Het is een gestandaardiseerde en veilige methode voor directe communicatie zonder betrokkenheid van de gebruiker. In deze flow wisselt de clienttoepassing (AEM Formulier) de clientgegevens uit, die zijn gedefinieerd in de toepassing waarmee Salesforce is verbonden, om een toegangstoken te verkrijgen. De vereiste cliëntgeloofsbrieven omvatten de consumentensleutel en het geheime voorgeheugen van de consument.

## Voordelen van integratie van Salesforce met AEM Forms met behulp van OAuth 2.0-clientaanmeldingsgegevens {#advantages-of-integrating-saleforce-aemforms}

AEM Forms ondersteunt de integratie van Salesforce met de stroom van de Code van de Vergunning, naast de OAuth 2.0 cliëntgeloofsbrieven stroom. In de stroom van de Code van de Vergunning OAuth 2.0, verkrijgt de Toepassing van de Cliënt (AEM Forms) middeltoegang namens een gebruiker Salesforce, die sommige beperkingen heeft:

* Maximaal vijf verbindingen per gebruiker zijn toegestaan. Meer verbindingen trekken automatisch oudere verbindingen in.
* Als een gebruiker wordt gedeactiveerd, toegang verliest of een wachtwoord bijwerkt, houdt de AEM gegevensbronconfiguratie op te werken.

## Vereisten {#prerequisites}

Voor het ophalen en ophalen van gegevens tussen Salesforce- en AEM-omgevingen zijn bepaalde voorwaarden vereist voordat u verdergaat:

+++ **Een Saleforce-toepassing instellen die is verbonden met de gegevensstroom van de client en een gebruiker met alleen een API**

Het is verplicht om een Salesforce-verbonden app te maken met OAuth 2.0-clientgegevens en een gebruiker met alleen een API voor uw organisatie. Raadpleeg het artikel voor gedetailleerde stappen [OAuth 2.0 Client Credentials Flow for Server-to-Server Integration](https://help.salesforce.com/s/articleView?id=sf.connected_app_client_credentials_setup.htm&amp;type=5). Deze stappen helpen u de sleutel van de consument en het consumentengeheim verkrijgen.

>[!NOTE]
>
> Zorg ervoor om van de consumentensleutel en het consumentengeheim nota te nemen aangezien zij terwijl het creëren van een AEM gegevensbronconfiguratie worden vereist.

+++

+++ **Een wagerbestand maken**

Swagger is een open-source set regels, specificaties en hulpmiddelen voor het ontwikkelen en beschrijven van RESTful-API&#39;s. [Een wagerbestand maken](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/forms/integrate-with-salesforce/describe-rest-api.html) voordat Salesforce wordt geïntegreerd met AEM Forms.

>[!NOTE]
>
> AEM 6.5 ondersteunt alleen Swagger 2.0-bestandsspecificaties.

+++

## Stappen om Salesforce met de stroom van de Verantwoording van de Cliënt te vormen {#steps-to-create-aem-datasource-configuration}

1. Meld u aan bij de instantie Auteur.
1. Ga naar **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Data Sources]**.
1. Selecteer de configuratiemap.
1. Klikken **[!UICONTROL Create]** en de **[!UICONTROL Create Data Source Configuration]** wordt weergegeven.
1. Geef de **[!UICONTROL Title]** en selecteert u de **[!UICONTROL Service Type]** als **[!UICONTROL RESTful Service]**.
1. Klik op **[!UICONTROL Next]**.
1. Selecteer **[!UICONTROL Swagger Source]** als **[!UICONTROL File].**
   >[!NOTE]
   >
   > Zodra het wagerbestand is geselecteerd, worden het schema, de hostnaam en het basispad automatisch ingevuld.

1. Upload het gemaakte wagerbestand van uw lokale computer door op **[!UICONTROL Browse]**.
1. Selecteer **[!UICONTROL Authentication Type]** als **[!UICONTROL OAuth 2.0]** en de **[!UICONTROL Authentication Settings]** wordt weergegeven.
1. Selecteer **[!UICONTROL Grant Type]** als **[!UICONTROL Client Credentials]**.
1. Geef de **[!UICONTROL Client Id]** en **[!UICONTROL Client Secret]** verkregen uit de Salesforce-app.
1. Geef de **[!UICONTROL Access Token URL]** in formaat
   `https://[MyDomainName].my.salesforce.com/services/oauth2/token`.

   >[!NOTE]
   >
   > Elke organisatie heeft een eigen specifieke domeinnaam.

1. Klik op **[!UICONTROL Test Connection]**.
1. Als de verbinding is gelukt, klikt u op de knop **[!UICONTROL Create]** knop.

Nu kunt u [Maak het formuliergegevensmodel](https://experienceleague.adobe.com/docs/experience-manager-65/forms/form-data-model/create-form-data-models.html?lang=en) om de gevormde gegevensbron met uw Aangepaste Vorm te integreren.


