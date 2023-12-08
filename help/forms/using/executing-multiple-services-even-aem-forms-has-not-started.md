---
title: Het uitvoeren van meerdere services ondanks AEM Forms is nog niet begonnen.
description: Zelfs als de AEM Forms niet volledig is begonnen, verwerkt het veelvoudige diensten.
source-git-commit: 6b24067c1808475044a612f21d5d4d2793c13e17
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 0%

---

# Het uitvoeren van meerdere services ondanks AEM Forms is nog niet helemaal begonnen{#steps-to-resolve-error-after-installing-service-pack}


## Probleem {#issue}

Wanneer de gebruiker AEM Forms opnieuw start, worden de huidige aanroepende processen voortgezet, zoals het renderen van PDF-documenten en meer. Hierdoor wordt de AEM Forms-server niet correct opgestart.

## Van toepassing op {#applies-to}

De oplossing is van toepassing op AEM Forms op JEE Server en AEM Forms op OSGi Server.

## Oplossing {#solution}

Gebruikers voegen een argument toe om het probleem op te lossen `Dcom.adobe.livecycle.dsc.deferServiceStart=true` tot [batchbestand](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/command-line-start-and-stop.html#windows-platform-start-bat-script-example) tijdens het opstarten van de server.





