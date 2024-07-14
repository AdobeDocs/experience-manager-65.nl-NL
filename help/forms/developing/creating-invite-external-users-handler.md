---
title: Een Uitnodigingshandler voor externe gebruikers maken
description: Leer hoe u een Invite External Users Handler maakt. Het laat de dienst van het Rights Management toe om externe gebruikers uit te nodigen om Rights Management gebruikers te worden.
role: Developer
exl-id: b0416716-dcc9-4f80-986a-b9660a7c8f6b
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,APIs & Integrations
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '1118'
ht-degree: 0%

---

# Een Uitnodigingshandler voor externe gebruikers maken {#create-invite-external-users-handler}

**de Steekproeven en de voorbeelden in dit document zijn slechts voor AEM Forms op milieu JEE.**

U kunt een Invite External Users Handler voor de service Rights Management maken. Een Invite External Users Handler stelt de service Rights Management in staat externe gebruikers uit te nodigen Rights Management gebruikers te worden. Nadat een gebruiker een gebruiker van het Rights Management wordt, kan de gebruiker taken, zoals het openen van een beleid-beschermd document van de PDF uitvoeren. Nadat de Invite External Users Handler wordt opgesteld aan AEM Forms, kunt u beleidsconsole gebruiken om met het in wisselwerking te staan.

>[!NOTE]
>
>Een Invite External Users Handler is een AEM Forms-component. Voordat u een Invite External Users Handler maakt, wordt u aangeraden vertrouwd te raken met het maken van componenten.

**Samenvatting van stappen**

Als u een Invite External Users Handler wilt ontwikkelen, moet u de volgende stappen uitvoeren:

1. Stel uw ontwikkelomgeving in.
1. Definieer de implementatie Invite External Users Handler.
1. Definieer het XML-bestand van de component.
1. Implementeer de handler Externe gebruikers uitnodigen.
1. Test de Invite External Users Handler.

## De ontwikkelomgeving instellen {#setting-up-development-environment}

Als u uw ontwikkelomgeving wilt instellen, moet u een Java-project maken, zoals een Eclipse-project. De ondersteunde versie van Eclipse is `3.2.1` of hoger.

De Rights Management-SPI vereist dat het `edc-server-spi.jar` -bestand wordt ingesteld in het klassenpad van uw project. Als u niet naar dit JAR-bestand verwijst, kunt u de Rights Management-SPI niet gebruiken in uw Java-project. Dit JAR-bestand wordt samen met de AEM Forms SDK in de map `[install directory]\Adobe\Adobe_Experience_Manager_forms\sdk\spi` geïnstalleerd.

Naast het toevoegen van het `edc-server-spi.jar` dossier aan de klassenweg van uw project, moet u ook de JAR dossiers toevoegen die worden vereist om de Dienst API van het Rights Management te gebruiken. Deze bestanden zijn nodig om de Rights Management Service API in de Uitnodiging External Users Handler te gebruiken.

## De implementatie van de uitnodigen van externe gebruikers definiëren {#define-invite-external-users-handler}

Als u een uitnodigingshandler voor externe gebruikers wilt ontwikkelen, moet u een Java-klasse maken die de `com.adobe.edc.server.spi.ersp.InvitedUserProvider` -interface implementeert. Deze klasse bevat een methode genoemd `invitedUser`, die de dienst van het Rights Management aanhaalt wanneer de e-mailadressen gebruikend **worden voorgelegd voeg Uitgenodigde Gebruikers** pagina toegankelijk door beleidsconsole toe.

De `invitedUser` methode keurt een `java.util.List` instantie goed, die koord-getypte e-mailadressen bevat die van **worden voorgelegd voeg Uitgenodigde Gebruikers** pagina toe. De methode `invitedUser` retourneert een array met `InvitedUserProviderResult` -objecten. Dit is doorgaans een toewijzing van e-mailadressen aan Gebruikersobjecten (retourneren niet null).

>[!NOTE]
>
>In deze sectie wordt niet alleen getoond hoe u een uitnodigen voor externe gebruikers-handler kunt maken, maar ook de AEM Forms API gebruikt.

De implementatie van de uitnodigen externe gebruikers-handler bevat een door de gebruiker gedefinieerde methode met de naam `createLocalPrincipalAccount` . Deze methode accepteert een tekenreekswaarde die een e-mailadres opgeeft als parameterwaarde. De methode `createLocalPrincipalAccount` gaat ervan uit dat een lokaal domein met de naam `EDC_EXTERNAL_REGISTERED` al bestaat. U kunt deze domeinnaam om het even wat vormen u wenst; nochtans, voor een productietoepassing, kunt u met een ondernemingsdomein willen integreren.

De methode `createUsers` doorloopt elk e-mailadres en maakt een overeenkomstig object User (een lokale gebruiker in het `EDC_EXTERNAL_REGISTERED` -domein). Tot slot wordt de methode `doEmails` aangeroepen. Deze methode wordt opzettelijk als een stoofpot in het monster gelaten. In een productie-implementatie zou deze toepassingslogica bevatten om uitnodigings-e-mailberichten te verzenden naar de nieuwe gebruikers. Het wordt in de steekproef verlaten om de stroom van de toepassingslogica van een echte toepassing aan te tonen.

### De implementatie van de uitnodigen van externe gebruikers definiëren {#user-handler-implementation}

De volgende uitnodigingsimplementatie van de externe gebruikersmanager keurt e-mailadressen goed die van Add Uitgenodigde pagina van Gebruikers toegankelijk door beleidsconsole worden voorgelegd.

```as3
package com.adobe.livecycle.samples.inviteexternalusers.provider; 
 
import com.adobe.edc.server.spi.ersp.*; 
import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
import com.adobe.idp.um.api.*; 
import com.adobe.idp.um.api.infomodel.*; 
import com.adobe.idp.um.api.impl.UMBaseLibrary; 
import com.adobe.livecycle.usermanager.client.DirectoryManagerServiceClient; 
 
import java.util.ArrayList; 
import java.util.Iterator; 
import java.util.List; 
 
public class InviteExternalUsersSample implements InvitedUserProvider 
{ 
       private ServiceClientFactory _factory = null; 
 
       private User createLocalPrincipalAccount(String email_address) throws Exception 
       { 
    String ret = null; 
 
    //  Assume the local domain already exists! 
    String domain = "EDC_EXTERNAL_REGISTERED"; 
         
    List aliases = new ArrayList(); 
    aliases.add( email_address ); 
         
    User local_user = UMBaseLibrary.createUser( email_address, domain, email_address ); 
    local_user.setCommonName( email_address ); 
    local_user.setEmail( email_address ); 
    local_user.setEmailAliases( aliases ); 
         
    //  You may wish to disable the local user until, for example, his registration is processed by a confirmation link 
    //local_user.setDisabled( true ); 
 
    DirectoryManager directory_manager = new DirectoryManagerServiceClient( _factory ); 
    String ret_oid = directory_manager.createLocalUser( local_user, null ); 
     
    if( ret_oid == null ) 
    { 
        throw new Exception( "FAILED TO CREATE PRINCIPAL FOR EMAIL ADDRESS: " + email_address ); 
    } 
 
    return local_user; 
       } 
 
       protected User[] createUsers( List emails ) throws Exception 
       { 
    ArrayList ret_users = new ArrayList(); 
 
    _factory = ServiceClientFactory.createInstance(); 
 
    Iterator iter = emails.iterator(); 
 
    while( iter.hasNext() ) 
    { 
        String current_email = (String)iter.next(); 
 
        ret_users.add( createLocalPrincipalAccount( current_email ) ); 
    } 
 
    return (User[])ret_users.toArray( new User[0] ); 
       } 
 
       protected void doInvitations(List emails) 
       { 
    //  Here you may choose to send the users who were created an invitation email 
    //  This step is completely optional, depending on your requirements.   
       } 
 
       public InvitedUserProviderResult[] invitedUser(List emails) 
       { 
    //  This sample demonstrates the workflow for inviting a user via email 
 
    try 
    { 
 
        User[] principals = createUsers(emails); 
 
        InvitedUserProviderResult[] result = new InvitedUserProviderResult[principals.length]; 
        for( int i = 0; i < principals.length; i++ ) 
        { 
        result[i] = new InvitedUserProviderResult(); 
 
        result[i].setEmail( (String)emails.get( i ) ); 
        result[i].setUser( principals[i] ); 
        } 
 
        doInvitations(emails); 
 
        System.out.println( "SUCCESSFULLY INVITED " + result.length + " USERS" ); 
 
        return result; 
 
    } 
    catch( Exception e ) 
    { 
        System.out.println( "FAILED TO INVITE USERS FOR INVITE USERS SAMPLE" ); 
        e.printStackTrace(); 
 
        return new InvitedUserProviderResult[0]; 
    } 
       } 
}
 
```

>[!NOTE]
>
>Deze Java-klasse wordt opgeslagen als een JAVA-bestand met de naam InviteExternalUsersSample.java.

## Het XML-bestand van de component definiëren voor de machtigingshandler {#define-component-xml-authorization-handler}

Bepaal een dossier van componentXML om de uitnodigings externe gebruikersmanagercomponent op te stellen. Er bestaat een XML-componentbestand voor elke component en er worden metagegevens over de component weergegeven.

Het volgende `component.xml` -bestand wordt gebruikt voor de uitnodigen van externe gebruikers-handler. De servicenaam is `InviteExternalUsersSample` en de bewerking die deze service beschikbaar stelt, krijgt de naam `invitedUser` . De invoerparameter is een `java.util.List` -instantie en de uitvoerwaarde is een array van `com.adobe.edc.server.spi.esrp.InvitedUserProviderResult` -instanties.

### Het XML-bestand van de component definiëren voor de handler voor externe gebruikers uitnodigen {#component-xml-invite-external-users-handler}

```as3
<component xmlns="https://adobe.com/idp/dsc/component/document"> 
<component-id>com.adobe.livecycle.samples.inviteexternalusers</component-id> 
<version>1.0</version> 
<bootstrap-class>com.adobe.livecycle.samples.inviteexternalusers.provider.BootstrapImpl</bootstrap-class> 
<descriptor-class>com.adobe.idp.dsc.component.impl.DefaultPOJODescriptorImpl</descriptor-class> 
<services> 
<service name="InviteExternalUsersSample"> 
<specifications> 
<specification spec-id="com.adobe.edc.server.spi.ersp.InvitedUserProvider"/> 
</specifications> 
<specification-version>1.0</specification-version> 
<implementation-class>com.adobe.livecycle.samples.inviteexternalusers.provider.InviteExternalUsersSample</implementation-class> 
<auto-deploy category-id="Samples" service-id="InviteExternalUsersSample" major-version="1" minor-version="0"/> 
<operations> 
<operation name="invitedUser"> 
<input-parameter name="input" type="java.util.List" required="true"/> 
<output-parameter name="result" type="com.adobe.edc.server.spi.esrp.InvitedUserProviderResult[]"/> 
</operation> 
</operations> 
</service> 
</services> 
</component> 
```

## De uitnodigen van externe gebruikers-handler in een pakket plaatsen {#packaging-invite-external-users-handler}

Als u de uitnodigen van externe gebruikers-handler wilt implementeren in AEM Forms, moet u uw Java-project in een JAR-bestand plaatsen. Zorg ervoor dat de externe JAR-bestanden waarvan de zakelijke logica van de uitnodigen voor externe gebruikers afhankelijk is, zoals de `edc-server-spi.jar` - en `adobe-rightsmanagement-client.jar` -bestanden, ook in het JAR-bestand worden opgenomen. Het XML-bestand van de component moet ook aanwezig zijn. Het `component.xml` -bestand en externe JAR-bestanden moeten zich in de hoofdmap van het JAR-bestand bevinden.

>[!NOTE]
>
>In de onderstaande afbeelding wordt een `BootstrapImpl` -klasse weergegeven. In deze sectie wordt niet besproken hoe u een `BootstrapImpl` -klasse kunt maken.

In de volgende afbeelding ziet u de inhoud van het Java-project die is verpakt in het JAR-bestand van de uitnodigingshandler voor externe gebruikers.

![ nodigt gebruikers ](assets/ci_ci_InviteUsers.png) uit

A. Externe JAR-bestanden vereist door component B. JAVA-bestand

Plaats de uitnodigen van externe gebruikers-handler in een JAR-bestand. In het vorige diagram worden .JAVA-bestanden weergegeven. Nadat de bestanden in een JAR-bestand zijn verpakt, moeten ook de bijbehorende .CLASS-bestanden worden opgegeven. Zonder de .CLASS dossiers, werkt de vergunningsmanager niet.

>[!NOTE]
>
>Nadat u de externe machtigingshandler in een JAR-bestand hebt verpakt, kunt u de component implementeren in AEM Forms. Slechts één nodigt externe gebruikersmanager uit kan in een bepaalde tijd worden opgesteld.

>[!NOTE]
>
>U kunt een component programmatically ook opstellen.

## Testen van de Uitnodigings externe gebruikersmanager {#testing-invite-external-users-handler}

Om de uitnodigings externe gebruikersmanager te testen, kunt u externe gebruikers toevoegen om uit te nodigen door beleidsconsole te gebruiken.

Om externe gebruikers toe te voegen om uit te nodigen gebruikend beleidsconsole:

1. Implementeer het JAR-bestand van de uitnodigen van externe gebruikers met Workbench.
1. Start de toepassingsserver opnieuw.

   >[!NOTE]
   >
   > Het wordt aanbevolen de SDK opnieuw te starten met de opdracht &#39;Ctrl + C&#39;. Het opnieuw opstarten van de AEM SDK met behulp van alternatieve methoden, bijvoorbeeld het stoppen van Java-processen, kan leiden tot inconsistenties in de AEM ontwikkelomgeving.

1. Log in bij de beheerconsole.
1. Klik op **[!UICONTROL Services]** > **[!UICONTROL Rights Management]** > **[!UICONTROL Configuration]** > Uitgenodigd **[!UICONTROL User Registration]** .
1. Schakel het selectievakje **[!UICONTROL Enable invited user registration]** in om uitgenodigde gebruikers te registreren. Klik onder **[!UICONTROL Use Built-in registration system]** op **[!UICONTROL No]** . Sla uw instellingen op.
1. Klik op de startpagina van de beheerconsole op **[!UICONTROL Settings]** > **[!UICONTROL User Management]** > **[!UICONTROL Domain Management]** .
1. Klik op **[!UICONTROL New Local Domain]**. Maak op de volgende pagina een domein met de naam en de id-waarde `EDC_EXTERNAL_REGISTERED` . Sla uw wijzigingen op.
1. Klik op de startpagina van de beheerconsole op **[!UICONTROL Services]** > **[!UICONTROL Rights Management]** > **[!UICONTROL Invited and Local Users]** . De pagina **[!UICONTROL Add Invited User]** wordt weergegeven.
1. Voer e-mailadressen in (omdat de huidige uitnodigen van externe gebruikers geen e-mailberichten verzendt, hoeft de geadresseerde e-mail niet geldig te zijn). Klik op **[!UICONTROL OK]**. De gebruikers worden uitgenodigd aan het systeem.
1. Klik op de startpagina van de beheerconsole op **[!UICONTROL Settings]** > **[!UICONTROL User Management]** > **[!UICONTROL Users and Groups]** .
1. Voer in het veld **[!UICONTROL Find]** een e-mailadres in dat u hebt opgegeven. Klik op **[!UICONTROL Find]**. De gebruiker die u hebt uitgenodigd, wordt als een gebruiker weergegeven in het lokale `EDC_EXTERNAL_REGISTERED` domein.

>[!NOTE]
>
>De uitnodigen externe gebruikers-handler mislukt als de component is gestopt of verwijderd.
