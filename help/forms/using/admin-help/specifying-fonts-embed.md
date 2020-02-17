---
title: Te insluiten fonts opgeven
seo-title: Te insluiten fonts opgeven
description: Leer hoe u fonts kunt opgeven die u wilt insluiten.
seo-description: Leer hoe u fonts kunt opgeven die u wilt insluiten.
uuid: 97de6f98-ed3b-4a93-854a-193a967b4672
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 4c83694c-b00f-40be-9ac4-f5785cd60741
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Te insluiten fonts opgeven {#specifying-fonts-to-embed}

U kunt opgeven welke fonts altijd worden ingesloten of nooit worden ingesloten met de formulieren die de service Forms genereert. Als u fonts insluit, neemt de bestandsgrootte van de formulieren toe. Ongebruikelijke lettertypen die gebruikers zelden op hun systeem hebben, insluiten. Sluit geen algemene lettertypen in die ze doorgaans hebben geïnstalleerd.

>[!NOTE]
>
>Als u een aangepast XCI-bestand hebt opgegeven voor Forms, overschrijft de optie voor het insluiten van lettertypen in het XCI-bestand deze instellingen. (Zie Locaties [configureren voor Forms](/help/forms/using/admin-help/configuring-locations-forms.md#configuring-locations-for-forms).)

1. Klik in de beheerconsole op **[!UICONTROL Services > Formulieren]**.
1. Typ onder Instellingen **** Lettertype insluiten in het vak **[!UICONTROL Fonts]** altijd insluiten de namen van de fonts die u wilt insluiten met de formulieren, gescheiden door komma&#39;s. De fonts die u opgeeft, worden alleen ingesloten in het gegenereerde formulier als ze in het formulier worden gebruikt. Deze instelling wordt genegeerd als de optie Lettertype insluiten is ingeschakeld in het XCI-bestand dat aan de service is doorgegeven, omdat in dat geval alle lettertypen die in de PDF worden gebruikt, altijd worden ingesloten.
1. Typ in het vak **[!UICONTROL Fonts]** nooit insluiten de namen van de fonts die u niet wilt insluiten met de formulieren, gescheiden door komma&#39;s. De fonts die u opgeeft, worden niet ingesloten in de PDF, zelfs niet als ze worden gebruikt in de gegenereerde PDF. Deze instelling wordt genegeerd als de optie voor het insluiten van lettertypen is uitgeschakeld in het XCI-bestand dat aan de service is doorgegeven, omdat in dat geval geen van de in de PDF gebruikte lettertypen is ingesloten.
1. Click **[!UICONTROL Save]**.

