---
title: Lettertypen beschikbaar maken
description: Zorg ervoor dat de fonts die in een formulier worden gebruikt, beschikbaar zijn voor gebruik op de J2EE-toepassingsserver waarop AEM formulieren worden gehost.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: e9eae896-b1e4-4caa-b466-ac8c9e7416a4
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: 6a9806d8f40f711a610c130c63d9ab9b2460d075
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---

# Lettertypen beschikbaar maken {#make-fonts-available}

>[!NOTE]
> 
> Zorg ervoor dat de gebruiker beheerdersrechten heeft om toegang te krijgen tot de beheerdersconsole.

Zorg ervoor dat de fonts die in een formulier worden gebruikt, beschikbaar zijn voor gebruik op de J2EE-toepassingsserver waarop AEM formulieren worden gehost. Neem bijvoorbeeld het volgende scenario. Een formulierontwerper voegt een lettertype toe aan de lettertypemap die door Designer wordt gebruikt en maakt een formulier dat dat lettertype gebruikt op een andere computer. Plaats het lettertype in de lettertypenmap van de klant, zodat de Output-service het lettertype kan gebruiken. Als de map met lettertypen van de klant niet bestaat, maakt u een directory op de J2EE-toepassingsserver waarop AEM formulieren worden gehost.

Voor informatie over extra doopvontmontages, zie [ algemene AEM vormmontages ](/help/forms/using/admin-help/configure-general-aem-forms-settings.md#configure-general-aem-forms-settings) vormen.

**specificeer de plaats van de folder van de doopvonten van de Klant**

1. Klik in de beheerconsole op Instellingen > Core Systems Settings > Configurations.
1. Typ in het vak Locatie van de map Systeemlettertypen het pad naar de map Klantlettertypen. U kunt meerdere mappen toevoegen, gescheiden door een puntkomma **;**
1. Klik op OK.
1. Start het systeem opnieuw waarop AEM formulieren zijn geïnstalleerd.

>[!NOTE]
>
>De lettertypen worden gekozen uit de cache van het Windows-systeemlettertype en het systeem moet opnieuw worden opgestart om de cache bij te werken. Nadat u de lettertypemap voor de klant hebt opgegeven, dient u het systeem waarop AEM formulieren zijn geïnstalleerd opnieuw te starten.
