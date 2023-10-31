---
title: Bestandslocaties voor uitvoer opgeven
description: Leer hoe u bestandslocaties opgeeft voor Output voor bepaalde bestandstypen, bijvoorbeeld Content Root URI, XCI Configuration File, Cache and Default.
uuid: 3287274f-85b5-4811-8abb-d347a9b80947
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 460bbb31-8187-469c-8102-b310093b6c03
exl-id: 620c69d6-4fe1-46d6-b5d4-3b562142e547
source-git-commit: 6caf3ef4a00275f0f73be52b6a9ccba77d277f1a
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 0%

---

# Bestandslocaties voor uitvoer opgeven {#specify-file-locations-for-output}

U kunt de locaties opgeven waar Output naar bepaalde bestandstypen zoekt die deze vereist.

1. Klik in de beheerconsole op Services > Uitvoer.
1. Geef onder Locaties de juiste opties op.
1. Klik op Opslaan.

## Locatie-instellingen {#locations-settings}

**URI van basisinhoud:** De URI of absolute locatie van de opslagplaats waar formulieren worden opgehaald. Deze waarde wordt gecombineerd met de parameter sForm, opgegeven via de API, om het absolute pad naar het opgehaalde formulier te maken. Deze waarde kan verwijzen naar een map of een weblocatie die toegankelijk is via HTTP.

De standaardwaarde is een lege tekenreeks.

**XCI-configuratiebestand:** De relatieve of absolute locatie van het XCI-configuratiebestand dat de uitvoerservice gebruikt voor rendering. Voor een relatieve waarde wordt aangenomen dat het XCI-bestand zich in de AEM formulieren bevindt die kunnen worden geïmplementeerd in het EAR-bestand.

De standaardwaarde is `com/adobe/formServer/PA/pa_output.xci`.

**Cachelocatie:** Hiermee geeft u de locatie van de uitvoerschijfcache op. Wanneer u deze instelling wijzigt, worden alle bestaande cachegegevens van de huidige locatie opnieuw ingesteld en wordt een nieuwe cache gemaakt op de nieuwe locatie. Selecteer een van de volgende opties:

**Standaardlocatie:** Dit is de standaardselectie. Als deze optie is geselecteerd, wordt de cache gemaakt op een locatie die afhankelijk is van de toepassingsserver die u gebruikt:

* **JBoss:** `[JBoss Home]\server\[install type]\svcdata\Output\Cache`
* **WebLogic:** `[WebLogic Home]\user_projects\domains\[aem-forms domain Name]\adobe\[forms server name]\Output\Cache`
* **WebSphere** `[IBM Home]\WebSphere\AppServer\installedApps\adobe\server1\Output\Cache`

**LC Temp-map:** De cache wordt gemaakt in een submap van de tijdelijke map voor AEM formulieren, die wordt opgegeven in de beheerconsole onder Instellingen > Core System Settings > Configurations > Location of Temp Directory. De naam van de submap is `adobeoutput_[servername]`.

>[!NOTE]
>
>Als u een hulpprogramma voor tijdelijke reiniging gebruikt, moet u er rekening mee houden dat het verwijderen van deze mappen geen invloed heeft op de functionaliteit, maar dat dit de prestaties gedurende korte tijd aanzienlijk kan beïnvloeden, totdat de nieuwe cache wordt gemaakt. U voorkomt dit door deze mappen niet te verwijderen terwijl u de tijdelijke map voor AEM formulieren wist.
