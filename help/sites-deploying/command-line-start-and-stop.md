---
title: Start en stop opdrachtregel
seo-title: Start en stop opdrachtregel
description: Leer om AEM van de bevellijn te beginnen en tegen te houden.
seo-description: Leer om AEM van de bevellijn te beginnen en tegen te houden.
uuid: 585f071c-2286-4a2c-af07-404bf298cba8
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: deploying
discoiquuid: 9333ff84-f624-4cfa-a9e4-c5e3882171ff
translation-type: tm+mt
source-git-commit: 3f53945579eaf5de1ed0b071aa9cce30dded89f1
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---


# Start en stop van opdrachtregel{#command-line-start-and-stop}

## Adobe Experience Manager starten vanaf de opdrachtregel {#starting-adobe-experience-manager-from-the-command-line}

Het `start`-script is beschikbaar onder *de map &lt;cq-installation>/bin*. Zowel Unix als de versies van Vensters worden verstrekt. Het manuscript begint de instantie die in *&lt;cq-installation>* folder wordt geïnstalleerd.

Deze twee versies ondersteunen een lijst met omgevingsvariabelen die kunnen worden gebruikt om het AEM te starten en af te stemmen.

<table>
 <tbody>
  <tr>
   <td><strong>Omgevingsvariabele </strong></td>
   <td><strong>Beschrijving </strong></td>
  </tr>
  <tr>
   <td>CQ_PORT</td>
   <td>TCP-poort voor stop- en statusscripts<br /> </td>
  </tr>
  <tr>
   <td>CQ_HOST</td>
   <td>Hostnaam<br /> </td>
  </tr>
  <tr>
   <td>CQ_INTERFACE</td>
   <td>Interface die deze server zou moeten luisteren aan<br /> </td>
  </tr>
  <tr>
   <td>CQ_RUNMODE</td>
   <td>Runmode(s) gescheiden door komma<br /> </td>
  </tr>
  <tr>
   <td>CQ_JARFILE</td>
   <td>Naam van het jarfile<br /> </td>
  </tr>
  <tr>
   <td>CQ_USE_JAAS</td>
   <td>Gebruik van JAAS (indien waar)<br /> </td>
  </tr>
  <tr>
   <td>CQ_JAAS_CONFIG</td>
   <td>Pad van de JAAS-configuratie<br /> </td>
  </tr>
  <tr>
   <td>CQ_JVM_OPTS</td>
   <td>Standaard JVM-opties<br /> </td>
  </tr>
 </tbody>
</table>

>[!CAUTION]
>
>Houd er rekening mee dat bepaalde uitvoermodi, waaronder auteur en publicatie, moeten worden ingesteld voordat de AEM voor het eerst wordt gestart en dat deze naderhand niet kunnen worden gewijzigd. Voordat u een AEM-instantie instelt die in productie moet worden gebruikt, raadpleegt u de [documentatie over de uitvoermodi](/help/sites-deploying/configure-runmodes.md) voor meer informatie.

### Windows-platform start.bat-scriptvoorbeeld {#windows-platform-start-bat-script-example}

```shell
SET CQ_PORT=1234 & ./start.bat
```

### Voorbeeld van Unix platform start script {#unix-platform-start-script-example}

```shell
CQ_PORT=1234 ./start
```

>[!NOTE]
>
>Het beginscript start de AEM QuickStart die onder *de map &lt;cq-installation>/app* is geïnstalleerd.

## Adobe Experience Manager {#stopping-adobe-experience-manager} stoppen

Voer een van de volgende handelingen uit om AEM te stoppen:

* Afhankelijk van het platform dat u gebruikt:

   * Als u AEM bent begonnen via een script of de opdrachtregel, drukt u op **Ctrl+C** om de server af te sluiten.
   * Als u het beginmanuscript op UNIX hebt gebruikt, moet u het stopmanuscript gebruiken om AEM tegen te houden.

* Als u AEM bent begonnen door te dubbelklikken op het jar-bestand, klikt u op de knop **Aan** in het opstartvenster (de knop verandert vervolgens in **Uit**) om de server af te sluiten.

   ![chlimage_1-63](assets/chlimage_1-63.png)

## Adobe Experience Manager stoppen vanaf de opdrachtregel {#stopping-adobe-experience-manager-from-the-command-line}

Het `stop`-script is beschikbaar onder *de map &lt;cq-installation>/bin*. Zowel Unix als de versies van Vensters worden verstrekt. Het script stopt de actieve instantie die is geïnstalleerd in de map *&lt;cq-installation>*.

### Voorbeeld van Unix platform stop script {#unix-platform-stop-script-example}

```shell
./stop
```

### Windows-platform stop.bat-scriptvoorbeeld {#windows-platform-stop-bat-script-example}

```shell
./stop.bat
```

Als u enkel de bewaarplaats wilt vooraf vormen (zonder het te verplaatsen) moet u slechts:

* `repository.xml` uitpakken naar de gewenste locatie

* `repository.xml` naar behoefte bijwerken

* `bootstrap.properties` maken en `repository.config` definiëren

Opnieuw, alvorens de daadwerkelijke installatie te beginnen.

