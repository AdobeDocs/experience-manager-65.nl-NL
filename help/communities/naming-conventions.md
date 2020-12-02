---
title: Naamgevingsconventies
seo-title: Naamgevingsconventies
description: Afbreekstreepjes in Java-pakketnaam
seo-description: Afbreekstreepjes in Java-pakketnaam
uuid: 48086e6c-c35b-4ffc-b216-d01feca7bf9a
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 5271feb9-70c6-4c82-8ac7-34a63d80e3aa
translation-type: tm+mt
source-git-commit: 22e853ecaf2696c7329a81bb9d375b1dbc74452c
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---


# Naamgevingsconventies {#naming-conventions}

## Afbreekstreepjes in Java Package Name {#hyphens-in-java-package-name}

Houd er bij het maken van een locatie voor een Java-klasse rekening mee dat de pakketnaam moet overeenkomen met de naam van de opslagplaats en dat eventuele koppeltekens in het pad correct moeten worden beschermd.

Bij AEM ontwikkeling wordt aangeraden afbreekstreepjes te gebruiken in de namen van opslagplaats-items. Afbreekstreepjes zijn echter niet toegestaan in de pakketnamen van Java.

Het onderliggende CRX-platform moet een onderscheid kunnen maken tussen een werkelijk onderstrepingsteken `_ `en een afbreekstreepje `-`. In JCR moet het afbreekstreepje daarom worden vervangen door de Unicode-waarde (u002d) en worden genummerd door een onderstrepingsteken `_`.

Als het opslagruimtepad bijvoorbeeld **/apps/my-example/component/info/Info.java** is, moet de pakketnaam `java package apps.my_002dexample.component.info;` zijn

U ziet dat een onderstrepingsteken op dezelfde manier moet worden escape, zodat `_` `_005f` wordt.
