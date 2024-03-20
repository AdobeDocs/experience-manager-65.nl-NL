---
title: De gebruikersavatar weergeven
description: De AEM Forms-werkruimte aanpassen om de afbeelding van een aangemelde gebruiker weer te geven.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
exl-id: ee0708b0-b630-4a2b-84b6-3c0b92dd7777
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 0%

---

# De gebruikersavatar weergeven {#displaying-the-user-avatar}

Avatar van de het programma geopende gebruiker wordt getoond in de hoger-juiste hoek van de werkruimte van AEM Forms. Ook, worden de avatars van directe rapporten in de organisatorische hiërarchie getoond in de Mening van de Manager. U kunt de AEM Forms-werkruimte zodanig configureren dat de gebruikersafbeeldingen in uw database, bijvoorbeeld de LDAP-server, worden gekozen.

>[!NOTE]
>
>De ondersteunde hoogte-breedteverhouding van de gebruikersafbeeldingen is 1:1.

1. Maak een DSC met de details die in de volgende stap worden vermeld. Zie het onderwerp &#39;Componenten ontwikkelen voor AEM Forms&#39; in voor meer informatie [Programmeren met AEM Forms](https://www.adobe.com/go/learn_aemforms_programming_63) hulplijn.
1. Definieer in de DSC een nieuwe SPI die de methoden getCurrentUserImageUrl en getUserImageUrl beschikbaar maakt voor het ophalen van een afbeeldings-URL voor een AEM Forms-gebruiker. Hier volgt een voorbeeld van een Java™-codefragment:

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

1. Implementeer DSC via Workbench. Opnieuw starten `ProcessManagementClientSessionService` service.
1. Mogelijk moet u de browser vernieuwen of u opnieuw afmelden/aanmelden bij de gebruiker.
