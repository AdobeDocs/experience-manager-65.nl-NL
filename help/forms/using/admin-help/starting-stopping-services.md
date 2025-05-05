---
title: Starten en stoppen van services
description: Leer hoe u services die aan AEM Forms-modules en de toepassingsserver en -database zijn gekoppeld, kunt starten en stoppen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_services
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 55bf5196-22c6-4286-8c92-ff44d81dde49
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: 6a9806d8f40f711a610c130c63d9ab9b2460d075
workflow-type: tm+mt
source-wordcount: '311'
ht-degree: 0%

---

# Starten en stoppen van services {#starting-and-stopping-services}

>[!NOTE]
> 
> Zorg ervoor dat de gebruiker beheerdersrechten heeft om toegang te krijgen tot de beheerdersconsole.

Er zijn twee soorten diensten die deel van AEM vormen uitmaken:

* Services die de toepassingsserver en database voor AEM formulieren besturen.
* Diensten die AEM formuliermodules controleren

## De diensten verbonden aan AEM vormmodules beginnen of tegenhouden {#start-or-stop-the-services-associated-with-aem-forms-modules}

AEM formuliermodules (bijvoorbeeld Forms, Rights Management, Output) werken als services. Het kan gebeuren dat u de services voor deze AEM formuliermodules moet stoppen of starten. U moet bijvoorbeeld een AEM formulierservice stoppen en opnieuw starten nadat u een instelling voor de service hebt gewijzigd.

>[!NOTE]
>
> U wordt aangeraden de SDK opnieuw op te starten met de opdracht &#39;Ctrl + C&#39;. Het opnieuw opstarten van de AEM SDK met behulp van alternatieve methoden, bijvoorbeeld het stoppen van Java-processen, kan leiden tot inconsistenties in de AEM ontwikkelomgeving.

1. In beleidsconsole klik **de Diensten van 0&rbrace; >** Toepassingen en de Diensten **>** Beheer van de Dienst **.**
1. Voor de pagina van het Beheer van de Dienst, selecteer de controledoos naast de dienst om te stoppen of te beginnen en Einde of Begin te klikken.

## De diensten van het begin of van het einde voor de toepassingsserver en gegevensbestand {#start-or-stop-services-for-the-application-server-and-database}

Een volledige implementatie van AEM formulieren omvat een toepassingsserver en databaseservices:

* *`[application server]`* voor AEM formulieren
* *`[database]`* voor AEM formulieren

Op Vensters, zijn deze diensten toegankelijk door **Administratieve Hulpmiddelen** > **het paneel van de Diensten**. Als u bijvoorbeeld AEM formulieren op JBoss hebt geïnstalleerd met de methode key turnkey, zijn de volgende services beschikbaar op uw systeem:

* JBoss voor Adobe Experience Manager-formulieren
* MySQL voor Adobe Experience Manager-formulieren

Start of stop deze services door deze te selecteren in de lijst in het deelvenster Services en vervolgens op de desbetreffende actieknop in het deelvenster te klikken.

Voer in UNIX® of Linux de volgende tekst in vanaf een opdrachtregel, waarbij *`[service name]`* de naam is van de service die u controleert:

```java
     ps -A | grep [service name]
```
