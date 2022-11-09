---
title: Cache voor aangepaste formulieren configureren
seo-title: Configure adaptive forms cache
description: De cache voor adaptieve formulieren is speciaal ontworpen voor adaptieve formulieren en documenten. Het slaat adaptieve formulieren en adaptieve documenten in het cachegeheugen op om de tijd te verkorten die nodig is om een adaptief formulier of document op de client te genereren.
seo-description: The adaptive forms cache is designed specifically for adaptive forms and documents. It caches adaptive forms and adaptive documents with the objective of reducing the time required to render an adaptive form or document on the client.
uuid: ba8f79fd-d8dc-4863-bc0d-7c642c45505c
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Configuration
discoiquuid: 9fa6f761-58ca-4cd0-8992-b9337dc1a279
docset: aem65
role: Admin
exl-id: 153986f0-b6ff-4278-8bb6-70c320a4e539
source-git-commit: 63f066013c34a5994e2c6a534d88db0c464cc905
workflow-type: tm+mt
source-wordcount: '858'
ht-degree: 0%

---

# Cache voor aangepaste formulieren configureren {#configure-adaptive-forms-cache}

Een cache is een mechanisme om de toegangstijd voor gegevens te verkorten, de latentie te verminderen en de invoer-/uitvoersnelheid (I/O) te verbeteren. In de cache van adaptieve formulieren worden alleen de HTML-inhoud en de JSON-structuur van een adaptief formulier opgeslagen zonder dat vooraf ingevulde gegevens worden opgeslagen. Hierdoor wordt de tijd die nodig is om een adaptief formulier op de client te genereren, verkort. Het is specifiek ontworpen voor adaptieve formulieren.

## Cache voor adaptieve formulieren configureren bij auteur- en publicatieinstanties {#configure-adaptive-forms-caching-at-author-and-publish-instances}

1. Ga naar AEM webconsoleconfiguratiebeheer op `https://[server]:[port]/system/console/configMgr`.
1. Klikken **[!UICONTROL Adaptive Form and Interactive Communication Web Channel Configuration]** om de configuratiewaarden te bewerken.
1. In de [!UICONTROL edit configuration values] het maximumaantal formulieren of documenten in een exemplaar van de AEM [!DNL Forms] server kan in cache plaatsen in de **[!UICONTROL Number of Adaptive Forms]** veld. De standaardwaarde is 100.

   >[!NOTE]
   >
   >Als u de cache wilt uitschakelen, stelt u de waarde in het veld Number Adaptive Forms in op **0**. De cache wordt opnieuw ingesteld en alle formulieren en documenten worden uit de cache verwijderd wanneer u de cachemonfiguratie uitschakelt of wijzigt.

   ![Dialoogvenster Configuratie voor HTML-cache van adaptieve formulieren](assets/cache-configuration-edit.png)

1. Klikken **[!UICONTROL Save]** om de configuratie op te slaan.

Uw omgeving is geconfigureerd voor het gebruik van cacheadaptieve formulieren en gerelateerde elementen.


## (Optioneel) Adaptief formuliercache configureren bij verzender {#configure-the-cache}

U kunt ook adaptieve formulieren in cache plaatsen bij dispatcher voor extra prestatieverhoging.

### Voorwaarden {#pre-requisites}

* De optie [samenvoegen of vooraf invullen van gegevens op de client](prepopulate-adaptive-form-fields.md#prefill-at-client) optie. Hiermee kunt u unieke gegevens samenvoegen voor elk exemplaar van een vooraf ingevuld formulier.

### Overwegingen bij het in cache plaatsen van adaptieve formulieren op een verzender {#considerations}

* Wanneer u de cache voor aangepaste formulieren gebruikt, gebruikt u de AEM [!DNL Dispatcher] in cache plaatsen van clientbibliotheken (CSS en JavaScript) van een adaptief formulier.
* Zorg tijdens het ontwikkelen van aangepaste componenten op de server die wordt gebruikt voor ontwikkeling dat de cache van adaptieve formulieren uitgeschakeld blijft.
* URL&#39;s zonder extensie worden niet in de cache opgeslagen. Bijvoorbeeld URL met patroon`/content/forms/[folder-structure]/[form-name].html` worden in cache geplaatst en worden URL&#39;s met een patroon genegeerd `/content/dam/formsanddocument/[folder-name]/<form-name>/jcr:content`. Gebruik dus URL&#39;s met extensies om te profiteren van caching.
* Overwegingen voor gelokaliseerde adaptieve formulieren:
   * URL-indeling gebruiken `http://host:port/content/forms/af/<afName>.<locale>.html` om een gelokaliseerde versie van een adaptief formulier aan te vragen in plaats van `http://host:port/content/forms/af/afName.html?afAcceptLang=<locale>`
   * [Uitschakelen met landinstelling browser](supporting-new-language-localization.md#how-localization-of-adaptive-form-works) voor URL&#39;s met opmaak `http://host:port/content/forms/af/<adaptivefName>.html`.
   * Wanneer u URL-indeling gebruikt `http://host:port/content/forms/af/<adaptivefName>.html`, en **[!UICONTROL Use Browser Locale]** als configuratiebeheer is uitgeschakeld, wordt de niet-gelokaliseerde versie van het adaptieve formulier weergegeven. De niet-gelokaliseerde taal is de taal die wordt gebruikt bij het ontwikkelen van het adaptieve formulier. De landinstelling die is geconfigureerd voor uw browser (landinstelling browser) wordt niet in aanmerking genomen en er wordt een niet-gelokaliseerde versie van het adaptieve formulier weergegeven.
   * Wanneer u URL-indeling gebruikt `http://host:port/content/forms/af/<adaptivefName>.html`, en **[!UICONTROL Use Browser Locale]** als configuratiemanager ingeschakeld is, wordt een gelokaliseerde versie van het adaptieve formulier weergegeven, indien beschikbaar. De taal van het gelokaliseerde adaptieve formulier is gebaseerd op de landinstelling die is geconfigureerd voor uw browser (landinstelling browser). Het kan leiden tot [alleen eerste exemplaar van een adaptief formulier in cache plaatsen]. Als u wilt voorkomen dat het probleem op uw exemplaar optreedt, raadpleegt u [problemen oplossen](#only-first-insatnce-of-adptive-forms-is-cached).

### Het in cache plaatsen van de verzender inschakelen

Voer de onderstaande stappen uit om adaptieve formulieren in de cache in te schakelen en te configureren op de dispatcher:

1. Open de volgende URL voor elke publicatie-instantie van uw omgeving en [flush-agent inschakelen voor het publiceren van exemplaren van uw omgeving](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/page-invalidate.html#invalidating-dispatcher-cache-from-a-publishing-instance):
   `http://[server]:[port]]/etc/replication/agents.publish/flush.html`

1. [Voeg het volgende toe aan uw dispatcher.any-bestand](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#automatically-invalidating-cached-files):

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

   * Wanneer een nieuwere versie van de bron waarnaar in een adaptief formulier wordt verwezen, wordt gepubliceerd, worden de beïnvloede adaptieve formulieren automatisch ongeldig gemaakt. Er zijn enkele uitzonderingen op de automatische ongeldigmaking van bronnen waarnaar wordt verwezen. Zie voor meer informatie over uitzonderingen [problemen oplossen](#troubleshooting) sectie.
1. [Voeg het onderstaande bestand met regels dispatcher.any of aangepaste regels toe](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#specifying-the-documents-to-cache). De URL&#39;s die caching niet ondersteunen, worden uitgesloten. Bijvoorbeeld interactieve communicatie.

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

1. [De volgende parameters toevoegen aan de lijst met URL-parameters negeren](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#ignoring-url-parameters):

   ```JSON
      /ignoreUrlParams {
      /0001 { /glob "*" /type "deny" }
      # added for AEM forms specific use cases.
      /0003 { /glob "dataRef" /type "allow" }
      }
   ```

Uw AEM-omgeving is geconfigureerd om adaptieve formulieren in de cache op te slaan. Alle typen adaptieve formulieren worden in het cachegeheugen opgeslagen. Als u de toegangsrechten van gebruikers voor een pagina moet controleren voordat u de pagina in de cache aflevert, raadpleegt u [caching, beveiligde inhoud](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/permissions-cache.html).

## Problemen oplossen {#troubleshooting}

### Sommige adaptieve formulieren met afbeeldingen of video&#39;s worden niet automatisch ongeldig gemaakt in de verzendingscache {#videos-or-images-not-auto-invalidated}

#### Probleem {#issue1}

Wanneer u via de middelenbrowser afbeeldingen of video&#39;s selecteert en toevoegt aan een adaptief formulier en deze afbeeldingen en video&#39;s worden bewerkt in de Middelen-editor, worden adaptieve formulieren met dergelijke afbeeldingen niet automatisch ongeldig gemaakt in de verzendercache.

#### Oplossing {#Solution1}

Nadat u de afbeeldingen en video hebt gepubliceerd, maakt u de publicatie van de adaptieve formulieren die naar deze elementen verwijzen, expliciet ongedaan en publiceert u deze.

### Alleen de eerste instantie van een adaptief formulier wordt in de cache opgeslagen {#only-first-instance-of-adaptive-forms-is-cached}

#### Probleem {#issue3}

Wanneer de URL van het aangepaste formulier geen lokalisatiegegevens bevat, en **[!UICONTROL Use Browser Locale]** in Configuration Manager is ingeschakeld, wordt een gelokaliseerde versie van het adaptieve formulier aangeleverd en wordt alleen het eerste exemplaar van het adaptieve formulier in de cache geplaatst en aan elke volgende gebruiker bezorgd.

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
