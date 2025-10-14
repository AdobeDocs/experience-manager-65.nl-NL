---
title: Activiteitsstroom van digitale elementen in de tijdlijnweergave
description: In dit artikel wordt beschreven hoe u activiteitenlogboeken voor elementen op de tijdlijn kunt weergeven.
contentOwner: AG
feature: Asset Management
role: User, Admin
exl-id: 28dc0aa5-f2be-4e27-b7d8-415569b7ecd4
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 7%

---

# Activiteitsstroom in tijdlijn {#activity-stream-in-timeline}

Deze functie geeft activiteitenlogboeken voor elementen op de tijdlijn weer. Als u een van de volgende bewerkingen met betrekking tot elementen uitvoert in [!DNL Adobe Experience Manager Assets] , wordt de tijdlijn door de functie voor de activiteitsstroom bijgewerkt met de activiteit.

De volgende bewerkingen worden in de activiteitsstroom aangemeld:

* Maken
* Verwijderen
* Downloaden (inclusief uitvoeringen)
* Publish
* Publiceren ongedaan maken
* Goedkeuren
* Afwijzen
* Verplaatsen

De activiteitenlogboeken die in de tijdlijn moeten worden weergegeven, worden opgehaald van de locatie `/var/audit/com.day.cq.dam/content/dam` in CRX, waar de logbestanden worden opgeslagen. Bovendien wordt de chronologieactiviteit geregistreerd wanneer de nieuwe activa worden geupload of de bestaande activa worden gewijzigd en in [!DNL Experience Manager] gecontroleerd via [&#x200B; de Verbinding van Activa van de Adobe &#x200B;](https://helpx.adobe.com/nl/enterprise/admin-guide.html/enterprise/using/manage-assets-using-adobe-asset-link.ug.html) of [&#x200B; Desktop app van de Experience Manager &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/release-notes.html?lang=nl-NL).

>[!NOTE]
>
>Tijdelijke workflows worden niet weergegeven in de tijdlijn, omdat er voor deze workflows geen historiegegevens worden opgeslagen.

Als u de activiteitsstroom wilt weergeven, voert u een of meer bewerkingen uit op het element, selecteert u het element en kiest u vervolgens **[!UICONTROL Timeline]** in de lijst GlobalNav.

![&#x200B; chronologie-2 &#x200B;](assets/timeline-2.png)

De tijdlijn geeft de activiteitsstroom weer voor de bewerkingen die u uitvoert op de elementen.

![&#x200B; activity_stream &#x200B;](assets/activity_stream.png)

>[!NOTE]
>
>De standaardopslaglocatie voor logboekbestanden voor de taken **[!UICONTROL Publish]** en **[!UICONTROL Unpublish]** is `/var/audit/com.day.cq.replication/content`. Voor de taken **[!UICONTROL Move]** is de standaardlocatie `/var/audit/com.day.cq.wcm.core.page`.
