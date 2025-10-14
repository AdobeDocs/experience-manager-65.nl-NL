---
title: Logboek inschakelen voor HTML5-formulieren
description: Met het hulpprogramma Logger kunt u zich aanmelden voor een formulier en kunt u fouten in formuliergerelateerde problemen opsporen.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
docset: aem65
feature: HTML5 Forms,Mobile Forms
exl-id: 2f574c98-550c-4b84-be1e-46a2700e7277
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '629'
ht-degree: 3%

---

# Logboek inschakelen voor HTML5-formulieren{#enable-logging-for-html-forms}

U kunt het hulpprogramma Logger configureren om logbestanden voor HTML5-formulieren te maken. Het loggerhulpprogramma heeft verschillende niveaus en u kunt een niveau instellen op basis van uw vereisten. HTML5-formulieren hebben server- en clientcomponenten. U kunt logboeken voor beide componenten vormen.

## Logboekregistratie op de server configureren {#configuring-server-side-logging}

Voer de volgende stappen uit om logbestanden aan de serverzijde te configureren:

1. Ga naar `https://'[server]:[port]'/system/console/configMgr` . Bepaal en open de *van de het Registreren registrerenconfiguratie van de PlaatsING van de Plaatsing de 1&rbrace; optie.* Er wordt een dialoogvenster weergegeven:

   ![&#x200B; Het dialoogvenster voor de configuratieoptie van het logbestand voor spellingcontrole van Apace &#x200B;](assets/logconfig.png)

   Configuratieoptie Apace Sling-logboekregistratie

1. Verander het **Niveau van het Logboek** aan **zuivert**.

1. Specificeer naam en weg van het **Dossier van het Logboek**.

   >[!NOTE]
   >
   >Als u logbestanden wilt genereren in de logmap met HTML5-formulieren, voegt u ../logs/ toe vóór de bestandsnaam.

1. Verandering **Logger** aan **HTMLFormsPerfLogger**. Klik **sparen**.

## Logboekregistratie van clients configureren {#configuring-client-logging}

U kunt de volgende methoden gebruiken om aanmelding op de client in HTML5-formulieren in te schakelen:

* De parameter request met de naam `log` gebruiken
* CQ-configuratiebeheer gebruiken

### Registreren met behulp van aanvraagparameter inschakelen {#enabling-logging-using-request-parameter}

Met deze methode kunt u logboeken voor een bepaalde aanvraag genereren. De naam van de parameter request is `log` . Het logbestand-URL ziet er als volgt uit:

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
   <td>De logboeken worden geleid aan browser <strong> Console </strong></td>
  </tr>
  <tr>
   <td>2</td>
   <td>De logboeken worden verzameld in een voorwerp van JavaScript op cliëntkant en kunnen aan <strong> Server </strong> worden gepost </td>
  </tr>
  <tr>
   <td>3</td>
   <td>Beide van bovengenoemde opties <br /> </td>
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
   <td>UIT <br type="_moz" /> </td>
  </tr>
  <tr>
   <td>1</td>
   <td>FATAL <br type="_moz" /> </td>
  </tr>
  <tr>
   <td>2</td>
   <td>FOUT <br type="_moz" /> </td>
  </tr>
  <tr>
   <td>3</td>
   <td>WAARSCHUWING <br type="_moz" /> </td>
  </tr>
  <tr>
   <td>4</td>
   <td>INFO <br type="_moz" /> </td>
  </tr>
  <tr>
   <td>5</td>
   <td>FOUTOPSPORING <br type="_moz" /> </td>
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

#### Gebruikerscategorieën {#logger-categories}

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
   <td>xfaView (aan de motor van de Lay-out verwante logboeken) <br type="_moz" /> </td>
  </tr>
  <tr>
   <td>c</td>
   <td>xfaPerf (Prestatiegerelateerde logboeken) <br type="_moz" /> </td>
  </tr>
 </tbody>
</table>

#### Logboekconfiguratie {#log-configuration}

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
   <td>Doel: Server <br /> xfa-niveau: INFO <br /> xfaView-niveau: DEBUG <br /> xfaPerf-niveau: TRACE</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Het standaardlogniveau voor elke logcategorie a (xfa), b (xfaView), en c (xfaPerf) is 2 (ERROR). Voor logconfiguratie 2-b6 zijn de logniveaus voor de verschillende categorieën dienovereenkomstig:
>a (xfa): 2 (standaardniveauFOUT)
>b (xfaView): 6 (door gebruiker opgegeven TRACE)
>a (xfaPerf): 2 (standaardniveauFOUT)

### Registreren inschakelen met Configuratiebeheer {#enabling-logging-using-configuration-manager}

Als u de Manager van de Configuratie voor het toelaten van registreren gebruikt, worden de logboeken geproduceerd voor elk teruggeven verzoek tot het registreren opnieuw onbruikbaar wordt gemaakt.

1. Meld u aan bij CQ Configuration Manager op `https://'[server]:[port]'/system/console/configMgr` en meld u aan met de beheerdersreferenties.
1. Zoek naar en klik **Mobiele Configuraties van Forms**.
1. In het Debug de tekstvakje van Opties, ga de logboekconfiguraties in zoals die in de vorige sectie bijvoorbeeld worden beschreven, **2-a4-b5-c6**

   ![&#x200B; Configuratie van Forms &#x200B;](assets/forms_configuration.png)

   Forms-configuratie

## Logbestanden uploaden {#uploading-logs}

Als de bestemming als 1 wordt geplaatst, worden alle berichten van het cliëntmanuscript logboek geleid aan de console. Als een beheerder deze logboeken samen met serverlogboeken vereist, plaats bestemmingsniveau aan 2. Op dit niveau, worden alle logboeken verzameld in een voorwerp JS op cliëntkant en als de vorm met standaardProfiel toen a **wordt teruggegeven verzendt Logs** knoop verschijnt links van **Hoogtepunt Bestaande Gebieden** knoop in toolbar. Wanneer de gebruiker op de koppeling klikt, worden alle verzamelde logbestanden naar de server gepost en aangemeld bij het geconfigureerde foutenlogbestand op de server.

Standaard wordt alle informatie toegevoegd aan het bestand error.log in de map /crx-repository/logs/.

De locatie en naam van het logbestand wijzigen:

1. Meld u aan bij Configuratiebeheer als beheerder. De standaard-URL van Configuration Manager is `https://'[server]:[port]'/system/console/configMgr` .
1. Klik **Apache Sling Logging Logger Configuratie van het Logboek**. Er wordt een dialoogvenster weergegeven.

   ![&#x200B; logconfig-1 &#x200B;](assets/logconfig-1.png)

1. Verander het **Niveau van het Logboek** om te zuiveren.

1. Specificeer weg en naam van het **Dossier van het Logboek**.

   >[!NOTE]
   >
   >Als u logbestanden wilt maken in dezelfde map waarin andere logbestanden worden opgeslagen, geeft u ../logs/&lt;bestandsnaam> op in de eigenschap Logbestanden.

1. Verander **Logger** aan **HTMLFormsPerfLogger** en klik **sparen**.
