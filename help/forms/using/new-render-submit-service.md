---
title: Nieuwe renderservice en verzendservice
description: Definieer de renderservices en verzend services in Workbench om XDP-formulier te renderen als HTML of PDF, afhankelijk van het apparaat waartoe deze toegang heeft.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
docset: aem65
exl-id: 46de0101-9607-4429-84c3-7c1f34d2da27
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '891'
ht-degree: 0%

---

# Nieuwe renderservice en verzendservice{#new-render-and-submit-service}

## Inleiding {#introduction}

Als u in Workbench een `AssignTask` Geef een bepaald formulier op (XDP- of PDF-formulier). Geef ook een set services voor renderen en verzenden op via een actieprofiel.

Een XDP kan als vorm van de PDF of een vorm van de HTML worden teruggegeven. De nieuwe mogelijkheden omvatten de capaciteit om:

* Een XDP-formulier renderen en verzenden als HTML
* Een XDP-formulier weergeven en verzenden als PDF op het bureaublad en als HTML op mobiele apparaten (bijvoorbeeld een iPad)

### Nieuwe HTML Forms-service {#new-html-forms-service}

De nieuwe HTML Forms-service gebruikt de nieuwe functie in Forms om het weergeven van XDP-formulieren als HTML te ondersteunen. De nieuwe dienst van HTML Forms stelt de volgende methodes bloot:

```java
/*
 * Generates a URL (for the HTML Form) to be passed to client, given a TaskContext.
 * The output of this API is something like this - /lc/content/xfaforms/profiles/default.ws.html?ContentRoot=repository://Applications/MyApplication/MyFolder&template=MyForm.xdp
 * @param taskContext task context
 * @param profileName Forms servlet URL.
 * @return form URL string
 */
public String generateFormURL(TaskContext taskContext, String profileName);

/*
 * Render the XDP Form as HTML. Can be used directly for updating the runtimeMap in render.
 * It adds the following keys to the map -
 * hint:new html form = true
 * newHTMLFormURL = the URL returned after calling 'generateFormURL' API.
 * @param TaskContext taskContext
 * @param profileName Forms servlet URL.
 * @param runtimeMap runtime map<string,object> associated with form rendering.
 * return runtimeMap
 */
public Map<String, Object> renderHTMLForm (TaskContext taskContext, String profileName, Map<String,Object> runtimeMap);
```

Meer informatie over profielen van mobiele formulieren vindt u op [Een aangepast profiel maken](/help/forms/using/custom-profile.md).

## Nieuwe HTML-formulieren renderen en verzenden {#new-html-form-render-amp-submit-processes}

Geef voor elke bewerking &#39;AssignTask&#39; een Render- en een Verzendproces op met het formulier. Deze processen worden aangeroepen door TaskManager `renderForm`en `submitForm`API&#39;s voor aangepaste afhandeling. Semantiek van deze processen voor Nieuwe vorm van HTML:

### Een nieuw HTML-formulier renderen {#render-a-new-html-form}

Het nieuwe proces om HTML terug te geven, zoals elk teruggeven proces heeft de volgende I/O parameters -

Invoer - `taskContext`

Uitvoer - `runtimeMap`

Uitvoer - `outFormDoc`

Deze methode simuleert het exacte gedrag van `renderHTMLForm` API van de NewHTMLFormsService. Het roept de `generateFormURL` API voor het ophalen van de URL voor HTML-uitvoering van het formulier. Vervolgens wordt de runtimeMap gevuld met de volgende sleutel of waarden:

new html form = true

newHTMLFormURL = de URL die wordt geretourneerd na het aanroepen `generateFormURL` API.

### Een nieuw HTML-formulier verzenden {#submit-a-new-html-form}

Dit proces voor het verzenden van een nieuw HTML-formulier werkt met de volgende I/O-parameters -

Invoer - `taskContext`

Uitvoer - `runtimeMap`

Uitvoer - `outputDocument`

Het proces stelt de `outputDocument`aan de `inputDocument`opgehaald van `taskContext`.

## Standaardwaarden voor renderen of verzenden, processen en actieprofielen {#default-render-or-submit-processes-and-action-profiles}

Met de standaardservices Renderen en Verzenden kunt u ondersteuning inschakelen voor het renderen van PDF op een desktop en voor het HTML op mobiele apparaten (iPad).

### Standaardformulier voor renderen {#default-render-form}

Met dit proces wordt een XDP-formulier naadloos weergegeven op meerdere platforms. Het proces wint de gebruikersagent van terug `taskContext`en gebruikt de gegevens om het proces aan te roepen om HTML of PDF te renderen.

![default-render-vorm](assets/default-render-form.png)

### Standaardformulier verzenden {#default-submit-form}

Met dit proces wordt een XDP-formulier naadloos verzonden naar meerdere platforms. Het wint de gebruikersagent van terug `taskContext`en gebruikt de gegevens om het proces aan te roepen om of HTML of PDF te verzenden.

![default-submit-form](assets/default-submit-form.png)

## De weergave van mobiele formulieren wijzigen van PDF naar HTML {#switch-the-rendering-of-mobile-forms-from-pdf-to-html}

Browsers trekken de ondersteuning voor op NPAPI gebaseerde plug-ins, waaronder plug-ins voor Adobe Acrobat en Adobe Acrobat Reader, geleidelijk in. U kunt de weergave van mobiele formulieren van PDF naar HTML als volgt wijzigen:

1. Meld u als geldige gebruiker aan bij Workbench.
1. Selecteren **Bestand** > **Toepassingen ophalen**.

   Het dialoogvenster Toepassingen ophalen wordt geopend.

1. Selecteer de toepassingen waarvoor u de rendering van mobiele formulieren wilt wijzigen en klik op **OK**.
1. Open het proces waarvoor u de rendering wilt wijzigen.
1. Open het beoogde startpunt/de beoogde taak, ga naar de sectie Presentatie en gegevens en klik op **Actieprofielen beheren**.

   Het dialoogvenster Actieprofielen beheren wordt geopend.
1. Standaardrenderprofielconfiguraties wijzigen van PDF naar HTML en klikken op **OK**.
1. Controleer het proces.
1. Herhaal de stappen om de rendering voor andere processen te wijzigen.
1. Implementeer de toepassing die relevant is voor de processen die u hebt gewijzigd.

### Standaardactieprofiel {#default-action-profile}

Het standaard-actieprofiel heeft het XDP-formulier weergegeven als PDF. Dit gedrag is nu gewijzigd en gebruikt nu de processen Standaardformulier renderen en Standaardformulier verzenden.

Enkele vaak gestelde vragen over actieprofielen zijn als volgt:

![gen_question_b_20](assets/gen_question_b_20.png) **Welke processen Renderen/Verzenden zijn beschikbaar uit de doos?**

* Handleiding voor renderen (hulplijnen zijn afgekeurd)
* Formulierhulplijn renderen
* PDF-formulier renderen
* HTML-formulier renderen
* Nieuw HTML-formulier renderen (nieuw)
* Standaardformulier renderen (nieuw)

Equivalente verzendprocessen.

![gen_question_b_20](assets/gen_question_b_20.png) **Welke Profielen van de Actie zullen uit de doos beschikbaar zijn?**

Voor XDP Forms:

* Standaard (renderen/verzenden met de nieuwe processen Standaard renderen/verzenden)

![gen_question_b_20](assets/gen_question_b_20.png) **Wat moet door de procesontwerper worden gedaan om de vorm toe te laten om in HTML op een apparaat, en in PDF op een Desktop worden teruggegeven?**

Niets. Het standaardprofiel van de Actie wordt automatisch gekozen, en de wijze van het teruggeven wordt ook behandeld, automatisch.

![gen_question_b_20](assets/gen_question_b_20.png) **Wat moet er gebeuren om ervoor te zorgen dat het formulier in HTML op een bureaublad wordt weergegeven?**

De gebruiker moet het keuzerondje HTML selecteren voor het standaardprofiel.

![gen_question_b_20](assets/gen_question_b_20.png) **Zal er een upgrade-effect zijn op het wijzigen van het standaardgedrag van het actieprofiel?**

Ja, omdat de vorige renderings- en verzendservices die aan het standaardactieprofiel zijn gekoppeld verschillend waren, worden deze beschouwd als een aanpassing van de bestaande formulieren. Bij klikken **Standaardwaarden herstellen**, worden de gebrek teruggeeft en voorlegt de diensten in plaats daarvan geplaatst.

Als u de bestaande Render of Submit de diensten van de Vorm van de PDF of de gecreeerde douanediensten (bijvoorbeeld custom1) had gewijzigd, en nu de zelfde functionaliteit voor de vertoning van de HTML willen gebruiken. U moet de nieuwe renderen herhalen of de dienst voorleggen (zoals custom2) en gelijkaardige aanpassingen op die toepassen. Pas nu het actieprofiel voor uw XDP aan begin gebruikend de diensten custom2, in plaats van custom1 voor terug of voorleggen.

Wat moet door de procesontwerper worden gedaan om de vorm toe te laten om in HTML op een apparaat, en in PDF op een Desktop worden teruggegeven?
Wat moet door de procesontwerper worden gedaan om de vorm toe te laten om in HTML op een apparaat, en in PDF op een Desktop worden teruggegeven?
