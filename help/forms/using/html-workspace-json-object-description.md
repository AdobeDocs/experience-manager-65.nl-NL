---
title: JSON-objectbeschrijving in de AEM Forms-werkruimte
description: Conceptuele informatie over de JSON JavaScript-objecten die in de werkruimte van LiveCycle AEM Forms worden gebruikt voor aanpassing, uitbreiding, wijziging en hergebruik.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
exl-id: f837a2b3-4650-4261-84c6-291bb2a46dc7
solution: Experience Manager, Experience Manager Forms
feature: HTML5 Forms,Adaptive Forms,Mobile Forms
role: Admin, User, Developer
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '2144'
ht-degree: 0%

---

# JSON-objectbeschrijving in de AEM Forms-werkruimte {#aem-forms-workspace-json-object-description}

JSON-objecten die in de AEM Forms-werkruimte worden gebruikt, worden hieronder beschreven.

1. Categorie

   Categorieën bevinden zich op het tabblad Start van de werkruimte. Deze categorieën worden gebruikt om de startpunten te classificeren.

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschap</strong></td>
   <td><strong>Alleen client</strong></td>
   <td><strong>Opmerkingen</strong></td>
  </tr>
  <tr>
   <td>name</td>
   <td>F</td>
   <td>Categorienaam</td>
  </tr>
  <tr>
   <td>id</td>
   <td>F</td>
   <td>Categorie-id <br type="_moz" /> </td>
  </tr>
  <tr>
   <td>description<br type="_moz" /> </td>
   <td>F</td>
   <td>Categoriebeschrijving <br type="_moz" /> </td>
  </tr>
  <tr>
   <td>parentOid <br type="_moz" /> </td>
   <td>F</td>
   <td>Bevat id van oudercategorie <br type="_moz" /> </td>
  </tr>
  <tr>
   <td>startPointsList <br type="_moz" /> </td>
   <td>T</td>
   <td>Bevat een lijst met alle startpunten die in een categorie aanwezig zijn</td>
  </tr>
  <tr>
   <td>categoryList</td>
   <td>T</td>
   <td>Bevat lijst van directe kindcategorieën van een categorie <br type="_moz" /> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Alle beginpunten en Favorieten zijn categorieën die aan clientzijde zijn gedefinieerd. De categorie Favorieten bevat alle startpunten die door de gebruiker als favoriet zijn gemarkeerd. Alle beginpunten-categorieën bevatten alle beginpunten.

1. Startpoint

   Het beginpunt wordt gebruikt om een proces van de werkruimte te beginnen wanneer aangeroepen.

   | **Bezit** | **slechts Cliënt** | **Commentaren** |
   |---|---|---|
   | categoryId | F | Het bevat id van de categorie waartoe het startpunt behoort. |
   | beschrijving | F | Het bevat een beschrijving voor een startpunt. |
   | name | F | Deze bevat de naam van het startpunt. |
   | serializedImageTicket | F | Het bevat een afbeeldingsticket dat overeenkomt met het startpunt. Dit beeldkaartje wordt gebruikt in imageUrl gebied van startpoint, om beeld voor startpunt van de server te krijgen. |
   | serviceName | F | Het bevat naam van de dienst voor startpunt. |
   | startpointId | F | Het bevat id van startpunt. |
   | isFavorite | T | Geeft aan of het startpunt favoriet is of niet. True if startpoint is preferred else false. |
   | isDefaultImage | T | Geeft aan of er een afbeelding is opgegeven voor proces of niet. True if there is no image associated with process else false. |
   | taak | T | Deze bevat een taak die wordt gemaakt wanneer het startpunt wordt aangeroepen. |
   | imageUrl | T | Deze bevat URL van de afbeelding die overeenkomt met het startpunt. |

1. Taak

   Taken worden toegewezen aan gebruikers/groepen en bevatten een gebruikersinterface (een formulier of een hulplijn (afgekeurd)) die kan worden gevuld met gegevens. Wanneer gebruikers een taak krijgen toegewezen, ontvangen zij het formulier of de gids om in te vullen en te verzenden.

<table>
 <tbody>
  <tr>
   <td>Eigenschap <br /> </td>
   <td>Alleen client <br /> </td>
   <td>Opmerkingen <br /> </td>
  </tr>
  <tr>
   <td>classOfTask</td>
   <td>F</td>
   <td>De klasse van taak is "LC8"wanneer de taak lc8 taak anders "Standaard"is.<br /> </td>
  </tr>
  <tr>
   <td>completeTime <br /> </td>
   <td>F</td>
   <td>Het bevat de tijdstempel wanneer de taak wordt voltooid.<br /> </td>
  </tr>
  <tr>
   <td>consultGroupId <br /> </td>
   <td>F</td>
   <td>Het bevat id van een groep waarvoor de taak kan worden geraadpleegd. Het wordt geplaatst tijdens het proces het ontwerpen.<br /> </td>
  </tr>
  <tr>
   <td>createTime <br /> </td>
   <td>F</td>
   <td>Het bevat de tijdstempel wanneer de taak wordt gecreeerd.<br /> </td>
  </tr>
  <tr>
   <td>creationId<br /> </td>
   <td>F</td>
   <td>Het bevat identiteitskaart van de gebruiker die de taak creeerde.<br /> </td>
  </tr>
  <tr>
   <td>currentAssignment<br /> </td>
   <td>F</td>
   <td>Het bevat details over huidige taak.<br /> </td>
  </tr>
  <tr>
   <td>deadline <br /> </td>
   <td>F</td>
   <td>Het bevat de tijdzegel dat wanneer een taak zijn deadline zal bereiken.<br /> </td>
  </tr>
  <tr>
   <td>description<br /> </td>
   <td>F</td>
   <td>Het bevat beschrijving van de taak.<br /> </td>
  </tr>
  <tr>
   <td>displayName <br /> </td>
   <td>F</td>
   <td>Het bevat vertoningsnaam van de taak.<br /> </td>
  </tr>
  <tr>
   <td>forwardGroupId<br /> </td>
   <td>F</td>
   <td>Het bevat identiteitskaart van een groep waaraan de taak kan worden door:sturen. Het wordt geplaatst tijdens het proces het ontwerpen.<br /> </td>
  </tr>
  <tr>
   <td>instructies <br /> </td>
   <td>F</td>
   <td>Het bevat instructies voor een taak.<br /> </td>
  </tr>
  <tr>
   <td>isLocked<br /> </td>
   <td>F</td>
   <td>True if task is locked.<br /> </td>
  </tr>
  <tr>
   <td>isMustOpenToComplete<br /> </td>
   <td>F</td>
   <td>True if task form must be opened to complete the task.<br /> </td>
  </tr>
  <tr>
   <td>isOpenFullScreen <br /> </td>
   <td>F</td>
   <td>Indien waar (true), neemt het formulier bij het openen van de taak de eerste keer een volledig scherm in.<br /> </td>
  </tr>
  <tr>
   <td>isRouteSelectionRequired <br /> </td>
   <td>F</td>
   <td>Indien waar, moet de route worden geselecteerd om de taak te voltooien.<br /> </td>
  </tr>
  <tr>
   <td>isShowAttachments <br /> </td>
   <td>F</td>
   <td>Bijlagen worden getoond als het waar is.<br /> </td>
  </tr>
  <tr>
   <td>isStartTask <br /> </td>
   <td>F</td>
   <td>Indien waar, wordt de taak gecreeerd van beginpunt.<br /> </td>
  </tr>
  <tr>
   <td>isVisible<br /> </td>
   <td>F</td>
   <td>True if task is visible in workspace.<br /> </td>
  </tr>
  <tr>
   <td>nextReminder<br /> </td>
   <td>F</td>
   <td>Tijdstempel voor de volgende herinnering.<br /> </td>
  </tr>
  <tr>
   <td>priority <br /> </td>
   <td>F</td>
   <td>Het bevat een prioriteit.<br /> 1 = Hoogste prioriteit <br /> 2 = Hoge Prioriteit <br /> 3 = Normale Prioriteit <br /> 4 = Lage Prioriteit <br /> 5 = Laagste Prioriteit <br /> </td>
  </tr>
  <tr>
   <td>processInstanceId</td>
   <td>F</td>
   <td>Identiteitskaart van de procesinstantie waarvan taak deel uitmaakt.<br /> </td>
  </tr>
  <tr>
   <td>processInstanceStatus <br /> </td>
   <td>F</td>
   <td>Status van de procesinstantie van de taak.<br /> </td>
  </tr>
  <tr>
   <td>reminderCount<br /> </td>
   <td>F</td>
   <td>Het bevat telling van herinneringen voor de taak.<br /> </td>
  </tr>
  <tr>
   <td>routeList <br /> </td>
   <td>F</td>
   <td>Het bevat lijst van routes verbonden aan taak. De gebruiker kan de taak voltooien door om het even welke route van routenelijst te selecteren.<br /> </td>
  </tr>
  <tr>
   <td>selectedRoute <br /> </td>
   <td>F</td>
   <td>Het bevat naam van de geselecteerde route toen de taak werd voltooid.<br /> </td>
  </tr>
  <tr>
   <td>serializedImageTicket <br /> </td>
   <td>F</td>
   <td>Het bevat een afbeeldingsticket dat overeenkomt met een taak. Dit afbeeldingskaartje wordt gebruikt in het taakveld imageUrl om een afbeelding voor taak op te halen van de server. <br /> <br /> </td>
  </tr>
  <tr>
   <td>serviceName<br /> </td>
   <td>F</td>
   <td>Het bevat naam van de dienst voor taak.<br /> </td>
  </tr>
  <tr>
   <td>serviceTitle<br /> </td>
   <td>F</td>
   <td>Het bevat titel van de dienst voor taak.<br /> </td>
  </tr>
  <tr>
   <td>status <br /> </td>
   <td>F</td>
   <td>1 = Gemaakt (Taak wordt gemaakt vanaf beginpunt.)<br /> 2 = Gemaakt en Opgeslagen (Taak wordt gemaakt vanaf het beginpunt en opgeslagen.)<br /> 3 = Toegewezen (Taak wordt toegewezen aan de gebruiker nadat het proces is begonnen.)<br /> 4 = Toegewezen en Opgeslagen (Taak wordt toegewezen en opgeslagen.)<br /> 100 = Voltooid (Taak is voltooid.)<br /> 101 = Gedetailleerd (Taak heeft de deadline bereikt.)<br /> 102 = beëindigd <br /> </td>
  </tr>
  <tr>
   <td>stepName <br /> </td>
   <td>F</td>
   <td>Het bevat naam van de taakreeks tijdens proces het ontwerpen.<br /> </td>
  </tr>
  <tr>
   <td>summaryUrl <br /> </td>
   <td>F</td>
   <td>Het bevat taak summiere url.<br /> </td>
  </tr>
  <tr>
   <td>taskACL <br /> </td>
   <td>F</td>
   <td>Het is toegangsbeheerlijst voor een taak.<br /> </td>
  </tr>
  <tr>
   <td>taskId<br /> </td>
   <td>F</td>
   <td>Id van een taak.<br /> </td>
  </tr>
  <tr>
   <td>updateTime <br /> </td>
   <td>F</td>
   <td>Tijdstempel wanneer taak voor het laatst is bijgewerkt.<br /> </td>
  </tr>
  <tr>
   <td>formUrl <br /> </td>
   <td>T</td>
   <td>Het bevat url van vorm voor een taak.<br /> </td>
  </tr>
  <tr>
   <td>taskFormType <br /> </td>
   <td>T</td>
   <td>Het bevat het type taakformulier. Gebruikend dit gebied, wordt de taak teruggegeven op cliënt als pdf voor, swf vorm, etc.<br /> </td>
  </tr>
  <tr>
   <td>showDirectActions <br /> </td>
   <td>T</td>
   <td>Indien waar, zijn de routeacties zichtbaar in werkruimte.<br /> </td>
  </tr>
  <tr>
   <td>showACLActions <br /> </td>
   <td>T</td>
   <td>Indien waar, zijn de acties zoals voorwaarts, raadpleeg, aandeel zichtbaar in werkruimte.<br /> </td>
  </tr>
  <tr>
   <td>supportsOffline <br /> </td>
   <td>T</td>
   <td>Indien waar (true), kan het formulier offline worden genomen. Dit is alleen voor PDF-formulieren.<br /> </td>
  </tr>
  <tr>
   <td>supportsSave <br /> </td>
   <td>T</td>
   <td>Indien waar (true), kan de gebruiker de taak opslaan.<br /> </td>
  </tr>
  <tr>
   <td>readerSubmitOptions <br /> </td>
   <td>T</td>
   <td>Dit object bevat opties waarmee u PDF-formulieren via het leesprogramma kunt verzenden als het PDF-formulier geen verzendknop bevat. <br /> </td>
  </tr>
  <tr>
   <td>isDefaultImage <br /> </td>
   <td>T</td>
   <td>Geeft aan of er een afbeelding is opgegeven voor proces of niet. True if there is no image associated with process else false.<br /> </td>
  </tr>
  <tr>
   <td>historyTaskList <br /> </td>
   <td>T</td>
   <td>Het bevat een lijst van taken die in geschiedenislusje van taakdetails worden gebruikt.<br /> </td>
  </tr>
  <tr>
   <td>isOwner <br /> </td>
   <td>T</td>
   <td>Waar als het programma geopende gebruiker eigenaar van taak is.<br /> </td>
  </tr>
  <tr>
   <td>availableCommands <br /> </td>
   <td>T</td>
   <td>Het bevat alle acties die op taak kunnen worden genomen.<br /> </td>
  </tr>
  <tr>
   <td>availableCommands.directCommands<br /> </td>
   <td>T</td>
   <td>Het bevat alle routeacties die voor een taak beschikbaar zijn.<br /> </td>
  </tr>
  <tr>
   <td>availableCommands.taskACLCommands<br /> </td>
   <td>T</td>
   <td>Het bevat bevelen als voorwaarts, deel en raadpleeg als beschikbaar voor een taak.<br /> </td>
  </tr>
  <tr>
   <td>availableCommands.otherCommands<br /> </td>
   <td>T</td>
   <td>Het bevat bevelen zoals slot, ontgrendelen, verlaten, terugkeer, eis, etc., zoals beschikbaar.<br /> </td>
  </tr>
  <tr>
   <td>processInstanceInfo <br /> </td>
   <td>T</td>
   <td>Het bevat informatie over de procesinstantie van de taak.<br /> </td>
  </tr>
  <tr>
   <td>processVariables <br /> </td>
   <td>T<br /> </td>
   <td>Het bevat serie van voorwerpen van procesvariabelen als heden.<br /> </td>
  </tr>
  <tr>
   <td>pendingTasks <br /> </td>
   <td>T</td>
   <td>Het bevat een lijst van hangende taken voor de het procesinstantie van de taak.<br /> </td>
  </tr>
  <tr>
   <td>userActions <br /> </td>
   <td>T</td>
   <td>Het is een array van objecten. Elk voorwerp bevat details over route en zijn overeenkomstige bevestigingsbericht indien aanwezig.<br /> </td>
  </tr>
  <tr>
   <td>dataUrl <br /> </td>
   <td>T</td>
   <td>Het is url voor de gegevens van de vorm van een taak.<br /> </td>
  </tr>
  <tr>
   <td>externalAppConfig <br /> </td>
   <td>T</td>
   <td>Dit is configuratie voor derdetoepassingsvormen.<br /> </td>
  </tr>
  <tr>
   <td>submit<br /> </td>
   <td>T</td>
   <td>Waar als de taak wordt voorgelegd.<br /> </td>
  </tr>
  <tr>
   <td>bijlagen <br /> </td>
   <td>T</td>
   <td>Lijst van gehechtheid voor een taak.<br /> </td>
  </tr>
  <tr>
   <td>toewijzingen <br /> </td>
   <td>T</td>
   <td>Lijst van taken van een taak.<br /> </td>
  </tr>
 </tbody>
</table>

1. Filter

   Filter is in feite een wachtrij van een gebruiker of groep. Wanneer een taak aan gebruiker/groep wordt toegewezen, wordt de taak toegevoegd in overeenkomstige rij.

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschap</strong></td>
   <td><strong>Alleen client</strong></td>
   <td><strong>Opmerkingen</strong></td>
  </tr>
  <tr>
   <td>isDefault <br type="_moz" /> </td>
   <td>F</td>
   <td>Waar als de rij standaardrij van de het programma geopende gebruiker is, anders vals.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>name<br type="_moz" /> </td>
   <td>F</td>
   <td>Naam van de eigenaar van de rij.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>qid</td>
   <td>F</td>
   <td>Id van de wachtrij.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>type</td>
   <td>F</td>
   <td>Het bevat het type van de rij.<br /> 0 - Gebruikerswachtrij.<br /> 1 Gedeelde wachtrij.<br /> 2. Groepswachtrij.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>query</td>
   <td>T</td>
   <td>Dit bevat query die aan een filter is gekoppeld. Deze vraag wordt gebruikt om taken van volledige tasklist te zoeken.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>taken</td>
   <td>T</td>
   <td>Het bevat een lijst van alle taken die tot een filter behoren.<br type="_moz" /> </td>
  </tr>
 </tbody>
</table>

1. Buiten het bureau

   U kunt uw uit-van-bureauprogramma beheren en de stroom van taken controleren die aan u in uw afwezigheid worden toegewezen.

<table>
 <tbody>
  <tr>
   <td><strong> Bezit </strong><br type="_moz" /> </td>
   <td><strong> slechts Cliënt </strong><br type="_moz" /> </td>
   <td><strong> Commentaren </strong><br type="_moz" /> </td>
  </tr>
  <tr>
   <td>dateRanges <br type="_moz" /> </td>
   <td>F</td>
   <td>Het bevat arrayvoorwerpen van uit-van-bureauprogramma's van een gebruiker. In elk planningsvoorwerp, bevat het begingebied van startDate de begindatum van het programma en einddatum het gebied bevat de einddatum van het programma. Als endDate in programma ongeldig is, impliceert het dat de gebruiker niet de einddatum van uit-van-bureauprogramma heeft gepland.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>isNoPrimaryDesignate <br type="_moz" /> </td>
   <td>F</td>
   <td>Waar als er geen primaire aanwijzen in als de gebruiker buiten-van-bureau is.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>isOutOfOffice <br type="_moz" /> </td>
   <td>F</td>
   <td>True if user is out-of-office.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>outOfOfficeDesignate <br type="_moz" /> </td>
   <td>F</td>
   <td>Het bevat details van gebruiker die als primaire aanwijzen door gebruiker wordt toegewezen.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>processSpecificDesignates <br type="_moz" /> </td>
   <td>F</td>
   <td>Het bevat serie van voorwerpen voor proces-specifieke uit-van-bureau aangewezen. In elk proces-specifiek wijs voorwerp toe, bevat processName de naam van het proces, isNotDesignated is waar als geen gebruiker voor het overeenkomstige proces wordt toegewezen, en userDesignated is ongeldig als geen gebruiker anders details van de gebruiker toegewezen voor het overeenkomstige proces.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>processen <br type="_moz" /> </td>
   <td>T</td>
   <td>Het bevat een lijst van alle processen die aan de gebruiker beschikbaar zijn.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>initialOutOfOfficeSettings <br type="_moz" /> </td>
   <td>T</td>
   <td>Het bevat aanvankelijke out-of-office montages van gebruiker die aanvankelijk worden gehaald.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>outOfOfficeSettings <br type="_moz" /> </td>
   <td>T</td>
   <td>Het bevat gewijzigde uit-van-bureaumontages.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>userSearchHistory <br type="_moz" /> </td>
   <td>T</td>
   <td>Het bevat een lijst van gebruikers die door een het programma geopende gebruiker tot datum worden gezocht.<br type="_moz" /> </td>
  </tr>
 </tbody>
</table>

1. Procesinstantie

   Een procesinstantie wordt gecreeerd wanneer een proces via werkruimte of werkbank wordt aangehaald.

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschap</strong></td>
   <td><strong>Alleen client</strong></td>
   <td><strong>Opmerkingen</strong></td>
  </tr>
  <tr>
   <td>description<br type="_moz" /> </td>
   <td>F</td>
   <td>Beschrijving van procesinstantie <br type="_moz" /> </td>
  </tr>
  <tr>
   <td>initiator</td>
   <td>F</td>
   <td>Naam van initiatiefnemer van een procesinstantie.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>initiatorId</td>
   <td>F</td>
   <td>Id van initiator van procesinstantie.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>processCompleteTime <br type="_moz" /> </td>
   <td>F</td>
   <td>Tijdstempel wanneer het proces is voltooid.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>processInstanceId<br type="_moz" /> </td>
   <td>F</td>
   <td>Id van procesinstantie.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>processInstanceStatus <br type="_moz" /> </td>
   <td>F</td>
   <td>0 = geïnitieerd <br /> 1 = Lopend <br /> 2 = Volledig <br /> 3 = Voltooiend <br /> 4 = Beëindigd <br /> 5 = Beëindigd <br /> 6 = Opgeschort <br /> 7 = Opgeschort <br /> 8 = Onophoudelijk <br type="_moz" /> </td>
  </tr>
  <tr>
   <td>processName <br type="_moz" /> </td>
   <td>F</td>
   <td>Naam van het proces.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>processStartTime <br type="_moz" /> </td>
   <td>F</td>
   <td>Tijdstempel wanneer het proces is gestart.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>processVariables <br type="_moz" /> </td>
   <td>F</td>
   <td>Array van objecten met procesvariabelen. Elk voorwerp van de procesvariabele bevat naam die naam van procesvariabele is, waarde die waarde van procesvariabele is en type dat type van procesvariabele is.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>tasklist <br type="_moz" /> </td>
   <td>T</td>
   <td>Taken die door deze procesinstantie worden geproduceerd.<br type="_moz" /> </td>
  </tr>
 </tbody>
</table>

1. Procesnaam

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschap</strong></td>
   <td><strong>Alleen client</strong></td>
   <td><strong>Opmerkingen</strong></td>
  </tr>
  <tr>
   <td>processMajorVersion <br type="_moz" /> </td>
   <td>F</td>
   <td>Belangrijke versie van een proces.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>processMinorVersion <br type="_moz" /> </td>
   <td>F</td>
   <td>Kleine versie van een proces.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>processName <br type="_moz" /> </td>
   <td>F</td>
   <td>Naam van het proces.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>processTitle<br type="_moz" /> </td>
   <td>F</td>
   <td>Titel van het proces.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>processInstanceList <br type="_moz" /> </td>
   <td>T</td>
   <td>Lijst van procesinstanties voor dit proces.<br type="_moz" /> </td>
  </tr>
 </tbody>
</table>

1. Taaktoewijzingsobject

   Taaktoewijzingsobject bevat informatie over de taaktoewijzing. Hieronder vindt u de eigenschappen van de taaktoewijzing.

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschap</strong></td>
   <td><strong>Alleen client</strong></td>
   <td><strong>Opmerkingen</strong></td>
  </tr>
  <tr>
   <td>assignCreateTime <br type="_moz" /> </td>
   <td>F</td>
   <td>Tijdstempel wanneer deze toewijzing van een taak wordt gemaakt.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>assignType <br type="_moz" /> </td>
   <td>F</td>
   <td>0 = Eerste Taak <br /> 1 = Voorwaarts (De Taak is door:sturen aan huidige eigenaar van taak.)<br /> 2 = Geretourneerd (Taak is teruggekeerd aan huidige eigenaar van taak door vorige eigenaar van taak.)<br /> 3 = Gevraagd (Taak is gevorderd door huidige eigenaar van taak.)<br /> 4 = Escalatie (Taak is toegewezen aan huidige eigenaar van taak na escalatie.)<br /> 5 = Toegewezen beheerder (Taak is toegewezen door beheerder aan huidige eigenaar van taak.)<br /> 6 = Consulted (Taak is geraadpleegd aan huidige eigenaar van taak.) <br type="_moz" /> </td>
  </tr>
  <tr>
   <td>assignUpdateTime <br type="_moz" /> </td>
   <td>F</td>
   <td>Tijdstempel wanneer deze toewijzing van een taak wordt bijgewerkt.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>queueId<br type="_moz" /> </td>
   <td>F</td>
   <td>Identiteitskaart van Rij van huidige eigenaar van taak.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>queueOwner <br type="_moz" /> </td>
   <td>F</td>
   <td>Naam van huidige eigenaar van taak.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>queueOwnerId<br type="_moz" /> </td>
   <td>F</td>
   <td>Identiteitskaart van huidige eigenaar van taak.<br type="_moz" /> </td>
  </tr>
 </tbody>
</table>

1. ACL-object taak

   Het ACL van de taak voorwerp bevat informatie over toestemmingen zoals voorwaarts, aandeel, raadpleeg, etc., van een taak. Na zijn de eigenschappen van ACL van taak.

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschap</strong></td>
   <td><strong>Alleen client</strong></td>
   <td><strong>Opmerkingen</strong></td>
  </tr>
  <tr>
   <td>canAddAttachments <br type="_moz" /> </td>
   <td>F</td>
   <td>Indien waar, kunnen de gehechtheid aan taak worden toegevoegd.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>canAddNotes <br type="_moz" /> </td>
   <td>F</td>
   <td>Indien waar (true), kunnen notities aan de taak worden toegevoegd.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>canClaim <br type="_moz" /> </td>
   <td>F</td>
   <td>Indien waar (true), kan de taak worden geclaimd.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>canConsult <br type="_moz" /> </td>
   <td>F</td>
   <td>Indien waar (true), kan de taak worden geraadpleegd.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>canForward <br type="_moz" /> </td>
   <td>F</td>
   <td>Indien waar, kan de taak door:sturen.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>canShare <br type="_moz" /> </td>
   <td>F</td>
   <td>Indien waar (true), kan de taak worden gedeeld.<br type="_moz" /> </td>
  </tr>
 </tbody>
</table>

1. Taakbijlage

   U kunt bijlagen toevoegen aan een taak. Bijlage kan van het type bijlage en nota zijn. Hieronder vindt u de eigenschappen van het bijlageobject.

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschap</strong></td>
   <td><strong>Alleen client</strong></td>
   <td><strong>Opmerkingen</strong></td>
  </tr>
  <tr>
   <td>creationDate <br type="_moz" /> </td>
   <td>F</td>
   <td>Tijdstempel bij maken van bijlage.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>creatorId<br type="_moz" /> </td>
   <td>F</td>
   <td>Identiteitskaart van gebruiker die de gehechtheid toevoegde.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>creatorName <br type="_moz" /> </td>
   <td>F</td>
   <td>Naam van de gebruiker die de gehechtheid toevoegde.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>description<br type="_moz" /> </td>
   <td>F</td>
   <td>Beschrijving van de bijlage.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>fileName<br type="_moz" /> </td>
   <td>F</td>
   <td>Naam van gehechtheid.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>id<br type="_moz" /> </td>
   <td>F</td>
   <td>Id van bijlage.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>lastModifiedDate <br type="_moz" /> </td>
   <td>F</td>
   <td>Tijdstempel bij laatste wijziging van bijlage.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>noteExtended <br type="_moz" /> </td>
   <td>F</td>
   <td>Indien waar, is de nota een uitgebreide (lange) nota.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>machtigingen <br type="_moz" /> </td>
   <td>F</td>
   <td>Machtigingen die aan een bijlage zijn gekoppeld. allowRead het gebied is voor gelezen toestemming, allowWrite is voor schrijftoestemming, allowDelete is voor schrappingstoestemming.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>size<br type="_moz" /> </td>
   <td>F</td>
   <td>Grootte van de bijlage in bytes.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>taskId<br type="_moz" /> </td>
   <td>F</td>
   <td>Identiteitskaart van taak waaraan gehechtheid wordt toegevoegd.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>type<br type="_moz" /> </td>
   <td>F</td>
   <td>Het type is gehechtheid voor dossiers en het Type is nota voor nota's.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>formattedCreationDate <br type="_moz" /> </td>
   <td>T</td>
   <td>Het bevat de aanmaakdatum van de gehechtheid volgens de montages UI van de gebruiker.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>formattedDescription <br type="_moz" /> </td>
   <td>T</td>
   <td>Beschrijving van opgemaakte bijlage. Wordt gebruikt om speciale tekens weer te geven die aanwezig zijn in de bijlagebeschrijving in de AEM Forms-werkruimte.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>formattedFileName <br type="_moz" /> </td>
   <td>T</td>
   <td>Opgemaakte bijlagenaam. Wordt gebruikt om speciale tekens weer te geven die zich in de naam van de bijlage in de AEM Forms-werkruimte bevinden. Dit is slechts voor nota's.<br type="_moz" /> </td>
  </tr>
 </tbody>
</table>

1. Gebruiker

   Hieronder vindt u de eigenschappen van het gebruikersobject.

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschap</strong></td>
   <td><strong>Alleen client</strong></td>
   <td><strong>Opmerkingen</strong></td>
  </tr>
  <tr>
   <td>address<br type="_moz" /> </td>
   <td>F</td>
   <td>Adres van de gebruiker.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>commonName <br type="_moz" /> </td>
   <td>F</td>
   <td>Algemene naam van de gebruiker.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>description<br type="_moz" /> </td>
   <td>F</td>
   <td>Beschrijving van de gebruiker.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>directGroupMembership <br type="_moz" /> </td>
   <td>F</td>
   <td>Lijst van gebruikersgroep.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>displayName <br type="_moz" /> </td>
   <td>F</td>
   <td>De naam van de vertoning van de gebruiker.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>email<br type="_moz" /> </td>
   <td>F</td>
   <td>E-mailadres van de gebruiker.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>isOutOfOffice <br type="_moz" /> </td>
   <td>F</td>
   <td>True if user is out-of-office.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>lastName <br type="_moz" /> </td>
   <td>F</td>
   <td>Achternaam van de gebruiker.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>firstName <br type="_moz" /> </td>
   <td>F</td>
   <td>Voornaam van de gebruiker.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>oid<br type="_moz" /> </td>
   <td>F</td>
   <td>Identiteitskaart van de gebruiker.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>org<br type="_moz" /> </td>
   <td>F</td>
   <td>Naam van organisatie van de gebruiker.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>postalAddress <br type="_moz" /> </td>
   <td>F</td>
   <td>Postadres van de gebruiker.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>Telefoon <br type="_moz" /> </td>
   <td>F</td>
   <td>Het aantal van het contact van de gebruiker.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>phoneNumber <br type="_moz" /> </td>
   <td>F</td>
   <td>Het aantal van het contact van de gebruiker.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>userid<br type="_moz" /> </td>
   <td>F</td>
   <td>Login identiteitskaart van de gebruiker.<br type="_moz" /> </td>
  </tr>
 </tbody>
</table>
