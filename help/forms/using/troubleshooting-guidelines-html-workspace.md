---
title: Richtlijnen voor het oplossen van problemen in de AEM Forms-werkruimte
description: Logboeken inschakelen en foutopsporing gebruiken in browser om problemen in de AEM Forms-werkruimte op te lossen.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
exl-id: a054b60a-5e89-4c98-87bc-35669988d160
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: Admin, User, Developer
source-git-commit: e821be5233fd5f6688507096790d219d25903892
workflow-type: tm+mt
source-wordcount: '738'
ht-degree: 0%

---

# Richtlijnen voor het oplossen van problemen in de AEM Forms-werkruimte {#troubleshooting-guidelines-for-aem-forms-workspace}

In dit artikel wordt beschreven hoe u fouten in de AEM Forms-werkruimte kunt opsporen door logboekregistratie in te schakelen en foutopsporing te gebruiken in een browser. Hierin worden ook enkele algemene problemen beschreven die u kunt tegenkomen bij het gebruik van de AEM Forms-werkruimte en de bijbehorende oplossingen.

## Kan het AEM Forms-werkruimtenpakket niet installeren {#unable-to-install-aem-forms-workspace-package}

Nadat u de patch hebt geïnstalleerd, opent u de AEM Forms-werkruimte. Als u de fout Geen resource gevonden tegenkomt, opent u CRX Package Manager en installeert u het `adobe-lc-workspace-pkg-<version>.zip` -pakket opnieuw.

Voer tijdens het installeren van het pakket de volgende stappen uit als er een fout optreedt `javax.jcr.nodetype.ConstraintViolationException: OakConstraint0025: Authorizable property rep:authorizableId may not be removed` :

1. Meld u aan bij CRXDE Lite. De standaard-URL is `https://[localhost]:'port'/lc/crx/de/index.jsp`
1. Verwijder het volgende knooppunt:

   `/home/groups/P/PERM_WORKSPACE_USER`

1. Ga naar Pakketbeheer. De standaard-URL is `https://[localhost]:'port'/lc/crx/packmgr/index.jsp.`
1. Zoek en installeer het `adobe-lc-workspace-pkg-[version].zip` -pakket.
1. Start de toepassingsserver opnieuw.

>[!NOTE]
>
> Het wordt aanbevolen de SDK opnieuw te starten met de opdracht &#39;Ctrl + C&#39;. Het opnieuw opstarten van de AEM SDK met behulp van alternatieve methoden, bijvoorbeeld het stoppen van Java-processen, kan leiden tot inconsistenties in de AEM ontwikkelomgeving.

## Logboek van AEM Forms-werkruimte {#aem-forms-workspace-nbsp-logging}

U kunt logboeken op diverse niveaus produceren om het optimale oplossen van problemen van fouten toe te laten. Bijvoorbeeld, in een complexe toepassing, helpt het registreren op componentenniveau bij het zuiveren en het oplossen van problemen specifieke componenten.

In de AEM Forms-werkruimte:

* Voeg `/log/<ComponentFile>/<LogLevel>` toe aan de URL en druk op `Enter` om de logboekgegevens over een specifiek componentbestand op te halen. Alle logboekinformatie voor het componentendossier op het gespecificeerde logboekniveau wordt gedrukt op de console.

* Als u logboekgegevens van alle deelbestanden wilt opvragen, voegt u `/log/all/trace` toe aan de URL en drukt u op `Enter` .

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

### Logboekniveaus beschikbaar in de AEM Forms-werkruimte {#log-levels-available-in-nbsp-aem-forms-workspace}

* FATAAL
* FOUT
* WAARSCHUWING
* INFO
* DEBUG
* TRACE
* UIT

## Foutopsporingsgegevens voor browsers {#debugging-information-for-browsers}

Scripts en stijlen kunnen in verschillende browsers worden opgespoord.

* **het Zuiveren in IE**: Om de werkruimte van AEM Forms in IE te zuiveren, zie: [&#x200B; https://learn.microsoft.com/en-us/office/dev/add-ins/testing/debug-add-ins-using-f12-tools-ie &#x200B;](https://learn.microsoft.com/en-us/office/dev/add-ins/testing/debug-add-ins-using-f12-tools-ie).

* **het Zuiveren in Chrome**: Om debugger in Chrome te openen, gebruik de kortere weg: Ctrl+Shift+I. Voor meer informatie, zie: [&#x200B; https://developer.chrome.com/docs/extensions/mv3/tut_debugging/ &#x200B;](https://developer.chrome.com/docs/extensions/mv3/tut_debugging/).

* **het Zuiveren in Firefox**: Verscheidene toe:voegen-ons zijn beschikbaar om manuscripten en stijlen in Firefox te zuiveren. Bijvoorbeeld, is het Vuurwerk één dergelijk het zuiveren nut ([&#x200B; https://getfirebug.com &#x200B;](https://getfirebug.com)).

## Veelgestelde vragen {#faqs}

1. PDF-formulier wordt niet gegenereerd of verzonden in Google Chrome.

   1. Installeer de Adobe® Reader® plug-in.
   1. Open chrome://plugins in Chrome om beschikbare plug-ins weer te geven.
   1. Schakel de insteekmodule Chrome PDF Viewer uit en schakel de Adobe Reader-insteekmodule in.

1. SWF formulier of Guide wordt niet weergegeven in Google Chrome.

   1. Open chrome://plugins in Chrome om beschikbare plug-ins weer te geven.
   1. Zie details voor Adobe Flash® Player plug-in.
   1. PepperFlash uitschakelen onder Adobe Flash Player plug-in.

1. Ik heb de werkruimte van AEM Forms aangepast, maar ik kan de wijzigingen niet zien.

   Wis het cachegeheugen van uw browser en open vervolgens de AEM Forms-werkruimte.

1. Wat moet de gebruiker doen om ervoor te zorgen dat het formulier in HTML wordt weergegeven wanneer het wordt geopend op het bureaublad?

   Selecteer het keuzerondje HTML voor het standaardprofiel in de taakstap toewijzen tijdens het gebruik van Workbench.

1. Bijlage wordt niet weergegeven wanneer erop wordt geklikt.

   Schakel popups in uw browser in om bijlagen weer te geven.

1. Een gebruiker wordt aangemeld bij een formuliertoepassing. Als de gebruiker zich probeert aan te melden bij de werkruimte, wordt het mogelijk niet geladen als de gebruiker geen werkruimtemachtigingen heeft.

   Meld u af bij de andere formuliertoepassing en meld u vervolgens aan bij de werkruimte.

1. Als formulieren in de AEM Forms-werkruimte worden gerenderd, met behulp van proceseigenschappen in hun ontwerp, geeft u de knop Verzenden in het formulier weer.

   Wanneer u formulieren ontwerpt en proceseigenschappen gebruikt, wordt een knop Verzenden toegevoegd aan het formulier. Wanneer de knop Verzenden als een PDF wordt weergegeven in de AEM Forms-werkruimte, is deze niet zichtbaar voor de eindgebruiker. Wanneer de weergave als een HTML-formulier in de AEM Forms-werkruimte plaatsvindt, is de knop Verzenden echter zichtbaar voor de eindgebruiker. Als u op deze knop Verzenden klikt in het formulier, wordt er geen actie gestart. Als u klikt op de knop Verzenden onder aan de AEM Forms-werkruimte, buiten het formulier, wordt de taak voltooid.
