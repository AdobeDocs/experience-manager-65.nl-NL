---
title: Aangepaste weergaven maken voor adaptieve formuliervelden
description: De weergave van out-of-the-box componenten aanpassen in Adaptive Forms.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: customization
docset: aem65
exl-id: 770e257a-9ffd-46a4-9703-ff017ce9caed
solution: Experience Manager, Experience Manager Forms
role: User, Developer
feature: Adaptive Forms,Foundation Components
source-git-commit: 8a77756e8ba771c8de9950c2323bef8f23cc59b4
workflow-type: tm+mt
source-wordcount: '1692'
ht-degree: 0%

---

# Aangepaste weergaven maken voor adaptieve formuliervelden{#create-custom-appearances-for-adaptive-form-fields}

## Inleiding {#introduction}

De adaptieve vormen gebruiken het [ verschijningskader ](/help/forms/using/introduction-widgets.md) om u te helpen douaneverschijningen voor adaptieve vormgebieden tot stand brengen en een verschillende gebruikerservaring verstrekken. Vervang bijvoorbeeld keuzerondjes en selectievakjes door schakelknoppen of gebruik aangepaste jQuery-plug-ins om gebruikersinvoer in velden zoals telefoonnummers of e-mailadressen te beperken.

In dit document wordt uitgelegd hoe u met een jQuery-insteekmodule deze alternatieve ervaringen voor adaptieve formuliervelden kunt maken. Daarnaast wordt een voorbeeld weergegeven voor het maken van een aangepaste weergave voor numerieke veldcomponenten die worden weergegeven als een numerieke stapfunctie of schuifregelaar.

Laten we eerst kijken naar de belangrijkste termen en concepten die in dit artikel worden gebruikt.

**Verschijning** verwijst naar de stijl, de blik en het gevoel, en de organisatie van diverse elementen van een adaptief vormgebied. Het omvat gewoonlijk een etiket, een interactief gebied om input, een hulppictogram, en korte en lange beschrijvingen van het gebied te verstrekken. De aanpassing van de weergave die in dit artikel wordt besproken, is van toepassing op de weergave van het invoergebied van het veld.

**jQuery plugin** verstrekt een standaardmechanisme, dat op het kader van jQuery widget wordt gebaseerd, om een afwisselende verschijning uit te voeren.

**ClientLib** een cliënt-zijbibliotheeksysteem in AEM cliënt-zijverwerking die door complexe JavaScript en CSS code wordt gedreven. Zie Client-Side Libraries gebruiken voor meer informatie.

**Archetype** Een Maven toolkit van de projectemplating die als origineel patroon of model voor Gemaakt projecten wordt bepaald. Voor meer informatie, zie Inleiding aan Archetypes.

**Controle van de Gebruiker** verwijst naar het belangrijkste element in een widget die de waarde van het gebied bevat, en door het vormgevingskader wordt gebruikt om douane widget UI met het adaptieve vormmodel te binden.

## Stappen om een aangepaste weergave te maken {#steps-to-create-a-custom-appearance}

Op hoog niveau zijn de volgende stappen nodig om een aangepaste weergave te maken:

1. **creeer een project**: Creeer een Gemaakt project dat een inhoudspakket produceert om op AEM op te stellen.
1. **breid een bestaande widgetklasse** uit: breid een bestaande widgetklasse uit en treedt de vereiste klassen met voeten.
1. **creeer een cliëntbibliotheek**: Creeer a `clientLib: af.customwidget` bibliotheek en voeg de vereiste JavaScript en CSS dossiers toe.

1. **bouwt en installeert het project**: Bouw het Gemaakt project en installeer het geproduceerde inhoudspakket op AEM.
1. **werk de adaptieve vorm** bij: Werk de adaptieve eigenschappen van het vormgebied bij om de douaneverschijning te gebruiken.

### Een project maken {#create-a-project}

Een bepaald archetype is een uitgangspunt voor het creëren van een douaneverschijning. De details van het te gebruiken archetype zijn als volgt:

* **Bewaarplaats**: https://repo1.maven.org/maven2/com/adobe/
* **Identiteitskaart van Artefact**: douane-verschijning-archetype
* **Identiteitskaart van de Groep**: com.adobe.aemforms
* **Versie**: 1.0.4

Voer het volgende bevel uit om een lokaal project tot stand te brengen dat op archetype wordt gebaseerd:

`mvn archetype:generate -DarchetypeRepository=https://repo1.maven.org/maven2/com/adobe/ -DarchetypeGroupId=com.adobe.aemforms -DarchetypeArtifactId=custom-appearance-archetype -DarchetypeVersion=1.0.4`

De opdracht downloadt de Maven-plug-ins en archetype-informatie van de opslagplaats en genereert een project op basis van de volgende informatie:

* **groupId**: Identiteitskaart van de groep die door het geproduceerde Gemaakt project wordt gebruikt
* **artifactId**: Artefactidentiteitskaart die door het geproduceerde Geweven project wordt gebruikt.
* **versie**: Versie voor het geproduceerde Gemaakt project.
* **pakket**: Pakket gebruikt voor de dossierstructuur.
* **artifactName**: Artefactnaam van het geproduceerde AEM pakket.
* **packageGroup**: De groep van het pakket van het geproduceerde AEM pakket.
* **widgetName**: Naam van de verschijning die voor verwijzing wordt gebruikt.

Het gegenereerde project heeft de volgende structuur:

```java
─<artifactId>

 └───src

     └───main

         └───content

             └───jcr_root

                 └───etc

                     └───clientlibs

                         └───custom

                             └───<widgetName>

                                 ├───common [client library - af.customwidgets which encapsulates below clientLibs]

                                 ├───integration [client library - af.customwidgets.<widgetName>_widget which contains template files for integrating a third-party plugin with Adaptive Forms]

                                 │   ├───css

                                 │   └───javascript

                                 └───jqueryplugin [client library - af.customwidgets.<widgetName>_plugin which holds the third-party plugins and related dependencies]

                                     ├───css

                                     └───javascript
```

### Een bestaande widgetklasse uitbreiden {#extend-an-existing-widget-class}

Zodra het projectmalplaatje wordt gecreeerd, doe de volgende veranderingen, zoals vereist:

1. Neem de afhankelijkheid van de externe plug-in van het project op.

   1. Plaats de externe of aangepaste jQuery-plug-ins in de map `jqueryplugin/javascript` en de bijbehorende CSS-bestanden in de map `jqueryplugin/css` . Zie de JS- en CSS-bestanden in de map `jqueryplugin/javascript and jqueryplugin/css` voor meer informatie.

   1. Wijzig de `js.txt` - en `css.txt` -bestanden om eventuele extra JavaScript- en CSS-bestanden van de jQuery-insteekmodule op te nemen.

1. Integreer de externe insteekmodule met het framework om interactie mogelijk te maken tussen het aangepaste weergaveframework en de jQuery-insteekmodule. De nieuwe widget werkt alleen nadat u de volgende functies hebt uitgebreid of genegeerd.

<table>
 <tbody>
  <tr>
   <td><strong>Functie</strong></td>
   <td><strong>Beschrijving</strong></td>
  </tr>
  <tr>
   <td><code>render</code></td>
   <td>De renderfunctie retourneert het jQuery-object voor het standaard HTML-element van de widget. Het standaardelement van HTML zou van brandpuntsafhankelijk type moeten zijn. Bijvoorbeeld <code>&lt;a&gt;</code> , <code>&lt;input&gt;</code> en <code>&lt;li&gt;</code> . Het geretourneerde element wordt gebruikt als <code>$userControl</code> . Als de <code>$userControl</code> bovenstaande beperking opgeeft, werken de functies van de <code>AbstractWidget</code> -klasse zoals verwacht, anders vereisen sommige gemeenschappelijke API's (focus, klik) wijzigingen. </td>
  </tr>
  <tr>
   <td><code>getEventMap</code></td>
   <td>Retourneert een kaart om HTML-gebeurtenissen om te zetten in XFA-gebeurtenissen. <br /> <code class="code">&lbrace;
      blur: XFA_EXIT_EVENT,
      &rbrace;</code><br /> In dit voorbeeld wordt getoond dat <code>blur</code> een HTML-gebeurtenis is en <code>XFA_EXIT_EVENT</code> de bijbehorende XFA-gebeurtenis. </td>
  </tr>
  <tr>
   <td><code>getOptionsMap</code></td>
   <td>Retourneert een kaart met details over de handeling die moet worden uitgevoerd bij de wijziging van een optie. De sleutels zijn de opties die aan widget worden verstrekt en de waarden zijn functies die worden geroepen wanneer een verandering in de optie wordt ontdekt. De widget biedt handlers voor alle algemene opties (behalve <code>value</code> en <code>displayValue</code> ).</td>
  </tr>
  <tr>
   <td><code>getCommitValue</code></td>
   <td>Het jQuery-widgetframework laadt de functie wanneer de waarde van de jQuery-widget in het XFA-model wordt opgeslagen (bijvoorbeeld bij afsluitgebeurtenis van een tekstveld). De implementatie moet de waarde retourneren die is opgeslagen in de widget. De handler krijgt de nieuwe waarde voor de optie.</td>
  </tr>
  <tr>
   <td><code>showValue</code></td>
   <td>Standaard wordt in XFA bij Enter de <code>rawValue</code> van het veld weergegeven. Deze functie wordt aangeroepen om de <code>rawValue</code> aan de gebruiker te tonen. </td>
  </tr>
  <tr>
   <td><code>showDisplayValue</code></td>
   <td>Standaard wordt in XFA bij afsluitgebeurtenis de <code>formattedValue</code> van het veld weergegeven. Deze functie wordt aangeroepen om de <code>formattedValue</code> aan de gebruiker te tonen. </td>
  </tr>
 </tbody>
</table>

1. Werk het JavaScript-bestand naar wens bij in de map `integration/javascript` .

   * Vervang de tekst `__widgetName__` door de werkelijke naam van de widget.
   * Breid de widget uit van een geschikte buitenste widgetklasse. In de meeste gevallen is dit de klasse widget die overeenkomt met de bestaande widget die wordt vervangen. De naam van de bovenliggende klasse wordt op meerdere locaties gebruikt. Het wordt daarom aanbevolen naar alle instanties van de tekenreeks `xfaWidget.textField` in het bestand te zoeken en deze te vervangen door de werkelijk gebruikte bovenliggende klasse.
   * Breid de `render` methode uit om een afwisselende UI te verstrekken. Dit is de locatie vanwaar de jQuery-insteekmodule wordt aangeroepen om de gebruikersinterface of het interactiegedrag bij te werken. De methode `render` moet een element met gebruikersbesturing retourneren.

   * Breid de methode `getOptionsMap` uit om opties te overschrijven die worden beïnvloed door een wijziging in de widget. De functie retourneert een toewijzing die details bevat voor de actie die moet worden uitgevoerd bij wijziging van een optie. De sleutels zijn de opties die aan widget worden verstrekt en de waarden zijn de functies die worden geroepen wanneer een verandering in de optie wordt ontdekt.
   * De methode `getEventMap` wijst gebeurtenissen toe die door de widget worden geactiveerd, met de gebeurtenissen die door het adaptieve formuliermodel worden vereist. De standaardwaarde wijst standaard HTML-gebeurtenissen voor de standaardwidget toe en moet worden bijgewerkt als een alternatieve gebeurtenis wordt geactiveerd.
   * De `showDisplayValue` en `showValue` passen de weergave- en bewerkingsafbeeldingsvoorwaarde toe en kunnen worden overschreven voor een ander gedrag.

   * De `getCommitValue` methode wordt geroepen door het adaptieve vormenkader wanneer de `commit` gebeurtenis voorkomt. Over het algemeen is dit de afsluitgebeurtenis, behalve voor de vervolgkeuzelijst, het keuzerondje en de selectievakjes (waar deze voorkomt bij wijziging). Voor meer informatie, zie [ Aangepaste Uitdrukkingen van Forms ](../../forms/using/adaptive-form-expressions.md#p-value-commit-script-p).

   * Het sjabloonbestand biedt voorbeeldimplementatie voor verschillende methoden. Verwijder methoden die niet moeten worden uitgebreid.

### Een clientbibliotheek maken {#create-a-client-library}

Het voorbeeldproject dat door het Maven archetype wordt geproduceerd leidt automatisch tot vereiste cliëntbibliotheken, en verpakt hen in een cliëntbibliotheek met een categorie `af.customwidgets`. De JavaScript- en CSS-bestanden die beschikbaar zijn in de `af.customwidgets` worden automatisch opgenomen bij uitvoering.

### Samenstellen en installeren {#build-and-install}

Om het project te bouwen, voer het volgende bevel op shell uit om een pakket van CRX te produceren dat op de AEM server moet worden geïnstalleerd.

`mvn clean install`

>[!NOTE]
>
>Het beheerde project verwijst naar een externe opslagplaats binnen het POM-bestand. Dit is alleen ter referentie en volgens de Maven-standaarden wordt de opslagplaats-informatie vastgelegd in het `settings.xml` -bestand.

### Het aangepaste formulier bijwerken {#update-the-adaptive-form}

De aangepaste weergave toepassen op een adaptief formulierveld:

1. Open het adaptieve formulier in de bewerkingsmodus.
1. Open de **dialoog van het Bezit** voor het gebied waarop u de douaneverschijning wilt toepassen.
1. In het **Stijlvolle** lusje, werk het `CSS class` bezit bij om de verschijningsnaam in het `widget_<widgetName>` formaat toe te voegen. Bijvoorbeeld: **widget_numericstepper**

## Voorbeeld: een aangepaste weergave maken   {#sample-create-a-custom-appearance-nbsp}

Bekijk nu een voorbeeld om een douaneverschijning voor een numeriek gebied tot stand te brengen om als numerieke stapper of schuif te verschijnen. Voer de volgende stappen uit:

1. Voer het volgende bevel uit om een lokaal project tot stand te brengen dat op Maven archetype wordt gebaseerd:

   `mvn archetype:generate -DarchetypeRepository=https://repo1.maven.org/maven2/com/adobe/ -DarchetypeGroupId=com.adobe.aemforms -DarchetypeArtifactId=custom-appearance-archetype -DarchetypeVersion=1.0.4`

   U wordt gevraagd waarden op te geven voor de volgende parameters.
   *de waarden die in deze steekproef worden gebruikt worden benadrukt in vette letters*.

   `Define value for property 'groupId': com.adobe.afwidgets`

   `Define value for property 'artifactId': customWidgets`

   `Define value for property 'version': 1.0.1-SNAPSHOT`

   `Define value for property 'package': com.adobe.afwidgets`

   `Define value for property 'artifactName': customWidgets`

   `Define value for property 'packageGroup': adobe/customWidgets`

   `Define value for property 'widgetName': numericStepper`

1. Navigeer naar de map `customWidgets` (opgegeven waarde voor de eigenschap `artifactID` ) en voer de volgende opdracht uit om een Eclipse-project te genereren:

   `mvn eclipse:eclipse`

1. Open het gereedschap Eclipse en voer de volgende handelingen uit om het Eclipse-project te importeren:

   1. Selecteer **[!UICONTROL File > Import > Existing Projects into Workspace]** .

   1. Blader naar de map waarin u de opdracht `archetype:generate` hebt uitgevoerd en selecteer deze.

   1. Klik op **[!UICONTROL Finish]**.

      ![ eclipse-screenshot ](assets/eclipse-screenshot.png)

1. Selecteer de widget die voor de aangepaste weergave moet worden gebruikt. In dit voorbeeld wordt de volgende numerieke stepper-widget gebruikt:

   [ https://www.jqueryscript.net/form/User-Friendly-Number-Input-Spinner-with-jQuery-Bootstrap.html](https://www.jqueryscript.net/form/User-Friendly-Number-Input-Spinner-with-jQuery-Bootstrap.html)

   Controleer in het Eclipse-project de insteekcode in het `plugin.js` -bestand om te controleren of deze voldoet aan de vereisten voor de weergave. In dit voorbeeld voldoet de weergave aan de volgende vereisten:

   * De numerieke stapfunctie moet worden uitgebreid vanaf `- $.xfaWidget.numericInput` .
   * De methode `set value` van de widget stelt de waarde in nadat de focus zich op het veld bevindt. Dit is een verplichte vereiste voor een adaptieve formulierwidget.
   * De methode `render` moet worden overschreven om de methode `bootstrapNumber` aan te roepen.

   * Er is geen andere afhankelijkheid van de plug-in dan de hoofdbroncode van de plug-in.
   * In het voorbeeld wordt geen stijl toegepast op de stapfunctie. Er is dus geen extra CSS vereist.
   * Het object `$userControl` moet beschikbaar zijn voor de methode `render` . Dit is een veld van het type `text` dat is gekloond met de insteekmodulecode.

   * De knoppen **+** en **-** moeten worden uitgeschakeld wanneer het veld wordt uitgeschakeld.

1. Vervang de inhoud van de plug-in `bootstrap-number-input.js` (jQuery) door de inhoud van het bestand `numericStepper-plugin.js` .
1. Voeg in het `numericStepper-widget.js` -bestand de volgende code toe om de rendermethode te overschrijven om de insteekmodule aan te roepen en het `$userControl` -object te retourneren:

   ```javascript
   render : function() {
        var control = $.xfaWidget.numericInput.prototype.render.apply(this, arguments);
        var $control = $(control);
        var controlObject;
        try{
            if($control){
            $control.bootstrapNumber();
            var id = $control.attr("id");
            controlObject = $("#"+id);
            }
        }catch (exc){
             console.log(exc);
        }
        return controlObject;
   }
   ```

1. Overschrijf in het bestand `numericStepper-widget.js` de eigenschap `getOptionsMap` om de toegangsoptie te overschrijven en verberg de knoppen + en - in de uitgeschakelde modus.

   ```javascript
   getOptionsMap: function(){
       var parentOptionsMap = $.xfaWidget.numericInput.prototype.getOptionsMap.apply(this,arguments),
   
       newMap = $.extend({},parentOptionsMap,
   
        {
   
              "access": function(val) {
              switch(val) {
                 case "open" :
                   this.$userControl.removeAttr("readOnly");
                   this.$userControl.removeAttr("aria-readonly");
                   this.$userControl.removeAttr("disabled");
                   this.$userControl.removeAttr("aria-disabled");
                   this.$userControl.parent().find(".input-group-btn button").prop('disabled',false);
                   break;
                 case "nonInteractive" :
                 case "protected" :
                   this.$userControl.attr("disabled", "disabled");
                   this.$userControl.attr("aria-disabled", "true");
                   this.$userControl.parent().find(".input-group-btn button").prop('disabled',true);
                   break;
                case "readOnly" :
                   this.$userControl.attr("readOnly", "readOnly");
                   this.$userControl.attr("aria-readonly", "true");
                   this.$userControl.parent().find(".input-group-btn button").prop('disabled',true);
                   break;
               default :
                   this.$userControl.removeAttr("disabled");
                   this.$userControl.removeAttr("aria-disabled");
                   this.$userControl.parent().find(".input-group-btn button").prop('disabled',false);
                   break;
             }
          },
      });
      return newMap;
    }
   ```

1. Sla de wijzigingen op, navigeer naar de map met het `pom.xml` -bestand en voer de volgende Maven-opdracht uit om het project te maken:

   `mvn clean install`

1. Installeer het pakket met AEM Package Manager.

1. Open het adaptieve formulier in de bewerkingsmodus waarop u de aangepaste weergave wilt toepassen en voer de volgende handelingen uit:

   1. Klik met de rechtermuisknop op het veld waarop u de weergave wilt toepassen en klik op **[!UICONTROL Edit]** om het dialoogvenster Component bewerken te openen.

   1. Werk op het tabblad Stijl de eigenschap **[!UICONTROL CSS class]** bij om `widget_numericStepper` toe te voegen.

De nieuwe weergave die u hebt gemaakt, is nu beschikbaar voor gebruik.
