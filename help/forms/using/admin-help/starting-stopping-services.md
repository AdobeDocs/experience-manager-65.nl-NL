---
title: Starten en stoppen van services
seo-title: Starten en stoppen van services
description: Leer hoe u services die aan AEM Forms-modules en de toepassingsserver en -database zijn gekoppeld, kunt starten en stoppen.
seo-description: Leer hoe u services die aan AEM Forms-modules en de toepassingsserver en -database zijn gekoppeld, kunt starten en stoppen.
uuid: 8c831cb2-4165-4118-8a09-764cec4e5e05
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_services
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: b93060bd-c6e1-40d2-8acd-ccafb8ed56da
translation-type: tm+mt
source-git-commit: 1343cc33a1e1ce26c0770a3b49317e82353497ab
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%

---


# Services {#starting-and-stopping-services} starten en stoppen

Er zijn twee soorten diensten die deel van AEM vormen uitmaken:

* Services die de toepassingsserver en database voor AEM formulieren besturen.
* Diensten die AEM vormen modules controleren

## De services voor AEM formuliermodules starten of stoppen {#start-or-stop-the-services-associated-with-aem-forms-modules}

AEM formuliermodules (bijvoorbeeld Forms, Rights Management, Output) werken als services. Het kan gebeuren dat u de services voor deze AEM formuliermodules moet stoppen of starten. U moet bijvoorbeeld een AEM formulierservice stoppen en opnieuw starten nadat u een instelling voor de service hebt gewijzigd.

1. Klik in de beheerconsole op **Services** > **Toepassingen en services** > **Servicebeheer**.
1. Voor de pagina van het Beheer van de Dienst, selecteer de controledoos naast de dienst om te stoppen of te beginnen en Einde of Begin te klikken.

## Start- of stopservices voor de toepassingsserver en database {#start-or-stop-services-for-the-application-server-and-database}

Een volledige implementatie van AEM formulieren omvat een toepassingsserver en databaseservices:

* *`[application server]`* voor AEM
* *`[database]`* voor AEM

In Windows zijn deze services toegankelijk via **Systeembeheer** > **Deelvenster Services**. Als u bijvoorbeeld AEM formulieren op JBoss hebt geïnstalleerd met de methode key turnkey, zijn de volgende services beschikbaar op uw systeem:

* JBoss voor Adobe Experience Manager-formulieren
* MySQL voor Adobe Experience Manager-formulieren

Start of stop deze services door deze te selecteren in de lijst in het deelvenster Services en vervolgens op de desbetreffende actieknop in het deelvenster te klikken.

Voer in UNIX® of Linux de volgende tekst in vanaf een opdrachtregel, waarbij *`[service name]`* de naam is van de service die u controleert:

```java
     ps -A | grep [service name]
```

