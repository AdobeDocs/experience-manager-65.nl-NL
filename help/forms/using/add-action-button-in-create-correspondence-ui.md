---
title: Aangepaste actie/knop toevoegen in interface voor correspondentie maken
description: Leer hoe u een aangepaste handeling/knop toevoegt in de gebruikersinterface voor correspondentie maken
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: correspondence-management
docset: aem65
feature: Correspondence Management
exl-id: a582ba41-83cb-46f2-9de9-3752f6a7820a
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '1854'
ht-degree: 0%

---

# Een aangepaste actieknop toevoegen in de gebruikersinterface voor correspondentie maken {#add-custom-action-button-in-create-correspondence-ui}

## Overzicht {#overview}

Met de oplossing Correspondence Management kunt u aangepaste handelingen toevoegen aan de gebruikersinterface Correspondentie maken.

Het scenario in dit document legt uit hoe u een knop in de gebruikersinterface voor correspondentie maken kunt maken om een brief te delen als een revisiebericht dat aan een e-mail is gekoppeld.

### Vereisten {#prerequisites}

Om dit scenario te voltooien, vereist u het volgende:

* Kennis van CRX en JavaScript
* LiveCycle Server

## Scenario: maak de knop in de gebruikersinterface Correspondentie maken om een brief ter controle te verzenden {#scenario-create-the-button-in-the-create-correspondence-user-interface-to-send-a-letter-for-review}

Het toevoegen van een knop met een actie (hier verzend brief voor overzicht) aan Create Correspondence Gebruikersinterface omvat:

1. De knop toevoegen aan de gebruikersinterface Correspondentie maken
1. Handeling-afhandeling aan de knop toevoegen
1. Het LiveCycle toevoegen om handelingen te kunnen afhandelen

### De knop toevoegen aan de gebruikersinterface Correspondentie maken {#add-the-button-to-the-create-correspondence-user-interface}

1. Ga naar `https://'[server]:[port]'/[ContextPath]/crx/de` en meld u aan als beheerder.
1. Maak in de map Apps een map met de naam `defaultApp` met een pad/structuur die lijkt op de map defaultApp (in de configuratiemap). Gebruik de volgende stappen om de map te maken:

   1. Klik met de rechtermuisknop op de **defaultApp** omslag bij de volgende weg en selecteer **Knoop van de Bedekking**:

      /libs/fd/cm/config/defaultApp/

      ![ knoop van de Bedekking ](assets/1_defaultapp.png)

   1. Zorg ervoor dat het dialoogvenster Overlay-knooppunt de volgende waarden heeft:

      **Weg:** /libs/fd/cm/config/defaultApp/

      **Plaats van de Bedekking:** /apps/

      **de Types van Knoop van de Gelijke:** Gecontroleerd

      ![ knoop van de Bedekking ](assets/2_defaultappoverlaynode.png)

   1. Klik **OK**.
   1. Klik **sparen allen**.

1. Maak een kopie van het bestand acmExtensionsConfig.xml (bestaat onder de tak /libs) onder de tak /apps.

   1. Ga naar /libs/fd/cm/config/defaultApp/acmExtensionsConfig.xml

   1. Klik het acmExtensionsConfig.xml- dossier met de rechtermuisknop aan en selecteer **Exemplaar**.

      ![ ExtensionsConfig.xml van het Exemplaar {](assets/3_acmextensionsconfig_xml_copy.png)

   1. Klik met de rechtermuisknop op de **defaultApp** omslag bij &quot;/apps/fd/cm/config/defaultApp/,&quot;en selecteer **Deeg**.
   1. Klik **sparen allen**.

1. Dubbelklik op de kopie van acmExtencesConfig.xml die u net in de map apps hebt gemaakt. Het bestand wordt geopend voor bewerking.
1. Zoek de volgende code:

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <extensionsConfig>
       <modelExtensions>
           <modelExtension type="LetterInstance">
     <customAction name="Preview" label="loc.letterInstance.preview.label" tooltip="loc.letterInstance.preview.tooltip" styleName="previewButton"/>
               <customAction name="Submit" label="loc.letterInstance.submit.label" tooltip="loc.letterInstance.submit.tooltip" styleName="submitButton" permissionName="forms-users"/>
               <customAction name="SaveAsDraft" label="loc.letterInstance.saveAsDraft.label" tooltip="loc.letterInstance.saveAsDraft.tooltip" styleName="submitButton" permissionName="forms-users"/>
               <customAction name="Close" label="loc.letterInstance.close.label" tooltip="loc.letterInstance.close.tooltip" styleName="closeButton"/>
           </modelExtension>
       </modelExtensions>
   </extensionsConfig>
   ```

1. U kunt Forms Workflow LiveCycle gebruiken om een e-mailbrief te verzenden. Voeg als volgt een customAction-tag toe onder de modelExtension-tag in acmExtensionsConfig.xml:

   ```xml
    <customAction name="Letter Review" label="Letter Review" tooltip="Letter Review" styleName="" permissionName="forms-users" actionHandler="CM.domain.CCRCustomActionHandler">
         <serviceName>Forms Workflow -> SendLetterForReview/SendLetterForReviewProcess</serviceName>
       </customAction>
   ```

   ![ customAction markering ](assets/5_acmextensionsconfig_xml.png)

   De tag modelExtension heeft een set onderliggende tags van customAction die de handeling, machtigingen en weergave van de actieknop configureren. Hieronder volgt een lijst met aangepasteAction-configuratietags:

   | **Naam** | **Beschrijving** |
   |---|---|
   | name | De alfanumerieke naam voor de handeling die moet worden uitgevoerd. Waarde van deze tag is vereist, moet uniek zijn (binnen de tag modelExtension) en moet beginnen met een alfabet. |
   | label | Het label dat op de actieknop moet worden weergegeven |
   | knopinfo | Knopinfo-tekst van de knop, die wordt weergegeven wanneer de gebruiker de muisaanwijzer op de knop plaatst. |
   | styleName | Naam van de aangepaste stijl die op de actieknop wordt toegepast. |
   | permissionName | De overeenkomstige actie wordt getoond slechts als de gebruiker de toestemming heeft die door permissionName wordt gespecificeerd. Wanneer u permissionName opgeeft als `forms-users` , krijgen alle gebruikers toegang tot deze optie. |
   | actionHandler | Volledig gekwalificeerde naam van de klasse ActionHandler die wordt aangeroepen wanneer de gebruiker op de knop klikt. |

   Naast de bovenstaande parameters, kunnen er extra configuraties verbonden aan een customAction zijn. Deze extra configuraties worden ter beschikking gesteld aan de manager door het voorwerp CustomAction.

   | **Naam** | **Beschrijving** |
   |---|---|
   | serviceName | Als een customAction een kindmarkering met name serviceName bevat, dan wanneer het klikken van de relevante knoop/de verbinding, wordt een proces geroepen met de naam die door serviceName markering wordt vertegenwoordigd. Zorg ervoor dat dit proces dezelfde handtekening heeft als het PostProcess Letter. Voeg het voorvoegsel &quot;Forms Workflow ->&quot; toe aan de servicenaam. |
   | Parameters die het voorvoegsel cm_ bevatten in tagnaam | Als een customAction een kindmarkeringen bevat die met naam cm_ beginnen, dan in post proces (of het Proces van Letter Post of het speciale proces dat door de markering serviceName wordt vertegenwoordigd) zijn deze parameters beschikbaar in de inputXML code onder de relevante markering met cm_ prefix verwijderd. |
   | actionName | Wanneer een postproces aan een klik toe te schrijven is, bevat voorgelegde XML een speciale markering met naam onder de markering met de naam van de gebruikersactie. |

1. Klik **sparen allen**.

#### Een map met eigenschappen voor een landinstelling maken in de tak /apps {#create-a-locale-folder-with-properties-file-in-the-apps-branch}

Het bestand ACMExtensionsMessages.properties bevat labels en knopinfo-berichten van verschillende velden in de gebruikersinterface Correspondentie maken. Maak een kopie van dit bestand in de tak /apps om de aangepaste handelingen/knoppen te laten werken.

1. Klik met de rechtermuisknop op de **scène** omslag bij de volgende weg en selecteer **Knoop van de Bedekking**:

   /libs/fd/cm/config/defaultApp/locale

1. Zorg ervoor dat het dialoogvenster Overlay-knooppunt de volgende waarden heeft:

   **Weg:** /libs/fd/cm/config/defaultApp/locale

   **Plaats van de Bedekking:** /apps/

   **de Types van Knoop van de Gelijke:** Gecontroleerd

1. Klik **OK**.
1. Klik **sparen allen**.
1. Klik het volgende dossier met de rechtermuisknop aan en selecteer **Exemplaar**:

   `/libs/fd/cm/config/defaultApp/locale/ACMExtensionsMessages.properties`

1. Klik met de rechtermuisknop op de **scène** omslag bij de volgende weg en selecteer **Deeg**:

   `/apps/fd/cm/config/defaultApp/locale/`

   Het bestand ACMExtensionsMessages.properties wordt gekopieerd naar de map locale.

1. Als u de labels van de zojuist toegevoegde aangepaste handeling/knop wilt lokaliseren, maakt u het bestand ACMExtensionsMessages.properties voor de desbetreffende landinstelling in `/apps/fd/cm/config/defaultApp/locale/` .

   Als u bijvoorbeeld de aangepaste handeling/knop wilt lokaliseren die in dit artikel is gemaakt, maakt u een bestand met de naam ACMExtensionsMessages_fr.properties met de volgende vermelding:

   `loc.letterInstance.letterreview.label=Revue De Lettre`

   Op dezelfde manier kunt u in dit bestand meer eigenschappen toevoegen, zoals voor knopinfo en stijl.

1. Klik **sparen allen**.

#### Start de bundel Adobe Asset Composer Building Block opnieuw {#restart-the-adobe-asset-composer-building-block-bundle}

Nadat u elke wijziging aan de serverzijde hebt aangebracht, start u de bundel Adobe Asset Composer Building Block opnieuw. In dit scenario worden de bestanden acmExtensionsConfig.xml en ACMExtensionsMessages.properties op de server bewerkt. Daarom moet de bundel Adobe Asset Composer Building Block opnieuw worden gestart.

>[!NOTE]
>
>Mogelijk moet u de browsercache wissen.

1. Ga naar `https://[host]:'port'/system/console/bundles` . Meld u indien nodig aan als beheerder.

1. Zoek de bundel Adobe Asset Composer Building Block. Start de bundel opnieuw: klik op Stoppen en klik vervolgens op Start.

   ![ het Blok van de Bouw van de Bouw van Activa van de Adobe ](assets/6_assetcomposerbuildingblockbundle.png)

Nadat u de bundel Adobe Asset Composer Building Block opnieuw hebt gestart, verschijnt de aangepaste knop in de Create Correspondence User Interface. U kunt een letter openen in de gebruikersinterface Correspondentie maken om een voorvertoning van de aangepaste knop weer te geven.

### Handeling toevoegen aan de knop {#add-action-handling-to-the-button}

De gebruikersinterface Correspondentie maken is standaard geïmplementeerd door ActionHandler in het bestand cm.domain.js op de volgende locatie:

/libs/fd/cm/ccr/gui/components/admin/clientlibs/ccr/js/cm.domain.js

Maak voor aangepaste afhandeling van handelingen een bedekking van het bestand cm.domain.js in de tak /apps van CRX.

De handeling/knop bij klikken op handeling/knop wordt uitgevoerd met logica voor:

* De nieuw toegevoegde actie zichtbaar/onzichtbaar maken: gedaan door de actionVisible() functie met voeten te treden.
* Nieuwe toegevoegde actie in- en uitschakelen: gedaan door de functie actionEnabled() te negeren.
* Werkelijke afhandeling van actie wanneer de gebruiker op de knop klikt: gedaan door de implementatie van de functie handleAction() te negeren.

1. Ga naar `https://'[server]:[port]'/[ContextPath]/crx/de` . Meld u indien nodig aan als beheerder.

1. Maak in de map apps een map met de naam `js` in de tak /apps van CRX met een structuur die lijkt op de volgende map:

   `/libs/fd/cm/ccr/gui/components/admin/clientlibs/ccrui/js`

   Gebruik de volgende stappen om de map te maken:

   1. Klik met de rechtermuisknop op de **js** omslag bij de volgende weg en selecteer **Knoop van de Bedekking**:

      `/libs/fd/cm/ccr/gui/components/admin/clientlibs/ccrui/js`

   1. Zorg ervoor dat het dialoogvenster Overlay-knooppunt de volgende waarden heeft:

      **Weg:** /libs/fd/cm/ccr/gui/components/admin/clientlibs/ccrui/js

      **Plaats van de Bedekking:** /apps/

      **de Types van Knoop van de Gelijke:** Gecontroleerd

   1. Klik **OK**.
   1. Klik **sparen allen**.

1. Maak in de map js een bestand met de naam ccrcustomization.js met de code voor het uitvoeren van handelingen met de knop door de volgende stappen uit te voeren:

   1. Klik met de rechtermuisknop op de **js** omslag bij de volgende weg en selecteer **creëren > Dossier** creëren:

      `/apps/fd/cm/ccr/gui/components/admin/clientlibs/ccrui/js`

      Geef het bestand een naam als ccrcustomization.js.

   1. Dubbelklik op het bestand ccrcustomization.js om het te openen in CRX.
   1. In het dossier, kleef de volgende code en klik **sparen allen**:

      ```javascript
      /* for adding and handling custom actions in Extensible Toolbar.
        * One instance of handler will be created for each action.
        * CM.domain.CCRCustomActionHandler is actionHandler class.
        */
      var CCRCustomActionHandler;
          CCRCustomActionHandler = CM.domain.CCRCustomActionHandler = new Class({
              className: 'CCRCustomActionHandler',
              extend: CCRDefaultActionHandler,
              construct : function(action,model){
              }
          });
          /**
           * Called when user user click an action
           * @param extraParams additional arguments that may be passed to handler (For future use)
           */
          CCRCustomActionHandler.prototype.handleAction = function(extraParams){
              if (this.action.name == CCRCustomActionHandler.SEND_FOR_REVIEW) {
                  var sendForReview = function(){
                      var serviceName = this.action.actionConfig["serviceName"];
                      var inputParams = {};
                      inputParams["dataXML"] = this.model.iccData.data;
                      inputParams["letterId"] = this.letterVO.id;
                      inputParams["letterName"] = this.letterVO.name;
                      inputParams["mailId"] = $('#email').val();
                      /*function to invoke the LivecyleService */
                      ServiceDelegate.callJSONService(this,"lc.icc.renderlib.serviceInvoker.json","invokeProcess",[serviceName,inputParams],this.onProcessInvokeComplete,this.onProcessInvokeFail);
                      $('#ccraction').modal("hide");
                  }
                  if($('#ccraction').length == 0){
                      /*For first click adding popup & setting letterName.*/
                      $("body").append(popUp);
                      $("input[id*='letterName']").val(this.letterVO.name);
                      $(document).on('click',"#submitLetter",$.proxy( sendForReview, this ));
                  }
                  $('#ccraction').modal("show");
              }
          };
          /**
           * Should the action be enabled in toolbar
           * @param extraParams additional arguements that may be passed to handler (For future use)
           * @return flag indicating whether the action should be enabled
           */
         CCRCustomActionHandler.prototype.actionEnabled = function(extraParams){
                  /*can be customized as per user requirement*/
                  return true;
          };
          /**
           * Should the action be visible in toolbar
           * @param extraParams additional arguments that may be passed to handler (For future use)
           * @return flag indicating whether the action should be enabled
           */
          CCRCustomActionHandler.prototype.actionVisible = function(extraParams){
              /*Check can be enabled for Non-Preview Mode.*/
              return true;
          };
          /*SuccessHandler*/
          CCRCustomActionHandler.prototype.onProcessInvokeComplete = function(response) {
              ErrorHandler.showSuccess("Letter Sent for Review");
          };
          /*FaultHandler*/
          CCRCustomActionHandler.prototype.onProcessInvokeFail = function(event) {
              ErrorHandler.showError(event.message);
          };
          CCRCustomActionHandler.SEND_FOR_REVIEW  = "Letter Review";
      /*For PopUp*/
          var popUp = '<div class="modal fade" id="ccraction" tabindex="-1" role="dialog" aria-hidden="true">'+
          '<div class="modal-dialog modal-sm">'+
              '<div class="modal-content">' +
                  '<div class="modal-header">'+
                      '<button type="button" class="close" data-dismiss="modal" aria-label="Close"><span aria-hidden="true">&times;</code></button>'+
                      '<h4 class="modal-title"> Send Review </h4>'+
                  '</div>'+
                  '<div class="modal-body">'+
                      '<form>'+
                          '<div class="form-group">'+
                              '<label class="control-label">Email Id</label>'+
                              '<input type="text" class="form-control" id="email">'+
                          '</div>'+
                          '<div class="form-group">'+
                              '<label  class="control-label">Letter Name</label>'+
                              '<input id="letterName" type="text" class="form-control" readonly>'+
                          '</div>'+
                          '<div class="form-group">'+
                              '<input id="letterData" type="text" class="form-control hide" readonly>'+
                          '</div>'+
                      '</form>'+
                  '</div>'+
                  '<div class="modal-footer">'+
                     '<button type="button" class="btn btn-default" data-dismiss="modal"> Cancel </button>'+
                     '<button type="button" class="btn btn-primary" id="submitLetter"> Submit </button>'+
                  '</div>'+
              '</div>'+
          '</div>'+
      '</div>';
      ```

### Het proces LiveCycle toevoegen om handeling in te schakelen <span class="acrolinxCursorMarker"></code>afhandeling {#add-the-livecycle-process-to-enable-action-span-class-acrolinxcursormarker-span-handling}

In dit scenario schakelt u de volgende componenten in, die deel uitmaken van het bestand components.zip in de bijlage:

* DSC-component jar (DSCSample.jar)
* Letter verzenden voor revisieproces LCA (SendLetterForReview.lca)

Download en decomprimeer het bestand components.zip om de bestanden DSCSample.jar en SendLetterForReview.lca op te halen. Gebruik deze bestanden volgens de onderstaande procedures.
[ krijgt Dossier ](assets/components.zip)

#### Vorm de Server van het LiveCycle om het proces LCA in werking te stellen {#configure-the-livecycle-server-to-run-the-lca-process}

>[!NOTE]
>
>Deze stap wordt vereist slechts als u op een opstelling OSGI bent en LC integratie wordt vereist voor het type van aanpassing u implementeert.

Het proces LCA loopt op de server van het LiveCycle en vereist het serveradres en de login geloofsbrieven.

1. Ga naar `https://'[server]:[port]'/system/console/configMgr` en meld u aan als beheerder.
1. Bepaal de plaats van de Configuratie van SDK van de Cliënt van het LiveCycle van de Adobe en klik **uitgeven** (geef pictogram uit). Het deelvenster Configuraties wordt geopend.

1. Ga de volgende details in en klik **sparen**:

   * **Url van de Server**: URL van de server LC waarvan verzendt voor de dienst van het Overzicht de code van de actiemanager gebruikt.
   * **Gebruikersnaam**: Admin gebruikersnaam van de server LC
   * **Wachtwoord**: Wachtwoord van Admin gebruikersnaam

   {de Configuratie van SDK van de Cliënt van het LiveCycle van 0} Adobe ](assets/3_clientsdkconfiguration.png)![

#### LiveCycle archiveren (LCA) installeren {#install-livecycle-archive-lca}

Het vereiste LiveCycle-proces dat het e-mailserviceproces inschakelt.

>[!NOTE]
>
>Als u wilt zien wat dit proces doet of een vergelijkbaar proces wilt maken, hebt u Workbench nodig.

1. Meld u bij `https:/[lc server]/:[lc port]/adminui` aan als Administrator bij LiveCycle® Server-adminui.

1. Navigeer aan **Huis > de Diensten > Toepassingen en de Diensten > het Beheer van de Toepassing**.

1. Als de toepassing SendLetterForReview al aanwezig is, sla de resterende stappen in deze procedure over, anders ga aan de volgende stappen verder.

   ![ SendLetterForReview toepassing in UI ](assets/12_applicationmanagementlc.png)

1. Klik **Invoer**.

1. Klik **kiezen Dossier** en selecteren SendLetterForReview.lca.

   ![ Uitgezochte SendLetterForReview.lca- dossier ](assets/14_sendletterforreview_lca.png)

1. Klik **Voorproef**.

1. Selecteer **Deploy activa aan runtime wanneer de invoer volledig** is.

1. Klik **Invoer**.

#### Het toevoegen van ServiceName aan de lijst van de Dienst van de Lijst van gewenste personen {#adding-servicename-to-the-allowlist-service-list}

Vermelding in de server van de Experience Manager de diensten van het LiveCycle u tot de server van de Experience Manager wilt toegang hebben.

1. Meld u aan als beheerder bij `https:/[host]:'port'/system/console/configMgr` .

1. Bepaal en klik {de Configuratie van SDK van de Cliënt van het LiveCycle van 0} Adobe **.** Het deelvenster Configuratie SDK-client van Adobe LiveCycle wordt weergegeven.
1. In de lijst van de Naam van de Dienst, klik + pictogram en voeg een serviceName **SendLetterForReview/SendLetterForReviewProcess** toe.

1. Klik **sparen**.

#### De e-mailservice configureren {#configure-the-email-service}

In dit scenario, voor het Beheer van de Correspondentie om een e-mail te kunnen verzenden, vorm de e-maildienst in de server van het LiveCycle.

1. Meld u bij `https:/[lc server]:[lc port]/adminui` aan met beheerdersreferenties naar de beheerder van de LiveCycle Server.

1. Navigeer aan **Huis > de Diensten > Toepassingen en de Diensten > het Beheer van de Dienst**.

1. Zoek en klik **EmailService**.

1. In **SMTP Gastheer**, vorm de e-maildienst.

1. Klik **sparen**.

#### De DSC-service configureren {#configure-the-dsc-service}

Als u de API voor correspondentiebeheer wilt gebruiken, downloadt u de DSCSample.jar (die in dit document is gekoppeld als onderdeel van components.zip) en uploadt u deze naar de server van het LiveCycle. Nadat het DSCSample.jar- dossier aan de server van het LiveCycle wordt geupload, gebruikt de server van de Experience Manager het DSCSample.jar- dossier om tot renderLetter API toegang te hebben.

Voor meer informatie, zie [ Verbindend AEM Forms met het LiveCycle van de Adobe ](/help/forms/using/aem-livecycle-connector.md).

1. Werk de URL van de server-URL van de Experience Manager in cmsa.properties in DSCSample.jar bij, die zich op de volgende locatie bevindt:

   DSCSample.jar\com\adobe\livecycle\cmsa.properties

1. Geef de volgende parameters op in het configuratiebestand:

   * **crx.serverUrl**=https:/host:port/ [ contextweg ]/[ AEM URL ]
   * **crx.username**= de gebruikersnaam van de Experience Manager
   * **crx.password**= het wachtwoord van de Experience Manager
   * **crx.appRoot**=/content/apps/cm

   >[!NOTE]
   >
   >Telkens als u om het even welke veranderingen bij de serverzijde aanbrengt, begin de Server van het LiveCycle opnieuw.

   Het bestand DSCSample.jar gebruikt de renderLetter-API. Voor meer Informatie over renderLetter API, zie [ Interface LetterRenderService ](https://www.adobe.io/experience-manager/reference-materials/6-5/forms/javadocs/index.html?com/adobe/icc/ddg/api/LetterRenderService.html).

#### DSC importeren in LiveCyle {#import-dsc-to-livecyle}

Het bestand DSCSample.jar gebruikt de renderLetter-API om een letter te renderen als PDF bytes van XML-gegevens die door DSC als invoer worden gegeven. Voor meer Informatie over renderLetter en andere APIs, zie [ de Brief geeft Dienst ](https://www.adobe.io/experience-manager/reference-materials/6-5/forms/javadocs/index.html?com/adobe/icc/ddg/api/LetterRenderService.html) terug.

1. Start Workbench en meld u aan.
1. Selecteer **Venster > toont Weergaven > Componenten**. De weergave Componenten wordt toegevoegd aan Workbench ES2.

1. Klik **Componenten** met de rechtermuisknop aan en selecteer **installeer Component**.

1. Selecteer het {**dossier 0} DSCSample.jar door dossierbrowser en klik** Open **.**
1. Klik **RenderWrapper** met de rechtermuisknop aan en selecteer **Component van het Begin**. Als de component start, verschijnt er een groene pijl naast de naam van de component.

## Ter controle verzenden {#send-letter-for-review}

Nadat u de actie en de knoop voor het verzenden van de brief voor overzicht hebt gevormd:

1. Wis de browsercache.

1. In Create Correspondence UI, klik **het Overzicht van de Brief** en specificeer e-mailidentiteitskaart van de recensent.

1. Klik **voorleggen**.

![ sendReview ](assets/sendreview.png)

De controleur ontvangt een e-mail van het systeem met de brief als PDF bijlage.
