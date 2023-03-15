---
title: Het beheerderswachtwoord configureren bij installatie
seo-title: Configure the Admin Password on Installation
description: Leer hoe u het beheerderswachtwoord bij AEM installatie wijzigt.
seo-description: Learn how to change the Admin Password on AEM Installation.
uuid: 06da9890-ed63-4fb6-88d5-fd0e16bc4ceb
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
discoiquuid: 00806e6e-3578-4caa-bafa-064f200a871f
exl-id: b55ff9d5-8139-4ecf-ba09-5cf88207c5c4
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# Het beheerderswachtwoord configureren bij installatie{#configure-the-admin-password-on-installation}

## Overzicht {#overview}

Sinds versie 6.3 kan AEM het beheerderswachtwoord via de opdrachtregel worden ingesteld wanneer een nieuwe instantie wordt geïnstalleerd.

Bij eerdere versies van AEM moest het wachtwoord voor de beheerdersaccount, samen met het wachtwoord voor verschillende andere consoles, na de installatie worden gewijzigd.

Deze eigenschap voegt de faciliteit toe om een nieuw beheerderwachtwoord voor de bewaarplaats en de Motor van het Servlet tijdens de installatie van een AEM instantie te plaatsen, zo eliminerend de behoefte om het achteraf manueel te doen.

>[!CAUTION]
>
>Houd er rekening mee dat deze functie niet van toepassing is op de Felix Console, waarvoor het wachtwoord handmatig moet worden gewijzigd. Zie voor meer informatie de relevante [Sectie Beveiligingscontrolelijst](/help/sites-administering/security-checklist.md#change-default-passwords-for-the-aem-and-osgi-console-admin-accounts).

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

## De markering -nointeractive gebruiken {#using-the-nointeractive-flag}

U kunt ook het wachtwoord opgeven in een eigenschappenbestand. Dit wordt gedaan door te gebruiken `-nointeractive` markering gecombineerd met`-Dadmin.password.file` system, eigenschap.

Hieronder ziet u een voorbeeld:

```shell
java -Dadmin.password.file =/path/to/passwordfile.properties -jar aem6.3.jar -nointeractive
```

Het wachtwoord in de `passwordfile.properties` bestand moet de volgende indeling hebben:

```xml
admin.password = 12345678
```

>[!NOTE]
>
>Als u gewoon de `-nointeractive` parameter zonder `-Dadmin.password.file` systeemeigenschap, AEM het standaardbeheerderswachtwoord gebruiken zonder dat u wordt gevraagd dit te wijzigen, in feite gedrag uit eerdere versies repliceert. Deze niet-interactieve modus kan worden gebruikt voor geautomatiseerde installaties die de opdrachtregel in een installatiescript gebruiken.
