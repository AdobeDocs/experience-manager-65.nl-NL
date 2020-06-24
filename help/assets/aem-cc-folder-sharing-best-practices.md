---
title: Adobe Experience Managers naar Adobe Creative Cloud-map met beste praktijken
description: Configureer Adobe Experience Manager zodat gebruikers in Experience Manager Assets mappen kunnen uitwisselen met gebruikers van Adobe Creative Cloud (CC).
contentOwner: AG
translation-type: tm+mt
source-git-commit: 70b18dbe351901abb333d491dd06a6c1c1c569d6
workflow-type: tm+mt
source-wordcount: '1079'
ht-degree: 0%

---


# Adobe Experience Managers naar Adobe Creative Cloud-map delen {#aem-to-creative-cloud-folder-sharing-best-practices}

>[!CAUTION]
>
>De functie voor het delen van mappen tussen Experience Manager en Creative Cloud is verouderd. Adobe raadt u ten zeerste aan om nieuwere mogelijkheden te gebruiken, zoals [Adobe Asset Link](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html) of [Experience Manager-bureaubladtoepassing](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app.html). Meer informatie over beste praktijken [bij de integratie van](/help/assets/aem-cc-integration-best-practices.md)Experience Manager en Creative Cloud.

Adobe Experience Manager kan zo worden geconfigureerd dat gebruikers in Middelen mappen kunnen delen met gebruikers van Adobe Creative Cloud-toepassingen, zodat ze beschikbaar zijn als gedeelde mappen in de Adobe Creative Cloud Assets-service. De functie kan worden gebruikt om bestanden uit te wisselen tussen creatieve teams en gebruikers van middelen, vooral wanneer creatieve gebruikers geen toegang hebben tot de instantie Assets (ze bevinden zich niet op het bedrijfsnetwerk).

Dit type integratie kan in de volgende gebruiksgevallen worden gebruikt, vooral wanneer het werken met gebruikers die geen directe toegang tot Activa hebben:

* Gebruikers van middelen delen een set specifieke middelen met gebruikers van Adobe Creative Cloud Files (bijvoorbeeld een creatieve samenvatting en een set goedgekeurde middelen voor ontwerpwerkzaamheden voor een nieuwe marketingactiviteit)
* Gebruikers van middelen ontvangen nieuwe bestanden die zijn gemaakt door gebruikers van de Adobe Creative Cloud-app.

>[!NOTE]
>
>Voordat u dit document leest, kunt u de algemene best practices [voor](/help/assets/aem-cc-integration-best-practices.md) Experience Manager- en Creative Cloud-integratie doornemen voor een overzicht op een hoger niveau van het onderwerp.

## Overzicht {#overview}

Voor het delen van mappen naar Creative Cloud is het afhankelijk van het delen van mappen en bestanden op de server tussen Middelen en Creative Cloud-accounts. Creatieve professionals die de Creative Cloud-bureaubladtoepassing op hun bureaublad gebruiken, kunnen de gedeelde mappen bovendien rechtstreeks op hun schijven beschikbaar stellen met behulp van Adobe CreativeSync-technologie.

Het volgende diagram geeft een overzicht van de integratie.

![chlimage_1-179](assets/chlimage_1-406.png)

De integratie omvat de volgende elementen:

* **Experience Manager Assets-server** geïmplementeerd in het bedrijfsnetwerk (beheerde services of on-premise): Hier wordt het delen van mappen gestart.
* **Adobe Marketing Cloud Assets core service**: Fungeert als tussenpersoon tussen Experience Manager en Creative Cloud-opslagservices. Beheerders van het bedrijf dat de integratie gebruikt, moeten een vertrouwensrelatie tot stand brengen tussen de organisatie Marketing Cloud en de instantie Assets. Ze [definiëren ook een lijst met goedgekeurde Creative Cloud-medewerkers](https://docs.adobe.com/content/help/en/core-services/interface/assets/t-admin-add-cc-user.html)die gebruikers van middelen ook mappen kunnen delen voor extra beveiliging.

* **Creative Cloud Assets-webservices** (webinterface voor opslag en Creative Cloud Files): Op deze manier kunnen specifieke gebruikers van de Creative Cloud-app met wie een map Middelen is gedeeld, de uitnodiging accepteren en de map bekijken in hun opslag van Creative Cloud-account.
* **Creative Cloud-bureaubladtoepassing**: (Optioneel) Hiermee kunt u rechtstreeks via synchronisatie met Creative Cloud Assets-opslag toegang krijgen tot gedeelde mappen/bestanden vanaf het bureaublad van de creatieve gebruiker.

## Kenmerken en beperkingen {#characteristics-and-limitations}

* **Eenvoudige doorgave van wijzigingen:** Bestandswijzigingen worden alleen in één richting doorgegeven, vanaf het systeem (Experience Manager of Creative Cloud Assets) waar het element oorspronkelijk is gemaakt (geüpload). De integratie biedt geen volledig geautomatiseerde, tweezijdige synchronisatie tussen de twee systemen.
* **Versioning:**

   * Experience Manager maakt bij updates alleen versies van een element als het bestand in Experience Manager is gestart en daar is bijgewerkt.
   * Creative Cloud Assets beschikt over een eigen [versiefunctie](https://helpx.adobe.com/creative-cloud/help/versioning-faq.html) die is gericht op Werk in uitvoering-updates (slaat updates in principe maximaal 10 dagen op)

* **Ruimtebeperkingen:** Grootte en volumes van uitgewisselde bestanden worden beperkt door het specifieke quotum [voor](https://helpx.adobe.com/creative-cloud/kb/file-storage-quota.html) Creative Cloud-middelen voor creatieve gebruikers (afhankelijk van het abonnementsniveau) en een limiet van 5 GB voor de bestandsgrootte. De ruimte wordt bovendien beperkt door het assetquotum dat de organisatie heeft in de kernservice Adobe Marketing Cloud Assets.

* **Ruimtevereisten:** De bestanden in gedeelde mappen moeten ook fysiek worden opgeslagen in Experience Manager en vervolgens in een Creative Cloud-account, met een kopie in cache in de Marketing Cloud Assets Core-service.
* **Netwerken en bandbreedte:** De bestanden in gedeelde mappen en alle updates moeten via het netwerk tussen de systemen worden getransporteerd. Zorg ervoor dat alleen relevante bestanden en updates worden gedeeld.
* **Maptype**: Het delen van een map Middelen van het type `sling:OrderedFolder`wordt niet ondersteund bij het delen in Adobe Marketing Cloud. Als u een map wilt delen, selecteert u bij het maken ervan in Elementen niet de optie Geordend.

## Best practices {#best-practices}

Aanbevolen procedures voor het delen van Experience Manager naar Creative Cloud-mappen zijn:

* **Overwegingen voor volume:** Mapdeling via Experience Manager/Creative Cloud moet worden gebruikt om een kleiner aantal bestanden te delen, bijvoorbeeld voor een specifieke campagne of activiteit. Als u grotere sets middelen wilt delen, zoals alle goedgekeurde middelen in de organisatie, gebruikt u andere distributiemethoden (bijvoorbeeld Assets Brand Portal) of de Experience Manager-bureaubladtoepassing.

* **Vermijd het delen van diepe hiërarchieën:** Het delen werkt recursief en maakt het niet mogelijk selectief te delen. Gewoonlijk worden alleen mappen zonder submappen of met een zeer oppervlakkige hiërarchie, zoals 1 submapniveau, beschouwd als gedeelde mappen.
* **Afzonderlijke mappen voor delen in één richting:** Afzonderlijke mappen moeten worden gebruikt voor het delen van definitieve middelen van middelen naar Creative Cloud-bestanden en voor het delen van creatieve middelen van Creative Cloud-bestanden naar middelen. Samen met een goede naamgevingsconventie voor deze mappen, wordt er een beter te begrijpen werkomgeving gemaakt voor zowel Middelen als Creative Cloud-gebruikers.
* **WIP in de gedeelde map vermijden:** Gedeelde map mag niet worden gebruikt voor Werk in uitvoering. Gebruik een aparte map in Creative Cloud Files om werk uit te voeren waarvoor regelmatig wijzigingen in het bestand nodig zijn.
* **Nieuwe taken starten buiten de gedeelde map:** Nieuwe ontwerpen (creatieve bestanden) moeten worden gestart in de afzonderlijke WIP-map in Creative Cloud Files. Wanneer u ze wilt delen met gebruikers van middelen, moeten ze worden verplaatst of opgeslagen naar de gedeelde map.
* **Structuur voor delen vereenvoudigen:** Voor een beter te beheren werkende opstelling, denk over het vereenvoudigen van de het delen structuur. In plaats van met alle creatieve gebruikers te delen, zouden de omslagen van Activa met teamvertegenwoordiger(s) slechts, zoals een creatieve directeur of teammanager moeten worden gedeeld. De manager aan de creatieve kant ontvangt definitieve activa, beslist over werktaken, en laat ontwerpers dan in hun eigen Creative Cloud- rekeningen op WIP activa werken. Ze kunnen de samenwerkingsfuncties van Creative Cloud gebruiken om het werk te coördineren en ten slotte elementen selecteren en weer delen naar Middelen in hun creatieve, klare gedeelde map.

Het volgende diagram illustreert een voorbeeldconfiguratie voor het creëren van nieuwe ontwerpen die op bestaande definitieve activa van Activa worden gebaseerd.

![chlimage_1-180](assets/chlimage_1-407.png)
