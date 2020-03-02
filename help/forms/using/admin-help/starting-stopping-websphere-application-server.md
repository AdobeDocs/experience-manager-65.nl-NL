---
title: WebSphere-toepassingsserver starten en stoppen
seo-title: WebSphere-toepassingsserver starten en stoppen
description: Verscheidene procedures vereisen u om de instantie van WebSphere te tegenhouden of te beginnen waar u AEM vormenproducten wilt opstellen. In dit document wordt beschreven hoe u de WebSphere-toepassingsserver start en stopt.
seo-description: Verscheidene procedures vereisen u om de instantie van WebSphere te tegenhouden of te beginnen waar u AEM vormenproducten wilt opstellen. In dit document wordt beschreven hoe u de WebSphere-toepassingsserver start en stopt.
uuid: e0373197-aa57-4087-933d-92a86840a11a
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_application_server
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: bcd16691-67ab-4694-9e6b-c9d3e0c7bf0b
translation-type: tm+mt
source-git-commit: 67ea825215d1ca7cc2e350ed1c128c3146de45ec

---


# WebSphere-toepassingsserver starten en stoppen {#starting-and-stopping-websphere-application-server}

Verscheidene procedures vereisen u om de instantie van WebSphere te tegenhouden of te beginnen waar u AEM vormenproducten wilt opstellen. Als u niet zeker bent of de toepassingsserver is begonnen, kunt u het statuut van de Server van de Toepassing eerst bekijken WebSphere.

## De status van WebSphere Application Server weergeven {#view-the-status-of-websphere-application-server}

1. Van een bevelherinnering, ga naar de `[appserver root]/bin` folder.
1. Ga het volgende bevel in, die *server_name* met de naam van uw Server van de Toepassing WebSphere vervangt:

   * (Windows) `serverStatus.bat`*server_name *
   * (Linux, UNIX) ./ `serverStatus.sh`*server_naam *

## WebSphere-toepassingsserver starten {#start-websphere-application-server}

1. Van een bevelherinnering, ga naar de `[appserver root]/bin` folder.
1. Ga het volgende bevel in, die *server_name* met de naam van uw Server van de Toepassing WebSphere vervangt:

   * (Windows) `startServer.bat`*server_name *
   * (Linux, UNIX) ./ `startServer.sh`*server_naam *

## WebSphere-toepassingsserver stoppen {#stop-websphere-application-server}

1. Van een bevelherinnering, ga naar de `[appserver root]/bin` folder.
1. Ga het volgende bevel in, die *server_name* met de naam van uw Server van de Toepassing WebSphere vervangt:

   * (Windows) `stopServer.bat`*server_name *
   * (Linux, UNIX) ./ `stopServer.sh`*server_naam *

