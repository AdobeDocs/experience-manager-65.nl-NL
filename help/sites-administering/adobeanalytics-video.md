---
title: Video bijhouden configureren voor Adobe Analytics
description: Meer informatie over het configureren van videotracering voor SiteCatalyst.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
docset: aem65
exl-id: 5d51f898-b6d1-40ac-bdbf-127cda1dc777
solution: Experience Manager, Experience Manager Sites
feature: Integration
role: Admin
source-git-commit: f30decf0e32a520dcda04b89c5c1f5b67ab6e028
workflow-type: tm+mt
source-wordcount: '1758'
ht-degree: 0%

---

# Video bijhouden configureren voor Adobe Analytics{#configuring-video-tracking-for-adobe-analytics}

Er zijn verschillende methoden beschikbaar voor het bijhouden van videogebeurtenissen, waarvan er twee oudere opties zijn voor oudere versies van Adobe Analytics. Deze oudere optie is: oudere mijlpalen en oudere seconden.

>[!NOTE]
>
>Alvorens u verdergaat, zorg ervoor dat u a **playable video** geupload binnen AEM hebt.
>
>Om ervoor te zorgen dat uw video&#39;s op de pagina spelen, raadpleeg **[dit leerprogramma](/help/sites-authoring/default-components-foundation.md#video)** voor informatie over hoe te om videodossiers in AEM te transcoderen.

Gebruik de volgende procedure om een framework voor het bijhouden van video&#39;s in te stellen met elke methode.

>[!NOTE]
>
>Voor nieuwe implementaties, adviseert men dat u **niet** de erfenisopties voor video het volgen gebruikt. Gebruik in plaats hiervan de **methode 0} Mijlpalen.**

## Gemeenschappelijke stappen {#common-steps}

1. Opstelling een Web-pagina door a **videocomponent** van sidekick te slepen en een playable **video als activa** voor de component toe te voegen

1. [ creeer een configuratie en kader van Adobe Analytics ](/help/sites-administering/adobeanalytics.md).

   * De voorbeelden in de secties die volgen gebruiken de naam **my-sc-configuration** voor de configuratie en **video** voor het kader.

1. Voor de kaderpagina, selecteer RSID en plaats het gebruik aan allen. ([ https://localhost:4502/cf#/etc/cloudservices/sitecatalyst/videoconf/videofw.html](https://localhost:4502/cf#/etc/cloudservices/sitecatalyst/videoconf/videofw.html))
1. Sleep de component Video van de categorie Algemeen in Sidekick naar het framework.
1. Selecteer een methode voor bijhouden:

   * [Mijlpalen](/help/sites-administering/adobeanalytics.md)
   * [Niet-oudere mijlpalen](/help/sites-administering/adobeanalytics.md)
   * [Legacy-mijlpalen](/help/sites-administering/adobeanalytics.md)
   * [Oudere seconden](/help/sites-administering/adobeanalytics.md)

1. Wanneer u een methode voor bijhouden selecteert, wordt de lijst met CQ-variabelen dienovereenkomstig gewijzigd. Gebruik de secties die volgen voor informatie over hoe te om de component verder te vormen en de CQ variabelen met de eigenschappen van Adobe Analytics in kaart te brengen.

## Mijlpalen {#milestones}

De methode van Mijlpalen volgt de meeste informatie over de video, is hoogst klantgericht, en gemakkelijk te vormen.

Als u de methode Mijlpalen wilt gebruiken, geeft u op tijd gebaseerde verschuivingen op om de mijlpalen te definiëren. Wanneer een videoplayback een mijlpaal overgaat, roept de pagina Adobe Analytics aan om de gebeurtenis te volgen. Voor elke mijlpaal die u definieert, maakt de component een CQ-variabele die u kunt toewijzen aan een Adobe Analytics-eigenschap. De naam van deze CQ-variabelen gebruikt de volgende indeling:

```shell
eventdata.events.milestoneXX
```

Het achtervoegsel XX is de spoorcompensatie die de mijlpaal bepaalt. Als u bijvoorbeeld verschuivingen van 4, 8, 16, 20 en 28 seconden opgeeft, worden de volgende CQ-variabelen gegenereerd:

* `eventdata.events.milestone4`
* `eventdata.events.milestone8`
* `eventdata.events.milestone16`
* `eventdata.events.milestone20`
* `eventdata.events.milestone28`

In de volgende tabel worden de standaard CQ-variabelen beschreven die voor de methode Mijlpalen worden verschaft:

<table>
 <tbody>
  <tr>
   <th>CQ-variabelen</th>
   <th>Adobe Analytics-eigenschappen</th>
  </tr>
  <tr>
   <td>eventdata.videoName </td>
   <td>De variabelen die aan dit worden in kaart gebracht zullen de <strong> gebruikersvriendelijke </strong> naam (<strong> Titel </strong>) van de video bevatten als reeks in DAM; als dit niet wordt geplaatst, zal het 4} dossier van de video </strong> in plaats daarvan worden verzonden. <strong> Slechts één keer verzonden, aan het begin van het afspelen van een video.</td>
  </tr>
  <tr>
   <td>eventdata.videoFileName </td>
   <td>Variabelen die hieraan zijn toegewezen, bevatten de bestandsnaam. Alleen verzonden samen met eventData.events.a.media.view </td>
  </tr>
  <tr>
   <td>eventdata.videoFilePath </td>
   <td>Variabelen die hieraan zijn toegewezen, bevatten het bestandspad op de server. Alleen verzonden samen met eventData.events.a.media.view </td>
  </tr>
  <tr>
   <td>eventdata.events.a.media.segmentView </td>
   <td>Verzonden telkens wanneer een segment mijlpaal wordt overgegaan </td>
  </tr>
  <tr>
   <td>eventdata.events.a.media.timePlayed</td>
   <td>Verzonden telkens als een mijlpaal wordt teweeggebracht, wordt het aantal seconden de gebruiker besteedde het letten op het bepaalde segment ook verzonden samen met deze gebeurtenis. bijvoorbeeld, eventX=21 <br /> </td>
  </tr>
  <tr>
   <td>eventdata.events.a.media.view </td>
   <td>Verzonden bij initialisatie videoweergave</td>
  </tr>
  <tr>
   <td>eventdata.events.a.media.complete </td>
   <td>Verzonden wanneer video klaar is met afspelen <br /> </td>
  </tr>
  <tr>
   <td>eventdata.events.milestoneX </td>
   <td>Verzonden wanneer de bepaalde mijlpaal wordt overgegaan, X staat voor de tweede mijlpaal wordt teweeggebracht bij <br /> </td>
  </tr>
  <tr>
   <td>eventdata.a.contentType </td>
   <td>Verzonden op elke mijlpaal; toont omhoog zoals pev3 in de vraag van Adobe Analytics, gewoonlijk verzonden als "video"<br /> </td>
  </tr>
  <tr>
   <td>eventdata.a.media.name </td>
   <td>Komt exact overeen met eventdata.videoName </td>
  </tr>
  <tr>
   <td>eventdata.a.media.segment </td>
   <td>Bevat informatie over het segment dat is weergegeven, bijvoorbeeld <code>2:O:4-8</code> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>U kunt een video **gebruikersvriendelijke** naam plaatsen door de video voor het uitgeven in DAM te openen, en het **Titel** meta-gegevensgebied aan de gewenste naam te plaatsen.

1. Nadat u Mijlpalen hebt geselecteerd als de methode voor bijhouden, voert u in het vak Verschuiving track een door komma&#39;s gescheiden lijst met verschuivingen in seconden in. De volgende waarde definieert bijvoorbeeld mijlpalen 4, 8, 16, 20 en 28 seconden na het begin van de video:

   ```xml
   4,8,16,20,24
   ```

   De verschuivingswaarden moeten gehele getallen zijn die groter zijn dan 0. De standaardwaarde is `10,25,50,75` .

1. Als u de CQ-variabelen wilt toewijzen aan Adobe Analytics-eigenschappen, sleept u de Adobe Analytics-eigenschappen van ContentFinder naast de CQ-variabele op de component.

   Voor informatie over het optimaliseren van de afbeeldingen, zie [ het Meten Video in Adobe Analytics ](https://experienceleague.adobe.com/docs/media-analytics/using/media-overview.html) gids.

1. [ voeg het kader ](/help/sites-administering/adobeanalytics.md) aan de pagina toe.
1. Om de opstelling op **wijze van de Voorproef** te testen, speel de video om de vraag van Adobe Analytics te krijgen om teweeg te brengen.

De volgende voorbeelden van Adobe Analytics-volggegevens zijn van toepassing op het bijhouden van mijlpaden met gebruik van trackverschuivingen van 4,8,16,20 en 24, en de volgende toewijzingen voor de CQ-variabelen:

<table>
 <tbody>
  <tr>
   <th>Variabele CQ</th>
   <th>Adobe Analytics, eigenschap</th>
  </tr>
  <tr>
   <td>eventdata.videoName </td>
   <td>prop2</td>
  </tr>
  <tr>
   <td>eventdata.videoFileName </td>
   <td>prop3 </td>
  </tr>
  <tr>
   <td>eventdata.videoFilePath </td>
   <td>prop4</td>
  </tr>
  <tr>
   <td>eventdata.events.a.media.segmentView </td>
   <td>event1</td>
  </tr>
  <tr>
   <td>eventdata.events.a.media.timePlayed</td>
   <td>event2<br /> </td>
  </tr>
  <tr>
   <td>eventdata.events.a.media.view </td>
   <td>event3</td>
  </tr>
  <tr>
   <td>eventdata.events.a.media.complete </td>
   <td>event4<br /> </td>
  </tr>
  <tr>
   <td>eventdata.events.milestone4</td>
   <td>event10</td>
  </tr>
  <tr>
   <td>eventdata.events.milestone8</td>
   <td>event11</td>
  </tr>
  <tr>
   <td>eventdata.events.milestone16</td>
   <td>event12</td>
  </tr>
  <tr>
   <td>eventdata.events.milestone20</td>
   <td>event13</td>
  </tr>
  <tr>
   <td>eventdata.events.milestone24</td>
   <td>event14</td>
  </tr>
  <tr>
   <td>eventdata.a.contentType </td>
   <td>eVar3</td>
  </tr>
  <tr>
   <td>eventdata.a.media.name </td>
   <td>eVar1, prop1 </td>
  </tr>
  <tr>
   <td>eventdata.a.media.segment </td>
   <td>eVar2</td>
  </tr>
 </tbody>
</table>

In dit voorbeeld wordt de component Video als volgt weergegeven op de frameworkpagina:

![ video1 ](assets/video1.png)

>[!NOTE]
>
>Om de vraag te zien die aan Adobe Analytics wordt gemaakt gebruik een aangewezen hulpmiddel, zoals Debugger DigitalPulse of Fiddler.

De vraag aan Adobe Analytics die het verstrekte voorbeeld gebruikt zou als dit moeten kijken wanneer bekeken met Debugger DigitalPulse:

![ chlimage_1-128 ](assets/chlimage_1-128.png)

*dit is de **eerste vraag**die aan Adobe Analytics wordt gemaakt die de volgende waarden bevatten:*

* *prop1 en eVar1 voor eventdata.a.media.name,*
* *props2-4, samen met eVar2 en eVar3 die contentType (video) en segment (1 :O: 1-4) bevatten*
* *event3 die aan eventdata.events.a.media.view in kaart werd gebracht.*

![ chlimage_1-129 ](assets/chlimage_1-129.png)

*dit is de **derde vraag**die aan Adobe Analytics wordt gemaakt:*

* *prop1 en eVar1 bevatten a.media.name;*
* *event1 omdat een segment is bekeken*
* *event2 die met tijd wordt verzonden = 4*
* *event11 verzonden omdat eventData.events.milestone8 is bereikt*
* *prop2 aan 4 wordt niet verzonden (aangezien eventdata.events.a.media.view niet werd teweeggebracht)*

## Niet-oude mijlpalen {#non-legacy-milestones}

De methode Niet-verouderde mijlpalen is vergelijkbaar met de methode Mijlpalen, behalve dat mijlpalen worden gedefinieerd met percentages van de lengte van de sporen. De gemeenschappelijke waarden zijn als volgt:

* Wanneer een videoplayback een mijlpaal overgaat, roept de pagina Adobe Analytics aan om de gebeurtenis te volgen.
* De [ statische reeks variabelen van CQ ](#cqvars) die voor afbeelding met eigenschappen van Adobe Analytics worden bepaald.
* Voor elke mijlpaal die u definieert, maakt de component een CQ-variabele die u kunt toewijzen aan een Adobe Analytics-eigenschap.

De naam van deze CQ-variabelen gebruikt de volgende indeling:

Het achtervoegsel XX is het percentage van spoorlengte dat de mijlpaal bepaalt. Als u bijvoorbeeld percentages van 10, 25, 50 en 75 opgeeft, worden de volgende CQ-variabelen gegenereerd:

* `eventdata.events.milestone10`
* `eventdata.events.milestone25`
* `eventdata.events.milestone50`
* `eventdata.events.milestone75`

```shell
eventdata.events.milestoneXX
```

1. Nadat u Niet-verouderde mijlpalen hebt geselecteerd als methode voor het bijhouden van wijzigingen, voert u in het vak Verschuiving track een door komma&#39;s gescheiden lijst met percentages van de lengte van de track in. De volgende standaardwaarde definieert bijvoorbeeld mijlpalen op 10, 25, 50 en 75 procent van de lengte van het spoor:

   ```xml
   10,25,50,75
   ```

   De verschuivingswaarden moeten gehele getallen zijn die groter zijn dan 0.

1. Als u de CQ-variabelen wilt toewijzen aan Adobe Analytics-eigenschappen, sleept u de Adobe Analytics-eigenschappen van ContentFinder naast de CQ-variabele op de component.

   Voor informatie over het optimaliseren van de afbeeldingen, zie [ het Meten Video in Adobe Analytics ](https://experienceleague.adobe.com/docs/media-analytics/using/media-overview.html) gids.

1. [ voeg het kader ](/help/sites-administering/adobeanalytics.md) aan de pagina toe.
1. Om de opstelling op **wijze van de Voorproef** te testen, speel de video om de vraag van Adobe Analytics te krijgen om teweeg te brengen.

## Legacy-mijlpalen {#legacy-milestones}

Deze methode is gelijkaardig aan de methode van Mijlpalen met het verschil dat de mijlpalen die in het *Volgorde* gebied worden gespecificeerd percentages in plaats van vastgestelde punten binnen de video zijn.

>[!NOTE]
>
>Het veld Verschuiving voor reeksspatiëring accepteert alleen een door komma&#39;s gescheiden lijst met hele getallen tussen 1 en 100.

1. Stel de verschuiving track in.

   * bijvoorbeeld 10,50,75,100

   Bovendien is de informatie die naar Adobe Analytics wordt verzonden minder aanpasbaar. Er zijn slechts drie variabelen beschikbaar voor toewijzing:

<table>
 <tbody>
  <tr>
   <td>eventData.videoName <br /> </td>
   <td>De variabelen die aan dit worden in kaart gebracht zullen de <strong> gebruikersvriendelijke </strong> naam (<strong> Titel </strong>) van de video bevatten als reeks in DAM; als de Titel niet wordt geplaatst, zal het 4} dossier van de video </strong> in plaats daarvan worden verzonden. <strong> Slechts één keer verzonden, aan het begin van het spelen van een video.<br /> </td>
  </tr>
  <tr>
   <td>eventdata.videoFileName </td>
   <td>Variabelen die hieraan zijn toegewezen, bevatten de bestandsnaam. Slechts één keer verzonden, aan het begin van het afspelen van een video.</td>
  </tr>
  <tr>
   <td>eventdata.videoFilePath </td>
   <td>De variabele die aan dit wordt toegewezen zal het weg van het dossier op de server bevatten. Slechts één keer verzonden, aan het begin van het afspelen van een video.</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>U kunt een video **gebruikersvriendelijke** naam plaatsen door de video voor het uitgeven in DAM te openen, en het **Titel** meta-gegevensgebied aan de gewenste naam te plaatsen. U moet ook de aangebrachte wijzigingen opslaan wanneer u klaar bent.

1. Deze variabelen toewijzen aan de profielen 1 tot en met 3

   De **rest van de relevante informatie** in de vraag zal in **worden samengevoegd één** genoemde variabele **pev3**.

   **vraag van de Steekproef** aan Adobe Analytics die het verstrekte voorbeeld gebruikt zou als dit moeten kijken wanneer bekeken met Debugger DigitalPulse:

   ![ lmilestone1 ](assets/lmilestones1.png)

   *de **pev3**variabele die in de vraag wordt verzonden bevat de volgende informatie:*

   * *Naam* - de naam van het videodossier (*film.avi*)

   * *Lengte* - de lengte van het videodossier, in seconden (*100*)

   * {de Naam van de Speler van 0} *- de videospeler die wordt gebruikt om het videodossier (* HTML5 video *) te spelen*

   * *Totale Seconden gespeeld* - het totale aantal seconden de video werd gespeeld (*25*)

   * *Tijdstempel van het Begin* - Tijdstempel die identificeert toen het videospel begon (*1331035567*)

   * *Zitting van het Spel* - de details van de spelzitting. In dit veld wordt aangegeven hoe de gebruiker met de video heeft gewerkt. Dit zou gegevens kunnen omvatten zoals waar zij begonnen de video te spelen, of zij de videoschuif gebruikten om de video vooruit te gaan, en waar zij ophouden speel de video (*L10E24S58L58 - de video werd tegengehouden bij sec. 25 van sectie L10, overgeslagen tot sec. 48*)

## Verouderde seconden {#legacy-seconds}

Wanneer het gebruiken van de** erfenisseconden** methode, worden de vraag van Adobe Analytics teweeggebracht om de n-de seconde, waar N op het Spoor compensatieveld wordt gespecificeerd.

1. Stel de verschuiving van track in op een willekeurig aantal seconden,

   * bijvoorbeeld 6

   >[!NOTE]
   >
   >Het veld Tracking-verschuiving accepteert alleen hele getallen die hoger zijn dan 0

   De gegevens die naar Adobe Analytics worden verzonden, kunnen minder worden aangepast. Er zijn slechts drie variabelen beschikbaar voor toewijzing:

<table>
 <tbody>
  <tr>
   <td>eventData.videoName <br /> </td>
   <td>De variabelen die aan dit worden in kaart gebracht zullen de <strong> gebruikersvriendelijke </strong> naam (<strong> Titel </strong>) van de video bevatten als reeks in DAM; als de Titel niet wordt geplaatst, zal het 4} dossier van de video </strong> in plaats daarvan worden verzonden. <strong> Slechts één keer verzonden, aan het begin van het spelen van een video.<br /> </td>
  </tr>
  <tr>
   <td>eventdata.videoFileName </td>
   <td>De variabele die hieraan is toegewezen, bevat de bestandsnaam. Slechts één keer verzonden, aan het begin van het afspelen van een video.</td>
  </tr>
  <tr>
   <td>eventdata.videoFilePath </td>
   <td>De variabele die aan dit wordt toegewezen zal het weg van het dossier op de server bevatten. Slechts één keer verzonden, aan het begin van het afspelen van een video.</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>U kunt een video **gebruikersvriendelijke** naam plaatsen door de video voor het uitgeven in DAM te openen, en het **Titel** meta-gegevensgebied aan de gewenste naam te plaatsen. U moet ook de aangebrachte wijzigingen opslaan wanneer u klaar bent.

1. Deze variabelen toewijzen aan prop1, prop2 en prop3

   De **rest van de relevante informatie** in de vraag zal in **worden samengevoegd één** genoemde variabele **pev3**.

   De vraag aan Adobe Analytics die het verstrekte voorbeeld gebruikt zou als dit moeten kijken wanneer bekeken met Debugger DigitalPulse:

   ![ seconden ](assets/lseconds.png)

   *de vraag is gelijkaardig aan de vraag van de Mondiale Oudheid hierboven. Zie de informatie over pev3 die onder [ wordt verstrekt Integrerend met Adobe Analytics ](/help/sites-administering/adobeanalytics.md).*

**Verwijzingen die in dit leerprogramma worden gebruikt:**

[ 0 ] [ https://experienceleague.adobe.com/docs/media-analytics/using/media-overview.html](https://experienceleague.adobe.com/docs/media-analytics/using/media-overview.html)
