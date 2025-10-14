---
title: HTML5-voorbeeld van een XDP-formulier genereren
description: Het tabblad Voorbeeld van HTML in LiveCycle Designer kan worden gebruikt voor een voorbeeld van formulieren zoals deze worden weergegeven in een browser.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
docset: aem65
feature: HTML5 Forms,Mobile Forms
exl-id: 548f302b-57f0-4bdc-8a99-1a4967caa32f
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '769'
ht-degree: 0%

---

# HTML5-voorbeeld van een XDP-formulier genereren{#generate-html-preview-of-an-xdp-form}

Tijdens het ontwerpen van een formulier in AEM Forms Designer kunt u niet alleen een voorbeeld bekijken van de PDF-uitvoering van een formulier, maar ook een voorbeeld bekijken van een HTML5-uitvoering. U kunt het **lusje van de HTML van de Voorproef** gebruiken om een vorm voor te proef aangezien het in browser zou verschijnen.

## Voorvertoning van HTML inschakelen voor XDP-formulieren in Designer {#html-preview-of-forms-in-forms-designer}

Voer de volgende configuraties uit om Designer in staat te stellen een voorbeeld van een HTML-XDP-formulier te genereren:

* Apache Sling Authentication Service configureren
* Beveiligde modus uitschakelen
* Geef details van de AEM Forms-server op

### Apache Sling Authentication Service configureren {#configure-apache-sling-authentication-service}

1. Ga naar `https://'[server]:[port]'/system/console/configMgr` op AEM Forms die wordt uitgevoerd op OSGi of
   `https://'[server]:[port]'/lc/system/console/configMgr` op AEM Forms wordt uitgevoerd op JEE.
1. Zoek en klik **configuratie van de Authentificatie van Apache het Verdelen van de Dienst** om het op uit te geven wijze te openen.

1. Afhankelijk van of u AEM Forms op OSGi of JEE in werking stelt, voeg het volgende op het **gebied van de Vereisten van de Authentificatie** toe:

   * AEM Forms op JEE

      * -/content/xfaforms
      * -/etc/clientlibs

   * AEM Forms op OSGi

      * -/content/xfaforms
      * -/etc/clientlibs/fd/xfaforms

   >[!NOTE]
   >
   >Kopieer en plak de opgegeven waarde niet in het veld Verificatievereisten omdat de speciale tekens in de waarde hierdoor kunnen beschadigd raken. Typ in plaats daarvan de opgegeven waarde in het veld.

1. Geef een gebruikersnaam en wachtwoord op in respectievelijk **[!UICONTROL Anonymous User Name]** en **[!UICONTROL Anonymous User Password]** . De gespecificeerde geloofsbrieven worden gebruikt om anonieme authentificatie te behandelen en toegang tot anonieme gebruikers toe te staan.
1. Klik **sparen** om de configuratie te bewaren.

### Beveiligde modus uitschakelen {#disable-protected-mode}

De [&#x200B; beschermde wijze &#x200B;](../../forms/using/get-xdp-pdf-documents-aem.md) is, door gebrek. Houd het ingeschakeld voor de productieomgevingen. U kunt deze uitschakelen voor een ontwikkelomgeving om een voorvertoning van HTML5 Forms weer te geven in Designer. Voer de volgende stappen uit om het uit te schakelen:

1. Meld u als beheerder aan bij AEM webconsole.

   * URL voor AEM Forms op OSGi is `https://'[server]:[port]'/system/console/configMgr`
   * URL voor AEM Forms op JEE is `https://'[server]:[port]'/lc/system/console/configMgr`

1. Open **[!UICONTROL Mobile Forms Configurations]** voor bewerking.
1. Schakel de optie **[!UICONTROL Protected Mode]** uit en klik op **[!UICONTROL Save]** .

### Geef details van de AEM Forms-server op {#provide-details-of-aem-forms-server}

1. In Designer, ga naar **Hulpmiddelen** > **Opties**.
1. In het venster van Opties, uitgezochte **pagina van de Opties van de Server 0&rbrace; &lbrace;, verstrek de volgende details, en klik** O.K. **.**

   * **Server URL**: De server URL van AEM Forms.

   * **HTTP havenaantal**: AEM serverhaven. De standaardwaarde is 4502.
   * **de Context van de Voorproef van de HTML:** Weg van het profiel voor het teruggeven van XFA vormen. De volgende standaardprofielen worden gebruikt om een voorbeeld van het formulier in Designer weer te geven. U kunt echter ook het pad naar een aangepast profiel opgeven.

      * `/content/xfaforms/profiles/default.html` (AEM Forms op OSGi)

      * `/lc/content/xfaforms/profiles/default.html` (AEM Forms op JEE)

   * **Context van de Manager van Forms:** de weg van de context waarbij de Manager UI van Forms wordt opgesteld. De standaardwaarden zijn:

      * `/aem/forms` (AEM Forms op OSGi)
      * `/lc/forms` (AEM Forms op JEE)

   >[!NOTE]
   >
   >Zorg ervoor dat de AEM Forms-server actief is. De voorproef van HTML verbindt met de server van CRX ** produceren een voorproef.

   ![&#x200B; AEM Forms Designer-opties &#x200B;](assets/server_options.png)

   AEM Forms Designer-opties

1. Aan voorproef een vorm in HTML, klik de **HTML** tabel van de Voorproef.

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
   >Als u de werkelijke ervaring van eindgebruikers wilt testen, kunt u ook een voorbeeld van uw formulieren weergeven in externe browsers (Google Chrome, Microsoft Edge, Mozilla Firefox en meer). Elke browser gebruikt een aparte engine om HTML te renderen. Er kunnen dus enkele verschillen zijn in de manier waarop een formuliervoorvertoning wordt weergegeven in Designer en de externe browser.

## Een voorbeeld van een formulier weergeven met behulp van voorbeeldgegevens {#to-preview-a-form-using-sample-data}

Met Designer kunt u een voorbeeld van een formulier bekijken en het formulier testen met XML-voorbeeldgegevens. Het wordt aanbevolen om regelmatig uw formulier te testen met voorbeeldgegevens om te controleren of het formulier correct wordt weergegeven.

Als u geen voorbeeldgegevens hebt, kan Designer deze maken of deze zelf maken. (Zie [&#x200B; om steekproefgegevens automatisch te produceren om uw vorm &#x200B;](https://help.adobe.com/en_US/AEMForms/6.1/DesignerHelp/WS107c29ade9134a2c136ae6f212a1f379c94-8000.2.html#WS92d06802c76abadb-728f46ac129b395660c-7efe.2) voor te vertonen en [&#x200B; om steekproefgegevens tot stand te brengen om uw vorm &#x200B;](https://help.adobe.com/en_US/AEMForms/6.1/DesignerHelp/WS107c29ade9134a2c136ae6f212a1f379c94-8000.2.html#WS92d06802c76abadb-728f46ac129b395660c-7eff.2) voor te vertonen.)

Als u het formulier test met een voorbeeldgegevensbron, weet u zeker dat de gegevens en velden zijn toegewezen en dat herhalende subformulieren op de verwachte manier worden herhaald. U kunt een evenwichtige formulierindeling maken die de juiste ruimte biedt voor elk object om de samengevoegde gegevens weer te geven.

1. Selecteer **Dossier > de Eigenschappen van de Vorm**.

1. Klik het **lusje van de Voorproef** en, in het vakje van het Dossier van Gegevens, typ de volledige weg aan uw dossier van testgegevens. U kunt de Browse knoop ook gebruiken om aan het dossier te navigeren.

1. Klik **OK**. De volgende keer u voorproef de vorm in het **HTML** lusje van de Voorproef, zullen de gegevenswaarden van het dossier van steekproefXML in de respectieve voorwerpen verschijnen.

## Formulieren voorvertonen in een gegevensopslagruimte {#html-preview-of-forms-in-forms-manager}

In AEM Forms kunt u formulieren en documenten voorvertonen in een gegevensopslagruimte. Met Voorvertoning kunt u precies zien hoe de formulieren er uitzien en hoe ze zich gedragen door eindgebruikers.
