---
title: Beveiligde informatieverstrekking voor grote volumes
seo-title: Beveiligde informatieverstrekking voor grote volumes
description: Documentbeveiliging ondersteunt het koppelen van licenties aan gebruikers in plaats van aan documenten in omgevingen waar veel mensen worden geproduceerd.
seo-description: Documentbeveiliging ondersteunt het koppelen van licenties aan gebruikers in plaats van aan documenten in omgevingen waar veel mensen worden geproduceerd.
uuid: 9747d283-506c-434e-9850-e50b95290cc8
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_document_security
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: b76d7d93-23a5-4c08-81f5-a56267b1556a
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Beveiligde informatieverstrekking voor grote volumes {#high-volume-secure-information-delivery}

In een massaproductieomgeving, zoals een omgeving die beveiligde maandelijkse facturen voor een telecombedrijf genereert, kan het maken van licenties die specifiek zijn voor elk document een hulpbronnenintensief proces worden. In dergelijke gevallen ondersteunt documentbeveiliging het koppelen van licenties aan gebruikers in plaats van aan de documenten. De licentie die voor een gebruiker wordt gegenereerd, wordt gebruikt voor alle documenten die voor die gebruiker zijn beveiligd.

Een voordeel van deze aanpak is dat de grootte van de documentbeveiligingsdatabase niet lineair met de documenten toeneemt, maar met het aantal gebruikers. Omdat u de licentie slechts één keer voor een gebruiker moet maken, wordt de verdere beveiliging van documenten via dit beleid bovendien sneller. Functies zoals offline toegang, verlopen van documenten en intrekking worden voor al dergelijke documenten ondersteund.

Documentbeveiliging ondersteunt ook Abstract beleid. Abstract beleid is beleidssjablonen die alle beleidskenmerken bevatten, zoals documentbeveiligingsinstellingen en gebruiksrechten, maar die geen lijst met principes bevatten. De beheerders kunnen om het even welk aantal beleid van het abstracte beleid met verschillende hoofden tot stand brengen die toegang tot de documenten zouden moeten hebben. Wijzigingen in het abstracte beleid hebben geen invloed op het feitelijke beleid dat wordt gegenereerd op basis van het abstracte beleid.

In het geval van maandelijkse factuurgeneratie voor een telecombedrijf, creeert u een abstract beleid, creeert gebruikers, en produceert dan unieke vergunningen voor elke gebruiker. De licenties worden later toegepast op documenten voor elke gebruiker.

Het maken van een abstract beleid wordt alleen ondersteund door Java SDK voor documentbeveiliging. U kunt echter wel het beleid beheren dat u maakt op basis van het abstracte beleid van de webpagina&#39;s voor documentbeveiliging. Beleid dat met deze methode wordt gemaakt, werkt hetzelfde als het beleid dat op basis van webpagina&#39;s voor documentbeveiliging wordt gemaakt.

Zie [Programmeren met AEM-formulieren](https://www.adobe.com/go/learn_aemforms_programming_63) voor meer informatie.
