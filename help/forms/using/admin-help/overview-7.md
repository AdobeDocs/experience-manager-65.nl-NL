---
title: Basisbeginselen van het configureren van formulieren
description: Leer meer over de verschillende formulierservices die u helpen interactieve toepassingen voor het vastleggen van gegevens te maken.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 169f3d94-ac00-41c7-853e-ecf0dbee559f
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: e821be5233fd5f6688507096790d219d25903892
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 0%

---

# Basisbeginselen van het configureren van formulieren {#basics-of-configuring-forms}

Met de Forms-service kunt u interactieve gegevensvastleggingsclienttoepassingen maken die formulieren valideren, verwerken, transformeren en leveren die gewoonlijk in Designer zijn gemaakt. Auteurs van formulieren ontwikkelen één formulierontwerp dat door de Forms-service in verschillende indelingen wordt weergegeven:

* als PDF in Adobe Reader of in een browser
* als HTML in verschillende browseromgevingen, inclusief een compatibele XHTML 1.0-rendering
* als formulierhulplijnen in verschillende browseromgevingen die Adobe Flash Player ondersteunen.

Voor extra informatie over de dienst van Forms, zie [ Verwijzing van de Diensten ](https://www.adobe.com/go/learn_aemforms_services_63).

Met de Forms-pagina in de beheerconsole kunt u het gedrag van de Forms-service configureren. Deze instellingen zijn van toepassing op alle aanroepen van de service. Alle parameters die via de SDK voor AEM formulieren worden verzonden, overschrijven de instellingen die in de beheerconsole zijn ingesteld. Ze hebben echter alleen invloed op die specifieke aanroep.

Klik op Opslaan nadat u de Forms-instellingen in de beheerconsole hebt gewijzigd. De wijzigingen worden van kracht als u de server niet opnieuw hoeft te starten. Het kan echter zijn dat u de Forms-service moet stoppen en opnieuw opstarten wanneer u de instellingen voor de cachemodus configureert. (Zie [ Beginnend en tegenhoudend de diensten ](/help/forms/using/admin-help/starting-stopping-services.md#starting-and-stopping-services).)
