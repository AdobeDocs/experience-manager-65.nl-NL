---
title: Nieuwe renderservice en verzendservice
seo-title: Nieuwe renderservice en verzendservice
description: Definieer de renderings- en verzendservices in Workbench om XDP-formulieren te renderen als HTML of PDF, afhankelijk van het apparaat waartoe deze toegang hebben.
seo-description: Definieer de renderings- en verzendservices in Workbench om XDP-formulieren te renderen als HTML of PDF, afhankelijk van het apparaat waartoe deze toegang hebben.
uuid: 7f8348a1-753c-4dab-87d5-4a4a301198dd
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: 6a32d240-c6a6-4937-a31f-7a5ec3c60b1f
docset: aem65
translation-type: tm+mt
source-git-commit: 56c6cfd437ef185336e81373bd5f758205b96317
workflow-type: tm+mt
source-wordcount: '929'
ht-degree: 0%

---


# Nieuwe render- en verzendservice{#new-render-and-submit-service}

## Inleiding {#introduction}

Als u in Workbench een bewerking `AssignTask` definieert, geeft u een bepaald formulier (XDP- of PDF-formulier) op. Geef ook een set services voor renderen en verzenden op via een actieprofiel.

Een XDP kan worden weergegeven als een PDF-formulier of een HTML-formulier. De nieuwe mogelijkheden omvatten de capaciteit:

* Een XDP-formulier weergeven en verzenden als HTML
* Een XDP-formulier weergeven en verzenden als PDF-bestand op het bureaublad en als HTML op mobiele apparaten (bijvoorbeeld een iPad)

### Nieuwe HTML Forms-service {#new-html-forms-service}

De nieuwe HTML Forms-service maakt gebruik van de nieuwe functie in Forms ter ondersteuning van de rendering van XDP-formulieren als HTML. De nieuwe HTML Forms-service stelt de volgende methoden beschikbaar:

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

## Nieuwe processen voor het renderen en verzenden van HTML-formulieren {#new-html-form-render-amp-submit-processes}

Geef voor elke bewerking &#39;AssignTask&#39; een Render- en een Verzendproces op met het formulier. Deze processen worden aangeroepen door TaskManager `renderForm`en `submitForm`APIs om douanebehandeling toe te staan. Semantiek van deze processen voor Nieuwe HTML-vorm:

### Een nieuw HTML-formulier weergeven {#render-a-new-html-form}

Het nieuwe proces voor het renderen van HTML heeft, net als elk renderproces, de volgende I/O-parameters -

Invoer - `taskContext`

Uitvoer - `runtimeMap`

Uitvoer - `outFormDoc`

Deze methode simuleert het nauwkeurige gedrag van `renderHTMLForm` API van NewHTMLFormsService. De API `generateFormURL` wordt aangeroepen om de URL voor HTML-uitvoering van het formulier op te halen. Vervolgens wordt de runtimeMap gevuld met de volgende sleutel of waarden:

new html form = true

newHTMLFormURL = de URL die wordt geretourneerd na het aanroepen van de `generateFormURL`-API.

### Een nieuw HTML-formulier {#submit-a-new-html-form} verzenden

Dit proces voor het verzenden van een nieuw HTML-formulier werkt met de volgende I/O-parameters -

Invoer - `taskContext`

Uitvoer - `runtimeMap`

Uitvoer - `outputDocument`

Het proces plaatst `outputDocument`aan `inputDocument`teruggewonnen van `taskContext`.

## Standaard renderen- of verzendprocessen en actieprofielen {#default-render-or-submit-processes-and-action-profiles}

Met de standaardservices Renderen en Verzenden kunt u ondersteuning inschakelen voor het weergeven van PDF&#39;s op een bureaublad en van HTML op mobiele apparaten (iPad).

### Standaardformulier voor renderen {#default-render-form}

Met dit proces wordt een XDP-formulier naadloos weergegeven op meerdere platforms. Het proces wint de gebruikersagent van `taskContext` terug, en gebruikt de gegevens om het proces te roepen om of HTML of PDF terug te geven.

![default-render-vorm](assets/default-render-form.png)

### Standaardformulier {#default-submit-form} verzenden

Met dit proces wordt een XDP-formulier naadloos verzonden naar meerdere platforms. De gebruikersagent wordt opgehaald uit `taskContext`en de gegevens worden gebruikt om het proces aan te roepen om HTML of PDF te verzenden.

![default-submit-form](assets/default-submit-form.png)

## De weergave van mobiele formulieren overschakelen van PDF naar HTML {#switch-the-rendering-of-mobile-forms-from-pdf-to-html}

Browsers trekken de ondersteuning voor op NPAPI gebaseerde plug-ins, waaronder plug-ins voor Adobe Acrobat en Adobe Acrobat Reader, geleidelijk in. U kunt de weergave van mobiele formulieren van PDF naar HTML als volgt wijzigen:

1. Meld u als geldige gebruiker aan bij Workbench.
1. Selecteer **Bestand** > **Toepassingen ophalen**.

   Het dialoogvenster Toepassingen ophalen wordt geopend.

1. Selecteer de toepassingen waarvoor u de rendering van mobiele formulieren wilt wijzigen en klik op **OK**.
1. Open het proces waarvoor u de rendering wilt wijzigen.
1. Open het beoogde startpunt/de beoogde taak, navigeer naar de sectie Presentatie en gegevens en klik op **Actieprofielen beheren**.

   Het dialoogvenster Actieprofielen beheren wordt geopend.
1. Wijzig de standaardrenderprofielconfiguraties van PDF naar HTML en klik op **OK**.
1. Controleer het proces.
1. Herhaal de stappen om de rendering voor andere processen te wijzigen.
1. Implementeer de toepassing die relevant is voor de processen die u hebt gewijzigd.

### Standaardactieprofiel {#default-action-profile}

Met het standaardactieprofiel wordt het XDP-formulier weergegeven als PDF. Dit gedrag is nu gewijzigd en gebruikt nu de processen Standaardformulier renderen en Standaardformulier verzenden.

Enkele vaak gestelde vragen over actieprofielen zijn als volgt:

![gen_question_b_20](assets/gen_question_b_20.png) **Welke processen Renderen/Verzenden beschikbaar zullen zijn uit de doos?**

* Handleiding voor renderen (hulplijnen zijn afgekeurd)
* Formulierhulplijn renderen
* PDF-formulier renderen
* HTML-formulier renderen
* Nieuw HTML-formulier renderen (nieuw)
* Standaardformulier renderen (nieuw)

Equivalente verzendprocessen.

![gen_question_b_20](assets/gen_question_b_20.png) **Welke Profielen van de Actie uit de doos beschikbaar zullen zijn?**

Voor XDP Forms:

* Standaard (renderen/verzenden met de nieuwe processen Standaard renderen/verzenden)

![gen_question_b_20](assets/gen_question_b_20.png) **Wat moet de procesontwerper doen om ervoor te zorgen dat het formulier in HTML op een apparaat en in PDF op een bureaublad kan worden weergegeven?**

Niets. Het standaardactieprofiel wordt automatisch gekozen en de renderingmodus wordt automatisch ook geactiveerd.

![gen_question_b_20](assets/gen_question_b_20.png) **Wat moet er gebeuren om ervoor te zorgen dat het formulier in HTML op een bureaublad wordt weergegeven?**

De gebruiker moet het HTML-keuzerondje voor het standaardprofiel selecteren.

![gen_question_b_20](assets/gen_question_b_20.png) **Zal er om het even welk verbeteringseffect op het veranderen van het standaardgedrag van het actieprofiel zijn?**

Ja, omdat de vorige renderings- en verzendservices die aan het standaardactieprofiel zijn gekoppeld verschillend waren, worden deze beschouwd als een aanpassing van de bestaande formulieren. Als u op **Standaardwaarden herstellen** klikt, worden de standaardservices voor renderen en verzenden ingesteld.

Als u de bestaande services voor het renderen of verzenden van PDF-formulieren of aangepaste services (zoals custom1) hebt gewijzigd, wilt u nu dezelfde functionaliteit gebruiken voor HTML-uitvoering. U moet de nieuwe renderen herhalen of de dienst voorleggen (zoals custom2) en gelijkaardige aanpassingen op die toepassen. Pas nu het actieprofiel voor uw XDP aan begin gebruikend de diensten custom2, in plaats van custom1 voor terug of voorleggen.

Wat moet de procesontwerper doen om ervoor te zorgen dat het formulier in HTML op een apparaat en in PDF op een bureaublad kan worden weergegeven?
Wat moet de procesontwerper doen om ervoor te zorgen dat het formulier in HTML op een apparaat en in PDF op een bureaublad kan worden weergegeven?
