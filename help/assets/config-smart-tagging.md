---
title: Asset tagging configureren met behulp van de Smart Content Service
description: Leer hoe u slimme tags en verbeterde slimme tags kunt configureren in AEM met behulp van de Smart Content Service.
contentOwner: AG
translation-type: tm+mt
source-git-commit: c7d0bcbf39adfc7dfd01742651589efb72959603

---


# Asset tagging configureren met behulp van de Smart Content Service {#configure-asset-tagging-using-the-smart-content-service}

U kunt Adobe Experience Manager (AEM) met de Smart Content Service integreren met behulp van Adobe I/O. Gebruik deze configuratie om tot de Slimme Dienst van de Inhoud van binnen AEM toegang te hebben.

Het artikel detailleert de volgende zeer belangrijke taken uit die worden vereist om de Slimme Dienst van de Inhoud te vormen. Aan de achterkant verifieert de AEM-server uw servicegegevens met de Adobe IO-gateway voordat uw verzoek naar de Smart Content Service wordt doorgestuurd.

* Creeer een Slimme configuratie van de Dienst van de Inhoud in AEM om een openbare sleutel te produceren. Overheidscertificaat verkrijgen voor OAuth-integratie.
* Maak een integratie in Adobe I/O en upload de gegenereerde openbare sleutel.
* Configureer uw AEM-instantie met behulp van de API-sleutel en andere referenties van Adobe I/O.
* Schakel eventueel automatische labeling in bij het uploaden van elementen.

## Vereisten {#prerequisites}

Voordat u de Smart Content Service kunt gebruiken, moet u het volgende doen om een integratie in de Adobe I/O te maken:

* Een Adobe-id-account met beheerdersrechten voor de organisatie.
* De service Smart Content Service is ingeschakeld voor uw organisatie.

## Openbaar certificaat verkrijgen {#obtain-public-certificate}

Met een openbaar certificaat kunt u uw profiel verifiëren op Adobe I/O.

1. Klik in de AEM-gebruikersinterface op het AEM-logo en ga naar **[!UICONTROL Gereedschappen > Cloud Services]**> **[!UICONTROL Oudere Cloud Services]**.

1. Klik op de pagina Cloud Services op **[!UICONTROL Nu]** configureren onder Slimme tags voor **[!UICONTROL middelen]**.
1. Geef in het dialoogvenster Configuratie **** maken een titel en naam op voor de configuratie Slimme tags. Klik op **[!UICONTROL Maken]**.
1. Gebruik de volgende waarden in het dialoogvenster **[!UICONTROL AEM Smart Content Service]** :

   **[!UICONTROL Service-URL]**: `https://mc.adobe.io/marketingcloud/smartcontent`

   **[!UICONTROL Autorisatieserver]**: `https://ims-na1.adobelogin.com`

   Laat de overige velden voorlopig leeg (later te verstrekken). Click **[!UICONTROL OK]**.

   ![Dialoogvenster van de AEM Smart Content Service voor het aanbieden van de inhoudsservice-URL](assets/aem_scs.png)

1. Klik op Openbaar certificaat **[!UICONTROL downloaden voor OAuth Integration]** en download het openbare certificaatbestand `AEM-SmartTags.crt`.

   ![Een voorstelling van de instellingen die voor de service voor slimme tags zijn gemaakt](assets/download_link.png)

### Opnieuw configureren wanneer een certificaat verloopt {#certrenew}

Wanneer het certificaat verloopt, wordt het niet meer vertrouwd. Voer de volgende stappen uit om een nieuw certificaat toe te voegen. U kunt een verlopen certificaat niet vernieuwen.

1. Meld u aan bij uw AEM-implementatie als beheerder. Klik op **[!UICONTROL Gereedschappen]** > **[!UICONTROL Beveiliging]** > **[!UICONTROL Gebruikers]**.

1. Zoek en klik op **[!UICONTROL dam-update-service]** -gebruiker. Klik op het tabblad **[!UICONTROL Keystore]** .
1. Verwijder het bestaande sleutelarchief voor **[!UICONTROL gelijkenissen]** met het verlopen certificaat. Klik op **[!UICONTROL Opslaan en sluiten]**.

   ![Bestaande vermelding voor zoeken op basis van overeenkomst in sleutelarchief verwijderen om een nieuw beveiligingscertificaat toe te voegen](assets/smarttags_delete_similaritysearch_keystore.png)

   Bestaande vermelding voor zoeken op basis van overeenkomst in sleutelarchief verwijderen om een nieuw beveiligingscertificaat toe te voegen

1. Ga naar **[!UICONTROL Gereedschappen]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Oudere cloudservices]**. Klik op Slimme tags voor **[!UICONTROL middelen]** > **[!UICONTROL Configuratie]** tonen > **[!UICONTROL Beschikbare configuraties]**. Klik op de gewenste configuratie.

1. Als u een openbaar certificaat wilt downloaden, klikt u op Openbaar certificaat **[!UICONTROL downloaden voor OAuth-integratie]**.
1. Ga naar [https://console.adobe.io](https://console.adobe.io) en navigeer naar de bestaande Smart Content Services op de pagina **[!UICONTROL Integrations]** . Upload het nieuwe certificaat. Zie de instructies in Adobe I/O-integratie [](#create-adobe-i-o-integration)maken voor meer informatie.

## Adobe I/O-integratie maken {#create-adobe-i-o-integration}

Als u API&#39;s voor Smart Content Service wilt gebruiken, maakt u een integratie in Adobe I/O om API-sleutel, technische account-id, organisatie-id en clientgeheim te genereren.

1. Ga naar [https://console.adobe.io](https://console.adobe.io/).
1. Voor de pagina van **[!UICONTROL Integraties]** , selecteer de aangewezen rekening en verifieer dat de bijbehorende organisatierol systeembeheerder is.
1. Klik op **[!UICONTROL Nieuwe integratie]**.
1. Selecteer **[!UICONTROL Toegang tot een API]** op de **[!UICONTROL pagina Een nieuwe integratie]** maken. Klik op **[!UICONTROL Doorgaan]**.
1. Selecteer onder **[!UICONTROL Experience Cloud]** de optie **[!UICONTROL Slimme inhoud]**. Klik op **[!UICONTROL Doorgaan]**.

   ![Selecteer bij het maken van een nieuwe integratie de optie Slimme inhoud onder Experience Cloud met de beschikbare opties](assets/smart_content.png)

1. Selecteer **[!UICONTROL Nieuwe integratie]** op de volgende pagina. Klik op **[!UICONTROL Doorgaan]**.
1. Voor de pagina van de Details **[!UICONTROL van de]** Integratie, specificeer een naam voor de integratiesgateway en voeg een beschrijving toe.
1. Upload in de certificaten **[!UICONTROL met]** openbare sleutels `AEM-SmartTags.crt` het bestand dat u hierboven hebt gedownload.
1. Klik op **[!UICONTROL Integratie]** maken.
1. Klik op **[!UICONTROL Doorgaan naar integratiegegevens]** om de integratiegegevens weer te geven.

   ![Op het tabblad Overzicht kunt u de informatie bekijken die voor integratie is opgegeven.](assets/integration_details.png)

## Smart Content Service configureren {#configure-smart-content-service}

Als u de integratie wilt configureren, gebruikt u de waarden Technical Account ID, Organization ID, Client Secret, Authorization Server en API-sleutelvelden van de Adobe I/O-integratie. Door een cloud-configuratie met slimme tags te maken, kunnen API-aanvragen van de AEM-instantie worden geverifieerd.

1. Navigeer in Experience Manager naar **[!UICONTROL Extra > Cloud Service > Legacy Cloud Services]** om de [!UICONTROL Cloud Services] -console te openen.
1. Open de hierboven gemaakte configuratie onder Slimme **[!UICONTROL elementtags]**. Klik op de pagina met service-instellingen op **[!UICONTROL Bewerken]**.
1. Gebruik in het dialoogvenster **[!UICONTROL AEM Smart Content Service]** de vooraf ingevulde waarden voor de velden **[!UICONTROL Service URL]** en **[!UICONTROL Authorization Server]** .
1. Voor de velden **[!UICONTROL API Key]**, **[!UICONTROL Technical Account Id]**, **[!UICONTROL Organization Id]** en **[!UICONTROL Client Secret]** gebruikt u de hierboven gegenereerde waarden.

## De configuratie valideren {#validate-the-configuration}

Nadat u de configuratie hebt voltooid, kunt u een JMX MBean gebruiken om de configuratie te bevestigen. Voer de volgende stappen uit om te valideren.

1. Open uw AEM-server op `https://[server]:[port]`.

1. Ga naar **[!UICONTROL Hulpmiddelen > Verrichtingen > de Console]** van het Web om de console te openen OSGi. Klik op **[!UICONTROL Hoofd > JMX]**.
1. Klik op **[!UICONTROL com.day.cq.dam.similaritysearch.internal.impl]**. Het opent **[!UICONTROL GelijksoortigheidOnderzoek Diverse Taken.]**
1. Klik op **[!UICONTROL validateConfigs()]**. Klik in het dialoogvenster **[!UICONTROL Configuraties]** valideren op **[!UICONTROL Invoke]**.

   Het validatieresultaat wordt in hetzelfde dialoogvenster weergegeven.

## Slimme tags toepassen inschakelen in de workflow Element bijwerken (optioneel) {#enable-smart-tagging-in-the-update-asset-workflow-optional}

1. Ga in Experience Manager naar **[!UICONTROL Extra > Workflow > Modellen]**.
1. Selecteer op de pagina **[!UICONTROL Workflowmodellen]** het workflowmodel **[!UICONTROL DAM Update Asset]** .
1. Klik op **[!UICONTROL Bewerken]** op de werkbalk.
1. Vouw het zijpaneel uit om de stappen weer te geven. Drag **[!UICONTROL Smart Tag Asset]** step that is available in the DAM Workflow section and place it after the **[!UICONTROL Process Thumbnails]** step.

   ![Voeg de stap Slimme tag-elementen toe na de stap met de miniaturen van het proces in de workflow [!UICONTROL DAM-element] bijwerken](assets/chlimage_1-105.png)

   *Afbeelding: Voeg de stap Slimme tag-elementen toe na de stap met de miniaturen van het proces in de workflow[!UICONTROL DAM-element]bijwerken*

1. Open de stap in de bewerkingsmodus. Controleer of onder **[!UICONTROL Geavanceerde instellingen]** de optie **[!UICONTROL Handler bevorderen]** is geselecteerd.

   ![chlimage_1-3](assets/chlimage_1-106.png)

1. Selecteer op het tabblad **[!UICONTROL Argumenten]** de optie **[!UICONTROL Fouten negeren]** als u wilt dat de workflow wordt voltooid, zelfs als de stap Automatisch taggen mislukt.

   ![chlimage_1-4](assets/chlimage_1-107.png)

   Als u elementen wilt labelen terwijl ze worden geüpload, ongeacht of slimme tags zijn ingeschakeld in mappen, selecteert u **[!UICONTROL Slimme tagmarkering]** negeren.

   ![chlimage_1-5](assets/chlimage_1-108.png)

1. Klik op **[!UICONTROL OK]** om de processtap te sluiten en sla de workflow op.

>[!MORELIKETHIS]
>
>* [Slimme tags beheren](managing-smart-tags.md)
>* [Overzicht van slimme tags en hoe deze kunnen worden getraind](enhanced-smart-tags.md)
>* [Richtlijnen en regels voor de opleiding van de Smart Content Service](smart-tags-training-guidelines.md)
>* [Videozelfstudie over het configureren van slimme tags](https://docs.adobe.com/content/help/en/experience-manager-learn/assets/metadata/smart-tags-technical-video-setup.html)

