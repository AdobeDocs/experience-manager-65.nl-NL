---
title: Problemen met de Adobe Campaign Classic-integratie oplossen
description: Leer hoe u problemen met de Adobe Campaign Classic-integratie kunt oplossen.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
exl-id: 317bab41-3504-4e46-9ddc-72e291a34e06
solution: Experience Manager, Experience Manager Sites
feature: Integration
role: Admin
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '802'
ht-degree: 0%

---


# Problemen met de Adobe Campaign Classic-integratie oplossen{#troubleshooting-your-adobe-campaign-classic-integration}

Leer hoe u problemen kunt oplossen met de integratie met Adobe Campaign Classic (ACC).

De volgende het oplossen van problemenuiteinden helpen de gemeenschappelijkste problemen oplossen u kunt ontmoeten wanneer u AEM met ACC integreert.

## Algemene tips voor probleemoplossing {#general-troubleshooting-tips}

Controleer of HTTP-aanroepen door beide oplossingen worden verzonden en ontvangen (AEM > Adobe Campaign Classic, Adobe Campaign Classic > AEM). Met deze tip kunt u problemen met firewall/SSL voorkomen.

* Voor AEM functionaliteit, kunt u zien dat de vraag JSON van de AEM auteursinterface wordt gevraagd
   * Deze vraag zou niet in een HTTP-500 fout moeten resulteren.
   * Als u HTTP-500 fouten ziet, controleer `error.log` voor meer informatie .
* Het verhogen van zuivert niveau voor campagne-klassen in AEM kan ook helpen om kwesties problemen op te lossen.

## Als de verbinding mislukt {#when-the-connection-fails}

Controleer of u de **`aemserver`** in Adobe Campaign Classic.

## Als er geen afbeeldingen worden weergegeven in de Adobe Campaign Classic-console {#if-images-do-not-appear-in-the-adobe-campaign-console}

Controleer de bron van de HTML en bevestig dat u URL van de cliëntmachine kunt openen. Als de URL `localhost:4503` in het, dan verander de configuratie van de Verbinding Externalzer van de Vraag van de Dag CQ op uw AEM auteursinstantie. Laat het naar een publicatie-instantie verwijzen die kan worden bereikt vanaf de Adobe Campaign Classic-consolemachine.

Zie [Het vormen van ExternalAlizer.](/help/sites-administering/campaignstandard.md#configuring-the-externalizer)

## Als u geen verbinding kunt maken van AEM naar Adobe Campaign Classic  {#if-you-cannot-connect-from-aem-to-adobe-campaign}

Zoek het volgende foutbericht in Adobe Campaign Classic.

* `No datasource defined in the instance 'default'.`

* `Make sure the DNS alias used to access the server is correct (for example, avoid hard-coded IP addresses). (iRc=16384)`

Als u dit probleem wilt verhelpen, wijzigt u het volgende in `$CAMPAIGN_HOME/conf/config-<instance-name>.xml`:

* `<dataStore hosts="*" lang="en_GB">`

## Als er geen gegevens worden weergegeven in het dialoogvenster Adobe Campaign Classic {#if-no-data-displays-in-the-adobe-campaign-dialog}

In Adobe Campaign Classic moet u ervoor zorgen dat er geen schuine streep aan het einde komt (`/`) na het poortnummer.

![Adobe Campaign Classic - zorg ervoor dat er geen sprake is van een slash na het poortnummer](assets/chlimage_1-149.png)

## Als u een waarschuwing over setlocale ontvangt {#if-you-get-a-warning-about-your-setlocale}

Bij het starten van de Apache HTTPD-service voor Adobe Campaign Classic ziet u mogelijk de fout `Warning: setlocale: LC_CTYPE cannot change locale`

Zorg ervoor dat u `en_CA.ISO-8859-15 locale` is geïnstalleerd op uw Adobe Campaign Classic-server.

* U kunt controleren of het geïnstalleerd door te gebruiken `local -a`.
* Als het niet geïnstalleerd is, kunt u de `/usr/local/neolane/nl6/env.sh` en wijzig de landinstelling in een geïnstalleerd script.

## Als er een fout optreedt tijdens het compileren van script &#39;get_nms_amcGetSeedMetaData_jssp&#39; {#if-you-get-an-error-while-compiling-script-get-nms-amcgetseedmetadata-jssp}

Als u het volgende foutbericht ziet in het AEM logbestand:

`com.day.cq.mcm.campaign.impl.CampaignConnectorImpl Internal Adobe Campaign error: response body is Error while compiling script 'get_nms_amcGetSeedMetaData_jssp' line 45: String.prototype.toJSON called on incompatible XML.`

Gebruik de volgende tijdelijke oplossing op de Adobe Campaign Classic-server.

1. Bestand openen `$CAMPAIGN_HOME/datakit/nms/fra/js/amcIntegration.js`
1. Regel 467 van de methode wijzigen `amcGetSeedMetaData`
1. Wijzigen `label : [inclView.@label](mailto:inclView.@label)` tot `label : String([inclView.@label](mailto:inclView.@label))`
1. Opslaan.
1. Start de server opnieuw.

## Als Adobe Campaign Classic een fout weergeeft wanneer op de knop Synchroniseren wordt geklikt {#if-adobe-campaign-displays-an-error-when-clicking-the-synchronize-button}

Wanneer u op de knop **Synchroniseren** in Adobe Campaign Classic wordt mogelijk de volgende fout weergegeven.

* `Error while executing the method 'aemListContent' of service [nms:delivery](https://nmsdelivery/)`

Controleer of de URL van de AEM verbinding is geconfigureerd in het dialoogvenster **Externe rekeningen** in Adobe Campaign Classic bereikbaar is vanaf de machine.

Een schakelaar van `localhost` naar een IP-adres voor de URL kan dit probleem vaak oplossen.

## Als u een fout &#39;Kan XTK Date+Time &#39;undefined&#39; niet parseren&#39; ontvangt {#if-you-get-a-cannot-parse-xtk-date-time-undefined-error}

Na klikken **Synchroniseren** AEM ontvangt u mogelijk een fout die een script op de pagina&#39;s heeft plaatsgevonden.

* `Cannot parse XTK Date+Time 'undefined': not a valid XTK value.`

Deze fout treedt op als er verouderde Adobe Campaign Classic-informatie over het AEM-exemplaar is. U kunt dit probleem als volgt oplossen:

1. Verwijder alle Adobe Campaign Classic-integratieconfiguraties die op AEM staan.
1. Herstel de integratie.
1. Maak een sjabloon.

## Als bij een verbinding met SSL een fout wordt weergegeven bij het instellen van de Cloud Service {#if-a-connection-to-ssl-displays-an-error-when-setting-up-the-cloud-service}

Stuur een ticket naar het Adobe Campaign-ondersteuningsteam als u het volgende ziet in het dialoogvenster `error.log` AEM.

```text
javax.net.ssl.SSLProtocolException: handshake alert:  unrecognized_name
at sun.security.ssl.ClientHandshaker.handshakeAlert(Unknown Source)
at sun.security.ssl.SSLSocketImpl.recvAlert(Unknown Source)
at sun.security.ssl.SSLSocketImpl.readRecord(Unknown Source)
at sun.security.ssl.SSLSocketImpl.performInitialHandshake(Unknown Source)
at sun.security.ssl.SSLSocketImpl.writeRecord(Unknown Source)
at sun.security.ssl.AppOutputStream.write(Unknown Source)
```

## Als u HTTP ziet in plaats van de verwachte HTTPS-koppelingen in het synchronisatiedialoogvenster {#if-you-see-http-instead-of-an-expected-https-links-in-the-synchronization-dialog}

Wanneer u probeert inhoud te synchroniseren in Adobe Campaign Classic-levering, wordt AEM een lijst met nieuwsbrieven geretourneerd. De URL&#39;s naar de nieuwsbrieven in de lijst kunnen echter HTTP-adressen zijn in plaats van HTTPS. Als u een van de items in de lijst selecteert, treedt er een fout op. Deze fout kan met de volgende opstelling gebeuren.

* Gehoste Adobe Campaign die https gebruikt voor communicatie met AEM auteur
* Reverse proxy die SSL beëindigt
* Instantie AEM auteur op locatie

Ga als volgt te werk om dit probleem op te lossen:

* De AEM Dispatcher of reverse-proxy moet zijn geconfigureerd om het oorspronkelijke protocol als een header door te geven.
* De **Apache Felix HTTP Service SSL-filter** in de configuratie OSGi van AEM moet met de vereiste kopbalmontages worden gevormd.
   * `https://<host>:<port>/system/console/configMgr`
   * Zie [https://github.com/apache/felix-dev/tree/master/http#using-the-ssl-filter](https://github.com/apache/felix-dev/tree/master/http#using-the-ssl-filter)

## Een aangepaste sjabloon kan niet worden geselecteerd in Pagina-eigenschappen {#if-the-custom-template-i-created-cannot-be-selected-in-page-properties}

Wanneer u een mailsjabloon maakt in AEM voor Adobe Campaign Classic, moet u de eigenschap `acMapping` met de waarde `mapRecipient` in de `jcr:content` knooppunt van de sjabloon. Als u dit niet doet, kunt u de Adobe Campaign Classic-sjabloon niet selecteren in **Pagina-eigenschappen** AEM. Het veld wordt uitgeschakeld weergegeven.

## Als u de fout &quot;com.day.cq.mcm.campagne.servlets.util.ParameterMapper&quot;in de Logboeken van de AEM ziet {#if-you-get-the-error-com-day-cq-mcm-campaign-servlets-util-parametermapper-in-your-logs}

U ziet de fout `com.day.cq.mcm.campaign.servlets.util.ParameterMapper` in de AEM logboeken wanneer het gebruiken van een douanemalplaatje.

Deze fout treedt op als `acMapping` eigenschap is ingesteld op een andere waarde dan `recipient.firstName`, wordt een lege waarde gemaakt in Adobe Campaign Manager.

Als deze fout optreedt, installeert u functiepak 6576 voor AEM van [Pakket delen](/help/sites-administering/package-manager.md#package-share).
