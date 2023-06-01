---
title: EAR-implementatie mislukt op JEE WebLogic-server
seo-title: EAR Deployment failing on JEE Weblogic Server
description: Stappen om de mislukte implementatie van EAR op JEE WebLogic Server op te lossen
seo-description: Steps to resolve EAR Deployment failing on JEE Weblogic Server
source-git-commit: 45bb54a2666c2c196a8fb52795a7f428aa751e4d
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 2%

---


# EAR-implementatie mislukt op JEE WebLogic-server {#ear-deployment-failing-on-jee-weblogic-server}

## Probleem {#issue}

Wanneer een gebruiker probeert om `adobe-livecycle-weblogic.ear`de `Null Pointer` Er is een uitzondering opgetreden.

## Van toepassing op {#applies-to}

Deze oplossing is van toepassing op:

* AEM Forms on WebLogic JEE-server versie 12.2.1.x.

## Oplossing {#solution}

Ga als volgt te werk om het probleem op te lossen:

1. Ga naar de `<domain_home>\bin` map met geïnstalleerde WebLogic JEE-server.

1. Bewerk de `setDomainEnv.cmd` of `setDomainEnv.sh` bestand, als `applicable`.

1. Zoeken naar de laatste instantie van `JAVA_OPTS` en toevoegen `-DANTLR_USE_DIRECT_CLASS_LOADING=true` aan het. De bijgewerkte tekenreeks wordt bijvoorbeeld weergegeven als:

       set ` JAVA_OPTIONS=%JAVA_OPTIONS% -DANTLR_USE_DIRECT_CLASS_LOADING=true`
   
1. Sla de wijzigingen op.


