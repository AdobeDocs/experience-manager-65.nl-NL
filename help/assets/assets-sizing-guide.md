---
title: '[!DNL Assets] hulplijn voor grootte wijzigen'
description: De beste praktijken om efficiënte metriek te bepalen om de infrastructuur en de middelen te schatten die worden vereist om  [!DNL Adobe Experience Manager Assets] op te stellen.
contentOwner: AG
role: Developer, Admin
feature: Asset Management
exl-id: fd58ead9-5e18-4f55-8d20-1cf4402fad97
solution: Experience Manager, Experience Manager Assets
source-git-commit: 07289e891399a78568dcac957bc089cc08c7898c
workflow-type: tm+mt
source-wordcount: '1619'
ht-degree: 0%

---

# [!DNL Assets] hulplijn voor grootte wijzigen {#assets-sizing-guide}

Wanneer het rangschikken van het milieu voor een [!DNL Adobe Experience Manager Assets] implementatie, is het belangrijk om ervoor te zorgen dat er voldoende middelen in termen van schijf, CPU, geheugen, IO, en netwerkproductie beschikbaar zijn. Als u veel van deze bronnen wilt vergroten, moet u weten hoeveel elementen in het systeem worden geladen. Als er geen betere maateenheid beschikbaar is, kunt u de grootte van de bestaande bibliotheek delen door de leeftijd van de bibliotheek om de snelheid te vinden waarmee elementen worden gemaakt.

## Schijf {#disk}

### DataStore {#datastore}

Een algemene fout die wordt gemaakt bij het instellen van de grootte van de vereiste schijfruimte voor een [!DNL Assets] -implementatie, is het baseren van de berekeningen op de grootte van de Raw-afbeeldingen die in het systeem worden opgenomen. Standaard maakt [!DNL Experience Manager] naast de oorspronkelijke afbeelding drie uitvoeringen voor gebruik bij het renderen van de gebruikersinterface-elementen van [!DNL Experience Manager] . In vorige implementaties, zijn deze vertoningen waargenomen tweemaal de grootte van de activa veronderstellen die worden opgenomen.

De meeste gebruikers definiëren aangepaste uitvoeringen naast de uitvoeringen buiten de box. Naast de uitvoeringen kunt u met [!DNL Assets] subelementen extraheren uit gangbare bestandstypen, zoals [!DNL Adobe InDesign] en [!DNL Adobe Illustrator] .

Tot slot worden bij versiemogelijkheden van [!DNL Experience Manager] dubbele bestanden van de elementen in de versiegeschiedenis opgeslagen. U kunt de versies configureren die vaak moeten worden gewist. Veel gebruikers kiezen er echter voor om de versies in het systeem lange tijd te behouden, wat extra opslagruimte verbruikt.

Gezien deze factoren, vereist u een methodologie om een aanvaardbare nauwkeurige opslagruimte te berekenen om gebruikersactiva op te slaan.

1. Bepaal de grootte en het aantal elementen die in het systeem worden geladen.
1. Hiermee krijgt u een representatief voorbeeld van de elementen die u wilt uploaden naar [!DNL Experience Manager] . Als u bijvoorbeeld PSD-, JPG-, AI- en PDF-bestanden in het systeem wilt laden, hebt u meerdere voorbeeldafbeeldingen van elke bestandsindeling nodig. Bovendien moeten deze monsters representatief zijn voor de verschillende bestandsgrootten en complexiteiten van afbeeldingen.
1. Definieer de uitvoeringen die moeten worden gebruikt.
1. Maak de uitvoeringen in [!DNL Experience Manager] met behulp van [!DNL ImageMagick] - of [!DNL Adobe Creative Cloud] -toepassingen. Naast de vertoningen die de gebruikers specificeren, creeer uit-van-de-doos vertoningen. Voor gebruikers die Dynamische media implementeren, kunt u de binaire IC-code gebruiken om de PTIFF-uitvoeringen te genereren die in Experience Manager moeten worden opgeslagen.
1. Als u subassets wilt gebruiken, genereert u deze voor de juiste bestandstypen.
1. Vergelijk de grootte van de uitvoerafbeeldingen, uitvoeringen en subelementen met de oorspronkelijke afbeeldingen. Hiermee kunt u een verwachte groeifactor genereren wanneer het systeem wordt geladen. Als u bijvoorbeeld uitvoeringen en subelementen genereert met een gecombineerde grootte van 3 GB na het verwerken van 1 GB aan elementen, is de groeifactor voor de uitvoering 3.
1. Bepaal de maximumtijd gedurende welke elementversies in het systeem moeten worden onderhouden.
1. Bepaal hoe vaak bestaande elementen in het systeem worden gewijzigd. Als [!DNL Experience Manager] wordt gebruikt als een samenwerkingshoofd in creatieve werkschema&#39;s, is de hoeveelheid veranderingen hoog. Als alleen voltooide elementen naar het systeem worden geüpload, is dit aantal veel lager.
1. Bepaal hoeveel elementen elke maand in het systeem worden geladen. Als u niet zeker weet, controleert u het aantal elementen dat momenteel beschikbaar is en verdeelt u het getal door de leeftijd van het oudste element om een geschatte waarde te berekenen.

Door de bovenstaande stappen uit te voeren, kunt u het volgende bepalen:

* Onbewerkte grootte van te laden elementen.
* Aantal te laden elementen.
* Rendition growth factor.
* Aantal per maand aangebrachte wijzigingen in activa.
* Aantal maanden om elementversies te onderhouden.
* Aantal nieuwe elementen dat elke maand wordt geladen.
* Jaren van groei voor toewijzing van opslagruimte.

U kunt deze aantallen in het Netwerk het Rangschikken spreadsheet specificeren om de totale ruimte te bepalen die voor uw datastore wordt vereist. Het is ook een handig hulpmiddel om te bepalen wat de invloed is van het onderhoud van elementversies of het wijzigen van elementen in [!DNL Experience Manager] op schijfgroei.

De voorbeeldgegevens die in het gereedschap zijn ingevuld, tonen aan hoe belangrijk het is om de vermelde stappen uit te voeren. Als u de datastore alleen op basis van de te laden Raw-afbeeldingen (1 TB) wijzigt, hebt u de grootte van de opslagplaats mogelijk met een factor 15 onderschat.

[Bestand ophalen](assets/disk_sizing_tool.xlsx)

### Gedeelde datastores {#shared-datastores}

Voor grote datastores, kunt u een gedeelde datastore of door een gedeelde dossierdatastore op een netwerk in bijlage aandrijving of door een datastore van Amazon S3 uitvoeren. In dit geval hoeft in afzonderlijke gevallen geen kopie van de binaire bestanden te worden bijgehouden. Bovendien vergemakkelijkt een gedeelde datastore binair-geen replicatie en helpt de bandbreedte verminderen die wordt gebruikt om activa aan publicatiemilieu&#39;s te herhalen.

#### Gebruik hoofdletters {#use-cases}

De datastore kan tussen een primaire en reserve auteursinstantie worden gedeeld om de hoeveelheid tijd te minimaliseren die het vergt om de reserve instantie met veranderingen bij te werken die in de primaire instantie worden aangebracht. U kunt datastore tussen de auteur ook delen en instanties publiceren om het verkeer tijdens replicatie te minimaliseren.

#### Nadelen {#drawbacks}

Door sommige valkuilen wordt het delen van een datastore niet in alle gevallen aanbevolen.

#### Eén foutpunt {#single-point-of-failure}

Met een gedeelde datastore introduceert u één foutpunt in een infrastructuur. Overweeg een scenario waarin uw systeem één auteur en twee publiceer instanties heeft, elk met hun eigen datastore. Als één van hen crasht, kunnen de andere twee nog lopen. Nochtans, als datastore wordt gedeeld, kan één enkele schijfmislukking de volledige infrastructuur onderdrukken. Zorg er daarom voor dat u een back-up van de gedeelde datastore bijhoudt vanaf waar u de datastore snel kunt herstellen.

De voorkeur wordt gegeven aan de AWS S3-service voor gedeelde datastores, omdat hierdoor de kans op mislukking aanzienlijk afneemt in vergelijking met normale schijfarchitecturen.

#### Meer complexiteit {#increased-complexity}

Gedeelde datastores verhogen ook de ingewikkeldheid van verrichtingen, zoals huisvuilinzameling. Normaal, kan de huisvuilinzameling voor een standalone datastore met één enkele klik in werking worden gesteld. Nochtans, vereisen de gedeelde datastores de verrichtingen van de marktopening op elk lid dat datastore gebruikt, naast het runnen van de daadwerkelijke inzameling op één enkele knoop.

Voor AWS-bewerkingen kan het implementeren van één centrale locatie (via Amazon S3) in plaats van een RAID-array van EBS-volumes te maken, de complexiteit en operationele risico&#39;s op het systeem aanzienlijk compenseren.

#### Prestatieproblemen {#performance-concerns}

Een gedeelde datastore vereist dat de binaire getallen op een netwerk-opgezette aandrijving worden opgeslagen die tussen alle instanties wordt gedeeld. Omdat deze binaire getallen over een netwerk worden betreden, worden de systeemprestaties nadelig beïnvloed. U kunt het effect gedeeltelijk verlichten door een snelle netwerkverbinding aan een snelle serie van schijven te gebruiken. Dit is echter een kostbaar voorstel. Als er AWS-bewerkingen zijn, zijn alle schijven extern en vereisen ze netwerkconnectiviteit. Ephemeral-volumes verliezen gegevens wanneer de instantie start of stopt.

#### Latentie {#latency}

De latentie in S3 implementaties wordt geïntroduceerd door de achtergrond schrijvend draden. Back-upprocedures moeten rekening houden met deze vertraging. Bovendien kunnen de indexen van Lucene onvolledig blijven wanneer het maken van een steun. Het is van toepassing op elk tijdgevoelig dossier dat aan S3 datastore wordt geschreven en van een andere instantie wordt betreden.

### Node Store of document Store {#node-store-document-store}

Het is moeilijk om exacte cijfers voor de grootte van een NodeStore of DocumentStore te bepalen vanwege de middelen die door het volgende worden verbruikt:

* Metagegevens van element
* Elementen
* Controlelogboeken
* Gearchiveerde en actieve workflows

Omdat de binaire getallen in de datastore worden opgeslagen, neemt elk binair getal wat ruimte in. De meeste opslagruimten zijn kleiner dan 100 GB. Er kunnen echter grotere opslagruimten zijn met een maximale grootte van 1 TB. Bovendien hebt u voldoende vrije ruimte op het volume nodig om de gecomprimeerde opslagplaats naast de vooraf gecomprimeerde versie te herschrijven om offline compacte compressie uit te voeren. Een goede regel-van-duim is de grootte van de schijf aan 1.5 keer de grootte die voor de bewaarplaats wordt verwacht.

Voor de opslagplaats, gebruik SSDs of schijven met een IOPS niveau groter dan 3000. Om de kans te elimineren dat IOPS prestatieknelheden introduceert, controleert u de CPU IO-wachttijden op vroege tekenen van problemen.

[Bestand ophalen](assets/aem_environment_sizingtool.xlsx)

## Netwerk {#network}

[!DNL Assets] heeft verschillende gebruiksgevallen die netwerkprestaties belangrijker maken dan bij veel van onze [!DNL Experience Manager] -projecten. Een klant kan een snelle server hebben, maar als de netwerkverbinding niet groot genoeg is om de lading van de gebruikers te steunen die activa van het systeem uploaden en downloaden, dan zal het nog langzaam lijken. Er is een goede methode om het knooppunt in het netwerkverbinding van een gebruiker aan [!DNL Experience Manager] bij [&#x200B; Assets overwegingen voor gebruikerservaring, instantie het rangschikken, werkschemaevaluatie, en netwerktopologie &#x200B;](/help/assets/assets-network-considerations.md) te bepalen.

## Beperkingen {#limitations}

Wanneer het rangschikken van een implementatie, is het belangrijk om systeembeperkingen in mening te houden. Als de voorgestelde implementatie deze beperkingen overschrijdt, kunt u creatieve strategieën gebruiken, zoals het verdelen van de elementen over meerdere [!DNL Assets] -implementaties.

Bestandsgrootte is niet de enige factor die bijdraagt aan problemen met onvoldoende geheugen (OOM). Het hangt ook van afmetingen van het beeld af. U kunt OOM-problemen voorkomen door een hogere heapgrootte op te geven wanneer u [!DNL Experience Manager] start.

Bovendien kunt u het bezit van de drempelgrootte van de `com.day.cq.dam.commons.handler.StandardImageHandler` component in de Manager van de Configuratie uitgeven om tussentijds tijdelijk dossier groter dan nul te gebruiken.

## Maximumaantal activa {#maximum-number-of-assets}

De limiet voor het aantal bestanden dat in een datastore kan bestaan, kan 2,1 miljard zijn vanwege bestandssysteembeperkingen. Het is waarschijnlijk dat de gegevensopslagruimte problemen tegenkomt vanwege een groot aantal knooppunten lang voordat de datastore-limiet wordt bereikt.

Gebruik de Camera Raw-bibliotheek als de uitvoeringen onjuist zijn gegenereerd. In dit geval mag de langste zijde van de afbeelding echter niet groter zijn dan 65000 pixels. Bovendien mag de afbeelding niet meer dan 512 MP (512 x 1024 x 1024 pixels) bevatten. De grootte van het actief is niet van belang.

Het is moeilijk nauwkeurig de grootte te schatten van het TIFF-bestand dat buiten de box met een specifieke heap voor [!DNL Experience Manager] wordt ondersteund, omdat extra factoren, zoals pixelgrootte, de verwerking beïnvloeden. Het is mogelijk dat [!DNL Experience Manager] een bestand van 255 MB buiten de box kan verwerken, maar geen bestandsgrootte van 18 MB kan verwerken omdat het laatste bestand een ongewoon groter aantal pixels bevat dan het eerste.

## Omvang van elementen {#size-of-assets}

Standaard kunt u met [!DNL Experience Manager] elementen van maximaal 2 GB uploaden. Om zeer grote activa in [!DNL Experience Manager] te uploaden, zie [&#x200B; Configuratie om zeer grote activa &#x200B;](managing-video-assets.md#configuration-to-upload-assets-that-are-larger-than-gb) te uploaden.
