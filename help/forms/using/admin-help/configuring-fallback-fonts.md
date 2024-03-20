---
title: Terugvallettertypen configureren
description: Leer hoe u fallback-lettertypen kunt configureren voor AEM Forms. Met het bestand FontManagerResources.properties kunt u de standaardlettertypen handmatig toewijzen aan terugvallettertypen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_pdf_generator
products: SG_EXPERIENCEMANAGER/6.5/FORMS
feature: PDF Generator
exl-id: 76dd2b0c-9f16-47bf-a565-99277be750fb
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---

# Terugvallettertypen configureren {#configuring-fallback-fonts}

U kunt het bestand FontManagerResources.properties handmatig zodanig configureren dat de standaardfonts AEM formulieren worden toegewezen aan fallback (of vervangen) als de standaardfonts niet beschikbaar zijn op de server. Dit eigenschapbestand bevindt zich in het bestand adobe-fontmanager.jar.

>[!NOTE]
>
>De fontconfiguratie van de reserve is ook op de assembleerdienst van toepassing.

1. Navigeren naar de adobe-livecycle-*`[appserver]`*.ear-bestand in de *`[aem-forms root]`*/configurationManager/export directory, maak een reservekopie en pak het origineel uit.
1. Zoek het bestand adobe-fontmanager.jar en pak het uit.
1. Zoek het bestand FontManagerResources.properties en open het in een teksteditor.
1. Wijzig desgewenst de locaties en namen van de lettertypen Algemeen en Fallback en sla het bestand op.

   De fontitems in het bestand FontManagerResources.properties zijn relatief ten opzichte van de *`[aem-forms root]`*/fonts directory. Als u lettertypen opgeeft die niet standaard AEM formulierlettertypen zijn, moet u deze lettertypen installeren in deze mapstructuur (binnen een bestaande map of in een nieuw gemaakte map).

   >[!NOTE]
   >
   >Als het opgegeven lettertype of standaardlettertype geen specifiek Unicode-teken bevat of als dit niet beschikbaar is, wordt het teken volgens de volgende prioriteit van een fallback-lettertype genomen:

   * Landspecifiek lettertype
   * HOOFDLETTERlettertype indien landinstelling niet is ingesteld
   * Algemeen lettertype, doorzocht op volgorde ingesteld in de fallback-tabel

1. Verpak het bestand adobe-fontmanager.jar opnieuw.
1. De adobe-livecycle opnieuw verpakken *`[appserver]`*.ear-bestand en gebruikt het vervolgens handmatig of door Configuratiebeheer uit te voeren.

>[!NOTE]
>
>Gebruik Configuration Manager niet om de adobe-livecycle-`[appserver]`.ear-bestand omdat hiermee uw wijzigingen worden overschreven door de standaardwaarden van de AEM formulieren.
