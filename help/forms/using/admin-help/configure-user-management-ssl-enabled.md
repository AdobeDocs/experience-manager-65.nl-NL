---
title: Gebruikersbeheer configureren voor een LDAP-server die geschikt is voor SSL
description: Leer hoe u gebruikersbeheer configureert voor een LDAP-server die geschikt is voor SSL, zodat synchronisatie correct werkt via LDAPS.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 606e84f2-6728-47a9-a439-dbe2e55100ad
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '279'
ht-degree: 0%

---

# Gebruikersbeheer configureren voor een LDAP-server die geschikt is voor SSL {#configure-user-management-for-an-ssl-enabled-ldap-server}

Synchronisatie werkt alleen correct via LDAPS als de LDAP-certificaten die de certificeringsinstantie (CA) heeft uitgegeven, aanwezig zijn in de JRE-omgeving (Java Runtime Environment) van de toepassingsserver. Importeer het certificaat in het JRE-cacerts-bestand van de toepassingsserver, dat zich gewoonlijk in het *[JAVA_HOME]*/jre/lib/security/cacerts directory.

1. Schakel SSL in op de directoryserver. Zie de documentatie die is geleverd door de leverancier van de directory voor meer informatie.
1. Een clientcertificaat exporteren vanuit de directoryserver.
1. Gebruik het hulpprogramma Keytool om het clientcertificaatbestand te importeren in het standaard JVM™-certificaatarchief van de AEM formuliertoepassingsserver. De procedure voor deze taak varieert, afhankelijk van uw JVM en de installatiepaden van de client. Als u bijvoorbeeld BEA WebLogic Server met JDK 1.5 gebruikt, typt u deze tekst via een opdrachtprompt:

   `keytool -import -alias`*alias* `-file certificatename -keystore C:\bea\jdk15_04\jre\lib\security\cacerts`

1. Typ desgevraagd het wachtwoord. (Voor Java is het standaardwachtwoord `changeit`.) Er verschijnt een bericht met de mededeling dat het certificaat is geïmporteerd.
1. Typ desgevraagd `Yes` om het certificaat te vertrouwen.
1. Schakel SSL in Gebruikersbeheer in en selecteer bij het configureren van de directory-instellingen Ja voor de SSL-optie en wijzig de poortinstelling dienovereenkomstig. Het standaardpoortnummer is 636.

>[!NOTE]
>
>Als u problemen ondervindt met SSL, gebruikt u een LDAP-browser om te controleren of deze toegang heeft tot het LDAP-systeem wanneer SSL wordt gebruikt. Als de LDAP-browser geen toegang kan krijgen, is uw certificaat- of toepassingsserver niet correct geconfigureerd. Als de LDAP-browser correct werkt en u nog steeds problemen ondervindt, wordt Gebruikersbeheer niet correct geconfigureerd.
