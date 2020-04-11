---
title: Een aangepast profiel maken voor HTML5-formulieren
seo-title: Een aangepast profiel maken voor HTML5-formulieren
description: Een HTML5-formulierprofiel is een resourceknooppunt in Apache Sling. Deze vertegenwoordigt een aangepaste versie van de renderservice voor HTML5-formulieren.
seo-description: Een HTML5-formulierprofiel is een resourceknooppunt in Apache Sling. Deze vertegenwoordigt een aangepaste versie van de renderservice voor HTML5-formulieren.
uuid: b9938280-a92c-4dde-b465-04372db3ca8d
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
discoiquuid: 9cd22244-9aa6-4b5f-96cf-c9cb3d6f9c8a
translation-type: tm+mt
source-git-commit: 56c6cfd437ef185336e81373bd5f758205b96317

---


# Een aangepast profiel maken voor HTML5-formulieren {#creating-a-custom-profile-for-html-forms}

Een profiel is een resourceknooppunt in [Apache Sling](https://sling.apache.org/). Deze vertegenwoordigt een aangepaste versie van de renderingsservice voor HTML5-formulieren. Met de service HTML5 Forms Rendition kunt u de weergave, het gedrag en de interacties van de HTML5-formulieren aanpassen. Er bestaat een profielknooppunt in de `/content` map in de JCR-opslagplaats. U kunt het knooppunt rechtstreeks in de `/content` map of in een submap van de `/content` map plaatsen.

Het profielknooppunt heeft de eigenschap **sling:resourceSuperType** en de standaardwaarde is **xfaforms/profile**. Het renderscript voor het knooppunt staat op /libs/xfaforms/profile.

De Sling-scripts zijn JSP-scripts. Deze JSP-scripts dienen als containers voor het samenstellen van de HTML voor het aangevraagde formulier en de vereiste JS/CSS-artefacten. Deze het Verdelen manuscripten worden ook bedoeld als manuscripten **van de Renderer van het** Profiel. De profielrenderer roept de dienst van Forms OSGi aan om de gevraagde vorm terug te geven.

Het profielscript bevindt zich in html.jsp en html.POST.jsp voor GET en POST aanvragen. U kunt een of meer bestanden kopiëren en wijzigen om uw aanpassingen te overschrijven en toe te voegen. Breng geen wijzigingen op de plaats aan. Dergelijke wijzigingen worden door de patchupdate overschreven.

Een profiel bevat verschillende modules. De modules zijn formRuntime.jsp, config.jsp, toolbar.jsp, formBody.jsp, nav_footer.jsp, en footer.jsp.

## formRuntime.jsp {#formruntime-jsp-br}

De modules formRuntime.jsp bevat verwijzingen van de cliëntbibliotheken. Het toont ook methodes om scèneinformatie uit het verzoek te halen en de gelokaliseerde berichten in het verzoek te omvatten. U kunt eigen aangepaste javascript-bibliotheken of -stijlen opnemen in formRuntime.jsp.

## config.jsp {#config-jsp}

De module config.jsp bevat diverse configuraties zoals registreren, de volmachtsdiensten, en gedragsversie. U kunt uw eigen configuratie en widgetaanpassing aan de module config.jsp toevoegen. U kunt configuraties zoals de registratie van de douanewidget aan de module config.jsp ook toevoegen.

## toolbar.jsp {#toolbar-jsp}

Het bestand toolbar.jsp bevat code waarmee een gekleurde werkbalk wordt gemaakt. Als u de werkbalk wilt verwijderen, verwijdert u toolbar.jsp uit HTML.jsp

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

1. Navigeer in het linkerdeelvenster naar de locatie */inhoud/XFAFORM/profielen*.

1. Kopieer de standaardinstelling voor het knooppunt en plak het knooppunt in een andere map (*/inhoud/profielen*) met de *naamstructuur*.

1. Selecteer het nieuwe knooppunt, *vorm* en voeg een tekenreekseigenschap toe: *sling:resourceType* met waarde: *Transformatie/demo*.

1. Klik op Alles opslaan in het werkbalkmenu om de wijzigingen op te slaan.

### Het rendererscript voor profielen maken {#create-the-profile-renderer-script}

Nadat u een aangepast profiel hebt gemaakt, voegt u renderinformatie toe aan dit profiel. Wanneer het ontvangen van een verzoek om het nieuwe profiel, controleert CRX het bestaan van de /apps omslag voor de JSP pagina die moet worden teruggegeven. Maak de JSP-pagina in de map /apps.

1. Navigeer in het linkerdeelvenster naar de `/apps` map.
1. Klik met de rechtermuisknop op de `/apps` map en kies een map met de naam **Transform**.
1. Met behulp van de map **Transform** maakt u een map met de naam **demo**.
1. Klik op de knop **Alles** opslaan.
1. Navigeer naar `/libs/xfaforms/profile/html.jsp` en kopieer het knooppunt **html.jsp**.
1. Plak het **knooppunt html.jsp** in de `/apps/hrform/demo` map die hierboven met dezelfde naam **html.jsp** is gemaakt en klik op **Opslaan**.
1. Als u andere componenten van profielmanuscript hebt, volg stap 1-6 om de componenten in /apps/hrform/demo omslag te kopiëren.

1. Open de URL om te controleren of het profiel is gemaakt `https://'[server]:[port]'/content/xfaforms/profiles/hrform.html`

Als u uw formulieren wilt verifiëren, [importeert u uw formulieren](/help/forms/using/get-xdp-pdf-documents-aem.md) van uw lokale bestandssysteem naar AEM Forms en [bekijkt u een voorbeeld van het formulier](/help/forms/using/previewing-forms.md) op de auteur van de AEM-server.
