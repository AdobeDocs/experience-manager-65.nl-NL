---
title: Beschrijving van herbruikbare onderdelen
seo-title: Beschrijving van herbruikbare onderdelen
description: Een volledige lijst met herbruikbare componenten met bestandsnamen en afhankelijkheden, waarmee u de AEM Forms-werkruimtecomponent kunt integreren in uw webtoepassingen.
seo-description: Een volledige lijst met herbruikbare componenten met bestandsnamen en afhankelijkheden, waarmee u de AEM Forms-werkruimtecomponent kunt integreren in uw webtoepassingen.
uuid: 8e6accc7-0935-4d7b-b838-d23676df5cda
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: d3facd17-ceb0-4799-8cd9-ff9e81e09793
translation-type: tm+mt
source-git-commit: 56c6cfd437ef185336e81373bd5f758205b96317

---


# Beschrijving van herbruikbare onderdelen {#description-of-reusable-components}

De werkruimte van AEM-formulieren bestaat uit [herbruikbare](/help/forms/using/integrating-html-ws-components-web.md) componenten die zijn geordend in een specifieke [mapstructuur](/help/forms/using/folder-structure.md) in CRX™. Elke component heeft model, mening, en malplaatjedossier op plaats die in de omslagstructuur wordt gespecificeerd, JavaScript™ gebiedsdelen op andere componentendossiers, gebeurtenissen die door de component en voorwerpen worden geluisterd JavaScript die deze gebeurtenissen in de werkruimte van Vormen AEM teweegbrengen. De volledige lijst van herbruikbare componenten met samenstellende bestandsnamen en afhankelijkheden wordt hier gegeven.

## TaskList {#tasklist}

<table>
 <tbody>
  <tr>
   <td><p>Model</p></td>
   <td><p>tasklist.js</p></td>
  </tr>
  <tr>
   <td><p>Weergave</p></td>
   <td><p>tasklist.js</p></td>
  </tr>
  <tr>
   <td><p>Sjabloonmodel</p></td>
   <td><p>tasklist.html</p></td>
  </tr>
  <tr>
   <td><p>Vereist componenten</p></td>
   <td>
    <ul>
     <li><p>UserSearch</p></li>
     <li><p>Taak</p></li>
     <li><p>Teamtask</p></li>
    </ul></td>
  </tr>
  <tr>
   <td><p>JS-afhankelijkheden</p></td>
   <td>
    <ul>
     <li><p>taakmodel</p></li>
     <li><p>teamtask-model</p></li>
    </ul></td>
  </tr>
  <tr>
   <td><p>Gebeurtenissen waarnaar wordt geluisterd (naam gebeurtenis - activering)</p></td>
   <td>
    <ul>
     <li><p>filterGeselecteerd - taaklijstmodel</p></li>
     <li><p>remove - taaklijstmodel</p></li>
     <li><p>updateQueue - taaklijstmodel</p></li>
    </ul></td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Deze component kan onafhankelijk van de werkruimte van Vormen van AEM worden gebruikt, op voorwaarde dat u filterSelected gebeurtenis voor deze component van uw douanetoepassing teweegbrengt.

## Taak {#task}

<table>
 <tbody>
  <tr>
   <td><p>Model</p></td>
   <td><p>task.js</p></td>
  </tr>
  <tr>
   <td><p>Weergave</p></td>
   <td><p>task.js</p></td>
  </tr>
  <tr>
   <td><p>Sjabloonmodel</p></td>
   <td><p>task.html</p></td>
  </tr>
  <tr>
   <td><p>Vereist componenten</p></td>
   <td><p>NA</p></td>
  </tr>
  <tr>
   <td><p>JS-afhankelijkheden</p></td>
   <td>
    <ul>
     <li><p>taaklijstmodel</p></li>
     <li><p>hulpprogramma taskactions</p></li>
    </ul></td>
  </tr>
  <tr>
   <td><p>Gebeurtenissen waarnaar wordt geluisterd (naam gebeurtenis - activering)</p></td>
   <td>
    <ul>
     <li><p>submitComplete - taakmodel</p></li>
     <li><p>Afwijzen - taakmodel</p></li>
    </ul></td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>De werkruimte roept fetchTasks functie van model TaskList om de modellen van de Taak voor deze component tot stand te brengen.

## FilterList {#filterlist}

<table>
 <tbody>
  <tr>
   <td><p>Model</p></td>
   <td><p>tasklist.js</p></td>
  </tr>
  <tr>
   <td><p>Weergave</p></td>
   <td><p>filterlist.js</p></td>
  </tr>
  <tr>
   <td><p>Sjabloonmodel</p></td>
   <td><p>filterlist.html</p></td>
  </tr>
  <tr>
   <td><p>Vereist componenten</p></td>
   <td><p>NA</p></td>
  </tr>
  <tr>
   <td><p>JS-afhankelijkheden</p></td>
   <td><p>NA</p></td>
  </tr>
  <tr>
   <td><p>Gebeurtenissen waarnaar wordt geluisterd (naam gebeurtenis - activering)</p></td>
   <td>
    <ul>
     <li><p>opgehaald - taaklijstmodel </p></li>
     <li><p>remove - taaklijstmodel </p></li>
     <li><p>updateQueue - taaklijstmodel </p></li>
     <li><p>vernieuwde wachtrij - taaklijstmodel </p></li>
     <li><p>filterGeselecteerd - taaklijstmodel</p></li>
    </ul></td>
  </tr>
 </tbody>
</table>

## Filter {#filter}

<table>
 <tbody>
  <tr>
   <td><p>Weergave</p> </td>
   <td><p>filter.js</p> </td>
  </tr>
  <tr>
   <td><p>Sjabloonmodel</p> </td>
   <td><p>filter.html</p> </td>
  </tr>
  <tr>
   <td><p>Vereist componenten</p> </td>
   <td><p>NA</p> </td>
  </tr>
  <tr>
   <td><p>JS-afhankelijkheden</p> </td>
   <td>
    <ul>
     <li><p>Veld: wachtrij: { name, qid, isDefault, type}</p> </li>
     <li><p>Veld: query: string</p> </li>
     <li><p>Veld: parentView: filterlijstweergave</p> </li>
     <li><p>Veld: parentModel: taaklijstmodel</p> </li>
     <li><p>Veld: nut</p> </li>
    </ul> </td>
  </tr>
  <tr>
   <td><p>Gelistende gebeurtenissen</p> </td>
   <td><p>NA</p> </td>
  </tr>
 </tbody>
</table>

## TeamQueues {#teamqueues}

<table>
 <tbody>
  <tr>
   <td><p>Model</p></td>
   <td><p>tasklist.js</p></td>
  </tr>
  <tr>
   <td><p>Weergave</p></td>
   <td><p>teamqueues.js</p></td>
  </tr>
  <tr>
   <td><p>Sjabloonmodel</p></td>
   <td><p>teamqueues.html</p></td>
  </tr>
  <tr>
   <td><p>Vereist componenten</p></td>
   <td><p>NA</p></td>
  </tr>
  <tr>
   <td><p>JS-afhankelijkheden</p></td>
   <td><p>NA</p></td>
  </tr>
  <tr>
   <td><p>Gebeurtenissen waarnaar wordt geluisterd (naam gebeurtenis - activering)</p></td>
   <td>
    <ul>
     <li><p>opgehaald - taaklijstmodel </p></li>
     <li><p>remove - taaklijstmodel </p></li>
     <li><p>updateQueue - taaklijstmodel </p></li>
     <li><p>teamQueuesFetched - taaklijstmodel </p></li>
    </ul></td>
  </tr>
 </tbody>
</table>

## TeamFilter {#teamfilter}

<table>
 <tbody>
  <tr>
   <td><p>Model</p> </td>
   <td><p>NA</p> </td>
  </tr>
  <tr>
   <td><p>Weergave</p> </td>
   <td><p>teamfilter.js</p> </td>
  </tr>
  <tr>
   <td><p>Sjabloonmodel</p> </td>
   <td><p>teamfilter.html</p> </td>
  </tr>
  <tr>
   <td><p>Vereist componenten</p> </td>
   <td><p>NA</p> </td>
  </tr>
  <tr>
   <td><p>JS-afhankelijkheden</p> </td>
   <td>
    <ul>
     <li><p>Breidt uit: filterweergave</p> </li>
     <li><p>Veld: queue :{ name, qid, isDefault, type }</p> </li>
     <li><p>Veld: query: string</p> </li>
     <li><p>Veld: parentView: filterlijstweergave</p> </li>
     <li><p>Veld: parentModel : taaklijstmodel</p> </li>
     <li><p>Veld: nut</p> </li>
    </ul> </td>
  </tr>
  <tr>
   <td><p>Gelistende gebeurtenissen</p> </td>
   <td><p>NA</p> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>TeamFilter krijgt de gebeurtenis erop wijst die welke taak van de component TaskList is geselecteerd. Hoewel deze componenten de modelklasse delen, is er geen andere afhankelijkheid.

## TaskDetails {#taskdetails}

<table>
 <tbody>
  <tr>
   <td><p>Model</p> </td>
   <td><p>tasklist.js</p> </td>
  </tr>
  <tr>
   <td><p>Weergave</p> </td>
   <td><p>taskdetails.js</p> </td>
  </tr>
  <tr>
   <td><p>Sjabloonmodel</p> </td>
   <td><p>taskdetails.html</p> </td>
  </tr>
  <tr>
   <td><p>Vereist componenten</p> </td>
   <td><p>De meeste klassen van het Nut</p> </td>
  </tr>
  <tr>
   <td><p>JS-afhankelijkheden</p> </td>
   <td>
    <ul>
     <li><p>processinstancehistory.html</p> </li>
     <li><p>hulpprogramma voor formrendering</p> </li>
     <li><p>hulpprogramma voor notities</p> </li>
     <li><p>hulpprogramma voor bijlagen</p> </li>
     <li><p>hulpprogramma taskactions</p> </li>
     <li><p>historiehulpprogramma</p> </li>
    </ul> </td>
  </tr>
  <tr>
   <td><p>Gebeurtenissen waarnaar wordt geluisterd (naam gebeurtenis - activering)</p> </td>
   <td>
    <ul>
     <li><p>doorgestuurd - taakmodel</p> </li>
     <li><p>gedeeld - taakmodel</p> </li>
     <li><p>geraadpleegd - taakmodel</p> </li>
     <li><p>afgewezen - taakmodel</p> </li>
     <li><p>verlaten - taakmodel</p> </li>
     <li><p>ontgrendeld - taakmodel</p> </li>
     <li><p>vergrendeld - taakmodel</p> </li>
     <li><p>geclaimd - taakmodel</p> </li>
     <li><p>wijzigen:geselecteerde taak - taaklijstmodel</p> </li>
     <li><p>wijzigen:formUrl - taakmodel</p> </li>
     <li>bijlageURLFetched - taakmodel</li>
    </ul>
    <ul>
     <li>newAttachment - taakmodel</li>
     <li><p>taskHistoryFetched - taakmodel</p> </li>
     <li>prepareForSubmitComplete - taakmodel</li>
     <li><p>submitComplete - taakmodel</p> </li>
    </ul> </td>
  </tr>
 </tbody>
</table>

## CategorieLijst {#categorylist}

<table>
 <tbody>
  <tr>
   <td><p>Model</p></td>
   <td><p>categorylist.js</p></td>
  </tr>
  <tr>
   <td><p>Weergave</p></td>
   <td><p>categorylist.js</p></td>
  </tr>
  <tr>
   <td><p>Sjabloonmodel</p></td>
   <td><p>startprocess.html (in de routeomslag)</p></td>
  </tr>
  <tr>
   <td><p>Vereist componenten</p></td>
   <td><p>Categorie</p></td>
  </tr>
  <tr>
   <td><p>JS-afhankelijkheden</p></td>
   <td>
    <ul>
     <li><p>gunstig architectuurmodel</p></li>
     <li><p>categoriemodel</p></li>
    </ul></td>
  </tr>
  <tr>
   <td><p>Gebeurtenissen waarnaar wordt geluisterd (naam gebeurtenis - activering)</p></td>
   <td>
    <ul>
     <li><p>allStartpointsFetched - categorielijst model </p></li>
     <li><p>add - categorielijstmodel </p></li>
    </ul></td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Deze component gebruikt modelklassen van sommige andere componenten zoals StartPointList, StartPoint, en Taak. Naast dit gebiedsdeel, kan CategorieList onafhankelijk worden gebruikt.

## Categorie {#category}

<table>
 <tbody>
  <tr>
   <td><p>Model</p></td>
   <td><p>category.js</p></td>
  </tr>
  <tr>
   <td><p>Weergave</p></td>
   <td><p>category.js</p></td>
  </tr>
  <tr>
   <td><p>Sjabloonmodel</p></td>
   <td><p>category.html</p></td>
  </tr>
  <tr>
   <td><p>Vereist componenten</p></td>
   <td><p>NA</p></td>
  </tr>
  <tr>
   <td><p>JS-afhankelijkheden</p></td>
   <td>
    <ul>
     <li><p>categorielijstmodel</p></li>
     <li><p>startpointlist-model</p></li>
    </ul></td>
  </tr>
  <tr>
   <td><p>Gebeurtenissen waarnaar wordt geluisterd (naam gebeurtenis - activering)</p></td>
   <td>
    <ul>
     <li><p>gewijzigd - categoriemodel </p></li>
     <li><p>childFetched - categoriemodel </p></li>
     <li><p>categorie:geselecteerd - categorielijstmodel </p></li>
    </ul></td>
  </tr>
 </tbody>
</table>

## StartPointList {#startpointlist}

<table>
 <tbody>
  <tr>
   <td><p>Model</p></td>
   <td><p>categorylist.js</p></td>
  </tr>
  <tr>
   <td><p>Weergave</p></td>
   <td><p>startpointlist.js</p></td>
  </tr>
  <tr>
   <td><p>Sjabloonmodel</p></td>
   <td><p>startprocess.html (in de routeomslag)</p></td>
  </tr>
  <tr>
   <td><p>Vereist componenten</p></td>
   <td><p>NA</p></td>
  </tr>
  <tr>
   <td><p>JS-afhankelijkheden</p></td>
   <td>
    <ul>
     <li><p>categoriemodel</p></li>
     <li><p>gunstig architectuurmodel</p></li>
     <li><p>categoriemodel</p></li>
     <li><p>startpuntweergave</p></li>
     <li><p>startpointlist-model</p></li>
     <li><p>startpuntmodel</p></li>
     <li><p>taakmodel</p></li>
     <li><p>taakmodel</p></li>
     <li><p>taaklijstmodel</p></li>
     <li><p>teamtask-model</p></li>
    </ul></td>
  </tr>
  <tr>
   <td><p>Gebeurtenissen waarnaar wordt geluisterd (naam gebeurtenis - activering)</p></td>
   <td>
    <ul>
     <li><p>categorie:geselecteerd - categorielijstmodel </p></li>
     <li><p>allStartpointsFetched - categorielijst model </p></li>
    </ul></td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>De componenten StartPointList en CategorieList delen de modelklasse, vandaar eerste hangt van laatstgenoemde af. CategorieList heeft toegang tot de informatie over welke beginpunten van de categorie worden getoond. Om StartPointList onafhankelijk te gebruiken, simuleer de gebeurtenistrekker van CategorieList.

## StartPoint {#startpoint}

<table>
 <tbody>
  <tr>
   <td><p>Model</p></td>
   <td><p>startpoint.js</p></td>
  </tr>
  <tr>
   <td><p>Weergave</p></td>
   <td><p>startpoint.js</p></td>
  </tr>
  <tr>
   <td><p>Sjabloonmodel</p></td>
   <td><p>startpoint.html</p></td>
  </tr>
  <tr>
   <td><p>Vereist componenten</p></td>
   <td><p>NA</p></td>
  </tr>
  <tr>
   <td><p>JS-afhankelijkheden</p></td>
   <td><p>taakmodel</p></td>
  </tr>
  <tr>
   <td><p>Gebeurtenissen waarnaar wordt geluisterd (naam gebeurtenis - activering)</p></td>
   <td><p>wijziging - startpuntmodel </p></td>
  </tr>
 </tbody>
</table>

## StartProcess {#startprocess}

<table>
 <tbody>
  <tr>
   <td><p>Model</p> </td>
   <td><p>categorylist.js</p> </td>
  </tr>
  <tr>
   <td><p>Weergave</p> </td>
   <td><p>startprocess.js</p> </td>
  </tr>
  <tr>
   <td><p>Sjabloonmodel</p> </td>
   <td><p>startprocess.html</p> </td>
  </tr>
  <tr>
   <td><p>Vereist componenten</p> </td>
   <td>
    <ul>
     <li><p>De meeste klassen van het Nut</p> </li>
     <li><p>UserSearch</p> </li>
    </ul> </td>
  </tr>
  <tr>
   <td><p>JS-afhankelijkheden</p> </td>
   <td>
    <ul>
     <li><p>categoriemodel</p> </li>
     <li><p>gunstig architectuurmodel</p> </li>
     <li><p>categoriemodel</p> </li>
     <li><p>hulpprogramma voor formrendering</p> </li>
     <li><p>hulpprogramma voor notities</p> </li>
     <li><p>hulpprogramma voor bijlagen</p> </li>
     <li><p>hulpprogramma taskactions</p> </li>
    </ul> </td>
  </tr>
  <tr>
   <td><p>Gebeurtenissen waarnaar wordt geluisterd (naam gebeurtenis - activering)</p> </td>
   <td>
    <ul>
     <li><p>categorie:geselecteerd - categorielijstmodel</p> </li>
     <li><p>change:calledTask - startpointlist, model</p> </li>
     <li><p>wijzigen:formUrl - taakmodel</p> </li>
     <li><p>startpunt:geselecteerd - startpointlist, model</p> </li>
     <li><p>doorgestuurd - taakmodel</p> </li>
     <li><p>verlaten - taakmodel</p> </li>
     <li><p>ontgrendeld - taakmodel</p> </li>
     <li><p>vergrendeld - taakmodel</p> </li>
     <li>bijlageURLFetched - taakmodel</li>
     <li>newAttachment - taakmodel</li>
     <li>prepareForSubmitComplete - taakmodel </li>
     <li><p>submitComplete - taakmodel</p> </li>
     <li><p>allStartpointsFetched - categorielijst model</p> </li>
    </ul> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>De componenten StartProcess en StartPointList delen de modelklasse. Deze component wordt relevant u een startpunt van StartPointList selecteert.

## ProcessNameList {#processnamelist}

<table>
 <tbody>
  <tr>
   <td><p>Model</p></td>
   <td><p>processnamelist.js</p></td>
  </tr>
  <tr>
   <td><p>Weergave</p></td>
   <td><p>processnamelist.js</p></td>
  </tr>
  <tr>
   <td><p>Sjabloonmodel</p></td>
   <td><p>tracking.html (in de routemap)</p></td>
  </tr>
  <tr>
   <td><p>Vereist componenten</p></td>
   <td><p>NA</p></td>
  </tr>
  <tr>
   <td><p>JS-afhankelijkheden</p></td>
   <td><p>procesnaammodel</p></td>
  </tr>
  <tr>
   <td><p>Gebeurtenissen waarnaar wordt geluisterd (naam gebeurtenis - activering)</p></td>
   <td>
    <ul>
     <li><p>add - procesnamelist-model </p></li>
     <li><p>opgehaald:procesnamen - procesnamelist, model </p></li>
     <li><p>change - model van procesnamelist </p></li>
    </ul></td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>ProcessNameList is niet afhankelijk van andere componenten. Intern hangt het echter af van de modelklasse ProcessInstanceList die op zijn beurt weer afhankelijk is van andere componenten. Daarom gebruikt ProcessNameList vele modelklassen zoals ProcessInstanceList, ProcessInstance, TaskList, Teamtask, en Taak. Naast deze gebiedsdelen, kan ProcessNameList onafhankelijk worden gebruikt.

## ProcessName {#processname}

<table>
 <tbody>
  <tr>
   <td><p>Model</p></td>
   <td><p>processname.js</p></td>
  </tr>
  <tr>
   <td><p>Weergave</p></td>
   <td><p>procesnaam (in processnamelist.js)</p></td>
  </tr>
  <tr>
   <td><p>Sjabloonmodel</p></td>
   <td><p>processname.html</p></td>
  </tr>
  <tr>
   <td><p>Vereist componenten</p></td>
   <td><p>NA</p></td>
  </tr>
  <tr>
   <td><p>JS-afhankelijkheden</p></td>
   <td><p>procesinstancelist-model</p></td>
  </tr>
  <tr>
   <td><p>Gebeurtenissen waarnaar wordt geluisterd (naam gebeurtenis - activering)</p></td>
   <td><p>change - model van verwerkingsnaam </p></td>
  </tr>
 </tbody>
</table>

## ProcessInstanceList {#processinstancelist}

<table>
 <tbody>
  <tr>
   <td><p>Model</p></td>
   <td><p>processnamelist.js</p></td>
  </tr>
  <tr>
   <td><p>Weergave</p></td>
   <td><p>processinstancelist.js</p></td>
  </tr>
  <tr>
   <td><p>Sjabloonmodel</p></td>
   <td><p>tracking.html (in de routemap)</p></td>
  </tr>
  <tr>
   <td><p>Vereist componenten</p></td>
   <td><p>NA</p></td>
  </tr>
  <tr>
   <td><p>JS-afhankelijkheden</p></td>
   <td><p>procesnaammodel</p></td>
  </tr>
  <tr>
   <td><p>Gebeurtenissen waarnaar wordt geluisterd (naam gebeurtenis - activering)</p></td>
   <td>
    <ul>
     <li><p>procesnaam:geselecteerd - model verwerkingsnamelist </p></li>
     <li><p>procesnaam:instancesfetch, procesnamelist, model </p></li>
    </ul></td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>ProcessInstanceList verwacht een gebeurtenis van ProcessNameList die de procesnaam voor het halen en tonen van instanties wijst. Als u ProcessInstanceList onafhankelijk wilt gebruiken, moet u de gebeurtenistrigger afzonderlijk simuleren.

## ProcessInstance {#processinstance}

<table>
 <tbody>
  <tr>
   <td><p>Model</p></td>
   <td><p>processinstance.js</p></td>
  </tr>
  <tr>
   <td><p>Weergave</p></td>
   <td><p>procesnaam in procesnamelist.js</p></td>
  </tr>
  <tr>
   <td><p>Sjabloonmodel</p></td>
   <td><p>processinstance.html</p></td>
  </tr>
  <tr>
   <td><p>Vereist componenten</p></td>
   <td><p>NA</p></td>
  </tr>
  <tr>
   <td><p>JS-afhankelijkheden</p></td>
   <td><p>taaklijstmodel</p></td>
  </tr>
  <tr>
   <td><p>Gebeurtenissen waarnaar wordt geluisterd (naam gebeurtenis - activering)</p></td>
   <td><p>change - procesinstantiemodel </p></td>
  </tr>
 </tbody>
</table>

## ProcessInstanceHistory {#processinstancehistory}

<table>
 <tbody>
  <tr>
   <td><p>Model</p></td>
   <td><p>processnamelist.js</p></td>
  </tr>
  <tr>
   <td><p>Weergave</p></td>
   <td><p>processinstancehistory.js</p></td>
  </tr>
  <tr>
   <td><p>Sjabloonmodel</p></td>
   <td><p>processinstancehistory.html</p></td>
  </tr>
  <tr>
   <td><p>Vereist componenten</p></td>
   <td><p>NA</p></td>
  </tr>
  <tr>
   <td><p>JS-afhankelijkheden</p></td>
   <td>
    <ul>
     <li><p>procesnaammodel</p></li>
     <li><p>historiehulpprogramma</p></li>
    </ul></td>
  </tr>
  <tr>
   <td><p>Gebeurtenissen waarnaar wordt geluisterd (naam gebeurtenis - activering)</p></td>
   <td>
    <ul>
     <li><p>procesnaam:geselecteerd - model verwerkingsnamelist </p></li>
     <li><p>procesinstantie:geselecteerd - model procesinstancelist </p></li>
     <li><p>tasksFetched - procesinstantiemodel </p></li>
    </ul></td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>ProcessInstanceHistory verwacht een gebeurtenis van ProcessInstanceList die erop wijst welke geschiedenis van de procesinstantie moet worden getoond. Naast deze afhankelijkheid kan de component onafhankelijk worden gebruikt.

## OutofOffice {#outofoffice}

<table>
 <tbody>
  <tr>
   <td><p>Model</p> </td>
   <td><p>outofoffice.js</p> </td>
  </tr>
  <tr>
   <td><p>Weergave</p> </td>
   <td><p>outofoffice.js</p> </td>
  </tr>
  <tr>
   <td><p>Sjabloonmodel</p> </td>
   <td><p>outofoffice.html</p> </td>
  </tr>
  <tr>
   <td><p>Vereist componenten</p> </td>
   <td><p>UserSearch</p> </td>
  </tr>
  <tr>
   <td><p>JS-afhankelijkheden</p> </td>
   <td><p>gebruikerszoekweergave</p> </td>
  </tr>
  <tr>
   <td><p>Gebeurtenissen waarnaar wordt geluisterd (naam gebeurtenis - activering)</p> </td>
   <td>
    <ul>
     <li><p>outOfOfficeSettingsFetched - outoffice-model</p> </li>
     <li><p>outOfOfficeSettingsSaved - outoffice-model</p> </li>
     <li><p>processenFetched - outtofoffice model</p> </li>
     <li><p>principalSelected - principiële zoekweergave</p> </li>
    </ul> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>OutofOffice kan onafhankelijk worden gebruikt.

## ShareQueue {#sharequeue}

<table>
 <tbody>
  <tr>
   <td><p>Model</p> </td>
   <td><p>sharequeue.js</p> </td>
  </tr>
  <tr>
   <td><p>Weergave</p> </td>
   <td><p>sharequeue.js</p> </td>
  </tr>
  <tr>
   <td><p>Sjabloonmodel</p> </td>
   <td><p>sharequeue.html</p> </td>
  </tr>
  <tr>
   <td><p>Vereist componenten</p> </td>
   <td><p>UserSearch</p> </td>
  </tr>
  <tr>
   <td><p>JS-afhankelijkheden</p> </td>
   <td><p>gebruikerszoekweergave</p> </td>
  </tr>
  <tr>
   <td><p>Gebeurtenissen waarnaar wordt geluisterd (naam gebeurtenis - activering)</p> </td>
   <td>
    <ul>
     <li><p>queueAccessGranted - sharequeue-model</p> </li>
     <li><p>queueAccessRequested - sharequeue-model</p> </li>
     <li><p>allowedUsersFetched - sharequeue-model</p> </li>
     <li>accessibleUsersFetched - sharequeue-model</li>
     <li><p>queueAccessRevoked - sharequeue-model</p> </li>
     <li><p>queueAccessRemoved - sharequeue-model</p> </li>
     <li><p>principalSelected - principiële zoekweergave</p> </li>
    </ul> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>ShareQueue kan onafhankelijk worden gebruikt.

## UISettings {#uisettings}

<table>
 <tbody>
  <tr>
   <td><p>Model</p></td>
   <td><p>uisettings.js</p></td>
  </tr>
  <tr>
   <td><p>Weergave</p></td>
   <td><p>uisettings.js</p></td>
  </tr>
  <tr>
   <td><p>Sjabloonmodel</p></td>
   <td><p>uisettings.html</p></td>
  </tr>
  <tr>
   <td><p>Vereist componenten</p></td>
   <td><p>NA</p></td>
  </tr>
  <tr>
   <td><p>JS-afhankelijkheden</p></td>
   <td><p>NA</p></td>
  </tr>
  <tr>
   <td><p>Gebeurtenissen waarnaar wordt geluisterd (naam gebeurtenis - activering)</p></td>
   <td>
    <ul>
     <li><p>preferencesFetched - instellingenmodel </p></li>
     <li><p>settingUpdated - uisettings model </p></li>
    </ul></td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>UISettings kan onafhankelijk worden gebruikt.

## AppNavigation {#appnavigation}

<table>
 <tbody>
  <tr>
   <td><p>Model</p></td>
   <td><p>appnavigation.js</p></td>
  </tr>
  <tr>
   <td><p>Weergave</p></td>
   <td><p>appnavigation.js</p></td>
  </tr>
  <tr>
   <td><p>Sjabloonmodel</p></td>
   <td><p>appnavigation.html</p></td>
  </tr>
  <tr>
   <td><p>Vereist componenten</p></td>
   <td><p>NA</p></td>
  </tr>
  <tr>
   <td><p>JS-afhankelijkheden</p></td>
   <td><p>NA</p></td>
  </tr>
  <tr>
   <td><p>Gelistende gebeurtenissen</p></td>
   <td><p>NA</p></td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>AppNavigation kan onafhankelijk worden gebruikt.

## UserInfo {#userinfo}

<table>
 <tbody>
  <tr>
   <td><p>Model</p> </td>
   <td><p>userinfo.js</p> </td>
  </tr>
  <tr>
   <td><p>Weergave</p> </td>
   <td><p>userinfo.js</p> </td>
  </tr>
  <tr>
   <td><p>Sjabloonmodel</p> </td>
   <td><p>userinfo.html</p> </td>
  </tr>
  <tr>
   <td><p>Vereist componenten</p> </td>
   <td><p>NA</p> </td>
  </tr>
  <tr>
   <td><p>JS-afhankelijkheden</p> </td>
   <td><p>NA</p> </td>
  </tr>
  <tr>
   <td><p>Gebeurtenissen waarnaar wordt geluisterd (naam gebeurtenis - activering)</p> </td>
   <td>
    <ul>
     <li>userImageUrlFetched - userinfo model</li>
     <li>sessionRenewed - gebruikersinformatiemodel <br /> </li>
     <li>sessionExpired - gebruikersinformatiemodel </li>
    </ul> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>UserInfo kan onafhankelijk worden gebruikt.

## WSError {#wserror}

<table>
 <tbody>
  <tr>
   <td><p>Model</p></td>
   <td><p>wserror.js</p></td>
  </tr>
  <tr>
   <td><p>Weergave</p></td>
   <td><p>wserror.js</p></td>
  </tr>
  <tr>
   <td><p>Sjabloonmodel</p></td>
   <td><p>wserror.html</p></td>
  </tr>
  <tr>
   <td><p>Vereist componenten</p></td>
   <td><p>NA</p></td>
  </tr>
  <tr>
   <td><p>JS-afhankelijkheden</p></td>
   <td><p>NA</p></td>
  </tr>
  <tr>
   <td><p>Gebeurtenissen waarnaar wordt geluisterd (naam gebeurtenis - activering)</p></td>
   <td><p>newWsError - wserror-model </p></td>
  </tr>
 </tbody>
</table>

## UserSearch {#usersearch}

<table>
 <tbody>
  <tr>
   <td><p>Model</p> </td>
   <td><p>usersearch.js</p> </td>
  </tr>
  <tr>
   <td><p>Weergave</p> </td>
   <td><p>usersearch.js</p> </td>
  </tr>
  <tr>
   <td><p>Sjabloonmodel</p> </td>
   <td><p>usersearch.html</p> </td>
  </tr>
  <tr>
   <td><p>Vereist componenten</p> </td>
   <td><p>NA</p> </td>
  </tr>
  <tr>
   <td><p>JS-afhankelijkheden</p> </td>
   <td><p>NA</p> </td>
  </tr>
  <tr>
   <td><p>Gebeurtenissen waarnaar wordt geluisterd (naam gebeurtenis - activering)</p> </td>
   <td>
    <ul>
     <li>principalSearched - hoofdzoekmodel</li>
     <li>outOfOfficeInfoFetched - gebruikerszoekmodel</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

## SearchTemplate {#searchtemplate}

<table>
 <tbody>
  <tr>
   <td><p>Model</p> </td>
   <td><p>searchtemplate.js</p> </td>
  </tr>
  <tr>
   <td><p>Weergave</p> </td>
   <td><p>searchtemplate (in searchtemplatelist.js) </p> </td>
  </tr>
  <tr>
   <td><p>Sjabloonmodel</p> </td>
   <td><p>searchtemplate.html</p> </td>
  </tr>
  <tr>
   <td><p>Vereist componenten</p> </td>
   <td><p>NA</p> </td>
  </tr>
  <tr>
   <td><p>JS-afhankelijkheden</p> </td>
   <td><p>NA</p> </td>
  </tr>
  <tr>
   <td><p>Gebeurtenissen waarnaar wordt geluisterd (naam gebeurtenis - activering)</p> </td>
   <td><p>templateFetched-zoekplaatmodel</p> </td>
  </tr>
 </tbody>
</table>

## SearchTemplateList {#searchtemplatelist}

<table>
 <tbody>
  <tr>
   <td><p>Model</p> </td>
   <td><p>searchtemplatelist.js</p> </td>
  </tr>
  <tr>
   <td><p>Weergave</p> </td>
   <td><p>searchtemplatelist.js</p> </td>
  </tr>
  <tr>
   <td><p>Sjabloonmodel</p> </td>
   <td><p>tracking.html (in de routemap)</p> </td>
  </tr>
  <tr>
   <td><p>Vereist componenten</p> </td>
   <td><p>NA</p> </td>
  </tr>
  <tr>
   <td><p>JS-afhankelijkheden</p> </td>
   <td><p>searchtemplate-model</p> </td>
  </tr>
  <tr>
   <td><p>Gebeurtenissen waarnaar wordt geluisterd (naam gebeurtenis - activering)</p> </td>
   <td><p>change - model voor searchtemplatelist</p> </td>
  </tr>
 </tbody>
</table>

## SearchTemplateDetails {#searchtemplatedetails}

<table>
 <tbody>
  <tr>
   <td><p>Model</p> </td>
   <td><p>searchtemplatelist.js</p> </td>
  </tr>
  <tr>
   <td><p>Weergave</p> </td>
   <td><p>searchtemplatedetails.js</p> </td>
  </tr>
  <tr>
   <td><p>Sjabloonmodel</p> </td>
   <td><p>searchtemplatedetails.html</p> </td>
  </tr>
  <tr>
   <td><p>Vereist componenten</p> </td>
   <td><p>NA</p> </td>
  </tr>
  <tr>
   <td><p>JS-afhankelijkheden</p> </td>
   <td>NA<br /> </td>
  </tr>
  <tr>
   <td><p>Gebeurtenissen waarnaar wordt geluisterd (naam gebeurtenis - activering)</p> </td>
   <td><p>searchTemplate:selected - zoekplaatmodel</p> </td>
  </tr>
 </tbody>
</table>
