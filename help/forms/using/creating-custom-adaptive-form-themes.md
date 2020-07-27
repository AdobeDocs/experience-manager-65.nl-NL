---
title: Aangepaste aangepaste formulierthema's maken
seo-title: Aangepaste aangepaste formulierthema's maken
description: Een adaptief formulierthema is een AEM-clientbibliotheek waarmee u de stijlen (look and feel) voor een adaptief formulier kunt definiëren. Leer hoe u aangepaste formulierthema's kunt maken.
seo-description: Een adaptief formulierthema is een AEM-clientbibliotheek waarmee u de stijlen (look and feel) voor een adaptief formulier kunt definiëren. Leer hoe u aangepaste formulierthema's kunt maken.
uuid: b25df10e-b07c-4e9d-a799-30f1c6fb3c44
content-type: reference
topic-tags: customization
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 437e6581-4eb1-4fbd-a6da-86b9c90cec89
translation-type: tm+mt
source-git-commit: 1343cc33a1e1ce26c0770a3b49317e82353497ab
workflow-type: tm+mt
source-wordcount: '825'
ht-degree: 0%

---


# Aangepaste aangepaste formulierthema&#39;s maken {#creating-custom-adaptive-form-themes}

>[!CAUTION]
>
>AEM Forms bieden de [Thema-editor](/help/forms/using/themes.md) de mogelijkheid om adaptieve [formulierthema](/help/forms/using/themes.md)&#39;s te maken en te wijzigen. Voer de stappen uit die in dit artikel worden vermeld, slechts als u van een versie hebt bevorderd die niet de Redacteur [van het](/help/forms/using/themes.md) Thema heeft en u een bestaande investering in thema&#39;s hebt die worden gecreeerd gebruikend Minder/CSS dossiers (pre-thema redacteursmethode).

## Vereisten {#prerequisites}

* Kennis van het LESS-framework (Leaner CSS)
* Een clientbibliotheek maken in Adobe Experience Manager
* [Een aangepaste formuliersjabloon](/help/forms/using/custom-adaptive-forms-templates.md) maken voor het gebruik van het thema dat u maakt

## Adaptief formulierthema {#adaptive-form-theme}

Een **adaptief formulierthema** is een AEM-clientbibliotheek waarmee u de stijlen (look and feel) voor een adaptief formulier kunt definiëren.

U maakt een **adaptieve sjabloon** en past het thema toe op de sjabloon. Vervolgens gebruikt u deze aangepaste sjabloon om een **adaptief formulier** te maken.

![Adaptief formulier en clientbibliotheek](assets/hierarchy.png)

## Een adaptief formulierthema maken {#to-create-an-adaptive-form-theme}

>[!NOTE]
>
>De volgende procedure wordt beschreven gebruikend steekproefnamen voor voorwerpen AEM zoals knoop, eigenschappen, en omslagen.
>
>Als u deze stappen met de namen uitvoert, zou het resulterende malplaatje aan de volgende momentopname gelijkaardig moeten lijken:

![Adaptieve formuliermomentopname](assets/thumbnail.png)**op basis van woud:** *Forest Theme Sample*

1. Maak een knooppunt van het type `cq:ClientLibraryFolder` onder het `/apps`knooppunt.

   Maak bijvoorbeeld het volgende knooppunt:

   `/apps/myAfThemes/forestTheme`

1. Voeg een multi-getaxeerde koordbezit `categories` aan de knoop toe en plaats geschikt zijn waarde.

   Stel de eigenschap bijvoorbeeld in op: `af.theme.forest`.

   ![Opname van CRX-opslagplaats](assets/3-2.png)

1. Voeg twee mappen `less` en `css``css.txt` een bestand toe aan het knooppunt dat in stap 1 wordt gemaakt:

   * `less` map: Bevat de `less` veranderlijke dossiers waarin u de `less` variabelen bepaalt en `less mixins` die worden gebruikt om de .css stijlen te beheren.

      Deze map bestaat uit `less` variabele bestanden, `less` mengbestanden, `less` bestanden die stijlen definiëren met behulp van mixins en variabelen. En al deze minder dossiers worden dan ingevoerd in styles.less.

   * `css`map: Bevat de CSS-bestanden waarin u de statische stijlen definieert die in het thema moeten worden gebruikt.

   **Minder variabelebestanden**: Dit zijn de bestanden waarin u de variabelen definieert of overschrijft die worden gebruikt bij het definiëren van CSS-stijlen.

   Adaptieve formulieren bieden OTB-variabelen die zijn gedefinieerd in de volgende bestanden zonder .less:

   * `/apps/clientlibs/fd/af/guidetheme/common/less/globalvariables.less`
   * `/apps/clientlibs/fd/af/guidetheme/common/less/layoutvariables.less`

   Adaptieve formulieren bevatten ook variabelen van derden, zoals gedefinieerd in:

   `/apps/clientlibs/fd/af/third-party/less/variables.less`

   U kunt de variabelen gebruiken waarvoor minder nodig is, maar u kunt ook deze variabelen overschrijven of nieuwe, minder variabelen maken.

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

   De `less`variabelen overschrijven:

   1. Standaardadaptieve formuliervariabelen importeren:

      `/apps/clientlibs/fd/af/guidetheme/common/less/globalvariables.less/apps/clientlibs/fd/af/guidetheme/common/less/layoutvariables.less`

   1. Importeer vervolgens het bestand met de waarde Minder, dat overschreven variabelen bevat.

   Voorbeeld van nieuwe definities van variabelen:

   ```css
   @button-focus-bg-color: rgb(40, 208, 90);
   @button-hover-bg-color: rgb(30, 156, 67);
   ```

   **Minder gemengde bestanden:** U kunt de functies definiëren die variabelen als argumenten accepteren. De uitvoer van deze functies is de resulterende stijlen. Gebruik deze combinaties in verschillende stijlen om te voorkomen dat CSS-stijlen worden herhaald.

   Adaptieve formulieren bieden OTB-mixen die zijn gedefinieerd in:

   * `/apps/clientlibs/fd/af/guidetheme/common/less/adaptiveforms-mixins.less`

   Aangepaste formulieren bieden ook mengsels van derden, zoals gedefinieerd in:

   * `/apps/clientlibs/fd/af/third-party/less/mixins.less`

   Bemonsteringsmixterdefinitie:

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

   **Stijlen.bestand:** Gebruik dit bestand om alle bestanden op te nemen die u in de clientbibliotheek nodig hebt (variabelen, mixins, stijlen).

   In het volgende voorbeeldbestand kan `styles.less` de importinstructie in willekeurige volgorde worden geplaatst.

   De instructies voor het importeren van de volgende .less-bestanden zijn verplicht:

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

   Het `css.txt` bevat de paden van CSS-bestanden die voor de bibliotheek moeten worden gedownload.

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

1. Als u het thema wilt opnemen dat is gemaakt [om een aangepaste sectie over formulierthema](/help/forms/using/creating-custom-adaptive-form-themes.md#p-to-create-an-adaptive-form-theme-p) te maken, maakt u een aangepaste pagina van het type `cq:Component`.

   Bijvoorbeeld, `/apps/myAfCustomizations/myAfPages/forestPage`

   1. Voeg een `sling:resourceSuperType` eigenschap toe en stel de waarde ervan in als `fd/af/components/page/base`.

      ![Opname van CRX-opslagplaats](assets/1-2.png)

   1. Als u een thema op de pagina wilt gebruiken, moet u een bestand library.jsp overschrijven aan het knooppunt.

      Vervolgens importeert u het thema dat u hebt gemaakt in Een adaptieve sectie met formulierthema&#39;s van dit artikel maken.

      Het volgende voorbeeldcodefragment importeert het `af.theme.forest` thema.

      ```jsp
      <%@include file="/libs/fd/af/components/guidesglobal.jsp"%>
      <cq:includeClientLib categories="af.theme.forest"/>
      ```

   1. **Optioneel**: Hef op de aangepaste pagina de header.jsp, footer.jsp en de body.jsp op, al naar gelang de vereisten.

1. Een aangepaste sjabloon maken (bijvoorbeeld: `/apps/myAfCustomizations/myAfTemplates/forestTemplate`) waarvan jcr:content verwijst naar de aangepaste pagina die in de vorige stap is gemaakt (bijvoorbeeld: `myAfCustomizations/myAfPages/forestPage)`.

   ![Opname van CRX-opslagplaats](assets/2-1.png)

1. Maak een adaptief formulier met de sjabloon die u in de vorige stap hebt gemaakt. De vormgeving van het adaptieve formulier wordt bepaald door het thema dat is gemaakt in Een adaptieve sectie voor formulierthema maken van dit artikel.

