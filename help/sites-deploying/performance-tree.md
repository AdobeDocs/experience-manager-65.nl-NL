---
title: Prestatieschema
description: Leer over de stappen die moeten nemen om prestatieskwesties in AEM problemen op te lossen.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
exl-id: f2f968b8-b21c-487d-bc0d-ed60903bc4bf
solution: Experience Manager, Experience Manager Sites
feature: Administering
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '1088'
ht-degree: 0%

---

# Prestatieschema{#performance-tree}

## Scope {#scope}

Het volgende diagram wordt bedoeld om raad over de stappen te verstrekken om prestatieskwesties problemen op te lossen. Het wordt in vijf secties gesplitst, zodat u het gemakkelijk kunt lezen.

Elke stap in het diagram is verbonden met een documentatiemiddel of een aanbeveling.

## Vereisten en veronderstellingen {#prerequisites-and-assumptions}

De aanname is dat een prestatieprobleem wordt waargenomen op een bepaalde pagina (een AEM console of een webpagina) en consistent kan worden gereproduceerd. Een manier om de prestaties te testen of te controleren is een voorwaarde voordat het onderzoek wordt gestart.

De analyse begint bij stap 0. Het doel is te bepalen welke entiteit (Verzender, externe gastheer, of AEM) verantwoordelijk is voor de prestatieskwestie dan bepaalt welk gebied (server of netwerk) zou moeten worden onderzocht.

### Sectie 1 {#section}

![chlimage_1-103](assets/chlimage_1-103.png)

### Sectie 2 {#section-1}

![chlimage_1-104](assets/chlimage_1-104.png)

### Afdeling 3 {#section-2}

![chlimage_1-105](assets/chlimage_1-105.png)

### Sectie 4 {#section-3}

![chlimage_1-106](assets/chlimage_1-106.png)

### Afdeling 5 {#section-4}

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
   <td><p>U kunt standaard HTTP- verzoekanalyse in browser gebruiken om de verzoekstroom te analyseren. Voor meer informatie over hoe te om deze analyse op Chrome te doen, zie:<br /> </p> <p><a href="https://developers.google.com/web/tools/chrome-devtools/profile/network-performance/resource-loading">https://developer.chrome.com/docs/devtools/</a><br /> </p> </td>
  </tr>
  <tr>
   <td><strong>Stap 2</strong></td>
   <td>Worden verzoeken afkomstig van externe hosts?</td>
   <td>U kunt standaard HTTP- verzoekanalyse in browser gebruiken om de verzoekstroom te analyseren. Zie bovenstaande koppelingen voor deze analyse op Chrome.<br /> </td>
  </tr>
  <tr>
   <td><strong>Stap 3</strong></td>
   <td>Kunnen de verzoeken in de cache worden geplaatst?</td>
   <td>Voor meer informatie over cacheable verzoeken en algemene het optimaliseren van de prestaties van de Verzender advies, zie <a href="/help/sites-deploying/configuring-performance.md#optimizing-performance-when-using-the-dispatcher">Optimalisatie van de prestaties van de verzender</a>.</td>
  </tr>
  <tr>
   <td><strong>Stap 4</strong></td>
   <td>Zijn verzoeken afkomstig van de Dispatcher?</td>
   <td><p>Om te zien of zijn de verzoeken behoorlijk in het voorgeheugen ondergebracht, controleer <a href="https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#debugging">Debugging van de afzender documentatie</a>.<br /> </p> </td>
  </tr>
  <tr>
   <td><strong>Stap 5</strong></td>
   <td>Probeert de Dispatcher elk verzoek via AEM te verifiëren?</td>
   <td>Controleren of de Dispatcher verzendt <code>HEAD</code> verzoeken om AEM voor authentificatie alvorens het caching middel te leveren. Zoeken naar <code>HEAD</code> verzoeken in de AEM <code>access.log</code>. Zie voor meer informatie <a href="/help/sites-deploying/configure-logging.md">Logboekregistratie</a>.<br /> </td>
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
   <td><br /> <p>Gebruiken <a href="/help/sites-developing/tough-day.md">Grove dag</a> om "echte" omstandigheden van de productie-instanties te repliceren. Als dit scenario voor de ruimte van uw ontwikkeling niet realistisch is, zorg ervoor om de productieinstantie (of identieke het opvoeren) in een verschillende netwerkcontext te testen.<br /> </p> </td>
  </tr>
  <tr>
   <td><strong>Stap 9</strong></td>
   <td>Is de geografische plaats van de server ver weg van de gebruikers?</td>
   <td>Verplaats de server dichter naar de gebruikers.</td>
  </tr>
  <tr>
   <td><strong>Stappen 10 en 29</strong></td>
   <td>Onderzoek netwerklaag</td>
   <td><p>Onderzoek de netwerklaag voor verzadiging en latentiekwesties.</p> <p>Voor de auteurslaag, adviseert men dat de latentie 100 milliseconden niet overschrijdt.</p> <p>Zie voor meer informatie over tips voor het optimaliseren van prestaties <a href="https://helpx.adobe.com/customer-care-office-hours/aem/6x-performance-tuning-best-practices.html">deze pagina</a>.</p> </td>
  </tr>
  <tr>
   <td><strong>Stap 11</strong></td>
   <td>Server dichter naar elkaar verplaatsen of één server per gebied toevoegen</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Stap 12</strong></td>
   <td>Problemen met AEM server oplossen</td>
   <td>Controleer de volgende substappen in het diagram voor meer informatie.</td>
  </tr>
  <tr>
   <td><strong>Stap 13</strong></td>
   <td>Hardwarevereisten controleren</td>
   <td>Raadpleeg de documentatie op <a href="/help/managing/hardware-sizing-guidelines.md">Richtlijnen voor hardwareaanpassing</a>.<br /> </td>
  </tr>
  <tr>
   <td><strong>Stap 14</strong></td>
   <td>Controleren op frequente oorzaken van prestatieproblemen</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Stap 15</strong></td>
   <td>Langzame aanvragen zoeken</td>
   <td><p>U kunt op langzame verzoeken controleren door te analyseren <code>request.log</code> of door <code>rlog.jar</code>.</p> <p>Zie deze pagina voor meer informatie over het gebruik van rlog.jar.</p> <p>Zie <a href="/help/sites-deploying/monitoring-and-maintaining.md#using-rlog-jar-to-find-requests-with-long-duration-times">Aanvragen met lange tijdsduur zoeken met rlog.jar</a>.<br /> </p> <p> </p> </td>
  </tr>
  <tr>
   <td><strong>Stap 16</strong></td>
   <td>Profielserver</td>
   <td><p>Voor informatie over het profileren van hulpmiddelen kunt u met AEM gebruiken, zie <a href="/help/sites-deploying/monitoring-and-maintaining.md#tools-for-monitoring-and-analyzing-performance">Gereedschappen voor het bewaken en analyseren van prestaties</a>.<br /> </p> </td>
  </tr>
  <tr>
   <td><strong>Stap 17</strong></td>
   <td>Trage methoden zoeken in profielen</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Stap 18</strong></td>
   <td>Gemeenschappelijke scenario's voor profilering</td>
   <td>Zie <a href="/help/sites-deploying/monitoring-and-maintaining.md#analyzing-specific-scenarios">Specifieke scenario's analyseren</a> in de sectie Prestaties optimaliseren.<br /> </td>
  </tr>
  <tr>
   <td><strong>Stap 19</strong></td>
   <td>100% CPU</td>
   <td><a href="/help/sites-deploying/monitoring-and-maintaining.md#monitoring-performance">https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/previous-updates/aem-previous-versions.html</a></td>
  </tr>
  <tr>
   <td><strong>Stap 20</strong></td>
   <td>Onvoldoende geheugen</td>
   <td><br />
    <ol>
     <li><a href="/help/sites-deploying/monitoring-and-maintaining.md#out-of-memory">Onvoldoende geheugen</a></li>
     <li><a href="/help/sites-deploying/troubleshooting.md">Mijn toepassing genereert fouten vanwege onvoldoende geheugen</a></li>
     <li><a href="https://experienceleague.adobe.com/docs/experience-cloud-kcs/kbarticles/KA-17482.html">Geheugenproblemen analyseren.</a><br /> </li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Stap 21</strong></td>
   <td>I/O schijf</td>
   <td><p>Zie de <a href="/help/sites-deploying/monitoring-and-maintaining.md#disk-i-o">I/O schijf</a> in de documentatie voor toezicht en onderhoud.</p> </td>
  </tr>
  <tr>
   <td><strong>Stappen 22 en 22.1</strong></td>
   <td>Cacheverhouding</td>
   <td>Zie <a href="/help/sites-deploying/configuring-performance.md#calculating-the-dispatcher-cache-ratio">De cacheverhouding van de verzender berekenen</a>.<br /> <br /> </td>
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
     <li><a href="https://helpx.adobe.com/customer-care-office-hours/aem/6x-performance-tuning-best-practices.html">Tips voor afstemmen van prestaties</a></li>
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
   <td><p><a href="/help/sites-administering/msm-best-practices.md">Aanbevolen werkwijzen voor beheer op meerdere locaties</a><br /> </p> </td>
  </tr>
  <tr>
   <td><strong>Stap 27</strong></td>
   <td>Afstemming van activa</td>
   <td>
    <ol>
     <li><a href="/help/sites-deploying/configuring-performance.md#cq-dam-asset-synchronization-service">Assets Synchronization Service</a></li>
     <li><a href="/help/sites-deploying/configuring-performance.md#multiple-dam-instances">Meerdere DAM-instanties</a></li>
     <li>Tips voor het afstemmen van prestaties, artikel <a href="https://helpx.adobe.com/customer-care-office-hours/aem/6x-performance-tuning-best-practices.html">hier</a>.<br /> </li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Stap 28</strong></td>
   <td>Niet-afgesloten sessies</td>
   <td><p> </p> <p><a href="/help/sites-administering/troubleshoot.md#checking-for-unclosed-jcr-sessions">Controleren op niet-afgesloten JCR-sessies</a></p> <p> </p> </td>
  </tr>
  <tr>
   <td><strong>Stap 30</strong></td>
   <td>Dispatcher dichterbij verplaatsen (één object toevoegen per regio?)</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Stap 31</strong></td>
   <td>CDN vóór Dispatcher gebruiken</td>
   <td><a href="https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html#using-dispatcher-with-a-cdn">Dispatcher gebruiken met een CDN</a><br /> </td>
  </tr>
  <tr>
   <td><strong>Stap 32</strong></td>
   <td>Als u de AEM server wilt offloaden, gebruikt u sessiebeheer op Dispatcher-niveau</td>
   <td><p><a href="https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#enabling-secure-sessions-sessionmanagement">Beveiligde sessies inschakelen</a></p> </td>
  </tr>
  <tr>
   <td><strong>Stap 33</strong></td>
   <td>Verzoeken in cache plaatsen</td>
   <td>
    <ol>
     <li><a href="https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html">Algemene configuratie van verzender</a></li>
     <li><a href="https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#configuring-the-dispatcher-cache-cache">De Dispatcher Cache configureren</a></li>
    </ol> <p>Hoe te om geheim voorgeheugenverhouding te verbeteren; maak verzoeken geheim voorgeheugen-geschikt (de beste praktijken van de Verzender)</p> <p>Overweeg ook de onderstaande instellingen om uw cacheconfiguraties te optimaliseren<br /> </p>
    <ol>
     <li>Een no-cache-regel instellen voor een HTTP-aanvraag die geen GET is</li>
     <li>Vraagtekenreeksen configureren om niet cacheable te zijn</li>
     <li>Plaats geen URL's met ontbrekende extensies in cache</li>
     <li>Koppen voor cacheverificatie (mogelijk sinds Dispatcher versie 4.1.10)</li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Stap 34</strong></td>
   <td>Versie van Dispatcher upgraden</td>
   <td><p>U kunt de meest recente versie van Dispatcher downloaden op deze locatie:</p> <p><a href="https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/getting-started/release-notes.html">Koppeling volgen</a></p> </td>
  </tr>
  <tr>
   <td><strong>Stap 35</strong></td>
   <td>Dispatcher configureren</td>
   <td><a href="https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html">De Dispatcher configureren</a><br /> </td>
  </tr>
  <tr>
   <td><strong>Stap 36</strong></td>
   <td>Onvalidatie van cache controleren</td>
   <td><br />
    <ul>
     <li><a href="https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/page-invalidate.html#invalidating-dispatcher-cache-from-the-authoring-environment">Invalidatie van cache voor de auteurslaag;</a></li>
     <li><a href="https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/page-invalidate.html#invalidating-dispatcher-cache-from-a-publishing-instance">Cachevalidatie voor de publicatielaag.</a></li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Stappen 37 en 38</strong></td>
   <td>Lazy-loading</td>
   <td><a href="https://experienceleague.adobe.com/docs/experience-manager-gems-events/gems/gems2016/aem-web-performance.html">Zie Gem-sessie over AEM webprestaties.</a><br /> </td>
  </tr>
  <tr>
   <td><strong>Stap 39</strong></td>
   <td>Gebruik pre-verbindt om verbindingsoverheadkosten te verminderen</td>
   <td>Zie de Gem-sessie hierboven. Daarnaast vindt u aanvullende documentatie vóór de verbinding op W3c:<a href="https://html.spec.whatwg.org/#linkTypes"> https://html.spec.whatwg.org/#linkTypes</a></td>
  </tr>
  <tr>
   <td><strong>Stappen 40 en 41</strong><br /> </td>
   <td>Latentie en responstijd van externe hosts</td>
   <td>Onderzoek de latentie en reactietijd voor de externe gastheren.</td>
  </tr>
  <tr>
   <td><strong>Stappen 45<br /> en 47</strong><br /> </td>
   <td>HTTP/2 gebruiken</td>
   <td>Zie de Gem-sessie voor de stappen 37,38 en 39. Ook, uitchecken <a href="https://help-forums.adobe.com/content/adobeforums/en/experience-manager-forum/adobe-experience-manager.topic.html/forum__kdzc-does_anyoneknowwhe.html">dit</a> forumbericht over HTTP/2-ondersteuning.<br /> </td>
  </tr>
  <tr>
   <td><strong>Stap 49</strong></td>
   <td>Belastingsgrootte verkleinen</td>
   <td><a href="/help/sites-deploying/osgi-configuration-settings.md">Gzip inschakelen</a> en <a href="https://experienceleague.adobe.com/docs/experience-manager-gems-events/gems/gems2016/aem-web-performance.html">de afbeeldingsgrootte verkleinen</a>.<br /> </td>
  </tr>
  <tr>
   <td><strong>Stappen 42 en 43</strong></td>
   <td>Keep-Alive</td>
   <td><p>Is de <code>Keep-Alive</code> header aanwezig in de verschillende verzoeken om verbindingen opnieuw te gebruiken? Anders zou het betekenen dat elk verzoek tot een andere verbindingsinstelling leidt, wat onnodige overhead met zich meebrengt. (Standaard HTTP-aanvraaganalyse in de browser)</p> <p>U kunt de <a href="/help/sites-administering/proxy-jar.md">Proxyserver, gereedschap</a> om te controleren op Live-verbindingen.<br /> </p> </td>
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
     <li>Bronnen samenvoegen (afbeeldingen, CSS-sprites, JSON)<br /> </li>
     <li>Clientlibs insluiten:
      <ol>
       <li><a href="/help/sites-developing/clientlibs.md#creating-client-library-folders">Clientbibliotheekmappen maken</a> - zie kop Insluiten gebruiken om verzoeken te minimaliseren</li>
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
   <td><a href="https://experienceleague.adobe.com/docs/experience-manager-gems-events/gems/gems2016/aem-web-performance.html">https://experienceleague.adobe.com/docs/experience-manager-gems-events/gems/gems2016/aem-web-performance.html</a></td>
  </tr>
 </tbody>
</table>
