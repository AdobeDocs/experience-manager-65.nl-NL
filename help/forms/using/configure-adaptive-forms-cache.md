---
title: Cache voor aangepaste formulieren configureren
seo-title: Cache voor aangepaste formulieren configureren
description: 'De cache voor adaptieve formulieren is speciaal ontworpen voor adaptieve formulieren en documenten. Het slaat adaptieve formulieren en adaptieve documenten in het cachegeheugen op om de tijd te verkorten die nodig is om een adaptief formulier of document op de client te genereren. '
seo-description: 'De cache voor adaptieve formulieren is speciaal ontworpen voor adaptieve formulieren en documenten. Het slaat adaptieve formulieren en adaptieve documenten in het cachegeheugen op om de tijd te verkorten die nodig is om een adaptief formulier of document op de client te genereren. '
uuid: ba8f79fd-d8dc-4863-bc0d-7c642c45505c
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Configuration
discoiquuid: 9fa6f761-58ca-4cd0-8992-b9337dc1a279
docset: aem65
translation-type: tm+mt
source-git-commit: 317fadfe48724270e59644d2ed9a90fbee95cf9f

---


# Cache voor aangepaste formulieren configureren{#configure-adaptive-forms-cache}

Een cache is een mechanisme om de toegangstijd voor gegevens te verkorten, de latentie te verminderen en de invoer-/uitvoersnelheid (I/O) te verbeteren. In de cache van adaptieve formulieren worden alleen HTML-inhoud en JSON-structuur van een adaptief formulier opgeslagen zonder dat vooraf ingevulde gegevens worden opgeslagen. Hierdoor wordt de tijd die nodig is om een adaptief formulier of document op de client te genereren, verkort. Het is specifiek ontworpen voor adaptieve formulieren en ondersteunt ook adaptieve documenten.

>[!NOTE]
>
>Wanneer u de cache voor adaptieve formulieren gebruikt, gebruikt u de AEM Dispatcher om clientbibliotheken (CSS en JavaScript) van een adaptief formulier of document in cache te plaatsen.

>[!NOTE]
>
>Zorg tijdens het ontwikkelen van aangepaste componenten op de server die wordt gebruikt voor ontwikkeling dat de cache van adaptieve formulieren uitgeschakeld blijft.

## De cache configureren {#configure-the-cache}

Voer de volgende stappen uit om de cache voor adaptieve formulieren te configureren:

1. Ga naar AEM webconsoleconfiguratiebeheer op https://&#39;[server]:[port]&#39;/system/console/configMgr.
1. Klik de **Aangepaste Vorm en de Interactieve Configuratie** van het Kanaal van de Communicatie van het Web om zijn configuratiewaarden uit te geven.
1. Geef in het dialoogvenster Configuratiewaarden bewerken het maximumaantal formulieren of documenten op dat een instantie van de AEM Forms-server in cache kan plaatsen in het veld **Aantal adaptieve formulieren** . De standaardwaarde is 100.

   >[!NOTE]
   >
   >Als u de cache wilt uitschakelen, stelt u de waarde in het veld Aantal adaptieve formulieren in op **0**. De cache wordt opnieuw ingesteld en alle formulieren en documenten worden uit de cache verwijderd wanneer u de cachemonfiguratie uitschakelt of wijzigt.

   ![Configuratiedialoogvenster voor HTML-cache voor adaptieve formulieren](assets/cache-configuration-edit.png)

1. Klik op **Opslaan** om de configuratie op te slaan.

