---
title: Verbinding maken met Adobe Analytics en frameworks maken
description: Leer hoe u AEM verbindt met SiteCatalyst en frameworks maakt.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
docset: aem65
exl-id: 8262bbf9-a982-479b-a2b5-f8782dd4182d
solution: Experience Manager, Experience Manager Sites
feature: Integration
role: Admin
source-git-commit: eae057caed533ef16bb541b4ad41b8edd7aaa1c7
workflow-type: tm+mt
source-wordcount: '1484'
ht-degree: 0%

---

# Verbinding maken met Adobe Analytics en frameworks maken {#connecting-to-adobe-analytics-and-creating-frameworks}

Als u webgegevens wilt bijhouden van uw AEM in Adobe Analytics, maakt u een Adobe Analytics Cloud Services-configuratie en een Adobe Analytics-framework:

* **Configuratie van Adobe Analytics:** de informatie over uw rekening van Adobe Analytics. Met de Adobe Analytics-configuratie kunnen AEM verbinding maken met Adobe Analytics. Maak een Adobe Analytics-configuratie voor elk account dat u gebruikt.
* **Kader van Adobe Analytics:** een reeks afbeeldingen tussen de eigenschappen van de het rapportreeks van Adobe Analytics en CQ variabelen. Gebruik een framework om te configureren hoe uw websitegegevens uw Adobe Analytics-rapporten vullen. Frameworks zijn gekoppeld aan een Adobe Analytics-configuratie. U kunt veelvoudige kaders voor elke configuratie tot stand brengen.

Wanneer u een webpagina aan een framework koppelt, wordt de webpagina en de onderliggende pagina van die pagina bijgehouden. Paginaweergaven kunnen vervolgens worden opgehaald uit Adobe Analytics en worden weergegeven in de Sites-console.

## Vereisten {#prerequisites}

### Adobe Analytics-account {#adobe-analytics-account}

Als u AEM gegevens in Adobe Analytics wilt bijhouden, moet u een geldige Adobe Experience Cloud Adobe Analytics-account hebben.

De Adobe Analytics-account moet:

* Heb **voorrechten van de Beheerder**
* Wordt toegewezen aan de **gebruikersgroep van de Toegang van de Dienst van 0&rbrace; Web.**

>[!CAUTION]
>
>Het verstrekken van **voorrechten van de Beheerder** (binnen Adobe Analytics) is niet genoeg om een gebruiker toe te staan om van AEM met Adobe Analytics te verbinden. De rekening moet ook **voorrechten hebben van de Toegang van de Dienst van het 0&rbrace; Web.**

![&#x200B; chlimage_1-67 &#x200B;](assets/chlimage_1-67.png)

Voordat u verdergaat, moet u ervoor zorgen dat u zich bij Adobe Analytics kunt aanmelden. In een van de volgende gevallen:

* [&#x200B; het Teken van Adobe Experience Cloud &#x200B;](https://experience.adobe.com/#/@login/home)

* [&#x200B; het Teken van Adobe Analytics &#x200B;](https://sc.omniture.com/login/)

### AEM configureren voor het gebruik van uw Adobe Analytics-datacenters {#configuring-aem-to-use-your-adobe-analytics-data-centers}

Adobe Analytics [&#x200B; gegevenscentra &#x200B;](https://experienceleague.adobe.com/docs/analytics/analyze/reports-analytics/reporting-interface/overview-data-collection.html?lang=nl-NL) verzamelen, verwerken, en slaan gegevens verbonden aan uw het rapportreeks van Adobe Analytics op. Configureer AEM om het datacenter te gebruiken dat als host fungeert voor uw Adobe Analytics-rapportenpakket. Het datacenter wordt vermeld in uw contract. Neem voor deze informatie contact op met een beheerder in uw organisatie.

Gebruik indien nodig het volgende om naar het juiste datacenter te worden geleid: `https://api.omniture.com/` .

Als uw organisatie gegevensinzameling of herwinning van een specifiek gegevenscentrum vereist, gebruik het volgende:

| Datacenter | URL |
|---|---|
| Londen | `https://api3.omniture.com/` |
| Singapore | `https://api4.omniture.com/` |
| Oregon | `https://api5.omniture.com/` |

Gebruik de [&#x200B; Console van het Web om de bundel OSGi &#x200B;](/help/sites-deploying/configuring-osgi.md#osgi-configuration-with-the-web-console) te vormen **Adobe AEM de Cliënt van HTTP van Analytics**. Voeg het **Centrum URL van Gegevens** voor het gegevenscentrum toe dat gastheren een rapportreeks waarvoor uw AEM pagina&#39;s gegevens verzamelen.

![&#x200B; a-07 &#x200B;](assets/aa-07.png)

1. Open de webconsole in uw webbrowser. ([&#x200B; https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr))
1. Voer uw referenties in om toegang te krijgen tot de console.

   >[!NOTE]
   >
   >Neem contact op met de sitebeheerder als u wilt weten of u toegang hebt tot deze console.

1. Selecteer het punt van de Configuratie genoemd **Adobe AEM de Cliënt van HTTP van Analytics**.
1. Om URL voor een gegevenscentrum toe te voegen, druk + knoop naast de **lijst van het Centrum URLs van Gegevens**, en typ URL in de doos.

1. Klik op de knop - naast de URL om een URL uit de lijst te verwijderen.
1. Klik op Opslaan.

## De verbinding met Adobe Analytics configureren {#configuring-the-connection-to-adobe-analytics}

>[!CAUTION]
>
>Vanwege beveiligingswijzigingen in de Adobe Analytics API is het niet langer mogelijk om de versie van de Activity Map te gebruiken die in AEM is opgenomen.
>
>De [&#x200B; insteekmodule ActivityMap die door Adobe Analytics &#x200B;](https://experienceleague.adobe.com/docs/analytics/analyze/activity-map/getting-started/get-started-users/activitymap-install.html?lang=nl-NL) wordt verstrekt zou nu moeten worden gebruikt.

## Configureren voor de Activity Map {#configuring-for-the-activity-map}

>[!CAUTION]
>
>Vanwege beveiligingswijzigingen in de Adobe Analytics API is het niet langer mogelijk om de versie van de Activity Map te gebruiken die in AEM is opgenomen.
>
>De [&#x200B; insteekmodule ActivityMap die door Adobe Analytics &#x200B;](https://experienceleague.adobe.com/docs/analytics/analyze/activity-map/getting-started/get-started-users/activitymap-install.html?lang=nl-NL) wordt verstrekt zou nu moeten worden gebruikt.

## Een Adobe Analytics-framework maken {#creating-a-adobe-analytics-framework}

Voor identiteitskaart van de Reeks van het Rapport (RSID) die u gebruikt, kunt u controleren welke serverinstanties (auteur, publiceert, of allebei) gegevens aan de Reeks van het Rapport bijdragen:

* **allen**: De informatie van zowel de auteur als de publiceer instantie bevolkt de Reeks van het Rapport.
* **Auteur**: Slechts bevolkt de informatie van de auteursinstantie de Reeks van het Rapport.
* **Publish**: Slechts bevolkt de informatie van publiceert instantie de Reeks van het Rapport.

>[!NOTE]
>
>Het selecteren van het type van serverinstantie beperkt geen vraag tot Adobe Analytics, het controleert slechts welke vraag RSID omvat.
>
>Bijvoorbeeld, wordt een kader gevormd om de *diiweretail* rapportreeks te gebruiken en de auteur is de geselecteerde serverinstantie. Wanneer de pagina&#39;s samen met het kader worden gepubliceerd, worden de vraag nog gemaakt aan Adobe Analytics, nochtans bevatten deze vraag niet RSID. Slechts omvatten de vraag van de auteursinstantie RSID.

1. Gebruikend **Navigatie**, uitgezochte **Hulpmiddelen**, **Cloud Servicen**, toen **Oudere Cloud Servicen**.
1. De rol aan **Adobe Analytics** en selecteert **toont Configuraties**.
1. Klik de **[+]** verbinding naast uw configuratie van Adobe Analytics.

1. In **creeer Kader** dialoog:

   * Specificeer a **Titel**.
   * Naar keuze kunt u de **Naam** specificeren, voor de knoop die de kaderdetails in de bewaarplaats opslaat.
   * Selecteer **Kader van Adobe Analytics**

   En klik **creeer**.

   Het framework wordt geopend voor bewerking.

1. In de **sectie van de Suites van het Rapport** van de zijpeul (rechterkant van belangrijkste paneel), klik **Punt** toevoegen. Vervolgens gebruikt u de vervolgkeuzelijst om de rapportsuite-id (bijvoorbeeld `geometrixxauth` ) te selecteren waarmee het framework werkt.

   >[!NOTE]
   >
   >De inhoudzoeker aan de linkerkant wordt gevuld met Adobe Analytics-variabelen (SiteCatalyst Variables) wanneer u een rapportsuite-id selecteert.

1. Om de serverinstanties te selecteren die u informatie naar de Reeks van het Rapport wilt verzenden, gebruik de **drop-down Wijze van de Looppas** (naast Reeks van het Rapport identiteitskaart).

   ![&#x200B; a-framework-01 &#x200B;](assets/aa-framework-01.png)

1. Om het kader beschikbaar te maken op het publiceren geval van uw plaats, op het **lusje van de Pagina** van hulplid, klik **Activate Kader.**

### Serverinstellingen voor Adobe Analytics configureren {#configuring-server-settings-for-adobe-analytics}

Met het raamsysteem kunt u de serverinstellingen binnen elk Adobe Analytics-framework wijzigen.

>[!CAUTION]
>
>Deze montages bepalen waar uw gegevens worden verzonden en hoe, zodat is het noodzakelijk dat u *niet met deze montages* knoeit en uw vertegenwoordiger van Adobe Analytics in plaats daarvan plaatst.

Begin door het paneel te openen. Druk de benedenwaartse pijl naast **Servers**:

![&#x200B; server_001 &#x200B;](assets/server_001.png)

* **het Volgen Server**

   * bevat de URL waarmee Adobe Analytics-aanroepen worden verzonden

      * `cname` - gebreken aan de naam van het Bedrijf van de Adobe Analytics rekening **
      * `d1` - komt overeen met het datacenter waarnaar de informatie wordt verzonden (`d1` , `d2` of `d3` )
      * `sc.omtrdc.net` - domeinnaam

* **Veilige het Volgen Server**

   * Bevat dezelfde segmenten als de trackingserver
   * Wordt gebruikt voor het verzenden van gegevens van beveiligde pagina&#39;s (`https://`)

* **Namespace van de Bezoeker**

   * De naamruimte bepaalt het eerste deel van de URL voor bijhouden.
   * Bijvoorbeeld, veroorzaakt het veranderen van namespace in **CNAME** de vraag aan Adobe Analytics wordt gemaakt om als **CNAME.d1.omtr dc.net** in plaats van het gebrek te kijken dat.

## Een pagina koppelen aan een Adobe Analytics-framework {#associating-a-page-with-a-adobe-analytics-framework}

Wanneer een pagina is gekoppeld aan een Adobe Analytics-framework, verzendt de pagina gegevens naar Adobe Analytics wanneer de pagina wordt geladen. Variabelen die door de pagina worden gevuld, worden toegewezen aan en opgehaald uit Adobe Analytics-variabelen in het framework. Paginaweergaven worden bijvoorbeeld opgehaald uit Adobe Analytics.

Afstammingen van de pagina nemen de koppeling met het framework over. Wanneer u bijvoorbeeld de hoofdpagina van uw site aan een framework koppelt, worden alle pagina&#39;s van de site aan het framework gekoppeld.

1. Van de **console van Plaatsen**, selecteer de pagina u aan opstelling met het volgen wenst.
1. Open de **[Eigenschappen van de Pagina](/help/sites-authoring/editing-page-properties.md)**, of direct van de console, of de paginaredacteur.
1. Open het tabblad* Cloud Servicen**.

1. Gebruik **voeg de drop-down Configuratie** toe om **Adobe Analytics** van de beschikbare opties te selecteren. Als overerving is ingesteld, schakelt u die uit voordat de kiezer beschikbaar wordt.

1. De drop-down selecteur voor **Adobe Analytics** wordt toegevoegd aan de beschikbare opties. Selecteer de vereiste frameworkconfiguratie.

1. Selecteer **sparen &amp; Sluiten**.
1. Om de pagina en om het even welke verbonden configuraties/dossiers te activeren, **[Publish](/help/sites-authoring/publishing-pages.md)** de pagina.
1. De definitieve stap is de pagina op te bezoeken publiceert instantie en onderzoek naar een sleutelwoord (bijvoorbeeld, augplant) gebruikend de **component van het Onderzoek**.
1. U kunt dan de vraag controleren die aan Adobe Analytics wordt gemaakt gebruikend een aangewezen hulpmiddel; bijvoorbeeld, [&#x200B; Debugger van Adobe Experience Cloud &#x200B;](https://experienceleague.adobe.com/docs/experience-platform/debugger/home.html?lang=nl-NL).
1. Gebruikend het voorgelegde voorbeeld, zou de vraag de ingegane waarde (d.w.z., augplant) in eVar7 moeten bevatten en de gebeurtenislijst zou event3 moeten bevatten.

### Paginaweergaven {#page-views}

Wanneer een pagina aan een kader van Adobe Analytics wordt geassocieerd, kan het aantal paginameningen in de mening van de Lijst van de console van Plaatsen worden getoond.

Zie [&#x200B; het zien van de Gegevens van de Analytics van de Pagina &#x200B;](/help/sites-authoring/page-analytics-using.md) voor verdere details.

### Het Interval van de Invoer vormen {#configuring-the-import-interval}

Vorm de aangewezen instantie van de **Adobe AEM Analytics Report Sling Importer** dienst:

* **Vetch pogingen**:
Aantal pogingen om een een een rij gevormd rapport te halen.
De standaardwaarde is `6` .

* **de vertraging van de Opvanging**:
Het aantal milliseconden tussen pogingen om een een rij gevormd rapport te halen.
De standaardwaarde is `10000` . Aangezien dit in milliseconden is beantwoordt het aan 10 seconden.

* **Frequentie van de Opvanging**:
A `cron` expression to determine the frequency for fetching the Analytics Report.
De standaardwaarde is `0 0 0/12 * * ?` ; dit komt overeen met 12 opgehaalde gegevens per uur.

Om deze dienst te vormen OSGi, kunt u of de [&#x200B; Console van het Web &#x200B;](/help/sites-deploying/configuring-osgi.md#osgi-configuration-with-the-web-console) of een [&#x200B; osgiConfig knoop in de bewaarplaats &#x200B;](/help/sites-deploying/configuring-osgi.md#osgi-configuration-in-the-repository) gebruiken (de dienst PID is `com.day.cq.analytics.sitecatalyst.impl.importer.ReportImporterScheduler`).

## Adobe Analytics-configuraties en/of frameworks bewerken {#editing-adobe-analytics-configurations-and-or-frameworks}

Zoals wanneer het creëren van een configuratie of een kader van Adobe Analytics, navigeer aan het (erfenis) **scherm van Cloud Servicen**. Selecteer **tonen Configuraties**, dan klik de verbinding aan de specifieke configuratie u wilt bijwerken.

Wanneer het uitgeven van een configuratie van Adobe Analytics, druk **uitgeven** wanneer op de configuratiepagina zelf om **te openen geef de dialoog van de Component** uit.

## Adobe Analytics-frameworks verwijderen {#deleting-adobe-analytics-frameworks}

Om een kader van Adobe Analytics te schrappen, open eerst [&#x200B; het voor het uitgeven &#x200B;](#editing-adobe-analytics-configurations-and-or-frameworks).

Dan selecteer **Kader van de Schrapping** van het **Pagina** lusje van sidekick.
