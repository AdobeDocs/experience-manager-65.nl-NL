---
title: Veelgestelde vragen (FAQ) voor HTML5-formulieren
description: Veelgestelde vragen (FAQ) over indeling, ondersteuning van scripts en het bereik van HTML5-formulieren.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
docset: aem65
feature: HTML5 Forms,Mobile Forms
exl-id: 85c9315e-1bc8-44a9-937e-af6fc7cf54d1
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '2007'
ht-degree: 0%

---


# Veelgestelde vragen (FAQ) voor HTML5-formulieren{#frequently-asked-questions-faq-for-html-forms}

Er zijn een aantal veelgestelde vragen (FAQ) over indeling, ondersteuning van scripts en het bereik van HTML5-formulieren.

## Layout {#layout}

1. Waarom worden streepjescodes en handtekeningvelden niet in mijn formulier weergegeven?

   Antwoord: Streepjescodes en handtekeningvelden zijn niet relevant in scenario&#39;s voor HTML of mobiele apparaten. Deze velden worden weergegeven als een niet-interactief gebied. AEM Forms Designer biedt echter een nieuw veld voor het schrijven van handtekeningen dat kan worden gebruikt in plaats van een handtekeningveld. Men kan a [&#x200B; douanewidget &#x200B;](../../forms/using/custom-widgets.md) voor streepjescodes ook toevoegen en het integreren.

1. Wordt RTF-tekst ondersteund voor het XFA-tekstveld?

   Antwoord: Het XFA-veld, dat rijke inhoud in AEM Forms Designer toestaat, wordt niet ondersteund en wordt weergegeven als normale tekst zonder ondersteuning voor het opmaken van de tekst vanuit de gebruikersinterface. Daarnaast worden XFA-velden met de eigenschap combinatie weergegeven als een normaal veld, hoewel er nog steeds beperkingen zijn voor het aantal toegestane tekens op basis van de waarde van combinatie-cijfers.

1. Zijn er beperkingen met betrekking tot het gebruik van herhaalbare subformulieren?

   Antwoord: Herhalbare subformulieren moeten een beginaantal van 1 of meer hebben. Herhalbare subformulieren met een beginaantal van nul worden niet ondersteund. U kunt er ook voor kiezen een herhaalbaar subformulier te gebruiken en het niet weer te geven wanneer het formulier wordt geladen. Om het gebruiksgeval te bereiken:

   1. Stel het aanvankelijke aantal van het herhaalbare subformulier in op 1.

      ![&#x200B; eerste-telling &#x200B;](assets/intial-count.png)

   1. Gebruik de initialisatiegebeurtenis van het formulier om het primaire exemplaar van het subformulier te verbergen. De onderstaande code verbergt bijvoorbeeld het primaire exemplaar van Subform bij initialisatie van het formulier. Het verifieert ook het app type om ervoor te zorgen dat het manuscript slechts op de cliëntkant wordt uitgevoerd:

      ```javascript
      if ((xfa.host.appType == "HTML 5" || xfa.host.appType == "Exchange-Pro" || xfa.host.appType == "Reader")&&(_RepeatSubform.count == 1)&&(form1.Page1.Subform1.RepeatSubform.Key.rawValue == null)) {
      RepeatSubform.presence = "hidden";
      }
      ```

   1. Open het script om een exemplaar van het subformulier toe te voegen voor bewerking. Voeg de code zoals hieronder toe om een exemplaar van het Subform manuscript toe te voegen.

      De onderstaande code controleert het verborgen exemplaar van het subformulier. Als het verborgen exemplaar van het subformulier wordt gevonden, verwijdert u het verborgen exemplaar van het subformulier en voegt u een nieuw exemplaar van het subformulier in. Als het verborgen exemplaar van het subformulier niet wordt gevonden, voegt u gewoon een nieuw exemplaar van het subformulier in.

      ```javascript
      if (RepeatSubform.presence == "hidden")
      {
      RepeatSubform.instanceManager.insertInstance(0);
      RepeatSubform.instanceManager.removeInstance(1);
      }
      else
      {
      RepeatSubform.instanceManager.addInstance(1);
      }
      ```

   1. Open het script om een exemplaar van het subformulier te verwijderen en te bewerken. Voeg de volgende code toe om een exemplaar van het Subform-script te verwijderen.

      De code controleert het aantal subformulieren. Als het aantal subformulieren 1 is, wordt het subformulier door de code verborgen in plaats van het subformulier te verwijderen.

      ```javascript
      if (RepeatSubform.instanceManager.count == 1) {
      RepeatSubform.presence = "hidden";
      } else {
      RepeatSubform.instanceManager.removeInstance(RepeatSubform.instanceManager.count - 1);
      }
      ```

   1. Open de gebeurtenis presubmit van het formulier voor bewerking. Voeg het volgende script toe aan de gebeurtenis om het verborgen exemplaar van het script te verwijderen voordat u het bewerkt. Hiermee voorkomt u dat gegevens van het verborgen subformulier bij verzending worden verzonden.

      ```javascript
      if(RepeatSubform.instanceManager.count == 1 && RepeatSubform.presence == "hidden") {
      RepeatSubform.instanceManager.removeInstance(0);
      }
      ```

1. Zijn er beperkingen met betrekking tot het gebruik van verborgen subformulieren?

   Antwoord: Een verborgen subformulier met een complexe hiërarchie die over pagina&#39;s wordt gesplitst, veroorzaakt problemen met de indeling. Als tussenoplossing kunt u het subformulier in eerste instantie zichtbaar markeren en het vervolgens verbergen in een initialisatiescript op basis van logica of gegevens.

1. Waarom wordt tekst afgekapt of onjuist weergegeven in HTML5?

   Antwoord: Wanneer een Draw- of bijschrifttekstelement onvoldoende ruimte heeft om inhoud weer te geven, wordt de tekst afgekapt weergegeven in mobiele formulieruitvoering. Deze afkapping is ook zichtbaar in de ontwerpweergave van AEM Forms Designer. Hoewel deze afkapping kan worden afgehandeld in de PDF, kan deze niet worden afgehandeld in de HTML5-formulieren. Om dit probleem te voorkomen, moet u voldoende ruimte vrijmaken voor Draw of Bijschrifttekst, zodat deze niet wordt afgekapt in de ontwerpmodus van de AEM Forms Designer.

1. Ik observeer layoutproblemen met betrekking tot ontbrekende inhoud of overlappende inhoud. Wat is de reden?

   Antwoord: Als er een Draw-tekstelement of een Draw-afbeeldingselement is samen met een ander overlappend element op dezelfde positie (bijvoorbeeld een rechthoek), is de Draw-tekstinhoud niet zichtbaar als deze later in de documentvolgorde komt (in de AEM Forms Designer-hiërarchieweergave). PDF ondersteunt transparante lagen, maar HTML/browsers bieden geen ondersteuning voor transparante lagen.

1. Waarom worden sommige lettertypen in het HTML-formulier anders weergegeven dan de lettertypen die bij het ontwerpen van het formulier worden gebruikt?

   Antwoord: HTML5 Forms staat het insluiten van fonts niet toe (in tegenstelling tot PDF forms waarin fonts zijn ingesloten in het formulier). Zorg ervoor dat de HTML-versie van een formulier beschikbaar is in de CRX Repository (AEM Content Repository) van de AEM Forms-server en op het apparaat waarop Designer is geïnstalleerd, zodat de-versie van het formulier naar behoren wordt weergegeven. Wanneer de lettertypen niet beschikbaar zijn in de CRX-opslagplaats van uw AEM Forms-server of op de locatie waar AEM Designer is geïnstalleerd, wordt het formulier weergegeven met terugvallettertypen.

1. Worden vAlign- en hAlign-kenmerken ondersteund in HTML-formulieren?

   Antwoord: Ja, de kenmerken vAlign en hAlign worden ondersteund. Het kenmerk vAlign wordt niet ondersteund in Internet Explorer en in velden met meerdere regels.

1. Ondersteunt HTML5-formulieren Hebreeuwse tekens?

   Antwoord: HTML5-formulieren ondersteunen Hebreeuwse tekens in alle browsers behalve Microsoft Internet Explorer.

1. Hebben HTML5-formulieren enige beperkingen op het numerieke veld?

   Antwoord: Ja, HTML5-formulieren hebben een paar beperkingen. Als het aantal cijfers groter is dan het aantal dat is opgegeven in de afbeeldingsvoorwaarde, worden de getallen niet gelokaliseerd en weergegeven in de Engelse landinstelling.

1. Waarom zijn HTML-formulieren groter dan PDF forms?

   Antwoord: Er zijn talloze tussenliggende gegevensstructuren en objecten zoals formulierdom, gegevensdom en indelingsstructuur vereist om een XDP naar een HTML-formulier te renderen.

   Voor PDF forms beschikt Adobe Acrobat over een ingebouwde XTG-engine voor het maken van tussenliggende gegevensstructuren en -objecten. Acrobat houdt zich ook bezig met layout en scripts.

   Voor HTML5-formulieren beschikken browsers niet over een ingebouwde XTG-engine om tussenliggende gegevensstructuren te maken, en hebben ze geen objecten van onbewerkte XDP-bytes. Voor HTML5-formulieren worden dus tussenstructuren gegenereerd op de server en naar de client verzonden. Op client gebruikt de op JavaScript gebaseerde script- en indelingsengine deze tussenstructuren.

   De grootte van de tussenliggende structuur is afhankelijk van de grootte van de oorspronkelijke XDP en de gegevens die met de XDP zijn samengevoegd.

1. Zijn er om het even welke beperkingen betreffende het gebruiken van lijsten in mijn xdp?

   Antwoord: Complexe tabellen veroorzaken problemen bij het renderen.

   * Sectie (SubformSet) binnen een tabel wordt niet ondersteund.
   * In sommige tabellen worden kop- of voettekstrijen gemarkeerd voor herhaling. Bij sommige problemen kan het splitsen van dergelijke tabellen over meerdere pagina&#39;s een rol spelen.

1. Zijn er beperkingen voor toegankelijke tabellen?

   Antwoord: Ja, toegankelijke tabellen hebben de volgende beperkingen:

   * Geneste tabellen en subformulieren in een tabel worden niet ondersteund.
   * Kopteksten worden alleen ondersteund voor de bovenste of linkerkolom van de tabel. Kopteksten worden niet ondersteund voor elementen in de middelste tabel. U kunt kopteksten op veelvoudige rij en kolomkopballen toepassen worden gesteund op voorwaarde dat al dergelijke rijen en kolommen samen met de hoogste rij of uiterst linkse kolom van de lijst zijn.
   * `Rowspan` en `colspan` van een willekeurige plaats binnen de lijst wordt niet gesteund.

   * U kunt geen instantie van rijen dynamisch toevoegen of verwijderen die elementen met rowspan waarde groter dan 1 bevatten.

1. Wat is de leesvolgorde van knopinfo en bijschrift voor schermlezers?

   Antwoord:
   * Als zowel het bijschrift als de knopinfo aanwezig zijn, wordt het enige bijschrift gelezen. Als het bijschrift niet beschikbaar is, wordt de knopinfo gelezen. U kunt ook de prioriteit voor het lezen in een XDP opgeven met behulp van formulierontwerper
   * Wanneer u de muisaanwijzer op een element plaatst, wordt knopinfo weergegeven. Als knopinfo niet beschikbaar is, wordt spraaktekst weergegeven. Als de spraaktekst niet beschikbaar is, wordt de veldnaam weergegeven.

1. Wanneer u de cursor op een veld plaatst, wordt knopinfo weergegeven. Hoe kan ik het uitschakelen?

   Antwoord: Als u knopinfo wilt uitschakelen wanneer u de muisaanwijzer aanwijst, selecteert u geen knopinfo in het deelvenster Toegankelijkheid van de Designer.

1. In Designer kan een gebruiker aangepaste weergave-eigenschappen van keuzerondjes en selectievakjes configureren. Wordt bij het weergeven van formulieren rekening gehouden met dergelijke aangepaste weergave-eigenschappen in HTML5-formulieren?

   Antwoord: HTML5-formulieren negeren de aangepaste weergave-eigenschappen van keuzerondjes en selectievakjes. De keuzerondjes en selectievakjes worden weergegeven volgens de specificaties van de onderliggende browser.

1. Wanneer een HTML5-formulier wordt geopend in een ondersteunde browser, wordt de rand van de aangrenzende velden niet goed uitgelijnd of lijken subformulieren elkaar te overlappen. Als in Forms Designer een voorbeeld wordt weergegeven van hetzelfde HTML5-formulier, worden de velden en indeling niet verkeerd uitgelijnd en worden subformulieren op de juiste positie weergegeven. Hoe los je het probleem op?

   Antwoord: Wanneer een subformulier is ingesteld op Stroominhoud en het subformulier een verborgen randelement heeft, wordt de rand van de velden die ernaast worden geplaatst, niet correct uitgelijnd of worden subformulieren overlapt. U kunt het probleem verhelpen door de verborgen &lt;border>-elementen uit de bijbehorende XDP te verwijderen of er opmerkingen aan toe te voegen. Het volgende &lt;border>-element is bijvoorbeeld gemarkeerd als een opmerking:

   ```xml
               <!--<border>
                  <edge presence="hidden"/>
                  <corner thickness="0.175mm" presence="hidden"/>
               </border> -->
   ```

1. Waarom schermlezers niet correct werken met het datum-/tijdveldobject?

   Antwoord: Schermlezers ondersteunen geen datum-/tijdvelden. U kunt echter handmatig datum/tijd invoeren in het veld om de schermlezer de datum/tijd te laten lezen. Gebruik knopinfo of schermlezertekst om de gebruiker op te dragen handmatig datum/tijd voor het veld te selecteren.

1. Ondersteunt HTML5-formulieren weergavepatronen voor zwevende velden?

   Antwoord: HTML5-formulieren ondersteunen geen weergavepatronen voor zwevende velden.

1. Wat is de indeling van het veld Datum in HTML5 Forms?
Antwoord: Het veld Datum accepteert de ISO-indeling YYYY-MM-DD. Als u een datum in een andere notatie opgeeft, accepteert het veld Datum de opmaak pas als de gebruiker het veld met de Tab-toets verlaat.

### Scripts {#scripting}

1. Zijn er beperkingen in de implementatie van JavaScript voor HTML Forms?

   Antwoord:

   * Er is beperkte ondersteuning voor het script xfa.connectionSet. Voor connectionSet wordt alleen aanroep van de webservice op de server ondersteund. Voor gedetailleerde informatie, zie [&#x200B; Steun Scripting &#x200B;](/help/forms/using/scripting-support.md).
   * $record en $data worden niet ondersteund in clientscripts. Als de scripts echter zijn geschreven in een formReady, layoutReady-blok, werken de scripts nog steeds omdat deze gebeurtenissen op de server worden uitgevoerd.
   * Elementspecifieke scripts van XFA Draw, zoals het wijzigen van de Draw-tekst (of bijschrifttekst als er velden zijn), worden niet ondersteund.

1. Zijn er beperkingen in het gebruik van formCalc?

   Antwoord: momenteel wordt alleen een subset van de FormCalc-scripts geïmplementeerd. Voor gedetailleerde informatie, zie [&#x200B; Steun Scripting &#x200B;](/help/forms/using/scripting-support.md).

1. Is er een aanbevolen naamgevingsconventie en zijn er gereserveerde trefwoorden die moeten worden vermeden?

   Antwoord:
   * In AEM Forms Designer wordt aangeraden de naam van een object (zoals een subformulier of een tekstveld) niet met een onderstrepingsteken (_) te laten beginnen. Om onderstrepingsteken aan het begin van de naam te gebruiken, voeg een prefix na het onderstrepingsteken,_ &lt;prefix>&lt;objectname> toe.
   * Alle HTML5 formulieren-API&#39;s zijn gereserveerde trefwoorden. Voor douane APIs/functies, gebruik een naam die niet aan [&#x200B; HTML5 vormen APIs &#x200B;](/help/forms/using/scripting-support.md) identiek is.

1. Biedt HTML5-formulieren ondersteuning voor zwevende velden?

   Antwoord: Ja, HTML5 Forms ondersteunt zwevende velden. Als u zwevende velden wilt inschakelen, voegt u de volgende eigenschap toe aan het renderprofiel:

   >[!NOTE]
   >
   >De velden zijn standaard niet ingeschakeld voor zweven. Met Forms Designer kunt u de zwevende eigenschap van de velden instellen.

   1. Open de CRXde-lijst en navigeer naar het knooppunt `/content/xfaforms/profiles/default` .
   1. Voeg een eigenschap `mfDataDependentFloatingField` van het type String toe en stel de waarde van de eigenschap in op `true` .
   1. Klik **sparen allen**. De zwevende velden worden nu ingeschakeld voor de HTML Forms met behulp van het bijgewerkte renderprofiel.

      >[!NOTE]
      >
      >Als u zwevende velden wilt inschakelen voor een specifiek formulier zonder het renderingprofiel bij te werken, geeft u de eigenschap mfDataDependentFloatingField=true door als een URL-parameter.

1. Voeren HTML5-formulieren het initialisatiescript en de gebeurtenis form ready meerdere keren uit?

   Antwoord: Ja, de initialisatiescripts en de gebeurtenissen voor formulierklaar worden meerdere keren uitgevoerd, ten minste één keer op de server en één keer op de client. Er wordt voorgesteld om scripts als initialize of form:ready-gebeurtenissen te schrijven op basis van bepaalde bedrijfslogica (formulier- of veldgegevens), zodat de actie wordt uitgevoerd op basis van de status van de gegevens en de epidemische waarde (als de gegevens identiek zijn).

### XDP ontwerpen {#designing-xdp}

1. Zijn er gereserveerde trefwoorden in HTML5-formulieren?

   Antwoord: Alle HTML5 formulieren-API&#39;s zijn gereserveerde trefwoorden. Voor douane APIs/functies, gebruik een naam die niet aan [&#x200B; HTML5 vormen APIs &#x200B;](/help/forms/using/scripting-support.md) identiek is. Als u objectnamen gebruikt die met een onderstrepingsteken (_) beginnen, wordt het aangeraden naast gereserveerde trefwoorden ook een uniek voorvoegsel na het onderstrepingsteken toe te voegen. Door een voorvoegsel toe te voegen voorkomt u mogelijke conflicten met interne API&#39;s voor HTML5-formulieren. Bijvoorbeeld: `_fpField1`
