---
title: Map delen naar [!DNL Adobe Creative Cloud] best practices
description: Configureren [!DNL Adobe Experience Manager] om gebruikers toe te staan in [!DNL Experience Manager Assets] om mappen uit te wisselen met Adobe Creative Cloud-gebruikers.
contentOwner: AG
role: User, Admin
feature: Collaboration
exl-id: 130cec6d-1cdd-4304-94bb-65e6bb573e55
source-git-commit: a76772b8761e35a828814ffe0ac3b019266ff008
workflow-type: tm+mt
source-wordcount: '957'
ht-degree: 0%

---

# [!DNL Adobe Experience Manager] tot [!DNL Adobe Creative Cloud] map delen {#aem-to-creative-cloud-folder-sharing-best-practices}

>[!CAUTION]
>
>De [!DNL Experience Manager] tot [!DNL Creative Cloud] De functie Mappen delen is vervangen. Adobe raadt sterk aan om nieuwere mogelijkheden te gebruiken, zoals [Adobe-itemkoppeling](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/adobe-asset-link.ug.html) of [Experience Manager-bureaubladtoepassing](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html). Meer informatie in [Best practices op het gebied van Experience Manager- en Creative Cloud-integratie](/help/assets/aem-cc-integration-best-practices.md).

[!DNL Adobe Experience Manager] kan worden geconfigureerd om gebruikers toe te staan in [!DNL Assets] om mappen te delen met de gebruikers van [!DNL Adobe Creative Cloud] apps, zodat ze beschikbaar zijn als gedeelde mappen in de [!DNL Adobe Creative Cloud] assetservice. De functie kan worden gebruikt om bestanden uit te wisselen tussen creatieve teams en [!DNL Assets] gebruikers, met name wanneer de creatieve gebruikers geen toegang hebben tot de [!DNL Assets] plaatsing (zij zijn niet op het ondernemingsnetwerk).

Dit type integratie kan in de volgende gebruiksgevallen worden gebruikt, vooral wanneer het werken met gebruikers die geen directe toegang tot [!DNL Assets]:

* [!DNL Assets] gebruikers delen een set specifieke digitale elementen met gebruikers van [!DNL Adobe Creative Cloud] bestanden (bijvoorbeeld een creatief overzicht en een set goedgekeurde middelen voor ontwerpwerkzaamheden voor een nieuwe marketingactiviteit).
* [!DNL Assets] gebruikers ontvangen nieuwe bestanden die zijn gemaakt door [!DNL Adobe Creative Cloud] gebruikers van de app.

>[!NOTE]
>
>Voordat u dit document leest, kunt u de algemene [Best practices op het gebied van Experience Manager- en Creative Cloud-integratie](/help/assets/aem-cc-integration-best-practices.md) voor een overzicht van de integratie.

## Overzicht {#overview}

[!DNL Experience Manager] tot [!DNL Creative Cloud] het delen van mappen is afhankelijk van het delen van mappen en bestanden tussen servers [!DNL Assets] en [!DNL Creative Cloud] rekeningen. Creatieve professionals die de [!DNL Creative Cloud] bureaubladtoepassing op hun desktops, kunnen de gedeelde mappen bovendien rechtstreeks op hun schijven beschikbaar stellen via [!DNL Adobe CreativeSync] -technologie.

Het volgende diagram geeft een overzicht van de integratie.

![chlimage_1-179](assets/chlimage_1-406.png)

De integratie omvat de volgende elementen:

* **[!DNL Experience Manager Assets]** opgesteld in het ondernemingsnetwerk (beheerde diensten of op-gebouw): Hier wordt het delen van mappen gestart.
* **[!DNL Adobe Marketing Cloud Assets]kernservice**: Handelt als tussenpersoon tussen [!DNL Experience Manager] en [!DNL Creative Cloud] opslagservices. Een beheerder van een organisatie die de integratie gebruikt moet vertrouwensrelatie tot stand brengen tussen de organisatie van de Marketing Cloud en de [!DNL Assets] implementatie. Ook [een lijst met erkende Creative Cloud-medewerkers definiëren](https://experienceleague.adobe.com/docs/core-services/interface/assets/t-admin-add-cc-user.html), dat [!DNL Assets] gebruikers kunnen ook mappen delen voor extra beveiliging.

* **[!DNL Creative Cloud]Webservices voor middelen** (opslag en [!DNL Creative Cloud] bestanden (webinterface): Dit is waar specifieke gebruikers van een Creative Cloud-app, waarmee [!DNL Assets] is gedeeld, kan de uitnodiging accepteren en de map weergeven in de opslagruimte van de Creative Cloud-account.
* **Creative Cloud-bureaubladtoepassing**: (Optioneel) Hiermee wordt directe toegang tot gedeelde mappen/bestanden mogelijk vanaf het bureaublad van de creatieve gebruiker via synchronisatie met [!DNL Creative Cloud] Elementenopslag.

## Kenmerken en beperkingen {#characteristics-and-limitations}

* **Eenvoudige doorgave van wijzigingen:** Bestandswijzigingen worden alleen in één richting doorgegeven - van het systeem ([!DNL Experience Manager] of [!DNL Creative Cloud Assets]), waar het element oorspronkelijk is gemaakt (geüpload). De integratie biedt geen volledig geautomatiseerde synchronisatie in twee richtingen tussen de twee systemen.
* **Versioning:**

   * [!DNL Experience Manager] maakt alleen versies van een element bij updates als het bestand afkomstig is uit [!DNL Experience Manager] en wordt daar bijgewerkt.
   * [!DNL Creative Cloud] Activa zijn eigen [versiefunctie](https://helpx.adobe.com/creative-cloud/help/versioning-faq.html) dat is gericht op Werk in uitvoering updates (slaat updates in principe tot 10 dagen op)

* **Ruimtebeperkingen:** Grootte en volumes van uitgewisselde bestanden worden beperkt door de specifieke [Creative Cloud Assets-quota](https://helpx.adobe.com/creative-cloud/kb/file-storage-quota.html) voor creatieve gebruikers (afhankelijk van het abonnementsniveau) en een beperking van de maximale bestandsgrootte van 5 GB. De ruimte wordt bovendien beperkt door de quota van de activa die de organisatie in de kerndienst van Adobe Marketing Cloud Assets heeft.

* **Ruimtevereisten:** De bestanden in gedeelde mappen moeten ook fysiek worden opgeslagen in [!DNL Experience Manager] en vervolgens in [!DNL Creative Cloud] account, met een kopie in cache [!DNL Marketing Cloud Assets] kerndienst.
* **Netwerken en bandbreedte:** De bestanden in gedeelde mappen en alle updates moeten via het netwerk tussen de systemen worden getransporteerd. Zorg ervoor dat alleen relevante bestanden en updates worden gedeeld.
* **Maptype**: Een [!DNL Assets] map met het type `sling:OrderedFolder`, wordt niet ondersteund in de context van delen in [!DNL Adobe Marketing Cloud]. Als u een map wilt delen, maakt u deze in [!DNL Assets], selecteer de [!UICONTROL Ordered] optie.

## Aanbevolen procedures {#best-practices}

Aanbevolen procedures voor het benutten van de [!DNL Experience Manager] tot [!DNL Creative Cloud] map delen:

* **Overwegingen voor volume:** [!DNL Experience Manager] en [!DNL Creative Cloud] Mappen delen moet worden gebruikt om een kleiner aantal bestanden te delen, bijvoorbeeld voor een specifieke campagne of activiteit. Om grotere reeksen activa, zoals alle goedgekeurde activa in de organisatie te delen, gebruik andere distributiemethodes (bijvoorbeeld [!DNL Assets Brand Portal]) of [!DNL Experience Manager] bureaubladtoepassing.
* **Vermijd het delen van diepe hiërarchieën:** Het delen werkt recursief en maakt het niet mogelijk selectief te delen. Gewoonlijk worden alleen mappen zonder submappen of met een zeer oppervlakkige hiërarchie, zoals 1 submapniveau, beschouwd als gedeelde mappen.
* **Afzonderlijke mappen voor delen in één richting:** Afzonderlijke mappen moeten worden gebruikt voor het delen van uiteindelijke middelen van [!DNL Assets] tot [!DNL Creative Cloud] bestanden, en voor het delen van creatieve middelen [!DNL Creative Cloud] bestanden naar [!DNL Assets]. Samen met een goede noemingsconventie voor deze omslagen, leidt het tot een gemakkelijker te begrijpen werkende milieu voor [!DNL Assets] en [!DNL Creative Cloud] gebruikers.
* **WIP in de gedeelde map vermijden:** Gedeelde map mag niet worden gebruikt voor Werk in uitvoering. Gebruik een aparte map in Creative Cloud-bestanden om werk uit te voeren waarvoor regelmatig wijzigingen in het bestand nodig zijn.
* **Nieuwe taken starten buiten de gedeelde map:** Nieuwe ontwerpen (creatieve bestanden) moeten worden gestart in de aparte WIP-map in Creative Cloud-bestanden en wanneer ze klaar zijn om te worden gedeeld met [!DNL Assets] gebruikers, moeten ze naar de gedeelde map worden verplaatst of opgeslagen.
* **Structuur voor delen vereenvoudigen:** Voor een beter te beheren werkende opstelling, denk over het vereenvoudigen van de het delen structuur. In plaats van met alle creatieve gebruikers te delen, [!DNL Assets] mappen mogen alleen met teamvertegenwoordigers worden gedeeld, zoals een creatieve directeur of teammanager. De manager aan de creatieve kant zou definitieve activa ontvangen, over werktaken beslissen, en dan ontwerpers laten in hun eigen rekeningen van de Creative Cloud werken over activa WIP. Zij kunnen de samenwerkingseigenschappen van Creative Cloud gebruiken om het werk te coördineren, en tenslotte activa selecteren en zetten die klaar zijn om terug te delen aan [!DNL Assets] in hun creatief-klaar gedeelde omslag.

Het volgende diagram illustreert een voorbeeldconfiguratie voor het creëren van nieuwe ontwerpen die op bestaande definitieve activa van worden gebaseerd [!DNL Assets].

![chlimage_1-180](assets/chlimage_1-407.png)
