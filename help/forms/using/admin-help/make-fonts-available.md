---
title: Lettertypen beschikbaar maken
seo-title: Lettertypen beschikbaar maken
description: Zorg ervoor dat de fonts die in een formulier worden gebruikt, beschikbaar zijn voor gebruik op de J2EE-toepassingsserver die als host fungeert voor AEM-formulieren.
seo-description: Zorg ervoor dat de fonts die in een formulier worden gebruikt, beschikbaar zijn voor gebruik op de J2EE-toepassingsserver die als host fungeert voor AEM-formulieren.
uuid: 6588b4b6-f866-4253-91c8-3aa174340e8c
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 9f58a6c4-3190-49d4-800c-4a55dca7c296
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Lettertypen beschikbaar maken {#make-fonts-available}

Zorg ervoor dat de fonts die in een formulier worden gebruikt, beschikbaar zijn voor gebruik op de J2EE-toepassingsserver die als host fungeert voor AEM-formulieren. Neem bijvoorbeeld het volgende scenario. Een formulierontwerper voegt een font toe aan de fontmap die door Designer wordt gebruikt en maakt een formulier dat dat font gebruikt op een aparte computer. Plaats het lettertype in de lettertypenmap van de klant, zodat de Output-service het lettertype kan gebruiken. Als de map met lettertypen voor de klant niet bestaat, maakt u een directory op de J2EE-toepassingsserver die als host fungeert voor AEM-formulieren.

Zie Algemene AEM-formulierinstellingen [configureren voor informatie over extra lettertype-instellingen](/help/forms/using/admin-help/configure-general-aem-forms-settings.md#configure-general-aem-forms-settings).

**De locatie van de map met lettertypen voor de klant opgeven**

1. Klik in de beheerconsole op Instellingen > Core Systems Settings > Configurations.
1. Typ in het vak Locatie van de map Systeemlettertypen het pad naar de map Klantlettertypen. U kunt meerdere mappen toevoegen, gescheiden door een puntkomma **;**
1. Klik op OK.
1. Start het systeem opnieuw waarop AEM-formulieren zijn geïnstalleerd.

>[!NOTE]
>
>De lettertypen worden gekozen uit de cache van het Windows-systeemlettertype en het systeem moet opnieuw worden opgestart om de cache bij te werken. Nadat u de lettertypemap voor de klant hebt opgegeven, dient u het systeem waarop AEM-formulieren zijn geïnstalleerd opnieuw te starten.

