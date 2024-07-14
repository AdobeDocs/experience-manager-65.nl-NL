---
title: Extra stappen voor het ophalen van e-mail met bijlagen
description: Leer hoe u de fout verhelpt wanneer u geen e-mail met bijlagen voor AEM Forms op JEE-platforms kunt ophalen.
exl-id: 0d0713fb-d95a-4a95-91ef-9cdaea30e343
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: 9f59606bb58b9e90f07bd22e89f3213afb54a697
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# Kan geen e-mail ophalen met bijlagen voor AEM Forms op JEE-platforms{#unable-to-get-email-with-attachments}

De kwestie is op de volgende versie van toepassing:

* Experience Manager 6.5 Forms

## Probleem {#issue}

De gebruiker kan geen handelingen uitvoeren zoals PDF verzenden via e-mail of Bijlagen opnemen met de verzendconfiguratie.

## Oplossing {#solution}

1. Download jar als [ java.mail-1.0.jar ](/help/forms/using/java.mail-1.0.jar) en unzip het gedownloade jar dossier om het manifestdossier te verkrijgen.

1. Gebruik het manifestbestand van `java.mail-1.0.jar` dat u hebt opgehaald uit stap 1 om een aangepast jar-bestand te maken, bijvoorbeeld `java.mail-1.5.jar` .

1. Open het manifestbestand en vervang `1.5.0` overal door `1.5.6` en `Bundle-Version: 1.0` door `Bundle-Version:1.5`

1. Maak een aangepast jar-bestand (`java.mail-1.5.jar` ) met de volgende opdracht in de `C:\Adobe\Adobe_Experience_Manager_Forms\java\jdk\bin` -map als:
   `jar -cfm java.mail-1.5.jar manifest.mf`

   In het bovengenoemde bevel, *manifest.mf* is de naam van het manifestdossier en *java.mail-1.5.jar* is de naam van het dossier dat na het uitvoeren van bovengenoemd bevel zou worden gecreeerd.

1. Download [ javax.mail-1.5.6.redhat-1.jar ](https://mvnrepository.com/artifact/com.sun.mail/javax.mail/1.5.6.redhat-1).

1. Navigeer naar `http://<server name>:<port>/lc/system/console/bundles` en verwijder de bundel met de naam `JavaMail API (com.sun.mail.javax.mail) version 1.6.2` .

1. Installeer `java.mail-1.5.jar` uit stap 3. Met deze stap worden de verkoopeigenschappen van de JEE-implementatie opnieuw gestart. Wacht op de geïnstalleerde bundels bij `http://<server name>:<port>/lc/system/console/bundles` om Status als **Actieve** te tonen.

   >In het geval dat de status nog **InActive** is, nieuw begin   **JBoss®** van de **Console van de Diensten**.


1. Installeer `javax.mail-1.5.6.redhat-1.jar` gedownload dossier gebruikend stap 5.

1. Het eind **JBoss®** van de **Console van de Diensten** en voegt de volgende eigenschappen aan **toe Sling.properties** dossier:
   * `org.osgi.framework.system.packages.extra=javax.activation; version\=1.2.0`
   * `sling.bootdelegation.activation=javax.activation.*`

1. Begin **JBoss®** opnieuw.

>[!NOTE]
>
> Het wordt aanbevolen de SDK opnieuw te starten met de opdracht &#39;Ctrl + C&#39;. Het opnieuw opstarten van de AEM SDK met behulp van alternatieve methoden, bijvoorbeeld het stoppen van Java-processen, kan leiden tot inconsistenties in de AEM ontwikkelomgeving.
