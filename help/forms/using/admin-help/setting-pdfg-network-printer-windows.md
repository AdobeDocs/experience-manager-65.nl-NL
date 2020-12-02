---
title: Een PDFG-netwerkprinter instellen (alleen Windows)
seo-title: Een PDFG-netwerkprinter instellen (alleen Windows)
description: Leer hoe u een PDFG-netwerkprinter instelt (alleen Windows)
seo-description: Leer hoe u een PDFG-netwerkprinter instelt (alleen Windows)
uuid: 13b8481e-5ef0-4a07-9602-7bc4d9e05dd4
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_pdf_generator
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 7620e5e4-022e-49b2-8cfe-d5eec8ab99d7
translation-type: tm+mt
source-git-commit: 317fadfe48724270e59644d2ed9a90fbee95cf9f
workflow-type: tm+mt
source-wordcount: '627'
ht-degree: 0%

---


# Een PDFG-netwerkprinter instellen (alleen Windows) {#setting-up-a-pdfg-network-printer-windows-only}

Met PDFG Network Printer kunnen gebruikers een PDF-document genereren vanuit elke toepassing die afdrukken ondersteunt. Nadat een gebruiker de PDFG-netwerkprinter heeft geïnstalleerd, wordt een nieuwe printer met de naam *PDF-generator* weergegeven in het gedeelte Printers van het Configuratiescherm van Windows. Als er al een printer met dezelfde naam bestaat, wordt de gebruiker gevraagd een andere naam op te geven.

Als u vanuit een toepassing op deze printer afdrukt, wordt het document (in PostScript-indeling) naar PDF Generator verzonden, die het PostScript-bestand naar PDF converteert. Afhankelijk van de configuratie van de PDF Generator stuurt het PDF-document naar de gebruiker als een bijlage bij een e-mailbericht, stuurt het PDF-document door naar een opgegeven AEM formulierservice of -proces, of voert beide handelingen uit.

U moet de volgende stappen uitvoeren om een PDFG-netwerkprinter in te stellen:

1. E-mailinstellingen configureren. (Zie [E-mailinstellingen configureren voor PDFG Network Printer](setting-pdfg-network-printer-windows.md#configure-email-settings-for-pdfg-network-printer).)
1. In de beheersconsole, vorm de montages van de Printer van het Netwerk PDFG. (Zie [De instellingen voor de PDFG-netwerkprinter configureren](setting-pdfg-network-printer-windows.md#configure-the-pdfg-network-printer-settings).)
1. Zorg ervoor dat uw gebruikers zijn geconfigureerd met een geldig e-mailadres in de database met AEM formulieren en wijs de PDFGUserPermission toe aan elke gebruiker. <!-- Fix broken link See Setting up and organizing users -->
1. Zorg ervoor dat 32-bits JRE6 is geïnstalleerd op de computers van uw gebruikers.
1. Installeer de printer op de computers van uw gebruikers. (Zie [PDFG-netwerkprinter installeren op de computer van een gebruiker](setting-pdfg-network-printer-windows.md#install-pdfg-network-printer-on-a-user-s-computer).)

## E-mailinstellingen configureren voor PDFG-netwerkprinter {#configure-email-settings-for-pdfg-network-printer}

1. Klik in de beheerconsole op Services > Toepassingen en services > Servicebeheer.
1. Voor de pagina van het Beheer van de Dienst, klik provider.email_sendmail_service, specificeer de montages SMTP, en klik sparen.

## De instellingen voor PDFG-netwerkprinter configureren {#configure-the-pdfg-network-printer-settings}

1. Klik in de beheerconsole op Services > PDF Generator > PDFG Network Printer
1. Selecteer in de lijsten Adobe PDF-instellingen en Beveiligingsinstellingen de opties die u wilt toepassen op de gegenereerde PDF. Zie [Adobe PDF-instellingen configureren](/help/forms/using/admin-help/configuring-pdf-settings.md#configuring-adobe-pdf-settings) en [Beveiligingsinstellingen configureren](/help/forms/using/admin-help/configuring-security-settings.md#configuring-security-settings) voor meer informatie over deze instellingen.
1. Als u de geconverteerde PDF&#39;s weer naar gebruikers wilt verzenden, selecteert u de optie Het geconverteerde PDF-bestand naar gebruiker e-mailen en geeft u de volgende gegevens op:

   * Het e-mailadres dat moet worden gebruikt om PDF&#39;s naar de gebruikers te verzenden
   * Het onderwerp van het e-mailbericht
   * De kop-, tekst- en voettekst van het e-mailbericht. In het e-mailbericht wordt &lt;receiverName> vervangen door de volledige naam van de gebruiker die het document heeft afgedrukt.

1. Als u de geconverteerde PDF&#39;s naar een AEM formulierservice of -proces wilt verzenden, selecteert u de optie De geconverteerde PDF doorsturen naar de opgegeven AEM formulierservice of -verwerking en geeft u de volgende informatie op:

   * De naam van de service die moet worden aangeroepen
   * De naam van de verrichting van de dienst aan te halen
   * De naam van de invoerparameter, zoals opgegeven in het bestand component.xml van de service of het proces. Het PDF-document wordt gebruikt als een waarde voor die invoerparameter.

1. Klik op Opslaan.

Als u de oorspronkelijke standaard-e-mailtekst wilt herstellen, klikt u op E-mailinhoud herstellen.

## PDFG-netwerkprinter installeren op de computer van een gebruiker {#install-pdfg-network-printer-on-a-user-s-computer}

Gebruikers die de rol van PDFG-beheerder of PDFG-gebruiker hebben, kunnen een PDFG-netwerkprinter installeren. Er moet een 32-bits JDK op de computer zijn geïnstalleerd.

1. (PDFG-beheerders) Klik in de beheerconsole op Services > PDF Generator > PDFG Network Printer.

   (PDFG-gebruikers) Ga naar `http(s)://[host]:'port'/pdfgui` en klik op de koppeling onder Installatie van PDFG-netwerkprinter.

1. Klik op de koppeling onder de installatie van de PDFG-netwerkprinter. Geef bij de aanwijzing voor gegevens van gebruikersaccounts de gebruikersnaam en het wachtwoord op die u in stap 1 hebt gebruikt om u aan te melden. Er verschijnt een bericht met de mededeling dat de printer is geïnstalleerd.

   ***opmerking **: Als het wachtwoord van de gebruiker verandert, moeten gebruikers de PDFG-netwerkprinter opnieuw installeren op hun computer. U kunt het wachtwoord niet bijwerken vanaf de beheerconsole.*

1. Klik op OK.

