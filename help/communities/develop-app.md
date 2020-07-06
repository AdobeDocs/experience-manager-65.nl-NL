---
title: Sandbox-toepassing ontwikkelen
seo-title: Sandbox-toepassing ontwikkelen
description: Toepassing ontwikkelen met behulp van basisscripts
seo-description: Toepassing ontwikkelen met behulp van basisscripts
uuid: 572f68cd-9ecb-4b43-a7f8-4aa8feb6c64e
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 910229a3-38b1-44f1-9c09-55f8fd6cbb1d
translation-type: tm+mt
source-git-commit: d0b333ffa6cad4841e70e652328e92554fb2a7a1
workflow-type: tm+mt
source-wordcount: '598'
ht-degree: 2%

---


# Sandbox-toepassing ontwikkelen  {#develop-sandbox-application}

In deze sectie, nu het malplaatje in de [aanvankelijke toepassingssectie](initial-app.md) , en de aanvankelijke pagina&#39;s is opstelling die in de [aanvankelijke inhoudsectie](initial-content.md) worden gevestigd, kan de toepassing worden ontwikkeld gebruikend stichtingsmanuscripten met inbegrip van de capaciteit om creatie met de componenten van de Gemeenschappen toe te laten. Aan het einde van deze sectie is de website functioneel.

## Scripts voor basispagina&#39;s gebruiken {#using-foundation-page-scripts}

Het standaardmanuscript, dat wordt gecreeerd toen de component die het playpage malplaatje teruggeeft werd toegevoegd, wordt gewijzigd om head.jsp van de stichtingspagina en een lokale body.jsp te omvatten.

### Type superbron {#super-resource-type}

De eerste stap bestaat uit het toevoegen van een eigenschap van het type resource super aan het `/apps/an-scf-sandbox/components/playpage` knooppunt zodat het de scripts en eigenschappen van het supertype overneemt.

CRXDE Lite gebruiken:

1. Selecteer knooppunt `/apps/an-scf-sandbox/components/playpage`.
1. Voer op het tabblad Eigenschappen een nieuwe eigenschap in met de volgende waarden:

   Naam: `sling:resourceSuperType`

   Type: `String`

   Waarde: `foundation/components/page`

1. Klik op de groene **[!UICONTROL +Add]** knop.
1. Klik op **[!UICONTROL Save All]**.

   ![chlimage_1-231](assets/chlimage_1-231.png)

### Scripts voor hoofd en lichaam {#head-and-body-scripts}

1. Navigeer in het deelvenster **CRXDE Lite** -verkenner naar het bestand `/apps/an-scf-sandbox/components/playpage` en dubbelklik erop `playpage.jsp` om het te openen in het bewerkingsvenster.

   `/apps/an-scf-sandbox/components/playpage/playpage.jsp`

   ```xml
   <%--
   
     An SCF Sandbox Play Component component.
   
     This is the component which renders content for An SCF Sandbox page.
   
   --%><%
   %><%@include file="/libs/foundation/global.jsp"%><%
   %><%@page session="false" %><%
   %><%
    // TODO add your code here
   %>
   ```

1. Als u weet dat er scripttags voor openen/sluiten zijn, vervangt u &quot; // TODO ...&quot; met inbegrip van manuscripten voor het hoofd en lichaamsdelen van &lt;html>.

   Met een supertype van `foundation/components/page`, zal om het even welk manuscript niet die in deze zelfde omslag wordt bepaald aan een manuscript in `/apps/foundation/components/page` omslag (als het bestaat), anders aan een manuscript in `/libs/foundation/components/page` omslag oplossen.

   `/apps/an-scf-sandbox/components/playpage/playpage.jsp`

   ```xml
   <%--
   
       An SCF Sandbox Play Component component: playpage.jsp
   
     This is the component which renders content for An SCF Sandbox page.
   
   --%><%
   %><%@include file="/libs/foundation/global.jsp"%><%
   %><%@page session="false" %>
   <html>
     <cq:include script="head.jsp"/>
     <cq:include script="body.jsp"/>
   </html>
   ```

1. Het stichtingsmanuscript `head.jsp` moet niet worden bedekt, maar het stichtingsmanuscript `body.jsp` is leeg.

   Aan opstelling voor creatie, bedekking `body.jsp` met een lokaal manuscript en omvat een paragraafsysteem (parsys) in het lichaam:

   1. Ga naar `/apps/an-scf-sandbox/components`.
   1. Select the `playpage` node.
   1. Klik met de rechtermuisknop en selecteer `Create > Create File...`

      * Naam: **body.jsp**
   1. Klik op **[!UICONTROL Save All]**.
   Open `/apps/an-scf-sandbox/components/playpage/body.jsp` en plak in de volgende tekst:

   ```xml
   <%--
   
       An SCF Sandbox Play Component component: body.jsp
   
     This is the component which renders content for An SCF Sandbox page.
   
   --%><%
   %><%@include file="/libs/foundation/global.jsp"%><%
   %><%@page session="false" %>
   <body>
       <h2>Community Play</h2>
       <cq:include path="par" resourceType="foundation/components/parsys" />
   </body>
   ```

1. Klik op **[!UICONTROL Save All]**.

**De pagina in een browser weergeven in de bewerkingsmodus:**

* Standaardinterface: [http://localhost:4502/editor.html/content/an-scf-sandbox/en/play.html](http://localhost:4502/editor.html/content/an-scf-sandbox/en/play.md)

U moet niet alleen de kop **Community Play** zien, maar ook de interface voor het bewerken van pagina-inhoud.

Het paneel Middelen/component wordt weergegeven wanneer het zijpaneel geopend is en het venster breed genoeg is om zowel de inhoud als de pagina-inhoud weer te geven.

![chlimage_1-232](assets/chlimage_1-232.png)

* Klassieke gebruikersinterface: [http://localhost:4502/cf#/content/an-scf-sandbox/en/play.html](http://localhost:4502/cf#/content/an-scf-sandbox/en/play.html)

Hieronder ziet u hoe de afspeelpagina wordt weergegeven in de klassieke gebruikersinterface, inclusief in de zoekfunctie voor inhoud (cf):

![chlimage_1-233](assets/chlimage_1-233.png)

## Community-componenten {#communities-components}

Om de componenten van Communities voor ontwerp toe te laten, begin door deze instructies te volgen:

* [Toegang tot onderdelen van Gemeenschappen](basics.md#accessing-communities-components)

Voor deze zandbak, begin met deze **communautaire** componenten (toelaten door de doos te controleren):

* Opmerkingen
* Forum
* Classificatie
* Revisies
* Overzicht van revisies (weergave)
* Stemming

Kies bovendien **[!UICONTROL General]** componenten, zoals

* Afbeelding
* Tabel
* Tekst
* Titel (Stichting)

>[!NOTE]
>
>De componenten die voor het paginapunt worden toegelaten worden opgeslagen in de bewaarplaats als waarde van het `components` bezit van
>`/etc/designs/an-scf-sandbox/jcr:content/playpage/par` knooppunt.


## Landing Page {#landing-page}

In een meertalig milieu, zou de wortelpagina een manuscript omvatten dat het verzoek van de cliënt zou ontleden om de aangewezen taal te bepalen.

In dit eenvoudige voorbeeld wordt de basispagina statisch ingesteld op omleiding naar de Engelse pagina, die in de toekomst kan worden ontwikkeld als de hoofdbestemmingspagina met een koppeling naar de afspeelpagina.

Wijzig de URL van de browser in de hoofdpagina: [http://localhost:4502/editor.html/content/an-scf-sandbox.html](https://locahost:4502/editor.html/content/an-scf-sandbox.html)

* Het pictogram Pagina-informatie selecteren
* Selecteer **[!UICONTROL Open Properties]**
* Op het tabblad GEAVANCEERD

   * Blader voor het Redirect-bericht naar **[!UICONTROL Websites]** > **[!UICONTROL SCF Sandbox Site]** > **[!UICONTROL SCF Sandbox]**
   * Klik op **[!UICONTROL OK]**

* Klik op **[!UICONTROL OK]**

Als de site eenmaal is gepubliceerd, wordt het bladeren naar de hoofdpagina op een publicatie-instantie omgeleid naar de Engelse pagina.

De laatste stap vóór het spelen met de gemeenschappenSCF componenten moet een Omslag van de Bibliotheek van de Cliënt (clientlibs) toevoegen.... [Clienlibs toevoegen](add-clientlibs.md)