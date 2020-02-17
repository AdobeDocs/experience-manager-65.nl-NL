---
title: Activiteitsstroom in tijdlijn
description: In dit artikel wordt beschreven hoe u activiteitenlogboeken voor elementen op de tijdlijn kunt weergeven.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0ff23556444fcb161b0adf744bb72fdc50322d92

---


# Activiteitsstroom in tijdlijn {#activity-stream-in-timeline}

Deze functie geeft activiteitenlogboeken voor elementen op de tijdlijn weer. Als u een van de volgende elementgerelateerde bewerkingen uitvoert in Adobe Experience Manager (AEM) Assets, werkt de functie voor de activiteitsstroom de tijdlijn bij met de activiteit.

De volgende bewerkingen worden in de activiteitsstroom aangemeld:

* Maken
* Verwijderen
* Downloaden (inclusief uitvoeringen)
* Publiceren
* Publiceren ongedaan maken
* Goedkeuren
* Afwijzen
* Verplaatsen

De activiteitenlogboeken die in de chronologie moeten worden getoond worden opgehaald van de plaats `/var/audit/com.day.cq.dam/content/dam` in CRX, waar de logboekdossiers worden opgeslagen.  Bovendien wordt de tijdlijnactiviteit vastgelegd wanneer nieuwe elementen worden geüpload of bestaande elementen worden gewijzigd en gecontroleerd in AEM via de [Adobe Asset Link](https://helpx.adobe.com/enterprise/using/manage-assets-using-adobe-asset-link.html) of de AEM-bureaubladtoepassing [](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/release-notes.html).

>[!NOTE]
>
>Tijdelijke workflows worden niet weergegeven in de tijdlijn, omdat er voor deze workflows geen historiegegevens worden opgeslagen.

Als u de activiteitsstroom wilt weergeven, voert u een of meer bewerkingen uit op het element, selecteert u het element en kiest u vervolgens **[!UICONTROL Tijdlijn]** in de lijst GlobalNav.

![timeline-2](assets/timeline-2.png)

De tijdlijn geeft de activiteitsstroom weer voor de bewerkingen die u uitvoert op de elementen.

![activity_stream](assets/activity_stream.png)

>[!NOTE]
>
>De standaardopslaglocatie voor logbestanden voor **[!UICONTROL publicatie]** - en **[!UICONTROL Unpublish]** -taken is `/var/audit/com.day.cq.replication/content`. Voor **[!UICONTROL Verplaatsen]** is de standaardlocatie `/var/audit/com.day.cq.wcm.core.page`.
