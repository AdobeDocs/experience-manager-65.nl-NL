---
title: Naamgevingsconventies in de naam van het Java-pakket
description: Afbreekstreepjes in Java-pakketnaam
uuid: 48086e6c-c35b-4ffc-b216-d01feca7bf9a
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 5271feb9-70c6-4c82-8ac7-34a63d80e3aa
exl-id: 863900c3-5fe8-41a3-a151-466d0c62eeea
source-git-commit: a2fd3c0c1892ac648c87ca0dec440e22144c37a2
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 0%

---

# Naamgevingsconventies {#naming-conventions}

## Afbreekstreepjes in Java-pakketnaam {#hyphens-in-java-package-name}

Houd er bij het maken van een locatie voor een Java-klasse rekening mee dat de pakketnaam moet overeenkomen met de naam van de opslagplaats en dat eventuele koppeltekens in het pad correct moeten worden beschermd.

Bij AEM ontwikkeling wordt aangeraden afbreekstreepjes te gebruiken in de namen van opslagplaats-items. Afbreekstreepjes zijn echter niet toegestaan in de pakketnamen van Java.

Het onderliggende CRX-platform moet een onderscheid kunnen maken tussen een werkelijk onderstrepingsteken `_ `en een afbreekstreepje `-`. In JCR moet het afbreekstreepje daarom worden vervangen door de unicode-waarde (u002d) en met een onderstrepingsteken worden genummerd `_`.

Bijvoorbeeld als het repository pad is **/apps/my-example/component/info/Info.java** moet de pakketnaam `java package apps.my_002dexample.component.info;`

U ziet dat een onderstrepingsteken op dezelfde manier moet worden overgeslagen, zodat: `_` wordt `_005f`.
