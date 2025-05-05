---
title: Start en stop van opdrachtregel
description: Leer hoe u Adobe Experience Manager start en stopt vanaf de opdrachtregel.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: deploying
exl-id: 21041b55-240c-487d-9d79-c54c877f4e1e
solution: Experience Manager, Experience Manager Sites
feature: Administering
role: Admin
source-git-commit: 48d12388d4707e61117116ca7eb533cea8c7ef34
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---

# Start en stop van opdrachtregel{#command-line-start-and-stop}

## Adobe Experience Manager starten vanaf de opdrachtregel {#starting-adobe-experience-manager-from-the-command-line}

Het `start` manuscript is beschikbaar onder *&lt;cq-installation>/bin* folder. Zowel UNIX® als de versies van Vensters worden verstrekt. Het manuscript begint de instantie die in *wordt geïnstalleerd &lt;cq-installation>* folder.

Deze twee versies ondersteunen een lijst met omgevingsvariabelen die kunnen worden gebruikt om de instantie Adobe Experience Manager (AEM) te starten en af te stemmen.

<table>
 <tbody>
  <tr>
   <td><strong>Omgevingsvariabele </strong></td>
   <td><strong>Beschrijving </strong></td>
  </tr>
  <tr>
   <td>CQ_PORT</td>
   <td>De haven van TCP die voor stop en statusmanuscripten wordt gebruikt <br /> </td>
  </tr>
  <tr>
   <td>CQ_HOST</td>
   <td>Hostnaam <br /> </td>
  </tr>
  <tr>
   <td>CQ_INTERFACE</td>
   <td>Interface die deze server aan <br /> zou moeten luisteren </td>
  </tr>
  <tr>
   <td>CQ_RUNMODE</td>
   <td>De wijzen van de looppas die door komma <br /> worden gescheiden </td>
  </tr>
  <tr>
   <td>CQ_JARFILE</td>
   <td>Naam van het jarfile <br /> </td>
  </tr>
  <tr>
   <td>CQ_USE_JAAS</td>
   <td>Gebruik van JAAS (als waar) <br /> </td>
  </tr>
  <tr>
   <td>CQ_JAAS_CONFIG</td>
   <td>Pad van de JAAS-configuratie <br /> </td>
  </tr>
  <tr>
   <td>CQ_JVM_OPTS</td>
   <td>Standaard JVM-opties <br /> </td>
  </tr>
 </tbody>
</table>

>[!CAUTION]
>
>Sommige uitvoeringsmodi, waaronder auteur en publicatie, moeten worden ingesteld voordat de AEM voor het eerst wordt gestart en kunnen daarna niet worden gewijzigd. Alvorens vestiging een AEM instantie te vestigen die in productie wordt gebruikt, zie [ looppas wijzedocumentatie ](/help/sites-deploying/configure-runmodes.md) voor details.

### Windows-platform start.bat-scriptvoorbeeld {#windows-platform-start-bat-script-example}

```shell
SET CQ_PORT=1234 & ./start.bat
```

### UNIX® platform start script voorbeeld {#unix-platform-start-script-example}

```shell
CQ_PORT=1234 ./start
```

>[!NOTE]
>
>Het beginmanuscript lanceert de AEM QuickStart die onder *wordt geïnstalleerd &lt;cq-installation>/app* omslag.

## Adobe Experience Manager stoppen {#stopping-adobe-experience-manager}

Voer een van de volgende handelingen uit om AEM te stoppen:

* Afhankelijk van het platform dat u gebruikt:

   * Als u AEM van of een manuscript of de bevellijn begon, druk **Ctrl+C** om de server te sluiten.
   * Als u het beginmanuscript op UNIX® hebt gebruikt, moet u het stopmanuscript gebruiken om AEM tegen te houden.

* Als u AEM door het jar dossier tweemaal te klikken begon, klik **&#x200B;**&#x200B;knoop op het startvenster (de knoop verandert dan in **weg**) om de server te sluiten.

  ![ chlimage_1-63 ](assets/chlimage_1-63.png)

## Adobe Experience Manager stoppen vanaf de opdrachtregel {#stopping-adobe-experience-manager-from-the-command-line}

Het `stop` manuscript is beschikbaar onder *&lt;cq-installation>/bin* folder. Zowel UNIX® als de versies van Vensters worden verstrekt. Het manuscript houdt de lopende die instantie tegen in *wordt geïnstalleerd &lt;cq-installation>* folder.

### Voorbeeld van UNIX®-platformstop {#unix-platform-stop-script-example}

```shell
./stop
```

### Windows-platform stop.bat-scriptvoorbeeld {#windows-platform-stop-bat-script-example}

```shell
./stop.bat
```

Als u de repository alleen vooraf wilt configureren (zonder deze te verplaatsen), hoeft u alleen:

* `repository.xml` extraheren naar de gewenste locatie

* update `repository.xml` naar wens uitvoeren

* maken `bootstrap.properties` en definiëren `repository.config`

Opnieuw, alvorens de daadwerkelijke installatie te beginnen.
