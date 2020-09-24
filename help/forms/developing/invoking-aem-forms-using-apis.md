---
title: AEM Forms aanroepen met API's
seo-title: AEM Forms aanroepen met API's
description: 'null'
seo-description: 'null'
uuid: d100e106-e508-4d3c-ba8c-b5fe13c9e2d6
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: coding, development-tools
discoiquuid: 1825e12c-0306-4e0a-9643-47ce1ce82132
translation-type: tm+mt
source-git-commit: 46f2ae565fe4a8cfea49572eb87a489cb5d9ebd7
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 0%

---


# AEM Forms aanroepen met API&#39;s {#invoking-aem-forms-using-apis}

Adobe Experience Manager Forms is op J2EE gebaseerde bedrijfssoftware die bestaat uit services die werken binnen een gedeelde infrastructuur. De verrichtingen van de dienst verbruiken typisch of produceren documenten. Met AEM Forms kunt u de formulierwerkstroom combineren met elektronische formulieren, documentbeveiliging en het genereren van documenten in een geïntegreerde en samenhangende set services. Deze diensten kunnen van binnen en buiten de firewall worden betreden.

Clienttoepassingen kunnen AEM Forms-services programmatisch aanroepen met een Java API, webservices, Remoting en REST. Gebruikend beleidsconsole, kunt u de dienst vormen om een eindpunt bloot te stellen dat de diensten van AEM Forms door programmatically te roepen laat. Standaard zijn de meeste services vooraf geconfigureerd om eindpunten van verwijderingen, Java en webservices beschikbaar te maken.

Uw bedrijfsvereisten bepalen welke aanroepingsmethode moet worden gebruikt. Met de Java API kunt u bijvoorbeeld de AEM Forms-functionaliteit integreren in uw Java-bedrijfstoepassingen, zoals Java Entiteiten en Boodbonen. Eveneens, kunt u de functionaliteit van AEM Forms in .NET projecten (of andere projecten integreren die met ontwikkelomgevingen worden ontwikkeld die de normen van de Webdienst steunen) gebruikend de Webdiensten.

Voor services is een servicecontainer vereist die kan worden uitgevoerd, vergelijkbaar met de manier waarop EJB&#39;s (Enterprise JavaBeans™) een J2EE-container vereisen. AEM Forms bevat slechts één implementatie van een servicecontainer. De de dienstcontainer is verantwoordelijk voor het beheren van het leven van de dienst, met inbegrip van het opstellen van het en het verzekeren dat alle verzoeken worden verzonden naar de correcte dienst. Het beheert ook documenten die een dienst verbruikt of produceert.

>[!NOTE]
>
>Programmeren met AEM formulieren bevat geen informatie over het aanroepen van AEM Forms via Gecontroleerde mappen of e-mail.

