---
title: Fouten opsporen in HTML5-formulieren
seo-title: Fouten opsporen in HTML5-formulieren
description: In het document staan stappen voor het oplossen van verschillende bekende problemen.
seo-description: In het document staan stappen voor het oplossen van verschillende bekende problemen.
uuid: df1835aa-6033-4ecb-97c8-4c3b7b96b943
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
discoiquuid: 5260d981-da40-40ab-834e-88e091840813
translation-type: tm+mt
source-git-commit: 56c6cfd437ef185336e81373bd5f758205b96317

---


# Fouten opsporen in HTML5-formulieren {#debugging-html-forms}

Dit document bevat verschillende scenario&#39;s voor probleemoplossing. Voor elk scenario, worden sommige stappen verstrekt om het probleem problemen op te lossen. Volg deze stappen en, als het probleem voortduurt, vorm Logger om logboeken voor fouten/waarschuwingen te krijgen en te herzien. Zie Logboeken [genereren voor HTML5-formulieren](/help/forms/using/enable-logs.md)voor meer informatie over het loggen van HTML5-formulieren.

## Probleem: Bij het weergeven van het formulier zie ik de pagina met uitzonderingen org.apache.sling.api.SlingException {#problem-when-rendering-the-form-i-see-org-apache-sling-api-slingexception-exception-page}

In de uitzonderingsdetails, onderzoek naar woord **veroorzaakt door**.

De waarschijnlijke reden is dat een of meer parameters in de URL onjuist zijn.

Controleer de volgende parameters:

<table>
 <tbody>
  <tr>
   <td><strong>Parameter</strong></td>
   <td><strong>Beschrijving</strong></td>
  </tr>
  <tr>
   <td>template</td>
   <td>De bestandsnaam van de sjabloon</td>
  </tr>
  <tr>
   <td>contentRoot</td>
   <td>Het pad waar de sjabloon en de bijbehorende bronnen zich bevinden</td>
  </tr>
  <tr>
   <td>dataRef</td>
   <td>Absoluut pad van het gegevensbestand dat met de sjabloon is samengevoegd.<br /> Opmerking: Het pad definieert het absolute pad van het gegevensbestand.</td>
  </tr>
  <tr>
   <td>gegevens</td>
   <td>UTF-8-gecodeerde gegevensbytes die met de sjabloon worden samengevoegd.</td>
  </tr>
 </tbody>
</table>

## Probleem: Kan een formulier niet genereren (er wordt een foutbericht weergegeven) {#problem-unable-to-render-a-form-an-error-message-is-displayed}

1. Controleer of de opgegeven parameters correct zijn. Zie Parameters [](/help/forms/using/debug.md#main-pars-table)renderen voor gedetailleerde informatie over parameters.
1. Meld u aan bij CRX Package Manager (op https://&lt;server>:&lt;port>/crx/packmgr/index.jsp) en controleer of de volgende pakketten correct zijn geïnstalleerd:

   * adobe-lc-forms-content-pkg-&lt;version>.zip
   * adobe-lc-forms-runtime-pkg-&lt;version>.zip

1. Meld u aan bij de CQ-webconsole (Felix Console) op https://&lt;server>:&lt;port>/system/console/bundles.

   Zorg ervoor dat de status van de volgende bundels &quot;actief&quot; is:

   * scala-lang.bundle [osgi]
   (com.adobe.livecyclescala-lang.bundle)

   * Adobe XFA Forms Renderer
   (com.adobe.livecycle.adobe-lc-forms-core)

   * Adobe XFA Forms LC Connector
   (com.adobe.livecycle.adobe-lc-forms-lc-connector)

## Probleem: Formulierweergaven zonder stijlen {#problem-form-renders-without-styles}

1. Open **Developer Tools** in uw browser. Controleer of profile.css beschikbaar is.
1. Als het bestand profile.css niet beschikbaar is, meldt u zich aan bij CRX DE op https://&lt;server>:&lt;port>/crx/de.
1. Navigeer in de mappenhiërarchie links naar /etc/clientlibs/fd/xfaforms/. Open css.txt- dossiers die in de omslagen worden vermeld.

   * profiel
   * runtime
   * scrollnav
   * toolbar
   * xfalib

1. Controleer of de bestanden die in het bestand css.txt worden vermeld, aanwezig zijn in de CRX DE-lijst op /libs/fd/xfaforms/clientlibs/xfalib/css.

   ```css
   #base=css
   application.css
   dialog.css
   datepicker.css
   scribble.css
   listboxwidget.css
   ```

1. Als de vermelde bestanden niet beschikbaar zijn, installeert u het pakket adobe-lc-forms-runtime-pkg-&lt;version>.zip opnieuw.

### Probleem: Onverwachte fout aangetroffen {#problem-unexpected-error-encountered}

1. Voeg in de formulier-URL een queryparameter debugClientLibs toe en stel de waarde ervan in op true (bijvoorbeeld: https://&lt;server>:&lt;port>/content/xfaforms/profiles/test.html?contentRoot=&lt;some path>&amp;template=&lt;name of xdp file>&amp;log=1-a9-b9-c9&amp;debugClientLibs=true)
1. Ga in de desktopbrowser, zoals chroom, naar Developer Tools -> Console.
1. Open de logboeken om het type van fout te identificeren. Zie [logs voor HTML5-formulieren](/help/forms/using/enable-logs.md)voor gedetailleerde informatie over logboeken.
1. Ga naar Developer Tools -> Console. Gebruik stacktracering om de code te zoeken die de fout veroorzaakt. Foutopsporing de fout om het probleem op te lossen.

   >[!NOTE]
   >
   >Als er een scriptfout optreedt, controleert u of hetzelfde probleem optreedt tijdens de PDF-uitvoering van het formulier. Zo ja, dan is er een probleem in de logica van het formulierscript.

## Probleem: Kan het formulier niet verzenden {#problem-unable-to-submit-the-form}

1. Zorg ervoor dat u toegangsrechten hebt tot de AEM-server en dat u verbinding hebt met de server.
1. Controleer of de parameter submitUrl correct is.
1. Schakel de logbestanden aan de clientzijde in zoals vermeld in [Logs voor de HTML5-formulieren](/help/forms/using/enable-logs.md) met de optie Foutopsporing als **1-a5-b5-c5**. Geef het formulier vervolgens weer en klik op Verzenden. Open browser zuivert console en controleer als er een fout is.
1. Zoek de serverlogboeken zoals vermeld in [Logs voor de HTML5-formulieren](/help/forms/using/enable-logs.md). Controleer of er tijdens de verzending een fout is opgetreden in de serverlogboeken.

## Probleem: Gelokaliseerde foutberichten worden niet weergegeven {#problem-localized-error-messages-do-not-display}

1. Geef het formulier weer met extra queryparameter **debugClientLibs=true** in de desktopbrowser en ga vervolgens naar Developer Tools -> Resources en controleer het bestand I18N.css.
1. Als het bestand niet beschikbaar is, meldt u zich aan bij CRX DE op https://&lt;server>:&lt;port>/crx/de.
1. Navigeer in de mappenhiërarchie links naar /libs/fd/xfaforms/clientlibs/I18N en zorg ervoor dat de volgende bestanden en mappen bestaan:

   * Namespace.js
   * LogMessages.js
   * Mappen voor talen

1. Als een van de bovenstaande bestanden of mappen niet bestaat, installeert u het pakket **adobe-lc-forms-runtime-pkg-&lt;version>.zip** opnieuw.
1. Navigeer naar de map met dezelfde naam als de naam van de landinstelling en controleer de inhoud ervan. De map moet de volgende bestanden bevatten:

   * I18N.js
   * js.txt

1. Controleer de inhoud van js.txt en zorg ervoor dat het de volgende ingangen heeft.

   ```
   ../Namespace.js
   I18N.js
   ../LogMessages.js
   ```

## Probleem: Afbeelding niet zichtbaar {#problem-image-not-showing-up}

1. Controleer of de URL van de afbeelding juist is.
1. Controleer of uw browser dit type afbeelding ondersteunt.
1. In de uitzonderingsdetails, onderzoek naar woord **veroorzaakt door**.

   De waarschijnlijke reden is dat een of meer parameters in de URL onjuist zijn.

   Controleer de volgende parameters:
Staptekst

<table>
 <tbody>
  <tr>
   <td><strong>Parameter</strong></td>
   <td><strong>Beschrijving</strong></td>
  </tr>
  <tr>
   <td>template</td>
   <td>De bestandsnaam van de sjabloon</td>
  </tr>
  <tr>
   <td>contentRoot</td>
   <td>Het pad waar de sjabloon en de bijbehorende bronnen zich bevinden</td>
  </tr>
  <tr>
   <td>dataRef</td>
   <td>Absoluut pad van het gegevensbestand dat met de sjabloon is samengevoegd.<br /> Opmerking: Het pad definieert het absolute pad van het gegevensbestand.</td>
  </tr>
  <tr>
   <td>gegevens</td>
   <td>UTF-8-gecodeerde gegevensbytes die met de sjabloon worden samengevoegd.</td>
  </tr>
 </tbody>
</table>

1. Ga in de desktopbrowser naar Developer Tools -> Resources.

   Schakel links in Frames in als die afbeelding wordt weergegeven.
