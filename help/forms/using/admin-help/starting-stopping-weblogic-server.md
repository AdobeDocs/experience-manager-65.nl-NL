---
title: WebLogic Server starten en stoppen
description: Bij verschillende procedures moet u de instantie van WebLogic Server starten of stoppen waar u AEM formuliermodules wilt implementeren. In dit document wordt beschreven hoe u de WebLogic-server start en stopt.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_application_server
products: SG_EXPERIENCEMANAGER/6.5/FORMS
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '603'
ht-degree: 0%

---


# WebLogic Server starten en stoppen {#starting-and-stopping-weblogic-server}

Bij verschillende procedures moet u de instantie van WebLogic Server starten of stoppen waar u AEM formuliermodules wilt implementeren. Zorg ervoor dat WebLogic Server wordt gestopt of uitgevoerd, afhankelijk van de taak die u uitvoert.

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
   <td><p>AEM formulierproducten implementeren</p></td>
   <td><p>Wordt uitgevoerd</p></td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Als u WebLogic Server op Red Hat® Enterprise Linux Advanced Server 4.0 uitvoert, stelt u de `LD_ASSUME_KERNEL` omgevingsvariabele in op 2.4.19 met de opdracht `export LD_ASSUME_KERNEL=2.4.19` . Voer vervolgens WebLogic Server uit vanuit dezelfde shell waarin u deze omgevingsvariabele instelt.

## WebLogic-server starten {#start-weblogic-server}

1. Van een bevelherinnering, ga naar *[appserver wortel]*/user_projects/domains/*[appserverdomain]*.
1. Voer de volgende opdracht in:

   * (Windows) `startWebLogic.cmd`
   * (Linux, UNIX) ./ `startWebLogic.sh`

## WebLogic-server stoppen {#stop-weblogic-server}

1. Start WebLogic Server Administration Console door `https://[host name]:7001/console` in te voeren op de URL-regel van een webbrowser.
1. Meld u aan door de gebruikersnaam en het wachtwoord te typen die u hebt gebruikt bij het maken van deze WebLogic-configuratie en klik vervolgens op Aanmelden.
1. Klik onder Midden wijzigen op Vergrendelen en bewerken.
1. Klik onder Domeinstructuur op Omgeving > Servers.
1. Klik op AdminServer en klik in het deelvenster Instellingen voor AdminServer op het tabblad Beheer.
1. Controleer of AdminServer is geselecteerd in de tabel Serverstatus en klik op Uitschakelen.
1. Selecteer Wanneer het Werk voltooit om de server zachtjes te sluiten of de uitgezochte Sluiting van de Kracht nu om de server onmiddellijk tegen te houden zonder aan de gang zijnde taken te voltooien.
1. Klik in het venster Server Life Cycle Assistant op Ja om het afsluiten te voltooien.

De WebLogic Server-beheerconsole is niet meer beschikbaar en de opdrachtprompt waarmee u de start-opdracht hebt uitgevoerd, is beschikbaar.

## WebLogic-beheerconsole starten {#start-weblogic-administration-console}

1. Als de Server van Admin WebLogic niet reeds loopt, van een bevelherinnering, ga naar de *[toepassingswortel ] \user_projects\domains\ [domeinnaam]* folder, en ga het volgende bevel in:

   * (Windows) `startWebLogic.cmd`
   * (Linux, UNIX) ./ `startWebLogic.sh`

1. De het beleidsconsole van de Server van de toegang WebLogic door `https://[host name]:[port]/console` in de lijn URL van Webbrowser te typen, waar *[haven]* de niet veilige luisterhaven is. Deze poortwaarde is standaard 7001.
1. Typ in het aanmeldingsscherm uw gebruikersnaam en wachtwoord voor de beheerder en klik op Aanmelden.

## Notitiebeheer starten {#start-node-manager}

1. Zorg ervoor dat WebLogic Server wordt uitgevoerd.
1. Van een nieuwe bevelherinnering, ga naar *[appserver wortel]*/server/bin.
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
1. Start WebLogic Server Administration Console door `https://host name]:[port]/console` in te voeren op de URL-regel van een webbrowser.
1. Klik onder Domeinstructuur op Omgeving > Servers.
1. Klik in het rechterdeelvenster op het tabblad Beheer.
1. Selecteer de beheerde server die u wilt starten.
1. Klik op de knop Start onder de beheerde server die u wilt starten.

## Een door WebLogic beheerde server stoppen {#stop-a-weblogic-managed-server}

1. Het beleidsconsole van de Server van het begin WebLogic door `https://`*[ gastheernaam ] te typen:[ haven ]*`/console` in de lijn URL van Webbrowser.
1. Klik onder Domeinstructuur op Omgeving > Servers.
1. Klik in het rechterdeelvenster op het tabblad Beheer.
1. Selecteer de beheerde server die u wilt stoppen.
1. Klik op de knop Uitschakelen onder de beheerde server die u wilt stoppen.
1. Selecteer Wanneer het Werk voltooit om de server zachtjes te sluiten of de uitgezochte Sluiting van de Kracht nu om de server onmiddellijk tegen te houden zonder aan de gang zijnde taken te voltooien.
1. Klik in het venster Server Life Cycle Assistant op Ja om het afsluiten te voltooien.

