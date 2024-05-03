---
title: Extra stappen voor het ophalen van e-mail met bijlagen
description: Leer hoe u de fout verhelpt wanneer u geen e-mail met bijlagen voor AEM Forms op JEE-platforms kunt ophalen.
exl-id: 0d0713fb-d95a-4a95-91ef-9cdaea30e343
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
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

1. Kar downloaden als [java.mail-1.0.jar](/help/forms/using/java.mail-1.0.jar) en decomprimeer het gedownloade jar-bestand om het manifestbestand te verkrijgen.

1. Het manifestbestand gebruiken van `java.mail-1.0.jar` opgehaald uit Stap 1 om een aangepast jar-bestand te maken, bijvoorbeeld `java.mail-1.5.jar`.

1. Open het manifestbestand en vervang alle exemplaren van `1.5.0` with `1.5.6` en `Bundle-Version: 1.0` with `Bundle-Version:1.5`

1. Een aangepaste jar maken (`java.mail-1.5.jar`) bestand met de volgende opdracht in `C:\Adobe\Adobe_Experience_Manager_Forms\java\jdk\bin` map als:
   `jar -cfm java.mail-1.5.jar manifest.mf`

   In het bovenstaande bevel, *manifest.mf* de naam is van het manifestbestand en *java.mail-1.5.jar* Dit is de naam van het bestand dat wordt gemaakt nadat de bovenstaande opdracht is uitgevoerd.

1. Downloaden [javax.mail-1.5.6.redhat-1.jar](https://mvnrepository.com/artifact/com.sun.mail/javax.mail/1.5.6.redhat-1).

1. Navigeren naar `http://<server name>:<port>/lc/system/console/bundles`en verwijder de bundel met een naam als `JavaMail API (com.sun.mail.javax.mail) version 1.6.2`.

1. Installeren `java.mail-1.5.jar` verkregen uit stap 3. Met deze stap worden de verkoopeigenschappen van de JEE-implementatie opnieuw gestart. Wacht op de geïnstalleerde bundels bij `http://<server name>:<port>/lc/system/console/bundles` Status weergeven als **Actief**.

   >Als de status nog steeds **InActive**, opnieuw starten   **JBoss®** van de **Services Console**.


1. Installeren `javax.mail-1.5.6.redhat-1.jar`gedownload met gebruik van stap 5.

1. Stoppen **JBoss®** van de **Services Console** en voeg de volgende eigenschappen toe **Sling.properties** bestand:
   * `org.osgi.framework.system.packages.extra=javax.activation; version\=1.2.0`
   * `sling.bootdelegation.activation=javax.activation.*`

1. Opnieuw starten **JBoss®**.

>[!NOTE]
>
> Het wordt aanbevolen de SDK opnieuw te starten met de opdracht &#39;Ctrl + C&#39;. Het opnieuw opstarten van de AEM SDK met behulp van alternatieve methoden, bijvoorbeeld het stoppen van Java-processen, kan leiden tot inconsistenties in de AEM ontwikkelomgeving.
