---
title: Caching configureren voor Forms
description: Leer hoe te om geheim voorgeheugenmontages te vormen en hoe te om overwegingen voor geheime voorgeheugens te groeperen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 6b57d00e-5ba0-41ee-8497-49ecfec5b9ed
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: e821be5233fd5f6688507096790d219d25903892
workflow-type: tm+mt
source-wordcount: '1611'
ht-degree: 0%

---

# Caching configureren voor Forms{#configuring-caching-for-forms}

De Forms-service bestaat uit formulierontwerpen die in Designer zijn gemaakt en in verschillende indelingen worden weergegeven.

De Forms-pagina in de beheerconsole bevat instellingen die bepalen hoe de Forms-service items in cache plaatst. U kunt deze instellingen aanpassen om de prestaties van de Forms-service te optimaliseren.

De Forms-service plaatst de volgende items in cache:

* **vormontwerpen:** de dienstgeheime voorgeheugens van Forms vormontwerpen die het van de bewaarplaats of van de bronnen van HTTP terugwint. Dit in cache plaatsen verbetert de prestaties, omdat de Forms-service het formulierontwerp ophaalt uit de cache in plaats van uit de opslagplaats.
* **fragmenten en beelden:** de dienst van Forms kan fragmenten en beelden caching die in vormontwerpen worden gebruikt. Wanneer de Forms-service deze objecten in cache plaatst, worden de prestaties verbeterd omdat de fragmenten en afbeeldingen alleen worden gelezen uit de opslagplaats op het eerste verzoek.
* **vormen:** de dienst van Forms geheime voorgeheugens de vormen die het teruggeeft. Dit type caching verbetert de prestaties omdat de Forms-service niet hetzelfde formulier hoeft op te lossen en weer te geven in volgende aanvragen.

Forms slaat de cache op twee plaatsen op:

* **in geheugen:** de Punten worden opgeslagen in geheugen voor snelle toegang. De cache in het geheugen heeft een beperkte grootte en wordt verwijderd wanneer u de server opnieuw start.
* **op schijf:** de Punten worden opgeslagen in het het dossiersysteem van de server. De schijfcache heeft een grotere capaciteit dan de cache in het geheugen en deze blijft behouden wanneer u de server opnieuw start. De locatie van de schijfcache is afhankelijk van de toepassingsserver. Voor informatie bij het veranderen van de plaats van het schijfgeheime voorgeheugen, zie [ het Vormen plaatsen voor Forms ](/help/forms/using/admin-help/configuring-locations-forms.md#configuring-locations-for-forms).

## De cachemodus opgeven {#specifying-the-cache-mode}

Forms biedt ondersteuning voor twee modi voor caching:

* onvoorwaardelijk
* het gebruiken van het punt van de geheim voorgeheugencontrole

Als u tussen cachemodi schakelt, start u de Forms-service opnieuw om de wijziging van kracht te laten worden. Om deze dienst opnieuw te beginnen, of gebruik Workbench of zie [ Begin of stop de diensten verbonden aan AEM vormmodules ](/help/forms/using/admin-help/starting-stopping-services.md#start-or-stop-the-services-associated-with-aem-forms-modules) voor instructies.

De tijd van het punt van de geheim voorgeheugencontrole wordt automatisch teruggesteld wanneer u tussen wijzen schakelt.

### Onvoorwaardelijke caching gebruiken {#using-unconditional-caching}

Wanneer de Forms-service in deze modus een aanvraag ontvangt, worden de vereiste bronnen (formulierontwerp en gerelateerde elementen zoals fragmenten en afbeeldingen) gevalideerd. De Forms-service vergelijkt de tijdstempel van de bronnen in de opslagplaats met de tijdstempel van de bronnen in de cache. Als de resource in de cache ouder is, wordt deze door de Forms-service bijgewerkt.

Deze cachemodus garandeert dat de meest recente bronnen worden gebruikt. De prestaties worden echter beïnvloed omdat de Forms-service de in de cache opgeslagen items bij elke aanvraag valideert tegen de repository. Deze cachemodus is geschikt voor ontwikkelings- en staging-omgevingen waar bronnen regelmatig worden bijgewerkt en prestaties geen primair probleem zijn.

**specificeer onvoorwaardelijk caching**

1. Klik in de beheerconsole op Services > Forms.
1. Selecteer Onvoorwaardelijk onder Forms Cache Control Settings en klik op Save.

### Het controlepunt voor de cache gebruiken {#use-the-cache-check-point}

In deze modus controleert de Forms-service alleen de opslagplaats op nieuwere versies van bronnen wanneer de tijdstempel van de resource in de cache ouder is dan de tijd van het controlepunt voor de cache. De laatste tijd van het punt van de geheim voorgeheugencontrole wordt getoond op de pagina van Forms in de Console van het Beleid.

Gebruik deze cachemodus in productieomgevingen met hoge prestaties waar de prestaties van belang zijn en wijzigingen in bronnen niet vaak voorkomen. U kunt de tijd van het punt van de geheim voorgeheugencontrole terugstellen wanneer u om het even welke veranderingen wilt opstellen die aan de bewaarplaatsmiddelen worden aangebracht.

**specificeer het gebruik van een punt van de geheim voorgeheugencontrole**

1. Klik in Beheerconsole op Services > Forms.
1. Selecteer onder Instellingen voor Cachebeheer van Forms de optie Alleen als de laatste validatie is uitgevoerd vóór de tijd van het controlepunt voor de cache en klik op Opslaan.

**terugstellen het punt van de geheim voorgeheugencontrole**

1. Klik in de beheerconsole op Services > Forms.
1. Klik onder Forms Cache Control Settings op Cache Check Point.

**terugstellen de geheim voorgeheugeninhoud**

U kunt de inhoud van de cache op elk gewenst moment wissen. Na het opnieuw instellen van de cache wordt de eerste aanvraag voor elk formulier langzamer, omdat de Forms-service een volledige rendering uitvoert en nieuwe cacheinhoud maakt.

1. Klik in de beheerconsole op Services > Forms.
1. Klik onder Forms Cache Control Settings op Reset Cache.

## Cacheinstellingen configureren {#configuring-cache-settings}

U kunt instellingen opgeven die Forms gebruikt voor het in cache plaatsen, zodat de prestaties van uw AEM-formulieromgeving optimaal zijn.

Klik in de beheerconsole op Services > Forms om deze instellingen te openen.

>[!NOTE]
>
>De schijfvereisten voor de cache moeten gelijk zijn aan die van de opslagplaats.

### Algemene cache-instellingen opgeven {#specifying-global-cache-settings}

De montages in het **Globale gebied van de Montages van het Geheime voorgeheugen** beïnvloeden alle soorten geheime voorgeheugens. Als u een van deze instellingen wijzigt, start u de Forms-service opnieuw, zodat de wijziging van kracht wordt. Om deze dienst opnieuw te beginnen, of gebruik Workbench of zie [ Begin of stop de diensten verbonden aan AEM vormmodules ](/help/forms/using/admin-help/starting-stopping-services.md#start-or-stop-the-services-associated-with-aem-forms-modules) voor instructies.

**Max de Grootte van het Document van het Geheime voorgeheugen (KB):** de maximumgrootte, in kilobytes, van een vormontwerp of ander middel dat in om het even welk in-geheugengeheime voorgeheugen kan worden opgeslagen. Dit is een algemene instelling die van toepassing is op alle cache in het geheugen. Als een bron groter is dan deze waarde, wordt deze niet in het geheugen opgeslagen. De standaardwaarde is 1024 kilobytes. Deze instelling heeft geen invloed op de cache van de schijf.

**Toegelaten het Teruggeven van het Geheime voorgeheugen van de Vorm:** Door gebrek, wordt deze optie geselecteerd, zo betekent het dat de teruggegeven vormen voor verdere herwinning in het voorgeheugen ondergebracht zijn. Deze instelling verbetert de prestaties omdat de Forms-service slechts één keer een bepaald formulier hoeft te genereren en vervolgens de versie in de cache gebruikt. Deze optie werkt met de eigenschap voor het in cache plaatsen van het formulierontwerp. Raadpleeg de Help van Designer voor informatie over het configureren van deze waarde in het formulierontwerp.

### Formulierontwerpen in cache plaatsen {#caching-form-designs}

Wanneer de Forms-service een renderaanvraag ontvangt, haalt deze het formulierontwerp op van de gegevensopslagruimte en plaatst deze het in cache. Dit in cache plaatsen verbetert de prestaties, omdat de Forms-service het formulierontwerp ophaalt uit de cache in plaats van uit de opslagplaats.

De Forms-service plaatst formulierontwerpen altijd in cache op schijf. Als formulierontwerpen worden opgeslagen op de server, worden deze bestanden beschouwd als de schijfcache. De dienst van Forms bewaart ook vormontwerpen in geheugen, volgens het plaatsen in **in het Geheime voorgeheugen van het Malplaatje van het Geheugen** gebied. Als u een van deze instellingen wijzigt, start u de Forms-service opnieuw, zodat de wijziging van kracht wordt. Om deze dienst opnieuw te beginnen, of gebruik Workbench of zie [ Begin of stop de diensten verbonden aan AEM vormmodules ](/help/forms/using/admin-help/starting-stopping-services.md#start-or-stop-the-services-associated-with-aem-forms-modules) voor instructies.

**Grootte van het Geheime voorgeheugen van de Configuratie van het Malplaatje:** het maximumaantal voorwerpen van de malplaatjeconfiguratie in geheugen te houden. De standaardwaarde is 100. U wordt aangeraden deze waarde groter dan of gelijk aan de waarde voor Grootte sjablooncache in te stellen. Deze instelling heeft geen invloed op de cache van de schijf.

**Grootte van het Geheime voorgeheugen van het Malplaatje:** het maximumaantal voorwerpen van de malplaatjeinhoud in geheugen te houden. De standaardwaarde is 100. Deze instelling heeft geen invloed op de cache van de schijf.

**Toegelaten:** door gebrek, wordt dit controlevakje geselecteerd, betekenend dat de vormmalplaatjes in geheugen in het voorgeheugen in het voorgeheugen worden voorgebracht. Als deze optie niet is geselecteerd, worden formuliersjablonen alleen op de schijf in het cachegeheugen opgeslagen.

### Gerenderde formulieren in cache plaatsen {#caching-rendered-forms}

De Forms-service plaatst gegenereerde formulieren in cache, zodat deze niet hetzelfde formulier hoeven op te lossen en weer te geven in volgende aanvragen. Gegenereerde formulieren worden zowel op de schijf als in het geheugen in cache geplaatst.

Deze montages zijn in het **In het Teruggeven van het Geheime voorgeheugen van de Vorm van het Geheugen** gebied. Als u een van deze instellingen wijzigt, start u de Forms-service opnieuw, zodat de wijziging van kracht wordt. Om deze dienst opnieuw te beginnen, of gebruik Workbench of zie [ Begin of stop de diensten verbonden aan AEM vormmodules ](/help/forms/using/admin-help/starting-stopping-services.md#start-or-stop-the-services-associated-with-aem-forms-modules) voor instructies.

**Grootte van het Geheime voorgeheugen:** specificeert het maximumaantal teruggegeven vormen die in het in-geheugengeheime voorgeheugen kunnen verblijven. De standaardwaarde is 100. Deze instelling heeft geen invloed op de cache van de schijf.

**Toegelaten:** door gebrek, wordt deze optie geselecteerd, betekenend dat de teruggegeven vormen in geheugen in het voorgeheugen in het voorgeheugen worden voorgezeten. Als deze optie niet is geselecteerd, worden de weergegeven formulieren alleen op de schijf in het cachegeheugen opgeslagen.

### Fragmenten en afbeeldingen in cache plaatsen {#caching-fragments-and-images}

De Forms-service plaatst fragmenten en afbeeldingen die in formulierontwerpen op schijf worden gebruikt in cache. Dit verbetert de prestaties, omdat de fragmenten en afbeeldingen alleen worden gelezen van de opslagplaats op het eerste verzoek. Vervolgens leest de Forms-service op volgende verzoeken fragmenten en afbeeldingen uit de cache van de schijf. Fragmenten en afbeeldingen worden alleen op de schijf in het cachegeheugen opgeslagen en niet in het geheugen.

Met de volgende instellingen kunt u het in cache plaatsen op schijf van fragmenten en afbeeldingen beheren. Deze montages zijn in het **gebied van de Montages van het Geheime voorgeheugen van het Malplaatje**:

**Middel Caching** selecteer één van de volgende opties van de lijst:

**Toegelaten voor fragmenten en beelden:** de de dienstgeheime voorgeheugens van Forms fragmenten en beelden. Dit is de standaardoptie.

**Toegelaten voor fragmenten:** de dienstgeheime voorgeheugens van Forms fragmenten, maar geen beelden.

**Gehandicapte:** de dienst van Forms bewaart geen fragmenten of beelden.

**Interval van de Overboeking (Seconden):** specificeert hoe vaak de dienst van Forms oude ongeldige geheim voorgeheugendossiers verwijdert. De Forms-service verwijdert geen geldige cachebestanden. Als u het opschooninterval wijzigt, start u de Forms-service opnieuw om de wijziging in werking te laten treden. Als u deze service opnieuw wilt starten, gebruikt u Workbench of raadpleegt u De services die zijn gekoppeld aan AEM formuliermodules starten of stoppen voor instructies. De standaardwaarde is 600 seconden.

## Groeperingsoverwegingen voor caches {#clustering-considerations-for-caches}

In een gegroepeerde omgeving, handhaaft elke knoop zijn eigen in-geheugen en schijfgeheime voorgeheugen. De inhoud van de cache op elk knooppunt hangt af van de formulieren die op dat knooppunt zijn gegenereerd.

De locatie van de cache moet identiek zijn (dezelfde schijf en hetzelfde pad) op elk knooppunt van de cluster. Plaats de cache niet op gedeelde opslag.

Als u de Forms-pagina in de beheerconsole gebruikt om de cache-instellingen voor een bepaald knooppunt te wijzigen, worden de cache-instellingen op andere knooppunten bijgewerkt wanneer een aanvraag naar dat knooppunt gaat. Dit gedrag is ook van toepassing op de knoop van het Geheime voorgeheugen van het Terugstellen. Als u op de knop Cache opnieuw instellen voor één knooppunt klikt, wordt de cache onmiddellijk uit dat knooppunt verwijderd. Het geheime voorgeheugen op andere knopen wordt ontruimd wanneer een verzoek naar dat knoop gaat.
