---
title: Het delen van de omslag aan  [!DNL Adobe Creative Cloud]  beste praktijken
description: Vorm  [!DNL Adobe Experience Manager]  om gebruikers in  [!DNL Experience Manager Assets]  toe te staan om omslagen met de gebruikers van Adobe Creative Cloud uit te wisselen.
contentOwner: AG
role: User, Admin
feature: Collaboration
exl-id: 130cec6d-1cdd-4304-94bb-65e6bb573e55
source-git-commit: 49688c1e64038ff5fde617e52e1c14878e3191e5
workflow-type: tm+mt
source-wordcount: '927'
ht-degree: 0%

---

# [!DNL Adobe Experience Manager] naar [!DNL Adobe Creative Cloud] map delen {#aem-to-creative-cloud-folder-sharing-best-practices}

>[!CAUTION]
>
>De functie [!DNL Experience Manager] to [!DNL Creative Cloud] voor het delen van mappen is vervangen. De Adobe adviseert gebruikend nieuwere mogelijkheden zoals [ de Vermogensverbinding van de Adobe ](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html) of [ Desktop app van de Experience Manager ](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html). Leer meer in [ Experience Manager en de integratie van het Creative Cloud beste praktijken ](/help/assets/aem-cc-integration-best-practices.md).

[!DNL Adobe Experience Manager] kan zo worden geconfigureerd dat gebruikers in [!DNL Assets] mappen kunnen delen met de gebruikers van [!DNL Adobe Creative Cloud] -toepassingen, zodat ze beschikbaar zijn als gedeelde mappen in de [!DNL Adobe Creative Cloud] -services. De functie kan worden gebruikt om bestanden uit te wisselen tussen creatieve teams en [!DNL Assets] -gebruikers, vooral wanneer creatieve gebruikers geen toegang hebben tot de [!DNL Assets] -implementatie (ze bevinden zich niet op het bedrijfsnetwerk).

Dit type integratie kan in de volgende gebruiksgevallen worden gebruikt, met name wanneer u werkt met gebruikers die geen directe toegang hebben tot [!DNL Assets] :

* [!DNL Assets] -gebruikers delen een set specifieke digitale elementen met gebruikers van [!DNL Adobe Creative Cloud] -bestanden (bijvoorbeeld een creatieve samenvatting en set goedgekeurde middelen voor ontwerpwerkzaamheden voor een nieuwe marketingactiviteit).
* [!DNL Assets] -gebruikers ontvangen nieuwe bestanden die door [!DNL Adobe Creative Cloud] -gebruikers zijn gemaakt.

>[!NOTE]
>
>Alvorens dit document te lezen, kunt u de algemene [ beste praktijken van de de integratie van de Experience Manager en van het Creative Cloud ](/help/assets/aem-cc-integration-best-practices.md) voor een overzicht van de integratie herzien.

## Overzicht {#overview}

[!DNL Experience Manager] naar [!DNL Creative Cloud] mapdelen is afhankelijk van het delen van mappen en bestanden op de server tussen [!DNL Assets] - en [!DNL Creative Cloud] -accounts. Creatieve professionals die de [!DNL Creative Cloud] -bureaubladtoepassing op hun desktopcomputers gebruiken, kunnen de gedeelde mappen ook rechtstreeks op hun schijven beschikbaar stellen met behulp van [!DNL Adobe CreativeSync] -technologie.

Het volgende diagram geeft een overzicht van de integratie.

![ chlimage_1-179 ](assets/chlimage_1-406.png)

De integratie omvat de volgende elementen:

* **[!DNL Experience Manager Assets]** geïmplementeerd in het bedrijfsnetwerk (Managed Services of on-premise): hier wordt het delen van mappen gestart.
* **[!DNL Adobe Experience Cloud Assets]kernservice** : treedt op als tussenpersoon tussen [!DNL Experience Manager] en [!DNL Creative Cloud] opslagservices. Een beheerder van een organisatie die de integratie gebruikt, moet een vertrouwensrelatie tot stand brengen tussen de organisatie van het Experience Cloud en de implementatie van [!DNL Assets] . Zij [ bepalen ook een lijst van goedgekeurde medewerkers van het Creative Cloud ](https://experienceleague.adobe.com/docs/core-services/interface/services/assets/t-admin-add-cc-user.html), dat [!DNL Assets] de gebruikers omslagen ook voor extra veiligheid kunnen delen.

* **[!DNL Creative Cloud]Assets-webservices** (web-UI voor opslag en [!DNL Creative Cloud] bestanden): dit is de situatie waarin specifieke gebruikers van een Creative Cloud-app, met wie een [!DNL Assets] -map werd gedeeld, de uitnodiging kunnen accepteren en de map kunnen bekijken in de opslag van hun Creative Cloud-account.
* **Desktop app van het Creative Cloud**: (Facultatief) staat voor directe toegang tot gedeelde omslag/dossiers van creatieve gebruiker toe Desktop via synchronisatie met [!DNL Creative Cloud] opslag van Assets.

## Kenmerken en beperkingen {#characteristics-and-limitations}

* **unidirectionele propagatie van veranderingen:** de veranderingen van het Dossier worden verspreid in één richting slechts - van het systeem ([!DNL Experience Manager] of [!DNL Creative Cloud Assets]), waar de activa oorspronkelijk werden gecreeerd (geupload). De integratie biedt geen volledig geautomatiseerde, tweezijdige synchronisatie tussen de twee systemen.
* **Versioning:**

   * [!DNL Experience Manager] maakt alleen versies van een element bij updates als het bestand afkomstig is uit [!DNL Experience Manager] en daar wordt bijgewerkt.
   * [!DNL Creative Cloud] Assets verstrekt zijn eigen [ versioning eigenschap ](https://helpx.adobe.com/creative-cloud/help/versioning-faq.html) die bij Werk in Voortgang updates (fundamenteel, slaat updates voor maximaal tien dagen op) wordt gericht

* **de beperkingen van de Ruimte:** Grootte en volumes van geruilde dossiers worden beperkt door het specifieke [ quotum van Assets van het Creative Cloud ](https://helpx.adobe.com/creative-cloud/kb/file-storage-quota.html) voor creatieve gebruikers (hangt van abonnementsniveau af) en een beperking van 5-GB maximumdossiergrootte. De ruimte wordt ook beperkt door de quota van de activa die de organisatie in de kerndienst van Adobe Experience Cloud Assets heeft.

* **ruimtevereisten:** de dossiers in gedeelde omslagen moeten ook fysisch in [!DNL Experience Manager] en dan in [!DNL Creative Cloud] rekening, met een caching exemplaar in [!DNL Experience Cloud Assets] kerndienst worden opgeslagen.
* **Voorzien van een netwerk en bandbreedte:** de dossiers in gedeelde omslagen en alle updates moeten over het netwerk tussen de systemen worden vervoerd. Zorg ervoor dat alleen relevante bestanden en updates worden gedeeld.
* **Type van Omslag**: Het delen van een [!DNL Assets] omslag van het type `sling:OrderedFolder`, wordt niet gesteund in de context van het delen in [!DNL Adobe Experience Cloud]. Selecteer de optie [!UICONTROL Ordered] niet als u een map wilt delen wanneer u deze maakt in [!DNL Assets] .

## Aanbevolen procedures {#best-practices}

De aanbevolen procedures voor het delen van mappen in de [!DNL Experience Manager] tot [!DNL Creative Cloud] zijn:

* **overwegingen van het Volume:** [!DNL Experience Manager] en [!DNL Creative Cloud] het Delen van de Omslag zou moeten worden gebruikt om kleiner aantal dossiers, bijvoorbeeld, relevant voor een specifieke campagne of een activiteit te delen. Als u grotere sets elementen wilt delen, zoals alle goedgekeurde elementen in de organisatie, gebruikt u andere distributiemethoden (bijvoorbeeld [!DNL Assets Brand Portal] ) of de [!DNL Experience Manager] desktop-app.
* **vermijd het delen diepe hiërarchieën:** het delen werkt recursief en staat niet voor selectief uit elkaar delen toe. Gewoonlijk worden alleen mappen zonder submappen of met een ondiepe hiërarchie, zoals één submapniveau, beschouwd als mappen die kunnen worden gedeeld.
* **afzonderlijke omslagen voor eenrichtings het delen:** de afzonderlijke omslagen zouden voor het delen van definitieve activa van [!DNL Assets] aan [!DNL Creative Cloud] dossiers moeten worden gebruikt, en voor het delen van creatief-klaar activa terug van [!DNL Creative Cloud] dossiers aan [!DNL Assets]. Samen met een goede naamgevingsconventie voor deze mappen, wordt er een beter te begrijpen werkomgeving gemaakt voor [!DNL Assets] - en [!DNL Creative Cloud] -gebruikers.
* **vermijd WIP in de gedeelde omslag:** gebruik geen gedeelde omslag voor Werk in uitvoering - gebruik een afzonderlijke omslag in de Dossiers van het Creative Cloud om het werk uit te voeren dat frequente veranderingen in het dossier vereist.
* **het nieuwe werk van het Begin buiten gedeelde omslag:** Nieuwe ontwerpen (creatieve dossiers) zouden in de afzonderlijke omslag van WIP in de Dossiers van het Creative Cloud moeten zijn begonnen, en wanneer zij klaar zijn om met [!DNL Assets] gebruikers te worden gedeeld, zouden zij aan de gedeelde omslag moeten worden bewogen of worden bewaard.
* **vereenvoudig het delen structuur:** voor een handelbaardere werkende werkende opstelling, denk over het vereenvoudigen van de het delen structuur. In plaats van met alle creatieve gebruikers te delen, [!DNL Assets] zouden de omslagen met teamvertegenwoordigers slechts, zoals een creatieve directeur of teammanager moeten worden gedeeld. De manager aan de creatieve kant zou definitieve activa ontvangen, over werktaken beslissen, en dan ontwerpers laten in hun eigen rekeningen van het Creative Cloud op activa van het WIP werken. Ze kunnen de samenwerkingsfuncties van Creatives Cloud gebruiken om het werk te coördineren, en ten slotte elementen selecteren en plaatsen die klaar zijn om weer naar [!DNL Assets] te delen in hun creatieve, klare gedeelde map.

In het volgende diagram ziet u een voorbeeldconfiguratie voor het maken van ontwerpen op basis van bestaande definitieve elementen van [!DNL Assets] .

![ chlimage_1-180 ](assets/chlimage_1-407.png)
