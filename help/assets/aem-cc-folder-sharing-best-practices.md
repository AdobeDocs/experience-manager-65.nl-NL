---
title: AEM naar Creative Cloud-map met aanbevolen werkwijzen delen
description: Configureer Adobe Experience Manager (AEM) zodat gebruikers in AEM Assets mappen kunnen uitwisselen met gebruikers van Adobe Creative Cloud (CC).
contentOwner: AG
translation-type: tm+mt
source-git-commit: 70a88085a0fd6e949974aa7f1f92fdc3def3d98e

---


# AEM naar Creative Cloud-map met aanbevolen werkwijzen delen {#aem-to-creative-cloud-folder-sharing-best-practices}

>[!CAUTION]
>
>De functie voor het delen van mappen tussen AEM en Creative Cloud is verouderd. Adobe raadt u ten zeerste aan nieuwere mogelijkheden te gebruiken, zoals [Adobe Asset Link](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html) of [AEM-bureaubladtoepassing](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app.html). Leer meer over beste praktijken [bij de integratie met](/help/assets/aem-cc-integration-best-practices.md)AEM en Creative Cloud.

Adobe Experience Manager (AEM) kan zo worden geconfigureerd dat gebruikers in AEM Assets mappen kunnen delen met gebruikers van Adobe Creative Cloud-toepassingen, zodat ze beschikbaar zijn als gedeelde mappen in de Adobe Creative Cloud Assets-service. De functie kan worden gebruikt om bestanden uit te wisselen tussen creatieve teams en gebruikers van AEM Assets, vooral wanneer creatieve gebruikers geen toegang hebben tot de AEM Assets-instantie (ze bevinden zich niet op het bedrijfsnetwerk).

Dit type integratie kan in de volgende gebruiksgevallen worden gebruikt, vooral wanneer het werken met gebruikers die geen directe toegang tot activa AEM hebben:

* Gebruikers van AEM Assets delen een set specifieke middelen met gebruikers van Adobe Creative Cloud Files (bijvoorbeeld een creatief overzicht en een set goedgekeurde middelen voor ontwerpwerkzaamheden voor een nieuwe marketingactiviteit)
* Gebruikers van AEM Assets ontvangen nieuwe bestanden die zijn gemaakt door gebruikers van de Adobe Creative Cloud-app.

>[!NOTE]
>
>Voordat u dit document leest, kunt u de algemene best practices [voor](/help/assets/aem-cc-integration-best-practices.md) AEM- en Creative Cloud-integratie doornemen voor een overzicht op een hoger niveau van het onderwerp.

## Overzicht {#overview}

Voor het delen van mappen naar Creative Cloud is het afhankelijk van het delen van mappen en bestanden aan de serverzijde tussen AEM Assets en Creative Cloud-accounts. Creatieve professionals die de Creative Cloud-bureaubladtoepassing op hun bureaublad gebruiken, kunnen de gedeelde mappen bovendien rechtstreeks op hun schijven beschikbaar stellen met behulp van Adobe CreativeSync-technologie.

Het volgende diagram geeft een overzicht van de integratie.

![chlimage_1-179](assets/chlimage_1-406.png)

De integratie omvat de volgende elementen:

* **AEM-middelenserver** die wordt geïmplementeerd in het bedrijfsnetwerk (beheerde services of on-premise): Hier wordt het delen van mappen gestart.
* **Adobe Marketing Cloud Assets Core-service**: Handelt als tussenpersoon tussen AEM- en Creative Cloud-opslagservices. Beheerders van het bedrijf dat de integratie gebruikt, moeten een vertrouwensrelatie tot stand brengen tussen de organisatie Marketing Cloud en de instantie AEM Assets. Ze [definiëren ook een lijst met goedgekeurde Creative Cloud-medewerkers](https://marketing.adobe.com/resources/help/en_US/mcloud/t_admin_add_cc_user.html)die gebruikers van AEM Assets ook kunnen delen voor extra beveiliging.

* **Creative Cloud Assets-webservices** (webinterface voor opslag en Creative Cloud Files): Op deze manier kunnen specifieke gebruikers van de Creative Cloud-app met wie een AEM Assets-map is gedeeld, de uitnodiging accepteren en de map bekijken in hun Creative Cloud-accountopslag.
* **Creative Cloud-bureaubladtoepassing**: (Optioneel) Hiermee kunt u rechtstreeks via synchronisatie met Creative Cloud Assets-opslag toegang krijgen tot gedeelde mappen/bestanden vanaf het bureaublad van de creatieve gebruiker.

## Kenmerken en beperkingen {#characteristics-and-limitations}

* **** Eenvoudige doorgave van wijzigingen: Bestandswijzigingen worden alleen in één richting doorgegeven, van het systeem (AEM of Creative Cloud Assets) waar het element oorspronkelijk is gemaakt (geüpload). De integratie biedt geen volledig geautomatiseerde, tweezijdige synchronisatie tussen de twee systemen.
* **Versioning:**

   * AEM maakt alleen versies van een element op updates als het bestand is gemaakt in AEM en daar wordt bijgewerkt.
   * Creative Cloud Assets beschikt over een eigen [versiefunctie](https://helpx.adobe.com/creative-cloud/help/versioning-faq.html) die is gericht op Werk in uitvoering-updates (slaat updates in principe maximaal 10 dagen op)

* **** Ruimtebeperkingen: Grootte en volumes van uitgewisselde bestanden worden beperkt door het specifieke quotum [voor](https://helpx.adobe.com/creative-cloud/kb/file-storage-quota.html) Creative Cloud-middelen voor creatieve gebruikers (afhankelijk van het abonnementsniveau) en een limiet van 5 GB voor de bestandsgrootte. De ruimte wordt bovendien beperkt door de quota voor middelen die de organisatie heeft in de Adobe Marketing Cloud Assets core-service.

* **** Ruimtevereisten: De bestanden in gedeelde mappen moeten ook fysiek worden opgeslagen in AEM en vervolgens in een Creative Cloud-account, met een kopie in cache in de Marketing Cloud Assets Core-service.
* **** Netwerken en bandbreedte: De bestanden in gedeelde mappen en alle updates moeten via het netwerk tussen de systemen worden getransporteerd. Zorg ervoor dat alleen relevante bestanden en updates worden gedeeld.
* **Maptype**: Het delen van een map met middelen van het type `sling:OrderedFolder`, wordt niet ondersteund in de context van delen in Adobe Marketing Cloud. Als u een map wilt delen, selecteert u bij het maken ervan in AEM Assets niet de optie Geordend.

## Aanbevolen procedures {#best-practices}

Aanbevolen procedures voor het delen van de AEM-bestanden naar Creative Cloud-mappen zijn:

* **** Overwegingen voor volume: Mapdeling via AEM/Creative Cloud moet worden gebruikt om een kleiner aantal bestanden te delen, bijvoorbeeld voor een specifieke campagne of activiteit. Als u grotere sets middelen wilt delen, zoals alle goedgekeurde middelen in de organisatie, gebruikt u andere distributiemethoden (bijvoorbeeld AEM Assets Brand Portal) of de AEM-bureaubladtoepassing.

* **** Vermijd het delen van diepe hiërarchieën: Het delen werkt recursief en maakt het niet mogelijk selectief te delen. Gewoonlijk worden alleen mappen zonder submappen of met een zeer oppervlakkige hiërarchie, zoals 1 submapniveau, beschouwd als gedeelde mappen.
* **** Afzonderlijke mappen voor delen in één richting: Afzonderlijke mappen moeten worden gebruikt voor het delen van de uiteindelijke middelen van AEM Assets naar Creative Cloud-bestanden en voor het delen van Creative Cloud-bestanden naar AEM Assets. Samen met een goede naamgevingsconventie voor deze mappen, wordt er een beter te begrijpen werkomgeving gemaakt voor zowel AEM Assets als Creative Cloud-gebruikers.
* **** WIP in de gedeelde map vermijden: Gedeelde map mag niet worden gebruikt voor Werk in uitvoering. Gebruik een aparte map in Creative Cloud Files om werk uit te voeren waarvoor regelmatig wijzigingen in het bestand nodig zijn.
* **** Nieuwe taken starten buiten de gedeelde map: Nieuwe ontwerpen (creatieve bestanden) moeten worden gestart in de afzonderlijke WIP-map in Creative Cloud Files. Wanneer u ze wilt delen met gebruikers van AEM Assets, moeten ze worden verplaatst of opgeslagen naar de gedeelde map.
* **** Structuur voor delen vereenvoudigen: Voor een beter te beheren werkende opstelling, denk over het vereenvoudigen van de het delen structuur. In plaats van met alle creatieve gebruikers te delen, zouden de omslagen van Activa AEM met teamvertegenwoordiger(s) slechts, zoals een creatieve directeur of teammanager moeten worden gedeeld. De manager aan de creatieve kant ontvangt definitieve activa, beslist over werktaken, en laat ontwerpers dan in hun eigen Creative Cloud- rekeningen op WIP activa werken. Ze kunnen de samenwerkingsfuncties van Creative Cloud gebruiken om het werk te coördineren en ten slotte elementen selecteren en plaatsen die klaar zijn om te worden gedeeld naar AEM Assets in hun creatieve, klare gedeelde map.

In het volgende diagram ziet u een voorbeeldconfiguratie voor het maken van nieuwe ontwerpen op basis van bestaande definitieve elementen van AEM Assets.

![chlimage_1-180](assets/chlimage_1-407.png)
