---
title: Bestandslocaties voor uitvoer opgeven
description: Leer hoe u bestandslocaties opgeeft voor Output voor bepaalde bestandstypen, bijvoorbeeld Content Root URI, XCI Configuration File, Cache and Default.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 620c69d6-4fe1-46d6-b5d4-3b562142e547
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: 6a9806d8f40f711a610c130c63d9ab9b2460d075
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# Bestandslocaties voor uitvoer opgeven {#specify-file-locations-for-output}

>[!NOTE]
> 
> Zorg ervoor dat de gebruiker beheerdersrechten heeft om toegang te krijgen tot de beheerdersconsole.

U kunt de locaties opgeven waar Output naar bepaalde bestandstypen zoekt die deze vereist.

1. Klik in de beheerconsole op Services > Uitvoer.
1. Geef onder Locaties de juiste opties op.
1. Klik op Opslaan.

## Locatie-instellingen {#locations-settings}

**Inhoudswortel URI:** URI of absolute plaats van de bewaarplaats waarvan de vormen worden teruggewonnen. Deze waarde wordt gecombineerd met de parameter sForm, opgegeven via de API, om het absolute pad naar het opgehaalde formulier te maken. Deze waarde kan verwijzen naar een map of een weblocatie die toegankelijk is via HTTP.

De standaardwaarde is een lege tekenreeks.

**XCI het Dossier van de Configuratie:** de relatieve of absolute plaats van het XCI configuratiedossier dat de dienst van de Output voor het teruggeven gebruikt. Voor een relatieve waarde wordt aangenomen dat het XCI-bestand zich in de AEM formulieren bevindt die kunnen worden geïmplementeerd in het EAR-bestand.

De standaardwaarde is `com/adobe/formServer/PA/pa_output.xci` .

**Plaats van het Geheime voorgeheugen:** specificeert de plaats van het geheime voorgeheugen van de Output. Wanneer u deze instelling wijzigt, worden alle bestaande cachegegevens van de huidige locatie opnieuw ingesteld en wordt een nieuwe cache gemaakt op de nieuwe locatie. Selecteer een van de volgende opties:

**StandaardPlaats:** dit is de standaardselectie. Als deze optie is geselecteerd, wordt de cache gemaakt op een locatie die afhankelijk is van de toepassingsserver die u gebruikt:

* **JBoss:** `[JBoss Home]\server\[install type]\svcdata\Output\Cache`
* **WebLogic:** `[WebLogic Home]\user_projects\domains\[aem-forms domain Name]\adobe\[Forms Server name]\Output\Cache`
* **WebSphere:** `[IBM Home]\WebSphere\AppServer\installedApps\adobe\server1\Output\Cache`

**LC Temp Folder:** het geheime voorgeheugen wordt gecreeerd in een subdirectory van de folder van de AEM vormen temp, die in de beleidsconsole onder Montages > de Montages van het Systeem van de Kern > Configuraties > Plaats van de Folder van Temp wordt gespecificeerd. De submap heeft de naam `adobeoutput_[servername]` .

>[!NOTE]
>
>Als u een tijdelijk schoonmaakprogramma gebruikt, terwijl het schrappen van deze folders niet functionaliteit beïnvloedt, kan het prestaties voor een korte tijd beduidend beïnvloeden, tot het nieuwe geheime voorgeheugen wordt gecreeerd. U voorkomt dit door deze mappen niet te verwijderen terwijl u de tijdelijke map voor AEM formulieren wist.
