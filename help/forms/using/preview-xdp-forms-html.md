---
title: HTML5-voorbeeld van een XDP-formulier genereren
description: Het tabblad Voorbeeld-HTML in LiveCycle Designer kan worden gebruikt om een voorbeeld van formulieren weer te geven zoals deze in een browser worden weergegeven.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
docset: aem65
feature: HTML5 Forms
exl-id: 548f302b-57f0-4bdc-8a99-1a4967caa32f
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '769'
ht-degree: 0%

---

# HTML5-voorbeeld van een XDP-formulier genereren{#generate-html-preview-of-an-xdp-form}

Tijdens het ontwerpen van een formulier in AEM Forms Designer kunt u niet alleen een voorbeeld bekijken van de PDF-uitvoering van een formulier, maar ook een voorbeeld bekijken van een HTML5-uitvoering. U kunt de **Voorvertoning HTML** gebruiken om een voorbeeld van een formulier weer te geven zoals het in een browser wordt weergegeven.

## Voorvertoning van HTML inschakelen voor XDP-formulieren in Designer {#html-preview-of-forms-in-forms-designer}

Voer de volgende configuraties uit om Designer in staat te stellen een HTML-voorbeeld van XDP-formulieren te genereren:

* Apache Sling Authentication Service configureren
* Beveiligde modus uitschakelen
* Geef details van de AEM Forms-server op

### Apache Sling Authentication Service configureren {#configure-apache-sling-authentication-service}

1. Ga naar `https://'[server]:[port]'/system/console/configMgr` op AEM Forms, die wordt uitgevoerd op OSGi of
   `https://'[server]:[port]'/lc/system/console/configMgr` op AEM Forms in werking gesteld op JEE.
1. Zoeken en klikken **Apache Sling Authentication Service** configuratie om het in Edit wijze te openen.

1. Afhankelijk van of u AEM Forms op OSGi of JEE in werking stelt, voeg het volgende in toe **Verificatievereisten** veld:

   * AEM Forms op JEE

      * -/content/xfaforms
      * -/etc/clientlibs

   * AEM Forms op OSGi

      * -/content/xfaforms
      * -/etc/clientlibs/fd/xfaforms

   >[!NOTE]
   >
   >Kopieer en plak de opgegeven waarde niet in het veld Verificatievereisten omdat de speciale tekens in de waarde hierdoor kunnen beschadigd raken. Typ in plaats daarvan de opgegeven waarde in het veld.

1. Geef een gebruikersnaam en wachtwoord op in **[!UICONTROL Anonymous User Name]** en **[!UICONTROL Anonymous User Password]** respectievelijk velden. De gespecificeerde geloofsbrieven worden gebruikt om anonieme authentificatie te behandelen en toegang tot anonieme gebruikers toe te staan.
1. Klikken **Opslaan** om de configuratie op te slaan.

### Beveiligde modus uitschakelen {#disable-protected-mode}

De [beveiligde modus](../../forms/using/get-xdp-pdf-documents-aem.md) is standaard ingeschakeld. Houd het ingeschakeld voor de productieomgevingen. U kunt deze uitschakelen voor een ontwikkelomgeving om een voorvertoning van HTML5 Forms weer te geven in Designer. Voer de volgende stappen uit om het uit te schakelen:

1. Meld u als beheerder aan bij AEM webconsole.

   * URL voor AEM Forms op OSGi is `https://'[server]:[port]'/system/console/configMgr`
   * URL voor AEM Forms op JEE is `https://'[server]:[port]'/lc/system/console/configMgr`

1. Openen **[!UICONTROL Mobile Forms Configurations]** voor bewerken.
1. Hef de selectie van **[!UICONTROL Protected Mode]** en klik op **[!UICONTROL Save]**.

### Geef details van de AEM Forms-server op {#provide-details-of-aem-forms-server}

1. Ga in Designer naar **Gereedschappen** > **Opties**.
1. Selecteer in het venster Opties de optie **Serveropties** pagina, geef de volgende gegevens op en klik op **OK**.

   * **Server-URL**: URL AEM Forms-server.

   * **HTTP-poortnummer**: AEM serverpoort. De standaardwaarde is 4502.
   * **Context voorvertoning HTML:** Pad van het profiel voor het weergeven van XFA-formulieren. De volgende standaardprofielen worden gebruikt om een voorbeeld van het formulier weer te geven in Designer. U kunt echter ook het pad naar een aangepast profiel opgeven.

      * `/content/xfaforms/profiles/default.html` (AEM Forms op OSGi)

      * `/lc/content/xfaforms/profiles/default.html` (AEM Forms op JEE)

   * **Context Forms Manager:** Contextpad waarop de gebruikersinterface van Forms Manager wordt geïmplementeerd. De standaardwaarden zijn:

      * `/aem/forms` (AEM Forms op OSGi)
      * `/lc/forms` (AEM Forms op JEE)

   >[!NOTE]
   >
   >Zorg ervoor dat de AEM Forms-server actief is. De voorvertoning van de HTML maakt verbinding met de CRX-server met *genereren* een voorvertoning.

   ![Opties voor AEM Forms Designer ](assets/server_options.png)

   Opties voor AEM Forms Designer

1. Als u een voorbeeld van een formulier in HTML wilt weergeven, klikt u op de knop **Voorvertoning HTML** tab.

   >[!NOTE]
   >
   >
   >
   >
   >    * Als het tabblad Voorvertoning HTML is gesloten, drukt u op F4 om het tabblad Voorvertoning HTML te openen. U kunt ook Voorvertoning HTML selecteren in het menu Weergave om het tabblad Voorbeeld-HTML te openen.
   >    * De HTML-voorvertoning ondersteunt geen PDF-documenten, de HTML-voorvertoning is alleen voor XDP-documenten.
   >
   >

   >[!CAUTION]
   >
   >Als u de echte ervaring van eindgebruikers wilt testen, kunt u ook een voorbeeld van uw formulieren weergeven in externe browsers (Google Chrome, Microsoft Edge, Mozilla Firefox en meer). Elke browser gebruikt een aparte engine om HTML te renderen. Er kunnen dus enkele verschillen zijn in de manier waarop een voorbeeld van een formulier wordt weergegeven in Designer en de externe browser.

## Een voorbeeld van een formulier weergeven met behulp van voorbeeldgegevens {#to-preview-a-form-using-sample-data}

Met Designer kunt u een voorbeeld van een formulier bekijken en het formulier testen met XML-voorbeeldgegevens. Het wordt aanbevolen om regelmatig uw formulier te testen met voorbeeldgegevens om te controleren of het formulier correct wordt weergegeven.

Als u geen voorbeeldgegevens hebt, kunt u deze in Designer maken of deze zelf maken. (Zie [Voorbeeldgegevens automatisch genereren voor een voorbeeldweergave van het formulier](https://help.adobe.com/en_US/AEMForms/6.1/DesignerHelp/WS107c29ade9134a2c136ae6f212a1f379c94-8000.2.html#WS92d06802c76abadb-728f46ac129b395660c-7efe.2) en [Voorbeeldgegevens maken voor een voorbeeldweergave van uw formulier](https://help.adobe.com/en_US/AEMForms/6.1/DesignerHelp/WS107c29ade9134a2c136ae6f212a1f379c94-8000.2.html#WS92d06802c76abadb-728f46ac129b395660c-7eff.2).)

Als u het formulier test met een voorbeeldgegevensbron, weet u zeker dat de gegevens en velden zijn toegewezen en dat herhalende subformulieren op de verwachte manier worden herhaald. U kunt een evenwichtige formulierindeling maken die de juiste ruimte biedt voor elk object om de samengevoegde gegevens weer te geven.

1. Selecteren **File > Form Properties**.

1. Klik op de knop **Voorvertoning** en typt u in het vak Gegevensbestand het volledige pad naar het bestand met testgegevens. U kunt de Browse knoop ook gebruiken om aan het dossier te navigeren.

1. Klikken **OK**. De volgende keer dat u een voorbeeld van het formulier in het dialoogvenster **Voorvertoning HTML** worden de gegevenswaarden van het XML-voorbeeldbestand weergegeven in de desbetreffende objecten.

## Formulieren voorvertonen in een gegevensopslagruimte {#html-preview-of-forms-in-forms-manager}

In AEM Forms kunt u formulieren en documenten voorvertonen in een gegevensopslagruimte. Met Voorvertoning kunt u precies zien hoe de formulieren er uitzien en hoe ze zich gedragen door eindgebruikers.
