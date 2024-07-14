---
title: Hoe kan ik AEM Forms aanroepen met behulp van API's?
description: Leer hoe u AEM Forms-services aanroept met een Java&trade; API, webservices, Remoting en REST.
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: coding, development-tools
role: Developer
exl-id: 0e92d1ad-12bd-4bfd-81cc-9be8e376c5ca
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
source-git-commit: 939a2efa64c853928a9082aa30d7338e98deb695
workflow-type: tm+mt
source-wordcount: '295'
ht-degree: 0%

---

# AEM Forms aanroepen met API&#39;s {#invoking-aem-forms-using-apis}

**de Steekproeven en de voorbeelden in dit document zijn slechts voor AEM Forms op milieu JEE.**

Adobe Experience Manager Forms is op J2EE gebaseerde bedrijfssoftware die bestaat uit services die werken binnen een gedeelde infrastructuur. De verrichtingen van de dienst verbruiken typisch of produceren documenten. Door AEM Forms te gebruiken, kunt u Forms Workflow met elektronische vormen, documentveiligheid, en documentgeneratie in een geïntegreerde en samenhangende reeks diensten combineren. Deze diensten kunnen van binnen en buiten de firewall worden betreden.

Clienttoepassingen kunnen AEM Forms-services programmatisch aanroepen met een Java™ API, webservices, Remoting en REST. Gebruikend beleidsconsole, kunt u de dienst vormen om een eindpunt bloot te stellen dat de diensten van AEM Forms door programmatically te roepen laat. Standaard zijn de meeste services vooraf geconfigureerd om eindpunten van verwijderingen, Java™ en webservices beschikbaar te maken.

Uw bedrijfsvereisten bepalen welke aanroepingsmethode moet worden gebruikt. Met de Java™ API kunt u bijvoorbeeld de AEM Forms-functionaliteit integreren in uw Java™-bedrijfstoepassingen, zoals Java™-entiteit en berichtenbonen. Eveneens, kunt u de functionaliteit van AEM Forms in .NET projecten (of andere projecten integreren die met ontwikkelomgevingen worden ontwikkeld die de normen van de Webdienst steunen) gebruikend de Webdiensten.

Voor services is een servicecontainer vereist die kan worden uitgevoerd, vergelijkbaar met de manier waarop EJB&#39;s (Enterprise JavaBeans™) een J2EE-container vereisen. AEM Forms bevat slechts één implementatie van een servicecontainer. De de dienstcontainer is verantwoordelijk voor het beheren van het leven van de dienst, met inbegrip van het opstellen van het en het verzekeren dat alle verzoeken worden verzonden naar de correcte dienst. Het beheert ook documenten die een dienst verbruikt of produceert.

>[!NOTE]
>
>Programmeren met AEM formulieren bevat geen informatie over het aanroepen van AEM Forms via Gecontroleerde mappen of e-mail.
