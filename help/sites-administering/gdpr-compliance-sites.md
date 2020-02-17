---
title: AEM-sites - GDPR-gereedheid
seo-title: AEM-sites - GDPR-gereedheid
description: Meer informatie over de gereedheid van GDPR voor AEM-sites.
seo-description: Meer informatie over de gereedheid van GDPR voor AEM-sites.
uuid: 00d1fdce-ef9a-4902-a7a5-7225728e8ffc
contentOwner: aheimoz
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: 772f6188-5e0b-4e66-b94a-65a0cc267ed3
translation-type: tm+mt
source-git-commit: 85a3dac5db940b81da9e74902a6aa475ec8f1780

---


# AEM-sites - GDPR-gereedheid{#aem-sites-gdpr-readiness}

>[!IMPORTANT]
>
>GDPR wordt in de onderstaande secties als voorbeeld gebruikt, maar de betreffende details zijn van toepassing op alle regels inzake gegevensbescherming en privacy; zoals GDPR, CCPA enz.

De algemene gegevensbeschermingsverordening van de Europese Unie betreffende de bescherming van persoonsgegevens treedt in werking in mei 2018.

AEM-sites zijn klaar om klanten te helpen bij het nakomen van hun verplichtingen op het gebied van GDPR. Deze pagina begeleidt klanten door de procedures om GDPR- verzoeken in de Plaatsen van AEM te behandelen. Hierin wordt de locatie van opgeslagen privégegevens beschreven en hoe deze handmatig of met code kunnen worden verwijderd.

Zie de pagina [GDPR in het Adobe Privacy Center](https://www.adobe.com/privacy/general-data-protection-regulation.html)voor meer informatie.

>[!NOTE]
>
>Zie [AEM GDPR Gereedheid](/help/managing/data-protection-and-privacy.md) voor meer informatie.

## Auteursserver {#author-server}

Gebruikersaccounts en UGC-inhoud op de auteurserver worden behandeld in de GDPR-documentatie [van het](/help/managing/data-protection-and-privacy.md)platform.

## Server publiceren {#publish-server}

Gebruikersaccounts die worden gebruikt om bezoekers op de site te verifiëren, en UGC-inhoud op de publicatieserver worden behandeld in de GDPR-documentatie [van het](/help/managing/data-protection-and-privacy.md)platform.

Standaard slaan AEM-sitecomponenten geen formuliergegevens op die bezoekers op de publicatieserver hebben ingevoerd. U wordt aangeraden de gegevens naar een systeem van derden of naar Adobe Campagne te sturen voor verdere verwerking.

## Opt-in/Opt-out {#opt-in-opt-out}

AEM heeft een [cookie-uitschakelservice](/help/sites-developing/cookie-optout.md) die kan worden gebruikt voor het beheer van de opt-in/opt-out voor gebruikers.

## Verbeterde inzichten door Analytics {#enhanced-insights-by-analytics}

AEM Sites omvat een optionele integratie met Enhanced Insights van Analytics, die gebruikmaakt van functionaliteit binnen de Adobe Analytics On-demand Service.

Zie [Adobe Analytics en GDPR](https://marketing.adobe.com/resources/help/en_US/analytics/gdpr/)voor meer informatie over het beheer van aanvragen voor GDPR-gegevens met betrekking tot Adobe Analytics.

## Verbeterde personalisatie door doel {#enhanced-personalization-by-target}

AEM Sites omvat een optionele integratie met Enhanced Personalization by Target, die gebruikmaakt van functionaliteit binnen de Adobe Target On-demand Service.

Zie [Adobe Target - Privacy and General Data Protection Regulation](https://marketing.adobe.com/resources/help/en_US/target/target/privacy-and-general-data-protection-regulation.html)voor meer informatie over het beheer van aanvragen voor GDPR-gegevens met betrekking tot Adobe Target.

## ContextHub {#contexthub}

AEM verstrekt een facultatieve gegevenslaag met [ContextHub](/help/sites-developing/contexthub.md). Dit houdt bezoekersspecifieke gegevens in browser, die voor op regel-gebaseerde verpersoonlijking moeten worden gebruikt.

Deze bezoekergegevens worden standaard niet opgeslagen in AEM. AEM verzendt regels naar de gegevenslaag om verpersoonlijkingsbesluiten in browser te nemen.

>[!NOTE]
>
>Voorafgaand aan Adobe CQ 5.6, verzond ClientContext (een vroegere versie van ContextHub) de gegevens naar de server, maar bewaarde hen niet.
>
>Adobe CQ 5.5 en eerdere versies zijn nu EOL en worden niet behandeld in deze documentatie.

### Opt-in/Opt-out implementeren {#implementing-opt-in-opt-out}

De eigenaar van de site moet een opt-out-component implementeren in overeenstemming met de volgende richtlijnen.

Deze richtlijnen voeren opt-in als gebrek uit. Daarom moet een websitebezoeker het duidelijk met me eens zijn, voordat persoonlijke gegevens worden opgeslagen in de (client-side) persistentie van de browser.

* De opt-out component zou moeten worden omvat telkens als de component ContextHub inbegrepen is.
* De bepalingen en voorwaarden die betrekking hebben op de GDPR voor de website moeten worden weergegeven aan de websitebezoeker, zodat deze:

   * accepteren
   * afwijzen
   * vorige keuze wijzigen

* Als een plaatsbezoeker de voorwaarden van de plaats goedkeurt, zou het opt-outkoekje ContextHub moeten worden verwijderd:

   ```
   ContextHub.Utils.Cookie.removeItem('cq-opt-out');
   ```

* Als een plaatsbezoeker niet de voorwaarden van de plaats goedkeurt, zou het opt-out van ContextHub koekje moeten worden geplaatst:

   ```
   ContextHub.Utils.Cookie.setItem('cq-opt-out', 1);
   ```

* Om te controleren of ContextHub op opt-out wijze loopt, zou de volgende vraag in de browser console moeten worden gemaakt:

   ```
   var isOptedOut = ContextHub.isOptedOut(true) === true;
   // if isOptedOut is true, ContextHub is running in opt-out mode
   ```

### Previewing persistentie van ContextHub {#previewing-persistence-of-contexthub}

Aan voorproefpersistentie gebruikt ContextHub, kan een gebruiker:

* Gebruik de browserconsole; bijvoorbeeld:

   * Chroom:

      * Open Developer Tools > Application > Storage:

         * Local Storage > (website) > ContextHubPersistence
         * Session Storage > (website) > ContextHubPersistence
         * Cookies > (website) > SessionPersistence
   * Firefox:

      * Open Developer Tools > Storage:

         * Local Storage > (website) > ContextHubPersistence
         * Session Storage > (website) > ContextHubPersistence
         * Cookies > (website) > SessionPersistence
   * Safari:

      * Open Voorkeuren > Geavanceerd > Ontwikkelmenu tonen in menubalk
      * Ontwikkelen openen > JavaScript-console tonen

         * Console > Opslag > Lokale Opslag > (website) > ContextHubPersistence
         * Console > Storage > Session Storage > (website) > ContextHubPersistence
         * Console > Opslag > Cookies > (website) > ContextHubPersistence
   * Internet Explorer:

      * Developer Tools openen > Console

         * localStorage.getItem(&#39;ContextHubPersistence&#39;)
         * sessionStorage.getItem(&#39;ContextHubPersistence&#39;)
         * document.cookie




* Gebruik ContextHub API, in de browser console:

   * ContextHub biedt de volgende gegevenspersistentielagen:

      * ContextHub.Utils.Persistence.Modes.LOCAL (gebrek)
      * ContextHub.Utils.Persistence.Modes.SESSION
      * ContextHub.Utils.Persistence.Modes.COOKIE
      * ContextHub.Utils.Persistence.Modes.WINDOW
      De opslag ContextHub bepaalt welke persistentielaag zal worden gebruikt, zo om de huidige staat van persistentie te bekijken alle lagen zouden moeten worden gecontroleerd.


Als u bijvoorbeeld gegevens wilt weergeven die zijn opgeslagen in localStorage:

Aan voorproefpersistentie gebruikt ContextHub, kan een gebruiker:

* Gebruik de browserconsole:

   * Chrome - open Developer Tools > Application > Storage:

      * Local Storage > (website) > ContextHubPersistence
      * Session Storage > (website) > ContextHubPersistence
      * Cookies > (website) > SessionPersistence
   * Firefox - open Developer Tools > Storage:

      * Local Storage > (website) > ContextHubPersistence
      * Session Storage > (website) > ContextHubPersistence
      * Cookies > (website) > SessionPersistence


* Gebruik ContextHub API, in de browser console:

   * ContextHub biedt de volgende gegevenspersistentielagen:

      * ContextHub.Utils.Persistence.Modes.LOCAL (gebrek)
      * ContextHub.Utils.Persistence.Modes.SESSION
      * ContextHub.Utils.Persistence.Modes.COOKIE
      * ContextHub.Utils.Persistence.Modes.WINDOW
      De opslag ContextHub bepaalt welke persistentielaag zal worden gebruikt, zo om de huidige staat van persistentie te bekijken alle lagen zouden moeten worden gecontroleerd.


Als u bijvoorbeeld gegevens wilt weergeven die zijn opgeslagen in localStorage:

```
var storage = new ContextHub.Utils.Persistence({ mode: ContextHub.Utils.Persistence.Modes.LOCAL });
console.log(storage.getTree());
```

### De persistentie van ContextHub wissen {#clearing-persistence-of-contexthub}

Om de persistentie te ontruimen ContextHub:

* Om persistentie van momenteel geladen opslag te ontruimen:

   ```
   // in order to be able to fully access persistence layer, Opt-Out must be turned off
   ContextHub.Utils.Cookie.removeItem('cq-opt-out');
   
   // following call asks all currently loaded stores to clear their data
   ContextHub.cleanAllStores();
   
   // following call asks all currently loaded stores to set back default values (provided in their configs)
   ContextHub.resetAllStores();
   ```

* een specifieke persistentielaag te wissen; bijvoorbeeld sessionStorage:

   ```
   var storage = new ContextHub.Utils.Persistence({ mode: ContextHub.Utils.Persistence.Modes.SESSION });
   storage.setItem('/store', null);
   storage.setItem('/_', null);
   
   // to confirm that nothing is stored:
   console.log(storage.getTree());
   ```

* Om alle persistentielagen te ontruimen ContextHub, moet de aangewezen code voor alle lagen worden geroepen:

   * ContextHub.Utils.Persistence.Modes.LOCAL (gebrek)
   * ContextHub.Utils.Persistence.Modes.SESSION
   * ContextHub.Utils.Persistence.Modes.COOKIE
   * ContextHub.Utils.Persistence.Modes.WINDOW

