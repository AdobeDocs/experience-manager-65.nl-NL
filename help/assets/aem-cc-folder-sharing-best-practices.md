---
title: '[!DNL Adobe Experience Manager] [!DNL Adobe Creative Cloud] aan omslag die beste praktijken deelt.'
description: Configureer [!DNL Adobe Experience Manager] to allow users in [!DNL Experience Manager Assets] om mappen uit te wisselen met gebruikers van Adobe Creative Cloud (CC).
contentOwner: AG
translation-type: tm+mt
source-git-commit: 9fc1201db83ae0d3bb902d4dc3ab6d78cc1dc251
workflow-type: tm+mt
source-wordcount: '960'
ht-degree: 0%

---


# [!DNL Adobe Experience Manager] naar [!DNL Adobe Creative Cloud] mappen delen {#aem-to-creative-cloud-folder-sharing-best-practices}

>[!CAUTION]
>
>De functie [!DNL Experience Manager] voor delen naar [!DNL Creative Cloud] map is afgekeurd. Adobe raadt u ten zeerste aan om nieuwere mogelijkheden te gebruiken, zoals [Adobe Asset Link](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html) of [Experience Manager desktop app](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/using.html). Leer meer in [Experience Manager en Creative Cloud integratie beste praktijken](/help/assets/aem-cc-integration-best-practices.md).

[!DNL Adobe Experience Manager] Kan zo worden geconfigureerd dat gebruikers in [!DNL Assets] de app mappen kunnen delen met de gebruikers van [!DNL Adobe Creative Cloud] apps, zodat ze beschikbaar zijn als gedeelde mappen in de [!DNL Adobe Creative Cloud] services assets. De functie kan worden gebruikt om bestanden uit te wisselen tussen creatieve teams en [!DNL Assets] gebruikers, vooral wanneer creatieve gebruikers geen toegang hebben tot de [!DNL Assets] implementatie (ze bevinden zich niet op het bedrijfsnetwerk).

Dit type integratie kan in de volgende gebruiksgevallen worden gebruikt, vooral wanneer het werken met gebruikers die geen directe toegang tot hebben [!DNL Assets]:

* [!DNL Assets] gebruikers delen een reeks specifieke digitale middelen met gebruikers van [!DNL Adobe Creative Cloud] dossiers (bijvoorbeeld, een creatieve samenvatting en een reeks goedgekeurde activa voor ontwerpwerk voor een nieuwe marketing activiteit).
* [!DNL Assets] gebruikers ontvangen nieuwe bestanden die door gebruikers van de [!DNL Adobe Creative Cloud] app zijn gemaakt.

>[!NOTE]
>
>Voordat u dit document leest, kunt u de algemene best practices [voor](/help/assets/aem-cc-integration-best-practices.md) Experience Manager- en Creative Cloud-integratie doornemen voor een overzicht van de integratie.

## Overzicht {#overview}

[!DNL Experience Manager] voor het delen van [!DNL Creative Cloud] mappen afhankelijk van het delen van mappen en bestanden tussen [!DNL Assets] en [!DNL Creative Cloud] accounts op de server. Creatieve professionals die de [!DNL Creative Cloud] bureaubladtoepassing op hun desktopcomputers gebruiken, kunnen de gedeelde mappen bovendien rechtstreeks op hun schijven beschikbaar stellen met behulp van [!DNL Adobe CreativeSync] technologie.

Het volgende diagram geeft een overzicht van de integratie.

![chlimage_1-179](assets/chlimage_1-406.png)

De integratie omvat de volgende elementen:

* **[!DNL Experience Manager Assets]** opgesteld in het ondernemingsnetwerk (beheerde diensten of op-gebouw): Hier wordt het delen van mappen gestart.
* **[!DNL Adobe Marketing Cloud Assets]kernservice **: Handelt als tussenpersoon tussen[!DNL Experience Manager]en[!DNL Creative Cloud]opslagdiensten. Een beheerder van een organisatie die de integratie gebruikt moet vertrouwensrelatie tussen de organisatie van de Marketing Cloud en de[!DNL Assets]plaatsing vestigen. Zij[bepalen ook een lijst van erkende medewerkers](https://docs.adobe.com/content/help/en/core-services/interface/assets/t-admin-add-cc-user.html)van Creative Cloud, die de[!DNL Assets]gebruikers omslagen voor extra veiligheid kunnen delen.

* **[!DNL Creative Cloud]Webservices **voor middelen (web-UI voor opslag en[!DNL Creative Cloud]bestanden): In dit geval kunnen specifieke gebruikers van een Creative Cloud-app, met wie een[!DNL Assets]map werd gedeeld, de uitnodiging accepteren en de map bekijken in de opslag van hun Creative Cloud-account.
* **Creative Cloud-bureaubladtoepassing**: (Optioneel) Hiermee hebt u rechtstreeks toegang tot gedeelde mappen/bestanden vanaf het bureaublad van de creatieve gebruiker via synchronisatie met de opslag [!DNL Creative Cloud] Middelen.

## Kenmerken en beperkingen {#characteristics-and-limitations}

* **Eenvoudige doorgave van wijzigingen:** Bestandswijzigingen worden alleen in één richting doorgegeven - vanuit het systeem ([!DNL Experience Manager] of [!DNL Creative Cloud Assets]) waar het element oorspronkelijk is gemaakt (geüpload). De integratie biedt geen volledig geautomatiseerde, tweezijdige synchronisatie tussen de twee systemen.
* **Versioning:**

   * [!DNL Experience Manager] maakt alleen versies van een element bij updates als het bestand daar oorspronkelijk vandaan komt [!DNL Experience Manager] en daar wordt bijgewerkt.
   * [!DNL Creative Cloud] De activa verstrekt zijn eigen [versioning eigenschap](https://helpx.adobe.com/creative-cloud/help/versioning-faq.html) die op Werk in Lopende updates (hoofdzakelijk, slaat updates tot 10 dagen op) wordt gericht

* **Ruimtebeperkingen:** Grootte en volumes van uitgewisselde bestanden worden beperkt door het specifieke quotum [voor](https://helpx.adobe.com/creative-cloud/kb/file-storage-quota.html) Creative Cloud-middelen voor creatieve gebruikers (afhankelijk van het abonnementsniveau) en een beperking van de maximale bestandsgrootte van 5 GB. De ruimte wordt bovendien beperkt door het assetquotum dat de organisatie heeft in de kernservice Adobe Marketing Cloud Assets.

* **Ruimtevereisten:** De dossiers in gedeelde omslagen moeten ook fysisch in [!DNL Experience Manager] en dan in [!DNL Creative Cloud] rekening, met een caching exemplaar in de [!DNL Marketing Cloud Assets] kerndienst worden opgeslagen.
* **Netwerken en bandbreedte:** De bestanden in gedeelde mappen en alle updates moeten via het netwerk tussen de systemen worden getransporteerd. Zorg ervoor dat alleen relevante bestanden en updates worden gedeeld.
* **Maptype**: Het delen van een [!DNL Assets] map van het type `sling:OrderedFolder`, wordt niet ondersteund in de context van delen in [!DNL Adobe Marketing Cloud]. Als u een map wilt delen, selecteert u [!DNL Assets]de [!UICONTROL Ordered] optie niet wanneer u deze maakt.

## Best practices {#best-practices}

De beste werkwijzen voor het gebruiken van [!DNL Experience Manager] aan het delen van [!DNL Creative Cloud] omslag omvatten:

* **Overwegingen voor volume:** [!DNL Experience Manager] en [!DNL Creative Cloud] Mappen delen moet worden gebruikt om een kleiner aantal bestanden te delen, bijvoorbeeld voor een specifieke campagne of activiteit. Als u grotere sets middelen wilt delen, zoals alle goedgekeurde middelen in de organisatie, gebruikt u andere distributiemethoden (bijvoorbeeld [!DNL Assets Brand Portal]) of [!DNL Experience Manager] bureaubladtoepassingen.
* **Vermijd het delen van diepe hiërarchieën:** Het delen werkt recursief en maakt het niet mogelijk selectief te delen. Gewoonlijk worden alleen mappen zonder submappen of met een zeer oppervlakkige hiërarchie, zoals 1 submapniveau, beschouwd als gedeelde mappen.
* **Afzonderlijke mappen voor delen in één richting:** Afzonderlijke mappen moeten worden gebruikt voor het delen van definitieve bestanden van [!DNL Assets] naar [!DNL Creative Cloud] bestanden en voor het delen van creatieve middelen van bestanden naar [!DNL Creative Cloud] [!DNL Assets]. Samen met een goede noemende overeenkomst voor deze omslagen, leidt het tot een gemakkelijker te begrijpen het werk milieu voor [!DNL Assets] en [!DNL Creative Cloud] gebruikers.
* **WIP in de gedeelde map vermijden:** Gedeelde map mag niet worden gebruikt voor Werk in uitvoering. Gebruik een aparte map in Creative Cloud-bestanden om werk uit te voeren waarvoor regelmatig wijzigingen in het bestand nodig zijn.
* **Nieuwe taken starten buiten de gedeelde map:** Nieuwe ontwerpen (creatieve bestanden) moeten worden gestart in de aparte WIP-map in Creative Cloud-bestanden en wanneer deze klaar zijn om te worden gedeeld met [!DNL Assets] gebruikers, moeten ze naar de gedeelde map worden verplaatst of opgeslagen.
* **Structuur voor delen vereenvoudigen:** Voor een beter te beheren werkende opstelling, denk over het vereenvoudigen van de het delen structuur. In plaats van met alle creatieve gebruikers te delen, zouden de [!DNL Assets] omslagen met teamvertegenwoordiger(s) slechts, zoals een creatieve directeur of teammanager moeten worden gedeeld. De manager aan de creatieve kant zou definitieve activa ontvangen, over werktaken beslissen, en dan ontwerpers laten in hun eigen rekeningen van de Creative Cloud werken over activa WIP. Ze kunnen de samenwerkingsfuncties van Creative Cloud gebruiken om het werk te coördineren, en ten slotte elementen selecteren en plaatsen die klaar zijn om opnieuw te delen [!DNL Assets] in hun creatief-klaar gedeelde map.

Het volgende diagram illustreert een voorbeeldconfiguratie voor het creëren van nieuwe ontwerpen die op bestaande definitieve activa van worden gebaseerd [!DNL Assets].

![chlimage_1-180](assets/chlimage_1-407.png)
