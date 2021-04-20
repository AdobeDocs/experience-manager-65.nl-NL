---
title: AEM Assets-integratie configureren met Experience Cloud
description: Leer hoe u AEM Assets-integratie met Experience Cloud configureert.
contentOwner: AG
feature: Asset Management
role: Business Practitioner, Architect, Administrator
translation-type: tm+mt
source-git-commit: a9c9194ac1d163be3ab642ab5a6323de02d67363
workflow-type: tm+mt
source-wordcount: '920'
ht-degree: 1%

---


# AEM Assets-integratie configureren met Experience Cloud {#configure-aem-assets-integration-with-experience-cloud-and-creative-cloud}

Als u een Adobe Experience Cloud-klant bent, kunt u uw middelen in Adobe Experience Manager Assets synchroniseren met Adobe Creative Cloud en andersom. U kunt uw elementen ook synchroniseren met Experience Cloud en andersom. U kunt deze synchronisatie instellen via [!DNL Adobe I/O]. De bijgewerkte naam van [!DNL Adobe Marketing Cloud] is [!DNL Adobe Experience Cloud].

De workflow voor het instellen van deze integratie is:

1. Creeer een authentificatie in [!DNL Adobe I/O] gebruikend een openbare gateway en krijg toepassingsidentiteitskaart
1. Maak een profiel op uw AEM Assets-instantie met de toepassings-id.
1. Gebruik deze configuratie om uw elementen te synchroniseren.

Op de achtergrond, verifieert de AEM server uw profiel met de gateway en synchroniseert dan de gegevens tussen Middelen en Experience Cloud.

>[!NOTE]
>
>Deze functie is afgekeurd in AEM Assets. Vind vervangingen in [AEM en de beste praktijken van de Integratie van de Creative Cloud](/help/assets/aem-cc-integration-best-practices.md). Als u vragen hebt, [neem contact op met de klantenservice van Adobe](https://www.adobe.com/account/sign-in.supportportal.html).

<!-- Hiding this for now via cqdoc-16834.
![Flow of data when AEM Assets and Creative Cloud are integrated](assets/chlimage_1-48.png)

>[!NOTE]
>
>Sharing assets between Adobe Experience Cloud and Adobe Creative Cloud requires administrator privileges on the AEM instance.
-->

## Een toepassing {#create-an-application} maken

1. Heb toegang tot de de gatewayinterface van de Ontwikkelaar van Adobe door het programma te openen bij [https://legacy-oauth.cloud.adobe.io](https://legacy-oauth.cloud.adobe.io/).

   >[!NOTE]
   >
   >U hebt beheerdersrechten nodig om een toepassings-id te maken.

1. Navigeer in het linkervenster naar **[!UICONTROL Developer Tools]** > **[!UICONTROL Applications]** om een lijst met toepassingen weer te geven.
1. Klik **[!UICONTROL Add]** ![name_assets_addcircle_icon](assets/aem_assets_addcircle_icon.png) om een toepassing te maken.
1. Selecteer **[!UICONTROL Service Account (JWT Assertion)]** in de lijst **[!UICONTROL Client Credentials]**. Dit is een server-naar-server communicatieservice voor serververificatie.

   ![chlimage_1-49](assets/chlimage_1-49.png)

1. Geef een naam voor de toepassing en een optionele beschrijving op.
1. Selecteer in de lijst **[!UICONTROL Organization]** de organisatie waarvoor u elementen wilt synchroniseren.
1. Selecteer **[!UICONTROL Scope]** in de lijst **[!UICONTROL dam-read]**, **[!UICONTROL dam-sync]**, **[!UICONTROL dam-write]** en **[!UICONTROL cc-share]**.
1. Klik op **[!UICONTROL Create]**. Een bericht meldt dat de toepassing is gemaakt.

   ![Melding van het feit dat de toepassing is gemaakt om AEM Assets te integreren met Adobe CC](assets/chlimage_1-50.png)

1. Kopieer **[!UICONTROL Application ID]** die voor de nieuwe toepassing wordt geproduceerd.

   >[!CAUTION]
   >
   >Zorg ervoor dat u niet per ongeluk **[!UICONTROL Application Secret]** in plaats van **[!UICONTROL Application ID]** kopieert.

## Nieuwe configuratie toevoegen aan Experience Cloud {#add-a-new-configuration}

1. Klik op het AEM logo in de gebruikersinterface van uw lokale AEM Assets-instantie en navigeer naar **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Legacy Cloud Services]**.

1. Zoek de **[!UICONTROL Adobe Experience Cloud]**-service. Als er geen configuraties bestaan, klikt u op **[!UICONTROL Configure Now]**. Als configuraties bestaan, klik **[!UICONTROL Show Configurations]** en klik `+` om een nieuwe configuratie toe te voegen.

   >[!NOTE]
   >
   >Gebruik een Adobe ID-account met beheerdersrechten voor de organisatie.

1. Geef in het dialoogvenster **[!UICONTROL Create Configuration]** een titel en naam voor de nieuwe configuratie op en klik op **[!UICONTROL Create]**.

   ![Geef een nieuwe configuratie de naam om AEM Assets en CC te integreren](assets/aem-ec-integration-config1.png)

1. Geef in het veld **[!UICONTROL Tenant URL]** de URL voor AEM Assets op. Als de URL in het verleden is gedefinieerd als `https://<tenant_id>.marketing.adobe.com`, wijzigt u deze in `https://<tenant_id>.experiencecloud.adobe.com`.

   1. Navigeer naar **Gereedschappen > Cloud Services > Oudere Cloud Services**. Klik onder Adobe Experience Cloud op **Configuraties tonen**.
   1. Selecteer de bestaande configuratie die u wilt bewerken. Bewerk de configuratie en vervang `marketing.adobe.com` naar `experiencecloud.adobe.com`.
   1. Sla de configuratie op. Test de MAC-sync replicatieagenten.

1. Plak in het veld **[!UICONTROL Client ID]** de toepassings-id die u aan het einde van de procedure hebt gekopieerd [een toepassing maken](#create-an-application).

   ![Geef de waarden voor de toepassings-id op die vereist zijn voor de integratie van AEM Assets en Creative Cloud](assets/cloudservices_tenant_info.png)

1. Selecteer **[!UICONTROL Synchronization]** onder **[!UICONTROL Enabled]** om synchronisatie in te schakelen en klik **[!UICONTROL OK]**. Als u **disabled** selecteert, werkt de synchronisatie in één richting.

1. Van de configuratiepagina, klik **[!UICONTROL Display Public Key]** om de openbare sleutel te tonen die voor uw instantie wordt geproduceerd. U kunt ook op **[!UICONTROL Download Public Key for OAuth Gateway]** klikken om het bestand met de openbare sleutel te downloaden. Open vervolgens het bestand om de openbare sleutel weer te geven.

## Synchronisatie {#enable-synchronization} inschakelen

1. Toon de openbare sleutel gebruikend één van de volgende methodes die in de laatste stap van de procedure [worden vermeld voeg een nieuwe configuratie aan Experience Cloud ](#add-a-new-configuration) toe. Klik op **[!UICONTROL Display Public Key]**.

1. Kopieer de openbare sleutel en plak het in het **[!UICONTROL Public Key]** gebied van configuratieinterface van de toepassing u in [creeerde een toepassing ](#create-an-application).

   ![chlimage_1-53](assets/chlimage_1-53.png)

1. Klik op **[!UICONTROL Update]**. Synchroniseer uw elementen nu met de AEM Assets-instantie.

## Synchronisatie {#test-the-synchronization} testen

1. Klik op het AEM-logo in de gebruikersinterface van uw lokale AEM Assets-exemplaar en navigeer naar **[!UICONTROL Tools]** **[!UICONTROL Deployment]** **[!UICONTROL Replication]**om de replicatieprofielen te zoeken die voor synchronisatie zijn gemaakt.
1. Ga naar de pagina **[!UICONTROL Replication]** en klik op **[!UICONTROL Agents on author]**.
1. Klik in de lijst met profielen op het standaard replicatieprofiel voor uw organisatie om dit te openen.
1. Klik in het dialoogvenster op **[!UICONTROL Test Connection]**.

   ![Verbinding testen en standaardreplicatieprofiel voor uw organisatie instellen](assets/chlimage_1-54.png)

1. Wanneer de replicatierest voltooit, controleer een succesbericht aan het eind van de testresultaten.

## Gebruikers toevoegen aan Experience Cloud {#add-users-to-experience-cloud}

1. Meld u met beheerdersreferenties aan bij Experience Cloud.
1. Ga vanaf de rails naar **[!UICONTROL Administration]** en klik vervolgens op **[!UICONTROL Launch Enterprise Dashboard]**.
1. Klik in de track op **[!UICONTROL Users]** om de pagina **[!UICONTROL User Management]** te openen.
1. Klik op **Add** ![aem_assets_add_icon](assets/aem_assets_add_icon.png) op de werkbalk.
1. Voeg een of meer gebruikers toe die u de mogelijkheid wilt bieden elementen te delen met Creative Cloud.

<!-- TBD: Check.
   >[!NOTE]
   >
   >Only the users that you add to Experience Cloud can share assets from AEM Assets to Creative Cloud.

-->

## Wisselmiddelen tussen AEM Assets en Experience Cloud {#exchange-assets-between-aem-and-experience-cloud}

1. Meld u aan bij AEM Assets.
1. Maak een map in de middelenconsole en upload enkele bestanden naar deze map. Maak bijvoorbeeld een map **mc-demo** en upload er een element naar.
1. Selecteer de map en klik op **Delen** ![assets_share](assets/do-not-localize/assets_share.png).
1. Selecteer **[!UICONTROL Adobe Experience Cloud]** in het menu en klik **[!UICONTROL Share]**. Een bericht meldt dat de map wordt gedeeld met Experience Cloud.

   >[!NOTE]
   >
   >Het delen van een map Middelen van het type `sling:OrderedFolder` wordt niet ondersteund in de context van delen in Adobe Experience Cloud. Als u een map wilt delen, moet u bij het maken ervan in AEM Assets de optie **[!UICONTROL Ordered]** niet selecteren.

1. Vernieuw de AEM Assets-gebruikersinterface. De map die u in de middelenconsole van uw lokale AEM Assets-instantie hebt gemaakt, wordt gekopieerd naar de gebruikersinterface van de Experience Cloud. Het middel dat u uploadt naar de omslag in AEM Assets verschijnt in het exemplaar van de omslag in Experience Cloud nadat het door de AEM server wordt verwerkt.
1. U kunt ook elementen uploaden in de gekopieerde kopie van de map in Experience Cloud. Nadat het element is verwerkt, wordt het in de gedeelde map in AEM Assets weergegeven.

<!-- Removing as per PM guidance via https://jira.corp.adobe.com/browse/CQDOC-16834?focusedCommentId=22881523&page=com.atlassian.jira.plugin.system.issuetabpanels:comment-tabpanel#comment-22881523.

## Exchange assets between AEM Assets and Creative Cloud {#exchange-assets-between-aem-assets-and-creative-cloud}

>[!CAUTION]
>
>The AEM to Creative Cloud Folder Sharing feature is deprecated. Customers are strongly advised to use newer capabilities, like [Adobe Asset Link](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html) or [AEM desktop app](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app.html). Learn more in [AEM and Creative Cloud Integration Best Practices](/help/assets/aem-cc-integration-best-practices.md).

AEM Assets lets you share folders containing assets with Adobe Creative Cloud users.

1. In the Assets console, select the folder to share with Creative Cloud.
1. From the toolbar, click **[!UICONTROL Share]** ![assets_share](assets/do-not-localize/assets_share.png).
1. From the list, select the **[!UICONTROL Adobe Creative Cloud]** option.

   >[!NOTE]
   >
   >The options are available for users with read permissions on the root. Users must have the required permission to access the replication agent information of Marketing Cloud.

1. In the **[!UICONTROL Creative Cloud Sharing]** page, add the user to share the folder with and choose a role for the user. Click **[!UICONTROL Save]** and click **[!UICONTROL OK]**.

1. Log on to Creative Cloud with the credentials of the user you shared the folder with. The shared folder is available in Creative Cloud.

The AEM Assets-Marketing Cloud synchronization is designed in a way that the user machine instance from where the asset is uploaded retains the right to modify the asset. Only these changes are propagated to the other instance.

For example, if an asset is uploaded from an AEM Assets (on premises) instance, the changes to the asset from this instance are propagated to the Marketing Cloud instance. However, the changes done from the Marketing Cloud instance to the same asset aren’t propagated to the AEM instance and vice versa for asset uploaded from Marketing Cloud.
-->

>[!MORELIKETHIS]
>
>* [Aanbevolen werkwijzen voor het integreren van middelen en Creative Cloud](/help/assets/aem-cc-integration-best-practices.md)
>* [Middelen naar Creative Cloud-map die aanbevolen werkwijzen deelt](/help/assets/aem-cc-folder-sharing-best-practices.md)

