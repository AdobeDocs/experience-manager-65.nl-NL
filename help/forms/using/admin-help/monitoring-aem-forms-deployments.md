---
title: Implementaties van AEM-formulieren controleren
seo-title: Implementaties van AEM-formulieren controleren
description: U kunt de implementatie van AEM-formulieren zowel op systeemniveau als op intern niveau controleren. Meer informatie over het controleren van AEM-formulierimplementaties in dit document.
seo-description: U kunt de implementatie van AEM-formulieren zowel op systeemniveau als op intern niveau controleren. Meer informatie over het controleren van AEM-formulierimplementaties in dit document.
uuid: 032b7a93-3069-4ad5-a8c6-4c160f290669
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_aem_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: b3e7bca0-5aaf-4f28-bddb-fd7e8ed72ee8
translation-type: tm+mt
source-git-commit: 1343cc33a1e1ce26c0770a3b49317e82353497ab
workflow-type: tm+mt
source-wordcount: '634'
ht-degree: 0%

---


# Implementaties van AEM-formulieren controleren {#monitoring-aem-forms-deployments}

U kunt de implementatie van AEM-formulieren zowel op systeemniveau als op intern niveau controleren. U kunt specialistische beheersinstrumenten zoals HP OpenView, IBM Tivoli, en CA UniCenter en een derdeJMX monitor gebruiken genoemd *JConsole* om de activiteit van Java specifiek te controleren. De implementatie van een monitoringstrategie verbetert de beschikbaarheid, betrouwbaarheid en prestaties van uw AEM-formulieren.

Voor meer informatie over het controleren van AEM vormplaatsingen, zie [Een technische gids voor het controleren van AEM vormplaatsingen](https://www.adobe.com/devnet/livecycle/pdfs/lc_monitoring_wp_ue.pdf).

## Bewaking met behulp van MBeans {#monitoring-using-mbeans}

AEM-formulieren bieden twee geregistreerde MB&#39;s die navigatie- en statistische informatie bieden. Dit zijn de enige MBeans die voor integratie en inspectie worden gesteund:

* **ServiceStatistic:** Dit MBean verstrekt informatie over de naam van de Dienst en zijn versie.
* **OperationStatistic:** Dit MBean verstrekt de statistiek van de dienst van elke vormserver. Dit is waar de beheerders informatie over een bepaalde dienst zoals oproepingstijd, aantal fouten, etc. kunnen krijgen.

### ServiceStatisticMbean, openbare interfaces {#servicestatisticmbean-public-interfaces}

Deze openbare interfaces van ServiceStatistic MBean kunnen voor testdoeleinden worden betreden:

```java
 public String getServiceId();
 public int getMajorVersion();
 public int getMinorVersion();
```

### Openbare interfaces van OperationStatisticMbean {#operationstatisticmbean-public-interfaces}

Deze openbare interfaces van OperationStatistic MBean kunnen voor testdoeleinden worden betreden:

```java
 // InvocationCount: The number of times the method is invoked.
 public long getInvocationCount();
 // InvocationStartTime: The time at which the method started to execute.
 public long getInvocationStartTime();
 // InvocationEndTime: The time at which the method finished execution.
 public long getInvocationEndTime();
 // InvocationTime: The time taken for the execution of the method.
 public long getInvocationTime();
 // LastSamplingDateTime: Convert InvocationStartTime to a formatted string
 public String getLastSamplingDateTime();
 // MaxInvocationTime: The maximum time taken for the execution of the method.
 public long getMaxInvocationTime();
 // MinInvocationTime: The minimum time taken for the execution of the method.
 public long getMinInvocationTime();
 // AverageInvocationTime: the averege execution time taken for the execution of the method.
 public double getAverageInvocationTime();
 // ExceptionCount: The number of times the method has thrown an Exception.
 public long getExceptionCount();
 // ExceptionMessage: The message of the last exception occurred.
 public String getExeptionMessage();
 public void setExceptionMessage(String errorMessage);
```

### MBean Tree &amp; Operation Statistics {#mbean-tree-operation-statistics}

Met behulp van een JMX-console (JConsole) zijn statistieken van OperationStatistic MBean beschikbaar. Deze statistieken zijn de attributen van MBean, en kunnen onder de volgende hiërarchieboom worden genavigeerd:

**MBean tree**

**Naam Adobe-domein:** Afhankelijk van de toepassingsserver. Als het domein niet wordt gedefinieerd door de toepassingsserver, wordt standaard adobe.com gebruikt.

**ServiceType:** AdobeService is de naam die wordt gebruikt om alle services weer te geven.

**AdobeServiceName:** Servicenaam of Service-id.

**Versie:** Versie van de service.

**Bewerkingsstatistieken**

**Aanroepingstijd:** Tijd die nodig is om de methode uit te voeren. Dit omvat niet de tijd het verzoek in series wordt vervaardigd, van cliënt aan server wordt overgebracht, en deserialized.

**Aantal aanroepen:** Het aantal tijden de dienst wordt aangehaald.

**Gemiddelde aanroepingstijd:** Gemiddelde tijd van alle aanroepen die zijn uitgevoerd sinds de server is gestart.

**Maximale aanroepingstijd:** De duur van de langste aanroep die is uitgevoerd sinds de server is gestart.

**Minimale aanroepingstijd:** De duur van de kortste aanroep die is uitgevoerd sinds de server is gestart.

**Aantal uitzonderingen:** Aantal oproepen die tot mislukkingen hebben geleid.

**Uitzonderingsbericht:** Het foutbericht van de laatste uitzondering die is opgetreden.

**Datum laatste monsterneming:** De datum van de laatste aanroeping.

**Tijdeenheid:** De standaardwaarde is millisecond.

Voor JMX-bewaking hebben de toepassingsservers doorgaans een bepaalde configuratie nodig. Raadpleeg de documentatie bij de toepassingsserver voor meer informatie.

### Voorbeelden van het instellen van open JMX-toegang {#examples-of-how-to-set-up-open-jmx-access}

**JBoss 4.0.3/4.2.0 - het JVM-opstarten configureren**

Om MBans van JConsole te bekijken, vorm de JBoss startparameters van de JVM van de toepassingsserver. Zorg ervoor dat JBoss wordt gestart vanuit het bestand run.bat/sh.

1. Bewerk het bestand run.bat onder InstallJBoss/bin.
1. Zoek de lijn JAVA_OPTS en voeg het volgende toe:

   ```shell
    -Dcom.sun.management.jmxremote -Dcom.sun.management.jmxremote.port=9088 -Dcom.sun.management.jmxremote.authenticate=false -Dcom.sun.management.jmxremote.ssl=false
   ```

**WebLogic 9.2/10 - vorm het JVM opstarten**

1. Bewerk het startWebLogic.bat-bestand onder `[WebLogic home]/user_projects/domains/Adobe_Live_Cycle/bin`.
1. Zoek de lijn JAVA_OPTS en voeg het volgende toe:

   ```shell
    -Dcom.sun.management.jmxremote -Dcom.sun.management.jmxremote.port=9088 -Dcom.sun.management.jmxremote.authenticate=false -Dcom.sun.management.jmxremote.ssl=false
   ```

1. Start WebLogic opnieuw.

>[!NOTE]
>
>Voor WebLogic kunt u toegang krijgen tot de MBean via extern of IOOP.

**De MBean extern openen**

1. Start JConsole voor nieuwe verbinding en klik op extern tabblad.
1. Voer de hostnaam en poort in (9088, het nummer dat u opgeeft tijdens de startopties van JVM).

**Websfeer 6.1 - JVM-opstarten configureren**

1. Voeg op de beheerconsole (Application Server > server1 > Process Definition > JVM) de volgende regel toe aan het veld voor Generic JVM-argument:

   ```shell
    -Djavax.management.builder.initial= -Dcom.sun.management.jmxremote
   ```

1. Voeg de volgende drie regels toe aan het bestand /opt/IBM/WebSphere/AppServer/java/jre/lib/management/management.properties (of &lt;Your Websphere JRE>/ lib/management/management.properties) of verwijder de commentaarmarkering:

   ```shell
    com.sun.management.jmxremote.port=9999 //any port you like, but make sure you use this port when you connect
    com.sun.management.jmxremote.authenticate=false
    com.sun.management.jmxremote.ssl=false
   ```

1. Start WebSphere opnieuw.

