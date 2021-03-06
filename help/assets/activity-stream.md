---
title: Activiteitsstroom van digitale elementen in de tijdlijnweergave
description: In dit artikel wordt beschreven hoe u activiteitenlogboeken voor elementen op de tijdlijn kunt weergeven.
contentOwner: AG
feature: Beheer van bedrijfsmiddelen
role: User, Admin
exl-id: 28dc0aa5-f2be-4e27-b7d8-415569b7ecd4
source-git-commit: bb46b0301c61c07a8967d285ad7977514efbe7ab
workflow-type: tm+mt
source-wordcount: '213'
ht-degree: 18%

---

# Activiteitsstroom in tijdlijn {#activity-stream-in-timeline}

Deze functie geeft activiteitenlogboeken voor elementen op de tijdlijn weer. Als u een van de volgende bewerkingen met betrekking tot elementen uitvoert in [!DNL Adobe Experience Manager Assets], werkt de functie voor de activiteitsstroom de tijdlijn bij om de activiteit weer te geven.

De volgende bewerkingen worden in de activiteitsstroom aangemeld:

* Maken
* Verwijderen
* Downloaden (inclusief uitvoeringen)
* Publicatie
* Publiceren ongedaan maken
* Goedkeuren
* Afwijzen
* Verplaatsen

De activiteitenlogboeken die in de tijdlijn moeten worden weergegeven, worden opgehaald vanaf de locatie `/var/audit/com.day.cq.dam/content/dam` in CRX, waar logboekbestanden worden opgeslagen. Bovendien wordt de tijdlijnactiviteit geregistreerd wanneer nieuwe activa worden geupload of bestaande activa worden gewijzigd en in [!DNL Experience Manager] via [Adobe Activa Link](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/manage-assets-using-adobe-asset-link.ug.html) of [Experience Manager Desktop app](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/release-notes.html) worden gecontroleerd.

>[!NOTE]
>
>Tijdelijke workflows worden niet weergegeven in de tijdlijn, omdat er voor deze workflows geen historiegegevens worden opgeslagen.

Als u de activiteitsstroom wilt weergeven, voert u een of meer bewerkingen uit op het element, selecteert u het element en kiest u **[!UICONTROL Timeline]** in de lijst GlobalNav.

![timeline-2](assets/timeline-2.png)

De tijdlijn geeft de activiteitsstroom weer voor de bewerkingen die u uitvoert op de elementen.

![activity_stream](assets/activity_stream.png)

>[!NOTE]
>
>De standaardopslaglocatie voor logboekbestanden voor de taken **[!UICONTROL Publish]** en **[!UICONTROL Unpublish]** is `/var/audit/com.day.cq.replication/content`. Voor de taken **[!UICONTROL Move]** is de standaardlocatie `/var/audit/com.day.cq.wcm.core.page`.
