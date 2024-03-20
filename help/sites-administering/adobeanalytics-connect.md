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
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1484'
ht-degree: 0%

---

# Verbinding maken met Adobe Analytics en frameworks maken {#connecting-to-adobe-analytics-and-creating-frameworks}

Als u webgegevens wilt bijhouden van uw AEM in Adobe Analytics, maakt u een Adobe Analytics Cloud Services-configuratie en een Adobe Analytics-framework:

* **Adobe Analytics-configuratie:** De informatie over je Adobe Analytics-account. Met de Adobe Analytics-configuratie kunnen AEM verbinding maken met Adobe Analytics. Maak een Adobe Analytics-configuratie voor elk account dat u gebruikt.
* **Adobe Analytics-framework:** Een set toewijzingen tussen eigenschappen van Adobe Analytics-rapportsuite en CQ-variabelen. Gebruik een framework om te configureren hoe uw websitegegevens uw Adobe Analytics-rapporten vullen. Frameworks zijn gekoppeld aan een Adobe Analytics-configuratie. U kunt veelvoudige kaders voor elke configuratie tot stand brengen.

Wanneer u een webpagina aan een framework koppelt, wordt de webpagina en de onderliggende pagina van die pagina bijgehouden. Paginaweergaven kunnen vervolgens worden opgehaald uit Adobe Analytics en worden weergegeven in de Sites-console.

## Vereisten {#prerequisites}

### Adobe Analytics-account {#adobe-analytics-account}

Als u AEM gegevens in Adobe Analytics wilt bijhouden, moet u een geldige Adobe Experience Cloud Adobe Analytics-account hebben.

De Adobe Analytics-account moet:

* hebben **Beheerder** rechten
* Aan de **Webservicetoegang** gebruikersgroep.

>[!CAUTION]
>
>Verstrekken **Beheerder** rechten (in Adobe Analytics) is niet voldoende om een gebruiker in staat te stellen verbinding te maken van AEM naar Adobe Analytics. De rekening moet ook **Webservicetoegang** rechten.

![chlimage_1-67](assets/chlimage_1-67.png)

Voordat u verdergaat, moet u ervoor zorgen dat u zich bij Adobe Analytics kunt aanmelden. In een van de volgende gevallen:

* [Aanmelden bij Adobe Experience Cloud](https://experience.adobe.com/#/@login/home)

* [Aanmelden bij Adobe Analytics](https://sc.omniture.com/login/)

### AEM configureren voor het gebruik van uw Adobe Analytics-datacenters {#configuring-aem-to-use-your-adobe-analytics-data-centers}

Adobe Analytics [datacenters](https://experienceleague.adobe.com/docs/analytics/analyze/reports-analytics/reporting-interface/overview-data-collection.html) gegevens verzamelen, verwerken en opslaan die bij uw Adobe Analytics-rapportenpakket horen. Configureer AEM om het datacenter te gebruiken dat als host fungeert voor uw Adobe Analytics-rapportenpakket. Het datacenter wordt vermeld in uw contract. Neem voor deze informatie contact op met een beheerder in uw organisatie.

Indien nodig, gebruik het volgende om aan het correcte gegevenscentrum worden verpletterd: `https://api.omniture.com/`.

Als uw organisatie gegevensinzameling of herwinning van een specifiek gegevenscentrum vereist, gebruik het volgende:

| Datacenter | URL |
|---|---|
| Londen | `https://api3.omniture.com/` |
| Singapore | `https://api4.omniture.com/` |
| Oregon | `https://api5.omniture.com/` |

Gebruik de [Webconsole om de OSGi-bundel te configureren](/help/sites-deploying/configuring-osgi.md#osgi-configuration-with-the-web-console) **Adobe AEM Analytics HTTP Client**. Voeg de **URL datacenter** voor het gegevenscentrum dat gastheren een rapportreeks waarvoor uw AEM pagina&#39;s gegevens verzamelen.

![aa-07](assets/aa-07.png)

1. Open de webconsole in uw webbrowser. ([https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr))
1. Voer uw referenties in om toegang te krijgen tot de console.

   >[!NOTE]
   >
   >Neem contact op met de sitebeheerder als u wilt weten of u toegang hebt tot deze console.

1. Selecteer genoemd het punt van de Configuratie **Adobe AEM Analytics HTTP Client**.
1. Als u de URL voor een datacenter wilt toevoegen, drukt u op de knop + naast de knop **Datacenter-URL&#39;s** en typ de URL in het vak.

1. Klik op de knop - naast de URL om een URL uit de lijst te verwijderen.
1. Klik op Opslaan.

## De verbinding met Adobe Analytics configureren {#configuring-the-connection-to-adobe-analytics}

>[!CAUTION]
>
>Vanwege beveiligingswijzigingen in de Adobe Analytics API is het niet langer mogelijk om de versie van de Activity Map te gebruiken die in AEM is opgenomen.
>
>De [ActivityMap-plug-in geleverd door Adobe Analytics](https://experienceleague.adobe.com/docs/analytics/analyze/activity-map/getting-started/get-started-users/activitymap-install.html) moet nu worden gebruikt.

## Configureren voor de Activity Map {#configuring-for-the-activity-map}

>[!CAUTION]
>
>Vanwege beveiligingswijzigingen in de Adobe Analytics API is het niet langer mogelijk om de versie van de Activity Map te gebruiken die in AEM is opgenomen.
>
>De [ActivityMap-plug-in geleverd door Adobe Analytics](https://experienceleague.adobe.com/docs/analytics/analyze/activity-map/getting-started/get-started-users/activitymap-install.html) moet nu worden gebruikt.

## Een Adobe Analytics-framework maken {#creating-a-adobe-analytics-framework}

Voor identiteitskaart van de Reeks van het Rapport (RSID) die u gebruikt, kunt u controleren welke serverinstanties (auteur, publiceert, of allebei) gegevens aan de Reeks van het Rapport bijdragen:

* **Alles**: De informatie van zowel de auteur als de publicatieinstantie vult de rapportsuite in.
* **Auteur**: Alleen informatie van de auteurinstantie vult de rapportsuite.
* **Publiceren**: Alleen informatie uit de publicatieinstantie vult de rapportsuite.

>[!NOTE]
>
>Het selecteren van het type van serverinstantie beperkt geen vraag tot Adobe Analytics, het controleert slechts welke vraag RSID omvat.
>
>Een framework is bijvoorbeeld geconfigureerd om het *diiweretail* rapportsuite en auteur is de geselecteerde serverinstantie. Wanneer de pagina&#39;s samen met het kader worden gepubliceerd, worden de vraag nog gemaakt aan Adobe Analytics, nochtans bevatten deze vraag niet RSID. Slechts omvatten de vraag van de auteursinstantie RSID.

1. Gebruiken **Navigatie**, selecteert u **Gereedschappen**, **Cloud Servicen** vervolgens **Oudere Cloud Servicen**.
1. Schuiven naar **Adobe Analytics** en selecteert u **Configuraties tonen**.
1. Klik op de knop **[+]** naast uw Adobe Analytics-configuratie.

1. In de **Framework maken** dialoogvenster:

   * Geef een **Titel**.
   * U kunt desgewenst de optie **Naam**, voor het knooppunt dat de frameworkgegevens in de opslagplaats opslaat.
   * Selecteren **Adobe Analytics Framework**

   en klik op **Maken**.

   Het framework wordt geopend voor bewerking.

1. In de **Rapportageopties** van de zijpod (rechterkant van het hoofddeelvenster) klikt u op **Item toevoegen**. Gebruik vervolgens de vervolgkeuzelijst om de rapportsuite-id te selecteren (bijvoorbeeld `geometrixxauth`) waarmee het kader interactie heeft.

   >[!NOTE]
   >
   >De inhoudzoeker aan de linkerkant wordt gevuld met Adobe Analytics-variabelen (SiteCatalyst Variables) wanneer u een rapportsuite-id selecteert.

1. Om de serverinstanties te selecteren die u informatie naar de Reeks van het Rapport wilt verzenden, gebruik **Run-modus** vervolgkeuzelijst (naast de rapportsuite-id).

   ![aa-framework-01](assets/aa-framework-01.png)

1. Als u het framework beschikbaar wilt maken op het publicatieexemplaar van uw site, gaat u naar de **Pagina** tab of sidekick, klik op **Activeer Framework.**

### Serverinstellingen voor Adobe Analytics configureren {#configuring-server-settings-for-adobe-analytics}

Met het raamsysteem kunt u de serverinstellingen binnen elk Adobe Analytics-framework wijzigen.

>[!CAUTION]
>
>Deze instellingen bepalen waar en hoe uw gegevens worden verzonden. Het is dus absoluut noodzakelijk dat u *niet knoeien met deze instellingen* en laat uw Adobe Analytics-vertegenwoordiger het instellen.

Begin door het paneel te openen. Druk op de pijl omlaag naast **Servers**:

![server_001](assets/server_001.png)

* **Trackingserver**

   * bevat de URL waarmee Adobe Analytics-aanroepen worden verzonden

      * `cname` - wordt standaard ingesteld op de Adobe Analytics-account *Bedrijfsnaam*
      * `d1` - komt overeen met het datacenter waarnaar de informatie wordt verzonden (ofwel `d1`, `d2`, of `d3`)
      * `sc.omtrdc.net` - domeinnaam

* **Secure Tracking Server**

   * Bevat dezelfde segmenten als de trackingserver
   * Wordt gebruikt voor het verzenden van gegevens van beveiligde pagina&#39;s (`https://`)

* **Naamruimte van bezoeker**

   * De naamruimte bepaalt het eerste deel van de URL voor bijhouden.
   * De naamruimte wijzigen in **CNAME** veroorzaakt de vraag aan Adobe Analytics om te kijken als **CNAME.d1.omtrdc.net** in plaats van de standaardinstelling.

## Een pagina koppelen aan een Adobe Analytics-framework {#associating-a-page-with-a-adobe-analytics-framework}

Wanneer een pagina is gekoppeld aan een Adobe Analytics-framework, verzendt de pagina gegevens naar Adobe Analytics wanneer de pagina wordt geladen. Variabelen die door de pagina worden gevuld, worden toegewezen aan en opgehaald uit Adobe Analytics-variabelen in het framework. Paginaweergaven worden bijvoorbeeld opgehaald uit Adobe Analytics.

Afstammingen van de pagina nemen de koppeling met het framework over. Wanneer u bijvoorbeeld de hoofdpagina van uw site aan een framework koppelt, worden alle pagina&#39;s van de site aan het framework gekoppeld.

1. Van de **Sites** -console, selecteert u de pagina die u wilt instellen met bijhouden.
1. Open de **[Pagina-eigenschappen](/help/sites-authoring/editing-page-properties.md)**, rechtstreeks vanuit de console of de pagina-editor.
1. Open het tabblad* Cloud Servicen**.

1. Gebruik de **Configuratie toevoegen** vervolgkeuzelijst om te selecteren **Adobe Analytics** uit de beschikbare opties. Als overerving is ingesteld, schakelt u die uit voordat de kiezer beschikbaar wordt.

1. De vervolgkeuzelijst voor **Adobe Analytics** wordt toegevoegd aan de beschikbare opties. Selecteer de vereiste frameworkconfiguratie.

1. Selecteren **Opslaan en sluiten**.
1. De pagina en alle aangesloten configuraties/bestanden activeren **[Publiceren](/help/sites-authoring/publishing-pages.md)** de pagina.
1. De laatste stap bestaat uit het bezoeken van de pagina op de publicatie-instantie en het zoeken naar een trefwoord (bijvoorbeeld een tag) met de opdracht **Zoeken** component.
1. U kunt dan de vraag controleren die aan Adobe Analytics wordt gemaakt gebruikend een aangewezen hulpmiddel; bijvoorbeeld [Adobe Experience Cloud Debugger](https://experienceleague.adobe.com/docs/experience-platform/debugger/home.html).
1. Gebruikend het voorgelegde voorbeeld, zou de vraag de ingegane waarde (d.w.z., augplant) in eVar7 moeten bevatten en de gebeurtenislijst zou event3 moeten bevatten.

### Paginaweergaven {#page-views}

Wanneer een pagina aan een kader van Adobe Analytics wordt geassocieerd, kan het aantal paginameningen in de mening van de Lijst van de console van Plaatsen worden getoond.

Zie [Gegevens van paginaanalyse bekijken](/help/sites-authoring/page-analytics-using.md) voor nadere bijzonderheden.

### Het Interval van de Invoer vormen {#configuring-the-import-interval}

Vorm de aangewezen instantie van **Adobe AEM Analytics Report Sling Importer** service:

* **Ophaalpogingen**: Aantal pogingen om een een rij gevormd rapport te halen.
De standaardwaarde is `6`.

* **Ophaalvertraging**: Het aantal milliseconden tussen pogingen om een een rij gevormd rapport te halen.
De standaardwaarde is `10000`. Aangezien dit in milliseconden is beantwoordt het aan 10 seconden.

* **Ophaalfrequentie**: A `cron` om de frequentie voor het ophalen van het Analyserapport te bepalen.
De standaardwaarde is `0 0 0/12 * * ?`; dit komt overeen met 12 ophaalbeurten per uur.

Om deze dienst te vormen OSGi, kunt u of gebruiken [Webconsole](/help/sites-deploying/configuring-osgi.md#osgi-configuration-with-the-web-console) of een [osgiConfig-knooppunt in de repository](/help/sites-deploying/configuring-osgi.md#osgi-configuration-in-the-repository) (De service-PID is `com.day.cq.analytics.sitecatalyst.impl.importer.ReportImporterScheduler`).

## Adobe Analytics-configuraties en/of frameworks bewerken {#editing-adobe-analytics-configurations-and-or-frameworks}

Ga net als bij het maken van een Adobe Analytics-configuratie of -framework naar de (verouderd) **Cloud Servicen** scherm. Selecteren **Configuraties tonen** klikt u vervolgens op de koppeling naar de specifieke configuratie die u wilt bijwerken.

Druk op **Bewerken** wanneer op de configuratiepagina zelf om de **Component bewerken** in.

## Adobe Analytics-frameworks verwijderen {#deleting-adobe-analytics-frameworks}

Als u een Adobe Analytics-framework wilt verwijderen, moet u eerst [openen voor bewerken](#editing-adobe-analytics-configurations-and-or-frameworks).

Selecteer vervolgens **Framework verwijderen** van de **Pagina** tabblad van het hulpwerkje.
