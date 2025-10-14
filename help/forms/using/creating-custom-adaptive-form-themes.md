---
title: Aangepaste aangepaste formulierthema's maken
description: Een adaptief formulierthema is een Adobe Experience Manager-clientbibliotheek waarmee u de stijlen (look and feel) voor een adaptief formulier kunt definiëren. Leer hoe u aangepaste formulierthema's kunt maken.
content-type: reference
topic-tags: customization
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 73b0057f-082d-4502-90e2-5e41b52c1185
solution: Experience Manager, Experience Manager Forms
role: User, Developer
feature: Adaptive Forms,Foundation Components
source-git-commit: 8a77756e8ba771c8de9950c2323bef8f23cc59b4
workflow-type: tm+mt
source-wordcount: '790'
ht-degree: 0%

---

# Aangepaste aangepaste formulierthema&#39;s maken {#creating-custom-adaptive-form-themes}

>[!CAUTION]
>
>Adobe Experience Manager (AEM) Forms verstrekt het [&#x200B; vermogen van de Redacteur van het Thema &#x200B;](/help/forms/using/themes.md) om adaptieve vormen [&#x200B; thema&#39;s &#x200B;](/help/forms/using/themes.md) tot stand te brengen en te wijzigen. Voer de stappen uit die in dit artikel worden vermeld slechts als u van een versie hebt bevorderd die [&#x200B; Redacteur van het Thema &#x200B;](/help/forms/using/themes.md) niet heeft en u een bestaande investering in thema&#39;s hebt die gebruikend Minder/CSS dossiers (pre-thema redacteursmethode) worden gecreeerd.

## Vereisten {#prerequisites}

* Kennis van het LESS-framework (Leaner CSS)
* Een clientbibliotheek maken in Adobe Experience Manager
* [&#x200B; Creërend een adaptief vormmalplaatje &#x200B;](/help/forms/using/custom-adaptive-forms-templates.md) voor het gebruiken van het thema u creeert

## Adaptief formulierthema {#adaptive-form-theme}

Een **adaptief vormthema** is een AEM cliëntbibliotheek die u gebruikt om de stijlen (blik en gevoel) voor een adaptieve vorm te bepalen.

U creeert een **adaptieve malplaatje** en past het thema op het malplaatje toe. U kunt dit douanemalplaatje dan gebruiken om een **adaptieve vorm** tot stand te brengen.

![&#x200B; Aangepaste Vorm en de Bibliotheek van de Cliënt &#x200B;](assets/hierarchy.png)

## Een adaptief formulierthema maken {#to-create-an-adaptive-form-theme}

>[!NOTE]
>
>De volgende procedure wordt beschreven gebruikend steekproefnamen voor AEM voorwerpen zoals knopen, eigenschappen, en omslagen.
>
>Als u deze stappen met de namen uitvoert, zou het resulterende malplaatje aan de volgende momentopname gelijkaardig moeten lijken:

![&#x200B; bos de Adaptieve momentopname van de Vorm &#x200B;](assets/thumbnail.png)
**Figuur:** *Steekproef van het Thema van het Bos*

1. Creeer een knoop van type `cq:ClientLibraryFolder` onder de `/apps` knoop.

   Maak bijvoorbeeld het volgende knooppunt:

   `/apps/myAfThemes/forestTheme`

1. Voeg een multi-getaxeerde koordbezit `categories` aan de knoop toe en plaats correct zijn waarde.

   Stel de eigenschap bijvoorbeeld in op: `af.theme.forest` .

   ![&#x200B; momentopname van de bewaarplaats van CRX &#x200B;](assets/3-2.png)

1. Voeg twee mappen, `less` en `css` , en een bestand `css.txt` toe aan het knooppunt dat in stap 1 wordt gemaakt:

   * `less` map: bevat de `less` variabele bestanden waarin u de `less` variabelen en `less mixins` definieert die worden gebruikt om de CSS-stijlen te beheren.

     Deze map bestaat uit `less` variabele bestanden, `less` mixin bestanden `less` en bestanden die stijlen definiëren met behulp van mixins en variabelen. En al deze `less` dossiers worden dan ingevoerd in styles.less.

   * `css` omslag: Bevat de .css dossiers waarin u de statische stijlen bepaalt die in het thema moeten worden gebruikt.

   **Minder veranderlijke dossiers**: Dit zijn de dossiers waar u de variabelen bepaalt of met voeten treedt die in het bepalen van CSS stijlen worden gebruikt.

   Adaptieve formulieren bieden variabelen die in de volgende `.less` -bestanden zijn gedefinieerd:

   * `/apps/clientlibs/fd/af/guidetheme/common/less/globalvariables.less`
   * `/apps/clientlibs/fd/af/guidetheme/common/less/layoutvariables.less`

   Adaptieve formulieren bevatten ook variabelen van derden die zijn gedefinieerd in:

   `/apps/clientlibs/fd/af/third-party/less/variables.less`

   U kunt de variabelen van `less` gebruiken die bij adaptieve formulieren worden geleverd, u kunt deze variabelen overschrijven of u kunt nieuwe variabelen van `less` maken.

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

   Om de `less` variabelen met voeten te treden:

   1. Standaardadaptieve formuliervariabelen importeren:

      `/apps/clientlibs/fd/af/guidetheme/common/less/globalvariables.less/apps/clientlibs/fd/af/guidetheme/common/less/layoutvariables.less`

   1. Importeer vervolgens het bestand met de waarde Minder, dat overschreven variabelen bevat.

   Voorbeeld van nieuwe definities van variabelen:

   ```css
   @button-focus-bg-color: rgb(40, 208, 90);
   @button-hover-bg-color: rgb(30, 156, 67);
   ```

   **Minder mixin dossiers:** u kunt de functies bepalen die variabelen als argumenten goedkeuren. De uitvoer van deze functies is de resulterende stijlen. Gebruik deze combinaties in verschillende stijlen, zodat u niet telkens CSS-stijlen hoeft te herhalen.

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

   **Styles.less Dossier:** Gebruik dit dossier om alle `less` dossiers (variabelen, mengen, stijlen) te omvatten die u in de cliëntbibliotheek moet gebruiken.

   In het volgende voorbeeldbestand `styles.less` kan de instructie import in willekeurige volgorde worden geplaatst.

   De instructies voor het importeren van de volgende `.less` -bestanden zijn verplicht:

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

   `css.txt` bevat de paden van CSS-bestanden die voor de bibliotheek moeten worden gedownload.

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

1. Om het thema te omvatten dat in [&#x200B; wordt gecreeerd om een adaptieve sectie van het vormthema &#x200B;](/help/forms/using/creating-custom-adaptive-form-themes.md#p-to-create-an-adaptive-form-theme-p) tot stand te brengen, creeer een douanepagina van type `cq:Component`.

   Bijvoorbeeld: `/apps/myAfCustomizations/myAfPages/forestPage`

   1. Voeg een eigenschap `sling:resourceSuperType` toe en stel de waarde ervan in als `fd/af/components/page/base` .

      ![&#x200B; momentopname van de bewaarplaats van CRX &#x200B;](assets/1-2.png)

   1. Als u een thema op de pagina wilt gebruiken, moet u een bestand library.jsp dat met voeten wordt getreden, aan het knooppunt toevoegen.

      Vervolgens kunt u het thema importeren dat is gemaakt in Een adaptieve sectie voor formulierthema maken van dit artikel.

      In het volgende voorbeeldcodefragment wordt het thema `af.theme.forest` geïmporteerd.

      ```jsp
      <%@include file="/libs/fd/af/components/guidesglobal.jsp"%>
      <cq:includeClientLib categories="af.theme.forest"/>
      ```

   1. **Facultatief**: In de douanepagina, treedt header.jsp, footer.jsp, en body.jsp met voeten, zoals vereist.

1. Maak een aangepaste sjabloon (bijvoorbeeld: `/apps/myAfCustomizations/myAfTemplates/forestTemplate` ) waarvan de jcr:content verwijst naar een aangepaste pagina die in de vorige stap is gemaakt (bijvoorbeeld: `myAfCustomizations/myAfPages/forestPage)` .

   ![&#x200B; momentopname van de bewaarplaats van CRX &#x200B;](assets/2-1.png)

1. Maak een adaptief formulier met de sjabloon die u in de vorige stap hebt gemaakt. De vormgeving van het adaptieve formulier wordt bepaald door het thema dat is gemaakt in de sectie Voor het maken van een adaptief formulierthema van dit artikel.
