---
title: HTML5-voorbeeld van een XDP-formulier genereren
seo-title: HTML5-voorbeeld van een XDP-formulier genereren
description: Het tabblad Voorbeeld-HTML in LiveCycle Designer kan worden gebruikt om een voorbeeld van formulieren weer te geven zoals deze in een browser worden weergegeven.
seo-description: Het tabblad Voorbeeld-HTML in LiveCycle Designer kan worden gebruikt om een voorbeeld van formulieren weer te geven zoals deze in een browser worden weergegeven.
uuid: cbee956f-bf2d-40c5-8e03-58fce0fa215b
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
discoiquuid: 34e6d1bc-4eca-42dc-9ae5-9a2107fbefce
docset: aem65
translation-type: tm+mt
source-git-commit: 317fadfe48724270e59644d2ed9a90fbee95cf9f

---


# HTML5-voorbeeld van een XDP-formulier genereren{#generate-html-preview-of-an-xdp-form}

Tijdens het ontwerpen van een formulier in AEM Forms Designer kunt u niet alleen een voorbeeld bekijken van de PDF-uitvoering van een formulier, maar ook een voorbeeld bekijken van een HTML5-uitvoering. Op het tabblad **Voorbeeld-HTML** kunt u een voorbeeld van een formulier bekijken zoals het in een browser wordt weergegeven.

## HTML-voorbeeld voor XDP-formulieren inschakelen in Designer {#html-preview-of-forms-in-forms-designer}

Voer de volgende configuraties uit om Designer in staat te stellen een HTML-voorbeeld van XDP-formulieren te genereren:

* Apache Sling Authentication Service configureren
* Beveiligde modus uitschakelen
* Geef details van de AEM Forms-server

### Apache Sling Authentication Service configureren {#configure-apache-sling-authentication-service}

1. Ga naar `https://'[server]:[port]'/system/console/configMgr` AEM Forms die wordt uitgevoerd op OSGi of
   `https://'[server]:[port]'/lc/system/console/configMgr` op AEM Forms die wordt uitgevoerd op JEE.
1. Zoek en klik op de configuratie van **Apache Sling Authentication Service** om deze te openen in de bewerkingsmodus.

1. Afhankelijk van of u Vormen AEM op OSGi of JEE in werking stelt, voeg het volgende op het gebied van de Vereisten **van de** Authentificatie toe:

   * AEM-formulieren op JEE

      * -/content/xfaforms
      * -/etc/clientlibs
   * AEM-formulieren op OSGi

      * -/content/xfaforms
      * -/etc/clientlibs/fd/xfaforms
   >[!NOTE]
   >
   >Kopieer en plak de opgegeven waarde niet in het veld Verificatievereisten omdat de speciale tekens in de waarde hierdoor kunnen beschadigd raken. Typ in plaats daarvan de opgegeven waarde in het veld.

1. Geef een gebruikersnaam en wachtwoord op in respectievelijk de velden **[!UICONTROL Anonieme gebruikersnaam]** en **[!UICONTROL Anoniem gebruikerswachtwoord]** . De gespecificeerde geloofsbrieven worden gebruikt om anonieme authentificatie te behandelen en toegang tot anonieme gebruikers toe te staan.
1. Klik op **Opslaan** om de configuratie op te slaan.

### Beveiligde modus uitschakelen {#disable-protected-mode}

De [beveiligde modus](../../forms/using/get-xdp-pdf-documents-aem.md) is standaard ingeschakeld. Houd het ingeschakeld voor de productieomgevingen. U kunt dit uitschakelen voor een ontwikkelomgeving om HTML5 Forms in Designer voor te vertonen. Voer de volgende stappen uit om het uit te schakelen:

1. Meld u als beheerder aan bij de AEM-webconsole.

   * URL voor AEM-formulieren op OSGi is `https://'[server]:[port]'/system/console/configMgr`
   * URL voor AEM Forms on JEE is `https://'[server]:[port]'/lc/system/console/configMgr`

1. Open **[!UICONTROL Mobiele Forms Configurations]** voor bewerking.
1. Schakel de optie **[!UICONTROL Beveiligde modus]** uit en klik op **[!UICONTROL Opslaan]**.

### Geef details van de AEM Forms-server {#provide-details-of-aem-forms-server}

1. Ga in Designer naar **Gereedschappen** > **Opties**.
1. Selecteer in het venster Opties de pagina **Serveropties** , geef de volgende gegevens op en klik op **OK**.

   * **Server-URL**: URL AEM Forms-server.

   * **HTTP-poortnummer**: AEM-serverpoort. De standaardwaarde is 4502.
   * **Context HTML-voorvertoning:** Pad van het profiel voor het weergeven van XFA-formulieren. De volgende standaardprofielen worden gebruikt voor een voorbeeld van het formulier in Designer. U kunt echter ook het pad naar een aangepast profiel opgeven.

      * `/content/xfaforms/profiles/default.html` (AEM-formulieren op OSGi)

      * `/lc/content/xfaforms/profiles/default.html` (AEM-formulieren in JEE)
   * **Context van Forms Manager:** Contextpad waarop de interface van Forms Manager wordt geïmplementeerd. De standaardwaarden zijn:

      * `/aem/forms` (AEM-formulieren op OSGi)
      * `/lc/forms` (AEM-formulieren in JEE)
   **Opmerking:** Zorg ervoor dat de AEM Forms-server actief is. The HTML preview connects to the CRX server to *generate* a preview.

   ![Opties voor AEM Forms Designer ](assets/server_options.png)

   Opties voor AEM Forms Designer

1. Als u een voorbeeld van een formulier in HTML wilt bekijken, klikt u op het tabblad **Voorbeeld-HTML** .

   >[!NOTE]
   >
   >
   >
   >
   >    * Als het tabblad HTML-voorbeeld is gesloten, drukt u op F4 om het tabblad Voorbeeld-HTML te openen. U kunt ook Voorvertoning HTML selecteren in het menu Weergave om het tabblad Voorbeeld-HTML te openen.
   >    * De HTML-voorvertoning ondersteunt geen PDF-documenten, de HTML-voorvertoning is alleen voor XDP-documenten.


   >[!CAUTION]
   >
   >Als u de echte ervaring van eindgebruikers wilt testen, kunt u ook een voorbeeld van uw formulieren weergeven in externe browsers (Google Chrome, Microsoft Edge, Mozilla Firefox en meer). Elke browser gebruikt een aparte engine voor het weergeven van HTML. Er kunnen dus enkele verschillen zijn in de manier waarop een voorbeeld van een formulier wordt weergegeven in Designer en de externe browser.

## Een voorbeeld van een formulier weergeven met behulp van voorbeeldgegevens {#to-preview-a-form-using-sample-data}

Designer biedt u de mogelijkheid een voorbeeld van formulieren weer te geven en formulieren te testen met XML-voorbeeldgegevens. Het verdient aanbeveling regelmatig uw formulier te testen met voorbeeldgegevens om ervoor te zorgen dat het formulier correct wordt weergegeven.

Als u geen voorbeeldgegevens hebt, kunt u die laten maken in Designer of deze zelf maken. (Zie [Voorbeeldgegevens automatisch genereren voor een voorbeeldweergave van een formulier](https://help.adobe.com/en_US/AEMForms/6.1/DesignerHelp/WS107c29ade9134a2c136ae6f212a1f379c94-8000.2.html#WS92d06802c76abadb-728f46ac129b395660c-7efe.2) en [Voorbeeldgegevens maken voor een voorbeeldweergave van uw formulier](https://help.adobe.com/en_US/AEMForms/6.1/DesignerHelp/WS107c29ade9134a2c136ae6f212a1f379c94-8000.2.html#WS92d06802c76abadb-728f46ac129b395660c-7eff.2).)

Als u een formulier test met een bron voor voorbeeldgegevens, weer u zeker dat de gegevens en de velden zijn gekoppeld en dat herhalende subformulieren op de verwachte manier worden herhaald. U kunt een evenwichtige formulierindeling maken met voldoende ruimte voor elk object om de samengevoegde gegevens weer te geven.

1. Select **File > Form Properties**.

1. Click the **Preview** tab and, in the Data File box, type the full path to your test data file. U kunt de Browse knoop ook gebruiken om aan het dossier te navigeren.

1. Click **OK**. The next time you preview the form in the **Preview HTML** tab, the data values from the sample XML file will appear in the respective objects.

## Formulieren voorvertonen in een gegevensopslagruimte {#html-preview-of-forms-in-forms-manager}

In AEM Forms kunt u formulieren en documenten voorvertonen in een gegevensopslagruimte. Aan de hand van een voorbeeld kunt u precies zien hoe de formulieren eruitzien en zich gedragen zoals ze worden gebruikt door eindgebruikers.

[Contact opnemen met ondersteuning](https://www.adobe.com/account/sign-in.supportportal.html)
