---
title: Starten en stoppen van services
description: Leer hoe u services die aan AEM Forms-modules en de toepassingsserver en -database zijn gekoppeld, kunt starten en stoppen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_services
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 55bf5196-22c6-4286-8c92-ff44d81dde49
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# Starten en stoppen van services {#starting-and-stopping-services}

Er zijn twee soorten diensten die deel van AEM vormen uitmaken:

* Services die de toepassingsserver en database voor AEM formulieren besturen.
* Diensten die AEM formuliermodules controleren

## De diensten verbonden aan AEM vormmodules beginnen of tegenhouden {#start-or-stop-the-services-associated-with-aem-forms-modules}

AEM formuliermodules (bijvoorbeeld Forms, Rights Management, Output) werken als services. Het kan gebeuren dat u de services voor deze AEM formuliermodules moet stoppen of starten. U moet bijvoorbeeld een AEM formulierservice stoppen en opnieuw starten nadat u een instelling voor de service hebt gewijzigd.

>[!NOTE]
>
> Het wordt aanbevolen de SDK opnieuw te starten met de opdracht &#39;Ctrl + C&#39;. Het opnieuw opstarten van de AEM SDK met behulp van alternatieve methoden, bijvoorbeeld het stoppen van Java-processen, kan leiden tot inconsistenties in de AEM ontwikkelomgeving.

1. In beheerconsole klikken **Services** > **Toepassingen en services** > **Servicebeheer**.
1. Voor de pagina van het Beheer van de Dienst, selecteer de controledoos naast de dienst om te stoppen of te beginnen en Einde of Begin te klikken.

## De diensten van het begin of van het einde voor de toepassingsserver en gegevensbestand {#start-or-stop-services-for-the-application-server-and-database}

Een volledige implementatie van AEM formulieren omvat een toepassingsserver en databaseservices:

* *`[application server]`* voor AEM
* *`[database]`* voor AEM

In Windows zijn deze services toegankelijk via de **Administratieve gereedschappen** > **Deelvenster Services**. Als u bijvoorbeeld AEM formulieren op JBoss hebt geïnstalleerd met de methode key turnkey, zijn de volgende services beschikbaar op uw systeem:

* JBoss voor Adobe Experience Manager-formulieren
* MySQL voor Adobe Experience Manager-formulieren

Start of stop deze services door deze te selecteren in de lijst in het deelvenster Services en vervolgens op de desbetreffende actieknop in het deelvenster te klikken.

Voer in UNIX® of Linux de volgende tekst in via een opdrachtregel, waarbij *`[service name]`* Dit is de naam van de service die u controleert:

```java
     ps -A | grep [service name]
```
