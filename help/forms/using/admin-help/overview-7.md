---
title: Basisbeginselen van formulieren configureren
seo-title: Basics of configuring forms
description: Leer meer over de verschillende formulierservices die u helpen interactieve toepassingen voor het vastleggen van gegevens te maken.
seo-description: Learn about the various forms services that help you create interactive data capture applications.
uuid: f495c170-2d17-45b0-b09d-22cce101131e
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: e87c7379-28ed-4fda-aef1-970d2b54f30d
exl-id: 169f3d94-ac00-41c7-853e-ecf0dbee559f
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 0%

---

# Basisbeginselen van formulieren configureren {#basics-of-configuring-forms}

Met de Forms-service kunt u interactieve toepassingen voor het vastleggen van gegevens maken die formulieren valideren, verwerken, transformeren en leveren die normaal gesproken in Designer zijn gemaakt. Auteurs van formulieren ontwikkelen één formulierontwerp dat door de Forms-service in verschillende indelingen wordt weergegeven:

* als PDF in Adobe Reader of in een browser
* als HTML in verschillende browseromgevingen, inclusief een compatibele XHTML 1.0-rendering
* als formulierhulplijnen in verschillende browseromgevingen die ondersteuning bieden voor Adobe Flash Player.

Voor meer informatie over de Forms-service raadpleegt u [Servicereferentie](https://www.adobe.com/go/learn_aemforms_services_63).

Met de Forms-pagina in de beheerconsole kunt u het gedrag van de Forms-service configureren. Deze instellingen zijn van toepassing op alle aanroepen van de service. Alle parameters die via de SDK voor AEM formulieren worden verzonden, overschrijven de instellingen die in de beheerconsole zijn ingesteld. zij hebben echter alleen invloed op die specifieke aanroeping .

Nadat u de Forms-instellingen in de beheerconsole hebt gewijzigd, klikt u op Opslaan. De wijzigingen worden van kracht als u de server niet opnieuw hoeft te starten. Het kan echter zijn dat u de Forms-service moet stoppen en opnieuw opstarten wanneer u de instellingen voor de cachemodus configureert. (Zie [Starten en stoppen van services](/help/forms/using/admin-help/starting-stopping-services.md#starting-and-stopping-services).)
