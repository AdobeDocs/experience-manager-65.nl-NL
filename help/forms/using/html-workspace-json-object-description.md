---
title: Beschrijving van JSON-object in AEM Forms-werkruimte
seo-title: Beschrijving van JSON-object in AEM Forms-werkruimte
description: Conceptuele informatie over de JSON JavaScript-objecten die in de werkruimte van LiveCycle AEM Forms worden gebruikt voor aanpassing, uitbreiding, wijziging en hergebruik.
seo-description: Conceptuele informatie over de JSON JavaScript-objecten die in de werkruimte van LiveCycle AEM Forms worden gebruikt voor aanpassing, uitbreiding, wijziging en hergebruik.
uuid: 91c923c8-144a-4453-ba91-6a5193f1c4c4
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: 61b7246d-ed28-4470-a0a2-a4aaf1a061a4
translation-type: tm+mt
source-git-commit: 56c6cfd437ef185336e81373bd5f758205b96317

---


# Beschrijving van JSON-object in AEM Forms-werkruimte {#aem-forms-workspace-json-object-description}

JSON-objecten die worden gebruikt in de werkruimte van AEM-formulieren, worden hieronder beschreven.

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
   <td>Categorie-id<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>description<br type="_moz" /> </td>
   <td>F</td>
   <td>Categoriebeschrijving<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>parentOid<br type="_moz" /> </td>
   <td>F</td>
   <td>Bevat id van bovenliggende categorie<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>startPointsList<br type="_moz" /> </td>
   <td>T</td>
   <td>Bevat een lijst met alle startpunten die in een categorie aanwezig zijn</td>
  </tr>
  <tr>
   <td>categoryList</td>
   <td>T</td>
   <td>Bevat een lijst met directe onderliggende categorieën van een categorie<br type="_moz" /> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Alle beginpunten en Favorieten zijn categorieën die aan clientzijde zijn gedefinieerd. De categorie Favorieten bevat alle startpunten die door de gebruiker als favoriet zijn gemarkeerd. Alle beginpunten-categorieën bevatten alle beginpunten.

1. Startpoint

   Het beginpunt wordt gebruikt om een proces van de werkruimte te beginnen wanneer aangeroepen.

   | **Eigenschap** | **Alleen client** | **Opmerkingen** |
   |---|---|---|
   | categoryId | F | Het bevat id van de categorie waartoe het startpunt behoort. |
   | beschrijving | F | Het bevat een beschrijving voor een startpunt. |
   | name | F | Deze bevat de naam van het startpunt. |
   | serializedImageTicket | F | Het bevat een afbeeldingsticket dat overeenkomt met het startpunt. Dit beeldkaartje wordt gebruikt in imageUrl gebied van startpoint, om beeld voor startpunt van de server te krijgen. |
   | serviceName | F | Het bevat naam van de dienst voor startpoint. |
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
   <td>Eigenschap<br /> </td>
   <td>Client Only<br /> </td>
   <td>Opmerkingen<br /> </td>
  </tr>
  <tr>
   <td>classOfTask</td>
   <td>F</td>
   <td>De taakklasse is 'LC8' wanneer de taak een andere lc8-taak is dan 'Standaard'.<br /> </td>
  </tr>
  <tr>
   <td>completeTime<br /> </td>
   <td>F</td>
   <td>Het bevat de tijdstempel wanneer de taak is voltooid.<br /> </td>
  </tr>
  <tr>
   <td>consultGroupId<br /> </td>
   <td>F</td>
   <td>Het bevat id van een groep waarvoor de taak kan worden geraadpleegd. Deze wordt tijdens het ontwerpen van het proces ingesteld.<br /> </td>
  </tr>
  <tr>
   <td>createTime<br /> </td>
   <td>F</td>
   <td>De tijdstempel wordt weergegeven wanneer een taak wordt gemaakt.<br /> </td>
  </tr>
  <tr>
   <td>creationId<br /> </td>
   <td>F</td>
   <td>Het bevat de id van de gebruiker die de taak heeft gemaakt.<br /> </td>
  </tr>
  <tr>
   <td>currentAssignment<br /> </td>
   <td>F</td>
   <td>Het bevat details over de huidige taaktoewijzing.<br /> </td>
  </tr>
  <tr>
   <td>deadline<br /> </td>
   <td>F</td>
   <td>Het bevat de tijdstempel dat wanneer een taak zijn deadline zal bereiken.<br /> </td>
  </tr>
  <tr>
   <td>description<br /> </td>
   <td>F</td>
   <td>Het bevat een beschrijving van de taak.<br /> </td>
  </tr>
  <tr>
   <td>displayName<br /> </td>
   <td>F</td>
   <td>Deze bevat de weergavenaam van de taak.<br /> </td>
  </tr>
  <tr>
   <td>forwardGroupId<br /> </td>
   <td>F</td>
   <td>Het bevat identiteitskaart van een groep waaraan de taak kan worden door:sturen. Deze wordt tijdens het ontwerpen van het proces ingesteld.<br /> </td>
  </tr>
  <tr>
   <td>instructies<br /> </td>
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
   <td>isOpenFullScreen<br /> </td>
   <td>F</td>
   <td>Indien waar (true), neemt het formulier bij het openen van de taak de eerste keer het volledige scherm in beslag.<br /> </td>
  </tr>
  <tr>
   <td>isRouteSelectionRequired<br /> </td>
   <td>F</td>
   <td>Indien waar, moet de route worden geselecteerd om de taak te voltooien.<br /> </td>
  </tr>
  <tr>
   <td>isShowAttachments<br /> </td>
   <td>F</td>
   <td>Bijlagen worden weergegeven als dit waar is.<br /> </td>
  </tr>
  <tr>
   <td>isStartTask<br /> </td>
   <td>F</td>
   <td>Indien waar (true), wordt de taak vanaf het beginpunt gemaakt.<br /> </td>
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
   <td>priority<br /> </td>
   <td>F</td>
   <td>Het bevat een prioriteit.<br /> 1 = hoogste prioriteit<br /> 2 = hoge prioriteit<br /> 3 = normale prioriteit<br /> 4 = lage prioriteit<br /> 5 = laagste prioriteit<br /> </td>
  </tr>
  <tr>
   <td>processInstanceId</td>
   <td>F</td>
   <td>Id van de procesinstantie waarvan taak deel uitmaakt.<br /> </td>
  </tr>
  <tr>
   <td>processInstanceStatus<br /> </td>
   <td>F</td>
   <td>Status van procesexemplaar van taak.<br /> </td>
  </tr>
  <tr>
   <td>reminderCount<br /> </td>
   <td>F</td>
   <td>Het bevat aantal herinneringen voor de taak.<br /> </td>
  </tr>
  <tr>
   <td>routeList<br /> </td>
   <td>F</td>
   <td>Het bevat lijst van routes verbonden aan taak. De gebruiker kan de taak voltooien door om het even welke route van routenelijst te selecteren.<br /> </td>
  </tr>
  <tr>
   <td>selectedRoute<br /> </td>
   <td>F</td>
   <td>Het bevat naam van de route die werd geselecteerd toen de taak werd voltooid.<br /> </td>
  </tr>
  <tr>
   <td>serializedImageTicket<br /> </td>
   <td>F</td>
   <td>Het bevat een afbeeldingsticket dat overeenkomt met een taak. Dit beeldkaartje wordt gebruikt in imageUrl gebied van taak, om beeld voor taak van de server te krijgen.<br /> <br /> </td>
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
   <td>status<br /> </td>
   <td>F</td>
   <td>1 = Gemaakt (Taak wordt gemaakt vanaf beginpunt.)<br /> 2 = Gemaakt en Opgeslagen (Taak wordt gemaakt vanaf het beginpunt en opgeslagen.)<br /> 3 = Toegewezen (Taak wordt toegewezen aan de gebruiker nadat het proces is begonnen.)<br /> 4 = Toegewezen en Opgeslagen (Taak wordt toegewezen en opgeslagen.)<br /> 100 = Voltooid (Taak is voltooid.)<br /> 101 = Gedetailleerd (Taak heeft de deadline bereikt.)<br /> 102 = beëindigd<br /> </td>
  </tr>
  <tr>
   <td>stepName<br /> </td>
   <td>F</td>
   <td>Deze bevat een naam van de taakset tijdens het ontwerpen van processen.<br /> </td>
  </tr>
  <tr>
   <td>summaryUrl<br /> </td>
   <td>F</td>
   <td>Het bevat taak summiere url.<br /> </td>
  </tr>
  <tr>
   <td>taskACL<br /> </td>
   <td>F</td>
   <td>Het is toegangsbeheerlijst voor een taak.<br /> </td>
  </tr>
  <tr>
   <td>taskId<br /> </td>
   <td>F</td>
   <td>Id van een taak.<br /> </td>
  </tr>
  <tr>
   <td>updateTime<br /> </td>
   <td>F</td>
   <td>Tijdstempel wanneer taak voor het laatst is bijgewerkt.<br /> </td>
  </tr>
  <tr>
   <td>formUrl<br /> </td>
   <td>T</td>
   <td>Het bevat URL van formulier voor een taak.<br /> </td>
  </tr>
  <tr>
   <td>taskFormType<br /> </td>
   <td>T</td>
   <td>Het bevat het type taakformulier. Met dit veld wordt de taak op de client weergegeven als pdf for, swf form enzovoort.<br /> </td>
  </tr>
  <tr>
   <td>showDirectActions<br /> </td>
   <td>T</td>
   <td>Indien waar (true), zijn routeacties zichtbaar in de werkruimte.<br /> </td>
  </tr>
  <tr>
   <td>showACLActions<br /> </td>
   <td>T</td>
   <td>Indien waar (true), zijn acties zoals forward, consult en share zichtbaar in de werkruimte.<br /> </td>
  </tr>
  <tr>
   <td>supportsOffline<br /> </td>
   <td>T</td>
   <td>Indien waar (true), kan het formulier offline worden genomen. Dit is alleen voor PDF-formulieren.<br /> </td>
  </tr>
  <tr>
   <td>supportsSave<br /> </td>
   <td>T</td>
   <td>Indien waar (true), kan de gebruiker de taak opslaan.<br /> </td>
  </tr>
  <tr>
   <td>readerSubmitOptions<br /> </td>
   <td>T</td>
   <td>Dit object bevat opties die worden gebruikt om PDF-formulieren via Reader te verzenden als het PDF-formulier geen verzendknop bevat.<br /> </td>
  </tr>
  <tr>
   <td>isDefaultImage<br /> </td>
   <td>T</td>
   <td>Geeft aan of er een afbeelding is opgegeven voor proces of niet. True if there is no image associated with process else false.<br /> </td>
  </tr>
  <tr>
   <td>historyTaskList<br /> </td>
   <td>T</td>
   <td>Het bevat een lijst met taken die op het tabblad Historie van taakdetails worden gebruikt.<br /> </td>
  </tr>
  <tr>
   <td>isOwner<br /> </td>
   <td>T</td>
   <td>Waar als het programma geopende gebruiker eigenaar van taak is.<br /> </td>
  </tr>
  <tr>
   <td>availableCommands<br /> </td>
   <td>T</td>
   <td>Het bevat alle acties die op taak kunnen worden ondernomen.<br /> </td>
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
   <td>Het bevat bevelen zoals slot, ontgrendelen, verlaten, terugkeer, eis, etc. zoals beschikbaar.<br /> </td>
  </tr>
  <tr>
   <td>processInstanceInfo<br /> </td>
   <td>T</td>
   <td>Het bevat informatie over de procesinstantie van de taak.<br /> </td>
  </tr>
  <tr>
   <td>processVariables<br /> </td>
   <td>T<br /> </td>
   <td>De klasse bevat een array van objecten met procesvariabelen, indien aanwezig.<br /> </td>
  </tr>
  <tr>
   <td>pendingTasks<br /> </td>
   <td>T</td>
   <td>Het bevat een lijst met in behandeling zijnde taken voor de procesinstantie van de taak.<br /> </td>
  </tr>
  <tr>
   <td>userActions<br /> </td>
   <td>T</td>
   <td>Het is een array van objecten. Elk object bevat details over de route en het bijbehorende bevestigingsbericht, indien aanwezig.<br /> </td>
  </tr>
  <tr>
   <td>dataUrl<br /> </td>
   <td>T</td>
   <td>Het is de URL voor de gegevens in de vorm van een taak.<br /> </td>
  </tr>
  <tr>
   <td>externalAppConfig<br /> </td>
   <td>T</td>
   <td>Dit is de configuratie voor toepassingsformulieren van derden.<br /> </td>
  </tr>
  <tr>
   <td>ingediend<br /> </td>
   <td>T</td>
   <td>Waar als de taak wordt voorgelegd.<br /> </td>
  </tr>
  <tr>
   <td>attachments<br /> </td>
   <td>T</td>
   <td>Lijst met bijlagen voor een taak.<br /> </td>
  </tr>
  <tr>
   <td>toewijzingen<br /> </td>
   <td>T</td>
   <td>Lijst met taakopdrachten.<br /> </td>
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
   <td>Naam van de eigenaar van de wachtrij.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>qid</td>
   <td>F</td>
   <td>Id van de wachtrij.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>type</td>
   <td>F</td>
   <td>Het bevat het type van de rij.<br /> 0 - Gebruikerswachtrij.<br /> 1. Gedeelde wachtrij.<br /> 2. Groepswachtrij.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>query</td>
   <td>T</td>
   <td>Dit bevat query die aan een filter is gekoppeld. Deze query wordt gebruikt om taken te zoeken vanuit de volledige taaklijst.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>taken</td>
   <td>T</td>
   <td>Deze bevat een lijst met alle taken die bij een filter horen.<br type="_moz" /> </td>
  </tr>
 </tbody>
</table>

1. Buiten het bureau

   U kunt uw uit-van-bureauprogramma beheren en de stroom van taken controleren die aan u in uw afwezigheid worden toegewezen.

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschap</strong><br type="_moz" /> </td>
   <td><strong>Alleen client</strong><br type="_moz" /> </td>
   <td><strong>Opmerkingen</strong><br type="_moz" /> </td>
  </tr>
  <tr>
   <td>dateRanges<br type="_moz" /> </td>
   <td>F</td>
   <td>Het bevat arrayvoorwerpen van uit-van-bureauprogramma's van een gebruiker. In elk planningsvoorwerp, bevat het begingebied van startDate de begindatum van het programma en einddatum het gebied bevat de einddatum van het programma. Als endDate in programma ongeldig is, impliceert het dat de gebruiker niet de einddatum van out-of-office programma heeft gepland.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>isNoPrimaryDesignate<br type="_moz" /> </td>
   <td>F</td>
   <td>Waar als er geen primair aanwijst in het geval als de gebruiker buiten-van-bureau is.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>isOutOfOffice<br type="_moz" /> </td>
   <td>F</td>
   <td>True if user is out-of-office.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>outOfOfficeDesignate<br type="_moz" /> </td>
   <td>F</td>
   <td>Het bevat details van gebruiker die als primaire aanduiding door gebruiker wordt toegewezen.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>processSpecificDesignates<br type="_moz" /> </td>
   <td>F</td>
   <td>Het bevat een array met objecten voor processpecifieke aanwijzen buiten het kantoor. In elk proces-specifiek wijs voorwerp toe, bevat processName de naam van het proces, isNotDesignated is waar als geen gebruiker voor het overeenkomstige proces wordt toegewezen, en userDesignated is ongeldig als geen gebruiker anders details van de gebruiker toewees voor het overeenkomstige proces.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>processen<br type="_moz" /> </td>
   <td>T</td>
   <td>Het bevat een lijst van alle processen die aan de gebruiker beschikbaar zijn.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>initialOutOfOfficeSettings<br type="_moz" /> </td>
   <td>T</td>
   <td>Het bevat aanvankelijke out-of-office montages van gebruiker die aanvankelijk worden gehaald.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>outOfOfficeSettings<br type="_moz" /> </td>
   <td>T</td>
   <td>Het bevat gewijzigde instellingen voor buiten het kantoor.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>userSearchHistory<br type="_moz" /> </td>
   <td>T</td>
   <td>Het bevat een lijst met gebruikers die door de aangemelde gebruiker tot de datum worden doorzocht.<br type="_moz" /> </td>
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
   <td>Beschrijving van procesinstantie<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>initiator</td>
   <td>F</td>
   <td>Naam van initiator van een procesinstantie.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>initiatorId</td>
   <td>F</td>
   <td>Id van initiator van procesinstantie.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>processCompleteTime<br type="_moz" /> </td>
   <td>F</td>
   <td>Tijdstempel wanneer het proces is voltooid.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>processInstanceId<br type="_moz" /> </td>
   <td>F</td>
   <td>Id van procesinstantie.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>processInstanceStatus<br type="_moz" /> </td>
   <td>F</td>
   <td>0 = geïnitieerd<br /> 1 = start<br /> 2 = voltooid<br /> 3 = voltooid<br /> 4 = beëindigd<br /> 5 = beëindigd<br /> 6 = onderbroken<br /> 7 = onderbroken<br /> 8 = ononderbroken<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>processName<br type="_moz" /> </td>
   <td>F</td>
   <td>Naam van het proces.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>processStartTime<br type="_moz" /> </td>
   <td>F</td>
   <td>Tijdstempel wanneer het proces is gestart.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>processVariables<br type="_moz" /> </td>
   <td>F</td>
   <td>Array van objecten met procesvariabelen. Elk procesveranderlijke voorwerp bevat naam die naam is van procesvariabele, waarde die waarde van procesvariabele is en type dat type van procesvariabele is.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>taaklijst<br type="_moz" /> </td>
   <td>T</td>
   <td>Taken die door deze procesinstantie worden gegenereerd.<br type="_moz" /> </td>
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
   <td>processMajorVersion<br type="_moz" /> </td>
   <td>F</td>
   <td>Belangrijke versie van een proces.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>processMinorVersion<br type="_moz" /> </td>
   <td>F</td>
   <td>Kleine versie van een proces.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>processName<br type="_moz" /> </td>
   <td>F</td>
   <td>Naam van het proces.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>processTitle<br type="_moz" /> </td>
   <td>F</td>
   <td>Titel van het proces.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>processInstanceList<br type="_moz" /> </td>
   <td>T</td>
   <td>Lijst met procesinstanties voor dit proces.<br type="_moz" /> </td>
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
   <td>assignCreateTime<br type="_moz" /> </td>
   <td>F</td>
   <td>Tijdstempel wanneer deze toewijzing van een taak wordt gemaakt.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>assignType<br type="_moz" /> </td>
   <td>F</td>
   <td>0 = Oorspronkelijke Taak<br /> 1 = Voorwaarts (De Taak is door:sturen aan huidige eigenaar van taak.)<br /> 2 = teruggekeerd (Taak is teruggekeerd aan huidige eigenaar van taak door vorige eigenaar van taak.)<br /> 3 = Gevraagd (Taak is gevorderd door huidige eigenaar van taak.)<br /> 4 = Escalatie (Taak is toegewezen aan huidige eigenaar van taak na escalatie.)<br /> 5 = Toegewezen beheerder (Taak is toegewezen door beheerder aan huidige eigenaar van taak.)<br /> 6 = geraadpleegd (Taak is geraadpleegd aan de huidige eigenaar van de taak.)<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>assignUpdateTime<br type="_moz" /> </td>
   <td>F</td>
   <td>Tijdstempel wanneer deze toewijzing van een taak wordt bijgewerkt.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>queueId<br type="_moz" /> </td>
   <td>F</td>
   <td>Id van Wachtrij van huidige eigenaar van taak.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>queueOwner<br type="_moz" /> </td>
   <td>F</td>
   <td>Naam van huidige eigenaar van taak.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>queueOwnerId<br type="_moz" /> </td>
   <td>F</td>
   <td>Id van huidige eigenaar van taak.<br type="_moz" /> </td>
  </tr>
 </tbody>
</table>

1. ACL-object taak

   Het ACL voorwerp van de taak bevat informatie over toestemmingen zoals voorwaarts, aandeel, raadpleeg enz. van een taak. Na zijn de eigenschappen van ACL van taak.

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschap</strong></td>
   <td><strong>Alleen client</strong></td>
   <td><strong>Opmerkingen</strong></td>
  </tr>
  <tr>
   <td>canAddAttachments<br type="_moz" /> </td>
   <td>F</td>
   <td>Indien waar (true), kunnen bijlagen aan de taak worden toegevoegd.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>canAddNotes<br type="_moz" /> </td>
   <td>F</td>
   <td>Indien waar (true), kunnen notities aan de taak worden toegevoegd.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>canClaim<br type="_moz" /> </td>
   <td>F</td>
   <td>Indien waar (true), kan de taak worden opgehaald.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>canConsult<br type="_moz" /> </td>
   <td>F</td>
   <td>Indien waar (true), kan de taak worden geraadpleegd.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>canForward<br type="_moz" /> </td>
   <td>F</td>
   <td>Indien waar (true), kan de taak worden doorgestuurd.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>canShare<br type="_moz" /> </td>
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
   <td>creationDate<br type="_moz" /> </td>
   <td>F</td>
   <td>Tijdstempel bij maken van bijlage.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>creatorId<br type="_moz" /> </td>
   <td>F</td>
   <td>Id van gebruiker die de bijlage heeft toegevoegd.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>creatorName<br type="_moz" /> </td>
   <td>F</td>
   <td>Naam van de gebruiker die de bijlage heeft toegevoegd.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>description<br type="_moz" /> </td>
   <td>F</td>
   <td>Beschrijving van de bijlage.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>fileName<br type="_moz" /> </td>
   <td>F</td>
   <td>Naam van bijlage.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>id<br type="_moz" /> </td>
   <td>F</td>
   <td>Id van bijlage.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>lastModifiedDate<br type="_moz" /> </td>
   <td>F</td>
   <td>Tijdstempel wanneer bijlage voor het laatst is gewijzigd.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>noteExtended<br type="_moz" /> </td>
   <td>F</td>
   <td>Indien waar (true), is de opmerking een uitgebreide (lange) notitie.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>permissions<br type="_moz" /> </td>
   <td>F</td>
   <td>Machtigingen die aan een bijlage zijn gekoppeld. allowRead-veld is bestemd voor leesmachtigingen, allowWrite is voor schrijfmachtigingen, allowDelete is voor verwijderingsmachtigingen.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>size<br type="_moz" /> </td>
   <td>F</td>
   <td>Grootte van de bijlage in bytes.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>taskId<br type="_moz" /> </td>
   <td>F</td>
   <td>Id van taak waaraan bijlage wordt toegevoegd.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>type<br type="_moz" /> </td>
   <td>F</td>
   <td>Type is een bijlage voor bestanden en Type is een notitie voor notities.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>formattedCreationDate<br type="_moz" /> </td>
   <td>T</td>
   <td>Deze bevat de aanmaakdatum van de bijlage volgens de gebruikersinterface-instellingen.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>formattedDescription<br type="_moz" /> </td>
   <td>T</td>
   <td>Beschrijving van opgemaakte bijlage. Wordt gebruikt om speciale tekens weer te geven die aanwezig zijn in de beschrijving van de bijlage in de werkruimte van AEM-formulieren.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>formattedFileName<br type="_moz" /> </td>
   <td>T</td>
   <td>Opgemaakte bijlagenaam. Wordt gebruikt om speciale tekens weer te geven die zich in de naam van de bijlage in de werkruimte van AEM-formulieren bevinden. Dit is alleen voor notities.<br type="_moz" /> </td>
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
   <td>adres<br type="_moz" /> </td>
   <td>F</td>
   <td>Adres van de gebruiker.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>commonName<br type="_moz" /> </td>
   <td>F</td>
   <td>Algemene naam van de gebruiker.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>description<br type="_moz" /> </td>
   <td>F</td>
   <td>Beschrijving van de gebruiker.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>directGroupMembership<br type="_moz" /> </td>
   <td>F</td>
   <td>Lijst met gebruikersgroepen.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>displayName<br type="_moz" /> </td>
   <td>F</td>
   <td>Weergavenaam van de gebruiker.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>email<br type="_moz" /> </td>
   <td>F</td>
   <td>E-mailadres van de gebruiker.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>isOutOfOffice<br type="_moz" /> </td>
   <td>F</td>
   <td>True if user is out-of-office.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>achterNaam<br type="_moz" /> </td>
   <td>F</td>
   <td>Achternaam van de gebruiker.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>voorNaam<br type="_moz" /> </td>
   <td>F</td>
   <td>Voornaam van de gebruiker.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>oid<br type="_moz" /> </td>
   <td>F</td>
   <td>ID van de gebruiker.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>org<br type="_moz" /> </td>
   <td>F</td>
   <td>Naam van de organisatie van de gebruiker.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>postalAddress<br type="_moz" /> </td>
   <td>F</td>
   <td>Postadres van de gebruiker.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>telefoon<br type="_moz" /> </td>
   <td>F</td>
   <td>Contactnummer van de gebruiker.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>phoneNumber<br type="_moz" /> </td>
   <td>F</td>
   <td>Contactnummer van de gebruiker.<br type="_moz" /> </td>
  </tr>
  <tr>
   <td>userid<br type="_moz" /> </td>
   <td>F</td>
   <td>Login-id van de gebruiker.<br type="_moz" /> </td>
  </tr>
 </tbody>
</table>
