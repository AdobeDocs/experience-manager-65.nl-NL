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
translation-type: tm+mt
source-git-commit: 317fadfe48724270e59644d2ed9a90fbee95cf9f

---


# Logbestand voor HTML5-formulieren inschakelen{#enable-logging-for-html-forms}

U kunt het hulpprogramma Logger configureren om logboeken te maken voor HTML5-formulieren. Het loggerhulpprogramma heeft verschillende niveaus en u kunt een niveau instellen op basis van uw vereisten. HTML5-formulieren bevatten server- en clientcomponenten. U kunt logboeken voor beide componenten vormen.

## Logboekregistratie op de server configureren {#configuring-server-side-logging}

Voer de volgende stappen uit om logbestanden aan de serverzijde te configureren:

1. Ga naar `https://'[server]:[port]'/system/console/configMgr`. Zoek en open de configuratieoptie *Apace Sling-logboeklogger* . Er wordt een dialoogvenster weergegeven:

   ![ Het dialoogvenster voor het instellen van de optie Apace Sling-logboekregistratie](assets/logconfig.png)

   Configuratieoptie Apace Sling-logboekregistratie

1. Wijzig het **logniveau** in **Foutopsporing**.

1. Geef de naam en het pad van het **logbestand** op.

   >[!NOTE]
   >
   >Als u logbestanden wilt genereren in de logmap met HTML5-formulieren, voegt u ../logs/ toe vóór de bestandsnaam.

1. Wijzig **Logger** in **HTMLFormsPerfLogger**. Click **Save**.

## Logboekregistratie van clients configureren {#configuring-client-logging}

U kunt de volgende methoden gebruiken om aanmelding op de client in HTML5-formulieren in te schakelen:

* De genoemde parameter request gebruiken `log`
* CQ-configuratiebeheer gebruiken

### Registreren met behulp van aanvraagparameter inschakelen {#enabling-logging-using-request-parameter}

Met deze methode kunt u logboeken voor een bepaalde aanvraag genereren. De naam van de verzoekparameter is ` logboek. Het logbestand-URL ziet er als volgt uit:

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
   <td>Logboeken worden naar de <strong>browserconsole gestuurd</strong></td>
  </tr>
  <tr>
   <td>2</td>
   <td>Logbestanden worden verzameld in een JavaScript-object op de client en kunnen naar de <strong>server worden gepost</strong> </td>
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
   <td>FATAAL<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>2</td>
   <td>ERROR<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>3</td>
   <td>WAARSCHUWING<br type="_moz" /> </td>
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
   <td>xfaView (logbestanden met betrekking tot de layout-engine)<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>c</td>
   <td>xfaPerf (prestatiegerelateerde logs)<br type="_moz" /> </td>
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
   <td>Doel: XFA-niveau server<br /> : INFO<br /> xfaView-niveau: DEBUG<br /> xfaPerf-niveau: TRACE</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Het standaardlogniveau voor elke logcategorie a (xfa), b (xfaView), en c (xfaPerf) is 2 (ERROR). Dienovereenkomstig, voor logboekconfiguratie: 2-b6, de logboekniveaus voor verschillende categorieën zijn:
>a (xfa): 2 (FOUT OP standaardniveau)
>b (xfaView): 6 (door de gebruiker opgegeven TRACE)
>a (xfaPerf): 2 (FOUT OP standaardniveau)

### Registreren inschakelen met Configuratiebeheer {#enabling-logging-using-configuration-manager}

Als u de Manager van de Configuratie voor het toelaten van registreren gebruikt, worden de logboeken geproduceerd voor elk teruggeven verzoek tot het registreren opnieuw onbruikbaar wordt gemaakt.

1. Meld u aan bij CQ Configuration Manager op `https://'[server]:[port]'/system/console/configMgr` en meld u aan met de beheerdersreferenties.
1. Zoek naar en klik op Configuraties van **mobiele formulieren**.
1. Voer in het tekstvak Opties voor foutopsporing de logboekconfiguraties in zoals in de vorige sectie, bijvoorbeeld **2-a4-b5-c6**

   ![Formulierconfiguratie](assets/forms_configuration.png)

   Formulierconfiguratie

## Logbestanden uploaden {#uploading-logs}

Als de bestemming als 1 wordt geplaatst, worden alle berichten van het cliëntmanuscript logboek geleid aan de console. Als een beheerder deze logboeken samen met serverlogboeken vereist, plaats bestemmingsniveau aan 2. Op dit niveau worden alle logbestanden verzameld in een JS-object op de client. Als het formulier wordt weergegeven met het standaardprofiel, wordt er een knop Logboeken **** verzenden weergegeven links van de knop Bestaande velden **** markeren op de werkbalk. Wanneer de gebruiker op de koppeling klikt, worden alle verzamelde logbestanden naar de server gepost en aangemeld bij het geconfigureerde foutenlogbestand op de server.

Standaard wordt alle informatie toegevoegd aan het bestand error.log in de map /crx-repository/logs/.

De locatie en naam van het logbestand wijzigen:

1. Meld u aan bij Configuratiebeheer als beheerder. De standaard-URL van Configuration Manager is `https://'[server]:[port]'/system/console/configMgr`.
1. Klik op **Apache Sling Logging Logger Configuration**. Er wordt een dialoogvenster weergegeven.

   ![logconfig-1](assets/logconfig-1.png)

1. Wijzig het **logniveau** in Foutopsporing.

1. Geef het pad en de naam van het **logbestand** op.

   >[!NOTE]
   >
   >Als u logbestanden wilt maken in dezelfde map waarin andere logbestanden worden opgeslagen, geeft u ../logs/&lt;bestandsnaam> op in de eigenschap Logbestanden.

1. Wijzig de **Logger** in **HTMLFormsPerfLogger** en klik op **Opslaan**.

[Contact opnemen met ondersteuning](https://www.adobe.com/account/sign-in.supportportal.html)
