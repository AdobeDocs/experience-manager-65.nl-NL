---
title: '[!DNL Assets] formaatgids'
description: Aanbevolen werkwijzen om efficiënte metriek te bepalen om de infrastructuur en de middelen te schatten die worden vereist om  [!DNL Adobe Experience Manager Assets] op te stellen.
contentOwner: AG
role: Architect, Administrator
feature: Asset Management
translation-type: tm+mt
source-git-commit: 174e0703ae541641e3dc602e700bcd31624ae62c
workflow-type: tm+mt
source-wordcount: '1619'
ht-degree: 0%

---


# [!DNL Assets] formaatgids  {#assets-sizing-guide}

Wanneer het rangschikken van het milieu voor een [!DNL Adobe Experience Manager Assets] implementatie, is het belangrijk om ervoor te zorgen dat er voldoende middelen in termen van schijf, cpu, geheugen, IO, en netwerkproductie beschikbaar zijn. Als u veel van deze bronnen wilt vergroten, moet u weten hoeveel elementen in het systeem worden geladen. Als er geen betere maateenheid beschikbaar is, kunt u de grootte van de bestaande bibliotheek delen door de leeftijd van de bibliotheek om de snelheid te vinden waarmee elementen worden gemaakt.

## Schijf {#disk}

### DataStore {#datastore}

Een algemene fout die wordt gemaakt bij het instellen van de grootte van de vereiste schijfruimte voor een [!DNL Assets]-implementatie, is het baseren van de berekeningen op de grootte van de Raw-afbeeldingen die in het systeem worden opgenomen. [!DNL Experience Manager] maakt standaard drie uitvoeringen naast de oorspronkelijke afbeelding voor gebruik bij het renderen van de [!DNL Experience Manager]-gebruikersinterface-elementen. In vorige implementaties, zijn deze vertoningen waargenomen tweemaal de grootte van de activa veronderstellen die worden opgenomen.

De meeste gebruikers definiëren aangepaste uitvoeringen naast de uitvoeringen buiten de box. Naast de vertoningen, [!DNL Assets] laat u subactiva uit gemeenschappelijke dossiertypes, zoals [!DNL Adobe InDesign] en [!DNL Adobe Illustrator] halen.

Ten slotte worden bij versiemogelijkheden van [!DNL Experience Manager] dubbele elementen uit de versiegeschiedenis opgeslagen. U kunt de versies vormen om vaak worden gezuiverd. Veel gebruikers kiezen er echter voor om de versies in het systeem lange tijd te behouden, wat extra opslagruimte verbruikt.

Gezien deze factoren, vereist u een methodologie om een aanvaardbare nauwkeurige opslagruimte te berekenen om gebruikersactiva op te slaan.

1. Bepaal de grootte en het aantal elementen dat in het systeem wordt geladen.
1. Hiermee wordt een representatieve steekproef opgehaald van de elementen die naar [!DNL Experience Manager] moeten worden geüpload. Als u bijvoorbeeld PSD-, JPG-, AI- en PDF-bestanden in het systeem wilt laden, hebt u meerdere voorbeeldafbeeldingen van elke bestandsindeling nodig. Bovendien moeten deze monsters representatief zijn voor de verschillende bestandsgrootten en complexiteiten van afbeeldingen.
1. Definieer de uitvoeringen die moeten worden gebruikt.
1. Maak de uitvoeringen in [!DNL Experience Manager] met behulp van [!DNL ImageMagick] of [!DNL Adobe Creative Cloud] toepassingen. Naast de vertoningen die de gebruikers specificeren, creeer uit-van-de-doos vertoningen. Voor gebruikers die Dynamic Media implementeren, kunt u het binaire getal IC gebruiken om de PTIFF-uitvoeringen te genereren die in de Experience Manager moeten worden opgeslagen.
1. Als u subassets wilt gebruiken, genereert u deze voor de juiste bestandstypen.
1. Vergelijk de grootte van de uitvoerafbeeldingen, uitvoeringen en subelementen met de oorspronkelijke afbeeldingen. Hiermee kunt u een verwachte groeifactor genereren wanneer het systeem wordt geladen. Als u bijvoorbeeld uitvoeringen en subelementen genereert met een gecombineerde grootte van 3 GB na het verwerken van 1 GB aan elementen, is de groeifactor van de uitvoering 3.
1. Bepaal de maximumtijd gedurende welke elementversies in het systeem moeten worden onderhouden.
1. Bepaal hoe vaak bestaande elementen in het systeem worden gewijzigd. Als [!DNL Experience Manager] wordt gebruikt als een samenwerkingscentrum in creatieve werkschema&#39;s, is de hoeveelheid veranderingen hoog. Als alleen voltooide elementen naar het systeem worden geüpload, is dit aantal veel lager.
1. Bepaal hoeveel elementen elke maand in het systeem worden geladen. Als u niet zeker weet, controleert u het aantal elementen dat momenteel beschikbaar is en verdeelt u het getal door de leeftijd van het oudste element om een geschatte waarde te berekenen.

Door de bovenstaande stappen uit te voeren, kunt u het volgende bepalen:

* Onbewerkte grootte van te laden elementen.
* Aantal te laden elementen.
* Rendition growth factor.
* Aantal per maand aangebrachte wijzigingen in activa.
* Aantal maanden om elementversies te onderhouden.
* Aantal nieuwe elementen dat elke maand wordt geladen.
* Jaren van groei voor toewijzing van opslagruimte.

U kunt deze aantallen in het Netwerk het Rangschikken spreadsheet specificeren om de totale ruimte te bepalen die voor uw datastore wordt vereist. Het is ook een handig hulpmiddel om het effect te bepalen van het onderhoud van elementversies of het wijzigen van elementen in [!DNL Experience Manager] op schijfgroei.

De voorbeeldgegevens die in het gereedschap zijn ingevuld, tonen aan hoe belangrijk het is om de vermelde stappen uit te voeren. Als u de datastore alleen op basis van de te laden Raw-afbeeldingen (1 TB) wijzigt, hebt u de grootte van de opslagplaats mogelijk met een factor 15 onderschat.

[Bestand ophalen](assets/disk_sizing_tool.xlsx)

### Gedeelde datastores {#shared-datastores}

Voor grote datastores, kunt u een gedeelde datastore of door een gedeelde dossierdatastore op een netwerk in bijlage aandrijving of door een datastore van Amazon S3 uitvoeren. In dit geval hoeft in afzonderlijke gevallen geen kopie van de binaire bestanden te worden bewaard. Bovendien vergemakkelijkt een gedeelde datastore binair-geen replicatie en helpt de bandbreedte verminderen die wordt gebruikt om activa aan publicatiemilieu&#39;s te herhalen.

#### Gebruik gevallen {#use-cases}

De datastore kan tussen een primaire en reserve auteursinstantie worden gedeeld om de hoeveelheid tijd te minimaliseren die het vergt om de reserve instantie met veranderingen bij te werken die in de primaire instantie worden aangebracht. U kunt datastore tussen de auteur ook delen en instanties publiceren om het verkeer tijdens replicatie te minimaliseren.

#### Terugbetalingen {#drawbacks}

Door sommige valkuilen wordt het delen van een datastore niet in alle gevallen aanbevolen.

#### Enkel punt van fout {#single-point-of-failure}

Met een gedeelde datastore introduceert u één foutpunt in een infrastructuur. Overweeg een scenario waarin uw systeem één auteur en twee publiceer instanties heeft, elk met hun eigen datastore. Als één van hen crasht, kunnen de andere twee nog lopen. Nochtans, als datastore wordt gedeeld, kan één enkele schijfmislukking de volledige infrastructuur onderdrukken. Zorg daarom dat u een back-up van de gedeelde datastore bijhoudt vanaf waar u de datastore snel kunt herstellen.

Het implementeren van de AWS S3-service voor gedeelde datastores heeft de voorkeur, omdat dit de kans op mislukking aanzienlijk verkleint in vergelijking met normale schijfarchitecturen.

#### Hogere complexiteit {#increased-complexity}

Gedeelde datastores verhogen ook de ingewikkeldheid van verrichtingen, zoals huisvuilinzameling. Normaal, kan de huisvuilinzameling voor een standalone datastore met één enkele klik in werking worden gesteld. Nochtans, vereisen de gedeelde datastores de verrichtingen van de marktopening op elk lid dat datastore gebruikt, naast het runnen van de daadwerkelijke inzameling op één enkele knoop.

Voor AWS-bewerkingen kan het implementeren van één centrale locatie (via Amazon S3) in plaats van een RAID-array van EBS-volumes te maken, de complexiteit en operationele risico&#39;s op het systeem aanzienlijk compenseren.

#### Prestatieproblemen {#performance-concerns}

Een gedeelde datastore vereist dat de binaire getallen op een netwerk-opgezette aandrijving worden opgeslagen die tussen alle instanties wordt gedeeld. Omdat deze binaire getallen over een netwerk worden betreden, worden de systeemprestaties nadelig beïnvloed. U kunt het effect gedeeltelijk verlichten door een snelle netwerkverbinding aan een snelle serie van schijven te gebruiken. Dit is echter een kostbaar voorstel. In het geval van AWS-bewerkingen zijn alle schijven extern en vereisen ze netwerkconnectiviteit. Ephemeral-volumes verliezen gegevens wanneer de instantie start of stopt.

#### Latentie {#latency}

De latentie in S3 implementaties wordt geïntroduceerd door de achtergrond schrijvend draden. Bij de back-upprocedures moet rekening worden gehouden met deze latentie. Bovendien kunnen de indexen van Lucene onvolledig blijven wanneer het maken van een steun. Het is van toepassing op elk tijdgevoelig dossier dat aan S3 datastore wordt geschreven en van een andere instantie wordt betreden.

### Node store or document store {#node-store-document-store}

Het is moeilijk om exacte cijfers voor de grootte van een NodeStore of DocumentStore te bepalen vanwege de middelen die door het volgende worden verbruikt:

* Metagegevens van element
* Elementen
* Controlelogboeken
* Gearchiveerde en actieve workflows

Omdat de binaire getallen in de datastore worden opgeslagen, neemt elk binair getal wat ruimte in. De meeste opslagruimten zijn kleiner dan 100 GB. Er kunnen echter grotere opslagruimten zijn met een maximale grootte van 1 TB. Bovendien hebt u voldoende vrije ruimte op het volume nodig om de gecomprimeerde opslagplaats naast de vooraf gecomprimeerde versie te herschrijven om offline compacte compressie uit te voeren. Een goede regel-van-duim is de grootte van de schijf aan 1.5 keer de grootte die voor de bewaarplaats wordt verwacht.

Voor de opslagplaats, gebruik SSDs of schijven met een IOPS niveau groter dan 3000. Om de kans te elimineren dat IOPS prestatiesknelpunten introduceert, controleert cpu IO wachttijden niveaus op vroege tekenen van kwesties.

[Bestand ophalen](assets/aem_environment_sizingtool.xlsx)

## Netwerk {#network}

[!DNL Assets] heeft een aantal gebruiksgevallen die netwerkprestaties belangrijker maken dan op veel van onze  [!DNL Experience Manager] projecten. Een klant kan een snelle server hebben, maar als de netwerkverbinding niet groot genoeg is om de lading van de gebruikers te steunen die activa van het systeem uploaden en downloaden, dan zal het nog langzaam lijken. Er is een goede methodologie om het choke punt in de netwerkverbinding van een gebruiker aan [!DNL Experience Manager] bij [Activa overwegingen voor gebruikerservaring, instantie het rangschikken, werkschemaevaluatie, en netwerktopologie](/help/assets/assets-network-considerations.md) te bepalen.

## Beperkingen {#limitations}

Wanneer het rangschikken van een implementatie, is het belangrijk om systeembeperkingen in mening te houden. Als de voorgestelde implementatie deze beperkingen overschrijdt, maakt u gebruik van creatieve strategieën, zoals het verdelen van de elementen over meerdere [!DNL Assets] implementaties.

Bestandsgrootte is niet de enige factor die bijdraagt aan problemen met onvoldoende geheugen (OOM). Het hangt ook van afmetingen van het beeld af. U kunt OOM-problemen voorkomen door een hogere heapgrootte op te geven wanneer u [!DNL Experience Manager] start.

Bovendien kunt u het bezit van de drempelgrootte van de `com.day.cq.dam.commons.handler.StandardImageHandler` component in de Manager van de Configuratie uitgeven om tussentijds tijdelijk dossier groter dan nul te gebruiken.

## Maximum aantal elementen {#maximum-number-of-assets}

De limiet voor het aantal bestanden dat in een datastore kan bestaan, kan 2,1 miljard zijn vanwege bestandssysteembeperkingen. Het is waarschijnlijk dat de gegevensopslagruimte problemen tegenkomt vanwege een groot aantal knooppunten lang voordat de datastore-limiet wordt bereikt.

Gebruik de Camera Raw bibliotheek als de uitvoeringen onjuist zijn gegenereerd. In dit geval mag de langste zijde van de afbeelding echter niet groter zijn dan 65000 pixels. Bovendien mag de afbeelding niet meer dan 512 MP (512 x 1024 x 1024 pixels) bevatten. De grootte van het actief is niet van belang.

Het is moeilijk nauwkeurig de grootte te schatten van het TIF dossier dat uit-van-de-doos met een specifieke heap voor [!DNL Experience Manager] wordt gesteund omdat de extra factoren, zoals pixelgrootte verwerking beïnvloeden. Het is mogelijk dat [!DNL Experience Manager] een dossier van grootte van 255 MB uit-van-de-doos kan verwerken, maar niet een dossiergrootte van 18 MB kan verwerken omdat het laatstgenoemde uit een ongewoon hoger aantal pixel dan eerstgenoemde omvat.

## Grootte van elementen {#size-of-assets}

Standaard kunt u met [!DNL Experience Manager] elementen van maximaal 2 GB uploaden. Zie [Configuratie om zeer grote elementen te uploaden](managing-video-assets.md#configuration-to-upload-assets-that-are-larger-than-gb) voor informatie over het uploaden van zeer grote elementen.[!DNL Experience Manager]
