---
title: HTML5-formulierserviceproxy
seo-title: HTML5-formulierserviceproxy
description: De Proxy van de Dienst van HTML5-formulieren is een configuratie om een volmacht voor de voorleggingsdienst te registreren. Om de Volmacht van de Dienst te vormen, specificeer URL van de voorleggingsdienst door request parameter submissionServiceProxy.
seo-description: De Proxy van de Dienst van HTML5-formulieren is een configuratie om een volmacht voor de voorleggingsdienst te registreren. Om de Volmacht van de Dienst te vormen, specificeer URL van de voorleggingsdienst door request parameter submissionServiceProxy.
uuid: 42d6c1da-3945-469d-b429-c33e563ed70c
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
discoiquuid: 081f7c17-4e5d-4c7e-a5c3-5541a29b9d55
docset: aem65
translation-type: tm+mt
source-git-commit: 56c6cfd437ef185336e81373bd5f758205b96317

---


# HTML5-formulierserviceproxy{#html-forms-service-proxy}

De Proxy van de Dienst van HTML5-formulieren is een configuratie om een volmacht voor de voorleggingsdienst te registreren. Om de Volmacht van de Dienst te vormen, specificeer URL van de voorleggingsdienst door verzoekparameter *submissionServiceProxy*.

## Voordelen van de Volmacht van de Dienst {#benefits-of-service-proxy-br}

De serviceproxy verwijdert het volgende:

* Voor de workflow voor HTML5-formulieren moet de verzendservice &quot;/content/xfaforms/submission/default&quot; worden geopend voor gebruikers van HTML5-formulieren. AEM-servers worden blootgesteld aan een groter onbedoeld publiek.
* De service-URL is ingesloten in het runtimemodel van het formulier. Het is niet mogelijk om dienstURL weg te veranderen.
* De verzending bestaat uit twee stappen. Voor het verzenden van de formuliergegevens zijn ten minste twee ritten naar de server vereist. Hierdoor wordt de belasting op de server verhoogd.
* HTML5-formulieren verzenden gegevens in de POST-aanvraag in plaats van in de PDF-aanvraag. Voor werkstromen waarbij zowel PDF- als HTML5-formulieren worden gebruikt, zijn twee verschillende verwerkingsmethoden voor de verzending vereist.

### Topologieën {#topologies-br}

HTML5-formulieren kunnen de volgende topologieën gebruiken om verbinding te maken met AEM-servers.

* Een topologie waarbij AEM Server of HTML5 formulieren gegevens via POST naar de server verzenden.
* Een topologie waar de volmachtsserver POST gegevens naar de server verzendt.

![HTML5 Forms service proxy topologieën](assets/topology.png)

HTML5 Forms service proxy topologieën

HTML5-formulieren maken verbinding met de AEM-servers om serverscripts, webservices en verzendingen uit te voeren. De XFA-runtime van de HTML5-formulieren gebruikt Ajax-aanroepen naar het eindpunt &quot;/bin/xfaforms/submit&quot; met verschillende parameters om verbinding te maken met de AEM-servers. HTML5-formulieren maken verbinding met AEM-servers om de volgende bewerkingen uit te voeren:

#### Server-zijdig manuscripten en de Diensten van het Web uitvoeren {#execute-server-sided-scripts-and-web-services}

De scripts die zijn gemarkeerd om op de server te worden uitgevoerd, worden serverscripts genoemd. De volgende lijst maakt een lijst van alle parameters die in Server-zijde manuscripten en de Diensten van het Web worden gebruikt.

<table>
 <tbody>
  <tr>
   <td><p><strong>Parameter</strong></p> </td>
   <td><p><strong>Beschrijving</strong></p> </td>
  </tr>
  <tr>
   <td><p>activity</p> </td>
   <td><p>De activiteit bevat de gebeurtenissen die het verzoek teweegbrengen. Bijvoorbeeld klikken, afsluiten of wijzigen</p> </td>
  </tr>
  <tr>
   <td><p>contextSom</p> </td>
   <td><p>contextSom bevat SOM-expressie van het object waar gebeurtenissen worden uitgevoerd.</p> </td>
  </tr>
  <tr>
   <td><p>Sjabloonmodel</p> </td>
   <td><p>De sjabloon bevat de sjabloon die wordt gebruikt om het formulier te genereren.</p> </td>
  </tr>
  <tr>
   <td><p>contentRoot</p> </td>
   <td><p>contentRoot bevat de hoofdmap van de sjabloon die wordt gebruikt om het formulier weer te geven.</p> </td>
  </tr>
  <tr>
   <td><p>Data</p> </td>
   <td><p>Gegevens bevatten batchbytes die worden gebruikt om het formulier te genereren.</p> </td>
  </tr>
  <tr>
   <td><p>formDom</p> </td>
   <td><p>formDom bevat DOM van het HTML5-formulier in JSON-indeling.</p> </td>
  </tr>
  <tr>
   <td><p>packet</p> </td>
   <td><p>Het pakket wordt als formulier opgegeven.</p> </td>
  </tr>
  <tr>
   <td><p>debugDir</p> </td>
   <td><p>debugDir bevat de map voor foutopsporing die wordt gebruikt om het formulier te genereren.</p> </td>
  </tr>
 </tbody>
</table>

#### Gegevens verzenden {#submit-data}

Als u op de knop Verzenden klikt, sturen HTML5-formulieren gegevens naar de server. In de volgende tabel worden alle parameters weergegeven die HTML5-formulieren naar de server verzenden.

<table>
 <tbody>
  <tr>
   <td><p><strong>Parameter</strong></p> </td>
   <td><p><strong>Beschrijving</strong></p> </td>
  </tr>
  <tr>
   <td><p>Sjabloonmodel</p> </td>
   <td><p>Sjabloon waarmee het formulier wordt gegenereerd.</p> </td>
  </tr>
  <tr>
   <td><p>contentRoot</p> </td>
   <td><p>de hoofdmap van de sjabloon die wordt gebruikt om het formulier te genereren.</p> </td>
  </tr>
  <tr>
   <td><p>Data</p> </td>
   <td><p>batchbytes die worden gebruikt om het formulier weer te geven.</p> </td>
  </tr>
  <tr>
   <td><p>formDom</p> </td>
   <td><p>DOM van het HTML5-formulier in JSON-indeling.</p> </td>
  </tr>
  <tr>
   <td><p>voorlegger</p> </td>
   <td><p>De URL waar de gegevens-XML wordt gepost.</p> </td>
  </tr>
  <tr>
   <td><p>debugDir</p> </td>
   <td><p>De map voor foutopsporing die wordt gebruikt om het formulier te genereren.</p> </td>
  </tr>
 </tbody>
</table>

#### Hoe werkt de verzendproxy? {#how-nbsp-the-nbsp-submit-proxy-works}

De verzendserviceproxy fungeert als een pass through als de verzender niet aanwezig is in de parameter request. Het fungeert als een doorbraak. Het verzendt het verzoek naar het /bin/xfaforms/submitAction eindpunt en verzendt de reactie naar runtime XFA.

De voorgelegde de dienstvolmacht selecteert een topologie als voorlegger in de verzoekparameter aanwezig is.

* Als AEM-servers de gegevens posten, fungeert de proxyservice als een pass-through. Het verzendt het verzoek naar het /bin/xfaforms/submitAction eindpunt en verzendt de reactie naar runtime XFA.
* Als de volmacht de gegevens post, gaat de volmachtsdienst alle parameters behalve submitUrl tot het */bin/xfaforms/submit* eindpunt over en ontvangt xml bytes in reactiestream. Dan, post de volmachtsdienst de gegevens xml bytes aan submitUrl voor verwerking.

* Voordat gegevens (POST-aanvraag) naar een server worden verzonden, controleren HTML5-formulieren de connectiviteit en beschikbaarheid van de server. HTML-formulieren verzenden een lege hoofdaanvraag naar de server om de connectiviteit en beschikbaarheid te controleren. Als de server beschikbaar is, verzendt het HTML5-formulier gegevens (POST-aanvraag) naar de server. Als de server niet beschikbaar is, wordt een foutbericht weergegeven. *Kan geen verbinding maken met de server.* . De detectie vooraf voorkomt dat gebruikers het formulier kunnen bijvullen. De volmachtsservlet behandelt hoofdverzoek en werpen geen uitzondering.
