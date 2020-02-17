---
title: Prestatieschema
seo-title: Prestatieschema
description: Leer over de stappen die moeten worden genomen om prestatieskwesties in AEM problemen op te lossen.
seo-description: Leer over de stappen die moeten worden genomen om prestatieskwesties in AEM problemen op te lossen.
uuid: ab0624f7-6b39-4255-89e0-54c74b54cd98
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: 5febbb1e-795c-49cd-a8f4-c6b4b540673d
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Prestatieschema{#performance-tree}

## Scope {#scope}

Het hieronder diagram is bedoeld om begeleiding over de stappen te verstrekken die moeten worden genomen om prestatieskwesties problemen op te lossen. De afbeelding wordt in vijf secties gesplitst, zodat u deze gemakkelijker kunt lezen.

Elke stap in het diagram is verbonden met een documentatiemiddel of een aanbeveling.

## Vereisten en veronderstellingen {#prerequisites-and-assumptions}

De aanname is dat een prestatieprobleem wordt waargenomen op een bepaalde pagina (een AEM-console of een webpagina) en consistent kan worden gereproduceerd. Een manier om de prestaties te testen of te controleren is een voorwaarde voordat het onderzoek wordt gestart.

De analyse begint bij stap 0. Het doel is te bepalen welke entiteit (dispatcher, externe host of AEM) verantwoordelijk is voor het prestatieprobleem en vervolgens te bepalen welk gebied (server of netwerk) moet worden onderzocht.

### Section 1 {#section}

![chlimage_1-103](assets/chlimage_1-103.png)

### Section 2 {#section-1}

![chlimage_1-104](assets/chlimage_1-104.png)

### Section 3 {#section-2}

![chlimage_1-105](assets/chlimage_1-105.png)

### Section 4 {#section-3}

![chlimage_1-106](assets/chlimage_1-106.png)

### Section 5 {#section-4}

![chlimage_1-107](assets/chlimage_1-107.png)

## Referentiekoppelingen {#reference-links}

<table>
 <tbody>
  <tr>
   <td><strong>Stap</strong></td>
   <td><strong>Titel</strong></td>
   <td><strong>Bronnen</strong></td>
  </tr>
  <tr>
   <td><strong>Stap 0</strong></td>
   <td>Aanvraagstroom analyseren</td>
   <td><p>U kunt standaard HTTP- verzoekanalyse in browser gebruiken om de verzoekstroom te analyseren. Zie voor meer informatie over hoe u dit kunt doen op Chrome:<br /> </p> <p><a href="https://developers.google.com/web/tools/chrome-devtools/profile/network-performance/resource-loading">https://developers.google.com/web/tools/chrome-devtools/profile/network-performance/resource-loading</a><a href="https://developers.google.com/web/tools/chrome-devtools/profile/network-performance/understanding-resource-timing"><br /> https://developers.google.com/web/tools/chrome-devtools/profile/network-performance/understanding-resource-timing</a><br /> </p> </td>
  </tr>
  <tr>
   <td><strong>Stap 2</strong></td>
   <td>Worden verzoeken afkomstig van externe hosts?</td>
   <td>U kunt standaard HTTP- verzoekanalyse in browser gebruiken om de verzoekstroom te analyseren. Zie bovenstaande koppelingen voor informatie over hoe u dit kunt doen op Chrome.<br /> </td>
  </tr>
  <tr>
   <td><strong>Stap 3</strong></td>
   <td>Kunnen de verzoeken in de cache worden geplaatst?</td>
   <td>Voor meer informatie over cacheable verzoeken en algemene de prestatiesoptimalisering van de Verzender, zie de Optimalisering <a href="/help/sites-deploying/configuring-performance.md#optimizing-performance-when-using-the-dispatcher">van de Prestaties van de</a>Verzender.</td>
  </tr>
  <tr>
   <td><strong>Stap 4</strong></td>
   <td>Zijn verzoeken afkomstig van de Dispatcher?</td>
   <td><p>Controleer de foutopsporingsdocumentatie <a href="https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html#debugging">van de</a> Dispatcher om te zien of de aanvragen correct in de cache zijn opgeslagen.<br /> </p> </td>
  </tr>
  <tr>
   <td><strong>Stap 5</strong></td>
   <td>Probeert de Dispatcher elk verzoek te verifiëren via AEM?</td>
   <td>Controleer of de verzender <code>HEAD</code> aanvragen voor verificatie naar AEM verzendt voordat de in de cache opgeslagen bron wordt geleverd. U kunt dit doen door <code>HEAD</code> verzoeken in AEM te zoeken <code>access.log</code>. For more information, see <a href="/help/sites-deploying/configure-logging.md">Logging</a>.<br /> </td>
  </tr>
  <tr>
   <td><strong>Stap 6</strong></td>
   <td>Is de geografische locatie van de verzender ver van de gebruikers vandaan?</td>
   <td>Verplaats de Dispatcher dichter naar de gebruikers.</td>
  </tr>
  <tr>
   <td><strong>Stap 7</strong></td>
   <td>Is de netwerklaag van de Verzender OK?</td>
   <td><br /> Onderzoek de netwerklaag voor verzadiging en latentiekwesties.<p> </p> </td>
  </tr>
  <tr>
   <td><strong>Stap 8</strong></td>
   <td>Is de traagheid reproduceerbaar met een lokale instantie?</td>
   <td><br /> <p>Gebruik <a href="/help/sites-developing/tough-day.md">Dag</a> van de Stevige om "echte wereld"omstandigheden van de productie instanties te herhalen. Als dit voor de ruimte van uw ontwikkeling niet realistisch is, zorg ervoor om de productieinstantie (of identieke het opvoeren) in een verschillende netwerkcontext te testen.<br /> </p> </td>
  </tr>
  <tr>
   <td><strong>Stap 9</strong></td>
   <td>Is de geografische plaats van de server ver weg van de gebruikers?</td>
   <td>Verplaats de server dichter naar de gebruikers.</td>
  </tr>
  <tr>
   <td><strong>Stappen 10 en 29</strong></td>
   <td>Onderzoek netwerklaag</td>
   <td><p>Onderzoek de netwerklaag voor verzadiging en latentiekwesties.</p> <p>Voor de auteurslaag, adviseert men dat de latentie 100 milliseconden niet overschrijdt.</p> <p>Zie <a href="https://helpx.adobe.com/experience-manager/kb/performance-tuning-tips.html">deze pagina</a>voor meer informatie over tips voor het optimaliseren van prestaties.</p> </td>
  </tr>
  <tr>
   <td><strong>Stap 11</strong></td>
   <td>Server dichter naar elkaar verplaatsen of één server per gebied toevoegen</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Stap 12</strong></td>
   <td>Problemen met AEM-server oplossen</td>
   <td>Controleer de volgende substappen in het diagram voor meer informatie.</td>
  </tr>
  <tr>
   <td><strong>Stap 13</strong></td>
   <td>Hardwarevereisten controleren</td>
   <td>Raadpleeg de documentatie bij de richtlijnen voor <a href="/help/managing/hardware-sizing-guidelines.md">hardwaregrootte</a>.<br /> </td>
  </tr>
  <tr>
   <td><strong>Stap 14</strong></td>
   <td>Controleren op frequente oorzaken van prestatieproblemen</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Stap 15</strong></td>
   <td>Langzame aanvragen zoeken</td>
   <td><p>U kunt op langzame verzoeken controleren door het te analyseren <code>request.log</code> of door te gebruiken <code>rlog.jar</code>.</p> <p>Zie deze pagina voor meer informatie over het gebruik van rlog.jar.</p> <p>Zie <a href="/help/sites-deploying/monitoring-and-maintaining.md#using-rlog-jar-to-find-requests-with-long-duration-times">Using rlog.jar om verzoeken met lange duurtijden</a>te vinden.<br /> </p> <p> </p> </td>
  </tr>
  <tr>
   <td><strong>Stap 16</strong></td>
   <td>Profielserver</td>
   <td><p>Voor informatie over het profileren van hulpmiddelen kunt u met AEM gebruiken, zie <a href="/help/sites-deploying/monitoring-and-maintaining.md#tools-for-monitoring-and-analyzing-performance">Hulpmiddelen voor het Toezicht en het Analyseren van Prestaties</a>.<br /> </p> </td>
  </tr>
  <tr>
   <td><strong>Stap 17</strong></td>
   <td>Trage methoden zoeken in profielen</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Stap 18</strong></td>
   <td>Gemeenschappelijke scenario's voor profilering</td>
   <td>Zie Specifieke scenario's <a href="/help/sites-deploying/monitoring-and-maintaining.md#analyzing-specific-scenarios">analyseren</a> in de sectie Prestaties optimaliseren.<br /> </td>
  </tr>
  <tr>
   <td><strong>Stap 19</strong></td>
   <td>100% CPU</td>
   <td><a href="/help/sites-deploying/monitoring-and-maintaining.md#monitoring-performance">https://helpx.adobe.com/experience-manager/6-3/sites-deploying/monitoring-and-maintaining.html#MonitoringPerformance</a></td>
  </tr>
  <tr>
   <td><strong>Stap 20</strong></td>
   <td>Onvoldoende geheugen</td>
   <td><br />
    <ol>
     <li><a href="/help/sites-deploying/monitoring-and-maintaining.md#out-of-memory">Onvoldoende geheugen</a></li>
     <li><a href="/help/sites-deploying/troubleshooting.md">Mijn toepassing genereert fouten vanwege onvoldoende geheugen</a></li>
     <li><a href="https://helpx.adobe.com/experience-manager/kb/AnalyzeMemoryProblems.html">Geheugenproblemen analyseren op Helpx.</a><br /> </li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Stap 21</strong></td>
   <td>I/O schijf</td>
   <td><p>Zie de sectie <a href="/help/sites-deploying/monitoring-and-maintaining.md#disk-i-o">SchijfI/O</a> in de documentatie van de Controle en van het Onderhouden.</p> </td>
  </tr>
  <tr>
   <td><strong>Stappen 22 en 22.1</strong></td>
   <td>Cacheverhouding</td>
   <td><a href="/help/sites-deploying/configuring-performance.md#calculating-the-dispatcher-cache-ratio"> Zie De </a>cacheverhouding<br />van de verzender berekenen. <br /> </td>
  </tr>
  <tr>
   <td><strong>Stap 23</strong></td>
   <td>Langzame query's</td>
   <td><a href="/help/sites-deploying/best-practices-for-queries-and-indexing.md">Beste praktijken voor Vragen en het Indexeren</a></td>
  </tr>
  <tr>
   <td><strong>Stap 24</strong></td>
   <td>Afstelling in opslagplaats</td>
   <td>
    <ul>
     <li><a href="https://helpx.adobe.com/experience-manager/kb/performance-tuning-tips.html">Tips voor afstemmen van prestaties</a></li>
     <li><a href="/help/sites-deploying/configuring-performance.md#configuring-for-performance">Configureren voor prestaties</a></li>
     <li><a href="https://www.slideshare.net/jukka/repository-performance-tuning">Afstelling van prestaties opslagplaats</a></li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Stap 25</strong></td>
   <td>Workflows actief</td>
   <td>
    <ul>
     <li><a href="/help/sites-deploying/configuring-performance.md#concurrent-workflow-processing">Gelijktijdige workflowverwerking</a></li>
     <li><a href="/help/sites-deploying/configuring-performance.md#configure-the-queue-for-a-specific-workflow">Vorm de Rij voor een Specifieke Werkstroom</a></li>
     <li><a href="/help/sites-administering/workflows-administering.md#regular-purging-of-workflow-instances">Regelmatig leegmaken van workflowinstanties</a></li>
     <li><a href="/help/sites-developing/workflows.md#transient-workflows">Tijdelijke workflows</a><br /> </li>
    </ul> <p> </p> </td>
  </tr>
  <tr>
   <td><strong>Stap 26</strong></td>
   <td>MSM-infrastructuur</td>
   <td><p><a href="/help/sites-administering/msm-best-practices.md">Aanbevolen werkwijzen voor beheer van meerdere sites</a><br /> </p> </td>
  </tr>
  <tr>
   <td><strong>Stap 27</strong></td>
   <td>Afstemming van activa</td>
   <td>
    <ol>
     <li><a href="/help/sites-deploying/configuring-performance.md#cq-dam-asset-synchronization-service">Assets Synchronization Service</a></li>
     <li><a href="/help/sites-deploying/configuring-performance.md#multiple-dam-instances">Meerdere DAM-instanties</a></li>
     <li>Tips voor het afstemmen van prestaties <a href="https://helpx.adobe.com/experience-manager/kb/performance-tuning-tips.html">hier</a> en <a href="https://helpx.adobe.com/experience-manager/kb/performance-tuning-tips.html">hier</a>.<br /> </li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Stap 28</strong></td>
   <td>Niet-afgesloten sessies</td>
   <td><p> </p> <p><a href="/help/sites-administering/troubleshoot.md#checking-for-unclosed-jcr-sessions">Controleren op niet-afgesloten JCR-sessies</a></p> <p> </p> </td>
  </tr>
  <tr>
   <td><strong>Stap 30</strong></td>
   <td>Verplaats de dispatcher dichter (voeg er één toe per "regio"?)</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Stap 31</strong></td>
   <td>CDN vóór verzender gebruiken</td>
   <td><a href="https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher.html#using-dispatcher-with-a-cdn">Dispatcher gebruiken met een CDN</a><br /> </td>
  </tr>
  <tr>
   <td><strong>Stap 32</strong></td>
   <td>Gebruik sessiebeheer op verzendniveau om AEM-server te offloaden</td>
   <td><p><a href="https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html#enabling-secure-sessions-sessionmanagement">Beveiligde sessies inschakelen</a></p> </td>
  </tr>
  <tr>
   <td><strong>Stap 33</strong></td>
   <td>Verzoeken in cache plaatsen</td>
   <td>
    <ol>
     <li><a href="https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher.html">Algemene configuratie van verzender</a></li>
     <li><a href="https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html#configuring-the-dispatcher-cache-cache">De Dispatcher Cache configureren</a></li>
    </ol> <p>Hoe te om geheim voorgeheugenverhouding te verbeteren; aanvragen in cache kunnen plaatsen (best practices voor Dispatcher)</p> <p>Houd ook rekening met de onderstaande instellingen om uw cacheconfiguraties te optimaliseren<br /> </p>
    <ol>
     <li>Een no-cache-regel instellen voor HTTP-aanvragen die niet GET zijn</li>
     <li>Vraagtekenreeksen configureren om niet cacheable te zijn</li>
     <li>Plaats geen URL's met ontbrekende extensies in cache</li>
     <li>Koppen voor cacheverificatie (mogelijk sinds Dispatcher versie 4.1.10)</li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Stap 34</strong></td>
   <td>Versie van verzender bijwerken</td>
   <td><p>U kunt de meest recente versie van Dispatcher downloaden op deze locatie:</p> <p><a href="https://helpx.adobe.com/experience-manager/dispatcher/release-notes.html">Koppeling volgen</a></p> </td>
  </tr>
  <tr>
   <td><strong>Stap 35</strong></td>
   <td>Dispatcher configureren</td>
   <td><a href="https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html">De Dispatcher configureren</a><br /> </td>
  </tr>
  <tr>
   <td><strong>Stap 36</strong></td>
   <td>Onvalidatie van cache controleren</td>
   <td><br />
    <ul>
     <li><a href="https://helpx.adobe.com/experience-manager/dispatcher/using/page-invalidate.html#invalidating-dispatcher-cache-from-the-authoring-environment">Invalidatie van cache voor de auteurslaag;</a></li>
     <li><a href="https://helpx.adobe.com/experience-manager/dispatcher/using/page-invalidate.html#invalidating-dispatcher-cache-from-a-publishing-instance">Cachevalidatie voor de publicatielaag.</a></li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Stappen 37 en 38</strong></td>
   <td>Lazy-loading</td>
   <td><a href="https://docs.adobe.com/ddc/en/gems/aem-web-performance.html">Zie de Gem-sessie over AEM-webprestaties.</a><br /> </td>
  </tr>
  <tr>
   <td><strong>Stap 39</strong></td>
   <td>Gebruik pre-verbindt om verbindingsoverheadkosten te verminderen</td>
   <td>Zie de hierboven vermelde Gem-sessie. <a href="https://www.w3.org/TR/resource-hints/#dfn-preconnect"> Daarnaast is er extra documentatie beschikbaar die vooraf verbinding maakt met W3c: https://www.w3.org/TR/resource-hints/#dfn-preconnect</a></td>
  </tr>
  <tr>
   <td><strong>Stappen 40 en 41</strong><br /> </td>
   <td>Latentie en responstijd van externe hosts</td>
   <td>Onderzoek de latentie en reactietijd voor de externe gastheren.</td>
  </tr>
  <tr>
   <td><strong>Stappen 45<br /> en 47</strong><br /> </td>
   <td>HTTP/2 gebruiken</td>
   <td>Zie de Gem-sessie voor de stappen 37,38 en 39. Lees ook <a href="https://help-forums.adobe.com/content/adobeforums/en/experience-manager-forum/adobe-experience-manager.topic.html/forum__kdzc-does_anyoneknowwhe.html">dit</a> forumbericht op HTTP/2-ondersteuning.<br /> </td>
  </tr>
  <tr>
   <td><strong>Stap 49</strong></td>
   <td>Belastingsgrootte verkleinen</td>
   <td><a href="/help/sites-deploying/osgi-configuration-settings.md">Schakel Gzip</a> in en <a href="https://docs.adobe.com/ddc/en/gems/aem-web-performance.html">maak de afbeelding kleiner</a>.<br /> </td>
  </tr>
  <tr>
   <td><strong>Stappen 42 en 43</strong></td>
   <td>Keep-Alive</td>
   <td><p>Is de <code>Keep-Alive</code> kopbal aanwezig in de verschillende verzoeken om verbindingen opnieuw te gebruiken? Anders zou het betekenen dat elk verzoek tot een andere verbindingsinstelling leidt, wat onnodige overheadkosten met zich meebrengt. (Standaard HTTP-aanvraaganalyse in de browser)</p> <p>U kunt het hulpmiddel <a href="/help/sites-administering/proxy-jar.md">van de Server van de</a> Volmacht controleren om Levende verbindingen te controleren.<br /> </p> </td>
  </tr>
  <tr>
   <td><strong>Stap 44</strong></td>
   <td>Hoeveel verzoeken zijn er ingediend?</td>
   <td>Voer standaard HTTP- verzoekanalyse in browser uit.</td>
  </tr>
  <tr>
   <td><strong>Stap 46</strong></td>
   <td>Aantal aanvragen verminderen</td>
   <td>
    <ol>
     <li>Bronnen samenvoegen (afbeeldingen, CSS-sprites, JSON, enz.)<br /> </li>
     <li>Clientlibs insluiten:
      <ol>
       <li><a href="/help/sites-developing/clientlibs.md#creating-client-library-folders">Clientbibliotheekmappen</a> maken - zie kop Insluiten gebruiken om verzoeken tot een minimum te beperken</li>
      </ol> </li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Stap 48</strong></td>
   <td>Wat is de grootte van de lading?</td>
   <td>Standaard HTTP-aanvraaganalyse in de browser</td>
  </tr>
  <tr>
   <td><strong>Stappen 50 en 51</strong></td>
   <td>JS-code blokkeren</td>
   <td><a href="https://docs.adobe.com/ddc/en/gems/aem-web-performance.html">https://docs.adobe.com/ddc/en/gems/aem-web-performance.html</a></td>
  </tr>
 </tbody>
</table>

