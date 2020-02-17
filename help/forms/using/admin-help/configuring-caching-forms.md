---
title: Caching voor Forms configureren
seo-title: Caching voor Forms configureren
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

---


# Caching voor Forms configureren{#configuring-caching-for-forms}

De service Forms maakt gebruik van formulierontwerpen die zijn gemaakt in Designer en geeft deze in verschillende indelingen weer.

De pagina van Vormen in beleidsconsole bevat montages die de manier controleren de dienst van Vormen punten in het voorgeheugen plaatst. U kunt deze instellingen aanpassen om de prestaties van de service Forms te optimaliseren.

De service Forms plaatst de volgende items in cache:

* **** formulierontwerpen: De Forms-service plaatst formulierontwerpen in cache die worden opgehaald uit de opslagplaats of uit HTTP-bronnen. Dit in cache plaatsen verbetert de prestaties, omdat bij volgende renderaanvragen het formulierontwerp door de Forms-service wordt opgehaald uit de cache in plaats van uit de opslagplaats.
* **** fragmenten en afbeeldingen: Met Forms kunt u fragmenten en afbeeldingen die in formulierontwerpen worden gebruikt, in cache plaatsen. Wanneer deze objecten in cache worden geplaatst door de Forms-service, worden de prestaties verbeterd omdat de fragmenten en afbeeldingen alleen op de eerste aanvraag uit de opslagplaats worden gelezen.
* **** formulieren: De service Forms plaatst de formulieren die erin worden gegenereerd in cache. Dit type caching verbetert de prestaties omdat de service Forms niet hetzelfde formulier hoeft op te lossen en weer te geven in volgende aanvragen.

Forms slaat de cache op twee plaatsen op:

* **** in het geheugen: Items worden in het geheugen opgeslagen zodat ze snel kunnen worden geopend. De cache in het geheugen heeft een beperkte grootte en wordt verwijderd wanneer u de server opnieuw start.
* **** op schijf: Items worden opgeslagen in het bestandssysteem van de server. De schijfcache heeft een grotere capaciteit dan de cache in het geheugen en deze blijft behouden wanneer u de server opnieuw start. De locatie van de schijfcache is afhankelijk van de toepassingsserver. Zie Locaties [configureren voor Forms](/help/forms/using/admin-help/configuring-locations-forms.md#configuring-locations-for-forms)voor informatie over het wijzigen van de locatie van de schijfcache.

## De cachemodus opgeven {#specifying-the-cache-mode}

Forms ondersteunt twee modi voor het in cache plaatsen:

* onvoorwaardelijk
* het gebruiken van het punt van de geheim voorgeheugencontrole

Als u tussen cachemodi schakelt, start u de service Forms opnieuw om de wijziging door te voeren. Als u deze service opnieuw wilt starten, gebruikt u Workbench of raadpleegt u de services die aan de AEM-formuliermodules [](/help/forms/using/admin-help/starting-stopping-services.md#start-or-stop-the-services-associated-with-aem-forms-modules) zijn gekoppeld, starten of stoppen voor instructies.

De tijd van het punt van de geheim voorgeheugencontrole wordt automatisch teruggesteld wanneer u tussen wijzen schakelt.

### Onvoorwaardelijke caching gebruiken {#using-unconditional-caching}

Wanneer de service Forms in deze modus een aanvraag ontvangt, worden de vereiste bronnen (formulierontwerp en gerelateerde elementen zoals fragmenten en afbeeldingen) gevalideerd. De dienst van Vormen vergelijkt timestamp van de middelen in de bewaarplaats met timestamp van de middelen in het geheime voorgeheugen. Als het middel in het geheime voorgeheugen ouder is, werkt de dienst van Vormen het bij.

Deze cachemodus garandeert dat de meest recente bronnen worden gebruikt. De prestaties worden echter beïnvloed omdat de service Forms de in de cache opgeslagen items bij elke aanvraag valideert. Deze cachemodus is geschikt voor ontwikkelings- en staging-omgevingen waar bronnen regelmatig worden bijgewerkt en prestaties geen primair probleem zijn.

**Onvoorwaardelijke caching opgeven**

1. Klik in de beheerconsole op Services > Forms.
1. Selecteer Onvoorwaardelijk onder Instellingen voor Cachebeheer voor formulieren en klik op Opslaan.

### Het controlepunt voor de cache gebruiken {#use-the-cache-check-point}

In deze modus controleert de service Forms alleen de opslagplaats op nieuwere versies van bronnen wanneer de tijdstempel van de resource in de cache ouder is dan de tijd van het controlepunt voor de cache. De laatste tijd van het punt van de geheim voorgeheugencontrole wordt getoond op de pagina van Vormen in de Console van het Beleid.

Gebruik deze cachemodus in productieomgevingen met hoge prestaties waar de prestaties van belang zijn en wijzigingen in bronnen niet vaak voorkomen. U kunt de tijd van het punt van de geheim voorgeheugencontrole terugstellen wanneer u om het even welke veranderingen wilt opstellen die aan de bewaarplaatsmiddelen worden aangebracht.

**Het gebruik van een cachecontrolepunt opgeven**

1. Klik in Beheerconsole op Services > Formulieren.
1. Selecteer onder Instellingen voor Cachebeheer voor formulieren de optie Alleen als de laatste validatie is uitgevoerd vóór de tijd van het controlepunt voor de cache en klik op Opslaan.

**Het controlepunt voor de cache opnieuw instellen**

1. Klik in de beheerconsole op Services > Forms.
1. Klik onder Instellingen van Cachebeheer voor formulieren op Cachecontrolepunt.

**De inhoud van de cache opnieuw instellen**

U kunt de inhoud van de cache op elk gewenst moment wissen. Nadat de cache opnieuw is ingesteld, wordt de eerste aanvraag voor elk formulier langzamer omdat de Forms-service een volledige rendering uitvoert en nieuwe cacheinhoud maakt.

1. Klik in de beheerconsole op Services > Forms.
1. Klik onder Instellingen van Cachebeheer voor formulieren op Cache opnieuw instellen.

## Cacheinstellingen configureren {#configuring-cache-settings}

U kunt instellingen opgeven die door Forms worden gebruikt voor het in cache plaatsen, waardoor de prestaties van uw AEM-formulieromgeving kunnen worden geoptimaliseerd.

Klik in de beheerconsole op Services > Formulieren om deze instellingen te openen.

>[!NOTE]
>
>De schijfvereisten voor de cache moeten gelijk zijn aan die van de opslagplaats.

### Algemene cache-instellingen opgeven {#specifying-global-cache-settings}

De instellingen in het gebied **Algemene cacheinstellingen** zijn van toepassing op alle typen caches. Als u een van deze instellingen wijzigt, start u de service Forms opnieuw om de wijziging door te voeren. Als u deze service opnieuw wilt starten, gebruikt u Workbench of raadpleegt u de services die aan de AEM-formuliermodules [](/help/forms/using/admin-help/starting-stopping-services.md#start-or-stop-the-services-associated-with-aem-forms-modules) zijn gekoppeld, starten of stoppen voor instructies.

**** Max. documentgrootte cache (kB): De maximale grootte, in kilobytes, van een formulierontwerp of andere bron die in een cache in het geheugen kan worden opgeslagen. Dit is een algemene instelling die van toepassing is op alle cache in het geheugen. Als een bron groter is dan deze waarde, wordt deze niet in het geheugen opgeslagen. De standaardwaarde is 1024 kilobytes. Deze instelling heeft geen invloed op de cache van de schijf.

**** Cache voor het renderen van formulieren ingeschakeld: Deze optie is standaard ingeschakeld, wat betekent dat weergegeven formulieren in de cache worden geplaatst voor volgende opvraging. Deze instelling verbetert de prestaties omdat de service Forms slechts één keer een bepaald formulier hoeft te genereren en vervolgens de versie in de cache gebruikt. Deze optie werkt met de eigenschap voor het in cache plaatsen van het formulierontwerp. Zie Help bij Designer voor informatie over het configureren van deze waarde in het formulierontwerp.

### Formulierontwerpen in cache plaatsen {#caching-form-designs}

Wanneer de Forms-service een renderaanvraag ontvangt, haalt deze het formulierontwerp op uit de opslagplaats en plaatst deze het in cache. Dit in cache plaatsen verbetert de prestaties, omdat bij volgende renderaanvragen het formulierontwerp door de Forms-service wordt opgehaald uit de cache in plaats van uit de opslagplaats.

Met de service Forms worden formulierontwerpen altijd in cache opgeslagen. Als formulierontwerpen worden opgeslagen op de server, worden deze bestanden beschouwd als de schijfcache. Met de service Forms worden formulierontwerpen ook in het geheugen opgeslagen, afhankelijk van de instelling in het gedeelte **Sjablooncache** van In-geheugen. Als u een van deze instellingen wijzigt, start u de service Forms opnieuw om de wijziging door te voeren. Als u deze service opnieuw wilt starten, gebruikt u Workbench of raadpleegt u de services die aan de AEM-formuliermodules [](/help/forms/using/admin-help/starting-stopping-services.md#start-or-stop-the-services-associated-with-aem-forms-modules) zijn gekoppeld, starten of stoppen voor instructies.

**** Cachegrootte sjabloonconfiguratie: Het maximumaantal voorwerpen van de malplaatjeconfiguratie in geheugen te houden. De standaardwaarde is 100. U wordt aangeraden deze waarde groter dan of gelijk aan de waarde voor Grootte sjablooncache in te stellen. Deze instelling heeft geen invloed op de cache van de schijf.

**** Grootte sjablooncache: Het maximumaantal sjablooninhoudsobjecten dat in het geheugen moet worden bewaard. De standaardwaarde is 100. Deze instelling heeft geen invloed op de cache van de schijf.

**** Ingeschakeld: Dit selectievakje is standaard ingeschakeld, wat betekent dat formuliersjablonen in het geheugen worden opgeslagen. Als deze optie niet is geselecteerd, worden formuliersjablonen alleen op de schijf in het cachegeheugen opgeslagen.

### Gerenderde formulieren in cache plaatsen {#caching-rendered-forms}

De Forms-service plaatst gegenereerde formulieren in cache, zodat deze niet hetzelfde formulier hoeven op te lossen en weer te geven in volgende aanvragen. Gegenereerde formulieren worden zowel op de schijf als in het geheugen in cache geplaatst.

Deze instellingen bevinden zich in het gebied Rendercache **van** ingeheugenformulier. Als u een van deze instellingen wijzigt, start u de service Forms opnieuw om de wijziging door te voeren. Als u deze service opnieuw wilt starten, gebruikt u Workbench of raadpleegt u de services die aan de AEM-formuliermodules [](/help/forms/using/admin-help/starting-stopping-services.md#start-or-stop-the-services-associated-with-aem-forms-modules) zijn gekoppeld, starten of stoppen voor instructies.

**** Cachegrootte: Hiermee geeft u het maximum aantal weergegeven formulieren op dat in de cache in het geheugen kan worden opgeslagen. De standaardwaarde is 100. Deze instelling heeft geen invloed op de cache van de schijf.

**** Ingeschakeld: Deze optie is standaard geselecteerd, wat betekent dat gerenderde formulieren in het geheugen worden opgeslagen. Als deze optie niet is geselecteerd, worden de weergegeven formulieren alleen op de schijf in het cachegeheugen opgeslagen.

### Fragmenten en afbeeldingen in cache plaatsen {#caching-fragments-and-images}

De service Forms plaatst fragmenten en afbeeldingen die in formulierontwerpen op schijf worden gebruikt in cache. Dit verbetert de prestaties, omdat de fragmenten en afbeeldingen alleen worden gelezen van de opslagplaats op het eerste verzoek. Vervolgens leest de service Forms fragmenten en afbeeldingen uit de cache van de schijf op volgende aanvragen. Fragmenten en afbeeldingen worden alleen op de schijf in het cachegeheugen opgeslagen en niet in het geheugen.

Met de volgende instellingen kunt u het in cache plaatsen op schijf van fragmenten en afbeeldingen beheren. Deze instellingen bevinden zich in het gebied Instellingen voor **cache van** sjabloonbron:

**In cache plaatsen** van bronnen Selecteer een van de volgende opties in de lijst:

**** Ingeschakeld voor fragmenten en afbeeldingen: De service Forms plaatst fragmenten en afbeeldingen in het cachegeheugen. Dit is de standaardoptie.

**** Ingeschakeld voor fragmenten: De service Forms plaatst fragmenten in cache, maar geen afbeeldingen.

**** Uitgeschakeld: De service Forms slaat fragmenten of afbeeldingen niet in het cachegeheugen op.

**** Overbodig verwijderen (seconden): Hiermee geeft u op hoe vaak de service Forms oude ongeldige cachebestanden verwijdert. De service Forms verwijdert geen geldige cachebestanden. Als u het opschooninterval wijzigt, start u de service Forms opnieuw om de wijziging door te voeren. Als u deze service opnieuw wilt starten, gebruikt u Workbench of raadpleegt u De services die aan AEM-formuliermodules zijn gekoppeld voor instructies starten of stoppen. De standaardwaarde is 600 seconden.

## Groeperingsoverwegingen voor caches {#clustering-considerations-for-caches}

In een gegroepeerde omgeving, handhaaft elke knoop zijn eigen in-geheugen en schijfgeheime voorgeheugen. De inhoud van de cache op elk knooppunt hangt af van de formulieren die op dat knooppunt zijn gegenereerd.

De locatie van de cache moet identiek zijn (dezelfde schijf en hetzelfde pad) op elk knooppunt van de cluster. Plaats de cache niet op gedeelde opslag.

Als u de pagina Formulieren in de beheerconsole gebruikt om de cache-instellingen voor een bepaald knooppunt te wijzigen, worden de cache-instellingen voor andere knooppunten bijgewerkt wanneer een aanvraag naar dat knooppunt gaat. Dit gedrag is ook van toepassing op de knoop van het Geheime voorgeheugen van het Terugstellen. Als u op de knop Cache opnieuw instellen voor één knooppunt klikt, wordt de cache onmiddellijk uit dat knooppunt verwijderd. Het geheime voorgeheugen op andere knopen wordt ontruimd wanneer een verzoek naar dat knoop gaat.
