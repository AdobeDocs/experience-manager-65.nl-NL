---
title: Implementaties van AEM controleren
description: U kunt AEM formulierimplementaties zowel op systeemniveau als op intern niveau controleren. Meer informatie over het controleren AEM formulierimplementaties in dit document.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_aem_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 931e8095-5c7c-4c1f-b95b-75ac2827d4f3
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: e821be5233fd5f6688507096790d219d25903892
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 0%

---

# Implementaties van AEM controleren {#monitoring-aem-forms-deployments}

U kunt AEM formulierimplementaties zowel op systeemniveau als op intern niveau controleren. U kunt specialistische beheersinstrumenten zoals HP OpenView, IBM® Tivoli, en CA UniCenter en een derdeJMX monitor gebruiken genoemd *JConsole* om Java™ activiteit specifiek te controleren. De implementatie van een monitoringstrategie verbetert de beschikbaarheid, betrouwbaarheid en prestaties van uw AEM formulieren.

<!-- For more information about monitoring AEM forms deployments, see [A technical guide for monitoring AEM forms deployments](https://www.adobe.com/devnet/livecycle/pdfs/lc_monitoring_wp_ue.pdf). This URL is 404. No suitable replacement URL was found after a search. Do not make this link live if it is dead! -->

## Bewaking met behulp van MBeans {#monitoring-using-mbeans}

AEM Forms biedt twee geregistreerde MBans die navigatie- en statistische informatie bieden. Deze delen zijn de enige MBans die voor integratie en inspectie worden gesteund:

* **ServiceStatistic:** This MBean verstrekt informatie over de naam van de Dienst en zijn versie.
* **OperationStatistic:** This MBean verstrekt de statistiek van de dienst van elke server van AEM Forms. Dit MBean is waar de beheerders informatie over een bepaalde dienst zoals oproepingstijd, en aantal fouten kunnen krijgen.

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

**MBean boom**

**Naam van het Domein van de Adobe:** hangt van de Server van de Toepassing af. Als het domein niet wordt gedefinieerd door de toepassingsserver, is de standaardwaarde adobe.com.

**ServiceType:** AdobeService is de naam die wordt gebruikt om van alle diensten een lijst te maken.

**AdobeServiceName:** Naam van de Dienst, of identiteitskaart van de Dienst.

**Versie:** Versie van de dienst.

**Statistieken van de Verrichting**

**de Tijd van de Oroeping:** Tijd die voor de uitvoering van de methode wordt genomen. Deze aanroep omvat niet de tijd het verzoek in series wordt vervaardigd, van cliënt aan server wordt overgebracht, en deserialized.

**de telling van de Inroeping:** het aantal tijden de dienst wordt aangehaald.

**Gemiddelde aanroepingstijd:** Gemiddelde tijd van alle aanroepingen die hebben uitgevoerd aangezien de server was begonnen.

**Max aanroepingstijd:** de duur van de langste aanroeping die heeft uitgevoerd aangezien de server was begonnen.

**Min oproepingstijd:** De duur van de kortste aanroeping die heeft uitgevoerd aangezien de server was begonnen.

**Aantal van de Uitzondering:** Aantal aanroepen die in mislukkingen hebben geresulteerd.

**Bericht van de Uitzondering:** het foutenbericht van de laatste uitzondering die voorkwam.

**Laatste Tijd van de Datum van de Steekproef:** de datum van de laatste aanroeping.

**Eenheid van de Tijd:** Gebrek is milliseconde.

Voor JMX-bewaking hebben de toepassingsservers doorgaans een bepaalde configuratie nodig. Raadpleeg de documentatie bij de toepassingsserver voor meer informatie.

### Voorbeelden van het instellen van open JMX-toegang {#examples-of-how-to-set-up-open-jmx-access}

**JBoss® 4.0.3/4.2.0 - vorm het opstarten JVM**

Om MBans van JConsole te bekijken, vorm de JBoss startparameters van de JVM van de toepassingsserver. Zorg ervoor dat JBoss wordt gestart vanuit het bestand run.bat/sh.

1. Bewerk het bestand run.bat onder InstallJBoss/bin.
1. Zoek de lijn JAVA_OPTS en voeg het volgende toe:

   ```shell
    -Dcom.sun.management.jmxremote -Dcom.sun.management.jmxremote.port=9088 -Dcom.sun.management.jmxremote.authenticate=false -Dcom.sun.management.jmxremote.ssl=false
   ```

**WebLogic 9.2 /10 - vorm het opstarten JVM**

1. Bewerk het startWebLogic.bat-bestand onder `[WebLogic home]/user_projects/domains/Adobe_Live_Cycle/bin` .
1. Zoek de lijn JAVA_OPTS en voeg het volgende toe:

   ```shell
    -Dcom.sun.management.jmxremote -Dcom.sun.management.jmxremote.port=9088 -Dcom.sun.management.jmxremote.authenticate=false -Dcom.sun.management.jmxremote.ssl=false
   ```

1. Start WebLogic opnieuw.

>[!NOTE]
>
>Voor WebLogic kunt u toegang krijgen tot de MBean via extern of IOOP.

**toegang ver MBean**

1. Start JConsole voor nieuwe verbinding en klik op extern tabblad.
1. Voer de hostnaam en poort in (9088, het nummer dat u opgeeft tijdens de startopties van JVM).

**WebSphere® 6.1 - vorm JVM opstarten**

1. Voeg in de Admin Console (Toepassingsserver > server1 > Procesdefinitie > JVM) de volgende regel toe aan het veld voor Generic JVM-argument:

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
