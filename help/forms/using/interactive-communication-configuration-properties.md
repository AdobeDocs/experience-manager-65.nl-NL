---
title: Interactieve communicatie configuratieeigenschappen
description: Standaardconfiguratieeigenschappen voor interactieve communicatie bewerken
contentOwner: anujkapo
products: SG_EXPERIENCEMANAGER/6.5/FORMS
content-type: reference
topic-tags: interactive-communications
docset: aem65
feature: Interactive Communication
exl-id: 09eeade6-e16d-4159-b26a-803c7201097a
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '610'
ht-degree: 0%

---

# Interactieve communicatie configuratieeigenschappen{#interactive-communications-configuration-properties}

De interactieve Mededelingen omvat eigenschappen die automatisch na het installeren van het [&#x200B; toe:voegen-op &#x200B;](../../forms/using/installing-configuring-aem-forms-osgi.md) pakket van AEM Forms worden gevormd. De interactieve auteurs van de Communicatie kunnen deze standaardconfiguratieeigenschappen uitgeven gebruikend de **pagina van de Configuratie van de Console van het Web 0&rbrace; Adobe Experience Manager.**

Open de **pagina van de Configuratie van de Console van het Web van Adobe Experience Manager** gebruikend volgende URL:

`https:/[server]:[port]/<contextPath>/system/console/configMgr`

De configuratie-eigenschappen zijn onder andere:

* [Configuratie van documentfragmenten](#document-fragments-configuration)
* [Correspondentenconfiguratie maken](#create-correspondence-configuration)
* [Adaptieve vorm en interactieve communicatie Webkanaalconfiguratie](#adaptive-form-and-interactive-communication-web-channel-configuration)
* [Adaptieve vorm en interactieve communicatie webkanaalthemaconfiguratie](#adaptive-form-and-interactive-communication-web-channel-theme-configuration)

## Configuratie van documentfragmenten {#document-fragments-configuration}

Selecteer **de configuratie van Fragmenten van het Document** op de **pagina van de Configuratie van de Console van het Web van Adobe Experience Manager** om de configuratieeigenschappen voor documentfragmenten te bekijken.

<table>
 <tbody> 
  <tr> 
   <td>Eigenschap</td> 
   <td>Beschrijving</td> 
   <td>Standaard</td> 
   <td>Acceptabele waarden</td> 
  </tr> 
  <tr> 
   <td>Indelingen voor gegevensweergave</td> 
   <td>Landspecifieke weergave-indeling voor velden, variabelen en formuliergegevensmodelelementen die beschikbaar zijn tijdens het maken van een interactieve communicatie voor afdruk- en webkanalen.</td> 
   <td> 
    <ul> 
     <li>locale = en_US, de_DE, fr_FR en ja_JP</li> 
     <li>dateFormat = dd-MM-yyyy</li> 
     <li>numberDecimalSeparator = .</li> 
     <li>numberGroupSeparator = ,</li> 
     <li>numberUseGroupSeparator = true</li> 
    </ul> </td> 
   <td><p>—</p> </td> 
  </tr> 
  <tr> 
   <td>Inspringing</td> 
   <td>De breedte van één inspringingseenheid die wordt toegepast op tekst in documentfragmenten van de lijst.</td> 
   <td>12,7 mm</td> 
   <td>Getal</td> 
  </tr> 
  <tr> 
   <td>Roman Numbers Minimum Width</td> 
   <td>Minimumbreedte die moet worden toegepast op het opsommingsteken of nummerveld bij gebruik van Romeinse nummers in documentfragmenten van de lijst. </td> 
   <td>12,7 mm</td> 
   <td>Getal</td> 
  </tr> 
  <tr> 
   <td>Minimumbreedte aantal</td> 
   <td>Minimumbreedte die moet worden toegepast op het opsommingsteken of nummerveld bij het gebruik van genummerde lijsten behalve Romeinse nummers in documentfragmenten van de lijst.</td> 
   <td>8,0 mm</td> 
   <td>Getal</td> 
  </tr> 
 </tbody> 
</table>

## Correspondentenconfiguratie maken {#create-correspondence-configuration}

Selecteer **creëren de Configuratie van de Correspondentie** op de **pagina van de Configuratie van de Console van Adobe Experience Manager** om de configuratieeigenschappen voor Agent UI te bekijken.

<table>
 <tbody> 
  <tr> 
   <td>Eigenschap</td> 
   <td>Beschrijving</td> 
   <td>Standaard</td> 
   <td>Acceptabele waarden</td> 
  </tr> 
  <tr> 
   <td>Opgeloste inhoud tonen voor bewerking</td> 
   <td>Schakel het selectievakje in om de gevonden inhoud (werkelijke waarden in plaats van plaatsaanduidingen) weer te geven tijdens het bewerken van de tekstmodule in de gebruikersinterface van de agent.</td> 
   <td>Niet geselecteerd</td> 
   <td>Niet van toepassing</td> 
  </tr> 
  <tr> 
   <td>Watermerk toepassen tijdens voorvertoning</td> 
   <td>Schakel het selectievakje in om watermerk toe te passen op het kanaal voor interactieve communicatie afdrukken in de modus Voorbeeld.</td> 
   <td>Niet geselecteerd</td> 
   <td>Niet van toepassing</td> 
  </tr> 
  <tr> 
   <td>Lettertype insluiten in PDF inschakelen</td> 
   <td><p>Schakel het selectievakje in om het insluiten van lettertypen in de PDF-documenten in te schakelen. Nadat u deze optie hebt geselecteerd, kunt u nieuwe lettertypen insluiten nadat u de PDF-documenten hebt gegenereerd of een voorvertoning ervan hebt weergegeven met de gebruikersinterface van de Agent. Gebruik het kanaal van de Druk van Interactieve Communicatie om PDF documenten te produceren en voor te proef.</p> <p>Het insluiten van lettertypen in een PDF-document is handig als een lettertype beschikbaar is op een computer die wordt gebruikt om de PDF te genereren en die niet beschikbaar is op de clientcomputer die de PDF benadert.</p> <p>Voor meer informatie bij het inbedden van doopvonten, zie <a href="../../forms/using/customize-text-editor.md" target="_blank"> de tekstredacteur </a> aanpassen.</p> </td> 
   <td>Niet geselecteerd</td> 
   <td>Niet van toepassing</td> 
  </tr> 
 </tbody> 
</table>

## Adaptieve vorm en interactieve communicatie Webkanaalconfiguratie {#adaptive-form-and-interactive-communication-web-channel-configuration}

Selecteer **de AanpassingsVorm en Interactieve Configuratie van het Kanaal van de Communicatie van het Web** de pagina van de Configuratie van de Console van Adobe Experience Manager **om de configuratieeigenschappen voor het AanpassingsForms en Interactieve Communicatie kanaal van het Web te bekijken.** De volgende lijst beschrijft de eigenschappen met betrekking tot Interactieve Mededelingen:

| Eigenschap | Beschrijving | Standaard | Acceptabele waarden |
|---|---|---|---|
| Tijdelijke aanduiding tonen | Schakel het selectievakje in om de weergave van plaatsaanduidingen in te schakelen voor velden die zijn opgenomen in adaptieve formulieren en interactieve communicatie. | Geselecteerd | Niet van toepassing |
| Maximum aantal cacheitems | Stel het maximumaantal adaptieve formulieren en interactieve communicatie in dat kan worden opgehaald met het cachegeheugen. | 100 | Getal |
| Bestandsnaam uniek maken | Schakel het selectievakje in om unieke namen te hebben voor bestanden die als bijlagen zijn opgenomen in Adaptieve Forms en Interactieve communicatie. | Niet geselecteerd | Niet van toepassing |

## Adaptieve vorm en interactieve communicatie webkanaalthemaconfiguratie {#adaptive-form-and-interactive-communication-web-channel-theme-configuration}

Selecteer **de Adaptieve Configuratie van het Thema van de Vorm en Interactieve Communicatie van het Web van het Kanaal van de Vorm** &lbrace;op de **pagina van de Configuratie van de Console van Adobe Experience Manager** om de configuratieeigenschappen voor Adaptieve Forms en Interactieve Communicatie de kanaalthema&#39;s van het Web te bekijken.

<table>
 <tbody> 
  <tr> 
   <td>Eigenschap</td> 
   <td>Beschrijving</td> 
   <td>Standaard</td> 
   <td>Acceptabele waarden</td> 
  </tr> 
  <tr> 
   <td>Naam lettertypenlijst</td> 
   <td>Lijst met lettertypen die beschikbaar zijn voor gebruik tijdens het maken van Adaptieve Forms en Interactieve communicatie.</td> 
   <td><p>Georgia</p> <p>Boek-antiaqua</p> <p>Times New Roman</p> <p>Arial</p> <p>Arial Black</p> <p>Gevolgen</p> <p>Palatino Linotype</p> </td> 
   <td>Alle geldige serverlettertypen voor Adobe</td> 
  </tr> 
 </tbody> 
</table>
