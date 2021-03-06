---
title: Een Uitnodigingshandler voor externe gebruikers maken
description: Een Uitnodigingshandler voor externe gebruikers maken
role: Developer
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '1075'
ht-degree: 0%

---


# Externe gebruikershandler {#create-invite-external-users-handler} uitnodigen

**Voorbeelden en voorbeelden in dit document gelden alleen voor AEM Forms in JEE-omgeving.**

U kunt een Invite External Users Handler voor de service Rights Management maken. Een Invite External Users Handler stelt de service Rights Management in staat externe gebruikers uit te nodigen Rights Management gebruikers te worden. Nadat een gebruiker een gebruiker van het Rights Management wordt, kan de gebruiker taken uitvoeren, zoals het openen van een beleid-beschermd PDF document. Nadat de Invite External Users Handler wordt opgesteld aan AEM Forms, kunt u beleidsconsole gebruiken om met het in wisselwerking te staan.

>[!NOTE]
>
>Een Invite External Users Handler is een AEM Forms-component. Voordat u een Invite External Users Handler maakt, wordt u aangeraden vertrouwd te raken met het maken van componenten.

**Overzicht van de stappen**

Als u een Invite External Users Handler wilt ontwikkelen, moet u de volgende stappen uitvoeren:

1. Stel uw ontwikkelomgeving in.
1. Definieer de implementatie Invite External Users Handler.
1. Definieer het XML-bestand van de component.
1. Implementeer de handler Externe gebruikers uitnodigen.
1. Test de Invite External Users Handler.

## De ontwikkelomgeving instellen {#setting-up-development-environment}

Als u uw ontwikkelomgeving wilt instellen, moet u een nieuw Java-project maken, zoals een Eclipse-project. De ondersteunde versie van Eclipse is `3.2.1` of hoger.

De Rights Management SPI vereist dat het `edc-server-spi.jar` dossier in de klassenweg van uw project wordt geplaatst. Als u niet naar dit JAR-bestand verwijst, kunt u de Rights Management-SPI niet gebruiken in uw Java-project. Dit JAR-bestand wordt samen met de AEM Forms SDK ge??nstalleerd in de map `[install directory]\Adobe\Adobe_Experience_Manager_forms\sdk\spi`.

Naast het toevoegen van het `edc-server-spi.jar` dossier aan de klassenweg van uw project, moet u ook de JAR dossiers toevoegen die worden vereist om de Dienst API van het Rights Management te gebruiken. Deze bestanden zijn nodig om de Rights Management Service API in de Uitnodiging External Users Handler te gebruiken.

## Implementatie {#define-invite-external-users-handler} van de uitnodigen externe gebruikers-handler defini??ren

Als u een uitnodigingshandler voor externe gebruikers wilt ontwikkelen, moet u een Java-klasse maken die de `com.adobe.edc.server.spi.ersp.InvitedUserProvider`-interface implementeert. Deze klasse bevat een methode met de naam `invitedUser`, die de service Rights Management aanroept wanneer e-mailadressen worden verzonden met de pagina **Uitgenodigde gebruikers toevoegen** die toegankelijk is via de beheerconsole.

De `invitedUser` methode keurt een `java.util.List` instantie goed, die koord-getypte e-mailadressen bevat die van **Add Uitgenodigde Gebruikers** pagina worden voorgelegd. De methode `invitedUser` retourneert een array van `InvitedUserProviderResult`-objecten. Dit is doorgaans een toewijzing van e-mailadressen aan gebruikersobjecten (retourneert niet null).

>[!NOTE]
>
>In deze sectie wordt niet alleen getoond hoe u een uitnodigen voor externe gebruikers-handler kunt maken, maar ook de AEM Forms API gebruikt.

De implementatie van de uitnodigen externe gebruikers manager bevat een user-defined methode genoemd `createLocalPrincipalAccount`. Deze methode accepteert een tekenreekswaarde die een e-mailadres opgeeft als parameterwaarde. Bij de methode `createLocalPrincipalAccount` wordt ervan uitgegaan dat een lokaal domein met de naam `EDC_EXTERNAL_REGISTERED` al bestaat. U kunt deze domeinnaam om het even wat vormen u wenst; nochtans, voor een productietoepassing, kunt u met een ondernemingsdomein willen integreren.

De `createUsers` methode herhaalt over elk e-mailadres en leidt tot een overeenkomstig voorwerp van de Gebruiker (een lokale gebruiker in `EDC_EXTERNAL_REGISTERED` domein). Tot slot wordt de methode `doEmails` geroepen. Deze methode wordt opzettelijk als een stoofpot in het monster gelaten. In een productieimplementatie, zou het toepassingslogica bevatten om uitnodigings e-mailberichten naar de pas gecre??erde gebruikers te verzenden. Het wordt in de steekproef verlaten om de stroom van de toepassingslogica van een echte toepassing aan te tonen.

### Implementatie {#user-handler-implementation} van de uitnodigen externe gebruikers-handler defini??ren

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
???
```

>[!NOTE]
>
>Deze Java-klasse wordt opgeslagen als een JAVA-bestand met de naam InviteExternalUsersSample.java.

## Het XML-bestand van de component defini??ren voor de machtigingshandler {#define-component-xml-authorization-handler}

U moet een dossier van componentXML bepalen om de uitnodigings externe gebruikersmanagercomponent op te stellen. Er bestaat een XML-componentbestand voor elke component en er worden metagegevens over de component weergegeven.

Het volgende `component.xml` dossier wordt gebruikt voor de uitnodigings externe gebruikersmanager. De servicenaam is `InviteExternalUsersSample` en de bewerking die deze service beschikbaar stelt, krijgt de naam `invitedUser`. De invoerparameter is een `java.util.List`-instantie en de uitvoerwaarde is een array van `com.adobe.edc.server.spi.esrp.InvitedUserProviderResult`-instanties.

### Het XML-bestand van de component defini??ren voor de handler {#component-xml-invite-external-users-handler} voor externe gebruikers uitnodigen

```as3
<component xmlns="http://adobe.com/idp/dsc/component/document"> 
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

## De uitnodigen van externe gebruikers-handler {#packaging-invite-external-users-handler} in een pakket plaatsen

Als u de uitnodigen van externe gebruikers-handler wilt implementeren in AEM Forms, moet u uw Java-project in een JAR-bestand plaatsen. U moet ervoor zorgen dat de externe JAR-bestanden waarvan de bedrijfslogica van de uitnodigen van externe gebruikers afhankelijk is, zoals de `edc-server-spi.jar`- en `adobe-rightsmanagement-client.jar`-bestanden, ook in het JAR-bestand worden opgenomen. Het XML-bestand van de component moet ook aanwezig zijn. Het `component.xml`-bestand en externe JAR-bestanden moeten zich in de hoofdmap van het JAR-bestand bevinden.

>[!NOTE]
>
>In de onderstaande afbeelding wordt een klasse `BootstrapImpl` weergegeven. In deze sectie wordt niet besproken hoe u een klasse `BootstrapImpl` kunt maken.

In de volgende afbeelding ziet u de inhoud van het Java-project die is verpakt in het JAR-bestand van de uitnodigingshandler voor externe gebruikers.

![Gebruikers uitnodigen](assets/ci_ci_InviteUsers.png)

A. Externe JAR-bestanden vereist door component B. JAVA-bestand

U moet de uitnodigen externe gebruikers-handler verpakken in een JAR-bestand. In het vorige diagram worden .JAVA-bestanden weergegeven. Nadat de bestanden in een JAR-bestand zijn verpakt, moeten ook de bijbehorende .CLASS-bestanden worden opgegeven. Zonder de .CLASS dossiers, werkt de vergunningsmanager niet.

>[!NOTE]
>
>Nadat u de externe machtigingshandler in een JAR-bestand hebt verpakt, kunt u de component implementeren in AEM Forms. Slechts ????n nodigt externe gebruikersmanager uit kan in een bepaalde tijd worden opgesteld.

>[!NOTE]
>
>U kunt een component programmatically ook opstellen.

## De uitnodigen van externe gebruikers-handler {#testing-invite-external-users-handler} testen

Om de uitnodigings externe gebruikersmanager te testen, kunt u externe gebruikers toevoegen om uit te nodigen door beleidsconsole te gebruiken.

Om externe gebruikers toe te voegen om het gebruiken van beleidsconsole uit te nodigen:

1. Implementeer het JAR-bestand van de uitnodigen van externe gebruikers met Workbench.
1. Start de toepassingsserver opnieuw.
1. Meld u aan bij de beheerconsole.
1. Klik **[!UICONTROL Services]** > **[!UICONTROL Rights Management]** > **[!UICONTROL Configuration]** > Uitgenodigd **[!UICONTROL User Registration]**.
1. Schakel het selectievakje **[!UICONTROL Enable invited user registration]** in om de uitgenodigde gebruiker te registreren. Klik onder **[!UICONTROL Use Built-in registration system]** op **[!UICONTROL No]**. Sla uw instellingen op.
1. Klik op de startpagina van de beheerconsole op **[!UICONTROL Settings]** > **[!UICONTROL User Management]** > **[!UICONTROL Domain Management]**.
1. Klik op **[!UICONTROL New Local Domain]**. Maak op de volgende pagina een domein met de naam en de id-waarde `EDC_EXTERNAL_REGISTERED`. Sla uw wijzigingen op.
1. Klik op de startpagina van de beheerconsole op **[!UICONTROL Services]** > **[!UICONTROL Rights Management]** > **[!UICONTROL Invited and Local Users]**. De pagina **[!UICONTROL Add Invited User]** wordt weergegeven.
1. Voer e-mailadressen in (omdat de huidige uitnodigen van externe gebruikers geen e-mailberichten verzendt, hoeft de geadresseerde e-mail niet geldig te zijn). Klik op **[!UICONTROL OK]**. De gebruikers worden uitgenodigd aan het systeem.
1. Klik op de startpagina van de beheerconsole op **[!UICONTROL Settings]** > **[!UICONTROL User Management]** > **[!UICONTROL Users and Groups]**.
1. Voer in het veld **[!UICONTROL Find]** een e-mailadres in dat u hebt opgegeven. Klik op **[!UICONTROL Find]**. De gebruiker u uitnodigde verschijnt als gebruiker in het lokale `EDC_EXTERNAL_REGISTERED` domein.

>[!NOTE]
>
>De uitnodigen externe gebruikers-handler mislukt als de component is gestopt of verwijderd.
