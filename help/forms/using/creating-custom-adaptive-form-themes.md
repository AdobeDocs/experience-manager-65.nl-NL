---
title: Aangepaste aangepaste formulierthema's maken
description: Een adaptief formulierthema is een Adobe Experience Manager-clientbibliotheek waarmee u de stijlen (look and feel) voor een adaptief formulier kunt definiëren. Leer hoe u aangepaste formulierthema's kunt maken.
content-type: reference
topic-tags: customization
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 73b0057f-082d-4502-90e2-5e41b52c1185
solution: Experience Manager, Experience Manager Forms
source-git-commit: a28883778c5e8fb90cbbd0291ded17059ab2ba7e
workflow-type: tm+mt
source-wordcount: '790'
ht-degree: 0%

---

# Aangepaste aangepaste formulierthema&#39;s maken {#creating-custom-adaptive-form-themes}

>[!CAUTION]
>
>Adobe Experience Manager (AEM) Forms levert de [Thema-editor](/help/forms/using/themes.md) mogelijkheden om adaptieve formulieren te maken en te wijzigen [thema&#39;s](/help/forms/using/themes.md). Voer de stappen in dit artikel alleen uit als u een upgrade hebt uitgevoerd van een versie die niet [Thema-editor](/help/forms/using/themes.md) en u hebt een bestaande investering in thema&#39;s die met Minder/CSS dossiers (pre-thema redacteursmethode) worden gecreeerd.

## Vereisten {#prerequisites}

* Kennis van het LESS-framework (Leaner CSS)
* Een clientbibliotheek maken in Adobe Experience Manager
* [Een adaptieve formuliersjabloon maken](/help/forms/using/custom-adaptive-forms-templates.md) voor het gebruik van het thema dat u maakt

## Adaptief formulierthema {#adaptive-form-theme}

An **adaptief formulierthema** Dit is een AEM clientbibliotheek die u gebruikt om de stijlen (look and feel) voor een adaptief formulier te definiëren.

U maakt een **adaptieve sjabloon** en past u het thema toe op de sjabloon. U kunt deze aangepaste sjabloon vervolgens gebruiken om een **adaptieve vorm**.

![Adaptief formulier en clientbibliotheek](assets/hierarchy.png)

## Een adaptief formulierthema maken {#to-create-an-adaptive-form-theme}

>[!NOTE]
>
>De volgende procedure wordt beschreven gebruikend steekproefnamen voor AEM voorwerpen zoals knopen, eigenschappen, en omslagen.
>
>Als u deze stappen met de namen uitvoert, zou het resulterende malplaatje aan de volgende momentopname gelijkaardig moeten lijken:

![Adaptieve formulieropname met houtthema&#39;s](assets/thumbnail.png)
**Afbeelding:** *Forest Theme Sample*

1. Een knooppunt van het type maken `cq:ClientLibraryFolder` onder de `/apps`knooppunt.

   Maak bijvoorbeeld het volgende knooppunt:

   `/apps/myAfThemes/forestTheme`

1. Een multi-getaxeerde tekenreekseigenschap toevoegen `categories` naar het knooppunt en stel de waarde ervan op de juiste manier in.

   Stel de eigenschap bijvoorbeeld in op: `af.theme.forest`.

   ![Opname van CRX-opslagplaats](assets/3-2.png)

1. Twee mappen toevoegen `less` en `css`en een bestand `css.txt` op het knooppunt dat in stap 1 is gemaakt:

   * `less` map: bevat de `less` variabele bestanden waarin u de `less` variabelen en `less mixins` die worden gebruikt om de .css stijlen te beheren.

     Deze map bestaat uit `less` variabele bestanden, `less` bestanden mixen, `less` bestanden die stijlen definiëren met behulp van mixins en variabelen. En al deze `less` bestanden worden vervolgens geïmporteerd in styles.less.

   * `css`map: bevat de CSS-bestanden waarin u de statische stijlen definieert die in het thema moeten worden gebruikt.

   **Minder variabele bestanden**: Dit zijn de bestanden waarin u de variabelen definieert of overschrijft die worden gebruikt bij het definiëren van CSS-stijlen.

   Adaptieve formulieren bieden variabelen die buiten het vak vallen, zoals gedefinieerd in het volgende `.less` bestanden:

   * `/apps/clientlibs/fd/af/guidetheme/common/less/globalvariables.less`
   * `/apps/clientlibs/fd/af/guidetheme/common/less/layoutvariables.less`

   Adaptieve formulieren bevatten ook variabelen van derden die zijn gedefinieerd in:

   `/apps/clientlibs/fd/af/third-party/less/variables.less`

   U kunt de `less` U kunt deze variabelen overschrijven of u kunt nieuwe `less` variabelen.

   >[!NOTE]
   >
   >Geef tijdens het importeren van de bestanden van de mindere voorprocessor in de instructie import het relatieve pad van de bestanden op.

   Voorbeeld overschrijvende variabelen:

   ```css
   @button-background-color: rgb(19, 102, 44);
   @button-border-color: rgb(19, 102, 44);
   @button-border-size: 0px;
   @button-padding: 10px 15px;
   @button-font-color: #ffffff;
   ```

   Als u de opdracht `less`variabelen:

   1. Standaardadaptieve formuliervariabelen importeren:

      `/apps/clientlibs/fd/af/guidetheme/common/less/globalvariables.less/apps/clientlibs/fd/af/guidetheme/common/less/layoutvariables.less`

   1. Importeer vervolgens het bestand met de waarde Minder, dat overschreven variabelen bevat.

   Voorbeeld van nieuwe definities van variabelen:

   ```css
   @button-focus-bg-color: rgb(40, 208, 90);
   @button-hover-bg-color: rgb(30, 156, 67);
   ```

   **Minder gemengde bestanden:** U kunt de functies definiëren die variabelen als argumenten accepteren. De uitvoer van deze functies is de resulterende stijlen. Gebruik deze combinaties in verschillende stijlen, zodat u niet telkens CSS-stijlen hoeft te herhalen.

   Adaptieve formulieren bieden buitenste mixen die zijn gedefinieerd in:

   * `/apps/clientlibs/fd/af/guidetheme/common/less/adaptiveforms-mixins.less`

   Aangepaste formulieren bieden ook mengsels van derden, zoals gedefinieerd in:

   * `/apps/clientlibs/fd/af/third-party/less/mixins.less`

   Definitie van monstermix:

   ```css
   .rounded-corners (@radius) {
     -webkit-border-radius: @radius;
     -moz-border-radius: @radius;
     -ms-border-radius: @radius;
     -o-border-radius: @radius;
     border-radius: @radius;
   }
   
   .border(@color, @type, @size) {
      border: @color @size @type;
   }
   ```

   **Stijlen.bestand:** Gebruik dit bestand om alle `less` bestanden (variabelen, mixins, stijlen) die u in de clientbibliotheek moet gebruiken.

   In het volgende voorbeeld `styles.less` , kan de importinstructie in elke willekeurige volgorde worden geplaatst.

   De instructies voor het importeren van het volgende `.less` bestanden zijn verplicht:

   * `globalvariables.less`
   * `layoutvariables.less`
   * `components.less`
   * `layouts.less`

   ```css
   @import "../../../clientlibs/fd/af/guidetheme/common/less/globalvariables.less";
   @import "../../../clientlibs/fd/af/guidetheme/common/less/layoutvariables.less";
   @import "forestTheme-variables";
   @import "../../../clientlibs/fd/af/guidetheme/common/less/components.less";
   @import "../../../clientlibs/fd/af/guidetheme/common/less/layouts.less";
   
   /* custom styles */
   
   .guidetoolbar {
     input[type="button"], button, .button {
       .rounded-corners (@button-radius);
       &:hover {
         background-color: @button-hover-bg-color;
       }
       &:focus {
         background-color: @button-focus-bg-color;
       }
     }
   }
   
   form {
       background-image: url(../images/forest.png);
    background-repeat: no-repeat;
    background-size: 100%;
   }
   ```

   De `css.txt` bevat de paden van CSS-bestanden die voor de bibliotheek moeten worden gedownload.

   Bijvoorbeeld:

   ```javascript
   #base=/apps/clientlibs/fd/af/third-party/css
   bootstrap.css
   
   #base=less
   styles.less
   
   #base=/apps/clientlibs/fd/xfaforms/xfalib/css
   datepicker.css
   listboxwidget.css
   scribble.css
   dialog.css
   ```

   >[!NOTE]
   >
   >Het bestand styles.less is niet verplicht. Dit betekent dat u dit bestand niet hoeft te maken als u geen aangepaste stijlen, variabelen of mixen hebt gedefinieerd.
   >
   >Als u echter geen bestand style.less maakt, moet u de commentaarmarkering in het bestand css.txt op de volgende regel verwijderen:
   >
   >**`#base=less`**
   >
   >En becommentariëer de volgende lijn:
   >
   >**`styles.less`**

## Een thema in een adaptieve vorm gebruiken {#to-use-a-theme-in-an-adaptive-form}

Nadat u een adaptief formulierthema hebt gemaakt, voert u de volgende stappen uit om dit thema in een adaptieve vorm te gebruiken:

1. Het thema dat is gemaakt in [een adaptief formulierthema maken](/help/forms/using/creating-custom-adaptive-form-themes.md#p-to-create-an-adaptive-form-theme-p) sectie, een aangepaste pagina van type maken `cq:Component`.

   Bijvoorbeeld: `/apps/myAfCustomizations/myAfPages/forestPage`

   1. Voeg een `sling:resourceSuperType` eigenschap en de waarde ervan instellen als `fd/af/components/page/base`.

      ![Opname van CRX-opslagplaats](assets/1-2.png)

   1. Als u een thema op de pagina wilt gebruiken, moet u een bestand library.jsp dat met voeten wordt getreden, aan het knooppunt toevoegen.

      Vervolgens kunt u het thema importeren dat is gemaakt in Een adaptieve sectie voor formulierthema maken van dit artikel.

      Het volgende voorbeeldcodefragment importeert het `af.theme.forest` thema.

      ```jsp
      <%@include file="/libs/fd/af/components/guidesglobal.jsp"%>
      <cq:includeClientLib categories="af.theme.forest"/>
      ```

   1. **Optioneel**: Overschrijf op de aangepaste pagina de header.jsp, footer.jsp en de body.jsp, al naar gelang de vereisten.

1. Een aangepaste sjabloon maken (bijvoorbeeld: `/apps/myAfCustomizations/myAfTemplates/forestTemplate`) waarvan jcr:content verwijst naar de aangepaste pagina die in de vorige stap is gemaakt (bijvoorbeeld: `myAfCustomizations/myAfPages/forestPage)`.

   ![Opname van CRX-opslagplaats](assets/2-1.png)

1. Maak een adaptief formulier met de sjabloon die u in de vorige stap hebt gemaakt. De vormgeving van het adaptieve formulier wordt bepaald door het thema dat is gemaakt in de sectie Voor het maken van een adaptief formulierthema van dit artikel.
