---
title: De gebruikersavatar weergeven
seo-title: De gebruikersavatar weergeven
description: Hoe te om de werkruimte van AEM Forms aan te passen om het beeld van een het programma geopende gebruiker te tonen.
seo-description: Hoe te om de werkruimte van AEM Forms aan te passen om het beeld van een het programma geopende gebruiker te tonen.
uuid: 2961dc93-f0d0-4842-80f1-3c239a20e348
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: aec03ea5-17a6-4775-92cb-2ad361895fdf
translation-type: tm+mt
source-git-commit: 1343cc33a1e1ce26c0770a3b49317e82353497ab
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 0%

---


# De gebruikersavatar weergeven {#displaying-the-user-avatar}

Avatar van de het programma geopende gebruiker wordt getoond in de hoger-juiste hoek van de werkruimte van AEM Forms. Ook, worden de avatars van directe rapporten in de organisatorische hiërarchie getoond in de Mening van de Manager. U kunt de werkruimte van AEM Forms vormen om de gebruikersbeelden van uw gegevensbestand, zoals server te kiezen LDAP.

>[!NOTE]
>
>De ondersteunde hoogte-breedteverhouding van de gebruikersafbeeldingen is 1:1.

1. Maak een DSC met de details die in de volgende stap worden vermeld. Voor meer informatie, zie het Ontwikkelen van Componenten voor AEM Forms in het [Programmeren van AEM Forms](https://www.adobe.com/go/learn_aemforms_programming_63) gids.
1. Definieer in de DSC een nieuwe SPI die methoden getCurrentUserImageUrl en getUserImageUrl beschikbaar maakt om een beeld-URL voor een gebruiker van AEM Forms te krijgen. Hier volgt een voorbeeld van een Java™-codefragment:

   ```java
   public class DemoUserImageURLProviderService {
     public String getCurrentUserImageUrl()
     {
        // return the URL for profile Image of logged in user
     }
     public String getUserImageUrl(String principalOid)
     {
         // return the URL for profile Image for user represented by this principal Oid
      }
   }
   ```

1. Maak een bestand component.xml. Controleer of de specificatie-id overeenkomt met de weergave in het codefragment hieronder.

   Het volgende codefragment is een voorbeeld. Pas het aan uw specifieke vereisten aan.

   ```java
   <component xmlns="https://adobe.com/idp/dsc/component/document">
       <component-id>com.adobe.sample.DemoUsersComponent</component-id>
       <version>1.1</version>
       <supports-export>false</supports-export>
       <descriptor-class>com.adobe.idp.dsc.component.impl.DefaultPOJODescriptorImpl</descriptor-class>
       <services>
           <service name="DemoUserImageURLProviderService" title="Demo User ImageURL provider service" orchestrateable="false">
           <auto-deploy service-id="DemoUserImageURLProviderService" category-id="Demo Users Component DSC" major-version="1" minor-version="0" />
           <description>Service for resolving user image url.</description>
            <specifications>
            <specification spec-id="com.adobe.idp.taskmanager.dsc.enterprise.UserImageUrlProvider"/>
            </specifications>
           <specification-version>1.0</specification-version>
           <implementation-class>com.adobe.sample.demousers.DemoUserImageURLProviderService</implementation-class>
           <request-processing-strategy>single_instance</request-processing-strategy>
           <supported-connectors>default</supported-connectors>
           <operation-config>
               <operation-name>*</operation-name>
               <transaction-type>Container</transaction-type>
               <transaction-propagation>supports</transaction-propagation>
               <!--transaction-timeout>3000</transaction-timeout-->
           </operation-config>
           <operations>
               <operation anonymous-access="false" name="getCurrentUserImageUrl" method="getCurrentUserImageUrl">
                   <output-parameter name="result" type="java.lang.String"/>
               </operation>
               <operation anonymous-access="false" name="getUserImageUrl"
   method="getUserImageUrl">
               <input-parameter name="principalOid" type="java.lang.String"/>
               <output-parameter name="result" type="java.lang.String"/>
               </operation>
           </operations>
           </service>
       </services>
   </component>
   ```

1. Implementeer DSC via Workbench. Start de `ProcessManagementClientSessionService` service opnieuw.
1. Mogelijk moet u de browser vernieuwen of u opnieuw afmelden/aanmelden bij de gebruiker.
