---
title: WebSphere-toepassingsserver starten en stoppen
seo-title: WebSphere-toepassingsserver starten en stoppen
description: Verscheidene procedures vereisen u om het geval van WebSphere te tegenhouden of te beginnen waar u AEM vormenproducten wilt opstellen. In dit document wordt beschreven hoe u de WebSphere-toepassingsserver start en stopt.
seo-description: Verscheidene procedures vereisen u om het geval van WebSphere te tegenhouden of te beginnen waar u AEM vormenproducten wilt opstellen. In dit document wordt beschreven hoe u de WebSphere-toepassingsserver start en stopt.
uuid: e0373197-aa57-4087-933d-92a86840a11a
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_application_server
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: bcd16691-67ab-4694-9e6b-c9d3e0c7bf0b
translation-type: tm+mt
source-git-commit: 67ea825215d1ca7cc2e350ed1c128c3146de45ec
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---


# WebSphere-toepassingsserver starten en stoppen {#starting-and-stopping-websphere-application-server}

Verscheidene procedures vereisen u om het geval van WebSphere te tegenhouden of te beginnen waar u AEM vormenproducten wilt opstellen. Als u niet zeker bent of de toepassingsserver is begonnen, kunt u het statuut van de Server van de Toepassing eerst bekijken WebSphere.

## De status van WebSphere Application Server {#view-the-status-of-websphere-application-server} weergeven

1. Van een bevelherinnering, ga naar `[appserver root]/bin` folder.
1. Voer de volgende opdracht in en vervang *server_name* door de naam van uw WebSphere-toepassingsserver:

   * (Windows) `serverStatus.bat`*server_name*
   * (Linux, UNIX) ./ `serverStatus.sh`*servernaam*

## WebSphere-toepassingsserver starten {#start-websphere-application-server}

1. Van een bevelherinnering, ga naar `[appserver root]/bin` folder.
1. Voer de volgende opdracht in en vervang *server_name* door de naam van uw WebSphere-toepassingsserver:

   * (Windows) `startServer.bat`*server_name*
   * (Linux, UNIX) ./ `startServer.sh`*servernaam*

## WebSphere-toepassingsserver stoppen {#stop-websphere-application-server}

1. Van een bevelherinnering, ga naar `[appserver root]/bin` folder.
1. Voer de volgende opdracht in en vervang *server_name* door de naam van uw WebSphere-toepassingsserver:

   * (Windows) `stopServer.bat`*server_name*
   * (Linux, UNIX) ./ `stopServer.sh`*servernaam*

