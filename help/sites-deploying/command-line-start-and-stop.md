---
title: Start en stop opdrachtregel
seo-title: Command Line Start and Stop
description: Leer om AEM van de bevellijn te beginnen en tegen te houden.
seo-description: Learn how to start and stop AEM from the command line.
uuid: 585f071c-2286-4a2c-af07-404bf298cba8
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: deploying
discoiquuid: 9333ff84-f624-4cfa-a9e4-c5e3882171ff
exl-id: 21041b55-240c-487d-9d79-c54c877f4e1e
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# Start en stop opdrachtregel{#command-line-start-and-stop}

## Adobe Experience Manager starten vanaf de opdrachtregel {#starting-adobe-experience-manager-from-the-command-line}

De `start` script is beschikbaar onder *de &lt;cq-installation>/bin* directory. Zowel Unix als de versies van Vensters worden verstrekt. Het script start de instantie die in *&lt;cq-installation>* directory.

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
   <td>Interface waarnaar deze server moet luisteren<br /> </td>
  </tr>
  <tr>
   <td>CQ_RUNMODE</td>
   <td>Runmode(s) gescheiden door komma<br /> </td>
  </tr>
  <tr>
   <td>CQ_JARFILE</td>
   <td>Naam van het taalbestand<br /> </td>
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
>Houd er rekening mee dat bepaalde uitvoermodi, waaronder auteur en publicatie, moeten worden ingesteld voordat de AEM voor het eerst wordt gestart en dat deze naderhand niet kunnen worden gewijzigd. Voordat u een AEM-instantie instelt die in de productie moet worden gebruikt, raadpleegt u de [documentatie bij uitvoermodi](/help/sites-deploying/configure-runmodes.md) voor meer informatie.

### Windows-platform start.bat-scriptvoorbeeld {#windows-platform-start-bat-script-example}

```shell
SET CQ_PORT=1234 & ./start.bat
```

### Startscriptvoorbeeld van Unix-platform {#unix-platform-start-script-example}

```shell
CQ_PORT=1234 ./start
```

>[!NOTE]
>
>Het beginscript start de AEM QuickStart die onder *de &lt;cq-installation>/app* map.

## Adobe Experience Manager stoppen {#stopping-adobe-experience-manager}

Voer een van de volgende handelingen uit om AEM te stoppen:

* Afhankelijk van het platform dat u gebruikt:

   * Als u AEM bent begonnen via een script of de opdrachtregel, drukt u op **Ctrl+C** om de server uit te schakelen.
   * Als u het beginmanuscript op UNIX hebt gebruikt, moet u het stopmanuscript gebruiken om AEM tegen te houden.

* Als u AEM bent begonnen door te dubbelklikken op het jar-bestand, klikt u op de knop **Aan** knop in het opstartvenster (de knop verandert in **Uit**) om de server uit te schakelen.

   ![chlimage_1-63](assets/chlimage_1-63.png)

## Adobe Experience Manager stoppen vanaf de opdrachtregel {#stopping-adobe-experience-manager-from-the-command-line}

De `stop` script is beschikbaar onder *de &lt;cq-installation>/bin* directory. Zowel Unix als de versies van Vensters worden verstrekt. Het script stopt de actieve instantie die is geïnstalleerd in *&lt;cq-installation>* directory.

### Unix platform stop script voorbeeld {#unix-platform-stop-script-example}

```shell
./stop
```

### Windows-platform stop.bat-scriptvoorbeeld {#windows-platform-stop-bat-script-example}

```shell
./stop.bat
```

Als u enkel de bewaarplaats wilt vooraf vormen (zonder het te verplaatsen) moet u slechts:

* extract `repository.xml` naar de vereiste locatie

* update `repository.xml` vereist

* maken `bootstrap.properties` en definiëren `repository.config`

Opnieuw, alvorens de daadwerkelijke installatie te beginnen.
