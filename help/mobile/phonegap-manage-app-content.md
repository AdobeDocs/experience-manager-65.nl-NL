---
title: App-inhoud maken en beheren
description: Voor het beheren van app-inhoud is een gezamenlijke inspanning van ontwikkelaars, auteurs van inhoud en beheerders vereist. Auteurs bewerken pagina's op basis van sjablonen en componenten die door ontwikkelaars van apps worden gegenereerd.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: authoring-adobe-phonegap-enterprise
exl-id: 9d350935-129a-40d3-89f4-2e6f69676e5e
solution: Experience Manager
feature: Mobile
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '706'
ht-degree: 0%

---

# App-inhoud maken en beheren{#creating-and-managing-app-content}

>[!NOTE]
>
>De Adobe adviseert het gebruiken van de SPARedacteur voor projecten die op kader-gebaseerde cliënt-zijteruggeven van enige paginatoepassing (bijvoorbeeld, Reageren) vereisen. [ leer meer ](/help/sites-developing/spa-overview.md).

Het beheren van app inhoud vereist een collectieve inspanning van [ ontwikkelaars ](#developer), inhoud [ auteurs ](#author), en [ beheerders ](#administrator). Auteurs bewerken pagina&#39;s op basis van sjablonen en componenten die door ontwikkelaars van apps worden gegenereerd.

Tot slot publiceren beheerders strategisch de bijgewerkte app-inhoud.

>[!NOTE]
>
>**Vereiste**:
>
>In [ het Opstellen en het Onderhouden ](/help/sites-deploying/deploy.md), werden de ontwikkelaars vertrouwd met systeemcomponenten en malplaatjes in Adobe Experience Manager (AEM).

## De pagina-inhoudtegel beheren {#the-manage-page-content-tile}

>[!CAUTION]
>
>Als u geen out-of-the-box toepassingsmalplaatje gebruikt, om nieuwe toepassingsinhoud toe te laten om OTA worden gepubliceerd, moet u een manager van de Synchronisatie van de Inhoud vormen.
>
>Zie [ Mobiel met de Synchronisatie van de Inhoud ](/help/mobile/phonegap-contentsync.md) in de sectie van de Ontwikkelaar voor meer details.

Hier kunt u inhoud maken, bewerken en verwijderen in AEM Mobile, net als in AEM Sites.

De **beheert de tegel van de Inhoud van de Pagina** toont het aantal pagina&#39;s van beheerde inhoud en het laatst gewijzigd voor een bepaalde nuttige lading. U kunt inhoud inroepen om pagina&#39;s te maken, kopiëren, verplaatsen, verwijderen en bijwerken door op elke record in de tegel te klikken.

Zodra de inhoud is bijgewerkt, kunnen de beheerders een ladload van de inhoudsupdate over-de-Luchtvaart (OTA) aan klanten door de **publiceren beheert de tegel van de Pakketten van de Inhoud.**

![ chlimage_1-161 ](assets/chlimage_1-161.png)

Selecteer een van de weergegeven inhoudspakketten om inhoud te maken of te bewerken, zoals het maken, bewerken of verwijderen van pagina&#39;s, het wijzigen van de navigatie en de paginavolgorde, het maken of bijwerken van inhoud zoals kopiëren (tekst) en media.

Nota *alles is inhoud*, betekenend toepassingsstijlen, exemplaar (tekst), media, pagina&#39;s, navigatie en, richten van inhoud kan allen worden uitgegeven en worden bijgewerkt OTA, zonder een reis aan een toepassingsopslag.

Om de inhoud van AEM Mobile uit te geven, *AEM auteurs *zal een stevig inzicht in AEM inhoud het uitgeven interface nodig hebben: [ Authoring pagina&#39;s in AEM.](/help/sites-authoring/qg-page-authoring.md)

## De tegel Inhoud-pakketten beheren {#the-manage-content-packages-tile}

Hier, *AEM Beheerders* kunnen hun apps snel en gemakkelijk bijwerken om het aansprekende ervaringen en bijgewerkte inhoud te leveren om merkbetrokkenheid te drijven en bedrijfsdoelstellingen te ontmoeten allen zonder de behoefte aan een ontwikkelaar of een App store opnieuw voorlegging.

![ chlimage_1-162 ](assets/chlimage_1-162.png)

Zodra *AEM de Auteurs* inhoud door Manage Content Tile hebben toegevoegd of gewijzigd, *AEM de Beheerders* kunnen die veranderingen uit aan klanten met een update van de Pakketten van de Inhoud duwen.

De actie van het Pakket van de Inhoud staat de *AEM Auteur* toe om paginacontent tot stand te brengen en uit te geven terwijl het ontwikkelingsteam veranderingen in een ontwerp en implementatie van de Toepassing van de Gastheer met inbegrip van navigatie, stijl, server-zijlogica, malplaatjes, en componenten aanbrengt en dan die veranderingen uit OTA aan klanten zonder het moeten opnieuw voorleggen aan de diverse opslag voor distributie.

**om nieuwe of bijgewerkte inhoud** te publiceren

Selecteer een inhoudspakket uit de tegel, in dit voorbeeld het Engelse pakket. Bericht dat een de dialoogdoos van de inhoudsupdate van de relevante *Configuratie van de Synchronisatie van de Inhoud* een lijst maakt. Als de toepassingsinhoud sinds een vorige update is gewijzigd, zal de status *in afwachting van* tonen, zoals hieronder getoond.

![ chlimage_1-163 ](assets/chlimage_1-163.png)

Daarna, selecteer de **actie van het Stadium** bij het hoogste recht aan het creëren van de inhoudsupdate. Voeg de juiste updategegevens toe en druk op Gereed.

![ chlimage_1-164 ](assets/chlimage_1-164.png)

De *manager van de Synchronisatie van de Inhoud* leidt dan tot de vereiste pakketten door een delta (een pakket van *te vormen slechts* wat is veranderd). Zodra dit pakket met update-inhoud is voltooid, wordt het gefaseerd bijgewerkt, zoals hieronder wordt weergegeven.

Door een update van de inhoud te organiseren, kunnen verschillende updates worden uitgevoerd voordat deze naar OTA worden gepubliceerd naar mobiele apparaten.

>[!NOTE]
>
>De gefaseerde inhoud kan worden geverifieerd met de app AEM verifiëren voordat deze wordt gepubliceerd.
>
>Zie [ Mobiele QuickStart voor AEM verifiëren ](/help/mobile/phonegap-mobile-quickstart.md) voor meer details over AEM verifieer app.

![ chlimage_1-165 ](assets/chlimage_1-165.png)

Wanneer klaar om nieuwe inhoud aan uw toepassingsgebruikers met de Synchronisatie van de Inhoud OTA te leveren, uitgezochte **Publish** zoals hieronder getoond.

![ chlimage_1-166 ](assets/chlimage_1-166.png)

### De volgende stappen {#the-next-steps}

Zodra u over het Creëren van en het Leiden de Inhoud van de Toepassing in het toepassingsdashboard hebt geleerd, zie de volgende middelen voor andere auteursrollen:

* [De app-tegel beheren](/help/mobile/phonegap-app-details-tile.md)
* [App-metagegevens bewerken](/help/mobile/phonegap-editmetadata.md)
* [Toepassingsdefinities](/help/mobile/phonegap-app-definitions.md)
* [Een nieuwe app maken met de wizard App maken](/help/mobile/phonegap-create-new-app.md)
* [Een bestaande hybride app importeren](/help/mobile/phonegap-adding-content-to-imported-app.md)

### Aanvullende bronnen {#additional-resources}

Meer informatie over de rollen en verantwoordelijkheden van een Beheerder en Ontwikkelaar vindt u in de volgende bronnen:

* [Ontwikkelen voor Adobe PhoneGap Enterprise met AEM](/help/mobile/developing-in-phonegap.md)
* [Inhoud voor Adobe PhoneGap Enterprise beheren met AEM](/help/mobile/administer-phonegap.md)
