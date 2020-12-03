---
title: Caching configureren voor Forms
seo-title: Caching configureren voor Forms
description: Leer hoe te om geheim voorgeheugenmontages te vormen en hoe te om overwegingen voor geheime voorgeheugens te groeperen.
seo-description: Leer hoe te om geheim voorgeheugenmontages te vormen en hoe te om overwegingen voor geheime voorgeheugens te groeperen.
uuid: 70f36191-4163-410b-991a-e1481488aea0
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 8a07dddf-1281-45ac-a55e-4333b860a261
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '1625'
ht-degree: 0%

---


# Het vormen caching voor Forms{#configuring-caching-for-forms}

De Forms-service bestaat uit formulierontwerpen die in Designer zijn gemaakt en die in verschillende indelingen worden weergegeven.

De Forms-pagina in de beheerconsole bevat instellingen die bepalen hoe de Forms-service items in cache plaatst. U kunt deze instellingen aanpassen om de prestaties van de Forms-service te optimaliseren.

De Forms service plaatst de volgende items in cache:

* **formulierontwerpen:** de Forms-service plaatst formulierontwerpen in cache die ze ophalen uit de gegevensopslagruimte of HTTP-bronnen. Dit in cache plaatsen verbetert de prestaties, omdat de Forms-service het formulierontwerp ophaalt uit de cache in plaats van uit de opslagplaats.
* **fragmenten en afbeeldingen:** de Forms-service kan fragmenten en afbeeldingen die in formulierontwerpen worden gebruikt, in cache plaatsen. Wanneer de Forms-service deze objecten in cache plaatst, worden de prestaties verbeterd omdat de fragmenten en afbeeldingen alleen worden gelezen uit de opslagplaats op het eerste verzoek.
* **formulieren:** de Forms-service plaatst de formulieren die worden gegenereerd in cache. Dit type caching verbetert de prestaties omdat de Forms-service niet hetzelfde formulier hoeft op te lossen en weer te geven in volgende aanvragen.

Forms slaat de cache op twee plaatsen op:

* **in het geheugen:** Items worden in het geheugen opgeslagen, zodat ze snel kunnen worden geopend. De cache in het geheugen heeft een beperkte grootte en wordt verwijderd wanneer u de server opnieuw start.
* **op schijf:** Items worden opgeslagen in het bestandssysteem van de server. De schijfcache heeft een grotere capaciteit dan de cache in het geheugen en deze blijft behouden wanneer u de server opnieuw start. De locatie van de schijfcache is afhankelijk van de toepassingsserver. Zie [Locaties configureren voor Forms](/help/forms/using/admin-help/configuring-locations-forms.md#configuring-locations-for-forms) voor informatie over het wijzigen van de locatie van de schijfcache.

## De cachemodus {#specifying-the-cache-mode} opgeven

Forms biedt ondersteuning voor twee modi voor caching:

* onvoorwaardelijk
* het gebruiken van het punt van de geheim voorgeheugencontrole

Als u tussen cachemodi schakelt, start u de Forms-service opnieuw om de wijziging van kracht te laten worden. Als u deze service opnieuw wilt starten, gebruikt u Workbench of raadpleegt u [De services die aan AEM formuliermodules zijn gekoppeld, starten of stoppen voor instructies.](/help/forms/using/admin-help/starting-stopping-services.md#start-or-stop-the-services-associated-with-aem-forms-modules)

De tijd van het punt van de geheim voorgeheugencontrole wordt automatisch teruggesteld wanneer u tussen wijzen schakelt.

### Onvoorwaardelijke caching {#using-unconditional-caching} gebruiken

Wanneer de Forms-service in deze modus een aanvraag ontvangt, worden de vereiste bronnen (formulierontwerp en gerelateerde elementen zoals fragmenten en afbeeldingen) gevalideerd. De Forms-service vergelijkt de tijdstempel van de bronnen in de opslagplaats met de tijdstempel van de bronnen in de cache. Als de resource in de cache ouder is, wordt deze door de Forms-service bijgewerkt.

Deze cachemodus garandeert dat de meest recente bronnen worden gebruikt. De prestaties worden echter beïnvloed omdat de Forms-service de in de cache opgeslagen items bij elke aanvraag valideert tegen de repository. Deze cachemodus is geschikt voor ontwikkelings- en staging-omgevingen waar bronnen regelmatig worden bijgewerkt en prestaties geen primair probleem zijn.

**Onvoorwaardelijke caching opgeven**

1. Klik in de beheerconsole op Services > Forms.
1. Selecteer Onvoorwaardelijk onder Forms Cache Control Settings en klik op Save.

### Het controlepunt voor de cache {#use-the-cache-check-point} gebruiken

In deze modus controleert de Forms-service alleen de opslagplaats op nieuwere versies van bronnen wanneer de tijdstempel van de resource in de cache ouder is dan de tijd van het controlepunt voor de cache. De laatste tijd van het punt van de geheim voorgeheugencontrole wordt getoond op de pagina van Forms in de Console van het Beleid.

Gebruik deze cachemodus in productieomgevingen met hoge prestaties waar de prestaties van belang zijn en wijzigingen in bronnen niet vaak voorkomen. U kunt de tijd van het punt van de geheim voorgeheugencontrole terugstellen wanneer u om het even welke veranderingen wilt opstellen die aan de bewaarplaatsmiddelen worden aangebracht.

**Het gebruik van een cachecontrolepunt opgeven**

1. Klik in Beheerconsole op Services > Forms.
1. Selecteer onder Instellingen voor Cachebeheer van Forms de optie Alleen als de laatste validatie is uitgevoerd vóór de tijd van het controlepunt voor de cache en klik op Opslaan.

**Het controlepunt voor de cache opnieuw instellen**

1. Klik in de beheerconsole op Services > Forms.
1. Klik onder Forms Cache Control Settings op Cache Check Point.

**De inhoud van de cache opnieuw instellen**

U kunt de inhoud van de cache op elk gewenst moment wissen. Na het opnieuw instellen van de cache wordt de eerste aanvraag voor elk formulier langzamer, omdat de Forms-service een volledige rendering uitvoert en nieuwe cacheinhoud maakt.

1. Klik in de beheerconsole op Services > Forms.
1. Klik onder Forms Cache Control Settings op Reset Cache.

## Cacheinstellingen {#configuring-cache-settings} configureren

U kunt instellingen opgeven die Forms gebruikt voor het in cache plaatsen, zodat de prestaties van uw AEM-formulieromgeving optimaal zijn.

Klik in de beheerconsole op Services > Forms om deze instellingen te openen.

>[!NOTE]
>
>De schijfvereisten voor de cache moeten gelijk zijn aan die van de opslagplaats.

### Globale cache-instellingen opgeven {#specifying-global-cache-settings}

De instellingen in het gebied **Algemene cache-instellingen** hebben invloed op alle typen caches. Als u een van deze instellingen wijzigt, start u de Forms-service opnieuw, zodat de wijziging van kracht wordt. Als u deze service opnieuw wilt starten, gebruikt u Workbench of raadpleegt u [De services die aan AEM formuliermodules zijn gekoppeld, starten of stoppen voor instructies.](/help/forms/using/admin-help/starting-stopping-services.md#start-or-stop-the-services-associated-with-aem-forms-modules)

**Max. documentgrootte cache (kB):** de maximale grootte in kilobytes van een formulierontwerp of andere bron die in een cache in het geheugen kan worden opgeslagen. Dit is een algemene instelling die van toepassing is op alle cache in het geheugen. Als een bron groter is dan deze waarde, wordt deze niet in het geheugen opgeslagen. De standaardwaarde is 1024 kilobytes. Deze instelling heeft geen invloed op de cache van de schijf.

**Formulierrendercache ingeschakeld:** Standaard is deze optie geselecteerd, wat betekent dat gerenderde formulieren in cache worden geplaatst voor volgende opvraging. Deze instelling verbetert de prestaties omdat de Forms-service slechts één keer een bepaald formulier hoeft te genereren en vervolgens de versie in de cache gebruikt. Deze optie werkt met de eigenschap voor het in cache plaatsen van het formulierontwerp. Zie Help bij Designer voor informatie over het configureren van deze waarde in het formulierontwerp.

### Formulierontwerpen {#caching-form-designs} in cache plaatsen

Wanneer de Forms-service een renderaanvraag ontvangt, haalt deze het formulierontwerp op van de gegevensopslagruimte en plaatst deze het in cache. Dit in cache plaatsen verbetert de prestaties, omdat de Forms-service het formulierontwerp ophaalt uit de cache in plaats van uit de opslagplaats.

De Forms-service plaatst formulierontwerpen altijd in cache op schijf. Als formulierontwerpen worden opgeslagen op de server, worden deze bestanden beschouwd als de schijfcache. De Forms-service plaatst ook formulierontwerpen in het geheugen in cache volgens de instelling in het gebied **In Geheugensjablooncache**. Als u een van deze instellingen wijzigt, start u de Forms-service opnieuw, zodat de wijziging van kracht wordt. Als u deze service opnieuw wilt starten, gebruikt u Workbench of raadpleegt u [De services die aan AEM formuliermodules zijn gekoppeld, starten of stoppen voor instructies.](/help/forms/using/admin-help/starting-stopping-services.md#start-or-stop-the-services-associated-with-aem-forms-modules)

**Cachegrootte sjabloonconfiguratie:** het maximumaantal sjabloonconfiguratieobjecten dat in het geheugen moet worden bewaard. De standaardwaarde is 100. U wordt aangeraden deze waarde groter dan of gelijk aan de waarde voor Grootte sjablooncache in te stellen. Deze instelling heeft geen invloed op de cache van de schijf.

**Grootte sjablooncache:** het maximumaantal sjablooninhoudobjecten dat in het geheugen mag worden bewaard. De standaardwaarde is 100. Deze instelling heeft geen invloed op de cache van de schijf.

**Ingeschakeld:** Standaard is dit selectievakje ingeschakeld, wat betekent dat formuliersjablonen in het geheugen worden opgeslagen. Als deze optie niet is geselecteerd, worden formuliersjablonen alleen op de schijf in het cachegeheugen opgeslagen.

### Gerenderde formulieren {#caching-rendered-forms} in cache plaatsen

De Forms-service plaatst gegenereerde formulieren in cache, zodat deze niet hetzelfde formulier hoeven op te lossen en weer te geven in volgende aanvragen. Gegenereerde formulieren worden zowel op de schijf als in het geheugen in cache geplaatst.

Deze instellingen bevinden zich in het gebied **In cache voor het renderen van geheugenformulieren**. Als u een van deze instellingen wijzigt, start u de Forms-service opnieuw, zodat de wijziging van kracht wordt. Als u deze service opnieuw wilt starten, gebruikt u Workbench of raadpleegt u [De services die aan AEM formuliermodules zijn gekoppeld, starten of stoppen voor instructies.](/help/forms/using/admin-help/starting-stopping-services.md#start-or-stop-the-services-associated-with-aem-forms-modules)

**Cachegrootte:** Hiermee geeft u het maximum aantal weergegeven formulieren op dat zich in de cache in het geheugen kan bevinden. De standaardwaarde is 100. Deze instelling heeft geen invloed op de cache van de schijf.

**Ingeschakeld:** Deze optie is standaard geselecteerd, wat betekent dat de weergegeven formulieren in het geheugen worden opgeslagen. Als deze optie niet is geselecteerd, worden de weergegeven formulieren alleen op de schijf in het cachegeheugen opgeslagen.

### Fragmenten en afbeeldingen {#caching-fragments-and-images} in cache plaatsen

De Forms-service plaatst fragmenten en afbeeldingen die in formulierontwerpen op schijf worden gebruikt in cache. Dit verbetert de prestaties, omdat de fragmenten en afbeeldingen alleen worden gelezen van de opslagplaats op het eerste verzoek. Vervolgens leest de Forms-service fragmenten en afbeeldingen uit de cache van de schijf. Fragmenten en afbeeldingen worden alleen op de schijf in het cachegeheugen opgeslagen en niet in het geheugen.

Met de volgende instellingen kunt u het in cache plaatsen op schijf van fragmenten en afbeeldingen beheren. Deze instellingen bevinden zich in het gebied **Sjabloonbroncacheinstellingen**:

**In** cache plaatsenSelecteer een van de volgende opties in de lijst:

**Ingeschakeld voor fragmenten en afbeeldingen:** de Forms-service plaatst fragmenten en afbeeldingen in cache. Dit is de standaardoptie.

**Ingeschakeld voor fragmenten:** de Forms-service plaatst fragmenten in cache, maar afbeeldingen niet.

**Uitgeschakeld:** de Forms-service slaat fragmenten of afbeeldingen niet in het cachegeheugen op.

**Interval opschonen (seconden):** geeft aan hoe vaak de Forms-service oude ongeldige cachebestanden verwijdert. De Forms-service verwijdert geen geldige cachebestanden. Als u het opschooninterval wijzigt, start u de Forms-service opnieuw om de wijziging in werking te laten treden. Als u deze service opnieuw wilt starten, gebruikt u Workbench of raadpleegt u De services die zijn gekoppeld aan AEM formuliermodules starten of stoppen voor instructies. De standaardwaarde is 600 seconden.

## Overwegingen voor clustering voor caches {#clustering-considerations-for-caches}

In een gegroepeerde omgeving, handhaaft elke knoop zijn eigen in-geheugen en schijfgeheime voorgeheugen. De inhoud van de cache op elk knooppunt hangt af van de formulieren die op dat knooppunt zijn gegenereerd.

De locatie van de cache moet identiek zijn (dezelfde schijf en hetzelfde pad) op elk knooppunt van de cluster. Plaats de cache niet op gedeelde opslag.

Als u de Forms-pagina in de beheerconsole gebruikt om de cache-instellingen voor een bepaald knooppunt te wijzigen, worden de cache-instellingen op andere knooppunten bijgewerkt wanneer een aanvraag naar dat knooppunt gaat. Dit gedrag is ook van toepassing op de knoop van het Geheime voorgeheugen van het Terugstellen. Als u op de knop Cache opnieuw instellen voor één knooppunt klikt, wordt de cache onmiddellijk uit dat knooppunt verwijderd. Het geheime voorgeheugen op andere knopen wordt ontruimd wanneer een verzoek naar dat knoop gaat.
