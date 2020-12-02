---
title: Richtlijnen voor het oplossen van problemen in de AEM Forms-werkruimte
seo-title: Richtlijnen voor het oplossen van problemen in de AEM Forms-werkruimte
description: Logboeken inschakelen en foutopsporing gebruiken in browser om problemen in de AEM Forms-werkruimte op te lossen.
seo-description: Logboeken inschakelen en foutopsporing gebruiken in browser om problemen in de AEM Forms-werkruimte op te lossen.
uuid: 07b8c8ed-f1ff-4be5-8005-251ff7b2ac85
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: 5dae9ed9-77a3-44f5-a94d-ca5c355c8730
translation-type: tm+mt
source-git-commit: 56c6cfd437ef185336e81373bd5f758205b96317
workflow-type: tm+mt
source-wordcount: '747'
ht-degree: 0%

---


# Richtlijnen voor het oplossen van problemen in de AEM Forms-werkruimte {#troubleshooting-guidelines-for-aem-forms-workspace}

In dit artikel wordt beschreven hoe u fouten in de AEM Forms-werkruimte kunt opsporen door logboekregistratie in te schakelen en foutopsporing te gebruiken in een browser. Hierin worden ook enkele algemene problemen beschreven die u kunt tegenkomen bij het gebruik van de AEM Forms-werkruimte en de bijbehorende oplossingen.

## Kan AEM Forms-werkruimtepakket {#unable-to-install-aem-forms-workspace-package} niet installeren

Nadat u de patch hebt geïnstalleerd, opent u de AEM Forms-werkruimte. Als u de fout Geen bron gevonden tegenkomt, opent u de CRX Package Manager en installeert u het `adobe-lc-workspace-pkg-<version>.zip`-pakket opnieuw.

Voer tijdens het installeren van het pakket de volgende stappen uit als er een fout `javax.jcr.nodetype.ConstraintViolationException: OakConstraint0025: Authorizable property rep:authorizableId may not be removed` optreedt:

1. Meld u aan bij CRX DE List. De standaard-URL is `https://[localhost]:'port'/lc/crx/de/index.jsp`
1. Verwijder het volgende knooppunt:

   `/home/groups/P/PERM_WORKSPACE_USER`

1. Ga naar Pakketbeheer. De standaard-URL is `https://[localhost]:'port'/lc/crx/packmgr/index.jsp.`
1. Zoek en installeer het `adobe-lc-workspace-pkg-[version].zip` pakket.
1. Start de toepassingsserver opnieuw.

## Logboekregistratie van AEM Forms-werkruimte {#aem-forms-workspace-nbsp-logging}

U kunt logboeken op diverse niveaus produceren om het optimale oplossen van problemen van fouten toe te laten. Bijvoorbeeld, in een complexe toepassing, helpt het registreren op componentenniveau bij het zuiveren en het oplossen van problemen specifieke componenten.

In de AEM Forms-werkruimte:

* Als u de logboekgegevens over een specifiek componentbestand wilt opvragen, voegt u `/log/<ComponentFile>/<LogLevel>` toe aan de URL en drukt u op `Enter`. Alle logboekinformatie voor het componentendossier op het gespecificeerde logboekniveau wordt gedrukt op de console.

* Om logboekinformatie van alle componentendossiers te krijgen, voeg `/log/all/trace` in URL toe, en druk `Enter`.

* Logbestandsindeling: `<Component file> <Date>:<Time>: <Log Level> : <Log Message>`

>[!NOTE]
>
>Standaard wordt het logniveau van alle componenten ingesteld op INFO.

* Het logboekniveau dat door gebruiker wordt geplaatst wordt gehandhaafd slechts voor die browser zitting. Wanneer de gebruiker de pagina vernieuwt, wordt het logboekniveau geplaatst aan zijn aanvankelijke waarde voor alle componenten.

### Lijst met deelbestanden in de AEM Forms-werkruimte {#list-of-component-files-in-nbsp-aem-forms-workspace}

<table>
 <tbody>
  <tr>
   <td><p>allcategoryModel</p> </td>
   <td><p>processinstanceModel</p> </td>
   <td><p>tasklistModel</p> </td>
  </tr>
  <tr>
   <td><p>appnavigationModel</p> </td>
   <td><p>processInstanceView</p> </td>
   <td><p>tasklistView</p> </td>
  </tr>
  <tr>
   <td><p>appnavigationView</p> </td>
   <td><p>processnamelistModel</p> </td>
   <td><p>taskModel</p> </td>
  </tr>
  <tr>
   <td><p>categorylistModel</p> </td>
   <td><p>processnamelistView</p> </td>
   <td><p>taskView</p> </td>
  </tr>
  <tr>
   <td><p>categorylistView</p> </td>
   <td><p>processnameModel</p> </td>
   <td><p>teamrowsView</p> </td>
  </tr>
  <tr>
   <td><p>categoryModel</p> </td>
   <td><p>processnameView</p> </td>
   <td><p>todoView</p> </td>
  </tr>
  <tr>
   <td><p>categoryView</p> </td>
   <td><p>searchtemplatedetailsView</p> </td>
   <td><p>trackingView</p> </td>
  </tr>
  <tr>
   <td><p>favorieteModel</p> </td>
   <td><p>sharequeueModel</p> </td>
   <td><p>uisettingsModel</p> </td>
  </tr>
  <tr>
   <td><p>filterlistView</p> </td>
   <td><p>sharequeueView</p> </td>
   <td><p>uisettingsView</p> </td>
  </tr>
  <tr>
   <td><p>filterView</p> </td>
   <td><p>startpointlistModel</p> </td>
   <td><p>userinfoModel</p> </td>
  </tr>
  <tr>
   <td><p>outofofficeModel</p> </td>
   <td><p>startpointlistView</p> </td>
   <td><p>userinfoView</p> </td>
  </tr>
  <tr>
   <td><p>outofofficeView</p> </td>
   <td><p>startpointModel</p> </td>
   <td><p>usersearchModel</p> </td>
  </tr>
  <tr>
   <td><p>preferencesView</p> </td>
   <td><p>startpointView</p> </td>
   <td><p>usersearchView</p> </td>
  </tr>
  <tr>
   <td><p>processInstanceHistoryView</p> </td>
   <td><p>startProcessView</p> </td>
   <td><p>wserrorModel</p> </td>
  </tr>
  <tr>
   <td><p>processinstancelistModel</p> </td>
   <td><p>startprocessView</p> </td>
   <td><p>wserrorView</p> </td>
  </tr>
  <tr>
   <td><p>processinstancelistView</p> </td>
   <td><p>taskdetailsView</p> </td>
   <td><p>wsmessageView</p> </td>
  </tr>
 </tbody>
</table>

### Logniveaus beschikbaar in de werkruimte van AEM Forms {#log-levels-available-in-nbsp-aem-forms-workspace}

* FATAAL
* FOUT
* WAARSCHUWING
* INFO
* DEBUG
* TRACE
* UIT

## Foutopsporingsgegevens voor browsers {#debugging-information-for-browsers}

Scripts en stijlen kunnen in verschillende browsers worden opgespoord.

* **Foutopsporing in IE**: Ga als volgt te werk om fouten op te sporen in de AEM Forms-werkruimte in IE:  [https://msdn.microsoft.com/en-us/library/hh772704(v=vs.85).aspx](https://msdn.microsoft.com/en-us/library/hh772704(v=vs.85).aspx).

* **Foutopsporing in Chrome**: Als u foutopsporing wilt openen in Chrome, gebruikt u de sneltoets: Ctrl+Shift+I. Zie voor meer informatie:  [https://developer.chrome.com/extensions/tut_debugging.html](https://developer.chrome.com/extensions/tut_debugging.html).

* **Foutopsporing in Firefox**: Er zijn verschillende invoegtoepassingen beschikbaar voor foutopsporing in scripts en stijlen in Firefox. Firebug is bijvoorbeeld een hulpprogramma voor foutopsporing ([https://getfirebug.com](https://getfirebug.com)).

## Veelgestelde vragen {#faqs}

1. PDF-formulier wordt niet gegenereerd of verzonden in Google Chrome.

   1. Installeer de Adobe® Reader® plug-in.
   1. Open chrome://plugins in Chrome om beschikbare plug-ins weer te geven.
   1. Schakel de insteekmodule Chrome PDF Viewer uit en schakel de insteekmodule Adobe Reader in.

1. SWF-formulier of -hulplijn wordt niet weergegeven in Google Chrome.

   1. Open chrome://plugins in Chrome om beschikbare plug-ins weer te geven.
   1. Zie details voor Adobe Flash® Player plug-in.
   1. PepperFlash uitschakelen onder Adobe Flash Player-plug-in.

1. Ik heb de werkruimte van AEM Forms aangepast, maar ik kan de wijzigingen niet zien.

   Wis het cachegeheugen van uw browser en open vervolgens de AEM Forms-werkruimte.

1. Wat moet de gebruiker doen om ervoor te zorgen dat het formulier wordt weergegeven in HTML wanneer het wordt geopend in een desktopcomputer?

   Selecteer het HTML-keuzerondje voor het standaardprofiel in de taakstap toewijzen tijdens het gebruik van Workbench.

1. Bijlage wordt niet weergegeven wanneer erop wordt geklikt.

   Schakel popups in uw browser in om bijlagen weer te geven.

1. Een gebruiker wordt aangemeld bij een formuliertoepassing. Als de gebruiker zich probeert aan te melden bij de werkruimte, wordt het mogelijk niet geladen als de gebruiker geen werkruimtemachtigingen heeft.

   Meld u af bij de andere formuliertoepassing en meld u vervolgens aan bij de werkruimte.

1. In HTML-formulieren die gebruikmaken van proceseigenschappen in hun ontwerp, wordt de knop Verzenden in het formulier weergegeven wanneer deze worden weergegeven in de AEM Forms-werkruimte.

   Wanneer u formulieren ontwerpt en proceseigenschappen gebruikt, wordt een knop Verzenden toegevoegd aan het formulier. Als de PDF in de AEM Forms-werkruimte wordt gerenderd, is de knop Verzenden niet zichtbaar voor de eindgebruiker. Wanneer echter een HTML-formulier wordt weergegeven in de AEM Forms-werkruimte, is de knop Verzenden zichtbaar voor de eindgebruiker. Als u op deze knop Verzenden klikt in het formulier, wordt er geen actie gestart. Als u klikt op de knop Verzenden onder aan de AEM Forms-werkruimte, buiten het formulier, wordt de taak voltooid.
