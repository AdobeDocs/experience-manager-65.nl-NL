---
title: WebSphere-toepassingsserver starten en stoppen
seo-title: Starting and stopping WebSphere Application Server
description: Verscheidene procedures vereisen u om het geval van WebSphere te tegenhouden of te beginnen waar u AEM vormenproducten wilt opstellen. In dit document wordt beschreven hoe u de WebSphere-toepassingsserver start en stopt.
seo-description: Several procedures require you to stop or start the instance of WebSphere where you want to deploy AEM forms products. This document describes how to start and stop the WebSphere Application Server.
uuid: e0373197-aa57-4087-933d-92a86840a11a
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_application_server
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: bcd16691-67ab-4694-9e6b-c9d3e0c7bf0b
exl-id: 1a4e8f20-0644-4c96-9f52-f7a59521eac9
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 0%

---

# WebSphere-toepassingsserver starten en stoppen {#starting-and-stopping-websphere-application-server}

Verscheidene procedures vereisen u om het geval van WebSphere te tegenhouden of te beginnen waar u AEM vormenproducten wilt opstellen. Als u niet zeker bent of de toepassingsserver is begonnen, kunt u het statuut van de Server van de Toepassing eerst bekijken WebSphere.

## De status van WebSphere Application Server weergeven {#view-the-status-of-websphere-application-server}

1. Van een bevelherinnering, ga naar `[appserver root]/bin` directory.
1. Voer de volgende opdracht in en vervang *server_name* met de naam van uw WebSphere-toepassingsserver:

   * (Windows) `serverStatus.bat`*server_name*
   * (Linux, UNIX) ./ `serverStatus.sh`*server_name*

## WebSphere-toepassingsserver starten {#start-websphere-application-server}

1. Van een bevelherinnering, ga naar `[appserver root]/bin` directory.
1. Voer de volgende opdracht in en vervang *server_name* met de naam van uw WebSphere-toepassingsserver:

   * (Windows) `startServer.bat`*server_name*
   * (Linux, UNIX) ./ `startServer.sh`*server_name*

## WebSphere-toepassingsserver stoppen {#stop-websphere-application-server}

1. Van een bevelherinnering, ga naar `[appserver root]/bin` directory.
1. Voer de volgende opdracht in en vervang *server_name* met de naam van uw WebSphere-toepassingsserver:

   * (Windows) `stopServer.bat`*server_name*
   * (Linux, UNIX) ./ `stopServer.sh`*server_name*
