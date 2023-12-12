---
title: Het uitvoeren van meerdere services ondanks AEM Forms is nog niet begonnen.
description: Zelfs als de AEM Forms niet volledig is begonnen, verwerkt het veelvoudige diensten.
exl-id: 4ec40412-15b1-434b-a919-2cf23f48077c
source-git-commit: faa628ac4a4631564141f68f3efc9d69a67e5c40
workflow-type: tm+mt
source-wordcount: '96'
ht-degree: 0%

---

# Het uitvoeren van meerdere services ondanks AEM Forms is nog niet helemaal begonnen{#steps-to-resolve-error-after-installing-service-pack}


## Probleem {#issue}

Wanneer de gebruiker AEM Forms opnieuw start, worden de huidige aanroepende processen voortgezet, zoals het renderen van PDF-documenten en meer. Hierdoor wordt de AEM Forms-server niet correct opgestart.

## Van toepassing op {#applies-to}

De oplossing is van toepassing op AEM Forms op JEE Server en AEM Forms op OSGi Server.

## Oplossing {#solution}

Voeg een argument toe om het probleem op te lossen `Dcom.adobe.livecycle.dsc.deferServiceStart=true` tot [batchbestand](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/command-line-start-and-stop.html#windows-platform-start-bat-script-example) tijdens het opstarten van de server.
