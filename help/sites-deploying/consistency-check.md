---
title: Consistentie- en reiscontroles
description: Leer hoe u consistentiecontroles en transversale controles uitvoert.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
feature: Configuring
exl-id: 10dde29b-5dc7-4d4e-80ae-3d4fd0397f7e
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 0%

---

# Consistentie- en reiscontroles{#consistency-and-traversal-checks}

Tijdens de upgrade kunnen er problemen optreden als gevolg van inconsistenties in de werkruimte. U kunt een testupgrade uitvoeren om te zien of dit een probleem is, of de consistentiecontroles uitvoeren als een preventieve actie.

Als u een testverbetering in werking stelt die wegens werkruimteinconsistenties ontbreekt, ziet u ingangen gelijkend op het volgende in crx-quickstart/logs/crx/error.log:

```xml
*ERROR* TarPersistenceManager: No bundle found for uuid 'deadbeef-cafe-babe-cafe-babecafebabe'
 ...
*ERROR* RepositoryImpl: Failed to initialize workspace 'crx.default'
javax.jcr.RepositoryException: Error indexing workspace: Error indexing workspace: Error indexing workspace
...
```

## Een consistentiecontrole uitvoeren {#perform-a-consistency-check}

Om een consistentiecontrole uit te voeren, navigeer aan de beleidspagina voor JMX Mbean **com.adobe.granite (Bewaarplaats)**. Ga in het AEM hoofdscherm naar:

**Hulpmiddelen > de Console van het Web > Hoofd (op menubar) > JMX > com.adobe.granite (Bewaarplaats)**

Op een standaardinstallatie, wordt het hier gevonden: **[|Show me|](http://localhost:4502/system/console/jmx/com.adobe.granite%3Atype%3DRepository)**

In de **sectie van Verrichtingen** van de pagina, vindt u twee methodes: **`traversalCheck`** en **`consistencyCheck`**. Als u een controle wilt uitvoeren, klikt u op de bewerking en voert u de gewenste parameters in.

![ chlimage_1-117 ](assets/chlimage_1-117.png)
