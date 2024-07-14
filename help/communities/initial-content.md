---
title: Oorspronkelijke inhoud van sandbox
description: Leer hoe u de paginasjabloon in de sandbox gebruikt om een hoofdpagina te maken voor een Engelse versie van een website en een onderliggende pagina van de hoofdpagina.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: 068a0fff-ca48-4847-ba3f-d78416c97f6d
solution: Experience Manager
feature: Communities
role: Developer
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# Oorspronkelijke inhoud van sandbox {#initial-sandbox-content}

In deze sectie, creeert u de volgende pagina&#39;s die allen het [ paginamalplaatje ](initial-app.md#createthepagetemplate) gebruiken:

* SCF Sandbox Site, die wordt omgeleid naar de Engelse versie van de hoofdpagina.

   * SCF Sandbox - De hoofdpagina voor de Engelse versie van de site.

   * SCF-afspelen - Onderliggend item van de hoofdpagina waarop moet worden afgespeeld.

Dit leerprogramma delft niet in [ taalexemplaren ](../../help/sites-administering/tc-prep.md). In plaats daarvan, wordt het ontworpen zodat kan de wortelpagina opsporing van de aangewezen taal voor de gebruiker door de kopbal van de HTML uitvoeren, en aan de aangewezen belangrijkste pagina voor de taal opnieuw richten. De conventie is om de landcode van twee letters te gebruiken voor de knooppuntnaam van de pagina, bijvoorbeeld &quot;en&quot; voor Engels, en &quot;fr&quot; voor Frans.

## Eerste pagina&#39;s maken {#create-first-pages}

Nu er a [ paginamalplaatje ](initial-app.md#createthepagetemplate) is, kunt u de wortelpagina van de website in de /content folder vestigen.

1. De standaard-UI biedt momenteel blauwdrukken voor het maken van sites. Aangezien deze zelfstudie een eenvoudige plaats creeert, is klassieke UI nuttig.

   Als u wilt overschakelen naar de klassieke UI, selecteert u de globale navigatie en houdt u de muisaanwijzer boven de rechterzijde van het pictogram Projecten. Selecteer de *Schakelaar aan Klassieke UI* pictogram dat verschijnt:

   ![ klassieke-ui ](assets/classic-ui.png)

   De capaciteit om aan klassieke UI over te schakelen moet [ door een beheerder ](../../help/sites-administering/enable-classic-ui.md) worden toegelaten.

1. Van de [ klassieke UI Welkome pagina ](http://localhost:4502/welcome.html), uitgezochte **[!UICONTROL Websites]**.

   ![ klassieke-ui-website ](assets/classic-ui-website.png)

   U kunt de klassieke UI voor websites ook rechtstreeks openen door naar [ /site-admin te bladeren.](http://localhost:4502/siteadmin)

1. Selecteer **[!UICONTROL Websites]** in het verkennervenster en selecteer vervolgens op de werkbalk **[!UICONTROL New]** > **[!UICONTROL New Page]** .

   Voer in het dialoogvenster **[!UICONTROL Create Page]** het volgende in:

   * Titel: `SCF Sandbox Site`
   * Naam: `an-scf-sandbox`
   * Selecteren **[!UICONTROL An SCF Sandbox Play Template]**
   * Klikken **[!UICONTROL Create]**

   ![ klassiek-ui-creeer-pagina ](assets/classic-ui-create-page.png)

1. Selecteer in het verkenner-venster de pagina die u hebt gemaakt, `/Websites/SCF Sandbox Site` en klik op **[!UICONTROL New]** > **[!UICONTROL New Page]** :

   * Titel: `SCF Sandbox`
   * Naam: `en`
   * Selecteren **[!UICONTROL An SCF Sandbox Play Template]**
   * Klikken **[!UICONTROL Create]**

1. Selecteer in het verkenner-venster de pagina die u hebt gemaakt, `/Websites/SCF Sandbox Site/SCF Sandbox` en klik op **[!UICONTROL New]** > **[!UICONTROL New Page]**

   * Titel: `SCF Play`
   * Naam: `play`
   * Selecteren **[!UICONTROL An SCF Sandbox Play Template]**
   * Klikken **[!UICONTROL Create]**

1. Zo wordt de website nu weergegeven in de websiteconsole. U ziet dat onderliggende pagina&#39;s van het item dat is geselecteerd in het deelvenster Verkenner, worden weergegeven in het rechterdeelvenster waar ze kunnen worden beheerd.

   ![ klassieke-ui-website-pagina ](assets/classic-ui-website-page.png)

   Dit is de repository weergave van wat er is gemaakt met het gereedschap Website en de sjabloon:

   ![ klassiek-ui-bewaarplaats-mening ](assets/classic-ui-repository-view.png)

## Het ontwerppad toevoegen {#add-the-design-path}

Wanneer ` [/etc/designs/an-scf-sandbox](setup-website.md#setupthedesigntreeetcdesigns)` werd gecreeerd gebruikend de ontwerpsectie van de console van Hulpmiddelen, het bezit &quot;

* `cq:template="/libs/wcm/core/templates/designpage"`

Is gedefinieerd, wat de optionele mogelijkheid biedt om met `currentDesign.getPath()` te verwijzen naar ontwerpelementen in een script. Bijvoorbeeld

* `% String favIcon = currentDesign.getPath() + "/favicon.ico"; %`


   * Naam: `cq:designPath`
   * Type: `String`
   * Waarde: `/etc/designs/an-scf-sandbox`

* Klik op groen `[+] Add`

De gegevensopslagruimte moet er als volgt uitzien:

![ klassiek-ui-bewaarplaats-weg ](assets/classic-ui-repository-path.png)

* Klikken **[!UICONTROL Save All]**

Als er om het even welk probleem is die de configuratie opslaan, login opnieuw en vormen opnieuw.

>[!NOTE]
>
>Het gebruik van `cq:designPath` is facultatief en is niet verwant met het [ gebruik van clientlibs ](develop-app.md#includeclientlibsintemplate), die als componenten SCF [ clientlibs ](client-customize.md#clientlibs-for-scf) worden vereist om hun JS en CSS te beheren.
