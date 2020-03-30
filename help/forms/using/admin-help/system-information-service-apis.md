---
title: System Information Service API's
seo-title: System Information Service API's
description: Dit document bevat gedetailleerde informatie over de API's die worden geleverd door de systeeminformatiedienst.
seo-description: Dit document bevat gedetailleerde informatie over de API's die worden geleverd door de systeeminformatiedienst.
uuid: 7f624216-56e6-4d49-b9a1-3c9af045dabe
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/system_information_service
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 79fccce2-d090-4b50-9c58-3f2a00e651b2
translation-type: tm+mt
source-git-commit: 317fadfe48724270e59644d2ed9a90fbee95cf9f

---


# System Information Service API&#39;s {#system-information-service-apis}

De systeeminformatiedienst verstrekt een reeks REST APIs om informatie terug te winnen. De volgende tabel bevat gedetailleerde informatie over de API&#39;s:

<table>
 <thead>
  <tr>
   <th><p>Naam</p></th>
   <th><p>URL</p></th>
   <th><p>Beschrijving</p></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p>SystemInfo.properties</p></td>
   <td><p>https://'[server]:[poort]'/rest/services/SystemInfo.properties`</p></td>
   <td><p>Deze API is een wrapper voor <a href="https://docs.oracle.com/javase/6/docs/api/java/lang/System.html#getProperties()">system.getProperties</a> Java API. De configuratie van de huidige werkomgeving wordt opgehaald. </p></td>
  </tr>
  <tr>
   <td><p>SystemInfo.envVar</p></td>
   <td><p>https://'[server]:[poort]'/rest/services/ SystemInfo.envVar</p></td>
   <td><p>Hiermee worden alle omgevingsvariabelen van het hostbesturingssysteem opgehaald. </p></td>
  </tr>
  <tr>
   <td><p>SystemInfo.logs</p></td>
   <td><p>https://'[server]:[poort]'/rest/services/ SystemInfo.logs</p></td>
   <td><p>Downloadt een ZIP-bestand dat de logboeken van de toepassingsserver bevat. </p></td>
  </tr>
  <tr>
   <td><p>SystemInfo.config</p></td>
   <td><p>https://'[server]:[poort]'/rest/services/ SystemInfo.config</p></td>
   <td><p>Hiermee wordt alle inhoud van het bestand config.xml opgehaald. </p></td>
  </tr>
  <tr>
   <td><p>SystemInfo.services</p></td>
   <td><p>https://'[server]:[poort]'/rest/services/ SystemInfo.services</p></td>
   <td><p>Haalt status- en configuratieparameters van AEM-formulierservices op.</p></td>
  </tr>
  <tr>
   <td><p>SystemInfo.priorityDetails</p></td>
   <td><p>https://'[server]:[poort]'/rest/services/ SystemInfo.essentialDetails</p></td>
   <td><p>Haalt serveruptime, JVM-argumenten, systeemgeheugen, heapgrootte, naam van het besturingssysteem, aantal actieve threads en aantal threads op. </p></td>
  </tr>
  <tr>
   <td><p>SystemInfo.coreSettings</p></td>
   <td><p>https://'[server]:[poort]'/rest/services/ SystemInfo.coreSettings</p></td>
   <td><p>Haalt waarden op van de volgende eigenschappen:</p>
    <ul>
     <li><p>AdobeTempDir</p></li>
     <li><p>AdobeServerFontDir</p></li>
     <li><p>CustomerFontDir</p></li>
     <li><p>GlobalDocumentStorageRootDir</p></li>
     <li><p>DefaultDocumentMaxInlineSize</p></li>
     <li><p>DefaultDocumentDisposalTimeout</p></li>
     <li><p>EnableDocumentDBStorage</p></li>
     <li><p>GlobalDocumentStorageUseNetworkShare</p></li>
     <li><p>EnableFIPS</p></li>
     <li><p>EnableWSDL</p></li>
     <li><p>DataServicesConfigFile </p></li>
     <li><p>EnableRDS</p></li>
    </ul><p></p></td>
  </tr>
  <tr>
   <td><p>SystemInfo.database</p></td>
   <td><p>https://'[server]:[poort]'/rest/services/SystemInfo.database</p></td>
   <td><p>Hiermee wordt gedetailleerde informatie over de database opgehaald.</p></td>
  </tr>
  <tr>
   <td><p>SystemInfo.licenseInfo</p></td>
   <td><p>https://'[server]:[poort]'/rest/services/ SystemInfo.licenseInfo</p></td>
   <td><p>Hiermee worden versie- en licentiegegevens van geïnstalleerde AEM-formuliercomponenten opgehaald. </p></td>
  </tr>
  <tr>
   <td><p>SystemInfNo.serverConfig</p></td>
   <td><p>https://'[server]:[poort]'/rest/services/ SystemInfo.serverConfig</p></td>
   <td><p>Downloadt configuratiebestanden van de hosttoepassingsserver. </p></td>
  </tr>
  <tr>
   <td><p>SystemInfo.threads?delay=[n]&amp;iterations=[n]</p></td>
   <td><p>https://'[server]:[poort]'/rest/services/SystemInfo.threads?delay=[n]&amp;iterations=[n]</p></td>
   <td><p>Haalt aantal en stapelspoor van actieve draden terug. De volgende parameters worden geaccepteerd:</p>
    <ul>
     <li><p>iterations= [n]: Hiermee geeft u het aantal herhalingen op. Vervang n door een getal. </p></li>
     <li><p>Vertraging= [n]: Geeft het aantal milliseconden op dat moet worden gewacht voordat de volgende herhaling wordt gestart. </p></li>
    </ul><p></p></td>
  </tr>
  <tr>
   <td><p>SystemInfo.info</p></td>
   <td><p>https://'[server]:[poort]'/rest/services/ SystemInfo.info</p></td>
   <td><p>Deze API is een omslag voor alle dienst APIs van de systeeminformatiedienst. Intern worden alle API's voor systeeminformatie uitgevoerd en wordt informatie gedownload in de ZIP-indeling. </p><p><i><strong>opmerking</strong>: SystemInfo.info verstrekt geen telling en stapelspoor van actieve draden. </i></p></td>
  </tr>
 </tbody>
</table>

