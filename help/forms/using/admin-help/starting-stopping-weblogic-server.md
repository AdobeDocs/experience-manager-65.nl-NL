---
title: WebLogic Server starten en stoppen
seo-title: WebLogic Server starten en stoppen
description: Bij verschillende procedures moet u de instantie van WebLogic Server starten of stoppen waar u AEM-formuliermodules wilt implementeren. In dit document wordt beschreven hoe u de WebLogic-server start en stopt.
seo-description: Bij verschillende procedures moet u de instantie van WebLogic Server starten of stoppen waar u AEM-formuliermodules wilt implementeren. In dit document wordt beschreven hoe u de WebLogic-server start en stopt.
uuid: 957787fe-4cea-4ecd-b49a-c33023c5c309
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_application_server
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: c908d064-6596-473a-b218-22a2496c83f7
translation-type: tm+mt
source-git-commit: 317fadfe48724270e59644d2ed9a90fbee95cf9f

---


# WebLogic Server starten en stoppen {#starting-and-stopping-weblogic-server}

Bij verschillende procedures moet u de instantie van WebLogic Server starten of stoppen waar u AEM-formuliermodules wilt implementeren. Zorg ervoor dat WebLogic Server wordt gestopt of uitgevoerd, afhankelijk van de taak die u uitvoert.

<table>
 <thead>
  <tr>
   <th><p>Activiteit</p></th>
   <th><p>Vereiste WebLogic-status</p></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p>Een WebLogic-domein maken</p></td>
   <td><p>Gestopt</p></td>
  </tr>
  <tr>
   <td><p>Een WebLogic-beheerde server maken</p></td>
   <td><p>Wordt uitgevoerd</p></td>
  </tr>
  <tr>
   <td><p>Het aantal serververbindingen verhogen</p></td>
   <td><p>Wordt uitgevoerd</p></td>
  </tr>
  <tr>
   <td><p>AEM-formulierproducten implementeren</p></td>
   <td><p>Wordt uitgevoerd</p></td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Als u WebLogic Server op Red Hat® Enterprise Linux Advanced Server 4.0 uitvoert, stelt u de `LD_ASSUME_KERNEL` omgevingsvariabele in op 2.4.19 met de `export LD_ASSUME_KERNEL=2.4.19` opdracht. Voer vervolgens WebLogic Server uit vanuit dezelfde shell waarin u deze omgevingsvariabele instelt.

## WebLogic-server starten {#start-weblogic-server}

1. Van een bevelherinnering, ga naar *[toepassingswortel]*/user_projects/domeinen/*[appserverdomain]*.
1. Voer de volgende opdracht in:

   * (Windows) `startWebLogic.cmd`
   * (Linux, UNIX) ./ `startWebLogic.sh`

## WebLogic-server stoppen {#stop-weblogic-server}

1. Start de WebLogic Server-beheerconsole door `https://[host name]:7001/console` in de URL-regel van een webbrowser te typen.
1. Meld u aan door de gebruikersnaam en het wachtwoord te typen die u hebt gebruikt bij het maken van deze WebLogic-configuratie en klik vervolgens op Aanmelden.
1. Klik onder Midden wijzigen op Vergrendelen en bewerken.
1. Klik onder Domeinstructuur op Omgeving > Servers.
1. Klik op AdminServer en klik in het deelvenster Instellingen voor AdminServer op het tabblad Beheer.
1. Controleer of AdminServer is geselecteerd in de tabel Serverstatus en klik op Uitschakelen.
1. Selecteer Wanneer het Werk voltooit om de server zachtjes te sluiten of de uitgezochte Sluiting van de Kracht nu om de server onmiddellijk tegen te houden zonder aan de gang zijnde taken te voltooien.
1. Klik in het venster Server Life Cycle Assistant op Ja om het afsluiten te voltooien.

De WebLogic Server-beheerconsole is niet meer beschikbaar en de opdrachtprompt waarmee u de start-opdracht hebt uitgevoerd, is beschikbaar.

## WebLogic-beheerconsole starten {#start-weblogic-administration-console}

1. Als WebLogic Admin Server nog niet actief is, gaat u vanaf een opdrachtprompt naar de hoofdmap *[\user_projects\domains\[]domeinnaam]*van de toepassingsserver en voert u de volgende opdracht in:

   * (Windows) `startWebLogic.cmd`
   * (Linux, UNIX) ./ `startWebLogic.sh`

1. Toegang tot de WebLogic Server-beheerconsole door `https://[host name]:[port]/console` in de URL-regel van een webbrowser te typen, waar de *[poort]* de niet-beveiligde luisterpoort is. Deze poortwaarde is standaard 7001.
1. Typ in het aanmeldingsscherm uw gebruikersnaam en wachtwoord voor de beheerder en klik op Aanmelden.

## Notitiebeheer starten {#start-node-manager}

1. Zorg ervoor dat WebLogic Server wordt uitgevoerd.
1. Van een nieuwe bevelherinnering, ga naar *[toepassingswortel]*/server/bak.
1. Voer de volgende opdracht in:

   * (Windows) `startNodeManager.cmd`
   * (Linux, UNIX) `./startNodeManager.sh`

## Knooppuntbeheer stoppen {#stop-node-manager}

Nadat u WebLogic Server sluit, kunt u de bevelherinnering sluiten waarvan u de Manager van de Knoop riep.

## Een door WebLogic beheerde server starten {#start-a-weblogic-managed-server}

>[!NOTE]
>
>Deze taak kan alleen worden uitgevoerd nadat u een WebLogic-domein en een beheerde server hebt gemaakt.

1. Zorg ervoor dat WebLogic Server en Node Manager lopen.
1. Start WebLogic Server Administration Console door in de URL-regel van een webbrowser `https://host name]:[port]`een console te typen.
1. Klik onder Domeinstructuur op Omgeving > Servers.
1. Klik in het rechterdeelvenster op het tabblad Beheer.
1. Selecteer de beheerde server die u wilt starten.
1. Klik op de knop Start onder de beheerde server die u wilt starten.

## Een door WebLogic beheerde server stoppen {#stop-a-weblogic-managed-server}

1. Start WebLogic Server Administration Console door `https://`*[hostnaam]te typen:[poort ]*`/console`in de URL-regel van een webbrowser.
1. Klik onder Domeinstructuur op Omgeving > Servers.
1. Klik in het rechterdeelvenster op het tabblad Beheer.
1. Selecteer de beheerde server die u wilt stoppen.
1. Klik op de knop Uitschakelen onder de beheerde server die u wilt stoppen.
1. Selecteer Wanneer het Werk voltooit om de server zachtjes te sluiten of de uitgezochte Sluiting van de Kracht nu om de server onmiddellijk tegen te houden zonder aan de gang zijnde taken te voltooien.
1. Klik in het venster Server Life Cycle Assistant op Ja om het afsluiten te voltooien.

