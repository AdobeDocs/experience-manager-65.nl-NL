---
title: EAR-implementatie mislukt op JEE WebLogic-server
seo-title: EAR Deployment failing on JEE Weblogic Server
description: Stappen om de mislukte implementatie van EAR op JEE WebLogic Server op te lossen
source-git-commit: 05712cfcef1d9c37b7cd015133abaf6df0e351d2
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 3%

---


# EAR-implementatie mislukt op JEE WebLogic-server {#ear-deployment-failing-on-jee-weblogic-server}

## Probleem {#issue}

Wanneer een gebruiker probeert de `adobe-livecycle-weblogic.ear` te implementeren, wordt de uitzondering `Null Pointer` aangetroffen.

## Van toepassing op {#applies-to}

Deze oplossing geldt voor:

* AEM Forms on WebLogic JEE-server versie 12.2.1.x.

## Oplossing {#solution}

Ga als volgt te werk om het probleem op te lossen:

1. Ga naar de `<domain_home>\bin` -map van de geïnstalleerde WebLogic JEE-server.

1. Bewerk het bestand `setDomainEnv.cmd` of `setDomainEnv.sh` als `applicable` .

1. Zoek naar de laatste keer dat `JAVA_OPTS` voorkomt en voeg `-DANTLR_USE_DIRECT_CLASS_LOADING=true` eraan toe. De bijgewerkte tekenreeks wordt bijvoorbeeld weergegeven als:

        reeks ` JAVA_OPTIONS=%JAVA_OPTIONS% - DANTLR_USE_DIRECT_CLASS_LOADING=true ` 
   
1. Sla de wijzigingen op.
