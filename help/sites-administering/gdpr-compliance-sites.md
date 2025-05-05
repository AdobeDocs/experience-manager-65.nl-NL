---
title: AEM Sites - GDPR-gereedheid
description: Meer informatie over de procedures voor het verwerken van GDPR-aanvragen in AEM Sites en over het gebruik ervan.
contentOwner: AEM Docs
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
exl-id: 8c1ea483-7319-4e5c-be4c-d43a2b67d316
solution: Experience Manager, Experience Manager Sites
feature: Compliance
role: Admin, Architect, Developer, Leader, User, Data Architect, Data Engineer
source-git-commit: 207c6bcc25eca05d128115f7235e83a6965009c5
workflow-type: tm+mt
source-wordcount: '837'
ht-degree: 0%

---

# AEM Sites - GDPR-gereedheid{#aem-sites-gdpr-readiness}

>[!IMPORTANT]
>
>GDPR wordt in de onderstaande secties als voorbeeld gebruikt, maar de betreffende details zijn van toepassing op alle regels inzake gegevensbescherming en privacy, zoals GDPR, CCPA, enzovoort.

De algemene gegevensbeschermingsverordening van de Europese Unie betreffende de bescherming van persoonsgegevens treedt in werking in mei 2018.

AEM Sites is klaar om klanten te helpen bij het nakomen van hun GDPR-verplichtingen. Deze pagina begeleidt klanten door de procedures om GDPR-verzoeken in AEM Sites te behandelen. Hierin wordt de locatie van opgeslagen privégegevens beschreven en hoe deze handmatig of met code kunnen worden verwijderd.

Voor verdere informatie zie de [ pagina GDPR bij het Centrum van de Privacy van de Adobe ](https://www.adobe.com/privacy/general-data-protection-regulation.html).

>[!NOTE]
>
>Zie [ AEM GDPR Gereedheid ](/help/managing/data-protection-and-privacy.md) voor verdere details.

## Auteursserver {#author-server}

De rekeningen van de gebruiker en inhoud UGC op de auteurserver zijn behandeld in de [ documentatie van Platform GDPR ](/help/managing/data-protection-and-privacy.md).

## Publish Server {#publish-server}

De rekeningen van de gebruiker worden gebruikt om bezoekers op de plaats voor authentiek te verklaren, en de inhoud UGC op publiceer server wordt behandeld in de [ documentatie van Platform GDPR ](/help/managing/data-protection-and-privacy.md).

Standaard slaan AEM Sites-componenten geen formuliergegevens op die bezoekers op de publicatieserver hebben ingevoerd. Het wordt aanbevolen de gegevens naar een systeem van derden of naar Adobe Campaign te sturen voor verdere verwerking.

## Opt-in/Opt-out {#opt-in-opt-out}

AEM heeft de dienst van de a [ koekjesopt-out ](/help/sites-developing/cookie-optout.md) die voor het beheren van opt-in/opt-out voor gebruikers kan worden gebruikt.

## Verbeterde inzichten door Analytics {#enhanced-insights-by-analytics}

AEM Sites omvat een optionele integratie met Enhanced Insights van Analytics, die gebruikmaakt van functionaliteit binnen de Adobe Analytics On-demand Service.

Voor verdere informatie bij het beheren van GDPR- gegevensonderwerpverzoeken met betrekking tot Adobe Analytics zie [ Adobe Analytics en GDPR ](https://experienceleague.adobe.com/docs/analytics/admin/data-governance/an-gdpr-overview.html?lang=nl-NL).

## Enhanced Personalization by Target {#enhanced-personalization-by-target}

AEM Sites omvat een optionele integratie met Enhanced Personalization by Target, die gebruikmaakt van functionaliteit binnen de Adobe Target On-demand Service.

Voor meer informatie over het beheren van GDPR- gegevensonderwerpverzoeken met betrekking tot Adobe Target zie [ Adobe Target - de Privacy en Algemene Verordening van de Bescherming van Gegevens ](https://developer.adobe.com/target/before-implement/privacy/cmp-privacy-and-general-data-protection-regulation/?lang=en).

## ContextHub {#contexthub}

AEM verstrekt een facultatieve gegevenslaag met [ ContextHub ](/help/sites-developing/contexthub.md). Dit houdt bezoekersspecifieke gegevens in browser, die voor op regel-gebaseerde verpersoonlijking moeten worden gebruikt.

Door gebrek, wordt dit bezoeker-gegeven niet opgeslagen in AEM; AEM verzendt regels naar de gegevenslaag om verpersoonlijkingsbesluiten in browser te nemen.

>[!NOTE]
>
>Voorafgaand aan Adobe AEM (CQ) 5.6, verzond de ClientContext (een vroegere versie van ContextHub) de gegevens aan de server, maar bewaarde hen niet.
>
>Adobe AEM 6.4 en eerdere versies zijn nu EOL en worden niet door deze documentatie gedekt. Zie [ Oudere versies van Adobe Experience Manager, CQ, en de documentatie van CRX ](https://experienceleague.adobe.com/nl/docs/experience-manager-release-information/aem-release-updates/previous-updates/aem-previous-versions).

### Opt-in/Opt-out implementeren {#implementing-opt-in-opt-out}

De eigenaar van de site moet een opt-out-component implementeren in overeenstemming met de volgende richtlijnen.

Deze richtlijnen voeren opt-in als gebrek uit. Daarom moet een websitebezoeker het duidelijk met me eens zijn, voordat persoonlijke gegevens worden opgeslagen in de (client-side) persistentie van de browser.

* De opt-out component zou moeten worden omvat telkens als de component ContextHub inbegrepen is.
* De bepalingen en voorwaarden die betrekking hebben op de GDPR voor de website moeten worden weergegeven aan de websitebezoeker, zodat deze:

   * accepteren
   * afwijzen
   * vorige keuze wijzigen

* Als een plaatsbezoeker de voorwaarden van de plaats goedkeurt, zou het opt-outkoekje ContextHub moeten worden verwijderd:

  ```java
  ContextHub.Utils.Cookie.removeItem('cq-opt-out');
  ```

* Als een plaatsbezoeker niet de voorwaarden van de plaats goedkeurt, zou het opt-out van ContextHub koekje moeten worden geplaatst:

  ```java
  ContextHub.Utils.Cookie.setItem('cq-opt-out', 1);
  ```

* Om te controleren of ContextHub op opt-out wijze loopt, zou de volgende vraag in de browser console moeten worden gemaakt:

  ```java
  var isOptedOut = ContextHub.isOptedOut(true) === true;
  // if isOptedOut is true, ContextHub is running in opt-out mode
  ```

### Previewing persistentie van ContextHub {#previewing-persistence-of-contexthub}

Aan voorproefpersistentie gebruikt ContextHub, kan een gebruiker:

* Gebruik de browserconsole, bijvoorbeeld:

   * Chrome:

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
         * Console > Opslag > Sessieopslag > (website) > ContextHubPersistence
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

     De opslag ContextHub bepaalt welke persistentielaag wordt gebruikt, zo om de huidige staat van persistentie te bekijken alle lagen zouden moeten worden gecontroleerd.

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

     De opslag ContextHub bepaalt welke persistentielaag wordt gebruikt, zo om de huidige staat van persistentie te bekijken alle lagen zouden moeten worden gecontroleerd.

Als u bijvoorbeeld gegevens wilt weergeven die zijn opgeslagen in localStorage:

```java
var storage = new ContextHub.Utils.Persistence({ mode: ContextHub.Utils.Persistence.Modes.LOCAL });
console.log(storage.getTree());
```

### De persistentie van ContextHub wissen {#clearing-persistence-of-contexthub}

Om de persistentie te ontruimen ContextHub:

* Om persistentie van momenteel geladen opslag te ontruimen:

  ```java
  // to be able to fully access persistence layer, Opt-Out must be turned off
  ContextHub.Utils.Cookie.removeItem('cq-opt-out');
  
  // following call asks all currently loaded stores to clear their data
  ContextHub.cleanAllStores();
  
  // following call asks all currently loaded stores to set back default values (provided in their configs)
  ContextHub.resetAllStores();
  ```

* Om een specifieke persistentielaag te ontruimen, bijvoorbeeld, sessionStorage:

  ```java
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
