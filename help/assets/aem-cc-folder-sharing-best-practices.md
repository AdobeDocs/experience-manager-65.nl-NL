---
title: Mappen delen naar  [!DNL Adobe Creative Cloud] aanbevolen werkwijzen
description: Configureer [!DNL Adobe Experience Manager] to allow users in [!DNL Experience Manager Assets] om mappen uit te wisselen met gebruikers van Adobe Creative Cloud (CC).
contentOwner: AG
translation-type: tm+mt
source-git-commit: 18e62f8fb46de20e1668b2dcdcedf68fe4622b50
workflow-type: tm+mt
source-wordcount: '954'
ht-degree: 0%

---


# [!DNL Adobe Experience Manager] naar gedeelde  [!DNL Adobe Creative Cloud] map  {#aem-to-creative-cloud-folder-sharing-best-practices}

>[!CAUTION]
>
>De functie [!DNL Experience Manager] tot [!DNL Creative Cloud] Mappen delen is vervangen. Adobe raadt u ten zeerste aan nieuwere mogelijkheden te gebruiken, zoals [Adobe Asset Link](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/adobe-asset-link.ug.html) of [Experience Manager desktop app](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html). Leer meer in [Experience Manager en de integratie van de Creative Cloud beste praktijken](/help/assets/aem-cc-integration-best-practices.md).

[!DNL Adobe Experience Manager] Kan zo worden geconfigureerd dat gebruikers in  [!DNL Assets] de app mappen kunnen delen met de gebruikers van  [!DNL Adobe Creative Cloud] apps, zodat ze beschikbaar zijn als gedeelde mappen in de  [!DNL Adobe Creative Cloud] elementenservice. De functie kan worden gebruikt om bestanden uit te wisselen tussen creatieve teams en [!DNL Assets]-gebruikers, vooral wanneer creatieve gebruikers geen toegang hebben tot de [!DNL Assets]-implementatie (ze bevinden zich niet op het bedrijfsnetwerk).

Dit type integratie kan in de volgende gebruiksgevallen worden gebruikt, vooral wanneer het werken met gebruikers die geen directe toegang tot [!DNL Assets] hebben:

* [!DNL Assets] gebruikers delen een reeks specifieke digitale elementen met gebruikers van  [!DNL Adobe Creative Cloud] bestanden ( bijvoorbeeld een creatieve samenvatting en een set goedgekeurde middelen voor ontwerpwerkzaamheden voor een nieuwe marketingactiviteit ) .
* [!DNL Assets] gebruikers ontvangen nieuwe bestanden die door  [!DNL Adobe Creative Cloud] gebruikers van de app zijn gemaakt.

>[!NOTE]
>
>Voordat u dit document leest, kunt u de algemene [best practices voor Experience Manager- en Creative Cloud-integratie doornemen](/help/assets/aem-cc-integration-best-practices.md) voor een overzicht van de integratie.

## Overzicht {#overview}

[!DNL Experience Manager] voor het delen van  [!DNL Creative Cloud] mappen afhankelijk van het delen van mappen en bestanden tussen  [!DNL Assets] en  [!DNL Creative Cloud] accounts op de server. Creatieve professionals die de [!DNL Creative Cloud]-bureaubladtoepassing op hun desktops gebruiken, kunnen de gedeelde mappen bovendien rechtstreeks op hun schijven beschikbaar stellen met behulp van [!DNL Adobe CreativeSync]-technologie.

Het volgende diagram geeft een overzicht van de integratie.

![chlimage_1-179](assets/chlimage_1-406.png)

De integratie omvat de volgende elementen:

* **[!DNL Experience Manager Assets]** opgesteld in het ondernemingsnetwerk (beheerde diensten of op-gebouw): Hier wordt het delen van mappen gestart.
* **[!DNL Adobe Marketing Cloud Assets]kernservice**: Handelt als tussenpersoon tussen  [!DNL Experience Manager] en  [!DNL Creative Cloud] opslagdiensten. Een beheerder van een organisatie die de integratie gebruikt, moet een vertrouwensrelatie tot stand brengen tussen de organisatie van de Marketing Cloud en de [!DNL Assets]-implementatie. Zij [bepalen ook een lijst van erkende Creative Cloud medewerkers](https://experienceleague.adobe.com/docs/core-services/interface/assets/t-admin-add-cc-user.html), die [!DNL Assets] gebruikers omslagen voor extra veiligheid kunnen ook delen.

* **[!DNL Creative Cloud]Webservices**  voor middelen (interface voor opslag en  [!DNL Creative Cloud] bestanden): In dit geval kunnen specifieke gebruikers van een Creative Cloud-app, met wie een  [!DNL Assets] map werd gedeeld, de uitnodiging accepteren en de map bekijken in de opslag van hun Creative Cloud-account.
* **Creative Cloud-bureaubladtoepassing**: (Optioneel) Hiermee hebt u rechtstreeks toegang tot gedeelde mappen/bestanden vanaf het bureaublad van de creatieve gebruiker via synchronisatie met de opslag van  [!DNL Creative Cloud] middelen.

## Kenmerken en beperkingen {#characteristics-and-limitations}

* **Eenvoudige doorgave van wijzigingen:** Bestandswijzigingen worden alleen in één richting doorgegeven - vanuit het systeem ([!DNL Experience Manager] of  [!DNL Creative Cloud Assets]) waar het element oorspronkelijk is gemaakt (geüpload). De integratie biedt geen volledig geautomatiseerde, tweezijdige synchronisatie tussen de twee systemen.
* **Versioning:**

   * [!DNL Experience Manager] maakt alleen versies van een element bij updates als het bestand daar oorspronkelijk  [!DNL Experience Manager] en daar bijgewerkt is.
   * [!DNL Creative Cloud] De activa verstrekt zijn eigen  [versioning ](https://helpx.adobe.com/creative-cloud/help/versioning-faq.html) eigenschap die op Werk in uitvoering updates (hoofdzakelijk, slaat updates tot 10 dagen op) wordt gericht

* **Ruimtebeperkingen:** Grootte en volumes van uitgewisselde bestanden worden beperkt door het specifieke quotum voor  [ ](https://helpx.adobe.com/creative-cloud/kb/file-storage-quota.html) Creative Cloud-middelen voor creatieve gebruikers (afhankelijk van het abonnementsniveau) en een beperking van de maximale bestandsgrootte van 5 GB. De ruimte wordt bovendien beperkt door de quota van de activa die de organisatie in de kerndienst van Adobe Marketing Cloud Assets heeft.

* **Ruimtevereisten:** De bestanden in gedeelde mappen moeten ook fysiek worden opgeslagen in  [!DNL Experience Manager] en vervolgens in  [!DNL Creative Cloud] account, met een kopie in cache in de  [!DNL Marketing Cloud Assets] kernservice.
* **Netwerk en bandbreedte:** De bestanden in gedeelde mappen en alle updates moeten via het netwerk tussen de systemen worden getransporteerd. Zorg ervoor dat alleen relevante bestanden en updates worden gedeeld.
* **Maptype**: Het delen van een  [!DNL Assets] map van het type  `sling:OrderedFolder`, wordt niet ondersteund in de context van delen in  [!DNL Adobe Marketing Cloud]. Selecteer de optie [!UICONTROL Ordered] niet als u een map wilt delen wanneer u deze maakt in [!DNL Assets].

## Aanbevolen werkwijzen {#best-practices}

De beste werkwijzen voor het gebruiken van [!DNL Experience Manager] aan [!DNL Creative Cloud] omslag het delen omvatten:

* **Overwegingen bij het volume:** [!DNL Experience Manager] en delen van  [!DNL Creative Cloud] mappen moeten worden gebruikt om een kleiner aantal bestanden te delen, bijvoorbeeld voor een specifieke campagne of activiteit. Om grotere reeksen activa, zoals alle goedgekeurde activa in de organisatie te delen, gebruik andere distributiemethodes (bijvoorbeeld, [!DNL Assets Brand Portal]) of [!DNL Experience Manager] Desktop app.
* **Vermijd het delen van diepe hiërarchieën:** het delen werkt recursief en staat niet voor selectieve unsharing toe. Gewoonlijk worden alleen mappen zonder submappen of met een zeer oppervlakkige hiërarchie, zoals 1 submapniveau, beschouwd als gedeelde mappen.
* **Afzonderlijke mappen voor delen in één richting:** Afzonderlijke mappen moeten worden gebruikt voor het delen van definitieve bestanden van  [!DNL Assets] naar  [!DNL Creative Cloud] bestanden en voor het delen van creatieve middelen van  [!DNL Creative Cloud] bestanden naar  [!DNL Assets]. Samen met een goede noemende overeenkomst voor deze omslagen, leidt het tot een gemakkelijker te begrijpen het werk milieu voor [!DNL Assets] en [!DNL Creative Cloud] gebruikers zowel.
* **WIP in de gedeelde map vermijden:** Gedeelde map mag niet worden gebruikt voor Werk in uitvoering - gebruik een aparte map in Creative Cloud-bestanden om werk uit te voeren waarvoor regelmatig wijzigingen in het bestand nodig zijn.
* **Nieuwe taken starten buiten de gedeelde map:** Nieuwe ontwerpen (creatieve bestanden) moeten worden gestart in de aparte WIP-map in Creative Cloud-bestanden en wanneer deze klaar zijn om te worden gedeeld met  [!DNL Assets] gebruikers, moeten ze worden verplaatst of opgeslagen naar de gedeelde map.
* **Vereenvoudig het delen structuur:** voor een meer handelbare werkende opstelling, denk over het vereenvoudigen van de het delen structuur. In plaats van met alle creatieve gebruikers te delen, [!DNL Assets] zouden de omslagen met teamvertegenwoordiger(s) slechts, zoals een creatieve directeur of teammanager moeten worden gedeeld. De manager aan de creatieve kant zou definitieve activa ontvangen, over werktaken beslissen, en dan ontwerpers laten in hun eigen rekeningen van de Creative Cloud werken over activa WIP. Ze kunnen de samenwerkingsfuncties van Creative Cloud gebruiken om het werk te coördineren en ten slotte elementen selecteren en plaatsen die klaar zijn om weer te worden gedeeld naar [!DNL Assets] in hun creatief-klaar gedeelde map.

Het volgende diagram illustreert een voorbeeldconfiguratie voor het creëren van nieuwe ontwerpen die op bestaande definitieve activa van [!DNL Assets] worden gebaseerd.

![chlimage_1-180](assets/chlimage_1-407.png)
