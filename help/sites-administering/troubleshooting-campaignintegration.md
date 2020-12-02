---
title: Problemen met Adobe Campaign-integratie oplossen
seo-title: Problemen met Adobe Campaign-integratie oplossen
description: Leer hoe u problemen met de Adobe Campaign-integratie kunt oplossen.
seo-description: Leer hoe u problemen met de Adobe Campaign-integratie kunt oplossen.
uuid: 835ac2c3-ef2f-4963-9047-aeda3647b114
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
discoiquuid: b1d45f01-78de-423c-8f6b-5cb7067c3a2f
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '818'
ht-degree: 0%

---


# Problemen met de Adobe Campaign-integratie oplossen{#troubleshooting-your-adobe-campaign-integration}

>[!NOTE]
>
>Deze pagina is van toepassing op Campaign Classic.

De volgende tips voor het oplossen van problemen helpen u de meest voorkomende problemen op te lossen die u kunt tegenkomen wanneer u AEM met Adobe Campaign integreert:

## Algemene tips voor het oplossen van problemen {#general-troubleshooting-tips}

Voor beide integraties kunt u controleren of HTTP-aanroepen worden verzonden (AEM > Adobe Campaign, Adobe Campaign > AEM):

* Wanneer de integratie ontbreekt, zorg ervoor dat deze vraag op het andere eind aankomt (om firewall/SSL kwesties te vermijden).
* Voor AEM functionaliteit, zult u zien dat de verbindingsvraag van de AEM auteursinterface wordt gevraagd; deze moeten niet resulteren in een HTTP-500-fout. Als u HTTP-500 fouten ziet, controleer `error.log` voor meer informatie over dit.
* Het verhogen van zuivert niveau voor campagne-klassen in AEM helpt ook om kwesties problemen op te lossen.

## Als de verbinding {#if-the-connection-fails} mislukt

Controleer of u de **aemserver** exploitant in Adobe Campaign hebt gevormd.

## Als er geen afbeeldingen worden weergegeven in de Adobe Campaign-console {#if-images-do-not-appear-in-the-adobe-campaign-console}

Controleer de HTML-bron en controleer of u de URL kunt openen vanaf de clientcomputer. Als de URL localhost:4503 bevat, wijzigt u de configuratie van Day CQ Link Externalzer op de auteur om naar een publicatie-instantie te verwijzen die kan worden bereikt vanaf de Adobe Campaign-consolemachine.

Zie [Het vormen van Externalzer.](/help/sites-administering/campaignstandard.md#configuring-the-externalizer)

## Als u geen verbinding kunt maken van AEM naar Adobe Campaign {#if-you-cannot-connect-from-aem-to-adobe-campaign}

Zoek het volgende foutbericht in Adobe Campaign:

`No datasource defined in the instance 'default'.`

`Make sure the DNS alias used to access the server is correct (for example, avoid hard-coded IP addresses). (iRc=16384)`

U kunt dit probleem verhelpen door het volgende te wijzigen in **$CAMPAIGN_HOME/conf/config-&lt;instance-name>.xml**:

`<dataStore hosts="*" lang="en_GB">`

## Als er geen gegevens worden weergegeven in het dialoogvenster Adobe Campaign {#if-no-data-displays-in-the-adobe-campaign-dialog}

Zorg er in Adobe Campaign voor dat er na het poortnummer geen slash (/) achter het poortnummer staat.

![chlimage_1-149](assets/chlimage_1-149.png)

## Als u een waarschuwing over uw setlocale {#if-you-get-a-warning-about-your-setlocale} krijgt

Als u de Apache HTTPD-service start en de fout `"Warning: setlocale: LC_CTYPE cannot change locale"` ziet, moet u **en_CA.ISO-8859-15 locale** op uw systeem hebben geïnstalleerd.

U kunt controleren of het door `local -a` wordt geïnstalleerd te gebruiken. Als dit niet het geval is, kunt u het **/usr/local/neolane/nl6/env.sh**-script patcheren en de landinstelling wijzigen in een geïnstalleerd script.

## Als er een fout optreedt tijdens het compileren van script &#39;get_nms_amcGetSeedMetaData_jssp&#39; {#if-you-get-an-error-while-compiling-script-get-nms-amcgetseedmetadata-jssp}

Als u het volgende foutbericht ziet in het AEM logbestand:

`com.day.cq.mcm.campaign.impl.CampaignConnectorImpl Internal Adobe Campaign error: response body is Error while compiling script 'get_nms_amcGetSeedMetaData_jssp' line 45: String.prototype.toJSON called on incompatible XML.`

Gebruik de volgende tijdelijke oplossing:

1. Bestand **$CAMPAIGN_HOME/datakit/nms/fra/js/amcIntegration.js** openen
1. Regel 467 van methode &quot;amcGetSeedMetaData&quot; wijzigen
1. Wijzigen `label : [inclView.@label](mailto:inclView.@label)` in `label : String([inclView.@label](mailto:inclView.@label))`

1. Opslaan.
1. Start de server opnieuw.

## Als Adobe Campaign een fout weergeeft wanneer op de knop Synchroniseren wordt geklikt {#if-adobe-campaign-displays-an-error-when-clicking-the-synchronize-button}

Als u op de knop **Synchroniseren** in Adobe Campaign Classic klikt, wordt de volgende fout weergegeven:

`Error while executing the method ‘aemListContent' of service [nms:delivery](https://nmsdelivery/)`

Om deze kwestie te bevestigen, zorg ervoor de verbinding-URL AEM in de Externe Rekeningen wordt gevormd bereikbaar van de machine is.

Een schakelaar van **localhost** aan een IP-adres loste deze kwestie op.

## Als u de fout {#if-you-get-a-cannot-parse-xtk-date-time-undefined-error} van XTK Date+Time &#39;undefined&#39; krijgt

Nadat u op Synchroniseren hebt geklikt, wordt een fout weergegeven die door een script op de pagina&#39;s is opgetreden: Kan XTK Date+Time &#39;undefined&#39; niet parseren: geen geldige XTK-waarde.

Dit gebeurt als er nog verouderde Adobe Campaign-informatie over het AEM-exemplaar is. Los dit probleem op door alle configuraties van de campagnemontegratie te verwijderen die op AEM zijn en hen te herbouwen. Maak vervolgens een nieuwe sjabloon.

## Als bij een verbinding met SSL een fout optreedt bij het instellen van de cloudservice {#if-a-connection-to-ssl-displays-an-error-when-setting-up-the-cloud-service}

In error.log van AEM, als u het volgende ziet:

```xml
javax.net.ssl.SSLProtocolException: handshake alert:  unrecognized_name
at sun.security.ssl.ClientHandshaker.handshakeAlert(Unknown Source)
at sun.security.ssl.SSLSocketImpl.recvAlert(Unknown Source)
at sun.security.ssl.SSLSocketImpl.readRecord(Unknown Source)
at sun.security.ssl.SSLSocketImpl.performInitialHandshake(Unknown Source)
at sun.security.ssl.SSLSocketImpl.writeRecord(Unknown Source)
at sun.security.ssl.AppOutputStream.write(Unknown Source)
```

Neem een ticket mee naar het Adobe Campaign-ondersteuningsteam.

## Als u http ziet in plaats van een verwachte https-koppeling in het synchronisatiedialoogvenster {#if-you-see-http-instead-of-an-expected-https-links-in-the-synchronization-dialog}

Met de volgende instellingen:

* Gehoste Adobe Campaign die https gebruikt voor communicatie met AEM Author
* Reverse proxy die SSL beëindigt
* AEM-auteur-instantie op locatie

Wanneer u probeert inhoud te synchroniseren in Adobe Campaign-levering, wordt AEM een lijst met nieuwsbrieven geretourneerd. De URL&#39;s naar de nieuwsbrieven in de lijst zijn echter http-adressen. Als u een van de items in de lijst selecteert, treedt er een fout op.

U lost dit probleem als volgt op:

* De verzender of reverse-proxy moet zijn geconfigureerd om het oorspronkelijke protocol als header door te geven.
* Het *Apache Felix Http Service SSL-filter* in de OSGi-configuratie ([https://&lt;host>:&lt;port>/system/console/configMgr](http://localhost:4502/system/console/configMgr)) moet worden geconfigureerd volgens de respectievelijke headerinstellingen. Zie [https://felix.apache.org/documentation/subprojects/apache-felix-http-service.html#using-the-ssl-filter](https://felix.apache.org/documentation/subprojects/apache-felix-http-service.html#using-the-ssl-filter)

## Als de aangepaste sjabloon die ik heb gemaakt niet kan worden geselecteerd in Pagina-eigenschappen {#if-the-custom-template-i-created-cannot-be-selected-in-page-properties}

Wanneer u een mailsjabloon voor Adobe Campaign maakt, moet u de eigenschap **acMapping** met de waarde **mapRecipient** opnemen in het **jcr:content**-knooppunt van de sjabloon, anders kunt u de Adobe Campaign-sjabloon niet selecteren in **Pagina-eigenschappen** van AEM (veld is uitgeschakeld).

## Als u de fout &quot;com.day.cq.mcm.campagne.servlets.util.ParameterMapper&quot;in uw logboeken {#if-you-get-the-error-com-day-cq-mcm-campaign-servlets-util-parametermapper-in-your-logs} krijgt

Wanneer u uw douanemalplaatje gebruikt, krijgt u de fout &quot;com.day.cq.mcm.campagne.servlets.util.ParameterMapper&quot;in uw logboeken. In dit geval moet u Featurepack 6576 installeren vanuit [Pakket delen](/help/sites-administering/package-manager.md#package-share). Dit is een probleem waarbij als de eigenschap acMapping is ingesteld op een andere waarde dan receiving.firstName, een lege waarde wordt gemaakt aan de zijde van Adobe Campaign Manager.
