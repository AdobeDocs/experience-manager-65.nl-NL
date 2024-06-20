---
title: Caching configureren voor Output
description: De uitvoerservice plaatst de formulierontwerpen, fragmenten en afbeeldingen in cache. Leer hoe te om caching voor output te vormen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 1015f5c9-6ab8-4656-a5c8-40f82b9938b9
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: e821be5233fd5f6688507096790d219d25903892
workflow-type: tm+mt
source-wordcount: '1442'
ht-degree: 0%

---

# Caching configureren voor Output  {#configuring-caching-for-output}

De Output-service voegt XML-formuliergegevens samen met een formulierontwerp dat in Designer is gemaakt om een uitvoerstroom van een document in verschillende indelingen te maken.

De pagina van de Output in beleidsconsole bevat montages die de manier controleren de de dienstgeheime voorgeheugens van de Output punten. U kunt deze instellingen aanpassen om de prestaties van de uitvoerservice te optimaliseren.

De service Uitvoer plaatst de volgende items in cache:

* **formulierontwerpen:** De Output-service plaatst formulierontwerpen in cache die worden opgehaald uit de gegevensopslagruimte of HTTP-bronnen. Dit in cache plaatsen verbetert de prestaties, omdat bij volgende renderaanvragen het formulierontwerp door de Output-service wordt opgehaald uit de cache in plaats van uit de gegevensopslagruimte.
* **fragmenten en afbeeldingen:** De service Uitvoer kan fragmenten en afbeeldingen die worden gebruikt in formulierontwerpen in cache plaatsen. Wanneer deze objecten in cache worden geplaatst door de uitvoerservice, worden de prestaties verbeterd omdat de fragmenten en afbeeldingen alleen worden gelezen uit de opslagplaats op de eerste aanvraag.

Output slaat het cachegeheugen op twee locaties op:

* **in het geheugen:** Items worden in het geheugen opgeslagen zodat ze snel kunnen worden geopend. De cache in het geheugen heeft een beperkte grootte en wordt verwijderd wanneer u de server opnieuw start.
* **op schijf:** Items worden opgeslagen in het bestandssysteem van de server. De schijfcache heeft een grotere capaciteit dan de cache in het geheugen en deze blijft behouden wanneer u de server opnieuw start. De locatie van de schijfcache is afhankelijk van de toepassingsserver. Voor informatie over het wijzigen van de locatie van de schijfcache raadpleegt u [Bestandslocaties voor uitvoer opgeven](/help/forms/using/admin-help/specify-file-locations-output.md#specify-file-locations-for-output).

## De cachemodus opgeven {#specifying-the-cache-mode}

Output ondersteunt twee modi voor caching:

* onvoorwaardelijk
* het gebruiken van het punt van de geheim voorgeheugencontrole

Als u tussen cachemodi schakelt, start u de uitvoerservice opnieuw om de wijziging van kracht te laten worden. Als u deze service opnieuw wilt starten, gebruikt u Workbench of raadpleegt u [De diensten verbonden aan AEM vormmodules beginnen of tegenhouden](/help/forms/using/admin-help/starting-stopping-services.md#start-or-stop-the-services-associated-with-aem-forms-modules) voor instructies.

De tijd van het punt van de geheim voorgeheugencontrole wordt automatisch teruggesteld wanneer u tussen wijzen schakelt.

### Onvoorwaardelijke caching gebruiken {#using-unconditional-caching}

In deze modus worden de vereiste bronnen (formulierontwerp en gerelateerde elementen zoals fragmenten en afbeeldingen) gevalideerd wanneer de Output-service een aanvraag ontvangt. De Output-service vergelijkt de tijdstempel van de bronnen in de opslagplaats met de tijdstempel van de bronnen in de cache. Als het middel in het geheime voorgeheugen ouder is, werkt de dienst van de Output het bij.

Deze cachemodus garandeert dat de meest recente bronnen worden gebruikt. De prestaties worden echter beïnvloed omdat de Output-service de in de cache opgeslagen items bij elke aanvraag valideert tegen de repository. Deze cachemodus is geschikt voor ontwikkelings- en staging-omgevingen waar bronnen regelmatig worden bijgewerkt en prestaties geen primair probleem zijn.

**Onvoorwaardelijke caching opgeven**

1. Klik in de beheerconsole op Services > Uitvoer.
1. Selecteer Onvoorwaardelijk onder Instellingen voor Cachebeheer uitvoeren en klik op Opslaan.

### Het controlepunt voor de cache gebruiken {#use-the-cache-check-point}

Op deze wijze, controleert de dienst van de Output slechts de bewaarplaats op nieuwere versies van middelen wanneer timestamp van het caching middel ouder is dan de tijd van het geheim voorgeheugencontrolepunt. De laatste tijd van het punt van de geheim voorgeheugencontrole wordt getoond op de pagina van de Output in de Console van het Beleid.

Gebruik deze cachemodus in productieomgevingen met hoge prestaties waar de prestaties van belang zijn en wijzigingen in bronnen niet vaak voorkomen. U kunt de tijd van het punt van de geheim voorgeheugencontrole terugstellen wanneer u om het even welke veranderingen wilt opstellen die aan de bewaarplaatsmiddelen worden aangebracht.

**Het gebruik van een cachecontrolepunt opgeven**

1. Klik in Beheerconsole op Services > Uitvoer.
1. Selecteer onder Instellingen voor Cachebeheer voor uitvoer de optie Alleen als de laatste validatie is uitgevoerd vóór de tijd van het controlepunt voor de cache en klik op Opslaan.

**Het controlepunt voor de cache opnieuw instellen**

1. Klik in de beheerconsole op Services > Uitvoer.
1. Klik onder Instellingen voor Cachebeheer op Cachecontrolepunt.

### De inhoud van de cache opnieuw instellen {#reset-the-cache-contents}

U kunt de inhoud van de cache op elk gewenst moment wissen. Na het opnieuw instellen van de cache wordt de eerste aanvraag voor elk formulier langzamer, omdat de Output-service een volledige rendering uitvoert en nieuwe cacheinhoud maakt.

1. Klik in de beheerconsole op Services > Uitvoer.
1. Klik onder Instellingen voor beheer van uitvoercache op Cache opnieuw instellen.

## Cacheinstellingen configureren {#configuring-cache-settings}

U kunt instellingen opgeven die Output gebruikt voor caching, zodat de prestaties van de omgeving van uw AEM formulieren worden geoptimaliseerd.

Klik in de beheerconsole op Services > Uitvoer om deze instellingen te openen.

>[!NOTE]
>
>De schijfvereisten voor de cache moeten gelijk zijn aan die van de opslagplaats.

### Algemene cache-instellingen opgeven {#specifying-global-cache-settings}

De instellingen in het dialoogvenster **Algemene cache-instellingen** heeft invloed op alle typen caches. Als u een van deze instellingen wijzigt, start u de service Uitvoer opnieuw om de wijziging van kracht te laten worden. Als u deze service opnieuw wilt starten, gebruikt u Workbench of raadpleegt u [De diensten verbonden aan AEM vormmodules beginnen of tegenhouden](/help/forms/using/admin-help/starting-stopping-services.md#start-or-stop-the-services-associated-with-aem-forms-modules) voor instructies.

**Max. documentgrootte cache (kB):** De maximale grootte, in kilobytes, van een formulierontwerp of andere bron die in een cache in het geheugen kan worden opgeslagen. Dit is een algemene instelling die van toepassing is op alle cache in het geheugen. Als de bron groter is dan deze waarde, wordt deze niet in het geheugen opgeslagen. De standaardwaarde is 1024 kilobytes. Deze instelling heeft geen invloed op de cache van de schijf.

**Cache voor het renderen van formulieren ingeschakeld:** Deze optie is standaard ingeschakeld, wat betekent dat weergegeven formulieren in de cache worden geplaatst om ze later op te halen. Deze instelling heeft weinig effect op de prestaties van de uitvoerservice omdat niet-interactieve documenten niet in de cache worden opgeslagen. Deze optie heeft geen effect wanneer u de uitvoerservice gebruikt voor niet-interactieve documenten die op de client worden gerenderd.

### Formulierontwerpen in cache plaatsen {#caching-form-designs}

Wanneer de Output-service een renderaanvraag ontvangt, haalt deze het formulierontwerp op uit de gegevensopslagruimte of uit een HTTP-bron en plaatst deze in cache. Dit in cache plaatsen verbetert de prestaties, omdat bij volgende renderaanvragen het formulierontwerp door de Output-service wordt opgehaald uit de cache in plaats van uit de gegevensopslagruimte.

De Output-service plaatst formulierontwerpen altijd in cache op schijf. Als formulierontwerpen worden opgeslagen op de server, worden deze bestanden beschouwd als de schijfcache. De Output-service plaatst ook formulierontwerpen in het geheugen in de cache volgens de instelling in het dialoogvenster **In Geheugensjablooncache** gebied. Als u een van deze instellingen wijzigt, start u de service Uitvoer opnieuw om de wijziging in werking te laten treden. Als u deze service opnieuw wilt starten, gebruikt u Workbench of raadpleegt u [De diensten verbonden aan AEM vormmodules beginnen of tegenhouden](/help/forms/using/admin-help/starting-stopping-services.md#start-or-stop-the-services-associated-with-aem-forms-modules) voor instructies.

**Grootte sjabloonconfiguratiecache:** Het maximumaantal voorwerpen van de malplaatjeconfiguratie in geheugen te houden. De standaardwaarde is 100. U wordt aangeraden deze waarde groter dan of gelijk aan de waarde voor Grootte sjablooncache in te stellen. Deze instelling heeft geen invloed op de cache van de schijf.

**Grootte sjablooncache:** Het maximumaantal sjablooninhoudsobjecten dat in het geheugen moet worden bewaard. De standaardwaarde is 100. Deze instelling heeft geen invloed op de cache van de schijf.

**Ingeschakeld:** Dit selectievakje is standaard ingeschakeld, wat betekent dat formuliersjablonen in het geheugen worden opgeslagen. Als deze optie niet is geselecteerd, worden formuliersjablonen alleen op de schijf in het cachegeheugen opgeslagen.

### Fragmenten en afbeeldingen in cache plaatsen {#caching-fragments-and-images}

De uitvoerservice plaatst fragmenten en afbeeldingen die in formulierontwerpen op schijf worden gebruikt in cache. Dit verbetert de prestaties, omdat de fragmenten en afbeeldingen alleen worden gelezen van de opslagplaats op het eerste verzoek. Vervolgens leest de uitvoerservice op volgende verzoeken fragmenten en afbeeldingen uit de cache van de schijf. Fragmenten en afbeeldingen worden alleen op de schijf in het cachegeheugen opgeslagen en niet in het geheugen.

Met de volgende instellingen kunt u het in cache plaatsen op schijf van fragmenten en afbeeldingen beheren. Deze instellingen bevinden zich in het gedeelte **Instellingen voor sjabloonbroncache** gebied:

**Resource Caching** Selecteer een van de volgende opties in de lijst:

**Ingeschakeld voor fragmenten en afbeeldingen:** De uitvoerservice plaatst fragmenten en afbeeldingen in cache. Dit is de standaardoptie.

**Ingeschakeld voor fragmenten:** De uitvoerservice plaatst fragmenten in cache, maar geen afbeeldingen.

**Uitgeschakeld:** De service Uitvoer slaat geen fragmenten of afbeeldingen in de cache op.

**Overbodig verwijderen (seconden):** Hiermee geeft u op hoe vaak de service Uitvoer oude ongeldige cachebestanden verwijdert. De service Uitvoer verwijdert geen geldige cachebestanden. Als u het opschoningsinterval wijzigt, start u de service Uitvoer opnieuw om de wijziging in werking te laten treden. Als u deze service opnieuw wilt starten, gebruikt u Workbench of raadpleegt u De services die zijn gekoppeld aan AEM formuliermodules starten of stoppen voor instructies.

## Groeperingsoverwegingen voor caches {#clustering-considerations-for-caches}

In een gegroepeerde omgeving, handhaaft elke knoop zijn eigen in-geheugen en schijfgeheime voorgeheugen. De inhoud van de cache op elk knooppunt hangt af van de formulieren die op dat knooppunt zijn gegenereerd.

De locatie van de cache moet identiek zijn (dezelfde schijf en hetzelfde pad) op elk knooppunt van de cluster. Plaats de cache niet op gedeelde opslag.

Als u de pagina van de Output in beleidsconsole gebruikt om de geheim voorgeheugenmontages voor een bepaalde knoop te veranderen, worden de geheim voorgeheugenmontages op andere knopen bijgewerkt wanneer een verzoek naar die knoop gaat. Dit gedrag is ook van toepassing op de knoop van het Geheime voorgeheugen van het Terugstellen. Als u op de knop Cache opnieuw instellen voor één knooppunt klikt, wordt de cache onmiddellijk uit dat knooppunt verwijderd. Het geheime voorgeheugen op andere knopen wordt ontruimd wanneer een verzoek naar dat knoop gaat.
