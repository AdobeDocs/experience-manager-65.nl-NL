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

U kunt via programmacode knooppunten en eigenschappen wijzigen in de Adobe CQ-opslagplaats, die deel uitmaakt van de Adobe Experience Cloud. Gebruik de JCR-API (Java™ Content Repository) om toegang te krijgen tot de CQ-opslagplaats. U kunt de Java™ JCR API gebruiken om (CRUD)-inhoud te maken, te vervangen, bij te werken en te verwijderen in de Adobe CQ-opslagplaats. Voor meer informatie over Java™ JCR API, zie [&#x200B; https://jackrabbit.apache.org/jcr/jcr-api.html &#x200B;](https://jackrabbit.apache.org/jcr/jcr-api.html).

>[!NOTE]
>
>Dit ontwikkelingsartikel wijzigt de JCR van Adobe CQ van een externe toepassing Java™. U kunt het JCR daarentegen wijzigen vanuit een OSGi-bundel met behulp van de JCR API. Voor details, zie [&#x200B; Blijvend CQ- gegevens in de Bewaarplaats van de Inhoud Java™ &#x200B;](https://helpx.adobe.com/experience-manager/using/persisting-cq-data-java-content1.html).

>[!NOTE]
>
>Als u de JCR API wilt gebruiken, voegt u het `jackrabbit-standalone-2.4.0.jar` -bestand toe aan het klassepad van uw Java™-toepassing. U kunt dit JAR dossier van de Java™ JCR API Web-pagina in [&#x200B; verkrijgen https://jackrabbit.apache.org/jcr/jcr-api.html &#x200B;](https://jackrabbit.apache.org/jcr/jcr-api.html).

>[!NOTE]
>
>Leren hoe te om Adobe CQ JCR te vragen gebruikend de Vraag JCR API, zie [&#x200B; het Vragen van de Gegevens van Adobe Experience Manager gebruikend JCR API &#x200B;](https://helpx.adobe.com/experience-manager/using/querying-experience-manager-data-using1.html).

## Een instantie Repository maken {#create-a-repository-instance}

Hoewel er verschillende manieren zijn om verbinding te maken met een gegevensopslagruimte en een verbinding tot stand te brengen, gebruikt dit ontwikkelingsartikel een statische methode die tot de klasse `org.apache.jackrabbit.commons.JcrUtils` behoort. De naam van de methode is `getRepository` . Deze methode gebruikt een tekenreeksparameter die de URL van de Adobe CQ-server vertegenwoordigt. Bijvoorbeeld `http://localhost:4503/crx/server` .

De methode `getRepository` retourneert een `Repository` -instantie, zoals in het volgende codevoorbeeld wordt getoond.

```java
//Create a connection to the AEM JCR repository running on local host
Repository repository = JcrUtils.getRepository("http://localhost:4503/crx/server");
```

## Een instantie Sessie maken {#create-a-session-instance}

De `Repository` -instantie vertegenwoordigt de CRX-opslagplaats. U gebruikt de `Repository` -instantie om een sessie met de repository tot stand te brengen. Als u een sessie wilt maken, roept u de methode `login` van de `Repository` -instantie op en geeft u een `javax.jcr.SimpleCredentials` -object door. De methode `login` retourneert een `javax.jcr.Session` -instantie.

U maakt een `SimpleCredentials` -object door de constructor ervan te gebruiken en de volgende tekenreekswaarden door te geven:

* de gebruikersnaam;
* Het bijbehorende wachtwoord

Roep de methode `toCharArray` van het object String aan wanneer u de tweede parameter doorgeeft. De volgende code laat zien hoe u de methode `login` aanroept die een `javax.jcr.Sessioninstance` retourneert.

```java
//Create a Session instance
javax.jcr.Session session = repository.login( new SimpleCredentials("admin", "admin".toCharArray()));
```

## Een Node-instantie maken {#create-a-node-instance}

Gebruik een `Session` -instantie om een `javax.jcr.Node` -instantie te maken. Met een `Node` -instantie kunt u nodebewerkingen uitvoeren. U kunt bijvoorbeeld een knooppunt maken. Als u een knooppunt wilt maken dat het hoofdknooppunt vertegenwoordigt, roept u de methode `getRootNode` van de `Session` -instantie aan, zoals in de volgende coderegel wordt getoond.

```java
//Create a Node
Node root = session.getRootNode();
```

Wanneer u een `Node` -instantie hebt gemaakt, kunt u taken uitvoeren zoals een ander knooppunt maken en er een waarde aan toevoegen. Met de volgende code worden bijvoorbeeld twee knooppunten gemaakt en een waarde toegevoegd aan het tweede knooppunt.

```java
// Store content
Node day = adobe.addNode("day");
day.setProperty("message", "Adobe CQ is part of the Adobe Digital Marketing Suite!");
```

## Nodewaarden ophalen {#retrieve-node-values}

Als u een knooppunt en de bijbehorende waarde wilt ophalen, roept u de methode `getNode` van de instantie `Node` aan en geeft u een tekenreekswaarde door die het volledig gekwalificeerde pad naar het knooppunt vertegenwoordigt. Overweeg de knoopstructuur die in het vorige codevoorbeeld wordt gecreeerd. Als u het dagknooppunt wilt ophalen, geeft u adobe/day op, zoals in de volgende code wordt getoond:

```java
// Retrieve content
Node node = root.getNode("adobe/day");
System.out.println(node.getPath());
System.out.println(node.getProperty("message").getString());
```

## Knooppunten maken in de Adobe CQ Repository {#create-nodes-in-the-adobe-cq-repository}

Het volgende Java™-codevoorbeeld vertegenwoordigt een Java™-klasse die verbinding maakt met Adobe CQ, een `Session` -instantie maakt en nieuwe knooppunten toevoegt. Een knoop wordt toegewezen een gegevenswaarde en dan wordt de waarde van de knoop en zijn weg geschreven aan de console. Als u klaar bent met de sessie, moet u zich afmelden.

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

![&#x200B; chlimage_1-68 &#x200B;](assets/chlimage_1-68a.png)
