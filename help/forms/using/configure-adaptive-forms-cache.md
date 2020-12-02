---
title: Cache voor aangepaste formulieren configureren
seo-title: Cache voor aangepaste formulieren configureren
description: 'De cache voor adaptieve formulieren is speciaal ontworpen voor adaptieve formulieren en documenten. Het slaat adaptieve formulieren en adaptieve documenten in het cachegeheugen op om de tijd te verkorten die nodig is om een adaptief formulier of document op de client te genereren. '
seo-description: 'De cache voor adaptieve formulieren is speciaal ontworpen voor adaptieve formulieren en documenten. Het slaat adaptieve formulieren en adaptieve documenten in het cachegeheugen op om de tijd te verkorten die nodig is om een adaptief formulier of document op de client te genereren. '
uuid: ba8f79fd-d8dc-4863-bc0d-7c642c45505c
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Configuration
discoiquuid: 9fa6f761-58ca-4cd0-8992-b9337dc1a279
docset: aem65
translation-type: tm+mt
source-git-commit: ade3747ba608164a792a62097b82c55626245891
workflow-type: tm+mt
source-wordcount: '997'
ht-degree: 0%

---


# Cache voor adaptieve formulieren {#configure-adaptive-forms-cache} configureren

Een cache is een mechanisme om de toegangstijd voor gegevens te verkorten, de latentie te verminderen en de invoer-/uitvoersnelheid (I/O) te verbeteren. In de cache van adaptieve formulieren worden alleen HTML-inhoud en JSON-structuur van een adaptief formulier opgeslagen zonder dat vooraf ingevulde gegevens worden opgeslagen. Hierdoor wordt de tijd die nodig is om een adaptief formulier op de client te genereren, verkort. Het is specifiek ontworpen voor adaptieve formulieren.

## Cache voor adaptieve formulieren configureren bij auteur en exemplaren publiceren {#configure-adaptive-forms-caching-at-author-and-publish-instances}

1. Ga naar AEM webconsoleconfiguratiebeheer op `https://[server]:[port]/system/console/configMgr`.
1. Klik **[!UICONTROL Adaptive Form and Interactive Communication Web Channel Configuration]** om zijn configuratiewaarden uit te geven.
1. Geef in het dialoogvenster [!UICONTROL edit configuration values] het maximumaantal formulieren of documenten op dat een instantie van de AEM [!DNL Forms]-server in het veld **[!UICONTROL Number of Adaptive Forms]** in cache kan plaatsen. De standaardwaarde is 100.

   >[!NOTE]
   >
   >Als u de cache wilt uitschakelen, stelt u de waarde in het veld Aantal adaptieve Forms in op **0**. De cache wordt opnieuw ingesteld en alle formulieren en documenten worden uit de cache verwijderd wanneer u de cachemonfiguratie uitschakelt of wijzigt.

   ![Configuratiedialoogvenster voor HTML-cache voor adaptieve formulieren](assets/cache-configuration-edit.png)

1. Klik **[!UICONTROL Save]** om de configuratie te bewaren.

Uw omgeving is geconfigureerd voor het gebruik van cacheadaptieve formulieren en gerelateerde elementen.


## (Optioneel) Aangepast formuliercache configureren op verzender {#configure-the-cache}

U kunt ook adaptieve formulieren in cache plaatsen bij dispatcher voor extra prestatieverhoging.

### Voorwaarden {#pre-requisites}

* Schakel de optie [Gegevens samenvoegen of vooraf invullen op client](prepopulate-adaptive-form-fields.md#prefill-at-client) in. Hiermee kunt u unieke gegevens samenvoegen voor elk exemplaar van een vooraf ingevuld formulier.
* [De spoelagent inschakelen voor elke publicatie-instantie](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/page-invalidate.html#invalidating-dispatcher-cache-from-a-publishing-instance). Hierdoor worden adaptieve formulieren sneller in cache geplaatst. De standaard-URL van spoelmiddelen is `http://[server]:[port]]/etc/replication/agents.publish/flush.html`.

### Overwegingen bij het in cache plaatsen van adaptieve formulieren op een verzender {#considerations}

* Wanneer u de cache voor adaptieve formulieren gebruikt, gebruikt u de AEM [!DNL Dispatcher] om clientbibliotheken (CSS en JavaScript) van een adaptief formulier in cache te plaatsen.
* Zorg tijdens het ontwikkelen van aangepaste componenten op de server die wordt gebruikt voor ontwikkeling dat de cache van adaptieve formulieren uitgeschakeld blijft.
* URL&#39;s zonder extensie worden niet in de cache opgeslagen. URL met patroon`/content/forms/[folder-structure]/[form-name].html` worden bijvoorbeeld in de cache opgeslagen en URL&#39;s met patroon `/content/dam/formsanddocument/[folder-name]/<form-name>/jcr:content` worden in de cache genegeerd. Gebruik dus URL&#39;s met extensies om te profiteren van caching.
* Overwegingen voor gelokaliseerde adaptieve formulieren:
   * Gebruik de URL-indeling `http://host:port/content/forms/af/<afName>.<locale>.html` om een gelokaliseerde versie van een adaptief formulier aan te vragen in plaats van `http://host:port/content/forms/af/afName.html?afAcceptLang=<locale>`
   * [Schakel deze optie uit met ](supporting-new-language-localization.md#how-localization-of-adaptive-form-works) browserlandinstelling voor URL&#39;s met opmaak  `http://host:port/content/forms/af/<adaptivefName>.html`.
   * Wanneer u URL-indeling `http://host:port/content/forms/af/<adaptivefName>.html` gebruikt en **[!UICONTROL Use Browser Locale]** in configuratiebeheer is uitgeschakeld, wordt de niet-gelokaliseerde versie van het adaptieve formulier weergegeven. De niet-gelokaliseerde taal is de taal die wordt gebruikt bij het ontwikkelen van het adaptieve formulier. De landinstelling die is geconfigureerd voor uw browser (landinstelling browser) wordt niet in aanmerking genomen en er wordt een niet-gelokaliseerde versie van het adaptieve formulier weergegeven.
   * Wanneer u URL-indeling `http://host:port/content/forms/af/<adaptivefName>.html` gebruikt en **[!UICONTROL Use Browser Locale]** in configuratiebeheer is ingeschakeld, wordt een gelokaliseerde versie van het aangepaste formulier weergegeven, indien beschikbaar. De taal van het gelokaliseerde adaptieve formulier is gebaseerd op de landinstelling die is geconfigureerd voor uw browser (landinstelling browser). Dit kan leiden tot [caching slechts eerste instantie van een adaptief formulier]. Zie [Problemen oplossen](#only-first-insatnce-of-adptive-forms-is-cached) om te voorkomen dat het probleem op uw exemplaar optreedt.

### Het in cache plaatsen van de verzender inschakelen

Voer de onderstaande stappen uit om adaptieve formulieren in de cache in te schakelen en te configureren op de dispatcher:

1. Open volgende URL voor elk publiceer geval van u milieu en vorm de replicatieagent:
   `http://[server]:[port]]/etc/replication/agents.publish/flush.html`

1. [Voeg het volgende toe aan het bestand](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#automatically-invalidating-cached-files) dispatcher.any:

   ```JSON
      /invalidate
      {
      /0000
      {
      /glob "*"
      /type "deny"
      }
      /0001
      {
      # Consider all HTML files stale after an activation.
      /glob "*.html"
      /type "allow"
      }
      /0002
      {
      # Exclude htmls present in AF directories
      /glob "/content/forms/**/*.html"
      /type "deny"
      }
   ```

   Wanneer u het bovenstaande toevoegt:

   * Een adaptief formulier blijft in cache totdat een bijgewerkte versie van het formulier niet wordt gepubliceerd.

   * Wanneer een nieuwere versie van de bron waarnaar in een adaptief formulier wordt verwezen, wordt gepubliceerd, worden de beïnvloede adaptieve formulieren automatisch ongeldig gemaakt. Er zijn enkele uitzonderingen op de automatische ongeldigmaking van bronnen waarnaar wordt verwezen. Zie [sectie Problemen oplossen](#troubleshooting) voor een oplossing voor uitzonderingen.
1. [Voeg het onderstaande bestand](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#specifying-the-documents-to-cache) met regels dispatcher.any of aangepaste regels toe. De URL&#39;s die caching niet ondersteunen, worden uitgesloten. Bijvoorbeeld interactieve communicatie.

   ```JSON
      /0000 {
            /glob "*"
            /type "allow"
      }
      ## Don't cache csrf login tokens
      /0001 {
            /glob "/libs/granite/csrf/token.json"
            /type "deny"
      }
      ## Don't cache IC - print channel
      /0002 {
            /glob "/content/forms/**/channels/print.html"
            /type "deny"
      }
      ## Don't cache IC - web channel
      /0003 {
            /glob "/content/forms/**/channels/web.html"
            /type "deny"
      }
   ```

1. [Voeg de volgende parameters toe aan de lijst](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#ignoring-url-parameters) met URL-parameters negeren:

   ```JSON
      /ignoreUrlParams {
      /0001 { /glob "*" /type "deny" }
      # added for AEM forms specific use cases.
      /0003 { /glob "dataRef" /type "allow" }
      }
   ```

Uw AEM-omgeving is geconfigureerd om adaptieve formulieren in de cache op te slaan. Alle typen adaptieve formulieren worden in het cachegeheugen opgeslagen. Zie [Beveiligde inhoud in cache plaatsen](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/permissions-cache.html) als u toegangsmachtigingen voor gebruikers voor een pagina moet controleren voordat de pagina in de cache wordt geleverd.

## Problemen oplossen {#troubleshooting}

### Sommige adaptieve formulieren met afbeeldingen of video&#39;s worden niet automatisch ongeldig gemaakt in de verzendingscache {#videos-or-images-not-auto-invalidated}

#### Probleem {#issue1}

Wanneer u via de middelenbrowser afbeeldingen of video&#39;s selecteert en toevoegt aan een adaptief formulier en deze afbeeldingen en video&#39;s worden bewerkt in de middeleneditor, worden adaptieve formulieren met dergelijke afbeeldingen niet automatisch ongeldig gemaakt in de verzendercache.

#### Oplossing {#Solution1}

Nadat u de afbeeldingen en video hebt gepubliceerd, maakt u de publicatie van de adaptieve formulieren die naar deze elementen verwijzen, expliciet ongedaan en publiceert u deze.

### Sommige adaptieve formulieren met inhoudsfragment of ervaringsfragmenten worden niet automatisch ongeldig gemaakt in de verzendingscache {#content-or-experience-fragment-not-auto-invalidated}

#### Probleem {#issue2}

Wanneer u een inhoudsfragment of ervaringsfragment toevoegt aan een adaptief formulier en deze elementen onafhankelijk worden bewerkt en gepubliceerd, worden adaptieve formulieren met deze elementen niet automatisch ongeldig gemaakt door de verzendercache.

#### Oplossing {#Solution2}

Nadat u het bijgewerkte inhoudsfragment hebt gepubliceerd of een fragment hebt ervaren, publiceert u de adaptieve formulieren die deze elementen gebruiken expliciet ongedaan en publiceert u deze.

### Alleen de eerste instantie van een adaptief formulier wordt in de cache opgeslagen{#only-first-insatnce-of-adptive-forms-is-cached}

#### Probleem {#issue3}

Wanneer het aangepaste formulier-URL geen lokalisatiegegevens bevat en **[!UICONTROL Use Browser Locale]** in Configuration Manager is ingeschakeld, wordt een gelokaliseerde versie van het adaptieve formulier weergegeven en wordt alleen het eerste exemplaar van het adaptieve formulier in de cache geplaatst en geleverd aan elke volgende gebruiker.

#### Oplossing {#Solution3}

Voer de volgende stappen uit om het probleem op te lossen:

1. Open conf.d/httpd-dispatcher.conf of een ander configuratiebestand dat is geconfigureerd om te laden tijdens runtime.

1. Voeg de volgende code toe aan het bestand en sla deze op. Dit is een voorbeeldcode die u kunt aanpassen aan uw omgeving.

```XML
   <VirtualHost *:80>
        # Set log level high during development / debugging and then turn it down to whatever is appropriate
    LogLevel rewrite:trace6
        # Start Rewrite Engine
    RewriteEngine On
        # Handle actual URL convention (just pass through)
        RewriteRule "^/content/forms/af/(.*)[.](.*).html$" "/content/forms/af/$1.$2.html" [PT]
 
        # Handle selector based redirection basded on browser language
        # The Rewrite Cond(ition) is looking for the Accept-Lanague header and if found takes the first two character which most likely will be the desired language selector.
        RewriteCond %{HTTP:Accept-Language} ^(..).*$ [NC]
        RewriteRule "^/content/forms/af/(.*).html$" "/content/forms/af/$1.%1.html" [R]
   </VirtualHost>
```
