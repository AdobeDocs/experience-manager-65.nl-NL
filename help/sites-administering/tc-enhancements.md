---
title: Verbeteringen op gebied van vertaling
description: Incrementele verbeteringen en verfijningen van de mogelijkheden voor AEM vertaalbeheer.
topic-tags: site-features
content-type: reference
feature: Language Copy
exl-id: 2011a976-d506-4c0b-9980-b8837bdcf5ad
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: eae057caed533ef16bb541b4ad41b8edd7aaa1c7
workflow-type: tm+mt
source-wordcount: '669'
ht-degree: 0%

---

# Verbeteringen op gebied van vertaling{#translation-enhancements}

Deze pagina biedt incrementele verbeteringen en verfijningen voor AEM vertaalbeheermogelijkheden.

## Automatisering van vertaalprojecten {#translation-project-automation}

Er zijn opties toegevoegd om de productiviteit bij vertaalprojecten te verbeteren, zoals het automatisch promoten en verwijderen van lanceringen van vertalingen en het plannen van de terugkerende uitvoering van een vertaalproject.

1. In uw vertaalproject, klik de ellips bij de bodem van de **Vertaling Summiere** tegel.

   ![ screen_shot_2018-04-19at222622 ](assets/screen_shot_2018-04-19at222622.jpg)

1. Schakelaar aan **Geavanceerd** tabel. Bij de bodem, kunt u **selecteren bevordert automatisch VertaalLancjes**.

   ![ screen_shot_2018-04-19at223430 ](assets/screen_shot_2018-04-19at223430.jpg)

1. U kunt desgewenst instellen of het starten van vertalingen na ontvangst van vertaalde inhoud automatisch moet worden bevorderd en verwijderd.

   ![ screen_shot_2018-04-19at224033 ](assets/screen_shot_2018-04-19at224033.jpg)

1. Om de terugkomende uitvoering van een vertaalproject te selecteren, selecteer de frequentie met dropdown onder **Vertaling van de Herhaal**. Het terugkomen van projectuitvoering zal automatisch vertaalbanen in de gespecificeerde intervallen creëren en uitvoeren.

   ![ screen_shot_2018-04-19at223820 ](assets/screen_shot_2018-04-19at223820.jpg)

## Meertalige vertaalprojecten {#multilingual-translation-projects}

Het is mogelijk om veelvoudige doeltalen in een vertaalproject te vormen, om het totale aantal gecreeerde vertaalprojecten te verminderen.

1. In uw vertaalproject, klik de punten bij de bodem van de **Vertaling Summiere** tegel.

   ![ screen_shot_2018-04-19at222622 ](assets/screen_shot_2018-04-19at222622.jpg)

1. Schakelaar aan **Geavanceerd** tabel. U kunt veelvoudige talen onder **Taal van het Doel** toevoegen.

   ![ screen_shot_2018-04-22at212601 ](assets/screen_shot_2018-04-22at212601.jpg)

1. Alternatief, als u vertaling via de verwijzingenspoorstaaf in Plaatsen in werking stelt, voeg u talen toe en selecteer **creeer het Project van de Vertaling van de Meertaligheid**.

   ![ screen_shot_2018-04-22at212941 ](assets/screen_shot_2018-04-22at212941.jpg)

1. In het project worden vertaalbanen gecreëerd voor elke doeltaal. Zij kunnen of één voor één binnen het project, of allen in één keer zijn begonnen door het project globaal in Projecten Admin uit te voeren.

   ![ screen_shot_2018-04-22at213854 ](assets/screen_shot_2018-04-22at213854.jpg)

## Updates van vertaalgeheugen {#translation-memory-updates}

Handmatige bewerkingen van vertaalde inhoud kunnen worden gesynchroniseerd met het TMS (Translation Management System) om het vertaalgeheugen te trainen.

1. Van de console van Plaatsen, na het bijwerken van tekstinhoud in een vertaalde pagina, selecteer **het Geheugen van de Vertaling van de Update**.

   ![ screen_shot_2018-04-22at234430 ](assets/screen_shot_2018-04-22at234430.jpg)

1. Een lijstmening toont een zij-aan-zij vergelijking van de bron en de vertaling voor elke tekstcomponent die werd uitgegeven. Selecteer welke vertaalupdates aan het Geheugen van de Vertaling zouden moeten worden gesynchroniseerd, en **Geheugen van de Update** selecteren.

   ![ screen_shot_2018-04-22at235024 ](assets/screen_shot_2018-04-22at235024.jpg)

AEM werkt de vertaling van de bestaande koorden in het vertaalgeheugen van gevormde TMS bij.

* De actie werkt de vertaling van bestaande koorden in het vertaalgeheugen van gevormde TMS bij.
* Het creëert geen nieuwe vertaalbanen.
* De vertalingen worden via AEM vertalings-API teruggestuurd naar de TMS (zie hieronder).

Deze functie gebruiken:

* Een TMS moet voor gebruik met AEM worden gevormd.
* De schakelaar moet de methode uitvoeren [`storeTranslation` ](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/adobe/granite/translation/api/TranslationService.html).
   * De code binnen deze methode bepaalt wat met het verzoek van de vertaalgeheugenupdate gebeurt.
   * Het AEM vertaalkader verzendt de koordwaardeparen (originele en bijgewerkte vertaling) terug naar TMS via deze methodeimplementatie.

De updates van het vertaalgeheugen kunnen worden onderschept en naar een douanebestemming worden verzonden, voor gevallen waar een merkgebonden vertaalgeheugen wordt gebruikt.

## Taalkopieën op meerdere niveaus {#language-copies-on-multiple-levels}

Taalwortels kunnen nu worden gegroepeerd onder knooppunten, bijvoorbeeld per regio, terwijl ze nog steeds worden herkend als wortels van taalkopieën.

![ screen_shot_2018-04-23at144012 ](assets/screen_shot_2018-04-23at144012.jpg)

>[!CAUTION]
>
>Er is slechts één niveau toegestaan. Met de volgende code kan de pagina &#39;es&#39; bijvoorbeeld niet worden omgezet in een taalkopie:
>
>* `/content/we-retail/language-masters/en`
>* `/content/we-retail/language-masters/americas/central-america/es`
>
>Deze `es` -taalkopie wordt niet gedetecteerd omdat deze zich op twee niveaus (americas/central-america) van het knooppunt `en` bevindt.

>[!NOTE]
>
>Taalwortels kunnen elke paginanaam hebben, in plaats van alleen de ISO-code van de taal. AEM zal altijd het pad en de naam eerst controleren, maar als de paginanaam geen taal identificeert, zal AEM de eigenschap cq:language van de pagina controleren op de taalidentificatie.

## Vertaalstatus rapporteren {#translation-status-reporting}

Een eigenschap kan nu worden geselecteerd in de lijstweergave Sites, die aangeeft of een pagina is vertaald, vertaald is of nog niet is vertaald. Deze weergeven:

1. In Plaatsen, schakelaar aan **Mening van de Lijst.**

   ![ screen_shot_2018-04-23at130646 ](assets/screen_shot_2018-04-23at130646.jpg)

1. Klik **Montages van de Mening**.

   ![ screen_shot_2018-04-23at130844 ](assets/screen_shot_2018-04-23at130844.jpg)

1. Controle **Vertaalde** checkbox onder **Vertaling** en klik **Update**.

   ![ screen_shot_2018-04-23at130955 ](assets/screen_shot_2018-04-23at130955.jpg)

U kunt a **Vertaalde** kolom nu zien die de vertaalstatus van de pagina&#39;s toont.

![ screen_shot_2018-04-23at133821 ](assets/screen_shot_2018-04-23at133821.jpg)
