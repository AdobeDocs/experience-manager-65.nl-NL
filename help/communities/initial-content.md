---
title: Oorspronkelijke inhoud van sandbox
seo-title: Oorspronkelijke inhoud van sandbox
description: Inhoud maken
seo-description: Inhoud maken
uuid: 9810fe47-8d1a-4238-9b9c-0cc47c63d97a
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: e8f28cd5-7950-4aab-bf62-3d4ed3d33cbd
translation-type: tm+mt
source-git-commit: 85f3b8f2a5f079954f4907037c1c722a6b25fd91

---


# Oorspronkelijke inhoud van sandbox {#initial-sandbox-content}

In deze sectie maakt u de volgende pagina&#39;s die allemaal de [paginasjabloon](initial-app.md#createthepagetemplate)gebruiken:

* SCF Sandbox Site, die wordt omgeleid naar de Engelse versie van de hoofdpagina.

   * SCF Sandbox - De hoofdpagina voor de Engelse versie van de site.

      * SCF-afspelen - Onderliggend item van de hoofdpagina waarop moet worden afgespeeld.

Hoewel deze zelfstudie niet in [taalkopieën](../../help/sites-administering/tc-prep.md)wordt geschreven, is deze zo ontworpen dat de hoofdpagina detectie van de voorkeurstaal voor de gebruiker via de HTML-koptekst kan implementeren en omleidt naar de juiste hoofdpagina voor de taal. De conventie is de landcode van twee letters te gebruiken voor de knooppuntnaam van de pagina, bijvoorbeeld &quot;en&quot; voor Engels, &quot;fr&quot; voor Frans, enzovoort.

## Eerste pagina&#39;s maken {#create-first-pages}

Nu er een [paginamalplaatje](initial-app.md#createthepagetemplate)is, kunnen wij de wortelpagina van de website in de /content folder vestigen.

1. De standaard-UI biedt momenteel blauwdrukken voor het maken van sites. Aangezien deze zelfstudie een eenvoudige plaats creeert, is klassieke UI nuttig.

   Als u wilt overschakelen naar de klassieke UI, selecteert u de globale navigatie en houdt u de muisaanwijzer boven de rechterzijde van het pictogram Projecten. Selecteer het pictogram *Overschakelen naar klassieke gebruikersinterface* dat wordt weergegeven:

   ![chlimage_1-36](assets/chlimage_1-36.png)

   De capaciteit om op klassieke UI over te schakelen moet door een beheerder [worden](../../help/sites-administering/enable-classic-ui.md)toegelaten.

1. Van de [klassieke UI Welkome pagina](http://localhost:4502/welcome.html), uitgezochte **[!UICONTROL Websites]**.

   ![chlimage_1-37](assets/chlimage_1-37.png)

   U kunt ook rechtstreeks toegang krijgen tot de klassieke UI voor websites door naar [/sitebeheerder te bladeren.](http://localhost:4502/siteadmin)

1. Selecteer **[!UICONTROL Websites]** in het deelvenster Verkenner en selecteer vervolgens **[!UICONTROL Nieuw]** > **[!UICONTROL Nieuwe pagina]** op de werkbalk.

   Voer in het dialoogvenster Pagina **** maken het volgende in:

   * Titel: `SCF Sandbox Site`
   * Naam: `an-scf-sandbox`
   * Selecteer **[!UICONTROL een SCF-sandbox-afspeelsjabloon]**
   * Klik op **[!UICONTROL Maken]**
   ![chlimage_1-38](assets/chlimage_1-38.png)

1. Selecteer in het verkenner-venster de pagina die u net hebt gemaakt `/Websites/SCF Sandbox Site`en klik op **[!UICONTROL Nieuw]** > **[!UICONTROL Nieuwe pagina]**:

   * Titel: `SCF Sandbox`
   * Naam: `en`
   * Selecteer **een SCF-sandbox-afspeelsjabloon **
   * Klik op **Maken **

1. Selecteer in het verkenner-venster de pagina die u net hebt gemaakt `/Websites/SCF Sandbox Site/SCF Sandbox`en klik op **[!UICONTROL Nieuw]** > **[!UICONTROL Nieuwe pagina]**

   * Titel: `SCF Play`
   * Naam: `play`
   * Selecteer **[!UICONTROL een SCF-sandbox-afspeelsjabloon]**
   * Klik op **[!UICONTROL Maken]**

1. Zo wordt de website nu weergegeven in de websiteconsole. U ziet dat onderliggende pagina&#39;s van het item dat is geselecteerd in het deelvenster Verkenner, worden weergegeven in het rechterdeelvenster waar ze kunnen worden beheerd.

   ![chlimage_1-39](assets/chlimage_1-39.png)

   Dit is de repository weergave van wat er is gemaakt met het gereedschap Website en de sjabloon:

   ![chlimage_1-40](assets/chlimage_1-40.png)

## Het ontwerppad toevoegen {#add-the-design-path}

Wanneer ` [/etc/designs/an-scf-sandbox](setup-website.md#setupthedesigntreeetcdesigns)` werd gecreeerd gebruikend de ontwerpsectie van de console van Hulpmiddelen, het bezit &quot;

* `cq:template="/libs/wcm/core/templates/designpage"`

is gedefinieerd, hetgeen de optionele mogelijkheid biedt om naar ontwerpelementen in een script te verwijzen met behulp van `currentDesign.getPath()`. Bijvoorbeeld

* &lt;% String favIcon = currentDesign.getPath() + &quot;/favicon.ico&quot;; %>


   * Naam: `cq:designPath`
   * Type: `String`
   * Waarde: `/etc/designs/an-scf-sandbox`

* Klik op groen `[+] Add`

De oplossing moet er als volgt uitzien:

![chlimage_1-41](assets/chlimage_1-41.png)

* Klik op Alles **[!UICONTROL opslaan]**

[ Problemen met opslaan? Opnieuw aanmelden! ]

>[!NOTE]
>
>Het gebruik van cq:designPath is optioneel en staat los van het [gebruik van clientlibs](develop-app.md#includeclientlibsintemplate), die in wezen vereist zijn omdat de SCF-componenten [clientlibs](client-customize.md#clientlibs-for-scf) gebruiken om hun JS en CSS te beheren.


