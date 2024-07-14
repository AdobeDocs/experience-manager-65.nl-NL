---
title: Sandbox-toepassing ontwikkelen
description: Leer hoe u een Sandbox-toepassing ontwikkelt die gebruikmaakt van stichtingsscripts en die de mogelijkheid biedt om ontwerpen met Community-componenten mogelijk te maken.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: 7ac0056c-a742-49f4-8312-2cf90ab9f23a
solution: Experience Manager
feature: Communities
role: Developer
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '575'
ht-degree: 0%

---

# Sandbox-toepassing ontwikkelen  {#develop-sandbox-application}

In deze sectie, nu het malplaatje opstelling in de [ aanvankelijke toepassing ](initial-app.md) sectie is, en de aanvankelijke pagina&#39;s die in de [ worden gevestigd aanvankelijke inhoud ](initial-content.md) sectie, kunt u de toepassing ontwikkelen. U doet dit door stichtingsmanuscripten te gebruiken die de capaciteit omvatten om creatie met de componenten van de Gemeenschappen toe te laten. Aan het einde van deze sectie hebt u een volledig functionele website.

## Scripts voor basispagina&#39;s gebruiken {#using-foundation-page-scripts}

Het standaardmanuscript, dat wordt gecreeerd toen de component die het playpage malplaatje teruggeeft werd toegevoegd, wordt gewijzigd om head.jsp van de stichtingspagina en een lokale body.jsp te omvatten.

### Type superbron {#super-resource-type}

De eerste stap bestaat uit het toevoegen van een eigenschap van het type resource super aan het knooppunt `/apps/an-scf-sandbox/components/playpage` , zodat dit de scripts en eigenschappen van het supertype overneemt.

CRXDE Lite gebruiken:

1. Selecteer knooppunt `/apps/an-scf-sandbox/components/playpage` .
1. Voer op het tabblad Eigenschappen een nieuwe eigenschap in met de volgende waarden:

   Naam: `sling:resourceSuperType`

   Type: `String`

   Waarde: `foundation/components/page`

1. Klik op de groene knop **[!UICONTROL +Add]** .
1. Klik op **[!UICONTROL Save All]**.

   ![ pagina-manuscript ](assets/page-script.png)

### Scripts voor hoofd en lichaam {#head-and-body-scripts}

1. In **CRXDE Lite** ontdekkingsruit, navigeer aan `/apps/an-scf-sandbox/components/playpage` en klik het dossier `playpage.jsp` tweemaal om het in Edit ruit te openen.

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

1. Omdat u bekend bent met scripttags open/close, vervangt u &quot; // TODO ...&quot; door `includes` scripts voor de kop en de hoofdtekst van &lt;html>.

   Bij het supertype `foundation/components/page` wordt elk script dat niet in dezelfde map is gedefinieerd, omgezet naar een script in de `/apps/foundation/components/page` -map (indien aanwezig) of naar een script in de `/libs/foundation/components/page` -map.

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

1. Het is niet nodig om het basatiescript `head.jsp` te bedekken, maar het stichtingsscript `body.jsp` is leeg.

   Als u wilt instellen voor ontwerpen, bedekt u `body.jsp` met een lokaal script en neemt u een alineasysteem (parsys) op in de hoofdtekst:

   1. Navigeer naar `/apps/an-scf-sandbox/components` .
   1. Selecteer het knooppunt `playpage` .
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

**Mening de pagina in browser op geef wijze uit:**

* Standaardinterface: `http://localhost:4502/editor.html/content/an-scf-sandbox/en/play.html`

U zou niet alleen het rubriek **Communautaire Spel** moeten zien, maar ook UI voor het uitgeven van paginainhoud.

Het zijpaneel van Assets/Component is zichtbaar wanneer zowel het zijpaneel open en het venster wijd genoeg voor zowel de zijinhoud als de pagina inhoud om wordt getoond wordt geschakeld.

![ mening-pagina ](assets/view-page.png)

* Klassieke gebruikersinterface: `http://localhost:4502/cf#/content/an-scf-sandbox/en/play.html`

Hieronder ziet u hoe de afspeelpagina wordt weergegeven in de klassieke gebruikersinterface, inclusief in de zoekfunctie voor inhoud (cf):

![ spel-pagina-mening ](assets/play-page-view.png)

## Community-componenten {#communities-components}

Om de componenten van Communities voor ontwerp toe te laten, begin door deze instructies te volgen:

* [Toegang tot onderdelen van Gemeenschappen](basics.md#accessing-communities-components)

Voor deze zandbak, begin met deze **Communautaire** componenten (laat toe door doos te controleren):

* Opmerkingen
* Forum
* Classificatie
* Revisies
* Overzicht van revisies (weergave)
* Stemming

Kies bovendien **[!UICONTROL General]** -componenten, zoals

* Afbeelding
* Tabel
* Tekst
* Titel (Stichting)

>[!NOTE]
>
>De componenten die voor het paginapunt worden ingeschakeld, worden in de opslagplaats opgeslagen als de waarde van de eigenschap `components` van het
>
>Knooppunt `/etc/designs/an-scf-sandbox/jcr:content/playpage/par` .

## Openingspagina {#landing-page}

In een meertalig milieu, zou de wortelpagina een manuscript omvatten dat het verzoek van de cliënt zou ontleden om de aangewezen taal te bepalen.

In dit voorbeeld wordt de hoofdpagina statisch ingesteld op omleiding naar de Engelse pagina, die in de toekomst kan worden ontwikkeld als de hoofdbestemmingspagina met een koppeling naar de afspeelpagina.

Wijzig de URL van de browser in de hoofdpagina: `http://localhost:4502/editor.html/content/an-scf-sandbox.html`

* Het pictogram Pagina-informatie selecteren
* Selecteren **[!UICONTROL Open Properties]**
* Op het tabblad GEAVANCEERD

   * Blader voor de Redirect-vermelding naar **[!UICONTROL Websites]** > **[!UICONTROL SCF Sandbox Site]** > **[!UICONTROL SCF Sandbox]**
   * Klikken **[!UICONTROL OK]**

* Klikken **[!UICONTROL OK]**

Nadat de site is gepubliceerd, wordt het bladeren naar de hoofdpagina op een publicatie-instantie omgeleid naar de Engelse pagina.

De laatste stap vóór het spelen met de componenten van Communities SCF moet een Omslag van de Bibliotheek van de Cliënt toevoegen (clientlibs)... [ voeg Clientlibs ](add-clientlibs.md) toe
