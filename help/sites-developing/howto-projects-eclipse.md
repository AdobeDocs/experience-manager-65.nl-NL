---
title: Hoe te om AEM Projecten te ontwikkelen gebruikend Eclipse
seo-title: Hoe te om AEM Projecten te ontwikkelen gebruikend Eclipse
description: In deze handleiding wordt beschreven hoe u Eclipse kunt gebruiken voor het ontwikkelen van op AEM gebaseerde projecten
seo-description: In deze handleiding wordt beschreven hoe u Eclipse kunt gebruiken voor het ontwikkelen van op AEM gebaseerde projecten
uuid: 79fee76f-6bcc-498f-af46-530816b41bbe
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: development-tools
content-type: reference
discoiquuid: aa58cfb8-ec15-4698-a8f0-97683b0de51c
translation-type: tm+mt
source-git-commit: 06f1f753b9bb7f7336454f166e03f753e3735a16
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---


# Hoe te om AEM Projecten te ontwikkelen gebruikend Eclipse{#how-to-develop-aem-projects-using-eclipse}

In deze handleiding wordt beschreven hoe u Eclipse kunt gebruiken voor het ontwikkelen van op AEM gebaseerde projecten.

>[!NOTE]
>
>Adobe biedt nu de [AEM ontwikkelingstools voor Eclipse](/help/sites-developing/aem-eclipse.md) waarmee u AEM oplossingen kunt ontwikkelen met Eclipse.

## Overzicht {#overview}

Om met AEM ontwikkeling op Eclipse te beginnen, zijn de volgende stappen vereist.

Elk van hen wordt meer in detail beschreven in de rest van dit hoe te.

* Eclipse 4.3 (Kepler) installeren
* Uw AEM instellen op basis van Maven
* JSP-ondersteuning voorbereiden voor Eclipse in de Maven POM
* Geweven project importeren in Eclipse

>[!NOTE]
>
>Deze handleiding is gebaseerd op Eclipse 4.3 (Kepler) en AEM 5.6.1.

## Verduistering {#install-eclipse} installeren

Download de &quot;Eclipse IDE for Java EE Developers&quot; op de pagina [Eclipse Downloads](https://www.eclipse.org/downloads/).

Installeer Eclipse volgens de [Installatie-instructies](https://wiki.eclipse.org/Eclipse/Installation).

## Stel uw AEM in op basis van Maven {#set-up-your-aem-project-based-on-maven}

Stel vervolgens uw project in met Maven zoals beschreven in [Hoe kan ik AEM projecten bouwen met Apache Maven](/help/sites-developing/ht-projects-maven.md).

## JSP-ondersteuning voorbereiden voor Eclipse {#prepare-jsp-support-for-eclipse}

Eclipse kan ook ondersteuning bieden bij het werken met JSP, bijvoorbeeld

* tagbibliotheken automatisch invullen
* Eclipsebewustzijn van objecten die worden gedefinieerd door &lt;cq:defineObjects /> en &lt;sling:defineObjects />

Om dat te doen:

1. Volg de instructies op [Hoe te met JSPs](/help/sites-developing/ht-projects-maven.md#how-to-work-with-jsps) in [hoe te AEM Projecten bouwen gebruikend Apache Maven](/help/sites-developing/ht-projects-maven.md).
1. Voeg het volgende toe aan de &lt;build /> sectie in POM van uw inhoudsmodule.

   De Maven-supportplug-in van Eclipse, m2e, biedt geen ondersteuning voor de maven-jspc-plugin. Deze configuratie instrueert m2e om de plug-in en de bijbehorende taak van het opschonen van de resultaten van de tijdelijke compilatie te negeren.

   Dit is geen probleem: zoals vermeld in [Hoe te met JSPs](/help/sites-developing/ht-projects-maven.md#how-to-work-with-jsps) te werken, wordt de maven-jspc-stop in deze opstelling slechts gebruikt om te bevestigen dat JSPs als deel van het bouwstijlproces compileert. Eclipse rapporteert al problemen in JSPs en vertrouwt niet op deze Maven plugin om dit te kunnen doen.

   **myproject/content/pom.xml**

   ```xml
   <build>
     <!-- ... -->
     <pluginManagement>
       <plugins>
         <!--This plugin's configuration is used to store Eclipse m2e settings only. It has no influence on the Maven build itself.-->
         <plugin>
           <groupId>org.eclipse.m2e</groupId>
           <artifactId>lifecycle-mapping</artifactId>
           <version>1.0.0</version>
           <configuration>
             <lifecycleMappingMetadata>
               <pluginExecutions>
                 <pluginExecution>
                   <pluginExecutionFilter>
                     <groupId>org.apache.sling</groupId>
                     <artifactId>maven-jspc-plugin</artifactId>
                     <versionRange>[2.0.6,)</versionRange>
                     <goals>
                       <goal>jspc</goal>
                     </goals>
                   </pluginExecutionFilter>
                   <action>
                     <ignore/>
                   </action>
                 </pluginExecution>
                 <pluginExecution>
                   <pluginExecutionFilter>
                     <groupId>org.apache.maven.plugins</groupId>
                     <artifactId>maven-clean-plugin</artifactId>
                     <versionRange>[2.4.1,)</versionRange>
                     <goals>
                       <goal>clean</goal>
                     </goals>
                   </pluginExecutionFilter>
                   <action>
                     <ignore/>
                   </action>
                 </pluginExecution>
               </pluginExecutions>
             </lifecycleMappingMetadata>
           </configuration>
         </plugin>
       </plugins>
     </pluginManagement>
   </build>
   ```

### Het gemaakte project importeren in Eclipse {#import-the-maven-project-into-eclipse}

1. Kies in Eclipse Bestand > Importeren...
1. Kies Geweven > Bestaande gefabriceerde projecten in het dialoogvenster Importeren en klik op Volgende.

   ![chlimage_1-41](assets/chlimage_1-41a.png)

1. Voer het pad naar de map op het hoogste niveau van uw project in en klik op Alles selecteren en Voltooien.

   ![chlimage_1-42](assets/chlimage_1-42a.png)

1. U bent nu allen geplaatst voor het gebruiken van Eclipse om uw AEM project, met inbegrip van autocompletion te ontwikkelen JSP.

   ![chlimage_1-43](assets/chlimage_1-43a.png)

   >[!NOTE]
   >
   >Als u `/libs/foundation/global.jsp` of andere JSPs in `/libs` omvat, zult u dat aan uw project moeten kopiëren zodat kan de Verduistering de opneming oplossen. Tegelijkertijd moet u ervoor zorgen dat het pakket niet door Maven in het inhoudspakket wordt opgenomen. Hoe dit te bereiken wordt beschreven in [Hoe te om AEM Projecten te bouwen gebruikend Apache Maven](/help/sites-developing/ht-projects-maven.md).

