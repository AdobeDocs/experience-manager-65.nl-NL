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
>De Adobe adviseert het gebruiken van de SPARedacteur voor projecten die op kader-gebaseerde cliënt-zijteruggeven van enige paginatoepassing (bijvoorbeeld, Reageren) vereisen. [Meer informatie](/help/sites-developing/spa-overview.md).

Voor het beheren van app-inhoud is een gezamenlijke inspanning vereist van [ontwikkelaars](#developer), inhoud [auteurs](#author), en [beheerders](#administrator). Auteurs bewerken pagina&#39;s op basis van sjablonen en componenten die door ontwikkelaars van apps worden gegenereerd.

Tot slot publiceren beheerders strategisch de bijgewerkte app-inhoud.

>[!NOTE]
>
>**Vereiste**:
>
>In [Implementeren en onderhouden](/help/sites-deploying/deploy.md)Ontwikkelaars werden vertrouwd met systeemcomponenten en sjablonen in Adobe Experience Manager (AEM).

## De pagina-inhoudtegel beheren {#the-manage-page-content-tile}

>[!CAUTION]
>
>Als u geen out-of-the-box toepassingsmalplaatje gebruikt, om nieuwe toepassingsinhoud toe te laten om OTA worden gepubliceerd, moet u een manager van de Synchronisatie van de Inhoud vormen.
>
>Zie [Mobiel met inhoudssynchronisatie](/help/mobile/phonegap-contentsync.md) in de sectie Ontwikkelaar voor meer informatie.

Hier kunt u inhoud maken, bewerken en verwijderen in AEM Mobile, net als in AEM Sites.

De **Tile voor pagina-inhoud beheren** Hiermee geeft u het aantal pagina&#39;s van beheerde inhoud weer en de laatste pagina voor een bepaalde lading. U kunt inhoud inroepen om pagina&#39;s te maken, kopiëren, verplaatsen, verwijderen en bijwerken door op elke record in de tegel te klikken.

Als de inhoud eenmaal is bijgewerkt, kunnen beheerders via de **De tegel Inhoud verpakken beheren.**

![chlimage_1-161](assets/chlimage_1-161.png)

Selecteer een van de weergegeven inhoudspakketten om inhoud te maken of te bewerken, zoals het maken, bewerken of verwijderen van pagina&#39;s, het wijzigen van de navigatie en de paginavolgorde, het maken of bijwerken van inhoud zoals kopiëren (tekst) en media.

Opmerking *alles is inhoud*, dat wil zeggen toepassingsstijlen, kopiëren (tekst), media, pagina&#39;s, navigatie en, het richten van inhoud kunnen allen worden uitgegeven en worden bijgewerkt OTA, zonder een reis aan een toepassingsopslag.

*AEM auteurs *hebben een gedegen kennis van AEM interface voor het bewerken van inhoud nodig om AEM Mobile-inhoud te kunnen bewerken: [Ontwerppagina&#39;s in AEM.](/help/sites-authoring/qg-page-authoring.md)

## De tegel Inhoud-pakketten beheren {#the-manage-content-packages-tile}

Hier, *AEM* kunnen hun apps snel en gemakkelijk bijwerken om boeiende ervaringen en actuele inhoud te bieden om de betrokkenheid van merken te stimuleren en zakelijke doelen te halen, zonder dat een ontwikkelaar of app store opnieuw hoeft te worden ingediend.

![chlimage_1-162](assets/chlimage_1-162.png)

Eenmaal *Auteurs AEM* inhoud hebben toegevoegd of gewijzigd via de Content Tile beheren, *AEM* kunnen deze wijzigingen doorsturen naar klanten met een Content Packages-update.

Met de actie Inhoudspakket kan de *AEM auteur* om paginacontent tot stand te brengen en uit te geven terwijl het ontwikkelingsteam veranderingen in een ontwerp en implementatie van de Toepassing van de Gastheer met inbegrip van navigatie, stijl, server-zijlogica, malplaatjes, en componenten aanbrengt en dan die veranderingen uit OTA aan klanten duwt zonder aan de diverse opslag voor distributie opnieuw voor te leggen.

**Nieuwe of bijgewerkte inhoud publiceren**

Selecteer een inhoudspakket uit de tegel, in dit voorbeeld het Engelse pakket. Een dialoogvenster voor het bijwerken van inhoud bevat de relevante *Inhoud synchroniseren* configuratie. Als de inhoud van de app sinds een vorige update is gewijzigd, wordt de status weergegeven *In behandeling*, zoals hieronder weergegeven.

![chlimage_1-163](assets/chlimage_1-163.png)

Selecteer vervolgens de **Werkgebied** actie helemaal rechts boven om de inhoud bij te werken. Voeg de juiste updategegevens toe en druk op Gereed.

![chlimage_1-164](assets/chlimage_1-164.png)

De *Inhoud synchroniseren* handler maakt vervolgens de vereiste pakketten door een delta te vormen (een pakket van *alleen* wat is veranderd). Zodra dit pakket met update-inhoud is voltooid, wordt het gefaseerd bijgewerkt, zoals hieronder wordt weergegeven.

Door een update van de inhoud te organiseren, kunnen verschillende updates worden uitgevoerd voordat deze naar OTA worden gepubliceerd naar mobiele apparaten.

>[!NOTE]
>
>De gefaseerde inhoud kan worden geverifieerd met de app AEM verifiëren voordat deze wordt gepubliceerd.
>
>Zie [Mobile QuickStart voor AEM verifiëren](/help/mobile/phonegap-mobile-quickstart.md) voor meer informatie over AEM toepassing verifiëren.

![chlimage_1-165](assets/chlimage_1-165.png)

Wanneer u klaar bent om nieuwe inhoud aan uw gebruikers van de app te leveren met Content Sync OTA, selecteert u **Publiceren** zoals hieronder weergegeven.

![chlimage_1-166](assets/chlimage_1-166.png)

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
