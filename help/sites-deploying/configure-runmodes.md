---
title: Modi uitvoeren
seo-title: Modi uitvoeren
description: Leer hoe u uw AEM voor specifieke doeleinden kunt afstemmen met behulp van runmodi.
seo-description: Leer hoe u uw AEM voor specifieke doeleinden kunt afstemmen met behulp van runmodi.
uuid: 8a0c6e5c-4fae-43e2-b745-eee58f346ceb
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: configuring
content-type: reference
discoiquuid: 12329e26-40bc-4c94-bc60-6d9cbd01345f
feature: Configureren
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '766'
ht-degree: 0%

---


# Run Modes{#run-modes}

Met de uitvoermodi kunt u uw AEM instellen voor een bepaald doel. bijvoorbeeld auteur of publicatie, test, ontwikkeling, intranet of andere.

U kunt:

* [Bepaal inzamelingen van configuratieparameters voor elke looppaswijze](#defining-configuration-properties-for-a-run-mode).

   Een basisreeks configuratieparameters wordt toegepast voor alle looppaswijzen, kunt u extra reeksen aan het doel van uw specifiek milieu dan stemmen. Deze worden naar wens toegepast.

* [Geef aanvullende bundels op die voor een bepaalde modus](#defining-additional-bundles-to-be-installed-for-a-run-mode) moeten worden geïnstalleerd.

Alle instellingen en definities worden in één opslagplaats opgeslagen en geactiveerd door de **Run-modus** in te stellen.

## Installatie-uitvoeringsmodi {#installation-run-modes}

De (of vaste) loopwijzen van de installatie worden gebruikt op installatietijd en dan voor het volledige leven van de instantie bevestigd, kunnen zij niet worden veranderd.

De uitvoermodi voor de installatie zijn beschikbaar buiten de box:

* `author`
* `publish`
* `samplecontent`
* `nosamplecontent`

Dit zijn twee paren van elkaar uitsluitende loopwijzen; u kunt bijvoorbeeld :

* `author` of `publish` definiëren, niet beide tegelijk

* `author` combineren met `samplecontent` of `nosamplecontent` (maar niet beide)

>[!CAUTION]
>
>Wanneer u een van de bovenstaande uitvoeringsmodi gebruikt (auteur, publicatie, samplinginhoud, geen samplinginhoud), definieert de waarde die tijdens de installatietijd wordt gebruikt de uitvoeringsmodus voor de *volledige levensduur* van die installatie.
>
>Voor deze uitvoeringsmodi kunt u deze na de installatie *niet* wijzigen.

## Aangepaste uitvoermodi {#customized-run-modes}

U kunt ook uw eigen aangepaste uitvoermodi maken. Deze kunnen worden gecombineerd voor scenario&#39;s zoals:

* `author` + `development`

* `publish` +  `test`

* `publish` + `test` + `golive`

* `publish` +  `intranet`

* indien nodig. . .

De aangepaste looppaswijzen kunnen ook bij elk opstarten worden geselecteerd.

## Sampleinhoud en geen-samplinginhoud {#using-samplecontent-and-nosamplecontent} gebruiken

Met deze modi kunt u het gebruik van voorbeeldinhoud beheren. De voorbeeldinhoud wordt gedefinieerd voordat de quickstart wordt gemaakt en kan pakketten, configuraties, enz. omvatten:

* In de uitvoermodus `samplecontent` wordt deze inhoud geïnstalleerd (de standaardmodus).

* In de modus `nosamplecontent` wordt de voorbeeldinhoud niet geïnstalleerd.

De run-modus voor noSampling-inhoud is ontworpen voor productie-installaties.

## Configuratieeigenschappen definiëren voor een uitvoeringsmodus {#defining-configuration-properties-for-a-run-mode}

Een inzameling van waarden voor configuratieeigenschappen, die voor een bepaalde looppaswijze wordt gebruikt, kan in de bewaarplaats worden bewaard.

De uitvoeringsmodus wordt aangegeven met een achtervoegsel op de mapnaam. Hierdoor kunt u alle configuraties als één opslagplaats opslaan. Bijvoorbeeld:

* `config`

   Van toepassing op alle runmodi

* `config.author`

   Wordt gebruikt voor de uitvoeringsmodus van de auteur

* `config.publish`

   Wordt gebruikt voor de publicatiemodus

* `config.<run-mode>`

   Wordt gebruikt voor de toepasselijke uitvoeringsmodus; bijvoorbeeld config

Zie [OSGi Configuratie in Repository](/help/sites-deploying/configuring-osgi.md#osgi-configuration-in-the-repository) voor verdere details bij het bepalen van de individuele configuratieknopen binnen deze omslagen en voor het creëren van configuraties voor combinaties veelvoudige looppaswijzen.

>[!NOTE]
>
>Voor [Installatiemodus](#installation-run-modes) (bijvoorbeeld de auteur) kan de uitvoermodus na de installatie niet worden gewijzigd. Wijzigingen in de afzonderlijke configuratie-eigenschappen worden echter van kracht na het opnieuw opstarten.

## Aanvullende bundels definiëren die moeten worden geïnstalleerd voor een uitvoeringsmodus {#defining-additional-bundles-to-be-installed-for-a-run-mode}

U kunt ook extra bundels opgeven die voor een bepaalde uitvoermodus moeten worden geïnstalleerd. Voor deze definities worden installatiemappen gebruikt om de bundels vast te houden. Ook hier wordt de uitvoeringsmodus aangegeven met een voorvoegsel:

* `install.author`
* `install.publish`

Deze mappen zijn van het type `nt:folder` en moeten de juiste bundel bevatten.

## CQ starten met een specifieke uitvoeringsmodus {#starting-cq-with-a-specific-run-mode}

Als u configuraties voor veelvoudige looppaswijzen hebt bepaald dan moet u bepalen welke op opstarten moet worden gebruikt. Er zijn verschillende methoden om op te geven welke uitvoeringsmodus moet worden gebruikt. de volgorde van resolutie is :

1. [ `sling.properties` file](#using-the-sling-properties-file)
1. [ `-r` option](#using-the-r-option)
1. [systeemeigenschappen (`-D`)](#using-a-system-property-in-the-start-script)

1. [Bestandsnaamdetectie](#filename-detection-renaming-the-jar-file)

Wanneer u een toepassingsserver gebruikt, kunt u [ook de run mode in web.xml](#defining-the-run-mode-in-web-xml-with-application-server) bepalen.

### Het bestand sling.properties {#using-the-sling-properties-file} gebruiken

Het `sling.properties` dossier kan worden gebruikt om de vereiste looppaswijze te bepalen:

1. Bewerk het configuratiebestand:

   `<cq-installation-dir>/crx-quickstart/conf/sling.properties`

1. Voeg de volgende eigenschappen toe: het volgende voorbeeld is voor auteur:

   `sling.run.modes=author`

### De optie -r {#using-the-r-option} gebruiken

Een aangepaste uitvoeringsmodus kan worden geactiveerd door de optie `-r` te gebruiken wanneer u de snelstartmodus start. Gebruik bijvoorbeeld de volgende opdracht om een AEM instantie te starten met de uitvoermodus ingesteld op dev. &quot;

```shell
java -jar cq-56-p4545.jar -r dev
```

### Het gebruiken van een systeembezit in het beginmanuscript {#using-a-system-property-in-the-start-script}

Een systeemeigenschap in het beginscript kan worden gebruikt om de uitvoermodus op te geven.

* Gebruik bijvoorbeeld het volgende om een instantie te starten als een publicatie-instantie voor productie die zich in de VS bevindt:

   `-Dsling.run.modes=publish,prod,us`

### Bestandsnaamdetectie - naam van jar-bestand wijzigen {#filename-detection-renaming-the-jar-file}

De volgende twee uitvoeringsmodi voor de installatie kunnen worden geactiveerd door de naam van het installatiejar-bestand vóór de installatie te wijzigen:

* publish
* author

Voor het jar-bestand moet de naamgevingsconventie worden gebruikt:

`cq5-<run-mode>-p<port-number>`

Stel bijvoorbeeld de uitvoermodus `publish` in door het jar-bestand een naam te geven:

`cq5-publish-p4503`

### De uitvoeringsmodus definiëren in web.xml (met toepassingsserver) {#defining-the-run-mode-in-web-xml-with-application-server}

Wanneer u een toepassingsserver gebruikt, kunt u het bezit ook vormen:

`sling.run.modes`

in het bestand:

`WEB-INF/web.xml`

Dit staat in het AEM `war` dossier en zou vóór plaatsing moeten worden bijgewerkt.

Zie [AEM installeren met een toepassingsserver](/help/sites-deploying/application-server-install.md) voor meer informatie.
