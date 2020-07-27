---
title: Bestanden met meerdere threads omzetten
seo-title: Bestanden met meerdere threads omzetten
description: Leer hoe u bestanden met meerdere threads kunt omzetten.
seo-description: Leer hoe u bestanden met meerdere threads kunt omzetten.
uuid: 830c78aa-4f68-4e01-8b24-69a0275689c7
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_pdf_generator
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 85d655bb-1b6b-4b4d-ae39-eca3ef9b7fd7
translation-type: tm+mt
source-git-commit: 1343cc33a1e1ce26c0770a3b49317e82353497ab
workflow-type: tm+mt
source-wordcount: '880'
ht-degree: 0%

---


# Bestanden met meerdere threads omzetten {#enabling-multi-threaded-file-conversions}

PDF Generator biedt de mogelijkheid om multi-threaded bestandsconversies in te schakelen voor bepaalde bestandstypen. Bestandsconversie via meerdere threads verbetert de prestaties van de PDF Generator doordat deze meerdere conversies tegelijk kan uitvoeren.

## Multithread-bestandsconversies inschakelen voor OpenOffice-, Word- en PowerPoint-documenten {#enabling-multi-threaded-file-conversions-for-openoffice-word-and-powerpoint-documents}

PDF Generator kan standaard slechts één OpenOffice-, Microsoft Word- of PowerPoint-document tegelijk converteren. Als u multi-threaded conversies inschakelt, kan PDF Generator meer dan een van de documenten gelijktijdig converteren. Met de PDF Generator worden meerdere instanties van OpenOffice of PDFMaker gestart (die worden gebruikt om de conversies van Word en PowerPoint uit te voeren).

>[!NOTE]
>
>Bestanden met meerdere threads worden niet ondersteund in Microsoft Word 2003 en PowerPoint 2003. Om multi-threaded dossieromzettingen toe te laten, bevorder aan Microsoft Word 2007 en PowerPoint 2007 of Microsoft Word 2010 en PowerPoint 2010.

>[!NOTE]
>
>Bestanden met meerdere threads worden niet ondersteund in Microsoft Excel, Microsoft Visio, Microsoft Project of Microsoft Publisher.

Elke instantie van OpenOffice of PDFMaker wordt gestart met een aparte gebruikersaccount. Elke gebruikersaccount die u toevoegt, moet een geldige gebruiker zijn met beheerdersrechten op de computer van de formulierserver. In een gegroepeerd milieu, moet de zelfde reeks gebruikers voor alle knopen van de cluster geldig zijn.

Op de pagina Gebruikersaccounts in de beheerconsole kunt u opgeven welke gebruikersaccounts moeten worden gebruikt voor bestanden met meerdere threads. U kunt accounts toevoegen, verwijderen of wachtwoorden voor accounts wijzigen. Als u de Generator PDF op de Server 2003 van Vensters of de Server 2008 van Vensters in werking stelt, voeg minstens drie gebruikersrekeningen toe die beheerdervoorrechten hebben.

Wanneer het toevoegen van gebruikers voor OpenOffice, Microsoft Word, of Microsoft PowerPoint op de Server 2003 of 2008 van Vensters, of voor OpenOffice op Linux of Sun™ Solaris™, de aanvankelijke activeringsdialogen voor alle gebruikers verwerpen.

### Voeg het recht toe om het proces-vlakke teken te vervangen {#add-the-right-to-replace-the-process-level-token}

In een Windows-besturingssysteem moeten de beheerdersgebruikersaccounts die worden gebruikt voor PDF-conversie (PDFG-gebruikers) de tokenrechten op procesniveau vervangen. U kunt dit recht toevoegen door de Redacteur van het Beleid van de Groep te gebruiken:

1. Klik in het menu Start van Windows op Uitvoeren en voer vervolgens gpedit.msc in.
1. Klik op Lokaal computerbeleid > Computerconfiguratie > Windows-instellingen > Beveiligingsinstellingen > Lokaal beleid > Toewijzing gebruikersrechten. Bewerk het token *-beleid* Vervangen om de groep Beheerders op te nemen.
1. Voeg de gebruiker toe aan de Replace een Symbolische ingang van het Niveau van het Proces.

### Aanvullende configuratie vereist voor OpenOffice, Microsoft Word en Microsoft PowerPoint op Windows Server 2008 {#additional-configuration-required-for-openoffice-microsoft-word-and-microsoft-powerpoint-on-windows-server-2008}

Als u OpenOffice, Microsoft Word, of Microsoft PowerPoint op de Server 2008 van Vensters in werking stelt, maak UAC voor elke toegevoegde gebruiker onbruikbaar.

1. Klik op Configuratiescherm > Gebruikersaccounts > Gebruikersaccountbeheer in- of uitschakelen.
1. Schakel het selectievakje Gebruikersaccountbeheer (UAC) gebruiken om uw computer te beschermen uit en klik op OK.
1. Start de computer opnieuw om de instellingen te activeren.

### Aanvullende configuratie vereist voor OpenOffice op Linux of Solaris {#additional-configuration-required-for-openoffice-on-linux-or-solaris}

1. Gebruikersaccounts toevoegen. (Zie Een gebruikersaccount [](enabling-multi-threaded-file-conversions.md#add-a-user-account)toevoegen.)
1. Vervolgens brengt u wijzigingen aan in het bestand /etc/sudoers. De standaardmachtigingen voor dit bestand zijn 440. Wijzig de machtiging voor dit bestand in schrijfbaar.
1. Voeg vermeldingen toe voor extra gebruikers (behalve de beheerder die de formulierserver uitvoert) in het bestand /etc/sudoers. Als u bijvoorbeeld AEM-formulieren uitvoert als een gebruiker met de naam lcadm en een server met de naam myhost, en u gebruikers1 en user2 wilt imiteren, voegt u de volgende vermeldingen toe aan /etc/sudoers:

   ```shell
    lcadm myhost=(user1) NOPASSWD: ALL
    lcadm myhost=(user2) NOPASSWD: ALL
   ```

   Met deze configuratie kan lcadm elke opdracht op de host &quot;myhost&quot; uitvoeren als &quot;user1&quot; of &quot;user2&quot; zonder dat er om een wachtwoord wordt gevraagd.

   >[!NOTE]
   >
   >Zorg ervoor dat u de gebruikersrollen van de systeemgebruiker en PDFG aan &quot;user1&quot;en &quot;user2&quot;hebt toegewezen. Zie Een gebruikersaccount [toevoegen als u een PDFG-rol aan een gebruiker wilt toewijzen](enabling-multi-threaded-file-conversions.md#add-a-user-account)

1. Zoek en becommentariëer deze regel ook in het bestand /etc/sudoers door een hekje (#) aan het begin van de regel toe te voegen:

   ```shell
   Defaults requiretty
   ```

   Hiermee kunt u Linux-gebruikers toevoegen.

1. Wijzig de machtiging voor het bestand e-mail/submenu&#39;s weer in 440.
1. Hiermee kunnen alle gebruikers die u hebt toegevoegd via [Een gebruikersaccount](enabling-multi-threaded-file-conversions.md#add-a-user-account) toevoegen, verbinding maken met de formulierserver. Als u een lokale gebruiker met de naam user1 bijvoorbeeld toestemming wilt geven om verbinding te maken met de formulierserver, gebruikt u de volgende opdracht

   `xhost +local:user1@`

   Raadpleeg de documentatie van xhost voor meer informatie.

1. Start de server opnieuw.

>[!NOTE]
>
>OpenOffice moet zijn geïnstalleerd op een maplocatie waartoe alle PDFG-gebruikers toegang hebben. U kunt dit verifiëren door u aan te melden als gebruiker PDFG en te controleren of u OpenOffice zonder problemen kunt starten.

### Een gebruikersaccount toevoegen {#add-a-user-account}

1. Klik in de beheerconsole op Services > PDF Generator > Gebruikersaccounts.
1. Klik op Toevoegen en voer de gebruikersnaam en het wachtwoord in van een gebruiker die beheerdersrechten heeft op de formulierserver. Als u gebruikers voor OpenOffice vormt, verwerp de aanvankelijke activeringsdialoogvensters OpenOffice.

   >[!NOTE]
   >
   >Als u gebruikers voor OpenOffice vormt, kan het aantal instanties van OpenOffice niet groter zijn dan aantal gebruikersrekeningen die in deze stap worden gespecificeerd.

1. Start de formulierserver opnieuw.

### Een gebruiker verwijderen uit de lijst die wordt gebruikt voor bestanden met meerdere threads {#remove-a-user-from-the-list-used-for-multi-threaded-file-conversions}

1. Klik in de beheerconsole op Services > PDF Generator > Gebruikersaccounts.
1. Klik op het selectievakje naast de gebruiker die u wilt verwijderen en klik op Verwijderen.
1. Klik op de bevestigingspagina op Verwijderen.
1. Start de formulierserver opnieuw.

### Het wachtwoord voor een account wijzigen {#change-the-password-for-an-account}

1. Klik in de beheerconsole op Services > PDF Generator > Gebruikersaccounts.
1. Klik op de gebruikersnaam en voer het nieuwe wachtwoord in en bevestig dit. Dit wachtwoord moet overeenkomen met het systeemwachtwoord van de gebruiker.

