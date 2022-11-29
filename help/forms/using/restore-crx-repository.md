---
title: Kan beschadigde CRX-opslagplaats die van toepassing is op JEE-clusterserver niet herstellen
description: Stappen om beschadigde CRX-opslagplaats te herstellen
exl-id: 212f61f1-360f-4abe-b874-055ec65454c7
source-git-commit: cf034e8765317ee022aad4693ced37c3fa793ff2
workflow-type: tm+mt
source-wordcount: '182'
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

1. Zoek de `oak-core` bundelen en controleren of deze actief is.

1. Start de `oak-core` bundel als deze niet wordt uitgevoerd. Indien  ![De knop Pauzeren](/help/forms/using/assets/stop.png) is aanwezig vóór het pictogram `oak-core` -bundel, dan geeft dit aan dat de bundel actief is.

1. Als het probleem nog steeds niet is opgelost, kunt u het terugzetten vanaf de back-up van de CRX-opslagplaats of de CRX-opslagplaats opnieuw opbouwen als er geen back-up beschikbaar is.


## Van toepassing op {#applies-to}

Deze oplossing is van toepassing op:

* AEM Forms on JEE Cluster Environment