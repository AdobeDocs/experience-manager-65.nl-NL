---
title: Eigenschappen van Correspondentenbeheer
seo-title: Correspondence Management Configuration Properties
description: Dit onderwerp verklaart hoe u de Composer van Activa met oplossing-specifieke configuraties kunt wijzigen. In dit onderwerp worden de eigenschappen beschreven die u kunt bewerken, met de beschrijving, standaardwaarden en acceptabele waarden.
seo-description: This topic explains how you can modify Asset Composer with solution-specific configurations. This topic details the properties you can edit, with their description, default values, and acceptable values.
uuid: 6b401d51-9332-459b-b751-42a9b5a1462d
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: correspondence-management
discoiquuid: f2955419-c680-44a7-9913-c594b4577551
feature: Correspondence Management
exl-id: c9c007d0-c545-4738-b11b-4c50986342ee
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '845'
ht-degree: 1%

---

# Eigenschappen van Correspondentenbeheer {#correspondence-management-configuration-properties}

Als u deze eigenschappen wilt configureren, opent u de volgende URL in een browser: `https://<server>:<port>/<contextPath>/system/console/configMgr` en selecteert u **Correspondentiebeheerconfiguraties**.

Correspondentiebeheer heeft de volgende configuratie-eigenschappen:

<table>
 <tbody>
  <tr>
   <th><p><strong>Eigenschap</strong></p> </th>
   <th><p><strong>Beschrijving</strong></p> </th>
   <th><p><strong>Standaard</strong></p> </th>
   <th><p><strong>Acceptabele waarden</strong></p> </th>
  </tr>
  <tr>
   <td><p>Inspringing</p> </td>
   <td>Inspringing op modules<p> </p> </td>
   <td><p>12.7mm</p> </td>
   <td><p>Willekeurig getal</p> </td>
  </tr>
  <tr>
   <td>Minimumbreedte aantal</td>
   <td>Minimumbreedte die moet worden toegepast op het veld opsommingsteken/nummer wanneer u genummerde lijsten naast Romeinse nummers gebruikt</td>
   <td>8.0mm</td>
   <td>Willekeurig getal</td>
  </tr>
  <tr>
   <td><p>Roman Numbers Minimum Width</p> </td>
   <td><p>Minimumbreedte die moet worden toegepast op het veld opsommingsteken/nummer bij gebruik van Romeinse getallen</p> </td>
   <td><p>12.7mm</p> </td>
   <td><p>Willekeurig getal</p> </td>
  </tr>
  <tr>
   <td>Type vertoning</td>
   <td>Het type uitvoering dat de toepassing Correspondentie maken gebruikt om de lettervoorvertoning weer te geven. </td>
   <td>HTML-vertoning</td>
   <td>HTML-vertoning / PDF-vertoning</td>
  </tr>
  <tr>
   <td><p>CCR-markering PDF inschakelen</p> </td>
   <td><p>Hiermee wordt markering bij PDF ingeschakeld in de toepassing Correspondentie maken</p> </td>
   <td><p>true</p> </td>
   <td><p>true / false</p> </td>
  </tr>
  <tr>
   <td><p>Type markering doel</p> </td>
   <td><p>Type hooglicht doel in de toepassing Correspondentie maken</p> </td>
   <td><p>border</p> </td>
   <td><p>border / fill / none</p> </td>
  </tr>
  <tr>
   <td><p>Markeerkleur doel</p> </td>
   <td><p>Markeringskleur doel in de toepassing Correspondentie maken</p> </td>
   <td><p>90;155;245</p> </td>
   <td><p>Elke RGB-kleur in de indeling R;G;B</p> </td>
  </tr>
  <tr>
   <td><p>Type markering van inhoud</p> </td>
   <td><p>Type markering voor inhoud in de toepassing Correspondentie maken</p> </td>
   <td><p>Vullen</p> </td>
   <td><p>border / fill / none</p> </td>
  </tr>
  <tr>
   <td><p>Markeerkleur inhoud</p> </td>
   <td><p>Markeringskleur voor inhoud in de toepassing Correspondentie maken</p> </td>
   <td><p>210;225;245</p> </td>
   <td><p>Elke RGB-kleur in de indeling R;G;B</p> </td>
  </tr>
  <tr>
   <td><p>Type markering veld</p> </td>
   <td><p>Type veldmarkering in de toepassing Correspondentie maken</p> </td>
   <td><p>vullen</p> </td>
   <td><p>border / fill / none</p> </td>
  </tr>
  <tr>
   <td><p>Markeerkleur veld</p> </td>
   <td><p>Markeerkleur veld in toepassing Correspondentie maken</p> </td>
   <td><p>210;225;245</p> </td>
   <td><p>Elke RGB-kleur in de indeling R;G;B</p> </td>
  </tr>
  <tr>
   <td><p>Time-out toepassing</p> </td>
   <td><p>Vertraging toepassing in seconden</p> </td>
   <td><p>1200</p> </td>
   <td><p>Willekeurig getal</p> </td>
  </tr>
  <tr>
   <td><p>Naam van PDF-documentparameter</p> </td>
   <td><p>Parameternaam voor PDF-document na verwerking</p> </td>
   <td><p>inPDFDoc</p> </td>
   <td><p>Willekeurige naam van tekenreeksvariabele</p> </td>
  </tr>
  <tr>
   <td><p>Naam XML-gegevensparameter</p> </td>
   <td><p>Parameternaam voor XML-document (gegevens) na verwerking</p> </td>
   <td><p>inXMLDoc</p> </td>
   <td><p>Willekeurige naam van tekenreeksvariabele</p> </td>
  </tr>
  <tr>
   <td><p>Naam van XDP-documentparameter</p> </td>
   <td><p>Parameternaam voor XDP-document dat naar het postproces wordt verzonden</p> </td>
   <td><p>inXDPDoc</p> </td>
   <td><p>Willekeurige naam van tekenreeksvariabele</p> </td>
  </tr>
  <tr>
   <td><p>Naam URL-parameter omleiden</p> </td>
   <td><p>Parameternaam voor de omleidings-URL die wordt verzonden vanuit het postproces Deze waarde kan elke naam van een tekenreeksvariabele zijn</p> </td>
   <td><p>redirectURL</p> </td>
   <td><p>Willekeurige naam van tekenreeksvariabele</p> </td>
  </tr>
  <tr>
   <td><p>Type PDF verzenden</p> </td>
   <td><p>PDF Verzendtype (type PDF dat wordt gegenereerd bij verzending via de toepassing Correspondentie maken)</p> </td>
   <td><p>nonInteractive</p> </td>
   <td><p>interactief/niet-interactief</p> </td>
  </tr>
  <tr>
   <td><p>Gegevenswoordenboekinstantie optimaliseren</p> </td>
   <td><p>Maakt geoptimaliseerde overdracht van gegevenswoordenboekinstantie via b/w-server en -client mogelijk</p> </td>
   <td><p>true</p> </td>
   <td><p>true / false</p> </td>
  </tr>
  <tr>
   <td><p>Inconsistenties automatisch corrigeren </p> </td>
   <td><p>Wanneer toegelaten, behandelt het automatisch de mogelijke inconsistenties in de Toewijzingen van de Brief</p> </td>
   <td><p>true</p> </td>
   <td><p>true / false</p> </td>
  </tr>
  <tr>
   <td><p>Gevormde gegevensindelingen gebruiken</p> </td>
   <td><p>Bepaalt of Vormde gegevens moeten worden gebruikt, formaten bewerken en de indeling Gegevensweergave</p> </td>
   <td><p>true</p> </td>
   <td><p>true / false</p> </td>
  </tr>
  <tr>
   <td><p>Indelingen voor gegevensweergave</p> </td>
   <td><p>Hiermee wordt de specifieke landinstelling voor gegevensweergave opgegeven</p> </td>
   <td><p>locale=nl_NL; dateFormat=dd-MM-yyyy; numberDecimalSeparator=.; numberGroupSeparator=,; numberUseGroupSeparator=truelocale=de_DE; dateFormat=dd-MM-yyyy; numberDecimalSeparator=,; numberGroupSeparator=.; numberUseGroupSeparator=truelocale=fr_FR; dateFormat=dd-MM-yyyy; numberDecimalSeparator=,; numberGroupSeparator= ; numberUseGroupSeparator=truelocale=ja_JP; dateFormat=dd-MM-yyyy; numberDecimalSeparator=.; numberGroupSeparator=,; numberUseGroupSeparator=true</p> </td>
   <td><p>—</p> </td>
  </tr>
  <tr>
   <td><p>Gegevensbewerkingsindeling</p> </td>
   <td><p>Opmaak voor gegevens bewerken. Dit wordt gebruikt wanneer het schrijven van gegevens als Koord of het ontleden gegevens van Koord</p> </td>
   <td><p>locale=nl_NL; dateFormat=dd-MM-yyyy; numberDecimalSeparator=.; numberGroupSeparator=,; numberUseGroupSeparator=true</p> </td>
   <td>--<p> </p> </td>
  </tr>
  <tr>
   <td><p>Lettervarianten beheren bij publicatie</p> </td>
   <td><p>De functie Letter beheren in-/uitschakelen (alleen van toepassing op publicatieserver)</p> </td>
   <td><p>false</p> </td>
   <td><p>true / false</p> </td>
  </tr>
  <tr>
   <td><p>Audit inschakelen</p> </td>
   <td><p>De auditfunctie in-/uitschakelen. Indien onwaar, worden auditlogs voor alle acties uitgeschakeld</p> </td>
   <td><p>false</p> </td>
   <td><p>true / false</p> </td>
  </tr>
  <tr>
   <td><p>Controle lezen inschakelen</p> </td>
   <td><p>De auditfunctionaliteit voor het lezen van elementen inschakelen/uitschakelen</p> </td>
   <td><p>false</p> </td>
   <td><p>true / false</p> </td>
  </tr>
  <tr>
   <td><p>Audit maken</p> </td>
   <td><p>De auditfunctionaliteit inschakelen/uitschakelen voor het maken van elementen</p> </td>
   <td><p>false</p> </td>
   <td><p>true / false</p> </td>
  </tr>
  <tr>
   <td><p>Update Audit inschakelen</p> </td>
   <td><p>De auditfunctionaliteit inschakelen/uitschakelen voor het bijwerken van elementen</p> </td>
   <td><p>false</p> </td>
   <td><p>true / false</p> </td>
  </tr>
  <tr>
   <td><p>Audit herstellen inschakelen</p> </td>
   <td><p>De auditfunctie voor het terugzetten van elementen in-/uitschakelen</p> </td>
   <td><p>false</p> </td>
   <td><p>true / false</p> </td>
  </tr>
  <tr>
   <td><p>Publicatie-controle inschakelen</p> </td>
   <td><p>De auditfunctionaliteit voor het publiceren van elementen inschakelen/uitschakelen</p> </td>
   <td><p>false</p> </td>
   <td><p>true / false</p> </td>
  </tr>
  <tr>
   <td><p>SaveAsDraft-controle inschakelen</p> </td>
   <td><p>De auditfunctionaliteit inschakelen/uitschakelen voor het opslaan van letterconcepten</p> </td>
   <td><p>false</p> </td>
   <td><p>true / false</p> </td>
  </tr>
  <tr>
   <td><p>Controle verzenden inschakelen</p> </td>
   <td><p>De auditfunctie inschakelen/uitschakelen voor verzenden van brief</p> </td>
   <td><p>false</p> </td>
   <td><p>true / false</p> </td>
  </tr>
  <tr>
   <td><p>E-mailcontrole inschakelen</p> </td>
   <td><p>De auditfunctie voor e-mailbrieven inschakelen/uitschakelen</p> </td>
   <td><p>false</p> </td>
   <td><p>true / false</p> </td>
  </tr>
  <tr>
   <td><p>Afdrukcontrole inschakelen</p> </td>
   <td><p>De auditfunctie voor het afdrukken van letters in-/uitschakelen</p> </td>
   <td><p>false</p> </td>
   <td><p>true / false</p> </td>
  </tr>
  <tr>
   <td><p>Aangepaste leveringscontrole inschakelen</p> </td>
   <td><p>Auditfunctionaliteit inschakelen/uitschakelen voor aangepaste levering van letters</p> </td>
   <td><p>false</p> </td>
   <td><p>true / false</p> </td>
  </tr>
  <tr>
   <td><p>Naam van parameter voor bijlagen</p> </td>
   <td><p>Parameternaam voor bijlage-documenten die naar het postproces worden verzonden</p> </td>
   <td><p>inAttachmentDocs</p> </td>
   <td><p>Willekeurige naam van tekenreeksvariabele</p> </td>
  </tr>
  <tr>
   <td><p>CM-gebruikersbasis</p> </td>
   <td><p>URL van de map met alle Correspondentenbeheergebruikerselementen</p> </td>
   <td><p>--</p> </td>
   <td><p>Geldige maplocatie</p> </td>
  </tr>
  <tr>
   <td><p>Grootte lettercache</p> </td>
   <td><p>Geef het maximumaantal letters op dat in de cache moet worden opgeslagen.</p> <p>Als u deze waarde wijzigt, wordt de opdracht <code>in-memory</code> cache.</p> </td>
   <td><p>100</p> </td>
   <td><p>Willekeurige numerieke waarde</p> </td>
  </tr>
  <tr>
   <td><p>Lettercache inschakelen</p> </td>
   <td><p>De lettercache in-/uitschakelen.</p> <p>Als u deze waarde wijzigt, wordt de opdracht <code>in-memory </code> cache.</p> </td>
   <td><p>true</p> </td>
   <td><p>true / false</p> </td>
  </tr>
  <tr>
   <td><p>Volgorde gegevenselementen</p> </td>
   <td><p>Hiermee behoudt u gegevenselementen die in de corresponderende interface worden geordend volgens de volgorde in Letter</p> </td>
   <td><p>true</p> </td>
   <td><p>true / false</p> </td>
  </tr>
  <tr>
   <td><p>Ondersteuning voor opnieuw laden</p> </td>
   <td><p>Ondersteuning voor opnieuw laden inschakelen/uitschakelen in letters die op de server worden weergegeven.</p> <p>Als u deze optie uitschakelt, worden de prestaties voor het renderen van letters verbeterd.</p> </td>
   <td><p>false</p> </td>
   <td><p>true / false</p> <p> </p> </td>
  </tr>
  <tr>
   <td>Temp-map</td>
   <td>Locatie van de tijdelijke map.</td>
   <td>acm.tpmFolder</td>
   <td> </td>
  </tr>
  <tr>
   <td>Extern opslaan</td>
   <td>Hiermee worden de Letter-instanties opgeslagen op de opgegeven auteur voor de verwerking.</td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Compatibiliteitsopties</td>
   <td>Compatibiliteitsopties van de indeling configname:configvalue, gescheiden door komma's.</td>
   <td>acm.compatibilityOptions</td>
   <td> </td>
  </tr>
  <tr>
   <td><p>Foutopsporingsdirectory </p> <p> </p> </td>
   <td>Locatie bestandssysteemmap voor foutopsporing. Als de map niet <code>exists</code>Er worden geen foutopsporingsdumps gegenereerd.</td>
   <td>acm.debugDirectory</td>
   <td> </td>
  </tr>
 </tbody>
</table>
