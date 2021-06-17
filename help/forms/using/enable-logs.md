---
title: Logbestand voor HTML5-formulieren inschakelen
seo-title: Logbestand voor HTML5-formulieren inschakelen
description: Met het hulpprogramma Logger kunt u zich aanmelden voor een formulier en kunt u fouten in formuliergerelateerde problemen opsporen.
seo-description: Met het hulpprogramma Logger kunt u zich aanmelden voor een formulier en kunt u fouten in formuliergerelateerde problemen opsporen.
uuid: 322306ba-8ad7-463d-8a9d-4cea5a0c4b55
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
discoiquuid: 973806f8-fb44-4d52-ad3f-bfbf335f60a1
docset: aem65
feature: Mobile Forms
exl-id: 2f574c98-550c-4b84-be1e-46a2700e7277
source-git-commit: d1fc2ff44378276522c2ff3208f5b3bdc4484bba
workflow-type: tm+mt
source-wordcount: '647'
ht-degree: 4%

---

# Logbestand inschakelen voor HTML5-formulieren{#enable-logging-for-html-forms}

U kunt het hulpprogramma Logger configureren om logboeken te maken voor HTML5-formulieren. Het loggerhulpprogramma heeft verschillende niveaus en u kunt een niveau instellen op basis van uw vereisten. HTML5-formulieren bevatten server- en clientcomponenten. U kunt logboeken voor beide componenten vormen.

## Logboekregistratie op de server configureren {#configuring-server-side-logging}

Voer de volgende stappen uit om logbestanden aan de serverzijde te configureren:

1. Ga naar `https://'[server]:[port]'/system/console/configMgr`. Zoek en open de *Apace Sling Logger configuration* optie. Er wordt een dialoogvenster weergegeven:

   ![ Het dialoogvenster voor het instellen van de optie Apace Sling-logboekregistratie](assets/logconfig.png)

   Configuratieoptie Apace Sling-logboekregistratie

1. Wijzig **Logniveau** in **Foutopsporing**.

1. Geef de naam en het pad op van het **logbestand**.

   >[!NOTE]
   >
   >Als u logbestanden wilt genereren in de logmap met HTML5-formulieren, voegt u ../logs/ toe vóór de bestandsnaam.

1. Wijzig **Logger** in **HTMLFormsPerfLogger**. Klik **Opslaan**.

## Logboekregistratie van client configureren {#configuring-client-logging}

U kunt de volgende methoden gebruiken om aanmelding op de client in HTML5-formulieren in te schakelen:

* Het gebruiken van de verzoekparameter genoemd `log`
* CQ-configuratiebeheer gebruiken

### Het registreren toelaten gebruikend verzoekparameter {#enabling-logging-using-request-parameter}

Met deze methode kunt u logboeken voor een bepaalde aanvraag genereren. De naam van de parameter request is `log`. Het logbestand-URL ziet er als volgt uit:

`https://<server>:<port>/content/xfaforms/profiles/test.html?contentRoot=<path of the folder containing form xdp>&template=<name of the xdp>&log=<log configuration>.`

De logboekconfiguratie wordt samengesteld uit het logboekniveau en de logboekcategorie.

#### Logbestemming {#log-destination}

<table>
 <tbody>
  <tr>
   <th><strong>Logbestemming</strong></th>
   <th><strong>Beschrijving</strong></th>
  </tr>
  <tr>
   <td>1</td>
   <td>De logboeken worden gericht aan browser <strong>Console</strong></td>
  </tr>
  <tr>
   <td>2</td>
   <td>Logbestanden worden verzameld in een JavaScript-object op de client en kunnen worden gepost op <strong>Server</strong> </td>
  </tr>
  <tr>
   <td>3</td>
   <td>Beide opties<br /> </td>
  </tr>
 </tbody>
</table>

#### Logboekniveaus {#log-levels}

<table>
 <tbody>
  <tr>
   <th>Logboekniveau</th>
   <th>Beschrijving</th>
  </tr>
  <tr>
   <td>0</td>
   <td>OFF<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>1</td>
   <td>FATAL<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>2</td>
   <td>FOUT<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>3</td>
   <td>WARN<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>4</td>
   <td>INFO<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>5</td>
   <td>DEBUG<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>6</td>
   <td>TRACE<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>7</td>
   <td>ALL<br type="_moz" /> </td>
  </tr>
 </tbody>
</table>

#### Logboekcategorieën {#logger-categories}

<table>
 <tbody>
  <tr>
   <th>Logboekcategorie</th>
   <th>Beschrijving</th>
  </tr>
  <tr>
   <td>a</td>
   <td>xfa (logboeken met scriptengine)</td>
  </tr>
  <tr>
   <td>b</td>
   <td>xfaView (logbestanden met betrekking tot de engine voor lay-out)<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>c</td>
   <td>xfaPerf (prestatiegerelateerde logboeken)<br type="_moz" /> </td>
  </tr>
 </tbody>
</table>

#### Logconfiguratie {#log-configuration}

In het logboek URL, wordt de parameter van het de vraagkoord van de logboekconfiguratie als volgt bepaald:

`{destination}-{a level}-{b level}-{c level}`

Bijvoorbeeld:

<table>
 <tbody>
  <tr>
   <th>Logboekconfiguratie</th>
   <th>Beschrijving</th>
  </tr>
  <tr>
   <td>2-a4-b5-c6<br type="_moz" /> </td>
   <td>Doel: Server<br /> xfa-niveau: INFO<br /> xfaView-niveau: DEBUG<br /> xfaPerf-niveau: TRACE</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Het standaardlogniveau voor elke logcategorie a (xfa), b (xfaView), en c (xfaPerf) is 2 (ERROR). Dienovereenkomstig, voor logboekconfiguratie: 2-b6, de logboekniveaus voor verschillende categorieën zijn:
>a (xfa): 2 (FOUT OP standaardniveau)
>b (xfaView): 6 (door gebruiker opgegeven TRACE)
>a (xfaPerf): 2 (FOUT OP standaardniveau)

### Registreren inschakelen met Configuratiebeheer {#enabling-logging-using-configuration-manager}

Als u de Manager van de Configuratie voor het toelaten van registreren gebruikt, worden de logboeken geproduceerd voor elk teruggeven verzoek tot het registreren opnieuw onbruikbaar wordt gemaakt.

1. Meld u aan bij CQ Configuration Manager op `https://'[server]:[port]'/system/console/configMgr` en meld u aan met beheerdersreferenties.
1. Zoek naar en klik **Mobiele Configuraties van Forms**.
1. Voer in het tekstvak Opties voor foutopsporing de logconfiguraties in zoals in de vorige sectie, bijvoorbeeld **2-a4-b5-c6**

   ![Forms-configuratie](assets/forms_configuration.png)

   Forms-configuratie

## Logbestanden {#uploading-logs} uploaden

Als de bestemming als 1 wordt geplaatst, worden alle berichten van het cliëntmanuscript logboek geleid aan de console. Als een beheerder deze logboeken samen met serverlogboeken vereist, plaats bestemmingsniveau aan 2. Op dit niveau worden alle logbestanden verzameld in een JS-object op de client en als het formulier wordt weergegeven met het standaardprofiel, wordt de knop **Logs verzenden** links van de knop **Bestaande velden markeren** op de werkbalk weergegeven. Wanneer de gebruiker op de koppeling klikt, worden alle verzamelde logbestanden naar de server gepost en aangemeld bij het geconfigureerde foutenlogbestand op de server.

Standaard wordt alle informatie toegevoegd aan het bestand error.log in de map /crx-repository/logs/.

De locatie en naam van het logbestand wijzigen:

1. Meld u aan bij Configuratiebeheer als beheerder. De standaard URL van de Manager van de Configuratie is `https://'[server]:[port]'/system/console/configMgr`.
1. Klik **Configuratie van Apache Sling Logging Logger**. Er wordt een dialoogvenster weergegeven.

   ![logconfig-1](assets/logconfig-1.png)

1. Wijzig **Logniveau** in Foutopsporing.

1. Geef het pad en de naam op van het **logbestand**.

   >[!NOTE]
   >
   >Als u logbestanden wilt maken in dezelfde map waarin andere logbestanden worden opgeslagen, geeft u ../logs/&lt;bestandsnaam> op in de eigenschap Logbestanden.

1. Wijzig de **Logger** in **HTMLFormsPerfLogger** en klik **Save**.
