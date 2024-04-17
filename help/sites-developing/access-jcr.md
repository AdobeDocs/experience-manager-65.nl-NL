---
title: Programmatoegang tot het AEM JCR
description: U kunt via programmacode knooppunten en eigenschappen wijzigen die zich bevinden in de AEM opslagplaats, die deel uitmaakt van de Adobe Experience Cloud
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
exl-id: fe946b9a-b29e-4aa5-b973-e2a652417a55
solution: Experience Manager, Experience Manager Sites
feature: Developing,JCR
role: Developer
source-git-commit: 305227eff3c0d6414a5ae74bcf3a74309dccdd13
workflow-type: tm+mt
source-wordcount: '565'
ht-degree: 0%

---

# Programmatoegang tot het AEM JCR{#how-to-programmatically-access-the-aem-jcr}

U kunt via programmacode knooppunten en eigenschappen wijzigen in de Adobe CQ-opslagplaats, die deel uitmaakt van de Adobe Experience Cloud. Gebruik de JCR-API (Java™ Content Repository) om toegang te krijgen tot de CQ-opslagplaats. U kunt de Java™ JCR API gebruiken om (CRUD)-inhoud te maken, te vervangen, bij te werken en te verwijderen in de Adobe CQ-opslagplaats. Zie voor meer informatie over de Java™ JCR API [https://jackrabbit.apache.org/jcr/jcr-api.html](https://jackrabbit.apache.org/jcr/jcr-api.html).

>[!NOTE]
>
>Dit ontwikkelingsartikel wijzigt de JCR van Adobe CQ van een externe toepassing Java™. U kunt het JCR daarentegen wijzigen vanuit een OSGi-bundel met behulp van de JCR API. Zie voor meer informatie [CQ-gegevens behouden in de Java™ Content Repository](https://helpx.adobe.com/experience-manager/using/persisting-cq-data-java-content1.html).

>[!NOTE]
>
>Als u de JCR API wilt gebruiken, voegt u de `jackrabbit-standalone-2.4.0.jar` naar het klassepad van uw Java™-toepassing. U kunt dit JAR-bestand verkrijgen via de Java™ JCR API-webpagina op [https://jackrabbit.apache.org/jcr/jcr-api.html](https://jackrabbit.apache.org/jcr/jcr-api.html).

>[!NOTE]
>
>Ga voor meer informatie over het zoeken naar de Adobe CQ JCR met de JCR Query API [Adobe Experience Manager-gegevens opvragen met de JCR API](https://helpx.adobe.com/experience-manager/using/querying-experience-manager-data-using1.html).

## Een instantie Repository maken {#create-a-repository-instance}

Hoewel er verschillende manieren zijn om verbinding te maken met een opslagplaats en een verbinding tot stand te brengen, gebruikt dit ontwikkelingsartikel een statische methode die tot de `org.apache.jackrabbit.commons.JcrUtils` klasse. De methode heet `getRepository`. Deze methode gebruikt een tekenreeksparameter die de URL van de Adobe CQ-server vertegenwoordigt. Bijvoorbeeld: `http://localhost:4503/crx/server`.

De `getRepository` methode retourneert een `Repository` -instantie, zoals in het volgende codevoorbeeld wordt getoond.

```java
//Create a connection to the AEM JCR repository running on local host
Repository repository = JcrUtils.getRepository("http://localhost:4503/crx/server");
```

## Een instantie Sessie maken {#create-a-session-instance}

De `Repository` -instantie staat voor de CRX-opslagplaats. U gebruikt de `Repository` -instantie om een sessie met de gegevensopslagruimte tot stand te brengen. Als u een sessie wilt maken, roept u de opdracht `Repository` instantie `login` methode en een `javax.jcr.SimpleCredentials` object. De `login` methode retourneert een `javax.jcr.Session` -instantie.

U maakt een `SimpleCredentials` object door de constructor ervan te gebruiken en de volgende tekenreekswaarden door te geven:

* de gebruikersnaam;
* Het bijbehorende wachtwoord

Roep bij het doorgeven van de tweede parameter het object String `toCharArray` methode. De volgende code laat zien hoe u de `login` methode die een `javax.jcr.Sessioninstance`.

```java
//Create a Session instance
javax.jcr.Session session = repository.login( new SimpleCredentials("admin", "admin".toCharArray()));
```

## Een Node-instantie maken {#create-a-node-instance}

Een `Session` instantie om een `javax.jcr.Node` -instantie. A `Node` Met instantie kunt u knooppuntbewerkingen uitvoeren. U kunt bijvoorbeeld een knooppunt maken. Als u een knooppunt wilt maken dat het hoofdknooppunt vertegenwoordigt, roept u het `Session` instantie `getRootNode` , zoals in de volgende coderegel wordt getoond.

```java
//Create a Node
Node root = session.getRootNode();
```

Wanneer u een `Node` kunt u taken uitvoeren, zoals het maken van een ander knooppunt en het toevoegen van een waarde aan dat knooppunt. Met de volgende code worden bijvoorbeeld twee knooppunten gemaakt en een waarde toegevoegd aan het tweede knooppunt.

```java
// Store content
Node day = adobe.addNode("day");
day.setProperty("message", "Adobe CQ is part of the Adobe Digital Marketing Suite!");
```

## Nodewaarden ophalen {#retrieve-node-values}

Om een knoop en zijn waarde terug te winnen, haal `Node` instantie `getNode` methode en geef een koordwaarde door die volledig - gekwalificeerde weg aan de knoop vertegenwoordigt. Overweeg de knoopstructuur die in het vorige codevoorbeeld wordt gecreeerd. Als u het dagknooppunt wilt ophalen, geeft u adobe/day op, zoals in de volgende code wordt getoond:

```java
// Retrieve content
Node node = root.getNode("adobe/day");
System.out.println(node.getPath());
System.out.println(node.getProperty("message").getString());
```

## Knooppunten maken in de Adobe CQ Repository {#create-nodes-in-the-adobe-cq-repository}

Het volgende Java™-codevoorbeeld vertegenwoordigt een Java™-klasse die verbinding maakt met Adobe CQ, maakt een `Session` en voegt nieuwe knooppunten toe. Een knoop wordt toegewezen een gegevenswaarde en dan wordt de waarde van de knoop en zijn weg geschreven aan de console. Als u klaar bent met de sessie, moet u zich afmelden.

```java
/*
 * This Java Quick Start uses the jackrabbit-standalone-2.4.0.jar
 * file. See the previous section for the location of this JAR file
 */

import javax.jcr.Repository;
import javax.jcr.Session;
import javax.jcr.SimpleCredentials;
import javax.jcr.Node;

import org.apache.jackrabbit.commons.JcrUtils;
import org.apache.jackrabbit.core.TransientRepository;

public class GetRepository {

public static void main(String[] args) throws Exception {

try {

    //Create a connection to the CQ repository running on local host
    Repository repository = JcrUtils.getRepository("http://localhost:4503/crx/server");

   //Create a Session
   javax.jcr.Session session = repository.login( new SimpleCredentials("admin", "admin".toCharArray()));

  //Create a node that represents the root node
  Node root = session.getRootNode();

  // Store content
  Node adobe = root.addNode("adobe");
  Node day = adobe.addNode("day");
  day.setProperty("message", "Adobe CQ is part of the Adobe Digital Marketing Suite!");

  // Retrieve content
  Node node = root.getNode("adobe/day");
  System.out.println(node.getPath());
  System.out.println(node.getProperty("message").getString());

  // Save the session changes and log out
  session.save();
  session.logout();
  }
 catch(Exception e){
  e.printStackTrace();
  }
 }
}
```

Nadat u het volledige codevoorbeeld in werking stelt en de knopen creeert, kunt u de nieuwe knopen in bekijken **[!UICONTROL CRXDE Lite]**, zoals in de volgende afbeelding wordt getoond.

![chlimage_1-68](assets/chlimage_1-68a.png)
