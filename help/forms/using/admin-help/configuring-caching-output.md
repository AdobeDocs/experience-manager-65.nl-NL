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
source-git-commit: 6a9806d8f40f711a610c130c63d9ab9b2460d075
workflow-type: tm+mt
source-wordcount: '1454'
ht-degree: 0%

---

# Caching configureren voor Output  {#configuring-caching-for-output}

>[!NOTE]
> 
> Zorg ervoor dat de gebruiker beheerdersrechten heeft om toegang te krijgen tot de beheerdersconsole.

De Output-service voegt XML-formuliergegevens samen met een formulierontwerp dat in Designer is gemaakt om een uitvoerstroom van een document in verschillende indelingen te maken.

De pagina van de Output in beleidsconsole bevat montages die de manier controleren de de dienstgeheime voorgeheugens van de Output punten. U kunt deze instellingen aanpassen om de prestaties van de uitvoerservice te optimaliseren.

De service Uitvoer plaatst de volgende items in cache:

* **vormontwerpen:** de dienstgeheime voorgeheugens van de Output de vormontwerpen die het van de bewaarplaats of van de bronnen van HTTP terugwint. Dit in cache plaatsen verbetert de prestaties, omdat bij volgende renderaanvragen het formulierontwerp door de Output-service wordt opgehaald uit de cache in plaats van uit de gegevensopslagruimte.
* **fragmenten en beelden:** de dienst van de Output kan fragmenten en beelden caching die in vormontwerpen worden gebruikt. Wanneer deze objecten in cache worden geplaatst door de uitvoerservice, worden de prestaties verbeterd omdat de fragmenten en afbeeldingen alleen worden gelezen uit de opslagplaats op de eerste aanvraag.

Output slaat het cachegeheugen op twee locaties op:

* **in geheugen:** de Punten worden opgeslagen in geheugen voor snelle toegang. De cache in het geheugen heeft een beperkte grootte en wordt verwijderd wanneer u de server opnieuw start.
* **op schijf:** de Punten worden opgeslagen in het het dossiersysteem van de server. De schijfcache heeft een grotere capaciteit dan de cache in het geheugen en deze blijft behouden wanneer u de server opnieuw start. De locatie van de schijfcache is afhankelijk van de toepassingsserver. Voor informatie bij het veranderen van de plaats van het schijfgeheime voorgeheugen, zie [ dossierplaatsen voor Output ](/help/forms/using/admin-help/specify-file-locations-output.md#specify-file-locations-for-output) specificeren.

## De cachemodus opgeven {#specifying-the-cache-mode}

Output ondersteunt twee modi voor caching:

* onvoorwaardelijk
* het gebruiken van het punt van de geheim voorgeheugencontrole

Als u tussen cachemodi schakelt, start u de uitvoerservice opnieuw om de wijziging van kracht te laten worden. Om deze dienst opnieuw te beginnen, of gebruik Workbench of zie [ Begin of stop de diensten verbonden aan AEM vormmodules ](/help/forms/using/admin-help/starting-stopping-services.md#start-or-stop-the-services-associated-with-aem-forms-modules) voor instructies.

De tijd van het punt van de geheim voorgeheugencontrole wordt automatisch teruggesteld wanneer u tussen wijzen schakelt.

### Onvoorwaardelijke caching gebruiken {#using-unconditional-caching}

In deze modus worden de vereiste bronnen (formulierontwerp en gerelateerde elementen zoals fragmenten en afbeeldingen) gevalideerd wanneer de Output-service een aanvraag ontvangt. De Output-service vergelijkt de tijdstempel van de bronnen in de opslagplaats met de tijdstempel van de bronnen in de cache. Als het middel in het geheime voorgeheugen ouder is, werkt de dienst van de Output het bij.

Deze cachemodus garandeert dat de meest recente bronnen worden gebruikt. De prestaties worden echter beïnvloed omdat de Output-service de in de cache opgeslagen items bij elke aanvraag valideert tegen de repository. Deze cachemodus is geschikt voor ontwikkelings- en staging-omgevingen waar bronnen regelmatig worden bijgewerkt en prestaties geen primair probleem zijn.

**specificeer onvoorwaardelijk caching**

1. Klik in de beheerconsole op Services > Uitvoer.
1. Selecteer Onvoorwaardelijk onder Instellingen voor Cachebeheer uitvoeren en klik op Opslaan.

### Het controlepunt voor de cache gebruiken {#use-the-cache-check-point}

Op deze wijze, controleert de dienst van de Output slechts de bewaarplaats op nieuwere versies van middelen wanneer timestamp van het caching middel ouder is dan de tijd van het geheim voorgeheugencontrolepunt. De laatste tijd van het punt van de geheim voorgeheugencontrole wordt getoond op de pagina van de Output in de Console van het Beleid.

Gebruik deze cachemodus in productieomgevingen met hoge prestaties waar de prestaties van belang zijn en wijzigingen in bronnen niet vaak voorkomen. U kunt de tijd van het punt van de geheim voorgeheugencontrole terugstellen wanneer u om het even welke veranderingen wilt opstellen die aan de bewaarplaatsmiddelen worden aangebracht.

**specificeer het gebruik van een punt van de geheim voorgeheugencontrole**

1. Klik in Beheerconsole op Services > Uitvoer.
1. Selecteer onder Instellingen voor Cachebeheer voor uitvoer de optie Alleen als de laatste validatie is uitgevoerd vóór de tijd van het controlepunt voor de cache en klik op Opslaan.

**terugstellen het punt van de geheim voorgeheugencontrole**

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

De montages in het **Globale gebied van de Montages van het Geheime voorgeheugen** beïnvloeden alle soorten geheime voorgeheugens. Als u een van deze instellingen wijzigt, start u de service Uitvoer opnieuw om de wijziging van kracht te laten worden. Om deze dienst opnieuw te beginnen, of gebruik Workbench of zie [ Begin of stop de diensten verbonden aan AEM vormmodules ](/help/forms/using/admin-help/starting-stopping-services.md#start-or-stop-the-services-associated-with-aem-forms-modules) voor instructies.

**Max de Grootte van het Document van het Geheime voorgeheugen (KB):** de maximumgrootte, in kilobytes, van een vormontwerp of ander middel dat in om het even welk in-geheugengeheime voorgeheugen kan worden opgeslagen. Dit is een algemene instelling die van toepassing is op alle cache in het geheugen. Als de bron groter is dan deze waarde, wordt deze niet in het geheugen opgeslagen. De standaardwaarde is 1024 kilobytes. Deze instelling heeft geen invloed op de cache van de schijf.

**Toegelaten het Teruggeven van het Geheime voorgeheugen van de Vorm:** Door gebrek, wordt deze optie geselecteerd, zo betekent het dat de teruggegeven vormen voor verdere herwinning in het voorgeheugen ondergebracht zijn. Deze instelling heeft weinig effect op de prestaties van de uitvoerservice omdat niet-interactieve documenten niet in de cache worden opgeslagen. Deze optie heeft geen effect wanneer u de uitvoerservice gebruikt voor niet-interactieve documenten die op de client worden gerenderd.

### Formulierontwerpen in cache plaatsen {#caching-form-designs}

Wanneer de Output-service een renderaanvraag ontvangt, haalt deze het formulierontwerp op uit de gegevensopslagruimte of uit een HTTP-bron en plaatst deze in cache. Dit in cache plaatsen verbetert de prestaties, omdat bij volgende renderaanvragen het formulierontwerp door de Output-service wordt opgehaald uit de cache in plaats van uit de gegevensopslagruimte.

De Output-service plaatst formulierontwerpen altijd in cache op schijf. Als formulierontwerpen worden opgeslagen op de server, worden deze bestanden beschouwd als de schijfcache. De dienst van de Output geheime voorgeheugens ook vormontwerpen in geheugen, volgens het plaatsen in het **Geheime voorgeheugen** gebied van het Geheime voorgeheugen. Als u een van deze instellingen wijzigt, start u de service Uitvoer opnieuw om de wijziging in werking te laten treden. Om deze dienst opnieuw te beginnen, of gebruik Workbench of zie [ Begin of stop de diensten verbonden aan AEM vormmodules ](/help/forms/using/admin-help/starting-stopping-services.md#start-or-stop-the-services-associated-with-aem-forms-modules) voor instructies.

**Grootte van het Geheime voorgeheugen van de Configuratie van het Malplaatje:** het maximumaantal voorwerpen van de malplaatjeconfiguratie in geheugen te houden. De standaardwaarde is 100. U wordt aangeraden deze waarde groter dan of gelijk aan de waarde voor Grootte sjablooncache in te stellen. Deze instelling heeft geen invloed op de cache van de schijf.

**Grootte van het Geheime voorgeheugen van het Malplaatje:** het maximumaantal voorwerpen van de malplaatjeinhoud in geheugen te houden. De standaardwaarde is 100. Deze instelling heeft geen invloed op de cache van de schijf.

**Toegelaten:** door gebrek, wordt dit controlevakje geselecteerd, betekenend dat de vormmalplaatjes in geheugen in het voorgeheugen in het voorgeheugen worden voorgebracht. Als deze optie niet is geselecteerd, worden formuliersjablonen alleen op de schijf in het cachegeheugen opgeslagen.

### Fragmenten en afbeeldingen in cache plaatsen {#caching-fragments-and-images}

De uitvoerservice plaatst fragmenten en afbeeldingen die in formulierontwerpen op schijf worden gebruikt in cache. Dit verbetert de prestaties, omdat de fragmenten en afbeeldingen alleen worden gelezen van de opslagplaats op het eerste verzoek. Vervolgens leest de uitvoerservice op volgende verzoeken fragmenten en afbeeldingen uit de cache van de schijf. Fragmenten en afbeeldingen worden alleen op de schijf in het cachegeheugen opgeslagen en niet in het geheugen.

Met de volgende instellingen kunt u het in cache plaatsen op schijf van fragmenten en afbeeldingen beheren. Deze montages zijn in het **gebied van de Montages van het Geheime voorgeheugen van het Malplaatje**:

**Middel Caching** selecteer één van de volgende opties van de lijst:

**Toegelaten voor fragmenten en beelden:** de de dienstgeheime voorgeheugens van de Output fragmenten en beelden. Dit is de standaardoptie.

**Toegelaten voor fragmenten:** de de dienstgeheime voorgeheugens van de Output fragmenten, maar geen beelden.

**Gehandicapten:** de dienst van de Output bewaart geen fragmenten of beelden.

**Interval van de Overboeking (Seconden):** specificeert hoe vaak de dienst van de Output oude ongeldige geheim voorgeheugendossiers verwijdert. De service Uitvoer verwijdert geen geldige cachebestanden. Als u het opschoningsinterval wijzigt, start u de service Uitvoer opnieuw om de wijziging in werking te laten treden. Als u deze service opnieuw wilt starten, gebruikt u Workbench of raadpleegt u De services die zijn gekoppeld aan AEM formuliermodules starten of stoppen voor instructies.

## Groeperingsoverwegingen voor caches {#clustering-considerations-for-caches}

In een gegroepeerde omgeving, handhaaft elke knoop zijn eigen in-geheugen en schijfgeheime voorgeheugen. De inhoud van de cache op elk knooppunt hangt af van de formulieren die op dat knooppunt zijn gegenereerd.

De locatie van de cache moet identiek zijn (dezelfde schijf en hetzelfde pad) op elk knooppunt van de cluster. Plaats de cache niet op gedeelde opslag.

Als u de pagina van de Output in beleidsconsole gebruikt om de geheim voorgeheugenmontages voor een bepaalde knoop te veranderen, worden de geheim voorgeheugenmontages op andere knopen bijgewerkt wanneer een verzoek naar die knoop gaat. Dit gedrag is ook van toepassing op de knoop van het Geheime voorgeheugen van het Terugstellen. Als u op de knop Cache opnieuw instellen voor één knooppunt klikt, wordt de cache onmiddellijk uit dat knooppunt verwijderd. Het geheime voorgeheugen op andere knopen wordt ontruimd wanneer een verzoek naar dat knoop gaat.
