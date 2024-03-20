---
title: Dynamic Media configureren - hybride modus
description: Leer hoe u Dynamic Media - Hybride modus configureert.
mini-toc-levels: 3
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
docset: aem65
legacypath: /content/docs/en/aem/6-0/administer/integration/dynamic-media/config-dynamic
role: User, Admin
exl-id: 5719d32c-4f19-47c1-bea9-8fd0bc8439ed
feature: Configuration,Hybrid Mode
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '7503'
ht-degree: 0%

---

# Dynamic Media configureren - hybride modus {#configuring-dynamic-media-hybrid-mode}

>[!IMPORTANT]
>
>Einde van steun voor Veilige Laag 2.0 en 3.0 van de Contactdoos en de Veiligheid van de Laag van het Vervoer 1.0 en 1.1.
>Vanaf 30 april 2024 beëindigt Adobe Dynamic Media de steun voor:
>
>* SSL (Secure Socket Layer) 2.0
>* SSL 3.0
>* TLS (Transport Layer Security) 1.0 en 1.1
>* De volgende zwakke ciphers in TLS 1.2:
> `TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA384`
> `TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA`
> `TLS_RSA_WITH_AES_256_GCM_SHA384`
> `TLS_RSA_WITH_AES_256_CBC_SHA256`
> `TLS_RSA_WITH_AES_256_CBC_SHA`
> `TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256`
> `TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA`
> `TLS_RSA_WITH_AES_128_GCM_SHA256`
> `TLS_RSA_WITH_AES_128_CBC_SHA256`
> `TLS_RSA_WITH_AES_128_CBC_SHA`
> `TLS_RSA_WITH_CAMELLIA_256_CBC_SHA`
> `TLS_RSA_WITH_CAMELLIA_128_CBC_SHA`
> `TLS_ECDHE_RSA_WITH_3DES_EDE_CBC_SHA`
> `TLS_RSA_WITH_SDES_EDE_CBC_SHA`
>
> Zie ook [Dynamic Media-beperkingen](/help/assets/limitations.md).

<!-- FOR ABOVE - CQDOC-19433 (original ticket)
and CQDOC-19792 (removed as per this ticket December 5, 2022) -->


Dynamic Media-Hybrid moet voor gebruik worden toegelaten en worden gevormd. Afhankelijk van je gebruikscase heeft Dynamic Media verschillende [ondersteunde configuraties](#supported-dynamic-media-configurations).

>[!NOTE]
>
>Als u Dynamic Media wilt configureren en uitvoeren in de Scene7-uitvoeringsmodus, raadpleegt u [Dynamic Media configureren - Scene7-modus](/help/assets/config-dms7.md).
>
>Volg de instructies op deze pagina als u Dynamic Media wilt configureren en uitvoeren in de hybride uitvoeringsmodus.

Meer informatie over werken met [video](/help/assets/video.md) in Dynamic Media.

>[!NOTE]
>
>Als u Adobe Experience Manager-configuratie gebruikt voor verschillende omgevingen, zoals een omgeving voor ontwikkeling, staging en live productie, configureert u Dynamic Media-Cloud Servicen voor elke omgeving.

>[!NOTE]
>
>Als u problemen hebt met uw Dynamic Media-configuratie, raadpleegt u de logbestanden die specifiek zijn voor Dynamic Media. Deze bestanden worden automatisch geïnstalleerd wanneer u Dynamic Media inschakelt:
>
>* `s7access.log`
>* `ImageServing.log`
>
>Deze worden beschreven in [De instantie van de Experience Manager bewaken en onderhouden](/help/sites-deploying/monitoring-and-maintaining.md).

Hybride uitgeverij en levering vormen een kernelement van de toevoeging van Dynamic Media aan Adobe Experience Manager. Met hybride publicaties kunt u Dynamic Media-elementen, zoals afbeeldingen, sets en video, uit de cloud leveren in plaats van uit de publicatieknooppunten van de Experience Manager.

Andere inhoud, zoals Dynamic Media-viewers, sitepagina&#39;s en statische inhoud, wordt nog steeds aangeboden vanaf de publicatieknooppunten van de Experience Manager.

Als u een klant van Dynamic Media bent, moet u hybride levering als leveringsmechanisme voor alle Dynamic Media-inhoud gebruiken.

## Hybride publicatiearchitectuur voor video&#39;s {#hybrid-publishing-architecture-for-videos}

![chlimage_1-506](assets/chlimage_1-428.png)

## Hybride publicatiearchitectuur voor afbeeldingen {#hybrid-publishing-architecture-for-images}

![chlimage_1-507](assets/chlimage_1-507.png)

## Ondersteunde Dynamic Media-configuraties {#supported-dynamic-media-configurations}

De configuratietaken die volgen verwijzen naar de volgende termen:

| **Term** | **Dynamic Media ingeschakeld** | **Beschrijving** |
|---|---|---|
| Knooppunt Auteur Experience Manager | Wit vinkje in een groene cirkel | Het auteurknooppunt dat u op locatie of via Managed Services implementeert. |
| Knooppunt Experience Manager publiceren | Wit &quot;X&quot; in een rood vierkant. | Het publicatieknooppunt dat u op locatie of via Managed Services implementeert. |
| Knooppunt voor publiceren van afbeeldingenservice | Witte vinkje in een groene cirkel. | Het publiceerknooppunt dat u uitvoert op datacenters die worden beheerd door Adobe. Verwijst naar de URL van de afbeeldingsservice. |

U kunt ervoor kiezen om Dynamic Media alleen te implementeren voor beeldbewerking, alleen voor video of voor beeldbewerking en video. Zie de volgende tabel voor informatie over de stappen voor het configureren van Dynamic Media voor uw specifieke scenario.

<table>
 <tbody>
  <tr>
   <td><strong>Scenario</strong></td>
   <td ><strong>Hoe het werkt</strong></td>
   <td><strong>Configuratiestappen</strong></td>
  </tr>
  <tr>
   <td>ALLEEN images in productie leveren</td>
   <td>Afbeeldingen worden via servers in de wereldwijde datacenters van Adobe geleverd en worden vervolgens in cache geplaatst door een CDN voor schaalbare prestaties en wereldwijd bereik.</td>
   <td>
    <ol>
     <li>Op de Experience Manager <strong>auteur</strong> knooppunt, <a href="#enabling-dynamic-media">Dynamic Media inschakelen</a>.</li>
     <li>Afbeeldingen configureren in <a href="#configuring-dynamic-media-cloud-services">Dynamic Media Cloud Servicen</a>.</li>
     <li><a href="#configuring-image-replication">Afbeeldingsreplicatie configureren</a>.</li>
     <li><a href="#replicating-catalog-settings">Catalogusinstellingen repliceren</a>.</li>
     <li><a href="#replicating-viewer-presets">Viewervoorinstellingen repliceren</a>.</li>
     <li><a href="#using-default-asset-filters-for-replication">Standaardelementfilters gebruiken voor replicatie</a>.</li>
     <li><a href="#configuring-dynamic-media-image-server-settings">Dynamic Media Image Server-instellingen configureren</a>.</li>
     <li><a href="#delivering-assets">Elementen leveren</a>.</li>
    </ol> </td>
  </tr>
  <tr>
   <td>Alleen afbeeldingen leveren in pre-productie (Dev, QE, Stage, enzovoort.)</td>
   <td>Afbeeldingen worden geleverd via het publicatieknooppunt Experience Manager. In dit scenario, omdat het verkeer minimaal is, is er geen behoefte om beelden aan het gegevenscentrum van de Adobe te leveren. En het maakt een veilige voorvertoning van inhoud mogelijk voordat de productie wordt gestart.</td>
   <td>
    <ol>
     <li>Op de Experience Manager <strong>auteur</strong> knooppunt, <a href="#enabling-dynamic-media">Dynamic Media inschakelen</a>.</li>
     <li>Op Experience Manager <strong>publish</strong> knooppunt, <a href="#enabling-dynamic-media">Dynamic Media inschakelen</a>.</li>
     <li><a href="#replicating-viewer-presets">Viewervoorinstellingen repliceren</a>.</li>
     <li>Instellen <a href="#setting-up-asset-filters-for-imaging-in-non-production-deployments">middelenfilter voor niet-productieafbeeldingen</a>.</li>
     <li><a href="#configuring-dynamic-media-image-server-settings">Dynamic Media Image Server-instellingen configureren.</a></li>
     <li><a href="#delivering-assets">Elementen leveren.</a></li>
    </ol> </td>
  </tr>
  <tr>
   <td>ALLEEN video leveren in elke omgeving (Productie, Dev, QE, Stage, enzovoort)</td>
   <td>De video's worden geleverd en in het voorgeheugen ondergebracht door CDN voor scalable prestaties en globaal bereik. De videoposterafbeelding (videominiatuur die wordt weergegeven voordat het afspelen wordt gestart) wordt geleverd door de publicatieinstantie van de Experience Manager.</td>
   <td>
    <ol>
     <li>Op de Experience Manager <strong>auteur</strong> knooppunt, <a href="#enabling-dynamic-media">Dynamic Media inschakelen</a>.</li>
     <li>Op de Experience Manager <strong>publish</strong> knooppunt, <a href="#enabling-dynamic-media">Dynamic Media inschakelen</a> (De publicatie-instantie dient voor de video-posterafbeelding en biedt metagegevens voor het afspelen van video.)</li>
     <li>Video configureren in <a href="#configuring-dynamic-media-cloud-services">Dynamic Media-Cloud Servicen.</a></li>
     <li><a href="#replicating-viewer-presets">Viewervoorinstellingen repliceren</a>.</li>
     <li>Instellen <a href="#setting-up-asset-filters-for-video-only-deployments">middelenfilter voor alleen video</a>.</li>
     <li><a href="#delivering-assets">Elementen leveren.</a></li>
    </ol> </td>
  </tr>
  <tr>
   <td>Lever ZOWEL beelden als video in productie</td>
   <td><p>De video's worden geleverd en in het voorgeheugen ondergebracht door CDN voor scalable prestaties en globaal bereik. Afbeeldingen en videoposterafbeeldingen worden via servers in wereldwijde datacenters van Adobe geleverd en worden vervolgens in cache geplaatst door een CDN voor schaalbare prestaties en een wereldwijd bereik.</p> <p>Verwijs naar vorige secties aan opstellingsbeeld of video in preproductie. </p> </td>
   <td>
    <ol>
     <li>Op de Experience Manager <strong>auteur</strong> knooppunt, <a href="#enabling-dynamic-media">Dynamic Media inschakelen</a>.</li>
     <li>Video configureren in <a href="#configuring-dynamic-media-cloud-services">Dynamic Media-Cloud Servicen.</a></li>
     <li>Afbeeldingen configureren in <a href="#configuring-dynamic-media-cloud-services">Dynamic Media-Cloud Servicen.</a></li>
     <li><a href="#configuring-image-replication">Afbeeldingsreplicatie configureren</a>.</li>
     <li><a href="#replicating-catalog-settings">Catalogusinstellingen repliceren</a>.</li>
     <li><a href="#replicating-viewer-presets">Viewervoorinstellingen repliceren</a>.</li>
     <li><a href="#using-default-asset-filters-for-replication">Gebruik standaardelementfilters voor replicatie.</a></li>
     <li><a href="#configuring-dynamic-media-image-server-settings">Dynamic Media Image Server-instellingen configureren.</a></li>
     <li><a href="#delivering-assets">Elementen leveren.</a></li>
    </ol> </td>
  </tr>
 </tbody>
</table>

## Dynamic Media inschakelen {#enabling-dynamic-media}

[Dynamic Media](https://business.adobe.com/products/experience-manager/assets/dynamic-media.html) is standaard uitgeschakeld. Als u wilt profiteren van Dynamic Media-functies, moet u Dynamic Media inschakelen met de `dynamicmedia` de uitvoermodus zoals u bijvoorbeeld zou doen, `publish` uitvoeringsmodus. Controleer voordat u de functie inschakelt of [technische voorschriften](/help/sites-deploying/technical-requirements.md#requirements-for-aem-dynamic-media-add-on).

>[!NOTE]
>
>Als u Dynamic Media inschakelt via de uitvoeringsmodus, wordt de functionaliteit in Experience Manager 6.1 en Experience Manager 6.0 vervangen, waarbij Dynamic Media is ingeschakeld door het instellen van de `dynamicMediaEnabled` markeren naar **[!UICONTROL true]**. Deze markering heeft geen functionaliteit in Experience Manager 6.2 en later. Bovendien hoeft u de snelstartprocedure niet opnieuw te starten om Dynamic Media in te schakelen.

Als u Dynamic Media inschakelt, zijn de Dynamic Media-functies beschikbaar in de gebruikersinterface en ontvangt elk geüploade afbeeldingselement een *cqdam.pyramid.tiff* uitvoering die wordt gebruikt voor snelle levering van dynamische afbeeldingsuitvoeringen. Deze PTIFF&#39;s hebben belangrijke voordelen, zoals:

* De mogelijkheid om slechts één primaire bronafbeelding te beheren en een oneindige uitvoering te genereren zonder extra opslagruimte.
* De mogelijkheid om interactieve visualisatie te gebruiken, zoals zoomen, pannen en draaien.

Als u Dynamic Media Classic in Experience Manager wilt gebruiken, moet u Dynamic Media alleen inschakelen als u een [specifiek scenario](/help/sites-administering/scene7.md#aem-scene-integration-versus-dynamic-media). Dynamic Media is uitgeschakeld, tenzij u Dynamic Media inschakelt in de uitvoeringsmodus.

Als u Dynamic Media wilt inschakelen, moet u de Dynamic Media-uitvoeringsmodus inschakelen via de opdrachtregel of de snelstartbestandsnaam.

**Dynamic Media inschakelen:**

1. Ga als volgt te werk op de opdrachtregel wanneer u de snelstart start:

   * Toevoegen `-r dynamicmedia` aan het einde van de opdrachtregel wanneer het jar-bestand wordt gestart.

   ```shellsession {.line-numbers}
   java -Xmx4096m -Doak.queryLimitInMemory=500000 -Doak.queryLimitReads=500000 -jar cq-quickstart-6.5.0.jar -r dynamicmedia
   ```

   Als u publiceert naar s7delivery, moet u de volgende TrustStore argumenten ook omvatten:

   ```shellsession {.line-numbers}
   -Djavax.net.ssl.trustStore=<absoluteFilePath>/customerTrustStoreFileName>
   
    -Djavax.net.ssl.trustStorePassword=<passwordForTrustStoreFile>
   ```

1. Verzoek `https://localhost:4502/is/image` en zorg ervoor dat de Server van het Beeld nu loopt.

   >[!NOTE]
   >
   >Als u problemen met Dynamic Media wilt oplossen, raadpleegt u de volgende logboeken in het dialoogvenster `crx-quickstart/logs/` map:
   >
   >* ImageServer-&lt;portid>-&lt;yyyy>&lt;mm>&lt;dd>.log - Het logboek ImageServer verstrekt statistieken en analytische informatie die voor het analyseren van het gedrag van het interne proces ImageServer wordt gebruikt.
   >
   Voorbeeld van de naam van een logbestand voor een afbeeldingsserver: `ImageServer-57346-2020-07-25.log`
   >
   * s7access-&lt;yyyy>&lt;mm>&lt;dd>.log - Het s7access logboek registreert elk verzoek dat aan Dynamic Media via `/is/image` en `/is/content`.
   >
   Deze logboeken worden alleen gebruikt als Dynamic Media is ingeschakeld. Zij zijn niet opgenomen in de **Volledige download** pakket dat wordt gegenereerd op basis van het `system/console/status-Bundlelist` pagina; wanneer u Customer Support belt als u een Dynamic Media-probleem hebt, voegt u beide logboeken toe aan het probleem.

### Als u Experience Manager op een andere haven of een contextweg installeerde... {#if-you-installed-aem-to-a-different-port-or-context-path}

Als u implementeert [Experience Manager naar een toepassingsserver](/help/sites-deploying/application-server-install.md) en Dynamic Media ingeschakeld hebben, moet u de **zelfdomein** in de externalizer. Anders werkt het genereren van miniaturen voor elementen niet correct voor Dynamic Media-elementen.

Als u bovendien quickstart uitvoert op een andere poort of een ander contextpad, moet u ook de **zelfdomein**.

Als Dynamic Media is ingeschakeld, worden de statische miniatuuruitvoeringen voor afbeeldingselementen gegenereerd met Dynamic Media. Om ervoor te zorgen dat miniaturen correct worden gegenereerd voor Dynamic Media, moet de Experience Manager een URL-aanvraag naar zichzelf uitvoeren en zowel het poortnummer als het contextpad weten.

In Experience Manager:

* De **zelfdomein** in de [ExternalAlizer](/help/sites-developing/externalizer.md) wordt gebruikt om zowel het havenaantal als contextweg terug te winnen.
* Indien niet **zelfdomein** wordt gevormd, worden het havenaantal en contextweg teruggewonnen van de dienst van HTTP van de Plaatsheid.

In een plaatsing van de WAR van QuickStart van de Experience Manager, kunnen het havenaantal en de contextweg niet worden afgeleid, daarom moet u een **zelfdomein**. Zie [ExternalAlizer-documentatie](/help/sites-developing/externalizer.md) op hoe te om te vormen **zelfdomein**.

>[!NOTE]
>
In een [Zelfstandige implementatie van Experience Manager Quickstart](/help/sites-deploying/deploy.md), **zelfdomein** hoeft over het algemeen niet te worden geconfigureerd omdat het poortnummer en het contextpad automatisch kunnen worden geconfigureerd. Nochtans, als alle netwerkinterfaces worden uitgezet, moet u vormen **zelfdomein**.

## Dynamic Media uitschakelen  {#disabling-dynamic-media}

Dynamic Media is niet standaard ingeschakeld. Als u Dynamic Media eerder hebt ingeschakeld, kunt u deze later uitschakelen.

Als u Dynamic Media wilt uitschakelen nadat u deze hebt ingeschakeld, verwijdert u de `-r dynamicmedia` markering voor uitvoermodus.

**Dynamic Media uitschakelen:**

1. Op de bevellijn, wanneer het lanceren van de snelstart, kunt u één van beiden van het volgende doen:

   * Niet toevoegen `-r dynamicmedia` op de opdrachtregel wanneer het jar-bestand wordt gestart.

   ```shellsession {.line-numbers}
   java -Xmx4096m -Doak.queryLimitInMemory=500000 -Doak.queryLimitReads=500000 -jar cq-quickstart-6.5.0.jar
   ```

1. Verzoek `https://localhost:4502/is/image`. Je ontvangt een bericht dat Dynamic Media is uitgeschakeld.

   >[!NOTE]
   >
   Nadat de Dynamic Media-uitvoeringsmodus is uitgeschakeld, wordt de workflowstap die het `cqdam.pyramid.tiff` uitvoering wordt automatisch overgeslagen. De functie schakelt ook ondersteuning voor dynamische uitvoeringen en andere Dynamic Media-functies uit.
   >
   Houd er ook rekening mee dat wanneer de Dynamic Media-uitvoeringsmodus wordt uitgeschakeld nadat de Experience Manager-server is geconfigureerd, alle middelen die in die uitvoeringsmodus zijn geüpload, nu ongeldig zijn.

## (Optioneel) Dynamic Media-voorinstellingen en -configuraties migreren van 6,3 naar 6,5 Nul downtime {#optional-migrating-dynamic-media-presets-and-configurations-from-to-zero-downtime}

Als u Experience Manager - Dynamic Media van 6.3 aan 6.5 bevordert (die nu de capaciteit voor nul onderbreking plaatsingen) omvat, moet u het volgende krullbevel in werking stellen. Met deze opdracht migreert u al uw voorinstellingen en configuraties van `/etc` tot `/conf` in CRXDE Lite.

>[!NOTE]
>
Als u de Experience Manager-instantie uitvoert in de compatibiliteitsmodus - u hebt het compatibiliteitspakket geïnstalleerd - hoeft u deze opdrachten niet uit te voeren.

Voor alle upgrades, met of zonder het compatibiliteitspakket, kunt u de standaard, out-of-box viewer vooraf instelt kopiëren die oorspronkelijk met Dynamic Media door het volgende Linux® krullbevel in werking te stellen kwam:

`curl -u admin:admin -X POST https://<server_address>:<server_port>/libs/settings/dam/dm/presets/viewer.pushviewerpresets.json`

Aangepaste voorinstellingen en configuraties van viewers migreren die u hebt gemaakt van `/etc` tot `/conf`, voert u de volgende Linux® curl-opdracht uit:

`curl -u admin:admin -X POST https://<server_address>:<server_port>/libs/settings/dam/dm/presets.migratedmcontent.json`

## Afbeeldingsreplicatie configureren {#configuring-image-replication}

Dynamic Media-beeldlevering werkt door afbeeldingselementen, waaronder videominiaturen, te publiceren van Auteur van Experience Manager en deze te repliceren naar de replicatieservice op aanvraag van de Adobe (de Replication Service URL). De activa worden dan geleverd door de dienst van de beeldlevering op bestelling (de Dienst URL van het Beeld).

Ga als volgt te werk:

1. [Verificatie instellen](#setting-up-authentication).
1. [De replicatieagent configureren](#configuring-the-replication-agent).

De Replication Agent publiceert Dynamic Media-elementen, zoals afbeeldingen, videometagegevens en stelt deze in op de door de Adobe gehoste Image Service. De replicatieagent is niet standaard ingeschakeld.

Nadat u de replicatieagent hebt gevormd, moet u [valideren en testen of de installatie is gelukt](#validating-the-replication-agent-for-dynamic-media). In dit gedeelte worden deze procedures beschreven.

>[!NOTE]
>
De standaardgeheugenlimiet voor het maken van PTIFF is 3 GB voor alle workflows. U kunt bijvoorbeeld één afbeelding verwerken die 3 GB geheugen vereist terwijl andere workflows worden gepauzeerd, of u kunt 10 afbeeldingen parallel verwerken die elk 300 MB geheugen vereisen.
>
De geheugenlimiet is configureerbaar en past bij de beschikbaarheid van systeembronnen en het type afbeeldingsinhoud dat wordt verwerkt. Als u vele grote activa hebt en genoeg geheugen op het systeem hebt, kunt u deze grens verhogen om ervoor te zorgen dat de beelden parallel worden verwerkt.
>
Een afbeelding waarvoor meer dan de maximale geheugenlimiet nodig is, wordt afgewezen.
>
Als u de geheugenlimiet voor het maken van PTIFF wilt wijzigen, gaat u naar **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]** > **[!UICONTROL Adobe CQ Scene7 PTiffManager]** en wijzigt u **[!UICONTROL maxMemory]** waarde.

### Verificatie instellen {#setting-up-authentication}

Stel replicatieverificatie in bij de auteur, zodat u afbeeldingen kunt repliceren naar de Dynamic Media-service voor het leveren van afbeeldingen. U ontvangt eerst een KeyStore en slaat deze vervolgens op onder de **[!UICONTROL dynamic-media-replication]** gebruiken en configureren. Uw bedrijfsbeheerder heeft tijdens het inrichtingsproces een welkomstbericht met het KeyStore-bestand en de benodigde gegevens ontvangen. Neem contact op met de Klantenondersteuning van de Adobe als u deze gegevens niet hebt ontvangen.

**Aan opstellingsauthentificatie:**

1. Neem contact op met de Klantenondersteuning van de Adobe voor uw KeyStore-bestand en wachtwoord als u nog geen bestand en wachtwoord hebt. Deze informatie is een noodzakelijk onderdeel van provisioning. De sleutels worden aan uw account gekoppeld.

1. Selecteer in Experience Manager het logo van de Experience Manager voor toegang tot de algemene navigatieconsole en navigeer naar **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Users]**.

1. Ga op de pagina Gebruikersbeheer naar de **[!UICONTROL dynamic-media-replication]** gebruiker, en selecteer vervolgens om te openen.

   ![dm-replicatie](assets/dm-replication.png)

1. Selecteer in de pagina Gebruikersinstellingen bewerken voor dynamische media-replicatie de optie **[!UICONTROL Keystore]** tab, dan selecteren **[!UICONTROL Create KeyStore]**.

   ![dm-replication-keystore](assets/dm-replication-keystore.png)

1. Voer een wachtwoord in en bevestig het wachtwoord in het dialoogvenster **[!UICONTROL Set KeyStore Access Password]** in.

   >[!NOTE]
   >
   Herinner het wachtwoord omdat u het moet opnieuw ingaan wanneer u de Agent van de Replicatie later vormt.

   ![chlimage_1-508](assets/chlimage_1-508.png)

1. Op de **[!UICONTROL Edit User Settings For dynamic-media-replication]** pagina, breid de **Persoonlijke sleutel toevoegen uit sleutelarchiefbestand** en voeg het volgende toe (zie de volgende afbeeldingen):

   * In de **[!UICONTROL New Alias]** veld, voert u de naam in van een alias die u later in de replicatieconfiguratie wilt gebruiken. U kunt bijvoorbeeld `replication` als een alias.
   * Selecteer **[!UICONTROL KeyStore File]**. Navigeer naar het KeyStore-bestand dat u via de Adobe ontvangt, selecteer het en selecteer vervolgens **[!UICONTROL Open]**.
   * In de **[!UICONTROL KeyStore File Password]** Voer het wachtwoord voor het KeyStore-bestand in. Dit wachtwoord is **niet** Het KeyStore-wachtwoord dat u in Stap 5 hebt gemaakt, maar dat de Adobe Wachtwoord voor sleutelarchief-bestanden bevat in het welkomstbericht dat u tijdens de provisioning hebt ontvangen. Neem contact op met de Klantenondersteuning van de Adobe als u geen wachtwoord voor een KeyStore-bestand hebt ontvangen.
   * In de **[!UICONTROL Private Key Password]** Voer het wachtwoord voor de persoonlijke sleutel in (dit kan hetzelfde wachtwoord zijn als dat voor de vorige stap). Adobe geeft het wachtwoord voor de persoonlijke sleutel op in het welkomstbericht dat u tijdens de levering ontvangt. Neem contact op met de klantenondersteuning van de Adobe als u geen wachtwoord voor persoonlijke sleutels hebt ontvangen.
   * In de **[!UICONTROL Private Key Alias]** veld, voert u de alias van de persoonlijke sleutel in. Bijvoorbeeld: `*companyname*-alias`. Adobe geeft de alias voor de persoonlijke sleutel op in het welkomstbericht dat u tijdens de levering hebt ontvangen. Neem contact op met de klantenondersteuning van de Adobe als u geen alias voor een persoonlijke sleutel hebt ontvangen.

   ![edit_settings_fordynamic-media-replication2](assets/edit_settings_fordynamic-media-replication2.png)

1. Selecteren **[!UICONTROL Save & Close]** om uw wijzigingen in deze gebruiker op te slaan.

   Vervolgens moet u [vorm de replicatieagent](#configuring-the-replication-agent).

### De replicatieagent configureren {#configuring-the-replication-agent}

1. Selecteer in Experience Manager het logo van de Experience Manager voor toegang tot de algemene navigatieconsole en navigeer naar **[!UICONTROL Tools]** > **[!UICONTROL Deployment]** > **[!UICONTROL Replication]** > **[!UICONTROL Agents on author]**.
1. Selecteer op de pagina Agents op de auteurspagina de optie **[!UICONTROL Dynamic Media Hybrid Image Replication (s7delivery)]**.
1. Selecteren **[!UICONTROL Edit]**.
1. Selecteer de **[!UICONTROL Settings]** en voert u het volgende in:

   * **[!UICONTROL Enabled]** - Schakel dit selectievakje in om de replicatieagent in te schakelen.
   * **[!UICONTROL Region]** - Instellen op de juiste regio: Noord-Amerika, Europa of Azië
   * **[!UICONTROL Tenant ID]** - Deze waarde is de naam van uw bedrijf/huurder die aan de Dienst van de Replicatie publiceert. Deze waarde is de huurder-id die de Adobe opgeeft in het welkomstbericht dat u tijdens de levering hebt ontvangen. Neem contact op met de Klantenondersteuning van de Adobe als u deze gegevens niet hebt ontvangen.
   * **[!UICONTROL Key Store Alias]** - Deze waarde is gelijk aan **Nieuwe alias** waarde ingesteld bij het genereren van de sleutel in [Verificatie instellen](#setting-up-authentication); bijvoorbeeld `replication`. (Zie stap 7 in [Verificatie instellen](#setting-up-authentication).)
   * **[!UICONTROL Key Store Password]** - Het KeyStore-wachtwoord dat is gemaakt toen u op **[!UICONTROL Create KeyStore]**. Dit wachtwoord wordt niet opgegeven door de Adobe. Zie stap 5 van [Verificatie instellen](#setting-up-authentication).

   In de volgende afbeelding ziet u de replicatieagent met voorbeeldgegevens:

   ![chlimage_1-509](assets/chlimage_1-509.png)

1. Selecteren **[!UICONTROL OK]**.

### De replicatieagent voor Dynamic Media valideren {#validating-the-replication-agent-for-dynamic-media}

Ga als volgt te werk om de replicatieagent voor Dynamic Media te valideren:

Selecteer **[!UICONTROL Test Connection]**. Voorbeeld-uitvoer is als volgt:

```shell
11.03.2016 10:57:55 - Transferring content for ReplicationAction{type=TEST, path[0]='/content/dam', time=1457722675402, userId='admin', revision='null'}
11.03.2016 10:57:55 - * Auth User: replication-receiver
11.03.2016 10:57:55 - * HTTP Version: 1.1
11.03.2016 10:57:55 - * Using OAuth 2.0 Authorization Grants
11.03.2016 10:57:55 - * OAuth 2.0 User: dynamic-media-replication
11.03.2016 10:57:55 - * OAuth 2.0 Token: '*****' initialized
11.03.2016 10:57:55 - Publishing: POST[https://replicate-na.assetsadobe.com:8580/is-publish/publish-receiver?Cmd=Test&RootId=xfpuu-6613]
11.03.2016 10:57:55 - Publish response: OK[]
11.03.2016 10:57:55 - Transfer succeeded in 141 ms for ReplicationAction{type=TEST, path[0]='/content/dam', time=1457722675402, userId='admin', revision='null'}
-------------------------------------------------------------------------------------------------------------------------------
Replication test succeeded
```

>[!NOTE]
>
U kunt ook op een van de volgende manieren controleren:
>
* Controleer de replicatielogboeken om ervoor te zorgen dat het middel wordt herhaald.
* Publiceer een afbeelding. Selecteer de afbeelding en selecteer **[!UICONTROL Viewers]** selecteert u vervolgens een voorinstelling voor de viewer in het vervolgkeuzemenu. Selecteer **[!UICONTROL URL]**. Kopieer en plak het URL-pad in de browser om te controleren of de afbeelding zichtbaar is.
>

### Verificatie problemen oplossen {#troubleshooting-authentication}

Bij het instellen van verificatie zijn er enkele problemen die u kunt oplossen. Controleer voordat u op deze problemen controleert of u replicatie hebt ingesteld.

#### Probleem: HTTP-statuscode 401 met bericht - Autorisatie vereist {#problem-http-status-code-with-message-authorization-required}

Dit probleem kan worden veroorzaakt doordat KeyStore niet is ingesteld voor `dynamic-media-replication` gebruiker.

```shell
Replication test to s7delivery:https://s7bern.macromedia.com:8580/is-publish/
17.06.2016 18:54:43 - Transferring content for ReplicationAction{type=TEST, path[0]='/content/dam', time=1466214883309, userId='admin', revision='null'}
17.06.2016 18:54:43 - * Auth User: replication-receiver
17.06.2016 18:54:43 - * HTTP Version: 1.1
17.06.2016 18:54:43 - * Using OAuth 2.0 Authorization Grants
17.06.2016 18:54:43 - * OAuth 2.0 User: dynamic-media-replication
17.06.2016 18:54:43 - No OAuth token available. OAuth not initialized
17.06.2016 18:54:43 - * Using Client Auth SSL alias - replication-alias *
17.06.2016 18:54:43 - Publishing: POST[https://<localhost>:8580/is-publish//publish-receiver?Cmd=Test&RootId=brough]
17.06.2016 18:54:43 - Transfer failed for ReplicationAction{type=TEST, path[0]='/content/dam', time=1466214883309, userId='admin', revision='null'}. java.io.IOException: Failed to execute request
'https://<localhost>:8580/is-publish//publish-receiver?Cmd=Test&RootId=brough':
 Server returned status code 401 with message: Authorization required.
17.06.2016 18:54:43 - Error while replicating: com.day.cq.replication.ReplicationException: Transfer failed for ReplicationAction{type=TEST, path[0]='/content/dam', time=1466214883309,
 userId='admin', revision='null'}. java.io.IOException: Failed to execute request
'https://<localhost>:8580/is-publish//publish-receiver?Cmd=Test&RootId=brough':
 Server returned status code 401 with message: Authorization required.
```

**Oplossing:**
Controleer of de `KeyStore` is opgeslagen naar **dynamic-media-replicatie** en wordt voorzien van het juiste wachtwoord.

#### Probleem: sleutel kan niet worden ontsleuteld - gegevens kunnen niet worden ontsleuteld {#problem-could-not-decrypt-key-could-not-decrypt-data}

```xml
Replication test to s7delivery:https://<localhost>:8580/is-publish/
17.06.2016 19:00:16 - Transferring content for ReplicationAction{type=TEST, path[0]='/content/dam', time=1466215216662, userId='admin', revision='null'}
17.06.2016 19:00:16 - * Auth User: replication-receiver
17.06.2016 19:00:16 - * HTTP Version: 1.1
17.06.2016 19:00:16 - * Using OAuth 2.0 Authorization Grants
17.06.2016 19:00:16 - * OAuth 2.0 User: dynamic-media-replication
17.06.2016 19:00:16 - No OAuth token available. OAuth not initialized
17.06.2016 19:00:16 - * Using Client Auth SSL alias - replication-alias *
17.06.2016 19:00:16 - Transfer failed for ReplicationAction{type=TEST, path[0]='/content/dam', time=1466215216662, userId='admin', revision='null'}. java.lang.SecurityException: java.security.UnrecoverableKeyException: Could not decrypt key: Could not decrypt data.
```

**Oplossing:**
Controleer het wachtwoord. Het wachtwoord in de replicatieagent wordt opgeslagen is niet het zelfde wachtwoord dat werd gebruikt om keystore tot stand te brengen dat.

#### Probleem: InvalidAlgorithmParameterException {#problem-invalidalgorithmparameterexception}

Deze kwestie wordt veroorzaakt door een configuratiefout in uw instantie van de Auteur van de Experience Manager. Het Java™-proces op de auteur krijgt niet de juiste `javax.net.ssl.trustStore`. U ziet deze fout in het replicatielogboek:

```shell
14.04.2016 09:37:43 - Transfer failed for ReplicationAction{type=TEST, path[0]='/content/dam', time=1460651862089, userId='admin', revision='null'}. java.io.IOException: Failed to execute request 'https://<localhost>:8580/is-publish/publish-receiver?Cmd=Test&RootId=rbrough-osx2': java.lang.RuntimeException: Unexpected error: java.security.InvalidAlgorithmParameterException: the trustAnchors parameter must be non-empty
14.04.2016 09:37:43 - Error while replicating: com.day.cq.replication.ReplicationException: Transfer failed for ReplicationAction{type=TEST, path[0]='/content/dam', time=1460651862089, userId='admin', revision='null'}. java.io.IOException: Failed to execute request 'https://<localhost>:8580/is-publish/publish-receiver?Cmd=Test&RootId=rbrough-osx2': java.lang.RuntimeException: Unexpected error: java.security.InvalidAlgorithmParameterException: the trustAnchors parameter must be non-empty
```

Of het foutenlogboek:

```shell
07.25.2019 12:00:59.893 *ERROR* [sling-threadpool-db2763bb-bc50-4bb5-bb64-10a09f432712-(apache-sling-job-thread-pool)-90-com_day_cq_replication_job_s7delivery(com/day/cq/replication/job/s7delivery)] com.day.cq.replication.Agent.s7delivery.queue Error during processing of replication.

java.io.IOException: Failed to execute request 'https://replicate-na.assetsadobe.com:8580/is-publish/publish-receiver?Cmd=Test&RootId=rbrough-osx': java.lang.RuntimeException: Unexpected error: java.security.InvalidAlgorithmParameterException: the trustAnchors parameter must be non-empty
        at com.scene7.is.catalog.service.publish.atomic.PublishingServiceHttp.executePost(PublishingServiceHttp.scala:195)
```

**Oplossing:**
Zorg ervoor dat het Java™-proces op de Experience Manager Auteur de systeemeigenschap heeft `-Djavax.net.ssl.trustStore=` ingesteld op een geldige truststore.

#### Probleem: KeyStore is niet ingesteld of is niet geïnitialiseerd {#problem-keystore-is-either-not-set-up-or-it-is-not-initialized}

Dit probleem wordt waarschijnlijk veroorzaakt door een hotfix of een functiepak die het dynamic-media-user of keystore-knooppunt overschrijft.

Voorbeeld van replicatielogboek:

```shell
Replication test to s7delivery:https://replicate-na.assetsadobe.com/is-publish
02.08.2016 14:37:44 - Transferring content for ReplicationAction{type=TEST, path[0]='/content/dam', time=1470173864834, userId='admin', revision='null'}
02.08.2016 14:37:44 - * Auth User: replication-receiver
02.08.2016 14:37:44 - * HTTP Version: 1.1
02.08.2016 14:37:44 - * Using OAuth 2.0 Authorization Grants
02.08.2016 14:37:44 - * OAuth 2.0 User: dynamic-media-replication
02.08.2016 14:37:44 - Transfer failed for ReplicationAction{type=TEST, path[0]='/content/dam', time=1470173864834, userId='admin', revision='null'}. com.adobe.granite.keystore.KeyStoreNotInitialisedException: Uninitialised key store for user dynamic-media-replication
```

**Oplossing:**

1. Ga naar de pagina Gebruikersbeheer:
   `localhost:4502/libs/granite/security/content/useradmin.html`
1. Ga op de pagina Gebruikersbeheer naar de `dynamic-media-replication` gebruiker, en selecteer vervolgens om te openen.
1. Selecteer de **[!UICONTROL KeyStore]** tab. Als de **[!UICONTROL Create KeyStore]** wordt weergegeven, moet u de stappen onder opnieuw uitvoeren [Verificatie instellen](#setting-up-authentication) eerder.
1. Als u de KeyStore-instelling opnieuw moest uitvoeren, moet u dat doen [De replicatieagent configureren](/help/assets/config-dynamic.md#configuring-the-replication-agent) ook hier weer.

   Wijzig de s7delivery Replication Agent.
   `localhost:4502/etc/replication/agents.author/s7delivery.html`

1. Selecteren **[!UICONTROL Test Connection]** zodat kunt u verifiëren dat de configuratie geldig is.

#### Probleem: publicatieagent gebruikt SSL in plaats van OAuth {#problem-publish-agent-is-using-ssl-instead-of-oauth}

Dit probleem wordt waarschijnlijk veroorzaakt door een hotfix of een functiepakket die de instellingen niet correct hebben geïnstalleerd of overschreven.

Voorbeeld van replicatielogboek:

```shell
01.08.2016 18:42:59 - Transferring content for ReplicationAction{type=TEST, path[0]='/content/dam', time=1470073379634, userId='admin', revision='null'}
01.08.2016 18:42:59 - * Auth User: replication-receiver
01.08.2016 18:42:59 - * HTTP Version: 1.1
01.08.2016 18:42:59 - * Using Client Auth SSL alias - replication-receiver *
01.08.2016 18:42:59 - Publishing: POST[https://replicate-eu.assetsadobe2.com:443/is-publish/publish-receiver?Cmd=Test&RootId=altayerstaging]
01.08.2016 18:42:59 - Transfer failed for ReplicationAction{type=TEST, path[0]='/content/dam', time=1470073379634, userId='admin', revision='null'}. java.io.IOException: Failed to execute request 'https://replicate-eu.assetsadobe2.com:443/is-publish/publish-receiver?Cmd=Test&RootId=rbroughstaging': Server returned status code 401 with message: Authorization required.
01.08.2016 18:42:59 - Error while replicating: com.day.cq.replication.ReplicationException: Transfer failed for ReplicationAction{type=TEST, path[0]='/content/dam', time=1470073379634, userId='admin', revision='null'}. java.io.IOException: Failed to execute request 'https://replicate-eu.assetsadobe2.com:443/is-publish/publish-receiver?Cmd=Test&RootId=rbroughstaging': Server returned status code 401 with message: Authorization required.
```

**Oplossing:**

1. Navigeer in Experience Manager naar **[!UICONTROL Tools]** > **[!UICONTROL General]** > **[!UICONTROL CRXDE Lite]**.

   `localhost:4502/crx/de/index.jsp`

1. Navigeer aan de knoop van de Agent van de Replicatie s7delivery.
   `localhost:4502/crx/de/index.jsp#/etc/replication/agents.author/s7delivery/jcr:content`

1. Deze instelling toevoegen aan de replicatieagent (Boolean met waarde ingesteld op **[!UICONTROL True]**):

   `enableOauth=true`

1. Selecteer in de linkerbovenhoek van de pagina de optie **[!UICONTROL Save All]**.

### Uw configuratie testen {#testing-your-configuration}

De Adobe adviseert dat u een test van begin tot eind van de configuratie uitvoert.

Zorg ervoor dat u het volgende al hebt gedaan voordat u deze test start:

* Voorinstellingen voor toegevoegde afbeelding.
* Configureren **[!UICONTROL Dynamic Media Configuration (Pre 6.3)]** onder Cloud Servicen. De afbeeldingsservice-URL is vereist voor deze test

**Om uw configuratie te testen:**

1. Upload een afbeeldingselement. (Navigeer in Elementen naar **[!UICONTROL Create]** > **[!UICONTROL Files]** en selecteer het bestand.)
1. Wacht tot de workflow is voltooid.
1. Publiceer het afbeeldingselement. (Selecteer het element en selecteer **[!UICONTROL Quick Publish]**.)
1. Navigeer naar de uitvoeringen voor die afbeelding door de afbeelding te openen en te tikken **[!UICONTROL Renditions]**.

   ![chlimage_1-510](assets/chlimage_1-510.png)

1. Selecteer een dynamische vertoning.
1. Selecteer **[!UICONTROL URL]**.
1. Navigeer naar de geselecteerde URL en controleer of de afbeelding zich naar behoren gedraagt.

U kunt ook testen of uw elementen zijn geleverd door req=exists aan uw URL toe te voegen.

## Dynamic Media-Cloud Servicen configureren {#configuring-dynamic-media-cloud-services}

De Dynamic Media-Cloud Service ondersteunt onder andere hybride publicatie en levering van afbeeldingen en video, videoanalyse en videocodering.

Als onderdeel van de configuratie moet u een registratie-id, een URL voor de videoservice, een URL voor de afbeeldingsservice, een URL voor de replicatieservice en een verificatieverificatie invoeren. Deze gegevens zijn per e-mail naar u verzonden als onderdeel van het proces voor het verschaffen van accounts. Als u deze informatie niet hebt ontvangen, neemt u contact op met de Adobe Experience Manager Administrator of Adobe Customer Support om deze informatie te vragen.

>[!NOTE]
>
Voordat u Dynamic Media-Cloud Servicen instelt, moet u eerst uw publicatieexemplaar hebben ingesteld. U moet ook replicatie hebben opstelling alvorens de Cloud Servicen van Dynamic Media te vormen.

**Dynamic Media-Cloud Servicen configureren:**

1. Selecteer in Experience Manager het logo van de Experience Manager voor toegang tot de algemene navigatieconsole en navigeer naar **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Dynamic Media Configuration (Pre-6.3)]**.
1. Selecteer in het linkerdeelvenster van de Dynamic Media Configuration Browser-pagina de optie **[!UICONTROL global]** selecteert u vervolgens **[!UICONTROL Create]**.
1. In de **[!UICONTROL Create Dynamic Media Configuration]** typt u een titel in het veld Titel.
1. Als u Dynamic Media for video configureert,

   * In de **[!UICONTROL Registration ID]** veld, typt u uw registratie-id.
   * In de **[!UICONTROL Video Service URL]** Voer de URL van de videoservice voor de Dynamic Media Gateway in.

1. Als u Dynamic Media configureert voor beeldbewerking, kunt u het volgende doen: **[!UICONTROL Image Service URL]** Voer de URL van de afbeeldingsservice voor de Dynamic Media Gateway in.
1. Selecteren **[!UICONTROL Save]** om terug te keren naar de Dynamic Media Configuration Browser-pagina.
1. Als u de globale navigatieconsole wilt openen, selecteert u het logo van de Experience Manager.

## Videorapportage configureren {#configuring-video-reporting}

Met Dynamic Media Hybrid kunt u videomelding configureren voor meerdere installaties van Experience Manager.

**Wanneer gebruiken:** Op het moment dat u Dynamic Media Configuration configureert (ouder dan 6.3), worden er veel functies gestart, waaronder videoverslag. De configuratie leidt tot een rapportreeks in een regionaal bedrijf Analytics. Als u veelvoudige knopen van de Auteur vormt, creeert u een afzonderlijke rapportreeks voor elke. Dit heeft tot gevolg dat de rapportage van gegevens tussen de installaties inconsistent is. Bovendien als elke knoop van de Auteur naar de zelfde Hybride Publish server verwijst, verandert de laatste installatie van de Auteur de reeks van het bestemmingsrapport voor al videorapportering. Deze kwestie overlaadt het systeem van Analytics met teveel rapportseries.

**Aan de slag:** Configureer videomelding door de volgende drie taken uit te voeren.

1. Maak een voorinstellingspakket voor Video Analytics nadat u Dynamic Media Configuration (Pre 6.3) hebt geconfigureerd op het eerste auteurknooppunt. Deze aanvankelijke taak is belangrijk omdat het een nieuwe configuratie toestaat om het gebruiken van de zelfde rapportreeks voort te zetten.
1. Installeer het vooraf ingestelde pakket voor Video Analytics op een willekeurige locatie ***new*** Auteur-knooppunt ***voor*** U configureert Dynamic Media Configuration (Pre 6.3).
1. Verifieer en zuivert de pakketinstallatie.

### Een vooraf ingesteld pakket voor videoanalyse maken nadat het eerste auteurknooppunt is geconfigureerd {#creating-a-video-analytics-preset-package-after-configuring-the-first-author-node}

Wanneer u deze taak hebt voltooid, hebt u een pakketbestand dat de voorinstellingen voor Video Analytics bevat. Deze voorinstellingen bevatten een rapportsuite, de trackingserver, de naamruimte voor bijhouden en de organisatie-id van het Experience Cloud, indien beschikbaar.

1. Indien u dit nog niet hebt gedaan, configureert u Dynamic Media Configuration (Pre 6.3).
1. (Optioneel) Geef de rapportsuite-id weer en kopieer deze. (U moet toegang hebben tot het JCR). Hoewel het niet nodig is om de rapportsuite-id te hebben, wordt de validatie eenvoudiger.
1. Maak een pakket met gebruik van Package Manager.
1. Bewerk het pakket om een filter op te nemen.

   In Experience Manager: `/conf/global/settings/dam/dm/presets/analytics/jcr:content/userdata`

1. Maak het pakket.
1. Download of deel het voorinstellingspakket voor Video Analytics, zodat het kan worden gedeeld met de volgende nieuwe auteurknooppunten.

### Installeer het voorinstellingspakket voor Video Analytics voordat u meer ontwerpknooppunten configureert {#installing-the-video-analytics-preset-package-before-you-configure-additional-author-nodes}

Zorg ervoor dat u deze taak uitvoert ***voor*** U configureert Dynamic Media Configuration (Pre 6.3). Als u dit niet doet, wordt er een andere ongebruikte rapportsuite gemaakt. Bovendien, alhoewel de video het melden correct blijft werken, wordt het verzamelen van gegevens niet geoptimaliseerd.

Zorg ervoor dat het vooraf ingestelde pakket voor Video Analytics van het eerste auteurknooppunt toegankelijk is op het nieuwe auteurknooppunt.

1. Upload het vooraf ingestelde pakket voor Video Analytics dat u eerder hebt gemaakt naar Package Manager.
1. Installeer het vooraf ingestelde pakket Video Analytics.
1. Dynamic Media-configuratie configureren (ouder dan 6.3).

### De installatie van het pakket controleren en fouten hierin opsporen {#verifying-and-debugging-the-package-installation}

1. Voer een van de volgende handelingen uit om de installatie van het pakket te controleren en, indien nodig, fouten op te sporen:

   * **Controleer de voorinstelling Video Analytics via het JCR**
Als u de voorinstelling Video-analyse via de JCR wilt controleren, moet u toegang hebben tot CRXDE Lite.

     Experience Manager - Navigeer in CRXDE Lite naar `/conf/global/settings/dam/dm/presets/analytics/jcr:content/userdata`

     Als in `https://localhost:4502/crx/de/index.jsp#/conf/global/settings/dam/dm/presets/analytics/jcr%3Acontent/userdata`

     Als u geen toegang hebt tot CRXDE Lite op het knooppunt Auteur, kunt u de voorinstelling controleren via de server Publiceren.

   * **Controleer de vooraf ingestelde Video Analytics via de Server van het Beeld**

     U kunt de voorinstelling Video-analyse rechtstreeks valideren door een verzoek om req=userdata in te dienen op een afbeeldingsserver.
Als u bijvoorbeeld de voorinstelling Analytics wilt weergeven op het knooppunt Auteur, kunt u het volgende verzoek indienen:

     `https://localhost:4502/is/image/conf/global/settings/dam/dm/presets/analytics?req=userdata`

     Als u de voorinstelling wilt valideren op publicatieservers, kunt u een vergelijkbare directe aanvraag indienen bij de publicatieserver. De reacties zijn hetzelfde op de knooppunten Auteur en Publiceren. De reactie ziet er ongeveer als volgt uit:

     ```
     marketingCloudOrgId=0FC4E86B573F99CC7F000101
      reportSuite=aemaem6397618-2018-05-23
      trackingNamespace=aemvideodal
      trackingServer=aemvideodal.d2.sc.omtrdc.net
     ```

   * **Controleer de voorinstelling Video Analytics via het gereedschap Video Rapportage in Experience Manager**
Navigeren naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Video Reporting]**

     `https://localhost:4502/mnt/overlay/dam/gui/content/s7dam/videoreports/videoreport.html`

     Als u het volgende foutbericht ziet, is de rapportsuite beschikbaar, maar niet gevuld. Deze fout is correct-en gewenst-in een nieuwe installatie alvorens het systeem om het even welke gegevens verzamelt.

   ![screen_shot_2018-05-23at52254pm](assets/screen_shot_2018-05-23at52254pm.png)

   Als u rapportgegevens wilt genereren, uploadt en publiceert u één video. Gebruiken **[!UICONTROL Copy URL]** en voer de video minstens één keer uit.

   Het kan 12 uur duren voordat de rapportgegevens zijn gevuld met het gebruik van de Video Viewer.

   Als er een fout is en de rapportreeks niet correct wordt geplaatst, wordt het volgende alarm getoond.

   ![screen_shot_2018-05-23at52612pm](assets/screen_shot_2018-05-23at52612pm.png)

   Deze fout wordt ook weergegeven als Video Reporting wordt uitgevoerd voordat u Dynamic Media Configuration (Pre 6.3)-services configureert.

### Los de video rapporteringsconfiguratie problemen op {#troubleshooting-the-video-reporting-configuration}

* Tijdens de installatie zijn soms verbindingen met de Analytics API-server onderbroken. De installatie probeert de verbinding 20 keer opnieuw, maar het ontbreekt nog. Wanneer deze situatie voorkomt, registreert het logboekdossier veelvoudige fouten. Zoeken naar `SiteCatalystReportService`.
* Als u het pakket met voorinstellingen voor analysemogelijkheden niet eerst installeert, wordt mogelijk een nieuwe rapportsuite gemaakt.
* De bevordering van Experience Manager 6.3 aan Experience Manager 6.4 of Experience Manager 6.4.1, dan het vormen van de Configuratie van Dynamic Media (pre 6.3), leidt nog tot een rapportreeks. Dit probleem is bekend en moet worden opgelost voor Experience Manager 6.4.2.

### Informatie over de voorinstelling Video Analytics {#about-the-video-analytics-preset}

De voorinstelling voor Video-analyse (ook wel analysevoorinstelling genoemd) wordt naast de voorinstellingen voor de viewer in Dynamic Media opgeslagen. Het is in feite hetzelfde als een voorinstelling voor viewers, maar met informatie die wordt gebruikt om AppMeasurement- en videorecittering te configureren.

De eigenschappen van de voorinstelling zijn als volgt:

* `reportSuite`
* `trackingServer`
* `trackingNamespace`
* `marketingCloudOrgId` (niet aanwezig in oudere versies van Experience Managers)

Experience Manager 6.4 en nieuwere versies slaan deze voorinstelling op `/conf/global/settings/dam/dm/presets/analytics/jcr:content/userdata`

## Catalogusinstellingen repliceren {#replicating-catalog-settings}

Publiceer uw eigen standaardinstellingen voor de catalogus als onderdeel van het installatieproces via het JCR. Catalogusinstellingen herhalen:

1. In een Eindvenster, stel het volgende in werking:

   `curl -u admin:admin localhost:4502/libs/settings/dam/dm/presets/viewer.pushviewerpresets`

1. Navigeer in Experience Manager naar de volgende locatie in CRXDE Lite (vereist beheerdersrechten):

   `https://<*server*>:<*port*>/crx/de/index.jsp#/conf/global/settings/dam/dm/imageserver/`

1. Selecteer de **[!UICONTROL Replication]** tab.
1. Selecteren **[!UICONTROL Replicate]**.

## Viewervoorinstellingen repliceren {#replicating-viewer-presets}

Om *een middel met een vooraf ingestelde kijker, moet u herhalen/publiceren* de viewervoorinstelling. (Alle viewervoorinstellingen moeten zijn geactiveerd *en* gerepliceerd om de URL of insluitcode voor een element te verkrijgen.
Zie [Voorinstellingen voor viewers publiceren](/help/assets/managing-viewer-presets.md#publishing-viewer-presets) voor meer informatie .

>[!NOTE]
>
Standaard worden in het systeem verschillende uitvoeringen weergegeven wanneer u **[!UICONTROL Renditions]** en diverse viewervoorinstellingen wanneer u **[!UICONTROL Viewers]** in de gedetailleerde weergave van het element. U kunt het aantal dat u ziet verhogen of verlagen. Zie [Het aantal weergegeven voorinstellingen voor afbeeldingen vergroten](/help/assets/managing-image-presets.md#increasing-or-decreasing-the-number-of-image-presets-that-display) of [Het aantal weergegeven viewervoorinstellingen vergroten](/help/assets/managing-viewer-presets.md#increasing-the-number-of-viewer-presets-that-display).

## Elementen filteren voor replicatie {#filtering-assets-for-replication}

Bij niet-Dynamic Media-implementaties repliceert u *alles* elementen (zowel afbeeldingen als video) van de ontwerpomgeving van de Experience Manager naar het publicatieknooppunt van de Experience Manager. Deze workflow is nodig omdat de Experience Manager Publish-servers ook de elementen leveren.

Bij Dynamic Media-implementaties is het echter niet nodig dezelfde middelen te repliceren naar publicatieknooppunten van Experience Managers, omdat assets via de cloud worden geleverd. Zo voorkomt u extra opslagkosten en langere verwerkingstijden om elementen te repliceren. Andere inhoud, zoals Dynamic Media-viewers, sitepagina&#39;s en statische inhoud, wordt nog steeds aangeboden vanaf de publicatieknooppunten van de Experience Manager.

Naast het repliceren van de activa, worden de volgende niet-activa ook herhaald:

* Dynamic Media-leveringsconfiguratie: `/conf/global/settings/dam/dm/imageserver/jcr:content`
* Voorinstellingen afbeelding: `/conf/global/settings/dam/dm/presets/macros`
* Voorinstellingen viewer: `/conf/global/settings/dam/dm/presets/viewer`

Met de filters kunt u *uitsluiten* elementen die worden gerepliceerd naar het publicatieknooppunt Experience Manager.

### Standaardelementfilters gebruiken voor replicatie {#using-default-asset-filters-for-replication}

Als u Dynamic Media gebruikt voor (1) beeldbewerking in productie *of* (2) beeldbewerking en video, kunt u de standaardfilters gebruiken die Adobe &#39;as-is&#39; biedt. De volgende filters zijn standaard actief:

<table>
 <tbody>
  <tr>
   <td> </td>
   <td><strong>Filter</strong></td>
   <td><strong>MIME-type</strong></td>
   <td><strong>Uitvoeringen</strong></td>
  </tr>
  <tr>
   <td>Afbeeldingen leveren op Dynamic Media</td>
   <td><p>filterafbeeldingen</p> <p>filtersets</p> <p> </p> </td>
   <td><p>Begint met <strong>image/</strong></p> <p>Bevat <strong>application/</strong> en eindigt met <strong>set</strong>.</p> </td>
   <td>De 'filter-images' die buiten het vak (voor afzonderlijke afbeeldingselementen, inclusief interactieve afbeeldingen) en 'filtersets' (voor centrifuges, afbeeldingssets, gemengde mediasets en Carousel-sets) worden gebruikt, zijn:
    <ul>
     <li>Inclusief PTIFF-afbeeldingen en metagegevens voor replicatie (elke uitvoering die begint met <strong>cqdam</strong>).</li>
     <li>Sluit de oorspronkelijke afbeelding en statische afbeeldingsuitvoeringen uit van replicatie.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Dynamic Media Video Delivery</td>
   <td>filter-video</td>
   <td>Begint met <strong>video/</strong></td>
   <td>De uit-van-de-doos "filter-video"zal:
    <ul>
     <li>Inclusief proxy-video-uitvoeringen, videominiatuur/posterafbeelding, metagegevens (zowel bij bovenliggende video als bij video-uitvoeringen) voor replicatie (Willekeurige uitvoering die begint met <strong>cqdam</strong>).</li>
     <li>Sluit de originele video en statische miniatuuruitvoeringen uit van replicatie.<br /> <br /> <strong>Opmerking:</strong> De proxy-video-uitvoeringen bevatten geen binaire elementen, maar zijn in plaats daarvan alleen knooppunteigenschappen. Er is dus geen invloed op de grootte van de uitgeversopslagplaats.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Integratie van Dynamic Media Classic (Scene7)</td>
   <td><p>filterafbeeldingen</p> <p>filtersets</p> <p>filter-video</p> </td>
   <td><p>Begint met <strong>image/</strong></p> <p>Bevat <strong>application/</strong> en eindigt met <strong>set</strong>.</p> <p>Begint met <strong>video/</strong></p> </td>
   <td><p>U vormt het Vervoer URI om aan uw Experience Manager te richten publiceert server in plaats van de Adobe van de Dienst URL van de Replicatie van de Wolk van Dynamic Media. Door dit filter in te stellen, kan Dynamic Media Classic elementen leveren in plaats van de Experience Manager-publicatie-instantie.</p> <p>Met de 'filter-images', 'filtersets' en 'filter-video' uit de box worden:</p>
    <ul>
     <li>Inclusief PTIFF-afbeelding, proxyvideo-uitvoeringen en metagegevens voor replicatie. Maar omdat ze niet bestaan in het JCR-programma voor degenen die Experience Manager voeren - integratie in Dynamic Media Classic - doet het in feite niets.</li>
     <li>Sluit de oorspronkelijke afbeelding, statische afbeeldingsuitvoeringen, oorspronkelijke video en statische miniatuuruitvoeringen uit van replicatie. In plaats daarvan levert Dynamic Media Classic afbeeldingen en video-elementen.</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
Filters zijn van toepassing op MIME-typen en kunnen geen padspecifieke notatie hebben.

### Elementfilters instellen voor alleen-video-implementaties {#setting-up-asset-filters-for-video-only-deployments}

Als u Dynamic Media alleen voor video gebruikt, voert u de volgende stappen uit om elementfilters voor replicatie in te stellen:

1. Selecteer in Experience Manager het logo van de Experience Manager voor toegang tot de algemene navigatieconsole en navigeer naar **[!UICONTROL Tools]** > **[!UICONTROL Deployment]** > **[!UICONTROL Replication]** > **[!UICONTROL Agents on author]**.
1. Selecteer op de pagina Agents op de auteurspagina de optie **[!UICONTROL Default Agent (publish)]**.
1. Selecteren **[!UICONTROL Edit]**.
1. In de **[!UICONTROL Agent Settings]** in het dialoogvenster **[!UICONTROL Settings]** tab, check **[!UICONTROL Enabled]** om de agent in te schakelen.
1. Selecteren **[!UICONTROL OK]**.
1. Navigeer in Experience Manager naar **[!UICONTROL Tools]** > **[!UICONTROL General]** > **[!UICONTROL CRXDE Lite]**.
1. Navigeer in de linkermappenstructuur naar `/etc/replication/agents.author/dynamic_media_replication/jcr:content/damRenditionFilters`
1. Zoeken **[!UICONTROL filter-video]**, klikt u er met de rechtermuisknop op en selecteert u vervolgens **[!UICONTROL Copy]**.
1. Navigeer in de linkermappenstructuur naar `/etc/replication/agents.author/publish`
1. Zoeken `jcr:content`, klikt u er met de rechtermuisknop op en selecteert u vervolgens **[!UICONTROL Paste]**.

Met deze stappen stelt u de publicatieinstantie van de Experience Manager zo in dat de video-posterafbeelding en de videometagegevens die zijn vereist voor het afspelen, worden geleverd terwijl de video zelf wordt geleverd door de Dynamic Media-Cloud Service. Het filter sluit de originele video en statische miniatuurweergaven, die niet nodig zijn voor de publicatie-instantie, uit van replicatie.

### Elementfilters instellen voor imaging in implementaties buiten de productie {#setting-up-asset-filters-for-imaging-in-non-production-deployments}

Als u Dynamic Media gebruikt voor het maken van images in implementaties die niet voor productiedoeleinden worden gebruikt, voert u de volgende stappen uit om elementfilters voor replicatie in te stellen:

1. Selecteer in Experience Manager het logo van de Experience Manager voor toegang tot de algemene navigatieconsole en navigeer naar **[!UICONTROL Tools]** > **[!UICONTROL Deployment]** > **[!UICONTROL Replication]** > **[!UICONTROL Agents on author]**.
1. Selecteer op de pagina Agents op de auteurspagina de optie **[!UICONTROL Default Agent (publish)]**.
1. Selecteren **[!UICONTROL Edit]**.
1. In de **[!UICONTROL Agent Settings]** in het dialoogvenster **[!UICONTROL Settings]** tab, check **[!UICONTROL Enabled]** om de agent in te schakelen.
1. Selecteren **[!UICONTROL OK]**.
1. Navigeer in Experience Manager naar **[!UICONTROL Tools]** > **[!UICONTROL General]** > **[!UICONTROL CRXDE Lite]**.
1. Navigeer in de linkermappenstructuur naar `/etc/replication/agents.author/dynamic_media_replication/jcr:content/damRenditionFilters`

   ![image-2018-01-16-10-22-40-410](assets/image-2018-01-16-10-22-40-410.png)

1. Zoeken **[!UICONTROL filter-images]**, klikt u er met de rechtermuisknop op en selecteert u vervolgens **[!UICONTROL Copy]**.
1. Navigeer in de linkermappenstructuur naar `/etc/replication/agents.author/publish`
1. Zoeken `jcr:content`, klikt u er met de rechtermuisknop op en gaat u naar **[!UICONTROL Create]** > **[!UICONTROL Create Node]**. Voer de naam in `damRenditionFilters` van het type `nt:unstructured`.
1. Zoeken `damRenditionFilters`, klikt u er met de rechtermuisknop op en selecteert u vervolgens **[!UICONTROL Paste]**.

Deze stappen plaatsen opstelling de Experience Manager publiceer instantie om de beelden aan uw niet productiemilieu te leveren. Het filter sluit de oorspronkelijke afbeelding en statische uitvoeringen, die niet nodig zijn voor de publicatie-instantie, ook uit van replicatie.

>[!NOTE]
>
Als er vele verschillende filters in een auteur zijn, heeft elke agent een verschillende gebruiker nodig die aan het wordt toegewezen. De granietcode dwingt het model van één filter per gebruiker af. Zorg altijd voor een andere gebruiker voor elke filterinstelling.
>
Gebruikt u meer dan één filter op een server? Bijvoorbeeld, één filter voor replicatie om te publiceren en een tweede filter voor s7delivery. Als dat het geval is, moet u ervoor zorgen dat deze twee filters een andere instelling hebben **userId** die aan hen in `jcr:content` knooppunt. Zie de volgende afbeelding:

![image-2018-01-16-10-26-28-465](assets/image-2018-01-16-10-26-28-465.png)

### Elementfilters aanpassen voor replicatie (optioneel) {#customizing-asset-filters-for-replication}

1. Selecteer in Experience Manager het logo van de Experience Manager voor toegang tot de algemene navigatieconsole en navigeer naar **[!UICONTROL Tools]** > **[!UICONTROL General]** > **[!UICONTROL CRXDE Lite]**.
1. Navigeer in de linkermappenstructuur naar `/etc/replication/agents.author/dynamic_media_replication/jcr:content/damRenditionFilters` om de filters te bekijken.

   ![chlimage_1-511](assets/chlimage_1-511.png)

1. Als u het Mime-type voor het filter wilt definiëren, gaat u als volgt naar het Mime-type:

   Vouw in de linkerspoorstaaf uit `content > dam > <locate_your_asset> >  jcr:content > metadata` en vervolgens in de tabel, zoekt u `dc:format`.

   De volgende afbeelding is een voorbeeld van het pad van een element naar `dc:format`.

   ![chlimage_1-512](assets/chlimage_1-512.png)

   Let erop dat de `dc:format` voor het actief `Fiji Red.jpg` is `image/jpeg`.

   Als u dit filter wilt toepassen op alle afbeeldingen, ongeacht de indeling, stelt u de waarde in op `image/*` waar `*` is een reguliere expressie die wordt toegepast op alle afbeeldingen in elke indeling.

   Als u het filter alleen wilt toepassen op afbeeldingen van het type JPEG, voert u een waarde in van `image/jpeg`.

1. Bepaal welke uitvoeringen u van replicatie wilt omvatten of uitsluiten.

   U kunt onder andere de volgende tekens gebruiken om te filteren voor replicatie:

   | Te gebruiken teken | Hoe het activa voor replicatie filtreert |
   | --- | --- |
   | `*` | Jokerteken |
   | `+` | Bevat elementen voor replicatie |
   | `-` | Sluit elementen van replicatie uit |

   Navigeren naar `content/dam/<locate your asset>/jcr:content/renditions`.

   De volgende afbeelding is een voorbeeld van de uitvoeringen van een element.

   ![chlimage_1-513](assets/chlimage_1-4.png)

   Als u het bovenstaande voorbeeld gebruikt en alleen de PTIFF (Pyramid TIFF) wilt repliceren, voert u `+cqdam,*` inclusief alle uitvoeringen waarmee wordt gestart `cqdam`. In het voorbeeld is die vertoning `cqdam.pyramid.tiff`.

   Als u alleen het origineel wilt repliceren, voert u `+original`.

## Dynamic Media Image Server-instellingen configureren {#configuring-dynamic-media-image-server-settings}

Als u de Dynamic Media Image Server configureert, moet u de Adobe CQ Scene7 ImageServer-bundel en de Adobe CQ Scene7 PlatformServer-bundel bewerken.

>[!NOTE]
>
Dynamic Media werkt buiten de doos [nadat deze is ingeschakeld](#enabling-dynamic-media). U kunt echter desgewenst de installatie verfijnen door Dynamic Media Image Server te configureren om aan bepaalde specificaties of vereisten te voldoen.

**Vereiste** - *Voor* Als u Dynamic Media Image Server configureert, dient u ervoor te zorgen dat uw VM van Windows® een installatie van de Microsoft® Visual C++-bibliotheken omvat. De bibliotheken zijn nodig om Dynamic Media Image Server uit te voeren. U kunt [Download het Microsoft® Visual C++ 2010 Redistributable Package (x64) hier](https://www.microsoft.com/en-us/download/details.aspx?id=26999).

Dynamic Media Image Server-instellingen configureren:

1. Selecteer in de linkerbovenhoek van de Experience Manager de optie **[!UICONTROL Adobe Experience Manager]** om tot de globale navigatieconsole toegang te hebben, dan navigeer aan **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]**.
1. Ga op de Adobe Experience Manager Web Console Configuration-pagina naar **[!UICONTROL OSGi]** > **[!UICONTROL Configuration]** om alle bundels weer te geven die momenteel binnen de Experience Manager worden uitgevoerd.

   De Dynamic Media Delivery Servers staan onder de volgende namen in de lijst:

   * `Adobe CQ Scene7 ImageServer`
   * `Adobe CQ Scene7 PlatformServer`

1. Selecteer in de lijst met bundels rechts van Adobe CQ Scene7 ImageServer de optie **[!UICONTROL Edit]** pictogram.
1. Stel in het dialoogvenster Adobe CQ Scene7 ImageServer de volgende configuratiewaarden in:

   >[!NOTE]
   >
   Gewoonlijk hoeven de standaardwaarden niet te worden gewijzigd. Als u de standaardwaarden echter wijzigt, moet u de bundel opnieuw starten voordat de wijzigingen van kracht worden.

   | Eigenschap | Standaardwaarde | Beschrijving |
   | --- | --- | --- |
   | `TcpPort.name` | *`empty`* | Het aantal van de haven voor communicatie met het proces ImageServer te gebruiken. Standaard wordt de vrije poort automatisch gedetecteerd. |
   | `AllowRemoteAccess.name` | *`empty`* | Externe toegang tot ImageServer-proces toestaan of weigeren. Indien onwaar, luistert de beeldserver slechts op localhost.<br> De standaard montages van de externalizer die aan localhost richten moeten het daadwerkelijke domein of IP adres van de specifieke VM instantie specificeren. De reden is dat de localhost naar het hoofdsysteem van de VM wijst.<br>Domeinen of IP-adressen voor de VM moeten een vermelding van het hostbestand hebben, zodat deze zichzelf kan oplossen. |
   | `MaxRenderRgnPixels` | 16 MP | Maximale grootte in megapixels die wordt weergegeven. |
   | `MaxMessageSize` | 16 MB | Maximale berichtgrootte in megabytes die wordt geleverd. |
   | `RandomAccessUrlTimeout` | 20 | De waarde van de tijd uit voor hoe lang in seconden de Server van het Beeld op JCR wacht om op een gerangschikte tegelverzoek te antwoorden. |
   | `WorkerThreads` | 10 | Aantal arbeidersdraden. |

1. Selecteren **[!UICONTROL Save]**.
1. Selecteer in de lijst met bundels rechts van Adobe CQ Scene7 PlatformServer de optie **[!UICONTROL Edit]** pictogram.
1. Stel in het dialoogvenster Adobe CQ Scene7 PlatformServer de volgende standaardopties in:

   >[!NOTE]
   >
   Dynamic Media Image Server gebruikt een eigen schijfcache om reacties in de cache op te slaan. De Experience Manager HTTP-cache en de Dispatcher kunnen niet worden gebruikt om reacties van Dynamic Media Image Server in cache te plaatsen.

   | Eigenschap | Standaardwaarde | Beschrijving |
   |---|---|---|
   | Cache ingeschakeld | Ingeschakeld | Of de responscache is ingeschakeld |
   | Cachewortels | cachegeheugen | Een of meer paden naar de responscachemappen. Relatieve paden worden omgezet in de interne bundelmap s7imaging. |
   | Max. grootte cache | 200000000 | Maximale grootte van responscache in bytes. |
   | Max. items in cache | 100000 | Maximumaantal items dat is toegestaan in de cache. |

### Standaardinstellingen voor manifest {#default-manifest-settings}

Standaard manifest laat u de gebreken vormen die worden gebruikt om de antwoorden van de Levering van Dynamic Media te produceren. U kunt de kwaliteit (kwaliteit van de JPEG, de resolutie, het opnieuw berekenen van het aantal pixels), het in cache plaatsen (verlopen) verfijnen en het renderen van te grote afbeeldingen voorkomen (standaardpixel, standaardminiatuur, maxpix).

De plaats van de standaard manifeste configuratie wordt genomen van **[!UICONTROL Catalog root]** standaardwaarde van de **[!UICONTROL Adobe CQ Scene7 PlatformServer]** bundel. Deze waarde staat standaard op het volgende pad binnen **[!UICONTROL Tools]** > **[!UICONTROL General]** > **[!UICONTROL CRXDE Lite]**

`/conf/global/settings/dam/dm/imageserver/`

![Afbeeldingsserver configureren in CRXDE Lite](assets/configimageservercrxdelite.png)

U kunt de waarden van de eigenschappen wijzigen, zoals wordt beschreven in de onderstaande tabel, door nieuwe waarden in te voeren.

Wanneer u klaar bent met het wijzigen van het standaardmanifest, selecteert u in de linkerbovenhoek van de pagina **[!UICONTROL Save All]**.

Zorg ervoor dat u de optie **[!UICONTROL Access Control]** (rechts van het tabblad Eigenschappen), stelt u vervolgens de toegangsbeheerbevoegdheden in op `jcr:read` voor alle gebruikers en voor gebruikers met dynamische media-replicatie.

![Afbeeldingsserver in CRXDE Lite configureren en het tabblad Toegangsbeheer instellen](assets/configimageservercrxdeliteaccesscontroltab.png)

Instellingen voor de manifestatie en de standaardwaarden ervan:

| Eigenschap | Standaardwaarde | Beschrijving |
| --- | --- | --- |
| `bkgcolor` | `FFFFFF` | Standaardachtergrondkleur. De RGB-waarde die wordt gebruikt om elk gebied van een antwoordafbeelding dat geen werkelijke afbeeldingsgegevens bevat, in te vullen. Zie ook [BkgColor](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-bkgcolor.html#image-serving-api) in de Image Serving API. |
| `defaultpix` | `300,300` | Standaardweergavegrootte. De server beperkt antwoordafbeeldingen tot maximaal deze breedte en hoogte als in de aanvraag niet expliciet de weergavegrootte wordt opgegeven met wid=, hei= of scl=.<br>Opgegeven als twee gehele getallen, 0 of groter, gescheiden door een komma. Breedte en hoogte in pixels. U kunt een van beide of beide waarden instellen op 0 om ze onbeperkt te houden. Is niet van toepassing op geneste/ingesloten aanvragen.<br>Zie ook [DefaultPix](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-defaultpix.html#image-serving-api) in de Image Serving API.<br>Gewoonlijk gebruikt u echter een viewer-voorinstelling of een voorinstelling voor afbeeldingen om het element te leveren. De standaardvoorinstelling is alleen van toepassing op elementen die geen viewervoorinstelling of voorinstelling voor afbeeldingen gebruiken. |
| `defaultthumbpix` | `100,100` | Standaardminiatuurgrootte. Gebruikt in plaats van kenmerk::DefaultPix voor miniatuuraanvragen (`req=tmb`).<br>De server beperkt de antwoordafbeeldingen tot maximaal deze breedte en hoogte. Deze actie is waar als een miniatuurverzoek (`req=tmb`) wordt de grootte niet expliciet opgegeven en wordt de weergavegrootte niet expliciet opgegeven met `wid=`, `hei=`, of `scl=`.<br>Opgegeven als twee gehele getallen, 0 of groter, gescheiden door een komma. Breedte en hoogte in pixels. U kunt een van beide of beide waarden instellen op 0 om ze onbeperkt te houden.<br>Is niet van toepassing op geneste/ingesloten aanvragen.<br>Zie ook [DefaultThumbPix](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-defaultthumbpix.html#image-serving-api) in de Image Serving API. |
| `expiration` | `36000000` | De standaardtijd voor de clientcache om te live gaan. Biedt een standaardvervalinterval voor het geval dat een bepaalde catalogusrecord geen geldige catalogus bevat::Expiration value.<br>Reëel getal, 0 of hoger. Aantal milliseconden tot aan vervaldatum sinds de antwoordgegevens werden geproduceerd. Reeks aan 0 om altijd het antwoordbeeld onmiddellijk te verlopen, dat effectief cliënt caching onbruikbaar maakt. Deze waarde wordt standaard ingesteld op 10 uur. Als een nieuwe afbeelding wordt gepubliceerd, duurt het tien uur voordat de oude afbeelding de cache van de gebruiker verlaat. Neem contact op met de Klantenondersteuning als u de cache sneller moet wissen.<br>Zie ook [Verlopen](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-expiration.html) in de Image Serving API. |
| `jpegquality` | `80` | Standaardcoderingskenmerken van JPEG. Hiermee geeft u de standaardkenmerken op voor JPEG-antwoordafbeeldingen.<br>Geheel getal en markering, gescheiden door een komma. De eerste waarde ligt in het bereik 1.100 en definieert de kwaliteit. De tweede waarde kan 0 zijn voor normaal gedrag of 1 voor het uitschakelen van de downsampling van RGB-chromaticiteit door JPEG-encoders.<br>Zie ook [JpegQuality](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-jpegquality.html#image-serving-api) in de Image Serving API. |
| `maxpix` | `2000,2000` | Limiet voor afbeeldingsgrootte beantwoorden. Maximale breedte en hoogte van antwoordafbeelding die aan de client worden geretourneerd.<br>De server retourneert een fout als een aanvraag een antwoordafbeelding veroorzaakt waarvan de breedte of hoogte groter is dan kenmerk::MaxPix.<br>Zie ook [MaxPix](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-maxpix.html#image-serving-api) in de Image Serving API. |
| `resmode` | `SHARP2` | Standaardmodus voor opnieuw berekenen van pixels. Hiermee geeft u de standaardkenmerken voor resampling en interpolatie op die moeten worden gebruikt voor het schalen van afbeeldingsgegevens.<br>Wordt gebruikt wanneer `resMode=` wordt niet opgegeven in een aanvraag.<br>Toegestane waarden worden opgenomen `BILIN`, `BICUB`, of `SHARP2`.<br>Enum. Instellen op 2 voor `bilin`, 3 voor `bicub`, of 4 voor `sharp2` interpolatiemodus. Gebruiken `sharp2` voor de beste resultaten.<br>Zie ook [ResMode](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-is-cat-resmode.html#image-serving-api) in de Image Serving API. |
| `resolution` | `72` | Standaardobjectresolutie. Biedt een standaardobjectresolutie voor het geval een bepaalde catalogusrecord geen geldige catalogus bevat::resolutiewaarde.<br>Real number, groter dan 0. Doorgaans uitgedrukt als pixels per inch, maar ook in andere eenheden, zoals pixels per meter.<br>Zie ook [Resolutie](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-resolution.html#image-serving-api) in de Image Serving API. |
| `thumbnailtime` | `1%,11%,21%,31%,41%,51%,61%,71%,81%,91%` | Deze waarden vertegenwoordigen een momentopname van de videoplaytime en worden overgegaan tot [encoding.com](https://www.encoding.com/). Zie [Informatie over videominiatuur](/help/assets/video.md#about-video-thumbnails-in-dynamic-media-hybrid-mode) voor meer informatie . |

## Dynamic Media-kleurbeheer configureren {#configuring-dynamic-media-color-management}

Met Dynamic Media-kleurbeheer kunt u correcte elementen kleuren om ze voor te vertonen.

Met kleurcorrectie behouden ingesloten elementen hun kleurruimte (RGB, CMYK, Grijs) en ingesloten kleurprofiel in de gegenereerde piramide-TIFF-uitvoering. Wanneer u een dynamische uitvoering aanvraagt, wordt de afbeeldingskleur gecorrigeerd in de doelkleurruimte. U configureert het uitvoerkleurprofiel in de Dynamic Media-publicatie-instellingen in de JCR.

In het kleurbeheer van de Adobe worden ICC-profielen (International Color Consortium) gebruikt, een indeling die door de ICC wordt gedefinieerd.

U kunt Dynamic Media-kleurbeheer configureren en voorinstellingen voor afbeeldingen configureren met CMYK, RGB of Grijsuitvoer. Zie [Voorinstellingen voor afbeeldingen configureren](/help/assets/managing-image-presets.md).

Gevallen voor geavanceerd gebruik kunnen een handmatige configuratie gebruiken `icc=` Hiermee kunt u expliciet een uitvoerkleurprofiel selecteren:

* `icc` - [https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-icc.html](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-icc.html)

* `iccEmbed` - [https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-iccembed.html](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-iccembed.html)

>[!NOTE]
>
De standaardset kleurprofielen van de Adobe is alleen beschikbaar als u [Feature Pack 12445 van de Distributie van de Software](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/featurepack/cq-6.3.0-featurepack-12445) geïnstalleerd. Alle eigenschapspakken en de dienstpakken zijn beschikbaar bij [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html). Feature Pack 12445 biedt kleurprofielen van de Adobe.


### Functiepakket 12445 installeren {#installing-feature-pack}

Installeer functiepak 12445 om de Dynamic Media-mogelijkheden voor kleurbeheer te gebruiken.

**Voor de installatie van functiepak 12445:**

1. Navigeren naar [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) en download `cq-6.3.0-featurepack-12445`.

   Zie [Werken met pakketten](/help/sites-administering/package-manager.md) voor meer informatie over het gebruik van pakketten in [!DNL Adobe Experience Manager].

1. Installeer het functiepakket.

### De standaardkleurprofielen configureren {#configuring-the-default-color-profiles}

Nadat u het functiepakket hebt geïnstalleerd, configureert u de juiste standaardkleurprofielen om kleurcorrectie in te schakelen wanneer u om RGB- of CMYK-afbeeldingsgegevens vraagt.

**De standaardkleurprofielen configureren:**

1. In **[!UICONTROL Tools]** > **[!UICONTROL General]** > **[!UICONTROL CRXDE Lite]**, navigeer naar `/conf/global/settings/dam/dm/imageserver/jcr:content` die de standaard Adobe Color-profielen bevat.

   ![chlimage_1-514](assets/chlimage_1-514.png)

1. Voeg een eigenschap voor kleurcorrectie toe door naar de onderkant van het deelvenster **[!UICONTROL Properties]** tab. Voer handmatig de naam, het type en de waarde van de eigenschap in, die in de volgende tabellen worden beschreven. Nadat u de waarden hebt ingevoerd, selecteert u **[!UICONTROL Add]** en vervolgens **[!UICONTROL Save All]** om uw waarden op te slaan.

   De eigenschappen voor kleurcorrectie worden beschreven in het dialoogvenster **Eigenschappen van kleurcorrectie** tabel. Waarden die u kunt toewijzen aan eigenschappen voor kleurcorrectie bevinden zich in de **Kleurprofiel** tabel.

   Bijvoorbeeld in **[!UICONTROL Name]**, toevoegen `iccprofilecmyk`, selecteert u **[!UICONTROL Type]** `String`en toevoegen `WebCoated` als **[!UICONTROL Value]**. Selecteer vervolgens **[!UICONTROL Add]** en vervolgens **[!UICONTROL Save All]** om uw waarden op te slaan.

   ![chlimage_1-515](assets/chlimage_1-515.png)

   **Tabel met kleurcorrectie-eigenschappen**

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschap</strong></td>
   <td><strong>Type</strong></td>
   <td><strong>Standaard</strong></td>
   <td><strong>Beschrijving</strong></td>
  </tr>
  <tr>
   <td><a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccprofilergb.html">iccprofilergb</a></td>
   <td>String</td>
   <td>&lt;empty&gt;</td>
   <td>Naam van het standaardkleurprofiel RGB.</td>
  </tr>
  <tr>
   <td><a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccprofilecmyk.html">icprofilecmyk</a></td>
   <td>String</td>
   <td>&lt;empty&gt;</td>
   <td>Naam van het standaard CMYK-kleurprofiel.</td>
  </tr>
  <tr>
   <td><a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccprofilegray.html">icprofilegray</a></td>
   <td>String</td>
   <td>&lt;empty&gt;</td>
   <td>Naam van het standaardkleurprofiel Grijs.</td>
  </tr>
  <tr>
   <td><a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccprofilesrcrgb.html">iccprofilesrcrgb</a></td>
   <td>String</td>
   <td>&lt;empty&gt;</td>
   <td>Naam van het standaardkleurprofiel RGB dat wordt gebruikt voor RGB-afbeeldingen zonder ingesloten kleurprofiel</td>
  </tr>
  <tr>
   <td><a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccprofilesrccmyk.html">iccprofilesrcmyk</a></td>
   <td>String</td>
   <td>&lt;empty&gt;</td>
   <td>Naam van het standaard CMYK-kleurprofiel dat wordt gebruikt voor CMYK-afbeeldingen zonder ingesloten kleurprofiel.</td>
  </tr>
  <tr>
   <td><a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccprofilesrcgray.html">iccprofilesrcgray</a></td>
   <td>String</td>
   <td>&lt;empty&gt;</td>
   <td>Naam van het standaard grijskleurprofiel dat wordt gebruikt voor CMYK-afbeeldingen zonder ingesloten kleurprofiel.</td>
  </tr>
  <tr>
   <td><a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccblackpointcompensation.html">icblackpointcompensatie</a></td>
   <td>Boolean</td>
   <td>Waar</td>
   <td>Hiermee wordt opgegeven of zwartpuntcompensatie wordt toegepast tijdens kleurcorrectie. Adobe raadt aan deze instelling in te schakelen.</td>
  </tr>
  <tr>
   <td><a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccdither.html">icdithering</a></td>
   <td>Boolean</td>
   <td>Onwaar</td>
   <td>Hiermee bepaalt u of dithering wordt toegepast tijdens kleurcorrectie.</td>
  </tr>
  <tr>
   <td><a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccrenderintent.html">iccrenderintent</a></td>
   <td>String</td>
   <td>relatief</td>
   <td><p>Geeft de render-intentie aan. Acceptabele waarden zijn: <strong>perceptueel, relatief, verzadiging, absoluut. </strong><i></i>Adobe beveelt aan <strong>relatief </strong><i></i>als de standaardinstelling.</p> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
Namen van eigenschappen zijn hoofdlettergevoelig en moeten allemaal kleine letters zijn.

**Kleurprofieltabel**

De volgende kleurprofielen zijn geïnstalleerd:

<table>
 <tbody>
  <tr>
   <th><p>Naam</p> </th>
   <th><p>Kleurruimte</p> </th>
   <th><p>Beschrijving</p> </th>
  </tr>
  <tr>
   <td>Adobe RGB</td>
   <td>RGB</td>
   <td>Adobe RGB (1998)</td>
  </tr>
  <tr>
   <td>AppleRGB</td>
   <td>RGB</td>
   <td>Apple RGB</td>
  </tr>
  <tr>
   <td>CIERGB</td>
   <td>RGB</td>
   <td>CIE RGB</td>
  </tr>
  <tr>
   <td>CoatedFogra27</td>
   <td>CMYK</td>
   <td>Coated FOGRA27 (ISO 12647-2:2004)</td>
  </tr>
  <tr>
   <td>CoatedFogra39</td>
   <td>CMYK</td>
   <td>Coated FOGRA39 (ISO 12647-2:2004)</td>
  </tr>
  <tr>
   <td>CoatedGraCol</td>
   <td>CMYK</td>
   <td>Coated GRACoL 2006 (ISO 12647-2:2004)</td>
  </tr>
  <tr>
   <td>ColorMatchRGB</td>
   <td>RGB</td>
   <td>ColorMatch RGB</td>
  </tr>
  <tr>
   <td>EuropeISOCoated</td>
   <td>CMYK</td>
   <td>Europe ISO Coated FOGRA27</td>
  </tr>
  <tr>
   <td>EuroscaleCoated</td>
   <td>CMYK</td>
   <td>Euroscale Coated v2</td>
  </tr>
  <tr>
   <td>EuroscaleUncoated</td>
   <td>CMYK</td>
   <td>Euroscale Uncoated v2</td>
  </tr>
  <tr>
   <td>JapanColorCoated</td>
   <td>CMYK</td>
   <td>Japan Color 2001 Coated</td>
  </tr>
  <tr>
   <td>JapanColorNewspaper</td>
   <td>CMYK</td>
   <td>Japan Color 2002 Newspaper</td>
  </tr>
  <tr>
   <td>JapanColorUncoated</td>
   <td>CMYK</td>
   <td>Japan Color 2001 Uncoated</td>
  </tr>
  <tr>
   <td>JapanColorWebCoated</td>
   <td>CMYK</td>
   <td>Japan Color 2003 Web Coated</td>
  </tr>
  <tr>
   <td>JapanWebCoated</td>
   <td>CMYK</td>
   <td>Japan Web Coated (Ad)</td>
  </tr>
  <tr>
   <td>NewsprintSNAP2007</td>
   <td>CMYK</td>
   <td>US Newsprint (SNAP 2007)</td>
  </tr>
  <tr>
   <td>NTSC</td>
   <td>RGB</td>
   <td>NTSC (1953)</td>
  </tr>
  <tr>
   <td>PAL</td>
   <td>RGB</td>
   <td>PAL/SECAM</td>
  </tr>
  <tr>
   <td>ProPhoto</td>
   <td>RGB</td>
   <td>ProPhoto RGB</td>
  </tr>
  <tr>
   <td>PS4Default</td>
   <td>CMYK</td>
   <td>Photoshop 4 standaard CMYK</td>
  </tr>
  <tr>
   <td>PS5Standaard</td>
   <td>CMYK</td>
   <td>Photoshop 5 standaard CMYK</td>
  </tr>
  <tr>
   <td>SheetfedCoated</td>
   <td>CMYK</td>
   <td>U.S. Sheetfed Coated v2</td>
  </tr>
  <tr>
   <td>SheetfedUncoated</td>
   <td>CMYK</td>
   <td>U.S. Sheetfed Uncoated v2</td>
  </tr>
  <tr>
   <td>SMPTE</td>
   <td>RGB</td>
   <td>SMPTE-C</td>
  </tr>
  <tr>
   <td>sRGB</td>
   <td>RGB</td>
   <td>sRGB IEC61966-2.1</td>
  </tr>
  <tr>
   <td>UncoatedFogra29</td>
   <td>CMYK</td>
   <td>Uncoated FOGRA29 (ISO 12647-2:2004)</td>
  </tr>
  <tr>
   <td>WebCoated</td>
   <td>CMYK</td>
   <td>U.S. Web Coated (SWOP) v2</td>
  </tr>
  <tr>
   <td>WebCoatedFogra28</td>
   <td>CMYK</td>
   <td>Web Coated FOGRA28 (ISO 12647-2:2004)</td>
  </tr>
  <tr>
   <td>WebCoatedGrade3</td>
   <td>CMYK</td>
   <td>Web Coated SWOP 2006 Grade 3 Paper</td>
  </tr>
  <tr>
   <td>WebCoatedGrade5</td>
   <td>CMYK</td>
   <td>Web Coated SWOP 2006 Grade 5 Paper</td>
  </tr>
  <tr>
   <td>WebUncoated</td>
   <td>CMYK</td>
   <td>U.S. Web Uncoated v2</td>
  </tr>
  <tr>
   <td>WideGamutRGB</td>
   <td>RGB</td>
   <td>Brede kleuromvang RGB</td>
  </tr>
 </tbody>
</table>

1. Selecteren **[!UICONTROL Save All]**.

U kunt bijvoorbeeld de opdracht **[!UICONTROL iccprofilergb]** tot `sRGB`, en **[!UICONTROL iccprofilecmyk]** tot **[!UICONTROL WebCoated]**.

Dit doet het volgende:

* Hiermee schakelt u kleurcorrectie in voor RGB- en CMYK-afbeeldingen.
* RGB-afbeeldingen die geen kleurprofiel hebben, worden verondersteld in de *sRGB* kleurruimte.
* CMYK-afbeeldingen zonder kleurprofiel worden geacht zich in *WebCoated* kleurruimte.
* Dynamische uitvoeringen die RGB-uitvoer retourneren, retourneren deze in de *sRGB *kleurruimte.
* Dynamische uitvoeringen die CMYK-uitvoer retourneren, retourneren deze in het dialoogvenster *WebCoated* kleurruimte.

## Elementen leveren {#delivering-assets}

Nadat u alle bovenstaande taken hebt voltooid, worden de geactiveerde Dynamic Media-middelen aangeboden via de Image- of Video-service. In de Experience Manager komt deze mogelijkheid tot uiting in een **[!UICONTROL Copy Image URL]**, **[!UICONTROL Copy Viewer URL]**, **[!UICONTROL Embed Viewer Code]** en in de WCM.

Zie [Dynamic Media-middelen leveren](/help/assets/delivering-dynamic-media-assets.md).

<table>
 <tbody>
  <tr>
   <td><strong>Wanneer u...</strong></td>
   <td><strong>Resultaat</strong></td>
  </tr>
  <tr>
   <td>URL van afbeelding kopiëren</td>
   <td><p>In het dialoogvenster URL kopiëren wordt een URL weergegeven die vergelijkbaar is met de volgende URL (URL is alleen bedoeld voor demonstratiedoeleinden):</p> <p><code>https://IMAGESERVICEPUBLISHNODE/is/image/content/dam/path/to/Image.jpg?$preset$</code></p> <p>Wanneer <code>IMAGESERVICEPUBLISHNODE</code> verwijst naar de URL van de afbeeldingsservice.</p> <p>Zie ook <a href="/help/assets/delivering-dynamic-media-assets.md">Dynamic Media-middelen leveren</a>.</p> </td>
  </tr>
  <tr>
   <td>Een viewer-URL kopiëren</td>
   <td><p>In het dialoogvenster URL kopiëren wordt een URL weergegeven die vergelijkbaar is met de volgende URL (URL is alleen bedoeld voor demonstratiedoeleinden):</p> <p><code>https://PUBLISHNODE/etc/dam/viewers/s7viewers/html5/BasicZoomViewer.html?asset=/content/dam/path/to/Image.jpg&amp;config=/conf/global/settings/dam/dm/presets/viewer/Zoom_dark&amp;serverUrl=https://IMAGESERVICEPUBLISHNODE/is/image/&amp;contentRoot=%2F</code></p> <p>Wanneer <code>PUBLISHNODE</code> verwijst naar het publicatieknooppunt van de gewone Experience Manager en <code>IMAGESERVICEPUBLISHNODE</code> verwijst naar de URL van de afbeeldingsservice.</p> <p>Zie ook <a href="/help/assets/delivering-dynamic-media-assets.md">Dynamic Media-middelen leveren</a>.</p> </td>
  </tr>
  <tr>
   <td>Insluitcode van een viewer kopiëren</td>
   <td><p>In het dialoogvenster Code insluiten kopiëren wordt een codefragment weergegeven dat lijkt op het volgende (codevoorbeeld is alleen bedoeld voor demonstratiedoeleinden):</p> <p><code class="code">&lt;style type="text/css"&gt;
       #s7basiczoom_div.s7basiczoomviewer{
       width:100%;
       height:auto;
       }
       &lt;/style&gt;
       &lt;script
       type="text/javascript" src="https://PUBLISHNODE/etc/dam/viewers/s7viewers/html5/js/BasicZoomViewer.js"&gt;&lt;/script&gt;
       &lt;div id="s7basiczoom_div"&gt;&lt;/div&gt;
       &lt;script type="text/javascript"&gt;
       var s7basiczoomviewer = new s7viewers.BasicZoomViewer({
       "containerId" : "s7basiczoom_div",
       "params" : {
       "serverurl" : "https://IMAGESERVICEPUBLISHNODE/is/image/",
       "contenturl" : "https://PUBLISHNODE/",
       "config" : "/conf/global/settings/dam/dm/presets/viewer/Zoom_dark",
       "asset" : "/content/dam/path/to/Image.jpg" }
       }).init();
       &lt;/script&gt;</code></p> <p>Wanneer <code>PUBLISHNODE</code> verwijst naar het publicatieknooppunt van de gewone Experience Manager en <code>IMAGESERVICEPUBLISHNODE</code> verwijst naar de URL van de afbeeldingsservice.</p> <p>Zie ook <a href="/help/assets/delivering-dynamic-media-assets.md">Dynamic Media-middelen leveren</a>.</p> </td>
  </tr>
 </tbody>
</table>

### WCM Dynamic Media en interactieve mediacomponenten {#wcm-dynamic-media-and-interactive-media-components}

WCM-pagina&#39;s die verwijzen naar Dynamic Media en Interactive Media-componenten verwijzen naar de leveringsservice.
