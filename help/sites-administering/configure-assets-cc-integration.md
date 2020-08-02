---
title: Integratie van AEM Assets met Experience Cloud en Creative Cloud configureren
seo-title: Integratie van AEM Assets met Marketing Cloud en Creative Cloud configureren
description: Leer hoe te om de integratie van AEM Assets met Experience Cloud en Creative Cloud te vormen.
seo-description: Leer hoe te om de integratie van AEM Assets met Experience Cloud en Creative Cloud te vormen.
uuid: ec36ea0e-607f-4c73-89df-e095067fccd4
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
discoiquuid: 82a8e807-a2df-4fe3-a68c-2dabc9328eca
docset: aem65
translation-type: tm+mt
source-git-commit: c7f06670ca8b488a661fde7a133bce6886ee7f5d
workflow-type: tm+mt
source-wordcount: '1326'
ht-degree: 1%

---


# Integratie van AEM Assets met Experience Cloud en Creative Cloud configureren {#configure-aem-assets-integration-with-experience-cloud-and-creative-cloud}

Als u een Adobe Experience Cloud-klant bent, kunt u uw middelen binnen Adobe Experience Manager (AEM) Middelen synchroniseren met Adobe Creative Cloud en vice versa. U kunt uw elementen ook synchroniseren met Experience Cloud en andersom. U kunt deze synchronisatie instellen via Adobe I/O.

De workflow voor het instellen van deze integratie is:

1. Creeer een authentificatie in Adobe I/O gebruikend een openbare gateway en krijg toepassingsidentiteitskaart
1. Maak een profiel op uw AEM Assets-instantie met de toepassings-id.
1. Gebruik deze configuratie om uw elementen binnen AEM Assets met Creative Cloud te synchroniseren.

Op de achtergrond, verklaart de AEM server uw profiel met de gateway voor authentiek en synchroniseert dan de gegevens tussen AEM Assets en Experience Cloud.

>[!CAUTION]
>
>AEM naar de functie Mappen delen van Creative Cloud is afgekeurd in AEM Assets. Leer meer en vind vervangingen in [AEM en de Beste praktijken](/help/assets/aem-cc-integration-best-practices.md)van de Integratie van de Creative Cloud.

![Gegevensstroom wanneer AEM Assets en Creative Cloud zijn geïntegreerd](assets/chlimage_1-48.png)

Gegevensstroom wanneer AEM Assets en Creative Cloud zijn geïntegreerd

>[!NOTE]
>
>Voor het delen van elementen tussen Adobe Experience Cloud en Adobe Creative Cloud zijn beheerdersrechten voor de AEM vereist.

>[!CAUTION]
>
>Adobe Marketing Cloud is omgedoopt tot Adobe Experience Cloud. In de onderstaande procedures wordt nog steeds verwezen naar Marketing Cloud om de huidige interface te weerspiegelen. Deze vermeldingen zullen later worden gewijzigd.

## Een toepassing maken {#create-an-application}

1. Heb toegang tot de de gatewayinterface van de Ontwikkelaar van Adobe door het programma te openen bij [https://legacy-oauth.cloud.adobe.io](https://legacy-oauth.cloud.adobe.io/).

   >[!NOTE]
   >
   >U hebt beheerdersrechten nodig om een toepassings-id te maken.

1. Navigeer in het linkervenster naar **[!UICONTROL Developer Tools]** > **[!UICONTROL Applications]** om een lijst met toepassingen weer te geven.
1. Klik op **[!UICONTROL Add]** name_assets_addcircle_icon ![](assets/aem_assets_addcircle_icon.png) om een toepassing te maken.
1. Selecteer in de **[!UICONTROL Client Credentials]** lijst **[!UICONTROL Service Account (JWT Assertion)]** een communicatieservice van server naar server voor serververificatie.

   ![chlimage_1-49](assets/chlimage_1-49.png)

1. Geef een naam voor de toepassing en een optionele beschrijving op.
1. Selecteer in de **[!UICONTROL Organization]** lijst de organisatie waarvoor u elementen wilt synchroniseren.
1. Selecteer in de **[!UICONTROL Scope]** lijst **[!UICONTROL dam-read]**, **[!UICONTROL dam-sync]**, **[!UICONTROL dam-write]** en **[!UICONTROL cc-share]**.
1. Klik op **[!UICONTROL Create]**. Een bericht meldt dat de toepassing is gemaakt.

   ![Melding van het feit dat de toepassing met succes is gemaakt voor de integratie van AEM Assets met Adobe CC](assets/chlimage_1-50.png)

1. Kopieer de gegenereerde **[!UICONTROL Application ID]** code voor de nieuwe toepassing.

   >[!CAUTION]
   >
   >Zorg ervoor dat u de afbeelding niet per ongeluk kopieert **[!UICONTROL Application Secret]** in plaats van de **[!UICONTROL Application ID]**.

## Een nieuwe configuratie toevoegen aan de Marketing Cloud {#add-a-new-configuration-to-marketing-cloud}

1. Klik op het AEM logo in de gebruikersinterface van de lokale AEM Assets en navigeer naar **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Legacy Cloud Services]**.

1. Zoek de **[!UICONTROL Adobe Marketing Cloud]** service. Klik op **[!UICONTROL Configure Now]** als er geen configuraties bestaan. Als configuraties bestaan, klik **[!UICONTROL Show Configurations]** en klik `+` om een nieuwe configuratie toe te voegen.

   >[!NOTE]
   >
   >Gebruik een Adobe ID-account met beheerdersrechten voor de organisatie.

1. Geef in het **[!UICONTROL Create Configuration]** dialoogvenster een titel en naam op voor de nieuwe configuratie en klik op **[!UICONTROL Create]**.

   ![Geef een nieuwe configuratie de naam om AEM Assets en CC te integreren](assets/chlimage_1-51.png)

1. Geef in het **[!UICONTROL Tenant URL]** veld de URL voor AEM Assets op.

   >[!CAUTION]
   >
   >Als u vanwege het opnieuw brandmerken de URL van de huurder hebt ingevoerd `https://<tenant_id>.marketing.adobe.com` `https://<tenant_id>.experiencecloud.adobe.com.` Om dit te kunnen doen, volgt u de onderstaande stappen:
   >
   >1. Ga naar **Gereedschappen > Cloud Servicen > Oudere Cloud Servicen**.
   1. Klik onder Adobe Marketing Cloud op **Configuraties** tonen.
   1. Selecteer de configuratie die terwijl vestiging de AEM-MAC-CC synchronisatie werd gecreeerd.
   1. Bewerk de configuratie van cloudservice en vervang **marketing.adobe.com** in het veld Tenant URL naar **experienceCloudservice.adobe.com**.
   1. Sla de configuratie op.
   1. Test de MAC-sync replicatieagenten.


1. Plak in het **[!UICONTROL Client ID]** veld de toepassings-id die u aan het einde van de procedure hebt gekopieerd. [Maak een toepassing](/help/sites-administering/configure-assets-cc-integration.md#create-an-application).

   ![Geef de waarden voor de toepassings-id op die vereist zijn voor de integratie van AEM Assets en Creative Cloud](assets/cloudservices_tenant_info.png)

1. Selecteer onder **[!UICONTROL Synchronization]** Selecteren **[!UICONTROL Enabled]** om synchronisatie in te schakelen en klik **[!UICONTROL OK]**.

   >[!NOTE]
   Als u **uitgeschakeld** selecteert, werkt de synchronisatie in één richting.

1. Van de configuratiepagina, klik **[!UICONTROL Display Public Key]** om de openbare sleutel te tonen die voor uw instantie wordt geproduceerd. U kunt ook klikken **[!UICONTROL Download Public Key for OAuth Gateway]** om het bestand met de openbare sleutel te downloaden. Open vervolgens het bestand om de openbare sleutel weer te geven.

## Synchronisatie inschakelen {#enable-synchronization}

1. Toon de openbare sleutel gebruikend één van de volgende methodes die in de laatste stap van de procedure worden vermeld [voeg een nieuwe configuratie aan Marketing Cloud](/help/sites-administering/configure-assets-cc-integration.md#add-a-new-configuration-to-marketing-cloud)toe. Klik op **[!UICONTROL Display Public Key]**.

   ![chlimage_1-52](assets/chlimage_1-52.png)

1. Kopieer de openbare sleutel en plak het in het **[!UICONTROL Public Key]** gebied van configuratieinterface van de toepassing u in [Create een toepassing](/help/sites-administering/configure-assets-cc-integration.md#create-an-application)creeerde.

   ![chlimage_1-53](assets/chlimage_1-53.png)

1. Klik op **[!UICONTROL Update]**. Synchroniseer uw elementen nu met de instantie AEM Assets.

## Synchronisatie testen {#test-the-synchronization}

1. Klik op het AEM-logo in de gebruikersinterface van uw lokale AEM Assets en navigeer naar **[!UICONTROL Tools]**> **[!UICONTROL Deployment]**> **[!UICONTROL Replication]**om de replicatieprofielen te zoeken die voor synchronisatie zijn gemaakt.
1. Ga naar de pagina **[!UICONTROL Replication]** en klik op **[!UICONTROL Agents on author]**.
1. Klik in de lijst met profielen op het standaard replicatieprofiel voor uw organisatie om dit te openen.
1. Klik in het dialoogvenster op **[!UICONTROL Test Connection]**.

   ![Verbinding testen en standaardreplicatieprofiel voor uw organisatie instellen](assets/chlimage_1-54.png)

1. Wanneer de replicatierest voltooit, controleer een succesbericht aan het eind van de testresultaten.

## Gebruikers toevoegen aan Marketing Cloud {#add-users-to-marketing-cloud}

1. Meld u aan bij de Marketing Cloud met beheerdersreferenties.
1. Ga vanaf de rails naar **[!UICONTROL Administration]** en klik/tik op **[!UICONTROL Launch Enterprise Dashboard]**.
1. Klik vanaf de rails **[!UICONTROL Users]** om de **[!UICONTROL User Management]** pagina te openen.
1. Klik op de werkbalk op **Toevoegen** /Tikken ![naam_elementen_add_icon](assets/aem_assets_add_icon.png).
1. Voeg een of meer gebruikers toe die u de mogelijkheid wilt bieden elementen te delen met Creative Cloud.

   >[!NOTE]
   Alleen de gebruikers die u aan de Marketing Cloud toevoegt, kunnen elementen delen van AEM Assets naar Creative Cloud.

## Wisselmiddelen tussen AEM Assets en Marketing Cloud {#exchange-assets-between-aem-assets-and-marketing-cloud}

1. Meld u aan bij AEM Assets.
1. Maak een map in de middelenconsole en upload enkele bestanden naar deze map. Maak bijvoorbeeld een map **mc-demo** en upload er middelen aan.
1. Selecteer de map en klik op **Share** ![assets_share](assets/assets_share.png).
1. Selecteer en klik in het menu op **[!UICONTROL Adobe Marketing Cloud]** **[!UICONTROL Share]**. Een bericht meldt dat de map wordt gedeeld met Marketing Cloud.

   ![chlimage_1-55](assets/chlimage_1-55.png)

   >[!NOTE]
   Het delen van een map Middelen van het type `sling:OrderedFolder`wordt niet ondersteund bij het delen in Adobe Marketing Cloud. Als u een map wilt delen, moet u deze bij het maken in AEM Assets niet selecteren. **[!UICONTROL Ordered]**

1. Vernieuw de gebruikersinterface van AEM Assets. De map die u hebt gemaakt in de middelenconsole van uw lokale AEM Assets-instantie, wordt gekopieerd naar de gebruikersinterface van de Marketing Cloud. Het element dat u in AEM Assets naar de map uploadt, wordt in de kopie van de map in Marketing Cloud weergegeven nadat deze door de AEM server is verwerkt.
1. U kunt ook elementen uploaden in de gekopieerde kopie van de map in Marketing Cloud. Nadat het middel is verwerkt, wordt het element in AEM Assets weergegeven in de gedeelde map.

## Wisselmiddelen tussen AEM Assets en Creative Cloud {#exchange-assets-between-aem-assets-and-creative-cloud}

>[!CAUTION]
De functie Mappen delen AEM naar Creative Cloud is vervangen. Klanten wordt ten zeerste aangeraden nieuwere mogelijkheden te gebruiken, zoals [Adobe Asset Link](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html) of [AEM desktop app](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app.html). Leer meer in [AEM en de Beste praktijken](/help/assets/aem-cc-integration-best-practices.md)van de Integratie van Creative Cloud.

Met AEM Assets kunt u mappen met elementen delen met Adobe Creative Cloud-gebruikers.

1. Selecteer in de middelenconsole de map die u wilt delen met Creative Cloud.
1. Klik op **[!UICONTROL Share]** assets_share ![](assets/assets_share.png)op de werkbalk.
1. Selecteer de **[!UICONTROL Adobe Creative Cloud]** optie in de lijst.

   >[!NOTE]
   De opties zijn beschikbaar voor gebruikers met leesmachtigingen in de hoofdmap. De gebruikers moeten de vereiste toestemming hebben om tot de informatie van de replicatieagent van Marketing Cloud toegang te hebben.

1. Voeg op de **[!UICONTROL Creative Cloud Sharing]** pagina de gebruiker toe om de map te delen met en kies een rol voor de gebruiker. Klik **[!UICONTROL Save]** en klik **[!UICONTROL OK]**.

1. Meld u aan bij Creative Cloud met de gegevens van de gebruiker met wie u de map hebt gedeeld. De gedeelde map is beschikbaar in Creative Cloud.

De synchronisatie tussen AEM Assets en Marketing Cloud is zodanig ontworpen dat de instantie van de gebruikersmachine van waaruit het element is geüpload het recht behoudt om het element te wijzigen. Alleen deze wijzigingen worden doorgegeven aan de andere instantie.

Als een element bijvoorbeeld wordt geüpload vanaf een instantie AEM Assets (in een gebouw), worden de wijzigingen in het element van deze instantie doorgegeven aan de instantie Marketing Cloud. De wijzigingen die zijn doorgevoerd van de instantie Marketing Cloud naar hetzelfde element, worden echter niet doorgegeven aan de instantie AEM en andersom voor elementen die zijn geüpload uit Marketing Cloud.

>[!MORELIKETHIS]
* [Aanbevolen werkwijzen voor AEM en Creative Cloud-integratie](/help/assets/aem-cc-integration-best-practices.md)
* [Aanbevolen werkwijzen voor het delen van mappen AEM naar Creative Cloud](/help/assets/aem-cc-folder-sharing-best-practices.md)

