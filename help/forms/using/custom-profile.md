---
title: Een aangepast profiel maken voor HTML5-formulieren
description: Een HTML5-formulierprofiel is een resourceknooppunt in Apache Sling. Deze vertegenwoordigt een aangepaste versie van de renderservice voor HTML5-formulieren.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
discoiquuid: 9cd22244-9aa6-4b5f-96cf-c9cb3d6f9c8a
feature: HTML5 Forms,Mobile Forms
exl-id: cf86c810-c466-4894-acc2-d4faf49754cc
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '656'
ht-degree: 0%

---

# Een aangepast profiel maken voor HTML5-formulieren {#creating-a-custom-profile-for-html-forms}

Een profiel is een resourceknooppunt in [Apache Sling](https://sling.apache.org/). Deze staat voor een aangepaste versie van de renderingsservice voor HTML5-formulieren. U kunt de service Renditie van HTML5-formulieren gebruiken om de weergave, het gedrag en de interacties van de HTML-5-formulieren aan te passen. Er bestaat een profielknooppunt in het dialoogvenster `/content` in de gegevensopslagruimte van de JCR. U kunt het knooppunt rechtstreeks onder het dialoogvenster `/content` of een submap van de `/content` map.

Het profielknooppunt bevat de **sling:resourceSuperType** eigenschap en de standaardwaarde is **xfaforms/profile**. Het renderscript voor het knooppunt staat op /libs/xfaforms/profile.

De Sling-scripts zijn JSP-scripts. Deze JSP-scripts dienen als containers voor het samenstellen van de HTML voor het aangevraagde formulier en de vereiste JS/CSS-artefacten. Deze verkoopscripts worden ook wel **Scripts voor renderer van profiel**. De profielrenderer roept de Forms OSGi-service aan om het gevraagde formulier te genereren.

Het profielscript bevindt zich in html.jsp en html.POST.jsp voor verzoeken om GET en POST. U kunt een of meer bestanden kopiëren en wijzigen om uw aanpassingen te overschrijven en toe te voegen. Breng geen wijzigingen op de plaats aan. Dergelijke wijzigingen worden door de patchupdate overschreven.

Een profiel bevat verschillende modules. De modules zijn formRuntime.jsp, config.jsp, toolbar.jsp, formBody.jsp, nav_footer.jsp, en footer.jsp.

## formRuntime.jsp {#formruntime-jsp-br}

De modules formRuntime.jsp bevat verwijzingen van de cliëntbibliotheken. Het toont ook methodes om scèneinformatie uit het verzoek te halen en de gelokaliseerde berichten in het verzoek te omvatten. U kunt eigen aangepaste JavaScript-bibliotheken of -stijlen opnemen in formRuntime.jsp.

## config.jsp {#config-jsp}

De module config.jsp bevat diverse configuraties zoals registreren, de volmachtsdiensten, en gedragsversie. U kunt uw eigen configuratie en widgetaanpassing aan de module config.jsp toevoegen. U kunt configuraties zoals de registratie van de douanewidget aan de module config.jsp ook toevoegen.

## toolbar.jsp {#toolbar-jsp}

Het bestand toolbar.jsp bevat code waarmee een gekleurde werkbalk wordt gemaakt. Om de toolbar te verwijderen, verwijder toolbar.jsp uit HTML.jsp

## formBody.jsp {#formbody-jsp}

De module formBody.jsp is bedoeld voor de HTML-weergave van het XFA-formulier.

## nav_footer.jsp {#nav-footer-jsp}

Eerst wordt met het HTML5-formulier alleen de eerste pagina van het formulier weergegeven. Wanneer een gebruiker door het formulier schuift, worden de overige formulieren geladen. Hierdoor verloopt het laden sneller. De component nav_footer.jsp bevat alle stijlen en vereiste elementen om het laden van de pagina&#39;s tijdens het schuiven te vergemakkelijken.

## footer.jsp {#footer-jsp}

De module footer.jsp is leeg. Hiermee kunt u scripts toevoegen die alleen voor gebruikersinteractie worden gebruikt.

## Aangepaste profielen maken {#creating-custom-profiles}

Voer de volgende stappen uit om een aangepast profiel te maken:

### Profielknooppunt maken {#create-profile-node}

1. Navigeer naar de interface CRX DE bij URL: `https://'[server]:[port]'/crx/de` en login aan de interface met beheerdergeloofsbrieven.

1. Navigeer in het linkerdeelvenster naar de locatie */content/xfaforms/profiles*.

1. Kopieer het standaardknooppunt en plak het knooppunt in een andere map (*/content/profiles*) met naam *geforceerd*.

1. Selecteer het nieuwe knooppunt. *geforceerd* en voeg een tekenreekseigenschap toe: *sling:resourceType* met waarde: *Transformatie/demo*.

1. Klik op Alles opslaan in het werkbalkmenu om de wijzigingen op te slaan.

### Het rendererscript voor profielen maken {#create-the-profile-renderer-script}

Nadat u een aangepast profiel hebt gemaakt, voegt u renderinformatie toe aan dit profiel. Wanneer het ontvangen van een verzoek om het nieuwe profiel, controleert CRX het bestaan van de /apps omslag voor de JSP pagina die moet worden teruggegeven. Maak de JSP-pagina in de map /apps.

1. Navigeer in het linkervenster naar het `/apps` map.
1. Klik met de rechtermuisknop op de knop `/apps` en maak een map met de naam **geforceerd**.
1. Met de **geforceerd** map maken een map met de naam **demo**.
1. Klik op de knop **Alles opslaan** knop.
1. Navigeren naar `/libs/xfaforms/profile/html.jsp` en kopieer het knooppunt **html.jsp**.
1. Plakken **html.jsp** in de `/apps/hrform/demo` hierboven gemaakte map met dezelfde naam **html.jsp** en klik op **Opslaan**.
1. Als u andere componenten van profielmanuscript hebt, volg stap 1-6 om de componenten in /apps/hrform/demo omslag te kopiëren.

1. Open de URL om te controleren of het profiel is gemaakt `https://'[server]:[port]'/content/xfaforms/profiles/hrform.html`

Om uw formulieren te verifiëren, [Uw formulieren importeren](/help/forms/using/get-xdp-pdf-documents-aem.md) van uw lokale bestandssysteem naar AEM Forms en [Een voorbeeld van het formulier bekijken](/help/forms/using/previewing-forms.md) op AEM instantie van de serverauteur.
