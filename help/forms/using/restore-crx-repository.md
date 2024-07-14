---
title: Kan beschadigde CRX-opslagplaats die van toepassing is op JEE-clusterserver niet herstellen
description: Leer de stappen voor het herstellen van een beschadigde CRX-opslagplaats.
exl-id: 212f61f1-360f-4abe-b874-055ec65454c7
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: 9f59606bb58b9e90f07bd22e89f3213afb54a697
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 0%

---

# Kan beschadigde CRX-opslagplaats niet herstellen {#unable-to-restore-corrupt-crx-repository}

## Probleem {#issue}

Voor AEM Forms on JEE die een relationele gegevensbank gebruikt, zou de tijd op de machine die AEM Forms en relationele gegevensbank ontvangt altijd in absolute synchronisatie moeten zijn. Als de tijd op deze computers niet meer synchroon is, kan de CRX-opslagplaats van AEM Forms op de JEE-server ontoegankelijk worden. Het kan beschadigd lijken en ontoegankelijk worden via URL. De fout `AuthenticationsupportService missing` wordt geregistreerd.

## Vereisten {#prerequisites}

Maak een back-up van uw CRX-opslagplaats voordat u de onderstaande stappen uitvoert.

## Oplossing {#solution}

1. Ga naar `https://[AEM Forms Server]:[port]/system/console/bundles` .

1. Zoek de `oak-core` -bundel en controleer of deze wordt uitgevoerd.

1. Start de `oak-core` -bundel opnieuw als deze niet wordt uitgevoerd. Als ![ de knoop van de Pauze ](/help/forms/using/assets/stop.png) pictogram vóór de `oak-core` bundel aanwezig is, dan wijst het erop dat de bundel in lopende staat is.

1. Als het probleem nog steeds niet is opgelost, kunt u het herstellen vanaf de CRX-opslagplaats via de back-up of de CRX-opslagplaats opnieuw opbouwen als er geen back-up beschikbaar is.


## Van toepassing op {#applies-to}

Deze oplossing geldt voor AEM Forms op JEE Cluster.
