---
title: Kan beschadigde CRX-opslagplaats die van toepassing is op JEE-clusterserver niet herstellen
description: Stappen om beschadigde CRX-opslagplaats te herstellen.
exl-id: 212f61f1-360f-4abe-b874-055ec65454c7
source-git-commit: 0e5b89617d481c69882ec5d4658e76855aa9b691
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 0%

---

# Kan beschadigde CRX-opslagplaats niet herstellen {#unable-to-restore-corrupt-crx-repository}

## Probleem {#issue}

Voor AEM Forms on JEE die een relationele gegevensbank gebruikt, zou de tijd op de machine die AEM Forms en relationele gegevensbank ontvangt altijd in absolute synchronisatie moeten zijn. Als de tijd op deze computers niet meer synchroon is, kan de CRX-opslagplaats van AEM Forms op de JEE-server ontoegankelijk worden. Het kan beschadigd lijken en ontoegankelijk worden via URL. De `AuthenticationsupportService missing` fout is geregistreerd.

## Vereisten {#prerequisites}

Maak een back-up van uw CRX-opslagplaats voordat u de onderstaande stappen uitvoert.

## Oplossing {#solution}

Voer de volgende stappen uit om het probleem op te lossen:
1. Ga naar  `https://[AEM Forms Server]:[port]/system/console/bundles`.

1. Zoek de `oak-core` bundel en controleer of het programma wordt uitgevoerd.

1. De opdracht opnieuw starten `oak-core` bundel als deze niet wordt uitgevoerd. Indien  ![De knop Pauzeren](/help/forms/using/assets/stop.png) is aanwezig vóór het pictogram `oak-core` dan geeft de bundel aan dat de bundel actief is.

1. Als het probleem nog steeds niet is opgelost, kunt u het terugzetten vanaf de back-up van de CRX-opslagplaats of de CRX-opslagplaats opnieuw opbouwen als er geen back-up beschikbaar is.


## Van toepassing op {#applies-to}

Deze oplossing geldt voor:

* AEM Forms on JEE Cluster