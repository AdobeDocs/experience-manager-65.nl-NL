---
title: Naamgevingsconventies in Java&trade; pakketnaam
description: Leer over noemende overeenkomsten en het gebruik van koppeltekens in Java&trade; pakketnaam.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: 863900c3-5fe8-41a3-a151-466d0c62eeea
solution: Experience Manager
feature: Communities
role: Developer
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 0%

---

# Naamgevingsconventies {#naming-conventions}

## Afbreekstreepjes in Java™-pakketnaam {#hyphens-in-java-package-name}

Wanneer u een locatie voor een Java™-klasse maakt, moet de pakketnaam overeenkomen met de naam van de opslagplaats en moeten eventuele afbreekstreepjes in het pad correct worden beschermd.

Het gebruik van afbreekstreepjes in de namen van opslagplaats-items wordt aanbevolen bij AEM ontwikkeling, maar afbreekstreepjes zijn in Java™-pakketnamen niet toegestaan.

Het onderliggende CRX-platform moet onderscheid kunnen maken tussen een werkelijk onderstrepingsteken `_ ` en een afbreekstreepje `-` . In JCR moet het afbreekstreepje daarom worden vervangen door de Unicode-waarde (u002d) en worden genummerd door een onderstrepingsteken `_` .

Bijvoorbeeld, als de opbergweg **/apps/my-example/component/info/Info.java** is, zou de pakketnaam `java package apps.my_002dexample.component.info;` moeten zijn

U ziet dat een onderstrepingsteken op dezelfde manier moet worden genegeerd, zodat `_` `_005f` wordt.
