---
title: Overzicht van uitvoerservice
seo-title: Overzicht van uitvoerservice
description: Met Uitvoer kunt u XML-formuliergegevens samenvoegen met een formulierontwerp dat in Designer is gemaakt, om een uitvoerstroom van het document in verschillende indelingen te maken.
seo-description: Met Uitvoer kunt u XML-formuliergegevens samenvoegen met een formulierontwerp dat in Designer is gemaakt, om een uitvoerstroom van het document in verschillende indelingen te maken.
uuid: 7890b0a6-bae5-4ad5-ae41-503b988ba3da
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 5a96f5ea-6fe3-44b1-b314-14097b9e9c01
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---


# Overzicht van uitvoerservice {#overview-of-output-service}

Met Uitvoer kunt u XML-formuliergegevens samenvoegen met een formulierontwerp dat in Designer is gemaakt, om een uitvoerstroom van het document in verschillende indelingen te maken. De uitvoerstream kan naar een netwerkprinter, een lokale printer of een schijfbestand worden verzonden

U kunt de pagina van de Output in beleidsconsole gebruiken om de dienst van de Output te beheren. De instellingen die u configureert, worden tijdens runtime gebruikt wanneer de equivalente instellingen niet zijn opgegeven via de API voor AEM formulieren. De configuratie die door de AEM vormen SDK wordt gedaan treedt de montages met behulp van beleidsconsole wordt gevormd met voeten.

Voor extra informatie over de dienst van de Output, zie [Verwijzing van de Diensten](https://www.adobe.com/go/learn_aemforms_services_61).

Op de pagina&#39;s van de Output in beleidsconsole, kunt u verscheidene taken uitvoeren:

* Geef tekensets op voor internationalisatie. (Zie [De tekenset wijzigen](/help/forms/using/admin-help/change-character-set.md#change-the-character-set).)
* Geef absolute en relatieve paden op voor URL&#39;s, URI&#39;s, XCI&#39;s en bestandslocaties. (Zie [Bestandslocaties opgeven voor Output](/help/forms/using/admin-help/specify-file-locations-output.md#specify-file-locations-for-output).)
* Cachegrootten en beleid configureren. (Zie [De cachemodus opgeven](/help/forms/using/admin-help/configuring-caching-output.md#specifying-the-cache-mode) en [Cacheinstellingen configureren](/help/forms/using/admin-help/configuring-caching-output.md#configuring-cache-settings).)
* Maak lettertypen beschikbaar op de toepassingsserver. (Zie [Lettertypen beschikbaar maken](/help/forms/using/admin-help/make-fonts-available.md#make-fonts-available).)
* Geef de fonts op die u wilt insluiten. (Zie [Fonts opgeven om in te sluiten](/help/forms/using/admin-help/specify-fonts-embed.md#specify-fonts-to-embed).)
* Geef XCI-configuratieopties op. (Zie [XCI-configuratieopties opgeven](/help/forms/using/admin-help/specify-xci-configuration-options.md#specify-xci-configuration-options).)
* Geef beveiligingsinstellingen op. (Zie [Beveiligingsinstellingen opgeven](/help/forms/using/admin-help/specify-security-settings.md#specify-security-settings).)

Nadat u de instellingen hebt gewijzigd, klikt u op Opslaan om deze toe te passen op Uitvoer. De wijzigingen worden van kracht als u de server niet opnieuw hoeft op te starten, maar u moet mogelijk de uitvoerservice opnieuw starten wanneer u de cache-instellingen configureert.
