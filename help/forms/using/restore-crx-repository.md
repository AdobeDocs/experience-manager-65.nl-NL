---
title: Kan beschadigde CRX-opslagplaats die van toepassing is op JEE-clusterserver niet herstellen
description: Stappen om beschadigde CRX-opslagplaats te herstellen
source-git-commit: a7d125503b0bd3c52cb3a959e2f0dde1a69cbe2b
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 0%

---

# Kan beschadigde CRX-opslagplaats niet herstellen {#unable-to-restore-corrupt-crx-repository}

## Probleem {#issue}

Voor AEM Forms die op JEE met RDB persistentie wordt opgesteld, is het noodzakelijk dat de gastheermachines van AEM Forms en gegevensbestandmachines in absolute tijdsynch zijn. Als echter klokken om een of andere reden niet meer synchroon zijn, wordt de CRX-opslagplaats beschadigd en zijn URL&#39;s niet meer toegankelijk. De fout als `AuthenticationsupportService missing` vindt plaats in logbestanden.

## Oplossing {#solution}

Voer de volgende stappen uit om het probleem op te lossen:
1. Ga naar  [https://localhost:4502/system/console/bundles](http://localhost:4502/system/console/bundles).

1. Zoek de `oak-core` bundelen en controleren of deze actief is.

1. Start de `oak-core` bundel als deze niet wordt uitgevoerd. Als de pauzeknop aanwezig is vóór de `oak-core` dan geeft de bundel aan dat de bundel actief is.

1. Als het probleem nog steeds niet is opgelost, kunt u het terugzetten vanaf de back-up van de CRX-opslagplaats of de CRX-opslagplaats opnieuw opbouwen als er geen back-up beschikbaar is.

   >[!NOTE]
   >
   >Maak een back-up van uw CRX-opslagplaats voordat u de bovenstaande stappen uitvoert.

## Van toepassing op {#applies-to}

Deze oplossing is van toepassing op:

* AEM Forms op JEE Cluster Server


