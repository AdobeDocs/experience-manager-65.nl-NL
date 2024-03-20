---
title: Een PDFG-netwerkprinter instellen (alleen Windows)
description: Leer hoe u een PDFG-netwerkprinter instelt (alleen Windows)
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_pdf_generator
products: SG_EXPERIENCEMANAGER/6.5/FORMS
feature: PDF Generator
exl-id: c3fc159e-2677-4b71-b0b2-2feaf69e1a32
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '604'
ht-degree: 0%

---

# Een PDFG-netwerkprinter instellen (alleen Windows) {#setting-up-a-pdfg-network-printer-windows-only}

Met PDFG-netwerkprinter kunnen gebruikers een PDF-document genereren vanuit elke toepassing die afdrukken ondersteunt. Nadat een gebruiker de PDFG-netwerkprinter heeft geïnstalleerd, wordt een nieuwe printer met de naam *PDF-generator* wordt weergegeven in het gedeelte Printers van het Configuratiescherm van Windows. Als er al een printer met dezelfde naam bestaat, wordt de gebruiker gevraagd een andere naam op te geven.

Als u vanuit een toepassing op deze printer afdrukt, wordt het document (in PostScript-indeling) naar de PDF Generator verzonden. Hiermee wordt het PostScript-bestand naar PDF geconverteerd. Afhankelijk van de manier waarop u PDF Generator hebt geconfigureerd, verzendt het het PDF-document naar de gebruiker als een bijlage bij een e-mailbericht, stuurt het PDF-document door naar een opgegeven AEM formulierservice of -proces, of voert beide handelingen uit.

U moet de volgende stappen uitvoeren om een PDFG-netwerkprinter in te stellen:

1. E-mailinstellingen configureren. (Zie [E-mailinstellingen configureren voor PDFG Network Printer](setting-pdfg-network-printer-windows.md#configure-email-settings-for-pdfg-network-printer).)
1. In de beheersconsole, vorm de montages van de Printer van het Netwerk PDFG. (Zie [De instellingen voor de PDFG-netwerkprinter configureren](setting-pdfg-network-printer-windows.md#configure-the-pdfg-network-printer-settings).)
1. Zorg ervoor dat uw gebruikers zijn geconfigureerd met een geldig e-mailadres in de database met AEM formulieren en wijs de PDFGUserPermission toe aan elke gebruiker. <!-- Fix broken link See Setting up and organizing users -->
1. Zorg ervoor dat 32-bits JRE6 is geïnstalleerd op de computers van uw gebruikers.
1. Installeer de printer op de computers van uw gebruikers. (Zie [PDFG-netwerkprinter installeren op de computer van een gebruiker](setting-pdfg-network-printer-windows.md#install-pdfg-network-printer-on-a-user-s-computer).)

## E-mailinstellingen configureren voor PDFG Network Printer {#configure-email-settings-for-pdfg-network-printer}

1. Klik in de beheerconsole op Services > Toepassingen en services > Servicebeheer.
1. Voor de pagina van het Beheer van de Dienst, klik provider.email_sendmail_service, specificeer de montages SMTP, en klik sparen.

## De instellingen voor de PDFG-netwerkprinter configureren {#configure-the-pdfg-network-printer-settings}

1. Klik in de beheerconsole op Services > PDF Generator > PDFG Network Printer
1. Selecteer in de lijsten Adobe PDF-instellingen en Beveiligingsinstellingen de opties die u wilt toepassen op de gegenereerde PDF. Zie voor meer informatie over deze instellingen [Adobe PDF-instellingen configureren](/help/forms/using/admin-help/configuring-pdf-settings.md#configuring-adobe-pdf-settings) en [Beveiligingsinstellingen configureren](/help/forms/using/admin-help/configuring-security-settings.md#configuring-security-settings).
1. Als u de omgezette PDF weer naar gebruikers wilt terugsturen, selecteert u de optie Het omgezette bestand van de PDF terug naar de gebruiker e-mailen en geeft u de volgende gegevens op:

   * Het e-mailadres dat moet worden gebruikt om PDF naar de gebruikers te verzenden
   * Het onderwerp van het e-mailbericht
   * De kop-, tekst- en voettekst van het e-mailbericht. In het e-mailbericht: &lt;receivername> wordt vervangen door de volledige naam van de gebruiker die het document heeft afgedrukt.

1. Als u de geconverteerde PDF naar een AEM formulierservice of -proces wilt verzenden, selecteert u de optie De geconverteerde PDF naar de opgegeven AEM formulierservice of -verwerking doorsturen en geeft u de volgende informatie op:

   * De naam van de service die moet worden aangeroepen
   * De naam van de verrichting van de dienst aan te halen
   * De naam van de invoerparameter, zoals opgegeven in het bestand component.xml van de service of het proces. Het PDF-document wordt gebruikt als een waarde voor die invoerparameter.

1. Klik op Opslaan.

Als u de oorspronkelijke standaard-e-mailtekst wilt herstellen, klikt u op E-mailinhoud herstellen.

## PDFG-netwerkprinter installeren op de computer van een gebruiker {#install-pdfg-network-printer-on-a-user-s-computer}

Gebruikers met de rol PDFG-beheerder of PDFG-gebruiker kunnen een PDFG-netwerkprinter installeren. Er moet een 32-bits JDK op de computer zijn geïnstalleerd.

1. (PDFG-beheerders) Klik in de beheerconsole op Services > PDF Generator > PDFG-netwerkprinter.

   (PDF-gebruikers) Ga naar `http(s)://[host]:'port'/pdfgui` en klik op de koppeling onder de installatie van de PDFG-netwerkprinter.

1. Klik op de koppeling onder Installatie van PDFG-netwerkprinter. Geef bij de aanwijzing voor gegevens van gebruikersaccounts de gebruikersnaam en het wachtwoord op die u in stap 1 hebt gebruikt voor aanmelding. Er verschijnt een bericht met de mededeling dat de printer is geïnstalleerd.

   ***notitie **: Als het wachtwoord van de gebruiker wordt gewijzigd, moeten gebruikers de PDFG-netwerkprinter opnieuw installeren op hun computer. U kunt het wachtwoord niet bijwerken vanaf de beheerconsole.*

1. Klik op OK.
