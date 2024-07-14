---
title: Foutberichten over vervangen API's in foutlogboeken
description: Foutberichten over vervangen API's in foutlogboeken
source-git-commit: b05666883645ca11784292e4bfb5bf9c1e35a43b
workflow-type: tm+mt
source-wordcount: '94'
ht-degree: 1%

---


# Foutberichten over vervangen API&#39;s in foutlogboeken {#error-messages-about-deprecated-apis-in-error-logs}

De kwestie is op de volgende versies van toepassing:

* Experience Manager 6.5 Forms

## Probleem {#issue}

* De volgende foutberichten worden weergegeven in het bestand error.log:
  ` *WARN* [default task-36] org.apache.jackrabbit.oak.spi.security.principal.AclGroupDeprecation use of deprecated java.acl.Group-related API - this method is going to be removed in future Oak releases - see OAK-7358 for details` (NPR-38282)

## Resolutie {#workaround}

1. Installeer [ Experience Manager Forms Service Pack 13 of later (6.5.13.0 of later) ](https://experienceleague.adobe.com/docs/experience-manager-65/release-notes/release-notes.html)
1. Gebruik de volgende koppeling om het pakket (.jar-bestand met resolutie) te downloaden van Software Distribution:

   https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?pack[..] pack/com.adobe.livecycle.dsc.externalloginmodule-4.0.8.jar

1. Open de Manager van de Configuratie van de Experience Manager en installeer het gedownloade dossier com.adobe.livecycle.dsc.externalloginmodule-4.0.8.jar.

Het probleem is opgelost.