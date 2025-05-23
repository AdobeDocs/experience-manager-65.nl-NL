---
title: Synchronisatie van actieve kopie configureren
description: Meer informatie over het configureren van Live Copy-synchronisatie.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: site-features
content-type: reference
docset: aem65
feature: Multi Site Manager
exl-id: ac24b8b4-b3ed-47fa-9a73-03f0c9e68ac8
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: eae057caed533ef16bb541b4ad41b8edd7aaa1c7
workflow-type: tm+mt
source-wordcount: '2672'
ht-degree: 0%

---

# Synchronisatie van actieve kopie configureren{#configuring-live-copy-synchronization}

Voer de volgende taken uit om te controleren hoe en wanneer de levende exemplaren met hun broninhoud worden gesynchroniseerd.

* Bepaal of de bestaande rollout configuraties aan uw vereisten voldoen, of u één of meerdere moet tot stand brengen.
* Geef de rollout-configuraties op die u wilt gebruiken voor uw live kopieën.

## Geïnstalleerde en Aangepaste implementatieconfiguraties {#installed-and-custom-rollout-configurations}

Deze sectie verstrekt informatie over de geïnstalleerde rollout configuraties en de synchronisatieacties die zij gebruiken, en hoe te om douaneconfiguraties tot stand te brengen indien nodig.

>[!CAUTION]
>
>Het bijwerken van of het veranderen van een uit de (geïnstalleerde) doos rollout configuratie wordt **niet** geadviseerd. Als er een vereiste voor een douanelevende actie is dan zou het in een aangepaste rollout configuratie moeten worden toegevoegd.

### Rollouttriggers {#rollout-triggers}

Elke rollout configuratie gebruikt een rollout trekker die de rollout veroorzaakt om voor te komen. Rolloutconfiguraties kunnen een van de volgende triggers gebruiken:

* **op Rollout**: Het **bevel van de Uitvoer** wordt gebruikt op de blauwe drukpagina, of het **synchroniseer** bevel wordt gebruikt op de levende exemplaarpagina.

* **op Wijziging**: De bronpagina wordt gewijzigd.

* **op Activering**: De bronpagina wordt geactiveerd.

* **op Deactivation**: De bronpagina wordt gedeactiveerd.

>[!NOTE]
>
>Het gebruik van de trigger Bij wijziging kan van invloed zijn op de prestaties. Zie [ MSM beste praktijken ](/help/sites-administering/msm-best-practices.md#onmodify) voor meer informatie.

### Geïnstalleerde uitrolconfiguraties {#installed-rollout-configurations}

De volgende lijst maakt een lijst van de rollout configuraties die met AEM geïnstalleerd zijn. De lijst omvat de trekker en synchronisatieacties van elke rollout configuratie. Als de geïnstalleerde acties van de rollout configuratie niet aan uw vereisten voldoen, kunt u [ een rollout configuratie ](#creating-a-rollout-configuration) tot stand brengen.

<table>
 <tbody>
  <tr>
   <th>Naam</th>
   <th>Beschrijving</th>
   <th>Trigger</th>
   <th>De Acties van de synchronisatie <br /> <br /> zien ook <a href="#installed-synchronization-actions"> Geïnstalleerde Acties van de Synchronisatie </a></th>
  </tr>
  <tr>
   <td>Standaardconfiguratie voor rollout</td>
   <td>Standaardrollout-configuratie waarmee u het implementatieproces kunt starten bij rollout-trigger en acties kunt uitvoeren: maken, bijwerken, inhoud verwijderen en onderliggende knooppunten ordenen.</td>
   <td>Bij rollout</td>
   <td>contentUpdate <br /> contentCopy <br /> contentDelete <br /> referencesUpdate <br /> productUpdate <br /> orderChildren</td>
  </tr>
  <tr>
   <td>Activeren bij activering van blauwdruk</td>
   <td>De live kopie wordt gepubliceerd wanneer de bron wordt gepubliceerd.</td>
   <td>Bij activering</td>
   <td>targetActivate</td>
  </tr>
  <tr>
   <td>Deactiveren bij deactivering van blauwdruk</td>
   <td>Hiermee wordt de actieve kopie gedeactiveerd wanneer de bron wordt gedeactiveerd.</td>
   <td>Bij deactivering</td>
   <td>targetDeactivate<br /> </td>
  </tr>
  <tr>
   <td>Verschuiven bij wijzigen</td>
   <td><p>Hiermee wordt de inhoud naar de live kopie gespoeld wanneer de bron wordt gewijzigd.</p> <p>Gebruik spaarzaam deze rollout configuratie aangezien het bij de trekker van de Wijziging gebruikt.</p> </td>
   <td>Bij wijziging</td>
   <td>contentUpdate <br /> contentCopy <br /> contentDelete <br /> referencesUpdate <br /> orderChildren <br /> </td>
  </tr>
  <tr>
   <td>Ingedrukt op wijzigen (ondiep)</td>
   <td><p>Hiermee wordt inhoud naar de live kopie gespoeld wanneer de pagina met de blauwdruk wordt gewijzigd, zonder referenties bij te werken (bijvoorbeeld voor oppervlakkige kopieën).</p> <p>Gebruik spaarzaam deze rollout configuratie aangezien het bij de trekker van de Wijziging gebruikt.</p> </td>
   <td>Bij wijziging</td>
   <td>contentUpdate <br /> contentCopy <br /> contentDelete <br /> orderChildren</td>
  </tr>
  <tr>
   <td>Starten bevorderen</td>
   <td>Standaardrollout-configuratie voor het promoten van opstartiepagina's.</td>
   <td>Bij rollout</td>
   <td>contentUpdate <br /> contentCopy <br /> contentDelete <br /> referencesUpdate <br /> orderChildren <br /> markLiveRelationship</td>
  </tr>
  <tr>
   <td>Config. voor het uitvoeren van inhoud voor cataloguspagina</td>
   <td>Hiermee past u paginasjablonen toe vanuit een catalogusblauwdruk.</td>
   <td>Bij rollout</td>
   <td>contentUpdate <br /> contentCopy <br /> contentDelete <br /> referencesUpdate <br /> productCreateUpdate <br /> orderChildren</td>
  </tr>
  <tr>
   <td>Uitrolconfiguratie van cataloguspagina bijwerken</td>
   <td>Past doeleigenschappen van een catalogusblauwdruk toe. Moet worden uitgevoerd na configuratie voor het uitvoeren van cataloguspagina-inhoud.</td>
   <td>Bij rollout</td>
   <td>catalogRolloutHooks</td>
  </tr>
  <tr>
   <td>DPS-configuratie voor publicatie</td>
   <td>Configuratie voor rollout van DPS-publicatie waarmee u het implementatieproces kunt starten bij rollout-trigger en tegelijkertijd bindingseigenschappen van FolioProducer bij de eerste rollout kunt uitsluiten</td>
   <td>Bij rollout</td>
   <td>contentUpdate <br /> contentCopy <br /> contentDelete <br /> referencesUpdate <br /> orderChildren <br /> dpsMetadataFilter</td>
  </tr>
  <tr>
   <td>Verouderde (5.6.0) configuratie van de Catalogusuitrol</td>
   <td>Vervangen. Gebruik Catalogusgenerator in plaats van MSM voor catalogusrollouts.</td>
   <td>Bij rollout</td>
   <td>editProperties</td>
  </tr>
 </tbody>
</table>

### Geïnstalleerde synchronisatiehandelingen {#installed-synchronization-actions}

De volgende lijst maakt een lijst van de synchronisatieacties die met AEM geïnstalleerd zijn. Als de geïnstalleerde acties niet aan uw vereisten voldoen, kunt u [ een Nieuwe Actie van de Synchronisatie ](/help/sites-developing/extending-msm.md#creating-a-new-synchronization-action) tot stand brengen.

<table>
 <tbody>
  <tr>
   <th>Naam van handeling</th>
   <th>Beschrijving</th>
   <th>Eigenschappen <br /> </th>
  </tr>
  <tr>
   <td>contentCopy</td>
   <td>Wanneer knooppunten van de bron niet op de live kopie bestaan, worden de knooppunten naar de live kopie gekopieerd. <a href="#excluding-properties-and-node-types-from-synchronization"> vorm de dienst van de Actie van het Exemplaar van de Inhoud CQ MSM </a> om de knooptypes, paragraafpunten, en paginaeigenschappen te specificeren om uit te sluiten. <br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td>contentDelete</td>
   <td><p>Verwijdert knooppunten van de live kopie die niet op de bron bestaan. <a href="#excluding-properties-and-node-types-from-synchronization"> vorm de CQ MSM Inhoud de dienst van de Actie van de Schrapping </a> om de knooptypes, paragraafpunten, en paginaeigenschappen te specificeren om uit te sluiten. </p> </td>
   <td> </td>
  </tr>
  <tr>
   <td>contentUpdate</td>
   <td>Hiermee werkt u de inhoud van de live kopie bij met de wijzigingen van de bron. <a href="#excluding-properties-and-node-types-from-synchronization"> vormt de dienst van de Actie van de Update van de Inhoud CQ MSM </a> om de knooptypes, paragraafpunten, en paginaeigenschappen te specificeren om uit te sluiten. <br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td>editProperties</td>
   <td><p>Hiermee bewerkt u de eigenschappen van de actieve kopie. De eigenschap editMap bepaalt welke eigenschappen worden bewerkt en de waarde ervan. De waarde van de eigenschap editMap moet de volgende indeling gebruiken:</p> <p><code>[property_name_1]#[current_value]#</code>[new_value],<br /> <code>[property_name_2]#[current_value]#</code>[new_value], <br /> ..., <br /> <code>[property_name_n]#[current_value]#</code>[new_value]</p> <p>De items <code>current_value</code> en <code>new_value</code> zijn reguliere expressies. <br /> </p> <p>Neem bijvoorbeeld de volgende waarde voor editMap:</p> <p><code>sling:resourceType#/</code>(contentPage|homepage)#/<br /> mobileContentPage, <br /> cq:template#/contentPage#/mobileContentPage</p> <p>Met deze waarde worden de eigenschappen van de knooppunten van de live kopie als volgt bewerkt:</p>
    <ul>
     <li>De <code>sling:resourceType</code> -eigenschappen die zijn ingesteld op <code>contentpage</code> of op <code>homepage</code> , worden ingesteld op <code>mobilecontentpage.</code></li>
     <li>De <code>cq:template</code> -eigenschappen die zijn ingesteld op <code>contentpage</code> , worden ingesteld op <code>mobilecontentpage.</code></li>
    </ul> </td>
   <td><p> </p> <p>editMap: (String) Hiermee worden de eigenschap, de huidige waarde en de nieuwe waarde aangegeven. Zie de Beschrijving voor informatie.<br /> </p> </td>
  </tr>
  <tr>
   <td>meedelen</td>
   <td>Verstuurt een paginagebeurtenis die de pagina heeft uitgerold. Om op de hoogte te worden gebracht, moet u zich eerst abonneren op rollout-gebeurtenissen.</td>
   <td> </td>
  </tr>
  <tr>
   <td>orderChildren</td>
   <td>Voor het levende exemplaar, orden het de kinderen (knopen), die op de orde op de blauwdruk worden gebaseerd <br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td>referencesUpdate</td>
   <td><p>Voor de live kopie werkt deze synchronisatiehandeling verwijzingen zoals koppelingen bij.<br /> Er wordt gezocht naar paden op de pagina's met live kopieën die verwijzen naar een bron in de blauwdruk. Wanneer gevonden, werkt het de weg bij om aan het verwante middel binnen het levende exemplaar (in plaats van het blauwdruk) te richten. Verwijzingen die doelen buiten de blauwdruk hebben, worden niet gewijzigd.</p> <p><a href="#excluding-properties-and-node-types-from-synchronization"> vormt de dienst van de Actie van de Update van de Verwijzingen CQ MSM </a> om de knooptypes, paragraafpunten, en paginaeigenschappen te specificeren om uit te sluiten. </p> </td>
   <td> </td>
  </tr>
  <tr>
   <td>targetVersion</td>
   <td><p>Hiermee maakt u een versie van de actieve kopie.</p> <p>Deze actie moet de enige synchronisatieactie inbegrepen in een rollout configuratie zijn.</p> </td>
   <td> </td>
  </tr>
  <tr>
   <td>targetActivate</td>
   <td><p>Hiermee activeert u de live kopie.</p> <p>Deze actie moet de enige synchronisatieactie inbegrepen in een rollout configuratie zijn.</p> </td>
   <td> </td>
  </tr>
  <tr>
   <td>targetDeactivate</td>
   <td><p>Hiermee wordt de actieve kopie gedeactiveerd.</p> <p>Deze actie moet de enige synchronisatieactie inbegrepen in een rollout configuratie zijn.</p> </td>
   <td> </td>
  </tr>
  <tr>
   <td>werkstroom</td>
   <td><p>Hiermee wordt de workflow gestart die door de eigenschap target (alleen voor pagina's) wordt gedefinieerd en wordt de live kopie als een payload ingesteld.</p> <p>Het doelpad is het pad van het modelknooppunt.</p> </td>
   <td>target: (Koord) de weg aan het werkschemamodel.<br /> </td>
  </tr>
  <tr>
   <td>verplicht</td>
   <td><p>Plaatst de toestemming van verscheidene ACLs op de levende exemplaarpagina aan read-only voor een specifieke gebruikersgroep. De volgende ACLs wordt gevormd:</p>
    <ul>
     <li>ActionSet.ACTION_NAME_REMOVE</li>
     <li>ActionSet.ACTION_NAME_SET_PROPERTY</li>
     <li>ActionSet.ACTION_NAME_ACL_MODIFY</li>
    </ul> <p>Gebruik deze handeling alleen voor pagina's.</p> </td>
   <td>target: (String) De id van de groep waarvoor u machtigingen instelt. <br /> </td>
  </tr>
  <tr>
   <td>mandatoryContent</td>
   <td><p>Plaatst de toestemming van verscheidene ACLs op de levende exemplaarpagina aan read-only voor een specifieke gebruikersgroep. De volgende ACLs wordt gevormd:</p>
    <ul>
     <li>ActionSet.ACTION_NAME_SET_PROPERTY</li>
     <li>ActionSet.ACTION_NAME_ACL_MODIFY</li>
    </ul> <p>Gebruik deze handeling alleen voor pagina's.</p> </td>
   <td>target: (String) De id van de groep waarvoor u machtigingen instelt. </td>
  </tr>
  <tr>
   <td>mandatoryStructure</td>
   <td>Plaatst de toestemming van ACL ActionSet.ACTION_NAME_REMOVE op de levende exemplaarpagina aan read-only voor een specifieke gebruikersgroep. Gebruik deze handeling alleen voor pagina's.</td>
   <td>target: (String) De id van de groep waarvoor u machtigingen instelt. </td>
  </tr>
  <tr>
   <td>VersionCopyAction</td>
   <td>Als de blauwdruk-/bronpagina ten minste één keer is gepubliceerd, wordt een pagina voor live kopieën gemaakt met de versie die wordt gepubliceerd. Opmerking: deze handeling is alleen beschikbaar voor het maken van een pagina voor live kopieën op basis van een gepubliceerde bronpagina, niet voor het bijwerken van een bestaande pagina voor live kopieën. </td>
   <td> </td>
  </tr>
  <tr>
   <td>PageMoveAction</td>
   <td><p>De PageMoveAction is van toepassing wanneer een pagina in de blauwdruk is verplaatst.</p> <p>De actie kopieert eerder dan verplaatst de (verwante) pagina LiveCopy van de plaats vóór de beweging aan de plaats na.</p> <p>De PageMoveAction verandert niet de pagina LiveCopy bij de plaats vóór de beweging. Daarom voor opeenvolgende RolloutConfigurations heeft het de status van een LiveRelationship zonder Blauwdruk.</p> <p><a href="#excluding-properties-and-node-types-from-synchronization"> vormt de dienst van de Actie van de Beweging van de Pagina CQ MSM </a> om de knooptypes, paragraafpunten, en paginaeigenschappen te specificeren om uit te sluiten. </p> <p>Deze actie moet de enige synchronisatieactie inbegrepen in een rollout configuratie zijn.</p> </td>
   <td><p>prop_referenceUpdate: (Boolean) Ingesteld op true om verwijzingen bij te werken. De standaardwaarde is true.</p> <p> </p> </td>
  </tr>
  <tr>
   <td>productCreateUpdate</td>
   <td>Hiermee maakt of werkt u productbronnen in een catalogus bij. Deze actie is bedoeld om in één van de volgende situaties te worden gebruikt:
    <ul>
     <li>Een catalogus genereren of implementeren (of sectie Catalogus)</li>
     <li>Een gebruiker herstelt synchronisatieovererving voor een productcomponent.</li>
    </ul> </td>
   <td> </td>
  </tr>
  <tr>
   <td>markLiveRelationship</td>
   <td>Geeft aan dat er een live relatie bestaat voor inhoud die is gestart.</td>
   <td> </td>
  </tr>
  <tr>
   <td>catalogRolloutHooks</td>
   <td>Voert catalogus-generatie-specifieke rollout haken uit. Roept de methoden executePageRolloutHooks en executeProductRolloutHooks van de CatalogGenerator aan.<br /> Zie com.adobe.cq.commerce.pim.api.CatalogGenerator in de AEM Javadocs.</td>
   <td> </td>
  </tr>
  <tr>
   <td>productUpdate</td>
   <td>Hiermee werkt u productpagina's bij in een live kopie van een productcatalogus</td>
   <td> </td>
  </tr>
 </tbody>
</table>

### Een rollout-configuratie maken {#creating-a-rollout-configuration}

U kunt [ een rollout configuratie ](/help/sites-developing/extending-msm.md#creating-a-new-rollout-configuration) tot stand brengen wanneer de geïnstalleerde rollout configuraties niet aan uw toepassingsvereisten voldoen:

* [ creeer de rollout configuratie ](/help/sites-developing/extending-msm.md#create-the-rollout-configuration).
* [ voegt synchronisatieacties aan de rollout configuratie ](/help/sites-developing/extending-msm.md#add-synchronization-actions-to-the-rollout-configuration) toe.

De nieuwe rollout configuratie is dan beschikbaar aan u wanneer het plaatsen van rollout configuraties op een blauwdruk of een levende exemplaarpagina.

### Eigenschappen en knooppunttypen uitsluiten van synchronisatie {#excluding-properties-and-node-types-from-synchronization}

U kunt verscheidene diensten vormen OSGi die overeenkomstige synchronisatieacties steunen zodat zij geen specifieke knooptypes en eigenschappen beïnvloeden. Veel eigenschappen en subknooppunten die bijvoorbeeld betrekking hebben op de interne werking van AEM, mogen niet in een live kopie worden opgenomen. Alleen de inhoud die relevant is voor de gebruiker van de pagina moet worden gekopieerd.

Wanneer het werken met AEM, zijn er verscheidene methodes om de configuratiemontages voor dergelijke diensten te beheren; zie [ Vormend OSGi ](/help/sites-deploying/configuring-osgi.md) voor meer details en de geadviseerde praktijken.

In de volgende tabel worden de synchronisatiehandelingen weergegeven waarvoor u de knooppunten kunt opgeven die moeten worden uitgesloten. De lijst verstrekt de namen van de diensten om het gebruiken van de Console en PID van het Web voor het vormen van het gebruiken van een gegevensopslagknoop te vormen.

| Synchronisatie-actie | Servicenaam in webconsole | Service PID |
|---|---|---|
| contentCopy | CQ MSM-inhoud kopiëren, actie | com.day.cq.wcm.msm.impl.actions.ContentCopyActionFactory |
| contentDelete | CQ MSM-inhoud Handeling verwijderen | com.day.cq.wcm.msm.impl.actions.ContentDeleteActionFactory |
| contentUpdate | Update-actie CQ MSM-inhoud | com.day.cq.wcm.msm.impl.actions.ContentUpdateActionFactory |
| PageMoveAction | Handeling Verplaatsen CQ MSM-pagina | com.day.cq.wcm.msm.impl.actions.PageMoveActionFactory |
| referencesUpdate | Update-actie CQ MSM-verwijzingen | com.day.cq.wcm.msm.impl.actions.ReferencesUpdateActionFactory |

In de volgende tabel worden de eigenschappen beschreven die u kunt configureren:

<table>
 <tbody>
  <tr>
   <th>Web Console-eigenschap / OSGi-eigenschap</th>
   <th>Beschrijving</th>
  </tr>
  <tr>
   <td><p>Uitgesloten knooppunten</p> <p>cq.wcm.msm.action.excludednodetypes</p> </td>
   <td>Een reguliere expressie die overeenkomt met de knooppunttypen die moeten worden uitgesloten van de synchronisatiehandeling.</td>
  </tr>
  <tr>
   <td><p>Uitgesloten alinea-items</p> <p>cq.wcm.msm.action.excludedparagraphitems</p> </td>
   <td>Een reguliere expressie die overeenkomt met de alinea-items die moeten worden uitgesloten van de synchronisatiehandeling.</td>
  </tr>
  <tr>
   <td><p>Eigenschappen van uitgesloten pagina</p> <p>cq.wcm.msm.action.excludedprops</p> </td>
   <td>Een reguliere expressie die overeenkomt met de pagina-eigenschappen die moeten worden uitgesloten van de synchronisatiehandeling.</td>
  </tr>
  <tr>
   <td><p>Genegeerde Mixin NodeTypes</p> <p>cq.wcm.msm.action.ignoredMixin</p> </td>
   <td>Alleen beschikbaar voor CQ MSM Content Update Action. Een reguliere expressie die overeenkomt met de namen van knooppunttypen die moeten worden uitgesloten van de synchronisatiehandeling.</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>In de klassieke gebruikersinterface geeft het vergrendelingspictogram dat in het dialoogvenster Pagina-eigenschappen voor LiveCopy-pagina&#39;s wordt weergegeven, niet de configuratie van de eigenschap Eigenschappen van uitgesloten pagina weer. Het vergrendelingspictogram wordt zelfs weergegeven voor eigenschappen die zijn uitgesloten van de synchronisatiehandeling.

>[!NOTE]
>
>In aanraking-geoptimaliseerde UI zie ook [ Vormend Msm Locks op de Eigenschappen van de Pagina (aanraking-Geoptimaliseerde UI) ](/help/sites-developing/extending-msm.md#configuring-msm-locks-on-pagep-roperties-touch-optimized-ui).

#### Actie voor bijwerken van CQ MSM-inhoud - Uitsluitingen {#cq-msm-content-update-action-exclusions}

Verscheidene eigenschappen en knooptypes worden uitgesloten door gebrek, worden deze bepaald in de configuratie OSGi van **CQ MSM de Actie van de Update van de Inhoud**, onder **Uitgesloten Eigenschappen van de Pagina**.

Standaard worden eigenschappen die overeenkomen met de volgende reguliere expressies uitgesloten (dat wil zeggen niet bijgewerkt) bij rollout:

![ CQ MSM de Actie van de Update van de Inhoud ](assets/chlimage_1.png)

U kunt de expressies wijzigen die de uitsluitingslijst naar wens definiëren.

Bijvoorbeeld, als u de pagina **Titel** in de veranderingen wilt worden omvat die voor rollout worden overwogen, verwijder `jcr:title` van de uitsluitingen. Bijvoorbeeld met regex:

`jcr:(?!(title)$).*`

### Synchronisatie configureren voor het bijwerken van verwijzingen {#configuring-synchronization-for-updating-references}

U kunt verscheidene diensten vormen OSGi die overeenkomstige synchronisatieacties met betrekking tot het bijwerken van verwijzingen steunen.

Wanneer het werken met AEM, zijn er verscheidene methodes om de configuratiemontages voor dergelijke diensten te beheren; zie [ Vormend OSGi ](/help/sites-deploying/configuring-osgi.md) voor meer details en de geadviseerde praktijken.

In de volgende tabel staan de synchronisatiehandelingen waarvoor u de update van de verwijzing kunt opgeven. De lijst verstrekt de namen van de diensten om het gebruiken van de Console en PID van het Web voor het vormen van het gebruiken van een gegevensopslagknoop te vormen.

<table>
 <tbody>
  <tr>
   <th>Web Console-eigenschap / OSGi-eigenschap</th>
   <th>Beschrijving</th>
  </tr>
  <tr>
   <td><p>Referentie bijwerken in geneste LiveCopy's</p> <p>cq.wcm.msm.impl.action.referencesupdate.prop_updateNested</p> </td>
   <td>Alleen beschikbaar voor Update-actie CQ MSM-verwijzingen. Selecteer deze optie (de Console van het Web) of plaats dit booleaanse bezit aan waar (bewaarplaats configuratie) om verwijzingen te vervangen die om het even welke middel richten dat binnen de tak van top-most LiveCopy is.</td>
  </tr>
  <tr>
   <td><p>Referentiepagina's bijwerken</p> <p>cq.wcm.msm.impl.actions.pagemove.prop_referenceUpdate</p> </td>
   <td>Alleen beschikbaar voor CQ MSM Page Move Action. Selecteer deze optie (Webconsole) of stel deze Booleaanse eigenschap in op <code>true</code> (configuratie van de opslagplaats) om verwijzingen bij te werken naar het gebruik van de oorspronkelijke pagina in plaats van naar de LiveCopy-pagina te verwijzen.</td>
  </tr>
 </tbody>
</table>

## De te gebruiken configuraties voor rollout opgeven {#specifying-the-rollout-configurations-to-use}

MSM laat u toe om reeksen rollout configuraties te specificeren die algemeen worden gebruikt, en wanneer vereist kunt u hen voor specifieke levende exemplaren met voeten treden. MSM verstrekt verscheidene plaatsen voor het specificeren van de rollout configuraties aan gebruik. De locatie bepaalt of de configuratie van toepassing is op een specifieke live kopie.

De volgende lijst van plaatsen waar u de rollout configuraties kunt specificeren om te gebruiken beschrijft hoe MSM bepaalt welke rollout configuraties aan gebruik voor een levende kopie:

* **[Levende eigenschappen van de exemplaarpagina ](/help/sites-administering/msm-sync.md#setting-the-rollout-configurations-for-a-live-copy-page):** wanneer een levende exemplaarpagina wordt gevormd om één of meerdere rollout configuraties te gebruiken, gebruikt MSM die rollout configuraties.
* **[eigenschappen van de pagina van de Vervaging ](/help/sites-administering/msm-sync.md#setting-the-rollout-configuration-for-a-blueprint-page):** wanneer een levend exemplaar op een blauwdruk gebaseerd is, en de levende exemplaarpagina niet met een rollout configuratie wordt gevormd, wordt de rollout configuratie die met de bron van de blauwdruk pagina wordt geassocieerd gebruikt.
* **Levende eigenschappen van de exemplaarouderpagina van het exemplaar:** wanneer noch de levende exemplaarpagina noch de WebPrint bronpagina met een rollout configuratie worden gevormd, wordt de rollout configuratie die op de levende de ouderpagina van de exemplaarpagina van toepassing is gebruikt.
* **[gebrek van het Systeem ](/help/sites-administering/msm-sync.md#setting-the-system-default-rollout-configuration):** wanneer de rollout configuratie van de levende ouder van het exemplaar pagina niet kan worden bepaald, wordt de systeem standaardrollout configuratie gebruikt.

Bijvoorbeeld, gebruikt een blauwdruk de Site van de Verwijzing Wij.Retail als broninhoud. Op basis van de blauwdruk wordt een site gemaakt. Elk punt in de volgende lijst beschrijft een verschillend scenario betreffende het gebruik van rollout configuraties:

* Geen van de pagina&#39;s van de blauwdruk of de levende exemplaarpagina&#39;s worden gevormd om een rollout configuratie te gebruiken. MSM gebruikt de systeem standaardrollout configuratie voor alle levende exemplaarpagina&#39;s.
* De wortelpagina van de Site van de Verwijzing Wij.Retail wordt gevormd met verscheidene rollout configuraties. MSM gebruikt deze rollout configuraties voor alle levende exemplaarpagina&#39;s.
* De wortelpagina van de Site van de Verwijzing Wij.Retail wordt gevormd met verscheidene rollout configuraties, en de wortelpagina van de levende exemplaarplaats wordt gevormd met een verschillende reeks rollout configuraties. MSM gebruikt de rollout configuraties die op de wortelpagina van de levende exemplaarplaats worden gevormd.

### De rollout-configuraties instellen voor een Live Copy-pagina {#setting-the-rollout-configurations-for-a-live-copy-page}

Vorm een levende exemplaarpagina met de rollout configuraties aan gebruik wanneer de bronpagina uit wordt opgerold. Onderliggende pagina&#39;s nemen de configuratie standaard over. Wanneer u de rollout configuratie aan gebruik vormt, treedt u de configuratie met voeten die de levende exemplaarpagina van zijn ouder erft.

U kunt de rollout configuraties voor een levende exemplaarpagina ook vormen wanneer u [ het levende exemplaar ](/help/sites-administering/msm-livecopy.md#creating-a-live-copy-of-a-page) creeert.

1. Gebruik de **console van Plaatsen** om de levende exemplaarpagina te selecteren.
1. Selecteer **Eigenschappen** van de toolbar.
1. Open het **Levende 1&rbrace; lusje van het Exemplaar &lbrace;.**

   De **sectie van de Configuratie** toont de rollout configuraties die de pagina erft.

   ![ Configuratie ](assets/chlimage_1-1.png)

1. Indien nodig, pas de **Levende markering van de Overerving van het Exemplaar** aan. Als deze optie is ingeschakeld, is de configuratie van de live kopie effectief voor alle onderliggende elementen.

1. Ontruim de **Configuratie van de Overerving van het Bezit van de Output van de Ouder**, dan selecteer één of meerdere rollout configuraties van de lijst.

   De geselecteerde rollout configuraties verschijnen onder de drop-down lijst.

   ![ Geselecteerde Configuraties van de Output ](assets/chlimage_1-2.png)

1. Klik **sparen**.

### De configuratie van de Output instellen voor een vervagingspagina {#setting-the-rollout-configuration-for-a-blueprint-page}

Configureer een blauwdrukpagina met de rollout-configuraties die moeten worden gebruikt wanneer de blauwdrukpagina wordt uitgevouwen.

De onderliggende pagina&#39;s van de blauwdrukpagina nemen de configuratie over. Wanneer u de rollout configuratie aan gebruik vormt, zou u de configuratie kunnen met voeten treden die de pagina van zijn ouder erft.

1. Gebruik de **console van Plaatsen** om de wortelpagina van de blauwdruk te selecteren.
1. Selecteer **Eigenschappen** van de toolbar.
1. Open het **Vervagen** lusje.
1. Selecteer één of meerdere **Configuraties van de Output** gebruikend de drop-down selecteur.
1. Zet uw updates met **sparen** voort.

### De standaardconfiguratie van de systeemuitrol instellen {#setting-the-system-default-rollout-configuration}

Geef een rollout-configuratie op die u als systeemstandaard wilt gebruiken. Om het gebrek te specificeren, vorm de dienst OSGi:

* **Dag CQ WCM de Levende Manager van de Verhouding**
de service-PID is `com.day.cq.wcm.msm.impl.LiveRelationshipManagerImpl`

Vorm de dienst gebruikend of de [ Console van het Web ](/help/sites-deploying/configuring-osgi.md#osgi-configuration-with-the-web-console) of de knoop van de a [ bewaarplaats ](/help/sites-deploying/configuring-osgi.md#osgi-configuration-in-the-repository).

* In de Webconsole, is de naam van het bezit om te vormen Standaardrollout config.
* Met behulp van een opslagplaats-knooppunt is de naam van de eigenschap die moet worden geconfigureerd `liverelationshipmgr.relationsconfig.default` .

Plaats deze bezitswaarde aan de weg van de rollout configuratie aan gebruik als systeemgebrek. De standaardwaarde is `/libs/msm/wcm/rolloutconfigs/default`, die **StandaardConfiguratie van de Uitvoer** is.
