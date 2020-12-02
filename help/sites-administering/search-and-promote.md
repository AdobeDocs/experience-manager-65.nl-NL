---
title: Integreren met Adobe Search&Promote
seo-title: Integreren met Adobe Search&Promote
description: Leer hoe u kunt integreren met Adobe Search&Promote.
seo-description: Leer hoe u kunt integreren met Adobe Search&Promote.
uuid: 7e9384d9-9e4f-4e00-a1c9-35547de6ceb8
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
discoiquuid: aca444f6-418a-4c01-ae19-663b4e04fab9
docset: aem65
translation-type: tm+mt
source-git-commit: 1c1ade947f2cbd26b35920cfd10b1666b132bcbd
workflow-type: tm+mt
source-wordcount: '910'
ht-degree: 1%

---


# Integreren met Adobe Search&amp;Promote{#integrating-with-adobe-search-promote}

Voer de volgende taken uit om de service Adobe Search&amp;Promote van uw website aan te roepen:

1. Geef de URL van de cloud op.
1. Configureer de verbinding met de service Search&amp;Promote.
1. Voeg Search&amp;Promote-componenten toe aan Sidetrap.
1. Gebruik de componenten om de inhoud te ontwerpen. (Zie [Search&amp;Promote toevoegen aan een webpagina](/help/sites-authoring/search-and-promote.md).)
1. Voeg banners toe aan uw pagina&#39;s. Bannerafbeeldingen zijn gevoelig voor Search&amp;Promote-gegevens.
1. Genereer een site-overzicht voor de service Search&amp;Promote die u wilt gebruiken.

>[!NOTE]
>
>Als u Search&amp;Promote met een configuratie van de douanevolmacht gebruikt, moet u zowel de volmachtsconfiguraties van de Cliënt van HTTP vormen aangezien sommige functionaliteiten van AEM de 3.x APIs en sommige anderen 4.x APIs gebruiken:
>
>* 3.x is geconfigureerd met [https://localhost:4502/system/console/configMgr/com.day.commons.httpclient](https://localhost:4502/system/console/configMgr/com.day.commons.httpclient)
>* 4.x wordt geconfigureerd met [https://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator](https://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator)

>



## De service-URL van de Search&amp;Promote wijzigen {#changing-the-search-promote-service-url}

De standaard URL die voor de dienst van de Search&amp;Promote wordt gevormd is `https://searchandpromote.omniture.com/px/`. Om de verschillende dienst te gebruiken, gebruik de console OSGi om een verschillende URL te specificeren.

1. Open de console OSGi en klik de Configuratie tabel. ([https://localhost:4502/system/console/configMgr.](https://localhost:4502/system/console/configMgr))
1. Klik het punt van de Configuratie van de Search&amp;Promote van Dag CQ.
1. Voer de URL in het vak Externe server-URI in en klik op Opslaan.

## De verbinding met Search&amp;Promote {#configuring-the-connection-to-search-promote} configureren

Vorm één of meerdere verbindingen aan Search&amp;Promote zodat uw Web-pagina&#39;s met de dienst kunnen interactie aangaan. Als u verbinding wilt maken, hebt u de lididentificatie en het accountnummer van uw Search&amp;Promote-account nodig.

1. Selecteer **Gereedschappen** pictogram > **Implementatie** **Cloud Services**.

   Hiermee gaat u naar het dashboard van Cloud Services. Als de URL van het dashboard op een lokale machine er ongeveer als volgt uitziet:

   [https://localhost:4502/libs/cq/core/content/tools/cloudservices.html](https://localhost:4502/libs/cq/core/content/tools/cloudservices.html)

1. Klik op de pagina Cloud Services op de koppeling Adobe Search&amp;Promote of Search&amp;Promote.

1. Als dit de eerste keer is vormt u Adobe Search&amp;Promote, klik **vorm nu** om het Create paneel van de Configuratie te openen.

   Als u meer over Search&amp;Promote wilt leren klikt **Meer** in plaats daarvan.

   ![](assets/chlimage_1-59.png)

1. Voer een **Titel** in die herkenbaar is voor auteurs van pagina&#39;s en voer een unieke **Naam** in en klik vervolgens op **Maken**.

   Het venster **Component bewerken** wordt geopend.

   Ook, verschijnt de pas gecreëerde Configuratie onder **Beschikbare Configuraties** op **Cloud Services dashboard** de lijstpunt van de Search&amp;Promote van de Adobe.

   ![](assets/chlimage_1-60.png)

1. Voeg het volgende toe aan de gebieden in **geef Component** dialoogdoos uit.

   * **Lid-id**
   * **Rekeningnummer**

   >[!NOTE]
   >
   >Om deze informatie **uzelf te krijgen,** moet u eerst login
   >
   >[https://searchandpromote.omniture.com/center/](https://searchandpromote.omniture.com/center/)
   >
   >
   >met uw geldige e-mail&amp;Promote referenties (e-mail/wachtwoord).
   >Dan, moet u uw url in de adresbar van uw browser bekijken die iets als dit zou moeten kijken:
   >[](https://searchandpromote.omniture.com/px/home/?sp_id=XXXXXXXX-spYYYYYYYY)
   >
   >[https://searchandpromote.omniture.com/px/home/?sp_id=XXXXXXXX-spYYYYYYYY](https://searchandpromote.omniture.com/px/home/?sp_id=XXXXXXXX-spYYYYYYYY)
   >
   >**Waar:**
   >
   >    * **** XXXXXXXXXX komt overeen met uw** lid-id**
   >    * **** spYYYYYY komt overeen met uw  **accountnummer**


1. Klik **Verbinding maken met Search&amp;Promote**.

   Wanneer het bericht van het verbindingssucces verschijnt, klik **OK**.

   (Na verbinding wordt de knoptekst gewijzigd in** Opnieuw verbinden met Search&amp;Promote**.)

1. Klik **OK**. De pagina Instellingen Search&amp;Promote wordt weergegeven voor de configuratie die u zojuist hebt gemaakt.

## Het vormen van het Centrum van Gegevens {#configuring-the-data-center}

Als uw Search&amp;Promote-account zich in Azië of Europa bevindt, moet u het standaarddatacenter wijzigen zodat het naar het juiste datacenter wijst (het standaarddatacenter is voor Noord-Amerikaanse accounts).

Het datacenter configureren:

1. Navigeer naar de webconsole op `https://localhost:4502/system/console/configMgr/com.day.cq.searchpromote.impl.SearchPromoteServiceImpl`

   ![](assets/chlimage_1-61.png)

1. Wijzig afhankelijk van de locatie van de server de URI in een van de volgende:

   * Noord-Amerika: [https://center.atomz.com/px/](https://center.atomz.com/px/)
   * EMEA: [https://center.lon5.atomz.com/px/](https://center.lon5.atomz.com/px/)
   * APAC: [https://center.sin2.atomz.com/px/](https://center.sin2.atomz.com/px/)

1. Klik **Opslaan**.

## Search&amp;Promote toevoegen aan Sidetrap {#adding-search-promote-components-to-sidekick}

Bewerk in de ontwerpmodus een **par**-component om de Search&amp;Promote-componenten in Sidetrap toe te staan. (Zie de documentatie [Components](/help/sites-developing/components.md#addinganewcomponenttotheparagraphsystemdesignmode) voor meer informatie.)

Voor informatie over het gebruiken van de componenten, zie [Search&amp;Promote aan een Web-pagina toevoegen](/help/sites-authoring/search-and-promote.md).)

## De service Search&amp;Promote opgeven die uw pagina&#39;s gebruiken {#specifying-the-search-promote-service-that-your-pages-use}

Webpagina&#39;s configureren zodat deze een specifieke Search&amp;Promote-service gebruiken. Componenten van Search&amp;Promote gebruiken automatisch de service van hun hostpagina.

Wanneer u de Search&amp;Promote-eigenschappen voor een pagina configureert, nemen alle onderliggende pagina&#39;s de instellingen over. Indien nodig, kunt u kindpagina&#39;s vormen om de geërfte montages met voeten te treden.

>[!NOTE]
>
>De de dienstverbinding moet reeds worden gevormd. (Zie [De verbinding met Search&amp;Promote](#connection) configureren.)

1. Open het dialoogvenster **Pagina-eigenschappen**. Klik bijvoorbeeld op de pagina** Websites** met de rechtermuisknop op de pagina en klik op **Eigenschappen**.
1. Klik op het tabblad **Cloud Services**.
1. Als u de overerving van configuraties van cloudservices van een bovenliggende pagina wilt uitschakelen, klikt u op het hangslotpictogram naast het overervingspad.

   ![](assets/sandpinheritpadlock.png)

1. Klik **Service toevoegen**, selecteer **Adobe Search&amp;Promote**, en klik **OK**.
1. Selecteer de verbindingsconfiguratie voor uw Search&amp;Promote-account en klik op **OK**.

## Productfeed {#product-feed}

Dankzij de Search&amp;Promote-integratie kunt u:

* gebruik de eCommerce-API, onafhankelijk van de onderliggende structuur van de gegevensopslagruimte en het handelsplatform.
* hefboomwerking de eigenschap van de Schakelaar van de Index van Search&amp;Promote om een productvoer in formaat van XML te verstrekken.
* de functie voor afstandsbediening van Search&amp;Promote gebruiken om op aanvraag of geplande aanvragen van de productfeed uit te voeren
* feed generation voor verschillende Search&amp;Promote-accounts, geconfigureerd als cloudservices configuraties.

Lees [Productfeed](/help/sites-administering/product-feed.md) voor meer informatie.
