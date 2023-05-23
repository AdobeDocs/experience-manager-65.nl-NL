---
title: Sandbox-toepassing ontwikkelen
seo-title: Develop Sandbox Application
description: Toepassing ontwikkelen met behulp van basisscripts
seo-description: Develop application using foundation scripts
uuid: 572f68cd-9ecb-4b43-a7f8-4aa8feb6c64e
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 910229a3-38b1-44f1-9c09-55f8fd6cbb1d
exl-id: 7ac0056c-a742-49f4-8312-2cf90ab9f23a
source-git-commit: 1d334c42088342954feb34f6179dc5b134f81bb8
workflow-type: tm+mt
source-wordcount: '552'
ht-degree: 1%

---

# Sandbox-toepassing ontwikkelen  {#develop-sandbox-application}

In deze sectie, nu het malplaatje opstelling in is geweest [eerste toepassing](initial-app.md) en de eerste pagina&#39;s die zijn vastgesteld in de [initiële inhoud](initial-content.md) -sectie, kan de toepassing worden ontwikkeld met behulp van stichtingsscripts, waaronder de mogelijkheid om ontwerpen met Gemeenschapscomponenten mogelijk te maken. Aan het einde van deze sectie is de website functioneel.

## Scripts voor basispagina&#39;s gebruiken {#using-foundation-page-scripts}

Het standaardmanuscript, dat wordt gecreeerd toen de component die het playpage malplaatje teruggeeft werd toegevoegd, wordt gewijzigd om head.jsp van de stichtingspagina en een lokale body.jsp te omvatten.

### Type superbron {#super-resource-type}

De eerste stap bestaat uit het toevoegen van een eigenschap van het type resource super aan de `/apps/an-scf-sandbox/components/playpage` knoop zodat het de manuscripten en de eigenschappen van het super type erft.

CRXDE Lite gebruiken:

1. Knooppunt selecteren `/apps/an-scf-sandbox/components/playpage`.
1. Voer op het tabblad Eigenschappen een nieuwe eigenschap in met de volgende waarden:

   Naam: `sling:resourceSuperType`

   Type: `String`

   Waarde: `foundation/components/page`

1. Klik op groen **[!UICONTROL +Add]** knop.
1. Klik op **[!UICONTROL Save All]**.

   ![pageScript](assets/page-script.png)

### Scripts voor hoofd en lichaam {#head-and-body-scripts}

1. In **CRXDE Lite** verkenner, deelvenster, navigeren naar `/apps/an-scf-sandbox/components/playpage` en dubbelklik op het bestand `playpage.jsp` openen in het bewerkvenster.

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

1. Als u weet dat er scripttags voor openen/sluiten zijn, vervangt u &quot; // TODO ...&quot; met inbegrip van scripts voor de kop en de hoofdtekst van &lt;html>.

   Met een supertype van `foundation/components/page`, worden scripts die niet in dezelfde map zijn gedefinieerd, omgezet naar een script in `/apps/foundation/components/page` map (als deze bestaat), anders naar een script in `/libs/foundation/components/page` map.

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

1. Het basatiescript `head.jsp` hoeven niet te worden bedekt, maar het stichtingsscript `body.jsp` is leeg.

   Omzetten in ontwerpomgeving, bedekking `body.jsp` met een lokaal manuscript en omvat een paragraafsysteem (parsys) in het lichaam:

   1. Ga naar `/apps/an-scf-sandbox/components`.
   1. Selecteer `playpage` knooppunt.
   1. Klik met de rechtermuisknop en selecteer `Create > Create File...`

      * Naam: **body.jsp**
   1. Klik op **[!UICONTROL Save All]**.

   Openen `/apps/an-scf-sandbox/components/playpage/body.jsp` en plak in de volgende tekst:

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

* Standaardinterface: `http://localhost:4502/editor.html/content/an-scf-sandbox/en/play.html`

U moet niet alleen de kop zien **Community Play**, maar ook de gebruikersinterface voor het bewerken van pagina-inhoud.

Het paneel Middelen/component wordt weergegeven wanneer het zijpaneel geopend is en het venster breed genoeg is om zowel de inhoud als de pagina-inhoud weer te geven.

![weergavepagina](assets/view-page.png)

* Klassieke gebruikersinterface: `http://localhost:4502/cf#/content/an-scf-sandbox/en/play.html`

Hieronder ziet u hoe de afspeelpagina wordt weergegeven in de klassieke gebruikersinterface, inclusief in de zoekfunctie voor inhoud (cf):

![play-page-view](assets/play-page-view.png)

## Community-componenten {#communities-components}

Om de componenten van Communities voor ontwerp toe te laten, begin door deze instructies te volgen:

* [Toegang tot onderdelen van Gemeenschappen](basics.md#accessing-communities-components)

In deze sandbox begint u hiermee **Gemeenschappen** componenten (inschakelen door het selectievakje in te schakelen):

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
>De componenten die voor het paginapunt worden toegelaten worden opgeslagen in de bewaarplaats als waarde van `components` eigendom van de
>
>`/etc/designs/an-scf-sandbox/jcr:content/playpage/par` knooppunt.

## Openingspagina {#landing-page}

In een meertalig milieu, zou de wortelpagina een manuscript omvatten dat het verzoek van de cliënt zou ontleden om de aangewezen taal te bepalen.

In dit eenvoudige voorbeeld wordt de basispagina statisch ingesteld op omleiding naar de Engelse pagina, die in de toekomst kan worden ontwikkeld als de hoofdbestemmingspagina met een koppeling naar de afspeelpagina.

Wijzig de URL van de browser in de hoofdpagina: `http://localhost:4502/editor.html/content/an-scf-sandbox.html`

* Het pictogram Pagina-informatie selecteren
* Selecteer **[!UICONTROL Open Properties]**
* Op het tabblad GEAVANCEERD

   * Blader voor de Redirect-vermelding naar **[!UICONTROL Websites]** > **[!UICONTROL SCF Sandbox Site]** > **[!UICONTROL SCF Sandbox]**
   * Klik op **[!UICONTROL OK]**

* Klik op **[!UICONTROL OK]**

Als de site eenmaal is gepubliceerd, wordt het bladeren naar de hoofdpagina op een publicatie-instantie omgeleid naar de Engelse pagina.

De laatste stap vóór het spelen met de gemeenschappenSCF componenten moet een Omslag van de Bibliotheek van de Cliënt (clientlibs) toevoegen.... [Clienlibs toevoegen](add-clientlibs.md)
