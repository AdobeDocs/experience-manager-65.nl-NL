---
title: De sendToPrinter-API gebruiken
description: Een document naar de printer verzenden met de service sendToPrinter.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: document_services
feature: Document Services
exl-id: 585d4053-1056-4d2b-a9df-9516775afe50
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---

# De sendToPrinter-API gebruiken {#using-the-sendtoprinter-api}

## Overzicht {#overview}

In AEM Forms kunt u een document naar de printer verzenden met de SendToPrinter-service. De dienst SendToPrinter steunt de volgende druktoegangsmechanismen:

* **Direct toegankelijke printer** `: A printer that is installed on the same computer is called a direct accessible printer, and the computer is named printer host. This type of printer can be a local printer that is connected to the computer directly.`

* **Indirecte toegankelijke printer** `: The printer that is installed on a print server is accessed from other computers. Technologies such as the common UNIX® printing system (CUPS) and the Line Printer Daemon (LPD) protocol are available to connect to a network printer. To access an indirect accessible printer, specify the print server’s IP or host name. Using this mechanism, you can send a document to an LPD URI when the network has an LPD running. The mechanism lets you route the document to any printer that is connected to the network that has an LPD running.`

  Wanneer u een document naar een printer verzendt, geeft u een van de volgende afdrukprotocollen op:

   * **CUPS** `: A printing protocol named common UNIX printing system. This protocol is used for UNIX operating systems and enables a computer to function as a print server. The print server accepts print requests from client applications, processes them, and sends them to configured printers. On the IBM AIX® operating system, usage of CUPS is not recommended.`
   * &quot;**DirectIP** `: A standard protocol for remote printing and managing print jobs. This protocol can be used locally or remotely. Print queues are not required.`
   * &quot;**LPD** `: A printing protocol named Line Printer Daemon protocol or Line Printer Remote (LPR) protocol. This protocol provides network print server functionality for UNIX-based systems.`
   * **SharedPrinter** `: A printing protocol that enables a computer to use a printer that is configured for that computer.`
   * **CIF**: De uitvoerservice ondersteunt het afdrukprotocol Common Internet File System (CIF).

## De SendToPrinter-service gebruiken {#using-sendtoprinter-service}

De onderstaande tabel bevat:

* informatie over printerName of printServer aan gebruik voor diverse protocollen.
* waarde of uitzondering die door een printer wordt geretourneerd voor verschillende combinaties van de printerserverURI en de printernaam

| Protocol (Toegangsmechanisme) | Print Server URI (PrinterSpec.printServer) | Naam van de printer (PrinterSpec.printerName) | Resultaat |
|--- |--- |--- |--- |
| SharedPrinter | Alle | Leeg | Uitzondering: vereist argument sPrinterName mag niet leeg zijn. |
| SharedPrinter | Alle | Ongeldig | Een uitzondering geeft aan dat de printer niet kan worden gevonden. |
| SharedPrinter | Alle | Geldig | Afdruktaak is voltooid. |
| LPD | Leeg | Alle | een uitzondering die verklaart dat het vereiste argument sPrintServerUri niet leeg kan zijn. |
| LPD | Ongeldig | Leeg | een uitzondering die verklaart dat het vereiste argument sPrinterName niet leeg kan zijn. |
| LPD | Ongeldig | Niet leeg | een uitzondering die verklaart dat sPrintServerUri niet wordt gevonden. |
| LPD | Geldig | Ongeldig | een uitzondering waarin staat dat de printer niet kan worden gevonden. |
| LPD | Geldig | Geldig | Een geslaagde afdruktaak. |
| CUPS | Leeg | Alle | een uitzondering die verklaart dat het vereiste argument sPrintServerUri niet leeg kan zijn. |
| CUPS | Ongeldig | Alle | een uitzondering waarin staat dat de printer niet kan worden gevonden. |
| CUPS | Geldig | Alle | Afdruktaak is voltooid. |
| DirectIP | Leeg | Alle | een uitzondering die verklaart dat het vereiste argument sPrintServerUri niet leeg kan zijn. |
| DirectIP | Ongeldig | Alle | een uitzondering waarin staat dat de printer niet kan worden gevonden. |
| DirectIP | Geldig | Alle | Afdruktaak is voltooid. |
| CIF | Geldig | Leeg | Afdruktaak is voltooid. |
| CIF | Ongeldig | Alle | een onbekende fout tijdens het afdrukken met CIF. |
| CIF | Leeg | Alle | een uitzondering die verklaart dat het vereiste argument sPrintServerUri niet leeg kan zijn. |

## Verificatieondersteuning {#authentication-support}

Verificatie wordt alleen ondersteund voor CIF afdrukken. Geef voor verificatie de gebruikersnaam/het wachtwoord/domein op in PrinterSpec. U kunt een wachtwoord coderen met AEM Granite CyprusSupport Service door de volgende stappen uit te voeren:

1. Ga naar https://&lt;server>:&lt;port>/system/console.

1. Ga naar **[!UICONTROL Main]** > **[!UICONTROL Crypto Support]**.

1. Typ een gewone tekst en klik op **[!UICONTROL Protect]**.
