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

1. Ga naar `https://'[server]:[port]'/[ContextPath]/crx/de` en aanmelden als beheerder.
1. Maak in de map Apps een map met de naam `defaultApp` met pad/structuur vergelijkbaar met de map defaultApp (in configuratiemap). Gebruik de volgende stappen om de map te maken:

   1. Klik met de rechtermuisknop op de knop **defaultApp** map op het volgende pad en selecteer **Overlayknooppunt**:

      /libs/fd/cm/config/defaultApp/

      ![Overlay-knooppunt](assets/1_defaultapp.png)

   1. Zorg ervoor dat het dialoogvenster Overlay-knooppunt de volgende waarden heeft:

      **Pad:** /libs/fd/cm/config/defaultApp/

      **Locatie bedekking:** /apps/

      **Identieke knooppunttypen:** Ingeschakeld

      ![Overlay-knooppunt](assets/2_defaultappoverlaynode.png)

   1. Klikken **OK**.
   1. Klikken **Alles opslaan**.

1. Maak een kopie van het bestand acmExtensionsConfig.xml (bestaat onder de tak /libs) onder de tak /apps.

   1. Ga naar /libs/fd/cm/config/defaultApp/acmExtensionsConfig.xml

   1. Klik met de rechtermuisknop op het bestand acmExtensionsConfig.xml en selecteer **Kopiëren**.

      ![acmExtensionsConfig.xml kopiëren](assets/3_acmextensionsconfig_xml_copy.png)

   1. Klik met de rechtermuisknop op de knop **defaultApp** map op &quot;/apps/fd/cm/config/defaultApp/&quot; en selecteer **Plakken**.
   1. Klikken **Alles opslaan**.

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

   ![customAction-tag](assets/5_acmextensionsconfig_xml.png)

   De tag modelExtension heeft een set onderliggende tags van customAction die de handeling, machtigingen en weergave van de actieknop configureren. Hieronder volgt een lijst met aangepasteAction-configuratietags:

   | **Naam** | **Beschrijving** |
   |---|---|
   | name | De alfanumerieke naam voor de handeling die moet worden uitgevoerd. Waarde van deze tag is vereist, moet uniek zijn (binnen de tag modelExtension) en moet beginnen met een alfabet. |
   | label | Het label dat op de actieknop moet worden weergegeven |
   | knopinfo | Knopinfo-tekst van de knop, die wordt weergegeven wanneer de gebruiker de muisaanwijzer op de knop plaatst. |
   | styleName | Naam van de aangepaste stijl die op de actieknop wordt toegepast. |
   | permissionName | De overeenkomstige actie wordt getoond slechts als de gebruiker de toestemming heeft die door permissionName wordt gespecificeerd. Wanneer u permissionName opgeeft als `forms-users`, krijgen alle gebruikers toegang tot deze optie. |
   | actionHandler | Volledig gekwalificeerde naam van de klasse ActionHandler die wordt aangeroepen wanneer de gebruiker op de knop klikt. |

   Naast de bovenstaande parameters, kunnen er extra configuraties verbonden aan een customAction zijn. Deze extra configuraties worden ter beschikking gesteld aan de manager door het voorwerp CustomAction.

   | **Naam** | **Beschrijving** |
   |---|---|
   | serviceName | Als een customAction een kindmarkering met name serviceName bevat, dan wanneer het klikken van de relevante knoop/de verbinding, wordt een proces geroepen met de naam die door serviceName markering wordt vertegenwoordigd. Zorg ervoor dat dit proces dezelfde handtekening heeft als het PostProcess Letter. Voeg het voorvoegsel &quot;Forms Workflow ->&quot; toe aan de servicenaam. |
   | Parameters die het voorvoegsel cm_ bevatten in tagnaam | Als een customAction een kindmarkeringen bevat die met naam cm_ beginnen, dan in postproces (of het Proces van de Post van de Brief of het speciale proces door de markering serviceName wordt vertegenwoordigd) zijn deze parameters beschikbaar in de inputXML code onder de relevante markering met cm_ prefix verwijderd. |
   | actionName | Wanneer een postproces aan een klik toe te schrijven is, bevat voorgelegde XML een speciale markering met naam onder de markering met de naam van de gebruikersactie. |

1. Klikken **Alles opslaan**.

#### Een map met eigenschappen voor een landinstelling maken in de tak /apps {#create-a-locale-folder-with-properties-file-in-the-apps-branch}

Het bestand ACMExtensionsMessages.properties bevat labels en knopinfo-berichten van verschillende velden in de gebruikersinterface Correspondentie maken. Maak een kopie van dit bestand in de tak /apps om de aangepaste handelingen/knoppen te laten werken.

1. Klik met de rechtermuisknop op de knop **landinstelling** map op het volgende pad en selecteer **Overlayknooppunt**:

   /libs/fd/cm/config/defaultApp/locale

1. Zorg ervoor dat het dialoogvenster Overlay-knooppunt de volgende waarden heeft:

   **Pad:** /libs/fd/cm/config/defaultApp/locale

   **Locatie bedekking:** /apps/

   **Identieke knooppunttypen:** Ingeschakeld

1. Klikken **OK**.
1. Klikken **Alles opslaan**.
1. Klik met de rechtermuisknop op het volgende bestand en selecteer **Kopiëren**:

   `/libs/fd/cm/config/defaultApp/locale/ACMExtensionsMessages.properties`

1. Klik met de rechtermuisknop op de knop **landinstelling** map op het volgende pad en selecteer **Plakken**:

   `/apps/fd/cm/config/defaultApp/locale/`

   Het bestand ACMExtensionsMessages.properties wordt gekopieerd naar de map locale.

1. Als u de labels van de zojuist toegevoegde aangepaste handeling/knop wilt lokaliseren, maakt u het bestand ACMExtensionsMessages.properties voor de relevante landinstelling in `/apps/fd/cm/config/defaultApp/locale/`.

   Als u bijvoorbeeld de aangepaste handeling/knop wilt lokaliseren die in dit artikel is gemaakt, maakt u een bestand met de naam ACMExtensionsMessages_fr.properties met de volgende vermelding:

   `loc.letterInstance.letterreview.label=Revue De Lettre`

   Op dezelfde manier kunt u in dit bestand meer eigenschappen toevoegen, zoals voor knopinfo en stijl.

1. Klikken **Alles opslaan**.

#### Start de bundel Adobe Asset Composer Building Block opnieuw {#restart-the-adobe-asset-composer-building-block-bundle}

Nadat u elke wijziging aan de serverzijde hebt aangebracht, start u de bundel Adobe Asset Composer Building Block opnieuw. In dit scenario worden de bestanden acmExtensionsConfig.xml en ACMExtensionsMessages.properties op de server bewerkt. Daarom moet de bundel Adobe Asset Composer Building Block opnieuw worden gestart.

>[!NOTE]
>
>Mogelijk moet u de browsercache wissen.

1. Ga naar `https://[host]:'port'/system/console/bundles`. Meld u indien nodig aan als beheerder.

1. Zoek de bundel Adobe Asset Composer Building Block. Start de bundel opnieuw: klik op Stoppen en klik vervolgens op Start.

   ![Adobe Asset Composer Building Block](assets/6_assetcomposerbuildingblockbundle.png)

Nadat u de bundel Adobe Asset Composer Building Block opnieuw hebt gestart, verschijnt de aangepaste knop in de Create Correspondence User Interface. U kunt een letter openen in de gebruikersinterface Correspondentie maken om een voorvertoning van de aangepaste knop weer te geven.

### Handeling toevoegen aan de knop {#add-action-handling-to-the-button}

De gebruikersinterface Correspondentie maken is standaard geïmplementeerd door ActionHandler in het bestand cm.domain.js op de volgende locatie:

/libs/fd/cm/ccr/gui/components/admin/clientlibs/ccr/js/cm.domain.js

Voor aangepaste handelingen-afhandeling maakt u een bedekking van het bestand cm.domain.js in de /apps-vertakking van CRX.

De handeling/knop bij klikken op handeling/knop wordt uitgevoerd met logica voor:

* De nieuw toegevoegde actie zichtbaar/onzichtbaar maken: gedaan door de actionVisible() functie met voeten te treden.
* Nieuwe toegevoegde actie in- en uitschakelen: gedaan door de functie actionEnabled() te negeren.
* Werkelijke afhandeling van actie wanneer de gebruiker op de knop klikt: gedaan door de implementatie van de functie handleAction() te negeren.

1. Ga naar `https://'[server]:[port]'/[ContextPath]/crx/de`. Meld u indien nodig aan als beheerder.

1. Maak in de map Apps een map met de naam `js` in de /apps tak van CRX met structuur gelijkend op de volgende omslag:

   `/libs/fd/cm/ccr/gui/components/admin/clientlibs/ccrui/js`

   Gebruik de volgende stappen om de map te maken:

   1. Klik met de rechtermuisknop op de knop **js** map op het volgende pad en selecteer **Overlayknooppunt**:

      `/libs/fd/cm/ccr/gui/components/admin/clientlibs/ccrui/js`

   1. Zorg ervoor dat het dialoogvenster Overlay-knooppunt de volgende waarden heeft:

      **Pad:** /libs/fd/cm/ccr/gui/components/admin/clientlibs/ccrui/js

      **Locatie bedekking:** /apps/

      **Identieke knooppunttypen:** Ingeschakeld

   1. Klikken **OK**.
   1. Klikken **Alles opslaan**.

1. Maak in de map js een bestand met de naam ccrcustomization.js met de code voor het uitvoeren van handelingen met de knop door de volgende stappen uit te voeren:

   1. Klik met de rechtermuisknop op de knop **js** map op het volgende pad en selecteer **Maken > Bestand maken**:

      `/apps/fd/cm/ccr/gui/components/admin/clientlibs/ccrui/js`

      Geef het bestand een naam als ccrcustomization.js.

   1. Dubbelklik op het bestand ccrcustomization.js om dit te openen in CRX.
   1. Plak de volgende code in het bestand en klik op **Alles opslaan**:

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

### Voeg het proces van het LiveCycle toe om actie toe te laten <span class="acrolinxCursorMarker"></code>afhandeling {#add-the-livecycle-process-to-enable-action-span-class-acrolinxcursormarker-span-handling}

In dit scenario schakelt u de volgende componenten in, die deel uitmaken van het bestand components.zip in de bijlage:

* DSC-component jar (DSCSample.jar)
* Letter verzenden voor revisieproces LCA (SendLetterForReview.lca)

Download en decomprimeer het bestand components.zip om de bestanden DSCSample.jar en SendLetterForReview.lca op te halen. Gebruik deze bestanden volgens de onderstaande procedures.
[Bestand ophalen](assets/components.zip)

#### Vorm de Server van het LiveCycle om het proces LCA in werking te stellen {#configure-the-livecycle-server-to-run-the-lca-process}

>[!NOTE]
>
>Deze stap wordt vereist slechts als u op een opstelling OSGI bent en LC integratie wordt vereist voor het type van aanpassing u implementeert.

Het proces LCA loopt op de server van het LiveCycle en vereist het serveradres en de login geloofsbrieven.

1. Ga naar `https://'[server]:[port]'/system/console/configMgr` en aanmelden als beheerder.
1. Zoek Adobe LiveCycle Client SDK Configuration en klik op **Bewerken** (pictogram Bewerken). Het deelvenster Configuraties wordt geopend.

1. Voer de volgende gegevens in en klik op **Opslaan**:

   * **Server-URL**: URL van de server LC waarvan verzendt voor de dienst van het Overzicht de code van de actiemanager gebruikt.
   * **Gebruikersnaam**: Admin-gebruikersnaam van de LC-server
   * **Wachtwoord**: Wachtwoord voor de gebruikersnaam Admin

   ![Adobe LiveCycle client SDK Configuration](assets/3_clientsdkconfiguration.png)

#### LiveCycle archiveren (LCA) installeren {#install-livecycle-archive-lca}

Het vereiste LiveCycle-proces dat het e-mailserviceproces inschakelt.

>[!NOTE]
>
>Als u wilt zien wat dit proces doet of een vergelijkbaar proces wilt maken, hebt u Workbench nodig.

1. Meld u aan als beheerder bij Server-adminui van LiveCycle® op `https:/[lc server]/:[lc port]/adminui`.

1. Navigeren naar **Home > Services > Toepassingen en services > Toepassingsbeheer**.

1. Als de toepassing SendLetterForReview al aanwezig is, sla de resterende stappen in deze procedure over, anders ga aan de volgende stappen verder.

   ![SendLetterForReview-toepassing in de gebruikersinterface](assets/12_applicationmanagementlc.png)

1. Klikken **Importeren**.

1. Klikken **Bestand kiezen** en selecteer SendLetterForReview.lca.

   ![Selecteer het bestand SendLetterForReview.lca](assets/14_sendletterforreview_lca.png)

1. Klikken **Voorvertoning**.

1. Selecteren **Elementen tijdens het importeren naar runtime implementeren**.

1. Klikken **Importeren**.

#### Het toevoegen van ServiceName aan de lijst van de Dienst van de Lijst van gewenste personen {#adding-servicename-to-the-allowlist-service-list}

Vermelding in de server van de Experience Manager de diensten van het LiveCycle u tot de server van de Experience Manager wilt toegang hebben.

1. Aanmelden als beheerder `https:/[host]:'port'/system/console/configMgr`.

1. Zoeken en klikken **Adobe LiveCycle client SDK Configuration**. Het deelvenster Configuratie SDK-client van Adobe LiveCycle wordt weergegeven.
1. In de lijst van de Naam van de Dienst, klik + pictogram en voeg een serviceName toe **SendLetterForReview/SendLetterForReviewProcess**.

1. Klikken **Opslaan**.

#### De e-mailservice configureren {#configure-the-email-service}

In dit scenario, voor het Beheer van de Correspondentie om een e-mail te kunnen verzenden, vorm de e-maildienst in de server van het LiveCycle.

1. Meld u aan met beheerdersreferenties naar de beheerder van de LiveCycle-server op `https:/[lc server]:[lc port]/adminui`.

1. Navigeren naar **Home > Services > Toepassingen en services > Servicebeheer**.

1. Zoeken en klikken **EmailService**.

1. In **SMTP-host**, configureert u de e-mailservice.

1. Klikken **Opslaan**.

#### De DSC-service configureren {#configure-the-dsc-service}

Als u de API voor correspondentiebeheer wilt gebruiken, downloadt u de DSCSample.jar (die in dit document is gekoppeld als onderdeel van components.zip) en uploadt u deze naar de server van het LiveCycle. Nadat het DSCSample.jar- dossier aan de server van het LiveCycle wordt geupload, gebruikt de server van de Experience Manager het DSCSample.jar- dossier om tot renderLetter API toegang te hebben.

Zie voor meer informatie [AEM Forms verbinden met Adobe LiveCycle](/help/forms/using/aem-livecycle-connector.md).

1. Werk de URL van de server-URL van de Experience Manager in cmsa.properties in DSCSample.jar bij, die zich op de volgende locatie bevindt:

   DSCSample.jar\com\adobe\livecycle\cmsa.properties

1. Geef de volgende parameters op in het configuratiebestand:

   * **crx.serverUrl**=https:/host:port/[contextpad]/[URL AEM]
   * **crx.username**= gebruikersnaam Experience Manager
   * **crx.password**= wachtwoord Experience Manager
   * **crx.appRoot**=/content/apps/cm

   >[!NOTE]
   >
   >Telkens als u om het even welke veranderingen bij de serverzijde aanbrengt, begin de Server van het LiveCycle opnieuw.

   Het bestand DSCSample.jar gebruikt de renderLetter-API. Zie voor meer informatie over de renderLetter-API [Interface LetterRenderService](https://www.adobe.io/experience-manager/reference-materials/6-5/forms/javadocs/index.html?com/adobe/icc/ddg/api/LetterRenderService.html).

#### DSC importeren in LiveCyle {#import-dsc-to-livecyle}

Het bestand DSCSample.jar gebruikt de renderLetter-API om een letter te renderen als PDF bytes van XML-gegevens die door DSC als invoer worden gegeven. Voor meer informatie over renderLetter en andere APIs, zie [Letter Render-service](https://www.adobe.io/experience-manager/reference-materials/6-5/forms/javadocs/index.html?com/adobe/icc/ddg/api/LetterRenderService.html).

1. Start Workbench en meld u aan.
1. Selecteren **Venster > Weergaven tonen > Componenten**. De weergave Componenten wordt toegevoegd aan Workbench ES2.

1. Klikken met rechtermuisknop **Componenten** en selecteert u **Component installeren**.

1. Selecteer de **DSCSample.jar** bestand via de bestandsbrowser en klik op **Openen**.
1. Klikken met rechtermuisknop **RenderWrapper** en selecteert u **Component starten**. Als de component start, verschijnt er een groene pijl naast de naam van de component.

## Ter controle verzenden {#send-letter-for-review}

Nadat u de actie en de knoop voor het verzenden van de brief voor overzicht hebt gevormd:

1. Wis de browsercache.

1. Klik in de interface Correspondentie maken op **Letter Review** en geef de e-mailid van de controleur op.

1. Klikken **Verzenden**.

![sendreview](assets/sendreview.png)

De controleur ontvangt een e-mail van het systeem met de brief als PDF bijlage.
