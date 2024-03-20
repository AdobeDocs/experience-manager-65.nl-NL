---
title: Een aanmeldingsscherm maken
description: Hoe te om de login pagina van de modules van het LiveCycle, bijvoorbeeld, van de werkruimte van AEM Forms of de Manager van Forms te wijzigen.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
docset: aem65
exl-id: 5cb906b6-6a3c-498c-94f5-27a9071ea934
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 1%

---

# Een aanmeldingsscherm maken{#creating-a-new-login-screen}

U kunt het aanmeldingsscherm wijzigen van alle AEM Forms-modules die het AEM Forms-aanmeldingsscherm gebruiken. De wijzigingen zijn bijvoorbeeld van invloed op het aanmeldingsscherm van zowel de Forms Manager- als de AEM Forms-werkruimte.

## Vereiste {#prerequisite}

1. Aanmelden bij `/lc/crx/de` met beheerdersmachtigingen.
1. Voer de volgende handelingen uit:

   1. Repliceer de hiërarchische structuur: van `/libs/livecycle/core/content` om `/apps/livecycle/core/content`.

      Handhaaf de zelfde (knoop/omslag) eigenschappen en toegangsbeheer.

   1. Kopieer de inhoudsmap:

      van: `/libs/livecycle/core`

      tot: `/apps/livecycle/core`.

   1. De inhoud van `/apps/livecycle/core` map.

1. Voer de volgende handelingen uit:

   1. Repliceer de hiërarchische structuur: van `/libs/livecycle/core/components/login` om `/apps/livecycle/core/components/login`. Handhaaf de zelfde (knoop/omslag) eigenschappen en toegangsbeheer.

   1. Map met componenten kopiëren: van `/libs/livecycle/core` tot `/apps/livecycle/core`.

   1. Verwijder de inhoud van de map: `/apps/livecycle/core/components/login`.

### Een nieuwe landinstelling toevoegen {#adding-a-new-locale}

1. De `i18n` map:

   * Van `/libs/livecycle/core/components/login`
   * tot `/apps/livecycle/core/components/login`

1. Alle mappen in de map verwijderen `i18n` op één na, zeg `en`.

1. In de map `en`, voert u de volgende handelingen uit:

   1. Wijzig de naam van de map in de naam van de landinstelling die u wilt ondersteunen. Bijvoorbeeld: `ar`.

   1. De eigenschap wijzigen `jcr:language` waarde aan `ar`(voor de `ar` map).

   >[!NOTE]
   >
   >Als locale een combinatie van taal- en landcode is, bijvoorbeeld `ar-DZ`Wijzig vervolgens de mapnaam en de eigenschapswaarde in `ar-DZ`.

1. Kopiëren `login.jsp`:

   * Van `/libs/livecycle/core/components/login`
   * tot `/apps/livecycle/core/components/login`

1. Het volgende codefragment wijzigen voor `/apps/livecycle/core/components/login/login.jsp`:

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

1. Kopiëren `i18n` map:

   * Van `/libs/livecycle/core/components/login`
   * tot `/apps/livecycle/core/components/login`

1. Wijzig nu de waarde van de eigenschap `sling:message` van het knooppunt (in de gewenste map met landinstellingscodes) waarvoor u de tekst wilt wijzigen. Vertaling gebeurt via de sleutel die wordt vermeld in de waarde van `sling:key` eigenschap van het knooppunt.

1. Voer de volgende handelingen uit voor het toevoegen van een nieuw sleutelwaardepaar. Controleer een voorbeeld in het volgende schermafbeelding.

   1. Een knooppunt van het type maken `sling:MessageEntry`of kopieer een bestaand knooppunt en wijzig de naam ervan in alle mappen voor landinstellingen.
   1. Kopiëren `login.jsp` :

      * Van `/libs/livecycle/core/components/login`

      * tot `/apps/livecycle/core/components/login`

   1. Wijzigen `/apps/livecycle/core/components/login/login.jsp` om de toegevoegde tekst op te nemen.

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

1. Kopiëren `login` knooppunt:

   * Van `/libs/livecycle/core/content`
   * tot `/apps/livecycle/core/content`

1. Bestanden verwijderen `login.js` en `jquery-1.8.0.min.js`, van het knooppunt `/apps/livecycle/core/content/login.`
1. Wijzig de stijlen in het CSS-bestand.
1. Nieuwe stijlen toevoegen:

   1. Nieuwe stijlen toevoegen aan `/apps/livecycle/core/content/login/login.css`
   1. Kopiëren `login.jsp`

      * Van `/libs/livecycle/core/components/login`

      * tot `/apps/livecycle/core/components/login`

   1. Wijzigen `/apps/livecycle/core/components/login/login.jsp` om de toegevoegde stijlen op te nemen.


Bijvoorbeeld:

* Voeg het volgende toe aan `/apps/livecycle/core/content/login/login.css`.

```
css.newLoginContentArea {
    width: 700px;
    padding: 100px 0px 0px 100px;
   }
```

* Na wijzigen in `/apps/livecycle/core/components/login.jsp`.


  ```jsp
  <div class="loginContentArea">
  ```

  Naar

  ```jsp
  <div class="newLoginContentArea">
  ```

>[!NOTE]
>
>Als de bestaande afbeeldingen in `/apps/livecycle/core/content/login` (gekopieerd van `/libs/livecycle/core/content/login`) worden verwijderd en verwijderen vervolgens de bijbehorende verwijzingen in CSS.

### Nieuwe afbeeldingen toevoegen {#add-new-images}

1. Voer de stappen uit om een nieuwe stijl toe te voegen of een bestaande stijl te wijzigen (zoals hierboven beschreven).
1. Nieuwe afbeeldingen toevoegen in `/apps/livecycle/core/content/login`. Afbeelding toevoegen:

   1. WebDAV-client installeren.
   1. Navigeren naar `/apps/livecycle/core/content/login` met webDAV-client. Zie voor meer informatie [WebDAV-toegang](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/webdav-access.html?lang=en).

   1. Voeg nieuwe afbeeldingen toe.

1. Nieuwe stijlen toevoegen in `/apps/livecycle/core/content/login/login.css,` komt overeen met nieuwe afbeeldingen toegevoegd in `/apps/livecycle/core/content/login`.
1. De nieuwe stijlen gebruiken in `login.jsp` om `/apps/livecycle/core/components`.

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
