---
title: Interactieve communicatie configuratieeigenschappen
seo-title: Eigenschappen van interactieve communicatieconfiguratie
description: Standaardconfiguratieeigenschappen voor interactieve communicatie bewerken
seo-description: Standaardconfiguratieeigenschappen voor interactieve communicatie bewerken
uuid: 4030078f-64a3-40bb-9892-49e22a8da561
contentOwner: anujkapo
products: SG_EXPERIENCEMANAGER/6.5/FORMS
content-type: reference
topic-tags: interactive-communications
discoiquuid: acb61d37-cd22-422e-bbf3-a2979b13ad41
docset: aem65
translation-type: tm+mt
source-git-commit: f9389a06f9c2cd720919486765cee76257f272c3

---


# Interactieve communicatie configuratieeigenschappen{#interactive-communications-configuration-properties}

Interactieve communicatie bevat eigenschappen die automatisch worden geconfigureerd nadat het invoegpakket voor [AEM-formulieren is geïnstalleerd](../../forms/using/installing-configuring-aem-forms-osgi.md) . De interactieve auteurs van Communicatie kunnen deze standaardconfiguratieeigenschappen uitgeven gebruikend de pagina van de Configuratie **van de Console van de Console van de** Ervaring van Adobe Manager.

Open de pagina Configuratie webconsole van **Adobe Experience Manager** met de volgende URL:

`https:/[server]:[port]/<contextPath>/system/console/configMgr`

De configuratie-eigenschappen omvatten:

* [Configuratie van documentfragmenten](#document-fragments-configuration)
* [Correspondentenconfiguratie maken](#create-correspondence-configuration)
* [Adaptieve vorm en interactieve communicatie Webkanaalconfiguratie](#adaptive-form-and-interactive-communication-web-channel-configuration)
* [Adaptieve vorm en interactieve communicatie webkanaalthemaconfiguratie](#adaptive-form-and-interactive-communication-web-channel-theme-configuration)

## Configuratie van documentfragmenten {#document-fragments-configuration}

Tik op de **pagina Configuratie** van de webconsole van Adobe Experience Manager op de configuratie **** van documentfragmenten om de configuratie-eigenschappen voor documentfragmenten weer te geven.

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
   <td><p>--</p> </td> 
  </tr> 
  <tr> 
   <td>Inspringing</td> 
   <td>De breedte van één inspringingseenheid die wordt toegepast op tekst in documentfragmenten van de lijst.</td> 
   <td>12.7mm</td> 
   <td>Getal</td> 
  </tr> 
  <tr> 
   <td>Roman Numbers Minimum Width</td> 
   <td>Minimumbreedte die moet worden toegepast op het opsommingsteken of nummerveld bij gebruik van Romeinse nummers in documentfragmenten van de lijst. </td> 
   <td>12.7mm</td> 
   <td>Getal</td> 
  </tr> 
  <tr> 
   <td>Minimumbreedte aantal</td> 
   <td>Minimumbreedte die op het opsommingsteken of nummerveld moet worden toegepast wanneer u genummerde lijsten gebruikt, met uitzondering van Romeinse nummers in documentfragmenten van de lijst.</td> 
   <td>8.0mm</td> 
   <td>Getal</td> 
  </tr> 
 </tbody> 
</table>

## Correspondentenconfiguratie maken {#create-correspondence-configuration}

Tik op Correspondentieconfiguratie **** maken op de pagina Configuratie **** van de webconsole van Adobe Experience Manager om de configuratieeigenschappen voor de gebruikersinterface van de Agent weer te geven.

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
   <td><p>Schakel het selectievakje in om het insluiten van fonts in de PDF-documenten in te schakelen. Nadat u deze optie hebt geselecteerd, kunt u nieuwe fonts insluiten nadat u de PDF-documenten hebt gegenereerd of voorvertoond met de gebruikersinterface van de Agent. Gebruik het kanaal Afdrukken van interactieve communicatie om PDF-documenten te genereren en voor te vertonen.</p> <p>Het insluiten van fonts in een PDF-document is nuttig als een font beschikbaar is op een computer die wordt gebruikt om de PDF te genereren en niet beschikbaar is op de clientcomputer die de PDF opent.</p> <p>Zie <a href="../../forms/using/customize-text-editor.md" target="_blank">Teksteditor</a>aanpassen voor meer informatie over het insluiten van lettertypen.</p> </td> 
   <td>Niet geselecteerd</td> 
   <td>Niet van toepassing</td> 
  </tr> 
 </tbody> 
</table>

## Adaptieve vorm en interactieve communicatie Webkanaalconfiguratie {#adaptive-form-and-interactive-communication-web-channel-configuration}

Tik op de pagina Configuratie **van de webconsole van** **** Adobe Experience Manager op Adaptive Form en Interactive Communication Web Channel om de configuratieeigenschappen voor Adaptive Forms en Interactive Communications Web Channel weer te geven. De volgende lijst beschrijft de eigenschappen met betrekking tot Interactieve Mededelingen:

| Eigenschap | Beschrijving | Standaard | Acceptabele waarden |
|---|---|---|---|
| Tijdelijke aanduiding tonen | Schakel het selectievakje in om de weergave van plaatsaanduidingen in te schakelen voor velden die zijn opgenomen in adaptieve formulieren en interactieve communicatie. | Geselecteerd | Niet van toepassing |
| Maximum aantal cacheitems | Stel het maximumaantal adaptieve formulieren en interactieve communicatie in dat kan worden opgehaald met behulp van het cachegeheugen. | 100 | Getal |
| Bestandsnaam uniek maken | Schakel het selectievakje in als u unieke namen wilt gebruiken voor bestanden die als bijlagen zijn opgenomen in Adaptieve formulieren en interactieve communicatie. | Niet geselecteerd | Niet van toepassing |

## Adaptieve vorm en interactieve communicatie webkanaalthemaconfiguratie {#adaptive-form-and-interactive-communication-web-channel-theme-configuration}

Tik op de pagina Configuratie **van het thema Adaptief formulier en Interactieve communicatie Web Channel op de pagina Configuratie** van de webconsole van de **** Adobe Experience Manager om de configuratieeigenschappen voor Adaptieve formulieren en Interactieve communicatiekanaalthema&#39;s weer te geven.

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
   <td>Lijst met lettertypen die beschikbaar zijn voor gebruik bij het maken van adaptieve formulieren en interactieve communicatie.</td> 
   <td><p>Georgia</p> <p>Boek-antiaqua</p> <p>Times New Roman</p> <p>Arial</p> <p>Arial Black</p> <p>Gevolgen</p> <p>Palatino Linotype</p> </td> 
   <td>Alle geldige Adobe-serverlettertypen</td> 
  </tr> 
 </tbody> 
</table>

