---
title: AEM Forms Server begint de documenten te verwerken, zelfs voordat alle services actief zijn.
description: De Server van AEM Forms begint de documenten zelfs te verwerken alvorens alle diensten op Server JEE en Server OSGi in werking zijn.
exl-id: 1a1bc1cb-e0ce-49a0-9b05-ae59f900cfb2
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms, Troubleshooting
role: User, Developer
source-git-commit: 539da06db98395ae6eaee8103a3e4b31204abbb8
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 0%

---

# AEM Forms Server begint de documenten te verwerken, zelfs voordat alle services zijn gestart{#aem-forms-server-start-processing-documents-even-if-it-is-not-fully-up}

## Probleem {#issue}

<!--When user restarts AEM Forms server, the current calling processes or services still continue such as rendering PDF documents and more. It causes the restart of the AEM Forms server to not startup correctly.-->

Voordat de AEM Forms-server volledig is geactiveerd en alle toepassingen actief zijn, begint AEM Forms Server met het verwerken van de documenten.


## Van toepassing op {#applies-to}

De oplossing is van toepassing op AEM Forms op JEE Server en AEM Forms op OSGi Server.

## Oplossing {#solution}

Voeg een argument toe om het probleem op te lossen `Dcom.adobe.livecycle.dsc.deferServiceStart=true` aan de [batchbestand](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/command-line-start-and-stop.html#windows-platform-start-bat-script-example) tijdens het opstarten van de server.
