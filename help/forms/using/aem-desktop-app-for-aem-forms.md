---
title: AEM-bureaubladtoepassing voor AEM-formulieren
seo-title: AEM-bureaubladtoepassing voor AEM-formulieren
description: 'null'
seo-description: 'null'
uuid: 99e0f2fb-8623-45bb-8e2e-5c5d6f482366
contentOwner: khsingh
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: manage
discoiquuid: c30332b6-e012-442d-8e84-28832c116c7b
noindex: true
translation-type: tm+mt
source-git-commit: 6fa293028332596bb93013119b4339c7721eb536

---


# AEM-bureaubladtoepassing voor AEM-formulieren {#aem-desktop-app-for-aem-forms}

Met de AEM-bureaubladtoepassing kunt u de gegevensopslagplaats van Adobe Experience Manager (AEM) en de binaire bestanden van AEM Forms toewijzen aan een netwerkmap op uw systeem. U kunt de gesynchroniseerde elementen en binaire bestanden weergeven in een bestandsverkenner en verschillende apps gebruiken om de bestanden naar wens te bewerken. Behalve het bekijken van de bestanden kunt u ook binaire bestanden maken, uploaden en verwijderen. U kunt bestanden ook rechtstreeks vanuit de software openen, bewerken en opslaan. U kunt bijvoorbeeld een XDP-bestand rechtstreeks vanuit Designer openen en bewerken. De wijzigingen die u lokaal aanbrengt in de elementen worden weerspiegeld in de AEM Assets-opslagplaats en de gebruikersinterface van AEM Forms.

U kunt de app downloaden van een AEM-instantie. Zie Opmerkingen bij de release van de [AEM-bureaubladtoepassing voor meer informatie over het downloaden van de app](https://helpx.adobe.com/experience-manager/desktop-app/release-notes.html).

## AEM Forms-middelen die worden ondersteund in de AEM-bureaubladtoepassing {#aem-forms-assets-supported-in-aem-desktop-app}

Met de app kunt u binaire bestanden met AEM Forms synchroniseren van het type Form Templates (.xdp), PDF Form (.pdf), Document (.pdf), Images, XML Schema (.xsd), stijlpagina&#39;s (.xfs). In de app worden alle andere bestanden (niet-ondersteunde bestanden) weergegeven als bestanden van 0 byte. Door niet-ondersteunde bestanden als 0-byte bestanden te vermelden, weet de gebruiker zeker dat er andere middelen beschikbaar zijn op de AEM Forms-server.

>[!NOTE]
>
>Een bestandsnaam mag alleen alfanumerieke tekens, afbreekstreepjes of onderstrepingstekens bevatten.

## AEM-formulieren inschakelen voor AEM-bureaubladtoepassing {#enable-aem-forms-for-aem-desktop-app}

AEM-bureaubladtoepassing gebruikt WebDAV-protocol in Microsoft Windows en SMB1 in Mac OS X om verbinding te maken met een AEM Forms-server. Uit de doos, wordt de server van Vormen AEM niet toegelaten om binaire dossiers en andere activa met een cliënt te synchroniseren WebDAV of SMB. Voer de volgende stappen uit om AEM Forms voor AEM Desktop App in te schakelen:

1. Meld u als beheerder aan bij AEM Forms.
1. Klik in de auteurinstantie op ![adobeexperienceManager](assets/adobeexperiencemanager.png) **[!UICONTROL Adobe Experience Manager > Tools **![hammer](assets/hammer.png)> Deployment > Operations > Web Console**]**. De webconsole wordt in een nieuw venster geopend.
1. Zoek en open de optie **[!UICONTROL FormsManager AddOn Configuration]** in het venster Webconsole.
1. Schakel in het dialoogvenster FormsManager AddOn-configuratie het selectievakje Bronnen **[!UICONTROL asynchroon synchroniseren uit en klik op]** Opslaan ****.
1. Start de AEM Forms-server opnieuw. Nadat u de computer opnieuw hebt opgestart, kan de AEM Forms-server inhoud accepteren en delen met de AEM-bureaubladtoepassing.
1. Open de app en maak verbinding met de AEM Forms-server.

   Wanneer de verbinding tot stand is gebracht, worden de `content/dam` mappen en `content/dam/formsanddocuments` mappen ingevuld. U kunt de app gebruiken om bestanden van de bovenliggende mappen naar lokale mappen te verplaatsen en omgekeerd, en om inhoud tussen automatisch gevulde mappen te verplaatsen.

