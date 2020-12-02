---
title: Programmatoegang tot het AEM JCR
seo-title: Programmatoegang tot het AEM JCR
description: U kunt via programmacode knooppunten en eigenschappen wijzigen die zich bevinden in de AEM opslagplaats, die deel uitmaakt van de Adobe Marketing Cloud
seo-description: U kunt via programmacode knooppunten en eigenschappen wijzigen die zich bevinden in de AEM opslagplaats, die deel uitmaakt van de Adobe Marketing Cloud
uuid: 2051d03f-430a-4cae-8f6d-e5bc727d733f
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
discoiquuid: 69f62a38-7991-4009-8db7-ee8fd35dc535
translation-type: tm+mt
source-git-commit: 6d216e7521432468a01a29ad2879f8708110d970
workflow-type: tm+mt
source-wordcount: '616'
ht-degree: 0%

---


# Hoe te om tot AEM JCR{#how-to-programmatically-access-the-aem-jcr} programmatically toegang te hebben

U kunt via programmacode knooppunten en eigenschappen wijzigen in de Adobe CQ-opslagplaats, die deel uitmaakt van de Adobe Marketing Cloud. Als u toegang wilt krijgen tot de CQ-opslagplaats, gebruikt u de JCR-API (Java Content Repository). U kunt de Java JCR API gebruiken om (CRUD)-bewerkingen te maken, te vervangen, bij te werken en te verwijderen op inhoud in de Adobe CQ-opslagplaats. Zie [https://jackrabbit.apache.org/jcr/jcr-api.html](https://jackrabbit.apache.org/jcr/jcr-api.html) voor meer informatie over de Java JCR API.

>[!NOTE]
>
>Dit ontwikkelingsartikel wijzigt het JCR van Adobe CQ van een externe toepassing van Java. U kunt het JCR daarentegen wijzigen vanuit een OSGi-bundel met behulp van de JCR API. Zie [CQ-gegevens behouden in de Java Content Repository](https://helpx.adobe.com/experience-manager/using/persisting-cq-data-java-content1.html) voor meer informatie.

>[!NOTE]
>
>Als u de JCR API wilt gebruiken, voegt u het `jackrabbit-standalone-2.4.0.jar`-bestand toe aan het klassepad van uw Java-toepassing. U kunt dit JAR-bestand verkrijgen via de Java JCR API-webpagina op [https://jackrabbit.apache.org/jcr/jcr-api.html](https://jackrabbit.apache.org/jcr/jcr-api.html).

>[!NOTE]
>
>Zie [Adobe Experience Manager-gegevens opvragen met de JCR API](https://helpx.adobe.com/experience-manager/using/querying-experience-manager-data-using1.html) voor meer informatie over het opvragen van een query op de JCR API.

## Een instantie Repository maken {#create-a-repository-instance}

Hoewel er verschillende manieren zijn om verbinding te maken met een opslagplaats en een verbinding tot stand te brengen, gebruikt dit ontwikkelingsartikel een statische methode die tot de klasse `org.apache.jackrabbit.commons.JcrUtils` behoort. De naam van de methode is `getRepository`. Deze methode gebruikt een tekenreeksparameter die de URL van de Adobe CQ-server vertegenwoordigt. Bijvoorbeeld `http://localhost:4503/crx/server`.

De methode `getRepository`retourneert een `Repository`instantie, zoals in het volgende codevoorbeeld wordt getoond.

```java
//Create a connection to the AEM JCR repository running on local host
Repository repository = JcrUtils.getRepository("http://localhost:4503/crx/server");
```

## Een Session-instantie maken {#create-a-session-instance}

De `Repository`instantie vertegenwoordigt de CRX-opslagplaats. U gebruikt de `Repository`instantie om een zitting met de bewaarplaats te vestigen. Als u een sessie wilt maken, roept u de methode `Repository`van de instantie aan en geeft u een object `login` door. `javax.jcr.SimpleCredentials` De methode `login`retourneert een `javax.jcr.Session`-instantie.

U maakt een `SimpleCredentials`object door de constructor ervan te gebruiken en de volgende tekenreekswaarden door te geven:

* de gebruikersnaam;
* Het bijbehorende wachtwoord

Roep bij het doorgeven van de tweede parameter de methode `toCharArray`van het object String aan. De volgende code toont hoe te om de `login`methode te roepen die `javax.jcr.Sessioninstance` terugkeert.

```java
//Create a Session instance
javax.jcr.Session session = repository.login( new SimpleCredentials("admin", "admin".toCharArray()));
```

## Een knooppuntinstantie maken {#create-a-node-instance}

Gebruik een `Session`instantie om een `javax.jcr.Node` instantie te maken. Met een `Node`-instantie kunt u nodebewerkingen uitvoeren. U kunt bijvoorbeeld een nieuw knooppunt maken. Als u een knooppunt wilt maken dat het hoofdknooppunt vertegenwoordigt, roept u de methode `getRootNode` van de `Session`instantie aan, zoals in de volgende coderegel wordt getoond.

```java
//Create a Node
Node root = session.getRootNode();
```

Wanneer u een `Node`instantie hebt gemaakt, kunt u taken uitvoeren zoals een ander knooppunt maken en er een waarde aan toevoegen. Met de volgende code worden bijvoorbeeld twee knooppunten gemaakt en een waarde toegevoegd aan het tweede knooppunt.

```java
// Store content
Node day = adobe.addNode("day");
day.setProperty("message", "Adobe CQ is part of the Adobe Digital Marketing Suite!");
```

## Nodewaarden {#retrieve-node-values} ophalen

Als u een knooppunt en de bijbehorende waarde wilt ophalen, roept u de methode `Node`van de instantie op en geeft u een tekenreekswaarde door die het volledig gekwalificeerde pad naar het knooppunt vertegenwoordigt. `getNode` Overweeg de knoopstructuur die in het vorige codevoorbeeld wordt gecreeerd. Als u het dagknooppunt wilt ophalen, geeft u adobe/day op, zoals in de volgende code wordt getoond:

```java
// Retrieve content
Node node = root.getNode("adobe/day");
System.out.println(node.getPath());
System.out.println(node.getProperty("message").getString());
```

## Maak knooppunten in de Adobe CQ Repository {#create-nodes-in-the-adobe-cq-repository}

Het volgende Java-codevoorbeeld vertegenwoordigt een Java-klasse die verbinding maakt met Adobe CQ, een `Session`instantie maakt en nieuwe knooppunten toevoegt. Een knoop wordt toegewezen een gegevenswaarde en dan wordt de waarde van de knoop en zijn weg geschreven aan de console. Als u klaar bent met de sessie, moet u zich afmelden.

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

Nadat u het volledige codevoorbeeld in werking stelt en de knopen creeert, kunt u de nieuwe knopen in **[!UICONTROL CRXDE Lite]** bekijken, zoals aangetoond in de volgende afbeelding.

![chlimage_1-68](assets/chlimage_1-68a.png)

