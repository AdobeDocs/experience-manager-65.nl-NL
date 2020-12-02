---
title: Basisbeginselen van formulieren configureren
seo-title: Basisbeginselen van formulieren configureren
description: Leer meer over de verschillende formulierservices die u helpen interactieve toepassingen voor het vastleggen van gegevens te maken.
seo-description: Leer meer over de verschillende formulierservices die u helpen interactieve toepassingen voor het vastleggen van gegevens te maken.
uuid: f495c170-2d17-45b0-b09d-22cce101131e
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: e87c7379-28ed-4fda-aef1-970d2b54f30d
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 0%

---


# Basisbeginselen van het configureren van formulieren {#basics-of-configuring-forms}

Met de Forms-service kunt u interactieve toepassingen voor het vastleggen van gegevens maken die formulieren valideren, verwerken, transformeren en leveren die normaal gesproken in Designer zijn gemaakt. Auteurs van formulieren ontwikkelen één formulierontwerp dat door de Forms-service in verschillende indelingen wordt weergegeven:

* als PDF in Adobe Reader of in een browser
* als HTML in verschillende browseromgevingen, inclusief een compatibele XHTML 1.0-rendering
* als formulierhulplijnen in verschillende browseromgevingen die ondersteuning bieden voor Adobe Flash Player.

Zie [Referentiehandleiding Services](https://www.adobe.com/go/learn_aemforms_services_63) voor aanvullende informatie over de Forms-service.

Met de Forms-pagina in de beheerconsole kunt u het gedrag van de Forms-service configureren. Deze instellingen zijn van toepassing op alle aanroepen van de service. Alle parameters die via de SDK voor AEM formulieren worden verzonden, overschrijven de instellingen die in de beheerconsole zijn ingesteld. zij hebben echter alleen invloed op die specifieke aanroeping .

Nadat u de Forms-instellingen in de beheerconsole hebt gewijzigd, klikt u op Opslaan. De wijzigingen worden van kracht als u de server niet opnieuw hoeft te starten. Het kan echter zijn dat u de Forms-service moet stoppen en opnieuw opstarten wanneer u de instellingen voor de cachemodus configureert. (Zie [Services starten en stoppen](/help/forms/using/admin-help/starting-stopping-services.md#starting-and-stopping-services).)
