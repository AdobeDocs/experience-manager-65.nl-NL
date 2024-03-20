---
title: Modi uitvoeren
description: Leer hoe u uw AEM voor specifieke doeleinden kunt afstemmen met behulp van runmodi.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: configuring
content-type: reference
feature: Configuring
exl-id: 6d03cb1d-500e-4a23-80e5-347a43dff30e
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '746'
ht-degree: 0%

---

# Modi uitvoeren{#run-modes}

Met uitvoeringsmodi kunt u de AEM voor een bepaald doel instellen, bijvoorbeeld auteur of publicatie, test, ontwikkeling, intranet of andere.

U kunt:

* [Definieer verzamelingen van configuratieparameters voor elke uitvoeringsmodus](#defining-configuration-properties-for-a-run-mode).

  Een basisreeks configuratieparameters wordt toegepast voor alle looppaswijzen, kunt u extra reeksen aan het doel van uw specifiek milieu dan stemmen. Deze worden naar wens toegepast.

* [Aanvullende bundels definiëren die voor een bepaalde modus moeten worden geïnstalleerd](#defining-additional-bundles-to-be-installed-for-a-run-mode).

Alle instellingen en definities worden opgeslagen in de ene opslagplaats en geactiveerd door de instelling van de **Run-modus**.

## Installatie-uitvoeringsmodi {#installation-run-modes}

De (of vaste) loopwijzen van de installatie worden gebruikt op installatietijd en dan voor het volledige leven van de instantie bevestigd, kunnen zij niet worden veranderd.

De uitvoermodi voor de installatie zijn beschikbaar buiten de box:

* `author`
* `publish`
* `samplecontent`
* `nosamplecontent`

Dit zijn twee paren van elkaar uitsluitende looppaswijzen; bijvoorbeeld, kunt u:

* definiëren: `author` of `publish`, niet beide tegelijk

* combineren `author` met ofwel `samplecontent` of `nosamplecontent` (maar niet beide)

>[!CAUTION]
>
>Wanneer u een van de bovenstaande uitvoeringsmodi gebruikt (auteur, publicatie, samplinginhoud, geen samplinginhoud), definieert de waarde die tijdens de installatie wordt gebruikt de uitvoeringsmodus voor de *volledige levensduur* van die installatie.
>
>Voor deze uitvoeringsmodi *kan* wijzigen na installatie.

## Aangepaste uitvoermodi {#customized-run-modes}

U kunt ook uw eigen aangepaste uitvoermodi maken. Deze kunnen worden gecombineerd voor scenario&#39;s zoals:

* `author` + `development`

* `publish` + `test`

* `publish` + `test` + `golive`

* `publish` + `intranet`

* indien nodig. . .

De aangepaste looppaswijzen kunnen ook bij elk opstarten worden geselecteerd.

## Inhoud en geen samplinginhoud gebruiken {#using-samplecontent-and-nosamplecontent}

Met deze modi kunt u het gebruik van voorbeeldinhoud beheren. De voorbeeldinhoud wordt gedefinieerd voordat de quickstart wordt gemaakt en kan pakketten, configuraties, enzovoort bevatten:

* De `samplecontent` Deze inhoud wordt geïnstalleerd in de uitvoermodus (de standaardmodus).

* De `nosamplecontent` de voorbeeldinhoud wordt niet geïnstalleerd.

De run-modus voor noSampling-inhoud is ontworpen voor productie-installaties.

## Configuratieeigenschappen definiëren voor een uitvoermodus {#defining-configuration-properties-for-a-run-mode}

Een inzameling van waarden voor configuratieeigenschappen, die voor een bepaalde looppaswijze wordt gebruikt, kan in de bewaarplaats worden bewaard.

De uitvoeringsmodus wordt aangegeven met een achtervoegsel op de mapnaam. Hiermee kunt u alle configuraties als één opslagplaats opslaan. Bijvoorbeeld:

* `config`

  Van toepassing op alle runmodi

* `config.author`

  Wordt gebruikt voor de uitvoeringsmodus van de auteur

* `config.publish`

  Wordt gebruikt voor de publicatiemodus

* `config.<run-mode>`

  Gebruikt voor de toepasselijke looppaswijze; bijvoorbeeld config

Zie [OSGi-configuratie in de opslagplaats](/help/sites-deploying/configuring-osgi.md#osgi-configuration-in-the-repository) voor meer informatie over het bepalen van de individuele configuratieknooppunten binnen deze omslagen en voor het creëren van configuraties voor combinaties veelvoudige looppaswijzen.

>[!NOTE]
>
>Voor [Installatie-uitvoeringsmodi](#installation-run-modes) (bijvoorbeeld de auteur) de uitvoeringsmodus kan na de installatie niet meer worden gewijzigd. Wijzigingen in de afzonderlijke configuratie-eigenschappen worden echter van kracht na het opnieuw opstarten.

## Aanvullende bundels definiëren die moeten worden geïnstalleerd voor een uitvoeringsmodus {#defining-additional-bundles-to-be-installed-for-a-run-mode}

U kunt ook extra bundels opgeven die voor een bepaalde uitvoermodus moeten worden geïnstalleerd. Voor deze definities worden installatiemappen gebruikt om de bundels vast te houden. Ook hier wordt de uitvoeringsmodus aangegeven met een voorvoegsel:

* `install.author`
* `install.publish`

Deze mappen zijn van het type `nt:folder` en moet de juiste bundel bevatten.

## CQ starten met een specifieke uitvoeringsmodus {#starting-cq-with-a-specific-run-mode}

Als u configuraties voor veelvoudige looppaswijzen hebt bepaald dan moet u bepalen welke op opstarten moet worden gebruikt. Er zijn verschillende methoden om op te geven welke uitvoeringsmodus moet worden gebruikt. De volgorde van resolutie is:

1. [systeemeigenschappen (](#using-a-system-property-in-the-start-script)
1. [](#using-the-sling-properties-file)
1. [](#using-the-r-option)
1. [Bestandsnaamdetectie](#filename-detection-renaming-the-jar-file)

Wanneer u een toepassingsserver gebruikt, kunt u ook [de uitvoeringsmodus in web.xml definiëren](#defining-the-run-mode-in-web-xml-with-application-server).

### Het bestand sling.properties gebruiken {#using-the-sling-properties-file}

De `sling.properties` bestand kan worden gebruikt om de vereiste uitvoermodus te definiëren:

1. Bewerk het configuratiebestand:

   `<cq-installation-dir>/crx-quickstart/conf/sling.properties`

1. Voeg de volgende eigenschappen toe; het volgende voorbeeld is voor auteur:

   `sling.run.modes=author`

### De optie -r gebruiken {#using-the-r-option}

U kunt een aangepaste uitvoermodus activeren door de opdracht `-r` als u de snelstart start start. Gebruik bijvoorbeeld de volgende opdracht om een AEM instantie te starten met de uitvoermodus ingesteld op dev. &quot;

```shell
java -jar cq-56-p4545.jar -r dev
```

### Het gebruiken van een systeembezit in het beginmanuscript {#using-a-system-property-in-the-start-script}

Een systeemeigenschap in het beginscript kan worden gebruikt om de uitvoermodus op te geven.

* Gebruik bijvoorbeeld het volgende om een instantie te starten als een publicatie-instantie voor productie in de VS:

  `-Dsling.run.modes=publish,prod,us`

### Bestandsnaamdetectie - naam van jar-bestand wijzigen {#filename-detection-renaming-the-jar-file}

De volgende twee uitvoeringsmodi voor de installatie kunnen worden geactiveerd door de naam van het installatiejar-bestand vóór de installatie te wijzigen:

* publish
* auteur

Voor het jar-bestand moet de naamgevingsconventie worden gebruikt:

`cq5-<run-mode>-p<port-number>`

Stel bijvoorbeeld de `publish` uitvoeringsmodus door naam te geven aan het jar-bestand:

`cq5-publish-p4503`

### De uitvoeringsmodus definiëren in web.xml (met toepassingsserver) {#defining-the-run-mode-in-web-xml-with-application-server}

Wanneer u een toepassingsserver gebruikt, kunt u het bezit ook vormen:

`sling.run.modes`

in het bestand:

`WEB-INF/web.xml`

Dit staat in de AEM `war` en moet vóór de implementatie worden bijgewerkt.

Zie [AEM installeren met een toepassingsserver](/help/sites-deploying/application-server-install.md) voor nadere bijzonderheden.
