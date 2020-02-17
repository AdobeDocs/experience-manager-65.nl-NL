---
title: Op certificaten gebaseerde verificatie configureren
seo-title: Op certificaten gebaseerde verificatie configureren
description: Importeer een certificaat van certificeringsinstanties (CA) in het vertrouwde archief en maak een certificaattoewijzing voor verificatie op basis van een certificaat.
seo-description: Importeer een certificaat van certificeringsinstanties (CA) in het vertrouwde archief en maak een certificaattoewijzing voor verificatie op basis van een certificaat.
uuid: 9802a969-6d29-4b80-a4ed-06eb6e66e046
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: d958ae65-3008-4d68-9e11-4346e149827f
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Op certificaten gebaseerde verificatie configureren {#configuring-certificate-based-authentication}

Gebruikersbeheer voert meestal verificatie uit met een gebruikersnaam en wachtwoord. Gebruikersbeheer ondersteunt ook op certificaten gebaseerde verificatie, waarmee u gebruikers kunt verifiëren via Acrobat of gebruikers programmatisch kunt verifiëren. Voor details over het voor authentiek verklaren van gebruikers programmatically, zie [Programmering met vormen](https://www.adobe.com/go/learn_aemforms_programming_63)AEM.

Als u verificatie op basis van certificaten wilt gebruiken, importeert u een certificaat van certificeringsinstanties (CA) dat u vertrouwt in het vertrouwde archief en maakt u vervolgens een certificaattoewijzing.

## Het CA-certificaat importeren {#import-the-ca-certificate}

Selecteer tijdens het importeren van het certificaat de opties Vertrouwd op certificaatverificatie en Vertrouwen op identiteit en eventuele andere opties die u nodig hebt. Zie Certificaten [beheren voor meer informatie over het importeren van certificaten](/help/forms/using/admin-help/certificates.md#managing-certificates).

## Certificaattoewijzing configureren {#configuring-certificate-mapping}

Als u verificatie op basis van certificaten wilt inschakelen voor gebruikers, maakt u een certificaattoewijzing. Een *certificaattoewijzing* definieert een kaart tussen de kenmerken van een certificaat en de kenmerken van gebruikers in een domein. U kunt meerdere certificaten toewijzen aan hetzelfde domein.

Wanneer u een certificaat test, uploadt Gebruikersbeheer de certificaatcontroles om ervoor te zorgen dat het aan de volgende vereisten voldoet:

* Het certificaat is geldig.
* De uitgever u specificeerde kan het certificaat verifiëren.
* Het certificaat bevat het kenmerk dat is vereist voor toewijzing.
* Door de toewijzing die u hebt opgegeven, wordt het certificaat toegewezen aan slechts één gebruiker in de AEM-formulierdatabase. Zowel huidige als verouderde (verwijderde) gebruikers worden gecontroleerd om te bepalen of zij aan de toewijzingscriteria voldoen. Daarom ontbreekt de certificaattest als meer dan één gebruiker, met inbegrip van verouderde gebruikers, de attributenwaarde heeft die wordt overwogen.

>[!NOTE]
>
>U kunt een bestaande certificaattoewijzing niet bewerken.

**Certificaattoewijzing toevoegen**

1. Klik in de beheerconsole op Instellingen > Gebruikersbeheer > Configuratie > Certificaattoewijzing.
1. Klik op Nieuwe certificaattoewijzing en selecteer in de lijst Voor uitgever de certificaatalias zoals geconfigureerd in Betrouwbaarheidsopslagbeheer.
1. Wijs een van de kenmerken van het certificaat toe aan het kenmerk van een gebruiker. U kunt bijvoorbeeld de algemene naam van het certificaat toewijzen aan de aanmeldings-id van de gebruiker.

   Als de inhoud van het kenmerk in het certificaat afwijkt van de inhoud in het kenmerk van de gebruiker in de gebruikersbeheerdatabase, kunt u een reguliere Java-expressie (regex) gebruiken die overeenkomt met de twee kenmerken. Bijvoorbeeld, als de gemeenschappelijke namen van de certificaten namen zoals *Alex Pink (Authentificatie)* en *Alex Pink (Ondertekenen)* zijn en de gemeenschappelijke naam in het gegevensbestand van het Beheer van de Gebruiker *Alex Pink* is, gebruikt u een regex om het vereiste deel van het certificaatattribuut (in dit voorbeeld, *Alex Pink*.) te halen. De reguliere expressie die u opgeeft, moet voldoen aan de Java regex-specificatie.

   U kunt de expressie transformeren door de volgorde van de groepen op te geven in het vak Aangepaste volgorde. De aangepaste volgorde wordt gebruikt bij de `java.util.regex.Matcher.replaceAll()` methode. Het gedrag dat wordt weergegeven, komt overeen met het gedrag van die methode en de invoertekenreeks (de aangepaste volgorde) moet dienovereenkomstig worden opgegeven.

   Om regex te testen, ga een waarde in het vakje van de Parameter van de Test in en klik Test.

   U kunt de volgende tekens in de regex gebruiken:

   * . (om het even welk karakter)
   *  &amp;ast; (0 of meer exemplaren)
   * () (geef de groep tussen haakjes op)
   * \ (wordt gebruikt om een regex-teken te verwijderen uit een normaal teken)
   * $n (wordt gebruikt om naar de negende groep te verwijzen)
   Voorbeelden van reguliere expressies:

   * Om &quot;Alex Pink&quot; te extraheren uit &quot;Alex Pink (Authentication)&quot;

      **** Regex: (.&amp;ast;) \(Authentificatie\)

   * &quot;Alex Pink&quot; uit &quot;Alex (Authentication) Pink&quot; extraheren

      **** Regex: (.&amp;ast;)\(Authentificatie\) (.&amp;ast;)

   * Om &quot;Roze Alex&quot; te extraheren uit &quot;Alex (Authentication) Pink&quot;

      **** Regex: (.&amp;ast;)\(Authentificatie\) (.&amp;ast;)

      Aangepaste volgorde: $2 $1 (tweede groep retourneren, samengevoegd met eerste groep, vastgelegd door teken voor witruimte)

   * &quot;apink@sampleorg.com&quot; extraheren uit &quot;smtp:apink@sampleorg.com&quot;

      **** Regex: smtp:(.&amp;ast;)
   Zie [Java-zelfstudie over reguliere expressies](https://java.sun.com/docs/books/tutorial/essential/regex/)voor meer informatie over het gebruik van reguliere expressies.

1. Selecteer in de lijst Voor domein het domein van de gebruiker.
1. Als u deze configuratie wilt testen, klikt u op Bladeren om een voorbeeldgebruikerscertificaat te uploaden, klikt u op Certificaat testen en klikt u op OK als de configuratie juist is.

**Een bestaande certificaattoewijzing bewerken**

1. Klik in Beheerconsole op Instellingen > Gebruikersbeheer > Configuratie.
1. Klik op Certificaattoewijzing.
1. Selecteer de certificaattoewijzing om de configuratie ervan te bewerken. U kunt de reguliere expressie en de aangepaste volgorde bijwerken.
1. Als u uw wijzigingen wilt testen, klikt u op Bladeren om een voorbeeldcertificaat te uploaden, klikt u op Certificaat testen en vervolgens op OK.

**Certificaattoewijzing verwijderen**

1. Klik in de beheerconsole op Instellingen > Gebruikersbeheer > Configuratie > Certificaattoewijzing.
1. Schakel het selectievakje voor de certificaattoewijzing in die u wilt verwijderen, klik op Verwijderen en klik vervolgens op OK.

