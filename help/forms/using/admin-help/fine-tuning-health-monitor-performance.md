---
title: Prestaties van de fijnafgestelde Health Monitor
description: Leer hoe u de prestaties van de Health Monitor kunt verfijnen. Beheer de systeemstatistieken die invloed hebben op de prestaties van de formulieromgeving met behulp van de optie voor JAVA-instelling.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/health_monitor
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 41042e08-5e14-4809-89b7-16d98a72d1b4
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: e821be5233fd5f6688507096790d219d25903892
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# Prestaties van de fijnafgestelde Health Monitor{#fine-tuning-health-monitor-performance}

Het verzamelen van de systeemstatistieken die de Health Monitor bevolken heeft enig effect op de prestaties van uw AEM formulieromgeving. Dit effect kan worden beheerd door de Java-opties in te stellen die hieronder in uw toepassingsserver worden vermeld.

<table>
 <thead>
  <tr>
   <th><p>Eigenschap</p></th>
   <th><p>Doel</p></th>
   <th><p>Standaardwaarde</p></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p>adobe.healthmonitor.enabled</p></td>
   <td><p>De Health Monitor-thread in- of uitschakelen</p></td>
   <td><p>true</p></td>
  </tr>
  <tr>
   <td><p>adobe.cache.statistics-enabled</p></td>
   <td><p>In- of uitschakelen van plaatsing onder vuur</p></td>
   <td><p>true</p></td>
  </tr>
  <tr>
   <td><p>adobe.healthmonitor.refresh-interval</p></td>
   <td><p>Het interval in milliseconden waarna de draad van de Monitor van de Gezondheid de statistieken verzamelt</p></td>
   <td><p>10 minuten (600.000 milliseconden)</p></td>
  </tr>
  <tr>
   <td><p>adobe.cache.multicast-port</p></td>
   <td><p>De multicast haven die wordt gebruikt om met andere leden van het verdeelde systeem te communiceren. Indien ingesteld op nul, wordt multicast uitgeschakeld voor detectie en distributie van leden. </p><p>Nota: Selecteer verschillende multicast adressen en havens voor verschillende verdeelde systemen. Gebruik niet alleen andere adressen.</p></td>
   <td><p>Geen standaardwaarde. Geldige waarden liggen tussen 0 en 65535.</p></td>
  </tr>
  <tr>
   <td><p>Statistisch steekproefpercentage</p></td>
   <td><p>De snelheid in milliseconden waarmee statistieken worden gesampled. De statistieken van het besturingssysteem worden alleen bijgewerkt wanneer een steekproef wordt genomen.</p></td>
   <td><p>600000</p></td>
  </tr>
  <tr>
   <td><p>adobe.workmanager.healthmonitor.enabled</p></td>
   <td><p>Met deze eigenschap wordt de statistische verzameling van Werkbeheer, zoals het aantal taken of het aantal werkitems, in- of uitgeschakeld.</p></td>
   <td><p>true</p></td>
  </tr>
 </tbody>
</table>

## Java-opties toevoegen aan JBoss {#add-java-options-to-jboss}

1. Stop de JBoss-toepassingsserver.
1. Open de *[toepassingswortel]* /bin/run.bat (Vensters) of looppas.sh (Linux of UNIX) in een redacteur en voeg om het even welke opties van Java toe zoals vereist.
1. Start de server opnieuw.

## Java-opties toevoegen aan WebLogic {#add-java-options-to-weblogic}

1. Begin de WebLogic beleidsconsole door https:// [ gastheernaam ] te typen:&#39;haven&#39;/console in de lijn URL van Webbrowser.
1. Typ de gebruikersnaam en het wachtwoord die u voor het WebLogic Server-domein hebt gemaakt en klik op Log Under Change Center, klik op Vergrendelen en bewerken.
1. Klik onder Domeinstructuur op Omgeving > Servers en klik in het rechterdeelvenster op de naam van de beheerde server.
1. Voor het volgende scherm, klik het lusje van de Configuratie > het Begin tabel van de Server.
1. Voeg in het vak Argumenten de gewenste argumenten toe aan het einde van de huidige inhoud. Als u bijvoorbeeld toevoegt - `Dadobe.healthmonitor.enabled=false` schakelt u Health Monitor uit.
1. Klik op Opslaan en vervolgens op Wijzigingen activeren.
1. Start WebLogic managed server opnieuw.

## Java-opties toevoegen aan WebSphere {#add-java-options-to-websphere}

1. Voer in de WebSphere-navigatiestructuur voor de beheerconsole het volgende uit voor uw toepassingsserver:

   (WebSphere 6.x) Klik op Servers > Toepassingsservers

   (WebSphere 7.x) Klik op Servers > Servertypen > WebSphere-toepassingsservers

1. Klik in het rechterdeelvenster op de servernaam.
1. Klik onder Serverinfrastructuur op Java en de formulierworkflow > Procesdefinitie.
1. Klik onder Extra eigenschappen op Java Virtual Machine.
1. Typ in het vak Algemene JVM-argumenten de argumenten die u nodig hebt.
1. Klik op OK of Toepassen en klik vervolgens rechtstreeks op Opslaan in de hoofdconfiguratie.
