---
title: Integreren met dynamisch Adobe-tagbeheer
seo-title: Integreren met dynamisch Adobe-tagbeheer
description: Leer over integratie met het Dynamische Beheer van de Markering van Adobe.
seo-description: Leer over integratie met het Dynamische Beheer van de Markering van Adobe.
uuid: cbb9f942-44e3-4cd5-b07d-4298a7a08376
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
discoiquuid: b8c7a20a-7694-4a49-b66a-060720f17dad
translation-type: tm+mt
source-git-commit: 58fa0f05bae7ab5ba51491be3171b5c6ffbe870d
workflow-type: tm+mt
source-wordcount: '2222'
ht-degree: 0%

---


# Integreren met dynamisch Adobe-tagbeheer {#integrating-with-adobe-dynamic-tag-management}

Integreer [Adobe Dynamic Tag Management](https://www.adobe.com/solutions/digital-marketing/dynamic-tag-management.html) met AEM, zodat u uw Dynamic Tag Management-webeigenschappen kunt gebruiken om AEM sites bij te houden. Met Dynamic Tag Management kunnen marketers tags beheren voor het verzamelen van gegevens en gegevens verspreiden over digitale marketingsystemen. Gebruik bijvoorbeeld Dynamic Tag Management om gebruiksgegevens voor uw AEM website te verzamelen en de gegevens voor analyse te verspreiden in Adobe Analytics of Adobe Target.

Voordat u gaat integreren, moet u het dynamische tagbeheer [webeigenschap](https://microsite.omniture.com/t2/help/en_US/dtm/#Web_Properties) maken dat het domein van uw AEM-site bijhoudt. De [hostingopties](https://microsite.omniture.com/t2/help/en_US/dtm/#Hosting__Embed_Tab) van de webeigenschap moeten zodanig zijn geconfigureerd dat u AEM kunt configureren voor toegang tot de Dynamic Tag Management-bibliotheken.

Nadat u de integratie vormt, vereisen de veranderingen in Dynamische de plaatsingshulpmiddelen en de regels van het Beheer van de Markering u niet om de Dynamische configuratie van het Beheer van de Markering in AEM te veranderen. De wijzigingen zijn automatisch beschikbaar voor AEM.

>[!NOTE]
>
>Als u DTM met een configuratie van de douanevolmacht gebruikt, moet u zowel de volmachtsconfiguraties van de Cliënt van HTTP vormen aangezien sommige functionaliteiten van AEM de 3.x APIs en sommige anderen 4.x APIs gebruiken:
>
>* 3.x is geconfigureerd met [http://localhost:4502/system/console/configMgr/com.day.commons.httpclient](http://localhost:4502/system/console/configMgr/com.day.commons.httpclient)
>* 4.x wordt geconfigureerd met [http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator](http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator)

>



## Implementatieopties {#deployment-options}

De volgende plaatsingsopties beïnvloeden de configuratie van de integratie met Dynamisch Beheer van de Markering.

### Dynamic Tag Management Hosting {#dynamic-tag-management-hosting}

AEM ondersteunt Dynamic Tag Management dat wordt gehost in de cloud of wordt gehost op AEM.

* Door cloud gehost: De dynamische JavaScript-bibliotheken voor tagbeheer worden opgeslagen in de cloud en de AEM pagina&#39;s verwijzen er rechtstreeks naar.
* AEM: Met Dynamisch tagbeheer worden JavaScript-bibliotheken gegenereerd. AEM gebruikt een workflowmodel voor het ophalen en installeren van de bibliotheken.

Het type van het ontvangen dat uw implementatie gebruikt bepaalt enkele configuratie en implementatietaken die u uitvoert. Zie [Hosting - Embed Tab](https://microsite.omniture.com/t2/help/en_US/dtm/#Hosting__Embed_Tab) in de Help voor dynamisch tagbeheer voor informatie over de hostopties.

### Bibliotheek van het Staging en van de Productie {#staging-and-production-library}

Bepaal of uw AEM auteurinstantie de Dynamische het opvoeren of productiecode van het Beheer van de Markering gebruikt.

Meestal gebruikt uw auteurinstantie de Dynamische het opvoeren bibliotheken van het Beheer van de Markering, en de productiemilitie gebruikt de productiebibliotheken. In dit scenario kunt u de instantie van de auteur gebruiken om niet-goedgekeurde configuraties voor dynamisch tagbeheer te testen.

Indien gewenst, kan uw auteurinstantie de productiebibliotheken gebruiken. De browser van het Web plugins zijn beschikbaar die u toelaten om tussen het gebruik van het opvoeren bibliotheken voor testende doeleinden te schakelen wanneer de bibliotheken wolk-ontvangen zijn.

### De dynamische implementatie van tagbeheer gebruiken {#using-the-dynamic-tag-management-deployment-hook}

Wanneer AEM gastheren de Dynamische bibliotheken van het Beheer van de Markering, kunt u de Dynamische de plaatsingshakendienst van het Beheer van de Markering gebruiken om bibliotheekupdates aan AEM automatisch te duwen. De bibliotheekupdates worden geduwd wanneer de veranderingen in de bibliotheken zoals worden aangebracht wanneer de Dynamische het Webeigenschappen van het Beheer van de Markering worden uitgegeven.

Om de plaatsingshaak te gebruiken, moet het Dynamische Beheer van de Markering met de AEM instantie kunnen verbinden die gastheren de bibliotheken. U moet [toegang tot AEM](/help/sites-administering/dtm.md#enabling-access-for-the-deployment-hook-service) voor de Dynamische servers van het Beheer van de Markering toelaten.

In sommige omstandigheden AEM onbereikbaar, zoals wanneer AEM achter een firewall ligt. In deze gevallen kunt u de optie voor het importeren van opiniepeilingen AEM gebruiken om de bibliotheken regelmatig op te halen. Een uitsnijdtaakexpressie schrijft het programma voor het downloaden van bibliotheken voor.

## Toegang voor de implementatie van Hook-service {#enabling-access-for-the-deployment-hook-service} inschakelen

Laat de Dynamische de plaatsingshaakdienst van het Beheer van de Markering aan toegang tot AEM toe zodat de dienst de AEM-ontvangen bibliotheken kan bijwerken. Geef het IP-adres op van Dynamic Tag Management-servers die de staging- en productiebibliotheken naar wens bijwerken:

* Staging: `107.21.99.31`
* Productie: `23.23.225.112` en `204.236.240.48`

Voer de configuratie uit gebruikend of [de Console van het Web](/help/sites-deploying/configuring-osgi.md#osgi-configuration-with-the-web-console) of een [`sling:OsgiConfig`](/help/sites-deploying/configuring-osgi.md#osgi-configuration-in-the-repository) knoop:

* In de Console van het Web, gebruik het punt van de Configuratie van de Haak van de Adobe DTM op de pagina van de Configuratie.
* Voor een configuratie OSGi, is de dienst PID `com.adobe.cq.dtm.impl.servlets.DTMDeployHookServlet`.

In de volgende tabel worden de eigenschappen beschreven die moeten worden geconfigureerd.

| Webconsole, eigenschap | OSGi, eigenschap | Beschrijving |
|---|---|---|
| DTM IP-witte lijst opslaan | `dtm.staging.ip.whitelist` | Het IP-adres van de Dynamic Tag Management-server waarmee de testbibliotheken worden bijgewerkt. |
| Productie DTM IP witte lijst | `dtm.production.ip.whitelist` | Het IP-adres van de Dynamic Tag Management-server waarmee de productiebibliotheken worden bijgewerkt. |

## De dynamische configuratie voor tagbeheer maken {#creating-the-dynamic-tag-management-configuration}

Maak een wolkenconfiguratie zodat de AEM-instantie kan worden geverifieerd met Dynamic Tag Management en kan communiceren met uw webeigenschap.

>[!NOTE]
>
>Vermijd het opnemen van twee volgcodes voor Adobe Analytics op uw pagina&#39;s wanneer uw DTM-webeigenschap het Adobe Analytics-gereedschap bevat en u ook [Content Insight](/help/sites-authoring/content-insights.md) gebruikt. Selecteer in de [Adobe Analytics-cloudconfiguratie](/help/sites-administering/adobeanalytics-connect.md#configuring-the-connection-to-adobe-analytics) de optie Geen code bijhouden opnemen.

### Algemene instellingen {#general-settings}

<table>
 <tbody>
  <tr>
   <th>Eigenschap</th>
   <th>Beschrijving</th>
  </tr>
  <tr>
   <td>API-token</td>
   <td>De waarde van de eigenschap API Token van uw Dynamic Tag Management-gebruikersaccount. AEM gebruikt deze eigenschap om te verifiëren met Dynamic Tag Management.</td>
  </tr>
  <tr>
   <td>Bedrijf</td>
   <td>Het bedrijf waaraan uw login identiteitskaart wordt geassocieerd.</td>
  </tr>
  <tr>
   <td>Eigenschap</td>
   <td>De naam van het bezit van het Web dat u voor het beheren van de markeringen voor uw AEM plaats creeerde.</td>
  </tr>
  <tr>
   <td>Productiecode opnemen op auteur</td>
   <td><p>Selecteer deze optie om ervoor te zorgen dat de AEM auteur en de publicatie instanties de productieversie van de bibliotheken voor dynamisch tagbeheer gebruiken. </p> <p>Als deze optie niet is geselecteerd, zijn de instellingen voor afspelen van toepassing op de auteurinstantie en zijn de Productie-instellingen van toepassing op de publicatie-instantie.</p> </td>
  </tr>
 </tbody>
</table>

### Eigenschappen voor zelfhosting - Staging en productie {#self-hosting-properties-staging-and-production}

De volgende eigenschappen van de Dynamische configuratie van het Beheer van de Markering laten AEM toe om de Dynamische bibliotheken van het Beheer van de Markering te ontvangen. Met deze eigenschappen kunnen AEM de bibliotheken downloaden en installeren. Desgewenst kunt u de bibliotheken automatisch bijwerken om ervoor te zorgen dat deze de wijzigingen weerspiegelen die zijn aangebracht in de beheertoepassing Dynamisch tagbeheer.

Sommige eigenschappen gebruiken waarden die u uit de sectie van de Download van de Bibliotheek van het Embed lusje voor uw Dynamische het Webbezit van het Beheer van de Markering verkrijgt. Zie [Bibliotheek downloaden](https://microsite.omniture.com/t2/help/en_US/dtm/#Library_Download) in de Help van dynamisch tagbeheer voor meer informatie.

>[!NOTE]
>
>Wanneer u de Dynamic Tag Management-bundel host op AEM, moet Bibliotheek downloaden zijn ingeschakeld in Dynamisch tagbeheer voordat u de configuratie maakt. Akamai moet ook zijn ingeschakeld, omdat Akamai de bibliotheken beschikbaar stelt om te downloaden.

Wanneer het ontvangen van de Dynamische bibliotheken van het Beheer van de Markering op AEM, AEM automatisch sommige eigenschappen van het Webbezit volgens uw configuratie vormt. Zie de beschrijvingen in de volgende lijst.

<table>
 <tbody>
  <tr>
   <th>Eigenschap</th>
   <th>Beschrijving</th>
  </tr>
  <tr>
   <td>Zelf hosten gebruiken</td>
   <td>Selecteer deze optie wanneer u het bibliotheekbestand voor dynamisch tagbeheer op AEM host. Als u deze optie selecteert, worden de andere eigenschappen in deze tabel weergegeven.</td>
  </tr>
  <tr>
   <td>DTM Bundle URL</td>
   <td>De URL die moet worden gebruikt voor het downloaden van de Dynamic Tag Management-bibliotheek. Verkrijg deze waarde van de sectie van Download URLs van de Bibliotheek downloadt pagina van Dynamisch het Beheer van de Markering. Om veiligheidsredenen moet deze waarde handmatig worden geconfigureerd.</td>
  </tr>
  <tr>
   <td>Workflow downloaden</td>
   <td><p>Het workflowmodel dat moet worden gebruikt voor het downloaden en installeren van de Dynamic Tag Management-bibliotheek. Het standaardmodel is Default DTM Bundle Download. Gebruik dit model tenzij u een aangepast model hebt gemaakt.</p> <p>De standaarddownloadworkflow activeert automatisch de bibliotheken wanneer ze worden gedownload.</p> </td>
  </tr>
  <tr>
   <td>Domeinhint</td>
   <td><p>(Optioneel) Het domein van de AEM server die als host fungeert voor de Dynamic Tag Management-bibliotheek. Specificeer een waarde om het standaarddomein met voeten te treden dat voor <a href="/help/sites-developing/externalizer.md">de dienst van de Verbinding van de Verbinding van </a> van &lt;dag CQ wordt gevormd.</p> <p>Wanneer AEM verbinding maakt met Dynamisch tagbeheer, gebruikt u deze waarde om het Staging HTTP Path of het Production HTTP Path van de eigenschappen Library Download voor de Dynamic Tag Management-webeigenschap te configureren.</p> </td>
  </tr>
  <tr>
   <td>Beveiligde domeintip</td>
   <td><p>(Optioneel) Het domein van de AEM server die als host fungeert voor de Dynamic Tag Management-bibliotheek via HTTPS. Specificeer een waarde om het standaarddomein met voeten te treden dat voor <a href="/help/sites-developing/externalizer.md">de dienst van de Verbinding van de Verbinding van </a> van &lt;dag CQ wordt gevormd.</p> <p>Wanneer AEM verbinding maakt met Dynamisch tagbeheer, gebruikt u deze waarde om het Staging HTTPS-pad of het Production HTTPS-pad van de eigenschappen Library Download te configureren voor de Dynamic Tag Management-webeigenschap.</p> </td>
  </tr>
  <tr>
   <td>Gedeeld geheim</td>
   <td><p>(Optioneel) Het gedeelde geheim dat moet worden gebruikt voor het decoderen van de download. Verkrijg deze waarde van het Gedeelde Geheime gebied van de pagina van de Download van de Bibliotheek van het Dynamische Beheer van de Markering.</p> <p><strong>Opmerking: </strong> u moet de  <a href="https://www.openssl.org/docs/apps/openssl.html"></a> OpenSSL-bibliotheken hebben geïnstalleerd op de computer waarop AEM is geïnstalleerd, zodat AEM de gedownloade bibliotheken kan decoderen.</p> </td>
  </tr>
  <tr>
   <td>Opiniepeilingimportfunctie inschakelen</td>
   <td><p>(Optioneel) Selecteer deze optie om de Dynamic Tag Management-bibliotheek periodiek te downloaden en installeren om er zeker van te zijn dat u een bijgewerkte versie gebruikt. Als u Dynamisch tagbeheer inschakelt, worden geen HTTP-aanvragen naar de URL van Hook-POST implementeren verzonden.</p> <p>AEM vormt automatisch het bezit van HookURL van de Reparatie van de Eigenschappen van de Download van de Bibliotheek voor het Dynamische het Webbezit van het Beheer van de Markering. Wanneer geselecteerd, wordt het bezit gevormd zonder waarde. Wanneer niet geselecteerd, wordt het bezit gevormd met URL van uw Dynamische configuratie van het Beheer van de Markering.</p> <p>Schakel polling importer in wanneer de Dynamic Tag Management-haak geen verbinding kan maken met AEM, bijvoorbeeld wanneer AEM zich achter een firewall bevindt.</p> </td>
  </tr>
  <tr>
   <td>Planningsexpressie</td>
   <td>(Wordt weergegeven en is vereist als de optie Polling Importer inschakelen is geselecteerd.) Een uitsnijdexpressie die bepaalt wanneer de bibliotheken voor dynamisch tagbeheer worden gedownload.</td>
  </tr>
 </tbody>
</table>

![chlimage_1-352](assets/chlimage_1-352.png)

### Hosteigenschappen voor cloud - Staging en productie {#cloud-hosting-properties-staging-and-production}

U configureert de volgende eigenschappen voor uw dynamische configuratie van het Tagbeheer wanneer de Dynamische Configuratie van de Markering wolk-ontvangen is.

<table>
 <tbody>
  <tr>
   <th>Eigenschap</th>
   <th>Beschrijving</th>
  </tr>
  <tr>
   <td>Zelf hosten gebruiken</td>
   <td>Schakel deze optie uit als het bibliotheekbestand voor dynamisch tagbeheer wordt gehost in de cloud.</td>
  </tr>
  <tr>
   <td>Koptekstcode</td>
   <td><p>De koptekstcode voor het opvoeren die wordt verkregen uit Dynamic Tag Management voor uw host. Deze waarde wordt automatisch ingevuld wanneer u verbinding maakt met Dynamisch tagbeheer.</p> <p> Als u de code wilt weergeven in Dynamisch tagbeheer, klikt u op het tabblad Insluiten en vervolgens op de hostnaam. Vouw de sectie Koptekstcode uit en klik op de code Insluiten kopiëren van de code Insluiten van het werkgebied of het gebied Code insluiten van de productie.</p> </td>
  </tr>
  <tr>
   <td>Voettekstcode</td>
   <td><p>De voettekstcode voor het opvoeren die wordt verkregen van het Dynamische Beheer van de Markering voor uw gastheer. Deze waarde wordt automatisch ingevuld wanneer u verbinding maakt met Dynamisch tagbeheer.</p> <p>Als u de code wilt weergeven in Dynamisch tagbeheer, klikt u op het tabblad Insluiten en vervolgens op de hostnaam. Vouw de sectie Voettekstcode uit en klik op de sectie Code insluiten kopiëren van de code Insluiten van werkruimte of het gebied Code insluiten van productie.</p> </td>
  </tr>
 </tbody>
</table>

![chlimage_1-353](assets/chlimage_1-353.png)

In de volgende procedure wordt gebruikgemaakt van de geoptimaliseerde interface voor het configureren van de integratie met Dynamic Tag Management.

1. Klik in de track op Gereedschappen > Bewerkingen > Wolk > Cloud Services.
1. In het dynamische gebied van het Beheer van de Markering, verschijnen één van de volgende verbindingen voor het toevoegen van een configuratie:

   * Klik vormen nu als dit de eerste configuratie is die u toevoegt.
   * Klik op Configuraties tonen en klik vervolgens op de koppeling + naast Beschikbare configuraties als er een of meer configuraties zijn gemaakt.

   ![chlimage_1-354](assets/chlimage_1-354.png)

1. Typ een titel voor de configuratie en klik vervolgens op Maken.
1. Voer in het veld API-token de waarde in van de eigenschap API Token van uw gebruikersaccount voor dynamisch tagbeheer.

   Neem contact op met de DTM Client Care voor de waarde van uw API-token.

   >[!NOTE]
   >
   >Het API-token verloopt pas wanneer de gebruiker van het Dynamic Tag Management er expliciet om vraagt.

   ![chlimage_1-355](assets/chlimage_1-355.png)

1. Klik op Verbinding maken met DTM. AEM wordt geverifieerd met Dynamic Tag Management en haalt de lijst op met bedrijven waaraan uw account is gekoppeld.
1. Selecteer het Bedrijf, en selecteer dan het Bezit dat u gebruikt om uw AEM plaats te volgen.
1. Schakel de optie Productiecode opnemen op auteur uit als u code in de opmaakcode gebruikt.
1. Geef indien nodig waarden op voor de eigenschappen op het tabblad Staging-instellingen en het tabblad Productie-instellingen en klik op OK.

## De dynamische tagbeheerbibliotheek {#manually-downloading-the-dynamic-tag-management-library} handmatig downloaden

Download handmatig de bibliotheken voor dynamisch tagbeheer om deze meteen bij te werken bij AEM. Download bijvoorbeeld handmatig wanneer u een bijgewerkte bibliotheek wilt testen voordat de pollingimporter is gepland om de bibliotheek automatisch te downloaden.

1. Klik in de track op Gereedschappen > Bewerkingen > Wolk > Cloud Services.
1. Klik in het gedeelte Dynamisch tagbeheer op Configuraties tonen en klik vervolgens op uw configuratie.
1. Klik in het gebied Instellingen voor staging of Productie-instellingen op de knop Workflow voor downloaden om de bibliotheekbundel te downloaden en implementeren.

   ![chlimage_1-356](assets/chlimage_1-356.png)

>[!NOTE]
>
>De gedownloade bestanden worden opgeslagen onder `/etc/clientlibs/dtm/my config/companyID/propertyID/servertype`.
>
>Het volgende wordt direct genomen van uw [DTM configuratie](#creating-the-dynamic-tag-management-configuration).
>
>* `myconfig`
>* `companyID`
>* `propertyID`
>* `servertype`

>



## Een dynamische configuratie voor tagbeheer koppelen aan uw site {#associating-a-dynamic-tag-management-configuration-with-your-site}

Koppel uw Dynamic Tag Management-configuratie aan de pagina&#39;s van uw website, zodat AEM het vereiste script aan de pagina&#39;s toevoegt. Koppel de hoofdpagina van uw site aan de configuratie. Alle afstammingen van die pagina nemen de koppeling over. Indien nodig, kunt u de vereniging op een afstammende pagina met voeten treden.

Gebruik de volgende procedure om een pagina en de afstammelingen aan een Dynamische configuratie van het Beheer van de Markering te associëren.

1. Open de hoofdpagina van uw site in de klassieke gebruikersinterface.
1. Gebruik Sidetrap om de pagina-eigenschappen te openen.
1. Klik op het tabblad Cloud Services op Service toevoegen, selecteer Dynamisch tagbeheer en klik op OK.

   ![chlimage_1-357](assets/chlimage_1-357.png)

1. Gebruik het Dynamische drop-down menu van het Beheer van de Markering om uw configuratie te selecteren, en dan O.K. te klikken.

Gebruik de volgende procedure om de geërfte configuratievereniging voor een pagina met voeten te treden. De overschrijving heeft invloed op de pagina en op alle onderliggende pagina&#39;s.

1. Open de pagina in klassieke UI.
1. Gebruik Sidetrap om de pagina-eigenschappen te openen.
1. Klik op het tabblad Cloud Services op het hangslotpictogram naast de eigenschap Geërfd van en klik vervolgens op Ja in het bevestigingsdialoogvenster.

   ![chlimage_1-358](assets/chlimage_1-358.png)

1. Verwijder of selecteer een andere Dynamische configuratie van het Beheer van de Markering, en klik dan O.K.

