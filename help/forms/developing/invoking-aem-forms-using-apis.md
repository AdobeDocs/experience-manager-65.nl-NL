---
title: AEM-formulieren aanroepen met API's
seo-title: AEM-formulieren aanroepen met API's
description: 'null'
seo-description: 'null'
uuid: d100e106-e508-4d3c-ba8c-b5fe13c9e2d6
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: development-tools
discoiquuid: 1825e12c-0306-4e0a-9643-47ce1ce82132
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# AEM-formulieren aanroepen met API&#39;s {#invoking-aem-forms-using-apis}

Adobe Experience Manager Forms is op J2EE gebaseerde bedrijfssoftware die bestaat uit services die werken binnen een gedeelde infrastructuur. De verrichtingen van de dienst verbruiken typisch of produceren documenten. Met AEM Forms kunt u de formulierwerkstroom combineren met elektronische formulieren, documentbeveiliging en het genereren van documenten in een geïntegreerde en samenhangende set services. Deze diensten kunnen van binnen en buiten de firewall worden betreden.

Clienttoepassingen kunnen via programmacode AEM Forms-services aanroepen met behulp van een Java API, webservices, Remoting en REST. Gebruikend beleidsconsole, kunt u de dienst vormen om een eindpunt bloot te stellen dat de diensten van Vormen AEM door programmatically aangehaald laat. Standaard zijn de meeste services vooraf geconfigureerd om eindpunten van verwijderingen, Java en webservices beschikbaar te maken.

Uw bedrijfsvereisten bepalen welke aanroepingsmethode moet worden gebruikt. Met de Java API kunt u bijvoorbeeld de functionaliteit van AEM-formulieren integreren in uw Java-bedrijfstoepassingen, zoals Java Entiteiten en Bonen met berichten. Eveneens, kunt u functionaliteit van Vormen AEM in .NET projecten (of andere projecten integreren die met ontwikkelomgevingen worden ontwikkeld die de normen van de Webdienst steunen) gebruikend de Webdiensten.

Voor services is een servicecontainer vereist die kan worden uitgevoerd, vergelijkbaar met de manier waarop EJB&#39;s (Enterprise JavaBeans™) een J2EE-container vereisen. AEM Forms omvat slechts één implementatie van een de dienstcontainer. De de dienstcontainer is verantwoordelijk voor het beheren van het leven van de dienst, met inbegrip van het opstellen van het en het verzekeren dat alle verzoeken worden verzonden naar de correcte dienst. Het beheert ook documenten die een dienst verbruikt of produceert.

>[!NOTE]
>
>Programmeren met AEM-formulieren bevat geen informatie over het aanroepen van AEM-formulieren via Gecontroleerde mappen of e-mail.

