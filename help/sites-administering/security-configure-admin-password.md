---
title: Het beheerderswachtwoord configureren bij installatie
seo-title: Het beheerderswachtwoord configureren bij installatie
description: Leer hoe u het beheerderswachtwoord bij AEM installatie wijzigt.
seo-description: Leer hoe u het beheerderswachtwoord bij AEM installatie wijzigt.
uuid: 06da9890-ed63-4fb6-88d5-fd0e16bc4ceb
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
discoiquuid: 00806e6e-3578-4caa-bafa-064f200a871f
translation-type: tm+mt
source-git-commit: 1c1ade947f2cbd26b35920cfd10b1666b132bcbd
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 0%

---


# Vorm het Wachtwoord Admin op Installatie{#configure-the-admin-password-on-installation}

## Overzicht {#overview}

Sinds versie 6.3 kan AEM het beheerderswachtwoord via de opdrachtregel worden ingesteld wanneer een nieuwe instantie wordt geïnstalleerd.

Bij eerdere versies van AEM moest het wachtwoord voor de beheerdersaccount, samen met het wachtwoord voor verschillende andere consoles, na de installatie worden gewijzigd.

Deze eigenschap voegt de faciliteit toe om een nieuw beheerderwachtwoord voor de bewaarplaats en de Motor van het Servlet tijdens de installatie van een AEM instantie te plaatsen, zo eliminerend de behoefte om het achteraf manueel te doen.

>[!CAUTION]
>
>Houd er rekening mee dat deze functie niet van toepassing is op de Felix Console, waarvoor het wachtwoord handmatig moet worden gewijzigd. Zie de relevante [sectie Beveiligingscontrolelijst](/help/sites-administering/security-checklist.md#change-default-passwords-for-the-aem-and-osgi-console-admin-accounts) voor meer informatie.

## Hoe gebruik ik het? {#how-do-i-use-it}

Deze functie wordt automatisch geactiveerd als u ervoor kiest AEM te installeren via de opdrachtregel, in plaats van te dubbelklikken op de JAR vanuit een bestandssysteemverkenner.

De algemene synthax voor het runnen van een AEM instantie van de bevellijn is:

```shell
java -jar aem6.3.jar
```

Wanneer u de instantie uitvoert vanaf de opdrachtregel, krijgt u de mogelijkheid om het beheerderswachtwoord te wijzigen tijdens het installatieproces:

![chlimage_1-116](assets/chlimage_1-116a.png)

>[!NOTE]
>
>De vraag om het admin wachtwoord te veranderen zal slechts tijdens de installatie van een nieuw AEM geval verschijnen.

## De -nointeractive vlag {#using-the-nointeractive-flag} gebruiken

U kunt ook het wachtwoord opgeven in een eigenschappenbestand. Dit wordt gedaan door de `-nointeractive` vlag te gebruiken die met `-Dadmin.password.file` systeembezit wordt gecombineerd.

Hieronder ziet u een voorbeeld:

```shell
java -Dadmin.password.file =/path/to/passwordfile.properties -jar aem6.3.jar -nointeractive
```

Het wachtwoord binnen het `passwordfile.properties` dossier moet het hieronder formaat hebben:

```xml
admin.password = 12345678
```

>[!NOTE]
>
>Als u de `-nointeractive` parameter zonder `-Dadmin.password.file` systeembezit eenvoudig gebruikt, AEM zal het standaard admin wachtwoord gebruiken zonder u te vragen om het te veranderen, hoofdzakelijk het herhalen gedrag van vroegere versies. Deze niet-interactieve modus kan worden gebruikt voor geautomatiseerde installaties die de opdrachtregel in een installatiescript gebruiken.

