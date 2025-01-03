---
title: Te insluiten fonts opgeven
description: Leer hoe u fonts kunt opgeven die u wilt insluiten in een adaptief formulier. U kunt opgeven welke lettertypen worden ingesloten of nooit worden ingesloten met formulieren die door Forms Service worden gegenereerd.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: b2cbf5f3-ee13-47bf-bf7f-f6a1884cee66
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: 6a9806d8f40f711a610c130c63d9ab9b2460d075
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# Te insluiten fonts opgeven {#specifying-fonts-to-embed}

>[!NOTE]
> 
> Zorg ervoor dat de gebruiker beheerdersrechten heeft om toegang te krijgen tot de beheerdersconsole.

U kunt opgeven welke lettertypen altijd worden ingesloten of nooit worden ingesloten met de formulieren die de Forms-service genereert. Als u fonts insluit, neemt de bestandsgrootte van de formulieren toe. Ongebruikelijke lettertypen die gebruikers zelden op hun systeem hebben, insluiten. Sluit geen algemene lettertypen in die ze doorgaans hebben geïnstalleerd.

>[!NOTE]
>
>Als u een aangepast XCI-bestand hebt opgegeven voor Forms, overschrijft de optie voor het insluiten van lettertypen in het XCI-bestand deze instellingen. (Zie [ het Vormen plaatsen voor Forms ](/help/forms/using/admin-help/configuring-locations-forms.md#configuring-locations-for-forms).)

1. Klik in de beheerconsole op **[!UICONTROL Services > Forms]** .
1. Typ in het vak **[!UICONTROL Always Embed Fonts]** onder **[!UICONTROL Font Embedding Settings]** de namen van de fonts die u wilt insluiten met de formulieren, gescheiden door komma&#39;s. De fonts die u opgeeft, worden alleen ingesloten in het gegenereerde formulier als ze in het formulier worden gebruikt. Deze instelling wordt genegeerd als de optie voor het insluiten van lettertypen is ingeschakeld in het XCI-bestand dat aan de service is doorgegeven, omdat in dat geval alle lettertypen die in de PDF worden gebruikt, altijd worden ingesloten.
1. Typ in het vak **[!UICONTROL Never Embed Fonts]** de namen van de fonts die u niet wilt insluiten met de formulieren, gescheiden door komma&#39;s. De lettertypen die u opgeeft, worden niet ingesloten in de PDF, zelfs niet als ze worden gebruikt in de gegenereerde PDF. Deze instelling wordt genegeerd als de optie voor het insluiten van lettertypen is uitgeschakeld in het XCI-bestand dat aan de service is doorgegeven, omdat in dat geval geen van de lettertypen die in de PDF worden gebruikt, zijn ingesloten.
1. Klik op **[!UICONTROL Save]**.
