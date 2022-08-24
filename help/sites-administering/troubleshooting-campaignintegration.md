---
title: Problemen met Adobe Campaign-integratie oplossen
seo-title: Troubleshooting your Adobe Campaign Integration
description: Leer hoe u problemen met de Adobe Campaign-integratie kunt oplossen.
seo-description: Learn how to troubleshoot issues with the Adobe Campaign Integration.
uuid: 835ac2c3-ef2f-4963-9047-aeda3647b114
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
discoiquuid: b1d45f01-78de-423c-8f6b-5cb7067c3a2f
exl-id: 317bab41-3504-4e46-9ddc-72e291a34e06
source-git-commit: 9d142ce9e25e048512440310beb05d762468f6a2
workflow-type: tm+mt
source-wordcount: '803'
ht-degree: 0%

---

# Problemen met Adobe Campaign-integratie oplossen{#troubleshooting-your-adobe-campaign-integration}

>[!NOTE]
>
>Deze pagina is van toepassing op Campaign Classic.

De volgende tips voor het oplossen van problemen helpen u de meest voorkomende problemen op te lossen die u kunt tegenkomen wanneer u AEM met Adobe Campaign integreert:

## Algemene tips voor probleemoplossing {#general-troubleshooting-tips}

Voor beide integraties kunt u controleren of HTTP-aanroepen worden verzonden (AEM > Adobe Campaign, Adobe Campaign > AEM):

* Wanneer de integratie ontbreekt, zorg ervoor dat deze vraag op het andere eind aankomt (om firewall/SSL kwesties te vermijden).
* Voor AEM functionaliteit, zult u zien dat de verbindingsvraag van de AEM auteursinterface wordt gevraagd; deze moeten niet resulteren in een HTTP-500-fout. Als u HTTP-500 fouten ziet, controleer `error.log` voor meer informatie hierover .
* Het verhogen van zuivert niveau voor campagne-klassen in AEM helpt ook om kwesties problemen op te lossen.

## Als de verbinding mislukt {#if-the-connection-fails}

Controleer of u de **aemserver** in Adobe Campaign.

## Als er geen afbeeldingen worden weergegeven in de Adobe Campaign-console {#if-images-do-not-appear-in-the-adobe-campaign-console}

Controleer de bron van de HTML en bevestig dat u URL van de cliëntmachine kunt openen. Als de URL localhost:4503 bevat, wijzigt u de configuratie van Day CQ Link Externalzer op de auteur om naar een publicatie-instantie te verwijzen die kan worden bereikt vanaf de Adobe Campaign-consolemachine.

Zie [Het vormen van ExternalAlizer.](/help/sites-administering/campaignstandard.md#configuring-the-externalizer)

## Als u geen verbinding kunt maken van AEM met Adobe Campaign {#if-you-cannot-connect-from-aem-to-adobe-campaign}

Zoek het volgende foutbericht in Adobe Campaign:

`No datasource defined in the instance 'default'.`

`Make sure the DNS alias used to access the server is correct (for example, avoid hard-coded IP addresses). (iRc=16384)`

Als u dit probleem wilt verhelpen, wijzigt u het volgende in **$CAMPAIGN_HOME/conf/config-&lt;instance-name>.xml**:

`<dataStore hosts="*" lang="en_GB">`

## Als er geen gegevens worden weergegeven in het dialoogvenster Adobe Campaign {#if-no-data-displays-in-the-adobe-campaign-dialog}

Zorg er in Adobe Campaign voor dat er na het poortnummer geen slash (/) achter het poortnummer staat.

![chlimage_1-149](assets/chlimage_1-149.png)

## Als u een waarschuwing over uw setlocale krijgt {#if-you-get-a-warning-about-your-setlocale}

Als u de Apache HTTPD-service start en de fout ziet `"Warning: setlocale: LC_CTYPE cannot change locale"` zorg ervoor dat u **en_CA.ISO-8859-15 locale** op uw systeem geïnstalleerd.

U kunt controleren of het geïnstalleerd door te gebruiken `local -a`. Als het niet geïnstalleerd is, kunt u repareren **/usr/local/neolane/nl6/env.sh** en wijzig de landinstelling in een geïnstalleerd script.

## Als er een fout optreedt tijdens het compileren van script &#39;get_nms_amcGetSeedMetaData_jssp&#39; {#if-you-get-an-error-while-compiling-script-get-nms-amcgetseedmetadata-jssp}

Als u het volgende foutbericht ziet in het AEM logbestand:

`com.day.cq.mcm.campaign.impl.CampaignConnectorImpl Internal Adobe Campaign error: response body is Error while compiling script 'get_nms_amcGetSeedMetaData_jssp' line 45: String.prototype.toJSON called on incompatible XML.`

Gebruik de volgende tijdelijke oplossing:

1. Bestand openen **$CAMPAIGN_HOME/datakit/nms/fra/js/amcIntegration.js**
1. Regel 467 van methode &quot;amcGetSeedMetaData&quot; wijzigen
1. Wijzigen `label : [inclView.@label](mailto:inclView.@label)` tot `label : String([inclView.@label](mailto:inclView.@label))`

1. Opslaan.
1. Start de server opnieuw.

## Als er een fout wordt weergegeven in Adobe Campaign wanneer wordt geklikt op de knop Synchroniseren {#if-adobe-campaign-displays-an-error-when-clicking-the-synchronize-button}

Als u op de knop **Synchroniseren** in Adobe Campaign Classic wordt de volgende fout weergegeven:

`Error while executing the method ‘aemListContent' of service [nms:delivery](https://nmsdelivery/)`

Om deze kwestie te bevestigen, zorg ervoor de verbinding-URL AEM in de Externe Rekeningen wordt gevormd bereikbaar van de machine is.

Een schakelaar van **localhost** aan een IP-adres opgeloste deze kwestie.

## Als er een fout &#39;Kan XTK Date+Time &#39;undefined&#39; niet parseren&#39; optreedt {#if-you-get-a-cannot-parse-xtk-date-time-undefined-error}

Nadat u op Synchroniseren hebt geklikt, wordt een fout weergegeven die door een script op de pagina&#39;s is opgetreden: Kan XTK Date+Time &#39;undefined&#39; niet parseren: geen geldige XTK-waarde.

Dit gebeurt als er nog verouderde Adobe Campaign-informatie over het AEM-exemplaar is. Los dit probleem op door alle configuraties van de campagnemontegratie te verwijderen die op AEM zijn en hen te herbouwen. Maak vervolgens een nieuwe sjabloon.

## Als een verbinding met SSL een fout weergeeft bij het instellen van de cloudservice {#if-a-connection-to-ssl-displays-an-error-when-setting-up-the-cloud-service}

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
* De *Apache Felix Http Service SSL-filter* in de OSGi-configuratie ([https://&lt;host>:&lt;port>/system/console/configMgr](http://localhost:4502/system/console/configMgr)) moet worden geconfigureerd met de respectievelijke headerinstellingen. Zie [https://felix.apache.org/documentation/subprojects/apache-felix-http-service.html#using-the-ssl-filter](https://felix.apache.org/documentation/subprojects/apache-felix-http-service.html#using-the-ssl-filter)

## Als de aangepaste sjabloon die ik heb gemaakt niet kan worden geselecteerd in Pagina-eigenschappen {#if-the-custom-template-i-created-cannot-be-selected-in-page-properties}

Wanneer u een e-mailsjabloon voor Adobe Campaign maakt, moet u de eigenschap **acMapping** met de waarde **mapRecipient** in de **jcr:inhoud** van de sjabloon, of u kunt de Adobe Campaign-sjabloon niet selecteren in **Pagina-eigenschappen** AEM (veld is uitgeschakeld).

## Als u de fout &quot;com.day.cq.mcm.campagne.servlets.util.ParameterMapper&quot;in uw logboeken krijgt {#if-you-get-the-error-com-day-cq-mcm-campaign-servlets-util-parametermapper-in-your-logs}

Wanneer u uw douanemalplaatje gebruikt, krijgt u de fout &quot;com.day.cq.mcm.campagne.servlets.util.ParameterMapper&quot;in uw logboeken. In dit geval moet u Featurepack 6576 installeren vanaf [Pakket delen](/help/sites-administering/package-manager.md#package-share). Dit is een probleem waarbij als de eigenschap acMapping is ingesteld op een andere waarde dan receiving.firstName, een lege waarde wordt gemaakt aan de zijde van Adobe Campaign Manager.
