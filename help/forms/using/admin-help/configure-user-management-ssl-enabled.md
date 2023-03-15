---
title: Gebruikersbeheer configureren voor een LDAP-server die geschikt is voor SSL
seo-title: Configure User Management for an SSL-enabled LDAP server
description: Leer hoe u gebruikersbeheer configureert voor een LDAP-server die geschikt is voor SSL, zodat synchronisatie correct werkt via LDAPS.
seo-description: Learn how  to configure User Management for an SSL-enabled LDAP server to enable synchronization to work properly over LDAPS.
uuid: 4b3f8ac7-fa38-4adf-a851-82d55fe431fe
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: e6e7e2fa-579d-4b36-8598-6ced469a94b1
exl-id: 606e84f2-6728-47a9-a439-dbe2e55100ad
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 0%

---

# Gebruikersbeheer configureren voor een LDAP-server die geschikt is voor SSL {#configure-user-management-for-an-ssl-enabled-ldap-server}

Synchronisatie werkt alleen correct via LDAPS als de LDAP-certificaten die de certificeringsinstantie (CA) heeft uitgegeven, aanwezig zijn in de JRE-omgeving (Java Runtime Environment) van de toepassingsserver. Importeer het certificaat in het JRE-cacerts-bestand van de toepassingsserver, dat zich gewoonlijk in het *[JAVA_HOME]*/jre/lib/security/cacerts directory.

1. Schakel SSL in op de directoryserver. Zie de documentatie die is geleverd door de leverancier van de directory voor meer informatie.
1. Exporteer een clientcertificaat van de directoryserver.
1. Gebruik het hulpprogramma Keytool om het clientcertificaatbestand te importeren in het standaard JVM™-certificaatarchief van de AEM formuliertoepassingsserver. De procedure voor deze taak varieert, afhankelijk van uw JVM- en clientinstallatiepaden. Als u bijvoorbeeld BEA WebLogic Server met JDK 1.5 gebruikt, typt u deze tekst via een opdrachtprompt:

   `keytool -import -alias`*alias* `-file certificatename -keystore C:\bea\jdk15_04\jre\lib\security\cacerts`

1. Typ desgevraagd het wachtwoord. (Voor Java is het standaardwachtwoord `changeit`.) Er verschijnt een bericht met de mededeling dat het certificaat is geïmporteerd.
1. Typ desgevraagd `Yes` om het certificaat te vertrouwen.
1. Schakel SSL in Gebruikersbeheer in en selecteer bij het configureren van de directory-instellingen Ja voor de SSL-optie en wijzig de poortinstelling dienovereenkomstig. Het standaardpoortnummer is 636.

>[!NOTE]
>
>Als u problemen ondervindt met SSL, gebruikt u een LDAP-browser om te controleren of deze toegang heeft tot het LDAP-systeem wanneer SSL wordt gebruikt. Als de LDAP-browser geen toegang kan krijgen, is uw certificaat- of toepassingsserver niet correct geconfigureerd. Als de LDAP-browser correct werkt en u nog steeds problemen ondervindt, wordt Gebruikersbeheer niet correct geconfigureerd.
