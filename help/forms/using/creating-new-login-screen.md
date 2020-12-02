---
title: Een nieuw aanmeldingsscherm maken
seo-title: Een nieuw aanmeldingsscherm maken
description: Hoe kan ik de aanmeldingspagina van LiveCycle-modules wijzigen, bijvoorbeeld van de AEM Forms-werkruimte of Forms Manager.
seo-description: Hoe kan ik de aanmeldingspagina van LiveCycle-modules wijzigen, bijvoorbeeld van de AEM Forms-werkruimte of Forms Manager.
uuid: 2d4a72f4-cc9a-412d-856d-0fca75f1272b
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: 35497785-263d-44b1-9ee4-85921997295b
docset: aem65
translation-type: tm+mt
source-git-commit: 9fcfd1c2c63d9a32f2d68f5b0c974bc5b5d22b40
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 3%

---


# Een nieuw aanmeldingsscherm maken{#creating-a-new-login-screen}

U kunt het aanmeldingsscherm wijzigen van alle AEM Forms-modules die het AEM Forms-aanmeldingsscherm gebruiken. De wijzigingen zijn bijvoorbeeld van invloed op het aanmeldingsscherm van zowel de Forms Manager- als de AEM Forms-werkruimte.

## Vereiste {#prerequisite}

1. Meld u aan bij `/lc/crx/de` met beheerdersmachtigingen.
1. Voer de volgende handelingen uit:

   1. Repliceer de hiërarchische structuur: van `/libs/livecycle/core/content` om `/apps/livecycle/core/content`.

      Handhaaf de zelfde (knoop/omslag) eigenschappen en toegangsbeheer.

   1. Kopieer de inhoudsmap:

      Van: `/libs/livecycle/core`

      tot: `/apps/livecycle/core`.

   1. Verwijder de inhoud van de map `/apps/livecycle/core`.

1. Voer de volgende handelingen uit:

   1. Repliceer de hiërarchische structuur: van `/libs/livecycle/core/components/login` om `/apps/livecycle/core/components/login`. Handhaaf de zelfde (knoop/omslag) eigenschappen en toegangsbeheer.

   1. Kopieer de map met componenten: van `/libs/livecycle/core` naar `/apps/livecycle/core`.

   1. Verwijder de inhoud van de map: `/apps/livecycle/core/components/login`.

### Een nieuwe landinstelling toevoegen {#adding-a-new-locale}

1. Kopieer de map `i18n`:

   * Van `/libs/livecycle/core/components/login`
   * tot `/apps/livecycle/core/components/login`

1. Verwijder alle mappen in `i18n`, behalve één, bijvoorbeeld `en`.

1. Voer in de map `en` de volgende handelingen uit:

   1. Wijzig de naam van de map in de naam van de landinstelling die u wilt ondersteunen. Bijvoorbeeld, `ar`.

   1. Wijzig de waarde van de eigenschap `jcr:language` in `ar` (voor de map `ar`).
   >[!NOTE]
   >
   >Als locale een taal-land codecombinatie is, bijvoorbeeld `ar-DZ`, dan verander de omslagnaam en bezitswaarde in `ar-DZ`.

1. Kopiëren `login.jsp`:

   * Van `/libs/livecycle/core/components/login`
   * tot `/apps/livecycle/core/components/login`

1. Wijzig het volgende codefragment voor `/apps/livecycle/core/components/login/login.jsp`:

***Landinstelling is taalcode***

```jsp
String browserLocale = "en";

    for(int i=0; i<locales.length; i++)
    {
        String prioperty = locales[i];
        if(prioperty.trim().startsWith("en")) {
            browserLocale = "en";
            break;
        }
        if(prioperty.trim().startsWith("de")){
            browserLocale = "de";
            break;
        }
        if(prioperty.trim().startsWith("ja")){
            browserLocale = "ja";
            break;
        }
        if(prioperty.trim().startsWith("fr")){
            browserLocale = "fr";
            break;
        }
    }
```

Naar

```jsp
String browserLocale = "en";
    for(int i=0; i<locales.length; i++)
    {
        String prioperty = locales[i];
        if(prioperty.trim().startsWith("ar")) {
            browserLocale = "ar";
            break;
        }
        if(prioperty.trim().startsWith("en")) {
            browserLocale = "en";
            break;
        }
        if(prioperty.trim().startsWith("de")){
            browserLocale = "de";
            break;
        }
        if(prioperty.trim().startsWith("ja")){
            browserLocale = "ja";
            break;
        }
        if(prioperty.trim().startsWith("fr")){
            browserLocale = "fr";
            break;
        }
    }
```

```jsp
String browserLocale = "en";

    for(int i=0; i<locales.length; i++)
    {
        String prioperty = locales[i];
        if(prioperty.trim().startsWith("en")) {
            browserLocale = "en";
            break;
        }
        if(prioperty.trim().startsWith("de")){
            browserLocale = "de";
            break;
        }
        if(prioperty.trim().startsWith("ja")){
            browserLocale = "ja";
            break;
        }
        if(prioperty.trim().startsWith("fr")){
            browserLocale = "fr";
            break;
        }
    }
```

Naar

```jsp
String browserLocale = "en";
    for(int i=0; i<locales.length; i++)
    {
        String prioperty = locales[i];
        if(prioperty.trim().equalsIgnoreCase("ar-DZ")) {
            browserLocale = "ar-DZ";
            break;
        }
        if(prioperty.trim().startsWith("en")) {
            browserLocale = "en";
            break;
        }
        if(prioperty.trim().startsWith("de")){
            browserLocale = "de";
            break;
        }
        if(prioperty.trim().startsWith("ja")){
            browserLocale = "ja";
            break;
        }
        if(prioperty.trim().startsWith("fr")){
            browserLocale = "fr";
            break;
        }
    }
```

***Standaardlandinstelling wijzigen***

```jsp
   String browserLocale = "en";
   for(int i=0; i<locales.length; i++)

   To

   String browserLocale = "ar";
   for(int i=0; i<locales.length; i++)
```

### Nieuwe tekst toevoegen of bestaande tekst wijzigen {#adding-new-text-or-modifying-existing-text}

1. Map `i18n` kopiëren:

   * Van `/libs/livecycle/core/components/login`
   * tot `/apps/livecycle/core/components/login`

1. Wijzig nu de waarde van de eigenschap `sling:message` van het knooppunt (onder de gewenste map met landinstellingscode) waarvoor u de tekst wilt wijzigen. Vertaling wordt uitgevoerd via de sleutel die wordt vermeld in de waarde van de eigenschap `sling:key` van het knooppunt.

1. Voer de volgende handelingen uit voor het toevoegen van een nieuw sleutelwaardepaar. Controleer een voorbeeld in het volgende schermafbeelding.

   1. Maak een knooppunt van het type `sling:MessageEntry` of kopieer een bestaand knooppunt en wijzig de naam ervan onder alle mappen voor landinstellingen.
   1. Kopiëren `login.jsp` :

      * Van `/libs/livecycle/core/components/login`

      * tot `/apps/livecycle/core/components/login`
   1. Wijzig `/apps/livecycle/core/components/login/login.jsp` om de toegevoegde tekst op te nemen.

   ![Nieuw sleutelwaardepaar toevoegen](assets/capture_new.png)

   ```jsp
   div class="loginContent">
   
                       <span class="loginFlow"></code>
                       <span class="loginVersion"><%= i18n.get("Version: 11.0.0") %></code>
                       <span class="loginTitle"><%= i18n.get("Login") %></code>
                       <% if (loginFailed) {%>
   ```

   Naar

   ```jsp
   div class="loginContent">
   
                       <span class="loginFlow"></code>
                       <span class="loginVersion"><%= i18n.get("My Welcome Message") %></code>
                       <span class="loginVersion"><%= i18n.get("Version: 11.0.0") %></code>
                       <span class="loginTitle"><%= i18n.get("Login") %></code>
                       <% if (loginFailed) {%>
   ```

### Nieuwe stijl toevoegen of bestaande stijl wijzigen {#adding-new-style-or-modifying-existing-style}

1. Knooppunt `login` kopiëren:

   * Van `/libs/livecycle/core/content`
   * tot `/apps/livecycle/core/content`

1. Bestanden `login.js` en `jquery-1.8.0.min.js` verwijderen uit het knooppunt `/apps/livecycle/core/content/login.`
1. Wijzig de stijlen in het CSS-bestand.
1. Nieuwe stijlen toevoegen:

   1. Nieuwe stijlen toevoegen aan `/apps/livecycle/core/content/login/login.css`
   1. Kopiëren `login.jsp`

      * Van `/libs/livecycle/core/components/login`

      * tot `/apps/livecycle/core/components/login`
   1. Wijzig `/apps/livecycle/core/components/login/login.jsp` om de toegevoegde stijlen op te nemen.



Bijvoorbeeld:

* Voeg het volgende toe aan `/apps/livecycle/core/content/login/login.css`.

```
css.newLoginContentArea {
    width: 700px;
    padding: 100px 0px 0px 100px;
   }
```

* Wijzig het volgende in `/apps/livecycle/core/components/login.jsp`.


   ```jsp
   <div class="loginContentArea">
   ```

   Naar

   ```jsp
   <div class="newLoginContentArea">
   ```

>[!NOTE]
>
>Als de bestaande afbeeldingen in `/apps/livecycle/core/content/login` (gekopieerd uit `/libs/livecycle/core/content/login`) worden verwijderd, verwijdert u de bijbehorende verwijzingen in CSS.

### Nieuwe afbeeldingen toevoegen {#add-new-images}

1. Voer de stappen uit om een nieuwe stijl toe te voegen of bestaande stijl te wijzigen (zoals hierboven beschreven).
1. Voeg nieuwe afbeeldingen toe in `/apps/livecycle/core/content/login`. Afbeelding toevoegen:

   1. WebDAV-client installeren.
   1. Navigeer naar de map `/apps/livecycle/core/content/login` met WebDAV-client. Zie voor meer informatie: [https://dev.day.com/docs/en/crx/current/how_to/webdav_access.html](https://docs.adobe.com/docs/en/crx/current/how_to/webdav_access.html).

   1. Voeg nieuwe afbeeldingen toe.

1. Voeg nieuwe stijlen toe in `/apps/livecycle/core/content/login/login.css,` die overeenkomen met nieuwe afbeeldingen die worden toegevoegd in `/apps/livecycle/core/content/login`.
1. Gebruik de nieuwe stijlen in `login.jsp` bij `/apps/livecycle/core/components`.

Bijvoorbeeld:


```css
.newLoginContainerBkg {

 background-image: url(my_Bg.gif);
 background-repeat: no-repeat;
 background-position: left top;
 width: 727px;
}
```


    * Ga als volgt te werk in /apps/livecycle/core/components/login.jsp.

```jsp
<div class="loginContainerBkg">
```

Naar

```jsp
<div class="newLginContainerBkg">
```
