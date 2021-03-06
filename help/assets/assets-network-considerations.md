---
title: Netwerkoverwegingen en -vereisten
description: Bespreekt netwerkoverwegingen wanneer het ontwerpen van een  [!DNL Adobe Experience Manager Assets] plaatsing.
contentOwner: AG
role: Architect, Admin
feature: Gereedschappen voor ontwikkelaars
exl-id: 1313842c-18b1-4727-ba63-b454d0f5a2cc
source-git-commit: bb46b0301c61c07a8967d285ad7977514efbe7ab
workflow-type: tm+mt
source-wordcount: '994'
ht-degree: 0%

---

# [!DNL Assets] netwerkoverwegingen {#assets-network-considerations}

Kennis van uw netwerk is even belangrijk als begrip [!DNL Adobe Experience Manager Assets]. Het netwerk kan uploaden, downloaden, en gebruikerservaring beïnvloeden. Het Diagrammen van uw hulp van de netwerktopologie identificeert onderdrukkingspunten en sub-geoptimaliseerde gebieden in het netwerk die u moet bevestigen om netwerkprestaties en gebruikerservaring te verbeteren.

Zorg ervoor dat u het volgende in uw netwerkdiagram omvat:

* Connectiviteit van het cliëntapparaat (bijvoorbeeld, computer, mobiel, en tablet) aan het netwerk.
* Topologie van het collectieve netwerk.
* Een uplink naar internet vanuit het bedrijfsnetwerk en de [!DNL Experience Manager]-omgeving.
* Topologie van de [!DNL Experience Manager] milieu.
* Gelijktijdige gebruikers van de [!DNL Experience Manager]-netwerkinterface definiëren.
* Gedefinieerde workflows van de [!DNL Experience Manager]-implementatie.

## Connectiviteit van het cliëntapparaat aan het collectieve netwerk {#connectivity-from-the-client-device-to-the-corporate-network}

Begin door de connectiviteit tussen de individuele cliëntapparaten en het collectieve netwerk te diagrammen. In dit stadium, identificeer gedeelde middelen, zoals WiFi verbindingen, waar de veelvoudige gebruikers tot het zelfde punt of Ethernet schakelaar toegang hebben om activa te uploaden en te downloaden.

![chlimage_1-353](assets/chlimage_1-353.png)

Clientapparaten maken op verschillende manieren verbinding met het bedrijfsnetwerk, zoals gedeelde WiFi, Ethernet met een gedeelde switch en VPN. Het identificeren van en het begrip van chokepoints op dit netwerk is belangrijk voor [!DNL Assets] planning en om het netwerk te wijzigen.

Linksboven in het diagram worden drie apparaten weergegeven als een 48 Mbps WiFi-toegangspunt. Als alle apparaten tegelijk uploaden, wordt de bandbreedte van het WiFi-netwerk gedeeld tussen de apparaten. Vergeleken met het systeem als geheel, kan een gebruiker een verschillend onderdrukkingspunt voor de drie cliënten over dit verdeelde kanaal ontmoeten.

Het is een uitdaging om de ware snelheid van een WiFi-netwerk te meten omdat een traag apparaat andere clients kan beïnvloeden op het toegangspunt. Als u WiFi wilt gebruiken voor de interactie tussen bedrijfsmiddelen, voert u een snelheidstest uit bij meerdere clients tegelijk om de doorvoer te evalueren.

De bodem verlaten van het diagram toont twee apparaten die met het collectieve netwerk door onafhankelijke kanalen worden verbonden. Daarom kan elk apparaat een minimumsnelheid van 10 Mbps en 100 Mbps hebben.

De computer die aan het recht wordt getoond heeft een beperkt stroomopwaarts aan het collectieve netwerk over VPN met een snelheid van 1 Mbps. De gebruikerservaring voor de verbinding 1Mbps is zeer verschillend van de gebruikerservaring over de verbinding 1Gbps. Afhankelijk van de grootte van de activa interactie met gebruikers, kan hun opstraalverbinding van VPN voor de taak ontoereikend zijn.

## Topologie van het collectieve netwerk {#topology-of-the-corporate-network}

![chlimage_1-354](assets/chlimage_1-354.png)

Het diagram toont hogere opstraalverbindingssnelheden binnen het collectieve netwerk dan wat over het algemeen wordt gebruikt. Deze buizen zijn gedeelde bronnen. Als de gedeelde schakelaar wordt verwacht om 50 cliënten te behandelen, kan het potentieel een onderdrukking-punt zijn. In het aanvankelijke diagram, delen slechts twee computers de bijzondere verbinding.

## Uploaden naar internet vanuit het bedrijfsnetwerk en de [!DNL Experience Manager]-omgeving {#uplink-to-the-internet-from-the-corporate-network-and-aem-environment}

![chlimage_1-355](assets/chlimage_1-355.png)

Het is belangrijk om onbekende factoren op Internet en de verbinding te overwegen VPC omdat de bandbreedte over Internet wegens pieklading of grootschalig leveranciersstroomonderbrekingen kan worden verminderd. Over het algemeen is internetconnectiviteit betrouwbaar. Soms kan dit echter wel leiden tot een verschuiving.

Bij de opstraalverbinding van een collectief netwerk aan Internet, kunnen er andere diensten zijn gebruikend de bandbreedte. Het is belangrijk om te begrijpen hoeveel van de bandbreedte voor Activa kan worden gewijd of worden geprioriteerd. Bijvoorbeeld, als een verbinding 1 Gbps reeds bij 80% gebruik is, kunt u een maximum van 20% van de bandbreedte voor [!DNL Experience Manager Assets] slechts toewijzen.

De firewalls en de volmachten van de onderneming kunnen bandbreedte op vele verschillende manieren ook vormen. Dit type van apparaat kan bandbreedte voorrang geven gebruikend kwaliteit van de dienst, bandbreedtebeperkingen per gebruiker, of bitsnelheidsbeperkingen per gastheer. Dit zijn belangrijke te onderzoeken punten aangezien zij [!DNL Assets] gebruikerservaring beduidend kunnen beïnvloeden.

In dit voorbeeld heeft de onderneming een opstraalverbinding van 10 Gbps. Het moet groot genoeg zijn voor meerdere clients. Bovendien legt de firewall een grens van het gastheertarief van 10 Mbps op. Deze beperking kan verkeer aan één enkele gastheer aan 10 Mbps potentieel vertragen, alhoewel de opstraalverbinding aan Internet bij 10 Gbps is.

Dit is het kleinste clientgeoriënteerde onderdrukkingspunt. Nochtans, kunt u voor een verandering evalueren of een lijst van gewenste personen vormen met de groep van netwerkverrichtingen verantwoordelijk voor deze firewall.

Van de steekproefdiagrammen, kunt u concluderen dat zes apparaten een conceptueel kanaal 10Mbps delen. Afhankelijk van de omvang van de hefboomwerking van de activa, kan dit ontoereikend zijn om aan gebruikersverwachtingen te voldoen.

## Topologie van de [!DNL Experience Manager]-omgeving {#topology-of-the-aem-environment}

![chlimage_1-356](assets/chlimage_1-356.png)

Het ontwerpen van de topologie van het [!DNL Experience Manager] milieu vereist gedetailleerde kennis van de systeemconfiguratie en hoe het netwerk binnen het gebruikersmilieu wordt aangesloten.

Het steekproefscenario omvat publiceer landbouwbedrijf met vijf servers, een S3 binaire opslag, en gevormde Dynamic Media.

De verzender deelt het 100Mbps verbinding met twee entiteiten, de buitenwereld en de [!DNL Experience Manager] plaatsing. Voor gelijktijdige upload- en downloadbewerkingen moet u dit getal door twee delen. De externe opslag in de bijlage gebruikt een aparte verbinding.

De [!DNL Experience Manager]-implementatie deelt de 1Gbps-verbinding met meerdere services. Vanuit een perspectief van de netwerktopologie, is het gelijkwaardig aan het delen van één enkel kanaal met de verschillende diensten.

Als u het netwerk van het clientapparaat tot de [!DNL Experience Manager]-implementatie bekijkt, lijkt het kleinste onderdrukkingspunt de 10 Mbit firewallvertrager te zijn. U kunt deze waarden in de rangschikkingscalculator in [Middelen het Grootte Gids](assets-sizing-guide.md) gebruiken om de gebruikerservaring te bepalen.

## Gedefinieerde workflows van de [!DNL Experience Manager]-implementatie {#defined-workflows-of-the-aem-deployment}

Wanneer het overwegen van netwerkprestaties, kan het belangrijk zijn om de werkschema&#39;s en het publiceren te overwegen die in het systeem zullen voorkomen. Bovendien verbruiken S3 of andere netwerk in bijlage opslag die u gebruikt en I/O verzoeken netwerkbandbreedte. Daarom zelfs in een volledig geoptimaliseerd netwerk, kunnen de prestaties door schijf I/O worden beperkt.

Als u processen wilt stroomlijnen rond het opnemen van elementen (met name bij het uploaden van een groot aantal elementen), verkent u workflows met middelen en begrijpt u meer over de configuratie ervan.

Wanneer het evalueren van de interne werkschematopologie, zou u het volgende moeten analyseren:

* Procedures die een actief schrijven
* Workflows/gebeurtenissen die worden geactiveerd wanneer het element/de metagegevens worden gewijzigd
* Procedures die een actief lezen

Hier volgen enkele punten die u in overweging wilt nemen:

* XMP metagegevens lezen/schrijven
* Automatische activering en replicatie
* Watermerken
* Subelement opnemen/pagina uitnemen
* Overlappende workflows.

Hier volgt een voorbeeld van de klant voor het definiëren van een workflow met middelen.

![chlimage_1-357](assets/chlimage_1-357.png)
