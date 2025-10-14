---
title: Modi uitvoeren
description: Leer hoe u uw AEM voor specifieke doeleinden kunt afstemmen met behulp van runmodi.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: configuring
content-type: reference
feature: Administering
exl-id: 6d03cb1d-500e-4a23-80e5-347a43dff30e
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: 48d12388d4707e61117116ca7eb533cea8c7ef34
workflow-type: tm+mt
source-wordcount: '746'
ht-degree: 0%

---

# Modi uitvoeren{#run-modes}

Met uitvoeringsmodi kunt u de AEM voor een bepaald doel instellen, bijvoorbeeld auteur of publicatie, test, ontwikkeling, intranet of andere.

U kunt:

* [&#x200B; bepaalt inzamelingen van configuratieparameters voor elke looppaswijze &#x200B;](#defining-configuration-properties-for-a-run-mode).

  Een basisreeks configuratieparameters wordt toegepast voor alle looppaswijzen, kunt u extra reeksen aan het doel van uw specifiek milieu dan stemmen. Deze worden naar wens toegepast.

* [&#x200B; bepaalt extra bundels die voor een bepaalde wijze &#x200B;](#defining-additional-bundles-to-be-installed-for-a-run-mode) moeten worden geïnstalleerd.

Alle montages en definities worden opgeslagen in één bewaarplaats en geactiveerd door de **Wijze van de Looppas** te plaatsen.

## Installatie-uitvoeringsmodi {#installation-run-modes}

De (of vaste) loopwijzen van de installatie worden gebruikt op installatietijd en dan voor het volledige leven van de instantie bevestigd, kunnen zij niet worden veranderd.

De uitvoermodi voor de installatie zijn beschikbaar buiten de box:

* `author`
* `publish`
* `samplecontent`
* `nosamplecontent`

Dit zijn twee paren van elkaar uitsluitende looppaswijzen; bijvoorbeeld, kunt u:

* `author` of `publish` definiëren, niet tegelijkertijd

* `author` combineren met `samplecontent` of `nosamplecontent` (maar niet met beide)

>[!CAUTION]
>
>Wanneer het gebruiken van één van de bovengenoemde looppaswijzen (auteur, publiceer, steekproefinhoud, geen steekproefinhoud), bepaalt de waarde die bij installatietijd wordt gebruikt de looppaswijze voor het *volledige leven* van die installatie.
>
>Voor deze looppaswijzen kunt u *niet* hen na installatie veranderen.

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

* In de uitvoermodus van `samplecontent` wordt deze inhoud geïnstalleerd (de standaardmodus).

* In de modus `nosamplecontent` wordt de voorbeeldinhoud niet geïnstalleerd.

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

Zie {Configuratie 0} OSGi in de Bewaarplaats [&#128279;](/help/sites-deploying/configuring-osgi.md#osgi-configuration-in-the-repository) voor verdere details bij het bepalen van de individuele configuratieknopen binnen deze omslagen en voor het creëren van configuraties voor combinaties veelvoudige looppaswijzen.

>[!NOTE]
>
>Voor [&#x200B; Wijzen van de Looppas van de Installatie &#x200B;](#installation-run-modes) (bijvoorbeeld, auteur) kan de looppaswijze niet na installatie worden veranderd. Wijzigingen in de afzonderlijke configuratie-eigenschappen worden echter van kracht na het opnieuw opstarten.

## Aanvullende bundels definiëren die moeten worden geïnstalleerd voor een uitvoeringsmodus {#defining-additional-bundles-to-be-installed-for-a-run-mode}

U kunt ook extra bundels opgeven die voor een bepaalde uitvoermodus moeten worden geïnstalleerd. Voor deze definities worden installatiemappen gebruikt om de bundels vast te houden. Ook hier wordt de uitvoeringsmodus aangegeven met een voorvoegsel:

* `install.author`
* `install.publish`

Deze mappen zijn van het type `nt:folder` en moeten de juiste bundel bevatten.

## CQ starten met een specifieke uitvoeringsmodus {#starting-cq-with-a-specific-run-mode}

Als u configuraties voor veelvoudige looppaswijzen hebt bepaald dan moet u bepalen welke op opstarten moet worden gebruikt. Er zijn verschillende methoden om op te geven welke uitvoeringsmodus moet worden gebruikt. De volgorde van resolutie is:

1. [systeemeigenschappen (](#using-a-system-property-in-the-start-script)
1. [&#128279;](#using-the-sling-properties-file)
1. [&#128279;](#using-the-r-option)
1. [Bestandsnaamdetectie](#filename-detection-renaming-the-jar-file)

Wanneer u een toepassingsserver gebruikt kunt u ook [&#x200B; de looppaswijze in web.xml &#x200B;](#defining-the-run-mode-in-web-xml-with-application-server) bepalen.

### Het bestand sling.properties gebruiken {#using-the-sling-properties-file}

U kunt het bestand `sling.properties` gebruiken om de vereiste uitvoermodus te definiëren:

1. Bewerk het configuratiebestand:

   `<cq-installation-dir>/crx-quickstart/conf/sling.properties`

1. Voeg de volgende eigenschappen toe; het volgende voorbeeld is voor auteur:

   `sling.run.modes=author`

### De optie -r gebruiken {#using-the-r-option}

Een aangepaste uitvoeringsmodus kan worden geactiveerd door de optie `-r` te gebruiken wanneer de snelstartmodus wordt gestart. Gebruik bijvoorbeeld de volgende opdracht om een AEM instantie te starten met de uitvoermodus ingesteld op dev. &quot;

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

Stel bijvoorbeeld de uitvoermodus van `publish` in door het jar-bestand een naam te geven:

`cq5-publish-p4503`

### De uitvoeringsmodus definiëren in web.xml (met toepassingsserver) {#defining-the-run-mode-in-web-xml-with-application-server}

Wanneer u een toepassingsserver gebruikt, kunt u het bezit ook vormen:

`sling.run.modes`

in het bestand:

`WEB-INF/web.xml`

Dit staat in het AEM `war` -bestand en moet worden bijgewerkt voordat het wordt geïmplementeerd.

Zie [&#x200B; Installerend AEM met een Server van de Toepassing &#x200B;](/help/sites-deploying/application-server-install.md) voor verdere details.
