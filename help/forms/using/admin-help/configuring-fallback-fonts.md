---
title: Terugvallettertypen configureren
seo-title: Terugvallettertypen configureren
description: Leer hoe u fallback-lettertypen configureert.
seo-description: Leer hoe u fallback-lettertypen configureert.
uuid: 2745541c-8c6d-4bb4-aa14-ec19afd6bc35
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_pdf_generator
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: d997a268-a40a-462d-badd-94f0731f7ba4
translation-type: tm+mt
source-git-commit: d3719a9ce2fbb066f99445475af8e1f1e7476f4e
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 0%

---


# Terugvallettertypen configureren {#configuring-fallback-fonts}

U kunt het bestand FontManagerResources.properties handmatig zodanig configureren dat de standaardfonts AEM formulieren worden toegewezen aan fallback (of vervangen) als de standaardfonts niet beschikbaar zijn op de server. Dit eigenschapbestand bevindt zich in het bestand adobe-fontmanager.jar.

>[!NOTE]
>
>De fontconfiguratie van de reserve is ook op de assembleerdienst van toepassing.

1. Navigeer naar het bestand adobe-livecycle-*`[appserver]`*.ear in de map *`[aem-forms root]`*/configurationManager/export, maak een reservekopie en pak het origineel uit.
1. Zoek het bestand adobe-fontmanager.jar en pak het uit.
1. Zoek het bestand FontManagerResources.properties en open het in een teksteditor.
1. Wijzig desgewenst de locaties en namen van de lettertypen Algemeen en Fallback en sla het bestand op.

   De fontitems in het bestand FontManagerResources.properties zijn relatief ten opzichte van de map *`[aem-forms root]`*/fonts. Als u lettertypen opgeeft die niet standaard AEM formulierlettertypen zijn, moet u deze lettertypen installeren in deze mapstructuur (binnen een bestaande map of in een nieuw gemaakte map).

   >[!NOTE]
   >
   >Als het opgegeven lettertype of standaardlettertype geen specifiek Unicode-teken bevat of als dit niet beschikbaar is, wordt het teken volgens de volgende prioriteit van een fallback-lettertype genomen:

   * Landspecifiek font
   * HOOFDLETTERlettertype indien landinstelling niet is ingesteld
   * Algemeen lettertype, doorzocht op volgorde ingesteld in de fallback-tabel

1. Verpak het bestand adobe-fontmanager.jar opnieuw.
1. Herhaal het bestand adobe-livecycle-*`[appserver]`*.ear en implementeer het bestand vervolgens handmatig of door Configuratiebeheer uit te voeren.

>[!NOTE]
>
>Gebruik Configuration Manager niet om het bestand adobe-livecycle-`[appserver]`.ear opnieuw te verpakken, omdat hierdoor uw wijzigingen worden overschreven door de standaardwaarden voor AEM formulieren.

