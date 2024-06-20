---
title: Adobe Experience Manager (AEM) desktop app voor AEM Forms
description: Adobe Experience Manager (AEM) desktop app voor AEM Forms
contentOwner: khsingh
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: manage
noindex: true
role: Admin,User
exl-id: b87e07b1-4a19-4888-bad0-c0f5327b9ad3
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
source-git-commit: 539da06db98395ae6eaee8103a3e4b31204abbb8
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# Adobe Experience Manager (AEM) desktop app voor AEM Forms {#aem-desktop-app-for-aem-forms}

Met AEM bureaubladtoepassing kunt u de gegevensopslagruimte van Adobe Experience Manager (AEM) en de binaire bestanden van AEM Forms toewijzen aan een netwerkmap op uw systeem. U kunt de gesynchroniseerde elementen en binaire bestanden weergeven in een bestandsverkenner en verschillende apps gebruiken om de bestanden naar wens te bewerken. Behalve het bekijken van de bestanden kunt u ook binaire bestanden maken, uploaden en verwijderen. U kunt bestanden ook rechtstreeks vanuit de software openen, bewerken en opslaan. U kunt bijvoorbeeld een XDP-bestand rechtstreeks vanuit Designer openen en bewerken. De wijzigingen die u lokaal aanbrengt in de elementen worden weerspiegeld in de AEM Assets-opslagplaats en de AEM Forms-gebruikersinterface.

U kunt de app downloaden van een AEM. Ga voor gedetailleerde informatie over het downloaden van de app naar [Opmerkingen bij de release AEM bureaubladtoepassing](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/release-notes.html?lang=en).

## AEM Forms-middelen die worden ondersteund in AEM bureaubladtoepassing {#aem-forms-assets-supported-in-aem-desktop-app}

Met de app kunt u binaire bestanden van het type AEM Forms synchroniseren met het type Form Templates (.xdp), PDF Form (.pdf), Document (.pdf), Images, XML-schema (.xsd), stijlpagina&#39;s (.xfs). In de app worden alle andere bestanden (niet-ondersteunde bestanden) weergegeven als bestanden van 0 byte. Door niet-ondersteunde bestanden als 0-bytebestanden te vermelden, weet de gebruiker zeker dat er andere middelen op de AEM Forms-server beschikbaar zijn.

>[!NOTE]
>
>Een bestandsnaam mag alleen alfanumerieke tekens, afbreekstreepjes of onderstrepingstekens bevatten.

## AEM Forms inschakelen voor AEM bureaubladtoepassing {#enable-aem-forms-for-aem-desktop-app}

AEM desktop app gebruikt WebDAV-protocol op Microsoft® Windows en SMB1 op macOS X om verbinding te maken met een AEM Forms Server. De AEM Forms-server is niet in staat om binaire bestanden en andere elementen te synchroniseren met een WebDAV- of SMB-client. Voer de volgende stappen uit zodat u AEM Forms for AEM desktop app kunt inschakelen:

1. Meld u als beheerder aan bij AEM Forms.
1. Klik in de auteur-instantie op ![adobeexperienceManager](assets/adobeexperiencemanager.png) **[!UICONTROL Adobe Experience Manager > Tools]** ![hamer](assets/hammer.png) **[!UICONTROL > Deployment > Operations > Web Console]**. De webconsole wordt in een nieuw venster geopend.
1. Zoek in het venster Webconsole de **[!UICONTROL FormsManager AddOn Configuration]** -optie.
1. Schakel in het dialoogvenster FormsManager AddOn-configuratie de optie **[!UICONTROL Asynchronously Sync Resources]** en klik op **[!UICONTROL Save]**.
1. Start de AEM Forms-server opnieuw. Nadat u de computer opnieuw hebt opgestart, kan de AEM Forms-server inhoud accepteren en delen met de AEM-bureaubladtoepassing.
1. Open de toepassing en maak verbinding met de AEM Forms-server.

   >[!NOTE]
   >
   > Het wordt aanbevolen de SDK opnieuw te starten met de opdracht &#39;Ctrl + C&#39;. Het opnieuw opstarten van de AEM SDK met behulp van alternatieve methoden, bijvoorbeeld het stoppen van Java-processen, kan leiden tot inconsistenties in de AEM ontwikkelomgeving.

   Wanneer de verbinding tot stand is gebracht, wordt de toepassing gevuld met de `content/dam` en `content/dam/formsanddocuments` mappen. Samen met het verplaatsen van bestanden van boven naar lokale mappen en omgekeerd kunt u de app gebruiken om inhoud te verplaatsen tussen automatisch gevulde mappen.
