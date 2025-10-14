---
title: Het beheerderswachtwoord configureren bij installatie
description: Leer hoe u het beheerderswachtwoord bij Adobe Experience Manager-installatie wijzigt.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
exl-id: b55ff9d5-8139-4ecf-ba09-5cf88207c5c4
solution: Experience Manager, Experience Manager Sites
feature: Security
role: Admin
source-git-commit: 48d12388d4707e61117116ca7eb533cea8c7ef34
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---

# Het beheerderswachtwoord configureren bij installatie{#configure-the-admin-password-on-installation}

## Overzicht {#overview}

Sinds versie 6.3 kan in Adobe Experience Manager (AEM) het beheerderswachtwoord worden ingesteld via de opdrachtregel wanneer een nieuwe instantie wordt geïnstalleerd.

Bij eerdere versies van AEM moest het wachtwoord voor de beheerdersaccount, samen met het wachtwoord voor verschillende andere consoles, na de installatie worden gewijzigd.

Deze eigenschap voegt de faciliteit toe om een nieuw beheerderwachtwoord voor de bewaarplaats en de Motor van het Servlet tijdens de installatie van een AEM instantie te plaatsen, zo eliminerend de behoefte om het achteraf manueel te doen.

>[!CAUTION]
>
>De functie is niet van toepassing op de Felix Console, waarvoor het wachtwoord handmatig moet worden gewijzigd. Voor meer informatie, zie de relevante [&#x200B; sectie van Controlelijst van de Veiligheid &#x200B;](/help/sites-administering/security-checklist.md#change-default-passwords-for-the-aem-and-osgi-console-admin-accounts).

## Hoe gebruik ik het? {#how-do-i-use-it}

Deze functie wordt automatisch geactiveerd als u ervoor kiest om AEM via de opdrachtregel te installeren in plaats van te dubbelklikken op de JAR vanuit een bestandssysteemverkenner.

De algemene syntaxis voor het uitvoeren van een AEM instantie vanaf de opdrachtregel is:

```shell
java -jar aem6.3.jar
```

Nadat u de instantie via de opdrachtregel hebt uitgevoerd, kunt u het beheerderswachtwoord tijdens het installatieproces wijzigen:

![&#x200B; chlimage_1-116 &#x200B;](assets/chlimage_1-116a.png)

>[!NOTE]
>
>De vraag om het beheerderswachtwoord te wijzigen verschijnt slechts tijdens de installatie van een nieuw AEM.

## De markering -nointeractive gebruiken {#using-the-nointeractive-flag}

U kunt ook het wachtwoord opgeven in een eigenschappenbestand. Dit wordt gedaan door de markering `-nointeractive` te gebruiken in combinatie met de eigenschap `-Dadmin.password.file` system.

Hieronder ziet u een voorbeeld:

```shell
java -Dadmin.password.file =/path/to/passwordfile.properties -jar aem6.3.jar -nointeractive
```

Het wachtwoord in het `passwordfile.properties` -bestand moet de volgende indeling hebben:

```xml
admin.password = 12345678
```

>[!NOTE]
>
>Als u de parameter `-nointeractive` zonder de eigenschap system van `-Dadmin.password.file` gebruikt, gebruikt AEM het standaard beheerderswachtwoord zonder dat u wordt gevraagd dit te wijzigen, wat in feite het gedrag van eerdere versies is. Deze niet-interactieve modus kan worden gebruikt voor geautomatiseerde installaties die de opdrachtregel in een installatiescript gebruiken.
